---
title: "Installing Skills"
weight: 5
bookToc: true
---

# Installing Skills

## Introduction

Step-by-step guide for installing skills from the Anthropic repository and custom skills.

## From the Anthropic Repository

```bash
# Clone the repository
git clone https://github.com/anthropics/skills.git

# In Claude Code
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
```

## Custom Skills

### Step 1: Create a skill folder

```bash
mkdir my-skill
```

### Step 2: Create SKILL.md

```markdown
---
name: my-skill
description: My custom skill description
---

# My Skill Instructions
```

### Step 3: Connect to Claude

- **Claude Code**: place in project directory
- **Claude.ai**: upload via project settings
- **API**: include content in the request

## Summary

- Skills install via Claude Code (`/plugin`) or manually
- The Anthropic repo contains ready-made skill sets
- Custom skills need a folder with `SKILL.md`
- Skills activate automatically after installation
