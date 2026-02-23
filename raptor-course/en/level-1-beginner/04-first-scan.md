---
title: "Running Your First Scan"
weight: 4
bookToc: true
---

## Running Your First Scan

### What Is a Scan?

A scan examines your source code for known vulnerability patterns **without running the program**. This is called "static analysis."

### How to Run a Scan

1. Open RAPTOR in Claude Code
2. Type the command:

```
/scan
```

3. RAPTOR will ask you for a path to your code repository
4. It runs **Semgrep** and **CodeQL** against your code
5. Results appear in a structured report

### Understanding the Results

Each finding includes:

- **Severity** — How dangerous is this? (Critical, High, Medium, Low)
- **Location** — Which file and line number
- **Description** — What the vulnerability is
- **Category** — Type of issue (SQL injection, XSS, hardcoded secrets, etc.)

### Example: Scanning Test Files

RAPTOR includes test files you can practice with:

```
/scan --repo test/data/
```

This will find intentional vulnerabilities like SQL injection and XSS in the sample files.

### What Happens Behind the Scenes

RAPTOR uses **Semgrep rules** stored in `engine/semgrep/rules/` covering:

- SQL injection
- Command injection
- Path traversal
- Hardcoded secrets
- Weak cryptography
- SSRF (Server-Side Request Forgery)

### Key Takeaway

Your first scan is as simple as typing `/scan`. Start with the test files to see what RAPTOR can find, then point it at your own code.
