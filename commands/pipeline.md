---
description: "Manage and configure deployment pipelines"
---

# Pipeline

Manage and configure your deployment pipelines.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `pipeline.provider` → `--provider`
- `pipeline.auth_type` → `--auth-type`
- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Build and execute the `azd pipeline config` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd pipeline config [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--provider` | | Pipeline provider: `github` (GitHub Actions) or `azdo` (Azure Pipelines) |
| `--auth-type` | | Authentication type: `federated` or `client-credentials` (GitHub only) |
| `--principal-id` | | Client ID of the service principal for Azure access |
| `--principal-name` | | Name of the service principal for Azure access |
| `--principal-role` | | Roles to assign to the service principal (default: `Contributor`, `User Access Administrator`) |
| `--remote-name` | | Git remote name to configure pipeline on (default: `origin`) |
| `--applicationServiceManagementReference` | `-m` | Service Management Reference UUID |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Configure pipeline interactively:
```bash
azd pipeline config
```

Configure for GitHub Actions with federated auth:
```bash
azd pipeline config --provider github --auth-type federated
```

Configure for Azure DevOps:
```bash
azd pipeline config --provider azdo
```

Configure with existing service principal:
```bash
azd pipeline config --principal-id <client-id> --principal-name my-sp
```

Configure with custom roles:
```bash
azd pipeline config --principal-role Contributor --principal-role Reader
```

2. This command configures your deployment pipeline to connect securely to Azure using service principals with federated credentials or client credentials.
