---
title: "Deep Dive: Static Analysis"
weight: 1
bookToc: true
---

## Deep Dive: Static Analysis

### Two Engines, One Goal

RAPTOR uses two complementary static analysis engines:

#### Semgrep

Semgrep is a pattern-matching tool. It looks for code that matches known vulnerability patterns. RAPTOR ships with custom rules in `engine/semgrep/rules/`:

- `sinks/ssrf.yaml` — Server-Side Request Forgery
- `injection/sql-concat.yaml` — SQL Injection via string concatenation
- `injection/command-taint.yaml` — Command injection
- `crypto/weak-hash.yaml` — Weak hash algorithms (MD5, SHA1)
- `secrets/hardcoded-api-key.yaml` — Hardcoded API keys
- `auth/tls-skip-verify.yaml` — Disabled TLS verification

#### CodeQL

CodeQL is GitHub's semantic analysis engine. Unlike Semgrep's pattern matching, CodeQL understands **data flow** — it can trace how untrusted user input travels through your program to a dangerous function.

### When to Use Which

| Feature | Semgrep | CodeQL |
|---------|---------|--------|
| Speed | Very fast | Slower (builds a database) |
| Accuracy | Pattern-based (more false positives) | Data-flow-aware (fewer false positives) |
| Setup | Minimal | Requires database creation |

### Running CodeQL Separately

```
/codeql
```

This runs CodeQL-only analysis with full dataflow tracing.

### Dataflow Validation

RAPTOR attempts to validate findings by tracing data flow from **source** (user input) to **sink** (dangerous function). Validated findings are much more likely to be real vulnerabilities.

### Key Takeaway

Use Semgrep for quick, broad scans. Use CodeQL when you need deeper analysis with fewer false positives. RAPTOR combines both for the best results.
