# ArXiv AI Research Digest 2026-07-28

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 50 papers | Generated: 2026-07-28 03:14 UTC

---

# ArXiv AI Research Digest — July 28, 2026

## Today's Highlights
Research this week emphasizes moving LLMs toward socially intelligent autonomy through frameworks like **Zhijing**, which infers mental states and adapts behavior in human environments. Significant progress is being made in verifying and securing agentic systems via formal methods (**DualityCert**, **Formally Verified Floating-Point**) and security audits (**Do LLMs Know Their Vulnerable Scenarios?**). Furthermore, specialized attention mechanisms for scientific computing (**Variational-Ising-Attention**) alongside tools for agent orchestration (**Focus Is All You Need**) highlight a shift toward domain-specific precision and efficient multi-agent coordination rather than general-scale scaling alone.

## Key Papers

### 🧠 Large Language Models (architecture, training, alignment, evaluation)
| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [**Zing: Social Mind for LLMs**](http://arxiv.org/abs/2607.23740v1) | Zing Team et al. | Presents Zhijing, an integrated framework enabling LLMs to track social relations, reason over norms, and adapt behavior in long-term human settings. This is critical as models transition from isolated task solvers to persistent service agents requiring genuine social intelligence. |
| [**Language Shapes Instruction Hierarchy Compliance in Multilingual LLMs**](http://arxiv.org/abs/2607.23545v1) | Jiwon Moon et al. | Investigates whether language influences how multilingual LLMs prioritize instructions by source. The findings suggest alignment benchmarks must expand beyond English to ensure safe, controllable deployment across diverse linguistic contexts. |
| [**ATLAS: Automated Approximation of Transformers for Efficient Homomorphic Inference in One Hour**](http://arxiv.org/abs/2607.23478v1) | Jianhang Xie et al. | Proposes ATLAS, a method to automatically approximate non-linear operations in transformers for homomorphic encryption, reducing inference cost while preserving privacy. This addresses the computational bottleneck preventing secure private inference on large models. |

### 🤖 Agents & Reasoning (planning, tool use, multi-agent, chain-of-thought)
| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [**E-Bench: Benchmarking Multi-Step Tool-Use Agents in Real-World Product Scenarios**](http://arxiv.org/abs/2607.23722v1) | Weihuang Zheng et al. | Introduces E-Bench, a benchmark evaluating LLM agents on complex, stateful interactions involving hidden information gathering and step-by-step tool commitment. It fills a gap left by simpler benchmarks that do not reflect real-world product scenarios. |
| [**Focus Is All You Need: Adaptive Goal-aware Attention Orchestration for Multi-Agent Graph Systems**](http://arxiv.org/abs/2607.23678v1) | Mingzhou Fan et al. | Describes a mechanism where LLM-based agents organize into specialized graph nodes with adaptive attention orchestration. This improves flexibility and coordination in multi-agent planning without sacrificing interpretability or increasing overhead. |
| [**Delegation Intelligence in Deep Search: A Controllable Framework for Disentangled Capability Diagnosis**](http://arxiv.org/abs/2607.23524v1) | Xinhao Yao et al. | Offers a framework to disentangle retrieval, comprehension, verification, and tool-use decisions during deep search tasks. By diagnosing capabilities individually, it allows better control and improvement of agentic workflows beyond end-to-end accuracy metrics. |

### 🔧 Methods & Frameworks (new techniques, benchmarks, efficiency improvements)
| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [**Compute Globally, Materialize Locally: The Memory Contract of Sparse Event-KV**](http://arxiv.org/abs/2607.23693v1) | Zefeng Cai et al. | Analyzes the premise underlying KV cache eviction schemes for long-horizon agents—whether retained events remain informative after original observations are dropped. This informs more reliable memory contracts for agent systems. |
| [**Variational-Ising-Attention (VIA)**](http://arxiv.org/abs/2607.23634v1) | Rui Wang | Proposes VIA, tailored attention using variational Ising models to capture dependencies beyond softmax independence assumptions. Designed for science tasks where long context isn’t the constraint but contextual richness is key. |
| [**MS-GPT: Rethinking MS/MS De Novo Structure Elucidation...**](http://arxiv.org/abs/2607.23607v1) | Xin Zhao et al. | Reformulates mass spectrometry structure elucidation as spectrum-induced posterior querying of a molecule-language model. Moves away from library dependency toward generative de novo identification, advancing chemistry-AI integration. |

### 📊 Applications (domain-specific, multimodal, code generation)
| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [**EmoTrace: An Emotion Trajectory-Centered Framework for Psychological Support Dialogue Generation**](http://arxiv.org/abs/2607.23648v1) | Kaitong Weng et al. | Constructs high-quality psychological support dialogue corpora focused on emotion trajectories over time, providing foundational data for training counseling-oriented conversational AI systems that respond empathetically to evolving user moods. |
| [**CALMRec: Causally Aligned Language Memory for Long-Horizon Recommendation**](http://arxiv.org/abs/2607.23647v1) | Gengyu Zhan | Addresses feedback loops in recommender systems by causally aligning memory components to separate enduring preferences from transient intent and exposure-induced behavior, improving recommendation robustness over time. |
| [**The Cross-Domain Generalization Cost of Offensive Language Detection**](http://arxiv.org/obs/2607.23512v1) | Ruixing Ren et al. | Provides a systematic methodology to decompose performance degradation of offensive language detection models when deployed across datasets and languages, helping developers understand and mitigate cross-domain failure modes. |

## Research Trend Signal
There is a clear convergence on **trustworthy agency**—not just building smarter agents, but making them verifiable, accountable, and socially coherent. Topics such as earned authority under fixed ceilings (paper #26), mission-level runtime assurance for swarm ISR (paper #35), and iterative reprompting to close security gaps in code generation (paper #6) signal growing concern with safety at scale. Simultaneously, domain-aware architectures emerge: VIA for scientific reasoning (#17), MS-GPT for chemistry (#22), and EmoTrace for mental health (#14). We’re seeing less focus on pure model size and more on **modular verify-and-deploy pipelines**, especially around tool use, memory contracts, and causality in recommendations. The field appears maturing from “what can we make?” to “how do we guarantee it works safely across domains?”

## Worth Deep Reading

1. **[Zing: Social Mind for LLMs](http://arxiv.org/abs/2607.23740v1)** – This paper represents a major leap toward social AI. If LLMs are to serve long-term in human environments, they need theory-of-mind-like capacities. Zhijing’s approach to tracking relations and norms could become foundational for future personal assistants or companions.

2. **[E-Bench: Benchmarking Multi-Step Tool-Use Agents...](http://arxiv.org/abs/2607.23722v1)** – As agents grow more autonomous, benchmarks must evolve beyond single-step tasks. E-Bench’s focus on real-world scenarios with stateful environments offers a much-needed standard for evaluating practical deployment readiness.

3. **[ATLAS: Automated Approximation of Transformers...](http://arxiv.org/abs/2607.23478v1)** – Homomorphic encryption remains one of the hardest challenges for deploying ML securely. ATLAS’ hour-long approximation pipeline makes private inference feasible for practitioners—a rare win-win between usability and cryptographic rigor.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*