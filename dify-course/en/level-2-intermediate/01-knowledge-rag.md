---
title: "Knowledge Base & RAG"
weight: 1
bookToc: true
---

# Knowledge Base & RAG

## What is RAG?

RAG (Retrieval-Augmented Generation) lets your AI answer questions using your own documents. Instead of relying only on training data, the AI searches your files first.

## How It Works

1. You upload documents (PDF, TXT, Markdown, HTML)
2. Dify splits them into chunks and creates embeddings
3. When a user asks a question, Dify finds relevant chunks
4. The LLM uses those chunks to generate an answer

## Creating a Knowledge Base

1. Go to **Knowledge** → **Create Knowledge Base**
2. Name it (e.g., "Company Docs")
3. Upload files or paste text
4. Choose chunking settings:
   - **Automatic** — Dify decides chunk size
   - **Custom** — you set chunk size and overlap
5. Choose an embedding model
6. Click **Save and Process**

## Connecting to Your App

1. Open your app in **Studio**
2. In the **Context** section, click **Add**
3. Select your knowledge base
4. Set **Top K** (how many chunks to retrieve, default: 3)
5. Set **Score Threshold** (minimum relevance, e.g., 0.5)

## Chunking Tips

| Setting | Small Chunks (200 tokens) | Large Chunks (1000 tokens) |
|---------|--------------------------|---------------------------|
| **Precision** | Higher | Lower |
| **Context** | Less surrounding info | More surrounding info |
| **Best for** | FAQ, definitions | Long explanations |

## Testing RAG

In the preview, ask questions about your documents. Check:
- Does the AI find the right information?
- Are citations accurate?
- Does it say "I don't know" when info isn't in the docs?

## Next Step

Let's connect your app to external services via API!
