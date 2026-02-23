---
title: "Creating Custom Attacks"
weight: 2
bookToc: true
---

# Creating Custom Attacks

## Introduction

Shannon uses AI agents for attacks, so "custom attacks" means controlling agent behavior through configuration.

## Focus and Avoid Rules

```yaml
rules:
  focus:
    - description: "Test only API v2"
      type: path
      url_path: "/api/v2"
  avoid:
    - description: "Don't touch payment system"
      type: path
      url_path: "/payment"
```

## Custom Login Flows

For complex login scenarios, describe each step:

```yaml
authentication:
  login_flow:
    - "Navigate to the login page"
    - "Click 'Sign in with SSO'"
    - "Type $username into the corporate email field"
    - "Click 'Next'"
    - "Type $password into the password field"
    - "Type the TOTP code into the verification field"
    - "Click 'Verify'"
```

## Testing Multiple Roles

Create separate configs for different roles:

```bash
./shannon start URL=https://app.com REPO=app CONFIG=./configs/user-config.yaml
./shannon start URL=https://app.com REPO=app CONFIG=./configs/admin-config.yaml
```

Comparing results reveals privilege escalation issues.

## Multi-Repository Setup

```bash
mkdir ./repos/platform
cd ./repos/platform
git clone frontend-repo
git clone auth-service-repo
git clone api-gateway-repo
```

## Limitations

Shannon Lite doesn't allow adding new vulnerability categories or custom agents without modifying source code (AGPL allows this for internal use).

## Summary

- Custom attacks are managed via YAML configuration
- Focus and avoid rules control scanning priorities
- Complex login flows are described in natural language
- Testing different roles reveals authorization issues
