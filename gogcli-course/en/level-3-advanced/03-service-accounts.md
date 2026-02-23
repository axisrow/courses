---
title: "Service Accounts & Workspace"
weight: 13
bookToc: true
---

# Service Accounts & Workspace

For Google Workspace organizations, service accounts provide powerful, automated access.

## What Is a Service Account?

A service account is a special Google identity that belongs to a project, not a person. With **domain-wide delegation**, a service account can impersonate any user in your Workspace domain — no browser login needed.

This is ideal for:
- Server-side automation
- Admin tools that manage multiple users
- CI/CD pipelines
- Background jobs

## Setting Up a Service Account

### Step 1: Create in Google Cloud

1. Go to **IAM & Admin → Service Accounts** in Google Cloud Console
2. Create a new service account
3. Enable **Domain-wide delegation**
4. Create a JSON key (**Keys → Add key → Create new key → JSON**)
5. Download the key file

### Step 2: Allowlist Scopes in Workspace Admin

1. Open **Admin Console → Security → API controls → Domain-wide delegation**
2. Add a new API client:
   - **Client ID**: from the service account
   - **Scopes**: comma-separated list of OAuth scopes you need

Check available scopes:

```bash
gog auth services
```

### Step 3: Configure gogcli

```bash
gog auth service-account set user@yourdomain.com --key ~/Downloads/service-account.json
```

### Step 4: Verify

```bash
gog --account user@yourdomain.com auth status
gog auth list   # Shows "service-account" next to the account
```

Now commands for that account use the service account automatically (it takes precedence over OAuth tokens).

## Managing Service Accounts

```bash
# Check status
gog auth service-account status user@yourdomain.com

# Remove service account configuration
gog auth service-account unset user@yourdomain.com
```

## Google Keep (Workspace Only)

Keep requires a service account with domain-wide delegation:

```bash
gog auth service-account set user@yourdomain.com --key ~/key.json

# List notes
gog keep list --account user@yourdomain.com

# Get a specific note
gog keep get NOTE_ID --account user@yourdomain.com

# Search notes
gog keep search "meeting notes" --account user@yourdomain.com

# Download attachment
gog keep attachment ATTACHMENT_NAME --account user@yourdomain.com --out ./file.bin
```

## Google Chat (Workspace Only)

Chat requires a Workspace account (not available for personal Gmail):

```bash
# List spaces
gog chat spaces list

# Find a space
gog chat spaces find "Engineering"

# Send a message
gog chat messages send spaces/SPACE_ID --text "Build deployed!"

# Direct message
gog chat dm send user@company.com --text "Hey, quick question..."
```

## Google Groups (Workspace Only)

```bash
# List groups you belong to
gog groups list

# View members of a group
gog groups members engineering@company.com
```

## Google Classroom (Workspace for Education)

```bash
# List courses
gog classroom courses list

# Create a course
gog classroom courses create --name "Math 101"

# Manage roster
gog classroom roster COURSE_ID
gog classroom students add COURSE_ID student@school.edu

# Create an assignment
gog classroom coursework create COURSE_ID \
  --title "Homework 1" --type ASSIGNMENT --state PUBLISHED

# Grade a submission
gog classroom submissions grade COURSE_ID WORK_ID SUBMISSION_ID --grade 95
```

## Next Steps

In the next lesson, you'll learn about email tracking and Gmail push notifications.
