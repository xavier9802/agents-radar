# Hugging Face Trending Models Digest 2026-08-14

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-14 02:26 UTC

---



# Hugging Face Trending Models Digest — 2026-08-14

## 1. Today's Highlights

Kimi-K3 by moonshotai tops the charts with over 10,600 weekly likes, cementing its position as the most-liked model on the platform. The MiniMax-H3 ecosystem dominates the video-generation space, with the base model, its Turbo variant, and a thriving community of LoRA adapters and ComfyUI integrations collectively accumulating over 10 million downloads. DeepSeek's V4 series continues its momentum, while NVIDIA introduces quantized variants of its Nemotron 3.5 Lightning line targeting efficient deployment.

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,624 | 1,871,575 | A powerful image-text-to-text model from the Kimi team that has become the standout LLM of the week. Its 1.8M+ downloads and 10K+ likes reflect strong community adoption, particularly for its multimodal conversational capabilities. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,324 | 1,431,587 | DeepSeek's fast text-generation model that continues the V4 family's strong presence on the leaderboard. It is trending due to its balance of speed and quality, driving over 1.4M downloads. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 230 | 44,859 | NVIDIA's newly quantized NVFP4 variant of its Nemotron 3.5 Lightning model, offering highly efficient inference. It targets practitioners needing performance on constrained hardware without sacrificing quality. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 131 | 22,279 | The BF16 counterpart to the NVFP4 release, providing a full-precision option for users who prioritize maximum accuracy. It rounds out NVIDIA's Lightning deployment strategy. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 603 | 116,640 | A compact 2.6B text-generation model from LiquidAI that is gaining traction for its efficiency. Its small footprint and solid performance make it appealing for edge and mobile deployments. |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 354 | 3,868 | A preview MoE (mixture-of-experts) model from deepgrove that is attracting early adopters. Its architecture promises efficient inference through sparse activation patterns. |
| [endless-frontier/BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-fronter | 188 | 3,184 | A multimodal conversational model based on the Qwen3.5 MoE architecture. It targets users seeking an open image-text-to-text option with strong conversational abilities. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,831 | 1,605,940 | The flagship MiniMax-H3 model for image-text-to-video generation, which has become the most-downloaded generative model of the week. Its high-quality video outputs and accessible licensing are driving massive adoption. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 308 | 0 | DeepSeek's latest Pro variant for text-generation, representing the premium tier of the V4 lineup. Early interest is building despite zero downloads, suggesting a recently released model. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 352 | 25 | MiniMax's expansion into audio generation with a text-to-audio model built on the Music3 architecture. It is generating early buzz as the company diversifies beyond video. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 729 | 57,287 | Lightricks' image-to-video model supporting text-to-video, image-to-video, and video-to-video pipelines. It is trending as a strong open alternative for high-fidelity video synthesis. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 726 | 0 | A community LoRA adapter that fine-tunes MiniMax-H3 for text-to-video generation, enabling creative control without full model training. Its zero-download count suggests it is newly released and still accumulating usage. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 462 | 91,455 | A Turbo variant of MiniMax-H3 optimized for faster image-to-video generation while preserving quality. Its strong download count indicates practical utility for production workflows. |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 373 | 1,164 | NVIDIA's voice-optimized conversational model designed for low-latency speech interaction. It targets real-time voice agents and conversational AI applications. |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 133 | 0 | A compact 2.9B text-to-image model based on the Anima architecture. Its small size makes it accessible for local generation with ComfyUI integration. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 216 | 1,292 | A lightweight model using the Bailing hybrid architecture with an MIT license. It is trending among developers seeking a small, permissively licensed option for specific localization tasks. |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 159 | 4,692 | A LoRA adapter that fine-tunes MiniMax-H3 specifically for photorealistic human generation in video. It addresses a key community demand for realistic person depiction in AI-generated video. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 389 | 352,023 | A GGUF-quantized version of Muse-Glimmer-30B by Unsloth, enabling efficient local inference. Its 350K+ downloads highlight strong demand for running large vision-language models on consumer hardware. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,427 | 121,042 | The original 30B image-text-to-text model from Meta's experimental lineup that is gaining rapid adoption. Its multimodal conversational capabilities are attracting attention from researchers and hobbyists alike. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,989 | 2,793,115 | An uncensored community fine-tune of Qwen3.6-27B in GGUF format, combining Fable-Fusion and Heretic styles. Its nearly 2.8M downloads demonstrate enormous demand for unconstrained open-weight conversational models. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,291 | 10,365,210 | A ComfyUI-integrated single-file variant of MiniMax-H3 that has become the most-downloaded model on the entire list. It offers seamless integration for users building video-generation workflows in ComfyUI. |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 257 | 136,783 | The official GGUF conversion of Muse-Glimmer-30B, maintaining the original's vision-language capabilities in an efficient format. It serves users who prefer GGUF over safetensors for local deployment. |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 162 | 4,000 | An FP8-quantized version of the massive 2.4T-parameter Qwen3.8 MoE model, reducing memory requirements significantly. It makes running this 95B-active model more feasible on available hardware. |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 149 | 111,222 | Unsloth's GGUF conversion of MiniMax-H3, enabling efficient local video generation. It extends Unsloth's ecosystem into the video-generation domain alongside their existing LLM tools. |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 483 | 0 | An INT8-quantized ComfyUI-compatible fine-tune of Qwen3-VL-32B with Heretic and H3 variants. It targets users running quantized vision-language models in ComfyUI workflows, though it is newly released. |
| [lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 149 | 652 | A LoRA adapter that rewrites and enhances prompts for MiniMax-H3 video generation, improving output quality through better prompt engineering. It addresses a common pain point in AI video workflows. |
| [SexGod1979/PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 298 | 324 | A community text-to-video fine-tune of MiniMax-H3 with an Apache 2.0 license. Its niche audience and low download count suggest it targets a specific creative community. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 795 | 1,012 | The base 2.4T-parameter MoE conversational model from Qwen, representing one of the largest open-weight architectures available. Its low download count relative to model size suggests it requires significant infrastructure. |

## 3. Ecosystem Signal

The dominant trend this week is the **MiniMax-H3 video-generation ecosystem**, which has spawned an extensive layer of LoRA adapters, GGUF conversions, ComfyUI integrations, and prompt-rewriting tools — a pattern signaling that the base model has achieved production-grade reliability. MiniMaxAI itself is expanding from video into **audio generation** with MiniMax-Music3, mirroring the multi-modal platform strategy seen from DeepSeek and Google. In the **language model space**, DeepSeek's V4 family (Flash and Pro) continues to gain ground, while NVIDIA is shipping **production-oriented quantized variants** (NVFP4, BF16) of its Nemotron Lightning line, indicating a shift from raw capability toward deployment efficiency. The **uncensored community fine-tune** space remains highly active, as demonstrated by DavidAU's Qwen3.6 Heretic variant approaching 2.8M downloads. Open-weight models remain dominant on the leaderboard, though models like Kimi-K3 show that well-promoted proprietary-adjacent releases can capture massive attention when paired with accessible weights.

## 4. Worth Exploring

- **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — The clear flagship of the week with 10,624 likes and 1.87M downloads. Its image-text-to-text pipeline and compressed-tensors support make it a strong choice for multimodal conversational tasks.

- **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — With over 10M downloads, this is the most-downloaded model on the list and essential for anyone building ComfyUI-based video-generation pipelines. It bundles everything needed for immediate use.

- **[unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF)** — Combines Unsloth's quantization expertise with Meta's promising Muse-Glimmer architecture, enabling local inference of a 30B vision-language model on consumer hardware — a practical bridge between capability and accessibility.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*