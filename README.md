# AI Superpowers

Centralized AI agent configuration for multiple IDEs and coding assistants. One source of truth — install to any project with a single command.

## Supported IDEs

| IDE | Flag | Config Folder |
|---|---|---|
| Cursor | `-c` | `.cursor/` |
| GitHub Copilot | `-C` | `.vscode/` |
| Kilocode | `-k` | `.kilo/` |
| Qwen Code CLI | `-q` | `.qwen/` |
| OpenCode | `-o` | `.opencode/` |
| Google Antigravity | `-a` | `.agents/` |

## Quick Start

```bash
# Interactive install — choose IDEs and MCP servers
./install.sh -p /path/to/your/project

# Non-interactive — all IDEs, all MCP servers
./install.sh -p /path/to/your/project -A -y

# Specific IDE only
./install.sh -p /path/to/your/project -c

# Dry run — see what would happen
./install.sh -p /path/to/your/project -A -n

# Uninstall
./install.sh -p /path/to/your/project -A -u
```

## What Gets Installed

### IDE Config Folders

Each IDE folder contains agents, rules, skills, workflows, and commands — copied from this repo's source directories.

### MCP Servers

MCP configs are **merged** from `configs/mcp/` and written as real files (not symlinks) to each IDE's expected location:

| IDE | MCP Config File | Format |
|---|---|---|
| Cursor | `.cursor/mcp.json` | `{mcpServers: {...}}` |
| Copilot | `.vscode/mcp.json` | `{servers: {...}}` |
| Kilocode | `.kilo/mcp.json` | `{mcpServers: {...}}` |
| Qwen | `.qwen/settings.json` | `{mcpServers: {...}}` (httpUrl normalized) |
| OpenCode | `.opencode/opencode.json` | `{mcp: {...}}` (converted format) |
| Antigravity | `~/.gemini/antigravity/mcp_config.json` | `{mcpServers: {...}}` (global) |

### MCP Server Sources

Servers are merged from:

- `configs/mcp/mcp-servers.json` — main server collection
- `configs/mcp/http/*.json` — HTTP/streamable servers (Context7, DeepWiki, GitHub, GitLab, Exa, Atlassian, etc.)
- `configs/mcp/docker/*.json` — Docker-based servers (Engram, Playwright, Sequential Thinking, Fetch, CodeMap, Code Index, GitHub)
- `configs/mcp/node/*.json` — npx-based servers (BrowserMCP, Chrome DevTools, Codebase Index, Memory, Supabase, Railway, Playwright, Browserbase, Magic UI, Firecrawl, Exa, Fal AI, Confluence, Token Optimizer, Filesystem, GitHub)
- `configs/mcp/command/*.json` — CLI command servers (Trivy)

## MCP Servers Available

### HTTP (Remote)
| Server | URL | Description |
|---|---|---|
| context7 | https://mcp.context7.com/mcp | Live documentation lookup |
| deepwiki | https://mcp.deepwiki.com/mcp | Code documentation |
| github-http | https://api.githubcopilot.com/mcp/ | GitHub via Copilot API |
| GitLab-http | GitLab instance | GitLab API |
| exa-http | https://mcp.exa.ai/mcp | Web search |
| atlassian-http | https://mcp.atlassian.com/v1/mcp | Atlassian products |

### Docker
| Server | Image | Description |
|---|---|---|
| engram | cylian/engram | Persistent memory |
| playwright | mcp/playwright | Browser automation |
| sequentialthinking | mcp/sequentialthinking | Chain-of-thought |
| fetch | mcp/fetch | Web fetching |
| codemap | ghcr.io/breca/mcp-codemap | Code mapping |
| code-index | ghcr.io/code-index-mcp/mcp-index | Code indexing |
| github | ghcr.io/github/github-mcp-server | GitHub operations |

### Node (npx)
| Server | Package | Description |
|---|---|---|
| browsermcp | @browsermcp/mcp | Browser control |
| chrome-devtools | chrome-devtools-mcp | Chrome DevTools |
| codebase-index | opencode-codebase-index | Code indexing |
| memory | @modelcontextprotocol/server-memory | Persistent memory |
| sequential-thinking | @modelcontextprotocol/server-sequential-thinking | Reasoning |
| filesystem | @modelcontextprotocol/server-filesystem | File operations |
| context7 | @upstash/context7-mcp | Documentation lookup |
| supabase | @supabase/mcp-server-supabase | Database operations |
| railway | @railway/mcp-server | Railway deployments |
| playwright | @playwright/mcp | Browser automation |
| browserbase | @browserbasehq/mcp-server-browserbase | Cloud browser |
| magic | @magicuidesign/mcp | Magic UI components |
| firecrawl | firecrawl-mcp | Web scraping |
| exa | exa-mcp-server | Web search |
| fal-ai | fal-ai-mcp-server | AI media generation |
| confluence | confluence-mcp-server | Confluence integration |
| token-optimizer | token-optimizer-mcp | Token optimization |
| github | @modelcontextprotocol/server-github | GitHub operations |

### Command
| Server | Command | Description |
|---|---|---|
| trivy | trivy mcp | Security scanning |

## Dependencies

### Core
- `rsync` — file synchronization
- `node` / `npm` / `npx` — Node.js runtime
- `python3` / `pip3` — Python runtime
- `jq` — JSON processing (required for MCP merge)

### IDE-Specific (optional)
- `qwen-code` — Qwen Code CLI
- `opencode` — OpenCode
- `openspec` — OpenSpec
- `kilo` — Kilocode
- `semgrep` — Static analysis
- `trivy` — Security scanning (auto-installs MCP plugin)

Install dependencies interactively:
```bash
./install.sh -p /path/to/project -A -d
```

## Directory Structure

```
ai-configs/
├── install.sh              # Main installer
├── package.json            # npm dependencies (MCP servers)
├── .cursor/                # Cursor config source
├── .kilo/                  # Kilocode config source
├── .qwen/                  # Qwen config source
├── .opencode/              # OpenCode config source
├── .vscode/                # Copilot config source
├── .agents/                # Antigravity config source
│   ├── agents/             # Agent definitions
│   ├── rules/              # Coding rules & style guides
│   ├── skills/             # Agent skills (191+)
│   ├── workflows/          # Workflow definitions (91+)
│   ├── scripts/            # Helper scripts
│   └── .shared/            # Shared resources
├── configs/
│   └── mcp/
│       ├── mcp-servers.json    # Main server collection
│       ├── http/               # HTTP/streamable servers
│       ├── docker/             # Docker-based servers
│       ├── node/               # npx-based servers
│       └── command/            # CLI command servers
├── openspec/               # OpenSpec configuration
└── docs/                   # Documentation
```

## Interactive Mode

When run on a TTY without IDE flags, the installer prompts:

1. **IDE Selection** — choose which tools to configure (1-6 or all)
2. **MCP Server Selection** — choose which servers to enable (all, skip, or subset)

## Non-Interactive Mode

Use `-y` for CI/CD or scripted installs:

```bash
# All IDEs, all MCP servers
./install.sh -p /path/to/project -A -y

# Specific IDEs, no MCP
./install.sh -p /path/to/project -c -q --no-mcp -y

# With dependency check
./install.sh -p /path/to/project -A -y -d
```

## OpenSpec

Run `openspec init` after install with `-O`:

```bash
./install.sh -p /path/to/project -A -y -O
```

## Uninstall

```bash
./install.sh -p /path/to/project -A -u
```

## License

MIT
