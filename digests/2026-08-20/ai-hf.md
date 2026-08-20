# Hugging Face 热门模型日报 2026-08-20

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-20 01:38 UTC

---



# Hugging Face 热门模型日报
**日期：2026-08-20 | 分析师：Sapiens AI**

---

## 今日速览

Kimi-K3 与 Qwen3.8-27B 双雄并立，周赞数均突破万级，彰显主流开源 LLM 的持续号召力。MiniMax-H3 视频生成模型下载量突破 300 万，社区对高质量多模态生成工具需求旺盛。Qwen3.8 系列量化版（GGUF/FP8/NVFP4）被社区密集搬运与微调，abliterated 与 uncensored 版本活跃度高，反映本地化部署与自由化微调的强劲趋势。DeepSeek-V4-Pro 与 LTX-2.5 亦进入榜单前列，竞争格局日趋多元。

---

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
|:---|:---|---:|---:|:---|
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,854 | 2,289,863 | Moonshot 推出的多模态对话模型，支持图文理解与生成，采用 compressed-tensors 技术优化推理效率。 |
| [Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 11,487 | 1,006,235 | 阿里云通义千问系列 27B 参数多模态语言模型，支持图像-文本联合理解与对话，性能位居开源榜单前列。 |
| [DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 634 | 37,583 | DeepSeek 最新 Pro 版本，专注文本生成与复杂推理任务，代表国产开源模型的技术进阶。 |
| [Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,702 | 430,313 | 多模态对话模型，30B 参数规模支持图像-文本联合理解，在开源生态中崭露头角。 |
| [dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 232 | 1,239 | 新一代多模态语言模型前驱版本，探索文本与图像联合生成能力。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
|:---|:---|---:|---:|:---|
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,185 | 3,055,205 | MiniMax 最新多模态生成模型，支持文本/图像到视频生成，下载量突破 300 万，社区热度极高。 |
| [LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,325 | 555,993 | Lightricks 视频生成模型，支持图生视频、文生视频及视频重绘，在创意生成领域表现突出。 |
| [MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,038 | 13,138 | MiniMax 音乐生成模型，支持文本到音乐生成，填补开源音乐生成工具空白。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

> 本期榜单中暂无专注于代码、数学、医疗或嵌入的专用模型。

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
|:---|:---|---:|---:|:---|
| [Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,085 | 4,318,134 | Unsloth 整理的 Qwen3.8-27B GGUF 量化版本，下载量突破 430 万，是本地部署首选方案之一。 |
| [Qwen3.6-27B-Fable-Fusion-Uncensored-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,165 | 3,033,363 | 融合 Heretic 与 Abliteration 技术的无审查 GGUF 模型，下载量超 300 万，社区活跃度极高。 |
| [MiniMax-H3 (ComfyUI)](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,445 | 15,213,225 | MiniMax-H3 的 ComfyUI 集成版本，累计下载量超 1500 万，是视频生成工作流的核心组件。 |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,549 | 2,330,940 | DeepSeek V4 快速推理版本，兼顾性能与速度，下载量突破 230 万。 |
| [Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 601 | 1,063,646 | Qwen 官方 FP8 量化版本，平衡显存占用与推理质量，适合 24GB+ 显卡部署。 |
| [Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 614 | 60,078 | orcarouter 对 Qwen3.8-27B 进行 abliterated 无审查处理的 FP8 量化版本。 |
| [Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,100 | 12,699 | Qwen3.8 MoE 大规模稀疏模型（2.4T 参数/95B 激活），代表开源 MoE 架构的技术前沿。 |
| [Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 601 | 27 | Apple Silicon 适配的无审查 MLX 格式版本，支持本地 Mac 部署。 |
| [Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 188 | 26,472 | orcarouter 出品的 Qwen3.8 无审查 GGUF 版本，社区定制代表作。 |
| [Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 197 | 32,454 | empero-ai 整理的 Ridge 量化 GGUF 版本，优化推理性能。 |
| [Qwen3.8-27B-ABLITERATED-GGUF](https://huggingface.co/Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF) | Blackfrost-AI | 170 | 164,263 | Blackfrost 团队的 abliterated 无审查 GGUF 版本，下载量超 16 万。 |
| [Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 172 | 94,234 | huihui-ai 的 abliterated GGUF 版本，本地社区活跃用户。 |
| [Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 160 | 245,266 | 融合 Heretic 与 Abliteration 双技术的无审查 GGUF 版本，下载量超 24 万。 |
| [MiniMax-Music-3 (ComfyUI)](https://huggingface.co/Comfy-Org/MiniMax-Music-3) | Comfy-Org | 193 | 325,083 | MiniMax-Music3 的 ComfyUI 集成版本，支持音频生成工作流。 |
| [Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 625 | 340,984 | MiniMax-H3 的 Turbo 加速版本，优化视频生成推理速度。 |
| [10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 283 | 0 | MiniMax-H3 的微调变体，专注图像-文本到视频生成。 |
| [Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 270 | 26,566 | 轻量级 2.9B 文本到图像生成模型，适配 ComfyUI 工作流。 |
| [Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,290 | 0 | Qwen 系列聊天模板修复工具，解决部分模型对话格式兼容问题。 |
| [Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 288 | 653,042 | Unsloth 推出的 NVFP4 量化版本，面向 NVIDIA 硬件优化推理性能。 |
| [Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 167 | 7,207 | huihui-ai 的 safetensors 格式 abliterated 版本。 |
| [Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 288 | 131,113 | HauhauCS 的激进 MTP 无审查 GGUF 版本，支持多轮对话与多任务处理。 |

---

## 生态信号

本期榜单呈现三大趋势：其一，**Qwen3.8 系列成为社区量化与微调的核心基础模型**，unsloth、orcarouter、huihui-ai 等团队密集产出 GGUF/FP8/NVFP4 等多格式变体，abliterated 无审查技术已被广泛采用；其二，**视频生成赛道竞争白热化**，MiniMax-H3 及其 ComfyUI 集成版本下载量合计超 1800 万，LTX-2.5 与 Turbo 加速版同步涌入榜单；其三，**国产开源 LLM（Kimi、DeepSeek、Qwen）集体霸榜**，证明国内模型生态已进入与开源社区深度互动的成熟阶段，闭源与开源的边界逐步模糊。

---

## 值得探索

1. **[Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 月之暗面最新旗舰，压缩张量技术优化推理效率，周赞 10,854、下载 229 万，是当前开源多模态对话模型的代表作，值得对比测试其 reasoning 与多模态能力。

2. [MiniMax-H3 (ComfyUI)](https://huggingface.co/Comfy-Org/MiniMax-H3) — 累计下载超 1500 万，视频生成工作流的核心基础设施。ComfyUI 集成使其易于接入现有 creative pipeline，适合视频生成爱好者与创作者。

3. [DavidAU/Qwen3.6-27B-Fable-Fusion-Uncensored-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) — 融合 Heretic 与 Abliteration 双技术的旗舰无审查模型，下载量超 300 万，代表社区定制微调的技术高度，适合研究本地化自由推理场景。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*