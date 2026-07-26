# Hugging Face 热门模型日报 2026-07-26

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-26 03:35 UTC

---

# Hugging Face 热门模型日报 (2026-07-26)

## 今日速览
今日 HF 榜单呈现“多模态大模型”与“极致量化”双轮驱动态势。Qwen3.6 系列（特别是 35B-A3B MoE 架构）凭借极高的下载量和社区微调热度，成为绝对焦点；GLM-5.2 也展现出强劲的开源竞争力。同时，OCR 领域出现突破性进展，百度 Unlimited-OCR 以数百万次下载领跑，显示高效视觉理解需求的爆发。此外，社区对 GGUF 格式的偏好依然强烈，大量模型通过量化适配本地部署，体现了边缘计算与低成本推理的持续升温。

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,448 | 707,029 | 智谱最新一代 MoE 架构语言模型，性能强劲且推理效率高，是本周点赞最高的开源 LLM。其 conversational 标签表明在对话场景下表现优异，受到开发者广泛青睐。 |
| [Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B) | Qwen | 2,516 | 6,413,105 | 通义千问最新 MoE 架构旗舰模型，拥有惊人的下载量，显示其作为通用基座模型的极高普及度。结合 image-text-to-text 能力，它不仅是纯文本生成利器，也是多模态交互的核心组件。 |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 664 | 45,260 | Poolside 推出的高性能文本生成模型，专注于代码和长上下文处理。虽然基数较小，但其技术特性使其在特定垂直领域（如工程开发）中备受推崇。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 567 | 2,784 | Upstage 发布的超大参数开源模型，旨在挑战顶级闭源模型的性能。尽管下载量尚低，但 250B 的规模使其成为研究大规模 MoE 架构的重要样本。 |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,466 | 1,570,995 | 基于 Qwen3.5 微调的推理增强模型，支持 1M 超长上下文。其高下载量反映了用户对长文档分析和复杂逻辑推理能力的迫切需求。 |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 406 | 11,573 | 小型高效的语言模型，适合资源受限的边缘设备或特定轻量级任务。其存在证明了小参数模型在特定场景下的实用价值。 |
| [Motif-Technologies/Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 191 | 2,270 | Motif 系列的最新 Beta 版本，主打特征提取和通用文本理解。目前处于早期测试阶段，但已显示出在社区中的初步影响力。 |
| [fdtn-ai/antares-1b](https://huggingface.co/fdtn-ai/antares-1b) | fdtn-ai | 166 | 5,661 | 仅 1B 参数的超轻量模型，专注于安全性和效率。其 GranitMoEHybrid 架构使其在极小体积下保持不错的性能，适合嵌入式部署。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,110 | 2,564,264 | 百度发布的强大 OCR 模型，支持无限分辨率和高精度文本识别。其数百万次的下载量表明，高精度视觉信息提取是当前工业界最刚需的能力之一。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,094 | 1,988,680 | 基于 Qwen3.6 的无限制微调版本，专为去除安全护栏后的创意写作和角色扮演设计。高下载量反映了部分用户群体对自由生成内容的强烈需求。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,572 | 31,575 | Thinking Machines 推出的多模态对话模型，擅长图像与文本的深度交互。其 conversational 特性使其在智能助手和视觉问答场景中具有独特优势。 |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,277 | 749,449 | 月之暗面发布的代码专用多模态模型，结合压缩张量技术优化推理速度。它在代码生成和理解方面表现出色，是开发者工具箱中的重要补充。 |
| [microsoft/Fara1.5-27B](https://huggingface.co/microsoft/Fara1.5-27B) | microsoft | 93 | 1,039 | 微软推出的计算机使用（Computer Use）多模态模型，能够直接操作图形界面。虽然目前下载量不高，但其代表的“代理智能”方向极具前瞻性。 |
| [nvidia/Cosmos3-Edge](https://huggingface.co/nvidia/Cosmos3-Edge) | nvidia | 121 | 31,759 | NVIDIA Cosmos 系列的边缘端视频生成模型，旨在实现本地化的高保真视频创作。它标志着生成式 AI 从云端向边缘设备下沉的关键一步。 |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 88 | 47 | 超轻量级文本转语音模型，专为 CPU 和边缘 AI 设备优化。其极小的体积使其在无 GPU 环境下也能实现高质量的语音合成。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 175 | 607 | 面壁智能发布的机器人操作专用模型，具备视觉-语言-动作（VLA）能力。它展示了多模态模型在物理世界交互和机器人控制领域的最新进展。 |
| [openbmb/MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 128 | 379 | 另一款机器人相关模型，专注于目标跟踪与感知。与 Manip 模型形成互补，共同构建了 MiniCPM 在具身智能领域的完整解决方案。 |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 287 | 33,109 | 基于 Qwen3.5 优化的新一代 OCR 模型，在复杂排版和手写体识别上表现更佳。它是 Unlimited-OCR 的有力竞争者，提供了更多样化的选择。 |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 168 | 841 | 专为开发者设计的代码生成模型，基于 Qwen3.5 MoE 架构。其 V2.5 版本在代码质量和调试能力上进行了显著增强。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 638 | 2,114,963 | 27B 参数模型的极致量化版本，采用 1-bit 量化技术，大幅降低显存需求。其极高的下载量证明了社区对极致压缩和高效推理的强烈追求。 |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,029 | 611,685 | Bonsai 系列的三元组量化变体，平衡了模型性能与存储效率。相比 1-bit 版本，它在保持较低资源占用的同时提供了更好的精度。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 548 | 483,845 | 针对 Qwen3.6 进行的深度无限制微调，并转换为 GGUF 格式。其复杂的命名反映了社区对个性化、去约束化模型的精细化定制趋势。 |
| [unsloth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 187 | 71,893 | Unsloth 提供的 Laguna-S-2.1 的高效 GGUF 转换版本，利用其快速微调技术优化了推理速度。这体现了工具链厂商对主流模型的快速适配能力。 |
| [poolside/Laguna-S-2.1-GGUF](https://huggingface.co/poolside/Laguna-S-2.1-GGUF) | poolside | 143 | 76,957 | 官方提供的 Laguna-S-2.1 GGUF 版本，确保了格式兼容性和稳定性。对于希望在本机运行该模型的用户来说，这是首选方案。 |
| [poolside/Laguna-S-2.1-NVFP4](https://huggingface.co/poolside/Laguna-S-2.1-NVFP4) | poolside | 135 | 117,106 | 采用 NVIDIA FP4 量化技术的版本，专为支持该格式的硬件（如 Blackwell 架构）优化。这代表了下一代高精度低比特量化的前沿探索。 |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF) | LuffyTheFox | 153 | 60,643 | 基于 Hermes 风格微调的无限制 Qwen3.6 版本，采用 GGUF 格式。它满足了喜欢自由对话且不介意移除安全过滤器的用户需求。 |
| [conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit) | conradlocke | 539 | 0 | 针对 Krea-2 模型的 Identity 编辑 LoRA，用于保持人物身份一致性的图像编辑。虽然下载量为 0，但其点赞数表明其在创意工作流中具有潜在的高价值。 |

## 生态信号
当前生态呈现出**“大小通吃、量化为王”**的特征。一方面，Qwen3.6 和 GLM-5.2 等中型至大型 MoE 模型通过开源迅速占领市场，显示出开源模型在性能上已能匹敌甚至超越部分闭源产品。另一方面，GGUF 和 NVFP4 等量化格式的流行，表明用户越来越关注**推理成本与硬件兼容性**。社区微调（Uncensored, Hermes 等）活跃，反映出用户对模型可控性和特定风格的高度定制化需求。此外，OCR 和机器人（Robotics）任务的崛起，标志着多模态 AI 正从单纯的“聊天”向“感知与行动”深化。

## 值得探索
1. **[Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)**：作为本周下载量最高的模型，其 35B 参数、A3B 激活的高效 MoE 架构代表了当前平衡性能与成本的黄金标准，值得深入研究其训练数据和微调潜力。
2. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**：在文档数字化和信息抽取领域具有极高的实用价值，其 Unlimited 能力暗示了对高分辨率和复杂布局的强大处理力，是构建企业级知识图谱的理想基础。
3. **[openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip)**：代表了 VLA（Vision-Language-Action）模型的前沿，对于从事具身智能和机器人控制的开发者而言，这是一个极具参考价值的开源基准模型。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*