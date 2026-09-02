# Hugging Face Trending Models Digest 2026-09-02

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-09-02 04:01 UTC

---



# 🤗 Hugging Face Trending Models Digest
**Date: 2026-09-02**

---

## 1. Today's Highlights

Qwen's **Qwen3.8-Flash-Next** family continues to dominate this week's trending charts, with the base model, GGUF, and FP8 variants all ranking in the top 20. Meanwhile, **MiniMax-H3** has emerged as a powerhouse in video generation, amassing over 5.5 million downloads and nearly 4,800 weekly likes. The uncensored/abliterated fine-tuning ecosystem remains highly active around the Qwen3.8-27B backbone, with six community variants charting this week. Notably, the **unsloth/Qwen3.8-27B-GGUF** model leads the entire list in downloads at nearly 9.4 million, underscoring sustained community demand for efficient local inference.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,657 | 207,941 | The latest flash-tier model from Qwen, optimized for fast conversational and multimodal image-text-to-text tasks. Its rapid uptake reflects strong community appetite for a cost-effective, high-throughput LLM. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,894 | 441,348 | A flash-optimized GLM 5.3 variant supporting image-text-to-text pipelines. High download volume signals strong deployment interest for multimodal chat applications. |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,472 | 94,403 | The base text-generation model from the GLM 5.3 line, using a MoE DSA architecture. Gaining traction as a strong open-weight alternative for pure text tasks. |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,595 | 4,960,483 | The flagship 27B Qwen3.8 model with image-text-to-text capability, ranking among the most-liked models on the platform. Its massive download count reflects its role as a go-to open-weight generalist. |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 386 | 3,516 | Tencent's Hunyuan v4 preview text-generation model. Early community interest is building around this next-gen Hunyuan release. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,130 | 2,783,061 | Kimi's K3 model with image-text-to-text support and compressed-tensors optimization. Extremely high likes and downloads indicate strong momentum for Moonshot AI's open-weight offering. |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 181 | 1,130 | A compact Qwen3.5 MoE model from Thomson Reuters tailored for conversational image-text-to-text. Targets the legal and financial vertical with an efficient footprint. |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 186 | 6,813 | A voice-centric text-generation model from Pipecat, built on Nemotron architecture. Aimed at real-time conversational voice AI pipelines. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,759 | 5,532,597 | A leading image-to-video and text-to-video model with over 5.5 million downloads. Its massive adoption reflects a surge in demand for high-quality open video generation. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,473 | 1,232,274 | Lightricks' diffusion-based video generation model supporting image-to-video, text-to-video, and video-to-video pipelines. Strong engagement signals healthy competition in the video-gen space. |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 458 | 17,893 | DeepSeek's experimental vision-capable Flash model for image-text-to-text tasks. An early preview attracting researchers interested in DeepSeek's next-gen multimodal direction. |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 238 | 0 | A 4-step distilled video generation model using VSA and data-free training. Notable for its extreme speed, targeting real-time video synthesis use cases. |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 314 | 3,086 | A text-to-speech model from BreezeBlue for high-quality voice synthesis. Early interest from the voice AI community. |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 178 | 32,893 | Accuracy-boosting LoRA adapters for MiniMax-H3, targeting improved text-to-video fidelity. Leverages community research from arXiv (2607.26004). |
| [Kijai/MiniMax-H3-experimental](https://huggingface.co/Kijai/MiniMax-H3-experimental) | Kijai | 390 | 0 | An experimental integration of MiniMax-H3, likely for ComfyUI or similar workflows. Aiming to broaden access for the node-based generation community. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 226 | 0 | Google's latest time-series forecasting model (v3.0) in PyTorch. A specialized tool gaining early attention from the forecasting and analytics community. |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 184 | 130,086 | A 35B MoE coding model (A3B active params) quantized to GGUF with imatrix calibration. Targets developers seeking a capable open-code model for local inference. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,344 | 9,354,057 | The most-downloaded model this week: an unsloth-optimized GGUF quantization of Qwen3.8-27B. Near-9.4M downloads prove GGUF remains the dominant format for local LLM deployment. |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 676 | 431,339 | A GGUF quantization of the new Qwen3.8-Flash-Next, enabling efficient local inference. Strong download numbers show users prioritizing accessibility for the latest Qwen releases. |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 327 | 63,718 | Unsloth's GGUF port of GLM-5.3-Flash, making the model accessible for local and edge deployment with optimized inference. |
| [Qwen/Qwen3.8-Flash-Next-FP8](https://huggingface.co/Qwen/Qwen3.8-Flash-Next-FP8) | Qwen | 180 | 130,451 | Official FP8 quantization from Qwen for Flash-Next, targeting GPU users who want near-lossless speedups without third-party tools. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,006 | 805,791 | An "obliterated" (safety-filter-removed) version of Qwen3.8-27B in both MLX and GGUF formats. High engagement reflects continued demand for uncensored open models. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,352 | 316,128 | The highest-liked uncensored variant this week: an FP8 abliterated Qwen3.8-27B. Combines community demand for unrestricted models with practical quantization. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,261 | 121,028 | An MLX-formatted uncensored Qwen3.8-27B, optimized for Apple Silicon inference. Reflects growing adoption of MLX for local LLM running on Mac hardware. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 635 | 254,529 | A GGUF uncensored variant of Qwen3.8-27B, providing unrestricted inference for the popular backbone model. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 842 | 1,276,092 | An aggressive MTP-enhanced uncensored GGUF fine-tune with over 1.27M downloads. Demonstrates the community's appetite for both unrestricted and performance-boosted models. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 893 | 2,143,289 | A heavily downloaded uncensored GGUF fine-tune with 2.1M+ downloads. Stands out as one of the most-used local deployment variants this week. |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 144 | 2,576 | An FP8 uncensored variant of GLM-5.3-Flash, bringing the abliterated approach to the GLM model family. |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 170 | 64,325 | A GGUF uncensored port of the newest Qwen3.8-Flash-Next model, extending the abliterated pipeline to the latest release. |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 127 | 56,208 | A research-grade GGUF quantization using GSQ and RCO mixed-precision techniques from ISTA-DAS Lab. Targets users interested in cutting-edge quantization methods. |

---

## 3. Ecosystem Signal

The Qwen3.8 family is the clear ecosystem anchor this week. Both the Flash-Next and 27B variants have spawned extensive quantization and fine-tune ecosystems, with unsloth's GGUF ports and orcarouter's uncensored variants accumulating millions of combined downloads. This signals that **Qwen remains the dominant open-weight backbone** for community customization, much like Llama did in prior cycles.

In the video generation space, **MiniMax-H3** is rapidly closing the gap with established players, driven by Alibaba's distribution channel and the model's strong quality. The emergence of accuracy LoRAs and experimental integrations indicates a maturing ecosystem around open video models.

Quantization diversity is notable: GGUF still leads in raw downloads, but **FP8 and MLX formats are gaining share**, reflecting hardware-specific optimization trends (NVIDIA FP8 support and Apple Silicon's MLX framework). The uncensored/abliterated sub-ecosystem around Qwen3.8-27B is unusually large this cycle, with six distinct variants charting—suggesting sustained demand for unrestricted open models despite industry compression efforts.

---

## 4. Worth Exploring

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — With 5.5M+ downloads and 4,700+ likes, this is the video generation model to watch. Its multimodal (image-to-video + text-to-video) pipeline and rapid community adoption make it a strong candidate for evaluating open video generation capabilities.

2. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — 11,130 likes and 2.78M downloads are exceptional numbers. The compressed-tensors optimization and strong multimodal support suggest Kimi-K3 could become a leading open-weight competitor to Qwen and GLM in the generalist LLM space.

3. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — The single most-downloaded model this week (9.35M). Studying its quantization approach and community usage patterns offers practical insight into what drives local LLM adoption and the GGUF ecosystem's current state.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*