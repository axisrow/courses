---
title: "SKILL.md Format"
weight: 4
bookToc: true
---

# SKILL.md Format

## Introduction

`SKILL.md` is the main file of any skill. It contains metadata and instructions for Claude.

## File Structure

```markdown
---
name: my-skill-name
description: Description of the skill and when to use it
---

# Skill Name

Instructions that Claude will follow.

## Examples
- Example 1
- Example 2

## Guidelines
- Guideline 1
- Guideline 2
```

## Frontmatter

The YAML block between `---` at the top. Required fields:

| Field | Description |
|-------|-------------|
| `name` | Unique identifier (lowercase, hyphens) |
| `description` | Full description of the skill and when to use it |

Optional fields:

| Field | Description |
|-------|-------------|
| `license` | License information |

## Body (Markdown)

After frontmatter, write standard Markdown with instructions, examples, and guidelines.

## Summary

- `SKILL.md` is required for every skill
- Frontmatter contains `name` and `description`
- The body contains Markdown instructions for Claude
- More specific instructions = better results
