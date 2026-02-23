---
title: "What is CrewAI?"
weight: 1
bookToc: true
---

# What is CrewAI?

## Introduction

CrewAI is an open-source Python framework for building **multi-agent AI systems**. Instead of one AI doing everything, you create a team (a "crew") of specialized AI agents that work together.

Think of it like a company: you have a researcher, a writer, a reviewer — each with their own role and skills. CrewAI lets you build exactly that with code.

## Why Multi-Agent?

A single AI prompt can only do so much. When you split work across multiple agents:

- Each agent focuses on what it does best
- Agents can use different tools
- Complex tasks get broken into manageable pieces
- Results are more reliable and detailed

## Key Concepts

| Concept | What It Means |
|---------|--------------|
| **Agent** | An AI worker with a specific role, goal, and backstory |
| **Task** | A specific job assigned to an agent |
| **Crew** | A team of agents working together on tasks |
| **Tool** | An external capability an agent can use (search, file read, API call) |
| **Process** | How agents coordinate — sequentially or hierarchically |

## A Simple Example

```python
from crewai import Agent, Task, Crew

researcher = Agent(
    role="Researcher",
    goal="Find accurate information about AI trends",
    backstory="You are an experienced tech researcher."
)

task = Task(
    description="Research the top 3 AI trends in 2025.",
    expected_output="A short summary of 3 trends.",
    agent=researcher
)

crew = Crew(agents=[researcher], tasks=[task])
result = crew.kickoff()
print(result)
```

## When to Use CrewAI

- Content generation pipelines
- Research and analysis workflows
- Data processing with multiple steps
- Any task that benefits from division of labor

## Summary

CrewAI makes it easy to build teams of AI agents in Python. Each agent has a role, tasks to complete, and tools to use. Together, they solve complex problems better than a single prompt.

---

**Next:** Installing CrewAI and setting up your environment.
