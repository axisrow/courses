---
title: "XBOW Benchmark"
weight: 3
bookToc: true
---

# XBOW Benchmark

## Introduction

XBOW is an open benchmark of 104 vulnerable applications for evaluating AI pentesting agents. Shannon Lite achieved **96.15% success** (100/104 exploits).

## Results by Vulnerability Type

| Type | Total | Succeeded | Rate |
|------|-------|-----------|------|
| Broken Authorization | 25 | 25 | 100% |
| SQL Injection | 7 | 7 | 100% |
| Blind SQL Injection | 3 | 3 | 100% |
| SSRF / Misconfiguration | 22 | 21 | 95.45% |
| XSS | 23 | 22 | 95.65% |
| SSTI | 13 | 12 | 92.31% |
| Command Injection | 11 | 10 | 90.91% |

## The 4 Failures

- **XBEN-10 (XSS):** Misjudged JSFuck payload viability
- **XBEN-22 (SSTI):** Misclassified SSTI as false positive
- **XBEN-34 (RFI):** Confused RFI with LFI
- **XBEN-82 (Command Injection via SSRF):** Misclassified eval() risk

## Cost Comparison

| Metric | Traditional Pentest | Shannon |
|--------|-------------------|---------|
| Cost | $10,000+ | ~$16 |
| Time | Weeks | <1.5 hours |
| Frequency | 1–2x/year | Every deploy |

## Reproducibility

- Cleaned benchmark: [KeygraphHQ/xbow-validation-benchmarks](https://github.com/KeygraphHQ/xbow-validation-benchmarks)
- Full results: [xben-benchmark-results](https://github.com/KeygraphHQ/shannon/tree/main/xben-benchmark-results)

## Summary

- 96.15% success on a strict, hint-free benchmark
- Best results in Broken Authorization and SQL Injection (100%)
- 4 failures are classification issues, not fundamental limitations
- Results are fully reproducible
