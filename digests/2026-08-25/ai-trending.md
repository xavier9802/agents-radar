# AI 开源趋势日报 2026-08-25

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-08-25 01:39 UTC

---



# 🤖 AI 开源趋势日报
**日期：2026-08-25**

---

## 1. 今日速览

今日 AI 开源领域最引人注目的动向是 **OpenAI Codex 客户端正式开源**，当日即斩获近 2000 stars，标志着 OpenAI 在终端 coding agent 赛道的全面入场。与此同时，**Claude Code 生态迎来爆发式增长**，从 Karpathy 经验提炼的 agent skills、社区插件市场到本地记忆持久化方案，"围绕 Claude Code 构建生产力的第二大脑"成为今日最热主题。此外，**Rust 语言在 AI 基础设施层的渗透持续加速**，从向量数据库到 coding agent 均有亮眼项目涌现。

---

## 2. 各维度热门项目

### 🔧 AI 基础工具

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [openai/codex](https://github.com/openai/codex) | Rust | ⭐0（+1,994 today） | OpenAI 官方轻量级终端 coding agent，以 Rust 重写，代表 OpenAI 正式进军本地 coding agent 市场，对 Claude Code 形成直接竞争。 |
| [f/prompts.chat](https://github.com/f/prompts.chat) | HTML | ⭐167,862 | 原名 Awesome ChatGPT Prompts，社区驱动的提示词共享平台，支持自托管，是提示词工程领域的标志性开源项目。 |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | ⭐179,355 | 本地运行 LLM 的入门首选框架，支持 DeepSeek、Qwen、Gemma 等主流模型，本地 AI 部署的基础设施层核心项目。 |
| [freellmapi](https://github.com/tashfeenahmed/freellmapi) | TypeScript | ⭐0（+174 today） | 聚合 34 个免费 LLM 提供商、635 个端点的统一 OpenAI 兼容网关，智能路由+自动故障转移，降低多模型接入门槛。 |
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Go | ⭐100,705 | Claude Code skill，通过"原始人风格"对话将 token 消耗削减 65%，反映社区对 agent 成本优化的强烈需求。 |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | ⭐35,122 | DeepSeek 原生 terminal coding agent，以 prefix-cache 稳定性为设计核心，适合长时间运行任务场景。 |

---

### 🤖 AI 智能体/工作流

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | Python | ⭐235,827 | NousResearch 推出的"与你共同成长的 agent"，今日 Trending 新增 896 stars，反映开源模型厂商向 agent 层延伸的趋势。 |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | JavaScript | ⭐242,938 | Agent harness 性能优化系统，覆盖 skills、记忆、安全与研究，支持 Claude Code/Codex/Cursor 等多平台，是当前最全面的 agent 优化工具。 |
| [shareAI-lab/learn-claude-code](https://github.com/shareAI-lab/learn-claude-code) | Python | ⭐75,174 | "Bash is all you need" 理念打造的 nano Claude Code agent harness，从零构建，是学习 agent 原理的最佳实战教程。 |
| [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | Python | ⭐46,657 | 开源超级 AI 助手 & Agent Harness，支持多模型/多通道，具备记忆与知识自进化能力，原 chatgpt-on-wechat 升级版本。 |
| [HKUDS/nanobot](https://github.com/HKUDS/nanobot) | Python | ⭐47,352 | 超轻量级开源自托管个人 AI agent 框架，支持 WebUI、工具调用、MCP 及多智能体工作流，适合嵌入式场景。 |
| [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | Python | ⭐186,853 | 早期 autonomous agent 标杆项目，持续维护中，代表 agent 自动化方向的长期积累。 |
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | Python | ⭐110,377 | 让 AI agent 能够操控浏览器的工具库，是 web 自动化场景下 agent 能力的关键基础设施。 |
| [Hmbown/CodeWhale](https://github.com/Hmbown/CodeWhale) | Rust | ⭐40,852 | Rust 编写的开源 terminal coding agent，强调社区驱动持续改进，体现 Rust 在 coding agent 领域的崛起。 |

---

### 📦 AI 应用

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | ⭐51,009 | AI 生产力工作室，集成智能聊天、自主 agent 及 300+ 助手，统一接入前沿 LLM，是桌面端 AI 应用的有力竞争者。 |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | ⭐49,046 | AI 生成原生 PowerPoint，支持原生形状/过渡/动画、数据图表及音频旁白，是文档生成类 AI 应用的典型代表。 |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | ⭐63,780 | LLM 驱动的多市场股票智能分析系统，支持零成本定时运行，反映 AI+金融垂直场景的持续热度。 |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | ⭐115,978 | 一键 AI 短视频生成工具，自动化工作流驱动，在内容创作领域具有广泛用户基础。 |
| [santifer/career-ops](https://github.com/santifer/career-ops) | JavaScript | ⭐68,157 | 开源 AI 求职平台，扫描职位、生成 A-H 评级报告、定制简历，本地运行于 Claude Code/Codex 等 CLI agent。 |
| [MadsLorentzen/ai-job-search](https://github.com/MadsLorentzen/ai-job-search) | Python | ⭐0（+434 today） | 基于 Claude Code 构建的 AI 求职框架，支持岗位评估、简历定制、面试准备全流程，今日新增 434 stars。 |
| [bojieli/ai-agent-book](https://github.com/bojieli/ai-agent-book) | Python | ⭐41,787 | 《深入理解 AI Agent》开源教程，配套完整代码，是学习 agent 设计原理的系统性资料。 |
| [iOfficeAI/AionUi](https://github.com/iOfficeAI/AionUi) | TypeScript | ⭐32,251 | 24/7 开源 Cowork 应用，支持 Claude Code/Codex/Hermes 等 20+ CLI agent，提供 Web 界面与团队协作能力。 |

---

### 🧠 大模型/训练

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [huggingface/transformers](https://github.com/huggingface/transformers) | Python | ⭐164,404 | Hugging Face 旗舰模型框架，支持文本/视觉/音频/多模态模型的推理与训练，是 LLM 生态的事实标准。 |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | ⭐197,561 | Google 开源的通用深度学习框架，仍是工业界大规模 ML 部署的重要基石。 |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | ⭐102,578 | Meta 主导的深度学习框架，因动态图与社区生态成为 LLM 研究与开发的首选平台。 |
| [jingyaogong/minimind](https://github.com/jingyaogong/minimind) | Python | ⭐54,974 | 2 小时内从 0 训练 64M 参数 LLM 的教学项目，是理解 LLM 训练全流程的最佳入门实践。 |
| [rasbt/LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch) | Jupyter Notebook | ⭐103,688 | 从零用 PyTorch 实现 ChatGPT 级 LLM 的系列教程，社区影响力持久，是 LLM 教育的经典资源。 |
| [rohitg00/ai-engineering-from-scratch](https://github.com/rohitg00/ai-engineering-from-scratch) | Python | ⭐48,308 | "学会·构建·交付"三位一体的 AI 工程实战教程，今日 Trending 新增 349 stars，反映开发者对落地能力的迫切需求。 |
| [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | Python | ⭐60,928 | YOLO26/YOLO11/v8 系列目标检测与分割模型，视觉 AI 领域的工业级标准工具。 |

---

### 🔍 RAG/知识库

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | Python | ⭐51,852 | 文档 agent 与 OCR 平台标杆，RAG 应用开发的核心框架，生态成熟度领先。 |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | ⭐89,169 | 融合 RAG 与 Agent 能力的开源检索引擎，支持深度文档解析，是企业级 RAG 落地的热门选择。 |
| [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps) | Python | ⭐133,946 | 收录 100+ AI Agent、Agent Skills 与 RAG 应用的开源汇总，是追踪 RAG 应用生态的重要资源。 |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | ⭐63,970 | 通用 AI agent 记忆层，支持跨会话持久化，解决 agent 上下文丢失的核心痛点。 |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | JavaScript | ⭐91,727 | 为 Claude Code/Codex 等 agent 提供跨会话持久上下文，AI 压缩+智能注入，今日新增关注度高。 |
| [HKUDS/LightRAG](https://github.com/HKUDS/LightRAG) | Python | ⭐39,146 | EMNLP2025 论文开源实现，轻量快速的 RAG 系统，在准确性与效率间取得平衡。 |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Python | ⭐30,237 | 开源 AI 记忆平台，基于知识图谱引擎为 agent 提供跨会话持久化长时记忆。 |
| [AGI-OS/AGI-OS](https://github.com/AGI-OS/AGI-OS) | TypeScript | ⭐36,515 | 自托管个人 AI 操作系统，整合 agent 工作流与本地知识管理，代表"个人 AI  OS"的新方向。 |
| [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) | Python | ⭐110,144 | 将代码库/文档/SQL schema 转换为可查询知识图谱，支持 Claude Code/Cursor/Codex，无需向量数据库。 |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | ⭐35,313 | "无向量" RAG 索引方案，基于推理而非向量相似度，代表 RAG 技术的新探索方向。 |

---

## 3. 趋势信号分析

今日 GitHub Trending 榜呈现三大明确信号：**第一，OpenAI Codex 开源引发 coding agent 格局重塑**。作为 OpenAI 首款终端原生 coding agent，Codex 以 Rust 重写且零 stars 起步却单日涌入近 2000 星，与 Claude Code 形成正面竞争，预示 coding agent 赛道将从"封闭生态"走向"开源多极化"。**第二，Claude Code 生态呈现"工具矩阵化"态势**。从 Karpathy 经验提炼的 skills（`andrej-karpathy-skills`，+588 stars）、社区插件市场（`claude-plugins-community`，+489 stars）、到记忆持久化（`claude-mem`，91,727 stars）和知识库构建（`claude-obsidian`，+310 stars），围绕 Claude Code 的工具链正快速丰满，开发者从"使用 agent"转向"围绕 agent 构建工作流"。**第三，Rust 在 AI 基础设施层的渗透速度超预期**。从 Codex 本体、CodeWhale、qdrant 到 Apache Maka，Rust 已成为 coding agent 和向量数据库的首选语言，性能与内存安全的双重优势正推动 AI 基础设施从 Python 单极向多语言生态演进。

---

## 4. 社区关注热点

- **[openai/codex](https://github.com/openai/codex)** — OpenAI 首款开源 terminal coding agent，直接竞争 Claude Code，Rust 实现+零依赖，适合关注 coding agent 赛道演进的开发者。
- **[thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)** — 解决 agent 跨会话记忆丢失的核心痛点，91K stars 且兼容多平台 agent，是构建长期 AI 助手的必要组件。
- **[Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify)** — 无需向量数据库的知识图谱构建工具，本地确定性 AST 解析，代表 RAG 从"向量检索"向"结构化理解"的范式转移。
- **[affaan-m/ECC](https://github.com/affaan-m/ECC)** — 242K stars 的 agent harness 性能优化系统，覆盖 skills/记忆/安全/研究，是当前最全面的 Claude Code/Codex 优化工具。
- **[VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex)** — 35K stars 的"无向量 RAG"新方案，基于推理而非相似度检索，代表 RAG 技术的创新探索方向。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*