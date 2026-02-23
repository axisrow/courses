---
title: "Multimodal Capabilities"
weight: 13
bookToc: true
---

# Multimodal Capabilities

## Beyond Text

Nexent is not limited to text conversations. It supports multiple modes of interaction:

- **Text** — standard chat.
- **Voice** — speak your questions and hear answers.
- **Images** — share pictures and get analysis.
- **Image generation** — ask the agent to create images.

## Voice Input & Output

### Setup

Voice services require a voice provider configuration. In your `.env` file, set your voice service credentials (APPID, TOKEN).

### Usage

1. Click the microphone icon in the chat.
2. Speak your question.
3. Nexent transcribes your speech and sends it to the agent.
4. The response can be read aloud or displayed as text.

## Image Understanding

### How It Works

1. Drag and drop an image into the chat.
2. Ask a question about it: *"What's in this image?"* or *"Extract the text from this receipt."*
3. The agent uses a vision-capable model to analyze the image.

### Use Cases

- **Document scanning** — extract text from photos of documents.
- **Chart analysis** — describe trends in a chart image.
- **Object identification** — identify items in photos.

## Image Generation

If your model provider supports image generation, you can ask:

> "Create an image of a sunset over mountains in watercolor style."

The agent will generate and display the image in the chat.

## Combining Modalities

The real power comes from combining modes:

- Upload a spreadsheet → ask the agent to create a chart → get an image.
- Send a photo of a whiteboard → get a structured text summary.
- Speak a question about an uploaded document → hear the answer.

## Practice Exercise

1. Upload a photo of a document (receipt, menu, or handwritten note).
2. Ask the agent to extract and organize the text.
3. Try voice input if you have voice services configured.
4. Ask the agent to generate an image based on a text description.
