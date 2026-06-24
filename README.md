<p align="center">
  <img src="https://api.jilianai.com/logo.png" alt="JiLianAi Api Logo" width="120" />
  <h1 align="center">JiLianAi Api（极联 AI）</h1>
  <p align="center">
    <strong>统一 AI API 网关 · AI 资产管理平台</strong>
  </p>
  <p align="center">
    Unified AI API Gateway &amp; AI Asset Management System
  </p>
  <p align="center">
    <a href="https://api.jilianai.com/sign-up?aff=pAkT" target="_blank">🌐 官网首页</a>
    ·
    <a href="https://api.jilianai.com/docs" target="_blank">📖 API 文档</a>
    ·
    <a href="https://api.jilianai.com/pricing" target="_blank">💰 定价</a>
  </p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-active-brightgreen" alt="Status" />
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="License" />
  <img src="https://img.shields.io/badge/OpenAI-Compatible-14b8a6" alt="OpenAI Compatible" />
</p>

---

## 📋 简介

**JiLianAi Api（极联 AI）** 是一个统一的 AI API 网关和 AI 资产管理平台，致力于为开发者和企业提供**一站式 AI 模型 API 调用解决方案**。

通过 JiLianAi Api，您仅需 **一个 API Key**、**一个 Base URL**，即可无缝调用全球主流大语言模型，无需在多个供应商之间切换和管理多个订阅。

---

## ✨ 核心特性

### 🚀 统一 API 接入

- **单一接口调用多模型**：一个 API Key 即可调用 OpenAI、Anthropic Claude、Google Gemini、DeepSeek 等国内外主流大模型
- **完全兼容 OpenAI 格式**：无需修改现有代码，仅需更改 Base URL 即可完成迁移
- **多协议支持**：原生支持 SSE 流式响应，提供毫秒级低延迟体验

### 🔄 智能路由与容灾

- **自动 Fallback**：当主模型不可用时，自动切换到备用模型，保障服务高可用
- **负载均衡**：智能分发请求到多个可用的模型实例
- **自动重试**：请求失败自动重试，提升调用成功率

### 💰 成本管理

- **按量付费**：预充值模式，用多少扣多少，无需预付费套餐绑定
- **透明定价**：实时查询各模型单价，费用清晰可查
- **消费记录**：提供详细的 API 调用日志和费用明细

### 🔐 安全与权限

- **API Key 管理**：支持创建多个 API Key，分别设置权限和额度
- **访问控制**：可按消费者粒度控制模型访问权限
- **数据安全**：TLS 加密传输，保障数据安全

### 📊 资产管理

- **AI 资产统一管理**：集中管理模型调用、配额、凭证等资源
- **用量监控**：实时查看 API 调用量、Token 消耗和响应延迟
- **统计报表**：提供多维度的数据统计和可视化报表

---

## 🧩 支持模型

JiLianAi Api 聚合了全球主流大语言模型，涵盖文本生成、图像生成、多模态理解等能力。覆盖但不限于：

| 类别 | 模型 |
|------|------|
| **OpenAI** | GPT-4o、GPT-4o-mini、GPT-4-Turbo、GPT-3.5-Turbo、o1、o1-mini |
| **Anthropic** | Claude 3.5 Sonnet、Claude 3 Opus、Claude 3 Haiku、Claude 4 |
| **Google** | Gemini 2.0 Flash、Gemini 1.5 Pro、Gemini 1.5 Flash |
| **DeepSeek** | DeepSeek-V3、DeepSeek-R1 |
| **Meta** | Llama 3.1 (8B/70B/405B)、Llama 3 |
| **Mistral** | Mistral Large、Mistral Medium、Mixtral 8x22B |
| **国内模型** | Qwen 系列（通义千问）、Doubao（豆包）、GLM（智谱）、Yi（零一万物） |
| **多模态** | DALL·E 3、Stable Diffusion、Midjourney |
| **其他** | Grok、Cohere Command R+ 等 |

> 完整模型列表请访问 [官网模型页面](https://api.jilianai.com) 查看最新信息。

---

## 🔌 快速开始

### 1. 获取 API Key

注册并登录 [JiLianAi Api 控制台](https://api.jilianai.com/sign-up?aff=pAkT)，在 "API Keys" 页面创建您的 API Key。

### 2. 配置 Base URL

将您代码中的 Base URL 替换为：

```
https://api.jilianai.com
```

### 3. 发起请求

**使用 cURL：**

```bash
curl https://api.jilianai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "gpt-4o",
    "messages": [
      {"role": "user", "content": "Hello!"}
    ]
  }'
```

**使用 Python（OpenAI SDK）：**

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://api.jilianai.com/v1"
)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Hello!"}]
)

