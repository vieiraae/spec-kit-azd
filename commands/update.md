---
description: "Update azd to the latest version"
---

# Update

Update Azure Developer CLI to the latest version.

## User Input

$ARGUMENTS

## Steps

1. Build and execute the `azd update` command with appropriate flags.

### Command Reference

```
azd update [flags]
```

### Available Flags

| Flag | Description |
|------|-------------|
| `--channel` | Update channel: `stable` or `daily` |
| `--check-interval-hours` | Override the update check interval in hours |

### Examples

Update to latest stable:
```bash
azd update
```

Update from daily channel:
```bash
azd update --channel daily
```

2. After update, verify the new version with `azd version`.
