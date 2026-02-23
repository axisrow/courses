---
title: "Agent Collaboration and Delegation"
weight: 9
bookToc: true
---

# Agent Collaboration and Delegation

## How Agents Work Together

In CrewAI, agents don't just complete tasks in isolation. They can **delegate** work and **ask questions** to other agents.

## Enabling Delegation

```python
writer = Agent(
    role="Writer",
    goal="Write accurate articles",
    backstory="You write well but delegate fact-checking to others.",
    allow_delegation=True
)
```

When `allow_delegation=True`, the agent can:
- Ask another agent to help with part of a task
- Request information from a specialist agent

## How Delegation Works

1. Agent A is working on a task
2. Agent A realizes it needs specific information
3. Agent A delegates a sub-request to Agent B
4. Agent B responds
5. Agent A uses the response to complete its task

This happens automatically — you just enable it.

## Example: Writer + Fact Checker

```python
from crewai import Agent, Task, Crew, Process

fact_checker = Agent(
    role="Fact Checker",
    goal="Verify claims and provide accurate data",
    backstory="You are meticulous about accuracy."
)

writer = Agent(
    role="Article Writer",
    goal="Write engaging, accurate articles",
    backstory="You write clearly and delegate fact-checking when needed.",
    allow_delegation=True
)

task = Task(
    description="Write an article about the benefits of solar energy. Verify all statistics.",
    expected_output="A 400-word article with verified facts.",
    agent=writer
)

crew = Crew(
    agents=[fact_checker, writer],
    tasks=[task],
    process=Process.sequential,
    verbose=True
)

result = crew.kickoff()
```

The writer may ask the fact checker to verify specific claims during execution.

## Controlling Delegation

| Setting | Effect |
|---------|--------|
| `allow_delegation=True` | Agent can delegate to others |
| `allow_delegation=False` | Agent works alone (default) |

## Best Practices

1. **Enable delegation selectively** — not every agent needs it
2. **Have specialist agents available** — delegation works best when there's someone to delegate to
3. **Watch the logs** — delegation adds LLM calls and can increase execution time
4. **Use clear roles** — agents delegate based on role matching

## Summary

Delegation lets agents ask each other for help during task execution. Enable it with `allow_delegation=True` and make sure specialist agents are in the crew.

---

**Next:** Error handling and debugging.
