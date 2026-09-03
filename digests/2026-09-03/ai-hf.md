# Hugging Face 热门模型日报 2026-09-03

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-03 04:00 UTC

---



# 📰 Hugging Face 热门模型日报
**日期：2026-09-03**

---

## 一、今日速览

本周期 Qwen 家族霸榜，Qwen3.8-27B 以 **496 万下载** 成为绝对热门，其 Flash-Next 变体与社区 GGUF/量化衍生版本集体上榜。MiniMax-H3 视频生成模型下载量突破 **553 万**，GLM-5.3 系列亦表现强劲。与此同时，社区对"去限"（abliterated/uncensored）微调的活跃度显著上升，多个 Qwen3.8 衍生模型进入榜单，反映用户对定制化权重的持续需求。

---

## 二、热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,704 | 4,960,483 | 阿里通义千问旗舰多模态语言模型，支持图文理解与对话，周下载近 500 万，生态影响力突出。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,743 | 207,941 | Qwen3.8 的 Flash 推理加速版本，适配低延迟场景，标签含 qwen4_exp，预示新一代架构探索。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,526 | 94,403 | Zhipu AI GLM 系列新一代 MoE 架构语言模型，标签 glm_moe_dsa 体现稀疏高效设计，下载增长迅速。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,975 | 441,348 | GLM-5.3 的多模态 Flash 版本，支持图文输入，下载量高居榜单前列，社区关注度极高。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 401 | 3,516 | 腾讯混元 Hy4 预览版语言模型，标签 hy_v4 表明架构迭代，目前处于早期曝光阶段。 |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,548 | 14,290,101 | OpenAI 经典开源语言模型，累计下载超 1400 万，仍是教程、基准测试和嵌入任务的事实标准。 |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 200 | 6,813 | 面向语音对话的实时 LLM 后端模型，标签 nemotron 表明基于 NVIDIA 底座微调，适配低延迟语音链路。 |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 127 | 429 | 讯飞 Spark-X2.5 的 4B 小型部署版本，标签 spark2_5 指向轻量化指令模型，处于早期阶段。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,817 | 5,532,597 | MiniMax 新一代图像/视频生成模型，支持文本到视频与图像到视频，下载突破 550 万，为视频生成赛道头部。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,586 | 1,232,274 | Lightricks 开源视频生成扩散模型，支持多图/文到视频，标签 diffusion-single-file 便于一键部署，下载超 120 万。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 363 | 3,086 | Breeze 第二代文本转语音模型，融合自然语言理解与声学生成，适合对话系统端到端落地。 |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 306 | 0 | 谷歌 TimesFM 时间序列预测模型 3.0 版，专注工业级时序推理，目前尚未开放下载，处于预告阶段。 |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 250 | 0 | 基于 MiniMax-H3 的 4 步快速推理加速版，采用 VSA DataFree 蒸馏技术，旨在大幅缩短视频生成耗时。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,402 | 250,280,836 | 最常用的句子嵌入模型，轻量高效，累计下载超 2.5 亿，是语义相似度、RAG 检索的事实标准。 |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,865 | 63,694,017 | Google 经典 BERT 底座模型，累计下载超 6300 万，仍是词向量、预训练微调的基石模型。 |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 195 | 130,086 | 基于 Qwen3.5 MoE 架构的代码专用模型，激活参数 3B 而总参数 35B，兼顾性能与效率，适合编程助手场景。 |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,050 | 6,870,903 | BERT 的轻量蒸馏版本，保留 97% 性能的同时参数减半，下载近 690 万，适合边缘部署与快速推理。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,397 | 9,354,057 | Unsloth 官方 Qwen3.8-27B 的 GGUF 量化版本，优化推理速度，下载超 935 万，社区部署首选。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 731 | 431,339 | Qwen3.8-Flash-Next 的 GGUF 量化版，适配 llama.cpp 生态，便于本地高效运行。 |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 338 | 63,718 | GLM-5.3-Flash 的 GGUF 量化版本，支持本地化部署，降低多模态对话模型的使用门槛。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 873 | 1,276,092 | 激进的"去限"微调版本，保留 MTP 多步预测能力，下载超 127 万，满足用户对无限制输出的需求。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,029 | 805,791 | 基于 mlx 与 GGUF 的 abliterated 版本，移除安全对齐约束，在苹果 MLX 生态中广受欢迎。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 924 | 2,143,289 | 社区主导的 Qwen3.8-27B 去限 GGUF 版本，下载超 214 万，反映用户对可控输出的强烈需求。 |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 179 | 56,208 | ISTA-DASLab 实验性量化版本，采用 GSQ+RCO 混合精度方案，探索更高效的压缩路径。 |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 195 | 64,325 | Flash-Next 的去限 GGUF 版本，面向需要完整输出能力的研究者与爱好者。 |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 153 | 2,576 | GLM-5.3-Flash 的 FP8 去限版本，兼顾量化效率与无约束输出，适合实验性部署。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 661 | 254,529 | Qwen3.8-27B 的 GGUF 去限版本，在 abliterated 社区中下载表现稳定。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,373 | 316,128 | Qwen3.8-27B 的 FP8 去限版本，采用 safetensors 格式，点赞数在同类中领先，反映社区对该格式的偏好。 |

---

## 三、生态信号

本周期生态呈现三大趋势：其一，**Qwen 与 GLM 双雄格局确立**，两者均有原生模型及多个社区量化/微调变体入榜，形成从官方到 GGUF/FP8 的完整生态链；其二，**视频生成赛道竞争加剧**，MiniMax-H3 与 LTX-2.5 下载量均突破百万，FastVideo 等加速方案紧随其后，开源视频模型正从"可用"走向"高效可用"；其三，**abliterated/uncensored 微调活跃度显著**，多个 Qwen3.8-27B 去限版本累计下载超 400 万，反映社区用户对可控权重的持续需求，同时量化技术（GGUF、FP8、GSQ）已成为模型普惠化的关键路径。

---

## 四、值得探索

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 当前视频生成领域下载量最高的开源模型，支持多模式输入，社区加速方案（FastVideo）已跟进，是视频生成研究与应用的首选基准。

2. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 下载量近 940 万，是本地部署 Qwen3.8-27B 的最优路径，GGUF 格式配合 llama.cpp 可实现高效推理，适合资源受限场景。

3. **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — 谷歌新一代时间序列预测模型，目前处于预告阶段，对金融、能源等时序敏感领域具有重要研究价值，建议持续关注。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*