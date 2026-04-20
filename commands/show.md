---
description: "Display information about your project and its resources"
---

# Show Project Information

Display information about your project and its resources.

## User Input

$ARGUMENTS

## Steps

1. Build and execute the `azd show` command with appropriate flags.

### Command Reference

```
azd show [resource-name|resource-id] [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--show-secrets` | | Unmask secrets in output |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Show project overview:
```bash
azd show
```

Show a specific resource:
```bash
azd show my-resource
```

Show with secrets unmasked:
```bash
azd show --show-secrets
```

2. The output includes project name, services, endpoints, and resource information.
