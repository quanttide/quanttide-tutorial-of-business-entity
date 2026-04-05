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
