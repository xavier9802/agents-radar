# Hugging Face Trending Models Digest 2026-09-06

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-09-06 04:06 UTC

---



# 🤗 Hugging Face Trending Models Digest
**Date:** 2026-09-06 | **Models:** 30 tracked | **Sorted by:** Weekly Likes

---

## 1. Today's Highlights

DeepSeek's experimental **V4-Flash-Vision** multimodal model leads the榜 with 684 weekly likes, signaling the company's continued push into high-efficiency vision-language reasoning. **Qwen3.8-27B** dominates overall downloads (6M+) and remains the most-copied open-weight model in the ecosystem, while a wave of community **uncensored/abliterated GGUF variants** (8 entries) reflects sustained demand for unrestricted local deployment. The video generation space sees momentum with **MiniMax-H3** maintaining near-5K likes and **LTX-2.5** offering a streamlined diffusion pipeline. Quantization activity is at an all-time high — three separate **unsloth** and **ISTA-DASLab** releases push mixed-precision GGUF to new sizes.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 684 | 184,542 | DeepSeek's experimental vision-language model targeting high-efficiency image-text reasoning. The "Flash" variant suggests optimized inference, driving rapid community adoption. |
| [Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 14,044 | 6,024,467 | The flagship open-weight multilingual model with 27B parameters, supporting both text and vision. Its enormous download count reflects it as the de facto standard for local deployment. |
| [Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,918 | 401,327 | A faster inference variant of Qwen3.8, optimized for lower latency while retaining 27B-capacity performance. Gaining traction among developers prioritizing speed. |
| [GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,080 | 727,610 | ZAI's flash-optimized multimodal model, building on the GLM-5.3 base with accelerated inference. Strong download-to-like ratio indicates serious production use. |
| [GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,720 | 370,417 | The full-parameter base model from the GLM-5 series, supporting text and vision pipelines. Serves as the foundation for the Flash variant above. |
| [Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 551 | 4,755 | A compact 4B parameter model from the Spark family, targeting resource-constrained environments. Modest but steady engagement suggests niche deployment interest. |
| [Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 443 | 6,195 | Tencent's Hunyuan preview model, representing the company's next-generation language architecture. Early access status is generating community anticipation. |
| [K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 175 | 1,333 | A large 36B-parameter model from IFM's Horizon series, targeting high-complexity reasoning tasks. Low download count suggests it's still in early discovery phase. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,938 | 5,057,414 | MiniMax's flagship image-to-video and text-to-video generation model with 5M+ downloads. Its dual modality support and strong engagement make it a video-gen standout. |
| [LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,894 | 1,484,329 | Lightricks' diffusion-based video generation pipeline offering image-to-video, text-to-video, and video-to-video in a single file. Practical for creative workflows. |
| [Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 449 | 5,962 | A text-to-speech model from the Breeze family, targeting natural voice synthesis. Modest but growing community interest in accessible TTS solutions. |
| [timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 460 | 123,025 | Google's time-series forecasting model, applying transformer architectures to temporal prediction. Growing adoption in analytics and operations research communities. |
| [vdn-minimax-h3](https://huggingface.co/OpenVDN/vdn-minimax-h3) | OpenVDN | 191 | 0 | A variant of MiniMax-H3 optimized for video generation pipelines. Zero downloads suggest it's newly released or awaiting community testing. |
| [FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 279 | 22,851 | A distilled 4-step inference variant of MiniMax-H3, trading quality for speed. Appeals to developers needing faster video generation without full retraining. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,560 | 255,006,933 | The most-downloaded embedding model in the list with 255M+ downloads. Industry standard for sentence similarity and semantic search applications. |
| [gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,702 | 14,739,982 | OpenAI's foundational text-generation model, still widely used for legacy compatibility and educational purposes. Maintains strong historical relevance. |
| [bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,986 | 56,175,564 | Google's classic masked-language-model architecture with 56M+ downloads. Remains a backbone for NLP pipelines and fine-tuning workflows. |
| [clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,210 | 20,755,211 | OpenAI's vision-language embedding model enabling zero-shot image classification. Foundational for multimodal retrieval and cross-modal applications. |
| [distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,156 | 7,101,423 | A lighter distillation of BERT offering ~40% faster inference with minimal accuracy loss. Popular choice for production NLP deployments. |
| [mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 263 | 12,961 | Meta's multilingual speech model covering 100+ languages. Growing interest in low-resource speech synthesis and transcription use cases. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,548 | 10,157,510 | Unsloth's GGUF-quantized version of Qwen3.8-27B with 10M+ downloads — the most-copied quantized model in the list. Enables efficient local inference. |
| [Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 800 | 780,823 | Unsloth's quantized variant of the Flash-Next model, balancing speed and quality for deployment. Strong adoption among efficiency-focused users. |
| [Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 418 | 297,493 | ISTA-DASLab's mixed-precision GGUF release using GSQ and RCO techniques. Academic-grade quantization targeting best-in-class compression ratios. |
| [Qwopus3.8-27B-Flash-GGUF](https://huggingface.co/Jackrong/Qwopus3.8-27B-Flash-GGUF) | Jackrong | 120 | 10,680 | A community GGUF build combining Qwen3.8 and Flash optimizations. Niche but demonstrates active community experimentation. |
| [Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 966 | 1,527,627 | An uncensored fine-tune with aggressive MTP (multi-token prediction) optimization. High downloads reflect demand for unrestricted local models. |
| [Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,096 | 968,936 | The "abliterated" variant removing safety alignment from Qwen3.8. Strong engagement indicates significant community interest in unrestricted versions. |
| [Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 988 | 2,453,361 | JonathanColetti's uncensored GGUF release with 2.4M+ downloads. One of the most popular community fine-tunes in the list. |
| [Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 729 | 283,774 | Another abliterated variant from orcarouter, contributing to the ecosystem's uncensored model diversity. |
| [Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 240 | 106,845 | Flash-Next base with uncensored removal, serving users who want both speed and unrestricted output. |
| [Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 227 | 174,405 | A heavily branded uncensored fine-tune with MTP and coder optimizations. Long model name reflects community naming conventions. |

---

## 3. Ecosystem Signal

The open-weight model ecosystem is consolidating around three dominant families: **Qwen3.8**, **DeepSeek V4**, and **GLM-5**. Qwen3.8-27B alone accounts for over 17 million combined downloads across its base, Flash, and quantized variants — an unprecedented concentration of community activity. **Quantization** is the clear meta-trend: GGUF releases dominate the fine-tune category, with unsloth leading efficiency optimizations and ISTA-DASLab pushing academic mixed-precision techniques. The **"uncensored/abliterated" movement** is especially notable, with 6 community variants collectively attracting 5.5M+ downloads, reflecting sustained demand for unrestricted local deployment. Meanwhile, **video generation** is heating up — MiniMax-H3 and LTX-2.5 demonstrate that open models are closing the gap with proprietary offerings. The **DeepSeek** family's experimental flash variants suggest a strategic shift toward efficiency-first architectures. Notably, **open-weight models now capture the majority of top download metrics**, indicating the community's preference for local, customizable deployments over API-dependent solutions.

---

## 4. Worth Exploring

1. **[DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp)** — DeepSeek's experimental vision-language model represents the cutting edge of multimodal efficiency. Its rapid uptake (184K downloads in one week) signals strong developer interest in flash-optimized reasoning.

2. **[LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5)** — Lightricks' single-file diffusion pipeline is unique in supporting image-to-video, text-to-video, and video-to-video natively. With 1.4M downloads, it's becoming a practical choice for creative workflows without heavy infrastructure.

3. **[all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)** — At 255M downloads, this remains the backbone of semantic search and embedding pipelines. Any developer building retrieval-augmented or similarity-based systems should have this in their toolkit.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*