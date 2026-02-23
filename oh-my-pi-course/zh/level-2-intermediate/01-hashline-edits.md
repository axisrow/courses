---
title: "哈希锚点编辑 (Hashline)"
level: 2
lesson: 1
lang: zh
tags: [hashline, 编辑, 哈希]
---

# 哈希锚点编辑 (Hashline)

## 介绍

Hashline 是 OMP 的关键创新之一。文件中每一行都会获得一个短哈希锚点。模型引用锚点而非复制文本。

## 问题所在

传统方式（str_replace）中，模型必须精确复制原始文本进行替换，这经常失败：

- 多余/缺少空格
- "字符串未找到"
- 模糊匹配

## Hashline 工作原理

1. 读取文件时，每行获得一个短哈希（例如 `#a3f`）
2. 模型指定要编辑的哈希范围
3. 如果文件自上次读取后发生变化 — 哈希不匹配，编辑在**造成损坏之前**被拒绝

## 基准测试结果

- **Grok Code Fast 1**：6.7% → 68.3% — 十倍提升
- **Gemini 3 Flash**：比 str_replace 高 5 个百分点
- **Grok 4 Fast**：输出 token 减少 61%
- **MiniMax**：成功率翻倍以上

## 使用示例

正常工作即可 — hashline 默认启用：

```
> 为 src/config.ts 中的 parseConfig 函数添加错误处理
```

模型读取文件，看到哈希锚点，进行精确编辑。

## 总结

Hashline 消除了典型的文本编辑问题，使 AI 文件编辑变得可靠。
