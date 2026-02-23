---
title: "Voice, Notifications, and Files"
weight: 9
bookToc: true
---

# Voice, Notifications, and Files

## Voice Chat

Sentient supports full voice conversations:

- **Speech-to-Text** — Powered by **Deepgram**. Your voice is transcribed in real time.
- **Text-to-Speech** — Powered by **ElevenLabs**. Sentient reads its responses aloud with natural-sounding voices.
- **Audio processing** — The client includes an `audioProcessor.js` that handles microphone input in the browser.

### Setting Up Voice

1. Add your Deepgram API key to the server `.env` file.
2. Add your ElevenLabs API key to the server `.env` file.
3. Click the microphone icon in the chat interface.

## Push Notifications

Sentient can send browser push notifications using **Web Push** (via the `pywebpush` library). This is useful when:

- A background task completes.
- A triggered task fires.
- Sentient has a proactive suggestion for you.

### Enabling Notifications

1. Allow notifications in your browser when prompted.
2. The service worker (`sw.js`) handles receiving push messages even when the tab is closed.

## File Handling

You can upload files to Sentient during a conversation. The server's `files` module handles:

- File upload and storage.
- Passing file contents to the AI for analysis.
- Generating files (e.g., charts via **QuickChart**).

### Supported Use Cases

- Upload a PDF and ask Sentient to summarize it.
- Upload a spreadsheet and ask for analysis.
- Ask Sentient to create a chart and download it.

## Summary

Voice makes Sentient hands-free, notifications keep you informed, and file handling extends what you can do in conversations. These features combine to make Sentient a versatile daily companion.
