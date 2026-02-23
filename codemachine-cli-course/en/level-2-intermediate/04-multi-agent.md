---
title: "Multi-Agent Orchestration"
weight: 4
bookToc: true
---

# Multi-Agent Orchestration

## Why Multiple Agents?

Just like a team of specialists is better than one generalist, multiple AI agents can handle complex tasks more effectively. Each agent focuses on what it does best.

## Sub-Agents

Sub-agents work alongside main agents. They run in parallel and can communicate with the main workflow.

### Configuring Sub-Agents

```javascript
// config/sub.agents.js
export default [
  {
    id: 'frontend-dev',
    name: 'Frontend Developer',
    description: 'Builds UI components',
    mirrorPath: 'prompts/frontend-mirror.md',
  },
  {
    id: 'backend-dev',
    name: 'Backend Developer',
    description: 'Builds API endpoints',
    mirrorPath: 'prompts/backend-mirror.md',
  },
];
```

### Using Sub-Agents in a Workflow

```javascript
export default {
  name: 'Full Stack Builder',
  steps: [
    resolveStep('architect'),
    resolveStep('implementation'),
  ],
  subAgentIds: ['frontend-dev', 'backend-dev'],
};
```

## Parallel Execution

When sub-agents are assigned, they can work simultaneously:

```
Main Agent (Architect)
    ├── Sub-Agent: Frontend Dev  ──→ Building UI
    └── Sub-Agent: Backend Dev   ──→ Building API
```

This is significantly faster than running tasks one after another.

## Controller Agents

A controller agent oversees the workflow and makes decisions:

```javascript
export default {
  name: 'Managed Workflow',
  controller: controller('project-manager', {
    engine: 'claude',
    model: 'opus',
  }),
  steps: [...],
};
```

The controller can:
- Approve or reject agent outputs
- Adjust the workflow direction
- Provide feedback to agents

## Engine Mixing

Different agents can use different AI engines:

```javascript
resolveStep('planning', { engine: 'claude' }),    // Claude for analysis
resolveStep('coding', { engine: 'codex' }),       // Codex for code
resolveStep('review', { engine: 'claude' }),      // Claude for review
resolveStep('testing', { engine: 'codex' }),      // Codex for tests
```

## Summary

- Use sub-agents for parallel work
- Controllers oversee and make decisions
- Mix engines to leverage each AI's strengths
- Parallel execution saves time

> **Next lesson:** Modules, loops, and advanced step control.
