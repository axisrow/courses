---
title: "Установка RAPTOR"
weight: 3
bookToc: true
---

## Установка RAPTOR

### Требования

Перед началом вам нужно:

- Компьютер с Linux или macOS (Windows работает через WSL)
- Установленный **Claude Code** (скачайте с https://claude.ai/download)
- **API-ключ Anthropic** для AI-анализа
- **Git** для скачивания кода

### Пошаговая установка

#### Вариант 1: Ручная установка

```bash
# Скачайте RAPTOR
git clone https://github.com/gadievron/raptor.git
cd raptor

# Запустите Claude Code
claude

# Внутри Claude установите зависимости
"Install dependencies from requirements.txt"
"Install semgrep"
"Set my ANTHROPIC_API_KEY to ВАШ_КЛЮЧ"
```

#### Вариант 2: DevContainer (рекомендуется для начинающих)

DevContainer поставляется со всем предустановленным. Откройте папку RAPTOR в VS Code и выберите **Dev Container: Open Folder in Container**.

Или соберите вручную:

```bash
docker build -f .devcontainer/Dockerfile -t raptor-devcontainer:latest .
```

### Что устанавливается?

- **Semgrep** — движок статического анализа
- **CodeQL** — семантический анализ от GitHub
- **AFL++** — инструмент фаззинга
- **rr debugger** — отладчик с записью и воспроизведением

### Главный вывод

Проще всего начать с DevContainer — он сам установит все зависимости. Если предпочитаете ручную настройку, следуйте инструкциям выше.
