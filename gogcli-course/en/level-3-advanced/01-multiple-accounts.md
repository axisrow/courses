---
title: "Multiple Accounts & Aliases"
weight: 11
bookToc: true
---

# Multiple Accounts & Aliases

Manage personal and work Google accounts seamlessly.

## Adding Multiple Accounts

```bash
gog auth add personal@gmail.com
gog auth add work@company.com
```

## Switching Between Accounts

### Per-command

```bash
gog gmail search 'is:unread' --account personal@gmail.com
gog gmail search 'is:unread' --account work@company.com
```

### Via environment variable

```bash
export GOG_ACCOUNT=work@company.com
gog gmail search 'is:unread'   # Uses work account
```

### Auto-select

If you only have one account stored, `auto` picks it automatically:

```bash
gog gmail labels list --account auto
```

## Account Aliases

Instead of typing full email addresses, create short aliases:

```bash
# Create aliases
gog auth alias set work work@company.com
gog auth alias set me personal@gmail.com

# Use aliases anywhere
gog gmail search 'is:unread' --account work
gog calendar events primary --today --account me

# List aliases
gog auth alias list

# Remove an alias
gog auth alias unset work
```

Reserved names: `auto` and `default` cannot be used as aliases.

## Multiple OAuth Clients

If your work and personal accounts use different Google Cloud projects:

```bash
# Store work credentials under a named client
gog --client work auth credentials ~/Downloads/work-client.json

# Add account using that client
gog --client work auth add work@company.com

# List all stored credentials
gog auth credentials list
```

### Automatic Client Selection

Map accounts or domains to clients in your config file:

```json5
{
  account_clients: {
    "work@company.com": "work"
  },
  client_domains: {
    "company.com": "work"
  }
}
```

Or name your credentials file after the domain: `credentials-company.com.json`.

Selection order when `--client` is not set:
1. `--client` flag or `GOG_CLIENT` env var
2. `account_clients` config mapping
3. `client_domains` config mapping
4. Domain-named credentials file
5. `default`

## Configuration File

Find your config file location:

```bash
gog config path
```

Manage settings via commands:

```bash
gog config list              # Show all settings
gog config keys              # Available config keys
gog config get default_timezone
gog config set default_timezone "America/New_York"
gog config unset default_timezone
```

Example `config.json`:

```json5
{
  keyring_backend: "file",
  default_timezone: "UTC",
  account_aliases: {
    work: "work@company.com",
    personal: "me@gmail.com"
  }
}
```

## Next Steps

In the next lesson, you'll learn to automate tasks with gogcli scripts.
