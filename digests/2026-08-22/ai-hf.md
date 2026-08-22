# Hugging Face 热门模型日报 2026-08-22

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-22 01:36 UTC

---



# 📰 Hugging Face 热门模型日报
**日期：2026-08-22**

---

## 今日速览

今天 HF 热门榜被 **Qwen3.8-27B** 家族全面霸榜，官方与社区共推出超过 15 个变体（FP8、GGUF、MLX、abliterated、NVFP4 等），量化与去约束化仍是社区最热话题。国产模型 **Kimi-K3** 以 10,913 点赞紧随 Qwen 之后，**MiniMax-H3** 视频生成模型下载量突破 360 万，**DeepSeek-V4-Flash** 以 283 万下载量领跑开源文本生成。多模态与生成领域，MiniMax 与 Lightricks 的视觉生成模型持续吸睛，音乐生成赛道也有 MiniMax-Music3 新入局。

---

## 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 11,968 | 1,726,651 | Qwen 官方旗舰稠密模型，支持图文对话，单日下载超 170 万。以 11,968 点赞成为今日最热模型，代表开源 LLM 的标杆级影响力。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,913 | 2,448,810 | 月之暗面发布的 Kimi-K3 系列模型，支持图文理解与压缩张量推理。以近 250 万下载量证明其在中文场景的广泛采用。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,612 | 2,833,064 | DeepSeek V4 快速版，专注于文本生成的轻量化推理版本。超 280 万下载量说明社区对高效推理变体的强劲需求。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 709 | 49,601 | DeepSeek V4 专业版，强调更高精度的文本生成能力。作为旗舰版补充，适合需要极致质量的严肃应用场景。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,738 | 505,113 | Meta-models 推出的 30B 级图文对话模型，以适中体量提供多模态理解能力，在开源生态中占据细分市场。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,139 | 15,702 | Qwen 系列 MoE 专家模型，总计 2.4T 参数但仅激活 95B，兼顾规模效率与性能，代表 MoE 架构的工业实践方向。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 290 | 9,165 | Ornith 系列 35B MoE 模型（仅激活 3B），基于 Qwen3.5 架构，以极低激活参数实现高效推理，适合资源受限场景。 |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 191 | 1,136 | 轻量级语音识别（ASR）模型，基于 Qwen3 架构扩展，面向端侧语音交互场景，体量小巧便于部署。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,295 | 3,614,443 | MiniMax 图文转视频旗舰模型，支持文本/图像/视频三模态输入，超 360 万下载量表明社区对国产视频生成模型的强烈兴趣。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,493 | 654,175 | Lightricks 推出的单文件扩散视频模型，支持图/文/视频多种输入模式，以即开即用的便捷性赢得视频创作社区青睐。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,163 | 15,678 | MiniMax 第三代音乐生成模型，支持文本到音频的高质量音乐创作，填补了国产开源音乐生成赛道的空白。 |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 311 | 0 | 基于 MiniMax-H3 的微调视频生成模型，专为特定风格优化，代表社区在开源视频生成模型之上的创意延伸。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,371 | 0 | 修复 Qwen 系列聊天模板的 MLX/Jinja 工具包，虽无下载量但 1,371 点赞说明社区对规范对话格式的迫切需求。 |

### 🔧 专用模型

