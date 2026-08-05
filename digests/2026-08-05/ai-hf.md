# Hugging Face 热门模型日报 2026-08-05

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-05 03:13 UTC

---



# Hugging Face 热门模型日报 | 2026-08-05

---

## 一、今日速览

今日榜单由 **DeepSeek V4 Flash** 系列与 **MiniMax H3** 视频生成模型主导，前者以超 270 万下载量领跑，后者填补了开源图生视频赛道的空白。多模态语言模型持续走强，**Kimi K3** 以破万点赞稳居榜首，**GLM-5.2** 和 **百度 Unlimited-OCR** 亦表现亮眼。量化与社区微调生态极为活跃，**Qwen3.6/3.5 GGUF** 系列多版本同时上榜，Heretic / Uncensored 等社区微调路线热度不减。

---

## 二、热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,016 | 1,125,935 | 月之暗面发布的多模态语言模型，支持图像-文本到文本；以破万点赞成为今日榜单最热 LLM，搭载压缩张量（compressed-tensors）以优化推理效率。 |
| [DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 2,011 | 2,737,621 | DeepSeek 开源推理优化版旗舰，下载量突破 270 万，是今日实际使用量最大的语言模型；聚焦低延迟高吞吐的对话场景。 |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,320 | 433,284 | DeepSeek V4 Flash 的 7 月 31 日更新版本，点赞超越原版；持续优化推理性能与对话质量，是 Flash 系列热度最高的分支。 |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,821 | 2,234,662 | 智谱 AI 开源 MoE 架构语言模型，下载量超 220 万；继承 GLM 系列在中文及多语言能力上的优势，适合通用对话与指令跟随。 |
| [Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 920 | 82,912 | Poolside 推出的高性能开源语言模型，专注于长上下文与代码任务，近期社区热度持续上升。 |
| [Qwythos-27B-v1](https://huggingface.co/empero-ai/Qwythos-27B-v1) | empero-ai | 134 | 2,243 | Empero AI 的 27B 参数多模态语言模型，基于 Qwen3.5 架构；面向视觉语言理解与对话的中等规模开源方案。 |
| [Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 174 | 69,253 | Nota AI 的 250B 超大参数开源语言模型，采用 NVFP4 量化格式，支持 vLLM 部署，兼顾模型规模与推理效率。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 2,050 | 0 | MiniMax 开源的图像-文本到视频生成模型，支持文生视频与图生视频双模式；作为高热度视频生成开源项目，引发社区广泛关注。 |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,882 | 2,703,366 | 百度开源的无限分辨率 OCR 模型，支持任意尺寸图像的文字识别与理解；下载量超 270 万，是今日多模态领域下载冠军。 |
| [Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 257 | 435,784 | 微软开源的多模态视觉语言模型，支持图像到文本的理解与生成；在综合多模态基准上表现优异。 |
| [Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 286 | 15,500 | Thinking Machines 推出的轻量级多模态语言模型，适合资源受限环境下的图像-文本交互任务。 |
| [Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 249 | 11,276 | Audio8 开源的 0.6B 参数文本转语音模型预览版，主打轻量高效的语音合成，适合本地部署场景。 |
| [Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 410 | 2,072 | 面向边缘设备与 CPU 推理优化的微型 TTS 模型，体积小巧，适合嵌入式或离线语音合成应用。 |
| [Kroma (LoRA)](https://huggingface.co/lodestones/Kroma) | lodestones | 176 | 0 | 基于 Krea2 的文本到图像 LoRA 微调模型，专为 ComfyUI 工作流设计，适合个性化图像生成风格。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 475 | 15,381 | 面向开发者的专用代码生成模型，支持图像-文本到代码的多模态编程辅助，是榜单上最聚焦编程场景的模型之一。 |
| [Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 195 | 2,987 | EschaLabs 基于 Qwen3.5 MoE 架构的 35B 参数模型，针对编码与数学推理做了专项优化。 |
| [XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | XYZAILab | 404 | 1,317 | XYZAILab 的轻量级多模态语言模型，基于 Qwen3.6 微调，适合端侧快速部署与日常对话。 |
| [XYZ-Aquila-pro](https://huggingface.co/XYZAILab/XYZ-Aquila-pro) | XYZAILab | 358 | 1,388 | XYZ-Aquila 系列的专业版，在 mini 基础上增强 agentic search 能力，适合需要网络搜索辅助的复杂任务。 |
| [LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 163 | 47,393 | LiquidAI 的 2.6B 参数流式语言模型，面向低延迟、流式输出的应用场景设计。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen3.6-27B-Fable-Fusion-Uncensored-Heretic (GGUF)](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,516 | 1,633,405 | DavidAU 对 Qwen3.6-27B 进行的 Heretic 风格无审查微调 GGUF 版本，下载量超 160 万，是社区微调活跃度最高的模型之一。 |
| [DeepSeek-V4-Flash-0731 GGUF (Unsloth)](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 474 | 111,678 | Unsloth 提供的 DeepSeek V4 Flash 官方 GGUF 量化版本，针对本地推理做了加速优化，大幅降低显存门槛。 |
| [Kimi-K3 GGUF (Unsloth)](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 304 | 170,055 | Unsloth 将 Kimi K3 量化为 GGUF 格式，使消费者级 GPU 也能流畅运行这一万赞多模态大模型。 |
| [Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6 (GGUF)](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 364 | 308,857 | 基于 Hermes 和 Genesis 体系的 Qwen3.6 MoE 无审查微调版，GGUF 格式便于本地部署，在开源社区热度较高。 |
| [Qwen3.5-9B-The-Defiant-Fable-Uncensored (GGUF)](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 266 | 323,116 | DavidAU 针对 Qwen3.5-9B 推出的 Heretic 风格无审查 GGUF 微调，采用 Neo Imatrix 技术，兼顾性能与自由度。 |
| [Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive (GGUF)](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,296 | 1,930,898 | HauhauCS 推出的激进风格无审查微调，基于 Qwen3.6 MoE，下载量近 200 万，是社区 GGUF 微调赛道最大热门。 |
| [MiniMax-H3 ComfyUI 版](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 619 | 2 | 专为 ComfyUI 工作流适配的 MiniMax H3 推理版本，便于创作者在 ComfyUI 中直接使用视频生成能力。 |
| [MiniMax-H3 GGUFs (ComfyUI)](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 104 | 40,010 | 社区对 MiniMax H3 进行的 GGUF 量化适配，支持 ComfyUI 本地视频生成推理，降低硬件门槛。 |
| [Qwen3-VL-32B-Ultra-Heretic-MiniMax-H3-ComfyUI-INT8](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-MiniMax-H3-ComfyUI-INT8-ConvRot) | ethanfel | 190 | 0 | 融合 Qwen3-VL-32B 与 MiniMax H3 的 Heretic 风格混合微调，INT8 量化并适配 ComfyUI，探索多模型融合路径。 |
| [Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 665 | 37,256 | Nanbeige 推出的 3B 参数高效语言模型，在保持较小体积的同时实现出色的指令跟随能力，适合端侧应用。 |
| [K-EXAONE-2.0-750B-A37B](https://huggingface.co/LGAI-EXAONE/K-EXAONE-2.0-750B-A37B) | LGAI-EXAONE | 117 | 325 | LG AI 发布的 750B 参数 MoE 语言模型，是榜单上参数量最大的开源模型之一，代表韩系开源大模型的最新进展。 |

---

## 三、生态信号

**模型家族趋势**：DeepSeek V4 系列（Flash 及 Flash-0731）与 Qwen3.6/3.5 系列是今日两大绝对主力，前者领跑下载量，后者在社区微调侧占据主导地位。Kimi K3 以破万点赞证明多模态语言模型仍是用户最关注方向。

**开源 vs 闭源**：榜单几乎全部为开源权重，闭源 API 模型未出现，反映 HF 社区以可下载开源模型为核心诉求。GLM-5.2、K-EXAONE-2.0 等机构级开源模型持续补充分布，开源生态在高端模型上竞争力强劲。

**量化与微调**：GGUF 量化已成为社区标配，Unsloth 提供的官方 GGUF 版本下载量可观。Heretic / Uncensored 风格微调路线热度极高，DavidAU 与 HauhauCS 等创作者贡献了多个百万级下载版本。MiniMax H3 出现 ComfyUI 原生适配版本，显示视频生成模型正快速融入现有本地工作流。

---

## 四、值得探索

1. **[MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 开源图生/文生视频的新标杆，填补了高质量开源视频生成模型的空白，配合 ComfyUI 适配版可快速上手本地视频创作。

2. **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — 智谱开源的 MoE 语言模型，中文能力突出，下载量超 220 万验证了社区认可度，适合需要高质量中文对话与指令跟随的生产场景。

3. **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — GGUF 量化版 Heretic 微调模型中的下载冠军，近 200 万下载量说明其在开源社区的高活跃使用率，适合探索无审查微调的技术边界。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*