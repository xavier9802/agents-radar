# Hugging Face Trending Models Digest 2026-07-23

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-23 01:23 UTC

---

### 1. Today's Highlights

The Hugging Face landscape on July 23, 2026, is dominated by the widespread adoption of ultra-efficient quantization techniques, particularly GGUF and MLX formats, allowing massive models to run locally with minimal resource overhead. Google’s `gemma-4-31B-it` leads in downloads, signaling a strong community preference for accessible, high-performance open-weight language models. Meanwhile, specialized multimodal capabilities are expanding rapidly, with significant traction in OCR, robotics vision-language-action models, and streaming audio processing. The trend toward "uncensored" or heavily fine-tuned variants of base architectures like Qwen and MiniCPM also remains robust, reflecting ongoing developer demand for customizable, unrestricted model behaviors.

### 2. Trending Models

#### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,327 | 12,113,203 | This latest iteration of Gemma offers robust conversational abilities and instruction following at a highly accessible size. Its massive download count indicates it has become a standard baseline for many local inference pipelines. |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,336 | 545,109 | Featuring advanced MoE and DSA architectures, GLM-5.2 delivers superior reasoning capabilities compared to its predecessors. It is trending due to its impressive balance of performance and efficiency for complex text-generation tasks. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 2,712 | 2,237,351 | While primarily an OCR tool, its underlying image-text-to-text pipeline functions as a powerful multimodal language interface. It is trending because of its exceptional utility in document processing and data extraction workflows. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,000 | 1,997,690 | This aggressive, uncensored fine-tune of Qwen3.6 leverages Mixture-of-Experts for efficient inference. It is popular among users seeking unrestricted creative writing and roleplay capabilities without safety filters. |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,416 | 2,133,420 | A heavily quantized GGUF version of a reasoning-focused model inspired by Claude-style outputs. It trends due to its ability to perform long-context reasoning on consumer hardware thanks to its small footprint. |

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,449 | 16,441 | Inkling is a versatile image-text-to-text model designed for nuanced visual understanding and conversation. It is gaining attention for its high-quality multimodal alignment and conversational fluency. |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,223 | 722,058 | Although labeled "Code," this multimodal model excels in interpreting visual code structures and diagrams. It is trending for developers who need to bridge the gap between visual interfaces and executable logic. |
| [nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b) | nvidia | 914 | 590,230 | This streaming ASR model provides real-time speech-to-text capabilities with low latency. It is widely adopted for live transcription applications and voice-enabled AI assistants requiring immediate feedback. |
| [OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize) | OpenMOSS-Team | 308 | 92,265 | Capable of both transcription and speaker diarization, this audio-text model simplifies meeting and interview processing. It is valued for its all-in-one approach to structured audio data analysis. |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 124 | 0 | A new text-to-image generation model from Microsoft using Diffusers. It is currently being explored by researchers for its potential improvements in coherent scene composition and style transfer. |

#### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 154 | 58 | A vision-language-action model specifically tuned for robotic manipulation tasks. It is notable for bridging the gap between high-level language instructions and precise physical robot movements. |
| [nvidia/Nemotron-3-Embed-1B-BF16](https://huggingface.co/nvidia/Nemotron-3-Embed-1B-BF16) | nvidia | 102 | 93,021 | A high-performance embedding model optimized for sentence similarity tasks. It is trending in RAG systems where accurate semantic retrieval is critical for downstream LLM performance. |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 249 | 17,162 | An advanced OCR pipeline that combines image recognition with text extraction. It is preferred for complex document layouts where traditional OCR tools often fail to maintain structure. |

#### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 941 | 432,196 | A 2-bit ternary quantized version of Bonsai, demonstrating extreme compression without significant quality loss. It is popular for running large models on devices with very limited VRAM. |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 595 | 1,404,962 | The standard GGUF quantization of Bonsai-27B, offering a balance between speed and accuracy. It remains a top choice for general-purpose local LLM deployment via llama.cpp. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 321 | 62,842 | A highly specialized uncensored fine-tune with complex naming conventions indicating multiple optimization layers. It attracts users seeking maximum creative freedom and lack of content restrictions. |
| [prism-ml/Bonsai-27B-mlx-1bit](https://huggingface.co/prism-ml/Bonsai-27B-mlx-1bit) | prism-ml | 165 | 25,273 | A 1-bit quantized version optimized for Apple Silicon via MLX. It represents the cutting edge of efficiency for Mac users wanting to run state-of-the-art models locally. |
| [GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF) | GnLOLot | 153 | 51,746 | A tiny 1B parameter model fine-tuned to mimic Claude Opus's reasoning style. It is trending for its surprising capability to perform complex chain-of-thought reasoning on edge devices. |

### 3. Ecosystem Signal

The current ecosystem shows a decisive shift toward **extreme efficiency** and **local accessibility**. The dominance of GGUF and MLX formats across top downloads indicates that developers are prioritizing models that can run on consumer hardware over raw parameter counts. Families like **Bonsai**, **Laguna**, and **Qwen** are seeing massive community engagement through various quantization levels (1-bit, 2-bit, ternary), suggesting that post-training optimization is now as critical as pre-training innovation.

Furthermore, there is a clear trend in **multimodal convergence**. Models are no longer strictly text-only; even "language" models like `Inkling` and `Kimi-K2.7-Code` integrate visual understanding deeply. The rise of **robotics-specific VLA (Vision-Language-Action)** models like `MiniCPM-RobotManip` highlights the expansion of LLMs into physical world interaction. Finally, the persistence of **uncensored/fine-tuned** variants in the top rankings reflects a sustained demand for customizable, unrestricted models for creative and niche applications, despite the availability of robust base models like `Gemma-4`.

### 4. Worth Exploring

1.  **[prism-ml/Bonsai-27B-mlx-1bit](https://huggingface.co/prism-ml/Bonsai-27B-mlx-1bit)**: This model is worth studying for its 1-bit quantization on Apple Silicon. It demonstrates how far efficiency can go while maintaining usability, offering a blueprint for deploying large models on resource-constrained edge devices.
2.  **[openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip)**: For those interested in embodied AI, this model bridges the gap between language understanding and physical action. It provides valuable insights into how multimodal models can be adapted for real-world robotics tasks beyond simple perception.
3.  **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)**: This streaming ASR model is essential for building responsive voice agents. Its ability to provide low-latency transcription makes it a critical component for next-generation interactive AI applications.