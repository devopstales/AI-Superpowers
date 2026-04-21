# MCP Servers

Model Context Protocol (MCP) server configurations for AI coding assistants. Servers are merged from `configs/mcp/` and written to each IDE's expected config location.

See also: [Tools and dependencies](tools-and-dependencies.md) (how `install.sh` checks and installs CLIs used with MCP).

## Configuration Merge

MCP configs are **merged** from multiple source directories and written as real files (not symlinks):

| Source | Content |
|---|---|
| `configs/mcp/mcp-servers.json` | Main server collection |
| `configs/mcp/http/*.json` | HTTP/streamable servers |
| `configs/mcp/docker/*.json` | Docker-based servers |
| `configs/mcp/node/*.json` | npx-based servers |
| `configs/mcp/command/*.json` | CLI command servers |

## IDE MCP Config Locations

| IDE | Config File | Format |
|---|---|---|
| Cursor | `.cursor/mcp.json` | `{mcpServers: {...}}` |
| Copilot | `.vscode/mcp.json` | `{servers: {...}}` |
| Kilocode | `.kilo/mcp.json` | `{mcpServers: {...}}` |
| OpenCode | `.opencode/opencode.json` | `{mcp: {...}}` (converted format) |
| Antigravity | `~/.gemini/antigravity/mcp_config.json` | `{mcpServers: {...}}` (global) |

## Available MCP Servers

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

## Server Categories

### Documentation & Research

| Server | Type | Use Case |
|---|---|---|
| context7 | HTTP + Node | Library/framework docs lookup |
| deepwiki | HTTP | GitHub repo documentation |
| exa | HTTP + Node | Neural web search |
| firecrawl | Node | Web scraping and crawling |

### Code Analysis

| Server | Type | Use Case |
|---|---|---|
| codebase-index | Node | Code indexing and search |
| code-index | Docker | Code indexing (alternative) |
| codemap | Docker | Code structure mapping |
| chrome-devtools | Node | Browser debugging |

### Browser Automation

| Server | Type | Use Case |
|---|---|---|
| playwright | Docker + Node | Browser automation and testing |
| browsermcp | Node | Browser control |
| browserbase | Node | Cloud browser operations |
| fetch | Docker | Web page fetching |

### Memory & Context

| Server | Type | Use Case |
|---|---|---|
| memory | Node | Persistent conversation memory |
| engram | Docker | Persistent memory (alternative) |
| sequentialthinking | Docker + Node | Chain-of-thought reasoning |

### Platform Integration

| Server | Type | Use Case |
|---|---|---|
| github | Docker + Node | GitHub operations (PRs, issues, repos) |
| github-http | HTTP | GitHub via Copilot API |
| GitLab-http | HTTP | GitLab API operations |
| confluence | Node | Confluence wiki integration |
| atlassian-http | HTTP | Atlassian products (Jira, Confluence) |

### Database & Infrastructure

| Server | Type | Use Case |
|---|---|---|
| supabase | Node | Supabase database operations |
| railway | Node | Railway deployment management |
| filesystem | Node | Local file system operations |

### AI & Media Generation

| Server | Type | Use Case |
|---|---|---|
| fal-ai | Node | AI image/video/audio generation |
| magic | Node | Magic UI component generation |

### Security

| Server | Type | Use Case |
|---|---|---|
| trivy | Command | Vulnerability scanning |

### Utilities

| Server | Type | Use Case |
|---|---|---|
| token-optimizer | Node | Token usage optimization |

## Adding Custom MCP Servers

To add a new server, create a JSON file in the appropriate source directory:

### HTTP Server (`configs/mcp/http/`)

```json
{
  "name": "my-server",
  "type": "http",
  "url": "https://mcp.example.com/mcp"
}
```

### Node/npx Server (`configs/mcp/node/`)

```json
{
  "name": "my-server",
  "type": "node",
  "command": "npx",
  "args": ["-y", "@scope/my-server-mcp"]
}
```

### Docker Server (`configs/mcp/docker/`)

```json
{
  "name": "my-server",
  "type": "docker",
  "image": "my-org/my-server:latest",
  "command": ["my-server", "mcp"]
}
```

### Command Server (`configs/mcp/command/`)

```json
{
  "name": "my-server",
  "type": "command",
  "command": "my-server mcp"
}
```

## MCP Selection During Install

The installer (`install.sh`) prompts for MCP server selection:

- **All** — enable every server
- **Skip** — no MCP servers
- **Subset** — interactive selection per category

Use `--no-mcp` flag to skip MCP configuration entirely:

```bash
./install.sh -p /path/to/project -A --no-mcp -y
```
