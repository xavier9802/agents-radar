# Hugging Face Trending Models Digest 2026-08-25

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-25 01:39 UTC

---



# 🤗 Hugging Face Trending Models Digest — 2026-08-25

## 1. Today's Highlights

Qwen3.8-27B dominates the weekly charts with over 12,500 likes and 2.6M downloads, commanding a wide ecosystem of quantized and abliterated community variants. DeepSeek-V4-Flash-0731 continues its rapid ascent with 3.2M downloads, while Kimi-K3 earns strong community interest with nearly 11K likes. The video generation space heats up with MiniMax-H3 pulling 4.5M downloads and LTX-2.5 pushing diffusion-based image-to-video forward. Meanwhile, Ornith's 35B-A3B MoE architecture signals growing momentum in sparse mixture-of-experts design outside the Qwen family.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 12,517 | 2,645,226 | The flagship Qwen3.8 model in its native 27B parameter configuration, supporting image-text-to-text conversational pipelines. It leads the charts driven by strong benchmark performance and broad community adoption. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,682 | 3,274,129 | DeepSeek's V4 Flash release, optimized for fast inference without sacrificing conversational quality. Its 3.2M downloads reflect strong enterprise and open-source community traction. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,973 | 2,787,971 | Moonshot AI's K3 multimodal model using compressed-tensors for efficient deployment. With nearly 11K likes, it stands out as one of the most liked models on the list despite a slightly smaller download base than DeepSeek. |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 398 | 60,294 | An Ornith 1.5 mixture-of-experts model with 35B total and 3B active parameters, supporting image-text-to-text. Its MoE design offers an efficient alternative to dense 27B models in the open-weight space. |
| [ornith-ai/Ornith-1.5-9B](https://huggingface.co/ornith-ai/Ornith-1.5-9B) | ornith-ai | 204 | 83,192 | The lighter 9B Ornith variant, offering a compact option for resource-constrained deployments while retaining image-text understanding. |
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 214 | 50,763 | Applies DFlash2 speculative decoding to Qwen3.8-27B, aiming to accelerate inference speed with minimal quality loss. |
| [incoai/Qwen3.8-27B-DFlash2](https://huggingface.co/incoai/Qwen3.8-27B-DFlash2) | incoai | 173 | 85,034 | Another DFlash2 speculative decoding implementation on Qwen3.8-27B from incoai, showing community experimentation with decoding acceleration. |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 230 | 2,976 | A small Qwen3-based model with an ASR (automatic speech recognition) pipeline, targeting lightweight speech-to-text applications. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,418 | 4,465,161 | MiniMax's video generation model supporting text-to-video, image-to-video, and video-to-video pipelines with 4.5M downloads. It is one of the most downloaded generative models on the list, signaling strong demand for open video generation. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,725 | 790,378 | A diffusion-based image-to-video model from Lightricks, supporting text, image, and video conditioning. Its 790K downloads reflect sustained interest in high-quality open video generation. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,228 | 18,065 | MiniMax's third-generation text-to-music model, generating audio from textual descriptions using the diffusers pipeline. Its dedicated focus on music generation fills a niche in the open generative audio space. |
| [Audio8/Audio8-TTS-Preview-0.1b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.1b) | Audio8 | 146 | 2,775 | A tiny 0.1B text-to-speech model from Audio8, targeting efficient and lightweight speech synthesis. |
| [LBH-123-AI/Minimax_h3_latent_Upscaler](https://huggingface.co/LBH-123-AI/Minimax_h3_latent_Upscaler) | LBH-123-AI | 181 | 0 | A latent upscaler designed to complement MiniMax-H3, enabling higher-resolution video output from the base model. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,447 | 0 | Provides corrected Jinja chat templates for Qwen 3.5 models in the MLX format, addressing common formatting issues in local deployments. |
| [peculiar-ragdoll/Qwen-Sharp-Chat-Templates](https://huggingface.co/peculiar-ragdoll/Qwen-Sharp-Chat-Templates) | peculiar-ragdoll | 230 | 0 | Another MLX-compatible Jinja chat template collection for Qwen 3.5, focused on sharper, more precise instruction following. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,839 | 7,009,063 | Unsloth's GGUF quantization of Qwen3.8-27B, optimized for fast local inference via llama.cpp. With 7M downloads it is the most downloaded model on the list, underscoring the critical role of quantization in open-weight adoption. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 681 | 3,004,940 | The official FP8 quantized variant of Qwen3.8-27B from Qwen, offering reduced memory footprint while preserving conversational quality. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,030 | 57,947 | An abliterated (uncensored) MLX port of Qwen3.8-27B, removing alignment filters for unrestricted local use on Apple Silicon. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 696 | 312,627 | Another abliterated variant in GGUF and safetensors formats, continuing the community trend of unaligned Qwen3.8 releases. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,098 | 224,114 | Combines abliterated uncensored training with FP8 quantization, offering both unrestricted output and reduced VRAM requirements. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 580 | 761,975 | An aggressive MTP (multi-token prediction) fine-tune with abliterated alignment in GGUF format, pushing throughput on uncensored Qwen3.8. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 690 | 1,456,700 | A popular uncensored GGUF conversion with MTP support, reaching 1.4M downloads among local inference users. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 424 | 143,108 | orcarouter's GGUF quantization of their abliterated Qwen3.8-27B model, targeting llama.cpp compatibility. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 335 | 1,140,375 | A widely downloaded abliterated GGUF variant from huihui-ai, combining uncensored alignment with efficient quantization. |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 226 | 209,017 | Applies Cold-Fusion GAIN training with MTP acceleration to Qwen3.8-27B, representing advanced community fine-tuning experimentation. |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 275 | 988,170 | GGUF quantization of Ornith's 35B-A3B MoE model, enabling efficient local deployment of the sparse architecture. |
| [ornith-ai/Ornith-1.5-9B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-9B-GGUF) | ornith-ai | 187 | 971,104 | GGUF quantization of the 9B Ornith variant, achieving nearly 1M downloads for a compact open-weight option. |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 260 | 654,805 | A "Heretic" abliterated GGUF build targeting users seeking maximally unrestricted Qwen3.8 inference. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 278 | 27,316 | The safetensors (non-quantized) version of huihui-ai's abliterated Qwen3.8-27B, for users preferring full-precision weights. |
| [orcarouter/Qwen3.8-27B-Uncensored](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored) | orcarouter | 170 | 10,482 | The base safetensors uncensored release from orcarouter, preceding their various quantized variants. |

---

## 3. Ecosystem Signal

The Qwen3.8 family overwhelmingly dominates this week's trends, anchoring nearly half of all listed models through official, quantized, and community-finetuned variants. DeepSeek and Kimi maintain strong competitive presence, with DeepSeek-V4-Flash-0731 leading in raw download volume (3.2M) and Kimi-K3 excelling in community engagement (11K likes). A defining ecosystem trend is the massive wave of abliterated/uncensored fine-tunes built on Qwen3.8-27B — over a dozen community variants exist, each removing alignment restrictions for unrestricted local deployment. Quantization activity is equally intense: GGUF conversions from Unsloth, JonathanColetti, and huihui-ai collectively account for over 9M downloads, demonstrating that efficient local inference remains the primary deployment bottleneck. Open-weight models continue to drive the ecosystem, with proprietary models like Kimi and DeepSeek Flash coexisting alongside a thriving community of remixers. Speculative decoding (DFlash2) and MoE architectures (Ornith) represent emerging optimization fronts, while video generation sees rapid iteration with MiniMax-H3 and LTX-2.5 pushing quality and accessibility forward.

---

## 4. Worth Exploring

1. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — With 7M downloads, this is the most-downloaded model on the list. Unsloth's quantization expertise ensures excellent performance-per-watt on consumer hardware, making it the default choice for local deployment study.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — At 4.5M downloads, it demonstrates that open video generation models are reaching production-scale adoption. Its multi-modal pipeline (text, image, and video conditioning) makes it a valuable reference for generative video research.

3. **[ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B)** — Ornith's MoE design with 35B total / 3B active parameters offers a compelling efficiency trade-off worth studying as an alternative to dense architectures. Its GGUF variant alone has nearly 1M downloads, confirming real-world viability.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*