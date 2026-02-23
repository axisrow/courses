---
title: "TUI и Web UI"
weight: 2
bookToc: true
---

# TUI и Web UI

## Введение

Pi Mono включает два пакета для создания интерфейсов: **pi-tui** для терминала и **pi-web-ui** для браузера.

## Pi TUI

Библиотека для создания терминальных интерфейсов с дифференциальным рендерингом (обновляется только то, что изменилось).

### Возможности

- Безмерцательный рендеринг (CSI 2026)
- Встроенные компоненты: Text, Editor, Markdown, SelectList, Image
- Поддержка тем оформления
- Отображение изображений (Kitty/iTerm2)

### Пример

```typescript
import { TUI, Text, Editor, ProcessTerminal } from "@mariozechner/pi-tui";

const terminal = new ProcessTerminal();
const tui = new TUI(terminal);

tui.addChild(new Text("Добро пожаловать!"));
tui.start();
```

## Pi Web UI

Веб-компоненты для чат-интерфейсов на базе mini-lit и Tailwind CSS.

### Возможности

- Полный чат-интерфейс с историей и стримингом
- Поддержка вложений (PDF, DOCX, изображения)
- Артефакты (HTML, SVG, Markdown) с песочницей
- Хранение в IndexedDB

### Пример

```typescript
import { ChatPanel, AppStorage } from '@mariozechner/pi-web-ui';
import '@mariozechner/pi-web-ui/app.css';

const chatPanel = new ChatPanel();
document.body.appendChild(chatPanel);
```

## Итоги

- pi-tui — для терминальных интерфейсов
- pi-web-ui — для веб-интерфейсов
- Оба пакета хорошо интегрируются с pi-ai и pi-agent-core
