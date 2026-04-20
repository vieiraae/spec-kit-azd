---
description: "Find and view template details"
---

# Templates

Find and view azd template details.

## User Input

$ARGUMENTS

## Steps

1. Determine the template action from user input and execute the appropriate sub-command.

### Sub-commands

---

### `azd template list`

Show list of sample azd templates. (Beta)

```
azd template list [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--filter` | `-f` | Tag(s) to filter template results (comma-separated) |
| `--source` | `-s` | Filter templates by source |

#### Examples

List all templates:
```bash
azd template list
```

Filter by tag:
```bash
azd template list --filter python
azd template list --filter "python,appservice"
```

Filter by source:
```bash
azd template list --source awesome-azd
```

---

### `azd template show`

Show details for a given template. (Beta)

```
azd template show <template> [flags]
```

#### Examples

```bash
azd template show todo-nodejs-mongo
```

---

### `azd template source add`

Add a template source. (Beta)

```
azd template source add <key> [flags]
```

#### Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--location` | `-l` | Location of the template source |
| `--name` | `-n` | Display name of the template source |
| `--type` | `-t` | Kind of source: `file`, `url`, or `gh` |

#### Examples

```bash
azd template source add my-templates --location https://example.com/templates.json --type url --name "My Templates"
```

Well-known keys:
- `default`: Default templates
- `awesome-azd`: Templates from https://aka.ms/awesome-azd

---

### `azd template source list`

List configured template sources. (Beta)

```
azd template source list [flags]
```

---

### `azd template source remove`

Remove a template source. (Beta)

```
azd template source remove <key> [flags]
```

#### Examples

```bash
azd template source remove my-templates
```

---

### Common Flags (all sub-commands)

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

2. Templates are blueprint repositories that include application code, infrastructure templates, and configurations for deploying to Azure.
