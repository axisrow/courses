---
title: "Understanding Workflows"
weight: 4
bookToc: true
---

# Understanding Workflows

## What Is a Workflow?

A workflow is a sequence of steps that tell AI agents what to do and in what order. Each step has:

- **An agent** — which AI performs the task
- **A prompt** — instructions telling the agent what to do
- **Settings** — how the agent should behave

## A Real-World Example

Let's say you want to build a new feature for a website. Your mental workflow might look like:

1. Research what's needed
2. Plan the architecture
3. Write the code
4. Review the code
5. Write tests

In CodeMachine, each of these becomes a **step** with its own dedicated agent and instructions.

## The Workflow File

Workflows are defined in JavaScript files. Here's a simplified example:

```javascript
export default {
  name: 'Feature Builder',

  steps: [
    resolveStep('research-agent'),
    resolveStep('planning-agent'),
    resolveStep('coding-agent'),
    resolveStep('review-agent'),
    resolveStep('testing-agent'),
  ],
};
```

Each `resolveStep` points to an agent that has its own prompt file with detailed instructions.

## Three Types of Building Blocks

| Block | Purpose | Example |
|-------|---------|---------|
| **Step** | A single task | "Review the code" |
| **Module** | A task that can loop | "Check and fix until done" |
| **Folder** | A group of related steps | "All setup steps" |

## How Steps Connect

Steps run one after another. When one step finishes, the next one begins. The output from one step can become context for the next.

```
Step 1 → Step 2 → Step 3 → Step 4 → Done!
```

## Summary

- A workflow is a saved sequence of AI tasks
- Each step has an agent, a prompt, and settings
- Workflows are defined in JavaScript files
- Steps, modules, and folders are your building blocks

> **Next lesson:** Understanding agents — the AI workers in your workflow.
