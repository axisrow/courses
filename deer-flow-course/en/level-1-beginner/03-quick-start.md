---
title: "Quick Start"
weight: 3
bookToc: true
---

# Quick Start

## Introduction

DeerFlow is up and running. Time to try it out! In this lesson, you'll make your first requests and see what the super agent can do.

## Opening the Web Interface

1. Make sure DeerFlow is running (`make docker-start` or `make dev`)
2. Open your browser and go to **http://localhost:2026**
3. You'll see a chat interface similar to ChatGPT

## Your First Request

Type in the chat:

```
Find information about the latest news in artificial intelligence
and write a brief overview with 5 key points.
```

### What Happens Behind the Scenes

1. The **lead agent** receives your request
2. It decides to use **web search**
3. Runs the `web_search` tool to find news
4. Uses `web_fetch` to load page contents
5. Analyzes the findings and composes a response

You'll see the process in real time — DeerFlow shows which tools it's using.

## Try Code Generation

```
Write a Python script that downloads the weather forecast
and displays the temperature for the next 3 days.
Run it and show the result.
```

DeerFlow will not only write the code but also **execute** it in the sandbox.

## Create a Document

```
Create a report about the Rust programming language:
history, advantages, and real-world use cases.
Save it as a Markdown file.
```

## Plan Mode

For complex tasks, enable **Plan Mode** — DeerFlow will first create a step list, then execute them:

```
[Enable Plan Mode in the interface]

Create a portfolio website for a photographer.
Include: home page, gallery, and contacts.
Use a modern design.
```

## File Uploads

DeerFlow supports file uploads for analysis:

1. Click the upload button
2. Select a file (PDF, Excel, Word, PowerPoint)
3. Ask the agent to analyze it

Supported formats are automatically converted to text.

## Tips

- **Be specific**: the more precise your task, the better the result
- **Break it down**: use Plan Mode for complex tasks
- **Experiment**: DeerFlow can surprise you with its capabilities
- **Verify results**: AI can make mistakes — always check important data

## Summary

- DeerFlow's web interface is at http://localhost:2026
- The agent can search, write and run code, create files
- Plan Mode helps with complex multi-step tasks
- You can upload files for analysis

In the next lesson, we'll explore the core concepts in more detail.
