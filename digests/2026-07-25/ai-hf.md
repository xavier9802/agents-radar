# Hugging Face 热门模型日报 2026-07-25

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-25 03:21 UTC

---

# Hugging Face 热门模型日报 (2026-07-25)

## 今日速览
今日 HF 热门榜单呈现出**多模态大模型（VLM）与高效量化技术**并行的强劲趋势。Qwen 3.6 系列及其社区微调版本占据半壁江山，尤其是混合专家（MoE）架构在保持高性能的同时显著降低了部署门槛。同时，GLM-5.2 和 Gemma-4 等新一代开源基座模型下载量激增，显示出开发者对高质量通用基座的迫切需求。此外，OCR 和机器人视觉任务中涌现出多个垂直领域专用模型，反映出 AI 应用正加速向具体场景落地。

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,416 | 667,403 | 智谱最新一代 MoE 架构语言模型，具备强大的对话与推理能力，近期下载量爆发式增长，成为开源界新宠。 |
| [google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,360 | 12,629,921 | Google 发布的 31B 参数指令微调模型，凭借极高的下载量和稳定的性能，继续巩固其在中等规模开源模型中的领先地位。 |
| [Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B) | Qwen | 2,504 | 6,460,680 | 通义千问 3.6 系列的 MoE 变体，仅激活 3B 参数即可发挥 35B 模型的潜力，极大地优化了推理成本与效率。 |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,019 | 2,500,391 | 百度推出的高精度 OCR 模型，支持长文本与复杂布局解析，在图像文本转换任务中表现卓越，下载量稳居前列。 |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 613 | 28,992 | 专注于代码生成的轻量级语言模型，通过特定数据集微调提升了编程逻辑准确性，适合嵌入式或边缘设备部署。 |
| [Motif-Technologies/Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 185 | 2,108 | 新兴的文本生成模型，主打特征提取与基础语言理解，目前处于 Beta 阶段，适合早期探索者测试。 |
| [fdtn-ai/antares-1b](https://huggingface.co/fdtn-ai/antares-1b) | fdtn-ai | 150 | 4,266 | 一款仅有 1B 参数的安全导向型语言模型，专为资源受限环境下的安全内容过滤与基础交互设计。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 236 | 891 | 微软推出的文本到图像生成模型，擅长处理复杂指令与图像编辑任务，为创意工作流提供新的开源选择。 |
| [nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b) | nvidia | 937 | 797,525 | NVIDIA 发布的流式语音识别模型，仅 0.6B 参数却支持实时转录，在低延迟应用场景中极具竞争力。 |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 373 | 8,169 | 纳米贝格系列最新 3B 多模态模型，虽下载量不高，但在特定垂直领域的图文理解上展现出独特优势。 |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 173 | 559 | 面向机器人操作的视觉-语言-动作模型，旨在提升机械臂在复杂环境中的抓取与操作精度，具前沿探索价值。 |
| [openbmb/MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 124 | 349 | 专注于机器人视觉跟踪任务的模型，结合 MiniCPM 的多模态能力，为自动化物流与巡检提供技术支撑。 |
| [conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit) | conradlocke | 532 | 0 | 基于 Krea-2 的身份编辑 LoRA，允许用户在不改变面部特征的前提下进行风格迁移，是图像创作爱好者的利器。 |
| [nvidia/Cosmos3-Edge](https://huggingface.co/nvidia/Cosmos3-Edge) | nvidia | 113 | 30,303 | NVIDIA Cosmos 系列的边缘版视频生成模型，优化了移动端与边缘设备的推理速度，适合实时视频处理场景。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,263 | 756,668 | 月之暗面推出的代码专用模型，融合视觉理解能力，在复杂代码生成与调试任务中表现优异，深受开发者喜爱。 |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 126 | 396 | 一款专注于开发环境的代码辅助模型，基于 Qwen3.5-MoE 架构，提供高效的代码补全与重构建议。 |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 277 | 30,292 | 针对文档扫描与复杂版面分析的 OCR 专用模型，在表格识别与多语言混合文本处理上具有高精度。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,547 | 27,883 | 思考机器发布的视觉语言模型，擅长图像描述生成与视觉问答，在对话式视觉应用中表现流畅自然。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 632 | 2,028,115 | Bonsai 系列的 27B GGUF 量化版本，采用 1-bit 量化技术，在极小体积下保留了出色的推理性能，下载量极高。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,070 | 2,057,103 | 针对 Qwen3.6 MoE 结构的激进去审查微调版，满足部分用户对自由输出内容的极端需求，社区争议与热度并存。 |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,455 | 1,906,539 | 融合 Claude 推理风格的 9B 量化模型，支持 1M 上下文窗口，适合需要超长文档分析与深度推理的场景。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 487 | 407,421 | 基于 Qwen3.6 的多重微调融合模型，去除内容限制并优化指令遵循，是追求极致个性化输出的高阶玩家首选。 |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF) | LuffyTheFox | 135 | 36,703 | 结合 Hermes 指令微调风格的 Qwen3.6 去审查版本，旨在提升模型在角色扮演与创意写作中的自由度。 |
| [unsloth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 171 | 57,536 | Unsloth 团队提供的 Laguna-S-2.1 GGUF 格式版本，优化了加载速度与内存占用，便于本地快速部署。 |
| [poolside/Laguna-S-2.1-GGUF](https://huggingface.co/poolside/Laguna-S-2.1-GGUF) | poolside | 133 | 62,092 | 官方发布的 Laguna-S-2.1 GGUF 量化包，兼容多种推理后端，为开发者提供标准化的轻量级部署方案。 |
| [poolside/Laguna-S-2.1-NVFP4](https://huggingface.co/poolside/Laguna-S-2.1-NVFP4) | poolside | 130 | 89,186 | 采用 NVIDIA FP4 量化技术的 Laguna-S-2.1 版本，专为支持 NVFP4 的硬件加速卡设计，实现极致推理效率。 |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,007 | 595,415 | Bonsai 的三元组量化版本，相比 1-bit 更平衡地保留精度，在 2-bit 量化市场中具有较高的性价比与口碑。 |
| [baseten/GLM-5.2-Vision-NVFP4](https://huggingface.co/baseten/GLM-5.2-Vision-NVFP4) | baseten | 90 | 494 | 百世智能推出的 GLM-5.2 视觉版 NVFP4 量化模型，针对云端大规模推理进行优化，降低 GPU 显存压力。 |
| [bottlecapai/ThinkingCap-Qwen3.6-27B](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B) | bottlecapai | 542 | 26,092 | 瓶盖 AI 对 Qwen3.6 进行的思维链增强微调，提升了模型在复杂逻辑推理任务中的步骤清晰度与准确性。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 543 | 1,106 | Upstage 发布的超大规模开源模型，尽管下载量因资源门槛较低，但其作为基准模型的价值不容忽视。 |

## 生态信号

当前生态中，**Qwen 3.6 系列**无疑是绝对的核心，其 MoE 架构（如 A3B）不仅吸引了官方发布，更引发了社区海量的去审查（Uncensored）与特定风格微调（如 GGUF 量化），显示出开发者对高能效比且可控模型的强烈偏好。**GLM-5.2** 与 **Gemma-4** 的竞争日益激烈，两者均在多模态与长上下文能力上大幅领先，下载量的爆发表明开源基座正在迅速替代部分闭源 API 的需求。量化方面，**NVFP4** 与 **1-bit/2-bit GGUF** 成为主流，反映出硬件加速与边缘部署需求的精细化。此外，**OCR 与机器人视觉**专用模型的增多，标志着 AI 正从通用聊天向垂直行业深度渗透。

## 值得探索

1. **[Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)**：MoE 架构的典范，仅需激活少量参数即可获得接近大参数模型的性能，是平衡成本与效果的首选，适合大多数生产环境。
2. **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)**：1-bit 量化技术的极致代表，在极低的显存占用下仍保持良好推理质量，非常适合在消费级显卡或边缘设备上运行大型模型。
3. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**：在处理复杂文档、长文本及多语言混合场景时表现优异，是构建文档自动化处理流水线不可或缺的工具。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*