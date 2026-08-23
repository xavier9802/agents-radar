# Hugging Face 热门模型日报 2026-08-23

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-23 01:46 UTC

---



# 📊 Hugging Face 热门模型日报
**2026-08-23 | 数据周期：本周**

---

## 1. 今日速览

今日 HF 榜单被 Qwen3.8 系列全面刷屏，官方 27B 基础模型及 FP8 量化版稳居前列，社区同步推出数十个 abliterated/uncensored 微调变体，显示社区对开源模型深度定制的热情高涨。多模态领域 MiniMax-H3 视频生成模型以 4,300+ 赞强势上榜，LTX-2.5 和 MiniMax-Music3 分别领跑图生视频和文生音乐赛道。DeepSeek-V4 系列和 Kimi-K3 两款新旗舰同样进入视野，开源 LLM 竞争进入白热化阶段。

---

## 2. 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 12,143 | 2,090,699 | Qwen 官方 27B 多模态语言模型，图像-文本对话能力，本周点赞数最高的模型。提供标准 transformers 与 safetensors 格式，适合直接部署对话系统。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,929 | 2,612,739 | 月之暗面发布的 Kimi-K3 模型，支持图像-文本交互，采用 compressed-tensors 技术优化推理效率，下载量突破 260 万，表现强劲。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,632 | 2,976,281 | DeepSeek V4 系列的 Flash 版本，专注快速推理的对话模型，下载量近 300 万，是本周下载量最高的模型之一。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 719 | 54,566 | DeepSeek V4 Pro 版本，面向更高性能场景的对话模型，8 月 13 日更新，为专业用户提供更强的推理能力。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,757 | 517,564 | 30B 参数的图像-文本对话模型，支持 conversational 任务，近期热度快速攀升，成为多模态对话领域的新兴选择。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,146 | 17,386 | Qwen 官方 MoE 架构大模型，2.4T 总参数 / 95B 激活参数，适合对推理质量和长上下文有严苛要求的场景。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 323 | 12,611 | Ornith 1.5 系列的 35B MoE 模型（3B 激活），基于 qwen3_5_moe 架构，兼顾多模态输入与文本生成效率。 |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 202 | 1,913 | 轻量级 s1-mini 模型，标签同时包含 text-generation 与 asr，适合语音识别和文本生成的轻量级应用。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,338 | 3,899,160 | MiniMax 最新图像-文本到视频生成模型，支持 text-to-video / image-to-video / video-to-video 多种模式，本周多模态生成领域下载量冠军。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,568 | 694,670 | LTX-2.5 视频生成模型，支持图像/文本到视频及视频到视频编辑，扩散单文件架构便于快速部署，创作工具生态活跃。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,183 | 16,644 | MiniMax 第三代文生音乐模型，基于 diffusers 生态，为用户提供高质量的 AI 音乐生成能力，填补榜单音频生成空白。 |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 317 | 0 | 基于 MiniMax-H3 的微调版本，专注图像-文本到视频生成，为特定视觉风格提供定制化视频生成能力。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,628 | 6,320,542 | 基于 unsloth 优化的 Qwen3.8-27B GGUF 量化版本，下载量超过 630 万，是社区量化模型中热度最高的一款，适合本地高效推理。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 624 | 1,223,422 | 解除内容限制的 Qwen3.8-27B GGUF 版本，支持 MTP 多 token 预测，在本地推理社区广受欢迎。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 991 | 142,846 | abliterated 版本的 FP8 量化模型，在降低显存占用的同时去除原始安全限制，适合高级用户自定义部署。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 887 | 34,909 | 面向 Apple Silicon 的 MLX 格式 abliterated 版本，无需额外量化即可在 Mac 设备上高效运行。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 535 | 164,950 | 同时提供 MLX 和 GGUF 两种格式的 abliterated 模型，覆盖苹果设备和 CPU/GPU 推理场景。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 489 | 486,221 | 激进 MTP 微调的 uncensored GGUF 版本，多模态输入支持，在保持推理速度的同时强化输出自由度。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 256 | 635,416 | huihui-ai 社区的 abliterated GGUF 量化版，兼顾低显存占用与去除安全对齐的灵活使用需求。 |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 227 | 505,813 | Heretic 路线的 abliterated GGUF 模型，适合追求最大输出自由度的本地部署用户。 |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 245 | 97,247 | Ridge 量化策略的 GGUF 版本，在保留更多原始能力的同时进行高效压缩，适合边缘部署。 |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 193 | 176,969 | 融合 COLD-FUSION 与 GAIN 训练技术的 GGUF 模型，加入 MTP 加速推理，社区实验性微调的代表作品。 |
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 194 | 29,705 | 基于 DFlash2 投机解码优化的文本生成模型，在不显著损失质量的前提下提升推理速度。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 233 | 173,935 | Ornith 1.5 35B MoE 的 GGUF 量化版本，MIT 授权且兼容推理端点，为社区提供低成本部署路径。 |
| [ornith-ai/Ornith-1.5-9B](https://huggingface.co/ornith-ai/Ornith-1.5-9B) | ornith-ai | 163 | 15,301 | Ornith 1.5 轻量版 9B 模型，支持图像-文本输入和文本生成，适合资源受限环境的快速部署。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,398 | 0 | 修复 Qwen 系列 chat template 的 Jinja 模板资源，虽然不是权重模型，但对正确使用 Qwen3.5/3.8 对话格式至关重要。 |

---

## 3. 生态信号

本周 Qwen3.8 模型家族呈现爆发式生态扩散：官方发布 27B 与 2.4T-A95B MoE 两档模型后，社区在 48 小时内涌现十余个 abliterated/uncensored/GGUF/FP8/MLX 变体，下载量合计超千万次，显示开源模型本地化与自由定制的旺盛需求。MiniMax-H3 和 LTX-2.5 共同推动文本/图像到视频生成赛道竞争，而 MiniMax-Music3 的入榜则标志着音频生成开始进入主流视野。DeepSeek-V4 系列以 Flash 和 Pro 双版本并行策略覆盖不同性能需求。量化（GGUF）仍是社区最活跃的优化方向，unsloth 和 abliterated 路线各占一极，反映性能与自由度两条技术路线的分野。

---

## 4. 值得探索

**[Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B)** — 本周绝对热度第一，官方维护、多模态能力完整、社区生态丰富，是评估当前开源多模态 LLM 的首选基线。

**[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成领域本周最强开源模型，支持文本/图像/视频三种输入模式，下载量接近 400 万，适合研究或应用图像到视频的生成管线。

**[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 630 万下载量验证了其在本地部署中的受欢迎程度，unsloth 优化 + GGUF 格式的组合是当前性价比最高的 Qwen3.8 本地推理方案之一。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*