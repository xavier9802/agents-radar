# AI 开源趋势日报 2026-08-18

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-08-18 01:38 UTC

---



# 📊 AI 开源趋势日报 — 2026-08-18

---

## 1. 今日速览

今日 GitHub AI 开源领域最显著的信号是**Agent 记忆与上下文管理**成为爆发焦点——从 `ai-memory`、`claude-mem`、`mem0` 到 `cognee`，多个项目同日涌入热榜，说明社区正在从"如何让 Agent 执行任务"转向"如何让 Agent 持续学习与跨会话协作"。其次，**AI 视频生成工具** `MoneyPrinterTurbo` 今日新增 1,189 stars 领跑热榜，反映多模态内容生成的大众化需求持续升温。同时，**AI 安全与渗透测试**方向首次密集出现（`strix`、`Anthropic-Cybersecurity-Skills`），标志 LLM 安全工程化已进入工具落地阶段。

---

## 2. 各维度热门项目

### 🔧 AI 基础工具

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 178,814 | 本地运行 LLM 的最流行框架，支持多模型一键部署，持续扩展新模型支持。 |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Python | 89,283 | 高吞吐 LLM 推理引擎，PagedAttention 技术领先，是生产部署的核心基础设施。 |
| [jundot/omlx](https://github.com/jundot/omlx) | Python | 78（+78 today） | macOS 菜单栏管理的 LLM 推理服务器，支持持续批处理与 SSD 缓存，专为 Apple Silicon 优化。 |
| [AlexsJones/llmfit](https://github.com/AlexsJones/llmfit) | Rust | 198（+198 today） | 一条命令检测数百个模型在本地硬件的适配情况，降低 LLM 部署门槛。 |
| [akitaonrails/ai-memory](https://github.com/AlexsJones/llmfit) | Rust | 207（+207 today） | 面向 Agent CLI 的长期记忆解决方案，支持跨 Agent 厂商的上下文交接，今日新上榜即获关注。 |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | JavaScript | 240,717 | Agent harness 性能优化系统，覆盖 Claude Code、Codex、Cursor 等，聚焦技能/记忆/安全工程。 |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | 34,685 | DeepSeek 原生终端 AI 编码 Agent，基于 prefix-cache 稳定性设计，适合长时间运行。 |
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Go | 98,764 | Claude Code 技能，用"穴居人模式"削减 65% token 消耗，在成本控制场景下受关注。 |
| [0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig) | Rust | 8,302 | Rust 原生模块化 LLM 应用框架，适合追求性能和类型安全的开发者。 |
| [Mirrowel/LLM-API-Key-Proxy](https://github.com/Mirrowel/LLM-API-Key-Proxy) | Python | 543 | 统一 LLM 网关，支持 OpenAI/Anthropic 等多提供商兼容接口与智能负载均衡。 |

---

### 🤖 AI 智能体/工作流

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [langchain-ai/langchain](https://github.com/langchain-ai/langchain) | Python | 144,417 | Agent 工程平台标杆，工具链与模型抽象最完整，仍是生态基石。 |
| [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | Python | 186,657 | 自主 AI Agent 先驱项目，持续迭代，代表通用 Agent 愿景方向。 |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | Python | 232,049 | "与你共同成长的 Agent"，强调持续学习与自我演化，获大量关注。 |
| [shareAI-lab/learn-claude-code](https://github.com/shareAI-lab/learn-claude-code) | Python | 74,493 | 从零构建类 Claude Code Agent Harness 的教学仓库，推动开发者理解 Agent 内部机制。 |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | JavaScript | 91,024 | 跨会话持久化 Agent 上下文，AI 压缩+注入机制实现"记忆延续"，今日多项目同期上榜验证趋势。 |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | 63,470 | 通用 Agent 记忆层，抽象出跨平台记忆管理 API，是记忆基础设施的代表。 |
| [FlowiseAI/Flowise](https://github.com/FlowiseAI/Flowise) | TypeScript | 55,379 | 可视化构建 AI Agent 工作流，降低 Agent 开发门槛，适合非代码用户。 |
| [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) | Python | 72,553 | 赋予 Agent "眼睛"，一行 CLI 访问 Twitter/Reddit/YouTube/GitHub 等平台，零 API 费用。 |
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | Python | 109,536 | 让 Agent 可自动化操作网页，是 Web 交互类 Agent 的核心基础设施。 |
| [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | Python | 46,534 | 开源超级 AI 助手，支持多模型/多渠道、记忆自进化， formerly chatgpt-on-wechat。 |
| [Hmbown/CodeWhale](https://github.com/Hmbown/CodeWhale) | Rust | 40,828 | 社区驱动的 Rust Agent Harness，填补 Rust 生态 Agent 工具空白。 |
| [mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills) | Python | 198（+198 today） | 817 项结构化 AI 安全技能，映射 MITRE ATT&CK/NIST 等 6 大框架，Agent 安全工程化新标杆。 |

---

### 📦 AI 应用

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 106,132（+1,189 today） | AI 一键生成高清短视频，今日 Trending 榜首，多模态内容生成大众化需求爆发的标志。 |
| [usestrix/strix](https://github.com/usestrix/strix) | Python | 598（+598 today） | 开源 AI 渗透测试工具，帮助发现并修复应用漏洞，AI 安全应用新玩家。 |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 63,185 | LLM 驱动的多市场股票智能分析系统，支持零成本定时运行，垂直金融场景落地代表。 |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | 47,509 | AI 生成原生 PowerPoint 演示文稿，支持动画、图表、音频旁白，办公自动化利器。 |
| [santifer/career-ops](https://github.com/santifer/career-ops) | JavaScript | 64,693（+218 today） | AI 开源求职助手，扫描职位、结构化评分、定制简历，全程本地 CLI 运行，今日持续增星。 |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 50,670 | AI 生产力工作室，聚合 300+ 助手与自主 Agent，统一接入前沿 LLM。 |
| [HKUDS/nanobot](https://github.com/HKUDS/nanobot) | Python | 47,106 | 超轻量级自托管个人 AI Agent 框架，支持 WebUI、MCP、多 Agent 工作流，适合边缘部署。 |

---

### 🧠 大模型/训练

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | 196,990 | 工业级 ML 框架基石，持续维护，仍是大规模训练首选之一。 |
| [huggingface/transformers](https://github.com/huggingface/transformers) | Python | 164,196 | SOTA 模型定义框架，文本/视觉/音频多模态覆盖，生态核心。 |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,441 | 动态计算图深度学习框架，研究到生产全线覆盖。 |
| [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | Python | 60,700 | YOLO 系列目标检测/分割/姿态估计权威实现，计算机视觉基石。 |
| [scikit-learn/scikit-learn](https://github.com/scikit-learn/scikit-learn) | Python | 66,963 | Python ML 经典库，传统 ML 任务首选。 |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | Python | 7,311 | 开源 LLM 评估平台，支持 Llama3/Qwen/GLM/Claude 等百+数据集评测，模型评估基础设施。 |

---

### 🔍 RAG/知识库

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [langgenius/dify](https://github.com/langgenius/dify) | TypeScript | 152,727 | Agentic RAG 工作流平台，支持云端/VPC/自托管，企业级落地首选。 |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | Python | 149,054 | 开源 WebUI，支持 Ollama/OpenAI API，本地 LLM 交互入口。 |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 88,685 | RAG + Agent 融合引擎，文档理解深度处理，中文场景表现突出。 |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | Go | 45,666 | 云原生向量数据库，ANN 搜索性能标杆，大规模 RAG 部署首选。 |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Rust | 34,031 | 高性能向量数据库，Rust 原生，嵌入式与分布式双模式。 |
| [meilisearch/meilisearch](https://github.com/meilisearch/meilisearch) | Rust | 58,996 | 闪电级 hybrid search 引擎，AI 语义+关键词融合搜索，开发者友好。 |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | Python | 51,711 | 文档 Agent 与 OCR 平台，RAG 工具链核心组件。 |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | 35,223 | 无向量库的 RAG 新范式，基于 Reasoning 的文档索引，挑战传统向量方案。 |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Python | 30,086 | 开源 AI 记忆平台，基于知识图谱的持久化 Agent 记忆，跨会话知识管理。 |
| [NirDiamant/RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) | Jupyter Notebook | 29,084 | RAG 高级技术教程合集，每个技术带详细 Notebook，学习资源标杆。 |
| [alibaba/zvec](https://github.com/alibaba/zvec) | C++ | 15,453 | 阿里巴巴轻量级嵌入式向量数据库，高性能内聚方案。 |

---

## 3. 趋势信号分析

**Agent 记忆基础设施正在形成独立赛道。** 今日热榜中 `ai-memory`（+207）、`claude-mem`（91K stars）、`mem0`（63K stars）、`cognee`（30K stars）四个记忆类项目同时活跃，表明社区共识已从"Agent 执行能力"转向"Agent 持续学习能力"。跨会话记忆、知识图谱记忆、压缩注入记忆等细分方向同时涌现，说明该领域仍处于快速分化期，尚未形成统一标准。

**AI 安全工程化进入工具落地阶段。** `strix`（+598 今日）和 `Anthropic-Cybersecurity-Skills`（+198 今日）同日登榜，且后者映射了 MITRE ATT&CK、NIST CSF 2.0 等 6 大安全框架，标志着 AI 安全从"研究概念"走向"可执行技能库"。结合 `ECC`（240K stars）对 Agent harness 安全的聚焦，安全正成为 Agent 工程不可绕过的模块。

**多模态内容生成持续出圈。** `MoneyPrinterTurbo` 今日 +1,189 stars 领跑热榜，叠加 `ppt-master`（47K stars）等办公自动化 AI 工具的热度，反映 Agent 正从"编码助手"向"通用生产力工具"扩展，视频/PPT 等富媒体生成是下一波大众化突破口。

---

## 4. 社区关注热点

- **🔥 `harry0703/MoneyPrinterTurbo`** — 今日 stars 增量最高（+1,189），AI 视频生成工具大众化需求明确，适合内容创作者和短视频从业者关注。
- **🧠 `akitaonrails/ai-memory`** — 新上榜即获 207 stars，Rust 实现的跨 Agent 记忆交接方案，填补了 Agent 持久化记忆的工具空白。
- **🛡️ `mukul975/Anthropic-Cybersecurity-Skills`** — 817 项结构化安全技能映射 6 大框架，AI 安全工程化的里程碑项目，安全团队和 Agent 开发者应重点关注。
- **⚡ `affaan-m/ECC`** — 240K stars 的 Agent harness 性能优化系统，覆盖 Claude Code/Codex/Cursor 等主流工具，是提升 Agent 效率的实用工程方案。
- **🌐 `Panniantong/Agent-Reach`** — 赋予 Agent 全网浏览能力（Twitter/Reddit/YouTube/GitHub 等），零 API 费用，适合需要实时信息的 Agent 应用场景。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*