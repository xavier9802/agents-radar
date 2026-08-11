# Hugging Face Trending Models Digest 2026-08-11

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-11 02:09 UTC

---



# Hugging Face Trending Models Digest — August 11, 2026

---

## 1. Today's Highlights

MiniMax-H3 and its ecosystem of variants dominate this week's chart, with over a dozen derivations spanning text-to-video, ComfyUI integrations, LoRA adapters, and GGUF quantizations — signaling that MiniMax-H3 has become the de facto standard for open video generation. FLUX.1-dev by Black Forest Labs remains the most-liked model overall (14,077 likes), cementing its position as the leading open image generator. Kimi-K3 by moonshotai surges to the top of the language model category with over 10,000 likes and 1.5 million downloads, while Baidu's Unlimited-OCR continues to see massive community adoption with nearly 3 million downloads.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,472 | 1,510,032 | A strong image-text-to-text conversational model that has become the most-liked LLM on this week's chart. Its use of compressed tensors and feature extraction pipeline makes it efficient for deployment alongside its multimodal input support. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,063 | 954,441 | DeepSeek's latest flash variant delivers high-throughput text generation with conversational fine-tuning. Nearly a million downloads in its early window show strong demand for efficient open-weight LLMs. |
| [inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 288 | 5,261 | An open conversational model built on the Bailing hybrid architecture, featuring custom code support. It represents the growing interest in architecturally diverse alternatives to standard transformer designs. |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 312 | 1,344 | A preview release of a mixture-of-experts causal language model, signaling continued community experimentation with MoE scaling for efficient text generation. |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 222 | 6,343 | Mistral's security-focused 3B model designed for content moderation and shield-classification tasks, extending the Mistral 3 family into safety-critical deployment. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 754 | 0 | A 30B image-text-to-text conversational model from the meta-models collective, notable for its high like count despite zero recorded downloads (likely still processing). |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 490 | 89,680 | A 2.6B liquid neural network language model that offers an alternative to standard Transformer architectures, showing strong engagement for its novel approach to sequential modeling. |
| [endless-frontier/BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-frontier | 153 | 617 | A conversational image-text-to-text model built on a Qwen3.5 MoE backbone, representing the latest wave of MoE-based multimodal language models. |
| [SyzygyResearch/Mach-1-Additive-35B](https://huggingface.co/SyzygyResearch/Mach-1-Additive-35B) | SyzygyResearch | 116 | 2,129 | A 35B additive ternary mixture-of-experts model built on Qwen, exploring ternary weight representations for memory-efficient large-scale language modeling. |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 299 | 597 | NVIDIA's 11B conversational model optimized for voice interaction, with multiple arXiv references suggesting a research-backed approach to spoken dialogue systems. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [black-forest-labs/FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev) | black-forest-labs | 14,077 | 480,762 | The most-liked model on this week's chart and the leading open text-to-image generator. Its dev variant continues to set the quality bar for open-weight image synthesis. |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,438 | 47,468 | MiniMax's flagship image-text-to-video model that has spawned an entire ecosystem of derivatives. It leads the video generation category with strong community adoption. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 4,003 | 2,921,751 | Baidu's open OCR model with massive adoption — nearly 3 million downloads make it one of the most-used vision-language models on the platform. |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 338 | 13,432 | A compact 0.6B text-to-speech model from the ArkTTS lineage, offering an efficient open alternative for voice synthesis with strong community interest. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 261 | 15,087 | A turbo-optimized variant of MiniMax-H3 for faster image-to-video generation, catering to users who need speed without sacrificing quality. |
| [lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 117 | 268 | A LoRA adapter that rewrites text prompts for better MiniMax-H3 video generation results, showing the maturation of the H3 ecosystem with utility-focused tools. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 222 | 6,343 | A 3B safety/shield model from Mistral for content classification and moderation, part of the growing demand for open security-classification tools. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,149 | 6,009,639 | The most-downloaded model this week — a ComfyUI-compatible single-file diffusion package for MiniMax-H3 with over 6 million downloads, reflecting massive community integration. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,862 | 2,439,083 | An uncensored Heretic fine-tune of Qwen3.6-27B in GGUF format with over 2.4 million downloads, showing sustained demand for unrestricted open-weight LLM variants. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 638 | 199,167 | An Unsloth-optimized GGUF quantization of DeepSeek-V4-Flash, enabling efficient local inference with near-original quality. |
| [LiquidAI/LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 186 | 89,611 | GGUF quantization of the LiquidAI LFM2.5-2.6B model, making the liquid neural network architecture accessible for local llama.cpp deployment. |
| [realrebelai/MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 193 | 174,862 | GGUF-quantized MiniMax-H3 models for ComfyUI, providing memory-efficient versions for users running video generation on consumer hardware. |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 217 | 0 | Unsloth's GGUF quantization of the 30B Muse-Glimmer model, preparing it for efficient local inference once download data catches up. |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 154 | 0 | Official GGUF release of Muse-Glimmer-30B, directly from the model authors for optimized local deployment. |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 440 | 0 | An INT8-quantized Heretic fine-tune of Qwen3-VL-32B paired with MiniMax-H3 components for ComfyUI, targeting local multimodal generation. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 601 | 0 | A LoRA adapter for accelerated MiniMax-H3 video generation, part of the expanding toolkit around the H3 ecosystem. |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 251 | 0 | A ComfyUI-ready, pruned LoRA variant of the MiniMax-H3 turbo adapter for efficient local video generation workflows. |
| [sakamakismile/Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4](https://huggingface.co/sakamakismile/Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4) | sakamakismile | 152 | 0 | An NVFP4-quantized Heretic fine-tune combining Qwen3-VL-32B with MiniMax-H3 text encoding for ComfyUI, pushing the boundaries of quantized multimodal pipelines. |
| [SexGod1979/PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 251 | 0 | An Apache 2.0 licensed text-to-video fine-tune of MiniMax-H3, representing the diverse community creative applications built on the H3 foundation. |

---

## 3. Ecosystem Signal

The dominant ecosystem signal this week is the **MiniMax-H3 video generation supercluster**. Over a dozen models derive from or interoperate with MiniMax-H3, ranging from LoRA adapters and prompt rewriters to GGUF quantizations and ComfyUI integrations. The Comfy-Org single-file variant alone has accumulated over 6 million downloads, making it the most-downloaded model on the chart by a wide margin. This mirrors the earlier FLUX pattern, where a single strong open video generator catalyzes a wave of community tooling.

In language models, **DeepSeek-V4-Flash** continues its momentum with both a base release and Unsloth GGUF variants, while **Kimi-K3** emerges as the most-liked LLM of the week. The **GGUF quantization pipeline** remains extremely active — Unsloth, LiquidAI, and realrebelai are all converting popular models for local inference, reflecting sustained demand for efficient on-device deployment. Meanwhile, **MoE architectures** (Maple, BigBang, Mach-1) are gaining traction as the community explores scaling beyond dense models. Open-weight models continue to dominate the top spots, though proprietary-leaning releases from Baidu and NVIDIA show that labs are increasingly willing to ship open variants of specialized models.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — With over 10,000 likes and 1.5M downloads, this is the standout LLM of the week. Its compressed-tensor support and image-text-to-text pipeline make it a compelling choice for multimodal conversational applications, and the engagement numbers suggest it's already proven in production.

2. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — The most-downloaded model this week (6M+ downloads) by far. If you're working in video generation, this ComfyUI single-file package is essential infrastructure. It's the clear reference implementation that the entire H3 ecosystem orbits around.

3. **[black-forest-labs/FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev)** — Still the most-liked model on the platform (14,077 likes). As the benchmark against which all new image generators are measured, it remains worth studying for its architecture choices and quality ceiling, even as video generation steals the spotlight.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*