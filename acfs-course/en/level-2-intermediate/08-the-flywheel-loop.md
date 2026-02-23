---
title: "The Flywheel Loop: How Everything Connects"
weight: 8
bookToc: true
---

# The Flywheel Loop: How Everything Connects

## The Core Concept

The "flywheel" in ACFS isn't just a name — it's a workflow pattern where each cycle of work makes the next one better.

### The Loop

```
Plan (Beads) → Coordinate (Agent Mail) → Execute (NTM + Agents)
    ↑                                              |
    |                                              ↓
    └──── Remember (CASS Memory) ← Scan (UBS) ←──┘
```

### Step by Step

#### 1. Plan with Beads
Break your project into tasks using Beads Viewer (`bv`). Each task is a "bead" that can depend on other beads.

#### 2. Coordinate with Agent Mail
Use MCP Agent Mail so your agents can communicate. Agent A can tell Agent B: "I finished the database — you can start the API now."

#### 3. Execute with NTM + Agents
Use NTM to assign tasks to agents. They work in parallel, each in their own tmux session.

#### 4. Scan with UBS
After agents write code, UBS scans it for bugs and security issues before you commit.

#### 5. Remember with CASS Memory
CASS records everything your agents did. Next time you work on a similar problem, your agents can look up what worked before.

### Why It's a Flywheel

- **Cycle 1**: Agents write code from scratch. Slow.
- **Cycle 2**: Agents remember what they learned. Faster.
- **Cycle 5**: Agents have deep context. Much faster.
- **Cycle 20**: Agents practically anticipate your needs.

Each cycle builds on the last. The more you use the system, the more powerful it becomes.

### Key Takeaway

The flywheel loop is: Plan → Coordinate → Execute → Scan → Remember → Repeat. Each cycle improves the next, making you faster over time.
