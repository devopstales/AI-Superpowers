# Skills Reference

Complete skill library for AI coding assistants. Skills are specialized agent definitions that encode domain expertise, workflows, and best practices.

## Overview

| Metric | Count |
|--------|-------|
| Total Skills | 249 |
| Location | `.agents/skills/` |
| Format | `SKILL.md` inside directories, or standalone `.md` files |
| Shared Config | `.agents/skills/_shared/` |

## Skill Format

Each skill is a Markdown file with YAML frontmatter:

```yaml
---
name: skill-name
description: Short description of what this skill does and when to use it.
tools: ["Read", "Write", "Edit", "Bash", "Grep", "Glob"]
model: sonnet  # or opus, haiku
---
```

### Key Fields

| Field | Description |
|-------|-------------|
| `name` | Unique identifier (kebab-case) |
| `description` | When and how to activate the skill |
| `tools` | Allowed tool capabilities |
| `model` | Recommended model tier (`sonnet`, `opus`, `haiku`) |

## Skill Categories

### Architecture & Design

| Skill | Description |
|-------|-------------|
| `architect` | System design, scalability, technical decision-making |
| `architecture` | Requirements analysis, trade-off evaluation, ADR documentation |
| `blueprint` | Project blueprint and structure planning |
| `database-design` | Schema design, indexing strategy, ORM selection |
| `database-migrations` | Schema changes, data migrations, rollbacks, zero-downtime deployments |
| `frontend-design` | Design thinking for web UI — components, layouts, color schemes, typography |
| `mobile-design` | Mobile-first design for iOS/Android — touch interaction, platform conventions |
| `api-design` | REST API patterns — resource naming, status codes, pagination, filtering, error responses |
| `api-patterns` | REST vs GraphQL vs tRPC selection, response formats, versioning, pagination |

### Code Quality & Review

| Skill | Description |
|-------|-------------|
| `code-reviewer` | Expert code review for quality, security, maintainability |
| `code-review-checklist` | Code review guidelines — quality, security, best practices |
| `coding-standards` | Universal coding standards for TypeScript, JavaScript, React, Node.js |
| `clean-code` | Pragmatic standards — concise, direct, no over-engineering |
| `lint-and-validate` | Automatic quality control, linting, static analysis |
| `security-reviewer` | Vulnerability detection — secrets, SSRF, injection, OWASP Top 10 |
| `security-review` | Comprehensive security checklist and patterns |
| `security-scan` | Scan Claude Code configuration for vulnerabilities |
| `semgrep-security` | Semgrep static analysis for security and code quality |
| `trivy-security` | Trivy scanner — vulnerabilities, misconfigurations, secrets, SBOM |
| `vulnerability-scanner` | OWASP 2025, supply chain security, attack surface mapping |

### Language-Specific Patterns

#### Python

| Skill | Description |
|-------|-------------|
| `python-patterns` | Pythonic idioms, PEP 8, type hints, best practices |
| `python-testing` | pytest, TDD methodology, fixtures, mocking, coverage |
| `python-reviewer` | PEP 8 compliance, Pythonic idioms, type hints, security |
| `django-patterns` | Django architecture, REST API with DRF, ORM, caching, signals |
| `django-security` | Django security — auth, CSRF, SQL injection, XSS, deployment |
| `django-tdd` | Django testing with pytest-django, factory_boy, coverage |
| `django-verification` | Verification loop — migrations, linting, tests, security scans |
| `pytorch-build-resolver` | PyTorch runtime, CUDA, training error resolution |

#### TypeScript/JavaScript

| Skill | Description |
|-------|-------------|
| `typescript-reviewer` | Type safety, async correctness, Node/web security |
| `frontend-patterns` | React, Next.js, state management, performance, UI patterns |
| `backend-patterns` | Node.js, Express, Next.js API routes patterns |
| `nodejs-best-practices` | Framework selection, async patterns, security, architecture |
| `react-best-practices` | React/Next.js performance optimization from Vercel Engineering |
| `tailwind-patterns` | Tailwind CSS v4 — CSS-first config, container queries, design tokens |
| `nextjs-turbopack` | Next.js 16+ and Turbopack — incremental bundling, FS caching |

#### Java/Kotlin

