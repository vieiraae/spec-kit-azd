---
description: "Develop, test and run hooks for a project"
---

# Hooks

Develop, test, and run hooks for a project.

## User Input

$ARGUMENTS

## Steps

1. Build and execute the `azd hooks run` command with appropriate flags.

### Command Reference

```
azd hooks run <name> [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--service` | | Only run hooks for the specified service |
| `--layer` | | Only run hooks for the specified provisioning layer |
| `--platform` | | Force hooks to run for the specified platform |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Run a specific hook:
```bash
azd hooks run predeploy
```

Run hook for a specific service:
```bash
azd hooks run postdeploy --service web
```

Run hook for a specific layer:
```bash
azd hooks run preprovision --layer infra
```

2. Hooks are defined in `azure.yaml` and can be set at the project level or service level. They follow the naming convention `pre{command}` or `post{command}` (e.g., `predeploy`, `postprovision`).
