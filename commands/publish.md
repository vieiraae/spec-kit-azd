---
description: "Publish a service to a container registry"
---

# Publish

Publish a service to a container registry.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Build and execute the `azd publish` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd publish <service> [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--all` | | Publish all services listed in azure.yaml |
| `--environment` | `-e` | Name of the environment to use |
| `--from-package` | | Publish from a container image (image tag) |
| `--to` | | Target container image in the form `[registry/]repository[:tag]` |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Publish all services:
```bash
azd publish --all
```

Publish a specific service:
```bash
azd publish api
```

Publish to a specific registry:
```bash
azd publish api --to myregistry.azurecr.io/myapp:latest
```

Publish from an existing package:
```bash
azd publish api --from-package myapp:v1.0
```

2. This command is used for container-based services to push images to a container registry.
