# Hugging Face Trending Models Digest 2026-07-26

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-26 03:35 UTC

---

# Hugging Face Trending Models Digest
**Date:** 2026-07-26

## 1. Today's Highlights
The ecosystem is currently dominated by the widespread adoption of Qwen3.6 variants and GLM-5.2, with massive download volumes indicating strong community preference for open-weight multimodal models. There is a significant surge in high-performance quantized formats, particularly GGUF and NVFP4, as users prioritize efficiency without sacrificing the capabilities of large-scale architectures like the 27B and 35B A3B MoE models. Additionally, specialized domains such as OCR and robotics are seeing notable activity, reflecting a shift toward practical, deployable AI solutions on edge devices and specific industrial applications.

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,448 | 707,029 | This conversational model leads in engagement with over 4,400 likes, showcasing robust text-generation capabilities. Its high download count suggests it is becoming a standard baseline for advanced chat applications. |
| [Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B) | Qwen | 2,516 | 6,413,105 | With over 6.4 million downloads, this MoE model is the most downloaded item on the list, highlighting its utility for large-scale deployment. It combines high performance with efficient resource usage, making it a community favorite. |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 638 | 2,114,963 | This 1-bit quantized version of Bonsai-27B offers extreme efficiency while maintaining conversational quality. The massive download volume indicates a strong demand for ultra-low-latency inference options. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,094 | 1,988,680 | An uncensored fine-tune of the popular Qwen3.6 architecture, this model appeals to users seeking unrestricted generation capabilities. Its high engagement reflects ongoing interest in modified base models for creative or adversarial testing. |
| [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,466 | 1,570,995 | This reasoning-focused model leverages a 1M context window, catering to users needing extensive document analysis. The GGUF format ensures it can run efficiently on consumer hardware. |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 664 | 45,260 | A text-generation model from Poolside, likely optimized for specific stylistic or professional tasks. Its moderate but steady growth suggests niche adoption within professional workflows. |

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,110 | 2,564,264 | Baidu’s OCR model leads in likes, offering powerful image-to-text conversion for document processing. Its high download count confirms its status as a go-to tool for accurate text extraction. |
| [moonshotai/Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,277 | 749,449 | While tagged for code, this multimodal model supports image-text interactions, bridging vision and programming tasks. Its compressed-tensor support allows for faster inference in development environments. |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 277 | 1,156 | A text-to-image generation model designed for flow-based synthesis, offering new creative possibilities. Early adoption metrics suggest it is being explored by researchers and artists alike. |
| [nvidia/Cosmos3-Edge](https://huggingface.co/nvidia/Cosmos3-Edge) | nvidia | 121 | 31,759 | Optimized for edge devices, this model brings high-quality video or image generation capabilities to local hardware. Its presence highlights NVIDIA’s push for accessible generative AI at the edge. |

### 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 168 | 841 | A developer-focused coding model built on Qwen3.5 MoE, tailored for software engineering tasks. Its specialized nature limits broad downloads but ensures high relevance for developers. |
| [openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip) | openbmb | 175 | 607 | Designed for robotic manipulation, this vision-language-action model enables precise control in physical systems. It represents the growing intersection of LLMs and robotics. |
| [openbmb/MiniCPM-RobotTrack](https://huggingface.co/openbmb/MiniCPM-RobotTrack) | openbmb | 128 | 379 | Complementing the manipulation model, this variant focuses on tracking and spatial understanding for robots. It underscores MiniCPM’s comprehensive approach to embodied AI. |
| [ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 287 | 33,109 | A specialized OCR model leveraging Qwen3.5, likely offering improved accuracy for complex document layouts. It serves as an alternative to larger general-purpose OCR tools. |

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 548 | 483,845 | A heavily customized GGUF fine-tune of Qwen3.6, featuring uncensored and heretic themes. Its popularity highlights the demand for personalized and unrestricted model variants. |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V5-GGUF) | LuffyTheFox | 153 | 60,643 | Another uncensored GGUF variant, this one based on the Hermes V5 style, offering high-quality roleplay or creative writing capabilities. It caters to users seeking expressive, unfiltered outputs. |
| [unsloth/Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 187 | 71,893 | An Unsloth-optimized GGUF version of Laguna-S-2.1, designed for fast and efficient local inference. This reflects the community’s reliance on Unsloth for speed improvements. |
| [poolside/Laguna-S-2.1-GGUF](https://huggingface.co/poolside/Laguna-S-2.1-GGUF) | poolside | 143 | 76,957 | The official GGUF release from Poolside, providing a standardized quantized format for their Lagua-S-2.1 model. It ensures compatibility with various local inference engines. |
| [poolside/Laguna-S-2.1-NVFP4](https://huggingface.co/poolside/Laguna-S-2.1-NVFP4) | poolside | 135 | 117,106 | An NVFP4 quantized version, optimized for NVIDIA hardware, demonstrating the trend toward hardware-specific optimizations. This format likely offers superior performance on supported GPUs. |
| [conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit) | conradlocke | 539 | 0 | A LoRA adapter for identity editing in Krea-2, allowing precise control over generated images. Although downloads are zero, its high likes indicate strong interest in identity-preserving generation. |
| [fdtn-ai/antares-1b](https://huggingface.co/fdtn-ai/antares-1b) | fdtn-ai | 166 | 5,661 | A small, security-focused language model, ideal for edge deployments where privacy is paramount. Its GraniteMoEHybrid architecture suggests efficient performance for sensitive tasks. |

## 3. Ecosystem Signal
The current landscape is defined by the maturation of the Qwen3.6 and GLM-5.2 families, which have become the de facto standards for open-weight multimodal and text-generation tasks. The sheer volume of downloads for Qwen3.6-35B-A3B (over 6.4 million) signals a mass migration toward highly efficient Mixture-of-Experts (MoE) architectures that balance performance with computational cost. There is also a pronounced trend toward aggressive quantization; GGUF formats dominate the fine-tune category, with several models achieving millions of downloads, proving that lossless or near-lossless compression is now viable for production-grade local inference. Furthermore, the rise of NVFP4 and Unsloth-optimized versions indicates a deeper integration with hardware-specific accelerators, particularly from NVIDIA and specialized inference engines like vLLM. While proprietary models remain influential, the open-source community is rapidly closing the gap through specialized fine-tunes (e.g., uncensored, coding, and robotics) that cater to niche but high-value use cases.

## 4. Worth Exploring
1. **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**: As the most-liked model, it represents the current state-of-the-art in conversational AI among open models. Its high engagement suggests robust performance and reliability, making it an essential benchmark for any new application.
2. **[openbmb/MiniCPM-RobotManip](https://huggingface.co/openbmb/MiniCPM-RobotManip)**: For those interested in embodied AI, this model bridges the gap between language understanding and physical action. It offers a unique opportunity to study how LLMs can be adapted for real-world robotics tasks.
3. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**: With over 2.5 million downloads, this model is a powerhouse for document processing. Exploring its capabilities can provide insights into high-accuracy text extraction techniques that are critical for enterprise automation.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*