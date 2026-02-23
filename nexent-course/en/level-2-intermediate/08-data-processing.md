---
title: "Data Processing Pipeline"
weight: 8
bookToc: true
---

# Data Processing Pipeline

## Overview

Nexent includes a powerful data processing engine that can handle 20+ file formats. It extracts text, tables, and images from your documents and prepares them for use in knowledge bases and agent conversations.

## Supported Formats

Nexent can process documents in formats including PDF, DOCX, XLSX, PPTX, TXT, Markdown, HTML, CSV, and various image formats (JPG, PNG, etc.) with OCR support.

## How Data Processing Works

### 1. Upload

You upload files to a knowledge base or directly in a conversation.

### 2. Extraction

Nexent extracts content from the file:

- **Text** is pulled from text-based documents.
- **Tables** are detected and their structure is preserved.
- **Images** are processed with OCR to extract any visible text.

### 3. Chunking

Long documents are split into smaller, meaningful chunks. This makes searching faster and more accurate.

### 4. Indexing

Chunks are stored in Elasticsearch with vector embeddings, enabling semantic search — finding content by meaning, not just keywords.

### 5. Summarization

An AI model generates a summary of the document, which helps agents understand what each knowledge base contains.

## Batch Processing

For large volumes of documents, Nexent supports batch processing:

- Upload multiple files at once.
- Processing happens in the background.
- You can monitor progress in the interface.

## Data Quality Tips

- **Clean files** produce better results. Remove watermarks and unnecessary formatting when possible.
- **Structured documents** (with headings and clear sections) are easier for the system to process.
- **High-resolution images** yield better OCR results.

## Practice Exercise

1. Upload a PDF with tables and images to a knowledge base.
2. Ask the agent a question that requires reading a table from the document.
3. Check if the answer includes the correct data from the table.
