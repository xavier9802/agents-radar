# Hugging Face 热门模型日报 2026-09-06

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-06 04:06 UTC

---



# 📊 Hugging Face 热门模型日报
**日期：2026-09-06** | 共 30 个模型

---

## 1. 今日速览

本周 Hugging Face 热度最高的新模型来自 DeepSeek 的 **DeepSeek-V4-Flash-Vision-Exp**，作为视觉语言模型的实验版本引发大量关注。Qwen 家族持续霸榜，Qwen3.8-27B 以超过 14,000 点赞稳居语言模型首位，同时社区围绕其产生了大量 GGUF 量化与去审查微调版本。视频生成领域迎来 MiniMax-H3 与 LTX-2.5 的双强竞争，Google 的时间序列模型 TimesFM 3.0 也正式开源。整体趋势显示：**多模态大模型**与**高效量化部署**是当前社区最活跃的两个方向。

---

## 2. 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 14,044 | 6,024,467 | Qwen3.8 系列的 27B 参数主力模型，支持图文对话与多轮交互，下载量突破 600 万，是目前社区使用最广泛的开源 LLM 之一。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,918 | 401,327 | Qwen3.8 Flash 系列的下一代实验版本，兼顾性能与推理效率，定位为轻量级多模态对话模型。 |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,938 | 5,057,414 | MiniMax 最新多模态模型，支持文本到图像与图像到视频生成，下载量超 500 万，是当前视频生成领域的热门选择。 |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,560 | 255,006,933 | 最流行的句子嵌入模型之一，轻量高效，累计下载超过 2.5 亿次，是 RAG 和语义搜索的基础设施级模型。 |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,702 | 14,739,982 | OpenAI 的经典文本生成模型，仍是众多研究和教程的首选基座，累计下载近 1,500 万次。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,080 | 727,610 | GLM-5.3 系列的 Flash 版本，支持图文输入与对话输出，在效率与质量之间取得良好平衡。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,720 | 370,417 | GLM-5.3 完整版本，采用 MoE 架构，专注纯文本生成任务，下载量已突破 37 万。 |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,986 | 56,175,564 | Google 的经典 BERT 基座模型，累计下载超 5,600 万次，仍是 NLP 预训练和微调的标杆模型。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 443 | 6,195 | 腾讯混元 Hy4 预览版，国产大模型代表之一，支持多轮文本对话，目前处于早期开源阶段。 |
| [IFM/K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 175 | 1,333 | IFM 推出的 36B 参数 MoVA 架构模型，专注高效文本生成，属于较新的探索性项目。 |

---

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,894 | 1,484,329 | Lightricks 最新图像到视频生成模型，支持文本、图像、视频多种输入模态，下载量接近 150 万，是视频生成赛道的明星模型。 |
| [DeepSeek/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 684 | 184,542 | DeepSeek 视觉语言模型的实验版本，支持图像-文本联合理解与生成，本周新增关注度最高。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 449 | 5,962 | Breeze 第二代文本转语音模型，支持高质量语音合成，适合音频生成应用。 |
| [facebook/mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 263 | 12,961 | Meta 的多语言语音预训练模型 MMS，支持 100+ 语言语音识别与合成，跨语言场景的实用选择。 |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,210 | 20,755,211 | OpenAI CLIP 视觉-语言对齐模型，支持零样本图像分类，累计下载超 2,000 万次，是多模态应用的经典基石。 |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 279 | 22,851 | 基于 MiniMax-H3 的快速视频生成加速方案，仅需 4 步推理，大幅降低视频生成成本。 |

---

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 460 | 123,025 | Google 第三代时间序列预测模型，专攻时序数据分析与预测任务，是业界首个开源的大型时序基础模型。 |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,156 | 7,101,423 | DistillBERT 轻量版 BERT，在保持 97% 性能的同时模型体积减半，累计下载超 700 万，是部署友好型嵌入模型的首选。 |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 551 | 4,755 | Spark-X2.5 的 4B 轻量版本，专注高效文本生成，适合资源受限的推理场景。 |

---

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,548 | 10,157,510 | Unsloth 提供的 Qwen3.8-27B GGUF 量化版本，累计下载突破 1,000 万，是本地部署规模最大的 Qwen 量化模型。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 966 | 1,527,627 | 社区激进去审查微调版本，基于 MTP 架构优化，在本地 GGUF 部署场景中广受欢迎。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 988 | 2,453,361 | JonathanColetti 制作的去审查 GGUF 版本，下载量超 245 万，是社区最受欢迎的非审查 Qwen 变体之一。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,096 | 968,936 | 采用 Abliterated 技术去除审查的 Qwen3.8 版本，同时提供 GGUF 与 MLX 格式，满足多平台本地部署需求。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 800 | 780,823 | Unsloth 对 Qwen3.8-Flash-Next 的 GGUF 量化版本，便于低资源环境的本地推理部署。 |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 418 | 297,493 | ISTA-DASLab 采用 GSQ+RCO 混合精度量化方案，在保留模型质量的同时大幅降低显存占用。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 729 | 283,774 | orcarouter 社区成员制作的去审查 GGUF 版本，采用 Abliterated 技术，在本地部署圈有稳定用户群。 |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 240 | 106,845 | 针对 Flash-Next 版本的去审查 GGUF 量化，适合追求更轻量部署的用户。 |
| [DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion...](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 227 | 174,405 | DavidAU 整合多重技术（Cold-Fusion、Heretic、NEO-CODER）的超长命名微调版本，专注编码与推理能力增强。 |
| [Jackrong/Qwopus3.8-27B-Flash-GGUF](https://huggingface.co/Jackrong/Qwopus3.8-27B-Flash-GGUF) | Jackrong | 120 | 10,680 | Jackrong 基于 llama.cpp 适配的 Qwen3.8 Flash GGUF 版本，面向 C++ 推理场景优化。 |

---

## 3. 生态信号

**Qwen 家族占据绝对主导**：本日报 30 个热门模型中，直接以 Qwen3.8 为基础的模型占比超过 40%，包括官方版本、GGUF 量化、去审查微调及社区变体，显示出 Qwen 系列在开源生态中的统治力。**视频生成竞争加剧**：MiniMax-H3 与 LTX-2.5 在下载量上形成双雄格局，同时 FastVideo 推出了 4 步快速推理方案，表明视频生成正从"追求质量"向"追求效率"演进。**量化部署生态高度活跃**： Unsloth 的 GGUF 量化包下载量已突破千万级，社区围绕 Qwen3.8 产生了十余个去审查/微调变体，反映出本地部署与定制化需求的持续增长。**Google TimesFM 3.0 开源**标志着时序预测模型正式进入开源大模型赛道，值得后续关注。

---

## 4. 值得探索

1. **[Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5)** — 视频生成领域最新的强有力竞争者，支持图像/视频/文本多模态输入，本地部署可行，适合探索高质量视频生成的开源方案。

2. **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — Google 开源的首个大型时序预测基础模型，填补了时序分析领域缺少大模型的空白，对金融、能源等时序数据密集场景具有实用价值。

3. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 下载量超千万的社区量化标杆，提供了成熟的本地部署路径，适合想在消费级硬件上运行 27B 级别多模态模型的开发者和研究者。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*