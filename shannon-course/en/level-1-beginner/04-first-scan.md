---
title: "Your First Scan"
weight: 4
bookToc: true
---

# Your First Scan

## Introduction

Let's run a full pentest on OWASP Juice Shop — a deliberately vulnerable practice application.

## Step 1: Launch Juice Shop

```bash
docker run -d -p 3000:3000 bkimminich/juice-shop
```

Open `http://localhost:3000` — you'll see an online juice store.

## Step 2: Prepare Source Code

```bash
git clone https://github.com/juice-shop/juice-shop.git ./repos/juice-shop
```

## Step 3: Run Shannon

```bash
./shannon start URL=http://host.docker.internal:3000 REPO=juice-shop
```

Shannon will return a workflow ID, e.g.: `shannon-1771007534808`.

## Step 4: Watch the Process

```bash
./shannon logs
# Or open the web UI
open http://localhost:8233
```

The process takes about 1–1.5 hours. Shannon goes through 4 phases:
1. **Reconnaissance** — maps the application, finds entry points
2. **Vulnerability Analysis** — finds potential issues in code
3. **Exploitation** — attempts to actually exploit each vulnerability
4. **Reporting** — compiles proven findings into a report

## Step 5: Get Results

After completion, the report appears in:

```
audit-logs/{hostname}_{sessionId}/deliverables/
```

## Using Workspaces

If the test is interrupted, resume from where it stopped:

```bash
./shannon start URL=http://host.docker.internal:3000 REPO=juice-shop WORKSPACE=my-test
# Resume later
./shannon start URL=http://host.docker.internal:3000 REPO=juice-shop WORKSPACE=my-test
```

## Summary

- You ran a full pentest on a practice application
- Saw Shannon's 4 phases in action
- Learned to use workspaces for resuming tests
- Results are saved in the `audit-logs/` directory
