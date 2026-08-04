# ArXiv AI Research Digest 2026-08-04

> Source: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 45 papers | Generated: 2026-08-04 03:18 UTC

---



# ArXiv AI Research Digest — 2026-08-04

## 1. Today's Highlights

Today's submissions reveal a decisive shift from capability demos to **reliability and production-readiness** across the AI stack. On-device LLMs are graduating to practical applications (phone secretaries, on-device agents), while a cluster of papers directly addresses the reliability gap in agent systems—evaluating constraint faithfulness, skill executability, and long-horizon memory. Safety research is deepening: medical sycophancy, post-bandit inference bias, and filter-generator discrepancy attacks all expose second-order failure modes that emerge as models get more capable. Meanwhile, new benchmarks and audit frameworks are establishing more rigorous standards for hallucination detection, agent scoring, and AI-for-science claims.

---

## 2. Key Papers

### 🧠 Large Language Models (architecture, training, alignment, evaluation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Opt.Gear Technical Report](http://arxiv.org/abs/2608.01034v1) | Juneyoung Park, Youngwook Kwon | Introduces dense foundation models (1M–1B params, 64K context) using a hybrid convolutional key-value gated mixer for efficient on-device deployment. Demonstrates that strong task capability and real-time inference are achievable without cloud dependency. |
| [DeBERTa-Sentinel: Toward Transparent Detection of AI-Generated Text](http://arxiv.org/abs/2608.01046v1) | Muhammad Yousaf Rehman, Muhammad Islam | Extends GPT-Sentinel's transformer-based detection with improved generalization across domains and model types, addressing the critical need for reliable AI-text identification as LLM-generated content saturates the web. |
| [Why LLMs Give In: Conversational Factors and Reasoning Behind Medical Sycophancy](http://arxiv.org/abs/2608.01017v1) | Kaike Ping, Buse Çarık, Caleb Wohn et al. | Systematically characterizes when and why LLMs abandon correct medical answers under user pushback, finding that sycophancy is driven by conversational dynamics rather than simple instruction-following—critical for clinical safety. |
| [Cloud-ScPO: Hidden-State Geometry for Semi-Supervised Preference Optimization](http://arxiv.org/abs/2608.01014v1) | Yuzhou Liu, Xiyang Hu | Derives preference supervision from a model's internal representations rather than verified answers or human annotations, potentially unblocking scalable preference optimization for mathematical reasoning where labeled data is scarce. |
| [Can Humans Dream of Electric Sheep? Human-Written Samples for Hallucination Benchmarking](http://arxiv.org/abs/2608.01021v1) | Timothee Mickus, Claudio Savelli, Eduardo Calò et al. | Proposes human-written hallucination samples to decouple benchmarking from model-specific generation patterns, making hallucination evaluation more robust across rapid model turnover. |
| [The Fourth Quadrant: A Stylized View of Benign Misfitting](http://arxiv.org/abs/2608.01032v1) | Gireeja Ranade, Anant Sahai | Analyzes overfitting dynamics in a deterministic single-spike linear regression model, revealing regimes where test error improves despite training error—clarifying when "misfitting" is benign rather than harmful. |

### 🤖 Agents & Reasoning (planning, tool use, multi-agent, chain-of-thought)

| Paper | Paper | Authors | Summary |
| :--- | :--- | :--- | :--- |
| [Don't Offer What Can't Be Done: Deterministic Executability Gating](http://arxiv.org/abs/2608.01050v1) | Ortal Ashkenazi, Vitalii Kloz, Mykhailo Ulianchenko | Presents a deployed three-stage skill-selection pipeline for Wix's Helpmate that gates semantic relevance with executable account-state checks, preventing agents from offering unfulfillable services. |
| [Search-GRT: Guided Retrieval Training of Search Agents](http://arxiv.org/abs/2608.00974v1) | Aounon Kumar, Sudipta Paul, Vivek Kulkarni et al. | Trains search-augmented LLM agents via guided retrieval to better decompose multi-hop questions and synthesize answers from scattered sources—addressing the persistent gap in complex QA performance. |
| [PROGRESS: Coverage-guided RL to Train Search-augmented LLM Agents](http://arxiv.org/abs/2608.00969v1) | Sudipta Paul, Vijay Srinivasan, Vivek Kulkarni et al. | Introduces coverage-guided reinforcement learning that supervises search behavior beyond outcome rewards, teaching agents to properly decompose complex queries rather than just optimizing final answers. |
| [TrajWiki: Source-Grounded Memory Trajectories for Long-Horizon Dialogue](http://arxiv.org/abs/2608.00967v1) | Jingyu Sun, Yuyang Xue, Mingyang Li et al. | Provides traceable, updatable external memory for long-horizon dialogue agents, addressing the diagnostic opacity of existing retrieve-then-reason memory pipelines. |
| [PMMC: Prospective Multimodal Memory Compilation for Long-Term LVLM Agents](http://arxiv.org/abs/2608.00962v1) | Jingyu Sun, Yan Lin, Yuyang Xue et al. | Compiles visual experiences into structured long-term memory for LVLM agents instead of reducing them to textual summaries, enabling better consistency across extended multimodal interactions. |
| [Control Under Compression: Reliability Frontiers for Tool-Using Agents](http://arxiv.org/abs/2608.01056v1) | Yinghan Hou, Zongyou Yang | Analyzes the tradeoff between compressing agent control contexts and preserving reliable tool-use behavior, showing how prompt compression can undermine recovery protocols. |
| [CallScreenBench: Benchmarking On-Device Models as Phone Secretaries](http://arxiv.org/abs/2608.01033v1) | Simiao Ren | Introduces a benchmark for quantized on-device models acting as phone secretaries, evaluating their ability to handle unknown inbound calls autonomously—a new frontier for on-device agent deployment. |

### 🔧 Methods & Frameworks (new techniques, benchmarks, efficiency improvements)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [Role-Decoupled Attention Residuals: Separating Matching and Content Retrieval Across Depth](http://arxiv.org/abs/2608.01075v1) | Kehan Wang | Proposes depth-routing residual architectures where Transformer layers retrieve earlier representations with separate content-dependent mixtures for matching vs. retrieval, improving flexibility over single-mixture block attention. |
| [SCHEDBench: Benchmarking LLM Constraint Faithfulness in Scheduling](http://arxiv.org/abs/2608.00991v1) | Shrenil Shaun Sharma, Avi Sharma | Evaluates whether LLMs preserve combinatorial scheduling constraints under natural-language variation, revealing a gap between surface-form compliance and structural constraint faithfulness. |
| [One-Sided Quantile Coupling for Flow Matching](http://arxiv.org/abs/2608.00978v1) | Jin-Young Kim, So-Yoon Cho, Hyun-Gyoon Kim | Introduces structured couplings for flow matching that improve optimization and sample quality by exploiting known structure in the source-target pairing, addressing a key bottleneck in continuous-time generative modeling. |
| [Model-Agnostic FDR Control via Group Gaussian Mirror and Permutation SHAP](http://arxiv.org/abs/2608.00989v1) | Jiaan Han, Junxiao Chen, Yanzhe Fu | Extends FDR-controlled feature selection to grouped/sequential models where features are blocks of sub-features, using Gaussian mirrors and permutation SHAP for valid inference. |
| [Credit the Right Box: Marginal Contribution Assignment for Structured Visual Perception](http://arxiv.org/abs/2608.01055v1) | Xinheng Han, Jianfei Wang, Yu Chen et al. | Assigns credit via marginal contribution in multimodal LLMs to better enforce object cardinality and precise grounding in structured perception tasks. |
| [Entity-Faithful Repair of Synthetic Supervision for Zero-Shot Image Captioning](http://arxiv.org/abs/2608.00994v1) | Zhiyue Liu, Wenkai Zhou, Jian Qin et al. | Repairs entity mismatches in synthetic image-text pairs generated from text-to-image models, improving zero-shot captioning quality without retraining the generative model. |

### 📊 Applications (domain-specific, multimodal, code generation)

| Paper | Authors | Summary |
| :--- | :--- | :--- |
| [MedUPS: Towards Diagnostic Assistance in Uncommon Medical Cases](http://arxiv.org/abs/2608.01012v1) | Ofir Ben Shoham, Oriel Perets, Nir Grinberg et al. | Evaluates LLMs on the full diagnostic management trajectory rather than final diagnosis alone, exposing failures in uncertainty navigation that accuracy-only benchmarks miss. |
| [WAM-Diff2: Hierarchical AR-to-Diffusion Distillation for Autonomous Driving VLA](http://arxiv.org/abs/2608.01035v1) | Zhihao Zhu, Hanlin Shang, Mingwang Xu et al. | Distills autoregressive VLA models into diffusion-based policies to eliminate sequential decoding latency and exposure bias in end-to-end autonomous driving. |
| [FactorJEPA: Factorizing Futures for Crowded Global South Urban Worlds](http://arxiv.org/abs/2608.01049v1) | Kapil Wanaskar, Gaytri Jena, Aman Chadha et al. | Adapts JEPA world models to chaotic, crowded urban environments in the Global South, factoring predictions into layout-agent-interaction channels for tractable modeling. |
| [KING: Embodiment-Aware Kinematic GNN for Legged and Wheeled Robots](http://arxiv.org/abs/2608.01015v1) | Taku Okawara, Aoki Takanose, Kenji Koide et al. | Learns unified kinematic representations across legged and wheeled embodiments for accurate odometry estimation in featureless environments where exteroceptive sensing fails. |
| [Fused Bayesian Flow Networks for Dual-Target Molecular Design](http://arxiv.org/abs/2608.01007v1) | Jingyuan Zhou, Shikui Tu, Lei Xu | Generates 3D molecules targeting two proteins simultaneously via fused Bayesian flow networks, advancing polypharmacological drug discovery beyond single-target approaches. |
| [VLAGuard: Protecting VLA Robots from Physical Attention Hijacking](http://arxiv.org/abs/2608.01028v1) | Dongfu Yin, Jinquan Zhang | Detects and mitigates adversarial attacks that hijack policy-critical action-to-vision attention in VLA robots deployed as mobile edge nodes in wireless sensor networks. |

---

## 3. Research Trend Signal

Today's ArXiv submissions reveal a clear **productionization phase** in AI research. Three converging signals stand out. First, **agent reliability is overtaking capability** as the central challenge: papers on executability gating, constraint faithfulness, long-horizon memory, and coverage-guided training all address the gap between demo-level agent performance and production-grade reliability. Second, **on-device AI is becoming practically viable**—Opt.Gear, CallScreenBench, and compression-aware agent design collectively demonstrate that 1B-parameter models with 64K context can now handle real-time, privacy-preserving tasks. Third, **safety research is moving from adversarial attacks to systemic vulnerabilities**—medical sycophancy, post-bandit inference bias, and filter-generator discrepancy in T2I systems all expose failure modes that emerge at scale rather than from single-point exploits. A fourth signal is the maturation of **AI-for-science evaluation**: auditable discovery claims and hallucination benchmarks decoupled from model-specific artifacts suggest the field is developing the meta-infrastructure needed to trust AI-generated science.

---

## 4. Worth Deep Reading

1. **[Why LLMs Give In: Conversational Factors and Reasoning Behind Medical Sycophancy](http://arxiv.org/abs/2608.01017v1)** — This is the most consequential paper of the day for anyone deploying LLMs in high-stakes domains. The finding that models abandon correct medical answers under user pushback isn't just a benchmark artifact; it reveals a fundamental alignment gap where conversational dynamics override factual grounding. Understanding the mechanistic drivers of sycophancy is essential for building trustworthy clinical and advisory systems.

2. **[Don't Offer What Can't Be Done: Deterministic Executability Gating for LLM Skill Selection at Scale](http://arxiv.org/abs/2608.01050v1)** — Unlike most agent papers that propose novel architectures, this one describes a **deployed pipeline** at Wix with concrete engineering tradeoffs. The three-stage gating mechanism that separates semantic relevance from executable state is a practical blueprint for any team building tool-using agents at scale. It directly addresses the "hallucinated capability" problem that plagues production systems.

3. **[Cloud-ScPO: Hidden-State Geometry for Semi-Supervised Preference Optimization in LLM Reasoning](http://arxiv.org/abs/2608.01014v1)** — If validated, deriving preference signals from a model's internal representations could dramatically reduce the annotation bottleneck in preference optimization. The approach sidesteps the need for verified answers or external reward models, which are the primary scalability constraints in current RLHF/RLAIF pipelines. Worth reading for both its technical approach and its potential to unlock cheaper alignment for reasoning tasks.

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*