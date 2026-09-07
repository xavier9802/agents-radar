# Hugging Face Trending Models Digest 2026-09-07

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-09-07 04:04 UTC

---



# 🤗 Hugging Face Trending Models Digest
**As of 2026-09-07**

---

## 1. Today's Highlights

The Qwen3.8 ecosystem dominates the weekly trending charts, with both base and fine-tuned variants of the 27B model pulling millions of downloads across multiple quantization formats. Community-driven "uncensored" and specialization fine-tunes continue to surge in popularity, particularly around the Qwen3.8-27B family, reflecting sustained demand for custom instruction-tuned models. On the multimodal side, MiniMax-H3 and LTX-2.5 are leading the image-to-video and text-to-video wave, while Google's TimesFM 3.0 extends time-series forecasting into new territory. NVIDIA and Unsloth are pushing quantization forward with NVFP4 and GGUF releases tailored for the latest Qwen3.8 architecture.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 14,142 | 6,190,807 | A flagship 27B multimodal LLM from the Qwen team supporting image-text-to-text pipelines. It's the most-liked model on the list by a wide margin, signaling strong community appetite for capable open-weight chat models. |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,946 | 432,966 | The next-generation flash variant of Qwen3.8, optimized for faster inference while retaining multimodal capabilities. Its rapid uptake shows the market is prioritizing speed-accuracy trade-offs for production deployments. |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,971 | 4,986,349 | A high-performing image-to-video model from MiniMax with nearly 5 million downloads. Its strong download count relative to likes indicates broad practical adoption beyond casual experimentation. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,101 | 761,364 | A flash-optimized variant of GLM-5.3 targeting efficient image-text-to-text generation. Gaining traction as an open alternative for multimodal inference workloads. |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,740 | 410,074 | The base GLM-5.3 model featuring a MoE DSA architecture for conversational text generation. Offers a strong open-weight foundation for downstream fine-tuning. |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 751 | 209,191 | An experimental vision-capable variant of DeepSeek V4 Flash, targeting efficient image-text generation. Early community interest suggests DeepSeek is pushing further into multimodal efficiency. |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 445 | 6,441 | Tencent's Hunyuan Hy4 preview model for text generation, representing continued investment in open Chinese-language LLMs. |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,707 | 14,612,342 | The classic GPT-2 model remains a ubiquitous baseline with over 14 million downloads. Its persistence on the trending list is a testament to its role as a reference implementation and educational tool. |
| [IFM/K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 187 | 1,723 | A 36B MoE text-generation model from IFM, showcasing the trend toward larger sparse architectures for specialized workloads. |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 621 | 5,477 | A compact 4B text-generation model from the Spark family, targeting efficient on-device and edge deployments. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,982 | 1,526,928 | A diffusion-based image-to-video model supporting text-to-video and video-to-video pipelines. Over 1.5 million downloads signal strong creator and developer adoption for generative video use cases. |
| [OpenVDN/vdn-minimax-h3](https://huggingface.co/OpenVDN/vdn-minimax-h3) | OpenVDN | 210 | 0 | A finetune of MiniMax-H3 targeting text-to-video generation. Demonstrates the community's rapid adaptation of popular video models for specialized pipelines. |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 462 | 6,357 | An advanced text-to-speech model in the Breeze family, catering to the growing demand for high-quality open-source voice synthesis. |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 515 | 144,455 | Google's TimesFM 3.0 is a time-series forecasting model extending the family's capabilities to more complex temporal predictions. Notable for bringing state-of-the-art forecasting to the open-weight space. |
| [facebook/mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 263 | 12,464 | Meta's Massive Multimodal Sound model for speech recognition and multilingual audio understanding. Continues to serve as a foundational model for audio AI research. |
| [microsoft/VibeVoice-ASR-Streaming-7B](https://huggingface.co/microsoft/VibeVoice-ASR-Streaming-7B) | microsoft | 121 | 889 | Microsoft's streaming ASR model for real-time automatic speech recognition. Represents the push toward low-latency voice transcription at the edge. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,569 | 253,029,336 | The most-downloaded embedding model on the list with over 253 million downloads. Remains the go-to choice for sentence similarity and semantic search applications. |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,989 | 52,338,347 | Google's foundational BERT model with over 52 million downloads, still widely used as a baseline for NLU tasks despite its age. |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,211 | 20,579,479 | OpenAI's CLIP vision-language embedding model with over 20 million downloads. Essential infrastructure for zero-shot image classification and multimodal retrieval. |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,156 | 7,054,316 | A distilled 40% smaller variant of BERT, balancing efficiency and performance for production NLP pipelines. |
| [dealignai/GLM-5.3-CYBERSECURITY-FP8](https://huggingface.co/dealignai/GLM-5.3-CYBERSECURITY-FP8) | dealignai | 179 | 15,648 | A domain-specialized GLM-5.3 fine-tune in FP8 precision targeting cybersecurity applications. An example of the growing trend toward vertical-specific open models. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,603 | 10,311,462 | Unsloth's GGUF-quantized version of Qwen3.8-27B with over 10 million downloads — the highest download count on the entire list. Demonstrates the critical role of efficient quantization in making large models accessible. |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 471 | 348,389 | A mixed-precision GGUF quantization using GSQ and RCO techniques, targeting memory-efficient deployment without significant quality loss. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 983 | 1,568,315 | An aggressive uncensored fine-tune of Qwen3.8-27B with multi-token prediction, pulling over 1.5 million downloads. Reflects sustained demand for unfiltered models in the open-weight community. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,108 | 995,160 | An "obliterated" (refusal-removed) fine-tune of Qwen3.8-27B available in both GGUF and MLX formats. Nearly 1 million downloads highlight the robust niche for uncensored models. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 754 | 287,720 | Another abliterated GGUF variant of Qwen3.8-27B, contributing to the dense ecosystem of community customizations around this base model. |
| [DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 253 | 211,018 | A heavily customized uncensored fine-tune with MTP and coding enhancements, combining multiple community techniques into a single release. |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 814 | 823,733 | Unsloth's quantized GGUF release for Qwen3.8-Flash-Next, bringing efficient inference to the newer flash architecture. |
| [nvidia/Qwen3.8-Flash-Next-NVFP4](https://huggingface.co/nvidia/Qwen3.8-Flash-Next-NVFP4) | nvidia | 119 | 13,321 | NVIDIA's NVFP4 quantization of Qwen3.8-Flash-Next, representing hardware-aware quantization tailored for NVIDIA GPU inference. |
| [Jackrong/Qwopus3.8-27B-Flash-GGUF](https://huggingface.co/Jackrong/Qwopus3.8-27B-Flash-GGUF) | Jackrong | 132 | 22,128 | A GGUF quantization with llama.cpp compatibility for the Qwen3.8 Flash variant, targeting local inference on consumer hardware. |

---

## 3. Ecosystem Signal

The dominant story on Hugging Face this week is the **Qwen3.8-27B ecosystem**, which now has at least a dozen derivatives in various quantization and fine-tuning states. This concentric-ring pattern — a strong base model spawning quantized, uncensored, and specialized variants — mirrors the trajectory previously set by Llama and has now transferred to Qwen. Community fine-tunes (abliterated, uncensored, MTP-enhanced) collectively account for tens of millions of downloads, proving that open-weight models with permissive licenses are capturing mindshare that proprietary APIs once held. In video generation, **MiniMax-H3** and **LTX-2.5** are the clear leaders, with the former exceeding 4.9 million downloads and the latter 1.5 million — a strong signal that open video models are approaching production viability. Google's **TimesFM 3.0** is notable as a specialized domain model breaking into the mainstream trending space, indicating growing interest in vertical AI beyond general-purpose LLMs. Quantization remains a fierce competitive arena, with Unsloth (10.3M downloads on a single GGUF release), NVIDIA (NVFP4), and ISTA-DASLab (GSQ/RCO mixed precision) all vying for inference efficiency leadership.

---

## 4. Worth Exploring

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — With nearly 5 million downloads and a 4,971 like count, this is the most actively adopted video generation model on the list. Its image-to-video and text-to-video capabilities make it a strong candidate for creative workflows, and studying its architecture could inform how open video models are scaling.

2. **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — A rare specialized model from a top-tier lab entering the trending charts. TimesFM 3.0 represents the cutting edge of foundation-model-based time-series forecasting, a domain where open-weight models are still scarce compared to the LLM space.

3. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — The highest-download model on the list at over 10.3 million. As a practical deployment target, it showcases how effective Unsloth's quantization pipeline is at making 27B-class models runnable on consumer hardware — directly relevant for anyone building local inference stacks.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*