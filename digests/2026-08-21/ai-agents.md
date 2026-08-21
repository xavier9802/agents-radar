# OpenClaw 生态日报 2026-08-21

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-21 01:43 UTC

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
**日期：2026-08-21 | 数据周期：2026-08-20 ~ 2026-08-21**

---

## 1. 今日速览

过去24小时 OpenClaw 项目保持高活跃度，共产生 500 条 Issue 更新和 500 条 PR 更新，社区参与度旺盛。无新版本发布，当前主要版本为 `v2026.8.1-beta.2`（正在验证中）。Issue 中聚焦于多个 P0/P1 级 Bug 修复（Session 状态、消息丢失、崩溃循环），PR 侧也有若干关键修复待合并（如 Nostr SecretRef 配置丢失、会话启动投影恢复、Claude CLI OAuth 等）。整体来看，项目处于 beta 迭代期，维护团队正在集中处理历史积压的稳定性问题，社区贡献活跃度较高。

---

## 2. 版本发布

**无新版本发布。**

当前最新候选版本为 `v2026.8.1-beta.2`，发布验证 Issue [#125626](https://github.com/openclaw/openclaw/issues/125626) 仍处于活跃状态，由维护者 Patrick-Erichsen 发起，要求测试人员在真实网关上升级并完成工作表验证。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 主题 | 作者 | 状态 |
|---|---|---|---|
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | 插件安装策略警告审查功能（Control UI） | jesse-merhi | ✅ 已关闭（已合并） |
| [#126921](https://github.com/openclaw/openclaw/pull/126921) | CLI `sessions --json` 记录身份修复 | steipete | ✅ 已关闭（已合并） |
| [#125471](https://github.com/openclaw/openclaw/pull/125471) | Claude CLI OAuth 在 Control UI 可用性修复 | VACInc | ✅ 已关闭（已合并） |

### 关键待合并 PR

- **[#126934](https://github.com/openclaw/openclaw/pull/126934)** — Nostr SecretRef 配置账户消失问题修复（`channels.nostr.privateKey` 配置丢失），由 steipete 提交，影响 Nostr 频道运营者。
- **[#126931](https://github.com/openclaw/openclaw/pull/126931)** — 停止持久化仅运行时技能目录，修复多会话操作者的性能问题，替代了被污染的 PR #126684。
- **[#123189](https://github.com/openclaw/openclaw/pull/123189)** — 恢复 Chat 启动投影中嵌入频道运行，修复 Control UI 中活跃会话显示为空的问题。
- **[#122918](https://github.com/openclaw/openclaw/pull/122918)** — Control UI 支持 Tailscale 身份验证 HTTP 读取，解决 Tailscale Serve 场景下的会话认证断连。
- **[#125822](https://github.com/openclaw/openclaw/pull/125822)** — 会话启动期间模型控件稳定性修复，防止 Extra high 推理强度被重置。
- **[#126935](https://github.com/openclaw/openclaw/pull/126935)** — 安全策略扫描从 `agents.list` 迁移到 `agents.entries` 键控映射的修复，影响沙箱/工具策略扫描准确性。
- **[#126616](https://github.com/openclaw/openclaw/pull/126616)** — HTTP Chat 固定用户会话绑定修复，防止 Raycast 等客户端多实例共享单一会话导致上下文膨胀。

**总体评估：** 过去24小时有 127 条 PR 已合并/关闭，373 条待处理，维护团队在 Beta 验证期间仍保持了较高的合并效率，重点集中在状态管理、认证和 UI 稳定性三个方向。

---

## 4. 社区热点

### 讨论最活跃的 Issues

| Issue | 标题 | 评论数 | 👍 | 热度 |
|---|---|---|---|---|
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | Per-agent 成本预算网关级强制 | 23 | 1 | 🔥 高 |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | 集中式文件名编码工具（多编码 Content-Disposition） | 20 | 1 | 🔥 高 |
| [#125626](https://github.com/openclaw/openclaw/issues/125626) | v2026.8.1-beta.2 发布验证 | 18 | 0 | 🔥 高 |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | Gateway 升级到 2026.7.1 后启动失败 | 14 | 3 | 🔥 高 |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | google-vertex/gemini-3.1-pro-preview 报错 "Cannot convert undefined or null to object" | 14 | 3 | 🔥 高 |

### 讨论最活跃的 PRs

| PR | 标题 | 影响面 |
|---|---|---|
| [#121576](https://github.com/openclaw/openclaw/pull/121576) | 模型特殊 Token 剥离时仅在单词字符间插入分隔符 | 跨20+频道/应用的全局修复 |
| [#89040](https://github.com/openclaw/openclaw/pull/89040) | 嵌入式 Bootstrap 上下文事件循环硬化 + 子阶段计时 | 网关核心性能 |
| [#122918](https://github.com/openclaw/openclaw/pull/122918) | Control UI Tailscale 身份验证支持 | 远程部署体验 |

**热点分析：**
- **#42475** 成本预算功能反映运营方对多 Agent 场景下费用控制的迫切需求，与 LiteLLM 代理场景直接相关。
- **#48788** 文件名编码问题影响飞书等多语言渠道，PR #48578 仅修复了 UTF-8/Latin-1 场景，社区呼吁架构级解决方案。
- **#108435** 和 **#38327** 均为 P0/P1 回归 Bug，评论热度高说明影响面广，分别涉及 Gateway 启动和 Google Vertex 集成。

---

## 5. Bug 与稳定性

### P0 严重级别

| Issue | 标题 | 类型 | Fix PR |
|---|---|---|---|
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | Gateway 升级到 2026.7.1 后启动失败（崩溃循环） | Regression | 待确认 |
| [#119270](https://github.com/openclaw/openclaw/issues/119270) | 文件工具删除目标路径前导 `@`，导致写入/删除错误文件 | Behavior | 待确认 |
| [#48920](https://github.com/openclaw/openclaw/issues/48920) | Live Docs 超前于 Release（IsolatedSessions 文档缺失） | Regression | 待确认 |

### P1 严重级别

| Issue | 标题 | 类型 | Fix PR |
|---|---|---|---|
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | google-vertex/gemini-3.1-pro-preview "Cannot convert undefined or null to object" | Regression | 待确认 |
| [#125431](https://github.com/openclaw/openclaw/issues/125431) | Codex 受限工具策略静默禁用 workspace AGENTS.md | Behavior | 待确认 |
| [#123273](https://github.com/openclaw/openclaw/issues/123273) | 命名 Agent 图片附件上传失败 | Behavior | 待确认 |
| [#112259](https://github.com/openclaw/openclaw/issues/112259) | 入站频道 turn 零 payload 静默丢弃（无重试/死信） | Behavior | 待确认 |
| [#86612](https://github.com/openclaw/openclaw/issues/86612) | Docker 沙箱模式下 Gateway 容器重启循环 | Behavior | 待确认 |
| [#114234](https://github.com/openclaw/openclaw/issues/114234) | Usage-cost 刷新锁在容器重启后永远不可释放 | Behavior | 待确认 |
| [#124284](https://github.com/openclaw/openclaw/issues/124284) | v2026.8.1-beta.2 子 Agent vLLM thinking 模式 XML 工具调用损坏 | Regression | 待确认 |
| [#92241](https://github.com/openclaw/openclaw/issues/92241) | 更新/回滚后 Gateway 持有过期模块路径，消息静默丢失 | Regression | 待确认 |
| [#126246](https://github.com/openclaw/openclaw/issues/126246) | Telegram 持久化外发消息重启后丢失 | Behavior | 待确认 |
| [#119475](https://github.com/openclaw/openclaw/issues/119475) | WhatsApp LID 地址 DM 静默丢弃（24h 内丢失 79 个独立发送者） | Behavior | 待确认 |

### P2 严重级别（节选）

| Issue | 标题 | 类型 |
|---|---|---|
| [#53628](https://github.com/openclaw/openclaw/issues/53628) | XDG_CONFIG_HOME 在 Docker 中安装 Skill 时未处理 | Behavior |
| [#113306](https://github.com/openclaw/openclaw/issues/113306) | SQLite 快照恢复缺乏端到端崩溃和身份保证 | Behavior |
| [#88657](https://github.com/openclaw/openclaw/issues/88657) | DeepSeek V4 Flash 不完整 turn（payloads=0） | Regression |
| [#43747](https://github.com/openclaw/openclaw/issues/43747) | 内存管理混乱（多 Agent 状态不一致） | Regression |
| [#119796](https://github.com/openclaw/openclaw/issues/119796) | Windows vitest teardown EBUSY unlink agent DB | Behavior |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) | active-memory 阻塞回复 + QMD 启动过载多 Agent 网关 | Reliability |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/Tool 子进程泄漏导致僵尸积累 | Regression |
| [#58957](https://github.com/openclaw/openclaw/issues/58957) | 长会话上下文过大使模型切换静默失败 | Behavior |
| [#124393](https://github.com/openclaw/openclaw/issues/124393) | sessions 同步转录重写并发删除 transcript 行 | Behavior |

**稳定性总结：** 今日 Issue 中回归类 Bug 占比较高（约 30%），涉及 Gateway 启动、模型集成、状态持久化等核心路径。多个 P0/P1 Bug 尚无明确 Fix PR，beta.2 验证期间需重点关注。

---

## 6. 功能请求与路线图信号

| Issue | 标题 | 评论数 | 优先级 | 路线图信号 |
|---|---|---|---|---|
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | Per-agent 成本预算网关级强制 | 23 | P2 | 运营方刚需，可能与 LiteLLM 路由功能协同 |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | 集中式文件名编码工具 | 20 | P3 | 架构级修复，影响所有频道适配器 |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | 在 session_status 暴露解析后的后端模型 | 8 | P2 | 与 #42475 配套，路由透明化需求 |
| [#47910](https://github.com/openclaw/openclaw/issues/47910) | 按失败类别的 Provider 故障隔离 | 8 | P2 | 提升多 Provider 容错能力 |
| [#71142](https://github.com/openclaw/openclaw/issues/71142) | Control UI 可配置上传大小限制 | 8 | P2 | UX 摩擦点，5MB 硬编码已受诟病 |
| [#45501](https://github.com/openclaw/openclaw/issues/45501) | `session.resetPrompt` 可配置会话启动消息 | 6 | P3 | 自定义化需求，已有多人支持 |
| [#42276](https://github.com/openclaw/openclaw/issues/42276) | 推理流（Reasoning Stream）可覆盖写入 | 6 | P3 | 对标 OpenAI/Grok 体验 |
| [#50798](https://github.com/openclaw/openclaw/issues/50798) | ACP 线程绑定会话 Agent-to-Agent 可见消息 | 5 | P2 | 多 Agent 协作场景需求 |
| [#55235](https://github.com/openclaw/openclaw/issues/55235) | Bootstrap/Update 时自动生成 openclaw.json JSON Schema | 5 | P3 | 开发者体验改善 |
| [#45564](https://github.com/openclaw/openclaw/issues/45564) | `/new` 和 `/reset` 添加确认步骤 | 6 | P2 | 防误操作 UX 改进 |

**路线图判断：** 成本预算（#42475）、Provider 故障隔离（#47910）、后端模型暴露（#51441）形成一组强关联需求，反映运营侧对可观测性和成本控制的诉求。文件名编码（#48788）是架构级技术债，社区讨论成熟后可纳入中期计划。

---

## 7. 用户反馈摘要

### 痛点 TOP 5

1. **Session 状态管理不稳定** — 多条 Issue 指向 transcript 并发写入丢失（[#124393](https://github.com/openclaw/openclaw/issues/124393)、[#114234](https://github.com/openclaw/openclaw/issues/114234)、[#126246](https://github.com/openclaw/openclaw/issues/126246)），用户反映重启后消息丢失、锁状态无法恢复。

2. **多 Provider 集成可靠性不足** — DeepSeek V4 Flash（[#88657](https://github.com/openclaw/openclaw/issues/88657)）、Google Vertex（[#38327](https://github.com/openclaw/openclaw/issues/38327)）、Anthropic OAuth（[#83598](https://github.com/openclaw/openclaw/issues/83598)）均有回归问题，用户抱怨"之前能用的现在不行"。

3. **WhatsApp/Telegram 消息静默丢失** — WhatsApp LID 地址 DM（[#119475](https://github.com/openclaw/openclaw/issues/119475)）和 Telegram 外发持久化（[#126246](https://github.com/openclaw/openclaw/issues/126246)）均报告消息无声丢失，影响生产环境信任度。

4. **Windows 平台兼容性** — CLI 进程残留（[#74378](https://github.com/openclaw/openclaw/issues/74378)）、vitest EBUSY（[#119796](https://github.com/openclaw/openclaw/issues/1197

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-08-21 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026年8月下旬，个人 AI 助手与自主智能体开源生态呈现**"高活跃分化、安全与稳定性并重"**的态势。OpenClaw、Hermes Agent、IronClaw、ZeroClaw 和 CoPaw 保持高频迭代，其中 OpenClaw 与 ZeroClaw 日活最高（各500/50级活动量），但 Bug 密度也显著偏高。生态整体已从"功能扩展期"进入**"生产化加固期"**——多项目聚焦会话状态管理、Provider 容错、沙箱安全、可观测性等工程化命题，社区需求从"能用"转向"可靠可用"。

---

## 2. 各项目活跃度对比

| 项目 | Issues (今日) | PRs (今日) | Release | 健康度 | 核心特征 |
|------|:---:|:---:|:---:|:---:|------|
| **OpenClaw** | ~500 | ~500 | 无（beta.2 验证中） | 🟡 活跃但 Bug 密集 | 多渠道网关，稳定性修复为主 |
| **Hermes Agent** | 50 | 50 | 无 | 🟡 高强度调试期 | Windows/Linux 安装链痛点，Kanban 工作流 |
| **ZeroClaw** | 50 | 50 | 无 | 🟢 活跃，安全导向 | 安全硬化 + 架构 RFC 双轨 |
| **IronClaw** | 21 | 35 | 无 | 🟢 良好 | WebUI 设计系统，Hook 生命周期扩展 |
| **CoPaw** | 14 | 50 | v2.1.1-beta.1 | 🟢 活跃健康 | 长会话稳定性，已步入生产应用阶段 |
| **NanoBot** | 5 | 29 | 无 | 🟢 良好 | MCP SDK v2 迁移，Provider 生态扩展 |
| **LobsterAI** | 2 | 7 | 无 | 🟢 良好（合并率86%） | 体验打磨，响应迅速 |
| **PicoClaw** | 3 | 9 | 无 | 🟡 中等活跃 | 多智能体框架合入，前端性能待改善 |
| **Moltis** | 0 | 6 | 20260820.01 | 🟢 稳定 | 渠道体验+安全治理，低 Issue 流入 |
| **NanoClaw** | 3 | 50 | 无 | 🟢 高频迭代 | 集成稳定性与路由修正 |
| **NullClaw** | 0 | 0 | 无 | ⚪ 停滞 | — |
| **ZeptoClaw** | 0 | 0 | 无 | ⚪ 停滞 | — |

---

## 3. OpenClaw 在生态中的定位

**优势：**
- **渠道覆盖最广**：支持 Nostr、Telegram、WhatsApp、Claude CLI、Tailscale 等 20+ 频道/应用，是生态中唯一的"全渠道网关"定位
- **社区规模领先**：日活 500/500 量级，Issue/PR 绝对数量显著高于其他项目，社区贡献密度最高
- **运营侧功能前瞻**：Per-agent 成本预算（#42475）、Provider 故障隔离（#47910）等需求反映其面向多 Agent 运营场景

**技术路线差异：**
| 维度 | OpenClaw | 竞品对比 |
|------|----------|----------|
| 架构 | 网关+频道适配器模式 | Hermes 偏桌面/本地优先；IronClaw 偏 Rust 原生 sandbox |
| 核心场景 | 多渠道路由 + 运营控制面 | NanoBot：MCP 工具链；CoPaw：长会话对话 |
| 发布节奏 | Beta 验证期，稳定优先 | Moltis 已转向持续交付；LobsterAI 小步快跑 |

**社区规模**：OpenClaw Issue 数约为 Hermes 的 10 倍、IronClaw 的 24 倍，生态中处于绝对头部。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **会话状态/持久化稳定性** | OpenClaw、Hermes Agent、CoPaw、ZeroClaw | OpenClaw：transcript 并发丢失、锁状态恢复；CoPaw：history.db 膨胀至 7.6GB；Hermes：state.db 损坏 |
| **Provider 集成可靠性** | OpenClaw、NanoBot、CoPaw | DeepSeek/Google Vertex/Anthropic OAuth 回归；流式 mid-stream 错误不重试（NanoBot #5454） |
| **多 Agent/工具链协作** | OpenClaw、PicoClaw、ZeroClaw | PicoClaw 合入多智能体框架；ZeroClaw RFC "swarm"临时集群；OpenClaw A2A 可见消息 |
| **安全策略精细化** | ZeroClaw、IronClaw、Hermes Agent | ZeroClaw Shell 分层确认（#7155）；IronClaw user-sandbox 持久化；Hermes 记忆插件指令污染修复 |
| **可观测性与成本可控** | OpenClaw、CoPaw、IronClaw | OpenClaw 成本预算网关强制；CoPaw embedding 超时降级；IronClaw 桌面资源控制面 |
| **渠道体验打磨** | Moltis、LobsterAI、OpenClaw | Moltis WhatsApp 推送名称修复；LobsterAI 文件预览+取消启动；OpenClaw Nostr SecretRef 配置丢失 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键词 |
|------|----------|----------|----------------|
| **OpenClaw** | 全渠道路由 + 运营控制面 | 多 Agent 运营方、网关部署者 | 频道适配器、网关、成本预算 |
| **Hermes Agent** | 桌面优先 + Kanban 工作流 | 个人开发者、本地部署用户 | Rust、state.db、桌面集成 |
| **IronClaw** | Sandbox 安全 + WebUI 设计系统 | 企业级部署、安全敏感场景 | Rust、iron-proxy、Hook 生命周期 |
| **ZeroClaw** | 安全硬化 + WASM 插件 | 安全研究者、架构演进探索者 | WASM、RFC 驱动、SSRF 防护 |
| **CoPaw** | 长会话对话 + 控制台体验 | 深度对话用户、研究场景 | Scroll 机制、向量召回、数据库优化 |
| **NanoBot** | MCP 工具链 + Provider 扩展 | 工具调用场景、MCP 生态用户 | MCP SDK v2、SenseNova、OAuth |
| **LobsterAI** | 文件交互 + 桌面体验 | 日常办公用户、国内用户 | Write 工具预览、启动逃逸 |
| **PicoClaw** | 多智能体框架 + Skill 生态 | 嵌入式/边缘场景、多 Agent 实验 | Blackboard、skill 管理、Anthropic 协议 |
| **Moltis** | 渠道稳定性 + 安全治理 | WhatsApp 用户、自托管运营者 | 持续交付、Snyk 扫描、策略配置 |

---

## 6. 社区热度与成熟度

```
快速迭代阶段（高频功能交付）          质量巩固阶段（稳定性/安全优先）
┌──────────────────────┐            ┌──────────────────────┐
│ ZeroClaw  ██████████ │            │ OpenClaw █████████   │
│ NanoClaw ██████████  │            │ Hermes   ████████    │
│ IronClaw ████████    │            │ CoPaw    ███████     │
│ NanoBot  ████████    │            │ Moltis   █████       │
│ LobsterAI ██████     │            │ PicoClaw ████        │
└──────────────────────┘            └──────────────────────┘
       功能导向                          稳定/安全导向
```

- **快速迭代层**：ZeroClaw、NanoClaw、IronClaw 以功能 RFC 和安全 PR 驱动，架构演进活跃
- **质量巩固层**：OpenClaw 处于 beta.2 验证期，Bug 密度高但合并效率高；CoPaw 长会话问题集中爆发，进入生产化阵痛期
- **成熟稳定层**：Moltis Issue 流入趋近于零，依赖持续交付版本；LobsterAI 合并率 86%，反馈闭环快
- **停滞项目**：NullClaw、ZeptoClaw 无活动，需警惕生态萎缩

---

## 7. 值得关注的趋势信号

### 信号 1：生产化阵痛集中显现
OpenClaw（Session 状态）、CoPaw（7.6GB 数据库膨胀）、Hermes（state.db 损坏）同时暴露**会话持久化**这一共性工程难题。趋势指向：智能体框架需从"对话演示"转向**生产级状态管理**，WAL 模式、并发控制、快照恢复将成为标配能力。

### 信号 2：安全策略从"可选"走向"核心"
ZeroClaw（Shell 分层确认 #7155）、IronClaw（sandbox 持久化 #7732）、Hermes（记忆插件指令污染修复）共同反映——**安全不再只是附加功能，而是框架基础能力**。"类 Claude Code" 交互式确认模式（ZeroClaw #7155）可能成为行业标准 UX。

### 信号 3：Provider 生态碎片化推动标准化需求
OpenClaw（Per-agent 成本预算）、CoPaw（自动模型路由 #6436）、NanoBot（SenseNova/Vertex AI）表明：**多 Provider 接入已成常态，但路由、成本、故障隔离缺乏统一抽象**。LiteLLM 类路由层与智能体框架的协同将是短期热点。

### 信号 4：多 Agent 协作框架进入实现期
PicoClaw 合入 Blackboard 共享上下文（#423）、ZeroClaw RFC "swarm"（#10025）、OpenClaw A2A 消息可见（#50798）——**多智能体从概念验证走向工程实现**，共享记忆、任务委托、上下文隔离将成为下一轮功能竞赛焦点。

### 信号 5：Windows/跨平台兼容性是隐性技术债
Hermes（Windows 安装链路 4+ Issue）、ZeroClaw（Windows 桌面启动失败）、OpenClaw（Windows vitest EBUSY）——**跨平台支持不足正在成为社区反馈的集中痛点**，建议开发者在框架选型时重点评估目标平台的测试覆盖。

---

**总结**：2026年8月，个人 AI 助手开源生态正处于**从功能竞赛到工程化质量竞赛**的转折期。OpenClaw 作为渠道网关领导者面临 beta 期稳定性阵痛；ZeroClaw 与 IronClaw 在安全架构上领先；CoPaw 代表长会话场景的生产化挑战；Moltis 与 LobsterAI 展现成熟项目的稳健迭代。对开发者而言，**会话持久化、Provider 路由、安全策略框架、跨平台测试覆盖**是短期内最值得投入的四个技术方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报
**日期：2026-08-21** | 数据来源：[HKUDS/nanobot](https://github.com/HKUDS/nanobot)

---

## 1. 今日速览

过去24小时NanoBot保持高活跃开发节奏：新增5条Issues（3条活跃、2条已关闭），29条PR更新（12条已合并/关闭、17条待审）。项目无新版本发布，但多个关键修复与功能增强已进入主干，包括MCP SDK v2迁移评估、SenseNova（商汤日日新）原生Provider支持、Telegram可复用贴纸回复以及WebUI观测性改进。整体项目健康度良好，社区贡献者持续活跃。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要PR（2条）

| PR | 内容 | 影响 |
|---|---|---|
| [#5452](https://github.com/HKUDS/nanobot/pull/5452) | 新增TUI退出时打印`nanobot agent --session websocket:<id>`恢复命令 | 提升TUI用户体验，简化会话恢复流程 |
| [#5240](https://github.com/HKUDS/nanobot/pull/5240) | WebUI浮动控件统一重构 | 统一Dropdown类组件样式语义，改善界面一致性 |

### 关键待合并PR（部分）

- **#5180 / #5179**：MCP SDK v2迁移评估与正式实现并行推进，#5180为最小可行性基线评估，#5179为完整迁移方案，维护者需在两者间做出决策
- **#5453**：新增SenseNova（商汤日日新）Provider，支持`sensenova-6.8-flash-lite`、`deepseek-v4-flash`、`glm-5.2`等模型
- **#5420**：WebUI Turn观测性与安全恢复功能，支持中断任务展示与Provider用量累积统计

---

## 4. 社区热点

### 活跃Issue

- **[#5444](https://github.com/HKUDS/nanobot/issues/5444)** — Docker环境下通过OAuth登录OpenAI失败（`localhost:1455`回调URL问题）
- **[#5459](https://github.com/HKUDS/nanobot/issues/5459)** — 功能请求：为Claude模型添加Google Vertex AI原生Provider支持
- **[#5454](https://github.com/HKUDS/nanobot/issues/5454)** — Bug：流式Provider在内容已部分输出后遇到`server_error`时跳过重试

### 活跃PR

- **[#5179](https://github.com/HKUDS/nanobot/pull/5179)** — MCP SDK v2完整迁移，涉及传输层改造与SSRF防护保留，评论数较多，讨论焦点在迁移范围与兼容性平衡
- **[#5420](https://github.com/HKUDS/nanobot/pull/5420)** — WebUI Turn观测性，社区对中断恢复与用量统计需求强烈

---

## 5. Bug 与稳定性

| Issue | 描述 | 严重程度 | 状态 | 关联Fix PR |
|---|---|---|---|---|
| [#5444](https://github.com/HKUDS/nanobot/issues/5444) | Docker下OAuth登录回调URL异常 | 中 | OPEN | 无 |
| [#5454](https://github.com/HKUDS/nanobot/issues/5454) | 流式Provider mid-stream `server_error`不重试 | 高 | OPEN | [#5455](https://github.com/HKUDS/nanobot/pull/5455) 已提交（待合并） |
| [#5425](https://github.com/HKUDS/nanobot/issues/5425) | `socks://`代理URL未被识别 | 中 | CLOSED | 已修复 |

**说明**：#5455 是#5454的针对性修复，将`"server_error"`加入瞬态错误标记列表，但仅覆盖首delta前的场景；内容已流式输出后的重试问题尚未解决，需后续跟进。

---

## 6. 功能请求与路线图信号

- **[#5459](https://github.com/HKUDS/nanobot/issues/5459)** — Vertex AI原生Provider支持Claude模型：社区对多云/多Provider策略需求明显，当前已有Anthropic直连、OpenAI兼容层等，但缺少Google云原生路径。若NanoBot战略覆盖主流云平台，此功能具备纳入路线图价值。
- **[#5453](https://github.com/HKUDS/nanobot/pull/5453)** — SenseNova（商汤日日新）Provider：中国本土化模型接入需求，已作为PR提交，若通过评审将丰富Provider生态。
- **#5420** — WebUI Turn观测性与安全恢复：反映用户对对话可追溯性与中断安全的强烈诉求，预计将在后续版本中优先合并。

---

## 7. 用户反馈摘要

| 用户诉求 | 来源 | 反馈摘要 |
|---|---|---|
| OAuth在Docker容器中失效 | [#5444](https://github.com/HKUDS/nanobot/issues/5444) | 本地回环地址在容器网络中无法被用户浏览器正常访问，需适配容器部署场景的回调URL策略 |
| 需要Vertex AI托管Claude | [#5459](https://github.com/HKUDS/nanobot/issues/5459) | 企业用户倾向于通过云平台（Vertex AI）而非直接API调用Claude，降低合规与运维负担 |
| 流式响应中断后丢失已输出内容 | [#5454](https://github.com/HKUDS/nanobot/issues/5454) | `server_error`在部分输出后触发时不重试，导致用户体验中断且内容不完整 |
| TUI退出后难以恢复会话 | [#5452](https://github.com/HKUDS/nanobot/pull/5452) | 用户在退出TUI后需手动查找session ID重连，体验不佳（已修复） |
| MCP OAuth凭证丢失风险 | [#5338](https://github.com/HKUDS/nanobot/pull/5338) | OAuth存储读取失败时会将凭证覆盖为空，存在凭证丢失的安全隐患 |

---

## 8. 待处理积压

| 条目 | 类型 | 创建时间 | 说明 |
|---|---|---|---|
| [#5444](https://github.com/HKUDS/nanobot/issues/5444) | Bug | 2026-08-19 | Docker OAuth回调URL问题，尚无修复PR |
| [#5454](https://github.com/HKUDS/nanobot/issues/5454) | Bug | 2026-08-20 | 流式Provider mid-stream错误重试，#5455仅覆盖部分场景 |
| [#5179](https://github.com/HKUDS/nanobot/pull/5179) | 功能 | 2026-07-30 | MCP SDK v2迁移，与#5180形成 competing proposals，维护者决策等待中 |
| [#5453](https://github.com/HKUDS/nanobot/pull/5453) | 功能 | 2026-08-20 | SenseNova Provider，待评审合并 |
| [#5459](https://github.com/HKUDS/nanobot/issues/5459) | 功能请求 | 2026-08-20 | Vertex AI Claude Provider，社区呼声较高 |

---

*报告生成时间：2026-08-21 | 分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-21

## 1. 今日速览

Hermes Agent 今日保持高活跃度：50 条 Issue 更新（44 新开/活跃、6 已关闭）与 50 条 PR 更新（47 待合并、3 已合并）。项目暂无新版本发布，但技术债修复推进较快，主要集中在 Windows 桌面安装/更新链路、多进程日志竞态、state.db 并发稳定性等核心问题。整体项目处于**高强度调试期**，社区参与度旺盛，但 Bug 报告密度偏高，稳定性承压明显。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

今日关闭/合并的 PR 主要推进以下方向：

| PR | 内容 | 意义 |
|---|---|---|
| [#81432](https://github.com/NousResearch/hermes-agent/issues/81432) | `fix(goals)`: 不再将"等待用户输入"标记为 DONE，改为 WAIT 自动恢复 | 修复非人工值守场景下 goal 循环意外终止的 bug |
| [#91205](https://github.com/NousResearch/hermes-agent/pull/91205) | `fix(kanban)`: 保留 worktree 仓库绑定 | 修复自动拆解任务丢失仓库上下文后陷入 `spawn_failed` 循环的问题 |
| [#91206](https://github.com/NousResearch/hermes-agent/pull/91206) | `fix(kanban)`: 临时供应商失败后重新入队 worker | 区分瞬态 provider 错误与 worker 协议违规，避免误判终止 |
| [#91187](https://github.com/NousResearch/hermes-agent/pull/91187) | `fix(plugins/memory/honcho)`: 清理 peer-card 中的指令形/self-narration 行 | 修复 Honcho 记忆插件自由文本污染系统提示的安全问题 |
| [#87978](https://github.com/NousResearch/hermes-agent/pull/87978) | `fix(desktop)`: 用实时 usage 度量替换预计算估计值 | 修复桌面上下文使用量仪表盘在流式响应期间数值卡死的问题 |
| [#80551](https://github.com/NousResearch/hermes-agent/pull/80551) | `docs`: 将 All Gods Must Die  doctrine 正式纳入版本控制 | 建立可复用生产 skill 的文档化基线 |
| [#91194](https://github.com/NousResearch/hermes-agent/pull/91194) | `docs(design)`: 固化 structured run provenance contract v1.0.0 + v1.1.0 | 为运行溯源提供可校验版本化规范 |

项目整体在**可靠性修复**方向获得实质推进，尤其是 kanban 工作流和记忆插件安全两条链路。

---

## 4. 社区热点

| 议题 | 评论数 | 热度说明 |
|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) Skills index 过期/降级 | 66 | 自动化探针持续报 degraded，社区高度关注 skills hub 可用性 |
| [#87093](https://github.com/NousResearch/hermes-agent/issues/87093) Debian 安装脚本失败 | 15 | 新版安装脚本在 Debian 13.6 上 uv.lock/npm install 双重失败，影响 Linux 新用户上手 |
| [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) ZIP 回退删除桌面应用且不重建 | 13 | 用户报告桌面应用在更新后静默消失，Start Menu 快捷方式指向空路径 |
| [#27649](https://github.com/NousResearch/hermes-agent/issues/27649) 多进程日志写到已旋转的文件 | 8 | ✅ 已修复（见 PR #91210） |
| [#20765](https://github.com/NousResearch/hermes-agent/issues/20765) 浏览器仪表板语音模式 | 7 | 👍 6 | Web 端麦克风捕获功能需求强烈 |
| [#75801](https://github.com/NousResearch/hermes-agent/issues/75801) OpenCode Go 流式响应 finish_reason 缺失 | 7 | 与 Desktop 桌面流式剥离 bug 叠加，影响 streaming 体验 |

**热点分析**：安装/更新链路是 Windows 和 Linux 用户共同的痛点；skills index 的自动化健康监控是长期高频问题；浏览器端语音交互是用户呼声最高的功能需求之一。

---

## 5. Bug 与稳定性

| 严重度 | Issue | 描述 | 状态 |
|---|---|---|---|
| 🔴 P1 | [#89293](https://github.com/NousResearch/hermes-agent/issues/89293) | 高负载单机部署 `state.db` 8 天内 3 次损坏，WAL 模式被静默回退 | 已修复 PR #85079 |
| 🔴 P1 | [#87093](https://github.com/NousResearch/hermes-agent/issues/87093) | Debian 安装脚本 uv.lock + npm install 双重失败 | 未修复 |
| 🔴 P1 | [#34597](https://github.com/NousResearch/hermes-agent/issues/34597) | Windows Gateway 启动后 ~400ms 崩溃（计划停止标记误触发） | ✅ 已关闭 |
| 🟡 P2 | [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) | ZIP 回退删除桌面应用后永不重建 | 未修复 |
| 🟡 P2 | [#90829](https://github.com/NousResearch/hermes-agent/issues/90829) | Windows 每日自动更新因 `node_modules` 损坏+fail-closed gate 失败 | 未修复 |
| 🟡 P2 | [#75801](https://github.com/NousResearch/hermes-agent/issues/75801) | OpenCode Go 流式响应 finish_reason 缺失导致 Desktop 剥离 | 未修复 |
| 🟡 P2 | [#91216](https://github.com/NousResearch/hermes-agent/issues/91216) | 多 profile Gateway `/handoff` 使用错误 state.db 和 session key | ✅ 有 PR #91217 |
| 🟡 P2 | [#90477](https://github.com/NousResearch/hermes-agent/issues/90477) | SSH 远程桌面 profile 切换时后台进程在本地启动 | 未修复 |
| 🟡 P2 | [#90297](https://github.com/NousResearch/hermes-agent/issues/90297) | auto_tts 在桌面播放两遍（gateway + useAutoSpeakReplies 双路径） | 未修复 |
| 🟡 P2 | [#91087](https://github.com/NousResearch/hermes-agent/issues/91087) | Windows ACP session/prompt 无限挂起（agent-browser 未安装时 npx 探测） | 有 PR #91219 |
| 🟢 P3 | [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index 探针持续报 degraded | 未修复 |

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求 | 路线图信号 |
|---|---|---|
| [#20765](https://github.com/NousResearch/hermes-agent/issues/20765) + [#54352](https://github.com/NousResearch/hermes-agent/issues/54352) | 浏览器端 WebRTC 麦克风语音输入（无需服务端 PortAudio） | 👍 6，需求明确，可能被纳入下一版本 |
| [#90051](https://github.com/NousResearch/hermes-agent/issues/90051) | 桌面 + 远程 Gateway 的 client-mic 全双工语音 | 与 #20765 互补，指向远程语音交互场景 |
| [#91149](https://github.com/NousResearch/hermes-agent/issues/91149) | 预览窗格 localhost 流量经 harness 路由到远程 backend | 架构级改进，支持远程开发场景 |
| [#91204](https://github.com/NousResearch/hermes-agent/pull/91204) | 桌面账号资源与 Gateway 指标控制面（CPU/RAM/Disk/配额） | 正在开发中，属于可观测性增强 |
| [#91192](https://github.com/NousResearch/hermes-agent/pull/91192) | A2A 可信操作者授权：跨 Agent 委托本地/私有资源任务 | 安全边界设计，pending decision |
| [#91213](https://github.com/NousResearch/hermes-agent/pull/91213) | 桌面 Bot Mode 分离 DM 与群组视图 | 用户体验优化，正在开发 |

**判断**：语音交互增强和可观测性控制面是明确的下个版本候选；A2A 安全授权和 Kanban 运行溯源契约属于架构级演进。

---

## 7. 用户反馈摘要

**核心痛点**：
- **Windows 安装/更新极不稳定**：多条 Issue 报告 ZIP 回退删除应用、`node_modules` 损坏、npx 挂起、PowerShell 受限语言模式安装失败（[#83846](https://github.com/NousResearch/hermes-agent/issues/83846)、[#90829](https://github.com/NousResearch/hermes-agent/issues/90829)、[#89857](https://github.com/NousResearch/hermes-agent/issues/89857)、[#91087](https://github.com/NousResearch/hermes-agent/issues/91087)）。
- **Linux 新用户入门门槛高**：Debian 安装脚本失败（[#87093](https://github.com/NousResearch/hermes-agent/issues/87093)）。
- **多进程/并发场景下 state.db 和日志存在竞态**（[#89293](https://github.com/NousResearch/hermes-agent/issues/89293)、[#27649](https://github.com/NousResearch/hermes-agent/issues/27649)）。
- **语音体验在远程场景完全不可用**：服务端无麦克风，浏览器端又无法获取音频设备（[#20765](https://github.com/NousResearch/hermes-agent/issues/20765)、[#54352](https://github.com/NousResearch/hermes-agent/issues/54352)）。
- **TTS 双路径导致语音重复播放**（[#90297](https://github.com/NousResearch/hermes-agent/issues/90297)）。

**用户满意点**：
- Kanban 工作流的自动任务拆解和 requeue 机制改善明显（[#91205](https://github.com/NousResearch/hermes-agent/pull/91205)、[#91206](https://github.com/NousResearch/hermes-agent/pull/91206)）。
- 实时上下文使用量仪表盘的修复提升了可观测性体验（[#87978](https://github.com/NousResearch/hermes-agent/pull/87978)）。
- 结构化运行溯源契约的文档化让高级用户可追溯任务来源（[#91194](https://github.com/NousResearch/hermes-agent/pull/91194)）。

---

## 8. 待处理积压

| Issue | 标签 | 建议关注 |
|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | `tool/skills` · P3 · 66 条评论 | 长期 open，skills index 健康度是生产用户核心依赖，建议排期修复 cron 触发或索引构建逻辑 |
| [#88683](https://github.com/NousResearch/hermes-agent/issues/88683) | `architecture` · `needs-decision` | 安装/更新/bootstrap 多条路径缺乏单一事实源，导致 operational drift；建议架构评审 |
| [#90866](https://github.com/NousResearch/hermes-agent/issues/90866) | `architecture` · `needs-decision` | 可观测状态 proof-carrying 提案，涉及多模块重构，需决策是否纳入当前迭代 |
| [#91178](https://github.com/NousResearch/hermes-agent/issues/91178) | `comp/cron` · P3 | `kanban create --initial-status blocked` 任务被错误提升（已关闭但标注 duplicate）|
| [#89857](https://github.com/NousResearch/hermes-agent/issues/89857) | `platform/windows` · P2 | PowerShell Constrained Language Mode 下安装脚本崩溃，企业用户常见场景 |

---

**项目健康度评估**：活跃度 A-，稳定性 B，开发者响应速度 A。核心风险集中在 Windows 桌面更新链路和 state.db 并发安全，建议下一迭代优先处理 [#90829](https://github.com/NousResearch/hermes-agent/issues/90829) 和 [#83846](https://github.com/NousResearch/hermes-agent/issues/83846)。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 | 2026-08-21

---

## 一、今日速览

过去24小时 PicoClaw 社区活跃度处于**中等水平**：Issue 更新 3 条（均为新开/活跃，无关闭），PR 更新 9 条（4 条已合并/关闭，5 条待合并），无新版本发布。今日主要进展集中在 **Skill 工具链重构** 与 **Web 依赖修复**，多智能体协作框架基础已合入。社区持续反馈 Web UI 性能与 ASR 引擎灵活性问题，维护者关注度较低（多 Issue 已 stale）。整体项目健康度：后端功能迭代稳定，前端性能优化与社区响应有待加强。

---

## 二、版本发布

无新版本发布。

---

## 三、项目进展

### 今日已关闭 PR（4 条）

| PR | 类型 | 作者 | 进展概述 |
|----|------|------|----------|
| [#714](https://github.com/sipeed/picoclaw/pull/714) | 增强 | seanly | Skills 安装/重装 CLI 重构，支持 `repo@branch` 及子路径选择，新增 `skills reinstall` 子命令，底层改用 GitHub Trees API 拉取完整目录。 |
| [#1158](https://github.com/sipeed/picoclaw/pull/1158) | 功能 | hyperwd | 新增 `anthropic-messages` 协议前缀，支持 Anthropic 原生 `/v1/messages` 端点，修复 [#269](https://github.com/sipeed/picoclaw/issues/269)，使仅支持 Anthropic 原生格式的代理服务可用。 |
| [#423](https://github.com/sipeed/picoclaw/pull/423) | 功能（WIP→基线） | Leeaandrob | 多智能体协作框架基础合入：引入线程安全 Blackboard（共享上下文池）、Agent 移交与发现工具，建立在 #213 与 #131 之上。 |
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) | 修复 | nuestraai | 修复 `web/frontend/pnpm-lock.yaml` 中 `semver@7.8.5` 重复键导致的锁文件解析错误，保障前端构建恢复正常。 |

**整体推进评估**：今日合并内容覆盖技能管理、协议扩展、多智能体基础与前端构建修复，项目在多智能体协作与生态兼容性方向稳步前进，但无新版本伴随，功能尚未发布至生产环境。

---

## 四、社区热点

### Issue 分析

| Issue | 类型 | 作者 | 评论 | 👍 | 摘要 |
|-------|------|------|------|-----|------|
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) | BUG | xpader | 6 | 1 | Web UI 聊天输入在会话历史较长时严重卡顿 |
| [#3330](https://github.com/sipeed/picoclaw/issues/3330) | 功能 | v2up-32mb | 1 | 0 | 要求 `delegate`/`spawn`/`subagent` 工具支持调用时动态覆盖模型 |
| [#3331](https://github.com/sipeed/picoclaw/issues/3331) | 功能 | stanislavvv | 1 | 0 | 请求通过 flag 支持任意模型调用 `/audio/transcriptions`，而非仅 `*-whisper-*` 模型 |

**热点解读**：

- **#3281**（最高关注度）：用户报告在 Web UI 中会话历史积累到一定长度后输入框明显卡顿，影响使用体验。该 Issue 已 stale 但仍有 6 条评论，表明社区对此问题持续关切。
- **#3330**：多智能体工具链的灵活性诉求。当前 `delegate`/`spawn`/`subagent` 模型配置静态绑定，用户希望运行时动态指定模型以适配不同任务复杂度。
- **#3331**：ASR 引擎扩展诉求。当前仅支持 Whisper 模型进行音频转录，用户希望接入更现代的语音模型，提升识别效率与质量。

---

## 五、Bug 与稳定性

| 问题 | 来源 | 严重程度 | 状态 | Fix PR |
|------|------|----------|------|--------|
| Web UI 长历史会话输入卡顿 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | 中（影响 UX） | 未修复，stale | 无 |
| `pnpm-lock.yaml` 重复键导致构建失败 | [#3318](https://github.com/sipeed/picoclaw/pull/3318) | 高（阻塞构建） | **已修复** | [#3318](https://github.com/sipeed/picoclaw/pull/3318) ✅ |

**稳定性评估**：后端依赖更新（5 条 Dependabot PR）属于常规维护，无已知回归。Web UI 性能问题为当前主要稳定性风险，尚未有修复 PR 跟进。

---

## 六、功能请求与路线图信号

| 需求 | Issue | 信号强度 | 分析 |
|------|-------|----------|------|
| 动态模型覆盖（delegate/spawn/subagent） | [#3330](https://github.com/sipeed/picoclaw/issues/3330) | 中高 | 与已合入的多智能体框架（#423）高度相关，若纳入下一版本可显著提升工具链灵活性。 |
| 任意模型接入 ASR 端点 | [#3331](https://github.com/sipeed/picoclaw/issues/3331) | 中 | 请求通过配置 flag 扩展 ASR 引擎支持，实现与 [#1158](https://github.com/sipeed/picoclaw/pull/1158) 类似的协议扩展模式，可参考。 |
| Anthropic 原生协议支持 | PR [#1158](https://github.com/sipeed/picoclaw/pull/1158) | ✅ 已落地 | 已合入，解决 [#269](https://github.com/sipeed/picoclaw/issues/269)，扩展了 Anthropic 兼容服务的接入能力。 |

**路线图判断**：多智能体协作框架已奠定基线，后续版本预计将围绕 Blackboard 上下文共享、动态模型路由、Skill 生态完善展开。ASR 引擎扩展需求与现有协议扩展模式一致，具备实现可行性。

---

## 七、用户反馈摘要

| 来源 | 用户痛点/场景 | 情绪 |
|------|--------------|------|
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI 在长会话历史下输入卡顿，影响日常对话使用 | 不满（6 条评论持续关注） |
| [#3330](https://github.com/sipeed/picoclaw/issues/3330) | 多智能体工具模型配置过于僵化，无法按任务动态切换 | 期待功能扩展 |
| [#3331](https://github.com/sipeed/picoclaw/issues/3331) | 现有 Whisper 模型老旧缓慢，希望接入更高效的语音识别方案 | 期待功能扩展 |
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) | 锁文件错误导致前端构建阻塞 | 问题已解决，反馈积极 |

---

## 八、待处理积压

| 类型 | 编号 | 标题 | 创建时间 | 状态 | 备注 |
|------|------|------|----------|------|------|
| Issue | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI 输入卡顿 | 2026-07-21 | stale，6 评论 | 最高关注 Bug，建议优先处理 |
| Issue | [#3330](https://github.com/sipeed/picoclaw/issues/3330) | 动态模型覆盖 | 2026-08-13 | stale，1 评论 | 与多智能体路线相关 |
| Issue | [#3331](https://github.com/sipeed/picoclaw/issues/3331) | ASR 引擎扩展 | 2026-08-13 | stale，1 评论 | 协议扩展模式成熟，可实现 |
| PR | [#3332](https://github.com/sipeed/picoclaw/pull/3332) | bump aws-sdk-go-v2 | 2026-08-13 | open，stale | Dependabot 依赖更新 |
| PR | [#3333](https://github.com/sipeed/picoclaw/pull/3333) | bump mautrix | 2026-08-13 | open，stale | Dependabot 依赖更新 |
| PR | [#3334](https://github.com/sipeed/picoclaw/pull/3334) | bump anthropic-sdk-go | 2026-08-13 | open，stale | Dependabot 依赖更新 |
| PR | [#3335](https://github.com/sipeed/picoclaw/pull/3335) | bump aws-sdk-go-v2/config | 2026-08-13 | open，stale | Dependabot 依赖更新 |
| PR | [#3336](https://github.com/sipeed/picoclaw/pull/3336) | bump aws-bedrockruntime | 2026-08-13 | open，stale | Dependabot 依赖更新 |

**维护者关注建议**：

1. **#3281** 社区反馈最活跃，建议评估 Web UI 渲染性能瓶颈并给出排期或临时缓解方案。
2. 5 条 Dependabot PR 均处于 stale 状态，建议批量审查合并以维持依赖安全。
3. **#3330** 与已合入的多智能体框架（#423）直接相关，可评估纳入下一版本功能范围。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 | 2026-08-21

## 1. 今日速览
过去24小时 NanoClaw 保持高频迭代节奏，共接收 50 条 PR（35 待合并 / 15 已合并或关闭），Issues 更新 3 条，无新版本发布。活跃度评估：**高**。今日工作重心已从功能扩展转向集成稳定性、路由逻辑修正与多实例部署兼容性加固，核心维护者与贡献者协同高效，项目技术债务正在快速清偿。

## 2. 版本发布
过去24小时无 Release 发布。

## 3. 项目进展
今日已合并/关闭的关键 PR 包括：
- [#1311](https://github.com/nanocoai/nanoclaw/issues/1311) (Closed)：新 session 创建特性收尾。
- [#3421](https://github.com/nanocoai/nanoclaw/pulls/3421) (Closed)：One-click Slack 助手文档与引导层发布就绪。
- [#3423](https://github.com/nanocoai/nanoclaw/pulls/3423)：修复 Slack bot 订阅 `app_mention` 时缺失 `app_mentions:read` scope 的配置断层。
- [#3401](https://github.com/nanocoai/nanoclaw/pulls/3401)：对齐 WhatsApp Cloud skill 与主仓库的 payload 兼容性，修复跨分支组合时的注册失败。
- [#3403](https://github

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-08-21

---

## 1. 今日速览

IronClaw 今日保持高活跃度，过去24小时内新增/更新 Issues 21条、PR 35条，净贡献为正（新开17 Issue + 21 待合并 PR）。核心开发聚焦于 **WebUI 设计系统 Phase 1–3**（Storybook 集成、DESIGN.md 治理、主题重构）、**AfterTurn Hook 生命周期扩展**（#7770 第一阶段）、**user-sandbox 代理化**（#7732 第二步）三大方向。CI 因 Rust 1.98 clippy 新 lint 短暂变红，已由 #7777/#7778 修复。**无新版本发布**，项目整体健康度良好，技术债清理（cleanup PRs）与功能交付同步推进。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 作者 | 变更摘要 |
|---|---|---|
| [#7786](https://github.com/nearai/ironclaw/pull/7786) | henrypark133 | **SEV修复**：修正 OpenAI 模型 suggestion 生成失败（`uniqueItems` 误配置） |
| [#7777](https://github.com/nearai/ironclaw/pull/7777) | henrypark133 | **CI修复**：清除 clippy 1.98 lint 级联阻塞，恢复合并队列 |
| [#7778](https://github.com/nearai/ironclaw/pull/7778) | serrrfirat | **Rust 1.98 迁移**：整个 workspace 在 `+1.98.0 clippy --all-features` 下零错误 |
| [#7729](https://github.com/nearai/ironclaw/pull/7729) | serrrfirat | **feat(automations)**：新增 `run-now` 手动触发能力，覆盖模型能力、产品层、WebUI 三端 |
| [#7763](https://github.com/nearai/ironclaw/pull/7763) | henrypark133 | **docs(subagent)**：7份文档、7000+ 行压缩为单一 canonical README，净减 9,713 行 |
| [#7738](https://github.com/nearai/ironclaw/pull/7738) | thisisjoshford | **feat(slack)**：配置卡片每字段增加 help text（来源 #7550） |
| [#7733](https://github.com/nearai/ironclaw/issues/7733) | serrrfirat | **Epic 合并**：DESIGN.md 治理 + 主题重构 Phases 2–3 并入 #7781，原 Epic 关闭 |

**整体判断**：今日合并以"修复型"PR 为主（SEV bug、CI 阻断、lint 迁移），功能型交付集中在 automations `run-now` 和 Slack 配置体验。技术债清理（#7763 文档压缩、#7755 类型折叠）持续进行，项目结构在稳步收敛。

---

## 4. 社区热点

### 讨论最活跃的 Issues

1. **#7732 — Persistent per-user sandbox with iron-proxy** ⭐ Epic v1.4.0
   - 作者：serrrfirat | 评论：8
   - 核心诉求：将 `builtin.shell` 的 Docker 路由从"每次命令启停容器"升级为持久化用户沙箱，按 `(tenant, user)` 维度复用容器，`/workspace` 跨命令持久化。这是当前最高优先级的架构升级。
   - 链接：<https://github.com/nearai/ironclaw/issues/7732>

2. **#7770 — Hook the agent lifecycle (phased)** ⭐ Epic
   - 作者：serrrfirat | 评论：3
   - 核心诉求：将 `ironclaw_hooks` 扩展到 turn 生命周期中尚未覆盖的时机点（after-turn、before-turn、compaction、tool-result），使"当 X 发生时做 Y"功能以 hook 注册形式实现，而非核心引擎修改。Phase 1（AfterTurn）已在 #7765 落地。
   - 链接：<https://github.com/nearai/ironclaw/issues/7770>

3. **#7783 — LLM timeout policy: TTFT measurement gap**
   - 作者：henrypark133 | 评论：1
   - 核心问题：structured-output finalization 在非流式 HTTP 客户端运行，传输 stalls 在 60s wall-clock cap 触发前不可见，导致 75s finalization deadline 在重试完成前即终止。
   - 链接：<https://github.com/nearai/ironclaw/issues/7783>

### 讨论最活跃的 PR

1. **#7765 — AfterTurn lifecycle hook + memory curation**
   - 作者：serrrfirat | 这是 #7770 Phase 1 的落地 PR，首次在 `ironclaw_hooks` 中引入 act-capable 生命周期钩子点，以 memory curation 为首个消费者。
   - 链接：<https://github.com/nearai/ironclaw/pull/7765>

2. **#7779 — Route user-sandbox egress through iron-proxy sidecar**
   - 作者：serrrfirat | #7732 Step 2，沙箱出口流量改走 per-user `ironsh/iron-proxy` sidecar，替代 `--network none` + host broker 方案。
   - 链接：<https://github.com/nearai/ironclaw/pull/7779>

3. **#7711 — Typed tool response, guest migration, dispatch-error cleanup**
   - 作者：henrypark133 | capability-response-normalization stack 的最终 PR（#7627 栈顶），清理了 #7703 中被删除的 0.3.0 兼容 shim。
   - 链接：<https://github.com/nearai/ironclaw/pull/7711>

4. **#7750 — Storybook + design-system catalog integration**
   - 作者：rdisandro | WebUI Design System Phase 1，从 `main` 重新创建以避免堆叠 merge-commit 问题，可直接 squash merge。
   - 链接：<https://github.com/nearai/ironclaw/pull/7750>

5. **#7699 — Publish actionable run gates**
   - 作者：italic-jinxin | 将 approval-required / authentication-required / blocked-run 事件推送到持久化 Inbox，支持重试和 replay 收敛到同一记录。
   - 链接：<https://github.com/nearai/ironclaw/pull/7699>

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 描述 | Fix PR |
|---|---|---|---|
| 🔴 SEV | [#7786](https://github.com/nearai/ironclaw/pull/7786) | OpenAI 模型 suggestion 生成全部失败：`schemas/suggestions.output.json` 中 `sources` 字段的 `uniqueItems: true` 导致 OpenAI strict structured-output 校验不通过 | ✅ 已合并 |
| 🟡 Medium | [#7783](https://github.com/nearai/ironclaw/issues/7783) | LLM finalization 超时时序缺陷：非流式客户端无法感知 TTFT，60s 传输 cap 与 75s finalization deadline 冲突，单次传输 stall 即可摧毁一次 run | 待修复 |
| 🟡 Medium | [#7776](https://github.com/nearai/ironclaw/issues/7776) | `memory.write` 缺乏 expected-version 模式：`append: false` 的 read-modify-write 虽用 CAS 保护了 torn write，但并发写入仍可能被静默覆盖 | 待修复 |
| 🟡 Medium | [#7308](https://github.com/nearai/ironclaw/issues/7308) | Attio MCP OAuth 注册因 scope 不合法持续失败，agent 按 Attio 官方文档注册也无法通过 auth gate | 待修复 |
| 🟢 Low | [#7768](https://github.com/nearai/ironclaw/issues/7768) | Settings / Extensions 存在重复 tab 组件和已漂移的路由元数据 | #7773 已修复（合并） |
| 🟢 Low | [#7767](https://github.com/nearai/ironclaw/issues/7767) | Automation presenter 日期测试在 `Asia/Shanghai` 等时区下断言失败 | 待修复 |

---

## 6. 功能请求与路线图信号

| 功能方向 | 信号来源 | 预期版本 |
|---|---|---|
| **User-sandbox 持久化 + iron-proxy** | #7732（Epic, v1.4.0）+ #7779（Step 2 PR） | v1.4.0 |
| **Agent 生命周期 Hook 扩展** | #7770（Epic）+ #7765（Phase 1 已合并） | v1.4.0 |
| **Automation run-now 手动触发** | #7193（需求）+ #7729（已合并） | 已落地 |
| **WebUI Design System（5阶段）** | #7038（Phase 1, #7750 已合并）→ #7781（Phases 2–3）→ #7782（Phases 4–5） | v1.4.0 |
| **Telegram 分离 bot pairing 与 device linking** | #7766（已合并） | 已落地 |
| **Run gate 可操作通知** | #7699（PR 开放中） | 待定 |
| **Memory.write CAS + expected-version** | #7776（bug report，实为功能缺口） | 待定 |
| **OAuth 配置错误在 Configure 中全面暴露** | #7769（Open） | 待定 |

---

## 7. 用户反馈摘要

- **Sandbox 持久化是最高优先级诉求**：#7732 拥有 8 条评论，是今日 Issue 中讨论最深入的议题。当前"每命令启停容器"的模式不可扩展，用户需要按 `(tenant, user)` 的持久化沙箱环境。
- **Hook 机制扩展获得社区高度认可**：#7770 的设计方向（将核心引擎修改替换为 hook 注册）符合项目长期可维护性目标，Phase 1 已顺利通过 PR review 合并。
- **OpenAI suggestion 生成 SEV 回归被快速修复**：#7786 在创建后 1 天内被合并，说明核心维护者对生产可用性问题的响应速度较快。
- **文档质量改善需求明显**：#7763 将 subagent 的 7 份矛盾文档压缩为单一 README，净减 9,713 行，反映社区对"文档漂移"问题的持续关注。
- **时区敏感测试是跨地域贡献者的隐性痛点**：#7767 暴露了测试套件在 `Asia/Shanghai` 时区下的断言失败，暗示项目测试基础设施对非 UTC 环境覆盖不足。

---

## 8. 待处理积压

| 优先级 | Issue/PR | 状态 | 备注 |
|---|---|---|---|
| 🔴 高 | [#7783](https://github.com/nearai/ironclaw/issues/7783) — LLM timeout TTFT 测量缺陷 | Open，1 评论 | 直接影响 finalization 可靠性，无 pending PR |
| 🔴 高 | [#7776](https://github.com/nearai/ironclaw/issues/7776) — memory.write 缺 expected-version | Open，0 评论 | 并发写入静默覆盖风险，由 #7765 review 发现 |
| 🟡 中 | [#7308](https://github.com/nearai/ironclaw/issues/7308) — Attio MCP OAuth scope 非法 | Open，1 评论，7/16 创建至今 | 阻塞 Attio 用户，无修复进展 |
| 🟡 中 | [#7780](https://github.com/nearai/ironclaw/issues/7780) — AfterTurn hook 调度器失败路径未覆盖 | Open，0 评论 | #7770 Phase 1 的后续，需跟进 |
| 🟡 中 | [#7775](https://github.com/nearai/ironclaw/issues/7775) — Unbound runs 跳过 gate 而非 abort | Open，0 评论 | #7770 Phase 1 遗留决策，需确定 gate posture |
| 🟢 低 | [#7767](https://github.com/nearai/ironclaw/issues/7767) — Automation 日期测试时区鲁棒性 | Open，0 评论 | 影响非 UTC 地区 CI |
| 🟢 低 | [#7785](https://github.com/nearai/ironclaw/issues/7785) — executor test-support 拆分 | Open，0 评论 | 清理型 PR，#7784 姊妹 issue |
| 🟢 低 | [#7784](https://github.com/nearai/ironclaw/issues/7784) — capability-port test forest 提取 | Open，0 评论 | 同上，需独立 PR |

---

**项目健康度评估**：🟢 **良好**。今日 PR 合并速率（14/35 = 40%）和 Issue 处理节奏正常，SEV 修复响应迅速（<24h）。主要风险点在于 #7783（LLM timeout）和 #7776（memory.write 并发）两个无 pending fix 的 medium-severity 问题，建议维护者优先排期。v1.4.0 路线图（sandbox 持久化、Design System、Hook 扩展）推进有序。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI 项目日报 | 2026-08-21

---

## 1. 今日速览

今日 LobsterAI 社区活跃度较高，共处理 **9 条动态**（2 Issues + 7 PRs）。PR 合并率约 **86%**（6/7），显示维护者对社区贡献响应及时。**无新版本发布**，但多个高质量 PR 已合并，聚焦于体验优化（文件预览、设置搜索、Agent 切换修复）与打包稳定性修复，项目整体健康度良好，代码质量与用户交付效率稳步提升。

---

## 2. 版本发布

⏸️ 本周期无新版本发布。

---

## 3. 项目进展

今日合并/关闭了 **6 个 PR**，覆盖用户交互、引擎稳定性、构建流程与设置体验四大方向：

### ✅ 已合并/关闭的 PR

| PR | 类型 | 摘要 |
|----|------|------|
| [#1553](https://github.com/netease-youdao/LobsterAI/issues/1553) | **feat** | Write 工具文件卡片及分屏预览面板（Closes #1552） |
| [#1557](https://github.com/netease-youdao/LobsterAI/issues/1557) | **feat** | 设置面板侧栏支持搜索筛选分类 |
| [#1560](https://github.com/netease-youdao/LobsterAI/issues/1560) | **fix** | 修复 Agent 编辑后点击原 Agent 无法切换回聊天界面的问题 |
| [#1545](https://github.com/netease-youdao/LobsterAI/issues/1545) | **fix** | 修复 Agent 技能徽章不实时更新的问题（Fixes #1502） |
| [#1546](https://github.com/netease-youdao/LobsterAI/issues/1546) | **feat** | 引擎启动超时后显示取消启动和查看日志按钮 |
| [#1555](https://github.com/netease-youdao/LobsterAI/issues/1555) | **fix** | 修复 macOS `npm run dist:mac:x64` 打包失败（sha256sum 兼容） |

**亮点**：
- **#1553** 是最具用户体验价值的合并项，为 Write 工具添加了内联文件卡片与右侧可拖拽预览面板，支持 Markdown、HTML、代码、图片等多种格式，直接闭环了 Issue #1552 的诉求。
- **#1546** 解决了引擎启动卡死时用户"无逃逸出口"的痛点，提供了"取消启动"与"查看日志"两个实用操作。

### 🔄 待合并 PR

| PR | 状态 | 摘要 |
|----|------|------|
| [#1547](https://github.com/netease-youdao/LobsterAI/issues/1547) | **OPEN** | 修复定时任务通知渠道选择后无法改回"不通知"的 bug |

> PR #1547 为纯 bug 修复，改动极小（仅 2 行），建议优先合并。

---

## 4. 社区热点

### 🔥 高关注 Issues

**#1552 — AI 产物 Markdown 预览及文件卡片支持**
- 作者：noransu
- 评论：1 | 👍：0
- 链接：[Issue #1552](https://github.com/netease-youdao/LobsterAI/issues/1552)
- **分析**：此 Issue 描述了写作、文档生成场景下的核心体验痛点，已被 PR #1553 完整实现并关闭。用户反馈路径清晰，贡献闭环。

**#1556 — IM 机器人配置指南 404**
- 作者：darkSheep404
- 评论：2 | 👍：0 | 状态：⚠️ stale
- 链接：[Issue #1556](https://github.com/netease-youdao/LobsterAI/issues/1556)
- **分析**：文档链接失效问题，已标记 stale，建议维护者尽快修复或关闭。

---

## 5. Bug 与稳定性

| 严重度 | 问题 | PR 状态 | 链接 |
|--------|------|---------|------|
| 🟡 中 | 定时任务通知渠道无法改回"不通知" | PR #1547 待合并 | [PR #1547](https://github.com/netease-youdao/LobsterAI/issues/1547) |
| 🟢 低 | macOS 打包失败（sha256sum 不兼容） | ✅ PR #1555 已合并 | [PR #1555](https://github.com/netease-youdao/LobsterAI/issues/1555) |
| 🟢 低 | Agent 编辑后切换回聊天界面失效 | ✅ PR #1560 已合并 | [PR #1560](https://github.com/netease-youdao/LobsterAI/issues/1560) |
| 🟢 低 | 技能徽章不实时更新 | ✅ PR #1545 已合并 | [PR #1545](https://github.com/netease-youdao/LobsterAI/issues/1545) |

> 今日无新增崩溃或回归报告，修复 PR 响应速度较快。

---

## 6. 功能请求与路线图信号

| 需求来源 | 诉求 | 状态 | 判断 |
|----------|------|------|------|
| Issue #1552 | Write 工具文件卡片 + 分屏预览 | ✅ 已实现（PR #1553） | 已纳入当前迭代 |
| Issue #1556 | IM 配置指南 404 修复 | ⚠️ stale | 文档维护优先级较低 |
| PR #1546 | 引擎启动超时逃逸机制 | ✅ 已合并 | 稳定性增强，可能成为后续引擎优化的模板 |

**路线图信号**：项目正在加强**文件交互体验**与**用户操作可逆性**（取消启动、日志查看），同时持续优化设置面板的可发现性。

---

## 7. 用户反馈摘要

| 用户痛点 | 来源 | 反馈摘要 |
|----------|------|----------|
| Write 工具产出的文件无法预览 | #1552 | 用户此前只能让 Agent 全文贴入聊天或手动切换文件管理器，体验割裂；PR #1553 解决了此问题 |
| Agent 设置面板分类过多难以定位 | #1557 | 用户希望快速搜索跳转，PR #1557 增加了侧栏搜索框，支持中英关键词过滤 |
| 引擎启动卡住无退出方式 | #1546 | 用户曾被迫等待 5 分钟硬超时，PR #1546 提供了 30 秒后显示的取消按钮与日志查看入口 |
| 打包环境兼容性问题 | #1555 | macOS 用户反馈 sha256sum 不存在，PR #1555 已修复 |

---

## 8. 待处理积压

| 类型 | 编号 | 问题 | 状态 | 建议 |
|------|------|------|------|------|
| 📋 Issue | [#1556](https://github.com/netease-youdao/LobsterAI/issues/1556) | IM 机器人配置指南 404 | stale | 修复文档链接或关闭 |
| 🔀 PR | [#1547](https://github.com/netease-youdao/LobsterAI/issues/1547) | 定时任务通知渠道无法改回"不通知" | OPEN | 优先合并（2 行改动，纯 bug fix） |

---

> 📊 **项目健康度评分**：⭐⭐⭐⭐☆（4/5）— PR 合并率高、bug 响应快，但部分 Issue/PR 标记 stale 需维护者跟进清理。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-08-21

---

## 1. 今日速览

过去 24 小时 Moltis 项目保持**中低活跃度**，无新 Issue 产生，社区讨论趋于平静。PR 活跃度较高，共 6 条更新，其中 2 条已合并/关闭，4 条仍待处理。项目于昨日（2026-08-20）发布新版本 `20260820.01`，主要聚焦 WhatsApp 渠道体验优化与安全加固。整体项目健康度良好，安全与渠道稳定性是今日核心方向。

---

## 2. 版本发布

### `20260820.01`（2026-08-20）
- 随当日 PR 合并产出，为持续交付版本（continuous delivery）。
- 本次发布包含两个已合并修复：
  - WhatsApp 推送名称不再硬编码为 `"Moltis"`（[#1218](https://github.com/moltis-org/moltis/pull/1218)）
  - `untrusted-turn` 工具天花板策略可配置化（[#1219](https://github.com/moltis-org/moltis/pull/1219)）
- **破坏性变更**：无。
- **迁移注意**：使用 WhatsApp 渠道且自定义过推送名称的用户，建议升级以恢复正确的显示名称；依赖工具策略分层（layer 4/5）的用户可重新启用此前不可达的策略层。

---

## 3. 项目进展

### 今日已合并 / 关闭
| PR | 类型 | 说明 |
|---|---|---|
| [#1218](https://github.com/moltis-org/moltis/pull/1218) | Bug 修复 | 修复 WhatsApp 客户端硬编码推送名称问题，解决未保存联系人视角下 bot 显示异常 |
| [#1219](https://github.com/moltis-org/moltis/pull/1219) | Bug 修复 | 将 `untrusted-turn` 工具天花板从硬编码改为可配置，恢复 `/sh` 渠道外公共受众工具策略的完整性 |

### 推进方向
- **渠道体验**：WhatsApp 渠道连续两日获得修复（[#1218](https://github.com/moltis-org/moltis/pull/1218) 命名问题 + [#1220](https://github.com/moltis-org/moltis/pull/1220) Markdown 渲染待合并），显示层与消息格式问题正在被系统性清理。
- **安全加固**：[#1221](https://github.com/moltis-org/moltis/pull/1221) 将 Snyk Agent Scan 固定至 `0.5.17` 并通过 `uvx` 执行，移除冗余 fallback，供应链安全防线进一步收紧。

---

## 4. 社区热点

| PR/Issue | 状态 | 热度说明 |
|---|---|---|
| [#468](https://github.com/moltis-org/moltis/pull/468) | OPEN（逾 5 个月） | Windows shell hook 兼容性修复，长期未响应，涉及 Windows 用户核心可用性 |
| [#1222](https://github.com/moltis-org/moltis/pull/1222) | OPEN | Sandbox 镜像请求校验，涉及管理员权限边界，安全敏感度高 |
| [#1221](https://github.com/moltis-org/moltis/pull/1221) | OPEN | Snyk 版本锁定，维护者 tsauvajon 连续提交安全相关 PR，关注度高 |

**诉求分析**：
- [#468](https://github.com/moltis-org/moltis/pull/468) 反映出 Windows 平台用户在 shell hook 场景下的长期痛点，建议维护者优先 review。
- [#1222](https://github.com/moltis-org/moltis/pull/1222) 和 [#1221](https://github.com/moltis-org/moltis/pull/1221) 均指向安全治理方向，社区对供应链安全和容器镜像安全的关注持续升温。

---

## 5. Bug 与稳定性

| 问题 | 严重程度 | 修复状态 | 链接 |
|---|---|---|---|
| WhatsApp 推送名称硬编码导致 bot 在群聊中显示错误 | 中（影响用户体验） | ✅ 已修复 [#1218](https://github.com/moltis-org/moltis/pull/1218) | [PR #1218](https://github.com/moltis-org/moltis/pull/1218) |
| `untrusted-turn` 工具策略层 4/5 不可达，公共受众工具被意外移除 | 中高（功能回归） | ✅ 已修复 [#1219](https://github.com/moltis-org/moltis/pull/1219) | [PR #1219](https://github.com/moltis-org/moltis/pull/1219) |
| Windows 下 shell hook 因 `sh -c` 不可用而失败 | 高（平台兼容） | 🔄 待合并 [#468](https://github.com/moltis-org/moltis/pull/468) | [PR #468](https://github.com/moltis-org/moltis/pull/468) |
| Sandbox 镜像请求未做引用和包名校验 | 中高（安全风险） | 🔄 待合并 [#1222](https://github.com/moltis-org/moltis/pull/1222) | [PR #1222](https://github.com/moltis-org/moltis/pull/1222) |

> 注：今日无新 Issue 报告，无新增崩溃或回归。

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 分析 |
|---|---|---|
| WhatsApp 消息 Markdown → 原生 Markup 转换 | [#1220](https://github.com/moltis-org/moltis/pull/1220) | 功能完善型 PR，修复模型输出格式与 WhatsApp 平台渲染不兼容问题，预计纳入近期版本 |
| Sandbox 镜像输入校验 + 管理员权限收紧 | [#1222](https://github.com/moltis-org/moltis/pull/1222) | 安全治理路线清晰，Operator Admin 权限边界进一步明确 |
| Snyk Agent Scan 固定版本 + 移除 fallback | [#1221](https://github.com/moltis-org/moltis/pull/1221) | 安全扫描策略从"可用即可"转向"锁定可追溯"，体现供应链安全优先级提升 |

**预判**：下一版本（`20260821.xx`）可能包含 [#1220](https://github.com/moltis-org/moltis/pull/1220)、[#1221](https://github.com/moltis-org/moltis/pull/1221)、[#1222](https://github.com/moltis-org/moltis/pull/1222)，形成 WhatsApp 渠道体验+安全治理的组合更新。

---

## 7. 用户反馈摘要

今日无新 Issue 产生，用户反馈主要来自已合并 PR 的上下文：

- **WhatsApp 渠道用户**：对推送名称硬编码问题反馈积极（[#1218](https://github.com/moltis-org/moltis/pull/1218)），该问题直接影响 bot 在群聊中的身份识别，修复后体验改善明显。
- **工具策略使用者**：[#1219](https://github.com/moltis-org/moltis/pull/1219) 修复了 `/sh` 渠道策略变更导致的工具层覆盖过宽问题，恢复了公共受众工具的正常可用。
- **Windows 用户**：[#468](https://github.com/moltis-org/moltis/pull/468) 是 Windows 平台用户长期诉求，shell hook 在 Windows 下的可用性直接影响插件生态的完整性。

---

## 8. 待处理积压

| PR/Issue | 开放时长 | 优先级 | 建议 |
|---|---|---|---|
| [#468](https://github.com/moltis-org/moltis/pull/468) | **~151 天**（2026-03-23 至今） | 高 | Windows shell hook 兼容性，影响平台覆盖范围，建议优先 review 合并 |
| [#1222](https://github.com/moltis-org/moltis/pull/1222) | 1 天 | 中 | Sandbox 镜像校验，测试用例已提交（`image_input`），待维护者确认 |
| [#1221](https://github.com/moltis-org/moltis/pull/1221) | 1 天 | 中 | Snyk 版本锁定，`cargo test -p moltis-gateway snyk_agent_scan` 待完成 |
| [#1220](https://github.com/moltis-org/moltis/pull/1220) | 1 天 | 中 | WhatsApp Markdown 渲染，依赖结构性 head/separator 验证逻辑 |

---

**报告生成时间**：2026-08-21  
**数据来源**：[moltis-org/moltis](https://github.com/moltis-org/moltis) GitHub API

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-08-21

## 1. 今日速览

CoPaw 今日保持高活跃度：过去 24 小时内新增/活跃 Issue 14 条、已关闭 14 条；PR 总数 50 条（待合并 22、已合并/关闭 28）。v2.1.1-beta.1 正式发布，聚焦控制台交互优化与日志级别调整。社区关注点集中在长会话数据库膨胀、网络瞬断恢复、流式输出稳定性三大问题上，反映出项目已步入生产场景应用阶段，稳定性与可观测性需求显著上升。

---

## 2. 版本发布

### v2.1.1-beta.1
**链接**: https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.1.1-beta.1

| 变更项 | 说明 |
|--------|------|
| `feat(console)` | 改进编辑器 Tab 溢出导航（[#6983](https://github.com/agentscope-ai/QwenPaw/pull/6983)） |
| `fix(providers)` | 降低 rate limiter 初始化日志级别（[#6988](https://github.com/agentscope-ai/QwenPaw/pull/6988)） |
| `chore` | 更新发布说明 |

- **破坏性变更**：无
- **迁移注意事项**：本次为 beta 版本，建议测试环境先行验证；rate limiter 日志降级不影响行为，仅减少控制台噪音。

---

## 3. 项目进展

### 今日关闭/合并的重要 PR

| PR | 作者 | 进展说明 |
|----|------|----------|
| [#7186](https://github.com/agentscope-ai/QwenPaw/pull/7186) — datapaw PyPI 运行时路径与 docker-compose 演示 | cyruszhang | DataPaw 应用现支持 `pip install qwenpaw[datapaw]` 开箱即用，补齐端到端运行链路 |
| [#6947](https://github.com/agentscope-ai/QwenPaw/pull/6947) — Scroll 重构时丢弃孤立 tool 消息 | yutai78786 | 修复 DeepSeek 等模型上下文重建时 role="tool" 消息断裂问题，提升长会话稳定性 |
| [#7119](https://github.com/agentscope-ai/QwenPaw/pull/7119) — master key 文件以 0o600 权限创建 | Yigtwxx | 修复 secret_store 安全漏洞，符合文档承诺的权限契约 |
| [#6371](https://github.com/agentscope-ai/QwenPaw/pull/6371) — 下载器超时后继续回退 | patrick-andstar | 修复 wget/curl 超时未触发后续 urllib 回退的缺陷 |
| [#7161](https://github.com/agentscope-ai/QwenPaw/pull/7161) — 助手消息卡片增加 artifacts 展示 | zhijianma | 控制台产物可见性增强 |
| [#7174](https://github.com/agentscope-ai/QwenPaw/pull/7174) — 持久化 Driver 并发初始化 | rayrayraykk | 工作区冷启动时间降低 |
| [#6880](https://github.com/agentscope-ai/QwenPaw/pull/6880) — 统一应用/插件/技能市场页 | yuluo1007 | 商城体验整合，路由统一至 `/market` |

**整体判断**：今日 PR 以稳定性修复和功能打磨为主，Scroll 上下文完整性、下载器容错、安全权限修复三项对生产部署有直接价值。

---

## 4. 社区热点

| Issue/PR | 类型 | 评论数 | 核心诉求 |
|----------|------|--------|----------|
| [#7168](https://github.com/agentscope-ai/QwenPaw/issues/7168) | Bug · 已关闭 | 2 | 长运行 agent 的 `history.db` 被 `recall_history` expand 撑至 7.6GB，且同一段落重复落库 |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | Bug · 开放 | 10 | 模型输出规划语句后静默停止，需用户手动说"继续"才能恢复任务 |
| [#7102](https://github.com/agentscope-ai/QwenPaw/issues/7102) | Bug · 已关闭 | 9 | 使用 glm 5.3 时会话冻结超过 10 分钟，无 token 输出 |
| [#6932](https://github.com/agentscope-ai/QwenPaw/issues/6932) | Bug · 开放 | 3 | 网络短暂中断恢复后 QwenPaw 无法自动重连 LLM API，需手动重启进程 |
| [#6436](https://github.com/agentscope-ai/QwenPaw/issues/6436) | 功能 · 开放 | 4 👍 | 按消息类型自动路由到合适模型（小模型/视觉模型/大模型） |

**趋势分析**：
- **#7168** 和 **#6921** 反映多步长任务场景下的稳定性瓶颈，是生产用户的核心痛点。
- **#6932** 网络恢复问题与 **#7162**（流式 ReadError 不重试）互为关联，说明 HTTP 层容错机制亟待统一完善。
- **#6436** 获 👍 支持，体现用户对"按场景选模型"的成本优化诉求强烈。

---

## 5. Bug 与稳定性

| 严重度 | Issue | 描述 | Fix PR |
|--------|-------|------|--------|
| 🔴 高 | [#7168](https://github.com/agentscope-ai/QwenPaw/issues/7168) | `conversation_history` 因 `recall_history` expand 导致数据库膨胀至 7.6GB，且存在重复落库 | 已关闭，待查根因修复状态 |
| 🔴 高 | [#6932](https://github.com/agentscope-ai/QwenPaw/issues/6932) | 网络中断恢复后 LLM 请求持续超时，无自动重连机制 | 无 |
| 🟡 中 | [#7162](https://github.com/agentscope-ai/QwenPaw/issues/7162) | 流式输出中途 `httpx.ReadError` 触发 `UNKNOWN_AGENT_ERROR`，`_get_httpx_retryable()` 未覆盖 ReadError | 无 |
| 🟡 中 | [#7156](https://github.com/agentscope-ai/QwenPaw/issues/7156) | embedding health check 硬编码 5s 超时，预热后仍超时导致向量召回降级为 BM25-only | PR [#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133) 正在推进可配置超时 |
| 🟡 中 | [#7110](https://github.com/agentscope-ai/QwenPaw/issues/7110) | 上下文含无法下载的图片链接时整个会话挂掉，仅 `/clear` 可恢复 | 已关闭 |
| 🟢 低 | [#6826](https://github.com/agentscope-ai/QwenPaw/issues/6826) | 助手消息结束时间显示异常（实际思考 2min 页面显示几秒） | 已关闭 |
| 🟢 低 | [#7060](https://github.com/agentscope-ai/QwenPaw/issues/7060) | `view_video` inline-media 限制硬编码 2MB，provider 配置不生效 | PR [#7061](https://github.com/agentscope-ai/QwenPaw/pull/7061) 待合并 |
| 🟢 低 | [#7118](https://github.com/agentscope-ai/QwenPaw/issues/7118) | 损坏的 `envs.json` 被静默吞掉并覆盖，所有环境变量丢失 | 已关闭 |

---

## 6. 功能请求与路线图信号

| Issue | 需求概述 | 关联 PR | 纳入可能性 |
|-------|----------|---------|------------|
| [#6436](https://github.com/agentscope-ai/QwenPaw/issues/6436) | 自动模型路由（按消息类型选模型） | 暂无直接 PR | ⭐⭐⭐ 高 — 获 👍 支持，架构层面价值明显 |
| [#7013](https://github.com/agentscope-ai/QwenPaw/issues/7013) | Chat 页统一工具面板 + Web 预览 + 交互式 Terminal | 暂无直接 PR | ⭐⭐ 中 — 功能全面但范围较大 |
| [#7184](https://github.com/agentscope-ai/QwenPaw/issues/7184) | Agent 级跨会话 recall 开关（Scroll 模式） | 暂无直接 PR | ⭐⭐ 中 — 与 Scroll 机制强相关 |
| [#7182](https://github.com/agentscope-ai/QwenPaw/issues/7182) | workspace-scoped always-on Skills | PR [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) 已提交 | ⭐⭐⭐ 高 — PR 已存在，近期可合并 |
| [#7181](https://github.com/agentscope-ai/QwenPaw/issues/7181) | 支持 Qwen_Code 作为第三方 agent harness | 暂无 PR | ⭐ 低 — 小众需求 |
| [#7159](https://github.com/agentscope-ai/QwenPaw/issues/7159) | QQ 群定时任务推送 | 暂无 PR | ⭐⭐ 中 — 跟随 QQ 频道能力开放 |
| [#7158](https://github.com/agentscope-ai/QwenPaw/issues/7158) | 钉钉群聊上下文模式可配置（隔离/共享） | 暂无 PR | ⭐⭐ 中 — 企业场景刚需 |
| [#7179](https://github.com/agentscope-ai/QwenPaw/issues/7179) | 优化智能体切换下拉框体验 | 暂无 PR | ⭐ 低 — UI 体验优化 |
| [#7177](https://github.com/agentscope-ai/QwenPaw/issues/7177) | 优化 deploy 首页操作入口布局 | 暂无 PR | ⭐ 低 — UI 优化 |

---

## 7. 用户反馈摘要

| 痛点场景 | 来源 | 典型反馈 |
|----------|------|----------|
| 多步任务中断 | [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | "模型规划好下一步就停了，无提示无视觉反馈，必须说'继续'" |
| 网络瞬断恢复 | [#6932](https://github.com/agentscope-ai/QwenPaw/issues/6932) | "同一天复现两次，网络恢复后必须手动重启才能继续" |
| 数据库膨胀 | [#7168](https://github.com/agentscope-ai/QwenPaw/issues/7168) | "长期运行 agent 的 history.db 膨胀到 7.6GB，同一区间被重复落库" |
| embedding 降级 | [#7156](https://github.com/agentscope-ai/QwenPaw/issues/7156) | "后端已预热仍超时 10.4s，导致本次 session 向量召回降级为 BM25-only" |
| 流式错误 | [#7162](https://github.com/agentscope-ai/QwenPaw/issues/7162) | "API 已接受请求并开始输出 token，但流式传输中途断开即报 UNKNOWN_AGENT_ERROR" |
| 技能加载冲突 | [#7073](https://github.com/agentscope-ai/QwenPaw/issues/7073) | "自定义技能与内置技能同名时两者都会被加载"（已修复） |
| 文件名显示 | [#6453](https://github.com/agentscope-ai/QwenPaw/issues/6453) | "中文文件名被转成不可识别字符，提示极不友好"（已关闭） |
| 技能搜索 | [#7090](https://github.com/agentscope-ai/QwenPaw/issues/7090) | "几百个技能只能上下翻，希望增加搜索/过滤"（已关闭） |
| 视频大小限制 | [#7060](https://github.com/agentscope-ai/QwenPaw/issues/7060) | "2MB 硬编码限制使大视频无法进入模型上下文，provider 配置无效" |

---

## 8. 待处理积压

| Issue/PR | 状态 | 创建时间 | 提醒事项 |
|----------|------|----------|----------|
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | OPEN · 10 评论 | 2026-08-12 | 多步任务静默停止问题影响广泛，建议优先排查模型输出截断与中间态提示机制 |
| [#6932](https://github.com/agentscope-ai/QwenPaw/issues/6932) | OPEN · 3 评论 | 2026-08-12 | 网络恢复自动重连是生产必备能力，与 [#7162](https://github.com/agentscope-ai/QwenPaw/issues/7162) 应统筹修复 |
| [#7156](https://github.com/agentscope-ai/QwenPaw/issues/7156) | OPEN · 2 评论 | 2026-08-20 | embedding 超时硬编码问题，PR [#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133) 正在修复中，可跟进合并进度 |
| [#6436](https://github.com/agentscope-ai/QwenPaw/issues/6436) | OPEN · 4 评论 · 1 👍 | 2026-07-24 | 自动模型路由是架构级功能，建议排入中期路线图 |
| [#7013](https://github.com/agentscope-ai/QwenPaw/issues/7013) | OPEN · 3 评论 | 2026-08-14 | 统一工具面板需求明确，可评估拆分优先级 |
| [#7185](https://github.com/agentscope-ai/QwenPaw/issues/7185) | OPEN · 1 评论 | 2026-08-21 | OAuth 远程 MCP 服务器文档缺失，需补充 |

---

**项目健康度评估**：🟢 活跃健康。Issue/PR 吞吐比接近 1:2，闭环效率高；新版本 beta 节奏稳定。主要风险点在于长会话稳定性（数据库膨胀、网络

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报
**日期：2026-08-21** | 数据周期：过去24小时

---

## 1. 今日速览

ZeroClaw 今日保持高强度活跃，24小时内共产出 **50条 Issue** 与 **50条 PR**，贡献密度稳健。维护者团队聚焦于**安全风险硬化**（shell策略、插件egress、SSRF防护）与**架构RFC推进**（会话所有权、内存生命周期、WASM插件体系），同时清理了部分长期积压的技术债务。无新版本发布，但多个关键安全修复与RFC已进入实现阶段，项目整体处于"稳定强化+架构演进"的双重轨道。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（2条）

| PR | 摘要 |
|---|---|
| [#10194](https://github.com/zeroclaw-labs/zeroclaw/issues/10194) | 修复AI reviewer在PR合并后仍发布审阅结果的竞态问题 |
| [#9016](https://github.com/zeroclaw-labs/zeroclaw/issues/9016) | 修复OpenAI tool在reasoning effort被拒绝时整个turn失败的问题 |

### 关键进行中 PR（按优先级）

- **[PR #9819](https://github.com/zeroclaw-labs/zeroclaw/pull/9819)** — 多模态图片像素级验证：新增 `validate_image_content()` 函数，彻底解码图片而非仅检测header签名，防止损坏图片导致provider请求失败。高风险修复，影响所有多模态provider。

- **[PR #9582](https://github.com/zeroclaw-labs/zeroclaw/pull/9582)** — 插件egress策略Stage 2：为 `wasi:http` 请求引入主机端策略拦截（`PluginEgressHooks`），是ADR-014决策的关键落地。

- **[PR #9678](https://github.com/zeroclaw-labs/zeroclaw/pull/9678)** — 加固Git shell策略参数：在命令策略边界统一规范化shell词，确保可执行文件白名单、风险分类、环境变量检查使用一致的引号/转义表示。

- **[PR #10072](https://github.com/zeroclaw-labs/zeroclaw/pull/10072)** — SSRF硬化Stage 2：在`file_download`工具中引入RFC 6052 NAT64前缀分类，补全私有地址拦截后的网络层防护。

- **[PR #9809](https://github.com/zeroclaw-labs/zeroclaw/pull/9809)** — 单provider多模型支持：新增 `[providers.models.<family>.<alias>.models.<model_alias>]` 子表，一个credential+endpoint可托管多模型，减少配置冗余。

- **[PR #9772](https://github.com/zeroclaw-labs/zeroclaw/pull/9772)** — Telegram per-user会话：新增 `per_user_session` 开关，解决群聊中多人协作时上下文串扰问题。

- **[PR #9713](https://github.com/zeroclaw-labs/zeroclaw/pull/9713)** — 历史裁剪token会计：在history-trim事件中暴露 `tokens_before`/`tokens_after`，解决大段裁剪被误判为正常消耗的问题（[#9619](https://github.com/zeroclaw-labs/zeroclaw/issues/9619)）。

---

## 4. 社区热点

### 高评论Issue（活跃讨论）

| Issue | 评论数 | 主题 | 热度分析 |
|---|---|---|---|
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | 23 | Shell命令分层确认策略 + 类Claude Code政策模式 | ⭐最高 — P1级安全增强，社区对"allow/ask/deny"三级策略期待强烈，maintainer已确认范围 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 22 | 运行时拥有的会话与传输适配器 | ⭐高 — 涉及运行时架构核心边界，Revision 2已确立与#9488/#9600的归属契约 |
| [#10118](https://github.com/zeroclaw-labs/zeroclaw/issues/10118) | 16 | Rust anti-slop策略债务清理 | ⭐高 — 审计发现1,078个Rust文件中307个违规候选，是规模化项目的必要治理动作 |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | 14 | 内存生命周期与存储后端解耦 | 高 — 解决各gateway/channel重复实现合并/治理逻辑的技术债 |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | 14 | Gemini Live实时语音通道 | 高 — v2已重写为broker契约，实时语音是差异化竞争点 |

### 社区诉求分析
- **安全策略精细化**：#7155与#6996（沙箱策略）反映用户对agent执行shell/文件系统操作的**可预测性**和**可控性**有强烈需求，期望类Claude Code的交互式确认模式。
- **架构清晰度**：#9487、#6850、#10076（WASM插件全架构）形成一组信号——社区期望运行时边界更清晰，插件体系从"可选功能"走向"一等公民"。
- **多provider灵活性**：#9809 PR直接响应用户对"一凭据多模型"配置的诉求。

---

## 5. Bug 与稳定性

### 已关闭
| Issue | 严重度 | 摘要 |
|---|---|---|
| [#10194](https://github.com/zeroclaw-labs/zeroclaw/issues/10194) | S2 | PR reviewer在合并后发布结果的竞态bug已修复 |
| [#9016](https://github.com/zeroclaw-labs/zeroclaw/issues/9016) | S1 | OpenAI tool+reasoning effort拒绝导致turn失败的bug已修复 |

### 进行中（待合并）
| Issue | 严重度 | 摘要 | Fix PR |
|---|---|---|---|
| [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | S2 | 交互式agent会话context硬限32k，忽略`max_context_tokens=131072`配置 | 标记in-progress，尚未见fix PR |
| [#10111](https://github.com/zeroclaw-labs/zeroclaw/issues/10111) | — | Windows桌面版`TaskDialogIndirect`入口点未找到 | 重复标记，需关联主问题 |
| [#10106](https://github.com/zeroclaw-labs/zeroclaw/issues/10106) | S2 | 代理选择器错误拒绝支持的转录服务（Groq/Deepgram/AssemblyAI/Google） | #10106，标记in-progress |
| [#10103](https://github.com/zeroclaw-labs/zeroclaw/issues/10103) | S3 | ZeroCode健康状态值在法语/西班牙语中宽度错位 | 标记in-progress |

### 文档问题
| Issue | 严重度 | 摘要 |
|---|---|---|
| [#10074](https://github.com/zeroclaw-labs/zeroclaw/issues/10074) | — | `SECURITY.md`引用了4月已移除的CI job，容器安全检查现为convention而非强制 |

---

## 6. 功能请求与路线图信号

### 高置信度纳入下一版本
| 来源 | 内容 | 判断依据 |
|---|---|---|
| [#9809](https://github.com/zeroclaw-labs/zeroclaw/pull/9809) PR | 单provider多模型配置 | PR已创建并活跃，直接解决配置冗余痛点 |
| [#9772](https://github.com/zeroclaw-labs/zeroclaw/pull/9772) PR | Telegram per-user会话隔离 | 明确的群聊协作痛点，PR已就绪 |
| [#10168](https://github.com/zeroclaw-labs/zeroclaw/issues/10168) Issue | 默认启用stall watchdog | 已被accept，保守非零默认值降低挂起风险 |
| [#10166](https://github.com/zeroclaw-labs/zeroclaw/issues/10166) Issue | 默认`stream_mode=partial` | 已被accept，改善UX的零成本变更 |

### RFC阶段（中长期）
| Issue | 内容 | 状态 |
|---|---|---|
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | Shell命令分层确认策略 | Revision 3，maintainer已确认范围，P1 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 运行时会话所有权+传输适配器 | Revision 2，契约已确立 |
| [#10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) | 全面WASM插件架构 | 已被accept，NiuBlibing提出"everything is a plugin"愿景 |
| [#8850](https://github.com/zeroclaw-labs/zeroclaw/issues/8850) | 编译期feature flag→运行时WASM插件 | in-progress，JordanTheJet推进中 |
| [#10025](https://github.com/zeroclaw-labs/zeroclaw/issues/10025) | zeroclaw swarm——临时agent集群+TUI | RFC阶段，解决多agent编排痛点 |
| [#10069](https://github.com/zeroclaw-labs/zeroclaw/issues/10069) | Agent可移植性（导出/共享bundle） | in-progress，3阶段实施计划 |

---

## 7. 用户反馈摘要

### 核心痛点
1. **上下文截断不透明**：[#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) 用户配置了131k context但实际被32k硬限，#9713 PR正是对此的直接响应——用户需要知道"我的tokens去哪了"。
2. **群聊上下文串扰**：[#9772](https://github.com/zeroclaw-labs/zeroclaw/pull/9772) 反映Telegram/微信等多人群聊场景下，不同用户消息共享会话导致上下文污染，per-user session是明确需求。
3. **转录服务被误拒**：[#10106](https://github.com/zeroclaw-labs/zeroclaw/issues/10106) 用户配置了Groq/Deepgram等标准转录服务，但代理选择器逻辑错误拒绝，影响语音输入工作流。
4. **Windows桌面启动失败**：[#10111](https://github.com/zeroclaw-labs/zeroclaw/issues/10111) `TaskDialogIndirect`入口缺失，是Windows特定链接/依赖问题，影响桌面用户体验。

### 积极反馈信号
- **#9016**（已关闭）：用户对OpenAI reasoning effort兼容性的修复表达认可（1个👍）。
- **#10086**（ZeroCode日志可复制）与**#10087**（Postgres测试入CI）反映用户对可观测性和测试覆盖的关注正在被响应。

---

## 8. 待处理积压

### 需维护者关注
| Issue/PR | 状态 | 风险 | 建议 |
|---|---|---|---|
| [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | in-progress，无fix PR | S2用户配置被静默忽略 | 需确认是否已有WIP PR或未合并分支 |
| [#10118](https://github.com/zeroclaw-labs/zeroclaw/issues/10118) | in-progress | 307个Rust违规候选，清理工作量大 | 建议分阶段推进，优先处理production panic相关项 |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | 维护者决策队列 | RFC积压可能阻塞功能交付 | 作为决策入口，建议maintainer定期review队列 |
| [#8398](https://github.com/zeroclaw-labs/zeroclaw/issues/8398) | needs-author-action | 插件权限模型遗留开放问题 | 需author回应，当前粗粒度`PluginPermission`影响安全粒度 |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | needs-author-action | 沙箱策略两层漂移，长期未收敛 | 与#7155形成安全策略矩阵，建议协调推进 |

### 长期开放Issue
| Issue | 创建时间 | 内容 | 备注 |
|---|---|---|---|
| [#4668](https://github.com/zeroclaw-labs/zeroclaw/issues/4668) | 2026-03-25 | MariaDB memory backend支持 | 6个月+未推进，自托管用户明确需求 |
| [#7910](https://github.com/zeroclaw-labs/zeroclaw/issues/7910) | 2026-06-18 | Windows自更新测试覆盖 | PR #7853修复后缺失测试，跟进延迟 |

---

**报告生成时间**：2026-08-21 | **数据源**：GitHub API (zeroclaw-labs/zeroclaw)

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*