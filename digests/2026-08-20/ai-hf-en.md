# Hugging Face Trending Models Digest 2026-08-20

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-20 01:38 UTC

---



# Hugging Face Trending Models Digest — 2026-08-20

## 1. Today's Highlights

Kimi-K3 by moonshotai dominates with 10,854 weekly likes, reaffirming the competitive momentum of Chinese open-weight LLMs. The Qwen3.8-27B family is overwhelmingly represented across quantization variants (GGUF, FP8, NVFP4, MLX) and uncensored/abliterated fine-tunes, signaling intense community engagement around accessible 27B-class models. MiniMax-H3 also stands out as a high-impact multimodal generation model, with its ComfyUI port racking over 15 million downloads. Meanwhile, DeepSeek-V4-Flash continues to be a popular workhorse for text generation, and MiniMax-Music3 emerges as the leading text-to-music model on the trending list.

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 10,854 | 2,289,863 | A strong open-weight multilingual chat model using compressed-tensors for efficient inference. It leads the weekly榜 despite not being the highest-downloaded, indicating high community enthusiasm. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 3,549 | 2,330,940 | A fast text-generation variant of DeepSeek-V4 optimized for conversational use. Its massive download count reflects its reputation as a practical, high-throughput open LLM. |
| [deepseek-ai/DeepSeek-V4-Pro-0813](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-0813) | deepseek-ai | 634 | 37,583 | The more capable but newer Pro variant of DeepSeek-V4, released in August 2026. Still early in its lifecycle but shows strong initial interest for demanding reasoning tasks. |
| [meta-models/Muse-Glimmer-30B](https://huggingface.co/meta-models/Muse-Glimmer-30B) | meta-models | 1,702 | 430,313 | A 30B-parameter image-text-to-text conversational model with strong multimodal understanding. Gaining traction as a competitive open alternative in the mid-tier model range. |
| [dots-studio/dots3-note-prev](https://huggingface.co/dots-studio/dots3-note-prev) | dots-studio | 232 | 1,239 | A newer image-text-to-text model from dots-studio, likely a specialized or experimental release. Early-stage model with modest but growing engagement. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,185 | 3,055,205 | A leading image-text-to-video and text-to-video model producing high-quality short video clips. Its open availability has made it one of the most-used video generation models on HF. |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 11,487 | 1,006,235 | The flagship dense Qwen3.8 model with native image-text-to-text capabilities and conversational alignment. The original reference checkpoint that nearly all community variants are built upon. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 1,325 | 555,993 | A diffusion-based image-to-video and text-to-video model supporting multiple video transformation pipelines. Stands out for its flexibility across t2v, i2v, and v2v workflows. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 1,445 | 15,213,225 | The ComfyUI-ready single-file port of MiniMax-H3, enabling plug-and-play video generation in Comfy workflows. Its download count is the highest on the entire list, reflecting massive adoption. |
| [MiniMaxAI/MiniMax-Music3](https://huggingface.co/MiniMaxAI/MiniMax-Music3) | MiniMaxAI | 1,038 | 13,138 | A text-to-music generation model producing structured musical audio from natural language prompts. The first dedicated music-generation model in the current top 30, marking a new category entry. |
| [Comfy-Org/MiniMax-Music-3](https://huggingface.co/Comfy-Org/MiniMax-Music-3) | Comfy-Org | 193 | 325,083 | The ComfyUI-compatible packaging of MiniMax-Music3, enabling integration into existing audio-generation pipelines. Bridges the gap between the original model and the Comfy ecosystem. |
| [lightx2v/Minimax-h3-Turbo](https://huggingface.co/lightx2v/Minimax-h3-Turbo) | lightx2v | 625 | 340,984 | A distilled/turbo variant of MiniMax-H3 aimed at faster image-to-video inference. Trades some quality for significantly reduced generation time, appealing to latency-sensitive users. |
| [Gazingstars123/Anima-2.9B](https://huggingface.co/Gazingstars123/Anima-2.9B) | Gazingstars123 | 270 | 26,566 | A compact 2.9B text-to-image diffusion model packaged for ComfyUI. Targets resource-constrained setups where a small footprint matters without sacrificing usable output quality. |
| [TenStrip/10Eros-Max](https://huggingface.co/TenStrip/10Eros-Max) | TenStrip | 283 | 0 | A fine-tune of MiniMax-H3 extended for enhanced image-text-to-video generation. Zero downloads suggest it was recently published and has not yet been pulled. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates) | froggeric | 1,290 | 0 | A Jinja-based chat template collection fixing known formatting issues in Qwen model conversations. Zero downloads are expected since it is a template repository, not a model checkpoint. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 2,085 | 4,318,134 | An unsloth-optimized GGUF quantization of Qwen3.8-27B, enabling efficient CPU and low-VRAM GPU inference. The highest-downloaded quantized variant, showcasing demand for accessible deployment. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 2,165 | 3,033,363 | A heavily fine-tuned uncensored GGUF variant of Qwen3.6-27B using Heretic and MTP techniques. Its high download count reflects strong community appetite for unrestricted 27B-class models. |
| [Qwen/Qwen3.8-27B-FP8](https://huggingface.co/Qwen/Qwen3.8-27B-FP8) | Qwen | 601 | 1,063,646 | The official FP8-quantized release from Qwen, balancing memory efficiency with minimal quality loss. A go-to choice for serving the 27B model on consumer GPUs with 8–16 GB VRAM. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 467 | 766,812 | An uncensored GGUF conversion of Qwen3.8-27B with MTP (multi-token prediction) support. Appeals to users seeking unrestricted output with faster inference via MTP. |
| [Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) | Qwen | 1,100 | 12,699 | A 2.4 trillion-parameter MoE variant (active 95B) from the Qwen3.8 family, designed for text generation. Represents Qwen's push into extreme-scale sparse models for maximum capability. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 614 | 60,078 | An uncensored FP8 quantization of Qwen3.8-27B, merging the abliterated style with efficient tensor format. Caters to users who want both unrestricted behavior and lower memory footprint. |
| [orcarouter/Qwen3.8-27B-Uncensored-MLX](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-MLX) | orcarouter | 601 | 27 | An MLX-format uncensored variant of Qwen3.8-27B, optimized for Apple Silicon inference. Very low download count indicates a recently released or niche-format offering. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 288 | 131,113 | An aggressively tuned uncensored GGUF variant with MTP, targeting users who prioritize throughput and unfiltered responses. Combines vision and text in a multimodal GGUF package. |
| [unsloth/Qwen3.8-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.8-27B-NVFP4) | unsloth | 288 | 653,042 | An NVFP4 (NVIDIA Float Point 4) quantized variant from unsloth, targeting next-gen GPU architectures. Appeals to users with H100/Blackwell-class hardware seeking maximum throughput. |
| [Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF](https://huggingface.co/Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF) | Blackfrost-AI | 170 | 164,263 | An abliterated GGUF variant of Qwen3.8-27B, removing RLHF alignment restrictions. Part of the broader wave of community abliterations targeting the 27B dense model. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated-GGUF) | huihui-ai | 172 | 94,234 | A GGUF-packaged abliterated Qwen3.8-27B from huihui-ai, known for consistent uncensored conversions. Offers a practical balance between quality retention and unrestricted behavior. |
| [empero-ai/Qwen3.8-27B-Ridge-GGUF](https://huggingface.co/empero-ai/Qwen3.8-27B-Ridge-GGUF) | empero-ai | 197 | 32,454 | A Ridge-quantized GGUF variant from empero-ai, likely employing a specialized quantization method. Targets users seeking alternative quantization approaches beyond standard GGUF. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 188 | 26,472 | An earlier uncensored GGUF release from orcarouter, predating their FP8 and MLX variants. Serves as the baseline community conversion for the Qwen3.8-27B family. |
| [0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF](https://huggingface.co/0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF) | 0bserverx | 160 | 245,266 | A Heretic-processabliterated GGUF variant combining uncensored behavior with Heretic's style alignment. Notable for its significant download count relative to its like count. |
| [huihui-ai/Huihui-Qwen3.8-27B-abliterated](https://huggingface.co/huihui-ai/Huihui-Qwen3.8-27B-abliterated) | huihui-ai | 167 | 7,207 | The safetensors (non-GGUF) abliterated version from huihui-ai, for users who prefer the native format. Lower downloads suggest most users prefer the GGUF port for deployment. |

## 3. Ecosystem Signal

The dominant narrative this week is the **Qwen3.8-27B ecosystem explosion**. The base model has spawned over a dozen community variants spanning every major quantization format (GGUF, FP8, NVFP4, MLX) and uncensored/abliterated style. This signals that the 27B dense checkpoint has become the de facto sweet spot for enthusiasts: large enough to be capable, small enough to run on consumer hardware with quantization. Chinese open-weight families (Qwen, DeepSeek, Kimi, MiniMax) are clearly gaining momentum, outpacing Western counterparts in both volume and community engagement. The **open-weight vs. proprietary** landscape remains firmly in open-weight's favor on HF, with all top performers releasing permissive or Apache-2.0 licenses. Quantization activity is particularly notable—NVFP4 and MLX variants indicate hardware-specific optimization is maturing, while the sheer number of abliterated/uncensored GGUFs reflects sustained community demand for unrestricted inference. MiniMax's entry into video and music generation marks an expansion of Chinese labs into generative media, not just language.

## 4. Worth Exploring

1. **moonshotai/Kimi-K3** — Its 10,854 likes (second only to the top Qwen release) and 2.3M downloads show it has become a mainstream choice. Studying its compressed-tensors approach could reveal efficient serving strategies for other models.

2. **MiniMaxAI/MiniMax-Music3** — As the first music-generation model on the trending list, it represents an emerging category. Its relatively low download count (13K) versus high likes suggests early adopter enthusiasm, making it a model to watch as the text-to-music space matures.

3. **unsloth/Qwen3.8-27B-NVFP4** — NVFP4 is a cutting-edge quantization format targeting NVIDIA's latest hardware. With 653K downloads, it signals that the community is already optimizing for next-gen GPUs, making it a useful case study for future deployment pipelines.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*