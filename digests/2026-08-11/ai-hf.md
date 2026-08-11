# Hugging Face 热门模型日报 2026-08-11

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-11 02:09 UTC

---



# Hugging Face 热门模型日报
**日期：2026-08-11**

---

## 一、今日速览

今日 HF 榜单最大热点是 **MiniMax-H3** 视频生成模型的全面爆发——原版及多个社区 ComfyUI 适配、LoRA 微调版本占据榜单近半数席位，MiniMax 已成为视频生成领域的焦点。Kimi-K3（10,472 赞）与 DeepSeek-V4-Flash-0731（95 万+ 下载）在语言模型赛道持续领跑，百度 Unlimited-OCR 凭借近 292 万下载量稳居 OCR 工具首选。与此同时，社区量化（GGUF/INT8/NVFP4）和 ComfyUI 集成活动极为活跃，反映出本地部署与可视化工作流需求旺盛。

---

## 二、热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,472 | 1,510,032 | 月之暗面最新多模态语言模型，支持图文理解与对话。点赞数全场最高，下载超 150 万，展现强劲社区热度。 |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,063 | 954,441 | DeepSeek 轻量 Flash 版语言模型，支持高效对话与文本生成。下载量近百万，兼顾性能与推理效率。 |
| [LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 490 | 89,680 | Liquid AI 推出的液态架构小参数语言模型，专为高效推理设计。配合其 GGUF 版本下载量接近 9 万。 |
| [Qwen3.6-27B-Fable-Fusion-711-Uncensored](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,862 | 2,439,083 | 基于 Qwen3.6 的大规模非审查社区微调版本，采用 GGUF 格式便于本地部署，下载量超 240 万。 |
| [LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 186 | 89,611 | LFM2.5-2.6B 的 GGUF 量化版本，兼容 llama.cpp 生态，为资源受限环境提供轻量化选择。 |
| [DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 638 | 199,167 | DeepSeek-V4-Flash 的 GGUF 量化版本，由 unsloth 优化，显著降低本地推理显存占用。 |

---

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,438 | 47,468 | MiniMax 最新图像-文本到视频生成模型，支持高质量视频创作。原版首发即引发社区大量衍生开发。 |
| [MiniMax-H3 (ComfyUI)](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,149 | 6,009,639 | MiniMax-H3 的 ComfyUI 单文件集成版本，下载量破 600 万，成为 ComfyUI 用户首选的视频生成工具。 |
| [FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev) | black-forest-labs | 14,077 | 480,762 | Black Forest Labs 出品的 SOTA 文本到图像生成模型，点赞数仅次于 Kimi-K3，稳居图像生成头部。 |
| [MiniMax-H3-Turbo (lightx2v)](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 261 | 15,087 | 基于 MiniMax-H3 的 Turbo 加速版本，侧重图像到视频生成，显著提升推理速度。 |
| [MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 601 | 0 | MiniMax-H3 的 LoRA 微调版本，针对文本到视频生成优化，支持更精细的风格控制。 |
| [Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 338 | 13,432 | 轻量级文本到语音模型，0.6B 参数适配多场景语音合成，为新星 TTS 工具值得关注。 |

---

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 4,003 | 2,921,751 | 百度开源的多语言 OCR 模型，覆盖印刷体与手写体识别，下载量近 292 万，是中文场景的热门选择。 |
| [Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 222 | 6,343 | Mistral 推出的安全护栏模型，专注于内容审核与风险检测，vllm 兼容便于部署。 |
| [maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 312 | 1,344 | DeepGrove 的 MoE 架构实验性语言模型，目前处于预览阶段，社区反馈尚在积累中。 |

---

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 193 | 174,862 | MiniMax-H3 的 GGUF 系列量化版本，支持多种量化精度，本地部署便捷。 |
| [Muse-Glimmer-30B-GGUF (unsloth)](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 217 | 0 | meta-models/Muse-Glimmer-30B 的 GGUF 量化版本，由 unsloth 提供优化推理支持。 |
| [Qwen3-VL-32B-Ultra-Heretic-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 440 | 0 | Qwen3-VL-32B 的 INT8 量化版本，结合 ComfyUI 集成，适合显存受限环境运行大 VL 模型。 |
| [Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4](https://huggingface.co/sakamakismile/Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4) | sakamakismile | 152 | 0 | 将 Qwen3-VL 作为文本编码器接入 MiniMax-H3 工作流的 NVFP4 量化方案，展示多模型融合趋势。 |
| [MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 117 | 268 | 针对 MiniMax-H3 的提示词重写 LoRA 适配器，可提升视频生成指令遵循质量。 |

---

## 三、生态信号

**MiniMax 家族全面爆发**是当前榜单最显著的信号：原版 MiniMax-H3 及至少 8 个衍生版本（ComfyUI 集成、Turbo、LoRA、GGUF 量化、Prompt Rewriter）同时上榜，累计下载量超过 620 万，表明视频生成赛道正经历一轮社区驱动的生态扩张。DeepSeek-V4-Flash 与 Kimi-K3 作为语言模型双雄，下载量分别突破 95 万和 150 万，反映出用户对高效、低延迟推理方案的持续偏好。**量化与本地部署仍是社区高频活动**：unsloth 持续为热门模型提供 GGUF 版本，NVFP4、INT8 等异构量化方案频现，ComfyUI 集成成为模型扩散的关键加速器。此外，百度 Unlimited-OCR 以近 292 万下载量位居专用模型之首，验证了实用工具类模型在开源社区的持久价值。

---

## 四、值得探索

1. **[Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 榜单点赞之王，多模态理解与对话能力出色，适合需要图文推理与高质量文本生成的场景，建议作为语言模型首选进行评估。

2. **[MiniMax-H3 ComfyUI 版](https://huggingface.co/Comfy-Org/MiniMax-H3)** — 下载量破 600 万的视频生成热点，ComfyUI 原生集成让工作流搭建极为便捷，适合视频内容创作者快速体验最新视频生成能力。

3. **[FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev)** — 图像生成 SOTA 模型，Stable Diffusion 创始团队新作，综合质量与社区生态稳居顶部，是图像生成任务的高置信度选择。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*