---
title: "多文件编辑"
weight: 8
bookToc: true
---

# 多文件编辑

## 为什么需要多文件？

真实项目有很多文件。添加功能时，通常需要同时修改多个文件。Windsurf 理解这一点。

## Cascade 如何处理多文件

Cascade 可以：

1. **读取**相关文件以理解上下文
2. **编辑**多个文件
3. **创建**新文件
4. 分别**显示 diff**

## 示例：添加新 API 端点

向 Cascade 提示：
```
添加 GET /api/users/:id 端点，从数据库返回用户数据
```

Cascade 可能修改：
- `routes/users.js` — 添加路由
- `controllers/userController.js` — 添加处理器
- `models/user.js` — 验证模型
- `tests/users.test.js` — 添加测试

## 审查多文件更改

1. Cascade 显示受影响的文件列表
2. 点击每个文件查看 diff
3. 逐文件接受或拒绝更改
4. 也可以一次全部接受

## 多文件提示技巧

- **说明架构**："使用 MVC 模式，添加..."
- **引用具体文件**："更新 `config.js` 和 `server.js`..."
- **描述完整功能**：上下文越多越好

## 限制

- Cascade 读取已打开和相邻的文件
- 大型项目需要指向具体文件夹
- 二进制文件（图片等）会跳过

## 练习

让 Cascade 添加一个完整功能（如用户注册），观察它如何修改多个文件。
