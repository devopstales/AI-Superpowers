
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
| Commands  | `.github/prompts/` | `.cursor/commands/`? | `.kilo/commands/` | `.opencode/commands/*.md` | `.qwen/commands/` | `.agents/workflows` |
| Skills    | `.agents/skills/` | `.agents/skills/` | `.kilo/skills/` | `.opencode/skills/` | `.qwen/skills/` | `.agents/skills/` |
| Rules     | `.vscode/instructions/*.instructions.md`, `AGENTS.md` | `.cursor/rules/` | `.kilo/rules/` | `opencode/rules/`, `AGENTS.md` | `.qwen/rules/`, `QWEN.md` | `.agents/rules/` |
| Agents    | `.github/agents/` | `.cursor/agents/` | `.kilo/agents/` | `.opencode/agents/` |      | ? |
| Hooks     | `.github/hooks/*.json` | `.cursor/hooks.json`, `.cursor/hooks/` | ? | `.opencode/hook/hooks.md` |      | ? |
| MCP       | `.vscode/mcp.json` | `.cursor/mcp.json` | `.kilo/kilo.jsonc` | `.opencode/opencode.jsonc` | `.qwen/settings.json` | `~/.gemini/antigravity/mcp_config.json` |
| plugins       |  | `.cursor/plugins/` |      | `.opencode/plugins/` |    |             |

### VSCode

```json
.vscode/mcp.json
{
  "servers": {
    "context7": {
      "type": "http",
      "url": "https://mcp.context7.com/mcp"
    },
    "engram": {
      "args": [
        "mcp",
        "--tools=agent"
      ],
      "command": "engram"
    }
  }
}
```

### Cursor

```json
.cursor/hooks.json
{
  "version": 1,
  "hooks": {
    "preToolUse": [
      {
        "command": "context-mode hook cursor pretooluse",
        "matcher": "Shell|Read|Grep|WebFetch|Task|MCP:ctx_execute|MCP:ctx_execute_file|MCP:ctx_batch_execute"
      }
    ],
    "postToolUse": [
      {
        "command": "context-mode hook cursor posttooluse"
      }
    ]
  }
}
```

```json
.cursor/mcp.json
{
  "mcpServers": {
    "context7": {
      "args": [
        "-y",
        "@upstash/context7-mcp"
      ],
      "command": "npx"
    },
    "engram": {
      "args": [
        "mcp",
        "--tools=agent"
      ],
      "command": "engram"
    }
  }
}
```

### Opencode

```json
.opencode/opencode.json
{
  "$schema": "https://opencode.ai/config.json",
  "instructions": ["CONTRIBUTING.md", "docs/guidelines.md", ".opencode/rules/*.md"],
  "plugin": [
    "./plugins"
  ]
}
```

```json
.opencode/opencode.json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "context7": {
      "enabled": true,
      "type": "remote",
      "url": "https://mcp.context7.com/mcp"
    },
    "engram": {
      "command": [
        "engram",
        "mcp",
        "--tools=agent"
      ],
      "enabled": true,
      "type": "local"
    }
  }
}
```

### QWEN

```json
.qwen/settings.json
{
  "mcpServers": {
    "deepwiki": {
      "type": "streamable-http",
      "httpUrl": "https://mcp.deepwiki.com/mcp"
    }
  }
}
```

```json
.qwen/setting.json
{
  "hooks": {
    "Notification": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "notify-send 'Claude Code' 'Awaiting your input'"
          }
        ]
      }
    ]
  }
}
# https://github.com/QwenLM/qwen-code/issues/1708
```

## IDE Functions

|           | Copilot | Cursor | Kilo | Opencode | qwen | Antigravity |
| --------- | ------- | ------ | ---- | -------- | ---- | ----------- |
| Commands  | `.github/prompts/` | — | 83 | 92 | 9 | — |
| Skills    | 249 | 249 | 76 | 88 | — | 249 |
| Rules     | `.vscode/instructions/*.instructions.md`, `AGENTS.md` | `.cursor/rules/` | `.kilo/rules/` | `opencode/rules/`, `AGENTS.md` | `.qwen/rules/`, `QWEN.md` | `.agents/rules/` |
| Agents    | `.github/agents/` | `.cursor/agents/` | `.kilo/agents/` | `.opencode/agents/` | — | — |
| Hooks     | `.github/hooks/*.json` | `.cursor/hooks.json`, `.cursor/hooks/` | — | `.opencode/hook/hooks.md` | — | — |
| MCP       | `.vscode/mcp.json` | `.cursor/mcp.json` | `.kilo/kilo.jsonc` | `.opencode/opencode.jsonc` | `.qwen/settings.json` | `~/.gemini/antigravity/mcp_config.json` |
| plugins   | — | `.cursor/plugins/` | — | `.opencode/plugins/` | — | — |

> **Note:** Skills counts reflect directories in `.agents/skills/` (source of truth). Cursor, Kilo, and Opencode reference subsets from this location.

## Sources

* [X] [Everything Claude Code](https://github.com/affaan-m/everything-claude-code)
* [X] [Antigravity Kit](https://github.com/vudovn/antigravity-kit)
* [X] [AI Gentle Stack](https://github.com/Gentleman-Programming/gentle-ai)
* [ ] [context-mode](https://github.com/mksglu/context-mode/tree/main/configs)
* [ ] [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)
* [ ] [awesome-codex-subagents](https://github.com/VoltAgent/awesome-codex-subagents)
* [ ] [superpowers](https://github.com/obra/superpowers)
* [X] [Awesome Copilot](https://github.com/github/awesome-copilot)
  * [Awesome Copilot Agents](https://awesome-copilot.github.com/agents/)