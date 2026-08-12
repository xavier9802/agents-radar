# Hugging Face 热门模型日报 2026-08-12

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-12 02:27 UTC

---



# 📊 Hugging Face 热门模型日报
**日期：2026-08-12 | 数据周期：周点赞排序**

---

## 今日速览

MiniMax-H3 视频生成模型成为本周最大赢家，官方发布与社区微调、ComfyUI 集成版本共同占据热门榜前列，掀起一轮视频生成热潮。DeepSeek-V4-Flash-0731 以超 100 万下载量证明其语言模型实力，unsloth 同步推出 GGUF 量化版本加速落地。Kimi-K3 以 10,532 点赞位居榜首，百度 Unlimited-OCR 凭借 4,000+ 点赞和近 300 万下载量成为实用型标杆。整体生态呈现"视频生成爆发 + 大模型量化普及"的双主线趋势。

---

## 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,159 | 1,048,685 | DeepSeek 官方 Flash 版语言模型，以高吞吐量与低延迟著称，下载量突破百万，是当前最热门开源 LLM 之一。 |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,532 | 1,565,484 | 月之暗面多模态对话模型，以 10,532 点赞位列全榜第一，支持图像-文本联合理解，综合能力突出。 |
| [Qwen3.6-27B-Fable-Fusion-711-Uncensored](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,904 | 2,521,093 | Qwen3.6-27B 社区深度微调版本，去除内容限制，超 250 万下载量显示其在自由对话场景需求旺盛。 |
| [LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 555 | 93,668 | LiquidAI 轻量级语言模型，以 2.6B 参数规模提供高效推理能力，适合边缘部署场景。 |
| [maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 336 | 2,049 | deepgrove 推出的 MoE 架构语言模型预览版，采用混合专家设计，在推理效率上具备探索潜力。 |
| [Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 307 | 6,148 | inclusionAI 轻量对话模型，采用 Bailing Hybrid 架构，适合快速推理与低延迟应用。 |
| [BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-frontier | 171 | 708 | Qwen3.5 MoE 架构多模态对话模型，支持图文联合理解与对话，目前处于早期阶段。 |
| [Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 159 | 0 | inclusionAI 超轻量版本，MIT 协议开源，适合资源受限环境部署与快速实验。 |
| [Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 232 | 6,769 | Mistral 安全护栏模型，3B 参数专注内容审核与安全分类，与 vLLM 深度集成便于生产部署。 |
| [NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 137 | 19,250 | NVIDIA 激活稀疏化语言模型，30B 总参数仅激活 3B，NVFP4 高精度量化带来高效推理性价比。 |

---

## 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,585 | 59,368 | MiniMax 官方图像-文本到视频生成模型，支持 T2V/I2V 多模式，本周视频生成赛道的核心模型。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,216 | 6,798,796 | MiniMax-H3 的 ComfyUI 集成版本，下载量超 679 万，是社区视频生成工作流的首选集成方案。 |
| [Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,108 | 0 | Meta 多模态对话模型，30B 参数规模支持图像-文本联合理解与对话，官方权重首发引起关注。 |
| [LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 245 | 39 | Lightricks 视频生成模型，支持 I2V/T2V/V2V 多种模式，Diffusion Single File 格式便于快速部署。 |
| [NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 331 | 653 | NVIDIA 语音对话模型，支持中英文及阿拉伯语，专注端到端语音交互场景。 |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 4,022 | 2,892,191 | 百度开源 OCR 模型，支持多语言文本识别，近 300 万下载量验证其在文档处理场景的实用价值。 |

---

## 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 4,022 | 2,892,191 | 百度开源 OCR 模型，覆盖多语言场景，文档图像文字提取效率与精度俱佳，实用性强。 |
| [Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 232 | 6,769 | Mistral 安全分类模型，3B 参数轻量高效，专注于内容安全审核与风险识别任务。 |

---

## 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 655 | 0 | 基于 MiniMax-H3 的 LoRA 微调版本，专注于视频生成加速与质量提升，社区适配成果。 |
| [MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 279 | 0 | ComfyUI 版 MiniMax-H3 LoRA 适配器，剪枝后模型更轻量，方便创作者在 ComfyUI 中使用。 |
| [MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 134 | 353 | 提示词重写 LoRA 适配器，帮助用户将普通文本提示转化为更适合 MiniMax-H3 的生成格式。 |
| [MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 119 | 0 | fal.ai 推出的写实风格人物 LoRA，针对人物生成优化，填补视频生成中写实人像的空白。 |
| [Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 311 | 0 | unsloth 提供的 Muse-Glimmer-30B GGUF 量化版本，支持 llama.cpp 等推理框架本地部署。 |
| [Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 207 | 0 | Meta 官方 Muse-Glimmer-30B 的 GGUF 量化版，保留原始模型能力同时大幅降低内存占用。 |
| [DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 652 | 207,990 | unsloth 量化版 DeepSeek-V4-Flash，GGUF 格式兼容 llama.cpp，超 20 万下载显示量化版本需求旺盛。 |
| [LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 205 | 111,942 | LiquidAI LFM2.5-2.6B 的 GGUF 量化版本，与官方 safetensors 版形成互补，满足不同部署需求。 |
| [MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 113 | 781 | MiniMax-H3 的 GGUF 量化版本，让视频生成模型也可在消费级硬件上本地运行，降低使用门槛。 |
| [Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 464 | 0 | Qwen3-VL-32B 的 INT8 量化 + ComfyUI 适配版本，Heretic 社区定制，提升多模态推理效率。 |
| [MiniMax-H3_comfy](https://huggingface.co/Kijai/MiniMax-H3_comfy) | Kijai | 280 | 0 | Kijai 出品的 MiniMax-H3 ComfyUI 实验性集成，面向视频生成工作流探索者。 |
| [MiniMax-H3-experimental](https://huggingface.co/Kijai/MiniMax-H3-experimental) | Kijai | 196 | 0 | MiniMax-H3 实验性变体，社区创作者探索视频生成模型的不同配置与应用场景。 |
| [PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 268 | 0 | 基于 Apache 2.0 协议的 MiniMax-H3 微调版本，针对特定风格进行优化。 |

---

## 生态信号

本周生态呈现三股显著趋势。首先，**MiniMax-H3 视频生成模型家族**爆发式增长，从官方基础模型到 LoRA 微调、GGUF 量化、ComfyUI 集成，生态链已高度成熟，显示社区对视频生成工具的强劲需求。其次，**量化与本地部署**仍是核心主线，unsloth 对 DeepSeek-V4、MiniMax-H3 等热门模型的 GGUF 版本快速跟进，下载数据印证了本地化推理的持续升温。最后，**安全与合规模型**（如 Shieldstral-1.0-3B）开始进入热门榜单，反映企业对 AI 安全工具的需求正在上升。开源权重仍占主流，但闭源模型的微调衍生版本（如 Heretic、Fable 等社区定制）也 gaining traction，显示出"开源基础模型 + 社区差异化微调"已成为主流创新模式。

---

## 值得探索

1. **[DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731)** — 超百万下载量验证其综合竞争力，Flash 优化带来出色的推理效率，是追求性价比语言模型的优先选择。

2. **[MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 本周视频生成领域的核心模型，生态丰富度高，从官方模型到各种 LoRA 和 ComfyUI 集成一应俱全，适合深入探索视频生成工作流。

3. **[Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B)** — Mistral 出品的轻量安全护栏模型，3B 参数适合生产环境部署，在 AI 安全合规需求日益增长的大背景下具有实用价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*