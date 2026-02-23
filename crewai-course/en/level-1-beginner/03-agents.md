---
title: "Understanding Agents"
weight: 3
bookToc: true
---

# Understanding Agents

## What is an Agent?

An agent is an AI worker with a clear identity. Every agent has:

- **Role** — what the agent does (e.g., "Data Analyst")
- **Goal** — what the agent tries to achieve
- **Backstory** — context that shapes how the agent behaves

## Creating an Agent

```python
from crewai import Agent

writer = Agent(
    role="Blog Writer",
    goal="Write engaging blog posts about technology",
    backstory="You are a seasoned tech blogger with 10 years of experience.",
    verbose=True
)
```

## Key Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `role` | str | The agent's job title |
| `goal` | str | What the agent aims to accomplish |
| `backstory` | str | Background context for the agent |
| `verbose` | bool | Print detailed logs (default: False) |
| `allow_delegation` | bool | Can this agent delegate to others? |
| `tools` | list | Tools the agent can use |
| `llm` | str | Which language model to use |
| `max_iter` | int | Maximum reasoning iterations |
| `memory` | bool | Enable memory for this agent |

## Multiple Agents

```python
researcher = Agent(
    role="Researcher",
    goal="Find accurate data on market trends",
    backstory="Expert market analyst with deep research skills."
)

writer = Agent(
    role="Writer",
    goal="Turn research into clear reports",
    backstory="Technical writer who makes complex topics simple."
)
```

## Tips for Good Agents

1. **Be specific** with roles — "SEO Blog Writer" is better than "Writer"
2. **Make goals measurable** — "Write a 500-word summary" beats "Write something"
3. **Use backstory** to set tone and expertise level
4. **Start with verbose=True** to understand what's happening

## YAML Configuration

You can also define agents in `agents.yaml`:

```yaml
researcher:
  role: "Senior Researcher"
  goal: "Find comprehensive information on given topics"
  backstory: "You are a thorough researcher who always verifies facts."

writer:
  role: "Content Writer"
  goal: "Create clear, engaging content from research"
  backstory: "You write in simple language that anyone can understand."
```

## Summary

Agents are the workers of your crew. Define them with a clear role, goal, and backstory. The more specific you are, the better results you get.

---

**Next:** Understanding Tasks.
