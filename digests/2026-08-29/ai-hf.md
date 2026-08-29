# Hugging Face 热门模型日报 2026-08-29

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-29 06:43 UTC

---



# Hugging Face 热门模型日报
**日期：2026-08-29**

---

## 📋 今日速览

今日 HF 热门榜被 **Qwen 3.8 系列** 深度统治，其 Flash-Next、27B 原版及社区 GGUF 量化版本集体上榜，下载量总计超 **1100 万次**，是开源多模态大模型生态的核心主力。**Moonshot AI 的 Kimi-K3** 以 11,069 点赞位居榜二，展现国产大模型在语义理解与对话领域的强劲势头。**MiniMax-H3 视频生成模型** 下载突破 484 万，配合阿里推出的 Controlnet 与 LoRA 扩展，视频生成赛道竞争日趋白热化。此外，**abliterated（去抑制）** 与 **MLX/GGUF 量化** 社区活动活跃，反映用户对可控性与本地部署的持续追求。

---

## 🔥 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,165 | 3,457,687 | Qwen 3.8 旗舰模型，支持图像-文本到文本的多模态对话。以超过 345 万下载量成为榜单下载冠军，是开源多模态 LLM 的标杆之作。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,069 | 2,675,145 | Moonshot AI 发布的多模态语言模型，支持特征提取与压缩张量推理，下载超 267 万，点赞位列第二。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,181 | 4,810 | Qwen 3.8 Flash 系列的最新迭代，面向高效对话与多模态推理，点赞超 4100，代表 Qwen 在轻量化路线上的持续突破。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,790 | 3,959,575 | DeepSeek V4 Flash 版本，专注高效文本生成与对话，下载近 400 万，延续 DeepSeek 在开源对话模型领域的竞争力。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,530 | 34 | GLM 5.3 Flash 快速版，支持图像-文本到文本与文本生成，代表智谱在下一代 GLM 架构上的探索。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,176 | 0 | GLM 5.3 正式版，采用 MoE DSA 架构，支持多模态对话，是智谱最新基准模型。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 486 | 88,102 | Ornith 1.5 系列 35B 参数模型，采用 MoE 架构与 Qwen3.5 基础，兼具高效推理与多模态理解能力。 |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 146 | 349 | 路透推出的 1.0 小型多模态模型，面向金融与专业领域对话，是垂直行业大模型的早期尝试。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 254 | 0 | 腾讯混元 Hy4 预览版，基于 hunyuan 架构的文本生成模型，尚未开放下载，值得关注后续发布。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,589 | 4,848,404 | MiniMax 最新视频生成模型，支持文生视频、图生视频与视频视频生成，下载近 485 万，领跑开源视频生成赛道。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,033 | 912,729 | LTX 视频生成模型 2.5 版本，支持多模态输入（图/文→视频），下载超 91 万，是图像到视频领域的热门选择。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,290 | 19,726 | MiniMax 第三代音乐生成模型，支持文生音乐，是公司在音频生成方向的最新布局，社区关注度快速上升。 |
| [alibaba-pai/MiniMax-H3-Fun-Controlnet-Union](https://huggingface.co/alibaba-pai/MiniMax-H3-Fun-Controlnet-Union) | alibaba-pai | 159 | 3,344 | 阿里 PAI 为 MiniMax-H3 推出的 Controlnet 联合版，支持精细化的视频生成控制，拓展了 H3 的应用边界。 |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 136 | 609 | 阿里 PAI 提供的 MiniMax-H3 加速 LoRA 插件，基于 arxiv:2607.26004 研究，旨在提升视频生成效率。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 171 | 240 | Breeze 第二代文本转语音模型，支持自然语音合成，是社区 TTS 领域的持续迭代之作。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 124 | 64 | Pipecat AI 推出的语音语言模型 Alpha 版，基于 Nemotron 架构，探索语音原生大模型的新范式。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,512 | 0 | 专为 Qwen 模型修复对话模板的 Jinja 模板工具，解决多模型集成中的格式兼容问题，工具类模型热度高。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,155 | 7,758,790 | Unsloth 对 Qwen3.8-27B 的 GGUF 量化版本，下载近 **776 万**，是本地高效部署的顶级选择，与原版形成互补。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 808 | 1,666,948 | 去抑制版本的 Qwen3.8-27B GGUF 量化，下载超 166 万，满足用户对无约束生成的需求。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 426 | 1,355,482 | Abliterated（去抑制+安全恢复）版本的 Qwen3.8-27B，下载超 135 万，反映社区对"自由且可用"模型的持续追求。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,237 | 273,577 | 去抑制版本的 Qwen3.8-27B FP8 量化，兼顾精度与显存效率，下载超 27 万，适合 GPU 资源有限的用户。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,194 | 83,352 | 去抑制版本的 Qwen3.8-27B MLX 格式，面向 Apple Silicon 本地部署，下载超 8 万。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 533 | 188,460 | 去抑制版本的 Qwen3.8-27B GGUF 量化，是 GGUF 阵营中"自由生成"路线的代表之一。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 884 | 509,270 | Abliterated 版本的 Qwen3.8-27B，支持 MLX 与 GGUF 格式，下载超 50 万，是去抑制技术的重要实践。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 729 | 938,219 | HauhauCS 推出的激进 MTP（多令牌预测）加速版本，下载超 93 万，探索推理速度优化的新路径。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 531 | 4,354 | Unsloth 对 Qwen3.8-Flash-Next 的 GGUF 量化，为 Flash 系列提供本地部署选项。 |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 250 | 0 | Unsloth 对 GLM-5.3-Flash 的 GGUF 量化，目前尚未开放下载，预示后续本地部署需求。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 333 | 1,469,059 | Ornith 1.5 35B 的 GGUF 量化版本，MIT 许可，兼容端点部署，下载超 146 万，是小型 MoE 模型本地化的热门选择。 |
| [Qwen/Qwen3.8-Flash-Next-FP8](https://huggingface.co/Qwen/Qwen3.8-Flash-Next-FP8) | Qwen | 148 | 2,219 | Qwen 官方发布的 Flash-Next FP8 量化版，在精度与显存之间取得平衡，适合 mid-range GPU 部署。 |

---

## 📊 生态信号

**Qwen 3.8 家族** 是今日绝对核心：从原版 27B 到 Flash-Next，再到社区十余个量化与去抑制变体，覆盖全场景部署需求，总下载量超 **1800 万次**，显示开源多模态 LLM 已形成完整的生态矩阵。**GLM-5.3 系列** 作为智谱的下一代架构，虽下载量尚低，但 Flash 与正式版同时亮相，预示其即将进入大规模应用阶段。**MiniMax** 通过 H3 视频模型 + Controlnet/LoRA 插件的组合拳，构建视频生成工具链，竞争策略清晰。**abliterated / uncensored 模型** 占据量化榜近半数席位，且下载量普遍可观，说明"可控自由"仍是社区核心诉求。**GGUF 与 MLX 量化** 并行发展，分别覆盖 NVIDIA/AMD 与 Apple Silicon 生态，本地部署门槛持续降低。

---

## 🌟 值得探索

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 开源视频生成赛道下载量最高模型（近 485 万），配合阿里 Controlnet 与 LoRA 扩展，是研究视频生成工作流与二次开发的理想入口。

2. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 点赞超 1.1 万、下载 267 万，综合热度仅次于 Qwen 旗舰。支持压缩张量推理，适合对多模态对话质量与部署效率有双重要求的场景。

3. **[huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF)** — Abliterated 技术路线的代表作，在下载超 135 万的同时保留了模型的基础能力，是探索"去抑制但不失控"平衡点的优质样本。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*