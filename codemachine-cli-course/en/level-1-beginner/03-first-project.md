---
title: "Your First Project"
weight: 3
bookToc: true
---

# Your First Project

## Setting Up a Project Folder

Let's create a simple project to practice with CodeMachine:

```bash
mkdir my-first-workflow
cd my-first-workflow
```

## Launching CodeMachine

Now, start CodeMachine:

```bash
codemachine
```

When you run this for the first time, CodeMachine creates a `.codemachine` folder inside your project. This folder stores all workflow configurations and settings.

## The .codemachine Folder

```
my-first-workflow/
└── .codemachine/
    ├── config/          ← agent and workflow settings
    ├── prompts/         ← instructions for AI agents
    ├── inputs/          ← your project specifications
    └── logs/            ← execution logs
```

You don't need to create these folders manually — CodeMachine does it for you.

## The TUI (Text User Interface)

When CodeMachine launches, you see a text-based interface in your terminal. This is the TUI. It shows:

- The current workflow status
- Which agent is active
- A timeline of completed steps

## Keyboard Shortcuts

| Key | What It Does |
|-----|-------------|
| Tab | Show/hide the timeline panel |
| Shift+Tab | Toggle autonomous mode |
| P | Pause the workflow |
| H | View history |
| ↑ / ↓ | Navigate |
| Escape | Stop (with confirmation) |

## The Ali Workflow Builder

CodeMachine comes with a built-in workflow called **Ali**. Ali is a friendly assistant that helps you create your first workflow by asking you questions and generating the necessary files.

Think of Ali as a setup wizard — it guides you through the process step by step.

## Summary

- Create a project folder and run `codemachine` inside it
- CodeMachine creates a `.codemachine` folder automatically
- The TUI provides a visual interface in your terminal
- Ali helps you build your first workflow interactively

> **Next lesson:** Understanding workflows — what they are and how they work.
