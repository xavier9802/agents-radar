# Hugging Face 热门模型日报 2026-07-28

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-28 03:14 UTC

---

# 📈 Hugging Face 热门模型日报 (2026-07-28)

## 今日速览
今日榜单中，Qwen 与 Moonshotai 的多模态对话模型占据主导，特别是 Qwen3.6 系列凭借极高的下载量（超 600 万）成为开源界的焦点。社区对量化版本（GGUF）的需求显著增长，多个模型（如 Bonsai、Qwen 家族）的 GGUF 衍生品上榜且下载表现优异，表明高效推理需求旺盛。此外，OCR 和多模态理解任务依旧活跃，Unlimited-OCR 和 Anthos 等模型维持高热度，反映出工业界对实际落地场景的偏好。

---

## 热门模型

### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | :--- | :--- |
| [GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) | zai-org | 4,553 | 1,003,547 | MoE 架构的大规模对话模型，以高效推理和强上下文处理能力著称；因其开源且性能强劲，成为用户首选之一。 |
| [Solar Open2 250B](https://huggingface.co/upstage/Solar-Open2-250B) | upstage | 630 | 3,761 | 基于 Transformer 的大容量文本生成模型，适合长文档处理；虽然下载量不及其他模型，但作为开源大模型仍具代表性。 |
| [Nanbeige4.2-3B](https://huggingface.co/Nanbeige/Nanbeige4.2-3B) | Nanbeige | 494 | 16,518 | 专为多轮对话优化的轻量级模型，响应速度快，适合部署在资源受限环境；在社区中因实用性强而受到关注。 |
| [Laguna-S-2.1](https://huggingface.co/poolside/Laguna-S-2.1) | poolside | 759 | 63,605 | 专注于高质量文本生成的模型，尤其在创意写作和逻辑推理方面表现出色；其平衡的性能与大小使其广受欢迎。 |

*(注：由于列表中含有大量量化/衍生作品，本部分仅筛选最符合“纯文本生成/对话”原始分类的原型模型)*

### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | :--- | :--- |
| [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) | moonshotai | 6,511 | 2,850 | 强大的图文交互模型，支持复杂视觉问答与推理；尽管下载次数不高，但凭借极高的关注度（点赞第一）成为现象级产品。 |
| [Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) | baidu | 3,340 | 2,645,773 | 百度出品的超大规模光学字符识别模型，支持高精度文字提取与转换；高下载量证明其在自动化办公和信息抽取领域的实用性。 |
| [Inkling](https://huggingface.co/thinkingmachines/Inkling) | thinkingmachines | 1,606 | 36,196 | 针对跨模态内容理解和生成设计，能解析并生成包含图像与文本的综合表达；在创意辅助工具领域潜力巨大。 |
| [Mage-Flow](https://huggingface.co/microsoft/Mage-Flow) | microsoft | 393 | 1,691 | Microsoft 推出的文生图模型，依托 Stable Diffusion 基础，强调可控性与细节还原度；虽数据较小，但在特定应用场景中有独到之处。 |

### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | :--- | :--- |
| [KAT-Coder-V2.5-Dev](https://huggingface.co/Kwaipilot/KAT-Coder-V2.5-Dev) | Kwaipilot | 245 | 5,312 | 基于 Qwen3.5 MoE 架构的代码辅助开发工具，能够自动生成片段或调试错误代码；对于前端后端开发者来说是利器。 |
| [Inflect Micro v2 / Nano v2](https://huggingface.co/owensong/Inflect-Micro-v2), [owensong/Inflect-Nano-v2] | owensong | 227 / 92 | 483 / 349 | 两款极低功耗本地语音合成引擎，专为边缘设备设计，无需云端即可流畅运行 TTS 服务；满足隐私敏感型应用需求。 |

### 📦 微调与量化（社区微调、GGUF、AWQ）

*(该类别存在较多重复项，按影响力精选主要代表)*

| 模型 | 作者 | 点赞 | 下载 | 简要说明 |
| :--- | :--- | ---: | :--- | :--- |
| [Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | prism-ml | 1,069 | 648,938 | 经过极致三值化处理的 LLaMA 变体，体积压缩近十倍同时保留原大部分能力；极适合老旧硬件上的快速部署体验。 |
| [Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | prism-ml | 659 | 2,257,928 | 另一款同样源自 Bonsai 家族的 GGUF 格式量化模型，通过 AWQ 技术实现了更好的精度损失控制；是追求极致性价比方案者的首选。 |
| [Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | HauhauCS | 3,133 | 1,894,395 | 由爱好者改造去除了过滤限制的 Qwen3.6 变体，更适合开放讨论甚至灰色地带议题；虽然下载数惊人，但也提醒了合规风险的存在。 |
| [Empero AI's Claude Mythos](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | empero-ai | 2,491 | 1,336,263 | 融合了类似 Claude reasoning能力的增强版 Qwen3.5，采用 1 million token 超长窗口记忆；在处理长文本分析任务时展现出非凡深度。 |

---

## 生态信号

当前 Hugging Face 呈现出明显的 **“多模态融合 + 轻量化落地”** 趋势。**Qwen 家族**无疑是最耀眼的明星，不仅官方发布的 A3B 模型登顶榜单，各路社区大佬也争相对其进行 GGUF/AWC 等形式的二次加工优化，显示出强大的生命力及兼容性潜力。与此同时像 **Moonshot AI** 这样的新兴力量也在迅速崛起，其 Kimi 系列产品展示了出色的 multimodal understanding 能力。值得注意的是，为了适应日益增长的移动端和嵌入式市场需求，许多开发者开始专注于打造体积小效率高的模型（例如 Inflect 系列）。这预示着未来几年内会有更多专注于特定领域的小巧但精悍的作品涌现出来。另外，从数据上看，“Uncensored”相关字眼频繁出现在热门条目名称之中，反映了部分群体对抗审查机制的态度以及对自由言论空间的渴望——当然这也引发了关于如何平衡创新与法律法规之间关系的思考。

---

## 值得探索

1. **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**  
   *推荐理由*: 作为一款最新推出的开源大型语言模型，它不仅在技术上达到了先进水平，而且因其良好的开放性吸引了大量研究者和工程师加入改进行列。建议重点关注它的 fine-tuning documentation 以及 benchmark results，以便深入了解其具体优势所在以及如何将其集成到自己的项目当中去提升效率或者解决问题。

2. **[Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**  
   *推荐理由*: 对于从事数字化转型业务的企业来说，这项技术简直就像是一个宝藏！无论是纸质档案电子化还是合同扫描件智能提取关键字段等等用途都非常广泛而且效果不错哦～想要了解更多细节的话可以直接访问 demo page 看看实际操作演示哈:)  

希望这份报告对你有所帮助！如果还有其他疑问欢迎随时提问~

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*