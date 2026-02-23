---
title: "Modules and Loops"
weight: 5
bookToc: true
---

# Modules and Loops

## What Is a Module?

A module is a special type of step that can repeat itself. It's perfect for tasks that need iteration — like fixing bugs until all tests pass.

## Configuring a Module

```javascript
// config/modules.js
export default [
  {
    id: 'quality-check',
    name: 'Quality Checker',
    description: 'Checks code quality and loops back if issues found',
    promptPath: 'prompts/quality-check.md',
    behavior: {
      type: 'loop',
      action: 'stepBack',
    },
  },
];
```

## Using a Module in a Workflow

```javascript
export default {
  name: 'Build and Verify',
  steps: [
    resolveStep('planner'),
    resolveStep('coder'),
    resolveModule('quality-check', {
      loopSteps: 2,            // Go back 2 steps when looping
      loopMaxIterations: 10,   // Maximum 10 attempts
      loopSkip: ['planner'],   // Don't repeat planning
    }),
  ],
};
```

### How It Works

```
Step 1: Plan → Step 2: Code → Step 3: Check
                  ↑                    ↓
                  └──── Loop back ─────┘
                    (if issues found)
```

The quality checker reviews the code. If it finds problems, it sends the workflow back to the coding step. This repeats until the code passes or the maximum iterations are reached.

## The executeOnce Option

Some steps should only run once, even if the workflow restarts:

```javascript
resolveStep('initial-setup', {
  executeOnce: true,  // Won't run again on restart
}),
```

## Folders — Grouping Steps

Load multiple steps from a folder:

```javascript
// Loads 0-setup.md, 1-research.md, 2-plan.md, etc.
...resolveFolder('preparation'),
```

Files are loaded in order based on their number prefix.

You can apply settings to all steps in a folder:

```javascript
...resolveFolder('implementation', {
  engine: 'codex',
  model: 'gpt-5',
}),
```

## Summary

- Modules are steps that can loop back
- Set `loopSteps`, `loopMaxIterations`, and `loopSkip` to control loops
- Use `executeOnce` for one-time steps
- Use `resolveFolder` to load groups of steps
- Combine modules and folders for complex workflows

> **Congratulations!** You've completed Level 2. You can now build real workflows. In Level 3, we'll explore advanced patterns and optimization.
