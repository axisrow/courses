---
title: "Architecture Overview"
weight: 2
bookToc: true
---

# Architecture Overview

## The Big Picture

Sentient has two main parts:

1. **Client (Frontend)** — A web application built with Next.js. This is what you see and interact with in your browser.
2. **Server (Backend)** — A Python application built with FastAPI. This is the brain that processes your messages, talks to AI models, and connects to external services.

## Supporting Services

Behind the scenes, several services keep everything running:

| Service | Role |
|---|---|
| **Redis** | Fast in-memory cache and message broker for background tasks. |
| **PostgreSQL + pgvector** | Stores structured data and vector embeddings for memory search. |
| **ChromaDB** | An additional vector database for semantic search of memories. |
| **LiteLLM** | A proxy that lets Sentient talk to many different AI models (OpenAI, Google Gemini, local models via Ollama, etc.). |
| **Celery Workers** | Run background and scheduled tasks without blocking the main server. |

## How a Message Flows

1. You type a message in the web interface (Client).
2. The Client sends it to the Server via a WebSocket connection.
3. The Server checks your memories and context, then sends everything to an AI model through LiteLLM.
4. The AI model responds. If it decides to use a tool (e.g., check your calendar), the Server calls the appropriate **MCP server** (more on those later).
5. The final answer travels back through the WebSocket to your browser.

## MCP Hub — The Integration Layer

MCP stands for **Model Context Protocol**. Sentient uses small MCP servers to connect to external apps: Gmail, Google Calendar, Slack, Notion, Trello, GitHub, and many more. Each MCP server knows how to authenticate and talk to one specific service.

## Summary

Sentient = **Web UI** + **Python API server** + **databases** + **AI models** + **MCP integrations**. Understanding these building blocks will help you in later lessons when we set everything up.
