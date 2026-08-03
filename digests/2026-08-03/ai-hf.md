# Hugging Face 热门模型日报 2026-08-03

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-03 03:35 UTC

---



# 📰 Hugging Face 热门模型日报
**日期：2026-08-03**

---

## 今日速览

Kimi-K3 以 9,661 点赞领跑榜单，DeepSeek-V4 系列（原版+Flash）持续霸榜，GLM-5.2 与 Solar-Open2-250B 强势入围。多模态赛道迎来百度 Unlimited-OCR 与 Microsoft Mage-VL，MiniMax-H3 成为首个开源的 image-to-video 模型。社区量化与微调活动异常活跃，GGUF 格式席卷榜单，显示出用户对本地部署的强烈需求。

---

## 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | --- | ---: | ---: | :--- |
| [DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 1,960 | 2,785,810 | DeepSeek 最新旗舰文本生成模型，支持对话与指令遵循。下载量破 278 万，稳居榜单前列。 |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 1,780 | 156,173 | 7 月 31 日发布的 Flash 轻量版本，论文 arxiv:2606.19348 同步公开。兼顾性能与效率，适合快速部署。 |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,758 | 2,050,533 | 智谱 GLM 系列最新 MoE 架构模型，支持文本生成与对话。下载量超 205 万，社区反响热烈。 |
| [Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 720 | 14,863 | Upstage 开源的 250B 参数大模型，完整权重释放。为研究型用户提供了强大的本地推理基础。 |
| [Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 154 | 68,199 | Solar-Open2 的 NVFP4 量化版本，显著降低显存占用。让 250B 模型在消费级硬件上运行成为可能。 |
| [Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 879 | 80,102 | Poolside 推出的高效文本生成模型，专注指令跟随。下载量近 8 万，适合企业级应用。 |
| [Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | nanbeige | 628 | 33,042 | 南贝科技 3B 轻量模型，专注中文场景优化。小参数高能效，适合边缘设备部署。 |
| [XYZ-Aquila-pro](https://huggingface.co/XYZAILab/XYZ-Aquila-pro) | xyzailab | 335 | 1,094 | XYZAI Lab 的 Agentic 搜索增强模型，支持文本生成。适合需要联网搜索的智能体应用。 |
| [Instella-MoE-16B-A3B-Think](https://huggingface.co/amd/Instella-MoE-16B-A3B-Think) | amd | 124 | 1,957 | AMD 推出的 MoE 架构推理优化模型，针对 RDNA 硬件调优。为 GPU 用户带来高效推理体验。 |

---

## 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | --- | ---: | ---: | :--- |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 9,661 | 837,202 | 月之暗面推出的图像-文本-文本多模态模型，点赞数断层领先。支持特征提取与压缩推理，生态热度第一。 |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,783 | 2,536,284 | 百度开源的无限分辨率 OCR 模型，支持图像文本提取。下载量超 253 万，视觉语言任务标杆。 |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | minimaxai | 281 | 0 | MiniMax 开源的图像-文本到视频生成模型，填补多模态视频生成空白。首批下载记录为零，等待评测爆发。 |
| [Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 192 | 272,148 | 微软开源的多模态视觉语言模型，支持图像理解与对话。下载量近 27 万，适合 RAG 增强场景。 |
| [Fara1.5-27B](https://huggingface.co/microsoft/Fara1.5-27B) | microsoft | 250 | 2,938 | 微软推出的 27B 多模态模型，专注计算机使用能力。适合构建自动化操作与 GUI 交互智能体。 |
| [Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 232 | 6,839 | ThinkingMachines 推出的轻量多模态模型，支持图像文本理解。小尺寸高效率，适合资源受限环境。 |
| [XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | xyzailab | 366 | 903 | XYZAI Lab 的轻量多模态版本，基于 Qwen3.6 架构。适合快速部署与原型验证。 |
| [Kroma](https://huggingface.co/lodestones/Kroma) | lodestones | 129 | 0 | 基于 Krea2 的文本到图像生成 LoRA，适配 ComfyUI 工作流。首发零下载，待社区验证。 |

---

## 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | --- | ---: | ---: | :--- |
| [KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | kwaipilot | 402 | 13,164 | Kwai 推出的代码专用模型，支持图像-文本-代码生成。基于 Qwen3.5 MoE 架构，开发者工具链优选。 |
| [Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 372 | 1,825 | 超轻量级本地 TTS 模型，支持 CPU 推理。边缘设备与离线语音合成场景的理想选择。 |
| [Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | audio8 | 180 | 4,314 | Audio8 开源的 0.6B 参数 TTS 预览模型，支持特征提取。低资源部署，语音合成爱好者可试水。 |

---

## 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | --- | ---: | ---: | :--- |
| [Qwen3.6-27B-Fable-Fusion...GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,345 | 1,372,285 | DavidAU 基于 Qwen3.6-27B 的微调版本，移除安全限制。下载量破 137 万，社区活跃度极高。 |
| [Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 305 | 259,237 | LuffyTheFox 的 Hermes 风格微调，移除内容过滤。下载量近 26 万，适合自由对话场景。 |
| [Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,244 | 1,892,654 | HauhauCS 的激进风格微调，支持视觉理解。点赞 3,244、下载近 190 万，热度仅次于 Kimi-K3。 |
| [Qwen3.5-9B-The-Defiant-Fable...GGUF](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 210 | 292,511 | DavidAU 的 9B 轻量微调版本，采用 MTP 技术。下载量近 29 万，兼顾性能与资源效率。 |
| [DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 344 | 48,707 | Unsloth 提供的 Flash 版本 GGUF 量化。优化推理速度，适合本地 GPU 部署。 |
| [Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 252 | 88,481 | Unsloth 对 Kimi-K3 的 GGUF 量化版本。让 83 万下载的原版模型在本地设备高效运行。 |
| [Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 120 | 2,550 | EschaLabs 的微调版本，专注 MoE 架构优化。下载量约 2,500，适合研究实验。 |
| [MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | comfy-org | 97 | 2 | ComfyUI 兼容版本，适配图像视频生成工作流。首发阶段，等待社区集成。 |

---

## 📊 生态信号

**模型家族势头：** DeepSeek-V4 系列（含 Flash 与 GGUF 量化版）形成矩阵式霸榜，GLM-5.2 与 Solar-Open2-250B 构成第二梯队。Qwen3.6 生态在微调社区活跃，DavidAU、LuffyTheFox、HauhauCS 等创作者贡献多个热门 GGUF 版本。

**开源 vs 闭源：** 本轮榜单以开源模型为主导，DeepSeek、GLM、Solar、Qwen 等开源权重全面开花。闭源 API 在 Hugging Face 热度相对较低，反映用户更倾向本地部署与可审计的开源方案。

**量化与微调活动：** GGUF 格式占据下载总量的核心份额，Unsloth 与社区创作者推动量化普及。 uncensored 风格微调引发高下载，显示用户对无限制内容生成的需求旺盛，但也带来合规风险。

---

## 🔍 值得探索

1. **[Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 点赞 9,661 断层领先，代表多模态能力的新高度。支持图像-文本到文本生成与特征提取，适合研究 VLM 前沿能力。

2. **[DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash)** — 278 万下载验证其工业级可用性。Flash 版本在性能与效率间取得平衡，是企业部署的首选基座。

3. **[MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 首个开源的 image-text-to-video 模型，填补多模态视频生成空白。虽然首发下载为零，但技术突破值得密切关注。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*