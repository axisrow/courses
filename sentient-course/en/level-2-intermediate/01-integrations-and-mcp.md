---
title: "Integrations and MCP Servers"
weight: 6
bookToc: true
---

# Integrations and MCP Servers

## What Is MCP?

MCP stands for **Model Context Protocol**. It's the way Sentient connects to external services. Each integration (Gmail, Slack, Notion, etc.) is implemented as a small MCP server that knows how to:

1. Authenticate with the external service (usually via OAuth).
2. Provide a set of **tools** the AI can call.
3. Return results back to the main Sentient server.

## Available Integrations

Sentient ships with 20+ MCP servers:

| Category | Services |
|---|---|
| **Google Workspace** | Gmail, Calendar, Drive, Docs, Sheets, Slides, Tasks, Contacts, Maps |
| **Communication** | Slack, Discord, WhatsApp |
| **Productivity** | Notion, Trello, GitHub |
| **Information** | Google Search, News, AccuWeather |
| **Utilities** | File Management, QuickChart, Memory, History |

## Connecting an Integration

1. Go to the **Integrations** page in the Sentient UI.
2. Click **Connect** next to the service you want.
3. Follow the OAuth flow (sign in to the service and grant permission).
4. Once connected, Sentient can use that service in conversations and tasks.

## How the AI Uses Integrations

When you say "Check my calendar for tomorrow," the AI:

1. Recognizes it needs the Google Calendar tool.
2. Calls the `gcal` MCP server.
3. The MCP server uses your stored OAuth token to fetch events.
4. Results are returned to the AI, which formats them for you.

## The Orchestrator

The `orchestrator` MCP module coordinates complex multi-tool workflows. If a task requires reading an email (Gmail), creating a calendar event (GCal), and posting a summary to Slack — the orchestrator chains these calls together.

## Summary

MCP servers are the bridge between Sentient and the outside world. They make Sentient more than a chatbot — they make it an **action-taking agent**.
