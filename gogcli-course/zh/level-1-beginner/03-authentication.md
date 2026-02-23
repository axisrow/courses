---
title: "认证"
weight: 3
bookToc: true
---

# 认证

使用 gogcli 前需要授权访问你的 Google 账户。

## 登录

```bash
gog auth login
```

这会打开浏览器，让你登录 Google 账户并授权。

## 检查状态

```bash
gog auth status
```

## 登录指定账户

```bash
gog auth login user@gmail.com
```

## 限制权限

只请求需要的权限：

```bash
gog auth login --scopes gmail.readonly
gog auth login --scopes drive,calendar
```

## 退出登录

```bash
gog auth revoke
gog auth revoke user@gmail.com
```

## 练习

1. 运行 `gog auth login` 完成授权
2. 用 `gog auth status` 确认已登录
3. 试试用只读权限登录
