---
title: "Hash-Anchored Edits (Hashline)"
level: 2
lesson: 1
lang: en
tags: [hashline, editing, hashes]
---

# Hash-Anchored Edits (Hashline)

## Introduction

Hashline is one of OMP's key innovations. Every line in a file gets a short content-hash anchor. The model references anchors instead of reproducing text.

## The Problem

With traditional approaches (str_replace), the model must exactly reproduce original text for replacement. This often fails:

- Extra/missing whitespace
- "String not found"
- Ambiguous matches

## How Hashline Works

1. When reading a file, each line gets a short hash (e.g., `#a3f`)
2. The model specifies a range of hashes to edit
3. If the file changed since last read — hashes won't match and the edit is rejected **before** corruption

## Benchmark Results

- **Grok Code Fast 1**: 6.7% → 68.3% — a tenfold improvement
- **Gemini 3 Flash**: +5pp over str_replace
- **Grok 4 Fast**: 61% fewer output tokens
- **MiniMax**: more than doubled success rate

## Usage Example

Just work normally — hashline is active by default:

```
> Add error handling to the parseConfig function in src/config.ts
```

The model reads the file, sees hash anchors, and makes a precise edit.

## Summary

Hashline eliminates typical text editing problems, making AI file edits reliable.
