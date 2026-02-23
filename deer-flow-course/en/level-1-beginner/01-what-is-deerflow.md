---
title: "What is DeerFlow"
weight: 1
bookToc: true
---

# What is DeerFlow

## Introduction

Imagine having a smart assistant that doesn't just answer questions but actually **does work**: searches the internet, writes code, creates reports, presentations, and even web pages. That's **DeerFlow**.

**DeerFlow** (Deep Exploration and Efficient Research Flow) is a free, open-source platform by ByteDance (the creators of TikTok). It's a "super agent" — an AI-powered program that can:

- 🔍 **Search for information** on the internet
- 💻 **Write and run code** in a secure environment
- 📝 **Create documents**, reports, and presentations
- 🧠 **Remember** your preferences across sessions
- 👥 **Delegate tasks** to helper agents

## Key Concepts

### What is an "Agent"?

An **agent** is an AI-powered program that can independently make decisions and take actions. Unlike a regular chatbot, an agent doesn't just reply with text — it can call tools, run code, and interact with external services.

### What is a "Super Agent"?

A **super agent** is an agent that manages other agents. It receives your task, breaks it into parts, and assigns each part to a separate helper (sub-agent). Think of it as a team leader who distributes work.

### What is a "Sandbox"?

A **sandbox** is an isolated environment for running code. Code runs in a separate container and cannot harm your computer. Think of it as a room where you can experiment without consequences.

## How It Works (Simplified)

```
You give a task
       ↓
Lead Agent analyzes the task
       ↓
Breaks into subtasks → Launches sub-agents
       ↓
Sub-agents use tools:
  • Web search
  • Code writing
  • File creation
       ↓
Results are collected → You receive the final answer
```

## How DeerFlow Differs from ChatGPT

| Feature | ChatGPT | DeerFlow |
|---------|---------|----------|
| Answers questions | ✅ | ✅ |
| Own file system | ❌ | ✅ |
| Code execution in sandbox | Limited | ✅ Full |
| Sub-agents | ❌ | ✅ |
| Long-term memory | Limited | ✅ |
| Open source | ❌ | ✅ |
| Choose any AI model | ❌ | ✅ |

## What Can You Do with DeerFlow?

- **Research**: give a topic — get a detailed report with sources
- **Programming**: describe a task — get working code
- **Presentations**: give a topic — get a slide deck
- **Web pages**: describe a design — get HTML/CSS
- **Data analysis**: upload a file — get visualizations and insights
- **Automation**: any multi-step tasks

## Summary

- DeerFlow is an open-source "super agent" platform
- It can not only answer but perform real tasks
- Uses sub-agents, sandbox, memory, and extensible skills
- Works with any AI model (GPT-4, Claude, DeepSeek, etc.)
- Created by ByteDance and developed by the community

In the next lesson, we'll install DeerFlow on your computer.
