---
title: "Последовательности и тайминг"
weight: 7
bookToc: true
---

# Последовательности и тайминг

Настоящие видео состоят из нескольких сцен. Компонент `<Sequence>` позволяет расположить их на временной шкале.

## Что такое Sequence?

Sequence — это часть видео, которая начинается с определённого кадра. Представьте клипы на таймлайне.

```tsx
import { Sequence } from "remotion";

export const MyVideo = () => {
  return (
    <>
      <Sequence from={0} durationInFrames={60}>
        <TitleScreen />
      </Sequence>
      <Sequence from={60} durationInFrames={90}>
        <MainContent />
      </Sequence>
      <Sequence from={150} durationInFrames={60}>
        <EndScreen />
      </Sequence>
    </>
  );
};
```

## Как работают Sequence

- `from`: кадр, с которого начинается последовательность
- `durationInFrames`: длительность (необязательно — без него длится до конца)
- Внутри Sequence `useCurrentFrame()` сбрасывается на 0

Это мощная возможность! Анимации каждой сцены начинаются с 0 — сцены можно создавать независимо.

## Именование

Добавьте `name` для наглядности на таймлайне:

```tsx
<Sequence name="Титульный экран" from={0} durationInFrames={60}>
```

## Перекрытие

Sequence могут перекрываться — удобно для переходов:

```tsx
<Sequence from={0} durationInFrames={60}>
  <Scene1 />
</Sequence>
<Sequence from={50} durationInFrames={60}>
  <Scene2 />
</Sequence>
```

Кадры 50–59 показывают обе сцены одновременно.

## Итог

Sequence организуют видео в секции с таймингом. Каждая последовательность получает свой локальный таймлайн.
