# OpenClaw 生态日报 2026-08-23

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-23 01:46 UTC

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



# OpenClaw 项目动态日报 — 2026-08-23

---

## 1. 今日速览

过去24小时 OpenClaw 保持高活跃度：500 条 Issue 更新、500 条 PR 更新，其中 65 条 PR 已合并/关闭，435 条待合并，整体代码流转速度较快。当前聚焦于 **v2026.8.1-beta.2** 的发布验证（Issue #125626），同时暴露出多个 P0/P1 级别的关键问题，包括 SQLite 数据库 corruption（#126821）、网关事件循环阻塞约100秒（#124788）以及子代理完成消息丢失（#128060）。社区修复意愿强烈，多个高优先级 PR 已进入 maintainer review 阶段。

---

## 2. 版本发布

**无新版本发布。** 当前最新候选版本为 **v2026.8.1-beta.2**，正处于发布验证阶段（#125626）。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（65 条）

| PR | 作者 | 内容概述 |
|---|---|---|
| [#116489](https://github.com/openclaw/openclaw/pull/116489) [CLOSED] | jesse-merhi | **安全增强**：安装策略警告需人工确认，CLI 和 Control UI 均支持 `acknowledgeInstallPolicyWarning` |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) [CLOSED] | jesse-merhi | **UI 安全审查**：Control UI 中增加安装策略警告的交互式确认流程 |
| [#125471](https://github.com/openclaw/openclaw/pull/125471) [CLOSED] | VACInc | **修复 Claude CLI OAuth**：解决 Gateway 重启后 OAuth refresh token 所有权丢失导致认证失效的问题 |
| [#128070](https://github.com/openclaw/openclaw/pull/128070) [CLOSED] | clawsweeper | **UI 微调**：侧边栏折叠后不再显示多余的展开 tooltip |

### 重点进行中的 PR

| PR | 作者 | 优先级 | 内容 |
|---|---|---|---|
| [#128060](https://github.com/openclaw/openclaw/pull/128060) | alexeysophia | P1 🦐 gold | **修复子代理完成消息丢失**：OpenAI-compatible HTTP session 中 subagent 结果静默丢失（关联 #128003） |
| [#123189](https://github.com/openclaw/openclaw/pull/123189) | SunnyShu0925 | P1 🦐 gold | **修复 Chat 启动时 run 恢复**：Control UI 无法还原正在执行的通道 run（关联 #121756） |
| [#119525](https://github.com/openclaw/openclaw/pull/119525) | momothemage | P1 🦪 silver | **memory_search 超时后允许重试**：解决搜索超时后 provider cooldown 误阻塞问题 |
| [#127881](https://github.com/openclaw/openclaw/pull/127881) | vyctorbrzezowski | P1 | **UI 优化**：首连解析期间预渲染已存储的对话，减少 p50 延迟 3,284ms |
| [#126424](https://github.com/openclaw/openclaw/pull/126424) [CLOSED] | joshavant | P1 🐚 platinum | **修复多 Agent 会话路由**：保持会话投递在 agent binding 内（跨 Discord/iMessage/Slack/Telegram 等） |
| [#121576](https://github.com/openclaw/openclaw/pull/121576) | ruel225 | P2 🦐 gold | **修复 token 剥离插入多余空格**：影响全部 30+ 渠道 |

> **整体判断**：今日 65 条 PR 已合并/关闭，覆盖安全、认证、多 Agent 路由、UI 体验等关键领域，项目修复节奏健康。多个 P1 级 PR 处于 `needs proof` 或 `waiting on author` 状态，是近期合并的关键阻塞点。

---

## 4. 社区热点

### 讨论最活跃的 Issue（按评论数排序）

| Issue | 评论数 | 优先级 | 摘要 | 链接 |
|---|---|---|---|---|
| [#125626](https://github.com/openclaw/openclaw/issues/125626) | 19 | P2 | **v2026.8.1-beta.2 发布验证**，组织测试者升级网关并完成工作表验证 | [链接](https://github.com/openclaw/openclaw/issues/125626) |
| [#68596](https://github.com/openclaw/openclaw/issues/68596) | 15 | P2 🔸8👍 | **流式 watchdog 超时阈值可配置化**，extended reasoning 模型（Kimi-K2.5、DeepSeek-R1）频繁触发误告警 | [链接](https://github.com/openclaw/openclaw/issues/68596) |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | 14 | P1 🐚 platinum | **WhatsApp 1:1 图片消息导致主通道阻塞约3分钟**，多模态注入机制存在问题 | [链接](https://github.com/openclaw/openclaw/issues/96834) |
| [#51429](https://github.com/openclaw/openclaw/issues/51429) | 12 | P2 🦞 diamond | **工作路径被 hardcode 进代码并随版本发布**（`/Users/wangtao`），引发社区关注 | [链接](https://github.com/openclaw/openclaw/issues/51429) |
| [#85030](https://github.com/openclaw/openclaw/issues/85030) | 12 | P1 🐚 platinum 🔸6👍 | **MCP tools 未注入 subagent sessions**，`bundle-mcp` 及各类 allowlist 配置均失效 | [链接](https://github.com/openclaw/openclaw/issues/85030) |

### 社区热点分析

- **beta.2 验证社区参与度高**：#125626 以工作表形式组织测试，体现项目发布了较规范的验证流程。
- **MCP + subagent 问题是高频痛点**：#85030 和 #67777 均指向 subagent 机制的稳定性缺陷，且已被多个用户复现。
- **硬编码路径事件**：#51429 虽为 P2 级别，但反映出代码审查流程的疏漏，社区反应强烈（12条评论）。

---

## 5. Bug 与稳定性

### P0 级问题

| Issue | 标题 | 状态 | 已有 Fix PR | 链接 |
|---|---|---|---|---|
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite corruption 在重建后15-24h内复发，WSL2 环境出现5次，含"瘫痪网关"模式 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/126821) |
| [#124788](https://github.com/openclaw/openclaw/issues/124788) | beta.2 网关事件循环每 ~10min 阻塞约100s（字符串构建 + fs scan），所有 memory 插件禁用仍存在 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/124788) |

### P1 级问题

| Issue | 标题 | 状态 | 已有 Fix PR | 链接 |
|---|---|---|---|---|
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 子进程泄漏导致 zombie 累积，运行时性能退化 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| [#45224](https://github.com/openclaw/openclaw/issues/45224) | Playwright CDP assertion error 未捕获导致 Gateway 崩溃 | OPEN | ✅ [#126618](https://github.com/openclaw/openclaw/pull/126618) 部分相关 | [链接](https://github.com/openclaw/openclaw/issues/45224) |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | subagent 完成投递在超时/drains/orphan prune 时丢失 | OPEN | ✅ [#128060](https://github.com/openclaw/openclaw/pull/128060) | [链接](https://github.com/openclaw/openclaw/issues/67777) |
| [#85030](https://github.com/openclaw/openclaw/issues/85030) | MCP tools 未注入 subagent sessions | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/85030) |
| [#124284](https://github.com/openclaw/openclaw/issues/124284) | v2026.8.1-beta.2 引入的 vLLM + thinking 模式 XML 工具调用畸形 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/124284) |
| [#113701](https://github.com/openclaw/openclaw/issues/113701) | 大 tool output 超出 context window，compaction 无法恢复，session 进入失败循环 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/113701) |
| [#126707](https://github.com/openclaw/openclaw/issues/126707) | 原生 Codex compaction 在同一 turn 中重复发送成功消息 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/126707) |
| [#126906](https://github.com/openclaw/openclaw/issues/126906) | 拒绝 write tool 会静默禁用 memory 持久化，agent 仍报告成功 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/126906) |
| [#49381](https://github.com/openclaw/openclaw/issues/49381) | Feishu 模型 failover 后出现重复最终回复 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/49381) |
| [#127728](https://github.com/openclaw/openclaw/issues/127728) | 远程扩展配对在 relay 启动后 ~10ms 被网关拒绝 | OPEN | ❌ 暂无 | [链接](https://github.com/openclaw/openclaw/issues/127728) |

### 稳定性评估

> **健康度：需关注**。两个 P0 问题（SQLite corruption、事件循环周期性阻塞）直接影响网关可用性，且均无对应 fix PR。beta.2 版本暴露了多个回归问题（#124284、#126707），建议发布团队在正式版前解决。子代理相关缺陷（#67777、#85030、#78055）形成一条明显的稳定性弱链。

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 社区支持 | 关联 PR | 链接 |
|---|---|---|---|---|
| [#68596](https://github.com/openclaw/openclaw/issues/68596) | 可配置 streaming watchdog 超时阈值 | 🔸8👍 | — | [链接](https://github.com/openclaw/openclaw/issues/68596) |
| [#57425](https://github.com/openclaw/openclaw/issues/57425) | 优雅网关重启 + Session 恢复机制 | 🔸1👍 | — | [链接](https://github.com/openclaw/openclaw/issues/57425) |
| [#75947](https://github.com/openclaw/openclaw/issues/75947) | 基于 UX 评分的 UI 重新设计 | 🔸2👍 | [#127793](https://github.com/openclaw/openclaw/pull/127793)（视觉层级简化） | [链接](https://github.com/openclaw/openclaw/issues/75947) |
| [#33102](https://github.com/openclaw/openclaw/issues/33102) | TUI `--deliver` 标志的配置文件默认值支持 | 🔸1👍 | — | [链接](https://github.com/openclaw/openclaw/issues/33102) |

**路线图判断**：
- **#68596（watchdog 超时可配置）** 支持度高（8👍），且与 extended reasoning 模型普及趋势一致，纳入下一版本概率较高。
- **#57425（优雅重启+Session恢复）** 是架构级需求，#57425 已存在较久，短期内完整实现可能性低，但可作为中长期路线图目标。
- **#75947（UI redesign）** 已有渐进式改进 PR（#127793 Sessions 页面视觉简化），预计会以迭代方式推进。

---

## 7. 用户反馈摘要

### 主要痛点

1. **beta.2 稳定性问题集中爆发**
   - 事件循环周期性阻塞100s（#124788）
   - vLLM + thinking 模式工具调用畸形（#124284）
   - SQLite corruption 复发（#126821）
   - 用户反馈："paralyzed gateway mode"——网关拒绝所有服务但不退出

2. **subagent 机制可靠性不足**
   - 完成消息丢失（#67777、#78055）
   - MCP tools 未注入（#85030）
   -  stale 结果投递（#78055）
   - 用户评论反映 subagent 是"看起来能工作，但关键时刻丢消息"的典型问题

3. **认证/授权相关摩擦**
   - Codex OAuth refresh 超时（#89278）
   - CLI auth epoch 翻转导致所有 live session 失效（#80178）
   - Claude CLI OAuth 重启后丢失（#125471，已有 fix）
   - 模型选择器仅对新 session 生效（#124689）

4. **工具执行平台差异**
   - Windows 上 `exec`/`read` 静默返回空输出（#105528）
   - Talk JPEG 图片60s超时（#83416）
   - ACP sessions_spawn 产生0字节 transcript（#95759）

### 正面反馈
- Control UI 的 Sessions 页面视觉简化（#127793）获得认可
- 安全策略安装确认功能（#116489、#120900）受到安全敏感用户欢迎
- memory_search 超时重试修复（#119525）解决了长期使用中的阻塞问题

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 天数未动 | 优先级 | 问题描述

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-08-23**

---

## 1. 生态全景

2026年8月，个人AI助手与自主智能体开源生态呈现**高活跃、强分化、安全导向**三大特征。头部项目（OpenClaw、Hermes Agent、NanoClaw）日处理PR超20条，社区贡献密集；中坚力量（IronClaw、NanoBot、Moltis）以稳定性修复和功能打磨为主；部分项目（NullClaw、ZeptoClaw）处于沉寂期。生态整体从"功能堆砌"转向"可靠性与安全治理"，MCP集成、网关认证、子代理机制、多通道适配成为共同痛点，技术路线在通用网关架构与垂直场景定制之间形成明显分层。

---

## 2. 各项目活跃度对比

| 项目 | Issues（24h） | PRs（24h） | 已合并 | Release | 健康度 |
|------|--------------|-----------|--------|---------|--------|
| **OpenClaw** | 500 | 500 | 65 | v2026.8.1-beta.2（验证中） | 🟡 需关注（2个P0问题无修复） |
| **Hermes Agent** | 50 | 50 | 4 | 无 | 🟢 良好（安全修复集中） |
| **NanoClaw** | 1 | 26 | 8 | 无 | 🟢 良好（多通道集成稳定） |
| **IronClaw** | 9 | 21 | 5 | 无 | 🟢 良好（CI+子代理并行） |
| **NanoBot** | 0 | 19 | 5 | 无 | 🟢 良好（WebUI可观测性提升） |
| **LobsterAI** | 2 | 6 | 5 | 无 | 🟢 良好（7.5/10，修复效率高） |
| **Moltis** | 1 | 3 | 1 | 无 | 🟢 良好（安全Hook+兼容性） |
| **CoPaw** | 7 | 4 | 0 | 无 | 🟡 中等（积压PR待审） |
| **PicoClaw** | 2 | 6 | 4 | 无 | 🟡 中等（MCP阻塞关键） |
| **ZeroClaw** | 50 | 50 | 7 | 无 | 🟢 良好（v0.9.0安全重构） |
| **NullClaw** | 0 | 0 | 0 | 无 | 🔴 无活动 |
| **ZeptoClaw** | 0 | 0 | 0 | 无 | 🔴 无活动 |

---

## 3. OpenClaw 在生态中的定位

**优势：**
- **社区规模断层领先**：日处理500+ Issue/PR，是第二名Hermes Agent的10倍，体现最强的生态吸引力
- **多通道集成最广**：支持Discord/iMessage/Slack/Telegram/WhatsApp等30+渠道，是最成熟的"网关型"智能体平台
- **发布节奏最规范**：beta验证流程（工作表组织测试）体现企业级项目管理能力

**技术路线差异：**
| 维度 | OpenClaw | 同类项目 |
|------|----------|----------|
| 架构 | 网关中心+多Agent路由 | Hermes/ZeroClaw：进程模型；NanoBot：Provider抽象 |
| 部署 | WSL2/Linux/macOS全栈 | LobsterAI：Web优先；CoPaw：Qwen生态绑定 |
| 扩展 | MCP+bundles+subagent | Moltis：WASM插件；IronClaw：AfterTurn钩子 |

**差距：** P0级稳定性问题（SQLite corruption、事件循环阻塞）反映超大规模项目的技术债务风险，需警惕"功能先行、稳定滞后"的模式。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **MCP集成稳定性** | OpenClaw、Hermes、PicoClaw、Moltis、NanoClaw | 连接失败不阻塞agent loop、凭据变更后重连、工具错误不触发熔断 |
| **子代理机制** | OpenClaw、IronClaw、NanoBot | 完成消息丢失、超时/drains场景可靠性、MCP工具注入 |
| **网关/会话生命周期** | OpenClaw、Hermes、ZeroClaw、CoPaw | 优雅重启、Session恢复、跨设备同步、运行时所有权 |
| **多通道适配** | OpenClaw、NanoClaw、Hermes、LobsterAI | Telegram/Slack/Discord身份识别、审批门禁、重复消息抑制 |
| **安全与认证** | Hermes、ZeroClaw、Moltis、OpenClaw | PKCE/OAuth token管理、安全Hook fail-closed、高风险命令拦截 |
| **可观测性** | NanoBot、IronClaw、ZeroClaw | token用量透明、轮次延迟指标、网关健康状态暴露 |
| **长上下文/长会话** | OpenClaw、Hermes、IronClaw | 压缩机制、token成本优化、500k+会话恢复 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 多通道网关+多Agent路由 | 企业/个人全场景用户 | 网关中心架构，subagent依赖central dispatch |
| **Hermes Agent** | 桌面端+安全控制+Skills Hub | 技术用户、安全敏感群体 | Electron桌面壳，fleet-update机制（被诟病为spaghetti） |
| **NanoClaw** | 多Bot部署+容器化 | 多通道运维者、K8s用户 | 电路断路器实例隔离、Bun运行时优化 |
| **IronClaw** | 沙箱+工具合约重构 | 研究/实验型用户 | AfterTurn钩子、Pi-style compaction、通用凭证broker |
| **NanoBot** | WebUI可观测性+Provider抽象 | 开发者、调试需求强 | 统一轮次观测、Provider类型契约 |
| **ZeroClaw** | 安全重构+SOP控制面 | 高阶用户、架构探索者 | WASM插件化、SOP只读视图、运行时会话所有权 |
| **Moltis** | 安全Hook+跨平台兼容 | 企业集成场景 | fail-closed策略、OpenAI strict schema兼容 |
| **LobsterAI** | Web搜索+Cowork协作 | 中文用户、知识工作者 | Chrome自动化、Markdown导出、模型ID解析 |
| **CoPaw** | Qwen生态+定时任务 | 阿里通义用户 | Chrome LAN桥接、Cron模型覆盖、UTF-8编码适配 |
| **PicoClaw** | 嵌入式/MCP调试 | 边缘计算、Skill开发者 | skill安装重构、cron循环修复 |

---

## 6. 社区热度与成熟度

```
活跃度分层：

🔥 高活跃（日PR > 20）
   ├── OpenClaw (500 PRs) — 规模领先，但P0问题暴露成熟期阵痛
   ├── Hermes Agent (50 PRs) — 安全修复密集，处于质量巩固期
   └── ZeroClaw (50 PRs) — RFC驱动架构演进，v0.9.0攻坚中

⚡ 中活跃（日PR 5-20）
   ├── NanoClaw (26 PRs) — 多通道集成成熟，容器化部署领先
   ├── IronClaw (21 PRs) — CI优化+子代理并行，技术债清理中
   ├── NanoBot (19 PRs) — WebUI可观测性里程碑，Provider重构
   └── LobsterAI (6 PRs) — 修复效率高，功能闭环快

📊 低活跃（日PR < 5）
   ├── Moltis (3 PRs) — 安全Hook落地，小而精
   └── PicoClaw (6 PRs) — MCP阻塞修复关键，维护人力紧张

💤 沉寂
   ├── NullClaw — 无活动
   └── ZeptoClaw — 无活动
```

**成熟度判断：**
- **快速迭代期**：OpenClaw（功能扩展快于稳定性）、ZeroClaw（架构重构期）
- **质量巩固期**：Hermes（安全修复集中）、NanoClaw（多通道稳定化）、IronClaw（技术债清理）
- **垂直深耕期**：LobsterAI（中文生态）、CoPaw（Qwen绑定）、Moltis（企业兼容）

---

## 7. 值得关注的趋势信号

### 趋势一：MCP从"锦上添花"变为"稳定性瓶颈"
**信号**：OpenClaw (#85030 #67777)、Hermes (#79645 #79298)、PicoClaw (#3269)、Moltis (#1231) 均聚焦MCP连接/错误处理
**启示**：MCP已成为智能体平台的核心依赖，但其稳定性尚未成熟。开发者应关注连接生命周期管理、错误隔离机制，避免单点故障级联。

### 趋势二：安全边界从"功能开关"转向"架构内生"
**信号**：Hermes (#92551 审批绕过)、Moltis (#1230 fail-closed)、ZeroClaw (#9203 SOP认证)、NanoClaw (#3446 Bot门控)
**启示**：安全不再依赖单一控制点，而是嵌入网关认证、Hook策略、命令拦截多层防线。"默认拒绝"（fail-closed）成为新标准。

### 趋势三：子代理从"实验特性"走向"生产可靠性的试金石"
**信号**：OpenClaw (#67777 #85030) 的完成消息丢失、Hermes 的长会话死亡 (#78981)、IronClaw 的后台子代理 (#7818)
**启示**：子代理机制的可靠性是区分"玩具"与"生产工具"的关键指标。消息丢失、超时处理、上下文压缩是三大技术挑战。

### 趋势四：可观测性成为WebUI竞争焦点
**信号**：NanoBot (#5486 统一轮次观测)、IronClaw (#7824 token成本)、ZeroClaw (#9694 SOP面板)
**启示**：用户不再满足于"能跑"，而是需要"看得清"。token用量、延迟分布、会话状态成为产品差异化要素。

### 趋势五：跨平台/容器化部署从"支持"变为"刚需"
**信号**：NanoClaw (#3318 Bun AVX2兼容)、Hermes (#92095 .desktop Exec路径)、ZeroClaw (#9291 AppImage检测)、NanoBot (#5485 LangSmith tracing)
**启示**：部署复杂性是用户流失的主因。容器镜像兼容性、跨平台测试矩阵、自动检测机制成为基础设施层的关键能力。

---

**总结**：2026年8月的开源智能体生态正从"功能竞赛"转向"可靠性竞赛"。OpenClaw以规模领先但需解决P0稳定性；Hermes/ZeroClaw以安全架构见长；NanoClaw/IronClaw在多通道与可观测性上形成差异化；LobsterAI/CoPaw深耕垂直场景。对开发者而言，MCP集成、子代理可靠性、安全内生设计是近期最值得投入的技术方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目日报 — 2026-08-23

## 1. 今日速览

过去24小时 NanoBot 共处理 **19 条 PR**（14 条待合并、5 条已合并/关闭），无新 Issues 提交，无新版本发布。项目活跃度中等，PR 合并节奏稳定，今日工作集中在 **WebUI 可观测性提升** 和 **Provider 层重构** 两大方向。5 条合并的 PR 均为维护性工作，包含功能修复、文档更新和配置增强，项目整体处于稳步迭代状态。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭 **5 条 PR**，主要推进方向如下：

- **#5486** [CLOSED] feat(webui): unify turn observability — 统一用户轮次观测，将推理、工具调用、文件编辑等中间片段映射到单一答案表面，保留用户展开/折叠状态，并报告准确的 per-turn 输入输出 token 和延迟指标。这是 WebUI 可观测性的重要里程碑。
- **#3869** [CLOSED] fix(providers): DeepSeek message hardening — 修复 DeepSeek 模型因 `null` content 返回 400 错误及 `"(empty)"` 占位符泄漏的兼容性问题，显著提升 DeepSeek 用户稳定性。
- **#4430** [CLOSED] feat(web): configure web_fetch provider — 新增可配置的 `web_fetch` provider（支持 `auto`、`tavily`、`jina`、`readability` 四种模式），替代原有的 `useJinaReader` 开关，增强 Web 抓取灵活性。
- **#3294** [CLOSED] feat(dream): optional kill switch + custom Phase 1/2 template paths — 为 Dream 自学习循环增加 Kill Switch 和自定义模板路径配置，避免每次升级都需要 fork 模板。
- **#5488** [CLOSED] docs: refresh team and contributor credits — 更新维护者展示和贡献者墙，移除机器人账号，增强社区可视化。

> 整体判断：今日合并以**维护性修复和文档/配置增强**为主，核心功能开发（如 WebUI 观测性统一、Provider 重构）已进入待合并状态，下一批次合并预计带来显著功能提升。

---

## 4. 社区热点

今日无活跃 Issues，PR 讨论热度分析如下：

| PR | 类型 | 热度分析 |
|---|---|---|
| [#5486](https://github.com/HKUDS/nanobot/pull/5486) | WebUI 可观测性 | 高价值：统一轮次观测是用户长期诉求，直接影响排查体验 |
| [#5480](https://github.com/HKUDS/nanobot/pull/5480) | Provider 类型重构 | 高影响力：为上游 provider usage 报告建立统一契约，是后续功能的基础 |
| [#5420](https://github.com/HKUDS/nanobot/pull/5420) | 用户可控轮次恢复 | 高关注：WebSocket 中断恢复是稳定性关键路径，用户反馈较多 |
| [#5483](https://github.com/HKUDS/nanobot/pull/5483) | 已删除会话防止重建 | 中关注：修复了延迟消息导致会话被意外恢复的竞态问题 |
| [#5408](https://github.com/HKUDS/nanobot/pull/5408) | 后续建议功能 | 中关注：参考 DeerFlow 交互模式的后续问题建议，提升对话体验 |

---

## 5. Bug 与稳定性

今日无新 Issues 提交。现有待合并的高优先级 Bug/回归 PR：

| PR | 严重级别 | 问题描述 | 状态 |
|---|---|---|---|
| [#5485](https://github.com/HKUDS/nanobot/pull/5485) | P2 / 回归 | LiteLLM → 原生 SDK 迁移后 LangSmith tracing 失效 | 待合并 |
| [#5483](https://github.com/HKUDS/nanobot/pull/5483) | P2 / 回归 | 已删除会话被延迟跨会话消息意外重建 | 待合并 |
| [#5484](https://github.com/HKUDS/nanobot/pull/5484) | P2 | MCP 服务端返回 `isError=false` 的业务错误信封被误判为成功 | 待合并 |
| [#5491](https://github.com/HKUDS/nanobot/pull/5491) | P2 | WebUI 推理 shell 内答案文本展示异常，需要剥离保留 | 待合并 |
| [#5490](https://github.com/HKUDS/nanobot/pull/5490) | P2 / 回归 | 聚合轮次 token 用量显示不清晰，缺少上下文容量信息 | 待合并 |
| [#5469](https://github.com/HKUDS/nanobot/pull/5469) | P2 | TUI 页脚未展示实际测量上下文，显示累积值误导用户 | 待合并 |
| [#5471](https://github.com/HKUDS/nanobot/pull/5471) | 普通 | `ephemeral=True` SDK 运行时意外改变了会话状态 | 待合并 |

> **风险评估**：`#5485`（LangSmith tracing 回归）和 `#5483`（会话重建竞态）建议优先合并，均影响生产环境可追踪性和数据一致性。

---

## 6. 功能请求与路线图信号

| PR | 功能方向 | 路线图判断 |
|---|---|---|
| [#5408](https://github.com/HKUDS/nanobot/pull/5408) | WebUI 后续建议生成（参考 DeerFlow） | 高概率纳入下一版本，提升对话 UX |
| [#5367](https://github.com/HKUDS/nanobot/pull/5367) | Agent 活动标签多语言本地化（10 种 locale） | 已就绪， likely 随 WebUI 更新一同发布 |
| [#5420](https://github.com/HKUDS/nanobot/pull/5420) | 用户可控轮次恢复（Continue/Dismiss） | 核心稳定性功能，应优先合并 |
| [#5487](https://github.com/HKUDS/nanobot/pull/5487) | 文件预览修复 + 子代理生命周期回放 | 增强功能，与 #5486 可协同发布 |
| [#5481](https://github.com/HKUDS/nanobot/pull/5481) | 统一 Provider 用量后端（轨迹记录） | 基础设施层重构，是 #5480 的上游依赖 |
| [#5489](https://github.com/HKUDS/nanobot/pull/5489) | 邮件频道性能优化（先取 headers，跳过重复 fetch） | 性能优化，已就绪 |

> **综合判断**：下一版本核心主题预计为 **"WebUI 可观测性统一 + Provider 类型化重构"**，`#5486`、`#5480`、`#5481` 构成主线；`#5420`（轮次恢复）和 `#5408`（后续建议）为体验增强项。

---

## 7. 用户反馈摘要

无新 Issues 提交，但从待合并 PR 描述中可提炼以下用户痛点：

- **Token 用量不透明**：用户难以区分"累积输入"与"单次请求上下文"，导致成本估算偏差 → 由 `#5490`、`#5469`、`#5486` 系列 PR 解决。
- **DeepSeek 兼容性**：`null` content 和占位符泄漏导致 400 错误，影响中文用户群体 → 已由 `#3869` 修复。
- **LangSmith 追踪丢失**：LiteLLM 迁移后 tracing 失效，影响生产链路追踪 → `#5485` 待合并。
- **MCP 错误误判**：部分 MCP 服务端将业务错误封装在成功响应中，nanobot 未能正确识别 → `#5484` 修复中。
- **Ephemeral 运行时状态污染**：SDK 用户期望临时运行不影响会话，但旧实现存在状态泄漏 → `#5471` 修复。

---

## 8. 待处理积压

| PR | 创建时间 | 状态 | 关注点 |
|---|---|---|---|
| [#5367](https://github.com/HKUDS/nanobot/pull/5367) | 2026-08-13 | OPEN（冲突） | 本地化功能已就绪但存在冲突，需维护者介入 |
| [#5408](https://github.com/HKUDS/nanobot/pull/5408) | 2026-08-17 | OPEN（冲突） | 后续建议功能，等待依赖合并后解决冲突 |
| [#5420](https://github.com/HKUDS/nanobot/pull/5420) | 2026-08-18 | OPEN | 轮次恢复，无冲突但待审核，建议优先 |
| [#5469](https://github.com/HKUDS/nanobot/pull/5469) | 2026-08-21 | OPEN（冲突） | TUI 上下文显示修复，等待上游合并 |
| [#5487](https://github.com/HKUDS/nanobot/pull/5487) | 2026-08-22 | OPEN（冲突） | 文件预览修复，与 #5486 存在冲突依赖 |

> **维护者建议**：`#5367` 和 `#5408` 已开放超 5 天，`#5420` 为稳定性关键路径，建议优先 review 合并。冲突 PR 可考虑与 `#5486`、`#5480` 的合并顺序协调处理。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-08-23 | 数据周期：过去 24 小时**

---

## 1. 今日速览

今日 Hermes Agent 项目保持高度活跃：过去 24 小时内共更新 **50 条 Issues**（新开/活跃 48，关闭 2）和 **50 条 PR**（待合并 46，已合并/关闭 4），无新版本发布。当日工作重心集中在两处：一是 MCP 工具错误与传输熔断器的分离修复（2 个相关 PR 被关闭，可能已合并），二是大量新提交的 P2 级别兼容性与 Windows 平台回归问题。整体健康度良好，社区贡献活跃，但桌面端、网关稳定性和认证安全方向存在集中式风险暴露。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 状态 | 摘要 |
|---|---|---|
| [#79645](https://github.com/NousResearch/hermes-agent/issues/79645) | CLOSED | **fix(mcp): 将工具错误与服务器熔断器分离** — 修复了 `CallToolResult.isError` 累积导致整个 MCP 服务器被熔断的错误，无效参数或资源缺失不再误杀健康传输。 |
| [#79298](https://github.com/NousResearch/hermes-agent/issues/79298) | CLOSED | **fix(mcp): 工具级错误独立于传输熔断器** — 与 #79645 配合，确保 `tools/call` RPC 完成后重置服务器健康状态，区分会话缺失和传输异常的处理路径。 |
| [#40391](https://github.com/NousResearch/hermes-agent/issues/40391) | CLOSED (Issue) | **修复 Desktop 远程网关 WebSocket 回落问题** — 修复了 macOS Desktop 远程模式下 WebSocket 连接失败后静默回退本地后端的问题。 |
| [#92551](https://github.com/NousResearch/hermes-agent/issues/92551) | CLOSED (Issue) | **computer_use 审批门禁在所有网关表面均被绕过**（标记为重复）— 当未注册 CLI 审批回调时，`_request_approval` 错误地返回已批准，涉及 Telegram/Discord/Slack/api_server 全部网关。 |

**推进评估：** 本日合并以 MCP 稳定性和安全边界修复为主，解决了一个长期存在的误熔断问题，对多工具 MCP 场景有显著正向影响。Windows 安装更新和 venv 路径问题也有 PR（#92617、#92090）待合并。

---

## 4. 社区热点

### 讨论最活跃的 Issues（按评论数）

**🔥 #66616 — Skills 索引陈旧/降级（78 条评论）**
> Skills Hub 依赖的 unified index 超过 26h 限制（当前 29.8h），自动化探针标记 `degraded`。cron 调度或构建流水线可能存在异常。长期未解决，社区关注度最高。
> 🔗 https://github.com/NousResearch/hermes-agent/issues/66616

**🔥 #84834 — Webhook Feature Package 元 Issue（22 条评论）**
> 全面修复 Hermes webhook 表面（入口、执行、投递、配置、管理 UI、部署、文档），以 graph-gated 5×2×3 方式推进。作为追踪元 Issue 汇总多个子问题。
> 🔗 https://github.com/NousResearch/hermes-agent/issues/84834

**🔥 #91277 — 舰队更新可靠性追踪（14 条评论）**
> 维护者 teknium1 指出：当前更新机制是"每个平台分别编写的 imperatice spaghetti"，~30 个开放 Issues 和 ~15 个 PR 各自修补同一类问题，亟需统一方案。
> 🔗 https://github.com/NousResearch/hermes-agent/issues/91277

**🔥 #78981 — DeepSeek 500k token 会话永久死亡（8 条评论）**
> 长会话（132 tool turns）在 DeepSeek 上经历上下文压缩 hang 后永久挂死，600s 超时 ceiling 触发后中断轮次无法恢复。
> 🔗 https://github.com/NousResearch/hermes-agent/issues/78981

### 社区热点分析

- **多设备会话同步**（#74816，2👍）受到关注，用户期望"类似微信"的跨端实时会话体验，当前会话文件绑定单一设备是核心痛点。
- **网关控制 Socket 设计**（#92091）指向 fleet-update 所有 Bug 的根因：网关缺乏"自有控制面"，各进程通过扫描进程表发现和管理网关，是架构级问题。

---

## 5. Bug 与稳定性

### P1 问题

| Issue | 描述 | Fix PR |
|---|---|---|
| [#78981](https://github.com/NousResearch/hermes-agent/issues/78981) | DeepSeek 500k token 会话经压缩 hang 后永久死亡，600s 超时后被中断的 turn 无法恢复 | 无 |
| [#92302](https://github.com/NousResearch/hermes-agent/issues/92302) | `.env` 变量 `HERMES_STREAM_STALE_TIMEOUT` 改名后，120s 超时对本地模型+大上下文过短，导致连接断开警告 | 无（需配置调整） |

### P2 问题（高优先级）

| Issue | 描述 | Fix PR |
|---|---|---|
| [#92095](https://github.com/NousResearch/hermes-agent/issues/92095) | Linux uv-based 安装下 `.desktop` Exec= 指向裸 uv interpreter 而非项目 venv python，图标点击静默失败 | [#92090](https://github.com/NousResearch/hermes-agent/pull/92090)（待合并） |
| [#92271](https://github.com/NousResearch/hermes-agent/issues/92271) | Windows Docker 沙箱 session 目录名含 `:` 导致 WinError 267，所有 tool call 失败 | 无 |
| [#58593](https://github.com/NousResearch/hermes-agent/issues/58593) | Linux Desktop 内建更新反复失败且重置 Electron sandbox 权限 | 无 |
| [#92606](https://github.com/NousResearch/hermes-agent/issues/92606) | Anthropic OAuth PKCE 流程中陈旧 credential 覆盖旋转后的 token，两个 pool 行共享 single-use refresh token 导致 401 revoked | 无 |
| [#92553](https://github.com/NousResearch/hermes-agent/issues/92553) | `pre_tool_call` shell hook 返回的 `"approve"` action 被解析为 None，hook 静默失效但 `hermes hooks doctor` 显示健康 | 无 |
| [#91980](https://github.com/NousResearch/hermes-agent/issues/91980) | 审批 prompt 在断开连接的 client transport 上发出后超时静默，无日志、无重试、无 fallback | [#55506](https://github.com/NousResearch/hermes-agent/pull/55506)（待合并） |
| [#83832](https://github.com/NousResearch/hermes-agent/issues/83832) | PKCE state cookie 以字面 `;` 序列化，违反 RFC 6265，导致 OIDC 登录失败 | 无 |
| [#92506](https://github.com/NousResearch/hermes-agent/issues/92506) | `profiles.list` JSON-RPC 永远无响应——`WSTransport.write` 因 profile.yaml 中 datetime 不可序列化而静默杀死 pool worker | 无 |
| [#92565](https://github.com/NousResearch/hermes-agent/issues/92565) | MCP server 凭据变更后不会重连，sessions 仅按名称复用，导致认证失效 | 无 |
| [#92554](https://github.com/NousResearch/hermes-agent/issues/92554) | `hermes config set` 写入时销毁所有用户注释，默认注释块被覆盖 | 无 |
| [#84599](https://github.com/NousResearch/hermes-agent/issues/84599) | SSH 后端在非默认 profile 的 desktop-remote 会话中，idle 清理后静默回退到 local | 无 |

### 安全类 Bug

| Issue | 描述 | Fix PR |
|---|---|---|
| [#92551](https://github.com/NousResearch/hermes-agent/issues/92551) | `computer_use` 审批门禁在所有网关表面均被绕过（已关闭为重复） | — |
| [#92449](https://github.com/NousResearch/hermes-agent/pull/92449) | PR：为 file toolset 添加 profile-local 文件系统边界 | 待合并 |

---

## 6. 功能请求与路线图信号

| Issue | 诉求 | 路线图判断 |
|---|---|---|
| [#74816](https://github.com/NousResearch/hermes-agent/issues/74816) | 多设备会话实时同步（类微信体验） | 愿景型需求，当前架构为单设备会话文件，需网关层重构，短期难实现 |
| [#92087](https://github.com/NousResearch/hermes-agent/issues/92087) | 暴露 Discord adapter 实时健康状态，与持久化 gateway state 分离 | 可纳入近期版本，运维可观测性需求明确 |
| [#69203](https://github.com/NousResearch/hermes-agent/issues/69203) | Discord 适配器缺少出站 @Name → <@id> mention 解析（Feishu 已有） | 平台适配缺口，修复成本低，可能纳入下一版本 |
| [#92568](https://github.com/NousResearch/hermes-agent/issues/92568) | Azure Foundry 原生跨进程 token 准入、重试与隐私安全 rate-limit receipts | 企业用户诉求，依赖上游 ClarityWeb 仓库进展 |
| [#91277](https://github.com/NousResearch/hermes-agent/issues/91277) | 统一舰队更新方案（本地/多 profile/远程/image-managed） | 架构级重构，维护者已明确标注为 P1 追踪项 |

---

## 7. 用户反馈摘要

- **痛点 1：更新机制极不可靠。** 用户反复遭遇 Windows venv 更新卡死（#92617）、Linux 更新反复失败（#58593）、.desktop 入口 Exec 路径错误（#92095）。多个用户和 maintainer 均指出这是"platform spaghetti"。
- **痛点 2：长会话稳定性差。** DeepSeek 500k token 会话经压缩 hang 后永久死亡（#78981），以及 120s 超时对本地大模型过短（#92302），反映长上下文场景的超时策略需要参数化。
- **痛点 3：网关状态不可观测。** Discord 等适配器连接健康但无实时状态暴露（#92087），审批请求在客户端断开后静默丢失（#91980）。
- **痛点 4：安全边界缺陷集中爆发。** PKCE cookie 序列化 bug（#83832）、MCP 凭据变更后不重连（#92565）、computer_use 审批绕过（#92551）、Anthropic OAuth token 互斥吊销（#92606）—— 4 个独立安全/认证 Bug 集中在同一日提交，提示近期 PR 可能引入了回归。
- **满意点：** MCP 工具错误不再误杀整个服务器（#79645/#79298 已合并）、profile 归档导入时安全 symlink 保留（#62194 待合并）。

---

## 8. 待处理积压

| Issue/PR | 创建日期 | 状态 | 风险 |
|---|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) Skills 索引陈旧 | 2026-07-18 | 78 条评论，长期 open | 高 — 影响 Skills Hub 可用性 |
| [#83832](https://github.com/NousResearch/hermes-agent/issues/83832) PKCE cookie `;` 序列化 | 2026-08-11 | open，无 fix PR | 高 — OIDC 登录阻断 |
| [#92606](https://github.com/NousResearch/hermes-agent/issues/92606) Anthropic OAuth token 互斥吊销 | 2026-08-23 | 今日新开 | 高 — 认证回退 |
| [#92565](https://github.com/NousResearch/hermes-agent/issues/92565) MCP 凭据变更后不重连 | 2026-08-22 | open，无 fix PR | 中 — 影响生产环境凭据轮换 |
| [#92553](https://github.com/NousResearch/hermes-agent/issues/92553) pre_tool_call hook approve 静默失效 | 2026-08-22 | open，无 fix PR | 中 — 安全 hook 形同虚设 |
| [#92091](https://github.com/NousResearch/hermes-agent/issues/92091) Gateway 控制 Socket 设计 | 2026-08-22 | open，标记 needs-decision | 高 — fleet-update 所有 Bug 的根因 |
| [#78981](https://github.com/NousResearch/hermes-agent/issues/78981) DeepSeek 长会话死亡 | 2026-08-05 | open，无 fix PR | 高 — P1 |
| [#92271](https://github.com/NousResearch/hermes-agent/issues/92271) Windows Docker session `:` 目录名 | 2026-08-22 | open，无 fix PR | 高 — Windows Docker 用户完全不可用 |

> **维护者关注建议：** 今日集中提交了多个 P2 Bug（#92095、#92271、#92553、#92554、#92565、#92606、#92607、#92608），且多个安全问题（#83832、#92606）无对应 fix PR。建议优先处理 Gateway 控制面设计（#92091）和 PKCE/OAuth 认证链修复。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-23

---

## 1. 今日速览

过去24小时内 PicoClaw 社区保持中等活跃度：**6 条 PR** 更新（4 已合并/关闭，2 待处理）、**2 条 Issue** 新开，均与 MCP 连接稳定性及工具回调异常相关，无任何新版本发布。综合评估：**项目健康度中等**，核心 agent loop 存在阻塞缺陷，已有对应修复 PR 等待合并，社区对稳定性问题响应积极，但积压的 stale PR 表明维护人力紧张。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并 / 关闭的 PR（4 条）

| PR | 作者 | 摘要 | 影响 |
|---|---|---|---|
| [#3319](https://github.com/sipeed/picoclaw/pull/3319) [CLOSED] | MrTreasure | `exec` 工具现在正确遵守 per-run `timeout` 参数，并修正 `background`/`pty` 的布尔类型声明 | 修复工具行为不一致的潜在隐患 |
| [#714](https://github.com/sipeed/picoclaw/pull/714) [CLOSED] | seanly | skill 安装/重装 CLI 重构，引入 `skillsCmd`，支持 `repo@branch` 及子路径安装 | 增强 skill 生态的可维护性 |
| [#1083](https://github.com/sipeed/picoclaw/pull/1083) [CLOSED] | liugangjian | 修复循环 cron 任务执行后静默变为一次性任务的问题（Fixes #1043） | 修复定时任务可靠性 |
| [#1545](https://github.com/sipeed/picoclaw/pull/1545) [CLOSED] | xuwei-xy | 合并 #1500 #1490 #1488 #1487 #1485 多项修复 | 批量合并历史积压修复 |

### 待处理 PR（2 条）

- [#3337](https://github.com/sipeed/picoclaw/pull/3337) — **高优先级**：修复 MCP 服务器连接失败时 agent loop 阻塞的 Bug，对应 Issue #3269，**建议优先合并**。
- [#3222](https://github.com/sipeed/picoclaw/pull/3222) — Deltachat 重构清理，减少约 200 行代码，标记 `stale`，长期无人跟进。

> **整体判断**：今日主要进展集中在**修复稳定性问题**（cron 循环、exec 超时），MCP 阻塞 Bug 的修复 PR 已就绪但尚未合并，是阻碍 chat 界面可用性的关键路径。

---

## 4. 社区热点

| 条目 | 类型 | 评论/状态 | 热度分析 |
|---|---|---|---|
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) | Issue（BUG） | 6 条评论，1 👍，`stale` | **今日最活跃 Issue**。MCP 连接失败导致 chat 界面完全停止响应，直接影响用户体验。已有 PR #3337 修复，但因 `stale` 标记可能面临被自动关闭风险，需维护者手动跟进。 |
| [#3343](https://github.com/sipeed/picoclaw/issues/3343) | Issue（BUG） | 0 条评论，新创建 | Telegram 工具回调在 agent turn 失败后仍持续调用 `editMessageText`，三天内产生 228,000+ 次请求，触发 Telegram 服务端限流。属于**资源浪费型 Bug**，尚无修复 PR。 |
| [#3337](https://github.com/sipeed/picoclaw/pull/3337) | PR（待合并） | — | 直接对应 #3269，修复 MCP 连接失败时的 agent loop 挂起问题，**是当前最值得关注的 PR**。 |

---

## 5. Bug 与稳定性

按严重程度排列：

| 优先级 | Issue | 描述 | 是否有 Fix PR |
|---|---|---|---|
| 🔴 **高** | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP 服务器连接失败 → agent loop 永久挂起 → chat 界面停止响应 | ✅ [#3337](https://github.com/sipeed/picoclaw/pull/3337)（待合并） |
| 🟠 **中** | [#3343](https://github.com/sipeed/picoclaw/issues/3343) | Telegram `editMessageText` 在任务失败后仍每3秒重复调用，导致 22.8 万次无效请求及服务端限流 | ❌ 暂无 |
| 🟡 **低** | [#3319](https://github.com/sipeed/picoclaw/pull/3319)（已关闭） | `exec` 工具 `timeout`/布尔参数被静默忽略（已修复） | ✅ 已合并 |
| 🟡 **低** | [#1083](https://github.com/sipeed/picoclaw/pull/1083)（已关闭） | 循环 cron 任务执行后静默变为一次性任务（已修复） | ✅ 已合并 |

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 分析 |
|---|---|---|
| skill 安装工具链重构 | [#714](https://github.com/sipeed/picoclaw/pull/714) 已合并 | 支持 `repo@branch` 及子路径安装，反映社区对**更灵活的 skill 管理**的诉求，预计纳入后续版本迭代。 |
| Deltachat 代码清理 | [#3222](https://github.com/sipeed/picoclaw/pull/3222) 待处理 | 移除遗留功能、统一配置方式（secrets 移至 jsonrpc），体现**配置现代化**方向，但需维护者解除 `stale` 状态。 |
| 工具超时与布尔参数规范化 | [#3319](https://github.com/sipeed/picoclaw/pull/3319) 已合并 | 用户对工具行为一致性要求明确，预计后续工具层将系统性检查参数类型声明。 |

---

## 7. 用户反馈摘要

- **痛点 1（高共鸣）**：MCP 服务器不稳定时，整个 chat 界面"假死"，用户完全无法获得回复。[#3269](https://github.com/sipeed/picoclaw/issues/3269) 用户环境：nightly 版本 + Qwen3 模型，说明 MCP 已成为生产环境常见依赖，其稳定性直接影响核心体验。
- **痛点 2（资源浪费）**：Telegram 回调在任务失败后未正确终止，产生大量无效请求并触发平台限流。[#3343](https://github.com/sipeed/picoclaw/issues/3343) 反映出**错误处理链路不完善**，工具生命周期管理存在漏洞。
- **正面反馈**：cron 循环任务和 exec 超时等 Bug 修复已合并，用户对这些底层可靠性的改进有明确需求（[#1083](https://github.com/sipeed/picoclaw/pull/1083)、[#3319](https://github.com/sipeed/picoclaw/pull/3319)）。

---

## 8. 待处理积压

| 条目 | 类型 | 创建时间 | 风险 | 建议 |
|---|---|---|---|---|
| [#3337](https://github.com/sipeed/picoclaw/pull/3337) | PR（待合并） | 2026-08-14 | 🔴 高 — 修复阻塞性 Bug，久拖可能导致用户流失 | **立即合并**，解除 `stale` 标记 |
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) | Issue（BUG） | 2026-07-20 | 🔴 高 — 已 `stale`，有修复 PR 但未合并 | 合并 #3337 后关闭此 Issue |
| [#3222](https://github.com/sipeed/picoclaw/pull/3222) | PR（待合并） | 2026-07-03 | 🟠 中 — `stale` 标记超 50 天 | 评估是否保留，若保留需解除 stale 并安排 review |
| [#3343](https://github.com/sipeed/picoclaw/issues/3343) | Issue（BUG） | 2026-08-22 | 🟠 中 — 新发现，无修复方案 | 分配开发资源，优先处理回调生命周期管理 |

---

**报告生成时间**：2026-08-23 | 数据来源：[github.com/sipeed/picoclaw](https://github.com/sipeed/picoclaw)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-08-23

## 1. 今日速览

过去24小时 NanoClaw 保持高活跃开发节奏：**1个新 Issue、26条 PR（8条已合并/关闭，18条仍待合并）**，整体贡献热度较高。今日重点推进了 **Slack 集成修复**（2条已合）、**Telegram 稳定性改进**（多项正在进行）以及 **构建系统优化**（Bun / better-sqlite3）。社区对多通道适配器的可靠性关注集中，暂无新版本发布。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

### 今日已合并/关闭的 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#3394](https://github.com/nanocoai/nanoclaw/pull/3394) | Bug Fix (Slack) | 修复了当工作区应用审批策略阻止托管安装时，手动安装回退 URL 的 `redirect_uri` 验证失败及代理驱动配置的死锁问题。 |
| [#3390](https://github.com/nanocoai/nanoclaw/pull/3390) | Bug Fix (Slack Setup) | 修复 Slack 重新配置流程中重复创建 Bot 的缺陷：预检步骤现在检测到已有 `SLACK_BOT_TOKEN` 则跳过重新 provision。 |
| [#3443](https://github.com/nanocoai/nanoclaw/pull/3443) | 构建优化 | 移除 `better-sqlite3` 的 `onlyBuiltDependencies` 配置，直接使用包内预编译绑定，避免 `node-gyp rebuild` 失败。 |
| [#3445](https://github.com/nanocoai/nanoclaw/pull/3445) | 无效 PR | 提交者误开仓库，主动关闭，无实际变更。 |

**整体推进评估**：核心通道（Slack、Telegram）的可靠性修复是今日主线，构建工具链也有实质改进，项目健康度良好。

## 4. 社区热点

### 高关注 PR / Issue

1. **[PR #3318](https://github.com/nanocoai/nanoclaw/pull/3318)** — *Fix: 强制使用非-AVX2 基础版 Bun 二进制*
   - 问题：CI 构建机 CPU 支持 AVX2，但安装脚本基于构建机探测而非目标容器，导致生成的镜像在旧硬件上崩溃。
   - 诉求：容器镜像的跨平台兼容性。

2. **[PR #3447](https://github.com/nanocoai/nanoclaw/pull/3447)** — *Fix: 电路断路器崩溃计数按实例隔离*
   - 问题：启动熔断器计数器未绑定实例，挂载同一 `data/` 目录的多个实例会相互干扰，导致错误延迟启动。
   - 诉求：多实例部署场景下的容错隔离。

3. **[PR #3446](https://github.com/nanocoai/nanoclaw/pull/3446)** — *Fix: 未知发送者门控中自动丢弃 Bot/Webhook 发送方*
   - 问题：Discord/Slack/Telegram 的 Bot 触发 `request_approval` 后，发送方无法点击审批卡片，造成死循环。
   - 诉求：自动化消息不应触发人工审批流程。

4. **[Issue #3453](https://github.com/nanocoai/nanoclaw/issues/3453)** — *stdin-json 测试在 Node 25+ 失败*
   - 问题：tsx loader 触发的 `module.register()` 弃用警告污染 stderr，导致断言失败。
   - 诉求：保持与最新 Node.js LTS 版本的测试兼容性。

5. **[PR #3450](https://github.com/nanocoai/nanoclaw/pull/3450)** — *Telegram: 在 sender_scope 门控中信任频道自身身份*
   - 修复 #2991，解决 Telegram 广播频道匿名帖子无法通过身份验证的问题。

## 5. Bug 与稳定性

| 严重程度 | 问题 | 状态 | 关联 PR/Issue |
|---|---|---|---|
| 🔴 高 | 多实例部署时电路断路器崩溃计数相互干扰 | 待合并 | [#3447](https://github.com/nanocoai/nanoclaw/pull/3447) |
| 🔴 高 | Telegram 广播频道帖子被未知发送者门控拦截 | 待合并 | [#3450](https://github.com/nanocoai/nanoclaw/pull/3450) |
| 🟡 中 | Slack 配置流程重复创建 Bot | ✅ 已修复 | [#3390](https://github.com/nanocoai/nanoclaw/pull/3390) |
| 🟡 中 | Slack 手动安装回退 URL 失效 | ✅ 已修复 | [#3394](https://github.com/nanocoai/nanoclaw/pull/3394) |
| 🟡 中 | Bot/Webhook 触发审批卡片导致死循环 | 待合并 | [#3446](https://github.com/nanocoai/nanoclaw/pull/3446) |
| 🟢 低 | Node 25+ tsx loader 弃用警告污染测试 stderr | 新开 | [#3453](https://github.com/nanocoai/nanoclaw/issues/3453) |
| 🟢 低 | Docker 镜像 Bun 二进制 AVX2 兼容性 | 待合并 | [#3318](https://github.com/nanocoai/nanoclaw/pull/3318) |

## 6. 功能请求与路线图信号

| 方向 | 证据 | 可能性 |
|---|---|---|
| **Cursor 编辑器集成** | [#3355](https://github.com/nanocoai/nanoclaw/pull/3355)（add-cursor agent provider skill）、[#3356](https://github.com/nanocoai/nanoclaw/pull/3356)（Cursor Agent SDK payload） | 高 — 两条 PR 已形成完整功能链路 |
| **多 Telegram Bot 支持** | [#3438](https://github.com/nanocoai/nanoclaw/pull/3438)、[#3437](https://github.com/nanocoai/nanoclaw/pull/3437)、[#3435](https://github.com/nanocoai/nanoclaw/pull/3435) — setup 向导支持添加第二个 Bot、携带 adapter 实例贯穿配对流程 | 高 — 多实例 Telegram 配置链路完整 |
| **MPDM（多人员 DM）通道名称可读性** | [#3385](https://github.com/nanocoai/nanoclaw/pull/3385) — 修复 Slack MPDM 审批卡片显示 `mpdm-…` slug 而非可读名称 | 中 — 体验改进型修复，已准备就绪 |
| **组作用域参数显式覆盖警告** | [#3448](https://github.com/nanocoai/nanoclaw/pull/3448) — 当调用方显式传入的值与组作用域自动填充值冲突时发出警告 | 中 — 开发者体验改进 |

## 7. 用户反馈摘要

- **多通道适配稳定性是核心痛点**：Telegram 频道身份识别、Slack 重复配置、Bot 触发审批死循环等问题集中反映了用户在**多平台生产环境部署**中遇到的可靠性质疑。
- **容器化部署的跨硬件兼容性**：[#3318](https://github.com/nanocoai/nanoclaw/pull/3318) 指向用户在不同 CPU 架构的服务器上运行容器时的实际困扰，AI 智能体平台的部署灵活性诉求明显。
- **测试环境与 Node.js 升级的摩擦**：[#3453](https://github.com/nanocoai/nanoclaw/issues/3453) 表明项目需持续跟进 Node 25+ 的 TSX loader 变化，以维持 CI 稳定性。

## 8. 待处理积压

| PR/Issue | 状态 | 建议 |
|---|---|---|
| [#3447](https://github.com/nanocoai/nanoclaw/pull/3447) | OPEN — 电路断路器实例隔离 | 高优，多实例部署场景刚需，建议优先 Review |
| [#3450](https://github.com/nanocoai/nanoclaw/pull/3450) | OPEN — Telegram sender_scope 修复 | 高优，影响频道广播功能可用性 |
| [#3446](https://github.com/nanocoai/nanoclaw/pull/3446) | OPEN — Bot 发送者审批门控修复 | 中高，自动化场景必需 |
| [#3318](https://github.com/nanocoai/nanoclaw/pull/3318) | OPEN — Bun 二进制兼容性 | 中，容器镜像质量问题 |
| [#3453](https://github.com/nanocoai/nanoclaw/issues/3453) | OPEN — Node 25+ 测试兼容性 | 低，纯测试修复，建议合并相关 PR 后跟进 |
| [#3434](https://github.com/nanocoai/nanoclaw/pull/3434) | OPEN — 轮询适配器不应启动 webhook 服务器 | 中，逻辑正确性修复 |

---

**项目健康度评级**：🟢 **良好** — 过去24小时有4个实质性修复已合入主干，8+个关键稳定性 PR 待合并，开发节奏稳定，无阻塞性 release 延期风险。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目日报 — 2026-08-23

---

## 1. 今日速览

过去24小时 IronClaw 保持高活跃度：共 9 条 Issues 更新（5 新开、4 关闭）和 21 条 PR 更新（5 合并、16 待审）。核心开发集中在三项并行轨道：(1) CI/CD 效率优化（T1-T4 四通道同步推进），(2) 后台子代理能力交付，(3) WebUI 治理与 UX 打磨。无新版本发布，整体项目处于"密集集成+持续重构"阶段，健康度良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 主题 | 贡献者 | 影响 |
|----|------|--------|------|
| [#7773](https://github.com/nearai/ironclaw/issues/7773) | 移除重复的 Settings / Extensions 标签组件 | @italic-jinxin | 清理 WebUI 技术债，消除导航元数据漂移 |
| [#7774](https://github.com/nearai/ironclaw/issues/7774) | 使自动化 presenter 日期断言时区鲁棒 | @italic-jinxin | 修复 `Asia/Shanghai` 等时区下测试失败 |
| [#7772](https://github.com/nearai/ironclaw/issues/7772) | 在 Configure 中暴露扩展设置阶段与阻塞项 | @italic-jinxin | 修复弹窗误报"无需配置"的 UX 缺陷 |
| [#7700](https://github.com/nearai/ironclaw/issues/7700) | 发布权威的运行结果通知 | @italic-jinxin | 从 Process Journal 转换派生通知，替代 delivery watcher |

### 关键开放 PR（待审/合并中）

- **[PR #7491](https://github.com/nearai/ironclaw/pull/7491)** — 核心工具合约重构（`read/write/edit/glob/grep/bash` 六种精确裸名），移除遗留的 `builtin__*` 混合表面，是长期技术债清理的关键一步。
- **[PR #7810](https://github.com/nearai/ironclaw/pull/7810)** — 沙箱通过通用凭证绑定中介 GitHub CLI，支持 per-user egress，是 [#7825](https://github.com/nearai/ironclaw/issues/7825) 的实现载体。
- **[PR #7818](https://github.com/nearai/ironclaw/pull/7818)** — 后台子代理 Producer 侧（slice 2b+2c），完成子代理生成、逐子投递、激活与愈合扫描的核心能力。
- **[PR #7765](https://github.com/nearai/ironclaw/pull/7765)** — `AfterTurn` 生命周期钩子（[#7770](https://github.com/nearai/ironclaw/issues/7770) Phase 1），允许在 turn 终态后执行 privileged hook，为 memory curation 等下游能力铺路。

---

## 4. 社区热点

| Issue/PR | 热度 | 核心诉求 |
|----------|------|----------|
| [#7824](https://github.com/nearai/ironclaw/issues/7824) | ⭐ 高 | **上下文投影与 token 成本** — PinchBench 实测：PR #7491（54.4% 任务）消耗 227.7M token / $10.31，vs 旧基线（60.5%）仅 55.1M / $2.52。用户关注上下文压缩（Pi-style compaction barrier）与溢出恢复机制。 |
| [#7825](https://github.com/nearai/ironclaw/issues/7825) | 中 | **沙箱出口认证通用化** — 消除 GitHub 特例，通过 `iron-proxy` + 宿主凭证 broker 实现 provider-neutral 的凭证注入。 |
| [#7815](https://github.com/nearai/ironclaw/issues/7815) | 中 | **Onboarding 建议流程** — 补齐 connect → suggest → thread 的累积净新增工作量，前端已由 [#7816](https://github.com/nearai/ironclaw/pull/7816) 覆盖。 |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) | 中 | **IronHub Agent Link WebUI 面板** — 首次为 operator 提供 WebUI 侧的安装表面，解决纯 CLI 无法完成部署的痛点。 |

---

## 5. Bug 与稳定性

| Issue | 严重度 | 状态 | Fix PR |
|-------|--------|------|--------|
| [#7823](https://github.com/nearai/ironclaw/issues/7823) — Notion 安装失败 | Medium | Open | 暂无 |
| [#7822](https://github.com/nearai/ironclaw/issues/7822) — Slack 设置失败 | Medium | Open | 暂无 |

> 两者均源于同一 Slack 反馈线程（C09FDEDH5PA，报告者 alejo.escriva），归类为 `integration-install` 类别，反映第三方工具集成安装流程存在用户体验断点，建议优先关注。

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 推断 |
|------|------|------|
| **上下文压缩与成本优化** | [#7824](https://github.com/nearai/ironclaw/issues/7824) | 高频 token 消耗是用户核心痛点；Pi-style compaction 可能是下一版本的关键特性 |
| **AfterTurn 生命周期钩子** | [#7765](https://github.com/nearai/ironclaw/pull/7765) | 为 memory curation、自动摘要等能力提供扩展点，预示插件生态深化 |
| **后台子代理（Background Subagents）** | [#7818](https://github.com/nearai/ironclaw/pull/7818) | R2 系列功能的第二阶段，标志项目向"多代理协作"架构演进 |
| **CI 效率四通道优化** | [#7821](https://github.com/nearai/ironclaw/pull/7821), [#7817](https://github.com/nearai/ironclaw/pull/7817), [#7819](https://github.com/nearai/ironclaw/pull/7819), [#7809](https://github.com/nearai/ironclaw/pull/7809) | 基础设施层持续加固，T1-T4 并行推进反映对交付速度的重视 |

---

## 7. 用户反馈摘要

- **痛点**：第三方集成（Notion、Slack）安装/配置流程存在障碍，用户反馈渠道明确但 fix PR 尚未出现。
- **成本敏感**：[#7824](https://github.com/nearai/ironclaw/issues/7824) 中 PinchBench 的实测数据（227.7M vs 55.1M token）显示用户对 token 消耗极度敏感，性能优化是核心诉求。
- **满意度**：WebUI 设计系统提案 [#7257](https://github.com/nearai/ironclaw/pull/7257) 和 APDD 治理框架评估 [#7255](https://github.com/nearai/ironclaw/pull/7255) 表明团队在系统化 UX 治理方面获得社区认可。

---

## 8. 待处理积压

| Issue/PR | 类型 | 关注理由 |
|----------|------|----------|
| [#7823](https://github.com/nearai/ironclaw/issues/7823) | Bug | Notion 安装失败，medium 严重度，无 fix PR，来自活跃用户反馈 |
| [#7822](https://github.com/nearai/ironclaw/issues/7822) | Bug | Slack 设置失败，同上，建议合并处理 |
| [#7824](https://github.com/nearai/ironclaw/issues/7824) | 功能 | 上下文压缩机制影响核心性能与成本，需优先排期 |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) | Feature | IronHub 链接 WebUI 面板，XL 规模，待合并中，需关注 review 进度 |
| [#7798](https://github.com/nearai/ironclaw/issues/7798) → [#7821](https://github.com/nearai/ironclaw/pull/7821) | Infra | CI 工具链锁定，T1 通道关键 PR，影响所有 Rust 任务构建 |

---

**报告生成时间**：2026-08-23  
**数据周期**：过去 24 小时  
**项目健康度**：🟢 良好 — 高活跃开发节奏，技术债清理与功能交付并行推进，无阻塞性崩溃报告。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 — 2026-08-23

---

## 1. 今日速览

过去 24 小时内，LobsterAI 共产生 8 个 GitHub 事件（2 Issues + 6 PRs），项目保持**中等活跃度**。5 个 PR 已合并/关闭，2 个 Issues 已关闭，整体贡献流转效率较高。今日无新版本发布，但修复类 PR 占比 83%（5/6），表明项目正集中打磨稳定性与用户体验。唯一开放的 PR（#2452）涉及 OpenClaw 模型 ID 解析修复，预计近期可合并。

---

## 2. 版本发布

暂无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#1205](https://github.com/netease-youdao/LobsterAI/pull/1205) | fix | 会话重命名失败时增加 Toast 错误提示，避免用户无感知失败 |
| [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | feat | Cowork 会话新增手动重试按钮，支持 429/网络故障等瞬时可重试错误的快速重试 |
| [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | fix | 修复 web-search 中 `--disable-blink-features=AutomationControlled` flag 导致的 Chrome 启动异常 |
| [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | fix | 自定义模型提供商数量上限从 10 个扩展至 20 个，解决用户无法保留旧配置的问题 |
| [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) | feat | 会话详情新增「导出为 Markdown」功能，支持用户引用、整理和分享对话记录 |

**整体评估：** 今日 5 个已关闭 PR 覆盖了错误反馈、重试机制、浏览器兼容性、配置容量和功能导出四个维度，项目在前端交互稳定性和功能完整性方面稳步前进。

---

## 4. 社区热点

### Issue [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) — kimi2.5 模型重复处理文档
- **状态：** CLOSED（stale）
- **评论数：** 2 | **点赞：** 0
- **热度分析：** 用户反馈私有化部署的 kimi2.5 模型在分析文档时重复回复当前动作，复现概率高（当前任务必现），切换模型后恢复正常。该 Issue 标记为 stale 且已关闭，但未见关联 Fix PR，**建议确认是否已真正修复或仅因超时而关闭**。

### Issue [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) → PR [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) — 导出为 Markdown 功能
- **状态：** CLOSED（关联 PR 已合并）
- **评论数：** 2 | **点赞：** 0
- **热度分析：** 用户痛点明确——当前仅支持图片导出，不便引用和检索。PR #1214 已完整实现该功能，复用已有数据结构生成 Markdown，并自动截断过长工具调用结果（300 字）。**功能闭环，用户满意度预期较高。**

---

## 5. Bug 与稳定性

| 级别 | 问题 | 状态 | Fix PR |
|---|---|---|---|
| 中 | [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) kimi2.5 模型分析文档重复回复 | CLOSED (stale) | 无关联 PR，需跟进 |
| 低 | [#1205](https://github.com/netease-youdao/LobsterAI/issues/1205) 会话重命名失败无错误提示 | CLOSED | [#1205](https://github.com/netease-youdao/LobsterAI/pull/1205) ✅ |
| 低 | [#1209](https://github.com/netease-youdao/LobsterAI/issues/1209) web-search Chrome flags 兼容性问题 | CLOSED | [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) ✅ |

**稳定性评估：** 今日关闭的 Bug 均为低中优先级，无崩溃或回归类严重问题。但 #1206 以 stale 状态关闭而缺乏明确修复记录，建议维护者复查。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 状态 | 纳入下一版本概率 |
|---|---|---|---|
| 会话详情导出为 Markdown | [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) | ✅ 已实现（PR #1214） | — |
| 自定义模型提供商扩容 | 用户反馈累积 | ✅ 已实现（PR #1212） | — |
| Cowork 手动重试按钮 | [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | ✅ 已实现 | — |

**路线图信号：** 用户反馈集中在「导出能力」「错误容错」「配置容量」三类场景，项目正沿此方向持续迭代，暂无高风险需求积压。

---

## 7. 用户反馈摘要

- **kimi2.5 模型行为异常（#1206）：** 用户反馈重复回复问题明确，但切换模型后恢复正常，疑似模型适配器层的兼容性问题，非全局 Bug。
- **导出功能需求强烈（#1213）：** 用户明确表示图片导出不便引用和检索，Markdown 格式更符合工作流，该需求已被快速响应并实现。
- **重试机制体验改善（#1208）：** 用户对 429 等瞬时错误的重试体验提出改进建议，新增内联重试按钮显著提升 Cowork 会话的容错能力。
- **配置容量瓶颈（#1212）：** 用户反馈 10 个自定义提供商上限已无法满足实际使用，扩容至 20 个解决了配置切换痛点。

---

## 8. 待处理积压

| 项目 | 链接 | 风险等级 | 建议 |
|---|---|---|---|
| PR #2452 — OpenClaw  slashed model IDs 的 provider 保留 | [#2452](https://github.com/netease-youdao/LobsterAI/pull/2452) | 中 | 仍 OPEN，涉及 `custom_0` + `deepseek-ai/DeepSeek-V4-Flash` 类模型 ID 的持久化问题，建议尽快审查合并 |
| Issue #1206 — kimi2.5 重复处理（stale closed） | [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | 低-中 | 以 stale 关闭但无关联 Fix PR，建议维护者确认是否真正修复或重新打开 |

---

**项目健康度评分：7.5/10** — 活跃度良好，Bug 修复效率较高，功能需求响应及时；唯一隐患是 #1206 的关闭方式不够明确，建议跟进确认。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-08-23

## 1. 今日速览

Moltis 今日整体活跃度中等偏上：1 个 Issue 已关闭，3 个 PR 待合并，无新版本发布。**安全性与兼容性**是今日主要工作方向**——涉及安全 Hook 的 fail-closed 策略落地，以及 MCP 客户端重启、Browserless v2 兼容性等稳定性修复。项目维护节奏稳健，技术债务清理持续推进，整体健康度良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已关闭 Issue

- **[Issue #1230](https://github.com/moltis-org/moltis/issues/1230)** — `feat(hooks): add an opt-in fail-closed error policy for modifying security hooks`
  - 状态：✅ 已关闭
  - 作者：`kantorcodes`
  - 推进内容：为安全 Hook 边界场景引入可选项的 **fail-closed 错误策略**，修复了 runtime hook 失败时降级为继续执行的漏洞。此前 `BeforeToolCall` 等 modifying hooks 仅在显式 `Block` 时短路，而运行时异常未做安全兜底，此次补齐了该缺口。

### 待合并 PR（3 条）

| PR | 作者 | 领域 | 摘要 |
|---|---|---|---|
| [#1232](https://github.com/moltis-org/moltis/pull/1232) | IlyaBizyaev | tools | 修复 object schemas 与 OpenAI strict mode 的兼容性，解决 Codex 强制发送 null/空值的问题 |
| [#1231](https://github.com/moltis-org/moltis/pull/1231) | IlyaBizyaev | mcp | 修复 MCP 服务端重启后客户端引用失效，保持 server connection 绑定而非捕获旧实例 |
| [#1229](https://github.com/moltis-org/moltis/pull/1229) | rubenssoto | browser | 新增 Browserless v2 container-protocol 支持，同时保留 v1 作为默认向后兼容 |

> **进展评估**：今日合并/关闭 1 项，3 项待审，无阻塞性进展。PR 集中在**稳定性修复**，无新功能上线，项目整体稳步向前。

---

## 4. 社区热点

### 高关注 Issue

- **[Issue #1230](https://github.com/moltis-org/moltis/issues/1230)** — `feat(hooks): add an opt-in fail-closed error policy for modifying security hooks`
  - 评论：1 | 👍：0
  - 诉求分析：用户关注**安全边界的可靠性**——当 security hook 本身出现异常（如 shell hook 超时）时，期望系统默认拒绝而非继续执行，符合"fail-closed"安全原则。此 Issue 现已关闭，预计对应 PR 即将合并。

### 高关注 PR

- **[PR #1232](https://github.com/moltis-org/moltis/pull/1232)** — `fix(tools): make object schemas OpenAI-safe`
  - 诉求分析：OpenAI strict tool schemas 要求对象以 `additionalProperties=false` 关闭，导致未声明的 patch/map 字段被强制置空，影响 Codex 等 Agent 的数据传递。修复后 cron 和 webhook patch 字段显式声明，MCP 环境变量以固定 name/value 形式表示，提升跨平台兼容性。

- **[PR #1231](https://github.com/moltis-org/moltis/pull/1231)** — `fix(mcp): resolve current client after server restart`
  - 诉求分析：MCP tool bridges 在注册表同步时捕获了当前 client 引用，服务端重启后旧 client 被关闭，但活跃 chat turn 仍通过已关闭实例分发请求，导致功能失效直至下一轮重建注册表。修复方案为绑定 server connection 而非 client 实例，提升连接稳定性。

---

## 5. Bug 与稳定性

| 问题 | 严重级别 | 来源 | 状态 |
|---|---|---|---|
| MCP 服务端重启后客户端引用失效，活跃 turn 继续通过已关闭实例分发 | 中 | PR #1231 | 🔧 待合并 |
| OpenAI strict schemas 导致 patch/map 字段被强制置 null | 中 | PR #1232 | 🔧 待合并 |
| Browserless v2 container 协议不支持 | 低 | PR #1229 | 🔧 待合并 |

> 无严重崩溃或回归报告。今日修复均为**兼容性/稳定性类**问题，无高危 Bug。

---

## 6. 功能请求与路线图信号

| 需求来源 | 内容 | 路线图信号 |
|---|---|---|
| [Issue #1230](https://github.com/moltis-org/moltis/issues/1230) | 安全 Hook 的 fail-closed 策略 | ✅ 已关闭，预计随安全修复版本合入 |
| [PR #1232](https://github.com/moltis-org/moltis/pull/1232) | OpenAI strict schema 兼容 | 🟡 待合并，反映对主流 LLM 平台兼容性的持续投入 |
| [PR #1231](https://github.com/moltis-org/moltis/pull/1231) | MCP 连接稳定性 | 🟡 待合并，MCP 生态稳定性是近期重点 |
| [PR #1229](https://github.com/moltis-org/moltis/pull/1229) | Browserless v2 支持 | 🟡 待合并，反映对容器化工具链的跟进 |

> **判断**：下一版本预计聚焦**安全性加固 + MCP/Browser 生态兼容性**，暂无大型新功能信号。

---

## 7. 用户反馈摘要

- **安全 Hook 可靠性**：用户明确指出当前 security hook 在运行时失败时"degrade to continuation"存在风险，期望提供 opt-in 的 fail-closed 策略以强化安全边界（[Issue #1230](https://github.com/moltis-org/moltis/issues/1230)）。
- **OpenAI 兼容性问题**：Codex 等 Agent 在使用 strict tool schemas 时被迫发送 null/空值，影响实际数据传递；用户期望 Moltis 能正确声明 patch/map 字段（[PR #1232](https://github.com/moltis-org/moltis/pull/1232)）。
- **MCP 连接稳定性**：服务端重启后连接未及时重建，导致活跃 chat turn 持续失败，用户期待更健壮的连接管理（[PR #1231](https://github.com/moltis-org/moltis/pull/1231)）。
- **容器化工具链**：Browserless v2 的 container-protocol 支持缺失，影响使用新容器部署的用户（[PR #1229](https://github.com/moltis-org/moltis/pull/1229)）。

---

## 8. 待处理积压

| 项目 | 类型 | 状态 | 建议 |
|---|---|---|---|
| [PR #1232](https://github.com/moltis-org/moltis/pull/1232) | fix(tools) | 🔓 待合并 | 建议尽快审查，影响 OpenAI/Codex 兼容性 |
| [PR #1231](https://github.com/moltis-org/moltis/pull/1231) | fix(mcp) | 🔓 待合并 | 建议优先处理，MCP 连接稳定性问题影响面较广 |
| [PR #1229](https://github.com/moltis-org/moltis/pull/1229) | fix(browser) | 🔓 待合并 | 建议跟进，Browserless v2 用户呼声较高 |

> 3 个 PR 均创建已超过 24 小时，评论数为 undefined，建议维护者加快审查节奏。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目日报 — 2026-08-23

---

## 1. 今日速览

过去24小时 CoPaw 项目保持中等活跃度，新增 7 条 Issues 和 4 条 PR，整体趋势偏向问题反馈而非新功能贡献。唯一关闭的 Issue（#7043）为功能请求类，且已归档。无新版本发布，但积压了 4 条待合并 PR，涵盖文档修复、Chrome 远程桥接、Cron Job 模型选择及自定义 Profile 显示等改进，项目功能层面仍在稳步推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日 **0 条 PR 合并**，4 条 PR 均处于待审查/待合并状态：

| PR | 类型 | 内容摘要 |
|----|------|----------|
| [#7214](https://github.com/agentscope-ai/QwenPaw/issues/7214) | docs | 补充 README 中被遗漏的"访问控制策略"安全层说明 |
| [#7054](https://github.com/agentscope-ai/QwenPaw/pull/7054) | feat | 支持 Chrome 插件通过 LAN/网络桥接连接非本机浏览器 |
| [#7050](https://github.com/agentscope-ai/QwenPaw/pull/7050) | feat | Cron Job 新增独立模型选择器，支持按任务覆盖默认模型 |
| [#6808](https://github.com/agentscope-ai/QwenPaw/pull/6808) | fix | 修复自定义 Profile Markdown 文件在文件工作区中被过滤隐藏的问题 |

**进展评估**：PR #7054 和 #7050 为首次贡献者提交，处于 Under Review 状态，是近期最有价值的功能推进，分别解决了多机协作和定时任务灵活性两大痛点。PR #6808 修复了已存在的 UX 缺陷。

---

## 4. 社区热点

### 🔥 Issue #7196 — 推理过程默认折叠（2 条评论 · 1 👍）
[链接](https://github.com/agentscope-ai/QwenPaw/issues/7196)

**热度原因**：直接触及长期使用体验的核心痛点——推理过程全量展开造成严重的视觉干扰，用户明确要求参考 Hermes 提供可配置的折叠行为。评论数在当日 Issues 中最高，表明社区对 UI/UX 精细化控制的期待。

### Issue #7216 — shell 工具名被 LLM 间歇性字符替换
[链接](https://github.com/agentscope-ai/QwenPaw/issues/7216)

**热度原因**：涉及工具调用链路的稳定性，`execute_shell_command` 被替换为 `execute_|hell_command` 等变体导致 `ToolNotFoundError`，属于较隐蔽的 LLM 输出可靠性问题，影响面广。

---

## 5. Bug 与稳定性

| 严重级别 | Issue | 描述 | Fix PR |
|----------|-------|------|--------|
| 🔴 高 | [#7212](https://github.com/agentscope-ai/QwenPaw/issues/7212) | 图片像素维度超出 Provider 限制时请求崩溃（`MODEL_EXECUTION_ERROR`），会话直接结束，未做优雅降级 | 无 |
| 🔴 高 | [#7216](https://github.com/agentscope-ai/QwenPaw/issues/7216) | LLM 输出中间歇性字符替换导致工具名失效 | 无 |
| 🟡 中 | [#7215](https://github.com/agentscope-ai/QwenPaw/issues/7215) | 添加 OpenRouter/OpenCode 后端后 GUI 界面无法正常显示 | 无 |
| 🟡 中 | [#7213](https://github.com/agentscope-ai/QwenPaw/issues/7213) | 会话输出持续产生无意义空行，已反馈多次未修复 | 无 |

**稳定性评估**：今日新增 Bug 集中在模型 Provider 适配层（图片处理、后端注册）和输出格式层，未见严重回归，但 #7212 的崩溃问题直接影响用户体验完整性，建议优先处理。

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 纳入可能性 |
|-------|----------|------------|
| [#7196](https://github.com/agentscope-ai/QwenPaw/issues/7196) | 推理过程默认折叠，提供可配置开关 | ⭐⭐⭐ 高——UI 体验类优化，社区呼声明确 |
| [#7201](https://github.com/agentscope-ai/QwenPaw/issues/7201) | 拆分 `max_inline_media_bytes` 为独立的图片/视频/音频上限，并在 Provider 高级设置中暴露 | ⭐⭐ 中——与 #7212 关联，可能合并处理 |
| [#7043](https://github.com/agentscope-ai/QwenPaw/issues/7043) | 启动时自动执行 `chcp 65001` 切换 UTF-8 环境（已关闭） | 已处理/已拒绝，关闭归档 |

**路线图信号**：媒体处理能力的精细化控制（#7201）与崩溃修复（#7212）存在强关联，预计会在同一迭代中解决。推理过程折叠（#7196）属于高优先级体验优化，可能进入下一版本的 Roadmap。

---

## 7. 用户反馈摘要

- **视觉干扰**：推理过程默认全量展开被多位用户抱怨，期望提供类似 Hermes 的折叠控制选项。
- **Windows 编码问题**：中文 Windows 用户因默认 GBK 环境导致 shell 工具 UTF-8 输出异常，#7043 已关闭但暗示同类问题仍可能存在。
- **Provider 兼容性**：OpenRouter / OpenCode 后端注册后 GUI 渲染异常（#7215），以及图片维度限制导致崩溃（#7212），反映多 Provider 适配层尚不稳健。
- **输出格式**：会话输出空行问题（#7213）多次反馈未解决，说明前端渲染逻辑存在累积债务。

---

## 8. 待处理积压

| 类型 | Issue/PR | 创建时间 | 风险 |
|------|----------|----------|------|
| 📌 Bug | [#7212](https://github.com/agentscope-ai/QwenPaw/issues/7212) | 2026-08-22 | 图片处理崩溃，影响多模态场景 |
| 📌 PR | [#7054](https://github.com/agentscope-ai/QwenPaw/pull/7054) | 2026-08-15 | Chrome 远程桥接 PR 已等待 8 天，Under Review |
| 📌 PR | [#7050](https://github.com/agentscope-ai/QwenPaw/pull/7050) | 2026-08-15 | Cron Job 模型覆盖 PR 已等待 8 天 |
| 📌 PR | [#6808](https://github.com/agentscope-ai/QwenPaw/pull/6808) | 2026-08-07 | 自定义 Profile 显示修复已等待 16 天，长期未响应 |

**建议**：PR #6808 已积压超过两周，建议维护者优先审查；#7212 崩溃问题需在下一版本前定位修复。

---

*报告生成时间：2026-08-23 | 数据来源：CoPaw GitHub Repository*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-08-23

---

## 1. 今日速览

ZeroClaw 项目在 2026-08-23 保持高活跃度：过去 24 小时内新增/更新 Issue 50 条（新开 39、关闭 11），PR 更新 50 条（待合并 43、已合并/关闭 7），无新版本发布。项目当前处于 **v0.9.0 安全与网关重构攻坚期**，核心方向围绕运行时会话所有权、网关认证边界、插件生命周期和 SOP 控制平面推进。社区 RFC 讨论热度高，架构层争议集中，维护者决策队列运转正常。整体项目健康度良好，技术债清理与安全性加固并行。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 标题 | 影响 |
|---|---|---|
| [#9281](https://github.com/zeroclaw-labs/zeroclaw/issues/9281) | `fix(config): roll back auto-created map aliases when config set fails` | 修复 `config set` RPC 在持久化失败时残留别名的问题，提升配置写入原子性 |
| [#9960](https://github.com/zeroclaw-labs/zeroclaw/issues/9960) | `fix(quickstart): reject duplicate enabled webhook ports` | 防止 quickstart 生成多个别名绑定同一端口的非法配置 |
| [#9291](https://github.com/zeroclaw-labs/zeroclaw/issues/9291) | `fix(cli): detect installed AppImage and use a working desktop download URL` | 修复 Linux AppImage 安装检测失败及下载链接失效问题（关联 Issue #9202） |
| [#9694](https://github.com/zeroclaw-labs/zeroclaw/issues/9694) | `feat(zerocode): expose the SOP pane as a read-only status view` | zerocode TUI 新增 SOP 状态面板只读视图，补齐 #7790 路线图一项 |
| [#9203](https://github.com/zeroclaw-labs/zeroclaw/issues/9203) | `fix(sop): wire authenticated HTTP fan-in` | SOP HTTP 入口完成认证接入，关闭未认证 webhook dispatch 安全缺口 |

**推进评估：** 今日 7 条 PR 关闭，其中 5 条为 bug fix，2 条为功能补齐。核心进展集中在配置健壮性、CLI 可用性和 SOP 安全化，为 v0.9.0 安全强化路线提供了直接支撑。

---

## 4. 社区热点

### 讨论最活跃的 Issues

| Issue | 标题 | 评论数 | 标签 |
|---|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC: Runtime-owned conversation sessions and transport surface adapters | 24 | RFC, security, architecture, p2 |
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | Bug: 74 test failures on Windows | 19 | bug, p1, ci, runtime |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | RFC: Decouple memory lifecycle policy from storage backends | 16 | RFC, p2, memory |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | RFC: Realtime speech-to-speech channel for Gemini Live | 16 | RFC, p2, channel |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker: Maintainer decision queue for RFCs and design issues | 13 | tracker, p2 |

**分析：**
- **#9487** 是当前讨论焦点，涉及运行时会话所有权边界，与 PR #10265 直接对应，是 v0.9.0 安全重构的核心 RFC。
- **#7462** 的 Windows 测试失败问题持续 2 个月，74 个测试在 Windows 下失败且 CI 未覆盖，暴露跨平台测试矩阵缺口。
- **#6850** 和 **#8780** 分别指向内存策略解耦和实时语音通道扩展，反映用户对存储抽象和 multimodal 通道的需求。
- **#8692** 维护者决策队列 tracker 正常运行，说明 RFC 评审流程有专门协调机制。

---

## 5. Bug 与稳定性

### 严重 Bug（P1）

| Issue | 标题 | 状态 | Fix PR |
|---|---|---|---|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | 74 test failures on Windows | OPEN | — |
| [#9666](https://github.com/zeroclaw-labs/zeroclaw/issues/9666) | fix(channels): make the filesystem listener cancellation-aware | OPEN（进行中） | 关联 PR |
| [#9718](https://github.com/zeroclaw-labs/zeroclaw/issues/9718) | Telegram channel delivers duplicate messages when model emits both tool_call and content | OPEN（进行中） | — |
| [#9255](https://github.com/zeroclaw-labs/zeroclaw/issues/9255) | WASM plugin calls have no wall-clock timeout; a dripping HTTP response runs unbounded | CLOSED（已修复） | #9255 已关闭 |
| [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) | `block_high_risk_commands = false` is not honored — allowlisted high-risk command still blocked | OPEN | — |

### 中等严重 Bug（P2）

| Issue | 标题 | 状态 |
|---|---|---|
| [#9708](https://github.com/zeroclaw-labs/zeroclaw/issues/9708) | daemon: bound service launcher stdout and stderr logs | OPEN（进行中） |
| [#10073](https://github.com/zeroclaw-labs/zeroclaw/issues/10073) | Retire StoragePolicy::Rolling; absorb row-count cap into Rotating | OPEN（进行中） |
| [#10232](https://github.com/zeroclaw-labs/zeroclaw/issues/10232) | Daemon diagnostics drop the underlying error chain | OPEN |
| [#9001](https://github.com/zeroclaw-labs/zeroclaw/issues/9001) | Provider turn failures bury cause-specific diagnostics under a generic retry envelope | OPEN（进行中） |
| [#9590](https://github.com/zeroclaw-labs/zeroclaw/issues/9590) | Concurrent models refresh runs can lose cache entries | OPEN（进行中） |
| [#10251](https://github.com/zeroclaw-labs/zeroclaw/issues/10251) | 17 telegram listen_* tests assert on wall-clock timeouts | OPEN |

**稳定性评估：** 今日新增 2 个 P1 bug（#10164 安全策略失效、#10251 CI 间歇性失败）。#9255 WASM 超时问题已关闭，#9202 AppImage 检测已通过 #9291 修复。Windows 测试矩阵和 Telegram 重复消息问题尚未解决，建议优先跟进。

---

## 6. 功能请求与路线图信号

| Issue/PR | 标题 | 路线图表征 |
|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | Runtime-owned conversation sessions and transport surface adapters | v0.9.0 安全重构核心，PR #10265 已在推进 |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | Decouple memory lifecycle policy from storage backends | 存储抽象层重构，预计纳入 v0.9.x |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | Realtime speech-to-speech channel for Gemini Live | 实时语音通道扩展，多模态路线图 |
| [#7943](https://github.com/zeroclaw-labs/zeroclaw/issues/7943) | Realtime voice-host channel (backend-agnostic WS client) | 与 #8780 互补，通用语音通道基础 |
| [#8850](https://github.com/zeroclaw-labs/zeroclaw/issues/8850) | Move optional channels & tools from compile-time to runtime plugins | 编译时特性标志 → 运行时 WASM 插件，二进制瘦身 |
| [#5607](https://github.com/zeroclaw-labs/zeroclaw/issues/5607) | Add deterministic precondition gates to cron jobs | SOP/cron 前置条件门控，增强可靠性 |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) | Verbatim channel send over the gateway, without an agent turn | 网关直接消息透传，减少 agent 介入 |
| [#7790](https://github.com/zeroclaw-labs/zeroclaw/issues/7790) | Bring remaining web dashboard operator surfaces into zerocode | zerocode TUI 补齐 web dashboard 功能 |

**路线图判断：** v0.9.0 将聚焦安全强化（会话所有权、网关认证、WASM 超时），#8850 插件化是长期架构目标。实时语音通道（#8780/#7943）和零代码 SOP（#7790/#8288）是用户价值highest 的功能方向。

---

## 7. 用户反馈摘要

| 来源 | 痛点/反馈 |
|---|---|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | Windows 用户无法运行测试套件，74 个测试失败，CI 未覆盖 Windows，跨平台兼容性差 |
| [#10141](https://github.com/zeroclaw-labs/zeroclaw/issues/10141) | zerocode session 管理体验差，无法方便地复制/导航历史会话，用户抱怨"quite frustrating" |
| [#9202](https://github.com/zeroclaw-labs/zeroclaw/issues/9202) | Linux AppImage 安装后 `zeroclaw desktop` 命令无法检测，下载链接失效（已通过 #9291 修复） |
| [#9718](https://github.com/zeroclaw-labs/zeroclaw/issues/9718) | Telegram 渠道在模型同时返回 tool_call 和 content 时发送重复消息，影响用户体验 |
| [#10073](https://github.com/zeroclaw-labs/zeroclaw/issues/10073) | `StoragePolicy::Rolling` 在高事件量下性能严重退化，用户报告日志轮转瓶颈 |
| [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) | 安全策略 `block_high_risk_commands = false` 未生效，允许列表命令仍被拦截，用户信任受损 |
| [#9590](https://github.com/zeroclaw-labs/zeroclaw/issues/9590) | 并发 `models refresh` 导致缓存条目丢失，竞态条件影响多进程场景 |

---

## 8. 待处理积压

| Issue | 标题 | 创建时间 | 未响应时长 | 建议优先级 |
|---|---|---|---|---|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | 74 test failures on Windows | 2026-06-10 | ~74 天 | **P1** — CI 缺失 Windows 矩阵 |
| [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) | `block_high_risk_commands = false` not honored | 2026-08-20 | 3 天 | **P1** — 安全策略失效 |
| [#9255](https://github.com/zeroclaw-labs/zeroclaw/issues/9255) | WASM plugin calls have no wall-clock timeout | 2026-07-22 | ~32 天 | **P1** — 已关闭，确认修复 |
| [#9666](https://github.com/zeroclaw-labs/zeroclaw/issues/9666) | filesystem listener cancellation-aware | 2026-08-02 | 21 天 | **P1** — 进行中但未合并 |
| [#9718](https://github.com/zeroclaw-labs/zeroclaw/issues/9718) | Telegram duplicate messages | 2026-08-03 | 20 天 | **P1** — 进行中但未合并 |
| [#10251](https://github.com/zeroclaw-labs/zeroclaw/issues/10251) | 17 telegram tests assert on wall-clock timeouts | 2026-08-22 | 1 天 | **P2** — 新建，需跟进 |
| [#5607](https://github.com/zeroclaw-labs/zeroclaw/issues/5607) | Deterministic precondition gates to cron jobs | 2026-04-10 | ~135 天 | **P2** — 长期未响应 |

**维护者提醒：**
1. **#7462** Windows 测试失败已存在两个多月，建议将 Windows CI 加入测试矩阵。
2. **#10164** 安全策略失效属于高优先级 bug，需尽快审查 fix PR。
3. **#9666** 和 **#9718** 已标记进行中但未合并，建议推动代码审查。
4. **#5607** 长期未响应的 RFC/功能请求，建议维护者在决策队列中明确状态。

---

*报告生成时间：2026-08-23 | 数据来源：ZeroClaw GitHub Repository*

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*