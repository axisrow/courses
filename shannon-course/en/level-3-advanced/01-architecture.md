---
title: "Shannon Architecture"
weight: 1
bookToc: true
---

# Shannon Architecture

## Introduction

Shannon isn't a single "bot" — it's a system of specialized AI agents working together through four distinct phases.

## Architecture Overview

```
                ┌──────────────────────┐
                │   Reconnaissance     │
                └──────────┬───────────┘
                           │
            ┌──────────────┼──────────────┐
            ▼              ▼              ▼
    ┌──────────────┐ ┌──────────────┐ ┌──────────┐
    │ Analysis     │ │ Analysis     │ │   ...    │
    │ (Injection)  │ │ (XSS)        │ │          │
    └──────┬───────┘ └──────┬───────┘ └────┬─────┘
           ▼                ▼              ▼
    ┌──────────────┐ ┌──────────────┐ ┌──────────┐
    │ Exploitation │ │ Exploitation │ │   ...    │
    │ (Injection)  │ │ (XSS)        │ │          │
    └──────┬───────┘ └──────┬───────┘ └────┬─────┘
           └────────┬───────┴──────────────┘
                    ▼
            ┌──────────────────────┐
            │      Reporting       │
            └──────────────────────┘
```

## Phase 1: Reconnaissance
Builds a comprehensive map: source code analysis, Nmap/Subfinder/WhatWeb scanning, browser exploration. Produces a detailed attack surface map.

## Phase 2: Vulnerability Analysis
Specialized agents hunt for vulnerabilities **in parallel** — one per OWASP category. They perform data flow analysis tracing user input to dangerous sinks. Produces a list of **hypothesized exploitable paths**.

## Phase 3: Exploitation
Dedicated agents attempt real-world attacks using browser automation, CLI tools, and custom scripts. **"No Exploit, No Report"** — failed hypotheses are discarded.

## Phase 4: Reporting
Compiles all validated findings into a professional report with reproducible PoCs.

## Technology Stack

- **Anthropic Claude Agent SDK** — AI reasoning core
- **Temporal** — workflow orchestration
- **Docker** — isolation and reproducibility
- **Browser automation** — real browser interaction
- **Nmap, Subfinder, WhatWeb, Schemathesis** — recon tools

## Summary

- Shannon is a multi-agent system with 4 phases
- Agents work in parallel for speed
- Strict "no exploit, no report" policy eliminates false positives
