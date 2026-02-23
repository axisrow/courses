---
title: "OSS Forensics Investigation"
weight: 3
bookToc: true
---

## OSS Forensics Investigation

### What Is OSS Forensics?

RAPTOR's OSS Forensics module investigates **public GitHub repositories** for evidence of supply chain attacks, backdoors, or suspicious activity.

### The `/oss-forensics` Command

```
/oss-forensics
```

This launches a comprehensive forensic investigation.

### Evidence Collection Sources

RAPTOR collects evidence from multiple sources:

1. **GH Archive** — Immutable historical data of all public GitHub events, queryable via BigQuery
2. **GitHub API** — Current repository state, commits, issues, pull requests
3. **Wayback Machine** — Historical snapshots of web pages and content
4. **Local Git** — Direct repository analysis (commit history, blame, diffs)

### Investigation Process

The forensics module uses a **multi-agent architecture**:

1. **Evidence Collection Phase** — Specialized investigators work in parallel to gather data from all sources
2. **IOC Extraction** — Automated extraction of Indicators of Compromise from vendor reports
3. **Evidence Verification** — Rigorous validation against original immutable sources
4. **Hypothesis Formation** — AI-powered hypothesis generation with iterative refinement
5. **Forensic Reporting** — Detailed timeline, attribution analysis, and IOCs

### Deleted Content Recovery

One of the most powerful features: RAPTOR can recover **deleted content** including:
- Deleted commits (still accessible via SHA if known)
- Deleted issues and comments (via GH Archive)
- Modified repository descriptions and READMEs (via Wayback Machine)

### BigQuery Setup

For GH Archive queries, you need Google Cloud credentials:

```bash
export GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account.json
```

### Real-World Use Case

The XZ Utils backdoor (CVE-2024-3094) is a perfect example where OSS forensics tools like RAPTOR's could help investigate:
- When suspicious commits were introduced
- What accounts were involved
- How the attack progressed over time

### Key Takeaway

OSS Forensics is RAPTOR's investigative arm. It turns GitHub repositories into crime scenes and provides evidence-backed analysis of potential supply chain attacks.
