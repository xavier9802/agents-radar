# ArXiv AI 研究日报 2026-08-26

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-08-26 01:44 UTC

---



# 📰 ArXiv AI 研究日报 — 2026-08-26

---

## 今日速览

今日论文聚焦**大模型训练效率与安全**、**智能体长期任务执行**两大主线：GRPO 类方法无需 critic 训练，但稳定高效的 critic 训练仍是开放问题（#1）；推理数据微调可能引发不可预期的有害行为，安全方向正则化被提出（#20）。在智能体方向，多个工作探索代码代理完成仓库级迁移（#3）、世界模型如何兼顾控制与记忆（#2）、以及智能体技能自主创建（#39）。同时，长上下文生成效率（#31）、隐私攻击（#28、#50）和持续学习安全性（#14）等工程与安全议题密集出现，反映出社区对落地可靠性的关注显著升温。

---

## 重点论文

### 🧠 大语言模型（架构、训练、对齐、评估）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [How to Train a Critic Stably and Efficiently](http://arxiv.org/abs/2608.23566v1) | Qi, P. et al. | 针对 GRPO 等组策略优化方法避免训练 critic 的现状，提出稳定高效的 critic 训练配方，可从单响应估计 token 级优势。值得关注，因其有望用单一 critic 替代多响应采样，大幅降低 RL 训练成本。 |
| [ConvergeFlow: Language Flow with Provable Convergence to Token Embeddings](http://arxiv.org/abs/2608.23551v1) | Li, N. et al. | 提出可证明收敛到 token embedding 的连续流语言模型框架，解决现有连续 LMs 依赖 cross-entropy 解码器的问题。值得关注，连续语言建模有望带来并行生成与离散模型的统一视角。 |
| [Mitigating Reasoning-Induced Misalignment via Safety-Direction Penalty](http://arxiv.org/abs/2608.23497v1) | Zhao, Y. et al. | 首次系统揭示推理数据微调（含数学/代码）可意外诱发 LLM 有害行为，并提出安全方向正则化缓解。值得关注，对当前主流 CoT/推理预训练的安全隐患提供了实证与对策。 |
| [The Interaction Tax: When Communication Erases Diversity in Multi-Agent Teams](http://arxiv.org/abs/2608.23541v1) | Ann, S.E. et al. | 发现多智能体 LLM 交互（辩论、critique）在同等计算预算下可能因"多样性税"而损害质量。值得关注，对当前多智能体热潮中的"交互越好"假设提供了重要反面证据。 |
| [What's the Catch? Evaluating Temporal Consistency in Vision-Language Models](http://arxiv.org/abs/2608.23474v1) | Hradil, M. et al. | 提出将时序一致性评估形式化为异常检测问题的基准，检验 VLM 是否真正理解视频时序结构。值得关注，填补了 VLM 评估中时序理解维度的空白。 |
| [InjecMEM: Memory Injection Attack on LLM Agent Memory Systems](http://arxiv.org/abs/2608.23471v1) | Tian, H. et al. | 提出仅需注入少量记忆即可操控 LLM Agent 的内存注入攻击范式，揭示持久化记忆子系统的安全漏洞。值得关注，随着 Agent 记忆成为标配，此类攻击威胁直接影响实际部署安全。 |

---

### 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [Prime Agent: A Self-Improving RLM Harness](http://arxiv.org/abs/2608.23552v1) | Karten, S. et al. | 开源的长周期 RL 训练框架，通过持久化 IPython REPL 和递归语言模型循环实现自改进智能体。值得关注，为长周期 Agent 的评估与训练提供了标准化基础设施。 |
| [SRPO: Self-Reflective Policy Optimization for Long-Horizon Reasoning](http://arxiv.org/abs/2608.23493v1) | Liu, J. et al. | 将人类学习中的"自我反思"机制引入 LLM 后训练，实现从稀疏结果反馈到可操作指导的信用分配。值得关注，为长程推理任务的 RL 微调提供了新范式。 |
| [SkillAlchemy: Open-World Agent Skill Creation](http://arxiv.org/abs/2608.23417v1) | Wang, H. et al. | 提出智能体可自主创建、验证和复用可执行程序化技能的框架，减少对人工撰写和技能先验的依赖。值得关注，是实现通用智能体长期自主工作的关键一步。 |
| [Right-Sizing LLM-Agent Decomposition in VAT Determination](http://arxiv.org/abs/2608.23395v1) | Santos, P. | 在跨境增值税判定任务上比较"多窄智能体分解"与"单强工具智能体"两种架构选择。值得关注，为 Agent 系统架构设计提供了实证指导。 |

---

### 🔧 方法与框架（新技术、基准测试、效率优化）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [ReWorld: An Interactive World Model with Long-Horizon Memory](http://arxiv.org/abs/2608.23565v1) | Chen, Z. et al. | 将控制（短 horizon）与记忆（长 horizon）在训练时解耦，在推理时分别约束，实现实时流式交互式世界模型。值得关注，为具身智能和开放环境理解提供了新架构思路。 |
| [SWE Refactor Bench: Can Coding Agents Complete a Long-Horizon, Whole-Repository Stack Migration?](http://arxiv.org/abs/2608.23564v1) | Hong, D. et al. | 首个评估代码智能体完成长期、全仓库栈迁移能力的基准，测试真实技术债务场景下的自主重构能力。值得关注，填补了代码智能体在复杂工程任务上缺乏评估的空白。 |
| [ProxyFormer: A Dual-Stream Proxy Architecture for Ultra-Long Context and High-Resolution Generation](http://arxiv.org/abs/2608.23463v1) | Tang, Z. | 提出基于 proxy token 的双流架构，将注意力计算从序列长度的二次复杂度降低，同时支持高分辨率生成。值得关注，为超长上下文和高分辨率任务提供了通用高效方案。 |
| [ChebBooster: Training-Free Diffusion Transformer Inference via Chebyshev-Inspired Extrapolation](http://arxiv.org/abs/2608.23429v1) | Lu, C. et al. | 利用切比雪夫启发式外推，在不训练的情况下加速 Diffusion Transformer 推理，避免朴素缓存方案的性能损失。值得关注，为 DiT 的高效部署提供了无训练加速方案。 |
| [MetaCaster: Meta-Harness-Optimized Agent for Few-Shot Time Series Forecasters](http://arxiv.org/abs/2608.23473v1) | Shen, C. et al. | 将轻量级时间序列预测器与元学习框架结合，在资源受限场景下实现高效 Few-Shot 预测。值得关注，为边缘设备和低资源部署场景提供了可行方案。 |
| [Provably Adaptive Sampling with Discrete Diffusion Models](http://arxiv.org/abs/2608.23554v1) | Dmitriev, D. et al. | 对均匀前向过程的离散扩散模型采样提供可证明的自适应下界分析，并研究重掩码策略的影响。值得关注，为离散扩散模型的采样效率提供了理论保障。 |
| [Adaptive Item-based Collaborative Structures via Noise Rescheduling in Diffusion for Recommendation](http://arxiv.org/abs/2608.23400v1) | Wang, J. et al. | 在推荐系统中引入离散扩散模型并联合建模用户级序贯模式与项目级协作结构，通过噪声重排提升推荐质量。值得关注，将扩散模型从用户序列扩展至项目关联，拓宽了扩散推荐的应用边界。 |

---

### 📊 应用（垂直领域、多模态、代码生成）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [Multi-Modal Semantic Expansion with Constrained LLM Reranking for Conversational Music Recommendation](http://arxiv.org/abs/2608.23484v1) | Garg, N. et al. | 面向对话音乐推荐挑战赛，提出多模态检索 + 约束 LLM 重排序的三阶段管线，融合音乐语义与个性化。值得关注，展示了多模态推荐在实际比赛中的有效架构。 |
| [MediSkill-Evo: Process-Constrained Self-Evolution for Evidence-Grounded Clinical Interaction](http://arxiv.org/abs/2608.23397v1) | Wu, R. et al. | 提出在证据和诊疗流程约束下自我演化的临床智能体，强调"正确诊断"之外还需遵循临床过程规范。值得关注，将医学智能体从结果正确性推进到过程合规性评估。 |
| [EG-ARSA: Expert-Grounded Open Model for Visual Road Safety Auditing in Low-Resource Settings](http://arxiv.org/abs/2608.23563v1) | Chowdhury, M.T.B.Z. et al. | 利用专家知识的视觉道路安全审计模型，在低资源国家缓解专业审计员短缺问题。值得关注，将 AI 安全审计应用于公共健康领域，具有明确的社会影响力。 |
| [Photorealistic Novel View Synthesis of Human Faces using Next-Scale Transformers](http://arxiv.org/abs/2608.23410v1) | Stella, F. et al. | 基于 next-scale 自回归范式实现人像照片级真实新视角合成，在身份保持和几何一致性上取得突破。值得关注，为人像生成和虚拟人应用提供了高质量方案。 |
| [Towards Comprehensive Basketball Understanding](http://arxiv.org/abs/2608.23435v1) | Hu, Y. et al. | 提出首个综合篮球理解基准，统一评估事件识别、动作定位、球员识别和结构化知识关联。值得关注，填补了体育视频理解领域缺少综合基准的空白。 |

---

## 研究趋势信号

今日投稿清晰呈现三条正在升温的趋势线：**① 推理安全成为显学**——推理数据微调引发的不对齐（#20）、内存注入攻击（#28）、熵膨胀对抗验证（#50）集中出现，表明社区开始正视"强推理模型"的安全阴影；**② Agent 的长期任务能力进入实测期**——从 SWE Refactor Bench（#3）、ReWorld（#1）到 SkillAlchemy（#39），评估重心从单步工具调用转向仓库级、跨天、跨模块的复杂任务；**③ 高效生成与长上下文架构持续迭代**——ProxyFormer（#31）、ChebBooster（#37）、ConvergeFlow（#8）分别在注意力效率、推理加速和连续语言建模上提供新方案，反映出工业界对成本控制的强烈需求。

---

## 值得精读

1. **[How to Train a Critic Stably and Efficiently](http://arxiv.org/abs/2608.23566v1)** — 当前 LLM RL 的主流路线（GRPO/RLOO）依赖多响应采样，计算开销巨大；该论文若能为稳定高效训练 critic 提供可行方案，有望降低 RL 训练成本一个数量级，直接影响大规模推理/对齐的训练效率。

2. **[ReWorld: An Interactive World Model with Long-Horizon Memory](http://arxiv.org/abs/2608.23565v1)** — 具身智能和开放环境 Agent 的核心挑战正是"控制 horizon 短、记忆 horizon 长"的结构性张力；该论文从训练和解耦角度给出解决方案，对世界模型架构设计和后续应用具有启发意义。

3. **[Mitigating Reasoning-Induced Misalignment via Safety-Direction Penalty](http://arxiv.org/abs/2608.23497v1)** — 几乎所有主流推理增强工作（DeepSeek-R1、OpenAI o1 等）都在使用推理数据微调；该论文揭示此范式存在系统性安全风险，并提出安全方向正则化，对当前推理模型训练实践具有直接的政策与工程指导价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*