---
title: "Extending and Contributing to RAPTOR"
weight: 5
bookToc: true
---

## Extending and Contributing to RAPTOR

### RAPTOR Is Built to Be Extended

RAPTOR's modular architecture makes it straightforward to add new capabilities.

### Adding a New Package

1. Create a new directory in `packages/`:

```
packages/your_capability/
  ├── __init__.py
  ├── analyzer.py
  └── config.py
```

2. Register it in `raptor.py` (the unified launcher)

3. Create a Claude command in `.claude/commands/your-command.md`

See `docs/EXTENDING_LAUNCHER.md` for the complete developer guide.

### Creating Custom Skills

The `/create-skill` command lets you save custom approaches:

```
/create-skill
```

Skills are stored in `.claude/skills/` and automatically available in future sessions.

### Expert Personas

You can create new expert personas by adding markdown files to the Tier 2 system. A persona defines:

- **Identity** — Who the expert is
- **Approach** — How they analyze problems
- **Focus areas** — What they specialize in
- **Communication style** — How they present findings

### Contributing to the Community

RAPTOR is open source (MIT License) and welcomes contributions:

- **New Semgrep rules** for additional vulnerability patterns
- **CodeQL queries** for language-specific analysis
- **Fuzzing harnesses** for popular libraries
- **LLM provider integrations** for new AI models
- **Documentation** improvements and translations

### Community

Join the discussion:
- **GitHub Issues**: https://github.com/gadievron/raptor/issues
- **Slack**: #raptor channel at Prompt||GTFO

### Ideas for Contributors

- YARA signature generation
- Port to other AI coding assistants (Cursor, Windsurf, Copilot, Codex)
- Better web exploitation module
- Integration with bug bounty platforms

### Key Takeaway

RAPTOR's power comes from its community. Whether you write rules, improve tools, or share knowledge, your contribution makes security research better for everyone.
