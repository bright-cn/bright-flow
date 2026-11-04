# 配置指南

## 快速设置

将 `conf.yaml.example` 文件复制到 `conf.yaml`，并根据你的具体设置和要求修改配置。

```bash
cd deer-flow
cp conf.yaml.example conf.yaml
```

## DeerFlow 支持哪些模型？

DeerFlow 目前仅支持非推理模型，这意味着暂不支持 OpenAI 的 o1/o3 或 DeepSeek 的 R1 等模型，但我们将在未来增加支持。

### 支持的模型

`doubao-1.5-pro-32k-250115`、`gpt-4o`、`qwen-max-latest`、`gemini-2.0-flash`、`deepseek-v3`，以及理论上实现 OpenAI API 规范的任何其他非推理聊天模型。

> [!NOTE]
> 深度研究流程要求模型具有**更长的上下文窗口**，但并非所有模型都支持这一点。一种变通方法是，在网页右上角的设置对话框中将 `Max steps of a research plan` 设置为 `2`，或在调用 API 时将 `max_step_num` 设置为 `2`。

### 如何切换模型？
你可以修改项目根目录中的 `conf.yaml` 文件，并使用 [litellm 格式](https://docs.litellm.ai/docs/providers/openai_compatible)的配置来切换所用模型。

---

### 如何使用 OpenAI 兼容模型？

DeerFlow 支持集成 OpenAI 兼容模型，即实现 OpenAI API 规范的模型。其中包括提供与 OpenAI 格式兼容的 API 端点的各种开源及商业模型。有关详细文档，请参阅 [litellm OpenAI-Compatible](https://docs.litellm.ai/docs/providers/openai_compatible)。以下是使用 OpenAI 兼容模型的 `conf.yaml` 配置示例：

```yaml
# An example of Doubao models served by VolcEngine
BASIC_MODEL:
  base_url: "https://ark.cn-beijing.volces.com/api/v3"
  model: "doubao-1.5-pro-32k-250115"
  api_key: YOUR_API_KEY

# An example of Aliyun models
BASIC_MODEL:
  base_url: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  model: "qwen-max-latest"
  api_key: YOUR_API_KEY

# An example of deepseek official models
BASIC_MODEL:
  base_url: "https://api.deepseek.com"
  model: "deepseek-chat"
  api_key: YOU_API_KEY

# An example of Google Gemini models using OpenAI-Compatible interface
BASIC_MODEL:
  base_url: "https://generativelanguage.googleapis.com/v1beta/openai/"
  model: "gemini-2.0-flash"
  api_key: YOUR_API_KEY
```

### 如何使用 Ollama 模型？

DeerFlow 支持集成 Ollama 模型。你可以参阅 [litellm Ollama](https://docs.litellm.ai/docs/providers/ollama)。<br> 以下是使用 Ollama 模型的 `conf.yaml` 配置示例：

```yaml
BASIC_MODEL:
  model: "ollama/ollama-model-name"
  base_url: "http://localhost:11434" # Local service address of Ollama, which can be started/viewed via ollama serve
```

### 如何使用 OpenRouter 模型？

DeerFlow 支持集成 OpenRouter 模型。你可以参阅 [litellm OpenRouter](https://docs.litellm.ai/docs/providers/openrouter)。要使用 OpenRouter 模型，你需要：
1. 从 OpenRouter（https://openrouter.ai/）获取 OPENROUTER_API_KEY，并在环境变量中进行设置。
2. 在模型名称前添加 `openrouter/` 前缀。
3. 配置正确的 OpenRouter 基础 URL。

以下是使用 OpenRouter 模型的配置示例：
1. 在环境变量（例如 `.env` 文件）中配置 OPENROUTER_API_KEY
```ini
OPENROUTER_API_KEY=""
```
2. 在 `conf.yaml` 中设置模型名称
```yaml
BASIC_MODEL:
  model: "openrouter/google/palm-2-chat-bison"
```

注意：可用模型及其确切名称可能会随时间变化。请在 [OpenRouter 官方文档](https://openrouter.ai/docs)中确认当前可用的模型及其正确标识符。

### 如何使用 Azure 模型？

DeerFlow 支持集成 Azure 模型。你可以参阅 [litellm Azure](https://docs.litellm.ai/docs/providers/azure)。`conf.yaml` 的配置示例：
```yaml
BASIC_MODEL:
  model: "azure/gpt-4o-2024-08-06"
  api_base: $AZURE_API_BASE
  api_version: $AZURE_API_VERSION
  api_key: $AZURE_API_KEY
```
