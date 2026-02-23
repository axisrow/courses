---
title: "Understanding Results"
weight: 5
bookToc: true
---

# Understanding Results

## Introduction

Shannon finished the test — now let's learn how to read the report and what to do with it.

## Output Structure

```
audit-logs/{hostname}_{sessionId}/
├── session.json          # Metrics and session data
├── agents/               # Per-agent execution logs
├── prompts/              # Prompt snapshots
└── deliverables/
    └── comprehensive_security_assessment_report.md   # Main report
```

The most important file is `comprehensive_security_assessment_report.md`.

## How to Read the Report

The report contains only **proven vulnerabilities**. Each finding includes:

### 1. Vulnerability Description
What was found and what type it is (SQL Injection, XSS, SSRF, etc.)

### 2. Severity Level
- **Critical** — full data theft or complete system takeover possible
- **High** — serious issue, fix urgently
- **Medium** — issue exists but exploitation is harder
- **Low** — minor risk

### 3. Proof of Concept (PoC)
The most valuable part — ready-to-use code or command to reproduce the attack. You can copy and execute the PoC to verify it yourself.

### 4. Remediation Recommendations
What to change in your code to fix the vulnerability.

## Example Finding

```markdown
## SQL Injection in /api/products/search

**Severity:** Critical

**Description:** The `q` parameter in the search endpoint is unfiltered
and allows arbitrary SQL query execution.

**PoC:**
curl "http://target.com/api/products/search?q=test')) UNION SELECT
  id,email,password,role,... FROM Users--"

**Result:** Full user table with password hashes obtained.

**Recommendation:** Use parameterized queries instead of string concatenation.
```

## What to Do with Results

1. **Prioritize** — fix Critical and High first
2. **Reproduce** — use the PoC to verify the vulnerability
3. **Fix** — make code changes
4. **Re-test** — run Shannon again to confirm the fix

## Summary

- The main file is the report in the `deliverables/` folder
- Each finding includes description, severity, PoC, and recommendations
- All vulnerabilities in the report are proven (actually exploited)
- Fix Critical and High first, then re-run the test