| Skill | Description |
|-------|-------------|
| `java-reviewer` | Java/Spring Boot review — layered architecture, JPA, security, concurrency |
| `java-build-resolver` | Java/Maven/Gradle build and compilation error resolution |
| `java-coding-standards` | Spring Boot standards — naming, immutability, Optional, streams |
| `springboot-patterns` | Spring Boot architecture, REST API, layered services, caching |
| `springboot-security` | Spring Security — authn/authz, validation, CSRF, secrets, rate limiting |
| `springboot-tdd` | TDD for Spring Boot — JUnit 5, Mockito, Testcontainers, JaCoCo |
| `springboot-verification` | Verification loop — build, static analysis, tests, security scans |
| `jpa-patterns` | JPA/Hibernate — entity design, relationships, query optimization |
| `kotlin-patterns` | Idiomatic Kotlin — coroutines, null safety, DSL builders |
| `kotlin-reviewer` | Kotlin/Android/KMP review — coroutines, Compose, clean architecture |
| `kotlin-build-resolver` | Kotlin/Gradle build and compilation error resolution |
| `kotlin-testing` | Kotest, MockK, coroutine testing, property-based testing |
| `kotlin-coroutines-flows` | Coroutines and Flow — structured concurrency, StateFlow, error handling |
| `kotlin-ktor-patterns` | Ktor server — routing DSL, plugins, auth, Koin DI, WebSockets |
| `kotlin-exposed-patterns` | JetBrains Exposed ORM — DSL queries, DAO, transactions, Flyway |
| `android-clean-architecture` | Clean Architecture for Android/KMP — modules, UseCases, Repositories |
| `compose-multiplatform-patterns` | Compose Multiplatform — state, navigation, theming, platform UI |

#### Go

| Skill | Description |
|-------|-------------|
| `go-reviewer` | Idiomatic Go review — concurrency, error handling, performance |
| `go-build-resolver` | Go build, vet, compilation error resolution |
| `go-testing` | Go testing patterns — table-driven, subtests, benchmarks, fuzzing |
| `golang-patterns` | Idiomatic Go patterns, best practices, conventions |
| `golang-testing` | Go testing with TDD methodology, idiomatic practices |

#### Rust

| Skill | Description |
|-------|-------------|
| `rust-reviewer` | Rust review — ownership, lifetimes, error handling, unsafe, idioms |
| `rust-build-resolver` | Rust build/cargo compilation error resolution |
| `rust-patterns` | Idiomatic Rust — ownership, error handling, traits, concurrency |
| `rust-pro` | Master Rust 1.75+ with modern async patterns and advanced type system |
| `rust-testing` | Rust testing — unit, integration, async, property-based, coverage |

#### C++

| Skill | Description |
|-------|-------------|
| `cpp-reviewer` | C++ review — memory safety, modern idioms, concurrency, performance |
| `cpp-build-resolver` | C++ build, CMake, compilation error resolution |
| `cpp-coding-standards` | C++ Core Guidelines — modern, safe, idiomatic practices |
| `cpp-testing` | GoogleTest/CTest, coverage, sanitizers |

#### Swift/iOS

| Skill | Description |
|-------|-------------|
| `swiftui-patterns` | SwiftUI — state management with @Observable, navigation, performance |
| `swift-concurrency-6-2` | Swift 6.2 Concurrency — single-threaded default, @concurrent, isolated conformances |
| `swift-actor-persistence` | Thread-safe data persistence with actors — cache + file storage |
| `swift-protocol-di-testing` | Protocol-based DI for testable Swift — mock FS, network, APIs |
| `foundation-models-on-device` | Apple FoundationModels — text generation, tool calling, snapshot streaming |
| `liquid-glass-design` | iOS 26 Liquid Glass — dynamic glass material, blur, reflection |

#### PHP/Laravel

| Skill | Description |
|-------|-------------|
| `laravel-patterns` | Laravel — routing, Eloquent ORM, service layers, queues, events |
| `laravel-security` | Laravel security — auth, validation, CSRF, mass assignment, rate limiting |
| `laravel-tdd` | Laravel TDD — PHPUnit, Pest, factories, database testing, coverage |
| `laravel-verification` | Verification loop — env, linting, static analysis, tests, security |
| `laravel-plugin-discovery` | Discover Laravel packages via LaraPlugins.io MCP |

#### Perl

