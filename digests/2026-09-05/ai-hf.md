# Hugging Face 热门模型日报 2026-09-05

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-05 03:58 UTC

---



# Hugging Face 热门模型日报

**日期：2026-09-05** | **分析师：Agnes**

---

## 一、今日速览

DeepSeek 发布 DeepSeek-V4-Flash-Vision-Exp 实验版本，首日斩获 608 赞与 13 万+ 下载，多模态能力持续迭代。Qwen3.8 系列霸榜现象显著，旗舰 27B 模型周下载突破 570 万，Flash-Next 变体亦表现强劲。视频生成赛道竞争激烈，MiniMax-H3 与 LTX-2.5 合计下载超 650 万，社区推理工具 Unsloth 的 GGUF 量化版本下载量接近千万级。整体生态呈现**旗舰模型持续放量 + 视频生成爆发 + 量化微调活跃**三大趋势。

---

## 二、热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,962 | 5,739,341 | Qwen3.8 系列旗舰 27B 模型，支持图像-文本多模态对话，当周热度最高的开源 LLM。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,706 | 303,534 | GLM 新一代文本生成模型，采用 MoE DSA 架构，对话能力显著提升。 |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 481 | 3,524 | 星火 X2.5 轻量 4B 模型，面向端侧部署的指令微调版本。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 437 | 5,684 | 腾讯混元 Hy4 预览版，新一代文本生成模型，预计后续开放完整能力。 |
| [IFM/K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 156 | 433 | K2-Horizon MoVA 架构 36B 大模型，采用 A4B 稀疏激活设计，专注高效推理。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 608 | 133,024 | DeepSeek V4 视觉实验版，支持图像-文本联合生成，Flash 速度优化版本，首日获高度关注。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,880 | 351,374 | Qwen3.8 Flash 下一代模型，多模态对话+推理加速，社区下载量快速攀升。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,053 | 654,957 | GLM-5.3 多模态 Flash 版本，视觉-文本联合理解能力突出，下载量超过基础版。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,795 | 1,399,511 | 高质量图像转视频模型，支持文生视频/图生视频/视频重绘，社区应用广泛。 |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,912 | 5,118,457 | MiniMax 新一代多模态视频生成模型，支持文本到视频和图像到视频，下载量领跑本周。 |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 277 | 0 | MiniMax-H3 的 4 步快速推理预览版，免数据蒸馏加速方案，填补极速视频生成空白。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 432 | 105,304 | Google 时间序列预测模型 v3.0，支持零样本与 few-shot  forecasting，工业场景实用性强。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 434 | 5,388 | Breeze 第二代文本转语音模型，自然度与多语言支持显著提升。 |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,519 | 253,789,790 | 经典句子相似度嵌入模型，下载量超 2.5 亿，长期稳居社区首选。 |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,661 | 14,607,268 | GPT-2 开源原版的持续活跃下载，作为基础模型与教学用途的经典选择。 |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,951 | 58,675,189 | BERT 基准模型，Masked Language Modeling 任务的行业标准参考。 |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,185 | 20,569,141 | CLIP 视觉语言预训练模型的轻量版本，零样本图像分类与跨模态检索的核心基座。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,514 | 9,951,693 | Unsloth 出品的 Qwen3.8-27B GGUF 量化版本，本地推理效率大幅提升，下载量近千万。 |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 315 | 206,575 | 采用 GSQ+RCO 混合精度量化技术的 Qwen3.8-27B GGUF 版本，兼顾质量与推理速度。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 788 | 702,251 | Flash-Next 模型的 GGUF 量化版，本地多模态部署的热门选择。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 949 | 1,463,966 | HauhauCS 激进 MTP 微调的非审查版本，适合无内容限制的研究与创意场景。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,090 | 928,393 | 采用 Abliterated 技术移除对齐约束的 Qwen3.8-27B，支持 MLX 与 GGUF 多格式。 |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 183 | 7,782 | GLM-5.3-Flash 的 FP8 非审查量化版，探索无对齐约束下的多模态生成能力。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 717 | 276,706 | Qwen3.8-27B 的非审查 GGUF 版本，社区探索开源模型边界的重要实践。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 971 | 2,395,758 | Qwen3.8-27B 非审查 GGUF 版本，使用 llama.cpp 推理，支持 MTP 加速，下载量超 239 万。 |

---

## 三、生态信号

本周期开源模型生态呈现三大特征：**Qwen 家族持续主导流量**，Qwen3.8 系列及其衍生量化版本贡献了榜单近半的热度；**视频生成模型进入白热化竞争**，MiniMax-H3 与 LTX-2.5 在下载量上已形成千万级壁垒，FastVideo 的 4 步蒸馏方案预示推理加速将成为下一阶段关键战场；**量化与微调社区极度活跃**，Unsloth GGUF 版本下载量接近千万，同时 Abliterated/Uncensored 类非审查微调模型大量涌现，反映社区对开源模型可控性与伦理边界的深度探索。同时，Google 时间序列模型 timesfm-3.0 的出现表明垂类专用模型在实用化道路上持续突破。

---

## 四、值得探索

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 当周下载量最高的视频生成模型（超 510 万），代表开源视频生成能力的最新水平，适合评估当前文生视频的质量与可控性边界。

2. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 本地部署首选，下载量近千万验证了其生态地位，适合希望在不依赖云端 API 的情况下运行高性能多模态模型的研究者与开发者。

3. **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — Google 官方时间序列预测模型 v3.0，零样本能力出色，对金融、能源、供应链等时序敏感行业具有直接应用价值，值得专业领域从业者关注。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*