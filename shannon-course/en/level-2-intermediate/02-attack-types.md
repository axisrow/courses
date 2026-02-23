---
title: "Attack Types"
weight: 2
bookToc: true
---

# Attack Types

## Introduction

Shannon tests several vulnerability categories. Let's explain each one in simple terms.

## SQL Injection

**What it is:** An attacker inserts SQL code into input fields (search, login), and the server executes it as part of a database query.

**Example:** Typing `' OR 1=1 --` in a search field returns all records from the table.

**Why it's dangerous:** Data theft, database deletion, password exposure.

## Cross-Site Scripting (XSS)

**What it is:** An attacker injects JavaScript code into a page that executes in other users' browsers.

**Types:**
- **Reflected** — malicious code in URL, triggers when clicking a link
- **Stored** — code is saved on the server (e.g., in a comment) and runs for all visitors
- **DOM-based** — code manipulates the page's DOM tree

**Why it's dangerous:** Cookie theft, phishing redirects, actions on behalf of the victim.

## Server-Side Request Forgery (SSRF)

**What it is:** An attacker makes the server send a request to an internal resource it shouldn't access.

**Example:** An "upload image by URL" feature is used to access `http://localhost:8080/admin`.

**Why it's dangerous:** Internal service access, token theft, internal network recon.

## Broken Authentication & Authorization

**What it is:** Flaws in authentication (who you are) and authorization (what you can do).

**Examples:** Login bypass, privilege escalation (regular user → admin), IDOR (accessing others' data by changing IDs), JWT attacks.

## Command Injection

**What it is:** An attacker injects OS commands through input fields.

**Example:** A "ping host" field accepts `google.com; cat /etc/passwd`.

**Why it's dangerous:** Full server control.

## What Shannon Doesn't Cover (Yet)

- Vulnerable third-party libraries
- Weak encryption
- Insecure configurations (if not exploitable)
- Business logic flaws

These are available in Shannon Pro.

## Summary

- Shannon covers 5 main attack categories: SQLi, XSS, SSRF, Broken Auth, Command Injection
- Every vulnerability is proven with a real exploit
- Shannon Pro extends coverage further
