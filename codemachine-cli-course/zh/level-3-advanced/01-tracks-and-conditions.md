---
title: "轨道和条件"
weight: 1
bookToc: true
---

# 轨道和条件

## 什么是轨道？

轨道让用户在启动工作流时选择项目类型：

```javascript
tracks: {
  question: '什么类型的 Web 应用？',
  options: {
    spa: { label: '单页应用', description: 'React/Vue/Angular' },
    ssr: { label: '服务端渲染', description: 'Next.js/Nuxt.js' },
    static: { label: '静态网站', description: 'HTML/CSS/JS' },
  },
},
steps: [
  resolveStep('researcher'),
  resolveStep('spa-setup', { tracks: ['spa'] }),
  resolveStep('ssr-setup', { tracks: ['ssr'] }),
  resolveStep('deployment'),
],
```

## 条件组

条件像功能开关：

```javascript
conditionGroups: [
  {
    id: 'features',
    question: '需要哪些功能？',
    multiSelect: true,
    conditions: {
      auth: { label: '身份验证' },
      payments: { label: '支付' },
      notifications: { label: '通知' },
    },
  },
],
```

## 嵌套条件

```javascript
children: {
  auth: {
    question: '什么验证方式？',
    multiSelect: false,
    conditions: {
      oauth: { label: 'OAuth（Google/GitHub）' },
      email: { label: '邮箱/密码' },
    },
  },
},
```

## 组合轨道和条件

```javascript
conditionGroups: [
  {
    id: 'database',
    question: '哪种数据库？',
    tracks: ['spa', 'ssr'],
    conditions: {
      postgres: { label: 'PostgreSQL' },
      mongodb: { label: 'MongoDB' },
    },
  },
],
```

## 总结

- 轨道用于选择项目类型
- 条件作为功能开关
- 嵌套条件用于后续问题
- 步骤可按轨道和条件过滤

> **下一课：** 上下文工程。
