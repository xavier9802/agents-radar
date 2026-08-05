# Hugging Face Trending Models Digest 2026-08-05

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-05 03:13 UTC

---



# 🤗 Hugging Face Trending Models Digest
**Date: 2026-08-05**

---

## 1. Today's Highlights

DeepSeek's **V4-Flash** family dominates the top spots, with both the original and a dated checkpoint ranking in the top 5 by weekly likes, signaling sustained community appetite for efficient open-weight language models. **moonshotai's Kimi-K3** leads all models with over 10,000 likes and 1.1 million downloads, establishing itself as the week's standout multimodal language model. Meanwhile, MiniMaxAI's **H3** emerges as the first image-text-to-video model on the leaderboard, marking a notable expansion of open video generation capabilities. Community fine-tuning remains fierce around the **Qwen3.6** family, with at least four uncensored and GGUF variants racking up massive download counts.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 2,320 | 433,284 | The July 31 checkpoint of DeepSeek's V4-Flash continues to attract strong engagement. Its efficient architecture and conversational pipeline make it a top choice for self-hosted deployments. |
| [deepseek-ai/DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 2,011 | 2,737,621 | The original V4-Flash remains hugely popular with over 2.7M downloads. It offers a lightweight, high-performance text-generation pipeline for production use. |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,821 | 2,234,662 | GLM-5.2 leads the Chinese-language model niche with nearly 5,000 likes and 2.2M downloads. Its MoE DSA architecture delivers strong conversational performance at scale. |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 920 | 82,912 | Poolside's Laguna-S 2.1 stands out in the mid-tier LLM space with strong weekly engagement. It targets reliable text generation with a clean transformer pipeline. |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 665 | 37,256 | A compact 3B parameter model gaining traction for resource-constrained deployments. Its Efficient LLM design offers a compelling on-device option. |
| [EschaLabs/Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 195 | 2,987 | A specialized fine-tune of the Qwen3.6 MoE family targeting improved instruction following. Early downloads suggest interest in its agentic capabilities. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 163 | 47,393 | LiquidAI's LFM2.5 brings continuous-time modeling to a 2.6B parameter text generator. It offers a novel architectural approach for edge-friendly inference. |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 475 | 15,381 | A Qwen3.5 MoE-based coder model with strong dev-toolkit integration. It bridges code generation and multimodal understanding for software workflows. |
| [XYZAILab/XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | XYZAILab | 404 | 1,317 | The "mini" variant of XYZAI's Aquila line offers a lighter Qwen3.6 MoE model for faster inference. Early adoption signals interest in its agentic search features. |
| [XYZAILab/XYZ-Aquila-pro](https://huggingface.co/XYZAILab/XYZ-Aquila-pro) | XYZAILab | 358 | 1,388 | The full-sized counterpart to Aquila-mini, targeting production workloads with agentic search capabilities. Both variants share the Qwen3.5 MoE backbone. |
| [LGAI-EXAONE/K-EXAONE-2.0-750B-A37B](https://huggingface.co/LGAI-EXAONE/K-EXAONE-2.0-750B-A37B) | LGAI-EXAONE | 117 | 325 | LG AI's massive 750B MoE model represents the high-end of Korean-language open-weight research. Its sparse activation design enables large-scale reasoning. |
| [nota-ai/Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 174 | 69,253 | Solar Open2 in NVFP4 quantization targets vLLM-compatible high-throughput serving. Its 250B parameter scale makes it a serious open-weight competitor. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 2,050 | 0 | MiniMax's H3 is the week's most-liked image-text-to-video model, pioneering open video generation. Its debut generated significant buzz despite 0 recorded downloads (newly listed). |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,016 | 1,125,935 | Kimi-K3 leads the entire chart with over 10,000 likes and 1.1M downloads. Its image-text-to-text pipeline and compressed-tensor support make it a top multimodal choice. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,882 | 2,703,366 | Baidu's Unlimited-OCR is a heavyweight vision-language model for document and text recognition. With 2.7M downloads, it's a go-to for production OCR pipelines. |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 257 | 435,784 | Microsoft's multimodal VL model brings strong image-text understanding to the open ecosystem. Its 435K downloads reflect solid community adoption for vision-language tasks. |
| [thinkingmachines/Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 286 | 15,500 | A smaller vision-language model targeting efficient image-text understanding. Its compact size makes it attractive for edge and low-latency applications. |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 249 | 11,276 | A lightweight 0.6B parameter text-to-speech model with promising preview quality. Its compact footprint enables local TTS generation on consumer hardware. |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 410 | 2,072 | An ultra-compact CPU-friendly TTS model built for edge AI deployment. Its small size enables real-time speech synthesis without GPU dependency. |
| [lodestones/Kroma](https://huggingface.co/lodestones/Kroma) | lodestones | 176 | 0 | A Krea-powered text-to-image model distributed as a ComfyUI LoRA. Early interest is building despite 0 downloads (newly listed). |
| [realrebelai/MiniMax-H3_GGUFs](https://huggingface.co/realrebelai/MiniMax-H3_GGUFs) | realrebelai | 104 | 40,010 | A GGUF-quantized adaptation of MiniMax-H3, enabling local video generation. It bridges the gap between the original model and accessibility. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 475 | 15,381 | A code-specialized model built on Qwen3.5 MoE, targeting developer workflows. Its integration of image-text understanding adds versatility for diagram and UI code tasks. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,516 | 1,633,405 | The highest-downloaded fine-tune on the list, offering an uncensored Qwen3.6 27B in GGUF format with MTP support. Its Heretic-style training and Unsloth optimization make it a community favorite. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,296 | 1,930,898 | An aggressive uncensored fine-tune of the Qwen3.6 35B MoE with vision support. With 1.9M downloads and 3,296 likes, it's one of the most popular community variants this week. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 474 | 111,678 | Unsloth's GGUF conversion of DeepSeek V4-Flash enables efficient local inference. The Unsloth optimization stack ensures fast loading and low memory footprint. |
| [unsloth/Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 304 | 170,055 | A GGUF-quantized version of Kimi-K3, bringing the top-ranked model to local deployment. It preserves the compressed-tensor efficiency of the base model. |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 364 | 308,857 | A Hermes-style uncensored GGUF fine-tune of Qwen3.6's 35B MoE architecture. Its V6 iteration and Genesis training recipe have attracted dedicated community adoption. |
| [DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 266 | 323,116 | A smaller 9B variant of DavidAU's Fable-Fusion series, using I-Matrix MAX and MTP techniques. It offers a balance between capability and local deployability. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 619 | 2 | A ComfyUI-native packaging of MiniMax-H3 for direct pipeline integration. Its "base_model" and "finetune" tags indicate support for both variants. |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-MiniMax-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-MiniMax-H3-ComfyUI-INT8-ConvRot) | ethanfel | 190 | 0 | A custom ComfyUI INT8 quantization fusing Qwen3-VL 32B with MiniMax-H3 techniques. Its ConvRot innovation targets memory-efficient multimodal generation. |

---

## 3. Ecosystem Signal

The current landscape is defined by the **Qwen3.6 family**, which dominates the fine-tune and quantization space with at least four community variants across 9B, 27B, and 35B sizes. Uncensored "Heretic" and "Hermes" style models account for the highest download volumes, reflecting persistent demand for unrestricted local LLMs. DeepSeek's **V4-Flash** series shows remarkable staying power, with both base and GGUF variants maintaining top-tier engagement—likely driven by Unsloth's optimized conversions lowering inference barriers. **Kimi-K3** represents a major shift toward open multimodal language models, proving that compressed-tensor and feature-extraction pipelines can rival proprietary offerings. On the generation side, **MiniMax-H3** marks the first video-generation entry on the leaderboard, hinting at an opening in the open video model space. Quantization activity remains intense, with GGUF and INT8 variants consistently bridging the gap between cutting-edge research and local deployment. The 750B ExaOne and 250B Solar Open2 signals that the parameter arms race continues among open-weight providers, even as the community increasingly favors efficient, fine-tunable smaller models.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — The most-liked model on the board with 10,000+ likes and 1.1M downloads. Its compressed-tensor support and image-text-to-text pipeline make it a compelling open alternative for multimodal reasoning. Worth studying for its efficiency innovations.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — A landmark entry as the first image-text-to-video model on the trending list. As open video generation matures, this model could define the baseline for community-driven video synthesis workflows.

3. **[DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF)** — With 1.6M downloads, it's the most-downloaded fine-tune this week. Its combination of MTP (multi-token prediction), I-Matrix quantization, and Unsloth optimization makes it a model for understanding how the community pushes open LLMs to their practical limits.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*