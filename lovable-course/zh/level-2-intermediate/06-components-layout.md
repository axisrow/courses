---
title: "组件与布局"
weight: 6
bookToc: true
---

# 组件与布局

用可复用组件构建复杂界面。

## 什么是组件？

组件是构建块：按钮、卡片、导航栏。Lovable 自动生成 React 组件。

## 通过提示词创建

> 创建一个可复用的卡片组件，包含图片、标题、描述和「了解更多」按钮。

AI 会创建单独的组件文件。

## 多页面应用

> 添加一个「关于」页面。在首页和关于页之间添加导航。

Lovable 会设置路由（React Router）。

## 布局模式

### 仪表盘

> 创建仪表盘：侧边导航、顶部带用户头像的标题栏、主内容区域。

### 落地页

> 创建落地页：主视觉区、功能网格、用户评价、页脚。

## shadcn/ui 组件

Lovable 使用 [shadcn/ui](https://ui.shadcn.com/)：

- Dialog、Sheet、Drawer
- Table、DataTable
- Tabs、Accordion
- Toast 通知
- 下拉菜单

示例：

> 添加一个带排序和分页的数据表格，显示用户列表。

## 代码组织

```
src/
  components/
    ui/          ← shadcn/ui 基础组件
    Header.tsx
    Sidebar.tsx
    TaskCard.tsx
  pages/
    Home.tsx
    About.tsx
```

## 总结

组件让应用有条理、可复用。Lovable 处理组件创建、路由，并使用 shadcn/ui 提供精美界面。
