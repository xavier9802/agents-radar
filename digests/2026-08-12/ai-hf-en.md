# Hugging Face Trending Models Digest 2026-08-12

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-12 02:27 UTC

---



# Hugging Face Trending Models Digest — 2026-08-12

---

## 1. Today's Highlights

MiniMax-H3 dominates the video generation space, with its base model topping the weekly likes chart and spawning a thriving ecosystem of LoRA adapters, GGUF quantizations, and ComfyUI integrations — over 6.8 million combined downloads across its variants. NVIDIA continues to push the open-weight frontier with its Nemotron 3.5 Lightning family, introducing the A3B sparse expert and NVFP4 quantization formats for efficient deployment. Meanwhile, DeepSeek-V4-Flash-0731 remains a community powerhouse with over 1 million downloads, now also available in GGUF via unsloth for local inference.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,159 | 1,048,685 | DeepSeek's latest Flash-tier open model for fast, cost-effective text generation. It is trending due to its strong benchmark performance and massive community adoption for local deployment. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,108 | 0 | Meta's 30B-image-text-to-text conversational model with multimodal reasoning. It is generating strong interest as a native multimodal LLM from a top-tier research lab. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,532 | 1,565,484 | The highest-liked model on the chart, Kimi-K3 is a multimodal conversational model with compressed-tensor support. Its popularity reflects Moonshot AI's growing reputation for long-context, high-quality chat. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 555 | 93,668 | A 2.6B parameter liquid-state text generation model leveraging novel continuous-time dynamics. It is drawing attention as an experimental architecture challenging standard transformer approaches. |
| [inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 307 | 6,148 | Inclusion AI's conversational text-generation model built on a custom Bailing-hybrid architecture. It is noted for its multilingual coverage and efficiency in low-resource settings. |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 336 | 2,049 | A preview release of a mixture-of-experts text-generation model from DeepGrove. Early interest is driven by its sparse MoE design aimed at inference efficiency. |
| [endless-frontier/BigBang-v1](https://huggingface.co/endless-frontier/BigBang-v1) | endless-frontier | 171 | 708 | An image-text-to-text conversational model based on the Qwen3.5 MoE architecture. It is a community-driven effort exploring post-training on MoE backbones. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 137 | 19,250 | NVIDIA's 30B sparse expert model using NVFP4 quantization for extreme efficiency. It represents a new direction in open-weight, highly compressed frontier models. |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 232 | 6,769 | A 3B shield/routing model from Mistral for content moderation and safety classification. It fills a growing niche for open guardrail models in production pipelines. |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 159 | 0 | The tiny variant of Ling-3.0, optimized for edge and low-latency text generation. It extends the Ling family to resource-constrained deployment scenarios. |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 331 | 653 | An 11B voice-enabled conversational model from NVIDIA's NemotronLabs. It targets real-time voice interaction applications with arxiv-backed research. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,585 | 59,368 | MiniMax's flagship image-text-to-video model setting a new bar for generative video quality. It is the anchor of a massive ecosystem of community adaptations and fine-tunes. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 4,022 | 2,892,191 | Baidu's open OCR model for image-text extraction with strong multilingual support. Its near-3 million downloads reflect its utility as a production-grade document understanding tool. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 245 | 39 | A versatile video generation model supporting image-to-video, text-to-video, and video-to-video. It is notable for its single-file diffusion format and flexible pipeline support. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [mistralai/Shieldstral-1.0-3B](https://huggingface.co/mistralai/Shieldstral-1.0-3B) | mistralai | 232 | 6,769 | A safety-routed classifier for content moderation, operating under 3B parameters. It is gaining traction as teams adopt open guardrail models for compliant inference. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 4,022 | 2,892,191 | A high-accuracy optical character recognition model covering 100+ languages. It is widely used in enterprise pipelines for document digitization and receipt parsing. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,216 | 6,798,796 | The most-downloaded model on the list, this ComfyUI single-file package of MiniMax-H3 enables local video generation. Its 6.8M downloads highlight ComfyUI's dominance in the creative AI workflow. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,904 | 2,521,093 | An uncensored, community fine-tuned GGUF variant of Qwen3.6-27B targeting unrestricted creative use. Its 2.5M downloads reflect strong demand for permissive open-weight chat models. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 652 | 207,990 | An unsloth-optimized GGUF quantization of DeepSeek-V4-Flash, enabling fast local inference. It extends the original model's reach to CPU and lower-memory GPU setups. |
| [LiquidAI/LFM2.5-2.6B-GGUF](https://huggingface.co/LiquidAI/LFM2.5-2.6B-GGUF) | LiquidAI | 205 | 111,942 | A GGUF quantized version of LiquidAI's experimental LFM2.5-2.6B model. It allows the liquid-state architecture to run efficiently on consumer hardware. |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 311 | 0 | An unsloth-quantized GGUF release of Meta's Muse-Glimmer-30B for accessible local deployment. It pairs with the original's multimodal capabilities for offline inference. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 655 | 0 | A LoRA adapter that speeds up MiniMax-H3 video generation with minimal quality loss. It is part of the expanding MiniMax-H3 fine-tune ecosystem. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 348 | 20,376 | A Turbo variant of MiniMax-H3 optimized for faster image-to-video inference. It targets creators who need reduced generation latency without significant quality trade-offs. |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 113 | 781 | A GGUF quantization of MiniMax-H3 enabling local video generation on constrained hardware. It extends the H3 ecosystem to ggml-compatible runtimes. |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 279 | 0 | A pruned LoRA adapter for MiniMax-H3 integrated with ComfyUI workflows. It targets users seeking faster generation within the ComfyUI node ecosystem. |
| [lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 134 | 353 | A prompt-rewriting LoRA that enhances MiniMax-H3's input processing for better video output. It is a niche but useful tool for prompt engineering workflows. |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 119 | 0 | A fal-provided LoRA fine-tuned for realistic human figure generation in MiniMax-H3 videos. It addresses a common quality gap in generative video pipelines. |
| [SexGod1979/PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 268 | 0 | An Apache-2.0 licensed fine-tune of MiniMax-H3 with endpoint compatibility. It is notable for its permissive license within a typically restrictive video-gen space. |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 464 | 0 | An INT8-quantized, ConvRot-enhanced Qwen3-VL-32B fine-tune adapted for ComfyUI. It combines heretic-style post-training with aggressive quantization for local use. |
| [Kijai/MiniMax-H3_comfy](https://huggingface.co/Kijai/MiniMax-H3_comfy) | Kijai | 280 | 0 | A ComfyUI integration pack for MiniMax-H3, maintained by a known community contributor. It provides workflow nodes and preprocessing for the H3 video model. |
| [Kijai/MiniMax-H3-experimental](https://huggingface.co/Kijai/MiniMax-H3-experimental) | Kijai | 196 | 0 | An experimental ComfyUI build exploring advanced MiniMax-H3 features and sampling strategies. It serves power users testing the model's capabilities beyond defaults. |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 207 | 0 | A direct GGUF release of Meta's Muse-Glimmer-30B, quantized for local inference. It gives users a standalone quantized option outside of unsloth's build. |

---

## 3. Ecosystem Signal

The MiniMax-H3 family is the defining trend this week, transforming from a single video-generation model into a sprawling ecosystem of over a dozen community adaptations — LoRA adapters for realism and speed, GGUF quantizations for local inference, and ComfyUI integration packs driving nearly 7 million downloads. This mirrors a broader pattern: foundational open models are becoming platform anchors around which dense communities of fine-tunes and tooling organically form.

Open-weight models continue to dominate the trending charts. Every top-tier model listed is open-weight, and quantization activity (GGUF, NVFP4, INT8) is intensifying across the board — unsloth, DavidAU, and community authors are converting frontier models into accessible formats. NVIDIA's introduction of NVFP4 quantization for its Nemotron 3.5 Lightning series signals a push toward ultra-efficient open deployment.

Proprietary boundaries remain clear in video generation, where MiniMax and Lightricks lead, but the gap is narrowing as open models like MiniMax-H3 achieve commercial-grade quality. The rise of safety/routing models (Shieldstral) and OCR specialists (Unlimited-OCR) also reflects a maturing ecosystem where specialized open tools fill gaps left by generalist LLMs.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — With 10,532 likes and 1.5M+ downloads, it is the most engaged-with model on the list. Its compressed-tensor support and strong multimodal conversational performance make it a prime candidate for both research and production use.

2. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — The single most-downloaded model (6.8M) demonstrates the power of ComfyUI as a distribution layer. Studying its adoption reveals how community tooling can amplify a base model's reach far beyond its original audience.

3. **[nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4)** — NVIDIA's first public NVFP4-quantized sparse expert model is a significant technical step. It deserves close study for how it balances 30B total parameters with only 3B active, and whether NVFP4 becomes a new standard for efficient open deployment.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*