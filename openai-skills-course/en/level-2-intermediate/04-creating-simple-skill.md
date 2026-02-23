---
title: "Creating a Simple Skill"
weight: 4
bookToc: true
---

# Creating a Simple Skill

## Introduction

In this lesson we will create our first skill from scratch using the system skill-creator.

## Step 1: Come Up with an Idea

A good skill solves a specific, recurring task. Examples:

- Formatting reports by company template
- Checking code against team standards
- Generating documentation in a specific style

For this lesson we'll create a **greeting** skill — greeting users in different languages.

## Step 2: Initialize the Skill

Use `init_skill.py` from skill-creator:

```bash
python scripts/init_skill.py greeting --path ./skills
```

This creates:

```
skills/greeting/
├── SKILL.md
└── agents/
    └── openai.yaml
```

## Step 3: Write SKILL.md

```markdown
---
name: greeting
description: Greet users in different languages. Use when a user asks to greet someone, create a welcome message, or translate a greeting.
---

# Greeting

Create greetings in different languages.

## Supported Languages

- English: "Hello, {name}! Welcome!"
- Русский: «Привет, {name}! Добро пожаловать!»
- 中文: "{name}，你好！欢迎！"
- Español: "¡Hola, {name}! ¡Bienvenido!"

## Instructions

1. Determine the target language from context
2. Insert the user's name into the template
3. If no language is specified, default to English
```

## Step 4: Configure openai.yaml

```yaml
display_name: "Greeting"
short_description: "Greetings in multiple languages"
default_prompt: "Greet the user"
```

## Step 5: Validate

```bash
python scripts/quick_validate.py ./skills/greeting
```

## Step 6: Install

```bash
cp -r ./skills/greeting ~/.codex/skills/
```

Restart Codex — the skill is ready!

## Summary

- Skill creation starts with `init_skill.py`
- The main file is SKILL.md with frontmatter and instructions
- `openai.yaml` provides UI metadata
- `quick_validate.py` checks for errors
- Copy to `~/.codex/skills/` to make it available
