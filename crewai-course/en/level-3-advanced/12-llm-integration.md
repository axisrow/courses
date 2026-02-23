---
title: "Integrating Different LLMs"
weight: 12
bookToc: true
---

# Integrating Different LLMs

## Beyond OpenAI

CrewAI works with many LLM providers. You can even use different models for different agents.

## Supported Providers

| Provider | Model Example |
|----------|--------------|
| OpenAI | `gpt-4o`, `gpt-4o-mini` |
| Anthropic | `anthropic/claude-sonnet-4-20250514` |
| Google | `gemini/gemini-pro` |
| Ollama (local) | `ollama/llama3` |
| Azure OpenAI | `azure/gpt-4o` |

## Setting the LLM per Agent

```python
researcher = Agent(
    role="Researcher",
    goal="Find information",
    backstory="Expert researcher.",
    llm="gpt-4o"
)

writer = Agent(
    role="Writer",
    goal="Write content",
    backstory="Skilled writer.",
    llm="anthropic/claude-sonnet-4-20250514"
)
```

## Using Local Models with Ollama

```bash
# Install and start Ollama
ollama pull llama3
ollama serve
```

```python
agent = Agent(
    role="Local Analyst",
    goal="Analyze data using local AI",
    backstory="You run entirely on local hardware.",
    llm="ollama/llama3"
)
```

## Environment Variables

```bash
# OpenAI
export OPENAI_API_KEY="sk-..."

# Anthropic
export ANTHROPIC_API_KEY="sk-ant-..."

# Azure
export AZURE_API_KEY="..."
export AZURE_API_BASE="https://your-resource.openai.azure.com"
export AZURE_API_VERSION="2024-02-01"
```

## Mixed Crews

Use expensive models for complex tasks and cheaper ones for simple tasks:

```python
# Complex reasoning - use powerful model
analyst = Agent(
    role="Senior Analyst",
    goal="Deep analysis of market data",
    backstory="Expert analyst.",
    llm="gpt-4o"
)

# Simple formatting - use cheaper model
formatter = Agent(
    role="Formatter",
    goal="Format reports nicely",
    backstory="You format text into clean markdown.",
    llm="gpt-4o-mini"
)
```

## Tips

1. **Match model to task complexity** — don't use GPT-4 for simple formatting
2. **Use local models** for sensitive data that shouldn't leave your machine
3. **Test with cheaper models first**, then upgrade where needed
4. **Check rate limits** — different providers have different limits

## Summary

CrewAI supports multiple LLM providers. Assign different models to different agents to optimize for cost, speed, and capability.

---

**Next:** Deploying CrewAI to production.
