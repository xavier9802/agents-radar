# Hugging Face 热门模型日报 2026-08-02

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-02 03:33 UTC

---



# 📰 Hugging Face 热门模型日报
**日期：2026-08-02 | 样本量：30 个**

---

## 一、今日速览

Kimi-K3 以近万点赞强势登顶本周榜单，成为今日最值得关注的旗舰多模态模型。DeepSeek-V4-Flash 系列持续高居热榜，其 Flash 版本下载量已突破 280 万，社区量化版本紧随其后发布。百度 Unlimited-OCR 以 3717 赞和超 240 万下载刷新了 OCR 领域热度标杆。与此同时，2-bit Ternary-Bonsai 等极端量化模型和多种 Uncensored Qwen3.6 微调版本显示出社区对本地化部署和自由微调的持续热情。

---

## 二、热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,738 | 1,683,442 | 智谱 GLM-5.2 对话模型，支持 MoE 架构与 DSA 注意力机制。获近 5000 点赞，下载超 168 万，是榜单下载量最高的纯文本生成模型之一。 |
| [deepseek-ai/DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 1,947 | 2,814,414 | DeepSeek V4 Flash 推理加速版，面向高吞吐对话场景。下载量突破 280 万，是社区使用最广泛的 DeepSeek V4 变体。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 1,450 | 15,366 | DeepSeek V4 Flash 的 2026-07-31 快照版本，附带 arxiv:2606.19348 技术报告。作为最新研究快照，下载稳步增长。 |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,135 | 716,341 | 采用三元（ternary）2-bit 权重量化的 27B 对话模型，支持 llama.cpp 推理。以极端低比特实现高效本地部署，下载超 71 万。 |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 868 | 77,021 | Poolside 公司推出的 Lagun a S 系列语言模型，针对代码和通用对话优化。以稳健的推理质量在专业用户中获得良好反响。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 718 | 13,426 | Upstage Solar Open2 系列 250B 参数旗舰模型，开源完整权重。是榜单上参数量最大的开源 LLM 之一，吸引研究社区关注。 |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 611 | 27,892 | Nanbeige 4.2 系列 3B 轻量级语言模型，面向端侧和低成本部署场景。小巧高效，在移动端和边缘设备上具有竞争力。 |
| [XYZAILab/XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | XYZAILab | 358 | 650 | XYZAI Lab 的 Aquila 迷你版，基于 Qwen3.5 MoE 架构，兼顾轻量与推理能力。适合资源受限场景的入门级探索。 |
| [XYZAILab/XYZ-Aquila-pro](https://huggingface.co/XYZAILab/XYZ-Aquila-pro) | XYZAILab | 332 | 923 | XYZAI Lab 的 Aquila Pro 版本，集成 agentic search 能力，面向自主代理任务。在搜索增强型 AI 应用中具有潜力。 |
| [nota-ai/Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 152 | 22,396 | 对 Solar Open2-250B 进行 NVFP4 量化优化的版本，适配 vLLM 推理引擎。以更低精度实现高吞吐推理，适合服务化部署。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 9,497 | 559,924 | 月之暗面 Kimi K3 多模态大模型，支持图像-文本到文本任务。本周点赞量断层第一，下载超 55 万，引领多模态热潮。 |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,717 | 2,457,387 | 百度开源的通用 OCR 模型，支持无限分辨率图像的文字识别。下载量超 245 万，是榜单下载量最高的多模态模型之一。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,227 | 1,823,436 | 基于 Qwen3.6-35B-A3B MoE 的无审查微调版本，支持视觉输入。社区对无限制版本需求强劲，下载量接近 183 万。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,243 | 1,173,001 | DavidAU 制作的 Qwen3.6 27B Fable Fusion 微调 GGUF 版本，集成 MTP 多步预测。下载超 117 万，社区高频使用的本地化选择。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,672 | 59,076 | ThinkingMachines Inkling 多模态对话模型，支持图像理解与文本交互。以紧凑架构实现高效多模态推理，受开发者关注。 |
| [ThinkingMachines/Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 213 | 3,998 | Inkling 的轻量版本，面向资源受限场景的多模态推理。更小参数量使其在边缘设备上也具备部署可行性。 |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 365 | 1,565 | 极轻量级本地 TTS 模型，支持 CPU 推理，适合边缘和嵌入式设备。在文字转语音的轻量部署场景中填补空白。 |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 169 | 3,254 | Audio8 的 0.6B 参数 TTS 预览版，基于 ArktTS 架构。作为早期预览版本，展示了高效的语音合成能力。 |
| [microsoft/VibeVoice-ASR-BitNet](https://huggingface.co/microsoft/VibeVoice-ASR-BitNet) | microsoft | 142 | 5,835 | 微软 VibeVoice 语音识别模型，采用 BitNet 二值化权重。以极低精度实现高效 ASR，适合低功耗语音应用。 |
| [lodestones/Kroma](https://huggingface.co/lodestones/Kroma) | lodestones | 97 | 0 | 基于 Krea 生态的文本到图像 LoRA 微调，适配 ComfyUI 工作流。针对创意图像生成社区提供专用风格微调能力。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 391 | 10,771 | KAT Coder V2.5 开发版，基于 Qwen3.5 MoE 架构，专为代码生成优化。面向开发者社区，提供高质量代码补全与生成能力。 |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 173 | 10,525 | 微软 Mage-VL 多模态视觉语言模型，面向通用视觉理解与推理任务。微软在多模态通用能力上的持续投入，具有研究价值。 |
| [microsoft/Fara1.5-27B](https://huggingface.co/microsoft/Fara1.5-27B) | microsoft | 243 | 2,775 | 微软 Fara 1.5 版 27B 参数计算机使用模型，集成视觉理解与工具调用能力。面向 Computer Use 场景，是微软 Agent 产品线的重要一环。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 243 | 41,337 | Unsloth 提供的 Kimi-K3 GGUF 量化版本，支持 llama.cpp 高效推理。利用 Unsloth 加速技术实现本地低延迟部署。 |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 292 | 4,048 | Unsloth 量化的 DeepSeek V4 Flash-0731 GGUF 版本。配合 Unsloth 推理加速，在消费级硬件上实现高效文本生成。 |
| [unsloth/Kimi-K3](https://huggingface.co/unsloth/Kimi-K3) | unsloth | 222 | 1,072 | Unsloth 优化的 Kimi-K3 原生格式版本，利用其压缩张量技术加速推理。为用户提供了比原版更高效的部署选项。 |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 289 | 228,610 | LuffyTheFox 制作的 Qwen3.6 Hermes V6 GGUF 微调版，支持 MoE 架构的本地推理。Hermes 系列在社区中以高质量对话著称。 |
| [DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 189 | 267,572 | DavidAU 的 Qwen3.5 9B Fable Uncensored GGUF 版本，集成 Imatrix 校准与 MTP。小参数版本适合低显存环境的高频使用。 |
| [EschaLabs/Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 112 | 875 | EschaLabs 对 Qwen3.6 MoE 的 W2 量化版本，探索极低比特下的性能边界。代表了社区对 MoE 模型极致量化的持续实验。 |
| [empero-ai/Qwythos-27B-v1](https://huggingface.co/empero-ai/Qwythos-27B-v1) | empero-ai | 89 | 941 | Empero AI 的 Qwythos 27B 多模态版本，基于 Qwen3.5 架构构建。作为新团队作品，展现了 Qwen 生态的活跃衍生能力。 |

---

## 三、生态信号

本周 HF 榜单呈现三个鲜明趋势：**DeepSeek 与 Qwen 双核驱动**。DeepSeek-V4-Flash 系列以官方原始版 + Unsloth 量化版组合霸榜，GLM-5.2 则以近 5000 赞显示国产模型持续崛起。**量化生态高度活跃**——Ternary-Bonsai 2-bit 极端量化、NVFP4 服务级量化、GGUF 社区量产并行推进，反映出本地部署从"能用"迈向"好用"的阶段。开源权重持续挤压闭源 API 空间，但月之暗面 Kimi-K3 以近万赞成为本周最大黑马，证明闭源厂商仍可通过开源权重建立影响力。此外，Uncensored 社区微调版本下载量普遍超百万级，表明自由微调需求依然是社区核心驱动力之一。

---

## 四、值得探索

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周无可争议的顶流，近万点赞 + 56 万下载，综合性能与多模态能力均处于第一梯队，是替换现有多模态模型的首选。

2. **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — 2-bit 三元量化代表，71 万下载验证了极端量化方案的可用性，适合研究低比特推理或部署在低显存环境。

3. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — 百度开源通用 OCR 模型，245 万下载量表明其在生产环境已被广泛采用，适合需要高分辨率文本识别的应用场景。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*