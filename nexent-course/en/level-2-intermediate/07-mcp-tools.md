---
title: "MCP Tools Ecosystem"
weight: 7
bookToc: true
---

# MCP Tools Ecosystem

## What Is MCP?

MCP (Model Context Protocol) is a standard for building tools that AI agents can use. Think of it as a universal plug system: any tool built to the MCP spec can work with any Nexent agent.

## Why Tools Matter

Without tools, an agent can only generate text from its training data. With tools, it can:

- Search the internet.
- Read and process files.
- Query databases.
- Send emails or messages.
- Interact with external services.

## Built-in Tools

Nexent comes with several tools pre-installed:

| Tool | What It Does |
|------|-------------|
| Web Search | Searches 5+ search providers for fresh information |
| Knowledge Base Search | Looks up information in your uploaded documents |
| File Reader | Reads uploaded files during conversation |
| Image Generation | Creates images from text descriptions |

## Adding Remote MCP Tools

You can connect external MCP tools hosted on remote servers:

1. Go to **Settings → Tools**.
2. Click **Add Remote MCP Tool**.
3. Enter the tool's server URL and configuration.
4. The tool becomes available to all your agents.

## Using Tools in Agents

When you create or edit an agent, you can select which tools it has access to. The agent will automatically decide when to use each tool based on the conversation.

For example, if a user asks "What's the weather in Paris?", an agent with a web search tool will automatically search the web for the answer.

## The MCP Community

Nexent integrates with the broader MCP ecosystem. You can find community-built tools on:

- The [Nexent MCP Ecosystem page](https://modelengine-group.github.io/nexent/en/mcp-ecosystem/overview.html)
- Community hubs and repositories

## Practice Exercise

1. Check which tools are currently available in your Nexent installation.
2. Create an agent and give it access to web search.
3. Ask the agent a question that requires current information (e.g., today's news).
4. Observe how the agent uses the web search tool to answer.
