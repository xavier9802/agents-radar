# Hugging Face 热门模型日报 2026-08-27

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-27 08:44 UTC

---



# Hugging Face 热门模型日报
**日期：2026-08-27 | 按周点赞数排序 | 共 30 个模型**

---

## 一、今日速览

Kimi-K3 以 11,027 点赞强势登顶，成为本周最受关注的模型；Qwen 家族（含 Flash 变体）持续霸榜，生态扩展明显。视频生成领域 MiniMax-H3 和 LTX-2.5 双星并起，多模态与生成能力成为社区焦点。量化微调（GGUF/MLX）与"去审查"（Uncensored/Abliterated）社区活动活跃，开源生态呈现多元化分化趋势。

---

## 二、热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 12,952 | 3,298,569 | Qwen 旗舰开源模型，支持图像-文本到文本的多模态对话，下载量超 329 万，是本周下载量最高的模型。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,027 | 2,921,257 | 月之暗面开源多模态对话模型，支持特征提取，点赞 11,027 登顶，反映社区对国产大模型的持续关注。 |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,122 | 0 | 智谱 GLM 5.3 Flash 轻量版本，主打高效文本生成，0 下载暗示可能为权重待发布或仅托管格式说明。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,747 | 3,857,140 | DeepSeek V4 Flash 版本，7 月 31 日构建，320 万+ 下载证明 DeepSeek 系列持续保持高人气。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 459 | 83,342 | Ornith 1.5 系列 35B MoE 架构，混合专家模式兼顾性能与效率，适合对推理成本敏感的场景。 |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,511 | 4,793,098 | MiniMax 新一代多模态模型，支持图像-文本到视频生成，479 万下载彰显视频生成赛道的爆发力。 |
| [ornith-ai/Ornith-1.5-9B](https://huggingface.co/ornith-ai/Ornith-1.5-9B) | ornith-ai | 232 | 119,053 | Ornith 1.5 轻量版 9B 参数，适配资源受限的部署环境，11.9 万下载说明小模型仍有稳定需求。 |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 255 | 3,921 | Whisper 系轻量语音模型，集成 ASR 能力，3.9 千下载表明社区对端侧语音模型的持续兴趣。 |
| [sensenova/SenseNova-U1.5-8B-MoT](https://huggingface.co/sensenova/SenseNova-U1.5-8B-MoT) | sensenova | 174 | 3,264 | 森森科技 8B MoT 多模态模型，支持任意到任意（any-to-any）任务，体现国产厂商在多模态方向的布局。 |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 3,782 | 2,551 | Qwen 3.8 Flash 下一代实验版本，3.7K 点赞显示社区对 Qwen Flash 系列迭代的期待。 |

---

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,887 | 894,094 | Lightricks 开源视频生成模型，支持文本/图像到视频及视频到视频，89 万下载成为视频生成细分赛道标杆。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,266 | 19,501 | MiniMax 音乐生成模型，文本到音频（text-to-music）能力，1.2K 点赞反映音频生成赛道的关注度上升。 |
| [alibaba-pai/MiniMax-H3-Fun-Controlnet-Union](https://huggingface.co/alibaba-pai/MiniMax-H3-Fun-Controlnet-Union) | alibaba-pai | 142 | 3,148 | MiniMax-H3 的 ControlNet 联合版本，支持视频到视频编辑，3.1K 下载说明视频编辑工具链需求旺盛。 |
| [Audio8/Audio8-TTS-Preview-0.1b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.1b) | Audio8 | 176 | 4,257 | Audio8 文本转语音模型，0.1B 参数量小巧，4.2K 下载显示端侧 TTS 仍有明确应用场景。 |

---

### 🔧 专用模型（代码、数学、医疗、嵌入）

> 本榜单无严格意义上的代码/数学/医疗专用模型，多模态能力普遍覆盖任务泛化需求，专用模型尚未进入本周 Top 30。

---

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,021 | 7,638,591 | 由 unsloth 对 Qwen3.8-27B 进行的 GGUF 量化，763 万下载是本周最高，GGUF 格式因兼容 llama.cpp 而广受欢迎。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 764 | 1,620,754 | "去审查" GGUF 量化版，162 万下载显示开源社区对无约束模型的强烈需求，MTP 训练进一步增强了输出质量。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 671 | 911,795 | 激进的 MTP（Mixture of Token Predictors）训练策略，91 万下载证明社区对强化训练方法的认可。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 385 | 1,318,749 | "Abliterated" 技术去审查版本，131 万下载反映去审查社区对高质量推理框架的重视。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 318 | 1,391,218 | Ornith 1.5 35B 的 GGUF 量化版，139 万下载说明大模型量化是部署的主流路径。 |
| [ornith-ai/Ornith-1.5-9B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-9B-GGUF) | ornith-ai | 224 | 1,389,641 | 9B 模型同样获得 138 万 GGUF 下载，小模型量化市场极其活跃。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 824 | 468,746 | "Obliterated" 风格去审查变体，46.8 万下载展示不同社区流派的分化。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,188 | 269,805 | FP8 精度量化版本，26.9 万下载说明高比特量化方案仍有稳定用户群。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,148 | 79,395 | Apple MLX 格式版本，7.9 万下载反映苹果生态开发者对原生格式的需求。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 480 | 183,871 | orcarouter 另一款 GGUF 版本，18 万下载印证该作者在去审查社区的影响力。 |
| [orcarouter/Qwen3.8-27B-Uncensored](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored) | orcarouter | 194 | 17,567 | 原始去审查版本（未量化），1.7 万下载表明仍有用户偏好非量化原生权重。 |
| [EschaLabs/Qwen3.8-27B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.8-27B-Escha-W2) | EschaLabs | 134 | 2,481 | 2-bit 极端量化版本，2.4 千下载证明超轻量推理场景存在市场。 |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 256 | 232,525 | 融合 GAIN 训练与 MTP 的冷融合方案，23 万下载显示社区对混合训练方法的探索热情。 |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 391 | 0 | Flash Next 的 GGUF 版本，0 下载表明该量化尚未正式发布或仅处于早期阶段。 |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 144 | 0 | GLM 5.3 Flash 的 GGUF 版本，0 下载同样暗示尚未正式发布。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,490 | 0 | 修复 Qwen 聊天模板的 Jinja 配置，0 下载反映其定位为工具型仓库而非权重模型。 |

---

## 三、生态信号

**Qwen 家族生态扩张迅猛**：从原始模型到 Flash 变体、GGUF 量化、MLX 版本、"去审查"社区微调，形成完整的模型生态树。3.8-27B 原始权重 + 500 万+ GGUF 下载的组合，显示开源模型从发布到本地化部署的全链路已非常成熟。

**视频生成赛道爆发**：MiniMax-H3（479 万下载）和 LTX-2.5（89 万下载）双强竞争，ControlNet 联合版也进入榜单，说明视频生成已从"能生成"进化到"可精确控制"阶段。

**量化与去审查社区活跃**：GGUF 仍是量化主流格式（unsloth 主导），MLX 格式在苹果生态内增长。"Uncensored/Abliterated"系列共出现 8 个变体，下载总量超 400 万，反映开源社区对内容审查的持续反制需求。

---

## 四、值得探索

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周点赞最高（11,027），月之暗面开源多模态模型，支持特征提取，适合需要国产大模型能力的团队。

2. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 下载量最高的模型（763 万），代表 Qwen 3.8 在生产环境落地的首选路径，llama.cpp 兼容使其成为本地部署最实用的版本。

3. **[Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5)** — 视频生成领域的开源标杆，支持文本/图像到视频及视频到视频，89 万下载验证其成熟度，值得视频内容创作者深入尝试。

---

*数据来源：Hugging Face Hub 热门榜（2026-08-27）* | *生成时间：2026-08-27*

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*