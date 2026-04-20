---
description: "Add a component to your project"
---

# Add Component

Add a component to your project.

## User Input

$ARGUMENTS

## Steps

1. Build and execute the `azd add` command with appropriate flags.

### Command Reference

```
azd add [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Add a component interactively:
```bash
azd add
```

2. The command runs interactively to guide you through adding a new component (service, database, etc.) to your project. It updates the `azure.yaml` and infrastructure templates accordingly.
