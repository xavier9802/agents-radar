# OpenClaw 生态日报 2026-08-10

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-10 02:18 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw 项目深度报告



# OpenClaw 项目动态日报
**日期：2026-08-10**  
**数据来源：github.com/openclaw/openclaw**

---

## 1. 今日速览

过去24小时 OpenClaw 项目保持高度活跃：共处理 500 条 Issue 更新（新开/活跃 429 条，关闭 71 条）和 500 条 PR 更新（待合并 332 条，已合并/关闭 168 条）。今日无新版本发布，但核心维护者 `steipete` 主导了一系列大规模重构与修复 PR，涵盖 session 缓存优化、Agent 重置逻辑修复、安全策略统一等关键模块。项目整体健康度良好，但 DeepSeek v4 Flash 静默失败、Telegram 消息重复等稳定性问题仍需持续关注。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 状态 | 描述 |
|---|---|---|
| [#121342](https://github.com/openclaw/openclaw/pull/121342) | ✅ CLOSED | **Session 缓存优化**：修复工具密集型对话后全量 SQLite session_nodes 扫描问题，50 条消息曾触发 2,500 行扫描，500 sessions 时达 25,000 行，性能提升显著 |
| [#121146](https://github.com/openclaw/openclaw/pull/121146) | ✅ CLOSED | **Agent 重置修复**：解决 provider 跨重置边界复用 call ID 导致 tool result 与 tool call 错配的问题，避免 replay context 混乱 |
| [#121346](https://github.com/openclaw/openclaw/pull/121346) | ✅ CLOSED | **GPT-5 配置保留**：修复 `openclaw doctor --fix` 后 `gpt5.personality: "off"` 被静默重置的回归问题 |
| [#121322](https://github.com/openclaw/openclaw/pull/121322) | ✅ CLOSED | **UI 恢复**：修复 Cloud Worker Desktop 面板无法通过工具栏或命令面板发现的回归 |
| [#120588](https://github.com/openclaw/openclaw/pull/120588) | ✅ CLOSED | **QA Lab 优化**：Docker 调度器现在跨证据生产者复用同一候选镜像，提升测试一致性 |

### 进行中关键 PR

- [#121312](https://github.com/openclaw/openclaw/pull/121312) — 删除重复的 account-id / sleep / config 包装层
- [#121335](https://github.com/openclaw/openclaw/pull/121335) — **安全**：统一 secret-redaction 与 SSRF 策略，消除四处分散的模式表
- [#121308](https://github.com/openclaw/openclaw/pull/121308) — 扁平化 channel-turn dispatch 命名层（6层→1层）
- [#120190](https://github.com/openclaw/openclaw/pull/120190) — 添加有界可恢复的 compaction 预检机制
- [#121278](https://github.com/openclaw/openclaw/pull/121278) — 将 quota 失败隔离到单个 auth profile，避免阻塞整个 command lane

---

## 4. 社区热点

| Issue | 评论数 | 标签 | 核心诉求 |
|---|---|---|---|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | 196 | 🦞 diamond lobster, P1, message-loss | **DeepSeek v4 Flash 静默回复失败**：2026-07-30 起多次复现，Telegram 群消息无回复且无错误日志 |
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | 19 | P1, message-loss | **#116277 关闭后静默失败仍持续**：监控 cron 在 issue 关闭后继续记录新发生，表明修复未触及根因 |
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | 18 | 🐚 platinum hermit, P1, crash-loop | **Codex PreToolUse 钩子 CPU 满载**：`openclaw-hooks` 子进程 100%+ CPU，阻塞 gateway RPC |
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | 16 | 🐚 platinum hermit, P2, security | **gh-issues 技能未净化 issue body 直接注入 sub-agent prompt**：存在 prompt injection 风险 |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | 16 | 🦞 diamond lobster, P1, session-state | **Steer 模式不注入消息**：`messages.queue.mode: "steer"` 在 tool 边界处未能注入用户消息 |
| [#10659](https://github.com/openclaw/openclaw/issues/10659) | 15 | 🦞 diamond lobster, P1, security, auth-provider | **Masked Secrets 功能请求**：Agent 可使用 API key 但不能查看明文，防 prompt injection 提取凭证 |

---

## 5. Bug 与稳定性

### 🔴 P0 / 高影响

| Issue | 描述 | Fix PR |
|---|---|---|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | DeepSeek v4 Flash 静默无回复，fallback 消息覆盖原有对话 | 已有 #121058 追踪，根因未定位 |
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | 静默失败在 #116277 关闭后持续发生 | 无 |
| [#111372](https://github.com/openclaw/openclaw/issues/111372) | macOS 上 gateway 启动后立即 SIGTERM 无限重启循环（2026.6.11→2026.7.1-2 回归） | 无 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/tool 子进程泄漏导致 zombie 累积，运行时性能退化 | 无 |

### 🟡 P1 / 中影响

| Issue | 描述 | Fix PR |
|---|---|---|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | Codex PreToolUse 钩子进程 CPU 满载，阻塞 gateway | 无 |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | Steer 模式消息注入失败 | 无 |
| [#96242](https://github.com/openclaw/openclaw/issues/96242) | Telegram 多渠道路径导致重复消息发送 | 无 |
| [#88079](https://github.com/openclaw/openclaw/issues/88079) | WebChat 中 Kimi Code / DeepSeek Reasoner 的 reasoning_content 不流式渲染 | 无 |
| [#105528](https://github.com/openclaw/openclaw/issues/105528) | Windows v2026.6.x 上 exec/read 工具静默返回空输出（回归） | 无 |
| [#120735](https://github.com/openclaw/openclaw/issues/120735) | Telegram 入站 stickers 未下载到磁盘，agent 无法查看 | 无 |

### 🟢 P2 / 低影响

| Issue | 描述 |
|---|---|
| [#57901](https://github.com/openclaw/openclaw/issues/57901) | Safeguard compaction 忽略 `compaction.model` 配置，使用 session 主模型 |
| [#47975](https://github.com/openclaw/openclaw/issues/47975) | Subagent 完成后主 session 无响应 |
| [#90378](https://github.com/openclaw/openclaw/issues/90378) | 升级 5.28→6.1 后 cron store 静默迁移至 SQLite，新 job 默认 `delivery.mode=announce` 导致渠道错误 |
| [#52130](https://github.com/openclaw/openclaw/issues/52130) | Telegram 重启风暴 + `SecretRef` 诊断误导 |
| [#56653](https://github.com/openclaw/openclaw/issues/56653) | Slack `reaction_added/removed` 事件在 Socket Mode 下未投递 |

---

## 6. 功能请求与路线图信号

| Issue | 诉求 | 路线图信号 |
|---|---|---|
| [#10659](https://github.com/openclaw/openclaw/issues/10659) | **Masked Secrets**：Agent 使用但不可见 API key | ⭐ 高需求（4👍），安全类功能，与 #121335 统一 secret-redaction 方向一致，可能纳入下一安全版本 |
| [#22438](https://github.com/openclaw/openclaw/issues/22438) | **分层 Bootstrap 文件加载**：按 session 类型（sub-agent/cron）选择性加载 workspace 文件 | 节省 context 预算，与 compaction 优化协同，可能作为性能改进纳入 |
| [#67413](https://github.com/openclaw/openclaw/issues/67413) | **Per-agent Dreaming 配置**：独立控制各 agent 的 memory dreaming 开关 | 多 agent 场景刚需（5👍），避免 MemoryMax OOM，路线图信号明确 |
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | **Multi-Slot Memory 架构**：多 memory 插件同时运行 | 架构级改进，替换单 slot 限制，长期路线图方向 |
| [#63990](https://github.com/openclaw/openclaw/issues/63990) | **多索引 Embedding Memory 与模型感知 failover** | 生产级可靠性需求，避免混合向量空间 |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) | Active-memory 阻塞回复 & QMD boot 过载 gateway | 需架构调整，当前 `active-memory` 插件行为需优化 |
| [#47677](https://github.com/openclaw/openclaw/issues/47677) | Telegram 反应（reaction）作为一等公民的 agent 唤醒/执行触发器 | 渠道能力增强，2👍 |

---

## 7. 用户反馈摘要

**痛点 Top 5：**

1. **DeepSeek v4 Flash 静默失败**（#116277，196 评论）：用户反复报告模型不回复且无错误日志，影响生产可用性。关闭后仍复现（#121058），信任度受损。
2. **消息丢失与重复**（#96242, #69208）：Telegram 多渠道路径导致重复发送；多 channel 下 transcript/replay 存在重复组装 bug。
3. **Windows exec/read 回归**（#105528）：v2026.6.x 后工具静默返回空输出，影响 Windows 用户工作流。
4. **升级迁移不可见**（#90378）：cron store 从 JSON→SQLite 静默迁移且丢失配置信息，用户无感知。
5. **Slack Socket Mode 事件丢失**（#56653）：reaction 事件未投递，多 bot 账号场景下排查困难。

**正面反馈：**
- QA Lab Docker 候选复用（#120588/#121253）提升了测试可重现性
- Session 缓存扫描优化（#121342）直接解决工具密集型对话的性能瓶颈

---

## 8. 待处理积压

| Issue | 创建时间 | 评论数 | 风险 | 建议 |
|---|---|---|---|---|
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | 2026-03-14 | 16 | 🔴 安全：untrusted input 直接注入 sub-agent prompt | 需安全审查，优先级 P1 |
| [#69208](https://github.com/openclaw/openclaw/issues/69208) | 2026-04-20 | 13 | 🟡 多 channel 重复 transcript/replay 的 umbrella issue | 需维护者主导分类 |
| [#56653](https://github.com/openclaw/openclaw/issues/56653) | 2026-03-28 | 5 | 🟡 Slack Socket Mode reaction 事件长期未投递 | 需 live repro 确认 |
| [#114211](https://github.com/openclaw/openclaw/issues/114211) | 2026-07-27 | 7 | 🟡 Matrix 房间 agent 无限循环 no-reply 输出 | 需维护者 review |
| [#78301](https://github.com/openclaw/openclaw/issues/78301) | 2026-05-06 | 6 | 🟡 插件加载器静默容忍非法 contract，调试成本极高 | 需改善错误诊断 |

---

**报告生成时间：2026-08-10**  
**分析师：Agnes (Sapiens AI)**

---

## 横向生态对比



# AI 智能体开源生态横向对比分析
**日期：2026-08-10 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026 年 8 月的个人 AI 智能体开源生态呈现**高活跃度、低合并率**的特征，核心项目普遍处于密集修复期而非功能爆发期。安全性（SSRF、shell 注入、凭证泄露）和会话状态可靠性已成为跨项目共同痛点，反映行业正从"功能竞赛"转向"生产可用性建设"。OpenClaw 作为参照标杆保持最大社区体量，而 ZeroClaw、Hermes、CoPaw 等项目在 Rust/安全导向方向快速追赶，生态分化趋势明显。

---

## 2. 各项目活跃度对比

| 项目 | Issues 更新 | PR 更新 | 合并/关闭 PR | Release | 健康度 |
|---|---|---|---|---|---|
| **OpenClaw** | 500（429 活跃 / 71 关闭） | 500（332 待合 / 168 已合） | 168 | ❌ 无 | 🟢 良好，稳定性待改善 |
| **ZeroClaw** | 50（38 活跃 / 12 关闭） | 50（49 待合 / 1 已合） | 1 | ❌ 无 | 🟡 高活跃但合并瓶颈严重 |
| **Hermes Agent** | 50 | 50（4 合并） | 4 | ❌ 无 | 🟡 P0 数据丢失需关注 |
| **CoPaw (QwenPaw)** | 18（7 关闭） | 26（1 合并） | 1 | ❌ 无 | 🟢 响应迅速，迭代健康 |
| **IronClaw** | 22（15 活跃 / 7 关闭） | 32（24 待合 / 8 已合） | 8 | ❌ 无 | 🟡 WebUI 回归较多 |
| **NanoBot** | 5 | 16（4 合并） | 4 | ❌ 无 | 🟡 双安全漏洞同日披露 |
| **NanoClaw** | 1 | 16（0 合并） | 0 | ❌ 无 | 🟡 高提交低交付 |
| **PicoClaw** | 3 | 6（1 合并） | 1 | ❌ 无 | 🟢 安全修复质量高 |
| **LobsterAI** | 3 | 0 | 0 | ❌ 无 | 🟡 停滞风险 |
| **Moltis** | 2 | 1（0 合并） | 0 | ❌ 无 | 🟢 小体量常规迭代 |
| **NullClaw** | — | — | — | — | ⚪ 无活动 |
| **ZeptoClaw** | — | — | — | — | ⚪ 无活动 |

---

## 3. OpenClaw 在生态中的定位

**规模优势**：OpenClaw 以 500 条 Issue/PR 更新量级远超其他项目（约为次高项 ZeroClaw 的 10 倍），是最成熟的参照基准。

**技术路线差异**：
- OpenClaw 采取**全渠道多通道统一架构**，Session 状态管理与渠道抽象层是其核心竞争力
- ZeroClaw 选择 **Rust 重写 + 可验证意图（verifiable intent）** 路线，侧重安全硬化
- Hermes Agent 聚焦**桌面端体验 + 工具链可靠性**
- CoPaw (QwenPaw) 与阿里通义生态绑定，强调**DeepSeek V4 大上下文支持 + SSE 流式**
- NanoBot 走**轻量级 + Telegram 优先**路线

**社区规模对比**：OpenClaw 每日处理 500 级更新，社区规模约为其他活跃项目的 5-10 倍。ZeroClaw 和 Hermes 社区增长迅速但体量仍小一个数量级。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|---|---|---|
| **会话状态可靠性** | OpenClaw, Hermes, CoPaw, ZeroClaw | Session 缓存扫描优化、数据丢失修复、断点恢复机制 |
| **安全性硬化** | OpenClaw, NanoBot, PicoClaw, ZeroClaw | SSRF 封堵、shell 注入绕过修复、Masked Secrets、verifiable intent |
| **可观测性** | NanoBot, ZeroClaw, CoPaw | Token 消耗明细日志、Langfuse OTel traces、SSE 实时流式渲染 |
| **多模型/上下文适配** | OpenClaw, CoPaw, ZeroClaw, LobsterAI | DeepSeek V4 100W token 支持、per-model 上下文窗口配置、模型名称解析 |
| **渠道稳定性** | OpenClaw, NanoBot, PicoClaw, ZeroClaw | Telegram 静默卡死恢复、长轮询重连、Slack Socket Mode 事件投递 |
| **工具调用可靠性** | OpenClaw, Hermes, ZeroClaw | tool call/result 错配修复、MCP 工具预算预检、参数类型安全转换 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 架构关键词 |
|---|---|---|---|
| **OpenClaw** | 全渠道统一接入、Session 管理、Agent 框架 | 生产级多通道部署用户 | TypeScript, SQLite session, 多渠道 dispatch |
| **ZeroClaw** | 安全硬化、可验证意图、Rust 底层 | 安全敏感场景（金融/政务） | Rust, verifiable intent, workspace isolation |
| **Hermes Agent** | 桌面端体验、Holographic Memory、CLI | 个人生产力用户 | Electron desktop, MemoryMax, skill system |
| **CoPaw (QwenPaw)** | DeepSeek V4 集成、流式渲染、审批机制 | 阿里通义生态用户 | SSE streaming, Qwen 模型深度集成, 审批流 |
| **NanoBot** | Telegram 优先、轻量部署、CLI | 个人 Telegram Bot 用户 | 轻量级, Telegram 深度集成 |
| **PicoClaw** | 多通道安全（SSRF 封堵）、表格渲染 | 多平台消息网关用户 | 多通道抽象, CreateSafeHTTPClient |
| **IronClaw** | WebUI v2、技能系统、自动化编排 | 可视化操作偏好用户 | WebUI-first, skill-based automation |
| **NanoClaw** | 容器化部署、Dial 渠道（SMS/语音） | 企业级容器部署用户 | Docker hardened-image, Dial adapter |
| **LobsterAI** | 多模型支持、跨模型子任务 | 多模型切换用户 | OpenRouter/NVIDIA 模型兼容 |
| **Moltis** | Vault 安全、Apple Container 集成 | 密码管理+容器编排用户 | Vault encryption, Apple sandbox |

---

## 6. 社区热度与成熟度分层

**🔴 快速迭代层（高活跃 + 高更新量）**
- **OpenClaw**：500 级更新，核心维护者密集推进重构，处于功能完善期
- **ZeroClaw**：100 级更新但合并率极低（1/50），处于高速开发但代码审查瓶颈期

**🟡 稳健迭代层（中等活跃 + 明确修复节奏）**
- **Hermes Agent**：100 级更新，安全与 Session 稳定性修复为主
- **CoPaw (QwenPaw)**：44 条更新，维护者响应迅速（同日关闭重复 Bug），迭代效率高
- **IronClaw**：54 条更新，WebUI 回归较多，处于稳定性巩固期

**🟢 成长积累层（低活跃 + 小体量但健康）**
- **NanoBot**：21 条更新，双安全漏洞披露但修复链清晰
- **PicoClaw**：9 条更新，安全修复质量高，合并节奏合理
- **NanoClaw**：17 条更新，基础设施重构为主，零合并需关注审阅节奏

**⚪ 停滞/低活跃层**
- **LobsterAI**：仅 3 条 Issue，0 PR，stale 标记 Issue 积压
- **Moltis**：3 条更新，小体量常规迭代
- **NullClaw / ZeptoClaw**：无活动，存在项目休眠风险

---

## 7. 值得关注的趋势信号

### ① 安全从"功能"变为"基础设施"
OpenClaw（#121335 统一 secret-redaction）、PicoClaw（#3322/#3323/#3324 SSRF 修复）、NanoBot（#5306/#5305 shell 绕过）、ZeroClaw（#9866 可验证意图硬化）同时推进安全加固，表明行业已进入**安全内生化**阶段，安全不再是附加功能而是架构核心。

**参考**：Agent 开发者应将 SSRF 防护、凭证脱敏、shell 命令白名单作为基础能力而非可选项。

### ② 大上下文模型的适配竞赛
CoPaw 已合并 DeepSeek V4 100W token 支持（#6846），OpenClaw 存在 DeepSeek v4 Flash 静默失败（#116277），LobsterAI 用户抱怨上下文窗口不可配置（#1187），ZeroClaw RFC #7100 提出 per-model 配置。

**参考**：100W+ token 上下文已成为新基线，**上下文管理策略**（压缩、选点、预算）将成为下一代 Agent 框架的核心竞争力。

### ③ 会话可靠性是信任分水岭
OpenClaw（session 缓存优化 #121342）、Hermes（P0 数据丢失 #82756 第三次发生）、CoPaw（断点恢复 #5579）均将会话状态作为最高优先级。

**参考**：Agent 的**幂等性**和**断点续传**能力直接影响生产可用性，建议在设计阶段即考虑 session persistence 和 crash recovery。

### ④ 可观测性成为新刚需
NanoBot（#5266 token 消耗明细）、ZeroClaw（#9556 Langfuse OTel）、CoPaw（#6843 SSE 流式渲染）同时推进可观测性建设。

**参考**：Agent 调用链追踪、token 成本可视化、流式输出体验将成为用户留存关键因素。

### ⑤ 渠道稳定性决定生产可用性
Telegram 静默卡死（NanoBot #5156）、Matrix 重连（PicoClaw #3203）、Slack Socket Mode 事件丢失（OpenClaw #56653）在多个项目同时出现。

**参考**：渠道适配层需要**活检测试 + 自动重连 + 错误可观测**三层保障，建议采用"健康探针 + 指数退避重连"的标准模式。

---

**报告结论**：2026 年 8 月个人 AI 智能体开源生态正经历从"功能扩张"到"质量巩固"的转型期。OpenClaw 保持生态领导者地位，ZeroClaw 和 Hermes 在安全和可靠性方向快速追赶，CoPaw 依托通义生态实现差异化突破。对开发者而言，**会话可靠性、安全硬化、大上下文适配、可观测性**是下一阶段最值得投入的四个方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-10

## 1. 今日速览

过去24小时 NanoBot 项目保持较高活跃度：共收到 **5 条 Issue**（全部为新建或活跃状态）和 **16 条 PR**（4 条已合并/关闭，12 条仍开放）。今日无新版本发布，但社区贡献集中体现在**安全性修复**与**Telegram 链路稳定性**两个方面。两条关于 `exec.allowPatterns` 的绕过漏洞同日报告，表明外部安全审计正在产生实效；Telegram 相关 PR 形成拆分修复链，显示出模块化的改进思路。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#5307](https://github.com/HKUDS/nanobot/pull/5307) | docs/feature | 恢复 GitHub Star History 图表（更换第三方提供商规避原项目下线限制） |
| [#5308](https://github.com/HKUDS/nanobot/pull/5308) | test/CI | 加强用户路径测试覆盖（CLI 交互、WebUI chat fork、版本检查、路由鉴权），新增 V8 覆盖率报告并强制 gates |
| [#5304](https://github.com/HKUDS/nanobot/pull/5304) | docs/fix | 澄清 WebUI 语音输入需要 HTTPS 的浏览器限制原因，并文档化可信 HTTPS 方案 |
| [#4019](https://github.com/HKUDS/nanobot/pull/4019) | feature | 关闭：GitAgent Protocol (agent.yaml + SOUL.md) 支持 PR，已合并后关闭 |

> **整体判断**：今日关闭的 PR 以文档完善、测试加固和辅助功能恢复为主，直接推动核心功能进度的 PR 均为开放状态，项目仍处于"积累性修复"阶段，尚未出现大型功能合入。

---

## 4. 社区热点

### 🔴 安全漏洞（双 Issue 同日报告，高度关注）

**[#5306](https://github.com/HKUDS/nanobot/issues/5306)** & **[#5305](https://github.com/HKUDS/nanobot/issues/5305)**
- **作者**：YLChen-007
- **问题**：`exec.allowPatterns` 配置的 allowlist 存在 shell-chain 绕过漏洞，攻击者可通过 OpenAI-compatible API 注入额外命令片段，突破权限限制执行未授权 shell 命令。
- **诉求**：社区对安全边界配置的有效性高度关注，两条 Issue 从不同角度（CLI 路径 vs API 路径）报告同一根因，建议维护者优先响应并评估是否需要紧急补丁版本。

### 🟡 Telegram 链路稳定性（PR 拆分修复链）

**[#5156](https://github.com/HKUDS/nanobot/pull/5156)** — 恢复静默卡死的 Telegram 轮询连接
- 长期存在的生产问题：网络抖动后 bot 进程继续运行但消息接收永久停止，日志无异常。
- **[PR #5301](https://github.com/HKUDS/nanobot/pull/5301)** 作为前置补丁已合并低风险的日志桥接 + 轻量活检测试，完整 watchdog 方案在 #5156 中推进。

### 🟢 Token 用量可观测性

**[#5266](https://github.com/HKUDS/nanobot/issues/5266)**（13 条评论）
- 用户反馈 nanobot 在无用户交互时 2 小时内消耗百万级 token，请求记录每次调用产生的 token 消耗。
- **[PR #5299](https://github.com/HKUDS/nanobot/pull/5299)** 已提出结构化 token usage records 方案（保留最近 50 条记录 + `/api/settings/usage/records` 端点），与 Issue 诉求高度对齐，有望合并。

---

## 5. Bug 与稳定性

| 级别 | Issue/PR | 描述 | Fix PR |
|------|----------|------|--------|
| 🔴 高 | [#5306](https://github.com/HKUDS/nanobot/issues/5306) / [#5305](https://github.com/HKUDS/nanobot/issues/5305) | `exec.allowPatterns` allowlist 绕过，允许未授权 shell 命令执行 | 暂无 |
| 🟠 中 | [#5311](https://github.com/HKUDS/nanobot/issues/5311) | Agnes AI 自定义 provider 对嵌套对象工具参数双重 JSON 编码，导致 MCP 工具调用失败 | 暂无 |
| 🟠 中 | [#5295](https://github.com/HKUDS/nanobot/issues/5295) | Docker Compose 部署报错：`entrypoint.sh: Permission denied` | 暂无 |
| 🟡 低 | [#5302](https://github.com/HKUDS/nanobot/pull/5302) | Dream 记忆整合期间使用不兼容工具导致 prompt/tool 不匹配 | PR #5302（开放） |
| 🟡 低 | [#5303](https://github.com/HKUDS/nanobot/pull/5303) | 天气 skill 中裸 `curl` 在 Windows PowerShell 下解析为 `Invoke-WebRequest` 别名导致失败 | PR #5303（开放） |

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 状态 | 纳入可能性 |
|------|------|------|------------|
| Token 消耗明细日志 | Issue #5266 | PR #5299 已提出方案 | ⭐⭐⭐⭐ 高（方案已就绪） |
| 声明式 Responses 能力配置 | PR #5204 | 开放，优先级 P1 | ⭐⭐⭐⭐ 高（重构类 PR，统一 provider 行为） |
| 跨平台 Computer Use 工具（browser + mouse/keyboard） | PR #4276 | 开放，draft 状态 | ⭐⭐⭐ 中（需解决依赖和后端适配） |
| Agent Plugins 与 CLI Apps 集成 | PR #5288 | 开放 | ⭐⭐⭐ 中（架构扩展，需评估兼容性） |
| API 服务状态真实显示（externally-managed servers） | PR #5255 | 开放，draft | ⭐⭐ 低（体验优化类） |
| 市场技能可覆盖内置技能 | PR #5309 | 开放 | ⭐⭐⭐⭐ 高（bug fix 性质，逻辑清晰） |

---

## 7. 用户反馈摘要

- **Token 成本焦虑**（#5266）：用户反映 nanobot 在空闲状态下仍大量消耗 token，缺乏可观测性导致难以排查和优化成本。
- **部署易用性问题**（#5295）：Docker Compose 一键部署因 entrypoint.sh 权限问题失败，影响新手用户首次体验。
- **第三方 Provider 兼容缺陷**（#5311）：Agnes AI 自定义 provider 在处理嵌套对象参数时出现双重编码，反映 nanobot 对非标准实现的容错能力有待加强。
- **微信登录强制刷新失效**（PR #5310）：`--force` 标志因 token 恢复逻辑被绕过而无效，用户期望能主动刷新登录态。
- **语音输入 HTTPS 困惑**（PR #5304 修复前）：浏览器安全策略导致 HTTP 环境下语音功能不可用，用户不清楚原因，需要明确文档说明。

---

## 8. 待处理积压

| 类型 | ID | 标题 | 风险提示 |
|------|----|------|----------|
| 🔴 安全 | [#5306](https://github.com/HKUDS/nanobot/issues/5306) | `exec.allowPatterns` shell-chain bypass | 已公开披露，建议紧急响应 |
| 🔴 安全 | [#5305](https://github.com/HKUDS/nanobot/issues/5305) | `exec.allowPatterns` allowlist bypass via API | 同上，两条需联动修复 |
| 🟠 Bug | [#5311](https://github.com/HKUDS/nanobot/issues/5311) | Agnes AI nested-object double encoding | 影响自定义 provider 用户 |
| 🟠 Bug | [#5295](https://github.com/HKUDS/nanobot/issues/5295) | Docker entrypoint.sh Permission denied | 影响部署体验 |
| 🟡 PR 积压 | [#5271](https://github.com/HKUDS/nanobot/pull/5271) | 防止陈旧后台任务覆盖会话数据（P0） | 标记 P0 且存在 conflict，需尽快处理 |
| 🟡 PR 积压 | [#5156](https://github.com/HKUDS/nanobot/pull/5156) | Telegram 静默卡死恢复 | 长期未合入，影响生产稳定性 |

---

**项目健康度评估**：🟢 活跃 | 安全类 Issue 需重点关注；测试和文档质量持续改进；核心功能修复 PR 数量充足但合入节奏偏慢。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-10

---

## 1. 今日速览

Hermes Agent 今日保持高活跃度：过去 24 小时内共处理 100 条更新（50 Issues + 50 PRs），其中 4 个 PR 已关闭（含 2 个合并修复），46 个 PR 仍在待合并状态。项目整体处于密集修复阶段，**安全性与 Session 状态稳定性**是今日最突出的两大主题，共发现 1 个 P0 级数据丢失 Bug、3 个 P2 级安全边界问题，以及多个影响桌面端体验的回归缺陷。无新版本发布。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已关闭/合并 PR（4 个）

| PR | 作者 | 内容 |
|----|------|------|
| [#82873](https://github.com/NousResearch/hermes-agent/pull/82873) | Baophan00 | 修复 `execute_code` sandbox 中 `read_file` 去重逻辑导致内容丢失的问题 |
| [#77992](https://github.com/NousResearch/hermes-agent/pull/77992) | ethernet8023 | 修复 OS 特定测试 fake 主机名问题，新增 macOS + Windows CI 通道 |
| [#43819](https://github.com/NousResearch/hermes-agent/pull/43819) | adambiggs | Holographic Memory 共享单个 SQLite 连接，修复并发写入竞争 |
| （关联修复）[#78490](https://github.com/NousResearch/hermes-agent/pull/78490) | itskaism | 对带前缀的凭证全文进行脱敏（结构级修复，非单 Vendor） |

**项目推进评估：** 今日合并的 PR 主要集中在**工具层可靠性**（文件读取去重、SQLite 连接共享）和**测试基础设施**（CI 覆盖）。安全类修复以开放 PR 为主，尚未合并，整体项目向前推进约 **10-15%**，安全边界加固是下一阶段重点。

---

## 4. 社区热点

### 评论数 Top 5 Issues

| Issue | 评论数 | 热度分析 |
|-------|--------|----------|
| [#63047](https://github.com/NousResearch/hermes-agent/issues/63047) — Desktop 在 macOS 27 beta 完全无响应 | 19 | 高热度：涉及最新 macOS 版本兼容性，UI 冻结影响核心体验 |
| [#26689](https://github.com/NousResearch/hermes-agent/issues/26689) — VoiceOver 无障碍访问改进 | 13 | 社区呼声：视障用户群体对 Hermes 后端能力认可，但 UX 门槛高 |
| [#66824](https://github.com/NousResearch/hermes-agent/issues/66824) / [#71987](https://github.com/NousResearch/hermes-agent/issues/71987) — cronjob `repeat='forever'` TypeError | 各 6 | 重复报告：同一根因导致两个独立 Issue，说明 cron 模块测试覆盖不足 |
| [#46064](https://github.com/NousResearch/hermes-agent/issues/46064) — OpenRouter router models 被 `hermes model` 静默隐藏 | 3 | 工具链问题：新模型上线但 CLI 未同步，用户只能手动编辑 config |
| [#80125](https://github.com/NousResearch/hermes-agent/issues/80125) — 微信 adapter `ret=-2` 误报为 rate limit | 3 | 平台适配：错误码映射不准确，掩盖真实原因（missing `context_token`） |

**热点分析：** 社区最关注的是 **Desktop 客户端稳定性**（#63047、#82872、#79518、#82851）和 **会话状态丢失**（#82756、#82770），反映出现有用户在生产使用中遇到了影响信任的严重问题。无障碍需求（#26689）获 1 个 👍，表明多元化用户群体正在增长。

---

## 5. Bug 与稳定性

### 🔴 P0 — 数据丢失

| Issue | 摘要 | 状态 | Fix PR |
|-------|------|------|--------|
| [#82756](https://github.com/NousResearch/hermes-agent/issues/82756) | Desktop 按 Enter 提交静默删除 ~65 条消息（第三次发生，前两次 #70516、#80763 的修复均未覆盖此路径） | OPEN | 暂无 |

### 🟠 P1 — 严重功能缺陷

| Issue | 摘要 | 状态 | Fix PR |
|-------|------|------|--------|
| [#63047](https://github.com/NousResearch/hermes-agent/issues/63047) | macOS 27 beta 上 Desktop 在约 5 条消息后完全冻结，Settings 也无法访问 | OPEN | 暂无 |
| [#82842](https://github.com/NousResearch/hermes-agent/issues/82842) | **Critical** Agent 在执行 scoped 文件夹删除后，对 C:\ 根目录执行了 `rd /s /q`，导致系统盘几乎完全数据丢失（因无管理员权限才幸免） | OPEN | 暂无 |
| [#82872](https://github.com/NousResearch/hermes-agent/issues/82872) | `ws_orphan_reap` 结束的 session 重启后成为不可点击的幽灵 tile | OPEN | 暂无 |

### 🟡 P2 — 中等问题

| Issue | 摘要 | Fix PR |
|-------|------|--------|
| [#66824](https://github.com/NousResearch/hermes-agent/issues/66824) / [#71987](https://github.com/NousResearch/hermes-agent/issues/71987) | cronjob `create`/`update` 抛出 `TypeError: '<=' not supported between 'str' and 'int'` | 暂无 |
| [#75097](https://github.com/NousResearch/hermes-agent/issues/75097) | AIAgent 默认 iteration budget=90，`execute_code` refund 语义不一致 | 暂无 |
| [#82846](https://github.com/NousResearch/hermes-agent/issues/82846) | Smart-approval 辅助 LLM 调用无超时，卡住整个 session | 暂无 |
| [#82770](https://github.com/NousResearch/hermes-agent/issues/82770) | 测试 session 泄漏到生产 `state.db`，产生 700+ 垃圾行 | 暂无 |
| [#82805](https://github.com/NousResearch/hermes-agent/issues/82805) | 本地 llama.cpp 间歇性返回空 body 400，httpx 连接池复用导致 | [#82809](https://github.com/NousResearch/hermes-agent/pull/82809) ✅ 已开 PR |
| [#82875](https://github.com/NousResearch/hermes-agent/issues/82875) | `reasoning_effort` 对命名 `providers:` 端点静默丢弃 | 暂无 |
| [#78190](https://github.com/NousResearch/hermes-agent/issues/78190) | Gmail MCP OAuth 在 gateway 进程中 `404 on /register` | 暂无 |
| [#80841](https://github.com/NousResearch/hermes-agent/issues/80841) | Fastmail `delete_event` 需要交互确认 widget，CLI/TUI/Matrix 无法完成 | 暂无 |

### 🟢 已有 Fix PR 的 Bug

| Issue | Fix PR |
|-------|--------|
| [#82805](https://github.com/NousResearch/hermes-agent/issues/82805) — llama.cpp 400 | [#82809](https://github.com/NousResearch/hermes-agent/pull/82809) |
| [#63047](https://github.com/NousResearch/hermes-agent/issues/63047) 相关 — read_file 去重 | [#82873](https://github.com/NousResearch/hermes-agent/pull/82873) ✅ 已关闭 |

---

## 6. 功能请求与路线图信号

| Issue | 诉求 | 已有 PR 匹配 | 纳入下一版本可能性 |
|-------|------|-------------|-------------------|
| [#15831](https://github.com/NousResearch/hermes-agent/issues/15831) — Job chaining：一个 cron job 完成时触发另一个 | 低，长期未响应 | 暂无 | ⭐ 低（无维护者响应） |
| [#61644](https://github.com/NousResearch/hermes-agent/issues/61644) — 自主评估与自改进引擎（HAEE） | 验证 Hermes 自称的 "self-improving" 是否真实有效 | 暂无 | ⭐⭐ 中（概念合理但需大幅开发） |
| [#76883](https://github.com/NousResearch/hermes-agent/issues/76883) — Memory 操作可逆化（local archive） | `remove()`/`replace()` 当前不可逆，技能已有 archive 机制，memory 不对称 | 暂无 | ⭐⭐ 中（需求明确，实现成本中等） |
| [#82854](https://github.com/NousResearch/hermes-agent/pull/82854) — Desktop 显示每个 skill 最近使用的 session | 技能用量遥感的 "where" 部分 | ✅ 已开 PR | ⭐⭐⭐ **高**（PR 已就绪） |
| [#82870](https://github.com/NousResearch/hermes-agent/pull/82870) — `no_agent` cron job 记录到桌面运行历史 | 脚本型 job 完成后在桌面不显示历史 | ✅ 已开 PR | ⭐⭐⭐ **高**（小修复，PR 已就绪） |
| [#82316](https://github.com/NousResearch/hermes-agent/issues/82316) — Desktop 新建 session 不强制进入项目 drill-in 视图 | 体验改进 | 暂无 | ⭐⭐ 中 |

---

## 7. 用户反馈摘要

### 痛点
1. **Session 数据丢失是最大信任危机**：#82756 是第三次同类报告，用户明确提到前两次修复（#70516、#80763）均未覆盖此路径，"valid ordinal with `confirm_truncate: true` 执行了破坏性替换"。
2. **Windows 下 Agent 权限越界**：#82842 用户描述 Agent 在 scoped 文件夹删除后升级为对 C:\ 根执行 `rd /s /q`，"仅因进程无管理员权限才幸免"，属于安全边界严重缺陷。
3. **Desktop 在最新 macOS 上不可用**：#63047 用户指出"不只是打字 lag，而是 UI 完全冻结，Settings 也无法访问"， recovery 只能重启。
4. **cronjob 模块测试覆盖不足**：#66824 和 #71987 是同一 TypeError 的独立报告，说明 `repeat='forever'` 路径缺乏自动化测试。
5. **OpenRouter 新模型上线滞后**：#46064 用户抱怨 `openrouter/pareto-code` 等 router 模型在 `hermes model` 中完全不可见，只能手动编辑 config.yaml。

### 正面反馈
- #26689 用户肯定 Hermes "后端和 agent 生态极其强大"，仅 UX 无障碍方面有落差。
- #15831 用户给 Job chaining 功能投了 1 个 👍，说明有社区需求基础。

---

## 8. 待处理积压

| Issue/PR | 类型 | 风险等级 | 建议优先级 |
|----------|------|----------|-----------|
| [#82756](https://github.com/NousResearch/hermes-agent/issues/82756) | P0 Bug | 🔴 极高 | 立即处理：第三次同类数据丢失，已破坏用户信任 |
|

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-10

---

## 1. 今日速览

过去 24 小时 PicoClaw 保持中等活跃度：**6 条 PR、3 条 Issue**，其中 1 条 PR 已合并，1 条 Issue 已关闭。今日贡献集中在两个方向：**Telegram 表格渲染体验优化**（1 Issue + 1 PR）和 **媒体下载安全加固**（3 条安全修复 PR）。项目整体健康度良好，社区参与度较高，但合并吞吐偏低（6 进 1 出），需关注 PR 积压情况。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### ✅ 已合并 / 已关闭

| PR | 作者 | 说明 |
|----|------|------|
| [#3326](https://github.com/sipeed/picoclaw/issues/3326) | As-tsaqib | 修复 `pnpm-lock.yaml` 中重复的 `semver@7.8.5` 映射条目，解决 `pnpm install --frozen-lockfile` 报错。属于构建基础设施修复，无功能变更。 |

### 🔄 待合并（重要 PR）

- **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222)** — `deltachat` 模块重构，减少约 200 行代码，删除遗留功能和过时测试，引用官方中继列表而非硬编码副本，重命名 `invite_link` → `join_invite_link`。该 PR 已开放较久（2026-07-03），需关注评审进度。

- **[PR #3327](https://github.com/sipeed/picoclaw/pull/3327)** — 对应 Issue #3325，实现 Telegram 原生表格渲染，支持 GFM 表格和 HTML `<table>` 块，替代目前降级为等宽代码块的体验。

- **[PR #3322/#3323/#3324](https://github.com/sipeed/picoclaw/pull/3322)** — SashaMIT 提交的系列安全修复，为 QQ/Telegram/Discord/LINE/Slack/微信/企微等通道引入 `CreateSafeHTTPClient` 和 `ValidateSafeHTTPURL`，封堵 SSRF 风险（媒体下载可被诱导访问内网/回环地址）。三条 PR 结构一致，建议批量合并。

---

## 4. 社区热点

| 类型 | 编号 | 热度 | 说明 |
|------|------|------|------|
| Issue | [#3203](https://github.com/sipeed/picoclaw/issues/3203) | ⭐⭐⭐ | Matrix 长轮询断网后无重连逻辑，systemd `Restart=on-failure` 无法触发，属生产环境稳定性痛点（8 评论 / 2 👍，已关闭） |
| PR | [#3327](https://github.com/sipeed/picoclaw/pull/3327) | ⭐⭐ | Telegram 表格渲染 native 化，直接回应用户需求（今日新建） |
| PR | [#3322](https://github.com/sipeed/picoclaw/pull/3322) | ⭐⭐ | 通用媒体下载 SSRF 修复，覆盖多个通道（今日新建） |

---

## 5. Bug 与稳定性

| 级别 | Issue/PR | 描述 | Fix 状态 |
|------|----------|------|----------|
| 🔴 高 | [#3203](https://github.com/sipeed/picoclaw/issues/3203) | Matrix `/sync` 循环在网络/服务中断后永久死亡，且因主进程存活导致 systemd 不重启 | ✅ 已关闭（未确认是否已合入修复） |
| 🟡 中 | [#3322/#3323/#3324](https://github.com/sipeed/picoclaw/pull/3322) | 多个通道媒体下载存在 SSRF 风险，可访问内网/回环地址 | 🔄 PR #3322/#3323/#3324 待合并 |

> **注：** #3203 已关闭但暂无关联合并 PR，需确认修复是否已包含在最近提交中。

---

## 6. 功能请求与路线图信号

| Issue | PR 关联 | 需求描述 | 纳入下版概率 |
|-------|---------|----------|--------------|
| [#3325](https://github.com/sipeed/picoclaw/issues/3325) | [#3327](https://github.com/sipeed/picoclaw/pull/3327) | Telegram 原生表格渲染 | 🟢 高 — PR 已提交，仅待评审 |
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) | 无 | IRCv3 长消息合并为单条语义消息 | 🟡 中 — 需求清晰但尚无 PR |
| [#3222](https://github.com/sipeed/picoclaw/pull/3222) | 自驱 PR | deltachat 模块清理与现代化 | 🟡 中 — PR 已提交但长期未合并 |

---

## 7. 用户反馈摘要

- **Matrix 通道稳定性**（#3203）：用户在生产环境遭遇网络闪断后同步永久中断，且无法通过 systemd 自动恢复，影响可用性。反映项目在长期运行韧性方面存在短板。
- **Telegram 表格展示**（#3325）：用户期望结构化 Markdown 表格在 Telegram 中以原生 UI 呈现，而非降级为代码块。这是对平台原生能力的充分利用诉求。
- **IRC 长消息语义**（#3287）：IRCv3 客户端自动拆分超 512 字节消息，导致 PicoClaw 将单条消息误判为多条，影响对话连贯性。
- **媒体下载安全**（#3322/#3323/#3324）：用户/贡献者主动发现并修复 SSRF 风险，体现社区安全意识提升。

---

## 8. 待处理积压

| 类型 | 编号 | 创建日期 | 距今 | 说明 |
|------|------|----------|------|------|
| PR | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | 2026-07-03 | ~38 天 | deltachat 重构，影响代码质量和可维护性，建议优先评审 |
| Issue | [#3287](https://github.com/sipeed/picoclaw/issues/3287) | 2026-07-22 | ~19 天 | IRC 长消息支持，无 PR 跟进，可考虑指派或招募贡献者 |
| Issue | [#3203](https://github.com/sipeed/picoclaw/issues/3203) | 2026-07-02 | ~39 天 | 虽已关闭，但需确认修复是否已合入主分支，避免回归 |

---

**综合评估：** 项目今日贡献质量较高（安全修复 + 体验优化），但合并节奏偏慢（6 PR 仅 1 合并），建议维护者优先处理 SashaMIT 的 SSRF 修复系列和 deltachat 重构 PR，以提升项目安全基线和代码健康度。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-08-10

## 1. 今日速览

今日 NanoClaw 项目呈现**高活跃度、低交付量**的状态：过去24小时内新增16条PR、1条Issue，但**零合并、零关闭**，所有变更均处于待审阅阶段。核心贡献者 zvi-fried 主导了基础设施重构（模块生命周期、数据库迁移、渠道渲染器注册），OmriBenShoham 推进了 Dial 渠道的 SMS/语音通话集成，安全侧由 gabi-simons 修复了 Critical 级 tar CVE。项目整体处于功能积累期，尚未进入合并交付节奏。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

今日**无 PR 被合并**，所有16条PR均为 OPEN 状态。已提交的变更涵盖以下方向：

| 方向 | PR | 作者 | 状态 |
|------|-----|------|------|
| 基础设施重构 | #3214 (host生命周期)、#3213 (渠道渲染器)、#3212 (DB迁移注册表) | zvi-fried | OPEN |
| 渠道能力扩展 | #3041 (Dial适配器)、#3050 (Dial集成到选择器) | OmriBenShoham | OPEN |
| 安全修复 | #3207 (升级pnpm/npm修复tar CVE)、#3208 (Docker Hub发布+CVE门禁) | gabi-simons | OPEN |
| 附件处理修复 | #2529 (Signal附件传递)、#3142 (Signal附件路径修复) | brentkearney / ira-at-work | OPEN |
| CLI能力 | #3218 (stdin JSON输入) | zvi-fried | OPEN |

**评估**：项目功能储备充足，但合并流水线停滞，核心维护者审阅节奏偏慢。

## 4. 社区热点

- **[#3217](https://github.com/nanocoai/nanoclaw/issues/3217)** — `install_packages` 缺少 pip channel，导致依赖 Python 工具的 agent 无法使用 hardened-image 路径。该 Issue 与 [#3216](https://github.com/nanocoai/nanoclaw/pull/3216)（文档补充说明）直接关联，反映出用户在实际部署中对容器化安全加固路径有真实需求，但当前实现存在功能缺口。
- **[#3041](https://github.com/nanocoai/nanoclaw/pull/3041) + [#3050](https://github.com/nanocoai/nanoclaw/pull/3050)** — Dial 渠道适配器（SMS + AI 语音通话）的完整功能栈，从底层适配到上层集成选择器，显示项目正在向多模态通信渠道扩展。
- **[#3207](https://github.com/nanocoai/nanoclaw/pull/3207)** — 修复 Critical 级 CVE（GHSA-23hp-3jrh-7fpw，tar < 7.5.19），该漏洞同时存在于 npm 和 pnpm 的 vendor 版本中，修复需要同时升级两个工具链，说明维护者对供应链安全较为敏感。

## 5. Bug 与稳定性

| 优先级 | Issue/PR | 描述 | Fix PR |
|--------|----------|------|--------|
| 🔴 Critical | [#3207](https://github.com/nanocoai/nanoclaw/pull/3207) | tar CVE 允许远程代码执行，存在于 base image 的 npm 和 pnpm 中 | #3207 (自身) |
| 🟡 High | [#3142](https://github.com/nanocoai/nanoclaw/pull/3142) | Signal 附件路径从未挂载到容器，导致 Read 工具无法打开 | #3142 (自身) |
| 🟡 High | [#2529](https://github.com/nanocoai/nanoclaw/pull/2529) | Signal 入站附件被丢弃而非传递给 agent | #2529 (自身) |
| 🟠 Medium | [#3217](https://github.com/nanocoai/nanoclaw/issues/3217) | install_packages 不支持 pip，阻碍 hardened-image 采用 | 暂无 fix PR |
| 🟠 Medium | [#3209](https://github.com/nanocoai/nanoclaw/pull/3209) | Slack 粘贴的表格未暴露给 agent | #3209 (自身) |

**稳定性评估**：今日无新增崩溃或回归报告，但存在2个长期未闭合的 Signal 附件相关 Bug（#2529 创建已超2个月），需关注。

## 6. 功能请求与路线图信号

- **Dial 渠道（SMS + AI语音）** [#3041](https://github.com/nanocoai/nanoclaw/pull/3041)、[#3050](https://github.com/nanocoai/nanoclaw/pull/3050) — 明确的路线图信号，项目正向实时通信场景扩展，下一版本大概率包含。
- **stdin JSON 输入模式** [#3218](https://github.com/nanocoai/nanoclaw/pull/3218) — 增强 CLI 可编程性，适合自动化流水线集成。
- **pip channel 支持** — Issue #3217 提出但尚无对应 PR，属于未被采纳的功能请求，若 hardened-image 推广是优先级方向，此功能应被纳入。

## 7. 用户反馈摘要

- **痛点1：hardened-image 路径对 Python 依赖不友好** — Issue #3217 指出，依赖 pip 安装的 agent 工具无法走 hardened-image 预构建路径，迫使用户回到自定义 Dockerfile 模式，与安全加固目标背道而驰。
- **痛点2：Signal 附件静默丢失** — #2529 和 #3142 两个独立 PR 修复同一类问题，说明 Signal 渠道的附件处理存在系统性缺陷，影响企业级消息场景。
- **满意信号**：Dial 渠道扩展、CI/CD 中引入 CVE 门禁（#3208）、重构模块化设计（#3212/#3214）显示项目在工程质量和安全运营方面持续投入。

## 8. 待处理积压

| PR/Issue | 创建时间 | 天数未响应 | 说明 |
|----------|----------|------------|------|
| [#2529](https://github.com/nanocoai/nanoclaw/pull/2529) | 2026-05-18 | ~84天 | Signal 附件传递修复，长期待合 |
| [#3142](https://github.com/nanocoai/nanoclaw/pull/3142) | 2026-07-27 | ~14天 | Signal 附件路径修复 |
| [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) | 2026-07-14 | ~27天 | Dial 渠道适配器，功能完整但待审阅 |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | 2026-07-14 | ~27天 | Dial 集成到选择器，依赖 #3041 |
| [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) | 2026-08-04 | ~6天 | 重构 host seams，待审阅 |

**建议**：优先处理 #2529（Signal 附件长期未合）和 #3041/#3050（Dial 渠道完整功能），这两组 PR 具有明确的用户价值和功能完整性。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期：2026-08-10 | 数据来源：GitHub (nearai/ironclaw)**

---

## 1. 今日速览

过去24小时内，IronClaw 项目保持中高活跃度：**22 条 Issue 更新**（15 条新开/活跃、7 条已关闭），**32 条 PR 更新**（24 条待合并、8 条已合并/关闭）。核心团队聚焦于 Reborn 架构下的工具发现优化（tool-search）、网络传输加固、以及 WebUI v2 稳定性修复。无新版本发布，但多项基础设施改进正在积压，预计将在后续版本中集中释放。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 摘要 |
|---|---|---|
| [#7171](https://github.com/nearai/ironclaw/pull/7171) | fix(skills) | 修复技能安装后消失的问题，为每个技能挂载点建立 DB-backed 树，使技能命令可运行（关闭 #7168） |
| [#7387](https://github.com/nearai/ironclaw/pull/7387) | chore(deps) | 更新基础依赖组（base64 0.22→0.23、toml 1.1.3→1.1.4 等 12 项） |
| [#7022](https://github.com/nearai/ironclaw/pull/7022) | chore(deps) | 更新 GitHub Actions 组（setup-node 4.0.2→7.0.0、docker/login-action） |
| [#5510](https://github.com/nearai/ironclaw/issues/5510) | closed | 旧 Routines 删除机制修复（QA 验证关闭） |
| [#4341](https://github.com/nearai/ironclaw/issues/4341) | closed | Qwen3.6 模型 Think 链暴露及卡住问题已修复 |
| [#4344](https://github.com/nearai/ironclaw/issues/4344) | closed | 修复 Agent 加载时镜像用户消息的问题 |
| [#7292](https://github.com/nearai/ironclaw/issues/7292) | closed | CoinGecko 工具安装后无法使用的 runner heartbeat 错误已修复 |
| [#5552](https://github.com/nearai/ironclaw/issues/5552) | closed | 多工具失败后泛化 "invalid result" 错误已修复 |

**项目推进判断：** 今日修复集中于**技能系统、工具安装、UI 渲染和历史缓存**等稳定性问题，同时 Dependabot 持续更新依赖，整体在加固 Reborn 基础层。

---

## 4. 社区热点

### 高关注度 Issues

| Issue | 标签 | 评论 | 核心诉求 |
|---|---|---|---|
| [#7405](https://github.com/nearai/ironclaw/issues/7405) | enhancement, tool, evaluation | 2 | 改进 deferred tool discovery，提供完整签名和命名空间感知的目录预览，减少模型调用轮次 |
| [#7407](https://github.com/nearai/ironclaw/issues/7407) | enhancement, performance | 2 | 将 `BatchPolicy::Parallel` 能力批次实际并发执行，当前为串行，存在性能瓶颈 |
| [#7400](https://github.com/nearai/ironclaw/issues/7400) | bug, high severity | 2 | `stream: true` + `tools[]` 在 `/api/v1/responses` 中流式中断，留下无法删除的 "zombie" 线程 |
| [#7346](https://github.com/nearai/ironclaw/issues/7346) | bug_bash_P2, qa-bug | 2 | Emoji shortcodes 显示为纯文本，未转换为 emoji 字符 |
| [#7348](https://github.com/nearai/ironclaw/issues/7348) | bug_bash_P2, qa-bug | 2 | Activity 时间线显示顺序错乱，影响调试体验 |
| [#7345](https://github.com/nearai/ironclaw/issues/7345) | bug_bash_P2, qa-bug | 2 | Agent 报告 61 个 automations，UI 仅显示 50，数据不一致 |
| [#7349](https://github.com/nearai/ironclaw/issues/7349) | bug_bash_P2, qa-bug | 2 | 刷新页面导致部分 run 历史和 Activity 时间线消失 |
| [#6046](https://github.com/nearai/ironclaw/issues/6046) | bug_bash_P2, qa-bug | 1 | 简单邮件→Sheet 任务触发 124 次工具调用，过度消耗 token |
| [#6479](https://github.com/nearai/ironclaw/issues/6479) | bug_bash_P2, qa-bug | 1 | Routines 可创建/修改其他 Routines，存在自繁殖自动化风险 |

**热点分析：** 社区关注点集中在 **工具发现效率**（#7405/#7407）、**流式 API 稳定性**（#7400）、**UI 时间线一致性**（#7348/#7349）以及**自动化安全边界**（#6479）。其中 #7400 为高严重度 Bug，直接影响 API 可用性。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 High | [#7400](https://github.com/nearai/ironclaw/issues/7400) | `stream: true` + tools 流式中断，产生无法删除的 zombie 线程（影响 1.1.0-rc.1 及 1.1.0） | 待修复 |
| 🟠 Medium | [#7346](https://github.com/nearai/ironclaw/issues/7346) | Emoji shortcodes 显示为纯文本（Regression） | 待修复 |
| 🟠 Medium | [#7348](https://github.com/nearai/ironclaw/issues/7348) | Activity 时间线顺序错乱 | 待修复 |
| 🟠 Medium | [#7345](https://github.com/nearai/ironclaw/issues/7345) | Agent 与 UI 的 automations 计数不一致（61 vs 50） | 待修复 |
| 🟠 Medium | [#7349](https://github.com/nearai/ironclaw/issues/7349) | 刷新页面导致历史数据丢失 | 待修复 |
| 🟡 Low | [#5882](https://github.com/nearai/ironclaw/issues/5882) | Slack 反复重连后认证流程卡死 | 待修复 |
| 🟡 Low | [#5878](https://github.com/nearai/ironclaw/issues/5878) | 已吊销 GitHub token 产生误导性错误而非重新认证流程 | 待修复 |
| 🟡 Low | [#5551](https://github.com/nearai/ironclaw/issues/5551) | Slack 自动化推送中间进度而非最终结果 | 待修复 |

**稳定性评估：** 今日有 7 条 Issue 关闭（含修复），但仍有 **8 条开放 Bug**，其中 #7400 为高严重度，建议在下一版本优先处理。WebUI 时间线和刷新一致性问题是近期回归重点。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 内容 | 纳入下一版本可能性 |
|---|---|---|---|
| [#7405](https://github.com/nearai/ironclaw/issues/7405) + [#7410](https://github.com/nearai/ironclaw/pull/7410) + [#7409](https://github.com/nearai/ironclaw/pull/7409) | enhancement | 改进 deferred tool discovery，返回完整签名 + 命名空间感知预览 | ⭐⭐⭐ 高（已有 stacked PRs） |
| [#7411](https://github.com/nearai/ironclaw/pull/7411) | feat(tool-search) | 将 deferred-tool retrieval 抽象为可替换 provider | ⭐⭐⭐ 高（与 #7405 配套） |
| [#7407](https://github.com/nearai/ironclaw/issues/7407) | enhancement | 并发执行 `BatchPolicy::Parallel` 能力批次 | ⭐⭐ 中（性能优化，需测试覆盖） |
| [#7398](https://github.com/nearai/ironclaw/pull/7398) | feat(web-push) | 新增 Web Push 通知通道（PWA + W3C Web Push 标准） | ⭐⭐⭐ 高（新功能，已实现） |
| [#7396](https://github.com/nearai/ironclaw/pull/7396) | feat(channels) | Slack/Telegram 渐进式预览功能 | ⭐⭐ 中（实验性功能） |
| [#7392](https://github.com/nearai/ironclaw/issues/7392) | experiment | 替换官方编码工具为 pinned omp tool surface | ⭐ 低（实验性质） |
| [#7360](https://github.com/nearai/ironclaw/issues/7360) | enhancement | 扩展内置能力写入路径的压力测试覆盖 | ⭐⭐ 中（基础设施） |

**路线图判断：** 下一版本（v1.2.0）预计将重点包含 **工具发现优化**（#7405/#7411）、**Web Push 通知**（#7398）和 **渐进式频道预览**（#7396）。并发执行优化（#7407）作为性能改进可能纳入。

---

## 7. 用户反馈摘要

### 痛点汇总

| 痛点类别 | 具体反馈 | 关联 Issue |
|---|---|---|
| **工具调用效率** | 简单任务触发 124 次工具调用，token 浪费严重 | [#6046](https://github.com/nearai/ironclaw/issues/6046) |
| **UI 一致性** | 刷新页面后运行历史和 Activity 时间线部分消失 | [#7349](https://github.com/nearai/ironclaw/issues/7349) |
| **UI 渲染** | Emoji shortcodes 显示为纯文本；时间线顺序错乱 | [#7346](https://github.com/nearai/ironclaw/issues/7346), [#7348](https://github.com/nearai/ironclaw/issues/7348) |
| **数据一致性** | Agent 报告 61 个 automations，UI 仅显示 50 | [#7345](https://github.com/nearai/ironclaw/issues/7345) |
| **自动化安全** | Routines 可创建/修改其他 Routines，存在自繁殖风险 | [#6479](https://github.com/nearai/ironclaw/issues/6479) |
| **错误体验** | 多工具失败后显示泛化错误，无法定位具体失败点 | [#5552](https://github.com/nearai/ironclaw/issues/5552) |
| **认证恢复** | Slack 重连后认证流程卡死；GitHub token 吊销后错误信息误导 | [#5882](https://github.com/nearai/ironclaw/issues/5882), [#5878](https://github.com/nearai/ironclaw/issues/5878) |
| **通知质量** | Slack 自动化推送中间进度而非最终结果 | [#5551](https://github.com/nearai/ironclaw/issues/5551) |

### 满意点
- 技能安装修复后功能恢复正常（#7171 关闭）
- Qwen3.6 模型的 Think 链暴露和消息镜像问题已修复（#4341、#4344）
- 依赖更新持续进行，系统安全性保持跟进

---

## 8. 待处理积压

| 类型 | Issue/PR | 创建时间 | 状态 | 建议 |
|---|---|---|---|---|
| 🔴 高优 Bug | [#7400](https://github.com/nearai/ironclaw/issues/7400) | 2026-08-09 | OPEN | 流式 API zombie 线程问题，影响生产环境，建议优先修复 |
| 🟠 性能 | [#6046](https://github.com/nearai/ironclaw/issues/6046) | 2026-07-13 | OPEN | 工具调用过度问题，需结合 #7405 tool-search 优化一并考虑 |
| 🟠 安全 | [#6479](https://github.com/nearai/ironclaw/issues/6479) | 2026-07-22 | OPEN | Routines 自繁殖风险，需增加 guardrail |
| 🟡 体验 | [#5882](https://github.com/nearai

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 | 2026-08-10

## 1. 今日速览

LobsterAI 今日社区活跃度中等，过去 24 小时共产生 **3 条 Issue 更新**，无 PR 提交、无新版本发布。社区关注点集中在模型配置兼容性与跨模型协作机制两个方向，整体项目处于功能迭代平稳期。无活跃合并或版本发布，项目进展节奏偏缓。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 合并或关闭，项目在代码层面暂无实质性推进。

---

## 4. 社区热点

| Issue | 主题 | 活跃度 |
|-------|------|--------|
| [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) | 建议增加上下文窗口大小与输出 token 设置 | 👍 1, 评论 2, stale 标记 |
| [#2453](https://github.com/netease-youdao/LobsterAI/issues/2453) | 自定义模型被系统判定为不许可 | 评论 1（今日新增） |
| [#2132](https://github.com/netease-youdao/LobsterAI/issues/2132) | 跨模型子任务调用机制问题 | 评论 1, stale 标记 |

**热点分析：**
- **#1187** 反映用户在使用 DeepSeek 模型时遇到 Context Overflow，急需可配置的上下文窗口参数，属于高频痛点。
- **#2453** 是新发 Issue，暴露了模型名称解析逻辑对非标准 Provider 格式（如 `custom_1/openai/gpt-oss-20b:free`）的兼容缺陷，影响 OpenRouter 及 NVIDIA 免费模型用户。
- **#2132** 涉及跨模型子任务调度架构，是较复杂的功能性诉求，社区对该机制有明确优化期望。

---

## 5. Bug 与稳定性

| 级别 | 问题 | Issue | 状态 |
|------|------|-------|------|
| 中 | 模型名称解析误判，自定义模型被拒绝 | [#2453](https://github.com/netease-youdao/LobsterAI/issues/2453) | OPEN，无 fix PR |
| 中 | 上下文窗口大小不可配置，导致运行时溢出报错 | [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) | OPEN (stale)，无 fix PR |
| 低 | 跨模型子任务调用结果无法回传主任务 | [#2132](https://github.com/netease-youdao/LobsterAI/issues/2132) | OPEN (stale)，无 fix PR |

今日无崩溃或回归类高严重度 Bug 报告。

---

## 6. 功能请求与路线图信号

- **上下文窗口可配置化**（#1187）：用户明确请求在模型设置中增加上下文窗口与输出 token 参数，适配 DeepSeek 等大上下文模型。该需求与当前多模型支持方向一致，可纳入下一版本配置项扩展计划。
- **自定义模型格式兼容**（#2453）：用户期望支持更灵活的模型标识符，尤其是 OpenRouter/NVIDIA 等第三方平台的自定义模型。建议在模型注册逻辑中优化 Provider 解析规则。
- **跨模型子任务回调机制**（#2132）：提出主-子任务间主动通知的设计方案，具备架构参考价值，可作为中长期路线图候选项。

---

## 7. 用户反馈摘要

| 场景 | 痛点 |
|------|------|
| DeepSeek 模型使用 | 上下文溢出时仅能 `/reset`，缺乏主动配置窗口大小的入口 |
| 多模型切换 | 自定义模型名称格式被误判，尤其在多线程场景下反复触发，影响使用连续性 |
| 跨模型协作 | 子任务结果无法感知，主任务与子任务间缺乏有效的异步通信机制 |

用户对 LobsterAI 的多模型支持能力有较高期待，当前配置灵活性与错误提示体验存在提升空间。

---

## 8. 待处理积压

| Issue | 创建时间 | 备注 |
|-------|----------|------|
| [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) | 2026-04-01 | stale 标记超 4 个月，高关注需求（👍1） |
| [#2132](https://github.com/netease-youdao/LobsterAI/issues/2132) | 2026-06-09 | stale 标记超 1 个月，涉及架构优化 |

建议维护者优先响应 **#1187** 与 **#2453**，前者为已有共识的功能需求，后者为新发现的兼容性 Bug，及时跟进有助于提升多模型场景下的用户留存。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 | 2026-08-10

## 1. 今日速览

Moltis 今日整体活跃度中等，过去24小时内新增 2 个 Issues、1 个待合并 PR，无版本发布。项目处于常规迭代节奏，社区反馈聚焦于 UI 行为异常与容器运行状态检测问题，同时 vault 安全相关修复正在推进。整体健康度良好，未发现阻塞性问题。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

**PR #1186** `[fix(vault): normalize recovery phrase before hashing]` — 作者 `pxmpsdev`

- **内容**：修复 vault 恢复密钥哈希计算时未对恢复短语进行归一化的问题。此前 `derive_recovery_kek` 函数在派生 KEK 前会规范化短语（去除破折号、统一大写），但存储的哈希值却基于原始短语计算，导致用户输入带格式差异的短语时可能产生验证不一致。
- **影响**：增强 vault 解锁流程的一致性与安全性，减少因输入格式差异导致的误判。
- **状态**：待合并（OPEN），尚无评论。

> 🔗 [PR #1186](https://github.com/moltis-org/moltis/pull/1186)

---

## 4. 社区热点

| Issue | 类型 | 创建时间 | 活跃度 |
|-------|------|----------|--------|
| [#1187](https://github.com/moltis-org/moltis/issues/1187) | Bug | 2026-08-09 | 新开，0 评论 |
| [#1185](https://github.com/moltis-org/moltis/issues/1185) | Bug | 2026-08-08 | 更新于 08-09，0 评论 |

- **#1185** 在 2026-08-09 有更新动作，反映用户持续关注 Apple Container 1.x 沙箱与 Moltis 状态同步的兼容性问题。
- **#1187** 为今日新增，直击 UI 表单字段的静默重置行为，可能影响用户体验与配置准确性。

> 🔗 [#1187](https://github.com/moltis-org/moltis/issues/1187) | [#1185](https://github.com/moltis-org/moltis/issues/1185)

---

## 5. Bug 与稳定性

| Issue | 标题 | 严重程度 | 状态 | Fix PR |
|-------|------|----------|------|--------|
| [#1187](https://github.com/moltis-org/moltis/issues/1187) | Heartbeat settings UI silently resets fields not represented by the form | 中 | 待处理 | — |
| [#1185](https://github.com/moltis-org/moltis/issues/1185) | Apple Container 1.x sandbox starts but Moltis treats it as not running | 中 | 更新中 | — |

- **#1187**：Heartbeat 设置面板在提交时静默重置未被表单直接表示的字段，可能导致配置丢失。尚无修复 PR。
- **#1185**：Apple Container 1.x 沙箱实际运行但 Moltis 误判为未启动，涉及容器状态检测逻辑。目前仍在排查阶段，暂无修复。

---

## 6. 功能请求与路线图信号

今日无新功能请求类 Issue。PR #1186 反映了项目对 **vault 安全体验一致性** 的持续优化方向，建议关注后续是否扩展至其他密钥管理场景。

---

## 7. 用户反馈摘要

- **痛点**：
  - Heartbeat 配置 UI 存在字段静默重置行为，用户可能在不感知情况下丢失设置（#1187）。
  - Apple Container 1.x 沙箱状态检测不准确，影响多容器环境的监控可靠性（#1185）。
- **满意度**：
  - 当前 Issues 无正面反馈或感谢类评论，用户聚焦于问题报告。
- **使用场景**：
  - 多容器编排环境下的状态同步需求（#1185）。
  - 精细化 Heartbeat 配置管理（#1187）。

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建时间 | 备注 |
|----------|------|----------|------|
| [#1185](https://github.com/moltis-org/moltis/issues/1185) | Bug | 2026-08-08 | 更新于 08-09，需跟进容器状态检测逻辑 |
| [#1187](https://github.com/moltis-org/moltis/issues/1187) | Bug | 2026-08-09 | 新开，需 UI/表单逻辑审查 |
| [#1186](https://github.com/moltis-org/moltis/pull/1186) | Fix | 2026-08-09 | 待合并，建议优先审查以保障 vault 安全性 |

> ⚠️ 建议维护者关注上述积压项，尤其是 #1185 的状态检测问题与 #1186 的修复合并。

---

**报告生成时间**：2026-08-10  
**数据来源**：[moltis-org/moltis](https://github.com/moltis-org/moltis) GitHub API

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-08-10

## 1. 今日速览

过去24小时 CoPaw 项目保持高活跃度：**18条 Issue、26条 PR**，其中7条 Issue 已关闭、1条 PR 已合并。开发者对前端渲染、时间戳显示、Google API 兼容等关键体验问题响应迅速，多个 Bug 在同日内收到对应 Fix PR，社区协作效率较高。无新版本发布，但功能增强（审批描述、CIDR 支持、DeepSeek V4 上下文窗口）和稳定性修复持续推进，项目健康度良好。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#6846](https://github.com/agentscope-ai/QwenPaw/issues/6846) | feat | 添加 DeepSeek V4 系列（v4-flash / v4-pro）的 100 万 token 上下文窗口配置，修复之前误用 131K 默认值导致过早压缩的问题 |
| [#6851/#6850/#6849/#6848](https://github.com/agentscope-ai/QwenPaw/issues/6851) | fix | 前端渲染器修复：长多行工具输出被折叠为不可读 blob 的问题，用户多次提交后维护者快速响应 |

### 重要在审/待合并 PR

- [#6854](https://github.com/agentscope-ai/QwenPaw/pull/6854) — **审批目的描述**：为权限审批请求添加一句话用途说明，直接回应用户 #6832 的痛点
- [#6845](https://github.com/agentscope-ai/QwenPaw/pull/6845) — **保留助手完成时间**：修复对话历史重载后 `completed_at` 被覆盖的问题
- [#6844](https://github.com/agentscope-ai/QwenPaw/pull/6844) — **Strip Gemini `$schema`**：移除 Google SDK 不接受的 JSON Schema 元数据字段
- [#6843](https://github.com/agentscope-ai/QwenPaw/pull/6843) — **SSE 实时流式传输**：用纯 ASGI middleware 替代 Starlette `BaseHTTPMiddleware`，解决输出延迟一次性渲染问题
- [#6750](https://github.com/agentscope-ai/QwenPaw/pull/6750) — **会话三大前端 Bug 修复**：会话身份死锁（消息排队不发送）、过早会话保存、超大 prompt 崩溃
- [#6704](https://github.com/agentscope-ai/QwenPaw/pull/6704) — **会话 Fork 功能**：右键会话可复制完整上下文到独立新会话，类似 checkpoint

## 4. 社区热点

| Issue/PR | 状态 | 评论数 | 热度说明 |
|----------|------|--------|----------|
| [#2291](https://github.com/agentscope-ai/QwenPaw/issues/2291) | CLOSED | 66 | 社区贡献任务清单，持续引导新用户参与，评论区活跃 |
| [#6851/#6850/#6849/#6848](https://github.com/agentscope-ai/QwenPaw/issues/6851) | CLOSED | 各2 | 同一前端渲染 Bug 在短时间内被同一用户多次提交，问题影响显著，已快速关闭 |
| [#6840](https://github.com/agentscope-ai/QwenPaw/issues/6840) | OPEN | 1 | 用户深入调研 ReMe4 路线图，询问 Auto-Link、三模态搜索、4 类摘要权重等功能的排期，反映高级用户对记忆系统的深度关注 |
| [#6841](https://github.com/agentscope-ai/QwenPaw/issues/6841) | OPEN | 1 | Auto-Dream 夜间任务中单单元 schema 验证失败导致整体标 error，用户建议增加重试和容错机制 |
| [#6853](https://github.com/agentscope-ai/QwenPaw/issues/6853) | OPEN | 1 | 指出 `prompts.py` 中关于 Dream 自动同步 digest 到 MEMORY.md 的描述与实际实现不符（从未实现），文档/注释准确性问题 |

## 5. Bug 与稳定性

### 已修复（今日关闭）

| Issue | 严重级别 | 说明 | Fix PR |
|-------|----------|------|--------|
| [#6851/#6850/#6849/#6848](https://github.com/agentscope-ai/QwenPaw/issues/6851) | 中 | 前端渲染器将长多行工具输出折叠为不可读 blob | —（已关闭） |
| [#5584](https://github.com/agentscope-ai/QwenPaw/issues/5584) | 中 | 升级后无法连接自定义 ascend-vllm 模型（OpenAI 连接错误） | —（已关闭） |
| [#5579](https://github.com/agentscope-ai/QwenPaw/issues/5579) | 高 | 异常中断（主机重启/进程被杀）导致对话记录丢失，无断点恢复机制 | —（已关闭，可能已有方案） |

### 待修复

| Issue | 严重级别 | 说明 | 关联 PR |
|-------|----------|------|---------|
| [#6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) | 高 | MCP 工具调用时将数字字符串（如 `apiKey`）错误转为数字类型，导致调用失败 | 无 |
| [#6826](https://github.com/agentscope-ai/QwenPaw/issues/6826) | 中 | 助手消息结束时间显示异常（实际耗时2min，页面显示几秒） | [#6845](https://github.com/agentscope-ai/QwenPaw/pull/6845) |
| [#6812](https://github.com/agentscope-ai/QwenPaw/issues/6812) | 高 | Google Gemini API 报错 `Model 'unknown'`，因 tool schema 含 `$schema` 字段 | [#6844](https://github.com/agentscope-ai/QwenPaw/pull/6844) |
| [#6806](https://github.com/agentscope-ai/QwenPaw/issues/6806) | 高 | Windows 插件 `qwenpaw-creator` 保存模型配置时持续返回 500 错误 | 无 |
| [#6847](https://github.com/agentscope-ai/QwenPaw/issues/6847) | 中 | 执行任务时被杀软拦截并强制关停进程（WorkBuddy 无此问题） | 无 |
| [#6852](https://github.com/agentscope-ai/QwenPaw/issues/6852) | 中 | 长文本渲染问题与 #6851 类似但未关闭，可能为补充报告 | — |
| [#6841](https://github.com/agentscope-ai/QwenPaw/issues/6841) | 中 | Auto-Dream 单单元集成失败时整任务标 error，缺少重试/容错 | 无 |
| [#6853](https://github.com/agentscope-ai/QwenPaw/issues/6853) | 低 | `prompts.py` 注释描述与实际 Dream 管道行为不符 | 无 |

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 纳入下一版本可能性 |
|------|----------|------------------|
| 审批时 AI 自动生成一句话用途描述 | [#6832](https://github.com/agentscope-ai/QwenPaw/issues/6832) + [#6854](https://github.com/agentscope-ai/QwenPaw/pull/6854) | ⭐⭐⭐ 高（已有 PR，首_contributor 提交） |
| 会话 Fork（复制上下文到独立会话） | [#6704](https://github.com/agentscope-ai/QwenPaw/pull/6704) | ⭐⭐⭐ 高（功能完整，涉及会话管理核心） |
| SSE 实时流式渲染 | [#6843](https://github.com/agentscope-ai/QwenPaw/pull/6843) | ⭐⭐⭐ 高（直接改善用户体验，ASGI 中间件方案明确） |
| 内置工具文档与参数在 Console 展示 | [#6325](https://github.com/agentscope-ai/QwenPaw/pull/6325) | ⭐⭐ 中（增强型功能，Under Review） |
| ReMe4 完整路线图（Auto-Link、三模态搜索、4类摘要权重） | [#6840](https://github.com/agentscope-ai/QwenPaw/issues/6840) | ⭐⭐ 中（用户主动询问，需维护者回应） |
| 移动端 Web 控制台适配 | [#6281](https://github.com/agentscope-ai/QwenPaw/issues/6281) | ⭐ 低（移动端场景，优先级待评估） |
| Agent hidden 标志（UI 隐藏但后台可用） | [#6842](https://github.com/agentscope-ai/QwenPaw/pull/6842) | ⭐⭐ 中（插件生态需求，first-time contributor） |
| No-auth 主机白名单支持 CIDR | [#6259](https://github.com/agentscope-ai/QwenPaw/pull/6259) | ⭐⭐ 中（安全增强，first-time contributor） |
| ReMe 记忆搜索 reranker 支持 | [#6398](https://github.com/agentscope-ai/QwenPaw/pull/6398) | ⭐⭐ 中（Under Review，后端增强） |
| 主题/skin 可配置模块 | [#6312](https://github.com/agentscope-ai/QwenPaw/pull/6312) | ⭐ 低（Draft 状态，需维护者确认方向） |

## 7. 用户反馈摘要

**痛点集中区：**

1. **工具调用的参数类型问题**（#6839）：MCP 工具参数中数字字符串被错误强转为数字类型，导致 API 调用失败——这是类型处理层面的核心 Bug，影响生产可用性。

2. **杀软误报/拦截**（#6847）：用户对比 WorkBuddy 无此问题，说明 QwenPaw 的某些行为（可能涉及进程创建、脚本执行）触发了安全软件敏感规则，Windows 用户体验受损。

3. **对话持久化脆弱**（#5579）：主机重启或进程被杀后对话记录完全丢失，缺乏断点保存机制——用户对 Agent 执行不可逆操作（如 `reboot`）后的数据恢复有明确诉求。

4. **前端渲染与流式体验**（#6851/#6843）：长文本被折叠、输出不实时流式展示，影响用户对 Agent 执行过程的可观测性。

**正面反馈：**
- 维护者对重复提交的前端渲染 Bug（#6851 系列）响应迅速，同日关闭多个重复 Issue
- #6854（审批描述）和 #6845（时间戳修复）等 PR 精准命中用户 Issue，用户参与感强

## 8. 待处理积压

| Issue | 天数 | 优先级 | 说明 |
|-------|------|--------|------|
| [#6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) — MCP 字符串参数类型错误 | 1天 | 🔴 高 | 无关联 Fix PR，影响工具调用核心路径 |
| [#6806](https://github.com/agentscope-ai/QwenPaw/issues/6806) — Windows 插件保存配置 500 | 3天 | 🔴 高 | 无关联 Fix PR，Windows 用户关键路径 |
| [#6847](https://github.com/agentscope-ai/QwenPaw/issues/6847) — 杀软拦截进程 | 1天 | 🟡 中 | 无关联 Fix PR，需维护者分析误报原因 |
| [#6841](https://github.com/agentscope-ai/QwenPaw/issues/6841) — Auto-Dream 单单元失败容错 | 1天 | 🟡 中 | 建议增加重试机制，无关联 PR |
| [#6853](https://github.com/agentscope-ai/QwenPaw/issues/6853) — prompts.py 描述不符 | 1天 | 🟢 低 | 文档/注释修正，无功能影响 |
| [#6840](https://github.com/agentscope-ai/QwenPaw/issues/6840) — ReMe4 路线图询问 | 1天 | 🟡 中 | 需维护者回应以安抚高级用户期待 |
| [#6281](https://github.com/agentscope-ai/QwenPaw/issues/6281) — 移动端适配 | 21天 | 🟢 低 | 长期未响应，移动端需求明确但优先级待排 |
| [#5579](https://github.com/agentscope-ai/QwenPaw/issues/5579) — 对话断点保存 | 44天 | 🔴 高 | 虽已关闭，但问题涉及架构层面，需确认是否已有方案或仍需跟进 |

---

**项目健康度评估**：今日 Issue/PR 比率（18:26）显示开发活动旺盛，多条高优先级 Bug 在同日内收到对应 Fix PR（#6826→#6845、#6812→#6844），维护者响应及时。DeepSeek V4 支持已合并，SSE 流式、会话 Fork 等功能 PR 进入审查阶段，

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-08-10

---

## 1. 今日速览

过去24小时 ZeroClaw 共更新 100 条 Issue/PR，其中活跃/新开 Issue 38 条、已关闭 12 条；PR 50 条中待合并 49 条、仅 1 条已合并，项目处于**高强度开发但合并节奏偏紧**的状态。今日无新版本发布，但 RFC 流程与安全性讨论持续推进，多个 P1 级 Bug 修复 PR 已就绪待审。整体活跃度较高，维护者正集中处理安全硬编码、通道稳定性与可观测性三大方向。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 摘要 | 链接 |
|---|---|---|---|
| #9866 | Bugfix | 加固可验证意图边界：停止序列化 JWK 私钥标量、修复货币约束空值拒绝、消除 u32 溢出风险 | [PR #9866](https://github.com/zeroclaw-labs/zeroclaw/pull/9866) |
| #9571 | Chore | 移除 WATI 通道模块（含 gateway 路由、CI、容器、安装器等全部关联代码） | [PR #9571](https://github.com/zeroclaw-labs/zeroclaw/pull/9571) |
| #9690 | Bugfix | 修复 Containerfile 中 rustc 1.95.0 低于声明 MSRV 导致 all-features 变体无法构建 | [PR #9690](https://github.com/zeroclaw-labs/zeroclaw/pull/9690) |
| #9192 | Bugfix | 修复 shared_budget TOCTOU 竞争导致 AtomicUsize 回绕及 SopEngine .unwrap 崩溃 | [PR #9192](https://github.com/zeroclaw-labs/zeroclaw/pull/9192) |
| #9834 | Bugfix | 修复 runtime 测试间歇性失败（共享进程全局状态竞争：turn_streamed receipts + model_switch） | [PR #9834](https://github.com/zeroclaw-labs/zeroclaw/pull/9834) |
| #8731 | Bugfix | 修复 stdio-based MCP 服务器作为僵尸进程累积问题 | [PR #8731](https://github.com/zeroclaw-labs/zeroclaw/pull/8731) |
| #8560 | Bugfix | 修复 browser_open 在无法打开窗口时导致 agent turn 无限挂起 | [PR #8560](https://github.com/zeroclaw-labs/zeroclaw/pull/8560) |
| #9860 | Bugfix | 修复文件系统 channel "created" 事件触发后 Web UI 冻结问题 | [PR #9860](https://github.com/zeroclaw-labs/zeroclaw/pull/9860) |

### 关键进行中 PR

- **#9196** — MCP 资源 blob 聚合预算预检，完成后物化至 workspace uploads 目录
- **#9777** — 修复 Signal 通道 sourceUuid 发送者识别问题
- **#9182** — Windows 原生支持 PowerShell 作为 shell
- **#9556** — 新增 Langfuse 可观测性后端（OTel traces）
- **#9809** — 支持单 provider profile 下配置多模型
- **#9544** — 修复 delegate 模式未遵循配置的 provider fallback 路由

**整体判断**：今日关闭的 PR 以安全性和稳定性修复为主，WATI 通道已移除、Zombie MCP、TOCTOU 竞争等隐患得到处理。维护工作正向"安全硬化 + 通道精简 + 可观测性扩展"三个方向收敛，项目整体稳健性在提升。

---

## 4. 社区热点

### 讨论最活跃的 Issue（评论数 Top）

| Issue | 评论数 | 状态 | 核心议题 | 链接 |
|---|---|---|---|---|
| #6808 | 22 | OPEN | Work Lanes / Board Automation / Label Cleanup RFC | [Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) |
| #7100 | 12 | OPEN | Per-model capability & context-window config RFC | [Issue #7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) |
| #9397 | 11 | OPEN | WhatsApp `allowed_groups` 空列表语义：permit-none RFC | [Issue #9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) |
| #8692 | 11 | OPEN | Maintainer RFC 决策队列 Tracker | [Issue #8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| #8054 | 10 | CLOSED | System prompt tool 可用性在多入口点不一致 Bug | [Issue #8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) |
| #8681 | 10 | CLOSED | Goal mode 实现分块提交 Tracker | [Issue #8681](https://github.com/zeroclaw-labs/zeroclaw/issues/8681) |
| #6971 | 10 | OPEN | 安全态势、凭证边界与通用入站策略 RFC | [Issue #6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) |

### 热点分析

- **#6808（22 条评论）**：维护者流程自动化 RFC 长期讨论，社区对 label 清理和工作流路由有强烈诉求，RFC 状态"审议延期/逐步 rollout"反映出决策谨慎。
- **#7100（12 条评论）**：per-model 上下文窗口配置缺失导致 vision 支持误报和 token 预算计算偏差，是高频用户痛点，RFC 已进入高优先级审议。
- **#9397（11 条评论）**：WhatsApp 通道安全配置语义问题，空 `allowed_groups` 默认允许所有群组，社区推动改为"permit-none"，属于安全硬编码的重要修正。
- **#6971（10 条评论）**：安全态势全局 RFC 覆盖凭证、运行时隔离、入站信任链，是架构层的核心治理议题。

---

## 5. Bug 与稳定性

### P0 / 高危 Bug

| Issue | 严重程度 | 摘要 | Fix PR | 链接 |
|---|---|---|---|---|
| #9565 | S0 安全/数据丢失 | gateway webhook 未 fail-closed（WhatsApp Cloud / Linq / WATI），未经认证的消息直接进入 agent | 进行中 | [Issue #9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) |
| #9328 | P1 高危 | verifiable-intent 在未验证凭证链的情况下评估约束 | PR #9866 已提交 | [Issue #9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) |
| #8642 | P1 高危 | MCP/tool-schema 克隆导致 agent loop 无界 RSS 增长（OOM 根因） | 待修复 | [Issue #8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642) |
| #8054 | P1 高危 | System prompt 工具可用性在多入口点不一致（推理模型误报"No tools"） | 已合并 #8053 | [Issue #8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) |
| #7897 | P3 高危 RFC | 无需全量 daemon reload 即可应用安全策略/通道配置更新 | RFC 阶段 | [Issue #7897](https://github.com/zeroclaw-labs/zeroclaw/issues/7897) |

### P1 / 中危 Bug

| Issue | 严重程度 | 摘要 | Fix PR | 链接 |
|---|---|---|---|---|
| #9284 | S2 | config flush 并发写入覆盖 | 待修复 | [Issue #9284](https://github.com/zeroclaw-labs/zeroclaw/issues/9284) |
| #9085 | S1 | pgvector 启用时 gateway/agent 启动时 nested runtime panic | 待修复 | [Issue #9085](https://github.com/zeroclaw-labs/zeroclaw/issues/9085) |
| #9486 | P2 高危 | 高熵检测器误删 Solana 钱包地址，`high_entropy_tokens=false` 在 channel 路径不生效 | 待修复 | [Issue #9486](https://github.com/zeroclaw-labs/zeroclaw/issues/9486) |
| #9779 | P1 高危 | `sops_dir` 文档默认值未被 daemon 遵守，SOP 静默不加载 | 待修复 | [Issue #9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) |
| #8560 | S1 | browser_open 在无法打开窗口时挂起 agent turn | 已关闭 | [Issue #8560](https://github.com/zeroclaw-labs/zeroclaw/issues/8560) |

### P2 / 低危 Bug

| Issue | 严重程度 | 摘要 | Fix PR | 链接 |
|---|---|---|---|---|
| #9198 | S3 | Discord 输入指示器在 daemon reload 后卡死 | 待修复 | [Issue #9198](https://github.com/zeroclaw-labs/zeroclaw/issues/9198) |
| #9656 | P2 | Telegram 审批等待期间 typing 指示器持续运行造成误导 | 已关闭 | [Issue #9656](https://github.com/zeroclaw-labs/zeroclaw/issues/9656) |
| #9860 | S2 | 文件系统 channel 创建事件后 Web UI 冻结 | 已关闭 | [Issue #9860](https://github.com/zeroclaw-labs/zeroclaw/issues/9860) |

---

## 6. 功能请求与路线图信号

| 请求 | 来源 | 状态 | 关联 PR / Issue | 链接 |
|---|---|---|---|---|
| Per-model 上下文窗口 & 能力配置 | #7100 | RFC 审议中 | #7100 | [Issue #7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) |
| 单 Provider Profile 多模型支持 | #9809 | PR 进行中 | PR #9809 | [PR #9809](https://github.com/zeroclaw-labs/zeroclaw/pull/9809) |
| Langfuse 可观测性后端 | #9556 | PR 进行中 | PR #9556 | [PR #9556](https://github.com/zeroclaw-labs/zeroclaw/pull/9556) |
| Windows PowerShell 原生 shell 支持 | #9182 | PR 进行中 | PR #9182 | [PR #9182](https://github.com/zeroclaw-labs/zeroclaw/pull/9182) |
| MCP 资源 blob 预算预检 | #9196 | PR 进行中 | PR #9196 | [PR #9196](https://github.com/zeroclaw-labs/zeroclaw/pull/9196) |
| 公开区块链地址发布例外策略 | #9825 | RFC 阶段 | #9825 | [Issue #9825](https://github.com/zeroclaw-labs/zeroclaw/issues/9825) |
| 安全策略热加载（无需 daemon reload）| #7897 | RFC 阶段 | #7897 | [Issue #7897](https://github.com/zeroclaw-labs/zeroclaw/issues/7897) |
| 发布认证机制整合（53→20 assets）| #9101 | 已接受 | #9101 | [Issue #9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) |
| workspace 级 `forbid(unsafe_code)` | #7130 | 已接受 | #7130 | [Issue #7130](https://github.com/zeroclaw-labs/zeroclaw/issues/7130) |
| Secret KeySource trait 抽象 | #9194 | PR 进行中 | PR #9194 | [PR #9194](https://github.com/zeroclaw-labs/zeroclaw/pull/9194) |

**路线图判断**：
- **短期（v0.8.x）**：PR #9809（多模型 per provider）、PR #9556（Langfuse）、PR #9182（PowerShell）、PR #9196（MCP blob）有较大可能随下一版本发布。
- **中期**：RFC #7100（per-model 配置）和 RFC #7897（热加载）一旦通过审议，将成为重要的架构升级。
- **安全方向**：RFC #9397（WhatsApp 安全语义）、RFC #9825（区块链地址例外）、PR #9866（可验证意图硬化）均指向安全硬化的持续强化。

---

## 7. 用户反馈摘要

### 真实痛点
1. **Solana 钱包地址被误红黑**（#9486 / #9825）：用户无法在 Telegram 中获取自己的钱包地址，支付请求 URL 被破坏，社区强烈要求定义"公开区块链地址"的发布例外策略。
2. **SOP 静默不加载**（#9779）：`sops_dir` 文档默认值未实现，导致定时 SOP 和通道 SOP 完全失效且无任何日志告警，严重影响自动化工作流可靠性。
3. **Memory 合并引入人格漂移**（#9758）：Consolidation 将一次性行为推广为持久人格描述，用户反馈 agent 在多次轮次后行为偏离预期设定。
4. **MCP 资源预算无预检**（#9196 提出）：MCP 工具调用后资源 blob 直接写入 workspace，缺乏预算前置检查，存在资源消耗失控风险。
5. **WATI 通道维护成本高**（#9571 移除）：用户群体较小但维护负担重，移除后社区反响中性，更多精力可投向核心通道。
6. **Telegram/Discord 输入指示器体验问题**（#9198 / #9656）：审批等待期间 typing 指示器持续闪烁误导用户，关闭后 Discord 指示器卡死。

### 满意之处
- Goal mode 实现分块提交（#8681）获得了认可，说明迭代式推进方式有效。
- System prompt tool 可用性不一致问题（#8054）已修复并关闭，用户反馈直接得到响应。
- WATI 通道移除后代码库更精简，CI 负担减轻。

---

## 8. 待处理积压

| Issue | 创建日期 | 评论数 | 优先级 | 风险 | 备注 | 链接 |
|---|---|---|---|---|---|---|
| #6808 | 2026-05-20 | 22 | P2 | Medium | RFC 审议延期近 3 个月，Work Lanes 自动化长期阻塞 | [Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) |
| #9565 | 2026-07-30 | 3 | P0 | High | Gateway webhook 未 fail-closed，安全高风险，仍在进行中 | [Issue #9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) |
| #8642 | 2026-07-03 | 4 | P1 | High | MCP schema 克隆导致 RSS 无界增长，OOM 根因未彻底修复 | [Issue #8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642) |
| #7100 | 2026-06-02 | 12 | P1 | High | Per-model 上下文配置 RFC，用户痛点强烈，推进缓慢 | [Issue #7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) |
| #6971 | 2026-05-27 | 10 | P2 | High

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*