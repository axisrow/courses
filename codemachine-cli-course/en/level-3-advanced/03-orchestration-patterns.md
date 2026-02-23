---
title: "Orchestration Patterns"
weight: 3
bookToc: true
---

# Orchestration Patterns

## The Spectrum of Automation

CodeMachine workflows can range from fully interactive to fully autonomous:

```
Fully Interactive ←──────────────────→ Fully Autonomous
  (You drive)        (Mixed)              (AI drives)
```

## Pattern 1: Human-in-the-Loop

Every step requires human approval. Best for critical or unfamiliar tasks.

```javascript
export default {
  name: 'Careful Builder',
  autonomousMode: 'never',
  steps: [
    resolveStep('planner'),        // Pause → review → approve
    resolveStep('implementer'),    // Pause → review → approve
    resolveStep('reviewer'),       // Pause → review → approve
  ],
};
```

## Pattern 2: Supervised Automation

Most steps run automatically, but critical steps pause for human review.

```javascript
export default {
  name: 'Smart Builder',
  autonomousMode: 'always',
  steps: [
    resolveStep('researcher'),                          // Auto
    resolveStep('planner'),                             // Auto
    resolveStep('implementer'),                         // Auto
    resolveStep('reviewer', { interactive: true }),     // PAUSE for human
    resolveStep('deployer'),                            // Auto
  ],
};
```

## Pattern 3: Full Automation

Everything runs without human intervention. Use for trusted, well-tested workflows.

```javascript
export default {
  name: 'Autopilot Builder',
  autonomousMode: 'always',
  steps: [
    resolveStep('researcher'),
    resolveStep('planner'),
    resolveStep('implementer'),
    resolveStep('reviewer'),
    resolveStep('deployer'),
  ],
};
```

## Pattern 4: Iterative Refinement

Uses modules to loop until quality standards are met.

```javascript
export default {
  name: 'Quality-First Builder',
  steps: [
    resolveStep('planner'),
    resolveStep('implementer'),
    resolveModule('quality-gate', {
      loopSteps: 1,
      loopMaxIterations: 5,
    }),
    resolveStep('deployer'),
  ],
};
```

## Pattern 5: Parallel Team

Multiple sub-agents work simultaneously on different parts.

```javascript
export default {
  name: 'Team Builder',
  steps: [
    resolveStep('architect'),
    resolveStep('coordinator'),
  ],
  subAgentIds: ['frontend-dev', 'backend-dev', 'qa-engineer'],
};
```

## Choosing the Right Pattern

| Pattern | Trust Level | Speed | Control |
|---------|------------|-------|---------|
| Human-in-the-Loop | Low | Slow | Maximum |
| Supervised | Medium | Medium | Balanced |
| Full Automation | High | Fast | Minimal |
| Iterative | Medium | Variable | Quality-focused |
| Parallel Team | High | Fastest | Distributed |

## Summary

- Choose patterns based on trust, speed, and control needs
- Start interactive, move to autonomous as you gain confidence
- Mix patterns within a single workflow
- Use loops for quality assurance
- Use sub-agents for parallel work

> **Next lesson:** Long-running workflows and persistence.
