# 🎙️ MiMo TTS - 智能语音合成

基于小米米墨 **MiMo‑V2.5‑TTS 系列** 的在线语音合成工具（纯静态前端）。

本项目已经按官方文档 <https://platform.xiaomimimo.com/docs/usage-guide/speech-synthesis-v2.5> 做了完整升级，覆盖：

- `mimo-v2.5-tts`（内置音色）
- `mimo-v2.5-tts-voicedesign`（文本描述设计音色）
- `mimo-v2.5-tts-voiceclone`（上传样本克隆音色）

---

## ✨ 功能总览

### 1) 三模型切换
- **mimo-v2.5-tts**：支持官方内置音色与风格标签。
- **mimo-v2.5-tts-voicedesign**：不使用内置音色，要求填写 voice design 描述（`user` 消息必填）。
- **mimo-v2.5-tts-voiceclone**：不使用内置音色，要求上传 `wav/mp3` 样本，前端自动转 Data URL（`data:...;base64,...`）。

### 2) 内置音色（v2.5，已全部补全）

| 显示名 | Voice ID | 语言 | 性别 | 说明 |
|---|---|---|---|---|
| MiMo-默认 | `mimo_default` | 跟随集群 | - | 中国集群默认对应 `冰糖`，其他集群默认对应 `Mia` |
| 冰糖 | `冰糖` | 中文 | 女 | 官方内置 |
| 茉莉 | `茉莉` | 中文 | 女 | 官方内置 |
| 苏打 | `苏打` | 中文 | 男 | 官方内置 |
| 白桦 | `白桦` | 中文 | 男 | 官方内置 |
| Mia | `Mia` | 英文 | 女 | 官方内置 |
| Chloe | `Chloe` | 英文 | 女 | 官方内置 |
| Milo | `Milo` | 英文 | 男 | 官方内置 |
| Dean | `Dean` | 英文 | 男 | 官方内置 |

### 3) 风格控制
- 支持 v2.5 推荐标签写法：`(<风格>)文本`
- 前端提供常见风格快捷按钮（含 `唱歌`）
- 限制：`唱歌` 仅在 `mimo-v2.5-tts` 下可用（与官方说明一致）

### 4) 音频格式
- `wav`
- `mp3`
- `pcm16`

### 5) 安全与交互
- API Key 仅保存在浏览器 `localStorage`
- 前端直连官方接口：`https://api.xiaomimimo.com/v1/chat/completions`
- 支持播放、下载、历史记录回放

---

## 🚀 快速开始

### 本地运行
1. 克隆仓库
2. 直接用浏览器打开 `index.html`
3. 输入小米米墨 API Key
4. 选择模型后生成语音

### 在线部署（GitHub Pages）
1. Fork 本仓库
2. 打开仓库 `Settings -> Pages`
3. Source 选择分支与根目录
4. 保存并等待发布

---

## 🔧 请求行为说明（与 v2.5 对齐）

### 请求头
使用：

- `Content-Type: application/json`
- `api-key: <YOUR_MIMO_API_KEY>`

> 注意：不是 Bearer Token 头。

### messages 规则
- 要合成的文本放在 `assistant.content`
- `user.content` 用作风格/语境指令或上下文
- `voicedesign` 模型下 `user.content` 为**音色描述**（必填）

### audio 规则
- `mimo-v2.5-tts`：`audio.voice` 传内置音色 ID
- `mimo-v2.5-tts-voicedesign`：`audio` 只需格式（无需 voice）
- `mimo-v2.5-tts-voiceclone`：`audio.voice` 传音色样本 Data URL

---

## 🧪 示例请求

### A. 内置音色
```json
{
  "model": "mimo-v2.5-tts",
  "messages": [
    {"role": "user", "content": "请用轻快积极语气朗读"},
    {"role": "assistant", "content": "(开心)今天效率非常高！"}
  ],
  "audio": {
    "format": "wav",
    "voice": "mimo_default"
  }
}
```

### B. Voice Design
```json
{
  "model": "mimo-v2.5-tts-voicedesign",
  "messages": [
    {"role": "user", "content": "年轻男声，口齿清晰，语速中等偏快，情绪积极。"},
    {"role": "assistant", "content": "今天我们继续推进项目。"}
  ],
  "audio": {
    "format": "wav"
  }
}
```

### C. Voice Clone
```json
{
  "model": "mimo-v2.5-tts-voiceclone",
  "messages": [
    {"role": "user", "content": ""},
    {"role": "assistant", "content": "今天工作完成得很好。"}
  ],
  "audio": {
    "format": "wav",
    "voice": "data:audio/mpeg;base64,<BASE64_AUDIO>"
  }
}
```

---

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

## 📄 License

MIT
