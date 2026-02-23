---
title: "Интеграция с CI/CD"
weight: 4
bookToc: true
---

# Интеграция с CI/CD

## Введение

CI/CD (Continuous Integration / Continuous Deployment) — это автоматический процесс сборки, тестирования и развёртывания кода. Shannon можно встроить в этот процесс, чтобы каждое обновление проверялось на безопасность.

## Зачем это нужно

Без интеграции: вы запускаете Shannon вручную, когда вспомните. С интеграцией: каждый pull request или релиз автоматически проверяется на уязвимости.

## Shannon Lite: ручной запуск

Shannon Lite не имеет встроенной CI/CD интеграции, но его можно запустить из скрипта:

```bash
#!/bin/bash
# simple-security-check.sh

# Запустить Shannon
./shannon start URL=$TARGET_URL REPO=$REPO_NAME WORKSPACE=ci-$BUILD_ID

# Дождаться завершения (проверяя логи)
# Проверить результат
```

## Shannon Pro: нативная интеграция

Shannon Pro предоставляет полноценную интеграцию с:

- **GitHub Actions** — автоматический запуск при push/PR
- **GitLab CI** — встроенная поддержка
- **Jenkins** — плагин для пайплайна

Также доступны:
- **API-доступ** — программный запуск и получение результатов
- **Интеграция с трекерами** — автоматическое создание тикетов в Jira, Linear, ServiceNow
- **Slack-уведомления** — оповещение команды о найденных уязвимостях

## Пример workflow с GitHub Actions (Shannon Pro)

```yaml
name: Security Test
on:
  pull_request:
    branches: [main]

jobs:
  pentest:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run Shannon
        env:
          SHANNON_API_KEY: ${{ secrets.SHANNON_API_KEY }}
        run: |
          # Shannon Pro CI/CD integration
          shannon-cli scan --url $STAGING_URL --repo .
```

## Рекомендуемый подход

1. **Для начала** — запускайте Shannon вручную после крупных изменений
2. **Далее** — добавьте скрипт в CI/CD для staging-окружения
3. **В идеале** — используйте Shannon Pro с полной автоматизацией

> ⚠️ **Никогда** не запускайте Shannon на production! Только staging или dev-окружения.

## Итоги

- Shannon можно интегрировать в CI/CD для автоматической проверки безопасности
- Shannon Lite подходит для ручного и скриптового запуска
- Shannon Pro предлагает нативную интеграцию с GitHub, GitLab, Jenkins
- Безопасность становится частью процесса разработки, а не разовым событием
