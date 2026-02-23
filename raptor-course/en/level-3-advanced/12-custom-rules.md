---
title: "Writing Custom Semgrep and CodeQL Rules"
weight: 2
bookToc: true
---

## Writing Custom Semgrep and CodeQL Rules

### Why Custom Rules?

RAPTOR's built-in rules cover common vulnerabilities, but your application may have unique patterns that need custom detection.

### Custom Semgrep Rules

Semgrep rules are written in YAML. Here's the structure:

```yaml
rules:
  - id: my-custom-rule
    pattern: |
      dangerous_function($INPUT)
    message: "Untrusted input passed to dangerous_function"
    severity: ERROR
    languages: [python]
    metadata:
      category: security
      cwe: CWE-78
```

#### Adding Rules to RAPTOR

Place your custom rules in:
```
engine/semgrep/rules/your-category/your-rule.yaml
```

RAPTOR's Semgrep configuration (`engine/semgrep/semgrep.yaml`) controls which rules are active.

### Custom CodeQL Queries

CodeQL queries use a SQL-like language called QL:

```ql
import python
import semmle.python.dataflow.new.DataFlow

from DataFlow::Node source, DataFlow::Node sink
where
  source.asExpr() instanceof UserInput and
  sink.asExpr() = dangerousCall.getAnArgument()
select sink, "Untrusted data flows to dangerous function"
```

CodeQL suites are stored in `engine/codeql/suites/`.

### SARIF Merge Tool

RAPTOR includes a SARIF merge tool (`engine/semgrep/tools/sarif_merge.py`) to combine results from multiple scanners into a single report.

### Testing Custom Rules

1. Write a test file with the vulnerable pattern
2. Place it in `test/data/`
3. Run your rule against it
4. Verify it detects the issue without false positives

### Key Takeaway

Custom rules let you tailor RAPTOR to your specific codebase and security concerns. Start with Semgrep rules (easier to write) and progress to CodeQL for data-flow analysis.
