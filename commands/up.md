---
description: "Provision and deploy your project to Azure with a single command"
---

# Provision and Deploy

Provision Azure resources and deploy your project code to Azure in a single command.

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

1. Ensure the project has an `azure.yaml` file in the root directory. If not, suggest running `azd init` first.

2. Build and execute the `azd up` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd up [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--location` | `-l` | Azure location for the new environment |
| `--subscription` | | Azure subscription ID for the new environment |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Run interactively:
```bash
azd up
```

With specific environment:
```bash
azd up -e production
```

With location and subscription:
```bash
azd up --location eastus --subscription <subscription-id>
```

Non-interactive (CI/CD):
```bash
azd up --no-prompt
```

3. The command performs three steps sequentially:
   - **Package**: Packages the application code
   - **Provision**: Creates Azure resources defined in the infrastructure templates
   - **Deploy**: Deploys the application code to the provisioned resources

4. After completion, display the service endpoints provided in the output.
