---
title: "Superpowers Architecture"
level: 3
lesson: 1
lang: en
---

# Superpowers Architecture

## Introduction

Deep dive into the skills system architecture.

## Repository Structure

```
superpowers/
├── skills/
│   ├── brainstorming/SKILL.md
│   ├── test-driven-development/SKILL.md
│   ├── subagent-driven-development/SKILL.md
│   └── ...
├── docs/
├── .claude/
├── .codex/
├── .opencode/
└── README.md
```

## How Skills Work

Each skill is a `SKILL.md` file with agent instructions. When the agent encounters a specific context, it loads the corresponding skill.

### Skill Chain

```
brainstorming → using-git-worktrees → writing-plans → 
subagent-driven-development → test-driven-development → 
requesting-code-review → finishing-a-development-branch
```

## Activation System

Skills are checked **before every task**. These are mandatory workflows, not suggestions.

## Inter-Skill Communication

Skills communicate through artifacts:
- Specification (brainstorming → writing-plans)
- Plan (writing-plans → subagent-driven-development)
- Code and tests (subagent-driven-development → code-review)

## Summary

- Skills live in `skills/*/SKILL.md`
- Activate automatically by context
- Form a chain from idea to merge
- Communicate through artifacts
