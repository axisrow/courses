---
title: "Embeddings and Semantic Search"
weight: 8
bookToc: true
---

# Embeddings and Semantic Search

## What Are Embeddings?

An **embedding** is a way to convert text into a list of numbers that captures its meaning. Documents with similar meanings get similar numbers, even if they use completely different words.

For example:
- "How to deploy the app" and "Release process for the application" have very similar embeddings
- "How to deploy the app" and "Best cookie recipe" have very different embeddings

## Generating Embeddings

After adding collections, generate embeddings for semantic search:

```sh
qmd embed
```

This processes all your documents through the EmbeddingGemma AI model. It runs locally on your computer.

## Re-Generating Embeddings

If you've added or changed many documents:

```sh
# Re-embed only new/changed documents
qmd embed

# Force re-embed everything
qmd embed -f
```

## How Chunking Works

Your documents might be very long. QMD splits them into chunks of about 900 tokens (roughly 700 words) for better search accuracy.

The splitting is smart:
- It prefers breaking at headings and paragraph boundaries
- Code blocks are kept together
- There's a 15% overlap between chunks so nothing falls through the cracks

## When to Use Semantic Search

Use `qmd vsearch` (semantic search) when:
- You don't know the exact words in the document
- You're asking a question in natural language
- You want to find conceptually similar content

Use `qmd search` (keyword search) when:
- You know the exact term or phrase
- You want the fastest results
- You need precise word matching

Use `qmd query` (hybrid) when:
- You want the best results regardless of speed
- You're not sure which approach will work better

## Checking Your Index

See how many documents and embeddings you have:

```sh
qmd status
```

## Next Steps

Let's explore how to use QMD with AI agents and the MCP protocol.
