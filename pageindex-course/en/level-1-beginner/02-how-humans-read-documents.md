---
title: "How Humans Read Documents"
weight: 2
bookToc: true
---

# How Humans Read Documents

## The Natural Way We Navigate Information

When you pick up a thick book or report, you don't start reading from page one. Instead, you:

1. **Look at the table of contents** — to understand what the document covers
2. **Identify the relevant section** — based on what you need
3. **Navigate to that section** — flipping to the right page
4. **Read in context** — understanding the information within its surrounding content

This is exactly how PageIndex works. It mimics this natural human behavior.

## Why Traditional AI Search Fails

Traditional AI search (vector-based RAG) works more like this:

1. Chop the document into hundreds of small pieces
2. Convert each piece into a list of numbers
3. Convert your question into numbers too
4. Find pieces whose numbers are "close" to your question's numbers

The problem? This approach:
- **Loses context** — a paragraph about revenue means different things in different sections
- **Confuses similarity with relevance** — words that sound alike aren't always what you need
- **Ignores structure** — it doesn't know that Section 3.2 is a subsection of Section 3

## The PageIndex Approach

PageIndex follows the human approach:

| Step | Human Expert | PageIndex |
|------|-------------|-----------|
| 1 | Look at table of contents | Build a tree structure from the document |
| 2 | Think about which section is relevant | Use AI reasoning to evaluate sections |
| 3 | Go to the right page | Navigate the tree to the right node |
| 4 | Read in context | Extract the relevant content with full context |

## A Real Example

Suppose you ask: *"What were the company's total liabilities in 2023?"*

- **Vector search** might find paragraphs containing the word "liabilities" — but could return results from 2022 or from a different context.
- **PageIndex** would look at the tree, reason that this information is likely in the "Financial Statements" section under "Balance Sheet," and go directly there.

## Summary

PageIndex works the way you do — by understanding document structure and reasoning about where to find information, not by blindly matching words.
