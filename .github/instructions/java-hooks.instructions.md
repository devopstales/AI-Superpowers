---
applyTo: "**/*.java"
---
# Java Hooks

> This file extends [common/hooks.instructions.md](../common/hooks.instructions.md) with Java-specific content.

## PostToolUse Hooks

Configure in `~/.agents/settings.json`:

- **google-java-format**: Auto-format `.java` files after edit
- **checkstyle**: Run style checks after editing Java files
- **./mvnw compile** or **./gradlew compileJava**: Verify compilation after changes
