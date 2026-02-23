---
title: "Calendar Mastery"
weight: 7
bookToc: true
---

# Calendar Mastery

Manage your schedule entirely from the terminal.

## Viewing Events

```bash
# Today's events
gog calendar events primary --today

# Tomorrow
gog calendar events primary --tomorrow

# This week
gog calendar events primary --week

# Next 3 days
gog calendar events primary --days 3

# Custom date range
gog calendar events primary --from 2025-03-01 --to 2025-03-15

# With day-of-week columns
gog calendar events primary --today --weekday

# All calendars at once
gog calendar events --all --today
```

## Searching Events

```bash
# Search within today
gog calendar search "standup" --today

# Search the next year
gog calendar search "birthday" --days 365
```

## Creating Events

```bash
# Simple event
gog calendar create primary \
  --summary "Lunch with Alice" \
  --from 2025-03-15T12:00:00Z \
  --to 2025-03-15T13:00:00Z

# With attendees and location
gog calendar create primary \
  --summary "Team Sync" \
  --from 2025-03-15T14:00:00Z \
  --to 2025-03-15T15:00:00Z \
  --attendees "alice@example.com,bob@example.com" \
  --location "Conference Room B"

# Recurring event with reminders
gog calendar create primary \
  --summary "Weekly Report" \
  --from 2025-03-17T09:00:00Z \
  --to 2025-03-17T09:30:00Z \
  --rrule "RRULE:FREQ=WEEKLY;BYDAY=MO" \
  --reminder "popup:15m" \
  --reminder "email:1h"

# All-day event
gog calendar create primary \
  --summary "Company Holiday" \
  --from 2025-12-25 \
  --to 2025-12-26 \
  --all-day

# Send notifications to attendees
gog calendar create primary \
  --summary "Planning" \
  --from 2025-03-20T10:00:00Z \
  --to 2025-03-20T11:00:00Z \
  --attendees "team@example.com" \
  --send-updates all
```

## Updating and Deleting Events

```bash
# Update an event
gog calendar update primary EVENT_ID \
  --summary "Renamed Meeting" \
  --from 2025-03-15T15:00:00Z \
  --to 2025-03-15T16:00:00Z

# Add attendees without replacing existing ones
gog calendar update primary EVENT_ID \
  --add-attendee "charlie@example.com"

# Delete an event
gog calendar delete primary EVENT_ID

# Delete and notify attendees
gog calendar delete primary EVENT_ID --send-updates all --force
```

## Responding to Invitations

```bash
gog calendar respond primary EVENT_ID --status accepted
gog calendar respond primary EVENT_ID --status declined
gog calendar respond primary EVENT_ID --status tentative
```

## Checking Availability

```bash
# Check free/busy for one or more calendars
gog calendar freebusy \
  --calendars "primary,colleague@example.com" \
  --from 2025-03-15T00:00:00Z \
  --to 2025-03-16T00:00:00Z

# Check for conflicts today
gog calendar conflicts --calendars "primary" --today
```

## Special Event Types

```bash
# Focus time (blocks your calendar)
gog calendar focus-time --from 2025-03-15T13:00:00Z --to 2025-03-15T15:00:00Z

# Out of office
gog calendar out-of-office --from 2025-04-01 --to 2025-04-02 --all-day

# Working location
gog calendar working-location --type office --office-label "HQ" \
  --from 2025-03-17 --to 2025-03-18
```

## Timezones

Set a default timezone:

```bash
export GOG_TIMEZONE=America/New_York
gog calendar events primary --today

# Or per-command
gog time now --timezone Europe/London
```

## Next Steps

In the next lesson, you'll learn to manage files with Google Drive.
