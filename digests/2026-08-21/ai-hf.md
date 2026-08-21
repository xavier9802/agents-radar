# Hugging Face 热门模型日报 2026-08-21

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-21 01:43 UTC

---



# 📊 Hugging Face 热门模型日报
**日期：2026-08-21 | 统计口径：周点赞数 Top 30**

---

## 一、今日速览

今日榜单被 **Qwen3.8-27B** 系列全面主导，官方原始模型以 11,751 赞登顶，社区贡献了十余个 GGUF / FP8 / MLX / abliterated 等变体，呈现"一核多翼"格局。**Kimi-K3** 以 10,884 赞紧随其后，DeepSeek-V4 系列（Flash 版下载量超 250 万）同样亮眼。多模态方向，**MiniMax-H3** 和 **LTX-2.5** 的视频生成能力持续吸引关注。整体趋势：开源 27B 级密集模型仍是社区微调与量化的首选底座，MCP / abliterated 等越狱玩法热度不减。

---

## 二、热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 11,751 | 1,373,584 | Qwen3.8 系列旗舰密集模型，支持图文对话，官方权重下载量超 137 万。登顶周榜，表明 27B 级别开源模型仍是社区首选底座。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,884 | 2,349,853 | Moonshot 开源的多模态语言模型，支持图文理解与对话，下载量超 234 万，用户关注度与 Qwen 并列第一梯队。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,576 | 2,547,549 | DeepSeek-V4 快速推理版本，侧重低延迟对话任务，下载量突破 254 万，是榜单中下载量最高的 DeepSeek 模型。 |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,242 | 3,308,673 | 多模态大模型，主打图文理解与视频生成基础能力，下载量超 330 万，为社区视频生成微调提供了热门底座。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,718 | 478,622 | 30B 参数多模态对话模型，支持图像-文本到文本任务，下载量近 48 万，是 30B 级别开源模型中关注度较高的代表。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 682 | 43,287 | DeepSeek-V4 专业版，侧重高质量对话与推理任务，下载量 4.3 万，适合对生成质量要求较高的研究场景。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,121 | 14,592 | Qwen3.8 MoE 文本生成架构（2.4T 总参数 / 95B 激活），稀疏专家设计兼顾性能与推理效率，适合研究 MoE 路径。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 221 | 1,713 | 35B MoE 模型（3B 激活），支持图文理解与文本生成，下载量 1,713，属于社区新兴 MoE 探索方向。 |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 242 | 1,373 | 轻量级图文对话模型，下载量较低但代表社区对小型化、低功耗 LLM 的持续探索。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 714 | 2,628 | 基于 Qwen3.8-27B 的 MLX 格式 abliterated 版本，针对 Apple Silicon 优化，适合本地运行无约束对话场景。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 678 | 76,109 | Qwen3.8-27B 的 FP8 量化 abliterated 版本，显存占用低、推理速度快，下载量超 7.6 万。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 514 | 979,768 | GGUF 格式 abliterated 模型，兼容 llama.cpp 生态，下载量接近 98 万，是本地部署热门选择。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 239 | 52,382 | 另一款 orcarouter 出品的 GGUF abliterated 变体，进一步覆盖不同量化档位用户需求。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 368 | 268,258 | 采用 MTP（Multi-Token Prediction）加速的 abliterated GGUF 版本，兼顾推理速度与无约束输出。 |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 225 | 55,074 | Ridge 量化策略 GGUF 模型，探索不同量化算法对质量与速度的平衡。 |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 190 | 326,638 | "Heretic" 方向的 abliterated GGUF 变体，下载量超 32 万，显示社区对越狱模型的需求持续旺盛。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 201 | 187,008 | huihui-ai 出品的 GGUF abliterated 版本，下载量约 18.7 万，覆盖更多本地部署用户。 |
| [Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF](https://huggingface.co/Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF) | Blackfrost-AI | 183 | 186,470 | Blackfrost-AI 的 abliterated GGUF 变体，下载量近 18.6 万，进一步丰富社区可选档位。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 202 | 10,540 | huihui-ai 的 safetensors 原始格式 abliterated 版本，适合需要自行二次量化的用户。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 270 | 4,415 | OBLITERATUS 出品的 abliterated 模型，支持 MLX 与 GGUF 格式，下载量 4,415，属于小众但活跃的探索方向。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,417 | 611,825 | 图像到视频生成模型，支持多种视频编辑模式（t2v / i2v / r2v），下载量超 61 万，是榜单中视频生成方向最热模型。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,106 | 14,471 | MiniMax 第三代文本到音乐生成模型，支持高质量音频创作，下载量 1.4 万，代表音频生成赛道的持续升温。 |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 299 | 0 | 基于 MiniMax-H3 微调的视频生成模型，支持图像/文本到视频，下载量为 0 表示刚发布，值得关注后续表现。 |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 654 | 380,072 | 基于 MiniMax-H3 的加速推理版本，专注图像到视频生成，下载量超 38 万，适合需要快速迭代的视频生成工作流。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,340 | 0 | 修复 Qwen 系列模型 Chat Template 的工具包，下载量为 0 但点赞近 1,340，说明开发者社区对其实用性高度认可。 |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 156 | 348 | Mini 规模语音识别模型（ASR），下载量 348，代表开源 ASR 领域的小型化探索方向。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,365 | 5,126,652 | unsloth 出品的 Qwen3.8-27B GGUF 量化版本，下载量突破 512 万，是榜单中下载量最高的量化模型，凸显 unsloth 品牌号召力。 |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 308 | 831,483 | 采用 NVIDIA FP4 格式的量化变体，针对 NPU/GPU 硬件优化，下载量超 83 万，代表硬件适配量化的最新进展。 |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 633 | 1,517,643 | 官方 FP8 量化版本，平衡精度与显存占用，下载量超 151 万，适合显存受限的 27B 部署场景。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 163 | 53,691 | Ornith-1.5 的 GGUF 量化版本，兼容 llama.cpp，下载量约 5.3 万，为 MoE 模型本地化部署提供选项。 |

---

## 三、生态信号

**Qwen3.8-27B** 以"一主多副"形态占据榜单半壁江山，社区围绕该底座生成了 GGUF、FP8、MLX、NVFP4、abliterated 等十余种变体，显示 27B 参数级模型已成为开源生态中**最活跃的量化与微调靶点**。DeepSeek-V4 系列（Flash 与 Pro）与 Kimi-K3 分别以差异化定位（速度 vs 多模态）保持高热度。值得注意的是，**abliterated（去约束）模型** 持续出现，表明社区对"越狱"能力的研究并未降温。同时，视频生成方向 MiniMax-H3 及其衍生 Turbo 版本下载量均超 300 万，显示多模态生成仍是开源社区最活跃的增量赛道。

---

## 四、值得探索

1. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 下载量超 512 万，是榜单中量化模型的首选。unsloth 的量化管线经过充分验证，适合需要在消费级 GPU 上部署 27B 模型的开发者。

2. **[Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5)** — 支持多种视频生成模式（文生视频 / 图生视频 / 视频重绘），下载量超 61 万，是目前开源视频生成赛道中功能最全的模型之一。

3. **[Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B)** — MoE 架构的代表作品，2.4T 总参数仅激活 95B，为研究稀疏专家模型的性能-效率平衡提供了极佳的开源实验平台。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*