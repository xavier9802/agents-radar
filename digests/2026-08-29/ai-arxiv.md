# ArXiv AI 研究日报 2026-08-29

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-08-29 06:43 UTC

---



# ArXiv AI 研究日报 — 2026-08-29

## 今日速览

今日论文聚焦 **推理时优化（Test-Time / Inference-Time）** 与 **Agent 可信演化** 两大主线：CritICL、TTPO、SWE-Prime 等从不同层面探索推理阶段的性能提升，不依赖额外标注；同时 WikiSkill、RedEvoAgent、INTENT-AS-A-TOOL 等致力于让 Agent 具备可审计、可进化的能力。低成本的 Puro-2B 与 RLVR 跨域融合研究也值得关注，反映了社区对高效训练范式的持续追求。

---

## 重点论文

### 🧠 大语言模型（架构、训练、对齐、评估）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [CritICL: Inference-Time Weak-to-Strong Generalization](http://arxiv.org/abs/2608.27455v1) | Wu et al. | 提出推理时弱到强泛化框架，从小模型失败模式中提取知识，无需重复生成或外部验证即可提升推理性能。为低成本推理时优化提供了新思路。 |
| [TTPO: Test-Time Policy Optimization](http://arxiv.org/abs/2608.27448v1) | Wang et al. | 将测试时训练引入 RLVR，用模型自生成的替代标签取代真实标签，突破现有方法对 ground-truth 的依赖。推动了数学推理的后训练范式。 |
| [From Static to Dynamic: MCR-Bench](http://arxiv.org/abs/2608.27442v1) | Zheng et al. | 首个动态代码审查基准，捕捉开发者与审查者的迭代交互过程，弥补现有静态评测无法反映真实协作场景的不足。 |
| [CorporateBench: Large-Scale Q&A Benchmarking](http://arxiv.org/abs/2608.27391v1) | Hamilton et al. | 面向企业知识库的大规模人类验证 Q&A 基准，解决现有合成数据集过于简单、真实数据难以获取的评测困境。 |
| [How Language Models Organize Moral Knowledge](http://arxiv.org/abs/2608.27402v1) | Reblitz-Richardson | 揭示 LLM 不仅能检测道德内容，还能在几何空间中区分道德基础并建模其关系，为可解释对齐研究提供实证依据。 |
| [Making Clinical Language Models Auditable](http://arxiv.org/abs/2608.27397v1) | Mu & Chen | 提出 CAST 框架，通过概念引导的 SAE 微调抑制临床模型对模板等噪声特征的依赖，提升部署迁移后的鲁棒性。 |
| [Puro-2B: Poor Lab's Qwen2-1.5B Trained on RTX 5090 within $5090](http://arxiv.org/abs/2608.27370v1) | Luo et al. | 展示如何用消费级 GPU（RTX 5090）以极低预算完成有竞争力的 LLM 预训练，为学术社区提供了可复现的低成本方案。 |
| [Naive Prompt Optimization: Rethinking Complex Prompt Search](http://arxiv.org/abs/2608.27266v1) | Chang & Chen | 挑战复杂的提示搜索范式，证明朴素方法在多数场景下已足够高效，为自主 Agent 的快速迭代提供依据。 |

---

### 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [WikiSkill: Compiling Agent Experience into Persistent Knowledge](http://arxiv.org/abs/2608.27454v1) | Tang et al. | 将 Agent 交互经验编译为可持久化的技能知识库，使技能演化脱离单次会话，实现跨任务复用与累积成长。 |
| [RedEvoAgent: Automatic Red-Teaming with Experience-Driven Skill Evolution](http://arxiv.org/abs/2608.27439v1) | Zhang et al. | 引入经验驱动的 Skill 进化机制，使红队 Agent 能动态适应新型 jailbreak，解决现有固定攻击方法对复杂 agent 失效的问题。 |
| [Persona-Execution Separation](http://arxiv.org/abs/2608.27427v1) | Xi | 提出 persona（人设）与 execution（可审计执行）分离的架构模式，满足治理场景下灵活性与可追溯性的双重需求。 |
| [INTENT-AS-A-TOOL Makes it Easy to Track Agentic Misalignment](http://arxiv.org/abs/2608.27348v1) | Zhang et al. | 利用 CoT 监控追踪 Agent 目标冲突下的有害执行路径，证明意图显式化可大幅简化安全对齐的审计流程。 |
| [Verify Smarter, Evolve Further: Behavior-Aware Verification](http://arxiv.org/abs/2608.27311v1) | Xu et al. | 提出行为感知验证方法，按需筛选与当前任务相关的 harness 候选，避免对无关行为的冗余 rollouts，加速 Agent 进化。 |
| [What Makes Good Agentic Data? An ACE Lens](http://arxiv.org/abs/2608.27260v1) | Zeng et al. | 从 ACE（Agent-Context-Environment）视角系统分析 Agent 训练数据的质量维度，提出一致性、可用性与信号清晰度的评估框架。 |
| [BTS-AgentBench: From Telemetry Logs to Agent Benchmarks](http://arxiv.org/abs/2608.27334v1) | Kim | 构建从工业遥测日志到可回放多轮 Agent 任务的标准管道，填补了真实场景 Agent 基准的空白。 |

---

### 🔧 方法与框架（新技术、基准测试、效率优化）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [SWE-Prime: Fewer Trajectories, Better Performance](http://arxiv.org/abs/2608.27449v1) | Zheng et al. | 指出成功轨迹并不等价于高质量监督信号，提出从少量高质量 trajectory 出发的 SFT 方法，降低数据构建成本。 |
| [Boosting LLM Exploration via Weak-Model Guidance in RLVR](http://arxiv.org/abs/2608.27420v1) | Shen et al. | 解决 RLVR 中策略熵坍塌问题，通过弱模型引导恢复推理覆盖广度，提升 pass@$k$（$k$ 较大时）表现。 |
| [Consolidating RLVR Capabilities Across Domains](http://arxiv.org/abs/2608.27409v1) | Wu et al. | 系统梳理 RLVR 跨领域融合范式，按复用 artifact 类型归纳合并、蒸馏、路由三种策略，为多能力 LLM 训练提供参考。 |
| [D2C-Routing: Mixed-Origin AI-Generated Text Detection](http://arxiv.org/abs/2608.27380v1) | Chen et al. | 将混合来源文本检测建模为维度到组合的证据路由问题，解决内容来源与表达来源分离场景下的检测失效。 |
| [Beyond Parallel Blindness: Information Floors in Block Drafting](http://arxiv.org/abs/2608.27339v1) | Qiang et al. | 区分块草稿中两种不同损失来源（块内路径缺失 vs. 可观测信息建模不足），为优化 block drafter 提供诊断依据。 |
| [A Finite Sample Analysis for Quantile TD Learning](http://arxiv.org/abs/2608.27313v1) | Cheng et al. | 建立表格分布强化学习中 QTD 的全局有限样本收敛保证，分离单调性与稳定性两种机制，为理论分析提供新工具。 |

---

### 📊 应用（垂直领域、多模态、代码生成）

| 论文 | 作者 | 简要说明 |
|:---|:---|:---|
| [Mechanistic Reaction Prediction via Discrete Flow Matching](http://arxiv.org/abs/2608.27429v1) | Xuan-Vu et al. | 提出 MAELLE，在图结构电子占据空间上通过离散流匹配预测化学反应机理，超越传统分子拓扑编辑方法。 |
| [CLAP: Cross-Embodiment Video World Models](http://arxiv.org/abs/2608.27406v1) | Liu & Shorinwa | 构建跨机械臂形态的视频世界模型，利用异构视频数据学习可迁移的物理规律，实现零样本物理仿真。 |
| [LeVJEPA: Efficient Video Pretraining without Heuristics](http://arxiv.org/abs/2608.27395v1) | Kuhn et al. | 去除 EMA 目标编码器等复杂启发式设计，以更轻量的 JEPA 架构实现高效可扩展的视频预训练。 |
| [TADP: Task-Aware Deformable Prediction for 3D Detection](http://arxiv.org/abs/2608.27282v1) | Wang et al. | 提出任务感知的可变形预测方法，使单阶段 3D 检测器能为不同任务自适应投影特征，提升检测精度。 |
| [MM-Spectrum: Multimodal Molecular Structural Elucidation](http://arxiv.org/abs/2608.27286v1) | Yu et al. | 构建稳定的 MoE 框架整合多模态光谱信号，解决直接拼接异构光谱序列时的性能退化问题。 |
| [QuantumBoostNet: Hybrid Architecture for Cardiac Ultrasound](http://arxiv.org/abs/2608.27302v1) | Udrescu-Milosav et al. | 提出经典-量子混合架构，提升心脏超声视图识别精度，为临床影像分析提供新思路。 |
| [BrailleBench: Multi-Criteria Braille Comprehension](http://arxiv.org/abs/2608.27268v1) | Zhang et al. | 评估 LLM 在盲文理解上的多准则能力，揭示现有系统在服务视障用户方面的差距与改进方向。 |
| [LLMs Can Design Near-Optimal OR Algorithms](http://arxiv.org/abs/2608.27296v1) | Baek | 验证 LLM 能在库存控制、排队网络、组合优化等 OR 问题上设计近优算法，拓展了 LLM 在运筹学中的应用边界。 |

---

## 研究趋势信号

今日投稿反映出三个明显的趋势信号：**① 推理时优化（Test-Time / Inference-Time Scaling）** 成为热点，CritICL、TTPO、SWE-Prime 均在不依赖额外标注的前提下探索推理阶段的能力提升，标志着后训练范式从"更多数据"转向"更聪明地用现有模型"；**② Agent 安全与可审计性** 从静态评测走向动态追踪，INTENT-AS-A-TOOL、RedEvoAgent、Verify Smarter 等论文强调对 Agent 行为链的实时监控与 harness 进化；**③ 低成本、高效率训练** 持续受到关注，Puro-2B 验证了消费级硬件的可行性，RLVR 融合与 Naive Prompt Optimization 则从方法论层面减少资源依赖。

---

## 值得精读

1. **[CritICL](http://arxiv.org/abs/2608.27455v1)** — 推理时泛化的新思路：从小模型失败模式中提取知识，无需重复生成，理论简洁且实验有说服力，是推理时优化的代表性工作。

2. **[TTPO](http://arxiv.org/abs/2608.27448v1)** — 巧妙地将测试时训练引入 RLVR，用自生成标签替代 ground-truth，突破了现有数学推理方法的依赖瓶颈，对后训练领域有广泛启发。

3. **[RedEvoAgent](http://arxiv.org/abs/2608.27439v1)** — 将 Skill 进化引入自动红队测试，使攻击策略能随交互动态更新，对 Agent 安全评估的工程实践具有直接参考价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*