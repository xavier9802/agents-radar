# Hugging Face Trending Models Digest 2026-08-23

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-23 01:46 UTC

---



# 🤗 Hugging Face Trending Models Digest
**Date:** 2026-08-23

---

## 1. Today's Highlights

Qwen's **Qwen3.8-27B** continues to dominate with over 12,000 weekly likes and nearly 2.1 million downloads, serving as the base for a massive wave of community fine-tunes and quantizations. **Moonshot's Kimi-K3** surged to the #27 spot with 10,929 likes and 2.6M downloads, signaling strong momentum for open-weight multimodal models. Meanwhile, video generation remains a hot frontier — MiniMax-H3 and LTX-2.5 show robust community adoption, while the "abliterated"/uncensored fine-tune ecosystem around Qwen3.8 continues to expand aggressively.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 12,143 | 2,090,699 | The flagship open-weight dense LLM of the Qwen 3.8 line, delivering strong conversational and reasoning performance. Its dominance here reflects its role as the foundational base for a vast ecosystem of community variants. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,929 | 2,612,739 | Kimi K3 is a compressed-tensors multimodal LLM from Moonshot AI with 2.6M downloads, making it one of the most-downloaded open models this week. Its high like count signals strong community endorsement for its image-text capabilities. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,632 | 2,976,281 | DeepSeek V4 Flash is the speed-optimized variant of DeepSeek's latest model family, with nearly 3M downloads showing massive adoption. It offers strong conversational performance at reduced latency, ideal for production use. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 719 | 54,566 | The "Pro" tier of DeepSeek V4 targets higher-end reasoning and instruction-following tasks. Though newer and less downloaded than its Flash counterpart, it attracts users seeking maximum capability. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,146 | 17,386 | A massive 2.4T-parameter Mixture-of-Experts model from Qwen, showcasing the continued push toward extremely large open MoE architectures. Its smaller download count reflects the niche hardware requirements for inference. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,757 | 517,564 | Muse Glimmer 30B is a conversational image-text-to-text model that has gained solid traction with nearly half a million downloads. It competes in the mid-size open multimodal LLM space with strong chat capabilities. |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 202 | 1,913 | A small Qwen3-based model that uniquely combines text generation with automatic speech recognition (ASR). Its niche positioning and very low download count suggest it is an early-stage or experimental release. |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 323 | 12,611 | An efficient MoE model (35B total, 3B active) from the Ornith family, built on Qwen3.5 architecture. Its low download count indicates it is still building community adoption despite its efficient design. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,338 | 3,899,160 | MiniMax-H3 is a text-to-video and image-to-video diffusion model with nearly 3.9M downloads, making it one of the most-used video generation models on the platform. Its high engagement reflects the explosive demand for open video-generation capabilities. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,568 | 694,670 | LTX-2.5 is a single-file diffusion model supporting text-to-video, image-to-video, and video-to-video workflows. Its ~700K downloads and strong like count indicate it is a go-to choice for creators seeking a streamlined video generation pipeline. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,183 | 16,644 | MiniMax-Music3 is a text-to-music generation model from MiniMax's AI lab. Though newly released with relatively low downloads, its strong like-to-download ratio suggests high community interest in its audio capabilities. |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 317 | 0 | A fine-tune of MiniMax-H3 targeting enhanced image-to-video and text-to-video generation. The zero download count likely reflects a very recent upload that has not yet been pulled by the community. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 194 | 29,705 | This model applies DFlash2 speculative decoding to Qwen3.8-27B, enabling faster inference without significant quality loss. Its modest download count reflects its specialized audience of latency-optimized deployment users. |
| [LBH-123-AI/Minimax_h3_latent_Upscaler](https://huggingface.co/LBH-123-AI/Minimax_h3_latent_Upscaler) | LBH-123-AI | 159 | 0 | A latent upscaler built on top of MiniMax-H3 to improve video resolution post-generation. Zero downloads and a regional US tag suggest it is either brand new or has limited discoverability. |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,398 | 0 | A Jinja-based chat template fix for Qwen models, addressing compatibility issues in MLX and other inference frameworks. Zero downloads likely indicate it is used in-code rather than downloaded as a model artifact. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,628 | 6,320,542 | The most-downloaded model this week, this GGUF-quantized version of Qwen3.8-27B from Unsloth enables efficient local inference. Its 6.3M downloads reflect its popularity for on-device and low-resource deployment. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 624 | 1,223,422 | An uncensored GGUF fine-tune with 1.2M downloads, catering to users who prioritize unrestricted generation over aligned behavior. Its high download count highlights sustained demand for open, unfiltered model variants. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 991 | 142,846 | An FP8-quantized uncensored variant of Qwen3.8-27B, balancing memory efficiency with removal of alignment constraints. Its ~143K downloads show a niche but committed user base seeking faster inference without guardrails. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 535 | 164,950 | The "OBLITERATED" abliterated model, available in both MLX and GGUF formats, removes safety alignment from Qwen3.8-27B. Its availability in multiple formats broadens its accessibility across different inference stacks. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 489 | 486,221 | An aggressive MTP (multi-token prediction) fine-tune with uncensored behavior, offering faster token generation alongside unrestricted output. Nearly 500K downloads indicate strong interest in performance-enhanced unfiltered models. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 256 | 635,416 | Another abliterated GGUF variant with 635K downloads, part of the growing wave of community-driven unalignment efforts on Qwen3.8. Its popularity demonstrates the scale of demand for uncensored open-weight models. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 337 | 85,371 | An earlier or alternative GGUF uncensored release from orcarouter, providing another option in the crowded uncensored fine-tune space. Its moderate download count suggests it serves users who prefer this specific variant. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 887 | 34,909 | An MLX-format uncensored fine-tune, targeting Apple Silicon users who want unfiltered inference. The high like count relative to downloads suggests strong community approval from the Mac-based AI developer segment. |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 227 | 505,813 | The "Heretic" abliterated variant with 505K downloads, representing yet another community effort to remove alignment constraints from Qwen3.8. Its branding and naming suggest a deliberate ideological stance within the uncensored movement. |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 245 | 97,247 | A GGUF-quantized model using Ridge regularization during fine-tuning, aiming to improve generalization while maintaining a compact footprint. Its modest download count reflects a more specialized technical audience. |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 193 | 176,969 | Combines Cold Fusion, GAIN training, and MTP for an enhanced GGUF-quantized model with improved generation quality. Its long name and niche approach attract users seeking cutting-edge fine-tuning techniques. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 246 | 21,612 | The non-quantized safetensors version of huihui-ai's abliterated Qwen3.8-27B, for users who prefer full-precision inference. Its lower download count compared to the GGUF variant is expected given the larger file size. |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 233 | 173,935 | The GGUF-quantized version of the Ornith 1.5 MoE model, making the efficient 35B-A3B architecture accessible for local inference. It extends the family's reach to users on constrained hardware. |
| [ornith-ai/Ornith-1.5-9B](https://huggingface.co/ornith-ai/Ornith-1.5-9B) | ornith-ai | 163 | 15,301 | A smaller 9B parameter variant from the Ornith 1.5 family, offering a more accessible entry point for resource-limited setups. Its low download count suggests it is still early in its adoption curve. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 664 | 2,306,777 | The official FP8-quantized release from Qwen, providing a memory-efficient path to running the full 27B model. With 2.3M downloads, it is one of the most popular quantized variants, favored by deployment-focused users. |

---

## 3. Ecosystem Signal

The Qwen 3.8 family is the undisputed center of gravity this week. The base **Qwen3.8-27B** model has spawned over a dozen community variants — abliterated, uncensored, GGUF-quantized, FP8-quantized, MTP-enhanced, and speculative-decoding-optimized — demonstrating the immense velocity of open-weight model iteration. The "abliterated" movement, in particular, has scaled dramatically, with multiple publishers producing variants that strip alignment constraints, collectively accumulating over 1.5M downloads. This signals a robust sub-ecosystem prioritizing unrestricted capability over safety-aligned behavior, fueled by open-weight accessibility.

In parallel, **Kimi-K3** from Moonshot AI is emerging as a serious competitor, with 10.9K likes and 2.6M downloads — a remarkable figure for a newer model. Its compressed-tensors format suggests a focus on efficient deployment, hinting at a trend toward practical, production-ready open models over raw parameter count.

Video generation remains a high-growth category. **MiniMax-H3** leads with 3.9M downloads, and its ecosystem is already spawning fine-tunes and upscalers. The open video-generation arms race is accelerating, with multiple actors (MiniMax, Lightricks) releasing strong competitors.

On the quantization front, GGUF continues to dominate local-inference adoption, while FP8 and MLX formats serve niche but dedicated audiences (Apple Silicon users, memory-constrained deployments). The open-weight vs. proprietary split remains clear: most top-download models are openly licensed, with DeepSeek and Qwen leading the charge in providing production-quality open alternatives to closed systems.

---

## 4. Worth Exploring

1. **[Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8)** — The official FP8 quantization from Qwen offers the best balance of speed, memory efficiency, and quality for the 27B model. With 2.3M downloads, it's the community-vetted choice for deploying Qwen3.8 in resource-constrained environments.

2. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — A compelling new entrant with exceptional download velocity and compressed-tensors support. Worth studying for its architecture choices and how it positions against Qwen and DeepSeek in the open multimodal LLM space.

3. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The leading open video-generation model with nearly 3.9M downloads. Its ecosystem of fine-tunes and upscalers makes it a rich subject for understanding how video-generation toolchains are evolving around a single base model.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*