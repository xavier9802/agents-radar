# AI 开源趋势日报 2026-08-30

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-08-30 04:56 UTC

---



# 🤖 AI 开源趋势日报 — 2026-08-30

---

## 一、今日速览

今日 AI 开源社区最显著的信号是 **Agent Skills（智能体技能）生态的爆发式增长**：K-Dense-AI 的科学智能体技能库单日涌入 1,587 star，addyosmani 的工程技能库、Composio 的 Claude Skills 合集以及 anthropics 官方插件目录同步登榜，表明「为 AI 编码助手打造可复用技能库」正成为开发者的核心关注点。与此同时，**RAG 基础设施竞争白热化**——RAGFlow、LightRAG、Mem0、Headroom 等多个检索增强项目集中亮相热榜，反映出现实落地中「上下文管理」已成为开发者最大痛点。另一大趋势是 **AI 视频/多媒体应用**崛起，OpenMontage 和 MoneyPrinterTurbo 证明生成式视频正从概念走向开源生产力工具。

---

## 二、各维度热门项目

### 🔧 AI 基础工具

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | JavaScript | 244,329 | Agent 性能优化系统，涵盖技能、记忆、安全与研究方向，为 Claude Code、Cursor、Codex 等编码助手提供底层支撑。未标注今日新增，但作为 Agent Harness 领域的头部项目持续影响生态。 |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 179,752 | 本地运行 Kimi-K2.6、GLM-5.2、DeepSeek、Qwen 等主流模型的推理引擎，支持一键启动。今日 Trending 热榜未更新，但作为本地 AI 基础设施的核心依赖，热度持续稳定。 |
| [JetBrains/go-modern-guidelines](https://github.com/JetBrains/go-modern-guidelines) | Go | —（+303 today） | JetBrains 发布的 Go 现代编码规范，专门为 AI 编码助手设计，帮助 Claude Code、Codex 等生成符合最佳实践的代码。今日新增 303 star，反映 AI 代码引导工具的社区需求。 |
| [workweave/router](https://github.com/workweave/router) | Go | —（+284 today） | 智能模型路由器，40-70% 成本削减，<50ms 延迟路由到最优模型。今日登榜，标志「多模型路由/成本优化」成为 AI 工程化落地的刚需方向。 |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | 35,246 | 基于 DeepSeek 原生的 AI 编码 Agent，以 prefix-cache 稳定性为核心设计，适合长时间持续运行。今日未更新增量，但 3.5万+ star 显示其社区认可度。 |
| [Hmbown/CodeWhale](https://github.com/Hmbown/CodeWhale) | Rust | 40,861 | 终端原生开源编码 Agent，使用 Rust 构建，强调持续社区协作改进。未标注今日增量，但作为 Rust + AI Agent 交叉方向代表值得关注。 |

---

### 🤖 AI 智能体/工作流

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | Python | 238,203 | 「与你一起成长的 Agent」，强调个性化学习和持续进化。作为 NousResearch 的旗舰 Agent 项目，总 star 数仅次于 ECC，是 Agent 框架赛道头部。 |
| [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | Python | 186,994 | 开源自主 Agent 的奠基项目，目标让每个人都能使用和构建 AI。今日 Trending 未更新，但作为 AutoGPT 赛道的标志性项目持续影响 Agent 社区。 |
| [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | Python | —（+1,587 today） | **今日最大黑马**：165 个经过验证的科学智能技能 + 100+ 科学数据库，已服务 19 万+ 科学家，兼容 Cursor/Claude Code/Codex 等主流 Agent 平台。单日 +1,587 star 显示科学 AI 的爆发需求。 |
| [THU-MAIC/OpenMAIC](https://github.com/THU-MAIC/OpenMAIC) | TypeScript | —（+907 today） | 多智能体交互课堂系统，一键即可获取沉浸式多 Agent 学习体验。清华大学 MAIC 团队出品，今日登榜反映 AI 教育赛道的社区兴趣。 |
| [calesthio/OpenMontage](https://github.com/calesthio/OpenMontage) | Python | —（+806 today） | 开源 Agentic 视频生产系统，12 条制作流水线、100+ 工具、700+ 智能体技能，将 AI 编码助手变成完整视频工作室。今日登榜标志「AI 视频生产」从概念走向工程化。 |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 64,280 | LLM 驱动的多市场股票智能分析系统，支持多源行情、实时新闻、决策看板与自动推送，可零成本定时运行。7 日搜索中热度稳定，显示 AI 金融垂直应用的持续需求。 |
| [zhayujie/CowAgent](https://github.com/zhayujie/CowAgent) | Python | 46,722 | 开源超级 AI 助手 & Agent Harness，支持任务规划、工具调用、技能执行、自我进化记忆，一键安装，兼容多模型多频道。原 chatgpt-on-wechat 升级版，社区积累深厚。 |
| [abi/screenshot-to-code](https://github.com/abi/screenshot-to-code) | Python | —（+550 today） | 截图转干净代码（HTML/Tailwind/React/Vue），一键生成前端代码。今日新增 550 star，反映 AI 辅助前端开发工具的持续热度。 |
| [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | JavaScript | —（+196 today） | 生产级 AI 编码智能体工程技能库，由 Addy Osmani 维护，今日登榜体现核心开发者对技能标准化的推动。 |

---

### 📦 AI 应用

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [langgenius/dify](https://github.com/langgenius/dify) | TypeScript | 153,857 | Agentic 工作流 + RAG 管道的一站式 AI 应用开发平台，支持云/私有化部署，助力团队从原型到生产。今日 Trending 未更新，但 15万+ star 确立其作为国产 AI 应用平台领先地位。 |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | Python | 150,365 | 用户友好的本地 AI 聊天界面，支持 Ollama 和 OpenAI API，无需云端即可运行多种模型。今日未更新增量，但作为本地 AI 用户体验标杆持续受欢迎。 |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 118,562 | 一键 AI 短视频生成工具，根据主题或关键词自动生成高清短视频。7 日搜索中热度稳定，反映 AI 内容创作工具的持久需求。 |
| [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) | Python | 76,589 | 赋予 AI Agent 「看」全互联网的能力，支持 Twitter、Reddit、YouTube、GitHub、Bilibili 等平台，零 API 费用。7 日搜索中热度稳定，显示多源信息聚合 Agent 的市场需求。 |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | 50,240 | AI 生成原生 PowerPoint 演示文稿，支持形状、转场、动画和数据图表，可用用户模板。7 日搜索中热度稳定，展示 AI 办公生产力的具体落地场景。 |
| [santifer/career-ops](https://github.com/santifer/career-ops) | JavaScript | 69,300 | 开源 AI 求职工具，自动扫描招聘平台、评估岗位、生成 A-H 级报告、定制简历并追踪申请状态。7 日搜索中热度稳定，是 AI + 职业赛道的特色项目。 |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 51,239 | AI 生产力工作室，集成智能聊天、自主 Agent 和 300+ 助手，统一接入前沿 LLM。7 日搜索中热度稳定，体现多模型统一管理的需求。 |
| [Osmantic/ODS](https://github.com/Osmantic/ODS) | Python | —（+35 today） | 将个人电脑变成 AI 服务器，支持 LLM 推理、聊天 UI、语音、Agent、工作流、RAG 和图像生成。今日小幅增长，适合个人开发者搭建本地 AI 基础设施。 |

---

### 🧠 大模型/训练

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | 198,021 | 最主流的开源机器学习框架，覆盖训练、推理、部署全链路。今日 Trending 未更新，但作为 ML 基础设施基石地位不可动摇。 |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,661 | 动态计算图深度学习框架，GPU 加速能力强，AI 研究者和生产开发者首选。今日未更新增量，但在 AI 生态中持续保持核心地位。 |
| [rasbt/LLMs-from-scratch](https://github.com/rasbt/rasbt/LLMs-from-scratch) | Jupyter Notebook | 104,023 | 从零用 PyTorch 实现类 ChatGPT 的 LLM，步骤详细、教学导向。今日 Trending 未更新，但作为 LLM 教育赛道标杆项目，长期热度极高。 |
| [jingyaogong/minimind](https://github.com/jingyaogong/minimind) | Python | 55,185 | 2 小时内训练 64M 参数小型 LLM 的教程项目，强调可落地性。7 日搜索中热度稳定，是 LLM 入门训练的热门选择。 |
| [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | Python | 61,079 | YOLOv8/YOLO11 系列目标检测、分割、姿态估计开源库。今日未更新增量，但作为计算机视觉领域的工业级工具，社区认可度高。 |

---

### 🔍 RAG/知识库

| 项目 | 语言 | Stars（总量 / 今日） | 简要说明 |
| :--- | :--- | ---: | :--- |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 89,605 | 领先开源 RAG 引擎，融合 RAG 与 Agent 能力，为 LLM 提供 Superior 上下文层。今日未更新增量，但 8.9万+ star 显示其在 RAG 赛道的领先地位。 |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | JavaScript | 92,599 | Agent 跨会话持久化记忆系统，AI 压缩会话内容，下次自动注入相关上下文，兼容 Claude Code/Codex/Gemini/Hermes 等。7 日搜索中热度极高，是 RAG 向「Agent 记忆」演进的代表。 |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | 64,333 | Agent 通用记忆层，跨会话持久存储和检索 AI 记忆。7 日搜索中热度稳定，显示记忆模块已成为 Agent 架构的标准组件。 |
| [HKUDS/LightRAG](https://github.com/HKUDS/LightRAG) | Python | 39,261 | EMNLP 2025 论文开源项目，简洁高效的检索增强生成实现。7 日搜索中热度稳定，代表学术界向工业界快速转化的趋势。 |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | Go | 45,874 | 高性能云原生向量数据库，支持大规模向量 ANN 搜索。7 日搜索中热度稳定，是 RAG 基础设施的核心组件。 |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Rust | 34,261 | 高性能向量数据库和向量搜索引擎，支持云部署。7 日搜索中热度稳定，Rust 在向量数据库赛道表现突出。 |
| [headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom) | Python | 68,030 | 在 token 到达 LLM 之前压缩工具输出、日志、文件和 RAG chunk，Coding Agent 减少 20% token、JSON 减少 60-95%。今日未更新增量，但作为「Token 节省层」定位独特且实用。 |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | 35,410 | 无向量库的 RAG 文档索引方案，基于推理的检索替代传统向量存储。7 日搜索中热度稳定，代表 RAG 免向量方案的探索方向。 |
| [StarTrail-org/LEANN](https://github.com/StarTrail-org/LEANN) | Python | 12,846 | MLsys 2026 最佳论文项目，RAG on Everything，97% 存储节省，可在个人设备本地运行。7 日搜索中显示学术成果的快速开源化。 |

---

## 三、趋势信号分析

**Agent Skills 生态正经历爆发式增长**：今日 Trending 榜单中，K-Dense-AI 科学智能技能（+1,587）、addyosmani 工程技能（+196）、Composio Claude Skills（+73）和 anthropics 官方插件目录（+358）同时上榜，叠加 ECC（24万+）和 hermes-agent（23万+）等 Agent Harness 项目的高热度，表明开发者正从「构建通用 Agent」转向「为特定领域打造可复用技能库」。这一趋势与 Claude Code、Cursor、Codex 等 AI 编码助手快速普及直接相关——技能标准化成为竞争焦点。

**RAG 基础设施进入「记忆层」深化阶段**：LightRAG（EMNLP 2025）、claude-mem、mem0、Headroom 等项目集中涌现，反映社区已超越「检索增强」本身，进入「Agent 持久记忆」「上下文压缩」「跨会话智能」等更深层次问题。这与近期各大模型厂商推出长上下文窗口（如 Claude 200K+、Gemini 1M+）形成呼应——当上下文变长，如何高效管理记忆成为新瓶颈。

**AI 应用向「垂直生产力工具」快速落地**：OpenMontage（视频生产）、MoneyPrinterTurbo（短视频）、screenshot-to-code（前端生成）、ppt-master（PPT 生成）等应用同时登榜，证明 AI 正从聊天界面走向具体工作流，开发者对「AI 替代重复劳动」的期待正在转化为实际项目。

---

## 四、社区关注热点

- **🔥 [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills)** — 今日最大增长黑马（+1,587 star），165 个经过验证的科学智能技能 + 100+ 数据库，兼容所有主流 Agent 平台，科学 AI 领域首个标准化技能库，值得 AI 科研工作者和 Agent 开发者重点关注。
- **🔥 [workweave/router](https://github.com/workweave/router)** — 多模型智能路由器，<50ms 延迟、40-70% 成本削减，切入 AI 工程化中最实际的痛点（多模型调度与成本优化），今日登榜显示市场认可。
- **💡 [calesthio/OpenMontage](https://github.com/calesthio/OpenMontage)** — 开源 Agentic 视频生产系统，12 条流水线 + 700+ 技能文件，将 AI 编码助手升级为完整视频工作室，标志 AI 多媒体应用从概念走向工程落地。
- **💡 [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)** — Agent 跨会话持久记忆，92,599 star 显示社区对「上下文连续性」的强烈需求，是 RAG 向 Agent Memory 演进的关键项目。
- **💡 [JetBrains/go-modern-guidelines](https://github.com/JetBrains/go-modern-guidelines)** — JetBrains 官方出品的 Go AI 编码规范，专为 AI 编码助手设计，反映大厂对「AI 代码质量标准化」的布局，值得关注其后续生态影响。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*