# LLM 库使用指南

## 简介

[llm](https://llm.datasette.io/) 是一个命令行工具，用于统一调用各种大语言模型 API。

## 安装

```bash
pip install llm --break-system-packages
```

## 配置

### API Key 管理

使用 `llm` 自带的密钥管理，密钥保存在本地 `keys.json` 中：

```bash
# 交互式输入 API Key（不会暴露在 Shell 历史中）
llm keys set openai
```

### 阿里云百炼（DashScope）配置

百炼兼容 OpenAI API，通过 `extra-openai-models.yaml` 配置文件添加模型：

配置文件路径：`~/.config/io.datasette.llm/extra-openai-models.yaml`

```yaml
- model_id: qwen-turbo
  model_name: qwen-turbo
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai
```

常用模型配置示例：

```yaml
# 千问系列
- model_id: qwen3-max
  model_name: qwen3-max
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai

- model_id: qwen3.6-plus
  model_name: qwen3.6-plus
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai

- model_id: qwen3.5-flash
  model_name: qwen3.5-flash
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai

# DeepSeek
- model_id: deepseek-v3.2
  model_name: deepseek-v3.2
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai

# GLM 智谱
- model_id: glm-5
  model_name: glm-5
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai

# Kimi
- model_id: kimi-k2.5
  model_name: kimi-k2.5
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai
```

### 代理问题

如果系统设置了 `socks://` 代理，`llm-ollama` 插件会崩溃。解决方法：

```bash
# 在 ~/.bashrc 中添加 alias
alias llm='ALL_PROXY="" all_proxy="" HTTP_PROXY="" HTTPS_PROXY="" http_proxy="" https_proxy="" llm'
```

## 常见问题

### 1. `llm keys set` 输入无效

**现象**：运行 `llm keys set openai` 后，输入的 Key 没有被正确保存，`keys.json` 中的值变成了 `"Enter key: "`。

**原因**：终端无法控制回显（`GetPassWarning`），导致 `llm` 捕获了提示文本而非实际输入。

**解决**：直接手动编辑 `keys.json` 文件：

```bash
# 找到配置文件路径
python3 -c "from llm import user_dir; print(user_dir() / 'keys.json')"
# 通常位于 ~/.config/io.datasette.llm/keys.json

# 直接编辑，写入正确的 Key
```

`keys.json` 格式：
```json
{
  "// Note": "This file stores secret API credentials. Do not share!",
  "openai": "sk-你的真实API密钥"
}
```

### 2. 代理导致连接失败或崩溃

**现象**：运行 `llm` 时报错 `ValueError: Unknown scheme for proxy URL URL('socks://...')` 或 `Connection error`。

**原因**：`llm-ollama` 插件依赖的 `ollama` Python 库在初始化时读取 `ALL_PROXY` 环境变量，但 `httpx` 不支持 `socks://` 协议。

**解决**：运行 `llm` 时清除所有代理变量：

```bash
ALL_PROXY="" all_proxy="" HTTP_PROXY="" HTTPS_PROXY="" http_proxy="" https_proxy="" llm -m qwen-turbo "你好"
```

持久化方案：在 `~/.bashrc` 中添加 alias：

```bash
alias llm='ALL_PROXY="" all_proxy="" HTTP_PROXY="" HTTPS_PROXY="" http_proxy="" https_proxy="" llm'
```

### 3. 自定义模型未被识别

**现象**：配置了 `extra-openai-models.yaml` 后，`llm models` 仍然看不到自定义模型。

**原因**：`llm` 的 OpenAI 插件内置了模型白名单，不会自动从自定义端点拉取模型列表。

**解决**：确保配置文件格式正确，每个模型需要同时指定 `model_id`、`model_name`、`api_base` 和 `api_key_name`：

```yaml
- model_id: qwen-turbo          # llm 中使用的名称
  model_name: qwen-turbo        # 实际传给 API 的名称
  api_base: "https://dashscope.aliyuncs.com/compatible-mode/v1"
  api_key_name: openai          # 对应 keys.json 中的键名
```

配置完成后运行 `llm models` 验证，新模型应出现在列表中。

### 4. 配置文件路径

`llm` 使用两个独立的目录：

| 用途 | 路径 |
|------|------|
| 用户数据（密钥、日志） | `~/.config/io.datasette.llm/` |
| 模型配置 | `~/.config/io.datasette.llm/extra-openai-models.yaml` |

可通过环境变量 `LLM_USER_PATH` 自定义用户目录位置。

## 基本使用

### 查看可用模型

```bash
llm models
```

### 执行提示词

```bash
# 使用默认模型
llm "你好"

# 指定模型
llm -m qwen-turbo "解释一下量子计算"

# 使用系统提示词
llm -m deepseek-v3.2 -s "你是一个编程老师" "解释递归"

# 管道输入
cat code.py | llm -m qwen3-coder-plus "审查这段代码"

# 多轮对话
llm chat -m qwen3.6-plus
```

### 常用参数

| 参数 | 说明 |
|------|------|
| `-m, --model` | 指定模型 |
| `-s, --system` | 系统提示词 |
| `-n, --no-log` | 不记录到数据库 |
| `-c, --continue` | 继续上次对话 |
| `-a, --attachment` | 附件（图片等） |
| `-o, --option` | 模型选项 |
| `-t, --template` | 使用模板 |

### 管理别名

```bash
llm aliases set my-ai qwen3.6-plus
llm -m my-ai "你好"
```

## 日志管理

`llm` 默认将所有对话记录到 SQLite 数据库。

```bash
# 查看最近的对话
llm logs -n 5

# 查看特定模型的对话
llm logs -m qwen-turbo

# 关闭日志
llm -m qwen-turbo "你好" --no-log
```

## 已配置模型清单

通过阿里云百炼可使用的模型：

| 类别 | 模型 |
|------|------|
| 千问旗舰 | qwen3-max, qwen3.6-plus, qwen-max |
| 千问均衡 | qwen-plus, qwen3.5-plus |
| 千问快速 | qwen3.5-flash, qwen-flash, qwen-turbo |
| 代码 | qwen-coder-plus, qwen3-coder-plus, qwen3-coder-flash |
| 视觉 | qwen-vl-max, qwen3-vl-plus, qwen3-vl-flash |
| 推理 | qwq-plus, qwq-32b |
| 长文本 | qwen-long |
| 数学 | qwen-math-plus |
| 深度研究 | qwen-deep-research |
| 翻译 | qwen-mt-plus |
| DeepSeek | deepseek-v3.2, deepseek-v3.1, deepseek-v3, deepseek-r1 |
| GLM | glm-5, glm-4.7, glm-4.6, glm-4.5 |
| Kimi | kimi-k2.5, kimi-k2-thinking |
| MiniMax | minimax-m2.7, minimax-m2.5 |
| 零一万物 | yi-large, yi-large-turbo, yi-medium |
| 百川 | baichuan2-turbo |
| Llama | llama-4-maverick, llama3.3-70b, llama3.1-405b |
