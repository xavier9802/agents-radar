# ArXiv AI 研究日报 2026-08-01

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-08-01 03:33 UTC

---



# ArXiv AI 研究日报（2026-08-01）

## 今日速览
今日投稿集中体现“效率优先、可验证部署”的研究转向：推理侧从复杂反思链回归重采样与自适应预算分配，训练侧强调蒸馏一致性与量化异质性适配；智能体侧则聚焦本地化算力约束下的扩展权衡与拓扑自演化。垂直领域落地正从“黑盒分类”迈向“结构化检索+可解释决策”，AI 研究加速向高可信、低开销的工程化阶段演进。

---

## 重点论文

### 🧠 大语言模型（架构、训练、对齐、评估）
| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [**$\beta$-OPSD: Deriving with Policy Optimization, Training with Self-Distillation**](http://arxiv.org/abs/2607.28582v1) | Jiawei Xu et al. | 揭示 vanilla OPSD 是 $\beta=1$ 的特例，通过引入调节参数 $\beta$ 缓解其对工程技巧的过度依赖。该方法为推理型语言模型的策略优化与自蒸馏提供了更稳定的训练结构。 |
| [**Sample More, Reflect Less: Self-Refine and Reflexion Lose to Repeated Sampling at Equal Token Cost**](http://arxiv.org/abs/2607.28576v1) | Iliya Mirzaei et al. | 在等量 token 预算下对比证明，重复采样显著优于自我修正、反思与辩论等复杂推理链。研究提示当前“重推理”范式可能高估了反思机制的收益，简洁采样更具性价比。 |
| [**SVR: Self-Verifying Refinement via Joint Verdict-Confidence Reinforcement Learning for Adaptive Test-Time Compute**](http://arxiv.org/abs/2607.28457v1) | Hongyu Chen et al. | 提出无外部验证器的多轮强化学习框架，联合学习预测结果与置信度以动态分配测试时计算。该设计避免了均匀分配或依赖外部反馈的缺陷，实现低成本自适应推理。 |
| [**Lightning OPD 2.0: Mitigating Style Bias in Cross-Teacher On-Policy Distillation for Large Reasoning Models**](http://arxiv.org/abs/2607.28449v1) | Yecheng Wu et al. | 针对跨教师策略蒸馏中教师风格与推理模式不一致导致的性能偏差，提出风格解耦与对齐机制。该方法在保持蒸馏密度的同时提升了推理模型的泛化稳定性。 |

### 🤖 智能体与推理（规划、工具使用、多智能体、思维链）
| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [**OSReward: Instituting Standardized Evaluation for Cross-Platform Computer-Use Reward Models**](http://arxiv.org/abs/2607.28609v1) | Qiushi Sun et al. | 构建面向跨平台计算机使用智能体的标准化奖励模型评估基准，解决现有验证器在轨迹判定时缺乏一致性的问题。该工作为 CUA 的训练数据筛选与 RL 优化提供了可复现的度量标准。 |
| [**Rethinking Inference-Time Scaling in Local Computer-Use Agents: Failure Modes and Compute Tradeoffs**](http://arxiv.org/abs/2607.28573v1) | Woongkyu Lee et al. | 系统分析本地部署计算机用智能体在推理扩展时的失效模式与算力权衡，指出受硬件约束时单纯堆叠 token 可能引发预算溢出或响应延迟。研究为隐私敏感场景下的 Agent 部署策略提供实用指南。 |
| [**MANTA: Multi-Agent Network Topology Adaptation for Self-Evolving Multi-Agent Systems**](http://arxiv.org/abs/2607.28527v1) | Mao-xun Huang et al. | 将多智能体系统的通信拓扑视为可在线学习的动态变量，而非固定设计或离线优化目标。该框架使 Agent 集群能根据任务演化自主重构协作结构，提升复杂场景下的协同效率。 |

### 🔧 方法与框架（新技术、基准测试、效率优化）
| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [**ReToken: One Token to Improve Vision-Language Models for Visual Retrieval**](http://arxiv.org/abs/2607.28627v1) | Yao Xiao et al. | 提出单一可学习嵌入 Token 作为显式检索信号，缓解长视觉上下文下性能随干扰物增长而下降的问题。该方法以极低参数代价显著提升 VLM 的视觉检索能力。 |
| [**DualG-MRAG: Decoupling Macro-Reasoning

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*