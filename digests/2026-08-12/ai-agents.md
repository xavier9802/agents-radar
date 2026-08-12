# OpenClaw 生态日报 2026-08-12

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-12 02:27 UTC

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
**日期：2026-08-12** | 数据来源：GitHub (openclaw/openclaw)

---

## 1. 今日速览

过去24小时 OpenClaw 社区保持**极高活跃度**，累计处理 Issues 500 条、PR 500 条，净增活跃 Issue 266 条、PR 60 条。整体项目健康度良好，但存在若干关键稳定性隐患：今日发现 `2026.8.1-beta.1` 版本因遗漏配套插件发布导致启动死循环（#121675，已关闭），暴露发布流程风险；同时 silent reply failure、内存泄漏、子 Agent 消息丢失等长期问题仍无根本修复。新功能方向聚焦于设备配对体验优化、多 Provider 认证管理及 MCP 工具链稳定性。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 | 链接 |
|---|---|---|---|
| #119528 | fix | 修复 Claude CLI 历史恢复后时间戳丢失问题，保障会话连续性 | [PR #119528](https://github.com/openclaw/openclaw/pull/119528) |
| #122381 | test | 移除重复的运行时迁移探测测试，保留核心迁移验证 | [PR #122381](https://github.com/openclaw/openclaw/pull/122381) |
| #119525 | fix | 修复 `memory_search` 超时后重试被 60s 冷却期阻塞的问题 | [PR #119525](https://github.com/openclaw/openclaw/pull/119525) |
| #121994 | fix | F1C 审计修复 v4：接受显式未知调用者证据 | [PR #121994](https://github.com/openclaw/openclaw/pull/121994) |
| #97295 | fix | 飞书插件在 token 无效时重试一次并清除缓存，修复 #97287 | [PR #97295](https://github.com/openclaw/openclaw/pull/97295) |

### 关键进行中 PR（等待维护者审查/作者回复）

- **#82572** [feat/queue] 跨 Gateway 重启持久化 followup 队列（SQLite 存储），解决重启消息丢失问题
- **#120768** [feat/pairing] 一键粘贴设备配对流程，简化多端绑定体验
- **#122300** [fix/ui] 修复多认证 Profile 下 Provider 卡片错误显示 "Credentials rejected"
- **#120332** [fix/config] 替换型渠道插件的配置键不再被 `config validate` 错误拒绝
- **#118579** [fix/discord] Discord 语音转录绑定到实际接收消息的账号，修复多账号环境下的路由错误

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issues（按评论数）

| Issue | 主题 | 评论数 | 评级 | 链接 |
|---|---|---|---|---|
| #121058 | Silent reply failures 在 #116277 关闭后仍复现 | 69 | 🦞 diamond | [Issue #121058](https://github.com/openclaw/openclaw/issues/121058) |
| #116201 | Realtime voice 会话保留无界 provider/consult 状态（内存泄漏） | 64 | 🦞 diamond | [Issue #116201](https://github.com/openclaw/openclaw/issues/116201) |
| #25592 | tool call 之间的文本泄漏到消息频道 | 46 | 🦞 diamond | [Issue #25592](https://github.com/openclaw/openclaw/issues/25592) |
| #7707 | 按来源对记忆条目添加信任标签（防记忆投毒） | 43 | 🌊 tidepool | [Issue #7707](https://github.com/openclaw/openclaw/issues/7707) |
| #92201 | Anthropic thinking signature 回放偶发无效，恢复包装未触发 | 23 | 🦪 silver | [Issue #92201](https://github.com/openclaw/openclaw/issues/92201) |

**热点分析：**
- **回复静默失败（#121058）** 已连续多日成为最高频问题，表明该故障模式的根因尚未定位，社区焦虑情绪上升。
- **实时语音内存泄漏（#116201）** 被标记为 diamond lobster 最高优先级，涉及长时间运行的语音会话资源失控。
- **记忆信任标签（#7707）** 反映用户对 AI 记忆安全性的关注提升，希望防范恶意内容通过非可信来源污染 agent 记忆。

### 👍 点赞最高的 Issues

| Issue | 主题 | 点赞数 | 链接 |
|---|---|---|---|
| #68596 | 可配置 streaming watchdog 超时阈值 | 8 | [Issue #68596](https://github.com/openclaw/openclaw/issues/68596) |
| #42840 | Control UI 支持 MathJax/LaTeX 渲染 | 10 | [Issue #42840](https://github.com/openclaw/openclaw/issues/42840) |

---

## 5. Bug 与稳定性

### 高严重度（P0/P1）

| Issue | 描述 | 状态 | Fix PR | 链接 |
|---|---|---|---|---|
| #121675 | `2026.8.1-beta.1` 未发布配套 `@openclaw/*` 插件，启动收敛守卫导致不可恢复的启动死循环 | ✅ CLOSED | 需重新规范发布流程 | [Issue #121675](https://github.com/openclaw/openclaw/issues/121675) |
| #121058 | Silent reply failures 在 #116277 关闭后持续复现 | 🔓 OPEN | 暂无 | [Issue #121058](https://github.com/openclaw/openclaw/issues/121058) |
| #116201 | Realtime voice 会话无界保留 provider 和 consult 状态 | 🔓 OPEN | 暂无 | [Issue #116201](https://github.com/openclaw/openclaw/issues/116201) |
| #87744 | Codex-backed Telegram 反复超时，turn 无法到达 terminal `turn/completed` | 🔓 OPEN | 暂无 | [Issue #87744](https://github.com/openclaw/openclaw/issues/87744) |
| #97983 | iOS/WebChat 消息附加到 transcript 但不触发/投递 assistant 回复 | 🔓 OPEN | 暂无 | [Issue #97983](https://github.com/openclaw/openclaw/issues/97983) |
| #96827 | `message_tool_only` 模式下 agent 投递 source reply 后不终止，产生级联自回复 | ✅ CLOSED | 已修复 | [Issue #96827](https://github.com/openclaw/openclaw/issues/96827) |
| #89315 | Gateway heap 无限增长，Linux systemd --user 部署被 cgroup OOM 杀死 | ✅ CLOSED | 需验证 | [Issue #89315](https://github.com/openclaw/openclaw/issues/89315) |
| #97616 | OpenClaw 泄漏未回收的 hook/tool 子进程，导致僵尸进程累积 | 🔓 OPEN | 暂无 | [Issue #97616](https://github.com/openclaw/openclaw/issues/97616) |
| #80498 | 子 Agent 完成通知在 tool-use turn 后可能提前或重复 | 🔓 OPEN | 暂无 | [Issue #80498](https://github.com/openclaw/openclaw/issues/80498) |
| #112668 | `sessions_yield` abort-settle timeout 在 2026.7.1-2 仍丢失子 Agent 通知 | 🔓 OPEN | 暂无 | [Issue #112668](https://github.com/openclaw/openclaw/issues/112668) |
| #114020 | Feishu/Telegram 渠道分发失败：`runChannelInboundEvent` 缺少 `runDispatchLifecycle` | 🔓 OPEN | 暂无 | [Issue #114020](https://github.com/openclaw/openclaw/issues/114020) |
| #83337 | 插件/核心版本漂移导致渠道静默失效 | 🔓 OPEN | 暂无 | [Issue #83337](https://github.com/openclaw/openclaw/issues/83337) |
| #71689 | tasks registry 从损坏的 SQLite 镜像恢复失败 | 🔓 OPEN | 暂无 | [Issue #71689](https://github.com/openclaw/openclaw/issues/71689) |

### 中低严重度（P2/P3）

