# Hugging Face Trending Models Digest 2026-09-03

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-09-03 04:00 UTC

---



# 🤗 Hugging Face Trending Models Digest — September 3, 2026

---

## 1. Today's Highlights

The **Qwen3.8-27B** family dominates this week's rankings, claiming the top spot with over 4.9 million downloads and nearly 14K likes — a clear signal that open-weight, mid-size dense models remain the community's primary focus. Meanwhile, **GLM-5.3-Flash** from zai-org surges with strong multimodal momentum, while **MiniMax-H3** emerges as a standout in video generation with 5.5M downloads. The uncensored/abliterated model sub-ecosystem shows no signs of slowing, with multiple variants of Qwen3.8 and GLM-5.3 climbing the likes charts.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,526 | 94,403 | A dense GLM-family language model built on the new glm_moe_dsa architecture. It's trending as the text-only sibling of the multimodal Flash variant, offering strong conversational performance. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 1,975 | 441,348 | An image-text-to-text model using the glm5_next architecture, bridging vision and language. Its rapid uptake — over 441K downloads — reflects strong community appetite for Chinese open-weight multimodal models. |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,743 | 207,941 | Qwen's latest multimodal model in the qwen4_exp lineage, supporting image-text understanding and conversation. It's gaining momentum as a lighter, faster alternative to the 27B variant. |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,704 | 4,960,483 | The flagship of this week's rankings — a 27B-parameter image-text-to-text model from Alibaba's Qwen team using the qwen3_5 architecture. Nearly 5 million downloads make it the most-used open-weight model in the list by a wide margin. |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 511 | 17,893 | An experimental vision-capable model from DeepSeek's V4 series. Early interest suggests community curiosity around DeepSeek's next-generation multimodal direction. |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 401 | 3,516 | Tencent's Hunyuan V4 preview, a text-generation model from the hy_v4 family. As a preview release, it's drawing attention from researchers tracking Tencent's open-weight trajectory. |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 127 | 429 | A compact 4B parameter text-generation model in the spark2_5 family. Its low download count suggests it's newly released but likely targets edge/low-resource deployment. |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,548 | 14,290,101 | The timeless foundational text-generation model that continues to accumulate downloads years after release. It remains the default reference model for tutorials and experiments. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,586 | 1,232,274 | A diffusion-based image-to-video and text-to-video model from Lightricks. Over 1.2M downloads indicate it's the go-to open-source video generation option for creators and researchers. |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,817 | 5,532,597 | A multimodal text-to-video and image-to-video model from MiniMax, using the minimax-h3 architecture. With 5.5M downloads it's the most-downloaded video model on this week's list, signaling massive community interest in open video generation. |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 250 | 0 | A 4-step distilled variant of the H3 video model using VSA and data-free distillation. Although download count is zero (likely a recent or region-locked upload), its acceleration approach is notable for inference-speed research. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 306 | 0 | Google's latest time-series forecasting model in the TimesFM series, targeting domain-specific predictive tasks. It's newly listed and likely still propagating through the community. |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 363 | 3,086 | A text-to-speech model from the Breeze family, supporting voice generation via the breeze architecture. Modest but steady adoption for TTS applications. |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,402 | 250,280,836 | The legendary sentence-embedding model — over a quarter-billion downloads across multiple frameworks. It remains the default choice for semantic similarity and RAG pipelines. |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,865 | 63,694,017 | The classic masked-language-model backbone with nearly 64M downloads. Still the most widely used foundation for fine-tuning and NLP education worldwide. |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,050 | 6,870,903 | A distilled, lighter counterpart to BERT with nearly 7M downloads. Favored for latency-sensitive deployments where full BERT is overkill. |
| [pipecat-ai/phonellm-alpha-1](https://huggingface.co/pipecat-ai/phonellm-alpha-1) | pipecat-ai | 200 | 6,813 | An alpha-stage phonetics-aware language model from the Pipecat team, built on the nemotron_h architecture. Early-stage but intriguing for voice-conversation research. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 731 | 431,339 | A GGUF-quantized version of Qwen3.8-Flash-Next by Unsloth, optimized for local inference. 431K downloads make it the most-used quantized variant of the Flash model. |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,397 | 9,354,057 | The GGUF-quantized flagship 27B model — over 9.3M downloads, making it the single most-downloaded model on this entire list. It's the go-to for running large Qwen models on consumer hardware. |
| [unsloth/GLM-5.3-Flash-GGUF](https://huggingface.co/unsloth/GLM-5.3-Flash-GGUF) | unsloth | 338 | 63,718 | An English-optimized GGUF quantization of GLM-5.3-Flash, enabling efficient local deployment of the Chinese multimodal model. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 873 | 1,276,092 | An aggressive uncensored fine-tune of Qwen3.8-27B with multi-token prediction, targeting unfiltered creative and role-play use cases. 1.2M downloads show strong niche demand. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,029 | 805,791 | An MLX-formatted abliterated version of Qwen3.8-27B that removes safety alignment. It's the largest abliterated model in the rankings by download count. |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 179 | 56,208 | A research-grade mixed-precision GGUF quantization using GSQ and RCO techniques from ISTA-DASLab. It's notable for pushing the boundaries of low-bit fidelity. |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 195 | 64,325 | An uncensored GGUF variant of the Flash-Next model, designed for unrestricted local inference. |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 153 | 2,576 | An FP8-quantized uncensored version of GLM-5.3-Flash. Low download count suggests a very recent release. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 661 | 254,529 | A community uncensored GGUF fine-tune of Qwen3.8-27B, part of a prolific series of abliterated variants. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 924 | 2,143,289 | A llama.cpp-compatible uncensored GGUF fine-tune of Qwen3.8-27B with MTP support. Over 2.1M downloads make it one of the most-used uncensored variants on the platform. |
| [orcarouter/Qwen3.8-27B-Uncensored-FP8](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-FP8) | orcarouter | 1,373 | 316,128 | An FP8-quantized uncensored version of Qwen3.8-27B. The 1.3K likes rank it among the highest-liked fine-tunes this week. |
| [peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF](https://huggingface.co/peculiar-ragdoll/Tiel-Coder-35B-A3B-GGUF) | peculiar-ragdoll | 195 | 130,086 | A code-specialized MoE model (35B total / 3B active) in GGUF format, using imatrix calibration. It targets developers who need strong coding ability at reduced compute cost. |

---

## 3. Ecosystem Signal

The dominant story this week is the **Qwen3.8-27B ecosystem**, which spans the base model, Flash derivatives, GGUF quantizations, uncensored fine-tunes, FP8 variants, and research-grade mixed-precision builds. This fractal proliferation around a single architecture signals that the open-weight community is converging on Qwen's 27B dense model as a practical ceiling — large enough for strong capability, compact enough for consumer GPU inference when quantized. Unsloth's GGUF versions alone account for over **9.3M downloads**, dwarfing most other releases and underscoring quantization as the primary path to accessibility.

Chinese model families (Qwen, GLM, DeepSeek, Hunyuan) are gaining clear momentum, collectively occupying the majority of top slots. Meanwhile, the **abliterated/uncensored sub-ecosystem** remains highly active — at least six variants across three different authors are climbing the likes charts, indicating sustained demand for unrestricted local models. Video generation is the other hot frontier, with MiniMax-H3 and LTX-2.5 pulling millions of downloads. Notably, quantization innovation is accelerating beyond simple GGUF: GSQ-RCO mixed-precision and FP8 variants from research labs suggest the community is pushing toward even more efficient inference paths.

---

## 4. Worth Exploring

1. **[Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B)** — The undisputed flagship of this week's list. With nearly 5M downloads and 13.7K likes, it represents the current sweet spot for open-weight multimodal models: strong capability at a size that quantized GGUF variants can run on a single consumer GPU.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — A compelling entry in open video generation with 5.5M downloads. If you're building video pipelines or researching controllable text-to-video, this is the model to benchmark against right now.

3. **[ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF)** — The most technically interesting quantization on the list. GSQ+RCO mixed-precision from a research lab could represent the next generation of fidelity-preserving compression, worth studying if you care about pushing quantization beyond standard GPTQ/AWQ approaches.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*