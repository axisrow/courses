---
title: "Advanced Query Syntax"
weight: 11
bookToc: true
---

# Advanced Query Syntax

## Query Markup Documents

QMD has its own query language called **Query Markup Documents**. Instead of typing a single search string, you can write structured multi-line queries with different search types.

## Query Types

| Type | Method | Description |
|------|--------|-------------|
| `lex` | BM25 keyword | Exact word matching |
| `vec` | Vector semantic | Meaning-based similarity |
| `hyde` | Hypothetical document | Write what you expect the answer looks like |
| `expand` | LLM-powered | Auto-generates lex, vec, and hyde variants |

## Default Behavior

A plain query is treated as `expand:` — the AI expands it automatically:

```sh
# These are equivalent:
qmd query "how does authentication work"
qmd query "expand: how does authentication work"
```

## Lex Query Syntax

Keyword queries support special operators:

| Syntax | Meaning | Example |
|--------|---------|---------|
| `word` | Prefix match | `perf` matches "performance" |
| `"phrase"` | Exact phrase | `"rate limiter"` |
| `-word` | Exclude term | `-sports` |
| `-"phrase"` | Exclude phrase | `-"test data"` |

```sh
qmd query 'lex: "machine learning" -"deep learning"'
qmd query 'lex: auth -oauth -saml'
```

## Vec Query Syntax

Write natural language questions:

```sh
qmd query 'vec: how does the rate limiter handle burst traffic'
```

## Hyde Query Syntax

Write a hypothetical answer (50–100 words) describing what you expect the document to say:

```sh
qmd query 'hyde: The rate limiter uses a sliding window algorithm with a 60-second window. When a client exceeds 100 requests per minute, subsequent requests return 429 Too Many Requests.'
```

This is powerful because QMD searches for documents that look *like your hypothetical answer*.

## Multi-Line Queries

Combine multiple types for best results. The first query gets 2× weight:

```sh
qmd query $'lex: rate limiter algorithm\nvec: how does rate limiting work in the API\nhyde: The API implements rate limiting using a token bucket algorithm...'
```

## Constraints

- Maximum one `expand:` per query
- Lex operators (`-term`, `"phrase"`) only work in `lex` queries
- Empty lines are ignored

## Next Steps

Let's look under the hood at how hybrid search and re-ranking actually work.
