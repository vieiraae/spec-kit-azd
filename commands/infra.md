---
description: "Manage your Infrastructure as Code (IaC)"
---

# Infrastructure

Manage your Infrastructure as Code (IaC).

## User Input

$ARGUMENTS

## Steps

1. Build and execute the `azd infra generate` command with appropriate flags.

### Command Reference

```
azd infra generate [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--force` | | Overwrite existing files without prompting |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Generate IaC templates:
```bash
azd infra generate
```

Generate and overwrite existing files:
```bash
azd infra generate --force
```

2. This command writes Infrastructure as Code (Bicep or Terraform) files to disk based on your `azure.yaml` configuration, allowing you to manually manage and customize them.

3. By default, infrastructure templates are placed in the `infra/` directory. The provider (Bicep or Terraform) is determined by the `infra.provider` setting in `azure.yaml`.
