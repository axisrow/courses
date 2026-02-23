---
title: "数据驱动视频"
weight: 11
bookToc: true
---

# 数据驱动视频

高级 Remotion 项目通常从 API 和数据库获取数据来自动生成视频。

## 获取数据

使用 `calculateMetadata()` 在渲染前获取数据：

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

## 动态时长

注意时长取决于数据。10个项目，每个30帧，视频就是300帧。

## delayRender

在组件内获取数据时，使用 `delayRender()`：

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

`delayRender()` 告诉 Remotion："等等，我还没准备好。" 数据到达后，`continueRender()` 说："好了，继续吧。"

## 实际案例

- **GitHub Unwrapped**：从 GitHub 数据生成年度回顾视频
- **销售仪表板**：每周视频报告
- **社交媒体**：自动生成精彩集锦

## 错误处理

务必处理错误：

```tsx
fetch(url)
  .then(...)
  .catch((err) => {
    cancelRender(err);
  });
```

## 总结

使用 `calculateMetadata()` 进行渲染前数据获取，`delayRender()`/`continueRender()` 用于组件内获取。务必处理错误。
