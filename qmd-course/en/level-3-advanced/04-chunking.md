---
title: "Smart Chunking Algorithm"
weight: 14
bookToc: true
---

# Smart Chunking Algorithm

## Why Chunking Matters

Documents can be very long, but AI models work best with focused pieces of text. QMD splits documents into chunks of ~900 tokens (~700 words) with 15% overlap.

The key is *where* to split. A bad split in the middle of a paragraph loses meaning. QMD uses a smart algorithm to find the best break points.

## Break Point Scores

QMD assigns scores to different markdown elements:

| Pattern | Score | Description |
|---------|-------|-------------|
| `# Heading` | 100 | H1 — major section |
| `## Heading` | 90 | H2 — subsection |
| `### Heading` | 80 | H3 |
| `#### Heading` | 70 | H4 |
| `##### Heading` | 60 | H5 |
| `###### Heading` | 50 | H6 |
| ` ``` ` | 80 | Code block boundary |
| `---` / `***` | 60 | Horizontal rule |
| Blank line | 20 | Paragraph boundary |
| `- item` / `1. item` | 5 | List item |
| Line break | 1 | Minimal break |

## The Algorithm

1. Scan the document for all break points and their scores
2. When approaching the 900-token target, search a 200-token window before the cutoff
3. Score each candidate: `finalScore = baseScore × (1 - (distance/window)² × 0.7)`
4. Cut at the highest-scoring break point

The distance decay formula means a heading 200 tokens back (scoring ~30) still beats a simple line break at the target (score 1), but a closer heading wins over a distant one.

## Code Block Protection

Break points inside code blocks are ignored. Code stays together. If a code block exceeds the chunk size, QMD keeps it whole when possible.

## Why 15% Overlap?

Overlapping ensures that information near chunk boundaries isn't lost. If a relevant passage straddles two chunks, the overlap means it appears fully in at least one of them.

## Embedding Format

Each chunk is embedded with its document title for context:

```
"title: Software Architecture | text: This section discusses..."
```

This helps the AI model understand what each chunk is about, even without seeing the full document.

## Next Steps

In the final lesson, let's put everything together with real-world workflows and tips.
