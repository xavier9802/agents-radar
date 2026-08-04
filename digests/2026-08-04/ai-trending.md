# AI 开源趋势日报 2026-08-04

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-08-04 03:18 UTC

---



# 🤖 AI 开源趋势日报 | 2026-08-04

---

## 一、今日速览

今日 GitHub AI 开源领域呈现**「本地推理 + Agent 记忆」双主线爆发**态势：AirLLM 以单卡 4GB 推理 70B 模型引发关注（+1,085 stars），DeepSeek 原生推理引擎 ds4 和 Reasonix 同步登榜，反映社区对**轻量化本地 LLM 部署**的强烈需求。同时，Agent 记忆与知识管理成为新热点——TencentDB-Agent-Memory、claude-mem、mem0、Cognee 等项目密集涌现，标志着 AI Agent 生态正从「单次对话」迈向「持久化记忆 + 知识沉淀」阶段。此外，向量数据库赛道竞争加剧，PageIndex 提出「无向量」RAG 新思路，LEANN 实现 97% 存储节省，社区对**成本与隐私**的关注持续升温。

---

## 二、各维度热门项目

### 🔧 AI 基础工具

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 177,716 | 本地多模型推理运行时，今日支持 Kimi-K2.6、GLM-5.2、DeepSeek 等主流开源模型，是本地 LLM 部署的事实标准。 |
| [huggingface/transformers](https://github.com/huggingface/transformers) | Python | 163,303 | Hugging Face 核心框架，支持文本/视觉/音频/多模态模型，是 AI 应用的底层基石。 |
| [lyogavin/airllm](https://github.com/lyogavin/airllm) | Python | —（+1,085 today） | **今日爆款**：单张 4GB 显存 GPU 即可推理 AirLLM 70B，大幅降低本地运行大模型的硬件门槛。 |
| [antirez/ds4](https://github.com/antirez/ds4) | C | —（+384 today） | DeepSeek 4 Flash/PRO 本地推理引擎，支持 Metal/CUDA/ROCm，Redis 作者新作，值得关注。 |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | 30,065（+883 today） | **今日爆款**：DeepSeek 原生终端 AI 编码 Agent，以 prefix-cache 稳定性为核心设计，适合长时间挂机运行。 |
| [0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig) | Rust | 8,158 | Rust 生态的模块化 LLM 应用构建框架，填补 Rust 在 AI 工具链的空白。 |
| [AarambhDevHub/aarambh-studio](https://github.com/AarambhDevHub/aarambh-studio) | Rust | 59 | 纯 Rust + Candle 从零实现 Decoder-only LLM，支持 MoE/量化/长程工具 Agent，技术实验价值高。 |
| [paulburgess1357/nvim-mcp](https://github.com/paulburgess1357/nvim-mcp) | Python | 60 | MCP 服务器将 Neovim 接入 AI Agent，无需插件即可双向通信，Vim 用户福音。 |

---

### 🤖 AI 智能体/工作流

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory) | TypeScript | —（+1,090 today） | **今日爆款**：腾讯开源的 Agent 记忆中枢，将对话/文档/代码沉淀为四种可复用记忆资产（Chat/Skill/LLM-Wiki/Code-Graph），支持跨 Agent 共享。 |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | 62,434 | 通用 Agent 记忆层，支持持久化跨会话记忆，是当前 Agent 记忆赛道的代表性项目。 |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | JavaScript | 89,448 | 为 Claude Code 等 Agent 提供跨会话持久化上下文，自动压缩并注入相关记忆，解决 Agent "失忆"痛点。 |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Python | 29,742 | 开源 AI 记忆平台，基于知识图谱实现 Agent 长期记忆，适合复杂任务场景。 |
| [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | Python | 185,795 | 最早的自主 Agent 项目之一，持续迭代，社区基数庞大。 |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | Python | 224,970 | 伴随用户成长的自我进化 Agent，强调技能与经验的持续积累。 |
| [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | Python | 46,297 | 开源超级 AI 助手，支持多模型/多通道，具备自进化记忆与知识库能力，原 chatgpt-on-wechat 演进而来。 |
| [livekit/agents](https://github.com/livekit/agents) | Python | —（+148 today） | 实时语音 AI Agent 框架，支持多模态交互（语音+视频），适合构建语音助手类应用。 |
| [HKUDS/nanobot](https://github.com/HKUDS/nanobot) | Python | 46,587 | 超轻量级自托管个人 AI Agent 框架，含 WebUI/工具/MCP/多 Agent 工作流，适合资源受限场景。 |
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | Python | 107,768 | 让 AI Agent 具备浏览器操控能力，实现网页自动化任务，是 Agent 工具链的关键组件。 |
| [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) | Python | —（+1,057 today） | **今日新秀**：给 AI Agent 装上"眼睛"，通过单 CLI 读取 Twitter/Reddit/YouTube/GitHub 等内容，零 API 费用。 |
| [zhaoxuya520/reverse-skill](https://github.com/zhaoxuya520/reverse-skill) | PowerShell | —（+2,446 today） | **今日最高增速**：AI 驱动的安全研究技能路由包，自动路由 + 按需自举工具链 + 自进化知识库，支持 Claude Code/Cursor 等主流编码 Agent。 |
| [santifer/career-ops](https://github.com/santifer/career-ops) | JavaScript | 62,677 | 开源 AI 求职助手：扫描职位、结构化评估、定制简历、追踪投递，运行于本地 AI 编码 CLI。 |

---

### 📦 AI 应用

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [jamiepine/voicebox](https://github.com/jamiepine/voicebox) | TypeScript | —（+412 today） | **今日新秀**：开源 AI 语音工作室，支持语音克隆、口播生成、内容创作，一站式语音 AI 应用。 |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 101,431 | 一键 AI 短视频生成：输入主题/关键词，自动产出高清短视频，国内热门应用项目。 |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | 42,818 | AI 生成原生 PowerPoint：支持形状/动画/数据图表/音频旁白，可直接套用自定义 .pptx 模板。 |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 49,367 | AI 生产力工作室，集成智能对话、自主 Agent 与 300+ 助手，统一接入前沿 LLM。 |
| [zhuyilin/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 59,957 | LLM 驱动的多市场股票智能分析系统，支持多源行情、实时新闻、决策看板与自动推送，可零成本定时运行。 |
| [HKUDS/Vibe-Trading](https://github.com/HKUDS/Vibe-Trading) | Python | 29,475 | "氛围交易"个人交易 Agent，将 LLM 能力应用于量化交易场景。 |
| [shiyu-coder/Kronos](https://github.com/shiyu-coder/Kronos) | Python | —（+200 today） | **今日新秀**：金融市场语言基础模型，面向金融领域的专用 LLM，细分赛道值得关注。 |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | Python | 147,759 | 用户友好的本地 AI 聊天界面，支持 Ollama/OpenAI API 等多种模型后端。 |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 86,752 | 开源 RAG 引擎，融合检索增强与 Agent 能力，提供 superior 上下文层。 |
| [FlowiseAI/Flowise](https://github.com/FlowiseAI/Flowise) | TypeScript | 55,126 | 可视化构建 AI Agent 与工作流，低代码友好的 Agent 开发平台。 |
| [firecrawl/pdf-inspector](https://github.com/firecrawl/pdf-inspector) | Rust | —（+1,699 today） | **今日新秀**：快速 Rust PDF 解析库，智能区分扫描件与文本 PDF，为 RAG/Agent 提供高质量数据预处理。 |
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | TypeScript | 160,180 | 大规模网页搜索/爬取/交互 API，为 AI Agent 提供实时网络上下文能力。 |

---

### 🧠 大模型/训练

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | 196,777 | Google 开源机器学习框架，工业界基石，持续活跃。 |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,166 | Meta 开源深度学习框架，研究与应用双栖，生态最为繁荣。 |
| [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | Python | 60,185 | YOLO 系列目标检测/分割/姿态估计工具包，计算机视觉领域使用最广的开源项目之一。 |
| [scikit-learn/scikit-learn](https://github.com/scikit-learn/scikit-learn) | Python | 66,866 | Python 经典机器学习库，覆盖分类/回归/聚类等传统 ML 任务。 |
| [keras-team/keras](https://github.com/keras-team/keras) | Python | 64,217 | 面向人类的高层深度学习 API，降低模型构建门槛。 |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | Python | 7,267 | 开源 LLM 评测平台，支持 Llama3/Mistral/Qwen/GLM 等 100+ 数据集，是国内重要的模型评测基础设施。 |
| [skyzh/tiny-llm](https://github.com/skyzh/tiny-llm) | Python | 4,436 | 面向 Apple Silicon 的轻量级 LLM 推理教学项目，从零构建 vLLM + Qwen，适合系统工程师学习。 |
| [thinkwee/AwesomeOPD](https://github.com/thinkwee/AwesomeOPD) | — | 797 | On-Policy Distillation（在策略蒸馏）资源合集，聚焦大模型高效微调方向。 |
| [chrisliu298/awesome-llm-unlearning](https://github.com/chrisliu298/awesome-llm-unlearning) | — | 617 | 大模型机器遗忘（Machine Unlearning）资源库，关注模型安全与合规的新兴方向。 |

---

### 🔍 RAG / 知识库

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | Python | 51,357 | 文档 Agent 与 OCR 平台，RAG 领域领先框架，支持复杂文档解析与检索。 |
| [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps) | Python | 130,260 | 100+ AI Agent 与 RAG 应用开源合集，是入门学习的高质量资源库。 |
| [Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) | JavaScript | 64,303 | 本地优先的 RAG/Agent 全栈平台，"停止出租你的智能"，强调数据私有化。 |
| [meilisearch/meilisearch](https://github.com/meilisearch/meilisearch) | Rust | 58,844 |  lightning-fast 搜索 API，支持 AI 驱动混合搜索，RAG 检索层的有力补充。 |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | Go | 45,497 | 云原生高性能向量数据库，支持海量向量 ANN 搜索，国产开源代表。 |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Rust | 33,761 | 高性能向量数据库与搜索引擎，云原生架构，适合生产级 RAG 部署。 |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | 34,998 | **今日新秀**：提出"无向量"RAG 新思路，基于推理而非向量搜索，减少存储依赖。 |
| [StarTrail-org/LEANN](https://github.com/StarTrail-org/LEANN) | Python | 12,763 | 个人设备上的全数据 RAG 应用，实现 97% 存储节省，兼顾隐私与效率。 |
| [NirDiamant/RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) | Jupyter Notebook | 28,928 | RAG 高级技巧教程库，每个技术附详细 Notebook，适合深入学习。 |
| [lancedb/lancedb](https://github.com/lancedb/lancedb) | Rust | 11,066 | 嵌入式多模态检索库，开发者友好，适合轻量级 RAG 场景。 |
| [headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom) | Python | 64,410 | Token 压缩代理，减少 20% 编码 Agent token、60-95% JSON token，直接降低 RAG 成本。 |
| [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) | Python | 101,911 | 将代码库/文档/SQL/配置/PDF 转为可查询知识图谱，支持 Claude Code/Cursor/Codex，本地确定性 AST 解析。 |
| [alibaba/zvec](https://github.com/alibaba/zvec) | C++ | 15,370 | 阿里开源的轻量级进程内向量数据库，极致性能，适合嵌入式场景。 |
| [neuml/txtai](https://github.com/neuml/txtai) | Python | 12,783 | 一体化 AI 框架，集语义搜索/LLM 编排/语言模型工作流于一体。 |
| [langchain4j/langchain4j](https://github.com/langchain4j/langchain4j) | Java | 12,773 | Java 生态的 LangChain 实现，支持 MCP/工具调用/RAG，无缝集成 Spring Boot/Quarkus。 |

---

## 三、趋势信号分析

**1. 本地推理与轻量部署成为主流方向。** 今日 Trending 前三大热点（AirLLM、ds4、Reasonix）均围绕"更低硬件门槛运行更强模型"展开，反映社区对云 API 依赖的焦虑与对本地化、隐私化部署的强烈诉求。antirez （Redis 作者）入局 DeepSeek 推理引擎，进一步提升了该方向的关注度。

**2. Agent 记忆层正在经历"基建化"竞争。** TencentDB-Agent-Memory、claude-mem、mem0、Cognee 四个项目同日内外齐发，说明 Agent 从"无状态对话"向"持久化记忆+知识沉淀"演进已成为共识，记忆层正成为 Agent 框架的必争之地。

**3. RAG 进入"降本增效"深水区。** PageIndex 的"无向量"方案与 LEANN 的 97% 存储节省，叠加 headroom 的 Token 压缩，共同指向一个信号：社区不再满足于"能跑 RAG"，而是追求极致的存储效率与推理成本优化，这是 RAG 从实验走向生产化的关键里程碑。

**4. 安全/逆向 Agent 工具首次登上热榜。** reverse-skill 今日以 +2,446 stars 领跑全榜，是 AI+安全垂直领域的突破，预示 AI Agent 在专业领域（安全研究、合规审计）的应用正在加速渗透。

---

## 四、社区关注热点

- **[lyogavin/airllm](https://github.com/lyogavin/airllm)** — 单卡 4GB 推理 70B 模型，门槛突破，适合边缘设备与个人开发者。
- **[TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory)** — 大厂入局 Agent 记忆层，四种记忆资产模型具有工程参考价值。
- **[zhaoxuya520/reverse-skill](https://github.com/zhaoxuya520/reverse-skill)** — 今日增速第一（+2,446），AI+安全研究垂直赛道的首个爆款项目。
- **[VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex)** — "无向量"RAG 新思路，挑战主流向量检索范式，技术实验价值高。
- **[esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix)** — 针对 DeepSeek 优化的终端 Agent，prefix-cache 稳定性设计解决长时间运行痛点。
- **[headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom)** — Token 压缩解决 RAG 成本瓶颈，直接回应开发者对 token 费用的焦虑。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*