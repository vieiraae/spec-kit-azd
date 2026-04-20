---
description: "Generate or validate an azure.yaml template definition"
---

# Azure YAML Template Definition

Generate or validate an `azure.yaml` file that defines your azd template.

## User Input

$ARGUMENTS

## Steps

1. Based on user input, either **generate** a new `azure.yaml` file or **validate/update** an existing one.

2. The `azure.yaml` file must be placed in the project root directory.

### Schema Reference

The `azure.yaml` schema defines apps and Azure resource types included in azd templates.

---

### Top-Level Properties

| Property | Required | Type | Description |
|----------|----------|------|-------------|
| `name` | Yes | string | Name of the application |
| `resourceGroup` | No | string | Azure resource group name (overrides default) |
| `metadata` | No | object | Template metadata |
| `infra` | No | object | Infrastructure provisioning configuration |
| `services` | Yes | object | Services that comprise the application |
| `pipeline` | No | object | CI/CD pipeline configuration |
| `hooks` | No | object | Command-level hooks (`pre{command}` / `post{command}`) |
| `workflows` | No | object | Custom workflow definitions |
| `requiredVersions` | No | string | Supported azd version range (e.g., `>= 0.6.0-beta.3`) |

---

### `metadata` Properties

| Property | Required | Type | Description |
|----------|----------|------|-------------|
| `template` | No | string | Template identifier (e.g., `todo-nodejs-mongo@0.0.1-beta`) |

---

### `infra` Properties

| Property | Required | Type | Description | Values |
|----------|----------|------|-------------|--------|
| `provider` | No | string | IaC provider (default: `bicep`) | `bicep`, `terraform` |
| `path` | No | string | Relative path to IaC templates (default: `infra`) | |
| `module` | No | string | Default module name (default: `main`) | |

---

### `services` Properties

Each service is a named entry under the `services` key:

| Property | Required | Type | Description | Values |
|----------|----------|------|-------------|--------|
| `project` | Yes | string | Path to service source code directory | |
| `host` | Yes | string | Azure resource type for hosting | `appservice`, `containerapp`, `function`, `staticwebapp`, `aks`, `springapp` |
| `language` | Yes | string | Service implementation language | `dotnet`, `csharp`, `fsharp`, `py`, `python`, `js`, `ts`, `java` |
| `module` | Yes | string | Infrastructure module path (relative to infra folder) | |
| `dist` | Yes | string | Relative path to deployment artifacts | |
| `resourceName` | No | string | Name of the Azure resource | |
| `docker` | No | object | Docker options (for `containerapp` host) | |
| `k8s` | No | object | AKS configuration options | |
| `config` | No | object | Extra service configuration | |
| `hooks` | No | object | Service-level hooks | |
| `apiVersion` | No | string | Explicit API version for ACA deployments | |

#### Docker Options

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `path` | string | `./Dockerfile` | Path to the Dockerfile |
| `context` | string | `.` | Docker build context |
| `platform` | string | `amd64` | Platform target |
| `remoteBuild` | boolean | `false` | Enable remote ACR builds |

#### AKS (`k8s`) Options

| Property | Type | Description |
|----------|------|-------------|
| `deploymentPath` | string | Relative path to K8s manifests (default: `manifests`) |
| `namespace` | string | K8s namespace (default: project name) |
| `deployment.name` | string | K8s deployment resource name |
| `service.name` | string | K8s service resource name |
| `ingress.name` | string | K8s ingress resource name |
| `ingress.relativePath` | string | Relative path from ingress root |

---

### `pipeline` Properties

| Property | Required | Type | Description | Values |
|----------|----------|------|-------------|--------|
| `provider` | No | string | Pipeline provider (default: `github`) | `github`, `azdo` |

---

### `workflows` Properties

| Property | Required | Type | Description |
|----------|----------|------|-------------|
| `up` | No | object | Override default `azd up` workflow |
| `up.steps` | Yes | array | Steps to execute in the workflow |
| `up.steps[].azd` | Yes | string | azd command and args to execute |

---

### Sample: Basic Web App

```yaml
name: myApp
metadata:
  template: myApp@0.0.1-beta
services:
  web:
    project: ./src/web
    dist: build
    language: js
    host: appservice
```

### Sample: Multi-Service App

```yaml
name: todo-nodejs-mongo
metadata:
  template: todo-nodejs-mongo@0.0.1-beta
services:
  web:
    project: ./src/web
    dist: build
    language: js
    host: appservice
  api:
    project: ./src/api
    language: js
    host: appservice
```

### Sample: Container App with Docker

```yaml
name: myApp-aca
metadata:
  template: myApp-aca@0.0.1-beta
services:
  api:
    project: ./src/api
    language: js
    host: containerapp
    docker:
      path: ./Dockerfile
      context: ../
  web:
    project: ./src/web
    language: js
    host: containerapp
    docker:
      remoteBuild: true
```

### Sample: Terraform Provider

```yaml
name: myApp-terraform
metadata:
  template: myApp-terraform@0.0.1-beta
services:
  web:
    project: ./src/web
    dist: build
    language: js
    host: appservice
infra:
  provider: terraform
```

### Sample: AKS with Hooks

```yaml
name: todo-nodejs-mongo-aks
metadata:
  template: todo-nodejs-mongo-aks@0.0.1-beta
services:
  web:
    project: ./src/web
    dist: build
    language: js
    host: aks
    hooks:
      postdeploy:
        shell: sh
        run: azd env set REACT_APP_WEB_BASE_URL ${SERVICE_WEB_ENDPOINT_URL}
  api:
    project: ./src/api
    language: js
    host: aks
    k8s:
      ingress:
        relativePath: api
    hooks:
      postdeploy:
        shell: sh
        run: azd env set REACT_APP_API_BASE_URL ${SERVICE_API_ENDPOINT_URL}
```

### Sample: Azure DevOps Pipeline

```yaml
name: myApp
services:
  web:
    project: src/web
    dist: build
    language: js
    host: appservice
pipeline:
  provider: azdo
```

### Sample: Custom Workflow

```yaml
name: todo-nodejs-mongo
metadata:
  template: todo-nodejs-mongo@0.0.1-beta
workflows:
  up:
    steps:
      - azd: provision
      - azd: package
      - azd: deploy --all
```

3. When generating, ask the user for:
   - Application name
   - Services (project path, language, host type)
   - Infrastructure provider (Bicep or Terraform)
   - Pipeline provider (GitHub Actions or Azure DevOps), if needed

4. When validating, check:
   - `name` is present
   - At least one service is defined under `services`
   - Each service has `project`, `host`, and `language`
   - `host` values are valid (`appservice`, `containerapp`, `function`, `staticwebapp`, `aks`, `springapp`)
   - `language` values are valid (`dotnet`, `csharp`, `fsharp`, `py`, `python`, `js`, `ts`, `java`)
   - Infrastructure provider is valid if specified (`bicep` or `terraform`)
   - Pipeline provider is valid if specified (`github` or `azdo`)
