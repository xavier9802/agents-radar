# Hugging Face Trending Models Digest 2026-08-13

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-13 02:27 UTC

---



# 🤗 Hugging Face Trending Models Digest — 2026-08-13

---

## 1. Today's Highlights

The MiniMax-H3 video generation family dominates this week's charts, with the base model from MiniMaxAI pulling over 3,700 likes and a sprawling ecosystem of LoRAs, ComfyUI adapters, and GGUF quantizations all gaining traction simultaneously. DeepSeek-V4-Flash-0731 continues its momentum with over one million downloads this week, reaffirming deepseek-ai's open-weight strategy. Meanwhile, Kimi-K3 from moonshotai leads the rankings by raw likes at over 10,500, signaling strong community appetite for its image-text-to-text capabilities. The rise of highly quantized and fine-tuned variants — from NVFP4 to INT8 to custom GGUF — underscores a broader shift toward accessible, deployment-ready open models.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,241 | 1,048,685 | A conversational text-generation model that continues to attract massive adoption, with over one million downloads this week alone. Its Flash variant targets speed without sacrificing output quality. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,584 | 1,565,484 | The most-liked model on this week's list, Kimi-K3 combines image understanding with text generation in a single pipeline. Its 1.5M+ downloads reflect strong interest in moonshotai's open-weight approach. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 207 | 19,250 | NVIDIA's latest Lightning series uses NVFP4 quantization to deliver 30B-parameter efficiency at a fraction of the compute cost. It joins its BF16 counterpart as a key entry in NVIDIA's open-weight lineup. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 117 | 15,740 | The BF16 counterpart to the NVFP4 variant, offering full-precision performance for users who prioritize quality over extreme compression. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 586 | 93,668 | LiquidAI's latest 2.6B text-generation model brings architectural innovations from its Liquid family into a compact, efficient package. |
| [deepgrove/maple-preview](https://huggingface.co/deepgrove/maple-preview) | deepgrove | 346 | 2,049 | A preview release of a mixture-of-experts causal language model from deepgrove, signaling early interest in sparse expert architectures. |
| [inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) | inclusionAI | 319 | 6,148 | The flash variant of inclusionAI's Ling series, targeting faster inference while maintaining conversational quality. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 529 | 978 | Qwen's 2.4T-parameter MoE model offers extreme capacity for complex reasoning tasks, though early adoption shows room for growth. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,718 | 83,484 | The foundational image-to-video model driving an entire ecosystem of community extensions this week. It generates high-quality video from images and text prompts with notable temporal coherence. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,302 | 0 | A 30B image-text-to-text model from meta-models that enables rich visual-language conversation. Its GGUF variant is also available from unsloth. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,259 | 6,798,796 | The most-downloaded model this week by a wide margin, this ComfyUI-ready integration of MiniMax-H3 enables local video generation through the ComfyUI workflow system. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 575 | 39 | Lightricks' latest image-to-video diffusion model supporting text-to-video, image-to-video, and video-to-video pipelines in a single architecture. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 412 | 20,376 | A Turbo variant of MiniMax-H3 optimized for faster image-to-video generation, supporting text, image, and reference video inputs. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 701 | 0 | A LoRA adapter adding Turbo-speed text-to-video capabilities on top of the MiniMax-H3 base, with surprising text-to-audio support as well. |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 193 | 0 | The tiny variant of the Ling series, likely designed for lightweight multimodal experimentation or edge deployment. |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 147 | 0 | A specialized LoRA fine-tune of MiniMax-H3 focused on realistic human figure generation in video output. |
| [lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA](https://huggingface.co/lightx2v/MiniMax-H3-Prompt-Rewriter-LoRA) | lightx2v | 141 | 353 | A prompt-rewriting LoRA that improves MiniMax-H3 video quality by restructuring user prompts into more effective conditioning signals. |
| [Kijai/MiniMax-H3-comfy](https://huggingface.co/Kijai/MiniMax-H3_comfy) | Kijai | 295 | 0 | An experimental ComfyUI integration by Kijai, another contributor to the MiniMax-H3 local-generation ecosystem. |
| [Kijai/MiniMax-H3-experimental](https://huggingface.co/Kijai/MiniMax-H3-experimental) | Kijai | 214 | 0 | A further experimental variant from Kijai, likely testing novel generation parameters or pipeline configurations. |
| [drbaph/MiniMax-H3-Turbo-Lora-ComfyUI](https://huggingface.co/drbaph/MiniMax-H3-Turbo-Lora-ComfyUI) | drbaph | 303 | 0 | A pruned-model LoRA + ComfyUI bundle for accelerated MiniMax-H3 video generation. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [nvidia/NVIDIA-NemotronLabs-VoiceChat-11B](https://huggingface.co/nvidia/NVIDIA-NemotronLabs-VoiceChat-11B) | nvidia | 355 | 653 | NVIDIA's specialized voice-chat model targeting low-latency conversational speech pipelines, part of the growing NemotronLabs series. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,960 | 2,521,093 | An aggressively fine-tuned and quantized Qwen3.6-27B variant with uncensored and heretic capabilities, achieving massive community adoption with over 2.5M downloads. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 666 | 207,990 | Unsloth's GGUF quantization of DeepSeek-V4-Flash-0731, making the popular model accessible for local inference with reduced memory footprint. |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 362 | 0 | Unsloth's GGUF quantization of Meta's Muse-Glimmer-30B, targeting efficient local deployment of the 30B image-text model. |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 241 | 0 | The official GGUF release from meta-models for Muse-Glimmer-30B, preserving the model's image-text-to-text capabilities in quantized form. |
| [ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot](https://huggingface.co/ethanfel/Qwen3-VL-32B-Ultra-Heretic-H3-ComfyUI-INT8-ConvRot) | ethanfel | 477 | 0 | An INT8-quantized, ComfyUI-ready Heretic fine-tune of Qwen3-VL-32B with custom rotation and ConvRot optimizations for efficient local video-model integration. |
| [SexGod1979/PinkCherry_MiniMax-H3](https://huggingface.co/SexGod1979/PinkCherry_MiniMax-H3) | SexGod1979 | 287 | 0 | A community fine-tune of MiniMax-H3 under an Apache 2.0 license, adding a distinct style adaptation for video generation. |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 137 | 781 | Unsloth's GGUF quantization of MiniMax-H3, extending the video generation model to local inference via stable-diffusion.cpp-compatible formats. |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 122 | 3,851 | The FP8-quantized variant of Qwen's 2.4T-parameter MoE model, offering a practical balance between precision and memory efficiency for large-scale deployment. |

---

## 3. Ecosystem Signal

This week's trending list reveals three dominant signals. First, **MiniMax-H3 has spawned a full ecosystem**: from the base model to Turbo LoRAs, ComfyUI integrations, prompt-rewriters, realism adapters, and GGUF quantizations. No single model this week has inspired as many community derivatives, suggesting MiniMax-H3 has struck a productive niche in open video generation. Second, **quantization remains a primary vector for model accessibility** — unsloth continues to be the go-to contributor for GGUF conversions across major model families (DeepSeek, MiniMax-H3, Muse-Glimmer), while community fine-tunes like DavidAU's Qwen variant demonstrate that uncensored/heretic adaptations still drive massive download volume (2.5M+). NVIDIA's NVFP4 quantization for Nemotron 3.5 is a notable proprietary effort toward efficient deployment. Third, the **open-weight vs. proprietary tension persists**: DeepSeek, Qwen, and Kimi all lead by likes and downloads simultaneously, reinforcing that high-quality open models are outpacing closed competitors in community engagement. Meta's Muse-Glimmer entry also signals renewed institutional interest in open multimodal language models.

---

## 4. Worth Exploring

1. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The most consequential model this week. With 3,700+ likes and a thriving derivative ecosystem, it's the clear bellwether for open video generation. Its image-to-video pipeline and the rich LoRA ecosystem make it essential to study for anyone working in generative video.

2. **[deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731)** — Over one million weekly downloads signal sustained, real-world usage beyond hype. As a Flash variant optimized for speed, it represents the growing demand for production-ready open conversational models that don't sacrifice capability.

3. **[DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF)** — A striking data point: 2.5M downloads for a community fine-tune. It demonstrates that the demand for uncensored, locally-deployable models remains enormous, and that GGUF quantization combined with aggressive fine-tuning can outperform many official releases in adoption.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*