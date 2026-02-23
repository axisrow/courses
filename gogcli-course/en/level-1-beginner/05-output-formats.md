---
title: "Output Formats"
weight: 5
bookToc: true
---

# Output Formats

gogcli can display results in three formats. Each is useful in different situations.

## 1. Default: Human-Readable Table

This is what you see by default — a nicely formatted table with colors:

```bash
gog gmail search 'newer_than:7d' --max 3
```

```
THREAD_ID           SUBJECT                FROM                  DATE
18f1a2b3c4d5e6f7    Meeting notes          alice@example.com     2025-01-10
17e1d2c3b4a5f6e7    Invoice #12345         billing@vendor.com    2025-01-09
```

Best for: **reading in your terminal**.

## 2. Plain Text (TSV)

Add `--plain` for tab-separated output without colors:

```bash
gog gmail search 'newer_than:7d' --max 3 --plain
```

Best for: **piping to other tools** like `grep`, `awk`, or `cut`.

Example — find emails from a specific sender:

```bash
gog gmail search 'newer_than:30d' --plain | grep "alice@"
```

## 3. JSON

Add `--json` for machine-readable JSON output:

```bash
gog gmail search 'newer_than:7d' --max 3 --json
```

```json
{
  "threads": [
    {
      "id": "18f1a2b3c4d5e6f7",
      "snippet": "Meeting notes from today..."
    }
  ]
}
```

Best for: **scripting and automation**.

### Using JSON with jq

`jq` is a powerful tool for processing JSON. Examples:

```bash
# Get just thread IDs
gog gmail search 'newer_than:7d' --json | jq -r '.threads[].id'

# Find PDF files in Drive
gog drive ls --json | jq '.files[] | select(.mimeType=="application/pdf")'
```

## Setting a Default Format

Use environment variables to set a default:

```bash
# Always output JSON
export GOG_JSON=1

# Always output plain text
export GOG_PLAIN=1
```

## Color Control

Colors are on by default in terminals and off for piped output. Override with:

```bash
# Force colors off
gog --color never gmail search 'newer_than:7d'

# Force colors on (even when piping)
gog --color always gmail search 'newer_than:7d'
```

## Important Note About stderr

gogcli sends **data** to stdout and **progress/hints** to stderr. This means piping works cleanly:

```bash
# Only the JSON data goes into the file, not progress messages
gog gmail search 'newer_than:7d' --json > emails.json
```

## Summary

| Flag | Format | Use case |
|------|--------|----------|
| *(none)* | Colored table | Reading in terminal |
| `--plain` | Tab-separated | Piping to grep/awk |
| `--json` | JSON | Scripting, automation |

## Next Steps

You've completed the Beginner level! Move on to **Level 2: Intermediate** to learn how to use each Google service in depth.
