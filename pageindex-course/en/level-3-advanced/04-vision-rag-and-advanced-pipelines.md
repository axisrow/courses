---
title: "Vision RAG and Advanced Pipelines"
weight: 4
bookToc: true
---

# Vision RAG and Advanced Pipelines

## Beyond Text: Vision-Based RAG

Traditional document processing relies on extracting text from PDFs using OCR or text parsers. But many documents contain information that's hard to capture as text: charts, diagrams, complex tables, and specialized layouts.

PageIndex supports **Vision RAG** — a pipeline that works directly with page images instead of extracted text.

## How Vision RAG Works

1. **Convert PDF pages to images** — Each page becomes an image file
2. **Build the tree structure** — Using text extraction for structure (or vision models)
3. **During retrieval, send page images** — Instead of sending text, send the actual page image to the LLM
4. **LLM reads the image** — Modern vision-capable LLMs can understand charts, tables, and layouts directly

## Advantages of Vision RAG

| Feature | Text-based RAG | Vision RAG |
|---------|---------------|------------|
| Charts and graphs | Lost or poorly converted | Fully visible |
| Complex tables | Often broken | Preserved |
| Formatting and layout | Lost | Preserved |
| OCR errors | Common | None |
| Processing cost | Lower | Higher |

## Building an Advanced RAG Pipeline

A complete PageIndex-based RAG system combines several components:

### Component 1: Document Preprocessing

```python
# Generate the tree structure
from pageindex import page_index

tree = page_index("document.pdf", if_add_node_summary="yes")
```

### Component 2: Query Understanding

Before searching the tree, analyze the user's question:
- What type of information is being requested?
- Does it require numerical data, text, or visual content?
- Does it span multiple sections?

### Component 3: Tree Navigation

Use the LLM to navigate the tree based on the query:
- Start at the top level
- At each level, select the most relevant branch
- Continue until reaching a leaf node or a sufficiently specific section

### Component 4: Content Extraction

Extract the relevant pages from the original document:
- For text RAG: extract the text from the identified pages
- For vision RAG: extract the page images

### Component 5: Answer Generation

Send the extracted content (text or images) along with the original question to the LLM for answer generation.

## Agentic Retrieval

The most advanced use of PageIndex involves **agentic retrieval** — where the AI agent can:

- Make multiple passes through the tree
- Combine information from different sections
- Ask follow-up questions to narrow down results
- Verify its own answers against the document

This is covered in the `agentic_retrieval.ipynb` cookbook.

## Combining with Other Tools

PageIndex can be combined with:

- **MCP**: Allow AI assistants to use PageIndex as a tool
- **LangChain / LlamaIndex**: Integrate PageIndex as a retriever in existing frameworks
- **Custom pipelines**: Build specialized workflows for your domain

## Summary

Vision RAG extends PageIndex to handle visually rich documents by working with page images. Advanced pipelines combine tree navigation, vision capabilities, and agentic retrieval for the most complex document analysis tasks.
