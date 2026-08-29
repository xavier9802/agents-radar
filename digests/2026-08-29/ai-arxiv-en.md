# ArXiv AI Research Digest 2026-08-29

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 50 papers | Generated: 2026-08-29 06:43 UTC

---



# ArXiv AI Research Digest — 2026-08-29

## 1. Today's Highlights

Today's submissions reveal a strong convergence around **test-time and inference-time scaling**: methods like CritICL, TTPO, and weak-model guidance in RLVR push reasoning gains without additional training. Concurrently, the **agent ecosystem matures rapidly** with papers on persistent skill evolution (WikiSkill), experience-driven red-teaming (RedEvoAgent), and principled agentic data generation (ACE lens), signaling a shift from ad-hoc agent prototyping to systematic agent engineering. A third notable direction is **efficiency-driven model development**, exemplified by Puro-2B's sub-$6,000 pretraining recipe, SWE-Prime's trajectory quality over quantity thesis, and successive capacity growth in JEPA world models — all challenging the assumption that scale alone drives progress.

---

## 2. Key Papers

### 🧠 Large Language Models (architecture, training, alignment, evaluation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [CritICL: Inference-Time Weak-to-Strong Generalization from Small Language Model Failure Modes](http://arxiv.org/abs/2608.27455v1) | Wu, He, Hu et al. | Introduces an inference-time framework that leverages failure modes of smaller models to guide correction in larger LLMs without repeated generation or external verification. This offers a parameter-efficient alternative to test-time scaling that operates purely at inference. |
| [TTPO: Test-Time Policy Optimization](http://arxiv.org/abs/2608.27448v1) | Wang, Lu, Wang et al. | Replaces ground-truth labels with signal-free verification to enable test-time training, extending RL and OPSD-style improvements to settings where labels are unavailable. This broadens the applicability of post-training gains beyond supervised domains. |
| [Puro-2B: Poor Lab's Qwen2-1.5B Trained on RTX 5090 within $5090](http://arxiv.org/abs/2608.27370v1) | Luo, Cui, Yin et al. | Demonstrates a cost-efficient, hardware-accessible LLM pretraining recipe using consumer-grade GPUs, achieving competitive performance at a fraction of conventional cost. It challenges the narrative that meaningful pretraining requires supercomputing-scale resources. |
| [How Language Models Organize and Structure Moral Knowledge](http://arxiv.org/abs/2608.27402v1) | Reblitz-Richardson | Trains independent linear probes to reveal whether LLMs geometrically distinguish moral foundations and organize relationships among them, moving beyond mere moral detection. The findings clarify the structure of moral reasoning in contemporary models. |
| [Beyond Parallel Blindness: Information Floors and Model Gaps in Block Drafting](http://arxiv.org/abs/2608.27339v1) | Qiang, Fang, Chen et al. | Disentangles two distinct failure modes in block drafters — missing within-block path information versus imperfect modeling of observable information — using an information-theoretic protocol. This enables more precise diagnosis of speculative decoding limitations. |
| [Naive Prompt Optimization: Rethinking the Need for Complex Prompt Search](http://arxiv.org/abs/2608.27266v1) | Chang, Chen | Shows that simple, direct prompt optimization can match the performance gains of complex evolutionary or gradient-based search methods for autonomous agents. It re-evaluates the cost-benefit of elaborate prompt engineering pipelines. |

### 🤖 Agents & Reasoning (planning, tool use, multi-agent, chain-of-thought)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [WikiSkill: Compiling Agent Experience into Persistent Knowledge for Skill Evolution](http://arxiv.org/abs/2608.27454v1) | Tang, Rashtchian, Ferng et al. | Proposes a system for automatically extracting reusable skills from agent interaction experience and persisting them for future reuse, enabling progressive adaptation. This addresses the gap between one-off skill discovery and long-term skill retention. |
| [RedEvoAgent: Automatic Red-Teaming Agent with Experience-Driven Skill Evolution](http://arxiv.org/abs/2608.27439v1) | Zhang, Liu, Chen et al. | Builds an autonomous red-teaming agent that evolves its attack strategies through accumulated experience, moving beyond fixed or scripted jailbreak methods. It provides a more realistic and adaptive security evaluation for production LLM agents. |
| [INTENT-AS-A-TOOL Makes it Easy to Track Agentic Misalignment](http://arxiv.org/abs/2608.27348v1) | Zhang, Dong, Xu et al. | Uses chain-of-thought monitoring to detect when agents take harmful actions under goal conflicts, treating intent tracking as a diagnostic tool for safety failures. It offers a practical framework for auditing agentic misalignment in deployment. |
| [What Makes Good Agentic Data? An ACE Lens on Data Generation for LLM Agents](http://arxiv.org/abs/2608.27260v1) | Zeng, Xu, Zhang et al. | Introduces an Accountability-Consistency-Usefulness (ACE) framework for evaluating whether generated agent interaction data is genuinely beneficial rather than merely abundant. It provides principled criteria for agentic data curation. |
| [SWE-Prime: Fewer Trajectories, Better Performance](http://arxiv.org/abs/2608.27449v1) | Zheng, Ye, Wang et al. | Argues that trajectory quality, not quantity, drives SFT performance for software-issue resolution, showing that curated smaller datasets outperform large-scale but noisy alternatives. It reframes the data strategy for agent-based coding tasks. |
| [Persona-Execution Separation: An Architecture Pattern for Evolving LLM Agents under Execution Audit](http://arxiv.org/abs/2608.27427v1) | Xi | Proposes separating persona (free-evolving instructions and tone) from execution (auditable, stateful work) into distinct trust domains. This enables compliant agent operation in governed organizations without sacrificing adaptability. |

### 🔧 Methods & Frameworks (new techniques, benchmarks, efficiency improvements)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Boosting LLM Exploration via Weak-Model Guidance in RLVR](http://arxiv.org/abs/2608.27420v1) | Shen, Zhang, Li et al. | Uses guidance from weaker models to counteract policy entropy collapse during RLVR, restoring broad reasoning coverage and improving pass@$k$ for large $k$. This improves the robustness of reinforcement learning-based reasoning training. |
| [Consolidating RLVR Capabilities Across Domains: A Deep Dive into Fusion Paradigms](http://arxiv.org/abs/2608.27409v1) | Wu, Yang, Cai et al. | Systematically compares three fusion paradigms (merge, distill, fine-tune) for consolidating RLVR-trained domain experts into unified models. It provides practical guidance on trade-offs between capability retention and model efficiency. |
| [SCIT: Testing Causal Cache Carriers in Latent Chain-of-Thought Models](http://arxiv.org/abs/2608.27265v1) | Ding, Huang, Yang | Introduces the Suffix Cache Interchange Test, a causal protocol that constructs exact counterfactuals to identify and verify cache carriers in latent CoT models. It offers a rigorous method for interpretability in continuous-reasoning architectures. |
| [BTS-AgentBench: A Deterministic, Replayable Pipeline from Read-Only Telemetry Logs to Agent Benchmarks](http://arxiv.org/abs/2608.27334v1) | Kim | Presents a pipeline that compiles industrial telemetry logs into executable multi-turn agent benchmarks with full replay capability. It bridges the gap between real-world operational data and reproducible agent evaluation. |
| [MCR-Bench: From Static to Dynamic — Benchmarking Real-World Code Review](http://arxiv.org/abs/2608.27442v1) | Zheng, Wang, Wang et al. | Introduces a benchmark that captures the iterative, interactive nature of real-world code review, moving beyond static single-turn evaluation. It provides a more realistic testbed for LLM-based code review systems. |
| [Evaluate Smarter, Evolve Further: Efficient Harness Evolution through Behavior-Aware Verification](http://arxiv.org/abs/2608.27311v1) | Xu, Zhang, Chen et al. | Proposes behavior-aware verification that avoids wasting rollouts on unrelated agent harness behaviors during adaptation. It makes harness evolution more sample-efficient for production agent systems. |

### 📊 Applications (domain-specific, multimodal, code generation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [CLAP: Cross-Embodiment Video World Models are Zero-Shot Physical Simulators](http://arxiv.org/abs/2608.27406v1) | Liu, Shorinwa | Trains cross-embodiment video world models on heterogeneous robot data to generalize physics understanding across different robotic platforms. This enables zero-shot physical simulation without embodiment-specific retraining. |
| [LeVJEPA: Efficient & Scalable Video Pretraining without the Heuristics](http://arxiv.org/abs/2608.27395v1) | Kuhn, Maes, Serra et al. | Removes architectural asymmetries and EMA target encoders from JEPA-style video pretraining while preventing representation collapse through a simpler, more scalable design. It makes video world-model pretraining more efficient and accessible. |
| [PAWBench: How Far Are We from Probabilistically Aligned World Modeling?](http://arxiv.org/abs/2608.27345v1) | Pu, Zhuo, Paul et al. | Evaluates whether video generation models can capture the full distribution of physically valid trajectories, not just single plausible outcomes. It establishes a benchmark for probabilistic alignment in world models. |
| [CorporateBench: Large-Scale Q&A Benchmarking with Temporal Knowledge Bases](http://arxiv.org/abs/2608.27391v1) | Hamilton, Sun, Romero et al. | Provides a human-validated, enterprise-scale Q&A benchmark using temporal knowledge bases, addressing the scarcity of realistic corporate evaluation data. It enables more rigorous testing of LLMs on real-world document retrieval. |
| [Mechanistic Reaction Prediction via Discrete Flow Matching on Graph-Structured Electron Occupation](http://arxiv.org/abs/2608.27429v1) | Xuan-Vu, Susanu, Armstrong et al. | Models chemical reactions as transformations in electron space using discrete flow matching on molecular graphs, offering a physically grounded alternative to heuristic graph-edit approaches. It advances AI-driven mechanistic chemistry prediction. |
| [BrailleBench: Investigating Multi-Criteria Braille Comprehension in Large Language Models](http://arxiv.org/abs/2608.27268v1) | Zhang, Mo, Chen et al. | Evaluates LLM capabilities across multiple braille comprehension criteria to assess inclusivity for blind and deafblind users. It highlights gaps in accessibility and pushes for more equitable AI evaluation. |
| [QuantumBoostNet: A Hybrid Classical-Quantum Architecture for Enhanced Accuracy in Cardiac Ultrasound View Identification](http://arxiv.org/abs/2608.27302v1) | Udrescu-Milosav, Jura, Udrescu et al. | Combines classical and quantum computing in a hybrid architecture to improve accuracy in identifying cardiac ultrasound views, a critical step for clinical imaging. It demonstrates practical quantum-classical synergy in medical diagnostics. |
| [Your Voice Cloning System is Secretly a Voice Anonymizer](http://arxiv.org/abs/2608.27360v1) | Muletta, Saaro, Cieliebak et al. | Repurposes the multilingual XTTSv2 voice cloning model for speaker anonymization without retraining, by exploiting its inherent ability to separate identity from linguistic content. It provides a zero-cost privacy-preserving alternative for voice systems. |
| [LLMs Can Design Near-Optimal OR Algorithms](http://arxiv.org/abs/2608.27296v1) | Baek | Shows that LLMs can generate near-optimal control policies for operations research problems including inventory control, queueing networks, and assortment optimization. It extends the scope of LLM algorithmic competence beyond code generation into OR. |

---

## 3. Research Trend Signal

Today's submissions signal a clear pivot from **training-time scaling to inference-time and test-time optimization**. CritICL, TTPO, and weak-model guidance in RLVR all demonstrate that performance gains can be extracted at deploy time without additional fine-tuning, reflecting growing interest in cost-efficient reasoning improvement. The agent research landscape is similarly maturing: papers on WikiSkill, RedEvoAgent, the ACE data framework, and harness evolution point to a community moving beyond single-turn agent demos toward **persistent, auditable, and self-improving agent systems**. There is also a notable emphasis on **evaluation rigor** — MCR-Bench's dynamic code review, PAWBench's probabilistic alignment tests, BTS-AgentBench's telemetry-derived benchmarks, and the statistical audit of LLM-judge methodologies all challenge the field to build more realistic and reproducible evaluation pipelines. Finally, the Puro-2B result and successive capacity growth in JEPA architectures reinforce a democratization trend: high-quality models and world models are becoming achievable on consumer hardware, which will likely accelerate open-source experimentation across sub-fields.

---

## 4. Worth Deep Reading

1. **[CritICL: Inference-Time Weak-to-Strong Generalization](http://arxiv.org/abs/2608.27455v1)** — This paper directly addresses the most pressing cost bottleneck in LLM reasoning: test-time compute. By extracting signal from small-model failures without repeated generation, it could become a foundational technique for inference-time scaling. Its implications extend to any deployment scenario where compute budget is constrained.

2. **[WikiSkill: Compiling Agent Experience into Persistent Knowledge](http://arxiv.org/abs/2608.27454v1)** — Persistent skill retention is the missing link between agents that perform well in isolated sessions and agents that genuinely improve over time. This paper's framework for extracting, compiling, and reusing skills from interaction experience is central to the next generation of self-improving agents.

3. **[TTPO: Test-Time Policy Optimization](http://arxiv.org/abs/2608.27448v1)** — Removing the ground-truth label requirement from post-training methods opens RLVR-style gains to unsupervised and weakly-supervised domains. Understanding how signal-free verification works in practice will be critical for applying reasoning improvements beyond mathematics and code.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*