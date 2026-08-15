# Hugging Face 热门模型日报 2026-08-15

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-15 01:37 UTC

---



# 📊 Hugging Face 热门模型日报
**2026-08-15 · 按周点赞排序**

---

## 一、今日速览

本月 Hugging Face 热门榜单呈现"三足鼎立"格局：月之暗面 Kimi-K3 以超万赞领跑语言模型赛道，Qwen 与 DeepSeek 紧随其后持续输出大参数版本。视频生成领域 MiniMax-H3 系列成为绝对焦点，单模型下载量突破 199 万，带动 ComfyUI 生态和 LoRA 微调同步爆发。与此同时，量化生态异常活跃，Unsloth 和 Meta 官方同步推出 GGUF 版本，FP8 量化亦被开源社区广泛采用。

---

## 二、热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,675 | 1,974,635 | 月之暗面最新一代多模态语言模型，采用压缩张量技术，周下载近 200 万。在文本理解和对话任务上表现均衡，目前热度第一。 |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 9,026 | 2 | 通义千问最新一代 27B 参数语言模型，支持图像-文本到文本对话。官方首发，标签涵盖 qwen3_5 架构，潜力巨大。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,385 | 1,606,491 | DeepSeek V4 系列 Flash 版本，强调推理速度。周下载超 160 万，是社区落地规模最大的开源 LLM 之一。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 918 | 3,832 | 通义千问 MoE 架构超大模型，总参数 2.4 万亿，激活参数 950 亿。代表当前开源 MoE 模型的规模天花板。 |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 615 | 124,172 | LiquidAI 推出的高效语言模型，采用液态架构创新，在资源受限场景下实现高吞吐推理。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 257 | 119,572 | NVIDIA 轻量级 MoE 模型，采用 NVFP4 自定义量化格式，30B 总量仅激活 3B，推理效率突出。 |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 235 | 2,283 | inclusionAI 推出的多语言小型语言模型，聚焦低资源语言环境，MIT 许可便于商用。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 143 | 34,137 | NVIDIA Nemotron 系列 BF16 版本，与 NVFP4 版形成互补，兼顾精度与部署灵活性。 |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 142 | 11 | 社区新兴语言模型，专注笔记与文本生成场景，尚在早期积累阶段。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,920 | 1,997,541 | MiniMax 最新视频生成模型，支持文生视频和图生视频，周下载近 200 万，是当前视频生成领域最受关注的开源模型。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,515 | 165,300 | Meta 最新多模态模型，图片文本到文本生成，在视觉理解和对话任务上表现均衡，社区热度持续攀升。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,318 | 11,768,622 | MiniMax-H3 的 ComfyUI 集成版本，周下载量超 1176 万，是视频生成领域社区适配最活跃的模型之一。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 859 | 207,830 | Lightricks 视频生成模型，支持单文件扩散，兼容文本/图像/视频生成多种模式，适合内容创作者。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 653 | 63 | MiniMax 音乐生成模型，支持文生音频，延续 H3 系列高质量生成能力，拓展至音频领域。 |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 493 | 149,865 | MiniMax-H3 的 Turbo 加速版，在图生视频场景显著降低推理延迟，社区采用广泛。 |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 162 | 10,106 | Anima 轻量图像生成模型，基于单文件扩散架构，适合资源受限场景的图像创作。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,017 | 2,891,524 | 社区基于 Qwen3.6-27B 的无限制微调版本，周下载近 290 万，反映用户对定制化开源模型的强烈需求。 |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 815 | 0 | Unsloth 对 Qwen3.8-27B 的 GGUF 量化版本，专为本地部署优化推理效率，降低显存门槛。 |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 414 | 596,774 | Unsloth 对 Meta Muse-Glimmer-30B 的 GGUF 量化版，周下载近 60 万，说明多模态模型的本地化部署需求旺盛。 |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 156 | 136,774 | Unsloth 对 MiniMax-H3 的 GGUF 量化版本，实现视频生成模型的本地部署，降低硬件门槛。 |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 270 | 228,364 | Meta 官方发布的 Muse-Glimmer-30B GGUF 版本，为模型原生量化，推理速度提升明显。 |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 302 | 0 | Qwen 官方 FP8 量化版本，在精度与效率间取得平衡，适合显存有限的推理场景。 |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 184 | 9,334 | Qwen MoE 超大模型的 FP8 版本，显著降低推理成本，是开源 MoE 模型轻量化的重要尝试。 |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 742 | 0 | 基于 MiniMax-H3-Turbo 的 LoRA 微调版本，针对特定视频生成风格进行适配，扩展模型应用边界。 |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 177 | 9,060 | fal.ai 推出的 MiniMax-H3 人像写实风格 LoRA，专注于人物视频生成，推动视频模型的垂直细分。 |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 318 | 112,975 | MiniMax-H3-Turbo 的 ComfyUI 适配 LoRA，整合工作流，在 ComfyUI 生态中下载活跃。 |

---

## 三、生态信号

本月生态呈现三大趋势：**其一，视频生成成为最热赛道**，MiniMax-H3 及其衍生模型（Turbo、LoRA、ComfyUI 集成）占据榜单近半席位，说明视频生成已进入社区共创的成熟期。**其二，量化生态空前繁荣**，Unsloth、Meta 官方、Qwen 官方均在 GGUF 和 FP8 方向密集布局，反映本地部署需求持续高涨。**其三，头部 LLM 家族持续迭代**，Qwen3.8、DeepSeek-V4、Kimi-K3 三大家族齐头并进，开源与闭源差距在性能上逐步缩小。值得注意的是，DavidAU 的无限制微调版 Qwen3.6-27B 下载量超 289 万，说明社区对定制化、去限制模型的需求依然旺盛。

---

## 四、值得探索

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 周赞 10,675、下载近 200 万，当前无可争议的第一。压缩张量技术使其在保持多模态能力的同时大幅降低推理成本，是研究和部署的首选。

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成领域的标杆级开源模型，周下载近 200 万且衍生生态（LoRA、Turbo、ComfyUI）丰富。无论是直接调用还是二次微调，都是当前最具潜力的视频生成模型。

3. **[DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-G

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*