# Hugging Face Trending Models Digest 2026-08-15

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-15 01:37 UTC

---



# 🤗 Hugging Face Trending Models Digest
**Date: 2026-08-15**

---

## 1. Today's Highlights

Kimi-K3 leads this week's rankings with 10,675 weekly likes and nearly 2 million downloads, cementing its position as the most-discussed open model. MiniMax-H3 dominates the video-generation space, accumulating almost 2 million downloads through ComfyUI packaging, while Qwen's 27B and 2.4T parameter models show strong adoption across both dense and MoE architectures. A clear wave of Chinese lab releases—Qwen, DeepSeek, MiniMax, and Kimi—dominates the top 30, reflecting accelerated open-weight momentum from Chinese AI labs. Quantization activity is particularly active, with GGUF, FP8, and NVFP4 variants of the same base models appearing side by side.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,675 | 1,974,635 | A compressed-tensors image-text-to-text conversational model from Moonshot AI that has become the most-liked model this week. Its high download count signals strong developer uptake for chat and RAG fine-tuning. |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 9,026 | 2 | The flagship dense 27B model in Qwen's 3.8 line, supporting image-text-to-text conversations. Despite only 2 downloads, its 9,026 likes indicate heavy community interest and anticipation. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,385 | 1,606,491 | DeepSeek's fast text-generation variant of V4, leveraging an optimized architecture for conversational throughput. Over 1.6 million downloads make it one of the most widely deployed open chat models. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 918 | 3,832 | A 2.4T-parameter MoE conversational model (95B active) from Qwen's 3.8 family, enabling high-capacity reasoning with efficient inference. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 434 | 245 | The "Pro" variant of DeepSeek V4, likely targeting higher-accuracy or more capable conversational use cases. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 257 | 119,572 | NVIDIA's 30B MoE chat model with only 3B active parameters, using proprietary NVFP4 quantization for inference speed. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 615 | 124,172 | A compact 2.6B text-generation model from Liquid AI, leveraging liquid neuron architectures for efficient language modeling. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 143 | 34,137 | The BF16 counterpart to NVIDIA's Lightning MoE model, offering full-precision inference as a baseline. |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 142 | 11 | A new image-text-to-text conversational model from Dots Studio, still in early adoption with minimal downloads. |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 184 | 9,334 | FP8-quantized variant of Qwen's 2.4T MoE conversational model, targeting lower-memory deployment. |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 381 | 1,366 | An 11B voice-chat-optimized model from NVIDIA, referencing research on conversational voice interfaces. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,920 | 1,997,541 | MiniMax's flagship image-text-to-video model that has exploded to nearly 2 million downloads, driven by strong quality and ComfyUI ecosystem adoption. It supports both text-to-video and image-to-video generation. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 859 | 207,830 | Lightricks' diffusion-based image-to-video model supporting text-to-video, image-to-video, and video-to-video pipelines in a single file. Over 200K downloads indicate solid creator adoption. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 493 | 149,865 | A turbo (optimized) variant of MiniMax-H3 for faster image-to-video generation, popular among ComfyUI users needing speed. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 653 | 63 | MiniMax's text-to-music generation model, continuing the H3 family into the audio domain. Still early in adoption with 63 downloads. |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 162 | 10,106 | A compact 2.9B text-to-image diffusion model in single-file format, targeting ComfyUI users seeking a lighter generation option. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 235 | 2,283 | A tiny embedding model from inclusion AI using a bailing-hybrid architecture under MIT license, suitable for lightweight retrieval tasks. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,515 | 165,300 | A 30B image-text-to-text conversational model whose 165K downloads suggest steady adoption; the companion GGUF versions see even higher quantized usage. |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 414 | 596,774 | Unsloth's GGUF quantization of Muse-Glimmer-30B, with nearly 600K downloads making it one of the most-downloaded quantized models this week. |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 270 | 228,364 | Official GGUF quantized variant of Muse-Glimmer-30B, citing arXiv papers on the underlying architecture. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,017 | 2,891,524 | An uncensored community fine-tune of Qwen3.6-27B with a lengthy descriptive name; its 2.89 million downloads make it the highest-downloaded model on this list. |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 815 | 0 | Unsloth's GGUF quantization of Qwen3.8-27B; no downloads yet, likely just posted. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 302 | 0 | Official FP8-quantized variant of Qwen3.8-27B; not yet downloaded, indicating a very recent release. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,318 | 11,768,622 | The ComfyUI-packaged version of MiniMax-H3 with a staggering 11.77 million downloads, making it the most-downloaded model on this list by a wide margin. |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 156 | 136,774 | GGUF quantized MiniMax-H3 for local video generation, seeing strong adoption in the quantized video-generation niche. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 742 | 0 | A LoRA adapter for MiniMax-H3 Turbo focused on text-to-video enhancement; new release with no downloads yet. |
| [SexGod1979/PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 311 | 473 | An uncensored fine-tune of MiniMax-H3 for text-to-video, licensed under Apache 2.0 with endpoint compatibility. |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 177 | 9,060 | A LoRA fine-tune focused on realistic human generation with MiniMax-H3, seeing active use in the 9K+ range. |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 318 | 112,975 | A ComfyUI-optimized LoRA adapter for MiniMax-H3 Turbo with over 112K downloads, reflecting strong community integration. |
| [Kijai/MiniMax-H3_comfy](https://huggingface.co/Kijai/MiniMax-H3_comfy) | Kijai | 340 | 0 | A ComfyUI-specific packaging of MiniMax-H3 by Kijai; recently posted with no downloads yet. |

---

## 3. Ecosystem Signal

The Hugging Face landscape this week is defined by the **dominance of Chinese open-weight labs**—Qwen, DeepSeek, MiniMax, and Kimi collectively account for the vast majority of top-liked and top-downloaded models. Chinese developers are releasing dense, MoE, quantized, and fine-tuned variants of the same base architectures at remarkable speed, creating a multi-tiered model family ecosystem rather than single-shot releases.

**MiniMax-H3** is the standout viral model: the original weights sit at 1.99M downloads, but the ComfyUI-packaged variant has amassed an astonishing **11.77M downloads**, making it the most-downloaded model on the list. This illustrates a growing trend where ecosystem tooling (ComfyUI, GGUF quantization) drives adoption far more than raw model quality alone.

**Quantization activity is intense.** Every major base model has GGUF and FP8 variants already appearing, with Unsloth dominating the GGUF space. NVIDIA is introducing a novel **NVFP4** quantization format, signaling continued hardware-aware optimization. The uncensored/community fine-tune market remains active, with the DavidAU Qwen3.6 fine-tune reaching 2.89M downloads. Open-weight remains the clear winner over proprietary-only releases in community engagement.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — The most-liked model this week with nearly 2M downloads and compressed-tensors optimization. Worth studying for its balance of quality and efficiency, and for understanding what Chinese-language and multilingual chat users are gravitating toward.

2. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — With 11.77M downloads, this is the highest-downloaded model on the list by far. It's a masterclass in ecosystem distribution: the same underlying model, packaged for ComfyUI, reaching a vastly larger audience. Essential for anyone building video-generation pipelines.

3. **[deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731)** — 1.6M downloads and 3,385 likes make this the most widely used open chat model this week. Its Flash designation suggests a speed-optimized variant, making it highly relevant for production deployments where latency matters.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*