# ArXiv AI Research Digest 2026-08-14

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 50 papers | Generated: 2026-08-14 02:26 UTC

---



# ArXiv AI Research Digest — 2026-08-14

---

## 1. Today's Highlights

A cluster of papers challenges core assumptions about scaling and robustness in modern AI systems. Research on long-context training reveals an *information abundance paradox* where extended context windows can actually degrade parametric knowledge, while another study documents *simulator collapse* in multi-agent RL, where frozen LLM simulators fail to generalize. On the efficiency front, a test-time capability-transfer method bypasses costly parameter updates entirely, and a new analysis of hybrid linear attention uncovers structured "massive activation" patterns with direct implications for model interpretability. Meanwhile, Agent and RAG infrastructure continues to mature with benchmarks for multi-hop API-tool reasoning, query-aware caching, and governed enterprise document generation.

---

## 2. Key Papers

### 🧠 Large Language Models (architecture, training, alignment, evaluation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [AI4AI at Test-Time: Strong-to-Weak Capability Transfer via Harnesses](http://arxiv.org/abs/2608.12307v1) | Cheng Qian, Wenting Zhao, Liangwei Yang et al. | Proposes transferring capabilities from large to small models entirely at test time using harnesses, avoiding expensive parameter updates or teacher-forced distillation. Demonstrates that capability transfer can be achieved without modifying the student model's weights. |
| [Information Abundance Paradox: Long-Context Training Undermines Parametric Knowledge](http://arxiv.org/abs/2608.12218v1) | Arda Uzunoglu, Benjamin van Durme, Daniel Khashabi et al. | Challenges the assumption that longer-context training is always beneficial, showing that extended contexts can degrade the model's internal parametric knowledge. Raises important questions about the trade-offs between retrieval and memorization in LLM design. |
| [Who Thinks Best Depends on How Long You Let Them: Budget-Dependent Rankings in LLM Evaluation](http://arxiv.org/abs/2608.12150v1) | Rodrigo Guedes de Souza, Alison R. Panisson | Shows that standard LLM rankings are unstable across inference token budgets (64–4,096), undermining the assumption of stable model comparisons. Calls for budget-aware evaluation protocols in LLM benchmarking. |
| [Massive Activations in Hybrid Linear Attention Large Language Models: Pre-Attention Spikes and Inter-Spike Plateaus](http://arxiv.org/abs/2608.12149v1) | Zunhai Su, Bohan Sun, Xialie Zhuang et al. | Presents the first systematic study of massive activation patterns in layer-interleaved hybrid linear attention LLMs, identifying pre-attention spikes and persistent inter-spike plateaus. These architecture-aligned activation morphologies offer new interpretability insights for efficient LLM designs. |
| [Do LLMs Take Care of Their Own? Similarity Signals Can Induce Cooperation](http://arxiv.org/abs/2608.12125v1) | Akash Kundu, Emanuel Tewolde, Ratip Emin Berker et al. | Investigates whether LLM-based agents can resolve cooperation dilemmas like the Prisoner's Dilemma when exposed to similarity signals. Finds that identity and likeness cues can steer multi-agent LLM interactions toward mutually beneficial outcomes. |

### 🤖 Agents & Reasoning (planning, tool use, multi-agent, chain-of-thought)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [DreamFly: Causal Memory and Receding-Horizon Diffusion Planning for Aerial Vision-Language Navigation](http://arxiv.org/abs/2608.12308v1) | Yan Deng, Fei Xu | Adapts vision-language-action models to aerial VLN under partial observability by combining causal memory with receding-horizon diffusion planning. Enables embodied agents to integrate visual evidence over time and decide when navigation goals are reached. |
| [VAKRA: Evaluating Multi-Hop Reasoning Across APIs and Retrieval Under Tool-Use Policies](http://arxiv.org/abs/2608.12282v1) | Ankita Rajaram Naik, Anupama Murthi, Benjamin Elder et al. | Introduces a benchmark of over [multi-hop] queries that jointly evaluate API reasoning and knowledge retrieval, capabilities previously tested in isolation. Targets the gap in evaluating enterprise agents that must navigate both structured APIs and document collections. |
| [SCOUT: Unlocking Enhanced Spatial Reasoning via Structured Chain-of-Thought and Multi-Objective Process Reward](http://arxiv.org/abs/2608.12220v1) | Zile Zhou, Huining Yuan, Weichen Zhang et al. | Addresses the spatial reasoning bottleneck in VLMs by combining structured chain-of-thought with a multi-objective process reward that improves credit assignment across intermediate steps. Outperforms prior RL-based approaches that suffer from poor step-level credit assignment. |
| [GUIDE: Governed Unified Intelligence for Document-to-Artifact Generation in Enterprise Settings](http://arxiv.org/abs/2608.12133v1) | Shivali Dalmia, Sumukha Thoppanahalli, Mohammadreza Sediqin et al. | Tackles hallucination, table degradation, and lack of governed workflows in enterprise multimodal document processing. Extends beyond extraction to include validation and artifact generation under structured guideline constraints. |
| [One Frozen Simulator Is Not Enough: Simulator Collapse in Multi-Agent RL](http://arxiv.org/abs/2608.12253v1) | Simon Yu, Nicholas Tomlin, Marwa Abdulhai et al. | Demonstrates that single frozen LLM simulators systematically fail to generalize in multi-agent RL for human-AI interaction due to mode collapse. Shows that policy learners trained on collapsed simulators inherit these generalization failures. |

### 🔧 Methods & Frameworks (new techniques, benchmarks, efficiency improvements)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Constructing Dynamic Master Logic Models as Knowledge Graphs for Complex System Diagnostics Using Retrieval-Augmented Large Language Models](http://arxiv.org/abs/2608.12304v1) | Saman Marandi, Yu-Shu Hu, Mohammad Modarres et al. | Automates the construction of Dynamic Master Logic knowledge graphs using RAG-enabled LLMs, replacing labor-intensive expert interpretation of technical documentation. Makes hierarchical system-behavior representation scalable for complex engineered systems. |
| [Diagram-MMU: A Multi-Modal Benchmark for Scientific Diagrams](http://arxiv.org/abs/2608.12262v1) | Weihao Bo, Shan Zhang, Yanpeng Sun et al. | Evaluates MLLMs on scientific diagram understanding, motivated by capabilities such as converting diagrams directly into LaTeX TikZ code. Highlights gaps in multimodal models' ability to interpret and regenerate complex scientific visuals. |
| [QV-PIC: Query-Aware Visual Position-Independent Caching for Efficient RAG Serving](http://arxiv.org/abs/2608.12121v1) | Yilin Liu, Rui Meng, Wangze Ni et al. | Reduces redundant KV-cache computation in RAG serving by making position-independent caching query-aware, addressing the bottleneck of large text-token volumes. Improves inference efficiency without sacrificing retrieval quality. |
| [HYDRA: Hyperbolic Dynamic Representation Architecture for Kolmogorov-Arnold Networks](http://arxiv.org/abs/2608.12194v1) | Zhao Su, Yuxin Xia, Haoran Li et al. | Reduces parameter redundancy in Kolmogorov-Arnold Networks by mapping connections to hyperbolic dynamic representations instead of independent univariate functions per edge. Improves scalability while preserving KANs' superior nonlinear approximation. |
| [SAG: SQL-Retrieval Augmented Generation with Query-Time Dynamic Hyperedges](http://arxiv.org/abs/2608.12129v1) | Yuchao Wu, Junqin Li, XingCheng Liang et al. | Extends graph-based RAG by constructing dynamic hyperedges at query time, enabling better handling of structured constraints and multi-hop reasoning over SQL-backed knowledge. Addresses limitations of static dense-retrieval RAG implementations. |

### 📊 Applications (domain-specific, multimodal, code generation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Large Language Model-Driven Small-Capitalization Trading: Integrating Financial News Sentiment, Macroeconomic Indicators, and Technical Signals](http://arxiv.org/abs/2608.12283v1) | Alireza Kargarzadeh, Nariman Khaledian, Navid Parvini et al. | Deploys an uncertainty-aware LLM pipeline that decomposes model-predicted risk into aleatoric and epistemic components for small-cap portfolio construction. Shows that LLM-extracted sentiment signals outperform fixed lexicons in financial signal extraction. |
| [ScreenShot: A Foundation Model for Few-Shot Combination Drug Screening](http://arxiv.org/abs/2608.12219v1) | Antoine de Mathelin, Christopher Tosh, Wesley Tansey et al. | Addresses the prohibitively expensive combinatorial search space in drug-combination screening using a foundation model trained for few-shot prediction. Enables predictive modeling of synergistic drug pairs where experimental screens are infeasible. |
| [Learning-Based Behavior Planning for Automated Driving: Real-World Integration and Deployment](http://arxiv.org/abs/2608.12198v1) | Jean-Pierre Busch, Guido Linden, Jan Bergmann et al. | Reports on real-world deployment of learning-based motion planning for automated vehicles, addressing transparency and trustworthiness concerns that hinder adoption. Bridges the gap between lab-scale deep learning planners and production autonomous driving systems. |
| [Machine Learning-Based Cyber Defense for Cloud Infrastructure: An Adaptive Deep Q-Network Architecture for Intelligent Intrusion Detection and Automated Threat Mitigation](http://arxiv.org/abs/2608.12190v1) | Md Yassir Mottalib, Md Yousuf, Eklachur Rahman Bhuiyan et al. | Proposes a DQN-based dynamic cyber-defense framework for real-time intrusion detection and autonomous threat mitigation in cloud environments. Addresses the need for adaptive security solutions against increasingly complex cloud-targeted cyber assaults. |
| [Attractor Image-Based Deep Learning of Arterial Pulse Waves for Age Classification](http://arxiv.org/abs/2608.12117v1) | Sara Vardanega, Patrick Segers, Philip Aston et al. | Uses deep learning on attractor representations of arterial pulse waves as a surrogate marker for cardiovascular (vascular) age. Demonstrates that pulse-wave morphology encodes age-relevant physiological information useful for disease-risk screening. |
| [Class Activation Mapping in Explainable Computer Vision: A Method-Centered Review of CNN, Transformer, and Foundation-Model-Era Visual Explanations](http://arxiv.org/abs/2608.12299v1) | AmirHossein Eshghi, Hamid Saadatfar, Seyyed Ali Hoseini et al. | Surveys CAM methods across CNNs, transformers, and foundation models, unifying how internal evidence is converted into heatmap-based visual explanations. Provides a method-centered taxonomy relevant to the interpretability needs of increasingly complex vision architectures. |

---

## 3. Research Trend Signal

Today's submissions reveal three converging themes. First, **robustness critiques of scaling assumptions** are gaining traction: long-context training may undermine parametric knowledge (#29), frozen simulators collapse in multi-agent settings (#18), and LLM rankings depend critically on inference budget (#38). These findings collectively push the field toward more nuanced scaling strategies rather than naive "bigger is better" paradigms. Second, **efficiency at inference time** is a major focus — test-time capability transfer without retraining (#3), query-aware caching for RAG serving (#49), mixed-precision quantization for compression (#22), and hardware-aware tree deployment (#42) all point to a maturing understanding that deployment constraints drive methodological innovation. Third, **agent evaluation and governance** is expanding beyond benchmarks into real-world constraints: multi-hop API-tool reasoning benchmarks (#10), governed enterprise document workflows (#45), and adversarial resilience in skill-based agents (#13) reflect growing maturity in how agents are tested, secured, and deployed in production settings.

---

## 4. Worth Deep Reading

**[Information Abundance Paradox: Long-Context Training Undermines Parametric Knowledge](http://arxiv.org/abs/2608.12218v1)** — This paper directly challenges one of the most widely held assumptions in the field: that longer context windows are unambiguously beneficial. If extended context degrades internal knowledge, it forces a re-evaluation of training strategies for retrieval-augmented systems and has immediate implications for any application that relies on large context windows. Essential reading for anyone building or training LLMs.

**[AI4AI at Test-Time: Strong-to-Weak Capability Transfer via Harnesses](http://arxiv.org/abs/2608.12307v1)** — The proposal to transfer capabilities at test time without any parameter updates is a notable departure from the dominant distillation paradigm. If validated, it could dramatically reduce the compute and data costs of deploying smaller models, making capability transfer accessible to resource-constrained settings. The conceptual simplicity makes it a paper worth understanding deeply.

**[One Frozen Simulator Is Not Enough: Simulator Collapse in Multi-Agent RL](http://arxiv.org/abs/2608.12253v1)** — This work identifies a concrete failure mode — mode collapse in frozen LLM simulators — that affects a growing number of multi-agent and human-AI interaction pipelines. Understanding simulator collapse is critical for anyone using LLMs as environment simulators, and the findings likely generalize beyond the specific experimental setup described.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*