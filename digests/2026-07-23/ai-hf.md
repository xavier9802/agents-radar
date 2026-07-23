# Hugging Face 热门模型日报 2026-07-23

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-23 01:23 UTC

---

# Hugging Face 热门模型日报 (2026-07-23)

## 1. 今日速览
今日 HF 榜单呈现出“多模态大模型”与“极致量化/推理优化”双轮驱动的特征。**google/gemma-4-31B-it** 以破千万的下载量稳居榜首，标志着 Gemma 4 系列已成为主流基准；同时，百度 **Unlimited-OCR** 和 ZAI Lab **GLM-5.2** 在各自领域保持极高热度。值得注意的是，社区对 **Qwen3.6** 及其衍生变体（如 Uncensored、Fable Fusion）的微调与量化版本表现出极强的生命力，而 **Laguna-S** 系列则展示了特定架构在效率上的突破。

## 2. 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,327 | 12,113,203 | Google 最新一代 Gemma 4 指令微调版，支持图文交互。其千万级下载量证明了其在开源生态中的统治地位及极高的实用性。 |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,336 | 545,109 | ZAI Lab 推出的 GLM-5.2 文本生成模型，采用 MoE DSA 架构。作为国产顶尖开源模型代表，其在对话与逻辑任务中表现优异。 |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 2,712 | 2,237,351 | 百度发布的无限上下文 OCR 模型，虽归类为 image-text-to-text，但核心能力在于高精度文本识别。海量下载反映了对长文档 OCR 的刚性需求。 |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,416 | 2,133,420 | 基于 Qwen3.5 的 9B 量化模型，主打 1M 上下文与推理增强。通过 GGUF 格式实现高效部署，深受本地部署用户喜爱。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,000 | 1,997,690 | Qwen3.6 的 35B 无限制微调版，采用 MOE 架构并支持视觉。高点赞与下载表明社区对强大且自由度高的小参数多模态模型的强烈兴趣。 |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 595 | 1,404,962 | Prism ML 开发的 27B Bonsai 模型 1-bit 量化版。极致的低比特量化使其能在消费级硬件上流畅运行，兼顾性能与效率。 |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,223 | 722,058 | 月之暗面 Kimi K2.7 代码专用模型，支持图文输入。凭借压缩张量技术提升效率，是开发者进行代码辅助的重要工具。 |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 391 | 3,056 | Poolside 发布的 Laguna S 2.1 文本生成模型。作为较新的发布，其下载量尚在积累，但标签显示其为原生 Transformer 格式，值得关注其后续表现。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 251 | 0 | Upstage 发布的 Solar Open2 250B 超大参数模型。目前下载量为 0，可能刚发布或处于私有/受限访问阶段，但 250B 规模极具潜力。 |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 230 | 0 | Nanbeige 4.2 系列的 3B 小模型。同样下载量为 0，可能是最新发布的轻量级模型，适合边缘设备或低延迟场景。 |
| [Motif-Technologies/Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 158 | 125 | Motif 3 Beta 版本文本生成模型。早期阶段，下载量极少，属于新探索性项目。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,449 | 16,441 | Thinking Machines 推出的 Inkling 多模态模型，支持图像文本到文本生成。作为榜单最高点赞的非巨头模型，显示出其在创意或多模态理解上的独特优势。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 321 | 62,842 | Qwen3.6 27B 的多重微调融合版，包含 Uncensored 和 Heretic 等社区风格。GGUF 格式便于本地使用，满足特定创作或角色扮演需求。 |
| [bottlecapai/ThinkingCap-Qwen3.6-27B](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B) | bottlecapai | 512 | 12,002 | Bottlecap AI 基于 Qwen3.6 优化的思考链（CoT）模型，支持图文输入。强调推理能力，适合需要复杂逻辑处理的视觉问答场景。 |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 249 | 17,162 | 基于 Qwen3.5 的 OCR 2.0 模型，专注于图像文本提取。相比 Unlimited-OCR，它更侧重于垂直领域的 OCR 精度优化。 |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 124 | 0 | 微软发布的 Mage-Flow 文生图模型。下载量为 0，可能为新发布或需特定权限，代表了微软在生成式视觉领域的布局。 |
| [nvidia/Cosmos3-Edge](https://huggingface.co/nvidia/Cosmos3-Edge) | nvidia | 89 | 6,623 | NVIDIA Cosmos 3 Edge 版本，面向边缘设备的视频或图像生成/编辑模型。利用 Diffusers 库，旨在实现端侧的高效多媒体处理。 |
| [conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit) | conradlocke | 495 | 0 | 针对 Krea-2 的身份编辑 LoRA 模型。用于 ComfyUI 工作流，允许用户在不改变面部特征的情况下编辑图像，下载量为 0 可能因仅上传了 LoRA 权重。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b) | nvidia | 914 | 590,230 | NVIDIA Nemotron 3.5 的 0.6B 流式自动语音识别（ASR）模型。专为实时语音转文本设计，轻量且高效，广泛应用于语音交互场景。 |
| [nvidia/Nemotron-3-Embed-1B-BF16](https://huggingface.co/nvidia/Nemotron-3-Embed-1B-BF16) | nvidia | 102 | 93,021 | NVIDIA Nemotron 3 的 1B 嵌入模型，支持句子相似度任务。BF16 精度平衡了性能与显存占用，适用于 RAG 系统中的向量检索。 |
| [OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize) | OpenMOSS-Team | 308 | 92,265 | 支持转录与说话人分离（Diarization）的音频文本到文本模型。在会议记录、播客分析等需要区分不同说话人的场景中非常有用。 |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 154 | 58 | MiniCPM 机器人操作模型，属于 Vision-Language-Action 架构。专门用于机器人操控任务，将视觉感知转化为动作指令。 |
| [openbmb/MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 114 | 72 | MiniCPM 机器人追踪模型，同样基于 VLA 架构。专注于动态环境下的目标追踪，为机器人提供持续的视觉反馈。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 941 | 432,196 | Bonsai 27B 的三元（Ternary）量化 GGUF 版本。相比 1-bit 版本，三元量化可能在精度损失与压缩率之间取得更好平衡，适合对精度有更高要求的本地部署。 |
| [unsloth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 106 | 0 | Unsloth 提供的 Laguna S 2.1 量化版。下载量为 0，可能是最新上传的量化格式，旨在利用 Unsloth 的优化技术加速推理。 |
| [poolside/Laguna-S-2.1-NVFP4](https://huggingface.co/poolside/Laguna-S-2.1-NVFP4) | poolside | 91 | 1,953 | Laguna S 2.1 的 NVFP4 量化版本，专为 NVIDIA 硬件优化。通过特定的量化格式提升在 GPU 上的推理吞吐量。 |
| [poolside/Laguna-S-2.1-GGUF](https://huggingface.co/poolside/Laguna-S-2.1-GGUF) | poolside | 91 | 289 | Poolside 官方发布的 Laguna S 2.1 GGUF 版本。作为基础量化包，供 llama.cpp 等框架直接使用，目前下载量较低，处于推广初期。 |
| [prism-ml/Bonsai-27B-mlx-1bit](https://huggingface.co/prism-ml/Bonsai-27B-mlx-1bit) | prism-ml | 165 | 25,273 | Bonsai 27B 的 1-bit 量化 MLX 版本，专为 Apple Silicon 优化。使得 27B 参数模型能在 MacBook 等设备上高效运行。 |
| [GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF) | GnLOLot | 153 | 51,746 | 基于 MiniCPM5 1B 的社区微调 GGUF 模型，融合了 Claude Opus 的风格与 Fable 思维链。小参数下的高性能微调示例，适合资源受限环境。 |
| [unsloth/inkling-GGUF](https://huggingface.co/unsloth/unsloth/inkling-GGUF) | unsloth | 120 | 7,377 | Unsloth 对 Inkling 模型的 GGUF 量化版本。结合 Unsloth 的加速技术，提升多模态模型在本地环境的推理速度。 |

## 3. 生态信号
当前生态呈现三大趋势：一是 **Qwen3.6 家族**成为社区微调与量化的绝对主力，从官方基座到各种 Uncensored、Thinking 风格的衍生版层出不穷，显示出其架构的极强适应性。二是 **极致量化**持续火热，1-bit、Ternary、NVFP4 等多种前沿量化格式并存，用户不仅追求 GGUF 的通用性，更开始关注针对特定硬件（如 Apple MLX、NVIDIA）优化的格式以提升推理效率。三是 **多模态下沉**，随着 Gemma 4 和 GLM 5.2 等大模型的普及，基于它们的轻量级 OCR、ASR 和机器人控制模型（如 MiniCPM-Robot 系列）正在快速填补垂直应用场景的空白。

## 4. 值得探索
1. **[google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it)**：作为本周下载量最高的模型，Gemma 4 代表了当前开源多模态能力的最高水平之一，适合构建通用的智能助手应用。
2. **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)**：其 1-bit 量化版本在保持较高下载量的同时，展示了极低比特量化在 27B 规模模型上的可行性，是研究边缘部署 LLM 的极佳案例。
3. **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)**：对于需要构建实时语音交互系统的开发者，这个 0.6B 参数的流式 ASR 模型提供了高性能与低延迟的完美平衡，且 NVIDIA 的生态支持完善。