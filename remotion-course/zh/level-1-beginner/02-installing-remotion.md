---
title: "安装 Remotion"
weight: 2
bookToc: true
---

# 安装 Remotion

在用 Remotion 创建视频之前，需要先设置你的电脑。别担心，我们一步步来。

## 第一步：安装 Node.js

Node.js 是一个让计算机运行 JavaScript 代码的程序，Remotion 需要它。

1. 访问 [nodejs.org](https://nodejs.org)
2. 下载 **LTS**（长期支持）版本
3. 运行安装程序，按提示操作

检查是否安装成功，在终端中输入：

```bash
node --version
```

你应该看到类似 `v20.11.0` 的版本号。

## 第二步：创建你的第一个项目

```bash
npx create-video@latest my-first-video
```

这条命令会下载一个入门模板。遇到问题直接按 Enter 即可。

## 第三步：启动预览

```bash
cd my-first-video
npm start
```

浏览器会打开，显示你的视频预览。

## 发生了什么？

你创建了一个包含以下内容的项目：
- 源代码文件（定义视频内容）
- 本地服务器（用于预览）
- 配置文件

## 常见问题

- **"command not found"**：确认 Node.js 已正确安装
- **下载很慢**：第一次是正常的

## 总结

安装 Remotion 只需三步：安装 Node.js、创建项目、启动预览。
