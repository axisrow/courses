---
title: "Prompt Engineering Basics"
weight: 4
bookToc: true
---

# Prompt Engineering Basics

## What is a Prompt?

A prompt is the instruction you give to the AI. A good prompt = a good answer.

## The ROLE-TASK-FORMAT Pattern

Structure your prompts with three parts:

```
ROLE: You are a [role].
TASK: Help the user [do something].
FORMAT: Respond in [format].
```

### Example

```
You are an experienced nutritionist.
Help users create healthy meal plans based on their dietary needs.
Respond with a structured daily plan using bullet points.
```

## Variables

Dify supports variables in prompts using `{{variable_name}}`:

```
Write a {{tone}} email about {{topic}} for {{audience}}.
```

Users fill in the variables when using the app.

## Tips for Better Prompts

1. **Be specific** — "Summarize in 3 bullet points" beats "Summarize"
2. **Give examples** — Show the AI what good output looks like
3. **Set boundaries** — "Do NOT give medical advice"
4. **Use simple language** — Clear instructions work best

## Temperature & Parameters

| Parameter | Low Value | High Value |
|-----------|-----------|------------|
| **Temperature** | Focused, predictable | Creative, varied |
| **Top P** | Narrow word choices | Wider word choices |
| **Max Tokens** | Short answers | Long answers |

## Common Mistakes

- ❌ Too vague: "Help me"
- ✅ Specific: "Help me write a 100-word product description for a blue leather wallet"
- ❌ Too long: Walls of text confuse the model
- ✅ Structured: Use numbered lists and clear sections

## Next Step

Let's publish your app so others can use it!
