---
title: "Видео на основе данных"
weight: 11
bookToc: true
---

# Видео на основе данных

Продвинутые проекты на Remotion часто берут данные из API и баз данных для автоматической генерации видео.

## Получение данных

Используйте `calculateMetadata()` для загрузки данных перед рендерингом:

```tsx
import { CalculateMetadataFunction } from "remotion";

const calculateMetadata: CalculateMetadataFunction<Props> = async () => {
  const response = await fetch("https://api.example.com/data");
  const data = await response.json();

  return {
    props: { data },
    durationInFrames: data.items.length * 30,
  };
};
```

## Динамическая длительность

Обратите внимание: длительность зависит от данных. 10 элементов по 30 кадров = 300 кадров.

## delayRender

Для загрузки данных внутри компонентов используйте `delayRender()`:

```tsx
import { delayRender, continueRender } from "remotion";

const [data, setData] = useState(null);
const [handle] = useState(() => delayRender());

useEffect(() => {
  fetch("https://api.example.com/stats")
    .then((r) => r.json())
    .then((d) => {
      setData(d);
      continueRender(handle);
    });
}, [handle]);
```

`delayRender()` говорит Remotion: «Подожди, я ещё не готов». Когда данные получены, `continueRender()` сообщает: «Можно продолжать».

## Реальные примеры

- **GitHub Unwrapped**: видео-итоги года из данных GitHub
- **Дашборды продаж**: еженедельные видеоотчёты
- **Соцсети**: автоматические подборки

## Обработка ошибок

Всегда обрабатывайте ошибки:

```tsx
fetch(url)
  .then(...)
  .catch((err) => {
    cancelRender(err);
  });
```

## Итог

Используйте `calculateMetadata()` для предварительной загрузки и `delayRender()`/`continueRender()` для загрузки в компонентах.
