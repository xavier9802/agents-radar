# Hugging Face Trending Models Digest 2026-08-09

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-09 02:10 UTC

---



# Hugging Face Trending Models Digest — 2026-08-09

---

## 1. Today's Highlights

MiniMax-H3 dominates the video generation space, spawning a wave of community LoRAs, ComfyUI integrations, and quantized variants — signaling a maturing ecosystem around open video models. DeepSeek-V4-Flash-0731 continues to set the bar for open-weight language models with massive download momentum, while GLM-5.2 emerges as a strong MOE-based contender. The trend toward NVFP4 and INT4/INT8 quantizations for large video and vision models is accelerating, reflecting community demand for local deployment viability.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,854 | 785,771 | A flash-tier open-weight LLM delivering strong conversational performance. Its massive download count reflects sustained developer adoption for local and deployed use cases. |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,902 | 2,480,368 | A conversational MOE model from the ZAI Org with exceptional download velocity. It's trending due to its strong benchmark performance and open-weight accessibility. |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 201 | 4,950 | A 3B safety-shield model from Mistral designed for content moderation and guardrailing. It addresses growing demand for responsible AI deployment pipelines. |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 246 | 458 | NVIDIA's open-weight voice chat model bridging LLM reasoning with conversational speech. A notable entry as voice-native models begin gaining traction. |
| [inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 222 | 4,189 | A lightweight conversational model featuring a novel bailing-hybrid architecture. It's attracting attention for its efficiency-focused design approach. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,970 | 2,857,997 | Baidu's high-accuracy OCR model with strong multilingual support. Its nearly 3M downloads make it one of the most-used vision-language models on the platform. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,111 | 26,693 | A high-quality image-text-to-video model establishing a new open benchmark. Its rapid community uptake is driving an entire ecosystem of fine-tunes and adapters. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,343 | 1,388,105 | Kimi's latest multimodal model with exceptional community engagement — the highest likes on this list. It combines strong vision-language reasoning with compressed-tensor efficiency. |
| [black-forest-labs/FLUX.1-dev](https://huggingface.co/black-forest-labs/FLUX.1-dev) | black-forest-labs | 14,038 | 502,330 | The flagship open-weight text-to-image model from the original Stable Diffusion team. It remains the gold standard for photorealistic image generation quality. |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 324 | 12,837 | A compact 0.6B text-to-speech model with strong naturalness for its size. It represents the growing trend of lightweight, high-quality voice synthesis. |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 314 | 457,581 | Microsoft's multimodal vision-language model with broad feature extraction support. It's gaining use in production pipelines requiring reliable image-text reasoning. |
| [thinkingmachines/Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 346 | 28,178 | A compact conversational vision-language model optimized for efficiency. It targets edge and resource-constrained multimodal deployment scenarios. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 544 | 17,885 | A code-specialized model built on Qwen3.5 MoE architecture with vision capabilities. It targets developers seeking open-weight coding assistants with multimodal input support. |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 255 | 896 | A preview mixture-of-experts model showcasing efficient sparse activation patterns. Early interest reflects curiosity about MoE scaling behavior in open models. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,007 | 3,943,176 | The most-downloaded ComfyUI-integrated version of MiniMax-H3, enabling local video generation workflows. Its 3.9M+ downloads demonstrate massive community infrastructure investment. |
| [Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot](https://huggingface.co/Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot) | Abiray | 143 | 471,519 | A quantized MiniMax-H3 variant using NVFP4 and INT4/INT8 mixed precision with ConvRot optimizations. It enables running large video models on consumer GPUs. |
| [realrebelai/MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 176 | 128,265 | GGUF-quantized MiniMax-H3 weights for llama.cpp and compatible inference engines. Extends MiniMax-H3 accessibility beyond the diffusers ecosystem. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 608 | 175,093 | SFAST-optimized GGUF quantizations of DeepSeek-V4-Flash for efficient local inference. Leverages Unsloth's compilation stack for significant speedups. |
| [LiquidAI/LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 157 | 49,562 | GGUF quantization of LiquidAI's novel LFM2.5 architecture for llama.cpp deployment. Bridges LiquidAI's experimental architecture with established inference tooling. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,761 | 2,345,190 | An uncensored community fine-tune of Qwen3.6-27B with extensive optimization tags. High download volume reflects demand for unrestricted open-weight LLMs. |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V7-GGUF) | LuffyTheFox | 438 | 373,651 | An uncensored Hermes-style fine-tune of the Qwen3.6-35B MoE model in GGUF format. Combines the Hermes instruction-tuning lineage with uncensored open weights. |

---

## 3. Ecosystem Signal

The MiniMax-H3 model family is the dominant ecosystem signal this week, with the base release spawning over a dozen community adaptations spanning LoRAs, ComfyUI wrappers, and aggressive quantizations (NVFP4, INT4/INT8). This pattern — a strong open-weight foundation enabling a rich fine-tune ecosystem — mirrors the FLUX.1-dev trajectory and indicates that open video generation is reaching a maturity inflection point. DeepSeek continues to solidify its position as the leading open-weight LLM provider, with both raw releases and Unsloth-optimized GGUF variants driving enormous download volumes. The NVFP4 quantization trend is particularly notable: it represents the bleeding edge of mixed-precision optimization for large models, making 30B+ video and vision models viable on consumer hardware. Community fine-tune activity remains heavily concentrated around uncensored and instruction-tuned variants of Qwen3.6, suggesting sustained demand for unrestricted conversational models. Open-weight dominance persists across both LLM and multimodal categories, with proprietary-only models notably absent from the top 30.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — With 10,343 likes (the highest on the list) and 1.3M+ downloads, it's the clear community favorite. Its compressed-tensor support and strong multimodal performance make it essential studying for anyone building vision-language pipelines.

2. **[Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot](https://huggingface.co/Abiray/Minimax-H3-nvfp4-INT4-INT8-Convrot)** — At 471K downloads, this is the standout quantization to watch. NVFP4 + ConvRot is pushing the envelope on what's runnable locally, and understanding this approach will be valuable as video models continue to scale.

3. **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — With nearly 2.5M downloads and strong like counts, GLM-5.2 is rapidly becoming a top-tier open conversational model. Its MoE architecture and competitive benchmarks make it a compelling alternative to DeepSeek for production deployments.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*