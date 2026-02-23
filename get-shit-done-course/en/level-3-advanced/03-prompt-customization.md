---
title: "Prompt Customization"
level: 3
lesson: 3
language: en
tags: [gsd, customization, prompts]
---

# Prompt Customization

## Introduction

GSD installs slash commands as markdown files. You can study and customize them for your needs.

## Instructions

### Where Commands Live

```
# Global install
~/.claude/commands/gsd/

# Local install
./.claude/commands/gsd/
```

Each command is a markdown file with instructions for Claude.

### Customization via CONTEXT.md

The simplest way to customize — through `/gsd:discuss-phase`. Your decisions are written to CONTEXT.md and influence all subsequent steps.

### Customization via Settings

```
/gsd:settings
```

Control which agents are enabled, model profiles, planning depth, and git strategy.

### Editing Commands Directly

For advanced users — edit the markdown command files:

1. Open a command file in `~/.claude/commands/gsd/`
2. Study the prompt structure
3. Add or modify instructions
4. Restart Claude Code

> **Warning:** GSD updates will overwrite your changes. Make backups.

### Local Overrides

Use local install for project-specific customizations:

```bash
npx get-shit-done-cc --claude --local
# Now edit ./.claude/commands/gsd/
```

Local commands take priority over global ones.

## Examples

```bash
# View command structure
ls ~/.claude/commands/gsd/

# Copy for customization
cp -r ~/.claude/commands/gsd/ ./.claude/commands/gsd/
```

## Summary

- GSD commands are markdown files
- Customization via CONTEXT.md is the simplest path
- Commands can be edited directly
- Local commands override global ones
- GSD updates overwrite customizations
