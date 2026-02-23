---
title: "Real-World Project: Newsletter Generator"
weight: 15
bookToc: true
---

# Real-World Project: Newsletter Generator

## The Goal

Build a crew that automatically generates a weekly tech newsletter:
1. Research trending topics
2. Write article summaries
3. Edit and format the final newsletter

## Project Setup

```bash
crewai create crew newsletter_crew
cd newsletter_crew
pip install 'crewai[tools]'
```

## Define Agents

```python
from crewai import Agent
from crewai_tools import SerperDevTool

researcher = Agent(
    role="Tech Trend Researcher",
    goal="Find the 5 most interesting tech stories this week",
    backstory="You track tech news daily and spot emerging trends.",
    tools=[SerperDevTool()],
    llm="gpt-4o",
    max_iter=10
)

writer = Agent(
    role="Newsletter Writer",
    goal="Write engaging summaries of tech stories",
    backstory="You write concise, witty summaries for a tech-savvy audience.",
    llm="gpt-4o-mini"
)

editor = Agent(
    role="Editor-in-Chief",
    goal="Polish the newsletter and ensure quality",
    backstory="You have high standards for clarity and accuracy.",
    llm="gpt-4o-mini"
)
```

## Define Tasks

```python
from crewai import Task

research_task = Task(
    description="""Find the 5 most notable tech news stories from this week.
    For each story, provide: title, source, and a 2-sentence summary.""",
    expected_output="A numbered list of 5 stories with titles, sources, and summaries.",
    agent=researcher
)

writing_task = Task(
    description="""Write a newsletter using the researched stories.
    Include: catchy subject line, intro paragraph, 5 story sections, closing.""",
    expected_output="A complete newsletter in markdown format, ~800 words.",
    agent=writer,
    context=[research_task]
)

editing_task = Task(
    description="""Review and polish the newsletter.
    Fix grammar, improve clarity, ensure consistent tone.""",
    expected_output="A polished, publication-ready newsletter in markdown.",
    agent=editor,
    context=[writing_task],
    output_file="newsletter.md"
)
```

## Assemble and Run

```python
from crewai import Crew, Process

crew = Crew(
    agents=[researcher, writer, editor],
    tasks=[research_task, writing_task, editing_task],
    process=Process.sequential,
    memory=True,
    verbose=True
)

result = crew.kickoff()
print(result)
print(f"\nTokens used: {result.token_usage}")
```

## Running It

```bash
export OPENAI_API_KEY="sk-..."
export SERPER_API_KEY="..."
python main.py
```

The output is saved to `newsletter.md`.

## Extending the Project

Ideas to make it better:
- Add a **translator agent** for multi-language newsletters
- Use **async tasks** to research topics in parallel
- Schedule with **cron** to run weekly
- Wrap in **FastAPI** to trigger via API
- Add a **quality scorer** agent that rates the output

## What You Learned

In this course, you learned:
- ✅ What CrewAI is and why multi-agent systems matter
- ✅ How to create agents, tasks, and crews
- ✅ Using tools, memory, and processes
- ✅ Collaboration, delegation, and debugging
- ✅ Custom tools, LLM integration, deployment, and optimization
- ✅ Building a complete real-world project

## Next Steps

- Explore the [CrewAI documentation](https://docs.crewai.com)
- Join the [CrewAI community](https://community.crewai.com)
- Build your own multi-agent projects
- Experiment with different LLMs and tools

---

**Congratulations!** You've completed the CrewAI course. 🎉