| Issue | 描述 | 状态 | 链接 |
|---|---|---|---|
| #114612 | memory-core SQLite 表无保留策略，持续填充磁盘 | 🔓 OPEN | [Issue #114612](https://github.com/openclaw/openclaw/issues/114612) |
| #90781 | memory-core 叙事生成静默输出空白，写入 fallback diary | 🔓 OPEN | [Issue #90781](https://github.com/openclaw/openclaw/issues/90781) |
| #58957 | 上下文过大时模型切换静默失败 | 🔓 OPEN | [Issue #58957](https://github.com/openclaw/openclaw/issues/58957) |
| #65538 | 流式输出时 screen reader 每 token 播报一次 | 🔓 OPEN | [Issue #65538](https://github.com/openclaw/openclaw/issues/65538) |
| #57256 | `openclaw status` 误报 openclaw-mem0 不可用 | 🔓 OPEN | [Issue #57256](https://github.com/openclaw/openclaw/issues/57256) |
| #42820 | Feishu send action 被 poll schema 污染，阻止文件发送 | 🔓 OPEN | [Issue #42820](https://github.com/openclaw/openclaw/issues/42820) |
| #121953 | DeepSeek cron agent turn 因 `[cron:...]` 前缀被降优先级导致卡顿 | 🔓 OPEN | [Issue #121953](https://github.com/openclaw/openclaw/issues/121953) |
| #92460 | Isolated cron announcer 丢弃 explicit `delivery.channel` | ✅ CLOSED | [Issue #92460](https://github.com/openclaw/openclaw/issues/92460) |
| #92076 | 子 Agent 完成投递在请求方 session 非活跃时失败 | ✅ CLOSED | [Issue #92076](https://github.com/openclaw/openclaw/issues/92076) |
| #91799 | Discord Agents 无法访问 MCP 工具 | ✅ CLOSED | [Issue #91799](https://github.com/openclaw/openclaw/issues/91799) |
| #49223 | WhatsApp inter_session 投递被错误抑制为 REPLY_SKIP | 🔓 OPEN | [Issue #49223](https://github.com/openclaw/openclaw/issues/49223) |

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 关联 PR | 纳入可能性 |
|---|---|---|---|
| #7707 | 记忆信任标签：按来源（用户命令/Web抓取/第三方技能）标记记忆条目，防记忆投毒 | — | ⭐⭐⭐ 高（安全相关） |
| #42475 | 网关层按 Agent 设置成本预算（日/月限额） | — | ⭐⭐ 中（企业场景需求） |
| #72741 | 标准外部安全/护栏检查接口 | — | ⭐⭐⭐ 高（生态扩展） |
| #68596 | 可配置的 streaming watchdog 超时阈值（当前硬编码 30s） | — | ⭐⭐ 中（长推理模型需求） |
| #40982 | 提升或移除 CLI 请求 3 分钟无输出 watchdog 上限 | — | ⭐⭐ 中（长任务场景） |
| #14785 | 减少 tool schema token 开销（当前 ~3,500 tok/session） | — | ⭐⭐⭐ 高（成本敏感） |
| #13700 | Session 快照：保存/加载上下文检查点 | — | ⭐⭐ 中 |
| #42840 | Control UI 支持 MathJax/LaTeX 渲染 | — | ⭐⭐ 中（学术/技术用户） |
| #55249 | Session 标签/昵称，便于识别 | — | ⭐ 低（UX 优化） |
| #16670 | Onboarding Wizard 包含 Memory/Embedding 配置必选项 | — | ⭐⭐ 中（新手友好） |
| #71058 | 单 Gateway 支持多个 Azure/Teams bot | — | ⭐⭐ 中（企业部署） |
| #47910 | Provider 按故障类别回退（隔离 auth 失效的 provider） | — | ⭐⭐⭐ 高（可靠性） |

---

## 7. 用户反馈摘要

### 核心痛点

1. **消息丢失/回复静默失败**：#121058、#87744、#97983、#80498、#112668 等多条高优先级 Issue 集中反映同一类问题——agent 响应未能可靠送达用户。用户抱怨"模型已完成但回复未出现"，且缺乏明确错误提示。

2. **资源泄漏与稳定性**：#116201（内存无界保留）、#89315（heap 无限增长）、#97616（僵尸进程）、#114612（SQLite 无界增长）表明长期运行的 Gateway 实例存在累积性资源问题，威胁生产环境可靠性。

3. **渠道集成脆弱性**：飞书（#42820、#114020）、Telegram（#87744）、iMessage（#115531）、WhatsApp（#49223）、Discord（#91799）等渠道均有用户报告特定场景下的失败，反映多渠道支持的质量参差不齐。

4. **发布流程风险**：#121675 暴露了 `2026.8.1-beta.1` 遗漏配套插件的发布事故，直接影响所有依赖 `@openclaw/*` 插件的用户。

### 用户满意度

- **

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-08-12 | 分析范围：OpenClaw 生态及相关项目**

---

## 1. 生态全景

个人 AI 助手开源生态呈现**头部项目高频迭代、中小项目差异化深耕**的格局。OpenClaw 作为核心参照系保持极高活跃度（500+ Issue/PR/日），但稳定性问题（silent reply failures、内存泄漏、渠道脆弱性）成为生态共性痛点。Hermes Agent 与 ZeroClaw 紧随其后，分别聚焦企业级多租户架构重构与多模态管道加固。中小项目如 PicoClaw、NanoClaw、LobsterAI 在特定场景（路由 agent 上下文、MCP 远程支持、思考级别配置）快速验证需求，而 Moltis 等代表"本地优先"路线的静谧推进者补充生态多样性。整体生态正从"功能验证期"向"生产可靠性期"过渡，消息路由确定性、Token 效率、安全边界成为下一阶段核心竞争点。

---

## 2. 各项目活跃度对比

| 项目 | Issues | PR | Release | 健康度 | 核心关注点 |
|------|--------|-----|---------|--------|-----------|
| **OpenClaw** | 500+ | 500+ | — | 🟡 高活跃但隐患多 | 稳定性（silent failures、内存泄漏）、多渠道集成、发布流程规范 |
| **Hermes Agent** | 50 | 50 | — | 🟢 活跃且健康 | Windows Desktop 更新机制、多租户架构、Token 效率优化、代码重构 |
| **ZeroClaw** | 50 | 50 | — | 🟢 高强度迭代中 | 架构 RFC 评审、多模态管道、安全修复、SOP 控制面收敛 |
| **LobsterAI** | 4 | 9 | 2026.8.11 | 🟢 稳健迭代 | 思考级别配置、配置安全、启动阻塞 Bug、快捷键优化 |
| **PicoClaw** | 3 | 6 | — | 🟡 活跃但积压 | 路由 agent 上下文管理、配置静默失效、LINE webhook 修复 |
| **NanoClaw** | 1 | 7 | — | 🟡 中等活跃 | 消息静默丢弃、MCP 远程 HTTP 支持、Agent 模板迁移 |
| **Moltis** | 0 | 1 | — | 🟢 低活跃稳健 | 本地 CalDAV 持久化、provider-neutral 连接器 |
| **NullClaw** | 0 | 0 | — | ⚪ 休眠 | — |
| **ZeptoClaw** | 0 | 0 | — | ⚪ 休眠 | — |
| **NanoBot/IronClaw/CoPaw** | — | — | — | ⚠️ 数据缺失 | 摘要生成失败 |

---

## 3. OpenClaw 在生态中的定位

**优势：**
- **社区规模与活跃度断层领先**：日处理 500+ Issue/PR，是次级项目（50 量级）的 10 倍，具备最强的问题发现与修复能力
- **多渠道集成覆盖最广**：Telegram、Discord、飞书、WhatsApp、iMessage、LINE 等，但稳定性是其软肋
- **MCP 生态兼容性推进最快**：远程 HTTP MCP Server 支持已从引擎层打通至各 provider

