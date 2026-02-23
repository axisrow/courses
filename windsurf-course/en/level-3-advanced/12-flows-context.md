---
title: "AI Flows & Context"
weight: 12
bookToc: true
---

# AI Flows & Context Management

## What are Flows?

Flows are Windsurf's way of tracking what the AI knows about your actions. As you code, Windsurf observes:

- Files you open and edit
- Terminal commands you run
- Errors you encounter
- Code you highlight

This creates a **context** that makes AI suggestions more relevant.

## How Context Works

### Automatic Context
Windsurf automatically includes:
- The current file
- Recently opened files
- Project structure (file tree)
- Language and framework detection

### Manual Context
You can add context by:
- Selecting code before prompting Cascade
- Using `@file` references in prompts
- Opening relevant files in tabs

## Context Window

The AI has a limited context window. Tips to use it well:

1. **Close irrelevant tabs** — fewer distractions for the AI
2. **Be specific about files** — "Look at `auth.js`, not the whole project"
3. **Start fresh conversations** for unrelated tasks

## Flows in Practice

### Flow Example: Bug Fix
1. You see an error in the terminal → Windsurf notices
2. You open the problematic file → added to context
3. You highlight the error line → pinpoints the issue
4. You ask Cascade to fix it → it has full context

### Flow Example: Feature Development
1. You create a new file → Windsurf tracks the pattern
2. You import from existing modules → Windsurf understands dependencies
3. AI suggestions align with your project's patterns

## Resetting Context

If the AI seems confused:
- Start a new Cascade conversation
- Close and reopen the project
- Clear the Cascade history

## Practice

Pay attention to how context affects AI quality. Try the same prompt with different files open and compare results.
