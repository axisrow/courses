---
title: "Контрибьюция в репозиторий Anthropic"
weight: 5
bookToc: true
---

# Контрибьюция в Anthropic

## Введение

Репозиторий `anthropics/skills` — открытый проект. Вы можете внести свой вклад, добавив навыки или улучшив существующие.

## Процесс контрибьюции

### Шаг 1: Fork репозитория

```bash
# На GitHub нажмите Fork
git clone https://github.com/YOUR-USERNAME/skills.git
cd skills
```

### Шаг 2: Создайте навык

```bash
mkdir skills/my-new-skill
```

Следуйте формату:
```
skills/my-new-skill/
├── SKILL.md
├── LICENSE.txt
└── scripts/         # если нужны
```

### Шаг 3: Следуйте стандартам

- Используйте шаблон из `template/SKILL.md`
- Добавьте `LICENSE.txt` (Apache 2.0)
- Напишите понятное описание на английском
- Протестируйте навык

### Шаг 4: Pull Request

```bash
git checkout -b add-my-skill
git add .
git commit -m "Add my-new-skill"
git push origin add-my-skill
```

Создайте Pull Request на GitHub с описанием:
- Что делает навык
- Примеры использования
- Результаты тестирования

## Улучшение существующих навыков

Не обязательно создавать новый навык. Можно улучшить существующие:

- Исправить ошибки в инструкциях
- Добавить примеры
- Улучшить описание
- Обновить скрипты

## Стандарт Agent Skills

Вы также можете внести вклад в стандарт Agent Skills на [agentskills.io](https://agentskills.io).

## Итоги

- Репозиторий Anthropic открыт для контрибьюций
- Используйте стандартный процесс: Fork → Branch → PR
- Следуйте формату шаблона
- Можно улучшать существующие навыки
- Стандарт Agent Skills тоже открыт для вкладов
