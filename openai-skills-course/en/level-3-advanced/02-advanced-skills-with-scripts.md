---
title: "Advanced Skills with Scripts"
weight: 2
bookToc: true
---

# Advanced Skills with Scripts

## Introduction

Simple skills contain only text instructions. For tasks requiring precision and repeatability, skills can include scripts — executable code in Python, Bash, or other languages.

## When to Add Scripts

Add scripts when:
- The same code has to be rewritten every time
- The task requires deterministic results
- Complex logic cannot be described in text alone

## Skill Structure with Scripts

```
my-advanced-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── scripts/
│   ├── process_data.py
│   └── generate_report.py
├── references/
│   └── api_docs.md
└── assets/
    └── template.html
```

## Example: CSV Analyzer Skill

### SKILL.md

```markdown
---
name: csv-analyzer
description: Analyze CSV files — statistics, filtering, visualization. Use when a user asks to analyze, summarize, or visualize data from a CSV.
---

# CSV Analyzer

Analyze and visualize data from CSV files.

## Usage

For basic statistics:
\`\`\`bash
python scripts/analyze.py data.csv
\`\`\`

For visualization:
\`\`\`bash
python scripts/analyze.py data.csv --chart bar --column revenue
\`\`\`
```

### scripts/analyze.py

```python
#!/usr/bin/env python3
import csv, sys, argparse

def analyze(filepath, column=None):
    with open(filepath) as f:
        rows = list(csv.DictReader(f))
    print(f"Rows: {len(rows)}")
    print(f"Columns: {len(rows[0]) if rows else 0}")
    if column and rows:
        values = [r[column] for r in rows if column in r]
        print(f"Unique values in '{column}': {len(set(values))}")

if __name__ == "__main__":
    parser = argparse.ArgumentParser()
    parser.add_argument("file")
    parser.add_argument("--column")
    args = parser.parse_args()
    analyze(args.file, args.column)
```

## Referencing Scripts in SKILL.md

Always describe scripts in SKILL.md: what they do, their parameters, when to run them, and examples.

## Summary

- Scripts give skills precision and repeatability
- Place scripts in the `scripts/` folder
- Describe scripts and their parameters in SKILL.md
- Use `references/` for large reference materials
- Test every script before publishing
