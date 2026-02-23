---
title: "What Are Agent Skills"
weight: 1
bookToc: true
---

# What Are Agent Skills

## Introduction

Agent Skills are folders of instructions, scripts, and resources that AI agents can discover and use to perform specific tasks. The principle is simple: **write once, use everywhere**.

Imagine onboarding a new employee. You hand them guides: "Here's how we handle clients," "Here's the report template." Skills work the same way — they "train" the AI agent Codex to perform specific tasks.

## Why Do You Need Skills?

Without skills, Codex is a smart but general-purpose assistant. With skills it becomes a **specialist**:

- 📸 **screenshot** — takes screenshots
- 📄 **pdf** — works with PDF documents
- 🎨 **figma** — converts Figma designs to code
- 🚀 **vercel-deploy** — deploys apps to Vercel

## How It Works

Each skill is a regular folder with files:

```
skill-name/
├── SKILL.md          — main instruction file
├── agents/
│   └── openai.yaml   — UI metadata
├── scripts/          — executable scripts (optional)
├── references/       — reference docs (optional)
└── assets/           — resource files (optional)
```

The most important file is **SKILL.md**. Codex reads it to understand what to do.

## Three Categories of Skills

| Category | Description | Installation |
|----------|-------------|-------------|
| `.system` | Built into Codex | Automatic |
| `.curated` | Verified by OpenAI | Via skill-installer |
| `.experimental` | Community, experimental | Via skill-installer |

## Summary

- Agent Skills extend Codex's abilities for specific tasks
- Each skill is a folder with instructions and resources
- Skills are divided into system, curated, and experimental
- The main skill file is SKILL.md
