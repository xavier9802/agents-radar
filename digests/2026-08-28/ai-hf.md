# Hugging Face 热门模型日报 2026-08-28

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-28 10:57 UTC

---



# 🤗 Hugging Face 热门模型日报
**日期：2026-08-28**

---

## 今日速览

今日 HF 热门榜被 **Qwen3.8 家族**强势占据，Flash-Next 与 27B 双版本齐发，社区 GGUF 量化与 uncensored/abliterated 微调作品涌现。DeepSeek-V4-Flash 与 Kimi-K3 紧随其后，国产开源模型全面领跑。**MiniMax-H3** 视频生成模型下载量突破 480 万，成为多模态方向的明星项目。整体生态呈现「大模型开源化 + 社区二次改造活跃 + 视频生成爆发」三大趋势。

---

## 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,078 | 3,457,687 | Qwen3.8 旗舰稠密模型，支持图像-文本对话，点赞数全榜第一，官方正式版下载量超 340 万。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,047 | 2,675,145 | Kimi K3 系列开源模型，支持图像-文本输入，采用压缩张量技术，点赞数仅次于 Qwen3.8-27B，下载量超 260 万。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,778 | 3,959,575 | DeepSeek V4 _flash 版本，专注文本生成与对话，下载量近 400 万，性价比与速度受到社区青睐。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,044 | 4,810 | Qwen3.8 Flash 系列下一代模型，支持图像-文本对话，周榜点赞第三，代表 Qwen 在多模态对话方向的快速迭代。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,408 | 34 | GLM 5.3 Flash 版本，主打文本生成，点赞数高但下载量尚在积累期，值得关注后续表现。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 470 | 88,102 | 35B 参数 MoE 架构语言模型，支持图像-文本对话，采用 Qwen3.5 MoE 技术路线。 |
| [sensenova/SenseNova-U1.5-8B-MoT](https://huggingface.co/sensenova/SenseNova-U1.5-8B-MoT) | sensenova | 185 | 4,232 | 8B MoT 架构多模态模型，支持任意-to-任意任务，具备原生多模态能力。 |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 136 | 349 | 路透推出的 Qwen3.5 MoE 小型模型，专注图像-文本对话场景，面向专业信息场景优化。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,550 | 4,848,404 | MiniMax 视频生成旗舰模型，支持文生视频与图生视频，下载量近 500 万，成为本周视频生成赛道绝对主角。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,953 | 912,729 | LTX 视频生成模型 2.5 版，支持文生视频、图生视频及视频重绘，下载量超 90 万，视频质量受社区认可。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,278 | 19,726 | MiniMax 音乐生成模型，支持文本到音乐生成，同公司 MiniMax-H3 生态延伸。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 138 | 240 | 新一代文本转语音模型，支持高质量语音合成，属于音频生成方向的新秀。 |
| [alibaba-pai/MiniMax-H3-Fun-Controlnet-Union](https://huggingface.co/alibaba-pai/MiniMax-H3-Fun-Controlnet-Union) | alibaba-pai | 149 | 3,344 | 基于 MiniMax-H3 的 ControlNet 联合模型，支持精细视频生成控制，为创作者提供更强可控性。 |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 124 | 609 | MiniMax-H3 加速 LoRA 适配器集合，通过低秩微调提升生成效率，延续 H3 视频生成能力。 |

### 🔧 专用模型

本周榜单未出现以代码、数学、医疗或嵌入为核心标签的专用模型，开源社区精力主要集中在通用语言模型与多模态生成方向。

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,097 | 7,758,790 | 基于 Qwen3.8-27B 的 GGUF 量化版本，由 unsloth 优化，下载量全榜最高超 770 万，本地部署首选。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 789 | 1,666,948 | Qwen3.8-27B 去审查 GGUF 版本，下载量超 160 万，社区对无限制对话模型需求旺盛。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 409 | 1,355,482 | 使用 abliterate 技术移除 Qwen3.8-27B 安全对齐的 GGUF 版本，下载量超 130 万。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 701 | 938,219 | 激进去审查版本，叠加 MTP（多令牌预测）加速，GGUF 格式，下载量超 90 万。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,216 | 273,577 | Qwen3.8-27B FP8 量化去审查版本，由高频微调作者 orcarouter 出品。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,175 | 83,352 | 同系列 MLX 格式版本，面向 Apple Silicon 本地推理优化。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 867 | 509,270 | 使用 OBLITERATED 技术的去对齐版本，同时提供 MLX 与 GGUF 格式。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 328 | 1,469,059 | Ornith 35B MoE 的 GGUF 量化版本，下载量超 140 万，适合本地运行大参数 MoE 模型。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 479 | 4,354 | Qwen3.8-Flash-Next 的 GGUF 量化版本，便于本地部署下一代 Flash 模型。 |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 265 | 238,691 | 融合 COLD-FUSION 与 GAIN 训练的 GGUF 版本，采用多令牌预测加速推理。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,506 | 0 | 修复 Qwen 系列对话模板的配置文件，点赞高但无下载，属于工具型项目。 |

---

## 生态信号

本周生态呈现三大信号：**其一，Qwen3.8 家族绝对主导**，从官方基础模型到社区 GGUF 量化、uncensored/abliterated 微调、MTP 加速变体，已形成完整生态矩阵，unsloth 量化版本下载量超 770 万为全榜之最。**其二，视频生成进入白热化**，MiniMax-H3 系列（含 ControlNet、LoRA 适配）与 LTX-2.5 共同推动 image-to-video 成为最热赛道。**其三，国产开源 LLM 全面崛起**，DeepSeek-V4-Flash、Kimi-K3、SenseNova-U1.5 与 Qwen3.8 形成四强格局，GLM-5.3 Flash 与 Ornith MoE 紧随其后，闭源模型压力持续加大。

---

## 值得探索

1. **[Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next)** — Qwen 最新一代 Flash 系列，多模态对话能力领先，配合 unsloth GGUF 量化后可在消费级硬件运行，兼顾性能与效率。

2. [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) — 视频生成领域下载量最高的模型，结合 ControlNet 与 LoRA 生态可灵活控制生成过程，是探索 AIGC 视频工作流的理想起点。

3. [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) — Kimi 系列开源力作，压缩张量技术降低部署门槛，在多轮对话与长上下文场景表现突出，值得与 Qwen3.8 系列横向对比评测。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*