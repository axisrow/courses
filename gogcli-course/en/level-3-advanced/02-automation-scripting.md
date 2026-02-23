---
title: "Automation & Scripting"
weight: 12
bookToc: true
---

# Automation & Scripting

Use gogcli in scripts to automate repetitive tasks.

## JSON + jq: The Power Combo

Most automation starts with `--json` output and `jq` for processing:

```bash
# Get all thread IDs from the last week
gog gmail search 'newer_than:7d' --json | jq -r '.threads[].id'

# Find PDF files in Drive
gog drive ls --json | jq -r '.files[] | select(.mimeType=="application/pdf") | .name'

# Get today's event summaries
gog calendar events primary --today --json | jq -r '.events[].summary'
```

## Practical Scripts

### Archive old emails

```bash
#!/bin/bash
# archive-old.sh — Archive emails older than 1 year

gog --json gmail search 'older_than:1y' --max 200 | \
  jq -r '.threads[].id' | \
  xargs -n 50 gog gmail labels modify --remove INBOX

echo "Done archiving."
```

### Download all PDF attachments

```bash
#!/bin/bash
# download-pdfs.sh — Download PDFs from Drive

mkdir -p ./pdfs

gog drive search "mimeType = 'application/pdf'" --raw-query --json | \
  jq -r '.files[].id' | \
  while read fileId; do
    gog drive download "$fileId" --out "./pdfs/${fileId}.pdf"
  done
```

### Daily schedule email

```bash
#!/bin/bash
# daily-schedule.sh — Send yourself today's schedule

SCHEDULE=$(gog calendar events primary --today --plain)

gog gmail send \
  --to me@example.com \
  --subject "Today's Schedule" \
  --body "$SCHEDULE"
```

### Update a spreadsheet from data

```bash
#!/bin/bash
# update-sheet.sh — Append today's stats to a tracking sheet

DATE=$(date +%Y-%m-%d)
UNREAD=$(gog gmail search 'is:unread' --json | jq '.threads | length')

gog sheets append SPREADSHEET_ID 'Sheet1!A:B' "${DATE}|${UNREAD}"
```

## Batch Email Processing

```bash
# Star all emails from boss
gog --json gmail search 'from:boss@company.com newer_than:30d' --max 200 | \
  jq -r '.threads[].id' | \
  xargs -n 50 gog gmail batch modify --add STARRED

# Label emails from a newsletter
gog --json gmail search 'from:newsletter@service.com' --max 200 | \
  jq -r '.threads[].id' | \
  xargs -n 50 gog gmail labels modify --add "Newsletters" --remove INBOX
```

## Non-Interactive Mode

For CI/CD and cron jobs, use `--no-input` to prevent any prompts:

```bash
gog --no-input gmail search 'is:unread' --max 5
```

For the file keyring backend, set the password via environment:

```bash
export GOG_KEYRING_PASSWORD='your-password'
export GOG_KEYRING_BACKEND=file
gog --no-input gmail search 'is:unread'
```

## Command Allowlist (Sandboxing)

Restrict which commands are available — useful for agents or untrusted scripts:

```bash
# Only allow calendar and tasks
export GOG_ENABLE_COMMANDS=calendar,tasks
gog calendar events primary --today    # Works
gog gmail search 'test'                # Blocked!
```

## Piping and Combining

```bash
# Export a Doc as text and search within it
gog docs cat DOC_ID | grep "important"

# Count events this week
gog calendar events primary --week --json | jq '.events | length'

# Find contacts who aren't in your calendar today
comm -23 \
  <(gog contacts list --json | jq -r '.contacts[].email' | sort) \
  <(gog calendar events primary --today --json | jq -r '.events[].attendees[].email' | sort)
```

## Running on a Schedule (Cron)

Add to your crontab (`crontab -e`):

```bash
# Every morning at 8am, send daily schedule
0 8 * * * /usr/local/bin/gog gmail send --to me@example.com --subject "Schedule" --body "$(/usr/local/bin/gog calendar events primary --today --plain)" 2>/dev/null
```

## Next Steps

In the next lesson, you'll learn about service accounts for Google Workspace.
