# Hugging Face Trending Models Digest 2026-08-10

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-10 02:18 UTC

---



# Hugging Face Trending Models Digest — 2026-08-10

## 1. Today's Highlights

MiniMax-H3 dominates the video generation space, spawning a rich ecosystem of over a dozen community ports, LoRAs, and ComfyUI integrations while the original from MiniMaxAI leads the榜 with over 3,200 weekly likes. DeepSeek-V4-Flash-0731 continues to see massive community adoption with hundreds of thousands of downloads, especially through quantized GGUF distributions. Multimodal frontiers are expanding rapidly — GLM-5.2 and Kimi-K3 push text/image understanding forward, while FLUX.1-dev remains the most-liked image generation model on the platform. A notable trend is the proliferation of aggressive quantization (NVFP4, INT4, INT8) and community fine-tuning around a handful of base models, particularly MiniMax-H3 and DeepSeek-V4.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,952 | 868,576 | DeepSeek's latest flash-tier conversational model, optimized for speed and cost. Its high download count signals strong demand for efficient open-weight LLMs in production pipelines. |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,914 | 2,488,397 | The latest GLM-series conversational model from Zhipu AI, built on a mixture-of-experts architecture. Nearly 2.5 million downloads make it one of the most-used open Chinese LLMs. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,399 | 1,456,459 | Moonshot AI's top multimodal model with image-text-to-text capability and compressed-tensors support. It holds the highest like count in this digest, reflecting strong community interest in capable vision-language models. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 453 | 85,651 | A compact 2.6B parameter model from Liquid AI leveraging liquid neural network architectures. Its unique architecture draws researchers and edge-deployment enthusiasts. |
| [inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 246 | 4,747 | An efficiency-optimized conversational model using Bailing-hybrid architecture with custom code support. Still early but shows promise for low-latency multilingual use cases. |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 290 | 1,089 | A Mixture-of-Experts causal LM in preview release, targeting efficient fine-grained routing. Its low download count suggests it's still building traction among MoE researchers. |
| [endless-frontier/BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-frontier | 125 | 482 | A Qwen3.5 MoE-based image-text-to-text conversational model. As a newer entrant, it's still accumulating adoption but offers an interesting MoE vision-language option. |
| [SyzygyResearch/Mach-1-Additive-35B](https://huggingface.co/SyzygyResearch/Mach-1-Additive-35B) | SyzygyResearch | 104 | 1,589 | A 35B-parameter MoE model using ternary additive quantization — a novel approach to extreme weight compression. Early-stage but notable for its research angle on loss-efficient quantization. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,251 | 35,295 | The original MiniMax-H3 image-text-to-video model, delivering high-quality video generation from text and image prompts. It anchors an entire ecosystem of community ports and fine-tunes. |
| [black-forest-labs/FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev) | black-forest-labs | 14,059 | 487,171 | The most-liked model in this digest — a state-of-the-art text-to-image generator from the Flux team. Its massive like count and steady downloads confirm its position as a community favorite. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,987 | 2,889,062 | Baidu's OCR model capable of processing images with unlimited resolution text. Nearly 2.9 million downloads make it one of the most-used open vision models for document and scene text extraction. |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 333 | 13,132 | A compact 0.6B text-to-speech model in preview, targeting efficient neural TTS deployment. Its small footprint makes it attractive for on-device and real-time voice applications. |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 261 | 543 | NVIDIA's 11B voice chat model combining speech understanding with generation. A very early release with low downloads but significant backing from NVIDIA's voice AI research. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 552 | 18,574 | A Qwen3.5 MoE-based code-specialist model designed for software development tasks. Its code-focused fine-tuning and solid engagement suggest growing demand for open coding assistants. |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 211 | 5,651 | Mistral's guardrail model for content moderation and safety classification, optimized for vLLM deployment. It addresses the growing need for reliable open-weight safety filtering. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,076 | 4,947,943 | A ComfyUI-ready single-file port of MiniMax-H3, achieving nearly 5 million downloads — the highest in the digest. It proves that accessibility through workflow integrations can dramatically expand a model's reach. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 629 | 188,761 | An Unsloth-optimized GGUF quantization of DeepSeek-V4-Flash, enabling fast local inference on consumer hardware. Strong downloads reflect sustained appetite for efficient DeepSeek variants. |
| [realrebelai/MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 188 | 160,747 | Community GGUF quantizations of MiniMax-H3 for ComfyUI, targeting lower-VRAM deployment. Over 160K downloads indicate significant local-inference demand for video generation models. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,808 | 2,390,692 | A heavily community-tuned GGUF variant of Qwen3.6-27B, combining multiple fine-tuning techniques and uncensored adaptations. Massive downloads reflect the robust market for customized open-weight LLMs. |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF) | LuffyTheFox | 455 | 396,282 | An uncensored Hermes-style GGUF fine-tune of the 35B Qwen3.6 MoE, blending multiple community techniques. Strong downloads show continued demand for unrestricted large open-weight models. |
| [Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot](https://huggingface.co/Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot) | Abiray | 155 | 511,473 | A multi-precision quantization suite for MiniMax-H3 supporting NVFP4, INT4, and INT8 with ConvRot optimizations. Over 500K downloads highlight the push toward run-time efficient video generation. |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 418 | 0 | A ComfyUI-compatible INT8-quantized variant of Qwen3-VL-32B with Heretic and ConvRot adaptations. Zero downloads suggest it was recently uploaded and has not yet been pulled. |
| [sakamakismile/Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4](https://huggingface.co/sakamakismile/Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4) | sakamakismile | 143 | 0 | An NVFP4-quantized text encoder combining Qwen3-VL and MiniMax-H3 components for ComfyUI workflows. Still zero downloads — a niche but technically ambitious integration. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 547 | 0 | A Turbo LoRA adapter for MiniMax-H3 targeting faster text-to-video generation. Notable like-to-download ratio suggests strong anticipation despite zero downloads so far. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 235 | 6,117 | A distilled "Turbo" variant of MiniMax-H3 focused on accelerated image-to-video synthesis. Modest but steady adoption points to growing demand for faster video generation. |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 232 | 0 | A ComfyUI-adapted Turbo LoRA for MiniMax-H3 with pruning optimizations. Zero downloads indicate a recent or niche release within the ComfyUI video-generation community. |
| [SexGod1979/PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 231 | 0 | An Apache-2.0 licensed text-to-video fine-tune of MiniMax-H3 with endpoint compatibility. Still un-pulled but notable for its permissive licensing in a space dominated by restrictive models. |
| [Kijai/MiniMax-H3_comfy](https://huggingface.co/Kijai/MiniMax-H3_comfy) | Kijai | 236 | 0 | A US-region ComfyUI wrapper for MiniMax-H3 from a well-known diffusion community contributor. Zero downloads suggest recent publication, but Kijai's reputation may drive future adoption. |
| [Kijai/MiniMax-H3-experimental](https://huggingface.co/Kijai/MiniMax-H3-experimental) | Kijai | 170 | 0 | An experimental ComfyUI variant exploring novel MiniMax-H3 configurations. Still early-stage with zero downloads, but worth monitoring for innovative workflow approaches. |
| [LiquidAI/LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 175 | 68,468 | GGUF-quantized version of LiquidAI's LFM2.5-2.6B, enabling efficient llama.cpp inference. A solid companion release for developers seeking to run the model on CPU or low-VRAM GPUs. |

---

## 3. Ecosystem Signal

The most dominant ecosystem signal this week is the **MiniMax-H3 video generation family**, which has spawned over a dozen community adaptations spanning GGUF quantizations, LoRA adapters, ComfyUI integrations, and Turbo distillations. This mirrors the pattern seen with earlier diffusion models — a strong base release catalyzing a rich secondary ecosystem. Similarly, **DeepSeek-V4-Flash** continues to see aggressive quantization activity, particularly through Unsloth's GGUF pipeline, reinforcing the trend toward efficient local inference.

**Chinese model families** (DeepSeek, GLM, Kimi, Qwen3.x, MiniMax) are gaining significant momentum, reflecting both technical competitiveness and strong community adoption. The open-weight movement remains robust: even models from well-funded labs like DeepSeek and Moonshot are released with permissive-enough weights to sustain massive fine-tuning cultures.

**Quantization innovation** is a standout theme — NVFP4, INT4/INT8 hybrid schemes, and ConvRot optimizations are pushing the boundary of what can run on consumer hardware. The uncensored/fine-tune community continues to be highly active around Qwen3.6 variants, indicating sustained demand for customized open-weight LLMs. Meanwhile, specialized models like Shieldstral and KAT-Coder signal growing maturity in safety and coding niches.

---

## 4. Worth Exploring

1. **moonshotai/Kimi-K3** — With over 10,000 likes and 1.4M downloads, it's the most-liked model this week and represents the current frontier in open multimodal vision-language capability. Its compressed-tensors support also makes it worth studying for efficient deployment strategies.

2. **Comfy-Org/MiniMax-H3** — Nearly 5 million downloads make it the most-downloaded model in the digest by a wide margin. It's a masterclass in how ComfyUI integration can dramatically expand a model's accessibility and adoption beyond its original diffusion-based audience.

3. **SyzygyResearch/Mach-1-Additive-35B** — The ternary additive quantization approach is a genuinely novel research direction in model compression. Even with modest current adoption, it deserves attention from anyone tracking the next generation of extreme quantization techniques that could make 35B+ models runnable on modest hardware.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*