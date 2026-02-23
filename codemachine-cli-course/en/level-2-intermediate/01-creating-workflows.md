---
title: "Creating Your First Workflow"
weight: 1
bookToc: true
---

# Creating Your First Workflow

## Using Ali to Build a Workflow

The easiest way to create a workflow is using Ali, the built-in workflow builder. When you run `codemachine` in a new project, Ali guides you through these steps:

1. **Setup** — Describe your project
2. **Brainstorming** — Define what you want to achieve
3. **Workflow definition** — Structure the steps
4. **Agents** — Configure the AI workers
5. **Prompts** — Write instructions for each agent
6. **Workflow generation** — Create the final files

## Building Manually

You can also create workflows by hand. You need three things:

### 1. Agent Configuration (`config/main.agents.js`)

```javascript
export default [
  {
    id: 'researcher',
    name: 'Research Agent',
    description: 'Gathers information about the task',
    promptPath: '.codemachine/prompts/research.md',
  },
  {
    id: 'implementer',
    name: 'Implementation Agent',
    description: 'Writes the actual code',
    promptPath: '.codemachine/prompts/implement.md',
  },
];
```

### 2. Prompt Files (`.codemachine/prompts/research.md`)

```markdown
---
name: 'Research Phase'
description: 'Gather requirements and context'
---

# Research Phase

## STEP GOAL:
Understand what needs to be built by analyzing the codebase and requirements.

## Sequence of Instructions
### 1. Read the project specification
### 2. Explore the existing codebase
### 3. Summarize findings for the next step
```

### 3. Workflow File (`.codemachine/workflows/my-workflow.workflow.js`)

```javascript
export default {
  name: 'My First Workflow',
  steps: [
    resolveStep('researcher'),
    resolveStep('implementer'),
  ],
};
```

## Running Your Workflow

```bash
codemachine
```

Select your workflow from the list, and CodeMachine begins executing it step by step.

## Summary

- Use Ali for guided workflow creation
- Or create agent configs, prompts, and workflow files manually
- Run with `codemachine` and select your workflow

> **Next lesson:** Mastering prompts — writing effective agent instructions.
