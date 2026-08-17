# OpenClaw 生态日报 2026-08-17

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-17 01:42 UTC

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



# OpenClaw 项目日报 | 2026-08-17

---

## 1. 今日速览

过去24小时项目保持高强度活跃：共产生 500 条 Issue 更新（454 新开/活跃，46 已关闭）及 500 条 PR 更新（116 条已合并/关闭，384 条待合并）。今日无正式版本发布，但发布了一组 Gateway 性能分析数据（PR #124528），用于事件循环热点对比。社区核心关注点集中在**消息丢失（message-loss）**与**子代理状态丢失**两大稳定性顽疾，多个 P1 级 Issue 评论数持续增长。整体项目健康度：核心通道稳定性仍有压力，但维护者在安全、审计、类型重构等基础设施层面推进明显。

---

## 2. 版本发布

> 今日无正式版本发布。

**性能分析归档：**
- **PR #124528** — Gateway profile evidence：发布来自三节点、十二并发轮次 Gateway 工作负载的 CPU profile 数据，用于事件循环热点对比分析。存档包含 Gateway profile 的 before/after 快照，为后续性能优化提供基准。

---

## 3. 项目进展

**今日合并/关闭的重要 PR：**

| PR | 类型 | 摘要 |
|---|---|---|
| [#116489](https://github.com/openclaw/openclaw/pull/116489) ✅ | feat(security) | 安装策略警告需人工确认——外部 `security.installPolicy` 命令可返回 `warn`，CLI 安装时展示原因并要求精确目标名确认 |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) ✅ | feat(ui) | Control UI 支持审查安装策略警告，`plugins.install` 新增 `acknowledgeInstallPolicyWarning: true` 字段 |

**今日活跃关键 PR（待合并）：**

| PR | 评级 | 摘要 |
|---|---|---|
| [#124891](https://github.com/openclaw/openclaw/pull/124891) 🔴 P1 | 修复控制平面轮询卡顿，解决多秒级 UI/RPC 停滞问题 |
| [#124963](https://github.com/openclaw/openclaw/pull/124963) | Agent 创建请求溯源保留，解决委托工具创建时来源被覆盖问题 |
| [#124961](https://github.com/openclaw/openclaw/pull/124961) | Zod 类型验证重构 Wave 2，统一持久化边界校验 |
| [#97485](https://github.com/openclaw/openclaw/pull/97485) | Agent 循环迭代预算，防止 tool-calling 无限循环 |
| [#112811](https://github.com/openclaw/openclaw/pull/112811) | Teams 多机器人账号支持 |
| [#123709](https://github.com/openclaw/openclaw/pull/123709) | 出站消息投递审计追踪 |
| [#124913](https://github.com/openclaw/openclaw/pull/124913) | TTS 结构化回复字段支持 |
| [#96513](https://github.com/openclaw/openclaw/pull/96513) | 飞书出站消息速率控制 |
| [#103845](https://github.com/openclaw/openclaw/pull/103845) | 修复 daemon 生成的 service env 文件中 JSON 引号值错误 |
| [#124083](https://github.com/openclaw/openclaw/pull/124083) | 修复 Android 实时麦克风音频重采样问题 |
| [#124914](https://github.com/openclaw/openclaw/pull/124914) | 修复大堆 Gateway RSS 诊断日志重复问题 |
| [#124951](https://github.com/openclaw/openclaw/pull/124951) | 修复 SQLite 升级时 Unicode session 丢失问题 |
| [#124947](https://github.com/openclaw/openclaw/pull/124947) | 修复 Codex 和受限 profile 中 plugin tools 消失问题 |
| [#124659](https://github.com/openclaw/openclaw/pull/124659) | 修复 managed Gateway 更新时重复 successor 进程竞争问题 |
| [#124954](https://github.com/openclaw/openclaw/pull/124954) | 修复多 agent 配置下 `agentId` 解析丢失问题 |

> **项目推进评估：** 今日维护者重点推进了**安全性（安装确认）**、**可观测性（审计/追踪）**、**类型安全（Zod 重构）** 及多个 P1 级稳定性修复，整体向生产可用方向稳步前进。

---

## 4. 社区热点

**评论数 Top Issue（活跃讨论）：**

| Issue | 评论 | 评级 | 核心诉求 |
|---|---|---|---|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | 97 | 🔴 P1 🦞 | **#116277 关闭后静默回复失败仍复发**，监控 cron 持续记录新发生 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 31 | 🔴 P1 🦞 | **子代理完成结果静默丢失**，无重试、无通知、无自动重启 |
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | 26 | 🟡 P2 | **Gateway 层 per-agent 成本预算强制限制**，防止 runaway spend |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | 21 | 🔴 P1 🦞 | **Steer 模式无法在 turn 中途注入消息**，消息被队列延迟到 turn 结束后 |
| [#22438](https://github.com/openclaw/openclaw/issues/22438) | 19 | 🟡 P2 | **分级 bootstrap 文件加载**，减少大 workspace 上下文浪费 |

**热门 PR 讨论：**
- [#124891](https://github.com/openclaw/openclaw/pull/124891) — 控制平面轮询卡顿修复，多位共享 Gateway 运营方关注
- [#97485](https://github.com/openclaw/openclaw/pull/97485) — Agent 迭代预算，生产环境 tool-loop 失控问题的潜在解决方案

---

## 5. Bug 与稳定性

**P1 级严重问题（按关注排序）：**

| Issue | 摘要 | Fix PR |
|---|---|---|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | 静默回复失败在 #116277 关闭后仍持续发生，消息丢失 | 暂无 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 子代理完成结果静默丢失，多种失败模式（E31/E42/E45） | 部分相关：[#92433](https://github.com/openclaw/openclaw/issues/92433) ✅ 已关闭 |
| [#87744](https://github.com/openclaw/openclaw/issues/87744) | Codex-backed Telegram turns 反复超时，无法到达 turn/completed | 暂无 |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | WhatsApp 1:1 入站图片导致主通道卡死 ~3 分钟，多模态注入阻塞 | 暂无 |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | 2026.3.2 升级后 google-vertex/gemini-3.1-pro-preview 报 "Cannot convert undefined or null to object" | 暂无 |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | Session 转录投影在高写入负载下 livelock，阻塞事件循环数十秒 | 暂无 |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | 大 SQLite 转录归档阻塞 Gateway 事件循环 | 暂无 |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | 长对话后 write/exec tool 参数静默丢失（空 arguments） | 暂无 |
| [#87561](https://github.com/openclaw/openclaw/issues/87561) | 多渠道 final fallback 投递语义未定义，用户端静默 | 暂无 |
| [#46786](https://github.com/openclaw/openclaw/issues/46786) | `tools.elevated.enabled: true` 导致所有 exec 路由到 gateway 而非 sandbox | 暂无 |
| [#95553](https://github.com/openclaw/openclaw/issues/95553) | Pre-flight compaction 硬限制 ~60s，忽略 `compaction.timeoutSeconds` 配置 | 暂无 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | OpenClaw 泄漏未 reap 的 hook/tool 子进程，zombie 累积导致运行时退化 | 暂无 |
| [#108865](https://github.com/openclaw/openclaw/issues/108865) | Session 归档后飞书等渠道入站消息静默丢弃，无自动恢复机制 | 暂无 |
| [#48709](https://github.com/openclaw/openclaw/issues/48709) | Gemini 2.5 Pro textSignature 膨胀 + think tags 导致 session 失败 | 暂无 |
| [#88079](https://github.com/openclaw/openclaw/issues/88079) | WebChat 中 Kimi Code / DeepSeek Reasoner 的 reasoning_content 未流式渲染 | 暂无 |
| [#117609](https://github.com/openclaw/openclaw/issues/117609) | 瞬时 LLM/socket 错误在 embedded-assistant 阶段不重试，长 turn 直接死亡 | 暂无 |

**中优先级 Bug：**
- [#45494](https://github.com/openclaw/openclaw/issues/45494) — Cron agent jobs 在 LLM API 持续 500 时不 fast-fail 而耗尽 timeout
- [#114612](https://github.com/openclaw/openclaw/issues/114612) — memory_index_chunks + memory_embedding_cache 无保留策略，磁盘无限增长
- [#50165](https://github.com/openclaw/openclaw/issues/50165) — 子代理 UI 显示已完成但实际委托工作未完成
- [#56217](https://github.com/openclaw/openclaw/issues/56217) — 1Password secret provider 失败导致 gateway crash-loop 耗尽 rate limit
- [#74378](https://github.com/openclaw/openclaw/issues/74378) — Windows 上 CLI 命令执行后 node.exe 进程残留
- [#62328](https://github.com/openclaw/openclaw/issues/62328) — node:sqlite 缺少 FTS5 模块，memory search 关键词回退失效
- [#112196](https://github.com/openclaw/openclaw/issues/112196) — memory_search 瞬时同步超时被误报为持久 provider 失败

---

## 6. 功能

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-08-17 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026年8月，个人AI助手/自主智能体开源生态呈现**多极分化、技术收敛**态势：OpenClaw 与 Hermes Agent 作为头部项目持续高投入迭代，ZeroClaw 在安全架构与RFC治理上形成差异化竞争力，LobsterAI 与 CoPaw 则深耕垂直场景（企业协作、教育工具链）。生态整体从"功能堆砌期"迈入"生产稳定性攻坚期"——消息丢失、工具调用崩溃、资源泄漏成为多项目共同痛点，而安全加固（插件隔离、SSRF防护、权限收紧）与可观测性建设成为本月主旋律。

---

## 2. 各项目活跃度对比

| 项目 | Issue（新开/活跃/关闭） | PR（待合并/已合并） | Release | 健康度 |
|------|------------------------|-------------------|---------|--------|
| **OpenClaw** | 454 / — / 46 | 384 / 116 | ❌ | 🟡 核心通道承压，基础设施稳步推进 |
| **Hermes Agent** | 50 / — / — | 50 / — | ✅ v0.20.2 | 🟢 密集修复期，bug密度偏高但可控 |
| **ZeroClaw** | 48 / — / — | 50 / — | ❌ | 🟢 安全架构里程碑落地，测试稳定性攻坚中 |
| **NanoBot** | 11 / — / 4 | 499 / 1 | ❌ | 🟡 社区参与度高，工程吞吐受审查瓶颈制约 |
| **NanoClaw** | — / — / — | 19 / 13 | ❌ | 🟢 高投入冲刺期，跨会话+投递稳定性为核心 |
| **LobsterAI** | 10 / — / 3 | 17 / 9 | ❌ | 🟡 安全加固+协作体验并行，长期积压需关注 |
| **CoPaw** | 12 / — / 4 | 11 / 2 | ❌ | 🟢 关键bug修复闭环，待合并PR质量较高 |
| **Moltis** | 3 / — / 1 | 6 / 5 | ❌ | 🟢 稳健开发，核心模块质量持续提升 |
| **IronClaw** | 1 / — / — | 9 / — | ❌ | 🟢 稳定维护状态，无紧急问题 |
| **PicoClaw** | 3 / — / — | 4 / 1 | ❌ | 🟢 安全+功能扩展双线推进，积压待review |
| **NullClaw** | — | — | — | ⚪ 无活动 |
| **ZeptoClaw** | — | — | — | ⚪ 无活动 |

---

## 3. OpenClaw 在生态中的定位

**体量与影响力**：OpenClaw 以 500 级 Issue/PR 单日吞吐远超其他项目（NanoBot PR 待合并 499 条，但合并仅 1 条），是生态中**工程规模与社区参与度最高**的平台型项目。

**技术路线差异**：
- **vs Hermes Agent**：OpenClaw 聚焦 Gateway 事件循环稳定性与多通道路由，Hermes 聚焦桌面端体验与 Bot-to-Bot 多 Agent 协议；两者均面临消息丢失问题，但 OpenClaw 的 P1 问题（静默回复失败 #121058、子代理状态丢失 #44925）影响面更广。
- **vs ZeroClaw**：ZeroClaw 走安全架构先行路线（插件 egress 三阶段落地、WASM 沙箱），OpenClaw 更注重生产可用性的渐进式加固。
- **vs NanoClaw/NanoBot**：三者均面向个人助手场景，但 NanoClaw 侧重跨会话上下文与投递可靠性，NanoBot 侧重 Token 成本管理与 MCP 生态，OpenClaw 覆盖最全通道类型与企业级部署需求。

**社区规模对比**（基于 Issue/PR 量级估算）：
OpenClaw ≈ Hermes Agent > ZeroClaw > LobsterAI > NanoClaw > CoPaw > PicoClaw > IronClaw > Moltis

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|---------|---------|
| **消息/结果丢失与静默失败** | OpenClaw (#121058, #44925)、NanoBot (#4864)、Hermes Agent (#87368)、NanoClaw (#3254) | 子代理完成结果丢失、工具调用死循环、静默投递失败，多项目复现同类问题 |
| **安全加固（插件隔离/权限收紧）** | ZeroClaw (#9580)、PicoClaw (#3322-#3324)、Hermes Agent (#88058)、LobsterAI (#1831-#1833)、NanoClaw (#3260) | 插件 egress 默认拒绝、SSRF 防护、IPC 越权限制、exec 策略收紧 |
| **可观测性与成本透明** | NanoBot (#5266)、OpenClaw (#121058)、CoPaw (#7075)、Hermes Agent (#87479) | Token 消耗明细日志、定时任务运行状态展示、缓存泄漏监控 |
| **跨会话/多 Agent 协作** | NanoClaw (#3257)、OpenClaw (#112811 Teams)、Hermes Agent (#87886 Bot Mode)、ZeroClaw (#10025 swarm) | 上下文 fan-out、会话历史 backfill、Agent 间消息路由 |
| **渠道能力扩展** | PicoClaw (#3299 Exa)、LobsterAI (#1682 语音)、NanoBot (MCP扩展)、ZeroClaw (#8780 Gemini Live) | 搜索 provider、TTS/实时语音、MCP 工具生态 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构特征 |
|------|---------|---------|-------------|
| **OpenClaw** | 全通道网关 + 企业级稳定性 | 生产环境部署者、多通道集成需求 | 事件循环架构，Gateway 为核心，重测试覆盖 |
| **Hermes Agent** | 桌面端 + Bot-to-Bot 协议 | 个人用户、多 Agent 协作实验者 | Electron + Python 混合架构，插件化 System Prompt |
| **ZeroClaw** | 安全沙箱 + RFC 治理 | 安全敏感用户、架构研究者 | WASM 插件、WASI 网络隔离、社区驱动 RFC 流程 |
| **NanoBot** | Token 成本优化 + MCP 生态 | 重度用户、成本敏感型 | 紧凑架构，MCP 工具链深度集成 |
| **NanoClaw** | 跨会话上下文 + 投递可靠性 | 多 Agent 群组协作 | 强类型（Rust/Zig）、双阶段批次选择 |
| **LobsterAI** | 企业协作 + Agent 模板 | 中文企业用户、有道生态 | Electron + React，模板导入/导出 |
| **CoPaw** | 教育工具链 + 定时任务 | 教育场景、AgentScope 生态 | Python 为主，AgentScope 集成 |
| **Moltis** | CalDAV + Vault 安全 | 日历集成需求、密钥管理 | Rust 核心，RFC 4791 查询优化 |
| **IronClaw** | Slack/企业 IM 集成 | 小型团队 | Rust，稳定维护模式 |
| **PicoClaw** | 多渠道适配 + 搜索扩展 | 轻量级部署 | Go，SSRF 加固快速响应 |

---

## 6. 社区热度与成熟度分层

**🔴 快速迭代期（高吞吐 + 问题密集）**
- **OpenClaw**：500 级活动量，P1 问题持续累积，处于功能扩张后的稳定性收敛期
- **Hermes Agent**：v0.20.2 发布后进入密集修复，bug 密度偏高但修复节奏快
- **ZeroClaw**：安全架构里程碑落地 + 测试基础设施攻坚双线并行

**🟡 活跃发展期（中等吞吐 + 方向明确）**
- **NanoBot**：社区参与度高但工程吞吐受审查瓶颈制约，处于功能积累阶段
- **NanoClaw**：单日 32 PR 高强度冲刺，跨会话上下文为核心方向
- **LobsterAI**：安全加固+协作体验双主线，但存在 4 个月积压 PR 需关注

**🟢 稳健成熟期（低吞吐 + 高质量维护）**
- **CoPaw**：关键 bug 修复闭环，待合并 PR 质量高，架构重构推进中
- **Moltis**：核心模块（网关/CalDAV/Vault）质量持续提升，技术债务可控
- **IronClaw**：稳定维护状态，无紧急问题，依赖治理为主

**🟡 早期/ niche 期**
- **PicoClaw**：安全修复与功能扩展并行，维护窗口明确

---

## 7. 值得关注的趋势信号

| 趋势 | 信号来源 | 对开发者的参考价值 |
|------|---------|------------------|
| **消息丢失成为行业共性顽疾** | OpenClaw #121058/#44925、NanoBot #4864、Hermes #87368 | 设计 Agent 系统时需将"结果确认+重试+通知"作为一等公民，不能假设工具调用必然成功 |
| **安全架构从被动修补转向主动设计** | ZeroClaw 插件 egress 三阶段、PicoClaw SSRF 加固、LobsterAI 敏感日志脱敏 | 新项目建设应前置安全边界设计（默认拒绝、沙箱隔离），而非事后打补丁 |
| **跨会话上下文管理成为多 Agent 协作基础设施** | NanoClaw #3257、OpenClaw #112811、Hermes Bot Mode | 多 Agent 系统需统一解决历史序列化、上下文 fan-out、echo pruning 等基础问题 |
| **可观测性从可选变为刚需** | NanoBot #5266、CoPaw #7075、Hermes #87479 | 生产部署需内置 Token 成本、任务状态、缓存增长的可视化能力 |
| **生态兼容性竞争加剧** | ZeroClaw #8603 Chat Completions profile、NanoBot MCP 扩展 | 支持主流协议（OpenAI Chat Completions、MCP）可降低用户迁移成本，是生态扩张的关键杠杆 |
| **稳定性修复 > 新功能开发** | OpenClaw P1 问题持续、Hermes bug 密度高、CoPaw 崩溃修复 | 社区对"能用"的容忍度降低，建议新入局者优先解决工具调用可靠性与资源泄漏问题 |

---

**总结**：2026年8月的开源 AI 助手生态正从"功能竞赛"转向"质量竞赛"。OpenClaw 与 Hermes Agent 作为头部玩家在稳定性攻坚上投入巨大，ZeroClaw 以安全架构形成差异化，而中腰部项目（NanoClaw、CoPaw、Moltis）在垂直方向上建立护城河。对开发者而言，消息丢失、资源泄漏、可观测性不足是当前最需要优先解决的三大共性挑战。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 (2026-08-17)

## 1. 今日速览
过去24小时 NanoBot 社区活跃度维持高位，共产生 **15 条 Issue**（11 新开/活跃、4 已关闭）与 **500 条 PR**（499 待合并、1 已合并/关闭）。项目当前聚焦于 **Token 成本管理、MCP 生态扩展、频道能力补齐** 三大方向。值得注意的是，PR 合并流速（24h 仅 1 条）与提交量存在显著剪刀差，维护者审查带宽成为当前制约版本迭代的主要瓶颈。整体健康度：社区参与度高，但工程吞吐面临积压压力。

## 2. 版本发布
- **无新版本发布**。过去24小时未触发 Release 流程，所有更新仍以 PR 合并与 Issue 修复形式推进。

## 3. 项目进展
- **合并/关闭动态**：过去24小时仅有 **1 条 PR 完成合并/关闭**（[PR #4329](https://github.com/HKUDS/nanobot/pull/4329) 被标记关闭，其内容已由 [PR #5406](https://github.com/HKUDS/nanobot/pull/5406) 接管，避免重复提交污染 `main` 分支）。
- **Issue 修复进展**：4 条 Issue 已进入 Closed 状态，覆盖 **安全漏洞**（[Issue #5305](https://github.com/HKUDS/nanobot/issues/5305) `exec.allowPatterns` 绕过）、**调度器稳定性**（[Issue #5373](https://github.com/HKUDS/nanobot/issues/5373) cron 持久化失败崩溃）、**模型回归**（[Issue #2185](https://github.com/HKUDS/nanobot/issues/2185) Gemini Flash Preview 兼容性）及 **渠道上下文对齐**（[Issue #5275](https://github.com/HKUDS/nanobot/issues/5275) Matrix 线程上下文）。表明核心缺陷与安全问题的修复节奏正常。
- **整体推进**：项目在本期主要处于“问题收敛 + 长尾 PR 积累”阶段，新功能 PR（如 TypeScript TUI、WebUI 协作、KV Cache 优化）已就绪但待审查队列阻塞，尚未形成可发布的版本合力。

## 4. 社区热点
| 热度 | 类型 | 标题 | 评论/状态 | 链接 |
|------|------|------|-----------|------|
| 🔥 高 | Issue | Architectural issue: nanobot does not preserve the exact prompt prefix | 15 评论 / Open | [Issue #2463](https://github.com/HKUDS/nanobot/issues/2463) |
| 🔥 高 | Issue | Logs about token consumption (too many tokens are burned) | 14 评论 / Open | [Issue #5266](https://github.com/HKUDS/nanobot/issues/5266) |
| 🔥 中 | Issue | Endless loop for `<function=complete_goal>` | 7 评论 / Open / 👍1 | [Issue #4864](https://github.com/HKUDS/nanobot/issues/4864) |

**热点分析**：
- **#2463** 触及项目架构根基：对话历史序列化与实际 Prompt Prefix 不一致，直接影响 OpenAI 兼容链路的缓存命中与成本预测，长期未决（2026-03 开单）引发核心维护者关注。
- **#5266** 反映企业/重度用户对 **Token 可观测性** 的迫切需求，当前无内置计费/调用明细日志，导致异常消耗难以定位。
- **#4864** 为网关层工具序列化回归，直接导致 Agent 陷入死循环，获得首条 👍 支持，说明该问题已实际影响生产稳定性。

## 5. Bug 与稳定性
按严重程度排序（均为 Open）：

| 严重度 | Issue | 问题描述 | 状态 |
|--------|-------|----------|------|
| 🔴 高 | [Issue #4864](https://github.com/HKUDS/nanobot/issues/4864) | `complete_goal` 工具调用陷入死循环，网关将 `recap` 参数解析为裸字符串而非 JSON，疑似近期工具序列化改动引入 | Open |
| 🟠 中 | [Issue #5402](https://github.com/HKUDS/nanobot/issues/5402) | Token 合并机制永远无法触发，`tiktoken` 估算值持续低于 API 实际返回量 | Open |
| 🟠 中 | [Issue #5377](https://github.com/HKUDS/nanobot/issues/5377) | 合并截断后 `Session.last_consolidated` 指针前移超出实际移除范围，导致部分历史消息永久丢失 | Open |

> ✅ 已修复：[Issue #5305](https://github.com/HKUDS/nanobot/issues/5305)（安全绕过）、[Issue #5373](https://github.com/HKUDS/nanobot/issues/5373)（Cron 调度崩溃）、[Issue #2185](https://github.com/HKUDS/nanobot/issues/2185)（模型兼容回归）。

## 6. 功能请求与路线图信号
**用户诉求集中区**：
- **[Issue #5251](https://github.com/HKUD

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报 — 2026-08-17

---

## 1. 今日速览

Hermes Agent 在过去 24 小时内保持**极高活跃度**：50 条 Issue 更新、50 条 PR 更新、1 个新版本发布。核心亮点是 v0.20.2 patch 版本的稳定化发布，累积了约 397 个 PR 的合并成果。今日社区焦点集中在三类问题：**文件描述符泄漏**（#88033、#88063）、**后台 review 与会话上下文断裂**（#87368、#88053）、以及 **Windows 桌面端自动更新路径的破坏性缺陷**（#87331、#87304）。同时 Bot Mode 正式并入桌面默认插件（#87886），标志着多 Agent 协作能力进入核心版本。

---

## 2. 版本发布

### v0.20.2（v2026.8.16）— Patch 稳定版

- **发布日期**：2026-08-16
- **性质**：补丁版本，累积 v0.20.1 以来约 397 个 PR
- **目标受众**：Docker 镜像、托管部署、全新安装用户
- **破坏性变更**：无
- **迁移注意**：直接升级即可；建议检查自 v0.20.1 以来的 cron 与 billing 相关行为变化

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#87886](https://github.com/NousResearch/hermes-agent/pull/87886) | Feature | **Bot Mode 正式捆绑为桌面内置默认插件**，bot-to-bot 协议从用户 SOUL.md 移入核心 system-prompt，覆盖所有 profile 的所有会话 |
| [#88056](https://github.com/NousResearch/hermes-agent/pull/88056) | Fix | Codex OAuth 上下文窗口提升至 **900K**（gpt-5.6/gpt-5.4 系列），适配 OpenAI ChatGPT 订阅的大上下文 rollout |
| [#88063](https://github.com/NousResearch/hermes-agent/pull/88063) | Fix | 修复废弃 SessionDB 实例泄漏文件描述符的问题，使空闲 accounting worker 可主动回收 |
| [#88050](https://github.com/NousResearch/hermes-agent/pull/88050) | Fix | 修复 gateway 被故意停止时 cron 重试风暴（OOF-266，5 个重复事故单） |
| [#88058](https://github.com/NousResearch/hermes-agent/pull/88058) | Security | 更新 Electron 40→41、NanoID 3.3.17→3.3.18，修复已知依赖漏洞 |
| [#88051](https://github.com/NousResearch/hermes-agent/pull/88051) | Fix | Kanban worktree 工作区现在在任务完成/归档时正确清理 |
| [#88062](https://github.com/NousResearch/hermes-agent/pull/88062) | Fix | Telegram adapter 懒重导入时重新绑定 TypeHandler，修复 PTB 不可用时名字解析回退问题 |
| [#84399](https://github.com/NousResearch/hermes-agent/pull/84399) | Fix | `config.yaml` 的 `model.temperature` 现已正确传递到 agent API 请求（此前静默丢弃） |
| [#87206](https://github.com/NousResearch/hermes-agent/pull/87206) | Fix | 修复桌面右侧面板拖拽时 sash 预览与最终位置不符的视觉错位 |
| [#6422](https://github.com/NousResearch/hermes-agent/pull/6422) | Fix | 飞书卡片操作回复现使用 `open_message_id`，修复 API 99992354 错误 |
| [#87755](https://github.com/NousResearch/hermes-agent/pull/87755) | Fix | Slack 原生任务卡片不再同时发送 `markdown_text` 和 `chunks`，修复渲染问题 |
| [#88048](https://github.com/NousResearch/hermes-agent/pull/88048) | Fix | SessionDB 支持上下文管理器协议（`with` 语句），作为 #88033 的文件描述符泄漏修复方案之一 |
| [#88027](https://github.com/NousResearch/hermes-agent/pull/88027) | Feature | **Devin ACP 作为一等公民 provider 接入**，支持别名 `devin`/`cognition`/`swe`/`devin-acp` |

**整体判断**：项目处于密集修复期，今日 7 个 PR 关闭 + 多个关键 P0/P1 有对应修复正在推进，健康度良好但 bug 密度偏高。

---

## 4. 社区热点

| 热度 | Issue/PR | 评论数 | 链接 | 核心诉求 |
|------|----------|--------|------|----------|
| 🔥 | #87559 ACP MCP 工具不可达 | 5 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87559) | Paseo daemon 注入的 MCP server 工具未进入可调用目录，影响 ACP 模式可用性 |
| 🔥 | #62158 桌面计时器重置 | 4（已关闭） | [Issue](https://github.com/NousResearch/hermes-agent/issues/62158) | 用户切换视图后耗时计数器归零，影响长时任务监控体验 |
| 🔥 | #87479 Telegram 状态消息缓存无限增长 | 3 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87479) | 多会话 Telegram 网关进程生命周期内 `_status_message_ids` 无容量上限，存在内存泄漏风险 |
| 🔥 | #87356 cronjob update schema 缺失 model/provider | 2 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87356) | 模型漂移防护无法通过 cronjob 工具触发，影响计费可控性 |
| 🔥 | #88012 honcho_search 始终返回空 | 2 | [Issue](https://github.com/NousResearch/hermes-agent/issues/88012) | `peer_perspective` 过滤器不受 Honcho 服务端支持，导致记忆检索功能失效 |

**热点分析**：社区关注点集中在**可观测性**（缓存泄漏、状态重置）和**核心功能链断裂**（MCP 工具注册、记忆检索）两类问题上，反映用户已从"能用"进入"生产部署"阶段，对稳定性要求显著提升。

---

## 5. Bug 与稳定性

### P0 级

| Issue | 标题 | 是否有 Fix PR | 链接 |
|-------|------|---------------|------|
| #87368 | 后台 review 丢弃 gateway 临时会话上下文，破坏 prompt-cache 前缀一致性 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87368) |

### P1 级

| Issue | 标题 | 是否有 Fix PR | 链接 |
|-------|------|---------------|------|
| #88033 | `hermes serve` 泄漏文件描述符至 EMFILE，SessionDB 永不清理 | ✅ [#88063](https://github.com/NousResearch/hermes-agent/pull/88063)、[#88048](https://github.com/NousResearch/hermes-agent/pull/88048) | [Issue](https://github.com/NousResearch/hermes-agent/issues/88033) |
| #87331 | Windows 桌面自动更新可销毁桌面构建（venv 锁被忽略） | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87331) |
| #87304 | Windows ZIP fallback 在依赖失败时触发，永久删除未提交更改 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87304) |
| #87488 | 无头审批升级永不解决：`approvals.timeout` 自动拒绝永不触发 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87488) |

### P2 级

| Issue | 标题 | 是否有 Fix PR | 链接 |
|-------|------|---------------|------|
| #87559 | ACP 提供的 MCP server 工具从未进入可调用目录 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87559) |
| #87497 | lifecycle_guard 嵌入式 NUL 字节仍可逃逸（#76762 修复不完整） | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87497) |
| #87503 | Codex OAuth refresh 仅写入 profile 级 auth store，全局 store 保留已消耗 token | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87503) |
| #87420 | `pre_tool_call` 指令聚合采用 first-valid-wins 语义，导致插件审批被遮蔽 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87420) |
| #87469 | 路由 profile 的后台 review 回执丢失 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87469) |
| #87319 | `transform_llm_output` 回调无保证的串行安全流水线 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87319) |
| #87509 | API server 会话无 cron_mode 审批豁免，陷入 approvals.timeout 等待 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87509) |
| #88053 | read-before-write 守卫拒绝所有后台 review skill 写入 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/88053) |
| #87248 | 桌面计费错误气泡在自动故障转移成功后仍永久保留 | 待确认 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87248) |

### P3 级（代表性）

| Issue | 标题 | 链接 |
|-------|------|------|
| #87479 | Telegram 状态消息缓存无上限增长 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87479) |
| #88012 | honcho_search peer_perspective 过滤不受支持 | [Issue](https://github.com/NousResearch/hermes-agent/issues/88012) |
| #85391 | WhatsApp 配对写入不同 session 目录，0 字节 creds.json 计为已配对 | [Issue](https://github.com/NousResearch/hermes-agent/issues/85391) |
| #87283 | Kanban 插件未声明 gateway 依赖和自动分发行为 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87283) |
| #87419 | Windows 破坏性命令（format C:、diskpart）仅为 dangerous 非 hardline，可绕过 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87419) |
| #87253 | 便携插件 MCP server 对 `hermes mcp` 命令不可见，OAuth 无法完成 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87253) |
| #87281 | Kanban notify-subscribe 省略 `--thread-id` 时静默发送至 Telegram DM 根频道 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87281) |
| #87502 | 两个内置 skill 违反 skill 工具自身强制的限额 | [Issue](https://github.com/NousResearch/hermes-agent/issues/87502) |
| #88064 | `skills.external_dirs` 为 package root 时 `/skill` 斜杠调用失败 | [Issue](https://github.com/NousResearch/hermes-agent/issues/88064) |

---

## 6. 功能请求与路线图信号

| 请求 | Issue/PR | 状态 | 分析 |
|------|----------|------|------|
| MAX（俄罗斯 VK 即时通讯）平台支持 | [#8

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-17

---

## 1. 今日速览

过去 24 小时内，PicoClaw 社区保持中等活跃度：新增 3 条 Issue 与 5 条 PR，其中 1 条 PR 已关闭（#3193），4 条待合并。今日无版本发布，但安全修复类 PR 集中出现（3 条来自同一作者的 SSRF 加固），反映出项目在渠道安全性方面正处于迭代阶段。整体项目健康度良好，Issue 与 PR 流转顺畅，主要维护窗口集中在安全与功能扩展两条主线。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已关闭 PR
- **[PR #3193](https://github.com/sipeed/picoclaw/pull/3193)** — 新增 `simplex` channel type  
  作者 `dim`，为项目扩展了新的通讯渠道支持，虽已关闭（可能已被合并或已放弃），但仍表明项目社区对多渠道接入持续活跃。

### 待合并 PR（4 条）
| PR | 作者 | 摘要 |
|----|------|------|
| [#3299](https://github.com/sipeed/picoclaw/pull/3299) | kesku | 原生支持 Exa 网页搜索 provider |
| [#3322](https://github.com/sipeed/picoclaw/pull/3322) | SashaMIT | 通用渠道媒体下载 SSRF 加固 |
| [#3323](https://github.com/sipeed/picoclaw/pull/3323) | SashaMIT | 修复 WeCom 媒体下载安全漏洞 |
| [#3324](https://github.com/sipeed/picoclaw/pull/3324) | SashaMIT | 修复 微信媒体下载安全漏洞 |

> **进展评估**：今日重点在于安全加固与搜索能力扩展，4 条待合并 PR 均已完成功能开发，处于 review 阶段，整体推进节奏稳健。

---

## 4. 社区热点

| 类型 | 编号 | 标题 | 评论数 | 链接 |
|------|------|------|--------|------|
| Issue | #3302 | Support OAuth 2.1 for MCP servers | 3 | [链接](https://github.com/sipeed/picoclaw/issues/3302) |
| Issue | #3325 | Render Telegram tables with rich messages | 1 | [链接](https://github.com/sipeed/picoclaw/issues/3325) |
| Issue | #3338 | Slack does not attach image media content | 0 | [链接](https://github.com/sipeed/picoclaw/issues/3338) |
| PR | #3299 | Add native Exa web search provider | — | [链接](https://github.com/sipeed/picoclaw/pull/3299) |

**热点分析**：
- **#3302** 评论最多（3 条），用户期望 MCP 服务器支持 OAuth 2.1，与 #2546 形成关联，体现用户对认证安全升级的持续诉求。
- **#3325** 反映用户希望 Telegram 支持原生表格渲染，说明现有 Markdown 表格在 Telegram 渠道的体验降级问题已引起关注。
- **#3299** Exa 搜索 provider 的引入是重要功能扩展，满足用户对 AI 工具集搜索能力的升级需求。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 标题 | 状态 | Fix PR | 链接 |
|----------|-------|------|------|--------|------|
| 🔴 高 | #3338 | Slack does not attach image media content | 新开 | 暂无 | [链接](https://github.com/sipeed/picoclaw/issues/3338) |

**详情**：Slack 媒体上传始终报错 `file.upload.v2: file size cannot be 0`，根因为 `SendMedia` 未设置 `FileSize` 字段，导致 SDK 在发送前拒绝请求。影响版本：`picoclaw 0.3+`。暂无关联修复 PR，需优先跟进。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 诉求摘要 | 纳入版本可能性 |
|----------|------|----------|----------------|
| [#3302](https://github.com/sipeed/picoclaw/issues/3302) | 功能请求 | MCP 服务器支持 OAuth 2.1 认证 | 中高（用户标注为 Nice-to-Have） |
| [#3325](https://github.com/sipeed/picoclaw/issues/3325) | 功能请求 | Telegram 原生表格渲染 | 中（Telegram API 10.1 已支持） |
| [#3299](https://github.com/sipeed/picoclaw/pull/3299) | 新功能 | Exa 网页搜索 provider | 高（已完成开发，待合并） |

**判断**：Exa 搜索已具备完整实现，预计下一版本即可纳入；OAuth 2.1 与 Telegram 表格渲染需求明确，但优先级较低，需结合 Roadmap 排期。

---

## 7. 用户反馈摘要

- **Slack 媒体上传失败**（#3338）：用户报告图片附件始终无法上传，报错指向 `FileSize` 未设置，属于直接阻断核心功能的使用问题。
- **Telegram 表格体验降级**（#3325）：用户反馈结构化 Markdown 表格在 Telegram 中降级为纯文本或等宽代码块，期望获得原生视觉表格 UI。
- **MCP OAuth 2.1 支持**（#3302）：用户希望 MCP 服务器端同步升级至 OAuth 2.1，关注认证安全能力的演进。
- **SSRF 安全加固**（#3322 / #3323 / #3324）：多渠道媒体下载存在重定向至内网的风险，用户（也是作者）主动提出加固方案，体现社区对安全问题的敏感度高。

---

## 8. 待处理积压

| 类型 | 编号 | 标题 | 创建时间 | 状态标签 | 链接 |
|------|------|------|----------|----------|------|
| Issue | #3302 | Support OAuth 2.1 for MCP servers | 2026-07-30 | stale | [链接](https://github.com/sipeed/picoclaw/issues/3302) |
| Issue | #3325 | Render Telegram tables with rich messages | 2026-08-09 | stale | [链接](https://github.com/sipeed/picoclaw/issues/3325) |
| PR | #3299 | Add native Exa web search provider | 2026-07-26 | — | [链接](https://github.com/sipeed/picoclaw/pull/3299) |
| PR | #3322 | fix(channels): block private targets on inbound media downloads | 2026-08-09 | stale | [链接](https://github.com/sipeed/picoclaw/pull/3322) |
| PR | #3323 | fix(wecom): use CreateSafeHTTPClient for media downloads | 2026-08-09 | stale | [链接](https://github.com/sipeed/picoclaw/pull/3323) |
| PR | #3324 | fix(weixin): use CreateSafeHTTPClient for media downloads | 2026-08-09 | stale | [链接](https://github.com/sipeed/picoclaw/pull/3324) |

> **维护者关注建议**：Issue #3302、#3325 及 4 条 PR 均已进入 `stale` 状态，建议尽快review并给出反馈；其中 #3299（Exa 搜索）与 #3322-#3324（SSRF 加固）价值明确，可优先处理。

---

*报告生成时间：2026-08-17 | 数据来源：PicoClaw GitHub 仓库（近 24 小时）*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目日报 — 2026-08-17

> 数据来源：github.com/qwibitai/nanoclaw  
> 统计窗口：2026-08-16 00:00 ~ 2026-08-17 00:00

---

## 1. 今日速览

今日 NanoClaw 项目活跃度**极高**：24 小时内产生 32 条 PR（19 条待合并、13 条已合并/关闭），是近期最高的单日 PR 量级。核心贡献者 `gavrielc` 主导了本轮迭代，主要聚焦于跨会话上下文管理、消息投递稳定性、渠道能力扩展及权限策略完善。无新版本发布，所有改动以 PR 形式进入主干。项目处于**高投入开发冲刺期**，技术债务清理与功能增强同步推进。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并 / 关闭的重要 PR（13 条）

| PR | 作者 | 摘要 |
|----|------|------|
| [#3283] [CLOSED] Preserve structured chat links | Koshkoshinsk | 修复 Chat SDK 链接富文本丢失问题，保留隐藏 URL 元数据 |
| [#3284] [CLOSED] Mid-turn streaming: single delivery door | gavrielc | 重构流式输出投递逻辑，确保 mid-turn 消息仅通过单一通道投递，消除重复 |
| [#3262] [CLOSED] Chat SDK bridge: DM-thread normalization | gavrielc | 扩展渠道桥接，支持 DM 线程上下文捕获与归一化 |
| [#3259] [CLOSED] skill-apply heading-ordinal strip | gavrielc | 修复技能引导步骤编号渲染错误 |
| [#3260] [CLOSED] `decline_notify` unknown-sender policy | gavrielc | 新增第四种未知发件人策略：礼貌拒绝 + 所有者 FYI 通知 |
| [#3261] [CLOSED] Optional adapter capabilities | gavrielc | 扩展渠道适配器能力注册表，支持 `setTyping`（带状态描述）、`setThreadTitle`、`setSuggestedPrompts` |
| [#3263] [CLOSED] Hot-start registered adapter | gavrielc | 新增 `startChannelAdapter(key)`，支持运行时热启动已注册适配器 |
| [#3264] [CLOSED] `registerDeliveryBatchPreview` hook | gavrielc | 新增投递前批量预览钩子，供模块预取扩展资源 |
| [#3265] [CLOSED] `suppressCreatedNotify` option | gavrielc | 新增 `createAgent` 选项，抑制终端创建成功消息 |
| [#3266] [CLOSED] `registerChannelCardInterceptor` seam | gavrielc | 新增渠道注册审批流拦截点，支持模块自定义审批行为 |
| [#1251] [CLOSED] Add `/add-openmail` skill | armandokun | 集成 OpenMail 邮件通道，支持三种模式（Channel / Tool+Notify / CLI） |
| [#3278] [CLOSED] `save_document` MCP tool (Story 1.1) | adar666 | 实现 Word/PDF 文档持久化至 Agent 内存的 MCP 工具 |

**整体推进评估：** 本轮迭代系统性完善了**跨会话上下文管理**（fan-out、backfill、echo pruning）和**消息投递可靠性**（two-phase batch selection、detached conversation 防护、streaming 单门控）。同时补齐了权限策略、渠道能力注册、适配器热启动等基础设施，项目向"多会话协作 + 高可靠投递"方向稳步推进。

---

## 4. 社区热点

### 当前待合并 / 开放的 PR（重点）

| PR | 作者 | 状态 | 说明 |
|----|------|------|------|
| [#3257] Cross-session context: fan-out, DM backfill, echo pruning | gavrielc | OPEN | 跨会话上下文核心模块，含 `ncl sessions history` 子命令 |
| [#3256] `messaging_groups.detached_at` 字段 + 投递防护 | gavrielc | OPEN | 数据库迁移 022，bot 被移除后拒绝向已脱离会话发送消息 |
| [#3255] Outbound delivery 修正 sender 解析逻辑 | gavrielc | OPEN | 修复多 bot 实例共享同一频道地址时的投递目标歧义 |
| [#3254] Two-phase inbound batch selection | gavrielc | OPEN | 修复 context 行积压挤压任务行的 bug，确保 pending 任务不被挤出批次 |
| [#3282] 接受 Telegram 配队码带空格输入 | amit-shafnir | OPEN | 修复 Telegram 配对码粘贴时因空格被拒绝的问题 |
| [#3281] 修复 agent-scoped `ncl tasks` 对旧版 session 不可见 | wakqasahmed | OPEN | 修复 `findTaskSessions()` 仅匹配 `messaging_group_id IS NULL` 导致 legacy session 被忽略的回归 |
| [#2752] Discord 入站附件仅暴露 URL | chubbicorn245 | OPEN | 修复 Discord 附件无法传递字节/路径，agent 仅见 `[file:...]` 占位符 |
| [#3280] `ncl groups config update` 无法清除 nullable scalar | stumpjumper | OPEN | 修复 `--model ""` 被存为字符串而非 NULL 的问题 |

**热点分析：**
- `gavrielc` 主导的 4 条核心 PR（#3254/#3255/#3256/#3257）构成一套完整的**跨会话 + 投递稳定性**改进包，彼此依赖，预计将作为一组联合作业合并。
- `#3281`（wakqasahmed）和 `#2752`（chubbicorn245）是社区贡献者提交的长期积压 Bug 修复，涉及版本回归和平台适配，修复后将显著提升多平台使用体验。
- `#3282` 是轻量 UX 修复，解决 Telegram 配对码空格问题，影响面小但用户体验敏感。

---

## 5. Bug 与稳定性

| 严重度 | Issue / PR | 描述 | Fix 状态 |
|--------|------------|------|----------|
| 🔴 高 | [#3281] | Agent-scoped `ncl tasks` 命令对 v2.1.54 之前的 legacy session 不可见，导致任务查询遗漏 | **已有 PR** [#3281](https://github.com/qwibitai/nanoclaw/pull/3281) |
| 🔴 高 | [#2752] | Discord 入站附件（图片/文本）无法传递字节/路径，agent 仅见占位符 | **已有 PR** [#2752](https://github.com/qwibitai/nanoclaw/pull/2752) |
| 🟡 中 | [#3280] | `ncl groups config update --model ""` 存为空字符串而非 NULL，导致运行时行为异常 | **已有 PR** [#3280](https://github.com/qwibitai/nanoclaw/pull/3280) |
| 🟡 中 | [#3254]（已合 PR 对应修复） | Two-phase batch selection 修复：context 行积压可挤出 pending 任务行，导致唤醒但无工作 | ✅ 已随 [#3254](https://github.com/qwibitai/nanoclaw/pull/3254) 合入 |
| 🟢 低 | [#3282] | Telegram 配对码带空格时被拒绝，粘贴体验差 | **已有 PR** [#3282](https://github.com/qwibitai/nanoclaw/pull/3282) |

> **稳定性评估：** 今日关闭的 13 条 PR 中包含多处投递可靠性修复（#3254/#3284/#3255/#3256），整体稳定性显著增强。仍有 2 个中高严重度 Bug（#3281/#2752）未合并，建议优先 review。

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 分析 |
|------|------|------|
| **跨会话协作能力** | [#3257] PR | fan-out / DM backfill / echo pruning 构成完整的 agent group 跨会话上下文机制，预计纳入下一正式版核心功能 |
| **OpenMail 邮件通道** | [#1251] PR（已合） | 社区贡献的 `/add-openmail` skill 已合入，暗示邮件通道正式支持 |
| **文档记忆持久化** | [#3278] PR（已合） | `save_document` MCP 工具（Story 1.1）已合入，Document Memory + Fill-In Editing 史诗进入实现阶段 |
| **渠道热启动** | [#3263] PR（已合） | `startChannelAdapter(key)` 支持运行时动态注册适配器，提升部署灵活性 |
| **`decline_notify` 权限策略** | [#3260] PR（已合） | 第四种 unknown_sender_policy 补充了"严格拒绝"与"审批"之间的中间选项 |
| **渠道能力扩展** | [#3261] PR（已合） | `setTyping`（带状态描述）/ `setThreadTitle` / `setSuggestedPrompts` 表明项目正向 richer channel interaction 演进 |

**路线图判断：** 当前迭代明显围绕 **"多 agent 协作 + 多平台稳定投递 + 文档记忆"** 三条主线推进，预计下一版本将重点包含跨会话上下文、OpenMail 支持和文档持久化能力。

---

## 7. 用户反馈摘要

| 反馈主题 | 来源 | 提炼 |
|----------|------|------|
| Telegram 配对体验差 | [#3282] | 平台展示带空格的 6 位码，用户粘贴原样输入时被拒绝，需容忍空格 |
| Discord 附件不可读 | [#2752] | 图片/文本附件仅以 `[file:...]` 占位符呈现，agent 完全无法处理内容，是 Discord 用户的长期痛点 |
| `ncl tasks` 遗漏旧 session | [#3281] | 升级至 v2.1.54+ 后，agent-scoped 任务命令无法覆盖 legacy session，导致任务查询不完整 |
| 配置更新无法清空字段 | [#3280] | `ncl groups config update` 缺少"清除"语义，`--model ""` 被当作空字符串而非 NULL，影响配置重置 |
| 聊天链接富文本丢失 | [#3283] | 平台显示文本与链接目标不一致时，结构化的 chat link 信息被截断 |

---

## 8. 待处理积压

| PR / Issue | 作者 | 创建时间 | 状态 | 备注 |
|------------|------|----------|------|------|
| [#3257] Cross-session context | gavrielc | 2026-08-15 | OPEN | 核心功能，待合并 |
| [#3256] `detached_at` 迁移 | gavrielc | 2026-08-15 | OPEN | 依赖 #3257 的数据库变更 |
| [#3255] Delivery sender 解析修正 | gavrielc | 2026-08-15 | OPEN | 多实例部署稳定性关键 |
| [#3254] Two-phase batch selection | gavrielc | 2026-08-15 | OPEN | 投递可靠性关键修复 |
| [#3281] Legacy session 任务不可见 | wakqasahmed | 2026-08-16 | OPEN | 社区贡献，版本回归修复，建议优先合并 |
| [#2752] Discord 附件 URL-only | chubbicorn245 | 2026-06-12 | OPEN | **积压超 2 个月**，Discord 用户高频痛点 |
| [#3282] Telegram 配对码空格 | amit-shafnir | 2026-08-16 | OPEN | 轻量修复，建议快速合并 |
| [#3280] Config update NULL 问题 | stumpjumper | 2026-08-16 | OPEN | CLI 行为修正，影响配置管理 |

> **维护者关注建议：**
> 1. `#2752`（Discord 附件）已开放超过 2 个月，建议优先 review 合并。
> 2. `#3254/#3255/#3256/#3257` 构成一组强依赖的跨会话 + 投递改进包，建议作为整体联合作业合并。
> 3. `#3281`（legacy session 回归）影响存量用户，建议高优先级处理。

---

*日报生成时间：2026-08-17*  
*分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目日报 — 2026-08-17

## 1. 今日速览

过去 24 小时 IronClaw 项目保持中低活跃度：共收到 1 条新 Issue 和 9 条 PR，无新版本发布。开发重点集中在依赖更新（6/9 PR 来自 Dependabot）和一项 Slack 体验优化修复。核心功能层面，PR #7651（确定性无结果抑制）和 #7682（Slack 私信连接）是推动功能改进的关键条目。项目整体处于**稳定维护状态**，无紧急 Bug 或回归问题。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 作者 | 内容 | 影响 |
|---|---|---|---|
| [#7632](https://github.com/nearai/ironclaw/issues/7632) | Dependabot | 升级 base64、toml、rstest、jsonschema | 依赖安全更新，低风险 |
| [#7683](https://github.com/nearai/ironclaw/issues/7683) | hanakannzashi | 移除已废弃的 IronLoop 网络设置字段 | 代码清理，保留现有角色行为 |

### 开放中的关键 PR

- **[PR #7682](https://github.com/nearai/ironclaw/issues/7682)** — `fix(slack): 将未链接用户连接提示改为私信，含一键连接链接`。直接响应 Issue #7681，修复 Slack 共享频道中连接提示公开暴露及手动多步跳转的 UX 痛点，预计合并后显著改善新用户 onboarding 体验。
- **[PR #7651](https://github.com/nearai/ironclaw/issues/7651)** — `feat(automations): 添加确定性无结果抑制`。由核心贡献者 serrrfirat 提交（XL 规模），实现基于用户措辞自动判断是否抑制通知的自动化逻辑，属于功能增强，可能纳入下一版本。

---

## 4. 社区热点

### 🔥 高关注度 Issue

**[Issue #7681](https://github.com/nearai/ironclaw/issues/7681)** — `Slack: 未链接用户连接消息公开且需手动多步操作`
- **标签**: enhancement / channel / UX / Onboarding / epic
- **作者**: sergeiest | **评论**: 0 | **👍**: 0
- **诉求分析**: 用户在 Slack 共享频道中 @bot 或 DM bot 时，收到的连接引导消息对全员可见，且流程断点严重（无上下文继承）。该 Issue 已被标记为 epic，表明影响范围广，**PR #7682 已针对此问题提供修复方案**，值得跟进合并。

### 📌 其他值得关注的开放 PR

- **[PR #7684](https://github.com/nearai/ironclaw/issues/7684)** — 批量依赖升级（base64 → 0.23.1、toml → 1.1.4），风险低，建议尽快合并以保持依赖安全。
- **[PR #7406](https://github.com/nearai/ironclaw/issues/7406)** — GitHub Actions 组升级（含 claude-code-action、setup-node 等），CI 基础设施维护。

---

## 5. Bug 与稳定性

| 问题 | 严重程度 | 状态 | Fix PR |
|---|---|---|---|
| [Issue #7681](https://github.com/nearai/ironclaw/issues/7681): Slack 未链接用户连接消息公开 | 中（UX 体验问题） | 新报告 | [PR #7682](https://github.com/nearai/ironclaw/issues/7682) 已开 |

- **无崩溃或回归报告。**
- **无紧急 Bug。**

---

## 6. 功能请求与路线图信号

| 请求 | 来源 | 分析 |
|---|---|---|
| **Slack 连接流程私密化 + 一键连接** | [Issue #7681](https://github.com/nearai/ironclaw/issues/7681) | 已被标记为 epic，PR #7682 已提交修复。**高概率纳入下一版本**。 |
| **自动化无结果抑制（确定性通知控制）** | [PR #7651](https://github.com/nearai/ironclaw/issues/7651) | 核心贡献者提交，功能定位清晰：根据用户措辞自动判断是否仅通知匹配/变更情况。**可能作为 `feat(automations)` 子功能发布**。 |
| **依赖安全升级** | 多个 Dependabot PR | 持续维护动作，非路线图功能。 |

---

## 7. 用户反馈摘要

- **痛点**（[Issue #7681](https://github.com/nearai/ironclaw/issues/7681)）:
  - 共享频道中未链接用户收到的连接提示**对全员可见**，造成信息泄露风险。
  - 连接流程为**多步手动操作**，且步骤间无上下文继承，用户体验断点严重。
  - 用户反馈：*"what's the link to connect you?"* — 说明现有流程引导不足。

- **满意度信号**:
  - 无正面反馈评论（当前 Issue 评论数为 0）。
  - 核心贡献者活跃（serrrfirat、hanakannzashi、ironclaw-ci[bot] 均有提交），项目维护健康。

---

## 8. 待处理积压

| 条目 | 类型 | 状态 | 建议 |
|---|---|---|---|
| [PR #7682](https://github.com/nearai/ironclaw/issues/7682) — Slack 连接消息修复 | 功能修复 | OPEN | **优先级高**：直接解决 epic 级别 UX 问题，建议尽快审核合并 |
| [PR #7651](https://github.com/nearai/ironclaw/issues/7651) — 无结果抑制自动化 | 功能增强 | OPEN | 规模 XL，需充分测试后合并 |
| [PR #7684](https://github.com/nearai/ironclaw/issues/7684) — 批量依赖升级 | 维护 | OPEN | 低风险，建议合并 |
| [PR #7406](https://github.com/nearai/ironclaw/issues/7406) — Actions 组升级 | CI 维护 | OPEN | 建议合并以保持 CI 最新 |

---

**项目健康度评估**: 🟢 良好 — 无紧急问题，依赖维护持续，核心功能改进有清晰路径。建议优先合并 PR #7682 以关闭高优先级 UX Issue。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报 — 2026-08-17

---

## 1. 今日速览

过去24小时内，LobsterAI 共活跃 10 条 Issue 和 17 条 PR，其中 9 条 PR 已合并，3 条 Issue 已关闭，整体提交与关闭速率保持中等水平。今日社区贡献者重点围绕**安全性加固**（敏感日志脱敏、存储访问控制、URL Scheme 白名单）和**协作体验优化**（Agent 模板导入导出、IM 删除确认、语音朗读）两个方向推进。无新版本发布，项目处于功能迭代与安全补丁并行的稳定更新周期。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

**🔒 安全加固（3 条，合并）**
- **#1831** — 脱敏主进程与 IM 模块的敏感日志，防止 Bearer Token、API Key、authCode 等落入 `electron-log` 文件。
- **#1832** — 限制 `store:*` IPC 越权访问，收窄通用 `ipcRenderer` 桥，阻断渲染端直接读写 SQLite KV 的权限。
- **#1833** — 为 `shell.openExternal` 增加 Scheme 白名单，拒绝 `file://`、`javascript://`、`data:` 等危险协议。

**🤖 Agent 与协作体验（5 条，合并）**
- **#1691** — 新增 Agent 模板导入/导出功能，支持本地文件和远程 URL，解决跨设备 Agent 配置迁移难题。
- **#1690** — IM 设置中钉钉、飞书、QQ 删除实例按钮增加二次确认弹窗，防止误删高成本配置。
- **#1715** — 修复 OpenClaw 服务端代理请求缺失 `session_id` 导致并发会话无法正确路由的问题。
- **#1760** — 新增 Image Avatar 支持，Agent 头像可同时使用 Emoji 或自定义图片。
- **#1835** — 修复 `continueSession` 失败时连续推送两条重复系统错误消息的问题。

**🎨 UI 与交互（2 条，合并）**
- **#1693** — 优化 ModelSelector 无模型时的交互体验，一键直达设置页，并修复未配置模型时输入内容丢失的 Bug。
- **#1773** — 补充记忆条目编辑按钮缺失的 `edit` i18n 翻译 key。

**项目整体推进评估：** 今日合并的 9 条 PR 中，3 条为安全修复，覆盖敏感数据泄露、权限越界和 XSS 入口；3 条为 Agent 协作核心体验优化；2 条为 UI/交互修复。项目安全基线显著提升，多 Agent 管理功能进一步完善，但新功能开发节奏平稳，无大版本特性推进。

---

## 4. 社区热点

### 高关注 Issue

| Issue | 标题 | 状态 | 评论 | 👍 | 链接 |
|-------|------|------|------|----|------|
| #1813 | DeepSeek V4 无法使用，LLM request failed | ✅ CLOSED | 8 | 0 | [Issue #1813](https://github.com/netease-youdao/LobsterAI/issues/1813) |
| #1698 | 有道龙虾与智企帝王蟹 Gateway 端口冲突 | 🟢 OPEN | 3 | 0 | [Issue #1698](https://github.com/netease-youdao/LobsterAI/issues/1698) |
| #1796 | Write tool execution always fail | ✅ CLOSED | 3 | 0 | [Issue #1796](https://github.com/netease-youdao/LobsterAI/issues/1796) |
| #1744 | Bug report（附件上传失败） | 🟢 OPEN | 3 | 0 | [Issue #1744](https://github.com/netease-youdao/LobsterAI/issues/1744) |

### 高关注 PR

| PR | 摘要 | 状态 | 链接 |
|----|------|------|------|
| #2452 | 修复 slashed model id（如 `deepseek-ai/DeepSeek-V4-Flash`）的 provider 前缀丢失问题 | 🟢 OPEN | [PR #2452](https://github.com/netease-youdao/LobsterAI/pull/2452) |
| #1682 | 为 Cowork AI 回复消息添加 Web Speech API 朗读功能 | 🟢 OPEN | [PR #1682](https://github.com/netease-youdao/LobsterAI/pull/1682) |
| #1832 | 限制 store:* IPC 越权访问（安全） | ✅ CLOSED | [PR #1832](https://github.com/netease-youdao/LobsterAI/pull/1832) |

**热点分析：**
- **#1813 / #2452**：DeepSeek V4 相关 Issue 和 PR 活跃，表明用户对该模型支持关注度较高，Provider/Model ID 解析逻辑是近期焦点。
- **#1698**：有道系产品（龙虾/帝王蟹）共存场景下的端口冲突问题，属于多产品生态兼容性痛点。
- **#1682**：语音朗读功能 PR 已提交但尚未合并，反映用户对多模态输出方式的呼声。

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 描述 | Fix 状态 | 链接 |
|--------|----------|------|----------|------|
| 🔴 高 | #1813 | DeepSeek V4 LLM 请求失败，provider 拒绝 schema/tool payload | ✅ 已关闭 | [Issue #1813](https://github.com/netease-youdao/LobsterAI/issues/1813) |
| 🔴 高 | #1796 | Write/Edit 工具调用持续失败，更新后仍存在 | ✅ 已关闭 | [Issue #1796](https://github.com/netease-youdao/LobsterAI/issues/1796) |
| 🟡 中 | #1698 | 有道龙虾与智企帝王蟹共存时 Gateway 端口冲突，必现 | 🟢 未修复 | [Issue #1698](https://github.com/netease-youdao/LobsterAI/issues/1698) |
| 🟡 中 | #1783 | 更新后 diff 功能失灵，`extractDiffFromToolInput` 存在 Bug | 🟢 未合并对应 Fix PR | [Issue #1783](https://github.com/netease-youdao/LobsterAI/issues/1783) |
| 🟡 中 | #1714 | Windows 11 安装过程中图标显示为白色且无效 | 🟢 未修复 | [Issue #1714](https://github.com/netease-youdao/LobsterAI/issues/1714) |
| 🟢 低 | #1744 | Bug report（附件上传失败，无法复现） | 🟢 未修复 | [Issue #1744](https://github.com/netease-youdao/LobsterAI/issues/1744) |

**稳定性评估：** 今日关闭 2 条高严重度 Bug（#1813、#1796），同时存在 1 条未修复的高优先级端口冲突问题（#1698）和 1 条 diff 功能回归（#1783）。整体 Bug 关闭率 30%（3/10），修复速度中等。

---

## 6. 功能请求与路线图信号

| 来源 | 需求描述 | 现有 PR 关联 | 纳入下一版本可能性 |
|------|----------|-------------|------------------|
| #1797 | 批量删除对话，清理无效上下文 | 🟢 未关联 | ⭐⭐⭐ 高（用户呼声明显，👍=1） |
| #1688 | 对话中动态调整 temperature 参数 | 🟢 未关联 | ⭐⭐ 中（技术可行但非紧急） |
| #1745 | 邮箱连接支持 OAuth2/新式身份验证 | 🟢 未关联 | ⭐⭐ 中（Outlook 用户刚需） |
| #1751 | 定时任务通知文案对齐问题 | 🟢 未关联 | ⭐ 低（文案级别 Bug） |
| #1682 | AI 回复语音朗读（已提交 PR） | ✅ PR #1682 | ⭐⭐⭐ 高（已在开发中） |
| #1760 | Image Avatar 支持（已提交 PR） | ✅ PR #1691 | ⭐⭐⭐ 高（已合并） |

**路线图信号分析：** 用户对**上下文管理**（批量删除对话）和**身份验证现代化**（OAuth2）需求明确；语音朗读和图片头像功能已在开发/合并路径中，预计将在下一版本上线。

---

## 7. 用户反馈摘要

| 反馈来源 | 用户痛点/场景 | 情绪倾向 |
|----------|--------------|----------|
| #1698 | 有道龙虾与智企帝王蟹共存时端口竞争，帝王蟹 Gateway 鉴权失败；关闭龙虾并重装可 workaround | 😤 不满（必现，影响多产品用户） |
| #1783 | 更新后 Edit Diff 功能失效，用户已深入定位到 `extractDiffFromToolInput` 的 Bug 根因 | 😤 不满（功能回归，用户主动 debug） |
| #1745 | Outlook 邮箱不支持 OAuth2，应用密码被完全禁止，无法连接邮箱 | 😟 困扰（身份验证方式落后） |
| #1714 | Windows 11 安装后图标白屏，影响使用体验 | 😟 困扰（UI 渲染问题） |
| #1797 | 上下文过长影响 AI 响应质量，希望批量删除无效对话 | 💡 建议（功能缺失） |
| #1688 | 希望以关键字动态调整 temperature，而非手动修改配置 | 💡 建议（交互便捷性） |

---

## 8. 待处理积压

### 长期未响应 Issue

| Issue | 创建时间 | 距今 | 严重度 | 描述 |
|-------|----------|------|--------|------|
| #1698 | 2026-04-15 | ~4 个月 | 🔴 高 | 有道龙虾与智企帝王蟹端口冲突必现，无修复进展 |
| #1714 | 2026-04-17 | ~4 个月 | 🟡 中 | Windows 11 安装图标白屏，无修复进展 |
| #1745 | 2026-04-19 | ~4 个月 | 🟡 中 | OAuth2 邮箱连接支持需求，无进展 |
| #1783 | 2026-04-21 | ~4 个月 | 🟡 中 | Diff 功能失效，用户已定位根因但无 Fix PR |
| #1688 | 2026-04-15 | ~4 个月 | 🟢 低 | temperature 动态调整需求 |
| #1751 | 2026-04-20 | ~4 个月 | 🟢 低 | 定时任务通知文案问题 |

### 长期未合并 PR

| PR | 创建时间 | 距今 | 描述 |
|----|----------|------|------|
| #2452 | 2026-08-07 | 10 天 | 修复 slashed model id provider 前缀丢失 |
| #1682 | 2026-04-14 | ~4 个月 | 语音朗读功能（Web Speech API） |
| #1683 | 2026-04-14 | ~4 个月 | 远程技能导入 URL 格式校验 |
| #1707 | 2026-04-16 | ~4 个月 | 切换 Agent 时自动清空输入框草稿 |
| #1765 | 2026-04-20 | ~4 个月 | @headlessui/react 依赖升级 |
| #1769 | 2026-04-20 | ~4 个月 | Cowork 初始化骨架屏加载 |
| #1770 | 2026-04-20 | ~4 个月 | Skills/TaskRunHistory 空状态优化 |

**提醒：** 多个功能型 PR 已提交超过 4 个月未合并，建议维护者关注review排期；Issue #1698 和 #1783 涉及已知 Bug 且用户已提供详细定位信息，建议优先处理。

---

*数据来源：LobsterAI GitHub Repository | 统计周期：2026-08-16 00:00 ~ 2026-08-17 00:00 UTC*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-08-17

---

## 1. 今日速览

Moltis 过去24小时保持稳健开发节奏，共接收 6 个 PR（5 个已合并）和 3 个 Issue（2 个仍开放）。项目整体健康度良好：核心网关模块修复了编译错误并解决了 flaky 测试问题，CalDAV 模块优化了事件拉取策略，通道活动日志新增细粒度可见性控制。一条新功能 PR（MiniMax Code ACP Agent）正在等待合并，显示出项目对多 Agent 生态的持续扩展。两个开放 Issue（心跳配置 Bug 和 CI 格式化违规）暂无对应修复 PR，建议维护者关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

| PR | 状态 | 贡献者 | 说明 |
|----|------|--------|------|
| [#1147](https://github.com/moltis-org/moltis/pull/1147) | ✅ 已合并 | thoscut | **CalDAV 事件查询优化**：将 `list_events` 的时间范围过滤从全量拉取改为 RFC 4791 `calendar-query` REPORT，显著提升大日历场景下的性能，同时保持 RFC 重叠语义正确性。 |
| [#1093](https://github.com/moltis-org/moltis/pull/1093) | ✅ 已合并 | s-salamatov | **通道活动日志可见性配置**：新增按账户/通道/用户三层粒度的 `activity_log` 可见性设置（`all` / `errors_only` / `off`），用户覆盖优先级高于通道，通道覆盖优先级高于账户默认值。 |
| [#1203](https://github.com/moltis-org/moltis/pull/1203) | ✅ 已合并 | Lstarsky0 | **网关测试稳定性修复**：通过暂停时钟驱动 `fanout_is_bounded_and_times_out_a_hung_endpoint` 测试，彻底解决全套件负载下间歇性竞争条件失败（#1193）。 |
| [#1201](https://github.com/moltis-org/moltis/pull/1201) | ✅ 已合并 | Lstarsky0 | **网关编译修复**：将 `start_background_tasks` 正确接入 `build_memory_runtime_from_store`，修复 #1158 重构后引入的编译错误。 |
| [#1186](https://github.com/moltis-org/moltis/pull/1186) | ✅ 已合并 | pxmpsdev | **Vault 恢复短语规范化**：确保存储哈希与验证哈希使用相同的规范化逻辑（去破折号、大写），消除大小写/格式不一致导致的密钥派生偏差。 |

**整体评估**：今日 5 个 PR 覆盖性能优化、功能增强和稳定性修复三个维度，项目核心模块（网关、CalDAV、Vault）质量持续提升，无明显技术债务积累。

---

## 4. 社区热点

| Issue/PR | 状态 | 作者 | 热度分析 |
|----------|------|------|----------|
| [#1205](https://github.com/moltis-org/moltis/issues/1205) | 🟡 开放 | IlyaBizyaev | 心跳模块未按配置的 active hours 运行，持续空转消耗资源。该问题触及多 Agent 调度场景下的能源效率痛点，可能影响生产部署。 |
| [#1202](https://github.com/moltis-org/moltis/issues/1202) | 🟡 开放 | Lstarsky0 | 两个文件（`store.rs` 1799 行、`admin.rs` 1531 行）超出 1500 行 CI 限制，阻塞 Format 检查。反映核心模块存在单文件膨胀风险，建议排期重构。 |

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | Fix PR |
|--------|-------|------|--------|
| 🔴 高 | [#1205](https://github.com/moltis-org/moltis/issues/1205) | Heartbeat 忽略配置的 active hours，持续运行导致不必要的资源消耗 | 暂无 |
| 🟡 中 | [#1202](https://github.com/moltis-org/moltis/issues/1202) | CI Format 检查因两个文件超行数限制而失败，阻塞合入流程 | 暂无 |
| ✅ 已修复 | [#1193](https://github.com/moltis-org/moltis/issues/1193) | `push fanout` 全套件负载下间歇性超时竞争条件 | [#1203](https://github.com/moltis-org/moltis/pull/1203) 已关闭 |

---

## 6. 功能请求与路线图信号

| PR | 类型 | 作者 | 评估 |
|----|------|------|------|
| [#1204](https://github.com/moltis-org/moltis/pull/1204) | 🆕 新功能 | hetaoBackend | **MiniMax Code ACP Agent 集成**：新增 `acp-minimax-code` 外部 Agent 类型，支持自动发现和 TOML 手动配置。目前状态为 OPEN，等待合并。若通过审查，将扩展 Moltis 的代码辅助 Agent 生态，符合项目多 Agent 协作的路线方向。 |

---

## 7. 用户反馈摘要

- **活跃时间控制**（#1205）：用户对 Heartbeat 模块的 active hours 配置存在明确预期，当前行为与预期不符，可能影响多 Agent 场景下的资源调度策略和能耗成本。
- **日历性能**（#1147 反馈）：用户关注 CalDAV `list_events` 的效率，全量拉取策略在高频率/大日历场景下不可接受，RFC 4791 查询方案得到认可。
- **审计可观测性**（#1093 反馈）：用户对通道活动日志的可见性有差异化需求，三层粒度（账户/通道/用户）的配置设计反映了细粒度权限管理的真实诉求。
- **安全性与兼容性**（#1186 反馈）：Vault 恢复短语的规范化问题涉及密钥派生安全，用户关注大小写/格式不一致带来的潜在风险。

---

## 8. 待处理积压

| 类型 | 编号 | 说明 | 建议 |
|------|------|------|------|
| 🐛 Bug | [#1205](https://github.com/moltis-org/moltis/issues/1205) | Heartbeat active hours 配置失效 | 建议维护者优先分配资源修复，影响生产部署稳定性 |
| 🛠 CI | [#1202](https://github.com/moltis-org/moltis/issues/1202) | 两个文件超行数限制，阻塞 CI | 建议排期对 `store.rs` 和 `admin.rs` 进行模块拆分或重构 |
| ✨ Feature | [#1204](https://github.com/moltis-org/moltis/pull/1204) | MiniMax Code ACP Agent 集成 | 建议尽快完成审查，该功能扩展了 Agent 生态，有明确用户需求 |

---

*数据截止：2026-08-16 24:00 UTC | 生成时间：2026-08-17*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报
**日期：2026-08-17 | 数据来源：github.com/agentscope-ai/CoPaw**

---

## 1. 今日速览

CoPaw 今日保持中等活跃度，24小时内共产生 **23 条**活动记录（12 Issues + 11 PRs），其中 **4 条 Issue 已关闭、2 条 PR 已合并**，社区贡献响应较为及时。无新版本发布，核心工作集中在 bug 修复与体验优化。整体项目健康度良好：关键 cron 同步 bug 已修复，多个长期存在的 bug（`_execute_tool_call` 崩溃、定时任务 misfire）已闭环，同时多个高质量 PR 待合并，预计近期版本更新节奏稳定。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的 PR

| PR | 作者 | 说明 |
|---|---|---|
| [#7064](https://github.com/agentscope-ai/CoPaw/pull/7064) | suantea | 修复 `qwenpaw cron update --text` 在 agent 类型任务上不生效的问题（`request.input` 与顶层 `text` 不同步） |
| [#7055](https://github.com/agentscope-ai/CoPaw/pull/7055) | lcq225 | 同上，补充修复 #7048，确保 `cron list/get` 正确反映更新 |

> 两条 PR 关联同一 Issue [#7048](https://github.com/agentscope-ai/CoPaw/issues/7048)，说明该修复经历了迭代，现已稳定关闭。

### 待合并的重要 PR（9 条）

| PR | 类型 | 说明 |
|---|---|---|
| [#6302](https://github.com/agentscope-ai/CoPaw/pull/6302) | feat | 统一 provider 发现、模型元数据、路由与 agent 控制，引入目录驱动模型系统，预计对架构有显著影响 |
| [#6940](https://github.com/agentscope-ai/CoPaw/pull/6940) | feat | 新增 DataPaw 原生应用运行时与持久化分析工作区，扩展项目生态边界 |
| [#7072](https://github.com/agentscope-ai/CoPaw/pull/7072) | feat | 后台聊天任务列表 API，支持多 agent 协调场景 |
| [#7071](https://github.com/agentscope-ai/CoPaw/pull/7071) | fix | `view_video` inline cap 从硬编码 2MB 改为可配置，修复大视频无法显示问题 |
| [#7070](https://github.com/agentscope-ai/CoPaw/pull/7070) | fix | 修复 OpenAI Responses API 路径下 `view_video` 静默失败（模型未收到视频帧） |
| [#7069](https://github.com/agentscope-ai/CoPaw/pull/7069) | fix | 修复历史消息中 data-URL 图片在会话重载后无法渲染的回归 |
| [#7067](https://github.com/agentscope-ai/CoPaw/pull/7067) | fix | 支持 `/chat/:agentId/:sessionId` 深度链接，解决多 agent 场景下 URL 被改写的问题 |
| [#7066](https://github.com/agentscope-ai/CoPaw/pull/7066) | fix | 修复 OAuth2 旋转 refresh_token 未持久化的认证失效问题 |
| [#6975](https://github.com/agentscope-ai/CoPaw/pull/6975) | fix | 修复 `/compact` 后 context-usage 环不更新的问题 |

> **进展评估**：今日合并的 PR 虽少，但修复的关键体验问题（cron 同步、工具调用崩溃、定时任务稳定性）用户感知度高；9 条待合并 PR 覆盖架构重构、多 agent 支持、媒体处理、OAuth 认证等核心路径，整体向前推进明显。

---

## 4. 社区热点

### 高关注 Issue / PR

| Issue/PR | 热度来源 | 分析 |
|---|---|---|
| [#7003](https://github.com/agentscope-ai/CoPaw/issues/7003) | 3 评论，已关闭 | ViBo 内存优化方案提出，用户关注会话间记忆持久化与 token 成本，反映社区对**长期记忆与成本控制**的强烈诉求 |
| [#6471](https://github.com/agentscope-ai/CoPaw/issues/6471) | 2 评论，已关闭 | APScheduler 在长时间空闲后 misfire，属于**生产环境稳定性隐患**，已关闭说明问题已定位 |
| [#7052](https://github.com/agentscope-ai/CoPaw/issues/7052) | 2 评论，开放中 | 插件 API 增加 `system_prompt` 权限请求，反映企业用户在插件生态中对**提示词安全隔离**的需求 |
| [#7062](https://github.com/agentscope-ai/CoPaw/issues/7062) | 1 评论，开放中 | `reasoning_effort` 按 agent/session 级配置请求，用户希望细粒度控制不同角色的思考深度 |
| [#7075](https://github.com/agentscope-ai/CoPaw/issues/7075) | 1 评论，开放中 | 定时任务缺少运行细节展示（开始/结束时间、状态），影响可观测性，与 #6471 形成互补诉求 |

> **热点分析**：社区今日关注点集中在**可观测性**（定时任务状态、上下文用量）、**企业级安全**（system_prompt 隔离）和**成本优化**（token 压缩、思考深度控制）三个方向，与当前 AI Agent 平台演进趋势一致。

---

## 5. Bug 与稳定性

### 已修复（今日关闭）

| Issue | 严重程度 | 说明 | Fix PR |
|---|---|---|---|
| [#7063](https://github.com/agentscope-ai/CoPaw/issues/7063) | 🔴 严重 | `async for` 遍历 coroutine 导致工具调用必现崩溃 | 已关闭，待确认修复 |
| [#7048](https://github.com/agentscope-ai/CoPaw/issues/7048) | 🟠 高 | `qwenpaw cron update --text` 静默失败，prompt 未更新 | [#7064](https://github.com/agentscope-ai/CoPaw/pull/7064) / [#7055](https://github.com/agentscope-ai/CoPaw/pull/7055) |
| [#6471](https://github.com/agentscope-ai/CoPaw/issues/6471) | 🟠 高 | APScheduler 事件循环空闲后定时任务 misfire | 已关闭 |

### 待处理 Bug（今日新开或活跃）

| Issue | 严重程度 | 说明 |
|---|---|---|
| [#7076](https://github.com/agentscope-ai/CoPaw/issues/7076) | 🟠 高 | `qwenpaw-creator` LLM 模型配置返回 404（v2.1.0） |
| [#7074](https://github.com/agentscope-ai/CoPaw/issues/7074) | 🟡 中 | 正常运行中崩溃，需刷新页面重启，**高频发生** |
| [#7065](https://github.com/agentscope-ai/CoPaw/issues/7065) | 🟡 中 | 多轮对话后无法查看早期历史记录（仅显示最近 3-4 条） |

> **稳定性评估**：今日共关闭 3 条严重/高优先级 bug，修复了工具调用崩溃和 cron 同步两个影响用户体验的核心问题；但 #7074（高频崩溃）和 #7076（404 错误）尚未闭环，建议维护者优先跟进。

---

## 6. 功能请求与路线图信号

| 请求 | Issue | 关联 PR | 纳入可能性 |
|---|---|---|---|
| 定时任务运行细节展示 | [#7075](https://github.com/agentscope-ai/CoPaw/issues/7075) | — | 🟢 高 — 与 #6471 同类需求，社区呼声强 |
| 插件 API system_prompt 权限 | [#7052](https://github.com/agentscope-ai/CoPaw/issues/7052) | — | 🟡 中 — 涉及安全边界调整，需产品决策 |
| 文件查看器支持更多语言（C#/Shader） | [#7068](https://github.com/agentscope-ai/CoPaw/issues/7068) | — | 🟡 中 — 游戏开发场景细分需求 |
| `reasoning_effort` 按 agent/session 配置 | [#7062](https://github.com/agentscope-ai/CoPaw/issues/7062) | — | 🟢 高 — 已在 PR #6302（统一 provider 控制）范畴内 |
| 后台任务列表 API | — | [#7072](https://github.com/agentscope-ai/CoPaw/pull/7072) | 🟢 高 — PR 已提交，待合并 |
| DataPaw 原生运行时 | — | [#6940](https://github.com/agentscope-ai/CoPaw/pull/6940) | 🟢 高 — 扩展项目边界，已提交 |

> **路线图信号**：PR #6302 的统一 provider 架构将影响后续多个功能迭代方向；定时任务可观测性与多 agent 任务管理是当前社区最集中的改进诉求。

---

## 7. 用户反馈摘要

| 痛点/场景 | 来源 | 情绪 |
|---|---|---|
| 工具调用必现崩溃，影响生产使用 | [#7063](https://github.com/agentscope-ai/CoPaw/issues/7063) | ❌ 不满 |
| Cron update 命令静默失败，误导用户以为更新成功 | [#7048](https://github.com/agentscope-ai/CoPaw/issues/7048) | ❌ 不满（已修复） |
| 定时任务运行中无状态反馈，无法判断是否触发/进行中 | [#7075](https://github.com/agentscope-ai/CoPaw/issues/7075) | ⚠️ 失望 |
| 高频正常运行崩溃，需手动刷新页面 | [#7074](https://github.com/agentscope-ai/CoPaw/issues/7074) | ❌ 不满 |
| 多轮对话后历史消息被截断，影响追溯 | [#7065](https://github.com/agentscope-ai/CoPaw/issues/7065) | ⚠️ 失望 |
| 插件 system_prompt 被用户可见，存在安全/体验风险 | [#7052](https://github.com/agentscope-ai/CoPaw/issues/7052) | ⚠️ 担忧 |
| LLM 模型配置 404，creator 工具链受阻 | [#7076](https://github.com/agentscope-ai/CoPaw/issues/7076) | ❌ 不满 |
| session 间记忆丢失，token 成本高 | [#7003](https://github.com/agentscope-ai/CoPaw/issues/7003) | ⚠️ 关切（已有 ViBo 方案） |
| view_video 在大文件或特定 provider 下静默失败 | [#7059](https://github.com/agentscope-ai/CoPaw/issues/7059) | ⚠️ 不满（已修复） |

> **满意度概览**：今日用户反馈以负面为主，集中在**稳定性**（崩溃、静默失败）和**可观测性**（任务状态、历史记录）两个维度。已关闭的 3 条 bug 显著改善体验，但 #7074 和 #7076 仍是当前主要痛点。

---

## 8. 待处理积压

| 类型 | 条目 | 说明 | 建议 |
|---|---|---|---|
| 🔴 Bug | [#7076](https://github.com/agentscope-ai/CoPaw/issues/7076) | qwenpaw-creator LLM 模型配置 404（v2.1.0） | 优先排查，可能影响新用户上手 |
| 🔴 Bug | [#7074](https://github.com/agentscope-ai/CoPaw/issues/7074) | 高频正常运行崩溃，需刷新页面 | 需复现堆栈，影响核心会话稳定性 |
| 🟡 Feature | [#7052](https://github.com/agentscope-ai/CoPaw/issues/7052) | 插件 system_prompt 权限隔离 | 评估企业用户影响，规划安全策略 |
| 🟡 Feature | [#7075](https://github.com/agentscope-ai/CoPaw/issues/7075) | 定时任务运行细节展示 | 与 #6471 合并评估，统一可观测性方案 |
| 🟡 PR | [#6302](https://github.com/agentscope-ai/CoPaw/pull/6302) | 统一 provider 发现与路由 | 架构级变更，需充分 review 后合并 |
| 🟡 PR | [#6940](https://github.com/agentscope-ai/CoPaw/pull/6940) | DataPaw 原生运行时 | 扩展性工作，确认与核心项目集成策略 |

---

**日报生成时间**：2026-08-17 | **分析师**：AI 开源项目分析师

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-08-17

## 1. 今日速览

ZeroClaw 今日保持高活跃开发节奏：过去24小时新增48条 Issue 与50条 PR，但无新版本发布。安全相关的插件 egress 策略（#9580）已合并，标志着插件网络隔离架构正式落地；多项 RFC（Work Lanes 流程治理、Chat Completions profile、实时语音通道）仍处于评审推进阶段。维护者团队集中精力处理测试稳定性与核心安全边界，项目整体健康度良好，架构演进与稳定性修复双线并行。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

**已合并/关闭的关键 PR：**

- **#9580 [CLOSED]** — `fix(security): harden built-in HTTP egress on the shared network guard`（JordanTheJet）。将内置 HTTP 出口强化至 `zeroclaw-infra::net_guard`，拒绝非全局 IPv4/IPv6，为后续插件 egress 策略奠定基础。这是安全架构的关键一步。
- **PR #9582、#9584、#9137 构成插件出口策略的三阶段落地**：Stage 2（#9582，wasi:http 主机策略）与 Stage 3（#9584，CLI 授权仪式）均已合并，实现了插件网络的"默认拒绝"模型。
- **#9854 [CLOSED]** — `fix(providers): derive context-window discovery from the family registry`（JordanTheJet）。将上下文窗口发现从手写提供者名单改为家族注册表驱动，解决了可扩展性问题。
- **#9547** — CPAL 升级至 0.18，语音唤醒模块迁移至统一 API。

**整体评估**：今日核心推进在安全架构（插件 egress 完整落地）与依赖治理（CPAL 升级、aardvark-sys 移除），为 0.8.x 系列的稳定性与可维护性打下基础。

## 4. 社区热点

**评论最多、讨论最活跃的 Issue：**

| 议题 | 作者 | 评论数 | 状态 |
|---|---|---|---|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) RFC: Work Lanes & Board Automation | Audacity88 | 23 | Ratified / 推进中 |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) RFC: Chat Completions profile | REL-mame | 22 | 评审中 |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) RFC: 统一附件架构 | NiuBlibing | 17 | 提案阶段 |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) RFC: 内部 Agent 轮次的来源与绑定契约 | mov-xound-glitch | 14 | 修订中 |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) RFC: 安全 posture 与通用入口策略 | Audacity88 | 14 | 评审中 |
| [#6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) RFC: 轻量核心（外部集成） | ilteoood | 14 | 评审中 |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) RFC: Gemini Live 实时语音通道 | metalmon | 13 | v2 修订（2026-08-16）|

**热点分析**：
- **#6808（Work Lanes）**：维护者流程治理的长期 RFC，已获 ratify，正推进落地。反映社区对项目板自动化与标签清理的迫切需求。
- **#8603（Chat Completions profile）**：填补 ZeroClaw 与 OpenAI 生态（Open WebUI、LobeChat、Aider 等）的直接兼容空白，评论活跃说明外部开发者生态对此高度期待。
- **#8780（Gemini Live 实时语音）**：v2 于昨日改写为 broker 合约，显示作者积极响应对话反馈，实时语音是用户端高频需求。
- **#9488（统一附件架构）**：新提案，尚未进入深度讨论，值得关注后续进展。

## 5. Bug 与稳定性

| 严重度 | Issue | 描述 | Fix PR |
|---|---|---|---|
| **S1 - 工作流阻断** | [#10013](https://github.com/zeroclaw-labs/zeroclaw/issues/10013) | Edge TTS 取消测试在并行负载下可能错过 fake 子进程启动 | 无 |
| **S1** | [#10006](https://github.com/zeroclaw-labs/zeroclaw/issues/10006) | `endpoint_lock_is_held_through_guard_cleanup` 测试在并行运行时门控下间歇失败 | [#10011](https://github.com/zeroclaw-labs/zeroclaw/issues/10011)（进行中） |
| **S1** | [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) | runtime 生成的可执行测试 fixture 在并行门控下触发 ETXTBSY | [#10011](https://github.com/zeroclaw-labs/zeroclaw/issues/10011)（进行中） |
| **S2 - 行为降级** | [#9655](https://github.com/zeroclaw-labs/zeroclaw/issues/9655) | Approval cards 无位置标识，连续卡片无法区分 | 无 |
| **S2** | [#9811](https://github.com/zeroclaw-labs/zeroclaw/issues/9811) | `/health` 错误报告从未连接的 Telegram 频道为 healthy | 无 |
| **S2** | [#10020](https://github.com/zeroclaw-labs/zeroclaw/issues/10020) | `delegate` 独立模式下忽略目标 thinking 策略 | 无 |
| **S2** | [#10037](https://github.com/zeroclaw-labs/zeroclaw/issues/10037) | `POST /api/cron` 静默存储无效 `session_target` 为 isolated | 无 |
| **S2** | [#9953](https://github.com/zeroclaw-labs/zeroclaw/issues/9953) [已关闭] | SOP 步骤 schema 校验拒绝双重编码输出对象 | 已修复 |

**稳定性评估**：测试基础设施（并行运行时门控）是今日最大稳定性痛点，3 个 P1 测试问题集中爆发，#10011 正在修复中。生产级 Bug 多为 S2 降级，无 S0 级崩溃。

## 6. 功能请求与路线图信号

| 提案 | Issue | 信号强度 |
|---|---|---|
| Chat Completions 协议原生支持 | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | 🔴 高 — 评论22，涉及多个主流客户端生态 |
| Gemini Live 实时语音通道 | [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | 🔴 高 — v2 刚修订，作者积极跟进 |
| 统一附件架构（Web Chat & Channels） | [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | 🟡 中 — 新提案，待定 |
| Date-range 条件 cron 调度 | [#7887](https://github.com/zeroclaw-labs/zeroclaw/issues/7887) [已接受] | 🟢 低 — 已接受，排期待确认 |
| Provider 回退熔断器 | [#7881](https://github.com/zeroclaw-labs/zeroclaw/issues/7881) [已接受] | 🟢 低 — 已接受 |
| Intra-family 回退通知 | [#7883](https://github.com/zeroclaw-labs/zeroclaw/issues/7883) [已接受] | 🟢 低 — 已接受 |
| Schema 验证型记忆合并 | [#6998](https://github.com/zeroclaw-labs/zeroclaw/issues/6998) [已接受] | 🟢 低 — 已接受 |
| WASM 插件生命周期 Hook 订阅 | [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) | 🟡 中 — 评审中，作者需跟进 |
| zeroclaw swarm（临时 Agent 群体） | [#10025](https://github.com/zeroclaw-labs/zeroclaw/issues/10025) | 🟡 中 — 新提案，今日提交 |
| 内置 HTTP egress 加固 | #9580 [已合并] | ✅ 已完成 |

**路线图判断**：Chat Completions profile 和 Gemini Live 实时语音是最可能纳入下一版本的两个功能，前者直接对接现有生态，后者是实时交互的差异化能力。

## 7. 用户反馈摘要

- **Chat Completions 兼容性是最大生态痛点**（#8603）：Open WebUI、LobeChat、Aider、Continue.dev 等用户希望直接使用 ZeroClaw 作为后端，当前仅 WebSocket/ACP/Webhook 通道造成接入成本。
- **审批卡片交互缺陷**（#9655）：单条消息触发多个工具调用时，连续 approval cards 无法区分，影响多工具流程体验。
- **健康检查误报**（#9811）：Telegram 频道的无效 token 场景下 `/health` 仍报告 healthy，影响运维监控。
- **代理/内网环境下的 OpenAI Responses 路由问题**（#9606 PR 涉及）：runtime proxy 配置未被 OpenAI Responses 路径遵守，已通过 #9606 修复。
- **知识图谱缺乏 Agent 隔离**（#9745 PR）：所有 Agent 共享同一 SQLite 图谱，无所有权维度，已提出修复 PR。
- **Telegram 群聊会话共享**（#9772 PR）：多人在同一群协作时会话范围硬编码为 `Sender`，缺乏 per-user 选项。

## 8. 待处理积压

| Issue | 作者 | 年龄 | 关注原因 |
|---|---|---|---|
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) WASM 插件 Hook 订阅 | dakaii | 2个月+ | 第三方插件生态关键能力，状态 `needs-author-action` |
| [#6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) 轻量核心 RFC | ilteoood | 4个月+ | 架构方向性决策，评论14条，维护者关注 |
| [#9655](https://github.com/zeroclaw-labs/zeroclaw/issues/9655) Approval cards 无位置 | ZiBibro | 15天 | S2 用户体验问题，无修复 PR |
| [#9811](https://github.com/zeroclaw-labs/zeroclaw/issues/9811) /health 误报 | bryankwandou | 10天 | 运维可观测性问题，无修复 PR |
| [#10020](https://github.com/zeroclaw-labs/zeroclaw/issues/10020) Delegate 忽略 thinking 策略 | vrurg | 1天 | S2，今日新发现 |
| [#10037](https://github.com/zeroclaw-labs/zeroclaw/issues/10037) Cron session_target 静默降级 | zyw02 | 1天 | S2，今日新发现 |
| [#7887](https://github.com/zeroclaw-labs/zeroclaw/issues/7887) Date-range cron | Audacity88 | 2个月+ | 已接受但未启动实现 |

---

**项目健康度评分**：🟢 良好。安全架构关键里程碑已达成，RFC 评审流程运转正常，测试基础设施问题正在集中修复中。主要风险点为并行测试门控的稳定性与多个 S2 Bug 的修复排期。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*