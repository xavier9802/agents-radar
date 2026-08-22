# OpenClaw 生态日报 2026-08-22

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-22 01:36 UTC

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
**日期：2026-08-22** | 数据周期：过去24小时

---

## 1. 今日速览

OpenClaw 社区今日保持高活跃度，共处理 500 条 Issues 与 500 条 PRs，其中 14 个 Issue 和 114 个 PR 得到关闭或合并。核心挑战集中在 **beta.2 版本的稳定性问题**——Gateway 内存泄漏、SQLite 数据损坏复现、event loop 周期性阻塞等 P0 级问题持续消耗维护资源。Codex 集成的 OAuth 刷新失败、工具调用丢失等问题引发大量用户反馈。与此同时，多个高质量修复 PR 已合并，包括 Claude CLI OAuth 修复、Telegram 回调值保留、安全安装策略确认等功能增强。项目整体处于 **beta.2 回归修复阶段**，维护团队正集中火力解决生产环境稳定性问题。

---

## 2. 版本发布

**无新版本发布。**

当前聚焦于 `v2026.8.1-beta.2` 的发布验证（Issue #125626），该 beta 版本已暴露多个严重稳定性问题，预计将在修复后推出后续候选版本。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 作者 | 状态 | 说明 |
|---|---|---|---|
| [#125471](https://github.com/openclaw/openclaw/pull/125471) | VACInc | ✅ CLOSED | 修复 Claude CLI OAuth 在 Gateway 重启后丢失 refresh 所有权的问题，恢复 Control UI 中的模型可用性 |
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | jesse-merhi | ✅ CLOSED | 新增 `security.installPolicy` 警告确认机制，支持交互式 CLI 安装前的安全审查 |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | jesse-merhi | ✅ CLOSED | Control UI 新增安装策略警告审查功能，管理员可确认并继续可疑插件安装 |
| [#127735](https://github.com/openclaw/openclaw/pull/127735) | steipete | ✅ CLOSED | 修复 Telegram inline button callback 值因尾部空白被规范化导致操作丢失的问题 |
| [#127727](https://github.com/openclaw/openclaw/pull/127727) | steipete | ✅ CLOSED | 移除浏览器桥接测试中的仅测试路由绕过，修复安全边界漏洞 |

### 待合并关键 PR（维护者审阅中）

- **[PR #127724](https://github.com/openclaw/openclaw/pull/127724)** — Codex 插件升级至 0.149，修复 reply delivery、sandbox 隔离、MCP app authority 等多处集成缺陷（⚠️ 高风险兼容性）
- **[PR #127739](https://github.com/openclaw/openclaw/pull/127739)** — 修复定时任务和多子 agent 场景下收到过期子 completion 结果的问题
- **[PR #127469](https://github.com/openclaw/openclaw/pull/127469)** — 修复自动记忆中包含已标记为不可信来源的内容的安全问题
- **[PR #126424](https://github.com/openclaw/openclaw/pull/126424)** — 修复多 agent 操作中 conversation 工具跨绑定泄漏的问题

**进展评估**：今日合并的 PR 主要聚焦于安全策略强化、OAuth 修复和渠道集成修正，对生产环境稳定性有直接改善。待合并的 PR #127724（Codex 升级）若通过验证，将是今日最重要的功能推进。

---

## 4. 社区热点

### 讨论最活跃的 Issues

| Issue | 标题 | 评论数 | 👍 | 严重程度 | 链接 |
|---|---|---|---|---|---|
| #91588 | Gateway 内存泄漏：RSS 从 350MB 增长至 15.5GB 导致 OOM 崩溃循环 | 23 | 1 | 🔴 P0 | [链接](https://github.com/openclaw/openclaw/issues/91588) |
| #91009 | Codex PreToolUse hook 导致 CPU 饱和并阻塞 Gateway RPC | 22 | 2 | 🔴 P1 | [链接](https://github.com/openclaw/openclaw/issues/91009) |
| #87744 | Codex-backed Telegram 会话反复超时无法完成 | 18 | 4 | 🔴 P1 | [链接](https://github.com/openclaw/openclaw/issues/87744) |
| #125626 | v2026.8.1-beta.2 发布验证 | 18 | 0 | — | [链接](https://github.com/openclaw/openclaw/issues/125626) |
| #68596 | 请求可配置的 streaming watchdog 超时阈值 | 16 | 8 | 🟡 P2 | [链接](https://github.com/openclaw/openclaw/issues/68596) |

### 热点分析

**内存泄漏与稳定性问题是当前最大痛点**。Issue #91588 描述的 Gateway 内存泄漏已持续数周，RSS 在 2-3 天内从 350MB 膨胀至 15.5GB 并触发 OOM killer，导致 `launchd-handoff` 重启循环。该问题与 beta.2 新引入的 event loop 阻塞（Issue #124788）和 SQLite 损坏（Issue #126821）形成连锁反应，严重影响生产部署可靠性。

**Codex 集成稳定性集中爆发**。#91009、#87744、#86215、#123799 四个高优先级 Issue 均指向 Codex 集成的不同层面：CPU 泄漏、Telegram 超时、OAuth 刷新失败、compact API 404。这反映出 Codex 插件在快速迭代中缺乏充分的回归测试。

**用户对新功能的期待明确**。Issue #68596（streaming watchdog 可配置超时）获得 8 个 👍，反映深度用户希望针对 Kimi-K2.5、DeepSeek-R1 等长推理模型优化流式处理行为。

---

## 5. Bug 与稳定性

### P0 级问题（需立即关注）

| Issue | 描述 | Fix PR | 链接 |
|---|---|---|---|
| #91588 | Gateway 内存泄漏，RSS 持续增长导致 OOM 崩溃循环 | — | [链接](https://github.com/openclaw/openclaw/issues/91588) |
| #126821 | beta.2 中 SQLite  corruption 在重建后 15-24 小时内复现，含"paralyzed gateway"模式 | — | [链接](https://github.com/openclaw/openclaw/issues/126821) |
| #124788 | beta.2 event loop 每 ~10.9 分钟阻塞 ~100-120 秒，WebSocket/HTTP/cron 全部停滞 | — | [链接](https://github.com/openclaw/openclaw/issues/124788) |

### P1 级问题

| Issue | 描述 | Fix PR | 链接 |
|---|---|---|---|
| #91009 | Codex PreToolUse hook  spawn CPU-bound 进程导致 Gateway RPC  stalls | — | [链接](https://github.com/openclaw/openclaw/issues/91009) |
| #87744 | Codex-backed Telegram 会话反复超时，无法到达 turn/completed | — | [链接](https://github.com/openclaw/openclaw/issues/87744) |
| #67777 | Subagent completion 在 direct-announce 超时/draining 时丢失 | — | [链接](https://github.com/openclaw/openclaw/issues/67777) |
| #86215 | Codex OAuth refresh 失败导致 agent 卡死数小时，无明确告警 | — | [链接](https://github.com/openclaw/openclaw/issues/86215) |
| #97616 | Hook/tool 子进程泄漏导致 zombie 积累和运行时退化 | — | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| #123799 | 生产环境受 Codex compact 404 影响，需安全升级指导 | — | [链接](https://github.com/openclaw/openclaw/issues/123799) |
| #45224 | Playwright CDP 未处理断言错误导致 Gateway 崩溃 | — | [链接](https://github.com/openclaw/openclaw/issues/45224) |
| #86612 | Docker sandbox 模式下 Windows 容器重启循环 | — | [链接](https://github.com/openclaw/openclaw/issues/86612) |
| #125570 | Skill Workshop update 覆盖 live skill description，破坏 skill routing | — | [链接](https://github.com/openclaw/openclaw/issues/125570) |
| #127176 | Windows 上 CLI 和 Node Host 设备元数据批准交替失败 | — | [链接](https://github.com/openclaw/openclaw/issues/127176) |
| #83598 | Anthropic OAuth refresh 在 2026.5.12 仍无法恢复主 lane | — | [链接](https://github.com/openclaw/openclaw/issues/83598) |
| #126246 | Telegram durable outbound 消息卡在 `send_attempt_started` 重启后丢失 | — | [链接](https://github.com/openclaw/openclaw/issues/126246) |
| #108215 | 大 tool output 后 context 使用率从 57% 骤降至 13% 且无 compaction | — | [链接](https://github.com/openclaw/openclaw/issues/108215) |

### 已有关闭 PR 的 Bug

| Issue | 描述 | 关闭 PR | 链接 |
|---|---|---|---|
| #125540 | 非 owner 通道 /new 和 /reset 命令失效 | [PR #125618](https://github.com/openclaw/openclaw/pull/125618) | [链接](https://github.com/openclaw/openclaw/issues/125540) |

**稳定性评估**：今日报告的 P0/P1 Bug 数量显著，且多数缺乏明确 fix PR。beta.2 引入的 event loop 阻塞和 SQLite 损坏问题尤为严重，建议在下一个候选版本发布前完成根治。

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 👍 | 匹配 PR | 纳入可能性 |
|---|---|---|---|---|
| #68596 | 可配置的 streaming watchdog 超时阈值 | 8 | — | 🟢 高（用户呼声强） |
| #50199 | Skill 优先级配置 | 0 | — | 🟡 中（架构复杂） |
| #71058 | 单 Gateway 支持多 Azure/Teams bot | 1 | — | 🟡 中（企业需求） |
| #52640 | 长时 channel turn 的持久 task-status 展示 | 2 | — | 🟢 高（UX 痛点） |
| #42840 | Control UI 支持 MathJax/LaTeX | 10 | — | 🟢 高（社区呼声最强） |
| #71195 | Talk Mode 支持 OpenAI Realtime speech-to-speech | 1 | — | 🟡 中（需平台支持） |
| #57425 | 优雅 Gateway 重启与会话恢复 | 1 | — | 🟢 高（稳定性相关） |
| #78865 | Tool call circuit breaker | 1 | — | 🟢 高（防 LLM 无限重试） |
| #45771 | 内置 pace-aware rate limiting | 2 | — | 🟡 中（自治 agent 需求） |
| #51572 | session-memory hook 在 reset/prune 时触发 | 1 | — | 🟡 中（开发者需求） |

**路线图信号**：
- **MathJax/LaTeX 支持**（#42840）获得 10 个 👍，是今日反馈最强的功能需求，反映用户群体中包含大量学术/技术场景使用者。
- **Tool call circuit breaker**（#78865）和 **优雅重启**（#57425）直击自治 agent 可靠性的核心痛点，与当前 beta.2 稳定性修复方向一致，可能被纳入近期版本。
- Codex 升级 PR #127724 若合并，将带来协议层面的功能增强，值得重点关注。

---

## 7. 用户反馈摘要

### 核心痛点

1. **生产环境稳定性堪忧**：多个用户报告 Gateway 在运行数天后因内存泄漏或 SQLite 损坏而崩溃。Issue #91588 中用户描述 RSS 从 350MB 增长至 15.5GB 的过程，以及 #126821 中 "paralyzed gateway" 模式拒绝所有服务但不退出的状态，严重影响生产信任度。

2. **Codex 集成回归集中爆发**：Issue #91009（CPU 泄漏）、#87744（Telegram 超时）、#86215（OAuth 卡死）形成问题集群，用户反馈 Codex 集成在 2026.5.x 版本后稳定性显著下降。Issue #123799 中用户明确表示为"受影响的生产部署"，需要 operational guidance。

3. **OAuth 刷新机制存在系统性缺陷**：除 Codex OAuth 外，Anthropic Claude CLI OAuth（#83598）

---

## 横向生态对比



# 2026-08-22 个人 AI 智能体开源生态横向对比分析报告

---

## 1. 生态全景

2026年8月下旬，个人AI助手与自主智能体开源生态呈现**分层加速、安全回归**的特征：头部项目（OpenClaw、Hermes Agent、ZeroClaw、IronClaw）进入高频迭代期，日均PR吞吐达30-500条，社区贡献与审查并行推进；中腰部项目（NanoBot、NanoClaw、CoPaw、LobsterAI）聚焦稳定性修复与通道集成完善；轻量级项目（PicoClaw、NullClaw、Moltis）处于功能打磨与协议扩展阶段。生态整体从"功能抢占"转向"生产可靠性与安全性"攻坚，内存泄漏、事件循环阻塞、沙箱策略一致性、多Agent通信稳定性成为共性问题。

---

## 2. 各项目活跃度对比

| 项目 | Issues(日) | PRs(日) | 关闭/合并 | 版本发布 | 健康度 |
|------|-----------|---------|----------|---------|--------|
| **OpenClaw** | 500 | 500 | 128 | 无（beta.2修复中） | 🟡 高风险 — P0稳定性问题集中 |
| **Hermes Agent** | 50 | 50 | ~93（含历史） | ✅ v0.20.5 | 🟢 良好 |
| **ZeroClaw** | 50 | 50 | 2 | 无 | 🟡 中等 — 4条安全类S0/S1 Bug |
| **IronClaw** | 15 | 35 | 16 | 无 | 🟢 良好 — CI/存储基建加固期 |
| **CoPaw** | 34 | 34 | 13 | 无（内部bump至v2.1.1b2） | 🟢 良好 |
| **NanoBot** | 5 | 38 | 28 | 无 | 🟢 良好 — 通道层修复集中 |
| **NanoClaw** | 1 | 24 | 11 | 无 | 🟢 良好 — 功能迭代快 |
| **LobsterAI** | 2 | 13 | 12+1 | 2026.8.21 | 🟢 良好 |
| **Moltis** | 2 | 8 | 1 | 无 | 🟡 中等 — PR积压（#468 5个月） |
| **PicoClaw** | 1 | 3 | 3 | 无 | 🟢 平稳 |
| **NullClaw** | 0 | 1 | 0 | 无 | 🟡 低活跃 |
| **ZeptoClaw** | 0 | 0 | 0 | 无 | ⚪ 停滞 |

---

## 3. OpenClaw 在生态中的定位

**优势**：
- **规模碾压**：日处理Issues/PRs均达500级，为次高峰项目（Hermes/ZeroClaw的10倍），社区参与度和贡献吞吐量领先。
- **协议深度**：支持多Channel（Telegram、WhatsApp、Slack、Dial、Mattermost）、多Provider（Claude CLI、Codex、Anthropic、OpenAI兼容）、多Agent协作（sub-agent、task delegation），生态最广。
- **技术栈完整**：涵盖Control UI、Gateway、Desktop组件、Docker/Sandbox部署，全链路覆盖。

**技术路线差异**：
| 维度 | OpenClaw | Hermes Agent | ZeroClaw | IronClaw |
|------|----------|-------------|----------|----------|
| 架构风格 | 集中式Gateway + 多Channel插件 | 多Profile + 委托链可观测 | 安全沙箱优先 + 策略审计 | Rust原生 + CI先行 |
| 语言栈 | TypeScript/Go混合 | TypeScript/Go | Rust | Rust |
| 发布节奏 | 高频小版本（beta.2回归期） | 稳定补丁（v0.20.5） | 低版本发布频率 | 无版本发布 |
| 安全定位 | OAuth/安装策略加固 | proof-carrying架构 | S0级沙箱策略审查 | MCP内存安全前置 |

**社区规模对比**（估算）：OpenClaw > Hermes Agent ≈ ZeroClaw > IronClaw > CoPaw > NanoClaw > NanoBot > LobsterAI > Moltis > PicoClaw > NullClaw

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|---------|---------|
| **生产稳定性（内存/事件循环）** | OpenClaw (#91588, #124788), ZeroClaw (#10230) | Gateway内存泄漏、event loop周期性阻塞、daemon栈溢出 |
| **通道集成可靠性** | OpenClaw (Codex问题集群), NanoBot, NanoClaw, Moltis | Telegram轮询卡死、WhatsApp文件持久化、Slack工具路由失效 |
| **多Agent/委托安全** | ZeroClaw (#10165, #10164), OpenClaw (#91009) | delegate绕过安全策略、PreToolUse hook CPU泄漏 |
| **可观测性基础设施** | Hermes Agent, NanoBot, IronClaw | Trajectory合约、proof-carrying、用户持久化Inbox、CI门禁体系 |
| **长上下文管理** | OpenClaw (#108215), ZeroClaw (#10068), NanoBot | context使用率骤降无compaction、交互式session硬编码32k限制 |
| **工具结果截断/传递** | ZeroClaw (#10114-#10116), OpenClaw | max_tool_result_chars与context解耦、tool output丢失 |
| **协议兼容性扩展** | PicoClaw (Anthropic协议), NanoClaw (Mattermost/Dial) | 原生协议支持、多通道统一适配层 |
| **安全策略一致性** | ZeroClaw (S0/S1), OpenClaw (OAuth), IronClaw (#7808) | block_high_risk_commands绕过、provider安全前置 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|---------|---------|----------------|
| **OpenClaw** | 全功能Agent平台，多Channel/多Provider/多Agent | 开发者、企业级部署、高级用户 | TypeScript/Go混合，Gateway为核心，Plugin生态 |
| **Hermes Agent** | 委托链可观测性、proof-carrying架构、多Profile | 需要审计追溯的企业用户 | Kanban调度器、Task-Scoped工作区、Docker Worker |
| **ZeroClaw** | 安全沙箱策略、SOP引擎、Desktop体验 | 安全敏感场景、个人开发者 | Rust编写，Sandbox-first设计，策略审计优先 |
| **IronClaw** | CI基建、可插拔内存(MCP协议)、设计系统 | 基础设施开发者、内部工程团队 | Rust原生，CI四轨并行，WebUI组件标准化 |
| **CoPaw** | 多租户Hub、长会话性能、MCP连接恢复 | 需要私有化部署的团队 | v2.1.x系列，Console性能优化，自托管Hub |
| **NanoBot** | 通道稳定性、Trajectory重构、PromptGuard | 轻量级Agent用户、教育/研究场景 | 统一LLMUsage合约、TUI LaTeX渲染、多语言支持 |
| **NanoClaw** | 模板化Agent、Telegram多实例、频道快速集成 | 快速原型开发者、Telegram用户 | 模板Agent创建、多bot实例绑定、CI修复 |
| **LobsterAI** | DSH实验性运行时、资料库优化、Cowork性能 | 网易有道内部/外部用户、Windows用户 | Electron架构，DeepSeek Harness集成，i18n完善 |
| **Moltis** | WhatsApp集成、Cron定时任务、浏览器隐身 | 个人用户、WhatsApp生态用户 | 专注单一通道深度优化，i18n支持 |
| **PicoClaw** | WebFetch增强、Anthropic协议兼容 | 轻量级/嵌入式Agent开发者 | Go语言，协议抽象层，文档驱动 |

---

## 6. 社区热度与成熟度分层

### 🔴 快速迭代阶段（高吞吐、功能扩张）
- **OpenClaw**：日均500条Issue/PR，但beta.2回归期暴露大量P0问题，处于"功能→稳定"的阵痛期
- **Hermes Agent**：高活跃度（50/50），v0.20.5已发布，架构重构（God-file分片）完成，进入功能验收期
- **NanoClaw**：24 PRs中11条已合并，模板Agent/多频道集成快速推进，处于功能扩张期

### 🟡 质量巩固阶段（稳定性修复、技术债清理）
- **IronClaw**：CI体系重构（T1-T4）、可插拔内存安全审查、WebUI标准化，基建加固期
- **CoPaw**：v2.1.1b2内部版本，长会话性能优化、多租户Hub，稳定性打磨期
- **NanoBot**：通道层修复集中（Telegram/Slack/Cron），Trajectory重构完成，可观测性完善期
- **LobsterAI**：DSH实验功能上线、性能优化持续，技术债清理期
- **ZeroClaw**：50条Issue/PR但仅2条关闭，安全S0/S1问题集中爆发，风险管控期

### 🟢 平稳维护阶段（低频迭代、协议扩展）
- **PicoClaw**：3 PRs/1 Issue，功能打磨与文档优化
- **Moltis**：8 PRs中1条合并，WhatsApp深度优化，Windows兼容性积压

### ⚪ 停滞/低活跃
- **NullClaw**：仅1条PR待合并
- **ZeptoClaw**：无活动

---

## 7. 值得关注的趋势信号

| 趋势 | 信号来源 | 对开发者的参考价值 |
|------|---------|-------------------|
| **从"功能堆叠"转向"生产可靠性"** | OpenClaw P0内存泄漏/SQLite损坏、ZeroClaw S0沙箱绕过 | 生产部署前需充分验证稳定性，内存管理和事件循环是高频故障点 |
| **安全策略一致性成为多Agent部署瓶颈** | ZeroClaw #10165/#10164、IronClaw #7808 | 委托链/独立agent场景下策略评估必须统一，需设计策略继承与审计机制 |
| **可观测性基础设施成为成熟度分水岭** | Hermes proof-carrying、NanoBot Trajectory、IronClaw CI门禁 | 长期运行的Agent系统需内置委托链溯源、用户Inbox、Token使用追踪 |
| **长上下文管理出现系统性缺陷** | OpenClaw #108215、ZeroClaw #10068/#10114 | context compaction策略、tool result截断行为需与模型上下文窗口联动设计 |
| **通道层稳定性成为差异化竞争点** | NanoBot Telegram修复、Moltis WhatsApp Markdown、NanoClaw Telegram多实例 | 单一通道深度优化（如WhatsApp文件持久化、Cron路由）可建立垂直优势 |
| **协议抽象层价值凸显** | PicoClaw Anthropic协议、IronClaw MCP内存协议 | 支持OpenAI/Anthropic双轨格式可降低接入成本，MCP作为内存协议扩展标准 |
| **企业级多租户能力需求上升** | CoPaw自托管Hub、IronClaw可插拔内存 | 多用户隔离、权限控制、审计追踪将成为团队部署的标配需求 |
| **CI/CD可重复性成为工程成熟度指标** | IronClaw T1-T4四轨并行、OpenClaw CI门禁 | 统一composite action、fixed toolchain、worktree-safe hooks可显著降低维护成本 |

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目日报 — 2026-08-22

## 1. 今日速览

NanoBot 在过去 24 小时内保持**高活跃度**，共处理 38 条 PR（24 条合并/关闭）和 5 条 Issues（4 条关闭），开发节奏稳定。核心进展集中在**提供者使用追踪重构**（LLMUsage 合约统一）、**Dream 记忆游标修复**以及**多渠道稳定性加固**（Telegram 轮询恢复、Slack 文件下载验证、通道异常边界隔离）。无新版本发布，但多项 PR 已就绪待合并，为后续版本积累了技术债务清理和可观测性提升。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 作者 | 更新内容 |
|----|------|----------|
| [#5156](https://github.com/HKUDS/nanobot/pull/5156) | QQQ300kuai | 修复 Telegram 轮询在瞬态网络抖动后静默卡死的问题，恢复消息接收能力 |
| [#5407](https://github.com/HKUDS/nanobot/pull/5407) | aiguozhi123456 | 修复 Cron 任务：禁用 `heartbeat`/`dream` 后仍能触发已持久化的系统任务，浪费 Token |
| [#5479](https://github.com/HKUDS/nanobot/pull/5479) | chengyongru | 合并统一的 Trajectory 提供者使用记录后端（含 fallback、错误、取消事件） |
| [#5478](https://github.com/HKUDS/nanobot/pull/5478) | chengyongru | 定义类型化的 LLMUsage 合约，统一 OpenAI/Anthropic/Bedrock 的 token 和缓存语义 |
| [#5442](https://github.com/HKUDS/nanobot/pull/5442) | flobo3 | 修复 Dream 工具错误恢复后内存游标未推进的问题，避免重复处理相同历史批次 |
| [#5476](https://github.com/HKUDS/nanobot/pull/5476) | chengyongru | TUI 支持 LaTeX 渲染为 Unicode 纯文本，覆盖行内和独立公式 |
| [#5414](https://github.com/HKUDS/nanobot/pull/5414) | KDB-Wind | 修复 Slack 文件下载跨重定向链的验证，防止 URL 劫持风险 |
| [#1149](https://github.com/HKUDS/nanobot/pull/1149) | rexlunae | 新增 PromptGuard 安全模块，检测系统提示词注入、角色混淆、工具调用 JSON 注入 |
| [#1592](https://github.com/HKUDS/nanobot/pull/1592) | wildwulfie427 | 完成 Lumina Windows 应用打包流程，修复 CMake 安装前缀问题 |
| [#2063](https://github.com/HKUDS/nanobot/pull/2063) | Laihiujin | 集成 Tauri v2 桌面应用壳，支持 WebSocket 通道和本地网关管理 |
| [#1539](https://github.com/HKUDS/nanobot/pull/1539) | streacy | 新增 CrowPay 技能，支持 AI Agent 自主支付 API 和服务费用 |
| [#5477](https://github.com/HKUDS/nanobot/pull/5477) | chengyongru | 修复 iOS PWA 安全区域问题，同步主题颜色与系统 PWA 表现 |

**项目整体推进评估：** 今日合并工作以**稳定性修复**和**基础设施重构**为主，重点清理了通道层、调度层和可观测性层的技术债务。未涉及核心 Agent 逻辑的重大功能迭代，但为下一版本的可观测性增强（Trajectory + Usage 合约）奠定了基础。

---

## 4. 社区热点

### 活跃 Issue

| Issue | 状态 | 作者 | 评论 | 热度分析 |
|-------|------|------|------|----------|
| [#5198](https://github.com/HKUDS/nanobot/issues/5198) | CLOSED | whisperity | 4 | 用户反馈模型切换体验与云端 SaaS 产品存在差距，期望更灵活的运行时模型选择 |
| [#1168](https://github.com/HKUDS/nanobot/issues/1168) | CLOSED | silence-breaker | 2 | Notion MCP 连接失败，反映开源项目对 MCP 生态的工具适配仍不完善 |
| [#5441](https://github.com/HKUDS/nanobot/issues/5441) | CLOSED | flobo3 | 0 | Dream 记忆游标被错误工具调用永久阻塞，已合并修复 PR #5442 |

### 待合并 PR

| PR | 状态 | 作者 | 优先级 | 说明 |
|----|------|------|--------|------|
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) | OPEN | goodtiding5 | P1 | 集成 mst-python 作为 Meta-Search 提供者，聚合多引擎搜索结果 |
| [#5480](https://github.com/HKUDS/nanobot/pull/5480) | OPEN | chengyongru | P2 | LLMUsage 类型化合约（PR #5479 的前置依赖） |
| [#5481](https://github.com/HKUDS/nanobot/pull/5481) | OPEN | chengyongru | — | Trajectory 提供者使用后端（PR #5479 的独立版本） |
| [#5420](https://github.com/HKUDS/nanobot/pull/5420) | OPEN | Re-bin | — | 会话可观测性 UI，支持中断恢复展示 |
| [#5405](https://github.com/HKUDS/nanobot/pull/5405) | OPEN | yu-xin-c | P2 | 支持技能手动调用模式（`disable-model-invocation`），防止副作用技能自动触发 |
| [#5379](https://github.com/HKUDS/nanobot/pull/5379) | OPEN | dajiaohuang | P2 | 修复记忆合并流程中原始输入丢失问题 |
| [#5475](https://github.com/HKUDS/nanobot/pull/5475) | OPEN | chengyongru | P2 | 清理无用代码和依赖（`websocket-client`） |
| [#5457](https://github.com/HKUDS/nanobot/pull/5457) | OPEN | Shizoqua | P2 | 修复通道分派器异常边界，防止单条消息错误导致 outbound 任务崩溃 |

**社区诉求分析：** 用户在**模型切换灵活性**（#5198）和**MCP 工具兼容性**（#1168）方面仍有痛点；维护者正通过 Trajectory 重构（#5480/#5481）和会话可观测性（#5420）提升产品成熟度。

---

## 5. Bug 与稳定性

| 优先级 | 问题 | 状态 | 关联 PR |
|--------|------|------|---------|
| P2 | [#5454](https://github.com/HKUDS/nanobot/issues/5454) — 流式提供者中途 `server_error` 不再重试（内容已流式传输） | 新建 | 暂无 |
| P2 | [#5441](https://github.com/HKUDS/nanobot/issues/5441) — Dream 工具错误恢复后内存游标未推进 | ✅ 已修复 | [#5442](https://github.com/HKUDS/nanobot/pull/5442) |
| P2 | [#5463](https://github.com/HKUDS/nanobot/issues/5463) — 钉钉通道后台任务未设置终态观察器 | 新建 | 暂无 |
| P2 | [#5171](https://github.com/HKUDS/nanobot/issues/5171) — Telegram 轮询网络抖动后静默卡死 | ✅ 已修复 | [#5156](https://github.com/HKUDS/nanobot/pull/5156) |
| P2 | [#5407](https://github.com/HKUDS/nanobot/issues/5407) — 禁用 Cron 任务后仍触发已持久化作业 | ✅ 已修复 | [#5407](https://github.com/HKUDS/nanobot/pull/5407) |

**稳定性评估：** 通道层（Telegram、钉钉、Slack）和调度层（Cron、Dream）的多个历史 Bug 已在本期修复，项目整体稳定性显著提升。新发现的 #5454 和 #5463 需关注，尤其是流式重试逻辑缺陷可能影响生产环境的用户体验。

---

## 6. 功能请求与路线图信号

| 请求/PR | 类型 | 优先级 | 纳入下一版本可能性 |
|---------|------|--------|-------------------|
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) — mst-python Meta-Search 提供者 | 新功能 | P1 | ⭐⭐⭐ 高，聚合搜索是明确用户需求 |
| [#5405](https://github.com/HKUDS/nanobot/pull/5405) — 技能手动调用模式 | 功能增强 | P2 | ⭐⭐ 中高，安全副作用控制是合理诉求 |
| [#5420](https://github.com/HKUDS/nanobot/pull/5420) — 会话可观测性 UI | 新功能 | — | ⭐⭐⭐ 高，与 Trajectory 重构配套 |
| [#5476](https://github.com/HKUDS/nanobot/pull/5476) — TUI LaTeX 渲染 | 体验增强 | P2 | ⭐⭐ 中，小众需求但实现完整 |
| [#1149](https://github.com/HKUDS/nanobot/pull/1149) — PromptGuard 安全模块 | 新功能 | — | ⭐⭐⭐ 高，安全能力是产品成熟度标志 |

**路线图信号：** 维护者正在推进**可观测性基础设施**（Trajectory + Usage 合约）和**安全能力**（PromptGuard），同时补充**搜索能力**（mst-python）。这些方向与社区对 AI Agent 产品成熟度的期望一致。

---

## 7. 用户反馈摘要

### 痛点

| 用户 | 反馈 | 链接 |
|------|------|------|
| whisperity (#5198) | 模型切换体验不足，期望像云端 SaaS 产品一样在会话内自由切换模型 | [Issue #5198](https://github.com/HKUDS/nanobot/issues/5198) |
| silence-breaker (#1168) | Notion MCP 连接失败，API 配置无误但无法连通 | [Issue #1168](https://github.com/HKUDS/nanobot/issues/1168) |
| akinolur (#5454) | 流式响应中途服务器错误不触发重试，导致用户看到不完整输出 | [Issue #5454](https://github.com/HKUDS/nanobot/issues/5454) |
| flobo3 (#5441) | Dream 工具错误恢复后游标未推进，导致重复处理相同历史 | [Issue #5441](https://github.com/HKUDS/nanobot/issues/5441) |

### 满意点

- Telegram 轮询恢复修复（#5156）解决了生产环境长期存在的静默卡死问题
- Cron 任务禁用失效修复（#5407）消除了不必要的 Token 消耗
- PromptGuard 安全模块的引入提升了产品的企业级安全能力

---

## 8. 待处理积压

| 类型 | Issue/PR | 创建时间 | 作者 | 风险 |
|------|----------|----------|------|------|
| Bug | [#5454](https://github.com/HKUDS/nanobot/issues/5454) | 2026-08-20 | akinolur | 流式重试逻辑缺陷，影响生产体验 |
| Bug | [#5463](https://github.com/HKUDS/nanobot/issues/5463) | 2026-08-21 | yu-xin-c | 钉钉通道后台任务无终态观察，可能导致任务泄漏 |
| PR | [#5480](https://github.com/HKUDS/nanobot/pull/5480) | 2026-08-21 | chengyongru | LLMUsage 合约重构待合并，是多个 PR 的前置依赖 |
| PR | [#5481](https://github.com/HKUDS/nanobot/pull/5481) | 2026-08-21 | chengyongru | Trajectory 后端待合并 |
| PR | [#5420](https://github.com/HKUDS/nanobot/pull/5420) | 2026-08-18 | Re-bin | 会话可观测性 UI 待合并 |
| PR | [#5405](https://github.com/HKUDS/nanobot/pull/5405) | 2026-08-16 | yu-xin-c | 技能手动调用模式待合并 |
| PR | [#5379](https://github.com/HKUDS/nanobot/pull/5379) | 2026-08-13 | dajiaohuang | 记忆合并修复待合并 |
| PR | [#5475](https://github.com/HKUDS/nanobot/pull/5475) | 2026-08-21 | chengyongru | 代码清理待合并 |
| PR | [#5457](https://github.com/HKUDS/nanobot/pull/5457) | 2026-08-20 | Shizoqua | 通道异常边界修复待合并 |

**维护者关注建议：** 两个新建 Bug（#5454、#5463）需优先分配资源；PR #5480/#5481 依赖关系需协调合并顺序；长期未合并的 PR #5379（8月13日）应跟进 reviewer。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：** 2026-08-22  
**数据周期：** 过去 24 小时  
**项目地址：** https://github.com/NousResearch/hermes-agent

---

## 1. 今日速览
过去 24 小时 Hermes Agent 保持高活跃开发节奏，共收录 50 条 Issue 与 50 条 PR 更新，其中 47 条 Issue 处于活跃状态、46 条 PR 待合并，项目流水线运转顺畅。今日核心重心明确指向**系统可观测性、状态证明（proof-carrying）架构与跨平台稳定性修复**，同时 v0.20.5 补丁版本已稳定下发，为下游 Docker 与托管部署提供了基线。整体健康度评估为**优**：架构演进清晰、缺陷响应及时，但 PR 审查积压与舰队更新可靠性仍是下一阶段需要集中攻克的瓶颈。

---

## 2. 版本发布
**v0.20.5 (v2026.8.19)**
- **类型：** 补丁版本（Patch Release）
- **内容：** 汇总自 v0.20.4 以来合并的约 323 个 PR，面向 Docker 镜像、托管部署与全新安装提供稳定基线。
- **破坏性变更：** 无。
- **迁移注意：** 升级后建议重点验证多 Profile 混合部署与 Gateway 冷启动行为；若涉及 Fleet 批量更新，建议配合 #91277 的验证清单逐项核对，避免旧版残留配置干扰新签名的本地 Desktop 组件。

---

## 3. 项目进展
今日关闭/合并的关键 PR 体现了对底层契约与诊断能力的收紧：
- [#91972](https://github.com/NousResearch/hermes-agent/pull/91972) 修复 Gateway 在 I/O 错误（磁盘满、/tmp 配额）时被误报为“认证失败”的问题，提升一线排障效率。
- [#91970](https://github.com/NousResearch/hermes-agent/pull/91970) 修正 `delegation.max_spawn_depth: 0` 被强制钳制为 1 的配置语义丢失问题，恢复成本隔离与能力裁剪的明确控制。
- [#91981](https://github.com/NousResearch/hermes-agent/pull/91981)（开放）推进 Kanban Dispatcher 的 Docker Worker 工作区改为 Task-Scoped 与 Host-Backed，解决并发任务隔离隐患。

当前 **46 条 PR 处于待合并状态**，涵盖上下文窗口预算提示（#91974）、委托链持久化溯源 ID（#91963）、内存条目论证溯源（#89418）等架构级改进，显示项目已进入“高吞吐实现 + 等待审查收敛”的阶段，建议维护者优先分配审查带宽以避免流水线阻塞。

---

## 4. 社区热点
| Issue / PR | 类型 | 评论数 | 核心诉求分析 |
|---|---|---|---|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) | 重构/架构（已关闭） | 78 | “God-file 分片”史诗级重构完成，社区对模块化治理与单一接口设计原则高度认可，标志技术债清理进入新阶段。 |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Bug/自动化 | 72 | Skills Index 新鲜度探针持续降级（超时 29.8h > 26h 限制），自动重建流水线稳定性受质疑，影响 `hermes skills` 检索体验。 |
| [#90473](https://github.com/NousResearch/hermes-agent/issues/90473) | Bug/UX | 11 | 长会话（~900 条）下“显示更早消息”分页交互严重破坏体验，用户情绪强烈，暴露 Desktop 消息虚拟化与虚拟滚动策略的缺陷。 |
| [#68592](https://github.com/NousResearch/hermes-agent/issues/68592) | Bug/协议 | 10 | 非 Kanban 调度型 Cron Agent 被强制注入 `kanban_show` 协议，导致 `task_id is required` 错误，反映调度上下文隔离边界不清。 |

---

## 5. Bug 与稳定性
按严重程度与修复状态排列：

**P2 / 影响核心可用性**
- [#89083](https://github.com/NousResearch/hermes-agent/issues/89083) macOS 睡眠唤醒后 Desktop WebSocket 半开状态未被检测，聊天窗口永久无响应（仅新窗口或 Cmd+R 可恢复）。*状态：待修复*
- [#91675](https://github.com/NousResearch/hermes-agent/issues/91675) Windows Gateway 启动打印 `✓` 后 6s 健康检查崩溃；更新后冷启动仅恢复活跃 Profile。*状态：待修复*
- [#63277](https://github.com/NousResearch/hermes-agent/issues/

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 | 2026-08-22

## 1. 今日速览
PicoClaw 在过去 24 小时内保持稳健的维护节奏：累计处理 3 条 PR（均已合并/关闭），新增 1 条 Issue，无新版本发布。整体活跃度中等偏上，社区贡献集中于底层工具链增强、多模型协议兼容与文档规范化。项目技术栈健康，无阻塞性 Bug 或回归报告，正处于功能打磨与协议扩展的平稳期。

## 2. 版本发布
今日无新版本发布。今日关闭的 PR #647、#1158、#1182 将随下一个正式版本统一纳入说明。

## 3. 项目进展
今日共合并/关闭 3 条 PR，均为实质性功能或工程优化：
- **PR #647** `WebFetchTool` 文本提取增强 | [链接](https://github.com/sipeed/picoclaw/pull/647)  
  长期积压（创建于 2026-02-22）后今日关闭。新增 HTML 实体解码与块级元素结构保留，显著提升网页抓取内容的解析准确率与可读性，为依赖网络数据的 Agent 工作流提供稳定底层支撑。
- **PR #1158** `anthropic-messages` 协议支持 | [链接](https://github.com/sipeed/picoclaw/pull/1158)  
  修复 #269。新增协议前缀以原生兼容仅支持 Anthropic `/v1/messages` 格式的 LLM 服务与第三方代理，扩展了项目在不修改服务端配置情况下的接入范围。
- **PR #1182** 文档重构 `agents.md` | [链接](https://github.com/sipeed/picoclaw/pull/1182)  
  将贡献指南由“清单式”调整为“原则优先”架构，并以 `go.mod` 作为 Go 版本单一数据源。降低 AI Agent 与新手贡献者的理解成本，提升仓库自文档化程度。

## 4. 社区热点
- **Issue #3342** `[Feature] Opt-in "after-turn" steering mode` | [链接](https://github.com/sipeed/picoclaw/issues/3342)  
  社区今日唯一新增 Issue，聚焦多轮交互调度策略。当前机制在收到新消息时会直接中断并丢弃任务 1 的剩余工具调用（日志提示 `Skipped due to queued user message.`）。用户诉求明确：希望提供可选的“回合后转向”模式，将新消息入队而非抢占执行流，从而在保障长任务完整性的同时保留手动干预能力。该反馈直击进阶用户的核心痛点，讨论热度具备持续发酵潜力。

## 5. Bug 与稳定性
今日未收到新的 Bug 报告、崩溃日志或性能回归。PR #647 与 #1158 均通过测试后合并，未发现引入稳定性风险。项目当前版本在并发工具调用与网络解析层面的表现趋于稳定。

## 6. 功能请求与路线图信号
- **高优先级信号**：Issue #3342 提出的 `after-turn` 模式若落地，将作为核心调度器的可选策略纳入。建议维护者将其列为下版本技术评审项，评估对现有 `steering` 逻辑的侵入性。
- **兼容层扩展**：PR #1158 的合并不仅闭环 #269，也释放了项目持续拓宽 LLM 协议抽象层（支持 OpenAI/Anthropic 原生格式双轨）的路线图信号。未来多代理/跨服务商场景的适配成本预计将进一步降低。

## 7. 用户反馈摘要
- **核心痛点**：现有消息处理机制缺乏队列缓冲，长周期任务易被突发输入打断，影响复杂工作流的确定性。
- **正面反馈**：网络抓取精度提升直接改善工具可靠性；Anthropic 原生协议支持解决了代理接入的长期限制；文档重构使仓库对 AI 助手与人类贡献者更友好。
- **典型场景**：多步工具链自动化、依赖实时网页数据的推理任务、使用非 OpenAI 格式第三方 LLM 服务的混合架构。

## 8. 待处理积压
今日数据未显示严重积压，但存在 1 条需优先 triage 的新增请求：
- **Issue #3342**（特性请求）：建议维护者评估实现路径（如基于现有调度器的非阻塞队列改造）及配置开关设计，并反馈大致排期。
- 其余 PR 与 Issue 状态健康，无长期未响应的阻塞项。建议在下个版本 Note 中同步 #3342 的处理结论，以维持社区参与预期。

---
*数据周期：2026-08-21 00:00 ~ 2026-08-22 00:00 UTC*  
*分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目日报 — 2026-08-22

## 1. 今日速览

过去24小时 NanoClaw 项目保持**高活跃度**：24 条 PR 更新（11 条合并/关闭，13 条待合并），1 条新开 Issue。核心贡献者 `amit-shafnir` 集中推进了 Template Agent、Telegram 多实例、Dial 集成等关键功能，`zvi-fried` 修复了多个稳定性问题（Matrix ESM patch、CI required check、registry skill 测试）。无新版本发布，仓库在频道集成、初始化向导体验和 CI 健壮性方面持续迭代。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展 — 今日合并/关闭的重要 PR

### 🔧 基础设施与稳定性
| PR | 类型 | 说明 |
|----|------|------|
| [#3439](https://github.com/nanocoai/nanoclaw/pull/3439) | 依赖升级 | Claude Code CLI 2.1.197 → 2.1.238，Agent SDK 0.3.197 → 0.3.238 |
| [#3403](https://github.com/nanocoai/nanoclaw/pull/3403) | 修复 | Matrix 适配器增加 refresh-safe ESM patch，修复 Node 22 下 extensionless import 失败 |
| [#3430](https://github.com/nanocoai/nanoclaw/pull/3430) | 修复 | 恢复 CI required check，修复 Node 22/24 matrix 下 `ci` 检查名变更导致的永久 pending |
| [#3424](https://github.com/nanocoai/nanoclaw/pull/3424) | CI | 新增 registry-backed skills 测试流程，覆盖所有 `add-*` 频道/Provider skill |
| [#3429](https://github.com/nanocoai/nanoclaw/pull/3429) | 功能 | 正式确立 `SessionExecSpec` driver 契约（`bin, argsTty, argsPlain`），为交互式 tool attach 能力铺路 |

### 📡 频道集成
| PR | 类型 | 说明 |
|----|------|------|
| [#3202](https://github.com/nanocoai/nanoclaw/pull/3202) | 新功能 | 新增 **Mattermost** 频道集成（复用 Chat SDK 模式） |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | 新功能 | **Dial** 正式加入频道选择器和初始化向导 |
| [#3433](https://github.com/nanocoai/nanoclaw/pull/3433) | 修复 | `add-dial-number` skill 改用 nc directives，消除 registry 识别异常 |
| [#3402](https://github.com/nanocoai/nanoclaw/pull/3402) | 修复 | 接受 provider 文件事件，修复 branch-backed provider 事件丢失 |
| [#3401](https://github.com/nanocoai/nanoclaw/pull/3401) | 修复 | whatsapp-cloud skill payload 与 main 兼容，修复跨分支测试失败 |

### 🤖 Agent 模板与初始化体验
| PR | 类型 | 说明 |
|----|------|------|
| [#3396](https://github.com/nanocoai/nanoclaw/pull/3396) | 新功能 | **从模板创建 Agent**：`create_agent` 工具新增 `template` 参数，支持 `ncl templates list` |
| [#3428](https://github.com/nanocoai/nanoclaw/pull/3428) | 新功能 | Slack 创建流程透传 template ref，补全模板化 Agent 创建链路 |
| [#3436](https://github.com/nanocoai/nanoclaw/pull/3436) | 新功能 | Telegram 支持 `TELEGRAM_INSTANCES` 多 bot 实例 + 实例绑定配对 |
| [#3438](https://github.com/nanocoai/nanoclaw/pull/3438) | 新功能 | 初始化向导：已配置一个 bot 时，提示"添加另一个 Telegram bot" |
| [#3435](https://github.com/nanocoai/nanoclaw/pull/3435) | 修复 | pairing 阶段透传 adapter 实例，修复多实例场景下的初始化链路断裂 |
| [#3431](https://github.com/nanocoai/nanoclaw/pull/3431) | 修复 | Telegram pairing card 显示正确的 6 位验证码 |
| [#3434](https://github.com/nanocoai/nanoclaw/pull/3434) | 修复 | polling 模式适配器不再错误启动 webhook 服务器 |
| [#3287](https://github.com/nanocoai/nanoclaw/pull/3287) | 修复 | 修正 inbound 消息 ID 携带 agent-group 后缀的 bug |
| [#3432](https://github.com/nanocoai/nanoclaw/pull/3432) | 修复 | Dial post-merge follow-up：凭证重填、步骤说明、registry CI |

> **整体评估**：今日 11 条 PR 中约 80% 为功能新增或体验优化（模板 Agent、Mattermost、Telegram 多实例、Dial 集成），约 20% 为稳定性修复。项目正向"多频道 + 模板化 Agent 初始化"方向快速推进。

---

## 4. 社区热点

### 🔴 重点关注 Issue
**[#3426](https://github.com/nanocoai/nanoclaw/issues/3426) — [bug] send_card docs promise callback buttons that the bridge drops since #2265**
- 作者：`glifocat` · 创建于 2026-08-21
- **问题核心**：`send_card` 文档声明支持 `actions`（按钮），但 Bridge 会丢弃所有无 `url` 的 action。Agent 看到按钮消失，结合 `fallbackText` 提示误判为"平台不支持卡片渲染"，导致 agent 向用户返回误导性信息。
- **诉求分析**：文档与行为不一致，影响 agent 对平台能力的判断准确性。涉及 Bridge 与 Agent SDK 间的 contract 对齐问题，可能需要：① 修复 Bridge 丢弃无 URL action 的行为；② 更新文档明确 `actions` 要求；③ 或在 Agent 侧增加降级提示逻辑。

### 🟡 其他活跃 PR
- [#3396](https://github.com/nanocoai/nanoclaw/pull/3396) — 模板 Agent 创建功能获 core-team 审核，后续可能有更多 template 相关讨论
- [#3428](https://github.com/nanocoai/nanoclaw/pull/3428) — Slack template 透传，supersedes 了之前有冲突的 #3397，说明 PR 间的依赖管理是近期社区关注点

---

## 5. Bug 与稳定性

| 级别 | 问题 | 状态 | 修复 PR |
|------|------|------|---------|
| 🔴 高 | `send_card` bridge 丢弃无 URL 的 action，导致 agent 误报平台不支持按钮 | 新开，待处理 | — |
| 🟡 中 | Matrix 适配器在 Node 22 下 ESM import 失败 | ✅ 已修复 | [#3403](https://github.com/nanocoai/nanoclaw/pull/3403) |
| 🟡 中 | CI required check 因 Node 22/24 matrix 变更而永久 pending | ✅ 已修复 | [#3430](https://github.com/nanocoai/nanoclaw/pull/3430) |
| 🟡 中 | polling 模式适配器错误启动 webhook 服务器 | ✅ 已修复 | [#3434](https://github.com/nanocoai/nanoclaw/pull/3434) |
| 🟢 低 | Telegram pairing card 显示位数错误 | ✅ 已修复 | [#3431](https://github.com/nanocoai/nanoclaw/pull/3431) |
| 🟢 低 | inbound 消息 ID 携带 agent-group 后缀 | ✅ 已修复 | [#3287](https://github.com/nanocoai/nanoclaw/pull/3287) |
| 🟢 低 | whatsapp-cloud skill payload 跨分支不兼容 | ✅ 已修复 | [#3401](https://github.com/nanocoai/nanoclaw/pull/3401) |

> **稳定性评估**：今日修复了 7 个 bug（含 1 个高优先级），CI 稳定性和频道适配器兼容性显著改善。仅 #3426 待处理，为文档/行为不一致类问题，不影响运行但影响 agent 决策准确性。

---

## 6. 功能请求与路线图信号

### 已合入/待合并的功能信号
| 功能方向 | 相关 PR | 判断 |
|----------|---------|------|
| **模板化 Agent 初始化** | #3396, #3428 | 已在 chat 侧合入，Slack 侧待合并，预计下一版本完整上线 |
| **Telegram 多 bot 实例** | #3436, #3438, #3435, #3437 | 功能完整，文档待合并，预计纳入下一版本 |
| **Dial 频道正式集成** | #3050, #3432, #3433 | 核心功能已合入，follow-up 修复中 |
| **Mattermost 频道支持** | #3202 | 已合入，新增频道 |
| **Driver attach 契约** | #3429 | 为交互式 tool attach 能力奠定基础，后续可能有更多 driver 相关 PR |

> **路线图判断**：项目正聚焦于"多频道 + 模板化 Agent + 标准化初始化体验"三大方向。下一版本预计包含：模板 Agent 完整链路（chat + Slack + Telegram）、Telegram 多实例、Mattermost 集成、以及 Dial 的稳定性加固。

---

## 7. 用户反馈摘要

- **痛点 1**：`send_card` 文档承诺支持按钮，但 Bridge 实际丢弃无 URL 的 action，agent 据此向用户返回错误信息（[#3426](https://github.com/nanocoai/nanoclaw/issues/3426)）。用户期望文档与行为对齐。
- **痛点 2**：Telegram 多 bot 场景下，配对流程和初始化向导缺乏对"已配置实例"的认知，导致重复配置或配对失败（由 #3438、#3435、#3436 系列 PR 间接反映）。
- **痛点 3**：Node 22/24 CI matrix 变更后，required check 命名变化导致 CI 永久 pending，影响开发者体验（[#3430](https://github.com/nanocoai/nanoclaw/pull/3430)）。
- **正面反馈**：Mattermost 集成（[#3202](https://github.com/nanocoai/nanoclaw/pull/3202)）、模板 Agent 创建（[#3396](https://github.com/nanocoai/nanoclaw/pull/3396)）、Dial 正式支持（[#3050](https://github.com/nanocoai/nanoclaw/pull/3050)）等功能得到社区贡献者积极响应。

---

## 8. 待处理积压

| 类型 | 编号 | 说明 | 建议优先级 |
|------|------|------|-----------|
| 🐛 Bug | [#3426](https://github.com/nanocoai/nanoclaw/issues/3426) | `send_card` bridge 丢弃无 URL action，agent 误报平台不支持 | 高 — 影响 agent 决策准确性 |
| 🔀 PR | [#3428](https://github.com/nanocoai/nanoclaw/pull/3428) | Slack template 透传，supersedes #3397，待合并 | 中 — 模板 Agent 功能闭环 |
| 🔀 PR | [#3437](https://github.com/nanocoai/nanoclaw/pull/3437) | Telegram 多 bot 文档更新，待合并 | 中 — 配合 #3436 功能 |
| 🔀 PR | [#3432](https://github.com/nanocoai/nanoclaw/pull/3432) | Dial post-merge follow-up，待合并 | 中 — Dial 稳定性加固 |
| 🔀 PR | [#3435](https://github.com/nanocoai/nanoclaw/pull/3435) | adapter 实例透传，待合并 | 中 — Telegram 多实例配对修复 |

---

**项目健康度评分**：🟢 良好 — 高 PR 吞吐、核心 contributor 活跃、bug 修复及时，仅 1 条待处理 bug issue。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目动态日报 | 2026-08-22

## 1. 今日速览

今日 NullClaw 项目整体活跃度较低，无 Issue 更新，无新版本发布。唯一动态为 PR #990 待合并，由 MVS-source 提交，旨在将 Eden AI 作为 OpenAI 兼容网关接入项目。项目当前处于平稳推进状态，维护者暂无新响应。

---

## 2. 版本发布

> 今日无新版本发布。

---

## 3. 项目进展

**待合并 PR：[#990](https://github.com/nullclaw/nullclaw/pull/990)**

- **类型：** 新功能（feat）
- **内容：** 添加 Eden AI 作为 OpenAI 兼容网关提供商，复用 `OpenAiCompatibleProvider` 实现，与 PR #922（NEAR AI Cloud 和 Atlas Cloud）保持一致的接入模式。
- **项目意义：** 扩展了项目的 AI 网关供应商生态，用户无需为 Eden AI 编写独立 provider，降低维护成本的同时丰富了上游厂商支持。
- **进展状态：** 待合并，尚无合并/关闭记录。

---

## 4. 社区热点

今日无高热度 Issue 或 PR 讨论。唯一关注点为 PR #990：

- **PR #990** - [feat(providers): add Eden AI as an OpenAI-compatible gateway](https://github.com/nullclaw/nullclaw/pull/990)
  - **诉求分析：** 用户希望支持 Eden AI 这一 EU-based 多厂商路由网关，满足数据主权与合规需求，同时避免重复实现 provider 逻辑。

---

## 5. Bug 与稳定性

> 今日无 Bug 报告、崩溃或回归问题。

---

## 6. 功能请求与路线图信号

- **EDEN AI 支持请求（PR #990）：** 反映出社区对多厂商聚合网关的需求持续存在，尤其是具备合规优势（EU-based）的服务商。该 PR 与 #922 模式一致，预计合并后可作为下一版本的 provider 扩展之一。

---

## 7. 用户反馈摘要

> 今日无新 Issue 或 PR 评论，无用户反馈数据。

---

## 8. 待处理积压

| 类型 | ID | 内容 | 状态 | 链接 |
|------|-----|------|------|------|
| PR | #990 | 添加 Eden AI 作为 OpenAI 兼容网关 | 待合并（创建于 2026-08-21） | [PR #990](https://github.com/nullclaw/nullclaw/pull/990) |

- **提醒：** PR #990 已等待一日，暂无维护者响应。建议关注合并进度，确认是否需要补充测试或文档。

---

**项目健康度评估：** 🟡 平稳 | 活跃度偏低，无阻塞问题，功能扩展持续推进中。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-08-22

## 1. 今日速览

过去 24 小时 IronClaw 项目保持高度活跃：**15 条 Issues**（11 新开/活跃，4 关闭）与 **35 条 PRs**（19 待合并，16 已合并/关闭）。核心重心集中在三条主线：CI 加速体系重构（T1-T4 四轨并行推进）、可插拔内存系统（MCP 协议）的落地完善，以及 WebUI 组件标准化与通知中心架构升级。无新版本发布，但多个关键修复与功能 PR 已合并入库，项目基础设施健壮性与开发者体验同步推进。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

今日合并/关闭的 PR 为项目带来以下实质性推进：

| PR | 类型 | 核心内容 |
|---|---|---|
| [#7805](https://github.com/nearai/ironclaw/pull/7805) | 修复 | 将 clippy 1.98 lint 修复前端口至 `release/2026-08-17`，解决 `chunks_exact` 常量块大小编译失败 |
| [#7804](https://github.com/nearai/ironclaw/pull/7804) | 修复 | 修复 `IRONCLAW_REBORN_WORKSPACE_ROOT` 环境变量在 `release/2026-08-17` 分支缺失的回归 |
| [#7803](https://github.com/nearai/ironclaw/pull/7803) | 修复 | Telegram 频道配对与个人账号认证逻辑修正，避免工作区机器人被误映射为个人账号 |
| [#7797](https://github.com/nearai/ironclaw/pull/7797) | 文档/治理 | 仓库级 agent guidance 审计：删除 21.5k 行漂移文档，统一测试规范至 `AGENTS.md` 约定 |
| [#7796](https://github.com/nearai/ironclaw/pull/7796) | 修复 | Railway 审计追加失败的闭源处理，保证审计记录可重放 |
| [#7802](https://github.com/nearai/ironclaw/pull/7802) | 修复 | 移除 `IRONCLAW_OOBE_SUGGESTIONS` 环境变量与 session feature gate，OOBE 建议始终启用 |
| [#7699](https://github.com/nearai/ironclaw/pull/7699) | 功能 | 将审批/认证/阻塞类运行时 gate 事件写入持久化用户 Inbox |
| [#7690](https://github.com/nearai/ironclaw/issues/7690) | 功能 | 自动化审批、认证、阻塞运行通知已发布至用户 Inbox（Issue 闭环） |

**整体判断：** 项目当前处于"基建加固期"——CI 流水线可重复性、存储隔离性、通知可追溯性同步提升，为后续功能扩张奠定稳定底座。

---

## 4. 社区热点

### 🔥 最活跃 Issue/PR（按评论数与关注度）

**1. CI Expedite 系列（T1–T4）— 4 个并行 Issue + 配套 PR**
- [Issue #7798 (T1)](https://github.com/nearai/ironclaw/issues/7798) — 统一 `setup-rust` composite action，替换 12 个工作流中 43 处散落的 `dtolnay/rust-toolchain` 调用
- [Issue #7799 (T2)](https://github.com/nearai/ironclaw/issues/7799) — `cargo-nextest` 替换顺序测试，引入 JUnit 失败汇总与 PR 并行度调整
- [Issue #7800 (T3)](https://github.com/nearai/ironclaw/issues/7800) — PR/Queue 绿灯分歧收敛：磁盘读取测试漂移守卫 + clippy `default-features`
- [Issue #7801 (T4)](https://github.com/nearai/ironclaw/issues/7801) — `preflight-gates.sh` 成为单一权威门禁列表，支持 worktree-safe hooks

**诉求分析：** 核心贡献者 `henrypark133` 系统性解决 CI 流水线碎片化问题，目标是建立可测量、可复现、自文档化的门禁体系，减少 PR 合并前的等待时间（当前预测耗时约 5 分钟）。

**2. 可插拔内存系统（MCP 协议）**
- [Issue #7664](https://github.com/nearai/ironclaw/issues/7664) — 追踪 pluggable memory 完成度，以 Mnesis Core 为首个消费者
- [Issue #7808](https://github.com/nearai/ironclaw/issues/7808) — **关键安全前置条件**：写路径必须在任何外部 provider 绑定前执行 redaction + taint metadata 注入

**诉求分析：** 内存系统正在从"内部实现"走向"可配置外部协议"，`#7808` 表明安全审查已进入最后阶段，防止隐私数据外泄是当前首要关注点。

**3. WebUI 设计系统标准化**
- [Issue #7792](https://github.com/nearai/ironclaw/issues/7792) — 引入共享 `PageScroll`/`PageStack`/`Skeleton` 组件
- [Issue #7793](https://github.com/nearai/ironclaw/issues/7793) — 将 Settings/Admin 残留 banners 统一迁移至 `InlineNotice`
- [PR #7750](https://github.com/nearai/ironclaw/pull/7750) — Storybook + 设计系统 catalog Phase 1 集成
- [PR #7257](https://github.com/nearai/ironclaw/pull/7257) — 设计系统全量提案与检查清单

**诉求分析：** WebUI 长期存在组件重复与样式不一致问题，当前通过架构重构系统性解决，预计将显著提升前端开发效率与用户体验一致性。

**4. GitHub CLI 凭证中介**
- [PR #7810](https://github.com/nearai/ironclaw/pull/7810)（进行中）/ [#7807](https://github.com/nearai/ironclaw/pull/7807) / [#7806](https://github.com/nearai/ironclaw/pull/7806)（已合并）— 通过 sandbox 机制将 `gh` 命令凭证化，执行前完成授权/审批

---

## 5. Bug 与稳定性

| 问题 | 严重度 | 状态 | 链接 |
|---|---|---|---|
| LLM 超时策略缺陷：结构化输出最终化无法测量 TTFT，重试预算超出截止时间 | **中（llm 作用域）** | 已关闭 [#7783](https://github.com/nearai/ironclaw/issues/7783) | [Issue #7783](https://github.com/nearai/ironclaw/issues/7783) |
| Telegram 连接流程缺少 Bot/个人账号间的用户选择与同意提示 | **中（P2）** | 已关闭 [#7715](https://github.com/nearai/ironclaw/issues/7715) | [Issue #7715](https://github.com/nearai/ironclaw/issues/7715) |
| Onboarding 建议生成未尊重用户级工具权限，且仅依赖内部搜索工具 | **低** | 新开 [#7812](https://github.com/nearai/ironclaw/issues/7812) | [Issue #7812](https://github.com/nearai/ironclaw/issues/7812) |
| UI 聊天首页 "What do you need help with?" 标题在建议面板出现时被裁切 | **低（UI）** | 新开 [#7813](https://github.com/nearai/ironclaw/issues/7813) | [Issue #7813](https://github.com/nearai/ironclaw/issues/7813) |

**稳定性评估：** 近期合并的 clippy lint 修复（#7805）和 workspace root 回归修复（#7804）消除了两个潜在的编译/运行时问题。Telegram 连接体验已修复。当前无高危或阻塞性 Bug。

---

## 6. 功能请求与路线图信号

| 需求 | 状态 | 关联 PR/Issue | 纳入下版本可能性 |
|---|---|---|---|
| 可插拔内存系统（MCP 协议） | 进行中 | [#7664](https://github.com/nearai/ironclaw/issues/7664) + [#7808](https://github.com/nearai/ironclaw/issues/7808) | ⭐⭐⭐ 高 — 安全审查（#7808）是最后前置条件，预计下个迭代完成 |
| Mnesis Core 作为首个外部内存消费者 | 进行中 | [#7664](https://github.com/nearai/ironclaw/issues/7664) | ⭐⭐⭐ 高 |
| OOBE 建议始终启用 | 已修复 | [#7802](https://github.com/nearai/ironclaw/pull/7802) | ✅ 已合并 |
| 扩展商店集成 Xquik MCP（Twitter/X 数据） | 进行中 | [#7811](https://github.com/nearai/ironclaw/pull/7811) | ⭐⭐ 中 — OAuth 2.1 + PKCE 已实现，等待审查 |
| IronHub Agent Link WebUI 操作面板 | 进行中 | [#7516](https://github.com/nearai/ironclaw/pull/7516) | ⭐⭐ 中 — 填补 CLI-only 空白 |
| WebUI 通知中心 → 持久化用户 Inbox | 部分完成 | [#7687](https://github.com/nearai/ironclaw/issues/7687) + [#7700](https://github.com/nearai/ironclaw/pull/7700) | ⭐⭐⭐ 高 — 后端已写入，前端展示层持续推进中 |
| GitHub CLI 凭证中介（sandbox 化） | 部分完成 | [#7810](https://github.com/nearai/ironclaw/pull/7810) | ⭐⭐ 中 |
| Telegram 连接模式选择 UX | 已修复 | [#7803](https://github.com/nearai/ironclaw/pull/7803) 关闭 #7715 | ✅ 已合并 |

---

## 7. 用户反馈摘要

**痛点：**
- **LLM 超时不可观测**（#7783）：结构化输出最终化阶段，TTFT 无法测量，导致 60s 总墙钟超时与 75s 最终化截止时间的双重矛盾，单次传输卡顿即可销毁整个 run。此问题已通过关闭 Issue 确认，需关注是否已在代码层面调整超时策略。
- **Telegram 连接模式不透明**（#7715，已关闭）：用户连接 Bot 或 Personal Account 时无明确选择与同意提示，体验混淆。
- **Onboarding 建议与用户实际数据脱节**（#7812）：建议生成仅使用内部搜索工具，未接入用户实际连接的扩展与工具权限。

**满意度信号：**
- CI 流水线正在被系统性重构，开发者对可预测的 gate 列表和 worktree-safe hooks 有明确需求，反映社区对开发效率的重视。
- WebUI 设计系统标准化（#7792, #7793）获得内部开发者认可，消除了长期存在的样式不一致问题。
- 持久化用户 Inbox（#7687）解决了此前通知"只读一次"不可追溯的痛点。

---

## 8. 待处理积压

| Issue/PR | 等待时间 | 风险 | 建议 |
|---|---|---|---|
| [#7810](https://github.com/nearai/ironclaw/pull/7810) — GitHub CLI 凭证中介（进行中 PR） | ~1 天 | 低 | 与已合并的 #7806/#7807 保持对齐，确认最终方案一致 |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) — IronHub Agent Link WebUI 操作面板 | ~10 天 | 低 | 等待核心贡献者审查，填补 CLI-only 空白 |
| [#7811](https://github.com/nearai/ironclaw/pull/7811) — Xquik hosted MCP bundle | <1 天 | 低 | 新贡献者 PR，建议快速审查以促进社区参与 |
| [#7664](https://github.com/nearai/ironclaw/issues/7664) — Pluggable Memory 完成追踪 | ~8 天 | 中 | 依赖 #7808 安全修复，完成后即具备发布条件 |
| [#7813](https://github.com/nearai/ironclaw/issues/7813) — UI 标题裁切 Bug | <1 天 | 低 | 快速 UI fix，建议优先处理 |
| [#7812](https://github.com/nearai/ironclaw/issues/7812) — Onboarding 建议权限尊重 | <1 天 | 低 | 与 #7664 内存系统存在依赖关系，可异步推进 |

---

**项目健康度评估：** 🟢 良好。基础设施层（CI、存储、通知）正在经历系统性加固，功能层（内存插件、扩展生态、WebUI）稳步推进。无阻塞性 Bug，社区贡献活跃（新贡献者 PR #7811、#7516），技术债清理与功能扩张同步进行。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI 项目日报 | 2026-08-22

---

## 1. 今日速览

LobsterAI 项目在 2026 年 8 月 21 日呈现高活跃度，**13 条 PR 全部处理完毕（12 条合并，1 条待审）**，其中 10 条为当日新合并，涵盖 DSH 实验性功能发布、性能优化与 i18n 修复三大主线。Issues 层面关闭 2 个历史遗留 bug，社区反馈得到及时响应。项目整体健康度良好，技术债清理与功能迭代并行推进，但仍有 1 个待合并 PR 需关注。

---

## 2. 版本发布

> 无新版本发布

今日 PR #2519 将 `release/2026.8.21` 分支合并至 `main`，标志 **2026.8.21 版本**开发周期结束。该版本核心变更包括：
- 实验性 DeepSeek Harness (DSH) 运行时升级至 `0.1.1-rc.1`
- DSH 功能启用与工作区打开的埋点分析上线
- Windows 系统集成可靠性改进

---

## 3. 项目进展

### 核心功能迭代
| PR | 内容 | 影响 |
|---|---|---|
| [#2519](https://github.com/netease-youdao/LobsterAI/pull/2519) | Release 2026.8.21 合并 | 版本发布入口 |
| [#2516](https://github.com/netease-youdao/LobsterAI/pull/2516) | DSH 升级至 0.1.1-rc.1 | 实验性功能迭代 |
| [#2515](https://github.com/netease-youdao/LobsterAI/pull/2515) | DSH 使用埋点（主进程） | 数据驱动决策 |
| [#2518](https://github.com/netease-youdao/LobsterAI/pull/2518) | 埋点逻辑迁移至 renderer | 架构解耦 |

### 体验与性能优化
| PR | 内容 | 影响 |
|---|---|---|
| [#2517](https://github.com/netease-youdao/LobsterAI/pull/2517) | 文件分享与收藏交互完善 | 资料库体验 |
| [#2514](https://github.com/netease-youdao/LobsterAI/pull/2514) | 本地产物预览与操作优化 | 资料库体验 |
| [#1219](https://github.com/netease-youdao/LobsterAI/pull/1219) | 消除会话列表/详情页无效重渲染 | 性能提升 |
| [#1220](https://github.com/netease-youdao/LobsterAI/pull/1220) | 消除 recentChats/conversationSearch 的 N+1 查询 | 性能提升 |
| [#1218](https://github.com/netease-youdao/LobsterAI/pull/1218) | 重构定时任务列表排序规则 | 交互体验 |
| [#1215](https://github.com/netease-youdao/LobsterAI/pull/1215) | 修复 IM 聊天处理器 stale 问题 | 稳定性 |
| [#1224](https://github.com/netease-youdao/LobsterAI/pull/1224) | 修复 i18n 硬编码、Agent 弹窗 Escape 键及删除防重复点击 | i18n + 体验 |

> **进展评估**：今日合并的 12 条 PR 中，性能优化占 2 条、体验修复占 4 条、功能迭代占 4 条、版本发布占 1 条、架构优化占 1 条。项目处于活跃迭代期，技术债清理力度较大。

---

## 4. 社区热点

| Issue/PR | 标题 | 评论 | 热度分析 |
|---|---|---|---|
| [#1217](https://github.com/netease-youdao/LobsterAI/issues/1217) | 运行过程中偶发启动网关 | 2 | 用户反馈网关稳定性问题，复现概率较高（日均 3-5 次），影响核心使用场景 |
| [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223) | CoworkPromptInput 硬编码中文 + Agent 弹窗问题 | 2 | 涉及 i18n 合规性与基础交互体验，已合并 PR #1224 修复 |
| [#1550](https://github.com/netease-youdao/LobsterAI/pull/1550) | 投递模式"不通知"时去除 channel/to 字段 | 0 | 定时任务边界场景修复，待合并 |

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | 严重程度 | 修复状态 |
|---|---|---|---|---|
| P1 | [#1217](https://github.com/netease-youdao/LobsterAI/issues/1217) | 运行过程中偶发重启网关，影响正常使用 | 🔴 高 | ✅ 已关闭（[stale]） |
| P2 | [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223) | i18n 硬编码中文混入提示词、Agent 弹窗缺少 Escape 关闭及删除防重复点击 | 🟡 中 | ✅ 已修复（PR #1224） |
| P3 | [#1550](https://github.com/netease-youdao/LobsterAI/pull/1550) | 定时任务投递模式为"不通知"时，网关校验报错 | 🟡 中 | ⏳ 待合并 |

> **稳定性评估**：今日关闭的 Issue 均为历史遗留问题，无新增高风险 bug。PR #1550 涉及的边界场景修复已就绪，预计合并后可进一步提升定时任务稳定性。

---

## 6. 功能请求与路线图信号

| 信号来源 | 内容 | 路线图中推断 |
|---|---|---|
| PR #2516/#2515/#2518 | DSH（DeepSeek Harness）运行时升级与埋点完善 | DSH 实验性功能进入稳定期，后续可能转为正式功能 |
| PR #2517/#2514 | 资料库文件分享、收藏、预览体验全面优化 | 资料库模块为当前迭代重点，持续投入 |
| PR #1219/#1220 | Cowork 模块性能优化（渲染 + 查询） | 长期性能优化计划持续推进 |
| PR #1218 | 定时任务排序规则重构 | 定时任务模块体验持续打磨 |

> **路线图判断**：项目当前聚焦于 **DSH 实验性功能上线**、**资料库模块完善**、**Cowork 性能优化**三大方向，预计下一版本将围绕 DSH 正式化与资料库体验深化展开。

---

## 7. 用户反馈摘要

| 来源 | 痛点/场景 | 情绪 |
|---|---|---|
| [#1217](https://github.com/netease-youdao/LobsterAI/issues/1217) | Windows 10 环境下网关偶发重启，日均 3-5 次，严重影响使用连续性 | 😠 不满 |
| [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223) | 英文用户发送含附件消息时，提示词中混入中文「输入文件」，违反多语言一致性原则 | 😐 中性（期待修复） |
| [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223) | Agent 创建/设置弹窗缺少 Escape 键关闭、删除操作无防重复点击保护 | 😐 中性（体验细节） |
| [#1550](https://github.com/netease-youdao/LobsterAI/pull/1550) | 通过会话/IM 创建的定时任务设置"不通知"模式后，触发运行时网关校验报错 | 😠 不满 |

---

## 8. 待处理积压

| PR/Issue | 标题 | 创建时间 | 状态 | 建议 |
|---|---|---|---|---|
| [#1550](https://github.com/netease-youdao/LobsterAI/pull/1550) | 投递模式"不通知"时去除发送给网关的 channel/to 字段 | 2026-04-07 | ⏳ OPEN（待合并） | 建议尽快合并，修复定时任务边界场景报错 |
| [#2513](https://github.com/netease-youdao/LobsterAI/pull/2513) | Feat/2026.8.17 library | 2026-08-21 | ✅ CLOSED | 确认是否已包含在 release/2026.8.21 中 |

---

**📊 项目健康度评分**：⭐⭐⭐⭐☆（4/5）
- 活跃度：高（13 PR/24h）
- 响应速度：良好（Issue 2 日内关闭，PR 当日处理）
- 技术债：逐步清理中（性能优化持续投入）
- 风险提示：PR #1550 已待处理约 4 个月，建议加速合并流程

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报
**日期：2026-08-22** | 数据来源：GitHub API | 统计周期：过去24小时

---

## 1. 今日速览

Moltis 在过去24小时保持中等活跃度，共新增 2 个 Issues 和 8 个 PR，其中 1 个 PR 已合并。活跃贡献者 **rubenssoto** 单日提交 3 个 PR，集中在 WhatsApp 网关修复和浏览器隐身模式优化，显示出对WhatsApp集成的重点投入。Cron 定时任务的稳定性问题持续受到关注，至少两个 PR 涉及 `heartbeat.active_hours` 的行为修正。整体项目处于稳定迭代阶段，无版本发布，无重大回归风险。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭

| PR | 类型 | 作者 | 说明 |
|----|------|------|------|
| [#1220](https://github.com/moltis-org/moltis/pull/1220) | fix(whatsapp) | rubenssoto | WhatsApp 出站消息 Markdown 渲染支持，将模型生成的 Markdown 转换为 WhatsApp 原生标记，提升消息可读性 |

**推进内容：** WhatsApp 网关体验改进——Markdown 渲染是高频用户需求，合并后用户可在 WhatsApp 会话中获得更规范的格式化输出，无需手动处理标记符号。

### 待合并（7 个）

| PR | 类型 | 作者 | 说明 |
|----|------|------|------|
| [#1228](https://github.com/moltis-org/moltis/pull/1228) | fix(whatsapp) | rubenssoto | 持久化 WhatsApp 入站文件，为本地工具提供稳定的 `local_path`，限制 20MB |
| [#1227](https://github.com/moltis-org/moltis/pull/1227) | fix(browser) | rubenssoto | 默认启用 Obscura 隐身模式，新增 `tools.browser.obscura_stealth` 配置项 |
| [#1226](https://github.com/moltis-org/moltis/pull/1226) | fix(cron) | rubenssoto | 定时任务输出投递回原始聊天窗口，修复路由丢失问题 |
| [#1225](https://github.com/moltis-org/moltis/pull/1225) | fix(i18n) | PeterDaveHello | 繁体中文（zh-TW）本地化更新，重点修订 `connectors.ts` 翻译 |
| [#1222](https://github.com/moltis-org/moltis/pull/1222) | fix(web) | tsauvajon | Sandbox 镜像请求校验，限制包检查和镜像构建仅对管理员开放 |
| [#1208](https://github.com/moltis-org/moltis/pull/1208) | fix(cron) | Lstarsky0 | 修复 `heartbeat.active_hours` 从未生效的问题，对应 Issue #1205/#1223 |
| [#468](https://github.com/moltis-org/moltis/pull/468) | fix(plugins) | jmikedupont2 | Windows 下 shell hooks 改用 `cmd.exe /C`，解决跨平台兼容性 |

**整体进展评估：** 今日代码变更以修复为主（8/8 均为 `fix`），无新功能开发，反映出项目当前处于稳定性和体验优化阶段。Rubenssoto 贡献占据主导（3/8），WhatsApp 网关是多线程修复的核心区域。

---

## 4. 社区热点

### 今日新增 Issues

**#1224** [bug] Tools stop working in shared Slack channels
- 作者: affanshahid | 创建: 2026-08-21
- [链接](https://github.com/moltis-org/moltis/issues/1224)
- **分析：** 在共享 Slack 频道中工具停止工作，涉及多用户/多上下文场景下的工具路由问题。当前 0 评论，属于新建报告，可能影响企业级 Slack 集成场景。

**#1223** heartbeat active_hours has no effect on a default config
- 作者: Lstarsky0 | 创建: 2026-08-21
- [链接](https://github.com/moltis-org/moltis/issues/1223)
- **分析：** `active_hours` 配置（默认 `08:00–24:00`）在任何时段均不产生抑制效果，`is_within_active_hours` 函数逻辑存在解析缺陷。该 Issue 已由 PR #1208 修复，属于已知问题的快速跟进。

---

## 5. Bug 与稳定性

| 严重级别 | 问题 | 关联 PR | 状态 |
|----------|------|---------|------|
| 🔴 高 | `heartbeat.active_hours` 配置完全失效，定时任务不受活跃时段约束 | [#1208](https://github.com/moltis-org/moltis/pull/1208) | ✅ PR 待合并 |
| 🟡 中 | Slack 共享频道中工具停止工作（#1224），影响多通道协同场景 | 无 | 📋 待响应 |
| 🟡 中 | WhatsApp 入站文件无法被本地工具访问（#1228 修复中） | [#1228](https://github.com/moltis-org/moltis/pull/1228) | 🔄 PR 待合并 |

**稳定性评估：** 无崩溃类报告。`heartbeat` 定时逻辑缺陷影响调度准确性，PR #1208 已覆盖。Slack 共享频道问题尚无对应 PR，建议维护者关注。

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 说明 |
|------|------|------|
| WhatsApp 入站文件持久化 | [#1228](https://github.com/moltis-org/moltis/pull/1228) | 本地工具需要稳定的文件路径引用，20MB 限制体现安全边界意识 |
| WhatsApp Markdown 渲染 | [#1220](https://github.com/moltis-org/moltis/pull/1220) | 已合并，反映用户对格式化输出有明确需求 |
| 浏览器隐身模式默认启用 | [#1227](https://github.com/moltis-org/moltis/pull/1227) | 安全/反检测需求，通过配置项保留灵活性 |
| Windows shell hooks 兼容 | [#468](https://github.com/moltis-org/moltis/pull/468) | 长期未合并保持开放（创建距今 5 个月），反映 Windows 用户群体的持续关注 |
| 繁体中文本地化深化 | [#1225](https://github.com/moltis-org/moltis/pull/1225) | i18n 覆盖面扩展，`connectors.ts` 为重点修订模块 |

**路线判断：** WhatsApp 集成是近期高频修复领域，预计下一版本将强化该网关的完整性；Windows 兼容性（#468）积压较久，建议优先处理。

---

## 7. 用户反馈摘要

| 用户/Issue | 痛点 | 使用场景 |
|------------|------|----------|
| Lstarsky0 (#1223) | 配置了 `active_hours` 但定时任务不遵守，调度行为与预期不符 | 希望按时段控制心跳/定时任务行为，用于节省资源或避免非工作时间通知 |
| affanshahid (#1224) | 共享 Slack 频道中工具突然失效 | 企业/团队 Slack 环境中多人共用 bot，工具调用出现上下文混淆 |
| rubenssoto (PR 提交者) | WhatsApp 入站文件仅暴露元数据，本地工具无法访问实际内容 | 需要通过 WhatsApp 接收图片/文档并调用本地处理工具 |

**满意度信号：** 无显式负面反馈，但多个 PR 针对同一模块（WhatsApp）连续修复，暗示该网关此前存在体验缺口。

---

## 8. 待处理积压

| PR/Issue | 作者 | 创建时间 | 状态 | 建议优先级 |
|----------|------|----------|------|------------|
| [#468](https://github.com/moltis-org/moltis/pull/468) fix(plugins): Windows shell hooks | jmikedupont2 | 2026-03-23（⚠️ 5 个月前） | 待合并 | 🔴 高 — Windows 用户基础较广，长期未响应影响口碑 |
| [#1224](https://github.com/moltis-org/moltis/issues/1224) Slack 共享频道工具失效 | affanshahid | 2026-08-21 | 无 PR | 🟡 中 — 新建 Issue，建议维护者尽快确认复现步骤 |
| [#1222](https://github.com/moltis-org/moltis/pull/1222) Sandbox 镜像校验 | tsauvajon | 2026-08-20 | 待合并（测试待完成） | 🟡 中 — 安全相关，完成后应优先合并 |

---

**项目健康度评分：7.2/10**
- 活跃度：中（8 PR/24h，1 合并）
- 响应速度：良好（Bug PR 在同日内跟进）
- 积压风险：Windows PR #468 长期未处理
- 代码质量：全部为 `fix` 类型，无功能发散，聚焦稳定

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 | 2026-08-22

## 1. 今日速览
过去24小时 CoPaw 保持高活跃度，共更新 Issues 34 条（新开/活跃 19，关闭 15）、PRs 34 条（待合并 21，已合并/关闭 13），贡献与反馈节奏均衡。今日无正式 Release，但内部版本已 bump 至 `v2.1.1b2`。社区关注点集中分布在 MCP 连接恢复、长会话性能、历史数据膨胀及自动化审批体验优化等生产级场景，项目整体健康度良好，正处于 v2.1.x 系列的稳定性加固与体验打磨期。

## 2. 版本发布
今日未发布新版本。内部构建已更新至 `v2.1.1b2`（#7200）。需提示：`v2.1.1-beta.1` 存在已知回归，手动执行 `/compact` 在 `compact_threshold_ratio=0.9` 时会触发 Pydantic 校验失败（#7206），建议测试环境暂缓升级或等待补丁发布。

## 3. 项目进展
今日合并/关闭的 PR 主要聚焦基础设施可靠性、多租户部署与长会话性能：
- **#7205** [test/coverage]: 修复 Windows 集成测试覆盖率夜间读取为 0 的 CI 隐患，增加 fail-closed 防护。
- **#7112** [feat/hub]: 推出自托管多用户 Hub，支持本地与 Docker 运行时隔离的 App 实例，补齐企业级多租户能力。
- **#7176** [perf/console]: 优化长对话 Console 响应，消除流式更新与 Markdown 重渲染带来的重复计算与卡顿。
- **#7200** [chore]: 版本 bump 至 `v2.1.1b2`，为后续正式版发布做准备。
整体而言，项目在“可观测性、多用户支持、长会话体验”三条主线同步推进，工程成熟度持续提升。

## 4. 社区热点
- **#6524** [MCP 后端重启后客户端无法自动恢复，需执行 list mcp 才能重新连接

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-08-22

---

## 1. 今日速览

ZeroClaw 今日维持**高活跃度**：24小时内共产生 50 条 Issue 更新（新开/活跃 48 条、关闭 2 条）与 50 条 PR 更新（待合并 48 条、已合并/关闭 2 条），无新版本发布。今日社区关注焦点集中在**安全沙箱绕过**（Issues #10165、#10164）、**daemon 稳定性**（Issues #10230、#10121）以及 **工具结果截断行为**（Issues #10114–#10116）三个高优先级话题上，整体呈现安全与稳定性双重优化的趋势。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 核心变更 |
|----|------|----------|
| [#10174](https://github.com/zeroclaw-labs/zeroclaw/pull/10174) | CI/测试 | 在 GitHub Actions 原生 Linux 与 Windows runner 上验证已锁定的 release 工具链，为发布门禁提供证据基线 |
| [#10236](https://github.com/zeroclaw-labs/zeroclaw/pull/10236) | 桌面端 | 将 daemon 捕获日志绑定至 8 MiB 上限，通过隐藏 supervisor 进程在 Desktop 退出后继续维持日志限流 |

### 进展评估
今日合并的两条 PR 均聚焦于**发布管线可靠性**与**桌面端可观测性**，属于基础设施加固而非功能里程碑。项目整体在安全审查与稳定性打磨层面稳步前进，但无面向用户的显著功能落地。

---

## 4. 社区热点

### 最高评论 Issue

| Issue | 标题 | 评论数 | 风险等级 | 状态 |
|-------|------|--------|----------|------|
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | Independent delegate bypasses `block_high_risk_commands` | 3 | 🔴 High (S0) | OPEN |
| [#10074](https://github.com/zeroclaw-labs/zeroclaw/issues/10074) | SECURITY.md 记录的 CI job 已于 April 移除 | 3 | 🟡 Medium | ✅ CLOSED |
| [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | Interactive agent session caps context at 32k tokens | 3 | 🟡 Medium (S2) | OPEN |
| [#10066](https://github.com/zeroclaw-labs/zeroclaw/issues/10066) | SOP engine 在记录拒绝前先推进后续步骤 | 3 | 🔴 High (S1) | OPEN |
| [#10059](https://github.com/zeroclaw-labs/zeroclaw/issues/10059) | ZeroCode 文本输入支持 Option-Backspace 删词 | 3 | 🟢 Low | OPEN |

**热点分析：**
- **#10165** 与 **#10164** 共同揭示了 `security/sandbox` 模块在 delegate 路径上的策略评估不一致，是当前社区最关切的安全议题，直接影响多 agent 部署的隔离性。
- **#10068** 暴露了交互式 session 的 context 硬编码上限（32,000）与 `max_context_tokens` 配置脱钩，严重影响长上下文场景的用户体验。
- **#10066** 描述了 SOP 引擎的步骤执行顺序与状态记录之间存在竞态，可能导致工作流语义错误。

---

## 5. Bug 与稳定性

按严重程度排列：

| Issue | 严重度 | 摘要 | Fix PR |
|-------|--------|------|--------|
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | 🔴 S0 — 数据/安全风险 | Independent delegate 绕过 `block_high_risk_commands` | 暂无 |
| [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) | 🔴 S2 — 功能降级 | `block_high_risk_commands = false` 在主路径未生效 | 暂无 |
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | 🔴 S1 — 工作流阻断 | Daemon 启动/重载时 agent 初始化触发栈溢出 | 暂无 |
| [#10121](https://github.com/zeroclaw-labs/zeroclaw/issues/10121) | 🔴 S0 — 数据丢失风险 | Code/ACP turn 中途进程退出导致部分流式文本消失 | [#10197](https://github.com/zeroclaw-labs/zeroclaw/pull/10197) |
| [#10116](https://github.com/zeroclaw-labs/zeroclaw/issues/10116) | 🟡 S2 — 功能降级 | 超大 tool result 字节级中间截断 | 暂无 |
| [#10115](https://github.com/zeroclaw-labs/zeroclaw/issues/10115) | 🟡 S2 — 可观测性 | tool-result 截断对模型外部不可见 | 暂无 |
| [#10114](https://github.com/zeroclaw-labs/zeroclaw/issues/10114) | 🟡 S2 — 配置缺陷 | `max_tool_result_chars` 固定 50k，与模型 context 无关 | 暂无 |
| [#10061](https://github.com/zeroclaw-labs/zeroclaw/issues/10061) | 🔴 S1 — 工作流阻断 | Provider 拒绝图片污染后续 vision session | 暂无 |
| [#10058](https://github.com/zeroclaw-labs/zeroclaw/issues/10058) | 🟡 S2 — 交互缺陷 | ZeroCode 文件浏览器搜索模式忽略行/页导航 | 暂无 |
| [#10238](https://github.com/zeroclaw-labs/zeroclaw/issues/10238) | 🟡 S2 — 状态不同步 | Daemon 退出后 ZeroCode 仍显示 Connected | 暂无 |

**关键观察：**
- 今日 **10 条新 Open Bug**，其中 4 条涉及安全/沙箱策略（S0/S1），占比最高。
- **#10121** 已有 PR [#10197](https://github.com/zeroclaw-labs/zeroclaw/pull/10197)（persist interrupted turn progress）跟进，预计可修复。
- **#10114/10115/10116** 构成一个相关集群，反映 `max_tool_result_chars` 设计层面的系统性缺陷，需整体重构。

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求摘要 | 纳入概率评估 |
|----------|----------|--------------|
| [#10166](https://github.com/zeroclaw-labs/zeroclaw/issues/10166) + [#10239](https://github.com/zeroclaw-labs/zeroclaw/pull/10239) | `stream_mode` 默认值由 `off` 改为 `partial`；interrupt_on_new_message 支持任意 alias | 🟢 高 — 体验改善明确，PR #10239 已就绪 |
| [#10200](https://github.com/zeroclaw-labs/zeroclaw/issues/10200) + [#10201](https://github.com/zeroclaw-labs/zeroclaw/pull/10201) | WhatsApp Web 支持从配置设置 bot display name | 🟢 高 — PR #10201 已实现 |
| [#10073](https://github.com/zeroclaw-labs/zeroclaw/issues/10073) | 废弃 `StoragePolicy::Rolling`，合并至 Rotating 并扩展日志查询 API | 🟡 中 — 性能优化但涉及架构变更，需充分测试 |
| [#10140](https://github.com/zeroclaw-labs/zeroclaw/issues/10140) | iMessage 通道支持入站语音消息转录 | 🟡 中 — 与 Telegram/Slack 能力对齐，需求明确但实现范围较大 |
| [#10059](https://github.com/zeroclaw-labs/zeroclaw/issues/10059) | ZeroCode 文本输入支持 macOS Option-Backspace 删词 | 🟢 高 — 小改动、高感知度，标注为 good first issue |
| [#10173](https://github.com/zeroclaw-labs/zeroclaw/issues/10173) + [#10176](https://github.com/zeroclaw-labs/zeroclaw/pull/10176) | Docker Alpine 镜像强制非 root（UID:GID=65534:65534） | 🟢 高 — 安全合规项，PR #10176 已就绪 |

---

## 7. 用户反馈摘要

| 痛点/场景 | 来源 | 情绪倾向 |
|-----------|------|----------|
| 安全策略在多 agent 场景下不一致，delegate 绕过高风险命令阻断 | #10165, #10164 | 😡 不满 |
| 交互式 session context 被硬编码限制在 32k，与配置脱钩 | #10068 | 😤 挫败 |
| SOP 工作流步骤顺序错乱，导致执行语义错误 | #10066 | 😡 不满 |
| 工具结果截断不可见，用户与模型均无法感知数据丢失 | #10115, #10116 | 😕 困惑 |
| WhatsApp bot 每次重新绑定后 display name 丢失 | #10200 | 😤 不便 |
| ZeroCode Logs 面板文本不可选中复制，仅支持隐藏快捷键 | #10086, #10096 | 😕 低效 |
| iMessage 语音消息被静默丢弃，功能不对齐 | #10140 | 😤 失望 |
| Docker 镜像安全合规需强化非 root 约束 | #10074, #10173 | ✅ 认可进展 |

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建日期 | 风险 | 备注 |
|----------|------|----------|------|------|
| [#10073](https://github.com/zeroclaw-labs/zeroclaw/issues/10073) | 架构优化 | 2026-08-18 | 🔴 High | `StoragePolicy::Rolling` 性能退化问题，尚无 PR |
| [#10114](https://github.com/zeroclaw-labs/zeroclaw/issues/10114) | Bug + 设计缺陷 | 2026-08-19 | 🔴 High | `max_tool_result_chars` 与 context window 解耦，需整体重构 |
| [#10140](https://github.com/zeroclaw-labs/zeroclaw/issues/10140) | 功能请求 | 2026-08-19 | 🟡 Medium | iMessage 语音转录，无 assignee |
| [#9225](https://github.com/zeroclaw-labs/zeroclaw/pull/9225) | PR（待审） | 2026-07-21 | 🟢 Low | boundary-backed replay 测试用例，长期 pending review |
| [#8576](https://github.com/zeroclaw-labs/zeroclaw/pull/8576) | PR（待审） | 2026-07-01 | 🟡 Medium | OpenAI STT 凭据环境变量桥接，超 50 天未合并 |
| [#9707](https://github.com/zeroclaw-labs/zeroclaw/pull/9707) | PR（待审） | 2026-08-03 | 🟡 Medium | vision_model_provider 别名迁移，需作者进一步操作 |
| [#9645](https://github.com/zeroclaw-labs/zeroclaw/pull/9645) | PR（待审） | 2026-08-01 | 🔴 High | ZeroRouter 网关集成，大型 PR 需充分 review |

**维护者关注建议：**
- **#10073** 与 **#10114** 均为架构级问题，建议纳入近期技术债清理计划。
- **#8576** 创建已超过 50 天，作为安全相关功能请求应优先 review。
- **#9645** 为高优先级功能集成，需协调 reviewer 资源推进。

---

**报告生成时间：** 2026-08-22  
**数据来源：** [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw) GitHub API

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*