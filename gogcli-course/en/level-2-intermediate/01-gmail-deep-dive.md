---
title: "Gmail Deep Dive"
weight: 6
bookToc: true
---

# Gmail Deep Dive

In this lesson you'll learn to fully manage your email from the command line.

## Searching Emails

gogcli uses the same search syntax as Gmail's web interface:

```bash
# Emails from last 7 days
gog gmail search 'newer_than:7d' --max 20

# From a specific person
gog gmail search 'from:alice@example.com' --max 10

# With attachments
gog gmail search 'has:attachment newer_than:30d'

# Unread only
gog gmail search 'is:unread' --max 20

# Combine criteria
gog gmail search 'from:boss@company.com subject:urgent newer_than:1d'
```

### Message-Level Search

By default, search returns threads (conversations). To get individual messages:

```bash
gog gmail messages search 'newer_than:7d' --max 10

# Include the message body
gog gmail messages search 'newer_than:7d' --max 5 --include-body
```

## Reading Emails

```bash
# Read a full thread
gog gmail thread get THREAD_ID

# Read a single message
gog gmail get MESSAGE_ID

# Download attachments from a thread
gog gmail thread get THREAD_ID --download --out-dir ./attachments
```

## Sending Emails

```bash
# Simple email
gog gmail send --to recipient@example.com --subject "Hello" --body "Hi there!"

# HTML email
gog gmail send --to recipient@example.com --subject "Report" \
  --body "Plain text version" \
  --body-html "<h1>Report</h1><p>See attached.</p>"

# Body from a file
gog gmail send --to recipient@example.com --subject "Notes" --body-file ./notes.txt

# Reply to a message (with quoted original)
gog gmail send --reply-to-message-id MSG_ID --quote \
  --to recipient@example.com --subject "Re: Hello" --body "Thanks!"
```

## Managing Labels

Labels are Gmail's way of organizing emails (like folders, but better — one email can have multiple labels).

```bash
# List all labels
gog gmail labels list

# Create a new label
gog gmail labels create "Projects/Active"

# Add/remove labels on a thread
gog gmail thread modify THREAD_ID --add STARRED --remove INBOX

# Delete a label
gog gmail labels delete "Old Label"
```

## Drafts

```bash
# List drafts
gog gmail drafts list

# Create a draft
gog gmail drafts create --to bob@example.com --subject "Draft" --body "Working on this..."

# Send a draft
gog gmail drafts send DRAFT_ID
```

## Filters

Filters automatically sort incoming emails:

```bash
# List filters
gog gmail filters list

# Create a filter
gog gmail filters create --from 'noreply@example.com' --add-label 'Notifications'

# Delete a filter
gog gmail filters delete FILTER_ID
```

## Batch Operations

Process multiple emails at once:

```bash
# Star multiple messages
gog gmail batch modify MSG_ID1 MSG_ID2 --add STARRED

# Delete multiple messages
gog gmail batch delete MSG_ID1 MSG_ID2
```

## Vacation Responder

```bash
# Check current status
gog gmail vacation get

# Enable
gog gmail vacation enable --subject "Out of office" --message "I'll be back on Monday."

# Disable
gog gmail vacation disable
```

## Next Steps

In the next lesson, you'll master Calendar management.
