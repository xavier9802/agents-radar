# Hugging Face Trending Models Digest 2026-07-27

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-27 03:43 UTC

---

# Hugging Face Trending Models Digest (2026-07-27)

## Today's Highlights
The week on Hugging Face has seen a surge in **GLM and Qwen-based models**, with `zai-org/GLM-5.2` claiming the top spot for weekly likes while community quantizations of these architectures dominate download counts. **Quantization remains a critical trend**, driven by demand for efficient inference on edge devices; three GGUF versions of Laguna-S-2.1 and multiple quantized Bonsai models reflect this shift toward accessible open-weight LLMs. Meanwhile, **multimodal OCR tools continue to thrive**, with both Baidu’s Unlimited-OCR and several Qwen-Vision variants maintaining high engagement through practical document analysis capabilities. Finally, specialized robotics models from OpenBMB signal growing integration between language models and physical control systems.

---

## 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 704 | 56,445 | A text-generation model optimized for conversational flow and contextual coherence. It gained traction due to its balanced performance across diverse dialogue tasks without excessive resource requirements. |
| [Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 600 | 3,305 | An ultra-large open-weight language model designed for complex reasoning and long-context understanding. Its size and architecture make it notable for pushing boundaries in scalable LLM deployment despite lower download volume. |
| [Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 450 | 14,049 | A compact yet powerful 3B parameter LLM focused on efficient local inference. Rising interest stems from strong output quality relative to footprint, appealing to developers targeting mobile or embedded use cases. |
| [Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 652 | 2,187,304 | A highly quantized 27B-parameter LLM in GGUF format optimized for llama.cpp execution. Massive downloads indicate widespread adoption for fast, low-memory chatbot applications requiring minimal hardware overhead. |
| [Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,052 | 631,970 | Further distilled version of Bonsai using ternary weights (~2-bit precision), offering extreme compression with preserved functionality. High like count suggests community appreciation for aggressive quantization techniques enabling novel deployment scenarios. |

---

## 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,220 | 2,593,460 | Baidu’s flagship image-to-text system excelling at parsing dense layouts, handwritten notes, and multilingual documents. Dominates downloads reflecting real-world utility in digitization workflows where accuracy matters more than novelty. |
| [Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,581 | 34,511 | Emerging multimodal assistant combining vision grounding with natural conversation capabilities. Gaining momentum as users explore hybrid approaches blending image comprehension with dynamic Q&A interactions beyond static captioning. |
| [OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2) | ATH-MaaS | 314 | 35,562 | Next-gen OCR grounded in Qwen-3.5 backbone, improving spatial alignment and table recognition over prior generations. Notable rise indicates maturing field moving toward production-ready industrial-grade scanning solutions. |
| [Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 339 | 1,375 | Microsoft’s diffusion-based tool generating rich scenes from textual prompts with emphasis on artistic style consistency. Early-stage but backed by brand credibility positions contender amid competing generative pipelines. |
| [Cosmos3-Edge](https://huggingface.co/nvidia/Cosmos3-Edge) | nvidia | 125 | 32,700 | NVIDIA’s lightweight variant tuned specifically for edge-device video generation tasks, balancing speed against fidelity metrics critical for latency-sensitive environments like AR interfaces. |

---

## 🔧 Specialized Models (code, math, medical, embeddings)

No entries found matching this category based on available metadata tags such as `code`, `math`, `medical`, or explicit embedding functionalities within provided dataset scope.

---

## 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,114 | 1,927,138 | Aggressively uncensored fork of Qwen-3.6 refined via RLHF-style tuning favoring raw expression freedom over safety constraints. Virality driven primarily by viral sharing among power seeking unrestricted experimentation platforms. |
| [Laguna-S-2.1-GGUF](https://huggingface.co/unsloth/Laguna-S-2.1-GGUF) | unsloth | 203 | 102,684 | Officially sanctioned quantized release authored directly by Unsloth Labs ensuring compatibility with popular frameworks vLLM / llama.cpp simultaneously validating official support pathways for accelerated inference stacks. |
| [Kimi-K2.7-Code](https://huggingface.co/moonshotai/Kimi-K2.7-Code) | moonshotai | 1,298 | 730,129 | Moonshot’s code-specialized adaptation of Kimi-K2.7 streamlining software development lifecycles through intelligent autocompletion plus semantic search across repositories simultaneously serving dual roles as IDE assistant documentation navigator too . |
| [Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,480 | 1,410,054 | Hybrid architecture merging strengths derived from Anthropic principles alongside extended context windows reaching one million tokens unprecedented scope for enterprise knowledge base query resolution without truncation loss whatsoever ! |

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*