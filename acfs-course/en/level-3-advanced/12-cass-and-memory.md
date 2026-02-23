---
title: "CASS and CM: Building Agent Memory"
weight: 12
bookToc: true
---

# CASS and CM: Building Agent Memory

## The Memory Problem

AI agents are stateless by default — each conversation starts fresh. That's like having an employee who forgets everything every morning. ACFS solves this with CASS and CM.

### CASS — Conversational Agent Session Search

CASS records and indexes all your agent sessions.

```bash
# Open the CASS TUI (visual interface)
cass

# Search for a specific topic
cass search "database migration"
```

### What CASS Captures

- Every prompt you sent to an agent
- Every response the agent gave
- The files that were created or modified
- Timestamps and session metadata

### CM — CASS Memory (Procedural Memory)

CM takes raw session history and distills it into **reusable knowledge**.

```bash
# Get relevant memories for a topic
cm context "Building a REST API"

# Update procedural memory from recent sessions
cm reflect
```

### How Memory Improves Over Time

**Week 1**: You build a REST API. CM records patterns, mistakes, and solutions.

**Week 3**: You build another API. You run `cm context "REST API"` and your agents immediately know your preferred patterns, past mistakes to avoid, and proven solutions.

**Month 2**: Your agents have deep knowledge of your coding style, project structure preferences, and common pitfalls.

### Practical Tips

1. Run `cm reflect` after completing significant work
2. Use `cm context "topic"` at the start of related projects
3. Search CASS when you can't remember how you solved something before
4. Memory compounds — the more you use it, the more valuable it becomes

### Key Takeaway

CASS records all agent sessions. CM distills them into reusable knowledge. Together, they give your agents persistent memory that improves over time. Run `cm reflect` after major work and `cm context` before starting related projects.
