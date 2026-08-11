# ArXiv AI Research Digest 2026-08-11

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 30 papers | Generated: 2026-08-11 02:09 UTC

---



# ArXiv AI Research Digest — 2026-08-11

## 1. Today's Highlights

Today's submissions reveal a maturing field pivoting from raw capability expansion toward reliability, efficiency, and deployability. The most notable threads are (1) **LLM reliability and safety** — papers on test-time reasoning aggregation, self-evolving guardrails, and frozen-representation guardrails signal a industry-wide shift toward production-hardened models; (2) **Agent infrastructure** — multiple works on skill reusability, resource-inefficient MCP patterns, and hierarchical self-improvement point to agents becoming a first-class engineering concern rather than a research novelty; (3) **Efficiency at scale** — KV-cache compression for audio, low-rank LLM compression, and spiking-neural-network simulators all target the same bottleneck: running capable models within real-world compute budgets.

## 2. Key Papers

### 🧠 Large Language Models

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Reproducing and Stress-Testing Two Approaches to LLM Reasoning Reliability: Test-Time Probability Aggregation and Logic-Representation Editing](http://arxiv.org/abs/2608.08514v1) | Minhan Cho, Jimin Kweon | Independently reproduces two methods — RPC (token-probability aggregation) and LCF (logic-representation editing) — across four new task domains and multiple 7–8B models. The reproduction provides evidence on which reliability techniques generalise versus collapse under distribution shift. |
| [HoloAegis: Frozen Representation, Topological Inference: Minimally Parametric Safety Manifolds for Zero-Shot LLM Guardrails](http://arxiv.org/abs/2608.08485v1) | Tak Ho Alex Li, Kaijie Liu, Lik-Hang Lee et al. | Proposes achieving safety through geometric reasoning over frozen pre-trained representations, avoiding the fine-tuning distortion and inference cost of current guardrail approaches. Aims for zero-shot safety without retraining. |
| [Yesterday's Shield, Today's Spear: A Self-Evolving Safety Guardrail in Production](http://arxiv.org/abs/2608.08471v1) | Cong Ming, Jingyi Chen, Bin Liu et al. | Introduces SESG, a multi-agent system where safety guardrails evolve alongside emerging jailbreaks, addressing the static-guardrail bottleneck where defenses are perpetually one step behind new attack techniques. |
| [Understanding Calibration and Truncation Error Propagation in Training-Free Low-Rank Compression for LLMs](http://arxiv.org/abs/2608.08506v1) | Mohanad Odema, Gabrielle De Micheli, Dayin Gou et al. | Analyzes how residual calibration errors propagate under training-free low-rank compression, revealing a key limitation shared by existing SOTA frameworks: error accumulation in calibration data activations. |
| [Time Present and Time Past: Benchmarking Large Language Models on Temporally Evolving Document Understanding](http://arxiv.org/abs/2608.08512v1) | Mahbub E Sobhani, Md. Faiyaz Abdullah Sayeedi, Fahmid Hasan Chowdhury et al. | Benchmarks LLMs on documents where correct answers change over time (laws, tax codes, software docs), introducing a temporal-dimension to evaluation that current benchmarks lack. |

### 🤖 Agents & Reasoning

| Paper | Paper | Authors | Summary |
| :--- | :--- | :--- | :--- |
| [FailForge: Distilling Procedural Competence from Persistent Failures into Code Agents](http://arxiv.org/abs/2608.08570v1) | Dongyi Lv, Fushun E, Aichen Cai et al. | Challenges rejection-sampling fine-tuning by showing even strong code agents repeatedly fail on a substantial fraction of tasks. Proposes learning from persistent failures rather than only from successes. |
| [What Keeps Agent Skills from Being Reusable? Evidence from 138K SKILL.md Files](http://arxiv.org/abs/2608.08453v1) | Chi Zhang, Yimin Liu, Xinze Chen et al. | Large-scale empirical study finding that most public agent skills originate from a single task, repository, or conversation, explaining the scarcity of truly reusable agent skills in the wild. |
| [LLM within MCP Matters: Measuring Inefficient Resource Utilization Driven by LLMs](http://arxiv.org/abs/2608.08467v1) | Minhan Cho, Soyoung Park, Kihyeon Jeong et al. | Measures how the Model Context Protocol (MCP) is used inefficiently in practice, showing that embedding reference data directly in server instructions leads to prompt bloat and wasted context window. |
| [Hierarchical Self-Improvement: A Framework for Task-Specific Evolvable Agent Harnesses](http://arxiv.org/abs/2608.08466v1) | Tailin Zhou | Proposes treating the agent harness as task-specific and evolvable rather than a fixed post-deployment artifact, enabling the executable scaffold to improve alongside the model. |
| [Discovering Diverse Planning Policies for Multimodal Embodied Agents with Quality-Diversity Optimization](http://arxiv.org/abs/2608.08523v1) | Pengfei Xu, Yong Liu, Xiaoya Nan et al. | Introduces quality-diversity optimization for discovering diverse planning policies in multimodal embodied agents, addressing the limitation of single-dominant-planning-style approaches. |
| [SkillsMetric: Mapping the Detection Boundary of Static Analysis for Malicious Agent Skills](http://arxiv.org/abs/2608.08468v1) | Xinze Chen, Chi Zhang, Ping Ji et al. | Presents a five-stage static analysis framework that scores skill packages along pattern density, stealth, and other security dimensions, bringing systematic security evaluation to the proliferating agent-skill ecosystem. |

### 🔧 Methods & Frameworks

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [VoxZip: Semantic-Anchored Temporal KV Cache Compression for Long-Context Audio Inference](http://arxiv.org/abs/2608.08569v1) | Wenxu Jia, Dongjie Fu, Xize Cheng et al. | Adapts text-centric KV-cache compression to speech LLMs with semantic anchoring, directly addressing the prohibitive memory demands that bottleneck long-context audio inference. |
| [SuperNeuroMAT: An Efficient Matrix-based Simulator for Spiking Neural Networks](http://arxiv.org/abs/2608.08479v1) | Prasanna Date, Kevin Zhu, Shruti Kulkarni et al. | Opensources a scalable, high-performance simulator for spiking neural networks, targeting the energy-efficiency pathway that traditional ANNs cannot reach. |
| [TRACE-Memory: Public-Conditioned Retrieval and Utility-Aware Evidence Admission for Personalized Generation](http://arxiv.org/abs/2608.08446v1) | Jing Wang, Zhu Wang, Yifan Guo et al. | Argues that personal memory should be injected only when it adds utility beyond public information, reducing noise in personalized generation systems. |
| [Aero Realtime: Fully Aligned Input-Output Streams for Low-Latency Streaming Multimodal Generation](http://arxiv.org/abs/2608.08469v1) | Kaichen Zhang, Wei Huang, Keming Wu et al. | Proposes a duplex streaming architecture where new observations can enter an active generation stream, eliminating the prefill-then-decode bottleneck of current real-time models. |
| [FSTC-Encoder: Feature--Spatial--Temporal Correlation Learning for Generalizable RF Sensing](http://arxiv.org/abs/2608.08439v1) | Jing Wang, Zhu Wang, Changlong Cheng et al. | Unifies heterogeneous RF representation learning through feature, spatial, and temporal correlation encoding, enabling cross-device and cross-modality generalization. |
| [Halpern Iteration Achieves $\tilde{\mathcal{O}}(\varepsilon^{-1/p})$ $p$th-Order Oracle Complexity for Monotone Variational Inequalities](http://arxiv.org/abs/2608.08463v1) | Lesi Chen, Xinliang Zhang, Hengyu Wang et al. | Establishes optimal oracle complexity bounds for higher-order methods on smooth monotone variational inequalities, extending classical results beyond second order. |

### 📊 Applications

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [SDDBMs: Soft Denoising Diffusion Bridge Models](http://arxiv.org/abs/2608.08594v1) | Shiyi Qi, Kun He, Mingmou Liu et al. | Introduces soft endpoint conditioning via Doob's $h$-transform, enabling diffusion bridge models to generate flexible image-to-image translations without hard conditioning constraints. |
| [CDGC-Net: 3D Medical Image Segmentation with Cooperative Dual-Scale Self-Attention and Grouped Channel Modeling](http://arxiv.org/abs/2608.08575v1) | Zheyang Jing, Qin Lu, Jianwang Li et al. | Jointly models global and local features at unified scales with grouped channel recalibration, resolving the semantic mismatch caused by independent multi-scale processing in existing segmentation methods. |
| [On-Device Multi-Species Malaria Detection with Uncertainty-Calibrated Slide-Level Aggregation](http://arxiv.org/abs/2608.08566v1) | Idaya Seidu, Ahmed Tahiru Issah, Charles B. Delahunt et al. | Deploys a calibration-aware malaria detection system on resource-constrained devices, addressing the critical gap between algorithmic accuracy and real-world clinical reliability. |
| [Deep probabilistic logic programming for diagnostic reasoning from incomplete information: A case study in stroke detection](http://arxiv.org/abs/2608.08561v1) | Felix Weitkämper, Monchito Avila, Elizabeth Nanjala et al. | Applies deep probabilistic logic programming to stroke diagnosis under data incompleteness, combining learnable representations with interpretable probabilistic inference. |
| [Beyond Tables: Doc2DB-Bench for Relationally Faithful Document-to-Database Construction](http://arxiv.org/abs/2608.08459v1) | Zhuowen Liang, Zhengxuan Zhang, Jiayang Wang et al. | Benchmarks LLMs on converting long, heterogeneous documents into queryable relational databases, evaluating relationally faithful schema construction across finance, healthcare, and enterprise domains. |
| [Calling the Bluff: Detecting Ever-Shifting Harmful Chat Dialogue via Ordered Reasoning Chain Regularization](http://arxiv.org/abs/2608.08451v1) | Haojie Yu, Ziyou Jiang, Junjie Wang et al. | Detects evolving harmful dialogues by regularizing on ordered reasoning chains — invariant patterns of topic progression and harm indicators that persist across lexical evasion. |
| [Hidden Language Consistency Phenomena in Reasoning LLMs](http://arxiv.org/abs/2608.08447v1) | Muhammad Ali Shafique, Kelly Marchisio | Reveals multilingual reasoning behaviors that vanish under standard evaluation, showing that models can preserve intended language during reasoning even when they produce incorrect answers. |
| [Private Etymology: Designing Relational Reuse of Shared Symbols in Long-Term Human-AI Interaction](http://arxiv.org/abs/2608.08443v1) | Miki Ueno | Studies how humans and conversational AI co-evolve partner-specific symbols and idioms over long interactions, informing the design of relational memory in persistent AI companions. |
| [Human-Guided Causal Knowledge Injection for Virtual Cells](http://arxiv.org/abs/2608.08430v1) | Pengcheng Wang, Changjian Chen, Zhuo Tang et al. | Injects human-curated causal graphs into virtual-cell ML models to improve interpretability of cellular behavior predictions, bridging computational biology and causal reasoning. |

## 3. Research Trend Signal

Today's submissions paint a clear picture of the field entering a **reliability-and-deployability phase**. Safety research has split into two complementary directions: *reactive* (SESG's self-evolving guardrails that track emerging jailbreaks) and *proactive* (HoloAegis's frozen-representation approach that avoids fine-tuning entirely). Agent research has matured from "can we build agents?" to "are our agents efficient, secure, and reusable?" — the SkillsMetric, MCP, and FailForge papers all diagnose specific failure modes in real agent deployments. Efficiency work is similarly converging on the same bottleneck: memory. VoxZip (audio KV cache), low-rank compression error analysis, and Aero Realtime (duplex streaming) all target the gap between model capability and practical inference cost. A secondary signal is the growing emphasis on **temporal and relational reasoning** — temporally evolving document benchmarks, private etymology in human-AI interaction, and relational-faithful database construction all treat time and relationship structure as first-class concerns rather than afterthoughts.

## 4. Worth Deep Reading

1. **[Reproducing and Stress-Testing Two Approaches to LLM Reasoning Reliability](http://arxiv.org/abs/2608.08514v1)** — Independent reproduction across new domains and models is rare and valuable. This paper will become a reference point for anyone evaluating test-time reliability methods, and its stress-test methodology is itself reusable.

2. **[FailForge: Distilling Procedural Competence from Persistent Failures](http://arxiv.org/abs/2608.08570v1)** — The rejection-sampling paradigm dominates code-agent training, yet this paper makes the case that the failures themselves contain more signal than the successes for a substantial fraction of tasks. A provocative shift in perspective for the agent-training community.

3. **[HoloAegis: Frozen Representation, Topological Inference](http://arxiv.org/abs/2608.08485v1)** — If the frozen-representation approach to safety generalizes, it could eliminate the continuous fine-tuning arms race that currently defines LLM guardrails. Worth understanding both the promise and the limitations before investing in this direction.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*