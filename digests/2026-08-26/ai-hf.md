# Hugging Face 热门模型日报 2026-08-26

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-26 01:44 UTC

---



# Hugging Face 热门模型日报 — 2026-08-26

---

## 今日速览

今日榜单以 **Qwen3.8-27B** 系列绝对主导，官方原版斩获 12,716 点赞，社区随之涌现大量量化、Abliterated 及推理加速变体。与此同时，**DeepSeek V4** 系列与 **Kimi-K3** 两大语言模型阵营热度不减，合计瓜分近 1.5 亿下载量。多模态方向，**MiniMax-H3** 和 **LTX-2.5** 分别领跑视频生成赛道，音频与任何-to-任何模型亦有新兴力量入场。整体生态呈现"官方底座 + 社区微调"的两级爆发格局。

---

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 12,716 | 2,945,415 | Qwen 官方发布的 27B 基础多模态语言模型，支持图像-文本对话，是今日点赞榜首。社区围绕其衍生出大量微调与量化版本，成为本周生态核心底座。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,996 | 2,865,293 | Kimi 开源的多模态对话模型，采用压缩张量技术，兼顾性能与推理效率。下载量近 290 万，显示开发者对其实际应用的高度认可。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,716 | 3,528,373 | DeepSeek 面向推理效率优化的 Flash 版本，以较低延迟提供高质量的文本生成能力。近 350 万下载量位居榜单前列，是生产部署的热门选择。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 758 | 74,707 | DeepSeek V4 系列的专业版，面向高难度推理与复杂指令场景优化。虽下载量不及 Flash 版，但仍是追求极致性能用户的首选。 |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 419 | 70,158 | Ornith 推出的 35B 参数 MoE 模型（A3B 架构），兼顾大模型性能与推理成本。作为独立语言模型家族，其首次进入热门榜即引发关注。 |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 238 | 3,474 | 面向语音识别（ASR）的小型专用语言模型，基于 Qwen3 架构构建。体量小巧，适合端侧或低资源场景部署。 |

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,457 | 4,639,786 | MiniMax 发布的多模态视频生成模型，支持图像/文本到视频及视频续生成。近 460 万下载量，是当前视频生成赛道下载量最高的模型。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,800 | 833,845 | 业界知名影视工具厂商 Lightricks 推出的图像/视频生成扩散模型，支持多种视频生成模式。高质量生成能力使其在创作者群体中迅速走红。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,246 | 18,705 | MiniMax 的第三代音乐生成模型，支持文本到音乐创作，采用 Diffusers 生态便于集成。音频生成领域的强势新品，代表大厂在多模态赛道的全面布局。 |
| [sensenova/SenseNova-U1.5-8B-MoT](https://huggingface.co/sensenova/SenseNova-U1.5-8B-MoT) | sensenova | 153 | 2,682 | 商汤 SenseNova 平台的任意-to-任意多模态模型，原生支持多模态特性。体现国内大厂在多模态通用能力上的持续投入。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| 本周榜单中未见以代码、数学、医疗或嵌入任务为核心的独立专用模型。现有模型多为通用语言模型或多模态模型，尚未出现垂直领域专用模型的集中爆发。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,918 | 7,334,695 | Unsloth 针对 Qwen3.8-27B 优化的 GGUF 量化版本，下载量突破 730 万为全榜最高。结合 Unsloth 的高效推理加速，成为本地部署的首选方案。 |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 623 | 832,185 | 激进版无审查 Qwen3.8-27B GGUF 模型，引入多步预测（MTP）技术提升生成速度。83 万下载量印证社区对高性能无审查模型的旺盛需求。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,148 | 249,744 | 采用 FP8 量化的无审查 Qwen3.8-27B 变体，在显存占用与推理速度间取得良好平衡。FP8 量化路线在资源受限场景下受到青睐。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 722 | 1,525,645 | 社区贡献的 GGUF 格式无审查版本，152 万下载量表明其对 llama.cpp 生态用户极具吸引力。MTP 技术支持进一步提升推理效率。 |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 357 | 1,230,831 | 采用 Abliterated 技术移除审查的 GGUF 版本，123 万下载量反映该技术在开源社区的影响力。Abliterated 方法相比传统 uncensored 微调更加精确可控。 |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 751 | 389,747 | 支持 MLX、GGUF、safetensors 三种格式的 Abliterated 版本，跨平台兼容性极强。751 点赞与 39 万下载显示其在苹果生态用户中的受欢迎程度。 |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 277 | 735,183 | "异端"风格的 Abliterated 无审查 GGUF 模型，73.5 万下载量证明细分风格模型在特定用户群中的稳定需求。 |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,097 | 68,855 | 面向苹果 MLX 框架的无审查量化版本，专为 Mac 本地推理设计。MLX 格式在苹果生态中的持续流行推动此类适配需求。 |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 297 | 1,156,903 | Ornith 官方提供的 GGUF 量化版本，115 万下载量使其成为 MoE 模型量化部署的重要参考。MIT 许可确保商业友好性。 |
| [ornith-ai/Ornith-1.5-9B](https://huggingface.co/ornith-ai/Ornith-1.5-9B) | ornith-ai | 217 | 98,323 | Ornith 轻量级 9B 版本，适合资源受限但需要高质量生成能力的场景。作为 MoE 架构的小参数版本，展现灵活的规模策略。 |
| [ornith-ai/Ornith-1.5-9B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-9B-GGUF) | ornith-ai | 201 | 1,144,037 | Ornith 9B 的 GGUF 版本，114 万下载量远超参数量，证明量化社区对小型高效模型的强烈需求。 |
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 227 | 64,984 | 采用 DFlash2 推测解码技术的加速版本，显著降低自回归推理延迟。推测解码成为推理加速领域的新热点方向。 |
| [incoai/Qwen3.8-27B-DFlash2](https://huggingface.co/incoai/Qwen3.8-27B-DFlash2) | incoai | 179 | 105,786 | 另一版本的 DFlash2 推测解码模型，与 z-lab 版本形成互补竞争，共同推动推测解码技术的社区落地。 |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 240 | 221,918 | 融合 Cold-Fusion、GAIN 训练与 MTP 技术的综合优化版本，代表社区微调技术的复杂化与专业化趋势。 |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 452 | 154,225 | orcarouter 的 GGUF 格式无审查版本，覆盖更多 llama.cpp 用户群体。 |
| [orcarouter/Qwen3.8-27B-Uncensored](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored) | orcarouter | 183 | 15,341 | safetensors 格式的无审查原版微调，适合不需要 GGUF 量化的使用场景。 |
| [EschaLabs/Qwen3.8-27B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.8-27B-Escha-W2) | EschaLabs | 127 | 2,319 | 2-bit 极端量化版本，以极低比特数实现模型压缩，探索推理资源的极限压缩边界。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,468 | 0 | 修复版 Qwen Chat 模板，以 MLX Jinja 格式提供标准化对话格式。0 下载但 1,468 点赞说明其作为工具资源深受社区认可。 |
| [peculiar-ragdoll/Qwen-Sharp-Chat-Templates](https://huggingface.co/peculiar-ragdoll/Qwen-Sharp-Chat-Templates) | peculiar-ragdoll | 245 | 0 | 另一款 Qwen 对话模板修复工具，与 froggeric 版本形成竞争，反映模板标准化在部署环节的重要性日益凸显。 |

---

## 生态信号

本周生态呈现**三大趋势**：一是 **Qwen3.8-27B 家族绝对统治**，官方底座 + 社区微调形成完整生态链，Unsloth GGUF 版本下载量破 730 万独占鳌头；二是 **Abliterated/无审查模型持续活跃**，数十个变体涌入榜单，反映开发者对模型可控性的强烈需求；三是 **推理加速技术百花齐放**，DFlash2 推测解码、FP8 量化、2-bit 极端压缩并行探索，显示社区在降低部署成本上持续发力。DeepSeek V4 与 Kimi-K3 两大闭源转开源阵营稳居语言模型第二梯队，MiniMax 在多模态视频生成领域全面出击。整体来看，开源模型性能已与闭源接近，量化与微调成为社区竞争的核心战场。

---

## 值得探索

1. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — 全榜下载量最高的模型（730 万+），Unsloth 推理加速 + GGUF 格式的组合使其成为本地部署的最佳起点，性能与效率兼顾。

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成赛道的下载冠军（460 万+），支持多模式视频生成，代表多模态生成的前沿水平，适合创意与生产场景探索。

3. **[z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2)** — 推测解码技术的代表性作品，展示推理加速的最新进展，对于关注部署效率的开发者具有重要参考价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*