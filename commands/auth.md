---
description: "Authenticate with Azure (login, logout, status)"
---

# Authentication

Authenticate with Azure using the Azure Developer CLI.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `auth.method` → selects sub-command and flags automatically
- `auth.service_principal.client_id` → `--client-id`
- `auth.service_principal.client_secret` → `--client-secret`
- `auth.service_principal.client_certificate` → `--client-certificate`
- `auth.service_principal.tenant_id` → `--tenant-id`
- `auth.service_principal.federated_credential_provider` → `--federated-credential-provider`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Determine the authentication action from user input and execute the appropriate sub-command.

### Sub-commands

---

### `azd auth login`

Log in to Azure. When run without arguments, logs in interactively using a browser.

```
azd auth login [flags]
```

#### Flags

| Flag | Description |
|------|-------------|
| `--use-device-code` | Log in using a device code instead of a browser |
| `--client-id` | Client ID for service principal authentication |
| `--client-secret` | Client secret for service principal authentication |
| `--client-certificate` | Path to client certificate for service principal authentication |
| `--tenant-id` | Tenant ID or domain name to authenticate with |
| `--federated-credential-provider` | Provider for federated token (`github`, `azure-pipelines`, `oidc`) |
| `--managed-identity` | Use managed identity to authenticate |
| `--redirect-port` | Port for redirect URI during interactive login |
| `--check-status` | Check login status instead of logging in |

#### Examples

Interactive login:
```bash
azd auth login
```

Login with device code:
```bash
azd auth login --use-device-code
```

Login as service principal:
```bash
azd auth login --client-id <client-id> --client-secret <client-secret> --tenant-id <tenant-id>
```

Login with client certificate:
```bash
azd auth login --client-id <client-id> --client-certificate /path/to/cert.pem --tenant-id <tenant-id>
```

Login with managed identity:
```bash
azd auth login --managed-identity
```

Login with user-assigned managed identity:
```bash
azd auth login --managed-identity --client-id <user-assigned-client-id>
```

Login with federated credentials (GitHub Actions):
```bash
azd auth login --client-id <client-id> --tenant-id <tenant-id> --federated-credential-provider github
```

---

### `azd auth logout`

Log out of Azure.

```
azd auth logout [flags]
```

#### Examples

```bash
azd auth logout
```

---

### `azd auth status`

Display whether you are logged in to Azure and the associated account information.

```
azd auth status [flags]
```

#### Examples

```bash
azd auth status
```

---

### Common Flags (all sub-commands)

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

2. If the user doesn't specify a sub-command, default to checking the current authentication status with `azd auth status`, then suggest login if not authenticated.
