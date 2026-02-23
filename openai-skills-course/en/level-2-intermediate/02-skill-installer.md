---
title: "Skill-installer In Depth"
weight: 2
bookToc: true
---

# Skill-installer In Depth

## Introduction

Skill-installer is a built-in system skill that manages installation of other skills. In this lesson we explore all its capabilities.

## Main Commands

### List Available Skills

```
$skill-installer
```

Output:
```
Skills from openai/skills:
1. figma
2. screenshot (already installed)
3. gh-fix-ci
...
Which ones would you like installed?
```

### Install a Curated Skill by Name

```
$skill-installer gh-address-comments
```

### Install from a Different Folder

```
$skill-installer install the create-plan skill from the .experimental folder
```

### Install from Any GitHub Repository

```
$skill-installer install https://github.com/user/repo/tree/main/my-skill
```

## What Happens During Installation

1. Skill-installer downloads the skill folder from GitHub
2. Copies it to `~/.codex/skills/skill-name/`
3. If already installed — installation is aborted
4. Restart Codex after installation

## Private Repositories

For skills in private repositories:

1. Skill-installer tries your existing git credentials
2. You can set `GITHUB_TOKEN` or `GH_TOKEN`
3. HTTPS is tried first, then SSH

## Under the Hood

Skill-installer uses three Python scripts:

- `list-skills.py` — fetches the skill list via GitHub API
- `install-skill-from-github.py` — downloads and installs a skill
- `github_utils.py` — GitHub helper functions

## Summary

- Skill-installer is a universal tool for installing skills
- Works with curated, experimental, and third-party skills
- Supports private repositories
- Always restart Codex after installation
