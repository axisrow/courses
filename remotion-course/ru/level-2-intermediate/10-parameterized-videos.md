---
title: "Параметризованные видео"
weight: 10
bookToc: true
---

# Параметризованные видео

Одна из суперспособностей Remotion — создание разных видео из одного шаблона с помощью параметров.

## Что такое входные параметры?

Входные параметры — это данные, которые вы передаёте видео для его кастомизации:

- Имя: «Алиса» → персональное поздравление для Алисы
- Имя: «Борис» → тот же шаблон, другой результат

## Определение схемы

```tsx
import { z } from "zod";

const mySchema = z.object({
  name: z.string(),
  color: z.string(),
});
```

## Использование в композиции

```tsx
export const RemotionRoot = () => {
  return (
    <Composition
      id="Greeting"
      component={Greeting}
      schema={mySchema}
      defaultProps={{
        name: "Мир",
        color: "blue",
      }}
      durationInFrames={150}
      fps={30}
      width={1920}
      height={1080}
    />
  );
};
```

## Доступ к параметрам в компоненте

```tsx
const Greeting: React.FC<z.infer<typeof mySchema>> = ({ name, color }) => {
  return (
    <div style={{ color, fontSize: 80 }}>
      Привет, {name}!
    </div>
  );
};
```

## Рендеринг с параметрами

```bash
npx remotion render Greeting out/alice.mp4 \
  --props='{"name": "Алиса", "color": "red"}'
```

## Пакетный рендеринг

Скомбинируйте со скриптом для создания сотен видео:

```bash
for name in Алиса Борис Виктор; do
  npx remotion render Greeting "out/${name}.mp4" \
    --props="{\"name\": \"${name}\", \"color\": \"blue\"}"
done
```

## Итог

Входные параметры позволяют создавать шаблоны и генерировать персонализированные вариации.
