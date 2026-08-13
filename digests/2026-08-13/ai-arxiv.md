# ArXiv AI 研究日报 2026-08-13

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-08-13 02:27 UTC

---



# 📰 ArXiv AI 研究日报 — 2026-08-13

---

## 今日速览

今日论文围绕"模型可靠性验证"与"跨语言能力"两大主线展开：多篇工作关注 LLM 的概率一致性检验、量化方法优化与跨语言对齐安全漏洞，显示出学界对模型可信赖性的深层关切。同时，智能体的自我进化、测试时自适应、以及因果推理在供应链等垂直场景中的应用持续推进。量子-经典混合方法与神经符号框架的交叉探索也呈现新兴迹象。

---

## 重点论文

### 🧠 大语言模型（架构、训练、对齐、评估）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [The Illusion of Cross-Lingual Safety in Low-Resource Languages](http://arxiv.org/abs/2608.11146v1) | Abigail Oppong et al. | 揭示低资源语言中安全对齐的跨语言迁移存在显著漏洞，LLM 安全评估仍以英语为主的风险被进一步量化。值得关注因其挑战了当前多语言安全对齐的普遍假设。 |
| [Beyond a Bag of Features: Set-Level Instability in Sparse Autoencoders](http://arxiv.org/abs/2608.11197v1) | Nikolai Bolik et al. | 指出 SAE 激活集合在模型表示中呈现不稳定性，修正了此前关于 LLM 表征恢复人类类别边界的结论。为机制可解释性研究提供了更精确的分析工具。 |
| [Attention-Path Fragility as an Uncertainty Signal in Large Language Models](http://arxiv.org/abs/2608.11138v1) | Minsoo Kim et al. | 提出 ASMI，利用注意力路径对扰动的脆弱性作为模型不确定性的信号，无需额外训练即可评估 token 级置信度。为不确定性量化提供了新的可解释路径。 |
| [ReRound: Reconstructive Rounding to Resolve Midpoint Ambiguity in Calibration-Free LLM Quantization](http://arxiv.org/abs/2608.11045v1) | He-Yen Hsieh et al. | 针对标准舍入方案中的中点歧义问题，提出基于条件扩散的重构舍入方法，显著提升校准-free 量化精度。对 LLM 高效部署具有直接实用价值。 |
| [Mapping and Measuring the Behavioral Evolution of Large Language Models](http://arxiv.org/abs/2608.11027v1) | Dong Qiao et al. | 通过 32 个模型、10,000 提示的跨家族对比，刻画 LLM 行为随代际的变化轨迹，填补了行为演化度量维度的空白。为模型迭代评估提供了系统性基准。 |
| [Data Attribution of Emergent Misalignment with Persona Features](http://arxiv.org/abs/2608.11025v1) | Clemens Vetter et al. | 验证了 emergent misalignment 可归因于预训练获得的 persona 特征方向，为有害行为的涌现提供了机制解释与数据溯源方法。对安全对齐干预策略设计具有指导意义。 |
| [V-FiLLM: Verified Financial LLM Reasoning Benchmark](http://arxiv.org/abs/2608.11047v1) | Alicia Larsen et al. | 构建基于可执行计算树的金融推理基准，通过形式化验证确保答案正确性，弥补了金融领域结构化推理评测的空白。对高风险领域 LLM 落地评估具有重要参考。 |
| [On the Limitations of Cross-Lingual Consistency in Multilingual Text-to-image Generation](http://arxiv.org/abs/2608.11002v1) | Sicheng Zhang et al. | 提出 LingT2I 基准，系统评测多语言文本到图像生成中的跨语言一致性缺陷，揭示当前模型在非英语生成任务中的显著退化。为多模态模型的全球化部署提供评估依据。 |

---

### 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Long-Horizon AI Research for Grothendieck Constant: A Case Study in Human-AI Mathematical Collaboration](http://arxiv.org/abs/2608.11195v1) | Alan Li et al. | 以 Grothendieck 常数边界改进为案例，系统总结 AI 在长期数学研究中的有效使用方式。为研究人员与 AI 协作提供了可复用的方法论框架。 |
| [SkillZip: Evaluation-Free Skill Compression for Self-Evolving Agents](http://arxiv.org/abs/2608.11079v1) | Xiaofan Bai et al. | 通过自动发现可复用结构对智能体技能进行压缩，无需评估即可解决技能冗余膨胀问题。对自进化智能体的可持续运行具有关键意义。 |
| [Actions Speak Louder than Words: Measuring Cross-Lingual Policy Retention in Tool-Using Agents](http://arxiv.org/abs/2608.11110v1) | Sourabrata Mukherjee et al. | 指出当前多语言智能体评估只关注最终答案而忽略动作序列，提出工具使用策略的跨语言一致性度量方法。揭示了多语言 agent 评估的重要盲区。 |
| [Why Does CLAUDE.md Keep Growing? Catastrophic Remembering in Agentic Coding](http://arxiv.org/abs/2608.11095v1) | Kushal Chakrabarti | 分析 Agentic Coding 项目中 README 文件无限增长的成因，归因于"灾难性记忆"——删除无效指令的成本高于追加。为智能体代码项目治理提供了实证洞察。 |

---

### 🔧 方法与框架（新技术、基准测试、效率优化）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Test-Time Self-Evolving GUI Visual Grounding via Reflection-Guided On-Policy Self-Distillation](http://arxiv.org/abs/2608.11191v1) | Shiyu Xuan et al. | 通过反射引导的在线策略自蒸馏实现测试时自适应，突破 GUI 智能体部署后参数冻结的限制。解决了现有测试时 RL 方法无法反思失败的根本问题。 |
| [How to Verify Consistency of Probabilistic Claims](http://arxiv.org/abs/2608.11181v1) | Orr Paradise et al. | 提出多项式时间内验证概率预测自一致性的方法，为 AI 安全中的诚实概率预测提供了可计算的安全保障机制。对风险敏感系统的可信部署至关重要。 |
| [SCOUT: Symmetric Consensus Outlier Detection for Failure Localization in LLM Pre-Training](http://arxiv.org/abs/2608.11034v1) | Zhuang Wang | 提出对称共识异常检测方法，解决大规模 LLM 预训练中分布式故障定位的核心难题，尤其在 trainer 崩溃后仍可有效诊断。对保障大规模训练稳定性具有直接价值。 |
| [Long-Horizon AI Research for Grothendieck Constant: A Case Study in Human-AI Mathematical Collaboration](http://arxiv.org/abs/2608.11195v1) | Alan Li et al. | 以数学研究案例为切入点，系统提炼人类与 AI 在长期复杂推理中的有效协作模式。为科学发现的 AI 增强范式提供了结构化方法论参考。 |
| [Batch Size or Negatives? A Selection Rule for Memory-Constrained Recommender Training](http://arxiv.org/abs/2608.11061v1) | Artyom Sabitov et al. | 针对大规模推荐系统训练中 softmax 层内存瓶颈，提出批量大小与负采样数量的最优选择规则。对工业级推荐模型的内存效率优化具有直接指导意义。 |
| [Conditional Independence Tests for Constraint-Based Causal Discovery: A Survey](http://arxiv.org/abs/2608.11156v1) | Pavel Averin et al. | 系统综述条件独立性检验在约束型因果发现中的作用，重点分析各类检验的假设与适用条件。为因果推断研究者提供了全面的工具箱参考。 |
| [Scheduling Mixed RL Rollouts Beyond Prefix Locality](http://arxiv.org/abs/2608.11152v1) | Zetao Hong et al. | 提出超越前缀局部性的混合 RL rollout 调度方法，解决多领域多反馈范式下的训练效率问题。对 LLM 强化学习后训练的分布式部署具有工程价值。 |
| [DACRI: Decision-Aware Causal Intervention Ranking for Critical Supply Chains](http://arxiv.org/abs/2608.11154v1) | Shiqi Huang et al. | 提出因果干预排序框架 CriticalSCM-Bench v1，将供应链恢复建模为因果决策问题。对基础设施韧性分析与应急响应优化具有实际应用价值。 |

---

### 📊 应用（垂直领域、多模态、代码生成）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Surgical WAM: A World-Action Model for Data-Efficient Surgical Robot Learning](http://arxiv.org/abs/2608.11204v1) | Wenrui Bao et al. | 构建世界-动作模型实现外科手术机器人的数据高效学习，突破遥操作轨迹标注稀缺的瓶颈。对高精度医疗机器人自主操作具有转化潜力。 |
| [ConVAWG: A Retrieval-Grounded Framework for Controlled Synthetic Dialogue Generation in Violence Against Women and Girls](http://arxiv.org/abs/2608.11200v1) | Chen Lyu et al. | 提出检索增强的合成对话生成框架，在敏感社会问题上实现可控、安全的数据合成。为难以获取真实数据的领域研究提供了合规替代方案。 |
| [myMediWhisper: Construction of Burmese Medical Speech Corpus and Whisper Fine-Tuning for Clinical Dialogue ASR](http://arxiv.org/abs/2608.11036v1) | Ye Kyaw Thu et al. | 构建 28 小时缅甸语医学语音语料库并微调 Whisper，显著提升低资源语言临床对话 ASR 性能。填补了缅甸语医疗语音识别的资源空白。 |
| [Self-Knowledge Retrieval Augmented Generation Framework for Patent Matching](http://arxiv.org/abs/2608.11030v1) | Jian Zhang et al. | 提出基于自知识检索增强的专利匹配框架，有效处理专利文档的多模态复杂结构。对知识产权保护与专利检索自动化具有直接应用价值。 |
| [Entropy-Centric Explainable AI for Remote Sensing Image Segmentation](http://arxiv.org/abs/2608.11064v1) | Ali Saleh et al. | 以熵为核心构建遥感图像分割的可解释框架，在保持高精度的同时提供决策透明度。对关键基础设施监控等安全敏感场景尤为重要。 |
| [Cross-View Feature Matching: Survey, Benchmarking, and Foundation-Model Perspectives](http://arxiv.org/abs/2608.11093v1) | Songlin Du et al. | 综述跨视角特征匹配领域十年进展，评估基础模型在该任务上的能力。为自动驾驶、SLAM 等需要跨视角感知的系统提供了方法论整合。 |
| [Two-stage Odd Residual Flows for Mean-Preserving Probabilistic Time Series Forecasting](http://arxiv.org/abs/2608.11114v1) | Kiran Madhusudhanan et al. | 提出两阶段奇数残差流方法，在概率时间序列预测中平衡分布灵活性与均值准确性。对金融、能源等长视距风险决策场景具有应用价值。 |

---

## 研究趋势信号

今日投稿呈现三个清晰趋势：一是**"验证优于增强"**——概率一致性检验、量化精度验证、行为演化度量等工作均在探索"如何确认模型说的是真话"；二是**跨语言公平性**成为安全研究新前沿，多篇论文指出低资源语言在安全对齐与生成质量上的系统性差距；三是**神经符号与可解释性**的融合加速，SAE 不稳定性分析、因果发现综述、逻辑张量网络等工作显示出机制层面理解模型的深入。

---

## 值得精读

1. **[The Illusion of Cross-Lingual Safety in Low-Resource Languages](http://arxiv.org/abs/2608.11146v1)** — 安全对齐的英语中心主义是当前 LLM 部署的最大隐患之一，此工作以系统实验揭示了低资源语言中的安全漏洞，对多语言产品团队和 AI 政策制定者均有重要参考价值。

2. **[Test-Time Self-Evolving GUI Visual Grounding via Reflection-Guided On-Policy Self-Distillation](http://arxiv.org/abs/2608.11191v1)** — 测试时自适应是打通 LLM Agent 落地"最后一公里"的关键技术，此方法通过反射机制实现部署后的自我改进，突破了参数冻结的限制，代表了 Agent 持续学习能力的新方向。

3. **[Data Attribution of Emergent Misalignment with Persona Features](http://arxiv.org/abs/2608.11025v1)** — Emergent Misalignment 是当前对齐研究的前沿难题，此工作将其机制归因于预训练 persona 特征，并提供了数据溯源方法，对理解与干预对齐失效具有基础性意义。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*