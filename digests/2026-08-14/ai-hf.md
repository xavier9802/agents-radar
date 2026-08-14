# Hugging Face 热门模型日报 2026-08-14

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-14 02:26 UTC

---



# Hugging Face 热门模型日报
**日期：2026-08-14**

---

## 一、今日速览

今日 HF 热门榜被 **MiniMax-H3 视频生成模型** 及其衍生生态全面占据，官方权重、ComfyUI 封装、LoRA 微调、GGUF 量化等周边版本扎堆上榜，显示社区对高质量视频生成的狂热追捧。**Kimi-K3** 以 10,624 赞稳居图文多模态模型榜首，DeepSeek-V4 家族在 LLM 赛道持续发力。同时，**Muse-Glimmer-30B** 的 GGUF 量化版本获得 unsloth 社区加持，下载量可观。量化（GGUF）和 ComfyUI 工作流适配仍是本周最活跃的生态方向。

---

## 二、热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,624 | 1,871,575 | Moonshot AI 推出的最新一代多模态语言模型，支持图像-文本理解与对话。以超过 10 万点赞位居今日榜单首位，显示国内用户对 Kimi 系列的极高关注度。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,324 | 1,431,587 | DeepSeek V4 系列的 Flash 版本，面向高效推理优化。下载量突破 140 万，是今日最受欢迎的国产开源 LLM 之一。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,989 | 2,793,115 | 基于 Qwen3.6-27B 的社区无约束微调版本，采用 Heretic 框架。下载量近 280 万，反映用户对定制化、越狱风格 LLM 的持续需求。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,427 | 121,042 | 300 亿参数图文多模态模型，支持图像-文本到文本生成。标签中包含 muse_glimmer，可能为 Meta 相关研究项目，下载量超 12 万。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 308 | 0 | DeepSeek V4 系列的 Pro 版本，发布于 8 月 13 日。目前下载量为 0，可能为最新发布尚未开始传播。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 230 | 44,859 | NVIDIA Nemotron 3.5 Lightning 系列，采用 NVFP4 量化格式，激活值为 3B。面向高效推理场景，适合边缘或低延迟部署。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 131 | 22,279 | 同系列的 BF16 精确度版本，适合对质量要求更高但显存预算充足的场景。与 NVFP4 版本形成互补。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 795 | 1,012 | Qwen3.8 系列 MoE 架构模型，总参数 2.4T，激活 95B。目前下载量较低，可能为新发布或仍在推广阶段。 |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 603 | 116,640 | LiquidAI 的 LFM 2.5 系列，2.6B 参数量，采用 Liquid 架构设计。下载量超 11 万，展示小型高效语言模型的竞争力。 |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 354 | 3,868 | MoE 架构的预览版文本生成模型，目前下载量较低但点赞表现稳健，可能为早期测试阶段。 |
| [endless-frontier/BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-frontier | 188 | 3,184 | 基于 Qwen3.5 MoE 架构的图文多模态对话模型，社区新发布，目前处于早期探索阶段。 |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 373 | 1,164 | NVIDIA NemotronLabs 推出的 11B 语音对话专用模型，针对语音交互场景优化，附带多篇相关 arXiv 论文。 |

---

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,831 | 1,605,940 | MiniMax 官方发布的图像/文本到视频生成模型，今日热度最高的视频模型，下载量超 160 万，标签涵盖 text-to-video、image-to-video、video-to-video 等多种模式。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,291 | 10,365,210 | ComfyUI 生态对 MiniMax-H3 的封装版本，下载量突破 1036 万，是榜单下载量最高的模型，证明 ComfyUI 工作流在视频生成领域的统治力。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 729 | 57,287 | Lightricks 推出的高性能视频生成模型，支持 image-to-video、text-to-video 和 video-to-video，是 MiniMax-H3 之外的重要竞品。 |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 462 | 91,455 | 基于 MiniMax-H3 的 Turbo 加速版本，提供更快的推理速度，适合实时或高频生成场景。 |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 389 | 352,023 | unsloth 对 Muse-Glimmer-30B 的 GGUF 量化版本，下载量超 35 万，显示社区对本地化部署图文多模态模型的强烈需求。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 352 | 25 | MiniMax 的音乐生成模型，支持 text-to-audio，目前下载量较低，可能刚发布。 |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 257 | 136,783 | Muse-Glimmer-30B 的官方 GGUF 版本，附带 arXiv 论文引用，提供学术可信度与本地部署便利性。 |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 159 | 4,692 | 针对人物写实风格的 MiniMax-H3 LoRA 微调，适合生成高质量人物视频内容。 |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 133 | 0 | 基于 ComfyUI 的轻量级文生图模型，2.9B 参数适合资源有限的本地部署。 |

---

### 🔧 专用模型（代码、数学、医疗、嵌入）

*本期热门榜暂无专门面向代码、数学、医疗或嵌入任务的模型。*

---

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 149 | 111,222 | unsloth 对 MiniMax-H3 的 GGUF 量化版本，使视频生成模型可在消费级 GPU 上本地运行，下载量超 11 万。 |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 162 | 4,000 | Qwen3.8 MoE 模型的 FP8 量化版本，平衡精度与显存占用，适合中等规模部署。 |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 726 | 0 | 基于 MiniMax-H3 Turbo 的 LoRA 微调版本，目前下载量为 0，可能为新发布或仍在训练中。 |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 314 | 0 | 适配 ComfyUI 的 MiniMax-H3 Turbo LoRA，为 ComfyUI 用户提供便捷微调能力。 |
| [lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 149 | 652 | 针对 MiniMax-H3 的提示词重写 LoRA，通过优化输入提示提升视频生成质量。 |
| [SexGod1979/PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 298 | 324 | 风格化微调的 MiniMax-H3，APACHE 2.0 协议，面向特定美学风格定制。 |
| [Kijai/MiniMax-H3_comfy](https://huggingface.co/Kijai/MiniMax-H3_comfy) | Kijai | 308 | 0 | Kijai 为 ComfyUI 提供的 MiniMax-H3 集成版本，专注美国区域用户，目前下载量为 0。 |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 483 | 0 | 基于 Qwen3-VL-32B 的 INT8 量化 + ConvRot 优化版本，适配 ComfyUI 工作流，面向高性能本地部署。 |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 216 | 1,292 | inclusionAI 的轻量级模型，MIT 协议，适合教育和研究用途。 |

---

## 三、生态信号

本周 Hugging Face 热门榜呈现出**视频生成模型生态的爆发式扩张**。MiniMax-H3 及其衍生版本（Turbo、LoRA、GGUF、ComfyUI 封装）占据近半数席位，Comfy-Org 的封装版本下载量突破 1036 万，是榜单下载量最高的模型，证明**工作流适配**已成为模型传播的关键杠杆。同时，**GGUF 量化**持续升温，unsloth 和 meta-models 均推出 Muse-Glimmer-30B 的 GGUF 版本，反映社区对本地化部署的强烈需求。开源 LLM 方面，Kimi-K3 以超 1 万点赞领跑，DeepSeek-V4 系列紧随其后，国产模型在开源生态中的影响力持续增强。

---

## 四、值得探索

1. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — 下载量超 1036 万，是今日榜单绝对的下载之王。ComfyUI 封装让视频生成工作流极大简化，是评估 MiniMax-H3 实际能力的最佳入口。

2. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 点赞数 10,624 位居榜首，代表当前多模态语言模型的社区风向。compressed-tensors 标签暗示模型经过压缩优化，适合研究高效多模态推理方案。

3. **[unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/unsloth/Muse-Glimmer-30B-GGUF)** — unsloth 的量化加持使 30B 参数的图文多模态模型可在消费级硬件运行，下载量超 35 万，是探索本地多模态部署的实用选择。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*