| Skill | Description |
|-------|-------------|
| `perl-patterns` | Modern Perl 5.36+ idioms and best practices |
| `perl-security` | Perl security — taint mode, input validation, safe process execution |
| `perl-testing` | Perl testing — Test2::V0, Test::More, prove, coverage, TDD |

#### Flutter

| Skill | Description |
|-------|-------------|
| `flutter-reviewer` | Flutter/Dart review — widget patterns, state management, performance, accessibility |

### Testing

| Skill | Description |
|-------|-------------|
| `tdd-guide` | TDD specialist — write-tests-first, Red-Green-Refactor, 80%+ coverage |
| `tdd-workflow` | TDD principles — RED-GREEN-REFACTOR cycle |
| `tdd2-workflow` | Extended TDD workflow patterns |
| `testing-patterns` | Unit, integration, mocking strategies |
| `e2e-testing` | Playwright E2E — Page Object Model, CI/CD, artifacts, flaky tests |
| `e2e-runner` | End-to-end testing with Vercel Agent Browser/Playwright — journey management |
| `webapp-testing` | Web application testing — E2E, Playwright, deep audit |
| `ai-regression-testing` | Regression testing for AI-assisted development — sandbox-mode API testing |

### AI Agent & LLM Patterns

| Skill | Description |
|-------|-------------|
| `agent-harness-construction` | Design agent action spaces, tool definitions, observation formatting |
| `agentic-engineering` | Agentic engineer — eval-first execution, decomposition, cost-aware routing |
| `ai-first-engineering` | Engineering operating model for AI agent teams |
| `app-builder` | Main application builder — creates full-stack apps from natural language |
| `autonomous-loops` | Autonomous Claude Code loops — sequential pipelines to RFC-driven multi-agent DAG |
| `claude-api` | Anthropic Claude API — Messages, streaming, tool use, vision, extended thinking, batches |
| `claude-devfleet` | Orchestrate multi-agent tasks via Claude DevFleet — plan, dispatch, monitor |
| `continuous-agent-loop` | Continuous autonomous agent loops with quality gates and recovery controls |
| `continuous-learning` | Extract reusable patterns from sessions and save as learned skills |
| `continuous-learning-v2` | Instinct-based learning — observes sessions, creates instincts with confidence scoring |
| `cost-aware-llm-pipeline` | Cost optimization — model routing by complexity, budget tracking, retry logic |
| `data-scraper-agent` | Automated data collection agent — scrape, enrich, store, learn from feedback |
| `dmux-workflows` | Multi-agent orchestration via dmux (tmux pane manager) |
| `enterprise-agent-ops` | Long-lived agent workloads with observability, security, lifecycle management |
| `eval-harness` | Formal evaluation framework — eval-driven development (EDD) |
| `game-development` | Game development orchestrator — routes to platform-specific skills |
| `gan-evaluator` | GAN Harness Evaluator — tests live app, scores against rubric |
| `gan-generator` | GAN Harness Generator — implements features, iterates until quality met |
| `gan-planner` | GAN Harness Planner — expands prompts into full product specifications |
| `harness-optimizer` | Analyze and improve local agent harness configuration |
| `intelligent-routing` | Automatic agent selection and intelligent task routing |
| `iterative-retrieval` | Progressive context retrieval for subagent context problem |
| `loop-operator` | Operate autonomous agent loops, monitor progress, intervene safely |
| `mcp-builder` | MCP server building — tool design, resource patterns, best practices |
| `mcp-server-patterns` | Build MCP servers with Node/TypeScript — tools, resources, prompts |
| `parallel-agents` | Multi-agent orchestration — independent tasks, different domain expertise |
| `ralphinho-rfc-pipeline` | RFC-driven multi-agent DAG execution with quality gates and merge queues |
| `team-builder` | Interactive agent picker for composing and dispatching parallel teams |
| `token-budget-advisor` | Token budget management and optimization |

### OpenSpec & SDD Workflows

| Skill | Description |
|-------|-------------|
| `openspec-apply-change` | Implement tasks from an OpenSpec change |
| `openspec-archive-change` | Archive completed change in experimental workflow |
| `openspec-explore` | Explore mode — thinking partner for ideas and requirements |
| `openspec-onboard` | Guided onboarding for OpenSpec — complete workflow cycle |
| `openspec-propose` | Propose new change with all artifacts in one step |
| `openspec-sync-specs` | Sync delta specs from change to main specs |
| `openspec-verify-change` | Verify implementation matches change artifacts |
| `sdd-apply` | Apply SDD design/development workflow |
| `sdd-archive` | Archive SDD change |
| `sdd-design` | SDD design phase |
| `sdd-explore` | SDD explore mode |
| `sdd-init` | Initialize SDD workflow |
| `sdd-propose` | SDD propose phase |
| `sdd-spec` | SDD specification |
| `sdd-tasks` | SDD task management |
| `sdd-verify` | SDD verification |

