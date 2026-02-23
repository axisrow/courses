---
title: "Working with the API and Integrations"
weight: 4
bookToc: true
---

# Working with the API and Integrations

## Ways to Use PageIndex

Beyond running PageIndex locally, there are several ways to integrate it into your workflow:

1. **Python API** — Call PageIndex functions directly from your code
2. **Cloud API** — Use the hosted service via HTTP requests
3. **MCP** — Connect PageIndex to AI assistants like Claude or Cursor
4. **Chat Platform** — Use the web interface for interactive document analysis

## Using the Python API

The simplest way to use PageIndex programmatically is through its Python function:

```python
from pageindex import page_index

result = page_index(
    "path/to/document.pdf",
    model="gpt-4o-2024-11-20",
    if_add_node_summary="yes",
    if_add_node_id="yes"
)
```

The `result` dictionary contains:
- `doc_name` — The name of your document
- `structure` — The full tree structure with sections, page ranges, and summaries
- `doc_description` — (optional) A description of the entire document

## Configuration Options

You can customize the behavior by passing parameters:

```python
result = page_index(
    "document.pdf",
    model="gpt-4o-2024-11-20",
    toc_check_page_num=20,        # Pages to scan for TOC
    max_page_num_each_node=10,     # Max pages per tree node
    max_token_num_each_node=20000, # Max tokens per tree node
    if_add_node_summary="yes",     # Generate section summaries
    if_add_doc_description="yes",  # Generate document description
    if_add_node_text="no"          # Include raw text in nodes
)
```

## Building a Simple RAG Pipeline

The cookbook includes a complete example of building a vectorless RAG system:

1. **Generate the tree** — Process your document with PageIndex
2. **Accept a question** — Get a user query
3. **Search the tree** — Use the LLM to reason through the tree structure
4. **Extract relevant pages** — Get the actual content from the identified section
5. **Generate an answer** — Use the LLM to answer based on the extracted content

This entire pipeline works without any vector database or chunking.

## Vision-Based RAG

PageIndex also supports a vision-based approach where instead of extracting text from PDFs, it works directly with **page images**. This is useful for documents with complex layouts, charts, or tables that are hard to extract as text.

## MCP Integration

MCP (Model Context Protocol) allows AI assistants to use PageIndex as a tool. Once configured, you can ask Claude or Cursor to analyze documents using PageIndex's capabilities, directly within your workflow.

## Summary

PageIndex offers multiple integration paths: direct Python API calls, cloud service, MCP for AI assistants, and an interactive chat platform. Each provides access to the same powerful tree-based reasoning retrieval.
