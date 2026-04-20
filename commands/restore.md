---
description: "Restore the project's dependencies"
---

# Restore

Restore the project's dependencies.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Build and execute the `azd restore` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd restore <service> [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--all` | | Restore all services listed in azure.yaml |
| `--environment` | `-e` | Name of the environment to use |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Restore all services:
```bash
azd restore --all
```

Restore a specific service:
```bash
azd restore web
```

2. This command restores language-specific dependencies (e.g., npm install, pip install, dotnet restore) for the specified services.
