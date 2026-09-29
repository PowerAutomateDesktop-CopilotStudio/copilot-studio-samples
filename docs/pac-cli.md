[How the samples are organised](../START-HERE.md)

# The pac CLI

The full paths of the samples use the Power Platform CLI (`pac`): it packs, imports, clones and pushes agents as files.

## Sign in to your environment

```text
pac auth create --environment <your environment URL>
pac env who
```

`pac env who` shows the environment the next commands will use.

## The commands the samples use

| Command | What it does |
|---|---|
| `pac copilot pack --publisher-prefix <prefix> --project-dir <agent folder> --output-path out` | builds a solution package from an agent folder |
| `pac solution import --path <zip> --publish-changes` | imports that package: the agent is created |
| `pac copilot clone --bot <schema name> --output-dir <folder>` | writes a synchronised copy of an agent |
| `pac copilot push --project-dir <folder>` | sends the changes of a synchronised copy (skills, tools, workflows) |
| `pac copilot list` | lists the agents of the environment |

Skills do not travel in the solution package: a sample's setup pushes them into the synchronised copy after the import.
