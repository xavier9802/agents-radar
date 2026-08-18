# Hugging Face 热门模型日报 2026-08-18

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-08-18 01:38 UTC

---



# Hugging Face 热门模型日报
**日期：2026-08-18**

---

## 今日速览

2026年8月中旬的HF社区呈现"多模态爆发 + 效率量化"双主线并行态势。MiniMax-H3视频生成模型登顶下载榜，累计下载超240万；Qwen3.8系列多形态权重（原生/GGUF/FP8/NVFP4）构成最完整的开源开源生态链；DeepSeek-V4-Flash以3,499赞跻身前三，显示高效推理模型的持续热度。同时，社区对Uncensored版本和ComfyUI集成格式的需求显著增长，量化技术从INT8向FP8、NVFP4演进。

---

## 热门模型

### 🧠 语言模型

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 10,725 | 415,039 | Qwen3.8系列旗舰稠密模型，支持图文对话，以10,725周赞稳居榜单首位，代表开源多模态语言的持续强势。 |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,041 | 9,465 | Qwen3.8 MoE大参数版本（2.4T总参数，激活95B），适合对推理质量要求极高且拥有充足算力的场景。 |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,662 | 334,099 | 30B级图文对话模型，综合性能与效率兼顾，下载量超33万，在社区获得稳定认可。 |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 574 | 25,006 | DeepSeek V4 Pro版本，标注日期为0813，面向需要高质量推理但更关注参数效率的用户。 |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,499 | 1,978,298 | DeepSeek V4 Flash版本，主打高效推理，以近200万下载量成为本周下载量第二高的LLM。 |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,802 | 2,163,953 | Kimi K3图文对话模型，周赞10,802略超Qwen3.8-27B，下载量超216万，体现长上下文能力的持续吸引力。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 307 | 231,271 | NVIDIA Nemotron 3.5 Lightning系列，采用NVFP4量化技术，总参数30B但激活仅3B，追求极致推理效率。 |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 307 | 6,266 | Ling 3.0 tiny版本，使用Bailing Hybrid架构，适合轻量级中文场景部署。 |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 207 | 633 | Dots3 Note系列前序版本，聚焦中文场景的轻量级对话模型。 |
| [LiquidAI/LFM2.5-VL-3B](https://huggingface.co/LiquidAI/LFM2.5-VL-3B) | LiquidAI | 162 | 6,816 | LiquidAI的3B多模态小模型，在有限参数下追求多模态理解能力，适合边缘部署。 |

### 🎨 多模态与生成

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,088 | 2,403,238 | MiniMax视频生成旗舰模型，支持文生视频/图生视频，以超240万下载量成为本周下载量榜首，代表视频生成模型的高需求。 |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,111 | 465,529 | LTX-2.5视频生成模型，支持文本/图像到视频的多模式生成，46万下载体现用户对开源视频生成模型的持续兴趣。 |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 586 | 264,351 | 基于MiniMax-H3的Turbo加速版本，在保持质量的同时提升生成速度，适合实时应用场景。 |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 906 | 10,375 | MiniMax音乐生成模型，支持文本到音乐生成，填补开源音频生成领域的空白。 |

### 🔧 专用模型

（本周榜单中无明确标注为代码、数学、医疗、嵌入等专用领域的模型，此分类省略。）

### 📦 微调与量化

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 1,635 | 2,727,609 | Qwen3.8-27B的GGUF量化版本，由unsloth优化，以超272万下载量成为本周下载量最高的量化模型，反映端侧部署需求强劲。 |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 532 | 495,646 | Qwen官方发布的FP8量化版本，比BF16原生版本显存占用降低约50%，同时保持较高精度。 |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 440 | 15,812 | 社区uncensored版本，结合FP8量化，面向需要突破安全限制的特定研究与应用场景。 |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 240 | 378,177 | Qwen3.8-27B的NVFP4量化版本，由unsloth出品，代表下一代低精度量化的实践探索。 |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 307 | 357,701 | 社区uncensored GGUF版本，支持llama.cpp直接运行，适合本地无限制对话场景。 |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 220 | 12,295 | Qwen3.8 MoE模型的FP8量化版本，使2.4T参数模型能够在单卡或多卡环境下部署。 |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 169 | 69,833 | Nemotron Lightning系列的BF16原生版本（未量化），与NVFP4版本形成对比，供追求极致精度的用户选择。 |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,120 | 3,033,928 | 社区大型微调融合模型，融合多种风格与能力，以超303万下载成为本周微调类最高，体现社区对定制化模型的强烈需求。 |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 470 | 755,125 | Muse-Glimmer-30B的GGUF量化版，支持llama.cpp端侧运行，下载量超75万。 |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,403 | 14,015,769 | MiniMax-H3的ComfyUI专用集成包，以超1,400万下载量傲视群雄，反映ComfyUI生态在视频生成领域的统治级地位。 |
| [Comfy-Org/MiniMax-Music-3](https://huggingface.co/Comfy-Org/MiniMax-Music-3) | Comfy-Org | 167 | 256,988 | MiniMax-Music3的ComfyUI集成版本，方便在ComfyUI工作流中直接使用音乐生成功能。 |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 244 | 18,562 | 基于MiniMax-H3的人物写实风格LoRA，用于提升视频中人物的真实感表现。 |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 786 | 0 | MiniMax-H3-Turbo的LoRA微调版本，面向需要更快速生成但保持质量的场景。 |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 237 | 0 | 基于MiniMax-H3的finetune版本，针对特定视觉风格进行优化。 |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,211 | 0 | Qwen系列固定对话模板工具，解决chat template兼容性问题，0下载但1,211赞说明其在社区中作为"工具型"资源的价值。 |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 233 | 23,202 | Anima 2.9B的ComfyUI集成版，轻量级文生图模型，适合资源有限的本地环境。 |

---

## 生态信号

本周HF生态呈现三大趋势：一是**Qwen家族占据绝对主导地位**，从原生权重到GGUF/FP8/NVFP4全链路覆盖，社区微调版本（Uncensored、融合版）也紧随其后，形成最完整的开源LLM生态；二是**MiniMax在视频生成领域迅速崛起**，H3模型及其ComfyUI集成包、LoRA衍生版本合计下载量极高，显示视频生成正在从"闭源垄断"转向"开源繁荣"；三是**量化技术向更低精度演进**，FP8成为主流新标准，NVFP4和GGUF并行发展，端侧部署门槛持续降低。同时，社区对Uncensored模型和ComfyUI集成格式的需求异常活跃，反映开发者对定制化与易用性的双重追求。

---

## 值得探索

1. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — 超1,400万下载量证明其价值，ComfyUI集成使视频生成工作流搭建大幅简化，是进入开源视频生成领域的最佳入口。

2. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Unsloth/Qwen3.8-27B-GGUF)** — 272万下载量+unsloth优化，代表当前端侧部署的最优实践之一，适合在消费级GPU上运行高质量多模态对话。

3. **[deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731)** — 近200万下载、3,499赞，体现高效推理模型的持续热度，适合在资源受限场景下替代更高参数模型。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*