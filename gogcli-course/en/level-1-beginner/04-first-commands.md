---
title: "Your First Commands"
weight: 4
bookToc: true
---

# Your First Commands

Now that authentication is set up, let's try some real commands.

## Setting Your Default Account

To avoid typing `--account` every time:

```bash
export GOG_ACCOUNT=you@gmail.com
```

Add this line to your `~/.bashrc` or `~/.zshrc` to make it permanent.

## Gmail: Check Your Inbox

### List your labels

```bash
gog gmail labels list
```

### Search recent emails

```bash
gog gmail search 'newer_than:7d' --max 5
```

This shows your last 5 email threads from the past 7 days.

### Read a specific thread

Copy a thread ID from the search results, then:

```bash
gog gmail thread get THREAD_ID_HERE
```

## Calendar: See Your Schedule

### List your calendars

```bash
gog calendar calendars
```

### View today's events

```bash
gog calendar events primary --today
```

`primary` means your main calendar.

### View this week's events

```bash
gog calendar events primary --week
```

## Drive: Browse Your Files

### List recent files

```bash
gog drive ls --max 10
```

### Search for a file

```bash
gog drive search "budget" --max 5
```

## Contacts: Find People

```bash
gog contacts search "John" --max 5
```

## Tasks: Check Your To-Dos

### List your task lists

```bash
gog tasks lists
```

### View tasks in a list

```bash
gog tasks list TASKLIST_ID_HERE
```

## Quick Reference

| What you want | Command |
|--------------|---------|
| Recent emails | `gog gmail search 'newer_than:7d'` |
| Today's events | `gog calendar events primary --today` |
| List files | `gog drive ls --max 10` |
| Find a contact | `gog contacts search "name"` |
| Your task lists | `gog tasks lists` |
| Current time | `gog time now` |

## Tips

- Add `--max N` to limit results
- Use `--account email` to specify which account (if you have multiple)
- Every command has `--help` for details

## Next Steps

In the next lesson, you'll learn about different output formats — human-readable, plain text, and JSON.
