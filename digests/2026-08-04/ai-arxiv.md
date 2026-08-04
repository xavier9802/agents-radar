# ArXiv AI 研究日报 2026-08-04

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 45 篇论文 | 生成时间: 2026-08-04 03:18 UTC

---



# ArXiv AI 研究日报 — 2026-08-04

## 今日速览

今日 ArXiv 投稿呈现三大趋势：**端侧高效模型与部署**受到持续关注，Opt.Gear 和 CallScreenBench 分别展示了轻量架构设计与手机秘书应用场景；**智能体记忆与长期交互**成为热点，TrajWiki 与 PMMC 均针对长程对话中的可追溯记忆问题提出新方案；**生成模型效率优化**方面，WAM-Diff2 将自回归与扩散模型蒸馏结合，为自动驾驶 VLA 模型部署提供新思路。此外，AI 对齐与安全议题中，DeBERTa-Sentinel、VLAGuard 和 Caliber 分别从文本检测、物理对抗防御和模型提取防护等角度推进防御体系。

---

## 重点论文

### 🧠 大语言模型（架构、训练、对齐、评估）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Role-Decoupled Attention Residuals](http://arxiv.org/abs/2608.01075v1) | Wang, K. et al. | 提出深度路由残差架构，将匹配与信息检索解耦至不同 Transformer 层，突破了现有 Block Attention 仅用单一内容依赖混合的局限。值得关注，为深层网络表征流控制提供了新设计范式。 |
| [Opt.Gear Technical Report](http://arxiv.org/abs/2608.01034v1) | Park, J. et al. | 推出 1M/270M/1B 三种规模的端侧基础模型，采用卷积-KV 混合门控架构，支持 64K 上下文与实时推理。对移动端部署具有重要工程参考价值。 |
| [Cloud-ScPO: Hidden-State Geometry for Semi-Supervised Preference Optimization](http://arxiv.org/abs/2608.01014v1) | Liu, Y. et al. | 探索仅从模型内部表示而非外部奖励信号中推导偏好监督，减少了对人类标注或验证答案的依赖，为数学推理优化的数据瓶颈提供了新思路。 |
| [Toward Fine-Grained Forgetting: Attribute Unlearning for Multimodal LLMs](http://arxiv.org/abs/2608.01008v1) | Lin, J. et al. | 面向多模态大模型提出属性级细粒度遗忘方法，在去除敏感信息的同时保留通用能力，为隐私合规提供了更精确的技术路径。 |
| [DeBERTa-Sentinel: Toward Transparent and Trustworthy Detection of AI-Generated Text](http://arxiv.org/abs/2608.01046v1) | Rehman, M.Y. et al. | 改进了现有 Transformer 检测器的泛化能力，在跨模型、跨域的 AI 生成文本检测任务上表现更稳定，对遏制虚假信息传播具有实际意义。 |
| [CallScreenBench: Benchmarking On-Device Models as Phone Secretaries](http://arxiv.org/abs/2608.01033v1) | Ren, S. | 构建了首个评估端侧小模型作为"手机秘书"能力的基准，测试其在静音接听、意图理解等实际场景中的可用性。填补了端侧任务自动化评测空白。 |
| [Hierarchical Solomonoff Induction: An Unbounded Machine Learning Model](http://arxiv.org/abs/2608.01005v1) | Young, N. | 将 de Finetti 定理应用于 Solomonoff 归纳，构建理论上无界的序列预测模型，为 LLM 外推能力的理论基础提供了新的形式化框架。 |
| [One-Sided Quantile Coupling for Flow Matching](http://arxiv.org/abs/2608.00978v1) | Kim, J.-Y. et al. | 提出单侧分位数耦合策略用于流匹配训练，结构化配对显著改善生成质量与优化稳定性，为连续时间生成模型提供了新的采样调度方案。 |

---

### 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Control Under Compression: Reliability Frontiers for Tool-Using Agents](http://arxiv.org/abs/2608.01056v1) | Hou, Y. et al. | 研究工具使用智能体在压缩控制上下文后的可靠性边界，揭示了现有 prompt 压缩方法的性能极限，为 Agent 系统效率优化提供理论依据。 |
| [Don't Offer What Can't Be Done: Deterministic Executability Gating for LLM Skill Selection at Scale](http://arxiv.org/abs/2608.01050v1) | Ashkenazi, O. et al. | 提出三阶段确定性地可执行性门控管道，解决语义匹配但实际无法执行的技能选择问题，已在 Wix Helpmate 平台部署验证。 |
| [Search-GRT: Guided Retrieval Training of Search Agents to Optimize for Complex Question Answering](http://arxiv.org/abs/2608.00974v1) | Kumar, A. et al. | 通过引导检索训练优化搜索增强 LLM 在复杂多跳问答中的表现，提升子问题分解与多源信息综合能力。 |
| [PROGRESS: Coverage-guided RL to Train Search-augmented LLM Agent](http://arxiv.org/abs/2608.00969v1) | Paul, S. et al. | 引入覆盖率导向的强化学习训练搜索增强智能体，弥补纯结果奖励对搜索行为监督不足的缺陷，提升复杂查询分解能力。 |
| [TrajWiki: Source-Grounded Memory Trajectories for Long-Horizon Dialogue Agents](http://arxiv.org/abs/2608.00967v1) | Sun, J. et al. | 提出基于来源的可追溯记忆轨迹方案，解决长期对话中记忆不可更新、不可诊断的问题，增强 Agent 记忆系统的透明度。 |
| [PMMC: Prospective Multimodal Memory Compilation for Long-Term LVLM Agents](http://arxiv.org/abs/2608.00962v1) | Sun, J. et al. | 面向长程多模态交互，提出前瞻性记忆编译机制，避免将视觉体验过度压缩为文本摘要，保留更多信息完整性。 |
| [What Could the Agent See at 19:05? Generating Temporal Enterprise Scenarios from Real Research and Replaying Them to Evaluate Agents](http://arxiv.org/abs/2608.01042v1) | Sahu, T. et al. | 从真实研究生成带时间维度的企业级场景进行 Agent 回放评估，突破静态快照评估的局限，更贴合实际动态数据环境。 |

---

### 🔧 方法与框架（新技术、基准测试、效率优化）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [WAM-Diff2: Hierarchical AR-to-Diffusion Distillation for Highly Efficient Autonomous Driving VLA](http://arxiv.org/abs/2608.01035v1) | Zhu, Z. et al. | 通过层次化自回归到扩散模型的蒸馏，显著降低 VLA 推理延迟并缓解暴露偏差，为自动驾驶端到端部署提供高效方案。 |
| [VLAGuard: A Framework for Evaluating and Mitigating Physical Attention Hijacking in Vision-Language-Action Robots](http://arxiv.org/abs/2608.01028v1) | Yin, D. et al. | 针对无线传感器网络中 VLA 机器人的物理对抗威胁，提出评估与缓解策略，保护关键动作-视觉注意力机制。 |
| [Caliber: Cross-Architecture Extraction-Cost Control for Score-Returning APIs](http://arxiv.org/abs/2608.01023v1) | Wang, C. et al. | 将噪声选择表述为校准问题，以可证明的查询成本对抗模型提取攻击，在保护 API 安全的同时保持监督信号质量。 |
| [SCHEDBench: A Benchmark for Evaluating LLM Constraint Faithfulness in Natural-Language Combinatorial Scheduling](http://arxiv.org/abs/2608.00991v1) | Sharma, S.S. et al. | 构建面向自然语言组合调度的基准，评估 LLM 在约束忠实性上的表现，为调度任务评估提供标准化方案。 |
| [Entity-Faithful Repair of Synthetic Supervision for Zero-Shot Image Captioning](http://arxiv.org/abs/2608.00994v1) | Liu, Z. et al. | 针对零样本图像描述中合成数据实体偏差问题提出修复方法，提升无标注场景下的描述质量。 |
| [FactorJEPA: Factorizing Monolithic Futures into Layout-Agent-Interaction Channels for Crowded Urban Worlds](http://arxiv.org/abs/2608.01049v1) | Wanaskar, K. et al. | 将 JEPA 世界模型因子化为布局-智能体-交互三通道，应用于人口稠密的南亚城市环境建模，填补了混乱环境下的研究空白。 |
| [Stress-Relief Annealing: Polynomial-Time Simulation-Free Layout Optimization for Automated Warehouses](http://arxiv.org/abs/2608.01024v1) | Luo, X. et al. | 提出无需仿真的多项式时间布局优化方法，大幅加速自动化仓库中数百至数千机器人的调度优化。 |

---

### 📊 应用（垂直领域、多模态、代码生成）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Why LLMs Give In: Conversational Factors and Reasoning Behind Medical Sycophancy](http://arxiv.org/abs/2608.01017v1) | Ping, K. et al. | 深入分析医疗领域 LLM 顺从行为（sycophancy）的对话因素与推理机制，揭示模型放弃正确答案的内在原因，对医疗 AI 安全至关重要。 |
| [MedUPS: Towards Diagnostic Assistance in Uncommon Medical Cases with Large Language Models](http://arxiv.org/abs/2608.01012v1) | Ben Shoham, O. et al. | 针对罕见病例和偏离指南场景构建诊断辅助框架，关注诊断不确定性下的系列决策支持，优于仅评估最终诊断的传统基准。 |
| [Credit the Right Box: Marginal Contribution Assignment for Structured Visual Perception](http://arxiv.org/abs/2608.01055v1) | Han, X. et al. | 提出边际贡献分配方案，解决多模态大模型在结构化感知任务中的视觉识别、语言绑定与定位精度问题。 |
| [Fused Bayesian Flow Networks for Dual-Target Molecular Design](http://arxiv.org/abs/2608.01007v1) | Zhou, J. et al. | 融合贝叶斯流网络用于双靶点药物设计，生成同时作用于两种靶蛋白的 3D 分子，为多药理学化合物发现提供新工具。 |
| [Decoy Images Amplify Caption-Mediated Defenses Against Encoded Jailbreaks](http://arxiv.org/abs/2608.01043v1) | Zhang, H. et al. | 发现无关诱饵图片可显著降低编码越狱攻击成功率，这一反直觉发现为视觉-语言模型的防御策略提供了新思路。 |

---

## 研究趋势信号

今日投稿中，**端侧部署与效率优化**持续升温，Opt.Gear、CallScreenBench、WAM-Diff2 等工作均聚焦于降低推理成本与延迟。同时，**智能体记忆系统**成为新兴热点，TrajWiki 与 PMMC 从可追溯性、信息保真度等角度重新思考长期交互中的记忆管理。此外，**防御与对齐**议题呈现多元化：除传统的文本检测外，VLAGuard 和 Caliber 分别从物理对抗与模型提取两个新维度构建了防御框架，表明 AI 安全研究正从内容层面向系统层面扩展。

---

## 值得精读

1. **[Don't Offer What Can't Be Done](http://arxiv.org/abs/2608.01050v1)** — 该工作直面生产环境中智能体技能选择的核心痛点：语义匹配不等于可执行。其三阶段管道已在 Wix 平台落地，兼具理论严谨性与工程实用性，对智能体系统开发者具有重要参考价值。

2. **[TrajWiki](http://arxiv.org/abs/2608.00967v1)** — 长期对话 Agent 的记忆问题长期被忽视，该论文从来源可追溯性、可更新性和诊断透明度三个维度系统性地重构了记忆设计，为构建可信的长程交互 Agent 提供了完整的思路框架。

3. **[Why LLMs Give In](http://arxiv.org/abs/2608.01017v1)** — 医疗顺从性（sycophancy）是极具危害的对齐缺陷，该研究不仅报告了现象，更深入分析了对话因素与推理机制，对理解 LLM 在高风险场景下的行为边界具有重要启示。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*