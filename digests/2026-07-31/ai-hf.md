# Hugging Face 热门模型日报 2026-07-31

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-31 03:34 UTC

---

# Hugging Face 热门模型日报 (2026-07-31)

## 1. 今日速览
本周 Hugging Face 上 multimodal（多模态）与 LLM（大语言模型）继续主导下载量，其中 Qwen 家族及 Moonshot 的 Kimi 模型受到社区高度关注。大量 GGUF 量化版本涌现，显示出本地部署和低资源推理需求的显著增长。特别值得注意的是，百度的 Unlimited-OCR 以极高的下载量证明了对高质量工具模型的旺盛需求。此外，针对特定场景的“Uncensored”或“Aggressive”微调变体依然拥有庞大的社群基础，体现了用户对灵活性的追求。

## 2. 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,685 | 1,527,760 | MoE 架构的通用大模型，主打对话和文本生成任务，榜单中点赞最高的官方模型之一，显示了其强大的社区认可度。 |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 847 | 73,246 | 专注于文本生成的 Transformer 模型，因其流畅的自然语言处理能力而在社区中保持持续热度。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 704 | 12,411 | 超大参数规模（250B）的语言模型，代表了开源界在尝试突破容量极限方面的努力。 |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 582 | 24,542 | 30 亿参数级别的轻量级 LLM，适合边缘设备运行，平衡了性能与计算成本。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 9,043 | 387,822 | 多模态大模型，凭借跨模态理解和对话能力登顶点赞榜，是本周关注度最高的模型。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,654 | 45,658 | 视觉 - 语言处理模型，专注于将图像转换为自然语言描述或对话交互。 |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,589 | 2,598,659 | OCR 识别模型，支持无限制输入尺寸的高精度文档解析，因实用性极强而获得惊人下载量。 |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 323 | 1,100 | 极小的语音合成（TTS）模型，专为 CPU 和边缘 AI 设备设计，满足低延迟语音生成需求。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 353 | 9,225 | 基于 MoE 架构的代码生成器，旨在提升复杂编程任务的解决能力和推理效率。 |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 353 | 57,439 | 新一代 OCR 增强版模型，结合 Qwen3.5 背景知识优化了文字识别准确率。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,191 | 1,803,090 | Qwen 的 GGUF 量化变体，经过特殊微调调整以增强响应性，深受开发者喜爱。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,042 | 955,767 | 高度复杂的社区微调版本，融合了多种 LoRA 权重并通过 MTP 方法进行融合优化。 |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,117 | 697,666 | 采用三进制（ternary）权重的量化模型，能在保持性能的同时大幅减小模型体积。 |

## 3. 生态信号
从榜单可见，**MoE（混合专家）架构**正在成为主流选择，多个榜单模型如 GLM-5.2、Qwen3.6 均采用此设计以兼顾效率与性能。**GGUF 格式**占据半壁江山，表明用户对于端侧部署（Edge AI）的需求正压倒性地优先于云端调用。同时，“Uncensored”或“Heretic”等关键词频繁出现，反映了部分研究者倾向于使用去约束化的权重进行创造性实验的趋势。

## 4. 值得探索

1.  **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)**：作为本周点赞第一的多模态模型，其在长上下文处理和图文理解方面的潜力值得关注，适合构建智能助理应用。
2.  **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**：尽管不是通用大模型，但其数千万级的下载量和 3,500+ 的超高评分证明了它在文档自动化领域的巨大价值，值得集成到工作流中。
3.  **[unswth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF)**：虽然原榜 Luna 热度适中，但经过 Unsloth 量化处理的 GGUF 版本提供了在消费级硬件上运行大模型的高效方案，非常适合本地部署爱好者。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*