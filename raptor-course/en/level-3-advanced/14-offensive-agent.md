---
title: "The Offensive Security Specialist Agent"
weight: 4
bookToc: true
---

## The Offensive Security Specialist Agent

### What Is It?

RAPTOR includes an **autonomous offensive security agent** powered by SecOpsAgentKit. This agent can independently plan and execute security testing operations.

### Capabilities

The agent can perform:

- **Web Application Testing** — SQLi, XSS, CSRF, authentication bypass
- **Network Penetration Testing** — Port scanning, service enumeration, vulnerability exploitation
- **Binary Exploitation** — Buffer overflows, format strings, ROP chains
- **Fuzzing** — Targeted fuzzing campaigns
- **Exploit Development** — Full PoC generation
- **Code Review** — Security-focused adversarial code review

### How to Use

```
"Use the offensive security specialist agent to test this application"
```

The agent will:
1. Plan its approach
2. Execute safe operations automatically
3. **Ask for confirmation** before dangerous operations
4. Report findings with full evidence

### Safety Model

The agent follows a strict safety hierarchy:

| Operation Type | Behavior |
|---------------|----------|
| **Safe** (scanning, enumeration) | Auto-executes |
| **Potentially dangerous** (exploitation) | Requires explicit confirmation |
| **Destructive** | Blocked by default |

### SecOpsAgentKit

The agent's skills come from SecOpsAgentKit, an open-source collection of offensive security skills stored in `.claude/skills/SecOpsAgentKit/`. These skills are modular and can be extended.

### Combining with Other Commands

The offensive agent works alongside RAPTOR's other capabilities:

1. Run `/scan` to find vulnerabilities
2. Use the offensive agent to attempt exploitation
3. Run `/patch` to generate fixes
4. Re-test with the agent to verify patches

### Key Takeaway

The offensive security agent brings autonomous penetration testing to RAPTOR. It's powerful but operates within safety guardrails, always keeping humans in control of dangerous operations.
