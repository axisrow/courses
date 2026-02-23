---
title: "多账户与别名"
weight: 11
bookToc: true
---

# 多账户与别名

## 添加账户

```bash
gog auth add personal@gmail.com
gog auth add work@company.com
```

## 切换账户

```bash
gog --account work@company.com mail list
gog -a personal@gmail.com drive list
```

### 设置默认账户

```bash
gog auth default work@company.com
gog auth list
```

## 别名

为账户创建简短名称：

```bash
gog auth alias work work@company.com
gog auth alias home personal@gmail.com
```

使用别名：

```bash
gog -a work mail list
gog -a home drive list
```

## 每个账户单独配置

```bash
gog config set --account work default_format json
gog config set --account home default_format table
```

## 练习

1. 添加两个 Google 账户
2. 为它们创建别名
3. 用工作账户给个人账户发邮件
