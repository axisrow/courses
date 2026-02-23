---
title: "Your First Conversation"
weight: 4
bookToc: true
---

# Your First Conversation

## Opening the Chat

After starting Sentient (see Lesson 3), open your browser to `http://localhost:3000`. You'll see a clean chat interface similar to ChatGPT.

## Text Chat

Simply type your question or request in the text box and press **Enter**. Sentient will respond in real time via a streaming connection (WebSocket).

Try these to get started:

- "Hi, who are you?"
- "What's the weather like today?"
- "Summarize this article: [paste a URL]"

## Voice Chat

Sentient supports voice input and output. Click the **microphone** icon to start speaking. Your speech is converted to text using Deepgram, processed by the AI, and the response is read back to you using ElevenLabs text-to-speech.

> **Tip:** Voice chat works best with a good microphone and a quiet room.

## Understanding Responses

Sentient's responses may include:

- **Plain text** — A direct answer to your question.
- **Tool calls** — If Sentient decides to check your calendar or search the web, it will show you what tool it's using.
- **Memory updates** — Sentient may note something about you ("User prefers morning meetings") and remember it for later.

## Keyboard Shortcuts

Sentient has a command palette (similar to VS Code). Press `Ctrl+K` (or `Cmd+K` on Mac) to search for actions quickly.

## Summary

You've had your first conversation! Sentient can answer questions, use voice, and even call external tools. Next, we'll dive deeper into how Sentient remembers things about you.
