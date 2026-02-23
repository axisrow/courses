---
title: "Publishing Skills"
weight: 4
bookToc: true
---

# Publishing Skills

## Introduction

You've created and tested a skill — now it's time to share it. This lesson covers publishing methods.

## Method 1: GitHub Repository

The simplest way — publish the skill in your own GitHub repository.

### Step 1: Create a Repository

```bash
mkdir my-skills && cd my-skills
git init
```

### Step 2: Add the Skill

```
my-skills/
└── csv-analyzer/
    ├── SKILL.md
    ├── agents/openai.yaml
    ├── scripts/analyze.py
    └── LICENSE.txt
```

### Step 3: Publish

```bash
git add .
git commit -m "Add csv-analyzer skill"
git remote add origin https://github.com/you/my-skills.git
git push -u origin main
```

### Step 4: Others Can Install

```
$skill-installer install https://github.com/you/my-skills/tree/main/csv-analyzer
```

## Method 2: Contributing to openai/skills

You can propose your skill to the official repository. More details in the next lesson.

## License

Every skill should include a `LICENSE.txt` file.

## Pre-publish Checklist

- [ ] Skill passes validation
- [ ] All scripts tested
- [ ] SKILL.md has a clear description
- [ ] `agents/openai.yaml` filled in
- [ ] `LICENSE.txt` included
- [ ] No secrets (keys, passwords, tokens)
- [ ] No extra files

## Summary

- Publish skills via GitHub repositories
- Skill-installer can install from any GitHub repo
- Include a license with every skill
- Check for secrets before publishing
