---
applyTo: "**/*.pl"
---
# Perl Hooks

> This file extends [common/hooks.instructions.md](../common/hooks.instructions.md) with Perl-specific content.

## PostToolUse Hooks

Configure in `~/.agents/settings.json`:

- **perltidy**: Auto-format `.pl` and `.pm` files after edit
- **perlcritic**: Run lint check after editing `.pm` files

## Warnings

- Warn about `print` in non-script `.pm` files — use `say` or a logging module (e.g., `Log::Any`)
