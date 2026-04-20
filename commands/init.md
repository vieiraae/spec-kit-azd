---
description: "Initialize a new azd application"
---

# Initialize Application

Initialize a new application using the Azure Developer CLI.

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

1. Determine the initialization approach based on user input:
   - **From template**: If a template name or URL is provided, use `--template`
   - **From existing code**: If the user has existing code, use `--from-code`
   - **Minimal**: If a minimal project is requested, use `--minimal`
   - **Interactive**: If no arguments, run interactively

2. Build and execute the `azd init` command with appropriate flags.

### Command Reference

```
azd init [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--template` | `-t` | Initialize from a template. Accepts Full URI, `<owner>/<repository>`, `<repository>` (if part of azure-samples), or local directory path |
| `--branch` | `-b` | Template branch to initialize from (use with `--template`) |
| `--from-code` | | Initialize from existing code |
| `--minimal` | `-m` | Initialize a minimal project |
| `--environment` | `-e` | Name of the environment to use |
| `--location` | `-l` | Azure location for the new environment |
| `--subscription` | `-s` | Azure subscription ID for the new environment |
| `--filter` | `-f` | Tag(s) to filter template results (comma-separated) |
| `--up` | | Provision and deploy to Azure after initializing from a template |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Initialize interactively:
```bash
azd init
```

Initialize from a template:
```bash
azd init --template todo-nodejs-mongo
```

Initialize from a GitHub repository:
```bash
azd init --template Azure-Samples/todo-nodejs-mongo
```

Initialize from existing code:
```bash
azd init --from-code
```

Initialize minimal project:
```bash
azd init --minimal
```

Initialize and immediately deploy:
```bash
azd init --template todo-nodejs-mongo --up
```

3. After initialization, verify that `azure.yaml` was created in the project root.

4. If the user needs help choosing a template, suggest using `azd template list` to browse available templates.
