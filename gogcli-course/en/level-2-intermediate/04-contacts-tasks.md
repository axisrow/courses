---
title: "Contacts & Tasks"
weight: 9
bookToc: true
---

# Contacts & Tasks

Keep your address book and to-do lists in order from the command line.

## Contacts

### Searching and Viewing

```bash
# Search contacts by name
gog contacts search "Alice" --max 10

# List all contacts
gog contacts list --max 50

# Get a specific contact
gog contacts get people/RESOURCE_NAME

# Get contact by email
gog contacts get alice@example.com
```

### Creating Contacts

```bash
gog contacts create \
  --given "John" \
  --family "Doe" \
  --email "john@example.com" \
  --phone "+1234567890"
```

### Updating Contacts

```bash
gog contacts update people/RESOURCE_NAME \
  --given "Jane" \
  --email "jane@example.com" \
  --birthday "1990-05-12" \
  --notes "Met at conference"
```

### Deleting Contacts

```bash
gog contacts delete people/RESOURCE_NAME
```

### Other Contacts

"Other contacts" are people you've interacted with but haven't saved:

```bash
gog contacts other list --max 50
gog contacts other search "John" --max 10
```

### Workspace Directory

If you use Google Workspace, you can search the company directory:

```bash
gog contacts directory list --max 50
gog contacts directory search "Jane" --max 10
```

## Tasks

### Managing Task Lists

```bash
# List all task lists
gog tasks lists

# Create a new task list
gog tasks lists create "Shopping"
```

### Working with Tasks

```bash
# View tasks in a list
gog tasks list TASKLIST_ID --max 20

# Get a specific task
gog tasks get TASKLIST_ID TASK_ID

# Add a new task
gog tasks add TASKLIST_ID --title "Buy groceries"

# Add a task with a due date
gog tasks add TASKLIST_ID --title "Pay rent" --due 2025-04-01

# Add a recurring task
gog tasks add TASKLIST_ID --title "Weekly review" \
  --due 2025-03-07 --repeat weekly --repeat-count 12
```

### Updating Tasks

```bash
# Change the title
gog tasks update TASKLIST_ID TASK_ID --title "Buy organic groceries"

# Mark as complete
gog tasks done TASKLIST_ID TASK_ID

# Mark as incomplete
gog tasks undo TASKLIST_ID TASK_ID
```

### Deleting Tasks

```bash
# Delete a single task
gog tasks delete TASKLIST_ID TASK_ID

# Clear all completed tasks from a list
gog tasks clear TASKLIST_ID
```

## People API

The People API provides profile information:

```bash
# Your own profile
gog people me

# Someone else's profile
gog people get people/USER_ID

# Search Workspace directory
gog people search "Ada Lovelace" --max 5

# View relations (manager, etc.)
gog people relations
```

## Practical Example: Quick Contact Lookup Before a Meeting

```bash
# Check who's in your 2pm meeting
gog calendar events primary --today --json | jq '.events[] | select(.summary | contains("Sync")) | .attendees'

# Look up their contact info
gog contacts get colleague@example.com
```

## Next Steps

In the next lesson, you'll learn about Sheets, Forms, and Slides.
