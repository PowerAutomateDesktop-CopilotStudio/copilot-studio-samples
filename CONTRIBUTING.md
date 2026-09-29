[All samples](README.md)

# Share a sample

A sample is one folder. You bring the agent or the workflow as files, and a card (`sample.yml`); the tool writes the
two pages (`README.md`, `SETUP.md`).

1. Copy [`templates/agent`](templates/agent) or [`templates/workflow`](templates/workflow) and rename the folder.
2. **Agent**: put the agent workspace in `agent/<Agent name>/` (`pac copilot clone`, then remove the `.mcs/` folder).
   **Workflow**: put `workflows/<Name>-<guid>/` (and, for an agent tool, `tool/<Name>.mcs.yml`).
3. Fill `sample.yml`: the problem, the solution, the techniques (ids of [`techniques.yml`](techniques.yml)), the
   category (one of [`categories.yml`](categories.yml)), the quick try, the limits. What the files already say
   (instructions, skills, tools, knowledge, inputs, outputs, steps) is **not** typed in the card.
4. `python tools/build_docs.py` writes the pages. Read the overview as a senior consultant would (can I decide in a
   minute?), the setup as a junior would (can I rebuild it without help?).
5. Open a pull request. The check runs `tools/build_docs.py --check`.

To see the site on your PC before the pull request:

```text
pip install -r tools/requirements-site.txt
python tools/build_site.py
python -m http.server 8797 --directory site
```

## Rules

- **The lightest path first**: an agent ships a quick try that works from its instructions alone (`quick_try.try`:
  the messages and what to expect); a workflow gives the inputs of its first run and the result (`quick_try`).
- **Tested**: `tested:` says when, which path, and the result. A sample never tested says so on its pages.
- **No personal or company data**: no names, e-mails, tenants, environment URLs, schema names of a real customer.
  Knowledge files are fictitious.
- **Files for the reader**: descriptions and instructions explain what the agent or the workflow does. Nothing about
  how the files were produced (scripts, generators): the check warns about it.
- **Limits stated**: what the sample does not do, and what was not tested, is written in `limits:`.

## Versions

| What changed | Version |
|---|---|
| A fix that changes no behaviour (a description, a typo) | patch: 1.0.**1** |
| Something new and optional (a skill, an output) | minor: 1.**1**.0 |
| The reader must set it up again (a new input, a new connection, a renamed skill) | major: **2**.0.0 |

After the merge, the tag `<sample id>-v<version>` publishes the sample alone as a zip on the Releases page.
