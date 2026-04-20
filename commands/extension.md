---
description: "Manage azd extensions"
---

# Extension Management

Manage azd extensions: install, list, show, uninstall, upgrade, and manage sources.

## User Input

$ARGUMENTS

## Steps

1. Determine the extension action from user input and execute the appropriate sub-command.

### Sub-commands

---

### `azd extension install`

Install a specified extension.

```
azd extension install <extension-id> [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--source` | `-s` | Extension source to use for installs |
| `--version` | `-v` | Version of the extension to install |
| `--force` | `-f` | Force installation (including downgrades and reinstalls) |

#### Examples

```bash
azd extension install my-extension
azd extension install my-extension --version 1.2.0
azd extension install my-extension --source my-source --force
```

---

### `azd extension list`

List available or installed extensions.

```
azd extension list [--installed] [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--installed` | List installed extensions only |
| `--source` | Filter extensions by source |
| `--tags` | Filter extensions by tags |

#### Examples

```bash
azd extension list
azd extension list --installed
azd extension list --tags azure,deploy
```

---

### `azd extension show`

Show details for a specific extension.

```
azd extension show <extension-id> [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--source` | `-s` | Extension source to use |

#### Examples

```bash
azd extension show my-extension
```

---

### `azd extension uninstall`

Uninstall an extension.

```
azd extension uninstall [extension-id] [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--all` | Uninstall all installed extensions |

#### Examples

```bash
azd extension uninstall my-extension
azd extension uninstall --all
```

---

### `azd extension upgrade`

Upgrade an extension.

```
azd extension upgrade [extension-id] [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--all` | | Upgrade all installed extensions |
| `--source` | `-s` | Extension source to use for upgrades |
| `--version` | `-v` | Version to upgrade to |

#### Examples

```bash
azd extension upgrade my-extension
azd extension upgrade --all
azd extension upgrade my-extension --version 2.0.0
```

---

### `azd extension source add`

Add an extension source.

```
azd extension source add [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--name` | `-n` | Name of the extension source |
| `--location` | `-l` | Location of the extension source |
| `--type` | `-t` | Type of source: `file` or `url` |

#### Examples

```bash
azd extension source add --name my-source --location https://example.com/registry.json --type url
```

---

### `azd extension source list`

List extension sources.

```
azd extension source list [flags]
```

---

### `azd extension source remove`

Remove an extension source.

```
azd extension source remove <name> [flags]
```

---

### `azd extension source validate`

Validate an extension source's registry.json file.

```
azd extension source validate <name-or-path-or-url> [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--strict` | Enable strict validation (require checksums) |

#### Examples

```bash
azd extension source validate my-source
azd extension source validate ./registry.json --strict
```

---

### Common Flags (all sub-commands)

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |
