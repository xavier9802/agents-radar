# Hugging Face Trending Models Digest 2026-09-01

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-09-01 04:39 UTC

---



# 🤗 Hugging Face Trending Models Digest — 2026-09-01

---

## 1. Today's Highlights

Qwen's 3.8 family continues its dominant run, with **Qwen3.8-Flash-Next** claiming the top spot for weekly likes while its larger **Qwen3.8-27B** variant sustains over 4.7 million downloads. MiniMax-H3 remains the standout video-generation model with 4.7K likes and 5.3M downloads, and DeepSeek-V4-Flash-0731 re-enters the top tier with nearly 4.6M downloads. Meanwhile, the abliterated/uncensored community fine-tune scene is extraordinarily active around Qwen3.8-27B, with at least five variants collectively racking up over 4M downloads.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,536 | 158,598 | Qwen's latest flash-tier conversational model with image-text-to-text support, leading this week's likes. Its conversational tuning and multimodal input make it a strong default for production chat pipelines. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,119 | 2,792,274 | Kimi's K3 series continues to attract massive adoption with over 2.7M downloads, leveraging compressed-tensors for efficient inference. Its image-text-to-text pipeline and strong engagement signal sustained momentum for Moonshot AI. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,843 | 4,561,861 | DeepSeek's conversational text-generation model crossing 4.5M downloads, reflecting strong community preference for its efficiency and open-weight availability. Its flash variant continues the lineage of high-throughput open LLMs. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,820 | 379,271 | GLM's flash-tier multimodal model with image-text-to-text capability and conversational fine-tuning. Its rapid download growth signals strong community interest in the next GLM iteration. |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,423 | 66,195 | The base text-generation conversational variant of GLM-5.3 using a novel MoE DSA architecture. Its lower download count compared to the Flash variant suggests users prefer the quantized/multimodal release. |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 356 | 2,589 | Tencent's Hunyuan Hy4 text-generation preview, an early release building on the Hunyuan lineage. As a preview model it is still accumulating adoption but represents an important open-weight benchmark. |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 516 | 172,695 | An MoE-based model from the Ornith family combining text-generation and image-text-to-text capabilities. Its efficient sparse activation (35B total / 3B active) is drawing attention for cost-effective deployment. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,711 | 5,362,365 | MiniMax's leading image-to-video and text-to-video model with 5.3M downloads, making it the most-downloaded generation model on this list. Its multimodal input support and videox-fun pipeline integration drive its popularity. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,380 | 1,182,585 | LTX-2.5 is a diffusion-single-file model supporting image-to-video, text-to-video, and video-to-video generation. Its single-file architecture simplifies deployment and it has accumulated over 1.1M downloads. |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 374 | 0 | DeepSeek's experimental vision-enabled flash variant, bridging image-text-to-text and text-generation. Being a new experimental release it has zero downloads but signals DeepSeek's push into multimodal flash models. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 166 | 105,974 | A coding-specialized MoE model using imatrix-calibrated quantization for GGUF delivery. Its 105K downloads indicate a niche but dedicated developer audience seeking efficient code-generation capabilities. |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 177 | 4,721 | A text-generation model built on the Nemotron-H architecture for low-latency voice pipelines. Its small download count reflects its early alpha stage and specialized real-time telephony use case. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,294 | 9,059,937 | The most-downloaded model on this digest — a community GGUF quantization of Qwen3.8-27B by Unsloth, enabling efficient CPU/GPU inference. Its near 9M downloads demonstrate that quantized variants often outperform base models in raw usage. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 879 | 2,055,081 | A GGUF uncensored fine-tune of Qwen3.8-27B that has become one of the most-used uncensored variants with over 2M downloads. It combines abliterated safety removal with llama.cpp-compatible quantization. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 816 | 1,202,914 | An aggressive MTP (multi-token prediction) enhanced uncensored fine-tune of Qwen3.8-27B, delivering both abliterated behavior and faster inference via MTP. Over 1.2M downloads make it one of the top uncensored GGUF releases. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,330 | 307,496 | An FP8-quantized uncensored version of Qwen3.8-27B, offering memory-efficient inference without the GGUF format. Its 1.3K likes indicate strong interest in the FP8 path for high-throughput deployments. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 607 | 246,445 | Another uncensored GGUF variant from the prolific orcarouter, providing an alternative calibration to the JonathanColetti release. Its steady adoption suggests a diverse community of abliterated model consumers. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 977 | 759,644 | The original abliterated Qwen3.8-27B release in mixed GGUF/safetensors formats, which helped catalyze the entire uncensored fine-tune wave. Nearly 760K downloads reflect its role as a benchmark for abliterated models. |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 639 | 373,029 | Unsloth's quantized GGUF release of the trending Qwen3.8-Flash-Next, extending the flash model's accessibility to resource-constrained environments. Over 373K downloads show strong demand for quantized conversational models. |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 152 | 51,125 | An abliterated GGUF fine-tune combining the Flash-Next architecture with uncensored behavior. Though newer, it already captures a portion of the community that prefers uncensored flash-tier models. |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 131 | 1,541 | The earliest entry in the GLM-5.3 Flash uncensored FP8 space, a nascent but growing category. Minimal downloads reflect its recent release but signal ongoing community experimentation. |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 218 | 0 | A distilled 4-step variant of MiniMax-H3 using VSA data-free conditioning for accelerated video generation. Zero downloads indicate it is a very new release, but the approach is notable for enabling fast video inference. |

---

## 3. Ecosystem Signal

The Qwen 3.8 family is the clear ecosystem anchor, appearing as the base for at least ten community fine-tunes and quantizations spanning GGUF, FP8, MLX, and abliterated variants. This reflects a maturing open-weight ecosystem where community extensions consistently outpace base-model download counts — the Unsloth Qwen3.8-27B GGUF (9M+) dwarfs its base model (4.7M). MiniMax-H3 dominates the video-generation space with half the ecosystem's total video-related downloads, while DeepSeek-V4-Flash-0731 continues proving that high-quality open conversational LLMs can compete with proprietary offerings on raw adoption. The abliterated/uncensored sub-ecosystem is exceptionally active around the 27B parameter sweet spot, with four distinct GGUF variants and one FP8 release collectively exceeding 4.3M downloads. Quantization activity is dominated by GGUF through Unsloth and community calibrations, with FP8 emerging as a secondary path for GPU-bound deployments. Open-weight models continue to capture the majority of trending engagement, though proprietary-preview models (Hy4-preview, DeepSeek-Vision-Exp) signal ongoing R&D velocity.

---

## 4. Worth Exploring

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The undisputed leader in open video generation with 5.3M downloads and strong multimodal input support. Worth studying for its videox-fun integration and as a benchmark against proprietary video models.

2. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — The most-downloaded model on the list (9M+), demonstrating that community quantization can dramatically expand a model's reach. A practical model for anyone deploying LLMs on constrained hardware.

3. **[deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp)** — An experimental release from DeepSeek combining their flash efficiency with vision capabilities. Worth tracking as a signal of where DeepSeek's multimodal roadmap is heading.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*