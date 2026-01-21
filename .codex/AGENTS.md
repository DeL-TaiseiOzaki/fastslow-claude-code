# Codex CLI Global Instructions

**These instructions apply to all projects using this configuration.**

## Mandatory: Load Context First

At the start of EVERY task, you MUST use the `context-loader` skill:

1. **Invoke `$context-loader`** - This loads coding rules and design decisions from `.claude/`
2. **Wait for context to load** - Understand the project's rules and constraints
3. **Then proceed with the task** - Follow the loaded rules strictly

## What context-loader Provides

- **Coding rules** from `.claude/rules/` (simplicity, type hints, security, etc.)
- **Design decisions** from `.claude/docs/DESIGN.md`
- **Library constraints** from `.claude/docs/libraries/`

## Why This Matters

You are called by Claude Code to handle complex analysis and design decisions. Claude Code already knows the project context. By loading context first, you ensure consistency between your recommendations and Claude Code's execution.

## Language Protocol

- **Thinking/Reasoning**: English
- **Code**: English (variables, functions, comments, docstrings)
- **User communication**: Japanese (when reporting back through Claude Code)
