---
title: "Long-Running Workflows"
weight: 4
bookToc: true
---

# Long-Running Workflows

## What Are Long-Running Workflows?

Some tasks take hours or even days. CodeMachine is designed to handle these extended workflows without requiring you to stay at your computer.

## Persistence

CodeMachine automatically saves workflow state. If your workflow is interrupted — by a crash, power outage, or intentional pause — you can resume exactly where you left off.

### How to Resume

Simply run `codemachine` again in the same project folder. CodeMachine detects the saved state and offers to resume.

## Pausing and Resuming

Press **P** during execution to pause. The workflow saves its current state and stops. When you're ready, restart CodeMachine to continue.

## The executeOnce Strategy

For long workflows, mark completed phases with `executeOnce`:

```javascript
export default {
  name: 'Large Project',
  steps: [
    resolveStep('requirements', { executeOnce: true }),    // Done once
    resolveStep('architecture', { executeOnce: true }),    // Done once
    resolveStep('implementation'),                         // Can re-run
    resolveModule('testing', {
      loopSteps: 1,
      loopMaxIterations: 20,
    }),
    resolveStep('deployment'),
  ],
};
```

If you restart the workflow, requirements and architecture won't re-run — saving time and AI costs.

## Signals

During execution, you can send signals to control the workflow:

| Signal | Shortcut | Effect |
|--------|----------|--------|
| Skip | Ctrl+S | Skip current step or prompt |
| Pause | P | Pause and save state |
| Stop | Escape | Stop with confirmation |
| Mode Toggle | Shift+Tab | Switch interactive/autonomous |
| Return | — | Return value from agent |

## MCP Integration

CodeMachine supports MCP (Model Context Protocol) for advanced agent communication. This enables agents to use tools, access external data, and coordinate more effectively.

## Monitoring

While a workflow runs, you can:
- Press **Tab** to view the timeline
- Press **H** to see history
- Check logs in `.codemachine/logs/`

## Best Practices for Long Workflows

1. **Use executeOnce** for setup steps
2. **Set loopMaxIterations** to prevent infinite loops
3. **Use checkpoints** to save progress at key points
4. **Monitor logs** for unexpected behavior
5. **Start supervised**, switch to autonomous once confident

## Summary

- CodeMachine handles workflows running hours or days
- State is saved automatically — resume anytime
- Use executeOnce for completed phases
- Send signals to control execution
- Monitor with timeline, history, and logs

> **Next lesson:** Best practices and real-world workflow design.
