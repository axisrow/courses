---
title: "Your First AI App"
weight: 3
bookToc: true
---

# Your First AI App

## Goal

Build a simple chatbot that answers questions about a topic you choose.

## Step by Step

### 1. Create the App

1. Go to **Studio** → **Create App**
2. Choose **Chatbot**
3. Name it (e.g., "Travel Assistant")
4. Click **Create**

### 2. Write the System Prompt

In the **Prompt** section, write instructions:

```
You are a friendly travel assistant. Help users plan trips.
Give practical advice about destinations, budgets, and packing.
Keep answers concise — 2-3 paragraphs max.
```

### 3. Choose a Model

In the model selector (top right), pick your LLM. For example:
- `gpt-4o-mini` — fast and cheap
- `gpt-4o` — smarter but costs more

### 4. Test It

Use the **Preview** panel on the right. Type a message like:

> "I want to visit Japan for 10 days on a budget. Any tips?"

Check if the answer is helpful and follows your instructions.

### 5. Adjust

- If answers are too long, add "Be brief" to the prompt
- If answers lack detail, ask for "detailed, step-by-step advice"
- Adjust **Temperature** (lower = more focused, higher = more creative)

## App Types in Dify

| Type | Best For |
|------|----------|
| **Chatbot** | Multi-turn conversations |
| **Text Generator** | Single input → single output |
| **Agent** | AI that can use tools and take actions |
| **Workflow** | Complex multi-step logic |

## Next Step

Let's learn how to write better prompts!
