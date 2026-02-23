---
title: "为DeerFlow做贡献"
weight: 5
bookToc: true
---

# 为DeerFlow做贡献

## 简介

DeerFlow是一个开源项目，欢迎社区贡献！在本课中，我们将介绍如何设置开发环境、进行更改和提交Pull Request。

## 开发环境设置

### 通过Docker（推荐）

```bash
git clone https://github.com/YOUR-USERNAME/deer-flow.git
cd deer-flow
cp config.example.yaml config.yaml
cp extensions_config.example.json extensions_config.json
export OPENAI_API_KEY="your-key"
make docker-init
make docker-start
```

所有服务都支持热重载——代码更改自动生效。

### 本地开发

```bash
make check    # Node.js 22+, pnpm, uv, nginx
make install
make dev
```

## 代码风格

- **Python：** ruff代码检查/格式化，240字符行长，Python 3.12+带类型提示
- **测试：** pytest

```bash
cd backend
make lint      # 检查
make format    # 自动格式化
pytest tests/  # 运行测试
```

## 贡献流程

1. **创建Issue** — 描述您想更改什么以及为什么
2. **创建分支** — `feature/my-feature`或`fix/my-bugfix`
3. **进行更改** — 编写测试，遵循代码风格，更新文档
4. **验证** — 检查代码、运行测试、确保应用启动
5. **提交并推送** — `git commit -m "feat: add my new feature"`
6. **创建Pull Request** — 描述做了什么以及如何测试

## 可以贡献什么

- **技能** — 最简单的方式；在`skills/public/`中创建`SKILL.md`
- **社区工具** — `backend/src/community/`中的新集成
- **文档** — 修复、翻译、示例
- **Bug修复** — 在GitHub上查找`good first issue`标签

## 重要规则

1. 代码更改后始终更新文档
2. 为新功能编写测试
3. 遵循现有代码风格
4. 小PR比大PR好
5. 您的代码将遵循MIT许可证

🎉 恭喜！您已完成整个DeerFlow课程。现在您知道如何使用、配置和扩展这个强大的超级智能体平台！
