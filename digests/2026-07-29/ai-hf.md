# Hugging Face 热门模型日报 2026-07-29

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-29 03:17 UTC

---

# Hugging Face 热门模型日报（2026-07-29）

---

## 今日速览

**Kimi 家族与 Qwen3.5 双雄领衔多模态与对话赛道**，MoonshotAI 的 Kimi-K3 以超 8k 周点赞登顶，Baidu Unlimited OCR 累计下载突破 260 万。**LLaMA 量化社区（如 Ternary/Bonsai）** 爆发式增长，3 款 GGUF 模型总下载量超 300 万，Edge AI 需求显著。**Microsoft Mage-Flow 系列** 正式切入图像生成与编辑领域，展示大厂在基础模型应用端的加速布局。

---

## 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| **[upstage/Solar-Open2-250B](https://huggingface.co/upstage/Solar-Open2-250B)** | upstage | 648 | 4,804 | 巨型开源 LLM，旨在挑战 SOTA 基准测试的规模上限。虽然下载次数目前较少，但获得了 648 个周赞，显示出技术圈内对其架构潜力的关注。 |
| **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | zai-org | **4,608** | **1,267,198** | GLM 系列的最新迭代，专为优化复杂推理和长文本任务设计。凭借惊人的点赞数成为榜单第三，证明其在开发者中的高活跃度。 |
|[Prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)| prism-ml | 680 | **2,339,098** | 经过 1-bit 极致量化的 Bonsai 版本，能在普通消费级硬件上运行。高下载量反映了本地部署大模型的迫切需求。 |

## 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| **[moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)** | moonshotai | **8,090** | 99,214 | Kimi 系列的旗舰多模态大模型，具备强大的跨模态理解和生成能力。获得本周最高点赞，显示其作为行业标杆的现象级热度。 |
| **[Qwen/Qwen3.6-35B-A3B](https://huggingface.co/Qwen/Qwen3.6-35B-A3B)** | Qwen | 2,572 | **6,158,876** | Qwen3.6 的多模态核心基座模型，采用 MoE 架构并针对视觉理解进行了增强。下载量位居全榜第一，是社区中使用最广泛的模型之一。 |
|[Baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)| baidu | 3,425 | **2,694,935** | 百度推出的轻量级 OCR 专用模型，专注于从图片中提取文字信息。极高的下载表明它在文档处理和自动化流程中是“开箱即用”的首选方案。 |

## 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| **[Kwaipilot/KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev)** | Kwaipilot | 289 | 6,275 | 基于 Qwen3_5 Moe 架构开发的代码专用模型，擅长处理编程相关的复杂任务。作为开发领域的垂直工具，展现了 LLM in Code 的趋势。 |

## 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | ---: | :--- |
| **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | HauhauCS | **3,158** | **1,855,505** | Qwen3.6 的非管制版本，由社区去除了部分过滤机制。拥有近 186 万的下载量和 3000+ 的周赞，表明市场对无限制内容生成的存在强烈需求。 |
|[Empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)| empero-ai | **2,503** | **1,262,662** | 结合了 Claude 思维链策略和大上下文窗口的 Qwen3.5 量化版。凭借 2500 周的快速增长势头，成为了中小型设备上实现深度推理的热门选择。 |

---

## 生态信号

当前 HuggingFace 生态呈现出清晰的 **“多模态竞争”** 与 **“端侧下沉”** 双重趋势。一方面，Moonshot(Kimi)、Baidu(百识) 及 Tongyi(Qwen) 等顶尖团队正密集发布新一代强大多模态底座，争夺视觉与语义融合的高地；另一方面，以 **prism-ml** 和 **empero-ai** 为代表的个人创作者/小团队通过极度激进的 **bit-level 量化 (如 1-bit Ternary-Bonsai)** 技术，成功将巨型模型压缩至本地设备运行，极大地降低了入门门槛，体现了社区对高性能、低延迟推理的极致追求。

---

## 值得探索

1.  **`prism-ml/Ternary-Bonsai-27B-gguf`**：仅用 **2-bit (三值)** 就能保持 270 亿参数模型的有效性和性能，且拥有极高的社区点赞（1,085）。深入研究其量化算法和 LoRA 融合思路，对于优化资源受限环境下的模型部署具有极高的参考意义。
2.  **`baidu/Unlimited-OCR`**：虽然是一个单一功能的模型，但其累计下载量高达 **260 万**。它是将通用大模型能力专业化（专攻 OCR）的典范案例，非常适合研究如何将复杂的 Transformer 架构针对特定工业场景进行轻量化改造和高效落地。

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*