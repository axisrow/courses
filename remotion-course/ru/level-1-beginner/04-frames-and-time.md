---
title: "Кадры и время"
weight: 4
bookToc: true
---

# Кадры и время

Любое видео — это серия неподвижных картинок, показываемых очень быстро. Remotion даёт вам контроль над каждой из них.

## Что такое кадр?

Кадр — это одно изображение. Когда много кадров показываются друг за другом (как в книжке-раскладушке), вы видите движение.

## Хук useCurrentFrame

Remotion предоставляет функцию `useCurrentFrame()`, которая сообщает компоненту, какой кадр сейчас отображается.

```tsx
import { useCurrentFrame } from "remotion";

export const Counter = () => {
  const frame = useCurrentFrame();
  return (
    <div style={{ fontSize: 80, textAlign: "center" }}>
      Кадр: {frame}
    </div>
  );
};
```

При 30 fps счётчик идёт от 0 до 149 за 5 секунд.

## Перевод кадров в секунды

Формула простая:

```
секунды = кадр / fps
```

При 30 fps кадр 90 = 3 секунды от начала.

## Хук useVideoConfig

Чтобы узнать настройки видео внутри компонента:

```tsx
import { useVideoConfig } from "remotion";

const { fps, width, height, durationInFrames } = useVideoConfig();
```

## Попробуйте сами

Создайте компонент с прогресс-баром, который заполняется по мере воспроизведения:

```tsx
const frame = useCurrentFrame();
const { durationInFrames } = useVideoConfig();
const progress = frame / durationInFrames;
```

## Итог

Кадры — строительные блоки видео. `useCurrentFrame()` сообщает текущий кадр, `useVideoConfig()` — свойства видео.
