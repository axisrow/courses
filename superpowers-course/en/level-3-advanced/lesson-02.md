---
title: "Creating Custom Skills"
level: 3
lesson: 2
lang: en
---

# Creating Custom Skills

## Introduction

How to create your own Superpowers skill.

## Skill Structure

```
skills/my-skill/
└── SKILL.md
```

### SKILL.md Format

```markdown
# Skill Name

## When to Use
Activation trigger description.

## Process
Step-by-step agent instructions.

## Examples
Concrete usage examples.

## Anti-patterns
What to avoid.
```

## The `writing-skills` Meta-Skill

Superpowers includes a meta-skill for creating new skills. Tell the agent:

```
I want to create a skill for automatic documentation generation
```

## Principles of Good Skills

- **Specificity** — exact instructions, not general advice
- **Triggers** — clear activation conditions
- **Verifiability** — how to check the skill works
- **Minimalism** — only what's necessary

## Summary

- A skill = a SKILL.md file with instructions
- Use the writing-skills meta-skill
- Skills should be specific and verifiable
- Test skills on real tasks
