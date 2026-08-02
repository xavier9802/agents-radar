# Hugging Face Trending Models Digest 2026-08-02

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-02 03:33 UTC

---



# Hugging Face Trending Models Digest — 2026-08-02

## 1. Today's Highlights

Kimi-K3 from moonshotai dominates the weekly chart with 9,497 likes and 559K downloads, signaling strong community appetite for its image-text-to-text pipeline. DeepSeek continues its momentum with both the base DeepSeek-V4-Flash and its 0731 checkpoint appearing in the top 10, while Baidu's Unlimited-OCR model racks up 2.4M downloads as a practical multimodal workhorse. The uncensored/fine-tune ecosystem around Qwen3.6 is exceptionally active, with three community variants collectively exceeding 2M downloads, and GGUF quantization from Unsloth and Prism-ML remains a major distribution channel for efficient local inference.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 1,450 | 15,366 | A July-31 checkpoint of DeepSeek's V4 Flash family, featuring an arxiv reference (2606.19348) and strong text-generation throughput. Its rapid uptake indicates developers are already benchmarking the refined weights against the earlier Flash release. |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,738 | 1,683,442 | GLM's fifth major revision brings conversational and reasoning improvements with 1.68M downloads in its first week. The model leverages GLM-MoE-DSA architecture for efficient inference on longer contexts. |
| [deepseek-ai/DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 1,947 | 2,814,414 | The original DeepSeek V4 Flash release remains the most-downloaded LLM in this ranking at 2.8M, reflecting sustained production adoption. Its conversational pipeline and open weights make it a go-to for both research and deployment. |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 718 | 13,426 | Upstage's 250B-parameter Solar Open2 delivers flagship-scale open-weight reasoning and chat capabilities. Early downloads suggest it is being evaluated as a serious open alternative to proprietary models at similar scale. |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,135 | 716,341 | A 2-bit ternary-quantized 27B model using llama.cpp GGUF, enabling high-throughput local inference at extreme compression. Over 700K downloads show strong demand for ultra-low-bit open models. |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 868 | 77,021 | Poolside's Laguna S 2.1 is a text-generation model focused on structured reasoning and data-processing workflows. Its steady download curve reflects niche enterprise interest in its specialized capabilities. |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 611 | 27,892 | A compact 3B parameter model from the Nanbeige line, optimized for efficient local chat and instruction-following. Its lightweight footprint makes it attractive for edge and resource-constrained deployments. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | :---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 9,497 | 559,924 | The clear #1 trending model, combining image understanding with text generation in a single pipeline. Nearly 10K weekly likes reflect exceptional community interest in Kimi's latest multimodal capabilities. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,717 | 2,457,387 | Baidu's OCR engine handles text extraction from images at scale with over 2.4M downloads, making it one of the most-used multimodal tools on the platform. Its feature-extraction pipeline integrates seamlessly into document-processing workflows. |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 173 | 10,525 | Microsoft's Mage-VL is a multimodal vision-language model supporting both image understanding and generation tasks. Its release adds to Microsoft's growing open multimodal portfolio for research and commercial use. |
| [microsoft/Fara1.5-27B](https://huggingface.co/microsoft/Fara1.5-27B) | microsoft | 243 | 2,775 | Fara 1.5 is a 27B vision-language model from Microsoft targeting computer-use scenarios, where the model can interpret screen images and execute actions. Early downloads indicate developer experimentation with agentic vision pipelines. |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 365 | 1,565 | A CPU-friendly, edge-optimized text-to-speech model designed for local and low-resource deployment. Its small footprint and local-TTS focus make it suitable for embedded and mobile applications. |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 169 | 3,254 | Audio8's 0.6B TTS preview model offers a compact speech-synthesis option with feature-extraction support. The early-stage release is drawing attention from developers evaluating lightweight voice generation. |
| [lodestones/Kroma](https://huggingface.co/lodestones/Kroma) | lodestones | 97 | 0 | Kroma is a text-to-image LoRA built on the Krea2/Krea architecture, designed for ComfyUI workflows. Zero downloads suggest it was newly uploaded and has not yet entered active distribution. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 391 | 10,771 | KAT-Coder V2.5 is a code-specialized model built on Qwen3.5 MoE architecture, supporting both text generation and image-text understanding for software engineering tasks. Its dev focus targets developers who need reliable code completion and debugging assistance. |
| [microsoft/VibeVoice-ASR-BitNet](https://huggingface.co/microsoft/VibeVoice-ASR-BitNet) | microsoft | 142 | 5,835 | Microsoft's VibeVoice ASR model uses BitNet quantization for efficient automatic-speech-recognition, reducing memory and compute requirements significantly. The novel quantization approach is drawing interest from researchers working on efficient speech pipelines. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,243 | 1,173,001 | A highly popular uncensored GGUF fine-tune of Qwen3.6-27B, featuring Heretic and MTP enhancements with over 1.17M downloads. Its uncensored nature and aggressive fine-tuning have made it a favorite for unrestricted local deployment. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,227 | 1,823,436 | This uncensored GGUF fine-tune of the Qwen3.6 35B MoE model is the second most-downloaded model overall at 1.82M, with a strong "aggressive" alignment style. Its vision-capable pipeline and 3.2K likes show the uncensored community's continued dominance in download volume. |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 289 | 228,610 | Another Qwen3.6-35B MoE uncensored variant, this time with Hermes V6 alignment and GGUF quantization, accumulating 228K downloads. The Genesis-Hermes lineage continues to be a trusted base for unrestricted local use. |
| [unsloth/Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 243 | 41,337 | Unsloth's GGUF-quantized version of Kimi-K3 enables efficient local inference with reduced memory footprint while preserving the original model's multimodal performance. The 41K downloads indicate strong adoption among users who need Kimi-K3 on consumer hardware. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 292 | 4,048 | A community GGUF conversion of DeepSeek V4 Flash 0731 by Unsloth, bringing quantization and optimization tools to the latest DeepSeek checkpoint. Though newer and with fewer downloads, it benefits from the DeepSeek ecosystem's momentum. |
| [DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 189 | 267,572 | A smaller 9B uncensored GGUF fine-tune from DavidAU's Fable/Heretic series, using Imatrix calibration and MTP for optimized quantization. Its 267K downloads show demand for lighter-weight unrestricted models. |
| [nota-ai/Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 152 | 22,396 | Nota's NVFP4 quantized variant of the 250B Solar Open2 model, optimized for vLLM inference with reduced precision. The quantization approach targets users who want flagship-scale performance without the full GPU memory cost. |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,672 | 59,076 | Inkling is a conversational multimodal model from Thinking Machines with strong image-text understanding and generation capabilities. Its 1.6K likes and growing downloads suggest it is emerging as a competitive open alternative in the generalist multimodal space. |
| [thinkingmachines/Inkling-Small](https://huggingface.co/thinkingmachines/Inkling-Small) | thinkingmachines | 213 | 3,998 | The smaller Inkling variant trades some capability for efficiency, targeting users who need lighter multimodal inference. Early adoption is modest but consistent with the parent model's trajectory. |

---

## 3. Ecosystem Signal

The dominant trend this week is the **Qwen3.6 / Qwen3.5 fine-tune ecosystem**, with three uncensored community variants (DavidAU, HauhauCS, LuffyTheFox) collectively exceeding 3.2M downloads. This signals a powerful gravitational pull around the Qwen architecture for local, unrestricted deployment — a pattern consistent with the prior Qwen3.5 cycle. DeepSeek also maintains strong momentum: both the base **DeepSeek-V4-Flash** (2.8M downloads) and its newer **0731 checkpoint** are trending, with Unsloth providing parallel GGUF conversions that lower the hardware barrier. The open-weight frontier is increasingly competitive — **GLM-5.2** (4.7K likes) and **Solar-Open2-250B** (718 likes) are gaining visibility as large-scale open alternatives, while **Kimi-K3** leads raw engagement at nearly 10K weekly likes, suggesting moonshotai's multimodal approach is resonating widely. Quantization remains a critical distribution layer: GGUF variants from Unsloth, Prism-ML's 2-bit Ternary-Bonsai (716K downloads), and Nota's NVFP4 Solar variant all reflect community investment in making large models runnable on consumer hardware. Microsoft's presence — Mage-VL, Fara1.5, and the BitNet ASR model — shows continued institutional output, though their engagement lags behind the community fine-tune surge.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — The undisputed #1 trending model with nearly 10K likes and 559K downloads. Its image-text-to-text pipeline positions it as a leading open multimodal model; understanding its architecture and capabilities is essential for anyone tracking the current frontier.

2. **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — A pioneering 2-bit ternary-quantized model with 716K downloads. Studying this release offers insight into the cutting edge of extreme weight compression, where inference efficiency is pushed to its limits without catastrophic quality loss.

3. **[deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731)** — The latest DeepSeek V4 checkpoint with an accompanying arxiv paper. For developers evaluating open-weight models for production, this represents the current state of the art in the DeepSeek lineage and warrants direct benchmarking.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*