---
title: "Error Handling and Debugging"
weight: 10
bookToc: true
---

# Error Handling and Debugging

## Common Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| Empty output | Vague task description | Be more specific in description and expected_output |
| API errors | Missing or invalid API key | Check environment variables |
| Infinite loops | Agent can't complete task | Set `max_iter` on the agent |
| Wrong tool used | Too many tools assigned | Reduce tools to only what's needed |
| Timeout | Task too complex | Break into smaller tasks |

## Verbose Mode

Always start debugging with verbose output:

```python
crew = Crew(
    agents=[agent1, agent2],
    tasks=[task1, task2],
    verbose=True  # see everything
)
```

This shows you:
- Which agent is working
- What tools are being called
- What the agent is "thinking"
- The final output of each task

## Max Iterations

Prevent agents from looping forever:

```python
agent = Agent(
    role="Analyst",
    goal="Analyze data",
    backstory="You are a data analyst.",
    max_iter=10  # stop after 10 reasoning loops
)
```

## Error Callbacks

Handle errors gracefully:

```python
def handle_error(error):
    print(f"Task failed: {error}")
    return "Could not complete the task."

task = Task(
    description="Do something risky.",
    expected_output="Result.",
    agent=agent,
    callback=handle_error
)
```

## Debugging Checklist

1. ✅ Turn on `verbose=True`
2. ✅ Check API keys are set correctly
3. ✅ Verify agent roles and goals make sense
4. ✅ Ensure task descriptions are specific
5. ✅ Check that expected_output is clear
6. ✅ Make sure tools are installed and configured
7. ✅ Set `max_iter` to prevent loops
8. ✅ Test with simple tasks first, then add complexity

## Logging

For production, use Python logging:

```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

## Summary

Debug with `verbose=True`, set `max_iter` to prevent loops, and be specific in task descriptions. Most issues come from vague instructions or missing API keys.

---

**Congratulations!** Level 2 complete. You now understand tools, memory, processes, collaboration, and debugging. Next: advanced topics.
