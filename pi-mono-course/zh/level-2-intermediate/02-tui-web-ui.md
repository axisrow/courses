---
title: "TUI 和 Web UI"
weight: 2
bookToc: true
---

# TUI 和 Web UI

## 简介

Pi Mono 包含两个 UI 包：**pi-tui** 用于终端，**pi-web-ui** 用于浏览器。

## Pi TUI

用于构建终端界面的库，支持差异化渲染（只更新变化的部分）。

### 功能

- 无闪烁渲染（CSI 2026）
- 内置组件：Text、Editor、Markdown、SelectList、Image
- 主题支持
- 内联图像（Kitty/iTerm2）

### 示例

```typescript
import { TUI, Text, Editor, ProcessTerminal } from "@mariozechner/pi-tui";

const terminal = new ProcessTerminal();
const tui = new TUI(terminal);

tui.addChild(new Text("欢迎！"));
tui.start();
```

## Pi Web UI

基于 mini-lit 和 Tailwind CSS 的聊天界面 Web 组件。

### 功能

- 完整的聊天 UI，支持历史和流式传输
- 附件（PDF、DOCX、图像）
- 工件（HTML、SVG、Markdown）带沙箱
- IndexedDB 存储

### 示例

```typescript
import { ChatPanel, AppStorage } from '@mariozechner/pi-web-ui';
import '@mariozechner/pi-web-ui/app.css';

const chatPanel = new ChatPanel();
document.body.appendChild(chatPanel);
```

## 总结

- pi-tui — 用于终端界面
- pi-web-ui — 用于 Web 界面
- 两者都与 pi-ai 和 pi-agent-core 良好集成
