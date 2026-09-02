# Hugging Face 热门模型日报 2026-09-02

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-09-02 04:01 UTC

---



# Hugging Face 热门模型日报 — 2026-09-02

---

## 一、今日速览

2026年9月初的HF热门榜被**Qwen3.8家族**与**GLM-5.x系列**强势主导，Qwen/Qwen3.8-27B 以13,595赞登顶全榜；**Kimi-K3** 以11,130赞紧随其后，显示国产多模态大模型的持续统治力。视频生成领域**MiniMax-H3**下载量突破550万，成为社区最活跃的生成模型。同时，社区量化微调活动异常活跃——GGUF、FP8、MLX、MLX消融版等各类变体占据榜单近半席位。

---

## 二、热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,657 | 207,941 | Qwen3.8系列的Flash版，支持图文对话，周赞破4,600位居当日榜单第一。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,894 | 441,348 | GLM-5.3系列的Flash量化版，支持图文对话，下载量超过44万，社区使用活跃。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,472 | 94,403 | GLM-5.3标准版，MoE架构（glm_moe_dsa标签），支持纯文本生成与对话。 |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,595 | 4,960,483 | Qwen3.8系列旗舰27B模型，13,595赞登顶全榜，下载近500万，是当前社区最热门的开源多模态LLM。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 386 | 3,516 | 腾讯Hunyuan V4预览版，纯文本生成模型，MoE架构，代表国产厂商持续布局开源生态。 |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 458 | 17,893 | DeepSeek V4 Flash视觉实验版，支持图文生成，为DeepSeek V4系列开源计划的一部分。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,130 | 2,783,061 | Kimi K3图文多模态模型，11,130赞仅次于Qwen3.8-27B，下载超278万，是长上下文能力的代表产品。 |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 181 | 1,130 | 路透社首个开源多模态模型（Small版），MoE架构，面向金融垂直领域的开源尝试。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,759 | 5,532,597 | MiniMax视频生成旗舰模型，支持文生视频和图生视频，下载超550万，是当日生成领域最活跃模型。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,473 | 1,232,274 | LTX-2.5视频生成模型，单文件扩散架构，支持文生/图生/视频生成，下载超120万。 |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 238 | 0 | 基于FastVideo框架的快速视频生成预览版，4步推理、无需额外训练数据，面向高效视频生成研究。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 314 | 3,086 | 第二代自然语音合成模型，支持高质量文本转语音，社区用户正在探索对话场景应用。 |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 186 | 6,813 | Pipecat团队的语音语言模型Alpha版，面向实时语音交互场景，结合nemotron架构。 |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 178 | 32,893 | 针对MiniMax-H3的加速LoRA适配器，可显著降低推理延迟，适合生产环境部署。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 226 | 0 | Google TimeFM 3.0时间序列预测模型，面向金融、能源等领域的专业预测任务。 |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 184 | 130,086 | 35B参数量的代码专用MoE模型（A3B激活），GGUF量化版本，专为编程任务优化。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 676 | 431,339 | 基于Qwen3.8-Flash-Next的GGUF量化版本，由unsloth封装，适合本地高效推理。 |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,344 | 9,354,057 | Qwen3.8-27B的GGUF量化版，下载量超935万，是全榜下载量最高的模型。 |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 327 | 63,718 | GLM-5.3-Flash的GGUF量化版，支持本地化部署和高效推理。 |
| [Qwen/Qwen3.8-Flash-Next-FP8](https://huggingface.co/Qwen/Qwen3.8-Flash-Next-FP8) | Qwen | 180 | 130,451 | Qwen3.8-Flash-Next的官方FP8量化版本，兼顾性能与显存效率。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,006 | 805,791 | 对Qwen3.8-27B进行abliterated处理的版本，去除部分安全对齐，下载超80万。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 842 | 1,276,092 | 激进取消安全对齐的Qwen3.8-27B GGUF版本，使用MTP多步预测技术，下载超127万。 |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 170 | 64,325 | orcarouter制作的Flash-Next取消对齐GGUF版本，面向特定研究场景。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 635 | 254,529 | Qwen3.8-27B取消对齐GGUF版，下载超25万，社区需求持续。 |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 144 | 2,576 | GLM-5.3-Flash的FP8取消对齐版本，提供低精度+无限制的双特性组合。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,352 | 316,128 | Qwen3.8-27B取消对齐FP8版，点赞1,352、下载超31万，是FP8+uncensored最受欢迎的组合之一。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,261 | 121,028 | 针对Apple Silicon优化的MLX格式取消对齐版本，适合Mac本地运行。 |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 127 | 56,208 | 采用GSQ+RCO混合精度量化技术的实验性GGUF版本，探索更低比特下的性能保持。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 893 | 2,143,289 | Qwen3.8-27B取消对齐GGUF版，使用llama.cpp推理，下载超214万，是该变体中下载量最高。 |
| [Kijai/MiniMax-H3-experimental](https://huggingface.co/Kijai/MiniMax-H3-experimental) | Kijai | 390 | 0 | 针对MiniMax-H3的实验性社区版本，面向视频生成加速研究。 |

---

## 三、生态信号

**模型家族方面**，Qwen3.8与GLM-5.x是绝对主力，其中Qwen3.8-27B以13,595赞稳居榜首，其GGUF/FP8/MLX等量化变体占据榜单近半，显示社区对本地化部署的强烈需求。GLM-5.3系列紧随其后，zai-org的持续开源策略获得市场认可。

**开源 vs 闭源**，今日榜单几乎全部为开源或预览权重，DeepSeek、Kimi、腾讯等厂商均在积极开源，闭源模型未出现在热门榜中，反映出社区对可复现、可微调权重的偏好。

**量化与微调**活动异常活跃：orcarouter、JonathanColetti、HauhauCS等社区作者在"uncensored/abliterated"方向持续产出，反映用户对无限制基座模型的旺盛需求；unsloth的GGUF封装下载量最高（超935万），证明本地推理生态成熟。

---

## 四、值得探索

1. **[Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B)** — 全榜点赞最高（13,595）、下载近500万的旗舰多模态模型，图文理解能力强大，适合研究先进多模态对齐技术或作为基座进行二次微调。

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成领域下载量最高（超550万）的模型，支持文生视频和图生视频，结合alibaba-pai提供的加速LoRA，适合探索高效视频生成工作流。

3. **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — Google TimeFM 3.0时间序列预测模型，虽然下载量较低但代表专业领域开源化的趋势，适合金融、能源预测等垂直场景尝试。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*