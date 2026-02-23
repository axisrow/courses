---
title: "Verification and Error Correction"
weight: 3
bookToc: true
---

# Verification and Error Correction

## Why Verification Matters

LLMs can make mistakes. A generated tree might assign a section to the wrong page. PageIndex includes a robust verification and correction system to catch and fix these errors.

## The Verification Process

### Step 1: Title Appearance Check

For each section in the tree, PageIndex asks the LLM: *"Does this section title appear on this page?"*

The function `check_title_appearance` takes a section's title and its assigned page, then verifies the match using fuzzy comparison. This handles minor formatting differences (extra spaces, capitalization).

### Step 2: Calculate Accuracy

After checking all (or a random sample of) sections:

```
accuracy = correct_count / total_checked
```

### Step 3: Decision Logic

Based on accuracy, PageIndex decides what to do:

| Accuracy | Action |
|----------|--------|
| 100% | Accept the tree as-is |
| 60-99% | Attempt to fix incorrect entries |
| Below 60% | Fall back to a different strategy |

## The Error Correction Process

When sections are incorrectly mapped, PageIndex tries to fix them:

### Finding the Correct Page

For each incorrect entry, PageIndex:

1. **Finds boundaries** — Looks at the nearest correct entries before and after the incorrect one
2. **Extracts that page range** — Gets the text from those pages
3. **Asks the LLM** — "In this text, where does this section start?"
4. **Verifies the fix** — Checks if the new page assignment is correct

### Retry Logic

The correction process uses retries with a maximum of 3 attempts:

```
Round 1: Fix all incorrect entries
  ↓ (check results)
Round 2: Fix remaining incorrect entries
  ↓ (check results)
Round 3: Fix remaining incorrect entries
  ↓ (accept whatever remains)
```

Each round narrows down the set of incorrect entries.

## Validation Guards

### Physical Index Validation

Before verification, PageIndex validates that all page numbers make sense:

- No page number should exceed the total document length
- Page numbers should be positive integers
- Entries with impossible page numbers are set to `None`

### Start Position Check

PageIndex also checks whether a section starts at the **beginning** of its assigned page or somewhere in the middle. This helps with edge cases where a section title appears on a page but doesn't actually start there.

## The Fallback Chain

If verification reveals the tree is unreliable:

1. **TOC with page numbers** → accuracy too low → fall back to:
2. **TOC without page numbers** → accuracy too low → fall back to:
3. **Generate from scratch** → if this also fails → raise an exception

This three-level fallback ensures PageIndex handles even the most difficult documents.

## Summary

PageIndex's verification system checks every section's page assignment, fixes errors through an iterative correction process, and falls back to alternative strategies when needed. This multi-layered approach is key to achieving 98%+ accuracy.
