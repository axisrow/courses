---
title: "Processes: Sequential and Hierarchical"
weight: 8
bookToc: true
---

# Processes: Sequential and Hierarchical

## What is a Process?

A process defines **how agents work together** — the order and coordination style.

## Sequential Process

Tasks run one after another, in the order you list them.

```python
from crewai import Crew, Process

crew = Crew(
    agents=[researcher, writer, editor],
    tasks=[research_task, writing_task, editing_task],
    process=Process.sequential
)
```

**Flow:** Research → Write → Edit

Best for: pipelines where each step depends on the previous one.

## Hierarchical Process

A **manager agent** coordinates the work. It decides which agent handles what and in what order.

```python
crew = Crew(
    agents=[researcher, writer, editor],
    tasks=[research_task, writing_task, editing_task],
    process=Process.hierarchical,
    manager_llm="gpt-4o"
)
```

The manager:
- Reads all tasks
- Assigns them to agents
- Reviews results
- Re-assigns if needed

Best for: complex workflows where the optimal order isn't fixed.

## Comparison

| Feature | Sequential | Hierarchical |
|---------|-----------|-------------|
| Order | Fixed (you define it) | Dynamic (manager decides) |
| Manager | None | Auto-created or custom |
| Simplicity | Simple | More complex |
| Control | Full control | Manager decides |
| Best for | Linear pipelines | Complex, flexible workflows |

## Custom Manager Agent

```python
manager = Agent(
    role="Project Manager",
    goal="Coordinate the team for best results",
    backstory="Experienced PM who knows how to delegate effectively."
)

crew = Crew(
    agents=[researcher, writer, editor],
    tasks=[research_task, writing_task, editing_task],
    process=Process.hierarchical,
    manager_agent=manager
)
```

## Tips

1. **Start with sequential** — it's simpler and easier to debug
2. **Use hierarchical** when tasks have complex dependencies
3. **Watch the logs** with `verbose=True` to understand the flow
4. In hierarchical mode, the manager uses extra LLM calls — be mindful of costs

## Summary

Sequential runs tasks in order. Hierarchical uses a manager to coordinate dynamically. Choose based on your workflow complexity.

---

**Next:** Agent collaboration and delegation.
