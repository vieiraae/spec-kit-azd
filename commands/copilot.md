---
description: "Manage GitHub Copilot agent settings (Preview)"
---

# Copilot

Manage GitHub Copilot agent settings. (Preview)

## User Input

$ARGUMENTS

## Steps

1. Determine the copilot action from user input and execute the appropriate sub-command.

### Sub-commands

---

### `azd copilot consent grant`

Grant trust rules for tools and servers.

```
azd copilot consent grant [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--global` | Apply globally to all servers |
| `--server` | Server name |
| `--tool` | Specific tool name (requires `--server`) |
| `--permission` | Permission: `allow`, `deny`, or `prompt` (default: `allow`) |
| `--scope` | Rule scope: `global` or `project` (default: `global`) |
| `--action` | Action type: `all` or `readonly` (default: `all`) |
| `--operation` | Operation type: `tool` or `sampling` (default: `tool`) |

#### Examples

Grant always permission to all tools globally:
```bash
azd copilot consent grant --global --permission allow
```

Grant project permission to a specific tool:
```bash
azd copilot consent grant --server my-server --tool my-tool --permission allow --scope project --action readonly
```

---

### `azd copilot consent list`

List all consent rules.

```
azd copilot consent list [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--scope` | Filter by scope: `global` or `project` |
| `--permission` | Filter by permission: `allow`, `deny`, or `prompt` |
| `--action` | Filter by action type: `readonly` or `any` |
| `--operation` | Filter by operation: `tool` or `sampling` |
| `--target` | Specific target (`server/tool` format) |

#### Examples

```bash
azd copilot consent list
azd copilot consent list --scope project --permission allow
```

---

### `azd copilot consent revoke`

Revoke consent rules.

```
azd copilot consent revoke [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--scope` | Filter by scope: `global` or `project` |
| `--permission` | Filter by permission: `allow`, `deny`, or `prompt` |
| `--action` | Filter by action type: `readonly` or `any` |
| `--operation` | Filter by operation: `tool` or `sampling` |
| `--target` | Specific target (`server/tool` format) |

#### Examples

```bash
azd copilot consent revoke --target my-server/my-tool
azd copilot consent revoke --scope global
```

---

### Common Flags (all sub-commands)

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

2. **Note**: This feature is in Preview and may change in future releases.
