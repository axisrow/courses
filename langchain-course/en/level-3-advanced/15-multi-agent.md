---
title: "Multi-Agent Systems with LangGraph"
weight: 15
bookToc: true
---

# Multi-Agent Systems with LangGraph

## What is LangGraph?

LangGraph is a library for building stateful, multi-step applications with LLMs. It models your app as a graph of nodes and edges.

```bash
pip install langgraph
```

## Basic Graph

```python
from langgraph.graph import StateGraph, START, END
from typing import TypedDict

class State(TypedDict):
    messages: list
    next: str

def researcher(state: State) -> State:
    # Research step
    return {"messages": state["messages"] + ["Research done"]}

def writer(state: State) -> State:
    # Writing step
    return {"messages": state["messages"] + ["Article written"]}

graph = StateGraph(State)
graph.add_node("researcher", researcher)
graph.add_node("writer", writer)
graph.add_edge(START, "researcher")
graph.add_edge("researcher", "writer")
graph.add_edge("writer", END)

app = graph.compile()
result = app.invoke({"messages": [], "next": ""})
```

## Conditional Routing

```python
def router(state: State) -> str:
    last = state["messages"][-1]
    if "need more research" in last.lower():
        return "researcher"
    return "writer"

graph.add_conditional_edges("reviewer", router)
```

## Multi-Agent Pattern

```python
from langgraph.prebuilt import create_react_agent

# Create specialized agents
research_agent = create_react_agent(llm, [search_tool])
code_agent = create_react_agent(llm, [python_tool])
review_agent = create_react_agent(llm, [])

# Add as nodes in a graph
graph = StateGraph(State)
graph.add_node("researcher", research_agent)
graph.add_node("coder", code_agent)
graph.add_node("reviewer", review_agent)
```

## Human-in-the-Loop

```python
from langgraph.checkpoint.memory import MemorySaver

graph = StateGraph(State)
# ... add nodes ...
graph.add_node("human_review", lambda s: s)  # Pause point

app = graph.compile(
    checkpointer=MemorySaver(),
    interrupt_before=["human_review"],
)

# Run until pause
result = app.invoke(input, config)

# Human reviews, then continue
app.invoke(None, config)
```

## Course Summary

Congratulations! You have completed the LangChain course. You learned:

1. **Beginner**: Models, prompts, templates, chains
2. **Intermediate**: Memory, documents, vector stores, RAG, agents
3. **Advanced**: LCEL, streaming, evaluation, deployment, multi-agent systems

Keep building and exploring the LangChain ecosystem!
