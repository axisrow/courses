---
title: "What Is PageIndex?"
weight: 1
bookToc: true
---

# What Is PageIndex?

## The Problem with Finding Information in Long Documents

Imagine you have a 300-page financial report and need to find specific information about a company's debt. You could read all 300 pages, but that would take hours. What if a computer could do it for you?

Traditional systems use something called **vector search** — they break documents into small pieces, convert them into numbers, and try to find pieces that "look similar" to your question. But **similar is not the same as relevant**. A sentence about "borrowing money" might be very relevant to your question about debt, but it doesn't look similar at all.

## How PageIndex Solves This

PageIndex takes a completely different approach. Instead of breaking documents into small pieces, it:

1. **Reads the document structure** — just like you would look at a table of contents
2. **Builds a tree** — organizing sections, subsections, and their page numbers
3. **Reasons about your question** — using AI to think through which sections are most relevant

Think of it like a librarian who knows the book inside out. Instead of searching for matching words, the librarian *understands* what you need and guides you to the right section.

## Key Terms

- **RAG** (Retrieval-Augmented Generation): A technique where AI retrieves relevant information from documents before answering your question.
- **Vector search**: The traditional way of finding similar text using mathematical representations.
- **Tree structure**: A hierarchical organization of content, like a table of contents with nested sections.
- **LLM** (Large Language Model): An AI system like ChatGPT that can understand and generate text.

## Why It Matters

PageIndex achieved **98.7% accuracy** on a financial document benchmark, significantly outperforming traditional vector-based systems. This means better, more reliable answers when working with complex professional documents.

## Summary

PageIndex is a new way to search documents that mimics how human experts read — by understanding structure and reasoning about relevance, rather than just matching words.
