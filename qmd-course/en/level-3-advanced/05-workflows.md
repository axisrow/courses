---
title: "Real-World Workflows"
weight: 15
bookToc: true
---

# Real-World Workflows

## Workflow 1: Daily Knowledge Worker

Start your day by updating your index:

```sh
qmd update --pull
qmd embed
```

Search for what you need during the day:

```sh
# Quick keyword search
qmd search "budget Q4"

# Deeper semantic search
qmd query "what decisions were made about the product roadmap"
```

## Workflow 2: AI-Powered Research Assistant

Set up QMD as a knowledge base for your AI assistant:

```sh
# Index everything
qmd collection add ~/research --name research
qmd context add qmd://research "Academic papers and research notes"
qmd embed

# Start MCP HTTP server for persistent access
qmd mcp --http --daemon
```

Now your AI can answer questions grounded in your documents.

## Workflow 3: Meeting Transcript Mining

```sh
qmd collection add ~/meetings --name meetings
qmd context add qmd://meetings "Team meeting transcripts from 2024-2025"
qmd embed

# Find action items
qmd query "action items and deadlines"

# Find decisions about specific topics
qmd query $'lex: "decision" "agreed"\nvec: what was decided about the hiring plan'
```

## Workflow 4: Code Documentation Search

```sh
qmd collection add ~/project/docs --name project-docs
qmd context add qmd://project-docs "Internal API documentation and architecture docs"
qmd embed

# Search with structured queries
qmd query $'lex: authentication API endpoint\nvec: how does the auth system work\nhyde: The authentication system uses JWT tokens with a 24-hour expiry...'
```

## Performance Tips

1. **Use `search` for quick lookups** — it's instant and often sufficient
2. **Reserve `query` for complex questions** — the full pipeline takes more time
3. **Set `--min-score`** — filter out low-quality results to save time
4. **Use `--files` output** — when you just need file paths, not content
5. **Run HTTP MCP server** — keeps models loaded for faster repeated queries

## Organizing Your Collections

| Collection | Content | Context |
|-----------|---------|---------|
| `notes` | Personal notes | "Daily notes and ideas" |
| `meetings` | Transcripts | "Meeting transcripts with action items" |
| `docs` | Documentation | "Project documentation and guides" |
| `research` | Papers/articles | "Research materials and references" |

## Troubleshooting

| Problem | Solution |
|---------|----------|
| No results | Check `qmd status`, run `qmd update` |
| Poor semantic results | Run `qmd embed -f` to re-embed |
| Slow queries | Use `search` instead of `query` for simple lookups |
| Stale results | Run `qmd update` to re-index |

## Congratulations!

You've completed the QMD course! You now know how to:

- ✅ Install and configure QMD
- ✅ Manage collections and context
- ✅ Use all three search modes effectively
- ✅ Write advanced structured queries
- ✅ Integrate with AI agents via MCP
- ✅ Understand the hybrid search pipeline
- ✅ Optimize for your workflow

Happy searching! 🎉
