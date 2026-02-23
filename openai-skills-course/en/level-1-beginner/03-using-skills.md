---
title: "Using Skills"
weight: 3
bookToc: true
---

# Using Skills

## Introduction

Skills in Codex work automatically. You don't need to manually "enable" a skill — Codex figures out which skill fits your request. In this lesson you'll learn how that happens.

## How Codex Picks a Skill

When you give Codex a task, it goes through three steps:

1. **Reads metadata** — checks `name` and `description` of all installed skills
2. **Selects the right one** — finds the skill whose description matches your task
3. **Loads instructions** — reads SKILL.md and carries out the task

## Usage Examples

### Example 1: Screenshot

You write:
> "Take a screenshot of my screen"

Codex finds the `screenshot` skill and executes the task.

### Example 2: GitHub

You write:
> "Check why CI is failing on my PR"

Codex activates `gh-fix-ci`, which inspects checks and proposes fixes.

### Example 3: Image Generation

You write:
> "Generate a logo for my project"

Codex uses the `imagegen` skill.

## Calling a Skill by Name

You can explicitly specify a skill with the `$` prefix:

```
$screenshot take a full-screen capture
```

## Viewing Installed Skills

To see available skills, use skill-installer:

```
$skill-installer
```

Codex will show the list with "already installed" annotations.

## Summary

- Codex automatically selects a skill based on your request
- A skill is triggered by its description in the metadata
- You can call a skill explicitly via `$skill-name`
- The skill list is available through skill-installer
