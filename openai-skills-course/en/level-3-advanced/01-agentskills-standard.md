---
title: "AgentSkills Standard (agentskills.io)"
weight: 1
bookToc: true
---

# AgentSkills Standard (agentskills.io)

## Introduction

AgentSkills is an open standard for describing AI agent skills. Published at [agentskills.io](https://agentskills.io), it defines a universal format that different AI agents can use — not just Codex.

## Why a Standard?

Without a standard, every AI agent uses its own skill format, making skills non-portable. AgentSkills solves this: **write once, use everywhere**.

## Core Principles

### 1. Folder as Skill
A skill is a regular folder. Not a package, not a container — just a folder.

### 2. SKILL.md as Entry Point
Every skill must have a `SKILL.md` in its root. This is the only required file.

### 3. YAML Frontmatter
SKILL.md starts with YAML metadata:

```yaml
---
name: skill-name
description: Skill description
---
```

### 4. agents/ Folder
Each agent can have its own config file:

```
agents/
├── openai.yaml
├── anthropic.yaml
└── other.yaml
```

### 5. Resources
Standard resource folders:
- `scripts/` — executable scripts
- `references/` — reference docs
- `assets/` — output files (templates, icons)

## Where to Learn More

- Standard website: [agentskills.io](https://agentskills.io)
- Documentation: [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills)
- Repository: [github.com/openai/skills](https://github.com/openai/skills)

## Summary

- AgentSkills is an open standard for AI agent skills
- Based on a folder with SKILL.md
- Ensures portability across agents
- Simple format: YAML frontmatter + Markdown instructions
