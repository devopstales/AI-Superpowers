# Commands Reference

Slash commands and custom commands across supported AI coding IDEs.

## Overview

| IDE | Command Location | Count |
|-----|-----------------|-------|
| Opencode | `.opencode/commands/` | 92 |
| Kilo | `.kilo/commands/` | 83 |
| Qwen | `.qwen/commands/` | 9 |
| Cursor | `.cursor/commands/` | — |
| Copilot | `.github/prompts/` | — |

## Command Categories

### Build & Compile

| Command | Description | IDEs |
|---------|-------------|------|
| `build-fix` | Fix build and compilation errors | Opencode, Kilo |
| `cpp-build` | C++ build resolution | Opencode, Kilo |
| `go-build` | Go build resolution | Opencode, Kilo |
| `gradle-build` | Gradle build resolution | Opencode, Kilo |
| `kotlin-build` | Kotlin build resolution | Opencode, Kilo |
| `rust-build` | Rust build resolution | Opencode, Kilo |

### Code Review

| Command | Description | IDEs |
|---------|-------------|------|
| `code-review` | General code review | Opencode, Kilo |
| `cpp-review` | C++ code review | Opencode, Kilo |
| `go-review` | Go code review | Opencode, Kilo |
| `kotlin-review` | Kotlin code review | Opencode, Kilo |
| `python-review` | Python code review | Opencode, Kilo |
| `rust-review` | Rust code review | Opencode, Kilo |

### Testing

| Command | Description | IDEs |
|---------|-------------|------|
| `tdd` | Test-driven development workflow | Opencode, Kilo |
| `e2e` | End-to-end testing | Opencode, Kilo |
| `test-coverage` | Test coverage analysis | Opencode, Kilo |
| `cpp-test` | C++ testing | Opencode, Kilo |
| `go-test` | Go testing | Opencode, Kilo |
| `kotlin-test` | Kotlin testing | Opencode, Kilo |
| `rust-test` | Rust testing | Opencode, Kilo |

### Security Scanning

| Command | Description | IDEs |
|---------|-------------|------|
| `security` | Security review and audit | Opencode, Kilo |
| `semgrep-scan` | Run Semgrep security analysis | Opencode, Kilo, Qwen |
| `trivy-scan` | Run Trivy vulnerability scan | Opencode, Kilo, Qwen |

### OpenSpec Workflow

| Command | Description | IDEs |
|---------|-------------|------|
| `opsx-explore` | Explore requirements and ideas | Opencode, Kilo, Qwen |
| `opsx-propose` | Propose a new change | Opencode, Kilo, Qwen |
| `opsx-apply` | Apply/implement a change | Opencode, Kilo, Qwen |
| `opsx-verify` | Verify implementation against spec | Opencode, Kilo, Qwen |
| `opsx-archive` | Archive a completed change | Opencode, Kilo, Qwen |
| `opsx-sync` | Sync delta specs to main specs | Opencode, Kilo, Qwen |
| `opsx-onboard` | Guided OpenSpec onboarding | Opencode, Kilo, Qwen |

### SDD Workflow

| Command | Description | IDEs |
|---------|-------------|------|
| `sdd-init` | Initialize SDD workflow | Opencode, Kilo |
| `sdd-new` | Create new SDD spec | Opencode |
| `sdd-explore` | SDD explore mode | Opencode, Kilo |
| `sdd-apply` | Apply SDD tasks | Opencode, Kilo |
| `sdd-continue` | Continue SDD implementation | Opencode |
| `sdd-verify` | Verify SDD implementation | Opencode, Kilo |
| `sdd-archive` | Archive SDD change | Opencode, Kilo |
| `sdd-ff` | SDD fast-forward | Opencode |

### GAN (Generate-Adapt-Navigate)

| Command | Description | IDEs |
|---------|-------------|------|
| `gan-design` | GAN design phase | Opencode, Kilo |
| `gan-build` | GAN build/implementation | Opencode, Kilo |

### Learning & Memory

| Command | Description | IDEs |
|---------|-------------|------|
| `learn` | Save session patterns as skills | Opencode, Kilo |
| `learn-eval` | Evaluate learned skills | Opencode, Kilo |
| `instinct-import` | Import instincts/skills | Opencode, Kilo |
| `instinct-export` | Export instincts/skills | Opencode, Kilo |
| `instinct-status` | Check instinct/skill status | Opencode, Kilo |

### Agent Loop Management

| Command | Description | IDEs |
|---------|-------------|------|
| `loop-start` | Start autonomous agent loop | Opencode, Kilo |
| `loop-status` | Check loop progress | Opencode, Kilo |
| `santa-loop` | Santa autonomous loop | Opencode, Kilo |

### Multi-Agent Orchestration

| Command | Description | IDEs |
|---------|-------------|------|
| `orchestrate` | Orchestrate multi-agent workflow | Opencode, Kilo |
| `devfleet` | DevFleet multi-agent dispatch | Opencode, Kilo |
| `multi-plan` | Multi-agent planning | Opencode, Kilo |
| `multi-backend` | Multi-backend development | Opencode, Kilo |
| `multi-frontend` | Multi-frontend development | Opencode, Kilo |
| `multi-workflow` | Multi-workflow execution | Opencode, Kilo |