### Content & Writing

| Skill | Description |
|-------|-------------|
| `article-writing` | Articles, guides, blog posts, tutorials, newsletters |
| `brand-voice` | Build style profile from real posts, reuse across content workflows |
| `content-engine` | Platform-native content systems — X, LinkedIn, TikTok, YouTube |
| `crosspost` | Multi-platform distribution — X, LinkedIn, Threads, Bluesky |
| `fal-ai-media` | Media generation via fal.ai — image, video, audio AI |
| `frontend-slides` | HTML presentations — animation-rich, from scratch or PPTX |
| `video-editing` | AI-assisted video editing — cutting, structuring, FFmpeg, Remotion |

### Research & Intelligence

| Skill | Description |
|-------|-------------|
| `deep-research` | Multi-source research via firecrawl/exa MCPs — web search, synthesis, citations |
| `docs-lookup` | Fetch current documentation via Context7 MCP |
| `documentation-lookup` | Library/framework docs via Context7 MCP |
| `documentation-templates` | Documentation structure — README, API docs, code comments |
| `exa-search` | Neural search via Exa MCP — web, code, company research |
| `market-research` | Market research, competitive analysis, due diligence, industry intelligence |
| `search-first` | Research-before-coding — search for existing tools before writing |

### DevOps & Infrastructure

| Skill | Description |
|-------|-------------|
| `bash-linux` | Bash/Linux patterns — critical commands, piping, error handling, scripting |
| `bun-runtime` | Bun as runtime, package manager, bundler, test runner |
| `clickhouse-io` | ClickHouse database — query optimization, analytics, data engineering |
| `database-reviewer` | PostgreSQL specialist — query optimization, schema design, performance |
| `deployment-patterns` | CI/CD pipelines, Docker, health checks, rollback, production readiness |
| `deployment-procedures` | Safe deployment workflows, rollback strategies, verification |
| `docker-patterns` | Docker/Compose — local dev, security, networking, volumes, multi-service |
| `performance-optimizer` | Performance analysis — bottlenecks, slow code, bundle sizes, runtime |
| `performance-profiling` | Performance profiling — measurement, analysis, optimization |
| `postgres-patterns` | PostgreSQL — query optimization, schema design, indexing, security |
| `powershell-windows` | PowerShell Windows patterns — syntax, error handling |
| `server-management` | Process management, monitoring strategy, scaling decisions |

### Planning & Communication

| Skill | Description |
|-------|-------------|
| `brainstorming` | Socratic questioning protocol — mandatory for complex/unclear requests |
| `chief-of-staff` | Personal communication chief of staff — triage email, Slack, LINE, Messenger |
| `connections-optimizer` | Reorganize X/LinkedIn network — prune, recommend, warm outreach |
| `investor-materials` | Pitch decks, one-pagers, investor memos, financial models |
| `investor-outreach` | Cold emails, warm intros, follow-ups, investor communications |
| `lead-intelligence` | AI-native lead intelligence — signal scoring, warm path discovery, outreach |
| `plan-writing` | Structured task planning with breakdowns, dependencies, verification |
| `planner` | Expert planning for complex features and refactoring |
| `prompt-optimizer` | Prompt optimization and refinement |

### Specialized Domains

| Skill | Description |
|-------|-------------|
| `carrier-relationship-management` | Carrier relationship management |
| `customs-trade-compliance` | Customs trade compliance |
| `energy-procurement` | Energy procurement operations |
| `google-workspace-ops` | Google Drive, Docs, Sheets, Slides operations |
| `healthcare-reviewer` | Healthcare app review — clinical safety, CDSS accuracy, PHI compliance |
| `inventory-demand-planning` | Inventory and demand planning |
| `logistics-exception-management` | Logistics exception management |
| `nutrient-document-processing` | Nutrient DWS API — PDF, DOCX, XLSX, PPTX, HTML processing |
| `production-scheduling` | Production scheduling |
| `quality-nonconformance` | Quality nonconformance management |
| `returns-reverse-logistics` | Returns and reverse logistics |
| `visa-doc-translate` | Translate visa application documents to bilingual PDF |
| `x-api` | X/Twitter API — posting, threads, search, analytics |

