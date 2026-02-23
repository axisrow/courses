---
title: "Understanding Agents"
weight: 5
bookToc: true
---

# Understanding Agents

## What Is an Agent?

An agent is an AI assistant assigned to a specific task in your workflow. Each agent has:

- **An ID** — a unique name (like `code-reviewer`)
- **A display name** — a friendly name (like "Senior Code Reviewer")
- **A prompt** — detailed instructions for what to do
- **An engine** — which AI system to use (Claude, Codex, etc.)

## Types of Agents

CodeMachine has three types of agents:

### 1. Main Agents
These are the primary workers. Each step in your workflow uses a main agent.

```javascript
// config/main.agents.js
{
  id: 'code-reviewer',
  name: 'Code Reviewer',
  description: 'Reviews code for quality and bugs',
  promptPath: 'prompts/review.md',
}
```

### 2. Sub-Agents
These are helpers that work alongside main agents. They run in parallel and can communicate with the main agent.

```javascript
// config/sub.agents.js
{
  id: 'frontend-dev',
  name: 'Frontend Developer',
  description: 'Handles UI components',
  mirrorPath: 'prompts/frontend-mirror.md',
}
```

### 3. Controller Agents
A special agent that oversees the whole workflow and makes high-level decisions.

## Choosing an Engine

CodeMachine supports multiple AI engines:

| Engine | Best For |
|--------|----------|
| Claude | Analysis, writing, code review |
| Codex | Code generation, implementation |
| Cursor | IDE-integrated tasks |

You can mix engines within a single workflow:

```javascript
resolveStep('planning', { engine: 'claude' }),
resolveStep('coding', { engine: 'codex' }),
resolveStep('review', { engine: 'claude' }),
```

## Summary

- Agents are AI workers assigned to workflow steps
- Main agents do primary tasks, sub-agents help, controllers oversee
- Each agent has an ID, name, prompt, and engine
- You can mix different AI engines in one workflow

> **Congratulations!** You've completed Level 1. You now understand the basics of CodeMachine. In Level 2, we'll start building real workflows.
