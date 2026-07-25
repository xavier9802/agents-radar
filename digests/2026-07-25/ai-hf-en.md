# Hugging Face Trending Models Digest 2026-07-25

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-25 03:21 UTC

---

# Hugging Face Trending Models Digest
**Date:** 2026-07-25

### 1. Today's Highlights

The Hugging Face ecosystem is currently dominated by the widespread adoption of the Qwen3.6 architecture, with multiple community fine-tunes and official releases capturing significant download volume and user engagement. Concurrently, Google’s Gemma-4 family continues to demonstrate strong momentum, particularly in multimodal capabilities, while specialized OCR and robotics models like Baidu’s Unlimited-OCR and MiniCPM-RobotManip highlight a shift toward practical, domain-specific applications. Notably, there is a surge in high-efficiency quantization efforts, with GGUF and NVFP4 variants of large models like Laguna-S and GLM-5.2 seeing substantial usage, reflecting the industry's ongoing drive for accessible, on-device inference.

### 2. Trending Models

#### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,416 | 667,403 | This latest iteration from ZhiPu AI offers advanced conversational abilities with significant community traction. Its high like count suggests strong satisfaction with its reasoning and general instruction-following performance. |
| [google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it) | google | 3,360 | 12,629,921 | Google’s latest open-weight model has achieved massive download numbers, indicating widespread enterprise and developer adoption. It excels in multilingual tasks and complex instruction tuning. |
| [Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B) | Qwen | 2,504 | 6,460,680 | The official release of this Mixture-of-Experts model provides efficient high-performance text generation. Its popularity stems from its balance of speed and accuracy in coding and logic tasks. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,019 | 2,500,391 | While primarily an OCR tool, its pipeline classification as image-text-to-text highlights its versatility in document understanding. It is trending due to its robust handling of complex layouts and low-resource languages. |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 613 | 28,992 | A specialized text-generation model optimized for code and technical documentation. It is gaining attention for its efficiency in developer-centric workflows compared to larger generalist models. |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 543 | 1,106 | Upstage’s massive 250B parameter model represents the frontier of open-weight LLMs. Early interest suggests it is being tested for high-complexity reasoning and long-context tasks. |

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 236 | 891 | Microsoft’s new entry in text-to-image generation focuses on coherent flow and editing capabilities. It is notable for integrating seamlessly with existing diffusers pipelines. |
| [nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b) | nvidia | 937 | 797,525 | NVIDIA’s streaming ASR model offers real-time speech recognition with low latency. It is trending for edge devices and live transcription applications due to its small footprint. |
| [nvidia/Cosmos3-Edge](https://huggingface.co/nvidia/Cosmos3-Edge) | nvidia | 113 | 30,303 | This video generation model is optimized for edge deployment, allowing high-quality video synthesis on local hardware. It addresses the growing demand for private, on-device content creation. |

#### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 173 | 559 | Designed for robotic manipulation, this vision-language-action model bridges perception and control. It is gaining niche interest from robotics researchers and developers. |
| [openbmb/MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 124 | 349 | Complementing the manipulation model, this variant focuses on precise object tracking for robotic tasks. It showcases OpenBMB’s expanding suite of embodied AI tools. |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 126 | 396 | A specialized code generation model built on Qwen3.5 MOE architectures. It is trending among developers for its improved debugging and multi-file context understanding. |

#### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 632 | 2,028,115 | This 1-bit quantized version of Bonsai-27B allows running large models on consumer hardware. Its massive download count reflects the critical need for extreme compression without significant quality loss. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,070 | 2,057,103 | An uncensored fine-tune of Qwen3.6 optimized for aggressive roleplay and unrestricted generation. It is highly popular in communities seeking bypasses for standard safety filters. |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,455 | 1,906,539 | This GGUF quantization combines Qwen3.5 backbones with advanced reasoning prompts inspired by Claude. Users are drawn to its ability to handle 1M context windows efficiently. |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 487 | 407,421 | A heavily modified uncensored GGUF model focusing on creative writing and narrative freedom. It retains high engagement due to its specific tuning for "heretic" or unfiltered storytelling styles. |
| [unsloth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 171 | 57,536 | Officially quantized by Unsloth, this model ensures optimal performance on llama.cpp. It is preferred by users who want verified, stable quantizations of the base Laguna model. |

### 3. Ecosystem Signal

The current landscape is defined by the **Qwen3.6 family's** overwhelming dominance in both official and community-driven spaces. With numerous variants ranging from official base models to aggressive, uncensored fine-tunes, Qwen3.6 has become the de facto backbone for many new releases. This suggests that model developers are prioritizing rapid iteration on proven architectures rather than launching entirely new foundational models.

Simultaneously, **quantization technology** is reaching new extremes. The presence of 1-bit models like `Bonsai-27B-gguf` and NVFP4 formats indicates a mature ecosystem focused on maximizing inference efficiency on consumer-grade hardware. The high download counts for these quantized versions highlight a market shift towards accessibility, where running large models locally is becoming feasible without sacrificing too much performance.

Regarding **open vs. proprietary**, while major tech giants (Google, NVIDIA, Microsoft) continue to push boundaries with specialized models like Gemma-4 and Cosmos3, the community activity is heavily skewed towards open-weight models that can be modified. The sheer volume of community fine-tunes for Qwen and GLM architectures underscores the power of open ecosystems in driving innovation and customization faster than closed-source counterparts can match.

### 4. Worth Exploring

1.  **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)**: With over 2 million downloads, this 1-bit quantized model is a fascinating case study in extreme compression. It demonstrates how far quantization has come, allowing a 27B parameter model to run on modest hardware with minimal degradation, making it essential for developers pushing the limits of on-device AI.

2.  **[google/gemma-4-31B-it](https://huggingface.co/google/gemma-4-31B-it)**: As the most downloaded model on this list, Gemma-4 represents the gold standard for open-weight, instruction-tuned models. Exploring its capabilities provides insight into how leading labs are balancing performance, safety, and multilingual support in their flagship open offerings.

3.  **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**: This model stands out for its practical application. With high engagement, it signals a strong demand for robust, versatile OCR solutions that can handle diverse document types. It is worth studying for anyone building applications involving document processing or visual information extraction.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*