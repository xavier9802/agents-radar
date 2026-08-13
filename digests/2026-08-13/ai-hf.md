# Hugging Face 热门模型日报 2026-08-13

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-13 02:27 UTC

---



# Hugging Face 热门模型日报 — 2026-08-13

## 今日速览

Moonshot AI 的 **Kimi-K3** 以超 1 万点赞领跑本周榜单，多模态对话模型持续受热捧。**MiniMax-H3** 视频生成生态异常繁荣，从官方基座到 ComfyUI 集成、各类 LoRA 微调再到 GGUF 量化，已形成完整工具链。DeepSeek-V4-Flash 系列维持高下载量，unsloth 的 GGUF 量化版本同步上线。NVIDIA Nemotron 3.5 Lightning 系列首次进入热门榜，FP4 量化推理路线值得关注。社区对 uncensored/无限制模型的持续需求推动 Qwen3.6 微调版下载量突破 250 万。

---

## 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,584 | 1,565,484 | Moonshot AI 多模态对话模型，支持图像-文本交互，本周点赞最高。使用 compressed-tensors 技术压缩权重，兼顾性能与部署效率。 |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,241 | 1,048,685 | DeepSeek 最新旗舰推理模型，对话能力突出，下载量逾百万。Flash 版本针对推理速度优化，适合生产部署。 |
| [Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,960 | 2,521,093 | 基于 Qwen3.6-27B 的无限制社区微调版，下载量突破 250 万，社区对 uncensored 模型的持续需求显著。采用 Heretic 系列微调技术栈。 |
| [LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 586 | 93,668 | LiquidAI 轻量级语言模型，2.6B 参数量适合边缘/端侧部署。支持特征提取，在小模型赛道展现竞争力。 |
| [NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 207 | 19,250 | NVIDIA Nemotron 3.5 推理加速系列，采用 NVFP4 低精度量化，激活值仅 3B，大幅降低显存占用。首次进入热门榜，代表推理效率优化新方向。 |
| [NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 355 | 653 | NVIDIA 语音对话专用模型，集成最新 arxiv 研究成果，面向实时语音交互场景。 |
| [Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 319 | 6,148 | inclusionAI 快速推理版本，采用 bailing_hybrid 架构，开源 MIT 协议，支持自定义代码扩展。 |

---

## 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,718 | 83,484 | MiniMax 官方视频生成模型，支持文生视频和图生视频，本周多模态生成领域核心模型。使用 diffusers 生态，推理效率优秀。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,259 | 6,798,796 | MiniMax-H3 的 ComfyUI 集成版本，下载量近 680 万，是本周下载最高的模型。为 ComfyUI 用户提供了开箱即用的视频生成工作流。 |
| [LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 575 | 39 | Lightricks 新一代视频生成模型，支持图生视频、文生视频和视频到视频，单文件扩散架构便于部署。 |
| [Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 412 | 20,376 | lightx2v 社区的 MiniMax-H3 Turbo 加速版本，支持 T2V/I2V/R2V 多种生成模式，推理速度优化。 |
| [Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,302 | 0 | Meta 多模态大模型，支持图像-文本到文本生成，30B 参数规模具备较强视觉理解能力。相关 arxiv 论文编号已公开。 |

---

## 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 193 | 0 | inclusionAI 轻量级模型，bailing_hybrid 架构，MIT 协议开源，适合资源受限场景的探索性研究。 |
| [maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 346 | 2,049 | deepgrove MoE 架构语言模型预览版，因果 LM 任务，参数高效，适合推理加速研究。 |
| [endless-frontier/BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-frontier | 182 | 708 | 基于 Qwen3.5 MoE 的多模态模型，支持图像-文本到文本生成，对话能力突出。 |

---

## 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 666 | 207,990 | DeepSeek-V4-Flash 的 GGUF 量化版本，由 unsloth 提供，支持本地高效部署。引用 arxiv:2606.19348 技术论文。 |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 362 | 0 | Meta Muse-Glimmer 30B 的 GGUF 量化版本，降低本地推理硬件门槛。 |
| [miniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 137 | 781 | MiniMax-H3 视频生成模型的 GGUF 量化版本，支持 stable-diffusion.cpp 本地推理，推动视频生成本地化部署。 |
| [MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 701 | 0 | 基于 MiniMax-H3 的 Turbo 加速 LoRA 微调，同时支持文生视频和文生音频跨模态生成。 |
| [MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 147 | 0 | fal 推出的 MiniMax-H3 人物写实风格 LoRA，针对人像生成质量优化，适配影视/设计工作流。 |
| [MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 141 | 353 | 提示词重写 LoRA，自动优化输入 prompt 以提升 MiniMax-H3 视频生成质量，形成生成-优化闭环工具链。 |
| [Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 122 | 3,851 | Qwen3.8 超大参数 MoE 模型的 FP8 量化版本，在保持推理质量的同时显著降低显存需求。 |
| [NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 117 | 15,740 | Nemotron 3.5 Lightning BF16 精度版本，与 NVFP4 版本形成精度-效率互补矩阵，供用户按需选择。 |
| [Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 529 | 978 | Qwen 最新超大参数 MoE 语言模型，2.4T 总参数量、95B 激活参数，代表开源 LLM 规模竞赛新高度。 |
| [Meta-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 241 | 0 | Muse-Glimmer 30B 官方 GGUF 版本，引用 arxiv:2504.13181 和 arxiv:2602.06036 两项技术论文。 |

---

## 生态信号

本周视频生成赛道呈现**完整工具链化**趋势：MiniMax-H3 从官方基座（MiniMaxAI）→ ComfyUI 集成（Comfy-Org）→ 加速 LoRA（lightx2v）→ 风格 LoRA（fal）→ GGUF 量化（unsloth），仅一周即形成覆盖生产全链路的模型矩阵。语言模型则延续**"旗舰推理 + 量化适配"双轨策略**，DeepSeek、Kimi、Qwen 三强并行推进 Flash/推理优化版本，unsloth 的 GGUF 适配速度持续领先。NVIDIA Nemotron 3.5 Lightning 系列首次上榜，**NVFP4 等低精度量化技术**正成为推理效率新标杆。此外，社区对 uncensored 模型的持续热情推动 Qwen3.6 Heretic 微调版下载量突破 250 万，反映开源 AI 在内容自由度的长期诉求。

---

## 值得探索

1. **[Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周点赞最高的多模态模型（10,584），compressed-tensors 技术值得研究，是中文生态多模态对话的标杆之作。

2. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — 下载量近 680 万，证明了 ComfyUI 生态在视频生成工作流中的核心地位，适合探索节点化视频生成管线。

3. **[NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4)** — FP4 量化推理的新路径，30B 模型仅激活 3B 参数，代表了极致推理效率的技术方向，值得开发者关注。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*