**技术路线差异：**
- vs Hermes Agent：OpenClaw 走"广覆盖渠道 + 核心稳定性"路线，Hermes 走"深度重构 + 企业多租户"路线
- vs LobsterAI：OpenClaw 聚焦 Gateway/Agent 架构，LobsterAI 聚焦桌面客户端体验（思考级别、快捷键、窗口提醒）
- vs PicoClaw/NanoClaw：OpenClaw 是平台级项目，二者是其生态的轻量化/嵌入式变体

**社区规模对比：**
OpenClaw（500+/日）>> Hermes Agent ≈ ZeroClaw（50/日）> LobsterAI ≈ PicoClaw ≈ NanoClaw（个位数/日）> Moltis（1/日）

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **消息路由确定性** | OpenClaw、Hermes Agent、NanoClaw | Silent reply failures（#121058）、消息静默丢弃（#3226）、子 Agent 通知丢失（#80498/#112668）——多项目反映同一根因：消息在网关/路由层丢失且无错误提示 |
| **Token 效率优化** | OpenClaw、Hermes Agent | Tool schema 注入开销（~3,500 tok/session）、懒加载 Tool Schema（#6839）、减少 tool schema token 开销（#14785）——50+ 工具场景下的成本焦虑 |
| **资源泄漏治理** | OpenClaw、Hermes Agent | 内存无界保留（#116201/#89315）、僵尸进程（#97616）、会话状态泄漏（#84201）——长期运行 Gateway 的生产可靠性威胁 |
| **配置安全与可观测性** | OpenClaw、LobsterAI、PicoClaw | 配置静默丢失（#1237）、配置项无效无提示（#3328）、Stream watcher 超时可配置（#68596）——用户从"能用"转向"可控" |
| **多租户/隔离架构** | Hermes Agent、OpenClaw | memory 操作绕过 hook 导致租户隔离失效（#34352）、Provider 按故障类别回退（#47910）——企业级部署的结构性挑战 |
| **MCP 生态兼容** | OpenClaw、NanoClaw | 远程 HTTP MCP Server 支持、Tavily/Exa 搜索 Provider 集成——工具链标准化需求 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 全渠道 Gateway + Agent 编排 | 企业/高级用户，需多渠道集成 | 多 Provider 认证、MCP 工具链、子 Agent 异步通信 |
| **Hermes Agent** | 桌面客户端 + 多租户企业部署 | 企业 IT、多用户场景 | God-file 重构（#78647）、Lazy Tool Schema、OAuth refresh 管理 |
| **LobsterAI** | 桌面客户端 UX 优化 | 个人用户、效率导向者 | 思考级别 per-model、窗口提醒、快捷键系统 |
| **PicoClaw** | 嵌入式/边缘设备（Raspberry Pi） | 边缘计算、资源受限场景 | Dispatch rules 路由 agent、LINE/Telegram forum topic 支持 |
| **NanoClaw** | 轻量级 Agent 模板化 | 快速原型、插件生态 | Agent Plugins 1.0.0 目录结构、Setup Wizard、升级事务化 |
| **ZeroClaw** | 多模态管道 + 安全加固 | 安全敏感场景、研究用户 | 全像素级图像校验、SSRF 防护、SOP 控制面收敛 |
| **Moltis** | 本地数据优先（CalDAV/私有数据） | 隐私导向用户、本地部署 | Provider-neutral connector、bounded full-text search、prompt-compiled dataset plans |

---

## 6. 社区热度与成熟度

```
活跃度分层：
┌─────────────────────────────────────────────────────────────┐
│  🔥 高频迭代层（500+/日）                                     │
│     OpenClaw — 功能扩张期，稳定性债务累积                      │
├─────────────────────────────────────────────────────────────┤
│  🟡 快速迭代层（50/日）                                       │
│     Hermes Agent — 架构重构期（god-file 分解、多租户）          │
│     ZeroClaw — 安全加固期（RFC 评审、多模态管道）               │
├─────────────────────────────────────────────────────────────┤
│  🟢 稳健推进层（个位数/日）                                   │
│     LobsterAI — 质量巩固期（配置安全、思考级别精细化）           │
│     PicoClaw — 功能补全期（路由 agent 上下文、LINE 修复）        │
│     NanoClaw — 生态扩展期（MCP 远程支持、模板迁移）             │
│     Moltis — 静谧积累期（本地 CalDAV 连接器）                   │
├─────────────────────────────────────────────────────────────┤
│  ⚪ 休眠/数据缺失层                                           │
│     NullClaw、ZeptoClaw、NanoBot、IronClaw、CoPaw              │
└─────────────────────────────────────────────────────────────┘
```

**成熟度判断：**
- **OpenClaw**：功能最完整，但生产可靠性待验证（silent failures、内存泄漏未根本修复）
- **Hermes Agent**：处于"重构阵痛期"，god-file 分解（#78647）是长期技术债清理，多租户架构（#34352）尚未官方落地
- **LobsterAI**：成熟度最高，Bug 修复闭环快（#1237→#1241、#2475），版本发布节奏稳定
- **PicoClaw/NanoClaw**：快速验证阶段，PR 积压（stale 标记）反映维护者 review 瓶颈

---

## 7. 值得关注的趋势信号

### 信号 1：消息路由确定性成为生态级痛点
**涉及项目**：OpenClaw（#121058/#80498/#112668）、Hermes Agent（#83213）、NanoClaw（#3226）
**趋势解读**：多项目同时暴露"消息静默丢失"问题，表明当前 Agent 架构在异步通信、子 Agent 通知、跨渠道路由层存在系统性缺陷。下一代框架需在消息生命周期管理上引入显式 ack/nack 机制与可观测性保证。

### 信号 2：Token 效率从"优化项"升级为"刚需"
**涉及项目**：OpenClaw（#14785）、Hermes Agent（#6839，18👍）
**趋势解读**：50+ 工具场景下 schema 注入消耗 3,500-5,000 tokens，对本地模型部署者形成硬性约束。Lazy Tool Schema Loading（两阶段注入）已成为社区共识，预计 2026 Q3-Q4 将成为主流实现。

### 信号 3：架构重构进入深水区
**涉及项目**：Hermes Agent（#78647 god-file 分解）、NanoClaw（#3220 Agent 模板迁移）
**趋势解读**：早期"功能优先"的代码积累开始反噬可维护性。god-file 分解、破坏性版本升级（Agent Plugins 1.0.0）反映项目从"验证期"进入"工程化期"，维护者需平衡技术债清理与用户迁移成本。

### 信号 4：安全与隔离从附加项变为核心能力
**涉及项目**：Hermes Agent（#34352 多租户隔离）、NanoClaw（#3226 消息安全）、ZeroClaw（#9819 图像校验/#8713 SSRF 防护）
**趋势解读**：企业级部署需求推动架构级安全设计。memory 操作绕过 hook、OAuth refresh 失效、SSRF 漏洞等问题表明，安全已从"功能层防护"转向"架构层内建"。

### 信号 5：本地优先与隐私可控路线崛起
**涉及项目**：Moltis（本地 CalDAV/#1190）、OpenClaw（#7707 记忆信任标签）
**趋势解读**：用户对数据主权意识提升，本地持久化、记忆来源信任标签、provider-neutral connector 等需求反映"私有化部署"从企业场景向个人用户渗透。

---

