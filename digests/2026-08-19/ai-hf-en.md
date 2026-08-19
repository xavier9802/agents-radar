# Hugging Face Trending Models Digest 2026-08-19

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-19 01:40 UTC

---



# Hugging Face Trending Models Digest — 2026-08-19

## 1. Today's Highlights

Qwen3.8 continues its dominant week, with the base 27B model topping likes at 11,148 and spawning a family of quantized, uncensored, and MoE variants. Moonshot's Kimi-K3 surges to 10,826 likes, signaling strong community appetite for open-weight long-context LLMs. MiniMax-H3 claims one of the highest download counts on the platform at 2.8 million, underscoring the continued momentum behind open video-generation models. Meanwhile, quantization diversity (GGUF, FP8, NVFP4, MLX) reflects a maturing ecosystem focused on accessibility across hardware.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 11,148 | 665,513 | The flagship open-weight 27B model from the Qwen3.8 family, leading this week's likes with strong conversational and vision capabilities. Its dominance reflects sustained community preference for Qwen's balance of performance and accessibility. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,826 | 2,226,898 | Moonshot's latest open-weight LLM with compressed-tensors support, offering strong long-context performance. It trends due to Kimi's reputation for extended context windows and competitive reasoning benchmarks. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,527 | 2,123,462 | DeepSeek's fast-ratio variant in the V4 family, optimized for speed without sacrificing quality. High download volume signals strong adoption for latency-sensitive production deployments. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 602 | 30,985 | DeepSeek's premium V4 Pro model targeting high-complexity reasoning tasks. A newer release that is building momentum as users evaluate it against Qwen and Kimi. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 323 | 269,372 | NVIDIA's MoE Lightning variant with NVFP4 quantization, designed for efficient inference on NVIDIA hardware. It stands out as a rare open-weight option from NVIDIA optimized for their GPU ecosystem. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,682 | 384,097 | A 30B image-text-to-text model gaining traction for its multimodal conversational quality. Its strong download-to-like ratio indicates active integration into production pipelines. |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 320 | 9,990 | inclusionAI's compact 3B-class model with custom code support, targeting multilingual and low-resource language tasks. It attracts interest as a lightweight alternative for edge and mobile deployments. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,146 | 2,855,539 | MiniMax's image-to-video and text-to-video model, one of the highest-download models on the platform. Its viral adoption is driven by high-quality video generation at accessible open weights. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,224 | 503,632 | Lightricks' diffusion-based image-to-video model supporting text, image, and video-to-video pipelines. It's trending as a strong open alternative for creators and editors seeking controllable video synthesis. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 963 | 11,745 | MiniMax's text-to-music generation model using the diffusers pipeline. It represents the growing category of open-weight audio generation tools gaining community experimentation. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 610 | 300,279 | A turbo-optimized variant of MiniMax-H3 for faster image-to-video generation. It trends due to practical speed improvements for production video-generation workflows. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,066 | 11,212 | Qwen's 2.4-trillion-parameter MoE model with 95B active parameters, designed for maximum reasoning capacity. It draws interest from researchers and power users benchmarking the frontier of open MoE architectures. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 1,824 | 3,561,466 | Unsloth's GGUF-quantized variant of Qwen3.8-27B, enabling efficient CPU and lower-memory GPU inference. The 3.5M+ downloads make it one of the most distributed quantized models this week. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 564 | 741,011 | Official FP8-quantized release from Qwen, reducing memory footprint while preserving quality for NVIDIA GPU inference. It provides a vendor-verified quantization path for production use. |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 262 | 523,919 | Unsloth's NVIDIA FP4 quantization targeting next-gen GPU tensor cores for maximum throughput. It's an early adopter format gaining traction among performance-focused engineers. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,142 | 3,020,528 | A heavily fine-tuned uncensored GGUF model combining MTP, heretic, and DAU techniques on Qwen3.6. Its massive download count reflects sustained community demand for unrestricted open-weight variants. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 414 | 558,767 | A community GGUF uncensored build of Qwen3.8-27B with MTP support, balancing download volume and engagement. It serves users seeking unrestricted inference on consumer hardware. |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 482 | 787,276 | Unsloth's GGUF-quantized version of Muse-Glimmer-30B, extending the base model's multimodal capabilities to resource-constrained environments. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 534 | 45,465 | An abliterated and uncensored FP8 quantization of Qwen3.8-27B, targeting users who want both reduced memory usage and removed alignment restrictions. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 281 | 0 | MLX-formatted uncensored variant for Apple Silicon inference, though downloads are currently zero as the release is new. It signals growing interest in MLX-optimized open-weight models. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 204 | 27,745 | An aggressively fine-tuned uncensored GGUF build with MTP, targeting users prioritizing raw capability over alignment. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,426 | 14,641,908 | ComfyUI-compatible packaging of MiniMax-H3 with over 14.6 million downloads, making it the most downloaded model this week. It enables seamless integration into ComfyUI-based video generation workflows. |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,258 | 0 | A Jina-formatted chat template fix for Qwen3.5 models in MLX, addressing compatibility issues that users reported. Zero downloads reflect its utility as a configuration resource rather than a model checkpoint. |
| [Comfy-Org/MiniMax-Music-3](https://huggingface.co/Comfy-Org/MiniMax-Music-3) | Comfy-Org | 178 | 285,444 | ComfyUI-ready packaging of MiniMax-Music3, extending the music generation model into the ComfyUI ecosystem for workflow integration. |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 266 | 0 | A fine-tune of MiniMax-H3 for enhanced image-to-video output, currently without downloads as a fresh release. It represents the trend of specialized video-generation fine-tunes built on open base models. |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 173 | 12,854 | A Ridge-optimized GGUF quantization of Qwen3.8-27B targeting efficient inference on llama.cpp. |
| [LiquidAI/LFM2.5-VL-3B](https://huggingface.co/LiquidAI/LFM2.5-VL-3B) | LiquidAI | 174 | 9,101 | LiquidAI's 3B vision-language model using their novel Liquid Flamingo architecture, offering a compact alternative for on-device multimodal tasks. |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 249 | 24,893 | A 2.9B text-to-image diffusion model packaged for ComfyUI, catering to users seeking smaller, faster image generation models. |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 227 | 13,344 | Official FP8 quantization of Qwen's 2.4T MoE model, making the largest open MoE architecture more practical for inference on compatible hardware. |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 221 | 1,120 | A newer text-generation model from dots-studio with limited download activity, still building its user base. |

---

## 3. Ecosystem Signal

The dominant trend this week is the **Qwen3.8 family ecosystem** — a single base model spawning an extraordinary cascade of quantizations (GGUF, FP8, NVFP4, MLX), uncensored fine-tunes, and community variants. This signals that Qwen has become the de facto reference architecture for the open-weight community, similar to how Llama models functioned in prior cycles. The uncensored/abliterated fine-tune subculture remains vigorous, with DavidAU's heavily merged GGUF pulling over 3 million downloads, indicating sustained demand for unrestricted models alongside the official releases.

In generative media, **MiniMax-H3** continues to be the most-downloaded model on the platform (14.6M via ComfyUI packaging), reinforcing that open video generation is the fastest-growing segment. Meanwhile, **Kimi-K3** and **DeepSeek-V4** show that Chinese labs are aggressively competing in the open-weight LLM space, offering both Pro and Flash tiers to capture different deployment segments. Quantization diversity — from NVFP4 to MLX to abliterated GGUF — reflects a maturing infrastructure layer where users can deploy frontier models on consumer hardware, reducing reliance on proprietary APIs.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — With 10,826 likes and 2.2M downloads, Kimi-K3 combines compressed-tensors efficiency with strong long-context performance. It's worth studying as a competitive open alternative to proprietary models, especially for applications requiring extended context windows.

2. **[Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B)** — As Qwen's largest MoE release (2.4T total / 95B active parameters), this model represents the current frontier of open-weight reasoning architectures. The FP8 variant ([Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8)) makes it viable for practical evaluation, offering a window into how MoE scaling translates to real-world capability.

3. **[Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5)** — With strong downloads and a flexible multi-pipeline design (image-to-video, text-to-video, video-to-video), LTX-2.5 is a compelling open alternative in the video-generation space. Its diffusion-single-file format simplifies deployment, making it ideal for experimentation and integration into creative workflows.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*