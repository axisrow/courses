---
title: "Advanced Cascade Workflows"
weight: 11
bookToc: true
---

# Advanced Cascade Workflows

## Beyond Simple Prompts

At this level, you can use Cascade for complex, multi-step tasks.

## Chained Prompts

Break large tasks into steps:

1. "Analyze the current project structure and suggest improvements"
2. "Implement the folder restructuring you suggested"
3. "Update all import paths to match the new structure"

Each prompt builds on the previous conversation context.

## System Design with Cascade

Ask Cascade to help design before coding:

```
I need a notification system that supports email, SMS, and push notifications.
Design the class hierarchy and interfaces first, then implement.
```

## Code Generation Patterns

### Generate from Spec
```
Here is my API spec (OpenAPI):
[paste spec]
Generate the Express routes and controllers.
```

### Generate from Examples
```
Given this input/output example:
Input: [1, 2, 3, 4, 5]
Output: [2, 4] (even numbers only)

Write a generic filter function.
```

### Generate Tests from Code
```
Look at src/services/auth.js and generate comprehensive unit tests
covering edge cases.
```

## Multi-turn Conversations

Keep the conversation going to refine results:

1. "Create a caching layer for the API"
2. "Add TTL support to the cache"
3. "Make it work with Redis instead of in-memory"
4. "Add cache invalidation on data updates"

## Using @-mentions

In Cascade, you can reference:
- `@file` — to point to a specific file
- `@folder` — to reference a directory
- `@symbol` — to reference a function or class

## Practice

Use Cascade to design and implement a complete feature from scratch using chained prompts.
