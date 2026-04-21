
# IDEs

* Google Antigravity
* Cursor
* Github Copilot
* Kilo Code
  * kilo cli
* Opencode
  * OpenChamber

## IDE Configs

|           | Copilot | Cursor | Kilo | Opencode | Antigravity |
| --------- | ------- | ------ | ---- | -------- | ----------- |
| Commands  | `.github/prompts/` | `.cursor/commands/`? | `.kilo/commands/` | `.opencode/commands/*.md` | `.agents/workflows` |
| Skills    | `.agents/skills/`, `.claude/skills/`, `.github/skills`, `.copilot/skills` | `.agents/skills/`, `.cursor/skills/` | `.agents/skills/ `, `.claude/skills/ `, `.kilo/skills/` | `.agents/skills/`, `.claude/skills/`, `.opencode/skills/` | `.agents/skills/` |
| Rules     | `.vscode/instructions/*.instructions.md`, `AGENTS.md` | `.cursor/rules/` | `.kilo/rules/` | `opencode/rules/`, `AGENTS.md` | `.agents/rules/`, `.agent/skills/` |
| Agents    | `.github/agents/` | `.cursor/agents/` | `.kilo/agents/` | `.opencode/agents/` | ? |
| Hooks     | `.github/hooks/*.json` | `.cursor/hooks.json`, `.cursor/hooks/` | ? | `.opencode/hook/hooks.md` | `.agents/hooks/` |
| MCP       | `.vscode/mcp.json` | `.cursor/mcp.json` | `.kilo/kilo.jsonc` | `.opencode/opencode.jsonc` | `~/.gemini/antigravity/mcp_config.json` |
| plugins   | X | `.cursor/plugins/` | X | `.opencode/plugins/` | X |

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

### pi

```bash
npm install -g @mariozechner/pi-coding-agent
```

# Tools

## OpenSpec

## GSD-2

```bash
npm install -g gsd-pi
gsd install npm:pi-dashscope
```

## Sources

* [X] [Everything Claude Code](https://github.com/affaan-m/everything-claude-code)
* [X] [Antigravity Kit](https://github.com/vudovn/antigravity-kit)
* [X] [AI Gentle Stack](https://github.com/Gentleman-Programming/gentle-ai)
* [ ] [Antigravity Skills](https://github.com/guanyang/antigravity-skills)
* [ ] [context-mode](https://github.com/mksglu/context-mode/tree/main/configs)
* [ ] [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)
* [ ] [awesome-codex-subagents](https://github.com/VoltAgent/awesome-codex-subagents)
* [-] [superpowers](https://github.com/obra/superpowers)
* [X] [Awesome Copilot](https://github.com/github/awesome-copilot)
  * [Awesome Copilot Agents](https://awesome-copilot.github.com/agents/)
* [X] [GSD](https://github.com/vudovn/antigravity-kit)
* [ ] [GSD-2](https://github.com/gsd-build/gsd-2)
* tools
  * [X] [CocoIndex Code](https://github.com/cocoindex-io/cocoindex-code)
  * [ ] [graphify](https://github.com/safishamsi/graphify)
* multiplexers
  * [X] [standardagents/dmux](https://github.com/standardagents/dmux)
  * [?] [coder/mux](https://github.com/coder/mux)