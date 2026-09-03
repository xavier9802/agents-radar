# OpenClaw 生态日报 2026-09-03

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-03 04:00 UTC

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



# OpenClaw 项目日报 | 2026-09-03

---

## 1. 今日速览

过去24小时 OpenClaw 项目保持高度活跃：共处理 500 条 Issues（新开/活跃 349 条，关闭 151 条）和 500 条 PR（待合并 393 条，已合并/关闭 107 条）。**无新版本发布**，但多项关键 Bug 修复 PR 已就绪待审。社区聚焦于 2026.8.1 升级回归问题、多 Agent 稳定性及消息丢失类缺陷，整体处于密集修复窗口期。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（107 条）

| PR | 类型 | 摘要 | 链接 |
|---|---|---|---|
| #134608 | Bug | 2026.8.1 auth migration 归档 JSON 但未保留凭据，导致永久阻塞修复 | [链接](https://github.com/openclaw/openclaw/issues/134608) |
| #123073 | Bug | dev-channel 更新失败：EUNSUPPORTEDPROTOCOL on workspace:*（npm/pnpm 协议不兼容） | [链接](https://github.com/openclaw/openclaw/issues/123073) |
| #134337 | Bug | memory_search 高并发下重复全量重索引导致状态污染 | [链接](https://github.com/openclaw/openclaw/issues/134337) |
| #135305 | Bug | Session observer 在投递失败后自我禁用，Slack 消息静默丢失 | [链接](https://github.com/openclaw/openclaw/issues/135305) |
| #78380 | Bug | Gateway 自重启时丢弃 Telegram/Discord 进行中回复 | [链接](https://github.com/openclaw/openclaw/issues/78380) |
| #123335 | Bug | `plugins init` 脚手架生成 `openclaw: latest`，可能选中旧版 CLI 导致构建失败 | [链接](https://github.com/openclaw/openclaw/issues/123335) |
| #134160 | UI Fix | Control UI 未读徽章在会话打开时不消失 | [链接](https://github.com/openclaw/openclaw/pull/134160) |
| #136496 | Fix | Codex legacy managed policy 失败时错误信息不透明 | [链接](https://github.com/openclaw/openclaw/pull/136496) |

**整体判断**：今日关闭的 Issues 多集中于 2026.8.1 升级回归链，维护者正在集中清理热修复 PR。393 条待合并 PR 显示开发节奏未放缓，但修复 PR 的合并速度是下一步关键指标。

---

## 4. 社区热点

### 高评论 Issue（Top 5）

| Issue | 评论数 | 标签 | 核心议题 | 链接 |
|---|---|---|---|---|
| #121953 | 13 | P1, diamond lobster | Cron agent 在 DeepSeek 上因前缀 `[cron:...]` 被 API edge 降权而卡顿 | [链接](https://github.com/openclaw/openclaw/issues/121953) |
| #85030 | 13 | P1, diamond lobster | MCP tools 未注入 subagent sessions，`bundle-mcp` 配置被忽略 | [链接](https://github.com/openclaw/openclaw/issues/85030) |
| #126360 | 12 | P1, diamond lobster | `agents.ownership: "explicit"` 下多 Agent 场景 `AgentSelectionRequiredError` 日志洪水 | [链接](https://github.com/openclaw/openclaw/issues/126360) |
| #98435 | 12 | P2, silver shellfish | MCP loopback transport 在 gateway 重启后未自动重连，`recovered=1` 误导 | [链接](https://github.com/openclaw/openclaw/issues/98435) |
| #127229 | 11 | P1, diamond lobster | Telegram durable update 在 watchdog 阶段被错误 tombstone，消息丢失 | [链接](https://github.com/openclaw/openclaw/issues/127229) |

**热点分析**：
- **MCP 与多 Agent 注入问题**（#85030）是社区关注焦点，6 个 👍 表明多位用户受此影响。
- **DeepSeek cron 前缀问题**（#121953）揭示了 LLM API 边缘路由对消息前缀的敏感性，属于跨 provider 的通用隐患。
- **升级回归链**（#134570、#134896）显示 2026.8.1 版本的状态迁移存在 7 个独立阻断点，用户反馈强烈。

---

## 5. Bug 与稳定性

### P0 / 高严重度

| Issue | 严重程度 | 类型 | 摘要 | Fix PR | 链接 |
|---|---|---|---|---|---|
| #123327 | **P0** | 数据损坏 | 共享状态 WAL checkpoint 在 ext4 上复制 SQLite page 1，导致数据库头被覆盖 | 无 | [链接](https://github.com/openclaw/openclaw/issues/123327) |
| #135835 | P1 | 行为 Bug | API key 充值后对话仍无法恢复，重启无效 | 无 | [链接](https://github.com/openclaw/openclaw/issues/135835) |
| #97616 | P1 | 回归 | Hook/tool 子进程泄漏，僵尸进程累积导致运行时退化 | 无 | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| #115424 | P1 | 崩溃 | Gateway V8 heap OOM 后 restart-recovery 触发 7 次 core-dump 循环 | 无 | [链接](https://github.com/openclaw/openclaw/issues/115424) |
| #128971 | P1 | 消息丢失 | Telegram final reply 在 `delivery_ambiguous` 时被静默丢弃 | 无 | [链接](https://github.com/openclaw/openclaw/issues/128971) |
| #134896 | P1 | 升级回归 | 2026.8.1 升级后 5 级 gateway 重启级联失败 + `doctor --fix` 自引用失败 | 无 | [链接](https://github.com/openclaw/openclaw/issues/134896) |
| #134570 | P1 | 升级回归 | 2026.8.1 升级后 gateway crash-loop + 静默投递失败，7 个独立阻断点 | 无 | [链接](https://github.com/openclaw/openclaw/issues/134570) |

### P1 关键 Bug

| Issue | 类型 | 摘要 | Fix PR | 链接 |
|---|---|---|---|---|
| #127229 | 行为 Bug | Telegram 消息在 watchdog 阶段被错误 tombstone | 无 | [链接](https://github.com/openclaw/openclaw/issues/127229) |
| #121953 | 行为 Bug | DeepSeek cron 前缀降权导致卡顿 | 无 | [链接](https://github.com/openclaw/openclaw/issues/121953) |
| #85030 | 行为 Bug | MCP tools 未注入 subagent | 无 | [链接](https://github.com/openclaw/openclaw/issues/85030) |
| #126360 | 行为 Bug | 多 Agent 所有权下 `AgentSelectionRequiredError` 日志洪水 | 无 | [链接](https://github.com/openclaw/openclaw/issues/126360) |
| #125570 | 行为 Bug | Skill Workshop update 覆盖 live skill 的 description，静默破坏路由 | 无 | [链接](https://github.com/openclaw/openclaw/issues/125570) |
| #118185 | 行为 Bug | 单次 turn 被写入 transcript 两次，内容不一致 | 无 | [链接](https://github.com/openclaw/openclaw/issues/118185) |
| #120449 | 行为 Bug | `tools.loopDetection` WARNING 仅服务端日志，模型/会话不可见 | 无 | [链接](https://github.com/openclaw/openclaw/issues/120449) |
| #136262 | 行为 Bug | openai-completions 流偶尔重复完整文本，消息数 n→2n→n 振荡 | 无 | [链接](https://github.com/openclaw/openclaw/issues/136262) |

### P2 中等问题

| Issue | 类型 | 摘要 | 链接 |
|---|---|---|---|
| #98435 | 行为 Bug | MCP loopback 重启后未重连，`recovered=1` 误导 | [链接](https://github.com/openclaw/openclaw/issues/98435) |
| #45494 | 回归 | Cron agent 在 LLM 持续 500 时未快速失败，耗尽 timeout | [链接](https://github.com/openclaw/openclaw/issues/45494) |
| #65374 | 行为 Bug | Dreaming 系统跨 Agent 污染记忆库 | [链接](https://github.com/openclaw/openclaw/issues/65374) |
| #123073 | 行为 Bug | dev 频道更新协议不兼容（npm vs pnpm） | [链接](https://github.com/openclaw/openclaw/issues/123073) |
| #96692 | 行为 Bug | Slack thread reply 生成成功但投递失败，origin tuple 丢失 | [链接](https://github.com/openclaw/openclaw/issues/96692) |
| #123596 | 行为 Bug | OpenAI Realtime agent-consult 慢响应导致语音会话误判为无回复 | [链接](https://github.com/openclaw/openclaw/issues/123596) |
| #120735 | 行为 Bug | Telegram sticker 作为原始文件引用到达，未生成描述 | [链接](https://github.com/openclaw/openclaw/issues/120735) |
| #88079 | 回归 | WebChat 中 Kimi Code / DeepSeek Reasoner 的 reasoning_content 未流式渲染 | [链接](https://github.com/openclaw/openclaw/issues/88079) |

---

## 6. 功能请求与路线图信号

| Issue | 优先级 | 摘要 | 相关 PR | 链接 |
|---|---|---|---|---|
| #45508 | P2 | WebChat 支持自托管 STT/TTS，绕过浏览器 Speech API | 无 | [链接](https://github.com/openclaw/openclaw/issues/45508) |
| #121729 | P3 | 为后台 Agent 添加友好型每日/共享花费预算 | 无 | [链接](https://github.com/openclaw/openclaw/issues/121729) |
| #16555 | P1 | 投递队列消息支持 TTL/过期，防止重启后陈旧条目堆积 | 无 | [链接](https://github.com/openclaw/openclaw/issues/16555) |
| #52803 | P2 | 多 Agent 编排 Control UI 升级：层级视图、批量操作 | 无 | [链接](https://github.com/openclaw/openclaw/issues/52803) |

**路线图信号**：
- PR #135890（task-lanes 可配置看板）和 #134943（插件自定义 Control UI）正在推进，与 #52803 的多 Agent UI 需求形成呼应。
- PR #134003（Talk native realtime）和 #136588（chat-triggered self-update 可见性修复）反映维护者对实时语音和可观测性的投入。
- 花费预算管理（#121729）暂无 PR，但属于高频用户需求，值得关注。

---

## 7. 用户反馈摘要

**痛点集中度最高**：
1. **2026.8.1 升级灾难**：多个用户报告升级后 gateway 重启级联失败、auth 凭据丢失、状态迁移不完整。#134896 和 #134570 均为一线用户实测反馈，非合成复现。
2. **消息丢失缺乏可见性**：Telegram #128971、Slack #96692、MCP loopback #98435 共同指向一个模式——系统报告成功但消息实际丢失，且 `recovered=1` 等状态字段误导运维判断。
3. **多 Agent 配置脆弱**：#85030（MCP 未注入）、#126360（AgentSelectionRequiredError 洪水）、#65374（记忆跨 Agent 污染）表明多 Agent 编排的边界条件尚未稳固。
4. **DevOps 体验摩擦**：#123073（npm/pnpm 协议冲突）、#135835（充值后无法恢复）、#122019（`update status` 忽略 plugin 兼容性）显示升级路径和状态管理存在系统性缺陷。

