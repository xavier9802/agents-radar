# Hugging Face 热门模型日报 2026-07-30

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-30 02:50 UTC

---

# Hugging Face 热门模型日报 (2026-07-30)

## 今日速览
本周榜单中，多模态大模型占据主导地位，特别是 Moonshot 的 Kimi 系列和 Qwen 家族的衍生版本表现强劲。社区活跃度高体现在 GGUF 量化版本的爆发式增长，表明本地部署需求持续增长。百度 Unlimited-OCR 以惊人的下载量（近 270 万）遥遥领先，显示实用型工具模型的巨大市场价值。同时，Solar-Open2 等超大参数模型虽参数庞大但社区热度相对平稳，显示出技术分层清晰。

## 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B) | Qwen | 2,587 | 6,158,876 | MoE 架构的高效混合专家模型，在中文语境下表现卓越，下载量破六百万成为开源首选。 |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 690 | 2,339,098 | 27B 参数的 GGUF 量化版 Bonsai 模型，采用 1-bit 极低比特压缩，兼顾高性能与低显存占用。 |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,516 | 1,262,662 | 基于 Claude 思想优化的 9B 量化模型，拥有 1M 超长上下文窗口推理能力，性价比极高。 |
| [unsloth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 247 | 129,601 | Laguna 系列的 GGUF 量化适配版，支持 vllm 加速推理，适合低资源环境下的快速文本生成。 |

## 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 8,685 | 99,214 | 本周点赞王，Moonshot 最新的多模态理解模型，在处理复杂图文推理任务上表现突出。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,641 | 39,052 | 专注于图像到文本转换的多模态模型，凭借高点赞数显示社区对其视觉理解能力的认可。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,171 | 1,855,505 | 去限制版 Qwen 多模态变体，结合 A3B 结构，在图像生成与理解领域提供无约束创作空间。 |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 290 | 645 | 轻量级端到端 TTS 模型，专为边缘设备和 CPU 优化，实现超小体积下的高质量语音合成。 |

## 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,517 | 2,694,935 | 百度推出的无边框 OCR 模型，针对扫描文档和复杂背景文字识别进行了极致优化。 |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 319 | 6,275 | 基于 Qwen3.5 Moe 架构开发的代码生成助手，具备较强的代码补全与逻辑生成功能。 |

## 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 948 | 736,692 | 社区深度微调的 Qwen3.6 GGUF 版本，融合了多种 LoRA 权重并提供去限制特性。 |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,098 | 665,427 | 采用三值化（Ternary）技术的 Bonsai 量化模型，进一步压缩体积并降低计算延迟。 |
| [not-ai/Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 140 | 6,189 | Solar 系列的大规模模型 NVFP4 量化探索，旨在为超大型模型寻找更高效的存储方案。 |

## 生态信号
本月趋势显示 **QQW/Qwen** 家族与 **Kimi** 家族双头垄断，其衍生量化版本（GGUF/A3B）数量激增，反映了开源社区对高效推理格式的迫切需求。**Moonshot** 的新品获得点赞榜冠军，证明前沿多模态架构仍最受关注。值得注意的现象是：**“去限制”（Uncensored）** 标签频繁出现在前排行列，且下载量普遍高于普通版，说明用户对自由生成内容的偏好强烈；此外，百度 Ultra-OCR 的超高下载量验证了垂直领域落地模型的务实价值。

## 值得探索
1. **[Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)**：作为下载量最高的官方模型之一，其 A3B 稀疏架构在保持高性能的同时大幅降低了计算成本，是研究 LMOE（Large Model of Experts）结构的优质样本。
2. **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**：展示了如何通过少量参数的 9B 模型借助长窗口技巧实现对百万 token 上下文的处理，对于追求高性价比本地部署的用户极具吸引力。
3. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**：尽管不是通用 LLM，但其极高的下载证明了专用 NLP 模型在特定场景（如智能办公、文档自动化）中的商业潜力和广泛实用性。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*