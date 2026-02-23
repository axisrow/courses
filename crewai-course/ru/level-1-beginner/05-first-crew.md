---
title: "Ваша первая команда"
weight: 5
bookToc: true
---

# Ваша первая команда

## Собираем всё вместе

Вы знаете агентов и задачи. Теперь соберём полноценную команду (Crew).

## Класс Crew

```python
from crewai import Crew, Process

crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    process=Process.sequential,
    verbose=True
)
```

## Полный пример

```python
from crewai import Agent, Task, Crew, Process

# Агенты
researcher = Agent(
    role="Технический исследователь",
    goal="Найти точную информацию о CrewAI",
    backstory="Вы — AI-исследователь, который внимательно читает документацию."
)

writer = Agent(
    role="Технический писатель",
    goal="Писать понятные резюме на основе исследований",
    backstory="Вы упрощаете сложные темы для новичков."
)

# Задачи
research_task = Task(
    description="Исследуйте, что такое CrewAI и его основные функции.",
    expected_output="Список из 5 ключевых функций CrewAI.",
    agent=researcher
)

writing_task = Task(
    description="Напишите понятное резюме о CrewAI для новичков.",
    expected_output="Резюме на 300 слов простым языком.",
    agent=writer,
    context=[research_task],
    output_file="crewai_summary.md"
)

# Команда
crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    process=Process.sequential,
    verbose=True
)

# Запуск
result = crew.kickoff()
print(result)
```

## Запуск

```bash
python main.py
```

В логах вы увидите:
1. Исследователь работает над задачей
2. Автор получает результат исследования и пишет резюме
3. Финальный результат выводится и сохраняется в файл

## Что происходит внутри

1. CrewAI отправляет первую задачу исследователю
2. Агент использует LLM для выполнения задачи
3. Результат передаётся как контекст следующей задаче
4. Автор использует контекст для создания финального результата

## Частые ошибки

| Ошибка | Решение |
|--------|---------|
| Нет API-ключа | Установите `OPENAI_API_KEY` |
| Агент не назначен | Убедитесь, что у каждой задачи есть `agent` |
| Пустой результат | Сделайте `expected_output` конкретнее |

## Упражнение

Создайте команду с:
- **Исследователем**, который находит 3 факта о выбранной теме
- **Автором**, который превращает факты в короткую статью
- Запустите и проверьте результат

## Итого

Crew объединяет агентов и задачи в рабочий конвейер. Используйте `Process.sequential` для последовательного выполнения. Вызовите `crew.kickoff()` для запуска.

---

**Поздравляем!** Уровень 1 пройден. Теперь вы можете создавать базовые приложения CrewAI.
