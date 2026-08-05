# AI Open Source Trends 2026-08-05

> Sources: GitHub Trending + GitHub Search API | Generated: 2026-08-05 03:13 UTC

---



# 2026-08-05 AI Open-Source Trend Report

---

## 1. Today's Highlights

AI agent tooling continues its explosive momentum, with **TencentDB-Agent-Memory** (1,111 new stars) and **reverse-skill** (2,297 new stars) both surging on the trending list, signaling strong developer appetite for reusable agent memory and skill-routing layers. The **DeepSeek-native** ecosystem remains dominant: `DeepSeek-Reasonix` appears in both trending and topic searches with 922 today's stars, while `ollama` adds support for DeepSeek and other open models. Meanwhile, **AirLLM** (1,711 today's stars) proves that local inference democratization is accelerating—running 70B-parameter models on a single 4 GB GPU is now achievable without cloud dependency. The **browser-use** family (video-use + browser-use) shows AI agents are expanding beyond coding into multimodal workflow automation.

---

## 2. Top Projects by Category

### 🔧 AI Infrastructure

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [lyogavin/airllm](https://github.com/lyogavin/airllm) | Jupyter Notebook | 0 (+1,711) | Enables inference of 70B-parameter models on a single 4 GB GPU by chunking and loading layers dynamically. Trending today with massive momentum—it makes local LLM deployment accessible to edge and hobbyist hardware. |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Python | 88,203 | High-throughput, memory-efficient LLM inference and serving engine using PagedAttention. A production staple for self-hosted model deployment; continues to be a go-to choice for serving open-weight models at scale. |
| [ollama/ollama](https://github.com/ollama/ollama) | Go | 177,800 | One-command local LLM runner supporting Kimi-K2.6, GLM-5.2, DeepSeek, Qwen, Gemma, and more. Its rapid model support expansion makes it the default entry point for developers testing new open-weight releases. |
| [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | Go | 30,884 (+922) | DeepSeek-native AI coding agent built around prefix-cache stability for long-running terminal sessions. Stands out as the first trending project explicitly optimized for the DeepSeek reasoning model family, signaling a shift toward model-specific agent tooling. |
| [0xPlaygrounds/rig](https://github.com/0xPlaygrounds/rig) | Rust | 8,174 | Modular, scalable LLM application framework written in Rust. Offers a systems-programming approach to agent construction with strong safety guarantees and zero-cost abstractions. |
| [Picovoice/picollm](https://github.com/Picovoice/picollm) | Python | 316 | On-device LLM inference powered by X-Bit Quantization. A lightweight solution for running quantized models directly on consumer hardware without cloud dependencies. |

### 🤖 AI Agents / Workflows

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [TencentCloud/TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory) | TypeScript | 0 (+1,111) | Team-level memory hub for AI agents that persists conversations, docs, and code as four reusable assets (Chat Memory, Skill, LLM-Wiki, Code-Graph). Backed by Tencent, this signals enterprise-grade agent memory infrastructure entering open source. |
| [zhaoxuya520/reverse-skill](https://github.com/zhaoxuya520/reverse-skill) | PowerShell | 0 (+2,297) | AI-powered skill router for reverse engineering and penetration testing with self-evolving knowledge base. Supports Claude Code, Kiro, Cursor, and Cline—unique in targeting the security research workflow with agentic tool routing. |
| [livekit/agents](https://github.com/livekit/agents) | Python | 0 (+432) | Framework for building real-time voice AI agents with WebSocket-based audio streaming. Taps into LiveKit's mature real-time infrastructure, making it a strong choice for conversational and voice-first agent applications. |
| [obra/superpowers](https://github.com/obra/superpowers) | Shell | 0 (+653) | Agentic skills framework and software development methodology. Provides a structured approach to chaining skills and tools for autonomous development workflows. |
| [uber/ADR](https://github.com/uber/ADR) | Python | 0 (+148) | Secures enterprise AI agents through observability, security benchmarking, and threat detection—currently deployed at Uber. Addresses the growing need for agent runtime security as autonomous systems handle production workloads. |
| [Eigenwise/atomic-agents](https://github.com/Eigenwise/atomic-agents) | Python | 6,115 | Building AI agents atomically—composable, minimal agent primitives. A design philosophy project for developers who want fine-grained control over agent behavior rather than monolithic frameworks. |
| [deepfakes/faceswap](https://github.com/deepfakes/faceswap) | Python | 57,239 | Deep-learning-based face-swapping toolkit. One of the most-watched computer-vision applications; continues to see active development and community contribution. |

### 📦 AI Applications

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [browser-use/video-use](https://github.com/browser-use/video-use) | Python | 0 (+320) | Edit videos with coding agents—extends the browser-use ecosystem into video production workflows. Represents AI agents moving beyond text into multimodal creative tasks. |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | Python | 43,045 | AI generates native PowerPoint decks with shapes, transitions, animations, charts, and narration from documents or topics. A practical productivity app that automates one of the most time-consuming office tasks. |
| [harry0703/MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo) | Python | 101,629 | Generates HD short videos from a topic or keyword using automated AI workflows. Popular in the content-creation space for one-click video production with minimal manual input. |
| [ZhuLinsen/daily_stock_analysis](https://github.com/ZhuLinsen/daily_stock_analysis) | Python | 60,085 | LLM-powered multi-market stock analysis with real-time news, decision dashboards, and automated notifications at zero running cost. A strong example of vertical AI for financial analysis with practical deployment. |
| [microsoft/generative-ai-for-beginners](https://github.com/microsoft/generative-ai-for-beginners) | Jupyter Notebook | 0 (+783) | 21-lesson beginner's guide to building with generative AI. Continues to trend as new developers enter the space; Microsoft's structured curriculum approach makes it a key onboarding resource. |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | TypeScript | 49,416 | AI productivity studio with smart chat, autonomous agents, and 300+ assistant integrations in a unified desktop app. Appeals to users who want a single client for multiple LLM providers and agent workflows. |

### 🧠 LLMs / Training

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [tensorflow/tensorflow](https://github.com/tensorflow/tensorflow) | C++ | 196,804 | The foundational open-source ML framework powering countless production models. Remains the most-starred ML project on GitHub and the default choice for large-scale model training and serving. |
| [pytorch/pytorch](https://github.com/pytorch/pytorch) | Python | 102,185 | Dynamic-tensor deep learning framework with strong GPU acceleration. The dominant research and production framework for LLM training; continues to see rapid feature additions around distributed training and efficiency. |
| [ultralytics/ultralytics](https://github.com/ultralytics/ultralytics) | Python | 60,210 | YOLOv8/YOLO11/YOLO26 for object detection, segmentation, pose estimation, and tracking. The most widely adopted computer-vision toolkit; regular releases keep it at the cutting edge of real-time detection. |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | Python | 7,273 | LLM evaluation platform supporting 100+ datasets across Llama 3, Mistral, Qwen, GLM, Claude, and more. Critical infrastructure for benchmarking the rapidly expanding open-model landscape, especially Chinese-language models. |
| [AarambhDevHub/aarambh-studio](https://github.com/AarambhDevHub/aarambh-studio) | Rust | 62 | Decoder-only LLM built from scratch in pure Rust using Candle—no Python, no PyTorch. Includes gated DeltaNet, sparse attention, MoE, and native video/document understanding; represents the emerging Rust-native LLM movement. |
| [skyzh/tiny-llm](https://github.com/skyzh/tiny-llm) | Python | 4,441 | Course on LLM inference serving on Apple Silicon, building a tiny vLLM + Qwen from scratch. Practical guide for systems engineers wanting to understand inference internals without relying on black-box frameworks. |

### 🔍 RAG / Knowledge

| Project | Lang | Stars (total / today) | Summary |
| :--- | :--- | ---: | :--- |
| [firecrawl/pdf-inspector](https://github.com/firecrawl/pdf-inspector) | Rust | 0 (+2,540) | Fast Rust library for PDF inspection, classification, and text extraction with smart scanned-vs-text routing. From the Firecrawl team; directly solves a critical RAG preprocessing bottleneck with high performance. |
| [meilisearch/meilisearch](https://github.com/meilisearch/meilisearch) | Rust | 58,858 | Lightning-fast search engine API with AI-powered hybrid search. Strong choice for RAG-backed applications needing sub-millisecond full-text + vector search combined. |
| [run-llama/llama_index](https://github.com/run-llama/llama_index) | Python | 51,381 | Leading document agent and OCR platform for building RAG pipelines. The de facto standard for enterprise document ingestion and retrieval; continues to add OCR and multi-modal capabilities. |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Go | 86,840 | Open-source RAG engine fusing retrieval with agent capabilities for superior LLM context. Distinguishes itself with visual workflow building and strong document parsing; a top contender in the RAG framework space. |
| [qdrant/qdrant](https://github.com/qdrant/qdrant) | Rust | 33,782 | High-performance, massive-scale vector database and search engine, also available as a managed cloud service. Mature Rust-native storage with strong filtering and payload support—widely used in production RAG systems. |
| [lancedb/lancedb](https://github.com/lancedb/lancedb) | Rust | 11,075 | Developer-friendly embedded retrieval library for multimodal AI—search more, manage less. Eliminates the need for a separate vector DB server by embedding storage directly into applications. |
| [VectifyAI/PageIndex](https://github.com/VectifyAI/PageIndex) | Python | 35,017 | Document index for vectorless, reasoning-based RAG. Challenges the vector-store paradigm by using direct document reasoning, potentially reducing infrastructure complexity and cost for certain retrieval workloads. |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Python | 29,780 | Open-source AI memory platform using a self-hosted knowledge graph engine for persistent long-term agent memory. Bridges the gap between vector search and graph-based reasoning for more structured RAG. |
| [alibaba/zvec](https://github.com/alibaba/zvec) | C++ | 15,376 | Lightweight, lightning-fast in-process vector database from Alibaba. Enables embedding-based search without a dedicated server, ideal for embedded and edge RAG deployments. |
| [StarTrail-org/LEANN](https://github.com/StarTrail-org/LEANN) | Python | 12,760 | Presented at MLsys 2026; achieves 97% storage savings while running fast, accurate, private RAG on personal devices. A breakthrough in on-device RAG efficiency with a novel compression approach. |

---

## 3. Trend Signal Analysis

The dominant signal across today's trending and topic data is the **maturation of the AI agent ecosystem beyond proof-of-concept into production infrastructure**. Agent memory (TencentDB-Agent-Memory, cognee, mem0, Claude-mem) and agent security (Uber ADR) are emerging as the next critical layer—developers are moving past "what can agents do" to "how do we operate agents reliably at scale." The `reverse-skill` project's 2,297 new stars in a single day is an outlier that deserves attention: security research workflows are being adopted as a primary domain for agentic toolchains, suggesting a crossover between AI coding agents and professional security tooling.

DeepSeek remains the most-referenced model family in new tooling. `DeepSeek-Reasonix` is engineered specifically for it, and `ollama` has added DeepSeek to its supported model list alongside Kimi-K2.6 and GLM-5.2—Chinese open-weight models are gaining traction in the Western developer ecosystem. The `airllm` trend (1,711 new stars) reinforces the local-inference movement: developers increasingly expect to run 70B-class models on consumer GPUs, reducing cloud dependency and cost.

A secondary trend is **RAG infrastructure diversification**. Vectorless RAG (PageIndex), on-device RAG (LEANN), and embedded vector DBs (LanceDB, zvec) are challenging the monolithic "vector database + embedding pipeline" paradigm. The `pdf-inspector` from Firecrawl (+2,540 today) highlights the growing recognition that data ingestion quality is the bottleneck, not the retrieval model itself.

---

## 4. Community Hot Spots

- **TencentDB-Agent-Memory** ([link](https://github.com/TencentCloud/TencentDB-Agent-Memory)) — Enterprise-grade agent memory from a major cloud provider; its four-asset model (Chat Memory, Skill, LLM-Wiki, Code-Graph) defines a practical architecture for team-level agent persistence.
- **firecrawl/pdf-inspector** ([link](https://github.com/firecrawl/pdf-inspector)) — Solves the "garbage in, garbage out" problem in RAG pipelines; 2,540 stars in one day indicate acute community demand for smart document preprocessing.
- **zhaoxuya520/reverse-skill** ([link](https://github.com/zhaoxuya520/reverse-skill)) — The first major agent skill router targeting reverse engineering and penetration testing; its self-evolving knowledge base and multi-client support (Claude Code, Kiro, Cursor, Cline) make it a unique bridge between security tooling and agentic workflows.
- **esengine/DeepSeek-Reasonix** ([link](https://github.com/esengine/DeepSeek-Reasonix)) — DeepSeek-native coding agent with prefix-cache stability; represents the emerging category of model-specific agent tooling rather than generic frameworks.
- **StarTrail-org/LEANN** ([link](https://github.com/StarTrail-org/LEANN)) — 97% storage savings in on-device RAG is a significant efficiency breakthrough; if validated, it could make private, local-first RAG viable on consumer hardware.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*