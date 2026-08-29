# Hugging Face Trending Models Digest 2026-08-29

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-29 06:43 UTC

---



# Hugging Face Trending Models Digest — 2026-08-29

## 1. Today's Highlights

Qwen continues its dominant run with the **Qwen3.8-27B** family capturing over 3.4 million downloads and 13,000+ likes, while its lighter Flash-Next variant leads this week's trending chart. MiniMax's **MiniMax-H3** video generation model has exploded in popularity, amassing nearly 5 million downloads, and the video ecosystem is expanding rapidly with multiple ControlNet and LoRA extensions. The community fine-tuning scene remains intensely active around Qwen3.8, with abliterated, uncensored, and GGUF variants driving enormous download numbers across the leaderboard.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,790 | 3,959,575 | DeepSeek's latest Flash variant delivers strong text-generation performance with conversational tuning, sustaining deepseek-ai's momentum in efficient open-weight LLMs. Nearly 4 million downloads signal strong community adoption for production deployment. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 11,069 | 2,675,145 | Moonshot AI's Kimi-K3 brings multimodal image-text-to-text capabilities with compressed-tensor optimization, making it both powerful and efficient. With over 11,000 likes it ranks among the most liked models on this week's list. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,530 | 34 | The Flash version of ZAI's GLM-5.3 series is a new image-text-to-text and text-generation model that signals continued investment in the GLM family architecture. Early engagement suggests strong interest in its upcoming capabilities. |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,176 | 0 | The full GLM-5.3 model using the new `glm_moe_dsa` architecture offers conversational text generation as the baseline release for the series. Zero downloads indicate it was just posted and is awaiting community evaluation. |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 254 | 0 | Tencent's Hunyuan Hy4-preview is a text-generation model tagged with the `hy_v4` architecture, representing the next iteration of Tencent's Hunyuan family. Its fresh release has not yet accumulated downloads, suggesting it is in early preview. |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 486 | 88,102 | Ornith's 35B MoE model with 3B active parameters offers efficient text generation and image-text-to-text capability under the qwen3_5_moe architecture. Over 88K downloads show steady adoption for its cost-performance balance. |
| [thomsonreuters/Thomson-1.0-Small](https://huggingface.co/thomsonreuters/Thomson-1.0-Small) | thomsonreuters | 146 | 349 | Thomson Reuters' domain-focused small model uses the qwen3_5_moe architecture for image-text-to-text conversational tasks, targeting legal and financial workflows. Low download count reflects its narrow enterprise audience and early release stage. |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 124 | 64 | A text-generation model built on the Nemotron architecture by Pipecat AI, aimed at telephony and voice-conversation applications. Minimal downloads indicate this is a very early alpha release. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,033 | 912,729 | Lightricks' LTX-2.5 is a diffusion-based image-to-video and text-to-video model supporting multiple video generation pipelines. Its single-file format and high download count make it a go-to for fast video generation prototyping. |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,589 | 4,848,404 | MiniMax-H3 is a high-quality image-to-video and text-to-video model using the diffusers pipeline, and has become one of the most-downloaded models this week. Nearly 5 million downloads demonstrate massive community demand for open video generation. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,290 | 19,726 | MiniMax-Music3 extends the MiniMax family into text-to-music generation via the diffusers pipeline, adding audio to their video capabilities. The growing download count reflects interest in open music-generation models. |
| [alibaba-pai/MiniMax-H3-Fun-Controlnet-Union](https://huggingface.co/alibaba-pai/MiniMax-H3-Fun-Controlnet-Union) | alibaba-pai | 159 | 3,344 | This ControlNet extension for MiniMax-H3 enables video-to-video and image-text-to-video generation with enhanced structural control. It broadens H3's applicability for precise video editing workflows. |
| [alibaba-pai/MiniMax-H3-Acc-LoRAs](https://huggingface.co/alibaba-pai/MiniMax-H3-Acc-LoRAs) | alibaba-pai | 136 | 609 | A set of LoRA adapters for MiniMax-H3 published alongside an arXiv paper (2607.26004), targeting accuracy and efficiency improvements for text-to-video generation. Early-stage adoption but significant research interest. |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 171 | 240 | Breeze-TTS-2 is a text-to-speech model in the transformers pipeline, continuing the Breeze family's focus on high-quality neural voice synthesis. Low download numbers suggest it is a newer or niche release. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,512 | 0 | This repository provides corrected Jinja chat templates for Qwen models on MLX, resolving known template formatting issues that affect inference. Zero downloads may reflect its utility as a config resource rather than a model checkpoint. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,155 | 7,758,790 | Unsloth's GGUF quantization of Qwen3.8-27B delivers near-lossless performance with dramatically reduced memory footprint, making it the most-downloaded model on this list. Over 7.7 million downloads underscore the critical role of quantization in open-model accessibility. |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,165 | 3,457,687 | The base Qwen3.8-27B model is a multimodal image-text-to-text conversational model that has become the backbone for the week's finest-tuning and quantization ecosystem. Its 13,000+ likes and 3.4M downloads reflect foundational importance. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 808 | 1,666,948 | This GGUF uncensored quantization of Qwen3.8-27B removes safety guardrails for community use, combining llama.cpp compatibility with MTP (multi-token prediction). Over 1.6 million downloads show strong demand for unrestricted open models. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 426 | 1,355,482 | The Huihui abliterated variant uses the abliterate technique to remove RLHF conditioning from Qwen3.8-27B, available in GGUF format for efficient local inference. Over 1.3 million downloads reflect sustained interest in abliterated models. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,237 | 273,577 | An FP8 quantized and abliterated uncensored version of Qwen3.8-27B by orcarouter, balancing memory efficiency with unrestricted generation capability. Strong engagement with 1,200+ likes indicates a dedicated user base. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,194 | 83,352 | The MLX-optimized uncensored variant of Qwen3.8-27B enables efficient inference on Apple Silicon while preserving abliterated behavior. Its 83K+ downloads highlight the popularity of Apple-native quantization formats. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 884 | 509,270 | The original abliterated Qwen3.8-27B release supporting multiple formats (MLX, SAFETENSORS, GGUF) that pioneered the community abliteration movement. Over half a million downloads mark it as a landmark community contribution. |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,181 | 4,810 | Qwen's latest Flash-tier model in the Qwen3.8 family, offering image-text-to-text conversational capabilities under the `qwen4_exp` architecture with efficient inference. Leading weekly likes despite modest download numbers as it is a newly released model. |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 531 | 4,354 | Unsloth's GGUF quantization of the new Qwen3.8-Flash-Next model, enabling fast local inference with reduced precision. Early-stage but rapid adoption signals strong community appetite for Flash-tier quantizations. |
| [Qwen/Qwen3.8-Flash-Next-FP8](https://huggingface.co/Qwen/Qwen3.8-Flash-Next-FP8) | Qwen | 148 | 2,219 | An official FP8-quantized variant of Qwen3.8-Flash-Next from the Qwen team, providing a memory-efficient option for hardware with FP8 support. Low but growing engagement as the model is newly available. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 533 | 188,460 | Another uncensored GGUF quantization of Qwen3.8-27B from orcarouter, providing an alternative to their FP8 and MLX releases in standard GGUF format. Steady adoption among local-inference users. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 729 | 938,219 | An aggressive MTP-enabled uncensored GGUF fine-tune of Qwen3.8-27B by HauhauCS, optimizing for both speed and unrestricted generation. Nearly a million downloads reflect strong demand for performant local uncensored models. |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 333 | 1,469,059 | The GGUF quantization of Ornith-1.5-35B-A3B makes this efficient MoE model accessible for local inference with MIT licensing and endpoint compatibility. Over 1.4 million downloads show significant demand for quantized MoE models. |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 250 | 0 | Unsloth's GGUF quantization of the new GLM-5.3-Flash model, targeting English-language text generation with reduced memory requirements. The freshly posted model has not yet accumulated downloads. |
| [orcarouter/Qwen3.8-27B-Uncensored](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored) | orcarouter | 201 | 18,598 | The original safetensors uncensored/abliterated checkpoint from orcarouter before format-specific quantizations were released. Lower download count compared to its GGUF/MLX variants indicates preference for quantized formats. |

---

## 3. Ecosystem Signal

The Qwen family — specifically Qwen3.8 — is the clear center of gravity this week. With the base **Qwen3.8-27B** amassing over 3.4 million downloads and its GGUF quantization reaching 7.7 million, the ecosystem around this model is unusually rich: uncensored, abliterated, FP8, MLX, and GGUF variants all compete for community attention. This signals a maturing open-weight ecosystem where a single strong base model spawns an entire fine-tuning economy. Meanwhile, **MiniMax-H3** has emerged as a breakout star in video generation with nearly 5 million downloads, and its ControlNet and LoRA extensions show the ecosystem is moving toward composable, modular generation pipelines. The GLM-5.3 series from zai-org and the new **Kimi-K3** from Moonshot represent growing competition in the multimodal LLM space, with compressed-tensor and MoE architectures becoming increasingly common. Open-weight remains the dominant paradigm for community innovation, while proprietary models like DeepSeek-V4-Flash continue to set performance benchmarks that the open community rapidly quantizes and adapts.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — With over 11,000 likes and 2.6 million downloads, Kimi-K3 combines multimodal understanding with compressed-tensor efficiency, making it one of the most compelling new open-weight LLMs of the week. Its architecture and performance warrant close study as competition intensifies.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The fastest-growing video generation model on the list with nearly 5 million downloads. Paired with the ControlNet and LoRA extensions from alibaba-pai, it represents a complete, composable video-generation stack that is worth experimenting with for both creative and technical applications.

3. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — The single most-downloaded model this week at 7.7 million, demonstrating the outsized impact of quality quantization. Studying its configuration and benchmarks provides insight into how the open community maximizes the accessibility of high-capability models.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*