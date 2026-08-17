# Hugging Face Trending Models Digest 2026-08-17

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-17 01:42 UTC

---



# 🤗 Hugging Face Trending Models Digest — August 17, 2026

---

## 1. Today's Highlights

Qwen's Qwen3.8-27B leads the charts with over 10,000 weekly likes, cementing the Qwen family as the dominant open-weight LLM force. MiniMax-H3 continues its streak as the most-downloaded video generation model, now spawning a wide ecosystem of LoRAs, turbo variants, and GGUF conversions. DeepSeek's V4-Flash variant has emerged as a strong open alternative for fast text generation, while NVIDIA's Nemotron 3.5 Lightning series introduces specialized NVFP4 quantization for accelerated inference.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 10,296 | 267,725 | The flagship open-weight vision-language model from Qwen, supporting image-text-to-text conversational pipelines. It tops the weekly likes chart, reflecting strong community adoption for multimodal chat. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,768 | 2,136,775 | Kimi's latest image-text-to-text model uses compressed-tensors for efficient inference. Its massive download count (2.1M) signals widespread production use in Chinese-language AI workflows. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,462 | 1,872,232 | A fast text-generation variant of DeepSeek V4 with over 1.8M downloads. It's trending for its balance of speed and quality in conversational pipelines. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 536 | 21,873 | DeepSeek's higher-capacity V4 Pro model targets complex reasoning tasks. Released in mid-August, it is still accumulating traction but represents the premium tier of the V4 lineup. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,012 | 7,932 | A 2.4T-parameter MoE variant (A95B active) from Qwen optimized for text generation. It extends the Qwen3.8 family into sparse architectures for more efficient large-scale inference. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 291 | 196,326 | NVIDIA's MoE text-generation model using novel NVFP4 quantization, targeting 3x speedup on Blackwell GPUs. It is trending as a practical option for low-latency deployment. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 160 | 66,253 | The full-precision BF16 counterpart to the NVFP4 Lightning model, offering maximum quality for benchmarks and evaluation before quantization. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 647 | 141,009 | A compact 2.6B text-generation model leveraging Liquid AI's continuous-time architecture. It's gaining attention for efficient on-device and edge deployment. |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 285 | 5,727 | A tiny hybrid model from inclusionAI under MIT license, targeting low-resource and regional language scenarios. Its open license makes it attractive for custom fine-tuning. |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 186 | 393 | A very new image-text-to-text model from dots-studio, still early in adoption. Represents the experimental dots3 line aimed at note-taking and document understanding. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,031 | 2,307,541 | The most-downloaded video generation model on HF, supporting text-to-video and image-to-video. Its 2.3M downloads reflect dominant community and production uptake for video creation. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,030 | 424,099 | Lightricks' diffusion-based image-to-video model with single-file distribution. It is a strong open alternative for creators needing high-quality video synthesis from images or text. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 844 | 8,639 | MiniMax's text-to-music generation model using diffusers. It introduces a new benchmark for AI-generated music quality and is building early community interest. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 560 | 239,206 | A turbo variant of MiniMax-H3 focused on faster image-to-video generation. Its 239K downloads indicate strong demand for lower-latency video synthesis. |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 229 | 16,103 | A specialized LoRA for MiniMax-H3 trained to improve photorealistic human depiction in generated video. It addresses a common failure mode of the base model. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 776 | 0 | A LoRA targeting combined text-to-video and audio-video generation on top of H3-Turbo. Still awaiting first downloads but shows community momentum. |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 223 | 20,860 | A compact 2.9B text-to-image diffusion model distributed as a single ComfyUI file. It targets users wanting a lightweight, easy-to-deploy image generator. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,389 | 13,406,892 | The ComfyUI-ready single-file packaging of MiniMax-H3 with the highest download count on the entire list (13.4M). It is the de facto standard for H3 in Comfy workflows. |
| [Comfy-Org/MiniMax-Music-3](https://huggingface.co/Comfy-Org/MiniMax-Music-3) | Comfy-Org | 153 | 0 | ComfyUI-packaged version of MiniMax-Music3. Awaiting initial downloads but provides an easy integration path for music generation in Comfy workflows. |

### 🔧 Specialized Models (code, math, medical, embeddings)

*No models in the current top 30 are classified primarily under specialized domains such as code, math, or medical.*

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 1,463 | 1,945,635 | Unsloth's GGUF quantization of Qwen3.8-27B with nearly 2M downloads. It is the go-to option for running the model locally with llama.cpp and similar runtimes. |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 458 | 718,178 | GGUF conversion of Muse-Glimmer-30B, enabling efficient local inference of this multimodal model. Strong download numbers indicate active community use. |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 298 | 357,877 | The official GGUF variant from meta-models, preserving the original base model architecture with arxiv references. Offers an authoritative quantization path. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 347 | 4,285 | An abliterated (uncensored) FP8 quantization of Qwen3.8-27B for unrestricted generation. Targets power users seeking maximal control over model output. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,096 | 3,020,070 | A heavily modified uncensored GGUF fine-tune of Qwen3.6 with MTP support and 3M downloads. Its long name belies a popular community build for unrestricted local use. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 215 | 183,988 | Another uncensored GGUF variant of Qwen3.8-27B with MTP (multi-token prediction). It provides a lighter alternative to the Fable-Fusion build for resource-constrained setups. |
| [unsloth/Qwen3.8-27B-FP8](https://huggingface.co/unsloth/Qwen3.8-27B-FP8) | unsloth | 202 | 276,269 | Unsloth's FP8 quantization of Qwen3.8-27B, offering a balance between quality and memory efficiency. A practical choice for GPU deployments with limited VRAM. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 485 | 352,971 | The official FP8 quantized release from Qwen itself, matching the base model's image-text-to-text pipeline. Preferred when authenticity and official weights are prioritized. |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 210 | 11,311 | Official FP8 quantization of the Qwen3.8 MoE 2.4T variant. Enables running the sparse MoE model with reduced memory footprint on consumer hardware. |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 175 | 204,344 | GGUF conversion of MiniMax-H3 for local video generation via stable-diffusion.cpp. Allows running H3 without GPU dependence, though with trade-offs in quality and speed. |

---

## 3. Ecosystem Signal

The dominant theme this week is the maturation of **video generation** as a first-class Hugging Face category. MiniMax-H3 alone accounts for over 17 million downloads across its variants (base, ComfyUI, GGUF, Turbo, and multiple LoRAs), demonstrating that open video models have reached production-scale adoption. The LoRA ecosystem around H3—spanning realism, turbo acceleration, and cross-modal audio-video—mirrors the fine-tuning culture that previously defined the image-generation space.

In language models, **Qwen's 3.8 family** continues to command attention, with official releases, FP8 quantizations, and multiple community uncensored GGUF variants all ranking in the top 30. The emergence of **NVFP4 quantization** from NVIDIA signals a shift toward hardware-aware compression targeting Blackwell GPUs, while DeepSeek's V4-Flash variant proves that open-weight models can compete on raw download volume. The **compressed-tensors** technique used by Kimi-K3 (2.1M downloads) suggests that memory-efficiency innovations are becoming a key differentiator alongside raw model quality.

---

## 4. Worth Exploring

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The most-downloaded video generation model on the list by a wide margin. Its extensive LoRA ecosystem (realism, turbo, audio-video) makes it the best platform for experimenting with open video synthesis.

2. **[deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731)** — With 1.87M downloads and 3,462 likes, this is a proven open-weight text generator that offers a compelling alternative to proprietary models. Ideal for deployment where latency and cost matter.

3. **[nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4)** — The introduction of NVFP4 quantization is a notable technical signal. Studying this model reveals how hardware-aware compression can enable efficient MoE inference on next-gen GPUs.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*