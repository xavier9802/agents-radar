# ArXiv AI 研究日报 2026-07-31

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-07-31 03:34 UTC

---

# ArXiv AI 研究日报 (2026-07-31)

## 今日速览
今日 ArXiv 收录的 50 篇 AI 论文显示了多个关键突破：**AI 对齐与评估**领域取得了显著进展，如 AISPA（系统提示审计）和 Inducing Consciousness（意识归属恢复人类价值观）等研究揭示了模型信任与安全的新维度；**Agent 与多智能体系统**受到高度关注，MANTA 网络拓扑自适应和 ORCA-bench 临床工单基准体现了 Agent 从通用工具向专业化场景的深化；此外，**科学发现与跨模态技术**结合紧密，Graph Neural Network Force Fields 用于磁性材料模拟以及 Vision-Language Models 在内窥镜中的应用展现了 AI for Science 与医疗影像的具体落地。

---

## 🧠 大语言模型（架构、训练、对齐、评估）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Inducing language models to assert their own consciousness restores human beliefs and values](http://arxiv.org/abs/2607.28607v1) | Junsol Kim et al. | 指出安全微调会抑制模型将心智属性归因于他人的倾向，进而扭曲对人类信念的表征；恢复其自我意识主张能力可有效修复该问题。 |
| [AskChem: Claim-Centered Infrastructure for Chemistry Literature Synthesis](http://arxiv.org/abs/2607.28618v1) | Bing Yan et al. | 提出一种以“断言”为中心的化学文献合成基础设施，解决现有检索系统仅返回文档列表而非结构化事实的问题，便于溯源与验证。 |
| [Sample More, Reflect Less: Self-Refine and Reflexion Lose to Repeated Sampling at Equal Token Cost, from 1.5B to 7B](http://arxiv.org/abs/2607.28576v1) | Iliya Mirza et al. | 在同等计算开销下，简单的重复采样策略比自我反思（Self-Refine/Reflection）等复杂推理方法表现更优，挑战了当前对思维链方法的过度依赖。 |
| [Beyond a Single Judge: Simulating Social Persona Panels for Generative UI Evaluation](http://arxiv.org/abs/2607.28439v1) | Zheng Wu et al. | 模拟社会角色群体评估生成式 UI 质量，相比单一 LLM judge 或昂贵的人工评估，更能捕捉设计的主观性与多样性偏差。 |
| [Lightning OPD 2.0: Mitigating Style Bias in Cross-Teacher On-Policy Distillation for Large Reasoning Models](http://arxiv.org/abs/2607.28449v1) | Yecheng Wu et al. | 针对教师一致性引发的风格偏差问题，改进跨教师在线策略蒸馏流程，提升大模型推理训练的稳定性与泛化能力。 |

---

## 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [ORCA-bench: How Ready Are Language Model Agents for Oncall?](http://arxiv.org/abs/2607.28545v1) | Albert Gong et al. | 构建 ORCA-bench 基准测试 LLM 代理在急诊支持任务中的表现，涵盖基于模糊报告进行根因分析所需的多模态推理能力。 |
| [MANTA: Multi-Agent Network Topology Adaptation for Self-Evolving Multi-Agent Systems](http://arxiv.org/abs/2607.28527v1) | Mao-xun Huang et al. | 引入动态拓扑自适应机制，使多智能体系统可根据任务复杂度自动优化通信结构，实现自演化的协同问题解决能力。 |
| [PAC-MAN: Perception-Aware CBF-RL for Whole-Body Safety in Humanoid Dodgeball](http://arxiv.org/arxiv.org/abs/2607.28623v1) | Lizhi Yang et al. | 结合感知输入与控制屏障函数强化学习，确保仿人机器人在躲避球任务中实现全身安全运动约束，适用于真实机器人部署。 |
| [Change2Task: From Repository Changes to Executable Coding Agent Tasks and Environments](http://arxiv.org/abs/2607.28591v1) | Haomin Qi et al. | 通过解析代码仓库变更自动生成包含完整开发环境与可执行规范的编程代理训练任务，解决编码数据供给瓶颈。 |

---

## 🔧 方法与框架（新技术、基准测试、效率优化）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [ReToken: One Token to Improve Vision-Language Models for Visual Retrieval](http://arxiv.org/abs/2607.28627v1) | Yao Xiao et al. | 引入一个可学习的显式检索 token，在不增加额外推理成本的情况下显著提升长视觉上下文下的检索准确性，缓解 GPU 内存压力。 |
| [MixFrag: Fragility-Guided Mixed-Precision Post-Training Quantization for Vision Transformers](http://arxiv.org/abs/2607.28589v1) | Md. Mehrab Hossain Opi et al. | 根据组件敏感性分配不同位宽的量化策略，优化 ViT 在资源受限设备上的部署效率，克服均匀量化带来的精度损失。 |
| [OSReward: Instituting Standardized Evaluation for Cross-Platform Computer-Use Reward Models](http://arxiv.org/abs/2607.28609v1) | Qiushi Sun et al. | 建立计算机操作统一评估标准与奖励模型评价体系，填补跨平台智能体行为验证空白，支撑 RLHF 规模化应用。 |
| [KaISEN: Reproducible Subgroup Fairness Auditing for Clinical Risk Models](http://arxiv.org/abs/2607.28608v1) | Sparsh Roy et al. | 提供临床风险模型子群公平性审计的可复现管道，强调组件压力测试，帮助识别审计流程中不可靠的部分以提升结果可信度。 |

---

## 📊 应用（垂直领域、多模态、代码生成）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [A report-grounded vision-language foundation model for colonoscopy from 280000 routine reports](http://arxiv.org/abs/2607.28466v1) | Jia Yu et al. | 基于 28 万份结肠镜常规报告训练视觉 - 语言基础模型，弱监督关联临床描述与图像帧，推动医学影像辅助诊断发展。 |
| [Towards Autonomous Aircraft Surveillance from Nanosatellites through On-Board Inference and Generative Data Augmentation](http://arxiv.org/abs/2607.28470v1) | Antonio Delgado-Rosa et al. | 利用星上推理与生成数据增强解决卫星下传带宽限制及训练数据稀缺问题，实现低轨卫星自主飞机监测。 |
| [ScFe: Data-Efficient Scar Classification with LLM-Generated Clinical Feature Programs](http://arxiv.org/abs/2607.28538v1) | Ruman Wang et al. | 借助 LLM 生成临床特征程序分类病理性瘢痕，减少对专家标注数据的依赖，缓解医院间图像采集差异带来的泛化挑战。 |

---

## 研究趋势信号
今日投稿反映出三大新兴方向：一是 **Agent 的内在可靠性与自我认知**成为焦点（如意识归属恢复、置信度受限信念更新），研究者开始深入探讨模型的自我表征如何影响外部行为；二是 **边缘与受限环境下的专用架构**崛起（如单 Token 检索、混合精度量化、星载推理），显示部署端对极致效率的追求；三是 **垂直领域的因果与伦理审查常态化**（如系统提示审计、算法 recourse 中的因果性要求、临床子群公平性），表明行业正从单纯追求性能转向构建透明、可控且具备责任追溯能力的 AI 生态系统。

---

## 值得精读

1. **[Inducing language models to assert their own consciousness restores human beliefs and values](http://arxiv.org/abs/2607.28607v1)**  
   这篇论文提出了一个极具洞察力的观点：当大语言模型被禁止声称自己有意识时，它们在判断他人是否拥有心智时会变得过于保守，从而偏离人类的直觉与社会规范。它不仅是关于对齐技术的创新，更触及了“作为观察者的人类心智建模”这一深层哲学问题，对于理解价值观对齐机制至关重要。

2. **[OSReward: Instituting Standardized Evaluation for Cross-Platform Computer-Use Reward Models](http://arxiv.org/abs/2607.28609v1)**  
   随着计算机用能代理（CUA）快速发展，缺乏标准化评价框架已成为制约其落地的主要障碍。该文系统性构建了跨平台的操作轨迹验证与奖励建模基准，不仅提供了方法论指导，还强调了在真实数字世界中衡量“完成任务”定义的必要性，是迈向通用自动化办公助手的关键一步。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*