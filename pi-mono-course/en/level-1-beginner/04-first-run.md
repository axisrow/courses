---
title: "First Run"
weight: 4
bookToc: true
---

# First Run

## Introduction

In this lesson, we'll run Pi for the first time and complete a few simple tasks.

## Preparation

Make sure Pi is installed and your API key is configured:

```bash
pi --help
```

## Step-by-Step Instructions

### Step 1: Launch Pi

```bash
mkdir my-project && cd my-project
pi
```

### Step 2: Say hello

Simply type:

```
Hello! What can you do?
```

The agent will describe its capabilities.

### Step 3: Ask it to create a file

```
Create a README.md with a description for "My First Project"
```

### Step 4: Ask it to run a command

```
Show the files in the current directory
```

### Step 5: Exit

Press `Ctrl+C` or type `/exit`.

## Useful Commands

| Command | Action |
|---------|--------|
| `/help` | List commands |
| `/login` | Authenticate with a provider |
| `/model` | Select model |
| `/exit` | Exit |

## Summary

- Launched Pi in interactive mode
- Asked the agent to create a file and run a command
- Learned basic commands
