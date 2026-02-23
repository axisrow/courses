---
title: "Document Skills (DOCX, PDF, PPTX, XLSX)"
weight: 3
bookToc: true
---

# Document Skills

## Introduction

Anthropic created skills for working with major document formats. These power Claude's file creation capabilities.

## DOCX — Word Documents

Create, edit, add comments, track changes, accept/reject redlines.

```
docx/
├── SKILL.md
├── scripts/
│   ├── comment.py
│   ├── accept_changes.py
│   └── office/ (validate, pack, unpack, schemas)
└── LICENSE.txt
```

## PDF, PPTX, XLSX

Similar structure for PDF documents, PowerPoint presentations, and Excel spreadsheets.

## Key Characteristics

1. **Include scripts** for processing binary formats
2. **Include XML schemas** for validation
3. **Source-available** — viewable but not open source

## Summary

- Anthropic provides skills for DOCX, PDF, PPTX, XLSX
- Document skills use scripts for file processing
- Study them as examples of complex skills
