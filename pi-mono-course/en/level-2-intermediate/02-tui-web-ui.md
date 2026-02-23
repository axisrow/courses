---
title: "TUI and Web UI"
weight: 2
bookToc: true
---

# TUI and Web UI

## Introduction

Pi Mono includes two UI packages: **pi-tui** for the terminal and **pi-web-ui** for the browser.

## Pi TUI

A library for building terminal interfaces with differential rendering (only updates what changed).

### Features

- Flicker-free rendering (CSI 2026)
- Built-in components: Text, Editor, Markdown, SelectList, Image
- Theme support
- Inline images (Kitty/iTerm2)

### Example

```typescript
import { TUI, Text, Editor, ProcessTerminal } from "@mariozechner/pi-tui";

const terminal = new ProcessTerminal();
const tui = new TUI(terminal);

tui.addChild(new Text("Welcome!"));
tui.start();
```

## Pi Web UI

Web components for chat interfaces built with mini-lit and Tailwind CSS.

### Features

- Complete chat UI with history and streaming
- Attachments (PDF, DOCX, images)
- Artifacts (HTML, SVG, Markdown) with sandboxing
- IndexedDB storage

### Example

```typescript
import { ChatPanel, AppStorage } from '@mariozechner/pi-web-ui';
import '@mariozechner/pi-web-ui/app.css';

const chatPanel = new ChatPanel();
document.body.appendChild(chatPanel);
```

## Summary

- pi-tui — for terminal interfaces
- pi-web-ui — for web interfaces
- Both integrate well with pi-ai and pi-agent-core
