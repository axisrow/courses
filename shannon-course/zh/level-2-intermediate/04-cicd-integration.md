---
title: "CI/CD集成"
weight: 4
bookToc: true
---

# CI/CD集成

## 简介

CI/CD（持续集成/持续部署）自动化代码的构建、测试和部署。Shannon可以成为这个过程的一部分，使每次更新都经过安全检查。

## 为什么重要

没有集成：您在想起来的时候手动运行Shannon。有集成：每个Pull Request或发布都会自动检查漏洞。

## Shannon Lite：手动/脚本化

Shannon Lite没有内置CI/CD集成，但您可以编写脚本：

```bash
#!/bin/bash
./shannon start URL=$TARGET_URL REPO=$REPO_NAME WORKSPACE=ci-$BUILD_ID
```

## Shannon Pro：原生集成

Shannon Pro提供与以下平台的原生集成：
- **GitHub Actions**
- **GitLab CI**
- **Jenkins**
- **API访问**用于编程使用
- **Jira/Linear/ServiceNow/Slack**用于工单和通知自动化

## 推荐方法

1. **起步** — 在重大更改后手动运行Shannon
2. **进阶** — 在CI/CD中为测试环境添加脚本
3. **理想** — 使用Shannon Pro实现完全自动化

> ⚠️ **永远不要**在生产环境运行Shannon！仅限测试或开发环境。

## 总结

- Shannon可以集成到CI/CD中进行自动安全检查
- Shannon Lite适用于手动和脚本化运行
- Shannon Pro提供与主要CI/CD平台的原生集成
- 安全成为开发流程的一部分
