---
title: "创建自定义攻击"
weight: 2
bookToc: true
---

# 创建自定义攻击

## 简介

Shannon使用AI智能体进行攻击，所以"自定义攻击"意味着通过配置控制智能体行为。

## Focus和Avoid规则

```yaml
rules:
  focus:
    - description: "仅测试API v2"
      type: path
      url_path: "/api/v2"
  avoid:
    - description: "不要触碰支付系统"
      type: path
      url_path: "/payment"
```

## 自定义登录流程

对于复杂的登录场景，描述每个步骤：

```yaml
authentication:
  login_flow:
    - "导航到登录页面"
    - "点击'使用SSO登录'"
    - "在企业邮箱字段中输入$username"
    - "点击'下一步'"
    - "在密码字段中输入$password"
    - "在验证字段中输入TOTP代码"
    - "点击'验证'"
```

## 测试多种角色

为不同角色创建单独的配置：

```bash
./shannon start URL=https://app.com REPO=app CONFIG=./configs/user-config.yaml
./shannon start URL=https://app.com REPO=app CONFIG=./configs/admin-config.yaml
```

比较结果可以发现权限提升问题。

## 多仓库设置

```bash
mkdir ./repos/platform
cd ./repos/platform
git clone frontend-repo
git clone auth-service-repo
git clone api-gateway-repo
```

## 限制

Shannon Lite不允许在不修改源代码的情况下添加新的漏洞类别或自定义智能体（AGPL允许内部使用时修改）。

## 总结

- 自定义攻击通过YAML配置管理
- Focus和Avoid规则控制扫描优先级
- 复杂的登录流程用自然语言描述
- 测试不同角色可发现授权问题
