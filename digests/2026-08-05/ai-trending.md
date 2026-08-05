# AI 开源趋势日报 2026-08-05

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-08-05 03:13 UTC

---



# 📊 AI 开源趋势日报 — 2026-08-05

---

## 一、今日速览

今日 AI 开源领域最显著的趋势是 **Agent 框架与工具链的爆发式增长**：从腾讯 DB-Agent-Memory 到 LiveKit 语音 Agent，再到 DeepSeek-Reasonix 等终端编程代理，Agent 正从概念验证快速走向工程化落地。同时，**RAG 基础设施**持续升温，PageIndex 提出"无向量库"推理型 RAG 的新思路引发关注。本地化高效推理（AirLLM 单卡 70B、Ollama 扩展新模型）与 Agent 安全（Uber ADR）也成为今日亮点方向。

---

## 二、各维度热门项目

### 🔧 AI 基础工具

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 177,800 | 本地运行 Kimi-K2.6、GLM-5.2、DeepSeek 等多模型的利器，降低大模型使用门槛。今日 Trending 未上榜，但长期位居 LLM 工具类榜首。 |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Python | 88,203 | 高吞吐 LLM 推理引擎，PagedAttention 技术领先。是生产部署大模型服务的事实标准之一。 |
| [lyogavin/airllm](https://github.com/lyogavin/airllm) | Jupyter Notebook | —（+1,711 today） | **今日 Trending 爆款**：单卡 4GB GPU 即可运行 AirLLM 70B 推理，极大降低了本地大模型运行门槛。 |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | 30,884（+922 today） | **今日 Trending 新上榜**：DeepSeek 原生终端编程 Agent，围绕 prefix-cache 稳定性设计，适合长时间挂机运行。 |
| [0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig) | Rust | 8,174 | Rust 语言构建模块化 LLM 应用的框架，填补 Rust AI 工具链的空白，生态持续扩展中。 |
| [livekit/agents](https://github.com/livekit/agents) | Python | —（+432 today） | **今日 Trending 新上榜**：实时语音 AI Agent 框架，支持 🤖🎙📹 多模态交互，填补语音 Agent 开发工具缺口。 |

---

### 🤖 AI 智能体/工作流

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | Python | 185,817 | 自主 Agent 标杆项目，支持任务自动规划与执行，社区活跃度持续领先。 |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | Python | 225,570 | "随用户成长的 Agent"，集成记忆、技能与 MCP 支持，是 Agent 框架的重要玩家。 |
| [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | Python | 46,322 | 开源超级 AI 助手，支持多模型、多渠道、自进化记忆，前身为 chatgpt-on-wechat，国内社区影响广泛。 |
| [TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory) | TypeScript | —（+1,111 today） | **今日 Trending 新上榜**：腾讯团队级 Agent 记忆中枢，将对话、文档、代码转化为 Chat Memory/Skill/LLM-Wiki/Code-Graph 四类资产，具工程落地价值。 |
| [obra/superpowers](https://github.com/obra/superpowers) | Shell | —（+653 today） | **今日 Trending 新上榜**：Agentic 技能框架与软件开发方法论，强调可工作的技能体系而非空泛概念。 |
| [uber/ADR](https://github.com/uber/uber/ADR) | Python | —（+148 today） | **今日 Trending 新上榜**：Uber 内部部署的 AI Agent 安全观测与威胁检测平台，Agent 安全方向的重要实践。 |
| [browser-use/video-use](https://github.com/browser-use/video-use) | Python | —（+320 today） | **今日 Trending 新上榜**：基于 browser-use 的视频编辑 Agent，体现 Agent 向多媒体创作领域延伸的趋势。 |

---

### 📦 AI 应用

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 101,629 | AI 一键生成高清短视频，利用大模型+自动化工作流，垂直内容生成领域标杆应用。 |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 60,085 | LLM 驱动的多市场股票智能分析系统，支持多源行情、实时新闻与自动推送，零成本定时运行。 |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | 43,045 | AI 生成原生 PowerPoint 演示文稿，支持形状、动画、图表与音频旁白，办公自动化场景实用。 |
| [microsoft/generative-ai-for-beginners](https://github.com/microsoft/generative-ai-for-beginners) | Jupyter Notebook | —（+783 today） | **今日 Trending 新上榜**：微软官方生成式 AI 入门教程（21 课），持续吸引初学者，教育类内容刚需。 |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 49,416 | AI 生产力工作室，集成智能聊天、自主 Agent 与 300+ 助手，统一接入前沿 LLM。 |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | Python | 147,869 | 用户友好的本地 AI 聊天界面，支持 Ollama 与 OpenAI API，是本地部署 LLM 的首选前端之一。 |

---

### 🧠 大模型/训练

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [huggingface/transformers](https://github.com/huggingface/transformers) | Python | 163,339 | Hugging Face 核心库，支持文本/视觉/音频/多模态 SOTA 模型的推理与训练，AI 领域基础设施级项目。 |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | 196,804 | Google 开源的机器学习框架，长期位居 GitHub 热门榜前列，生态完整。 |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,185 | Meta 主导的深度学习框架，动态计算图与丰富生态使其成为研究与工业界首选。 |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | Python | 7,273 | 开源 LLM 评估平台，支持 Llama3、Qwen、GLM 等 100+ 数据集，国内大模型评测重要工具。 |
| [skyzh/tiny-llm](https://github.com/skyzh/tiny-llm) | Python | 4,441 | Apple Silicon 上构建轻量 vLLM+Qwen 的 LLM 推理课程，适合系统工程师学习推理优化。 |

---

### 🔍 RAG/知识库

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [langgenius/dify](https://github.com/langgenius/dify) | TypeScript | 151,357 | Agentic 工作流与 RAG 管道构建平台，支持云端/VPC/自托管，从原型到生产的一站式方案。 |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 86,840 | 开源 RAG 引擎，融合前沿 RAG 与 Agent 能力，专注文档理解与上下文增强。 |
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | TypeScript | 161,124 | 大规模 Web 搜索/爬取/交互 API，为 Agent 提供高质量上下文输入，生态扩展迅速。 |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | 62,540 | Agent 通用记忆层，实现跨会话持久化记忆，解决 Agent 上下文窗口限制问题。 |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Python | 29,780 | 开源 AI 记忆平台，基于知识图谱引擎为 Agent 提供长期记忆，支持自托管部署。 |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | 35,017 | **创新方向**：无向量库的推理型文档索引，探索 Reasoning-based RAG 新范式，值得关注。 |
| [meilisearch/meilisearch](https://github.com/meilisearch/meilisearch) | Rust | 58,858 | 高性能搜索 API，支持 AI 驱动的混合搜索，适合集成到 RAG 管道中。 |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | Go | 45,510 | 云原生向量数据库，支持大规模 ANN 搜索，国产向量库代表。 |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Rust | 33,782 | 高性能向量数据库，支持过滤搜索与 Cloud 版本，Rust 生态向量库重要选手。 |

---

## 三、趋势信号分析

**Agent 框架正从"玩具"走向"工程"**：今日 Trending 中腾讯 DB-Agent-Memory、Uber ADR、obra/superpowers 等项目的集中涌现，标志着 Agent 基础设施（记忆、安全、技能管理）进入工程化深耕阶段。Agent 的安全观测与治理能力开始受到头部企业重视。

**RAG 方向出现分化信号**：传统向量数据库（Milvus、Qdrant）继续稳固，但 PageIndex 提出的"无向量库、推理型 RAG"新思路代表了一种降本增效的新探索，值得长期跟踪。

**本地化与高效推理热度不减**：AirLLM 单卡跑 70B 和 Ollama 持续扩展模型支持，反映开发者和中小企业对降低 LLM 使用成本有强烈需求。

**Agent 与开发工具链深度融合**：DeepSeek-Reasonix（Go）、browser-use/video-use、compound-engineering-plugin 等项目显示，AI Agent 正在快速渗透编程、运维、多媒体等开发者日常场景。

---

## 四、社区关注热点

- **[TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory)** — 今日 +1,111 stars，Agent 记忆管理的工程化实践，四类记忆资产（Chat Memory/Skill/LLM-Wiki/Code-Graph）的设计思路清晰，适合企业级场景参考。
- **[esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix)** — 国产 DeepSeek 原生终端编程 Agent，prefix-cache 稳定性设计有针对性，今日 +922 stars 反映国内开发者对本地化 Agent 工具的强烈需求。
- **[VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex)** — 探索无向量库的推理型 RAG，若验证可行将对现有 RAG 架构产生颠覆性影响，建议关注其后续迭代。
- **[uber/ADR](https://github.com/uber/ADR)** — Agent 安全观测与威胁检测平台，在 Agent 落地过程中安全问题日益突出，此类基础设施将逐渐成为标配。
- **[livekit/agents](https://github.com/livekit/agents)** — 实时语音 Agent 框架，填补了多模态 Agent 开发工具空白，音视频 AI 应用开发者应重点关注。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*