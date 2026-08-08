# Hugging Face 热门模型日报 2026-08-08

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-08 02:02 UTC

---

# Hugging Face 热门模型日报 — 2026-08-08

---

## 今日速览

MiniMax-H3 视频生成模型霸榜，相关模型与社区微调占据半壁江山，显示视频生成赛道热度空前。DeepSeek-V4-Flash 与 Kimi-K3 两大国产 LLM 持续收割关注，后者以超 10,000 点赞位列前三。量化社区活动活跃，GGUF 版本模型下载量动辄数十万。多模态与大模型融合是本周明显趋势。

---

## 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,748 | 702,709 | DeepSeek 新一代 Flash 推理模型，对话与长上下文能力出众。70万+下载验证其开发者生态影响力。 |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,284 | 1,308,186 | 月之暗面最新多模态语言模型，支持图文理解，点赞破万领跑本周榜单。下载量超130万，社区采用迅速。 |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,889 | 2,430,330 | 智谱 GLM 系列 MoE 架构语言模型，推理效率与质量兼顾。240万+下载，国产大模型持续放量。 |
| [Baidu Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,954 | 2,836,694 | 百度开源高精度 OCR 模型，支持多语言与复杂场景文字识别。280万+下载，实用型模型典型代表。 |
| [LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 380 | 77,973 | LiquidAI 推出的小型高效语言模型，适合边缘部署。轻量架构兼顾性能，开发者关注度高。 |
| [Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 336 | 25,340 | 思考机器公司开源的多模态对话模型，专注高效交互。小而精的设计吸引研究社区。 |
| [Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 302 | 456,140 | 微软发布的视觉语言模型，融合多模态理解能力。45万+下载，微软在开源多模态领域持续布局。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 2,959 | 18,112 | MiniMax 旗舰图文转视频模型，支持 image-text-to-video。虽下载量不高但热度极高，社区衍生模型众多。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 938 | 3,139,920 | MiniMax-H3 的 ComfyUI 集成版本，支持单次推理。310万+下载反映 ComfyUI 工作流生态强劲。 |
| [Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 307 | 12,633 | 轻量级文本转语音模型，0.6B 参数适合快速部署。TTS 领域开源竞争日趋激烈。 |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 532 | 17,399 | 面向代码生成的多模态模型，支持图文辅助编码。代码 AI 赛道持续升温。 |
| [NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 228 | 359 | 英伟达语音对话模型，支持自然语音交互。尽管下载量低但代表了大厂在语音交互领域的投入。 |

### 🔧 专用模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 184 | 2,480 | Mistral 推出的安全防御模型，用于内容审核与风险提示。3B 轻量参数适合嵌入生产管线。 |
| [maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 228 | 686 | 深度 Grove 的 MoE 架构预览版模型，实验性质强。预览版即获关注，值得关注后续发布。 |
| [Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 203 | 3,065 | InclusionAI 的高效对话模型，强调包容性与多语言支持。3000+下载反映小众但精准的社区需求。 |

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,709 | 2,217,339 | Qwen3.6 的 GGUF 量化微调版本，去除了内容限制。220万+下载显示无审查模型的社区需求。 |
| [MiniMax-H3-nvfp4-INT4-INT8-Convrot](https://huggingface.co/Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot) | Abiray | 128 | 452,420 | MiniMax-H3 的多精度量化版本（NVFP4/INT4/INT8）。45万+下载，量化技术多样化为硬件适配铺路。 |
| [Unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 588 | 161,253 | Unsloth 官方 DeepSeek-V4 的 GGUF 量化，优化推理速度。16万+下载，量化与效率兼顾。 |
| [LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 145 | 31,489 | LiquidAI 小模型的 GGUF 量化版，本地部署友好。配合原模型形成完整开源生态链。 |
| [MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 420 | 0 | MiniMax-H3 的 LoRA 微调，专注视频生成加速。虽无下载记录但技术方向受关注。 |
| [MiniMax-H3_Turbo_Lora_ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 178 | 0 | 集成 ComfyUI 的 LoRA 微调版本，降低使用门槛。反映社区对易用性的持续追求。 |
| [MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 168 | 87,870 | MiniMax-H3 的多 GGUF 量化集合，覆盖不同精度需求。8.7万+下载满足多样化本地部署场景。 |
| [Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF) | LuffyTheFox | 425 | 332,992 | Qwen3.6 大规模 MoE 模型的无审查 GGUF 版本。33万+下载，Heritage/Hermes 系列持续迭代。 |

---

## 生态信号

本周最显著的趋势是 **MiniMax-H3 视频生成模型引发的生态爆发**：不仅主模型高热，衍生出 ComfyUI 集成、LoRA 微调、多精度量化等数十个社区版本，形成完整的工具链生态。国产 LLM（DeepSeek、Kimi、GLM）持续领跑语言模型榜单，显示中国开源模型生态已进入高质量输出阶段。量化活动空前活跃，GGUF 版本下载量普遍在十万至百万级，反映本地部署需求旺盛。无审查/去限制模型虽属灰色地带，但 220万+下载的数据不容忽视。多模态融合（图文转视频、视觉语言模型）是明确的下一阶段竞争焦点。

---

## 值得探索

1. **[Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 本周点赞之王（10,284），国产多模态 LLM 的新标杆，图文理解能力值得重点测试。

2. **[MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — 视频生成赛道最新热门，虽官方下载量不高但生态衍生极为丰富，是研究文生视频技术的理想起点。

3. **[Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B)** — Mistral 推出的轻量安全模型，在内容审核与模型对齐领域具有独特价值，适合生产环境集成研究。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*