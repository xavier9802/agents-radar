# AI 开源趋势日报 2026-08-23

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-08-23 01:46 UTC

---



# AI 开源趋势日报 — 2026-08-23

---

## 一、今日速览

今日 AI 开源热榜呈现**编码智能体工具链全面爆发**之势：OpenAI Codex、Claude Code、ECC、Cursor 插件等终端编码智能体相关产品集体上榜，标志着"AI 编程助手生态"进入工具化深水区。同时，智能体记忆（Mem0、claude-mem）和 RAG 引擎（RAGFlow）等基础设施项目持续高增长，反映出社区对"可复用智能体能力"的强烈需求。开源本地模型推理（Ollama、Modular）和轻量级模型训练（minimind）继续受到开发者关注。

---

## 二、各维度热门项目

### 🔧 AI 基础工具

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [openai/codex](https://github.com/openai/codex) | Rust | 0（+1,544） | OpenAI 推出的轻量终端编码智能体，今日爆发性增星，标志开源编码智能体赛道再添重量级玩家。 |
| [modular/modular](https://github.com/modular/modular) | Mojo | 0（+395） | Modular 平台（含 MAX 推理引擎和 Mojo 语言），为 AI 推理提供硬件级优化方案。 |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 179,209 | 本地运行各类开源 LLM 的一站式工具，新增支持 Kimi-K2.6、GLM-5.2、DeepSeek 等新模型，持续更新模型库。 |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Python | 89,722 | 高吞吐 LLM 推理引擎，内存效率领先，是自建 LLM 服务的首选后端之一。 |
| [jingyaogong/minimind](https://github.com/jingyaogong/minimind) | Python | 54,927 | 2 小时从零训练 64M 参数 LLM 的入门项目，是理解 LLM 训练全流程的最佳实践教材。 |
| [AarambhDevHub/aarambh-studio](https://github.com/AarambhDevHub/aarambh-studio) | Rust | 82 | 纯 Rust 编写的解码器 LLM，基于 Candle 框架，支持 DeltaNet + 稀疏注意力，不依赖 Python。 |
| [skyzh/tiny-llm](https://github.com/skyzh/tiny-llm) | Python | 4,512 | 在 Apple Silicon 上实现轻量级 LLM 推理系统，适合系统工程师学习推理优化。 |

---

### 🤖 AI 智能体 / 工作流

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | JavaScript | 242,182（+411） | Agent harness 性能优化系统，支持 Claude Code/Codex/Cursor 等，今日同步登上 Trending，生态兼容性是其核心优势。 |
| [anthropics/claude-code](https://github.com/anthropics/claude-code) | Python | 0（+127） | Anthropic 官方终端智能体，理解代码库并通过自然语言执行任务，今日正式开源引爆社区关注。 |
| [mattpocock/skills](https://github.com/mattpocock/skills) | Shell | 0（+2,683） | 从开发者真实 `.agents` 目录提炼的智能体技能集，今日增星最快，反映社区对"可复用智能体技能"的旺盛需求。 |
| [obra/superpowers](https://github.com/obra/superpowers) | Shell | 0（+592） | Agentic skills 框架与软件开发方法论，为终端智能体提供系统化能力扩展路径。 |
| [Eigenwise/atomic-agents](https://github.com/Eigenwise/atomic-agents) | Python | 6,191 | 原子化构建 AI 智能体的框架，强调模块化和可组合性，适合复杂多步任务。 |
| [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | Python | 186,778 | 经典自主智能体项目，持续迭代中，是当前最成熟的开源 AI Agent 参考实现之一。 |
| [shareAI-lab/learn-claude-code](https://github.com/shareAI-lab/learn-claude-code) | Python | 74,957 | 从零实现类 Claude Code 的 nano agent harness 教程，配合今日 Claude Code 开源热点，成为学习首选资料。 |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | 35,047 | DeepSeek 原生终端编码智能体，专注于前缀缓存稳定性，适合长期运行场景。 |

---

### 📦 AI 应用

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | TypeScript | 0（+149） | 开源 AI 工作流自动化平台，支持 400+ 集成和 400+ AI 节点，企业级流程编排首选。 |
| [Tencent/AI-Infra-Guard](https://github.com/Tencent/AI-Infra-Guard) | Python | 0（+150） | 腾讯开源的全栈 AI 红队测试平台，覆盖 Agent 扫描、MCP 安全和 LLM 对抗评估，填补 AI 安全评测工具空白。 |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 114,667 | AI 驱动的一键短视频生成工具，支持多市场自动素材采集，在内容创作者群体中持续流行。 |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 50,926 | 集成 300+ 助手的 AI 生产力工作室，支持自主智能体，为多模型用户提供了统一入口。 |
| [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | Python | 46,634 | 开源超级 AI 助手，支持多模型、多通道、智能体进化与记忆，轻量易部署。 |
| [iOfficeAI/AionUi](https://github.com/iOfficeAI/AionUi) | TypeScript | 32,207 | 24/7 智能体协作应用，支持 Claude Code、Codex、OpenCode 等 20+ 终端智能体的统一接入与管理。 |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 63,638 | LLM 驱动的股市智能分析系统，支持多市场数据源和自动推送，零成本定时运行。 |

---

### 🧠 大模型 / 训练

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [huggingface/transformers](https://github.com/huggingface/transformers) | Python | 164,345 | 工业标准 LLM 训练与推理框架，支持文本、视觉、音频等多模态模型，生态最为完整。 |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,547 | 主流深度学习框架，持续迭代对 LLM 训练和推理的支持。 |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | Python | 7,327 | 开源 LLM 评测平台，支持 100+ 数据集和多模型评测，国内模型评测主流工具。 |
| [testtimescaling/testtimescaling.github.io](https://github.com/testtimescaling/testtimescaling.github.io) | HTML | 113 | "Test-time scaling" 领域系统性综述仓库，聚焦推理时计算分配策略，反映社区对推理效率优化的前沿关注。 |

---

### 🔍 RAG / 知识库

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 89,046 | 领先的开源 RAG 引擎，融合 Agent 能力，支持复杂文档解析和知识检索，企业级 RAG 首选方案之一。 |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | 63,836 | 智能体通用记忆层，跨会话持久化 AI 上下文，解决 Agent 记忆碎片化痛点。 |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | JavaScript | 91,534 | 为 Claude Code 等智能体提供跨会话持久记忆，自动压缩历史并注入相关上下文，生态兼容性极强。 |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | 35,295 | 向量无依赖的文档索引方案，基于推理的 RAG，避免向量库开销，适合资源受限场景。 |
| [headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom) | Python | 67,204 | 智能体工具输出压缩层，减少 20%~95% 的 Token 消耗，显著提升编码智能体效率。 |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | Python | 51,802 | 文档智能体和 OCR 平台，支持复杂文档结构解析，RAG 构建的核心基础设施之一。 |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | Go | 45,737 | 高性能云原生向量数据库，支持大规模 ANN 搜索，RAG 和语义检索的基础组件。 |

---

## 三、趋势信号分析

今日热榜最显著的趋势是**终端编码智能体（Terminal Coding Agent）工具链的全面爆发**。OpenAI Codex、Claude Code、ECC、DeepSeek-Reasonix 等编码智能体产品集中涌入热榜，说明该赛道已从概念验证进入大规模工程化应用阶段。与此同时，**"智能体技能/工具链"**成为新热点——skills、superpowers、claude-mem 等项目反映开发者正在追求更精细的 Agent 能力管理。RAG 方向上，**向量库去依赖化**（PageIndex、headroom）和**记忆抽象层**（Mem0、claude-mem）开始兴起，表明社区正从"能不能做 RAG"转向"如何让 RAG 更高效、更智能"。AI 安全（AI-Infra-Guard）和评测（opencompass）项目持续获得关注，也折射出产业端对模型可靠性的重视程度在提升。

---

## 四、社区关注热点

- **[affaan-m/ECC](https://github.com/affaan-m/ECC)** — 24 万星，Agent harness 性能优化系统的标杆，覆盖 Claude Code/Codex/Cursor 等主流智能体，生态兼容性极强，今日热度持续攀升。
- **[anthropics/claude-code](https://github.com/anthropics/claude-code)** — Anthropic 官方终端编码智能体今日开源，伴随 127 今日星，预计将成为 Claude Code 生态的核心项目，值得密切关注后续功能迭代。
- **[infiniflow/ragflow](https://github.com/infiniflow/ragflow)** — 8.9 万星，融合 Agent 能力的 RAG 引擎，在企业文档理解和复杂知识检索场景中表现突出，是 RAG 赛道的重点跟踪项目。
- **[Tencent/AI-Infra-Guard](https://github.com/Tencent/AI-Infra-Guard)** — 腾讯开源的全栈 AI 红队平台，填补了 Agent 安全评估和 LLM 对抗测试的开源工具空白，对企业 AI 落地安全有保障参考意义。
- **[thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)** — 9.1 万星，跨会话智能体记忆方案，解决 Agent 上下文断裂的核心痛点，与 ECC、claude-code 等形成良好的生态互补。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*