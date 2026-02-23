---
title: "Vector Databases and the Memory System"
weight: 13
bookToc: true
---

# Vector Databases and the Memory System

## Why Vector Databases?

Traditional databases search by exact matches. But memories are fuzzy — "User likes Italian food" should match the query "restaurant recommendations." **Vector databases** solve this by storing text as numerical vectors and finding similar meanings.

## Sentient's Dual-Database Approach

Sentient uses two vector stores:

| Database | Purpose |
|---|---|
| **PostgreSQL + pgvector** | Primary storage for memories with full SQL capabilities. |
| **ChromaDB** | Lightweight semantic search optimized for fast retrieval. |

## How Memories Are Created

1. During a conversation, the AI identifies noteworthy facts.
2. The server's `memories` module extracts and deduplicates them.
3. Each memory is converted to a **vector embedding** (a list of numbers representing meaning).
4. The embedding and original text are stored in both pgvector and ChromaDB.

## How Memories Are Retrieved

1. When you send a new message, the server creates an embedding of your message.
2. It queries both vector databases for the **most similar** stored memories.
3. The top results are injected into the AI's context as "things I know about this user."
4. The AI uses this context to personalize its response.

## Key Code Locations

- `src/server/main/memories/` — Memory CRUD operations and API routes.
- `src/server/main/vector_db.py` — Vector database abstraction layer.
- `src/server/main/db.py` — General database configuration.
- `src/server/mcp_hub/memory/` — MCP server for memory-related tools.

## Tuning Memory Retrieval

- **Top-K** — How many memories to retrieve (default: ~5–10). More context = better answers but slower.
- **Similarity threshold** — Ignore memories below a relevance score.
- **Recency bias** — Optionally prefer recent memories over old ones.

## Deleting Memories

Use the Memories page in the UI, or the helper scripts:

```bash
python src/server/delete_pg_memories.py
python src/server/delete_chroma_collection.py
```

## Summary

Vector databases are the foundation of Sentient's personalization. They enable fuzzy, meaning-based search that makes your assistant truly understand you.
