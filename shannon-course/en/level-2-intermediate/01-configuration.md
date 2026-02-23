---
title: "Configuration"
weight: 1
bookToc: true
---

# Configuration

## Introduction

Shannon works without a config file, but for real applications you'll want one — especially to let Shannon log in and test protected pages.

## Creating a Config File

```bash
cp configs/example-config.yaml configs/my-app-config.yaml
```

Config files go in `./configs/` — this directory is automatically mounted into the Docker container.

## Configuration Structure

### Authentication

```yaml
authentication:
  login_type: form
  login_url: "https://your-app.com/login"
  credentials:
    username: "test@example.com"
    password: "yourpassword"
    totp_secret: "LB2E2RX7XFHSTGCK"  # Optional, for 2FA

  login_flow:
    - "Type $username into the email field"
    - "Type $password into the password field"
    - "Click the 'Sign In' button"

  success_condition:
    type: url_contains
    value: "/dashboard"
```

- `login_flow` — step-by-step instructions for the AI on how to log in
- `totp_secret` — Shannon auto-generates TOTP codes for 2FA
- `success_condition` — how to know login succeeded

### Scanning Rules

```yaml
rules:
  avoid:
    - description: "Don't test logout"
      type: path
      url_path: "/logout"

  focus:
    - description: "Focus on API endpoints"
      type: path
      url_path: "/api"
```

## Running with Config

```bash
./shannon start URL=https://your-app.com REPO=my-app CONFIG=./configs/my-app-config.yaml
```

## Summary

- Configuration lets Shannon test protected areas
- YAML file contains login credentials and scanning rules
- 2FA/TOTP is supported out of the box
- `avoid` and `focus` rules control scanning priorities
