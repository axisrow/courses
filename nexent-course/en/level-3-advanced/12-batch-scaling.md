---
title: "Batch Scaling & Pipelines"
weight: 12
bookToc: true
---

# Batch Scaling & Pipelines

## When You Need Scale

Processing a few documents is easy. But what if you need to analyze 1,000 reports, process a year's worth of invoices, or build a knowledge base from an entire library? That's where Nexent's batch scaling comes in.

## From Single Process to Pipeline

Nexent scales smoothly from processing one file to handling large batches:

- **Single process** — upload one file, get results immediately.
- **Batch upload** — drop multiple files at once into a knowledge base.
- **Pipeline mode** — chain processing steps for complex workflows.

## Setting Up a Batch Pipeline

1. Create a knowledge base for the batch.
2. Upload all files at once (drag and drop multiple files).
3. Nexent queues and processes them in the background.
4. Monitor progress in the knowledge base dashboard.

## Processing Chain

For each document, Nexent runs:

1. **Format detection** — identifies the file type.
2. **Content extraction** — text, tables, images.
3. **OCR** (if needed) — converts image-based text.
4. **Chunking** — splits content into searchable pieces.
5. **Embedding** — creates vector representations.
6. **Summarization** — generates an overview.

## Performance Tips

- **Hardware matters.** More RAM and CPU cores speed up processing.
- **Batch similar files.** Processing 100 PDFs is faster than 50 PDFs + 30 spreadsheets + 20 images mixed together.
- **Monitor Elasticsearch.** Check `ES_JAVA_OPTS` in your `.env` file — allocate enough heap memory (default is 2 GB).

## Monitoring & Troubleshooting

- Check the knowledge base dashboard for processing status.
- Look at Docker logs for errors: `docker compose logs backend`.
- Failed files can be re-uploaded individually.

## Practice Exercise

1. Gather 10+ documents of various formats.
2. Upload them all to a single knowledge base.
3. Monitor the processing progress.
4. Once complete, ask the agent questions that span multiple documents.
