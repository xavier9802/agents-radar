# Hugging Face Trending Models Digest 2026-09-08

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-09-08 04:06 UTC

---



# 🤗 Hugging Face Trending Models Digest — September 8, 2026

## 1. Today's Highlights

The Qwen3.8 family continues to dominate, with multiple variants — from the base 27B model to Flash-Next and several community GGUF quantizations — collectively accounting for tens of millions of downloads this week. GLM-5.3 makes a strong showing alongside its Flash variant, while MiniMax-H3 cements itself as the leading open image-to-video model with nearly 5 million downloads. Meanwhile, specialized fine-tunes such as abliterated and uncensored variants of Qwen3.8 and GLM-5.3 reflect sustained community interest in removing alignment restrictions for research and deployment use cases.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 14,286 | 6,416,358 | The flagship Qwen3.8 open-weight LLM, this 27B multimodal model supports image-text-to-text conversation and continues to be the most-liked model on this week's list. Its massive download count reflects broad adoption across research and production pipelines. |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,983 | 474,693 | A next-generation flash variant of Qwen3.8, optimized for faster inference while retaining strong conversational and vision capabilities. It is rapidly gaining traction as a more efficient drop-in replacement for the base 27B model. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,137 | 784,005 | The accelerated GLM-5.3 variant offering improved throughput for image-text-to-text tasks. Its momentum signals strong community interest in faster GLM-series models for production deployment. |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,753 | 442,064 | The base GLM-5.3 text-generation model, featuring MoE architecture with DSA attention for efficient scaling. It remains a leading open-weight Chinese-language LLM with growing international adoption. |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 802 | 251,611 | An experimental flash vision variant from DeepSeek's V4 series, combining text generation with image understanding. Its release marks DeepSeek's continued push into efficient multimodal open-weight modeling. |
| [OpenVDN/vdn-minimax-h3](https://huggingface.co/OpenVDN/vdn-minimax-h3) | OpenVDN | 228 | 0 | A community fine-tune of MiniMax-H3 adapted for text-to-video generation using the Diffusers pipeline. Although downloads are pending, the link indicates early-stage community experimentation extending MiniMax's video capabilities. |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 749 | 7,216 | A 4B-parameter text-generation model from the Spark family, targeting efficient on-device and edge deployment. Its compact size positions it for resource-constrained production environments. |
| [IFM/K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 212 | 2,226 | A 36B open-weight language model from IFM's Horizon family, leveraging Mixture-of-Experts architecture. Early adoption suggests interest in large-scale open Chinese LLMs as alternatives to proprietary offerings. |
| [microsoft/VibeVoice-ASR-Streaming-7B](https://huggingface.co/microsoft/VibeVoice-ASR-Streaming-7B) | microsoft | 140 | 1,144 | Microsoft's streaming ASR model designed for real-time speech-to-text transcription. Its low download count reflects its niche positioning as a specialized infrastructure model for live audio pipelines. |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,716 | 14,629,637 | The legendary GPT-2 remains a cultural and educational cornerstone on the Hub, with sustained downloads decades after its release. Its continued presence reflects its role as a baseline and teaching reference. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 5,013 | 4,990,034 | The leading open image-to-video and text-to-video diffusion model, combining high-fidelity generation with strong multimodal conditioning. Nearly 5 million downloads make it the most-used generative model on this week's list. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 3,090 | 1,584,382 | Lightricks' diffusion-based video generation model supporting image-to-video, text-to-video, and video-to-video pipelines. Its single-file architecture and strong quality have driven rapid adoption in creative workflows. |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 478 | 6,754 | An upgraded text-to-speech model with improved naturalness and multilingual coverage. Its release adds to the growing ecosystem of open-weight TTS solutions competing with proprietary APIs. |
| [WarmBloodAban/Minimax-h3_Singularity](https://huggingface.co/WarmBloodAban/Minimax-h3_Singularity) | WarmBloodAban | 145 | 26,731 | A specialized fine-tune of MiniMax-H3 optimized for image-to-video generation with enhanced temporal consistency. It targets creators needing higher-quality single-image animations. |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 583 | 271,713 | Google's time-series forecasting model, now available in PyTorch, applying transformer-based architectures to multivariate forecasting tasks. It is the go-to open model for production forecasting pipelines. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,577 | 251,367,312 | The most-downloaded embedding model on the Hub by a wide margin, powering semantic search and similarity tasks across countless applications. Its ubiquity makes it the default choice for production embedding pipelines. |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,992 | 50,747,373 | The canonical BERT model remains the most-used foundational transformer for NLP research and fine-tuning workflows. Its timeless relevance underscores the enduring value of pre-trained encoder architectures. |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,156 | 7,041,011 | A distilled, faster variant of BERT retaining ~97% of its performance with 40% fewer parameters. It remains the preferred choice for latency-sensitive production deployments. |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,212 | 20,496,047 | OpenAI's foundational vision-language embedding model enabling zero-shot image classification and multimodal retrieval. Its cross-modal alignment made it the backbone for generations of multimodal systems. |
| [openbmb/MiniCPM5-2B](https://huggingface.co/openbmb/MiniCPM5-2B) | openbmb | 333 | 13 | A compact 2B-parameter LLM from the MiniCPM family, designed for on-device and edge deployment. Despite minimal downloads so far, its efficiency-first design is attracting attention for mobile and embedded use cases. |
| [facebook/mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 267 | 12,213 | Meta's Multilingual Speech Model at 300M parameters, providing self-supervised speech representations across 100+ languages. It is a key component for low-resource speech research and multilingual ASR pipelines. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,648 | 10,479,045 | The most-downloaded quantized model on the list, offering GGUF variants of Qwen3.8-27B optimized for llama.cpp inference. Unsloth's reputation for efficient quantization pipelines drives widespread community adoption. |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 571 | 403,292 | A mixed-precision GGUF quantization using Group-Scale Quantization and Rectified Codebook Optimization, achieving strong fidelity at low bit-widths. It represents the cutting edge of post-training quantization research. |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 829 | 868,243 | GGUF quantization of the Qwen3.8-Flash-Next model, enabling efficient local inference with minimal quality loss. Its popularity reflects demand for deployable flash variants on consumer hardware. |
| [nvidia/Qwen3.8-Flash-Next-NVFP4](https://huggingface.co/nvidia/Qwen3.8-Flash-Next-NVFP4) | nvidia | 142 | 18,068 | NVIDIA's FP4 quantization of Qwen3.8-Flash-Next using Model Optimizer, targeting NVIDIA GPU inference with extreme compression. It showcases the industry shift toward sub-4-bit quantization for production deployment. |
| [Jackrong/Qwopus3.8-27B-Flash-GGUF](https://huggingface.co/Jackrong/Qwopus3.8-27B-Flash-GGUF) | Jackrong | 142 | 60,343 | A community GGUF quantization combining Qwen3.8-Flash with the Qwopus fine-tune, available for llama.cpp. It targets users seeking a balanced blend of speed and capability in a single file. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 998 | 1,629,754 | An aggressively fine-tuned uncensored GGUF variant of Qwen3.8-27B with MTP training, removing refusal behaviors. It is the highest-liked uncensored model on this week's list, reflecting sustained demand. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 794 | 292,633 | Another abliterated GGUF variant of Qwen3.8-27B, removing alignment-related refusal patterns for unrestricted use. It joins a growing cohort of community "unlocked" models for research and creative applications. |
| [DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 305 | 258,896 | A heavily modified uncensored fine-tune with MTP, targeting coding and creative tasks with removed safety filters. Its lengthy name signals an aggressive stacking of community modifications on the Qwen3.8 base. |
| [dealignai/GLM-5.3-CYBERSECURITY-FP8](https://huggingface.co/dealignai/GLM-5.3-CYBERSECURITY-FP8) | dealignai | 277 | 18,602 | An abliterated FP8 quantization of GLM-5.3 tuned for cybersecurity applications, removing refusal behaviors. It targets red-team and security research workflows where standard alignment layers would be counterproductive. |

---

## 3. Ecosystem Signal

The dominant ecosystem trend this week is the **Qwen3.8 family's gravitational pull** — the base model, its Flash-Next variant, and a swarm of community GGUF quantizations collectively represent tens of millions of downloads. This mirrors a broader pattern where a single strong open-weight base becomes the nucleus for an entire quantization ecosystem. **GLM-5.3** is emerging as a credible rival, particularly in the Chinese-language LLM space, with both its base and Flash variants gaining significant traction.

On the **quantization front**, GGUF remains the standard for community distribution, but NVIDIA's NVFP4 entry signals a shift toward hardware-aware sub-4-bit formats for production inference. The **uncensored/abliterated segment** is notably active, with at least four major models stripping alignment refusals — a persistent demand from researchers and power users seeking unrestricted fine-tuning bases.

The **video generation sub-ecosystem** is maturing rapidly: MiniMax-H3 and LTX-2.5 are establishing clear leaders in open image-to-video, while community variants like Minimax-h3_Singularity show fine-tuning iteration accelerating output quality. Open-weight models continue to close the gap with proprietary offerings, particularly in multimodal and generative domains.

---

## 4. Worth Exploring

- **[Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next)** — The best balance of capability and speed in the current open-weight landscape. Its flash architecture and strong multimodal performance make it ideal for both research prototyping and production deployment.

- **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — With over 10 million downloads, this is the community's proven choice for running Qwen3.8-27B locally. Unsloth's quantization methodology consistently delivers high fidelity, making it the safest bet for resource-constrained inference.

- **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — For anyone working in time-series forecasting, this is the most credible open alternative to proprietary solutions. Google's transformer-based architecture has demonstrated state-of-the-art results across multiple benchmark datasets, and the PyTorch release removes a prior framework barrier.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*