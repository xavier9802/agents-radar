# Hugging Face Trending Models Digest 2026-07-28

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-28 03:14 UTC

---

# 🌐 Hugging Face Trending Models Digest — July 28, 2026

## Today's Highlights
Qwen3.6 emerges as the dominant force on Hugging Face Hub this week, with multiple fine-tuned versions (including **Qwen/Qwen3.6-35B-A3B** and several GGUF/uncensored variants) collectively amassing over 10 million downloads — underscoring strong developer adoption for large-scale multimodal reasoning. Concurrently, quantization trends continue to surge, particularly around **Laguna-S-2.1** and **Bonsai-27B**, where GGUF models prioritize edge deployment and low-latency inference. Multimodal capabilities are also gaining traction, especially in vision-language tasks like OCR (**Unlimited-OCR**) and image-text-to-dialogue (**Kimi-K3**, **Inkling**), indicating a pivot toward real-world interactive AI applications. Meanwhile, small but impactful innovations appear in niche domains such as local text-to-speech (**Inflect-Micro-v2**) and identity-preserving image editing (**krea2-identity-edit**), reflecting growing interest in accessible, privacy-conscious AI tools.

---

## 🧠 Language Models (LLMs, chat models, instruction-tuned)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B) | Qwen | 2,548 | 6,187,853 | A high-performance MoE-based conversational model excelling at complex reasoning and long-context understanding. Its widespread popularity reflects demand for open, scalable LLMs that rival proprietary systems in quality and accessibility. |
| [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,553 | 1,003,547 | An efficient yet powerful conversational language model optimized for dialogue and task completion. With robust performance across benchmarks and strong community support, it’s becoming a go-to choice for developers seeking reliable open alternatives. |
| [upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 630 | 3,761 | One of the largest publicly available models designed for general-purpose reasoning and generation. Though fewer downloads than expected due to size constraints, its architectural sophistication signals growing confidence in massive open-weight transformers. |

---

## 🎨 Multimodal & Generation (image, video, audio, text-to-X)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 6,511 | 2,850 | A leading image-text-to-text system known for exceptional multimodal alignment and compression efficiency. As one of the most liked recent releases, it represents rapid innovation in compact yet powerful visual reasoning engines. |
| [thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,606 | 36,196 | Specialized in conversational multimodal interactions between images and natural language. Its rising engagement suggests increasing utility in customer service, education, and assistive technologies requiring intuitive visual-audio dialogue. |
| [microsoft/Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 393 | 1,691 | Enables seamless text-to-image generation using advanced diffusion pipelines backed by Microsoft’s infrastructure. While download numbers remain modest early on, integration potential within enterprise workflows makes this noteworthy for future scaling. |

---

## 🔧 Specialized Models (code, math, medical, embeddings)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 245 | 5,312 | Focused specifically on code-related tasks through image-text-to-text pipelines targeting programming assistance or syntax analysis. Though currently downloaded less frequently, specialized niche development remains critical for full-stack AI ecosystems. |

*(No other models fit strictly under "specialized" categories without overlap into fine-tuning/generation; hence omitted per instructions.)*

---

## 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

| Model | Author | Likes | Downloads | Summary |
| :--- | :--- | ---: | ---: | :--- |
| [prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 659 | 2,257,928 | Highly popular GGUF-quantized version of Bonsai enabling efficient deployment on consumer-grade GPUs via llama.cpp. Near-zero memory footprint while retaining strong conversational ability drives massive usage among hobbyists and edge developers alike. |
| [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,133 | 1,894,395 | Aggressively tuned variant prioritizing unrestricted output generation for experimental research or creative exploration. High like count indicates active user base pushing boundaries of ethical openness despite inherent risks associated with unfiltered models. |
| [poolside/Laguna-S-2.1-GGUF](https://huggingface.co/poolside/Laguna-S-2.1-GGUF) | poolside | 154 | 85,554 | Lightweight quantized Luna-series transformer ideal for mobile/serverless environments. Despite lower likes compared to peers, consistent install volume proves viability for distributed computing setups favoring speed over peak accuracy. |

---

## Ecosystem Signal

The landscape reveals clear momentum toward **MoE architecture proliferation**, particularly centered around Qwen3.x and GLM families, which balance scalability with computational frugality via sparse activation mechanisms. Simultaneously, there's evident democratization driven by **GGUF-driven quantization movements**, allowing non-AI practitioners to run heavy models locally — exemplified by prism-ml’s Bonsai achieving >2M downloads primarily thanks to compatibility with llama.cpp frameworks. Open-source dominance continues solidifying: nearly every top-performing model originates from transparently licensed repositories, contrasting sharply against locked-down corporate equivalents even when matched functionally. Community-led adaptations thrive too — note how “uncensored” prefixes correlate strongly with elevated download metrics among certain user segments eager for freedom-of-expression experimentation zones without compromising underlying technical fidelity.

Furthermore, emerging evidence points to rising preference for **compressed tensor formats** (safetensors + custom packings), reducing storage/bandwidth overheads significantly during transfer/download phases. This shift aligns perfectly with global efforts optimizing AI resource distribution amid tightening cloud budgets and expanding green computing initiatives. Finally, micro-edge innovations hint at impending fragmentation beyond centralized hubs — smaller teams now routinely ship targeted solutions tailored for specific use cases rather than monolithic universals, fostering richer diversity overall.

---

## Worth Exploring

🔹 **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** – Exceptional versatility combined with industry-leading scale (over 2.6M weekly downloads). Ideal candidates should evaluate its role in document digitization, legal processing, or archival restoration projects needing robust character recognition regardless font/style variations.

🔹 **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** – Combines contextual depth (1M tokens!) with clever compression tricks suitable for remote teams managing extensive logs/conversation histories efficiently. Researchers studying memory retention dynamics across varied input lengths will find here fertile ground for hypothesis testing.

🔹 **[owensong/Inflect-Micro-v2](https://huggingface.co/owensong/Inflect-Micro-v2)** – Surprisingly rich functionality packed into tiny form factor (<5MB?). Perfect prototyping target for embedded devices requiring voice response sans internet dependency — think smart speakers offline fallback modes or accessibility aids deployed in rural areas lacking broadband connectivity.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*