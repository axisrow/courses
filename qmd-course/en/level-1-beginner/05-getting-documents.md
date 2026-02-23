---
title: "Getting Documents"
weight: 5
bookToc: true
---

# Getting Documents

## Retrieving a Single Document

Once you've found something interesting in search results, you can read the full document:

```sh
qmd get "notes/meeting-2024-01-15.md"
```

## Using Document IDs

Every search result shows a short ID like `#a1b2c3`. You can use this to quickly grab a document:

```sh
qmd get "#a1b2c3"
```

This is handy when you don't want to type the full path.

## Starting at a Specific Line

If you want to read from a particular line:

```sh
qmd get "notes/meeting.md:50"
```

This shows the document starting at line 50.

## Limiting Output

To read only a certain number of lines:

```sh
qmd get notes/meeting.md -l 100
```

Combine with a start line:

```sh
qmd get notes/meeting.md:50 -l 100
```

This shows 100 lines starting at line 50.

## Getting Multiple Documents

Use `multi-get` to retrieve several files at once:

```sh
# By glob pattern
qmd multi-get "journals/2025-05*.md"

# By comma-separated list
qmd multi-get "doc1.md, doc2.md, #abc123"
```

## Full Content in Search Results

You can also see full document content directly in search results:

```sh
qmd search "API design" --full
```

## Adding Line Numbers

For easier reference:

```sh
qmd get notes/meeting.md --line-numbers
```

## Export All Matching Files

Find all relevant files above a certain quality threshold:

```sh
qmd search "API" --all --files --min-score 0.3
```

This outputs a list of matching file paths — useful for feeding into other tools.

## Practice Exercise

1. Run a search and note a document ID from the results
2. Use `qmd get "#<id>"` to retrieve that document
3. Try `qmd multi-get` with a pattern matching several of your files

## Summary

You've completed the beginner level! You can now:

- ✅ Install and set up QMD
- ✅ Create and manage collections
- ✅ Search using keywords, semantic, and hybrid modes
- ✅ Retrieve documents by path, ID, or pattern

**Next level**: Learn about output formats, context, embeddings, and more advanced search techniques.
