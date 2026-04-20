---
description: "Monitor a deployed project"
---

# Monitor

Monitor a deployed project using Application Insights.

## User Input

$ARGUMENTS

## Extension Configuration

Load config from `.specify/extensions/azd/azd-config.yml`. Use the configured values to build the command so azd does not prompt:

- `environment.name` → `--environment`
- `global_flags.no_prompt` → `--no-prompt`
- `global_flags.debug` → `--debug`

## Steps

1. Build and execute the `azd monitor` command with appropriate flags, merging config defaults with any explicit user arguments (user arguments take precedence).

### Command Reference

```
azd monitor [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--environment` | `-e` | Name of the environment to use |
| `--overview` | | Open Application Insights Overview Dashboard |
| `--live` | | Open Application Insights Live Metrics (not supported for Python apps) |
| `--logs` | | Open Application Insights Logs |
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Open monitoring overview:
```bash
azd monitor --overview
```

Open live metrics:
```bash
azd monitor --live
```

Open logs:
```bash
azd monitor --logs
```

2. The command opens the selected Application Insights view in your web browser.

3. Note: Live Metrics is currently not supported for Python applications.
