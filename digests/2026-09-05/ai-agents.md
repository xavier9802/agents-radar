# OpenClaw 生态日报 2026-09-05

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-05 03:58 UTC

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
**日期：2026-09-05** | **数据来源：github.com/openclaw/openclaw**

---

## 1. 今日速览

过去24小时项目保持高活跃状态：新增/活跃 Issues 395条、关闭 105条；PR 更新 500条（待合并 347条、已合并/关闭 153条）。无新版本发布，但多项关键稳定性修复已合并，包括 Control UI 测试稳定化、Logbook 查询重构。核心痛点集中在 Gateway 事件循环阻塞、子进程泄漏、多代理编排不稳定等架构级问题，社区对 P0 级崩溃与消息丢失问题的关注持续升温。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

**今日合并/关闭的重要 PR：**

| PR | 类型 | 说明 |
|---|---|---|
| [#138776](https://github.com/openclaw/openclaw/pull/138776) | fix(ci) | 稳定 Control UI 流式传输与恢复测试，修复浏览器定时任务精度问题 |
| [#138816](https://github.com/openclaw/openclaw/pull/138816) | refactor(logbook) | 类型化 Logbook 查询，限制观察记录上限为 200 条，减少冗余 SQL |

**推进方向：** 今日合并聚焦于测试稳定性与内部查询性能优化，为后续大版本发布夯实基础设施。347条待合并 PR 中有多项 P1 级修复待审，项目整体处于"修复积累→版本释放"的临界状态。

---

## 4. 社区热点

**评论最多的 Issues（Top 5）：**

| Issue | 评论数 | 等级 | 核心议题 |
|---|---|---|---|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | 21 | 🐚 platinum / P0 | Codex PreToolUse hook 产生 CPU 密集型子进程，导致 Gateway RPC 停滞 |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | 20 | 🦞 diamond / P1 | Steer mode 无法在回合中途注入消息，消息被延迟到回合结束 |
| [#104721](https://github.com/openclaw/openclaw/issues/104721) | 17 | 🐚 platinum / P0 [CLOSED] | 所有 tool 结果返回字面字符串 "(see attached image)" 而非实际输出 |
| [#87307](https://github.com/openclaw/openclaw/issues/87307) | 15 | 🦞 diamond / P1 [CLOSED] | Matrix 线程回复回退为普通回复，/status 和 /model 命令静默失效 |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | 15 | 🦞 diamond / P1 | Session transcript projection 在高写入负载下 livelock，阻塞主线程 |

**热点分析：** 社区最关注的问题集中在**会话状态一致性**与**Gateway 线程阻塞**两大架构层面。#91009 和 #115908 均涉及 Node.js 事件循环被同步操作阻塞，反映出现有架构在高并发场景下的根本性压力。#48003 的 steer mode 问题影响多代理协作体验，是产品功能层面的关键摩擦点。

---

## 5. Bug 与稳定性

**P0 级问题（发布阻塞级）：**

| Issue | 状态 | 描述 | Fix PR |
|---|---|---|---|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | OPEN | Codex hook relay 产生 CPU 耗尽的子进程，Gateway RPC 停滞 | 无 |
| [#104721](https://github.com/openclaw/openclaw/issues/104721) | CLOSED | Tool 结果被占位符字符串替换 | 已关闭 |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | OPEN | 升级至 2026.7.1 后 Gateway 无法启动 | 无 |
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | OPEN | Provider 计费冷却时间持久化导致用户被阻塞数小时 | 无 |
| [#138272](https://github.com/openclaw/openclaw/issues/138272) | OPEN | Android Talk 在任务型回合崩溃："no live response owner" | 无 |
| [#107814](https://github.com/openclaw/openclaw/issues/107814) | CLOSED [2026-09-04] | gpt-5.3-codex-spark 对必需参数工具调用返回空参数 | 已关闭 |
| [#114234](https://github.com/openclaw/openclaw/issues/114234) | OPEN | 容器环境下 usage-cost 刷新锁无法释放，缓存永久冻结 | 无 |
| [#118793](https://github.com/openclaw/openclaw/issues/118793) | OPEN | Claude CLI session limit 错误未触发模型故障转移链 | 无 |
| [#71689](https://github.com/openclaw/openclaw/issues/71689) | OPEN | SQLite 损坏导致 tasks registry 恢复失败 | 无 |

**P1 级关键 Bug：**

| Issue | 状态 | 描述 | Fix PR |
|---|---|---|---|
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | OPEN | Steer mode 无法中途注入消息 | 无 |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | OPEN | Transcript projection livelock 阻塞事件循环 | 无 |
| [#43367](https://github.com/openclaw/openclaw/issues/43367) | OPEN | 多代理编排不稳定：配置覆盖、session-lock 失败 | 无 |
| [#131150](https://github.com/openclaw/openclaw/issues/131150) | OPEN | Gateway 重启后 Slack DM 静默丢失 | 无 |
| [#99947](https://github.com/openclaw/openclaw/issues/99947) | OPEN | Codex harness mirrored-session-history 读取失败 | 无 |
| [#118018](https://github.com/openclaw/openclaw/issues/118018) | OPEN | Stale 子代理完成结果投递到错误的请求者生命周期 | 无 |
| [#120162](https://github.com/openclaw/openclaw/issues/120162) | OPEN | Safeguard compaction qualityGuard 与摘要共用超时预算 | 无 |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | OPEN | 同步持久化阻塞 Gateway 事件循环 | 无 |

**已有 Fix PR 的 Bug：**

| Issue | Fix PR | 说明 |
|---|---|---|
| [#95840](https://github.com/openclaw/openclaw/issues/95840) | [#127992](https://github.com/openclaw/openclaw/pull/127992) | 恢复 OpenAI 模型的 cache-TTL 上下文剪枝 |
| [#138722](https://github.com/openclaw/openclaw/issues/138722) | [#138798](https://github.com/openclaw/openclaw/pull/138798) | 限制 memory chunk 重叠，防止上下文长度超限 |
| [#91941](https://github.com/openclaw/openclaw/issues/91941) | [#103928](https://github.com/openclaw/openclaw/pull/103928) | 飞书长流式回复 draining stale updates |

---

## 6. 功能请求与路线图信号

| Issue | 评级 | 需求摘要 | 路线图信号 |
|---|---|---|---|
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | 🌊 tidepool | 内置无头浏览器，消除对外部 Chrome/第三方 API 依赖 | 中长期：解决 web access 可靠性问题 |
| [#41366](https://github.com/openclaw/openclaw/issues/41366) | 🌊 tidepool | 持久化自然语言规则学习 + 多提及回复语义 | 长期：多代理协作体验改进 |
| [#16670](https://github.com/openclaw/openclaw/issues/16670) | 🌊 tidepool | Onboarding Wizard 强制 Memory/Embedding 配置 | 中期：降低新用户配置摩擦 |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | 🌊 tidepool | Agent 自主触发上下文压缩（self-compact tool） | 中期：提升长会话管理能力 |
| [#28300](https://github.com/openclaw/openclaw/issues/28300) | 🌊 tidepool | 主题定制系统：预设主题 + 自定义主题工作室 | 短期：UI 可观测性改进 |
| [#45501](https://github.com/openclaw/openclaw/issues/45501) | 🌊 tidepool | `session.resetPrompt` 可配置会话启动消息 | 短期：配置灵活性提升 |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | 🌊 tidepool | 暴露解析后的后端模型至 session_status | 中期：多代理路由可观测性 |

**路线图判断：** 社区对**可观测性**（模型解析、上下文使用、会话标签）和**配置简化**（Onboarding、resetPrompt）的需求明确。短期可能优先纳入 #28300（主题系统）和 #45501（启动消息配置），中长期关注 #53763（内置浏览器）和 #6757（自主压缩）。

---

## 7. 用户反馈摘要

**核心痛点：**

1. **事件循环阻塞导致 Gateway 停滞** — #115908、#119720、#91009 多个 Issue 指向同一根本问题：同步操作（持久化、transcript 重建、hook 执行）阻塞 Node.js 主线程，影响所有 channel transport。用户反馈"stalls for tens of seconds"、"blocking all channel transports"。

2. **多代理协作不可靠** — #43367 描述并发 agent 配置覆盖、session-lock 失败；#118018 报告 stale 子代理结果投递错误生命周期。用户表示"multi-agent runs unreliable in practice"。

3. **消息丢失与静默失败** — #112259 报告零 payload dispatch 无重试、无死信队列；#131150 描述 Gateway 重启后 Slack DM 全部丢失。用户对"silently dropped"反复表达 frustration。

4. **认证/授权脆弱** — #86215（Codex OAuth refresh 卡死数小时）、#70903（计费冷却持久化）、#98702（OAuth 继承在 built-in runtime 失败）反映认证链路缺乏弹性。

5. **工具调用兼容性问题** — #107449（cron tool JSON Schema 与 llama.cpp 不兼容）、#107814（gpt-5.3-codex-spark 返回空参数）显示模型-工具 schema 对齐仍存在 gap。

**正面反馈：** #28300（主题定制）获得 5 个 👍，#40982（watchdog 配置）获得 2 个 👍，反映用户对可配置性和 UI 体验改善的认可。

---

## 8. 待处理积压

**长期未响应的重要 Issue（stale）：**

| Issue | 创建时间 | 评级 | 状态 | 风险 |
|---|---|---|---|---|
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | 2026-04-24 | 🦞 diamond / P0 | stale | Provider 计费冷却机制影响用户体验，可能阻碍付费转化 |
| [#87212](https://github.com/openclaw/openclaw/issues/87212) | 2026-05-27 | 🦪 silver / P1 | stale | 系统信封 footer 被回显到 Telegram 消息，信息泄露风险 |
| [#84393](https://github.com/openclaw/openclaw/issues/84393) | 2026-05-20 | 🐚 platinum / P1 [CLOSED] | stale | Codex runtime 向操作代理注入编码 agent base prompt |
| [#69008](https://github.com/openclaw/openclaw/issues/69008) | 2026-04-19 | 🦐 gold / P2 [CLOSED] | stale | Telegram 群代理默认 session-only 导致消息不交付 |
| [#116176](https://github.com/openclaw/openclaw/issues/116176) | 2026-07-30 | 🦐 gold / P1 | stale + dedupe | Signal 自动启动守护进程端口绑定不匹配 |

**维护者关注建议：**
- #70903 和 #87212 已 stale 超过 3 个月，涉及认证弹性和信息安全，建议优先 triage。
- #116176 存在 dedupe 标记，需确认父 Issue 状态。
- 当前 347 条待合并 PR 中包含多项 P1 修复，建议加快 review 节奏以避免积压。

---

**报告生成时间：** 2026-09-05 | **分析师：** Agnes-2.0-Flash (Sapiens AI)

---

## 横向生态对比



# AI 智能体开源生态横评报告 — 2026-09-05

---

## 1. 生态全景

2026年9月，个人 AI 助手/自主智能体开源生态呈现**"高活跃+高复杂度"**的双重特征：Top 项目日均 PR 吞吐在 20-500 条不等，但 P0 级稳定性问题（事件循环阻塞、SQLite 并发损坏、消息丢失）已成为跨项目的共性挑战。社区需求正从"功能堆砌"转向"可靠性与可观测性"，多代理编排、会话状态一致性、渠道适配弹性成为新的技术高地。LobsterAI 以每日双版本发布领跑迭代速度，而 OpenClaw 虽处于修复积累期，其架构级问题仍最具生态代表性。

---

## 2. 各项目活跃度对比

| 项目 | Issue（新开/活跃） | Issue（关闭） | PR（待合并） | PR（已合并） | Release | 健康度 |
|------|------------------|-------------|------------|------------|---------|--------|
| **OpenClaw** | 395 | 105 | 347 | 153 | — | 🟡 需关注（P0 积压） |
| **Hermes Agent** | 50 | — | — | 3 | — | 🟡 需注意（P1 集中） |
| **CoPaw** | 15 | 8 | 20 | 6 | — | 🟢 良好 |
| **ZeroClaw** | 24 | 10 | 44 | 6 | v0.8.5 准备中 | 🟢 良好 |
| **LobsterAI** | 1 | — | 5 | 28 | v2026.9.3/9.4 | 🟢 优秀（SQLite 风险） |
| **NanoBot** | 2 | 3 | 21 | 7 | — | 🟢 良好 |
| **PicoClaw** | 3 | — | 2 | 20 | — | 🟢 良好 |
| **IronClaw** | 3 | — | 9 | 3 | — | 🟢 良好 |
| **Moltis** | 1 | — | 1 | — | — | 🟢 良好 |
| **NullClaw** | 1 | — | 0 | 0 | — | 🟢 平稳（低活跃） |
| **ZeptoClaw** | 0 | — | 0 | 0 | — | ⚪ 无活动 |

---

## 3. OpenClaw 在生态中的定位

**优势：**
- **架构规模最大**：347 条待合并 PR、395 条活跃 Issue，社区参与深度与广度均居首位，是生态的"核心参照系"
- **渠道覆盖最广**：Telegram/Slack/Matrix/飞书/Android Talk 等多渠道网关架构，事件驱动模型最具代表性
- **多代理编排先行者**：Steer mode、多代理生命周期管理、session transcript projection 等复杂场景走在生态前列

**技术路线差异：**
- 与 NanoBot/Moltis 的"单代理 TUI/WebUI"路线不同，OpenClaw 坚持**Gateway + Channel Transport**的分布式架构
- 与 LobsterAI 的"内置浏览器+协作"消费级路线不同，OpenClaw 聚焦**生产级多代理编排与工具链集成**
- 与 ZeroClaw 的 Rust 多 crate workspace 路线不同，OpenClaw 基于 Node.js 事件循环，架构选型差异导致稳定性问题类型不同（OpenClaw 为事件循环阻塞，ZeroClaw 为安全配置语义缺陷）

**社区规模对比（按 Issue/PR 活跃度）：**
OpenClaw > Hermes Agent ≈ ZeroClaw > CoPaw > LobsterAI > NanoBot > PicoClaw > IronClaw > Moltis > NullClaw

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|---------|---------|
| **事件循环/线程阻塞** | OpenClaw、Hermes Agent | Node.js 事件循环被同步持久化/hook 阻塞（OpenClaw #115908/#119720/#91009）；Windows terminal 死锁（Hermes #103398） |
| **多代理/多会话编排** | OpenClaw、CoPaw、Hermes Agent | 子代理结果投递错误（OpenClaw #118018）；Loop 模式状态丢失（CoPaw #7555）；Desktop 关闭后 Bot 需保持运行（Hermes #97681） |
| **消息丢失与静默失败** | OpenClaw、CoPaw、ZeroClaw | Gateway 重启后 Slack DM 丢失（OpenClaw #131150）；飞书 consumer 卡死（CoPaw #7534）；cron 静默失败无日志（ZeroClaw #10594/#10593） |
| **可观测性与可配置性** | NanoBot、CoPaw、ZeroClaw、Hermes Agent | WebUI 展示 tokens/s 速度（NanoBot #5660）；Skill preload 减少首轮延迟（CoPaw #7183）；推理层级跨会话持久化（Moltis #1259） |
| **内存/资源管理** | NanoBot、Hermes Agent、CoPaw | OAuth flow/summary cache 无界增长（NanoBot #5665/#5664/#5663）；20+ profile 池槽耗尽（Hermes #103375）；Playwright 安装阻塞启动（CoPaw #7023） |
| **渠道适配弹性** | OpenClaw、IronClaw、ZeroClaw | Telegram 错误提示不精准（IronClaw #7955/#7956/#8074）；WhatsApp 安全配置语义缺陷（ZeroClaw #9348/#9397） |
| **SQLite 并发/持久化** | OpenClaw、Hermes Agent、LobsterAI | WAL 并发写入导致状态库损坏（Hermes #103339）；ON DELETE CASCADE 失效/非原子写（LobsterAI #1071）；SQLite 损坏恢复失败（OpenClaw #71689） |

---

## 5. 差异化定位分析

| 维度 | OpenClaw | Hermes Agent | LobsterAI | NanoBot | CoPaw | ZeroClaw | Moltis |
|------|----------|-------------|-----------|---------|-------|----------|--------|
| **功能侧重** | 多代理编排+网关架构 | Desktop/TUI 优先+插件生态 | 内置浏览器+协作+订阅 | WebUI 可观测性+provider 扩展 | 多租户 Hub+Skill 系统 | 安全优先+RFC 治理 | 外部智能体集成 |
| **目标用户** | 生产级多代理部署 | 个人开发者+Desktop 用户 | 消费级+团队协作 | 企业/飞书生态用户 | 多租户 SaaS 运营 | 安全敏感部署 | 外部 Agent 互操作 |
| **技术架构** | Node.js Gateway+Channel | Electron Desktop+SQLite | Tauri+内置浏览器 | Go+WebUI | Python+多租户 | Rust 23-crate workspace | Go+外部 Agent 适配 |
| **发布节奏** | 修复积累期 | 高强度功能迭代 | 每日双版本 | 功能积累期 | 稳定迭代 | 周级 stabilization | 中等节奏 |

---

## 6. 社区热度与成熟度分层

| 阶段 | 项目 | 特征 |
|------|------|------|
| **快速迭代期** | LobsterAI、Hermes Agent | 高 PR 吞吐、每日版本发布、功能驱动、稳定性问题累积 |
| **修复积累期** | OpenClaw、CoPaw | 大量待合并 PR（347/20）、P0/P1 Bug 集中、处于"修复→版本释放"临界 |
| **质量巩固期** | ZeroClaw、NanoBot、PicoClaw | RFC 治理（ZeroClaw）、内存泄漏集中修复（NanoBot）、Provider 生态拓宽（PicoClaw） |
| **平稳运营期** | IronClaw、Moltis | 中低活跃度、方向清晰、无阻塞性 Bug |
| **低活跃期** | NullClaw、ZeptoClaw | 极少 Issue/PR，生态参与有限 |

---

## 7. 值得关注的趋势信号

| 趋势 | 信号来源 | 对开发者的参考价值 |
|------|---------|------------------|
| **SQLite 不再是安全的默认存储** | Hermes #103339（4天7次损坏）、Lobster #1071（CASCADE失效）、CoPaw #7558（请求PostgreSQL后端） | 多进程/多 profile 部署必须引入 WAL 锁机制或迁移至客户端数据库 |
| **事件循环阻塞是 Node.js 智能体的系统性风险** | OpenClaw #91009/#115908/#119720 三个 P0 指向同一根因 | 同步操作（持久化、transcript 重建、hook）必须迁移至 worker thread 或异步队列 |
| **可观测性从"加分项"变为"必选项"** | NanoBot #5660（tokens/s）、CoPaw #7183（Skill preload）、Moltis #1259（推理层级持久化） | 用户要求"看得见"模型速度、上下文使用、会话状态，可观测性直接影响留存 |
| **多代理编排仍是"看起来容易做起来难"** | OpenClaw #43367/#118018、CoPaw #7559/#7567、Hermes #97681 | 会话生命周期、结果投递、状态持久化是多代理可靠性的核心难点，建议 MVP 阶段限制并发度 |
| **安全配置语义需"fail-closed"默认** | ZeroClaw #9348（空 allowed_groups 等于放行全部） | 配置项默认值设计必须遵循安全默认原则，空值应解释为"拒绝"而非"放行" |
| **渠道适配弹性决定产品边界** | IronClaw #7955/#7956/#8074（Telegram 错误提示）、OpenClaw #131150（Slack DM 丢失） | 同一套消息路由逻辑在不同渠道的表现差异极大，建议建立渠道适配测试矩阵 |
| **自托管用户诉求上升** | NullClaw #993（Firecrawl 端点配置化）、CoPaw #7558（可插拔存储） | 自托管场景要求配置灵活性，硬编码端点/存储将直接阻碍企业采用 |

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目日报 | 2026-09-05

---

## 1. 今日速览

NanoBot 项目今日保持高活跃度，24小时内处理 **5 条 Issue**（2 新开/活跃，3 已关闭）与 **28 条 PR**（7 已合并/关闭，21 待合并），整体维护节奏紧凑。核心推进方向集中在三个领域：**内存管理与性能优化**（多处 bound cache/registry 修复）、**WebUI 体验增强**（上下文速度展示、session 标题生成修复）、**provider 生态扩展**（aimlapi.com 接入、OpenCode session affinity 适配）。暂无新版本发布，项目正处于功能积累期，多个稳定性修复待合并后有望形成下一版本的稳定性基线。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 贡献摘要 |
|---|---|---|
| [#5639](https://github.com/HKUDS/nanobot/pull/5639) | fix | 稳定 session 标签渲染、TUI 流式输出、配对 prompt；升级 OpenTUI 至 0.5.10 |
| [#5660](https://github.com/HKUDS/nanobot/pull/5660) | feat | WebUI 上下文气泡新增 **模型生成速度（tokens/s）** 展示，响应 #5631 |
| [#5657](https://github.com/HKUDS/nanobot/pull/5657) | refactor | 提取 WebUI 出站 wire 编码，统一 `send_payload` 原语，减少传输层重复代码 |

**项目推进评估：** 今日合并的 7 条 PR 中，#5639 解决了 TUI 流式代码块可见性这一长期痛点；#5660 完成了用户请求的观察指标功能；#5657 的架构重构为后续 WebUI 功能扩展打下基础。项目整体在**用户体验可观测性**与**代码架构整洁度**两个维度上有实质性进展。

---

## 4. 社区热点

### 🔥 高关注度 Issue / PR

1. **[Issue #5567](https://github.com/HKUDS/nanobot/issues/5567)** — 飞书渠道多轮回复整合为单条流式卡片
   - 当前 4 条评论，持续活跃
   - 反映企业用户（飞书生态）对"一问一答"交互一致性的强烈诉求

2. **[Issue #5661](https://github.com/HKUDS/nanobot/issues/5661) + [PR #5662](https://github.com/HKUDS/nanobot/pull/5662)** — OpenCode Zen/Go session affinity header
   - 关联 OpenCode 官方公告，2026-09-06 起缺失 header 可能导致错误
   - PR #5662 已就绪，属于**时效性 urgent fix**

3. **[PR #5656](https://github.com/HKUDS/nanobot/pull/5656)** — Context Compaction 可视化
   - 新增 `/compact` 命令与结构化 lifecycle events，让用户感知上下文压缩行为
   - 对应长对话场景下的性能透明度需求

4. **[PR #5626](https://github.com/HKUDS/nanobot/pull/5626)** — 新增 `copy_file` / `move_file` 工具
   - 填补文件系统工具集长期空白，减少模型通过 read+write 链式操作的开销

---

## 5. Bug 与稳定性

| 严重程度 | 问题 | Issue | 修复状态 |
|---|---|---|---|
| 🔴 高 | WebUI Channel locale registry 并发丢失 locale（如 `en`） | [#5644](https://github.com/HKUDS/nanobot/issues/5644) | ✅ 已关闭（推测已修复） |
| 🔴 高 | 0.3.0 升级后 `Current Time` runtime context 默认缺失（回归） | [#5645](https://github.com/HKUDS/nanobot/issues/5645) | ✅ 已关闭，[PR #5659](https://github.com/HKUDS/nanobot/pull/5659) 提供 opt-out 机制 |
| 🟡 中 | MCP Browser OAuth flow 内存无限增长 | — | ✅ [PR #5665](https://github.com/HKUDS/nanobot/pull/5665) 已 bound |
| 🟡 中 | Idle summary cache 无限增长 | — | ✅ [PR #5664](https://github.com/HKUDS/nanobot/pull/5664) 已 bound |
| 🟡 中 | Mattermost thread context cache 无限增长 | — | ✅ [PR #5663](https://github.com/HKUDS/nanobot/pull/5663) 已 bound |
| 🟡 中 | WebUI session 标题在 envelope 缺少 `webui` 标志时不生成 | [#5647](https://github.com/HKUDS/nanobot/issues/5647) | ✅ [PR #5658](https://github.com/HKUDS/nanobot/pull/5658) 已修复 |
| 🟢 低 | WebUI session 标题生成元数据检查 | — | ✅ [PR #5648](https://github.com/HKUDS/nanobot/pull/5648) 已修复 |

**稳定性评估：** 今日集中修复了 3 处内存无限增长的潜在泄漏（OAuth flow、idle summary、thread context），属于**系统性稳定性加固**。两个 0.3.0 回归问题（#5644、#5645）均已关闭，表明维护者对升级反馈响应迅速。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | PR 状态 | 纳入下一版本概率 |
|---|---|---|---|
| 飞书渠道流式卡片整合 | [#5567](https://github.com/HKUDS/nanobot/issues/5567) | 无关联 PR，持续开放 | 🟡 中（涉及渠道架构改动） |
| aimlapi.com provider 接入 | [PR #5666](https://github.com/HKUDS/nanobot/pull/5666) | 待合并 | 🟢 高（合作模式明确，50/50 分成） |
| Langfuse tracing for Codex | [PR #5520](https://github.com/HKUDS/nanobot/pull/5520) | 待合并 | 🟢 高（可观测性是趋势） |
| `copy_file` / `move_file` 工具 | [PR #5626](https://github.com/HKUDS/nanobot/pull/5626) | 待合并 | 🟢 高（工具集补全） |
| Heartbeat isolated session | [PR #4551](https://github.com/HKUDS/nanobot/pull/4551) | 待合并（超 2 个月） | 🟡 中（功能完整但排期靠后） |
| Heartbeat model override | [PR #4549](https://github.com/HKUDS/nanobot/pull/4549) | 待合并（超 2 个月） | 🟡 中 |
| 上下文压缩可视化 | [PR #5656](https://github.com/HKUDS/nanobot/pull/5656) | 待合并 | 🟢 高 |
| 模型重试状态展示 | [PR #5504](https://github.com/HKUDS/nanobot/pull/5504) | 待合并 | 🟢 高 |

**路线图判断：** 当前 PR 积压以"稳定性修复 + 可观测性增强"为主，新功能相对克制。`aimlapi.com` 合作 PR 和 `copy_file`/`move_file` 工具最有可能在下个版本合入。

---

## 7. 用户反馈摘要

- **飞书用户体验**：[#5567](https://github.com/HKUDS/nanobot/issues/5567) 指出多轮消息拆分破坏"一问一答"直觉，企业用户对此敏感度高，期望流式卡片整合。
- **可观测性诉求**：[#5631](https://github.com/HKUDS/nanobot/issues/5631) 希望 WebUI 展示模型速度与上下文信息，类似 DeepSeek harness，现已通过 [PR #5660](https://github.com/HKUDS/nanobot/pull/5660) 满足。
- **升级回归痛点**：[#5645](https://github.com/HKUDS/nanobot/issues/5645) 用户从 0.2.2 升级至 0.3.0 后发现 runtime context 行为不一致，影响依赖默认时区信息的场景。
- **内存健康担忧**：多个 PR（#5665、#5664、#5663）针对 OAuth flow、summary cache、thread context 的无界增长进行修复，反映用户/维护者对长期运行稳定性的关注。
- **session 标题缺失**：[#5647](https://github.com/HKUDS/nanobot/issues/5647) 用户在 WebUI 中发现 session 标题不生成，已修复（[#5658](https://github.com/HKUDS/nanobot/pull/5658)、[#5648](https://github.com/HKUDS/nanobot/pull/5648)）。

---

## 8. 待处理积压

| PR/Issue | 状态 | 积压时长 | 建议关注 |
|---|---|---|---|
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) feat(heartbeat): isolated_session config | 待合并 | ~71 天 | 功能完整，建议 review |
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) feat(heartbeat): model_override config | 待合并 | ~71 天 | 同上，配套功能 |
| [#5520](https://github.com/HKUDS/nanobot/pull/5520) feat: Langfuse tracing for Codex | 待合并 | ~12 天 | 可观测性重要补充 |
| [#5666](https://github.com/HKUDS/nanobot/pull/5666) feat: aimlapi.com provider | 待合并 | 1 天 | 合作 PR，建议优先合并 |
| [#5567](https://github.com/HKUDS/nanobot/issues/5567) 飞书流式卡片整合 | 无 PR | 9 天 | 需维护者评估是否纳入规划 |
| [#5661](https://github.com/HKUDS/nanobot/issues/5661) OpenCode session header | 有 PR #5662 | 1 天 | ⚠️ 2026-09-06 截止，建议紧急合并 |

---

**项目健康度总结：** 今日 NanoBot 维护节奏健康，Issue 响应迅速（3/5 关闭），PR 吞吐量高（28 条/天）。核心风险点为 **OpenCode session header 的时效性要求**（9 月 6 日截止）以及 **飞书渠道体验诉求尚无 PR 响应**。内存泄漏修复的集中出现表明项目正在经历从功能驱动向稳定性驱动的阶段过渡。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-09-05 | 数据周期：过去24小时**

---

## 1. 今日速览

Hermes Agent 今日保持高强度开发节奏，过去24小时共产生 **50 条 Issue** 和 **50 条 PR**，整体活跃度维持高位。社区反馈集中在三大领域：**Desktop 推理块显示缺陷**（多issue重复确认同一根因）、**SQLite 多进程写竞争导致状态库损坏**（P1 级稳定性问题）、以及 **SSH 远程模式认证回退**（401 连环回归）。开发侧同步推出 Group Chat 连续性功能补全（#98307/#98073）及多项 Windows/Desktop 稳定性修复，项目从功能完善与平台兼容性两个方向持续收敛。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭（3 条）
| PR | 类型 | 说明 |
|---|---|---|
| [#103394](https://github.com/NousResearch/hermes-agent/pull/103394) | Bugfix | `hermes cron` / `hermes webhook` 子命令现在正确传播非零退出码至 shell，修复之前静默成功的问题 |

### 重点进行中的 PR（待合并）
| PR | 类型 | 说明 |
|---|---|---|
| [#98307](https://github.com/NousResearch/hermes-agent/pull/98307) | Feature | **Group Chat 连续性完整实现**：Bot 在 Desktop 关闭后仍可跨网关收发消息和文件，用户可通过移动端检查状态、发送消息、检索文件 |
| [#98073](https://github.com/NousResearch/hermes-agent/pull/98073) | Feature | **从消息平台控制 Group Chat**：补充 Slack/Matrix 等网关侧的 Group Chat 管理命令（查看、消息、文件、暂停/重试、审批） |
| [#103399](https://github.com/NousResearch/hermes-agent/pull/103399) | Bugfix | 修复 20+ profile 场景下背景 tile  reconcile 耗尽本地后端池槽位的无限循环问题（#103375） |
| [#103400](https://github.com/NousResearch/hermes-agent/pull/103400) | Bugfix | Windows Desktop 更新时 QuickEdit 模式阻塞 PowerShell 句柄传递，已禁用 QuickEdit 修复 #103222 |
| [#103402](https://github.com/NousResearch/hermes-agent/pull/103402) | Bugfix | Windows terminal 工具 bash 探测死锁及孤儿进程清理 |
| [#103369](https://github.com/NousResearch/hermes-agent/pull/103369) | Bugfix | 修复 `--oneshot` 模式下 `--resume` 参数未传播的会话恢复问题 |
| [#98429](https://github.com/NousResearch/hermes-agent/pull/98429) | Bugfix | Terminal guards 误拦截含 `&` 的正常命令，现已修复扫描逻辑 |
| [#103395](https://github.com/NousResearch/hermes-agent/pull/103395) | Feature | `hermes doctor --quick` 跳过 npm audit 和 provider 连通性检查，适配 CI/启动钩子快速诊断 |
| [#103404](https://github.com/NousResearch/hermes-agent/pull/103404) | Feature | `pre_tool_call` 插件指令新增 `serve` 模式，允许插件直接提供结果而跳过工具执行 |

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issue
| Issue | 评论数 | 核心议题 |
|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 157 | Skills 索引超时失效（29.8h > 26h 阈值），自动化探针持续告警 |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 23 | Desktop 关闭后 Bot Group Chat 应保持运行（#98307 PR 正在解决） |
| [#18715](https://github.com/NousResearch/hermes-agent/issues/18715) | 18 👍29 | 远程 Agent + 本地工具执行的架构需求，获高赞同 |

### 📌 热点分析
- **Skills 索引老化**（#66616）：自 7 月持续告警至今，157 条评论显示社区对自动化维护可靠性的强烈关注，cron 调度（UTC 6/18）与部署流程的协调机制存在改进空间。
- **远程 Agent 架构**（#18715）：用户希望在本地机器执行工具但远程运行 Agent 大脑，涉及跨网段工具路由和安全边界，是典型的生产部署场景诉求。
- **Group Chat 连续性**（#97681）：随着 #98307 和 #98073 两个 PR 推进，该功能已进入验收阶段，预计将在下一版本正式交付。

---

## 5. Bug 与稳定性

### 🔴 P1 严重（功能阻塞级）
| Issue | 描述 | Fix PR |
|---|---|---|
| [#103339](https://github.com/NousResearch/hermes-agent/issues/103339) | 多 profile 主机上 SQLite `state.db` WAL 并发写入导致**4 天内 7 次损坏**，upstream 防护 fail-open | 作者提出 lazy flock 单写者门控方案，待评审 |
| [#102486](https://github.com/NousResearch/hermes-agent/issues/102486) | `hermes update` catch-up fleet restart 在 systemd 249 上因 `OOMPolicy=kill` 不被识别而**无限重试** | 待修复 |
| [#103313](https://github.com/NousResearch/hermes-agent/issues/103313) | Desktop SSH 远程模式所有敏感 API 调用返回 **401**，`mount_spa` 注入了过期 session token（regression from `5f1feb5344`） | 关联 #103054、#103366，涉及同一根因 |
| [#103054](https://github.com/NousResearch/hermes-agent/issues/103054) | SSH 连接成功后 Dashboard 仍提供过期 token，`/api/profiles` 持续 401 | 同上 |
| [#103366](https://github.com/NousResearch/hermes-agent/issues/103366) | Desktop SSH Isolated 模式：SSH 成功但 `refreshProfiles` 401，session token 不匹配 | 同上 |
| [#49664](https://github.com/NousResearch/hermes-agent/issues/49664) | Desktop `display.show_reasoning` 开关写入 config 但**渲染层从未读取**，推理块始终显示/隐藏一致 | 关联 #93817、#85110，同一根因多个用户验证 |
| [#93817](https://github.com/NousResearch/hermes-agent/issues/93817) | 推理块关闭后 Desktop 仍转储完整 agent trace（thinking tokens + 所有工具调用），**使 Desktop 不可用** | 同上 |
| [#85110](https://github.com/NousResearch/hermes-agent/issues/85110) | Desktop/TUI 无法提供纯答案模式，推理块和工具调用 chrome 无法隐藏 | 同上 |

### 🟡 P2 中等
| Issue | 描述 | Fix PR |
|---|---|---|
| [#103375](https://github.com/NousResearch/hermes-agent/issues/103375) | 20+ profile 下 Bot tiles 无限重连耗尽 local backend 池槽 | [#103399](https://github.com/NousResearch/hermes-agent/pull/103399) ✅ 待合并 |
| [#103398](https://github.com/NousResearch/hermes-agent/issues/103398) | Windows ACP 模式下 terminal 工具**挂起数分钟**，bash 启动探测死锁且孤儿进程无法 kill | [#103402](https://github.com/NousResearch/hermes-agent/pull/103402) ✅ 待合并 |
| [#103401](https://github.com/NousResearch/hermes-agent/issues/103401) | 多 profile 切换时报 `timed out while waiting for a free slot` | 待排查 |
| [#102619](https://github.com/NousResearch/hermes-agent/issues/102619) | 128GB M5 Max 上 Qwen3.8 27B 被错误标记为 "Too big for this machine" | 待修复 |
| [#96418](https://github.com/NousResearch/hermes-agent/issues/96418) | Loopback 绑定禁用 WS keepalive ping，反向代理后 PTY 子进程泄漏 | 待修复 |
| [#100610](https://github.com/NousResearch/hermes-agent/issues/100610) | Podman/Quadlet 容器中 UI 无法安装 pip 包（`_pip_install` 函数问题） | 待修复 |
| [#52382](https://github.com/NousResearch/hermes-agent/issues/52382) | PR #47856 移除 `messaging` toolset 后，旧配置启动时持续报 `Unknown toolsets: messaging` 警告 | 需 config migration |
| [#98022](https://github.com/NousResearch/hermes-agent/issues/98022) | `hermes update` catch-up fleet restart 在 stale interrupted receipt 时**无限重启** | 关联 #95294 |

---

## 6. 功能请求与路线图信号

| Issue | 诉求 | 路线图判断 |
|---|---|---|
| [#18715](https://github.com/NousResearch/hermes-agent/issues/18715) 👍29 | 远程 Agent + 本地工具执行 | 高优先级架构需求，涉及跨网段工具路由，短期难交付但社区呼声强 |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | Desktop 关闭后 Group Chat 保持运行 | **#98307 / #98073 已在开发中**，预计下一版本交付 |
| [#100428](https://github.com/NousResearch/hermes-agent/issues/100428) | `browser_exec` 按 session 选择 headed/headless 模式 | 低优先级工具增强，需浏览器工具模块配合 |
| [#100944](https://github.com/NousResearch/hermes-agent/issues/100944) | Kanban worker 按 profile 控制 create/link 权限 | 细粒度权限控制需求，待决策 |
| [#45562](https://github.com/NousResearch/hermes-agent/issues/45562) | Desktop 持久化 per-session 滚动/阅读位置 | 体验优化类，短期优先级低 |
| [#103368](https://github.com/NousResearch/hermes-agent/issues/103368) | Antigravity/Gemini ACP 支持 | 已在官方文档和 ACP Registry 中，可能已进入兼容测试 |
| [#103404](https://github.com/NousResearch/hermes-agent/pull/103404) | 插件 `pre_tool_call` 新增 `serve` 指令 | 插件扩展能力增强，已在 PR 中，预计纳入近期版本 |

---

## 7. 用户反馈摘要

### 核心痛点
1. **推理块无法隐藏**：多名用户（#49664、#93817、#85110）独立验证同一缺陷——设置 `display.show_reasoning: false` 后 Desktop 仍展示完整 thinking 和工具调用链，被描述为 "P0 / productivity-blocking" 和 "makes Hermes Desktop unusable"。

2. **SQLite 状态库损坏**：#103339 报告在 4 天内发生 7 次损坏，根因是 upstream 的并发写入防护 fail-open，多 profile 生产环境用户高度关注。

3. **SSH 远程 401 连环回归**：#103313、#103054、#103366 三个 issue 指向同一 commit 引入的 session token 注入错误，Desktop SSH 功能大面积不可用。

4. **Windows 平台稳定性**：terminal 工具挂起（#103398）、QuickEdit 阻塞更新（#103400）反映 Windows 端的边缘场景覆盖不足。

### 正面反馈
- Group Chat 跨设备连续性功能（#97681）获得积极关注，用户期待在移动端管理 Bot 协作。
- `hermes doctor --quick`（#103395）针对 CI/启动钩子的快速诊断路径获得认可。
- 插件 `serve` 指令（#103404）被看作增强插件生态灵活性的关键能力。

---

## 8. 待处理积压

| Issue | 天数 | 风险 | 建议 |
|---|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) Skills 索引老化 | ~49 天 | 自动化信任度下降 | 审查 cron 调度频率与重建可靠性 |
| [#18715](https://github.com/NousResearch/hermes-agent/issues/18715) 远程 Agent + 本地工具 | ~126 天 👍29 | 高价值架构需求长期未响应 | 纳入架构讨论或拆分 MVP |
| [#52382](https://github.com/NousResearch/hermes-agent/issues/52382) `messaging` toolset 迁移 | ~72 天 | 启动警告噪音影响体验 | 添加 config migration 清理陈旧 toolset 名 |
| [#98022](https://github.com/NousResearch/hermes-agent/issues/98022) Fleet restart 无限循环 | ~38 天 | 生产环境自动更新可能死循环 | 审查 `update_receipts/latest.json` 刷新逻辑 |
| [#96418](https://github.com/NousResearch/hermes-agent/issues/96418) WS keepalive 泄漏 | ~39 天 | 反向代理部署下 PTY 进程泄漏 | 修复 loopback 绑定对 keepalive 的影响 |
| [#102619](https://github.com/NousResearch/hermes-agent/issues/102619) "Too big" 误标 | 2 天 | Mac 统一内存设备兼容性 | 检查模型大小估算逻辑是否考虑 unified memory |

---

**项目健康度评估：🟡 需注意**

开发侧 PR 流水持续（今日 50 条），Group Chat 等功能推进积极；但 **P1 级 Bug 集中度较高**（SQLite 损坏、SSH 401、推理块失效），且部分问题存在多 issue 重复验证的情况，建议维护者优先闭环这三类根因，以避免用户信任持续流失。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期**：2026-09-05  
**数据来源**：GitHub (sipeed/picoclaw) 过去 24 小时更新

---

### 1. 今日速览
过去 24 小时内，PicoClaw 保持高频开发节奏，共产生 22 条 PR 更新（20 条已合并/关闭），3 条新 Issue 处于活跃状态。项目当前处于**稳定性加固与生态扩展并重**的阶段，无新版本发布。整体健康度良好，核心引擎容错、多平台渠道适配及第三方 LLM Provider 兼容性均有实质性推进，社区贡献活跃且维护者响应及时。

### 2. 版本发布
暂无新版本发布。

### 3. 项目进展
今日合并/关闭的 PR 集中推动了三条主线，项目整体稳健性显著提升：
- **Provider 生态拓宽**：陆续接入 GitHub Copilot stdio 传输（[#2240](https://github.com/sipeed/picoclaw/pull/2240)）、xAI 兼容路由（[#2260](https://github.com/sipeed/picoclaw/pull/2260)）、Azure AI Foundry 主机识别与 Prompt Caching（[#1860](https://github.com/sipeed/picoclaw/pull/1860)），并完善 OpenAI 严格模式与流式 Usage 上报（[#1683](https://github.com/sipeed/picoclaw/pull/1683)、[#2522](https://github.com/sipeed/picoclaw/pull/2522)）。
- **Agent 核心防御升级**：修复上下文溢出误判（[#2016](https://github.com/sipeed/picoclaw/pull/2016)）、SystemParts 未计入 Token 估算（[#2014](https://github.com/sipeed/picoclaw/pull/2014)）、工具调用 ID 重复导致 400 错误（[#1854](https://github.com/sipeed/picoclaw/pull/1854)）等底层缺陷，推理链路容错能力明显增强。
- **渠道与安全性加固**：完成 Telegram、Slack、Feishu 多项流式/路由 Bug 修复，并新增默认开放机器人的安全审计拦截（[#2088](https://github.com/sipeed/picoclaw/pull/2088)）及 Exec 脚本预检 fail-closed 机制（[#2298](https://github.com/sipeed/picoclaw/pull/2298)）。
- **文档与工具链**：合入 Parallel Search 与 Pilot MCP 的零配置接入指南（[#3368](https://github.com/sipeed/picoclaw/pull/3

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目动态日报 — 2026-09-05

---

## 1. 今日速览

NullClaw 在过去24小时内保持**低活跃度**，社区共发起 1 条 Issue，无新 PR 提交，无版本发布。今日焦点 Issue #993 围绕自托管场景下的 Firecrawl 搜索端点配置化需求展开，反映出项目自托管用户群体对灵活配置的强烈诉求。整体项目健康度平稳，社区参与度温和，暂无阻塞性 Bug 或紧急合并事项。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 合并或关闭。项目代码贡献层面无变动，维护者尚未处理新的特性或修复请求。

> 🔗 无相关链接

---

## 4. 社区热点

**Issue #993 — feat: make Firecrawl search endpoint configurable for self-hosted instances**

- 作者: @Crymfox
- 创建: 2026-08-24 | 最新更新: 2026-09-04
- 评论: 1 | 👍: 0
- 标签: `[OPEN]` `[enhancement]`

[🔗 Issue #993](https://github.com/nullclaw/nullclaw/issues/993)

**诉求分析**：该 Issue 指出 `src/tools/web_search_providers/firecrawl.zig` 中 Firecrawl API 端点被硬编码为 `https://api.firecrawl.dev/v1/search`，导致自托管 Firecrawl 实例的用户无法利用原生 `search_provider: "firecrawl"` 功能。评论数为 1，说明已有初步讨论或维护者回应，但尚未有维护者或贡献者提交修复 PR。该需求在自托管部署场景中具备较高的通用价值。

---

## 5. Bug 与稳定性

今日无 Bug 报告或稳定性问题。

> 🔗 无相关链接

---

## 6. 功能请求与路线图信号

| 优先级 | 请求内容 | Issue 链接 | 路线图信号 |
|--------|----------|------------|------------|
| 🟡 中 | 支持自定义 Firecrawl 端点以适配自托管部署 | [Issue #993](https://github.com/nullclaw/nullclaw/issues/993) | 自托管用户群体持续反馈，具备纳入下一版本的合理性；当前无配套 PR，需维护者评估是否作为配置项暴露 |

**判断**：该功能请求属于**配置扩展类**需求，不涉及核心架构变更，实现成本较低。建议维护者评估是否引入环境变量或配置文件覆盖端点，以兼容自托管 Firecrawl 实例。

---

## 7. 用户反馈摘要

从 Issue #993 的摘要中提取用户核心痛点：

- **痛点**：硬编码端点导致自托管 Firecrawl 用户无法使用内置搜索功能，必须绕开 `search_provider` 机制或自行 fork 修改源码。
- **使用场景**：企业内部或私有化部署环境，用户已自托管 Firecrawl 服务，希望 NullClaw 能直接对接自有实例而非官方云服务。
- **满意度**：当前体验为负面，用户反馈受阻于代码层面的限制，缺乏灵活的配置入口。

---

## 8. 待处理积压

| 类型 | Issue / PR | 创建时间 | 评论数 | 状态 | 建议关注优先级 |
|------|------------|----------|--------|------|----------------|
| Enhancement | [#993](https://github.com/nullclaw/nullclaw/issues/993) — Firecrawl 端点配置化 | 2026-08-24 | 1 | OPEN | 🟡 中 |

**提醒**：Issue #993 创建于 2026-08-24，距今已超过 10 天，当前仅有 1 条评论且无配套 PR。建议维护者尽快确认需求范围并给出回应，或引导社区贡献者提交修复方案。

---

*日报生成时间：2026-09-05 | 数据来源：nullclaw/nullclaw GitHub*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报

**日期：2026-09-05** | 数据来源：[nearai/ironclaw](https://github.com/nearai/ironclaw)

---

## 1. 今日速览

今日 IronClaw 保持中高强度开发节奏，24 小时内共产生 **15 条活动记录**（3 Issues + 12 PRs）。其中 **3 条 PR 已合并/关闭**，全部聚焦于 Telegram 集成体验优化，修复了未配对用户首次接触时的错误提示与 API 配置缺失时的用户误导问题。同时，WebUI 团队连续提交 4 个 PR（#8068–#8071）集中修复命令结果卡片的交互与布局问题，显示前端体验正在快速收敛。整体项目健康度良好，Bug 修复与功能完善并行推进。

---

## 2. 版本发布

**无新版本发布。** 当前处于功能迭代与 Bug 修复阶段，未触发 Release。

---

## 3. 项目进展

### 已合并/关闭的 PR（3 条）

| PR | 类型 | 摘要 | 推进方向 |
|----|------|------|----------|
| [#8073](https://github.com/nearai/ironclaw/pull/8073) | Bug Fix | 将 Telegram 个人账号链接失败提示从"你的账户有问题"改为"管理员未配置" | 改善部署端错误可观测性 |
| [#8054](https://github.com/nearai/ironclaw/pull/8054) | Bug Fix | 未配对用户首次 `/start` 现在优先展示配对引导，而非命令清单 | 修复首次接触体验断裂 |
| [#8062](https://github.com/nearai/ironclaw/pull/8062) | Bug Fix | OpenAI 请求路径现在正确传递对话缓存密钥 | 修复 LLM 缓存失效问题 |

**整体判断：** 今日 3 条合并 PR 均属于体验修复类，无架构性变更。项目在主线上稳步收敛 Telegram 集成和 LLM 通路的已知缺陷，为后续功能释放奠定基础。

---

## 4. 社区热点

### 高关注 Issue

- **[#8074](https://github.com/nearai/ironclaw/issues/8074)** [OPEN] — 已配对用户在看未连接的共享频道时，收到的是针对"未配对用户"的连接提示文案，而非"频道未连接"的准确说明。*这是今日唯一新开的 Issue，由同一作者（thisisjoshford）连续提交，反映其对 Telegram 渠道错误提示一致性的系统性关注。*

### 已解决热点 Issue

- **[#7956](https://github.com/nearai/ironclaw/issues/7956)** [CLOSED] — 未配对用户点击 `/start` 后看到命令清单而非配对引导。已通过 #8054 修复。
- **[#7955](https://github.com/nearai/ironclaw/issues/7955)** [CLOSED] — 管理员未配置 `api_id`/`api_hash` 时，用户看到 generic "Something went wrong"。已通过 #8073 修复。

**诉求分析：** 用户和贡献者对 Telegram 渠道的错误提示准确性有明确期望，当前的修复方向与社区诉求一致，预计后续会持续扫描同类文案不一致问题。

---

## 5. Bug 与稳定性

| 等级 | Issue/PR | 描述 | Fix 状态 |
|------|----------|------|----------|
| 🟡 中 | [#8074](https://github.com/nearai/ironclaw/issues/8074) | 已配对用户在未连接频道收到错误的配对提示文案 | ❌ 未修复 |
| 🟢 低 | [#8059](https://github.com/nearai/ironclaw/pull/8059) [OPEN] | `POST /api/v1/responses/{id}/cancel` 在所有状态下均返回 400，取消功能完全失效 | 🔶 有 PR 待合并 |
| 🟢 低 | [#7956](https://github.com/nearai/ironclaw/issues/7956) | 未配对用户首次接触展示错误引导 | ✅ #8054 已修复 |
| 🟢 低 | [#7955](https://github.com/nearai/ironclaw/issues/7955) | Telegram API 未配置时展示 generic 错误 | ✅ #8073 已修复 |

**稳定性评估：** 今日无崩溃类 Bug 上报。主要风险点在于取消响应 API（#8059）和频道连接提示不一致（#8074），两者均不影响核心流程但影响用户体验。

---

## 6. 功能请求与路线图信号

### 已确认推进中的功能

| PR | 功能 | 状态 | 版本预测 |
|----|------|------|----------|
| [#8072](https://github.com/nearai/ironclaw/pull/8072) | Telegram Bot API 命令菜单注册（`setMyCommands`） | 🟡 待合并 | 下一版本 |
| [#8067](https://github.com/nearai/ironclaw/pull/8067) | Subagent 后台交付自愈机制（启动 sweep + 定期扫描） | 🟡 待合并 | 下一版本 |
| [#8061](https://github.com/nearai/ironclaw/pull/8061) | Subagent 并发子节点上限控制 | 🟡 待合并 | 下一版本 |
| [#8069](https://github.com/nearai/ironclaw/pull/8069) | WebUI 命令结果卡片添加关闭操作 | 🟡 待合并 | 下一版本 |
| [#8070](https://github.com/nearai/ironclaw/pull/8070) | WebUI 斜杠命令元数据对齐（响应式网格） | 🟡 待合并 | 下一版本 |
| [#8071](https://github.com/nearai/ironclaw/pull/8071) | WebUI 命令结果卡片高度保护（防收缩） | 🟡 待合并 | 下一版本 |
| [#8068](https://github.com/nearai/ironclaw/pull/8068) | WebUI 斜杠命令导航时保持活跃选项可见 | 🟡 待合并 | 下一版本 |

**路线图信号：** 当前迭代重点集中在 **Telegram 渠道体验完善** 和 **WebUI 交互精细化** 两个方向，subagent 可靠性也在持续加固。预计下一个 Release 将包含上述 9 个待合并 PR 的主要内容。

---

## 7. 用户反馈摘要

### 痛点提炼

1. **Telegram 渠道错误提示不精准**（#7955, #7956, #8074）
   - 用户反馈集中在"看到的是通用错误而非针对性提示"，涉及未配对、API 未配置、频道未连接三种场景，说明当前错误处理层缺乏按上下文分支的文案策略。

2. **取消响应 API 完全不可用**（#8059）
   - 贡献者指出 `cancel_response` 硬编码的 reason 与 `parse_cancel_reason` 不匹配，导致取消请求永远返回 400。这是一个影响功能可用性的回归。

3. **WebUI 命令结果卡片体验问题**
   - 卡片高度收缩、斜杠命令元数据对齐、活跃选项不可见等问题集中由 `italic-jinxin` 提交修复，反映用户在复杂命令交互场景中存在滚动和视觉对齐痛点。

### 满意度信号
- `thisisjoshford` 连续修复 Telegram 体验类 Issue，说明维护者对用户反馈响应迅速。
- WebUI 团队一次性提交 4 个修复 PR，显示对交互细节的重视。

---

## 8. 待处理积压

| 类型 | 编号 | 描述 | 建议优先级 |
|------|------|------|----------|
| 🐛 Bug | [#8074](https://github.com/nearai/ironclaw/issues/8074) | 已配对用户在未连接频道收到配对提示文案 | 高 — 同一作者系统性修复中的遗漏 |
| 🐛 Bug | [#8059](https://github.com/nearai/ironclaw/pull/8059) | 取消响应 API 永远返回 400 | 高 — 功能完全失效 |
| 📦 PR 积压 | 9 条 OPEN PR | 含 Telegram 命令菜单、Subagent 自愈、WebUI 交互优化等 | 中 — 按 size 优先级推进 |
| 📦 PR 积压 | [#7988](https://github.com/nearai/ironclaw/pull/7988) | 代码库知识图谱刷新（CI 自动触发） | 低 — 常规维护 |

---

**报告生成时间：** 2026-09-05 | **分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报
**日期：2026-09-05** | 数据周期：2026-09-04 00:00 ~ 2026-09-05 00:00

---

## 1. 今日速览

LobsterAI 今日保持高活跃度，24小时内完成 **33 条 PR 更新**（28 条已合并/关闭），发布 **2 个新版本**（v2026.9.3 / v2026.9.4），迭代节奏紧凑。核心更新聚焦于**交互式浏览器体验**、**协作功能认证流程优化**及**订阅恢复引导**三大方向。Issue #1071 关于 SQLite 存储层数据完整性的缺陷审计持续活跃，提醒社区关注底层可靠性。整体项目健康度良好，开发与合并流速均处于高位。

---

## 2. 版本发布

### v2026.9.4（2026-09-04）
**链接：** [#2618](https://github.com/netease-youdao/LobsterAI/pull/2618)

**核心变更：**
| 功能 | 说明 | PR |
|------|------|-----|
| `feat(browser)` | 恢复交互式内置浏览器功能 | [#2602](https://github.com/netease-youdao/LobsterAI/pull/2602) |
| `feat(update)` | 安装更新前弹出确认提示，防止误操作退出 | [#2609](https://github.com/netease-youdao/LobsterAI/pull/2609) |
| `feat(publishing)` | 完善订阅恢复引导与资源状态同步 | [#2613](https://github.com/netease-youdao/LobsterAI/pull/2613) |
| `fix(browser)` | 支持 Unicode Windows 安装路径 | [#2615](https://github.com/netease-youdao/LobsterAI/pull/2615) |
| `fix(ci)` | 限制 Skill 审计时长，防止 npm audit 超时 | [#2616](https://github.com/netease-youdao/LobsterAI/pull/2616) |

**破坏性变更 / 迁移注意：** 无。

---

### v2026.9.3（2026-09-03）
**链接：**（本次版本对应合并 PR 集合）

**核心变更：**
| 功能 | 说明 | PR |
|------|------|-----|
| `feat(cowork)` | 未认证用户发起聊天前显示登录提示 | [#2573](https://github.com/netease-youdao/LobsterAI/pull/2573) |
| `feat(browser)` | 新增交互式内置浏览器功能（初始实现） | [#2574](https://github.com/netease-youdao/LobsterAI/pull/2574) |
| `feat(onboarding)` | 优化新用户引导流程 | - |

**破坏性变更 / 迁移注意：** 无。

---

## 3. 项目进展

今日 28 条 PR 已完成合并，主要推进以下方向：

### 🔧 浏览器与用户交互体验
- **#2617**（进行中）：优化内置浏览器登录反馈、标签页管理（可滚动标签条、相邻关闭行为）[链接](https://github.com/netease-youdao/LobsterAI/pull/2617)
- **#2602 / #2574**：交互式浏览器功能从初始实现到恢复稳定，完成闭环
- **#2503**：为可编辑文本控件添加上下文菜单（剪切/复制/粘贴/全选），提升跨平台一致性 [链接](https://github.com/netease-youdao/LobsterAI/pull/2503)

### 🏢 协作（Cowork）与认证流程
- **#2573**：未认证用户尝试聊天时弹出欢迎登录弹窗，改善新用户转化路径 [链接](https://github.com/netease-youdao/LobsterAI/pull/2573)
- **#2596**：新增聊天登录 CTA 点击埋点，完善数据分析能力 [链接](https://github.com/netease-youdao/LobsterAI/pull/2596)
- **#2612**：修复登录刷新期间模型选择丢失问题 [链接](https://github.com/netease-youdao/LobsterAI/pull/2612)

### ☁️ 发布订阅与 Artifact
- **#2613**：完善订阅恢复入口（Artifact/资料库/站点详情页均新增入口），支持自动恢复与重新部署两种方式，并补充全链路埋点 [链接](https://github.com/netease-youdao/LobsterAI/pull/2613)

### 🛡️ 工程稳定性
- **#2616**：CI 中 Skill 审计增加 90 秒上限，防止 npm audit 超时阻塞流水线 [链接](https://github.com/netease-youdao/LobsterAI/pull/2616)
- **#2520**：插件安装异常弹窗增加独立滚动，防止长错误日志遮挡操作按钮 [链接](https://github.com/netease-youdao/LobsterAI/pull/2520)

---

## 4. 社区热点

### 🔴 重点关注 Issue

**[#1071] SQLite 存储层三个数据完整性/可靠性缺陷**
- 状态：OPEN / stale | 创建：2026-03-30 | 最近更新：2026-09-04
- 作者：MaoQianTu
- [链接](https://github.com/netease-youdao/LobsterAI/issues/1071)

**问题摘要：**
1. **`ON DELETE CASCADE` 完全失效** — `cowork_messages` 表外键级联删除不生效，导致孤儿消息无限累积
2. **`save()` 非原子写** — SQLite 写入非原子操作，崩溃时可能导致数据库损坏
3. **`storeInitPromise` 超时后永久故障** — 初始化超时后无恢复机制，存储层永久不可用

**分析：** 该 Issue 由社区安全审计触发，涉及生产环境数据丢失风险。目前标记为 stale，已逾 5 个月未获官方回复，建议维护者优先跟进。

---

## 5. Bug 与稳定性

| 严重程度 | 问题 | 状态 | Fix PR |
|----------|------|------|--------|
| 🟡 中 | 插件安装异常时错误日志过长，操作按钮被遮挡 | 已修复 | [#2520](https://github.com/netease-youdao/LobsterAI/pull/2520) ✅ |
| 🟡 中 | 登录刷新期间选中的模型显示丢失 | 已修复 | [#2612](https://github.com/netease-youdao/LobsterAI/pull/2612) ✅ |
| 🟢 低 | Unicode Windows 安装路径导致浏览器启动失败 | 已修复 | [#2614](https://github.com/netease-youdao/LobsterAI/pull/2615) ✅ |
| 🔴 高（潜在） | SQLite CASCADE 失效 / 非原子写 / 初始化超时永久故障 | 未修复 | — |

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 判断 |
|------|------|------|
| 内置浏览器用户体验持续打磨 | #2617、#2615、#2602 | 已纳入近期路线图，预计 v2026.9.5 继续迭代 |
| 订阅恢复流程完整化 | #2613 | 已合并，预计将在 v2026.9.5 版本文档中补充说明 |
| 协作功能登录转化优化 | #2573、#2596 | 新功能已上线，下一步可能跟进 A/B 实验数据 |
| 技能升级进度覆盖优化 | #2501 | 已合并，反馈渲染稳定性改进 |

---

## 7. 用户反馈摘要

- **浏览器功能**：用户对交互式内置浏览器的回归（#2602）和 Unicode 路径支持（#2615）反馈积极，说明该功能是高优先级需求
- **订阅管理**：PR #2613 增加了订阅恢复的埋点覆盖，侧面反映用户对"发布站点订阅状态同步"存在痛点
- **认证流程**：#2573 明确针对未认证用户的聊天拦截场景，说明匿名体验与账号转化的平衡是社区关注点
- **SQLite 审计**：Issue #1071 的评论数为 1，但问题描述详尽，来自专业审计视角，潜在影响面大

---

## 8. 待处理积压

| 类型 | 编号 | 描述 | 久暂 | 建议 |
|------|------|------|------|------|
| 🔴 Issue | [#1071](https://github.com/netease-youdao/LobsterAI/issues/1071) | SQLite 存储层 CASCADE/原子写/初始化超时缺陷 | 5 个月 | 优先级提升，考虑安排专项修复 |
| 🟡 PR | [#2617](https://github.com/netease-youdao/LobsterAI/pull/2617) | 浏览器登录与标签页体验优化 | 1 天 | 待合并，可尽快跟进 |
| 🟡 PR | [#2614](https://github.com/netease-youdao/LobsterAI/pull/2614) | 测试模式服务端 API 地址修正 | 1 天 | 待合并 |

---

**📊 项目健康度评估**

| 指标 | 数值 | 评级 |
|------|------|------|
| PR 合并率 | 28/33 ≈ **84.8%** | 🟢 优秀 |
| Issue 日新增 | 1 条 | 🟢 正常 |
| 版本发布频率 | 2 版本/日 | 🟢 活跃 |
| 长期未响应 Issue | 1 条（#1071） | 🟡 需关注 |

> **总结**：LobsterAI 今日迭代效率较高，浏览器与协作体验持续完善。SQLite 存储层数据完整性问题（#1071）是潜在最大风险点，建议维护者优先评估修复方案。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-09-05

## 1. 今日速览

Moltis 项目今日保持**中等活跃度**，共收到 1 条新 Issue 与 1 条待合并 PR，无新版本发布。社区贡献者持续围绕外部智能体集成与用户体验优化方向推进工作，整体开发节奏平稳有序，健康度良好。

## 2. 版本发布

本日无新版本发布。

## 3. 项目进展

**[PR #1258](https://github.com/moltis-org/moltis/pull/1258) — feat(external-agents): add direct AGY streaming**

- **作者**：GTanger
- **状态**：待合并（OPEN）
- **内容**：为官方 `agy` CLI 添加第一类流式传输支持，复用其已有 Google OAuth 会话，无需 Gemini CLI 或 API Key；将 AGY 版本化的 `stream-json` 输出转换为 Moltis 标准的文本、推理、通知、工具调用、子智能体、用量及可恢复会话格式。
- **意义**：扩展了 Moltis 与外部智能体系统的集成能力，降低了用户接入 AGY 的门槛，是项目"外部智能体生态"路线图的重要一步。

## 4. 社区热点

**[Issue #1259](https://github.com/moltis-org/moltis/issues/1259) — Configurable default reasoning/thinking level (persist across sessions)**

- **状态**：OPEN | 标签：`enhancement` | `Feature`
- **作者**：Scentedtiger | 创建时间：2026-09-05
- **热度**：0 评论，0 👍
- **分析**：用户希望将推理/思考层级配置为默认值并跨会话持久化。该诉求反映了高级用户对长期对话一致性与可定制化的需求，与当前 AI 助手工具向"个性化记忆"演进的趋势一致。若后续 PR 跟进，有望纳入路线图。

## 5. Bug 与稳定性

今日无新 Bug 报告、崩溃或回归问题记录。

## 6. 功能请求与路线图信号

| 请求 | Issue 链接 | 优先级信号 | 可能纳入版本 |
|------|-----------|-----------|-------------|
| 可配置的默认推理/思考层级（跨会话持久化） | [#1259](https://github.com/moltis-org/moltis/issues/1259) | 中等（新诉求，尚无评论/赞） | 待定，需观察社区响应 |

结合 PR #1258（AGY 流式集成）的推进，项目当前重点聚焦于**外部智能体互操作性**与**用户个性化配置**两个方向。

## 7. 用户反馈摘要

- **Issue #1259**：用户希望对推理深度进行持久化配置，暗示当前 Moltis 可能每次新建会话需重新设定推理层级，造成使用摩擦。
- **PR #1258**：贡献者选择复用 AGY 现有 OAuth 会话，说明用户生态中已存在对"免 API Key 接入"的强烈需求，降低集成复杂度是明确方向。

## 8. 待处理积压

- **[PR #1258](https://github.com/moltis-org/moltis/pull/1258)**：创建于 2026-09-04，至今仍在待合并状态，无评论反馈。建议维护者尽快 review，避免贡献者冷却。
- **[Issue #1259](https://github.com/moltis-org/moltis/issues/1259)**：今日新开，尚无社区互动。可考虑维护者主动回应以确认需求范围。

---

**项目健康度评估**：🟢 良好 — 贡献流稳定，方向清晰，无阻塞性 Bug。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# 📊 CoPaw 项目动态日报 — 2026-09-05

> 数据周期：2026-09-04 00:00 ~ 2026-09-05 00:00 UTC
> 数据来源：[agentscope-ai/CoPaw](https://github.com/agentscope-ai/CoPaw)

---

## 1. 今日速览

过去 24 小时 CoPaw 社区活跃度**较高**：Issue 共 23 条（15 新开/活跃，8 已关闭），PR 共 26 条（20 待合并，6 已合并/关闭）。无新版本发布，但多项关键 Bug 与体验改进被推进解决，包括 Loop 模式状态持久化、MCP 工具白名单强制执行、桌面端启动性能优化等。社区对多租户版 QwenPaw Hub（2.2.0）的讨论持续升温（Issue #7318，22 条评论）。整体项目健康度良好，开发节奏稳定。

---

## 2. 版本发布

> ❌ 今日无新版本发布。

上一版本动向：2.2.0-beta.7 / 2.2.1b1 系列仍有部分问题待解决（见 Bug 章节）。

---

## 3. 项目进展

### 已合并 / 关闭的重要 PR

| PR | 类型 | 摘要 | 关联 Issue |
|----|------|------|-----------|
| [#7183](https://github.com/agentscope-ai/CoPaw/pull/7183) | Feature | 新增 workspace-scoped Skill preload 配置，支持对高频 Skill 启用预加载以减少首轮工具调用延迟 | [#7182](https://github.com/agentscope-ai/CoPaw/issues/7182) |
| [#7504](https://github.com/agentscope-ai/CoPaw/pull/7504) | Fix | 修复 MCP per-tool 白名单未在执行路径生效的问题，禁用工具不再出现在 agent 工具集中 | [#7470](https://github.com/agentscope-ai/CoPaw/issues/7470) |
| [#7560](https://github.com/agentscope-ai/CoPaw/pull/7560) | Fix | 修复切换页面/会话后 Loop 模式状态丢失问题，正确保留用户选择的 Mode 查询参数 | [#7555](https://github.com/agentscope-ai/CoPaw/issues/7555)、[#7552](https://github.com/agentscope-ai/CoPaw/issues/7552) |

**进展评估：** 今日 3 个关闭 PR 均聚焦用户体验与一致性修复，其中 MCP 白名单修复（#7504）涉及安全治理路径，具有较高优先级。Skill preload 功能（#7183）为 2.2.x 多租户能力打下基础。

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issue / PR

**Issue #7318 — QwenPaw Hub 多租户版 roadmap 社区共创**
- 作者：rayrayraykk | 评论：**22** | 👍 3 | 更新于 2026-09-04
- [链接](https://github.com/agentscope-ai/CoPaw/issues/7318)
- **摘要：** 社区反复呼声最高的多用户/团队管理需求，官方确认将在 2.2.0 推出 QwenPaw Hub 多租户版本。此 Issue 已链接多个相关社区诉求（#2324 等），是 2.2.0 的核心路线信号。

**Issue #7505 — 局域网 LLM Server 频繁 client disconnect 导致超时**
- 作者：yjyz1011 | 评论：12 | 更新于 2026-09-04
- [链接](https://github.com/agentscope-ai/CoPaw/issues/7505)
- **摘要：** 使用 LM Studio 作为局域网 LLM 后端时，streaming 连接频繁断开并触发重试最终超时，影响实际生产使用。

**Issue #6921 — 多步骤任务执行中自动停止、需用户手动"继续"**
- 作者：rerbin | 评论：12 | 已关闭
- [链接](https://github.com/agentscope-ai/CoPaw/issues/6921)
- **摘要：** 模型输出规划类消息（如"Let me do all three"）后任务静默停止，需用户说"继续"才能推进。

**PR #7486 — Creator 插件重大更新**
- 作者：xuanrui-L | 更新于 2026-09-05（今日最新）
- [链接](https://github.com/agentscope-ai/CoPaw/pull/7486)
- **摘要：** 包含 runtime notification bus、异步委托、多时间线 A/B 对比、T2V/I2V/S2V 调度、专业媒体提示词等多项新功能，是 Creator 模块的重要迭代。

---

## 5. Bug 与稳定性

| 严重级别 | Issue | 描述 | Fix PR | 状态 |
|---------|-------|------|--------|------|
| 🔴 高 | [#7559](https://github.com/agentscope-ai/CoPaw/issues/7559) | 任务执行中通过对话框发消息触发 409 错误（`A task is already running`） | — | OPEN |
| 🔴 高 | [#7534](https://github.com/agentscope-ai/CoPaw/issues/7534) | 飞书会话 queue consumer 卡死后会话静默无响应，新消息无法新建 consumer | — | OPEN |
| 🔴 高 | [#7567](https://github.com/agentscope-ai/CoPaw/issues/7567) | 点击停止后 UI 显示已停止，但实际任务仍在执行，再次发送消息触发 409 | — | OPEN |
| 🟡 中 | [#7549](https://github.com/agentscope-ai/CoPaw/issues/7549) | 火山引擎 Ark Responses API 拒绝以 assistant text turn 结尾的请求（400 MissingParameter: partial） | — | OPEN |
| 🟡 中 | [#7548](https://github.com/agentscope-ai/CoPaw/issues/7548) | 对话切换或重启后导航记录丢失（history.db 中内容完整但 UI 不展示） | — | OPEN |
| 🟡 中 | [#7510](https://github.com/agentscope-ai/CoPaw/issues/7510) | `/memory/status` 在 v2.2.0-beta.7 Desktop 返回 500 | — | ✅ 已关闭 |
| 🟢 低 | [#7554](https://github.com/agentscope-ai/CoPaw/issues/7554) | Windows 下 shell 工具子进程继承 console stdin，导致卡死且 Ctrl+C 无法终止 | — | OPEN |
| 🟢 低 | [#7023](https://github.com/agentscope-ai/CoPaw/issues/7023) | Desktop 启动时 Playwright Chromium 安装阻塞 ~60s，无 skip/lazy-load 选项 | — | ✅ 已关闭 |
| 🟢 低 | [#7367](https://github.com/agentscope-ai/CoPaw/issues/7367) | 仅启用 console 渠道时启动仍需 30-45s（无条件 import 全部 18 个渠道模块） | — | OPEN |

**稳定性评估：** 今日共报告 8 个新 Bug，其中 3 个高严重度（409 冲突、飞书 consumer 卡死、停止按钮失效）均与任务生命周期管理相关，建议维护者优先关注。**#7567 与 #7559 可能存在关联**（停止失效 → 残留任务 → 新消息触发 409）。

---

## 6. 功能请求与路线图信号

| Issue / PR | 类型 | 摘要 | 纳入下一版本可能性 |
|-----------|------|------|------------------|
| [#7318](https://github.com/agentscope-ai/CoPaw/issues/7318) | 路线图讨论 | QwenPaw Hub 多租户版，2.2.0 推出 | ✅ 已确认 |
| [#7568](https://github.com/agentscope-ai/CoPaw/issues/7568) | Enhancement | 闲时任务调度（Off-peak Task），利用模型厂商低谷 Token 折扣降低成本 | 🟡 可能，需评估实现复杂度 |
| [#7558](https://github.com/agentscope-ai/CoPaw/issues/7558) | Enhancement | 可插拔关系型存储后端（PostgreSQL/MySQL），替代 SQLite WAL，适配 K8s/Docker Swarm 部署 | 🟡 企业版/高级场景需求 |
| [#7556](https://github.com/agentscope-ai/CoPaw/issues/7556) | Enhancement | MCP driver 级 fallback chain，策略拒绝时自动降级 | 🟡 多 Agent 部署场景 |
| [#7557](https://github.com/agentscope-ai/CoPaw/issues/7557) | Enhancement | Skill 版本与依赖元数据管理（skill_pool） | 🟡 需配套工具链 |
| [#7550](https://github.com/agentscope-ai/CoPaw/issues/7550) | Enhancement | 镜像安装场景下预装 Codex CLI 等第三方 Agent | 🟢 低垂果实，可能纳入 |
| [#7541](https://github.com/agentscope-ai/CoPaw/issues/7541) | Enhancement | 修复按渠道隔离会话的架构问题，统一用户会话视图 | 🟡 架构级改动，需审慎 |
| [PR #7565](https://github.com/agentscope-ai/CoPaw/pull/7565) | Feature | Plugin 干净卸载 + rollback-safe 热重载 | 🟡 已提交 Review |
| [PR #6960](https://github.com/agentscope-ai/CoPaw/pull/6960) | Feature | PawPort 导入流程（从 Codex/Qoder 迁移设置、Skill、项目） | 🟡 已提交 Review |
| [PR #7378](https://github.com/agentscope-ai/CoPaw/pull/7378) | Feature | QwenPaw Native Mobile（Expo/React Native） | 🟡 Draft 阶段 |

---

## 7. 用户反馈摘要

### 痛点 TOP 3

1. **任务生命周期管理混乱**（#7559、#7567、#7552、#7555）
   - 用户反馈：停止按钮 UI 与后端状态不同步；切换页面后 Loop 模式选择丢失；执行中发消息触发 409 冲突。
   - 核心诉求：任务状态机需严格一致，UI 与实际执行状态实时对齐。

2. **启动性能**（#7023、#7367）
   - 用户反馈：即使只用 console 渠道，启动仍需 30-45s，根因是无条件 import 全部 18 个渠道模块及 Playwright Chromium 阻塞。
   - 核心诉求：按需懒加载渠道模块，支持跳过/延迟安装浏览器。

3. **多模型/多通道兼容性**（#7505、#7549）
   - 用户反馈：局域网 LM Studio 连接不稳定；火山引擎 Ark API 对 assistant turn 结尾的请求返回 400。
   - 核心诉求：增强 LLM 客户端的连接健壮性与 API 兼容性。

### 正面反馈

- Skill preload 功能（#7182/#7183）解决了"每个新对话都需重新发现工具"的首轮延迟问题。
- MCP 工具白名单强制执行（#7470/#7504）补上了安全治理的缺口。

---

## 8. 待处理积压

### ⚠️ 需维护者关注

| Issue / PR | 等待时长 | 说明 |
|-----------|---------|------|
| [#7367](https://github.com/agentscope-ai/CoPaw/issues/7367) | ~7 天 | 仅启用 console 时启动仍需 30-45s，根因已定位但 Fix 未提交 |
| [#7534](https://github.com/agentscope-ai/CoPaw/issues/7534) | 2 天 | 飞书 consumer 卡死导致会话静默无响应，高严重度 Bug，无 Fix PR |
| [#7554](https://github.com/agentscope-ai/CoPaw/issues/7554) | 1 天 | Windows shell 工具 stdin 继承问题，影响控制台用户体验 |
| [#7549](https://github.com/agentscope-ai/CoPaw/issues/7549) | 1 天 | 火山引擎 Ark API 兼容性 Bug，需要 Provider 层修复 |
| [PR #7486](https://github.com/agentscope-ai/CoPaw/pull/7486) | 3 天 | Creator 插件重大更新，含多项新功能，等待 Review |
| [PR #7565](https://github.com/agentscope-ai/CoPaw/pull/7565) | 1 天 | Plugin 热重载与回滚机制，已提交待 Review |
| [PR #6960](https://github.com/agentscope-ai/CoPaw/pull/6960) | 23 天 | PawPort 跨 Agent 导入功能，长期未合并，需确认状态 |

---

*报告生成时间：2026-09-05 | 分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-09-05

## 1. 今日速览

过去24小时 ZeroClaw 项目保持**高活跃度**：34条 Issues 更新（24活跃 / 10关闭）、50条 PR 更新（44待合并 / 6已合并）。整体节奏围绕 **v0.8.5  stabilization 窗口**推进，核心关注点集中在运行时安全性修复、会话管理架构 RFC、WhatsApp Web 安全补丁落地，以及 ZeroCode TUI 多项体验改进。项目健康度良好，安全类问题响应积极，维护者参与度高。

---

## 2. 版本发布

**v0.8.5 版本准备中**，版本 bump PR [#10632](https://github.com/zeroclaw-labs/zeroclaw/pull/10632) 已合并，将 23-crate workspace 及各分发面（installer、container、Nix、Tauri）从 `0.8.4` 升至 `0.8.5`，并锁定已批准的翻译快照。v0.8.5 stabilization 跟踪 Issue [#9459](https://github.com/zeroclaw-labs/zeroclaw/issues/9459) 显示：v0.8.5 的有限稳定窗口预计至 **2026-08-30** 结束（注：Issue 时间戳为 2026-07-27，稳定线为历史窗口），当前以周为单位推进 ready work。

**无重大破坏性变更公告**，本次版本主要为 bug 修复、文档补齐和内部版本协调。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 作者 | 类型 | 说明 |
|---|---|---|---|
| [#10632](https://github.com/zeroclaw-labs/zeroclaw/pull/10632) | JordanTheJet | chore | 版本 bump 至 v0.8.5，锁定翻译快照 |
| [#10158](https://github.com/zeroclaw-labs/zeroclaw/pull/10158) | JordanTheJet | feat | 将 23-crate workspace 发布至 crates.io，含 `zerorelay`、`zeroclaw-relay-proto`、`zeroclaw-tls` |
| [#10587](https://github.com/zeroclaw-labs/zeroclaw/pull/10587) | dependabot | chore | rust-all 依赖组更新 49 项 |
| [#10153](https://github.com/zeroclaw-labs/zeroclaw/pull/10153) | JordanTheJet | feat | WhatsApp Web 渠道端口至 `whatsapp-rust 0.7.0`，为渠道 crate 发布做准备 |
| [#10571](https://github.com/zeroclaw-labs/zeroclaw/pull/10571) | JordanTheJet | docs | Twitch 频道文档新增专属章节 |

**整体进展评估**：项目当前推进重心在 stabilization 收尾，核心功能（多会话 TUI、持久化会话 prompt 附件、代理凭据轮换）仍在 open 状态，预计下周期继续。

---

## 4. 社区热点

### 讨论最活跃的 Issues

1. **[#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487)** — RFC: Runtime-owned conversation sessions and transport surface adapters
   - 32 条评论，Revision 5，维护者主导的安全澄清版本
   - 社区关注点：运行时与 channel 间会话所有权分离，涉及 agent 生命周期与网关适配

2. **[#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909)** — RFC: Computer-use support for desktop screen interaction
   - 16 条评论，Revision 2（维护者接管），聚焦 bounded approval、执行时重新验证、sidecar trust
   - 社区关注点：桌面控制权限边界与用户授权粒度

3. **[#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397)** — RFC: Treat empty WhatsApp `allowed_groups` as permit-none
   - 14 条评论，已关闭（accepted）
   - 直接修复 [#9348](https://github.com/zeroclaw-labs/zeroclaw/issues/9348) 的安全漏洞：空 `allowed_groups` 默认放行全部群聊

4. **[#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050)** — RFC: Verbatim channel send over gateway
   - 13 条评论，accepted
   - 诉求：提供网关路由直接透传消息，无需 agent turn

---

## 5. Bug 与稳定性

按严重程度排列：

### 🔴 S1 — 工作流阻塞

| Issue | 说明 | Fix PR |
|---|---|---|
| [#10609](https://github.com/zeroclaw-labs/zeroclaw/issues/10609) | zerocode 忽略启动目录，强制以 agent workspace 为 cwd | 无 |
| [#10603](https://github.com/zeroclaw-labs/zeroclaw/issues/10603) | OpenCode providers 未发送 `x-opencode-session` header，导致 Go 模型报错并存在封号风险 | 无 |
| [#10357](https://github.com/zeroclaw-labs/zeroclaw/issues/10357) | 工具执行错误路径丢弃详细错误体，agent 仅收到 bare "HTTP 400" | 无 |
| [#10223](https://github.com/zeroclaw-labs/zeroclaw/issues/10223) | ZeroCode 重连期间丢失 Ctrl+C，阻塞输入 | 无 |
| [#9882](https://github.com/zeroclaw-labs/zeroclaw/issues/9882) | 图片标记绕过 `run_model_query` 的内容校验路径 | 无 |
| [#10593](https://github.com/zeroclaw-labs/zeroclaw/issues/10593) | `backup.schedule_cron` 无 agent 认领时静默调度失败 | 无 |
| [#9421](https://github.com/zeroclaw-labs/zeroclaw/issues/9421) | 不完整终端响应被报告为成功（Anthropic provider） | [#9447](https://github.com/zeroclaw-labs/zeroclaw/pull/9447) 进行中 |
| [#9348](https://github.com/zeroclaw-labs/zeroclaw/issues/9348) | WhatsApp Web 在 business 模式下回复所有 DM 和群聊 | [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) 已修复 |

### 🟡 S2 — 降级体验

| Issue | 说明 |
|---|---|
| [#10594](https://github.com/zeroclaw-labs/zeroclaw/issues/10594) | cron 任务未执行时不记录任何日志，静默失败 |
| [#10626](https://github.com/zeroclaw-labs/zeroclaw/issues/10626) | TTS 直接合成 Markdown/emoji，不清洗 |
| [#10625](https://github.com/zeroclaw-labs/zeroclaw/issues/10625) | 非视觉模型对话中向用户展示 `[media attachment]` 占位符 |
| [#10390](https://github.com/zeroclaw-labs/zeroclaw/issues/10390) | 进入 inactive Chat pane 时阻塞导航 |

---

## 6. 功能请求与路线图信号

| Issue | 类型 | 状态 | 纳入下一版本可能性 |
|---|---|---|---|
| [#10619](https://github.com/zeroclaw-labs/zeroclaw/issues/10619) | Anthropic prompt-cache passthrough 通过兼容网关 | 进行中 | ⭐⭐⭐ 高 — 已有 PR 路径 |
| [#10588](https://github.com/zeroclaw-labs/zeroclaw/issues/10588) | 提升 `multimodal.max_image_size_mb` 默认值至 20 | 进行中 | ⭐⭐⭐ 高 — 低风险配置变更 |
| [#10631](https://github.com/zeroclaw-labs/zeroclaw/pull/10631) | MCP Parallel Search 配置示例 | open PR | ⭐⭐ 中 — 文档增强 |
| [#10580](https://github.com/zeroclaw-labs/zeroclaw/issues/10580) | CI docs 链接检查扩展到全仓库死链 | open | ⭐⭐ 中 — 基础设施改进 |
| [#10579](https://github.com/zeroclaw-labs/zeroclaw/issues/10579) | Reference CLI/Config 页面缺失，39 处链接指向不存在页面 | open | ⭐⭐ 中 — 需补充文档 |
| [#9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109) | 原生 Hailo-Ollama provider 支持 | open，需 maintainer review | ⭐⭐ 中 — 等待审查 |

---

## 7. 用户反馈摘要

**痛点集中在以下几个方面：**

- **安全配置信任危机**：[#9348](https://github.com/zeroclaw-labs/zeroclaw/issues/9348) 暴露了 WhatsApp 渠道配置语义缺陷——空 `allowed_groups` 实际是"放行全部"而非"限制全部"，用户反映配置看似锁定实则完全开放，引发信任问题。该问题已通过 RFC [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) 修复并关闭。

- **静默失败难以排查**：[#10594](https://github.com/zeroclaw-labs/zeroclaw/issues/10594) 和 [#10593](https://github.com/zeroclaw-labs/zeroclaw/issues/10593) 均反映 cron 调度静默失败问题——无记录、无日志、`last_status` 不变，用户无法判断任务是否执行。

- **TUI 交互降级**：[#10223](https://github.com/zeroclaw-labs/zeroclaw/issues/10223) 和 [#10390](https://github.com/zeroclaw-labs/zeroclaw/issues/10390) 反映 ZeroCode 在重连和 pane 切换时输入阻塞，影响多会话工作流。

- **多模态体验不完整**：[#10625](https://github.com/zeroclaw-labs/zeroclaw/issues/10625) 和 [#10626](https://github.com/zeroclaw-labs/zeroclaw/issues/10626) 显示文本模型用户会看到 `[media attachment]` 占位符，TTS 用户会听到 Markdown 标记，用户体验割裂。

- **正面反馈**：[#10631](https://github.com/zeroclaw-labs/zeroclaw/pull/10631) 中用户特别感谢 MCP Parallel Search 提供无需 API key 的公开搜索配置示例。

---

## 8. 待处理积压

### 需维护者关注的长期 Issues

| Issue | 类型 | 创建时间 | 评论数 | 风险 | 说明 |
|---|---|---|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC | 2026-07-28 | 32 | 🔴 高 | Runtime-owned sessions RFC 处于 Revision 5，投票快照需重新开启 |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | RFC | 2026-05-25 | 16 | 🔴 高 | Computer-use 权限模型已 accept，但详细实现尚未启动 |
| [#10603](https://github.com/zeroclaw-labs/zeroclaw/issues/10603) | Bug | 2026-09-03 | 2 | 🔴 高 | OpenCode x-opencode-session header 缺失，存在账户封禁风险 |
| [#9421](https://github.com/zeroclaw-labs/zeroclaw/issues/9421) | Bug | 2026-07-27 | 3 | 🔴 高 | 不完整终端响应误报成功，[#9447](https://github.com/zeroclaw-labs/zeroclaw/pull/9447) 进行中 |
| [#9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109) | Feature | 2026-07-17 | — | 🟡 中 | Hailo-Ollama 原生 provider 需 maintainer review |

### 长期未响应的重要 PR

| PR | 作者 | 创建时间 | 状态 | 说明 |
|---|---|---|---|---|
| [#9713](https://github.com/zeroclaw-labs/zeroclaw/pull/9713) | Project516 | 2026-08-03 | blocked | 历史修剪 token 记账暴露，被阻塞 |
| [#9419](https://github.com/zeroclaw-labs/zeroclaw/pull/9419) | IftekharUddin | 2026-07-26 | do-not-merge | 凭据速率限制轮换，标记为 do-not-merge |
| [#10407](https://github.com/zeroclaw-labs/zeroclaw/pull/10407) | vrurg | 2026-08-27 | needs-author-action | 持久化会话 prompt 附件，需作者进一步操作 |



</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*