# ArXiv AI Research Digest 2026-08-05

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 50 papers | Generated: 2026-08-05 03:13 UTC

---



# ArXiv AI Research Digest — 2026-08-05

---

## Today's Highlights

Today's submissions are dominated by advances in **test-time scaling** and **efficient inference**, with three papers directly addressing how to allocate compute dynamically during LLM reasoning. There is also strong momentum in **agent self-improvement**, as multiple benchmarks (PAST-Bench, ContinualSkillBench) probe whether agents can turn accumulated experience into lasting capability gains. Meanwhile, domain-specific applications continue to mature rapidly—particularly in healthcare (CARE-X, ADMITBench) and legal/structured text (ANNOTARES, ParVL for multimodal scaling)—signalling a shift from capability demos toward production-grade evaluation.

---

## Key Papers

### 🧠 Large Language Models (architecture, training, alignment, evaluation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [ParVL: Parallel Scaling and Expandable Compute Allocation for Multimodal LLMs](http://arxiv.org/abs/2608.04010v1) | Yang Yang, Qinyu Zhao, Mouxiang Chen et al. | Proposes a parallel scaling strategy that dynamically allocates compute across modalities instead of relying on rigid fixed allocations. It reduces memory and latency overhead in MLLMs, making large-scale multimodal training more practical. |
| [Test-Time Scaling in Reasoning LLMs: Inference Regimes, Evaluation, and Reproducibility](http://arxiv.org/abs/2608.04001v1) | Mohsen Hariri, Weicong Chen, Nahal Shahini et al. | Provides a unified taxonomy and reproducibility audit of test-time scaling methods, distinguishing single-trajectory deliberation from multi-candidate voting. The paper establishes baseline protocols to compare approaches fairly. |
| [Cross-Model KV Cache Transfer in LLM Families: A Closed-Form Linear Mapping for Prefill Reuse](http://arxiv.org/abs/2608.03893v1) | Taekyung Heo, Rasoul Shafipour, Ritchie Zhao et al. | Introduces a closed-form linear mapping that transfers KV caches across differently-sized models in a family, eliminating redundant re-prefill at deployment time. This enables cost-quality cascading and mid-conversation model switching with near-zero latency penalty. |
| [Omega-S: A Functional Resilience Index for LLM Fine-Tuning](http://arxiv.org/abs/2608.03887v1) | Alberto Acedo | Defines a drop-in regularization penalty computed solely from the current weight matrix, requiring no stored copies of old weights or Fisher information. It offers a lightweight metric and safeguard against catastrophic forgetting during fine-tuning. |
| [Logic Before Language: Pre-pretraining on Formal Derivations Fosters Skill Acquisition and Compressibility](http://arxiv.org/abs/2608.03930v1) | Jo-Ku Cheng, Nikolaos Aletras, Marco Valentino | Shows that pre-pretraining on symbolic formal derivations—not just procedural tasks—accelerates natural language acquisition and improves representational compressibility. The approach closes the gap left by narrow pre-pretraining primitives like Dyck languages. |

### 🤖 Agents & Reasoning (planning, tool use, multi-agent, chain-of-thought)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [TurnSight: Turn-Level Hindsight Self-Distillation for Tool-Integrated Reasoning](http://arxiv.org/abs/2608.04007v1) | Changle Qu, Sunhao Dai, Hengyi Cai et al. | Introduces turn-level hindsight self-distillation that improves credit assignment in long-horizon tool-use trajectories. It outperforms trajectory-level RL baselines by supervising individual tool interactions rather than full rollouts. |
| [WorldCup Arena: Prospective, Leakage-Free Evaluation of Frontier LLMs on a Live Tournament](http://arxiv.org/abs/2608.04008v1) | Zhenran Wang, Zhonghan Bian, Jinsong Li et al. | Pilots a leakage-free prospective benchmark over the 2026 FIFA World Cup, evaluating LLMs on real-time match forecasting without post-hoc answer leakage. It sets a new standard for temporal, out-of-distribution evaluation of language models. |
| [Video-DeepResearch: Towards the Next-Generation Multimodal Deepresearch Agent](http://arxiv.org/abs/2608.03979v1) | Zhen Fang, Yu Zeng, Wenxuan Huang et al. | Extends multimodal research agents from static images to continuous video streams, demanding dense spatiotemporal grounding alongside open-web exploration. Identifies modality bias and sparse grounding as the two primary bottlenecks in current models. |
| [PAST-Bench: Benchmarking the Foundations of Recursive Self-Improvement in Personal Agents](http://arxiv.org/abs/2608.04003v1) | Shuhan Xue, Zixin Ding, Yichen Shen et al. | Proposes PAST-Bench to measure whether personal agents can convert retained preferences, histories, and skills into demonstrably better future behavior across sessions. It isolates the core challenge of recursive self-improvement in deployed settings. |
| [ContinualSkillBench: Can LLM Agents Truly Evolve Their Capabilities?](http://arxiv.org/abs/2608.03874v1) | Tianyi Guan, Yiding Wang, Haotong Yang et al. | Evaluates whether LLM agents equipped with external skill libraries actually accumulate and reuse skills over time, rather than relying on static libraries. Exposes a gap between agent framework promises and empirical skill evolution. |

### 🔧 Methods & Frameworks (new techniques, benchmarks, efficiency improvements)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Interpretable Adaptive Sampling for LLM Test-Time Scaling](http://arxiv.org/abs/2608.03961v1) | Mobina Kashaniyan, Ali Jannesari | Replaces fixed per-query compute budgets with an interpretable adaptive sampler that allocates more reasoning steps to hard prompts and fewer to easy ones. The method is transparent about per-query resource decisions, unlike opaque fixed-budget schemes. |
| [Muon Meets Mamba: Spectral Optimization for State Space Models](http://arxiv.org/abs/2608.03941v1) | Arslan Battalov, Karim Kramin, Alexander Markotenko et al. | Adapts the Muon optimizer—originally designed for Transformers—to state-space models, showing that spectral-norm steepest descent generalizes beyond attention architectures. Provides the first systematic evidence for Muon's effectiveness outside the Transformer family. |
| [Latent Reward Registers for Diffusion Preference Alignment](http://arxiv.org/abs/2608.03929v1) | Yuanshen Guan, Zipeng Feng, Zhiwei Xiong et al. | Proposes latent reward registers that estimate terminal rewards at each denoising step, addressing the severe temporal credit-assignment problem in diffusion preference alignment. Enables finer-grained alignment without waiting for full sample generation. |
| [Sparse Weight Decomposition for Efficient Circuit Extraction](http://arxiv.org/abs/2608.03913v1) | Chuanhao Yan, Xuhan Huang, Yawen Duan et al. | Extracts interpretable circuits from dense pretrained transformers via sparse weight decomposition without auxiliary training or fidelity-gap-inducing retraining. The approach exposes mechanistic units at significantly lower computational cost than prior methods. |
| [GENESIS: Towards Explainable Causal Discovery](http://arxiv.org/abs/2608.03868v1) | Abhinav Thorat, Ravi Kumar Kolla, Vishak K Bhat et al. | Combines LLM-assisted semantic reasoning with statistical structure recovery to resolve ambiguities in low-sample causal discovery regimes. Demonstrates that hybrid approaches can recover more plausible causal graphs than purely statistical baselines. |

### 📊 Applications (domain-specific, multimodal, code generation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [CARE-X: Towards Clinically Useful Radiology VLMs with Auxiliary Supervision, Reward-Aligned Learning, and Tool-Augmented Measurement](http://arxiv.org/abs/2608.03890v1) | Mercy Prasanna Ranjit, Anirban Porya, Sathvik Joel et al. | Builds a chest X-ray VLM that classifies findings with tunable thresholds, localizes them spatially, and derives anatomical measurements in a unified pipeline. Moves clinical VLMs beyond fluent report generation toward actionable diagnostic support. |
| [Can Large Language Models Recover Semantic Optimization Opportunities That Compilers Miss?](http://arxiv.org/abs/2608.03983v1) | Hailong Jiang, Feng Yu, Emran Hossain et al. | Tests whether LLMs can recover semantic optimization opportunities absent from C/C++ program representations, producing validated, contract-preserving transformations. Offers evidence that LLMs can complement traditional optimizing compilers on hard cases. |
| [HALLuTruthQA-4K: A Fine-Grained Corpus and Annotation Process for Arabic Hallucination Detection and Truth Verification](http://arxiv.org/abs/2608.03966v1) | Salah Eddine Bekhouche, Abdessalam Bouchekif, Hichem Telli et al. | Introduces a fine-grained Arabic hallucination dataset that annotates at the claim level rather than assigning binary labels to entire responses. Addresses the under-resourced gap in multilingual factual-consistency evaluation. |
| [MultiGlobeQA: A Multilingual and Globally Diverse Benchmark for Geospatial Reasoning](http://arxiv.org/abs/2608.03882v1) | Martin Böckling, Elizaveta Nosova, Heiko Paulheim et al. | Evaluates LLMs on multilingual geospatial reasoning tasks involving distances, containment, and topological relations over real-world entities. Reveals that stored geographic knowledge alone is insufficient without geometric and topological computation skills. |

---

## Research Trend Signal

The most visible theme this round is **inference-time compute optimization**: test-time scaling is no longer a niche topic but a central engineering challenge, with papers proposing adaptive sampling, KV-cache transfer, and parallel compute allocation as first-class primitives. A second rising direction is **agent-level self-improvement**, reflected in benchmarks that directly test whether retained experience translates into measurable capability growth rather than static skill libraries. A third signal is the maturation of **domain-specific VLMs**—particularly in healthcare (radiology, triage) and legal text—where the field is moving past generative fluency toward verifiable, actionable outputs with safety-governed evaluation contracts. Together, these trends suggest the community is transitioning from capability exploration toward production readiness, with evaluation rigor and efficiency becoming equally weighted concerns.

---

## Worth Deep Reading

1. **[Test-Time Scaling in Reasoning LLMs: Inference Regimes, Evaluation, and Reproducibility](http://arxiv.org/abs/2608.04001v1)** — This paper is the most comprehensive taxonomy of test-time scaling to date and directly addresses reproducibility gaps that have slowed the field. It will serve as a foundational reference for anyone working on inference-time compute allocation.

2. **[WorldCup Arena: Prospective, Leakage-Free Evaluation of Frontier LLMs on a Live Tournament](http://arxiv.org/abs/2608.04008v1)** — The prospective, leakage-free design is a major methodological contribution for evaluating forecasting ability without post-hoc contamination. It sets a template that can be adapted to any time-sensitive real-world event.

3. **[CARE-X: Towards Clinically Useful Radiology VLMs](http://arxiv.org/abs/2608.03890v1)** — This work exemplifies the shift from generative fluency to actionable clinical utility, integrating classification, localization, and measurement in one pipeline. It is essential reading for researchers targeting production deployment in regulated domains.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*