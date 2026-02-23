---
title: "RAPTOR Architecture Deep Dive"
weight: 1
bookToc: true
---

## RAPTOR Architecture Deep Dive

### Multi-Layered Design

RAPTOR uses a **progressive disclosure** architecture — it loads only what's needed:

#### Layer 1: Bootstrap (CLAUDE.md)
Always loaded. Contains the core decision system and basic commands.

#### Layer 2: Tier 1 Skills
Auto-loaded when relevant:
- Adversarial thinking
- Analysis guidance
- Recovery procedures

#### Layer 3: Tier 2 Expert Personas
Loaded on explicit request. Nine specialized expert personas:

1. **Mark Dowd** — Deep code review expertise
2. **Charlie Miller / Halvar Flake** — Binary exploitation
3. **Security Researcher** — General vulnerability research
4. **Patch Engineer** — Secure code remediation
5. **Penetration Tester** — Offensive testing methodology
6. **Fuzzing Strategist** — Fuzzing optimization
7. **Binary Exploitation Specialist** — Low-level exploitation
8. **CodeQL Dataflow Analyst** — Query authoring
9. **CodeQL Finding Analyst** — Results interpretation

#### Layer 4: Agents
Autonomous agents like the **Offensive Security Specialist** that can chain multiple operations.

### Python Execution Layer

```
raptor.py          → Unified launcher (CLI entry point)
packages/          → 9 security capability packages
  ├── autonomous/         → Full workflow orchestration
  ├── binary_analysis/    → Binary reversing and analysis
  ├── codeql/             → CodeQL integration
  ├── exploit_feasibility/→ Exploitability assessment
  ├── exploitability_validation/ → Validation engine
  ├── fuzzing/            → AFL++ integration
  ├── llm_analysis/       → LLM-powered analysis
  ├── recon/              → Reconnaissance
  └── sca/                → Software Composition Analysis
core/              → Shared utilities
engine/            → Rules and queries (Semgrep, CodeQL)
```

### Token Budget

The progressive loading keeps context efficient:
- Bootstrap: ~360 tokens
- Tier 1: ~925 tokens total
- Full load with personas: up to ~2,500 tokens

### Key Takeaway

RAPTOR's architecture is modular and efficient. Understanding the layers helps you use the right tool depth for each task.
