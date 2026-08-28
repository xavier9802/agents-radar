# ArXiv AI Research Digest 2026-08-28

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 50 papers | Generated: 2026-08-28 10:57 UTC

---



# ArXiv AI Research Digest — 2026-08-28

## 1. Today's Highlights

Inference-time reasoning continues to mature, with CritICL demonstrating that LLM failures on smaller models can be systematically leveraged for weak-to-strong generalization without additional verifiers, while TTPO introduces the first test-time policy optimization that replaces ground-truth labels with verifiable rewards. A parallel theme across today's submissions is *efficiency-driven scaling*: Puro-2B shows high-quality pretraining is feasible for under $5,000 on consumer hardware, and Successive Capacity Growth dynamically adjusts encoder width and depth in JEPA world models rather than over-provisioning statically. Agent safety and evaluation also see notable progress, with RedEvoAgent evolving its red-teaming skills autonomously, and the LLM-Judge audit paper revealing that standard difference-in-differences designs on censored rating scales can manufacture apparent effects.

---

## 2. Key Papers

### 🧠 Large Language Models (architecture, training, alignment, evaluation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [CritICL: Inference-Time Weak-to-Strong Generalization from Small Language Model Failure Modes](http://arxiv.org/abs/2608.27455v1) | Wu, He, Hu et al. | Proposes an inference-time framework that uses failure modes from small LLMs to steer larger model reasoning without repeated generation or external verifiers. This could make inference-time scaling cheaper and more accessible for deployment. |
| [TTPO: Test-Time Policy Optimization](http://arxiv.org/abs/2608.27448v1) | Wang, Lu, Wang et al. | Replaces the need for ground-truth labels in test-time training by using verifiable rewards, enabling on-policy self-distillation at inference time. It extends RLVR-style improvements beyond fixed training regimes into dynamic, per-sample adaptation. |
| [Puro-2B: Poor Lab's Qwen2-1.5B Trained on RTX 5090 within $5090](http://arxiv.org/abs/2608.27370v1) | Luo, Cui, Yin et al. | Demonstrates that a strong 2B-parameter LLM can be pretrained on a single RTX 5090 for approximately $5,090, challenging the assumption that quality pretraining requires massive budgets. Makes open-weight model development viable for academic and small-team settings. |
| [Understanding Evolution Strategies for LLM Reasoning: Broader Reasoning Coverage than GRPO](http://arxiv.org/abs/2608.27351v1) | Ba, Zheng, Xie et al. | Provides a first comparative analysis of Evolution Strategies versus GRPO for LLM reasoning post-training, showing ES achieves broader exploration across reasoning paths. The work establishes when and why ES may outperform policy gradient methods in practice. |
| [Not All Eval-Awareness Is Equal: Capabilities Framing Predicts Compliance](http://arxiv.org/abs/2608.27340v1) | Zhuang, Aranguri | Shows that verbalized eval-awareness in chain-of-thought can be identified and that capabilities framing—not just raw eval-awareness level—predicts model compliance. This refines how safety pipelines should treat and intervene on evaluation awareness. |
| [Difference-in-Differences on a Censored Rating Scale Can Manufacture an Effect: Evidence from a Pre-Registered LLM-Judge Audit](http://arxiv.org/abs/2608.27309v1) | Fan, Deng, Xu et al. | Demonstrates through pre-registered audits that difference-in-differences on bounded LLM-judge rating scales can produce spurious effects, threatening the validity of many LLM-evaluation comparisons. Urges stricter causal identification when using LLM judges for comparative evaluation. |
| [Naive Prompt Optimization: Rethinking the Need for Complex Prompt Search](http://arxiv.org/abs/2608.27266v1) | Chang, Chen | Argues that simple prompt optimization methods can match or exceed complex search-based approaches for autonomous agent improvement, delivering performance gains comparable to fine-tuning at a fraction of the cost. Challenges the assumption that sophisticated search is necessary for effective prompt engineering. |

### 🤖 Agents & Reasoning (planning, tool use, multi-agent, chain-of-thought)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [WikiSkill: Compiling Agent Experience into Persistent Knowledge for Skill Evolution](http://arxiv.org/abs/2608.27454v1) | Tang, Rashtchian, Ferng et al. | Introduces a framework for persisting and reusing agent experience as evolving skills, enabling agents to build on prior successes rather than relearning from scratch. Addresses the gap between one-off experience and long-term capability accumulation in autonomous agents. |
| [RedEvoAgent: Automatic Red-Teaming Agent with Experience-Driven Skill Evolution](http://arxiv.org/abs/2608.27439v1) | Zhang, Liu, Chen et al. | Designs a red-teaming agent that autonomously evolves its attack strategies based on past jailbreak success and failure, rather than relying on fixed prompts. Critical for security evaluation as LLM agents gain access to tools with persistent state changes. |
| [INTENT-AS-A-TOOL Makes it Easy to Track Agentic Misalignment](http://arxiv.org/abs/2608.27348v1) | Zhang, Dong, Xu et al. | Proposes a chain-of-thought monitoring framework to detect when agents take harmful actions under goal conflicts, using intent tracking as a tool. Helps close the safety gap between what agents are asked to do and what they actually execute. |
| [What Makes Good Agentic Data? An ACE Lens on Data Generation for LLM Agents](http://arxiv.org/abs/2608.27260v1) | Zeng, Xu, Zhang et al. | Introduces an ACE (Agent-Context-Experience) lens for evaluating whether generated agentic interaction data is useful, not just abundant. Provides a framework for constructing datasets that maintain environmental, task, and success-signal consistency. |
| [Persona-Execution Separation: An Architecture Pattern for Evolving LLM Agents under Execution Audit](http://arxiv.org/abs/2608.27427v1) | Xi | Separates the persona (instructions, tone, self-presentation) from execution (auditable, stateful work) into different trust domains, allowing persona evolution without compromising traceability. Enables governed organizations to deploy evolving agents with auditable behavior. |
| [SCIT: Testing Causal Cache Carriers in Latent Chain-of-Thought Models](http://arxiv.org/abs/2608.27265v1) | Ding, Huang, Yang | Introduces the Suffix Cache Interchange Test, a causal protocol for identifying and manipulating intermediate reasoning states in latent chain-of-thought models. Opens a path to auditing and editing the hidden reasoning traces of compact LLM architectures. |

### 🔧 Methods & Frameworks (new techniques, benchmarks, efficiency improvements)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Consolidating RLVR Capabilities Across Domains: A Deep Dive into Fusion Paradigms](http://arxiv.org/abs/2608.27409v1) | Wu, Yang, Cai et al. | Systematically compares three fusion paradigms—merging, distillation, and routing—for consolidating RLVR-trained domain experts into a single model. Provides the first comprehensive analysis of how to combine multi-domain reasoning capabilities efficiently. |
| [Boosting LLM Exploration via Weak-Model Guidance in RLVR](http://arxiv.org/abs/2608.27420v1) | Shen, Zhang, Li et al. | Uses a weaker model to guide exploration during RLVR training, mitigating the policy entropy collapse that narrows reasoning coverage and hurts pass@k. A practical technique to improve diversity without sacrificing convergence speed. |
| [Successive Capacity Growth: Task-Complexity-Driven Width and Depth Expansion for Vision Transformer Encoders in JEPA World Models](http://arxiv.org/abs/2608.27367v1) | Berenz | Proposes dynamically scaling Vision Transformer encoder capacity based on task complexity, reducing redundancy across attention heads in JEPA world models. Removes the need for over-provisioned fixed-size encoders and improves training efficiency. |
| [SWE-Prime: Fewer Trajectories, Better Performance](http://arxiv.org/abs/2608.27449v1) | Zheng, Ye, Wang et al. | Shows that selecting high-quality software-engineering trajectories for SFT, rather than simply collecting more, leads to better LLM performance on real-world issues. Challenges the scale-over-quality assumption in agent trajectory dataset construction. |
| [BTS-AgentBench: A Deterministic, Replayable Pipeline from Read-Only Telemetry Logs to Agent Benchmarks](http://arxiv.org/abs/2608.27334v1) | Kim | Converts industrial read-only telemetry into reproducible multi-turn agent benchmarks, closing the gap between real operational data and eval-ready datasets. Enables benchmarking agents on authentic infrastructure logs without access to live systems. |
| [A Finite Sample Analysis for Quantile Temporal Difference Learning in Distributional Reinforcement Learning](http://arxiv.org/abs/2608.27313v1) | Cheng, Li, Peng et al. | Provides the first global finite-sample guarantee for synchronous quantile TD learning in tabular distributional RL, separating two key stability mechanisms in the proof. Strengthens the theoretical foundation for distributional RL algorithms in practical settings. |

### 📊 Applications (domain-specific, multimodal, code generation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [From Static to Dynamic: Benchmarking Real-World Code Review with MCR-Bench](http://arxiv.org/abs/2608.27442v1) | Zheng, Wang, Wang et al. | Introduces MCR-Bench, a benchmark that models the iterative, multi-turn nature of real-world code review rather than treating it as a static single-pass task. Fills a gap in evaluating LLMs for production software engineering workflows. |
| [CLAP: Cross-Embodiment Video World Models are Zero-Shot Physical Simulators](http://arxiv.org/abs/2608.27406v1) | Liu, Shorinwa | Trains a cross-embodiment video world model that generalizes across different robot bodies, leveraging heterogeneous video data for physics learning. Enables zero-shot physical simulation without embodiment-specific retraining. |
| [LeVJEPA: Efficient & Scalable Video Pretraining without the Heuristics](http://arxiv.org/abs/2608.27395v1) | Kuhn, Maes, Serra et al. | Proposes a self-supervised video pretraining method that avoids the architectural asymmetries and EMA target encoders common in JEPA-style models. Makes video representation learning more efficient and scalable. |
| [RATIO: A Benchmark for Retrieval Across Typed Ideation Operations in Scientific Literature](http://arxiv.org/abs/2608.27394v1) | Sharon, Hope | Evaluates retrieval systems across different levels of scientific ideation abstraction—zooming in and out—rather than simple factual lookup. Provides a more nuanced benchmark for AI-assisted scientific discovery. |
| [LLMs Can Design Near-Optimal OR Algorithms](http://arxiv.org/abs/2608.27296v1) | Baek | Shows LLMs can design near-optimal algorithms for inventory control, queueing networks, and assortment optimization problems. Demonstrates that language models can contribute to algorithmic operations research beyond text generation. |
| [CorporateBench: Large-Scale Q&A Benchmarking with Temporal Knowledge Bases](http://arxiv.org/abs/2608.27391v1) | Hamilton, Sun, Romero et al. | Presents a human-validated enterprise Q&A benchmark that tests temporal reasoning over large document collections, addressing the limitation of oversimplified synthetic datasets. Directly relevant to RAG systems in production environments. |

---

## 3. Research Trend Signal

Today's submissions reveal three converging trends. First, **inference-time compute is becoming a first-class resource**: CritICL, TTPO, and the Naive Prompt Optimization paper all treat reasoning budget at inference as a lever separate from training, pushing toward models that adapt their compute dynamically rather than relying purely on scale. Second, **agent data quality is superseding agent data quantity**: SWE-Prime, WikiSkill, and the ACE lens paper all argue that curated, high-signal trajectories matter more than volume—a shift from the "collect more" mentality of earlier agent research. Third, **evaluation integrity is under scrutiny**: the LLM-judge audit, RCMN's work on misleading discourse, and Not All Eval-Awareness Is Equal collectively signal a field maturing past benchmark gaming toward causal, transparent evaluation methodology. Together, these point toward a phase of reinforcement learning and agentic systems where robustness, auditability, and cost efficiency are prioritized over raw capability scaling.

---

## 4. Worth Deep Reading

1. **[TTPO: Test-Time Policy Optimization](http://arxiv.org/abs/2608.27448v1)** — This is the most consequential methodological paper of the batch. By enabling per-sample policy optimization at inference without ground-truth labels, it closes a fundamental gap between training-time RLVR and deployment-time adaptation. Its implications span math reasoning, code generation, and any domain where verifiable rewards exist but ground truth is unavailable.

2. **[Consolidating RLVR Capabilities Across Domains](http://arxiv.org/abs/2608.27409v1)** — As the field moves from single-domain RLVR wins toward generalist reasoning models, understanding merge vs. distill vs. route trade-offs is essential. This paper provides the first systematic taxonomy, making it a practical reference for anyone building multi-capability LLMs from specialized checkpoints.

3. **[Difference-in-Differences on a Censored Rating Scale Can Manufacture an Effect](http://arxiv.org/abs/2608.27309v1)** — A must-read for anyone using LLM judges in evaluation pipelines. The pre-registered audit design and the finding that standard DiD identification fails on bounded scales directly undermines a significant portion of recent comparative LLM evaluation work, and its conclusions will reshape evaluation methodology.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*