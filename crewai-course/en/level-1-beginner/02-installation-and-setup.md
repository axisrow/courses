---
title: "Installation and Setup"
weight: 2
bookToc: true
---

# Installation and Setup

## Requirements

- Python 3.10 or higher
- An API key from OpenAI (or another LLM provider)
- pip or uv package manager

## Install CrewAI

The simplest way:

```bash
pip install crewai
```

To include built-in tools:

```bash
pip install 'crewai[tools]'
```

## Using the CLI

CrewAI comes with a command-line tool to scaffold projects:

```bash
crewai create crew my_project
```

This creates a folder structure with templates for agents, tasks, and configuration.

## Set Your API Key

CrewAI uses LLMs under the hood. Set your OpenAI key:

```bash
export OPENAI_API_KEY="sk-your-key-here"
```

Or add it to a `.env` file in your project:

```
OPENAI_API_KEY=sk-your-key-here
```

## Verify Installation

```python
import crewai
print(crewai.__version__)
```

If this prints a version number, you're good to go.

## Project Structure

When you use `crewai create crew`, you get:

```
my_project/
├── src/
│   └── my_project/
│       ├── config/
│       │   ├── agents.yaml
│       │   └── tasks.yaml
│       ├── crew.py
│       └── main.py
├── pyproject.toml
└── README.md
```

- `agents.yaml` — define your agents
- `tasks.yaml` — define your tasks
- `crew.py` — assemble the crew
- `main.py` — entry point

## Summary

Install CrewAI with pip, set up your API key, and optionally use the CLI to scaffold a project. Now you're ready to create your first agents.

---

**Next:** Understanding Agents in depth.