### Planning & Design

| Command | Description | IDEs |
|---------|-------------|------|
| `plan` | Feature planning and task breakdown | Opencode, Kilo |
| `definition` | Requirements definition | Opencode, Kilo |
| `aside` | Side conversation/context switch | Opencode, Kilo |

### Code Quality & Refactoring

| Command | Description | IDEs |
|---------|-------------|------|
| `refactor-clean` | Dead code cleanup and refactoring | Opencode, Kilo |
| `quality-gate` | Quality gate check | Opencode, Kilo |
| `context-budget` | Manage context window budget | Opencode, Kilo |
| `call-graph` | Generate call graph analysis | Opencode, Kilo |
| `checkpoint` | Save current state checkpoint | Opencode, Kilo |
| `claw` | Claw operation (specific tool) | Opencode, Kilo |

### Documentation

| Command | Description | IDEs |
|---------|-------------|------|
| `docs` | Fetch documentation for libraries | Opencode, Kilo |
| `update-docs` | Update project documentation | Opencode, Kilo |
| `update-codemaps` | Update code maps | Opencode, Kilo |

### Search & Discovery

| Command | Description | IDEs |
|---------|-------------|------|
| `find` | Code search and discovery | Opencode, Kilo |
| `search` | Web/code search | Opencode, Kilo |
| `index` | Update codebase index | Opencode, Kilo |

### Session Management

| Command | Description | IDEs |
|---------|-------------|------|
| `sessions` | List/manage sessions | Opencode, Kilo |
| `save-session` | Save current session state | Opencode, Kilo |
| `resume-session` | Resume saved session | Opencode, Kilo |
| `status` | Show current status | Opencode, Kilo |
| `projects` | List/manage projects | Opencode, Kilo |

### Prompt & Model Optimization

| Command | Description | IDEs |
|---------|-------------|------|
| `prompt-optimize` | Optimize prompts | Opencode, Kilo |
| `model-route` | Route to appropriate model | Opencode, Kilo |
| `evolve` | Evolve/improve patterns | Opencode, Kilo |
| `promote` | Promote patterns to skills | Opencode, Kilo |
| `prune` | Prune unused patterns | Opencode, Kilo |

### Rules & Skills Management

| Command | Description | IDEs |
|---------|-------------|------|
| `skill-create` | Create new skill | Opencode, Kilo |
| `skill-health` | Check skill health/status | Opencode, Kilo |
| `rules-distill` | Distill rules from sessions | Opencode, Kilo |
| `harness-audit` | Audit harness configuration | Opencode, Kilo |

### PRP (Product Requirements Prompt)

| Command | Description | IDEs |
|---------|-------------|------|
| `prp-prd` | Generate PRD | Opencode, Kilo |
| `prp-plan` | Plan implementation | Opencode, Kilo |
| `prp-implement` | Implement feature | Opencode, Kilo |
| `prp-pr` | Create PR | Opencode, Kilo |
| `prp-commit` | Generate commit message | Opencode, Kilo |

### Package Management

| Command | Description | IDEs |
|---------|-------------|------|
| `pm2` | PM2 process management | Opencode, Kilo |
| `setup-pm` | Setup package manager | Opencode, Kilo |

### Evaluation

| Command | Description | IDEs |
|---------|-------------|------|
| `eval` | Run evaluation suite | Opencode, Kilo |
| `verify` | Verify implementation | Opencode, Kilo |

## Qwen-Specific Commands

| Command | Description |
|---------|-------------|
| `opsx-apply.md` | Apply OpenSpec change |
| `opsx-archive.md` | Archive OpenSpec change |
| `opsx-explore.md` | Explore mode |
| `opsx-onboard.md` | Onboarding |
| `opsx-propose.md` | Propose change |
| `opsx-sync.md` | Sync specs |
| `opsx-verify.md` | Verify change |
| `semgrep-scan.md` | Semgrep security scan |
| `trivy-scan.md` | Trivy vulnerability scan |

## Command Format

Commands are Markdown files that define behavior. Example structure:

```markdown
# Command Name

Description of what this command does.

## Usage

How to invoke and use the command.

## Steps

1. Step one
2. Step two
3. Step three

## Output

Expected output format.
```

## IDE Command Locations

| IDE | Path | Notes |
|-----|------|-------|
| Opencode | `.opencode/commands/*.md` | Full command library |
| Kilo | `.kilo/commands/*.md` | Subset of Opencode commands |
| Qwen | `.qwen/commands/*.md` | OpenSpec + security scans |
| Cursor | `.cursor/commands/` | Custom commands (if any) |
| Copilot | `.github/prompts/` | GitHub prompt files |

## Skill vs Command

| Aspect | Skill | Command |
|--------|-------|---------|
| Purpose | Domain expertise & workflow patterns | Specific actionable operations |
| Format | `SKILL.md` in directory | Standalone `.md` file |
| Activation | Automatic or `skill: name` | Explicit `/command` invocation |
| Scope | Broad specialist knowledge | Narrow focused operation |
| Example | `code-reviewer` (review specialist) | `code-review` (run a review) |
