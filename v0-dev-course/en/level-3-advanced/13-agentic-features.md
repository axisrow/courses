---
title: "Agentic Features"
weight: 13
bookToc: true
---

# Agentic Features

## What Does "Agentic" Mean?

In v0, "agentic" means the AI doesn't just follow one instruction — it plans, breaks tasks into steps, and executes them autonomously. It acts more like an assistant than a simple tool.

## How Agentic Mode Works

When you give v0 a complex request, it:

1. **Plans** — breaks your request into smaller tasks
2. **Creates tasks** — organizes the work in order
3. **Executes** — builds each piece step by step
4. **Connects** — wires everything together (database, API, UI)
5. **Tests** — checks that things work

## Example

Prompt: "Build a job board where companies can post jobs and candidates can apply"

v0 will automatically:
- Design the database schema (jobs, companies, applications)
- Create the job listing page
- Build the job posting form
- Create the application flow
- Connect everything to a database
- Set up the API routes

## When to Use Agentic Mode

- Building complete applications (not just single components)
- Projects with multiple connected parts
- When you want v0 to make architectural decisions for you

## Tips for Agentic Prompts

- Describe the **goal**, not the steps
- Mention the key features you need
- Let v0 decide the technical approach
- Review the plan before it starts building

## Summary

Agentic features let v0 handle complex, multi-step projects autonomously. Describe your goal, and let the AI plan and build. Next: building full applications.
