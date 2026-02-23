---
title: "Error Handling"
weight: 8
bookToc: true
---

# Error Handling

## Why Handle Errors?

Workflows deal with external services that can fail at any time. Without error handling, one failure stops your entire workflow.

## Types of Errors

- **Connection errors** — Cannot reach the service
- **Authentication errors** — Invalid credentials
- **Data errors** — Unexpected data format
- **Rate limits** — Too many requests
- **Timeout** — Service took too long to respond

## Built-in Error Handling

### Continue on Fail
Enable this in any node's **Settings** tab:
- The node catches the error instead of stopping
- The next node receives error info in `$json.error`
- The workflow continues running

### Retry on Fail
Also in **Settings**:
- Set number of retries (e.g., 3)
- Set wait time between retries (e.g., 1000ms)
- Good for temporary failures

## Error Workflow

You can set a global error handler:

1. Create a separate workflow (e.g., "Error Handler")
2. Start it with an **Error Trigger** node
3. Add actions: send Slack alert, email notification, log to database
4. In your main workflow, go to **Settings → Error Workflow** and select it

Now, whenever any workflow fails, the error handler runs automatically.

## The IF Node for Validation

Check data before processing:

```
IF → $json.email contains "@"
   True → continue processing
   False → send error notification
```

## Try/Catch with Code Node

```javascript
try {
  const result = JSON.parse(items[0].json.rawData);
  items[0].json.parsed = result;
} catch (error) {
  items[0].json.parseError = error.message;
}
return items;
```

## Error Patterns

### Notify on Failure
```
Main Workflow → Error Workflow → Slack / Email notification
```

### Fallback Value
```
HTTP Request (might fail) → IF (has error?) → Yes: Set default value
                                             → No: continue normally
```

### Dead Letter Queue
```
Failed items → Save to Google Sheet for manual review later
```

## Monitoring Executions

1. Go to **Executions** in the left menu
2. Filter by **Failed** to see errors
3. Click an execution to see which node failed and why
4. Fix the issue and re-run

## Practice

1. Create a workflow that calls a broken URL (e.g., `https://httpstat.us/500`)
2. Enable **Continue on Fail**
3. Add an **IF** node to check if an error occurred
4. On error: log the error message with a Set node
5. Create an Error Workflow that sends you a notification

## Summary

You now know how to make your workflows resilient. Next, you will learn about conditional logic and branching.
