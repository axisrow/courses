---
title: "Memory and Context"
weight: 7
bookToc: true
---

# Memory and Context

## Why Memory Matters

By default, each crew run starts fresh. Memory lets agents remember information across tasks and even across runs.

## Types of Memory

| Type | Scope | Purpose |
|------|-------|---------|
| **Short-term** | Current run | Share info between tasks |
| **Long-term** | Across runs | Learn from past executions |
| **Entity** | Across runs | Remember facts about people, places, concepts |

## Enabling Memory

```python
crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    memory=True,
    verbose=True
)
```

That's it. Setting `memory=True` activates all three memory types.

## How It Works

1. **Short-term memory** — stores task outputs during a run. Later tasks can access earlier results automatically.
2. **Long-term memory** — after a run completes, key learnings are saved. On the next run, agents can recall what worked before.
3. **Entity memory** — the crew tracks entities (names, companies, concepts) and builds a knowledge base over time.

## Context Between Tasks

Even without memory, you can pass context explicitly:

```python
writing_task = Task(
    description="Write an article based on research.",
    expected_output="A 500-word article.",
    agent=writer,
    context=[research_task]
)
```

The `context` parameter passes the output of `research_task` directly to the writer.

## Memory Storage

By default, memory is stored locally using an embedded database. For production, you can configure external storage.

## When to Use Memory

- **Short-term**: always useful in multi-task crews
- **Long-term**: when you run the same crew repeatedly and want it to improve
- **Entity**: when your crew deals with recurring entities (customers, products, topics)

## Example

```python
from crewai import Agent, Task, Crew

support_agent = Agent(
    role="Customer Support",
    goal="Help customers based on their history",
    backstory="You remember past interactions and provide personalized help."
)

task = Task(
    description="Help customer John with his billing question.",
    expected_output="A personalized response referencing past interactions.",
    agent=support_agent
)

crew = Crew(
    agents=[support_agent],
    tasks=[task],
    memory=True
)

# First run - no history
result = crew.kickoff()

# Second run - agent remembers John
result = crew.kickoff()
```

## Summary

Memory lets crews learn and remember. Enable it with `memory=True`. Use context for explicit task chaining, and long-term memory for improving over repeated runs.

---

**Next:** Process types — sequential and hierarchical.
