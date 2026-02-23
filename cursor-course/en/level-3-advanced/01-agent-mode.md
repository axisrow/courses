---
title: "Agent Mode — Full Autonomy"
weight: 1
bookToc: true
---

# Agent Mode — Full Autonomy

## What Is Agent Mode?

Agent mode is Cursor's most powerful feature. Instead of you directing every step, the AI **takes initiative**:
- Reads and searches your codebase
- Creates and edits files
- Runs terminal commands
- Installs packages
- Runs tests and fixes errors

Think of it as giving the AI a task and letting it figure out the steps.

## How to Use Agent Mode

1. Open Chat (`Ctrl+L` / `Cmd+L`)
2. Select **Agent** mode (look for the toggle at the top)
3. Describe your task in natural language
4. Let the AI work — it will show you each step

## The Autonomy Slider

As Andrej Karpathy described it, Cursor has an "autonomy slider":
- **Tab completion** → Minimal autonomy (you drive)
- **Cmd+K** → Medium autonomy (you direct, AI executes)
- **Agent mode** → Maximum autonomy (AI drives, you review)

## What Agent Mode Can Do

- "Set up a Node.js project with Express, TypeScript, and PostgreSQL"
- "Write tests for all the API endpoints"
- "Find and fix the bug causing login failures"
- "Refactor the authentication system to use JWT"

## Safety: Approving Actions

Agent mode asks for your **approval** before:
- Running terminal commands
- Making significant changes
- Installing packages

You always have the final say.

## Best Practices

1. **Start with a clear plan** — Describe the full task upfront
2. **Review each step** — Don't blindly accept everything
3. **Use Git** — Commit before starting so you can revert
4. **Break large tasks** — "Build the entire app" is too vague; break it into features
5. **Provide context** — Mention relevant files with `@`

## Summary

- Agent mode = maximum AI autonomy
- The AI plans, codes, runs commands, and fixes errors
- You review and approve each step
- Best for larger, well-defined tasks
