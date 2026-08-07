# Hugging Face Trending Models Digest 2026-08-07

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-07 02:56 UTC

---



# Hugging Face Trending Models Digest
**Date:** 2026-08-07

---

## 1. Today's Highlights

The MiniMax-H3 image-to-video model dominates this week's leaderboard, spawning an entire ecosystem of ComfyUI integrations, LoRA adapters, and quantized variants — a rare display of community velocity around a single release. Meanwhile, DeepSeek's V4 Flash lineup continues to rack up massive download numbers, with both the base and July 31 checkpoint ranking among the most-used text-generation models on the platform. GLM-5.2 from zai-org also climbs the charts with nearly 2.4 million downloads, signaling strong ongoing interest in Chinese open-weight LLMs. The week's data reinforces a clear trend: multimodal video generation and quantized open-weight LLMs are the two fastest-moving fronts in the ecosystem.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,205 | 1,258,043 | A multimodal image-text-to-text model from Moonshot AI that is the most-liked model on this week's list. Its popularity likely reflects strong benchmark performance and broad utility for vision-language tasks. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,655 | 617,900 | A July 31 checkpoint of DeepSeek's V4 Flash family, this model combines high download volume with strong community engagement for fast conversational text generation. |
| [deepseek-ai/DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 2,045 | 2,639,756 | The flagship DeepSeek V4 Flash release with over 2.6 million downloads, cementing DeepSeek's position as a leading provider of efficient open-weight LLMs. |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,875 | 2,391,730 | Zai's GLM-5.2 continues to accumulate massive adoption, reflecting strong demand for Chinese open-weight conversational models in the MoE/DPA architecture space. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 336 | 73,573 | A compact 2.6B parameter text-generation model from Liquid AI, notable for its efficiency and liquid neural architecture. |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 522 | 16,961 | A code-specialized model built on Qwen3.5 MoE architecture with vision-language capabilities for developer workflows. |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 290 | 440,176 | Microsoft's multimodal vision-language model that has seen strong adoption, combining image and text understanding for general-purpose tasks. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,934 | 2,791,862 | Baidu's OCR-focused multimodal model with nearly 2.8 million downloads, making it one of the most widely deployed vision-language models on the platform. |
| [inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 190 | 1,196 | A conversational text-generation model using the novel Bailing Hybrid architecture, still early but worth watching. |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 211 | 419 | A preview MoE model from DeepGrove with a causal language modeling objective, currently in early access. |
| [thinkingmachines/Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 326 | 22,223 | A small-scale image-text-to-text conversational model from Thinking Machines, offering efficient multimodal reasoning. |
| [XYZAILab/XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | XYZAILab | 427 | 1,570 | A mini MoE model based on the Qwen3.5/Qwen3.6 family, targeting efficient image-text-to-text tasks. |
| [EschaLabs/Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 226 | 3,394 | A quantized or specially configured variant of Qwen3.6 with MoE architecture, representing continued community interest in the Qwen3.6 family. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 2,765 | 12,102 | MiniMax's latest image-text-to-video model that has ignited a massive community fine-tuning and quantization ecosystem in a single week. |
| [black-forest-labs/FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev) | black-forest-labs | 14,014 | 523,234 | The most-liked model on the entire weekly list, FLUX.1-dev remains the gold standard for open-weight text-to-image generation with outstanding community adoption. |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 297 | 12,211 | A compact 0.6B text-to-speech model in preview form, part of the ArkTTS family for lightweight voice generation. |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 184 | 206 | NVIDIA's 11B voice chat model for conversational audio, still in early adoption but backed by NVIDIA's multimodal roadmap. |
| [lodestones/Kroma](https://huggingface.co/lodestones/Kroma) | lodestones | 208 | 0 | A ComfyUI text-to-image LoRA targeting Krea-compatible workflows, currently in early community distribution. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 164 | 1,511 | Mistral's 3B safety-shielding model designed for content moderation and alignment evaluation, part of the growing open-weight safety tooling ecosystem. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 855 | 2,295,377 | The highest-download model this week, this ComfyUI single-file packaging of MiniMax-H3 enables efficient video generation at scale. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,654 | 2,087,189 | An uncensored "Heretic" fine-tune of Qwen3.6-27B in GGUF format with MTP support, one of the most downloaded community variants this week. |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF) | LuffyTheFox | 411 | 309,149 | An uncensored Hermes-v7 fine-tune of the large Qwen3.6-35B-A3B MoE model in GGUF, targeting unrestricted conversational use. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 554 | 145,105 | Unsloth's GGUF quantization of DeepSeek V4 Flash, enabling efficient local inference with their well-known optimization stack. |
| [realrebelai/MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 157 | 65,679 | A GGUF quantization bundle for MiniMax-H3, extending the model's reach to local CPU/GPU inference workflows. |
| [Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot](https://huggingface.co/Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot) | Abiray | 112 | 272,963 | A heavily quantized MiniMax-H3 variant using NVFP4 and INT4/INT8 formats with ConvRot, pushing video generation into tighter memory budgets. |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 341 | 0 | An INT8-quantized, Heretic fine-tuned version of Qwen3-VL-32B packaged for ComfyUI with ConvRot optimizations. |
| [sakamakismile/Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4](https://huggingface.co/sakamakismile/Qwen3-VL-32B-Heretic-MiniMax-H3-NVFP4) | sakamakismile | 111 | 0 | A community fusion combining Heretic fine-tuning with MiniMax-H3 and NVFP4 quantization for the Qwen3-VL-32B backbone. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 314 | 0 | A Turbo LoRA adapter for MiniMax-H3 designed to accelerate text-to-video generation. |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 130 | 0 | A pruned, ComfyUI-packaged version of the MiniMax-H3 Turbo LoRA for streamlined local video generation. |
| [LiquidAI/LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 128 | 12,790 | The GGUF quantization of LiquidAI's compact 2.6B model, enabling llama.cpp-compatible local inference. |

---

## 3. Ecosystem Signal

This week's trending data reveals several strong ecosystem signals. **MiniMax-H3** is the standout story: a single video generation model has spawned over a dozen community packages — GGUF quantizations, NVFP4/INT8 compressions, ComfyUI integrations, and Turbo LoRAs — all within days. This kind of rapid community multiplication signals both high utility and an underserved market for efficient local video generation. **DeepSeek's V4 Flash** family maintains its dominance in open-weight text generation, with both the base and July 31 checkpoint accumulating millions of downloads, reinforcing the trend that efficient MoE architectures are the sweet spot for open LLMs. **Chinese open-weight models** (GLM-5.2, Kimi-K3, DeepSeek-V4, Qwen3.6) continue to capture disproportionate engagement, reflecting both genuine capability and a community hungry for alternatives to proprietary US models. Quantization activity is notably intense across the board — NVFP4, GGUF, INT4, and INT8 variants are proliferating — suggesting the ecosystem is actively pushing toward local, resource-constrained deployment rather than cloud-only inference.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — The most-liked model this week (10,205 likes, 1.26M downloads) is a strong signal. Kimi-K3 combines image-text understanding with a compressed-tensor format, making it both high-performing and efficient. Its community momentum suggests it has earned its rank through genuine capability, not just hype.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The epicenter of this week's activity. Even if you don't generate video, studying how the community has forked this model into 12+ variants (ComfyUI, GGUF, NVFP4, LoRA) is a masterclass in how open-weight models catalyze ecosystem growth. The parent model's 2,765 weekly likes and the Comfy-Org fork's 2.3M downloads tell the full story.

3. **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — With 4,875 likes and nearly 2.4M downloads, GLM-5.2 is the most-downloaded model this week outside of the MiniMax video ecosystem. For anyone evaluating open-weight Chinese LLMs for production or research, this is the model to benchmark against — its adoption trajectory suggests it's becoming a default choice in its size class.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*