# OpenClaw 生态日报 2026-08-14

> Issues: 486 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-14 02:26 UTC

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



# OpenClaw 项目日报 — 2026-08-14

## 1. 今日速览

OpenClaw 昨日保持极高活跃度：24小时内共处理 486 条 Issues（324 条新开/活跃，162 条已关闭）和 500 条 PR 更新（374 条待合并，126 条已合并/关闭），社区参与度活跃但积压压力显著。核心痛点集中在 **子代理完成状态丢失、会话路由异常、Cron 任务超时与认证刷新失败** 等稳定性问题上，多个 P1 级问题已影响生产环境。今日无新版本发布，维护团队正集中处理多项关键修复 PR（如记忆系统 Phase 1C 读写隔离、多代理安全修复），整体项目处于"高频修复期"，向 2026.8.x 稳定通道积累变更。

## 2. 版本发布

**无新版本发布。**

当前关注版本：`OpenClaw 2026.3.x` / `2026.7.x`，多条 Bug 报告涉及 `2026.6.x`~`2026.7.1-2` 的回归问题，提示维护者需关注 release train 的完整性。

## 3. 项目进展

### 今日重要合并/关闭 PR

| PR | 作者 | 状态 | 内容摘要 |
|---|---|---|---|
| [#122344](https://github.com/openclaw/openclaw/pull/122344) | Patrick-Erichsen | ✅ Closed | OpenAI 模型发现器改为 profile-aware，按运行时认证顺序发现模型并绑定授权 Profile，解决多 Profile 环境下的模型选择错乱问题 |
| [#122517](https://github.com/openclaw/openclaw/pull/122517) | vatsalgargg | 🔄 Open (P1, platinum hermit) | 修复跨渠道 exec 审批泄漏至 Telegram 的安全问题，阻止了 `doesApprovalRequestSelectChannelAccount` 逻辑缺陷导致的审批提示跨渠道暴露 |
| [#123412](https://github.com/openclaw/openclaw/pull/123412) | steipete | 🔄 Open | 修复 iOS/Android 应用中 per-session 桌面按钮错误打开 source picker 而非目标机器的 Bug（关联 #123097） |
| [#123415](https://github.com/openclaw/openclaw/pull/123415) | joshavant | 🔄 Open | 将 Control UI 的 `models.list` 和 `models.authStatus` 请求 scope 到选定 Agent，避免多 Agent 环境下模型数据混叠 |
| [#123402](https://github.com/openclaw/openclaw/pull/123402) | steipete | 🔄 Open | 为 Anthropic 模型添加 opt-in 服务端压缩（compact-2026-01-12），替代客户端重写 prompt prefix 的方式，保护 warm prompt cache |
| [#123424](https://github.com/openclaw/openclaw/pull/123424) | steipete | 🔄 Open | 引入 legacy-main session 迁移引擎，支持未来 `main` Agent 退役后仍兼容 `agent:main:*` 历史会话，避免数据不可达 |
| [#123253](https://github.com/openclaw/openclaw/pull/123253) | steipete | 🔄 Open | 修复自动化（Cron）徽章不更新 Bug——cron 变更绕过 `sessions.list` 缓存 fence，客户端无法感知自动化状态变化 |

**整体判断：** 今日 PR 主要沿三条线推进——① **多代理/多用户隔离安全加固**；② **会话状态机与迁移基础设施**；③ **前端 UX 细节修复**。项目向"生产级多用户网关"方向稳步演进，但大量 P1 PR 仍等待维护者审查。

## 4. 社区热点

### 讨论最活跃的 Issues（按评论数排序）

| Issue | 评论数 | 评分 | 核心诉求 |
|---|---|---|---|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | 92 | 🦪 silver shellfish | `#116277` 关闭后静默回复失败仍复现，监控 cron 持续记录新发生——用户认为修复不彻底 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 48 | 🌊 off-meta tidepool | **内存信任标签化**：按来源对记忆条目打 trust tag，防御 memory poisoning 攻击 |
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | 48 | 🦞 diamond lobster | 工具调用间的文本泄漏到消息频道，严重破坏多用户聊天体验 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 27 | 🦪 silver shellfish | 子代理完成结果静默丢失，无重试、无通知、无自动重启 |
| [#121953](https://github.com/openclaw/openclaw/issues/121953) | 16 | 🦪 silver shellfish | Cron agent 使用 DeepSeek 时卡死——`[cron:<jobId> <name>]` 前缀被边缘节点降优先级 |

### 热点分析

1. **子代理可靠性是最大痛点**：#44925、#67777、#47975、#92433 四个高评论 Issue 均指向 subagent 完成投递/会话清理问题，形成明显的模式——当前 subagent 架构在高并发场景下存在系统性脆弱。
2. **安全诉求升温**：#7707（memory poisoning 防御）和 #25592（工具输出泄漏）反映了用户从"能用"向"安全可用"演进的需求，与今日 PR #122517（跨渠道审批泄漏修复）形成呼应。
3. **Cron 调度稳定性**：#121953 和 #91363 两个独立 Issue 均涉及 Cron 任务失败，指向不同的根因（DeepSeek 边缘节点 + 孤立 session LLM 调用），说明 Cron 子系统需要系统性审查。

## 5. Bug 与稳定性

### P1 级关键 Bug（按严重程度）

| Issue | 类型 | 严重程度 | 状态 | 已有 Fix PR |
|---|---|---|---|---|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | Regression | 🔴 回复静默失败持续复现 | OPEN | ❌ 无 |
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | Behavior | 🔴 工具间文本泄漏到消息频道 | OPEN | ❌ 无 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Bug | 🔴 子代理完成结果静默丢失 | OPEN | ❌ 无 |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | Bug | 🔴 子代理完成投递在超时/drains/orphan prune 时丢失 | OPEN | ❌ 无 |
| [#91363](https://github.com/openclaw/openclaw/issues/91363) | Bug | 🔴 孤立 Cron 任务始终 LLM 调用失败 | OPEN | ❌ 无 |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) | Reliability | 🔴 active-memory 插件导致网关在高并发时过载 | OPEN | ❌ 无 |
| [#97983](https://github.com/openclaw/openclaw/issues/97983) | Bug | 🔴 iOS/WebChat 消息写入 transcript 但不触发回复 | OPEN | ❌ 无 |
| [#89278](https://github.com/openclaw/openclaw/issues/89278) | Regression | 🔴 Codex OAuth refresh 超时 10s 导致 Cron/heartbeat 失败 | OPEN | ❌ 无 |
| [#121605](https://github.com/openclaw/openclaw/issues/121605) | Regression | 🔴 模型 fallback 后回复生成成功但不投递到频道 | ✅ Closed | ✅ 已修复 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Regression | 🟡 钩子/工具子进程泄漏导致 zombie 积累 | OPEN | ❌ 无 |
| [#111498](https://github.com/openclaw/openclaw/issues/111498) | Regression | 🟡 Anthropic auth 恢复后 TUI/CLI 持续阻塞于 workspace-state | OPEN | ❌ 无 |
| [#41165](https://github.com/openclaw/openclaw/issues/41165) | Behavior | 🟡 Telegram DM 路由到 agent:main:main 污染心跳会话 | OPEN | ❌ 无 |

**稳定性评估：** 过去 24 小时内有 **162 条 Issue 被解决**，但仍有 **324 条新开/活跃 Issue**，净增 162 条。多个 regression 类 Bug（#89278、#111498、#121605、#77733）指向近期版本引入的问题，建议维护者关注 `2026.5.x`~`2026.7.x` 版本的回归测试覆盖。

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 关联 PR | 纳入可能性 |
|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | **Memory Trust Tagging by Source** — 按来源对记忆条目打信任标签，防御 poisoning | PR #121422（memory authorization contract）、PR #121945（Phase 1C read isolation） | ⭐⭐⭐⭐ 高——与正在推进的多玩家记忆架构直接相关 |
| [#45758](https://github.com/openclaw/openclaw/issues/45758) | **YAML 配置文件支持** — 作为 JSON5 的替代格式 | 无直接关联 PR | ⭐⭐ 中低——DevOps 友好但改动面大 |
| [#9016](https://github.com/openclaw/openclaw/issues/9016) | **OpenRouter 使用成本暴露** — 将 API 响应中的费用信息透传给 Agent | 无直接关联 PR | ⭐⭐ 中——对成本敏感用户有价值 |
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | **WebChat 支持自托管 STT/TTS** — 绕过浏览器 Web Speech API，使用网关配置的语音服务 | 无直接关联 PR | ⭐⭐⭐ 中高——与多平台一致性战略相符 |
| [#45771](https://github.com/openclaw/openclaw/issues/45771) | **内置速率感知限流** — 防止自主 Agent 耗尽 LLM API 配额 | 无直接关联 PR | ⭐⭐⭐ 中高——与 #43374（多 Agent 并发超时）问题呼应 |
| [#16555](https://github.com/openclaw/openclaw/issues/16555) | **投递队列消息 TTL/过期** — 防止网关重启后陈旧消息淹没频道 | 无直接关联 PR | ⭐⭐⭐ 中高——与消息丢失类 Bug 直接相关 |
| [#114612](https://github.com/openclaw/openclaw/issues/114612) | **Memory SQLite 无界增长** — `memory_index_chunks` + `memory_embedding_cache` 表无保留策略 | PR #121422（memory contract）可能间接覆盖 | ⭐⭐⭐⭐ 高——生产环境已出现磁盘填充 |
| [#42276](https://github.com/openclaw/openclaw/issues/42276) | **Reasoning Stream** — 支持类似 OpenAI/Grok 的流式思考过程展示 | 无直接关联 PR | ⭐⭐ 中低——依赖底层模型能力 |

**路线图信号：** 记忆系统（memory-core）是当前最重要的架构演进方向，PR #121421（设计文档）、#121422（SDK contract）、#121945（Phase 1C read isolation）形成完整的技术栈推进。多玩家记忆（multiplayer memory）的安全隔离和权限模型将是下阶段核心。

## 7. 用户反馈摘要

### 真实痛点（高频出现）

1. **子代理生命周期管理失控**：多个用户报告 subagent 完成后会话残留（#47975）、结果丢失（#44925、#67777、#92433），主会话卡死或无响应。一位用户描述："spawn 了多个 subagent 后，主会话不可响应"（#47975）。

2. **消息路由/投递不可靠**：Telegram DM 路由到错误会话（#41165）、工具调用间文本泄漏到频道（#25592）、模型 fallback 后回复不投递（#121605）等问题反复出现，影响多用户聊天场景。

3. **Cron 调度与认证脆弱**：孤立 Cron 任务始终 LLM 失败（#91363）、Codex OAuth refresh 超 10s 导致 Cron/heartbeat 全部失败（#89278）、DeepSeek 前缀降级（#121953）——定时任务在边缘条件下极不可靠。

4. **多 Agent 并发瓶颈**：4 个并发 Agent 时所有 LLM 调用同时超时（#43374），`active-memory` 插件导致网关过载（#72015），session lane 被 followup drain 独占 20-30 分钟（#54488）。

### 正面反馈

- 用户认可 `active-memory` 功能的价值但希望改善性能（#72015）
- 多代理编排场景的用户基数在增长，对稳定性和安全性的要求也随之提高
- WebChat 的语音功能需求明确（#45508），反映用户希望全平台一致体验

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 天数 | 优先级 | 状态 | 风险 |
|---|---|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 2026-02-03 | 192 天 | P2 | OPEN，6 个 clawsweeper 标签 | 安全功能需求，与记忆架构路线图高度相关 |
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | 2026-02-24 | 170 天 | P1 | OPEN，🦞 diamond lobster | 多用户场景的关键体验 Bug，无修复 PR |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 2026-03-13 | 154 天 | P1 | OPEN，🦪 silver shellfish | 子代理可靠性核心问题 |
| [#43367](https://github.com/openclaw/openclaw/issues/43367) | 2026-03-11 | 156 天 | P1 | OPEN | 多代理并发编排不稳定，config 覆盖/会话锁失败 |
| [#54488](https://github.com/openclaw/openclaw/issues/54488) | 2026-03-25 | 142 天 | P1 | OPEN，🦞 diamond lobster | Session lane starvation 导致 20-30min 入站阻塞 |
| [#91363](https://github.com/openclaw/openclaw/issues/91363) | 2026-06-08 | 67 天 | P1 | OPEN | 孤立 Cron LLM 调用始终失败，6 个 👍 |
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | 2026-08-09 | 5 天 | P1 | OPEN，92 条评论 | 静默回复失败修复不完整，用户不满情绪明显 |

### 待审查 PR

| PR | 创建时间 | 状态 | 

---

## 横向生态对比



# AI 智能体开源生态横向对比分析
**日期：2026-08-14 | 分析师：Agnes-2.0-Flash (Sapiens AI)**

---

## 1. 生态全景

2026年8月，个人AI助手与自主智能体开源生态呈现**多极分化、高速迭代**的格局：OpenClaw、CoPaw、Hermes Agent 构成第一梯队，日均百级以上Issue/PR活跃，核心竞争焦点从"能否用"转向"稳定可用"；NanoBot、LobsterAI、Moltis 处于功能打磨阶段，以稳定性修复和技术债清理为主；PicoClaw、NanoClaw 分别聚焦嵌入式场景与模板化部署，形成差异化定位。生态整体从"功能竞赛"进入"工程化深水区"，安全性（权限模型、会话隔离）、可靠性（Cron调度、子代理生命周期）和用户体验（多平台一致、长会话管理）成为共同攻坚方向。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | 版本发布 | 健康度评级 | 核心状态 |
|------|-------------|-----------|----------|-----------|----------|
| **OpenClaw** | 486 (324活跃/162关闭) | 500 (374待合并/126合并) | 无 | 🟡 高频修复期 | P1积压严重，向2026.8.x稳定通道积累 |
| **CoPaw** | 45 (28活跃/17关闭) | 50 (31待合并/19合并) | v2.1.0 + beta.5 | 🟡 功能冻结期 | OS Shell发布后暴露2个回归Bug需hotfix |
| **Hermes Agent** | 50 (活跃) | 50 (活跃) | v0.20.1 | 🟡 回归阵痛期 | Windows Gateway生命周期6个P1集群 |
| **NanoBot** | 11 (10活跃/1关闭) | 31 (22待合并/9合并) | 无 | 🟢 稳健 | Cron调度与session持久化修复集中 |
| **LobsterAI** | 2 (活跃) | 10 (4待合并/6合并) | 无 | 🟡 打磨期 | UI重构+测试补强并行 |
| **Moltis** | 1 (活跃) | 4 (4待审) | 无 | 🟡 中等 | CalDAV连接器为本期重点 |
| **NanoClaw** | 2 (活跃) | 19 (13已合并) | v2.2.0 | 🟢 健康 | 模板系统迁移+CI/CD安全硬化 |
| **PicoClaw** | 2 (活跃) | 9 (6待合并/3合并) | 无 | 🟢 维护 | 依赖更新为主，构建修复待合并 |
| **IronClaw** | 50 | 50 | 无 | 🟡 重构期 | 架构重构+性能优化窗口 |
| **NullClaw** | 0 | 0 | 无 | 🔴 停滞 | 无活动 |
| **ZeptoClaw** | 0 | 0 | 无 | 🔴 停滞 | 无活动 |
| **ZeroClaw** | — | — | — | ⚠️ 数据异常 | 摘要生成失败 |

---

## 3. OpenClaw 在生态中的定位

**规模优势**：OpenClaw 以 486 Issues + 500 PRs 的绝对量级领先，社区参与度是 CoPaw 的10倍、Hermes 的9倍，表明其作为"核心参照"的项目地位。

**技术路线差异**：
- **多代理架构**：OpenClaw 聚焦子代理生命周期管理、跨渠道安全隔离（PR #122517）、多Agent并发路由，是生态中**多代理编排最成熟**的项目
- **记忆系统先行**：memory-core 架构（Phase 1C 读写隔离、信任标签化）处于生态最前沿，LobsterAI、NanoClaw 均沿类似方向演进
- **网关定位**：OpenClaw 明确指向"生产级多用户网关"，与 CoPaw 的"本地OS级体验"、Hermes 的"桌面应用"形成场景分化

**社区规模对比**（估算）：
| 项目 | 社区活跃度 | 贡献者结构 | 商业化程度 |
|------|-----------|-----------|-----------|
| OpenClaw | ⭐⭐⭐⭐⭐ | 核心维护者+高频社区贡献 | 企业级授权 |
| CoPaw | ⭐⭐⭐⭐ | AgentScope团队主导 | 阿里云生态绑定 |
| Hermes | ⭐⭐⭐⭐ | NousResearch主导 | 研究导向+商业化 |
| NanoBot | ⭐⭐⭐ | HKUDS学术团队 | 学术验证场景 |

---

## 4. 共同关注的技术方向

### 4.1 子代理/任务执行可靠性
| 项目 | 具体诉求 |
|------|---------|
| **OpenClaw** | 子代理完成结果静默丢失（#44925, #67777）、主会话卡死（#47975） |
| **CoPaw** | 多步骤任务中途静默停止需手动继续（#6921）、无限循环卡死（#6768） |
| **Hermes** | zero-downtime热更新需避免杀死运行中subagent（#71023） |

**共性**：自主Agent从"单次执行"向"长链任务"演进时，**执行连续性**成为共同瓶颈。

### 4.2 Cron/定时调度稳定性
| 项目 | 具体诉求 |
|------|---------|
| **OpenClaw** | 孤立Cron任务LLM调用失败（#91363）、OAuth刷新超时导致Cron全部失败（#89278） |
| **NanoBot** | 调度器单次持久化失败后永久死亡（#5373，已修复） |
| **LobsterAI** | 定时任务首次执行结果不推送UI（#1232，已修复） |
| **CoPaw** | 插件可静默创建cron job注入消息（#6916，安全漏洞） |

**共性**：定时任务从"辅助功能"变为"核心能力"，但**持久化失败恢复、认证刷新、权限隔离**仍是技术债。

### 4.3 会话/记忆系统
| 项目 | 具体诉求 |
|------|---------|
| **OpenClaw** | 多玩家记忆架构、信任标签化防御poisoning（#7707, PR #121945） |
| **CoPaw** | 上下文压缩破坏tool_call结构（#5856）、压缩后历史不可见（#6951） |
| **NanoClaw** | /add-hindsight长期记忆MCP封装（#2420） |
| **LobsterAI** | memory模块零测试覆盖（#1162） |

**共性**：记忆系统从"简单日志"向"可审计、可隔离、可压缩"的**生产级存储**演进。

### 4.4 安全与权限模型
| 项目 | 具体诉求 |
|------|---------|
| **OpenClaw** | 跨渠道审批泄漏（#25592）、memory poisoning防御（#7707） |
| **CoPaw** | 端口暴露+无鉴权+命令执行（#6992）、插件静默植入cron（#6916） |
| **NanoBot** | exec.allowPatterns可被shell链绕过（#5306） |
| **NanoClaw** | Telegram配对码弱随机源漏洞（#3229） |

**共性**：插件化架构带来**权限边界模糊**问题，生态普遍从"功能优先"转向"安全优先"。

---

## 5. 差异化定位分析

| 维度 | OpenClaw | CoPaw | Hermes Agent | NanoBot | NanoClaw | PicoClaw |
|------|----------|-------|-------------|---------|----------|----------|
| **核心定位** | 多用户生产网关 | 本地OS级AI助手 | 桌面研究应用 | 轻量级个人Agent | 模板化部署框架 | 嵌入式语音交互 |
| **目标用户** | 企业/多用户场景 | 个人生产力用户 | 研究/开发者 | 学术/验证场景 | DevOps/自动化 | 边缘设备 |
| **技术架构** | 多代理编排+记忆系统 | Electron+OS Shell | Python Desktop+Gateway | Rust+Session持久化 | Go+模板插件 | Go+Whisper ASR |
| **差异化优势** | 多代理并发、记忆架构 | OS级集成、阿里云生态 | 桌面体验、语音链 | 轻量稳定、cron修复 | 发布链路安全硬化 | 低功耗边缘部署 |
| **当前短板** | P1积压、回归多 | v2.1.0回归、杀软误报 | Windows Gateway崩溃 | 功能相对基础 | 社区规模小 | 核心功能推进缓 |

---

## 6. 社区热度与成熟度分层

```
第一梯队（高频迭代，功能竞争激烈）
├── OpenClaw    486 Issues / 500 PRs    → 高频修复期，技术深度领先
├── CoPaw      45 Issues / 50 PRs      → 功能发布期，回归风险上升
└── Hermes      50 Issues / 50 PRs      → 平台适配期，Windows阵痛

第二梯队（稳步演进，技术债清理）
├── NanoBot     11 Issues / 31 PRs      → 稳健期，关键Bug响应快
├── LobsterAI    2 Issues / 10 PRs      → 打磨期，测试补强阶段
├── NanoClaw     2 Issues / 19 PRs      → 健康期，模板系统成熟
└── Moltis       1 Issue  /  4 PRs      → 功能扩展期，连接器开发

第三梯队（维护/停滞）
├── PicoClaw     2 Issues /  9 PRs      → 维护期，依赖更新为主
├── IronClaw     50 Issues / 50 PRs     → 重构期（数据不完整）
├── NullClaw     0 / 0                  → 停滞
└── ZeptoClaw    0 / 0                  → 停滞
```

**成熟度判断**：
- **OpenClaw** 处于"规模扩张后的工程化阵痛"，问题数量与深度均领先，但P1积压反映维护能力承压
- **CoPaw** 处于"功能爆发后的质量收敛"，v2.1.0发布后回归问题集中暴露，需hotfix周期
- **NanoBot** 处于"精准修复期"，问题数量少但关键Bug响应迅速，健康度最优
- **LobsterAI/Moltis** 处于"技术债清理期"，PR多但 Issue 少，反映内部重构为主

---

## 7. 值得关注的趋势信号

### 7.1 从"能用"到"安全可用"的范式转移
**信号**：OpenClaw（memory poisoning防御）、CoPaw（插件权限漏洞）、NanoBot（exec绕过）均在本周聚焦安全议题。
**启示**：Agent生态进入**安全成熟期**，开发者需优先设计权限隔离、输入验证、插件沙箱，而非事后修补。

### 7.2 多代理编排成为竞争力分水岭
**信号**：OpenClaw 6个P1涉及subagent生命周期，CoPaw #6921 反映任务连续性痛点，Hermes #71023 呼吁热更新支持。
**启示**：单Agent能力已趋同质化，**多代理协调、任务链可靠性、状态恢复**将成为下一轮竞争核心。

### 7.3 Cron/自动化从"附加功能"变为"关键基础设施"
**信号**：4个项目同时暴露Cron稳定性问题，且CoPaw出现安全漏洞（插件静默创建cron）。
**启示**：自动化调度需**持久化+故障恢复+权限控制**三重保障，建议开发者优先投入该子系统。

### 7.4 记忆系统进入"架构化"阶段
**信号**：OpenClaw Phase 1C 读写隔离、NanoClaw Hindsight集成、LobsterAI 测试补强、CoPaw 上下文压缩修复。
**启示**：记忆系统从"简单存储"向**可审计、可压缩、可隔离**演进，建议关注持久化策略与隐私边界设计。

### 7.5 平台适配成为隐性成本
**信号**：Hermes Windows Gateway 6个P1集群、CoPaw 杀软误报、PicoClaw 构建依赖问题、Moltis macOS bash兼容。
**启示**：跨平台支持不再是"能跑就行"，需建立**平台专项测试矩阵**，Windows和macOS是常见重灾区。

### 7.6 版本发布策略分化
- **CoPaw**：正式版+beta并行，快速迭代但回归风险高
- **Hermes**：补丁版本汇总656个PR，倾向批量发布
- **NanoClaw**：v2.2.0无破坏性变更，平稳演进
- **OpenClaw**：无新版本，积压修复期

**启示**：高频发布需配套**自动化回归测试+灰度机制**，否则社区信任成本急剧上升。

---

**报告结语**：2026年8月的AI智能体开源生态已进入**工程化深水区**，功能竞赛让位于稳定性与安全治理。OpenClaw以规模领先但承压明显，CoPaw/Hermes在发布后进入质量收敛期，NanoBot以稳健节奏展现健康度标杆。对开发者而言，多代理可靠性、Cron调度健壮性、记忆系统架构、跨平台适配是本期最值得投入的四个方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目日报 | 2026-08-14

## 1. 今日速览

NanoBot 今日活跃度较高，24小时内共产生 11 条 Issue 更新（10 活跃 + 1 关闭）和 31 条 PR 更新（22 待合并 + 9 已合并/关闭）。核心进展集中在 cron 调度器稳定性修复、session 持久化竞态条件处理，以及安全漏洞响应。项目健康度良好，维护者对关键 bug 响应迅速，多个 P2 级问题同日获得修复 PR。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的重要 PR：

| PR | 状态 | 说明 |
|---|---|---|
| [#5374](https://github.com/HKUDS/nanobot/issues/5374) / [#5375](https://github.com/HKUDS/nanobot/issues/5375) / [#5376](https://github.com/HKUDS/nanobot/issues/5376) | ✅ 合并 | Cron 调度器持久化失败存活修复（#5376 为最终合并版） |
| [#4550](https://github.com/HKUDS/nanobot/issues/4550) | ✅ 合并 | 修复 cron 任务跨运行共享 session 上下文问题 |
| [#4556](https://github.com/HKUDS/nanobot/issues/4556) | ✅ 合并 | Dream consolidation 支持 `model_override` 配置 |
| [#5381](https://github.com/HKUDS/nanobot/issues/5381) | ✅ 合并 | WebUI 原生工作区文件夹选择器（macOS/Windows/Linux） |
| [#5384](https://github.com/HKUDS/nanobot/issues/5384) | ✅ 合并 | 恢复仅转录（transcript-only）会话历史 |

**整体推进**：今日重点是 session 一致性与 cron 调度稳定性，9 条已关闭 PR 修复了多个长期存在的隐患，项目稳健性明显提升。

---

## 4. 社区热点

| Issue/PR | 类型 | 热度 | 核心诉求 |
|---|---|---|---|
| [#5373](https://github.com/HKUDS/nanobot/issues/5373) | Bug | ⭐ 高 | Cron 调度器因单次持久化失败永久死亡，已有修复 PR [#5376](https://github.com/HKUDS/nanobot/pull/5376) 已合并 |
| [#5306](https://github.com/HKUDS/nanobot/issues/5306) | 安全 | ⭐⭐ 极高 | `exec.allowPatterns` 可被 shell 链绕过，已关闭但需关注后续补丁版本 |
| [#5298](https://github.com/HKUDS/nanobot/issues/5298) | 功能 | ⭐ 高 | 大工具集 MCP schema 超出上下文预算，对应实现 PR [#5388](https://github.com/HKUDS/nanobot/pull/5388) |
| [#5366](https://github.com/HKUDS/nanobot/issues/5366) | 本地化 | ⭐ 中 | WebUI Agent 活动文本硬编码英文，用户希望按界面语言本地化 |
| [#4841](https://github.com/HKUDS/nanobot/issues/4841) | Bug | ⭐ 中 | Matrix bot 设备显示 "Untrusted"，PR [#5385](https://github.com/HKUDS/nanobot/pull/5385) 已提交修复 |

---

## 5. Bug 与稳定性

### 🔴 高严重度

| Issue | 描述 | Fix PR |
|---|---|---|
| [#5306](https://github.com/HKUDS/nanobot/issues/5306) | `exec.allowPatterns` shell-chain 绕过导致非预期命令执行（安全漏洞） | 已关闭，待安全补丁 |
| [#5373](https://github.com/HKUDS/nanobot/issues/5373) | Cron 调度器单次持久化失败后永久死亡 | ✅ [#5376](https://github.com/HKUDS/nanobot/pull/5376) |
| [#4841](https://github.com/HKUDS/nanobot/issues/4841) | Matrix 交叉签名验证缺失，bot 设备始终显示 Untrusted | ✅ [#5385](https://github.com/HKUDS/nanobot/pull/5385) |

### 🟡 中严重度

| Issue | 描述 | Fix PR |
|---|---|---|
| [#5378](https://github.com/HKUDS/nanobot/issues/5378) | `file-cap` archive 失败时 session 状态已被突变，后续保存无法恢复溢出消息 | ✅ [#5380](https://github.com/HKUDS/nanobot/pull/5380) |
| [#5377](https://github.com/HKUDS/nanobot/issues/5377) | consolidation 截断后 `last_consolidated` 游标前进超过实际保留范围 | ✅ [#5379](https://github.com/HKUDS/nanobot/pull/5379) |
| [#5368](https://github.com/HKUDS/nanobot/issues/5368) | Agent turn 运行中 Copy/Fork 按钮提前出现，造成 UI 状态冲突 | 待处理 |
| [#5382](https://github.com/HKUDS/nanobot/issues/5382) | Windows `os.replace()` 权限错误导致 gateway 崩溃 | ✅ 已合并 |

---

## 6. 功能请求与路线图信号

| Issue | 需求 | 对应 PR | 纳入可能性 |
|---|---|---|---|
| [#5298](https://github.com/HKUDS/nanobot/issues/5298) | MCP 工具集预算模型（model-visible schema 裁剪） | [#5388](https://github.com/HKUDS/nanobot/pull/5388) | ⭐⭐⭐ 高，PR 已提交待审 |
| [#5289](https://github.com/HKUDS/nanobot/issues/5289) | Telegram 贴纸支持与消息反应 | [#5387](https://github.com/HKUDS/nanobot/pull/5387) | ⭐⭐⭐ 高，PR 已提交待审 |
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) | WebUI 支持 MCP Apps host | [#5386](https://github.com/HKUDS/nanobot/pull/5386) | ⭐⭐ 中，PR 已提交但侧重 metadata 保留 |
| [#5358](https://github.com/HKUDS/nanobot/issues/5358) | WebUI session 协作（@mention 功能） | [#5358](https://github.com/HKUDS/nanobot/pull/5358) | ⭐⭐ 中，PR 待合并但有 conflict |
| [#5372](https://github.com/HKUDS/nanobot/issues/5372) | ViBo 持久化内存系统集成提案 | 无 | ⭐ 低，第三方推广性质，需进一步评估 |

---

## 7. 用户反馈摘要

**痛点：**
- **Cron 调度脆弱性**：[#5373](https://github.com/HKUDS/nanobot/issues/5373) 用户反映持久化单点故障导致调度器静默死亡，影响自动化任务可靠性。
- **安全敏感**：[#5306](https://github.com/HKUDS/nanobot/issues/5306) 用户发现 `allowPatterns` 可被 shell 链绕过，表明企业对命令执行白名单有明确安全诉求。
- **上下文膨胀**：[#5298](https://github.com/HKUDS/nanobot/issues/5298) 大量 MCP 工具导致 schema 超出模型上下文预算，影响推理质量与成本。
- **跨平台一致性**：[#4841](https://github.com/HKUDS/nanobot/issues/4841) Matrix 环境下 bot 始终显示 Untrusted，破坏企业部署信任链。

**满意点：**
- WebUI 原生文件夹选择器（[#5381](https://github.com/HKUDS/nanobot/pull/5381)）获得好评，解决了远程部署场景下的路径配置痛点。
- Session 历史恢复能力（[#5384](https://github.com/HKUDS/nanobot/pull/5384)）修复了 transcript-only 会话不可见的退化问题。

---

## 8. 待处理积压

| Issue/PR | 类型 | 未响应时长 | 建议优先级 |
|---|---|---|---|
| [#5368](https://github.com/HKUDS/nanobot/issues/5368) | Bug | 今日 | ⭐⭐ 中 — UI 状态冲突影响用户体验 |
| [#5372](https://github.com/HKUDS/nanobot/issues/5372) | 功能 | 今日 | ⭐ 低 — 第三方推广，需评估可行性 |
| [#5358](https://github.com/HKUDS/nanobot/issues/5358) | 功能 | 2天 | ⭐⭐ 中 — 有 conflict 待解决，session 协作是重要 UX 增强 |
| [#4549](https://github.com/HKUDS/nanobot/issues/4549) | 功能 | 49天 | ⭐ 低 — heartbeat 优化，长期 open 但优先级不高 |
| [#4551](https://github.com/HKUDS/nanobot/issues/4551) | 功能 | 49天 | ⭐ 低 — heartbeat session 隔离配置，同 [#4549] |

> ⚠️ **维护者关注**：[#5306](https://github.com/HKUDS/nanobot/issues/5306) 安全漏洞已关闭但尚未见补丁版本公告，建议发布安全公告并标注受影响版本范围。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报 — 2026-08-14

---

## 1. 今日速览

Hermes Agent 昨日发布 **v0.20.1** 补丁版本，汇总了约 656 个 PR 的稳定变更。过去 24 小时内共新增/活跃 50 条 Issues 和 50 条 PR，活跃度维持在较高水平。主要矛盾集中在 **桌面端 Gateway 重启后的进程管理问题**（多个 Windows/macOS 回归 Bug），以及 TUI 面板可见性和技能索引新鲜度等体验问题。项目整体向前推进明显，但 Windows 桌面端的 gateway 生命周期管理仍是当前最高风险区域。

---

## 2. 版本发布

### v0.20.1 (v2026.8.13) — 补丁版本

- **发布日期：** 2026 年 8 月 13 日
- **性质：** Patch release，汇总自 v0.20.0 以来的约 656 个已合并 PR
- **目标受众：** Docker 镜像、托管部署及通过 latest tag 安装的用户
- **迁移说明：** 无破坏性变更；直接升级至最新 tag 即可

🔗 [GitHub Releases](https://github.com/NousResearch/hermes-agent/releases)

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（按影响度排序）

| PR | 类型 | 说明 |
|---|---|---|
| [#84155](https://github.com/NousResearch/hermes-agent/pull/84155) | 🔧 Fix | 修复 macOS Finder 截图拖拽后 `image not found` 问题，解决短生命周期的临时文件路径偏好错误 |
| [#67257](https://github.com/NousResearch/hermes-agent/pull/67257) | 🔧 Fix | 修复桌面端因 `ReasoningTextPart` 无限递归导致的启动崩溃（RangeError），附带 py39 兼容修复 |
| [#67251](https://github.com/NousResearch/hermes-agent/pull/67251) | 🔧 Fix | 同上崩溃修复的另一合并路径，修复 markdown lexer 在渲染推理内容时的栈溢出 |
| [#85769](https://github.com/NousResearch/hermes-agent/pull/85769) | 🔧 Fix | 统一 `normalize_usage()` 对所有 provider 缓存/用量数据格式的解析，修复 token 计数静默归零问题（整合了 5 个重叠 PR） |
| [#85707](https://github.com/NousResearch/hermes-agent/pull/85707) | 🔧 Fix | 修复 tool-schema 边界类型问题，确保 `cache_control` 标记在应用前完成类型规范化 |

> 项目整体推进：今日主要精力集中在**稳定性修复**（桌面崩溃、用量计算、截图上传）和**语音/缓存路径的底层修正**，同时新增了 Box 生产力技能。

---

## 4. 社区热点

### 最活跃 Issues（按评论数）

| Issue | 评论数 | 主题 | 热度分析 |
|---|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 25 | Skills 索引陈旧/降级（29.8h > 26h 阈值） | 索引更新机制可靠性引发持续关注 |
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | 20 | Windows 桌面重启后 Gateway 被杀死且不再启动（WeChat/QQ 静默） | **P1 回归**，多平台用户受影响，社区反馈强烈 |
| [#84834](https://github.com/NousResearch/hermes-agent/issues/84834) | 16 | Webhook 全面重构 Epic（5×2×3 修复战役） | 架构级改进计划，涉及 ingress/execution/delivery 全链路 |
| [#69592](https://github.com/NousResearch/hermes-agent/issues/69592) | 12 | TUI `/sessions` 和 `/models` 面板在 ambient widget 加载后不可见（第 13 天） | **P1**，核心 TUI 工作流被阻断，长期未修复 |
| [#83390](https://github.com/NousResearch/hermes-agent/issues/83390) | 9 | DeepSeek 辅助标题生成 HTTP 400（`response_format` 不可用） | 👍 2，模型兼容性问题的典型代表 |

### 最活跃 PR

| PR | 主题 |
|---|---|
| [#85773](https://github.com/NousResearch/hermes-agent/pull/85773) | 本地 Whisper STT 可配置 `beam_size` + 启动预热 |
| [#85771](https://github.com/NousResearch/hermes-agent/pull/85771) | MiniMax chunked-PCM TTS 流式提供者 |
| [#85770](https://github.com/NousResearch/hermes-agent/pull/85770) | 修复 wake_word.client 模式在远程后端重启后的静默失效 |
| [#85764](https://github.com/NousResearch/hermes-agent/pull/85764) | 修复 `/new-reset` 会话在 `session_search` 中不可召回的问题 |
| [#85765](https://github.com/NousResearch/hermes-agent/pull/85765) | 修复 Discord 进度消息编辑丢失 thread 路由 |

**热点分析：** 社区对 **桌面端稳定性**（Windows gateway 生命周期、macOS TUI 可见性）和 **语音交互体验**（STT/TTS 配置灵活性）的关注度最高。Webhook 重构 Epic 表明团队正系统性解决消息投递可靠性的深层架构问题。

---

## 5. Bug 与稳定性

### 🔴 P0 / P1（高严重性）

| Issue | 严重程度 | 描述 | Fix PR |
|---|---|---|---|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | **P1** | Windows 桌面重启杀死 Gateway 且不复启，WeChat/QQ/Telegram 静默 | 待确认 |
| [#85344](https://github.com/NousResearch/hermes-agent/issues/85344) | **P1** | `_reap_unsupervised_gateway_orphans` 误杀 macOS launchd 监管的 gateway | 待确认 |
| [#85368](https://github.com/NousResearch/hermes-agent/issues/85368) | **P1** | Windows Gateway 进程反复被 SIGKILL，消息平台掉线 | 待确认 |
| [#84855](https://github.com/NousResearch/hermes-agent/issues/84855) | **P1** | Windows 桌面启动时拒绝权限杀死孤儿 Gateway PID | 待确认 |
| [#85044](https://github.com/NousResearch/hermes-agent/issues/85044) | **P1** | Windows 桌面 `serve` 启动杀死 Scheduled Task 管理的 Gateway | 待确认 |
| [#69592](https://github.com/NousResearch/hermes-agent/issues/69592) | **P1** | TUI 面板不可见，`/reload` 静默失效（持续 13 天） | 待确认 |

### 🟡 P2（中严重性）

| Issue | 描述 |
|---|---|
| [#83427](https://github.com/NousResearch/hermes-agent/issues/83427) | `browser_exec` 在 Hermes venv PYTHONPATH 下报 `pydantic_core ModuleNotFoundError` |
| [#72064](https://github.com/NousResearch/hermes-agent/issues/72064) | `oneshot (-z)` 无法跳过内置 memory 注入，`--ignore-rules` 被静默忽略 |
| [#52339](https://github.com/NousResearch/hermes-agent/issues/52339) | `hermes update` 重建 Desktop 但 `/Applications/Hermes.app` 保持陈旧 |
| [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) | Windows ZIP fallback 删除已构建的 Desktop 应用且不复建 |
| [#80117](https://github.com/NousResearch/hermes-agent/issues/80117) | SQLite POSIX 锁冲突导致 Gateway `APIConnectionError` |
| [#85406](https://github.com/NousResearch/hermes-agent/issues/85406) | Windows + Docker 下 `vision_analyze` 路径分隔符错误 |
| [#76267](https://github.com/NousResearch/hermes-agent/issues/76267) | Windows `sync_back` 在远程后端关闭时丢失沙箱文件修改 |
| [#85104](https://github.com/NousResearch/hermes-agent/issues/85104) | 桌面端同一条 assistant 消息渲染两次（前端问题） |
| [#85745](https://github.com/NousResearch/hermes-agent/issues/85745) | 桌面端 Profile 切换显示错误会话列表 |
| [#83340](https://github.com/NousResearch/hermes-agent/issues/83340) | 桌面端终端中 `hermes cron run` 报告失败但未执行任务 |
| [#84058](https://github.com/NousResearch/hermes-agent/issues/84058) | 桌面端工具调用流式开始时输入框光标丢失 |

### 🟢 已有关闭/修复

| Issue/PR | 说明 |
|---|---|
| [#81639](https://github.com/NousResearch/hermes-agent/issues/81639) [CLOSED] | 工具调用参数修复路径将 `{}` 写入持久化历史导致会话卡死 |
| [#85707](https://github.com/NousResearch/hermes-agent/pull/85707) [CLOSED] | tool-cache 路径 schema 类型边界修复 |
| [#84155](https://github.com/NousResearch/hermes-agent/pull/84155) [CLOSED] | macOS Finder 截图拖拽修复 |
| [#67257 / #67251](https://github.com/NousResearch/hermes-agent/pull/67257) [CLOSED] | 桌面端 Reasoning 渲染崩溃修复 |

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 说明 | 纳入下版本可能性 |
|---|---|---|---|
| [#85773](https://github.com/NousResearch/hermes-agent/pull/85773) | 功能 | 本地 Whisper 可配置 `beam_size` + 启动预热 | ⭐⭐⭐ 高（已在 PR 中，性能优化） |
| [#85771](https://github.com/NousResearch/hermes-agent/pull/85771) | 功能 | MiniMax chunked-PCM TTS 流式 | ⭐⭐⭐ 高（已在 PR 中，补齐 TTS 能力） |
| [#85767](https://github.com/NousResearch/hermes-agent/pull/85767) | 功能 | 内置 Box 生产力技能（文件管理/搜索/AI/Hubs） | ⭐⭐⭐ 高（已在 PR 中） |
| [#4438](https://github.com/NousResearch/hermes-agent/issues/4438) | 功能请求 | 丰富的电子表格 Skill（xlsx/csv） | ⭐⭐ 中（长期需求，无近期 PR） |
| [#67798](https://github.com/NousResearch/hermes-agent/issues/67798) | 功能请求 | 生命周期 Hook 作为跨执行面的共享运行时契约 | ⭐⭐ 中（架构级，需决策） |
| [#71023](https://github.com/NousResearch/hermes-agent/issues/71023) | 功能请求 | 零停机热更新（不杀死运行中 subagent） | ⭐⭐ 中（用户呼声高 👍1，但涉及进程管理重构） |
| [#33049](https://github.com/NousResearch/hermes-agent/issues/33049) | 功能请求 | 可配置的凭证池耗尽 TTL | ⭐ 低（配置项，影响面有限） |
| [#84317](https://github.com/NousResearch/hermes-agent/issues/84317) | 功能请求 | Telegram 冷启动可选择不丢弃待处理更新 | ⭐⭐ 中（平台适配需求） |
| [#75539](https://github.com/NousResearch/hermes-agent/issues/75539) | 功能请求 | 桌面端"将会话移入项目"操作 | ⭐⭐ 中（UX 改进，需设计决策） |

---

## 7. 用户反馈摘要

**核心痛点：**

1. **Windows 桌面 Gateway 生命周期混乱** — 多个独立用户报告同一类问题：桌面启动/重启时无差别杀死已运行的 Gateway 进程（包括 launchd/Scheduled Task 监管的），且不复启。用户反馈"消息平台静默"、"进程反复被 SIGKILL"。这已构成 v0.20.x 的最严重回归集群。

2. **TUI 可用性受损** — `#69592` 用户强调第 13 天仍未修复，`/sessions` 和 `/models` 面板在默认 ambient widget 配置下完全不可见，`/reload` 也无响应，核心工作流被阻断。

3. **桌面端 Profile 系统不稳定** — 多个 Profile 相关 Bug（会话列表显示错误、远程 WS 路由静默回退到本地），用户反映"切换 Profile 后看不到对应会话"。

4. **语音体验改进受认可** — 用户对可配置的 STT beam_size、MiniMax 流式 TTS、wake word 修复等 PR 有积极反馈，说明语音链路的持续投入正在转化为体验提升。

5. **Windows 文件路径兼容性问题频发** — `vision_analyze` 路径分隔符错误、`sync_back` 文件丢失、ZIP fallback 删除已构建应用等，Windows 平台兼容性仍是薄弱环节。

---

## 8. 待处理积压

| Issue | 天数 | 严重度 | 风险 | 建议 |
|---|---|---|---|---|
| [#69592](https://github.com/NousResearch/hermes-agent/issues/69592) | **13+ 天** | P1 | TUI 核心功能完全不可用，影响大量用户 | 优先修复，建议紧急 patch |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 27 天 | P3 | Skills 索引陈旧，依赖 `/docs/skills` 的功能受影响 | 检查 cron 调度状态 |
| [#76267](https://github.com/NousResearch/hermes-agent/issues/76267) | 14 天 | P2 | Windows 远程后端关闭时文件丢失 | 需 Windows 平台专项测试 |
| [#52339](https://github.com/NousResearch/hermes-agent/issues/52339) | 50 天 | P2 | `hermes update` 与 Desktop 版本不同步 | 更新流程需要端到端验证 |
| [#4438](https://github.com/NousResearch/hermes-agent/issues/4438) | 135 天 | P3 | 电子表格 Skill 长期需求 | 考虑纳入 skill 扩展计划 |
| [#35966](https://github.com/NousResearch/hermes-agent/issues/35966) | 166 天 | P3 | 原生桌面/移动端客户端 | 已获 4 👍，路线图中优先级待确认 |

---

**项目健康度评估：** 过去 24 小时项目保持高活跃度（100 条 Issue+PR 更新），但 **v0.20.x 在 Windows 桌面端的 Gateway 生命周期管理存在系统性回归**，6 个 P1 Issue 指向同一根因（`_reap_unsupervised_gateway_orphans` 逻辑过于激进），建议维护者优先统一修复。TUI 面板可见性问题已持续 13 天需紧急关注。语音/缓存/用量计算等底层修复正在有序合并，项目基础能力在持续加固。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期：2026-08-14** | 数据来源：GitHub API

---

## 1. 今日速览

PicoClaw 今日呈现**中等活跃度**，9 条 PR 更新中 6 条待合并、3 条已合并/关闭，以 Dependabot 依赖更新为主，未见核心功能重构或重大修复。共 2 条 Issue 处于活跃状态，其中 **#3281**（Web UI 输入卡顿）已获 1 个 👍，反映用户对交互体验的持续关注。**今日无版本发布**，项目整体处于依赖维护与问题响应阶段，健康度良好但创新推进相对平缓。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（3 条）

| PR | 作者 | 内容概要 |
|---|---|---|
| [#3304](https://github.com/sipeed/picoclaw/issues/3304) | dependabot[bot] | 升级 `anthropic-sdk-go` 1.55.1 → 1.61.0 ✅ 已合并 |
| [#3305](https://github.com/sipeed/picoclaw/issues/3305) | dependabot[bot] | 升级 `aws-sdk-go-v2/service/bedrockruntime` 1.53.3 → 1.56.2 ✅ 已合并 |
| [#3306](https://github.com/sipeed/picoclaw/issues/3306) | dependabot[bot] | 升级 `aws-sdk-go-v2/config` 1.32.25 → 1.32.33 ✅ 已合并 |

> **进展评估**：已关闭的 3 条 PR 均为依赖安全更新，未引入新功能或核心 Bug 修复。项目整体处于**维护性更新阶段**，核心功能代码暂无实质推进。

### 待合并的 PR（6 条）

| PR | 类型 | 内容 |
|---|---|---|
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) | bug fix | 修复 `pnpm-lock.yaml` 中 `semver@7.8.5` 重复映射键导致的构建失败 |
| [#3332](https://github.com/sipeed/picoclaw/pull/3332) | 依赖升级 | `aws-sdk-go-v2` 1.42.0 → 1.43.4 |
| [#3333](https://github.com/sipeed/picoclaw/pull/3333) | 依赖升级 | `mautrix` 0.27.0 → 0.29.0 |
| [#3334](https://github.com/sipeed/picoclaw/pull/3334) | 依赖升级 | `anthropic-sdk-go` 1.55.1 → 1.62.0 |
| [#3335](https://github.com/sipeed/picoclaw/pull/3335) | 依赖升级 | `aws-sdk-go-v2/config` 1.32.25 → 1.32.35 |
| [#3336](https://github.com/sipeed/picoclaw/pull/3336) | 依赖升级 | `aws-sdk-go-v2/service/bedrockruntime` 1.53.3 → 1.57.1 |

> **关键提示**：[#3318](https://github.com/sipeed/picoclaw/pull/3318) 修复了 Web 端构建失败问题，当前标记为 `stale`，需维护者确认是否重新激活合并。

---

## 4. 社区热点

### 🔥 Issue #3281 — Web UI 聊天输入卡顿（高关注）
- **链接**：[Issue #3281](https://github.com/sipeed/picoclaw/issues/3281)
- **状态**：OPEN | 评论：5 | 👍：1
- **作者**：xpader
- **摘要**：当会话历史较长时，Web UI 输入框出现明显延迟，影响打字体验。复现步骤清晰，环境信息完整（PicoClaw 0.3.1 / Go 1.25.11）。
- **分析**：该 Issue 反映了用户对 Web 端交互性能的核心诉求。历史消息渲染或前端状态管理可能是瓶颈，建议维护者优先跟进。

### 📝 Issue #3331 — 支持自定义模型进行 ASR 转写（新功能诉求）
- **链接**：[Issue #3331](https://github.com/sipeed/picoclaw/issues/3331)
- **状态**：OPEN | 评论：0 | 👍：0
- **作者**：stanislavvv
- **摘要**：希望支持非 `*-whisper-*` 模型通过 `/audio/transcriptions` 端点进行处理，建议新增配置 flag（如 `whisper-transcription: true`）以强制走 ASR 路径。
- **分析**：用户希望扩展 ASR 能力至更现代的语音模型，诉求合理但涉及后端 `asr.go` 逻辑改造，需评估与现有 Whisper 路径的兼容性。

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 描述 | Fix PR |
|---|---|---|---|
| 🟡 中 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI 长历史会话输入卡顿 | 暂无 |
| 🟠 高 | [#3318](https://github.com/sipeed/picoclaw/pull/3318) | `pnpm-lock.yaml` 重复键导致构建失败 | 待合并 |

> **稳定性评估**：未发现崩溃或数据丢失类 Bug。[#3318](https://github.com/sipeed/picoclaw/pull/3318) 修复的 lockfile 问题影响构建稳定性，建议尽快合并。

---

## 6. 功能请求与路线图信号

| 请求 | 来源 | 可行性评估 |
|---|---|---|
| 支持非 Whisper 模型进行音频转写 | [Issue #3331](https://github.com/sipeed/picoclaw/issues/3331) | 中等。需改造 `asr.go` 路由逻辑，与现有架构兼容性待评估；可作为插件化方向探索 |
| 依赖持续更新 | 9 条 Dependabot PR | 当前依赖更新频率较高，表明维护者保持对安全与兼容性的关注 |

> **路线图信号**：今日无明确新功能 PR 提交，功能演进以依赖生态更新为主。若 #3331 获得社区支持，可能成为后续版本（0.3.2+）的候选特性。

---

## 7. 用户反馈摘要

- **痛点**：Web UI 在长历史会话下的输入延迟（#3281），用户明确描述了复现步骤并提供了环境信息，说明体验问题已影响实际使用。
- **满意点**：无今日正面反馈记录，但依赖更新频繁反映维护者对安全性的重视。
- **使用场景**：用户关注 ASR 功能的灵活性（#3331），希望摆脱对旧版 Whisper 模型的绑定，使用更现代的语音识别方案。

---

## 8. 待处理积压

| 类型 | 条目 | 建议 |
|---|---|---|
| 🔴 待合并 | [#3318](https://github.com/sipeed/picoclaw/pull/3318) | 构建修复 PR，当前标记 `stale`，建议维护者重新激活并合并，避免下游构建失败 |
| 🟡 待响应 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | 存在 5 条评论，社区关注度较高，建议分配维护者进行性能分析或标注优先级 |
| 🟡 待评估 | [#3331](https://github.com/sipeed/picoclaw/issues/3331) | 新功能请求，评论为 0，建议维护者回应以确认是否纳入路线图 |

---

**项目健康度总结**：PicoClaw 今日依赖更新活跃，构建稳定性问题有待修复，核心功能无突破性进展。建议维护者优先处理 #3318 和 #3281，以提升项目整体用户体验与开发效率。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 | 2026-08-14

## 1. 今日速览
今日 NanoClaw 项目活跃度维持高位，共完成 19 条 PR 更新（13 条已合并/关闭）并正式发布 **v2.2.0**。核心进展集中在三项主线：模板系统向 Agent Plugins 1.0 的格式迁移、CI/CD 发布链路的密码学硬化，以及 Telegram 配对码的加密安全修复。Issues 数量平稳（2 条），整体处于功能迭代与基础设施安全加固并行的健康节奏，无阻塞性回归风险。

## 2. 版本发布
**v2.2.0** 已正式发布。
- **核心更新**：`ncl groups create --template <ref>` 新增就地更新能力。当目标组已携带该模板插件时，命令将转为原地更新而非 mint 重复代理，`dry run` 模式会输出所有插件托管表面（plugin files、skills、MCP 配置）的变更计划。
- **破坏性变更**：无。
- **迁移注意**：无需额外操作，直接升级 CLI 即可。原有 `--template` 用法保持不变，仅行为由“强制新建”转为“存在则更新”。

## 3. 项目进展
今日合并/关闭的 PR 显著推进了以下方向：
- **模板/插件引擎升级**：#3220 将 Agent Templates 升级至 Agent Plugins 1.0.0 目录规范，同步修复 stamp 时的符号链接、权限与密钥硬编码问题；#2909 补齐向导模板流与首代理 stamping 流程，形成完整链路。
- **CI/CD 发布硬化**：#3158、#3238、#3240、#3241 串联了“镜像验证 → 发布者身份绑定 → 签名替代人工审批 → dispatch 触发版本 PR”的自动化闭环，发布链路的可验证性显著提升。
- **基础修复与兼容性**：#3229 修复 Telegram 配对码使用弱随机源的漏洞；#3231 补全 Codex/OpenCode 的插件 MCP cwd 支持；#3145 通过 DB 迁移脚本为历史消息组补填缺失的渠道目标地址。

## 4. 社区热点
- **#3235 [OPEN] 未知发送者审批风暴**：Webhook/机器人触发 `unknown_sender_policy = 'request_approval'` 时生成不可控的审批卡片队列，且拒绝状态无法持久化。反映出高频自动化场景与人工审批网关的兼容缺口。[链接](https://github.com/qwibitai/nanoclaw/issues/3235)
- **#2420 [OPEN] /add-hindsight 长期记忆 MCP 封装**：自 5 月起待合并，为 v2 代理提供 Hindsight 长时记忆桥接。社区对代理记忆持久化的需求持续，该 PR 评论与关注数近期有回升。[链接](https://github.com/qwibitai/nanoclaw/pull/2420)
- **#3243 [OPEN] verify-agent-image 自动合并逻辑修正**：修复因 `allow_auto_merge` 关闭或临时 API 错误导致误判镜像验证结果的问题，直接影响发布

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目日报 | 2026-08-14

## 1. 今日速览
过去 24 小时 IronClaw 保持高度活跃，共处理 50 条 Issues 与 50 条 PR（24 条已合并/关闭，26 条待审），项目处于架构重构与性能基线优化的关键窗口期。核心进展为 `v1.2.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报 — 2026-08-14

---

## 1. 今日速览

LobsterAI 今日保持中等活跃度，过去 24 小时内共产生 2 条 Issue 更新与 10 条 PR 更新（待合并 4 条，已合并/关闭 6 条），无新版本发布。社区贡献者 `fisherdaddy` 集中推进了 UI 重构工作，涉及协作界面、MCP/Skills 视图合并及签到活动常驻化；`MaoQianTu` 持续填补核心模块的测试盲区，今日 PR #1165 计划新增 75 个 Vitest 用例覆盖 `openclawMemoryFile` 与时间上下文模块。整体项目处于**功能打磨与测试补强**阶段，技术债务清理进展稳健。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR（6 条）

| PR | 作者 | 类型 | 说明 |
|----|------|------|------|
| [#2488](https://github.com/netease-youdao/LobsterAI/pull/2488) | fisherdaddy | refactor(cowork) | 重构协作端（cowork）与主渲染端（renderer）之间的通信与界面管理，清理旧有架构 |
| [#2487](https://github.com/netease-youdao/LobsterAI/pull/2487) | fisherdaddy | refactor(skills) | 将 Skills 视图与 MCP 视图合并为统一的「Skills & Connectors」管理面板，降低用户认知负担 |
| [#2485](https://github.com/netease-youdao/LobsterAI/pull/2485) | btc69m979y-dotcom | feat(activity) | 将签到活动调整为 **Evergreen 常驻形态**，取消限时活动逻辑，积分入口跳转网页详情页，对齐套餐摘要展示 |
| [#2486](https://github.com/netease-youdao/LobsterAI/pull/2486) | fisherdaddy | refactor(mcp) | 统一 MCP 卡片/详情 UI 与 Kits、Skills 的视觉风格，复用 `CardOverflowMenu`，新增 `McpCard` 与 `McpDetailModal` |
| [#1232](https://github.com/netease-youdao/LobsterAI/pull/1232) | choyuenga | fix(scheduledTask) | 修复定时任务**首次执行结果不推送到 UI**的 Bug，根因是 `previousRunAtMs` 初始为 0 导致轮询条件失效 |
| [#2484](https://github.com/netease-youdao/LobsterAI/pull/2484) | liugang519 | feat(enterprise) | 企业版相关功能合入，具体内容待进一步确认 |

**整体进展评估**：今日 6 条已关闭 PR 中，4 条为 UI/架构重构（由 `fisherdaddy` 主导），表明项目正在经历一次**前端体验统一化**改造；`#1232` 修复了定时任务的核心可用性问题，`#2485` 将限时活动固化为常驻功能，整体向更稳定的产品形态演进。

---

## 4. 社区热点

### Issue #2489 — [OPEN] 快更新 v4pro！（0 赞，1 评论）
- **链接**: [#2489](https://github.com/netease-youdao/LobsterAI/issues/2489)
- **摘要**: 用户催促更新 v4pro 版本，评论 1 条。
- **诉求分析**: 用户期待新版本（v4pro）的发布，反映社区对迭代速度的关注，属于**版本发布类反馈**。当前无对应 PR，建议维护者评估排期并公开 Roadmap 时间线以安抚用户。

### Issue #1162 — [OPEN, stale] 为 `openclawMemoryFile` 和 `openclawLocalTimeContextPrompt` 补充 Vitest 单元测试
- **链接**: [#1162](https://github.com/netease-youdao/LobsterAI/issues/1162)
- **摘要**: 描述 `openclawMemoryFile.ts`（记忆文件管理）与 `openclawLocalTimeContextPrompt.ts`（时间上下文 Prompt）两个核心模块此前零测试覆盖的背景，计划新增 75 个单元测试。
- **关联 PR**: [#1165](https://github.com/netease-youdao/LobsterAI/pull/1165) 已包含完整实现。

---

## 5. Bug 与稳定性

| 严重程度 | 问题 | 状态 | 修复 PR |
|----------|------|------|---------|
| 🟡 中 | 定时任务首次执行结果不推送到 UI，用户需等待第二次执行才能看到结果 | ✅ 已修复 | [#1232](https://github.com/netease-youdao/LobsterAI/pull/1232) |
| 🟡 中 | 「立即运行」按钮无 loading 状态，点击后无反馈，用户易重复点击；IPC 层同步阻塞 | 🟡 待处理 | [#1163](https://github.com/netease-youdao/LobsterAI/pull/1163) [OPEN, stale] |
| 🟢 低 | 创建自定义 Agent 时可提交重复名称，导致列表歧义 | 🟡 待处理 | [#1166](https://github.com/netease-youdao/LobsterAI/pull/1166) [OPEN, stale] |
| 🟢 低 | `commandSafety.ts`（危险命令检测）与 `coworkMemoryJudge.ts`（记忆质量评分）零测试覆盖，存在潜在安全/质量风险 | 🟡 待处理 | [#1156](https://github.com/netease-youdao/LobsterAI/pull/1156) [OPEN, stale] |

> **稳定性总评**：今日合并的 `#1232` 修复了定时任务的关键可用性问题；`#1163`（立即运行交互反馈）和 `#1166`（重复 Agent 名称）属用户体验类 Bug，已开 PR 但未合并；安全相关模块（`commandSafety`）仍待测试覆盖，建议优先级提升。

---

## 6. 功能请求与路线图信号

| 需求来源 | 内容 | 关联 PR | 纳入下一版本可能性 |
|----------|------|---------|------------------|
| Issue #2489 | 催促 v4pro 版本更新 | — | ⚠️ 无对应 PR，需维护者明确排期 |
| PR #2485 | 签到活动 Evergreen 常驻化 | [#2485](https://github.com/netease-youdao/LobsterAI/pull/2485) ✅ 已合入 | — |
| PR #2487 | Skills & MCP 视图统一 | [#2487](https://github.com/netease-youdao/LobsterAI/pull/2487) ✅ 已合入 | — |
| PR #2486 | MCP UI 风格对齐 | [#2486](https://github.com/netease-youdao/LobsterAI/pull/2486) ✅ 已合入 | — |
| PR #1163 | 定时任务"立即运行"交互优化（loading + 乐观更新 + Gateway 状态同步） | [#1163](https://github.com/netease-youdao/LobsterAI/pull/1163) [OPEN] | 🟢 高 — 修复体验痛点，且 PR 已就绪 |
| PR #1166 | 防止重复 Agent 名称 | [#1166](https://github.com/netease-youdao/LobsterAI/pull/1166) [OPEN] | 🟢 高 — 简单明确的 Bug Fix |
| PR #1156 | 安全/质量模块单元测试补全 | [#1156](https://github.com/netease-youdao/LobsterAI/pull/1156) [OPEN] | 🟡 中 — 测试类 PR，不影响功能但关乎长期稳定性 |
| PR #2484 | 企业版功能 | [#2484](https://github.com/netease-youdao/LobsterAI/pull/2484) ✅ 已合入 | — |

**路线图信号总结**：项目当前重点为**前端体验统一化**与**测试覆盖率提升**，两个方向均有明确 PR 推进。`#1163` 和 `#1166` 应优先合并，二者均为小范围、高价值的交互修复。

---

## 7. 用户反馈摘要

| 来源 | 反馈内容 | 情绪 |
|------|----------|------|
| Issue #2489 | 「快更新 v4pro！」——用户急切期待新版本发布 | 😤 不满/催促 |
| PR #2485 描述 | 签到活动从限时改为 Evergreen 常驻，积分入口改为网页跳转 | ✅ 正面 — 简化了产品逻辑 |
| PR #1232 描述（Bug 报告）| 定时任务首次执行结果不推送，用户需等待第二轮才能看到结果，体验差 | ❌ 负面 — 已修复 |
| PR #1163 描述（Bug 报告）| 点击「立即运行」后界面无反馈，易导致重复点击；右键菜单样式与系统 UI 不一致 | ❌ 负面 — 已开 PR 待处理 |
| PR #1166 描述（Bug 报告）| 创建自定义 Agent 时可提交重复名称，导致列表歧义 | ❌ 负面 — 已开 PR 待处理 |

**核心痛点提炼**：
1. **版本迭代节奏**：用户对 v4pro 发布速度有期待，需加强版本透明度和沟通。
2. **交互反馈缺失**：定时任务的「立即运行」和首次执行结果推送问题暴露了前端反馈机制的薄弱，建议系统性审查所有异步操作的 loading/error/success 状态。
3. **数据安全与质量**：`commandSafety` 和 `coworkMemoryJudge` 零测试覆盖是潜在风险点，用户虽未直接反馈，但一旦误判可能导致严重后果（静默执行危险命令、记忆污染）。

---

## 8. 待处理积压

| 类型 | ID | 标题 | 作者 | 创建时间 | 最后更新 | 积压天数 | 优先级建议 |
|------|-----|------|------|----------|----------|----------|------------|
| 🟡 PR | [#1163](https://github.com/netease-youdao/LobsterAI/pull/1163) | fix(定时任务): 补全"立即运行"交互反馈，引入乐观更新与 Gateway 状态同步 | gongzhi-netease | 2026-03-31 | 2026-08-13 | **136 天** | 🔴 高 — 体验 Bug 修复，PR 已就绪 |
| 🟡 PR | [#1166](https://github.com/netease-youdao/LobsterAI/pull/1166) | fix(agent): prevent duplicate custom agent names | leedalei | 2026-03-31 | 2026-08-13 | **136 天** | 🔴 高 — 简单明确的 Bug Fix |
| 🟡 PR | [#1156](https://github.com/netease-youdao/LobsterAI/pull/1156) | 为 `commandSafety` 和 `coworkMemoryJudge` 补充 Vitest 单元测试 | MaoQianTu | 2026-03-31 | 2026-08-13 | **136 天** | 🟡 中 — 安全/质量相关测试补全 |
| 🟡 Issue | [#1162](https://github.com/netease-youdao/LobsterAI/issues/1162) | 为 `openclawMemoryFile` 和 `openclawLocalTimeContextPrompt` 补充 Vitest 单元测试 | MaoQianTu | 2026-03-31 | 2026-08-13 | **136 天** | 🟡 中 — 关联 PR #1165 已含实现 |
| 🔵 Issue | [#2489](https://github.com/netease-youdao/LobsterAI/issues/2489) | 快更新 v4pro！ | nimamasl114514 | 2026-08-14 | 2026-08-14 | **0 天** | 🟡 中 — 需维护者回复版本规划 |

> **积压警示**：PR #1163、#1166、#1156 及 Issue #1162 均创建超过 **4 个月**，状态标记为 `stale`，但关联 PR 均已就绪。建议维护者尽快审查合并，以清理积压、恢复社区贡献者信心。Issue #2489 为今日新增，建议优先回复以安抚用户情绪。

---

**报告生成时间**: 2026-08-14  
**数据范围**: 过去 24 小时  
**分析师**: Agnes-2.0-Flash (Sapiens AI)

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 | 2026-08-14

---

## 1. 今日速览

Moltis 项目今日整体活跃度中等，过去24小时内产生1个新 Issue 和4个待审 PR，无任何合并或关闭记录。**核心维护者 Lstarsky0 贡献突出**，主导了3个修复类 PR 和1个 flaky test 报告。项目当前无新版本发布，主要工作集中在兼容性修复与新连接器功能开发上，整体向稳定化方向小幅推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日 **0 条 PR 已合并/关闭**，所有 PR 仍处于开放状态，项目整体向前推进幅度较小。

当前待审 PR 中，**PR #1190**（[Add durable CalDAV and channel history connectors](https://github.com/moltis-org/moltis/pull/1190)）为最具功能价值的一项，由开发者 `penso` 提交，引入以下内容：
- 提供器无关的连接器持久化机制
- 原子快照、调度、投影能力
- 本地全量搜索支持
- 只读 CalDAV 数据集及 Slack / Discord / Matrix / Teams 消息历史数据集（无需复制频道凭证）

该 PR 若合并，将显著扩展 Moltis 在多平台数据整合方面的能力，是本项目近期最重要的功能进展。

其余3条 PR（#1191、#1192、#1194）均为修复性质，聚焦于：
- Go 模块路径迁移至 `openclaw` 组织后的兼容性修正
- macOS bash 3.2 空数组展开的防护

---

## 4. 社区热点

| 类型 | 编号 | 标题 | 作者 | 链接 |
|------|------|------|------|------|
| Issue | #1193 | Flaky test: push fanout timeout assertion races under full-suite load | Lstarsky0 | [链接](https://github.com/moltis-org/moltis/issues/1193) |
| PR | #1190 | Add durable CalDAV and channel history connectors | penso | [链接](https://github.com/moltis-org/moltis/pull/1190) |
| PR | #1194 | fix(scripts): guard empty bash array expansions for macOS bash 3.2 | Lstarsky0 | [链接](https://github.com/moltis-org/moltis/pull/1194) |

**热点分析：**
- **Issue #1193** 反映的是测试稳定性问题，flaky test 仅在全量工作区套件运行时复现，说明存在并发竞争条件，对 CI/CD 流水线可靠性构成潜在威胁。
- **PR #1190** 是当前社区关注焦点，引入了多平台连接器持久化能力，属于功能型扩展，而非修复，预计合并后会引起较多测试验证讨论。

---

## 5. Bug 与稳定性

| 严重程度 | 编号 | 类型 | 描述 | Fix PR | 链接 |
|----------|------|------|------|--------|------|
| 中 | #1193 | Flaky Test | `push fanout` 超时断言在全量套件负载下存在竞争条件，3次运行中失败2次 | — | [Issue](https://github.com/moltis-org/moltis/issues/1193) |
| 低 | #1194 | 兼容性 | macOS bash 3.2 下空数组展开触发 `unbound variable` 错误，导致 `just local-validate-full` 直接失败 | PR #1194（待合并） | [PR](https://github.com/moltis-org/moltis/pull/1194) |
| 低 | #1191 / #1192 | 构建失败 | `gogcli` 和 `wacrawl` 模块路径迁移至 `openclaw` 组织后，Go install 因 HTTP 重定向失败 | PR #1191、#1192（待合并） | [PR #1191](https://github.com/moltis-org/moltis/pull/1191) · [PR #1192](https://github.com/moltis-org/moltis/pull/1192) |

**稳定性评估：** 无崩溃或回归报告。现有 Bug 均属于构建/测试环境兼容性问题，尚未影响核心功能。

---

## 6. 功能请求与路线图信号

| 来源 | 描述 | 状态 | 纳入下一版本可能性 |
|------|------|------|-------------------|
| PR #1190 |  durable CalDAV + 多平台消息历史连接器（Slack/Discord/Matrix/Teams） | 待审 | **高** — 功能完整，属于明确的功能扩展方向 |

**路线图信号分析：**
- 项目正在向**多平台数据聚合**方向演进，CalDAV 和即时通讯频道历史的数据接入能力是近期重点。
- `openclaw` 组织的模块迁移暗示项目依赖生态正在整合，未来可能有更多内部工具链统一动作。

---

## 7. 用户反馈摘要

今日无新增用户评论，反馈主要来源于 PR 摘要中的开发者描述：

- **痛点：** macOS 环境下的 bash 版本兼容性问题持续存在（bash 3.2 vs 5.x），影响本地验证流程。
- **使用场景：** 全量测试套件在 idle 10-core macOS 机器上仍出现 flaky test，说明 CI 环境与本地环境存在差异，测试稳定性需进一步保障。
- **满意点：** 无明确正面反馈记录；但从 PR #1190 的功能描述看，多平台连接器设计考虑了"不复制频道凭证"的安全最佳实践，受到开发者认可。

---

## 8. 待处理积压

| 编号 | 类型 | 标题 | 创建时间 | 未响应时长 | 建议 |
|------|------|------|----------|-----------|------|
| #1190 | PR | Add durable CalDAV and channel history connectors | 2026-08-11 | ~3天 | 安排代码审查，此 PR 功能价值高 |
| #1193 | Issue | Flaky test: push fanout timeout | 2026-08-13 | ~1天 | 建议添加 CI 重试机制或补充并发安全测试 |
| #1191 / #1192 / #1194 | PR | openclaw 迁移修复 + macOS bash 兼容修复 | 2026-08-13 | ~1天 | 优先合并，均为修复类，风险低 |

---

**项目健康度评级：🟡 良好（中等活跃度）**

- 无阻塞性 Bug 或崩溃
- 功能开发（CalDAV 连接器）持续推进
- 测试稳定性存在隐忧（flaky test）
- PR 积压3条待审，建议维护者安排审查节奏

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 | 2026-08-14

---

## 1. 今日速览

过去24小时项目保持高活跃度：45条Issue更新（新开/活跃28条，关闭17条）、50条PR更新（待合并31条，已合并/关闭19条），并发布了**2个新版本**（v2.1.0正式版及v2.1.0-beta.5）。社区同时关注到两处安全问题（端口暴露/无鉴权、插件静默植入cron），已触发关闭处理，显示维护团队对安全响应较为敏捷。整体项目健康度良好，功能迭代与安全治理同步推进。

---

## 2. 版本发布

### v2.1.0（正式版）
**核心新增——QwenPaw OS Shell**：支持在可移动、可缩放窗口中打开应用，配备启动器、任务栏、通知系统及保存的布局配置，并实现已安装应用与市场应用共享统一目录（App Center整合）。
🔗 PR #6645

### v2.1.0-beta.5
- **fix(chats)**：处理 dict-like 模型响应 (#6813) → PR #6816
- **fix(memory)**：简化长期记忆引导逻辑 → PR #6942
- **docs(website)**：优化 Files 工作区文档 → PR（截断）

> **迁移注意**：v2.1.0 引入 OS Shell 全新 UI 组件，旧版布局配置可能不兼容；建议先备份 `~/.qwenpaw` 配置目录后再升级。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| #6884 | fix | Auto-Dream 集成容错增强，LLM 返回畸形结构化输出时不再导致整个任务失败 |
| #6387 | feat | Channels 可选依赖按需安装，减小默认依赖体积 |
| #6652 | fix | Mission 模式服务端强制 `max_iterations` 限制，修复子代理无限调度问题（#6505） |
| #6636 | fix | 聊天记录接口增加分页与 GZip 压缩，修复长会话 30s 超时问题（#6635） |
| #6989 | chore | v2.1.0 发布说明（已合并） |

**整体推进**：今日关闭的 PR 集中在**稳定性修复**（Mission 无限循环、长会话超时、Auto-Dream 容错），表明 v2.1.0 发布前后的质量保障仍在密集进行，项目正向"功能冻结 + 问题清零"阶段过渡。

---

## 4. 社区热点

### 讨论最活跃的 Issues（按评论数排序）

1. **#6921** [Bug] 多步骤任务执行中途静默停止，需用户手动输入"继续"才能推进（6条评论）
   - 🔗 https://github.com/agentscope-ai/QwenPaw/issues/6921
   - **分析**：高频痛点，涉及 Agent 自主持续执行能力，与 v2.1.0 的"自动任务执行"定位直接相关，可能影响用户体验口碑。

2. **#6973** [Question] 是否支持阿里云百炼 token plan（5条评论）
   - 🔗 https://github.com/agentscope-ai/QwenPaw/issues/6973

3. **#6811** [Bug, 已关闭] OpenAI Responses 在 Scroll 压缩时忽略 `disable_thinking`，并将 60s 超时误报为 malformed output（5条评论）
   - 🔗 https://github.com/agentscope-ai/QwenPaw/issues/6811

4. **#5856** [Bug] 上下文压缩导致 `tool_call` 结构化数据丢失，引发 400 错误（4条评论，**未修复**）
   - 🔗 https://github.com/agentscope-ai/QwenPaw/issues/5856
   - **分析**：长期未解决的架构级问题，影响使用 context compaction 功能的所有用户，建议维护者优先级上调。

5. **#6047** [Bug, 已关闭] 升级后新会话会错误续写旧 session，`chats.json` 顺序与 session index 不同步（4条评论）

6. **#6847** [Question] QwenPaw 被杀软拦截/强制关停，竞品 WorkBuddy 无此问题（4条评论）
   - 🔗 https://github.com/agentscope-ai/QwenPaw/issues/6847
   - **分析**：涉及 Windows 平台可接受度，需关注是否因打包方式或运行时行为触发误报。

### 安全相关热点

- **#6992** [安全, 已关闭] 端口暴露 + 插件 API 无鉴权 + 任意命令执行 → 攻击者植入 SSH 后门（3条评论）
  - 🔗 https://github.com/agentscope-ai/QwenPaw/issues/6992
- **#6916** [安全, 已关闭] 插件可静默创建 cron job 并向会话注入消息，无需用户审批（2条评论）
  - 🔗 https://github.com/agentscope-ai/QwenPaw/issues/6916

> **分析**：两处安全问题均在报告后短时间内关闭，说明维护团队响应迅速，但暴露出插件权限模型和默认网络暴露配置存在缺口，建议在 v2.1.x 安全补丁中重点加固。

---

## 5. Bug 与稳定性

| 严重度 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高 | #7011 | v2.1.0 回归：并发会话下 Agent 状态写入错误 session 文件（macOS/Feishu） | 无（用户已回退至 2.0.1） |
| 🔴 高 | #7007 | Windows Desktop TUI 启动失败：`transport: Connection closed`，打包的 `qwenpaw.exe` 拒绝 `-m qwenpaw acp` 参数 | 无 |
| 🟠 中 | #6951 | Scroll 压缩后重新进入会话，压缩前历史消息不可见，仅显示 eviction index | 无 |
| 🟠 中 | #6921 | Agent 多步骤任务中途静默停止，等待用户输入"继续" | 无 |
| 🟠 中 | #7008 | Anthropic 模型安全审核误拦截，长历史会话中合法图片被标记为 sensitive（1026错误） | 无（模型端问题） |
| 🟡 低 | #6955 | v2.0.1 pip 安装版概率性启动崩溃（asyncio Windows event loop） | 无 |
| 🟡 低 | #7006 | 语言选项右上角下拉与左下角设置齿轮列表不一致 | 无 |
| 🟡 低 | #7005 | 启用 Shabox 后 UV 无法写入 `~/.cache/uv` 目录 | 用户通过 policy.yaml  workaround |

> **关注**：#7011 和 #7007 均为 v2.1.0 新增回归问题，建议纳入下一个 patch 版本优先修复。#5856（tool_call 丢失）为长期积压的高影响 Bug，至今未修复。

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 匹配 PR | 纳入可能性 |
|---|---|---|---|
| #7013 | Chat 页增加统一工具面板、Web 服务预览、交互式 Web Terminal | — | 🟡 待定，符合"完整 Agent 协作闭环"愿景 |
| #7012 | 会话级模型选择（当前为全局切换） | — | 🟢 高，多会话不同模型是常见需求 |
| #6970 | Chat 独立窗口模式（去侧栏/头部）+ URL 传 apikey + session 列表条件筛选 | — | 🟡 待定，偏企业/嵌入场景需求 |
| #7003 | ViBo 加密内存方案（97.5% token 节省） | — | 🔵 低，外部提案，需评估兼容性 |
| #6976 | 会话级多项目目录绑定 | PR #6976（开放中） | 🟢 高，PR 已提交，正在 Review |
| #6302 | 统一 Provider 发现、模型元数据、路由与 Agent 控制 | PR #6302（开放中） | 🟢 高，架构级重构，可能纳入 v2.2 |
| #6960 | 导入功能：从 Codex/Qoder 迁移配置、技能、插件 | PR #6960（开放中） | 🟢 高，PR 已提交 |
| #6283 | 自动在上下文附加真实时间（已关闭） | — | ✅ 已采纳（关闭） |

---

## 7. 用户反馈摘要

**痛点**：
- **任务连续性差**：#6921 反映 Agent 在执行多步骤任务时频繁"规划后静默停止"，用户需反复输入"继续"，严重影响自动化体验。
- **上下文压缩破坏可见性**：#6951、#5856 指出 Scroll 压缩后原始消息不可见、tool_call 结构丢失，用户认为"压缩只应影响模型输入，不应破坏 transcript"。
- **并发安全性**：#7011 报道 v2.1.0 并发会话状态写错文件，用户已回退版本，说明回归影响实际生产使用。
- **杀软误报**：#6847 反映 Windows 杀软频繁拦截 QwenPaw 进程，影响安装体验，需与竞品对比排查打包差异。

**正面反馈**：
- #6585 用户肯定项目整体质量，仅建议为动态字符计数添加关闭开关（已关闭，预计已处理）。
- #7003 外部贡献者对项目的 33,748 Stars 表示认可，并主动提出内存优化方案。

---

## 8. 待处理积压

| Issue/PR | 时长 | 说明 | 建议 |
|---|---|---|---|
| #5856 | ~37天 | tool_call 结构化数据在上下文压缩中永久丢失，导致 400 错误 | 🔴 高优修复，影响核心功能 |
| #6768 | ~8天 | Agent 完成多步骤任务后进入无限循环，会话卡死数小时（已关闭但需确认根因） | 确认 fix 是否已合入 |
| #7011 | 当日 | v2.1.0 并发会话状态写入错误文件（回归） | 🔴 尽快 hotfix |
| #7007 | 当日 | Windows TUI 启动崩溃（回归） | 🔴 尽快 hotfix |
| #6998 | 开放 | LLM 流未消费导致信号量泄漏（#5411） | PR 待 Review |
| #6302 | ~24天 | Provider 统一架构重构，长期开放中 | 推进 Review 进度 |

---

**综合评估**：CoPaw v2.1.0 发布后社区活跃度维持高位，新功能（OS Shell）获得关注，但同时也暴露了**并发安全**和**Windows TUI**两个回归问题，需尽快发布 patch 修复。安全响应及时，但插件权限模型仍有加固空间。#5856 长期未解决的上下文压缩 Bug 是当下最值得优先处理的积压项。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

⚠️ 摘要生成失败。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*