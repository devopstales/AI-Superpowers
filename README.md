# AI Superpowers

Centralized AI agent configuration for multiple IDEs and coding assistants. One source of truth — install to any project with a single command.

## Supported IDEs

| IDE | Flag | Config Folder |
|---|---|---|
| Cursor | `-c` | `.cursor/` |
| GitHub Copilot | `-C` | `.vscode/` |
| Kilocode | `-k` | `.kilo/` |
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

MCP configs are **merged** from `configs/mcp/` and written as real files (not symlinks) to each IDE's expected location. See [MCP Servers](docs/mcp.md) for the full server list and configuration details.

## Dependencies

### Core
- `rsync` — file synchronization
- `node` / `npm` / `npx` — Node.js runtime
- `python3` / `pip3` — Python runtime
- `jq` — JSON processing (required for MCP merge)

### IDE-Specific (optional)
- `opencode` — OpenCode
- `openspec` — OpenSpec
- `kilo` — Kilocode
- `semgrep` — Static analysis
- `trivy` — Security scanning (auto-installs MCP plugin)

Install dependencies interactively:
```bash
./install.sh -p /path/to/project -A -d
```

## Interactive Mode

When run on a TTY without IDE flags, the installer prompts:

1. **IDE Selection** — choose which tools to configure (1-5 or all)
2. **MCP Server Selection** — choose which servers to enable (all, skip, or subset)

## Non-Interactive Mode

Use `-y` for CI/CD or scripted installs:

```bash
# All IDEs, all MCP servers
./install.sh -p /path/to/project -A -y

# Specific IDEs, no MCP
./install.sh -p /path/to/project -c -o --no-mcp -y

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

## Documentation

| Topic | Description | Intended Usage |
|---|---|---|
| [Skills](docs/skills.md) | Complete skill library — 249 skills across 15+ categories | When to use which skill, model routing, activation triggers |
| [Commands](docs/commands.md) | Slash commands across IDEs — 92 Opencode, 83 Kilo, 9 Qwen | Running reviews, tests, builds, OpenSpec/SDD workflows |
| [MCP Servers](docs/mcp.md) | Model Context Protocol servers — HTTP, Docker, Node, Command | Adding servers, configuring integrations, troubleshooting |
| [IDE Configs](docs/TODO.md) | IDE configuration matrix — commands, skills, rules, agents, hooks, MCP | Understanding how each IDE maps to config files |
| [CocoIndex Code](docs/cocoindex-code.md) | Code indexing with cocoindex | Code search and indexing setup |

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
│   ├── skills/             # Agent skills (249+)
│   ├── workflows/          # Workflow definitions
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
    ├── skills.md           # Skill reference
    ├── commands.md         # Command reference
    ├── mcp.md              # MCP server documentation
    ├── TODO.md             # IDE config matrix
    └── cocoindex-code.md   # Code indexing docs
```

## License

MIT
