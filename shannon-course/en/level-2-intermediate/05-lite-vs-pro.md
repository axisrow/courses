---
title: "Shannon Lite vs Pro"
weight: 5
bookToc: true
---

# Shannon Lite vs Pro

## Introduction

Shannon comes in two editions. Let's compare them to help you choose.

## Comparison Table

| Feature | Shannon Lite | Shannon Pro |
|---------|:-----------:|:-----------:|
| Source-sink analysis | Basic | LLM-powered data flow analysis |
| CVSS scoring | ❌ | ✅ |
| Remediation guidance | Basic | Code-level fixes |
| CI/CD pipelines | ❌ | ✅ |
| API access | ❌ | ✅ |
| Jira / Linear / Slack | ❌ | ✅ |
| Hosting | Self-hosted | Cloud or self-hosted |
| Multi-user & RBAC | ❌ | ✅ |
| SSO/SAML | ❌ | ✅ |
| Compliance (OWASP, PCI-DSS, SOC2) | ❌ | ✅ |
| Support | Community | Dedicated + SLA |
| Cost | Free + API costs | Contact sales |

## Key Technical Difference

**Shannon Lite** analyzes code within the LLM context window — good for individual files and simple data flows.

**Shannon Pro** uses **LLM-powered data flow analysis** (inspired by [LLMDFA](https://arxiv.org/abs/2402.10754)):
- Graph-based analysis of the entire codebase
- Tracks data flows across files and modules
- Detects complex multi-component vulnerabilities

## Who Should Use What

**Shannon Lite:** Individual developers, small teams, personal projects, learning and research.

**Shannon Pro:** Organizations with compliance requirements, large codebases, CI/CD needs, enterprise support needs.

## License

- **Lite** — AGPL-3.0 (free, open source)
- **Pro** — Commercial license

## Summary

- Lite is free, great for small teams and personal projects
- Pro is for organizations needing deep analysis and integrations
- The key difference is Pro's advanced graph-based data flow analysis