### Security & Compliance

| Skill | Description |
|-------|-------------|
| `red-team-tactics` | Red team tactics based on MITRE ATT&CK — attack phases, evasion, reporting |
| `geo-fundamentals` | Generative Engine Optimization for AI search engines |
| `seo-fundamentals` | SEO fundamentals, E-E-A-T, Core Web Vitals, Google algorithms |
| `i18n-localization` | Internationalization — translation management, locale files, RTL support |

### Refactoring & Maintenance

| Skill | Description |
|-------|-------------|
| `build-error-resolver` | Build and TypeScript error resolution — minimal diffs, get build green |
| `refactor-cleaner` | Dead code cleanup — remove unused code, duplicates, safe refactoring |
| `plankton-code-quality` | Write-time quality enforcement — auto-format, lint, Claude-powered fixes |

### Open Source Pipeline

| Skill | Description |
|-------|-------------|
| `opensource-forker` | Fork projects for open-sourcing — strip secrets, replace references, clean history |
| `opensource-sanitizer` | Verify fork is sanitized — scan for secrets, PII, internal references |
| `opensource-packager` | Generate open-source packaging — CLAUDE.md, setup.sh, README, LICENSE |

### Miscellaneous

| Skill | Description |
|-------|-------------|
| `ccc` | Code search and indexing via cocoindex-code |
| `configure-ecc` | Interactive installer for Everything Claude Code |
| `content-hash-cache-pattern` | Cache expensive file processing with SHA-256 content hashes |
| `everything-claude-code` | Development conventions for everything-claude-code |
| `foundation-models-on-device` | Apple FoundationModels framework for on-device LLM |
| `regex-vs-llm-structured-text` | Decision framework — regex vs LLM for parsing structured text |
| `skill-creator` | Create new skills |
| `skill-stocktake` | Skill inventory and stocktake |
| `strategic-compact` | Strategic context compaction at logical intervals |
| `systematic-debugging` | 4-phase debugging methodology — root cause analysis, evidence-based verification |
| `verification-loop` | Comprehensive verification system for Claude Code sessions |
| `web-design-guidelines` | Review UI code for Web Interface Guidelines compliance |
| `workspace-surface-audit` | Audit active repo, MCP servers, plugins, connectors, harness setup |

## Shared Configuration

Located in `.agents/skills/_shared/`:

| File | Description |
|------|-------------|
| `engram-convention.md` | Engram MCP integration conventions |
| `openspec-convention.md` | OpenSpec workflow conventions |
| `persistence-contract.md` | Data persistence contract definitions |
| `sdd-phase-common.md` | SDD phase common patterns |

## IDE Skill Mapping

Different IDEs reference skills from different locations:

| IDE | Skill Location |
|-----|---------------|
| Copilot | `.agents/skills/` |
| Cursor | `.agents/skills/` |
| Kilo | `.kilo/skills/` |
| Opencode | `.opencode/skills/` |
| Antigravity | `.agents/skills/` |

## Usage Patterns

### When to Use Skills

1. **Proactive Activation** — Skills with "Use PROACTIVELY" should be triggered automatically when conditions match
2. **Explicit Invocation** — Reference via `skill: name` in conversation
3. **Automatic Routing** — `intelligent-routing` skill auto-selects appropriate specialists

### Skill Activation Triggers

| Trigger Pattern | Activated Skill |
|----------------|-----------------|
| "review my code" | `code-reviewer` |
| "build an app" | `app-builder` |
| "write tests" | `tdd-guide` |
| "design a system" | `architect` |
| "find docs for X" | `docs-lookup` |
| "fix build errors" | `{language}-build-resolver` |
| "security review" | `security-reviewer` |
| "optimize performance" | `performance-optimizer` |
| "refactor" | `refactor-cleaner` |
| "plan this feature" | `planner` |

## Model Routing

Skills recommend specific model tiers:

| Model | Use Case |
|-------|----------|
| `opus` | Complex architecture decisions, system design |
| `sonnet` | General coding, review, testing, patterns |
| `haiku` | Simple tasks, quick lookups |
