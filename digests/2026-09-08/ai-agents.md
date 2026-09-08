# OpenClaw 生态日报 2026-09-08

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-08 04:06 UTC

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



# OpenClaw 项目动态日报 — 2026-09-08

## 1. 今日速览

过去24小时项目活跃度极高：共处理 500 条 Issues（新开/活跃 265，关闭 235）及 500 条 PR（待合并 302，已合并/关闭 198），净增 PR 积压 104 条，表明贡献者参与度高但维护者 review 能力接近饱和。无新版本发布，但多个 P0/P1 级严重 bug 持续涌入，涉及多 agent 编排稳定性、SQLite 并发死锁、OAuth 刷新超时、Telegram/Signal 消息丢失等核心问题，项目稳定性处于警戒区间。修复工作主要集中在 gateway 启动恢复、session 状态管理、插件加载三个方向，整体向前推进但尚未形成系统性突破。

---

## 2. 版本发布

**今日无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#141815](https://github.com/openclaw/openclaw/pull/141815) | refactor | 模型目录投影重构，统一本地 reader 共享投影，减少 CLI/Gateway 重复逻辑 |
| [#141737](https://github.com/openclaw/openclaw/pull/141737) | refactor | 审批适配器重构，消除对 lazy-loaded channel runtime 的重复类型断言 |
| [#135970](https://github.com/openclaw/openclaw/issues/135970) | closed | Codex 插件 dist/extensions/codex 缺少 node_modules 问题已修复 |
| [#140497](https://github.com/openclaw/openclaw/issues/140497) | closed | Discord setup 接受 application ID 作为 bot token 的校验漏洞已修复 |

### 推进方向
- **状态管理稳定性**：[#112227](https://github.com/openclaw/openclaw/pull/112227) 解决 session group 并发创建丢失问题，直接回应在[#106362](https://github.com/openclaw/openclaw/issues/106362)中的用户痛点
- **认证体系加固**：[#141477](https://github.com/openclaw/openclaw/pull/141477) fence shared OAuth refresh 生成，缓解[#89278](https://github.com/openclaw/openclaw/issues/89278)报告的 10s 超时崩溃
- **插件加载修复**：[#129419](https://github.com/openclaw/openclaw/pull/129419) 替换 stale 源入口，解决多插件运行时顺序错乱

---

## 4. 社区热点

### 高热度 Issues（按评论数排序）

| Issue | 主题 | 评论 | 热度 |
|---|---|---|---|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent 完成结果静默丢失，无重试/通知/自动重启 | 26 | 🦞 diamond lobster |
| [#135111](https://github.com/openclaw/openclaw/issues/135111) | v2026.8.1 间歇性 "malformed JSON arguments" 回归 | 17 | 🐚 platinum hermit |
| [#126360](https://github.com/openclaw/openclaw/issues/126360) | 显式多 agent 所有权下 AgentSelectionRequiredError 日志洪水 | 16 | 🦪 silver shellfish |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | Session transcript projection 可持续写入下 livelock 阻塞主线程 | 16 | 🦞 diamond lobster |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/tool 子进程泄漏导致 zombie 累积和运行时退化 | 15 | 🦐 gold shrimp |

### 热点分析
- **多 agent 编排可靠性**是社区最关心的问题：[#44925](https://github.com/openclaw/openclaw/issues/44925)、[#43367](https://github.com/openclaw/openclaw/issues/43367)、[#137332](https://github.com/openclaw/openclaw/issues/137332) 均指向 subagent 生命周期管理和状态同步缺陷
- **升级破坏性**引发集中投诉：[#133984](https://github.com/openclaw/openclaw/issues/133984) 报告 2026.7.1-2 → 2026.8.1 升级后 gateway 无法启动，`doctor --fix` 自身也存在循环引用故障
- **Telegram 通道健壮性**持续薄弱：[#127229](https://github.com/openclaw/openclaw/issues/127229)、[#126246](https://github.com/openclaw/openclaw/issues/126246)、[#125764](https://github.com/openclaw/openclaw/issues/125764) 分别从 durable update tombstone、发送卡死、网络失败死信三个角度暴露问题

---

## 5. Bug 与稳定性

### P0 级（阻断性）

| Issue | 描述 | Fix PR |
|---|---|---|
| [#89278](https://github.com/openclaw/openclaw/issues/89278) | Codex OAuth 刷新成功但 cron/heartbeat 10s 超时失败 | [#141477](https://github.com/openclaw/openclaw/pull/141477) 已提交 |
| [#140497](https://github.com/openclaw/openclaw/issues/140497) | Discord setup 接受 application ID 作为 bot token，通道配置静默失败 | 已关闭 |

### P1 级（严重）

| Issue | 描述 | Fix PR |
|---|---|---|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent 完成结果静默丢失，无重试/通知/自动重启 | 无 |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | Session transcript projection livelock 阻塞主线程 tens of seconds | 无 |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | 同步 agent 持久化和 transcript 维护阻塞 Gateway 事件循环 | 部分修复（[#133925](https://github.com/openclaw/openclaw/pull/133925)、[#134062](https://github.com/openclaw/openclaw/pull/134062)） |
| [#137927](https://github.com/openclaw/openclaw/issues/137927) | 内部 context block `<<<BEGIN_OPENCLAW_INTERNAL_CONTEXT>>>` 泄露到 Telegram 可见消息 | 无 |
| [#136183](https://github.com/openclaw/openclaw/issues/136183) | ssh 命令执行 hang 后 SIGTERM（2026.8.1 回归） | 无 |
| [#117262](https://github.com/openclaw/openclaw/issues/117262) | SQLite 3 并发写句柄导致 ~33s 事件循环阻塞（DEF-61） | 无 |
| [#136311](https://github.com/openclaw/openclaw/issues/136311) | memory-core reindex 锁每次启动重新获取，19GB 孤立 temp DB 累积 | 无 |

### 回归问题

- [#135111](https://github.com/openclaw/openclaw/issues/135111) — v2026.8.1 引入 "malformed JSON arguments" 间歇失败
- [#136183](https://github.com/openclaw/openclaw/issues/136183) — ssh 执行 hang + SIGTERM（2026.8.1 回归）
- [#97616](https://github.com/openclaw/openclaw/issues/97616) — hook/tool 子进程泄漏（regression）

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求 | 纳入可能性 |
|---|---|---|
| [#96675](https://github.com/openclaw/openclaw/issues/96675) | Owner-signed 责任门控：助手输出/记忆/技能需显式用户确认才持久化 | 🟡 中等 — 安全增强方向，但需产品设计决策 |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | 在 session_status 暴露实际解析的 backend model（解决 LiteLLM 路由盲点） | 🟢 高 — PR [#51441](https://github.com/openclaw/openclaw/pull/51441) 已存在，P2 优先级 |
| [#60602](https://github.com/openclaw/openclaw/issues/60602) | Per-Agent Bedrock requestMetadata 注入以实现多 agent 成本分摊 | 🟡 中等 — 企业用户痛点明确，需产品决策 |
| [#112375](https://github.com/openclaw/openclaw/pull/112375) | Cron shell precheck gate：无工作时跳过 LLM 调用 | 🟢 高 — 已提交 PR，P2，降低闲置轮次的 API 成本 |
| [#131467](https://github.com/openclaw/openclaw/pull/131467) | update_goal tool 暴露 pause/resume 状态 | 🟢 高 — 对齐内部四态生命周期，PR 已就绪 |
| [#98084](https://github.com/openclaw/openclaw/issues/98084) | MiniMax M3 原生视频输入支持 | 🟡 中等 — reference branch only，依赖 MiniMax API 稳定性 |

---

## 7. 用户反馈摘要

### 痛点聚类

| 主题 | 典型反馈 | 来源 |
|---|---|---|
| **多 agent 编排不可靠** | "concurrent agents add/config overwrites, session-lock failures, and detached child work" — 并行编码批处理因配置覆盖和 session 锁失败而无法使用 | [#43367](https://github.com/openclaw/openclaw/issues/43367) |
| **升级风险高** | "2026.7.1-2 → 2026.8.1 left Gateway unstartable" — 升级后需 12 步手动修复，`doctor --fix` 自身存在循环引用 | [#133984](https://github.com/openclaw/openclaw/issues/133984)、[#134896](https://github.com/openclaw/openclaw/issues/134896) |
| **消息静默丢失** | Telegram durable outbound 卡在 `send_attempt_started`，重启后彻底丢失，无任何可见错误 | [#126246](https://github.com/openclaw/openclaw/issues/126246) |
| **内部状态泄露** | `<<<BEGIN_OPENCLAW_INTERNAL_CONTEXT>>>` 块作为 user 角色消息附加到每个模型请求，破坏对话完整性 | [#123265](https://github.com/openclaw/openclaw/issues/123265)、[#137927](https://github.com/openclaw/openclaw/issues/137927) |
| **性能退化** | SQLite 3 并发写句柄导致 33s 事件循环阻塞；memory-core reindex 锁每次启动重新获取，19GB 孤儿 temp DB 无法清理 | [#117262](https://github.com/openclaw/openclaw/issues/117262)、[#136311](https://github.com/openclaw/openclaw/issues/136311) |

### 满意度信号
- 部分用户认可 `openclaw doctor --fix` 的修复方向，但对自引用失败表示失望
- [#79077](https://github.com/openclaw/openclaw/issues/79077) Telegram bot-to-bot 和 guest-bot 模式支持请求获得 8 👍，显示社区对平台功能扩展的期待

---

## 8. 待处理积压

### 长期未响应 P0/P1 Issue

| Issue | 创建时间 | 状态 | 风险 |
|---|---|---|---|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 2026-03-13 | OPEN, diamond lobster | Subagent 完成静默丢失 — 核心可靠性问题，6 个月未修复 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 2026-06-29 | OPEN, gold shrimp | 子进程泄漏 zombie 累积 — regression，运行时退化风险 |
| [#117262](https://github.com/openclaw/openclaw/issues/117262) | 2026-08-01 | OPEN, diamond lobster | SQLite 33s 事件循环阻塞 — 生产环境可用性杀手 |
| [#136311](https://github.com/openclaw/openclaw/issues/136311) | 2026-09-02 | OPEN, platinum hermit | reindex 锁无法释放，19GB 孤儿 DB — 存储泄漏 |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | 2026-08-05 | OPEN, diamond lobster | 同步持久化阻塞 Gateway 事件循环 — 大规模场景致命 |

### 待合并 PR

| PR | 状态 | 说明 |
|---|---|---|
| [#141477](https://github.com/openclaw/openclaw/pull/141477) | 👀 ready for maintainer look | OAuth refresh fence 修复，解决 P0 [#89278](https://github.com/openclaw/openclaw/issues/89278) |
| [#112227](https://github.com/openclaw/openclaw/pull/112227) | 👀 ready for maintainer look | session group 并发丢失修复 |
| [#140339](https://github.com/openclaw/openclaw/pull/140339) | 👀 ready for maintainer look | 更新中断恢复机制，缓解升级风险 |

---

**项目健康度评估**：🟡 警戒 — 高活跃度背后是核心稳定性问题的集中爆发。多 agent 编排、SQLite 并发、消息持久化三个子系统存在系统性缺陷，且多个 P0 bug 积压超过 6 个月。建议维护团队优先处理 [#44925](https://github.com/openclaw/openclaw/issues/44925)、[#117262](https://github.com/openclaw/openclaw/issues/117262)、[#136311](https://github.com/openclaw/openclaw/issues/136311) 三个阻塞性问题的修复 PR。

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-09-08 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026年9月，个人AI助手与自主智能体开源生态呈现**"稳定性危机与架构进化并存"**的态势。OpenClaw、Hermes Agent、ZeroClaw、QwenPaw 四大主力项目同日涌入大量 P0/P1 级 Bug，集中在多 Agent 编排、上下文持久化、事件循环阻塞等核心路径，表明行业正从"功能驱动"转入"生产级可靠性验证"阶段。与此同时，NanoClaw 完成 durable host 整合、QwenPaw 推进插件化架构、Hermes 发布 v0.21.1，显示头部项目已在基础设施工事层面形成实质性突破。生态整体健康度分化明显：核心项目维护者 review 能力接近饱和（OpenClaw PR 积压 104 条、ZeroClaw 积压 44 条），而长尾项目（NullClaw、Moltis、ZeptoClaw）活跃度显著下降，生态呈现"马太效应"加剧。

---

## 2. 各项目活跃度对比

| 项目 | 新/活跃 Issues | 关闭 Issues | 新 PR | 合并 PR | 待合并 PR | 版本发布 | 健康度 |
|---|---|---|---|---|---|---|---|
| **OpenClaw** | 265 | 235 | 500 | 198 | 302 | — | 🟡 警戒 |
| **ZeroClaw** | 31 | 6 | 50 | 6 | 44 | — | 🟡 快速迭代/积压 |
| **Hermes Agent** | 44 | 6 | 50 | 1 | 49 | v0.21.1 | 🟢 良好 |
| **QwenPaw** | — | — | 36 | 28 | — | — | 🟢 稳定迭代 |
| **NanoClaw** | 2 | — | 30 | 17 | 11 | — | 🟢 良好 |
| **LobsterAI** | 0 | — | 7 | 5 | 2 | — | 🟢 良好 |
| **NanoBot** | 2 | — | 23 | 10 | 13 | — | 🟢 良好 |
| **IronClaw** | 1 | — | 4 | 0 | 4 | — | 🟢 良好 |
| **PicoClaw** | 1 | — | 5 | 0 | 5 | — | 🟡 PR合并停滞 |
| **Moltis** | 0 | — | 1 | 0 | 1 | — | 🟡 平稳 |
| **NullClaw** | 0 | — | 1 | 0 | 1 | — | 🟡 低维护 |
| **ZeptoClaw** | 0 | — | 0 | 0 | 0 | — | ⚪ 无活动 |

---

## 3. OpenClaw 在生态中的定位

**定位：生态基准参照物，多 Agent 编排与渠道集成的事实标准**

| 维度 | OpenClaw | 同类对比 |
|---|---|---|
| **技术路线** | 多 Agent 编排 + 全渠道接入（Telegram/Signal/Discord/Slack）+ Gateway 架构 | NanoBot 侧重单 agent 个人助手；Hermes 侧重桌面端多 profile；ZeroClaw 侧重 Rust 运行时 |
| **社区规模** | Issues/PR 绝对数量最高（500/500），贡献者基数最大 | Hermes（50/50）、ZeroClaw（37/50）次之；NanoBot/QwenPaw（30-40/30-36）中等 |
| **核心优势** | 渠道覆盖最广、插件生态最成熟（Codex/Bedrock/OpenCode 等）、多 agent 编排能力领先 | NanoClaw 在 durable host 持久化架构上领先；ZeroClaw 在 Rust 运行时可观测性上领先 |
| **当前短板** | P0 bug 积压严重（subagent 静默丢失、SQLite 33s 阻塞、消息静默丢失均超 6 个月未修复），维护者 review 饱和 | 其他项目在对应维度尚未暴露同等规模的生产级缺陷 |

**结论**：OpenClaw 是生态中**用户基数最大、场景覆盖最广**的参考实现，但当前稳定性危机使其"功能先行"路线受到质疑。NanoClaw 的 durable host 整合和 ZeroClaw 的可观测性设计，可能代表下一阶段的基础设施演进方向。

---

## 4. 共同关注的技术方向

### 4.1 多 Agent 编排可靠性
| 项目 | 具体诉求 |
|---|---|
| OpenClaw | subagent 完成结果静默丢失（#44925，26评论，6个月未修复）；并发 agent 配置覆盖与 session 锁失败（#43367） |
| Hermes Agent | multi-profile 场景下 approval.respond SessionOwnerResolutionError（#105481）；session lease 泄漏导致永久锁定（#104691） |
| NanoClaw | Agent-to-Agent 消息发送者身份保真（#3718）；A2A 通信失败回报告知（#3719） |
| ZeroClaw | ACP 会话切换后失败 turn 消失（#9333）；预算超限后 Code turn 进度丢失（#10659） |

### 4.2 上下文/记忆持久化
| 项目 | 具体诉求 |
|---|---|
| OpenClaw | session transcript projection livelock 阻塞主线程（#115908）；SQLite 3 并发写导致 33s 事件循环阻塞（#117262） |
| Hermes Agent | Projects 重构破坏 folder→session→sidebar 工作流（#53004，P1）；provider 400 误判为 context_overflow 导致破坏性压缩循环（#52261） |
| QwenPaw | 模型回复已持久化但后续请求丢失（#7579，6评论）；RetryChatModel 硬编码 32768 上下文回退（#7576） |
| ZeroClaw | 进程退出时 partial turn 数据丢失（#10121）；token 预算截断逻辑缺陷（#10702） |
| NanoClaw | conversations/archives 无限增长无保留策略（#3735）；transcript rotation 对长活容器失效（#3732） |

### 4.3 消息通道健壮性
| 项目 | 具体诉求 |
|---|---|
| OpenClaw | Telegram/Signal 消息静默丢失（#127229/#126246/#125764）；Discord setup 校验漏洞（#140497） |
| Hermes Agent | Bot Group Chats 跨设备持续运行（#97681，27评论） |
| QwenPaw | MCP 工具参数数字字符串序列化错误（#6839）；工具返回 image/PDF 触发 400 错误（#7597） |
| ZeroClaw | Slack WebSocket TLS 证书信任不一致（#10712 已修复）；WhatsApp 语音永不被转写（#10688 已修复） |
| NanoBot | 飞书渠道多轮回复碎片化，期望整合为单条流式卡片（#5567） |

### 4.4 升级/迁移风险
| 项目 | 具体诉求 |
|---|---|
| OpenClaw | 2026.7.1-2 → 2026.8.1 升级后 Gateway 无法启动，`doctor --fix` 自身循环引用（#133984） |
| Hermes Agent | v0.21.0 Projects 重构破坏性工作流（#53004） |
| QwenPaw | v2.2.0 移除主工作目录路径手动输入功能引发用户不满（#7588/#7601） |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|---|---|---|---|
| **OpenClaw** | 全渠道多 Agent 编排 + 插件生态 | 企业/重度用户，需要多渠道接入与复杂工作流 | Node.js + Gateway 架构，插件化 provider 体系 |
| **Hermes Agent** | 桌面端多 profile 隔离 + TUI | 个人开发者/技术用户，重视多任务隔离 | Electron + Ink TUI，native Gemini tool calls 支持 |
| **NanoClaw** | durable host 持久化 + fleet 部署 | 生产环境部署用户，重视可重启一致性 | Rust，durable host 完整链路（协调状态持久化/wake seam/reconcile queue） |
| **ZeroClaw** | 可观测性 + 安全加固 + Webhook | 基础设施敏感用户，重视日志与审计 | Rust tokio 运行时，size:XL PR 集中在日志旋转/安全限制 |
| **QwenPaw** | 插件化架构 + 多语言 + UI 现代化 | 中文用户/企业用户，重视本地化与插件生态 | Node.js，记忆后端插件化（OpenViking/ADBPG），Console UI 重设计 |
| **NanoBot** | WebUI 体验 + Provider 扩展 + 垂直场景 | 个人助手用户，重视 WebUI 交互 | Node.js，AnySearch/OpenCode provider，飞书/Slack/Discord 渠道 |
| **LobsterAI** | 内置浏览器 + Cowork 任务管理 | Windows 用户，重视浏览器自动化 | Electron，task 优先排序与网格分组 |
| **PicoClaw** | 嵌入式/边缘设备 + QQ 频道 | 边缘计算用户，Orange Pi 等 aarch64 设备 | Go，IRCv3/gbr 协议，opencode-go provider |
| **IronClaw** | WebUI 命令菜单细节打磨 | WebUI 重度用户 | 前端交互优化为主 |
| **Moltis** | cron 调度 | 定时任务用户 | Rust，active_hours 解析修复 |
| **NullClaw** | 无显著特色 | — | 低维护频率 |

---

## 6. 社区热度与成熟度分层

### 🔴 快速迭代期（高活跃度 + 高问题密度）
- **OpenClaw**：500 PR/500 Issues，但 P0 bug 积压严重，维护者 review 饱和，处于"功能扩张→稳定性补课"的阵痛期
- **ZeroClaw**：50 PR/37 Issues，44 PR 待合并，S1 bug 集中爆发（daemon 栈溢出、ACP 数据丢失），快速迭代但质量保障不足
- **Hermes Agent**：50 PR/50 Issues，v0.21.1 发布，session 管理+多 profile 隔离快速迭代，Projects 重构回归需修复

### 🟢 稳定维护期（中等活跃度 + 修复为主）
- **QwenPaw**：36 PR/34 Issues，28 条关闭，上下文管理+插件化架构稳步推进，响应速度较好
- **NanoClaw**：30 PR/2 Issues，17 条合并，durable host 整合完成，存储管理缺陷新暴露
- **NanoBot**：23 PR/2 Issues，10 条合并，稳定性修复+WebUI 优化，健康度良好

### 🟡 低维护/ niche 期（低活跃度）
- **LobsterAI**：7 PR，浏览器修复+任务管理改进，维护节奏稳定
- **IronClaw**：4 PR，WebUI 细节打磨
- **PicoClaw**：5 PR（0 合并），PR 审查停滞风险
- **Moltis**：1 PR，小项目 cron 修复
- **NullClaw**：1 Dependabot PR，滞留 85 天
- **ZeptoClaw**：无活动

---

## 7. 值得关注的趋势信号

### 信号 1：从"功能堆砌"转向"生产级可靠性"
**现象**：OpenClaw 的 subagent 静默丢失（#44925）、SQLite 33s 阻塞（#117262）、ZeroClaw 的 daemon 栈溢出（#10230）、QwenPaw 的上下文丢失（#7579）均指向**多 Agent 场景下的状态一致性**成为行业共性难题。
**参考价值**：新入局者应优先解决 session 持久化、事件循环非阻塞化、消息确认机制，而非单纯扩展功能。

### 信号 2：Durable Host 架构成为基础设施新标准
**现象**：NanoClaw 完成 durable host 完整链路整合（#3653），涵盖协调状态持久化、wake seam、reconcile queue、claim fencing。OpenClaw 的 session group 并发丢失（#112227）和 Hermes 的 zombie session lease（#104691）也指向同类问题。
**参考价值**：可重启一致性（restart coherence）是生产部署的必备能力，建议关注 NanoClaw 的实现路径。

### 信号 3：上下文管理从"压缩策略"转向"可观测+可配置"
**现象**：QwenPaw #7576 硬编码 32768 回退、Hermes #52261 provider 400 误判为 context_overflow、ZeroClaw #10702 token 预算截断缺陷、OpenClaw #115908 transcript projection livelock。
**参考价值**：上下文窗口管理需要暴露实际解析的 backend model（Hermes #51441 PR 已存在），并支持 per-agent cost attribution（OpenClaw #60602）。

### 信号 4：插件化架构加速分化
**现象**：QwenPaw 推进记忆后端插件化（OpenV

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报
**日期：2026-09-08 | 数据周期：过去 24 小时**

---

## 1. 今日速览

过去 24 小时 NanoBot 项目保持**高活跃度**。共产生 23 条 PR（10 条已合并/关闭，13 条待合并），显示核心维护者正处于密集的 bug 修复与性能优化周期。今日 Issues 新增 2 条，其中一条为飞书渠道多轮消息整合的用户体验诉求，另一条来自无人零售场景的潜在合作方，反映出项目在垂直场景的探索正在扩展。无新版本发布，但多项 P1/P2 级修复已合并，整体项目稳定性持续改善。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的 PR（10 条）

| PR | 类型 | 摘要 |
|---|---|---|
| [#5688](https://github.com/HKUDS/nanobot/pull/5688) | bug fix | 修复空闲压缩后 provider 状态未失效，导致 replay 历史错误的内存问题 |
| [#5689](https://github.com/HKUDS/nanobot/pull/5689) | bug fix | 修复 WebUI 服务器时钟滞后导致"Working timer"跳动异常的显示问题 |
| [#5690](https://github.com/HKUDS/nanobot/pull/5690) | docs | 统一个人代理安装文档与 Quick Start 路径，减少用户困惑 |
| [#5676](https://github.com/HKUDS/nanobot/pull/5676) | feature | 新增 CLI Desktop 独立安装与目标选择，支持 `attach-only` 模式 |
| [#5691](https://github.com/HKUDS/nanobot/pull/5691) | bug fix | 修复 WebUI 多行美元符数学公式渲染错误（KaTeX 报错） |
| [#5687](https://github.com/HKUDS/nanobot/pull/5687) | docs | 补充 Gateway 健康检查文档，明确 200/503 状态及 WebSocket 就绪条件 |
| [#5607](https://github.com/HKUDS/nanobot/pull/5607) | feature | 新增 AnySearch 网络搜索 Provider，支持匿名配额无需 API Key |
| [#5602](https://github.com/HKUDS/nanobot/pull/5602) | feature | WebUI 新增可选的 turn 完成提示音（`notificationSound` 偏好设置） |
| [#5662](https://github.com/HKUDS/nanobot/pull/5662) | feature | OpenCode 提供商新增 `x-opencode-session` header，保障 prompt-cache 优化 |

**总体评估**：今日合并的 PR 覆盖 **WebUI 体验修复、内存状态一致性、文档统一、搜索能力扩展**四大方向，项目工程健壮性有明显的提升。

---

## 4. 社区热点

### 活跃 Issue

**[#5567](https://github.com/HKUDS/nanobot/issues/5567) — 飞书渠道多轮回复整合为单条流式卡片**
- 评论 5 条，创建于 2026-08-27，今日仍有更新
- **诉求分析**：飞书渠道的 agent 回复当前分裂为工具提示、进度、最终回复多条消息，用户期望保持"用户发一条 → agent 回一条"的对应关系，体验类似 Discord/Slack 的流式卡片。这是 IM 渠道集成中典型的"消息粒度过细"问题，反映出用户对流畅对话体验的强烈需求。

**[#5693](https://github.com/HKUDS/nanobot/issues/5693) — 无人零售/IoT 轻量级部署场景建议**
- 由"AI 军团·笔芯秘书"自动提交，今日新建
- **诉求分析**：落朵无人零售生态希望将 NanoBot 作为边缘侧 self-hosted person 方案，诉求包括轻量部署、中文文档和场景适配。这代表 NanoBot 从通用个人助手向**垂直行业解决方案**延伸的潜在机会，值得关注是否有贡献者跟进。

### 高关注度 PR

**[#5580](https://github.com/HKUDS/nanobot/pull/5580) — 将 session 持久化移出事件循环（P1 + conflict）**
- 标签含 `performance`、`conflict`，创建于 2026-08-28
- **分析**：session 存储阻塞事件循环是架构级性能问题，PR 提出通过 `nanobot.session.io.call` dispatcher 异步化。`conflict` 标签表明需解决合并冲突，是需维护者优先处理的性能瓶颈修复。

**[#5630](https://github.com/HKUDS/nanobot/pull/5630) — Dream memory 文件大小限制回归修复**
- 标记 `regression`，指 PR #5622 修复 system-prompt 重复 bug 时意外移除了 `MEMORY.md` 等文件的大小上限
- **分析**：回归修复及时，防止 Dream 记忆文件无限增长影响性能，体现项目对历史修复的持续追踪。

---

## 5. Bug 与稳定性

### 已合并的 Bug 修复

| PR | 严重程度 | 描述 |
|---|---|---|
| [#5688](https://github.com/HKUDS/nanobot/pull/5688) | 🔴 高 | 内存压缩后 provider 状态未失效，导致 replay 使用过期历史 |
| [#5689](https://github.com/HKUDS/nanobot/pull/5689) | 🟡 中 | WebUI 时钟不一致导致 working timer 异常跳动 |
| [#5691](https://github.com/HKUDS/nanobot/pull/5691) | 🟡 中 | 多行数学公式渲染为 KaTeX 红色错误 |

### 待合并的 Bug/回归修复

| PR | 严重程度 | 描述 |
|---|---|---|
| [#5694](https://github.com/HKUDS/nanobot/pull/5694) | 🔴 高 | 压缩触发器使用 summary checkpoint，防止大请求残留 |
| [#5695](https://github.com/HKUDS/nanobot/pull/5695) | 🔴 高 | 工具结果在 replay 中保持稳定，防止重放截断不一致 |
| [#5686](https://github.com/HKUDS/nanobot/pull/5686) | 🔴 高 | Cron 定时器重设延迟修复，避免 `CancelledError` 导致任务丢失 |
| [#5682](https://github.com/HKUDS/nanobot/pull/5682) | 🟡 中 | `ExecTool` 相对 `working_dir` 解析错误，应基于 workspace 而非进程 cwd |
| [#5675](https://github.com/HKUDS/nanobot/pull/5675) | 🟡 中 | 模型超时后允许 fallback 切换，修复 runner deadline 导致整个 chain 被取消的回归 |
| [#5692](https://github.com/HKUDS/nanobot/pull/5692) | 🟡 中 | `find_files`/`grep` 递归 glob 匹配 `**` 行为不正确 |

**稳定性评估**：今日有 **6 项 P2 级 bug fix 待合并**，覆盖 cron 调度、工具执行、模型 fallback、压缩机制等核心路径，合并后项目整体稳定性将显著提升。

---

## 6. 功能请求与路线图信号

| 诉求 | 关联 PR | 纳入下一版本概率 |
|---|---|---|
| WebUI 完成提示音 | [#5602](https://github.com/HKUDS/nanobot/pull/5602) ✅ 已合并 / [#5547](https://github.com/HKUDS/nanobot/pull/5547) 🔄 重叠 PR | 已合入 |
| 新增 AnySearch Provider | [#5607](https://github.com/HKUDS/nanobot/pull/5607) ✅ 已合并 | 已合入 |
| Dream memory 文件尺寸限制 | [#5630](https://github.com/HKUDS/nanobot/pull/5630) 🔄 待合并 | 高（regression 修复） |
| 递归 glob 文件搜索 | [#5692](https://github.com/HKUDS/nanobot/pull/5692) 🔄 待合并 | 高 |
| 无人零售/边缘 IoT 场景支持 | [#5693](https://github.com/HKUDS/nanobot/issues/5693) 📝 仅 Issue | 低（需明确需求与贡献） |
| 飞书多渠道消息整合 | [#5567](https://github.com/HKUDS/nanobot/issues/5567) 📝 仅 Issue | 中（需评估架构改动范围） |
| macOS Seatbelt Sandbox | [#5628](https://github.com/HKUDS/nanobot/pull/5628) 🔄 待合并 | 中（macOS 特定，opt-in） |

**路线图信号**：项目当前重心在**稳定性修复**（cron、压缩、replay 一致性）和**WebUI 体验优化**（提示音、公式渲染、时钟一致性），同时持续扩展 Provider 生态（AnySearch、OpenCode header）。

---

## 7. 用户反馈摘要

- **IM 渠道体验**：[#5567](https://github.com/HKUDS/nanobot/issues/5567) 反映飞书用户希望减少消息碎片化，将工具调用/进度/最终回复整合为单条流式卡片，提升对话连贯性。类似诉求在 Slack/Discord 渠道可能有相同需求。
- **WebUI 时钟一致性**：[#5689](https://github.com/HKUDS/nanobot/pull/5689) 修复的问题源于服务器与浏览器时钟不同步，用户在实际使用中观察到 timer 跳变，影响对 agent 响应速度的感知。
- **数学公式渲染**：[#5691](https://github.com/HKUDS/nanobot/pull/5691) 的多行公式 bug 影响使用 LaTeX 表达专业内容的用户，修复后 KaTeX 渲染将更稳定。
- **边缘场景探索**：[#5693](https://github.com/HKUDS/nanobot/issues/5693) 来自无人零售领域的潜在合作意向，希望获得轻量级自托管方案，目前尚无明确技术响应。
- **文档体验**：[#5690](https://github.com/HKUDS/nanobot/pull/5690) 和 [#5687](https://github.com/HKUDS/nanobot/pull/5687) 的合并反映用户对安装指南和 Gateway 健康检查文档的清晰性有持续需求。

---

## 8. 待处理积压

| PR/Issue | 创建时间 | 状态 | 建议关注 |
|---|---|---|---|
| [#5580](https://github.com/HKUDS/nanobot/pull/5580) | 2026-08-28 | 🔄 待合并（含 conflict） | P1 性能问题，需优先解决冲突并合并 |
| [#5693](https://github.com/HKUDS/nanobot/issues/5693) | 2026-09-08 | 📝 新 Issue，无响应 | 无人零售场景需求，需评估是否纳入路线图或寻求贡献者 |
| [#5567](https://github.com/HKUDS/nanobot/issues/5567) | 2026-08-27 | 📝 5 评论，无 PR | 飞书消息整合需求持续，建议维护者评估技术方案或认领 |
| [#5611](https://github.com/HKUDS/nanobot/pull/5611) | 2026-08-30 | 🔄 待合并 | 推理回放大小限制，影响 token 效率，建议推进 |
| [#5694](https://github.com/HKUDS/nanobot/pull/5694) | 2026-09-08 | 🔄 待合并 | 压缩触发器修复，与 #5688 为同一问题的不同维度，建议配套合并 |

---

**项目健康度评级：🟢 良好**
- 合并速率：10 PR/天（高）
- Bug 修复占比：~43%（稳定维护期特征）
- 社区贡献：多元（内部维护者 + 外部贡献者）
- 待处理阻塞：1 个 P1 conflict，建议优先处理

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-09-08** | 数据来源：NousResearch/hermes-agent GitHub

---

## 1. 今日速览

Hermes Agent 项目今日保持高活跃度：过去24小时内共更新 **50 条 Issues**（新开/活跃 44 条，关闭 6 条）和 **50 条 PRs**（待合并 49 条，已合并 1 条），并发布了 **v0.21.1** patch 版本。项目整体处于快速迭代期，核心工作集中在 session 状态管理修复、多 profile 隔离改进、以及桌面端稳定性加固。今日关闭的 PR #105539 标志着群聊整理功能已进入最终阶段，多个 P1 级 bug 已有对应 fix PR 提交。项目健康度良好，社区参与度活跃。

---

## 2. 版本发布

### v0.21.1 (v2026.9.7)
- **发布日期**: 2026-09-07
- **性质**: Patch release
- **说明**: 该版本打包了自 v0.21.0 以来 main 分支的所有提交，适用于 tagged deployment 和下游消费者。
- **Commit**: `6178e9f4eed8d99f4fc550add939d58c7bed6206`
- **破坏性变更**: 无（patch 版本）
- **迁移注意**: 直接从 v0.21.0 升级即可，建议检查自定义 provider 配置是否与 v0.21.x session 管理变更兼容。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 摘要 | 状态 |
|---|---|---|---|
| [#105539](https://github.com/NousResearch/hermes-agent/pull/105539) | feat(desktop) | 群聊可按用户自定义分组整理到 roster sections | ✅ Closed |
| [#105545](https://github.com/NousResearch/hermes-agent/pull/105545) | fix | Native Gemini tool calls 支持 nullable 和 union 参数 | 🔄 Open |
| [#105546](https://github.com/NousResearch/hermes-agent/pull/105546) | fix | 修复 streaming scrubbers 中 Unicode offset 保留问题 | 🔄 Open |
| [#105542](https://github.com/NousResearch/hermes-agent/pull/105542) | fix(gateway) | 修复 profile reload 后共享 MCP visibility 丢失问题 | 🔄 Open |
| [#105481](https://github.com/NousResearch/hermes-agent/pull/105481) | fix(desktop) | 修复 multi-profile 场景下 approval.respond 的 SessionOwnerResolutionError | 🔄 Open |
| [#105540](https://github.com/NousResearch/hermes-agent/pull/105540) | fix(sessions) | 从已终止 lane 回收 resident session leases，修复 #104691 | 🔄 Open |
| [#105530](https://github.com/NousResearch/hermes-agent/pull/105530) | fix(agent) | 修复 display-only rewrites 后 usage anchor 丢失问题 | 🔄 Open |

**项目推进评估**: 今日有 7 个高质量 fix PR 进入 review 阶段，覆盖 session 状态、MCP 隔离、Unicode 处理等核心路径。群聊分组功能（#105539）已合并，桌面端用户体验进一步完善。

---

## 4. 社区热点

### 高讨论度 Issues

| Issue | 标题 | 评论数 | 标签 | 链接 |
|---|---|---|---|---|
| #97681 | Bot Group Chats should keep working after Desktop closes | 27 | feature, gateway, desktop, sessions | [链接](https://github.com/NousResearch/hermes-agent/issues/97681) |
| #53004 | Projects paradigm (#49037) broke folder → session → sidebar flow | 14 | bug, P1, desktop, sessions | [链接](https://github.com/NousResearch/hermes-agent/issues/53004) |
| #90663 | TUI (Ink) lowercases Shift+letter in prompt composer on Ghostty | 12 | bug, TUI, P1 | [链接](https://github.com/NousResearch/hermes-agent/issues/90663) |
| #86146 | Bug: Highlights (model switching across profiles) | 10 | bug, P2, desktop, profiles | [链接](https://github.com/NousResearch/hermes-agent/issues/86146) |
| #52261 | Provider memory/resource 400s misclassified as context_overflow | 9 | bug, agent, P1, compression | [链接](https://github.com/NousResearch/hermes-agent/issues/52261) |

**热点分析**:
- **#97681** (27评论): 用户强烈希望实现"跨设备无缝接力"的群聊体验，Bot 可部署在不同机器但保持会话连续性。这是一个架构级功能请求，涉及 gateway 分布式状态管理。
- **#53004** (14评论, 1👍): v0.21.0 的"first-class projects"重构引入了破坏性变更，导致现有工作流中断。这是典型的向后兼容性痛点，需要官方明确迁移路径或回滚。
- **#90663** (12评论): TUI/Ink 在 Ghostty 终端的输入处理 bug，影响专业用户群体。

---

## 5. Bug 与稳定性

### 按严重程度排列

#### 🔴 P0/P1 - 高优先级

| Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|
| [#104691](https://github.com/NousResearch/hermes-agent/issues/104691) | Zombie session lease 导致 session 永久锁定 ("already has a live owner") | Open | ✅ [#105540](https://github.com/NousResearch/hermes-agent/pull/105540) |
| [#52261](https://github.com/NousResearch/hermes-agent/issues/52261) | 本地推理 provider 400 错误被误判为 context_overflow，导致破坏性压缩循环 | Open | 待修复 |
| [#103786](https://github.com/NousResearch/hermes-agent/issues/103786) | Windows gateway retry 循环阻塞 Electron 主线程导致 AppHangB1 | Open | 待修复 |
| [#90663](https://github.com/NousResearch/hermes-agent/issues/90663) | TUI Ink 在 Ghostty 中 Shift+字母被转小写 | ✅ Closed | - |
| [#105541](https://github.com/NousResearch/hermes-agent/issues/105541) | Gateway turn cancellation 等待 stream flush 可被吞没 | Open | 待修复 |

#### 🟡 P2 - 中优先级

| Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|
| [#98524](https://github.com/NousResearch/hermes-agent/issues/98524) | Assistant 消息在 transcript 中渲染两次（DB 仅一行） | Open | 待修复 |
| [#91130](https://github.com/NousResearch/hermes-agent/issues/91130) | `drive_preview` 在 fractional-DPR 屏幕上点击偏移 ~20% | Open | 待修复 |
| [#101856](https://github.com/NousResearch/hermes-agent/issues/101856) | Browser preview tabs 未按 session/profile 隔离 | Open | 待修复 |
| [#99286](https://github.com/NousResearch/hermes-agent/issues/99286) | 自定义 provider 显示一半实际 context window（131072 vs 262144） | Open | 待修复 |
| [#80625](https://github.com/NousResearch/hermes-agent/issues/80625) | SSH remote backend 在 Fish shell 下失败 | Open | 待修复 |
| [#105497](https://github.com/NousResearch/hermes-agent/issues/105497) | Desktop barge-in transcript 被 stale `busy` closure 静默丢弃 | Open | 待修复 |
| [#105471](https://github.com/NousResearch/hermes-agent/issues/105471) | `_send_with_retry` 在 timeout 后错误发送 plain-text fallback | Open | 待修复 |

#### 🟢 P3 - 低优先级

| Issue | 描述 | 状态 |
|---|---|---|
| [#26665](https://github.com/NousResearch/hermes-agent/issues/26665) | Desktop 语言设置在重启后重置为英文 | Open |
| [#105465](https://github.com/NousResearch/hermes-agent/issues/105465) | `hermes update` 后 UI 语言重置（中文→英文） | Open |
| [#58083](https://github.com/NousResearch/hermes-agent/issues/58083) | Windows ACP session/new 启动卡死 | Open |
| [#9971](https://github.com/NousResearch/hermes-agent/issues/9971) | 微信 TTS 音频需要 OGG→SILK 转码 | Open |

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 优先级 | 纳入下版本可能性 |
|---|---|---|---|
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | Bot Group Chats 跨设备持续运行 | P2 | ⭐⭐⭐ 高（架构级功能，需规划） |
| [#44926](https://github.com/NousResearch/hermes-agent/issues/44926) | 可配置 interim assistant messages 速率限制 | P3 | ⭐⭐ 中（已有多平台需求） |
| [#105543](https://github.com/NousResearch/hermes-agent/pull/105543) | 群聊按用户自定义分组整理 | P3 | ✅ 已实现 |
| [#97510](https://github.com/NousResearch/hermes-agent/pull/97510) | Session model audit/reset CLI + cron list model pins | P3 | ⭐⭐ 中（CLI 可见性增强） |
| [#105503](https://github.com/NousResearch/hermes-agent/pull/105503) | 捷克语 i18n 翻译 | P3 | ⭐⭐⭐ 高（社区贡献） |

**路线图信号**: 项目正在加强 **session 状态管理** 和 **多 profile 隔离** 能力，同时扩展 **桌面端组织功能**（群聊分组）。i18n 社区贡献活跃，捷克语已提交。

---

## 7. 用户反馈摘要

### 痛点
1. **Session 状态持久化不可靠**: 多个用户报告 session lease 泄漏、zombie session 锁定问题，导致会话中断后无法恢复。
2. **多 Profile 隔离不完整**: Browser tabs、MCP 工具、approval 机制在 multi-profile 场景下存在跨会话污染。
3. **更新后配置丢失**: Windows 用户报告 `hermes update` 后 UI 语言重置、自定义路径配置冲突。
4. **本地推理兼容性**: 本地 MLX/oMLX provider 的错误分类逻辑导致破坏性自动压缩循环。
5. **Projects 重构回归**: v0.21.0 的"first-class projects"破坏了原有 folder → session 工作流。

### 满意点
- 群聊分组功能（#105543）获得正面反馈，用户希望更多组织化工具。
- TUI Ink 快速修复显示团队响应效率高。

### 使用场景
- **分布式 Bot 部署**: 用户希望 Bot 可运行在不同设备（笔记本/服务器/VPS），群聊保持连续。
- **多租户 Gateway**: 企业用户运行 per-tenant gateway 实例，需要严格的 profile 隔离。
- **本地优先**: 资源受限用户运行本地模型，对 context window 准确性敏感。

---

## 8. 待处理积压

### 需维护者关注

| Issue/PR | 积压时长 | 风险等级 | 建议行动 |
|---|---|---|---|
| [#53004](https://github.com/NousResearch/hermes-agent/issues/53004) | ~75 天 | 🔴 高 | Projects 重构回归影响大量现有用户，需官方回应或回滚 |
| [#52261](https://github.com/NousResearch/hermes-agent/issues/52261) | ~75 天 | 🔴 高 | 本地推理用户的关键 bug，误判导致数据丢失 |
| [#58083](https://github.com/NousResearch/hermes-agent/issues/58083) | ~97 天 | 🟡 中 | Windows ACP 启动卡死，影响 Agent 用户 |
| [#9971](https://github.com/NousResearch/hermes-agent/issues/9971) | ~146 天 | 🟡 中 | 微信 TTS 音讯格式问题，国内用户痛点 |
| [#44926](https://github.com/NousResearch/hermes-agent/issues/44926) | ~88 天 | 🟢 低 | 速率限制功能请求，可纳入 backlog |

### 需 Review 的 PR
- [#105545](https://github.com/NousResearch/hermes-agent/pull/105545) - Gemini nullable 参数修复
- [#105542](https://github.com/NousResearch/hermes-agent/pull/105542) - MCP visibility 修复
- [#105481](https://github.com/NousResearch/hermes-agent/pull/105481) - Approval session owner 修复
- [#105540](https://github.com/NousResearch/hermes-agent/pull/105540) - Session lease 回收（修复 P1 bug #104691）

---

**报告生成时间**: 2026-09-08 | **分析师**: AI Agent开源项目分析师

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-09-08

---

## 1. 今日速览

PicoClaw 今日整体活跃度中等，5 个 PR 待合并但尚无一条合并，项目处于"等待审查"状态。核心动态集中在功能扩展（新增 opencode-go 和 Keenable 搜索 provider）与协议完善（IRCv3 多行消息、gbr 配对协议）。社区同时暴露了一个 QQ 频道鉴权失败的兼容性问题（botgo + resty 版本冲突），属于上游依赖层面的回归风险。整体项目健康度良好，但 PR 合并进度偏慢，建议维护者关注审查积压。

---

## 2. 版本发布

无新版本发布。最新已知版本为 `0.3.1`（nightly）。

---

## 3. 项目进展

今日 **0 条 PR 合并**，所有 5 个 PR 均处于开放/待审查状态：

| PR | 主题 | 状态 |
|---|---|---|
| [#3371](https://github.com/sipeed/picoclaw/pull/3371) | 新增 opencode-go provider，支持 `x-opencode-session` 头部 | OPEN |
| [#3344](https://github.com/sipeed/picoclaw/pull/3344) | 支持 gbr/1 协议的远程 Agent 手机配对 | OPEN [stale] |
| [#3354](https://github.com/sipeed/picoclaw/pull/3354) | IRCv3 多行消息拼装支持 | OPEN [stale] |
| [#3353](https://github.com/sipeed/picoclaw/pull/3353) | 修复工具反馈动画无限循环问题 | OPEN [stale] |
| [#3370](https://github.com/sipeed/picoclaw/pull/3370) | 新增 Keenable web_search provider | OPEN |

**评估：** 3 个 PR（#3344、#3354、#3353）已标记 `[stale]`，超过 10 天未获维护者响应，存在被自动关闭的风险。项目在"修复小问题"层面有进展，但在"合并推进"层面处于停滞。

---

## 4. 社区热点

### 🔥 Issue #3365 — QQ 频道 401 鉴权失败
[链接](https://github.com/sipeed/picoclaw/issues/3365)

- **热度：** 1 条评论，1 个 👍
- **根因定位：** `botgo v0.2.1` 与 `resty v2.17.1` 之间的参数序列化兼容性问题
- **用户诉求：** 在 Orange Pi 3B（aarch64）上运行 QQ 频道机器人时，Authorization 头部格式错误导致鉴权失败
- **分析：** 该 Issue 属于上游依赖版本冲突，非 PicoClaw 自身逻辑缺陷，但影响主流使用场景。需关注 botgo 是否有兼容 resty v2.17+ 的 patch 版本，或 PicoClaw 是否需要在 go.mod 中 pin resty 版本

---

## 5. Bug 与稳定性

| 优先级 | 问题 | PR | 状态 |
|---|---|---|---|
| 🟡 中 | 工具反馈动画未清理，导致消息被无限编辑 | [#3353](https://github.com/sipeed/picoclaw/pull/3353) | OPEN [stale] — 已有 fix PR |
| 🔴 高 | QQ 频道 401 鉴权失败（botgo + resty 版本冲突） | [#3365](https://github.com/sipeed/picoclaw/issues/3365) | OPEN — 暂无 fix PR |

**稳定性评估：** 已知 2 个问题，1 个已有修复方案但 stale，1 个依赖上游。总体崩溃/回归风险可控。

---

## 6. 功能请求与路线图信号

| 需求 | 关联 PR | 纳入下一版本可能性 |
|---|---|---|
| 支持 OpenCode Go 作为独立 provider，自动路由到三个 endpoint 族 | [#3371](https://github.com/sipeed/picoclaw/pull/3371) | ⭐⭐⭐ 高 — 明确关闭 #3369，需求文档完整 |
| 支持 Keenable 公共网页搜索（无需 API Key） | [#3370](https://github.com/sipeed/picoclaw/pull/3370) | ⭐⭐ 中 — 零配置门槛，但为第三方 provider |
| IRCv3 多行消息拼装 | [#3354](https://github.com/sipeed/picoclaw/pull/3354) | ⭐⭐ 中 — 协议标准扩展，社区有需求 |
| gbr/1 协议手机配对 | [#3344](https://github.com/sipeed/picoclaw/pull/3344) | ⭐ 低 — 小众协议，已标 stale |

---

## 7. 用户反馈摘要

- **使用场景：** PicoClaw 在嵌入式/边缘设备（Orange Pi 3B）上运行，用户依赖 QQ 频道作为主要接入渠道
- **痛点 1：** 上游依赖（botgo/resty）版本兼容性未对齐，导致鉴权链断裂 — 用户期望 PicoClaw 能主动 pin 兼容版本
- **痛点 2：** 工具反馈动画缺少生命周期上限，长时间运行的会话会触发无限编辑 — 用户体验受损
- **满意度信号：** opencode-go 和 Keenable 的 provider 扩展由社区主动贡献，说明项目生态活跃，用户愿意为扩展功能提交 PR

---

## 8. 待处理积压

| 类型 | 编号 | 创建时间 | 天数 | 风险 |
|---|---|---|---|---|
| PR (stale) | [#3344](https://github.com/sipeed/picoclaw/pull/3344) | 2026-08-23 | 16 | 高 — 可能被自动关闭 |
| PR (stale) | [#3354](https://github.com/sipeed/picoclaw/pull/3354) | 2026-08-31 | 8 | 中 |
| PR (stale) | [#3353](https://github.com/sipeed/picoclaw/pull/3353) | 2026-08-31 | 8 | 中 |
| Issue | [#3365](https://github.com/sipeed/picoclaw/issues/3365) | 2026-09-04 | 4 | 中 — 无 fix PR |

**建议：** 维护者优先审查 [#3371](https://github.com/sipeed/picoclaw/pull/3371) 和 [#3370](https://github.com/sipeed/picoclaw/pull/3370)（均为新提交、非 stale），并尽快决定 #3344/#3353/#3354 是合并还是关闭，避免 stale 机制自动清理有效贡献。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：2026-09-08** | 数据来源：GitHub (nanocoai/nanoclaw)

---

## 1. 今日速览

NanoClaw 在过去24小时内保持**高度活跃**，共处理 30 个贡献（2 Issues + 28 PRs），其中 **17 个 PR 已合并/关闭**，11 个仍处于待合并状态。项目今日主要聚焦于**持久化基础设施整合**（durable host 完整链路合入）和**系统稳定性修复**（测试 race condition、Bun 安装重试、CI gate 机制）。同时，两个存储管理相关的 Issue 浮出水面，暴露出长期被忽视的 retention 策略缺陷。整体项目健康度良好，贡献节奏稳定，核心维护者（gavrielc）主导的基础设施改进正在收尾。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 作者 | 类型 | 说明 |
|----|------|------|------|
| [#3653](https://github.com/nanocoai/nanoclaw/pull/3653) | gavrielc | chore/core | **Durable Host 完整整合**：将 #3508–#3528 整个 durable host 链路一次性合入，涵盖协调状态持久化、wake seam、reconcile queue、restart-honest delivery、claim fencing 等关键基础设施。这是项目架构层面的重要里程碑。 |
| [#3518](https://github.com/nanocoai/nanoclaw/pull/3518) | gavrielc | fix/core | **Approvals 模块重启存活**：通过 `GatewayProvider` seam 实现 row-keyed 的 approvals 持久化，使审批状态不再随进程重启而丢失。 |
| [#3517](https://github.com/nanocoai/nanoclaw/pull/3517) | gavrielc | feat/db | **Shadow-write 协调状态**：所有易失性协调事实双写至持久化行，为 durable host 提供数据基础。 |
| [#3661](https://github.com/nanocoai/nanoclaw/pull/3661) | gavrielc | fix/container | **Bun 安装重试机制**：Dockerfile 中的 Bun 安装从单次失败改为自动重试，提升镜像构建可靠性。 |
| [#3400](https://github.com/nanocoai/nanoclaw/pull/3400) | Koshkoshinsk | fix/channels | **修复 Slack typing status 残留**：reply 投递后正确清除 typing 指示器，避免状态过期问题。 |
| [#3737](https://github.com/nanocoai/nanoclaw/pull/3737) | gavrielc | fix/core | **修复 PostgreSQL 测试 race condition**：调整 nested-continuation 测试的 watchdog 超时逻辑。 |
| [#3739](https://github.com/nanocoai/nanoclaw/pull/3739) | gavrielc | ci | **CI gate check 与 Docker Hub 5xx 容错**：增强 CI 工作流健壮性。 |

**进展评估**：今日合并的 PR 以基础设施和系统稳定性修复为主，durable host 整合（#3653）是最大的里程碑——标志着项目从"内存状态依赖"向"可重启一致"架构演进完成。17 个 PR 的合并量表明核心维护团队正在高效推进技术债清理。

---

## 4. 社区热点

### 今日新增 Issues（2 条）

**[#3735: conversations/archives 无限增长，无保留策略](https://github.com/nanocoai/nanoclaw/issues/3735)**
- 作者：TO-maschenborn | 创建：2026-09-07
- **核心问题**：`archiveTranscriptFile()` 每次 compaction 写入 `groups/<folder>/conversations/` 的 markdown 归档，但从不删除或轮换。在 fleet 部署场景下，目录大小随 agent group 生命周期持续增长。
- **用户诉求**：需要 retention policy、rotation 和容量上限机制。

**[#3732: Transcript rotation 对长活容器中的 tasks 失效](https://github.com/nanocoai/nanoclaw/issues/3732)**
- 作者：TO-maschenborn | 创建：2026-09-07
- **核心问题**：`maybeRotateContinuation()` 仅在 `runPollLoop()` 中调用（每次容器启动一次）。若 task recurrence 短于主机 30 分钟 idle 阈值，容器将永久存活，rotation 检查永远不会触发。
- **用户诉求**：需要独立于容器生命周期的 transcript 轮换机制。

**热点分析**：两条 Issue 来自同一作者（TO-maschenborn），均指向**存储管理的系统性缺陷**。这反映出 fleet 规模用户在实际生产环境中遇到的真实痛点——当前设计假设是短生命周期容器，但实际部署中持续运行的 task 越来越多，导致存储增长和 transcript 累积失控。这些问题需要架构层面的修复，而非简单的参数调整。

### 高关注度待合并 PR

| PR | 说明 | 关注度 |
|----|------|--------|
| [#3743](https://github.com/nanocoai/nanoclaw/pull/3743) | AgentMail 邮件渠道适配器——解决 DNS/MX 所有权难题 | 新功能，扩展渠道覆盖 |
| [#3741](https://github.com/nanocoai/nanoclaw/pull/3741) | `--fresh-session` 支持无状态 scheduled tasks——解决重复任务上下文膨胀问题 | 直接回应用户反馈 |
| [#3718](https://github.com/nanocoai/nanoclaw/pull/3718) | Agent-to-Agent 消息发送者身份保真 | 安全/互操作性改进 |
| [#3719](https://github.com/nanocoai/nanoclaw/pull/3719) | A2A 通信失败回报告知发送方 | 可观测性增强 |

---

## 5. Bug 与稳定性

| 问题 | 状态 | 严重度 | 说明 |
|------|------|--------|------|
| [#3735](https://github.com/nanocoai/nanoclaw/issues/3735) conversations/archives 无限增长 | OPEN | 中 | 生产环境 fleet 部署下存储持续膨胀，无自动清理机制 |
| [#3732](https://github.com/nanocoai/nanoclaw/issues/3732) Transcript rotation 对长活容器失效 | OPEN | 中 | 设计假设与现网部署模式存在偏差 |
| [#3690](https://github.com/nanocoai/nanoclaw/issues/3690) → [#3742](https://github.com/nanocoai/nanoclaw/pull/3742) `--ro` 标志为 no-op，无法创建读写挂载 | 修复中 (PR #3742) | 低 | CLI 功能缺陷，已有 PR 待合并 |
| [#3737](https://github.com/nanocoai/nanoclaw/pull/3737) [已合] PostgreSQL 测试 race condition | ✅ 已修复 | 低 | 测试稳定性修复，已合入 |
| [#3400](https://github.com/nanocoai/nanoclaw/pull/3400) [已合] Slack typing status 残留 | ✅ 已修复 | 低 | 用户体验问题，已合入 |

**稳定性评估**：今日无崩溃或严重回归报告。两个新增 Issue 属于设计缺陷类问题（非代码 bug），但影响生产环境的可维护性。修复难度中等，需要引入 retention/rotation 配置和独立的调度触发机制。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | PR 状态 | 纳入下版可能性 |
|------|------|---------|---------------|
| **邮件渠道支持** | PR #3743 | 待合并 | **高**——解决社区长期缺失的渠道类型，且通过 AgentMail 避免了 DNS/MX 复杂性 |
| **无状态定时任务** | PR #3741 + Issue #3732 | 待合并 | **高**——#3741 的 `--fresh-session` 直接缓解 #3732 的上下文膨胀问题，两者存在互补关系 |
| **OpenCode provider skill** | PR #3733 | 待合并 | **中**——扩展 provider 生态，作为安装恢复和调试工具 |
| **手机配对远程代理** | PR #3494 | 待合并 | **中**——扩展设备类型支持，但使用场景相对小众 |
| **Community cell 浏览器集成** | PR #3729 | 待合并 | **中**——完善 Web 门户体验 |

**路线图信号**：项目当前重点在于**基础设施夯实**（durable host 已完成）和**渠道生态扩展**（AgentMail、OpenCode）。存储管理（retention/rotation）尚未有对应 PR，两个 Issue 需要维护者主动响应或等待社区贡献。

---

## 7. 用户反馈摘要

### 真实痛点

1. **存储膨胀失控**（#3735）：Fleet 部署用户报告 `conversations/` 目录无限增长，缺乏 retention 和 rotation 机制。这是生产环境中最紧迫的可操作性问题。

2. **Transcript 轮转失效**（#3732）：持续运行的 task 无法触发 transcript rotation，导致会话历史和存储双重累积。用户明确指出这是设计假设（30 分钟 idle 阈值）与实际部署模式（高频 recurrence task 保持容器长活）不匹配所致。

3. **定时任务上下文膨胀成本**（#3741 用户反馈）：用户报告一个 nightly job 在单周内上下文增长 15%，因为每次执行都重新读取所有历史对话。`--fresh-session` 选项直接解决此问题。

4. **CLI 挂载选项不完整**（#3690 / #3742）：`--ro` 标志当前是 no-op，无法正确表达读写挂载意图，影响容器化部署的灵活性。

### 用户满意度

- **积极反馈**：Durable host 整合（#3653）被描述为"complete durable-host line, integrated"，反映了用户对系统可靠性的重视。
- **待改进**：存储管理、transcript 轮转等运维层面的功能缺失已被多次提及，但尚未有正式 PR 响应。

---

## 8. 待处理积压

| 项目 | 类型 | 创建时间 | 状态 | 建议 |
|------|------|----------|------|------|
| [#3735](https://github.com/nanocoai/nanoclaw/issues/3735) | Issue | 2026-09-07 | OPEN | 需维护者回应，建议纳入 storage management 特性路线 |
| [#3732](https://github.com/nanocoai/nanoclaw/issues/3732) | Issue | 2026-09-07 | OPEN | 与 #3741 存在关联，可考虑在 PR review 中评估兼容性 |
| [#3494](https://github.com/nanocoai/nanoclaw/pull/3494) | PR | 2026-08-23 | OPEN (16天) | Build Remote Agent 手机配对功能，等待 review |
| [#3729](https://github.com/nanocoai/nanoclaw/pull/3729) | PR | 2026-09-06 | OPEN | Community cell 集成，待合并 |
| [#3718](https://github.com/nanocoai/nanoclaw/pull/3718) | PR | 2026-09-04 | OPEN | A2A 身份保真修复，待 review |

**维护者关注建议**：
1. **#3735 和 #3732** 来自同一用户且同一天提交，建议在回复中建立关联，并评估是否需要统一的 storage management 特性设计。
2. **#3494** 已开放 16 天，建议优先完成 review 或给出明确反馈。
3. 当前有 **11 个待合并 PR**，建议维护者评估优先级，批量处理以避免积压。

---

**日报生成时间**：2026-09-08 | **分析师**：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 — 2026-09-08

---

## 1. 今日速览

NullClaw 项目在过去 24 小时内整体活跃度**较低**。无新 Issues 产生，无新版本发布。仅有一条由 Dependabot 自动提交的依赖更新 PR（#956）处于待合并状态，核心维护活动有限。项目当前处于稳定维护期，无重大功能迭代或紧急问题处理。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

| 类型 | PR / Issue | 状态 | 说明 |
|------|-----------|------|------|
| PR | [#956](https://github.com/nullclaw/nullclaw/pull/956) | 🔵 待合并 | 依赖更新：alpine 3.23 → 3.24 |

- 本次更新为 **Dependabot 自动维护**，仅涉及 Docker 镜像基础操作系统升级，不涉及业务功能变更。
- 项目核心代码库今日**无实质性进展**，维护重心仍停留在基础设施依赖层面。

---

## 4. 社区热点

今日无社区讨论热点。无新增 Issue 或高评论量 PR。

---

## 5. Bug 与稳定性

**无新 Bug 报告。**

项目今日未收到任何崩溃、回归或稳定性相关反馈。

---

## 6. 功能请求与路线图信号

**今日无新功能请求。**

当前无可见的路线图信号输入，建议关注后续社区 Issue 中的功能提议趋势。

---

## 7. 用户反馈摘要

**今日无用户反馈。**

---

## 8. 待处理积压

| 类型 | ID | 标题 | 创建时间 | 最后更新 | 备注 |
|------|-----|------|---------|---------|------|
| PR | [#956](https://github.com/nullclaw/nullclaw/pull/956) | `ci(deps): bump alpine from 3.23 to 3.24` | 2026-06-15 | 2026-09-07 | **已滞留约 2 个月**，等待维护者合并 |

### ⚠️ 维护者关注建议

- **PR #956** 自创建至今已超过 **85 天**仍未合并，建议尽快 Review 并处理。依赖更新虽小，但长时间滞留可能影响 CI 环境的依赖安全性。
- 项目整体 Issue/PR 积压量较低，无紧急积压项，但可考虑建立更主动的依赖更新响应机制。

---

## 项目健康度评估

| 维度 | 评分 | 说明 |
|------|------|------|
| 活跃度 | 🟡 低 | 24h 内仅 1 条自动 PR，无人工活跃 |
| 响应速度 | 🟡 待观察 | Dependabot PR 滞留超 2 个月 |
| 稳定性 | 🟢 良好 | 无 Bug 报告，无崩溃反馈 |
| 社区参与 | 🔴 低 | 无新 Issue，无讨论热度 |
| 整体健康 | 🟡 一般 | 项目处于低维护频率的稳定期，建议维护者关注依赖更新响应效率 |

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目日报 — 2026-09-08

---

## 1. 今日速览

IronClaw 在过去 24 小时内保持中等活跃度，共 1 条新 Issue 和 4 条待合并 PR。所有 PR 均由核心贡献者 `italic-jinxin` 提交，聚焦于 WebUI 侧边栏命令菜单与结果卡片的交互优化。未发现新版本发布或阻塞性 Bug。项目整体维护节奏稳定，WebUI 细节体验正处于集中打磨期。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 合并或关闭。4 条 PR 均处于 OPEN 状态，处于待审查/待合并阶段，暂无实质性进度推进。当前 WebUI 修复系列（#8068–#8071）已形成一组内聚的改进，待合并后将一次性提升命令菜单的可用性。

| PR | 标题 | 状态 |
|----|------|------|
| [#8071](https://github.com/nearai/ironclaw/pull/8071) | fix(webui): preserve command result card height | OPEN |
| [#8070](https://github.com/nearai/ironclaw/pull/8070) | fix(webui): align slash-command metadata | OPEN |
| [#8069](https://github.com/nearai/ironclaw/pull/8069) | fix(webui): add dismiss actions to command result cards | OPEN |
| [#8068](https://github.com/nearai/ironclaw/pull/8068) | fix(webui): keep the active slash command visible | OPEN |

---

## 4. 社区热点

- **Issue #8081** — [Daily ironclaw failure taxonomy — 2026-09-07](https://github.com/nearai/ironclaw/issues/8081)  
  作者自动生成的 daily failure 汇总帖，聚焦 officeqa 基准测试中 DeepSeek-V4-Flash 的数值错误。评论 0、👍 0，属于例行分析帖，暂无社区讨论热度。

---

## 5. Bug 与稳定性

今日无新增 Bug 报告或崩溃反馈。

4 条待合并 PR 均标注 **risk: low**，属于 WebUI 交互层面的修复，不涉及核心推理链路稳定性：

- **#8071**：修复 command-result 卡片在 flex 列中被压缩变矮的问题
- **#8068**：修复键盘导航时激活命令选项滚出视口的回归
- **#8069**：为命令结果卡片添加可访问的关闭操作（非 Bug，属功能补齐）

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 说明 |
|------|------|------|
| 命令菜单键盘导航可见性 | #8068 | 用户反馈导航时激活项易滚出视口，PR 已覆盖 |
| 命令结果卡片可关闭 | #8069 | 用户希望主动消除临时结果消息，PR 已实现 |
| 命令菜单排版对齐 | #8070 | 标题与描述列对齐，窄屏堆叠+截断 |
| 结果卡片高度保持 | #8071 | 防止紧凑布局挤压卡片内容 |

以上 4 项均为 WebUI 体验类改进，已以 PR 形式就绪。预计合并后将纳入下一次版本发布的 Changelog。

---

## 7. 用户反馈摘要

- **Issue #8081** 无评论，未见具体用户痛点表达。
- 4 条 PR 均由核心贡献者主动发起，非用户直接提交，间接反映出维护团队对 WebUI 命令交互细节的关注，而非用户大规模反馈驱动。

---

## 8. 待处理积压

- **无明确积压 Issue/PR**。4 条 PR 均已创建 4 天（09-04），等待审查合并，属于正常 Code Review 周期内。
- Issue #8081 为自动化生成的日报汇总帖，无需人工处理。

---

**项目健康度评估：🟢 良好** — 活跃度中等，无阻塞性问题，WebUI 修复系列即将交付，整体维护节奏健康。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报 — 2026-09-08

---

## 1. 今日速览

过去24小时 LobsterAI 项目活跃度集中在 **Pull Request 领域**，共处理 7 条 PR，其中 5 条已合并/关闭，2 条仍待合并，整体推进效率较高。Issues 板块今日无新增或更新，社区讨论热度相对平静。未发布新版本，代码层面的修复与功能迭代持续积累中，项目保持稳定迭代节奏。

---

## 2. 版本发布

今日无新版本发布，暂不需要迁移注意事项。

---

## 3. 项目进展

今日合并/关闭的 **5 条 PR** 覆盖了多个关键模块，项目实质性推进体现在以下方向：

| PR | 状态 | 模块 | 核心变更 |
|----|------|------|----------|
| [#2620](https://github.com/netease-youdao/LobsterAI/pull/2620) | ✅ 已关闭 | Platform / Installer | Windows NSIS 安装包 CJK 字体渲染修复 |
| [#2623](https://github.com/netease-youdao/LobsterAI/pull/2623) | ✅ 已关闭 | Renderer / Main / Cowork | 任务优先排序与网格分组折叠功能上线 |
| [#2621](https://github.com/netease-youdao/LobsterAI/pull/2621) | ✅ 已关闭 | Main / OpenClaw | 修复内置浏览器 `scrollIntoView` 元素引用崩溃 |
| [#2622](https://github.com/netease-youdao/LobsterAI/pull/2622) | ✅ 已关闭 | Main / OpenClaw | 网关子进程 Node 模式继承修复 |
| [#2617](https://github.com/netease-youdao/LobsterAI/pull/2617) | ✅ 已关闭 | Renderer / Artifacts | 内置浏览器登录体验与标签页控制优化 |

**整体评估：** 今日 PR 集中修复了浏览器子系统的稳定性问题（#2621、#2622、#2617），同时上线了 Cowork 任务管理的核心交互改进（#2623），并改善了 Windows 用户的安装体验（#2620）。项目健康度良好，修复与功能迭代并行推进。

---

## 4. 社区热点

今日无新增 Issues，社区讨论热度主要分布在以下长期 PR 上：

- **[PR #1277](https://github.com/netease-youdao/LobsterAI/pull/1277)** — Dependabot 维护的 Electron 依赖更新（40.2.1 → 44.2.0），已打开超过 5 个月仍为 **OPEN** 状态，涉及 Electron 主框架及构建工具的大版本跃迁，潜在兼容性风险较高，建议维护者优先评估合并或关闭。
- **[PR #1067](https://github.com/netease-youdao/LobsterAI/pull/1067)** — 标记为 **stale**，修复 OpenClaw 心跳任务自动创建无用 Cowork 会话的问题，已存在约 5 个月未合并，社区需求明确但优先级可能偏低。

---

## 5. Bug 与稳定性

| 优先级 | 问题描述 | 涉及 PR | 状态 |
|--------|----------|---------|------|
| 🔴 高 | 内置浏览器 `scrollIntoView` 传入 snapshot element ref 时触发 `TypeError: Uncaught`，错误信息被吞没，残留错误横幅 | [#2621](https://github.com/netease-youdao/LobsterAI/pull/2621) | ✅ 已修复 |
| 🔴 高 | 网关子进程 Node 模式未正确继承，可能导致运行时环境异常 | [#2622](https://github.com/netease-youdao/LobsterAI/pull/2622) | ✅ 已修复 |
| 🟡 中 | Windows NSIS 安装包 CJK 字体渲染锯齿，DPI 放大下体验差 | [#2620](https://github.com/netease-youdao/LobsterAI/pull/2620) | ✅ 已修复 |
| 🟡 中 | 内置浏览器登录反馈不可关闭、标签页切换体验不佳 | [#2617](https://github.com/netease-youdao/LobsterAI/pull/2617) | ✅ 已修复 |

> 今日所有已知 Bug 均已通过 PR 修复并关闭，**稳定性指标良好**。

---

## 6. 功能请求与路线图信号

- **任务分组与排序（[#2623](https://github.com/netease-youdao/LobsterAI/pull/2623)）** — 本次合并的功能直接响应了用户对任务管理效率的需求，包括分组折叠、独立分页、滚动位置恢复等交互改进，反映出项目正朝 **更精细化的 Cowork 体验** 方向演进。
- **OpenClaw 会话管理优化（[#1067](https://github.com/netease-youdao/LobsterAI/pull/1067)）** — 用户期望减少自动创建的冗余会话，说明 `heartbeat` 机制的副作用管理是长期改进方向。
- **Electron 大版本升级（[#1277](https://github.com/netease-youdao/LobsterAI/pull/1277)）** — 40 → 44 的大跨越若合并，将显著提升安全性和新 API 支持，可能影响路线图中的版本发布时间表，需提前规划兼容性测试。

---

## 7. 用户反馈摘要

今日 Issues 无新增，从已关闭 PR 的改动范围可反推用户核心诉求：

- **浏览器体验** 是用户痛点集中区：元素引用崩溃、登录反馈干扰、标签页管理不便等问题已被多次修复，说明内置浏览器是高频使用场景，用户对稳定性和交互细节有较高要求。
- **Windows 用户** 对安装包的视觉质量敏感（CJK 字体渲染问题），属于基础体验层面，修复后有助于提升新用户第一印象。
- **任务管理** 方面，用户期望更灵活的分组和排序能力，PR #2623 的上线表明该需求已进入产品迭代。

---

## 8. 待处理积压

| PR | 状态 | 创建时间 | 风险/说明 |
|----|------|----------|-----------|
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | 🟢 OPEN | 2026-04-02 | Electron 40→44 升级，已开放 5 个月，版本跨度大，合并前需充分回归测试 |
| [#1067](https://github.com/netease-youdao/LobsterAI/pull/1067) | 🟡 OPEN [stale] | 2026-03-30 | 移除心跳自动创建冗余会话，社区诉求明确，建议 review 后合并或关闭 |

> **建议维护者关注：** PR #1277 的 Electron 大版本升级是当前积压中最具影响力的变更，建议优先评估合并策略；PR #1067 虽为 stale 但修复内容明确且影响面小，可快速处理以清理积压。

---

*报告生成时间：2026-09-08 | 数据来源：[LobsterAI GitHub](https://github.com/netease-youdao/LobsterAI)*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-09-08

---

## 1. 今日速览

Moltis 今日整体活跃度较低，过去24小时内无新 Issue 提交，亦无新版本发布。唯一动态为 PR **#1262**，目前处于待合并状态，主要修复了 `cron` 模块中 `active_hours` 配置项解析异常问题。项目维护节奏平稳，无紧急事件或高优先级问题需即时响应。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

**PR #1262** — `fix(cron): treat active_hours end="24:00" as end-of-day`
- **状态**：待合并
- **作者**：atirna
- **创建/更新**：2026-09-07

该 PR 修复了一个配置解析 Bug：当 `active_hours` 的 `end` 字段设置为 `"24:00"`（即全天有效）时，`chrono` 的 `%H` 格式拒绝解析小时值 24，导致解析失败并触发了 fail-open 逻辑，使得 `is_within_active_hours` 始终返回 `true`，进而使 cron 调度逻辑在任何小时都判定为"活跃状态"。修复后，`end="24:00"` 将被正确识别为"全天有效"语义，确保 `24 * 60` 分钟级时间窗口的行为符合文档预期。

> 🔗 [PR #1262](https://github.com/moltis-org/moltis/pull/1262)

---

## 4. 社区热点

今日无高热度讨论。唯一活跃条目为上述 PR #1262，目前评论数为 0，👍 数为 0，社区关注度尚在等待合并 review 阶段。

> 🔗 [PR #1262](https://github.com/moltis-org/moltis/pull/1262)

---

## 5. Bug 与稳定性

| 严重级别 | 问题描述 | 状态 | 修复 PR |
|----------|----------|------|---------|
| **中** | `cron active_hours end="24:00"` 解析失败，导致时间窗口判断恒为活跃，可能引发非预期调度行为 | 已有 fix PR 待合并 | [#1262](https://github.com/moltis-org/moltis/pull/1262) |

> 注：该 Bug 影响 `is_within_active_hours` 函数的逻辑正确性，在用户使用默认时间窗口配置（`start="08:00"`, `end="24:00"`）时会触发。建议合并后关注回归测试覆盖情况。

---

## 6. 功能请求与路线图信号

今日无新功能需求提交，无明确的路线图信号。

---

## 7. 用户反馈摘要

今日无新 Issue 评论，无新增用户反馈可供提炼。

---

## 8. 待处理积压

| 类型 | 条目 | 描述 | 链接 |
|------|------|------|------|
| PR | #1262 | cron 模块 Bug 修复，待合并 | [PR #1262](https://github.com/moltis-org/moltis/pull/1262) |

> 建议维护者关注 PR #1262 的 review 进度，该修复影响 cron 调度的核心逻辑正确性，合并后可消除 `24:00` 时间窗口的已知异常行为。

---

**项目健康度评估**：🟡 平稳 — 今日无高危风险，无新 Issue 涌入，核心维护焦点在于跟进 PR #1262 的合并流程。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw / QwenPaw 项目动态日报
**日期：2026-09-08**

---

## 1. 今日速览

过去24小时内，QwenPaw 项目共处理 70 条活动记录（34 Issues + 36 PRs），其中 28 条得到关闭/合并处理，活动效率良好。核心焦点集中在：**上下文管理 bug 修复**（#7576、#6541）、**UI 体验优化**（#7502、#7499）以及**长期记忆后端扩展**（#7613 OpenViking、#7616 ADBPG/PowerContext 迁移）。项目整体处于稳定迭代期，无新版本发布，但已有多个重要 PR 待合并，预计下一版本将包含显著的架构调整和功能增强。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#6936](https://github.com/agentscope-ai/QwenPaw/issues/6936) | fix | 修复 MCP 工具调用时将数字字符串参数错误序列化为 JSON 数字的问题（关联 Issue #6839） |
| [#7499](https://github.com/agentscope-ai/QwenPaw/issues/7499) | fix | 统一侧边栏导航图标为 Spark 细线风格，修复视觉不一致（关联 Issue #7376） |
| [#7530](https://github.com/agentscope-ai/QwenPaw/issues/7530) | test | Console 单元测试新增 245 个用例，语句覆盖率提升 5.02pp |

### 今日关闭的 Issue（关键修复）

- **[#6541](https://github.com/agentscope-ai/QwenPaw/issues/6541)** — 滚动上下文压缩后 `[context compressed]` 块使用 `role=user` 导致 DeepSeek API 报错 → **已修复**
- **[#6885](https://github.com/agentscope-ai/QwenPaw/issues/6885)** — 中文 IME compositionEnd 导致 Console UI 崩溃 → **已修复**
- **[#7604](https://github.com/agentscope-ai/QwenPaw/issues/7604)** — LLM 流空闲超时硬编码 30s 不可配置 → **已修复**
- **[#7588](https://github.com/agentscope-ai/QwenPaw/issues/7588)** — 恢复 v2.1.0 的主工作目录路径手动输入功能 → **已恢复**
- **[#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469)** — ReMe 后台嵌入/索引任务静默失败 → **已修复**

---

## 4. 社区热点

### 讨论最活跃的 Issue（评论数 ≥ 4）

| Issue | 状态 | 评论数 | 核心议题 |
|---|---|---|---|
| [#7579](https://github.com/agentscope-ai/QwenPaw/issues/7579) | OPEN | 6 | 模型回复已持久化但在后续请求中丢失，"模型看不到自己刚说的话" |
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | CLOSED | 5 | ReMe 后台嵌入任务因依赖未启动而失败，且失败静默 |
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | OPEN | 5 | `RetryChatModel` 硬编码 32768 上下文回退导致所有模型报告 CONTEXT_UNFIT |
| [#7589](https://github.com/agentscope-ai/QwenPaw/issues/7589) | OPEN | 4 | Heartbeat cron session 反馈循环导致消息重复堆积，Agent 无响应约2小时 |
| [#7597](https://github.com/agentscope-ai/QwenPaw/issues/7597) | OPEN | 4 | 工具返回的 image/PDF 二进制以裸 base64 发送触发 400 错误 |
| [#6541](https://github.com/agentscope-ai/QwenPaw/issues/6541) | CLOSED | 4 | 滚动压缩策略中 `[context compressed]` 块 role 设置错误 |
| [#6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) | CLOSED | 4 | MCP 工具参数数字字符串被错误序列化为 JSON 数字 |

**热点分析：**
- **上下文管理**是当前社区最大痛点：#7579 和 #7576 均指向上下文窗口/压缩逻辑缺陷，#7579 更是涉及 Agent 记忆持久化的核心问题。
- **工具调用可靠性**：#7597（二进制文件处理）和 #6839（参数类型序列化）反映工具链的健壮性仍需加强。
- **Heartbeat 反馈循环**（#7589）属于高严重性 bug，直接影响生产环境稳定性。

---

## 5. Bug 与稳定性

### 高严重度 Bug

| Issue | 描述 | Fix PR |
|---|---|---|
| [#7589](https://github.com/agentscope-ai/QwenPaw/issues/7589) | Heartbeat cron session 反馈循环导致消息重复堆积，Agent 无响应 | 暂无 |
| [#7579](https://github.com/agentscope-ai/QwenPaw/issues/7579) | 模型回复已写入历史但后续请求中丢失（空响应） | 暂无 |
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | `RetryChatModel` 硬编码 32768 上下文导致非预期 CONTEXT_UNFIT | 暂无 |
| [#7597](https://github.com/agentscope-ai/QwenPaw/issues/7597) | 工具返回 image/PDF 二进制触发 OpenAI 兼容接口 400 错误 | [#7621](https://github.com/agentscope-ai/QwenPaw/pull/7621)（已提 PR） |

### 已修复 Bug

- [#6541](https://github.com/agentscope-ai/QwenPaw/issues/6541) — 滚动压缩 role 错误 → 已关闭
- [#6885](https://github.com/agentscope-ai/QwenPaw/issues/6885) — 中文 IME 崩溃 → 已关闭
- [#7604](https://github.com/agentscope-ai/QwenPaw/issues/7604) — LLM 流超时硬编码 → 已关闭
- [#7156](https://github.com/agentscope-ai/QwenPaw/issues/7156) — Embedding 健康检查超时硬编码 → 已关闭

### 新报告 Bug

- [#7619](https://github.com/agentscope-ai/QwenPaw/issues/7619) — Windows 11 上 qwen-35B-A3B-FP8 模型对话无故结束
- [#7617](https://github.com/agentscope-ai/QwenPaw/issues/7617) — 含 PDF DataBlock 的 session 历史永久破坏纯文本 OpenAI 兼容端点
- [#7620](https://github.com/agentscope-ai/QwenPaw/issues/7620) — MCP streamable-http 非规范 401 响应阻断 legacy fallback
- [#7607](https://github.com/agentscope-ai/QwenPaw/issues/7607) — Cursor ACP Runner 扩展方法违反 JSON-RPC 协议导致流崩溃

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 诉求 | 路线图判断 |
|---|---|---|---|
| [#7613](https://github.com/agentscope-ai/QwenPaw/pull/7613) | feat | 新增 OpenViking 长期记忆后端 | 已提 PR，预计纳入下一版本 |
| [#7616](https://github.com/agentscope-ai/QwenPaw/pull/7616) | refactor | ADBPG/PowerContext 迁移至插件体系 | 已完成内存后端插件化迁移 |
| [#7608](https://github.com/agentscope-ai/QwenPaw/issues/7608) | feat | 钉钉频道支持流模式下交互式卡片回调 | 已提 Issue，待开发 |
| [#7526](https://github.com/agentscope-ai/QwenPaw/pull/7526) | feat | 受保护执行合约（protected execution contract） | 安全/权限增强，已提 PR |
| [#7609](https://github.com/agentscope-ai/QwenPaw/pull/7609) | feat | Skills 版本暴露与依赖校验 | 已提 PR，增强生态可观测性 |
| [#7610](https://github.com/agentscope-ai/QwenPaw/pull/7610) | fix | 防止聊天提交绕过队列 | 已提 PR，提升并发可靠性 |
| [#7502](https://github.com/agentscope-ai/QwenPaw/pull/7502) | feat | Console 侧边栏与设置体验重新设计 | 已提 PR，UI 重大改版 |
| [#7482](https://github.com/agentscope-ai/QwenPaw/pull/7482) | feat | Agent Kanban 中英双语本地化 | 已提 PR，国际化推进 |

**路线图信号：** 项目正加速推进**插件化架构**（记忆后端、Skills 管理）、**多语言支持**（中文本地化、BiDi 修复 #7611）以及**UI 现代化**（侧边栏重设计 #7502）。OpenViking 记忆后端和受保护执行合约是值得关注的新增能力。

---

## 7. 用户反馈摘要

### 痛点
1. **上下文丢失/不可见** — #7579 用户反映模型"看不到自己刚说的话"，影响多轮对话连贯性
2. **工作目录切换体验下降** — #7588/#7601 用户抱怨 v2.2.0 移除了路径手动输入功能，图形选择器对深层目录不友好
3. **Dashboard 性能** — #7242 用户在 74 个 Agent 场景下 Dashboard 加载超过 6 分钟
4. **工具返回二进制文件** — #7597/#7617 用户报告 image/PDF 工具调用结果导致 OpenAI 兼容接口 400 错误
5. **中文 IME 兼容性** — #6885（已修复）曾导致 Console 在中文输入时完全不可用

### 满意点
- 社区对修复响应速度认可：#6885、#7604、#7588 等近期问题均快速关闭
- 单元测试覆盖度提升获得认可（#7530 新增 245 个用例）
- 图标统一等细节改进（#7499）体现对用户体验的关注

---

## 8. 待处理积压

### 长期未响应 Issue（需维护者关注）

| Issue | 创建时间 | 评论数 | 状态 | 建议 |
|---|---|---|---|---|
| [#7589](https://github.com/agentscope-ai/QwenPaw/issues/7589) | 2026-09-06 | 4 | OPEN | 高严重性，Heartbeat 反馈循环影响生产稳定，建议优先处理 |
| [#7579](https://github.com/agentscope-ai/QwenPaw/issues/7579) | 2026-09-06 | 6 | OPEN | 上下文持久化核心问题，影响用户体验，需优先修复 |
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | 2026-09-05 | 5 | OPEN | 硬编码上下文回退影响所有模型，已有 5 条评论讨论但未解决 |
| [#7567](https://github.com/agentscope-ai/QwenPaw/issues/7567) | 2026-09-04 | 2 | OPEN | Web 端任务停止后仍在执行，状态同步问题 |
| [#7479](https://github.com/agentscope-ai/QwenPaw/issues/7479) | 2026-09-01 | 1 | OPEN | 频道命令拼写错误仍被转发至 Agent，缺乏校验 |
| [#7612](https://github.com/agentscope-ai/QwenPaw/issues/7612) | 2026-09-07 | 1 | OPEN | Hub 本地沙箱中内置 CLI 命令失效 |

### 待合并 PR

- [#7621](https://github.com/agentscope-ai/QwenPaw/pull/7621) — 修复 PDF block 对纯文本模型的兼容问题（对应 #7597/#7617）
- [#7598](https://github.com/agentscope-ai/QwenPaw/pull/7598) — 修复 Windows shell 工具 stdin 继承问题
- [#7611](https://github.com/agentscope-ai/QwenPaw/pull/7611) — BiDi 文本渲染修复
- [#7614](https://github.com/agentscope-ai/QwenPaw/pull/7614) — Computer Use 重启 native helper 控制动作

---

**日报生成时间：** 2026-09-08  
**数据来源：** GitHub agentscope-ai/QwenPaw  
**分析视角：** 开源项目健康度 ·

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-09-08

## 1. 今日速览

过去24小时 ZeroClaw 保持较高活跃度：37个 Issues 更新（31个新开/活跃，6个已关闭），50个 PR 更新（44个待合并，6个已合并）。项目整体处于快速迭代期，核心运行时、Channel 和 Provider 层均有重要修复推进，但 **44个 PR 待合并** 形成一定积压，需关注维护者响应节奏。无任何新版本发布。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

**今日已关闭/合并的重要 PR：**

| PR | 作者 | 内容 |
|---|---|---|
| [#10712](https://github.com/zeroclaw-labs/zeroclaw/pull/10712) | askldjd | 修复 Slack WebSocket TLS 证书信任不一致问题，统一使用平台根证书 |
| [#10711](https://github.com/zeroclaw-labs/zeroclaw/pull/10711) | JordanTheJet | 完善文档站 SEO：canonical 链接、hreflang、robots.txt 和 sitemap |
| [#10710](https://github.com/zeroclaw-labs/zeroclaw/pull/10710) | JordanTheJet | README 和 crate 元数据补充项目官网链接 |

**重点进行中 PR（部分）：**
- [#10214](https://github.com/zeroclaw-labs/zeroclaw/pull/10214) — 日志 entry-count 旋转与多段查询（size:XL）
- [#10450](https://github.com/zeroclaw-labs/zeroclaw/pull/10450) — Webhook SSE 流式传输支持（size:XL）
- [#9535](https://github.com/zeroclaw-labs/zeroclaw/pull/9535) — 上下文压缩锚定到模型窗口比例（size:XL）
- [#9724](https://github.com/zeroclaw-labs/zeroclaw/pull/9724) — `always_ask` 策略在 Full autonomy 模式下生效（size:XL）
- [#10337](https://github.com/zeroclaw-labs/zeroclaw/pull/10337) — Git 操作 honored allowed roots 安全修复（size:XL）
- [#9977](https://github.com/zeroclaw-labs/zeroclaw/pull/9977) — 文件系统写入限制在授权 workspace 内（size:XL）

> 多个 size:XL PR 处于 `needs-author-action` 状态，项目整体向 **日志可观测性、Webhook 流式、安全加固、上下文管理** 四个方向持续演进。

---

## 4. 社区热点

**讨论最活跃的 Issues（按评论数排序）：**

| Issue | 状态 | 热度 | 摘要 |
|---|---|---|---|
| [#8720](https://github.com/zeroclaw-labs/zeroclaw/issues/8720) | ✅ CLOSED | 12 评论 | Bedrock Nova 2 Lite 缓存断点配置需求 |
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | 🔓 OPEN | 6 评论 | Daemon 启动/重载时 Tokio 栈溢出（S1） |
| [#9333](https://github.com/zeroclaw-labs/zeroclaw/issues/9333) | 🔓 OPEN | 4 评论 | ACP 会话切换后失败 turn 消失（S1） |

**分析：**
- **#8720** 社区关注度高，涉及 Bedrock 模型缓存策略的实际使用痛点，已关闭说明需求已响应。
- **#10230** 和 **#9333** 均为 S1 级工作流阻塞型 bug，由同一 contributor（Audacity88）报告，反映 ZeroCode TUI 与 ACP 通路的稳定性仍是当前核心短板。

---

## 5. Bug 与稳定性

**今日报告的高风险 Bug（按严重程度排列）：**

| 严重级别 | Issue | 标题 | 是否有 Fix PR |
|---|---|---|---|
| 🔴 S1 | [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | Daemon 启动/重载时栈溢出 | — |
| 🔴 S1 | [#9333](https://github.com/zeroclaw-labs/zeroclaw/issues/9333) | ACP 会话切换后失败 turn 消失 | — |
| 🔴 S1 | [#10121](https://github.com/zeroclaw-labs/zeroclaw/issues/10121) | 进程退出时 partial turn 数据丢失 | — |
| 🔴 S1 | [#10670](https://github.com/zeroclaw-labs/zeroclaw/issues/10670) | heartbeat.target 拒绝复合 key | ✅ CLOSED |
| 🔴 S1 | [#10693](https://github.com/zeroclaw-labs/zeroclaw/issues/10693) | ZeroCode Connected 状态忽略 Enter | — |
| 🔴 S1 | [#10659](https://github.com/zeroclaw-labs/zeroclaw/issues/10659) | 预算超限后 Code turn 进度丢失 | — |
| 🟡 S2 | [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | 活跃 turn 中第二条消息触发并行运行 | — |
| 🟡 S2 | [#10688](https://github.com/zeroclaw-labs/zeroclaw/issues/10688) | WhatsApp Web 语音笔记永不被转写 | ✅ CLOSED |
| 🟡 S2 | [#10697](https://github.com/zeroclaw-labs/zeroclaw/issues/10697) | ACP 中转录工具调用前文本丢失 | — |
| 🟡 S2 | [#10702](https://github.com/zeroclaw-labs/zeroclaw/issues/10702) | token 预算截断在首个 turn 边界停止 | — |

> **稳定性评估：** 今日新增 6 个 S1 级问题，主要集中在 daemon 生命周期、ACP 转录和 ZeroCode 交互层，**暂无对应修复 PR**，属于高风险敞口。已关闭的 #10670 和 #10688 说明维护者响应速度尚可，但积压的 S1 需优先处理。

---

## 6. 功能请求与路线图信号

| Issue | 类型 | 内容 | 纳入下版可能性 |
|---|---|---|---|
| [#10660](https://github.com/zeroclaw-labs/zeroclaw/issues/10660) | Feature | Anthropic 缓存增加第三个断点（落在上一 turn 末尾消息） | ⭐⭐⭐ 高（与 #10662 关联，同作者） |
| [#10663](https://github.com/zeroclaw-labs/zeroclaw/issues/10663) | Feature | 可配置 Anthropic 缓存 1 小时 TTL | ⭐⭐⭐ 高（已关闭 #10660 的延伸） |
| [#10708](https://github.com/zeroclaw-labs/zeroclaw/issues/10708) | Feature | OpenAI Responses WebSocket 主动响应转向 | ⭐⭐ 中（新需求，无相关 PR） |
| [#10707](https://github.com/zeroclaw-labs/zeroclaw/issues/10707) | Feature | OpenAI Responses 有界编程式工具调用 | ⭐⭐ 中 |
| [#10705](https://github.com/zeroclaw-labs/zeroclaw/issues/10705) | Feature | 支持 GPT-6 Astra `max` reasoning effort | ⭐⭐ 中 |
| [#10704](https://github.com/zeroclaw-labs/zeroclaw/issues/10704) | Feature | OpenAI Responses 异步函数工具 | ⭐⭐ 中 |
| [#10695](https://github.com/zeroclaw-labs/zeroclaw/issues/10695) | Feature | ZeroCode 多客户端同步 session 刷新 | ⭐⭐ 中（依赖 #9739 多 session 工作） |

> **路线图信号：** Anthropic 缓存优化（#10660/#10663/#10662）已形成系列需求，**极可能在下个版本集中处理**；OpenAI Responses 适配方向有多条功能请求，预计是下一迭代重点。

---

## 7. 用户反馈摘要

| 痛点 | 来源 | 用户场景 |
|---|---|---|
| Bedrock Nova 2 Lite 随机缓存报错 | [#8720](https://github.com/zeroclaw-labs/zeroclaw/issues/8720) | 生产环境使用 Bedrock，缓存策略无法通过配置文件灵活关闭 |
| Daemon 启动时栈溢出 | [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | Quickstart 配置应用在运行中的 daemon 时触发 Tokio runtime worker 崩溃 |
| ACP 会话切换后数据丢失 | [#9333](https://github.com/zeroclaw-labs/zeroclaw/issues/9333) | Code/ACP 转场失败后切换 session 再返回，整段工具调用记录消失 |
| WhatsApp 语音永不被转写 | [#10688](https://github.com/zeroclaw-labs/zeroclaw/issues/10688) | 企业用户依赖 WhatsApp 语音输入，当前版本完全不可用 |
| ZeroCode 输入被静默忽略 | [#10693](https://github.com/zeroclaw-labs/zeroclaw/issues/10693) | TUI 显示 Connected 但 Enter/Ctrl+Enter 不提交，用户无法输入 |
| ACP 工具调用前文本丢失 | [#10697](https://github.com/zeroclaw-labs/zeroclaw/issues/10697) | 模型先输出文本再做工具调用时，前半部分文本不在 transcript 中渲染 |
| cost records 无法按会话拆分 | [#10700](https://github.com/zeroclaw-labs/zeroclaw/issues/10700) | `costs.jsonl` 中所有会话共享同一个 daemon-lifetime session_id，无法按对话统计花费 |

---

## 8. 待处理积压

**需维护者优先关注的 Issue：**

| Issue | 严重度 | 风险 | 备注 |
|---|---|---|---|
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | S1 | High | Daemon 栈溢出，Quickstart 应用时触发，无 Fix PR |
| [#9333](https://github.com/zeroclaw-labs/zeroclaw/issues/9333) | S1 | High | ACP 会话切换数据丢失，无 Fix PR |
| [#10121](https://github.com/zeroclaw-labs/zeroclaw/issues/10121) | S0 | High | 进程退出导致 partial turn 数据丢失 |
| [#10693](https://github.com/zeroclaw-labs/zeroclaw/issues/10693) | S1 | High | ZeroCode 交互阻断，无 Fix PR |
| [#10659](https://github.com/zeroclaw-labs/zeroclaw/issues/10659) | S1 | High | 预算超限后进度丢失，无 Fix PR |
| [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | S2 | High | 并行 run 导致重复工作和重复回复 |
| [#10697](https://github.com/zeroclaw-labs/zeroclaw/issues/10697) | S2 | High | ACP transcript 丢失工具调用前文本 |
| [#10702](https://github.com/zeroclaw-labs/zeroclaw/issues/10702) | S3 | Medium | token 预算截断逻辑与 message cap 存在相同 hysteresis 问题 |

> **积压评估：** 当前有 **7 个 S1/S0 级 bug 无对应 Fix PR**，集中在 daemon 生命周期管理和 ACP 交互层，是下一版本需要优先覆盖的稳定性目标。44 个待合并 PR 中约半数处于 `needs-author-action` 状态，建议维护者推进作者响应或接手。

---

**报告生成时间：** 2026-09-08 | **数据来源：** [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw)

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*