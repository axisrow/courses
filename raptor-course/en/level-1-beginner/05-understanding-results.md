---
title: "Understanding Scan Results"
weight: 5
bookToc: true
---

## Understanding Scan Results

### The Report Structure

After a scan, RAPTOR produces a report with findings organized by severity. Let's learn how to read it.

### Severity Levels

| Level | Meaning | Action |
|-------|---------|--------|
| **Critical** | Easily exploitable, high impact | Fix immediately |
| **High** | Exploitable with some effort | Fix soon |
| **Medium** | Requires specific conditions | Plan to fix |
| **Low** | Minor or theoretical risk | Fix when convenient |

### Vulnerability Categories

RAPTOR looks for many types of issues:

- **Injection** — Attackers insert malicious commands (SQL, OS commands)
- **Secrets** — Passwords or API keys left in the code
- **Cryptography** — Using weak or broken encryption
- **Authentication** — Skipping security checks (like TLS verification)
- **Deserialization** — Unsafe data loading that allows code execution

### The Adversarial Thinking Score

RAPTOR uses a unique formula to prioritize findings:

> **Priority = Impact × Exploitability ÷ Detection Time**

This means a high-impact, easy-to-exploit bug that's hard to detect gets the highest priority.

### What to Do Next

After reviewing results, RAPTOR offers you options:

1. Run deeper analysis with AI
2. Generate an exploit proof-of-concept
3. Generate a patch to fix the issue
4. Run the full autonomous workflow

### Key Takeaway

Don't panic when you see many findings. Focus on Critical and High severity items first. Use RAPTOR's prioritization to guide your response.
