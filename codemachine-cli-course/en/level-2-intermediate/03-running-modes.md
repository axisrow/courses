---
title: "Running Modes"
weight: 3
bookToc: true
---

# Running Modes

## Three Ways to Run Workflows

CodeMachine offers three running modes, giving you control over how much human involvement is needed:

### 1. Interactive Mode (You're in control)

The agent pauses after each step and waits for your input. You can review the output, give feedback, or move to the next step.

**Best for:** Learning, sensitive tasks, first-time workflows.

### 2. Autonomous Mode (Fully automatic)

The agent runs through all steps without stopping. It sends all prompts automatically and moves forward on its own.

**Best for:** Trusted workflows you've already tested, batch processing, overnight runs.

### 3. Continuous Mode (Auto-advance)

The agent automatically moves to the next step after completing each one, but doesn't send additional prompts.

**Best for:** Simple, sequential workflows where each step is self-contained.

## The 8 Scenarios

CodeMachine combines three settings to create 8 possible scenarios:

| Setting | Values |
|---------|--------|
| Interactive | yes / no |
| Auto Mode | on / off |
| Chained Prompts | yes / no |

The most common scenarios are:

| Scenario | Description | Use Case |
|----------|-------------|----------|
| 3 | Interactive + manual + chained prompts | Guided learning |
| 4 | Interactive + manual + single prompt | Simple tasks |
| 5 | Fully autonomous | Trusted automation |
| 1 | Interactive + auto + chained prompts | Controller-driven |

## Switching Modes During Execution

You can switch between modes while a workflow is running:

- Press **Shift+Tab** to toggle autonomous mode
- Press **P** to pause
- Press **Ctrl+S** to skip a step

## Configuring Mode in Workflow

```javascript
export default {
  name: 'My Workflow',
  autonomousMode: 'always',  // 'always' | 'never' | true | false
  steps: [
    resolveStep('agent-1'),
    resolveStep('agent-2', { interactive: true }), // Override for this step
  ],
};
```

## Summary

- Interactive = you control each step
- Autonomous = fully automatic
- Continuous = auto-advance without prompts
- Switch modes anytime with keyboard shortcuts
- Configure default mode per workflow or per step

> **Next lesson:** Multi-agent orchestration — making agents work together.
