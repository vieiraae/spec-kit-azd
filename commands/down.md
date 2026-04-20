---
description: "Delete your project's Azure resources"
---

# Delete Resources

Delete Azure resources that were provisioned for your project.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Build and execute the `azd down` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd down [<layer>] [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--force` | | Delete resources without confirmation |
| `--purge` | | Permanently delete soft-deleted resources (e.g., key vaults) without confirmation |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Delete resources interactively:
```bash
azd down
```

Delete a specific layer:
```bash
azd down infra
```

Force delete without confirmation:
```bash
azd down --force
```

Force delete and purge soft-deleted resources:
```bash
azd down --force --purge
```

2. **Warning**: This operation is destructive and will delete Azure resources. Ensure you have confirmed the correct environment before proceeding.

3. Resources that support soft-delete (e.g., Azure Key Vault) will be soft-deleted by default. Use `--purge` to permanently delete them.
