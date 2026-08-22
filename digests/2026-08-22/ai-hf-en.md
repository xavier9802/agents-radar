# Hugging Face Trending Models Digest 2026-08-22

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-22 01:36 UTC

---



# Hugging Face Trending Models Digest — 2026-08-22

## Today's Highlights

Kimi-K3 by Moonshot AI surged to the #2 position with nearly 11,000 weekly likes and over 2.4 million downloads, powered by compressed-tensor quantization for efficient deployment. The Qwen3.8-27B ecosystem continues to dominate, spawning a wave of community fine-tunes, abliterated uncensored variants, and numerous quantization formats (GGUF, FP8, NVFP4). DeepSeek's V4 lineup gained serious momentum, with both Flash and Pro variants ranking among the top 30, while MiniMax expanded its footprint with strong video and music generation models.

---

## Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,913 | 2,448,810 | A high-performing open-weight multimodal model using compressed-tensor quantization for efficient inference. Its massive download count and near-record likes signal strong community adoption as a top-tier alternative to proprietary LLMs. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,612 | 2,833,064 | The faster variant of DeepSeek's latest V4 series, optimized for speed without sacrificing quality. It is trending as a practical production-grade choice for latency-sensitive applications. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 709 | 49,601 | DeepSeek's higher-accuracy V4 Pro model released mid-August, targeting demanding reasoning and coding tasks. Its recent release means lower download volume but strong early engagement from early adopters. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,738 | 505,113 | A 30B-parameter open-weight conversational model with strong multimodal (vision-language) capabilities. It is drawing attention as a competitive mid-range option between 7B and 70B-class models. |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 290 | 9,165 | A Mixture-of-Experts model with 35B total parameters but only ~3.5B active per token, enabling efficient high-quality inference. Its architectural novelty and Qwen3.5 foundation make it worth watching. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,139 | 15,702 | A massive 2.4-trillion-parameter sparse MoE model with 95B active parameters per token, representing the cutting edge of open-weight LLM scaling. It is trending as a showcase of Qwen's continued investment in MoE architectures. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,295 | 3,614,443 | A text-and-image-to-video generation model with exceptionally high adoption, making it one of the most-downloaded generative models on the platform. It supports diverse video creation workflows including image-to-video and video-to-video. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,493 | 654,175 | A diffusion-based single-file model for image, text, and video-to-video generation with strong temporal consistency. Its streamlined format makes it attractive for local and cloud deployment alike. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,163 | 15,678 | MiniMax's latest text-to-music generation model, notable as the company expands beyond video into audio synthesis. Early adoption is strong despite being a newer release. |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 311 | 0 | A fine-tune of MiniMax-H3 focused on enhanced video generation quality, leveraging the parent model's strong foundation. It is gaining attention among creators seeking a higher-fidelity video output. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 191 | 1,136 | A compact Qwen3-based ASR model optimized for speech recognition tasks. Its small size makes it suitable for on-device and low-latency transcription applications. |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,371 | 0 | A community-maintained set of Jinja chat templates with fixes for Qwen3.5 model compatibility issues. Despite zero downloads (template-only resource), it has strong engagement due to the practical value it provides developers. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 11,968 | 1,726,651 | The flagship base model driving the entire Qwen3.8 ecosystem, with multimodal vision-language support and conversational fine-tuning. It leads the榜单 in likes, reflecting its role as the foundation for hundreds of community variants. |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,510 | 5,804,917 | An Unsloth-optimized GGUF quantization of Qwen3.8-27B, boasting the highest download count on the entire list. It enables efficient local inference on consumer GPUs via llama.cpp. |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 328 | 1,013,917 | A novel NVFP4 quantization from Unsloth targeting next-gen NVIDIA GPUs, offering a new trade-off between precision and memory efficiency. It is early-stage but attracting attention from hardware-optimized inference users. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 660 | 1,939,895 | Official FP8 quantization from the Qwen team, providing a balanced reduction in memory footprint with minimal quality loss. It is widely adopted for GPU deployment where FP8 is supported. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 822 | 107,520 | An abliterated (safety-filter-removed) FP8-quantized version of Qwen3.8-27B, catering to users seeking unrestricted local deployment. It is one of the more popular uncensored variants in the ecosystem. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 295 | 68,275 | The GGUF equivalent of the above, enabling CPU and low-RAM GPU inference with the abliterated weights. It serves the growing demand for uncensored models running locally. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 821 | 18,193 | An MLX-format uncensored variant optimized for Apple Silicon, allowing efficient local inference on Mac hardware. Its high like count relative to downloads reflects strong community interest in the Apple ecosystem. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 571 | 1,126,222 | A community GGUF uncensored fine-tune with MTP (Multi-Token Prediction) support, achieving over a million downloads. It is notable for combining abliteration with speculative decoding optimizations. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 444 | 123,956 | An abliterated model available in both MLX and GGUF formats, reflecting the creator's focus on local-friendly deployments. It contributes to the growing library of unrestricted Qwen3.8 variants. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 424 | 357,225 | An aggressively abliterated GGUF variant with MTP, targeting users who want both unrestricted output and faster speculative decoding. It has solid adoption among local LLM enthusiasts. |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 238 | 74,038 | A Ridge-quantized GGUF variant applying a novel quantization approach to reduce memory usage while preserving quality. It represents the community's ongoing experimentation with post-training compression techniques. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 232 | 338,221 | A popular abliterated GGUF model with strong download numbers, indicating sustained demand for uncensored local inference options. It is one of the more widely deployed community variants. |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 213 | 421,918 | A heretic-style abliterated GGUF variant that has accumulated significant downloads, reflecting niche but active demand for unrestricted models. The "heretic" branding signals a more aggressive filtering removal approach. |
| [Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF](https://huggingface.co/Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF) | Blackfrost-AI | 201 | 197,667 | A dense 27B abliterated GGUF model offering a straightforward uncensored option for local deployment. It appeals to users who prefer simplicity over specialized fine-tuning approaches. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 229 | 17,521 | The safetensors version of the above abliterated model, for users who prefer native Transformers loading over GGUF. It has lower download volume but serves a different deployment audience. |
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 176 | 21,092 | A speculative-decoding-optimized variant (DFlash2) designed to accelerate generation speed without retraining. It targets users who want faster inference on existing hardware. |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 170 | 155,208 | A highly specialized GGUF variant combining GAIN training, Cold Fusion techniques, and MTP for performance optimization. It represents the frontier of community-driven model enhancement research. |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 207 | 123,237 | The GGUF-quantized version of Ornith's MoE model, making the efficient sparse architecture accessible for local inference. It pairs the architectural innovation of the base model with practical deployment compatibility. |

---

## Ecosystem Signal

The Qwen3.8-27B family is the dominant force on Hugging Face this week, anchoring an extraordinary ecosystem of over a dozen community variants spanning abliterated uncensored fine-tunes, multiple quantization formats (GGUF, FP8, NVFP4, MLX), and speculative decoding optimizations. This level of derivative activity signals that Qwen3.8-27B has become the default open-weight foundation for local deployment, much like Llama previously. Meanwhile, DeepSeek's V4 lineup (Flash and Pro) is establishing itself as a serious competitive force, while Kimi-K3's compressed-tensor approach is setting a new standard for efficient open-weight deployment. The abliteration trend — removing safety filters from base models — remains a persistent undercurrent, with multiple creators producing variants in every available format. Quantization diversity is also expanding, with Unsloth introducing NVFP4 alongside established GGUF and FP8 options, reflecting the community's drive to match hardware capabilities. Mixture-of-Experts models (Ornith, Qwen 2.4T-A95B) are gaining traction as a path to scaling without proportional inference costs.

---

## Worth Exploring

1. **moonshotai/Kimi-K3** — Its compressed-tensor quantization is a notable efficiency innovation, and with nearly 11K likes and 2.4M downloads, it has earned strong community validation. It deserves study as a potential successor to Llama and Qwen as the go-to open-weight model.

2. **unsloth/Qwen3.8-27B-NVFP4** — This is the first major NVFP4 release from Unsloth, targeting next-generation NVIDIA GPUs. It represents an emerging quantization format that could become important as hardware evolves, making it valuable to track even in its early adoption phase.

3. **MiniMaxAI/MiniMax-H3** — With over 4,200 likes and 3.6 million downloads, it is the most popular generative model on the list. Its image-text-to-video pipeline and strong adoption make it a key reference point for anyone working in video generation.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*