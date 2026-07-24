# Hugging Face 热门模型日报 2026-07-24

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-24 03:22 UTC

---

# Hugging Face 热门模型日报 (2026-07-24)

## 今日速览
今日 HF 榜单呈现出“多模态大模型全面普及”与“极致量化本地部署”并行的趋势。Zai-org 的 GLM-5.2 以极高的下载量和点赞数领跑，显示出中文语境下新一代 MoE 架构的强大吸引力；同时，Google 的 Gemma-4 系列凭借巨大的下载基数确立了其在开源多模态领域的基石地位。社区在 Qwen3.6 及 Laguna 系列上的微调与 GGUF 量化活动异常活跃，特别是针对推理增强和特定领域（如 OCR、机器人）的垂直优化，反映了开发者对高效能本地化部署的强烈需求。此外，Nvidia 和 Moonshot 等大厂在语音和代码领域的专用模型也保持了较高的关注度。

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,377 | 596,442 | 基于 MoE 架构的新一代对话模型，支持长上下文与复杂推理，本周下载量激增，显示其在开源社区的高活跃度。其高效的 DSA 机制使其在保持性能的同时降低了部署门槛。 |
| [google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,348 | 12,666,488 | Google 最新一代 Gemma 系列的指令微调版本，拥有超过千万的累计下载量，是构建多模态应用的基础底座。其出色的通用对话能力和低延迟特性使其成为工业界首选。 |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 468 | 362 | Upstage 发布的超大参数开源模型，旨在挑战顶级闭源模型的性能上限。虽然目前下载量尚低，但其 250B 的规模预示着在复杂逻辑推理任务上的巨大潜力。 |
| [Motif-Technologies/Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 174 | 1,856 | Motif 系列的第三个 Beta 版本，专注于提升特征提取和多语言理解能力。作为新兴模型家族，其早期采用者反馈积极，适合需要高精度语义嵌入的场景。 |
| [fdtn-ai/antares-1b](https://huggingface.co/fdtn-ai/antares-1b) | fdtn-ai | 122 | 2,747 | 一款轻量级的安全导向语言模型，采用 Hybrid MoE 架构，旨在在小参数下实现高安全性过滤。适合资源受限且对内容合规性要求极高的边缘设备部署。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 2,901 | 2,414,259 | 百度推出的全能型 OCR 模型，支持无限分辨率图像的文字识别，下载量已突破 240 万。其在复杂版面分析和多语言场景下的表现使其成为文档数字化任务的首选。 |
| [Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice) | Qwen | 1,800 | 2,497,020 | 通义千问系列的文本转语音模型，支持自定义声音克隆，累计下载近 250 万。其 12Hz 的高效采样率在保证音质的同时大幅降低了推理成本，适合实时语音交互应用。 |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,440 | 2,126,755 | 经过深度对齐的多模态模型，支持 1M 上下文窗口和复杂的视觉推理任务。其 GGUF 格式便于本地部署，且在代码和数学推理方面表现出接近顶级闭源模型的能力。 |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,036 | 2,027,080 | 基于 Qwen3.6 的无限制多模态微调版本，专注于去除安全护栏后的创意生成和角色扮演。高达 200 万的下载量反映了社区对高自由度内容生成工具的持续需求。 |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 190 | 411 | 微软推出的新型文生图模型，强调流畅的动态图像生成能力。虽然处于早期阶段，但其 Diffusers 兼容性使其易于集成到现有的图像编辑工作流中。 |
| [nvidia/Cosmos3-Edge](https://huggingface.co/nvidia/Cosmos3-Edge) | nvidia | 103 | 28,493 | Nvidia Cosmos 系列的边缘端视频生成模型，专为低功耗设备优化。它使得在本地硬件上进行高质量视频内容创作成为可能，推动了 AIGC 向边缘计算下沉。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,249 | 766,522 | 月之暗面发布的专用代码大模型，经过压缩张量优化，推理效率显著提升。其在复杂代码生成和调试任务上的表现优异，深受开发者喜爱。 |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 165 | 408 | 面向机器人操作任务的视觉-语言-动作模型，支持精细的物体操控指令解析。作为 MiniCPM 家族在具身智能领域的延伸，它为低成本机器人提供了强大的大脑。 |
| [openbmb/MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 117 | 306 | 专注于机器人视觉跟踪的任务模型，能够实时处理多模态输入以指导机械臂运动。它与 Manip 模型互补，共同构建了完整的机器人感知与控制闭环。 |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 257 | 26,919 | 第二代 Ovis OCR 模型，基于 Qwen3.5 架构，显著提升了公式和图表的识别准确率。其在结构化数据提取方面的改进使其成为金融和法律文档处理的有力工具。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 621 | 1,910,116 | Bonsai 系列的 27B 参数 GGUF 量化版本，支持 1-bit 极端量化，极大降低了显存需求。近 200 万的下载量证明了对超轻量级本地大模型的强劲市场需求。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 407 | 334,847 | 基于 Qwen3.6 的深度微调版本，融合了多种社区指令集并进行去敏感化处理。其独特的 Fable Fusion 策略在创意写作和无约束对话场景中表现突出。 |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,509 | 24,669 | 一种新颖的多模态对齐技术，专注于图像与文本的深度语义关联。虽然下载量相对较小，但其高点赞率表明社区对其创新架构的高度认可。 |
| [unsloth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 151 | 28,542 | Unsloth 提供的 Laguna 模型快速量化版本，利用其特有的加速库优化了推理速度。适合需要在消费级 GPU 上运行高性能文本生成模型的用户。 |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF) | LuffyTheFox | 118 | 24,982 | 结合 Hermes V5 指令集的 Qwen3.6 35B 量化模型，增强了逻辑推理和代码生成能力。其 GGUF 格式确保了广泛的硬件兼容性，便于本地实验。 |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 986 | 576,083 | Bonsai 的三元量化版本，平衡了模型精度与文件大小，下载量接近 60 万。对于需要在内存受限设备上部署较大参数模型的用户而言，这是一个极佳的折中选择。 |

## 生态信号
本周生态最显著的趋势是**Qwen 系列及其衍生模型**的统治力，从官方基础模型到社区大量的 Uncensored 和 GGUF 微调版本，形成了庞大的生态矩阵。同时，**多模态能力已成为标配**，即使是纯文本模型（如 GLM-5.2）也往往具备强大的图文交互潜力。在量化领域，**1-bit 和 Ternary 量化**开始进入主流视野，Prism-ML 和 Unsloth 等团队推动了极小体积模型的发展，使得 27B+ 参数模型在普通硬件上运行成为现实。此外，**具身智能（Robotics）** 成为新的增长点，MiniCPM 系列在机器人控制和跟踪上的专用模型展示了多模态大模型向物理世界延伸的巨大潜力。

## 值得探索
1. **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**：作为本周下载和点赞双料冠军，GLM-5.2 代表了当前开源中文大模型的最高水平之一。其 MoE 架构和对话能力使其成为构建智能助手的首选基座，值得深入评估其在实际业务场景中的表现。
2. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**：对于任何涉及文档处理的应用，这款模型都极具价值。其“无限”分辨率的处理能力和极高的下载量证明了其在工业界的广泛适用性，是优化 OCR 流程的关键组件。
3. **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)**：如果你需要在资源有限的设备上运行大型语言模型，这个 1-bit 量化版本提供了惊人的性价比。它展示了极端量化技术如何在保持可用性的前提下大幅降低部署门槛，是研究高效推理的绝佳案例。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*