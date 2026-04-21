# Tools and dependencies (`install.sh`)

This document describes what the installer checks, what it can install automatically, and **how** each piece is installed. Behavior matches `install.sh` in this repository.

## How dependency installation is triggered

1. **Normal install** (`./install.sh -p <project>`): the script counts missing “core” and “IDE-related” CLIs, then may prompt: *Would you like to install missing dependencies?* (skipped with **`-y`**).
2. **Explicit check** (**`-d` / `--deps`**): prints **`show_dependencies`** (what is installed vs missing) and can run the same install prompt when something is missing.
3. **Optional tool CLIs** (**`-t` / `--tools`**): interactive selection of extra tools; **`install_optional_tool_clis`** runs after the dependency prompt and **before** config folders are copied. With **`-y`**, the tools prompt is skipped (no optional tools selected).

**Dry run (`-n`)** prints what would happen; it does not run installs (optional-tool block still prints `[DRY-RUN]` lines where implemented).

**Install methods** used by the script:

| Method | Command pattern | When used |
|--------|-----------------|-----------|
| **Homebrew** | `brew install <formula>` | Core packages with a Brew mapping; IDE deps; optional **engram** |
| **pip** | `pip3 install --user <pkg>` | Only if a dependency row maps to pip (core/IDE rows currently favor Brew first) |
| **npm global** | `npm install -g <pkg>` | IDE deps with an npm mapping; **dmux**; **openspec** fallback; **Kilo** CLI during setup |
| **pipx** | `pipx install …` | Optional **cocoindex-code**, **graphify** (after ensuring `pipx` exists) |
| **Trivy plugin** | `trivy plugin install mcp` | After `trivy` was missing and then installed/available |

If **Homebrew** is not installed, Brew-backed installs are skipped with a warning (see script output).

### `AGENTS.md` (hub → project)

When **at least one IDE** is selected and **`configs/AGENTS.md`** exists in the hub, the installer copies it to:

- **`AGENTS.md`** at the project root, and  
- **`AGENTS.md`** inside each selected IDE’s config directory (e.g. `.cursor/`, `.vscode/`, `.kilo/`, `.opencode/`, `.agents/`).

This runs after IDE folders are rsync’d. Uninstall does **not** remove `AGENTS.md` (may contain project edits).

---

## Core dependencies (always checked)

These are verified on every install path (unless you only use modes that exit early, e.g. `-d` without a project path).

| Name | Detection | Default install mapping in script |
|------|-----------|-------------------------------------|
| **rsync** | `rsync --version` | `brew install rsync` |
| **jq** | `jq --version` | `brew install jq` |
| **node** | `node --version` | `brew install node` |
| **python3** | `python3 --version` | `brew install python@3.12` |
| **pip3** | `pip3 --version` | *No auto-install field in the dependency row* — install Python/pip yourself if missing |
| **npx** | `npx --version` | *No auto-install field* — usually comes with Node |

---

## IDE-specific dependencies (checked when relevant)

Rows come from **`IDE_DEPENDENCIES`** in `install.sh`. A row is checked when:

- The matching **IDE is selected** (e.g. **opencode** when OpenCode is chosen), **or**
- **`openspec`** when the **openspec** optional tool is selected (special case), **or**
- **`-A` / `--all`** is used (all IDE flags are treated as selected for this list, so every row below is checked).

| Name | Detection | Install method in `install_dependencies` |
|------|-----------|------------------------------------------|
| **opencode** | `opencode --version` | `brew install opencode` |
| **openspec** | `openspec --version` | `brew install openspec` |
| **kilo** | `kilo --version` | `brew install Kilo-Org/homebrew-tap/kilo` |
| **semgrep** | `semgrep --version` | `brew install semgrep` |
| **trivy** | `trivy --version` | `brew install trivy` |
| **trivy-mcp** | `trivy plugin list` | Same Brew stack as **trivy**; after install, script may run **`trivy plugin install mcp`** |

**Note:** **`openspec`** is also installed by the **optional tools** path (see below) with **Homebrew first**, then **`npm install -g @fission-ai/openspec@latest`** if Brew fails or is unavailable. The dependency list alone uses Brew for `openspec` when you accept `install_dependencies`.

### Kilocode CLI (extra, outside `IDE_DEPENDENCIES`)

When **Kilo** setup runs, if `kilo` is not on `PATH`, the script runs:

```bash
npm install -g @kilocode/cli
```

This is independent of the Homebrew **kilo** formula above (the installer uses both patterns in different places).

---

## Optional tools (`-t` / `--tools`)

Choosing tools fills **`SELECTED_TOOLS`**. **`install_optional_tool_clis`** installs CLIs **only for selected tools**, in this order:

| Tool id | What gets installed | Method |
|---------|---------------------|--------|
| **cocoindex-code** | `cocoindex-code[full]` | **`pipx install 'cocoindex-code[full]'`** — **`pipx`** is installed first if missing (`brew install pipx`, or `pip3 install --user pipx`). Skipped if `cocoindex` / `cocoindex-code` is already on `PATH`. |
| **graphify** | PyPI package **graphifyy** | **`pipx install graphifyy`** (same `pipx` bootstrap). Skipped if `graphifyy` or `graphify` is on `PATH`. |
| **openspec** | OpenSpec CLI | **`brew install openspec`** if that succeeds; else **`npm install -g @fission-ai/openspec@latest`**. Skipped if `openspec` is already on `PATH`. |
| **dmux** | dmux CLI | **`npm install -g dmux`**. Skipped if `dmux` is on `PATH`. |
| **engram** | Engram CLI | **`brew install gentleman-programming/tap/engram`**. Skipped if `engram` is on `PATH`. |

Optional tools can also drive **hub content** (e.g. copying **`openspec/`**, **`.cocoindex_code/`**, running **`openspec init`**) when those tool ids are selected — see `install.sh` **main** flow after MCP setup.

---

## Other declarations (not wired to auto-install)

The script declares **`OPTIONAL_DEPENDENCIES`** (**pipx**, **uv**) for future or manual use; it is **not** currently iterated by `install_dependencies` or `show_dependencies`. **`pipx`** is still installed on demand inside **`ensure_pipx`** when **cocoindex-code** or **graphify** optional tools are selected.

---

## Quick reference: flags

| Flag | Effect on tools / deps |
|------|-------------------------|
| **`-d`** | Run dependency report (`show_dependencies`) and optional install prompt when counts are non-zero |
| **`-y`** | Non-interactive: skips optional **tools** prompt (`-t` selects nothing) |
| **`-t`** | Enable interactive optional **tools** selection (TTY; not in CI) |
| **`-n`** | Dry run: no real installs; optional tools section emits `[DRY-RUN]` lines |

For full CLI options, run `./install.sh -h`.
