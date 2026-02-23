---
title: "Basic Nodes"
weight: 4
bookToc: true
---

# Basic Nodes

## What Are Nodes?

Nodes are the building blocks of every n8n workflow. Each node does one specific job. You connect nodes together to build powerful automations.

## Categories of Nodes

### Trigger Nodes
These start your workflow. Examples:
- **Manual Trigger** — Start by clicking a button
- **Schedule Trigger** — Start at a set time (like a cron job)
- **Webhook** — Start when an external service sends data

### Action Nodes
These do the actual work:
- **HTTP Request** — Call any API or website
- **Set** — Create or modify data fields
- **IF** — Make decisions based on conditions
- **Code** — Write custom JavaScript or Python
- **Merge** — Combine data from two sources

### App Nodes
These connect to specific services:
- **Gmail** — Send and read emails
- **Slack** — Send messages to channels
- **Google Sheets** — Read and write spreadsheet data
- **Notion** — Manage pages and databases
- **GitHub** — Work with repositories and issues

## The Most Important Nodes

### HTTP Request
The most versatile node. You can connect to any service that has an API.

```
URL: https://api.example.com/data
Method: GET, POST, PUT, DELETE
Headers: Authorization, Content-Type
Body: JSON data to send
```

### Set Node
Use it to reshape your data:
- Rename fields
- Add new fields
- Remove unwanted fields
- Combine values with expressions

### IF Node
Creates two paths based on a condition:
- **True** path — when the condition matches
- **False** path — when it does not

Example: If `status` equals `"urgent"` → send Slack alert, else → log to spreadsheet.

## How to Add a Node

1. Click the `+` button on the canvas or on a node
2. Browse categories or search by name
3. Click the node to add it
4. Configure its settings
5. Click **Execute Step** to test

## Node Settings

Every node has:
- **Parameters** — Main settings for what the node does
- **Settings** — Extra options like retries and error handling
- **Notes** — Add your own description

## Practice

Build a workflow with these nodes:
1. **Manual Trigger** → **Set** (create a name and age) → **IF** (age > 18) → two **Set** nodes (one for "adult", one for "minor")

## Summary

You now know the main types of nodes in n8n. In the next lesson, you will learn about triggers and scheduling.
