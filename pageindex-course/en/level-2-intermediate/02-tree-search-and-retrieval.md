---
title: "Tree Search and Retrieval"
weight: 2
bookToc: true
---

# Tree Search and Retrieval

## From Tree to Answers

Once PageIndex has built a tree structure, the second phase begins: using that tree to find relevant information for a user's question. This is called **tree search**.

## How Tree Search Works

Tree search is inspired by **AlphaGo**, the AI that beat the world champion in Go. Just as AlphaGo evaluates possible moves on a game board, PageIndex evaluates possible paths through the document tree.

The process works top-down:

1. **Start at the root** — Look at all top-level sections
2. **Evaluate relevance** — The LLM reads section titles and summaries, then reasons about which sections might contain the answer
3. **Descend into the most promising branch** — Move deeper into the tree
4. **Repeat** — Continue until reaching the most specific, relevant section
5. **Extract content** — Pull the actual text from the identified pages

## An Example Walkthrough

**Question**: *"What was the company's revenue growth rate in Q3?"*

```
Annual Report 2023
├── Letter to Shareholders          → Possibly relevant
├── Company Overview                → Unlikely
├── Financial Statements            → Very likely ✓
│   ├── Income Statement            → Very likely ✓
│   │   ├── Quarterly Breakdown     → Most relevant ✓✓
│   │   └── Annual Summary          → Less relevant
│   ├── Balance Sheet               → Not relevant
│   └── Cash Flow Statement         → Not relevant
└── Risk Factors                    → Not relevant
```

The LLM reasons through each level, quickly narrowing down to "Quarterly Breakdown" within "Income Statement."

## Why This Is Better Than Flat Search

| Flat Search | Tree Search |
|-------------|-------------|
| Searches all 300 pages | Searches 3-4 levels of the tree |
| Returns fragments without context | Returns full sections with context |
| Can't explain why a result was chosen | Shows the reasoning path |
| Misses related nearby content | Captures the entire relevant section |

## The Role of Summaries

Each node in the tree includes a **summary** — a brief description of what that section covers. These summaries are crucial for tree search because they help the LLM make informed decisions without reading the full text of every section.

For example, a summary might say: *"This section covers quarterly financial results, including revenue, operating expenses, and net income for each quarter of fiscal year 2023."*

## Retrieval with Context

When PageIndex identifies the relevant section, it doesn't just return a small snippet. It returns the content with its **full context**:

- What section it belongs to
- What page range it covers
- How it fits into the overall document structure

This context makes the AI's final answer more accurate and traceable.

## Summary

Tree search uses LLM reasoning to navigate the document hierarchy level by level, quickly reaching the most relevant section. Combined with node summaries and full-context extraction, this produces more accurate and explainable results than traditional flat search.
