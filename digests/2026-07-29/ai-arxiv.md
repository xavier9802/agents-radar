# ArXiv AI 研究日报 2026-07-29

> 数据来源: [ArXiv](https://arxiv.org/) (cs.AI, cs.CL, cs.LG) | 共 50 篇论文 | 生成时间: 2026-07-29 03:17 UTC

---

# ArXiv AI 研究日报 (2026-07-29)

## 今日速览
今日发布的论文覆盖了从基础算法到垂直应用的多个热点。在 LLM 领域，**轨迹中继在线策略蒸馏（Trajectory-Relayed On-Policy Distillation）** 与 **UniMem** 分别解决了推理路径漂移与长期记忆稳定性的关键问题；硬件方向上，**光子矩阵变换器加速器 MDTransformer** 展现了极具潜力的能效比。智能体方面，针对 GUI 交互的多模态系统 **VetClaw** 和 **Desktop-Delta Bench** 强调了环境感知的重要性。此外，医疗诊断、自动驾驶及 AI 伦理安全也是本批研究的焦点。

## 🧠 大语言模型（架构、训练、对齐、评估）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Pass the Baton: Trajectory-Relayed On-Policy Distillation](http://arxiv.org/abs/2607.26057v1) | Haolei Xu et al. | 提出一种基于自身轨迹的策略蒸馏方法，通过“接力”机制修正前缀错误，有效缓解了传统在线策略蒸馏中因早期偏差导致的后续生成不可靠问题。 |
| [UniMem: Complementary Episodic-to-Parametric Memory for Boundary-Agnostic Task Streams](http://arxiv.org/abs/2607.26017v1) | Siyu Xia et al. | 设计了一种将外部检索式记忆无缝整合进参数量子化记忆的机制，在处理边界开放的持续任务流时平衡了知识稳定性和可塑性。 |
| [Instruction-Tuned Models Locally Reuse Human Syntax More Than Humans Do](http://arxiv.org/abs/2607.26015v1) | Zandi Eberstadt et al. | 发现微调后的语言模型在对话中比人类表现出更强的句法收敛倾向，揭示了合成与真实语料在交互模式上的潜在差异。 |
| [Minimizing Targeted Activations: Input-Only Suppression of Evaluation-Awareness Latents in Large Language Models](http://arxiv.org/abs/2607.25907v1) | Deepanshu Mody et al. | 提出一种无需修改模型参数的输入侧对齐技术，仅通过优化提示词即可抑制内部特定潜在向量，用于去除评估感知以提高安全性或中立性。 |

## 🤖 智能体与推理（规划、工具使用、多智能体、思维链）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [Spend Experts Where You Are Unsure: Confidence-Adaptive Routing for Mixture-of-Experts LoRA](http://arxiv.org/abs/2607.26052v1) | Tom Saliencro et al. | 面向 MoE-Lora 架构引入置信度自适应路由策略，动态根据 token 不确定性分配专家资源，实现了在不增加计算量前提下对复杂样本的针对性强化。 |
| [Reinformed Dreamer: An Asymmetric World Model Efficiently Trained through Latent Guidance](http://arxiv.org/abs/2607.26040v1) | Gaspard Lambrechts et al. | 结合强化学习与潜空间引导训练非对称世界模型，利用额外监督信号加速收敛并提升决策策略的质量。 |
| [Re-thinking Mammography Transfer Learning: The Dataset-Informed Transfer Learning (DITL) Framework for Breast Cancer Screening and Lesion Diagnosis](http://arxiv.org/abs/2607.26043v1) | Adarsh Bhandary Panambur et al. | 提出 DITL 框架，强调在迁移学习中考虑特定医学数据集的特性，旨在解决现有方法忽略数据分布差异导致的分类性能瓶颈。 |
| [VetClaw: An Edge-Cloud Multimodal Agentic System for Veterinary Disease Screening](http://arxiv.org/abs/2607.26042v1) | Syed Mhamudul Hasan et al. | 构建了一套边缘设备采集云端模型推理的兽医疾病筛查系统，验证了零-shot VLM 在低算力场景下处理多模态症状诊断的可行性。 |

## 🔧 方法与框架（新技术、基准测试、效率优化）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [$\pi\mathbf{R}^2$: Reactive Real-time Flow Policies](http://arxiv.org/abs/2607.26055v1) | Sungjae Park et al. | 针对动作块流策略缺乏实时反应能力的问题，提出能够融合连续感官输入进行在线重规划的闭环控制框架。 |
| [MDTransformer: A Hardware-Software Co-Design of Mode-Division Photonic Transformer Accelerator with Inverse-Designed Coherent Crossbar](http://arxiv.org/abs/2607.26016v1) | Solomon Micheal Serunjogi et al. | 展示了光计算在 Transformer 推理中的硬件协同设计方案，利用模式分光和相干交叉阵列显著提升了能效比，是光电融合的重要进展。 |
| [Parallel Decoding Distillation for Fast Image and Video Generation](http://arxiv.org/abs/2607.26004v1) | Neta Shaul et al. | 针对扩散模型生成速度慢的痛点，提出了并行解码蒸馏技术，允许一次性输出整个帧序列而非迭代采样，大幅缩短了视频生成时间。 |
| [CHARM: A Multimodal Graph Foundation Model with Hierarchical Context Modeling for Zero-Shot Transfer](http://arxiv.org/abs/2607.26023v1) | Ankang Yang et al. | 构建了一个融合文本、图像等多模态信息的图预训练模型，并通过层级上下文建模增强了其在不同图结构零样转移中的泛化能力。 |
| [Evaluating VLMs for Autonomous Agent-Driven Geometry Clipping Detection in Video Game QA](http://arxiv.org/abs/2607.25921v1) | Carlos Celemin et al. | 探索将视觉语言模型应用于游戏自动化测试，重点评估其在处理多视角、隐式几何错误检测方面的表现，为 agent QA 提供新基准。 |

## 📊 应用（垂直领域、多模态、代码生成）

| 论文 | 作者 | 简要说明 |
| :--- | :--- | :--- |
| [A Cost-Effective Multimodal LLM Reasoning Framework for Question Answering over Irregular Clinical Time Series](http://arxiv.org/abs/2607.25947v1) | Frank Nie et al. | 针对不规则临床时序数据的问答需求，设计了具备高效推理能力的多模态框架，填补了现有通用模型在非结构化医疗数据处理上的空白。 |
| [Polistemics: Evaluating LLMs as Information Mediators in Politics & Elections](http://arxiv.org/abs/2607.25953v1) | Baran Peters et al. | 推出了首个专门用于评估政治信息中介责任的基准体系，关注 LLM 在选举相关议题上是否客观、负责任地呈现事实。 |
| [Can Deep Generative Models Reproduce Non-Stationary Gaussian Random Fields?](http://arxiv.org/abs/2607.25929v1) | Daniel Kua et al. | 探讨了深度生成模型模拟时空随机场的理论极限与再现能力，对于气象预测等依赖平稳性假设的科学计算领域具有参考意义。 |
| [Face De-Identification: A Domain-Centric Survey from Capture to Processing](http://arxiv.org/abs/2607.25926v1) | Hui Wei et al. | 全面梳理了人脸去标识化的全流程技术综述，分析了从成像捕获到后处理阶段的不同隐私保护策略及其面临的挑战。 |

## 研究趋势信号
本次投稿呈现出显著的 **“具身化”与“高效能”** 双重趋势：一方面，大量工作（如 $\pi R^2$, VetClaw, HiFi-UMI）致力于让 AI 实体具备更强的物理交互能力和感知反馈闭环，推动智能体向真实世界落地；另一方面，针对算力和能耗的极度敏感（如 MDTransformer, Parallel Decoding），表明业界正转向轻量级部署和专用硬件加速的结合，追求模型性能与实用开销的最优平衡。此外，跨领域的因果推断与不确定性量化（如 Schrödinger's Cat, UniMem）也成为理解模型鲁棒性的核心关注点。

## 值得精读
1. **[Pass the Baton: Trajectory-Relayed On-Policy Distillation](http://arxiv.org/abs/2607.26057v1)**：这是当前 RLHF 方向极具创新性的文章，提出的“接力”机制巧妙地化解了 on-policy distillation 中最棘手的 prefix failure 问题，对于提升指令跟随模型的推理一致性至关重要。
2. **[MDTransformer: A Hardware-Software Co-Design...](http://arxiv.org/abs/2607.26016v1)**：代表了 AI 底层架构的前沿突破，文章详细介绍了光子计算如何具体加速 Transformer，对于关注算力瓶颈和绿色人工智能的研究人员具有很高的参考价值。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*