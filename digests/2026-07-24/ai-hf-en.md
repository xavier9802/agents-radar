# Hugging Face Trending Models Digest 2026-07-24

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-24 03:22 UTC

---

# Hugging Face Trending Models Digest
**Date:** 2026-07-24

## 1. Today's Highlights
The ecosystem is currently dominated by the widespread adoption of Qwen3.6 variants, with multiple community fine-tunes and quantizations ranking highly in downloads and likes. Google’s Gemma-4-31B-it continues to show massive utility, securing its spot among the top liked models with over 12 million downloads, indicating strong enterprise and developer trust in open-weight multimodal instruction-tuned models. Meanwhile, specialized tools like Baidu’s Unlimited-OCR and NVIDIA’s Cosmos3-Edge highlight a growing demand for high-efficiency, domain-specific solutions ranging from optical character recognition to edge-compatible video generation.

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)
| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,377 | 596,442 | This MoE-based conversational model leads in engagement with nearly 4.4k likes. It showcases the continued strength of Chinese AI labs in producing high-performance, efficient instruction-tuned architectures. |
| [google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,348 | 12,666,488 | A cornerstone open-weight multimodal LLM with unparalleled download volume. Its high like count reflects sustained community preference for Google’s balanced performance and licensing terms. |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 468 | 362 | Represents the cutting edge of large-scale open-weight language models. Despite lower absolute numbers, its presence signals intense interest in massive parameter counts for complex reasoning tasks. |
| [Motif-Technologies/Motif-3-Beta](https://huggingface.co/Motif-Technologies/Motif-3-Beta) | Motif-Technologies | 174 | 1,856 | An emerging contender in the text-generation space, focusing on feature extraction capabilities. Early traction suggests niche appeal for developers testing next-gen base architectures. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)
| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 2,901 | 2,414,259 | The most downloaded image-text-to-text model, addressing critical document processing needs. Its popularity stems from robust performance in handling diverse, real-world OCR scenarios. |
| [Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice) | Qwen | 1,800 | 2,497,020 | A highly efficient text-to-speech model enabling custom voice cloning at scale. The massive download count indicates strong integration into consumer-facing applications requiring natural audio output. |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,440 | 2,126,755 | A quantized vision-language model optimized for long-context reasoning. It trends due to its ability to process vast amounts of multimodal data efficiently on consumer hardware. |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 190 | 411 | Microsoft’s entry into advanced image generation pipelines, focusing on flow-matching techniques. Though newer, it represents significant corporate investment in open diffusion architectures. |

### 🔧 Specialized Models (code, math, medical, embeddings)
| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,249 | 766,522 | A specialized code-focused multimodal model leveraging compressed tensor technology. It stands out for its efficiency in handling complex programming tasks alongside visual documentation. |
| [nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b) | nvidia | 926 | 750,118 | An ultra-lightweight automatic speech recognition model designed for streaming applications. Its small size and high download rate make it ideal for edge devices and low-latency use cases. |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 165 | 408 | A robotics-specific vision-language-action model for manipulation tasks. It highlights the growing convergence of LLMs with physical control systems in industrial automation. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)
| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 621 | 1,910,116 | A 1-bit quantized version of Bonsai, offering extreme compression for local inference. Its high download volume proves the market demand for running 27B models on limited RAM. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,036 | 2,027,080 | An aggressive, uncensored fine-tune of the Qwen3.6 MoE architecture. It ranks highly in likes due to the community’s appetite for unrestricted creative and roleplay capabilities. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 407 | 334,847 | A heavily customized GGUF quantization focusing on narrative generation ("Fable"). It demonstrates the trend toward hyper-specialized community models for specific stylistic outputs. |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 986 | 576,083 | Features ternary (2-bit) quantization, balancing speed and quality for Bonsai. It is trending due to its superior efficiency metrics compared to standard 4-bit or 8-bit alternatives. |

## 3. Ecosystem Signal
The current landscape is defined by the "Long Tail" of Qwen3.6. While base models like Google's Gemma-4 and Zai's GLM-5.2 maintain foundational dominance, the sheer volume of Qwen3.6-based fine-tunes and quantizations (including uncensored and specialized variants) indicates that the community is prioritizing customization and accessibility over raw base model novelty. Quantization is no longer just an optimization step but a primary distribution format, with 1-bit and 2-bit GGUF models achieving millions of downloads. This suggests a mature ecosystem where local deployment on consumer hardware is the default expectation for advanced models. Furthermore, there is a clear bifurcation between general-purpose reasoning models and highly specialized verticals like OCR (Unlimited-OCR) and Robotics (MiniCPM), signaling that generic LLMs are increasingly being wrapped in domain-specific adapters rather than replaced entirely.

## 4. Worth Exploring
*   **[google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it)**: Essential for any developer needing a reliable, open-weight multimodal model with extensive ecosystem support. Its download volume validates its stability and versatility for production environments.
*   **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**: Critical for applications dealing with document processing. It offers a robust solution for extracting structured data from images, a high-value task often overlooked in favor of pure text generation.
*   **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)**: For users interested in the frontier of quantization, this 1-bit model demonstrates how far inference efficiency can be pushed while maintaining usability, making it a key case study for edge AI.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*