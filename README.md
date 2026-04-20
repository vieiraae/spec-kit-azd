# spec-kit-azd

A [Spec Kit](https://github.com/github/spec-kit) extension for the [Azure Developer CLI (azd)](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/).

## Overview

This extension enables Spec Kit users to interact with the Azure Developer CLI directly through AI-assisted commands. It covers the full azd command surface including initialization, provisioning, deployment, environment management, and more.

## Prerequisites

- [Spec Kit](https://github.com/github/spec-kit) >= 0.1.0
- [Azure Developer CLI (azd)](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/install-azd) >= 1.0.0

## Installation

```bash
specify extension add --dev /path/to/spec-kit-azd
```

Or clone and install:

```bash
git clone https://github.com/vieiraae/spec-kit-azd
specify extension add --dev spec-kit-azd/
```

## Commands

### Core Workflow

| Command | Description |
|---------|-------------|
| `speckit.azd.init` | Initialize a new azd application |
| `speckit.azd.up` | Provision and deploy to Azure in one step |
| `speckit.azd.deploy` | Deploy project code to Azure |
| `speckit.azd.provision` | Provision Azure resources |
| `speckit.azd.down` | Delete Azure resources |
| `speckit.azd.monitor` | Monitor a deployed project |
| `speckit.azd.package` | Package code for deployment |
| `speckit.azd.publish` | Publish to a container registry |
| `speckit.azd.restore` | Restore project dependencies |
| `speckit.azd.show` | Display project and resource info |

### Project Management

| Command | Description |
|---------|-------------|
| `speckit.azd.add` | Add a component to your project |
| `speckit.azd.azure-yaml` | Generate or validate azure.yaml |
| `speckit.azd.template` | Find and view templates |
| `speckit.azd.infra` | Manage Infrastructure as Code |
| `speckit.azd.hooks` | Run project hooks |
| `speckit.azd.pipeline` | Configure deployment pipelines |

### Authentication & Configuration

| Command | Description |
|---------|-------------|
| `speckit.azd.auth` | Authenticate with Azure |
| `speckit.azd.config` | Manage azd configuration |
| `speckit.azd.env` | Manage environments |

### Extensions & Tools

| Command | Description |
|---------|-------------|
| `speckit.azd.extension` | Manage azd extensions |
| `speckit.azd.mcp` | MCP server management (Alpha) |
| `speckit.azd.copilot` | Copilot agent settings (Preview) |
| `speckit.azd.completion` | Shell completion scripts |

### Utility

| Command | Description |
|---------|-------------|
| `speckit.azd.version` | Print azd version |
| `speckit.azd.update` | Update azd to latest version |

## Usage

With Claude:

```
claude
> /speckit.azd.init --template todo-nodejs-mongo
> /speckit.azd.up
> /speckit.azd.monitor --overview
> /speckit.azd.down
```

## azure.yaml Schema

The `speckit.azd.azure-yaml` command provides full support for generating and validating the `azure.yaml` template definition file. It covers all schema properties including services, infrastructure, pipelines, hooks, and workflows.

See the [azure.yaml schema reference](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli/azd-schema) for full documentation.

## License

MIT
