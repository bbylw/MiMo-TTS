# 🎙️ MiMo TTS - 智能语音合成

基于小米米墨 **MiMo‑V2.5‑TTS** 的在线语音合成工具（纯静态页面），支持官方内置音色、格式选择与风格标签控制。

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Deploy-brightgreen)](https://pages.github.com/)
[![Platform](https://img.shields.io/badge/Platform-Xiaomi%20MiMo-blue)](https://platform.xiaomimimo.com)

## ✨ 已对齐 v2.5 文档的能力

- 使用模型：`mimo-v2.5-tts`
- 请求头使用：`api-key: <YOUR_KEY>`
- 支持官方内置音色（示例中已内置 `mimo_default / 冰糖 / 茉莉 / Mia / Milo`）
- 风格控制使用 `(<风格>)文本` 标签方式（例如 `(开心)今天真是太棒了！`）
- 支持 `WAV / MP3 / PCM16` 输出格式
- 新增唱歌风格入口：`(唱歌)`

> 参考文档：<https://platform.xiaomimimo.com/docs/usage-guide/speech-synthesis-v2.5>

## 🚀 使用方式

### 在线使用
访问你部署后的 GitHub Pages 地址即可。

### 本地使用
1. 克隆仓库
2. 直接用浏览器打开 `index.html`
3. 输入小米米墨 API Key 后即可调用

## 🔐 安全说明

- API Key 仅存储在浏览器 `localStorage`
- 前端直连小米米墨接口，不经过中间服务器

## 🔧 核心请求示例

```json
{
  "model": "mimo-v2.5-tts",
  "messages": [
    {
      "role": "user",
      "content": "请使用“开心”风格进行语音合成，保持自然表达。"
    },
    {
      "role": "assistant",
      "content": "(开心)明天就是周五了，真开心！"
    }
  ],
  "audio": {
    "format": "wav",
    "voice": "mimo_default"
  }
}
```

## 📁 项目结构

```text
MiMo-TTS/
├── index.html
└── README.md
```

## 🔗 相关链接

- 小米米墨开放平台：https://platform.xiaomimimo.com
- OpenAI 兼容 Chat API：https://platform.xiaomimimo.com/docs/api/chat/openai-api
- TTS v2.5 使用指南：https://platform.xiaomimimo.com/docs/usage-guide/speech-synthesis-v2.5

## 📄 许可证

MIT License