print(response.choices[0].message.content)
```

**使用 JavaScript / TypeScript：**

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: 'YOUR_API_KEY',
  baseURL: 'https://api.jilianai.com/v1',
});

const response = await client.chat.completions.create({
  model: 'gpt-4o',
  messages: [{ role: 'user', content: 'Hello!' }],
});

console.log(response.choices[0].message.content);
```

---

## 📚 API 参考

### 聊天完成

```
POST /v1/chat/completions
```

兼容 OpenAI Chat Completions API 格式，支持 `stream` 流式响应。

**请求体参数：**

| 参数 | 类型 | 必填 | 描述 |
|------|------|------|------|
| `model` | string | 是 | 模型名称，如 `gpt-4o`、`claude-sonnet-4` |
| `messages` | array | 是 | 消息列表 |
| `stream` | boolean | 否 | 是否启用流式输出，默认 `false` |
| `max_tokens` | integer | 否 | 最大生成 Token 数 |
| `temperature` | number | 否 | 采样温度，0-2 |
| `top_p` | number | 否 | 核采样参数 |

### 模型列表

```
GET /v1/models
```

获取当前可用的所有模型列表。

### 余额查询

```
GET /v1/dashboard/billing
```

查询账户余额和使用情况。

---

## 🛠️ 集成指南

### 支持的平台

几乎兼容所有支持 OpenAI API 格式的第三方应用和框架：

- [ChatGPT Next Web](https://github.com/ChatGPTNextWeb/ChatGPT-Next-Web)
- [Lobe Chat](https://github.com/lobehub/lobe-chat)
- [Open WebUI](https://github.com/open-webui/open-webui)
- [Jan](https://jan.ai/)
- [LangChain](https://www.langchain.com/)
- [Dify](https://dify.ai/)

> 仅需将自定义 API 地址指向 `https://api.jilianai.com` 即可。

---

## 📈 使用场景

- **🤖 智能客服**：快速接入多种 LLM，构建智能对话系统
- **📝 内容生成**：批量生成文案、代码、翻译等文本内容
- **🔬 AI 研究**：对比测试不同模型的效果与性能
- **🏢 企业应用**：统一管理企业内 AI API 调用，便于监控与审计
- **🛠️ 工具开发**：为您的应用或 SaaS 产品快速添加 AI 能力

---

## ❓ 常见问题

<details>
<summary><strong>Q: JiLianAi Api 与直接调用官方 API 有何区别？</strong></summary>
MeshsApi 提供统一的接入和管理平台，一个 API Key 即可调用多种模型，无需在多个供应商之间切换。同时提供智能路由、自动 Fallback、用量监控等增值功能。
</details>

<details>
<summary><strong>Q: 如何充值？</strong></summary>
登录控制台后，在 "充值" 页面选择充值金额，支持支付宝、微信支付等多种支付方式。
</details>

<details>
<summary><strong>Q: 数据会经过中转存储吗？</strong></summary>
MeshsApi 仅做实时请求转发，不存储您的对话数据。所有数据传输均经过 TLS 加密。
</details>

<details>
<summary><strong>Q: 如何查看调用记录？</strong></summary>
在控制台的 "日志" 或 "Dashboard" 页面，可以查看详细的 API 调用历史、Token 消耗和费用明细。
</details>

---

## 🤝 贡献

欢迎提交 Issue 和 PR 来帮助改进 MeshsApi 的文档和示例代码！

1. Fork 本仓库
2. 创建您的特性分支 (`git checkout -b feat/amazing-feature`)
3. 提交您的修改 (`git commit -m 'feat: add some amazing feature'`)
4. 推送至分支 (`git push origin feat/amazing-feature`)
5. 提交 Pull Request

---

## 📄 许可

本项目采用 MIT 许可证。详情请参见 [LICENSE](LICENSE) 文件。

---

<p align="center">
  <b>JiLianAi Api（极联 AI）</b> · <a href="https://api.jilianai.com">https://api.jilianai.com</a><br>
  <sub>统一 AI API 网关 · 让 AI 接入更简单</sub>
</p>
