---
title: "Пользовательские компоненты и переиспользование"
weight: 13
bookToc: true
---

# Пользовательские компоненты и переиспользование

По мере роста проектов вам нужны хорошо организованные, переиспользуемые компоненты.

## Архитектура компонентов

Организуйте проект так:

```
src/
  components/
    Title.tsx
    Subtitle.tsx
    Background.tsx
    Transitions/
      FadeIn.tsx
      SlideIn.tsx
  scenes/
    Intro.tsx
    MainContent.tsx
    Outro.tsx
  Root.tsx
```

## Переиспользуемый компонент Fade

```tsx
import { interpolate, useCurrentFrame } from "remotion";

type FadeProps = {
  children: React.ReactNode;
  durationInFrames?: number;
  direction?: "in" | "out";
};

export const Fade: React.FC<FadeProps> = ({
  children,
  durationInFrames = 30,
  direction = "in",
}) => {
  const frame = useCurrentFrame();
  const opacity = interpolate(
    frame,
    [0, durationInFrames],
    direction === "in" ? [0, 1] : [1, 0],
    { extrapolateRight: "clamp" }
  );

  return <div style={{ opacity }}>{children}</div>;
};
```

## Использование

```tsx
<Sequence from={0} durationInFrames={60}>
  <Fade>
    <Title text="Добро пожаловать" />
  </Fade>
</Sequence>
```

## AbsoluteFill для слоёв

```tsx
import { AbsoluteFill } from "remotion";

export const Scene = () => (
  <AbsoluteFill>
    <AbsoluteFill style={{ backgroundColor: "black" }} />
    <AbsoluteFill style={{ justifyContent: "center", alignItems: "center" }}>
      <h1>Привет</h1>
    </AbsoluteFill>
  </AbsoluteFill>
);
```

Несколько `AbsoluteFill` накладываются друг на друга.

## Советы

- Компоненты — для одной задачи
- Принимайте параметры для кастомизации
- Используйте TypeScript для типобезопасности
- Выносите магические числа в константы

## Итог

Создавайте переиспользуемые компоненты с параметрами и используйте `AbsoluteFill` для слоёв.
