
# IDEs

* Google Antigravity
* Cursor
* Github Copilot
* Kilo Code
* Opencode
  * OpenChamber
* qwen code

## IDE Configs

|           | Copilot | Cursor | Kilo | Opencode | qwen | Antigravity |
| --------- | ------- | ------ | ---- | -------- | ---- | ----------- |
| Commands  | `.vscode/workflows/` | `.cursor/commands/`? | `.kilo/commands/` | `.opencode/commands/*.md` |      | `.agents/workflows` |
| Skills    | `.agents/skills/` | `.agents/skills/` | `.kilo/skills/` | `.opencode/skills/` |      | `.agents/skills/` |
| Rules     | `.vscode/instructions/*.instructions.md`, `AGENTS.md` | `.cursor/rules/` | `.kilo/rules/` | `opencode/rules/`, `AGENTS.md` |      | `.agents/rules/` |
| Agents    | `.vscode/agents/` | `.cursor/agents/` | `.kilo/agents/` | `.opencode/agents/` |      | ? |
| Hooks     | `.vscode/hooks.json`, `.vscode/hooks/` | `.cursor/hooks.json`, `.cursor/hooks/` | ? | ? |      | ? |
| MCP       | `.vscode/mcp.json` | `.cursor/mcp.json` | `.kilo/kilo.jsonc` | `opencode.jsonc` |      | `~/.gemini/antigravity/mcp_config.json` |
| plugins       | `.vscode/plugins` | `.cursor/plugins/` |      | `.opencode/plugins/` |    |             |


### Opencode

```json
{
  "$schema": "https://opencode.ai/config.json",
  "instructions": ["CONTRIBUTING.md", "docs/guidelines.md", ".opencode/rules/*.md"],
  "plugin": [
    "./plugins"
  ]
}
```

## IDE Functions

|           | Copilot | Cursor | Kilo | Opencode | qwen | Antigravity |
| --------- | ------- | ------ | ---- | -------- | ---- | ----------- |
| Commands  |         |        |      |          |      |             |
| Skills    |         |        |      |          |      |             |
| Rules     |         |        |      |          |      |             |
| Agents    |         |        |      |          |      |             |
| Hooks     |         |        |      |          |      |             |
| MCP       |         |        |      |          |      |             |

## Sources

* [ ] [Everything Claude Code](https://github.com/affaan-m/everything-claude-code)
* [ ] [Antigravity Kit](https://github.com/vudovn/antigravity-kit)
* [ ] [AI Gentle Stack](https://github.com/Gentleman-Programming/gentle-ai)
* [ ] [Awesome Copilot](https://github.com/github/awesome-copilot)