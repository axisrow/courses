---
title: "Добавление аудио и изображений"
weight: 8
bookToc: true
---

# Добавление аудио и изображений

Видео — это не только текст. Давайте добавим аудио и изображения.

## Добавление изображений

Поместите изображения в папку `public` проекта и используйте их:

```tsx
import { Img, staticFile } from "remotion";

export const MyScene = () => {
  return <Img src={staticFile("photo.jpg")} />;
};
```

`staticFile()` указывает на файлы в папке `public`. Используйте компонент `<Img>` (не HTML `<img>`) — он ждёт загрузки изображения перед рендерингом.

## Добавление аудио

```tsx
import { Audio, staticFile } from "remotion";

export const MyScene = () => {
  return (
    <>
      <Audio src={staticFile("music.mp3")} />
      <div>Визуальный контент</div>
    </>
  );
};
```

## Управление громкостью

```tsx
<Audio
  src={staticFile("music.mp3")}
  volume={(f) =>
    interpolate(f, [0, 30], [0, 1], {
      extrapolateRight: "clamp",
    })
  }
/>
```

Звук плавно нарастает за 30 кадров.

## Аудио в Sequence

Аудио внутри `<Sequence>` воспроизводится только в этом интервале:

```tsx
<Sequence from={60} durationInFrames={120}>
  <Audio src={staticFile("narration.mp3")} />
</Sequence>
```

## Удалённые URL

Можно использовать ссылки:

```tsx
<Img src="https://example.com/photo.jpg" />
<Audio src="https://example.com/music.mp3" />
```

## Итог

Используйте `<Img>` для изображений и `<Audio>` для звука. Оба работают с локальными файлами (через `staticFile()`) и удалёнными URL.
