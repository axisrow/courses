---
title: "Index Maintenance"
weight: 10
bookToc: true
---

# Index Maintenance

## Keeping Your Index Fresh

As you add, edit, and delete files, your QMD index needs to be updated to reflect the changes.

## Updating the Index

```sh
# Re-index all collections
qmd update

# Re-index and pull git repos first
qmd update --pull
```

Run `qmd update` whenever you've made significant changes to your documents.

## Checking Index Status

```sh
qmd status
```

This shows:
- Number of indexed documents
- Collection information
- Context descriptions
- Embedding status
- MCP server status (if running)

## Cleaning Up

Remove orphaned data and clear caches:

```sh
qmd cleanup
```

This is safe to run anytime. It removes data for documents that no longer exist.

## Using Named Indexes

You can maintain separate indexes for different purposes:

```sh
# Create and use a "work" index
qmd --index work collection add ~/work/docs --name work-docs
qmd --index work embed
qmd --index work search "quarterly report"
```

This is useful when you want completely separate search spaces.

## Data Storage

All QMD data is stored in:
- **Index database**: `~/.cache/qmd/index.sqlite`
- **AI models**: `~/.cache/qmd/models/`

To completely reset QMD, you can delete the `~/.cache/qmd/` directory.

## Workflow Tips

1. **Add `qmd update` to your routine** — run it at the start of each work day
2. **Use `--pull` if your docs are in git repos** — keeps everything in sync
3. **Run `qmd embed` after major changes** — so semantic search stays accurate
4. **Check `qmd status` periodically** — to make sure everything is healthy

## Summary

You've completed the intermediate level! You can now:

- ✅ Use different output formats
- ✅ Add context to improve search quality
- ✅ Generate and manage embeddings
- ✅ Connect QMD to AI agents via MCP
- ✅ Maintain and troubleshoot your index

**Next level**: Advanced query syntax, hybrid search internals, HTTP transport, and performance tuning.
