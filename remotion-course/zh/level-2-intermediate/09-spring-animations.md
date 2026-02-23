---
title: "弹簧动画"
weight: 9
bookToc: true
---

# 弹簧动画

线性动画会感觉很机械。弹簧动画模拟真实世界的物理效果，让运动更自然。

## 什么是弹簧？

现实中，弹簧松开后会弹跳。Remotion 的 `spring()` 函数创建类似的自然弹性运动。

## 基本弹簧

```tsx
import { spring, useCurrentFrame, useVideoConfig } from "remotion";

export const BounceIn = () => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();

  const scale = spring({
    frame,
    fps,
    from: 0,
    to: 1,
  });

  return (
    <div style={{ transform: `scale(${scale})` }}>
      🎉
    </div>
  );
};
```

## 弹簧配置

```tsx
const scale = spring({
  frame,
  fps,
  from: 0,
  to: 1,
  config: {
    damping: 10,     // 阻尼（越高越不弹）
    stiffness: 100,  // 刚度（运动速度）
    mass: 1,         // 质量
  },
});
```

## Spring 与 Interpolate 对比

| 特性 | `interpolate()` | `spring()` |
|---|---|---|
| 运动类型 | 线性 | 基于物理 |
| 感觉 | 机械 | 自然 |
| 弹跳 | 无 | 有 |
| 持续时间 | 固定 | 自动 |

## 延迟弹簧

```tsx
const scale = spring({
  frame: frame - 30, // 从第30帧开始
  fps,
});
```

## 总结

`spring()` 创建自然的弹性动画。通过配置 damping、stiffness 和 mass 来控制效果。
