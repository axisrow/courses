---
title: "Installation and Setup"
weight: 3
bookToc: true
---

# Installation and Setup

## What You Need

Before installing PageIndex, make sure you have:

- **Python 3.8 or newer** installed on your computer
- **An OpenAI API key** (PageIndex uses GPT-4o by default)
- **A PDF document** to test with

## Step 1: Get the Code

Download the PageIndex repository from GitHub:

```bash
git clone https://github.com/VectifyAI/PageIndex.git
cd PageIndex
```

## Step 2: Install Dependencies

Install the required Python packages:

```bash
pip3 install --upgrade -r requirements.txt
```

This installs libraries for PDF processing, API communication, and text analysis.

## Step 3: Set Up Your API Key

Create a file called `.env` in the PageIndex folder and add your OpenAI key:

```bash
CHATGPT_API_KEY=your_openai_key_here
```

Replace `your_openai_key_here` with your actual API key from [platform.openai.com](https://platform.openai.com).

## Step 4: Run Your First Document

Process a PDF document:

```bash
python3 run_pageindex.py --pdf_path /path/to/your/document.pdf
```

The system will:
1. Read your PDF
2. Detect if there's a table of contents
3. Build the tree structure
4. Save the result as a JSON file in the `./results/` folder

## Understanding the Output

The output is a JSON file containing the full tree structure. You'll see sections with titles, page ranges, summaries, and nested subsections.

## Common Configuration Options

You can customize how PageIndex processes your document:

| Option | Default | Description |
|--------|---------|-------------|
| `--model` | gpt-4o-2024-11-20 | The AI model to use |
| `--toc-check-pages` | 20 | How many pages to scan for a TOC |
| `--max-pages-per-node` | 10 | Maximum pages before splitting a node |
| `--max-tokens-per-node` | 20000 | Maximum tokens before splitting a node |
| `--if-add-node-summary` | yes | Whether to generate summaries for each section |
| `--if-add-node-id` | yes | Whether to add unique IDs to each node |

## Markdown Support

PageIndex can also process Markdown files:

```bash
python3 run_pageindex.py --md_path /path/to/your/document.md
```

Note: The Markdown file must use proper heading hierarchy (`#`, `##`, `###`, etc.) for best results.

## Using the Cloud Service

If you don't want to install anything, you can use PageIndex through:

- **Chat Platform**: [chat.pageindex.ai](https://chat.pageindex.ai) — upload and chat with documents
- **API**: Integrate into your applications programmatically
- **MCP**: Use with Claude, Cursor, or other MCP-compatible tools

## Summary

Setting up PageIndex requires Python, an OpenAI API key, and a few commands. You can process PDF or Markdown documents locally, or use the cloud service for a simpler experience.
