---
title: "CI/CD Integration"
weight: 4
bookToc: true
---

# CI/CD Integration

## Introduction

CI/CD (Continuous Integration / Continuous Deployment) automates building, testing, and deploying code. Shannon can be part of this process so every update gets a security check.

## Why It Matters

Without integration: you run Shannon manually when you remember. With integration: every pull request or release is automatically checked for vulnerabilities.

## Shannon Lite: Manual / Scripted

Shannon Lite doesn't have built-in CI/CD integration, but you can script it:

```bash
#!/bin/bash
./shannon start URL=$TARGET_URL REPO=$REPO_NAME WORKSPACE=ci-$BUILD_ID
```

## Shannon Pro: Native Integration

Shannon Pro provides native integration with:
- **GitHub Actions**
- **GitLab CI**
- **Jenkins**
- **API access** for programmatic use
- **Jira/Linear/ServiceNow/Slack** for ticket and notification automation

## Recommended Approach

1. **Start** — run Shannon manually after major changes
2. **Next** — add a script to CI/CD for staging
3. **Ideal** — use Shannon Pro with full automation

> ⚠️ **Never** run Shannon on production! Staging or dev environments only.

## Summary

- Shannon can integrate into CI/CD for automatic security checks
- Shannon Lite works for manual and scripted runs
- Shannon Pro offers native integration with major CI/CD platforms
- Security becomes part of the development process
