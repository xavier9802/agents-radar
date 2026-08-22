# ArXiv AI Research Digest 2026-08-22

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 50 papers | Generated: 2026-08-22 01:36 UTC

---



# ArXiv AI Research Digest — 2026-08-22

## Today's Highlights

Today's submissions reveal a field sharpening its focus on **reliability and evaluation**: multiple papers introduce benchmarks for LLM unlearning, memory reliability, and self-improvement auditing, signaling that the community is moving beyond raw capability toward trustworthiness. There is also notable momentum in **agent systems and recursive self-improvement**, with work on skill transfer, harness optimization, and multi-agent topology design. On the methods side, efficient architectures (CPU-targeted models, MoE hyperparameter transfer) and novel inference-time controls for discrete diffusion show that scaling strategies are becoming increasingly nuanced.

---

## Key Papers

### 🧠 Large Language Models (architecture, training, alignment, evaluation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [ConceptGuard: Benchmarking Context-Sensitive Unlearning in LLMs](http://arxiv.org/abs/2608.20338v1) | Sahil Kale, Ian Harris | Introduces a benchmark evaluating whether models can selectively forget harmful knowledge while retaining related facts — a critical capability as LLMs face deletion and compliance demands. It reveals that current methods fail to preserve context-sensitive knowledge post-unlearning. |
| [Phantom Gains: Auditing Self-Improvement Against a Measured Null](http://arxiv.org/abs/2608.20290v1) | Cheng Xu, Nan Yan, Liming Chen et al. | Demonstrates that claimed self-improvement in LLMs may stem from measurement artifacts rather than genuine capability gains, using controlled LoRA fine-tuning audits. The work urges rigorous baselines before declaring recursive self-improvement achievements. |
| [Inject, Align, Recover: Staged Post-Training for Retrieval-Free Document Knowledge Internalization](http://arxiv.org/abs/2608.20281v1) | Qian Kou, Xiaofeng Shi, Xiaosong Qiu et al. | Proposes a staged fine-tuning approach to internalize document knowledge parametrically, eliminating the need for retrieval at inference time. This enables LLMs to answer questions from bounded corpora without external tool use, useful for private or resource-constrained settings. |
| [MemTrapBench: Benchmarking Cognitive Traps in LLM Memory Use](http://arxiv.org/abs/2608.20202v1) | Mengru Wang, Haozhe Luo, Zhenqian Xu et al. | Evaluates not just whether LLMs retrieve memory correctly, but whether retrieved memories lead to reasoning traps and degraded decisions. It reveals that retrieved memories can mislead models even when accurately recalled — a critical finding for memory-augmented systems. |
| [Daedalus-150M: A Convolution-Attention Hybrid Designed for CPU Inference](http://arxiv.org/abs/2608.20210v1) | Christos Koutsiaris | Designs a small language model from the ground up for 4-bit CPU inference, using full attention in only 6 of 18 blocks. It demonstrates that architecture choices tailored to target hardware outperform models squeezed from larger designs. |
| [Let's Scale Step by Step: Compute-Efficient Hyperparameter Transfer for Large-Scale MoE](http://arxiv.org/abs/2608.20061v1) | Nayeon Kim, Hojin Lee, Yunju Bak et al. | Introduces a stepwise transfer method for learning rates in Mixture-of-Experts models, avoiding prohibitively expensive hyperparameter sweeps at extreme scale. This makes scaling MoE architectures significantly more practical without sacrificing performance. |
| [Which Eviction Policy Should an LLM Cache Use?](http://arxiv.org/abs/2608.20280v1) | Yash Kulkarni, Shubham Harkare, Arvind Suresh Yogesh Babu | Systematically compares seven eviction policies (FIFO, LRU, LFU, ARC, GDSF, SISO, semantic-redundancy) for semantic caches under a unified protocol. Finds that no single policy dominates across workloads, capacities, and encoders — guiding practical cache deployment. |

### 🤖 Agents & Reasoning (planning, tool use, multi-agent, chain-of-thought)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [AI4AI-Bench: Benchmarking LLM Agents in Algorithmic Design for Recursive Self-Improvement](http://arxiv.org/abs/2608.20318v1) | Yizhe Chi, Wenyi Li, Deyao Hong et al. | Benchmarks LLMs on the task of designing better training algorithms for subsequent AI systems — a key step toward recursive self-improvement. It reveals that current agents struggle to produce objectively better optimizers, highlighting the gap to true RSI. |
| [Break It Down, Pass It On: Cross-Task Skill Transfer in LLM Agents](http://arxiv.org/abs/2608.20274v1) | Yiyang Feng, Biddut Sarker Bijoy, Niranjan Balasubramanian et al. | Studies when skills induced from completed tasks transfer reliably across different tasks for LLM agents, and when they harm performance. The analysis provides guidelines for safe skill reuse in growing agent systems. |
| [Task-CoEvolve: Efficient Harness Optimization via Adaptive Validation Task Selection](http://arxiv.org/abs/2608.20169v1) | Atsuyuki Miyai, Kiyoharu Aizawa, Toshihiko Yamasaki | Iteratively rewrites agent harness code based on adaptive validation task selection, achieving substantial gains without updating model weights. It offers a cost-effective alternative to fine-tuning for improving agent systems. |
| [Inducing Task Models from Computer-Use Traces](http://arxiv.org/abs/2608.20319v1) | Yucheng Jiang, Zora Zhiruo Wang, Ruishi Chen et al. | Derives symbolic, auditable task models from passive screenshots and action traces, enabling agents to learn real-world workflows without explicit programming. This bridges the gap between human demonstration and agent deployment in production environments. |
| [Multi-Agent Orchestration with Common-Sense Reasoning for Autonomous Driving](http://arxiv.org/abs/2608.20129v1) | Mehdi Azarafza, Faezeh Pasandideh, Ali Ehteshami Bejnordi et al. | Combines multi-agent LLM reasoning with reinforcement learning for robust autonomous driving in unseen scenarios. The system maintains safety guarantees through RL while leveraging common-sense reasoning for contextual decisions. |

### 🔧 Methods & Frameworks (new techniques, benchmarks, efficiency improvements)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [$TCP_\alpha$: Margin-Controlled Confidence Estimation for Music Information Retrieval](http://arxiv.org/abs/2608.20326v1) | Parampreet Singh, Anushka Singh, Sumit Kumar et al. | Introduces a post-hoc confidence estimation method using margin control to produce reliable uncertainty signals for classification models. It addresses the overconfidence problem in deep neural networks, enabling better human-AI decision trust. |
| [Explainable Transformer Models for Clinical Prediction on EHRs](http://arxiv.org/abs/2608.20315v1) | Jun Ni Du, Lukas Adamek, Maxim Kryukov et al. | Presents BERT-LER, an interpretable BERT-style model for structured electronic health records that jointly optimizes lab prediction and medical event interpretability. It advances the adoption of transformers in clinical settings by providing both accuracy and explainability. |
| [Feature Evolution and Migration during Vision Transformer Training](http://arxiv.org/abs/2608.20134v1) | Joonas Järve, Halil Ibrahim Aysel, Tarun Khajuria et al. | Visualizes feature evolution across network depth and training epochs using Sparse Autoencoders on ViT CLS-token representations. It provides new mechanistic insight into how visual features organize during training, aiding interpretability research. |
| [Discrete Diffusion Inference-Time Control with Nested Sequential Monte Carlo](http://arxiv.org/abs/2608.20123v1) | Lohithsai Yadala Chanchu, Hany Abdulsamad, Christian A. Naesseth | Proposes inference-time steering for discrete diffusion language models via nested Sequential Monte Carlo, without retraining. It extends control-based generation methods beyond particle-based approaches to more scalable sampling. |
| [Orthogonal JEPA: Factorized Predictive States for Latent World Models](http://arxiv.org/abs/2608.20065v1) | Taoyong Cui, Pheng Ann Heng, Wanli Ouyang | Introduces an orthogonal factorization of predictive latent states in Joint-Embedding Predictive Architectures, improving world model learning. The factorization promotes disentangled representations that support better planning and reasoning. |

### 📊 Applications (domain-specific, multimodal, code generation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [G-CARL: Grounded Checklist-Aligned Reward Learning for Medical Report Interpretation](http://arxiv.org/abs/2608.20331v1) | Shiao Xie, Siyu Chen, Jianwei Lv et al. | Aligns reward learning with clinical checklists to produce patient-oriented interpretations of medical reports that are both factually grounded and contextually appropriate. It addresses a key gap in medical VLMs where patient communication needs are often overlooked. |
| [ContractScrub: A Benchmark for Final Review of Legal Contracts](http://arxiv.org/abs/2608.20204v1) | Yejin Bang, Kirsty Fielding, Brandan Oliver et al. | Evaluates LLMs on contract "scrubbing" — the final review of transactional agreements for errors and inconsistencies — a task ideally suited to automation. It provides the first benchmark specifically targeting this high-stakes legal workflow. |
| [When Text and Numbers Disagree: Evidence Arbitration in LLMs](http://arxiv.org/abs/2608.20116v1) | Mattia Carletti, Edward Phillips, Fredrik K. Gustafsson et al. | Studies how LLMs arbitrate between conflicting textual, numerical, and tool-derived evidence in a controlled synthetic setting. It reveals systematic biases in evidence weighting that have implications for agentic and RAG systems. |
| [SaBET-QA: Temporal Knowledge Graph Question Answering](http://arxiv.org/abs/2608.20083v1) | Brahim Touayouch, Mirette Moawad, Dmitry Akulov | Proposes iterative refinement of reasoning states across multiple passes for TKG question answering, overcoming the limits of single-pass pipelines. It enables more accurate multi-step temporal reasoning over evolving knowledge graphs. |
| [DecoVAE: Lightweight Interpretable Trend-Seasonal VAE for Time Series Forecasting](http://arxiv.org/abs/2608.20052v1) | Alexander Marusov, Dmitry Anikin, Alexey Zaytsev | Separates trend and seasonal components in a probabilistic VAE framework with strong interpretability and low memory footprint. It advances practical deployment of probabilistic forecasting in energy, finance, and healthcare domains. |
| [Scale-Aware Pretraining of Time Series Foundation Models via Multi-Patch Token Alignment](http://arxiv.org/abs/2608.20005v1) | Taihua Chen, Xiang Ma, Yixin Zhang et al. | Addresses heterogeneous sampling frequencies in time series foundation models through multi-patch token alignment and hybrid masking. It produces more unified representations across datasets, improving generalization of pretraining. |
| [OenoBench: A Wine-Domain Benchmark for Knowledge-Grounded LLM Evaluation](http://arxiv.org/abs/2608.20106v1) | Nikita Khudov | Presents 3,266 source-anchored multiple-choice questions across six wine-domain pillars and four difficulty tiers for evaluating LLM knowledge grounding. It demonstrates how specialized domain benchmarks can reveal knowledge boundaries missed by general benchmarks. |

---

## Research Trend Signal

Today's ArXiv submissions reveal three converging trends. First, **evaluation and auditability** are becoming central: ConceptGuard, Phantom Gains, MemTrapBench, and ContractScrub all share a focus on rigorously measuring what models can and cannot do, rather than celebrating new benchmarks alone. The community is developing tools to distinguish genuine capability gains from measurement artifacts. Second, **agents are maturing from demos to systems**: papers on skill transfer, harness optimization, and topology design show that agent research is moving toward infrastructure that supports reliable, scalable deployment. Third, **foundation models are expanding into new domains** — time series (DecoVAE, CLaST, Scale-Aware pretraining), medicine (G-CARL, HealMed, BERT-LER), and legal (ContractScrub) — each requiring domain-specific adaptations of architecture, evaluation, and interpretability. The repeated emphasis on interpretability (SAE-Xplainers, Feature Evolution, BERT-LER) alongside capability work suggests the field is treating trustworthiness as inseparable from performance.

---

## Worth Deep Reading

1. **[Phantom Gains: Auditing Self-Improvement Against a Measured Null](http://arxiv.org/abs/2608.20290v1)** — As recursive self-improvement becomes a central claim in the field, this paper provides the methodological rigor needed to validate such claims. Its findings about measurement artifacts will shape how the community evaluates future self-improvement systems.

2. **[AI4AI-Bench: Benchmarking LLM Agents in Algorithmic Design for Recursive Self-Improvement](http://arxiv.org/abs/2608.20318v1)** — This paper tackles one of the most ambitious questions in AI: can an AI system improve its own training process? The benchmark and analysis here will serve as a reference point for the RSI research agenda for years to come.

3. **[Break It Down, Pass It On: Cross-Task Skill Transfer in LLM Agents](http://arxiv.org/abs/2608.20274v1)** — Skill transfer is the key to agents that grow more capable with experience. This paper's framework for understanding when transfer helps versus harms provides practical guidance for anyone building persistent, experience-learning agent systems.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*