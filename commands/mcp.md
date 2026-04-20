---
description: "Manage Model Context Protocol (MCP) server (Alpha)"
---

# MCP Server

Manage the Model Context Protocol (MCP) server. (Alpha)

## User Input

$ARGUMENTS

## Steps

1. Build and execute the `azd mcp start` command.

### Command Reference

```
azd mcp start [flags]
```

### Available Flags

| Flag | Short | Description |
|------|-------|-------------|
| `--cwd` | `-C` | Sets the current working directory |
| `--debug` | | Enable debugging and diagnostics logging |
| `--environment` | `-e` | Name of the environment to use |
| `--no-prompt` | | Accept defaults instead of prompting |

### Examples

Start the MCP server:
```bash
azd mcp start
```

2. This command starts an MCP server that can be used by MCP clients to access azd functionality through the Model Context Protocol interface.

3. **Note**: This feature is in Alpha stage and may change in future releases.
