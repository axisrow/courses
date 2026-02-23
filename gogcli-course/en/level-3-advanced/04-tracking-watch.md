---
title: "Email Tracking & Push Notifications"
weight: 14
bookToc: true
---

# Email Tracking & Push Notifications

Advanced Gmail features for power users.

## Email Tracking

gogcli can track when recipients open your emails using a small Cloudflare Worker backend.

### Setup

```bash
# Configure tracking for your account (generates encryption keys)
gog gmail track setup --worker-url https://gog-email-tracker.YOUR-ACCOUNT.workers.dev
```

Follow the printed instructions to deploy the Cloudflare Worker.

### Sending Tracked Emails

```bash
gog gmail send \
  --to recipient@example.com \
  --subject "Proposal" \
  --body-html "<p>Please review the attached proposal.</p>" \
  --track
```

**Requirements:**
- Exactly 1 recipient (no CC/BCC)
- HTML body (`--body-html` or `--quote`)

For multiple recipients, use `--track-split` to send separate tracked emails:

```bash
gog gmail send \
  --to alice@example.com,bob@example.com \
  --subject "Update" \
  --body-html "<p>Weekly update</p>" \
  --track-split
```

### Checking Opens

```bash
# By tracking ID
gog gmail track opens TRACKING_ID

# By recipient email
gog gmail track opens --to recipient@example.com

# View tracking status
gog gmail track status
```

**Privacy note:** The tracking worker stores IP address, user-agent, and approximate location by default.

## Gmail Watch (Push Notifications)

Gmail Watch uses Google Pub/Sub to notify you in real time when new emails arrive.

### How It Works

1. You tell Gmail to "watch" your inbox
2. Gmail sends a notification to a Pub/Sub topic when something changes
3. gogcli runs a local server that receives these notifications
4. The server can trigger actions (like calling a webhook)

### Setup

#### Step 1: Create a Pub/Sub topic and subscription in Google Cloud Console

#### Step 2: Start watching

```bash
gog gmail watch start \
  --topic projects/YOUR-PROJECT/topics/YOUR-TOPIC \
  --label INBOX
```

#### Step 3: Run the notification server

```bash
# Basic setup (shared token auth)
gog gmail watch serve \
  --bind 127.0.0.1 \
  --token YOUR_SHARED_SECRET \
  --hook-url http://127.0.0.1:18789/hooks/agent

# Production setup (OIDC verification)
gog gmail watch serve \
  --bind 0.0.0.0 \
  --verify-oidc \
  --oidc-email svc@your-project.iam.gserviceaccount.com \
  --hook-url https://your-webhook.example.com/hooks
```

### Filtering Notifications

```bash
# Exclude spam and trash (default)
gog gmail watch serve \
  --bind 127.0.0.1 \
  --token SECRET \
  --exclude-labels SPAM,TRASH \
  --hook-url http://localhost:8080/hook
```

### Using Gmail History

When you receive a push notification, fetch what changed:

```bash
gog gmail history --since HISTORY_ID
```

## Gmail Delegation (Workspace)

Allow someone else to read and send from your Gmail:

```bash
# List delegates
gog gmail delegates list

# Add a delegate
gog gmail delegates add --email assistant@company.com

# Remove a delegate
gog gmail delegates remove --email assistant@company.com
```

## Auto-Forwarding

```bash
# Check current forwarding
gog gmail autoforward get

# Set up forwarding
gog gmail forwarding add --email backup@example.com
gog gmail autoforward enable --email backup@example.com

# Disable
gog gmail autoforward disable
```

## Send-As (Email Aliases)

```bash
# List send-as addresses
gog gmail sendas list

# Add a send-as address
gog gmail sendas create --email alias@example.com
```

## Next Steps

In the final lesson, you'll learn about security best practices.
