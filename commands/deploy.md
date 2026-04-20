---
description: "Deploy your project code to Azure"
---

# Deploy

Deploy your project code to Azure.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `environment.name` → `--environment`
- `deploy.timeout` → `--timeout`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Ensure the project has been provisioned first. If not, suggest running `azd provision` or `azd up`.

2. Build and execute the `azd deploy` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd deploy <service> [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--all` | | Deploy all services listed in azure.yaml |
| `--environment` | `-e` | Name of the environment to use |
| `--from-package` | | Deploy from a packaged artifact (file path for zip, image tag for containers) |
| `--timeout` | | Maximum seconds to wait for each service deployment (default: 1200) |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Deploy all services:
```bash
azd deploy --all
```

Deploy a specific service:
```bash
azd deploy web
```

Deploy from a package:
```bash
azd deploy web --from-package ./dist/web.zip
```

Deploy with custom timeout:
```bash
azd deploy api --timeout 1800
```

3. Monitor the deployment output for any errors or warnings.

4. After deployment, the service endpoints will be displayed. Note that `--timeout` only stops azd from waiting — it does not cancel the Azure-side deployment.
