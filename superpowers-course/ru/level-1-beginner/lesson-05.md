---
title: "TDD-подход в Superpowers"
level: 1
lesson: 5
lang: ru
---

# TDD-подход в Superpowers

## Введение

Как Superpowers реализует test-driven development: RED → GREEN → REFACTOR.

## Что такое TDD

Test-Driven Development — подход, при котором **тесты пишутся до кода**:

1. **RED** — напиши тест, убедись что он падает
2. **GREEN** — напиши минимальный код, чтобы тест прошёл
3. **REFACTOR** — улучши код, не ломая тесты

## Как Superpowers применяет TDD

Superpowers **принуждает** агента следовать TDD. Навык `test-driven-development` активируется автоматически:

- Агент **не может** писать код до тестов
- Если агент написал код первым — навык заставит удалить его и начать с теста
- Каждый цикл RED-GREEN-REFACTOR завершается коммитом

## Пример цикла

### RED
```typescript
// test/calculator.test.ts
describe('Calculator', () => {
  it('should add two numbers', () => {
    const calc = new Calculator();
    expect(calc.add(2, 3)).toBe(5);
  });
});
```

Тест падает: `Calculator is not defined` ✗

### GREEN
```typescript
// src/calculator.ts
export class Calculator {
  add(a: number, b: number): number {
    return a + b;
  }
}
```

Тест проходит ✓

### REFACTOR
Код уже чистый — коммит!

## Антипаттерны

Superpowers защищает от типичных ошибок:

| Антипаттерн | Как Superpowers помогает |
|-------------|------------------------|
| Код без тестов | Не даёт писать код до тестов |
| Слишком большие шаги | Задачи по 2-5 минут |
| Пропуск RED-фазы | Требует увидеть падающий тест |
| Рефакторинг без тестов | Тесты уже есть |

## Итоги

- TDD — обязательная часть Superpowers
- Цикл RED → GREEN → REFACTOR применяется к каждой задаче
- Агент не может пропустить ни одну фазу
- Результат: надёжный код с полным покрытием тестами
