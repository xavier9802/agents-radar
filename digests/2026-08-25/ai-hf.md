# Hugging Face 热门模型日报 2026-08-25

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-25 01:39 UTC

---



# Hugging Face 热门模型日报 — 2026-08-25

## 今日速览

今日 HF 榜单被**Qwen3.8-27B 家族**彻底占领，原版+FP8+GGUF 三版齐发，社区涌现十余个 abliterated/Uncensored 微调版本，总下载量突破千万。**Moonshot AI 的 Kimi-K3** 以近 1.1 万赞紧随其后，国产大模型竞争白热化。多模态赛道同样热闹，**MiniMax-H3** 视频生成模型下载量逼近 450 万，**LTX-2.5** 与 **MiniMax-Music3** 分别领跑视频与音乐生成。

---

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 12,517 | 2,645,226 | Qwen 官方旗舰 27B 模型，支持图文对话，本周下载量最高。作为多模态基座，被社区广泛微调。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,973 | 2,787,971 | 月之暗面发布的新款多模态模型，采用 compressed-tensors 压缩技术，兼顾性能与推理效率。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,682 | 3,274,129 | DeepSeek V4 系列 Flash 版本，专注快速对话场景，下载量持续攀升。 |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,839 | 7,009,063 | Unsloth 出品的 GGUF 量化版，700 万+ 下载量，是本地部署 Qwen3.8 的首选方案。 |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,418 | 4,465,161 | MiniMax 多模态生成模型，支持文本/图像到视频，本周下载量近 450 万，表现强劲。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 398 | 60,294 | Ornith 新发布的 MoE 架构模型（35B 总量，激活 3B），适合高效推理场景。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 275 | 988,170 | Ornith 1.5 的 GGUF 量化版本，近 100 万下载，本地部署友好。 |
| [ornith-ai/Ornith-1.5-9B](https://huggingface.co/ornith-ai/Ornith-1.5-9B) | ornith-ai | 204 | 83,192 | Ornith 轻量版 9B 模型，适合边缘设备或资源受限场景。 |
| [ornith-ai/Ornith-1.5-9B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-9B-GGUF) | ornith-ai | 187 | 971,104 | Ornith 9B 的 GGUF 量化版，下载量接近 100 万，社区接受度高。 |
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 214 | 50,763 | 基于 Qwen3.8 的 Speculative Decoding 加速版本，推理速度提升明显。 |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 230 | 2,976 | 超小尺寸 1M 参数模型，兼顾文本生成与 ASR 能力，适合极致轻量场景。 |
| [incoai/Qwen3.8-27B-DFlash2](https://huggingface.co/incoai/Qwen3.8-27B-DFlash2) | incoai | 173 | 85,034 | 另一款 Qwen3.8 的 Speculative Decoding 优化版本，推理效率提升。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,725 | 790,378 | Lightricks 发布的多模态生成模型，支持图生视频/文生视频/视频重绘，是视频生成赛道热门选择。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,228 | 18,065 | MiniMax 音乐生成模型，支持文本到音乐创作，是音频生成领域的新锐力量。 |
| [Audio8/Audio8-TTS-Preview-0.1b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.1b) | Audio8 | 146 | 2,775 | 超轻量 TTS 模型（0.1B 参数），预览版已发布，适合嵌入式或移动端语音合成。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,447 | 0 | 修复 Qwen 系列模型 chat template 问题的 Jinja 模板工具，解决社区长期痛点。 |
| [peculiar-ragdoll/Qwen-Sharp-Chat-Templates](https://huggingface.co/peculiar-ragdoll/Qwen-Sharp-Chat-Templates) | peculiar-ragdoll | 230 | 0 | 另一款 Qwen chat template 优化工具，针对特定使用场景改进对话格式。 |
| [LBH-123-AI/Minimax_h3_latent_Upscaler](https://huggingface.co/LBH-123-AI/Minimax_h3_latent_Upscaler) | LBH-123-AI | 181 | 0 | MiniMax-H3 的 latent 上采样器，用于提升生成视频的分辨率与质量。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,098 | 224,114 | Qwen3.8 的 FP8 量化 + abliterated 版本，兼顾推理速度与内容自由度。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,030 | 57,947 | 面向 Apple Silicon 的 MLX 格式 abliterated 版本，本地运行流畅。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 690 | 1,456,700 | GGUF 格式的无审查版本，145 万下载量，是本地部署的热门选择。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 696 | 312,627 | Qwen3.8 的 abliterated 版本（MLX/GGUF 双格式），下载量超 30 万。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 580 | 761,975 | 结合 MTP（Multi-Token Prediction）与 aggressive 训练的 GGUF 版本，性能与速度兼顾。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 424 | 143,108 | 另一款 GGUF 格式的 uncensored Qwen3.8，社区广泛使用。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 335 | 1,140,375 | Huihui 团队的 abliterated GGUF 版本，114 万下载量，社区接受度高。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 278 | 27,316 | Huihui 的 safetensors 格式 abliterated 版本，适合标准 Transformer 管线。 |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 260 | 654,805 | "异端"风格的 abliterated GGUF 版本，65 万下载量。 |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 226 | 209,017 | 结合 Cold-Fusion、GAIN 训练与 MTP 的高级微调版本，技术栈复杂。 |
| [orcarouter/Qwen3.8-27B-Uncensored](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored) | orcarouter | 170 | 10,482 | Qwen3.8 的原始 safetensors 格式 abliterated 版本。 |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 681 | 3,004,940 | Qwen 官方 FP8 量化版本，300 万下载量，是推理效率优化的首选。 |

---

## 生态信号

**Qwen3.8-27B 家族**本周统治榜单，原版+FP8+十余个社区微调版本占据半壁江山，abliterated/Uncensored 微调活动异常活跃，反映用户对内容自由度的强烈需求。国产模型三强（Qwen、Kimi、DeepSeek）包揽前三，生态竞争进入白热化。**Ornith-1.5** 以 MoE 架构崭露头角，35B 总量仅激活 3B，代表高效推理的新方向。量化方面，GGUF 仍是本地部署主流，FP8 作为官方轻量化方案增长迅速。多模态赛道中，MiniMax-H3 视频生成与 LTX-2.5 的竞争格局初步形成。

---

## 值得探索

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 月之暗面新款模型，压缩张量技术兼顾性能与效率，是国产多模态大模型的最新竞争者，值得关注。

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成赛道热门模型，450 万+下载验证了社区认可度，适合图像/视频生成应用研究。

3. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 700 万下载量的量化版本，是本地部署 Qwen3.8 的最优选择，推理效率与易用性兼备。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*