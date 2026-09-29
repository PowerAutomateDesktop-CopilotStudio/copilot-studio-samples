[All samples](README.md)

# How the samples are organised

Two kinds of samples, one layout. Once you have read one, you know where to find everything in all the others.

| Kind | What it is | Its files |
|---|---|---|
| **Agent** | a Copilot Studio agent: instructions, skills, tools, knowledge | the agent workspace, as `pac copilot clone` writes it |
| **Workflow** | a Copilot Studio workflow: typed inputs, deterministic steps, typed outputs | the workflow folder (`metadata.yml` + `workflow.json`) |

## One folder per sample

```text
samples/<what-it-does>/
├── README.md        overview: try it, problem, solution, what it does, how it works, design, limits, tested on
├── SETUP.md         the paths to try it, from the lightest to the fullest, then troubleshooting
├── CHANGELOG.md     one section per version
├── sample.yml       the card both pages are generated from
├── agent/<Agent>/   (agent) settings.mcs.yml, behaviors/ (skills), capabilities/ (tools, knowledge), workflows/
├── workflows/       (workflow) <Name>-<guid>/metadata.yml and workflow.json
├── tool/            (workflow, optional) the file that makes it a tool of an agent
├── knowledge/       fictitious documents to add as knowledge
├── tests/           test-set.csv: messages, the skill expected to answer, words that must or must not appear
└── assets/          screenshots
```

Each sample is also published alone as a zip, on the **Releases** page, one release per version.

## Try it: the lightest path first

| Kind | 1 | 2 | 3 |
|---|---|---|---|
| Agent | **Quick try**: the instructions pasted into a new agent, a few messages | **Full agent**: pushed with the pac CLI, skills and knowledge included | **In your own agent**: one skill added to an agent you have |
| Workflow | **Run it** or **call it from an agent**: pushed into any agent workspace | **In your own build**: the steps and the contract reused | |

Each path says what it asks you to create. The counts are read from the files.

## What you need

- **Copilot Studio** in an environment where you can create agents.
- For the full paths, the **Power Platform CLI** (`pac`), signed in to that environment: see [the pac CLI](docs/pac-cli.md).

## Versions

Each sample has its own version (`x.y.z`): a patch changes no behaviour, a minor adds something optional, a major asks
you to set it up again. The **Tested on** table of each overview gives the date and the path that was tested.
