---
title: "Security & Best Practices"
weight: 15
bookToc: true
---

# Security & Best Practices

Keep your Google accounts and data safe while using gogcli.

## Credential Security

### Never commit credentials to Git

Your OAuth client JSON and service account keys should never be in version control:

```bash
# Add to .gitignore
echo "client_secret_*.json" >> .gitignore
echo "service-account*.json" >> .gitignore
```

Store credentials outside your project directory.

### Use different OAuth clients for dev and production

```bash
gog --client dev auth credentials ~/dev-client.json
gog --client prod auth credentials ~/prod-client.json
```

### Regularly audit your accounts

```bash
# List all stored accounts
gog auth list

# Verify tokens are still valid
gog auth list --check

# Check auth details
gog auth status

# Remove unused accounts
gog auth remove old@example.com
```

### Revoke compromised tokens

If you suspect a token has been compromised:

```bash
# Re-authorize with force consent (invalidates old token)
gog auth add you@gmail.com --force-consent

# Or remove and re-add
gog auth remove you@gmail.com
gog auth add you@gmail.com
```

You can also revoke access from Google's security page: [myaccount.google.com/permissions](https://myaccount.google.com/permissions)

## Least-Privilege Authentication

Only request the scopes you actually need:

```bash
# Read-only access (can't send emails or modify data)
gog auth add you@gmail.com --services drive,calendar --readonly

# Only specific services
gog auth add you@gmail.com --services calendar,tasks

# Limited Drive scope (only files created by this app)
gog auth add you@gmail.com --services drive --drive-scope file
```

## Keyring Security

### macOS: Use Keychain (default)

The most secure option on macOS. Tokens are stored in the system Keychain.

### Linux/Containers: Encrypted file backend

```bash
gog auth keyring file
```

For non-interactive environments:

```bash
export GOG_KEYRING_PASSWORD='strong-random-password'
export GOG_KEYRING_BACKEND=file
```

**Never hardcode** the keyring password in scripts. Use a secrets manager or environment variable injection.

### Check your current backend

```bash
gog auth keyring
```

## Sandboxing with Command Allowlists

When running gogcli in automated or agent contexts, restrict available commands:

```bash
# Only allow read operations
export GOG_ENABLE_COMMANDS=calendar,tasks

# The agent can use calendar and tasks, but nothing else
gog calendar events primary --today    # ✅ Allowed
gog gmail send --to ...                # ❌ Blocked
```

## Best Practices Checklist

1. ✅ **Use least-privilege scopes** — only request what you need
2. ✅ **Store credentials outside your code** — never in Git
3. ✅ **Use separate OAuth clients** for different environments
4. ✅ **Regularly audit** stored accounts with `gog auth list --check`
5. ✅ **Remove unused accounts** with `gog auth remove`
6. ✅ **Use `--no-input`** in automated environments to prevent hanging
7. ✅ **Set `GOG_ENABLE_COMMANDS`** for sandboxed/agent runs
8. ✅ **Use service accounts** for Workspace automation (no user tokens on servers)
9. ✅ **Rotate credentials** periodically
10. ✅ **Use `--force-consent`** if you suspect token compromise

## Verbose Mode for Debugging

When troubleshooting, enable verbose logging to see API requests:

```bash
gog --verbose gmail search 'newer_than:1d'
```

This shows the exact HTTP requests and responses — helpful for diagnosing permission errors.

## Congratulations!

You've completed the gogcli course! You now know how to:

- Install and configure gogcli
- Manage Gmail, Calendar, Drive, Contacts, Tasks, Sheets, and more
- Work with multiple accounts and OAuth clients
- Automate tasks with scripts
- Use service accounts for Workspace
- Track emails and set up push notifications
- Follow security best practices

Happy automating! 🎉
