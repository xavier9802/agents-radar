# ArXiv AI 研究日报 2026-08-06

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-08-06 03:16 UTC

---



# ArXiv AI 研究日报 — 2026-08-06

---

## 今日速览

今日 ArXiv 投稿继续围绕"长程推理（Long-Horizon Reasoning）"展开，多篇论文聚焦如何让模型在复杂任务中切换技能、持久化执行并自我校正。与此同时，智能体内存架构、强化学习后训练的效率优化，以及AI安全/对齐评估成为三大热点方向。一个值得注意的趋势是：研究从"训练更大模型"转向"让模型学会用推理链和结构化记忆管理复杂任务"。

---

## 重点论文

### 🧠 大语言模型

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :---|
| [Reasoning Core: Designing Broad Procedural Data for Completion-Supervised Reasoning Training](http://arxiv.org/abs/2608.05148v1) | Damien Sileo et al. | 提出 Reasoning Core，包含 50 个程序生成器，用于完成式监督微调的推理数据构建。填补了过程生成器在推理训练中的空白，值得推理数据方向关注。 |
| [Toward Skill-Native LLMs: Skill Entropy for Benchmarking and Training Long-Horizon Reasoning](http://arxiv.org/abs/2608.05139v1) | Yinghui He et al. | 提出"技能熵"概念，用于度量模型在跨技能长程任务中的推理能力。为长程推理评估和训练提供了新指标。 |
| [DelusionEval: Measuring Delusion-Linked Behaviors in AI Chatbots](http://arxiv.org/abs/2608.05004v1) | Jared Moore et al. | 首次系统性评估聊天机器人中的"妄想螺旋"行为——人机行为相互强化的风险。对AI心理健康安全评估具有重要意义。 |
| [Protoreasoning in Tiny Transformers](http://arxiv.org/abs/2608.04980v1) | Eduardo Valle et al. | 证明约100万参数的小模型也能从简单思维链中受益，为低资源推理研究打开新窗口。 |
| [Strengthening Target-Language Features: SAE-Based Steering for Multilingual Inference](http://arxiv.org/abs/2608.04904v1) | Hongsheng Wang et al. | 利用预训练稀疏自编码器在推理时引导多语言大模型，无需额外参数更新即可提升低资源语言表现。 |
| [Same Formulas, Different Semantics: Do Language Models Follow Modal Logic Specifications?](http://arxiv.org/abs/2608.05097v1) | Réemi Andrieu et al. | 检验语言模型是否真正理解模态逻辑中形式相同但语义不同的推理规则，揭示了当前模型在形式推理上的深层缺陷。 |

### 🤖 智能体与推理

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :---|
| [Argus: A General-Purpose Agentic Runtime for Long-Horizon Reasoning](http://arxiv.org/abs/2608.05144v1) | Boxiu Li et al. | 提出持久化自进化智能体运行时，支持 Manager/Planner/Engineer 角色分工，在证据支持时保持策略、在失败信号出现时主动调整。为长程智能体架构提供了新范式。 |
| [ABSeeker: Training Long-Horizon Search Agents via Answer-Backtracked Credit Assignment](http://arxiv.org/abs/2608.05102v1) | Yijun Lu et al. | 通过答案回溯信用分配解决长程搜索智能体训练中的步骤价值分配问题，使中间检索/验证步骤也能获得有效梯度信号。 |
| [Hierarchical Graph Memory for LLM Agents with Path-level Localization and Rewrite](http://arxiv.org/abs/2608.05095v1) | Xiawei Yue et al. | 引入层次图记忆结构，支持路径级定位与重写，解决长时推理智能体记忆更新效率低的痛点。 |
| [WorldCycle: Self-Verifiable Reinforcement Learning for Long-Horizon Video World Models](http://arxiv.org/abs/2608.04964v1) | Bohai Gu et al. | 针对视频世界模型的累积误差问题，提出自验证强化学习方法，使模型能在无真实标签的情况下自我校正。 |
| [State2State: Environment-Derived Mid-Training for LLM Agents](http://arxiv.org/abs/2608.04934v1) | Xuanyu Lei et al. | 从环境交互中自动生成训练信号进行中途训练，减少对人工标注轨迹的依赖，提升智能体训练可扩展性。 |
| [Capability-Gated Planning: Cost-to-Goal Discovery and the Limits of Myopic Experiment Selection](http://arxiv.org/abs/2608.05085v1) | Ahmed Hassoon et al. | 指出贪心实验选择方法的局限性，提出能力门控规划框架用于自动化科学发现中的资源分配决策。 |

### 🔧 方法与框架

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :---|
| [OctoLong: Mid-Training On Cross-Repository Code Contexts Enhances Long-Context Modeling](http://arxiv.org/abs/2608.05141v1) | Indraneil Paul et al. | 通过跨仓库代码上下文的中途训练增强长上下文建模能力，开辟了长上下文训练数据的实用新方向。 |
| [SpecRoll: Fast-Slow Verifier-Feedback Adaptation for Speculative Reinforcement Learning Rollouts](http://arxiv.org/abs/2608.04962v1) | Nhat Minh Pham et al. | 将投机解码与强化学习 rollout 结合，提出快慢验证器反馈机制，显著加速推理 RL 的训练效率。 |
| [OPD-V: Visual On-Policy Self-Distillation with Modality Balance](http://arxiv.org/abs/2608.05131v1) | Aniri et al. | 解决视觉多模态大模型后训练中模态不平衡问题，通过策略自我蒸馏提升视觉推理性能。 |
| [Revealed Rationality: Label-Free Evaluation and Regularization from Representation Theorems](http://arxiv.org/abs/2608.05015v1) | Isaiah Andrews | 将决策理论中的显示理性表示定理应用于LLM的无标签评估与正则化，为模型行为分析提供新的数学基础。 |
| [SSTQ: Privacy-Preserving Vector Quantization via Subsampled Stochastic TurboQuant](http://arxiv.org/abs/2608.05127v1) | Adel Javanmard et al. | 提出基于子采样随机 TurboQuant 的隐私保护向量量化方法，在分布式优化中实现低通信成本与本地差分隐私的平衡。 |
| [UG-UMRE: Uncertainty-Guided Modality Augmentation and Distributional Calibration for Unified Multimodal Relation Extraction](http://arxiv.org/abs/2608.04949v1) | Bo Kong et al. | 通过不确定度引导的模态增强和分布校准解决多模态关系抽取中的噪声传播和异构性问题。 |

### 📊 应用

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :---|
| [Teaching Nemotron Greek: Mining a Corpus, Adapting Retrieval, and Grounding Generation for Modern Greek across Specialist Domains](http://arxiv.org/abs/2608.05138v1) | Ayoub Kirouane et al. | 首次系统构建现代希腊语检索-生成适配方案，覆盖法律、能源、金融、医疗等专业领域，填补低资源语言AI基础设施空白。 |
| [MarsCast: Transfer Learning of AI Weather Foundation Models to Planetary Atmospheres](http://arxiv.org/abs/2608.05054v1) | M. L. Carroll et al. | 将地球气象基础模型 GraphCast 迁移到火星大气模拟，验证了跨行星天气预测的可行性，为行星科学提供新工具。 |
| [ORACLE: A Multi-Objective Reinforcement Learning-Based Analog Circuit Design Optimizer with Large Language Models-Guided Exploration](http://arxiv.org/abs/2608.04999v1) | Osei Brempong et al. | 结合多目标强化学习与LLM引导探索，实现模拟电路自动化设计优化，将AI引入半导体设计流程。 |
| [VQ-VAD: Vector-quantized Motion Representation Learning for Human-centric Video Anomaly Detection](http://arxiv.org/abs/2608.05069v1) | Narges Rashvand et al. | 利用向量量化运动表示学习提升以人为中心的视频异常检测性能，同时缓解隐私和视觉噪声问题。 |
| [RepairFormer: Automated Repair of Structured Inputs Using Transformers](http://arxiv.org/abs/2608.05060v1) | Ovi Paul et al. | 提出基于 Transformer 的自动修复方法，处理 JSON、DOT、OBJ 等结构化输入文件的损坏问题，提升软件系统鲁棒性。 |
| [MultiPathFormer: Towards a Foundation Model for Multipath Wireless Propagation](http://arxiv.org/abs/2608.05076v1) | Blessed Guda et al. | 构建无线传播基础模型 MultiPathFormer，支持信道估计、波束预测和定位任务，推动无线通信AI化。 |

---

## 研究趋势信号

今日投稿显示三大趋势：一是**长程推理训练基础设施化**，Reasoning Core、ABSeeker、Skill-Native 等论文共同指向"如何系统性构建长程推理数据与训练方法"；二是**智能体记忆与执行架构分离**，Hierarchical Graph Memory、Argus、State2State 表明研究者正从单一策略网络转向"规划-记忆-执行"分层架构；三是**效率优先的后训练方法**，SpecRoll、OPD-V、OctoLong 均聚焦用更少的计算资源获得更强的推理能力，反映出行业对成本敏感的务实转向。

---

## 值得精读

1. **Argus** — 长程智能体运行时的系统级设计，Manager/Planner/Engineer 分工与持久化自我演化机制对智能体架构研究有直接启发。

2. **Reasoning Core** — 50 个程序生成器覆盖数学、逻辑、规划等多领域，为推理数据工程提供了可复用的基础设施参考，适合关注推理训练的研究者。

3. **DelusionEval** — 首次将"妄想螺旋"这一心理健康概念引入AI评估，为聊天机器人长期交互风险分析提供了新框架，对AI安全社区有重要参考价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*