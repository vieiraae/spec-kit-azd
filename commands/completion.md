---
description: "Generate shell completion scripts"
---

# Shell Completion

Generate shell completion scripts for azd.

## User Input

$ARGUMENTS

## Steps

1. Determine the target shell and execute the appropriate sub-command.

### Sub-commands

---

### `azd completion bash`

Generate bash completion script.

```bash
azd completion bash
```

To install, add to your `~/.bashrc`:
```bash
source <(azd completion bash)
```

---

### `azd completion zsh`

Generate zsh completion script.

```bash
azd completion zsh
```

---

### `azd completion fish`

Generate fish completion script.

```bash
azd completion fish
```

---

### `azd completion powershell`

Generate PowerShell completion script.

```powershell
azd completion powershell
```

To install in PowerShell, add to your profile:
```powershell
azd completion powershell | Out-String | Invoke-Expression
```

---

### `azd completion fig`

Generate Fig autocomplete spec.

```bash
azd completion fig
```

---

### Common Flags (all sub-commands)

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

2. Choose the appropriate completion script for the user's shell environment.
