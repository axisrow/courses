---
title: "Architecture Deep Dive"
weight: 1
bookToc: true
---

# Architecture Deep Dive

## System Overview

PageIndex consists of several interconnected components that work together to transform raw documents into searchable tree structures. This lesson examines the internal architecture.

## Core Modules

### page_index.py — The Main Engine

This is the heart of PageIndex. It contains the logic for:

- **TOC Detection** (`find_toc_pages`, `toc_detector_single_page`): Scans pages to find table of contents
- **TOC Extraction** (`toc_extractor`, `extract_toc_content`): Extracts and cleans TOC content
- **TOC Transformation** (`toc_transformer`): Converts raw TOC text into structured JSON
- **Page Mapping** (`toc_index_extractor`, `calculate_page_offset`): Maps logical page numbers to physical PDF pages
- **Verification** (`verify_toc`, `check_title_appearance`): Validates the accuracy of the generated tree
- **Error Correction** (`fix_incorrect_toc`, `fix_incorrect_toc_with_retries`): Fixes incorrect page assignments
- **Recursive Decomposition** (`process_large_node_recursively`): Breaks large sections into subsections

### utils.py — Utility Functions

Provides helper functions for:
- OpenAI API communication (sync and async)
- Token counting
- JSON extraction and parsing
- Post-processing of tree structures
- PDF text extraction

### config.yaml — Default Configuration

Stores default parameters:

```yaml
model: "gpt-4o-2024-11-20"
toc_check_page_num: 20
max_page_num_each_node: 10
max_token_num_each_node: 20000
if_add_node_id: "yes"
if_add_node_summary: "yes"
if_add_doc_description: "no"
if_add_node_text: "no"
```

## The Processing Pipeline

```
PDF Input
  │
  ▼
Extract page text & token counts
  │
  ▼
Detect TOC (scan first N pages)
  │
  ├─ TOC with page numbers → Extract, map offsets, verify
  ├─ TOC without page numbers → Extract, scan for pages, verify
  └─ No TOC → Generate structure from full document
  │
  ▼
Verify accuracy (check title ↔ page matches)
  │
  ├─ Accuracy ≥ 60% → Fix incorrect entries
  └─ Accuracy < 60% → Fall back to next strategy
  │
  ▼
Recursive decomposition of large nodes
  │
  ▼
Add node IDs, summaries, descriptions
  │
  ▼
Output JSON tree
```

## Concurrency Model

PageIndex uses Python's `asyncio` with `asyncio.gather` for concurrent processing:

- Title appearance checks run concurrently across all nodes
- Error correction processes multiple incorrect entries simultaneously
- Large node decomposition runs in parallel for sibling nodes

This significantly speeds up processing of large documents.

## The Meta-Processor Pattern

The `meta_processor` function implements a strategy pattern with automatic fallback:

1. Try the most information-rich strategy first (TOC with page numbers)
2. If accuracy is below threshold, fall back to the next strategy
3. Continue falling back until a strategy succeeds or all options are exhausted

This makes PageIndex robust against documents with poor or missing TOCs.

## Summary

PageIndex's architecture is a pipeline of detection, extraction, mapping, verification, and correction — with smart fallbacks and concurrent processing. Understanding these components helps when customizing or extending the system.
