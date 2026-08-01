# Hugging Face 热门模型日报 2026-08-01

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-01 03:33 UTC

---



# 📰 Hugging Face 热门模型日报
**日期：2026-08-01**

---

## 一、今日速览

今日 HF 热榜最大亮点是 **moonshotai/Kimi-K3** 以 9,293 周点赞强势登顶，展现出中国市场在多模态大模型领域的强劲势头。DeepSeek 家族同步发布 V4 系列（Flash 及 0731 版本），下载量已突破 290 万，生态影响力持续扩大。社区量化与微调生态异常活跃，Uncensored GGUF 变体（如 DavidAU、HauhauCS 系列）下载量均超百万，反映出本地化部署与自由定制需求的旺盛。百度 Unlimited-OCR 以 250 万下载稳居 OCR 领域头部。

---

## 二、热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,712 | 1,651,533 | 智谱新一代 MoE 对话语言模型，支持多轮交互与复杂推理，是国内主流 LLM 的重要更新。本周点赞近 5k，下载超 165 万，持续领跑国产开源 LLM 榜单。 |
| [deepseek-ai/DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 1,927 | 2,923,499 | DeepSeek 最新 Flash 版轻量高效语言模型，以较低推理成本提供接近旗舰模型的文本生成能力。下载量近 300 万，是全球使用最广泛的开源 LLM 之一。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 1,061 | 0 | DeepSeek V4 Flash 的 7 月 31 日更新版本，附带 arxiv:2606.19348 论文，代表最新技术迭代方向。发布不久下载量待增长，值得持续关注性能基准。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 714 | 12,911 | 韩国 Upstage 推出的 250B 参数级开源旗舰 LLM，面向高性能推理场景。作为超大规模开源模型代表，为研究机构和高预算用户提供了新选择。 |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 863 | 76,212 | Poolside AI 的对话语言模型，注重指令遵循与结构化输出能力。在中参数规模下表现均衡，适合生产环境部署。 |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 596 | 26,928 | 南贝格新一代 3B 参数小模型，针对中文场景优化，适合边缘设备与低成本推理。在小模型赛道提供可靠的开源替代方案。 |
| [EschaLabs/Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 108 | 599 | 基于 Qwen3.5 MoE 架构的微调版本，参数高效但保持较强推理能力。属于社区深度微调实验，适合追求极致性能/参数比的研究者。 |
| [XYZAILab/XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | XYZAILab | 353 | 579 | XYZAI 轻量级 MoE 模型，基于 Qwen3.5 架构，面向低成本部署场景。mini 定位使其成为小团队快速原型验证的候选。 |
| [XYZAILab/XYZ-Aquila-pro](https://huggingface.co/XYZAILab/XYZ-Aquila-pro) | XYZAILab | 327 | 869 | XYZAI 专业版 MoE 模型，集成 agentic-search 能力，支持智能体搜索任务。代表国产开源模型向智能体方向的探索。 |

---

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 9,293 | 493,481 | 月之暗面新一代视觉-语言大模型，支持图像理解与文本生成，本周以绝对优势登顶热榜。融合压缩张量技术（compressed-tensors），推理效率表现突出。 |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,664 | 2,513,603 | 百度开源的多语言 OCR 模型，支持任意分辨率图像文字识别，在文档、场景文本等任务上表现优异。下载量已突破 250 万，成为工业级 OCR 首选之一。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,664 | 57,259 | Thinking Machines 的多模态对话模型，支持图像到文本的流畅交互，注重对话连贯性与视觉理解能力。在学术与开源社区积累了较高关注度。 |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 152 | 5,650 | 微软视觉语言模型，面向复杂视觉推理任务，与 Mage-Flow 工作流配套使用。支持 ComfyUI 生态，适合图像生成工作流集成。 |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 348 | 1,449 | 超轻量级本地 TTS 模型，专为 CPU 与边缘设备优化，支持低延迟语音合成。适合资源受限环境下的本地语音生成场景。 |
| [owensong/Inflect-Nano-v2](https://huggingface.co/owensong/Inflect-Nano-v2) | owensong | 121 | 802 | 比 Micro 更小的 Nano 版 TTS 模型，极致压缩下仍保持可听语音质量。面向嵌入式设备和移动端部署场景。 |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 152 | 2,481 | Audio8 开源 TTS 预览版，0.6B 参数规模支持高质量语音合成，为后续完整模型发布预热。值得 TTS 研究者与本地部署用户关注。 |
| [microsoft/VibeVoice-ASR-BitNet](https://huggingface.co/microsoft/VibeVoice-ASR-BitNet) | microsoft | 135 | 5,464 | 微软基于 BitNet 架构的语音识别模型，以极低精度（1-bit）实现高效 ASR 推理。在音频理解与低功耗场景具有独特优势。 |

---

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 371 | 10,241 | 面向代码生成的专用模型，基于 Qwen3.5 MoE 架构，支持图像-文本-代码多模态理解。适合开发者在本地部署代码助手场景。 |
| [thinkingmachines/Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 198 | 2,971 | Inkling 系列的小尺寸版本，降低多模态对话模型的部署门槛，适合中等资源环境。在保持核心能力的同时显著减少推理开销。 |

---

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,153 | 1,119,057 | DavidAU 基于 Qwen3.6-27B 的无审查 GGUF 微调版，采用 Heretic/NEO/MTP 等技术栈，支持本地高效推理。下载超 110 万，反映社区对自由定制模型的强烈需求。 |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,125 | 712,835 | 采用三元（ternary）2-bit 量化技术的 27B 大模型，以极低精度维持对话能力，适合显存受限场景。2-bit 量化方向代表开源量化社区的前沿探索。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,206 | 1,835,931 | HauhauCS 基于 Qwen3.6-35B MoE 的激进无审查 GGUF 微调版，覆盖视觉与文本能力。下载近 184 万，是社区最大规模的无审查微调项目之一。 |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 273 | 212,426 | LuffyTheFox 基于 Hermes V6 风格的无审查 Qwen3.6 MoE 微调版，兼顾指令遵循与自由输出。在 Hermes 微调圈层内获得稳定关注。 |
| [DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 175 | 261,856 | DavidAU 面向 Qwen3.5-9B 的无审查微调 GGUF 版，采用 Imatrix 校准技术提升量化质量。为中小参数无审查模型提供高质量本地推理选择。 |
| [unsloth/Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 228 | 36,180 | Unsloth 为 Kimi-K3 提供的 GGUF 量化版本，利用 unsloth 加速库优化推理速度。支持本地高效运行月之暗面旗舰多模态模型。 |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 194 | 0 | Unsloth 针对 DeepSeek V4 Flash 0731 版的 GGUF 量化，尚未产生下载，属于刚发布的新品。预计随主模型增长而快速累积使用量。 |
| [not

a-ai/Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 151 | 18,531 | nota-ai 为 Solar-Open2-250B 提供的 NVFP4 量化版本，适配 vLLM 推理引擎，显著降低大模型部署显存需求。为 250B 级别模型的本地推理提供可行路径。 |
| [Comfy-Org/Mage-Flow](https://huggingface.co/Comfy-Org/Mage-Flow) | Comfy-Org | 107 | 60,162 | 基于微软 Mage-VL 的 ComfyUI 工作流节点，集成图像生成与视觉理解能力到 ComfyUI 生态。适合使用 ComfyUI 搭建多模态自动化流水线。 |

---

## 三、生态信号

**模型家族**方面，**Qwen3.6 / Qwen3.5** 家族仍是社区微调最活跃的基座，DavidAU、HauhauCS、LuffyTheFox 等作者基于同一基座衍生出多个无审查 GGUF 变体，下载量合计超 300 万。**DeepSeek V4** 系列以 Flash 版本率先抢占用户心智，官方与 Unsloth 双轨并行加速本地化。**Kimi** 品牌首次登顶，标志着中国厂商在多模态 LLM 赛道的权重提升。

**开源 vs 闭源**：今日榜单几乎全部为开源模型（含权重公开或 GGUF 量化版本），闭源模型无直接上榜，反映出 HuggingFace 社区仍以开源生态为主力。**量化与微调**：GGUF 格式占据微调榜半壁江山，2-bit 三元量化（Ternary-Bonsai）和 NVFP4 量化（Solar）代表下一代低功耗量化的前沿探索，社区对"用小模型做大推理"的需求持续升温。

---

## 四、值得探索

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周绝对冠军，视觉-语言多模态能力的集大成者，融合压缩张量技术，适合需要端到端图像理解+对话的场景，值得关注其推理效率与多语言支持表现。

2. **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — 智谱最新 MoE 架构对话模型，国产开源 LLM 的标杆更新，中文能力与推理基准均有显著提升，适合中文生产环境部署与对比评测。

3. **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — 2-bit 三元量化代表，展示极端量化下大模型对话能力的保留程度，对显存受限场景的 27B 级部署有重要参考价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*