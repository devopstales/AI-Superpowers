---
applyTo: "**/*.py"
---
# Python Hooks

> This file extends [common/hooks.instructions.md](../common/hooks.instructions.md) with Python specific content.

## PostToolUse Hooks

Configure in `~/.agents/settings.json`:

- **black/ruff**: Auto-format `.py` files after edit
- **mypy/pyright**: Run type checking after editing `.py` files

## Warnings

- Warn about `print()` statements in edited files (use `logging` module instead)
