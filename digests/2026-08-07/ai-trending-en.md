# AI Open Source Trends 2026-08-07

> Sources: GitHub Trending + GitHub Search API | Generated: 2026-08-07 02:56 UTC

---



# 🤖 GitHub AI Open-Source Trends Report — 2026-08-07

---

## 1. Today's Highlights

The #1 trending repo today is **Cloudflare Computer** (+2,802 stars), a groundbreaking project that gives AI agents direct access to a sandboxed Linux environment—effectively letting agents "use a computer" rather than rely solely on API calls. The coding-agent ecosystem continues its explosive momentum: **Skills** by Matt Poock (+1,873) and **Superpowers** by obra (+858) signal a maturing ecosystem of production-grade agent skills frameworks. DeepSeek-native agents are also surging, with **DeepSeek-Reasonix** (+888) riding the wave of prefix-cache optimization for persistent terminal agents. Meanwhile, **TencentDB Agent Memory** (+1,057) introduces a team-level memory hub with four reusable asset types—Chat Memory, Skill, LLM-Wiki, and Code-Graph—marking the shift from individual to organizational agent intelligence.

---

## 2. Top Projects by Category

### 🔧 AI Infrastructure

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 177,949 | Get up and running with on-device LLMs including Kimi-K2.6, GLM-5.2, DeepSeek, Qwen, and Gemma. Remains the dominant local inference entry point. |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Python | 88,382 | High-throughput, memory-efficient LLM inference and serving engine. Essential for production model serving. |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | 32,505 / +888 | DeepSeek-native AI coding agent for the terminal, engineered around prefix-cache stability so it can run persistently without degrading. |
| [0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig) | Rust | 8,191 | Build modular and scalable LLM applications in Rust. A growing Rust-native option for agent infrastructure. |
| [aarambh-studio](https://github.com/AarambhDevHub/aarambh-studio) | Rust | 65 / +0 | Decoder-only LLM built from scratch in pure Rust using Candle—no Python, no PyTorch. Features sparse attention, native MoE, and long-horizon tool agents. |

### 🤖 AI Agents / Workflows

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [cloudflare/computer](https://github.com/cloudflare/computer) | TypeScript | — / +2,802 | Give your AI agent a sandboxed Linux computer. Trending #1 today with massive community interest in agent autonomy beyond API calls. |
| [mattpocock/skills](https://github.com/mattpocock/skills) | Shell | — / +1,873 | Skills for real engineers, pulled directly from Matt Poock's .agents directory. Signals the rise of shareable agent "skills" as a first-class pattern. |
| [obra/superpowers](https://github.com/obra/superpowers) | Shell | — / +858 | An agentic skills framework and software development methodology. Bridges skills distribution with engineering process. |
| [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | JavaScript | — / +593 | Production-grade engineering skills for AI coding agents. Backed by a well-known web dev figure, adding credibility to the skills ecosystem. |
| [huangruiteng/loopx](https://github.com/huangruiteng/loopx) | Python | — / +847 | Lightweight loop engineering state kernel for long-running AI agent teams. Agent-loop agnostic across Codex, Claude Code, and others, with durable goals and verifiable handoffs. |
| [TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory) | TypeScript | — / +1,057 | Team-level memory hub turning conversations, docs, and code into four reusable assets: Chat Memory, Skill, LLM-Wiki, and Code-Graph. A structural leap for organizational agent memory. |
| [headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom) | Python | 65,253 | Compresses tool outputs, logs, files, and RAG chunks before they reach the LLM—20% fewer tokens for coding agents, 60-95% for JSON. Addresses the critical context-cost problem. |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | JavaScript | 238,336 | Agent harness performance optimization system covering skills, instincts, memory, and security for Claude Code, Codex, Opencode, and Cursor. |
| [deepfakes/faceswap](https://github.com/deepfakes/faceswap) | Python | 57,318 | Deep learning software for face swapping. A persistent ML tool with ongoing community relevance. |

### 📦 AI Applications

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 101,935 | Generate HD short videos from a topic or keyword using an automated AI workflow. One of the most popular creative AI applications. |
| [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) | Python | 67,708 | Give your AI agent eyes to see the entire internet—read and search Twitter, Reddit, YouTube, GitHub, Bilibili, and XiaoHongShu via a single CLI with zero API fees. |
| [santifer/career-ops](https://github.com/santifer/career-ops) | JavaScript | 63,086 | Open-source AI job search: scans job portals, evaluates listings with an A-F rubric, tailors your CV, and tracks applications. Runs locally in your AI coding CLI. |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 60,272 | LLM-powered multi-market stock analysis with multi-source market data, real-time news, a decision dashboard, and cost-free scheduled runs. |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | 43,560 | AI turns documents or topics into real, native PowerPoint decks with shapes, transitions, animations, data-backed charts, and audio narration. |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 49,927 | AI productivity studio with smart chat, autonomous agents, and 300+ assistants. Unified access to frontier LLMs in a single desktop app. |
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | Python | 108,107 | Make websites accessible for AI agents. Automate browser tasks online with ease—critical infrastructure for web-capable agents. |
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | JavaScript | 96,507 | Claude Code skill that cuts 65% of tokens by talking like "caveman." A clever approach to prompt compression for coding agents. |

### 🧠 LLMs / Training

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [jingyaogong/minimind](https://github.com/jingyaogong/minimind) | Python | 54,414 | Train a 64M-parameter LLM from scratch in just 2 hours. An excellent educational project for understanding LLM training end-to-end. |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | Python | 7,281 | LLM evaluation platform supporting Llama3, Mistral, InternLM2, GPT-4, GLM, Claude, and 100+ datasets. Essential for model benchmarking. |
| [picollm](https://github.com/Picovoice/picollm) | Python | 316 | On-device LLM inference powered by X-Bit quantization. Enables efficient edge deployment of small language models. |
| [huggingface/transformers](https://github.com/huggingface/transformers) | Python | 163,420 | The definitive framework for state-of-the-art ML models in text, vision, audio, and multimodal domains. The backbone of the open LLM ecosystem. |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | 196,895 | Open-source machine learning framework. A perennial infrastructure staple. |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,252 | Tensors and dynamic neural networks with strong GPU acceleration. The dominant framework for LLM research and development. |

### 🔍 RAG / Knowledge

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [langgenius/dify](https://github.com/langgenius/dify) | TypeScript | 151,608 | Build agentic workflows and RAG pipelines with rich model/tool support in one collaborative workspace. The leading open-source LLM app platform. |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 86,989 | Leading open-source RAG engine fusing cutting-edge retrieval with agent capabilities. A superior context layer for LLMs. |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | Python | 51,416 | The leading document agent and OCR platform for RAG. Continues to be the go-to for document-centric AI workflows. |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | Python | 62,721 | Universal memory layer for AI agents. Persistent cross-session memory that works across frameworks. |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | JavaScript | 89,886 | Persistent context across sessions for every agent. Captures and compresses agent actions, injecting relevant context back into future sessions. |
| [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) | Python | 103,566 | Turns any codebase into a queryable knowledge graph via deterministic AST parsing. A /graphify skill for Claude Code, Cursor, and Codex—no vector store needed. |
| [firecrawl/pdf-inspector](https://github.com/firecrawl/pdf-inspector) | Rust | — / +1,190 | Fast Rust library for PDF inspection, classification, and text extraction. Intelligently detects scanned vs. text-based PDFs for smart routing in RAG pipelines. |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Rust | 33,819 | High-performance, massive-scale vector database and search engine. A top-tier choice for production RAG backends. |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | 35,049 | Document index for vectorless, reasoning-based RAG. A novel alternative that challenges the vector-only paradigm. |
| [alibaba/zvec](https://github.com/alibaba/zvec) | C++ | 15,393 | Lightweight, lightning-fast in-process vector database by Alibaba. Designed for embedded and low-latency use cases. |
| [tirth8205/code-review-graph](https://github.com/tirth8205/code-review-graph) | Python | — / +237 | Local-first code intelligence graph for MCP and CLI. Builds a persistent map of your codebase so AI coding tools read only what matters, with benchmarked context reductions. |

---

## 3. Trend Signal Analysis

Today's data reveals three dominant signals. First, **agent skills and memory are entering a "shipped product" phase**. Five of the eight trending repos today are directly about agent skills (Skills, Superpowers, Agent-Skills, Agent-Memory, Claude-Mem) or agent orchestration (loopx, computer). The community is moving past experimental agents toward reusable, shareable skill libraries and persistent memory—this is the infrastructure layer that coding-agent frameworks like Claude Code and Codex need to scale. Second, **prefix-cache stability for terminal agents** is a newly prominent theme via DeepSeek-Reasonix, which engineers agents specifically around the constraint that long-running sessions degrade without cache discipline. This is a direct response to real-world friction reported by thousands of Claude Code and Codex users. Third, **vectorless RAG** is gaining visibility through PageIndex and Graphify, both of which challenge the default assumption that every RAG system needs a vector database. Graphify's 103K stars and PageIndex's 35K stars signal that the community is actively seeking lighter, more deterministic alternatives to embedding-heavy pipelines—likely driven by cost and accuracy concerns in production environments.

---

## 4. Community Hot Spots

- **[cloudflare/computer](https://github.com/cloudflare/computer)** — #1 trending today (+2,802). Giving agents a real computer breaks the API-only paradigm. Any developer building autonomous agents should watch this closely.
- **[TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory)** — (+1,057 today). The four-asset memory model (Chat Memory, Skill, LLM-Wiki, Code-Graph) is a structured approach to team-level agent memory that could become a reference architecture.
- **[headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom)** — 65K stars. Token compression for agent tool outputs is a practical, immediately useful tool. The 60-95% JSON compression figures are compelling for any agent doing heavy tool use.
- **[Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify)** — 103K stars. AST-based knowledge graphs without vector stores represent a fundamentally different approach to codebase understanding. Worth trying for any agent working with large repositories.
- **[esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix)** — 32K stars, +888 today. The prefix-cache-stable terminal agent concept addresses a real pain point for long-running coding sessions. DeepSeek-native optimization is a growing niche.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*