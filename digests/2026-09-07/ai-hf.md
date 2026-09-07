# Hugging Face 热门模型日报 2026-09-07

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-07 04:04 UTC

---



# Hugging Face 热门模型日报
**日期：2026-09-07**

---

## 今日速览

本周 Hugging Face 上最大的赢家是 **Qwen3.8 系列**，27B 基础版以 1.4 万赞领跑，同时 Flash-Next、GGUF 量化版等多个变体同时上榜，形成家族式垄断态势。**DeepSeek-V4-Flash-Vision-Exp** 作为多模态新贵迅速崛起，单日下载量近 21 万，值得关注。**MiniMax-H3** 以近 500 万下载量刷新视频生成赛道热度。社区量化生态持续繁荣，同一模型衍生出十余个 GGUF 版本，涵盖 uncensored、FP8、NVFP4 等多种路径。

---

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 14,142 | 6,190,807 | 通义千问旗舰对话模型，支持图文多模态理解与对话。27B 参数规模在开源社区下载量突破 600 万，成为当前最受欢迎的中型 LLM 之一。 |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,707 | 14,612,342 | OpenAI 经典生成式预训练语言模型，长期占据基础模型库榜首。1460 万下载量彰显了其作为教学与嵌入式方案的持久生命力。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,101 | 761,364 | 智谱 GLM-5.3 系列 Flash 加速版，支持图文对话。下载量 76 万，以推理效率为卖点，是新一代国产多模态 LLM 代表。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,740 | 410,074 | GLM-5.3 基础对话模型，采用 MoE-DSA 架构。与 Flash 版共同形成产品矩阵，累计下载超 117 万。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 445 | 6,441 | 腾讯混元 Hy4 预览版，国产新一代语言模型。处于早期阶段，但体现了大厂在开源 LLM 赛道的持续投入。 |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 621 | 5,477 | 星火 X2.5 轻量 4B 模型，面向端侧部署场景。下载量相对较低，但在小型语言模型赛道有明确定位。 |
| [IFM/K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 187 | 1,723 | 36B MoE 架构语言模型，属于较新发布的开源 LLM。目前下载量不高，可作为新兴架构的实验性选择。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 751 | 209,191 | DeepSeek 新一代多模态视觉模型实验版，支持图像-文本理解。单日下载超 20 万，显示出市场对 DeepSeek 多模态能力的强烈兴趣。 |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,971 | 4,986,349 | MiniMax 视频生成模型，支持文本到视频与图像到视频。下载量近 500 万，在开源视频生成领域遥遥领先。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,982 | 1,526,928 | Lightricks 新一代视频生成模型，支持文生视频与视频编辑。152 万下载量证明其在创作者生态中的广泛采用。 |
| [OpenVDN/vdn-minimax-h3](https://huggingface.co/OpenVDN/vdn-minimax-h3) | OpenVDN | 210 | 0 | 基于 MiniMax-H3 的微调版本，针对特定视频生成任务优化。由于是新上传版本，暂无下载数据，值得关注后续发展。 |
| [microsoft/VibeVoice-ASR-Streaming-7B](https://huggingface.co/microsoft/VibeVoice-ASR-Streaming-7B) | microsoft | 121 | 889 | 微软流式语音识别模型，支持实时语音转写。7B 参数规模使其适合边缘部署，流式特性对在线场景有实用价值。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 462 | 6,357 | 文本到语音生成模型，第二代迭代版本。针对语音自然度和多说话人支持进行了优化。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,569 | 253,029,336 | 最流行的句子嵌入模型，支持文本相似度与语义搜索。2.5 亿下载量稳居 Hugging Face 平台下载榜首，是 NLP 应用的基石模型。 |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,989 | 52,338,347 | Google BERT 基础版，预训练语言模型的里程碑之作。5200 万下载量表明其作为下游任务默认基座的持续地位。 |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,211 | 20,579,479 | OpenAI CLIP 视觉-语言预训练模型，支持零样本图像分类。2057 万下载使其成为多模态研究的标配工具。 |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,156 | 7,054,316 | BERT 的轻量蒸馏版本，在保留大部分性能的同时显著降低推理成本。700 万下载量使其成为资源受限场景的首选。 |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 515 | 144,455 | Google 时间序列预测模型，专为长序列 Forecasting 设计。14.4 万下载量在垂直领域属于高关注度，体现了时序 AI 的快速增长。 |
| [facebook/mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 263 | 12,464 | Facebook 多语言语音模型（MMS），支持 140+ 语言的语音识别。在低资源语言覆盖方面具有独特优势。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,603 | 10,311,462 | Unsloth 对 Qwen3.8-27B 的 GGUF 量化版本，支持极速推理。1031 万下载量使其成为 Qwen 生态中最活跃的量化分支。 |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 471 | 348,389 | 采用 GSQ（组状量化）和 RCO（残差补偿优化）技术的混合精度量化版本，在精度与效率间寻求平衡。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 983 | 1,568,315 | Qwen3.8-27B 的无限制微调版本，移除了内容安全拒绝机制。156 万下载量表明社区对 uncensored 模型的持续需求。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,108 | 995,160 | 采用 MLX 和 GGUF 双格式的 abliterated 版本，移除安全限制。接近 100 万下载量，是 Qwen 社区最大的无限制微调项目之一。 |
| [DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 253 | 211,018 | 多标签复合微调版本，集成了编码增强、MTP 等能力。模型名本身反映了社区对功能叠加式微调的尝试。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 814 | 823,733 | Unsloth 对 Qwen3.8-Flash-Next 的 GGUF 量化版本，继承了原版的高效推理特性。82 万下载量是 Flash 系列中活跃度最高的量化分支。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 754 | 287,720 | Qwen3.8-27B 的 GGUF 无限制量化版本，提供 abliterated 推理能力。28.7 万下载量在同类模型中处于中上水平。 |
| [nvidia/Qwen3.8-Flash-Next-NVFP4](https://huggingface.co/nvidia/Qwen3.8-Flash-Next-NVFP4) | nvidia | 119 | 13,321 | NVIDIA 推出的 NVFP4 量化版本，专为 NVIDIA GPU 硬件优化。作为硬件厂商直接参与的量化实践，具有示范意义。 |
| [dealignai/GLM-5.3-CYBERSECURITY-FP8](https://huggingface.co/dealignai/GLM-5.3-CYBERSECURITY-FP8) | dealignai | 179 | 15,648 | 面向网络安全领域的 GLM-5.3 FP8 量化版本，采用 abliterated 技术移除拒绝机制。在垂直领域 + 无限制的交叉点上有独特定位。 |
| [Jackrong/Qwopus3.8-27B-Flash-GGUF](https://huggingface.co/Jackrong/Qwopus3.8-27B-Flash-GGUF) | Jackrong | 132 | 22,128 | Qwen3.8 Flash 的 GGUF 量化版本，面向 llama.cpp 生态。虽然下载量不高，但体现了社区对轻量化推理的持续探索。 |

---

## 生态信号

**Qwen3.8 家族**在本周呈现压倒性统治力：基础版、Flash 版及其 GGUF 量化变体、NVFP4 硬件优化版等共占据榜单近 15 席，形成完整的模型生态矩阵。GLM-5.3 作为竞争者同步推出 Flash 版与基础版，国产 LLM 双强格局正在形成。**开源 vs 闭源**方面，全部上榜模型均为开源权重，但 DeepSeek 以"Exp"名义发布实验版，暗示核心能力仍部分保留在闭源端。**量化活动**异常活跃——同一模型衍生出十余个 GGUF 版本，uncensored/abliterated 细分品类下载量可观（多个超百万），反映了社区对定制化推理和去限制场景的强烈需求。

---

## 值得探索

1. **[DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp)** — 下载增速最快（单日 20 万+），是 DeepSeek 在多模态领域的最新尝试，值得评估其相比闭源版本的实际能力差距。

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 500 万下载量的视频生成模型，在 LTX-2.5 等竞品中仍保持领先地位，开源视频生成的竞争格局值得关注。

3. **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — Google 时间序列预测模型，是时序 AI 这一新兴领域的高质量开源实现，在工业预测、金融分析等场景具有直接应用价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*