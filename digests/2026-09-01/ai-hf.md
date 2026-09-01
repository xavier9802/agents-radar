# Hugging Face 热门模型日报 2026-09-01

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-01 04:39 UTC

---



# Hugging Face 热门模型日报 — 2026-09-01

---

## 📋 今日速览

本日 HF 热门榜呈现 **"国产多模态模型集体爆发"** 态势：Qwen3.8 系列、GLM-5.3 系列、Kimi-K3、DeepSeek-V4 四大家族霸榜前十，形成第一梯队竞争格局。视频生成赛道热度持续攀升，MiniMax-H3 以 536 万次下载领先，LTX-2.5 紧随其后。社区量化活动极为活跃，unsloth 和 orcarouter 多个 GGUF/MLX 量化版本下载量突破百万，abliterated（去 RLHF 对齐）模型成为社区热门实验方向。

---

## 🏆 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,485 | 4,720,763 | 通义千问旗舰多模态模型，支持图像文本理解与对话；周点赞榜首，下载量近 500 万，是 Qwen3.8 系列的核心版本。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,119 | 2,792,274 | 月之暗面新一代多模态模型，采用压缩张量技术；点赞数极高，代表国产闭源模型开放权重的新趋势。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,843 | 4,561,861 | DeepSeek V4  Flash 版（2025-07-31 快照），专注文本生成与对话；下载量超 450 万，社区实用性强。 |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,294 | 9,059,937 | unsloth 对 Qwen3.8-27B 的 GGUF 量化版本，支持 llama.cpp 本地部署；下载量破 900 万，是量化模型中的标杆。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,820 | 379,271 | 智谱 GLM-5.3 Flash 多模态版本，支持图像文本到文本任务；38 万下载显示社区对国产多模态的持续青睐。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,423 | 66,195 | GLM-5.3 纯文本生成版本（MoeDSA 架构），作为 Flash 版的补充，支持更长上下文。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,330 | 307,496 | abliterated + FP8 量化的 Qwen3.8-27B，去除安全对齐以解锁完整能力；30 万下载反映社区对自由对话模型的强烈需求。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,250 | 114,057 | Apple Silicon 原生 MLX 格式，abliterated 版本，专为 Mac 用户优化推理体验。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,536 | 158,598 | Qwen3.8 系列的 Flash Next 版本，多模态对话能力进一步增强；是 Qwen 官方发布的最新迭代。 |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 374 | 0 | DeepSeek V4 Flash 视觉实验版，支持图像文本到文本任务；目前尚未开放下载，处于内部测试阶段。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 356 | 2,589 | 腾讯混元 Hy4 预览版，纯文本生成模型；代表腾讯在多模态大模型领域的持续布局。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 516 | 172,695 | 35B 参数、激活 3B 的 MoE 架构模型，支持文本生成与图像文本理解；高效 MoE 设计是其主要卖点。 |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 176 | 1,045 | 路透金融专用小模型，基于 Qwen3.5 MoE 架构；面向金融领域多模态理解任务。 |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 177 | 4,721 | 基于 Nemotron 架构的语音语言模型，面向实时语音对话场景；pipecat 实时语音管道的核心组件。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,711 | 5,362,365 | MiniMax 多模态视频生成模型，支持文本到视频与图像到视频；536 万下载领跑视频生成赛道。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,380 | 1,182,585 | Lightricks 开源视频生成模型，支持图像/视频到视频多模式生成；技术稳定，社区生态成熟。 |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 218 | 0 | 针对 MiniMax-H3 的 4 步快速推理加速版本，无需额外训练数据；目前未开放下载，处于预览阶段。 |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 168 | 27,009 | 针对 MiniMax-H3 的加速 LoRA 微调版本，优化视频生成推理速度；2.7 万下载显示社区对加速方案的需求。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 267 | 2,236 | Breeze 第二代文本到语音模型，支持高质量语音合成；轻量高效，适合嵌入式部署。 |
| [Kijai/MiniMax-H3-experimental](https://huggingface.co/Kijai/MiniMax-H3-experimental) | Kijai | 376 | 0 | MiniMax-H3 的实验性集成版本，面向 ComfyUI 等节点式工作流；目前未开放下载。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 166 | 105,974 | 35B 参数、激活 3B 的代码专用 MoE 模型，采用 imatrix 量化；10 万下载说明代码任务对轻量化模型的持续需求。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 639 | 373,029 | unsloth 对 Qwen3.8-Flash-Next 的 GGUF 量化版本，本地部署友好；37 万下载体现 Flash 模型的轻量化热度。 |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 313 | 53,350 | unsloth 对 GLM-5.3-Flash 的 GGUF 量化版本，支持 llama.cpp 高效推理；5.3 万下载显示智谱模型的社区适配活跃。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 977 | 759,644 | abliterated（去 RLHF 对齐）的 Qwen3.8-27B，支持 MLX、safetensors、GGUF 多格式；75 万下载反映社区对自由对话的持续探索。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 879 | 2,055,081 | uncensored 版本的 Qwen3.8-27B GGUF 量化，支持 MTP 多步预测；205 万下载是 uncensored 量化模型中的高下载代表。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 816 | 1,202,914 | 激进 MTP 优化的 uncensored GGUF 版本，追求更强推理速度；120 万下载体现性能优化的社区兴趣。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 607 | 246,445 | orcarouter 出品的 Qwen3.8-27B uncensored GGUF 版本，多格式兼容；24 万下载为 abliterated 社区的主流选择之一。 |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 152 | 51,125 | Flash Next 架构的 uncensored GGUF 版本，更轻量但保留完整能力；5 万下载显示 Flash 模型的二次开发热度。 |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 131 | 1,541 | GLM-5.3-Flash 的 uncensored FP8 量化版本；目前下载量较低，处于新兴探索阶段。 |
| [Qwen/Qwen3.8-Flash-Next-FP8](https://huggingface.co/Qwen/Qwen3.8-Flash-Next-FP8) | Qwen | 177 | 84,954 | Qwen 官方发布的 Flash Next FP8 量化版本，平衡精度与效率；8.5 万下载是官方量化方案的稳健选择。 |

---

## 📡 生态信号

**模型家族竞争加剧**：Qwen3.8、GLM-5.3、Kimi-K3、DeepSeek-V4 四大国产模型家族占据榜单核心位置，形成"旗舰开源 → 社区量化 → 二次微调"的完整生态链。Qwen3.8-27B 以 13,485 点赞和 472 万下载领跑，但社区量化版本（unsloth/Qwen3.8-27B-GGUF）下载量达 906 万，显示**量化模型的总使用量已超过原始权重**。

**去对齐（abliterated）模型进入主流视野**：orcarouter 和 OBLITERATUS 的 uncensored/abliterated 版本累计下载超过 500 万，表明用户对"无约束对话"的需求已从边缘走向规模化。这反映了当前 RLHF 对齐模型在创意、角色扮演等场景下的能力瓶颈正在推动社区寻求替代方案。

**视频生成赛道内卷加速**：MiniMax-H3 以 536 万下载遥遥领先，但 LTX-2.5、FastVideo 加速版、Alibaba PAI LoRA 加速版等多版本并存，说明视频生成模型的竞争已从"能不能生成"转向"生成速度有多快"。4 步推理的 FastH3 预览版虽未开放下载，但已引发关注。

**开源权重与闭源模型的博弈**：Kimi-K3 和 DeepSeek-V4 作为闭源厂商的开源权重，下载量均超 200 万，证明"开源权重 + 闭源 API"的双轨策略正在成为主流商业模式。这既促进了技术普及，也为厂商保留了云端部署的高价值客户群。

---

## 🔭 值得探索

1. **[Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next)** — Qwen 官方最新迭代，多模态能力显著提升，4,536 点赞证明社区认可度高；适合作为新项目的基础模型，尤其在图像理解 + 对话的联合任务上表现突出。

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成赛道的绝对霸主，536 万下载量远超同类；无论是文本到视频还是图像到视频都能胜任，且社区加速方案（FastVideo、LoRA）丰富，是视频生成应用的首选基座。

3. **[orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8)** — abliterated + FP8 量化，兼顾"自由对话"与"显存效率"；1,330 点赞和 30 万下载验证了社区需求。对于需要本地部署且不依赖 RLHF 对齐的创意应用场景，这是当前最值得尝试的版本之一。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*