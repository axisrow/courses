---
title: "System Skills (.system)"
weight: 4
bookToc: true
---

# System Skills (.system)

## Introduction

System skills are built into Codex and available immediately after installation. They live in the `.system` folder and require no separate installation.

## Available System Skills

There are currently two system skills in Codex:

### 1. skill-installer

**What it does:** Installs new skills into Codex from the openai/skills repository or any GitHub repository.

**When to use:**
- You want to see which skills are available
- You want to install a curated or experimental skill
- You want to install a skill from a third-party repository

**Example:**

```
$skill-installer show available skills
```

```
$skill-installer install gh-fix-ci
```

### 2. skill-creator

**What it does:** Helps create new skills. Guides you through the entire process from idea to finished skill.

**When to use:**
- You want to create a custom skill
- You want to update an existing skill

**Example:**

```
$skill-creator create a skill for database operations
```

## skill-installer Structure

```
skill-installer/
├── SKILL.md
├── agents/openai.yaml
├── scripts/
│   ├── list-skills.py
│   ├── install-skill-from-github.py
│   └── github_utils.py
└── LICENSE.txt
```

## skill-creator Structure

```
skill-creator/
├── SKILL.md
├── agents/openai.yaml
├── scripts/
│   ├── init_skill.py
│   ├── generate_openai_yaml.py
│   └── quick_validate.py
└── references/
    └── openai_yaml.md
```

## Summary

- Codex ships with two system skills: skill-installer and skill-creator
- skill-installer installs skills from GitHub
- skill-creator helps you build your own skills
- System skills need no installation — they work out of the box
