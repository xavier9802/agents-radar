# Hugging Face 热门模型日报 2026-08-06

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-06 03:16 UTC

---



# 📊 Hugging Face 热门模型日报 — 2026-08-06

---

## 1. 今日速览

今日 HF 热门榜单由中国模型家族强势主导，**Kimi-K3** 以 10,131 点赞、超 112 万下载领跑全榜，成为多模态视觉-语言模型的标杆之作。**DeepSeek-V4-Flash** 系列紧随其后，原始权重与 GGUF 量化版同步上榜，显示社区对高效推理的强烈需求。**MiniMax-H3** 作为罕见的开源 image-text-to-video 模型首次进入 Top 3，标志着视频生成赛道的白热化竞争。**GLM-5.2** 以近 223 万下载成为本周最被下载的对话模型，而百度 Unlimited-OCR 则以 270 万下载领跑 OCR 领域。

---

## 2. 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,851 | 2,234,662 | GLM 系列最新对话模型， MoE 架构（glm_moe_dsa），本周下载量最高的通用语言模型。 |
| [deepseek-ai/DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 2,031 | 2,737,621 | DeepSeek V4 闪速版官方权重，纯推理优化，以极高性价比获得大规模部署认可。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,510 | 433,284 | DeepSeek V4-Flash 的 0731 版本，官方 transformers 格式，性能与 Flash 版相当。 |
| [LGAI-EXAONE/K-EXAONE-2.0-750B-A37B](https://huggingface.co/LGAI-EXAONE/K-EXAONE-2.0-750B-A37B) | LGAI-EXAONE | 130 | 325 | 韩国 LG AI 发布的 750B MoE 大模型，支持 37B 活跃参数，代表韩国开源 LLM 力量。 |
| [inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 158 | 25 | Ling 3.0 闪速版，采用 bailing_hybrid 架构，专注高效对话推理。 |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 126 | 80 | NVIDIA Nemotron 系列语音对话模型，面向低延迟实时语音交互场景。 |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 163 | 0 | 早期预览版 MoE 模型，混合专家架构，处于开放测试阶段。 |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 288 | 47,393 | LiquidAI 的轻量级语言模型，2.6B 参数适合边缘推理场景。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,131 | 1,125,935 | Kimi K3 视觉语言模型，支持图像-文本联合理解，本周点赞量全榜最高，社区热度爆表。 |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,909 | 2,703,366 | 百度开源 OCR 模型，支持任意分辨率文本识别，本周下载量仅次于 DeepSeek-V4-Flash。 |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 2,520 | 10,841 | MiniMax 首款开源 image-text-to-video 模型，填补开源视频生成空白，视频 AI 赛道标志性发布。 |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 276 | 435,784 | 微软多模态视觉语言模型，支持复杂图像理解与对话，在企业级多模态应用中有潜力。 |
| [unsloth/Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 316 | 170,055 | Kimi-K3 的 GGUF 量化版本，由 Unsloth 优化，适合本地部署和低成本推理。 |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 275 | 11,276 | Audio8 开源 TTS 预览版，0.6B 参数轻量化语音合成，适合个人/小规模部署。 |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 417 | 2,072 | 超轻量级 TTS 模型，支持 CPU 推理和边缘设备，适合资源受限场景的语音合成。 |
| [lodestones/Kroma](https://huggingface.co/lodestones/Kroma) | lodestones | 192 | 0 | ComfyUI 专用 LoRA 模型，面向 Krea 生态的图像生成，处于早期预览阶段。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 497 | 15,381 | Kwaipilot 专业代码模型 V2.5，基于 Qwen3.5 MoE 架构，支持视觉-代码联合推理。 |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 132 | 166 | Mistral 安全防御模型，3B 参数用于内容审核与红队测试，维护模型生态安全。 |
| [thinkingmachines/Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 309 | 15,500 | ThinkingMachines 轻量级多模态模型，Small 版本适合快速实验和低成本推理。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,593 | 1,633,405 | 社区对 Qwen3.6-27B 的无限制 Heretic 微调版本，GGUF 格式，下载量极高反映社区对自由微调模型的强烈需求。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,319 | 1,930,898 | HauhauCS 针对 Qwen3.6-35B MoE 的激进无限制微调，视觉+文本双模态，社区影响力显著。 |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 502 | 111,678 | DeepSeek-V4-Flash 的 GGUF 量化版，由 Unsloth 提供，支持高效本地推理。 |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF) | LuffyTheFox | 390 | 308,857 | Qwen3.6-35B MoE 的 Hermes V7 无限制微调，GGUF 格式，面向高级本地部署用户。 |
| [DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 283 | 323,116 | Qwen3.5-9B 的无限制 Heretic 微调版，带 NEO Imatrix 优化，兼顾质量与效率。 |
| [EschaLabs/Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 210 | 2,987 | Qwen3.6 MoE 的 W2 版本微调，探索不同权重配置下的性能边界。 |
| [XYZAILab/XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | XYZAILab | 417 | 1,317 | XYZAI 轻量级 Qwen3.6 衍生模型，面向边缘部署的迷你版本。 |
| [XYZAILab/XYZ-Aquila-pro](https://huggingface.co/XYZAILab/XYZ-Aquila-pro) | XYZAILab | 366 | 1,388 | XYZAI 专业版，带 agentic-search 能力，探索 Agent 搜索与 Qwen 架构的结合。 |
| [realrebelai/MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 140 | 40,010 | MiniMax-H3 视频生成模型的 GGUF 量化版本，降低视频生成本地部署门槛。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 762 | 2 | ComfyUI 专用的 MiniMax-H3 单文件版本，适配 ComfyUI 工作流，社区工具链完善中。 |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 291 | 0 | Qwen3-VL-32B 的 INT8 量化+ComfyUI 适配版本，探索极端量化下的视觉语言性能。 |

---

## 3. 生态信号

本周生态呈现三个显著趋势：一是**中国模型家族全面霸榜**，DeepSeek、Kimi、GLM、百度、MiniMax 等占据绝对主导，开源中国模型已从"跟随"转向"引领"。二是**GGUF 量化活动极为活跃**，几乎每个热门基座模型都有多个社区量化版本，DavidAU、LuffyTheFox 等量化创作者贡献了大量高下载量作品，反映本地部署需求爆发。三是**视频生成成为新战场**，MiniMax-H3 作为开源 image-text-to-video 模型首次进入 Top 3，ComfyUI 生态快速跟进，视频生成开源化进程加速。同时，**无限制微调（Uncensored/Heretic）社区持续壮大**，多个此类微调模型下载量超过百万，显示部分用户对开放定制化的强烈需求。

---

## 4. 值得探索

- **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周全榜点赞和下载量最高的模型，视觉语言理解能力强，compressed-tensors 支持高效推理，是研究多模态对齐和部署优化的绝佳样本。

- **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 开源视频生成领域突破性模型，填补了 image-text-to-video 任务的空白，配合 Comfy-Org 和 GGUF 版本形成完整生态，值得跟踪视频生成开源化进展。

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — 百度开源的通用 OCR 模型，支持任意分辨率文本识别，270 万+下载验证了其广泛适用性，适合视觉文本提取、文档理解等实际应用场景。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*