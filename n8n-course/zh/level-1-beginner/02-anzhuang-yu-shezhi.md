---
title: "安装与设置"
weight: 2
bookToc: true
---

# 安装与设置

## 前提条件

- Windows、macOS 或 Linux 电脑
- **Node.js**（18 或更新版本）
- 基本的终端操作知识

## 方式一：npm 安装

```bash
npm install n8n -g
```

启动：

```bash
n8n start
```

在浏览器中打开 `http://localhost:5678`。

## 方式二：Docker

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

## 方式三：n8n Cloud

不想安装？使用 [n8n Cloud](https://n8n.io/cloud/)——几秒即可使用的云版本。

## 首次启动

首次打开 n8n 时：

1. 创建**管理员账户**（邮箱和密码）
2. 看到**工作流编辑器**——构建自动化的画布
3. 左侧是**节点面板**——所有可用节点

## 界面介绍

- **画布** — 拖拽和连接节点的主区域
- **节点面板** — 搜索和添加节点（点击 `+`）
- **执行列表** — 查看历史运行记录
- **设置** — 配置 n8n 选项

## 验证安装

1. 点击画布上的 `+`
2. 搜索 "Manual Trigger" 并添加
3. 添加 "Set" 节点并连接
4. 点击 **Execute Workflow**

看到绿色对勾表示一切正常！

## 小结

n8n 已安装并运行。下一课将创建你的第一个工作流。
