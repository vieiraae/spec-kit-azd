---
description: "Package the project's code to be deployed to Azure"
---

# Package

Package the project's code to be deployed to Azure.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Build and execute the `azd package` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd package <service> [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--all` | | Package all services listed in azure.yaml |
| `--environment` | `-e` | Name of the environment to use |
| `--output-path` | | File or folder path to save generated packages |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Package all services:
```bash
azd package --all
```

Package a specific service:
```bash
azd package web
```

Package to a specific output path:
```bash
azd package web --output-path ./dist
```

2. The packaged artifacts can be used with `azd deploy --from-package` for deployment.
