---
applyTo: "**/*.kt"
---
# Kotlin Hooks

> This file extends [common/hooks.instructions.md](../common/hooks.instructions.md) with Kotlin-specific content.

## PostToolUse Hooks

Configure in `~/.agents/settings.json`:

- **ktfmt/ktlint**: Auto-format `.kt` and `.kts` files after edit
- **detekt**: Run static analysis after editing Kotlin files
- **./gradlew build**: Verify compilation after changes
