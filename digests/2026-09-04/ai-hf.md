# Hugging Face 热门模型日报 2026-09-04

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-04 04:02 UTC

---



# Hugging Face 热门模型日报
> 📅 2026-09-04 · 共 30 个模型 · 按周点赞排序

---

## 今日速览

今日 Hugging Face Hub 的热门模型呈现**多模态模型持续领跑、开源大模型家族快速迭代、社区量化活动高涨**三大趋势。多模态与生成类模型中，MiniMax-H3 以近 510 万次下载成为本周下载量最高的多模态模型，LTX-2.5 视频生成模型也进入热门。Qwen 家族（Qwen3.8）依然是本轮榜单中**社区活跃度最高的模型家族**，不仅基础版下载量破 525 万，社区还涌现大量 GGUF 量化变体与 uncensored 微调。DeepSeek-V4 和 GLM-5.3 也在语言模型赛道持续获得关注。

---

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,843 | 5,254,882 | 通义千问 27B 参数语言模型，本周点赞数最高、下载量超 525 万，显示 Qwen 家族在开源大模型中的强大号召力。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,021 | 517,902 | GLM-5.3 的快速推理变体，支持图文到文对话，适合低延迟多轮交互场景。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,816 | 263,287 | 通义千问下一代 Flash 模型，聚焦图文多模态对话，点赞数接近 5,000。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,618 | 151,021 | 智谱 GLM-5.3 基础语言模型，支持长上下文对话，是本周 GLM 家族的标杆模型。 |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,606 | 14,071,683 | OpenAI GPT-2 基础语言模型，经典开源模型持续活跃，下载量超 1,400 万。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 900 | 1,336,061 | 社区 uncensored 微调版本，基于 Qwen3.8-27B 去除内容限制，下载量超 133 万。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,060 | 848,781 | 社区大幅调整的微调版本，聚焦开放域对话，点赞破千。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 687 | 262,325 | 社区 GGUF 量化版本，保留 Qwen3.8 核心能力的同时去除限制层。 |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 208 | 11,526 | 专为语音通信优化的语言模型，适合实时语音交互场景。 |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 212 | 85,105 | Flash-Next 的社区量化变体，兼顾性能与去除限制。 |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 165 | 4,477 | GLM-5.3-Flash 的 FP8 量化版本，降低显存占用的同时保持推理性能。 |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 168 | 1,514 | 讯飞 Spark 2.5 的 4B 参数版本，轻量高效，适合边缘部署。 |
| [DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 140 | 39,646 | 社区深度微调版本，结合多轮 MTP 优化与 uncensored 调整。 |

---

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,866 | 5,092,067 | 迷你猫 H3 多模态生成模型，本周下载量最高的视频生成模型，支持图生视频。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,702 | 1,293,463 | 快速视频生成模型，支持文生视频和图生视频，下载量超 129 万。 |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 557 | 54,571 | DeepSeek V4 的 Vision 实验版，支持图文理解与多模态生成。 |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 256 | 0 | 针对 MiniMax-H3 加速的 4 步预览版，追求极致生成速度。 |
| [OpenVDN/vdn-minimax-h3](https://huggingface.co/OpenVDN/vdn-minimax-h3) | OpenVDN | 142 | 0 | 社区基于 MiniMax-H3 的微调版本，优化视频生成质量。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 398 | 3,861 | 新一代文本转语音模型，支持自然语音合成。 |

---

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,461 | 246,135,287 | 最流行的句子嵌入模型，下载量超 2.46 亿，广泛用于语义搜索和相似度计算。 |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,910 | 58,556,227 | Google BERT 基础模型，自然语言处理的经典基石，下载量近 5,856 万。 |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,136 | 19,936,700 | OpenAI CLIP 视觉语言模型，多模态检索和零样本分类的核心基础模型。 |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,092 | 6,761,868 | 轻量版 BERT，速度快 60% 且保留 97% 性能，适合部署场景。 |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 370 | 46,862 | Google 时间序列预测模型，专注于时序数据的精准预测任务。 |
| [facebook/mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 181 | 12,386 | Meta 多语言语音模型（MMS），支持 1,000+ 语言的语音识别和文本转语音。 |

---

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,449 | 9,553,042 | Unsloth 社区对 Qwen3.8-27B 的 GGUF 量化版本，下载量近 955 万，显示量化需求巨大。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 764 | 535,984 | Flash-Next 模型的 GGUF 量化版，兼顾推理速度与显存效率。 |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 250 | 100,110 | GSQ（Grouped-Symmetric Quantization）技术实验版，探索新量化路径。 |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 349 | 75,195 | GLM-5.3-Flash 的 Unsloth 量化版，为中文社区提供高效推理选项。 |

---

## 生态信号

**Qwen 家族持续领跑**，Qwen3.8-27B 基础模型下载量破 525 万，社区还衍生出至少 4 个 GGUF 量化变体和多个 uncensored 微调版，显示开源大模型的完整生态链正在成型。**DeepSeek 和 GLM 紧随其后**，分别以 V4-Flash 和 GLM-5.3 系列进入热门。**多模态生成领域 MiniMax-H3 异军突起**，以 510 万下载量成为视频生成赛道的标杆。**量化需求旺盛**，Unsloth 社区的 GGUF 版本下载量普遍在百万级，反映端侧部署和成本优化的强烈诉求。同时，uncensored 微调活动频繁，显示用户对无限制模型的持续兴趣。

---

## 值得探索

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 本周视频生成下载量最高模型，支持图生视频，是探索多模态生成的首选。
2. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 955 万下载的 GGUF 量化版本，提供高效推理方案，适合资源受限场景。
3. **[sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)** — 2.46 亿下载的句子嵌入模型，语义搜索和 RAG 系统的标配。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*