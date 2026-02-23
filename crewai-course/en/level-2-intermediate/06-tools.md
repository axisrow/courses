---
title: "Working with Tools"
weight: 6
bookToc: true
---

# Working with Tools

## What Are Tools?

Tools give agents the ability to interact with the outside world — search the web, read files, call APIs, and more.

Without tools, agents can only use their training knowledge. With tools, they become truly useful.

## Built-in Tools

Install the tools package:

```bash
pip install 'crewai[tools]'
```

Popular built-in tools:

| Tool | What It Does |
|------|-------------|
| `SerperDevTool` | Google search |
| `ScrapeWebsiteTool` | Extract content from websites |
| `FileReadTool` | Read local files |
| `DirectoryReadTool` | List directory contents |
| `PDFSearchTool` | Search inside PDF files |
| `CSVSearchTool` | Query CSV data |

## Using a Tool

```python
from crewai import Agent
from crewai_tools import SerperDevTool

search = SerperDevTool()

researcher = Agent(
    role="Web Researcher",
    goal="Find current information online",
    backstory="You verify facts using web searches.",
    tools=[search]
)
```

The agent will automatically decide when to use the search tool.

## Task-Level Tools

You can also assign tools to specific tasks:

```python
task = Task(
    description="Search for recent news about AI regulation.",
    expected_output="Summary of 3 recent articles.",
    agent=researcher,
    tools=[search]  # only available for this task
)
```

## Multiple Tools

Agents can have several tools:

```python
from crewai_tools import SerperDevTool, ScrapeWebsiteTool, FileReadTool

researcher = Agent(
    role="Research Analyst",
    goal="Gather and analyze information",
    backstory="Expert at finding and processing data.",
    tools=[SerperDevTool(), ScrapeWebsiteTool(), FileReadTool()]
)
```

## Environment Variables

Most tools need API keys:

```bash
export SERPER_API_KEY="your-serper-key"
export OPENAI_API_KEY="your-openai-key"
```

## Tips

1. Give agents only the tools they need — fewer tools = better focus
2. Test tools individually before adding them to agents
3. Check API key requirements for each tool
4. Use `verbose=True` to see when tools are called

## Summary

Tools extend what agents can do. Use built-in tools for common tasks like web search and file reading. Assign tools at the agent or task level.

---

**Next:** Memory and context management.
