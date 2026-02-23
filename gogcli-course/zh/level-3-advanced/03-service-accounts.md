---
title: "服务账户"
weight: 13
bookToc: true
---

# 服务账户

服务账户是用于自动化的特殊 Google 账户，无需用户交互登录。

## 使用场景

- 服务器端脚本
- Google Workspace 组织数据处理
- CI/CD 流水线

## 设置

### 1. 在 Google Cloud Console 创建服务账户

下载 JSON 密钥文件，安全保存。

### 2. 在 gogcli 中认证

```bash
gog auth service --key-file /path/to/service-key.json
gog auth service --key-file key.json --subject admin@company.com
```

`--subject` 用于 Google Workspace 的身份委派。

### 3. 使用

```bash
gog --account service:my-service mail list
gog -a service:my-service drive list
```

## 身份委派

管理员可以允许服务账户代表用户操作：

```bash
gog auth service --key-file key.json --subject user@company.com
gog mail list  # 查看 user@company.com 的邮件
```

## 安全注意事项

- 密钥文件不要提交到 git
- 使用最小权限
- 定期轮换密钥

## 练习

1. 创建服务账户并下载密钥
2. 用 gogcli 进行服务账户认证
3. 通过服务账户列出云端硬盘文件
