# Hugging Face 热门模型日报 2026-08-19

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-19 01:40 UTC

---



# 📊 Hugging Face 热门模型日报
**2026-08-19**

---

## 一、今日速览

今日 HF 榜单被 **Qwen3.8 系列** 和 **Kimi-K3** 强势霸榜，前者以 11,148 点赞位居第一，后者紧随其后获得 10,826 点赞，两大模型家族均呈现多版本矩阵式发布策略。**DeepSeek-V4** 系列继续发力，Pro 版与 Flash 版并列榜单中段。**MiniMax** 在视频与音频两个生成赛道同步布局，MiniMax-H3 视频模型下载量突破 280 万，ComfyUI 集成包下载量超过 1400 万。社区微调与量化（FP8、GGUF、NVFP4）活跃度极高，反映出端侧部署需求的持续升温。

---

## 二、热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
|:---|:---|---:|---:|:---|
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 11,148 | 665,513 | 多模态对话模型，图像-文本联合理解能力突出，本周点赞量榜首。官方原生支持 transformers/safetensors 格式，生态兼容性最佳。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,826 | 2,226,898 | 月之暗面发布的新一代多模态语言模型，支持图像-文本-文本任务，采用 compressed-tensors 压缩格式，下载量已超 220 万。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,527 | 2,123,462 | DeepSeek V4 快速版本，专注文本生成与对话，下载量超 210 万，是追求推理速度与成本平衡用户的热门选择。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,682 | 384,097 | 30B 参数多模态对话模型，支持图像-文本到文本任务，标签中暗示 Meta 系架构，社区关注度较高。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,426 | 14,641,908 | ComfyUI 官方封装的 MiniMax-H3 集成包，下载量突破 1464 万，是 workflows 中视频生成管线的重要依赖。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 323 | 269,372 | NVIDIA 发布的 MoE 架构语言模型，30B 总参激活仅 3B，NVFP4 量化显著降低显存占用，适合高效推理部署。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 602 | 30,985 | DeepSeek V4 专业版本，8 月 13 日发布，面向高准确率场景，支持完整对话流程，官方 transformers 原生格式。 |
| [LiquidAI/LFM2.5-VL-3B](https://huggingface.co/LiquidAI/LFM2.5-VL-3B) | LiquidAI | 174 | 9,101 | LiquidAI 发布的 3B 轻量视觉语言模型，适合边缘设备与移动端部署，体积小但保持较好多模态理解能力。 |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 320 | 9,990 | inclusionAI 的超轻量对话模型，采用 bailing_hybrid 架构，适合资源受限场景下的文本生成任务。 |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 221 | 1,120 | dots3 系列的笔记/辅助生成版本，社区下载量尚低但标签独特，值得持续关注其后续迭代。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
|:---|:---|---:|---:|:---|
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,146 | 2,855,539 | 视频生成模型，支持文生视频、图生视频等多种模式，下载量近 286 万，是当前视频生成赛道的热门选择。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,224 | 503,632 | 单文件扩散模型，支持图像到视频、文本到视频、视频到视频，技术路线轻量，下载量超 50 万。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 963 | 11,745 | 文本到音乐生成模型，支持歌词/描述驱动的音乐创作，下载量稳步增长，是音频生成赛道的最新力作。 |
| [Comfy-Org/MiniMax-Music-3](https://huggingface.co/Comfy-Org/MiniMax-Music-3) | Comfy-Org | 178 | 285,444 | ComfyUI 封装的 MiniMax-Music3 集成包，下载量超 28 万，方便用户在节点工作流中直接使用音乐生成能力。 |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 249 | 24,893 | 轻量 2.9B 文生图模型，单文件 diffusion 格式，ComfyUI 友好，适合个人创作者快速部署图像生成。 |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 266 | 0 | 基于 MiniMax-H3 的微调版本，专注图像-文本到视频生成，目前下载量为零（可能刚发布），值得观望。 |

### 🔧 专用模型

> 本周榜单中无纯代码、数学、医疗或嵌入类专用模型上榜，相关模型未进入 TOP 30。

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
|:---|:---|---:|---:|:---|
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 1,824 | 3,561,466 | Qwen3.8-27B 的 GGUF 量化版本，下载量超 356 万，是本地部署（llama.cpp）用户的首选格式之一。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,142 | 3,020,528 | 社区精心微调的无限制 GGUF 版本，融合多种训练策略，下载量超 302 万，是本地自由对话场景的高人气选择。 |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 564 | 741,011 | 官方 FP8 量化版本，在保留较高精度的同时显著降低显存占用，适合 A100/H100 等支持 FP8 的 GPU。 |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 262 | 523,919 | Unsloth 推出的 NVFP4 格式，专为 NVIDIA 新型量化硬件优化，是极致省显存推理的新方向。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 414 | 558,767 | 社区 GGUF 无限制版本，下载量超 55 万，满足用户对自由对话场景的本地化需求。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 534 | 45,465 | FP8 量化且去除对齐限制的版本，abliterated 技术处理，适合追求更高自由度且需低显存部署的用户。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 281 | 0 | Apple Silicon 专属 MLX 格式的无限制版本，目前下载为零（新发布），是 Mac 用户的重要选择。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 204 | 27,745 | 激进 MTP 训练策略的微调版本，GGUF 格式，多模态支持，适合探索极限性能的本地部署用户。 |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 173 | 12,854 | Ridge 策略微调的 GGUF 版本，社区量化探索的一部分，注重推理效率与质量平衡。 |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 227 | 13,344 | 2.4T 参数 MoE 模型的 FP8 量化版，适合大规模 MoE 推理的显存优化场景。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,258 | 0 | MLX/Jinja 格式的修复版聊天模板，解决 Qwen 模型在部分框架中的对话格式问题，技术实用型工具。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,066 | 11,212 | 2.4 万亿参数 MoE 架构（激活 95B）的官方原生版本，代表当前开源 MoE 模型的技术上限。 |

---

## 三、生态信号

**Qwen 家族**呈现压倒性存在感：截至 2026 年 8 月，Qwen3.8 系列已衍生出原生版、FP8、NVFP4、GGUF、MLX、Uncensored 等多种格式与变体，覆盖从数据中心到消费级硬件的全场景部署需求，体现开源厂商"以量化换渗透"的战略思路。**DeepSeek-V4** 以 Pro 与 Flash 双版本并行策略维持竞争力，Kimi-K3 则凭借月之暗面的产品势能持续吸粉。**MiniMax** 在视频（H3）与音频（Music3）双赛道同时布局，ComfyUI 封装包下载量极高，显示其在创作工具链中的渗透率。**社区量化生态**尤为活跃：Unsloth、orcarouter、DavidAU 等贡献者持续产出多格式变体，GGUF 与新兴 NVFP4 并行发展，abliterated/uncensored 需求旺盛，反映出用户对本地自由推理的强烈诉求。

---

## 四、值得探索

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 综合点赞量与下载量均表现强劲，压缩张量格式降低部署门槛，是了解中文多模态 LLM 前沿进展的必试模型。

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成赛道竞争白热化，该模型以近 286 万下载量验证了市场认可度，支持 T2V/I2V/R2V 多模态输入，值得评测其生成质量与速度。

3. **[unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4)** — NVFP4 是 NVIDIA 新兴的量化格式，代表端侧推理的最新优化方向，下载量超 52 万且持续快速增长，对关注硬件效率的用户极具参考价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*