**正面信号**：
- PR #136959（跳过未使用的 BTW reasoning 收集）和 #136929（MCP scheduler alias 预计算）显示性能优化持续推进。
- PR #136960 修复 Tailscale 下图片预览不可用问题，解决远程部署场景痛点。

---

## 8. 待处理积压

### 需维护者关注的长期 Issue

| Issue | 创建时间 | 评论数 | 风险 | 状态 | 链接 |
|---|---|---|---|---|---|
| #123327 | 2026-08-13 | 6 | **数据损坏**，WAL checkpoint 覆盖 SQLite 页 1 | Open，无 PR | [链接](https://github.com/openclaw/openclaw/issues/123327) |
| #97616 | 2026-06-29 | 10 | 进程泄漏导致运行时退化，长期运行场景必现 | Open，无 PR | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| #115424 | 2026-07-28 | 7 | OOM 后 crash-loop，生产环境高危 | Open，无 PR | [链接](https://github.com/openclaw/openclaw/issues/115424) |
| #45494 | 2026-03-13 | 9 | Cron agent 在 LLM 持续故障时耗尽 timeout，缺乏快速失败 | Open，无 PR | [链接](https://github.com/openclaw/openclaw/issues/45494) |
| #65374 | 2026-04-12 | 9 | Dreaming 跨 Agent 记忆污染，多租户场景必现 | Open，无 PR | [链接](https://github.com/openclaw/openclaw/issues/65374) |
| #121617 | 2026-08-10 | 5 | 上下文压缩 "Already compacted" 误判导致 turn 静默失败 | Open，无 PR | [链接](https://github.com/openclaw/openclaw/issues/121617) |
| #123548 | 2026-08-14 | 4 | `message_tool_only` 请求者跳过 message tool 时子 Agent 结果丢失 | Open，无 PR | [链接](https://github.com/openclaw/openclaw/issues

---

## 横向生态对比



# AI 智能体开源生态横向对比分析
**日期：2026-09-03 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

开源个人 AI 助手与自主智能体生态呈现**多项目并行、活跃度高、技术路线分化**的特征。头部项目已进入密集修复期（升级回归、消息丢失、多 Agent 竞态），同时架构层 RFC 讨论升温，反映生态从"功能堆叠"向"系统稳定性与可观测性"演进。多项目共同关注**多 Agent 编排、会话状态管理、安全策略加固、MCP 协议集成**四大方向，技术成熟度分化明显——部分项目进入生产级打磨，部分仍在快速验证期。

---

## 2. 各项目活跃度对比

| 项目 | Issues (新开/活跃) | PR (待合并/已合并) | 版本发布 | 健康度 |
|------|-------------------|-------------------|----------|--------|
| **OpenClaw** | 349 / 151 | 393 / 107 | 无 | 🔴 密集修复窗口 |
| **Hermes Agent** | 47 / - | 47 / 3 | 无 | 🟢 架构重构期 |
| **ZeroClaw** | 50 / - | 50 / - | 无 | 🟢 高频迭代 |
| **CoPaw** | 18 / 10 | 21 / 6 | v2.2.0 + beta.7 | 🟢 活跃 |
| **NanoBot** | 2 / - | 19 / 4 | 无 | 🟢 健康 |
| **IronClaw** | 6 / 4 | 16 / 10 | 无 | 🟡 良好 |
| **LobsterAI** | 6 / - | 7 / 2 | 无 | 🟡 修复期 |
| **Moltis** | 2 / - | 0 / 2 | 3个快照版本 | 🟢 快速收敛 |
| **NanoClaw** | 2 / - | 18 / 3 | 无 | B+ 良好 |
| **PicoClaw** | 1 / - | 0 / 1 | 无 | 🟡 低活跃 |
| **NullClaw** | - | - | - | ⚪ 无活动 |
| **ZeptoClaw** | - | - | - | ⚪ 无活动 |

---

## 3. OpenClaw 在生态中的定位

**规模与定位**：OpenClaw 是当前生态中 **Issues 和 PR 数量最高**的项目（各 500 条），处于"核心参照"地位，定位为**全功能多 Agent 编排平台 + 多渠道网关**。

| 维度 | OpenClaw | 同类对比 |
|------|----------|----------|
| Issue/PR 量级 | 500/500 | 是第二名（Hermes Agent）的 10 倍以上 |
| 社区规模 | 最大，P1 diamond lobster 标签频发 | 反映用户基数与复杂度最高 |
| 技术路线 | 多 Agent 编排 + MCP + 全渠道网关 | 与 CoPaw（Hub 模式）、ZeroClaw（架构 RFC）分化 |
| 当前阶段 | 升级回归密集修复（2026.8.1 链式问题） | 其他项目处于功能扩张或架构重构 |

**优势**：渠道覆盖最广（Telegram/Discord/Slack/Matrix/Codex 等）、多 Agent 编排功能最完整、MCP 协议深度集成。

**劣势**：2026.8.1 升级回归暴露状态迁移脆弱性，P0 数据损坏 Bug（#123327）影响 SQLite 持久化安全。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **多 Agent 编排稳定性** | OpenClaw、Hermes Agent、CoPaw | 跨 Agent 记忆污染、会话锁竞态、MCP 未注入 subagent、多 Agent 所有权错误洪水 |
| **消息渠道可靠性** | OpenClaw、NanoBot、CoPaw、ZeroClaw | 消息丢失（Telegram/Slack/MCP loopback）、投递状态误导（`recovered=1`）、WebSocket 鉴权失效（PicoClaw QQ 401） |
| **会话状态管理** | Hermes Agent、ZeroClaw、OpenClaw | Lease 管理竞态、压缩超时与 Worker 行为不一致、session 合约层所有权争议（RFC-9487） |
| **安全策略与沙箱** | NanoBot、CoPaw、ZeroClaw、LobsterAI、NanoClaw | 路径遍历漏洞（NanoBot #5564）、安全沙箱绕过（CoPaw #7511）、delegate 绕过高危命令（ZeroClaw #10165）、MCP 参数白名单（LobsterAI #2590） |
| **供应链安全** | NanoClaw | `minimumReleaseAge` 提升至 3 天，防止同日恶意发布注入 |
| **可观测性与 Hook 系统** | Moltis、ZeroClaw、Hermes Agent | Hook 生命周期完整性（Moltis #1255/#1257）、事件追溯、审计链路 |
| **推理能力精细化** | Moltis、CoPaw、NanoBot | 推理努力等级控制（Moltis #1253）、推理上下文截断优化（NanoBot #5611） |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构差异 |
|------|----------|----------|--------------|
| **OpenClaw** | 全渠道网关 + 多 Agent 编排 | 企业/复杂工作流用户 | 重度 MCP 集成、多 provider 路由、WAL 持久化 |
| **NanoBot** | 轻量个人助手 + macOS 安全沙箱 | 开发者/个人用户 | Seatbelt sandbox、AgentRunner 内部压缩、本地 tiktoken 优化 |
| **Hermes Agent** | 桌面级 Agent + 实时语音 | 桌面应用用户 | Realtime Voice Provider ABC、AgentRuntime Plugin API、Group Chat 连续性 |
| **PicoClaw** | 国产信创渠道适配 | 中国用户 | QQ Channel 富媒体支持、Docker/Linux 双部署 |
| **NanoClaw** | 企业级网关 + 供应链安全 | 生产环境部署者 | Provider 合约化重构、credential lane 支持、pnpm 门控 |
| **CoPaw** | 多用户 Hub + Qwen 生态 | 团队/组织用户 | QwenPaw Hub 自托管、Make-Skill v2 审批流、ACP 代理 |
| **LobsterAI** | IM 会话并发处理 + 文件上传 | 中文 IM 用户 | per-session 执行序列化、per-conversation 互斥锁 |
| **Moltis** | Hook 系统 + 推理粒度控制 | 审计/复杂工作流用户 | 共享 Schema、OpenAI Codex Responses API 透传 |
| **ZeroClaw** | 架构 RFC 治理 + 会话合约重构 | 深度参与者/架构师 | Append-only 事件历史、Runtime-owned session、WASM Observer |
| **IronClaw** | WebUI v2 + 流式渲染优化 | Web 应用用户 | TypeScript 严格化、ProviderStreamSink 线性合并 |
| **Moltis** | Hook 生命周期 + 推理等级 | 生产级可观测性用户 | AgentEnd/MessageSending/MessageSent 事件派发补全 |

---

## 6. 社区热度与成熟度

### 快速迭代期（日更 50+ PR/Issue）
- **OpenClaw**：500+500，处于升级回归密集修复期
- **Hermes Agent**：50+50，架构重构（Realtime Voice、Plugin API）
- **ZeroClaw**：50+50，RFC 讨论活跃，安全漏洞修复中
- **CoPaw**：27+18，新版本发布后快速响应社区反馈

### 稳定发展期（日更 20-50）
- **NanoBot**：23 PR，安全修复与性能优化并重
- **IronClaw**：26 PR，WebUI 重构与流式性能优化
- **LobsterAI**：17 更新，IM 并发竞态修复

### 中等活跃度（日更 <20）
- **NanoClaw**：23 更新，provider 合约化重构中
- **Moltis**：4 更新，单日多版本发布，功能收敛期
- **PicoClaw**：2 更新，低活跃稳定期，QQ 鉴权问题待解决

### 无活动
- **NullClaw**、**ZeptoClaw**：生态边缘项目或已停更

---

## 7. 值得关注的趋势信号

| 趋势 | 证据 | 对开发者的参考价值 |
|------|------|-------------------|
| **会话状态管理成为瓶颈** | OpenClaw 7 个升级回归点、Hermes Agent Lease 竞态、ZeroClaw RFC-9487 重构 | 多 Agent 场景需优先保证 session 合约清晰度，避免状态迁移链式故障 |
| **安全策略从"能绕过"到"可审计"** | CoPaw #7511 沙箱突破、ZeroClaw #10165 delegate 绕过、NanoBot #5633 路径遍历 | 生产部署需关注委托执行链路的权限隔离与审计日志完整性 |
| **Hook/事件系统标准化** | Moltis #1257 补全生命周期派发、ZeroClaw RFC Append-only 事件历史 | 可观测性基建成为生产级 Agent 的标配需求 |
| **MCP 协议深度集成但暴露稳定性问题** | OpenClaw #85030 MCP 未注入、#98435 loopback 未重连、PicoClaw QQ 鉴权变更 | MCP 集成需关注连接生命周期管理与鉴权方式演进 |
| **上下文压缩与推理粒度精细化** | NanoBot #5403 tiktoken 低估、#5611 reasoning replay 限制、Moltis #1253 max effort | 长上下文场景需关注 token 估算准确性与推理策略可配置性 |
| **跨渠道消息丢失缺乏可见性** | OpenClaw #128971/#96692、NanoBot #5637、ZeroClaw 多处投递失败 | 消息网关需建立端到端投递追踪，避免 `recovered=1` 类误导状态 |

