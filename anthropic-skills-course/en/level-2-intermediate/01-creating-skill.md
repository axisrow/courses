---
title: "Creating Your Own Skill"
weight: 1
bookToc: true
---

# Creating Your Own Skill

## Introduction

Creating a skill is simple: you need a folder with a `SKILL.md` file.

## Step 1: Define the Task

Before creating, answer:
- What task should the skill solve?
- When should Claude activate it?
- What output is expected?

## Step 2: Create the Structure

```bash
mkdir code-reviewer && cd code-reviewer
```

## Step 3: Write SKILL.md

```markdown
---
name: code-reviewer
description: Reviews Python code for best practices, security vulnerabilities, and performance issues. Use when user asks to review Python code.
---

# Code Review Skill

## Review Process
1. Read the entire codebase
2. Check for security issues
3. Check for performance problems
4. Verify PEP 8 compliance

## Output Format
- 🔴 Critical — security vulnerabilities
- 🟡 Warning — performance issues
- 🔵 Info — style suggestions

## Guidelines
- Be constructive
- Provide fix examples
- Prioritize security over style
```

## Step 4: Test

Connect the skill and ask Claude a related question.

## Summary

- A skill is a folder with `SKILL.md`
- Start by defining the task and expected output
- Write specific instructions with examples
- Use `skill-creator` for help
