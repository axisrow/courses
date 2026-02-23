---
title: "Adding Context"
weight: 7
bookToc: true
---

# Adding Context to Collections

## Why Context Matters

Context is one of QMD's most powerful features. When you add a description to a collection or folder, that description is returned alongside search results. This helps AI tools understand *what kind* of content they're looking at.

Without context, an AI sees: `notes/meeting.md — Score: 85%`

With context, it sees: `notes/meeting.md — Context: "Weekly team standup notes" — Score: 85%`

This small addition makes a big difference in how well AI understands your results.

## Adding Context to a Collection

Use the `qmd://` virtual path format:

```sh
qmd context add qmd://notes "Personal notes and ideas"
qmd context add qmd://meetings "Meeting transcripts and notes"
qmd context add qmd://docs "Work documentation"
```

## Adding Context to Subfolders

Context works as a tree. You can be more specific for subfolders:

```sh
qmd context add qmd://docs/api "API documentation"
qmd context add qmd://notes/work "Work-related notes"
```

Documents inside `docs/api/` will inherit the "API documentation" context.

## Adding Context from Inside a Folder

If you're already in the directory:

```sh
cd ~/notes
qmd context add "Personal notes and ideas"

cd ~/notes/work
qmd context add "Work-related notes"
```

## Global Context

Apply context to everything:

```sh
qmd context add / "Knowledge base for my projects"
```

## Viewing All Contexts

```sh
qmd context list
```

## Removing Context

```sh
qmd context rm qmd://notes/old
```

## Best Practices

1. **Be descriptive** — "Weekly engineering standup notes from 2024" is better than "meetings"
2. **Use hierarchy** — set general context on collections, specific context on subfolders
3. **Think about the AI** — what would an AI need to know to understand these documents?
4. **Keep it concise** — one clear sentence is usually enough

## How Context Appears in Results

When you search, context shows up in the output:

```
notes/meeting.md:15 #d4e5f6
Title: Q4 Planning
Context: Personal notes and ideas
Score: 67%
```

## Next Steps

Let's learn about embeddings and how QMD understands the meaning of your documents.
