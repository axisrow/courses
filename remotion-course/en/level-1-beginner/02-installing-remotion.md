---
title: "Installing Remotion"
weight: 2
bookToc: true
---

# Installing Remotion

Before you can create videos with Remotion, you need to set up your computer. Don't worry — we'll go step by step.

## Step 1: Install Node.js

Node.js is a program that lets your computer run JavaScript code. Remotion needs it.

1. Go to [nodejs.org](https://nodejs.org)
2. Download the **LTS** (Long Term Support) version
3. Run the installer and follow the prompts

To check it worked, open your terminal (Command Prompt on Windows, Terminal on Mac) and type:

```bash
node --version
```

You should see a version number like `v20.11.0`.

## Step 2: Create Your First Project

In your terminal, type:

```bash
npx create-video@latest my-first-video
```

This command downloads a starter template. When asked questions, just press Enter to accept the defaults.

## Step 3: Start the Preview

```bash
cd my-first-video
npm start
```

A browser window will open showing your video preview. You can play, pause, and scrub through your video right in the browser.

## What Just Happened?

You created a project with:
- Source code files (where your video is defined)
- A local server (for previewing)
- Configuration files

## Troubleshooting

- **"command not found"**: Make sure Node.js is installed correctly
- **Slow download**: This is normal the first time — it downloads many packages

## Summary

Installing Remotion takes three steps: install Node.js, create a project, and start the preview.
