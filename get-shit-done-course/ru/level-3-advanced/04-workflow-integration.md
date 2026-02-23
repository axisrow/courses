---
title: "Интеграция в рабочий процесс"
level: 3
lesson: 4
language: ru
tags: [gsd, интеграция, workflow, ci-cd]
---

# Интеграция в рабочий процесс

## Введение

GSD можно интегрировать в существующие рабочие процессы: CI/CD, Docker, командную работу.

## Инструкции

### Docker и CI

Для контейнерных окружений используйте неинтерактивную установку:

```bash
# В Dockerfile
RUN npx get-shit-done-cc --claude --global

# Если ~ не раскрывается:
CLAUDE_CONFIG_DIR=/home/user/.claude npx get-shit-done-cc --global
```

### Git-стратегии для команд

Для командной работы рекомендуется стратегия `phase` или `milestone`:

```
/gsd:settings
> git.branching_strategy = phase
```

Каждая фаза создаёт ветку, merge при завершении фазы.

### Коммиты .planning/ в git

По умолчанию GSD коммитит `.planning/`. Это полезно:
- История решений
- Командная видимость
- Воспроизводимость

Отключить: `planning.commit_docs = false`.

### Безопасность

Защитите чувствительные файлы:

```json
{
  "permissions": {
    "deny": [
      "Read(.env)",
      "Read(.env.*)",
      "Read(**/*.pem)",
      "Read(**/*.key)"
    ]
  }
}
```

### Workflow для команд

```
Разработчик A: /gsd:new-project → создаёт спеку
Команда: Ревью REQUIREMENTS.md и ROADMAP.md
Разработчик A: /gsd:plan-phase 1 → создаёт планы
Разработчик B: /gsd:execute-phase 1 → выполняет
Разработчик A: /gsd:verify-work 1 → проверяет
```

## Примеры

```bash
# CI: установить и выполнить
npx get-shit-done-cc --claude --global
claude --dangerously-skip-permissions << 'EOF'
/gsd:resume-work
/gsd:execute-phase 3
EOF
```

## Итоги

- GSD работает в Docker и CI через неинтерактивную установку
- Git-стратегии phase/milestone для командной работы
- .planning/ в git даёт историю решений
- Защищайте чувствительные файлы через deny-список