> 今日热门榜暂无代码、数学、医疗、嵌入等垂直领域专用模型上榜。

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,510 | 5,804,917 | Unsloth 出品的 Qwen3.8-27B GGUF 量化版本，下载量突破 580 万位居榜首，是本地部署首选的高效推理方案。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 822 | 107,520 | FP8 量化 + 去约束（abliterated）的双重重制版本，兼顾推理效率与自由度，在技术玩家中广受欢迎。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 821 | 18,193 | Apple Silicon 优化的 MLX 格式去约束版本，专为 Mac 用户打造，体现开源社区对端侧高效推理的持续投入。 |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 660 | 1,939,895 | Qwen 官方 FP8 量化版本，在精度与速度之间取得平衡，近 200 万下载量说明官方量化版本同样深受社区信任。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 571 | 1,126,222 | 社区主导的 GGUF 去约束版本，支持 llama.cpp 直接加载，超 110 万下载证明 GGUF 格式在本地 LLM 部署中的统治地位。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 444 | 123,956 | 提供 MLX 与 GGUF 双格式的 abliterated 版本，以"彻底解锁"为卖点，吸引追求无限制输出的进阶用户。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 424 | 357,225 | 激进策略 MTP（Multi-Token Prediction）微调的去约束 GGUF 版本，在保持速度的同时提升输出质量，是技术爱好者的重要参考。 |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 328 | 1,013,917 | Unsloth 探索的 NVFP4 超低精度量化方案，以极限压缩换取推理速度，超 100 万下载表明社区对极致量化的持续关注。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 295 | 68,275 | orcarouter 系列的早期 GGUF 去约束版本，作为其产品线的基础款，为不同偏好的用户提供了多样化选择。 |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 213 | 421,918 | "异端"风格 abliterated GGUF 版本，以激进去约束策略著称，超 42 万下载说明特定圈层用户对无限制模型的稳定需求。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 232 | 338,221 | huihui-ai 出品的 abliterated GGUF 版本，在去约束与可用性之间寻求平衡，累计下载超 33 万。 |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 238 | 74,038 | empero-ai 推出的 Ridge 策略微调 GGUF 版本，在精度保持方面有所优化，适合对输出质量有要求的本地部署用户。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 207 | 123,237 | Ornith MoE 模型的 GGUF 量化版本，使低激活参数优势在本地推理中得以充分发挥，下载量稳定增长。 |
| [Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF](https://huggingface.co/Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF) | Blackfrost-AI | 201 | 197,667 | Blackfrost-AI 的 abliterated GGUF 版本，采用稠密架构进行去约束处理，在特定应用场景中展现出独特价值。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 229 | 17,521 | huihui-ai 的 safetensors 原生 abliterated 版本，为不使用 GGUF 的用户提供替代选择，覆盖更广泛的推理框架。 |
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 176 | 21,092 | 采用 DFlash2 推测解码技术优化的 Qwen3.8 版本，通过 Speculative Decoding 加速推理，代表性能优化的前沿探索方向。 |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 170 | 155,208 | 融合 Cold-Fusion、GAIN 训练与 MTP 的 GGUF 版本，汇集多种前沿训练技巧，为技术极客提供了实验性参考实现。 |

---

## 生态信号

今日榜单清晰呈现三大趋势：一是 **Qwen3.8 家族生态爆发**，官方 27B 稠密模型与 2.4T MoE 双轨并进，社区围绕其衍生出 15+ 个微调/量化变体，覆盖 GGUF、FP8、MLX、NVFP4 等全格式，说明 Qwen 已成为开源生态的事实标准之一。二是 **视频生成模型竞争白热化**，MiniMax-H3 以 360 万下载量领跑，LTX-2.5 与 TenStrip 跟进，国产团队在视频生成赛道展现强劲实力。三是 **去约束（abliterated/uncensored）需求持续旺盛**，虽然不涉及具体模型能力，但大量此类变体上榜反映社区对自由输出的稳定需求，同时也推动量化格式与推理框架的持续优化。

---

## 值得探索

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 国产视频生成模型的扛鼎之作，三模态输入能力 + 超 360 万下载量，代表当前开源视频生成的一线水平，值得研究与实地体验。

2. **[unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4)** — Unsloth 探索的极限量化方案，NVFP4 格式将推理速度推向新高度，100 万+ 下载验证了社区对极致效率的渴求，是本地部署的性能标杆。

3. **[Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5)** — 单文件扩散视频模型，即开即用的设计哲学使其成为视频生成入门的最佳选择，同时 65 万下载量也证明其在创作者群体中的广泛接受度。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*