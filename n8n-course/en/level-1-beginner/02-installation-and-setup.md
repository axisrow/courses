---
title: "Installation and Setup"
weight: 2
bookToc: true
---

# Installation and Setup

## Prerequisites

Before installing n8n, make sure you have:

- A computer with Windows, macOS, or Linux
- **Node.js** (version 18 or newer) installed
- Basic knowledge of using a terminal (command line)

## Option 1: Install with npm

The simplest way to install n8n:

```bash
npm install n8n -g
```

Then start it:

```bash
n8n start
```

Open your browser and go to `http://localhost:5678`.

## Option 2: Install with Docker

If you prefer Docker:

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

## Option 3: Use n8n Cloud

Don't want to install anything? Use [n8n Cloud](https://n8n.io/cloud/) — a hosted version that's ready to use in seconds.

## First Launch

When you open n8n for the first time, you will:

1. Create an **owner account** (email and password)
2. See the **workflow editor** — a blank canvas where you build automations
3. Notice the **node panel** on the left — this is where you find all available nodes

## The Interface

- **Canvas** — The main area where you drag and connect nodes
- **Node panel** — Search and add nodes (click the `+` button)
- **Execution list** — See past workflow runs
- **Settings** — Configure n8n options

## Verify Your Installation

Try this quick test:

1. Click the `+` button on the canvas
2. Search for "Manual Trigger" and add it
3. Add a "Set" node and connect it
4. Click **Execute Workflow**

If you see green checkmarks, n8n is working correctly!

## Summary

You now have n8n running on your machine. In the next lesson, you will create your first real workflow.
