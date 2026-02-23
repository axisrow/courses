---
title: "What Are Skills"
weight: 1
bookToc: true
---

# What Are Skills

## Introduction

Skills are folders of instructions, scripts, and resources that Claude loads dynamically to improve performance on specialized tasks. Skills teach Claude how to complete specific tasks in a repeatable way.

## Why Skills Matter

Without skills, Claude works from general knowledge. Skills allow you to:

- **Standardize** — define a consistent process for repeating tasks
- **Specialize** — teach Claude to work with specific tools and formats
- **Scale** — one skill can be shared across your entire team

## Use Cases

- Creating documents following company brand guidelines
- Analyzing data using organization-specific workflows
- Automating personal tasks
- Generating algorithmic art
- Testing web applications

## Skill Structure

Each skill is a folder containing at least one `SKILL.md` file:

```
my-skill/
├── SKILL.md          # Main skill file
├── scripts/          # Helper scripts (optional)
├── examples/         # Examples (optional)
└── LICENSE.txt       # License (optional)
```

The `SKILL.md` file includes:

1. **Metadata** (frontmatter) — name and description
2. **Instructions** — what Claude should do
3. **Examples** — usage samples
4. **Guidelines** — constraints and recommendations

## Summary

- Skills extend Claude's capabilities for specialized tasks
- Skills live in folders with a `SKILL.md` file
- They standardize and improve Claude's work
- You can create your own or use pre-built skills
