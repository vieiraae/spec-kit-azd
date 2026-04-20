# Changelog

All notable changes to this project will be documented in this file.

## [1.0.0] - 2026-04-20

### Added

- Initial release of the spec-kit-azd extension
- Core workflow commands: init, up, deploy, provision, down, monitor, package, publish, restore, show
- Authentication commands: auth login, auth logout, auth status
- Configuration management: config get, set, show, unset, reset, list-alpha, options
- Environment management: env new, list, select, set, get-value, get-values, refresh, remove, set-secret, config get/set/unset
- Extension management: extension install, list, show, uninstall, upgrade, source add/list/remove/validate
- Infrastructure management: infra generate
- Pipeline configuration: pipeline config
- Template browsing: template list, show, source add/list/remove
- MCP server management: mcp start
- Copilot settings: copilot consent grant/list/revoke
- Shell completion: completion bash, zsh, fish, powershell, fig
- azure.yaml schema support: generate and validate template definitions
- Utility commands: version, update
- Component management: add
- Hooks management: hooks run
