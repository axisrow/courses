---
title: "How Hybrid Search Works"
weight: 12
bookToc: true
---

# How Hybrid Search Works

## The Pipeline

When you run `qmd query`, your search goes through a sophisticated pipeline:

1. **Query Expansion** — AI generates alternative phrasings
2. **Parallel Retrieval** — each phrasing searches both keyword and vector indexes
3. **RRF Fusion** — results are merged using a mathematical formula
4. **LLM Re-ranking** — AI judges each result's relevance
5. **Position-Aware Blending** — final scores combine retrieval and reranking

## Step 1: Query Expansion

Your original query is sent to a fine-tuned local AI model that generates alternative phrasings. For example:

- Original: "how does authentication work"
- Variant 1: "user login and session management"
- Variant 2: "authentication flow and token validation"

The original query gets **2× weight** in the fusion step.

## Step 2: Parallel Retrieval

Each query variant (original + expansions) searches **both** indexes:
- **BM25 (FTS5)** — keyword matching via SQLite full-text search
- **Vector search** — semantic similarity via embeddings

This means 6 separate result lists are generated (3 queries × 2 methods).

## Step 3: Reciprocal Rank Fusion (RRF)

All result lists are merged using this formula:

```
score = Σ(1 / (k + rank + 1))    where k = 60
```

Documents that appear in multiple lists get higher scores. Results from the original query count double.

**Top-rank bonus**: Documents ranked #1 in any list get +0.05, ranks #2–3 get +0.02.

## Step 4: LLM Re-ranking

The top 30 candidates are sent to the Qwen3 Reranker model. It evaluates each document against your query and assigns a relevance score from 0 to 10.

## Step 5: Position-Aware Blending

The final score blends retrieval (RRF) and reranker scores differently based on position:

| RRF Rank | Retrieval Weight | Reranker Weight |
|----------|-----------------|-----------------|
| 1–3 | 75% | 25% |
| 4–10 | 60% | 40% |
| 11+ | 40% | 60% |

**Why?** Top retrieval results often include exact keyword matches that should be preserved. Lower-ranked results benefit more from the reranker's judgment.

## Score Interpretation

| Score | Meaning |
|-------|---------|
| 0.8–1.0 | Highly relevant |
| 0.5–0.8 | Moderately relevant |
| 0.2–0.5 | Somewhat relevant |
| 0.0–0.2 | Low relevance |

## Next Steps

Let's explore the MCP HTTP server for shared, long-running integrations.
