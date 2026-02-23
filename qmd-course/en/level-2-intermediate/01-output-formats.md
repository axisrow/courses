---
title: "Output Formats"
weight: 6
bookToc: true
---

# Output Formats

## Why Different Formats?

QMD can output results in several formats. The default is a colorful terminal display, but you may need machine-readable output for scripts or AI agents.

## Available Formats

| Flag | Format | Best For |
|------|--------|----------|
| *(default)* | Colorized CLI | Reading in the terminal |
| `--json` | JSON | Scripts and AI agents |
| `--files` | File list | Pipelines and tool integrations |
| `--csv` | CSV | Spreadsheets |
| `--md` | Markdown | Documentation and reports |
| `--xml` | XML | Structured data exchange |

## JSON Output

```sh
qmd search "authentication" --json -n 10
```

Returns structured data with paths, scores, snippets, and metadata. Ideal for passing results to an LLM or script.

## File List Output

```sh
qmd query "error handling" --all --files --min-score 0.4
```

Outputs: `docid,score,filepath,context` — one line per result. Great for piping into other commands.

## Markdown Output

```sh
qmd search "API design" --md --full
```

Generates clean markdown with full document content. Useful for building reports or feeding context to AI.

## CSV Output

```sh
qmd search "project plan" --csv
```

Easy to open in Excel, Google Sheets, or any spreadsheet tool.

## Controlling the Number of Results

```sh
# Show 10 results (default is 5 for terminal, 20 for --files/--json)
qmd search "query" -n 10

# Show ALL results above a score threshold
qmd search "query" --all --min-score 0.3
```

## Combining Options

```sh
# JSON output, 10 results, from a specific collection
qmd query "deployment" --json -n 10 -c docs

# All matching files with full content in markdown
qmd search "API" --all --md --full --min-score 0.5
```

## Disabling Colors

If you're piping output or prefer plain text:

```sh
NO_COLOR=1 qmd search "query"
```

## Next Steps

Let's learn how to add context to your collections to improve search quality.
