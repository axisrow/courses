---
title: "自定义代码"
weight: 11
bookToc: true
---

# 自定义代码

超越提示词——直接编辑代码。

## 代码视图

在编辑器中切换到代码视图，查看和编辑生成的文件。Lovable 创建整洁的 React + TypeScript 代码。

## 何时手动编辑

- 微调 AI 没有完全正确的逻辑。
- 添加复杂的业务规则。
- 集成小众库。

## 编辑文件

你可以直接编辑任何文件。更改立即反映在预览中。

## 添加 npm 包

> 添加「date-fns」库来格式化日期。

Lovable 会添加到 `package.json` 并在需要的地方导入。

## 自定义 Hooks

> 创建一个 useLocalStorage 自定义 hook，将状态持久化到 localStorage。

## TypeScript 类型

> 为 Product 和 Order 类型添加 TypeScript 接口。

## 文件结构

```
src/
  components/     ← UI 组件
  hooks/          ← 自定义 hooks
  lib/            ← 工具函数
  pages/          ← 页面路由
  integrations/   ← Supabase 客户端
  types/          ← TypeScript 类型
```

## 提示词 + 代码

最佳工作流：
1. 大改动用提示词。
2. 小调整手动编辑。
3. AI 理解并尊重你的手动修改。

## 总结

你可以完全访问源代码。需要时直接编辑、添加包、创建自定义逻辑。Lovable 尊重你的手动更改。
