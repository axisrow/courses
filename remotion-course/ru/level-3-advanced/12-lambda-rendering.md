---
title: "Серверный рендеринг с Remotion Lambda"
weight: 12
bookToc: true
---

# Серверный рендеринг с Remotion Lambda

Remotion Lambda позволяет рендерить видео в облаке AWS, используя массивный параллелизм.

## Зачем Lambda?

- **Скорость**: 5-минутное видео за секунды благодаря распределению по функциям
- **Масштаб**: тысячи видео одновременно
- **Стоимость**: платите только за использованное время

## Как это работает

1. Код видео упаковывается и загружается в S3
2. Lambda-функция вызывается для каждого блока кадров
3. Блоки склеиваются в финальное видео
4. Результат сохраняется в S3

## Настройка

```bash
npx remotion lambda policies role
npx remotion lambda sites create src/index.ts
npx remotion lambda functions deploy
```

## Рендеринг через CLI

```bash
npx remotion lambda render \
  <site-url> \
  MyVideo \
  --props='{"name": "Алиса"}'
```

## Рендеринг через API

```tsx
import { renderMediaOnLambda } from "@remotion/lambda/client";

const result = await renderMediaOnLambda({
  region: "us-east-1",
  functionName: "remotion-render",
  serveUrl: siteUrl,
  composition: "MyVideo",
  inputProps: { name: "Алиса" },
  codec: "h264",
});

console.log(result.outputUrl);
```

## Оптимизация стоимости

- Используйте меньшее разрешение для черновиков
- Выставляйте подходящий объём памяти (1769 МБ — хорошее значение)
- Регулярно удаляйте старые сайты и функции

## Альтернативы

Remotion также поддерживает:
- **Cloud Run** (Google Cloud)
- **Свои серверы** с `@remotion/renderer`

## Итог

Remotion Lambda распределяет рендеринг по многим функциям AWS для скорости и масштаба.
