---
title: "Basic Search"
weight: 4
bookToc: true
---

# Basic Search

## Three Ways to Search

QMD gives you three search commands, from simplest to most powerful:

| Command | Method | Speed | Best For |
|---------|--------|-------|----------|
| `qmd search` | Keywords (BM25) | Fast | Exact terms you know |
| `qmd vsearch` | Semantic (AI) | Medium | Concepts and meaning |
| `qmd query` | Hybrid (all combined) | Slower | Best overall results |

## Keyword Search

This is the fastest option. It finds documents containing your exact words:

```sh
qmd search "project timeline"
```

Use this when you know the specific words in your documents.

## Semantic Search

This understands *meaning*, not just words. It can find relevant documents even when they use different terminology:

```sh
qmd vsearch "how to deploy the application"
```

For example, searching for "how to deploy" might find a document about "release process" — because the meaning is similar.

## Hybrid Search (Recommended)

This combines keyword search, semantic search, and AI re-ranking for the best results:

```sh
qmd query "quarterly planning process"
```

It's slower but gives the most accurate results.

## Understanding the Results

When you search, QMD shows you:

```
docs/guide.md:42 #a1b2c3
Title: Software Craftsmanship
Score: 93%

This section covers the craftsmanship of building
quality software with attention to detail.
```

- **Path** — where the file is (`docs/guide.md`)
- **Docid** — a short ID (`#a1b2c3`) you can use to retrieve it later
- **Title** — the document title
- **Score** — how relevant the result is (higher = better)
- **Snippet** — a preview of the matching content

## Score Guide

| Score | Meaning |
|-------|---------|
| 80–100% | Highly relevant |
| 50–80% | Moderately relevant |
| 20–50% | Somewhat relevant |
| 0–20% | Low relevance |

## Limit Results to a Collection

Search only within a specific collection:

```sh
qmd search "API" -c notes
```

## Practice Exercise

1. Run `qmd search "some keyword"` with a word you know is in your documents
2. Try `qmd vsearch` with a question about your content
3. Compare the results from `qmd search` and `qmd query` for the same query

## Next Steps

Now let's learn how to retrieve full documents and customize your output.
