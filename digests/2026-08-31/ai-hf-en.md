# Hugging Face Trending Models Digest 2026-08-31

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-31 04:59 UTC

---



# Hugging Face Trending Models Digest — 2026-08-31

---

## 1. Today's Highlights

The Qwen3.8 family dominates the top of the leaderboard, with **Qwen/Qwen3.8-Flash-Next** claiming the #1 spot with over 4,400 weekly likes and 121K downloads — a clear signal that Qwen's latest generation is resonating strongly with the community. Meanwhile, **MiniMaxAI/MiniMax-H3** has become the most-downloaded video generation model on the list, surpassing 5.2M downloads, underscoring the explosive appetite for open video synthesis. The uncensored/abliterated fine-tune ecosystem around Qwen3.8-27B continues to surge, with multiple community variants collectively racking up tens of millions of downloads, while quantized GGUF releases from Unsloth are seeing massive adoption as users optimize for local deployment.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,404 | 121,976 | The top-trending model this week, combining the Qwen4_exp architecture with image-text-to-text capability and conversational tuning. Its rapid climb reflects strong community demand for a balanced, multimodal chat model that remains efficient to run. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,732 | 346,516 | A lightweight GLM-5 variant that supports both text generation and image-text-to-text pipelines, accumulating over 346K downloads — the second-highest in its category. Its dual-pipeline support makes it attractive for multimodal workflows on constrained hardware. |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,359 | 50,116 | The full-parameter counterpart to GLM-5.3-Flash, using the glm_moe_dsa architecture for text generation and conversational use. It offers a higher-fidelity option for users who prioritize quality over speed. |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,364 | 4,511,348 | The flagship open-weight model in the Qwen3.8 lineup with 13,364 likes — the highest in the entire list. It is a versatile image-text-to-text conversational model that has become the go-to foundation for both production and community fine-tuning. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,826 | 4,575,518 | DeepSeek's latest Flash variant with 4.5M+ downloads, delivering strong conversational text-generation performance at an accessible footprint. Its adoption trajectory mirrors the broader trend toward efficient, high-quality open-weight language models. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,106 | 2,794,721 | Kimi's K3 model brings compressed-tensors support to image-text-to-text pipelines, combining strong multimodal capability with deployment efficiency. Over 11K likes indicate significant community enthusiasm for Moonshot AI's open-weight direction. |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 323 | 2,123 | Tencent's Hunyuan v4 preview introduces the hy_v4 architecture for text generation, marking the company's latest open-weight foray into the competitive Chinese-language LLM space. Early downloads suggest cautious but growing interest. |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 158 | 1,009 | A domain-specific Qwen3.5 MoE model from Thomson Reuters targeting legal and financial text understanding with image-text-to-text support. Its modest but targeted download count reflects its niche enterprise orientation. |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 155 | 3,982 | A Nemotron-based text-generation model integrated into the Pipecat AI real-time voice pipeline, enabling on-device conversational capabilities. Early adoption signals interest in voice-first AI architectures. |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 507 | 147,038 | A Qwen3.5 MoE architecture model supporting both text generation and image-text-to-text, designed for high-throughput inference with an active-spec expert design. Its dual-pipeline support and 147K downloads reflect growing demand for efficient MoE models. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,665 | 5,263,381 | The most-downloaded model on this week's list, MiniMax-H3 is a text-to-video and image-to-video generator with 5.2M+ downloads. Its cinematic-quality video synthesis and open weights have made it the de facto standard for community video generation. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,281 | 1,137,181 | A diffusion-based image-to-video and text-to-video model from Lightricks, supporting single-file deployment and video-to-video workflows. Over 1.1M downloads highlight sustained demand for accessible video generation tools. |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 197 | 0 | A data-free, 4-step acceleration of MiniMax-H3 using VSA (Video State Attention), enabling dramatically faster video synthesis without retraining. Its experimental nature and zero downloads so far suggest it is in early preview stages. |
| [alibaba-pai/MiniMax-H3-Fun-Controlnet-Union](https://huggingface.co/alibaba-pai/MiniMax-H3-Fun-Controlnet-Union) | alibaba-pai | 163 | 5,538 | A ControlNet-Union adapter for MiniMax-H3 that enables precise structural control over text-to-video and image-to-video generation. It extends H3's creative flexibility for production video pipelines. |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 154 | 23,734 | Accuracy-tuned LoRA adapters for MiniMax-H3 that refine video generation quality across specific attributes. The 23K downloads indicate active experimentation with post-hoc enhancement of H3 outputs. |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 215 | 1,838 | A text-to-speech model in the Breeze family, offering high-quality voice synthesis with transformers-based inference. Early adoption suggests it is filling a niche for open-weight TTS in multimodal pipelines. |
| [Kijai/MiniMax-H3-experimental](https://huggingface.co/MiniMax-H3-experimental) | Kijai | 366 | 0 | An experimental integration of MiniMax-H3 designed for ComfyUI workflows, targeting nodes and regions in the US. Zero downloads indicate it is a very recent or niche addition to the ecosystem. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 145 | 87,848 | A code-specialized Qwen3.5 MoE model with 35B total parameters and 3B active, quantized to GGUF for efficient local inference. The 87K downloads reflect strong developer interest in open-weight coding assistants. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | Unsloth | 3,251 | 8,839,153 | The most-downloaded GGUF quantization in the digest, with nearly 8.8M downloads. Unsloth's optimized Qwen3.8-27B quant enables efficient local inference while preserving the base model's strong multimodal chat performance. |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | Unsloth | 607 | 328,195 | A GGUF-quantized version of the top-trending Qwen3.8-Flash-Next, giving users the ability to run the model locally with reduced memory footprint. Its 328K downloads show strong demand for accessible quantized variants. |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | Unsloth | 292 | 45,936 | Unsloth's quantized port of GLM-5.3-Flash, enabling efficient local deployment of the dual-pipeline GLM model. Modest but growing adoption signals early-stage uptake. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 952 | 725,757 | An abliterated (uncensored) variant of Qwen3.8-27B using MLX, GGUF, and safetensors formats, removing RLHF constraints for unrestricted generation. Over 725K downloads reflect significant community demand for unrestricted open-weight models. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,236 | 109,121 | An MLX-formatted uncensored fine-tune of Qwen3.8-27B, optimized for Apple Silicon inference. Its 1.2K likes and 109K downloads indicate strong interest from the Mac-based AI community. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,290 | 301,964 | An FP8-quantized uncensored variant of Qwen3.8-27B that balances memory efficiency with unrestricted generation capability. The 301K downloads show FP8 remains a popular quantization target for consumer GPU users. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 856 | 1,991,437 | A GGUF-quantized uncensored Qwen3.8-27B with MTP (Multi-Token Prediction) support, nearly 2M downloads making it one of the most-used community fine-tunes. It remains a cornerstone model for local unrestricted inference. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 586 | 238,397 | Another abliterated GGUF port of Qwen3.8-27B from the same author as the MLX and FP8 variants, offering consistency across quantization formats for power users. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 791 | 1,158,065 | An aggressively abliterated GGUF variant with MTP, targeting users who want maximum capability retention alongside unrestricted generation. Over 1.1M downloads make it one of the top community fine-tunes. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 459 | 1,622,056 | A widely downloaded abliterated GGUF fine-tune from huihui-ai, combining uncensored generation with strong multimodal support. The 1.6M downloads reflect its popularity as a local all-rounder. |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 125 | 42,864 | An abliterated GGUF port of the flash variant Qwen3.8-Flash-Next, bringing unrestricted generation to the more efficient model architecture. Early-stage but aligned with the growing uncensored-flash trend. |

---

## 3. Ecosystem Signal

The dominant ecosystem trend this week is the **Qwen3.8 generational leap**. Qwen3.8-27B and its Flash derivative form the backbone of both official and community activity — the base models lead in likes, while uncensored and quantized variants collectively exceed 20M downloads. This dual presence (official + community) signals a mature open-weight ecosystem where the base model acts as a universal substrate for specialization.

**Open-weight momentum is overwhelming.** Every top-tier model on this list is open-weight, with proprietary-only models entirely absent. The GLM-5.3 family from zai-org and DeepSeek-V4-Flash further reinforce the Chinese lab ecosystem as the primary engine of open model innovation.

**Quantization and abliteration are the two fastest-growing fine-tuning vectors.** Unsloth's GGUF ports see tens of millions of downloads, while abliterated/uncensored variants of Qwen3.8-27B collectively account for over 5M downloads — demonstrating that users are actively removing safety constraints rather than waiting for official releases. MoE architectures (Qwen3.5_moe, Tiel-Coder) are also gaining traction as efficiency benchmarks improve.

**Video generation is entering a maturation phase.** MiniMax-H3's 5.2M+ downloads and the emergence of ControlNet, LoRA, and acceleration variants indicate the ecosystem is moving from raw generation toward precise, production-grade video pipelines.

---

## 4. Worth Exploring

1. **[Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next)** — The #1 trending model for a reason. It pairs the latest Qwen4_exp architecture with image understanding and conversational tuning in an efficient package. Whether running the full model or the Unsloth GGUF variant, it represents the best current balance of capability and accessibility for general-purpose multimodal use.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — With over 5.2M downloads, this is the definitive open video generation model of the moment. Its ecosystem of ControlNet adapters, accuracy LoRAs, and 4-step accelerations makes it a rich subject for studying how a single base model can spawn a full generation pipeline ecosystem.

3. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — Kimi-K3's compressed-tensors support and 11K+ likes suggest it is solving the critical trade-off between context length and deployability. For users who need long-context multimodal understanding without the hardware cost of a full 27B model, this is the most compelling new entry on the list.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*