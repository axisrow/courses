---
title: "Your First Workflow"
weight: 3
bookToc: true
---

# Your First Workflow

## Goal

In this lesson, you will build a simple workflow that fetches a random joke from the internet and displays it.

## Step 1: Create a New Workflow

1. Open n8n in your browser
2. Click **Add Workflow** (or the `+` icon)
3. Give it a name: "My First Workflow"

## Step 2: Add a Trigger

Every workflow needs a trigger — the event that starts it.

1. Click the `+` button on the canvas
2. Search for **Manual Trigger**
3. Click it to add it to the canvas

The Manual Trigger lets you start the workflow by clicking a button.

## Step 3: Add an HTTP Request Node

1. Click the `+` button on the right side of the trigger node
2. Search for **HTTP Request**
3. Set the URL to: `https://official-joke-api.appspot.com/random_joke`
4. Method: **GET**
5. Click **Execute Step** to test it

You should see a joke with `setup` and `punchline` fields.

## Step 4: Add a Set Node

Let's format the output:

1. Add a **Set** node after the HTTP Request
2. Click **Add Value** → **String**
3. Name: `joke`
4. Value: `{{ $json.setup }} — {{ $json.punchline }}`

## Step 5: Run the Workflow

1. Click **Execute Workflow** at the bottom
2. Check each node — they should all show green checkmarks
3. Click the last node to see your formatted joke

## Understanding Data Flow

Data flows from left to right through the nodes:

```
Manual Trigger → HTTP Request → Set
                 (fetches data)   (formats data)
```

Each node receives data from the previous node, processes it, and passes it to the next.

## Save Your Workflow

Click **Save** (Ctrl+S) to keep your workflow. You can find it later in the workflow list.

## Practice

Try modifying the workflow:
- Change the API URL to a different public API
- Add more fields in the Set node
- Add a third node to the chain

## Summary

You built your first n8n workflow! You learned how to add nodes, connect them, and run the workflow. Next, you will learn about different types of nodes.
