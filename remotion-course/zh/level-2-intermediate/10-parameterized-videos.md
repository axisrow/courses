---
title: "参数化视频"
weight: 10
bookToc: true
---

# 参数化视频

Remotion 的超能力之一是使用参数从同一模板创建不同的视频。

## 什么是输入参数？

输入参数是传递给视频以自定义它的数据：

- 名字："Alice" → 为 Alice 定制的生日视频
- 名字："Bob" → 同一模板，不同结果

## 定义 Schema

```tsx
import { z } from "zod";

const mySchema = z.object({
  name: z.string(),
  color: z.string(),
});
```

## 在合成中使用参数

```tsx
export const RemotionRoot = () => {
  return (
    <Composition
      id="Greeting"
      component={Greeting}
      schema={mySchema}
      defaultProps={{
        name: "世界",
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

## 在组件中访问参数

```tsx
const Greeting: React.FC<z.infer<typeof mySchema>> = ({ name, color }) => {
  return (
    <div style={{ color, fontSize: 80 }}>
      你好, {name}!
    </div>
  );
};
```

## 使用自定义参数渲染

```bash
npx remotion render Greeting out/alice.mp4 \
  --props='{"name": "Alice", "color": "red"}'
```

## 批量渲染

结合脚本渲染数百个个性化视频：

```bash
for name in Alice Bob Charlie; do
  npx remotion render Greeting "out/${name}.mp4" \
    --props="{\"name\": \"${name}\", \"color\": \"blue\"}"
done
```

## 总结

输入参数让你创建视频模板并生成个性化变体。定义 schema，传递参数，渲染多个版本。
