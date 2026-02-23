---
title: "Meta-prompting"
level: 2
lesson: 3
language: en
tags: [gsd, meta-prompting, prompts]
---

# Meta-prompting

## Introduction

Meta-prompting is when AI creates prompts for other AI. In GSD, a thin orchestrator creates assignments for specialized agents.

## Instructions

### Meta-prompting Architecture in GSD

```
You → Orchestrator → Researchers (4 parallel)
                   → Planner → Checker → (loop until pass)
                   → Executors (parallel waves)
                   → Verifier
```

### How the Orchestrator Works

1. **Never does heavy work itself** — only coordinates
2. **Creates prompts for sub-agents** based on current state
3. **Collects results** and routes forward
4. **Preserves main window context** — your session stays at 30-40%

### XML Prompt Formatting

GSD uses XML to structure tasks because Claude understands structured prompts better:

```xml
<task type="auto">
  <name>Specific name</name>
  <files>Which files to touch</files>
  <action>Exact instructions</action>
  <verify>How to verify</verify>
  <done>Completion criteria</done>
</task>
```

## Examples

When you run `/gsd:plan-phase 1`, the orchestrator:
1. Reads PROJECT.md, REQUIREMENTS.md, CONTEXT.md
2. Creates prompt for researchers: "investigate stack, find patterns"
3. Collects research → creates prompt for planner
4. Planner creates XML plans
5. Checker verifies plans → if they fail, loop repeats

## Summary

- Meta-prompting = AI creates prompts for AI
- Orchestrator coordinates, doesn't do the work itself
- XML structure gives precise instructions to sub-agents
- Your main context stays clean
