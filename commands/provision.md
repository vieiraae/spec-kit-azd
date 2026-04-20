---
description: "Provision Azure resources for your project"
---

# Provision

Provision Azure resources for your project using the infrastructure templates defined in the project.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `azure.subscription` → `--subscription`
- `azure.location` → `--location`
- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Ensure the project has an `azure.yaml` file and infrastructure templates (Bicep or Terraform).

2. Build and execute the `azd provision` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd provision [<layer>] [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--location` | `-l` | Azure location for the new environment |
| `--subscription` | | Azure subscription ID for the new environment |
| `--no-state` | | (Bicep only) Force fresh deployment ignoring stored state |
| `--preview` | | Preview changes to Azure resources before applying |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Provision interactively:
```bash
azd provision
```

Provision a specific layer:
```bash
azd provision infra
```

Preview changes before provisioning:
```bash
azd provision --preview
```

Provision with fresh state (Bicep only):
```bash
azd provision --no-state
```

Provision with specific location:
```bash
azd provision --location westus2 --subscription <subscription-id>
```

3. Review the provisioned resources in the output. Environment values are automatically updated with resource information.
