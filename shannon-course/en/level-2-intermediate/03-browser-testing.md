---
title: "Browser-Based Testing"
weight: 3
bookToc: true
---

# Browser-Based Testing

## Introduction

Shannon doesn't just analyze code — it opens a real browser and interacts with your application like a human. This catches vulnerabilities only visible during actual use.

## How It Works

Shannon uses browser automation to:

1. **Log in** — fills forms, clicks buttons, handles 2FA
2. **Navigate** — browses pages, finds hidden endpoints
3. **Exploit** — executes XSS attacks, checks cookies, tests redirects
4. **Prove** — captures responses as evidence

## What Gets Tested via Browser

### XSS Attacks
A browser is needed to confirm injected JavaScript actually executes.

### Authentication
Shannon walks through the entire login process: forms, TOTP, OAuth flows.

### Client-Side Vulnerabilities
- DOM-based XSS
- Insecure browser storage
- URL redirects

## Combining with Code Analysis

| Approach | What it provides |
|----------|-----------------|
| **White-box** (code analysis) | Finds potential vulnerabilities in source code |
| **Black-box** (browser) | Confirms the vulnerability is actually exploitable |

This is called **code-aware dynamic testing** — code analysis guides attacks, the browser proves them.

## Built-in Tools

Besides the browser, Shannon uses:
- **Nmap** — port and service scanning
- **Subfinder** — subdomain discovery
- **WhatWeb** — technology fingerprinting
- **Schemathesis** — API schema testing

## Summary

- Shannon uses a real browser to exploit vulnerabilities
- The browser confirms XSS, handles authentication, checks client-side bugs
- Combining code analysis with browser testing maximizes accuracy
