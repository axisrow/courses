---
title: "Agents and Tools"
weight: 10
bookToc: true
---

# Agents and Tools

## What is an Agent?

An agent is an LLM that decides which actions to take. Instead of following a fixed chain, it reasons about what tool to use and when to stop.

## Defining Tools

```python
from langchain_core.tools import tool

@tool
def multiply(a: int, b: int) -> int:
    """Multiply two numbers."""
    return a * b

@tool
def add(a: int, b: int) -> int:
    """Add two numbers."""
    return a + b

tools = [multiply, add]
```

## Built-in Tools

```python
# pip install langchain-community duckduckgo-search
from langchain_community.tools import DuckDuckGoSearchRun

search = DuckDuckGoSearchRun()
result = search.invoke("LangChain latest version")
```

## Creating an Agent

```python
from langchain_openai import ChatOpenAI
from langgraph.prebuilt import create_react_agent

llm = ChatOpenAI(model="gpt-4o-mini")

agent = create_react_agent(llm, tools)

result = agent.invoke(
    {"messages": [{"role": "user", "content": "What is 15 * 37?"}]}
)

print(result["messages"][-1].content)
```

## How Agents Work

1. LLM receives the user question and tool descriptions
2. LLM decides to call a tool (or answer directly)
3. Tool runs and returns a result
4. LLM sees the result and decides next step
5. Repeat until the LLM has a final answer

## Agent with Memory

```python
from langgraph.checkpoint.memory import MemorySaver

memory = MemorySaver()
agent = create_react_agent(llm, tools, checkpointer=memory)

config = {"configurable": {"thread_id": "user-1"}}

agent.invoke(
    {"messages": [{"role": "user", "content": "My name is Alice"}]},
    config=config,
)

result = agent.invoke(
    {"messages": [{"role": "user", "content": "What is my name?"}]},
    config=config,
)
```

## Summary of Level 2

You now know how to:
- Add memory to conversations
- Load and split documents
- Use vector stores for semantic search
- Build RAG pipelines
- Create agents with tools

Next level: advanced topics like custom chains, streaming, and deployment.
