---
title: "The Tree Structure Explained"
weight: 3
bookToc: true
---

# The Tree Structure Explained

## What Is a Tree Structure?

A tree structure is a way of organizing information in layers, from general to specific. You already know many tree structures:

- **A company org chart**: CEO → Departments → Teams → Individuals
- **A file system on your computer**: Folders → Subfolders → Files
- **A book's table of contents**: Parts → Chapters → Sections → Subsections

PageIndex creates exactly this kind of structure for any document.

## How PageIndex Trees Look

Here is a simplified example of a tree that PageIndex might create for an annual report:

```
Annual Report 2023
├── Letter to Shareholders (pages 1-3)
├── Company Overview (pages 4-10)
│   ├── Our Mission (pages 4-5)
│   ├── Key Products (pages 6-8)
│   └── Global Presence (pages 9-10)
├── Financial Statements (pages 11-50)
│   ├── Income Statement (pages 11-20)
│   ├── Balance Sheet (pages 21-35)
│   └── Cash Flow Statement (pages 36-50)
└── Risk Factors (pages 51-60)
```

## The JSON Format

Internally, PageIndex stores this tree as JSON (a standard data format). Each section is called a **node** and contains:

- **title**: The name of the section
- **node_id**: A unique identifier
- **start_index**: The first page of this section
- **end_index**: The last page of this section
- **summary**: A brief description of what this section covers
- **nodes**: Any subsections (child nodes)

```json
{
  "title": "Financial Statements",
  "node_id": "0003",
  "start_index": 11,
  "end_index": 50,
  "summary": "Complete financial statements for fiscal year 2023",
  "nodes": [
    {
      "title": "Income Statement",
      "node_id": "0004",
      "start_index": 11,
      "end_index": 20,
      "summary": "Revenue, expenses, and net income details"
    }
  ]
}
```

## Why Trees Are Powerful

Trees allow PageIndex to:

1. **Start broad, then narrow down** — like using a map to zoom from country → city → street
2. **Skip irrelevant sections entirely** — no need to search through 300 pages
3. **Maintain context** — each node knows where it fits in the bigger picture

## Summary

The tree structure is the backbone of PageIndex. It organizes a document into a hierarchy of sections with page references, allowing AI to navigate efficiently — just like a human expert would use a detailed table of contents.
