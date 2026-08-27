# AI 开源趋势日报 2026-08-27

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-08-27 08:44 UTC

---



# 🤖 AI 开源趋势日报 — 2026-08-27

---

## 一、今日速览

今日 GitHub AI 开源圈呈现三大主线：**Claude Code 生态全面爆发**，Anthropic 官方插件目录与社区插件库同日登榜，带动"Agent Skills"标准化成为新热点；**本地化/开源大模型运行层持续升温**，Ollama 突破 17.9 万星，国产模型（Kimi、GLM、DeepSeek 等）首次纳入支持列表；**AI 职业生产力工具**异军突起，AI 求职、股票分析、PPT 生成等垂直应用集体上榜，社区对"AI 替代人类工作"的讨论进入白热化阶段。

---

## 二、各维度热门项目

### 🔧 AI 基础工具

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 179,535 | 本地大模型运行框架，今日支持 Kimi-K2.6、GLM-5.2、DeepSeek 等国产模型，生态扩展加速。 |
| [huggingface/transformers](https://github.com/huggingface/transformers) | Python | 164,489 | Hugging Face 核心 ML 框架，支持文本/视觉/音频多模态，仍是开源 AI 基础设施基石。 |
| [langchain-ai/langchain](https://github.com/langchain-ai/langchain) | Python | 145,098 | Agent 工程平台，工具调用与 RAG 编排的核心抽象层，保持生态最大规模。 |
| [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | Python | 40,531 | 构建弹性多步 Agent 工作流，图结构编排能力正成为复杂 Agent 项目标配。 |
| [langchain4j/langchain4j](https://github.com/langchain4j/langchain4j) | Java | 12,962 | Java 生态 LangChain 实现，支持 MCP、Spring Boot 集成，企业级 AI 应用首选。 |
| [0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig) | Rust | 8,418 | Rust 语言构建模块化 LLM 应用框架，填补 Rust AI 开发工具链空白。 |
| [freestylefly/awesome-gpt-image-2](https://github.com/freestylefly/awesome-gpt-image-2) | JavaScript | —（+4,050 今日） | GPT-Image2 工业级提示词引擎，530+ 案例逆向工程，提示词工程细分赛道新星。 |
| [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | JavaScript | —（+1,598 今日） | 让 AI Agent 像"最懒资深工程师"一样思考，极致压缩代码量，理念新颖。 |

---

### 🤖 AI 智能体/工作流

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | Python | 186,917 | 开源自主 Agent 鼻祖，持续迭代中，仍是社区学习 Agent 架构的首选参考。 |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | Python | 237,070 | 成长型 Agent 框架，"随你一起成长"设计理念，NousResearch 社区影响力显著。 |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | JavaScript | 243,591 | Agent Harness 性能优化系统，覆盖 Skills、记忆、安全，定位 Claude Code/Codex 增强层。 |
| [shareAI-lab/learn-claude-code](https://github.com/shareAI-lab/learn-claude-code) | Python | 75,427 | 从零实现类 Claude Code Agent Harness，Bash 实现，是学习 Agent 原理的绝佳教材。 |
| [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | Python | 46,698 | 前 ChatGPT-WeChat 升级版，支持多模型、多通道、技能自进化，国内用户基数大。 |
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | Python | 111,276（+149 今日） | 让 AI Agent 操控浏览器，11 万星标杆项目，Web 自动化场景首选。 |
| [CopilotKit/CopilotKit](https://github.com/CopilotKit/CopilotKit) | TypeScript | 37,068 | 前端 Agent 组件栈，支持 React/Angular/移动端，定义 AG-UI 协议，开发者友好。 |
| [anthropic/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Python | —（+308 今日） | **Anthropic 官方插件目录**，Claude Code 插件生态首次官方背书，信号意义强。 |
| [anthropic/claude-plugins-community](https://github.com/anthropics/claude-plugins-community) | Python | —（+538 今日） | Claude Code 社区插件市场只读镜像，插件提交入口开放，生态繁荣标志。 |
| [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | — | —（+242 今日） | 1000+ Agent Skills 精选合集，兼容 Claude Code/Codex/Gemini CLI/Cursor，标准化推动者。 |
| [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | Python | —（+138 今日） | 面向科学家的 163 个验证 Skills，覆盖生物/化学/药物发现，垂直领域深耕典范。 |

---

### 📦 AI 应用

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 117,050 | AI 一键生成短视频，自动化工作流落地典范，用户量持续走高。 |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 51,127 | 统一接入 300+ 助手的前端 AI 生产力工作室，多模型聚合体验优秀。 |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | 49,740 | AI 生成原生 PPT，支持动画/图表/音频，Office 生态 AI 化典型应用。 |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 64,072 | LLM 驱动多市场股票分析，零成本定时运行，金融 AI 应用热门案例。 |
| [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) | Python | 75,778 | 让 Agent "看见"全网：Twitter/Reddit/YouTube/GitHub/B站一键读取，零 API 费用，信息获取利器。 |
| [MadsLorentzen/ai-job-search](https://github.com/MadsLorentzen/ai-job-search) | Python | —（+1,300 今日） | **AI 求职框架**，自动评估岗位、定制简历、生成求职信，今日爆增 1300 star，就业焦虑催生需求。 |
| [santifer/career-ops](https://github.com/santifer/career-ops) | JavaScript | 68,732 | 开源 AI 求职工具，A-H 分级评估+CV 定制，与上述项目同赛道竞争。 |
| [AgriciDaniel/claude-obsidian](https://github.com/AgriciDaniel/claude-obsidian) | Python | —（+810 今日） | Obsidian+Claude Code 结合的第二大脑，Markdown 知识图谱，个人知识管理新玩法。 |
| [tt-a1i/archify](https://github.com/tt-a1i/archify) | JavaScript | —（+1,035 今日） | AI 架构/工作流/数据流图表工具，自包含 HTML 输出，设计工程师刚需工具。 |

---

### 🧠 大模型/训练

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | 197,716 | Google 开源 ML 框架，工业界基石，持续维护。 |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,612 | Meta 主导的深度学习框架，动态计算图优势明显，研究界首选。 |
| [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | Python | 61,004 | YOLO 系列目标检测全家桶（v8/v11/YOLO26），视觉 AI 部署首选。 |
| [jingyaogong/minimind](https://github.com/jingyaogong/minimind) | Python | 55,063 | 2 小时训练 64M 参数 LLM 入门教程，AI 初学者必读实践项目。 |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | Python | 7,370 | 国产 LLM 评测平台，支持 Llama3/GPT-4/DeepSeek 等 100+ 数据集，评测标准化工具。 |
| [scikit-learn/scikit-learn](https://github.com/scikit-learn/scikit-learn) | Python | 67,068 | Python 经典 ML 库，传统机器学习任务标准选择。 |
| [keras-team/keras](https://github.com/keras-team/keras) | Python | 64,217 | 高层深度学习 API，上手门槛低，教学与快速原型首选。 |
| [rohitg00/ai-engineering-from-scratch](https://github.com/rohitg00/ai-engineering-from-scratch) | Python | 49,804（+838 今日） | 从零构建 AI 工程完整链路教程，"Learn it. Build it. Ship it."理念，教育内容需求旺盛。 |

---

### 🔍 RAG/知识库

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | TypeScript | 172,972 | 大规模网页搜索/抓取/交互 API，RAG 数据摄取层核心基础设施。 |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | Python | 150,069 | 本地优先 AI 对话界面，支持 Ollama/OpenAI，开源 AI 应用入口级产品。 |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 89,369 | 国产 RAG 引擎，融合 Agent 能力，中文场景优化，RAG 落地首选之一。 |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | 64,157 | 通用 Agent 记忆层，跨会话持久记忆，解决 Agent"失忆"核心痛点。 |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | Python | 51,888 | 文档 Agent 与 OCR 平台，RAG 索引构建最强工具之一。 |
| [HKUDS/LightRAG](https://github.com/HKUDS/LightRAG) | Python | 39,214 | EMNLP2025 论文开源，简单快速的 RAG 实现，学术研究驱动工程落地案例。 |
| [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) | Python | 111,207 | 将代码库/文档/SQL 转为可查询知识图谱，无需向量库，确定性 AST 解析路线，理念创新。 |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | JavaScript | 91,984 | Claude Code 跨会话持久记忆，AI 压缩+上下文注入，Agent 记忆赛道明星项目。 |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | Go | 45,818 | 云原生向量数据库，大规模 ANN 搜索，RAG 基础设施层核心组件。 |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Rust | 34,217 | 高性能向量数据库，Rust 实现，分布式部署支持，性能与生态并重。 |
| [meilisearch/meilisearch](https://github.com/meilisearch/meilisearch) | Rust | 59,106 | 极速搜索引擎 API，AI 增强混合搜索，Rust 生态代表项目。 |
| [weaviate/weaviate](https://github.com/weaviate/weaviate) | Go | 16,754 | 向量数据库+对象存储，结构化过滤+向量搜索融合，企业级场景适用。 |

---

## 三、趋势信号分析

今日榜单释放三个强烈信号：**第一，Claude Code 生态进入官方加速期**。Anthropic 同日发布官方插件目录（`claude-plugins-official`）与社区镜像（`claude-plugins-community`），标志着 Agent Skills 标准化从社区自发走向官方背书，预计将催生更多垂直领域 Skill 市场。**第二，"AI 替代工作"焦虑转化为开源生产力工具爆发**。AI 求职（ai-job-search、career-ops）、股票分析（daily_stock_analysis）、PPT 生成（ppt-master）等项目今日集中上榜，反映开发者社区正在用 AI 工具解决自身就业与效率痛点，这类应用短期内将持续放量。**第三，Agent 记忆成为新竞争高地**。mem0、claude-mem、cognee 等项目同日进入视野，说明社区对"Agent 跨会话记忆"这一核心能力的争夺已白热化，未来 3-6 个月该赛道预计出现合并或标准化。

---

## 四、社区关注热点

- **[anthropic/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)** — Anthropic 官方插件目录首次上线，Claude Code 插件生态正式启航，开发者应密切关注插件提交规范与审核机制。
- **[Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach)** — 零 API 费用全网信息读取 Agent，覆盖 Twitter/Reddit/B站等主流平台，对信息聚合类应用开发者极具参考价值。
- **[Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify)** — 无需向量库的知识图谱构建工具，确定性 AST 解析路线在 RAG 领域提供全新思路，值得关注其工程落地能力。
- **[MadsLorentzen/ai-job-search](https://github.com/MadsLorentzen/ai-job-search)** — 今日新增 1300 star，AI 求职赛道爆发标志，建议跟踪其多模型适配与 CV 定制算法的开源实现。
- **[ollama/ollama](https://github.com/ollama/ollama)** — 国产模型（Kimi、GLM、DeepSeek）纳入支持是重要里程碑，本地部署门槛持续降低，对 AI 基础设施开发者有直接业务影响。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*