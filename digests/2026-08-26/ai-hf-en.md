# Hugging Face Trending Models Digest 2026-08-26

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-26 01:44 UTC

---



# Hugging Face Trending Models Digest — 2026-08-26

## Today's Highlights

Qwen3.8 continues to dominate the open-weight ecosystem, with its 27B parameter variant spawning over a dozen community variants spanning uncensored fine-tunes, GGUF quantizations, and speculative-decoding optimizations. DeepSeek-V4-Flash leads the proprietary-open competition with nearly 3.5 million downloads, while MiniMax's H3 video model and LTX-2.5 signal accelerating momentum in multimodal generation. Abliteration techniques are proliferating as a lightweight alternative to full retraining for removing safety alignments.

---

## Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
|:---|:---|---:|---:|:---|
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 12,716 | 2,945,415 | The flagship open-weight 27B model powering an entire ecosystem of derivatives. It supports image-text-to-text pipelines and has become the default base for community uncensored and quantized variants. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,716 | 3,528,373 | DeepSeek's fast-conversation variant leads in raw download volume among proprietary models. It sets the performance bar that open models now benchmark against. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,996 | 2,865,293 | Moonshot's latest 10.9K-liked model uses compressed-tensors for efficient inference. Its image-text-to-text capability makes it a strong competitor in the Chinese-language multimodal space. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 758 | 74,707 | DeepSeek's Pro variant targets high-accuracy reasoning tasks. Lower downloads but high likes suggest a niche but dedicated professional user base. |
| [ornith-ai/Ornith-1.5-35B-A3B](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B) | ornith-ai | 419 | 70,158 | A 35B MoE model with MIT licensing and endpoint compatibility. Its architecture targets cost-efficient serving while maintaining strong conversational performance. |
| [sensenova/SenseNova-U1.5-8B-MoT](https://huggingface.co/sensenova/SenseNova-U1.5-8B-MoT) | sensenova | 153 | 2,682 | SenseNova's any-to-any multimodal model with native multimodal support. Still early but signals SENS's push into open-weight competitive positioning. |
| [superwhisper/s1-mini](https://huggingface.co/superwhisper/s1-mini) | superwhisper | 238 | 3,474 | A small Qwen3-based model combining text generation and ASR. Its dual pipeline makes it notable for edge deployment in speech-enabled applications. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
|:---|:---|---:|---:|:---|
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,457 | 4,639,786 | The most-downloaded model this week, H3 generates video from text and images using diffusers. Its 4.6M downloads reflect massive creator and studio adoption. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,800 | 833,845 | Lightricks' diffusion-single-file video model supports image-to-video, text-to-video, and video-to-video. Its single-file architecture simplifies deployment for production pipelines. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,246 | 18,705 | MiniMax's text-to-music generator produces high-quality audio from natural language prompts. Early but rapidly gaining traction among content creators. |
| [Audio8/Audio8-TTS-Preview-0.1b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.1b) | Audio8 | 156 | 3,640 | A 0.1B parameter TTS model using the Arktts architecture. Its tiny footprint enables real-time speech synthesis on edge devices. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
|:---|:---|---:|---:|:---|
| [z-lab/Qwen3.8-27B-DFlash2](https://huggingface.co/z-lab/Qwen3.8-27B-DFlash2) | z-lab | 227 | 64,984 | Applies speculative decoding (DFlash2) to Qwen3.8 for accelerated inference. A research-grade optimization that could inform future official releases. |
| [incoai/Qwen3.8-27B-DFlash2](https://huggingface.co/incoai/Qwen3.8-27B-DFlash2) | incoai | 179 | 105,786 | IncoAI's speculative-decoding variant achieves similar speedups with slightly different beam strategies. Higher downloads suggest better out-of-the-box usability. |
| [EschaLabs/Qwen3.8-27B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.8-27B-Escha-W2) | EschaLabs | 127 | 2,319 | A 2-bit quantized Qwen3.8 targeting extreme compression. Still early but represents the cutting edge of aggressive quantization for 27B-class models. |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,468 | 0 | A Jinja-based chat template fix for Qwen models on MLX. Zero downloads but 1.4K likes indicate community appreciation for solving a persistent formatting bug. |
| [peculiar-ragdoll/Qwen-Sharp-Chat-Templates](https://huggingface.co/peculiar-ragdoll/Qwen-Sharp-Chat-Templates) | peculiar-ragdoll | 245 | 0 | Another MLX chat template utility with sharper system-prompt handling. Complements the earlier fix with additional edge-case coverage. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
|:---|:---|---:|---:|:---|
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,918 | 7,334,695 | The most-downloaded GGUF variant at 7.3M downloads. Unsloth's quantization preserves near-lossless quality while enabling CPU and low-VRAM inference. |
| [ornith-ai/Ornith-1.5-35B-A3B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-35B-A3B-GGUF) | ornith-ai | 297 | 1,156,903 | GGUF-quantized Ornith MoE with MIT licensing. Over 1M downloads prove that quantized MoE models are viable for production deployment. |
| [ornith-ai/Ornith-1.5-9B-GGUF](https://huggingface.co/ornith-ai/Ornith-1.5-9B-GGUF) | ornith-ai | 201 | 1,144,037 | The 9B sibling achieves similar download volume, showing strong demand for smaller quantized variants in resource-constrained environments. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 623 | 832,185 | Aggressive MTP (multi-token prediction) uncensored GGUF with 832K downloads. Combines speed optimization with removed alignment constraints. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 722 | 1,525,645 | One of the most-popular uncensored GGUF variants at 1.5M downloads. MTP-accelerated and widely used for local deployment. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 357 | 1,230,831 | Abliteration-based uncensored GGUF with 1.2M downloads. Demonstrates that abliteration is becoming the preferred method over full retraining for removing guardrails. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 751 | 389,747 | The original MLX/Safetensors abliteration that started a trend. 751 likes and 390K downloads show sustained community interest in the technique. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,148 | 249,744 | FP8-quantized uncensored variant balancing speed and quality. The highest-liked uncensored model at 1,148 likes signals strong community validation. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 1,097 | 68,855 | MLX-native uncensored variant for Apple Silicon optimization. 1K+ likes reflect Mac users' demand for locally runnable unfiltered models. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 452 | 154,225 | GGUF-port of the popular uncensored model. Solid downloads confirm cross-format demand for unfiltered Qwen3.8 inference. |
| [orcarouter/Qwen3.8-27B-Uncensored](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored) | orcarouter | 183 | 15,341 | The original safetensors uncensored release that spawned all derivatives. Smaller numbers but foundational to the entire abliteration ecosystem. |
| [DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-Cold-Fusion-GAIN-V1.1-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 240 | 221,918 | Cold-Fusion + GAIN training combined with MTP in a single GGUF package. Represents the cutting edge of technique-combination fine-tuning. |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 277 | 735,183 | "Heretic" branding signals a bold stance in the uncensored movement. 735K downloads make it one of the more popular GGUF abliterations. |

---

## Ecosystem Signal

The Qwen3.8 family has become the de facto reference point for open-weight model evaluation, analogous to how Llama served in 2024–2025. Its 27B variant now has over 15 community derivatives, with abliteration emerging as the dominant technique for producing uncensored variants — surpassing full fine-tuning in both adoption and efficiency. The uncensored/GGUF sub-ecosystem alone has accumulated over 20M combined downloads, demonstrating massive demand for locally deployable, unfiltered inference. GGUF quantization remains the format of choice, with Unsloth's variant alone reaching 7.3M downloads. Meanwhile, speculative decoding (DFlash2, MTP) is transitioning from research to production, with multiple variants targeting latency reduction. The open vs. proprietary battle is heating up: DeepSeek-V4-Flash and Kimi-K3 are closing the gap with impressive download numbers, while MiniMax-H3's 4.6M video downloads show multimodal generation as the next frontier. Apple MLX adoption is surging among abliterated variants, reflecting growing Mac-based local inference demand.

---

## Worth Exploring

1. **[unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF)** — The benchmark GGUF implementation. With 7.3M downloads and 2.9K likes, it's the most battle-tested quantization. Studying its configuration reveals how to balance quality and speed for 27B-class models on consumer hardware.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The most-downloaded model this week at 4.6M. Its image-to-video and text-to-video capabilities using diffusers represent the state of the art in open video generation. Worth examining for both use cases and architecture choices.

3. **[OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED)** — The prototypical abliteration release that catalyzed the entire uncensored derivative ecosystem. Its MLX and safetensors variants offer a clean reference for understanding the abliteration technique versus traditional fine-tuning approaches.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*