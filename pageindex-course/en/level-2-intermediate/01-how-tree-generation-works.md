---
title: "How Tree Generation Works"
weight: 1
bookToc: true
---

# How Tree Generation Works

## The Two-Step Process

PageIndex operates in two main phases:

1. **Index Generation** — Build a tree structure from the document
2. **Tree Search** — Use the tree to find relevant information

This lesson focuses on the first phase: how PageIndex creates the tree.

## Step 1: Table of Contents Detection

PageIndex starts by looking at the first pages of your document (by default, the first 20 pages) to check if there's an existing table of contents (TOC).

The system uses an LLM to analyze each page and answer: *"Does this page contain a table of contents?"* If a TOC is found, PageIndex extracts it and uses it as the foundation for the tree.

There are three possible scenarios:

| Scenario | What PageIndex Does |
|----------|-------------------|
| TOC found with page numbers | Extracts TOC and maps it to physical pages |
| TOC found without page numbers | Extracts TOC, then scans the document to find page numbers |
| No TOC found | Generates a structure by analyzing the entire document |

## Step 2: Page Number Mapping

If the TOC includes page numbers, PageIndex needs to figure out the **offset** — the difference between printed page numbers and actual PDF page numbers. For example, if "Chapter 1" says "page 1" in the TOC but is actually on PDF page 5, the offset is 4.

PageIndex calculates this by:
1. Looking at the first few sections from the TOC
2. Scanning the document to find where those sections physically appear
3. Calculating the most common difference (offset)
4. Applying that offset to all TOC entries

## Step 3: Verification

After building the tree, PageIndex verifies its accuracy:

1. For each section in the tree, it checks: *"Does this section title actually appear on the page we assigned?"*
2. If accuracy is above 60%, it attempts to fix incorrect entries
3. If accuracy is too low, it falls back to a different strategy (e.g., generating the structure from scratch)

## Step 4: Handling Large Nodes

If any section covers too many pages (more than 10 by default) or too many tokens (more than 20,000), PageIndex recursively breaks it down into subsections — creating deeper levels in the tree.

## The Fallback Strategy

PageIndex has a smart fallback system:

```
Try TOC with page numbers
    ↓ (if accuracy < 60%)
Try TOC without page numbers
    ↓ (if accuracy < 60%)
Generate structure from scratch
```

This ensures reliable results regardless of document quality.

## Summary

Tree generation is an intelligent, multi-step process: detect TOC, map page numbers, verify accuracy, and handle edge cases. The system adapts its strategy based on what it finds, always aiming for the most accurate tree possible.
