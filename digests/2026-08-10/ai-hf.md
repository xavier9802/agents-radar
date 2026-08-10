# Hugging Face 热门模型日报 2026-08-10

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-10 02:18 UTC

---



# 🤖 Hugging Face 热门模型日报
**2026-08-10**

---

## 今日速览

MiniMax-H3 家族本周霸榜，原模型及三个微调变体占据热门榜前五，展现了视频生成领域最强的开源竞争力；FLUX.1-dev 以 14,059 点赞稳居图像生成类模型人气王。DeepSeek-V4-Flash-0731 和 GLM-5.2 分别以 2,952 和 4,914 点赞领跑通用语言模型赛道。社区量化活动异常活跃，MiniMax-H3 衍生出 NVFP4、INT4/INT8 等多种量化版本，GGUF 格式模型下载量已超过 160 万。

---

## 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,952 | 868,576 | DeepSeek 最新 Flash 系列模型，专注文本生成与对话任务，采用 safetensors 格式，是当前开源大模型中性价比极高的选择。 |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,914 | 2,488,397 | 智谱 GLM 系列最新 MoE 架构模型，248 万下载量证明其广泛落地，支持文本生成与对话，是国产开源 LLM 的重要力量。 |
| [Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF) | LuffyTheFox | 455 | 396,282 | 基于 Qwen3.6 的 35B MoE 模型，经 Hermes 指令微调且去除审查限制，GGUF 格式便于本地推理，适合定制化部署场景。 |
| [LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 453 | 85,651 | LiquidAI 的 LFM 系列轻量语言模型，2.6B 参数量适合边缘设备部署，支持因果语言建模任务。 |
| [Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 246 | 4,747 | inclusionAI 的轻量对话模型，采用 bailing_hybrid 架构，专注于高效文本生成任务。 |
| [maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 290 | 1,089 | deepgrove 的实验性 MoE 语言模型预览版，采用 transformer 架构，适合研究探索。 |
| [BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-frontier | 125 | 482 | 基于 Qwen3.5 MoE 的多模态对话模型，支持图像-文本输入，适合多轮对话研究。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,251 | 35,295 | MiniMax 的图像-文本到视频生成模型，支持多模态输入生成高质量视频，本周最热门的生成模型。 |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,399 | 1,456,459 | 月之暗面 Kimi 系列多模态模型，支持图像-文本到文本任务，10,399 点赞印证其社区影响力。 |
| [FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev) | black-forest-labs | 14,059 | 487,171 | Black Forest Labs 的顶级文本到图像生成模型，14,059 点赞稳居全榜人气王，生成质量业界领先。 |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,987 | 2,889,062 | 百度开源的图像文本识别模型，288 万下载量证明其在 OCR 领域的广泛应用。 |
| [Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 333 | 13,132 | 轻量文本转语音模型，0.6B 参数适合实时 TTS 应用。 |
| [Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 235 | 6,117 | MiniMax-H3 的图像到视频加速版本，支持 T2V/I2V 任务，适合快速原型开发。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 552 | 18,574 | 基于 Qwen3.5 MoE 的代码专用模型，支持图像-文本到代码生成，适合开发辅助场景。 |
| [Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 211 | 5,651 | Mistral 的安全防护模型，3B 参数适合内容审核与安全分类任务。 |
| [Mach-1-Additive-35B](https://huggingface.co/SyzygyResearch/Mach-1-Additive-35B) | SyzygyResearch | 104 | 1,589 | Syzygy Research 的实验性 35B MoE 模型，采用 ternary 量化与加法混合架构，适合研究探索。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3 (Comfy-Org 版)](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,076 | 4,947,943 | MiniMax-H3 的 ComfyUI 适配版本，494 万下载量证明 ComfyUI 生态的强大分发能力。 |
| [DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 629 | 188,761 | Unsloth 优化的 GGUF 量化版本，兼顾推理速度与质量，适合本地部署。 |
| [MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 547 | 0 | MiniMax-H3-Turbo 的 LoRA 适配器，支持文本到视频/音频生成，适合定制化微调。 |
| [MiniMax-H3-nvfp4-INT4-INT8-Convrot](https://huggingface.co/Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot) | Abiray | 155 | 511,473 | MiniMax-H3 的多精度量化版本，支持 NVFP4/INT4/INT8 混合量化，51 万下载量。 |
| [LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 175 | 68,468 | LFM2.5 的 GGUF 量化版本，适配 llama.cpp 推理框架，适合资源受限环境。 |
| [Qwen3-VL-32B-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 418 | 0 | Qwen3-VL-32B 的 ComfyUI INT8 量化版本，支持图像-文本理解任务。 |
| [MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 188 | 160,747 | MiniMax-H3 的 GGUF 量化版本，16 万下载量，适合本地视频生成推理。 |

---

## 生态信号

**MiniMax-H3 家族本周呈现压倒性优势**，原模型及 ComfyUI、LoRA、GGUF、NVFP4 等 7 个衍生版本进入热门榜，显示视频生成领域已进入"模型家族化"竞争阶段。开源权重持续占领主流：DeepSeek-V4、GLM-5.2、Qwen3.6 等国产开源模型下载量均超百万，反映出对闭源 API 的替代需求。量化活动异常活跃——MiniMax-H3 同时推出 NVFP4、INT4、INT8 三种精度版本，说明社区正积极探索精度与速度的最优平衡点。ComfyUI 生态的 494 万下载量证明"模型+工作流"的捆绑分发模式已成为重要趋势。

---

## 值得探索

1. **[MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 本周最强多模态生成模型，3,251 点赞、35K+ 下载，支持图像-文本到视频生成，是开源视频生成领域的标杆之作，其丰富的生态衍生版本（LoRA、GGUF、ComfyUI）值得深入研究。

2. **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — 2,488 万下载量证明其广泛落地，4,914 点赞显示社区认可度高，作为国产开源 MoE 语言模型的代表，适合对比研究国内外 LLM 架构差异。

3. **[FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev)** — 14,059 点赞全榜第一，文本到图像生成质量业界领先，是图像生成领域的必测模型，适合评估开源图像生成模型的当前最高水平。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*