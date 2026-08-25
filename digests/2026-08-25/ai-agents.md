# OpenClaw 生态日报 2026-08-25

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-25 01:39 UTC

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
**日期：2026-08-25** | 数据来源：[github.com/openclaw/openclaw](https://github.com/openclaw/openclaw)

---

## 1. 今日速览

OpenClaw 今日保持高活跃度，过去24小时内共产生 **500 条 Issue** 更新（474 活跃/新开，26 关闭）及 **500 条 PR** 更新（428 待合并，72 已合并/关闭），发布 **v2026.8.1-beta.3** 新版本，核心亮点为 GPT-5.6 多模型推理支持、Control UI 首次设置流程优化及 Puppeteer CDP 中继支持。项目整体处于快速迭代阶段，社区反馈集中於消息投递可靠性、子代理生命周期管理及渠道兼容性等核心稳定性问题，部分 P1 级 Bug 已有 PR 跟进。

---

## 2. 版本发布

### v2026.8.1-beta.3

**更新亮点：**
- **GPT-5.6 推理支持**：在 OpenClaw 及 Codex runtime 中新增对 GPT-5.6 Sol、Terra、Luna 及 Ultra 模型的推理能力支持
- **Control UI 首次设置优化**：验证模型设置完成后自动衔接 Custodian 配置及可选渠道设置流程
- **Puppeteer CDP 中继支持**：新增与配对 Chrome 会话兼容的 CDP relay 功能

**迁移注意事项：**
- 此版本为 beta，建议在生产环境谨慎升级
- GPT-5.6 模型需在 `openclaw.json` 中显式配置方可使用
- CDP 中继功能需确保 Chrome 版本与 OpenClaw 版本兼容

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR（共 72 条）

| PR | 标题 | 贡献者 | 影响 |
|---|---|---|---|
| [#128371](https://github.com/openclaw/openclaw/pull/128371) | fix(release): authorize focused beta evidence | vincentkoc | 解决 beta.3 发布阻塞问题，允许聚焦测试证据通过验证 |
| [#123975](https://github.com/openclaw/openclaw/pull/123975) | fix(scripts): clean up tsgo process trees | jesse-merhi | 修复 tsgo 编译器进程泄漏，增加超时守护机制 |
| [#125471](https://github.com/openclaw/openclaw/pull/125471) | fix(models): keep Claude CLI OAuth available | VACInc | 修复 Gateway 重启后 Claude CLI OAuth refresh token 丢失问题 |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | feat(ui): review install policy warnings | jesse-merhi | Control UI 新增安装策略警告审查功能 |
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | feat(security): require acknowledgement for install policy warnings | jesse-merhi | 安全增强：外部插件安装需显式确认策略警告 |
| [#126424](https://github.com/openclaw/openclaw/pull/126424) | fix(gateway): keep conversation delivery within agent bindings | joshavant | 修复多代理场景中会话投递越界问题 |

**项目推进评估：** 今日合并的 PR 主要聚焦於发布流程修复、安全策略强化及 OAuth 生命周期管理，为 beta.3 的正式发布扫清了关键障碍，同时为多代理架构的稳定性奠定了基础。

---

## 4. 社区热点

### 讨论最活跃的 Issues（按评论数排序）

| Issue | 标题 | 评论数 | 主题 |
|---|---|---|---|
| [#125626](https://github.com/openclaw/openclaw/issues/125626) | Release validation: v2026.8.1-beta.2 | 18 | 版本发布验证流程 |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | Subagent completion delivery can be lost | 12 | 子代理消息投递丢失（P1） |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | OpenClaw leaks unreaped hook/tool child processes | 9 | 进程泄漏导致僵尸进程累积（P1） |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | Agent-triggered context compaction | 8 | 代理自主触发上下文压缩功能请求 |
| [#97680](https://github.com/openclaw/openclaw/issues/97680) | Beta-tagged update leaves plugins on latest | 8 | Beta 升级后官方插件版本不一致（P1） |

**热点分析：**
- **子代理可靠性**（#67777、#97616）是当前社区最关注的稳定性问题，涉及消息丢失、进程泄漏等生产环境高频痛点
- **上下文压缩自主触发**（#6757）反映高级用户对代理自主性的需求
- **Beta 版本管理**（#97680）问题表明多版本并行场景下的包管理仍需完善

---

## 5. Bug 与稳定性

### 今日报告的高优先级 Bug

| Issue | 严重程度 | 标题 | Fix PR |
|---|---|---|---|
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | P1 🔴 | 子进程泄漏导致僵尸进程累积 | 暂无 |
| [#126360](https://github.com/openclaw/openclaw/issues/126360) | P1 🔴 | AgentSelectionRequiredError 日志洪水 | 暂无 |
| [#125570](https://github.com/openclaw/openclaw/issues/125570) | P1 🔴 | Skill Workshop apply 覆盖真实 skill 描述 | 暂无 |
| [#126906](https://github.com/openclaw/openclaw/issues/126906) | P1 🔴 | 拒绝 write 工具静默禁用记忆持久化 | 暂无 |
| [#126458](https://github.com/openclaw/openclaw/issues/126458) | P1 🔴 | 自定义 openai-completions 忽略 maxTokens | 暂无 |
| [#126631](https://github.com/openclaw/openclaw/issues/126631) | P1 🔴 | Sandbox skills bind-mount 创建 root -owned 目录 | 暂无 |
| [#127287](https://github.com/openclaw/openclaw/issues/127287) | P1 🔴 | GitHub Copilot GHE 数据驻留兼容性问题 | 暂无 |
| [#126521](https://github.com/openclaw/openclaw/issues/126521) | P1 🔴 | zsh 交互式展开导致命令链断裂 | 暂无 |
| [#77467](https://github.com/openclaw/openclaw/issues/77467) | P1 🔴 | MiniMax OAuth token 无法自动刷新 | 暂无 |
| [#128067](https://github.com/openclaw/openclaw/issues/128067) | P1 🔴 | beta.7 可靠性缺陷报告（6类） | 暂无 |

**稳定性评估：** 今日报告 **10 个 P1 级 Bug**，主要集中在消息投递、代理生命周期管理、渠道兼容性三个领域。部分问题（如 #97616 进程泄漏）为长期存在的架构性缺陷，建议维护者优先处理。

---

## 6. 功能请求与路线图信号

### 高关注功能请求

| Issue | 标题 | 👍数 | 路线图信号 |
|---|---|---|---|
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | Agent-triggered context compaction | 2 | 代理自主性增强，可能纳入后续版本 |
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | Self-hosted STT/TTS provider support in webchat | 2 | 私有化部署需求明确，与 GPT-5.6 支持形成呼应 |
| [#45771](https://github.com/openclaw/openclaw/issues/45771) | Built-in pace-aware rate limiting | 2 | 自主代理场景下的 API 成本控制需求 |
| [#53548](https://github.com/openclaw/openclaw/issues/53548) | Decouple mode="session" from thread binding | 3 | 渠道灵活性改进，已有讨论 |
| [#9986](https://github.com/openclaw/openclaw/issues/9986) | Trigger model fallback on context length exceeded | 0 | 容错机制增强 |

**路线图判断：** 社区对**代理自主性**（上下文压缩、速率限制）和**渠道灵活性**（STT/TTS 自托管、session 解耦）的需求强烈，这些功能与今日发布的 GPT-5.6 推理支持、CDP 中继功能形成协同，可能成为下一版本的重点方向。

---

## 7. 用户反馈摘要

### 真实用户痛点

1. **消息投递可靠性**（#67777、#126246、#125838）
   - 子代理完成消息在超时/重启场景下丢失
   - Telegram 持久化投递卡在 `send_attempt_started` 状态
   - QQBot slash command 轻量回复未投递

2. **资源泄漏**（#97616、#86119）
   - Hook/tool 子进程未被 reap，累积为僵尸进程
   - 子代理/cron 执行后 node server.js worker 进程残留

3. **配置与版本管理**（#97680、#82020、#90786）
   - Beta 升级后官方插件版本不一致
   - 自定义 provider 与内置 provider 共享 baseUrl 时配置冲突
   - memory status 命令报错 "Unknown memory embedding provider: google"

4. **UX 摩擦**（#39406、#50677、#7406）
   - 工具瞬态错误仍向用户通道发送警告消息
   - Skills 被静默截断，用户无感知
   - Telegram 会话下拉显示原始 key 而非人类可读名称

### 用户满意度信号
- Control UI 改进获得正面反馈（#128954 色盲友好配色）
- 安全策略确认机制（#116489）受到管理员欢迎
- iOS 应用更新导致功能中断（#108520）引发用户不满

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 严重程度 | 状态 | 建议优先级 |
|---|---|---|---|---|
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | 2026-04-16 | P1 🔴 | 活跃讨论中 | 高 - 子代理可靠性核心问题 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 2026-06-29 | P1 🔴 | 待 maintainer review | 高 - 进程泄漏影响生产稳定性 |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | 2026-02-02 | P2 🟡 | 待产品决策 | 中 - 代理自主性关键功能 |
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | 2026-03-13 | P2 🟡 | 待 maintainer review | 中 - 私有化部署需求 |
| [#108520](https://github.com/openclaw/openclaw/issues/108520) | 2026-07-16 | P0 🚨 | 待 info | 高 - iOS 应用功能中断 |

### 建议维护者关注
1. **#67777** 已讨论 4 个月，涉及子代理消息投递的核心可靠性，建议优先处理
2. **#108520** 标记为 P0 但仍在等待用户信息，需主动跟进
3. **#97616** 进程泄漏问题影响生产环境，建议纳入下一 beta 修复范围

---

**报告生成时间：** 2026-08-25 | **分析模型：** Agnes-2.0-Flash (Sapiens AI)

---

## 横向生态对比



# 2026-08-25 个人 AI 助手/智能体开源生态横向对比分析

---

## 1. 生态全景

个人 AI 助手开源生态呈现**多线并进、分层竞争**格局：OpenClaw、CoPaw、ZeroClaw 处于高活跃迭代期，月级 Issues/PR 吞吐量支撑快速功能拓展；NanoBot、Hermes Agent、IronClaw 以中高密度维护质量基建与稳定性；NanoClaw、Moltis 聚焦渠道扩展与安全加固；PicoClaw、NullClaw、ZeptoClaw、LobsterAI 则处于细分场景或生态补位阶段。整体趋势从"单点能力突破"转向"生产级可靠性+多渠道覆盖+安全治理"的综合竞争。

---

## 2. 各项目活跃度对比

| 项目 | Issues (新/活跃/关闭) | PRs (待合并/已合) | Release | 健康度 |
|------|----------------------|-------------------|---------|--------|
| **OpenClaw** | 474 / 26 | 428 / 72 | v2026.8.1-beta.3 | 🟢 高活跃，快速迭代 |
| **CoPaw** | 32 / 18 | 22 / 26 | v2.1.1-beta.2 | 🟢 高活跃，稳定性攻坚 |
| **ZeroClaw** | 43 / 7 | 45 / 5 | 无 | 🟢 高活跃，协议+安全并重 |
| **Hermes Agent** | 47 / ~3 | 42 / 8 | 无 | 🟡 中高产，债务清理期 |
| **IronClaw** | 12 / 9 | 18 / 17 | 无 | 🟢 健康，架构收敛 |
| **NanoBot** | 8 / 0 | 14 / 12 | 无 | 🟢 健康，底层能力建设 |
| **NanoClaw** | 1 / 1 | 18 / 3 | v2.3.0 | 🟡 中活跃，渠道扩展期 |
| **LobsterAI** | 0 / 3 | 1 / 10 | 无 | 🟡 中等，清理积压 |
| **Moltis** | 0 / 2 | 0 / 7 | 20260824.01 | 🟢 高活跃，安全修复集中 |
| **PicoClaw** | 3 / 0 | 1 / 2 | 无 | 🟡 中等偏下，渠道 Bug 待解 |
| **NullClaw** | 2 / 0 | 1 / 0 | 无 | 🟡 低活跃，Dependabot 积压 |
| **ZeptoClaw** | 1 / 0 | 0 / 0 | 无 | 🔵 低活跃，静默等待期 |

---

## 3. OpenClaw 在生态中的定位

**规模领先**：OpenClaw 以日增 500 Issue/PR 的量级远超其他项目，社区贡献者矩阵最广（vincentkoc、jesse-merhi、joshavant 等核心维护者活跃），是生态中**最大众化、最活跃**的参考基线。

**技术路线差异**：
- OpenClaw 走**多模型推理+渠道泛化**路线，今日 GPT-5.6 多模型支持、Puppeteer CDP 中继、Control UI 首次设置优化体现"开箱即用"定位
- 相比 NanoBot（SQLite FTS5、usage 系统重构）偏底层能力，OpenClaw 更注重上层体验与渠道覆盖
- 相比 ZeroClaw（协议 RFC、安全治理）偏基础设施，OpenClaw 更侧重用户侧功能交付

**社区规模对比**：OpenClaw 日均 Issue 量约为 Hermes Agent 的 5 倍、CoPaw 的 15 倍、NanoBot 的 60 倍，反映其用户基数与反馈密度处于生态首位。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **消息投递可靠性** | OpenClaw、CoPaw、NanoBot | 子代理消息丢失、MCP 连接失败导致挂起、Gateway 重启后状态不同步 |
| **会话/状态持久化** | ZeroClaw、NanoBot、Hermes Agent | Session 所有权追踪、任务断点恢复、多步 agent 进度保护 |
| **渠道扩展** | NanoClaw、Moltis、OpenClaw、CoPaw | Mattermost、xAI Grok OAuth、Telegram rich message、WhatsApp 上下文保留 |
| **内存/进程管理** | OpenClaw、CoPaw、NanoBot | 僵尸进程泄漏、长运行内存累积至 GB 级、子进程 reap 机制 |
| **安全与权限治理** | ZeroClaw、OpenClaw、Moltis | delegate bypass 策略绕过、插件安装显式确认、节点配对签名验证 |
| **多模型/Provider 兼容** | OpenClaw、Hermes Agent、Moltis、CoPaw | GPT-5.6、Groq/Cerebras、xAI Grok OAuth、OpenAI strict schema |
| **可观测性与可观测性** | NanoBot、CoPaw、OpenClaw | usage 系统统一、Token 趋势图、日志洪水抑制 |

---

## 5. 差异化定位分析

| 维度 | OpenClaw | CoPaw | ZeroClaw | NanoBot | Hermes Agent | NanoClaw | Moltis |
|------|----------|-------|----------|---------|--------------|----------|--------|
| **核心定位** | 通用个人助手平台 | 多智能体协作 | 协议层+安全治理 | 轻量本地 agent | 桌面端友好 | 渠道集成 | Provider 接入 |
| **目标用户** | 大众用户 | 开发者/企业 | 协议适配者 | 本地部署用户 | 桌面用户 | 多渠道运营 | API/订阅用户 |
| **技术架构** | Gateway+Control UI+Puppeteer | Console+Marketplace+ReMe 记忆 | 协议层+session 持久化 | SQLite FTS5+Usage 系统 | Desktop WS-only | Slack/Mattermost 深度集成 | Provider OAuth+沙箱 |
| **差异化优势** | 最大生态、最多渠道 | 多智能体协作体验 | 协议兼容性（Chat Completions RFC） | 搜索性能+条件触发 | 桌面启动优化 | Slack 新架构 | xAI Grok 订阅接入 |
| **当前短板** | P1 Bug 积压（消息投递/进程泄漏） | 内存泄漏、会话隔离 | 安全漏洞密度高 | Telegram rich message 互斥 | Gateway SIGSEGV、SQLite 错误 | macOS better-sqlite3 segfault | Apple Container ID 越界 |

---

## 6. 社区热度与成熟度分层

```
第一梯队（快速迭代，日百级+吞吐）
├── OpenClaw   — 高频功能迭代 + P1 Bug 清理并行
├── ZeroClaw   — 协议 RFC 推进 + 安全治理双线
└── CoPaw      — 多智能体协作 + 稳定性攻坚

第二梯队（健康维护，日数十级吞吐）
├── Hermes Agent — 债务清理期，架构决策待落地
├── IronClaw    — 架构收敛，规范统一
├── Moltis      — 安全修复集中爆发，Provider 扩展
└── NanoBot     — 底层能力建设 > 功能堆叠

第三梯队（中等/低频，周期性迭代）
├── NanoClaw    — 渠道扩展期，Slack/Mattermost 并重
├── LobsterAI   — 文件/媒体体验优化，Electron 升级待合并
├── PicoClaw    — MCP/Slack Bug 待解，Web UI 重构中
└── NullClaw    — 自托管场景，Dependabot 积压

第四梯队（低活跃/静默）
└── ZeptoClaw   — CLI 体验打磨，核心管道稳定期
```

---

## 7. 值得关注的趋势信号

### 趋势一：从"能用"到"可靠生产"
OpenClaw 10 个 P1 Bug（消息投递、进程泄漏）、CoPaw 内存泄漏至 20GB+、Hermes Agent Gateway SIGSEGV、NanoClaw macOS better-sqlite3 segfault——**稳定性已成为各项目的共同瓶颈**。开发者应优先关注：子代理生命周期管理、连接恢复机制、进程资源回收。

### 趋势二：协议兼容性成为生态入口
ZeroClaw 的 Chat Completions RFC #8603（24 条评论）、Moltis 的 xAI Grok OAuth、NanoBot 的 QwenCloud provider——**谁能更好地适配主流协议（OpenAI API、A2A、MCP），谁就能接入更广泛的工具生态**。建议开发者关注 RFC 接受进度与 PR 合并状态。

### 趋势三：安全治理从"事后修复"转向"架构前置"
ZeroClaw S0 级 delegate bypass、OpenClaw 插件安装显式确认、Moltis 节点配对签名验证——**安全已从功能特性升级为基础设施层要求**。生产部署需重点关注：delegate 权限边界、OAuth 生命周期、插件信任链。

### 趋势四：渠道集成从"单点支持"到"策略化授权"
Moltis 的 Slack 共享频道工具策略化授权、NanoClaw 的 per-agent provisioned Slack apps、CoPaw 的按频道独立配置模型——**多渠道场景下的权限隔离与策略管理成为新战场**。企业用户应关注 `untrusted_audience`/`untrusted_tools` 类配置机制的成熟度。

### 趋势五：代理自主性需求上升
OpenClaw #6757（Agent-triggered context compaction）、NanoBot #5511（崩溃安全任务账本）、CoPaw #3224（自进化多智能体团队）——**用户期望代理能自主管理上下文、恢复中断任务、进化协作模式**。这是从"工具"到"助手"的关键跃迁点，值得长期跟踪。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-25

---

## 1. 今日速览

过去24小时 NanoBot 保持高活跃度：新增 8 个 Issues、26 个 PR，其中 12 个 PR 已被合并/关闭，14 个仍处于待合并状态。项目无新版本发布，但多项核心基础设施改进落地，涵盖**usage 系统重构**、**搜索性能优化**、**Gateway 稳定性修复**三大方向。社区贡献者以 `yrxeva`、`chengyongru`、`albatrossflyon-coder` 为主，整体进展呈现出"底层能力建设 > 功能堆叠"的健康节奏。

---

## 2. 版本发布

今日无新版本发布（Release 数：0）。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR（12 条）

| PR | 作者 | 内容摘要 |
|----|------|---------|
| [#5480](https://github.com/HKUDS/nanobot/pull/5480) | chengyongru | 重构 LLM Usage 系统：将动态字典替换为不可变类型化 `LLMUsage` contract，统一 OpenAI/Anthropic/Bedrock 的 token 与 cache 语义 |
| [#5481](https://github.com/HKUDS/nanobot/pull/5481) | chengyongru | 新增统一 provider usage backend，为每个 retry-managed provider 尝试记录一条 usage row |
| [#5507](https://github.com/HKUDS/nanobot/pull/5507) | yrxeva | 实现 SQLite FTS5 全文搜索索引，解决会话历史增长后的线性扫描性能瓶颈 |
| [#5508](https://github.com/HKUDS/nanobot/pull/5508) | yrxeva | 新增 `ConditionalTriggerRuntime`，实现零 LLM token 的条件触发预过滤 |
| [#5506](https://github.com/HKUDS/nanobot/pull/5506) | Re-bin | 修复 WebUI 选中的项目 workspace 未传递给 agent 的问题 |
| [#5496](https://github.com/HKUDS/nanobot/pull/5496) | chrischen-coder | 修复 `AgentRunner` 超时保护未覆盖 no-tools 请求的回归问题 |
| [#5517](https://github.com/HKUDS/nanobot/pull/5517) | chengyongru | 修复 Windows 进程计时的竞态条件测试问题 |

**整体判断**：项目正稳步推进"原生栈 #5482"架构升级，今日合并的核心 PR 集中解决了 **usage 系统可观测性**与**搜索性能**两大长期痛点，技术债清理节奏健康。

---

## 4. 社区热点

### 高关注 Issues

| Issue | 标题 | 作者 | 日期 | 链接 |
|-------|------|------|------|------|
| #5512 | WebUI 在 Gateway 重启后卡死在旋转状态 | yrxeva | 08-24 | [链接](https://github.com/HKUDS/nanobot/issues/5512) |
| #5516 | Telegram rich messages 与 streaming 互斥 | flobo3 | 08-24 | [链接](https://github.com/HKUDS/nanobot/issues/5516) |
| #5350 | 添加 QwenCloud provider 支持 | evelyn-jialin-zhang | 08-12 | [链接](https://github.com/HKUDS/nanobot/issues/5350) |

**热点分析**：
- **#5512** 是今日最高频报告的稳定问题，前端 `isStreaming` 状态在 Gateway 重启后无法重置，已有对应修复 PR [#5514](https://github.com/HKUDS/nanobot/pull/5514) 待合并。
- **#5516** 反映 Telegram Bot API 10.1-10.3 草案可能解决 rich message + streaming 的兼容问题，属于外部 API 演进驱动的修复需求。
- **#5350** 自 8 月 12 日提出，至今未获响应，关注阿里云 QwenCloud 国际化与 DashScope 兼容的开发者需求。

### 高关注 PR

| PR | 内容 | 作者 | 链接 |
|----|------|------|------|
| [#5504](https://github.com/HKUDS/nanobot/pull/5504) | 模型重试状态展示（NAN-34） | chengyongru | [链接](https://github.com/HKUDS/nanobot/pull/5504) |
| [#5498](https://github.com/HKUDS/nanobot/pull/5498) | Agent TUI 统一配置编辑器 | chengyongru | [链接](https://github.com/HKUDS/nanobot/pull/5498) |
| [#5344](https://github.com/HKUDS/nanobot/pull/5344) | 重复工具调用检测与警告 | albatrossflyon-coder | [链接](https://github.com/HKUDS/nanobot/pull/5344) |

---

## 5. Bug 与稳定性

| 严重程度 | Issue/PR | 描述 | 状态 |
|---------|----------|------|------|
| 🔴 高 | [#5512](https://github.com/HKUDS/nanobot/issues/5512) | WebUI 在 Gateway 重启后持续旋转，`isStreaming` 永远为 true | 修复 PR [#5514](https://github.com/HKUDS/nanobot/pull/5514) 待合并 |
| 🟠 中 | [#5516](https://github.com/HKUDS/nanobot/issues/5516) | Telegram rich message 与 streaming 功能互斥 | 未修复 |
| 🟠 中 | [#5496](https://github.com/HKUDS/nanobot/pull/5496) | no-tools 请求（malformed-call recovery）绕过超时保护 | ✅ 已合并 |
| 🟡 低 | [#5348](https://github.com/HKUDS/nanobot/issues/5348) | 时区相关测试在 ~5 小时窗口内确定性失败 | 修复 PR [#5349](https://github.com/HKUDS/nanobot/pull/5349) 待合并 |

**稳定性评估**：今日共识别 2 个高/中优先级 Bug，其中 Gateway 重启导致 WebUI 卡死为回归问题，修复已在途；Telegram rich message 限制为已知设计取舍，暂无计划修复。

---

## 6. 功能请求与路线图信号

| Issue | 功能需求 | 关联 PR | 纳入可能性 |
|-------|---------|---------|-----------|
| [#5511](https://github.com/HKUDS/nanobot/issues/5511) | 崩溃安全的任务账本（multi-step agent 断点恢复） | — | 🟡 中（需评估持久化方案） |
| [#5513](https://github.com/HKUDS/nanobot/issues/5513) | cron 结果路由到可配置频道 + 批量归档 | — | 🟡 中（运营场景明确） |
| [#5505](https://github.com/HKUDS/nanobot/issues/5505) | 添加 AnySearch 作为 web search provider | — | 🟢 高（key-optional，零集成成本） |
| [#5520](https://github.com/HKUDS/nanobot/pull/5520) | Codex provider 添加 Langfuse tracing | — | 🟢 高（PR 已提交） |

**路线图信号**：今日多 Issue 来自贡献者 `yrxeva`，聚焦于**自动化运维场景**（cron 路由、条件触发、任务持久化），与 #5508 已合并的 `ConditionalTriggerRuntime` 形成完整闭环，暗示项目正加强"无人值守 agent 任务"能力。

---

## 7. 用户反馈摘要

| 来源 | 用户痛点 / 反馈 |
|------|----------------|
| [#5512](https://github.com/HKUDS/nanobot/issues/5512) | Gateway 重启后 WebUI 会话永久挂起，用户无法感知后端已恢复，体验断裂 |
| [#5516](https://github.com/HKUDS/nanobot/issues/5516) | Telegram 用户期望在 streaming 时获得富文本消息，当前被迫在两者间二选一 |
| [#5513](https://github.com/HKUDS/nanobot/issues/5513) | 运维类 cron 任务的噪音污染个人对话窗口，缺乏独立频道和批量管理能力 |
| [#5511](https://github.com/HKUDS/nanobot/issues/5511) | 多步 agent 任务在 Gateway 重启后丢失进度，用户需手动重述任务 |
| [#5350](https://github.com/HKUDS/nanobot/issues/5350) | QwenCloud 开发者希望在不破坏现有 DashScope 配置的前提下使用新平台 |
| [#5344](https://github.com/HKUDS/nanobot/pull/5344) | agent 陷入重复工具调用的 silent spiral，用户从外部看表现为"冻结" |

---

## 8. 待处理积压

| Issue/PR | 创建日期 | 状态 | 风险提示 |
|---------|---------|------|---------|
| [#5350](https://github.com/HKUDS/nanobot/issues/5350) | 08-12 | 开放，无响应 | 阿里云生态扩展需求，13 天未处理 |
| [#5511](https://github.com/HKUDS/nanobot/issues/5511) | 08-24 | 开放，无 PR | 任务持久化关键能力，无对应 PR |
| [#5513](https://github.com/HKUDS/nanobot/issues/5513) | 08-24 | 开放，无 PR | 运维场景需求，无对应 PR |
| [#5516](https://github.com/HKUDS/nanobot/issues/5516) | 08-24 | 开放，无 PR | Telegram 用户痛点，无对应 PR |
| [#5430](https://github.com/HKUDS/nanobot/pull/5430) | 08-18 | 开放待合并 | 长期运行 agent 的内存泄漏修复，6 天未合并 |
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) | 06-26 | 开放待合并 | heartbeat 模型覆盖功能，近 2 个月未合并 |

**维护者建议**：`#4549` 和 `#5430` 已开放较长时间，建议优先 review 合并；`#5350` 涉及阿里云生态合作，可评估是否纳入官方 provider 列表。

---

*报告生成时间：2026-08-25 | 数据来源：HKUDS/nanobot GitHub*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-25

## 1. 今日速览

Hermes Agent 今日保持高活跃状态，过去24小时共处理 **100 条** Issue/PR 更新（50 Issues + 50 PRs），其中新开/活跃 Issues 达 47 条，显示社区反馈管道畅通。PR 池中有 **42 条待合并**，8 条已合并/关闭，合并吞吐量与新增量基本平衡。今日无明显版本发布，但多条 P1/P2 级 Bug 修复 PR 集中提交，反映维护团队正主动清理累积的稳定性债务。项目整体处于**健康迭代期**，在桌面端体验、会话状态管理、MCP 工具链和跨平台兼容性四个方向均有实质性推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（8 条）

| PR | 作者 | 内容概述 |
|---|---|---|
| [#18133](https://github.com/NousResearch/hermes-agent/pull/18133) [CLOSED] | dterenyi | Conductor mission 进程管理：新增 `/api/conductor/missions` 端点，使 Dashboard 启动的 Conductor 工作能够以持久化 Hermes 进程运行 |
| [#18138](https://github.com/NousResearch/hermes-agent/pull/18138) [CLOSED] | dterenyi | 修复 Dashboard 分析接口返回 `null` 而非数值零的 bug，补充回归测试 |
| [#58606](https://github.com/NousResearch/hermes-agent/pull/58606) [CLOSED] | kuehnberger | 新增 Groq 和 Cerebras 模型提供商自动识别支持 |

**整体判断：** 已合并 PR 集中在 Dashboard 后端修复和模型提供商扩展，属于低风险增量改进。今日尚无核心架构层面的大规模合入，但 **PR #94245**（精简 WS-only 服务器，移除 FastAPI/uvicorn 桌面启动路径）已进入最后 Review 阶段，将是桌面启动性能优化的关键一步。

---

## 4. 社区热点

### 高评论 Issue 排行

| 排名 | Issue | 评论数 | 类型 | 核心议题 |
|---|---|---|---|---|
| 🔥1 | [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 91 | Bug/P3 | Skills 索引过时/退化——自动化探测发现索引超过 26h 未刷新 |
| 🔥2 | [#85125](https://github.com/NousResearch/hermes-agent/issues/85125) | 20 | Feature/P3 | 统一超时/挂起修复架构：4 阶段计划，解决 400+ 同类 Issue |
| 🔥3 | [#25833](https://github.com/NousResearch/hermes-agent/issues/25833) | 10 | Feature/P2 | 自定义 Skill 缺乏正确性保障机制 |
| 4 | [#5114](https://github.com/NousResearch/hermes-agent/issues/5114) | 7 | Feature/P3 | 自动研究 Skill——基于 git 的 ML 实验循环 |
| 5 | [#93888](https://github.com/NousResearch/hermes-agent/issues/93888) | 7 | Bug/P2 | Desktop 远程会话恢复失败——runtime ID 不匹配 |

**热点分析：**
- **#66616** 以 91 条评论成为当前最活跃 Issue，反映用户对 Skills 索引可靠性的高度关注，该问题由自动化探针触发，说明项目已有基础监控但修复滞后。
- **#85125** 是对历史积压的结构性回应，将 77 个 runtime stall Issue 归约为 7 类机制，社区对系统性解决方案有明确期待。
- **#25833** 触及 Skill 生态的核心信任问题——Agent 自创 Skill 缺乏验证保障，直接影响 Skill Hub 的可信度。

### 高互动 PR

| PR | 核心内容 |
|---|---|
| [#94245](https://github.com/NousResearch/hermes-agent/pull/94245) | 精简桌面启动路径：移除 FastAPI/uvicorn，改用 bare websockets 服务器，预期显著降低启动延迟 |
| [#94312](https://github.com/NousResearch/hermes-agent/pull/94312) | 新增用户级会话路由，支持为子 Agent 指定独立 provider/model/reasoning effort |
| [#94339](https://github.com/NousResearch/hermes-agent/pull/94339) | 修复 MCP stdio 子进程存活检测逻辑反转 bug |

---

## 5. Bug 与稳定性

### P1 级（紧急）

| Issue | 标题 | 状态 | Fix PR |
|---|---|---|---|
| [#94248](https://github.com/NousResearch/hermes-agent/issues/94248) | Gateway SIGSEGV — delegate 超时后 17-72ms 崩溃（macOS arm64） | OPEN | 暂无 |
| [#92145](https://github.com/NousResearch/hermes-agent/issues/92145) | `hermes update` 在 ImportError 时残留 stale `sys.modules` | OPEN | 暂无 |
| [#94258](https://github.com/NousResearch/hermes-agent/issues/94258) | SQLite SystemError 未捕获导致 session 持久化失败 | OPEN | 暂无 |
| [#94264](https://github.com/NousResearch/hermes-agent/issues/94264) | 更新可恢复无效 Python 并报告成功，导致远程锁定 | OPEN | 暂无 |

### P2 级（重要）

| Issue | 标题 | 状态 | Fix PR |
|---|---|---|---|
| [#93888](https://github.com/NousResearch/hermes-agent/issues/93888) | 远程会话恢复失败——runtime ID 不匹配 | OPEN | 暂无 |
| [#90229](https://github.com/NousResearch/hermes-agent/issues/90229) | Desktop 右侧文件树启动后卡在 skeleton | OPEN | 暂无 |
| [#92818](https://github.com/NousResearch/hermes-agent/issues/92818) | Desktop 窗格布局跨重启不稳定 | OPEN | 暂无 |
| [#81051](https://github.com/NousResearch/hermes-agent/issues/81051) | OAuth MCP 连接 4h 后永久卡死（parked） | OPEN | 暂无 |
| [#94324](https://github.com/NousResearch/hermes-agent/issues/94324) | 后台 curator 编辑已有 Skill 时被 read-before-write guard 拒绝 | OPEN | 暂无 |
| [#93981](https://github.com/NousResearch/hermes-agent/issues/93981) | 非 loopback dashboard URL 导致 Desktop 聊天 WebSocket 拒绝 | OPEN | 暂无 |
| [#94271](https://github.com/NousResearch/hermes-agent/issues/94271) | ACP 忽略 `agent.max_turns` 配置 | OPEN | 暂无 |

**已有 Fix PR 的 Bug：**
- [#92701](https://github.com/NousResearch/hermes-agent/issues/92701) [CLOSED] — Docker 持久沙箱路径冒号未清洗导致 exit 125（已修复）
- [#94339](https://github.com/NousResearch/hermes-agent/pull/94339) — MCP stdio 子进程存活检测逻辑反转
- [#94340](https://github.com/NousResearch/hermes-agent/pull/94340) — Bot Mode 群组日志外部写入不同步
- [#94320](https://github.com/NousResearch/hermes-agent/pull/94320) — Computer Use 受限清单审批信任
- [#94338](https://github.com/NousResearch/hermes-agent/pull/94338) — 畸形 `mcp_servers` 条目导致 Desktop 崩溃（已提交 PR）

**稳定性评估：** 今日报告了 **4 个 P1 级问题**（Gateway 崩溃、更新损坏、SQLite 错误、远程锁定），加上 7 个 P2，整体稳定性压力偏高。多个 Windows 平台特定 Bug 集中爆发，需关注跨平台回归风险。

---

## 6. 功能请求与路线图信号

### 高潜力功能请求

| Issue | 需求描述 | 匹配 PR | 纳入可能性 |
|---|---|---|---|
| [#85125](https://github.com/NousResearch/hermes-agent/issues/85125) | 统一超时/挂起修复架构（4 阶段） | 尚无直接对应 PR | ⭐⭐⭐⭐⭐ 高优先级，维护者已标记 `needs-decision` |
| [#5114](https://github.com/NousResearch/hermes-agent/issues/5114) | Autoresearch Skill——git 驱动 ML 实验循环 | 尚无 | ⭐⭐⭐ 中等，需求明确但实现复杂 |
| [#94000](https://github.com/NousResearch/hermes-agent/issues/94000) | Cron 消息 per-target 文本变换 | [#41833](https://github.com/NousResearch/hermes-agent/pull/41833) | ⭐⭐⭐⭐ PR 已提交，聚焦 transform 子集 |
| [#79757](https://github.com/NousResearch/hermes-agent/issues/79757) | Gateway 忙/重定向消息 i18n | [#92338](https://github.com/NousResearch/hermes-agent/pull/92338) | ⭐⭐⭐⭐ PR 已提交，覆盖剩余硬编码文本 |
| [#92885](https://github.com/NousResearch/hermes-agent/issues/92885) | Desktop 预览浏览器独立配色 | 暂无 | ⭐⭐ 低优先级，体验类需求 |

### 路线图信号总结

1. **会话状态管理加固**：多个 P1/P2 Issue 指向 session 持久化、SQLite 错误处理和路由稳定性，预计下一版本将重点投入该方向。
2. **桌面启动性能优化**：PR #94245 的 WS-only 精简方案若合并，将是桌面端架构的重要演进。
3. **MCP 工具链可靠性**：今日提交的多个 MCP 相关修复（#94339、#94338）及 #81051 的 OAuth 卡死问题，表明 MCP 集成是当前稳定性短板，预计将持续投入。
4. **i18n 覆盖扩展**：PR #92338 正在补全 gateway 静态文本的本地化，是国际化路线图的明确信号。

---

## 7. 用户反馈摘要

### 真实痛点

| 痛点类别 | 用户反馈来源 | 核心诉求 |
|---|---|---|
| **会话恢复失败** | [#93888](https://github.com/NousResearch/hermes-agent/issues/93888)、[#94258](https://github.com/NousResearch/hermes-agent/issues/94258) | 远程会话和 SQLite 持久化不可靠，影响生产使用信任 |
| **Desktop 启动体验** | [#90229](https://github.com/NousResearch/hermes-agent/issues/90229)、[#92818](https://github.com/NousResearch/hermes-agent/issues/92818)、[#94319](https://github.com/NousResearch/hermes-agent/issues/94319) | Windows 上文件树卡死、窗口最大化/还原异常、布局跨重启丢失 |
| **MCP 连接稳定性** | [#81051](https://github.com/NousResearch/hermes-agent/issues/81051) | OAuth MCP 连接 4h 后永久卡死，仅重启可恢复 |
| **Skills 索引可靠性** | [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 索引超过 26h 未刷新，自动化探针持续告警 |
| **后台 Skill 编辑失败** | [#94324](https://github.com/NousResearch/hermes-agent/issues/94324) | curator 自动编辑已有 Skill 时被 read-before-write guard 拒绝 |
| **超时/挂起积压** | [#85125](https://github.com/NousResearch/hermes-agent/issues/85125) | 400+ 同类 Issue 长期未解决，用户期待架构级修复 |
| **Docker 沙箱路径** | [#92701](https://github.com/NousResearch/hermes-agent/issues/92701) | task_id 含冒号导致 Docker 命令失败（已修复） |
| **OpenWebUI 图片传输** | [#7895](https://github.com/NousResearch/hermes-agent/issues/7895) | 通过 OpenAI 端点集成时图片未传回 OpenWebUI（3 个 👍） |

### 满意点
- Docker 沙箱冒号问题已快速修复并关闭（#92701）
- Groq/Cerebras 提供商支持已合并（#58606）
- Conductor mission 进程管理功能已落地（#18133）

---

## 8. 待处理积压

### 需维护者重点关注

| Issue/PR | 优先级 | 未响应原因推测 | 建议行动 |
|---|---|---|---|
| [#85125](https://github.com/NousResearch/hermes-agent/issues/85125) | P3（但影响 400+ Issue） | `needs-decision`——需架构决策 | 安排专项讨论，确定 4 阶段实施顺序 |
| [#81051](https://github.com/NousResearch/hermes-agent/issues/81051) | P2 | 无 Fix PR，MCP SDK 1.26.0 引入的 teardown 竞态 | 评估 MCP SDK 升级或本地 workaround |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | P3（91 条评论） | 索引刷新 cron 可能配置或执行异常 | 检查 `.github/workflows/skills-index.yml` 运行日志 |
| [#25833](https://github.com/NousResearch/hermes-agent/issues/25833) | P2 | `needs-decision`——涉及 Skill 系统核心设计 | 明确 Skill 正确性保障机制的技术方案 |
| [#94248](https://github.com/NousResearch/hermes-agent/issues/94248) | P1 | SIGSEGV 复现需要 macOS arm64 环境 | 请求崩溃报告（12 份 crash report 已收集） |
| [#92145](https://github.com/NousResearch/hermes-agent/issues/92145) | P1 | `hermes update` 回滚机制缺陷 | 审查 auto-restart 阶段的错误处理路径 |

### 长期未合并 PR

| PR | 状态 | 内容 | 阻塞推测 |
|---|---|---|---|
| [#41833](https://github.com/NousResearch/hermes-agent/pull/41833) | OPEN（60+ 天） | Cron  rich delivery hooks | 范围较大，子 Issue #94000 建议裁剪后先合入 transform 部分 |
| [#64848](https://github.com/NousResearch/hermes-agent/pull/64848) | OPEN（40+ 天） | `browser_wait` 工具 | 独立 scoped，可优先 Review |
| [#68499](https://github.com/NousResearch/hermes-agent/pull/68499) | OPEN（35+ 天） | Delegate 生命周期与任务结果分离 | 影响面大，需充分测试 |
| [#92338](https://github.com/NousResearch/hermes-agent/pull/92338) | OPEN | Gateway i18n 补全 | 低风险，可优先合并 |

---

**报告生成时间：** 2026-08-25  
**数据周期：** 过去 24 小时  
**分析师：** Agnes-2.0-Flash (Sapiens AI)

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-08-25

---

## 1. 今日速览

过去 24 小时内，PicoClaw 共新增 3 条活跃 Issue、3 条 PR 更新（其中 2 条已合并、1 条待审），无新版本发布。项目整体活跃度中等偏下，核心维护工作集中在 Web 安全配置修复与新搜索提供商集成两条主线。当前无高危阻塞性 Bug，但 MCP 服务器挂起和 Slack 媒体上传两项缺陷已影响实际用户体验。

---

## 2. 版本发布

无新版本发布。最近一次版本更新未见记录。

---

## 3. 项目进展

### 已合并 / 关闭的 PR（2 条）

| PR | 类型 | 内容 |
|---|---|---|
| [#1929](https://github.com/sipeed/picoclaw/pull/1929) | Bug Fix | 修复 Web Launcher 在保存配置时校验时序错误导致的凭据校验失败问题 |
| [#1551](https://github.com/sipeed/picoclaw/pull/1551) | Bug Fix | 合并 #1428 / #1422 / #1417 三项修复 |

**分析：** PR #1929 解决了一个长期存在的配置保存时序 Bug——当 `pico` 频道启用时，`validateConfig()` 在安全凭据写入 `.security.yml` 之前就进行校验，导致合法的 token 被误判为缺失。该修复已合并，有助于提升配置管理稳定性。PR #1551 作为聚合修复，合并了三项历史遗留补丁。

### 待合并 PR（1 条）

| PR | 类型 | 内容 |
|---|---|---|
| [#3299](https://github.com/sipeed/picoclaw/pull/3299) | Feature | 新增 Exa 原生 Web 搜索 Provider |

**分析：** Exa 搜索支持是用户呼声较高的功能，PR 实现了 `tools.web` / `web_search` 接口的 Exa 适配器，支持 `startPublishedDate` 时间范围过滤与内容摘要高亮，符合项目现有扩展架构。

---

## 4. 社区热点

### Issue #806 — 最高关注度 🔥
**[Add webUI support](https://github.com/sipeed/picoclaw/issues/806)** · 👍 8 · 💬 10 · `enhancement` / `high` / `roadmap`

> 提议开发专用 Web UI，降低非技术用户的使用门槛。作者当前正在重构以支持此功能。

**诉求分析：** Web UI 是 PicoClaw 社区最核心、持续最久的功能请求。当前 TUI 对终端用户友好，但限制了大众用户群体。该 Issue 长期占据高票，说明用户需求明确且强烈。目前已有重构工作推进，值得持续关注。

### Issue #3269 — 活跃度上升
**[MCP 连接失败导致 agent 循环挂起](https://github.com/sipeed/picoclaw/issues/3269)** · 👍 1 · 💬 7 · `bug` / `stale`

**诉求分析：** 用户在使用 Qwen3 模型时，MCP 服务器连接失败导致整个 agent 循环挂起，聊天界面停止响应。该问题已标记为 `stale`，但评论持续活跃，说明问题尚未解决，需优先处理。

### Issue #3338 — 新报告 Bug
**[Slack 无法附加图片媒体](https://github.com/sipeed/picoclaw/issues/3338)** · 👍 0 · 💬 1 · `bug` / `stale`

**诉求分析：** Slack 媒体上传始终失败，根因是 `SendMedia` 未设置 `FileSize`，导致 SDK 在发起网络请求前即拒绝。问题定位清晰，但尚未有 PR 跟进。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|---|
| 🔴 高 | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP 服务器连接失败 → agent 循环挂起 → 聊天无响应 | OPEN / stale | ❌ 无 |
| 🟡 中 | [#3338](https://github.com/sipeed/picoclaw/issues/3338) | Slack 媒体上传因 `FileSize` 未设置而失败 | OPEN / stale | ❌ 无 |
| 🟢 低 | PR #1929 已修复 | Web 配置校验时序导致 token 校验误报 | CLOSED（已合并） | ✅ 已解决 |

**稳定性评估：** 两个未解决 Bug 均影响特定渠道（MCP、Slack），不涉及核心 agent 循环逻辑，但会直接导致用户会话中断或功能失效。建议优先处理 #3269，因其影响面更广。

---

## 6. 功能请求与路线图信号

| 信号 | Issue / PR | 可能纳入版本 |
|---|---|---|
| 🟢 高确定性 | [#3299](https://github.com/sipeed/picoclaw/pull/3299) — Exa 原生搜索 | 下一版本（PR 已就绪，待合并） |
| 🟡 中确定性 | [#806](https://github.com/sipeed/picoclaw/issues/806) — Web UI | 路线图中长期，重构进行中 |

**分析：** Exa 搜索 PR 架构完整、实现清晰，预期可在近期合入。Web UI 为大型重构，作者已标记"正在重构"，短期内难以上线正式版，但可作为里程碑跟踪。

---

## 7. 用户反馈摘要

- **痛点 1（#3269）：** MCP 服务器连接失败时整个 agent 循环挂起，用户对话完全卡死，体验极差。反映出错误处理机制存在缺陷，连接失败未能优雅降级。
- **痛点 2（#3338）：** Slack 频道图片上传静默失败，且错误信息不清晰（仅返回 `file size cannot be 0`），排查困难。
- **满意度（#1929 相关）：** 配置保存的凭据处理问题已得到修复，提升了非技术用户的配置体验。
- **期待（#806）：** 社区普遍渴望降低使用门槛，Web UI 是最高频需求，现有 TUI 对普通用户形成显著门槛。

---

## 8. 待处理积压

| Issue / PR | 类型 | 最后更新 | 建议 |
|---|---|---|---|
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) | Bug（高） | 2026-08-25 | ⚠️ 已 stale 但讨论活跃，建议维护者介入评估修复方案 |
| [#3338](https://github.com/sipeed/picoclaw/issues/3338) | Bug（中） | 2026-08-24 | ⚠️ 根因明确（缺 `FileSize`），建议安排修复 |
| [#3299](https://github.com/sipeed/picoclaw/pull/3299) | Feature（高） | 2026-08-24 | 待合并，建议 Review 后合入 |
| [#806](https://github.com/sipeed/picoclaw/issues/806) | Enhancement | 2026-08-24 | 长期路线图项，建议定期同步重构进度 |

---

**项目健康度总评：🟡 中等偏上。** 核心架构稳定，安全配置 Bug 已修复；但 MCP 和 Slack 两个渠道的 Bug 长期未解决，影响用户会话连续性和多平台体验。Exa 搜索功能即将落地，Web UI 重构持续推进，未来两个季度有明确的功能扩展方向。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：2026-08-25** | 分析周期：2026-08-24 ~ 2026-08-25

---

## 1. 今日速览

NanoClaw 过去24小时保持**中高水平活跃度**：1个新版本发布、21条PR（3条合并）、2条Issue（1条关闭）。核心亮点是 **v2.3.0** 带来了 Slack 体验的重大架构升级，以及 Mattermost 渠道的新增支持。项目整体处于快速迭代期，团队在渠道集成、数据库协调、AI编程CLI适配三个方向并行推进。

**活跃度评估**：🟢 健康 — 合并速率正常，新问题有响应，无积压风险。

---

## 2. 版本发布

### v2.3.0 — Slack 渠道体验升级

**破坏性变更**：
- 引入「per-agent provisioned Slack apps」架构，支持从 Slack 直接启动 agent
- 经典单 bot 模式继续正常工作，但新安装会引导用户选择新模式
- 非 Slack 安装不受影响

**迁移注意事项**：
- 该变更是「门控式」而非强制迁移，用户需主动选择是否切换到新 Slack 体验
- 经典 Slack 安装保持向后兼容，无需立即改动

> 🔗 关联 PR：#3428 `feat(slack-agent-flow): carry the template ref through Slack creation`

---

## 3. 项目进展

### 今日合并/关闭的 PR（3条）

| PR | 类型 | 说明 |
|----|------|------|
| [#2474](https://github.com/nanocoai/nanoclaw/issues/2474) | Fix | AI-coding-CLI picker：setup 流程支持选择 Claude Code 或 Codex |
| [#2475](https://github.com/nanocoai/nanoclaw/issues/2475) | Feature | Codex agent 现可访问与 Claude Code 相同的 persona + skill catalog |
| [#2767](https://github.com/nanocoai/nanoclaw/issues/2767) | Fix | Telegram Markdown 兼容性问题，适配 `@chat-adapter/telegram@4.30.0` 原生 MarkdownV2 |

**推进方向**：
- **AI编程CLI适配**：#2474/#2475 标志着 Codex 与 Claude Code 的功能对齐进入收尾阶段
- **渠道稳定性**：Telegram 的 `legacy-Markdown` 清理工作完成，减少上游依赖漂移风险

---

## 4. 社区热点

### 高关注度 PR（按活跃程度排序）

**① [#3508](https://github.com/nanocoai/nanoclaw/pull/3508) — `feat(db): durable host-coordination state`**
- 作者：gavrielc | 核心开发团队成员
- 解决重启导致的关键状态丢失问题：审批等待者、投递重试计数、stop/respawn 意图
- 这是基础设施级修复，影响所有生产部署的可靠性

**② [#3493](https://github.com/nanocoai/nanoclaw/pull/3493) — `docs(mindshub): add MindsHub provider guide`**
- 作者：torrmal
- 新增 MindsHub 提供商指南和 setup skill，完善生态文档覆盖

**③ [#3502](https://github.com/nanocoai/nanoclaw/pull/3502) + [#3507](https://github.com/nanocoai/nanoclaw/pull/3507) — Mattermost 渠道支持**
- 作者：glifocat
- 双 PR 组合：SDK adapter 改造 + 安装 skill，完整补齐 Mattermost 集成

**④ [#3396](https://github.com/nanocoai/nanoclaw/pull/3396) — `feat: create agents from templates in chat`**
- 作者：amit-shafnir
- 核心功能：通过 `create_agent` 工具的 `template` 参数从模板创建 agent，支持本地和注册表模板

> **热点分析**：今日讨论焦点集中在**基础设施可靠性**（#3508）和**渠道扩展**（Mattermost/Awaken），反映出用户从"能不能用"向"能不能稳定生产用"的诉求转变。

---

## 5. Bug 与稳定性

### 🔴 严重：better-sqlite3 13 segfault on macOS

**Issue [#3497](https://github.com/nanocoai/nanoclaw/issues/3497)** — 状态：OPEN
- 作者：brentkearney | 创建/更新：2026-08-24
- **问题**：`better-sqlite3@13.0.3` 在 Node 22 版本 < 22.14.0 的 macOS 上，调用 `new Database()` 时发生 segfault
- **影响**：数据库层完全不可用，`pnpm test` 无法完成，安装后功能瘫痪
- **根因**：项目声明的 Node 最低版本 `>=22` 与实际要求 `>=22.14.0` 存在偏差
- **Fix PR**：暂无

### 🟡 中等：macOS 上 update 事务控制器路径比较缺陷

**PR [#3506](https://github.com/nanocoai/nanoclaw/pull/3506)** — 状态：OPEN（待合并）
- 作者：chiptoe-svg
- 6 处修复使 `/update-nanoclaw` 事务控制器在 macOS 上行为正确
- 修复均在真实 macOS 安装更新过程中发现

### 🟢 轻微：OneCLI gateway bind address 未正确配置

**PR [#3302](https://github.com/nanocoai/nanoclaw/pull/3302)** — 状态：OPEN（待合并）
- 作者：wakqasahmed
- 修复 #2903：OneCLI gateway 安装后未将 `api-host` 写入 docker-compose 配置，导致容器内无法访问

---

## 6. 功能请求与路线图信号

### 已明确纳入近期版本的功能

| 功能 | 状态 | 关联 PR |
|------|------|---------|
| Mattermost 渠道集成 | 开发中 | #3502, #3507 |
| Apple Container 会话驱动 | 开发中 | #3503 |
| 从模板创建 agent | 开发中 | #3396 |
| Slack 模板创建流程 | 开发中 | #3428 |
| Dial 渠道文档完善 | 文档更新 | #3501 |

### 路线图中可见的趋势
1. **多渠道扩展**：Mattermost + Dial 同时推进，渠道生态持续丰富
2. **Provider 对齐**：Codex 与 Claude Code 的功能 parity 已基本完成（#2474/#2475）
3. **可靠性基建**：#3508 的 durable host-coordination state 是生产化必经之路

---

## 7. 用户反馈摘要

### 真实痛点

| 场景 | 反馈来源 | 用户声音 |
|------|---------|---------|
| **数据库层崩溃** | #3497 | "an affected Node passes every check and then leaves the install with no working database layer" — 安装后完全无法使用， frustrate 感强烈 |
| **模板创建 agent** | #3396 | 用户希望不写代码即可从预设模板快速启动 agent |
| **Slack 新体验** | v2.3.0 | 用户需要更灵活的 per-agent Slack 配置，而非单 bot 模式 |
| **OneCLI 内网访问** | #3302 | 容器化部署场景下 gateway 地址配置不透明 |

### 用户满意点
- Telegram MarkdownV2 原生适配完成（#2767），消除了 work-around 代码的维护负担
- setup 流程现在支持选择 AI 编程 CLI（Claude Code vs Codex），给了用户选择权

---

## 8. 待处理积压

### ⚠️ 需关注

| 类型 | Issue/PR | 风险 | 建议 |
|------|---------|------|------|
| 🔴 Bug | [#3497](https://github.com/nanocoai/nanoclaw/issues/3497) — macOS better-sqlite3 segfault | 高 | 紧急：需在 v2.3.x 中修复或提升 Node 最低版本声明 |
| 🟡 PR | [#3506](https://github.com/nanocoai/nanoclaw/pull/3506) — macOS update 控制器修复 | 中 | 待核心团队 review，影响 macOS 用户更新体验 |
| 🟡 PR | [#3500](https://github.com/nanocoai/nanoclaw/pull/3500) — OneCLI 硬编码 gateway image tag | 中 | 文档/配置类修复，影响升级流程 |
| 🟢 PR | [#3504](https://github.com/nanocoai/nanoclaw/pull/3504) — 本地分支合并到 main | 低 | 历史分支清理，需确认功能完整性 |

---

**日报总结**：NanoClaw v2.3.0 发布后整体健康度良好，核心工作在渠道扩展（Mattermost/Applied Container）和可靠性加固（host-coordination）双轨并行。需重点关注 **#3497** 的 macOS 数据库 segfault 问题，建议在下一版本中修复或明确升级 Node 版本要求。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 | 2026-08-25

---

## 1. 今日速览

NullClaw 过去24小时保持**低活跃度**状态，共收到 2 条 Issue 更新（均为新开）和 1 条 PR 更新（待合并），无版本发布。社区围绕自托管场景和配对码体验提出了实际痛点，反映出用户对灵活部署和调试便利性的持续需求。整体来看，项目维护节奏平稳，但 PR 积压存在一定风险。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日**无 PR 合并**，主要进展如下：

- **#956** [DEPENDABOT] CI依赖更新：将 Alpine 基础镜像从 3.23 升级至 3.24，提升 Docker 镜像的安全性与包生态一致性。该 PR 由 Dependabot 于 2026-06-15 创建，截至昨日仍有待处理，需维护者跟进审查。  
  [查看 PR #956](https://github.com/nullclaw/nullclaw/pull/956)

---

## 4. 社区热点

| Issue/PR | 类型 | 热度 | 链接 |
|----------|------|------|------|
| #993 | Enhancement | 新关注 | [查看 Issue #993](https://github.com/nullclaw/nullclaw/issues/993) |
| #992 | Bug | 新关注 | [查看 Issue #992](https://github.com/nullclaw/nullclaw/issues/992) |

**热点分析：**

- **#993** 反映了自托管用户的典型诉求：内置 Firecrawl provider 硬编码 API endpoint，限制了灵活部署能力。用户期望支持自定义 endpoint 配置，以适配私有化部署场景。
- **#992** 揭示了调试体验问题：配对码在隐藏模式下仅存于内存，导致用户无法获取 6 位配对 token，严重影响 Gateway API 配置流程。Issue 中引用了 #535 作为变更根源，说明历史决策可能影响了可用性。

---

## 5. Bug 与稳定性

| 问题 | 严重程度 | 链接 | Fix PR |
|------|----------|------|--------|
| #992 配对码隐藏后无法查看 | 中（影响配置体验） | [Issue #992](https://github.com/nullclaw/nullclaw/issues/992) | 暂无 |

**说明：** #992 描述了一个回归问题——此前配对码可通过 stdout 查看，#535 变更后改为仅存内存且未提供替代获取途径。该问题虽不影响核心功能稳定性，但对首次配置用户造成显著障碍，建议优先修复。

---

## 6. 功能请求与路线图信号

- **#993** [功能增强] 支持自托管 Firecrawl 实例：用户希望内置 provider 支持可配置的 endpoint，便于私有化部署。该需求与项目面向自托管 AI 助手场景的定位高度契合，可纳入后续版本规划。

---

## 7. 用户反馈摘要

- **痛点一**：自托管场景下内置工具的灵活性不足。#993 明确指出硬编码 endpoint 限制了 Firecrawl 在私有环境中的使用，反映出用户对可配置性的强烈诉求。
- **痛点二**：调试信息丢失导致配置困难。#992 中用户表示"困惑数天"，配对码隐藏后无处获取，暴露了 UX 设计在安全性与可用性之间的权衡问题。

---

## 8. 待处理积压

| 条目 | 类型 | 创建时间 | 待处理天数 | 链接 |
|------|------|----------|------------|------|
| #956 | PR（依赖更新） | 2026-06-15 | ~71 天 | [PR #956](https://github.com/nullclaw/nullclaw/pull/956) |

**提醒：** Dependabot 创建的 Alpine 升级 PR 已积压超过 70 天未合并，建议维护者优先审查处理，以确保基础镜像的安全性和兼容性。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 | 2026-08-25

## 1. 今日速览
过去24小时项目保持高活跃状态，共处理 21 个 Issues（新开/活跃 12，关闭 9）与 35 个 PRs（待合并 18，已合并/关闭 17）。开发重心集中在**Onboarding 建议数据接地、Telegram 设备绑定链路修复、CI Rust 工具链集中化、WebUI 组件标准化**四大方向。无新版本发布，整体项目健康度良好，Bug 修复与架构优化并行推进，技术债务（如超大文件分解、缓存稳定性）得到明确响应。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
今日合并/关闭的 PR 主要推动以下方向：
- **建议生成数据接地**：`#7833` 修复了建议卡片仅依赖硬编码工具白名单的问题，改为读取用户级权限并限制为只读/无需审批工具，使建议内容真正关联用户已连接账户（关联 `#7812`）。
- **CI 架构收敛**：`#7821` 将散落在 12 个 workflow 中的 43 处 `dtolnay/rust-toolchain` 调用收拢至单一 composite action，统一工具链、链接器与构建 profile，消除本地/CI 环境漂移（关联 `#7798`）。
- **WebUI 组件标准化**：`#7794` 引入共享的 `PageScroll`、`PageStack`、`Skeleton` 与 `SkeletonList` 原语，统一 Automations、Extensions、Admin 等路由的滚动、间距与加载态表现；`#7857` 修复了激活建议任务后左侧 Conversation 列表未同步刷新的回归问题（关联 `#7845`）；`#7854` 移除了登录页残留的 `Gateway v2` 标记与废弃 locale key。
- **Agent 循环缓存优化**：`#7001` 确保 system prefix 在跨模型调用时保持字节稳定，消除因时间戳/nuke nudges 导致的缓存无效化（关联 `#6985`）。

项目整体向前推进约 **0.3-0.5 个迭代周期**，核心体验闭环（连接→建议→线程）基础已打通，底层架构正从“单点修复”转向“规范收敛”。

## 4. 社区热点
- **Telegram 绑定链路阻塞**：`#7853` 反馈 Railway 实例中个人 Telegram 账号绑定流程卡死；`#7862` 补充了未配置 `telegram_api_id/api_hash` 时泛化报错 `Something went wrong while linking` 的现象；配套修复 PR `#7861` 已提交以恢复缺失的设备绑定引导。
- **MCP 工具命名兼容**：`#7856` 指出托管 MCP 发现逻辑静默跳过 camelCase 工具名，导致部分第三方工具不可见。
- **大文件架构治理**：`#7860` 提议将 `lifecycle_product_service.rs`（1,774 行）按架构规范拆解，避免单文件膨胀。
- **后台 Subagent 执行**：`#7818` 推进 R2 后台子代理的 Producer 阶段（2b+2c slice），实现 receipt 生成、子任务分发与愈合扫描。

## 5. Bug 与稳定性
| 严重级别 | Issue | 描述 | 修复状态 |
|:---:|:---|:---|:---|
| 🔴 高 | [#7853](https://github.com/nearai/ironclaw/issues/7853) / [#7862](https://github.com/nearai/ironclaw/issues/7862) | Telegram 个人账号绑定失败/泛化报错 | PR [#7861](https://github.com/nearai/ironclaw/pulls/7861) 跟进中 |
| 🟡 中 | [#7297](https://github.com/nearai/ironclaw/issues/7297) | 每次 prompt 失败后 UI 错误消息持续累积不清除 | 暂无 Fix |
| 🟡 中 | [#7856](https://github.com/nearai/ironclaw/issues/7856) | MCP 工具发现静默忽略 camelCase 名称 | 暂无 Fix |
| 🟢 低 | [#7845](https://github.com/nearai/ironclaw/issues/7845) | 激活建议任务后左侧 Conversation 列表未渲染 | 已合并 [#7857](https://github.com/nearai/ironclaw/pulls/7857) |
| 🟢 低 | [#7848](https://github.com/nearai/ironclaw/issues/7848) | Daily taxonomy 显示 DeepSeek-V4-Flash OCR 管道存在模型级错误 | 持续监控中 |

## 6. 功能请求与路线图信号
- **GSuite 原生 CLI 捆绑**：`#7849`（v1.4.0, suggested_P1）提议在 extensions 中内置 agent-first 的 Google Workspace CLI，解决 Gmail 列表/读取操作嵌套深、payload 冗余的问题，信号明确指向 v1.4.0 核心能力扩展。
- **意大利语本地化**：`#7855` 请求新增意大利语支持，与现有多语言策略对齐。
- **自动化能力事实暴露**：`#7850` 新增 `builtin.trigger_status`，使自动化任务可精确读取单次运行的状态元数据，提升可观测性。
- **WebUI 设计系统**：`#7257` 与 `#7255` 已归档，APDD 治理框架与 Storybook 蓝图进入实施期，支撑后续 UI 一致性迭代。

## 7. 用户反馈摘要
- **痛点**：Telegram 设备绑定流程缺乏明确的失败原因提示，用户无法判断是配置缺失还是工具未就绪（`#7853`、`#7862`）；UI 错误提示累积不刷新影响调试体验（`#7297`）；早期建议生成因无法读取用户实际数据而缺乏针对性（已修复）。
- **满意点**：Onboarding 建议流端到端跑通后，连接→建议→线程闭环体验显著提升（`#7815`）；WebUI 共享原语落地后页面加载态与滚动行为趋于一致（`#7792`、`#7794`）。
- **使用场景**：开发者更关注 CI 构建速度与环境一致性（Rust toolchain 集中化获支持）；企业用户期望 GSuite 能力从“接口映射”升级为“原生 CLI 优先”架构（`#7849`）。

## 8. 待处理积压
- [#7297](https://github.com/nearai/ironclaw/issues/7297) — UI 错误消息堆叠问题（Open since 2026-08-06，2 评论）
- [#7856](https://github.com/nearai/ironclaw/issues/7856) — MCP camelCase 工具名静默跳过（Open since 2026-08-24，0 评论）


</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 — 2026-08-25

## 1. 今日速览

过去24小时项目活跃度**中等偏高**：3条 Issue 全部关闭，11条 PR 中10条已合并，整体维护响应效率良好。核心贡献集中在 renderer 层（缩略图渲染、文件交互、插件安装体验）及性能优化（SQLite 写入放大修复）。无新版本发布，但 #1277 的 Electron 大版本升级（v40→v43）尚未合并，是下一版本上线的关键前置条件。项目整体健康度良好，维护者对 stale issue 的清理及时。

## 2. 版本发布

无新版本发布。

> **关注点**：PR #1277 待合并，涉及 Electron 40.2.1 → 43.4.1 大版本升级，合并后可能影响打包配置与原生模块兼容性，建议纳入下一版本 release note。  
> [PR #1277](https://github.com/netease-youdao/LobsterAI/pull/1277)

## 3. 项目进展

今日合并的 PR 按贡献维度分类：

| PR | 类型 | 核心内容 |
|---|---|---|
| #2524 | 功能 | 跨平台缩略图渲染器，支持图片/视频/PDF/Office/HTML，统一 16:9 尺寸与缓存策略 |
| #2522 | 功能 | 文件分享保留 Unicode 文件名，优化收藏状态即时更新与失败回滚 |
| #2520 | 修复 | 插件安装模态框支持独立滚动，防止长错误信息遮挡操作按钮 |
| #2521 | 修复 | 协作文本选择菜单行为修复，防止右键菜单触发前清空中选择 |
| #1193 | 性能 | 消除 SQLite 全量序列化写入，改用 debounce + batch transaction 大幅降低 I/O 放大 |
| #2527 | 修复 | 技能面板 tab 持久化 bug，重置默认到 marketplace |
| #2528 | 功能 | credits loading settings UI |
| #2523 / #2525 / #2526 | 小改 | IM 图标、登录指南、kits 图标 URL 更新 |

**整体评价**：今日开发节奏围绕**文件/媒体体验**与**性能优化**展开，#1193 的 SQLite 优化对高写入场景（如大规模聊天记录存储）有显著收益。项目向前推进了 artifact 渲染与本地存储两个核心体验面。

## 4. 社区热点

| Issue/PR | 热度 | 用户诉求 |
|---|---|---|
| [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) | 👍 1，3 评论 | 希望支持配置上下文窗口大小与输出 token 上限，解决 deepseek 模型 Context overflow 报错 |
| [#1195](https://github.com/netease-youdao/LobsterAI/issues/1195) | 3 评论 | 自建 skill 被错误安装到 OpenClaw 目录，重启后不显示，必现 bug |
| [#1192](https://github.com/netease-youdao/LobsterAI/issues/1192) | 2 评论 | 希望允许直接写死已有工具（如 browser）的默认参数，替代不可靠的 LLM 指令跟随 |

**分析**：三个 issue 均已被关闭（stale 处理），但诉求本身仍具代表性——#1187 反映用户对模型配置精细化的需求；#1195 是路径管理机制的潜在缺陷；#1192 暴露了 LLM 工具调用不稳定时的用户 workaround 诉求。建议维护者关注是否已有对应 fix PR。

## 5. Bug 与稳定性

| Issue | 严重度 | 状态 | Fix PR |
|---|---|---|---|
| [#1195](https://github.com/netease-youdao/LobsterAI/issues/1195) 自建 skill 安装路径错误 | 中 | 已关闭（stale） | 未见明确关联 PR |
| [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) 上下文窗口溢出无配置入口 | 低 | 已关闭（stale） | 未见明确关联 PR |

> 今日无新增崩溃或回归报告。PR #2520 和 #2521 修复了两处潜在的 UX 级 bug（插件安装遮挡、文本选择丢失），属于体验修复范畴。

## 6. 功能请求与路线图信号

| 诉求 | 来源 | 匹配信号 |
|---|---|---|
| 模型上下文/输出 token 配置 | #1187 | 无对应 PR，建议纳入 roadmap 评估 |
| 工具默认参数固化 | #1192 | 无对应 PR，可参考 skill/config 机制扩展 |
| 跨平台缩略图支持（图片/视频/PDF/Office） | PR #2524 | **已落地**，覆盖多格式渲染 |
| 文件分享 Unicode 兼容 | PR #2522 | **已落地**，修复历史文件名乱码 |
| Electron 升级 | PR #1277 | **待合并**，v43 是 LTS 长期维护版本 |

**判断**：缩略图与文件交互已是当前迭代重点，SQLite 性能优化（#1193）暗示数据层重构正在进行。用户配置类诉求暂无 PR 覆盖，可作为下阶段功能候选。

## 7. 用户反馈摘要

- **痛点 1**：deepseek 等模型运行时报 Context overflow，用户缺乏手动调整上下文窗口的手段，只能被迫 `/reset` 或切换模型。  
  （来源：#1187）

- **痛点 2**：通过 agent 创建的自定义 skill 被安装到 OpenClaw 目录下，LobsterAI 技能面板不识别，用户感知为"安装成功但不可用"，信任度受损。  
  （来源：#1195）

- **痛点 3**：browser 工具每次弹窗口打扰用户，LLM 记忆指令跟随不稳定，用户希望直接配置无头模式等默认参数。  
  （来源：#1192）

- **满意点**：PR #2524 提供的多格式缩略图支持、#2522 的分享/收藏体验优化，均针对高频使用场景，预期用户反馈积极。

## 8. 待处理积压

| Item | 类型 | 创建时间 | 风险 |
|---|---|---|---|
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) Electron v40→v43 升级 | PR（待合并） | 2026-04-02 | 合并后可消除 4.5 个月的依赖滞后，但未合并期间无法享受 v43 安全补丁 |
| [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) 上下文窗口配置 | Issue（stale 关闭） | 2026-04-01 | 功能诉求明确，暂无 PR 跟进，需维护者决策是否受理 |
| [#1195](https://github.com/netease-youdao/LobsterAI/issues/1195) skill 安装路径 bug | Issue（stale 关闭） | 2026-04-01 | 必现 bug，关闭后用户可能重新打开，建议关联 fix PR |

---

**项目健康度评分：🟢 良好**  
- 维护响应：Issue/PR 清理及时  
- 合并效率：10/11 PR 已合并（91%）  
- 风险点：Electron 大版本升级长期未合并、两个 stale issue 中的 bug/诉求未被实质性解决

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-08-25

---

## 1. 今日速览

今日 Moltis 项目呈现**高活跃度**状态：24 小时内完成 7 个 PR 合并、2 个 Issue 关闭，并发布了 `20260824.01` 新版本。贡献者分布较广（SP-937-215、penso、rubenssoto、IlyaBizyaev、tsauvajon），覆盖 Provider 接入、沙箱稳定性、心跳调度、安全加固等多个方向。整体健康度良好，维护者响应及时。

---

## 2. 版本发布

### `20260824.01`

今日发布新版本，包含当日合并的 7 个 PR 修复与功能更新。建议用户尽快升级，尤其是涉及 Apple Container 标识符越界、Coqui TTS 误报以及网关签名验证安全的修复。

---

## 3. 项目进展

今日合并的 PR 按功能模块归类如下：

### 新增功能
- **xAI Grok Subscription OAuth** — PR [#1240](https://github.com/moltis-org/moltis/pull/1240) | 关联 Issue [#1239](https://github.com/moltis-org/moltis/issues/1239)
  - 新增 `xai-oauth` Provider，支持 SuperGrok / X Premium+ 用户通过 RFC 8628 Device Code 登录，无需 `XAI_API_KEY` 即可调用 Grok，已有的 API Key Provider 保持不变作为 fallback。
- **Coder 远程工作空间沙箱** — PR [#1199](https://github.com/moltis-org/moltis/pull/1199)（待合并）
  - 通过 REST API 创建临时工作空间，支持模板 ID/名称、Presets、TTL、环境变量别名等功能，为容器化开发提供新后端。

### 安全与稳定性修复
- **网关节点配对签名验证** — PR [#1179](https://github.com/moltis-org/moltis/pull/1179)
  - 绑定 `node.pair.verify` 到服务端下发的待处理请求，防止调用方伪造密钥或挑战，加固节点配对安全性。
- **Apple Container 标识符越界修复** — PR [#1237](https://github.com/moltis-org/moltis/pull/1237) | 关联 Issue [#1137](https://github.com/moltis-org/moltis/issues/1137)
  - 将标识符限制在 64 字符以内，使用 SHA-256 后缀保证稳定性，修复容器启动失败问题。
- **心跳 `active_hours` 强制生效** — PR [#1241](https://github.com/moltis-org/moltis/pull/1241)
  - 修复 `end = "24:00"` 被 `chrono` 拒绝导致时间判断失效的问题，同时补全了此前未被调用的执行路径。

### 工具与渠道修复
- **TTS Coqui 误报消除** — PR [#1242](https://github.com/moltis-org/moltis/pull/1242)
  - 修正默认 Coqui 端点被错误标记为 `configured=true` 的问题，防止无 TTS 配置时出现红色警告。
- **OpenAI 严格 Schema 兼容** — PR [#1232](https://github.com/moltis-org/moltis/pull/1232)（待合并）
  - 修复 OpenAI strict tool schema 下 `additionalProperties=false` 导致 Codex 返回 null/空值的问题。
- **Cron 对话上下文保留** — PR [#1243](https://github.com/moltis-org/moltis/pull/1243)（待合并）
  - 修复定时消息在 WhatsApp 等渠道发送后，后续追问丢失上下文的问题，将已交付文本追加为 assistant 消息。
- **共享 Slack 频道工具访问** — PR [#1238](https://github.com/moltis-org/moltis/pull/1238)
  - 持久化并暴露 `untrusted_audience` / `untrusted_tools` 配置，允许基于策略显式授权工具访问，默认仍保持 fail-closed。

---

## 4. 社区热点

| 条目 | 类型 | 评论 | 👍 | 动态 |
|------|------|------|-----|------|
| [#1239](https://github.com/moltis-org/moltis/issues/1239) xAI Grok OAuth | Issue | 2 | 0 | 创建当日即被关闭（已合并至 PR #1240）|
| [#1137](https://github.com/moltis-org/moltis/issues/1137) Apple Container ID 越界 | Issue | 1 | 0 | 6 月创建，8 月 24 日通过 PR #1237 修复后关闭 |

**热点分析：**
- **xAI Grok OAuth** 诉求明确：用户希望绕过 API Key 模式，以订阅身份接入 Grok，与已有的 OpenAI Codex OAuth 体验对齐。该功能已快速实现并合并。
- **Apple Container 标识符问题** 属于历史遗留 Bug，从创建到修复历时近 2 个月，反映容器平台在命名规则上的边界处理需要更严格的单元测试覆盖。

---

## 5. Bug 与稳定性

| 严重程度 | 问题 | 状态 | 关联 PR |
|----------|------|------|---------|
| 🔴 高 | Apple Container ID 越界导致启动失败 | ✅ 已修复 | [#1237](https://github.com/moltis-org/moltis/pull/1237) |
| 🟡 中 | 网关节点配对可被伪造签名（安全漏洞） | ✅ 已修复 | [#1179](https://github.com/moltis-org/moltis/pull/1179) |
| 🟡 中 | `active_hours` 配置 `end=24:00` 被解析为非法值 | ✅ 已修复 | [#1241](https://github.com/moltis-org/moltis/pull/1241) |
| 🟡 中 | 无 TTS 配置时误报 `provider 'coqui' not configured` | ✅ 已修复 | [#1242](https://github.com/moltis-org/moltis/pull/1242) |
| 🟠 低 | OpenAI strict schema 下 patch/map 字段丢失数据 | 🔄 待合并 | [#1232](https://github.com/moltis-org/moltis/pull/1232) |
| 🟠 低 | Cron 定时消息后续追问丢失渠道上下文 | 🔄 待合并 | [#1243](https://github.com/moltis-org/moltis/pull/1243) |

> 共 6 个已知问题，4 个今日已修复，2 个待合并。今日修复集中爆发，整体稳定性显著提升。

---

## 6. 功能请求与路线图信号

| 需求 | 状态 | 信号强度 |
|------|------|----------|
| xAI Grok 订阅 OAuth 接入 | ✅ 已合并 | ⭐⭐⭐ 强信号 |
| Coder 远程工作空间沙箱后端 | 🔄 PR #1199 待合并 | ⭐⭐ 中信号（多参数支持说明需求成熟） |
| Slack 共享频道工具策略化授权 | ✅ 已合并 | ⭐⭐ 中信号 |
| WhatsApp 流式传输期间媒体下载限制 | ✅ 已合并（PR #1233） | ⭐ 低（已自动解决） |
| Cron 定时消息上下文延续 | 🔄 PR #1243 待合并 | ⭐⭐ 中信号 |

**判断：** xAI Grok OAuth 与 Coder 沙箱是近期最值得关注的两个方向，前者扩展了 Provider 生态，后者扩展了执行环境生态，均符合 Moltis 作为多通道 AI 助手平台的产品定位。

---

## 7. 用户反馈摘要

- **xAI 用户群体**：希望在不配置 API Key 的前提下，利用已有 Grok 订阅直接使用 Moltis，降低接入门槛。（Issue [#1239](https://github.com/moltis-org/moltis/issues/1239)）
- **Apple 容器用户**：身份限定前缀 + UUID 组合超出 64 字符限制，导致容器启动失败，影响生产环境稳定性。（Issue [#1137](https://github.com/moltis-org/moltis/issues/1137)）
- **TTS 配置用户**：未配置任何 TTS 服务时仍收到红色警告，误导用户以为存在配置错误。（PR [#1242](https://github.com/moltis-org/moltis/pull/1242) 修复）
- **安全敏感用户**：关注节点配对的安全性，要求防止签名伪造，体现企业对 Moltis 生产部署的合规要求。（PR [#1179](https://github.com/moltis-org/moltis/pull/1179) 修复）
- **WhatsApp 企业用户**：流式场景下需要限制媒体下载频率，避免带宽滥用。（PR [#1233](https://github.com/moltis-org/moltis/pull/1233) 修复）

---

## 8. 待处理积压

| 条目 | 类型 | 创建时间 | 备注 |
|------|------|----------|------|
| [#1199](https://github.com/moltis-org/moltis/pull/1199) Coder 沙箱支持 | PR | 2026-08-15 | 已开放 10 天，待合并，功能完整 |
| [#1232](https://github.com/moltis-org/moltis/pull/1232) OpenAI 严格 Schema 修复 | PR | 2026-08-22 | 已开放 3 天 |
| [#1243](https://github.com/moltis-org/moltis/pull/1243) Cron 上下文保留 | PR | 2026-08-24 | 刚提交，待评审 |

> **建议维护者关注：** PR #1199（Coder 沙箱）已开放 10 天，功能完整度较高，建议尽快完成合并评审，以推进多执行环境支持。

---

**总结：** 今日 Moltis 项目活跃度较高，安全修复与功能扩展并重，4 个 Bug 当日闭环，整体健康度良好。3 个待合并 PR 如能尽快完成评审，将为下一版本提供显著价值。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目日报 | 2026-08-25

## 1. 今日速览

CoPaw 项目在过去24小时保持高活跃度，共处理 **50 条 Issues**（32 条新开/活跃、18 条关闭）和 **48 条 PR**（22 条待合并、26 条已合并/关闭），社区贡献节奏稳定。发布了 **v2.1.1-beta.2** 版本，主要修复 Console 和视频工具调用问题。社区反馈集中在多智能体协作体验、MCP 连接稳定性、内存泄漏及会话管理 Bug 等方面，项目整体处于快速迭代期，活跃度处于健康水平。

---

## 2. 版本发布

### v2.1.1-beta.2
**链接**: [PR #7161](https://github.com/agentscope-ai/QwenPaw/pull/7161) / [PR #7061](https://github.com/agentscope-ai/QwenPaw/pull/7061)

**更新内容**:
- `feat(console)`: 在 Assistant 响应卡片中添加 Artifacts 支持，提升代码/文件展示体验
- `fix(video)`: 修复 OpenAI Responses API 下 tool-result 视频无法正确投递的问题

**破坏性变更**: 无

**迁移注意事项**: 无，此为 beta 补丁版本，不影响现有配置。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（26 条）

| PR | 类型 | 内容 | 作者 |
|----|------|------|------|
| [#7234](https://github.com/agentscope-ai/QwenPaw/pull/7234) | fix(memory) | 恢复 ReMe 索引定期压缩任务，修复内存中过期 BM25 条目累积问题 | rayrayraykk |
| [#7248](https://github.com/agentscope-ai/QwenPaw/pull/7248) | fix(ci) | Docker 构建从 `__version__.py` 动态推导版本号，消除硬编码 | rayrayraykk |
| [#7247](https://github.com/agentscope-ai/QwenPaw/pull/7247) | fix(providers) | 停止向 SiliconFlow DeepSeek V4 发送媒体内容，修复多模态能力误判 | rayrayraykk |
| [#7173](https://github.com/agentscope-ai/QwenPaw/pull/7173) | fix(e2e) | 修复因后端列新增导致的 E2E 测试选择器偏移 | yutai78786 |
| [#7209](https://github.com/agentscope-ai/QwenPaw/pull/7209) | fix(e2e) | 修复 Console 重构后的 E2E 测试用例 | yutai78786 |
| [#6067](https://github.com/agentscope-ai/QwenPaw/pull/6067) | feat | 扩展敏感文件检测规则，支持全局读取权限 | weidankong |

**整体进展**: 本日合并重点集中在**内存管理优化**（ReMe 索引压缩）、**CI/CD 稳定性**（Docker 版本推导）、**Provider 兼容性修复**（SiliconFlow），以及 **E2E 测试覆盖补强**。项目正逐步收敛 v2.1.x 系列的稳定性问题。

---

## 4. 社区热点

### 高讨论 Issues（评论数 Top 5）

1. **#6921** [OPEN] [bug] 多步骤任务执行中模型自行停止，需用户手动输入"继续"才能推进
   - 评论: 11 | 作者: rerbin | [链接](https://github.com/agentscope-ai/QwenPaw/issues/6921)
   - **热点分析**: 用户反馈模型在规划完成后未自动执行下一步，导致交互断层。这是多步骤任务可靠性的核心痛点，影响生产环境使用信心。

2. **#6782** [CLOSED] [bug] Docker 版本插件/应用市场始终提示"维护中"
   - 评论: 9 | 作者: Sakura7301 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/6782)
   - **热点分析**: Docker 部署用户普遍遇到市场功能异常，已关闭但可能涉及配置或网络问题，需关注是否彻底解决。

3. **#338** [OPEN] [enhancement] 建议添加 Webhook 功能
   - 评论: 8 | 作者: xiaobai08888 | 👍: 1 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/338)
   - **热点分析**: 用户希望实现 CoPaw 与外部系统的异步交互，这是企业集成场景的常见需求。

4. **#7011** [OPEN] [bug] Console 停止请求可跨 UI 会话取消活跃的飞书会话
   - 评论: 8 | 作者: djj532 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/7011)
   - **热点分析**: 会话隔离机制存在缺陷，多会话并发场景下操作边界模糊，属严重 UX Bug。

5. **#3224** [OPEN] [enhancement] 自然语言驱动的自进化多智能体协作团队
   - 评论: 7 | 作者: watsonagenda | [链接](https://github.com/agentscope-ai/QwenPaw/issues/3224)
   - **热点分析**: 用户提出从"手动挡"到"自动挡"的多智能体协作愿景，符合 Agent Teams 长期发展方向。

---

## 5. Bug 与稳定性

| 严重度 | Issue | 标题 | 链接 | 状态 | Fix PR |
|--------|-------|------|------|------|--------|
| 🔴 高 | #6921 | 多步骤任务执行中模型自行停止 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/6921) | OPEN | — |
| 🔴 高 | #7011 | Console 停止请求跨会话取消飞书会话 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/7011) | OPEN | — |
| 🔴 高 | #7231 | 并发会话中消息可能路由到错误会话 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/7231) | OPEN | [PR #7237](https://github.com/agentscope-ai/QwenPaw/pull/7237) |
| 🟠 中 | #6524 | MCP 后端重启后客户端无法自动恢复 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/6524) | OPEN | — |
| 🟠 中 | #7222 | 长运行 qwenpaw-backend 内存增长至 20GB+ | [链接](https://github.com/agentscope-ai/QwenPaw/issues/7222) | OPEN | — |
| 🟠 中 | #5720 | v1.1.12.post2 内存泄漏（64分钟后涨至580MB） | [链接](https://github.com/agentscope-ai/QwenPaw/issues/5720) | OPEN | — |
| 🟡 低 | #7199 | daily_paper 处理含代理字符 PDF 时崩溃 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/7199) | OPEN | — |
| 🟡 低 | #7242 | Dashboard 加载耗时 6 分钟+ | [链接](https://github.com/agentscope-ai/QwenPaw/issues/7242) | OPEN | — |
| 🟡 低 | #7210 | 工具在 agent.json 已启用但会话 schema 未注入 | [链接](https://github.com/agentscope-ai/QwenPaw/issues/7210) | OPEN | — |

**关键进展**: 
- **#7231** 已有修复 PR [#7237](https://github.com/agentscope-ai/QwenPaw/pull/7237)（冻结会话身份防止路由错乱）
- **#6822**（MCP 瞬态连接失败导致会话永久阻塞）仍待解决
- 内存泄漏问题（#7222、#5720）持续存在，#7234 已恢复索引压缩但运行时累积问题仍未根除

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 优先级信号 | 关联 PR |
|----------|----------|------------|---------|
| #3224 | 自然语言驱动的自进化多智能体团队 | 🟢 高（讨论活跃） | — |
| #7182 / [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | Workspace-scoped Skill preload 策略 | 🟢 高（已有 PR） | [PR #7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) |
| #7085 | 按频道独立配置模型 | 🟡 中 | — |
| #5563 | 多步骤回复消息聚合，避免刷屏 | 🟡 中 | — |
| #7219 | Token Usage 页面增加全 Agent LLM/工具调用趋势图 | 🟡 中 | [PR #7219](https://github.com/agentscope-ai/QwenPaw/pull/7219) |
| #6960 | 从 Codex/Qoder 导入配置的工作流 | 🟡 中 | [PR #6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) |
| #7080 | PowerContext 可选长期记忆后端 | 🟡 中 | [PR #7080](https://github.com/agentscope-ai/QwenPaw/pull/7080) |
| #6399 | ReMeLightMemoryCard 添加 Reranker UI 配置面板 | 🟡 中 | [PR #6399](https://github.com/agentscope-ai/QwenPaw/pull/6399) |
| #7198 | 审批模式优化：过程产物不应触发审批 | 🟡 中 | — |

**路线图判断**:
- **Skill 预加载策略**（#7183）和 **Token 使用趋势图**（#7219）已有 PR 进入 Review，可能纳入 v2.1.1 或 v2.1.2
- **多智能体协作体验**（#3224、#2420、#3013）是社区高频诉求，建议优先排期
- **按频道配置模型**（#7085）和**消息聚合**（#5563）属于体验优化，可能进入 v2.2.0

---

## 7. 用户反馈摘要

### 痛点
1. **多步骤任务执行不可靠**: #6921 反映模型常在"规划完毕"后停止，需人工干预"继续"，影响自动化信心
2. **会话隔离缺陷**: #7011 和 #7231 暴露并发场景下消息路由和会话边界问题，可能导致数据错乱
3. **内存泄漏持续**: #7222（20GB+ 增长）和 #5720（64分钟泄漏）表明运行时内存管理仍有漏洞
4. **MCP 连接脆弱**: #6524 和 #6822 反映远程 MCP 服务重启后客户端恢复机制不完善
5. **多智能体协作体验割裂**: #6925、#2420、#3013 用户反映跨 Agent 通信需手动切换、会话不连贯

### 满意点
1. **Console UI 重构** 获得正面反馈，但 E2E 测试需同步修复
2. **市场/插件功能** 受到关注，但 Docker 环境存在可用性差异
3. **记忆压缩阈值可调** 被用户认可（#7230 用户主动调整配置改善体验）

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 标题 | 创建时间 | 评论数 | 建议优先级 |
|-------|------|----------|--------|------------|
| #6724 / [#6874](https://github.com/agentscope-ai/QwenPaw/pull/6874) | MCP 工具调用超时配置 | 2026-08-10 | — | 🟢 高（已有 PR 待合并） |
| #7053 / [#7066](https://github.com/agentscope-ai/QwenPaw/pull/7066) | OAuth2 refresh_token 旋转后未持久化 | 2026-08-16 | — | 🟢 高（已有 PR Under Review） |
| #6504 / #6880 | Console/Marketplace 重构配套 | 2026 | — | 🟡 中（E2E 修复中） |

### 建议维护者关注
1. **#6921**（模型停止执行）和 **#7011**（跨会话操作干扰）是影响用户体验的核心 Bug，建议优先分配资源
2. **#7222**（长运行内存累积）与 **#5720**（早期版本泄漏）需系统性排查，可考虑引入内存 profiling 工具
3. **#3224**（自进化多智能体团队）是战略级需求，建议评估是否纳入 v2.2.0 路线图

---

**报告生成时间**: 2026-08-25  
**数据来源**: CoPaw GitHub Repository (agentscope-ai/QwenPaw)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



### ZeptoClaw 项目动态日报 (2026-08-25)

**1. 今日速览**
过去24小时 ZeptoClaw 项目整体活跃度处于低位，仅有 1 条新 Issue 提交，无 PR 合并记录与新版本发布。当前阶段无阻塞性开发或重大功能推进，维护重心偏向 CLI 交互层的体验加固。项目整体健康度良好，代码库处于稳定等待状态，社区反馈节奏平缓。

**2. 版本发布**
无。

**3. 项目进展**
今日无 PR 合并或关闭记录。项目未进行核心功能迭代或架构调整，代码库处于静默期，暂无实质性向前推进。

**4. 社区热点**
今日唯一讨论焦点为 Issue [#650](https://github.com/qhkm/zeptoclaw/issues/650) `feat(cli): REPL UX hardening - safe Ctrl+C/Ctrl+D, lone '/' command table`。该 Issue 评论与 👍 数均为 0，处于早期反馈阶段。背后的核心诉求是提升交互式终端的容错率，解决高频误操作导致的会话中断与边缘命令提示缺失问题。

**5. Bug 与稳定性**
无崩溃或严重回归报告。Issue [#650](https://github.com/qhkm/zeptoclaw/issues/650) 指出两处 UX 稳定性缺陷：
- 任意 `Ctrl+C` / `Ctrl+D` 均触发静默退出，缺乏上下文感知，易造成未完成会话丢失。
- 单独输入 `/` 落入未知命令分支，而非触发命令帮助表，影响探索性使用。
目前暂无对应 Fix PR。

**6. 功能请求与路线图信号**
Issue [#650](https://github.com/qhkm/zeptoclaw/issues/650) 标记为 `feat(cli)`，明确指向 REPL 信号处理与命令路由的优化。结合其内容可判断，ZeptoClaw 的近期路线图将优先纳入：
- 可配置的中断信号逻辑（软退出/保留上下文）
- 空白或符号输入的自动补全与帮助表映射
此类打磨型特性通常会在 Agent 核心管道稳定后纳入 `v1.x` minor 更新，建议关注后续 PR 提交。

**7. 用户反馈摘要**
来自 Issue [#650](https://github.com/qhkm/zeptoclaw/issues/650) 的反馈提炼：
- **痛点**：REPL 缺乏安全中断机制，误触退出键直接销毁工作流；边缘输入的错误提示不够直观。
- **使用场景**：频繁在终端试错命令、依赖快捷键快速中断/恢复任务的用户。
- **满意度倾向**：基础功能可用，但交互细节粗糙，用户期待更接近成熟 CLI 工具（如 `kubectl`、`tmux`）的容错设计。

**8. 待处理积压**
Issue [#650](https://github.com/qhkm/zeptoclaw/issues/650) 自 2026-08-24 创建以来尚无维护者回复或 PR 跟进。虽属轻量级 UX 改进，但建议 maintainer 尽快标注优先级或认领，避免社区反馈沉默累积。当前无长期未处理的重大积压项。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-08-25

---

## 1. 今日速览

过去24小时 ZeroClaw 仓库保持高强度活跃：新增 Issues 50条（活跃43、关闭7）、Pull Requests 50条（待合并45、已合并/关闭5），无新版本发布。今日讨论重心聚焦于**协议扩展**（OpenAI Chat Completions RFC #8603 持续发酵，24条评论）与**安全治理**（delegate bypass 风险命令的 S0 级漏洞修复进行中）。项目整体健康度良好，维护者决策队列（#8692）与 session 持久化所有权追踪（#9600）显示架构治理正在系统化推进，但安全相关 issue 密度偏高，需关注。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

今日已关闭/合并的主要工作：

| 编号 | 类型 | 内容 | 链接 |
|------|------|------|------|
| #10251 | Bug/Test | Telegram `listen_*` 并行测试因固定墙钟超时而失败的问题已关闭（回归修复） | [PR #10251](https://github.com/zeroclaw-labs/zeroclaw/issues/10251) |
| #9590 | Bug | 并发 `models refresh` 丢失缓存条目的竞态条件已关闭 | [Issue #9590](https://github.com/zeroclaw-labs/zeroclaw/issues/9590) |
| #10106 | Bug | 精确代理选择器拒绝支持服务的问题已关闭 | [Issue #10106](https://github.com/zeroclaw-labs/zeroclaw/issues/10106) |
| #10143 | Task | Provider 调用会计生命周期补全任务已关闭（PR #10003 收尾） | [Issue #10143](https://github.com/zeroclaw-labs/zeroclaw/issues/10143) |
| #10224 | Bug | 自定义 provider 5xx 错误以重复转义 JSON 格式记录的问题已关闭 | [Issue #10224](https://github.com/zeroclaw-labs/zeroclaw/issues/10224) |
| #10190 | Bug | Reasoning fallback 分类器匹配无关错误子句的问题已关闭 | [Issue #10190](https://github.com/zeroclaw-labs/zeroclaw/issues/10190) |

**进展评估：** 今日关闭的 7 个 issue 中 5 个为 bug 修复，2 个为 task 收尾，主要集中在**可观测性、provider 可靠性、测试稳定性**三个维度。主分支推进稳健，但尚无里程碑级新功能合入。

---

## 4. 社区热点

| 排名 | Issue/PR | 评论数 | 核心议题 | 链接 |
|------|----------|--------|----------|------|
| 1 | #8603 | 24 | RFC: Chat Completions 协议适配 | [Issue #8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) |
| 2 | #8692 | 14 | Maintainer RFC 决策队列追踪 | [Issue #8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| 3 | #9600 | 11 | Session 持久化所有权与层序追踪 | [Issue #9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) |
| 4 | #7431 | 6 | Pre-turn 工具提示自然语言路由 | [Issue #7431](https://github.com/zeroclaw-labs/zeroclaw/issues/7431) |
| 5 | #9512 | 5 | CI gate 问题溯源标注规范 | [Issue #9512](https://github.com/zeroclaw-labs/zeroclaw/issues/9512) |
| 6 | #9363 | 4 | 配置元数据非英文本地化缺失 | [Issue #9363](https://github.com/zeroclaw-labs/zeroclaw/issues/9363) |
| 7 | #7759 | 4 | Gateway WebSocket 与 agent turn 生命周期解耦 | [Issue #7759](https://github.com/zeroclaw-labs/zeroclaw/issues/7759) |

**热点分析：**
- **#8603** 是当前最高关注度的 RFC，目标是让 ZeroClaw 原生支持 OpenAI Chat Completions 协议，对接 Open WebUI、LobeChat、Continue.dev、Aider、LangChain 等生态。相关 PR #8486 已进入实现阶段。
- **#8692 / #9600** 反映维护者对**架构治理**的系统化需求：RFC 决策队列与 session 持久化所有权归属正在被明确界定，避免多 workstream 并行冲突。
- **#7431** 提出在 LLM 调用前插入轻量意图提取步骤，改善 `send_via` 路由的隐式调用体验。

---

## 5. Bug 与稳定性

### S0 — 数据丢失/安全风险

| Issue | 描述 | 状态 | 修复 PR |
|-------|------|------|---------|
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | Independent delegate 绕过 `block_high_risk_commands` 策略 | In Progress | — |
| [#10324](https://github.com/zeroclaw-labs/zeroclaw/issues/10324) | Cron 手动触发与 run-history 在 agent 重命名窗口存在 check-then-act 竞态 | Open | — |

### S1 — 高严重性

无今日新增 S1 issue。

### S2 — 功能降级

| Issue | 描述 | 状态 | 修复 PR |
|-------|------|------|---------|
| [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | 交互式 agent 会话 context 硬编码限制 32k tokens，忽略 `max_context_tokens` 配置 | In Progress | — |
| [#9812](https://github.com/zeroclaw-labs/zeroclaw/issues/9812) | Provider fallback 携带 primary model id 导致 fallback 永不触发 | Open (needs repro) | — |
| [#9820](https://github.com/zeroclaw-labs/zeroclaw/issues/9820) | Calculator tool 在 NVIDIA NIM 模型上输出 literal `<TOOLCALL>` 而非真实函数调用 | Open | — |
| [#10023](https://github.com/zeroclaw-labs/zeroclaw/issues/10023) | Pinned fallback provider 失败日志记录请求模型而非实际服务模型 | Closed | — |
| [#9363](https://github.com/zeroclaw-labs/zeroclaw/issues/9363) | 配置元数据在非英语 locale 下仍显示英文 | Open | — |

### S3 — 轻微问题

| Issue | 描述 | 状态 |
|-------|------|------|
| [#10180](https://github.com/zeroclaw-labs/zeroclaw/issues/10180) | ZeroCode 粘贴事件绕过输入所有权检查，突变隐藏 composer | Open |
| [#10178](https://github.com/zeroclaw-labs/zeroclaw/issues/10178) | Daemon socket 所有权错误未提供可操作的恢复路径 | Open |
| [#10175](https://github.com/zeroclaw-labs/zeroclaw/issues/10175) | Google TTS API Key 头部未标记为敏感 | Open |

**稳定性评估：** 今日新增 2 个 S0 级安全问题 + 3 个 S2 级功能缺陷，安全与可靠性压力较大。#10165（delegate bypass）与 #10324（cron 竞态）需优先处理。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 诉求摘要 | 纳入下一版本可能性 |
|----------|------|----------|-------------------|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) + [#8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486) | RFC/Feature | OpenAI Chat Completions 端点适配 | **高** — PR 已实现，等待 RFC 接受 |
| [#9986](https://github.com/zeroclaw-labs/zeroclaw/pull/9986) | Feature | `zeroclaw agents export` 可移植 bundle | **高** — PR 已提交，size:XL 但功能完整 |
| [#7431](https://github.com/zeroclaw-labs/zeroclaw/issues/7431) | Enhancement | Pre-turn 意图提取与路由 | **中** — 设计阶段，需进一步 RFC |
| [#10222](https://github.com/zeroclaw-labs/zeroclaw/issues/10222) | RFC | Opt-in single-tool provider rounds | **中** — 首次提出，需 maintainer 评审 |
| [#9324](https://github.com/zeroclaw-labs/zeroclaw/pull/9324) | Feature | A2A outbound client 配置与工具 | **中** — Phase 1 已实现，等待 review 轮次 |
| [#9582](https://github.com/zeroclaw-labs/zeroclaw/pull/9582) | Feature | Plugin WASI:HTTP egress policy | **中** — Stage 2，需 ADR-014 决策支持 |

**路线图信号：** 项目当前聚焦于**协议兼容性**（OpenAI Chat Completions、A2A）、**可移植性**（agent bundle export）与**安全治理**（plugin egress policy、browser automation opt-in）。`#9830`（浏览器自动化改为 opt-in）与 `#9977`（文件系统变更 confine 到 workspace）反映安全收紧趋势。

---

## 7. 用户反馈摘要

| 主题 | 来源 | 痛点/场景 |
|------|------|-----------|
| Chat Completions 协议缺失 | #8603 | Open WebUI、Aider、LangChain 等主流工具无法直连 ZeroClaw，被迫使用 WebSocket 适配层 |
| Fallback provider 配置失效 | #9812 | 用户配置 `groq.main` fallback 到 `gemini.main`，但因 model id 携带错误导致 fallback 永不触发，且被错误进入 cooldown |
| 交互式会话 context 限制 | #10068 | 用户配置 `max_context_tokens = 131072`，但实际被硬编码 32k 截断，导致长对话体验下降 |
| Provider 5xx 日志可读性差 | #10224 | 自定义 provider 错误被双重转义为 JSON 字符串，诊断困难 |
| Telegram 测试不稳定 | #10251 | CI 中 17 个 `listen_*` 测试因固定墙钟断言在负载环境下失败，实际代码无误 |
| 配置本地化不完整 | #9363 | 中文/其他 locale 下 ZeroCode TUI 与 web 面板的配置分组标题仍为英文 |
| 终端粘贴行为异常 | #10180 | ZeroCode Chat 中粘贴事件绕过输入所有权检查，导致 composer 状态混乱 |

---

## 8. 待处理积压

以下 issue/PR 已开放较长时间但尚未关闭或合并，建议维护者关注：

| 编号 | 类型 | 创建时间 | 状态 | 风险 | 链接 |
|------|------|----------|------|------|------|
| #7759 | Feature | 2026-06-16 | In Progress | 高 — WebSocket 断连导致 agent turn 取消影响用户体验 | [Issue #7759](https://github.com/zeroclaw-labs/zeroclaw/issues/7759) |
| #9812 | Bug | 2026-08-07 | Needs repro | 高 — fallback 机制核心缺陷 | [Issue #9812](https://github.com/zeroclaw-labs/zeroclaw/issues/9812) |
| #10165 | Bug | 2026-08-20 | In Progress | **S0** — delegate 绕过安全策略 | [Issue #10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) |
| #10324 | Bug | 2026-08-24 | Open | 高 — cron 竞态条件 | [Issue #10324](https://github.com/zeroclaw-labs/zeroclaw/issues/10324) |
| #8486 | Feature | 2026-06-29 | Open | 高 — Chat Completions 端点，阻塞生态对接 | [PR #8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486) |
| #9324 | Feature | 2026-07-24 | Open | 高 — A2A outbound client | [PR #9324](https://github.com/zeroclaw-labs/zeroclaw/pull/9324) |
| #9582 | Feature | 2026-07-31 | Open | 高 — Plugin egress policy Stage 2 | [PR #9582](https://github.com/zeroclaw-labs/zeroclaw/pull/9582) |
| #9986 | Feature | 2026-08-13 | Open | 中 — Agent export bundle | [PR #9986](https://github.com/zeroclaw-labs/zeroclaw/pull/9986) |
| #9830 | Bug | 2026-08-07 | Blocked | 高 — 浏览器自动化 opt-in 安全加固 | [PR #9830](https://github.com/zeroclaw-labs/zeroclaw/pull/9830) |

**积压评估：** 当前有 9 个高优先级 issue/PR 处于开放或阻塞状态，其中 **#10165（S0 安全漏洞）** 与 **#8486（Chat Completions 协议适配）** 应优先推进。PR #9830 与 #10241 标记为 `blocked`，需跟踪依赖项 #9574 的进展。

---

*报告生成时间：2026-08-25 | 数据来源：github.com/zeroclaw-labs/zeroclaw*

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*