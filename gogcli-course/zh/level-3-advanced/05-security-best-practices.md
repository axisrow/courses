---
title: "安全最佳实践"
weight: 15
bookToc: true
---

# 安全最佳实践

## 令牌管理

```bash
gog auth list
gog auth revoke user@gmail.com
gog auth revoke --all
```

## 最小权限

```bash
gog auth login --scopes gmail.readonly,drive.readonly
gog auth login --scopes calendar.events
```

## 配置存储

- 配置保存在 `~/.config/gog/`
- 令牌由系统 keyring 加密存储
- 不要将配置文件夹复制到其他机器

```bash
gog config path
gog auth status
```

## 脚本安全

```bash
# 不好：
export GOOGLE_TOKEN="ya29.xxxxx"

# 好：
gog auth login  # 令牌存储在 keyring 中
```

## 审计

```bash
gog auth scopes
gog auth scopes --account work
```

## 安全检查清单

- [ ] 使用最小权限范围
- [ ] 令牌存储在 keyring 中
- [ ] 服务账户密钥不在 git 仓库中
- [ ] 定期检查 `gog auth list`
- [ ] 撤销不再使用的账户访问权限

## 练习

1. 检查账户的权限范围
2. 撤销测试账户的访问权限
3. 用只读权限重新登录
