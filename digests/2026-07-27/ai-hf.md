# Hugging Face 热门模型日报 2026-07-27

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-27 03:43 UTC

---

# Hugging Face 热门模型日报（2026-07-27）

## 今日速览
Hugging Face 本周热门模型聚焦于多模态 OCR、LLM 对话及高性能微调技术。百度 `Unlimited-OCR` 以超 3,200 点赞登顶，GLM 家族与 Qwen 衍生 GGUF 量化版在中文语料处理上尤为活跃。Laguna-S 系列出现多次不同格式版本（GGUF/NVFP4），证明社区对生成式文本模型的落地应用需求极高。此外，微软 `Mage-Flow` 和 NVIDIA `Cosmos3-Edge` 的加入标志着大厂在基础生成任务上的持续投入，开源权重正成为量化社区争夺的核心资产。

## 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 704 | 56,445 | Laguna-S 系列的正式通用发布，具备强大的上下文处理能力。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 600 | 3,305 | 韩国 Upstage 推出的超大容量 LLM，针对复杂长文处理和推理进行了优化。 |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 450 | 14,049 | 小型高效模型，适合在资源受限设备上进行快速文本生成任务。 |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | **4,481** | **827,191** | 清华大学智源研究院推出，作为当前最受欢迎的对话模型之一，其性能与效率平衡优异。 |
| [KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 199 | 3,764 | 专为编程辅助训练的代码生成模型，支持图像文本理解以解决代码问题。 |
| [Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 193 | 2,400 | Motif 团队推出的 beta 版大模型，专注于特征提取与内容生成，安全合规性强。 |

## 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | **3,220** | **2,593,460** | Baidu 重磅发布的 OCR 模型，主打“无限制”扫描识别能力，处理长图与复杂布局效果出色。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,581 | 34,511 | 创新的多模态对话模型，可将手写笔记或图像转换为结构化文本，非常适合知识整理场景。 |
| [Microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 339 | 1,375 | 微软最新的文本到图像生成工具，采用 Diffusers 框架，致力于提升图像生成的逼真度与多样性。 |
| [Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,298 | 730,129 | 月之暗面开发的具备视觉能力的代码模型，能够解析图表并生成对应逻辑代码，开发辅助能力强。 |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 314 | 35,562 | 新一代视觉 OCR 模型，基于 Qwen 架构，专注于小样本学习与特定领域文档的高精度识别。 |
| [Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,114 | 1,927,138 | HuggingFace 上下载量极高的社区微调版，去除了不必要的过滤机制，适用于各类非敏感视觉问答。 |

## 🔧 专用模型（代码、数学、医疗、嵌入）

*(本分类本周无特别突出的新上榜模型)*

## 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,052 | 631,970 | Bonsai 模型的 ternary (2-bit) 量化版本，在极低显存占用下仍能保持较强的对话表现。 |
| [Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 652 | **2,187,304** | 目前下载量最高的 GGUF 文件之一，展示了 Llama.cpp 生态对轻量级本地大模型的巨大需求。 |
| [Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 203 | 102,684 | 由 Unsloth 提供的 Laguna-S 量化包，针对 vllm 加速部署做了特殊适配，推理速度极快。 |
| [Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,480 | 1,410,054 | empero-ai 的杰作，融合了 Claude 的伦理约束与长上下文（1M Token）能力，非常适合文档摘要任务。 |
| [Qwen3.6-27B-Fable-Fusion-711...](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 644 | 552,026 | 一个极度命名的混合增强模型，集成了多种 LoRA 风格与 Heretic 风格的修正，旨在打破安全限制以发挥最大潜力。 |

## 生态信号
近期数据清晰表明，“**轻量化部署优先**”已成为核心趋势。尽管仍有部分社区追求更大参数量（如 Solar-250B），但像 `Bonsai` 和 `Qwythos` 这样经过极致量化（1bit/2-bit）且拥有百万级下载的模型更受青睐，反映出用户更看重模型在消费级 GPU 或边缘设备上的可用性和响应速度。同时，**多模态（Vision-Language）热度高涨**，不仅有专业的 OCR 和编码工具，连纯语言模型也纷纷上线 vision-only 组件，预示着未来通用的“一切即文本”的交互范式正在加速形成。开源社区对于“Uncensored”或经过特殊调优（Fable/Fusion）的版本表现出极高的尝试意愿，这既是追求极致性能的需求，也是探索模型边界的表现。

## 值得探索
1. **Baid/Unlimited-OCR**: 尽管是传统任务类模型，但其巨大的下载量和点赞数验证了当前高质量文档数字化需求的爆发，建议开发者研究其 feature-extraction 部分以提取高精度文字嵌入用于检索增强。
2. **empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**: 这是一个极具性价比的方案，仅需 9B 级别参数即可支持 1M token 上下文且带有道德约束，对于需要在笔记本或云端低成本运行超长日志分析的用户来说是首选。
3. **thinkingmachines/Inkling**: 该模型的独特性在于结合了“图像转录 + 对话”，非常适合构建个人知识图谱助手或会议纪要自动整理系统，其 conversational 标签暗示了良好的后续追问能力。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*