---
title: "Understanding Tasks"
weight: 4
bookToc: true
---

# Understanding Tasks

## What is a Task?

A task is a specific piece of work you assign to an agent. It describes **what** needs to be done and **what output** is expected.

## Creating a Task

```python
from crewai import Task

research_task = Task(
    description="Research the latest trends in renewable energy for 2025.",
    expected_output="A bullet-point list of 5 trends with brief explanations.",
    agent=researcher
)
```

## Key Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `description` | str | What the task is about |
| `expected_output` | str | What the result should look like |
| `agent` | Agent | Who performs this task |
| `tools` | list | Task-specific tools (overrides agent tools) |
| `output_file` | str | Save output to a file |
| `context` | list | Other tasks whose output feeds into this one |
| `async_execution` | bool | Run this task in parallel |

## Task Dependencies with Context

Tasks can use output from previous tasks:

```python
research_task = Task(
    description="Research AI trends.",
    expected_output="List of 5 trends.",
    agent=researcher
)

writing_task = Task(
    description="Write a blog post based on the research.",
    expected_output="A 500-word blog post.",
    agent=writer,
    context=[research_task]  # uses research output
)
```

## Saving Output to File

```python
report_task = Task(
    description="Write a final report.",
    expected_output="A markdown report.",
    agent=writer,
    output_file="report.md"
)
```

## YAML Configuration

In `tasks.yaml`:

```yaml
research_task:
  description: "Research the latest trends in {topic}."
  expected_output: "A list of 5 key trends."
  agent: researcher

writing_task:
  description: "Write a blog post about {topic} using the research."
  expected_output: "A 500-word blog post in markdown."
  agent: writer
  context:
    - research_task
```

Notice the `{topic}` placeholder — you can pass variables at runtime.

## Tips

1. **Be precise** in descriptions — vague tasks give vague results
2. **Define expected output clearly** — format, length, structure
3. **Use context** to chain tasks together
4. **Save important outputs** to files

## Summary

Tasks define the work. Each task has a description, expected output, and an assigned agent. Use context to chain tasks so one agent's output feeds into the next.

---

**Next:** Building your first Crew.
