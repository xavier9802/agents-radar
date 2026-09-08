# Hugging Face 热门模型日报 2026-09-08

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-08 04:06 UTC

---



# Hugging Face 热门模型日报 — 2026-09-08

## 今日速览

2026 年 9 月初，Qwen3.8 模型家族全面霸榜，其 27B 基础版以 14,286 周赞和超 641 万下载位居榜首，Flash-Next 与社区 GGUF 量化版紧随其后，展现了极强的生态影响力。同时，MiniMax-H3 视频生成模型以近 500 万次下载领跑多模态生成赛道，GLM-5.3 与 DeepSeek-V4 Flash-Vision 等新家族快速崛起。量化与社区微调活动异常活跃，尤其是 GGUF 格式在 27B 级别模型上的广泛适配，以及大量"uncensored"变体的涌现，反映出端侧部署与内容自由度是当前社区两大核心诉求。

---

## 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 14,286 | 6,416,358 | 阿里通义系列最新旗舰，支持图像-文本-文本多模态对话，性能对标顶尖闭源模型。以超高点赞和下载量成为本期绝对核心。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,983 | 474,693 | Qwen3.8 系列的加速推理版本，在保持多模态对话能力的同时显著提升吞吐速度，适合生产部署。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,137 | 784,005 | 智谱 GLM-5.3 系列的 Flash 版本，支持图像-文本多模态对话，推理效率优化明显。GLM 新家族在多模态赛道强势崛起。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,753 | 442,064 | GLM-5.3 基准版，采用混合专家架构（MoE DSA），兼顾性能与资源效率，适合文本生成任务。 |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 802 | 251,611 | DeepSeek-V4 系列新发布的视觉实验版本，融合 Flash 加速技术，支持图像理解与文本生成。 |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 749 | 7,216 | 星火 X2.5 的 4B 轻量版本，面向端侧和低成本部署场景，在文本生成任务上表现稳健。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 794 | 292,633 | 社区对 Qwen3.8-27B 的 GGUF 量化版本，移除了内容审查限制，满足特定自由输出需求。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 998 | 1,629,754 | 激进的社区微调版本，基于 MTP（Multi-Token Prediction）技术，以 162 万下载量成为热度最高的去审查模型之一。 |
| [DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 305 | 258,896 | 综合多项社区技术的深度微调 GGUF 模型，融合 Heretic 框架与 MTP 加速，面向高级自定义场景。 |
| [openbmb/MiniCPM5-2B](https://huggingface.co/openbmb/MiniCPM5-2B) | openbmb | 333 | 13 | 面壁智能 MiniCPM 系列最新 2B 轻量模型，延续高效小模型路线，适合资源受限的端侧部署。 |
| [dealignai/GLM-5.3-CYBERSECURITY-FP8](https://huggingface.co/dealignai/dealignai/GLM-5.3-CYBERSECURITY-FP8) | dealignai | 277 | 18,602 | 针对网络安全领域微调的 GLM-5.3 版本，采用 FP8 量化并移除拒绝机制，服务于专业场景。 |
| [IFM/K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 212 | 2,226 | K2 Horizon 系列 MoVA 架构模型，36B 参数规模，在纯文本生成任务上探索新架构路线。 |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,716 | 14,629,637 | OpenAI 开源的经典 GPT-2 模型，虽已发布多年仍保持 1462 万下载量，证明基础模型具有长期生命力。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 5,013 | 4,990,034 | MiniMax 最新视频生成模型，支持图像到视频与文本到视频，近 500 万下载量彰显强大社区号召力。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 3,090 | 1,584,382 | Lightricks 迭代推出的视频生成模型，支持图像、文本、视频多输入模式，单文件 Diffusion 架构便于部署。 |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 583 | 271,713 | Google 时间序列预测模型 3.0 版本，专注时序数据预报任务，在企业预测场景中应用广泛。 |
| [WarmBloodAban/Minimax-h3_Singularity](https://huggingface.co/WarmBloodAban/Minimax-h3_Singularity) | WarmBloodAban | 145 | 26,731 | 基于 MiniMax-H3 社区的图像到视频微调版本，探索更精细的视频生成控制能力。 |
| [OpenVDN/vdn-minimax-h3](https://huggingface.co/OpenVDN/vdn-minimax-h3) | OpenVDN | 228 | 0 | 对 MiniMax-H3 的文本到视频微调实验版本，当前下载量为零，仍处于早期探索阶段。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 478 | 6,754 | Breeze 系列第二代文本转语音模型，在语音自然度和多语言支持上持续迭代优化。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,577 | 251,367,312 | 最流行的句子嵌入模型之一，轻量高效，支持 PyTorch/TF/Rust/ONNX 多后端，累计下载超 2.5 亿次。 |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,992 | 50,747,373 | BERT 基础版，NLP 领域的经典基石模型，5000 万下载量印证其不可动摇的基础地位。 |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,156 | 7,041,011 | DistilBERT 是对 BERT 的轻量蒸馏版本，在保持 97% 性能的同时模型规模缩小 40%，广泛用于生产环境。 |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,212 | 20,496,047 | OpenAI CLIP 视觉语言基础模型，零样本图像分类的标杆工具，支撑了大量多模态下游应用。 |
| [facebook/mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 267 | 12,213 | Meta 多语言语音模型（MMS）300M 版本，支持大规模多语言语音表示学习，覆盖数百种语言。 |
| [microsoft/VibeVoice-ASR-Streaming-7B](https://huggingface.co/microsoft/VibeVoice-ASR-Streaming-7B) | microsoft | 140 | 1,144 | 微软最新流式语音识别模型，7B 参数量支持实时转录，是 VibeVoice 系列在 ASR 领域的重要扩展。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,648 | 10,479,045 | Unsloth 出品的 Qwen3.8-27B GGUF 量化版本，下载量突破 1047 万，是社区端侧部署的首选方案之一。 |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 571 | 403,292 | ISTA-DASLab 实验室推出的 GSQ（Group-Scale Quantization）混合精度 GGUF 版本，在精度与效率间寻求平衡。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 829 | 868,243 | Unsloth 针对 Flash-Next 的 GGUF 量化适配，助力 Flash 系列模型在消费级硬件上高效运行。 |
| [Jackrong/Qwopus3.8-27B-Flash-GGUF](https://huggingface.co/Jackrong/Qwopus3.8-27B-Flash-GGUF) | Jackrong | 142 | 60,343 | 基于 llama.cpp 的 Qwen3.8 Flash 系列 GGUF 变体，面向本地推理场景提供进一步优化。 |
| [nvidia/Qwen3.8-Flash-Next-NVFP4](https://huggingface.co/nvidia/Qwen3.8-Flash-Next-NVFP4) | nvidia | 142 | 18,068 | NVIDIA 官方推出的 NVFP4 量化版本，利用 Model Optimizer 实现英伟达 GPU 上的极致推理性能。 |

---

## 生态信号

Qwen3.8 家族在本期呈现压倒性热度，其 27B 基础版、Flash-Next、以及十余个社区量化/微调变体占据榜单近半席次，显示出开源旗舰模型在开发者中的核心地位。GLM-5.3 与 DeepSeek-V4 Flash-Vision 作为新晋力量快速 gaining traction。量化方面，GGUF 格式在 27B 级别模型上已形成完整生态，Unsloth、ISTA-DASLab、NVIDIA 等机构均在布局；同时"uncensored"类微调模型下载量可观，反映端侧自由部署需求旺盛。视频生成赛道由 MiniMax-H3 和 LTX-2.5 双雄领跑，开源视频模型的竞争日趋激烈。

---

## 值得探索

1. **[Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B)** — 本期无可争议的现象级模型，多模态对话能力领先，生态丰富，是测试和部署的首选基准。
2. [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) — 视频生成领域下载量最高的开源模型，近 500 万次下载验证了其质量与实用性，值得关注其最新能力边界。
3. [nvidia/Qwen3.8-Flash-Next-NVFP4](https://huggingface.co/nvidia/Qwen3.8-Flash-Next-NVFP4) — NVIDIA 官方 FP4 量化方案代表了厂商级优化的新高度，对追求极致推理效率的生产场景极具参考价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*