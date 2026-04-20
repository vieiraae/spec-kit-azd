---
description: "Manage environments (create, list, select, set values)"
---

# Environment Management

Manage azd environments including creating, selecting, and configuring environment variables.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `azure.subscription` → `--subscription` (for `env new`)
- `azure.location` → `--location` (for `env new`)
- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Determine the environment action from user input and execute the appropriate sub-command.

### Sub-commands

---

### `azd env new`

Create a new environment and set it as the default.

```
azd env new <environment> [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--location` | `-l` | Azure location for the new environment |
| `--subscription` | | Azure subscription ID for the new environment |

#### Examples

```bash
azd env new dev
azd env new production --location westus2 --subscription <subscription-id>
```

---

### `azd env list`

List all environments.

```
azd env list [flags]
```

#### Examples

```bash
azd env list
```

---

### `azd env select`

Set the default environment.

```
azd env select [<environment>] [flags]
```

#### Examples

```bash
azd env select production
```

---

### `azd env set`

Set one or more environment values.

```
azd env set [<key> <value>] | [<key>=<value> ...] | [--file <filepath>] [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--file` | | Path to .env formatted file to load values from |

#### Examples

```bash
azd env set MY_VAR my-value
azd env set MY_VAR=my-value OTHER_VAR=other-value
azd env set --file .env.production
```

---

### `azd env get-value`

Get a specific environment value.

```
azd env get-value <keyName> [flags]
```

#### Examples

```bash
azd env get-value AZURE_LOCATION
```

---

### `azd env get-values`

Get all environment values.

```
azd env get-values [flags]
```

#### Examples

```bash
azd env get-values
```

---

### `azd env refresh`

Refresh environment values from a previous infrastructure provision.

```
azd env refresh <environment> [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--hint` | Hint to help identify the environment to refresh |
| `--layer` | Provisioning layer to refresh from |

#### Examples

```bash
azd env refresh dev
azd env refresh production --layer infra
```

---

### `azd env remove`

Remove an environment.

```
azd env remove <environment> [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--force` | Skip confirmation before removal |

#### Examples

```bash
azd env remove old-env
azd env remove old-env --force
```

---

### `azd env set-secret`

Set a name as a reference to a Key Vault secret in the environment.

```
azd env set-secret <name> [flags]
```

#### Examples

```bash
azd env set-secret DATABASE_PASSWORD
```

---

### `azd env config get`

Get a configuration value from the environment's config.json.

```
azd env config get <path> [flags]
```

#### Examples

```bash
azd env config get myapp.endpoint
```

---

### `azd env config set`

Set a configuration value in the environment's config.json. Values are auto-parsed as JSON types when possible.

```
azd env config set <path> <value> [flags]
```

#### Examples

```bash
azd env config set myapp.endpoint https://example.com
azd env config set myapp.debug true
azd env config set myapp.count 42
azd env config set infra.parameters.tags '{"env":"dev"}'
azd env config set myapp.port '"8080"'
```

---

### `azd env config unset`

Remove a configuration value from the environment's config.json.

```
azd env config unset <path> [flags]
```

#### Examples

```bash
azd env config unset myapp.endpoint
```

---

### Common Flags (all sub-commands)

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

2. Environment files are stored in `.azure/<environment-name>/` within your project directory.
