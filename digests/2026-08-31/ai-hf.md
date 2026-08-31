# Hugging Face 热门模型日报 2026-08-31

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-31 04:59 UTC

---



# Hugging Face 热门模型日报
**日期：2026-08-31**

---

## 📋 今日速览

今日 HF 热门榜单呈现多模态模型全面开花的态势，Qwen3.8 系列和 GLM-5.3 家族双雄并立，DeepSeek-V4-Flash 以近 500 万下载量领跑语言模型赛道。视频生成领域 MiniMax-H3 生态持续爆发，配套 ControlNet 与 LoRA 微调资源同步涌入。社区量化与去审查（abliterated）微调活动异常活跃，GGUF 与 MLX 格式成为本地部署首选。

---

## 🔥 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | ---: | ---: | :--- | :--- |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,404 | 121,976 | 官方 Flash 轻量版多模态模型，qwen4_exp 架构支持图文对话，周增 4,400+ 赞，成为当日最热新发布模型。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,826 | 4,575,518 | 纯文本生成旗舰，累计下载超 450 万，代表 DeepSeek V4 系列在推理效率与代码能力上的持续领先。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,732 | 346,516 | GLM-5.3 快速版，支持图文输入，glm5_next 架构，下载量超 34 万，成为国产开源多模态阵营重要力量。 |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,359 | 50,116 | GLM-5.3 标准版，glm_moe_dsa 稀疏专家架构，兼顾性能与资源效率，适合生产部署。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,106 | 2,794,721 | Kimi K3 多模态对话模型，kimi_k3 架构配合 compressed-tensors 压缩技术，累计下载近 280 万，社区热度极高。 |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 323 | 2,123 | 腾讯 Hunyuan 家族 V4 预览版，hy_v4 架构刚上线，下载量尚低但潜力值得关注。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 507 | 147,038 | 35B 参数 MoE 模型，qwen3_5_moe 架构支持图文，专精文本生成任务，社区下载活跃。 |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 158 | 1,009 |  Thomson Reuters 法律/金融领域专用小模型，qwen3_5_moe 架构，虽下载量低但专业定位明确。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | ---: | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,665 | 5,263,381 | MiniMax 最强图文视频生成模型，累计下载超 520 万，是当日视频生成领域绝对霸主，支持文本/图像到视频全流程。 |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,364 | 4,511,348 | Qwen3.8 旗舰多模态模型，qwen3_5 架构，下载量近 450 万，是当日点赞最高模型，代表开源多模态最强战力之一。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,281 | 1,137,181 | 专业视频生成模型，支持图像/文本/视频多种输入模式，diffusion-single-file 单文件部署，下载量超 110 万，影视创作场景热门。 |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 197 | 0 | 基于 MiniMax-H3 的极速推理加速版本，仅需 4 步采样，无训练数据依赖，技术路线值得关注。 |
| [alibaba-pai/MiniMax-H3-Fun-Controlnet-Union](https://huggingface.co/alibaba-pai/MiniMax-H3-Fun-Controlnet-Union) | alibaba-pai | 163 | 5,538 | MiniMax-H3 配套 ControlNet，支持视频到视频与图文控制生成，alibaba-pai 团队发布，为精细化视频创作提供工具。 |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 154 | 23,734 | MiniMax-H3 加速 LoRA 微调包，基于 arxiv:2607.26004 论文，帮助开发者高效定制视频生成风格。 |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 215 | 1,838 | 新一代文本转语音模型，breeze 架构，支持高质量语音合成，适合对话系统与音频内容创作。 |

### 🔧 专用模型

本期榜单中未见明确标注为代码、数学或医疗专用的独立模型；部分模型（如 Thomson-1.0-Small）虽面向专业领域，但尚未形成独立分类热度。

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | ---: | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,251 | 8,839,153 | 社区最热门量化版本，GGUF 格式配合 unsloth 优化，下载量突破 880 万，是本地部署 Qwen3.8-27B 的首选方案。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,290 | 301,964 | FP8 高精度量化无审查版本，safetensors 格式，abliterated 技术移除安全限制，适合研究用途。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,236 | 109,121 | Apple Silicon 原生 MLX 格式无审查版本，完美适配 Mac 本地推理，abliterated + MLX 双特性叠加。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 952 | 725,757 | 多格式无审查模型（mlx/gguf/safetensors），abliterated 技术移除 RLHF 安全层，跨平台兼容性强。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 791 | 1,158,065 | Aggressive MTP（Multi-Token Prediction）训练版本，无审查 GGUF 格式，下载量超 115 万，推理速度显著优化。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 856 | 1,991,437 | GGUF 格式无审查版本，配合 llama.cpp 推理框架，下载量近 200 万，是本地无限制对话的热门选择。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 459 | 1,622,056 | abliterated + GGUF 双格式支持，下载量超 160 万，社区对无限制模型的需求持续旺盛。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 607 | 328,195 | Flash 轻量版的 GGUF 量化，针对资源受限环境优化，配合 unsloth 推理加速框架部署友好。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 586 | 238,397 | orcarouter 出品的无审查 GGUF 版本，abliterated 技术+qwen3.8 架构，社区下载稳健。 |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 292 | 45,936 | GLM-5.3 Flash 版 GGUF 量化，glm5_next 架构，填补国产多模态模型本地量化生态空白。 |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 145 | 87,848 | 代码专用 MoE 量化模型，qwen35moe 架构配合 imatrix 训练，35B 参数 A3B 设计专注编程任务。 |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 125 | 42,864 | Flash-Next 轻量无审查版本，GGUF 格式，适合低资源场景下的自由对话需求。 |

---

## 📊 生态信号

当前 Hugging Face 模型生态呈现"旗舰模型家族化、部署格式碎片化、社区二次创作活跃化"三大特征。Qwen3.8、GLM-5.3、MiniMax-H3 三条模型家族各自形成从官方权重到量化、从基础版到微调的完整产品矩阵，竞争格局清晰。**开源权重**仍是绝对主流，DeepSeek-V4-Flash、Kimi-K3 等闭源模型通过官方开源其核心权重参与竞争，反映出"以开源换生态"的行业共识。量化与微调领域，**abliterated（去审查）模型**下载量异常突出，多版本累计下载超 600 万，表明本地部署用户对无限制模型的强烈需求。GGUF 和 MLX 成为双寡头格式，unsloth 团队凭借优化推理能力稳居量化榜首。视频生成赛道 MiniMax-H3 生态尤为活跃，ControlNet、LoRA、加速推理等周边资源同步爆发，显示多模态生成正从单模型竞争走向生态竞争。

---

## 🌟 值得探索

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成领域现象级模型，下载量超 520 万，配合阿里 pai 团队的 ControlNet 和 LoRA 微调资源，是探索图文视频生成的最佳入口。

2. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — Kimi 最新多模态模型，11,106 点赞领跑全场，compressed-tensors 压缩技术使其在保持高性能的同时大幅降低部署门槛，适合研究开源多模态最新架构。

3. **[HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF)** — 创新性地结合 MTP（Multi-Token Prediction）加速推理与 abliterated 去审查技术，下载量超 115 万，代表社区在性能与自由度之间的前沿探索。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*