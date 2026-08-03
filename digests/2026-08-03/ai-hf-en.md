# Hugging Face Trending Models Digest 2026-08-03

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-08-03 03:35 UTC

---



# 🤗 Hugging Face Trending Models Digest — August 3, 2026

---

## 1. Today's Highlights

Moonshot AI's **Kimi-K3** dominates this week with over 9,600 likes and 837K downloads, establishing itself as the leading new flagship multimodal model. DeepSeek continues to command significant attention with both the base **DeepSeek-V4-Flash** family and its mid-July refinement (**V4-Flash-0731**) ranking prominently. The open-weight ecosystem is experiencing intense quantization and fine-tune activity, particularly around Qwen3.6 and DeepSeek-V4 architectures, while **MiniMax-H3** emerges as a notable new entrant in text-to-video generation.

---

## 2. Trending Models

### 🧠 Language Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,758 | 2,050,533 | A next-generation Chinese multimodal LLM using the GLM-MoE-DSA architecture with strong conversational capabilities. Its 2M+ downloads reflect sustained community adoption of the GLM lineage. |
| [deepseek-ai/DeepSeek-V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash) | deepseek-ai | 1,960 | 2,785,810 | DeepSeek's latest flagship open-weight LLM, achieving remarkable download volume for a flagship release. It sets a new baseline that the community is rapidly quantizing and fine-tuning. |
| [deepseek-ai/DeepSeek-V4-Flash-0731](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-0731) | deepseek-ai | 1,780 | 156,173 | A mid-July refinement of DeepSeek-V4-Flash with updated technical details (arXiv:2606.19348). Strong engagement signals ongoing interest in iterative DeepSeek releases. |
| [poolside/Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 879 | 80,102 | A lean text-generation model from Poolside with an 879-like traction, reflecting strong interest in efficient open-weight alternatives for agentic workflows. |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 720 | 14,863 | Upstage's 250B-parameter open-weight LLM offering a high-capability baseline for the Solar family, with growing interest in its open licensing. |
| [Nanbeige/Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 628 | 33,042 | A compact 3B Chinese LLM with strong community likes for its size, indicating demand for efficient on-device Chinese language models. |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 402 | 13,164 | A code-specialized model based on Qwen3.5 MoE architecture, targeting software development workflows with image-text understanding for code-related tasks. |
| [amd/Instella-MoE-16B-A3B-Think](https://huggingface.co/amd/Instella-MoE-16B-A3B-Think) | amd | 124 | 1,957 | AMD's first entry as a model author — a 16B MoE model optimized for reasoning/thinking tasks on AMD hardware, signaling GPU vendors entering the model ecosystem directly. |

### 🎨 Multimodal & Generation

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 9,661 | 837,202 | Moonshot AI's latest multimodal model combining image and text understanding with text generation. Nearly 10K likes in its debut week make it the clear trending leader. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,783 | 2,536,284 | Baidu's high-performance OCR model with 2.5M+ downloads, demonstrating massive utility demand for document and text recognition pipelines in production. |
| [MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3) | MiniMaxAI | 281 | 0 | MiniMax's first open-weight entry in image-to-video generation, leveraging the diffusers pipeline — a notable move into the competitive video generation space. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,244 | 1,892,654 | An uncensored Qwen3.6-35B vision fine-tune with 1.89M downloads, reflecting the strong community appetite for unrestricted multimodal models. |
| [microsoft/Mage-VL](https://huggingface.co/microsoft/Mage-VL) | microsoft | 192 | 272,148 | Microsoft's multimodal vision-language model with steady adoption, providing an open-weight option for image-text understanding tasks. |
| [owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2) | owensong | 372 | 1,825 | A tiny CPU-friendly text-to-speech model designed for edge and local deployment, appealing to developers needing lightweight speech synthesis. |
| [Audio8/Audio8-TTS-Preview-0.6b](https://huggingface.co/Audio8/Audio8-TTS-Preview-0.6b) | Audio8 | 180 | 4,314 | A 0.6B parameter TTS model (ArkTTS architecture) offering a compact alternative for local speech generation workflows. |
| [lodestones/Kroma](https://huggingface.co/lodestones/Kroma) | lodestones | 129 | 0 | A LoRA-based text-to-image model built on Krea architecture, designed for ComfyUI integration — a new entrant in the generative image space. |
| [XYZAILab/XYZ-Aquila-mini](https://huggingface.co/XYZAILab/XYZ-Aquila-mini) | XYZAILab | 366 | 903 | A compact Qwen3.6-class multimodal model, representing XYZAI's push into efficient small-scale vision-language models. |
| [Comfy-Org/MiniMax-H3](https://huggingface.co/Comfy-Org/MiniMax-H3) | Comfy-Org | 97 | 2 | The ComfyUI-compatible packaging of MiniMax-H3, enabling seamless integration into node-based image-to-video workflows. |

### 🔧 Specialized Models

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 402 | 13,164 | A code-specialized model using Qwen3.5 MoE, built for developer tooling and software engineering tasks with multimodal code理解 capabilities. |
| [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,783 | 2,536,284 | A production-grade OCR pipeline model with exceptional adoption, serving as a workhorse for document digitization and text extraction at scale. |

### 📦 Fine-tunes & Quantizations

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.6-27B-Fable-Fusion-711-Uncensored-Heretic-NM-DAU-NEO-MAX-MTP-GGUF) | DavidAU | 1,345 | 1,372,285 | A heavily fine-tuned GGUF quantization of Qwen3.6-27B with MTP support, representing one of the most downloaded community models this week. |
| [LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF](https://huggingface.co/LuffyTheFox/Qwen3.6-35B-A3B-Uncensored-Genesis-Hermes-V6-GGUF) | LuffyTheFox | 305 | 259,237 | An uncensored Hermes-style fine-tune of the Qwen3.6-35B MoE in GGUF format, popular among users seeking unrestricted conversational capability. |
| [unsloth/Kimi-K3-GGUF](https://huggingface.co/unsloth/Kimi-K3-GGUF) | unsloth | 252 | 88,481 | Unsloth's GGUF quantization of Kimi-K3, bringing the flagship model to accessible GPU and CPU deployments with reduced memory footprint. |
| [unsloth/DeepSeek-V4-Flash-0731-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-0731-GGUF) | unsloth | 344 | 48,707 | Unsloth's quantized version of DeepSeek-V4-Flash-0731, enabling efficient local inference for the latest DeepSeek release. |
| [DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF](https://huggingface.co/DavidAU/Qwen3.5-9B-The-Defiant-Fable-Uncensored-Heretic-NEO-IMATRIX-MAX-MTP-GGUF) | DavidAU | 210 | 292,511 | A community fine-tune of Qwen3.5-9B with Imatrix-calibrated GGUF quantization and MTP, targeting efficient local deployment. |
| [EschaLabs/Qwen3.6-35B-A3B-Escha-W2](https://huggingface.co/EschaLabs/Qwen3.6-35B-A3B-Escha-W2) | EschaLabs | 120 | 2,550 | A fine-tuned Qwen3.6-35B MoE variant from EschaLabs, exploring further optimization of the 35B-A3B architecture. |
| [nota-ai/Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4) | nota-ai | 154 | 68,199 | NVFP4-quantized version of Solar-Open2-250B via vLLM, demonstrating the feasibility of deploying 250B-parameter models with aggressive quantization. |
| [unsloth/Kimi-K3](https://huggingface.co/unsloth/Kimi-K3) | unsloth | 227 | 1,277 | Unsloth-optimized version of the original Kimi-K3 with compressed-tensors support, targeting faster inference without full quantization. |

---

## 3. Ecosystem Signal

The open-weight ecosystem is dominated by **Qwen3.6** and **DeepSeek-V4** as the two most actively quantized and fine-tuned families. GGUF conversions — particularly from DavidAU and Unsloth — are driving the bulk of community engagement, with several Qwen3.6 GGUF variants exceeding 1M+ downloads. The rise of **uncensored/Heretic** fine-tunes (HauhauCS, LuffyTheFox, DavidAU) signals sustained demand for unrestricted models, while **NVFP4 quantization** (Nota-AI's Solar-Open2-250B) pushes the envelope for deploying 250B-parameter models efficiently. Vendor participation is expanding: AMD released its first model (Instella-MoE), and ComfyUI is absorbing video generation models natively. Open-weight continues to outpace proprietary releases in community momentum, with DeepSeek and Qwen families leading adoption.

---

## 4. Worth Exploring

1. **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** — The week's clear leader with 9,600+ likes. Its image-text-to-text pipeline and rapid adoption make it essential to understand, especially for multimodal production workloads.

2. **[MiniMaxAI/MiniMax-H3](https://huggingface.co/MiniMaxAI/MiniMax-H3)** — The only new open-weight image-to-video model on the board. Worth tracking as the video generation space heats up and ComfyUI integration (by Comfy-Org) suggests growing tooling support.

3. **[nota-ai/Solar-Open2-250B-Nota-NVFP4](https://huggingface.co/nota-ai/Solar-Open2-250B-Nota-NVFP4)** — A landmark demonstration that 250B-parameter models can be served via NVFP4 quantization with vLLM. Study this to understand the cutting edge of large-model deployment efficiency.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*