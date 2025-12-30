# langChain相关

## 1.Model

1.支持多种的模型调用

- Tool calling（工具调用）
- Structured output(结构化输出)
- Multimodality(多模态)
- Reasoning(推理)

2.调用模型的三种方式

- invoke():单次调用（同步）
- stream()：流式输出
- batch()：批量请求

3.模型参数

常见的模型参数包括：

- model：模型名称或标识符
- api_key：鉴权需要的key（通常使用环境变量设置）
- temperature：温度，越大越随机/有创意，越小越稳定
- timeout：超时时间（秒)
- max_tokens：限制输出 token 数量
- max_retries：网络失败等情况下的最大重试次数

## 2.Prompts（提示词）

**管理和优化**输入给模型的指令（即提示词），是提升模型表现的关键。

## 3.Tool调用

是Agent可调用的外部资源，包括API接口，函数等

## 4.langChain记忆

1.短期记忆

对话的上下文

## 5.代理（Agents）

这是 LangChain 中最强大的概念之一。代理让 LLM 具备了**决策能力**，可以动态地决定执行一系列动作（使用工具）来完成用户目标。

- **核心思想**： 模型作为“大脑”，根据用户输入和观察结果，决定下一步该调用哪个工具。
- **工具**： 代理可以调用的函数。可以是搜索引擎、计算器、数据库查询 API，或任何自定义函数。
- **代理类型**： LangChain 提供了多种预定义的代理推理策略，如 `ReAct`、`Plan-and-Execute` 等。

## 6.链

- **作用**：将多个组件（模型、提示、工具等）**按顺序组合**成完整的工作流，是LangChain“链式”思想的体现。