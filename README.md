🌐 API Gateway - api.jilianai.com
https://img.shields.io/badge/license-MIT-blue.svg
https://img.shields.io/docker/pulls/calciumion/new-api

https://api.jilianai.com 是一个高性能、自托管的 AI 模型聚合网关，基于 NewAPI 构建。它提供了一个统一的 OpenAI 风格接口，让您能够通过单一 API Key 轻松访问多种大语言模型（如 GPT-4、DeepSeek、Claude、Gemini 等），并支持图像生成（如 gpt-image-2）、文件处理等进阶能力。

✨ 主要特性
🔑 统一 API 接入：兼容 OpenAI API 规范，无缝替换官方 SDK。

🧩 多模型聚合：支持 OpenAI、Azure、Anthropic、DeepSeek、Google（Gemini）以及国内主流模型（通义千问、文心一言、智谱 GLM 等）。

🎨 图像生成支持：完整支持 gpt-image-2、dall-e-3 等图像模型，并可灵活配置超时规避 504 错误。

⚙️ 灵活的管理后台：提供 Web 管理界面，轻松管理渠道、模型、API Key 和额度。

🐳 容器化部署：官方 Docker 镜像，一键启动，搭配 Caddy/Nginx 实现 HTTPS 和自动超时控制。

📊 用量统计与监控：实时记录请求日志，支持 Prometheus 指标导出。

🔒 安全与限流：支持 IP 白名单、单 Key 限速、每日用量限制等。

📡 API 调用示例
您可以使用任何 OpenAI SDK 调用本网关，只需将 base_url 替换为 https://api.jilianai.com/v1，并填写您在管理后台生成的 API Key。

Python 示例
python
from openai import OpenAI

client = OpenAI(
    base_url="https://api.jilianai.com/v1",
    api_key="your-api-key-here"
)

# 文本生成
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "介绍一下你自己"}]
)
print(response.choices[0].message.content)

# 图像生成（支持 gpt-image-2）
image = client.images.generate(
    model="gpt-image-2",
    prompt="一只坐在云朵上的科幻风格熊猫",
    size="1024x1024",
    quality="low",   # 推荐 low 以避免超时
    n=1
)
print(image.data[0].url)
cURL 示例
bash
curl https://api.jilianai.com/v1/chat/completions \
  -H "Authorization: Bearer your-api-key" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek-v4-flash",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
🗂️ 管理后台功能
渠道管理：添加/启用/禁用各类模型提供方（如 OpenRouter、Azure、DeepSeek 等）。

模型映射：将不同提供方的模型统一命名，方便前端调用。

API Key 管理：生成、续期、限制额度。

请求日志：查看详细调用记录，便于审计和排错。


如何添加一个自定义模型？
在管理后台「渠道」中添加新的提供方，填写 Base URL 和 API Key。

在「模型」中创建映射，将自定义模型名称绑定到该渠道。


🤝 贡献与支持
欢迎提交 Issue 和 Pull Request！如需商业技术支持或定制服务，请联系 your-email@example.com。

📄 许可证
本项目基于 MIT License 开源。
