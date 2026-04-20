---
description: "Manage azd configurations (subscription, location)"
---

# Configuration

Manage the Azure Developer CLI user configuration, including default Azure subscription and location.

## User Input

$ARGUMENTS

## Steps

1. Determine the configuration action from user input and execute the appropriate sub-command.

### Configuration Path

The default config directory is:
- **Linux/macOS**: `$HOME/.azd`
- **Windows**: `%USERPROFILE%\.azd`

Override with the `AZD_CONFIG_DIR` environment variable.

### Sub-commands

---

### `azd config get`

Get a configuration value.

```
azd config get <path> [flags]
```

#### Examples

```bash
azd config get defaults.subscription
azd config get defaults.location
```

---

### `azd config set`

Set a configuration value.

```
azd config set <path> <value> [flags]
```

#### Examples

```bash
azd config set defaults.subscription <yourSubscriptionID>
azd config set defaults.location eastus
```

---

### `azd config show`

Show all configuration values.

```
azd config show [flags]
```

#### Examples

```bash
azd config show
```

---

### `azd config unset`

Remove a configuration value.

```
azd config unset <path> [flags]
```

#### Examples

```bash
azd config unset defaults.location
```

---

### `azd config reset`

Reset all configuration to defaults.

```
azd config reset [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--force` | `-f` | Force reset without confirmation |

#### Examples

```bash
azd config reset
azd config reset --force
```

---

### `azd config list-alpha`

Display the list of available features in alpha stage.

```
azd config list-alpha [flags]
```

#### Examples

```bash
azd config list-alpha
```

---

### `azd config options`

List all possible configuration settings with descriptions and allowed values.

```
azd config options [flags]
```

#### Examples

```bash
azd config options
```

---

### Common Flags (all sub-commands)

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

2. If the user wants to see current configuration, use `azd config show`. To set common defaults, use `azd config set`.
