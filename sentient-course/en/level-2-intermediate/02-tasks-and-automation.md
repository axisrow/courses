---
title: "Tasks and Automation"
weight: 7
bookToc: true
---

# Tasks and Automation

## Beyond Chat

Sentient isn't limited to real-time conversations. It can run **background tasks** — actions that happen on a schedule, in response to a trigger, or as long-running processes.

## Types of Tasks

| Type | Description | Example |
|---|---|---|
| **Scheduled** | Runs once at a specific date/time. | "Send me a summary of today's emails at 6 PM." |
| **Recurring** | Runs on a regular schedule (daily, weekly, etc.). | "Every Monday, create a weekly plan from my calendar." |
| **Triggered** | Runs when a specific event occurs. | "When I receive an email from my boss, notify me on Slack." |
| **Swarm** | A complex task broken into sub-tasks executed by multiple AI agents. | "Research competitors and create a report." |

## Creating a Task

1. Open the **Tasks** page.
2. Click **New Task**.
3. Use the **Task Composer** to describe what you want.
4. Choose the type (scheduled, recurring, triggered, or swarm).
5. Configure the schedule or trigger conditions.
6. Save. Sentient's **Celery workers** will handle execution.

## Viewing Task History

The Tasks page shows:

- Active tasks and their next run time.
- Completed task history with results.
- Failed tasks with error details.

## How Tasks Work Under the Hood

1. You create a task via the UI or chat.
2. The server stores the task definition in the database.
3. **Celery Beat** (a scheduler) checks for due tasks.
4. When a task is due, a **Celery Worker** picks it up and executes it.
5. The worker uses the same AI + MCP pipeline as chat, but without waiting for your input.

## Summary

Tasks transform Sentient from a reactive chatbot into a proactive automation engine. Set it up once, and it works for you around the clock.
