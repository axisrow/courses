---
title: "语音、通知和文件"
weight: 9
bookToc: true
---

# 语音、通知和文件

## 语音聊天

- **语音转文字** — 由 **Deepgram** 提供。实时转录你的语音。
- **文字转语音** — 由 **ElevenLabs** 提供。Sentient 用自然的声音朗读回复。

### 设置方法

1. 在服务器 `.env` 文件中添加 Deepgram API 密钥。
2. 在服务器 `.env` 文件中添加 ElevenLabs API 密钥。
3. 在聊天界面点击麦克风图标。

## 推送通知

Sentient 可以通过 **Web Push**（`pywebpush` 库）发送浏览器推送通知：
- 后台任务完成时。
- 触发任务触发时。
- Sentient 有主动建议时。

Service worker（`sw.js`）即使关闭标签页也能接收推送消息。

## 文件处理

你可以在对话中上传文件：
- 上传 PDF 请 Sentient 总结。
- 上传电子表格请求分析。
- 请 Sentient 创建图表（通过 **QuickChart**）并下载。

## 小结

语音让 Sentient 解放双手，通知让你随时掌握信息，文件处理扩展了对话的可能性。
