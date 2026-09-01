# OpenClaw 生态日报 2026-09-01

> Issues: 480 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-01 04:39 UTC

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



# OpenClaw 项目动态日报 — 2026-09-01

---

## 1. 今日速览

过去 24 小时内 OpenClaw 社区保持高强度活跃：**480 条 Issue 更新**（254 条关闭，226 条新开/活跃）、**500 条 PR 更新**（197 条已合并/关闭，303 条待合并）。项目整体处于密集修复期，多个 P0/P1 级别的启动、迁移、会话稳定性问题在近两日内集中关闭，但仍有若干核心缺陷（WhatsApp 多模态阻塞、MCP 工具注入失效、子进程泄漏、2026.8.x 升级链路断裂）处于 open 状态。未发布新版本，修复正以 PR 形式持续累积。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#126424](https://github.com/openclaw/openclaw/pull/126424) | fix(gateway) | 将对话投递限制在 agent bindings 内，修复多 agent 环境下消息误投问题（Platinum Hermit 评级） |
| [#123975](https://github.com/openclaw/openclaw/pull/123975) | fix(scripts) | 修复 `tsgo` wrapper 在超时报错时留下僵死编译器进程树的问题 |
| [#128223](https://github.com/openclaw/openclaw/pull/128223) | fix(cli) | 修复 `openclaw models aliases add` 从过时快照解析别名目标的问题 |
| [#123535](https://github.com/openclaw/openclaw/pull/123535) | fix(ui) | 避免 Control UI 会话目录在窗口焦点变化时触发全量刷新风暴 |

### 待合并的高优先级 PR

- [#134803](https://github.com/openclaw/openclaw/pull/134803) — Telegram + Claude CLI 的 compaction 进度显示与 final message 优先投递
- [#127999](https://github.com/openclaw/openclaw/pull/127999) — `doctor` 在 cron store 被其他进程更新后拒绝写入，防止静默数据丢失
- [#134819](https://github.com/openclaw/openclaw/pull/134819) — 修复 requester 解析期间意外驱逐 MCP runtime
- [#134589](https://github.com/openclaw/openclaw/pull/134589) — 修复 heartbeat 关闭时 one-shot main-session cron 任务被静默跳过的问题
- [#134758](https://github.com/openclaw/openclaw/pull/134758) — 修复 `agents.ownership="explicit"` 场景下 doctor 迁移不持久化的问题（关联 #133984）
- [#134818](https://github.com/openclaw/openclaw/pull/134818) — Memory Core dreaming cron 在插件热重载后丢失 reconcile 状态

---

## 4. 社区热点

### 评论数 Top Issues（含已关闭）

| Issue | 标题 | 评论 | 状态 | 链接 |
|-------|------|------|------|------|
| #45740 | gh-issues skill 将未 sanitization 的 issue body 直接注入子 agent prompt | 17 | ✅ Closed | [链接](https://github.com/openclaw/openclaw/issues/45740) |
| #96834 | WhatsApp 1:1 发送图片导致消息通道阻塞 ~3 分钟，multimodal run 陷入 `active_reply_work` 僵局 | 14 | 🔵 Open | [链接](https://github.com/openclaw/openclaw/issues/96834) |
| #85030 | MCP tools 注册后在 `sessions_spawn` 子 agent 中完全不可见 | 12 | 🔵 Open | [链接](https://github.com/openclaw/openclaw/issues/85030) |
| #53763 | 内置无头浏览器作为一等公民工具的需求 | 10 | 🔵 Open | [链接](https://github.com/openclaw/openclaw/issues/53763) |
| #97616 | 子进程（hook/tool）泄漏导致 zombie 积累，运行时退化 | 10 | 🔵 Open | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| #126360 | `agents.ownership: explicit` 模式下 `AgentSelectionRequiredError` 洪水日志 | 10 | 🔵 Open | [链接](https://github.com/openclaw/openclaw/issues/126360) |

**热点分析：**
- **#45740**（安全类）已被关闭，说明维护者认可"未信任内容不应直接注入子 agent prompt"的安全原则，预计将引入结构化隔离层。
- **#96834** 和 **#85030** 均为 P1 级别，分别涉及多模态处理链路和 MCP 工具传播，是生产部署中高频踩坑点，社区期待在下个 beta 中有实质性推进。
- **#53763** 长期呼声最高的功能需求之一，内置 Chromium 将消除用户对第三方 API/本地 Chrome 的依赖。

---

## 5. Bug 与稳定性

### 严重 Bug（P0/P1）

| Issue | 描述 | 状态 | Fix PR | 链接 |
|-------|------|------|--------|------|
| #107133 | Memory Core `embedding_cache` 冲突永久阻止 Gateway 启动 | ✅ Closed | — | [链接](https://github.com/openclaw/openclaw/issues/107133) |
| #133813 | 2026.8.1 升级后 Gateway crash-loop，`doctor --fix` 被 `ExecApprovalsMigrationRequiredError` 阻塞 | ✅ Closed | — | [链接](https://github.com/openclaw/openclaw/issues/133813) |
| #103076 | 更多 legacy-state migration sources 阻止启动（Matrix、Memory Core、Codex sidecar） | ✅ Closed | — | [链接](https://github.com/openclaw/openclaw/issues/103076) |
| #102006 | `exec` 工具中止后同一会话内后续 exec 调用永久挂起（PR #94412 回归） | ✅ Closed | — | [链接](https://github.com/openclaw/openclaw/issues/102006) |
| #133347 | 2026.8.1 迁移将有效 cron 任务误标为 `invalid-schedule` 并静默丢弃 | ✅ Closed | — | [链接](https://github.com/openclaw/openclaw/issues/133347) |
| #133999 | `doctor --fix` 陷入循环：提示运行自身但无法完成 legacy exec approvals 迁移 | ✅ Closed | — | [链接](https://github.com/openclaw/openclaw/issues/133999) |
| #134445 | 零字节 attestation 文件导致 `doctor --fix` 无法完成 legacy workspace 迁移 | ✅ Closed | — | [链接](https://github.com/openclaw/openclaw/issues/134445) |
| #96834 | WhatsApp 图片导致主通道阻塞 ~3 分钟 | 🔵 Open | — | [链接](https://github.com/openclaw/openclaw/issues/96834) |
| #85030 | MCP 工具未在 sessions_spawn 子 agent 中注入 | 🔵 Open | — | [链接](https://github.com/openclaw/openclaw/issues/85030) |
| #97616 | 子进程泄漏（hook/tool）导致 zombie 积累 | 🔵 Open | — | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| #124343 | `yield-owned settle-wake` 导致已完成子 agent 永久 park，无投递、无重试、无记录 | 🔵 Open | — | [链接](https://github.com/openclaw/openclaw/issues/124343) |
| #115424 | Gateway V8 heap OOM，restart-recovery 将单次崩溃转化为 7-core-dump 循环 | 🔵 Open | — | [链接](https://github.com/openclaw/openclaw/issues/115424) |
| #132765 | `agents_wait` 忽略 `timeoutSeconds`，约 60s 后以工具错误终止 | 🔵 Open | — |

---

## 横向生态对比



# 2026-09-01 AI 智能体开源生态横向对比分析报告

## 1. 生态全景

2026年9月，个人 AI 助手与自主智能体开源生态呈现**高活跃分化**态势：头部项目（OpenClaw、CoPaw、NanoClaw、ZeroClaw）保持日均数十至数百条 Issue/PR 的处理量，进入密集修复与架构演进期；安全与稳定性成为跨项目共同焦点，WhatsApp/Telegram 渠道可靠性、MCP 工具链健壮性、子进程/容器隔离是集体攻关方向。项目间技术路线出现分化——OpenClaw/Zeroclaw 偏重 Agent 运行时与协议层抽象，NanoBot/Moltis 聚焦渠道体验与执行安全，CoPaw 加速多租户企业化路径。生态整体从"功能竞赛"过渡到"质量巩固+场景深化"阶段。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | Release | 健康度 | 核心状态 |
|------|-------------|-----------|---------|--------|----------|
| **OpenClaw** | 480 条更新 | 500 条更新 | 无 | 🟡 高密度修复期 | P0/P1 启动、迁移、多模态阻塞问题集中关闭，仍有核心缺陷待解决 |
| **CoPaw** | 15 新/活跃, 14 关闭 | 39 条（16 合并） | v2.2.0-beta.4/5 | 🟢 高活跃迭代 | 多租户规划讨论热烈，稳定性修复响应迅速，测试覆盖冲刺中 |
| **ZeroClaw** | 25 活跃 | 50 待合并（0 合并） | 无 | 🟡 高活跃 Review 瓶颈 | 架构 RFC 密集，P0 配置保存缺陷浮出，WASM 生态活跃 |
| **NanoClaw** | 50 更新（9 新） | 34 条（16 合并） | 无 | 🟢 清理加固阶段 | WhatsApp/Signal 通道可靠性问题集中，治理基建（CI/模板）推进 |
| **LobsterAI** | 11 更新（5 新） | 27 条（11 合并） | 无 | 🟡 中等活跃 | 安全加固优先，Plan mode 积分争议需回应，electron 升级阻塞 |
| **IronClaw** | 14 新增 | 20 条（5 合并） | 无 | 🟡 中等活跃 | MCP 大目录发现链路阻塞，Design System 分阶段推进 |
| **NanoBot** | 6 条（3:3） | 18 条（10 合并） | 无 | 🟢 良好 | 无 P0 级问题，上下文重构+渠道体验优化双主线清晰 |
| **ZeptoClaw** | 8 新增（全安全） | 1 合并 | 无 | 🟡 安全整顿期 | RustSec 漏洞修复后进入系统性安全审计，P1-critical 子进程隔离待修 |
| **Moltis** | 2 条 | 4 条（3 合并） | 20260831.01 | 🟢 稳定迭代 | 安全加固+执行路径修复，K8s 沙箱需求长期跟踪 |
| **PicoClaw** | 活跃中等 | 5 条（1 修复） | 无 | 🟡 中等活跃 | Telegram 动画生命周期 Bug 修复，多渠道扩展并行 |
| **NullClaw** | 0 | 1（Dependabot） | 无 | 🔴 低活跃维护 | 核心贡献停滞，PR 积压超 2 月 |

---

## 3. OpenClaw 在生态中的定位

**规模与影响力**：OpenClaw 以日均 480+ Issue / 500+ PR 更新量位居生态首位，社区规模显著领先，是事实上的"参考实现"与问题风向标。

**技术路线差异**：
- 与 **NanoClaw** 同源但更偏 Gateway 层抽象与多 Agent 编排，NanoClaw 更侧重 Skill 整合与通道适配
- 与 **ZeroClaw** 均重视架构 RFC 治理，但 ZeroClaw 更激进地推进 WASM 插件生态与 eval 系统
- 与 **CoPaw** 相比，OpenClaw 更偏通用运行时，CoPaw 绑定 Qwen 模型栈并加速多租户商业化
- 与 **IronClaw** 共享"Design System + MCP 可靠性"关注点，但 IronClaw 更聚焦 WebUI 前端与工具发现链路

**社区规模对比**（基于 Issue/PR 吞吐估算）：
OpenClaw ≈ 10× CoPaw ≈ 5× NanoClaw ≈ 3× IronClaw > NanoBot ≈ Moltis > ZeptoClaw > PicoClaw >> NullClaw

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **多渠道通道可靠性** | OpenClaw, NanoClaw, PicoClaw, LobsterAI, ZeroClaw | WhatsApp 多模态阻塞、Telegram 富消息/动画生命周期、Signal 断开丢消息、Cron 投递噪音 |
| **MCP 工具链健壮性** | OpenClaw, NanoClaw, IronClaw, ZeroClaw | MCP 工具注入失效、大型目录发现阈值、schema 约束丢失、hosted-MCP 容错 |
| **执行隔离与安全** | ZeptoClaw, Moltis, ZeroClaw, LobsterAI | 子进程环境隔离、WASM 出站策略、容器镜像权限收窄、命令注入加固 |
| **上下文/记忆管理** | NanoBot, CoPaw, ZeroClaw | 长对话 Token 效率、Memory 可插拔召回、上下文压缩自适应、Embedding 重建可控性 |
| **本地模型支持** | NanoClaw, ZeroClaw, Moltis | 本地 OAI 兼容服务器长 turn 不被杀、Hailo-Ollama 原生支持、Ollama 集成 |
| **企业化/多租户** | CoPaw, NanoBot | QwenPaw Hub 多租户架构、Cron 批量归档、自定义 Bot API Base URL |

---

## 5. 差异化定位分析

| 维度 | OpenClaw | NanoClaw | CoPaw | ZeroClaw | NanoBot | IronClaw | Moltis | ZeptoClaw |
|------|----------|----------|-------|----------|---------|----------|--------|-----------|
| **功能侧重** | 通用 Agent 运行时 + 多通道网关 | Skill 生态 + 通道适配 | Qwen 模型栈 + 多租户 Hub | WASM 插件 + Eval 系统 | 轻量 Agent + 上下文重构 | Design System + MCP 工具发现 | 安全执行沙箱 + K8s | RustSec 安全基线 |
| **目标用户** | 广泛开发者/企业 | Skill 开发者 | 阿里云/Qwen 用户 | 插件生态贡献者 | 个人开发者 | 前端/设计系统参与者 | 高安全场景 | 安全合规敏感项目 |
| **技术架构** | Gateway + Agent Bindings + MCP | Skill-first + Channel adapters | Desktop + Cloud Hub + ReMe Memory | WASM runtime + Observer pattern | Rust + Telegram/Feishu focus | WebUI-first + Design tokens | K8s/Docker sandbox + Auth | Rust + CI/CD 安全扫描 |
| **发布节奏** | 无版本，PR 累积 | 无版本 | 高频 beta（日级） | 无版本，RFC 驱动 | 无版本 | 无版本 | 周级 patch | 无版本，安全审计驱动 |

---

## 6. 社区热度与成熟度

**🔥 快速迭代阶段**（日级发布/高频 PR 吞吐）：
- **CoPaw**：连续发布 beta，测试覆盖冲刺，多租户讨论热烈
- **OpenClaw**：480+ Issue/500+ PR 日吞吐，密集修复期，架构 RFC 并行

**🟢 质量巩固阶段**（稳定修复+治理基建）：
- **NanoClaw**：大量历史 Issue 清理关闭，CI 模板/changelog 自动化落地，Skill 整合
- **IronClaw**：Design System 分阶段推进，MCP 发现链路修复，CI 稳定性提升
- **Moltis**：安全加固+执行修复同步，版本迭代节奏稳定

**🟡 安全整顿阶段**（问题集中暴露+响应）：
- **ZeptoClaw**：系统性安全审计，8 个 RustSec 漏洞修复，6 个 P1/High 安全 Bug 待修
- **LobsterAI**：MCP 命令注入加固，但 electron 升级与积分争议需关注

**🟢 稳健发展阶段**（低阻塞+清晰方向）：
- **NanoBot**：无 P0 问题，上下文重构+渠道体验双主线，贡献者聚焦
- **ZeroClaw**：高活跃度但 Review 瓶颈，架构 RFC 密集，P0 配置缺陷需优先处理

**🔴 低活跃维护**：
- **NullClaw**：24 小时零动态，PR 积压超 2 月，建议关注维护者响应

---

## 7. 值得关注的趋势信号

### 1. 渠道可靠性成为生产部署首要门槛
OpenClaw（WhatsApp 多模态阻塞 #96834）、NanoClaw（WhatsApp mention 失效 #3085、Signal 断开丢消息 #3693）、PicoClaw（Telegram 动画无限编辑 #3343）、LobsterAI（DSH 推理强度缺失 #2577）共同暴露：**多通道适配的稳定性已超越单通道功能丰富性**，成为用户选择框架的核心考量。建议开发者优先评估目标渠道的边界场景覆盖率。

### 2. MCP 生态进入"规模瓶颈"期
IronClaw（47k 工具目录不可搜索 #8012）、OpenClaw（MCP 工具注入失效 #85030）、NanoClaw（shared-skills stale 副本 #3001）共同指向：**MCP 工具数量增长已触及发现与注入链路的工程极限**。未来 1-2 个版本，工具发现优化、schema 保真、目录分片将成为关键差异化能力。

### 3. 安全从"附加项"变为"架构 First"
ZeptoClaw（6 个安全 Bug 同日暴露）、Moltis（PR #1221/#1222 安全加固）、LobsterAI（MCP 命令注入 #2590）、ZeroClaw（WASM 出站策略 #9582）表明：**安全审查已从发布后补救转向设计阶段约束**。建议新项目在建构初期即纳入 least-privilege、常量时间比较、环境变量隔离等安全原语。

### 4. 本地模型支持从"可行"到"可用"的 gap
NanoClaw（30 分钟硬编码超时杀本地模型 turn #3643）、Moltis（Ollama 本地模型无法使用 #1635 stale）、ZeroClaw（Hailo-Ollama 原生支持 #9109）显示：**本地推理场景的工程化支持仍薄弱**，特别是长 turn 调度、资源隔离、超时配置等细节。这是差异化竞争的重要机会点。

### 5. 多租户/企业化路径加速显现
CoPaw（QwenPaw Hub 多租户讨论 #7318，15 评论）、NanoBot（Cron 批量归档 #5513、自定义 Bot API #4919）表明：**个人助手向团队协作的演进已启动**，但技术路径尚未收敛。预期 2026 年 Q4 将出现更多多租户原型与商业化探索。

### 6. Eval 系统与可观测性成为新基建
ZeroClaw（5 个 eval PR 堆叠：#9248/#9245/#9244/#9225/#9224）、CoPaw（Agent stats 测试对齐 TC-AGT-06）显示：**Agent 质量评估从"手工验证"转向"自动化 eval 流水线"**。这是框架成熟度的重要标志，建议开发者关注 eval 结果的可追溯性与 judge 校准机制。

---

**报告生成时间**：2026-09-01  
**分析师**：Agnes (Sapiens AI)

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-09-01

---

## 1. 今日速览

过去 24 小时内，NanoBot 保持高活跃度，共处理 24 条更新（6 Issues + 18 PRs），其中 10 条 PR 已合并/关闭，8 条仍处于待审状态，Issue 开闭比均衡（3:3），表明社区反馈与问题闭环速度较为同步。项目整体健康度良好，无阻塞性回归或 P0 级崩溃报告。今日贡献者以 `chengyongru`、`xiexiahao`、`nolanchic` 为核心，聚焦于 Agent 上下文管理重构、Telegram 流式富消息修复及 Cron 任务投递可配置化三个方向，技术栈推进方向清晰。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（10 条）

| PR | 作者 | 类型 | 摘要 |
|----|------|------|------|
| [#5617](https://github.com/HKUDS/nanobot/pull/5617) | Krislu1221 | Bug Fix (P1) | 修复 WebSocket 健康检查中 `SO_ACCEPTCONN` 的非移植性问题，解决 macOS/BSD 下误报关闭的问题 |
| [#5615](https://github.com/HKUDS/nanobot/pull/5615) | linhongyu510 | 新功能 | 支持 `RuntimeContextBlock` 的 `ephemeral` 生命周期，默认保持持久化行为不变 |
| [#5619](https://github.com/HKUDS/nanobot/pull/5619) | xiexiahao | 新功能 | 允许 Context Block 选择退出历史记录持久化，关闭 [#5586](https://github.com/HKUDS/nanobot/issues/5586) |
| [#5531](https://github.com/HKUDS/nanobot/pull/5531) | nolanchic | Bug Fix | 修复 Telegram `rich_messages` 与 `streaming` 同时启用时富消息无法渲染的问题 |
| [#5612](https://github.com/HKUDS/nanobot/pull/5612) | chengyongru | 重构 (P1) | 统一 AgentRunner 的请求适配逻辑，包含工具调用重试和无工具最终化场景 |
| [#5608](https://github.com/HKUDS/nanobot/pull/5608) | chengyongru | 重构 | 将 Transcript 组装延迟至 Runner，在模型执行前即时调用 ContextBuilder |
| [#5618](https://github.com/HKUDS/nanobot/pull/5618) | chengyongru | 样式 | 简化 TUI 运行时头部显示，移除装饰性分隔符，仅展示激活的 Preset |
| [#5598](https://github.com/HKUDS/nanobot/pull/5598) | dajiaohuang | 文档 | 明确 `edit_file` 工具的 `occurrence`/`line_hint`/`replace_all` 互斥性 |
| [#5604](https://github.com/HKUDS/nanobot/pull/5604) | LWT1212 | 文档 | 补充 `edit_file` 参数互斥说明，修复文档与运行时行为的偏差 |
| [#5610](https://github.com/HKUDS/nanobot/pull/5610) | chengyongru | 重构 | 使 Memory 摘要变为累积式替换检查点，保留前一检查点与新内容 |
| [#5513](https://github.com/HKUDS/nanobot/issues/5513) | yrxeva | Issue 关闭 | Cron 结果投递可配置通道 + 批量归档需求已闭环 |

**整体推进评估**：今日以 Agent 上下文生命周期管理与 Telegram 渠道稳定性修复为主轴，`chengyongru` 主导的上下文压缩重构（PR #5612 / #5608 / #5610）形成一套连贯的设计，预计将显著改善长对话场景下的 Token 效率与响应稳定性。Telegram 富消息渲染问题的修复消除了一个长期存在的功能缺失。

---

## 4. 社区热点

### 高关注度 Issue / PR

| 标题 | 状态 | 评论数 | 链接 | 热度分析 |
|------|------|--------|------|----------|
| 飞书多轮回复整合为单条流式卡片 | [OPEN](https://github.com/HKUDS/nanobot/issues/5567) | 3 | [#5567](https://github.com/HKUDS/nanobot/issues/5567) | 飞书用户体验痛点明确，用户期望保持"一问一答"的对应关系，当前多消息散列问题突出 |
| MCP Apps Host 支持 WebUI | [OPEN](https://github.com/HKUDS/nanobot/issues/5251) | 3 | [#5251](https://github.com/HKUDS/nanobot/issues/5251) | MCP 生态扩展需求，涉及官方 UI 扩展协议，技术方向与社区 MCP 热潮吻合 |
| Telegram 流式富消息 PR | [OPEN](https://github.com/HKUDS/nanobot/pull/5614) | — | [#5614](https://github.com/HKUDS/nanobot/pull/5614) | 作者主动跟进，计划本周 Review，与已合并的 #5531 形成互补 |
| 自定义 Bot API Base URL | [OPEN](https://github.com/HKUDS/nanobot/pull/4919) | — | [#4919](https://github.com/HKUDS/nanobot/pull/4919) | 企业/自托管场景刚需，长期未合并且标有 conflict，需维护者协调 |
| MST 元搜索 Provider 集成 | [OPEN](https://github.com/HKUDS/nanobot/pull/5234) | — | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | 多引擎聚合搜索方案，RRF 融合策略较有技术价值，但标签含 conflict |

**热点背后诉求分析**：社区最集中的方向是**多渠道体验优化**（飞书卡片整合、Telegram 富消息流式支持）和**企业级部署能力**（自定义 Bot API、Cron 批量归档），反映用户群体正从个人开发者向团队协作场景延伸。

---

## 5. Bug 与稳定性

| 严重度 | 问题 | 状态 | 关联 PR | 链接 |
|--------|------|------|---------|------|
| 🔴 P1 | WebSocket 健康检查在非 POSIX 系统误判端口状态 | 已修复 | [#5617](https://github.com/HKUDS/nanobot/pull/5617) | [#5617](https://github.com/HKUDS/nanobot/pull/5617) |
| 🟡 P2 | Telegram 富消息在流式模式下始终降级为 legacy HTML | 已修复 | [#5531](https://github.com/HKUDS/nanobot/pull/5531) | [#5516](https://github.com/HKUDS/nanobot/issues/5516) |
| 🟡 P2 | `edit_file` 文档与运行时行为不一致（参数互斥性未声明） | 已修复（文档） | [#5598](https://github.com/HKUDS/nanobot/pull/5598), [#5604](https://github.com/HKUDS/nanobot/pull/5604) | [#5592](https://github.com/HKUDS/nanobot/issues/5592) |

**稳定性评估**：今日无新增 Bug，所有已知 P1/P2 问题均有对应修复或文档补全，项目稳定性处于良好状态。

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 优先级 | 纳入下一版本可能性 |
|------|----------|--------|-------------------|
| MCP Apps Host 支持 WebUI | [#5251](https://github.com/HKUDS/nanobot/issues/5251) | 中 | ⭐⭐⭐ 高 — 与 MCP 生态趋势高度契合，已有技术路径 |
| 飞书多轮消息整合为流式卡片 | [#5567](https://github.com/HKUDS/nanobot/issues/5567) | 高 | ⭐⭐⭐ 高 — 用户痛点明确，技术路径清晰（CardKit 已有基础） |
| 非 WebUI 会话级沙箱隔离 | [#5283](https://github.com/HKUDS/nanobot/pull/5283) | P2 | ⭐⭐ 中 — 安全增强方向正确，但需充分测试 |
| 可配置 Cron 投递 + 批量归档 | [#5620](https://github.com/HKUDS/nanobot/pull/5620) [OPEN] | P2 | ⭐⭐⭐ 高 — 与已关闭的 [#5513](https://github.com/HKUDS/nanobot/issues/5513) 直接对应，实现已就绪 |
| Memory 可插拔召回后端 | [#5570](https://github.com/HKUDS/nanobot/pull/5570) | P2 | ⭐⭐ 中 — 架构扩展性强，但需评估对现有 Memory 模块的影响 |
| 默认显式召回 Memory | [#5571](https://github.com/HKUDS/nanobot/pull/5571) | P1 | ⭐⭐ 中 — 与 #5570 配套，涉及行为变更，需谨慎灰度 |
| MST 元搜索 Provider | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | P1 | ⭐⭐ 中 — 技术价值明确，但 conflict 状态需解决 |
| HTML/.txt/.md 文档预览 | [#5493](https://github.com/HKUDS/nanobot/issues/5493) | P2 | ⭐⭐ 中 — iframe+srcdoc 方案简单可行，社区呼声低但无冲突 |

---

## 7. 用户反馈摘要

### 核心痛点

1. **飞书多渠道消息割裂**（[#5567](https://github.com/HKUDS/nanobot/issues/5567)）：用户在飞书中收到工具提示、进度消息、最终回复等多条分离消息，破坏"一问一答"体验。`send_delta()` 流式卡片已有基础，但工具调用阶段仍使用 `send()` 发送独立消息，整合工作已提上日程。

2. **Telegram 富消息与流式互斥**（[#5516](https://github.com/HKUDS/nanobot/issues/5516)）：`rich_messages: true` 与 `streaming: true`（默认值）无法共存，最终消息始终降级为 HTML `editMessageText`，导致格式丢失。该问题已通过 [#5531](https://github.com/HKUDS/nanobot/pull/5531) 修复，[#5614](https://github.com/HKUDS/nanobot/pull/5614) 将进一步支持流式富消息。

3. **Cron 任务噪音污染个人会话**（[#5513](https://github.com/HKUDS/nanobot/issues/5513)）：自动化任务结果默认投递到创建会话，与个人对话混合，且缺乏批量管理能力。已关闭并提出 PR #5620 实现可配置投递与归档。

4. **`edit_file` 工具文档歧义**（[#5592](https://github.com/HKUDS/nanobot/issues/5592)）：参数互斥性未文档化，导致用户误用时报错困惑。已通过双 PR 补全文档说明。

### 满意度信号

- WebSocket 跨平台兼容性改进获认可（[#5617](https://github.com/HKUDS/nanobot/pull/5617)）
- TUI 头部简化提升可读性（[#5618](https://github.com/HKUDS/nanobot/pull/5618)）
- Memory 累积摘要重构预计改善长对话上下文管理（[#5610](https://github.com/HKUDS/nanobot/pull/5610)）

---

## 8. 待处理积压

| 类型 | ID | 标题 | 创建时间 | 状态 | 建议 |
|------|-----|------|----------|------|------|
| PR | [#5283](https://github.com/HKUDS/nanobot/pull/5283) | 非 WebUI 会话级沙箱隔离 | 2026-08-07 | OPEN | 安全增强，待 Review，建议优先处理 |
| PR | [#4919](https://github.com/HKUDS/nanobot/pull/4919) | Telegram 自定义 Bot API Base URL | 2026-07-14 | OPEN (conflict) | 企业部署刚需，需解决冲突后合并 |
| PR | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | MST 元搜索 Provider | 2026-08-03 | OPEN (conflict) | 多引擎搜索增强，需协调冲突 |
| PR | [#5620](https://github.com/HKUDS/nanobot/pull/5620) | Cron 可配置投递与批量归档 | 2026-09-01 | OPEN | 刚创建，关联已关闭 Issue #5513，预计近期可合并 |
| PR | [#5570](https://github.com/HKUDS/nanobot/pull/5570) | Memory 可插拔召回后端 | 2026-08-27 | OPEN (conflict) | 架构扩展，与 #5571 配套，需评估冲突 |
| PR | [#5571](https://github.com/HKUDS/nanobot/pull/5571) | 默认显式召回 Memory | 2026-08-27 | OPEN (conflict) | 行为变更，需谨慎灰度策略 |
| Issue | [#5251](https://github.com/HKUDS/nanobot/issues/5251) | MCP Apps Host 支持 WebUI | 2026-08-05 | OPEN | 生态扩展需求，建议纳入路线图评估 |
| Issue | [#5567](https://github.com/HKUDS/nanobot/issues/5567) | 飞书多轮消息整合 | 2026-08-27 | OPEN | 用户体验痛点，建议排期实现 |
| Issue | [#5493](https://github.com/HKUDS/nanobot/issues/5493) | 文档预览（HTML/txt/md） | 2026-08-23 | OPEN | 低复杂度增强，可快速落地 |

**维护者关注建议**：
- `#4919` 和 `#5234` 均带有 conflict 标记且已开放超 2 周，建议尽快协调合并或关闭
- `#5283` 沙箱隔离功能对多用户场景至关重要，建议优先 Review
- `#5567` 飞书整合需求强烈，可考虑与 Telegram 流式富消息修复同步推进

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期：2026-09-01 | 分析周期：过去24小时**

---

## 1. 今日速览

PicoClaw 今日整体活跃度中等，聚焦于修复 Telegram 渠道的核心 Bug。Issue #3343 暴露的 tool feedback animation 无限编辑问题已引发社区关注，作者 linhongyu510 在同日提交了修复 PR #3353，响应速度值得肯定。另有4个 PR 处于待审状态，涵盖 Exa 搜索集成、Build Remote Agent 配对、deltachat 重构及 IRCv3 多行消息支持。项目暂无新版本发布，整体处于稳定修复与功能迭代并行的阶段。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已关闭 PR
- **#3299** [stale] Add native Exa web search provider — 作者 kesku 提交的 Exa 原生搜索集成 PR 因长期无活动被标记 stale 并关闭。虽然 Exa API 的完整实现已暂告段落，但该 PR 为后续搜索 provider 扩展提供了参考模板。
  - [链接](https://github.com/sipeed/picoclaw/pull/3299)

### 已合并/修复
- **#3353** [OPEN] fix(channels): bound tool feedback animations — 作者 linhongyu510 直接针对 Issue #3343 提交的修复 PR。将 tool feedback animation 的生命周期限制在5分钟内（与 Telegram typing feedback 保持一致），并在首次编辑失败后立即停止，而非无限重试。该 PR 已修复核心 Bug，等待合并后发布。
  - [链接](https://github.com/sipeed/picoclaw/pull/3353)

### 待审 PR
- **#3344** [stale] Add Build Remote Agent phone pairing — 添加 gbr/1 协议的手机配对适配器，允许手机作为 Remote Agent 的 spectator 端。
  - [链接](https://github.com/sipeed/picoclaw/pull/3344)
- **#3222** [OPEN] refactor(deltachat): cleanup implementation, documentation -200LOC — 清理 deltachat 模块，删除遗留功能、过时测试，重命名配置项，并引用官方 relay 列表。
  - [链接](https://github.com/sipeed/picoclaw/pull/3222)
- **#3354** [OPEN] feat(irc): assemble IRCv3 multiline messages — 添加 IRCv3 `draft/multiline` 接收支持，使长消息或换行消息能作为完整 inbound 消息处理。
  - [链接](https://github.com/sipeed/picoclaw/pull/3354)

> **整体评估**：项目向前推进约 **1个核心 Bug 修复 + 4个功能/重构 PR 待审**，代码质量与稳定性有所提升。

---

## 4. 社区热点

### 最活跃 Issue
- **#3343** [BUG] Tool feedback animation can edit a Telegram message indefinitely — 2条评论，0赞。该 Issue 描述了一个严重问题：tool feedback animation 在 agent turn 停止后仍每3秒调用 `editMessageText`，持续数天产生 **228,000+ 次编辑尝试**，触发 Telegram 服务端速率限制。
  - [链接](https://github.com/sipeed/picoclaw/issues/3343)

### 相关 PR（修复）
- **#3353** 已针对该 Issue 提交修复，作者同一人（linhongyu510），显示出作者对自身提交问题的快速响应。

**诉求分析**：用户关注 Telegram 渠道的稳定性，尤其是对长时间运行的 agent turn 中动画生命周期的管理。该 Bug 暴露了资源清理逻辑的缺陷，社区期待更完善的 lifecycle 管理。

---

## 5. Bug 与稳定性

### 已知 Bug（按严重程度排列）

| 级别 | Issue/PR | 描述 | 状态 |
|------|----------|------|------|
| 🔴 高 | [#3343](https://github.com/sipeed/picoclaw/issues/3343) | Tool feedback animation 无限编辑 Telegram 消息，触发服务端限速 | 已修复 (PR #3353 待合并) |

> **备注**：目前无新报告崩溃或回归问题。#3353 合并后，上述 Bug 将得到修复。

---

## 6. 功能请求与路线图信号

| 功能 | PR | 状态 | 纳入下一版本可能性 |
|------|-----|------|------------------|
| Exa 原生 web 搜索 | [#3299](https://github.com/sipeed/picoclaw/pull/3299) | 已关闭 (stale) | ⚠️ 低（需重新激活） |
| Build Remote Agent 配对 (gbr/1) | [#3344](https://github.com/sipeed/picoclaw/pull/3344) | 开放 (stale) | ⚠️ 中（需维护者跟进） |
| deltachat 重构与清理 | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | 开放 | ✅ 高（代码质量改进） |
| IRCv3 多行消息支持 | [#3354](https://github.com/sipeed/picoclaw/pull/3354) | 开放 | ✅ 高（新功能，无 stale 标记） |

> **路线图文信号**：项目正逐步扩展渠道支持（IRCv3）并清理遗留代码（deltachat），同时尝试集成更多搜索 provider（Exa）。

---

## 7. 用户反馈摘要

### 痛点
- **Telegram 渠道稳定性差**：Issue #3343 反映了 tool feedback animation 生命周期管理缺陷，导致大量无效 API 调用并触发服务端限速，严重影响用户体验。
- **长时间运行任务缺乏兜底**：agent turn 停止后动画未正确清理，暴露了错误处理与资源释放的盲区。

### 满意点
- **快速响应**：Issue 提交后同日即有修复 PR，显示作者对问题的重视。
- **功能扩展活跃**：IRCv3 多行消息、Build Remote Agent 配对等功能 PR 表明社区持续参与项目发展。

---

## 8. 待处理积压

| 类型 | ID | 标题 | 状态 | 建议 |
|------|-----|------|------|------|
| PR | [#3299](https://github.com/sipeed/picoclaw/pull/3299) | Add native Exa web search provider | stale / closed | 如需继续，建议重新打开或分阶段提交 |
| PR | [#3344](https://github.com/sipeed/picoclaw/pull/3344) | Add Build Remote Agent phone pairing | stale / open | 建议维护者评估并给出反馈 |
| PR | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | refactor(deltachat): cleanup | open | 建议优先审阅，清理工作有助于长期维护 |
| Issue | [#3343](https://github.com/sipeed/picoclaw/issues/3343) | Tool feedback animation bug | 待修复合并 | 确认 PR #3353 合并后关闭 |

> **维护者关注点**：PR #3299 和 #3344 均已标记 stale，建议尽快给出明确反馈（合并/关闭/要求更新），避免社区贡献者体验受挫。

---

**报告生成时间**：2026-09-01  
**数据来源**：PicoClaw GitHub (github.com/sipeed/picoclaw)  
**分析师**：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-09-01

---

## 1. 今日速览

NanoClaw 昨日保持**高活跃度**：过去24小时内产生 50 条 Issue 更新（新开/活跃 9 条、关闭 41 条）和 34 条 PR 更新（待合并 18 条、已合并/关闭 16 条）。项目无新版本发布，但核心维护者在 CI 基础设施、Skill 整合、容器调度等多个方向推进了实质性修复与重构。整体来看，项目进入"清理+加固"阶段：大量历史 skill 分支的 merge-forward 失败问题集中关闭，同时多项长期存在的 container 和 channel 级别 bug 进入修复通道。

---

## 2. 版本发布

**无新版本发布**（0 releases）。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 概要 |
|----|------|------|
| [#3695](https://github.com/nanocoai/nanoclaw/pull/3695) | Feature/Skill | Slack agents companion skills 移入主仓库，`main` 成为 canonical home，消除外部 branch fetch 依赖 |
| [#3657](https://github.com/nanocoai/nanoclaw/pull/3657) | Hardening | CI-04 引入 template-compliance 报告-only 状态，帮助维护者快速识别 PR 模板合规问题 |
| [#3648](https://github.com/nanocoai/nanoclaw/pull/3648) | Docs/CI | PR 模板 v2 上线，包含 token parsing 和 managed-kind reconcile |
| [#3650](https://github.com/nanocoai/nanoclaw/pull/3650) | Feature/Release | 新增 release-note block 采集功能，自动从 PR 提取 changelog 条目 |
| [#3647](https://github.com/nanocoai/nanoclaw/pull/3647) | CI | 自动从变更路径推断 `area/*` 标签，从 PR 类型推断 `kind/*` 标签 |
| [#3651](https://github.com/nanocoai/nanoclaw/pull/3651) | Docs | 新增 CONTRIBUTING.md Issues 章节，明确四种 issue 类型及处理流程 |
| [#3644](https://github.com/nanocoai/nanoclaw/pull/3644) | Docs | 新增 `.github/ISSUE_TEMPLATE/`，包含 bug report / skill 请求 / docs correction / security hardening 四类表单 |

**整体推进评估**：今日合并的 PR 主要集中在**治理基建**（CI 标签自动化、模板规范、changelog 采集）和**skill 整合**（Slack skills 移入主仓），反映出项目维护团队在规范化贡献流程和降低 skill 维护成本方面取得了实质性进展。

---

## 4. 社区热点

### 高关注度 Issue

| Issue | 状态 | 摘要 | 链接 |
|-------|------|------|------|
| [#3085](https://github.com/nanocoai/nanoclaw/issues/3085) | OPEN | WhatsApp `engage_mode=mention` 仅对 autocomplete mention pills 生效，手动输入 `@name` 文本无法触发，`accumulate` 策略掩盖了该失败 | [链接](https://github.com/nanocoai/nanoclaw/issues/3085) |
| [#3643](https://github.com/nanocoai/nanoclaw/issues/3643) | OPEN | 容器 sweep 硬编码 30 分钟绝对超时，导致本地模型长推理 turn 被强制杀死，无配置接口 | [链接](https://github.com/nanocoai/nanoclaw/issues/3643) |
| [#2997](https://github.com/nanocoai/nanoclaw/issues/2997) | OPEN | 定时任务重复发送时，`hasIdenticalSend` 匹配到历史发送记录，导致固定文本的 recurring reminder 仅在首次触发后永久静默 | [链接](https://github.com/nanocoai/nanoclaw/issues/2997) |
| [#3105](https://github.com/nanocoai/nanoclaw/issues/3105) | OPEN | WhatsApp Cloud 升级现有安装时，`messaging_groups` 行 stranded，缺少 instance re-key 迁移逻辑 | [链接](https://github.com/nanocoai/nanoclaw/issues/3105) |
| [#3694](https://github.com/nanocoai/nanoclaw/issues/3694) | CLOSED | Slack skills 安装后构建失败：`/add-slack` 的 copy list 遗漏 `slack-raw-text.ts`，payload lint 和容器套件均报错 | [链接](https://github.com/nanocoai/nanoclaw/issues/3694) |

### 活跃 PR

| PR | 状态 | 摘要 | 链接 |
|----|------|------|------|
| [#3646](https://github.com/nanocoai/nanoclaw/pull/3646) | OPEN | 修复 sweep 杀死慢本地模型 turn 的问题，使 idle timeout 可配置并统一应用于两个 kill 路径 | [链接](https://github.com/nanocoai/nanoclaw/pull/3646) |
| [#3691](https://github.com/nanocoai/nanoclaw/pull/3691) | OPEN | 隔离 git fixtures 与 operator 全局配置，修复开发者机器含全局 git config 时测试失败的问题 | [链接](https://github.com/nanocoai/nanoclaw/pull/3691) |
| [#3591](https://github.com/nanocoai/nanoclaw/pull/3591) | OPEN | 重构 providers：从 core 拥有的 canon 渲染 provider instructions | [链接](https://github.com/nanocoai/nanoclaw/pull/3591) |
| [#3693](https://github.com/nanocoai/nanoclaw/pull/3693) | OPEN | Signal adapter 断开时 outbound send 静默丢失问题修复：改为 queue 并在重新连接时 flush | [链接](https://github.com/nanocoai/nanoclaw/pull/3693) |

**热点分析**：社区反馈高度集中在**通道可靠性**（WhatsApp/Signal）和**本地模型长时间运行**两个痛点。`#3643`（30分钟超时硬编码）和 `#3646`（对应修复 PR）直接相关，反映用户对本地模型场景的期望与当前实现存在显著 gap。`#3085` 和 `#3105` 均指向 WhatsApp channel 的迁移/升级兼容性，说明该通道在存量用户中的稳定性亟待改善。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 领域 | 摘要 | Fix PR |
|--------|-------|------|------|--------|
| 🔴 High | [#3085](https://github.com/nanocoai/nanoclaw/issues/3085) | WhatsApp Channels | `engage_mode=mention` 手动输入不触发，`accumulate` 策略掩盖错误 | — |
| 🔴 High | [#2997](https://github.com/nanocoai/nanoclaw/issues/2997) | Scheduled Tasks | recurring reminder 第二次起静默失效 | — |
| 🔴 High | [#3105](https://github.com/nanocoai/nanoclaw/issues/3105) | WhatsApp Cloud | 升级现有安装导致 `messaging_groups` stranded | — |
| 🟠 Medium | [#3643](https://github.com/nanocoai/nanoclaw/issues/3643) | Containers | 30分钟硬编码超时杀死本地模型长 turn | [#3646](https://github.com/nanocoai/nanoclaw/pull/3646) [OPEN] |
| 🟠 Medium | [#2868](https://github.com/nanocoai/nanoclaw/issues/2868) | Skills | `/update-skills` 对已安装 channel 为 silent no-op，跳过代码/依赖刷新 | — |
| 🟠 Medium | [#3001](https://github.com/nanocoai/nanoclaw/issues/3001) | Skills | shared-skills 重构前创建的 group 持有 stale skill 副本，阻止 symlinks 更新 | — |
| 🟡 Low | [#3426](https://github.com/nanocoai/nanoclaw/issues/3426) | Tools | `send_card` 文档承诺 callback buttons，bridge 实际丢弃无 url 的 action | — |
| 🟡 Low | [#3248](https://github.com/nanocoai/nanoclaw/issues/3248) | Setup | `setup.sh` Node 版本检查分支无法处理"版本过旧"场景 | — |

**稳定性评估**：今日新增 9 条活跃 Issue，其中 3 条 High priority 全部涉及核心通道（WhatsApp）和任务调度可靠性，属于**直接影响生产使用**的稳定性问题。`#3643` 已有对应 PR 在审，预计近期可闭环。大量历史 merge-forward 失败 Issue（#892-#1279）今日集中关闭，属于自动化 bot 的旧报障清理。

---

## 6. 功能请求与路线图信号

| 类型 | 内容 | 关联 PR | 纳入下一版本可能性 |
|------|------|---------|-------------------|
| 新功能 | 本地免费语音转写 skill（支持 openai-whisper / whisper.cpp 双后端） | [#2317](https://github.com/nanocoai/nanoclaw/pull/2317) [OPEN] | ⭐⭐⭐ 高 — 与 Signal voice 支持形成互补 |
| 新功能 | Paws4Claws AWS 凭证代理 daemon 集成 | [#2634](https://github.com/nanocoai/nanoclaw/pull/2634) [OPEN] | ⭐⭐ 中 — 特定云场景需求，受众有限 |
| 改进 | Signal 群聊 typing 指示器、outbound reactions、quote-reply 修复 | [#2685](https://github.com/nanocoai/nanoclaw/pull/2685) [OPEN] | ⭐⭐⭐ 高 — 完善 Signal channel 体验 |
| 重构 | Provider 合同声明与实现（OpenCode、Codex、Host、Runtime） | [#3581-#3591](https://github.com/nanocoai/nanoclaw/pulls?q=is%3Apr+is%3Aopen+label%3Acore-team) [OPEN] | ⭐⭐⭐ 高 — 基础设施重构，为后续扩展铺路 |

**路线图信号**：当前重点在**Provider 抽象层重构**和**Skill 整合**，辅以 Signal/WhatsApp 通道的稳定性修复。本地语音转写和 AWS 凭证代理属于扩展性功能，尚未进入 core。

---

## 7. 用户反馈摘要

**核心痛点**：

1. **WhatsApp 通道可靠性不足**（#3085, #3105, #2868）：用户反映 `engage_mode=mention` 行为不符合预期，升级现有安装时出现数据 stranded 问题，`/update-skills` 对已安装 channel 无效。这些均指向**存量用户迁移路径存在缺陷**。

2. **本地模型长 turn 被误杀**（#3643）：30 分钟硬编码超时对使用本地推理后端（如 OpenCode + 本地 OAI 兼容服务器）的用户造成严重体验问题，长推理 turn 被 sweep 强制终止且无任何配置接口。

3. **CLI 静默行为引发困惑**（#2464）：`ncl` CLI 在 group scope 下静默覆盖用户显式传入的 `--agent-group-id`，无任何 stderr 提示，导致运维人员误判操作结果。

4. **Skill 安装后构建失败**（#3694）：按文档操作执行 `/add-slack` 后，遗漏文件导致 lint 和容器套件均失败，文档与实现存在偏差。

**用户满意点**：CI 模板 v2、changelog 自动采集、skill 移入主仓库等治理改进获得正面反馈（通过 PR 合并且无负面评论可见）。

---

## 8. 待处理积压

| Issue/PR | 状态 | 创建时间 | 风险说明 |
|----------|------|----------|----------|
| [#3085](https://github.com/nanocoai/nanoclaw/issues/3085) | OPEN | 2026-07-18 | WhatsApp mention 触发失效，已 44 天未修复，影响生产使用 |
| [#2997](https://github.com/nanocoai/nanoclaw/issues/2997) | OPEN | 2026-07-09 | recurring reminder 静默失败，已 53 天，无 fix PR |
| [#3105](https://github.com/nanocoai/nanoclaw/issues/3105) | OPEN | 2026-07-20 | WhatsApp Cloud 升级 stranded 问题，已 42 天，缺少 migration 逻辑 |
| [#3001](https://github.com/nanocoai/nanoclaw/issues/3001) | OPEN | 2026-07-10 | shared-skills 重构前 group 的 stale 副本阻塞更新，已 52 天 |
| [#3693](https://github.com/nanocoai/nanoclaw/pull/3693) | OPEN | 2026-08-31 | Signal disconnect 时消息丢失修复，今日提交待审查 |
| [#3646](https://github.com/nanocoai/nanoclaw/pull/3646) | OPEN | 2026-08-29 | 可配置 idle timeout 修复，今日活跃审查中 |

**维护者关注建议**：
- `#3085`、`#2997`、`#3105` 三个 High priority Issue 均已在库 6 周以上且无 fix PR，建议优先排期。
- `#3693` 和 `#3646` 两个 PR 今日提交，建议尽快完成 code review 以缩短循环时间。
- `#2868`（`/update-skills` no-op）和 `#3001`（stale skill 副本）属于同一类"升级路径"问题，可考虑合并处理。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目动态日报
**日期：2026-09-01 | 分析范围：过去 24 小时**

---

## 1. 今日速览

NullClaw 今日整体活跃度较低，过去 24 小时内无新 Issue 提交，亦无版本发布。唯一动态为一条由 Dependabot 自动发起的 Alpine 镜像版本升级 PR（#956），当前处于待合并状态。项目目前处于低活跃维护阶段，无重大功能推进或社区讨论热点。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

今日无已合并/关闭的 PR，项目核心功能代码无增量更新。

- **待合并 PR #956**：`ci(deps): bump alpine from 3.23 to 3.24`，由 Dependabot 自动提交，涉及 Docker 镜像依赖升级，目前状态为 OPEN，尚未合并。

---

## 4. 社区热点

今日无社区讨论热点。

- Issues 更新：0 条
- PR 评论互动：0 条活跃讨论

---

## 5. Bug 与稳定性

今日无新的 Bug 报告或稳定性问题反馈。

---

## 6. 功能请求与路线图信号

今日无新功能请求提交。项目路线图暂无新的社区输入信号。

---

## 7. 用户反馈摘要

今日无新的用户反馈或评论，无法提炼使用痛点或场景信息。

---

## 8. 待处理积压

| 类型 | 编号 | 标题 | 状态 | 创建日期 | 最后更新 | 链接 |
|------|------|------|------|----------|----------|------|
| PR | #956 | ci(deps): bump alpine from 3.23 to 3.24 in the docker-images group | OPEN | 2026-06-15 | 2026-08-31 | [PR #956](https://github.com/nullclaw/nullclaw/pull/956) |

> **提醒**：PR #956 自 2026-06-15 提交以来已等待超过两个月未合并，建议维护者评估 Dependabot 依赖升级的安全价值并尽快处理。

---

**项目健康度评估**：🟡 低活跃维护状态。核心贡献停滞，依赖更新积压，建议关注维护者响应速度及长期未合并 PR 的处理进展。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-09-01

## 1. 今日速览

IronClaw 今日保持中等活跃度：24小时内新增 14 条 Issue、20 条 PR，其中 5 条 PR 已合并/关闭，整体以 WebUI 设计系统推进和 MCP 工具发现链路修复为主线。项目无新版本发布，但 Epic #7781（Design System Phases 2–3）进入集成预览阶段（#8005），M3 Reskin（#8011）作为新 PR 补入。同时，MCP 大型目录发现（#8012/#8008/#8009）和 tool schema 约束丢失（#7987）两个稳定性问题引发关注，已有对应修复 PR（#7964、#7999）待审。整体项目健康度良好，核心贡献者活跃，但 MCP 生态相关的发现路径存在若干阻塞性 Bug。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

**今日合并/关闭的重要 PR：**

- **#7977** [CLOSED] `fix(loop)` — 修复 agent loop 在重复输出场景下无法终止的问题，恢复了被 #7531 移除的终止逻辑，解决生产运行中 593 次工具调用、70 分钟不终止的挂起问题。
- **#7992** [CLOSED] `ci: unify bounded integration execution` — 统一集成测试执行，固定 4 测试并发上限，移除冗余 shell 投影，提升 CI 稳定性。
- **#7995** [CLOSED] `fix(ci): stabilize main branch coverage checks` — 修复 `approval_required` Inbox 通知残留问题，隔离 Railway sandbox 测试的网络干扰，回归覆盖通知校验逻辑。
- **#7993** [CLOSED] `chore(deps): bump everything-else (16 updates)` — Dependabot 常规依赖更新（uuid、base64、toml 等）。

**推进中的关键工作：**
- Epic #7781 的 Phase 2–3 已进入集成预览分支（#8005，标记为 **do not merge**），Phase 3 的 M3 Reskin 以新 PR #8011 重新提交，覆盖色板、字体、中性表面梯度和 `--v2-*` token 移除。
- #7996 正在修复 `github.list_repos` 的体积问题（与 #7986 Issue 对应），将 81 字段全量响应压缩为模型可用字段投影。
- #7999 正在修复 #7987 的 schema 约束丢失问题，改用白名单移除而非重建方式保留 `dependentRequired`、`$defs` 等合法约束。

## 4. 社区热点

**今日讨论活跃 Issue/PR：**

| 编号 | 类型 | 作者 | 热度说明 | 链接 |
|---|---|---|---|---|
| #7781 | Epic (OPEN) | rdisandro | Design System Phases 2–3 总控 Epic，今日更新，串联 #7042/#7038/#7782 | [Issue #7781](https://github.com/nearai/ironclaw/issues/7781) |
| #8012 | Bug (OPEN) | pranavraja99 | 47k 工具目录可 ingest 但 `tool_search` 完全不可达，2000 工具正常工作，定位关键阈值 | [Issue #8012](https://github.com/nearai/ironclaw/issues/8012) |
| #7987 | Bug (OPEN) | henrypark133 | `flatten_top_level` 重建 schema 时静默丢弃非白名单顶层约束 | [Issue #7987](https://github.com/nearai/ironclaw/issues/7987) |
| #7986 | Bug (OPEN) | henrypark133 | `github.list_repos` 单请求 519 KB，519 字节 × 98 repos 的冗余传输 | [Issue #7986](https://github.com/nearai/ironclaw/issues/7986) |
| #8008 | Bug (OPEN) | pranavraja99 | Hosted-MCP 一个工具被 leak detector 阻断即丢弃整个目录 | [Issue #8008](https://github.com/nearai/ironclaw/issues/8008) |
| #8010 | Feature (OPEN) | BenKurrek | WebUI session-event 传输统一 + run-completion 通知，XL 规模 | [PR #8010](https://github.com/nearai/ironclaw/pull/8010) |
| #8011 | Feature (OPEN) | rdisandro | M3 Reskin：全新色板、OKLab 派生暗色模式、token shim 退役 | [PR #8011](https://github.com/nearai/ironclaw/pull/8011) |
| #7999 | Fix (OPEN) | linhongyu510 | 修复 #7987，保留 flatten 后的合法 schema 约束 | [PR #7999](https://github.com/nearai/ironclaw/pull/7999) |
| #7964 | Fix (OPEN) | pranavraja99 | 修复 #8012/#8008，大型 MCP 目录截断而非全量丢弃 | [PR #7964](https://github.com/nearai/ironclaw/pull/7964) |

**热点分析：**
- **MCP 发现链路** 是今日最大焦点：#8012、#8008、#8009、#7964 形成一组关联问题，暴露了 hosted-MCP 在大目录场景下的多重脆弱性（leak detector 误杀、错误扁平化、静默失败），已有 #7964 修复但尚待合并。
- **Design System** 仍是前端主线：#7781 及其子任务推进有序，#8011 M3 Reskin 新提 PR 说明 Phase 3 工作持续迭代。
- **schema 保真**（#7987/#7999）涉及 LLM tool calling 的核心正确性， contributor `linhongyu510` 首次提交修复 PR，值得关注。

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | Fix PR | 状态 |
|---|---|---|---|---|
| 🔴 高 | #8012 | 47k 工具目录 ingest 成功但 `tool_search` 零可达 | #7964（待合并） | 有 fix |
| 🔴 高 | #8008 | 单个 tool 被 leak detector 阻断导致整个目录丢弃 | #7964（待合并） | 有 fix |
| 🔴 高 | #8009 | `mcp_http_error` 扁平化为 `"response_error"`，丢失诊断信息 | 无 | 待处理 |
| 🟠 中 | #7987 | `flatten_top_level` 白名单重建导致约束静默丢失 | #7999（待合并） | 有 fix |
| 🟠 中 | #7986 | `github.list_repos` 519 KB/次冗余响应 | #7996（待合并） | 有 fix |
| 🟡 低 | #8012 关联 | 大型 catalog 与 2000 工具间的阈值行为未定位 | 待排查 | 待处理 |

**已关闭的稳定性修复：**
- #7892 [CLOSED] — deferred tool 15 次搜索未调用问题，由 #7977 修复并关闭。

## 6. 功能请求与路线图信号

| 方向 | 信号来源 | 分析 |
|---|---|---|
| **Design System 完整落地** | Epic #7781 (Phases 2–3) + #7782 (Phases 4–5) + #8011 M3 Reskin | 设计系统分 5 阶段推进，Phase 1 已合并（#7038），Phase 2–3 进入集成预览，Phase 4–5 已拆分。M3 主题（`#6b4eff`/`#00e5ff`/`#ff4e9e` 三色系 + OKLab 暗色派生）预计纳入 v1.4.0。 |
| **WebUI 通知与传输统一** | PR #8010（session-event transport）+ PR #8006（progressive replies + Slack UI） | BenKurrek 主导的两条 PR 分别处理 WebUI 内部传输和跨 channel 回复，指向统一的即时通知体验，可能随 v1.4.0 或后续版本发布。 |
| **MCP 生态可靠性** | #8012、#8008、#8009、#7964 | 大型目录发现的多点故障暴露了 hosted-MCP 在生产场景的健壮性不足，#7964 修复截断逻辑后预计会带动一批相关改进。 |
| **NEAR AI 模型能力传播** | PR #7998 | 新增 `list_model_catalog()` 发现 API，保留旧 `list_models()`，扩展模型输入/输出模态的端到端传播。 |
| **CI/测试稳定性** | #7992、#7995 已合并 | 集成测试统一执行和覆盖率检查稳定化已完成，后续关注 #8007（progressive reply 的 5 个 `arch-exempt` waiver 清理）。 |

## 7. 用户反馈摘要

- **MCP 大目录完全不可搜索**（#8012，pranavraja99）：用户投入构建了 47,337 工具的主机 MCP catalog，ingest 成功但 `tool_search` 零结果，对比 2,000 工具版本正常工作，强烈暗示存在数量阈值或分页缺陷。这是高价值用户场景的阻塞性问题。
- **工具调用开销过高**（#7986，henrypark133）：`github.list_repos` 单次返回 519 KB（81 字段 × 98 repos），用户指出 package 自身的 projection seam 未被使用，存在明显的资源浪费。
- **Schema 约束静默丢失**（#7987，henrypark133）：`flatten_top_level` 从白名单重建 schema 导致非禁止的顶层约束（如 `dependentRequired`、`$defs`）被静默丢弃，无警告无测试，影响 tool schema 的语义正确性。
- **错误信息丧失诊断价值**（#8009，pranavraja99）：`mcp_http_error` 将所有 `RuntimeHttpEgressError` 扁平化为 `"response_error"`，使 hosted-MCP 发现失败无法定位根因。
- **Loop 无限重复调用**（#7892，已关闭，henrypark133）：生产运行中模型反复搜索同一工具（15 次 `google-calendar.list_events`）却无终止，消耗 79s/86s/123s，已修复。
- **设计系统治理需求明确**（#7042、#7994，rdisandro）：`DESIGN.md` 作为 M3 设计语言的书面 truth source 正在落地，用户（贡献者）推动将 design token、Storybook 指南和 React 19 + Tailwind v4 栈的兼容性文档化。

## 8. 待处理积压

| 编号 | 类型 | 描述 | 风险提示 | 链接 |
|---|---|---|---|---|
| #8009 | Bug (OPEN) | MCP egress 错误全部扁平化为 `"response_error"`，无诊断信息 | 影响 hosted-MCP 故障排查效率，#7964 修复截断问题后此问题仍独立存在 | [Issue #8009](https://github.com/nearai/ironclaw/issues/8009) |
| #8007 | Tracking (OPEN) | Progressive reply 的 5 个 `arch-exempt` waiver 待清理 | 技术债累积，需在 #8010/#8006 合并后跟进重构 | [Issue #8007](https://github.com/nearai/ironclaw/issues/8007) |
| #7890 | Task (OPEN) | 退役 `app.css` 中 Tailwind colour-alias compat layer（~100 行 `!important` 重写） | 与 M3 Reskin（#8011）强相关，建议在 reskin 合并后同步清理 | [Issue #7890](https://github.com/nearai/ironclaw/issues/7890) |
| #8012 关联阈值 | Bug (OPEN) | 47k vs 2000 工具间的 `tool_search` 可达性阈值未精确定位 | #7964 修复目录丢弃后需回归验证大目录搜索路径 | [Issue #8012](https://github.com/nearai/ironclaw/issues/8012) |

**维护者关注建议：**
- #7964 和 #7999 是两个关键修复 PR，合并后可消除今日最高严重性的两个 Bug（#8012/#8008 和 #7987）。
- #8005 为纯集成预览分支（**do not merge**），用于评估 Epic #7781 Phase 2–3 的整体效果，建议在 Phase 4–5（#7782）启动前完成评审。
- #7831（Chromatic Storybook 发布）的 token 部分已并入 #8011，需确认 CI 中 Chromatic lane 的非阻塞状态是否正常配置。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报
**日期：2026-09-01 | 数据周期：2026-08-31 ~ 2026-09-01**

---

## 1. 今日速览

过去24小时 LobsterAI 项目保持中等活跃度，共产生 **11 条 Issue 更新**（5 新开/活跃、6 已关闭）和 **27 条 PR 更新**（16 待合并、11 已合并/关闭）。无新版本发布。今日核心动向：安全团队提交 MCP stdio 命令注入加固 PR（#2590），开发者 `chiamsun` 修复了 DSH 工作台无法配置推理强度的 Bug（#2585），同时用户反馈 plan mode 大量消耗积分的问题（#2589）。整体项目健康度良好，依赖更新与功能优化持续推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（11 条）

| PR | 内容 | 影响 |
|---|---|---|
| [#2588](https://github.com/netease-youdao/LobsterAI/pull/2588) | 用户指南文档更新 | 完善使用文档 |
| [#2462](https://github.com/netease-youdao/LobsterAI/pull/2462) | bump mermaid 10.9.8 → 11.16.1 | 依赖升级 |
| [#2465](https://github.com/netease-youdao/LobsterAI/pull/2465) | bump vite 5.4.21 → 8.2.1 | 构建工具升级 |
| [#2463](https://github.com/netease-youdao/LobsterAI/pull/2463) | bump @vitejs/plugin-react 4.7.0 → 6.0.5 | React 插件升级 |
| [#2458](https://github.com/netease-youdao/LobsterAI/pull/2458) | bump @types/react-dom 18.3.7 → 19.2.4 | 类型定义升级 |
| [#2164](https://github.com/netease-youdao/LobsterAI/pull/2164) | bump trufflehog 3.88.30 → 3.95.5 | 安全扫描工具升级 |
| [#2167](https://github.com/netease-youdao/LobsterAI/pull/2167) | bump actions/stale 9.1.0 → 10.3.0 | CI 工具升级 |
| [#2165](https://github.com/netease-youdao/LobsterAI/pull/2165) | bump actions/checkout 4 → 6 | CI 工具升级 |

### 待合并 PR 亮点（16 条）

- **[#2590](https://github.com/netease-youdao/LobsterAI/pull/2590)** — 安全加固：修复 MCP stdio 命令字段无校验导致的命令注入漏洞，同时加固外部 URL 协议白名单，与历史 PR [#908](https://github.com/netease-youdao/LobsterAI/pull/908) 功能重叠但更新。
- **[#2585](https://github.com/netease-youdao/LobsterAI/pull/2585)** — 修复 DSH 工作台无法配置推理强度的 Bug，将 LobsterAI 模型的 `thinking` 元数据映射为 DSH 的 `reasoningEfforts`。
- **[#2587](https://github.com/netease-youdao/LobsterAI/pull/2587)** — bump mermaid 10.9.8 → 11.17.2（继 #2462 的后续版本）。
- **[#2586](https://github.com/netease-youdao/LobsterAI/pull/2586)** — bump vite 5.4.21 → 8.2.2。
- **[#2584](https://github.com/netease-youdao/LobsterAI/pull/2584)** — bump @vitejs/plugin-react 4.7.0 → 6.1.1。
- **[#2583](https://github.com/netease-youdao/LobsterAI/pull/2583)** — bump trufflehog 3.88.30 → 3.97.1。
- **[#2582](https://github.com/netease-youdao/LobsterAI/pull/2582)** — bump @types/react-dom 18.3.7 → 19.2.5。
- **[#2581](https://github.com/netease-youdao/LobsterAI/pull/2581)** — bump actions/stale 9.1.0 → 11.0.0。
- **[#2580](https://github.com/netease-youdao/LobsterAI/pull/2580)** — bump actions/cache 4 → 6。
- **[#2579](https://github.com/netease-youdao/LobsterAI/pull/2579)** — bump actions/checkout 4 → 7。
- **[#1277](https://github.com/netease-youdao/LobsterAI/pull/1277)** — 长期待合并：bump electron 40.2.1 → 44.0.0（含 electron-builder 更新）。

**进展评估：** 今日以依赖升级（dependabot 批量跟进）和安全加固为主，功能修复聚焦于 DSH 推理强度配置问题。electron 大版本升级（#1277）仍在等待审核，是当前最大的待合并阻塞项。

---

## 4. 社区热点

| Issue/PR | 状态 | 作者 | 热度分析 |
|---|---|---|---|
| [#2589](https://github.com/netease-youdao/LobsterAI/issues/2589) | OPEN | dreamsdesign | **今日最新**，用户强烈抱怨 plan mode 消耗大量积分（"you don't expect a repeat customer!"），情绪激烈，值得快速响应 |
| [#2577](https://github.com/netease-youdao/LobsterAI/issues/2577) | OPEN | chiamsun | 新报告 Bug，DSH 工作台无法配置 LobsterAI 模型的思考强度，作者已提交修复 PR #2585 |
| [#1117](https://github.com/netease-youdao/LobsterAI/issues/1117) | OPEN [stale] | MaoQianTu | 长期功能请求：工具权限弹窗支持 Enter/Escape 快捷键，中断键盘驱动编码流，有明确需求 |
| [#1120](https://github.com/netease-youdao/LobsterAI/issues/1120) | OPEN [stale] | MaoQianTu | 长期功能请求：会话出错后一键 Retry，当前无恢复路径，体验断裂 |
| [#1124](https://github.com/netease-youdao/LobsterAI/issues/1124) | OPEN [stale] | liangshuang24yy-bit | 长期 Bug：卸载/退出后安装新版仍提示"Lobster AI无法关闭"，影响安装体验 |
| [#908](https://github.com/netease-youdao/LobsterAI/pull/908) | OPEN [stale] | vdorchan | 历史安全 PR，修复 MCP stdio 命令注入，已被 #2590 覆盖但仍未合并 |

**热点分析：** 今日社区最突出的信号是**积分消耗透明度问题**（#2589）和**DSH 推理强度缺失**（#2577/#2585）。前者是付费用户的直接痛点，后者是技术用户的核心功能需求。用户 MaoQianTu 提交的两项功能请求（#1117、#1120）已 stale 较长时间，反映了用户对交互体验细节的强烈诉求。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 标题 | 修复状态 |
|---|---|---|---|
| 🟡 中 | [#2577](https://github.com/netease-youdao/LobsterAI/issues/2577) | DSH 工作台无法更改 LobsterAI 模型的思考强度 | ✅ PR #2585 已提交 |
| 🟡 中 | [#1124](https://github.com/netease-youdao/LobsterAI/issues/1124) | 关闭退出后安装新版仍弹出"无法关闭"提示 | ❌ 无 fix PR |
| 🔴 高 | [#908](https://github.com/netease-youdao/LobsterAI/pull/908) | MCP stdio 命令注入漏洞（安全） | ⚠️ PR 待合并，已被 #2590 替代 |
| 🟠 中高 | [#2589](https://github.com/netease-youdao/LobsterAI/issues/2589) | Plan mode 大量消耗积分（疑似 Bug） | ❌ 待确认 |

**历史 Bug 回顾（近期 stale 关闭）：**

| Issue | 摘要 | 状态 |
|---|---|---|
| [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) | groupPolicy 配置被覆盖为 allowlist | stale 关闭 |
| [#1635](https://github.com/netease-youdao/LobsterAI/issues/1635) | Ollama 本地模型无法使用 | stale 关闭 |
| [#1643](https://github.com/netease-youdao/LobsterAI/issues/1643) | 手动创建定时任务保存提示错误 | stale 关闭 |
| [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) | 期望增加基于 MD 的 Agent 工作流 | stale 关闭 |
| [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) | 除 SSE 外的 MCP 引擎无法使用 | stale 关闭 |
| [#1671](https://github.com/netease-youdao/LobsterAI/issues/1671) | MD 转 Word 中途 SSE 报错 | stale 关闭 |

**稳定性评估：** 近期有多个 Bug 因 stale 机制关闭，需关注是否真正修复或仅是超时无人问津。安全类 Issue #908 长期未合并在风险敞口上需优先处理。

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | PR 状态 | 纳入可能性 |
|---|---|---|---|
| [#1117](https://github.com/netease-youdao/LobsterAI/issues/1117) | 工具权限弹窗支持键盘快捷键（Enter/Escape） | ❌ 无 PR | ⭐⭐ 明确需求，建议排期 |
| [#1120](https://github.com/netease-youdao/LobsterAI/issues/1120) | 会话错误后一键 Retry 重发 | ❌ 无 PR | ⭐⭐ 明确需求，建议排期 |
| [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) | 基于 MD 的 Agent 工作流，支持 main agent 组织其他 agent | ❌ 无 PR | ⭐⭐⭐ 用户高频诉求，需架构级设计 |
| [#2585](https://github.com/netease-youdao/LobsterAI/pull/2585) | DSH 同步推理强度元数据 | ✅ 已提交 | ⭐⭐⭐ 即将合入 |

**路线图信号：** 用户对工作流编排（#1644）和交互效率（#1117、#1120）的需求持续积累。DSH 推理强度修复（#2585）即将合入，体现了对 DeepSeek 系列模型深度集成的投入。建议关注多 Agent 协作能力的规划。

---

## 7. 用户反馈摘要

### 🔴 痛点
- **Plan mode 积分消耗**（#2589）：用户表示"plan mode drains 200 credits"，情绪激动，质疑产品对用户留存的态度，属于付费体验的高危信号。
- **安装/更新体验**（#1124）：退出登录后安装新版本仍提示"Lobster AI无法关闭"，表明进程管理或资源清理存在缺陷。
- **MCP 引擎限制**（#1662、#1635）：除 SSE 外的 MCP 协议及 Ollama 本地模型无法正常使用，限制了自托管场景。

### 🟡 中等痛点
- **DSH 工作台功能缺失**（#2577）：LobsterAI 同步的模型缺少思考强度控件，而手动添加的 provider 却可以，体验不一致。
- **工具权限弹窗交互**（#1117）：完全依赖鼠标操作打断键盘流，对开发者用户体验影响显著。
- **会话错误恢复**（#1120）：出错后无 Retry 路径，需手动复制粘贴重发，效率低下。

### 🟢 正面信号
- 用户贡献了用户指南文档（PR #2588）。
- 多个依赖升级 PR 自动跟进，说明项目维护机制运转正常。

---

## 8. 待处理积压

| 类型 | Issue/PR | 创建时间 | 时长 | 优先级 | 建议 |
|---|---|---|---|---|---|
| 🔴 安全 | [#908](https://github.com/netease-youdao/LobsterAI/pull/908) | 2026-03-26 | ~5 个月 | 紧急 | 尽快审核合并，或关闭并引用 #2590 |
| 🔴 付费体验 | [#2589](https://github.com/netease-youdao/LobsterAI/issues/2589) | 2026-09-01 | 今日 | 紧急 | 快速响应，确认是否为 Bug 并公开说明 |
| 🟡 Bug | [#1124](https://github.com/netease-youdao/LobsterAI/issues/1124) | 2026-03-31 | ~5 个月 | 高 | 需要排期修复进程清理逻辑 |
| 🟡 功能 | [#1117](https://github.com/netease-youdao/LobsterAI/issues/1117) | 2026-03-31 | ~5 个月 | 中 | 低优先级但明确需求，可安排 |
| 🟡 功能 | [#1120](https://github.com/netease-youdao/LobsterAI/issues/1120) | 2026-03-31 | ~5 个月 | 中 | 同上 |
| 🟠 依赖 | [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | 2026-04-02 | ~5 个月 | 中 | Electron 44

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-09-01

## 1. 今日速览

Moltis 在 2026-08-31 至 2026-09-01 期间保持中等活跃度，共处理 6 条社区反馈（2 Issues + 4 PRs），其中 3 条 PR 已合并，项目整体呈稳定迭代态势。开发者聚焦于认证安全加固、执行路径修复及安全扫描规范，同时发布了 `20260831.01` 版本。一个涉及 Kubernetes 原生沙箱后端的长期功能请求仍在跟踪中，显示社区对执行隔离能力的持续关注。

---

## 2. 版本发布

### `20260831.01`

- **发布时间**：2026-08-31
- **内容说明**：该版本打包了当日合并的安全与执行修复，包括 Snyk Agent Scan 依赖锁定、沙箱镜像请求校验、null 节点选择处理及 Docker 本地连接认证放宽。
- **破坏性变更**：无明确声明，但 PR #1222 对非管理员用户的镜像构建权限进行了收窄，若项目存在依赖未授权构建镜像的使用场景，建议复核权限配置。
- **迁移注意**：升级后需确认管理员账户仍具备完整的密码/Passkey/信任回环身份管理权限；非管理员用户将无法触发容器镜像构建或 Dockerfile 操作。

---

## 3. 项目进展

### 已合并 PR（3 条）

**PR #1248** — `fix(exec): honor explicit null node selection`
- 修复 `ExecTool` 未正确处理 `node: null` 显式请求的回归问题，确保当用户明确指定 null 节点时使用本地执行路径；同时保留未指定节点时的默认行为。新增回归测试覆盖已连接节点提供器场景。

**PR #1221** — `fix(gateway): pin Snyk Agent Scan`
- 将技能安全扫描依赖锁定至 Snyk Agent Scan `0.5.17`（通过 uvx），移除独立的 `mcp-scan` 回退路径，强制要求 `uv` 环境。此变更提升了供应链安全审计的可追溯性，减少第三方扫描工具的版本漂移风险。

**PR #1222** — `fix(web): validate sandbox image requests`
- 在容器或 Dockerfile 使用前增加镜像引用与包名的前置校验，并将包检查与镜像构建权限限制为操作管理员；同时保持密码、Passkey 及信任回环身份的全量管理权限不变。该修复封堵了未授权用户发起镜像构建请求的攻击面。

> **进度评估**：今日 3 条 PR 中有 2 条（#1221、#1222）聚焦安全加固，1 条（#1248）修复执行路径稳定性，项目整体向"安全优先、执行可靠"方向稳步推进。

### 待合并 PR（1 条）

**PR #1249** — `fix(auth): let Docker loopback-only deployments count as local`
- 修复 Docker Bridge 网络下 `is_local_connection()` 因源 IP 被重写为非回环地址而误判为非本地连接的问题，使 Tier 2 本地开发便利性（含 `auth_disabled`）在 Docker 部署场景中正确生效。该 PR 解决长期存在的 Issue #1112，预计合并后可显著改善容器化开发体验。

---

## 4. 社区热点

| 类型 | 编号 | 主题 | 活跃度 | 链接 |
|------|------|------|--------|------|
| Issue | #1118 | Kubernetes 原生沙箱后端（支持 runtimeClassName） | 评论 3 · 👍 1 · 持续活跃 | [Issue #1118](https://github.com/moltis-org/moltis/issues/1118) |
| PR | #1249 | Docker 回环部署本地连接认证修复 | 待合并 · 关注度高 | [PR #1249](https://github.com/moltis-org/moltis/pull/1249) |

**热点分析**：
- **#1118** 自 2026-06-12 创建以来持续获得关注，用户诉求清晰：期望 Moltis 支持通过 Kubernetes Pod 运行 Agent 命令，并通过 `runtimeClassName` 接入 Kata Containers / gVisor 等 OCI 运行时实现 VM 级隔离。该功能填补了当前沙箱方案的空白，与 PR #1222 的安全校验能力形成互补，可作为下一阶段路线图重点。
- **#1249** 直接关联开发者的本地 Docker 调试痛点，合并后可降低容器化部署的认证摩擦，预计将获得社区正向反馈。

---

## 5. Bug 与稳定性

| 编号 | 严重度 | 描述 | 状态 | Fix PR | 链接 |
|------|--------|------|------|--------|------|
| #1246 | 中 | 添加节点后沙箱无法运行 | 已关闭 | 可能由 PR #1248 覆盖 | [Issue #1246](https://github.com/moltis-org/moltis/issues/1246) |

- **#1246** 报告在节点添加后沙箱执行失败，用户反馈路径完整。该 Issue 已于 2026-08-31 关闭，结合同日合并的 PR #1248（显式 null 节点选择修复），可推断二者存在关联，建议用户在 `20260831.01` 版本中验证回归情况。

---

## 6. 功能请求与路线图信号

**Issue #1118** — Kubernetes 原生沙箱后端
- **需求本质**：将 Agent 命令执行从当前沙箱模型扩展至 Kubernetes Pod，支持 `runtimeClassName` 以接入 Kata Containers、gVisor 等容器运行时，实现 VM 级隔离。
- **路线图判断**：该请求与 PR #1222（镜像请求校验）、PR #1248（执行路径修复）共同指向"增强执行隔离与安全性"方向。若 PR #1249 顺利合并、认证基础设施完善，#1118 具备纳入下一版本（`202609xx` 系列）的可行性，建议维护者优先评估其实现方案与资源投入。

---

## 7. 用户反馈摘要

| 来源 | 痛点 / 场景 | 情绪倾向 |
|------|-------------|----------|
| Issue #1118 | 现有沙箱隔离能力不足，需支持 Kata/gVisor 等 VM 级运行时以满足高安全场景 | 期待 |
| Issue #1246 | 节点添加后沙箱执行异常，影响多节点部署体验 | 受阻 |
| PR #1249（关联 Issue #1112） | Docker Bridge 网络导致本地连接误判，`auth_disabled` 本地开发便利失效 | 受阻 |
| PR #1222 | 镜像构建权限收窄，非管理员无法操作 | 需确认影响范围 |

**核心诉求提炼**：用户最关注的是**执行隔离能力**与**容器化开发体验**。前者通过 #1118 和 #1222 形成前后呼应的安全闭环，后者则依赖 #1249 的合并落地。

---

## 8. 待处理积压

| 编号 | 类型 | 摘要 | 等待时长 | 建议 | 链接 |
|------|------|------|----------|------|------|
| #1118 | Issue | Kubernetes 原生沙箱后端，支持 runtimeClassName | ~3 个月 | 评估纳入下版本 | [Issue #1118](https://github.com/moltis-org/moltis/issues/1118) |
| #1249 | PR | Docker 回环部署本地连接认证修复 | 待合并 | 优先审核合并 | [PR #1249](https://github.com/moltis-org/moltis/pull/1249) |

> **维护者提醒**：PR #1249 已就绪且关联长期反馈（Issue #1112），合并后可显著提升 Docker 开发体验；Issue #1118 作为关键功能请求，建议结合版本规划给予明确回应。

---

**项目健康度评估**：今日 Moltis 展现良好的维护节奏——安全修复（#1221、#1222）、执行稳定性（#1248）与开发者体验（#1249）同步推进，版本迭代与社区响应匹配度高。积压中仅 #1118 一项长期未决，其余均在可控范围内。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-09-01

## 1. 今日速览

CoPaw 项目今日保持高活跃度：过去 24 小时新增/活跃 Issues 15 条、关闭 14 条，PR 动态 39 条（23 待合并、16 已合并/关闭），并连续发布 v2.2.0-beta.4 与 v2.2.0-beta.5 两个测试版本。社区对 **QwenPaw Hub 多租户版** 的规划讨论热度最高（Issue #7318，15 条评论），反映出用户对团队部署能力的强烈诉求。同时，多个关键稳定性问题（上下文丢失、子 Agent 状态同步、Browser SDK Tab 管理）仍在开放中，需持续关注。整体项目健康度良好，修复 PR 响应及时，测试覆盖度持续攀升。

---

## 2. 版本发布

### v2.2.0-beta.5（最新发布）
- **fix(channels)**: 使渠道契约检查可移植且完整（解决 Windows 默认编码下的 `UnicodeDecodeError`）
- **fix(memory)**: 使 Embedding 重建显式化与作用域化，避免配置变更时自动全量重建
- **chore**: 版本号 bump

### v2.2.0-beta.4
- **fix(context)**: 限制超大单行 Tool 结果长度，防止上下文溢出
- **test(agent-stats)**: 对齐 TC-AGT-06 测试用例与当前 Agent 作用域
- **fix(desktop)**: 桌面端修复（内容截断，待补充）

> **迁移注意**: beta.5 的 memory 行为变更可能影响依赖自动 Embedding 重建的用户，建议手动触发 `Rebuild Memory Index` 验证。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#7438](https://github.com/agentscope-ai/QwenPaw/pull/7438) | chore | 版本号 bump 至 2.2.0b5 |
| [#7133](https://github.com/agentscope-ai/QwenPaw/pull/7133) | fix | Embedding 重索引逻辑重构，支持显式触发与撤销 |
| [#7220](https://github.com/agentscope-ai/QwenPaw/pull/7220) | fix | 拒绝超维度图片（修复 vision 提供商像素限制溢出）|
| [#7437](https://github.com/agentscope-ai/QwenPaw/pull/7437) | test | v2.2.0-beta.4 安装验证通过 |

### 待合并亮点 PR

- **#7457** [fix(browser)] Chrome 扩展 Tab Group 复用修复 — 解决每次 `open()`/`present()` 创建新分组的回归
- **#7453** [fix(pack)] PyInstaller 打包修复 — 解决 `Rebuild Memory Index` 500 错误（关联 Issue #7446）
- **#7066** [fix(drivers)] OAuth2 刷新令牌持久化 — 修复远程 MCP 服务器令牌轮换后认证失效
- **#7444** [feat(memory)] 统一 ReMe Slash 命令 — 将 `/dream`、`/memorize`、`/reme_status` 合并为单一入口
- **#7441** [feat(memory)] 引入 Auto Fin 作为长期记忆源 — 升级 ReMe 至 0.4.1.11
- **#7452/#7451** [test] 测试冲刺批量合并 — Console 单元测试 +617 用例，集成测试 +314 用例

> **进展评估**: 本次迭代聚焦 **稳定性修复** 与 **测试覆盖**，同时 memory 子系统功能持续增强。Beta.4 → Beta.5 仅用一天，修复节奏紧凑。

---

## 4. 社区热点

### 🔥 Issue #7318 — QwenPaw Hub 多租户版规划讨论
- **作者**: rayrayraykk | **评论**: 15 | **👍**: 2
- [链接](https://github.com/agentscope-ai/QwenPaw/issues/7318)
- **摘要**: 社区长期请求多用户/团队部署能力，Hub 是官方首次回应。讨论聚焦功能优先级与多租户架构设计。
- **信号**: 多租户是企业级采用的关键门槛，此 Issue 高热度表明该方向获得社区强支持。

### 🔥 Issue #7420 — Tool 结果丢失 + Doom-loop 保护触发
- **作者**: MG1058 | **评论**: 8
- [链接](https://github.com/agentscope-ai/QwenPaw/issues/7420)
- **摘要**: 升级至 2.2.0-beta.1 后出现单次会话 5 次卡死，两种不同机制触发 doom-loop 保护。
- **信号**: 涉及核心执行路径，需在正式 release 前解决。

### 🔥 Issue #7398 — 添加 `/btw` 侧边问题命令
- **作者**: Marlin-Phone | **评论**: 2
- [链接](https://github.com/agentscope-ai/QwenPaw/issues/7398)
- **摘要**: 请求借鉴 Claude Code 的 `/btw` 命令，允许用户问临时问题而不污染主上下文。
- **信号**: 用户体验类轻量功能，可快速采纳。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447) | 长上下文（~70% token）时早期记录**彻底丢失**，任务无法继续 | 无 |
| 🔴 高 | [#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420) | Tool 结果丢失 + doom-loop 保护误触发（5 次卡死/会话） | 无 |
| 🟠 中 | [#7446](https://github.com/agentscope-ai/QwenPaw/issues/7446) | Rebuild Memory Index 返回 500（ReMe instance is None） | ✅ [#7453](https://github.com/agentscope-ai/QwenPaw/pull/7453) |
| 🟠 中 | [#7363](https://github.com/agentscope-ai/QwenPaw/issues/7363) | 同步调用阻塞事件循环，timeout 失效（启动/发消息卡顿 118-135s） | 无 |
| 🟠 中 | [#7397](https://github.com/agentscope-ai/QwenPaw/issues/7397) | Browser SDK 每次调用创建新 Tab Group，无法共享 | ✅ [#7457](https://github.com/agentscope-ai/QwenPaw/pull/7457) |
| 🟡 低 | [#7377](https://github.com/agentscope-ai/QwenPaw/issues/7377) | Agent Loop 模式配置任务完成后重置为 Default | 无 |
| 🟡 低 | [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) | Console 流式输出重复文本块 | 无 |
| 🟡 低 | [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | 主 Agent+ 多子 Agent 模式下无主动进度查询 | 无 |

> **稳定性评估**: 2 个高危 Bug（上下文丢失、执行卡死）尚未有修复 PR，建议优先处理。中等严重程度问题已有对应修复在途。

---

## 6. 功能请求与路线图信号

| 请求 | Issue/PR | 状态 | 纳入下一版本可能性 |
|---|---|---|---|
| `/btw` 侧边问题命令 | [#7398](https://github.com/agentscope-ai/QwenPaw/issues/7398) | 开放 | ⭐⭐⭐⭐ 高（轻量、用户收益明显）|
| 所有自带云端提供商可停用 | [#7455](https://github.com/agentscope-ai/QwenPaw/issues/7455) | 已关闭 | ⭐⭐ 中（可能已在 beta.5 处理）|
| Agent Loop 模式配置持久化 | [#7377](https://github.com/agentscope-ai/QwenPaw/issues/7377) | 开放 | ⭐⭐⭐ 中 |
| 主 Agent 主动查询子 Agent 状态 | [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | 开放 | ⭐⭐ 中（需架构调整）|
| 左侧收起侧栏时会话图标置顶 | [#7125](https://github.com/agentscope-ai/QwenPaw/issues/7125) | 开放 | ⭐⭐⭐ 高（UI 体验优化）|
| 工作区级 Skill 预加载配置 | [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | PR 审核中 | ⭐⭐⭐⭐ 高（已在开发中）|
| ReMe Slash 命令统一 | [#7444](https://github.com/agentscope-ai/QwenPaw/pull/7444) | PR 开放 | ⭐⭐⭐⭐ 高（已在开发中）|
| 复制助手文本不含推理过程 | [#7448](https://github.com/agentscope-ai/QwenPaw/pull/7448) | PR 开放 | ⭐⭐⭐ 中 |

---

## 7. 用户反馈摘要

### 痛点
1. **上下文丢失**（#7447）: 用户处理 160 页中文 Word 文档时，手工压缩至 70% token 后仍发生早期记录消失，导致任务中断。
2. **子 Agent 执行黑盒**（#7450）: 主 Agent 调用多个子 Agent 执行复杂任务时，执行期间无状态更新，用户需主动询问"进度如何"才能获知，体验差。
3. **启动缓慢**（#7360/#7363）: Desktop 启动耗时约 247 秒（~4 分钟），同步调用阻塞事件循环是主因。
4. **OAuth2 令牌失效**（#7066）: 远程 MCP 服务器（如 XMind）使用旋转刷新令牌时，旧令牌未持久化导致认证失效。
5. **中文文件名乱码**（#7379）: 处理含十几个中文字符的 PDF 文件时报错 `UNKNOWN_AGENT_ERROR`。

### 满意点
- Beta 版本修复响应迅速（如 #7446 的 500 错误在发布次日即有修复 PR）
- 测试覆盖度 sprint 持续推进，质量保障意识强
- 多租户规划透明，社区参与感强

---

## 8. 待处理积压

| Issue | 类型 | 积压时间 | 建议 |
|---|---|---|---|
| [#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447) | Bug (高) | 1 天 | 优先排查上下文截断/清理逻辑 |
| [#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420) | Bug (高) | 1 天 | 回归测试重点，可能涉及 beta.1 引入的变更 |
| [#7363](https://github.com/agentscope-ai/QwenPaw/issues/7363) | Bug (中) | 5 天 | 审查同步调用路径，考虑异步化 |
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | Discussion | 6 天 | 安排架构师回应，输出路线图时间线 |
| [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | PR (待审) | 12 天 | 安排 reviewer 审核 |
| [#7066](https://github.com/agentscope-ai/QwenPaw/pull/7066) | PR (待审) | 16 天 | 安全相关修复，建议优先合并 |

---

**报告生成时间**: 22:13 CST | **数据截止**: 2026-09-01 | **分析师**: Agnes (Sapiens AI)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw 项目动态日报
**日期：2026-09-01 | 数据来源：GitHub qhkm/zeptoclaw**

---

## 1. 今日速览

今日 ZeptoClaw 项目聚焦于**安全审计与修复**，共新增 8 个 Issues 和 1 个已合并 PR，整体活跃度中等。所有新开 Issue 均标记为 `area:safety` 或安全相关，由核心维护者 `morler` 和 `qhkm` 主导，反映出项目在安全合规方面正进行系统性整顿。一条修复 8 个 RustSec 漏洞的 PR (#657) 已在当日合并关闭，为后续 CI 恢复扫清障碍。**项目健康度良好**，问题定位清晰、优先级明确（P1-critical），但暂无新版本发布。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭 PR
- **[PR #657] chore(deps): fix 8 RustSec advisories** — 由 `morler` 提交并关闭了 Issue #651。升级了 7 个核心依赖（h2、bcrypt、quinn-proto、crossbeam-epoch、anyhow、quick-xml、lopdf），修复了全部已知 CVE。**此 PR 是恢复 CI cargo-deny 检查的关键前置条件**，直接打通了 Issue #646 的阻塞路径。

> 链接：https://github.com/qhkm/zeptoclaw/pull/657

---

## 4. 社区热点

### 🔥 最活跃 Issue
- **[Issue #646] chore(ci): restore Clippy and cargo-deny checks** — 3 条评论，核心维护者 `qhkm` 主导。PR #657 的合并已解决其阻塞问题，预期即将进入 CI 修复流程。  
  > https://github.com/qhkm/zeptoclaw/issues/646

- **[Issue #651 / #657] 依赖安全修复** — Issue #651 由 `morler` 创建，PR #657 同日关闭。社区对 RustSec 合规要求高度一致，7 个漏洞覆盖 HTTP/2、加密、QUIC 等核心组件，修复优先级极高。  
  > https://github.com/qhkm/zeptoclaw/issues/651

### 📌 其他活跃 Issue
- **[Issue #644] bug(safety): scrub subprocess environments and terminate process trees on timeout** — `qhkm` 创建的 P1-critical 问题，关注子进程环境隔离与超时终止，是运行时安全的核心修复。  
  > https://github.com/qhkm/zeptoclaw/issues/644

---

## 5. Bug 与稳定性

今日报告 **6 个安全类 Bug**，按严重程度排列：

| 严重级别 | Issue | 描述 | 已有 Fix PR |
|---------|-------|------|------------|
| P1-critical | [#644](https://github.com/qhkm/zeptoclaw/issues/644) | 子进程继承完整环境变量；超时未终止进程树 | 无 |
| P1-critical | [#646](https://github.com/qhkm/zeptoclaw/issues/646) | CI Clippy/cargo-deny 检查被绕过 | 部分（#657） |
| High | [#656](https://github.com/qhkm/zeptoclaw/issues/656) | `panel start` 将完整 API token 打印到 stdout，泄露至终端历史/日志 | 无 |
| High | [#655](https://github.com/qhkm/zeptoclaw/issues/655) | Bearer token 使用 `==` 非常量时间比较（3 处），存在时序攻击风险 | 无 |
| High | [#653](https://github.com/qhkm/zeptoclaw/issues/653) | WS 认证 token 通过 `?auth=` 查询参数传递，泄露至反向代理/浏览器历史 | 无 |
| High | [#652](https://github.com/qhkm/zeptoclaw/issues/652) | `config.toml`、`panel.token` 以默认 umask 写入，可读性过宽 | 无 |
| Medium | [#654](https://github.com/qhkm/zeptoclaw/issues/654) | `/api/auth/login` 无速率限制，仅依赖 bcrypt 成本防护 | 无 |

**稳定性评估**：6 个未修复 Bug 均为安全合规类，无崩溃或功能回归报告。项目稳定性整体可控，但安全面较广，建议优先处理 #655（常量时间比较）和 #653（token 泄露路径）。

---

## 6. 功能请求与路线图信号

今日无新功能需求提出，所有 Issue 均为安全修复范畴。

**路线图画布**：项目正在强化**安全基线**，以下方向可能纳入近期版本：
- 完善速率限制框架（当前仅用于 channel messages，Issue #654 建议扩展至登录端点）
- 强化子进程安全隔离（Issue #644）
- 标准化文件权限管理（Issue #652）

> 无新功能 PR 今日提交，路线图仍以安全加固为主。

---

## 7. 用户反馈摘要

### 真实痛点
- **Token 泄露路径多**：Issue #656、#653 共同指向 API token 在多个环节（stdout、查询参数、文件权限）的暴露风险，用户对环境安全和日志安全高度关注。
- **安全工具链恢复需求迫切**：Issue #646 反映维护者对 CI 自动化安全扫描的依赖，cargo-deny 中断影响发布信心。
- **常量时间比较缺失**：Issue #655 指出 `==` 比较 bearer token 存在理论上的时序攻击面，虽当前场景风险有限，但合规审查严格。

### 满意之处
- 问题发现与修复节奏快：Issue #651 提出后 PR #657 同日合并，响应效率高。
- 维护者分工明确：`qhkm` 主导基础设施/CI，`morler` 聚焦安全审计，协作高效。

---

## 8. 待处理积压

### ⚠️ 需维护者关注
| Issue | 状态 | 风险 |
|-------|------|------|
| [#644](https://github.com/qhkm/zeptoclaw/issues/644) | 8/31 更新，无 PR | P1-critical，子进程环境隔离 |
| [#655](https://github.com/qhkm/zeptoclaw/issues/655) | 8/31 创建，无 PR | High，3 处非常量时间比较 |
| [#653](https://github.com/qhkm/zeptoclaw/issues/653) | 8/31 创建，无 PR | High，token 通过 URL 参数泄露 |
| [#652](https://github.com/qhkm/zeptoclaw/issues/652) | 8/31 创建，无 PR | High，密钥文件权限过宽 |
| [#656](https://github.com/qhkm/zeptoclaw/issues/656) | 8/31 创建，无 PR | High，token 打印至 stdout |
| [#654](https://github.com/qhkm/zeptoclaw/issues/654) | 8/31 创建，无 PR | Medium，登录端点无速率限制 |

**建议**：上述 6 个 Issue 均创建于 8 月 31 日，今日尚无 PR 响应。考虑到均为安全类问题，建议维护者优先处理 #655 和 #653（泄露路径明确），随后解决 #652（权限修复成本低）。

---

**报告生成时间**：2026-09-01  
**分析师**：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-09-01

## 1. 今日速览

ZeroClaw 今日保持高活跃度：过去 24 小时内新增 25 条活跃 Issue 和 50 条待合并 PR，无新版本发布。社区讨论焦点集中在架构 RFC（会话所有权、内存生命周期解耦、附件架构统一）和安全策略（沙箱粒度、插件出站控制）。多个关键 bug 浮出水面，包括 P0 级配置保存缺陷和 WASM 运行时稳定性问题，提示近期需要优先处理稳定性修复。整体项目健康度良好，技术债正在加速偿还。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日 **50 条 PR 全部待合并**（0 条已合并），涵盖以下重要方向：

| PR | 类型 | 摘要 |
|----|------|------|
| [#9740](https://github.com/zeroclaw-labs/zeroclaw/issues/9740) | feat | VoiceHost WebSocket 桥接，支持 FunASR/SenseVoice 音频转录 |
| [#9313](https://github.com/zeroclaw-labs/zeroclaw/issues/9313) | fix | 修复 WeChat channel 同步游标持久化时机问题 |
| [#9535](https://github.com/zeroclaw-labs/zeroclaw/issues/9535) | feat | 上下文压缩基于模型窗口比例自适应 |
| [#9109](https://github.com/zeroclaw-labs/zeroclaw/issues/9109) | feat | 原生 Hailo-Ollama provider 支持 |
| [#9809](https://github.com/zeroclaw-labs/zeroclaw/issues/9809) | feat | 单 provider profile 托管多模型 |
| [#9582](https://github.com/zeroclaw-labs/zeroclaw/issues/9582) | feat | WASM 插件 `wasi:http` 出站策略强制执行（Stage 2） |
| [#10351](https://github.com/zeroclaw-labs/zeroclaw/issues/10351) | feat | 执行树迭代预算上限控制 |
| [#10521](https://github.com/zeroclaw-labs/zeroclaw/issues/10521) | fix | 修复 `ZEROCLAW_CONFIG_DIR` 环境变量未生效问题 |
| [#10498](https://github.com/zeroclaw-labs/zeroclaw/issues/10498) | fix | 拒绝不安全的裸路径配置覆盖 |
| [#10448](https://github.com/zeroclaw-labs/zeroclaw/issues/10448) | fix | OpenAI-compatible provider 工具结果图片策略 |
| [#9248](https://github.com/zeroclaw-labs/zeroclaw/issues/9248) | feat | eval 运行历史追加式收据记录 |
| [#9245](https://github.com/zeroclaw-labs/zeroclaw/issues/9245) | feat | eval judge 校准工具链 |
| [#9244](https://github.com/zeroclaw-labs/zeroclaw/issues/9244) | feat | eval 隔离用例内存种子与评估 |

**进展评估**：今日 PR 池规模显著，但合并率为零，说明维护者 Review 负载较重。eval 子系统（5 个 PR 堆叠）和 provider 灵活性（多模型、Hailo-Ollama）是当前推进重点。

---

## 4. 社区热点

### 高讨论度 RFC（按评论数排序）

| Issue | 主题 | 评论数 | 核心诉求 |
|-------|------|--------|----------|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | Runtime-owned 会话与传输适配器 | 29 | 明确会话所有权边界，支持 durable admission |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | 内存生命周期与存储后端解耦 | 24 | 统一 Consolidation/Governance 策略，避免各 channel 重复实现 |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | Web/Channel 统一附件架构 | 23 | 标准化附件处理，当前处于 Revision 9 |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | 粒度化沙箱策略 | 18 | 统一 application-layer 和 OS-level sandbox 策略漂移 |
| [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) | 权威存储与富化连接器分离 | 17 | 保留存储/富化架构边界，避免 Lucid-first  rollout |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | Desktop 计算机使用支持 | 15 | 屏幕交互与输入控制的 bounded approval 机制 |
| [#9330](https://github.com/zeroclaw-labs/zeroclaw/issues/9330) | AI 辅助 PR 预审查 | 11 | 确立 comment-only SOP review pipeline |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) | WASM Observer 订阅 | 11 | 替换 Hook 为 Observer capability，明确宿主所有权 |

**热点分析**：社区对**架构清晰性**和**安全边界**高度关注。多个 RFC 已进入 maintainer takeover 阶段，说明核心维护者正在主动收口设计决策。WASM 插件生态（#7822、#10076、#9582）是近期架构演进的核心战场。

---

## 5. Bug 与稳定性

| Issue | 严重程度 | 摘要 | Fix PR |
|-------|----------|------|--------|
| [#10495](https://github.com/zeroclaw-labs/zeroclaw/issues/10495) | **P0 / S0** | `Config::save()` 可能将 109KB 配置替换为 702 字节空文件 | 待确认 |
| [#10513](https://github.com/zeroclaw-labs/zeroclaw/issues/10513) | **P1 / S2** | RPC `sops.run` 返回无效 run ID，无 driver sink | 待确认 |
| [#9850](https://github.com/zeroclaw-labs/zeroclaw/issues/9850) | **P1 / S2** | `llm_task` 通过 legacy factory 构建 provider，丢失 alias 配置 | [#10448](https://github.com/zeroclaw-labs/zeroclaw/issues/10448)（部分覆盖） |
| [#10523](https://github.com/zeroclaw-labs/zeroclaw/issues/10523) | P2 / S2 | Bootstrap 文件 6000 字符截断对操作员不可见 | 待确认 |
| [#10501](https://github.com/zeroclaw-labs/zeroclaw/issues/10501) | P1 / medium | MCP 工具结果图片在 OpenAI-compatible provider 报 400 | [#10448](https://github.com/zeroclaw-labs/zeroclaw/issues/10448) |
| [#10505](https://github.com/zeroclaw-labs/zeroclaw/issues/10505) | P2 / medium | WASM 插件 WIT 版本偏移导致实例化失败 | 待确认 |
| [#10506](https://github.com/zeroclaw-labs/zeroclaw/issues/10506) | P2 / high | WASM `wasi:http` 顺序请求间歇性连接失效 | 待确认 |

**稳定性评估**：今日出现 **1 个 P0 级数据丢失风险**（#10495），需优先处理。WASM 运行时稳定性（#10505、#10506）可能影响插件生态，建议维护者关注。

---

## 6. 功能请求与路线图信号

| 需求方向 | 相关 Issue/PR | 纳入可能性 |
|----------|---------------|------------|
| 多模型 Provider | #9809 | **高** — PR 已完成，待合并 |
| 自适应上下文压缩 | #9535 + #10524 | **高** — 与 RFC #9487 呼应 |
| Eval 系统完善 | #9248/#9245/#9244/#9225/#9224 | **高** — 5 PR 堆叠，功能完整 |
| VoiceHost 音频桥接 | #9740 | **中** — 依赖外部 ASR 服务集成 |
| Hailo-Ollama 原生支持 | #9109 | **中** — niche provider，需权衡维护成本 |
| 插件出站安全策略 | #9582 + RFC #6996 | **高** — 安全架构关键路径 |
| 执行预算控制 | #10351 | **高** — 防止 agent 无限循环 |
| WASM Observer 生态 | #7822 + #10076 | **中** — 架构 RFC 阶段，需设计收敛 |

---

## 7. 用户反馈摘要

- **配置安全焦虑**：#10495 暴露了 `Config::save()` 的严重缺陷，用户担心配置数据丢失；#10498 的 fix PR 表明维护者已识别并响应。
- **WASM 插件调试困难**：#10505 的 "cryptic linker error" 和 #10506 的间歇性连接失败反映了插件开发体验痛点，版本偏移问题需要更友好的错误提示。
- **MCP 图片支持缺失**：#10501 和 #9850 指向 OpenAI-compatible provider 的图片处理缺陷，影响多模态工作流。
- **上下文管理需求**：#9535 和 #10523 显示用户对自适应压缩和透明截断有明确诉求。
- **Eval 可观测性**：#9248 的 append-only receipt 和 #9245 的 judge 校准工具反映了用户对 eval 结果可追溯性的重视。

---

## 8. 待处理积压

| Issue/PR | 状态 | 建议优先级 |
|----------|------|------------|
| [#10495](https://github.com/zeroclaw-labs/zeroclaw/issues/10495) | P0 bug，无 fix PR | **立即** — 配置丢失风险 |
| [#9582](https://github.com/zeroclaw-labs/zeroclaw/issues/9582) | Stage 2 egress policy，blocked | **高** — 安全关键路径 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC Revision 待维护者收口 | **高** — 架构决策 |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | RFC in-progress，需 maintainer review | **高** — 沙箱策略统一 |
| [#10513](https://github.com/zeroclaw-labs/zeroclaw/issues/10513) | P1 bug，SOP run ID 无效 | **中** — 功能退化 |
| [#10505](https://github.com/zeroclaw-labs/zeroclaw/issues/10505) | WASM 版本偏移调试困难 | **中** — 开发者体验 |
| 50 条待合并 PR | 无合并 | **维护者关注** — Review 负载需分配 |

---

**日报生成时间**：2026-09-01  
**数据来源**：[zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw) GitHub API

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*