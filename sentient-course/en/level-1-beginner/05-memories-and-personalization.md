---
title: "Memories and Personalization"
weight: 5
bookToc: true
---

# Memories and Personalization

## What Are Memories?

Sentient doesn't just answer questions — it **remembers** things about you. These memories are stored securely in a database and used to personalize future interactions.

For example, if you mention "I'm a vegetarian," Sentient will remember this and avoid suggesting steak restaurants when you ask for dinner ideas.

## How Memories Work

1. During a conversation, the AI identifies useful facts about you.
2. These facts are stored as **vector embeddings** in PostgreSQL (pgvector) and ChromaDB.
3. In future conversations, Sentient searches these memories to find relevant context.

This means Sentient gets **better over time** — the more you talk to it, the more personalized it becomes.

## Viewing Your Memories

The Sentient interface has a dedicated **Memories** page where you can:

- See all stored memories.
- Delete specific memories you no longer want Sentient to remember.
- Understand how memories influence responses.

## Privacy and Control

Because Sentient is open-source and self-hostable, your memories never leave your machine unless you choose a cloud deployment. You are always in control.

## Types of Information Sentient Remembers

- Your name, job, and preferences.
- Important dates and deadlines.
- Communication style preferences.
- Frequently asked topics.
- Goals and habits you've shared.

## Summary

Memories are what make Sentient truly *personal*. It learns about you over time and tailors its behavior accordingly. In Level 2, we'll explore how to connect external apps and create powerful automated tasks.
