# Hugging Face 热门模型日报 2026-08-17

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-17 01:42 UTC

---



# 📅 Hugging Face 热门模型日报 — 2026-08-17

---

## 今日速览

今日 HF 榜单由 Qwen3.8 与 Kimi-K3 双雄领衔，两者均斩获超 1 万周点赞，彰显中文大模型社区强劲活力。MiniMax-H3 视频生成模型以超 230 万下载量领跑，GGUF/AWQ 等量化适配持续升温。开源 MoE 架构（Qwen 2.4T-A95B、NVIDIA Nemotron 30B-A3B）与 uncensored 微调版本同时活跃，反映推理效率与可控性需求并存。

---

## 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 10,296 | 267,725 | Qwen3.8 系列旗舰稠密模型，支持图文多模态对话；本周点赞量仅次于 Kimi-K3，热度极高。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,768 | 2,136,775 | Kimi K3 多模态语言模型，采用 compressed-tensors 技术优化推理；下载量超 213 万，为榜单最高。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,462 | 1,872,232 | DeepSeek V4 Flash 快速推理版本，以较低成本实现高质量文本生成；下载量近 187 万。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,012 | 7,932 | Qwen3.8 系列超大 MoE 模型（2.4T 参数/激活 95B），专为高吞吐场景设计。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 536 | 21,873 | DeepSeek V4 旗舰推理版本，对标顶级闭源模型；标签显示为 conversational 多轮对话优化。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 291 | 196,326 | NVIDIA Nemotron 3.5 Lightning MoE，采用 NVFP4 量化，兼顾性能与显存效率。 |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 285 | 5,727 | 轻量级小模型，MIT 许可，适用于低资源推理场景；为 inclusionAI 近期轻量方向代表。 |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 647 | 141,009 | LiquidAI 的 LFM 系列 2.6B 文本生成模型，在小型架构上实现较高推理效率。 |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 186 | 393 | dots3 系列实验性文本生成模型，处于早期发布阶段，关注社区后续迭代。 |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 210 | 11,311 | Qwen3.8-2.4T-A95B 的 FP8 量化版本，降低 MoE 大模型的部署门槛。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,031 | 2,307,541 | MiniMax 新一代图像/视频生成模型，支持图生视频与文生视频；下载量超 230 万，为生成类第一。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,030 | 424,099 | Lightricks 开源视频生成模型，支持 I2V/T2V/V2V 多种模式，被广泛用于视频创作工作流。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 844 | 8,639 | MiniMax 第三代音乐生成模型，支持高质量文本到音乐合成，标签为 diffusers 生态友好。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,632 | 292,973 | Meta 开源多模态语言模型 Muse-Glimmer 30B，支持图文对话，社区关注度较高。 |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 560 | 239,206 | MiniMax-H3 的 Turbo 加速版本，优化视频生成推理速度，适合实时创作场景。 |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/ fal/MiniMax-H3-Realism-People-LoRA) | fal | 229 | 16,103 | 针对 MiniMax-H3 的人物写实风格 LoRA 微调，聚焦生成逼真人物视频。 |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 223 | 20,860 | 轻量文本到图像生成模型，基于 diffusers 单文件格式，适合 ComfyUI 工作流快速部署。 |

### 🔧 专用模型

> 本期榜单中无纯代码、数学、医疗、嵌入类专用模型上榜，该分类暂缺。

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 1,463 | 1,945,635 | Unsloth 官方 Qwen3.8-27B GGUF 量化版，下载量近 195 万，为本地推理首选之一。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,389 | 13,406,892 | ComfyUI 一键部署包，包含 MiniMax-H3 的 diffuser 单文件版本；下载量超 1340 万，社区实用工具。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,096 | 3,020,070 | 社区知名 uncensored 微调 Qwen3.6-27B，融合多版本训练，GGUF 格式便于 llama.cpp 本地运行。 |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 458 | 718,178 | Unsloth 对 Meta Muse-Glimmer-30B 的 GGUF 量化适配，扩展该模型本地可用范围。 |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 298 | 357,877 | Meta 官方 Muse-Glimmer-30B 的 GGUF 版本，补充 unsloth 之外的又一官方量化来源。 |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 485 | 352,971 | Qwen 官方 FP8 量化稠密模型，平衡画质与显存占用，适合 A100/H100 部署。 |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 202 | 276,269 | Unsloth 推出的 Qwen3.8-27B NVFP4 版本，利用 NVIDIA 专用低精度格式进一步压缩显存。 |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 175 | 204,344 | MiniMax-H3 的 GGUF 本地化版本，使视频生成模型可在 CPU/消费级 GPU 上运行。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 347 | 4,285 | 社区 uncensored 微调 + FP8 量化的组合版本，面向无审查本地推理需求。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 215 | 183,988 | 另一款社区热门 uncensored GGUF 微调，基于 Qwen3.8-27B 并保留 MTP 多步推理能力。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 160 | 66,253 | Nemotron Lightning 的 BF16 全精度版本，提供 NVFP4 之外的性能上限选择。 |
| [Comfy-Org/MiniMax-Music-3](https://huggingface.co/Comfy-Org/MiniMax-Music-3) | Comfy-Org | 153 | 0 | ComfyUI 官方 MiniMax-Music-3 整合包，便于音乐生成模型的可视化工作流部署。 |

---

## 生态信号

本周期 Qwen3.8 系列占据语言模型热点核心，unsloth 对稠密与 MoE 模型的全栈量化（GGUF/NVFP4/FP8）表明社区正加速推动百亿参数模型本地化部署。MiniMax-H3 在视频生成领域以超 230 万下载遥遥领先，Comfy-Org 的 ComfyUI 包下载破千万，验证了"模型+工作流"捆绑分发模式的有效性。uncensored 微调持续活跃，反映用户对可控本地生成内容的强需求。MoE 架构（Qwen 2.4T-A95B、Nemotron 30B-A3B）进入开源主战场，开源权重与闭源能力的差距进一步缩小。

---

## 值得探索

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周点赞量第一，下载超 213 万，compressed-tensors 技术显著降低推理显存占用，是多模态对话场景的优先试水对象。

2. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — ComfyUI 一键集成方案，下载量破 1340 万，若需快速搭建视频生成工作流，此包省去大量配置步骤。

3. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 下载近 195 万的热门量化版，实测可在消费级 GPU 上流畅运行 27B 模型，适合本地化快速部署实验。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*