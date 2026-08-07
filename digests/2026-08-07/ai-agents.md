# OpenClaw 生态日报 2026-08-07

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-07 02:56 UTC

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



# OpenClaw 项目日报 — 2026-08-07

## 1. 今日速览

过去24小时 OpenClaw 保持极高社区活跃度：Issues 更新 500 条（活跃 430 / 关闭 70），PR 更新 500 条（待合并 397 / 已合并或关闭 103）。无新版本发布。今日整体健康度：**社区反馈密度高，P0 级回归与消息丢失类 bug 密集出现，需维护者优先关注核心运行时稳定性**。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭了 6 个 PR，主要涉及网关锁目录规范化与向量索引状态诊断修复：

| PR | 类型 | 进展说明 |
|---|---|---|
| [#119226](https://github.com/openclaw/openclaw/pull/119226) | fix | `resolveGatewayLockDir` 改为基于解析后的 `OPENCLAW_STATE_DIR`，修复沙盒场景下锁文件泄漏到系统 tmp 的问题 |
| [#118409](https://github.com/openclaw/openclaw/pull/118409) | fix | 保留沙盒网关锁文件，不出现在用户共享 tmp 目录（依赖 #119226） |
| [#119240](https://github.com/openclaw/openclaw/pull/119240) | fix | `openclaw memory status` 快速路径现能报告向量库可用状态 |
| [#118421](https://github.com/openclaw/openclaw/pull/118421) | fix | 快速路径利用持久化 chunk 判断向量库 ready |
| [#117572](https://github.com/openclaw/openclaw/pull/117572) | fix | 区分已持久化向量索引与运行时 live 状态，避免 "unknown" 误导 |
| [#119573](https://github.com/openclaw/openclaw/pull/119573) | fix | ACP session 初始化时传递配置的 model，修复 model override 不生效的回归 |

**推进方向**：今日合并主要覆盖**基础设施与可观测性**层面（网关锁隔离、memory status 诊断），核心运行时/消息传递层的修复 PR 仍处于 open 状态，待合并在即。

---

## 4. 社区热点

| Issue | 热度 | 核心诉求 |
|---|---|---|
| [#75](https://github.com/openclaw/openclaw/issues/75) — Linux/Windows Clawdbot Apps | 116 评论，80 👍 | 补齐 macOS/iOS/Android 之外的桌面端原生应用 |
| [#116277](https://github.com/openclaw/openclaw/issues/116277) — DeepSeek v4 Flash 静默回复失败 | 114 评论 | 模型调用失败时无错误信息，用户体验差 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging by Source | 28 评论 | 按来源（用户命令/网页抓取/第三方 skill）对记忆条目打信任标签，防 memory poisoning |
| [#27445](https://github.com/openclaw/openclaw/issues/27445) — sub-agent 完成 announce 路由 | 12 评论，5 👍 | `announceTarget` 选项，使子 agent 完成通知路由到父会话而非直接发到 channel |

**热点分析**：
- **#75** 长期积压的跨平台需求，用户期待原生桌面体验与 macOS 功能对等。
- **#116277** 反映 DeepSeek 模型集成中的核心稳定性问题，用户高度关注模型 fallback 和错误可观测性。
- **#7707** 和 **#27445** 代表高级用户群体对**多 agent 编排**和**记忆安全**的深层需求，与项目向 agent orchestration 平台演进的方向一致。

---

## 5. Bug 与稳定性

按严重程度排列，今日重点关注：

### 🔴 P0 — 阻塞性 / 数据丢失

| Issue | 标题 | 状态 | 修复 PR |
|---|---|---|---|
| [#119263](https://github.com/openclaw/openclaw/issues/119263) | Agent DB v14→v15 迁移失败，gateway 无法启动 | OPEN | 无 |
| [#118772](https://github.com/openclaw/openclaw/issues/118772) | `sessionEntry.totalTokens` 膨胀导致 4-8% 上下文窗口即触发过早 compaction（数据丢失） | OPEN | 无 |
| [#115700](https://github.com/openclaw/openclaw/issues/115700) | `chat.send` 报 "thread switched branches" — `expectedLeafEntryId` 未及时刷新 | OPEN | [#116382](https://github.com/openclaw/openclaw/pull/116382) 已开 |
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | DeepSeek v4 Flash 静默失败，无 reply 且无错误信息 | CLOSED | 无 |

### 🟠 P1 — 消息丢失 / 运行异常

| Issue | 标题 | 状态 | 修复 PR |
|---|---|---|---|
| [#90944](https://github.com/openclaw/openclaw/issues/90944) | `sessions_yield` resume 回复未投递，用户收到子 agent raw 摘要而非父回复 | OPEN | 无 |
| [#92186](https://github.com/openclaw/openclaw/issues/92186) | 前台 reply fence 取消对较早并发群消息的回复投递（WhatsApp） | OPEN | 无 |
| [#86012](https://github.com/openclaw/openclaw/issues/86012) | LINE 消息因 reply token 过期静默丢失，无 push fallback | OPEN | 无 |
| [#117358](https://github.com/openclaw/openclaw/issues/117358) | 回合后 compaction 忽略 reset 边界，延迟已完成的回复投递（回归） | OPEN | 无 |
| [#115546](https://github.com/openclaw/openclaw/issues/115546) | CLI-budget compaction 在 4.9s–50s 内超时，100% 失败率 | OPEN | 无 |
| [#88657](https://github.com/openclaw/openclaw/issues/88657) | DeepSeek V4 Flash 不完整 turn（payloads=0, stopReason=stop）| OPEN | 无 |

### 🟡 P2 — 行为异常 / 体验摩擦

| Issue | 标题 | 状态 |
|---|---|---|
| [#119087](https://github.com/openclaw/openclaw/issues/119087) | Gateway 冷启动从 2026.7.1 到 2026.7.2 回归约 2.5× | OPEN |
| [#87756](https://github.com/openclaw/openclaw/issues/87756) | prompt 启动的 Lobster workflow 在嵌套 `/tools/invoke` 处挂起 | OPEN |
| [#119796](https://github.com/openclaw/openclaw/issues/119796) | Windows vitest teardown 因 SQLite handle 未释放报 EBUSY | OPEN |
| [#117609](https://github.com/openclaw/openclaw/issues/117609) | 嵌入式 assistant 阶段 transient LLM/socket 错误不重试，长 turn 直接失败 | OPEN |
| [#116512](https://github.com/openclaw/openclaw/issues/116512) | Telegram progress 模式首条 commentary 重复 | OPEN |
| [#88079](https://github.com/openclaw/openclaw/issues/88079) | WebChat 中 Kimi Code / DeepSeek Reasoner 的 `reasoning_content` 未流式渲染（回归） | OPEN |
| [#118772](https://github.com/openclaw/openclaw/issues/118772) | 2026.7.1+ embedded-agent-runner session token 膨胀致过早 compaction | OPEN |
| [#117209](https://github.com/openclaw/openclaw/issues/117209) | AuthProfileStoreUnreadable 在 snapshot publication 失败后 sticky | OPEN |
| [#117445](https://github.com/openclaw/openclaw/issues/117445) | `@openclaw/feishu` 解码 inbound DM 为 "?"，`replies=0` | OPEN |
| [#109881](https://github.com/openclaw/openclaw/issues/109881) | Bedrock `bedrock-converse-stream` 无 thinking-signature replay 保护，永久 brick Claude 4+ session | OPEN |

---

## 6. 功能请求与路线图信号

| Issue | 功能诉求 | 路线图判断 |
|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Memory Trust Tagging by Source（按来源打信任标签防 poisoning） | 安全类 feature，长期价值高，暂无 PR，短期纳入可能性低 |
| [#27445](https://github.com/openclaw/openclaw/issues/27445) | `announceTarget` sub-agent 完成路由选项 | 多 agent 编排核心需求，[#116382](https://github.com/openclaw/openclaw/pull/116382) 相关修复已在途 |
| [#15032](https://github.com/openclaw/openclaw/issues/15032) | Per-spawn tool restrictions for sub-agents | 安全隔离刚需，长期需求，暂无 PR |
| [#45565](https://github.com/openclaw/openclaw/issues/45565) | Gateway lifecycle warnings 路由到专属 channel | 运维可观测性，低门槛 feature |
| [#88154](https://github.com/openclaw/openclaw/issues/88154) | Slack Modal Support for Interactive Workflows | 渠道功能增强 |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | Agent 自主触发 context compaction（self-compact tool） | 高级 agent 能力，有用户主动 filed |
| [#45771](https://github.com/openclaw/openclaw/issues/45771) | 内置 pace-aware rate limiting for autonomous agents | 多 agent 自治场景刚需 |
| [#44289](https://github.com/openclaw/openclaw/issues/44289) | 从 secret target registry 自动生成 secretref 文档 | 开发体验改进 |
| [#89584](https://github.com/openclaw/openclaw/pull/89584) | memory search 可选 cross-encoder rerank 阶段 | **PR 已开，可纳入近期版本** |
| [#119325](https://github.com/openclaw/openclaw/pull/119325) | `/model -s` session-only 模型选择 | **PR 已开，填补 session 级模型选择空白** |

---

## 7. 用户反馈摘要

**高频痛点**：
- **消息丢失** 是最集中的抱怨：WhatsApp reply fence 导致早期并发消息无法投递（#92186），LINE reply token 过期静默丢失（#86012），`sessions_yield` resume 回复未送达（#90944）。用户反复强调 "user gets child raw summary, not parent reply" 和 "silently lost"。
- **DeepSeek 模型集成问题**：v4 Flash 静默失败（#116277）、不完整 turn（#88657）、WebChat 推理流不渲染（#88079），用户期望更高的模型稳定性和错误可观测性。
- **Compaction 过度/过激**：`totalTokens` 膨胀导致 4-8% 上下文即触发 compaction（#118772），CLI-budget compaction 频繁在 4.9s 内超时（#115546），用户认为这是数据丢失风险。
- **Windows 兼容性**：SQLite handle 未释放（#119796）、`memory-lancedb` Docker bind mount 失败（#58139）、agent 发出 Unix 命令（#117644），Windows 用户群体诉求强烈。
- **DB 迁移阻塞启动**：v14→v15 迁移失败导致 gateway 无法启动（#119263），影响生产用户。

**正面反馈**：
- 用户认可 OpenClaw 已成为日常 workflow 核心（家庭/业务助手，Telegram 集成、自动化、Home Assistant 控制），来源见 [#73537](https://github.com/openclaw/openclaw/issues/73537)。
- Memory search 的 cross-encoder rerank 功能请求（#89584）显示用户对记忆质量有进阶需求。

---

## 8. 待处理积压

以下 Issue 长期未获维护者响应，建议优先处理：

| Issue | 严重程度 | 评论数 | 创建时间 | 备注 |
|---|---|---|---|---|
| [#119263](https://github.com/openclaw/openclaw/issues/119263) | **P0** | 6 | 2026-08-04 | DB v14→v15 迁移失败，gateway 无法启动，影响线上用户 |
| [#118772](https://github.com/openclaw/openclaw/issues/118772) | **P0** | 5 | 2026-08-03 | token 膨胀致 4-8% 即 compaction，数据丢失风险 |
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | P1 | 114 | 2026-07-30 | DeepSeek v4 Flash 静默失败，

---

## 横向生态对比



# 2026-08-07 个人 AI 智能体开源生态横向分析报告

## 1. 生态全景

2026年8月，个人 AI 智能体开源生态呈现"核心项目高频迭代、安全与稳定性成为共识焦点"的态势。OpenClaw、Hermes、ZeroClaw、CoPaw、IronClaw 等主力项目保持日活百级以上的开发节奏，安全修复（密钥泄露、SSRF、认证绕过）与运行时稳定性（消息丢失、会话崩溃）是跨项目共同痛点。生态整体从功能快速扩张期进入"架构治理 + 稳定性加固"的双轨阶段，god-file 分解、插件安全扫描、多租户上下文隔离等工程化能力正成为新标杆。

---

## 2. 各项目活跃度对比

| 项目 | Issues | PR | Release | 健康度评估 |
|------|--------|-----|---------|-----------|
| **OpenClaw** | 500（活跃430） | 500（待合并397） | 无 | ⚠️ 高活跃但P0级消息丢失/DB迁移bug密集，稳定性承压 |
| **Hermes Agent** | 50（活跃47） | 50（待合并39） | 无 | ✅ 高强度开发，god-file治理+安全扫描双线推进 |
| **ZeroClaw** | 36 | 50 | 无 | ✅ 高强度，SOP子系统bug集中爆发需关注 |
| **IronClaw** | 50（新开27） | 50（待合并33） | v1.1.0 | ✅ 里程碑发布，从功能扩展转向稳定性加固 |
| **CoPaw** | 28（14关闭） | 50（30关闭） | 无 | ✅ 高频迭代，企业级多租户与文件管理落地 |
| **NanoBot** | 10（8活跃） | 18（待合并11） | 无 | ✅ 安全修复集中，P0会话覆盖风险待处理 |
| **NanoClaw** | 2（状态变化） | 14（8已合并） | 无 | ✅ 中等活跃，升级可靠性修复已提交 |
| **LobsterAI** | 6 | 4（2已合并） | 无 | ✅ 健康，响应节奏正常 |
| **PicoClaw** | 0 | 2（1已合并） | 无 | ✅ 平稳，QQ Channel能力补全 |
| **NullClaw** | 0 | 0 | 无 | ⬜ 无活动 |
| **Moltis** | 0 | 0 | 无 | ⬜ 无活动 |
| **ZeptoClaw** | 0 | 0 | 无 | ⬜ 无活动 |

---

## 3. OpenClaw 在生态中的定位

**规模标杆**：OpenClaw 日活 500+ Issues/PR 远超其他项目，是生态中用户基数与贡献量最大的平台。

**技术路线差异**：
- 与 NanoBot/Hermes 相比，OpenClaw 更强调**多渠道网关**（WhatsApp/LINE/Telegram/Slack/飞书）与**多 agent 编排**（sub-agent announce、sessions_yield）
- 与 IronClaw/ZeroClaw 相比，OpenClaw 的 **memory 系统**（向量索引、cross-encoder rerank）和 **DB 迁移机制** 更复杂，但也带来更高的稳定性风险
- 与 PicoClaw（轻量级、嵌入式）相比，OpenClaw 定位为**全功能个人助手平台**

**社区规模对比**：OpenClaw 的 Issue 评论数（#116277 达 114 条、#75 达 80 👍）显著高于其他项目，反映其用户覆盖广但反馈密度也更高，维护者资源相对紧张。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **消息/通知可靠性** | OpenClaw、IronClaw、ZeroClaw | 消息丢失（OpenClaw #92186/#86012）、审批通知消失（IronClaw #5553）、cron SOP 网络操作失败（ZeroClaw #9780） |
| **安全加固** | NanoBot、Hermes、ZeroClaw、OpenClaw | API 密钥泄露（NanoBot #5270/#5269）、插件安全扫描（Hermes #80728）、SSRF/凭证验证（ZeroClaw #8826/#9328）、memory poisoning（OpenClaw #7707） |
| **模型集成稳定性** | OpenClaw、LobsterAI、ZeroClaw | DeepSeek 静默失败（OpenClaw #116277/#88657）、斜杠模型ID兼容（LobsterAI #2443）、per-model context 配置（ZeroClaw #7100） |
| **会话/上下文管理** | OpenClaw、NanoBot、Hermes、CoPaw | token 膨胀致过早 compaction（OpenClaw #118772）、会话数据被后台任务覆盖（NanoBot #5271）、token_count 未持久化（Hermes #80724）、user_id 穿透多租户（CoPaw #6525） |
| **多 Agent 编排** | OpenClaw、ZeroClaw | sub-agent 完成路由（OpenClaw #27445）、A2A 出站客户端（ZeroClaw #9106） |
| **架构治理** | Hermes、OpenClaw | god-file 分解（Hermes #78647）、基础设施规范化（OpenClaw 网关锁目录修复） |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构特点 |
|------|----------|----------|--------------|
| **OpenClaw** | 全渠道网关 + 多 agent 编排 + 记忆系统 | 个人用户/家庭助手/自动化场景 | 复杂 DB 迁移、向量索引、多协议适配 |
| **Hermes Agent** | 插件生态 + god-file 治理 + 桌面端 | 开发者/技术用户 | Python CLI + Rust 后端，强调可维护性 |
| **IronClaw** | 稳定性 + Inspector 诊断 + MCP 扩展 | 生产环境用户 | operator inspection API、libSQL FTS |
| **ZeroClaw** | SOP 自动化 + 安全硬化 + A2A | 自动化工作流用户 | RFC 治理流程、SOP.toml 配置驱动 |
| **CoPaw** | 企业级多租户 + AG-UI 协议 + 文件管理 | 团队/企业用户 | user_id/channel/tenant 穿透、RESTful 文件 API |
| **NanoBot** | 轻量级 + WebUI 体验 + 临时会话 | 个人用户/快速部署 | 会话隔离、临时内存模式 |
| **NanoClaw** | 调度可靠性 + Telegram 深度集成 | Telegram 用户群体 | 调度器失败恢复、频道 ID 命名空间 |
| **PicoClaw** | 轻量嵌入式 + QQ Channel | 嵌入式/轻量场景用户 | 简单渠道适配，PR #1349 补全多媒体 |
| **LobsterAI** | 配置管理 + Windows 兼容 | Windows 用户 | openclaw 配置清理、安装程序修复 |

---

## 6. 社区热度与成熟度分层

### 🟢 快速迭代期（高频开发，功能快速扩张）
- **OpenClaw**：500+ 日活，但稳定性问题密集，处于"边扩展边补课"阶段
- **Hermes Agent**：50+ 日活，god-file 分解史诗推进，架构治理与功能扩展并行
- **CoPaw**：高频迭代，企业级能力快速补齐

### 🟡 质量巩固期（里程碑发布，稳定性优先）
- **IronClaw**：v1.1.0 发布，从功能扩展转向诊断/可靠性加固，P1/P2 bug 积压需清理
- **ZeroClaw**：高强度开发但 SOP 子系统 bug 集中爆发，安全硬化队列推进中

### 🟠 稳健维护期（中等活跃度，响应及时）
- **NanoBot**：安全修复集中，P0 会话覆盖风险待处理
- **NanoClaw**：维护者响应快，升级可靠性修复在途

### 🔵 低活跃度/ niche 项目
- **LobsterAI**、**PicoClaw**：问题较少，维护节奏稳定
- **NullClaw**、**Moltis**、**ZeptoClaw**：无活动，可能处于休眠或私有化状态

---

## 7. 值得关注的趋势信号

### 趋势一：安全从"功能后补"转向"设计前置"
Hermes 的插件安全扫描（#80728）、ZeroClaw 的 verifiable-intent 凭证链验证（#9328）、NanoBot 的 API 密钥泄露修复（#5270/#5269）表明，生态对**信任边界**的认知正在深化。开发者应关注：插件沙箱、密钥隔离、SSRF 防护已成为开源 agent 项目的标配能力。

### 趋势二：消息/会话可靠性成为核心竞争力
OpenClaw 的消息丢失 bug（#92186/#86012/#90944）、IronClaw 的审批通知消失（#5553）、ZeroClaw 的 cron SOP 网络失败（#9780）共同指向一个结论：**用户信任建立在"消息不丢、状态不垮"的基础上**。开发者在构建 agent 时，应优先保障消息投递的可观测性与失败重试机制。

### 趋势三：多租户与上下文穿透是企业级化的必经之路
CoPaw 的 user_id/channel/tenant 透明穿透（#6525）和 Hermes 的插件接口扩展（#64182）反映了**从个人工具向团队协作平台演进**的趋势。企业用户需要会话隔离、审计追踪、权限控制等能力，这将是下一阶段项目的竞争焦点。

### 趋势四：架构治理（god-file 分解）成为长期可持续性的关键
Hermes 的 god-file 分解史诗（#78647，53 条评论）和 OpenClaw 的网关锁目录规范化（#119226/#118409）表明，**代码可维护性已从内部问题转变为用户可感知的价值**。项目维护者应重视技术债务清理，社区贡献者应积极参与架构治理。

### 趋势五：模型集成的稳定性与可观测性仍是短板
OpenClaw 的 DeepSeek 静默失败（#116277）、LobsterAI 的斜杠模型 ID 兼容（#2443）、ZeroClaw 的 per-model context 配置（#7100）共同揭示了**模型层集成仍是脆弱环节**。开发者在选择或集成 LLM provider 时，应优先关注错误可观测性、fallback 机制和上下文窗口管理的可靠性。

---

**报告生成时间：2026-08-07 | 分析师：Agnes (Sapiens AI)**

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-07

---

## 1. 今日速览

NanoBot 项目今日保持较高活跃度：24 小时内共产生 10 条 Issues（8 条新/活跃、2 条关闭）与 18 条 PR（11 条待合并、7 条已合并/关闭），整体贡献量充沛。今日安全类议题集中涌现，涉及 API 密钥泄露、会话存储隔离等核心风险，均已有修复 PR 跟进。WebUI 体验优化（临时会话、拖拽排序、性能瘦身）与多频道适配（Matrix、微信）稳步推进，项目整体处于稳健向前状态。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

**今日合并/关闭的重要 PR（7 条）：**

| PR | 类型 | 摘要 |
|----|------|------|
| [#5272](https://github.com/HKUDS/nanobot/pull/5272) | 🐛 Bug Fix | 修复会话保留裁剪时丢弃 `_channel_delivery` 主动消息的问题，解决 Issue #5273 |
| [#5231](https://github.com/HKUDS/nanobot/pull/5231) | ✨ Feature | 为 Dream 归档空闲会话，确保 `history.jsonl` 稳定产出 |
| [#5261](https://github.com/HKUDS/nanobot/pull/5261) | ✨ WebUI | 支持侧边栏会话拖拽排序与拖入 Composer 创建结构化会话提及 |
| [#5248](https://github.com/HKUDS/nanobot/pull/5248) | 🐛 Bug Fix | 修复 Matrix 机器人邀请后不自动加入的问题（Continuwity 兼容性） |
| [#5267](https://github.com/HKUDS/nanobot/pull/5267) | 🎨 WebUI | 收紧交互动画（220ms 统一过渡、减少不必要的布局位移） |
| [#5259](https://github.com/HKUDS/nanobot/pull/5259) | 🐛 Bug Fix | 强制临时会话状态仅保留在进程内存，不写入会话历史 |
| [#5262](https://github.com/HKUDS/nanobot/pull/5262) | ⚡ Performance | 减少 WebUI 冷启动负载（预压缩 gzip、拆分 React 共享运行时） |

**项目整体推进评估：** 今日 7 条已关闭 PR 覆盖了 session 数据完整性、频道兼容性、WebUI 交互与性能四个维度，项目健康度良好，核心缺陷得到及时修复。

---

## 4. 社区热点

**讨论活跃 / 关注度较高的 Issues：**

- **[#5278](https://github.com/HKUDS/nanobot/issues/5278)** — Session history should not live inside the agent workspace
  - 安全类 Issue，指出 PR #713 将会话存储移至工作区目录后存在隔离风险，已有对应修复 PR [#5279](https://github.com/HKUDS/nanobot/pull/5279) 跟进。
- **[#5270](https://github.com/HKUDS/nanobot/pull/5270)** — Fix CLI API 密钥泄露至子进程
  - P1 安全修复，涉及 `CliAppService.run` 将完整环境变量传递至不受信子进程的风险。
- **[#5269](https://github.com/HKUDS/nanobot/pull/5269)** — Fix 多 Provider 场景下 API 密钥写入全局 `os.environ`
  - P1 安全修复，与 #5270 为同一安全审计发现的配套修复。
- **[#5198](https://github.com/HKUDS/nanobot/issues/5198)** — 无法在特定会话中切换模型
  - 用户期望与 Cloud SaaS AI 类似的可即时切换模型体验，当前仅支持 top choice + fallback 模式，诉求明确但尚未有 PR 响应。

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 描述 | 状态 |
|--------|----------|------|------|
| 🔴 P0 | [#5271](https://github.com/HKUDS/nanobot/pull/5271) | 后台任务（如 `maybe_generate_webui_title`）在 `await` 窗口内持有旧 Session 引用，用户执行 `/new` 后可导致陈旧写入覆盖新会话数据 | 🟡 Open |
| 🔴 P1 | [#5270](https://github.com/HKUDS/nanobot/pull/5270) | CLI 子进程泄露完整环境变量（含 API 密钥） | 🟡 Open |
| 🔴 P1 | [#5269](https://github.com/HKUDS/nanobot/pull/5269) | 多 Provider 场景下 API 密钥污染全局 `os.environ` | 🟡 Open |
| 🟡 P2 | [#5264](https://github.com/HKUDS/nanobot/issues/5264) | `/api/sessions/{key}/messages` 不返回媒体根目录外的 `media_urls` | 🟡 Open，已有修复 PR [#5268](https://github.com/HKUDS/nanobot/pull/5268) |
| 🟡 P2 | [#5273](https://github.com/HKUDS/nanobot/issues/5273) | 会话裁剪逻辑丢弃主动频道交付消息 | ✅ 已修复 [#5272](https://github.com/HKUDS/nanobot/pull/5272) |
| 🟡 P2 | [#5247](https://github.com/HKUDS/nanobot/issues/5247) | Matrix 机器人被邀请时不自动加入房间（Continuwity 兼容性） | ✅ 已修复 [#5248](https://github.com/HKUDS/nanobot/pull/5248) |
| 🟡 P2 | [#4290](https://github.com/HKUDS/nanobot/issues/4290) | Cronjob 在子代理生成时提前结束，主代理无法处理子代理结果 | 🟡 Open，长期未解决 |
| 🟡 P2 | [#5265](https://github.com/HKUDS/nanobot/pull/5265) | 工具参数接受 `NaN` / `Infinity` 导致非有限 float 传入模型 | 🟡 Open |

> **稳定性评估：** 今日安全类 Bug 修复集中推进（3 条 P1 PR），session 数据一致性问题（#5271）值得关注。P0 级会话覆盖风险尚未合并，建议优先审查。

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 分析 |
|------|----------|------|
| **临时聊天模式** | [#5252](https://github.com/HKUDS/nanobot/pull/5252) + [#5259](https://github.com/HKUDS/nanobot/pull/5259) | 快速迭代中，临时会话内存隔离已完成，预计下一版本纳入 |
| **模型预设编辑器内联展开** | [#5277](https://github.com/HKUDS/nanobot/pull/5277) | WebUI 体验优化，状态 Open，有望随 WebUI 改版一起发布 |
| **MetaSearch 多引擎聚合** | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | 新增 mst-python 作为搜索 Provider，利用 RRF 融合多引擎结果，具备独立发布价值 |
| **共享项目级终端** | [#5253](https://github.com/HKUDS/nanobot/pull/5253) | 引入持久化 PTY 终端（xterm.js dock），支持多用户协作，功能体量大，需充分测试 |
| **Matrix 线程上下文隔离** | [#5275](https://github.com/HKUDS/nanobot/issues/5275) | 用户期望线程级对话隔离，与 Discord/Slack 行为对齐，属于频道体验增强 |
| **令牌消耗详细日志** | [#5266](https://github.com/HKUDS/nanobot/issues/5266) | 用户反馈异常高 Token 消耗（2小时百万级），需增加逐调用粒度日志以便排查 |
| **会话级临时文件隔离** | [#5276](https://github.com/HKUDS/nanobot/issues/5276) | 在多会话共享工作区场景下请求更强的隔离，与 #5278 安全诉求相关 |

---

## 7. 用户反馈摘要

**痛点：**
- **模型切换不灵活** — [#5198](https://github.com/HKUDS/nanobot/issues/5198)：用户期望在单个会话中即时切换模型，当前仅支持 top choice + fallback，体验与主流 SaaS AI 有差距。
- **Token 消耗不可见** — [#5266](https://github.com/HKUDS/nanobot/issues/5266)：用户在无感知活动中消耗百万级 Token，缺乏逐调用粒度日志，难以定位异常来源。
- **Cronjob 子代理后主代理不响应** — [#4290](https://github.com/HKUDS/nanobot/issues/4290)：长期未解决的问题，影响自动化工作流可靠性。

**满意度：**
- 临时会话内存隔离（[#5259](https://github.com/HKUDS/nanobot/pull/5259)）和冷启动性能优化（[#5262](https://github.com/HKUDS/nanobot/pull/5262)）获得认可。
- WebUI 拖拽交互（[#5261](https://github.com/HKUDS/nanobot/pull/5261)）提升日常使用效率。
- Matrix 频道兼容性修复（[#5248](https://github.com/HKUDS/nanobot/pull/5248)）解决了 Continuwity 用户的接入障碍。

---

## 8. 待处理积压

| Issue/PR | 天数（截至今日） | 严重度 | 备注 |
|----------|-----------------|--------|------|
| [#4290](https://github.com/HKUDS/nanobot/issues/4290) — cronjob 子代理提前结束 | ~58 天 | P2 | 长期未响应，影响自动化场景 |
| [#5198](https://github.com/HKUDS/nanobot/issues/5198) — 会话内模型切换 | ~37 天 | — | 用户高频诉求，暂无 PR 跟进 |
| [#5266](https://github.com/HKUDS/nanobot/issues/5266) — Token 消耗日志 | ~1 天 | — | 新提诉求，建议纳入 roadmap |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) — 陈旧后台任务覆盖会话数据 | ~1 天 | P0 | 已提交 PR，建议优先审查合并 |
| [#5270](https://github.com/HKUDS/nanobot/pull/5270) — CLI API 密钥泄露 | ~1 天 | P1 | 已提交 PR，安全修复优先 |
| [#5269](https://github.com/HKUDS/nanobot/pull/5269) — Provider API 密钥全局污染 | ~1 天 | P1 | 已提交 PR，安全修复优先 |

---

**项目健康度总结：** 今日 NanoBot 贡献活跃，安全修复集中推进（3 条 P1 PR），WebUI 体验持续打磨，频道兼容性稳步改善。P0 级会话数据一致性问题和长期未解的 cronjob bug 需维护者关注。整体项目处于健康迭代状态。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-07

---

## 1. 今日速览

Hermes Agent 今日保持高强度开发节奏：过去24小时共产生 100 条活动记录（50 Issues + 50 PRs），其中 47 条 Issue 保持活跃状态，3 条已关闭；PR 方面 39 条仍在待合并队列，11 条已合并/关闭。**无新版本发布**，项目继续以 `main` 分支迭代推进。核心亮点包括：god-file 分解史诗级任务持续推进（Issue #78647、#78645、#78637 等批量创建），MCP stdio 崩溃修复（PR #80729）已就绪，插件安全扫描功能上线（PR #80728），以及 Dyad AI App Builder 集成技能新增（PR #80727）。整体项目健康度良好，基础设施重构与社区功能扩展双线并行。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（11 条）

| PR | 类型 | 摘要 | 链接 |
|---|---|---|---|
| #80725 | fmt | `npm run fix` 自动格式化修复（CI 自动合并） | [链接](https://github.com/NousResearch/hermes-agent/pull/80725) |
| #80719 | bug/desktop | 修复桌面端运行状态标签与计时器重叠问题 | [链接](https://github.com/NousResearch/hermes-agent/pull/80719) |
| #80718 | bug/desktop | 修复"显示更早消息"按钮遮挡会话内容的问题 | [链接](https://github.com/NousResearch/hermes-agent/pull/80718) |
| #68708 | bug/cli/gateway | 修复 macOS launchd 自更新后服务未注册导致 gateway 离线的问题 | [链接](https://github.com/NousResearch/hermes-agent/pull/68708) |

### 待合并的重要 PR（精选）

| PR | 类型 | 摘要 | 链接 |
|---|---|---|---|
| #80729 | bug/mcp | **修复 MCP stdio bridge 崩溃**：`args: null` 时 `TypeError` → 修正为 `[]` | [链接](https://github.com/NousResearch/hermes-agent/pull/80729) |
| #80728 | feat/plugins | **插件安装/更新安全扫描**：灵感来自 Claude Cowork，拦截恶意插件 | [链接](https://github.com/NousResearch/hermes-agent/pull/80728) |
| #80727 | feat/skills | **Dyad 集成技能**：连接 local AI App Builder (21k★)，支持 SQLite 状态管理 | [链接](https://github.com/NousResearch/hermes-agent/pull/80727) |
| #80724 | bug/sessions | **修复 token_count 未持久化**：20,930 条消息的 `token_count` 全为 NULL，影响 context compaction 决策 | [链接](https://github.com/NousResearch/hermes-agent/pull/80724) |
| #80731 | bug/agent | 修复误判空 `.git` 目录为有效 git 仓库的问题 | [链接](https://github.com/NousResearch/hermes-agent/pull/80731) |
| #80713 | bug/desktop | 修复 Windows 桌面端关闭聊天窗口时的确认逻辑 | [链接](https://github.com/NousResearch/hermes-agent/pull/80713) |
| #80686 | feat/cli | 移植 grok-cli verify 子系统：run-recipe 检测 + 环境清单 + `hermes verify` 冒烟测试 | [链接](https://github.com/NousResearch/hermes-agent/pull/80686) |
| #79221 | bug/agent | 修复 `tool_call_id` 去重作用域过大（应为当前 turn 而非整个 session） | [链接](https://github.com/NousResearch/hermes-agent/pull/79221) |
| #80681 | bug/config | 修复 `hermes config set agent.system_prompt` 误报"未识别键"警告 | [链接](https://github.com/NousResearch/hermes-agent/pull/80681) |
| #80721 | feat/agent | 长会话跨午夜时自动注入日期变更提示，不触碰 prompt cache | [链接](https://github.com/NousResearch/hermes-agent/pull/80721) |

**项目整体推进评估**：今日合并/关闭了 11 条 PR，其中 4 条修复了桌面端已知 UX 问题，1 条修复 macOS 服务管理关键 bug。待合并的 39 条 PR 中，安全扫描、MCP 崩溃修复、token 持久化等均为高优先级项目，预计将在近期版本中集中释放。god-file 分解工作持续扩张，已形成多条并行分支推进。

---

## 4. 社区热点

### 评论最活跃的 Issue

**1. Issue #78647 — Epic: Shard all 20 god files（53 条评论）**
> [链接](https://github.com/NousResearch/hermes-agent/issues/78647)
>
> **核心诉求**：仓库级 god-file 分解史诗任务，2026-08 政策明确"所有 god file 必须被拆解，禁止回退"。这是项目架构治理的核心方向，社区参与度极高。

**2. Issue #64182 — Plugin Interface Expansion Tracking（27 条评论）**
> [链接](https://github.com/NousResearch/hermes-agent/issues/64182)
>
> **核心诉求**：插件接口扩展的社区需求追踪，汇总 Discord #plugins-interface-ideas 线程的长期排队 PR 计划。反映社区对插件生态扩展的强烈需求。

**3. Issue #78645 — Shard agent/context_compressor.py（19 条评论）**
> [链接](https://github.com/NousResearch/hermes-agent/issues/78645)
>
> **核心诉求**：6,789 行的 context compressor 作为 god-file 被点名分解，是 #78647 史诗任务的具体子项之一。

**4. Issue #78637 — Shard hermes_cli/auth.py（8 条评论）**
> [链接](https://github.com/NousResearch/hermes-agent/issues/78637)
>
> **核心诉求**：9,180 行的 auth.py 分解任务，是 CLI 组件 god-file 治理的关键一环。

### 评论最活跃的 PR

- **#80729** — MCP null args 崩溃修复（已提交，关联 #80652）
- **#80728** — 插件安全扫描功能（关联 Claude Cowork 设计模式）

---

## 5. Bug 与稳定性

### 高严重度 Bug（P2）

| Issue | 描述 | 状态 | Fix PR | 链接 |
|---|---|---|---|---|
| #79407 | **0.20.0 回归**：桌面端底部操作面板完全消失，app 变为纯查看壳 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/79407) |
| #79339 | **0.20 内存提供者静默失效**：`sync_turn()` 从未被调用，外部 memory provider 停止接收完成回合 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/79339) |
| #80652 | **MCP stdio bridge 崩溃**：`args: null` 时 `TypeError`，服务器进入连接-停放循环 | OPEN | #80729 已提交 | [链接](https://github.com/NousResearch/hermes-agent/issues/80652) |
| #79628 | **use_gateway 配置回退失效**：Tool Gateway 未认证时不 fallback 到直接凭证 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/79628) |
| #77484 | **安全缺陷**：`process(action=list)` 未对 raw command/output 做 redaction | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/77484) |
| #13924 | **飞书命令审批按钮报错 220340** | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/13924) |
| #25886 | **飞书卡片授权按钮报错 200343** | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/25886) |
| #7675 | **飞书三大问题**：卡片交互误判、审批按钮失效、流式卡片回复 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/7675) |
| #75468 | **桌面端会话固定功能失效**：后端 PATCH 返回 400，错误被吞 | CLOSED | ✅ | [链接](https://github.com/NousResearch/hermes-agent/issues/75468) |
| #74411 | **Desktop SSH 模式版本检查参数顺序错误**，误报不支持 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/74411) |
| #80646 | **agent_context 硬编码为"primary"**，cron/flush/subagent 上下文跳过逻辑成为死代码 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/80646) |
| #80259 | **消息表情回应远程桌面会话不可用**：`HERMES_DESKTOP` 仅本地设置 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/80259) |
| #77162 | **安全缺陷**：tool-result → provider 出口路径缺少 exact-value secret redaction | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/77162) |
| #79859 | **桌面端 Talk to Hermes 仍使用延迟 MP3 播放**，不支持低延迟对话式播放 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/79859) |
| #41331 | **邮箱插件 IMAP/SMTP 登录用户名硬编码**，不支持自定义域名别名 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/41331) |
| #38305 | **飞书 error 200340 在 v0.15.2 仍存在**，PR #10256 待合并 | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/38305) |
| #10073 | **飞书移动端命令审批卡片报错 200340** | OPEN | — | [链接](https://github.com/NousResearch/hermes-agent/issues/10073) |

### 中等/低严重度 Bug（P3）

- **#80596** — 学习图将外部安装的 skill 标记为"已学习"（use_count 膨胀）
- **#77286** — 更新程序错误提交

**关键风险点**：飞书平台 bug 集中爆发（#13924、#25886、#7675、#38305、#10073），共 5 个独立 Issue 均指向飞书卡片交互和 error 200340/220340，**建议优先关注**。桌面端 0.20.0 回归问题（#79407、#79339）直接影响用户体验，需尽快定位。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 描述 | 路线图信号 |
|---|---|---|---|
| #64182 | feature/plugins | **插件接口扩展**：社区需求追踪，长排队 PR 稳定发布计划 | ✅ 已在规划，有明确 tracking issue |
| #80727 | feat/skills | **Dyad AI App Builder 集成**：连接 21k★ 开源项目，支持本地 SQLite 状态管理 | ✅ PR 已提交，正在 review |
| #80728 | feat/plugins | **插件安全扫描**：install/update 时扫描插件树，拦截恶意插件 | ✅ PR 已提交，安全方向明确 |
| #80721 | feat/agent | **长会话日期变更通知**：跨午夜自动注入，不触碰 prompt cache | ✅ PR 已提交，用户体验优化 |
| #80686 | feat/cli | **hermes verify 冒烟测试**：移植 grok-cli verify 子系统 | ✅ PR 已提交，开发体验增强 |
| #70849 | feature/cron | **多路复用 gateway cron 支持 per-job deliver_profile** | 📋 待响应，多平台用户刚需 |
| #80723 | feature/gateway | **同一 live session 多设备同时观看**：当前仅支持单传输槽 | 📋 用户强烈诉求，涉及 WS 路由架构 |
| #80720 | feature/desktop | **Kanban 附件可操作化**：打开/预览/Quick Look/Reveal | 📋 桌面端功能增强 |
| #53317 | refactor | **image_gen/TTS 插件-provider 迁移**：对齐 video_gen 纯 registry 模式 | 📋 技术债清理，PR 已存在 |
| #78792 | refactor/telegram | **Telegram adapter.py 分解计划**：六波集群地图 | ✅ 已在 god-file 分解史诗中 |

**路线图判断**：项目正朝三个方向并进——(1) **架构治理**（god-file 分解、插件接口扩展）；(2) **安全加固**（插件扫描、secret redaction）；(3) **多平台生态**（飞书/Telegram/Dyad 集成）。`hermes verify` 和日期变更通知等小功能 PR 已就绪，预计近期版本会集中合并。

---

## 7. 用户反馈摘要

### 真实痛点

1. **飞书平台交互稳定性堪忧**：多个独立 Issue（#13924、#25886、#7675、#38305、#10073）反复报告相同的 error 200340/220340，用户被迫使用 `/approve session` 等手动命令绕过。飞书卡片按钮交互是高频痛点。

2. **0.20.0 桌面端严重回归**：#79407 用户报告"底部操作面板完全消失，app 变成纯查看壳"；#79339 报告 memory provider 静默失效——**升级后无报错但功能丧失**，用户体验极差。

3. **MCP 配置容错性差**：#80652 用户报告 `args: null` 时 stdio bridge 崩溃，进入连接循环，说明配置校验不足。

4. **飞书邮箱自定义域名不支持**：#41331 用户指出 IMAP/SMTP 登录用户名硬编码为 `EMAIL_ADDRESS`，无法使用自定义域名别名场景。

5. **桌面端会话固定功能后端失效**：#75468（已关闭）用户反馈 pin/unpin 仅写入 localStorage，后端 API 返回 400 被吞，导致数据不持久。

### 正面反馈/满意点

- god-file 分解工作得到社区高度关注（#78647 有 53 条评论），说明用户对代码可维护性有强烈诉求，也认可架构治理方向。
- 插件安全扫描（#80728）功能契合社区对插件生态安全的期待。
- Dyad 集成（#80727）展示了 Hermes 对本地 AI 生态的开放态度。

---

## 8. 待处理积压

### 需维护者关注的长期未响应 Issue

| Issue | 创建日期 | 评论数 | 严重度 | 风险提示 |
|---|---|---|---|

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-07

---

## 1. 今日速览

2026年8月7日，PicoClaw 项目整体保持平稳运行态势，过去24小时内无新 Issue 提交，活动主要由 2 条 PR 更新驱动。1 条增强类 PR（#1349）已完成合并/关闭，为 QQ Channel 渠道贡献了更多附件类型的解析与回复能力；另有 1 条 PR（#3200）仍处于开放状态，聚焦于模型回退链的可配置化改进。项目健康度良好，无紧急 Bug 或回归问题，社区活跃度处于中等偏低水平，核心维护工作集中在功能扩展层面。

---

## 2. 版本发布

今日无新版本发布（Releases: 0）。

---

## 3. 项目进展

**已合并/关闭的 PR：**

| PR | 类型 | 描述 |
|---|---|---|
| [#1349](https://github.com/sipeed/picoclaw/pull/1349) | enhancement | QQ Channel 附件支持增强 |

- **功能推进：** PR #1349 补全了 QQ Channel 渠道在多媒体消息处理上的能力，涵盖：
  1. 支持解析 QQ Channel 中的 Emoji 结构
  2. 支持接收语音、图片、视频、文件四类消息
  3. 支持回复本地多媒体附件（发送前自动上传）
  4. 优先使用 Markdown 消息回复，降级兼容处理

- **项目意义：** 该 PR 显著提升了 PicoClaw 在 QQ 生态中的消息兼容性与用户体验，填补了此前多媒体附件处理能力的空白。

**待合并 PR：**

| PR | 类型 | 描述 |
|---|---|---|
| [#3200](https://github.com/sipeed/picoclaw/pull/3200) | feat | 模型默认回退链可配置化 |

- 尚未合并，仍处于开放状态，预计将在下一迭代中纳入发布。

---

## 4. 社区热点

**今日讨论热点：PR #3200 — 模型默认回退链可配置化**

- **链接：** [sipeed/picoclaw PR #3200](https://github.com/sipeed/picoclaw/pull/3200)
- **状态：** OPEN
- **作者：** lc6464
- **创建时间：** 2026-07-01
- **最后更新：** 2026-08-06

**诉求分析：**
用户期望在 Web UI 和管理端 API 中实现对模型回退链的灵活配置，包括设置默认模型、添加备选模型、调整优先级顺序以及持久化保存配置。这一功能反映了多模型部署场景下用户对高可用性和故障转移的迫切需求，表明社区正在从"基础可用"向"生产级可靠性"演进。

---

## 5. Bug 与稳定性

今日无 Bug 报告、崩溃或回归问题。

---

## 6. 功能请求与路线图信号

**潜在路线图信号：**

| PR | 功能方向 | 优先级判断 |
|---|---|---|
| [#3200](https://github.com/sipeed/picoclaw/pull/3200) | 模型容错与高可用 | 高 — 生产环境核心需求 |

- PR #3200 提出的"可配置默认回退链"功能若被合并，将显著增强项目的容错能力，建议维护者优先审查并尽快纳入下一版本。

---

## 7. 用户反馈摘要

今日无新增 Issue 评论，无直接用户反馈可提炼。

从现有 PR 动态推断：
- **满意方向：** QQ Channel 多媒体附件支持的扩展获得了积极回应（PR #1349 已合并）
- **潜在痛点：** 模型回退机制的缺失已被社区成员主动推动（PR #3200），反映出多模型场景下的容错需求尚未被充分满足

---

## 8. 待处理积压

**需关注项：**

| 类型 | PR/Issue | 状态 | 最后更新 | 建议 |
|---|---|---|---|---|
| PR | [#3200](https://github.com/sipeed/picoclaw/pull/3200) | OPEN | 2026-08-06 | 创建时间已超 1 个月，建议维护者尽快审查 |

- **风险提示：** PR #3200 自 2026-07-01 创建以来仍处于开放状态，历时已超过 1 个月。作为涉及核心稳定性功能的关键 PR，建议优先处理，以避免功能积压影响发布节奏。

---

**报告生成时间：** 2026-08-07  
**数据来源：** [sipeed/picoclaw](https://github.com/sipeed/picoclaw) GitHub API

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：2026-08-07 | 数据来源：github.com/qwibitai/nanoclaw**

---

## 1. 今日速览

过去24小时项目保持中等活跃度：**8个PR已合并/关闭，6个待合并，2个Issue状态变化（1关闭、1活跃）**。今日核心进展集中在**调度可靠性**与**Telegram集成**两个方向的批量修复，同时移除了废弃的Qodo技能依赖。无新版本发布。整体项目健康度良好，维护者响应及时，bug修复类PR占比高，代码质量在持续改善。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭的重要PR（8条）

| PR | 类型 | 推进内容 |
|----|------|----------|
| [#2678](https://github.com/nanocoai/nanoclaw/pull/2678) | Fix | 调度器从失败任务中重新派发生成，修复了永久失败任务无法自动恢复的问题 |
| [#2679](https://github.com/nanocoai/nanoclaw/pull/2679) | Fix | 新增 `notifyFailedTasks` 调度钩子，将永久失败的定时任务以通知形式推送给用户，而非仅记录日志 |
| [#2644](https://github.com/nanocoai/nanoclaw/pull/2644) | Fix | Telegram 修复 `extractReplyContext` 丢失引用消息作者的问题，支持识别"回复机器人消息" |
| [#2643](https://github.com/nanocoai/nanoclaw/pull/2643) | Fix | 修复路由 `evaluateEngage` 中 pattern 模式忽略 @mention/DM/回复场景的 bug |
| [#2213](https://github.com/nanocoai/nanoclaw/pull/2213) | Fix | Telegram/Chat SDK 支持纯媒体消息（无文字说明的图片/视频/文件），修复消息被静默丢弃的问题 |
| [#2591](https://github.com/nanocoai/nanoclaw/pull/2591) | Fix | 用户ID命名空间从裸冒号前缀改为频道类型前缀，避免跨频道ID冲突 |
| [#3172](https://github.com/nanocoai/nanoclaw/pull/3172) | Refactor | 移除依赖 Qodo SaaS 和 Google MCP 的废弃技能，降低用户配置复杂度 |
| [#2873](https://github.com/nanocoai/nanoclaw/pull/2873) | Fix | 分离 skills 的 pre-flight 检查与凭据加载，使 `/update-skills` 可独立刷新代码而无需重新认证 |

**整体推进幅度**：调度系统可靠性显著提升（2条PR形成完整闭环：失败恢复 + 用户通知），Telegram 渠道消息处理链路修复了3个长期存在的交互缺陷，技能基础设施完成清理和可更新性改进。

---

## 4. 社区热点

### Issue

**[#3194](https://github.com/nanocoai/nanoclaw/issues/3194) — `/update-nanoclaw` 升级可能存在不可恢复的状态（OPEN，活跃）**
- 作者 glifocat（核心维护者）指出：更新命令在验证通过前就切换了运行仓库，回滚机制仅保护 Git，不保护 SQLite 数据库、gitignored 配置及外部组件
- 存在四个失败窗口，可能导致升级后系统无法自恢复
- **状态**：已有配套 PR [#3195](https://github.com/nanocoai/nanoclaw/pull/3195) 正在修复，将升级改为事务性操作

**[#3171](https://github.com/nanocoai/nanoclaw/issues/3171) — Qodo 技能依赖未配置的 SaaS 服务（CLOSED）**
- 用户反馈 `get-qodo-rules` 和 `qodo-pr-resolver` 技能依赖外部 Qodo 账号，但仓库未提供配置指引
- **状态**：已合并 PR [#3172](https://github.com/nanocoai/nanoclaw/pull/3172) 移除这两个技能

---

## 5. Bug 与稳定性

### 今日报告

| 严重级别 | Issue/PR | 描述 | Fix 状态 |
|----------|----------|------|----------|
| 🔴 高 | [#3194](https://github.com/nanocoai/nanoclaw/issues/3194) | `/update-nanoclaw` 非事务性升级可能导致不可恢复的系统状态 | PR [#3195](https://github.com/nanocoai/nanoclaw/pull/3195) [OPEN] 已提出修复 |
| 🟡 中 | [#3171](https://github.com/nanocoai/nanoclaw/issues/3171) | Qodo 技能依赖外部服务导致开箱即用体验差 | ✅ 已关闭，PR [#3172](https://github.com/nanocoai/nanoclaw/pull/3172) 已合并 |
| 🟡 中 | #2213（历史）| Telegram 纯媒体消息被静默丢弃 | ✅ 已关闭，PR [#2213](https://github.com/nanocoai/nanoclaw/pull/2213) 已合并 |
| 🟢 低 | #2644/#2643（历史）| Telegram 回复检测和直接寻址失效 | ✅ 已关闭，PR [#2644](https://github.com/nanocoai/nanoclaw/pull/2644)、[#2643](https://github.com/nanocoai/nanoclaw/pull/2643) 已合并 |

---

## 6. 功能请求与路线图信号

| 请求/信号 | PR | 状态 | 评估 |
|-----------|-----|------|------|
| Tavily MCP 搜索工具集成 | [#3190](https://github.com/nanocoai/nanoclaw/pull/3190) | OPEN | 社区贡献，符合 Utility skill 规范，可能纳入下一版本 |
| Skills 可独立刷新（无需重认证） | [#2873](https://github.com/nanocoai/nanoclaw/pull/2873) | ✅ 已合并 | 已落地，为后续技能热更新打下基础 |
| Skill 能力与 Host 解耦 | [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) | OPEN | 架构层重构，为插件化能力扩展做准备 |
| Telegram 富文本/富媒体支持 | [#3193](https://github.com/nanocoai/nanoclaw/pull/3193) | OPEN | Chat SDK 更新，增强 Telegram 渠道体验 |

**路线图信号**：项目正朝三个方向演进——① 技能生态扩展（Tavily MCP）；② 架构解耦（skill-host seam）；③ 渠道深度优化（Telegram 富消息）。

---

## 7. 用户反馈摘要

| 反馈来源 | 用户痛点/场景 | 情绪 |
|----------|--------------|------|
| [#3171](https://github.com/nanocoai/nanoclaw/issues/3171) | 开箱即用体验：捆绑技能依赖未配置的外部 SaaS 服务，新用户配置成本高 | ❌ 不满意 |
| [#3194](https://github.com/nanocoai/nanoclaw/issues/3194) | 升级可靠性：`/update-nanoclaw` 命令在中途失败时可能破坏系统，缺乏事务性保证 | ⚠️ 担忧 |
| #2213（已修复）| Telegram 使用场景：用户发送无文字的图片/视频时消息被静默丢弃，影响多模态交互体验 | ❌→✅ 已解决 |
| #2644/#2643（已修复）| Telegram 交互：回复机器人消息和 @mention 场景下 bot 无响应，影响对话连续性 | ❌→✅ 已解决 |

---

## 8. 待处理积压

### 长期未合并的 PR（建议关注）

| PR | 作者 | 创建时间 | 描述 | 建议 |
|----|------|----------|------|------|
| [#2705](https://github.com/nanocoai/nanoclaw/pull/2705) | premald | 2026-06-07（~2个月） | 修复 `use-native-credential-proxy` 技能未能真正绕过 OneCLI 网关的问题 | 优先级高，涉及凭据安全 |
| [#3149](https://github.com/nanocoai/nanoclaw/pull/3149) | winjer | 2026-07-29 | 为 `groups config add-mount` 添加 `--rw` 标志 | 中等优先级，增强挂载灵活性 |
| [#3190](https://github.com/nanocoai/nanoclaw/pull/3190) | manisrinivasan2k1 | 2026-08-05 | 新增 Tavily MCP 工具技能 | 优先级中，社区贡献，待审合并 |
| [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) | zvi-fried | 2026-08-04 | 为 skill-owned capabilities 添加 host seams（架构重构） | 优先级中，影响范围大，需充分测试 |
| [#3193](https://github.com/nanocoai/nanoclaw/pull/3193) | ump45nose | 2026-08-06 | 更新 Telegram Chat SDK 以支持富消息 | 优先级中，增强渠道能力 |
| [#3195](https://github.com/nanocoai/nanoclaw/pull/3195) | glifocat | 2026-08-06 | 使 NanoClaw 升级操作事务性（修复 #3194） | **优先级最高**，直接解决升级可靠性问题 |

---

**日报生成时间：2026-08-07 | 分析师：Agnes (Sapiens AI)**

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-08-07

## 1. 今日速览

IronClaw 今日发布 1.1.0 首个稳定版本，标志着项目自 1.0.0 以来完成重要里程碑。过去 24 小时 Issues 活跃度 50 条（新开/活跃 27、已关闭 23），PR 活跃度 50 条（待合并 33、已合并/关闭 17），整体开发节奏稳健。Inspector 诊断体系、Slack 交付修复、FTS 查询修正等核心改进集中落地。社区对 Routine 稳定性、Slack 集成的反馈高度集中，是下一阶段重点优化方向。

---

## 2. 版本发布

### v1.1.0 — 2026-08-06

**更新内容：**
- 将 `1.1.0-rc.1` 提升为稳定版，整合 RC 以来的修复
- **MCP 扩展能力**：支持注册任意托管 MCP 服务器，通过 IronHub deep links 一键安装
- **持久文件附件**：支持跨频道传递的 durable file attachments
- **Slack 集成增强**：新增 Slack 频道交付能力

**破坏性变更：** 无

**迁移注意事项：** 从 1.0.x 升级无需手动迁移，建议检查 Slack OAuth 绑定状态及 MCP 服务器配置

> [GitHub Release: v1.1.0](https://github.com/nearai/ironclaw/releases/tag/ironclaw-v1.1.0)

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#7235](https://github.com/nearai/ironclaw/pull/7235) | 已合并 | 新增 operator inspection API 与实时诊断流，为调试和运维提供基础设施 |
| [#7289](https://github.com/nearai/ironclaw/pull/7289) | 已合并 | 修复 libSQL FTS 查询中的自然语言召回缺陷，解决生产环境问题 |
| [#7303](https://github.com/nearai/ironclaw/pull/7303) | 已合并 | 修复 Docker 镜像缺少 curl 导致健康检查持续报错的问题 |
| [#7259](https://github.com/nearai/ironclaw/pull/7259) | 已合并 | 修复 docs/ 发布边界泄漏，将内部文档正确隔离 |

**项目整体推进：** Inspector 诊断体系已初步成型（#7235 → #7236 → #7239 → #7277 形成完整链路），Slack 交付修复（#7300）与 FTS 召回修复（#7289/#7288）解决了生产环境的高频痛点，项目从功能扩展向稳定性加固阶段过渡。

---

## 4. 社区热点

### 高评论 Issues

| Issue | 状态 | 评论数 | 热度分析 |
|-------|------|--------|----------|
| [#5553](https://github.com/nearai/ironclaw/issues/5553) | OPEN | 4 | 审批通知不可靠消失，影响用户对工作流控制的信任 |
| [#5702](https://github.com/nearai/ironclaw/issues/5702) | OPEN | 4 | GitHub 集成 HTTP 403，阻碍开发者使用核心功能 |
| [#5522](https://github.com/nearai/ironclaw/issues/5522) | OPEN | 3 | Reborn 模式读取 Slack DM 时 capability_info 重试循环失败 |
| [#3533](https://github.com/nearai/ironclaw/issues/3533) | CLOSED | 3 | Telegram 自动配对流程已失效，文档陈旧 |
| [#5701](https://github.com/nearai/ironclaw/issues/5701) | OPEN | 3 | 活动面板不实时更新、隐藏工具调用细节，影响可观测性 |
| [#5834](https://github.com/nearai/ironclaw/issues/5834) | OPEN | 3 | Slack 断开请求被 Agent 错误拒绝 |

**诉求分析：** 用户最关注的是 **通知可靠性**（#5553）、**集成稳定性**（#5702、#5834）和 **可观测性**（#5701）。这些问题均影响生产环境信任度，需优先处理。

---

## 5. Bug 与稳定性

### 按严重程度排列

**P1 — 高严重**
| Issue | 描述 | Fix PR |
|-------|------|--------|
| [#5456](https://github.com/nearai/ironclaw/issues/5456) | Routine 执行因 lease 过期而失败（90秒阈值对多工具任务过于激进） | 未关联 |
| [#3533](https://github.com/nearai/ironclaw/issues/3533) | Telegram 自动设置流程失效 | 已关闭 |
| [#5877](https://github.com/nearai/ironclaw/issues/5877) | Slack 通知送达错误用户（安全风险） | 未关联 |

**P2 — 中等严重**
| Issue | 描述 | Fix PR |
|-------|------|--------|
| [#5553](https://github.com/nearai/ironclaw/issues/5553) | 审批通知消失 | 未关联 |
| [#5702](https://github.com/nearai/ironclaw/issues/5702) | GitHub 搜索/创建返回 403 | 未关联 |
| [#5701](https://github.com/nearai/ironclaw/issues/5701) | 活动面板不实时更新 | 未关联 |
| [#5834](https://github.com/nearai/ironclaw/issues/5834) | Slack 断开被拒绝 | 未关联 |
| [#5836](https://github.com/nearai/ironclaw/issues/5836) | Routine 定时执行 "No thread attached" | 未关联 |
| [#5507](https://github.com/nearai/ironclaw/issues/5507) | 失败 Routine 无法调试（No thread attached） | 已关闭（关联问题仍存在） |
| [#5508](https://github.com/nearai/ironclaw/issues/5508) | Slack 交付目标未找到 | 未关联 |
| [#5552](https://github.com/nearai/ironclaw/issues/5552) | 多工具失败后返回通用 "invalid result" | 未关联 |
| [#5776](https://github.com/nearai/ironclaw/issues/5776) | 长输出导致超时后降级为 "invalid result" | 未关联 |
| [#5838](https://github.com/nearai/ironclaw/issues/5838) | Context compaction 失败 | 已关闭（#7289） |

**P3 — 低严重（UI/体验）**
| Issue | 描述 | Fix PR |
|-------|------|--------|
| [#5557](https://github.com/nearai/ironclaw/issues/5557) | Logs deep link 需点击两次 | 已关闭 |
| [#5704](https://github.com/nearai/ironclaw/issues/5704) | 活跃运行时图片预览变透明 | 已关闭 |
| [#5705](https://github.com/nearai/ironclaw/issues/5705) | Terminal 图标无隐藏选项 | 已关闭 |
| [#5706](https://github.com/nearai/ironclaw/issues/5706) | 侧边栏展示原始 thread ID | 已关闭 |

**稳定性评估：** P1/P2 问题中有 **11 条仍未关联 Fix PR**，其中 Routine 稳定性（#5456、#5836、#5507）和 Slack 集成（#5834、#5508）是最大痛点。

---

## 6. 功能请求与路线图信号

| 信号来源 | 描述 | 预期纳入版本 |
|----------|------|--------------|
| [#7236](https://github.com/nearai/ironclaw/pull/7236) + [#7239](https://github.com/nearai/ironclaw/pull/7239) | Inspector 诊断面板（prompt 检查、模型调用统计） | 已在 1.1.0 就绪 |
| [#7184](https://github.com/nearai/ironclaw/pull/7184) | Nostr WASM host functions | 可能进入 1.2.0 |
| [#7214](https://github.com/nearai/ironclaw/pull/7214) | Docker/Railway sandbox profiles | 已合并，增强部署灵活性 |
| [#7157](https://github.com/nearai/ironclaw/pull/7157) | 双通道交付工具（conversation lifecycle + notification channels） | 已在 1.1.0 中体现 |
| [#7306](https://github.com/nearai/ironclaw/pull/7306) | 文档/指南统一框架（canonical home per fact） | 文档体系优化 |

**路线图判断：** 项目当前重心从功能扩展转向 **诊断可观测性**（Inspector）和 **交付可靠性**（Slack/Routine），下一版本预计将继续聚焦于稳定性加固。

---

## 7. 用户反馈摘要

**痛点：**
1. **Routine 可靠性差**：多次出现 "No thread attached"、lease 过期、执行失败无反馈（#5456、#5836、#5507、#5504）
2. **集成集成脆弱**：Slack 断开/重连逻辑混乱（#5834、#5508）、GitHub 403 错误（#5702）、Telegram 配对流程失效（#3533）
3. **错误信息不友好**：多工具失败后仅显示 "invalid result"，无法定位根因（#5552、#5776）
4. **UI 可观测性不足**：活动面板不实时更新（#5701）、长历史导致创建新聊天延迟（#5509）

**正面反馈：**
- 1.1.0 新增的 MCP 扩展和 Slack 交付能力受到关注
- Inspector 诊断体系的引入回应了运维需求

---

## 8. 待处理积压

| Issue | 优先级 | 风险 | 建议 |
|-------|--------|------|------|
| [#5456](https://github.com/nearai/ironclaw/issues/5456) | P1 | Routine 生产失败主因，90s lease 阈值需调整 | 建议提高默认阈值或引入自适应超时 |
| [#5836](https://github.com/nearai/ironclaw/issues/5836) | P2 | "No thread attached" 系统性问题，影响所有定时 Routine | 需根因分析 thread 绑定机制 |
| [#5877](https://github.com/nearai/ironclaw/issues/5877) | P1 | Slack 通知送达错误用户，涉及数据隐私安全 | 紧急修复，检查 delivery target 匹配逻辑 |
| [#5553](https://github.com/nearai/ironclaw/issues/5553) | P2 | 审批通知不可靠，影响人机协作信任 | 修复通知持久化机制 |
| [#5702](https://github.com/nearai/ironclaw/issues/5702) | P2 | GitHub 403 错误，阻碍开发者工作流 | 检查 OAuth token 权限范围 |
| [#5509](https://github.com/nearai/ironclaw/issues/5509) | P2 | 聊天创建延迟随历史增长，影响用户体验 | 前端性能优化或分页加载 |

---

**项目健康度总评：** 1.1.0 发布标志重要里程碑，但 P1/P2 Bug 积压较多，尤其 Routine 稳定性和集成可靠性是用户信任的核心风险点。建议下一迭代优先处理 #5456、#5836、#5877 三个问题。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 — 2026-08-07

---

## 1. 今日速览

LobsterAI 今日项目活跃，过去24小时内产生 **6条Issue** 和 **4条PR**，无新版本发布。维护者fisherdaddy合并了2个PR（#2445、#2446），分别修复了openclaw配置清理和Windows安装程序看门狗退出的问题。社区反馈集中在配置管理和交互体验优化上，整体项目健康度良好，问题响应节奏正常。

---

## 2. 版本发布

> 过去24小时内无新Release。

---

## 3. 项目进展

**今日合并/关闭的PR：**

| PR | 类型 | 摘要 |
|---|---|---|
| [#2445](https://github.com/netease-youdao/LobsterAI/pull/2445) | Bug Fix | 修复openclaw中`config.set`时未清理plugin-index-managed键的问题，避免插件管理键污染用户配置 |
| [#2446](https://github.com/netease-youdao/LobsterAI/pull/2446) | Bug Fix | 修复Windows安装程序中watchdog异常退出时`exit code`为null导致的静默失败，通过extractor兜底获取退出码 |

**进展评估：** 今日修复均针对Windows平台和openclaw插件机制的稳定性，属于基础设施层面的关键修补，对项目鲁棒性有直接提升。

---

## 4. 社区热点

**今日热度最高的Issue：**

- **[Issue #2447](https://github.com/netease-youdao/LobsterAI/issues/2447)** — 执行无结果也无错误信息（新建，评论1条，👍 0）
  - 用户反馈执行后无任何输出或错误提示，影响使用信心。有1条评论，但尚未明确根因。

- **[Issue #2443](https://github.com/netease-youdao/LobsterAI/issues/2443)** — 模型ID含斜杠的自定义Provider无法在界面中使用（新建，👍 0）
  - SiliconFlow等OpenAI兼容服务商的模型ID含斜杠（如`deepseek-ai/DeepSeek-V4-Flash`），导致界面选择失败。**属于中严重程度的兼容性问题，影响面较广。**

- **[Issue #2444](https://github.com/netease-youdao/LobsterAI/issues/2444)** — 输入框编辑模式功能请求（新建，评论0条，👍 0）
  - 长Prompt输入时Shift+Enter换行不便，用户提出增加"编辑模式"切换或WYSIWYG编辑器支持。**该需求合理，可纳入后续迭代评估。**

---

## 5. Bug 与稳定性

| Issue | 描述 | 严重程度 | Fix PR |
|---|---|---|---|
| [#2447](https://github.com/netease-youdao/LobsterAI/issues/2447) | 执行无结果、无错误信息 | 中 | 待排查 |
| [#2443](https://github.com/netease-youdao/LobsterAI/issues/2443) | 模型ID含斜杠无法在界面选择 | 中 | 待修复 |
| [#2442](https://github.com/netease-youdao/LobsterAI/issues/2442) | PowerShell版本始终是5.1，未升级到7.x | 低 | 无（设计决策讨论） |

> **注：** PR #2446 已修复Windows安装程序watchdog相关稳定性问题。

---

## 6. 功能请求与路线图信号

- **[Issue #2444](https://github.com/netease-youdao/LobsterAI/issues/2444)** — 输入框编辑模式（Enter换行/Ctrl+Enter发送）
  - 用户痛点明确，方案合理。**建议纳入近期迭代评估。**

- **[PR #1199](https://github.com/netease-youdao/LobsterAI/pull/1199)** — 为每个模型添加`contextWindow`和`maxTokens`设置
  - 该PR处于stale状态，但功能对模型兼容性管理有意义，**建议维护者重新评估并尝试解决冲突后合入。**

- **[PR #1197](https://github.com/netease-youdao/LobsterAI/pull/1197)** — Agent管理页面交互优化（删除操作路径过深问题）
  - 与主分支存在冲突，处于stale状态，**建议跟进冲突解决。**

---

## 7. 用户反馈摘要

**主要痛点：**
1. **执行结果不可见**（#2447）：用户执行后无任何反馈，体验断裂。
2. **配置冗余**（#1196）：每次切换工作目录强制创建6个系统文件，用户希望支持全局配置文件或隐藏目录存储。
3. **网关重启状态不明确**（#1198）：进度条消失后无法判断重启进度，导致对话提示模型不可用。
4. **长Prompt输入体验差**（#2444）：频繁使用Shift+Enter换行，误触发送风险高。
5. **斜杠模型ID兼容**（#2443）：自定义Provider（如SiliconFlow）模型ID含斜杠时界面无法选择，属于配置层Bug。

**用户满意点：**
- 今日PR修复了openclaw配置和Windows安装程序的稳定性，反映出维护者对已知问题的响应。

---

## 8. 待处理积压

| 类型 | ID | 标题 | 创建时间 | 状态 | 建议 |
|---|---|---|---|---|---|
| Issue | [#1196](https://github.com/netease-youdao/LobsterAI/issues/1196) | 不要强制在工作目录建立系统文件 | 2026-04-01 | stale | 需维护者回应设计决策 |
| Issue | [#1198](https://github.com/netease-youdao/LobsterAI/issues/1198) | 网关重启进度条消失 | 2026-04-01 | stale | 需排查重启状态跟踪逻辑 |
| PR | [#1197](https://github.com/netease-youdao/LobsterAI/pull/1197) | Agent管理页面交互优化 | 2026-04-01 | stale/冲突 | 需解决与主分支冲突 |
| PR | [#1199](https://github.com/netease-youdao/LobsterAI/pull/1199) | 添加contextWindow和maxTokens设置 | 2026-04-01 | stale | 需重新评估并解决冲突 |

> **提醒：** 以上4项均已超过4个月未得到维护者响应，建议团队集中清理stale积压，必要时关闭或迁移至社区维护。

---

*报告生成时间：2026-08-07 | 数据来源：GitHub LobsterAI 项目*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报（2026-08-07）

## 1.  今日速览
过去24小时 CoPaw 保持高频迭代节奏，累计处理 Issues 28 条、PR 50 条，其中 14 个 Issue 与 30 个 PR 已关闭/合并，待处理 PR 20 条，整体吞吐健康。今日无新版本发布，但后端架构与稳定性修复是核心主线：用户上下文透明穿透、文件管理 API、AG-UI 协议暴露、记忆系统 Embedding 链路等关键能力集中落地。同时，MCP 工具调用超时、Agent 无限循环、浏览器 SDK 连接崩溃、跨天日期错位等生产环境高频痛点持续暴露，社区反馈积极，维护者响应较快，项目处于“架构补全 + 稳定性攻坚”的爬坡期。

## 2.  版本发布
暂无新版本发布。

## 3.  项目进展
今日合并/关闭的 PR 主要推动以下方向：
- **企业级上下文与多租户支持**：[#6525](https://github.com/agentscope-ai/CoPaw/pull/6525) 实现 `user_id`、`channel`、`tenant` 等元数据从 Chat API 穿透至 Agent、Tool、MCP 及 SKILL CLI，全程对 LLM 透明，为多租户隔离奠定基础。
- **文件管理后端补齐**：[#6651](https://github.com/agentscope-ai/CoPaw/pull/6651) 为 `/files` 路由补充删除、重命名/移动、创建目录、单文件上传/下载、目录级列表 6 个 REST 端点，复用现有 `FileGuard` 安全模型，前端文件管理能力得到实质性落地。
- **协议开放与扩展**：[#6337](https://github.com/agentscope-ai/CoPaw/pull/6337) 通过 `/protocol/agui/chat` SSE 端点暴露 AG-UI 协议，支持外部消费方以标准事件流接入 Agent 响应。
- **记忆与 Embedding 链路加固**：[#6741](https://github.com/agentscope-ai/CoPaw/pull/6741) 新增统一 Embedding 模型工厂（支持 OpenAI/DashScope/Gemini/Ollama），增加保存前连通性校验与空向量/维度检测；[#6739](https://github.com/agentscope-ai/CoPaw/pull/6739) 配套发布中英文配置指南。
- **Tool Call 元数据跨上下文保留**：[#6605](https://github.com/agentscope-ai/CoPaw/pull/6605) 与 [#6759](https://github.com/agentscope-ai/CoPaw/pull

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-08-07

## 1. 今日速览

ZeroClaw 今日保持高强度开发节奏：过去 24 小时新增 36 条 Issues、50 条 PR 更新，整体活跃度处于高位。无新版本发布，但社区聚焦于多项关键 RFC 的推进（A2A 出站客户端、Work Lanes 自动化、per-model context 配置），以及一批安全修复的落地。SOP 子系统暴露出多处静默失效问题（配置未生效、格式错误被吞、运行时 CPU 异常），成为今日讨论焦点。项目整体健康度良好，治理流程与技术债务同步受控。

---

## 2. 版本发布

无新版本发布。当前开发集中于 v0.9.0 安全加固队列（见 Issue #7432）。

---

## 3. 项目进展

### 今日关闭/合并的重要条目

| 条目 | 类型 | 说明 |
|------|------|------|
| [#7947](https://github.com/zeroclaw-labs/zeroclaw/issues/7947) | Bug (S0) | `execute_pipeline` 绕过 per-agent 工具权限控制（confused deputy）已修复 |
| [#1](https://github.com/zeroclaw-labs/zeroclaw/issues/1) | Bug (CRITICAL) | XOR 密文存储密钥问题已关闭（历史遗留加密缺陷） |
| [#9456](https://github.com/zeroclaw-labs/zeroclaw/issues/9456) | CI | Containerfile 变更自动校验已加入 PR CI |
| [#9672](https://github.com/zeroclaw-labs/zeroclaw/issues/9672) | Bug | `cron add` 文档示例全部失效问题已修复 |
| [#9172](https://github.com/zeroclaw-labs/zeroclaw/issues/9172) | Enhancement | ZeroCode slash commands 统一命令描述源已实现 |
| [#9741](https://github.com/zeroclaw-labs/zeroclaw/pull/9741) | CI | 全特性镜像构建校验防止 MSRV 漂移 |

**整体推进评估：** 今日关闭条目以安全修复和 CI 加固为主，反映 v0.9.0 安全硬化的实质进展；SOP 子系统的多项 Bug 仍在 Open 状态，尚未形成修复闭环。

---

## 4. 社区热点

### 高评论 RFC / Tracker（活跃讨论）

| Issue | 主题 | 评论数 | 热度分析 |
|-------|------|--------|----------|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) | Work Lanes, Board Automation, Label Cleanup | 19 | 治理流程优化 RFC，长期跟踪中（Rev.24），讨论成熟但批准延期 |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Maintainer decision queue for RFCs | 11 | 决策队列机制建设，支撑 RFC 评审流程 |
| [#9106](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) | A2A outbound client (A2ATool) | 11 | Agent-to-Agent 出站能力 RFC，社区需求强烈 |
| [#9246](https://github.com/zeroclaw-labs/zeroclaw/issues/9246) | ZeroCode ownership migration 配置保留 | 11 | ZeroCode 所有权迁移过程中的配置保护问题 |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) | Provenance & conversation binding | 10 | 内部 Agent 轮次的溯源与对话绑定 RFC |
| [#7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) | Per-model capability & context config | 8 | 按模型配置上下文窗口与能力，解决 provider 误报问题 |

**热点分析：** 社区讨论高度集中于架构治理（Work Lanes、决策队列）和 Agent 互联能力（A2A）。A2A 出站客户端 RFC 有对应 PR [#9324](https://github.com/zeroclaw-labs/zeroclaw/pull/9324) 推进，显示从设计到实现的良性循环。

---

## 5. Bug 与稳定性

### 安全类（高风险）

| Issue | 标题 | 严重度 | 状态 | Fix PR |
|-------|------|--------|------|--------|
| [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) | verifiable-intent 未验证凭证链 | High | Open | — |
| [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) | WhatsApp `allowed_groups` 空列表默认为全放行 | High | Open | — |
| [#8826](https://github.com/zeroclaw-labs/zeroclaw/pull/8826) | image_gen SSRF 防护 | High | Open PR | PR #8826 |
| [#9435](https://github.com/zeroclaw-labs/zeroclaw/pull/9435) | Gemini API Key 泄露到错误文本 | P1 | Open PR | PR #9435 |
| [#9438](https://github.com/zeroclaw-labs/zeroclaw/pull/9438) | `/api/pair` 未认证端点锁死绕过 | P1 | Open PR | PR #9438 |

### 运行时 / 稳定性

| Issue | 标题 | 严重度 | 状态 |
|-------|------|--------|------|
| [#9799](https://github.com/zeroclaw-labs/zeroclaw/issues/9799) | 长期 ephemeral daemon CPU >100% | High | Open |
| [#9800](https://github.com/zeroclaw-labs/zeroclaw/issues/9800) | SIGTERM 后终端 raw/mouse 状态未恢复 | Medium | Open |
| [#9786](https://github.com/zeroclaw-labs/zeroclaw/issues/9786) | 格式错误的 SOP.toml 被静默丢弃 | P1 | Open |
| [#9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) | `sops_dir` 文档默认值未生效 | P1 | Open |
| [#9783](https://github.com/zeroclaw-labs/zeroclaw/issues/9783) | SOP `finish_run` 丢弃失败原因 | Medium | Open |
| [#9770](https://github.com/zeroclaw-labs/zeroclaw/issues/9770) | `cron update` 静默丢弃 declarative 变更 | P1 | Open |
| [#9780](https://github.com/zeroclaw-labs/zeroclaw/issues/9780) | cron-triggered SOP 无法执行网络操作 | High | Open |
| [#8615](https://github.com/zeroclaw-labs/zeroclaw/issues/8615) | compatible provider 静默删除 `<think>` 内容 | Medium | Closed (PR) |

**关键观察：** SOP 子系统今日集中爆发 5+ 个高优先级 Bug，涉及配置加载、错误处理、能力缺失等核心问题，均未有关闭的 Fix PR，建议优先处理。

---

## 6. 功能请求与路线图信号

### 已进入 RFC 评审的新功能

| RFC | 状态 | 对应 PR | 纳入下版本可能性 |
|-----|------|---------|------------------|
| [#9106](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) A2A 出站客户端 | Accepted, in-progress | [#9324](https://github.com/zeroclaw-labs/zeroclaw/pull/9324) | **高** — Phase 1 已实现 |
| [#7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) Per-model context config | Needs review | — | **中** — 治理流程待定 |
| [#9530](https://github.com/zeroclaw-labs/zeroclaw/issues/9530) 测试变更风险优先級 | Needs review | — | **低** — 内部治理 |
| [#9496](https://github.com/zeroclaw-labs/zeroclaw/issues/9496) RFC 流程简化 | Needs review | — | **中** — 治理优化 |
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) Work Lanes 自动化 | Ratification deferred | — | **待定** — 流程延期 |

### 已有 PR 但待合并的功能

- [#9535](https://github.com/zeroclaw-labs/zeroclaw/pull/9535) — Context compaction 按模型窗口比例锚定
- [#9352](https://github.com/zeroclaw-labs/zeroclaw/pull/9352) — OTel 跨轮次对话关联
- [#9182](https://github.com/zeroclaw-labs/zeroclaw/pull/9182) — Windows PowerShell 原生 Shell 支持
- [#8443](https://github.com/zeroclaw-labs/zeroclaw/pull/8443) — Matrix 单消息进度草稿
- [#9420](https://github.com/zeroclaw-labs/zeroclaw/pull/9420) — Anthropic OAuth 存储配置

---

## 7. 用户反馈摘要

| 痛点 / 场景 | 来源 | 情绪 |
|-------------|------|------|
| SOP 配置默认值不生效导致整个子系统静默不加载 | [#9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) | 严重不满 |
| SOP.toml 格式错误无诊断，`sop validate` 报成功 | [#9786](https://github.com/zeroclaw-labs/zeroclaw/issues/9786) | 沮丧 |
| cron-triggered SOP 无法做网络请求，文档描述与实际能力不符 | [#9780](https://github.com/zeroclaw-labs/zeroclaw/issues/9780) | 失望 |
| WhatsApp `allowed_groups` 空列表等于全放行，存在安全隐患 | [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) | 担忧 |
| Telegram 命令菜单超过 100 条时静默失败 | [#8950](https://github.com/zeroclaw-labs/zeroclaw/issues/8950) | 已修复 |
| Bedrock Nova 2 Lite 缓存随机报错 | [#8720](https://github.com/zeroclaw-labs/zeroclaw/issues/8720) | 已关闭（待验证） |
| Kimi Code provider 支持需求 | [#657](https://github.com/zeroclaw-labs/zeroclaw/issues/657) | 已关闭 |
| 长期 daemon CPU 过高 + 重复 DB handle | [#9799](https://github.com/zeroclaw-labs/zeroclaw/issues/9799) | 严重不满 |
| Ctrl+C 退出后终端鼠标/原始模式残留 | [#9800](https://github.com/zeroclaw-labs/zeroclaw/issues/9800) |  annoyance |
| A2A 出站能力缺失限制 Agent 间协作 | [#9106](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) | 强烈需求 |

---

## 8. 待处理积压

| Issue | 标题 | 创建时间 | 时长 | 建议 |
|-------|------|----------|------|------|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) | Work Lanes RFC | 2026-05-20 | ~79 天 | 维持跟踪，Rev.24 待最终 ratification |
| [#657](https://github.com/zeroclaw-labs/zeroclaw/issues/657) | Kimi Code provider | 2026-02-17 | ~171 天 | 已关闭，无后续动作 |
| [#7432](https://github.com/zeroclaw-labs/zeroclaw/issues/7432) | v0.9.0 安全队列 Tracker | 2026-06-09 | ~59 天 | 持续跟踪，v0.9.0 核心目标 |
| [#9657](https://github.com/zeroclaw-labs/zeroclaw/issues/9657) | protected-literal 误判 "Signal" | 2026-08-02 | 5 天 | 已关闭 |
| — | **SOP 子系统 6+ Bug** | 2026-08-06~07 | 1~2 天 | ⚠️ **紧急** — 集中修复 SOP 配置加载、错误诊断、能力缺失问题 |
| — | **#9799 Ephemeral daemon CPU 异常** | 2026-08-07 | 1 天 | ⚠️ **高优** — 17h 运行后 CPU 140-177%，需尽快定位 |

---

*数据来源: ZeroClaw GitHub (github.com/zeroclaw-labs/zeroclaw) · 统计周期: 2026-08-06 00:00 ~ 2026-08-07 23:59 UTC*

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*