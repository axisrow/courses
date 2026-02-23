---
title: "Your First Crew"
weight: 5
bookToc: true
---

# Your First Crew

## Putting It All Together

You know agents and tasks. Now let's build a complete crew.

## The Crew Class

```python
from crewai import Crew, Process

crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    process=Process.sequential,
    verbose=True
)
```

## Key Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `agents` | list | All agents in the crew |
| `tasks` | list | All tasks to execute |
| `process` | Process | Sequential or hierarchical |
| `verbose` | bool | Detailed logging |
| `memory` | bool | Enable crew memory |

## Complete Example

```python
from crewai import Agent, Task, Crew, Process

# Agents
researcher = Agent(
    role="Tech Researcher",
    goal="Find accurate information about CrewAI",
    backstory="You are an AI researcher who reads documentation carefully."
)

writer = Agent(
    role="Technical Writer",
    goal="Write clear summaries from research",
    backstory="You simplify complex topics for beginners."
)

# Tasks
research_task = Task(
    description="Research what CrewAI is and its main features.",
    expected_output="A list of 5 key features of CrewAI.",
    agent=researcher
)

writing_task = Task(
    description="Write a beginner-friendly summary of CrewAI.",
    expected_output="A 300-word summary in simple language.",
    agent=writer,
    context=[research_task],
    output_file="crewai_summary.md"
)

# Crew
crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    process=Process.sequential,
    verbose=True
)

# Run
result = crew.kickoff()
print(result)
```

## Running the Crew

```bash
python main.py
```

You'll see logs showing:
1. The researcher agent working on its task
2. The writer agent receiving research and writing the summary
3. The final output printed and saved to file

## What Happens Under the Hood

1. CrewAI sends the first task to the researcher agent
2. The agent uses the LLM to complete the task
3. The output is passed as context to the next task
4. The writer agent uses that context to produce the final result

## Common Errors

| Error | Fix |
|-------|-----|
| Missing API key | Set `OPENAI_API_KEY` environment variable |
| Agent not assigned | Make sure every task has an `agent` |
| Empty output | Make `expected_output` more specific |

## Exercise

Build a crew with:
- A **Researcher** who finds 3 facts about a topic of your choice
- A **Writer** who turns those facts into a short article
- Run it and check the output

## Summary

A Crew combines agents and tasks into a working pipeline. Use `Process.sequential` to run tasks in order. Call `crew.kickoff()` to start execution.

---

**Congratulations!** You've completed Level 1. You can now build basic CrewAI applications. Next, we'll explore tools, memory, and advanced processes.