**报告结语**：2026 年 8 月的个人 AI 助手开源生态正经历从"功能竞赛"到"可靠性竞赛"的转折。OpenClaw 作为参照系暴露的稳定性问题具有生态代表性，而 Hermes Agent 的架构重构、LobsterAI 的体验打磨、Moltis 的本地化探索共同勾勒出下一阶段的技术演进路径。对开发者而言，消息路由确定性、Token 效率优化、架构级安全是必须提前布局的三个关键领域。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-08-12**

---

## 1. 今日速览

Hermes Agent 项目今日保持高度活跃，过去24小时内共产生 **50 条 Issue 更新**（49 新开/活跃 + 1 关闭）和 **50 条 PR 更新**（42 待合并 + 8 已合并/关闭），无任何新版本发布。社区活跃度旺盛，围绕 Windows Desktop 更新机制、网关会话管理、工具架构重构三大主题形成了集中讨论。整体项目健康度良好，技术债清理（god-file 分解）与生产级 bug 修复同步推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 作者 | 说明 |
|---|---|---|---|
| [#78149](https://github.com/NousResearch/hermes-agent/pull/78149) [CLOSED] | Bug fix | tiammomo | 修复 CLI 识别 prefixed MCP toolset 的问题 |
| [#78172](https://github.com/NousResearch/hermes-agent/pull/78172) [CLOSED] | Bug fix | tiammomo | 修复 cron 调度中 per-profile 并发上限 enforcement |
| [#78143](https://github.com/NousResearch/hermes-agent/pull/78143) [CLOSED] | Bug fix | tiammomo | 修复 kanban dry-run 计数未纳入全局并发上限的问题 |

上述三个 PR 均由 **tiammomo** 提交，聚焦于 cron/kanban 调度系统的并发控制修复，已合并完成。

### 今日重点开放 PR（高价值）

- **[PR #84212](https://github.com/NousResearch/hermes-agent/pull/84212)** — 修复 Windows 更新后 gateway 冷启动静默失败问题（关联 Issue #84185），增加启动验证步骤
- **[PR #83432](https://github.com/NousResearch/hermes-agent/pull/83432)** — WhatsApp bridge 安全加固，防止本地进程冒充拦截消息
- **[PR #84198](https://github.com/NousResearch/hermes-agent/pull/84198)** — 修复 `/reset` 后新会话在所有列表中不可见的问题
- **[PR #84201](https://github.com/NousResearch/hermes-agent/pull/84201)** — 修复 delegated terminal 会话的环境快照泄漏
- **[PR #82891](https://github.com/NousResearch/hermes-agent/pull/82891)** — 安全修复：锁定 KittenTTS wheel 的 sha256 哈希，防止第三方包篡改

---

## 4. 社区热点

### 高讨论 Issue 排行

| Issue | 主题 | 评论数 | 👍 | 链接 |
|---|---|---|---|---|
| #78647 | Epic: 分解 20 个 god files | 67 | 0 | [Issue #78647](https://github.com/NousResearch/hermes-agent/issues/78647) |
| #6839 | 懒加载 Tool Schema，减少 Token 开销 | 38 | 18 | [Issue #6839](https://github.com/NousResearch/hermes-agent/issues/6839) |
| #34352 | 多租户 Hermes 架构方案 | 25 | 3 | [Issue #34352](https://github.com/NousResearch/hermes-agent/issues/34352) |

### 热点分析

- **#78647**（god-file 分解 Epic）是当前讨论最激烈的架构议题，作者 **andrexibiza** 推动全仓库级别的代码拆分，已建立明确的 repo-wide policy："all god files are sharded, never reverted"。这是一个长期的重构战略，预计将显著改善代码可维护性。

- **#6839**（懒加载 Tool Schema）获得 **18 个 👍**，反映出社区对 token 开销问题的强烈共鸣。50+ 工具每次 API 调用注入完整 schema 消耗 ~3,500-5,000 tokens，对本地模型部署影响尤为显著。

- **#34352**（多租户方案）提出 memory 操作绕过 hook 系统导致租户隔离不可行的核心问题，作者声称已在生产环境运行修复方案数月。这暗示了当前架构在多租户场景下的结构性缺陷。

---

## 5. Bug 与稳定性

### P1 级严重问题

| Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | Windows Desktop 重启后 gateway 被杀掉且未重新拉起，WeChat/QQ 静默 | Open | [PR #84212](https://github.com/NousResearch/hermes-agent/pull/84212) 已提交 |
| [#84185](https://github.com/NousResearch/hermes-agent/issues/84185) | Windows 更新后 gateway 冷启动静默死亡（无日志/无 PID） | Open | [PR #84212](https://github.com/NousResearch/hermes-agent/pull/84212) |
| [#84109](https://github.com/NousResearch/hermes-agent/issues/84109) | `/reset` 后创建的新会话在所有列表中不可见（回归） | Open | [PR #84198](https://github.com/NousResearch/hermes-agent/pull/84198) |
| [#83213](https://github.com/NousResearch/hermes-agent/issues/83213) | 后台进程完成通知在 `/new` 后路由到错误会话 | Open | 待 fix |
| [#84200](https://github.com/NousResearch/hermes-agent/issues/84200) | macOS Desktop 更新后 SIGTERM launchd 管理的 gateway | Open | 待 fix |
| [#52179](https://github.com/NousResearch/hermes-agent/issues/52179) | Bedrock Guardrails 配置后从未强制执行 | Open | 待 fix |

### P2 级问题

| Issue | 描述 | 状态 |
|---|---|---|
| [#73779](https://github.com/NousResearch/hermes-agent/issues/73779) | Feishu 多租户模式下 WebSocket receive loop 崩溃 | Open |
| [#83427](https://github.com/NousResearch/hermes-agent/issues/83427) | browser_exec 因 pydantic_core 缺失崩溃 | Open |
| [#63717](https://github.com/NousResearch/hermes-agent/issues/63717) | Windows Desktop 更新失败综合诊断（7 个关联根因） | Open |
| [#69672](https://github.com/NousResearch/hermes-agent/issues/69672) | FTS5 索引 NUL sentinel 导致数据库完整性问题 | Open |
| [#81410](https://github.com/NousResearch/hermes-agent/issues/81410) | Nous OAuth refresh 在事件循环暂停后返回 invalid_grant | Open |
| [#84102](https://github.com/NousResearch/hermes-agent/issues/84102) | Local TTS 写入 Vorbis 编码导致平台语音气泡静默降级 | Open |
| [#82186](https://github.com/NousResearch/hermes-agent/issues/82186) | Windows Desktop 更新按钮 PermissionError (WinError 5) | Open |

### Bug 统计

- 今日新增 P1 级 Issue：**4 个**
- P1 问题已有 Fix PR：**2 个**（#84212, #84198）
- Windows Desktop 相关问题占据当日 Bug 报告的 ** majority**，是当前的稳定性重灾区

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 可能性评估 |
|---|---|---|
| [#6839](https://github.com/NousResearch/hermes-agent/issues/6839) | Lazy Tool Schema Loading — 两阶段工具注入减少 Token 开销 | ⭐⭐⭐⭐ 高 — 社区关注度高（18👍），架构价值明确 |
| [#83244](https://github.com/NousResearch/hermes-agent/issues/83244) | 添加 Antigravity (Google) 作为一等 OAuth provider | ⭐⭐⭐ 中 — 需求合理，但需评估维护成本 |
| [#67440](https://github.com/NousResearch/hermes-agent/issues/67440) | Blast-radius review mode with proof-backed safety facts | ⭐⭐ 低 — 实验性功能，需更多设计 |
| [#72658](https://github.com/NousResearch/hermes-agent/issues/72658) | Pre-completion vault verification gate for kanban | ⭐⭐ 低 — 特定工作流需求，适用范围有限 |
| [PR #84202](https://github.com/NousResearch/hermes-agent/pull/84202) | OneBot 11 平台适配器（QQ 支持） | ⭐⭐⭐⭐ 高 — 社区贡献，扩展平台覆盖 |
| [PR #84209](https://github.com/NousResearch/hermes-agent/pull/84209) | `host.attachFileToComposer` SDK 接口 | ⭐⭐⭐ 中 — 增强插件能力 |
| [PR #84192](https://github.com/NousResearch/hermes-agent/pull/84192) | 富插件 OS 通知 + deeplink 激活 | ⭐⭐⭐ 中 — 提升用户体验 |

---

## 7. 用户反馈摘要

### 痛点集中区

1. **Windows Desktop 更新机制存在系统性缺陷**
   - 多个 Issue 指向同一根因：`hermes update` 后 gateway 无法正常启动
   - 用户 **alainmfatwahe-cpu** (#63717) 提供了 3 周内 7 个关联根因的综合诊断，说明问题长期存在且影响深远
   - 用户 **zuowen7** (#83683) 报告 Desktop 重启导致 WeChat/QQ 完全静默

2. **多租户场景下的架构局限**
   - **NimbleCoAI** (#34352) 指出 memory 操作完全绕过 hook 系统，导致租户隔离必须 fork core
   - 用户已在生产环境运行修复方案数月，暗示官方实现滞后

3. **Token 效率焦虑**
   - **jarviszomine** (#6839) 量化了工具 schema 注入的开销：50+ 工具每次调用消耗 3,500-5,000 tokens
   - 18 个 👍 表明这是广泛存在的痛点，尤其影响本地模型部署者

4. **会话状态管理回归**
   - **#84109** 和 **#83213** 均指向 session 生命周期管理的回归问题
   - 用户 **shaggy2626** 明确指出这是 `d2a4d373eb` 提交引入的回归

### 正面反馈

- **技能系统改进**：[PR #84213](https://github.com/NousResearch/hermes-agent/pull/84213) 修复 skill write-approval 的静默失败问题，填补了用户体验缺口
- **安全加固**：[PR #83432](https://github.com/NousResearch/hermes-agent/pull/83432) 为 WhatsApp bridge 增加持久化随机 secret 和 challenge-response 认证，提升了安全透明度

---

## 8. 待处理积压

### 需维护者重点关注

| Issue | 类型 | 创建时间 | 天数未响应 | 说明 |
|---|---|---|---|---|
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) | 架构缺陷 | 2026-05-29 | ~75 天 | 多租户 memory 隔离问题，已有生产修复方案 |
| [#6839](https://github.com/NousResearch/hermes-agent/issues/6839) | 性能优化 | 2026-04-09 | ~125 天 | 懒加载 Tool Schema，18👍，高价值 |
| [#52179](https://github.com/NousResearch/hermes-agent/issues/52179) | 安全 Bug | 2026-06-24 | ~80 天 | Bedrock Guardrails 未执行，安全功能形同虚设 |
| [#67442](https://github.com/NousResearch/hermes-agent/issues/67442) | 架构缺陷 | 2026-07-19 | ~25 天 | 跨进程 turn serialization 需要 DB-level lease |
| [#78642](https://github.com/NousResearch/hermes-agent/issues/78642) | 重构 | 2026-08-04 | ~8 天 | `tools/mcp_tool.py` 7,230 行 god file 拆分 |

### 建议优先级

1. **#34352** — 多租户问题影响企业级部署，且已有社区验证的修复方案，应优先评估合入
2. **#52179** — 安全相关，Bedrock Guardrails 配置后不执行可能带来合规风险
3. **#6839** — 性能优化，社区呼声高，与 #78647 的架构重构可协同推进

---

**报告生成时间：2026-08-12**
**数据来源：NousResearch/hermes-agent GitHub Repository**

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期：2026-08-12 | 数据周期：2026-08-11 ~ 2026-08-12**

---

## 1. 今日速览

PicoClaw 今日保持高活跃度：过去24小时共产生 **3 条 Issues**（2 条活跃 / 1 条已关闭）与 **6 条 PR**（全部待合并）。Issue 端聚焦于路由代理上下文管理和 LINE webhook 配置缺失消费逻辑等 bug；PR 端则有 6 个待合并修复与新功能提案，覆盖路由 agent 历史管理、Telegram 私有聊天主题支持、Exa 搜索提供商集成及 LINE 配置告警修复。**无新版本发布**，但社区对 bug 修复的贡献密集，项目整体处于积极维护状态。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 被合并，但 **6 条待合并 PR** 均为有效修复或功能增强，预计近期将集中合入主干：

| PR | 类型 | 摘要 |
|----|------|------|
| [#3314](https://github.com/sipeed/picoclaw/pull/3314) | Bug Fix | 修复 `customAllowPatterns` 未生效的 bug，`guardCommand` 中默认拒绝模式优先级过高导致用户配置的 shell 命令被错误拦截 |
| [#3316](https://github.com/sipeed/picoclaw/pull/3316) | Bug Fix | 修复通过 dispatch rules 路由的 agent 无法正确管理会话上下文（历史、摘要、压缩及 seahorse 引导）的问题 |
| [#3329](https://github.com/sipeed/picoclaw/pull/3329) | Bug Fix | 修复 [#3328](https://github.com/sipeed/picoclaw/issues/3328)，将 LINE 的 `webhook_host/port` 从静默忽略改为启动时告警，避免配置无效 |
| [#3315](https://github.com/sipeed/picoclaw/pull/3315) | Feature | 支持 Telegram 私有聊天中的 forum topic 模式，补全 `IsTopicMessage` 字段判断 |
| [#3317](https://github.com/sipeed/picoclaw/pull/3317) | Feature | LLM 响应 debug 日志中新增 `prompt cache tokens` 信息，便于排查 DeepSeek/Cloudflare AI Gateway 等提供商的缓存命中情况 |
| [#3299](https://github.com/sipeed/picoclaw/pull/3299) | Feature | 新增 Exa 原生 web search provider，支持 `type: "auto"` 和 `contents.highlights`，兼容现有时间范围过滤参数 |

---

## 4. 社区热点

- **[Issue #3301](https://github.com/sipeed/picoclaw/issues/3301)** — `/clear` 和 session auto-compression 在通过 dispatch rules 路由到非默认 agent 的会话中失效（3 条评论，活跃讨论中）。用户反映在 Raspberry Pi 上运行 PicoClaw 0.3.1，通过 Discord/Telegram 路由到自定义 agent 后，上下文管理完全失效，已复现路径清晰。
- **[Issue #3294](https://github.com/sipeed/picoclaw/issues/3294)** — `/list models` 仅显示当前模型（已关闭）。用户配置了多个模型但命令只返回当前活动模型，与命令命名预期不符。该 Issue 因 stale 被关闭，但问题本身尚未在代码层面修复。
- **[PR #3316](https://github.com/sipeed/picoclaw/pull/3316)** — 直接关联 Issue #3301，由同一作者提交，修复路由 agent 的上下文管理缺失。这是今日最受关注的修复 PR。

---

## 5. Bug 与稳定性

| 级别 | 问题 | 状态 | Fix PR |
|------|------|------|--------|
| 🔴 高 | [#3301](https://github.com/sipeed/picoclaw/issues/3301) — 路由 agent 的 `/clear` 与 session auto-compression 失效 | OPEN | [#3316](https://github.com/sipeed/picoclaw/pull/3316) 待合并 |
| 🔴 高 | [#3328](https://github.com/sipeed/picoclaw/issues/3328) — LINE `webhook_host/port` 配置静默无效 | OPEN | [#3329](https://github.com/sipeed/picoclaw/pull/3329) 待合并 |
| 🟡 中 | [#3294](https://github.com/sipeed/picoclaw/issues/3294) — `/list models` 只显示当前模型（stale 关闭，未实质修复） | CLOSED（stale） | 无 |
| 🟡 中 | [#3314](https://github.com/sipeed/picoclaw/pull/3314) — `customAllowPatterns` 配置不生效 | OPEN（PR） | 自身即为 fix |

---

## 6. 功能请求与路线图信号

- **Exa 原生搜索集成** [#3299](https://github.com/sipeed/picoclaw/pull/3299)：用户社区对多样化 web search provider 有持续需求，PR 已完整实现并兼容现有参数，具备纳入下一版本的条件。
- **Telegram 私有聊天 topic 支持** [#3315](https://github.com/sipeed/picoclaw/pull/3315)：补全 Telegram Bot API 中 `IsTopicMessage` 的判断，覆盖 forum supergroup 之外的使用场景，属于功能完善类 PR。
- **LLM 缓存 Token 可观测性** [#3317](https://github.com/sipeed/picoclaw/pull/3317)：针对 DeepSeek 等支持 prompt cache 的提供商，增加 debug 日志输出，利于运维排查，实用性强。

以上三项 PR 质量较好、范围明确，预计将随下一版本一并发布。

---

## 7. 用户反馈摘要

- **路由 agent 上下文管理断裂**：用户通过 dispatch rules 将对话路由到独立 agent 后，发现历史记忆、自动压缩均不生效，严重影响多 agent 场景下的使用体验。这是今日社区最核心的痛点（[#3301](https://github.com/sipeed/picoclaw/issues/3301)、[#3316](https://github.com/sipeed/picoclaw/pull/3316)）。
- **配置静默失效**：LINE webhook 相关配置项虽有默认值和文档，但代码中从未消费，用户配置后无任何提示，排查成本高（[#3328](https://github.com/sipeed/picoclaw/issues/3328)、[#3329](https://github.com/sipeed/picoclaw/pull/3329)）。
- **模型列表命令语义不符**：`/list models` 预期列出所有配置模型，实际仅返回当前模型，与命令命名产生认知偏差（[#3294](https://github.com/sipeed/picoclaw/issues/3294)）。
- **安全白名单机制失效**：用户将命令加入 `customAllowPatterns` 后仍被拦截，暴露 `guardCommand` 中默认拒绝模式的优先级逻辑缺陷（[#3314](https://github.com/sipeed/picoclaw/pull/3314)）。

---

## 8. 待处理积压

- **[Issue #3294](https://github.com/sipeed/picoclaw/issues/3294)** — `/list models` 功能缺陷虽以 stale 关闭，但问题本身未被修复。建议维护者评估后 reopen 并纳入修复计划，或补充说明为何仅显示当前模型。
- **[PR #3315](https://github.com/sipeed/picoclaw/pull/3315) / [#3317](https://github.com/sipeed/picoclaw/pull/3317) / [#3299](https://github.com/sipeed/picoclaw/pull/3299)** — 三条功能型 PR 均已标 `[stale]`，虽内容为有效贡献，但长期未获维护者回应。建议尽快 review 合并或给予明确反馈，避免贡献者流失。
- **[PR #3316](https://github.com/sipeed/picoclaw/pull/3316) / [#3314](https://github.com/sipeed/picoclaw/pull/3314)** — 两条关键 bug fix PR 同样处于待合并状态，直接影响多 agent 路由和命令安全白名单两个核心功能，优先级较高，建议优先 review。

---

**项目健康度评估：良好。** 社区贡献活跃，bug 修复 PR 针对性强且与 Issues 形成闭环；主要风险在于 stale 标记的 PR 积压较多，维护者 review 节奏需加快以维持贡献者积极性。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-08-12

---

## 1. 今日速览

NanoClaw 过去24小时保持中等活跃度：共 **1 条新 Issue** 和 **7 条 PR 更新**（4 条待合并、3 条已合并/关闭），无新版本发布。团队在 MCP 远程支持、Agent 模板格式迁移和升级健壮性等核心路径上持续推进，基础设施层稳定性也在同步加固。社区反馈集中暴露了消息去重逻辑的隐性缺陷，需引起重视。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 核心内容 |
|---|---|---|
| [#3190](https://github.com/nanocoai/nanoclaw/pull/3190) | **Utility Skill** | 新增 **Tavily MCP Tool Skill**，扩展项目内置搜索能力 |
| [#3092](https://github.com/nanocoai/nanoclaw/pull/3092) | **Feature** | 引擎与 Claude Provider 层支持 **远程 Streamable HTTP MCP Servers**（`{ type: 'http', url }` 配置） |
| [#3221](https://github.com/nanocoai/nanoclaw/pull/3221) | **Feature** | 补齐 codex 和 opencode provider 对远程 HTTP MCP 的支持，解决上一步 PR 遗留的 stdio-only 兼容问题 |

**进展评估：** 本次更新显著推进了 MCP 生态兼容性——远程 HTTP MCP 服务器从引擎层到各 provider 层已完整打通；Tavily Skill 的合入丰富了默认工具集。项目整体在**扩展性与集成能力**方向稳步前进。

---

## 4. 社区热点

### 🔥 Issue #3226 — 消息静默丢失
> **[OPEN] Inbound messages silently dropped when a platform reuses a message id**  
> 作者: dweekly | 创建: 2026-08-10 | 评论: 1  
> [链接](https://github.com/nanocoai/nanoclaw/issues/3226)

**核心诉求：** 当平台在同一会话中复用已有 message ID 时，入站消息被**静默丢弃**，用户完全感知不到异常，现象等同于"Agent 无视了消息"。

**分析：** 这是典型的**静默失败（silent failure）问题**，比显式报错更难排查。用户无法区分"Agent 没有回复"与"消息从未到达 Agent"，严重影响用户体验和可观测性。该 Issue 反映社区对**消息路由透明性**和**错误可感知性**的强烈需求，建议作为中高优先级处理。

---

## 5. Bug 与稳定性

| 严重程度 | 问题 | 状态 | Fix PR |
|---|---|---|---|
| 🟡 **中** | 入站消息因 ID 复用被静默丢弃，用户无感知（#3226） | OPEN | 暂无 |
| 🟢 **低** | 已有消息组连线缺少 destination 条目（影响部分存量数据） | OPEN | [#3145](https://github.com/nanocoai/nanoclaw/pull/3145) |

**#3145** 已提交迁移脚本（migration 021），用于回填现有 wirings 的 destination 数据，当前待合并。

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 推测纳入版本 |
|---|---|---|
| Agent 模板格式升级为 **Agent Plugins 1.0.0 目录结构** | [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) | 下一主版本（含 `feat!` 破坏性标记） |
| 首次创建 Agent 时引导式模板选择（**Setup Wizard**） | [#2909](https://github.com/nanocoai/nanoclaw/pull/2909) | 近期版本（与 #3220 协同） |
| **升级事务化**，防止中断导致状态不一致 | [#3195](https://github.com/nanocoai/nanoclaw/pull/3195) | 近期版本 |
| 远程 HTTP MCP 全面支持（引擎 + 多 provider） | [#3092](https://github.com/nanocoai/nanoclaw/pull/3092), [#3221](https://github.com/nanocoai/nanoclaw/pull/3221) | 已合并 |

**判断：** 模板系统重构（#3220 + #2909）是近期最大功能里程碑，涉及破坏性变更，预计将作为独立主版本发布。升级事务化 (#3195) 和数据库回填 (#3145) 属于稳定性补强，将随后续 patch 版本推出。

---

## 7. 用户反馈摘要

- **痛点：** 消息 ID 复用导致静默丢弃（#3226）——用户无法区分 Agent 无响应与消息未到达，缺乏基本的可观测性。
- **正面：** 远程 MCP HTTP 支持的完整打通（#3092 + #3221）受到关注，说明用户对 **MCP 生态兼容性**有明确需求。
- **新增能力：** Tavily Skill 合入（#3190）丰富了默认工具集，满足搜索类场景需求。
- **运维诉求：** 升级事务化（#3195）反映用户希望获得更可靠的升级体验，避免中途失败导致系统不可用。

---

## 8. 待处理积压

| 类型 | PR/Issue | 开放时长 | 备注 |
|---|---|---|---|
| 📌 **Feature** | [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) — Agent 模板格式迁移 | ~2 天 | 破坏性变更，需充分审查与迁移文档 |
| 📌 **Feature** | [#2909](https://github.com/nanocoai/nanoclaw/pull/2909) — Setup Wizard 模板流程 | ~40 天 | 与 #3220 协同，长期待合并 |
| 📌 **Fix** | [#3195](https://github.com/nanocoai/nanoclaw/pull/3195) — 升级事务化 | ~6 天 | 稳定性关键 PR |
| 📌 **Fix** | [#3145](https://github.com/nanocoai/nanoclaw/pull/3145) — 回填 wirings destination | ~15 天 | 存量数据修复 |
| 🐛 **Bug** | [#3226](https://github.com/nanocoai/nanoclaw/issues/3226) — 消息静默丢弃 | ~2 天 | 建议优先回应，用户可观测性痛点 |

> ⚠️ **#2909** 已开放约 40 天仍未合并，建议维护者评估优先级或补充 Review 反馈。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI 项目动态日报
**日期：2026-08-12 | 数据周期：2026-08-11 ~ 2026-08-12**

---

## 1. 今日速览

过去24小时 LobsterAI 保持中等活跃度：**4 条 Issue 更新、9 条 PR 更新、1 个新版本发布**。核心亮点是发布了 **2026.8.11** 版本，并合并了多项关键改进：Per-model thinking level（思考强度按模型独立配置）、Settings 未保存确认机制、窗口焦点提醒、快捷键优化等。3 条 Issue 被关闭（含 1 条由对应 PR 修复），整体项目健康度良好，技术债务清理推进中。

---

## 2. 版本发布

### 📦 LobsterAI 2026.8.11

**链接：** https://github.com/netease-youdao/LobsterAI/releases

**更新内容：**
| 类型 | 描述 | PR |
|------|------|----|
| `feat(cowork)` | 添加 `collapse-agent-tasks` 快捷键，支持在输入时组合修饰键触发快捷键 | [#2469](https://github.com/netease-youdao/LobsterAI/pull/2469) |
| `feat(cowork)` | 侧边栏中标记计划任务（scheduled task）会话，便于识别 | [#1277?](https://github.com/netease-youdao/LobsterAI/pull/2469) |

**破坏性变更：** 无

**迁移注意：** 无特殊迁移要求，功能为新增/优化类。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 状态 | 类型 | 说明 |
|----|------|------|------|
| [#2475](https://github.com/netease-youdao/LobsterAI/pull/2475) | ✅ 已合并 | Bug Fix | **模型思考级别独立化**：修复了之前多模型共享同一 `thinking_level` 的互斥 Bug，每个模型现在可独立记忆思考深度设置 |
| [#2477](https://github.com/netease-youdao/LobsterAI/pull/2477) | ✅ 已合并 | Release | 2026.8.10 版本合并入 main，包含多模块改进 |
| [#2476](https://github.com/netease-youdao/LobsterAI/pull/2476) | ✅ 已合并 | feat(ui) | **Escape 键全局关闭顶层弹窗**：Modal 迁移至 document.body，支持嵌套弹窗时单层 Escape 关闭最外层 |
| [#2457](https://github.com/netease-youdao/LobsterAI/pull/2457) | ✅ 已合并 | feat(models) | **可配置思考级别**：支持服务端驱动的思考级别选项，持久化 per-session/per-agent 选择，支持 OpenClaw 别名映射 |
| [#1239](https://github.com/netease-youdao/LobsterAI/pull/1239) | ✅ 已合并 | feat(main) | **任务完成窗口提醒**：AI 任务完成/出错时，后台状态下自动闪烁任务栏（Windows）或弹跳 Dock 图标（macOS） |
| [#1241](https://github.com/netease-youdao/LobsterAI/pull/1241) | ✅ 已合并 | feat(settings) | **Settings 关闭确认机制**：修复 Issue #1237，新增 dirty check，拦截三种关闭路径（背景点击/X/Cancel） |
| [#2474](https://github.com/netease-youdao/LobsterAI/pull/2474) | ✅ 已合并 | fix(sidebar) | 修复侧边栏 Sites 图标描边宽度对齐问题 |

**项目整体推进：** 今日共合并 **7 条 PR**，覆盖模型配置、UI 交互、稳定性提醒三大方向，技术债务清理（#1237/#1239）和用户痛点响应速度良好。

---

## 4. 社区热点

### 讨论活跃 Issue/PR

| ID | 标题 | 状态 | 评论 | 热度分析 |
|----|------|------|------|----------|
| [#1237](https://github.com/netease-youdao/LobsterAI/issues/1237) | Settings 关闭无确认，配置静默丢失 | ✅ 已关闭（由 #1241 修复） | 2 | **高频痛点**：用户修改 API Key 等敏感配置后意外丢失，直接影响工作流，已修复 |
| [#1240](https://github.com/netease-youdao/LobsterAI/issues/1240) | 大模型受限后无法切换，整体瘫痪 | ✅ 已关闭 | 2 | **关键稳定性问题**：单 API 限流导致全应用不可用，反映错误隔离机制不足 |
| [#2062](https://github.com/netease-youdao/LobsterAI/issues/2062) | 任务超过最大时长报错 | ✅ 已关闭 | 2 | 长期任务（24h+）超时中断，用户关心后台执行状态可观测性 |
| [#1183](https://github.com/netease-youdao/LobsterAI/issues/1183) | 循环跳出遮罩启动网关 | 🟡 开放 | 1 | **阻塞性 Bug**：Windows 平台启动循环卡死，尚无修复 PR |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | Electron 依赖升级（40.2.1 → 43.3.0） | 🟡 开放 | 0 | 安全/性能升级，由 Dependabot 发起，长期未合入 |
| [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | 隐藏 OpenClaw 主 Agent 会话 | 🟡 开放 | 0 | UX 改进，清理会话列表噪音，长期未合入 |

**诉求分析：**
- 用户对 **配置安全性**（#1237）和 **错误隔离**（#1240）诉求强烈，属于核心稳定性问题
- #1183 为高优先级 Bug，影响启动体验，建议优先处理

---

## 5. Bug 与稳定性

### 今日报告/关闭的 Bug

| 严重级别 | Issue | 描述 | Fix PR | 状态 |
|----------|-------|------|--------|------|
| 🔴 高 | [#1183](https://github.com/netease-youdao/LobsterAI/issues/1183) | Windows 平台添加模型后反复弹出网关启动遮罩，无法正常进入主界面 | 无 | 🟡 待处理 |
| 🟡 中 | [#1240](https://github.com/netease-youdao/LobsterAI/issues/1240) | 单一 API 受限导致所有对话框任务瘫痪，缺乏降级/切换机制 | 无（Issue 已关闭，可能为预期行为或已缓解） | ✅ 已关闭 |
| 🟡 中 | [#2062](https://github.com/netease-youdao/LobsterAI/issues/2062) | 24h 长期任务超时中断，状态反馈不明确 | 无 | ✅ 已关闭 |
| 🟢 低 | [#1237](https://github.com/netease-youdao/LobsterAI/issues/1237) | Settings 关闭无确认导致配置丢失 | [#1241](https://github.com/netease-youdao/LobsterAI/pull/1241) | ✅ 已修复 |
| 🟢 低 | [#2475](https://github.com/netease-youdao/LobsterAI/pull/2475) | 多模型思考级别互斥 Bug | 已合入 | ✅ 已修复 |

**稳定性评估：** 今日关闭 3 条 Issue，其中 2 条为核心痛点。#1183 为阻塞性 Bug 仍待处理。

---

## 6. 功能请求与路线图信号

### 用户提出的新功能需求

| 来源 | 需求描述 | 关联 PR/状态 | 纳入可能性 |
|------|----------|--------------|------------|
| [#1239](https://github.com/netease-youdao/LobsterAI/pull/1239) | 任务完成时闪烁任务栏/Dock 图标 | ✅ 已合并 | — |
| [#2457](https://github.com/netease-youdao/LobsterAI/pull/2457) | 按模型/会话独立配置思考级别 | ✅ 已合并 | — |
| [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | 隐藏内部 Agent 会话，净化侧边栏 | 🟡 待合并 | **高** — UX 清理，无风险 |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | Electron 大版本升级（40→43） | 🟡 待合并 | **高** — 安全/性能必需 |
| #2062 | 长期任务状态可观测性 | 无 PR | **中** — 需产品决策 |

**路线图信号：**
- **思考级别精细化**（per-model/per-session）已落地，后续可能扩展至更多模型参数
- **窗口焦点提醒**功能已合并，预期会成为标准体验
- **内部会话隐藏**和 **依赖升级** 为低风险高收益项，建议优先合入

---

## 7. 用户反馈摘要

| 反馈主题 | 内容提炼 | 情绪倾向 |
|----------|----------|----------|
| **配置安全** | "修改 API Key 后未保存直接关闭，所有修改静默丢失" — 用户对此体验极度不满，涉及工作流中断风险 | ❌ 负面（已修复） |
| **错误隔离** | "一个 API 受限，整个应用瘫痪，连其他模型也无法使用" — 反映缺乏错误隔离和降级机制 | ❌ 负面 |
| **长期任务** | "24h 任务超时后不确定是停止了还是后台在跑" — 状态反馈不清晰，用户焦虑 | ⚠️ 中性偏负 |
| **启动卡死** | "关闭模型开关保存后，首页反复弹出网关启动遮罩，无法正常使用" | ❌ 负面（待修复） |
| **快捷键效率** | "希望在打字时也能使用修饰键快捷键，支持折叠 Agent 任务" | ✅ 正面（已合入） |
| **思考深度** | "两个模型不能同时设非默认思考级别，设了 B 就把 A 冲掉" | ❌ 负面（已修复） |

---

## 8. 待处理积压

| 类型 | ID | 标题 | 创建时间 | 滞留时长 | 建议优先级 |
|------|----|------|----------|----------|------------|
| 🐛 Bug | [#1183](https://github.com/netease-youdao/LobsterAI/issues/1183) | 一直循环跳出遮罩启动网关 | 2026-04-01 | ~4 个月 | 🔴 高 — 阻塞性 |
| 🔄 PR | [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | Electron 依赖升级（40.2.1 → 43.3.0） | 2026-04-02 | ~4 个月 | 🔴 高 — 安全/兼容性 |
| 🔄 PR | [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | 隐藏 OpenClaw 主 Agent 会话 | 2026-04-01 | ~4 个月 | 🟡 中 — UX 清理 |

**维护者关注建议：**
1. **#1183** 为 Windows 平台启动阻塞问题，需优先排查网关启动逻辑
2. **#1277** Electron 跨大版本升级涉及潜在 breaking changes，建议安排专项测试
3. 两个长期 Issue（#1240、#2062）已关闭但无明确修复记录，建议补充说明或关闭原因

---

*报告生成时间：2026-08-12 | 数据来源：GitHub API*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-08-12

## 1. 今日速览

Moltis 今日整体活跃度较低，过去24小时内无 Issues 更新，亦无新版本发布。唯一动态为 PR #1190 提交待合并，聚焦于本地 CalDAV 连接器持久化能力扩展。项目当前处于功能积累期，社区参与度平稳，维护节奏健康但节奏偏缓，适合视为"静默推进"日。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

| PR | 状态 | 内容概要 |
|----|------|---------|
| [#1190](https://github.com/moltis-org/moltis/pull/1190) | 🔵 待合并 | 新增 durable local CalDAV connectors，涵盖 provider-neutral 连接器持久化、原子快照、调度、投影及本地全量全文搜索能力；引入 prompt-compiled dataset plans 与只读 `connectors` agent 工具 |

本 PR 若合并，将为 Moltis 本地日历数据接入提供关键基础设施支撑，推进项目向"本地优先、隐私可控"的方向稳步演进。

## 4. 社区热点

- **PR #1190** — 唯一活跃条目，当前 👍 0、评论数未定，暂无社区热议。建议关注合并后用户试用反馈，预测该功能将受到本地数据管理场景用户的重点关注。

> 链接：[PR #1190](https://github.com/moltis-org/moltis/pull/1190)

## 5. Bug 与稳定性

今日无新增 Bug 报告或稳定性相关 Issues。

## 6. 功能请求与路线图信号

PR #1190 明确指向以下路线图方向：

- **本地数据持久化**：provider-neutral connector 架构表明 Moltis 正强化本地数据接入能力，降低对云端服务的依赖
- **Agent 工具生态**：引入只读 `connectors` agent 工具，说明项目持续完善 agent 可调用能力，契合个人 AI 助手定位
- **全文搜索本地化**：bounded local full-text search 显示项目对隐私敏感场景的支持意图

**预测**：该 PR 合并后可能纳入下一主要版本，作为 CalDAV 集成功能的核心基础。

## 7. 用户反馈摘要

今日无 Issues 更新，无新增用户反馈。上一 PR 摘要中提及的 `Settings > Connectors` 界面扩展，暗示用户有管理多账号/数据集的强烈需求，预计合并后可能迎来相关体验反馈。

## 8. 待处理积压

| 类型 | 条目 | 说明 |
|------|------|------|
| PR | [#1190](https://github.com/moltis-org/moltis/pull/1190) | 已提交待合并，建议维护者优先审查，功能价值明确且影响面广 |

---

**项目健康度评估**：🟡 平稳 — 无异常波动，核心功能持续迭代，社区参与度处于合理水平，建议关注 PR #1190 合并进展及后续用户反馈。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 | 2026-08-12

## 1. 今日速览
过去 24 小时 ZeroClaw 社区保持高强度运转，共处理 50 条 Issue 与 50 条 PR。Issue 以新开与活跃讨论为主（40 活跃 / 10 关闭），PR 队列中 49 条待合并、仅 1 条已合/关，反映项目正处于密集的功能迭代与安全加固期。整体健康度良好：架构 RFC 评审、多模态管道加固、SOP 控制面收敛三条主线同步推进，但维护者决策与 PR 合并节奏偏慢，存在一定积压风险。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
今日唯一已合/关 PR 为 **#9936**（`fix(sync): cherry-pick upstream security and correctness fixes`），从上游同步 9 项安全与正确性修复，跳过两项已合入的变更，保障了基线稳定性。多项高优先级修复已进入待合并队列：
- **#9819** 引入全像素级图像校验，解决畸形多媒体导致 Provider 请求失败的问题；
- **#8713** 为 `file_download` 补充 SSR

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*