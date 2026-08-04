# Hugging Face 热门模型日报 2026-08-04

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-04 03:18 UTC

---



# 📊 Hugging Face 热门模型日报
**日期：2026-08-04 | 分析师：Agnes**

---

## 1. 今日速览

Kimi-K3 以近万次点赞强势登顶，成为本周最受关注的多模态大模型。DeepSeek-V4 系列持续发力，官方 Flash 版下载量突破 274 万，GGUF 社区量化同步跟进。百度 Unlimited-OCR 以超 260 万下载量刷新 OCR 领域热度纪录。社区微调圈中，Qwen3.6 家族 Uncensored 变体引发大量下载，Heretic 与 Hermes 路线并存。微型 TTS 模型与 MoE 架构继续成为边缘部署与高效推理的热门方向。

---

## 2. 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 1,991 | 2,746,291 | DeepSeek 官方轻量版文本生成模型，对话能力出色，下载量居本日前列。其 0731 细粒度版本（[DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731)）同步登上榜单，获 2,083 赞。 |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,798 | 2,180,509 | 智谱 AI GLM 系列 MoE 架构模型，具备强对话与推理能力，下载量超 218 万，是开源中文 LLM 的重要更新。 |
| [Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 910 | 81,584 | Poolside 推出的轻量级文本生成模型，在代码与指令跟随任务中表现优异，适合资源受限场景。 |
| [Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 652 | 34,705 | Nanbeige 系列第三代 3B 参数模型，小而全的开源 LLM，适合本地部署与教育场景。 |
| [Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 169 | 68,778 | Nota AI 推出的 250B 参数开源模型，采用 NVFP4 稀疏量化格式，是超大参数开源模型的量化探索。 |
| [XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) / [XYZ-Aquila-pro](https://huggingface.co/XYZAILab/XYZ-Aquila-pro) | XYZAILab | 391 / 351 | 1,063 / 1,214 | XYZAILab 基于 Qwen3.6 MoE 推出的两个尺寸变体，mini 侧重轻量推理，pro 引入 agentic-search 能力。 |
| [Instella-MoE-16B-A3B-Think](https://huggingface.co/amd/Instella-MoE-16B-A3B-Think) | amd | 150 | 2,078 | AMD 推出的 MoE 架构推理优化模型，面向 GPU 高效部署，适合边缘推理场景。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 9,860 | 967,622 | 月之暗面推出的多模态大模型，支持图像理解与文本生成，点赞数远超其他模型，热度第一。 |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,848 | 2,601,062 | 百度开源的高性能 OCR 模型，支持多语言多场景文本识别，下载量超过 260 万，是图像文本理解任务的首选之一。 |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 1,518 | 0 | MiniMax 发布的图像文本到视频生成模型，支持文本与图像双重驱动的视频创作，社区 ComfyUI 适配版同步发布（[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)）。 |
| [Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 234 | 431,487 | 微软推出的多模态视觉语言模型，擅长图像理解与复杂视觉问答，下载量超 43 万。 |
| [Fara1.5-27B](https://huggingface.co/microsoft/Fara1.5-27B) | microsoft | 268 | 2,988 | 微软面向计算机视觉任务的轻量级多模态模型，支持图像理解与指令跟随。 |
| [Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 215 | 4,609 | 小型文本转语音模型，适合边缘设备与实时语音合成场景。 |
| [Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 399 | 1,944 | 微型本地 TTS 模型，专为 CPU 和边缘 AI 设备优化，支持低延迟语音合成。 |
| [Kroma (LoRA)](https://huggingface.co/lodestones/Kroma) | lodestones | 160 | 0 | 基于 Krea 平台的文本到图像 LoRA 微调模型，适配 ComfyUI 工作流。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 447 | 14,339 | 面向代码生成的专用模型，基于 Qwen3.5 MoE 架构，在代码补全与调试任务中表现突出。 |
| [LFM2.5-Encoder-350M](https://huggingface.co/LiquidAI/LFM2.5-Encoder-350M) | LiquidAI | 92 | 4,498 | LiquidAI 推出的小型填充掩码编码器，适合嵌入提取与语义匹配任务。 |
| [Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 264 | 8,504 | ThinkingMachines 的多模态小模型，支持图像理解与对话，适合快速部署。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen3.6-27B-Fable-Fusion-Uncensored (GGUF)](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,441 | 1,550,034 | DavidAU 基于 Qwen3.6 推出的无限制 Heretic 微调版本，GGUF 格式支持本地高效推理，下载量超 155 万。 |
| [Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive (GGUF)](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,273 | 1,895,741 | HauhauCS 的激进 Uncensored 微调版本，采用 GGUF 量化，深受社区用户青睐，下载量近 190 万。 |
| [Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6 (GGUF)](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 344 | 287,745 | LuffyTheFox 基于 Hermes 路线的微调版本，结合 GGUF 量化，适合个性化部署。 |
| [Qwen3.5-9B-The-Defiant-Fable-Uncensored (GGUF)](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 239 | 304,420 | DavidAU 针对 9B 尺寸的轻量级无限制微调版本，GGUF 格式适配本地运行。 |
| [DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 430 | 69,656 | Unsloth 提供的 DeepSeek-V4 Flash GGUF 量化版本，支持快速推理与低内存部署。 |
| [Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 284 | 128,215 | Unsloth 对 Kimi-K3 进行的 GGUF 量化适配，方便本地高效推理。 |
| [Qwen3-VL-32B-Ultra-Heretic-MiniMax-H3-ComfyUI-INT8](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-MiniMax-H3-ComfyUI-INT8-ConvRot) | ethanfel | 111 | 0 | 将 Qwen3-VL 与 MiniMax-H3 融合的微调版本，INT8 量化适配 ComfyUI 工作流。 |
| [Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 158 | 2,682 | EschaLabs 的 Qwen3.6 MoE 微调版本，针对特定风格进行对齐优化。 |
| [Qwythos-27B-v1](https://huggingface.co/empero-ai/Qwythos-27B-v1) | empero-ai | 119 | 1,736 | empero-ai 基于 Qwen3.5 的多模态微调版本，支持图像理解与文本生成。 |

---

## 3. 生态信号

本周生态呈现三大趋势：**一是国产多模态模型集体爆发**，Kimi-K3、GLM-5.2、DeepSeek-V4 三足鼎立，覆盖文本、视觉、视频生成全链路；**二是开源权重持续挤压闭源空间**，DeepSeek-V4 Flash 系列下载量超 274 万，月之暗面 Kimi-K3 以近万次点赞领跑；**三是社区量化与无限制微调活动空前活跃**，GGUF 格式几乎覆盖所有热门模型，DavidAU、HauhauCS、LuffyTheFox 等社区作者围绕 Qwen3.6 推出了多款 Heretic/Uncensored 变体，下载量合计超 370 万。与此同时，微型 TTS 模型（如 Inflect-Micro-v2）和 AMD 优化的 MoE 模型表明边缘部署与硬件适配正成为新的技术竞争点。

---

## 4. 值得探索

1. **[Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周绝对热度冠军，多模态能力全面，适合图像理解与通用对话场景，社区生态正在快速形成。

2. **[Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — 百度开源的高性能 OCR 模型，260 万下载量印证了其在实际生产中的广泛应用，是文档智能与多语言识别的首选。

3. **[DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash)** — 官方轻量版在保持强推理能力的同时显著降低部署成本，配合 Unsloth 的 GGUF 版本可实现本地高效运行，是当前开源 LLM 中最具实用价值的选择之一。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*