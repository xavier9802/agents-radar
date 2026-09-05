# Hugging Face Trending Models Digest 2026-09-05

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-09-05 03:58 UTC

---



# 🤗 Hugging Face Trending Models Digest
**Week of 2026-09-05**

---

## 1. Today's Highlights

Qwen's 27B family dominates the rankings, with the base `Qwen3.8-27B` accumulating nearly 6 million downloads and multiple community GGUF quantizations following close behind. DeepSeek's `DeepSeek-V4-Flash-Vision-Exp` claims the top spot this week with a remarkable ~133K downloads in just one week, signaling strong momentum for their next-gen vision-language flagship. MiniMax-H3 and LTX-2.5 continue to pull massive video-generation interest, while GLM-5.3 and its Flash variant make a strong showing from the zai-org lab. The quantization ecosystem remains highly active, with Unsloth, ISTA-DASLab, and community authors producing multiple GGUF variants of the week's top base models.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) | Qwen | 13,962 | 5,739,341 | A 27B-parameter multimodal LLM from the Qwen team with strong conversational and reasoning capabilities. It is trending as the de facto reference model for a wave of community fine-tunes and quantizations. |
| [Qwen/Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) | Qwen | 4,880 | 351,374 | The faster, more efficient sibling of Qwen3.8-27B, optimized for lower latency while retaining strong image-text understanding. Its "Next" designation signals an iterative improvement cycle driving community adoption. |
| [deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp) | deepseek-ai | 608 | 133,024 | DeepSeek's experimental flash vision model combining high throughput with image-text understanding. It is climbing fast with 608 weekly likes and over 133K downloads in a single week. |
| [zai-org/GLM-5.3-Flash](https://huggingface.co/zai-org/GLM-5.3-Flash) | zai-org | 2,053 | 654,957 | A Flash-optimized multimodal variant of GLM-5.3, offering faster inference for image-text-to-text pipelines. Over 650K downloads in its first week reflect strong interest in the GLM lineage. |
| [zai-org/GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) | zai-org | 1,706 | 303,534 | The full-parameter text-generation model from the GLM-5.3 family, designed for conversational and reasoning tasks. It pairs with the Flash variant to give users a choice between quality and speed. |
| [tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview) | tencent | 437 | 5,684 | Tencent's Hunyuan-based text-generation model still in preview, representing the next iteration of their open-weight LLM line. Early interest is modest but growing as the model matures. |
| [XHToken/Spark-X2.5-4B](https://huggingface.co/XHToken/Spark-X2.5-4B) | XHToken | 481 | 3,524 | A compact 4B-parameter text-generation model aimed at lightweight, efficient deployment. Niche adoption so far, but the 4B size appeals to edge and mobile use cases. |
| [IFM/K2-Horizon-MoVA-36B-A4B](https://huggingface.co/IFM/K2-Horizon-MoVA-36B-A4B) | IFM | 156 | 433 | A large 36B Mixture-of-Experts model from IFM, still in early discovery phase with minimal downloads. Its MoVA architecture and scale make it noteworthy for future benchmarking. |
| [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) | sentence-transformers | 5,519 | 253,789,790 | The perennial favorite embedding model, still accumulating downloads at a staggering rate over 253M. It remains the go-to choice for semantic similarity and retrieval tasks. |
| [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32) | openai | 1,185 | 20,569,141 | OpenAI's foundational vision-language encoder that continues to power zero-shot classification and multimodal pipelines. With over 20M downloads, it remains a cornerstone of the ecosystem. |
| [openai-community/gpt2](https://huggingface.co/openai-community/gpt2) | openai-community | 3,661 | 14,607,268 | The classic text-generation model that endures as an educational and benchmarking staple. Sustained 14.6M downloads attest to its role in onboarding and lightweight experimentation. |
| [google-bert/bert-base-uncased](https://huggingface.co/google-bert/bert-base-uncased) | google-bert | 2,951 | 58,675,189 | Google's iconic masked-language-model backbone, still heavily used for feature extraction and fine-tuning. Its 58.7M download count reflects decades of ecosystem reliance. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 4,912 | 5,118,457 | MiniMax's flagship image-to-video and text-to-video model with over 5M downloads this week. Its strong community engagement and versatile generation pipeline make it a standout. |
| [Lightricks/LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) | Lightricks | 2,795 | 1,399,511 | A diffusion-based video generation model supporting image-to-video, text-to-video, and video-to-video. Nearly 1.4M downloads confirm sustained demand for high-quality open video synthesis. |
| [FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree) | FastVideo | 277 | 0 | A distilled, 4-step accelerated variant of MiniMax-H3 for faster video generation without supplementary data. Worth watching as it matures, though downloads are currently zero. |
| [OpenVDN/vdn-minimax-h3](https://huggingface.co/OpenVDN/vdn-minimax-h3) | OpenVDN | 175 | 0 | A community finetune of MiniMax-H3 targeting video generation improvements. Still in early adoption with no downloads yet, but signals active community iteration on top models. |
| [BreezeBlue/Breeze-TTS-2](https://huggingface.co/BreezeBlue/Breeze-TTS-2) | BreezeBlue | 434 | 5,388 | A text-to-speech model delivering natural-sounding voice synthesis. Modest but growing download numbers suggest a promising entrant in the open TTS space. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | google | 432 | 105,304 | Google's latest time-series forecasting model, now available in native PyTorch. Over 100K downloads indicate strong uptake from the data-science and forecasting community. |
| [facebook/mms-300m](https://huggingface.co/facebook/mms-300m) | facebook | 237 | 12,823 | Meta's Multilingual Speech Model in a 300M-parameter variant for cross-lingual speech recognition and synthesis. Steady adoption in low-resource and multilingual settings. |
| [distilbert/distilbert-base-uncased](https://huggingface.co/distilbert/distilbert-base-uncased) | distilbert | 1,133 | 7,067,963 | A distilled, lighter version of BERT that retains most of its parent's performance. Its 7M+ downloads make it the preferred choice for latency-sensitive deployments. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [unsloth/Qwen3.8-27B-GGUF](https://huggingface.co/unsloth/Qwen3.8-27B-GGUF) | unsloth | 3,514 | 9,951,693 | Unsloth's GGUF quantization of Qwen3.8-27B, optimized for fast inference on consumer hardware. Nearly 10M downloads make it the single most-downloaded model on this list. |
| [ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF](https://huggingface.co/ISTA-DASLab/Qwen3.8-27B-GSQ-RCO-GGUF) | ISTA-DASLab | 315 | 206,575 | An advanced quantization using GSQ (Group-wise Scalar Quantization) and RCO (Residual Codebook Optimization) for mixed-precision efficiency. A technically notable approach for reducing fidelity loss. |
| [unsloth/Qwen3.8-Flash-Next-GGUF](https://huggingface.co/unsloth/Qwen3.8-Flash-Next-GGUF) | unsloth | 788 | 702,251 | Unsloth's GGUF port of the Flash-Next variant, bringing faster inference to the efficient Qwen model family. Over 700K downloads show strong demand for lightweight multimodal LLMs. |
| [HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF](https://huggingface.co/HauhauCS/Qwen3.8-27B-Uncensored-HauhauCS-Aggressive-MTP-GGUF) | HauhauCS | 949 | 1,463,966 | An uncensored, MTP-enhanced GGUF fine-tune of Qwen3.8-27B targeting unrestricted generation use cases. Nearly 1.5M downloads highlight sustained community interest in uncensored variants. |
| [OBLITERATUS/Qwen3.8-27B-OBLITERATED](https://huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED) | OBLITERATUS | 1,090 | 928,393 | An "abliterated" Qwen3.8-27B model that removes specific safety-related neural activations. A technically ambitious project with nearly 1M downloads from the red-teaming community. |
| [JonathanColetti/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/JonathanColetti/Qwen3.8-27B-Uncensored-GGUF) | JonathanColetti | 971 | 2,395,758 | A popular uncensored GGUF fine-tune of Qwen3.8-27B, one of the highest-downloaded quantized variants. Over 2.4M downloads reflect strong demand for unrestricted open-weight models. |
| [orcarouter/Qwen3.8-27B-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-27B-Uncensored-GGUF) | orcarouter | 717 | 276,706 | Another uncensored GGUF variant from the orcarouter collective, continuing the trend of community-driven safety removal. Modest but consistent adoption in the uncensored-model niche. |
| [orcarouter/GLM-5.3-Flash-Uncensored-FP8](https://huggingface.co/orcarouter/GLM-5.3-Flash-Uncensored-FP8) | orcarouter | 183 | 7,782 | An FP8 quantized, uncensored version of GLM-5.3-Flash, targeting memory-constrained deployments. A specialized niche play with early-stage download numbers. |
| [orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF](https://huggingface.co/orcarouter/Qwen3.8-Flash-Next-Uncensored-GGUF) | orcarouter | 232 | 97,994 | The uncensored GGUF port of Qwen3.8-Flash-Next, merging speed and unrestricted generation in a single package. Growing steadily within its target audience. |
| [DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.8-27B-TURBO-Fable-Cold-Fusion-735-882-Heretic-Uncensored-NEO-CODER-MAX-MTP-GGUF) | DavidAU | 184 | 95,226 | A heavily branded, MTP-enhanced uncensored GGUF fine-tune combining multiple community techniques. The long name reflects the layered fine-tuning pipeline behind it. |

---

## 3. Ecosystem Signal

Qwen's 27B family is the clear ecosystem anchor this week, with the base model and its Flash variant serving as the primary source for over a dozen community quantizations and fine-tunes. Unsloth's GGUF conversions are seeing the highest absolute download counts, underscoring that performance-per-dollar inference on consumer hardware remains a top priority. DeepSeek's experimental V4 Flash Vision model is the rising star, posting the highest weekly like-to-download ratio and suggesting that next-generation vision-language models are shifting user attention. The uncensored/abliterated sub-ecosystem continues to expand, with multiple authors producing variants of both Qwen and GLM models using different techniques (MTP, RCO, abliteration). Meanwhile, the video-generation category shows healthy innovation velocity, with fast-distilled variants of MiniMax-H3 appearing within days of the original release. Time-series forecasting also merits attention, as Google's TimesFM 3.0 enters the mainstream HF conversation.

---

## 4. Worth Exploring

1. **[deepseek-ai/DeepSeek-V4-Flash-Vision-Exp](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-Vision-Exp)** — The fastest-rising model on the list. Its combination of vision-language capability with flash-speed inference makes it a compelling candidate for production multimodal pipelines. Worth testing alongside Qwen3.8 for a head-to-head quality comparison.

2. **[google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch)** — A significant step up for Google's time-series lineup, now available natively in PyTorch. Any team working with forecasting or temporal data should evaluate this against their current baseline.

3. **[FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree](https://huggingface.co/FastVideo/FastVideo-FastH3-4-step-Preview-v1-VSA-DataFree)** — If you're doing video generation, the 4-step distilled variant of MiniMax-H3 could be a game-changer for latency-sensitive applications. Monitor its download trajectory as a signal of whether data-free distillation can sustain quality.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*