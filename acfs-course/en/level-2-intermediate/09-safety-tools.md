---
title: "Safety Tools: DCG, SLB, and UBS"
weight: 9
bookToc: true
---

# Safety Tools: DCG, SLB, and UBS

## Why Safety Matters

AI agents are powerful but can be dangerous. An agent told to "clean up the code" might delete important files. ACFS includes three safety tools to prevent disasters.

### DCG — Dangerous Command Guard

**What it does**: Blocks destructive commands before they execute.

```bash
# If an agent tries to run:
rm -rf /important-project

# DCG blocks it in sub-millisecond time
# ⛔ Blocked: destructive filesystem operation
```

DCG acts like a bouncer at a nightclub — it checks every command and stops the dangerous ones. It works specifically with Claude Code as a hook.

### SLB — Safety Lockbox

**What it does**: Requires confirmation for "nuclear" operations.

Think of it as the two-key system for launching missiles — certain dangerous actions need explicit human approval:

- Deleting repositories
- Force-pushing to main branch
- Dropping databases

Even if an agent tries to do these things, SLB stops and asks you first.

### UBS — Universal Bug Scanner

**What it does**: Scans code for bugs, security holes, and bad patterns.

```bash
# Scan your current project
ubs .
```

UBS runs comprehensive static analysis — it reads through code and flags potential problems without running the code.

### The Safety Stack Together

```
Agent wants to run a command
        ↓
   DCG: Is it destructive? → Block
        ↓ (if safe)
   SLB: Is it nuclear? → Ask human
        ↓ (if approved)
   Command runs
        ↓
   UBS: Scan the result for bugs
```

### Key Takeaway

ACFS protects you with three layers: DCG blocks dangerous commands instantly, SLB requires human approval for critical operations, and UBS scans code for bugs. You can let agents work freely knowing these guardrails exist.
