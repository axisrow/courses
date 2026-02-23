---
title: "Advanced Multi-Agent Workflows"
weight: 11
bookToc: true
---

# Advanced Multi-Agent Workflows

## Beyond Single Agents

At the beginner level, you used one agent at a time. At the intermediate level, you learned NTM for parallel work. Now let's orchestrate **complex multi-agent workflows**.

### Pattern 1: Divide and Conquer

Split a project across agents by specialty:

| Agent | Role | Task |
|-------|------|------|
| Claude | Architect | Design the system, write documentation |
| Codex | Builder | Implement the core code |
| Gemini | Reviewer | Review code, find bugs, suggest improvements |

### Pattern 2: Red Team / Blue Team

Have agents challenge each other:

1. **Agent A** writes a solution
2. **Agent B** tries to break it (find bugs, edge cases)
3. **Agent A** fixes the issues
4. Repeat until robust

### Pattern 3: Ensemble Approach

Give the same task to all three agents, then pick the best solution:

```
Same prompt → Claude → Solution A
Same prompt → Codex  → Solution B
Same prompt → Gemini → Solution C
                ↓
        Compare and merge the best parts
```

### Using Agent Mail for Coordination

```bash
# Start the mail server
am

# Agents can now send messages to each other
# Agent 1: "I finished the database schema, it's in /tmp/schema.sql"
# Agent 2: "Got it, starting the API layer"
```

Agent Mail also supports **file reservations** — an agent can "lock" a file so others don't edit it simultaneously.

### Practical Example: Building a Web App

1. Use Beads to plan: frontend, backend, database, tests, deployment
2. Assign via NTM: Claude→backend, Codex→frontend, Gemini→tests
3. Agent Mail coordinates: backend signals "API ready" → frontend starts integrating
4. UBS scans all code before merging
5. CASS records the entire process for future reference

### Key Takeaway

Advanced workflows use multiple agents in coordinated patterns: divide-and-conquer, red/blue team, or ensemble. Agent Mail enables inter-agent communication and file locking for conflict-free parallel work.
