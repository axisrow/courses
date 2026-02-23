---
title: "Generating Security Patches"
weight: 5
bookToc: true
---

## Generating Security Patches

### From Vulnerability to Fix

Finding and proving a bug is only half the job. RAPTOR can also **generate patches** to fix the vulnerabilities it discovers.

### The `/patch` Command

```
/patch
```

This generates code fixes for discovered vulnerabilities.

### What a Patch Includes

- **Modified code** — The specific changes needed
- **Explanation** — Why this fix works
- **Side effects** — Any potential impact on functionality
- **Test suggestions** — How to verify the fix works

### The Full Autonomous Workflow

The `/agentic` command runs everything in sequence:

```
/agentic
```

1. Scan → Find vulnerabilities
2. Analyze → Assess severity with AI
3. Exploit → Prove exploitability
4. Patch → Generate fixes

This is RAPTOR's most powerful mode — fully autonomous security testing from discovery to remediation.

### Python CLI for Automation

For CI/CD pipelines, use the Python interface:

```bash
python3 raptor.py agentic --repo /path/to/code
```

This enables automated security testing in your development workflow.

### Best Practices

1. **Review patches manually** — AI-generated fixes should always be reviewed by a human
2. **Run tests after patching** — Make sure the fix doesn't break functionality
3. **Document the change** — Record why the patch was applied
4. **Re-scan after patching** — Verify the vulnerability is actually fixed

### Key Takeaway

RAPTOR closes the loop from discovery to remediation. The `/agentic` command gives you a complete autonomous workflow, but human review of patches remains essential.
