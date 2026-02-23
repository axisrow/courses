---
title: "Installing QMD"
weight: 2
bookToc: true
---

# Installing QMD

## What You Need

Before installing QMD, make sure you have:

- **Node.js** version 22 or newer
- **macOS users**: Homebrew SQLite (`brew install sqlite`)

Don't worry if you're not sure — we'll check together.

## Check Your Node.js Version

Open your terminal (Terminal on Mac, Command Prompt on Windows) and type:

```sh
node --version
```

You should see something like `v22.0.0` or higher. If not, visit [nodejs.org](https://nodejs.org) to install the latest version.

## Install QMD

Run this command in your terminal:

```sh
npm install -g @tobilu/qmd
```

Or if you use Bun:

```sh
bun install -g @tobilu/qmd
```

## Verify the Installation

Type this to confirm QMD is installed:

```sh
qmd status
```

You should see information about the QMD index. If you see an error about the command not being found, try closing and reopening your terminal.

## Try It Without Installing

If you just want to try QMD without installing it globally:

```sh
npx @tobilu/qmd status
```

This downloads and runs QMD temporarily.

## About the AI Models

QMD uses three small AI models that run on your computer:

| Model | What It Does | Size |
|-------|-------------|------|
| EmbeddingGemma | Understands document meaning | ~300 MB |
| Qwen3 Reranker | Sorts results by relevance | ~640 MB |
| QMD Query Expansion | Improves your searches | ~1.1 GB |

These models are downloaded automatically the first time you use them. They're stored in `~/.cache/qmd/models/`.

## What's Next?

Now that QMD is installed, let's add your first collection of documents!