---

**总结**：开源 AI 智能体生态已进入**稳定性攻坚期**，头部项目从功能扩张转向修复升级回归、安全加固与架构重构。OpenClaw 作为规模最大项目承担较多技术债务清理，新兴项目通过架构 RFC 讨论（ZeroClaw）或快速迭代（Moltis）寻找差异化定位。对开发者而言，**会话状态管理、安全策略审计、消息投递可观测性**是当前最值得投入的技术方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-09-03

## 1. 今日速览

过去 24 小时内 NanoBot 保持高活跃度：共产生 **23 条 PR**（19 条待合并、4 条已合并/关闭），并新增 **2 条活跃 Issue**。项目无新版本发布，但开发节奏紧凑，涵盖安全修复、性能优化、WebUI 体验改进及多 Provider 集成等多个方向。整体健康度良好，Bug Fix 与功能增强并行推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展 — 今日合并/关闭的 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#5568](https://github.com/HKUDS/nanobot/pull/5568) | refactor | `AgentRunner` 现在拥有本地请求压力感知的上下文压缩流程，压缩决策从外部移至 Runner 内部，实现同步压缩 |
| [#5623](https://github.com/HKUDS/nanobot/pull/5623) | fix | 修复 `AgentLoop._active_tasks` 在任务完成后遗留空集合的内存泄漏（Fixes #5428） |
| [#5625](https://github.com/HKUDS/nanobot/pull/5625) | feat/webui | 重构首次运行 AI 设置流程，将"Model not configured"警告替换为中性引导，直接打开 Models 设置页 |

**整体评价**：今日 3 条关闭 PR 分别解决了架构职责划分、内存泄漏和用户体验三个不同层面的问题，项目在日常维护与体验打磨上稳步推进。

---

## 4. 社区热点 — 高关注度 Issues / PRs

| 编号 | 类型 | 说明 | 热度分析 |
|---|---|---|---|
| [#5628](https://github.com/HKUDS/nanobot/pull/5628) | feat/security | macOS Seatbelt sandbox 后端，通过 `sandbox-exec(1)` 实现进程级隔离 | 安全增强型 PR，镜像 `bwrap` 策略，关注 macOS 用户群体 |
| [#5403](https://github.com/HKUDS/nanobot/pull/5403) | fix/perf | 修复本地 tiktoken 估算比 API 实际值低 30-50%，导致上下文压缩从未触发（Fixes #5402） | P1 级性能问题，影响所有现代模型用户 |
| [#5633](https://github.com/HKUDS/nanobot/pull/5633) | fix/security | 修复 session 密钥路径遍历漏洞（Fixes #5564），未审计的 session id 可访问 sessions 目录外文件 | P1 级安全修复，容器部署场景风险更高 |
| [#5446](https://github.com/HKUDS/nanobot/pull/5446) | fix/provider | Codex OAuth token 持久化至 Nanobot 数据目录，解决容器环境下 token 不可持久的问题 | 与 #5638 形成 Copilot 侧对称修复 |
| [#5611](https://github.com/HKUDS/nanobot/pull/5611) | fix/perf | 将 reasoning replay 限制在最近一次 assistant turn，避免历史推理内容持续占用 token 预算 | 修复 #5584，影响使用 deep reasoning 模型的用户 |
| [#5520](https://github.com/HKUDS/nanobot/pull/5520) | feat/provider | 为 Codex provider 添加 Langfuse tracing 支持 | 填补 Codex 无 Langfuse 追踪的空白 |

---

## 5. Bug 与稳定性

### P1（高严重度）

| Issue/PR | 描述 | 状态 |
|---|---|---|
| [#5402](https://github.com/HKUDS/nanobot/issues/5402) → [#5403](https://github.com/HKUDS/nanobot/pull/5403) | 本地 tiktoken 低估 prompt tokens，导致上下文压缩永不触发 | ✅ PR 已合并 |
| [#5564](https://github.com/HKUDS/nanobot/issues/5564) → [#5633](https://github.com/HKUDS/nanobot/pull/5633) | Session 密钥路径遍历，未信任 session id 可读写 sessions 目录外文件 | ✅ PR 待合并 |

### P2（中等严重度）

| Issue/PR | 描述 | 状态 |
|---|---|---|
| [#5446](https://github.com/HKUDS/nanobot/pull/5446) + [#5638](https://github.com/HKUDS/nanobot/pull/5638) | Codex / Copilot OAuth token 存储于平台数据目录，容器部署下不可持久 | PR 待合并 |
| [#5637](https://github.com/HKUDS/nanobot/pull/5637) | Matrix stream 传递失败被静默丢弃，未传播至 channel manager retry 策略 | PR 待合并 |
| [#5635](https://github.com/HKUDS/nanobot/pull/5635) | SDK 流队列满时关闭会丢弃最早未读事件 | PR 待合并 |
| [#5634](https://github.com/HKUDS/nanobot/pull/5634) | `ChannelManager._origin_reply_fingerprints` 无限增长，长运行 gateway 内存泄漏 | PR 待合并 |

---

## 6. 功能请求与路线图信号

| 来源 | 需求描述 | 对应 PR | 纳入下一版本概率 |
|---|---|---|---|
| [#5586](https://github.com/HKUDS/nanobot/issues/5586) | 支持 `ephemeral` runtime context block，不持久化至历史 | [#5627](https://github.com/HKUDS/nanobot/pull/5627) | ⭐⭐⭐⭐ 高（PR 已提交，直接对应 Issue） |
| [#5631](https://github.com/HKUDS/nanobot/issues/5631) | WebUI 展示模型速度、上下文 token 等信息 | 暂无对应 PR | ⭐⭐ 中（需求明确，待实现） |
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) | `isolated_session` 配置，允许 heartbeat 共享目标 session | PR 待合并（标注 conflict） | ⭐⭐ 中（需解决冲突） |
| [#5620](https://github.com/HKUDS/nanobot/pull/5620) | Cron 任务支持可配置交付目标和批量归档 | PR 待合并 | ⭐⭐⭐ 高（功能完整，待 review） |
| [#5614](https://github.com/HKUDS/nanobot/pull/5614) | Telegram 富文本消息流式发送 | PR 待合并 | ⭐⭐⭐ 高（作者计划本周 review） |

---

## 7. 用户反馈摘要

- **上下文可见性诉求强烈**：Issue #5631 用户希望 WebUI 直观展示模型速度和上下文信息，类似 DeepSeek Harness 的体验，反映用户对"黑盒"交互的不满。
- **首次使用体验待改善**：PR #5625 解决了新用户面对"Model not configured"警告的困惑，将引导流程改为中性操作，说明此前首次设置体验不够友好。
- **长运行 Gateway 稳定性关注**：Issue #5428（已被 #5623 修复）和 #5634 都指向长期运行的 gateway 任务堆积和内存泄漏问题，说明生产场景用户对稳定性要求较高。
- **安全敏感度高**：路径遍历漏洞（#5564）和 OAuth token 持久化问题引发快速响应，说明用户和贡献者对部署安全较为关注。

---

## 8. 待处理积压

| 编号 | 类型 | 创建时间 | 说明 | 建议 |
|---|---|---|---|---|
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) | feat | 2026-06-26 | `heartbeat.isolatedSession` 配置，标注 conflict，已积压近 3 个月 | 优先解决 conflict 后合并 |
| [#5212](https://github.com/HKUDS/nanobot/pull/5212) | feat | 2026-08-02 | MiniMax music provider 支持，待合并 | 跟进 review |
| [#5614](https://github.com/HKUDS/nanobot/pull/5614) | feat | 2026-08-30 | Telegram 富文本流式消息，作者计划本周 review | 关注作者进展 |
| [#5586](https://github.com/HKUDS/nanobot/issues/5586) | enhancement | 2026-08-28 | Ephemeral runtime context，Issue 与 PR #5627 对应 | PR 待合并，跟进 |
| [#5631](https://github.com/HKUDS/nanobot/issues/5631) | enhancement | 2026-09-02 | WebUI 上下文/速度展示，无对应 PR | 可考虑排入下一迭代 |

---

**日报生成时间**：2026-09-03 | **数据来源**：[HKUDS/nanobot](https://github.com/HKUDS/nanobot) GitHub

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-09-03**

---

## 1. 今日速览

Hermes Agent 项目今日保持高活跃度，24小时内共产生50条Issue更新和50条PR更新，其中新开/活跃Issue 47条，待合并PR 47条，显示社区贡献持续活跃。开发重心集中在**会话状态管理（session-state）**和**桌面端稳定性**两大核心领域，多个P1级Bug被追踪修复。值得注意的是，Realtime Voice Provider 接口设计和 AgentRuntime Plugin API 两个架构级改进已进入关键开发阶段，反映项目正在从单点功能优化向系统性重构演进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日关键PR动态

| PR | 类型 | 摘要 |
|-----|------|------|
| [#101808](https://github.com/NousResearch/hermes-agent/issues/101808) | 功能 | Realtime Voice Provider 合约、编排器和首个内置Provider |
| [#101052](https://github.com/NousResearch/hermes-agent/issues/101052) | 功能 | AgentRuntime v1 插件API，支持provider-neutral运行时 |
| [#101852](https://github.com/NousResearch/hermes-agent/issues/101852) | 修复 | 解决Windows桌面端browser_exec 420s超时阻塞问题 |
| [#101850](https://github.com/NousResearch/hermes-agent/issues/101850) | 修复 | 修复Windows Desktop更新过程中日志断流问题 |
| [#101824](https://github.com/NousResearch/hermes-agent/issues/101824) | 修复 | 修复压缩会话中timeout-to-late-ack竞态条件 |
| [#98307](https://github.com/NousResearch/hermes-agent/issues/98307) | 功能 | Group Chat连续性、控制和文件支持完整化 |
| [#99992](https://github.com/NousResearch/hermes-agent/issues/99992) | 修复 | 修复Desktop预保存网关登录会话写入问题 |
| [#100303](https://github.com/NousResearch/hermes-agent/issues/100303) | 性能 | 桌面端会话转录本从持久化页面打开，提升加载性能 |

**项目推进评估：** 今日开发工作高度聚焦于**会话生命周期管理**和**桌面端稳定性**两个核心领域，同时推进了Realtime Voice和AgentRuntime两个架构级功能的接口设计。项目整体向前推进了约**3-4个关键模块**的成熟度。

---

## 4. 社区热点

### 讨论最活跃的Issues

| Issue | 评论数 | 标签 | 核心诉求 |
|-------|--------|------|----------|
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 23 | feature, gateway, desktop, sessions | Bot Group Chats在桌面端关闭后应保持运行 |
| [#77111](https://github.com/NousResearch/hermes-agent/issues/77111) | 22 | feature, agent, tts, needs-decision | 统一RealtimeVoiceProvider接口设计 |
| [#78642](https://github.com/NousResearch/hermes-agent/issues/78642) | 16 | refactor, mcp | 拆解mcp_tool.py god文件（7230行） |
| [#97948](https://github.com/NousResearch/hermes-agent/issues/97948) | 16 | bug, agent, compression, P1 | 大型会话压缩超时与背景Worker成功竞态 |

### 高赞Issue

| Issue | 👍数 | 摘要 |
|-------|-------|------|
| [#20765](https://github.com/NousResearch/hermes-agent/issues/20765) | 6 | 浏览器Dashboard Voice Mode WebRTC音频采集 |
| [#53836](https://github.com/NousResearch/hermes-agent/issues/53836) | 4 | 实时多模态语音模式功能请求 |

**热点分析：** 社区最关注的是**会话连续性**（Group Chat保活、跨设备同步）和**语音交互体验**提升。架构层面，mcp_tool.py重构和RealtimeVoiceProvider抽象设计引发激烈讨论，反映开发者对代码可维护性的重视。

---

## 5. Bug 与稳定性

### P1 严重级别

| Issue | 摘要 | Fix PR |
|-------|------|--------|
| [#97948](https://github.com/NousResearch/hermes-agent/issues/97948) | 手动/compress报告120s超时，但背景Worker数分钟后成功；大型会话压缩失败 | [#101824](https://github.com/NousResearch/hermes-agent/issues/101824) |
| [#98077](https://github.com/NousResearch/hermes-agent/issues/98077) | SQLite 3.50.4 WAL模式下state.db物理B树损坏 | 待定 |
| [#101415](https://github.com/NousResearch/hermes-agent/issues/101415) | 后台孤儿lease被识别为兄弟owner，永久锁定会话 | 已关闭 |
| [#81880](https://github.com/NousResearch/hermes-agent/issues/81880) | macOS Desktop MCP stdio进程累积导致OOM | 待定 |

### P2 重要级别

| Issue | 摘要 | Fix PR |
|-------|------|--------|
| [#61457](https://github.com/NousResearch/hermes-agent/issues/61457) | Desktop远程网关session cookie无法持久化，401循环 | [#99992](https://github.com/NousResearch/hermes-agent/issues/99992) |
| [#96731](https://github.com/NousResearch/hermes-agent/issues/96731) | Windows桌面browser_exec 420s超时 | [#101852](https://github.com/NousResearch/hermes-agent/issues/101852) |
| [#101644](https://github.com/NousResearch/hermes-agent/issues/101644) | v0.21.0 named conversation重复存储历史（2轮变8消息） | 待定 |
| [#101748](https://github.com/NousResearch/hermes-agent/issues/101748) | Dashboard仍为Electron渲染器提供服务（#52945修复缺口） | 待定 |
| [#101669](https://github.com/NousResearch/hermes-agent/issues/101669) | MCP boolean property schema导致整个server被park | 待定 |

### 今日新增Bug

| Issue | 摘要 |
|-------|------|
| [#101800](https://github.com/NousResearch/hermes-agent/issues/101800) | Rate-limit退出码75不可达，配额耗尽被误判为协议违规 |
| [#101817](https://github.com/NousResearch/hermes-agent/issues/101817) | ACP context meter报告累积token而非当前使用量 |
| [#101744](https://github.com/NousResearch/hermes-agent/issues/101744) | rollback.diff静默截断4000字符无标记 |
| [#101783](https://github.com/NousResearch/hermes-agent/issues/101783) | Discord typing indicator空闲后持续存在 |

**稳定性评估：** 今日共报告**11个Bug**，其中3个P1级，5个P2级。session-state相关故障占主导（6/11），建议优先关注Lease管理和压缩竞态条件。

---

## 6. 功能请求与路线图信号

| Issue | 需求摘要 | 关联PR | 纳入可能性 |
|-------|----------|--------|-----------|
| [#77111](https://github.com/NousResearch/hermes-agent/issues/77111) | RealtimeVoiceProvider ABC接口设计 | [#101808](https://github.com/NousResearch/hermes-agent/issues/101808) | **高** - 已有实现PR |
| [#101052](https://github.com/NousResearch/hermes-agent/issues/101052) | AgentRuntime插件API | 同Issue | **高** - 开发中 |
| [#20765](https://github.com/NousResearch/hermes-agent/issues/20765) | 浏览器Dashboard Voice Mode | 待定 | 中 |
| [#53836](https://github.com/NousResearch/hermes-agent/issues/53836) | 实时多模态语音模式 | 同[#77111] | **高** - 与Voice Provider重合 |
| [#79772](https://github.com/NousResearch/hermes-agent/issues/79772) | Slack功能补齐与@Hermes Tag | 待定 | 中 |
| [#38737](https://github.com/NousResearch/hermes-agent/issues/38737) | 远程控制与Cowork模式 | 待定 | 低 |
| [#20140](https://github.com/NousResearch/hermes-agent/issues/20140) | Cron job发送消息工具 | 待定 | 低 |

**路线图判断：** 下一版本（v0.22）预计重点推进：
1. Realtime Voice Provider架构落地
2. AgentRuntime Plugin API稳定
3. Group Chat跨设备连续性完善

---

## 7. 用户反馈摘要

### 主要痛点

1. **会话状态管理混乱**
   - 用户反馈压缩功能手动触发与后台Worker行为不一致，UI显示超时但实际成功
   - Lease机制存在竞态，导致会话被错误锁定
   
2. **桌面端稳定性问题**
   - Windows端browser_exec工具长时间阻塞（420s超时）
   - MCP进程泄漏导致Mac 16GB内存设备OOM
   - 远程网关登录会话cookie无法持久化

3. **配置与工具行为异常**
   - `hermes config set`将列表值序列化为JSON字符串而非YAML列表
   - Kanban rate-limit退出码不可达，配额耗尽被误判
   - rollback.diff静默截断无提示

### 用户满意点

- Group Chat连续性改进获得积极反馈
- 会话性能优化（PR #100303）在Windows验证场景下效果显著
- 技能写审查流程改进（PR #98794）提升用户体验

---

## 8. 待处理积压

### 长期未响应的重要Issue

| Issue | 创建日期 | 天数 | 优先级 | 风险标注 |
|-------|----------|------|--------|----------|
| [#98077](https://github.com/NousResearch/hermes-agent/issues/98077) | 2026-08-29 | 5天 | P1 | risk-session-state |
| [#81880](https://github.com/NousResearch/hermes-agent/issues/81880) | 2026-08-08 | 26天 | P1 | risk-session-state |
| [#61457](https://github.com/NousResearch/hermes-agent/issues/61457) | 2026-07-09 | 56天 | P2 | risk-session-state |
| [#78642](https://github.com/NousResearch/hermes-agent/issues/78642) | 2026-08-04 | 30天 | P3 | 代码质量 |

### 需要维护者关注

1. **#98077 SQLite数据库损坏** - P1级数据完整性问题，需紧急响应
2. **#81880 MCP进程泄漏** - 影响生产环境稳定性，已有但长期未修复
3. **#78642 mcp_tool.py重构** - 7230行god文件亟需模块化，影响长期可维护性

---

**报告生成时间：** 2026-09-03  
**数据来源：** NousResearch/hermes-agent GitHub仓库  
**分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-09-03

---

## 1. 今日速览

过去24小时内，PicoClaw 项目保持轻度活跃：新增 1 个 Issue（BUG 类）、关闭 1 个 PR（enhancement 类），无新版本发布。项目整体处于**低活跃稳定期**，社区贡献节奏平稳。值得关注的是，近期刚合并的 QQ Channel 附件支持 PR 与今日新增的 QQ 401 鉴权 Bug 存在关联性，二者可能需要同步关注。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

**PR #1349 — feat(qq): 支持解析和回复更多附件类型**（已合并）

- **作者**：aishannon
- **创建时间**：2026-03-11 → **合并时间**：2026-09-02
- **功能推进**：
  - 支持解析 QQ 频道的 emoji 结构
  - 支持接收语音、图片、视频、文件类消息
  - 支持回复本地附件（发送前自动上传）
  - 优先使用 Markdown 消息回复，降级兼容兜底
- **意义**：这是 QQ Channel 渠道的一次重要能力补齐，历时约 6 个月后终于合并，显著提升了 QQ 渠道的富媒体交互体验。结合今日 Issue #3349 的 401 报错，该 PR 的合并可能与 QQ API 鉴权方式的变更存在时间上的重叠。

🔗 [PR #1349](https://github.com/sipeed/picoclaw/pull/1349)

---

## 4. 社区热点

**Issue #3349 — [BUG] QQ频道无法正常使用（401 鉴权失败）** ⚠️

- **作者**：bxwl5 | 评论数：2 | 创建：2026-08-30 | 最新：2026-09-02
- **现象**：Docker 版本和 Linux x86 版本均受影响，gateway 日志返回：
  > `failed to get websocket info: code:401, text:{"message":"请求头Authorization参数格式错误","code":11241,"err_code":40011005}`
- **分析**：错误码 `40011005` 及 `11241` 指向 QQ 频道 API 对 Authorization 请求头的格式校验收紧，可能与 QQ 官方近期 API 变更有关。该 Issue 直接影响 QQ Channel 渠道可用性，是今日社区核心关注点。
- **与 PR #1349 的关联**：PR #1349 在 9 月 2 日刚合并（同一天 Issue 更新），需确认鉴权逻辑是否因 PR 合并或上游依赖更新而引入问题。

🔗 [Issue #3349](https://github.com/sipeed/picoclaw/issues/3349)

---

## 5. Bug 与稳定性

| 优先级 | 问题 | 严重程度 | 状态 | Fix PR |
|--------|------|----------|------|--------|
| 🔴 高 | QQ Channel 鉴权 401 报错，WebSocket 连接失败 | 功能性阻断 | 新建，无修复 | 暂无 |

- Issue #3349 为**功能性阻断 Bug**，影响 QQ 频道渠道的完整可用性，且跨平台（Docker / Linux x86）复现。
- 建议维护者评估是否需要回滚 PR #1349 相关改动或紧急更新 QQ API 鉴权实现。

---

## 6. 功能请求与路线图信号

**来自 PR #1349 的功能已落地**：
- QQ 附件类型解析与回复能力（语音/图片/视频/文件）✅
- Markdown 优先的回复策略 ✅

**潜在方向信号**：
- QQ 频道的富媒体支持已初步建立，后续可能围绕**更多消息类型解析**（如合并转发、小程序卡片等）和**鉴权稳定性**继续演进。
- Issue #3349 的反馈暗示 QQ 渠道 API 适配是当前重点维护方向，建议路线图优先保障渠道兼容。

---

## 7. 用户反馈摘要

- **痛点**：QQ 频道在鉴权层出现 401 错误，导致整个频道功能不可用，用户通过 Docker 和原生 Linux x86 两种部署方式均验证了问题存在。
- **使用场景**：用户在将 PicoClaw 作为多平台消息网关使用时，QQ 频道是重要的接入渠道之一，当前 Bug 直接阻断了该链路。
- **满意度信号**：PR #1349 的合并说明社区对 QQ 富媒体功能有较强需求，但鉴权稳定性问题可能抵消这一改进带来的收益。

---

## 8. 待处理积压

| 类型 | Issue / PR | 创建时间 | 状态 | 提醒 |
|------|-----------|---------|------|------|
| 🐛 Bug | [Issue #3349](https://github.com/sipeed/picoclaw/issues/3349) | 2026-08-30 | 新建，无回复 | 建议 48 小时内确认问题根因并给出回应，该 Bug 影响范围明确且用户已提供完整日志 |

> **维护者关注建议**：Issue #3349 与 PR #1349 存在时间上的紧邻关系，建议排查 PR #1349 合并后是否引入了 QQ 鉴权相关依赖变更，或 QQ 官方 API 侧是否同期发生了调整。

---

**项目健康度评估**：🟡 中等 — 新功能持续合入，但当日出现一个阻断性 Bug 且暂无回应，需关注维护者响应速度。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# 📊 NanoClaw 项目动态日报
**日期：2026-09-03** | 数据来源：GitHub API

---

## 1. 今日速览

NanoClaw 今日保持中高强度活跃，过去 24 小时内共产生 **23 条更新**（2 Issues + 21 PRs），其中 **18 条 PR 待合并**、**3 条已合并/关闭**，整体呈现"快速迭代 + 大量审查中"的状态。项目无新版本发布，但内部架构正在经历一波系统性重构——provider 合约化、delivery 可靠性修复、通道安全性加固三管齐下，技术债清理与稳定性提升是今日主旋律。

---

## 2. 版本发布

> 无新版本发布（0 个）。

---

## 3. 项目进展

### 今日已合并 / 关闭的 PR（3 条）

| PR | 类型 | 摘要 |
|---|---|---|
| [#2973](https://github.com/nanocoai/nanoclaw/pull/2973) | Fix · 已关闭 | 供应链安全：将 `minimumReleaseAge` 提升至 pnpm-workspace.yaml 顶层，激活 3 天版本等待门控，防止恶意发布同日注入 |
| [#3672](https://github.com/nanocoai/nanoclaw/pull/3672) | Fix · 已关闭 | 测试修复：修正 slack-raw-text skill 复制行为的预期 |
| [#3593](https://github.com/nanocoai/nanoclaw/pull/3593) | Test · 已关闭 | 锁定 Codex provider 的 `speed → service_tier` 渲染行为，补充回归测试 |

### 值得关注的新 PR（今日新建）

- **[#3703](https://github.com/nanocoai/nanoclaw/pull/3703)** — 修复 delivery 模块对断开连接适配器的无效重试，避免重复抛错消耗三次尝试配额
- **[#3702](https://github.com/nanocoai/nanoclaw/pull/3702)** — 修复 `ncl tasks run` 命令不立即触发 reconcile 的延迟问题（最长等待 60s）

> **整体评估**：今日推进了三条明确的质量线——供应链安全（#2973）、任务调度延迟（#3702）和 delivery 容错（#3703）。核心架构层正在由 `zvi-fried` 推动 provider 合约化重构（#3584/#3585/#3586/#3588/#3591），属于中长期技术债清理，暂不影响用户侧功能。

---

## 4. 社区热点

### Issues

| Issue | 主题 | 作者 | 创建时间 | 链接 |
|---|---|---|---|---|
| [#3701](https://github.com/nanocoai/nanoclaw/issues/3701) | 是否接受 gateway 声明的 credential lane 进入 validateSpec | davekim917 | 2026-09-02 | [链接](https://github.com/nanocoai/nanoclaw/issues/3701) |
| [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) | update-nanoclaw skill 刷新：本地适配器验证失败 / 无跳过选项 | glifocat | 2026-08-25 | [链接](https://github.com/nanocoai/nanoclaw/issues/3529) |

**热点分析：**

- **#3701** 由生产级部署者提出，维护着 24 个 agent group 各带独立凭证集的网关架构，诉求合理且与 `contributedEnv` 占位符替换模式兼容，有望被核心采纳。
- **#3529** 反映自定义适配器用户在自动更新场景下的痛点：skill refresh 误判本地适配器为 skill 产物并尝试覆盖，缺乏 opt-out 机制，需维护者评估是否纳入更新逻辑。

### PR 热度

- **[#3492](https://github.com/nanocoai/nanoclaw/pull/3492)** — 与已合并的 #2973 形成对照，展示核心团队对 pnpm 配置门控的双重验证，体现安全修复的严谨性。
- **[#3584 / #3585 / #3586 / #3588 / #3591](https://github.com/nanocoai/nanoclaw/pulls)** — zvi-fried 发起的 provider 合约化系列 PR，共 5 个关联 PR，显示核心层架构重构正在密集推进。

---

## 5. Bug 与稳定性

| 严重程度 | Issue/PR | 描述 | Fix PR |
|---|---|---|---|
| 🟡 中 | [#3703](https://github.com/nanocoai/nanoclaw/pull/3703) | delivery 未检查 `isConnected()`，对断开适配器浪费重试次数 | ✅ 新建 PR #3703 |
| 🟡 中 | [#3702](https://github.com/nanocoai/nanoclaw/pull/3702) | `ncl tasks run` 不主动注入 reconcile 队列，等待最长 60s | ✅ 新建 PR #3702 |
| 🟡 中 | [#3427](https://github.com/nanocoai/nanoclaw/pull/3427) | `send_card` 工具虚假报告成功，Chat SDK bridge 静默丢弃回调按钮 | ✅ PR #3427（待合并）|
| 🟡 中 | [#3674](https://github.com/nanocoai/nanoclaw/pull/3674) | Teams 出站文件未携带 MIME 类型，导致上传被拒 | ✅ PR #3674（待合并）|
| 🟡 中 | [#3596](https://github.com/nanocoai/nanoclaw/pull/3596) | Teams 含冒号用户 ID 未命名空间化，卡片点击与发送者解析失效 | ✅ PR #3596（待合并）|
| 🟡 中 | [#3597](https://github.com/nanocoai/nanoclaw/pull/3597) | 网关代理模式下 `host.docker.internal` 的 HTTP MCP 服务器不可达 | ✅ PR #3597（待合并）|
| 🟢 低 | [#3680](https://github.com/nanocoai/nanoclaw/pull/3680) | `validateSpec` 中 allowlisted-extra mount 存在绕过安全限制的风险 | ✅ PR #3680（待合并）|

> **稳定性评估**：今日无崩溃类 Bug，所有问题均为功能逻辑缺陷或安全边界加固，共 7 个 Bug 已有对应 PR，修复率 **100%**，项目健康度良好。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 关联 PR | 纳入预期 |
|---|---|---|---|
| Gateway-declared credential lane 支持 | Issue #3701 | — | 待核心讨论，架构兼容性强，有望纳入 |
| `speed` 推理属性（per-agent-group） | — | [#3592](https://github.com/nanocoai/nanoclaw/pull/3592) | ✅ PR 已提交，待合并即生效 |
| AIML API 集成 | PR #3573 | [#3573](https://github.com/nanocoai/nanoclaw/pull/3573) | 待 review，集成类 PR 通常进入下个版本 |
| Codex / OpenCode provider 合约化 | — | #3584 / #3588 / #3591 | 正在进行中，将统一 provider 接口规范 |
| Host provider 合约化 | — | [#3585](https://github.com/nanocoai/nanoclaw/pull/3585) | 正在进行中 |
| Setup provider 合约化 + 安装验证器 | — | [#3586](https://github.com/nanocoai/nanoclaw/pull/3586) | 正在进行中 |

> **路线图信号**：项目正从"各 provider 自由实现"向"合约化 + 核心渲染规范"演进，`speed` 属性和 credential lane 支持是近期最可能的用户可见功能。

---

## 7. 用户反馈摘要

| 痛点 / 场景 | 来源 | 情绪 |
|---|---|---|
| 自定义适配器被 `update-nanoclaw` skill 误判并覆盖，无跳过选项 | #3529 | 😤 不满 |
| 网关模式下 `host.docker.internal` 的本地 MCP 服务器不可访问 | #3597 | 😤 阻塞工作流 |
| `ncl tasks run` 触发后有最长 60s 延迟，影响实时性 | #3702 | 😐 可接受但需修复 |
| Teams 卡片按钮点击和发送者解析因冒号 ID 命名空间问题失效 | #3596 | 😤 影响生产 |
| 出站文件缺少 MIME 类型导致 Teams 拒绝 | #3674 | 😤 影响生产 |
| `send_card` 工具虚假成功报告，回调按钮被静默丢弃 | #3427 | 😤 信任问题 |
| 供应链安全：npm/pnpm 包发布当天可被安装，存在恶意发布窗口 | #2973 / #3492 | ✅ 已修复 |

---

## 8. 待处理积压

| 类型 | ID | 创建时间 | 距今日 | 建议 |
|---|---|---|---|---|
| Issue | [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) | 2026-08-25 | 9 天 | 需核心评估 `update-nanoclaw` skill 的适配器识别逻辑，增加 opt-out |
| PR | [#3492](https://github.com/nanocoai/nanoclaw/pull/3492) | 2026-08-23 | 11 天 | 补充 regression test，与已合并的 #2973 对齐 |
| PR | [#3113](https://github.com/nanocoai/nanoclaw/pull/3113) | 2026-07-21 | 44 天 | WhatsApp 媒体 staging 修复，长期待合并，建议优先 review |
| PR | [#3573](https://github.com/nanocoai/nanoclaw/pull/3573) | 2026-08-27 | 7 天 | AIML API 集成请求，待社区评价 |

> **维护者提醒**：PR #3113（WhatsApp 媒体修复）已积压 44 天，建议优先 review。Issue #3529 涉及用户自定义适配器保护，属于体验层面的重要缺口，建议在本轮重构中一并考虑。

---

**📈 项目健康度总评：B+**
- 活跃度：✅ 高（23 条/24h）
- 修复响应：✅ 快（Bug 100% 有 PR）
- 架构演进：✅ 有序推进中
- 积压风险：⚠️ 个别 PR 超过 40 天未 review

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 | 2026-09-03

## 1. 今日速览
过去24小时 IronClaw 保持高频迭代节奏，共处理 26 条 PR（10 条合并/关闭）与 10 条 Issue（6 条活跃/4 条关闭）。核心工作高度聚焦于 **WebUI v2 TypeScript 严格化攻坚**、**工具调用失败语义修复** 以及 **多通道流式响应性能优化**。项目整体健康状况良好，技术债务清理与底层稳定性加固并重，暂无新版本发布。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
今日推进了三项关键工程节点：
- **设计系统统一**：合并 Issue #8017 / #8018 / #8019 / #8020，完成扩展配置表单、自动化状态横幅、工作区与日志筛选器向共享组件（`Input` / `SearchField` / `InlineNotice`）的迁移，消除本地重复样式。
- **回复与流式渲染修复**：PR #8051 修正了 Slack/Telegram 渠道在多模型调用时错误累积历史叙述文本的显示逻辑；PR #8043 优化了 `ProviderStreamSink::text_delta` 的文本合并策略，将内存拷贝复杂度从 O(N·k) 降至线性，测试回归验证 16 KiB 流式更新开销显著下降。
- **CI/构建加速**：PR #8050 消除 Reborn 测试 lane 的冷编译冗余（稳定 hermetic Cargo home + push-only 共享缓存）；PR #8042 / #8045 修复 CLI serve 进程在

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 — 2026-09-03

---

## 1. 今日速览

LobsterAI 今日整体活跃度中等，过去 24 小时产生 8 条 Issue 更新（6 条已关闭）和 9 条 PR 更新（2 条已合并）。**无新版本发布**。社区层面反映出 IM 会话并发竞态问题引发较多关注，两名开发者（MaoQianTu、0xFLX）围绕核心 Cowork 和配置同步逻辑提交了修复 PR。项目稳定性处于修复窗口期，用户端反馈集中在文件上传丢失、网关重启异常及 Markdown 导出体验等问题。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

**已合并/关闭（2 条）：**

| PR | 作者 | 内容 |
|----|------|------|
| [#2598](https://github.com/netease-youdao/LobsterAI/pull/2598) | liuzhq1986 | 修复 Windows 端指南相关问题（`area: renderer`） |
| [#2597](https://github.com/netease-youdao/LobsterAI/pull/2597) | btc69m979y-dotcom | 将应用内浏览器功能从 2026.8.31 发布线回滚，保留原分支供后续重新引入 |

**关键待合并 PR 亮点：**
- **#1090** 与 **#1100**：针对 IM 消息并发导致重复会话创建和流式消息损坏的竞态修复，引入 per-session 执行序列化与 per-conversation 异步互斥锁。
- **#1101**：修复跨 Provider 切换模型后立即发消息触发「模型服务调用失败」的竞态问题，将 `configService.updateConfig()` 的 fire-and-forget 改为 await 完成后再允许用户发送。
- **#2590**：安全加固，对 MCP stdio 命令参数及外部 URL 进行协议白名单与路径校验。

---

## 4. 社区热点

| Issue/PR | 类型 | 评论数 | 核心诉求 |
|----------|------|--------|----------|
| [#1099](https://github.com/netease-youdao/LobsterAI/issues/1099) | Bug | 1 | IM 并发竞态导致重复会话与消息丢失；已有 PR #1100 跟进 |
| [#1090](https://github.com/netease-youdao/LobsterAI/pull/1090) | Fix | — | 同 Issue #1089 关联，修复 CoworkRunner 无重入保护问题 |
| [#1567](https://github.com/netease-youdao/LobsterAI/issues/1567) | 功能请求 | 2 | 输入框增加快捷操作按钮（停止当前话题、压缩上下文），提升用户可恢复性 |
| [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) | Bug | 3 | 最新版无论输入均返回相同内容，疑似上下文或模型调用链路异常 |

**热点分析**：IM 并发问题（#1099 / #1100）和 CoworkRunner 竞态（#1090）是近期技术讨论焦点，说明多用户/高并发场景下的会话管理已成为稳定性瓶颈。功能请求 #1567 反映了用户对「紧急中断」机制的迫切需求。

---

## 5. Bug 与稳定性

| 级别 | Issue | 描述 | Fix PR |
|------|-------|------|--------|
| 🔴 高 | [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) | 最新版输入任意内容均返回相同回复 | 待定 |
| 🔴 高 | [#1099](https://github.com/netease-youdao/LobsterAI/issues/1099) | IM 消息并发导致重复会话创建、消息丢失 | #1100 |
| 🟡 中 | [#1561](https://github.com/netease-youdao/LobsterAI/issues/1561) | 文件上传后模型无法感知已上传文件（新版本回归） | 待定 |
| 🟡 中 | [#1569](https://github.com/netease-youdao/LobsterAI/issues/1569) | 提问后无响应且无任何错误提示 | 待定 |
| 🟡 中 | [#1551](https://github.com/netease-youdao/LobsterAI/issues/1551) | 网络环境变化导致网关反复重启 | 待定 |
| 🟢 低 | [#1096](https://github.com/netease-youdao/LobsterAI/issues/1096) | md→pdf 转换产生多余浏览器标签页及会员弹窗干扰 | 待定 |
| 🟢 低 | [#1563](https://github.com/netease-youdao/LobsterAI/issues/1563) | 流量包服务条款页面存在文字错误 | 待定 |

**回归警示**：#1561（文件上传后模型不可见）和 #1566（固定回复）均为新版本引入的问题，建议发布前加强端到端回归测试。

---

## 6. 功能请求与路线图信号

| 请求 | Issue | 关联 PR | 评估 |
|------|-------|---------|------|
| 会话内容全文搜索与关键词高亮 | — | [#1125](https://github.com/netease-youdao/LobsterAI/pull/1125) | **高优先级**：已实现并待合并，扩展搜索范围从标题到消息全文，提升长历史会话可检索性 |
| 输入框快捷操作按钮（停止/压缩上下文） | [#1567](https://github.com/netease-youdao/LobsterAI/issues/1567) | 无 | **中优先级**：用户明确诉求，可考虑纳入下一版本 UX 优化 |
| Docker 沙箱就绪检测 | — | [#1103](https://github.com/netease-youdao/LobsterAI/pull/1103) | **中优先级**：增加只读 Docker daemon probe，帮助用户提前感知 sandbox 环境可用性 |
| 定时任务开关 Tooltip | — | [#1102](https://github.com/netease-youdao/LobsterAI/pull/1102) | **低优先级**：i18n tooltip 补充，已就绪 |

---

## 7. 用户反馈摘要

**核心痛点：**
1. **上下文失控**：用户多次反馈「回复相同内容」（#1566）和「输入无响应」（#1569），暗示长上下文管理或模型调用链路存在隐患。
2. **文件上传功能退化**：#1561 指出新版不再自动将文件放入 project 目录，导致模型无法感知附件，属明确回归。
3. **网络环境敏感**：#1551 反映网关在网络切换时反复重启，影响多环境（如移动网络/Wi-Fi 切换）下的稳定性。
4. **导出体验差**：#1096 抱怨 md→pdf 转换时残留浏览器标签页和会员弹窗，影响专业场景使用。

**正向反馈**：尚无正面评价反馈，建议后续版本收集用户满意度数据。

---

## 8. 待处理积压

| 类型 | 编号 | 创建时间 | 距今 | 备注 |
|------|------|----------|------|------|
| Issue | [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) | 2026-04-08 | 约 5 月 | 🔴 高优先级 Bug，无 Fix PR |
| Issue | [#1561](https://github.com/netease-youdao/LobsterAI/issues/1561) | 2026-04-08 | 约 5 月 | 🔴 新版本回归，需紧急排查 |
| Issue | [#1569](https://github.com/netease-youdao/LobsterAI/issues/1569) | 2026-04-08 | 约 5 月 | 🟡 无响应无报错，难以复现 |
| Issue | [#1551](https://github.com/netease-youdao/LobsterAI/issues/1551) | 2026-04-08 | 约 5 月 | 🟡 网关稳定性问题 |
| Issue | [#1096](https://github.com/netease-youdao/LobsterAI/issues/1096) | 2026-03-31 | 约 5 月 | 🟢 用户体验问题，长期未响应 |

**建议**：#1561 和 #1566 作为版本回归问题，应优先纳入下一 Hotfix 版本处理；#1096 长期未响应，可考虑标记 stale 或移入 backlog。

---

**报告生成时间**：2026-09-03  
**数据来源**：GitHub netease-youdao/LobsterAI

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 | 2026-09-03

## 1. 今日速览
Moltis 在过去24小时内处于高频迭代状态，单日连续发布3个版本（20260902.01~03），显示项目正快速收敛核心能力。Issues 与 PR 同步推进，虽暂无合并记录，但 `#1255`/`#1254` 与 `#1257` 形成明确的修复链路，`#1253` 补齐推理级别支持。整体健康度良好，项目正从基础可用阶段向生产级可观测性与精细化控制迈进。

## 2. 版本发布
- **20260902.01 / .02 / .03**：过去24小时密集发布的三个快照版本。原始数据未提供对应 Changelog，推测为按提交日期或构建流水线触发的快速迭代标签。建议后续版本说明中明确 Hook 派发修复与 `ReasoningEffort.max` 的具体变更，以降低升级验证成本。

## 3. 项目进展
今日无 PR 合并/关闭，但以下 PR 已就绪并直接推动项目向前：
- **#1257** `fix(hooks): complete lifecycle dispatch`：补全 `AgentEnd`、`MessageSending`、`MessageSent` 的运行时派发，并为 Tool Call 系列 Hook 注入可选 `tool_call_id`，实现单次调用端到端关联，同时保持旧版 JSON 载荷兼容。
- **#1253** `feat(reasoning): add max effort level`：在共享 Schema、OpenAI Codex Responses API 透传层及前端选择器中补齐 `max` 级别，支持上限推理力度的显式控制。
项目整体向前推进约 **1个主要维度**（Hook 生命周期完整化）与 **1个能力扩展维度**（推理努力等级精细化），技术债务正在被主动清除。

## 4. 社区热点
今日讨论高度集中在 **Hook 体系可观测性** 与 **推理能力对齐**：
- **#1255** 指出声明但未派发的生命周期事件将导致监控/审计静默失效，影响生产稳定性。
- **#1254** 提出在 `BeforeToolCall`/`AfterToolCall` 中传递稳定 ID，反映复杂多步工具调用场景下对调用链追踪的强需求。
- **#1253** 响应多模态/长链推理用户对算力分级管控的期待。
所有热点均由核心贡献者 `GTanger` 发起，说明当前迭代由主导开发者驱动，需求-实现链路紧凑。
🔗 [Issue #1255](https://github.com/moltis-org/moltis/issues/1255) | [Issue #1254](https://github.com/moltis-org/moltis/issues/1254) | [PR #1257](https://github.com/moltis-org/moltis/pull/1257) | [PR #1253](https://github.com/moltis-org/moltis/pull/1253)

## 5. Bug 与稳定性
- **[高] #1255** `AgentEnd/MessageSending/MessageSent hooks are declared but never dispatched`：Hook 系统结构性缺陷，可能导致依赖事件派发的插件/审计逻辑失效。**已有 Fix PR #1257**，状态 Open，预计合并后可彻底关闭。
- 无崩溃、回归或数据损坏报告。整体稳定性处于修复爬坡期，生产环境依赖 Hook 链路的用户建议跟踪 #1257 合并进度后再升级。

## 6. 功能请求与路线图信号
- **#1254** 稳定 `tool_call_id` 注入：明确指向复杂工作流可追溯性，与 #1257 的实现直接吻合，**极大概率纳入下一版本**。
- **#1253** `max` 推理级别：表明项目正在对齐上游 OpenAI Codex Responses API 最新能力，面向高阶推理/长上下文场景做准备。
路线图信号清晰：**可观测性基建强化 + 推理能力精细化** 双主线并行。

## 7. 用户反馈摘要
基于 Issue 正文与检查项（评论数均为0）提炼：
- **真实痛点**：Hook 系统存在“声明即完成”的假象，实际事件未触发，导致自定义生命周期逻辑静默失败；多步工具调用缺乏上下文关联 ID，难以实现端到端追踪。
- **使用场景**：生产级 AI Agent 部署、分布式任务审计、复杂工具链编排。
- **满意度**：开发者对向后兼容性要求严格（#1257 明确保留旧 JSON 载荷结构），说明项目注重平滑升级。
- **未满意**：单日多版本发布节奏快，但 Release Notes 滞后，增加集成验证负担。

## 8. 待处理积压
今日无长期未响应 Issue。当前积压均为 **高优先级待合并项**，建议维护者优先 Review：
1. **#1257** `fix(hooks): complete lifecycle dispatch` — 核心稳定性修复，直接闭环 #1255/#1254
2. **#1253** `feat(reasoning): add max effort level` — 上游 API 能力对齐
3. **#1256** `chore(deps-dev): bump browserslist from 4.28.2 to 4.28.8` — Dependabot 常规安全更新

整体来看，Moltis 当前处于功能加固与生命周期补全的关键窗口期，Issue-PR 对应

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 | 2026-09-03

---

## 1. 今日速览

CoPaw 在过去 24 小时内保持较高活跃度：新增/活跃 Issues 18 条、关闭 Issues 10 条；PR 更新 27 条（待合并 21 条、已合并/关闭 6 条）。项目今日发布 **v2.2.0 正式版** 及 **v2.2.0-beta.7** 测试版，核心进展集中在 Console 侧边栏重构、工具治理安全加固、MCP 白名单强制检查及 ACP 代理 Windows 启动阻塞修复。整体项目处于 2.2.0 稳定版上线后的快速迭代期，社区反馈较为积极。

---

## 2. 版本发布

### v2.2.0（正式版）
- **发布日期**：2026-09-03
- **主要新增**：
  - **QwenPaw Hub**：支持自托管多用户 Hub，提供本地进程/Docker 运行时、工作空间级访问控制、凭据管理及反向代理支持（[PR #7112](https://github.com/agentscope-ai/QwenPaw/pull/7112)）
  - ReMe 长时记忆后端 embedding 维度标准化修复
- **已知问题**：需关注 [Issue #7469](https://github.com/agentscope-ai/QwenPaw/issues/7469)（ReMe 背景 embedding 任务失败）、[Issue #7510](https://github.com/agentscope-ai/QwenPaw/issues/7510)（`/memory/status` 返回 500）

### v2.2.0-beta.7（测试版）
- **发布日期**：2026-09-02
- **修复内容**：
  - 标准化后端特定 embedding 维度（[PR #7465](https://github.com/agentscope-ai/QwenPaw/pull/7465)）
  - WebUI 深色模式样式覆盖修复（[PR #7485](https://github.com/agentscope-ai/QwenPaw/pull/7485)）
- **状态**：[Release Duty 验证 Issue #7503](https://github.com/agentscope-ai/QwenPaw/issues/7503)

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#7501](https://github.com/agentscope-ai/QwenPaw/pull/7501) | 功能 | 新增 Agent 模型路由设置面板（子模型、fallback 模型配置） |
| [#7348](https://github.com/agentscope-ai/QwenPaw/pull/7348) | 文档 | 发布 v2.2.0 变更说明 |
| [#7508](https://github.com/agentscope-ai/QwenPaw/pull/7508) | 功能 | Make-Skill v2 工作流（已合并至 #7509） |
| [#7489](https://github.com/agentscope-ai/QwenPaw/pull/7489) | 修复 | 修复 PyInstaller 多进程运行时钩子，解决 macOS StdIO MCP 崩溃问题 |
| [#7471](https://github.com/agentscope-ai/QwenPaw/pull/7471) | 修复 | 修复 MCP Clients 页面深色模式背景色异常 |
| [#7481](https://github.com/agentscope-ai/QwenPaw/pull/7481) | 修复 | 修复 macOS StdIO MCP 子进程导致后端被杀的问题 |

**整体判断**：6 个 PR 已合并/关闭，项目正在稳步推进 v2.2.0 的收尾工作，侧边栏重构、模型路由、工具治理安全等核心功能已落地。

---

## 4. 社区热点

### 高活跃 Issues

| Issue | 类型 | 评论数 | 摘要 |
|---|---|---|---|
| [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | Bug | 7 | 主 Agent+多子 Agent 场景下进度查询需用户主动触发 |
| [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) | Bug | 6 | Console 流式输出出现大量重复文本块 |
| [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | Bug | 5 | 危险指令绕过安全策略 |
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | Bug | 4 | ReMe 背景 embedding 任务失败（依赖访问时序问题） |
| [#6464](https://github.com/agentscope-ai/QwenPaw/issues/6464) | Bug | 4 | 平台模型连接测试失败、模型列表为空 |

### 高活跃 PRs

| PR | 状态 | 摘要 |
|---|---|---|
| [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) | OPEN | Pawport：支持从 Codex/Qoder 导入指令、技能、插件等 |
| [#7401](https://github.com/agentscope-ai/QwenPaw/pull/7401) | UNDER REVIEW | 修复 Windows ACP Agent 启动阻塞问题 |
| [#7509](https://github.com/agentscope-ai/QwenPaw/pull/7509) | OPEN | Make-Skill v2 工作流 |
| [#7502](https://github.com/agentscope-ai/QwenPaw/pull/7502) | OPEN | Console 侧边栏与设置体验重构 |

**热点分析**：用户最关注的是**多 Agent 协作的主动性**（#7450）、**流式输出稳定性**（#7417）、**安全沙箱绕过**（#7443/#7511）以及**跨平台导入能力**（#6960）。

---

## 5. Bug 与稳定性

### 严重级别：高

| Issue | 描述 | Fix PR |
|---|---|---|
| [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) | **安全沙箱被突破**，已关闭 | — |
| [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | 危险指令易绕过安全策略 | — |
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | ReMe 长时记忆 embedding 任务静默失败 | — |
| [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | 自定义提供商加载失败（`max_tokens` 迁移问题） | — |

### 严重级别：中

| Issue | 描述 | Fix PR |
|---|---|---|
| [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) | Console 流式输出重复文本块 | — |
| [#7431](https://github.com/agentscope-ai/QwenPaw/issues/7431) | Codex 第三方智能体返回空响应（火山方舟网关） | — |
| [#7513](https://github.com/agentscope-ai/QwenPaw/issues/7513) | DeepSeek-v4-pro 工具调用与对话混合异常 | — |
| [#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447) | 长上下文场景早期记录丢失 | — |
| [#7505](https://github.com/agentscope-ai/QwenPaw/issues/7505) | 局域网 LLM Server 频繁 client disconnect | — |
| [#7496](https://github.com/agentscope-ai/QwenPaw/issues/7496) | CRITICAL 规则直接拒绝而非触发审批 | [PR #7497](https://github.com/agentscope-ai/QwenPaw/pull/7497) ✅ |
| [#7510](https://github.com/agentscope-ai/QwenPaw/issues/7510) | `/memory/status` 返回 500 | — |

### 严重级别：低

| Issue | 描述 | Fix PR |
|---|---|---|
| [#7516](https://github.com/agentscope-ai/QwenPaw/issues/7516) | 企业微信无法发送 base64 图片 | — |
| [#7507](https://github.com/agentscope-ai/QwenPaw/issues/7507) | 企业微信流式输出单字延迟（150ms throttle） | — |
| [#7467](https://github.com/agentscope-ai/QwenPaw/issues/7467) | loop.rubric 强制确认轮次隐藏首条回复 | [已关闭](https://github.com/agentscope-ai/QwenPaw/issues/7467) |
| [#7493](https://github.com/agentscope-ai/QwenPaw/issues/7493) | Agent 模型路由面板无法渲染 | [PR #7501](https://github.com/agentscope-ai/QwenPaw/pull/7501) ✅ |
| [#7512](https://github.com/agentscope-ai/QwenPaw/issues/7512) | 对话进行中无法切换会话 | — |

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 评估 |
|---|---|---|
| [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) | **A2A 协议支持** | 用户询问 2.x A2A 支持计划；当前仅支持 MCP，预计纳入后续路线图 |
| [#7514](https://github.com/agentscope-ai/QwenPaw/issues/7514) | **远程 WebUI 首次加载优化** | 用户反馈长对话历史加载慢，移动端尤甚；优先级中等 |
| [#7406](https://github.com/agentscope-ai/QwenPaw/issues/7406) | **主题定制支持** | 请求支持 accent color、字体、间距配置；当前无官方支持 |
| [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) | **Pawport 导入功能** | 支持从 Codex/Qoder 导入配置，已 OPEN，有望纳入下一版本 |
| [#7509](https://github.com/agentscope-ai/QwenPaw/pull/7509) | **Make-Skill v2** | 审批驱动的技能创建工作流，已合并至 #7509 |
| [#7502](https://github.com/agentscope-ai/QwenPaw/pull/7502) | **侧边栏重构** | 统一侧边栏与设置体验，已 OPEN |

---

## 7. 用户反馈摘要

### 痛点
- **多 Agent 协作主动性不足**：用户反馈主 Agent 不会主动查询子 Agent 状态，需手动询问（#7450）
- **长上下文稳定性差**：上下文较长时早期记录丢失，导致任务中断（#7447）
- **安全策略可绕过**：危险指令绕过问题及 CRITICAL 规则直接拒绝而非审批的 bug（#7443、#7511、#7496）
- **局域网 LLM 连接不稳定**：client disconnect 导致频繁重试超时（#7505）
- **控制台性能**：远程 WebUI 首次加载对话历史滞后（#7514）

### 满意点
- v2.2.0 新增的 **Agent 模型路由设置** 解决了配置分散问题（#7501 已合并）
- **ReMe 记忆系统** 持续优化，embedding 维度标准化修复（#7465）
- **工具治理安全加固**：`OFF` 模式下敏感路径拒绝执行（#7497）

---

## 8. 待处理积压

| Issue/PR | 状态 | 创建时间 | 说明 |
|---|---|---|---|
| [#6464](https://github.com/agentscope-ai/QwenPaw/issues/6464) | CLOSED | 2026-07-25 | 模型连接测试失败，平台级问题，已关闭但需确认根因 |
| [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) | OPEN | 2026-08-13 | Pawport 导入功能，等待 Review |
| [#7401](https://github.com/agentscope-ai/QwenPaw/pull/7401) | UNDER REVIEW | 2026-08-29 | Windows ACP Agent 启动阻塞修复，影响 Windows 用户 |
| [#6399](https://github.com/agentscope-ai/QwenPaw/pull/6399) | UNDER REVIEW | 2026-07-23 | ReMe Reranker UI 配置面板，长期待审 |
| [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) | OPEN | 2026-09-02 | A2A 协议支持计划，需官方回复 |

---

**报告生成时间**：2026-09-03  
**数据范围**：过去 24 小时（2026-09-02 ~ 2026-09-03）  
**项目健康度评估**：🟢 活跃 — 新版本发布后社区反馈集中，Bug 修复节奏较快，安全相关 Issue 需持续关注。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-09-03

---

## 一、今日速览

过去 24 小时内 ZeroClaw 保持高活跃度：共新增/更新 Issues 50 条、PR 50 条，无任何新版本发布。架构层 RFC 讨论持续升温，今日最突出的是 **RFC-9487（会话持久化所有权）** 与 **RFC-10526（Append-only 事件历史）** 两条并行提案，均指向 session 合约层的根本重构。安全侧出现一个 P1 级委托绕过漏洞（#10165），对应的修复 PR #10188 已在处理中。整体项目健康度良好，但安全问题值得 maintainer 重点关注。

---

## 二、版本发布

今日无新版本发布。

---

## 三、项目进展

### 已关闭的 Issue（近 24h 完成）

| Issue | 类型 | 说明 |
|-------|------|------|
| [#10510](https://github.com/zeroclaw-labs/zeroclaw/issues/10510) | docs/ci | 升级 mdBook 至 0.5.4，新增键盘可访问图片缩放 |
| [#10243](https://github.com/zeroclaw-labs/zeroclaw/issues/10243) | refactor | 退役废弃的 HMAC node_transport 模块 |
| [#10193](https://github.com/zeroclaw-labs/zeroclaw/issues/10193) | bug | 修复 Matrix 流式推理与思考状态文本碰撞问题 |
| [#10147](https://github.com/zeroclaw-labs/zeroclaw/issues/10147) | bug | 修复 CLI 跨进程配置初始化无法完成的问题 |
| [#9760](https://github.com/zeroclaw-labs/zeroclaw/issues/9760) | bug | Quickstart 表单补齐 channel descriptor 默认值展示 |
| [#10456](https://github.com/zeroclaw-labs/zeroclaw/issues/10456) | bug | 修复 MCP SSE 持久化读取器在超大事件后错误恢复的行为 |
| [#10286](https://github.com/zeroclaw-labs/zeroclaw/issues/10286) | bug | 修复 ZeroCode transcript 恢复后历史裁剪导致条目丢失的问题 |

### 今日新开的重点 PR

- **[PR #10568](https://github.com/zeroclaw-labs/zeroclaw/pull/10568)** — 修复 `readReaderScale` 四舍五入导致 `0.85` 被还原为 `0.9` 的回归问题（XS，今日新建）
- **[PR #10519](https://github.com/zeroclaw-labs/zeroclaw/pull/10519)** — 修复 `llm_task` 注册时丢弃 provider alias，导致模型提供者构造错误（风险：高，今日新建）
- **[PR #10567](https://github.com/zeroclaw-labs/zeroclaw/pull/10567)** — 记忆召回条目增加时间戳标注，解决久远条目与新鲜条目无法区分的问题
- **[PR #10563](https://github.com/zeroclaw-labs/zeroclaw/pull/10563)** — 检测模型声称执行了工具但未真正调用（hallucination 防护）

---

## 四、社区热点

### 🔥 评论数 Top Issues（今日仍在活跃讨论）

| Issue | 标题 | 评论数 | 核心焦点 |
|-------|------|--------|----------|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC: Runtime-owned conversation sessions & transport adapters | 32 | Rev.5 替代 Rev.4，需重新开启投票窗口 |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | RFC: Decouple memory lifecycle from storage backends | 25 | 明确 Memory trait 边界，避免各 gateway 重复实现 |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | RFC: Granular sandbox policy — 文件/网络细粒度限制 | 22 | 解决 application-layer 与 OS sandbox 策略长期漂移 |
| [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) | RFC: 分离权威记忆存储与可选 enrichment connectors | 19 | 存储/增强架构边界，2026-08-22 维护者接管 |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) | RFC: Wire protocol 作为 provider 构造一等公民 | 19 | 协议优先设计，Rev.2026.08.28 |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | RFC: Desktop computer-use 支持 | 16 | Rev.2 — 安全边界与 session arming 澄清 |
| [#9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) | Tracker: Session-persistence contract 所有权 | 15 | 四条工作流触碰同一合约，无明确所有者 |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker: Maintainer RFC 决策队列 | 14 | 决策积压治理机制 |

**热点分析：** 社区当前最关注的是 **session 持久化合约重构**（#9487、#9600、#10526 三条交织），以及 **内存/沙箱策略解耦**（#6850、#6996）。这表明项目已进入"架构治理期"——大量 RFC 等待决策，维护者决策队列（#8692）压力较大。

---

## 五、Bug 与稳定性

### 当前开放的高优先级 Bug

| Issue | 严重程度 | 标题 | Fix PR |
|-------|----------|------|--------|
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | **S0 安全风险** | 独立 delegate 绕过 `block_high_risk_commands` | [PR #10188](https://github.com/zeroclaw-labs/zeroclaw/pull/10188) 已在处理 |
| [#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559) | S1 工作流阻断 | Web _dashboard 关闭后 agent 停止工作 | 无 |
| [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | S2 降级 | 交互式会话上下文被硬编码限制 32K token | [PR #9535](https://github.com/zeroclaw-labs/zeroclaw/pull/9535)（按模型窗口比例压缩） |
| [#10523](https://github.com/zeroclaw-labs/zeroclaw/issues/10523) | S2 降级 | Bootstrap 文件 6000 字符截断对操作员不可见 | 无 |
| [#10501](https://github.com/zeroclaw-labs/zeroclaw/issues/10501) | P1 | MCP 图片工具结果在 OpenAI 兼容 provider 返回 400 | [PR #10566](https://github.com/zeroclaw-labs/zeroclaw/pull/10566) 已创建 |

**重点关注：** #10165 是今日最高风险项——delegate 安全策略绕过意味着恶意 agent 可执行 `rm` 等高危命令。PR #10188 正在修复此问题，建议 maintainer 优先 review。

---

## 六、功能请求与路线图信号

| RFC/Issue | 诉求 | 对应 PR | 纳入概率 |
|-----------|------|---------|----------|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | Runtime _owned 会话 + transport 适配层 | — | 高（已在 Rev.5，等待投票） |
| [#10526](https://github.com/zeroclaw-labs/zeroclaw/issues/10526) | Append-only 事件历史 + 确定性状态重放 | — | 中（刚提出，需 maintainer review） |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) | Gateway 直接透传消息（不经 agent turn） | — | 中 |
| [#9975](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) | Web bundle/daemon 兼容性契约 | — | 中 |
| [#10222](https://github.com/zeroclaw-labs/zeroclaw/issues/10222) | 交互式 agent 单工具轮次 opt-in | — | 待定 |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | Desktop computer-use 支持 | — | 高（Rev.2，安全澄清已完成） |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) | WASM Observer 生命周期订阅 | — | 中 |

**路线图信号：** 项目正在向"会话层重构"和"沙箱精细化治理"两个方向同时推进，预计未来 1-2 个版本会集中处理这些架构变更。

---

## 七、用户反馈摘要

**🔴 痛点：**
- **#10165**：用户反映 delegate 安全策略形同虚设，`block_high_risk_commands` 在独立 delegate 模式下被绕过，直接威胁数据安全
- **#8559**：Web Dashboard 用户反馈关闭聊天窗口后 agent 任务中断，导致长期运行任务无法后台执行
- **#10068**：配置了 `max_context_tokens = 131072` 但交互会话仍被硬限制在 32K，用户认为配置无效
- **#10523**：Bootstrap 文件截断无警告，用户排查困难

**🟢 正面反馈（隐含）：**
- [#9739](https://github.com/zeroclaw-labs/zeroclaw/pull/9739)、[#9353](https://github.com/zeroclaw-labs/zeroclaw/pull/9353) 多会话 Tab 功能持续获得关注，用户需要 per-agent 独立会话
- [#9745](https://github.com/zeroclaw-labs/zeroclaw/pull/9745)、[#9746](https://github.com/zeroclaw-labs/zeroclaw/pull/9746) 知识图谱与 session 工具的 per-agent 权限隔离被认可

---

## 八、待处理积压

| Issue/PR | 状态 | 提醒 |
|----------|------|------|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | Rev.5 待投票 | 32 条评论，Rev.4 反对票未继承，需维护者开启新投票窗口 |
| [#9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) | Tracker 无所有者 | 四条工作流修改同一合约，亟需指定合约 owner |
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | S0 安全漏洞 | PR #10188 待 review，建议优先处理 |
| [#10526](https://github.com/zeroclaw-labs/zeroclaw/issues/10526) | 新建 RFC | 刚提出，需 maintainer review 后决定是否纳入流程 |
| [#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559) | S1 无修复 PR | Web Dashboard agent 中断问题长期未解决，用户影响面大 |

---

**报告生成时间：** 2026-09-03 | **数据来源：** [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw) GitHub API

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*