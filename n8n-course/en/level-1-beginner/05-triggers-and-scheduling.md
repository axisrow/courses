---
title: "Triggers and Scheduling"
weight: 5
bookToc: true
---

# Triggers and Scheduling

## What Are Triggers?

A trigger is the first node in a workflow. It decides **when** the workflow runs. Without a trigger, nothing happens.

## Types of Triggers

### Manual Trigger
Run the workflow by clicking a button. Good for testing.

### Schedule Trigger
Run the workflow on a timer. Examples:
- Every 5 minutes
- Every day at 9:00 AM
- Every Monday at 8:00 AM
- On the 1st of every month

**Settings:**
- **Rule** — Choose interval, cron, or specific times
- **Interval** — Minutes, hours, or days between runs

**Cron examples:**
```
0 9 * * *       → Every day at 9:00 AM
0 9 * * 1       → Every Monday at 9:00 AM
*/30 * * * *    → Every 30 minutes
0 0 1 * *       → First day of every month
```

### Webhook Trigger
Run the workflow when an external service sends an HTTP request.

1. Add a **Webhook** node
2. Copy the webhook URL
3. Paste it into the external service
4. When that service sends data, your workflow runs

**Use cases:**
- Receive form submissions
- Get notifications from GitHub, Stripe, etc.
- Connect with custom applications

### App Triggers
Many app nodes can act as triggers:
- **Gmail Trigger** — When a new email arrives
- **Slack Trigger** — When a message is posted
- **GitHub Trigger** — When a new issue is created
- **Google Sheets Trigger** — When a new row is added

## Activating a Workflow

Trigger nodes only work when the workflow is **active**:

1. Build your workflow
2. Click the **Active** toggle (top right)
3. The workflow now runs automatically based on the trigger

Manual triggers still require you to click Execute.

## Polling vs. Webhook

| Feature | Polling | Webhook |
|---------|---------|---------|
| How it works | n8n checks periodically | External service sends data |
| Speed | Slight delay | Instant |
| Setup | Easier | Requires URL configuration |
| Examples | Email trigger, RSS | GitHub, Stripe, custom apps |

## Practice

1. Create a workflow with a **Schedule Trigger** set to every 1 minute
2. Add an **HTTP Request** node to fetch the current time from `http://worldtimeapi.org/api/timezone/UTC`
3. Activate the workflow and check the execution list after a few minutes

## Summary

You learned how triggers work and how to schedule workflows. This completes the beginner level! Next, you will move to intermediate topics starting with working with APIs.
