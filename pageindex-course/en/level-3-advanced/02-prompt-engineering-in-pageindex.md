---
title: "Prompt Engineering in PageIndex"
weight: 2
bookToc: true
---

# Prompt Engineering in PageIndex

## How PageIndex Talks to the LLM

PageIndex relies heavily on carefully crafted prompts to guide the LLM through various tasks. Understanding these prompts reveals how the system achieves its accuracy.

## Types of Prompts

### 1. Detection Prompts

Used to detect if a page contains a table of contents:

```
Your job is to detect if there is a table of content
provided in the given text.
...
Please note: abstract, summary, notation list, figure list,
table list, etc. are not table of contents.
```

Key design choices:
- Explicitly excludes common false positives (figure lists, notation lists)
- Asks for structured JSON output with a "thinking" field
- Binary yes/no decision

### 2. Extraction Prompts

Used to extract and structure TOC content:

```
Your job is to transform the whole table of content
into a JSON format included table_of_contents.
Structure is the numeric system which represents the index
of the hierarchy section...
```

Key design choices:
- Defines the exact output format with examples
- Explains what "structure" means (the numbering system)
- Handles continuation for long TOCs that exceed token limits

### 3. Verification Prompts

Used to check if a section title actually appears on a given page:

```
Your job is to check if the given section appears or
starts in the given page_text.
Note: do fuzzy matching, ignore any space inconsistency.
```

Key design choices:
- Uses fuzzy matching to handle formatting differences
- Asks for reasoning ("thinking" field) before the answer
- Simple binary output

### 4. Structure Generation Prompts

Used when no TOC exists and the structure must be generated from content:

```
You are an expert in extracting hierarchical tree structure,
your task is to generate the tree structure of the document.
The provided text contains tags like <physical_index_X>...
```

Key design choices:
- Uses special page boundary tags (`<physical_index_X>`) to help the LLM track page numbers
- Asks for original titles (not paraphrased)
- Continuation prompts build on previous structure

## The "Thinking" Pattern

Most PageIndex prompts include a `"thinking"` field in the expected output:

```json
{
    "thinking": "<why do you think...>",
    "answer": "yes or no"
}
```

This is a form of **chain-of-thought prompting** — forcing the LLM to reason before answering improves accuracy.

## Handling Long Documents

When a document is too long for a single prompt, PageIndex:

1. Divides pages into groups (with overlap for continuity)
2. Processes the first group with an "init" prompt
3. Processes subsequent groups with "continue" prompts that include previous results
4. Checks completeness after each step

## Error Recovery in Prompts

PageIndex includes validation loops:
- After each LLM response, it checks if the output is complete
- If not, it sends a continuation prompt
- Maximum retry limits prevent infinite loops

## Summary

PageIndex's prompts are carefully designed with structured output formats, chain-of-thought reasoning, fuzzy matching, and continuation strategies. These design patterns are key to achieving high accuracy in tree generation.
