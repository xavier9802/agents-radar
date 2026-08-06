# OpenClaw 生态日报 2026-08-06

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-06 03:16 UTC

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



# OpenClaw 项目动态日报 — 2026-08-06

---

## 1. 今日速览

过去24小时 OpenClaw 保持高强度活跃：新增/更新 Issues 500 条（新开 426，关闭 74），PR 更新 500 条（待合并 435，已合并 65），无新版本发布。项目处于密集修复期，核心关注点集中在会话状态管理、消息丢失和网关稳定性。社区贡献活跃，多个 P0/P1 级别问题已进入 maintainer review 阶段，项目健康度良好但积压较重。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

**今日合并/关闭的重要 PR：**

- **#119146** — `fix(scripts): bound gh-read gh CLI child process`（已关闭）  
  为 `gh-read` 脚本的 gh CLI 子进程添加了可配置超时，防止因 `gh` 调用卡死导致 CI 任务无限挂起。  
  👉 [PR #119146](https://github.com/openclaw/openclaw/pull/119146)

- **#110601** — `fix(scripts): bound ci-run-timings git and GitHub CLI operations`（已关闭）  
  为 `ci-run-timings` 脚本中的 `git ls-remote` 等操作添加超时保护，避免网络不可达时 CI 计时报告完全阻塞。  
  👉 [PR #110601](https://github.com/openclaw/openclaw/pull/110601)

**整体进展：** 合并 PR 集中在脚本层稳定性加固（超时保护），为自动化流程提供了更强的容错能力。大量 P1 修复 PR（如 #119326、#119221、#117305）仍在 maintainer review 或等待作者回复，尚未进入合并队列。

---

## 4. 社区热点

**评论数 Top Issues：**

| Issue | 评论数 | 标签 | 核心议题 |
|-------|--------|------|----------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | 58 | P1, bug, diamond lobster | 实时语音会话未绑定资源上限，导致供应商状态积压 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 27 | P2, enhancement, security | 按来源对 Agent 记忆进行信任标签化，防止记忆投毒 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 25 | P1, bug, diamond lobster | 子 Agent 完成结果静默丢失，无重试/通知/自动重启 |
| [#118846](https://github.com/openclaw/openclaw/issues/118846) | 19 | P1, crash-loop, CLOSED | 网关主线程启动即被 plugin-metadata 快照占满，导致 WebSocket 连接失败 |
| [#86519](https://github.com/openclaw/openclaw/issues/86519) | 13 | P1, bug, regression | Telegram 渠道 5.20 更新后重复发送相同回复 2-10 次 |

**热点分析：**
- **#116201** 高讨论量反映社区对实时语音场景下资源失控的严重担忧，该问题涉及多供应商帧积压和会话状态管理。
- **#7707** 信任标签化需求与安全团队关注高度一致，属于长期架构增强项。
- **#44925** 和 **#118846** 是近期高频反馈的稳定性痛点，直接影响生产可用性。

---

## 5. Bug 与稳定性

**P0 级问题：**

| Issue | 摘要 | Fix PR |
|-------|------|--------|
| [#119263](https://github.com/openclaw/openclaw/issues/119263) | Agent DB v14→v15 迁移失败：`no such column: entry_valid`，网关拒绝启动 | 待修复 |
| [#119090](https://github.com/openclaw/openclaw/issues/119090) | 媒体清理失败时永久删除会话生成的媒体文件 | 待修复 |
| [#118846](https://github.com/openclaw/openclaw/issues/118846) | 网关主线程启动即被 plugin-metadata 快照占满，WebSocket 连接失败（1006） | ✅ 已关闭 |

**P1 级问题：**

| Issue | 摘要 | Fix PR |
|-------|------|--------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | 实时语音会话资源未绑定上限，停滞时积压 provider 状态 | 待修复 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 子 Agent 完成结果静默丢失 | 待修复 |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | 大 SQLite 转录清理阻塞网关事件循环 | 待修复 |
| [#85251](https://github.com/openclaw/openclaw/issues/85251) | Codex app-server 发出 `turn/started` 后静默，嵌入式运行挂起 | 待修复 |
| [#106231](https://github.com/openclaw/openclaw/issues/106231) | 循环检测阻止 exec 但未终止卡死的 Agent 运行 | 关联 PR #119221 |
| [#109490](https://github.com/openclaw/openclaw/issues/109490) | Telegram 渠道消息工具中断后承诺任务未执行 | 待修复 |
| [#96692](https://github.com/openclaw/openclaw/issues/96692) | Slack 线程回复生成但丢失（原始元组丢失） | 待修复 |
| [#86519](https://github.com/openclaw/openclaw/issues/86519) | Telegram 渠道重复回复回归（5.20 引入） | 待修复 |
| [#119401](https://github.com/openclaw/openclaw/issues/119401) | `NO_REPLY` 抑制无条件生效，忽略 `silentReply` 策略 | 待修复 |
| [#106786](https://github.com/openclaw/openclaw/issues/106786) | gpt-5.6-* 模型被广告但 silently 回退到备用模型 | 待修复 |

**近期回归问题：**
- **#86519** — Telegram 重复回复（5.20→5.22 改善未根治）
- **#77306** — QQBot 消息重复发送（`message_sending` hook 回放触发）
- **#107873** — Embedded prompt-lock 接管后工具失败时中止可见 WebChat 轮次而非重试

---

## 6. 功能请求与路线图信号

| Issue | 请求内容 | 关联 PR | 纳入可能性 |
|-------|----------|---------|------------|
| [#6615](https://github.com/openclaw/openclaw/issues/6615) | exec-approvals 支持 denylist（除 X 外允许一切） | 有 linked PR | 高 |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) | Control UI 支持 MathJax/LaTeX 渲染 | 无 | 中 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 按来源对 Agent 记忆进行信任标签化 | 无 | 中长期 |
| [#16555](https://github.com/openclaw/openclaw/issues/16555) | 投递队列消息支持 TTL/过期 | 无 | 中 |
| [#53654](https://github.com/openclaw/openclaw/issues/53654) | Discord 支持 messageUpdate/messageDelete 事件 | 无 | 中 |
| [#41965](https://github.com/openclaw/openclaw/issues/41965) | 强制媒体以文档附件形式发送（如 `#doc`） | 无 | 低 |

**路线图信号：** 安全与可观测性相关请求（#6615、#7707）持续获得社区关注，与当前维护团队强化 exec 安全和记忆完整性的方向一致。`#16555` TTL 需求与现有队列持久化 PR #82572 可形成互补。

---

## 7. 用户反馈摘要

**核心痛点：**
- **会话状态不可靠**：多起 Issue 反映会话 ID 旋转、转录丢失、子 Agent 结果静默丢失等问题，用户强调"结果丢失且无任何通知"是最大挫败点。
- **渠道稳定性差**：Telegram 重复回复、Slack 线程丢失、QQBot 重复发送等多渠道消息完整性问题集中爆发。
- **启动与迁移风险**：v14→v15 数据库迁移失败导致网关拒绝启动，自动更新后残留旧哈希模块引用，严重影响运维信心。
- **资源控制缺失**：实时语音会话、大转录清理、plugin-metadata 快照等操作未受资源上限约束，直接导致网关线程饥饿。

**用户满意点：**
- 部分回归问题（如 Telegram 重复回复）在 5.22 版本中得到缓解。
- 维护团队对 P0 问题的响应速度较快，如 #118846 已在 3 天内关闭。

---

## 8. 待处理积压

**长期未响应的重要 Issues（无 stale 标记）：**

| Issue | 创建时间 | 评论数 | 优先级 | 状态 |
|-------|----------|--------|--------|------|
| [#46031](https://github.com/openclaw/openclaw/issues/46031) | 2026-03-14 | 6 | P2 | `auth.order` 对 GitHub Copilot 渠道无效，始终使用首个 profile |
| [#106779](https://github.com/openclaw/openclaw/issues/106779) | 2026-07-13 | 12 | P1, CLOSED | llama.cpp 本地模型 400 错误（已关闭但可能需回归验证） |
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | 2026-04-24 | 6 | P0, stale | 计费冷却期在用户充值后仍持续数小时 |
| [#115642](https://github.com/openclaw/openclaw/issues/115642) | 2026-07-29 | 6 | P1 | 订阅认证计费冷却期过长，需探活恢复机制 |
| [#67419](https://github.com/openclaw/openclaw/issues/67419) | 2026-04-15 | 10 | P2 | Bootstrap 文件每轮重复注入，浪费 20-30% 上下文 token |
| [#53540](https://github.com/openclaw/openclaw/issues/53540) | 2026-03-24 | 7 | P1 | 大参数工具调用超时导致"Network connection lost"误报 |

**建议关注：**
- **#70903** 和 **#115642** 同属计费冷却机制问题，建议合并讨论。
- **#119263**（DB 迁移失败）和 **#119090**（媒体清理误删）作为 P0，需维护团队优先处理。
- **#119326**（账户级历史限制被忽略）和 **#119221**（会话 ID 旋转时转录追加）等修复 PR 已就绪，等待 maintainer review。

---

## 横向生态对比



# 2026-08-06 个人 AI 助手/自主智能体开源生态横向对比分析

---

## 1. 生态全景

2026年8月，个人 AI 助手开源生态呈现**多项目并行活跃、聚焦稳定性与协议兼容**的整体态势。OpenClaw 作为核心参照项目保持高强度活跃（日增 1000+ Issue/PR），社区规模与问题积压量均居首位；NanoBot、Hermes Agent、ZeroClaw 等中量级项目分别侧重 WebUI 体验、多平台适配与安全加固，形成差异化竞争格局。生态整体从"功能野蛮生长"进入"质量巩固期"——多个项目近期发布版本后集中暴露回归问题，MCP 集成、渠道投递稳定性、会话状态管理成为跨项目共性痛点。IronClaw、LobsterAI 已率先推出新版，ZeroClaw 和 Hermes Agent 正处于 RFC 密集讨论阶段，技术路线向协议标准化与安全可控方向收敛。

---

## 2. 各项目活跃度对比

| 项目 | Issue 更新 | PR 活动 | Release | 健康度 | 核心阶段 |
|------|-----------|---------|---------|--------|----------|
| **OpenClaw** | 500（新426/闭74） | 500（合并65/待435） | 无 | 🟢 良好（积压重） | 密集修复期 |
| **IronClaw** | 44（新34/闭10） | 50（合并17/待33） | v1.1.0-rc.1 | 🟢 良好 | 功能扩展+质量加固 |
| **ZeroClaw** | 50 | 50（合并1/待49） | 无 | 🟡 中等偏上 | 安全加固+RFC治理 |
| **Hermes Agent** | 50（新45/闭5） | 50（合并4/待46） | 无（v0.20.0有回归） | 🟡 中等偏紧张 | 重构+回归修复并行 |
| **LobsterAI** | 3（开放） | 10（合并） | v2026.8.5 | 🟢 良好 | 稳定迭代 |
| **NanoBot** | 4 | 14（合并5/待9） | 无 | 🟢 良好 | 体验精细化 |
| **NanoClaw** | 2 | 12（合并2/待10） | 无 | 🟢 良好 | 架构修复+通道扩展 |
| **PicoClaw** | 0 | 4（合并1/待3） | 无 | 🟡 中等 | 稳定迭代 |
| **NullClaw** | 0 | 2（待合并） | 无 | 🟡 一般 | 轻度维护 |
| **Moltis/ZeptoClaw** | 0 | 0 | 无 | — | 无活动 |
| **CoPaw** | — | — | — | ⚠️ 摘要失败 | 未知 |

---

## 3. OpenClaw 在生态中的定位

**社区规模与技术路线优势：**
- OpenClaw 日 Issue/PR 量（各 500 条）是第二梯队（IronClaw/Hermes/ZeroClaw 各 50 条左右）的 **10 倍**，社区活跃度和贡献体量显著领先。
- 技术路线聚焦**多通道网关架构**与**会话状态管理**，当前核心痛点（消息丢失、子 Agent 结果静默、网关线程饥饿）反映其生产级部署规模较大，问题暴露更充分。

**与同类项目差异：**
- 相比 IronClaw 的 MCP 扩展生态路线、ZeroClaw 的安全/协议兼容路线，OpenClaw 更侧重**通道稳定性与资源控制**（如实时语音会话上限、plugin-metadata 快照优化）。
- 相比 NanoBot/ NanoClaw 的轻量级定位，OpenClaw 定位为**企业级/生产级网关**，积压的 P0/P1 问题（DB 迁移失败、媒体清理误删）直接反映其复杂度和运维压力。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **MCP 工具集成与错误处理** | NanoBot、IronClaw、NanoClaw、ZeroClaw | NanoBot #5237 MCP 业务错误无法识别；IronClaw #7251/#7250 MCP 认证猜测而非主动发现；NanoClaw #3190 新增 Tavily MCP skill |
| **渠道投递稳定性** | OpenClaw、Hermes Agent、IronClaw、NanoBot | OpenClaw Telegram 重复回复 #86519；IronClaw Slack DM 错投 Telegram #7249；Hermes 飞书授权逻辑回归 #79841 |
| **会话状态/资源管理** | OpenClaw、ZeroClaw、Hermes Agent | OpenClaw 子 Agent 结果静默丢失 #44925；ZeroClaw 运行时会话所有权 RFC #9487；Hermes macOS 高负载消息串场 #79853 |
| **安全与认证** | ZeroClaw、PicoClaw、IronClaw | ZeroClaw SSRF 闸门 #8713、WebAuthn 校验 #9781；PicoClaw Anthropic OAuth setup-token #926；IronClaw Configuration-as-Code #3036 |
| **网关/通道运行时稳定性** | OpenClaw、NullClaw、Hermes Agent | OpenClaw 网关主线程被快照占满 #118846；NullClaw 通道夜间静默 #972；Hermes lifecycle_guard null byte 崩溃 #77780 |
| **Agent 间协作** | NanoClaw、ZeroClaw | NanoClaw #3187 移除 SendMessage 限制打通 agent-to-agent；ZeroClaw #9324 A2A outbound client |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 多通道网关、会话状态管理、资源控制 | 生产环境部署者、企业用户 | 集中式网关架构，强依赖 SQLite+WebSocket，积压问题反映复杂度高 |
| **IronClaw** | MCP 扩展生态、IronHub 深度集成、Skill 系统 | 扩展开发者、MCP 生态参与者 | Reborn 架构，Rust 核心，型级证明（ChannelAdapter）确保投递安全 |
| **ZeroClaw** | 安全加固、协议兼容（Chat Completions）、Goal Mode | 安全敏感用户、多协议对接需求 | RFC 治理模式成熟，WASM 插件系统，Session 所有权机制 |
| **Hermes Agent** | God-file 重构、多平台（Telegram/企微/飞书） | 中文用户、多平台接入需求 | 巨型文件拆解路线明确，平台路由抽出优先级高 |
| **NanoBot** | WebUI 体验、Quick Chat、元搜索 | 个人用户、WebUI 重度使用者 | 体验精细化路线，临时会话/共享终端等交互创新 |
| **LobsterAI** | 签到体验、企服账号隔离、对话搜索 | 企业用户、协作用户 | 依赖 OpenClaw 底层，侧重上层功能与品牌物料 |
| **NanoClaw** | Agent-to-Agent 通信、Dial 通道、Skill 扩展 | 多 Agent 协作场景用户 | 架构修复优先（command-gate 写入安全），通道矩阵扩展中 |
| **PicoClaw** | OAuth 认证灵活性、模型 fallback | 部署友好性优先用户 | 轻量级，关注构建稳定性与认证方式扩展 |
| **NullClaw** | 运行时稳定性（堆栈/监督循环） | 24/7 网关部署用户 | 底层运行时加固路线，无新功能信号 |

---

## 6. 社区热度与成熟度

| 层级 | 项目 | 特征 |
|------|------|------|
| **快速迭代阶段** | OpenClaw、IronClaw、Hermes Agent、ZeroClaw | 日增 Issue/PR 50-500 条，新版本发布后集中暴露回归问题，维护团队高强度响应，处于功能扩张与质量加固并行期 |
| **体验精细化阶段** | NanoBot、LobsterAI | 活跃度中等（PR 10-14 条/日），聚焦 WebUI 交互、功能打磨，Bug 修复节奏稳健，健康度良好 |
| **稳定迭代/轻度维护** | PicoClaw、NanoClaw、NullClaw | 日更新 2-12 条，核心贡献者集中，PR 积压未合并现象存在（NullClaw 2 条待合并无评论），处于维护节奏期 |
| **低活跃/停滞** | Moltis、ZeptoClaw、CoPaw | 无活动或摘要失败，生态存在感弱 |

**成熟度信号：**
- **高成熟度**：IronClaw（v1.1.0-rc.1 已发布，MCP 扩展机制成型）、LobsterAI（版本节奏稳定，依赖管理可见）
- **中成熟度**：OpenClaw（社区规模大但积压重）、ZeroClaw（RFC 治理机制完善但 Bug 静默故障需关注）
- **成长期**：NanoBot（功能快速落地但 MCP 错误处理等核心路径待完善）、NanoClaw（架构修复优先）

---

## 7. 值得关注的趋势信号

| 趋势 | 信号来源 | 对开发者的参考价值 |
|------|----------|-------------------|
| **MCP 生态成为标配** | NanoBot（元搜索集成）、IronClaw（MCP 认证链路问题）、NanoClaw（Tavily skill） | 未来 1-2 个版本，MCP 工具链集成能力将成为项目竞争力核心指标；错误处理语义（`isError` vs 业务错误）是集成质量的关键差异点 |
| **渠道投递正确性成为稳定性分水岭** | OpenClaw（Telegram 重复回复）、IronClaw（Slack DM 错投 Telegram）、Hermes（飞书授权回归） | 多通道网关的"投递原子性"和"渠道隔离"是生产可用性的核心门槛，型级证明（如 IronClaw ChannelAdapter）代表架构演进方向 |
| **Agent 间协作从概念走向实现** | NanoClaw（移除 SendMessage 限制）、ZeroClaw（A2A outbound client） | 多 Agent 协作场景需求显性化，agent-to-agent 消息传递机制将成为差异化能力 |
| **安全从附加功能变为核心架构** | ZeroClaw（SSRF 闸门、WebAuthn 校验）、PicoClaw（OAuth setup-token）、OpenClaw（记忆信任标签化） | 安全能力建设从"事后修复"转向"架构内建"，OAuth 灵活认证、SSRF 防护、记忆投毒防御将成为标配 |
| **网关运行时稳定性是生产部署关键** | OpenClaw（网关线程饥饿）、NullClaw（通道夜间静默）、Hermes（lifecycle_guard 崩溃） | 长时间运行的 Agent 网关需解决"静默故障"问题（无报错但功能失效），监督循环和自动恢复机制是运维体验核心 |
| **协议兼容性决定生态接入能力** | ZeroClaw（Chat Completions Profile RFC #8603）、OpenClaw（gpt-5.6 模型回退问题） | 与 OpenAI Chat Completions 协议兼容的项目（如 ZeroClaw）更容易接入 Open WebUI、Continue.dev 等主流客户端，生态协同价值显著 |

**综合建议：** 对于 AI 智能体开发者，当前生态已进入"质量巩固期"——功能扩展速度放缓，稳定性、安全性、协议兼容性成为竞争焦点。选择开源项目时，建议重点关注：**MCP 错误处理语义完整性**、**多渠道投递原子性保障机制**、**网关运行时自愈能力**，以及**与主流客户端的协议兼容程度**。OpenClaw 社区规模最大但积压重，适合深度参与贡献；IronClaw 和 ZeroClaw 架构演进方向清晰，适合关注长期技术路线；NanoBot 和 LobsterAI 体验打磨较快，适合个人用户快速上手。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-06

## 1. 今日速览

过去 24 小时 NanoBot 保持较高活跃度，共新增 4 个 Issues 和 14 个 PR（9 待合并 / 5 已关闭）。项目整体处于功能扩展与稳定性修复并行的阶段：WebUI 临时会话模式、快速聊天（Quick Chat）、共享终端等核心体验功能集中落地，同时针对 WhatsApp 音频、MCP 错误处理、Goal 循环等稳定性问题有实质性修复。无新版本发布，但多个关键 PR 已合并，为后续版本积累扎实。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（5 条）

| PR | 类型 | 作者 | 说明 |
|---|---|---|---|
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) | feat | goodtiding5 | 集成 `mst-python` 作为元搜索提供者，通过 Reciprocal Rank Fusion 聚合多引擎结果，显著提升网页搜索覆盖广度。 |
| [#5254](https://github.com/HKUDS/nanobot/pull/5254) | feat | chengyongru | 新增 WebUI provider 原生开关，支持 OpenAI Codex Fast 模式、DeepSeek 网页搜索、xAI Grok X Search 等能力直接通过 `extraBody` 下发。 |
| [#5203](https://github.com/HKUDS/nanobot/pull/5203) | fix | chengyongru | 修复 WhatsApp 出站媒体检测逻辑，改用 libmagic 内容识别替代文件名扩展名，解决音频格式误判问题。 |
| [#5184](https://github.com/HKUDS/nanobot/pull/5184) | feat | Re-bin | 新增 Quick Chat（持久会话）与 Temporary Chat（内存临时会话）功能，前者作为一级入口独立于普通话题列表，后者支持连接级内存隔离。 |
| [#5249](https://github.com/HKUDS/nanobot/pull/5249) | refactor | chengyongru | WebUI 视觉一致性重构：统一菜单/弹窗/面板的层级系统，简化 Skills 和 Channels 布局，移除持久消息的回放动画。 |

**整体推进评估：** 今日合并的 PR 集中于 WebUI 体验升级（临时会话、Quick Chat、视觉优化）和能力扩展（元搜索、Provider 开关），标志着项目正从"基础功能完善"向"用户体验精细化"过渡，整体前进步伐稳健。

---

## 4. 社区热点

### 高关注度 Issue / PR

| 条目 | 类型 | 评论数 | 亮点 |
|---|---|---|---|
| [#5149](https://github.com/HKUDS/nanobot/issues/5149) | Bug | 4 | WhatsApp 音频发送失败问题，用户反馈明确，已有配套 fix PR #5203 已合并，期待回归验证 |
| [#5237](https://github.com/HKUDS/nanobot/issues/5237) | Bug | 2 | MCP tool 返回业务错误时 nanobot 无法识别，导致 LLM 无限等待直至 `tool_timeout` |
| [#5256](https://github.com/HKUDS/nanobot/issues/5256) | Bug | 0 | `/goal` 消息在等待用户回复时产生数十条重复回复，已被 shakewingo 在 PR #5257 中修复 |
| [#5261](https://github.com/HKUDS/nanobot/pull/5261) | Feat | — | 拖拽会话到 composer 生成结构化 mention，交互体验提升，当前待合并 |

**热点分析：** 社区最关切的是 **WhatsApp 渠道的可靠性**（Issue #5149 获 4 条评论）和 **MCP 工具的错误语义处理**（Issue #5237）。后者涉及 agent 核心循环逻辑，可能影响多个 MCP 集成场景。Goal 循环问题（#5256）已触发用户手动干预，修复迫切性较高。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | Fix PR | 状态 |
|---|---|---|---|---|
| P1 | [#5237](https://github.com/HKUDS/nanobot/issues/5237) | MCP tool 返回 `isError=False` 但业务错误的 envelope 时，agent 无法识别失败原因，持续等待 | 暂无 | 🟡 待修 |
| P2 | [#5256](https://github.com/HKUDS/nanobot/issues/5256) | `/goal` 消息在等待用户时产生大量重复回复，形成循环 | [#5257](https://github.com/HKUDS/nanobot/pull/5257) 已提交 | 🟢 有 fix |
| P2 | [#5258](https://github.com/HKUDS/nanobot/pull/5258) | 含凭据的 URL 被转发至远程 Jina reader，存在信息泄露风险 | [#5258](https://github.com/HKUDS/nanobot/pull/5258) 已提交 | 🟢 有 fix |
| P2 | [#5248](https://github.com/HKUDS/nanobot/pull/5248) | Matrix 渠道 `join()` 发送空 POST body，Continuwity 等 homeserver 拒绝导致静默失败 | [#5248](https://github.com/HKUDS/nanobot/pull/5248) 已提交 | 🟢 有 fix |
| — | [#5149](https://github.com/HKUDS/nanobot/issues/5149) | WhatsApp 音频消息发送失败（已有 fix PR #5203 合并，待用户验证） | [#5203](https://github.com/HKUDS/nanobot/pull/5203) ✅ 已合并 | 🟡 待验证 |

**稳定性评估：** 今日报告 4 个 Bug，其中 3 个已有对应 Fix PR，1 个已合并待回归验证。整体 Bug 处理能力较强，但 MCP 错误处理（#5237）尚未修复，可能对 MCP 场景用户影响较大。

---

## 6. 功能请求与路线图信号

| Issue / PR | 需求描述 | 路线图信号 |
|---|---|---|
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) | 在 WebUI 中支持 MCP Apps host，展示 MCP server 附带的 UI 组件 | 🟡 用户主动提出，当前仅作为 Issue，暂无对应 PR，建议纳入后续迭代 |
| [#5261](https://github.com/HKUDS/nanobot/pull/5261) | 拖拽会话到 composer 生成结构化 mention | 🟢 已在开发中，预计下版本上线 |
| [#5253](https://github.com/HKUDS/nanobot/pull/5253) | 项目级共享交互式终端（xterm.js PTY） | 🟢 已在开发中，支持 WebUI 与 agent 共享终端会话 |
| [#5260](https://github.com/HKUDS/nanobot/pull/5260) | 忽略 workspace 内的运行时文件（避免 memory 误追踪） | 🟢 已在开发中，属于基础设施优化 |
| [#5259](https://github.com/HKUDS/nanobot/pull/5259) | 强制临时会话仅使用内存存储 | 🟢 作为 #5252 的配套修复已提交 |

**下版本预测：** Temporary Chat、Quick Chat、共享终端、拖拽 mention 等 WebUI 交互增强功能大概率进入下一个版本；MCP Apps host 支持因涉及 MCP 协议扩展，可能需要单独评估。

---

## 7. 用户反馈摘要

### 核心痛点

1. **WhatsApp 音频发送失败**（#5149）：用户反馈 nanobot 能接收 WhatsApp 音频但无法发送，已通过 PR #5203 修复，建议用户更新版本后验证。

2. **Goal 循环导致消息暴增**（#5256）：用户描述 `/goal` 触发后 agent 在等待期间发送"数十条几乎相同的回复"，需手动干预或等待模型自行识别循环。该问题已在 PR #5257 中修复，通过限制持续目标在空闲轮次中的注入次数解决。

3. **MCP 业务错误无法识别**（#5237）：当 MCP server 返回 `{"code": 404, "msg": "data not exist"}` 且 `isError=False` 时，agent 将其视为成功调用，LLM 无法获知真实失败原因，导致无限等待。此为 MCP 集成场景的关键盲区，尚无 Fix PR。

4. **凭据 URL 泄露风险**（#5258）：含 `user:pass@` 或 token 参数的 URL 被转发至远程 Jina reader，存在凭据泄露隐患，PR #5258 已修复。

### 用户满意度

- WebUI 交互体验持续改进（拖拽、临时会话、Quick Chat）获社区正面反馈
- Matrix 渠道 Continuwity 兼容性问题引发关注，PR #5248 修复后需多 homeserver 验证
- 视觉一致性重构（#5249）属于隐性改进，用户感知可能有限

---

## 8. 待处理积压

| 条目 | 类型 | 创建日期 | 关注点 |
|---|---|---|---|
| [#5237](https://github.com/HKUDS/nanobot/issues/5237) | Bug (P1) | 2026-08-04 | MCP tool 业务错误处理缺失，建议优先修复 |
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) | Enhancement | 2026-08-05 | MCP Apps host WebUI 支持，用户主动请求，暂无开发计划 |
| [#5261](https://github.com/HKUDS/nanobot/pull/5261) | PR (待合并) | 2026-08-06 | 拖拽会话到 composer 功能，今日提交，建议尽快 review |
| [#5253](https://github.com/HKUDS/nanobot/pull/5253) | PR (待合并) | 2026-08-05 | 共享终端功能，涉及 PTY 实现，需测试多平台兼容性 |
| [#5255](https://github.com/HKUDS/nanobot/pull/5255) | PR (Draft) | 2026-08-05 | API 服务状态显示真实性问题，当前为 Draft 状态 |

**维护者提醒：** Issue #5237 涉及 MCP 集成核心路径，当前无 Fix PR，建议优先处理；#5251 的用户需求明确，可评估纳入路线图。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-06

## 1. 今日速览

Hermes Agent 项目今日保持高度活跃：过去24小时共产生 50 条 Issue 更新（新开/活跃 45 条、关闭 5 条）和 50 条 PR 更新（待合并 46 条、已合并/关闭 4 条）。无新版本发布。整体呈现**高强度重构+密集修复**节奏：god-file 分解 Epic 持续推进，v0.20.0 发布后的多平台回归问题集中暴露（Windows/Desktop 面板缺失、Linux gateway 缓存过期），Telegram 平台特性补齐运动同步展开。项目健康度：**中等偏紧张**——重构与修复并行，但 P1 级稳定性问题数量较多需优先关注。

---

## 2. 版本发布

**无新版本发布。**

上一版本 v0.20.0（"The Herald Release"，2026-08-03）的后续影响仍在消化中，今日多个 Issue 直接关联该版本的回归问题。

---

## 3. 项目进展

### 今日已合并/关闭（4 条）

| PR | 类型 | 说明 | 链接 |
|---|---|---|---|
| #53525 | Bugfix | Gateway 端 WebSocket 会话重建保护，修复旧连接断开后会话所有权检查缺失导致的竞态问题（关联 #50005） | [PR #53525](https://github.com/NousResearch/hermes-agent/pull/53525) |
| #61326 | Bugfix | 集中化主 Agent 的受限模型回退逻辑，使无效模型 ID 和配额失败在所有上下文中一致进入回退链 | [PR #61326](https://github.com/NousResearch/hermes-agent/pull/61326) |
| #79820 | Feature | DeepSeek 服务端原生 `web_search` 支持（标记为 duplicate，已有方案） | [Issue #79820](https://github.com/NousResearch/hermes-agent/issues/79820) |
| #74560 | Bugfix | Desktop 双渲染气泡问题（`interimBoundaryPending` 标志重置导致），关联 #63679 | [Issue #74560](https://github.com/NousResearch/hermes-agent/issues/74560) |

### 重构推进

- **#78647**（Epic）：god-file 分解运动继续，`gateway/run.py`（858KB）和 `hermes_cli/main.py`（12,571 行）位列重点目标
- **#79778**：web_server.py 的 console/spa-mount/ws-auth mixins 抽出（Shard S5，5×2×3 方法论）
- **#78631**：`hermes_cli/main.py` 分解专项 Issue

> **进展评估**：今日 4 条已关闭 PR 多为历史积压的精准修复，新合并内容量不大。重构工作持续但无阶段性成果宣告，项目处于"修复回归+拆解巨文件"的双轨状态。

---

## 4. 社区热点

### 评论数 Top 5 Issue

| Issue | 评论数 | 热度原因 | 链接 |
|---|---|---|---|
| **#78647** | 17 | God-file 分解 Epic 的核心统筹帖，定义 repo 级重构策略 | [Issue #78647](https://github.com/NousResearch/hermes-agent/issues/78647) |
| **#77780** | 12 | `lifecycle_guard` 因 null byte 崩溃影响所有 terminal 命令，P2 级严重性 | [Issue #77780](https://github.com/NousResearch/hermes-agent/issues/77780) |
| **#54962** | 11 | `gateway/run.py` 平台路由抽出，858KB 巨文件的直接入口 | [Issue #54962](https://github.com/NousResearch/hermes-agent/issues/54962) |
| **#71941** | 5 | Delegated child context 跨终端快照泄漏，影响多子 agent 场景 | [Issue #71941](https://github.com/NousResearch/hermes-agent/issues/71941) |
| **#78791** | 5 | Telegram Bot API 10.2 特性对齐 Campaign 元 Issue | [Issue #78791](https://github.com/NousResearch/hermes-agent/issues/78791) |

**热点分析**：
- **重构诉求强烈**：Top 3 中有 2 条直接指向 god-file 拆解，社区对代码可维护性的关注度持续高位
- **Telegram 扩展活跃**：#78791 及其子 Issue（#78689–#78693, #78790）构成一个特性补齐 Campaign，反映 Telegram 作为核心平台的重要性上升
- **稳定性焦虑**：#77780 的 terminal 崩溃和 #71941 的 context 泄漏都直接影响日常使用，评论活跃说明用户深度参与调试

---

## 5. Bug 与稳定性

### P1 级（阻塞性）

| Issue | 描述 | Fix PR | 链接 |
|---|---|---|---|
| **#79407** | v0.20.0 回归：Windows Desktop 底部操作面板完全消失，应用变为"仅查看器" | — | [Issue #79407](https://github.com/NousResearch/hermes-agent/issues/79407) |
| **#78574** | Linux 默认 gateway 在 `hermes update` 后未重启，导致 ImportError（新旧模块混存） | — | [Issue #78574](https://github.com/NousResearch/hermes-agent/issues/78574) ⭐1 |

### P2 级（高优先级）

| Issue | 描述 | Fix PR | 链接 |
|---|---|---|---|
| **#77780** | `lifecycle_guard` 因 `ValueError: embedded null byte` 崩溃，影响全部 terminal 命令 | — | [Issue #77780](https://github.com/NousResearch/hermes-agent/issues/77780) |
| **#79562** | 企微 iLink 平台 `/approve` 文本 fallback 首次有效后失效（时序竞态） | — | [Issue #79562](https://github.com/NousResearch/hermes-agent/issues/79562) |
| **#79101** | API 创建 session 时虚拟模型别名被当作真实模型持久化，破坏 gateway 默认 | — | [Issue #79101](https://github.com/NousResearch/hermes-agent/issues/79101) |
| **#79841** | 飞书 DM 授权按钮错误绑定群组策略而非管理员列表（v0.20.0 回归） | — | [Issue #79841](https://github.com/NousResearch/hermes-agent/issues/79841) |
| **#79853** | v0.20.0 macOS：高负载下 CPU >90%、跨会话消息混合 | — | [Issue #79853](https://github.com/NousResearch/hermes-agent/issues/79853) |
| **#79459** | 本地 TTS（Piper/KittenTTS）忽略配置的 voice 参数 | — | [Issue #79459](https://github.com/NousResearch/hermes-agent/issues/79459) |
| **#71941** | Delegated child context 通过共享终端快照持久化 | — | [Issue #71941](https://github.com/NousResearch/hermes-agent/issues/71941) |

### 已有 Fix PR 的 Bug

| Issue | Fix PR | 链接 |
|---|---|---|
| #74560（Desktop 双渲染） | —（Issue 已关闭） | [Issue #74560](https://github.com/NousResearch/hermes-agent/issues/74560) |
| #78788（Telegram callback 未应答） | — | [Issue #78788](https://github.com/NousResearch/hermes-agent/issues/78788) |

> **稳定性评估**：v0.20.0 发布仅 3 天即涌现多平台 P1/P2 回归，**发布质量存在明显风险**。2 个 P1 问题（Windows 面板缺失、Linux gateway 缓存过期）均无可见 Fix PR，需优先处理。

---

## 6. 功能请求与路线图信号

| Issue | 需求 | 路线图信号 | 链接 |
|---|---|---|---|
| **#78307** | 内置 Memory（MEMORY.md / USER.md）的生命周期管理：巡检、去重、冲突检测、可恢复清理 | 中短期：内存管理是 Hermes 核心能力，系统化维护是合理演进方向 | [Issue #78307](https://github.com/NousResearch/hermes-agent/issues/78307) |
| **#78791** | Telegram Bot API 10.2 特性全量对齐（paid broadcast、LinkPreviewOptions、setMessageReaction、批量转发/复制、批量删除、管理员权限 API） | 高优先级：Telegram 作为主力平台，10.2 对齐 Campaign 已形成系列 Issue | [Issue #78791](https://github.com/NousResearch/hermes-agent/issues/78791) |
| **#79856** | Desktop Composer/对话区宽度可配置 | 低优先级：UI 个性化需求，硬编码在 styles.css 中 | [Issue #79856](https://github.com/NousResearch/hermes-agent/issues/79856) |
| **#79858** | 独立对话字体大小设置（不影响全局 UI 缩放） | 低优先级：与 #79856 同属桌面 UX 微调 | [Issue #79858](https://github.com/NousResearch/hermes-agent/issues/79858) |
| **#71985** | Preview 面板弹出为独立窗口 | 中优先级：多屏/分屏场景有用，当前预览窗格与侧边栏耦合 | [Issue #71985](https://github.com/NousResearch/hermes-agent/issues/71985) |
| **#41736** | Assistant 消息中的 Preview 链接路由到文件 Tab（新文件=新 Tab） | 中优先级：改善文件预览工作流 | [Issue #41736](https://github.com/NousResearch/hermes-agent/issues/41736) |

> **路线图判断**：Telegram 10.2 对齐和 Memory 生命周期管理是最可能纳入下一版本的功能信号；桌面 UI 微调类需求（宽度/字体）优先级较低，可能随整体 UX 迭代一起处理。

---

## 7. 用户反馈摘要

### 痛点

| 主题 | 反馈摘要 | 来源 |
|---|---|---|
| **v0.20.0 回归严重** | Windows 桌面面板消失、macOS 高 CPU + 消息串场、飞书授权逻辑错误——用户普遍认为 0.20.0 发布前测试覆盖不足 | #79407, #79853, #79841 |
| **Linux 更新后 gateway 卡顿** | `hermes update` 静默跳过 systemd user gateway 重启，导致 ImportError；用户需手动干预 | #78574 ⭐1 |
| **Terminal 命令不可靠** | lifecycle_guard 对 heredoc/-c payload 中的 null byte 未做防护，直接崩溃中断所有 terminal 操作 | #77780 |
| **成本显示失真** | DeepSeek 等低价模型每次 turn 成本低于 1 美分，但 2dp 格式化后显示 `$0.00`，误导用户认为免费 | #79220 |
| **TTS 配置不生效** | Piper/KittenTTS 忽略 `voice` 参数，始终使用默认音色，用户无法选择发音人 | #79459 |
| **企微审批流程中断** | 首次 `/approve` 后后续审批被静默忽略，危险命令审批 UI 形同虚设 | #79562 |

### 满意点

- AIDE² 自我改进系统 PR（#77236）获得社区关注，7 commits + 198 新测试 + CI green，体现项目在 AI 驱动自改进方向的探索
- God-file 分解运动有明确的 repo 级策略（"all god files are sharded, never reverted"），用户认可长期重构方向
- Docker `ddgs` 安装问题的修复（#75566）解决了容器部署的痛点

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 严重度 | 积压原因 | 链接 |
|---|---|---|---|---|
| **#78574** | 2026-08-04 | P1 | Linux gateway 更新后缓存过期，无 Fix PR；1 个 👍 | [Issue #78574](https://github.com/NousResearch/hermes-agent/issues/78574) |
| **#79407** | 2026-08-05 | P1 | Windows Desktop v0.20.0 回归，面板缺失，无 Fix PR | [Issue #79407](https://github.com/NousResearch/hermes-agent/issues/79407) |
| **#79853** | 2026-08-06 | P2 | macOS 高性能消耗 + 消息串场，刚报告尚无 Fix | [Issue #79853](https://github.com/NousResearch/hermes-agent/issues/79853) |
| **#54962** | 2026-06-29 | P3 | `gateway/run.py` 858KB 平台路由抽出，长期开单 | [Issue #54962](https://github.com/NousResearch/hermes-agent/issues/54962) |
| **#78631** | 2026-08-04 | P3 | `hermes_cli/main.py` 12,571 行分解，新开单 | [Issue #78631](https://github.com/NousResearch/hermes-agent/issues/78631) |

### 需维护者关注

1. **v0.20.0 回归紧急修复**：#79407（Windows 面板缺失）和 #78574（Linux gateway 过期）均为 P1 且无 Fix PR，建议优先处理
2. **God-file 分解进展**：#78647 Epic 下已有 #79778（Shard S5）推进，但 #54962（gateway/run.py）和 #78631（hermes_cli/main.py）仍无进展，需分配资源
3. **Telegram Campaign 协调**：#78791 下多个 duplicate Issue（#78689–#78693, #78790）建议合并跟踪，避免碎片化

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-06

---

## 1. 今日速览

PicoClaw 在过去 24 小时内呈现**中低活跃度**：0 条 Issue 更新，4 条 PR 变动（1 条合并，3 条待处理）。核心进展为 Anthropic OAuth setup-token 登录功能的正式合并（#926），扩展了认证方式的灵活性。社区维护工作持续进行，包括锁文件修复和安装脚本整合，但未发现紧急 Bug 或新版本发布，项目整体处于稳定迭代期。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#926](https://github.com/sipeed/picoclaw/pull/926) | enhancement (provider) | 新增 Anthropic OAuth setup-token 登录支持，同时集成 usage 端点展示 5 小时/7 天用量统计，并完善 OAuth token 的流式支持 |

**影响评估**：此次合并显著丰富了 Anthropic 的认证生态，使开发者可通过 `--setup-token` 标志或交互式菜单完成 OAuth 授权，降低了 API Key 的依赖门槛，对生产环境部署更具友好性。

### 待合并 PR（3 条）

- **#3318** — 修复 `pnpm-lock.yaml` 中 `semver@7.8.5` 重复映射键导致的锁文件损坏问题，直接影响前端构建稳定性。
- **#3200** — 引入可配置的模型默认 fallback 链，支持在 Web UI 和后端 API 层面持久化，提升多模型容错能力。
- **#1951** — 将安装脚本从 `picoclaw_docs` 仓库迁移至主仓库，统一维护入口，减少文档/代码割裂。

---

## 4. 社区热点

| PR | 状态 | 关注点 |
|---|---|---|
| [#926](https://github.com/sipeed/picoclaw/pull/926) | ✅ 已合并 | Anthropic OAuth 支持，作者 BallerIsLeet |
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) | 🔄 待处理 | pnpm 锁文件修复，作者 nuestraai（2026-08-05 提交） |
| [#3200](https://github.com/sipeed/picoclaw/pull/3200) | 🔄 待处理 | 模型 fallback 链配置化，作者 lc6464 |
| [#1951](https://github.com/sipeed/picoclaw/pull/1951) | 🔄 待处理 | 安装脚本迁移，作者 lc6464 |

**诉求分析**：
- **#926** 反映了用户对 OAuth 认证路径的持续需求，特别是 setup-token 模式在自动化部署场景中的价值。
- **#3318** 暴露了依赖管理中的潜在构建风险，修复后有助于减少新手用户的安装障碍。
- **#3200** 和 **#1951** 均来自同一作者 lc6464，显示其对项目架构稳定性和可维护性的长期关注。

---

## 5. Bug 与稳定性

- **#3318**（中等严重程度）— `pnpm-lock.yaml` 包含重复映射键 `semver@7.8.5`，导致 pnpm 报错 `ERR_PNPM_BROKEN_LOCKFILE`，阻碍前端构建。该 PR 本身即为修复方案，待合并后解决。

> 今日无严重崩溃、回归或高危 Bug 报告。

---

## 6. 功能请求与路线图信号

| 需求方向 | 关联 PR | 纳入下一版本的可能性 |
|---|---|---|
| 多模型容错 / 自动降级 | [#3200](https://github.com/sipeed/picoclaw/pull/3200) | ⭐ 高（PR 已就绪，UI+API 双端支持） |
| 安装体验统一化 | [#1951](https://github.com/sipeed/picoclaw/pull/1951) | ⭐ 高（维护成本优化，低风险） |
| OAuth 认证扩展 | [#926](https://github.com/sipeed/picoclaw/pull/926) | ✅ 已合并 |

**判断**：#3200 和 #1951 具备明确的实用价值且代码质量稳定，预计将在近期版本中合并；#3318 为必要的工程修复，优先级同样较高。

---

## 7. 用户反馈摘要

今日无新增 Issue，无法提取新评论反馈。基于已关闭的 #926，用户痛点主要集中在：

- **认证灵活性**：希望支持非 API Key 的授权方式（如 OAuth setup-token），适配企业级或 CI/CD 场景。
- **用量可见性**：需要内建查询 Anthropic 使用量（5h/7d 周期），便于成本监控。
- **构建稳定性**：锁文件损坏类问题影响新手部署体验，亟需自动化或人工修复。

---

## 8. 待处理积压

| PR | 提交时间 | 待处理时长 | 建议优先级 |
|---|---|---|---|
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) | 2026-08-05 | ~1 天 | 高（构建阻断） |
| [#3200](https://github.com/sipeed/picoclaw/pull/3200) | 2026-07-01 | ~36 天 | 高（核心功能） |
| [#1951](https://github.com/sipeed/picoclaw/pull/1951) | 2026-03-24 | ~135 天 | 中（维护优化） |

> ⚠️ **#3200** 和 **#1951** 已等待较长时间，建议维护者评估当前分支状态并尽快响应，以避免社区贡献者流失。

---

**项目健康度评级**：🟡 中等 — 核心功能持续迭代，但 Issue 响应较缓，部分 PR 积压时间偏长。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-08-06

## 1. 今日速览

过去24小时 NanoClaw 保持中等活跃度：**2 条 Issue 更新**，**12 条 PR 活动**（10 待合并，2 已关闭）。无新版本发布。核心方向集中在：数据库写入安全修复、WhatsApp 连接稳定性加固、MCP 工具链扩展以及 agent-to-agent 消息传递机制完善。整体项目健康度良好，PR 合并节奏稳定，社区贡献活跃。

---

## 2. 版本发布

暂无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的 PR

| PR | 作者 | 状态 | 说明 |
|----|------|------|------|
| [#3175](https://github.com/nanocoai/nanoclaw/pull/3175) | Joi | CLOSED | 原始 command-gate 路由修复 PR，后被 #3192 替代/覆盖 |
| [#3187](https://github.com/nanocoai/nanoclaw/pull/3187) | dim0627 | CLOSED | 禁止内置 `SendMessage` 以实现 agent-to-agent 消息传递（已合入主线） |

**关键推进：**
- **#3187** 的关闭意味着 agent 间消息传递的核心限制已被移除，为多 agent 协作场景铺平道路。
- **#3175 → #3192** 的演进表明 command-gate 写入修复经过 review 迭代后以更严谨的方式重新提交。

---

## 4. 社区热点

| 类型 | 编号 | 标题 | 活跃度 | 诉求分析 |
|------|------|------|--------|----------|
| Issue | [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) | Signal 图片/PDF 附件在容器内不可达 | 新报告，活跃 | 用户反馈 Signal 通道媒体文件传递存在容器化隔离缺陷，影响多模态对话体验 |
| Issue | [#2006](https://github.com/nanocoai/nanoclaw/issues/2006) | Debian 12 LXC 安装时 Docker socket 权限拒绝 | 新报告，活跃 | 安装脚本在 LXC 环境下 recovery 路径未正确触发，影响部署成功率 |
| PR | [#3192](https://github.com/nanocoai/nanoclaw/pull/3192) | command-gate 拒绝路由修复 | 活跃 review | 涉及数据库单写入者规则，属于核心架构修复 |
| PR | [#3190](https://github.com/nanocoai/nanoclaw/pull/3190) | 新增 Tavily MCP 工具 skill | 刚提交 | 社区贡献搜索能力，扩展 agent 信息获取渠道 |
| PR | [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | 添加 Dial 通道支持 | 长期活跃 | 新增通话类通道集成，扩展消息渠道矩阵 |

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 描述 | Fix PR |
|--------|----------|------|--------|
| 🔴 高 | [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) | Signal 媒体附件在 agent 容器内无法访问 | 暂无 |
| 🟠 中 | [#2006](https://github.com/nanocoai/nanoclaw/issues/2006) | Debian 12 LXC 环境下 Docker 权限恢复路径失效 | 暂无 |
| 🟡 低 | [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) | 未知斜杠命令被错误分类导致响应静默丢弃 | [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) [待合并] |
| 🟡 低 | [#3191](https://github.com/nanocoai/nanoclaw/pull/3191) | WhatsApp 未登录会话导致 host 启动挂起 | [#3191](https://github.com/nanocoai/nanoclaw/pull/3191) [待合并] |

---

## 6. 功能请求与路线图信号

| 方向 | PR | 状态 | 判断 |
|------|-----|------|------|
| 🔍 搜索能力扩展 | [#3190](https://github.com/nanocoai/nanoclaw/pull/3190) — Tavily MCP skill | 待合并 | 高可能性纳入下一版本，补充 agent 实时信息获取 |
| 📞 新通道接入 | [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) — Dial 通道 | 待合并 | 中长期路线图信号，扩展语音/通话类集成 |
| 🛠 调试工具 | [#3189](https://github.com/nanocoai/nanoclaw/pull/3189) — `add-why` skill（解释消息处理过程） | 待合并 | 开发者体验改进，可能作为诊断工具集一部分 |
| 🔌 网络代理支持 | [#3188](https://github.com/nanocoai/nanoclaw/pull/3188) — MCP 服务器转发 OneCLI 网关环境变量 | 待合并 | 企业/代理环境部署关键修复 |
| 🧹 技术债清理 | [#3172](https://github.com/nanocoai/nanoclaw/pull/3172) — 移除过期 qodo 和 Google MCP skills | 待合并 | 维护性操作，降低认知负担 |

---

## 7. 用户反馈摘要

**痛点：**
1. **容器化隔离与文件访问**（#2528）：用户期望 agent 能直接处理 Signal 收到的媒体附件，当前容器内路径不可达导致多模态交互中断。
2. **LXC 环境部署体验**（#2006）：Proxmox LXC 容器环境下 Docker 权限配置失败，且安装脚本的 recovery 路径未能正确执行，影响首次部署成功率。
3. **WhatsApp 会话状态挂起**：未登录的 WhatsApp 会话会导致 host 启动阻塞，缺乏超时保护。

**正面信号：**
- 社区对 skill 系统的扩展热情高涨（Tavily、add-why 等多个 skill PR 同日提交）。
- 核心架构修复（command-gate 写入安全、agent-to-agent 消息）正在稳步推进。

---

## 8. 待处理积压

| 类型 | 编号 | 创建时间 | 距今 | 建议优先级 |
|------|------|----------|------|------------|
| 🐛 Bug | [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) | 2026-05-18 | ~80 天 | 🔴 高 — Signal 媒体访问是核心体验问题 |
| 🐛 Bug | [#2006](https://github.com/nanocoai/nanoclaw/issues/2006) | 2026-04-25 | ~103 天 | 🟠 中 — 影响 LXC 用户部署，需确认 recovery 路径 |
| 🛠 PR | [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) | 2026-05-08 | ~90 天 | 🟡 低 — 小修复，久未合并 |
| 🛠 PR | [#3156](https://github.com/nanocoai/nanoclaw/pull/3156) | 2026-07-30 | ~7 天 | 🟡 低 — 附件结构化传递修复，近期提交 |

> **维护者提示：** Issue #2528 和 #2006 均已开放超过 80 天且尚无 fix PR，建议优先分配资源响应。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 — 2026-08-06

---

## 1. 今日速览

NullClaw 今日整体活跃度偏低：24小时内无 Issue 更新，无新版本发布，仅有 **2 条待合并 PR**（均由核心贡献者 `raskevichai` 提交）。两条 PR 均针对运行时与通道层面的底层稳定性修复，未涉及新功能开发。项目处于**轻度维护节奏**，无紧急阻塞事件，但 PR 积压未合并，需关注维护者响应时效。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

今日有 **2 条 PR 待合并**，均聚焦运行时稳定性修复，尚未合并：

- **#985** — 修复 Agent 运行时堆栈过小的问题。`SESSION_TURN_STACK_SIZE` 原复用 `HEAVY_RUNTIME_STACK_SIZE`（仅 2 MiB），导致 `SessionManager.processMessage*()` / `Agent.turn()` 路径存在栈溢出风险。修复后提升为 **16 MiB**，直接关闭 **#976**。
- **#984** — 修复通道监督逻辑缺陷。Telegram 和 Matrix 通道在夜间空闲后会陷入静默状态，`nullclaw agent` 仍可响应但通道层无法恢复，必须手动重启网关。根本原因是 `supervisionLoop` 无法感知死掉的轮询线程。修复后关闭 **#972**。

**进度评估**：两条 PR 均为稳定性修复，合并后能消除已知运行时隐患，但对功能演进无直接推动。当前无已合并 PR，项目代码库今日无净变更。

---

## 4. 社区热点

今日无新增 Issue，讨论集中在以下两条 PR：

- **[PR #985](https://github.com/nullclaw/nullclaw/pull/985)** — 堆栈大小修复。背后诉求：用户在长时间运行的 Agent 会话中偶发栈溢出/崩溃，影响生产部署可靠性。
- **[PR #984](https://github.com/nullclaw/nullclaw/pull/984)** — 通道轮询线程僵死修复。背后诉求：多通道（Telegram / Matrix）在夜间空闲后静默是高频痛点，用户反映需手动重启网关，运维体验差。

两条 PR 均由同一贡献者提交，且均标注为 `fix`，反映出当前社区需求主要集中在**运行时可靠性**而非新功能。

---

## 5. Bug 与稳定性

| 问题 | 严重级别 | 关联 PR | 状态 |
|------|----------|---------|------|
| [#976](https://github.com/nullclaw/nullclaw/issues/976) — Agent turn 路径栈溢出风险 | 中 | #985 | Fix PR 待合并 |
| [#972](https://github.com/nullclaw/nullclaw/issues/972) — Telegram/Matrix 通道夜间静默无法自动恢复 | 高 | #984 | Fix PR 待合并 |

**分析**：两条均为稳定性 Bug，#972 影响生产环境可用性（需手动重启），优先级更高。目前均有对应 PR，待合并后即关闭。

---

## 6. 功能请求与路线图信号

今日无新功能请求。从现有 PR 性质判断，当前路线图重心在 **运行时健壮性加固**（堆栈、监督循环、通道恢复），尚未释放明确的新功能信号。建议关注后续是否有关于多通道并发调度或 Agent 异步处理能力的 PR。

---

## 7. 用户反馈摘要

今日无新增 Issue 评论，无直接用户反馈。结合 PR 摘要可推断：

- **痛点**：通道夜间静默需手动重启是最高频抱怨点（#972），直接影响多通道部署的可用性信心。
- **满意点**：监督循环（supervisor）的设计意图已被用户认可，问题出在实现盲区而非架构缺陷。
- **使用场景**：24/7 运行的 AI Agent 网关，同时接入 Telegram 和 Matrix，对稳定性要求高。

---

## 8. 待处理积压

| 类型 | ID | 描述 | 风险提示 |
|------|----|------|----------|
| PR | [#985](https://github.com/nullclaw/nullclaw/pull/985) | Agent 堆栈大小修复 | 待合并，影响运行时稳定性 |
| PR | [#984](https://github.com/nullclaw/nullclaw/pull/984) | 通道死线程自动清理 | 待合并，影响多通道可用性 |

两条 PR 均创建至今未合并、无评论反馈，建议维护者尽快 Review。当前 Issue/PR 回流速度较慢，若积压持续可能影响社区贡献积极性。

---

**项目健康度评分**：🟡 **一般** — 无紧急事故，但 PR 合并速度偏慢，活跃度有限，稳定性修复已就绪待发布。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期：2026-08-06**

---

## 1. 今日速览

过去 24 小时内，IronClaw 项目保持高活跃度：共更新 Issues 44 条（新开/活跃 34 条，关闭 10 条），PR 50 条（待合并 33 条，已合并/关闭 17 条）。v1.1.0-rc.1 于 8 月 3 日发布，为 1.0.0 以来的首个候选版本，核心聚焦于 MCP 扩展能力、IronHub 集成和文件附件跨通道传递。今日 Bug Bash 阶段集中暴露了多个 MCP 认证与渠道交付问题，CI 稳定性持续改进，整体项目处于功能扩展与质量加固并行的关键阶段。

---

## 2. 版本发布

### ironclaw-v1.1.0-rc.1（2026-08-03）
**[链接](https://github.com/nearai/ironclaw/releases/tag/ironclaw-v1.1.0-rc.1)**

#### 主要更新内容
- **任意 MCP 服务器注册**：支持注册托管的 MCP 服务器，扩展 Agent 工具集
- **IronHub 深度链接安装**：可通过 IronHub deep link 安装扩展
- **跨通道持久文件附件**：附件可在不同渠道间传递
- **Slack `/ironclaw` 斜杠命令**：新增 Slack 原生交互入口
- **错误信息可读性提升**：全面改进失败场景的错误提示

#### 迁移注意事项
- 此为 Release Candidate，尚未稳定，生产环境建议继续使用 v1.0.x
- MCP 扩展机制变更可能影响现有自定义集成

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 内容 | 状态 |
|---|---|---|
| [#7244](https://github.com/nearai/ironclaw/pull/7244) | 修复 main 分支 CI 失败 | ✅ 已关闭 |
| [#7261](https://github.com/nearai/ironclaw/pull/7261) | 修复 release canary 临时路径问题 | ✅ 已关闭 |
| [#7196](https://github.com/nearai/ironclaw/pull/7196) | bump wasm 依赖组（wasmtime-wasi, wit-component, wit-parser） | ✅ 已关闭 |
| [#7234](https://github.com/nearai/ironclaw/pull/7234) | 误开的 issue 关闭 | ✅ 已关闭 |
| [#7028](https://github.com/nearai/ironclaw/pull/7028) | 恢复期间保留终端状态（outbound delivery） | 🔄 待合并 |
| [#7029](https://github.com/nearai/ironclaw/pull/7029) | 恢复持久交付声明（依赖 #7028） | 🔄 待合并 |
| [#7214](https://github.com/nearai/ironclaw/pull/7214) | 添加 Docker 和 Railway 用户沙箱 profile | 🔄 待合并 |
| [#7263](https://github.com/nearai/ironclaw/pull/7263) | 程序闭包：WS12 100% 门控 | 🔄 待合并 |

**推进总结**：今日合并以 CI 修复和依赖更新为主，核心功能 PR（outbound delivery 恢复、沙箱 profile、WS12 程序闭包）仍在开放 review 中，项目整体稳步向前。

---

## 4. 社区热点

### 高讨论度 Issues

1. **#3036 — Configuration-as-Code Epic**（7 评论）
   [链接](https://github.com/nearai/ironclaw/issues/3036)
   > 运维人员希望声明式配置 IronClaw，但当前需手动编辑 `.env`、workspace docs、settings JSON 等多处，缺乏 schema、diff 和审计追踪。此为 Reborn 架构的核心配置问题。

2. **#7194 — 共享频道作为出站投递目标**（3 评论）
   [链接](https://github.com/nearai/ironclaw/issues/7194)
   > Agent 可枚举 Slack 频道并发送消息，但无法将其设为 outbound delivery target，导致 host delivery layer 无法路由最终回复。

3. **#7265 — ChannelAdapter 类型级证明**
   [链接](https://github.com/nearai/ironclaw/issues/7265)
   > 针对 PR #7029 的后续设计讨论，要求 ChannelAdapter 在类型层面证明"供应商未收到此消息"，确保重试安全。

4. **#7038 — Storybook + AI-first Design System Epic**
   [链接](https://github.com/nearai/ironclaw/issues/7038)
   > 完整提案已通过 PR #7257，涉及 WebUI 主题、资产、交互和信息架构的系统化重构。

---

## 5. Bug 与稳定性

### 今日报告的问题（按严重程度排序）

| Issue | 严重程度 | 描述 | Fix PR |
|---|---|---|---|
| [#7249](https://github.com/nearai/ironclaw/issues/7249) | P2 | Slack DM 执行结果错误投递到 Telegram | — |
| [#7247](https://github.com/nearai/ironclaw/issues/7247) | P1 | Agent 虚假声称 GitHub 已连接 | — |
| [#7246](https://github.com/nearai/ironclaw/issues/7246) | P1 | Agent 幻觉自动化状态（声称运行中，实际无） | — |
| [#7251](https://github.com/nearai/ironclaw/issues/7251) | P2 | Agent 猜测 MCP 认证类型而非主动发现 | — |
| [#7250](https://github.com/nearai/ironclaw/issues/7250) | P2 | DeepWiki MCP 网络错误时给出误导性认证指引 | — |
| [#7248](https://github.com/nearai/ironclaw/issues/7248) | P2 | 无效自定义 MCP 端点被接受导致 run 失败 | — |
| [#7254](https://github.com/nearai/ironclaw/issues/7254) | P2 | 无法访问 Slack 反馈线程中的附件文件 | — |
| [#6257](https://github.com/nearai/ironclaw/issues/6257) | P2 | 发送/生成 PDF 时报 `attachments.mime_type` 错误 | — |
| [#7209](https://github.com/nearai/ironclaw/issues/7209) | — | CI regression gate 无法识别 `node:assert` 风格 | — |

> **趋势分析**：今日 Bug Bash 集中暴露了 **MCP 认证链路**和**渠道投递正确性**两大类问题，均位于 Reborn 架构的关键路径，建议优先关注。

---

## 6. 功能请求与路线图信号

| Issue / PR | 诉求 | 版本信号 |
|---|---|---|
| [#6731](https://github.com/nearai/ironclaw/issues/6731) | IronHub 深度集成（运行时安装工具/技能） | v1.1.0（已在 RC 中体现） |
| [#6941](https://github.com/nearai/ironclaw/issues/6941) | 模型可自创建、发现、选择 skills | v1.1.0（epic） |
| [#7203](https://github.com/nearai/ironclaw/issues/7203) | 将虚拟文件系统暴露为真实 mount | 跟进 #7171 |
| [#7157](https://github.com/nearai/ironclaw/pull/7157) | 显式渠道交付工具（双车道模型） | 待合并 |
| [#6938](https://github.com/nearai/ironclaw/pull/6938) | 模型选择 skill 而非关键词评分器 | 已 stacked on #6745 |
| [#7218](https://github.com/nearai/ironclaw/issues/7218) | Web Debug Inspector（调试视图） | 新功能 |
| [#7230](https://github.com/nearai/ironclaw/pull/7230) | 有界诊断会话存储（支持 Inspector） | 待合并 |

> **判断**：v1.1.0 将重点围绕 **MCP/IronHub 扩展生态**和**渠道交付重构**，skill 系统的模型驱动选择也是核心方向。

---

## 7. 用户反馈摘要

### 痛点提炼
1. **MCP 认证体验差**：多个 issue（#7251, #7250, #7248）反映 Agent 面对 MCP 端点时无法主动发现认证方式，只能猜测或接受无效配置。
2. **渠道投递异常**：#7249 显示 Slack DM 结果出现在 Telegram，#7254 显示无法读取 Slack 附件，渠道间隔离存在缺陷。
3. **状态幻觉**：#7246 和 #7247 显示 Agent 在未验证实际状态时自信陈述（GitHub 已连接、自动化运行中），影响可信度。
4. **配置管理复杂**：#3036 长期诉求，多类 Operator 被迫手编分散配置文件，缺乏 schema 和审计。

### 正面反馈
- WebUI 焦点修复（#7204 已关闭）改善了交互体验
- CI 稳定性持续改进（#7244、#7261 已修复）

---

## 8. 待处理积压

### 需维护者关注

| Issue / PR | 类型 | 风险 | 说明 |
|---|---|---|---|
| [#7231](https://github.com/nearai/ironclaw/issues/7231) | Bug | 中 | `APPROVE` 评论文本不触发实际 GitHub 审批，PR 持续阻塞 |
| [#7245](https://github.com/nearai/ironclaw/issues/7245) | 技术债 | 低 | `reborn_services.rs` 超 6400 行，需拆分重构 |
| [#7209](https://github.com/nearai/ironclaw/issues/7209) | CI Bug | 中 | regression gate 无法识别主流前端测试断言风格，阻塞正确 PR |
| [#6257](https://github.com/nearai/ironclaw/issues/6257) | Bug | 中 | PDF 附件 mime_type 校验问题，影响文件传输功能 |
| [#7203](https://github.com/nearai/ironclaw/issues/7203) | 功能 | 中 | skill 虚拟文件系统挂载需求，阻塞技能执行能力 |

---

**报告生成时间**：2026-08-06  
**数据来源**：GitHub API（nearai/ironclaw）

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报 — 2026-08-06

---

## 1. 今日速览

LobsterAI 今日发布 v2026.8.5，聚焦于日常签到体验与企服账号隔离两大功能方向。过去24小时内共合并/关闭 **10 条 PR**，涵盖启动海报更新、窗口生命周期加固、Gateway 锁竞争修复、对话搜索功能等，修复活跃度较高。开放 Issues 3 条，均为 Bug 报告，暂无新功能请求。整体项目健康度良好，维护节奏稳定，但依赖 `dependabot` 的长期未响应 PR 数量偏多，需关注。

---

## 2. 版本发布

### LobsterAI v2026.8.5（2026-08-05）

| 变更项 | 说明 |
|--------|------|
| **feat(activity)** | 新增原生每日签到体验（PR #2408） |
| **feat(enterprise)** | 隔离账号级认证与服务流程（PR #2409） |
| **style** | 样式优化 |

**破坏性变更：** 无。
**迁移注意事项：** 企业用户需确认新账号隔离逻辑与现有 SSO/授权配置的兼容性，建议先在测试环境验证。

---

## 3. 项目进展

今日合并/关闭的 PR 共 10 条，主要推进以下方向：

### 稳定性修复（2 条）
- **#2437** — 加固窗口生命周期与退出逻辑：为 OpenAI-compat 代理和 HTML 预览服务器增加 drain 定时器与硬截止时间，防止 keep-alive 连接阻塞应用退出；主窗口激活改为首次渲染后触发，修复焦点/第二实例时的队列展示问题。
- **#2436** — 修复 OpenClaw Gateway 自重启竞态导致的锁文件毒化：解决 Windows `TerminateProcess` 与 Gateway 自检过程中单实例锁文件写入中断问题，避免网关重启失败长达 30 秒。

### 启动体验优化（2 条）
- **#2439 / #2438** — 更新启动致谢海报为最新审核通过素材，补充右上角关闭图标及透明按钮热区。

### 功能增强（1 条）
- **#2435** — 在协作面板切换按钮旁新增对话搜索入口，复用侧边栏搜索工作流，支持响应式样式与查询感知导航。

### 依赖更新（3 条）
- **#1279 / #1280 / #1281** — Dependabot 批量升级 `cross-env 7→10.1.0`、`react-dom 18.3.1→19.2.4`、`vite 5.4.21→8.0.9`，**均已关闭但未明确合并状态**。

> 项目整体向前推进约 **3 个核心方向**（稳定性、启动体验、搜索能力），同时持续跟进依赖栈升级。

---

## 4. 社区热点

### 🔥 讨论活跃 Issue

| Issue | 标题 | 创建者 | 评论 | 关注点 |
|-------|------|--------|------|--------|
| [#1200](https://github.com/netease-youdao/LobsterAI/issues/1200) | NIM 超大群 teamTypeNum 硬编码错误 | MaoQianTu | 1 | 云信 SDK 枚举映射错误，影响 @mention 群名显示 |
| [#2441](https://github.com/netease-youdao/LobsterAI/issues/2441) | 技能开关按目录名写入但与 frontmatter 不匹配 | fujingzhai | 0 | 用户无法持久精简系统提示词，设计层面缺口 |
| [#2440](https://github.com/netease-youdao/LobsterAI/issues/2440) | 桌面端系统提示词重复注入（4,425 字符） | fujingzhai | 0 | AGENTS.md 托管区与注入块 78% 重复，浪费 Token |

**分析：**
- **Issue #1200** 关联 PR #1201 已提交一行修复，但 Issue 仍为 OPEN 且标记 `stale`，修复尚未随版本发布。
- **Issues #2441 / #2440** 来自同一用户，聚焦于系统提示词的可控性，反映高级用户对 AGENTS.md 托管机制的深层诉求，具有路线图参考价值。

---

## 5. Bug 与稳定性

| 级别 | Issue | 描述 | Fix PR |
|------|-------|------|--------|
| 🟡 中 | [#1200](https://github.com/netease-youdao/LobsterAI/issues/1200) | NIM 超大群 @mention 时群名显示为原始 ID | #1201（未合入版本） |
| 🔴 高 | [#2440](https://github.com/netease-youdao/LobsterAI/issues/2440) | 系统提示词重复注入，单会话浪费 ~3,500 字符 | 无 |
| 🔴 高 | [#2441](https://github.com/netease-youdao/LobsterAI/issues/2441) | 技能开关静默失效，用户无法精简系统提示词 | 无（设计缺口） |

> **注：** PR #2436 修复了 Gateway 锁竞态问题（此前可能导致重启失败长达 30 秒），属于稳定性关键修复，已合并。

---

## 6. 功能请求与路线图信号

| 诉求 | 来源 | 信号强度 |
|------|------|----------|
| 对话搜索能力 | PR #2435（已合并） | ✅ 已落地 |
| 企服账号/授权隔离 | PR #2409（已合并 v2026.8.5） | ✅ 已落地 |
| 系统提示词可控性（持久精简入口） | Issue #2441 | ⚠️ 用户明确诉求，尚无实现路径 |
| 启动海报/品牌物料自动化 | PR #2438/#2439（已合并） | ✅ 已落地 |
| 依赖栈全面升级至 React 19 / Vite 8 | PR #1280/#1281（open/stale） | ⚠️ 依赖更新已提交但未闭环 |

**判断：** Issue #2441 的"持久精简系统提示词"诉求与 AGENTS.md 托管机制的设计逻辑相关，建议维护者评估是否纳入下一版本议程。

---

## 7. 用户反馈摘要

- **满意点：** 启动海报更新频率正常，品牌物料能及时替换（#2438/#2439）；对话搜索功能受协作场景用户欢迎（#2435）。
- **痛点 1：** 系统提示词重复注入（#2440）直接导致 Token 浪费，对长会话成本敏感的用户影响显著。
- **痛点 2：** 技能开关与 OpenClaw frontmatter 命名不一致导致"静默失效"（#2441），用户难以察觉且无法持久配置，体验断层明显。
- **痛点 3：** NIM 超大群 @mention 时群名 fallback（#1200），影响多人群协作场景下的识别效率。
- **反馈趋势：** 用户从"功能可用"向"体验可控"演进，对系统提示词、授权隔离、对话检索等深层配置的诉求增强。

---

## 8. 待处理积压

| 类型 | 编号 | 标题 | 创建时间 | 状态 | 建议 |
|------|------|------|----------|------|------|
| 🐛 Bug | [#1200](https://github.com/netease-youdao/LobsterAI/issues/1200) | NIM teamTypeNum 硬编码错误 | 2026-04-01 | stale / Fix PR #1201 未发布 | 尽快合入并发布 patch |
| 🐛 Bug | [#2440](https://github.com/netease-youdao/LobsterAI/issues/2440) | 系统提示词重复注入 | 2026-08-05 | OPEN | 排入当前迭代修复 |
| 🐛 Bug | [#2441](https://github.com/netease-youdao/LobsterAI/issues/2441) | 技能开关与 frontmatter 不匹配 | 2026-08-05 | OPEN | 需设计层面决策 |
| 📦 依赖 | [#1279](https://github.com/netease-youdao/LobsterAI/pull/1279) | cross-env 7→10.1.0 | 2026-04-02 | stale | 确认兼容性后关闭或合并 |
| 📦 依赖 | [#1280](https://github.com/netease-youdao/LobsterAI/pull/1280) | react-dom 18→19.2.4 | 2026-04-02 | stale | React 19 升级需回归测试 |
| 📦 依赖 | [#1281](https://github.com/netease-youdao/LobsterAI/pull/1281) | vite 5→8.0.9 | 2026-04-02 | stale | 同内需配套验证 |

> **积压预警：** Dependabot 的 3 条依赖升级 PR 自 2026-04-02 起已 stale 超 4 个月，建议维护者统一评估后批量处理，避免长期悬置。

---

*报告生成时间：2026-08-06 | 数据来源：LobsterAI GitHub 过去 24 小时活动*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

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



# ZeroClaw 项目动态日报 — 2026-08-06

---

## 1. 今日速览

今日项目整体处于**高活跃度治理阶段**，50 条 Issue 与 50 条 PR 双向并进，其中仅 1 条 PR 被合并/关闭，大量 PR（49 条）处于待合并状态，表明审查节奏偏紧。今日核心议题集中在**安全加固**（SSRF 闸门、WebAuthn 断言校验、SOP 加载缺陷）、**架构 RFC 讨论**（Chat Completions profile、Agent Goal Mode、运行时会话所有权）以及**工具调用解析兼容**（DeepSeek DSML 格式、`<tools>` 标签恢复）。无新版本发布，但多个 RFC 持续推进，项目整体向前推进明显。

---

## 2. 版本发布

今日无新版本发布（Releases: 0）。

---

## 3. 项目进展

今日合并/关闭的重要 PR：

- **PR #9750** `[CLOSED]` — macOS LaunchAgent 守护进程日志无界重定向修复，改为 8 MiB 有界守护进程日志捕获（Audacity88）。该修复消除了长期存在的日志膨胀隐患。
  链接: <https://github.com/zeroclaw-labs/zeroclaw/pull/9750>

- **PR #9652** `[CLOSED]` — 修复 `config set` 拒绝含连字符 cron key 的 bug，与 `config list`/`get` 行为不一致（ZiBibro）。
  链接: <https://github.com/zeroclaw-labs/zeroclaw/pull/9652>

- **PR #9335** `[CLOSED]` — 新增对 data-wrapped OpenAI-compatible chat 响应格式的支持（brokensnow2）。
  链接: <https://github.com/zeroclaw-labs/zeroclaw/pull/9335>

- **PR #7467** `[CLOSED]` — 为 ZeroCode 字符串设置编辑添加方向键导航支持（damajor）。
  链接: <https://github.com/zeroclaw-labs/zeroclaw/pull/7467>

- **PR #9462** `[CLOSED]` — 修复 `zeroclaw-plugins` lib 单元测试在 `plugins-wasmtime` feature 下不被 CI 执行的 bug（IftekharUddin）。
  链接: <https://github.com/zeroclaw-labs/zeroclaw/pull/9462>

当前积压的 49 条待合并 PR 中，以下高优先级 PR 已接近就绪：

| PR | 内容 | 状态 |
|---|---|---|
| #9781 | WebAuthn 断言数据校验（安全加固） | 待合并 |
| #9776 | `forbidden_paths` 支持 workspace-relative glob 模式 | 待合并 |
| #9737 | 在 pipeline 中强制执行 agent 工具策略 | 待合并 |
| #9723 | DeepSeek DSML / `<|tool_call|>` 工具调用格式解析 | 待合并 |
| #9695 | 剥离流式/非流式响应中的终端标记（`<eom>` 等） | 待合并 |
| #8713 | `file_download` 工具 SSRF 闸门 + 私有主机白名单 | 待合并 |

---

## 4. 社区热点

### 🔥 高评论 RFC 议题

| 议题 | 评论数 | 核心诉求 |
|---|---|---|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) — Work Lanes & Board Automation | 18 | 工作流路由自动化，降低维护者负担 |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) — Goal Mode v1 | 18 | 跨 agent 回合的有界目标持久化执行 |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — Chat Completions Profile | 16 | 适配 OpenAI Chat Completions 协议，打通 Open WebUI / Continue.dev / Aider 等客户端 |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Shell 高风险命令确认层级 | 16 | 引入 Claude Code 风格的 allow/ask/deny 命令策略 |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) — 可插拔认证与规范主体 | 12 | 统一 OIDC / 可插拔认证提供者框架 |

**热点分析：** 社区当前最迫切的需求是**协议兼容**（#8603 Chat Completions）和**安全策略细化**（#7155 shell 命令策略、#8303 goal mode），这两个 RFC 讨论热度最高，反映了用户希望 ZeroClaw 与主流 AI 工具生态无缝对接，同时在高风险操作中拥有更强的可控性。

### 📌 待维护者决策
- [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — 维护者决策队列 tracker，汇总所有待处理 RFC 和设计议题（11 评论）。
- [#9346](https://github.com/zeroclaw-labs/zeroclaw/issues/9346) — 统一包/能力/配置/运行时目录契约（3 评论）。

---

## 5. Bug 与稳定性

| Issue | 严重度 | 摘要 | Fix PR |
|---|---|---|---|
| [#9768](https://github.com/zeroclaw-labs/zeroclaw/issues/9768) | **S2** — 降级行为 | SIGUSR1 未触发 daemon reload，且降级安全警告指示的信号会直接杀死守护进程（@AngryPacifist） | ❌ 无 |
| [#9780](https://github.com/zeroclaw-labs/zeroclaw/issues/9780) | **S2** — 工作流阻塞 | cron 触发的 SOP 无法执行网络操作（无 HTTP 能力，shell.exec/notify.channel 为占位符）（@Pratiikpy） | ❌ 无 |
| [#9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) | **S2** — 静默故障 | `sops_dir` 文档默认值未被守护进程遵循，SOP 引擎静默不加载，无任何错误/警告 | ❌ 无 |
| [#9775](https://github.com/zeroclaw-labs/zeroclaw/issues/9775) | **S1** — 工作流阻塞 | OpenRouter streaming 请求丢弃 `provider_extra`，导致配置的缓存参数不生效（@Audacity88） | ❌ 无 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | P2 | 运行时拥有的对话会话与传输适配器（RFC，含安全层面架构变更） | ❌ 无 |
| [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) | P2 | `verifiable-intent` 在未验证凭证链的情况下评估约束条件（@AngryPacifist） | ❌ 无 |
| [#8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642) | P1 | MCP 工具 schema 克隆导致 agent 循环中 RSS 无界增长（内存泄漏） | ❌ 无 |
| [#9697](https://github.com/zeroclaw-labs/zeroclaw/issues/9697) | S3 | ZeroCode 无法连接由 Windows Task Scheduler 启动的 daemon | ❌ 无 |
| [#6350](https://github.com/zeroclaw-labs/zeroclaw/issues/6350) | **S2** | WhatsApp Web `allowed-numbers` 对 LID-based 联系人被绕过，消息静默丢失 | ❌ 无（已 close） |

> **稳定性评估：** 今日报告了 **4 个 S1/S2 级 Bug**，其中 3 个涉及安全/配置静默失败（#9768、#9779、#9775），建议在下一版本发布前优先处理。`#8642` 的内存泄漏问题持续未解决，属于长期风险。

---

## 6. 功能请求与路线图信号

| RFC / 功能 | 链接 | 状态 | 纳入下版可能性 |
|---|---|---|---|
| Chat Completions Profile（#8603） | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | RFC Rev. 进行中 | ⭐⭐⭐ 高 — 已有多个客户端对接需求 |
| Goal Mode v1（#8303） | [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | RFC 讨论中 | ⭐⭐⭐ 高 — 核心 agent 能力 |
| 运行时会话所有权（#9487） | [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | Rev. 2 已修订 | ⭐⭐ 中 — 与 #9488/#9600 耦合 |
| Todo tracker 配置迁移（#9246） | [#9246](https://github.com/zeroclaw-labs/zeroclaw/issues/9246) | in-progress | ⭐⭐ 中 |
| Provenance & 内部 agent 回合回复契约（#6954） | [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) | Rev. 2 修订完成 | ⭐⭐ 中 |
| OpenRouter prompt cache session_id（#9631） | [#9631](https://github.com/zeroclaw-labs/zeroclaw/issues/9631) | Feature request | ⭐ 低 — 成本优化，非核心 |
| 桌面 Computer Use 支持（#6909） | [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | RFC 等待作者操作 | ⭐⭐ 中 — 长期能力 |
| Plugin 自有 Kanban Board（#8832） | [#8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832) | RFC 讨论中 | ⭐ 低 — 插件生态 |
| Anthropic OAuth alias 契约（#9464） | [#9464](https://github.com/zeroclaw-labs/zeroclaw/issues/9464) | in-progress | ⭐⭐ 中 — 已有关联 PR #9420 |

**路线图判断：** v0.9.0 的核心方向已清晰——**认证安全**（#7141）、**协议兼容**（#8603）、**Agent 会话治理**（#9487）三大支柱。PR #9324（A2A outbound client）也已进入实现阶段，跨 agent 协作能力正在成型。

---

## 7. 用户反馈摘要

- **"OpenRouter 对话费用过高"** — #9631 指出单次对话产生数十次 LLM 请求，system prompt 和 tool schemas 每次都被重放，用户强烈呼吁支持 `session_id` 以实现 prompt 缓存。
- **SOP 静默失效** — #9779 和 #9780 反映 cron 触发 SOP 既无法联网也无加载日志，用户称"文档承诺的功能实际上不存在"，这是严重的可用性质疑。
- **WhatsApp 消息静默丢失** — #6350 用户反馈 LID-based 联系人绕过 `allowed-numbers` 限制，消息被静默丢弃且无任何错误提示，安全感知差。
- **终端标记泄露** — #9695 用户报告 DeepSeek 等模型的 `<eom>` / `<|eom|>` 标记泄露到响应文本中，影响用户体验；#9723 补充 DeepSeek DSML 格式未解析问题。
- **Config CLI 不一致** — #9652 用户发现 `config set` 拒绝连字符 key 而 `list/get` 正常工作，属于微妙的可用性摩擦。
- **零代码体验** — #9697 用户反馈 ZeroCode TUI 无法连接由 Task Scheduler 启动的 daemon，Windows 场景下运维体验待改善。

---

## 8. 待处理积压

| Issue / PR | 标签 | 最后更新 | 风险 | 建议 |
|---|---|---|---|---|
| [#8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642) — MCP schema 克隆内存泄漏 | P1, accepted | 2026-08-05 | 🔴 高 | 优先分配，涉及生产环境稳定性 |
| [#9768](https://github.com/zeroclaw-labs/zeroclaw/issues/9768) — SIGUSR1 reload 失效 | P1, accepted | 2026-08-05 | 🔴 高 | 安全警告与实际操作矛盾，需紧急修复 |
| [#9775](https://github.com/zeroclaw-labs/zeroclaw/issues/9775) — OpenRouter streaming 丢 provider_extra | P1 | 2026-08-05 | 🔴 高 | 影响付费用户工作流，建议纳入 hotfix |
| [#9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) — sops_dir 默认值失效 | SOP | 2026-08-06 | 🟠 中高 | 静默故障，用户无感知，需修复 |
| [#9780](https://github.com/zeroclaw-labs/zeroclaw/issues/9780) — cron SOP 无法联网 | SOP | 2026-08-06 | 🟠 中高 | 文档承诺与实现脱节 |
| [#6350](https://github.com/zeroclaw-labs/zeroclaw/issues/6350) — WhatsApp LID bypass | P1, accepted | 2026-08-05 | 🟡 中 | 已关闭但修复未确认 |
| [#9464](https://github.com/zeroclaw-labs/zeroclaw/issues/9464) — Anthropic OAuth alias | P1, in-progress | 2026-08-06 | 🟡 中 | 需维护者确认契约 |
| #9324 — A2A outbound client | enhancement, XL | 2026-08-06 | — | 待审查合并，核心功能 PR |

---

**总体健康度评估：** 🟡 **中等偏上** — 项目治理活跃（大量 RFC 讨论）、安全加固持续推进，但存在若干 S1/S2 级未修复 Bug 和静默故障，建议维护者优先处理 #9768、#9775、#9779 三个影响用户体验与安全的 issue。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*