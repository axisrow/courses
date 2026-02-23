---
title: "CI/CD 与 GitHub"
weight: 14
bookToc: true
---

# CI/CD 与 GitHub

将项目连接到 GitHub 并自动化部署。

## 导出到 GitHub

1. 点击 **Export to GitHub**。
2. Lovable 创建一个包含所有代码的 GitHub 仓库。
3. 每次更改自动同步到 GitHub。

## GitHub 同步

- Lovable 在每次更改时推送提交。
- 你可以克隆仓库在本地工作。
- 推送回去——Lovable 会同步更改。

## 本地开发

```bash
git clone https://github.com/your-user/your-app.git
cd your-app
npm install
npm run dev
```

## 用 Vercel 部署

1. 将 GitHub 仓库连接到 [Vercel](https://vercel.com)。
2. Vercel 在每次推送时自动部署。
3. Pull request 的预览部署。

## 用 Netlify 部署

1. 将仓库连接到 [Netlify](https://netlify.com)。
2. 构建命令：`npm run build`。
3. 输出目录：`dist`。

## GitHub Actions

```yaml
name: Build
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm install
      - run: npm run build
```

## 分支策略

| 分支 | 用途 |
|------|------|
| main | 生产代码 |
| develop | 集成分支 |
| feature/* | 新功能 |

## 总结

导出到 GitHub 进行版本控制。用 Vercel 或 Netlify 部署。用 GitHub Actions 实现 CI/CD 自动化。
