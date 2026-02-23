---
title: "Vector Search vs. Reasoning-Based Retrieval"
weight: 4
bookToc: true
---

# Vector Search vs. Reasoning-Based Retrieval

## Two Approaches to Finding Information

There are fundamentally two ways a computer can find information in a document:

### Approach 1: Vector Search (Traditional)

1. Break the document into small chunks (usually 200-500 words each)
2. Convert each chunk into a list of numbers (a "vector") using a mathematical model
3. When a user asks a question, convert the question into numbers too
4. Find chunks whose numbers are closest to the question's numbers
5. Return those chunks to the AI to generate an answer

### Approach 2: Reasoning-Based Retrieval (PageIndex)

1. Analyze the entire document to understand its structure
2. Build a hierarchical tree with section titles, summaries, and page ranges
3. When a user asks a question, use AI to reason through the tree
4. Navigate to the most relevant sections based on understanding
5. Extract the full context from those sections

## Comparing the Two Approaches

| Feature | Vector Search | PageIndex |
|---------|--------------|-----------|
| **How it finds info** | Mathematical similarity | AI reasoning |
| **Document structure** | Ignored (chunks are independent) | Preserved (tree hierarchy) |
| **Context** | Lost (small chunks) | Maintained (full sections) |
| **Requires database** | Yes (vector database) | No |
| **Chunking needed** | Yes | No |
| **Explainability** | Low ("these numbers are close") | High ("section 3.2 is about debt") |

## When Vector Search Struggles

Vector search has particular problems with:

- **Tables and numbers**: "Revenue of $5.2 billion" and "Total income was 5,200 million" have very different words but mean the same thing
- **Negation**: "The company did NOT report losses" and "The company reported losses" look very similar as vectors
- **Multi-step reasoning**: Finding information that requires understanding relationships between different sections

## When PageIndex Shines

PageIndex excels when:

- Documents are long and well-structured (reports, manuals, textbooks)
- Questions require understanding context
- Accuracy matters more than speed
- You need to explain *where* an answer came from

## A Simple Analogy

- **Vector search** is like searching a library by scanning every page of every book for matching words.
- **PageIndex** is like asking a librarian who has read every book and can reason about where to find what you need.

## Summary

Vector search relies on mathematical similarity, which often confuses "similar" with "relevant." PageIndex uses AI reasoning over document structure, achieving higher accuracy — especially for complex, professional documents.
