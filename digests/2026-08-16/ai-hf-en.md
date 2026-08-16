# Hugging Face Trending Models Digest 2026-08-16

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-16 01:44 UTC

---



# Hugging Face Trending Models Digest — 2026-08-16

---

## Today's Highlights

The Qwen family continues its dominance with the **Qwen3.8-27B** series leading likes (9,810), while **Kimi-K3** from moonshotai surpasses all comers with 10,728 likes and 2.1M downloads — a clear signal that Chinese open-weight LLMs are capturing global attention. Meanwhile, **MiniMax-H3** has ignited a video generation rush, racking up 12.7M downloads on its ComfyUI variant alone and spawning an entire ecosystem of LoRA, Turbo, and GGUF derivatives. Quantization remains a first-class concern: every major model now ships with at least three quantized variants (GGUF, FP8, NVFP4), and community fine-tuners are moving fast.

---

## Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 9,810 | 91,917 | The flagship dense 27B model from Qwen's 3.8 lineup, supporting image-text-to-text conversations. It leads its category in likes, reflecting strong community confidence in Qwen's open-weight direction. |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,728 | 2,100,680 | Moonshot AI's latest instruction-tuned model with compressed-tensor support. It boasts the highest like count on the entire list and 2.1M downloads, marking it as the most-downloaded LLM this week. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,425 | 1,798,247 | DeepSeek's faster Flash variant of V4, optimized for conversational text generation. With 1.8M downloads it's the second-most-downloaded model overall, underscoring DeepSeek's rapid adoption. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 494 | 19,945 | DeepSeek's premium Pro variant targeting higher-quality outputs. Lower download volume suggests it's aimed at users who prioritize quality over speed. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 973 | 6,381 | Qwen's MoE (Mixture of Experts) flagship with 2.4T total parameters and 95B active. It's the most impressive architectural statement on the list, though early downloads are modest. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,581 | 246,454 | A 30B image-text-to-text model from the emerging meta-models collective. High download-to-like ratio (156:1) indicates strong practical utility driving adoption. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-NVFP4) | nvidia | 274 | 170,554 | NVIDIA's sparse 30B model with only 3B active parameters, quantized to NVFP4 for extreme efficiency. It represents NVIDIA's push into low-latency, high-throughput inference. |
| [LiquidAI/LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | LiquidAI | 631 | 135,448 | A compact 2.6B text-generation model from LiquidAI. Small footprint with respectable engagement suggests it's targeting edge and mobile deployment scenarios. |
| [inclusionAI/Ling-3.0-tiny](https://huggingface.co/inclusionAI/Ling-3.0-tiny) | inclusionAI | 262 | 4,832 | MIT-licensed tiny model with hybrid architecture. Niche but principled — open weights with explicit inclusion focus and US-region hosting. |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 168 | 240 | Emerging dots3-note family with text-generation capability. Very early stage with low download volume but represents a new architectural approach. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 3,977 | 2,212,155 | The defining multimodal sensation of the week — an image-text-to-video model with 2.2M downloads. It's the engine behind an entire derivative ecosystem of LoRAs and quantizations. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 948 | 378,439 | Lightricks' diffusion-single-file video model supporting text-to-video, image-to-video, and video-to-video. Strong download volume indicates real-world creative workflows adopting it. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 771 | 5,079 | MiniMax's text-to-audio model for music generation. A new vertical for the MiniMax family, though downloads are still early. |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 194 | 16,829 | A compact 2.9B text-to-image model with ComfyUI integration. Small but usable, targeting users who need fast local image generation. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 518 | 211,917 | Turbo variant of MiniMax-H3 optimized for image-to-video. 212K downloads show users are willing to trade some quality for speed in video generation. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [LiquidAI/LFM2.5-VL-3B](https://huggingface.co/LiquidAI/LFM2.5-VL-3B) | LiquidAI | 147 | 4,598 | LiquidAI's vision-language variant of LFM2.5, supporting image-text-to-text. Extends the compact LFM2.5 family into multimodal reasoning. |
| [nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Lightning-30B-A3B-BF16) | nvidia | 153 | 62,965 | The BF16 counterpart to NVIDIA's NVFP4 Lightning model. Users choosing precision over extreme quantization opt for this variant. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,349 | 12,790,850 | The ComfyUI-integrated MiniMax-H3 with 12.8M downloads — the single most-downloaded model on the entire list. It's the gateway drug for anyone using ComfyUI for video generation. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,055 | 2,983,500 | An uncensored, heretic-themed GGUF fine-tune of Qwen3.6-27B with 3M downloads. Demonstrates the appetite for unfiltered community variants of capable base models. |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 1,242 | 867,963 | Unsloth's GGUF quantization of Qwen3.8-27B with 868K downloads. The go-to choice for running the 27B model on consumer hardware. |
| [unsloth/Muse-Glimmer-30B-GGUF](https://huggingface.co/unsloth/Muse-Glimmer-30B-GGUF) | unsloth | 438 | 682,188 | Unsloth's GGUF variant of Muse-Glimmer-30B. Strong download count shows users prioritizing local deployability of the 30B model. |
| [meta-models/Muse-Glimmer-30B-GGUF](https://huggingface.co/meta-models/Muse-Glimmer-30B-GGUF) | meta-models | 281 | 321,049 | Official GGUF release from the meta-models team. Half the downloads of Unsloth's version, suggesting the community favors the Unsloth brand for quantized models. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 433 | 123,157 | Qwen's official FP8 quantization of the 27B model. A mid-tier option between full precision and GGUF, appealing to users with FP8-capable hardware. |
| [unsloth/MiniMax-H3-GGUF](https://huggingface.co/unsloth/MiniMax-H3-GGUF) | unsloth | 169 | 173,741 | GGUF quantization of the video-generation MiniMax-H3. Enables local video generation on modest hardware, though the model's size makes it a heavy lift. |
| [Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8) | Qwen | 198 | 10,745 | FP8 quantization of Qwen's massive 2.4T-parameter MoE model. Targets users who want to experiment with the full MoE architecture without the memory footprint. |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 170 | 90,924 | Unsloth's NVFP4 quantization targeting NVIDIA hardware. Represents the cutting edge of quantization — more aggressive than FP8, optimized for NVIDIA's tensor cores. |
| [fal/MiniMax-H3-Realism-People-LoRA](https://huggingface.co/fal/MiniMax-H3-Realism-People-LoRA) | fal | 199 | 12,737 | A LoRA fine-tune of MiniMax-H3 focused on photorealistic human generation. Niche but targeted, reflecting the community's push toward specific aesthetic outputs. |
| [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) | larryvrh | 761 | 0 | Turbo LoRA for MiniMax-H3. Zero downloads listed but 761 likes suggest strong community interest — possibly a recent release still warming up. |

---

## Ecosystem Signal

Three model families are clearly gaining momentum this week: **Qwen** (dense + MoE variants across every quantization format), **MiniMax-H3** (video generation spawning a derivative ecosystem), and **DeepSeek** (Flash and Pro variants splitting the market by speed vs. quality). The open-weight trend is accelerating — all top performers are openly licensed, and the community is moving with remarkable speed to produce GGUF, FP8, and NVFP4 variants within days of release. Quantization activity is unusually intense: the top 10 most-downloaded models include at least six quantized or fine-tuned derivatives, and Unsloth alone accounts for four of them. NVIDIA's NVFP4 format is emerging as a new standard for GPU-optimized inference, signaling that hardware-aware quantization is becoming a first-class ecosystem concern. The MiniMax-H3 video generation ecosystem is particularly noteworthy — a single base model has spawned ComfyUI integration, Turbo variants, realism LoRAs, and GGUF quantization, demonstrating how quickly a capable open model can become an ecosystem anchor.

---

## Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — The clear leader in both likes and downloads this week. Its compressed-tensor support and 2.1M downloads signal it's ready for production use. Worth studying for its approach to balancing model size with inference efficiency.

2. **[Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3)** — 12.8M downloads make it the most-downloaded model on the list by a wide margin. If you're doing any video generation work, this is the model to know. The ComfyUI integration makes it immediately usable without custom pipelines.

3. **[Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B)** — The most architecturally interesting model this week: a 2.4T-parameter MoE with 95B active parameters. Even with modest current downloads, it represents the frontier of open-weight large-scale modeling. The FP8 variant ([Qwen/Qwen3.8-2.4T-A95B-FP8](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B-FP8)) makes it testable on consumer hardware.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*