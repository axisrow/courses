---
title: "Multi-Agent Collaboration"
weight: 9
bookToc: true
---

# Multi-Agent Collaboration

## What Is Multi-Agent Collaboration?

Sometimes a single agent isn't enough for a complex task. Nexent supports **multi-agent collaboration**, where a manager agent coordinates several specialized agents to complete a job together.

## How It Works

1. A **manager agent** receives your request.
2. It breaks the task into sub-tasks.
3. Each sub-task is assigned to a **managed agent** with the right skills.
4. The managed agents complete their parts and report back.
5. The manager compiles the final answer.

## Example Scenario

Imagine you ask: *"Analyze our Q3 sales data, compare it with industry trends, and write an executive summary."*

The manager might delegate:

- **Data Agent** — reads your sales spreadsheet.
- **Research Agent** — searches the web for industry trends.
- **Writing Agent** — composes the executive summary.

## Setting Up Multi-Agent Workflows

1. Create each specialized agent with a focused description.
2. Create a manager agent and link it to the specialized agents.
3. In the manager's configuration, define which agents it can call.
4. Chat with the manager — it will orchestrate the others automatically.

## Benefits

- **Better results** — each agent focuses on what it does best.
- **Faster processing** — sub-tasks can run in parallel.
- **Modular design** — update one agent without affecting the others.

## Monitoring Collaboration

In the chat interface, you can see which agents were involved in answering your question. Each agent's contribution is tracked and visible.

## Practice Exercise

1. Create two specialized agents (e.g., a researcher and a writer).
2. Create a manager agent that coordinates them.
3. Give the manager a complex task that requires both skills.
4. Observe how the work is distributed.
