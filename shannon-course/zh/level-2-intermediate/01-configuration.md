---
title: "配置Shannon"
weight: 1
bookToc: true
---

# 配置Shannon

## 简介

Shannon可以在没有配置文件的情况下运行，但对于真实应用，您需要配置——特别是让Shannon能够登录并测试受保护的页面。

## 创建配置文件

```bash
cp configs/example-config.yaml configs/my-app-config.yaml
```

## 配置结构

### 身份验证

```yaml
authentication:
  login_type: form
  login_url: "https://your-app.com/login"
  credentials:
    username: "test@example.com"
    password: "yourpassword"
    totp_secret: "LB2E2RX7XFHSTGCK"  # 可选，用于2FA

  login_flow:
    - "Type $username into the email field"
    - "Type $password into the password field"
    - "Click the 'Sign In' button"

  success_condition:
    type: url_contains
    value: "/dashboard"
```

- `login_flow` — AI登录的分步指令
- `totp_secret` — Shannon自动生成2FA的TOTP代码

### 扫描规则

```yaml
rules:
  avoid:
    - description: "不测试登出功能"
      type: path
      url_path: "/logout"
  focus:
    - description: "重点测试API端点"
      type: path
      url_path: "/api"
```

## 使用配置运行

```bash
./shannon start URL=https://your-app.com REPO=my-app CONFIG=./configs/my-app-config.yaml
```

## 总结

- 配置让Shannon能测试受保护的区域
- YAML文件包含登录凭据和扫描规则
- 开箱即用支持2FA/TOTP
- `avoid`和`focus`规则控制扫描优先级
