# OpenClaw 生态日报 2026-08-28

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-28 10:57 UTC

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



# OpenClaw 项目动态日报 — 2026-08-28

## 1. 今日速览

过去24小时内，OpenClaw 共处理 **500 条 Issue** 和 **500 条 PR**，新增/活跃 329 条，关闭 171 条；PR 待合并 315 条，已合并/关闭 185 条，整体社区活跃度保持高位。今日无新版本发布，但 **v2026.8.1-beta.3** 仍在征集反馈（#125626）。项目重点关注 Codex 集成稳定性、Gateway 内存泄漏和会话路由正确性三大方向，多个 P0/P1 级 Bug 已产出修复 PR，整体处于积极修复期。

---

## 2. 版本发布

**无新版本发布。**

当前 Beta 版本为 `v2026.8.1-beta.3`，相关反馈 Issue #125626 仍在收集测试报告。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#128223](https://github.com/openclaw/openclaw/pull/128223) | `fix(cli)` | 修复 `openclaw models aliases add` 别名解析来自错误快照的问题（关闭 #127618） |
| [#123535](https://github.com/openclaw/openclaw/pull/123535) | `fix(ui)` | 修复 Control UI 会话目录在窗口获得焦点时的刷新风暴问题 |
| [#125471](https://github.com/openclaw/openclaw/pull/125471) | `fix(models)` | 修复 Gateway 重启后 Claude CLI OAuth 刷新令牌丢失的严重兼容性问题 |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | `feat(ui)` | 新增安装策略警告审查功能，允许管理员确认后继续插件安装 |
| [#126138](https://github.com/openclaw/openclaw/pull/126138) | `fix(sessions)` | 消除 Telegram 会话中重复的 `delivery-mirror` 消息，修复会话转录污染 |
| [#128995](https://github.com/openclaw/openclaw/pull/128995) | `feat(ui)` | 在聊天头部新增完整会话操作菜单（置顶、标记未读、复制 ID 等） |
| [#128371](https://github.com/openclaw/openclaw/pull/128371) | `fix(release)` | 修复 beta.3 发布阻塞问题，允许聚焦式 beta 证据通过验证 |

**整体评估：** 今日 7 条 PR 被关闭/合并，涵盖 CLI、UI、OAuth 认证、会话管理和发布流程，项目稳定性在多个关键路径上得到实质性推进。

### 待审查的重要开放 PR

| PR | 优先级 | 说明 |
|---|---|---|
| [#130993](https://github.com/openclaw/openclaw/pull/130993) | P1 | 修复 OpenAI Responses 会话过早触发 compaction 的 6 个串联缺陷 |
| [#130563](https://github.com/openclaw/openclaw/pull/130563) | P1 | 修复顺序子 Agent 运行中过早返回最终响应的竞争条件 |
| [#127854](https://github.com/openclaw/openclaw/pull/127854) | P1 | 修复 cron 任务在会话重置后写入过期结果的问题 |
| [#122604](https://github.com/openclaw/openclaw/pull/122604) | P1 | 修复多 Agent 继承式 OAuth 配置下使用限制静默失效的严重 Bug |
| [#115510](https://github.com/openclaw/openclaw/pull/115510) | P1 | 安全修复：在密码学操作前对 Ed25519 验证输入做长度边界检查 |
| [#117151](https://github.com/openclaw/openclaw/pull/117151) | P1 | 修复取消/超时 Attached Unix 子进程时未清理后代进程的问题 |
| [#131575](https://github.com/openclaw/openclaw/pull/131575) | P1 | 修复 Android 端长回复被截断后无法查看末尾内容的可用性问题 |

---

## 4. 社区热点

### 评论数 Top Issue

1. **#42475 — 按 Agent 维度的成本预算网关级强制执行** (23 条评论, 👍1)
   用户强烈希望为每个 Agent 设置日/月消费上限，由网关在调度前拦截超支调用。反映运营方对 LLM 调用成本失控的普遍焦虑。[链接](https://github.com/openclaw/openclaw/issues/42475)

2. **#125626 — v2026.8.1 beta 反馈收集** (22 条评论, 👍0)
   官方 beta 测试反馈 Issue，持续收录测试报告和回归问题。[链接](https://github.com/openclaw/openclaw/issues/125626)

3. **#91009 — [P0] Codex PreToolUse hook 导致 CPU 100% + Gateway RPC 卡死** (21 条评论, 👍2)
   P0 级崩溃循环 Bug，`openclaw-hooks` 进程在 Codex 工具调用时大量 spawning，导致 Gateway 无响应。[链接](https://github.com/openclaw/openclaw/issues/91009)

4. **#48003 — [P1] Steer 模式无法在回合中途注入消息** (20 条评论, 👍4)
   `messages.queue.mode: "steer"` 配置下用户消息被延迟到回合结束后才注入，破坏了实时引导体验。[链接](https://github.com/openclaw/openclaw/issues/48003)

5. **#87744 — [P1] Codex-backed Telegram 回合反复超时** (18 条评论, 👍4)
   升级到 v2026.5.27 后 Telegram 会话无法到达 `turn/completed` 终态，消息丢失。[链接](https://github.com/openclaw/openclaw/issues/87744)

---

## 5. Bug 与稳定性

### P0 级

| Issue | 描述 | 修复状态 |
|---|---|---|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | Codex PreToolUse hook 导致 CPU 100% 和 Gateway RPC 卡死 | 待修复 PR |
| [#92057](https://github.com/openclaw/openclaw/issues/92057) | 多会话/多 Agent 负载下 Gateway 超时变慢（已关闭） | ✅ 已关闭 |
| [#131150](https://github.com/openclaw/openclaw/issues/131150) | Gateway 重启后所有 Slack DM 静默丢弃（新建，1天前） | 待修复 |

### P1 级

| Issue | 描述 | 修复状态 |
|---|---|---|
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | Steer 模式 mid-turn 消息注入失效 | 待修复 PR |
| [#87744](https://github.com/openclaw/openclaw/issues/87744) | Codex Telegram 回合反复超时 | 待修复 |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | 长时间对话后 write/exec 工具参数静默丢失 | 待修复 |
| [#98435](https://github.com/openclaw/openclaw/issues/98435) | MCP loopback 传输 Gateway 重启后不自动重连 | 待修复 |
| [#86215](https://github.com/openclaw/openclaw/issues/86215) | Codex OAuth 刷新失败导致 Agent 卡死数小时 | 待修复 |
| [#87109](https://github.com/openclaw/openclaw/issues/87109) | Gateway heap 空闲时增长至 1GB+，cron 静默失败 | 待修复 |
| [#41165](https://github.com/openclaw/openclaw/issues/41165) | Telegram DM 仍被路由到 main session 污染心跳 | 待修复 |
| [#129314](https://github.com/openclaw/openclaw/issues/129314) | 内部 runtime-context 消息偶发作为独立回合展示 | 待修复 |
| [#116010](https://github.com/openclaw/openclaw/issues/116010) | 所有持久会话被硬性限制 128k context（已关闭） | ✅ 已关闭 |
| [#99947](https://github.com/openclaw/openclaw/issues/99947) | Codex mirrored-session-history 在临时会话和故障转移时读取失败 | 待修复 |
| [#100941](https://github.com/openclaw/openclaw/issues/100941) | Gateway 并行工具扇出时丢弃 WebSocket 连接 (1006) | 待修复 |
| [#53008](https://github.com/openclaw/openclaw/issues/53008) | 内存压缩阻塞主处理通道导致 Bot 10+ 分钟无响应 | 待修复 |

### 已关闭的 Bug

| Issue | 描述 | 关联 PR |
|---|---|---|
| [#90354](https://github.com/openclaw/openclaw/issues/90354) | Pre-compaction 内存 flush 有界追加语义 | — |
| [#106760](https://github.com/openclaw/openclaw/issues/106760) | Telegram 多 content block 时首段文本被静默删除 | — |
| [#106914](https://github.com/openclaw/openclaw/issues/106914) | `models list` 在 2026.7.1 崩溃（TypeError） | — |
| [#103884](https://github.com/openclaw/openclaw/issues/103884) | GPT-5.6 Sol 在 OpenClaw Codex 运行时拒绝运行 | — |
| [#112248](https://github.com/openclaw/openclaw/issues/112248) | @openclaw/codex 插件启动时 TypeError 无法注册 | — |

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 路线图判断 |
|---|---|---|
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | 网关级按 Agent 成本预算强制执行 | ⭐ 高优先级，运营刚需，可能纳入下一稳定版 |
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | 多槽位内存架构（替换单一 memory slot） | 架构级改进，长期方向，需大型重构 |
| [#88154](https://github.com/openclaw/openclaw/issues/88154) | Slack Modal 交互式工作流支持 | UX 增强，中等优先级 |
| [#28300](https://github.com/openclaw/openclaw/issues/28300) | 主题定制系统（预设+自定义调色板） | 👍5 最高赞功能请求之一，用户呼声高 |
| [#52640](https://github.com/openclaw/openclaw/issues/52640) | 长时间通道回合的持久任务状态面板 | 状态可见性增强，Discord 优先 |
| [#71058](https://github.com/openclaw/openclaw/issues/71058) | 单网关支持多个 Azure/Teams Bot | 企业场景需求，当前架构限制 |
| [#55249](https://github.com/openclaw/openclaw/issues/55249) | 会话标签/昵称功能 | 小而实用的 UX 改进 |
| [#73537](https://github.com/openclaw/openclaw/issues/73537) | 发布标记生产就绪稳定性标签 | 运维需求，社区反馈强烈 |

---

## 7. 用户反馈摘要

- **成本焦虑普遍**：#42475 获高频讨论，用户希望网关层能主动拦截超预算调用，而非依赖外部监控。
- **Codex 集成稳定性堪忧**：#91009（CPU 卡死）、#87744（回合超时）、#112248（插件启动崩溃）形成一串 Codex 相关问题，反映 Codex 作为重点集成方向在成熟度上仍有明显缺口。
- **内存管理是长期痛点**：#87109（heap 增长至 1GB+）、#53008（compaction 阻塞主通道）揭示 Gateway 在长时间运行场景下的资源管理缺陷。
- **会话路由正确性反复出现问题**：#41165（Telegram DM 污染 main session）、#126138（重复 delivery-mirror 消息）说明会话隔离机制仍有漏洞。
- **多 Agent OAuth 继承逻辑有严重缺陷**：#122604 / #86215 指出继承式认证配置下使用限制会静默失效，直接影响多租户部署的安全性。
- **iOS App 性能**：#124759 反馈启用"显示推理和工具活动"后 App 严重卡顿，移动端体验有待优化。
- **Android 长回复截断无法回看**：#131575 已提交修复 PR，说明移动端消息展示是持续改进方向。

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 严重程度 | 关注点 |
|---|---|---|---|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | 2026-06-06 | P0 崩溃循环 | Codex hook CPU 卡死，78+ 天未解决 |
| [#86215](https://github.com/openclaw/openclaw/issues/86215) | 2026-05-24 | P1 认证卡死 | OAuth 刷新失败无告警，65+ 天 |
| [#87109](https://github.com/openclaw/openclaw/issues/87109) | 2026-05-27 | P1 内存泄漏 | heap 持续增长导致 cron 静默失败，62+ 天 |
| [#53008](https://github.com/openclaw/openclaw/issues/53008) | 2026-03-23 | P1 可用性 | 内存压缩阻塞 10+ 分钟，51

---

## 横向生态对比



# AI 智能体开源生态横向对比分析
**日期：2026-08-28 | 分析师：Agnes**

---

## 1. 生态全景

2026年8月末，个人AI助手开源生态呈现"一超多强、分层演进"格局：OpenClaw 以日均千级工单处理量稳居生态核心，主导 Codex 集成、多通道路由、网关稳定性等技术方向；NanoClaw、ZeroClaw、LobsterAI 处于高频迭代期，分别在 Provider 抽象、运行时架构、桌面客户端三端发力；NanoBot、Moltis 进入系统重构与质量巩固阶段；PicoClaw 保持中等活跃度聚焦边缘场景优化。生态整体从"功能野蛮生长"转向"架构收敛与稳定性攻坚"，多项目同步推进 Provider 契约、会话持久化、记忆系统可插拔化三大底层能力。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PR (24h) | Release | 待合并 | 健康度 |
|------|-------------|----------|---------|--------|--------|
| **OpenClaw** | 500 (329活跃/171关闭) | 500 (185合并/315待审) | 无（beta.3 收集反馈） | 315 | 🟢 高位活跃 |
| **NanoClaw** | 10 | 50 (4合并/46待审) | 无 | 46 | 🟡 高活跃但积压重 |
| **ZeroClaw** | 23 (21活跃/2关闭) | 50 (3合并/47待审) | 无（v0.8.5 冲刺中） | 47 | 🟢 高活跃 |
| **LobsterAI** | 5 (全部 stale 关闭) | 12 (100% 合并) | ✅ v2026.8.26 | 0 | 🟢 良好 |
| **NanoBot** | 1 | 27 | 无 | — | 🟢 活跃健康 |
| **IronClaw** | 32 | 47 (30合并) | 无 | 17 | 🟢 良好 |
| **PicoClaw** | 3 (1新/2关闭) | 7 (6合并/1待审) | 无 | 1 | 🟡 中等活跃 |
| **Moltis** | 0 | 2 (全部合并) | 无 | 0 | 🟡 稳定维护期 |
| **NullClaw** | 0 | 0 | 无 | 0 | 🔴 无活动 |
| **ZeptoClaw** | 0 | 0 | 无 | 0 | 🔴 无活动 |
| **Hermes Agent** | — | — | — | — | ⚠️ 数据缺失 |
| **CoPaw** | — | — | — | — | ⚠️ 数据缺失 |

---

## 3. OpenClaw 在生态中的定位

**规模优势**：OpenClaw 单日工单处理量（1000+）约为次活跃项目 NanoClaw/ZeroClaw 的 20-40 倍，社区参与深度与广度均居首位。

**技术路线差异**：
- OpenClaw 走**网关中心化架构**，强调 Codex 集成、多通道会话路由、OAuth 继承、内存压缩等生产级能力
- NanoClaw/ZeroClaw 走**Provider 抽象+运行时重构**路线，前者聚焦通道层契约统一，后者推进会话所有权与内部代理主链
- LobsterAI 走**桌面客户端+安装器**路线，侧重用户体验与发布质量
- NanoBot 走**架构解耦**路线，聚焦会话持久化、记忆系统、provider fallback 显式化

**社区规模推断**：OpenClaw  Issue 最高评论数达 27 条，NanoClaw/ZeroClaw 热点 Issue 评论 5-16 条，LobsterAI 热点 3 条，侧面反映 OpenClaw 社区参与度显著领先。

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|---------|---------|---------|
| **Provider 抽象与扩展** | OpenClaw、NanoClaw、ZeroClaw、NanoBot | OpenClaw 推进 Codex/Claude CLI 集成；NanoClaw zvi-fried 主导 6 条 Provider 契约 PR；ZeroClaw 推进 wire protocol 优先化；NanoBot 引入不可变 `ProviderAttempt` 使 fallback 显式化 |
| **会话持久化与并发安全** | OpenClaw、NanoBot、ZeroClaw | OpenClaw 修复会话路由污染与 compaction 阻塞；NanoBot 将持久化移出事件循环；ZeroClaw 推进 `SessionBackend` 契约与并发 claim |
| **记忆/上下文管理** | OpenClaw、NanoBot、ZeroClaw | OpenClaw 修复 heap 增长至 1GB+ 与 compaction 阻塞；NanoBot 重构记忆系统（确定性归档+显式召回接口）；ZeroClaw 推进上下文投影压缩 |
| **多通道/多 Agent 路由** | OpenClaw、NanoClaw、ZeroClaw | OpenClaw 修复 Telegram DM 污染、Codex 回合超时；NanoClaw 修复 Discord approval 卡片与 WhatsApp 大图假死；ZeroClaw Telegram 多消息流式传输 |
| **OAuth/认证稳定性** | OpenClaw、NanoBot | OpenClaw 修复 Claude CLI OAuth 刷新令牌丢失与多 Agent 继承限制静默失效；NanoBot 推进 MCP OAuth Token 自动刷新 |
| **成本预算控制** | OpenClaw | #42475 网关级按 Agent 维度强制执行成本预算，反映运营侧普遍焦虑 |

---

## 5. 差异化定位分析

| 维度 | OpenClaw | NanoClaw | ZeroClaw | LobsterAI | NanoBot | PicoClaw | Moltis |
|------|----------|----------|----------|-----------|---------|----------|--------|
| **功能侧重** | 网关+多通道+Codex集成 | Provider抽象+通道稳定性 | 运行时架构+会话所有权 | 桌面客户端+安装器 | Agent架构重构+记忆系统 | 边缘场景+IRC/Matrix | 沙箱安全+OpenAI兼容 |
| **目标用户** | 生产部署运营方、多租户场景 | 通道集成开发者 | 运行时研究者、架构师 | 个人桌面用户 | 架构研究者、深度定制用户 | 资源受限/协议兼容场景 | 安全敏感部署 |
| **技术架构** | 中心化网关+多Agent调度 | Provider契约+插件系统 | 会话所有权+内部代理主链 | Electron桌面+本地运行时 | 异步事件循环+共享边界 | Go轻量架构 | Rust+沙箱隔离 |
| **成熟度信号** | Beta版稳定化攻坚 | Provider重构攻坚期 | v0.8.5稳定线冲刺 | 补丁打磨期 | 系统重构期 | 依赖维护期 | 安全加固期 |

---

## 6. 社区热度与成熟度分层

```
┌─────────────────────────────────────────────────────┐
│  🔥 快速迭代层                                       │
│  OpenClaw · ZeroClaw · NanoClaw                      │
│  特征：高频 PR/Issue、架构级重构、积压待处理          │
├─────────────────────────────────────────────────────┤
│  ⚡ 稳定推进层                                       │
│  LobsterAI · NanoBot · IronClaw                      │
│  特征：高合并率、版本发布正常、质量打磨为主            │
├─────────────────────────────────────────────────────┤
│  🛡️ 质量巩固层                                       │
│  PicoClaw · Moltis                                   │
│  特征：低新增、依赖维护、安全性/兼容性修复              │
├─────────────────────────────────────────────────────┤
│  💤 停滞/低活层                                      │
│  NullClaw · ZeptoClaw · (Hermes/CoPaw 数据缺失)      │
│  特征：24h 无活动或摘要失败                           │
└─────────────────────────────────────────────────────┘
```

---

## 7. 值得关注的趋势信号

### 信号一：Provider 抽象成为生态共识
NanoClaw（6条系列PR）、ZeroClaw（wire protocol RFC）、NanoBot（`ProviderAttempt` 不可变重构）、OpenClaw（Codex/Claude CLI 双轨集成）同步推进 Provider 层标准化。对开发者的启示：**未来 Agent 框架的竞争力将越来越取决于 Provider 扩展的灵活性与契约清晰度**，建议优先关注支持多 Provider 统一接口的架构。

### 信号二：会话管理从"能用"转向"可靠"
OpenClaw 的会话路由污染（#41165/#126138）、NanoBot 的持久化解耦（#5580）、ZeroClaw 的 SessionBackend 契约（#10412）、NanoClaw 的 system rows 饥饿（#3568）——四个项目不约而同地暴露会话层并发与状态一致性问题。**会话所有权与持久化边界**正在成为下一代 Agent 框架的核心分歧点。

### 信号三：通道稳定性成为生产部署瓶颈
OpenClaw Codex Telegram 超时（#87744）、NanoClaw Discord approval 按钮错乱（#3456）+ WhatsApp 大图假死（#3575）、ZeroClaw Telegram 多消息流式（#8561）。**多通道接入的稳定性成本被严重低估**，尤其是非 Telegram 通道（Discord/WhatsApp/IRC）的异常边界处理仍是普遍短板。

### 信号四：内存/资源管理是长期痛点
OpenClaw Gateway heap 1GB+（#87109）与 compaction 阻塞（#53008）、NanoBot 记忆系统重构、ZeroClaw 上下文投影压缩——**长对话场景下的资源管理**是各框架共同的技术债务，尚未出现优雅的通用解法。

### 信号五：运营侧成本可控性诉求上升
OpenClaw #42475 网关级 Agent 成本预算强制执行获 23 条评论，反映多租户/生产场景中**成本可见与可控**已从可选需求变为刚需。结合 LobsterAI 多 Provider 支持请求（#1174），"按 Agent 计费+多模型切换"将是企业级部署的关键能力。

### 信号六：v0.8.x 稳定线冲刺潮
ZeroClaw v0.8.5（截止 8/30）、OpenClaw v2026.8.1-beta.3 收集反馈、LobsterAI v2026.8.26 补丁发布——生态头部项目正在从功能扩张转向**稳定线收敛**，预示下一阶段竞争焦点将从"谁功能多"转向"谁更稳定"。

---

**结语**：2026年8月末的开源智能体生态正处于"架构收敛+稳定性攻坚"的转折期。OpenClaw 以规模优势维持生态定义权，NanoClaw/ZeroClaw 以架构创新差异化突围，LobsterAI/NanoBot 以质量打磨积累用户信任。对开发者而言，关注 Provider 契约标准化、会话所有权模型、多通道异常边界处理这三条主线，将有助于把握下一代 Agent 框架的技术走向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-28

## 1. 今日速览

NanoBot 昨日（8/27–8/28）呈现**高频开发活跃度**，27 条 PR 更新、1 条 Issue 关闭，整体节奏紧凑。核心贡献者 `chengyongru` 主导了 Agent 架构重构、会话持久化解耦及记忆系统重构三条关键分支，多个 P1/P2 优先级 PR 当日完成合并。项目处于**系统级重构阶段**，稳定性与可扩展性为主要目标，暂无版本发布。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 摘要 |
|---|---|---|
| [#5580](https://github.com/HKUDS/nanobot/pull/5580) | fix(session) | 将会话持久化移出事件循环，注入共享 `SessionIO` 边界，解耦 Worker 调度与会话有序性 |
| [#5574](https://github.com/HKUDS/nanobot/pull/5574) | refactor(providers) | 引入不可变 `ProviderAttempt`，使 fallback 重试路由显式化，Runner 驱动完整 provider 解析链 |
| [#5569](https://github.com/HKUDS/nanobot/pull/5569) | refactor(agent) | 从 `AgentRunner` 中提取工具执行边界，新增 `nanobot.agent.tools.execution` 模块，不引入新状态容器 |
| [#5575](https://github.com/HKUDS/nanobot/pull/5575) | refactor(memory) | 移除 `consolidationRatio` 配置及比例驱动的归档循环，改为确定性归档旧前缀，保留最近 8 条消息 |
| [#5572](https://github.com/HKUDS/nanobot/pull/5572) | fix(agent) | 默认并发请求数改为无上限，仅在有显式环境变量时才施加限制，修复 WebUI 并发瓶颈 |
| [#4346](https://github.com/HKUDS/nanobot/pull/4346) | fix(providers) | 修复图片 stripped 后路径泄露问题，标记为不可查看 |
| [#5578](https://github.com/HKUDS/nanobot/pull/5578) | test(tui) | 修复 Windows TUI 剪贴板测试竞争条件 |
| [#5576/5577](https://github.com/HKUDS/nanobot/pull/5576) | fix(tui) | 修复 Herdr 分屏场景下 TUI 全屏布局异常 |

**整体推进评估**：今日合并工作集中于**会话层并发安全**、**provider fallback 显式化**和**记忆系统重构**三大主题，项目架构向更清晰的边界划分演进，预计可降低长期维护复杂度。

---

## 4. 社区热点

### 高关注 Issue / PR

- **[#4429](https://github.com/HKUDS/nanobot/issues/4429)** `[CLOSED]` feat: Allow custom provider to configure thinking style
  - 核心诉求：VolcEngine/Doubao 等厂商使用非标准 thinking 参数（`{"thinking": {"type": "enabled"}}`），现有 `custom` provider 无法启用推理模式，用户期望支持自定义配置。
  - 已合并关闭，为多 provider 适配提供扩展能力。

- **[#5568](https://github.com/HKUDS/nanobot/pull/5568)** `[OPEN]` refactor(agent): let runner own context compaction
  - 作者 `chengyongru`，待合并。核心改动：`AgentRunner` 在每个 provider 调用前自行管理上下文压缩，若最新工具调用使当前 turn 过大，则先压缩再阻塞本轮执行。
  - 关联 P1 优先级，是上下文管理重构的关键一环。

- **[#5580](https://github.com/HKUDS/nanobot/pull/5580)** `[CLOSED]` fix(session): move persistence off event loop
  - P1 修复，解决异步持久化阻塞事件循环的潜在性能隐患，已合并。

- **[#5388](https://github.com/HKUDS/nanobot/pull/5388)** `[OPEN]` feat(agent): budget model-visible MCP schemas
  - 新增可选项：为模型可见的 MCP tool schema 设置字节预算（默认关闭），通过确定性选择子集保持 run 内稳定。冲突状态，尚未合并。

---

## 5. Bug 与稳定性

| 问题 | 级别 | 状态 | 关联 PR |
|---|---|---|---|
| Windows 上 TUI 退出后光标位置异常 | P2 | ✅ 已修复 | [#5581](https://github.com/HKUDS/nanobot/pull/5581) `[OPEN]` |
| Windows 剪贴板测试竞争条件 | P2 | ✅ 已修复 | [#5578](https://github.com/HKUDS/nanobot/pull/5578) |
| Windows `os.replace()` 瞬时权限拒绝导致 gateway 崩溃 | P2 | 🔶 待合并 | [#5382](https://github.com/HKUDS/nanobot/pull/5382) `[OPEN]` |
| 删除后的会话仍被延迟消息重建 | P2 | 🔶 待合并 | [#5483](https://github.com/HKUDS/nanobot/pull/5483) `[OPEN]` |
| WebUI 模型重试状态未向用户暴露 | P2 | 🔶 待合并 | [#5504](https://github.com/HKUDS/nanobot/pull/5504) `[OPEN]` |
| Herdr 分屏 TUI 布局破坏 | P2 | ✅ 已修复 | [#5576/5577](https://github.com/HKUDS/nanobot/pull/5576) |
| OAuth Token 过期后不自动刷新（MCP） | P2 | 🔶 待合并 | [#5573](https://github.com/HKUDS/nanobot/pull/5573) `[OPEN]` |

> **稳定性评分**：今日 Windows 平台相关 Bug 修复集中，共 3 项已合、3 项待合。跨平台稳定性有所提升，但 `os.replace()` 和会话重建两个 Bug 仍待合并，建议优先跟进。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 状态 | 纳入可能性 |
|---|---|---|---|
| 自定义 provider 配置 thinking 风格 | #4429 | ✅ 已合并 | 已完成，后续 provider 扩展可复用此模式 |
| 记忆系统显式召回（替代自动注入 system prompt） | #5571 / #5570 | 🔶 待合并 | 高优先级，已定义 `MemoryBackend` 接口，预计纳入下一版本 |
| MCP schema 字节预算控制 | #5388 | 🔶 待合并，有冲突 | 中，需解决冲突后合并 |
| 每次 spawn 独立模型预设（allowlist） | #5561 | 🔶 待合并 | 中，解决 #4231 复用需求 |
| MCP OAuth Token 自动刷新 | #5573 | 🔶 待合并 | 高，影响生产环境稳定性 |

**路线图信号**：项目明显在向**记忆系统可插拔化**、**会话并发安全**、**provider 适配扩展**三个方向演进，下一版本预计以记忆重构和 MCP OAuth 自动刷新为亮点。

---

## 7. 用户反馈摘要

- **Thinking 模式适配需求强烈**：#4429 的提出表明多模型 provider（VolcEngine、Doubao 等）的 thinking/reasoning 参数差异是真实痛点，自定义化配置已被实现。
- **Windows 稳定性问题集中反馈**：多条 PR 涉及 Windows TUI 光标、剪贴板、`os.replace()` 权限错误，说明 Windows 用户活跃但体验亟待改善。
- **会话重建 Bug 影响数据完整性**：#5483 反映用户删除会话后仍被意外重建，属于数据一致性问题，用户期望删除操作具有最终性。
- **WebUI 重试反馈缺失**：#5504 指出模型重试时用户看不到状态，影响交互体验。

---

## 8. 待处理积压

| PR/Issue | 类型 | 状态 | 提醒 |
|---|---|---|---|
| [#5382](https://github.com/HKUDS/nanobot/pull/5382) | fix(session) | 待合并 | Windows `os.replace()` 崩溃修复，P2 优先级，建议优先合并 |
| [#5483](https://github.com/HKUDS/nanobot/pull/5483) | fix(session) | 待合并 | 删除会话重建 Bug 修复，影响数据一致性 |
| [#5388](https://github.com/HKUDS/nanobot/pull/5388) | feat(agent) | 待合并，冲突 | MCP schema 字节预算，需解决冲突后推进 |
| [#5581](https://github.com/HKUDS/nanobot/pull/5581) | fix(tui) | 待合并 | Windows TUI 光标位置修复 |
| [#5573](https://github.com/HKUDS/nanobot/pull/5573) | fix(mcp) | 待合并 | OAuth Token 自动刷新，P2 稳定性修复 |

---

**整体健康度评估**：🟢 活跃且健康。日提交密度高，核心维护者响应迅速，Bug 修复与功能重构并行推进。主要风险点为 Windows 平台残留问题及 MCP OAuth 刷新的合并进度，建议维护者优先处理上述积压项。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 | 2026-08-28

---

## 1. 今日速览

今日PicoClaw项目活跃度中等，共处理 **3个Issues**（新开1条，关闭2条）与 **7个PRs**（待合并1条，已合并6条）。无新版本发布。社区贡献以依赖更新维护为主（5条Dependabot PR），另有1条界面性能优化PR待合并。整体项目状态稳定，核心维护工作聚焦于依赖版本升级与UI体验改进。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭 PR（6条）

| PR | 类型 | 作者 | 说明 |
|----|------|------|------|
| [#3347](https://github.com/sipeed/picoclaw/pull/3347) | 🔧 修复 | iMilnb | **Web UI 界面卡顿修复** — 解决聊天区域大量文本时的渲染延迟问题，已在桌面端和移动端（Brave浏览器）验证通过。 |
| [#3336](https://github.com/sipeed/picoclaw/pull/3336) | 📦 依赖 | Dependabot | 升级 `aws/aws-sdk-go-v2/service/bedrockruntime` 1.53.3 → 1.57.1 |
| [#3335](https://github.com/sipeed/picoclaw/pull/3335) | 📦 依赖 | Dependabot | 升级 `aws/aws-sdk-go-v2/config` 1.32.25 → 1.32.35 |
| [#3334](https://github.com/sipeed/picoclaw/pull/3334) | 📦 依赖 | Dependabot | 升级 `anthropic-sdk-go` 1.55.1 → 1.62.0 |
| [#3333](https://github.com/sipeed/picoclaw/pull/3333) | 📦 依赖 | Dependabot | 升级 `mautrix`（Matrix客户端）0.27.0 → 0.29.0 |
| [#3332](https://github.com/sipeed/picoclaw/pull/3332) | 📦 依赖 | Dependabot | 升级 `aws/aws-sdk-go-v2` 1.42.0 → 1.43.4 |
| [#1555](https://github.com/sipeed/picoclaw/pull/1555) | 📦 修复 | xuwei-xy | 合并修复 PR #1390、#1389、#1383、#1381（历史积压清理） |

> **进展评估**：今日合并以依赖更新为主，核心功能推进有限。PR #3347 是对用户体验有价值的性能修复，值得重点关注。

---

## 4. 社区热点

### 活跃 Issue

| Issue | 状态 | 评论数 | 摘要 | 链接 |
|-------|------|--------|------|------|
| #3287 | 🔵 OPEN | 8 | IRCv3长消息处理 | [#3287](https://github.com/sipeed/picoclaw/issues/3287) |

**分析**：Issue #3287 评论数最多（8条），围绕 IRC 消息截断问题展开讨论。用户期望 PicoClaw 能将超过 512 字节的消息视为一条连贯消息，而非按 IRC 协议自动分割。该问题涉及协议兼容性与用户体验的平衡，是当前社区关注度最高的开放问题。

---

## 5. Bug 与稳定性

| 问题 | 来源 | 严重程度 | 状态 |
|------|------|----------|------|
| Web UI 聊天区域大量文本时卡顿 | PR #3347 | 🟡 中（体验问题） | ✅ 已修复，待合并 |

> 暂无严重 Bug 或回归问题报告。

---

## 6. 功能请求与路线图信号

### 已关闭的功能请求

| Issue | 诉求 | 状态 | 纳入可能性 |
|-------|------|------|-----------|
| [#3331](https://github.com/sipeed/picoclaw/issues/3331) | 支持非 whisper-* 模型用于音频转录（`/audio/transcriptions` 端点） | 🟢 CLOSED [stale] | 低（缺乏近期活跃） |
| [#3330](https://github.com/sipeed/picoclaw/issues/3330) | `delegate`/`spawn`/`subagent` 工具支持运行时动态指定模型 | 🟢 CLOSED [stale] | 低（缺乏近期活跃） |

> 两条功能请求均标注 `[stale]` 后关闭，反映社区对这些需求的讨论热度已下降，短期内进入路线图的可能性较低。

---

## 7. 用户反馈摘要

- **界面体验**：用户 iMilnb 反馈 Web UI 在聊天区域文本量大时出现明显卡顿，已通过 PR #3347 修复，验证在桌面端和移动端（Brave）均无延迟。
- **IRC 兼容性**：Issue #3287 中用户希望 PicoClaw 更好地处理 IRCv3 长消息，避免消息被截断为多条。这是当前用户痛点之一，8条评论显示讨论较为深入。
- **语音转录灵活性**：Issue #3331 用户希望支持更广泛的 ASR 模型（不限于 `*-whisper-*`），反映出对转录速度和模型多样性的需求。
- **多Agent模型灵活性**：Issue #3330 用户期望在子Agent调用时能动态覆盖模型，而非静态配置，反映了对多Agent协作场景灵活性的需求。

---

## 8. 待处理积压

| 项目 | 类型 | 创建时间 | 最后活跃 | 建议 |
|------|------|----------|----------|------|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) | Feature | 2026-07-22 | 2026-08-27 | 活跃讨论中，建议维护者跟进 IRCv3 长消息支持方案 |
| [#3347](https://github.com/sipeed/picoclaw/pull/3347) | Fix | 2026-08-27 | 2026-08-28 | 待合并，建议优先审核以解决 UI 卡顿问题 |

---

**健康度评分**：🟡 中等活跃 — 依赖维护良好，但核心功能迭代节奏较慢，社区功能请求讨论热度有下降趋势。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目日报 — 2026-08-28

## 1. 今日速览

NanoClaw 在过去24小时内保持**高活跃度**：共更新 60 个工单（10 Issues + 50 PRs），其中4个 PR 已合并/关闭，46 个仍待合并，无新版本发布。今日社区焦点集中在 **Discord/WhatsApp 通道附件处理缺陷** 与 **Provider 层重构** 两条主线——前者由多个高严重度 Issue 集中暴露，后者由 zvi-fried 主导的系列 Refactor PR 密集推进，显示出项目在通道稳定性和provider抽象两个层面同时发力。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭（4 条）

| # | 类型 | 作者 | 说明 |
|---|------|------|------|
| [#3572](https://github.com/nanocoai/nanoclaw/issues/3572) | Bug Fix | BuckG71 | 已关闭，与 #2888 同源—— inbound 附件 URL 无法被消费者消费的问题进入修复流程 |
| [#3594](https://github.com/nanocoai/nanoclaw/pull/3594) | Fix | chiptoe-svg | 修复定时任务错误 turn 被静默丢弃的 bug（#3223），错误 turn 现正确标记为 FAILED 并写入 chat 消息 |
| [#3595](https://github.com/nanocoai/nanoclaw/pull/3595) | Fix | Koshkoshinsk | CLI 新增跨 session 状态查询能力，提升运维可观测性 |
| [#3471](https://github.com/nanocoai/nanoclaw/pull/3471) | Fix | amit-shafnir | 修复 pnpm workspace 中 `minimumReleaseAge` 配置因嵌套在 `pnpm:` key 下而失效的问题，providers 分支依赖锁恢复正常 |

### 重点推进中（46 条待合并）

- **Provider 重构系列（zvi-fried 主导，6 条 PR）**：#3581/#3584/#3585/#3586/#3588/#3591 系统性地声明并实现了 Codex/OpenCode/Host/Runtime 等 provider 契约，同时将 provider 指令渲染迁移至 core-owned canon。这是项目架构层面的一次重要整合，完成后 provider 扩展将具备统一的契约基础。
- **Google Gemini 支持**：[#2136](https://github.com/nanocoai/nanoclaw/pull/2136)（farooqu）持续跟进，采用与 Codex 相同的 `app-server` JSON-RPC over stdio 模式，预计为项目带来首个非 Anthropic/OpenAI 生态的 provider。
- **Codex 认证重构**：[#3489](https://github.com/nanocoai/nanoclaw/pull/3489) 用结构化 setup-driver 替代 clack 交互式提示，使 Codex 登录可在非 TTY 环境运行。
- **OpenCode provider 稳定性**：[#3463](https://github.com/nanocoai/nanoclaw/pull/3463) 修复了 `message.part.delta` 文本回退的消息丢失 race condition（原 margin ~78ms）；[#2878](https://github.com/nanocoai/nanoclaw/pull/2878) 修复了 stale OneCLI secret 导致重连失败的问题。

---

## 4. 社区热点

### 🔥 高关注 Issue

**[#3456](https://github.com/nanocoai/nanoclaw/issues/3456)** — *chat-sdk-bridge: Discord approval 卡片按钮值错乱*
- **严重度：高**。`ask_question` 卡片同时设置 `id` 和 `value` 导致 Discord 自定义 ID 被破坏，所有按钮点击均解析到错误选项，**approval / ask_question 功能在 Discord 上完全不可用**。5 条评论，由 DawoudIO 于 8/23 创建，8/27 仍活跃。

**[#2888](https://github.com/nanocoai/nanoclaw/issues/2888)** — *Discord 等 url-only 适配器丢弃图片/文件附件*
- 用户发送图片或文件后，agent 仅收到元数据 `{type, name, mimeType, size}`，内容本身从未下载。Telegram 正常。与 #3572 同源，已有关闭的修复 issue。**根因在 `messageToInbound` 仅下载字节但未传递 fetchData 能力。**

**[#3576](https://github.com/nanocoai/nanoclaw/issues/3576)** — *限流 turn 向频道批量发送重复错误通知*
- `deliverErrorResult` 无退避、无冷却、无去重，每次重试命中限流都会产生一条独立通知，**生产环境可能造成频道消息 flood**。由 DawoudIO 创建，问题描述精确指向 `container/agent-runner/src/poll-loop.ts`。

**[#3568](https://github.com/nanocoai/nanoclaw/issues/3568)** — *Pending system rows 饥饿入队导致 agent 静默停止响应*
- 当 session 累积超过 `maxMessagesPerPrompt`（默认 10）条 pending `kind='system'` 行时，agent 对所有入站消息停止响应且无任何错误提示，**需手动 `/clear` 恢复**。BuckG71 报告，问题隐蔽性强。

**[#3575](https://github.com/nanocoai/nanoclaw/issues/3575)** — *WhatsApp 大图楔入 session*
- 超过 2000px 单张照片导致整个 SDK session 所有 turn 失败，**agent 呈现"假死"状态持续数小时**。glifocat 提交的功能性修复 PR 已列出。

### 🔥 高关注 PR

- **[#2136](https://github.com/nanocoai/nanoclaw/pull/2136)** — Google Gemini provider（自 4/29 创建，持续活跃）
- **[#3356](https://github.com/nanocoai/nanoclaw/pull/3356)** — Cursor Agent SDK payload 支持（zvi-fried）
- **[#1995](https://github.com/nanocoai/nanoclaw/pull/1995)** — OpenCode provider 自定义端点 + `/add-local-llama` skill（TeeJS）

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | Fix PR |
|--------|-------|------|--------|
| 🔴 高 | [#3456](https://github.com/nanocoai/nanoclaw/issues/3456) | Discord approval 按钮 `value` 参数破坏 custom_id，功能完全不可用 | 待修 |
| 🔴 高 | [#3575](https://github.com/nanocoai/nanoclaw/issues/3575) | WhatsApp 大图楔入 session，agent 假死数小时 | [#3575](https://github.com/nanocoai/nanoclaw/issues/3575)（glifocat 已提修复方案） |
| 🔴 高 | [#3568](https://github.com/nanocoai/nanoclaw/issues/3568) | system rows 堆积导致 agent 静默停止响应，无报错 | 待修 |
| 🟡 中 | [#2888](https://github.com/nanocoai/nanoclaw/issues/2888) | Discord/URL-only 适配器丢弃附件内容 | [#3572](https://github.com/nanocoai/nanoclaw/issues/3572) 已关闭，修复中 |
| 🟡 中 | [#3576](https://github.com/nanocoai/nanoclaw/issues/3576) | 限流错误通知无去重，频道消息 flood | 待修 |
| 🟡 中 | [#3532](https://github.com/nanocoai/nanoclaw/issues/3532) | `add-*-tool` per-agent 作用域遗漏新创建 agent | 待修 |
| 🟡 中 | [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) | `update-nanoclaw` skill 误判本地 adapter 为 skill 并覆盖 | 待修 |

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 判断 |
|------|----------|------|
| **自动绑定唯一可用 agent-group**，避免每次 @mention 手动选择 | [#3577](https://github.com/nanocoai/nanoclaw/issues/3577) | 体验优化类，DawoudIO 提出，实现成本低， likely 纳入近期 |
| **防止 registry skills 与 channels/providers 漂移** | [#3579](https://github.com/nanocoai/nanoclaw/issues/3579) | 工程质量类，zvi-fried/glifocat 关注，与 Provider 重构 PR 系列呼应 |
| **Google Gemini provider** | [#2136](https://github.com/nanocoai/nanoclaw/pull/2136) | 自 4/29 维护中，架构已对齐 Codex 模式，预计下一版本 |
| **本地 LLM 接入（/add-local-llama）** | [#1995](https://github.com/nanocoai/nanoclaw/pull/1995) | 通过 OpenCode provider 的 env-gated 自定义端点实现，社区需求明确 |
| **Cursor Agent SDK payload** | [#3356](https://github.com/nanocoai/nanoclaw/pull/3356) | zvi-fried 推进，与 provider 重构方向一致 |

---

## 7. 用户反馈摘要

**核心痛点：**

1. **Discord 通道可用性严重受损**：[#3456](https://github.com/nanocoai/nanoclaw/issues/3456) 用户 DawoudIO 指出 approval 卡片"every click resolves to the wrong option"，[#2888](https://github.com/nanocoai/nanoclaw/issues/2888) 用户 eagansilverpathmarketing 报告附件功能完全失效。**Telegram 正常而 Discord 异常**，问题集中在 `chat-sdk-bridge.ts` 的 `messageToInbound` 和 `ask_question` 卡片构建逻辑。

2. **WhatsApp 极端用例导致 session 假死**：[#3575](https://github.com/nanocoai/nanoclaw/issues/3575) 用户 glifocat 发现一张超过 2000px 的大图即可使整个 session 陷入永久性错误状态，需手动 `/clear`，**用户体验极差**。

3. **限流错误通知缺乏节流**：[#3576](https://github.com/nanocoai/nanoclaw/issues/3576) 用户 DawoudIO 在生产环境观察到 rate-limit 触发后频道被大量重复错误消息淹没，`deliverErrorResult` 无 backoff/dedup 机制。

4. **system message 堆积导致静默失效**：[#3568](https://github.com/nanocoai/nanoclaw/issues/3568) 用户 BuckG71 描述的"agent 静默停止响应且无任何错误"是最隐蔽的 bug 之一，**难以排查**。

5. **更新机制误伤本地定制**：[#3529](https://github.com/nanocoai/nanoclaw/issues/3529) 用户 glifocat 反馈 `update-nanoclaw` skill 将用户自写 adapter 误判为 skill 并覆盖，**缺乏 opt-out 机制**。

---

## 8. 待处理积压

| Issue/PR | 创建时间 | 状态 | 风险 |
|----------|----------|------|------|
| [#2136](https://github.com/nanocoai/nanoclaw/pull/2136) — Google Gemini provider | 2026-04-29 | OPEN，持续活跃 | 4 个月未合并，长期 feature 积压 |
| [#1995](https://github.com/nanocoai/nanoclaw/pull/1995) — OpenCode 自定义端点 + local-llama | 2026-04-24 | OPEN | 4 个月未合并 |
| [#1994](https://github.com/nanocoai/nanoclaw/pull/1994) — Codex per-group 自定义端点路由 | 2026-04-24 | OPEN | 4 个月未合并，与 #1995 配套 |
| [#2872](https://github.com/nanocoai/nanoclaw/pull/2872) — OpenCode per-group model override | 2026-06-27 | OPEN | 2 个月未合并 |
| [#2865](https://github.com/nanocoai/nanoclaw/pull/2865) — OpenCode stale session 旋转 | 2026-06-26 | OPEN | 2 个月未合并 |
| [#2878](https://github.com/nanocoai/nanoclaw/pull/2878) — Codex stale secret 重连修复 | 2026-06-28 | OPEN | 2 个月未合并 |
| [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) — update skill 覆盖本地 adapter | 2026-08-25 | OPEN，1 评论 | 用户体验问题，无 fix PR |
| [#3532](https://github.com/nanocoai/nanoclaw/issues/3532) — add-*-tool 作用域遗漏 | 2026-08-25 | OPEN，1 评论 | 功能缺陷，无 fix PR |
| [#3577](https://github.com/nanocoai/nanoclaw/issues/3577) — 自动绑定唯一 agent-group | 2026-08-27 | OPEN，0 评论 | 新功能请求，尚未分配 |

---

**整体健康度评估**：项目正处于 **Provider 层重构攻坚期**（6 条系列 PR 密集提交），同时 **Discord/WhatsApp 通道稳定性问题集中爆发**。建议维护者优先处理 #3456 和 #3575 两个高严重度 bug，这两个问题直接影响核心聊天场景的可用性。长期未合并的 provider 系列 PR（#2136、#1995 等）也需安排 review 排期。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报（2026-08-28）

## 1. 今日速览
过去24小时 IronClaw 保持高活跃开发节奏，共更新 Issue 32 条、PR 47 条，其中 30 条已合并/关闭，核心维护者（`serrrfirat`、`henrypark133`、`italic-jinxin`、`pranavraja99`）与社区贡献者协同高效。今日工作主线高度收敛于 **Reborn 架构沙箱化**、**记忆/学习系统能力补齐**、**上下文投影压缩** 以及 **Gmail/Telegram/MCP 渠道稳定性**。整体代码库向“可信主机+持久化沙箱+结构化记忆”的确定性架构稳步演进，项目健康度良好，技术债清理与体验打磨同步推进。

## 2. 版本发布
无新版本发布。

## 3. 项目进展（已合并

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI 项目日报 | 2026-08-28

---

## 1. 今日速览

LobsterAI 今日保持**高活跃度**，过去24小时内共处理 **17 条** 开发动态（12 PR 全部合并、5 Issues 全部关闭），并发布了 **v2026.8.26** 新版本。PR 合并率 100%，说明维护者响应及时、代码审查流程顺畅。Issues 全部 stale 关闭，其中多为用户咨询类问题，整体项目健康度良好。新版本聚焦安装器稳定性与 UI 优化，未见大规模功能突破，但以修复和打磨为主。

---

## 2. 版本发布

### 📦 v2026.8.26（2026-08-26 发布）

| 类型 | 变更内容 | 链接 |
|------|---------|------|
| Bug Fix | `fix(installer): support silent upload-first web builds` — 支持静默模式下先上传的 Web 构建安装 | [PR #2511](https://github.com/netease-youdao/LobsterAI/pull/2511) |
| Bug Fix | `fix(installer): hide banner for dictbind silent package` — 隐藏 dictbind 静默包的横幅广告 | [PR #2512](https://github.com/netease-youdao/LobsterAI/pull/2512) |

**评估：** 本次版本为**补丁性质**，主要修复 Windows 静默安装场景下的体验问题，无破坏性变更，无迁移注意事项。

---

## 3. 项目进展

今日合并 **12 条 PR**，覆盖安装包加固、UI 优化、测试补齐、状态管理修复等多个方向：

| PR | 作者 | 领域 | 摘要 | 链接 |
|----|------|------|------|------|
| #2572 | liuzhq1986 | release/build | 2026.8.24 版本发布分支合并 | [#2572](https://github.com/netease-youdao/LobsterAI/pull/2572) |
| #2571 | liuzhq1986 | renderer | 修复手机号昵称显示问题 | [#2571](https://github.com/netease-youdao/LobsterAI/pull/2571) |
| #2570 | liuzhq1986 | renderer | 解决手机号脱敏合并冲突，替换测试数据为合成 Fixtures | [#2570](https://github.com/netease-youdao/LobsterAI/pull/2570) |
| #2569 | liuzhq1986 | renderer | 手机号昵称修复（重复提交） | [#2569](https://github.com/netease-youdao/LobsterAI/pull/2569) |
| #2568 | Mind-Hand | renderer/main | 折叠更多模型分组 + 同步侧边栏横幅调度（支持服务端版本门控与本地过期） | [#2568](https://github.com/netease-youdao/LobsterAI/pull/2568) |
| #2567 | liuzhq1986 | renderer | 2026.8.24 版本修复 | [#2567](https://github.com/netease-youdao/LobsterAI/pull/2567) |
| #2551 | fisherdaddy | renderer/main | 修复应用更新后 preserve ready state 问题 | [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) |
| #2566 | fisherdaddy | build/windows | Windows 安装包 payload 截断加固 | [#2566](https://github.com/netease-youdao/LobsterAI/pull/2566) |
| #2565 | liugang519 | renderer | 优化库列表查询切换与重新加载状态（防闪烁、防游标污染） | [#2565](https://github.com/netease-youdao/LobsterAI/pull/2565) |
| #1163 | gongzhi-netease | stale | 定时任务"立即运行"交互优化（乐观更新 + Gateway 状态同步） | [#1163](https://github.com/netease-youdao/LobsterAI/pull/1163) |
| #1165 | MaoQianTu | stale | 补全 `openclawMemoryFile` 与 `openclawLocalTimeContextPrompt` 的 75 个 Vitest 单测 | [#1165](https://github.com/netease-youdao/LobsterAI/pull/1165) |
| #1166 | leedalei | stale | 防止自定义 Agent 名称重复 | [#1166](https://github.com/netease-youdao/LobsterAI/pull/1166) |

**关键进展：**
- **安装器稳定性**显著提升（PR #2566、#2511、#2512），修复了 Windows 静默安装场景下的多个边界问题。
- **UI 体验**持续打磨：手机号脱敏显示优化、库列表防闪烁、更多模型分组折叠。
- **质量保障**：75 个新增单元测试覆盖了此前零覆盖的核心模块。
- **Agent 创建**增加了名称重复校验，修复了潜在的数据冲突问题。

---

## 4. 社区热点

今日 5 条 Issues 全部在 2026-08-27 被标记 stale 并关闭，按关注度与讨论价值排序：

| Issue | 主题 | 作者 | 评论数 | 链接 |
|-------|------|------|--------|------|
| #1179 | 3.31 版本强制沙箱怎么关闭？ | syrphid | 3 | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) |
| #1173 | 卸载后程序仍运行（安全疑虑） | 773780238 | 2 | [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) |
| #1180 | 修改自建 Agent 触发网关反复重启 | HsiYaTung | 2 | [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) |
| #1174 | 支持多个自定义模型提供商 | neoliuhua | 2 | [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) |
| #1162 | 补充 openclaw 模块 Vitest 单测 | MaoQianTu | 2 | [#1162](https://github.com/netease-youdao/LobsterAI/issues/1162) |

**热点分析：**
- **#1179**（3 条评论）反映用户对**沙箱模式**的困惑，认为 3.31 版本新增了强制沙箱且缺少关闭入口，说明版本更新中的功能变更缺少足够的用户引导。
- **#1173** 涉及**用户对软件行为的信任问题**，"卸载后门"的质疑虽被标记 stale，但反映出卸载流程的彻底性需要官方明确说明。
- **#1180** 是真实 Bug 报告：修改自建 Agent 图标触发网关重启，**可能与 #1166（防止 Agent 名称重复）属于同一次 Agent 相关修复的关联问题**。
- **#1174** 是明确的功能请求：多自定义模型提供商，目前单一 Provider 限制影响多场景用户。
- **#1162** 是技术改进需求，已合并为 PR #1165，体现社区贡献者对测试覆盖的重视。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | Fix PR | 状态 |
|---------|-------|------|--------|------|
| 🟠 中 | #1180 | 修改自建 Agent 图标触发网关反复重启（v2026.3.31） | 关联 #1166（Agent 创建逻辑修复） | 已关闭 |
| 🟡 低 | #1179 | 3.31 强制沙箱无关闭入口，用户无法回退 | 无 | 已关闭（stale） |
| 🟡 低 | #1173 | 卸载后进程仍残留运行 | 无 | 已关闭（stale） |

**评估：** 今日无新增 Bug 报告。关闭的 Issues 中，#1180 有潜在的关联修复（#1166），但网关重启问题的根因尚未单独确认，建议在后续版本中验证。#1179 和 #1173 无明确 fix PR，属于**体验优化类问题**，需关注是否纳入后续版本规划。

---

## 6. 功能请求与路线图信号

| 请求 | Issue | 信号强度 | 分析 |
|------|-------|---------|------|
| 多自定义模型提供商 | #1174 | 🟡 中 | 用户明确表达多 Provider 管理需求，当前仅支持单个。若项目有模型生态扩展计划，可考虑纳入下一版本。 |
| 沙箱模式可配置 | #1179 | 🟢 低 | 用户希望保留关闭选项，建议文档补充说明或在设置中增加开关。 |
| 卸载流程彻底性 | #1173 | 🟡 中 | 涉及用户信任，建议在安装包中添加卸载后清理确认机制。 |

**PR 与路线图关联：**
- PR #2568（折叠更多模型分组）暗示项目正在**整合模型管理入口**，可能与 #1174 的多 Provider 需求存在协同空间。
- PR #2551（修复更新后状态保持）和 PR #2565（库列表状态优化）体现项目对**应用稳定性与流畅度**的持续投入。

---

## 7. 用户反馈摘要

| 来源 | 用户原意提炼 | 情绪倾向 |
|------|-------------|---------|
| #1179 | "半夜更新了 3.31 要强制沙箱了吗？找不到关的按钮" | 😠 不满（功能变更无引导） |
| #1173 | "卸载后还能运行，是不是留后门？" | 😠 不信任（安全感缺失） |
| #1180 | "改了个图标网关反复重启，删了就好了" | 😐 困扰（Bug 复现路径明确） |
| #1174 | "希望保留多个自定义 Provider，弃用旧的时不想丢历史配置" | 😊 建设性（合理需求） |
| #1162 | 主动贡献 75 个测试用例 | 😊 正向（社区贡献活跃） |

**核心痛点：**
1. **版本更新缺少变更引导**，用户对新增的强制沙箱模式感到突兀。
2. **卸载流程不够透明**，残留进程引发安全疑虑。
3. **Agent 管理功能**存在稳定性问题（图标修改触发重启）和体验限制（名称重复、单 Provider）。

---

## 8. 待处理积压

| Issue | 类型 | 创建时间 | 最后活跃 | 积压天数 | 优先级建议 |
|-------|------|---------|---------|---------|-----------|
| #1179 | 体验优化 | 2026-03-31 | 2026-08-27 | ~150 天 | 🟡 中 |
| #1173 | 安全信任 | 2026-03-31 | 2026-08-27 | ~150 天 | 🟡 中 |
| #1174 | 功能请求 | 2026-03-31 | 2026-08-27 | ~150 天 | 🟢 低 |

> ⚠️ 以上 Issues 均标记为 `stale` 并关闭，但未形成正式修复 PR。建议维护者评估是否需要在后续版本中补充文档说明或功能迭代，避免同类问题再次积累。

---

## 📊 项目健康度总评

| 指标 | 评分 | 说明 |
|------|------|------|
| PR 合并率 | ✅ 100% | 今日 12/12 全部合并 |
| Issue 响应 | ⚠️ 中等 | 5 条全部 stale 关闭，无活跃讨论 |
| 新版本发布 | ✅ 正常 | v2026.8.26 补丁更新 |
| Bug 修复 | ✅ 良好 | Agent 相关修复落地，网关重启问题待验证 |
| 测试覆盖 | ✅ 提升 | 新增 75 个单元测试 |

**结论：** LobsterAI 今日以**稳定性修复和体验打磨**为主，无重大功能发布，但 PR 合并效率高、测试覆盖有进步。需关注卸载流程透明度与沙箱模式的用户引导问题。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-08-28

---

## 1. 今日速览

过去24小时 Moltis 项目保持**低活跃度**状态，无新 Issue 产生，亦无新版本发布。PR 活动平稳，共完成 2 项修复类合并，分别涉及沙箱镜像请求验证和 OpenAI 工具 Schema 兼容性。项目整体处于**稳定维护期**，未出现显著的功能推进或社区讨论热潮。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

| PR | 类型 | 作者 | 状态 | 摘要 |
|----|------|------|------|------|
| [#1222](https://github.com/moltis-org/moltis/pull/1222) | fix(web) | tsauvajon | ✅ 已合并 | 校验沙箱镜像请求的引用与包名，限制包检查与镜像构建权限仅保留给操作员管理员，同时保障密码、Passkey 及可信回环身份的管理权限不受影响 |
| [#1232](https://github.com/moltis-org/moltis/pull/1232) | fix(tools) | IlyaBizyaev | ✅ 已合并 | 修复 OpenAI 严格工具 Schema 下对象类型 `additionalProperties=false` 导致 Codex 发送 null/空值的问题；明确 webhook patch 字段语义，将 MCP 环境变量表示为固定 name/value 条目 |

**进展评估**：两项均为安全性与兼容性修复，分别加固了容器镜像构建的安全边界，并解决了与 OpenAI Codex 集成的关键兼容性问题。项目在前一天（08-27）集中处理了已积压的 PR，整体向稳定性方向推进。

---

## 4. 社区热点

过去24小时 **无活跃 Issue 或 PR 讨论**，评论区无新增动态。当前社区参与热度较低，建议关注即将到期的依赖升级或下游集成需求是否将触发新一轮讨论。

---

## 5. Bug 与稳定性

| 问题 | 严重级别 | 描述 | 修复状态 |
|------|----------|------|----------|
| [#1232](https://github.com/moltis-org/moltis/pull/1232) | 🟡 中（兼容性） | OpenAI 严格 Schema 导致 Codex 工具调用返回空值 | ✅ 已修复 |
| [#1222](https://github.com/moltis-org/moltis/pull/1222) | 🟡 中（安全） | 沙箱镜像请求未校验包名和引用，存在潜在越权风险 | ✅ 已修复 |

**稳定性评估**：今日无新增 Bug 报告，两项历史问题均已通过 PR 修复，项目稳定性略有提升。

---

## 6. 功能请求与路线图信号

过去24小时 **无新功能 Issue 或 PR 提交**。#1232 的修复间接反映了用户对 OpenAI / Codex 集成的使用诉求，建议关注后续是否会有更多 AI 工具链兼容性问题浮现。

---

## 7. 用户反馈摘要

今日无新 Issue 评论，**暂无新增用户反馈**。

---

## 8. 待处理积压

基于当前数据，**未发现明确积压项**。两项今日关闭的 PR（#1222、#1232）均已妥善处理。建议维护团队关注：

- 沙箱镜像权限模型的后续使用反馈（#1222 权限收紧可能影响部分用户工作流）
- OpenAI Schema 修复后的集成回归验证（#1232）

---

> **项目健康度评级**：🟡 中等 — 修复活动正常，但缺乏新功能推进与社区讨论，建议关注长期活跃度趋势。

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



# ZeroClaw 项目动态日报
**日期：2026-08-28 | 数据来源：github.com/zeroclaw-labs/zeroclaw**

---

## 1. 今日速览

ZeroClaw 今日保持高活跃度，过去24小时内新增/更新 Issue 23条（21条活跃 + 2条关闭），PR 50条（3条已合并/关闭，47条待审）。整体态势聚焦于 **运行时架构演进**（会话所有权、内部代理主链 RFC 实施）与 **v0.8.5 稳定线冲刺**（截止 2026-08-30）。合并的 PR 覆盖了日志系统、多模态图片验证、风险分类器安全修复三大方向。无新版本发布。

---

## 2. 版本发布

无新版本发布。v0.8.5 稳定线进行中，截止日为 2026-08-30，入流已于 2026-08-04 冻结。详见 #9459。

---

## 3. 项目进展

### 今日已合并/关闭 PR（3条）

**① PR #10214 — 日志条目计数旋转与多段日志查询**
- 作者：NiuBlibing
- 引入 `log_persistence_max_entries_per_segment` 配置键，支持按条目数触发日志旋转，并新增多段日志查询能力，提升可观测性。

**② PR #9819 — 多模态图片像素级验证**
- 作者：NiuBlibing
- 新增 `validate_image_content()`，使用 `image` crate 完整解码图片以验证字节有效性，解决仅靠魔术数字（如 PNG 8字节签名）检测时无法发现的截断/损坏图片导致 provider 请求失败的问题。

**③ PR #8561 — Telegram 多消息流式传输模式**
- 作者：metalmon
- 为 Telegram 通道新增 `multi_message_delay_ms` 配置（默认 800ms），实现 `StreamMode::MultiMessage`，与 Discord/Matrix 保持一致。

### 其他重要待合并 PR
- **PR #9635** — 修复安全分类器中 git 子命令读取逻辑（agent 通过 `git -C <path> <verb>` 调用时，`args.first()` 误读为全局选项而非子命令）
- **PR #10412** — 提取原子会话所有权声明为共享 `SessionBackend` 契约，支持并发调用方安全 claim
- **PR #10425** — RFC #6954 实施第 1/3 部分：`InternalPrincipal` 内部主链信封与 cron 运行结果分离

---

## 4. 社区热点

### 高评论 RFC/Tracker Issues

| Issue | 评论数 | 主题 | 链接 |
|---|---|---|---|
| #9487 | 27 | Runtime-owned conversation sessions & transport adapters | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) |
| #9488 | 21 | Unified attachment architecture for web chat & channels | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) |
| #6954 | 16 | Provenance & reply contract for internally initiated agent turns | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) |
| #8396 | 15 | Wire protocol as first-class in provider construction | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) |
| #8692 | 14 | Maintainer decision queue for RFCs & design issues | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| #9600 | 14 | Session-persistence contract ownership & layer ordering | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) |

**热点分析：** 社区焦点集中在运行时核心架构（会话所有权、传输适配器、附件统一）与贡献流程治理（maintainer 决策队列）。#9487/#9488/#9600 三件 RFC/Tracker 相互关联，指向同一组会话持久化层的设计重构。#6954 已进入实施阶段（PR #10425 已提交），标志 RFC 流程从设计向落地推进。

### 其他活跃 Issue
- #10076（WASM plugin runtime RFC，4评论）— 扩展当前 WASM 组件模型的边界
- #10405（Session-scoped prompt attachments tracker，1评论）— 协调 #9998 的实现批次

---

## 5. Bug 与稳定性

| Issue | 严重度 | 组件 | 状态 | 链接 | Fix PR |
|---|---|---|---|---|---|
| #10329 — Resilient wrapper truncation 遮蔽 context overflow 恢复 | S2 | provider | ✅ 已关闭 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10329) | 已有合并 PR |
| #10063 — Anthropic-backed 兼容网关拒绝 tool results 中的 image_url | S1 | provider | 🔶 开放 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10063) | — |
| #10408 — 同 session 内并行启动导致重复工作 | S2 | runtime/daemon | 🔶 开放 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | — |
| #10324 — cron 手动触发与 run-history 在 agent rename 时存在 check-then-act 竞态 | S2 | runtime/daemon | 🔶 开放 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10324) | — |
| #10237 — Telegram reply-threads 将会话历史碎片化为 per-thread bucket | Medium | channel/telegram | 🔶 开放 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10237) | 关联 PR #8561 |
| #10186 — Terminal fallback 绕过 live delivery 契约 | S2 | runtime/daemon | 🔶 开放 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10186) | — |
| #10286 — ZeroCode 恢复的 transcript 忽略 history trimming 后的已持久化 turns | S2 | zerocode/tui | 🔶 开放 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10286) | — |
| #10326 — Reliable 流式错误报告请求模型而非 pinned 模型 | S3 | provider | 🔶 开放 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/10326) | — |

**重点：** #10063（S1，workflow blocked）和 #10408 影响用户体验较重，尚无合并 fix PR，需关注。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 说明 | 纳入下一版本可能性 |
|---|---|---|---|
| #10419 — 通过 SSE 流式传输 agent-loop tokens | Feature | `POST /webhook` 支持流式响应 | 中（受限于 v0.8.5 截止） |
| #10244 — ZeroCode agent 删除与批量清理 | Feature | 增强 ZeroCode Dashboard 管理能力 | 高（tracker #9459 支持） |
| #10421 — ZeroCode ACP transcript 分页恢复 | Feature | 分页加载持久化 Code/ACP 会话 | 高 |
| #10422 — 将 SOP 配置为 heartbeat | Feature | 确定性 heartbeat 行为 | 低（enhancement，非核心路径） |
| #10076 — Composable WASM plugin runtime | RFC | 扩展 WASM 组件模型边界 | 中长期（架构重构） |

**路线图信号：** v0.8.5 稳定线（#9459）聚焦于运行时契约重构与治理完善。WASM 插件架构（#10076）和 wire protocol 优先化（#8396）为中长期方向，预计 v0.9.x 纳入。

---

## 7. 用户反馈摘要

**痛点：**
- **多模态支持不稳定**：#10063 指出 tool results 中 image_url 被 Anthropic-backed 网关拒绝，影响多模态工作流；#9819 PR 针对损坏图片导致请求失败的问题正在修复。
- **Telegram 通道记忆碎片化**：#10237 反馈 reply-threads 导致会话历史按 thread 分桶，丢失跨 thread 上下文。
- **Session 并发安全问题**：#10408 报告同 session 并发消息触发并行 agent run，产生重复工作与重复回复。
- **日志可读性差**：#10306（已关闭）指出 `web/` 目录 bare `tsc` 打印 75 条误导性错误，PR #10214 通过日志旋转改进可观测性。

**满意度：**
- 用户认可项目对安全策略的精细化（#9753 区分 absent/empty allowed_tools，#9724 确保 always_ask 不被 Full autonomy 静默覆盖）。
- 通道健康检查改进（#10005 基于 channel 而非 listener liveness）解决误报问题。

---

## 8. 待处理积压

| Issue/PR | 问题 | 建议 |
|---|---|---|
| #10063 | S1 bug，无 fix PR | 优先排期，影响多模态可用性 |
| #10408 | S2 bug，并发 session 安全问题 | 高优先级，与 PR #10412 的 SessionBackend 契约相关 |
| #10324 | S2 bug，cron 竞态条件 | 需maintainer review |
| #9487 / #9488 / #9600 | 高评论 RFC/Tracker，相互关联 | 建议协调审议，避免设计冲突 |
| #10076 | RFC，WASM 架构扩展 | 中长期规划，需架构师评估 |

---

**整体健康度评估：** 项目处于 v0.8.5 稳定线冲刺阶段，社区活跃度较高（23 issue + 50 PR/24h），架构 RFC 推进有序，安全与多模态相关 bug 需尽快关注。合并 PR 覆盖可观测性、通道增强、安全修复三个维度，项目整体向前稳步推进。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*