---
title: "SKILL.md Structure"
weight: 3
bookToc: true
---

# SKILL.md Structure

## Introduction

SKILL.md is the main file of every skill. Codex reads it to understand what to do and how. In this lesson we break down its structure.

## Overall Structure

SKILL.md has two parts:

1. **YAML frontmatter** — metadata (name and description)
2. **Body** — Markdown instructions

## YAML Frontmatter

The frontmatter sits at the very beginning between `---`:

```yaml
---
name: my-skill
description: Skill description — when and why to use it. This is the most important part because Codex uses it to decide whether to activate the skill.
---
```

### The `name` Field

- The skill name
- Use lowercase letters, digits, and hyphens
- Examples: `pdf`, `gh-fix-ci`, `notion-meeting-intelligence`

### The `description` Field

- The most important part of the skill!
- Describes **what** the skill does and **when** to use it
- Codex reads this for every request to decide which skill to activate
- Be thorough: list all usage scenarios

**Good example:**
```yaml
description: "Comprehensive document creation, editing, and analysis with support for tracked changes, comments, and formatting. Use when Codex needs to: (1) create a new document, (2) modify content, (3) work with tracked changes."
```

## Body

After the frontmatter come the Markdown instructions:

```markdown
# Skill Name

## Overview
Brief description of what the skill does.

## How to Use
Step-by-step instructions.

## Scripts
Description of available scripts and when to run them.
```

### Key Rules for the Body:

- **Be concise** — the context window is limited
- **Don't duplicate** — don't repeat "when to use" from description
- **Imperative style** — write "Run", "Check", not "The skill does"
- **Under 500 lines** — if longer, move content to `references/`

## Summary

- SKILL.md consists of frontmatter (name + description) and body (instructions)
- The description is the most important part — it determines when the skill activates
- The body should be concise and practical
- Use imperative style
