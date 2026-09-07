# OpenClaw 生态日报 2026-09-07

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-07 04:04 UTC

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
**日期：2026-09-07**  
**数据来源：github.com/openclaw/openclaw**

---

## 1. 今日速览

OpenClaw 今日保持高强度开发节奏，过去24小时内共产生 **500条 Issue 更新**（新开/活跃 317 条，已关闭 183 条）和 **500条 PR 更新**（待合并 275 条，已合并/关闭 225 条），净增长约 25 条待处理 PR，表明开发流水线运转高效但积压仍在累积。无新版本发布，但多个 P0/P1 级 Bug 修复 PR 已提交，涉及 Windows 路径溢出、JSON 嵌套深度、子进程泄漏等核心稳定性问题。社区活跃度评估：**🟢 健康**，Issue 关闭率 36.6%，PR 合并率 45%，维护者响应及时。

---

## 2. 版本发布

**无新版本发布。**

当前最新稳定版本为 `2026.8.2`，Beta 渠道为 `2026.9.1-beta.1`。多个 Issue 报告了从 `2026.7.1-2` 升级至 `2026.8.x` 后的回归问题，建议用户暂缓升级直至相关修复合并。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 作者 | 说明 |
|---|---|---|---|
| [#140756](https://github.com/openclaw/openclaw/pull/140756) | refactor(macos) | steipete | 重构 macOS 连接窗口为标准设置窗口，统一 UI 规范 |
| [#140754](https://github.com/openclaw/openclaw/pull/140754) | refactor(media) | steipete | 简化远程附件文件名选择逻辑 |
| [#140750](https://github.com/openclaw/openclaw/pull/140750) | perf(meeting) | steipete | 移除会议回环关联的临时数据，减少内存占用 |
| [#140755](https://github.com/openclaw/openclaw/pull/140755) | refactor(skills) | steipete | 共享 Gateway skill 状态类型，消除 UI 与后端定义漂移 |
| [#140712](https://github.com/openclaw/openclaw/pull/140712) ✅ | refactor(subagents) | steipete | 统一 subagent 索引逻辑，合并重复的 latest-generation 选择 |
| [#140741](https://github.com/openclaw/openclaw/pull/140741) ✅ | refactor(memory-lancedb) | steipete | 重构 LanceDB embedding 测试，通过 requests 覆盖 fallback 路径 |
| [#140761](https://github.com/openclaw/openclaw/pull/140761) | refactor(channels) | steipete | 复用飞书/Synology Chat 的 setup 配置 patch helpers |
| [#140742](https://github.com/openclaw/openclaw/pull/140742) | refactor(logging) | steipete | 共享便携式脱敏模式，统一 Dashboard 与后端的 PEM 掩码逻辑 |
| [#140628](https://github.com/openclaw/openclaw/pull/140628) | fix(policy) | steipete | 对齐 Policy 插件工具目录与核心词汇表，修复策略查询不一致 |
| [#140760](https://github.com/openclaw/openclaw/pull/140760) | fix(daemon) | zenglingbiao | 原子化发布 Gateway 服务环境变量文件，防止写入中断导致 token 丢失 |
| [#140759](https://github.com/openclaw/openclaw/pull/140759) | fix(android) | steipete | 修复 Android 端流式回复时阅读位置丢失问题 |
| [#140758](https://github.com/openclaw/openclaw/pull/140758) | feat(workboard) | Leon-SK668 | Workboard 卡片支持文件附件，填补创建/编辑时无法交换文件的空白 |
| [#140339](https://github.com/openclaw/openclaw/pull/140339) | feat(update) | fuller-stack-dev | **重大功能**：集成检查点与中断更新恢复，需继续跟进 |
| [#140753](https://github.com/openclaw/openclaw/pull/140753) | fix(windows) | steipete | 修复 Windows 清理逻辑在子进程退出后仍尝试 target PID 的问题 |
| [#116108](https://github.com/openclaw/openclaw/pull/116108) | fix(config) | sasan1200 | 修复 `$include` 嵌套配置保存问题，`doctor --fix` 现在可正确写入拥有文件 |
| [#140696](https://github.com/openclaw/openclaw/pull/140696) | refactor(policy) | steipete | 共享 Docker bind 解析逻辑，修复 Windows 驱动器前缀差异 |
| [#140751](https://github.com/openclaw/openclaw/pull/140751) ✅ | fix(ci) | vincentkoc | 避免 iOS 截图 CI 重复编译 Watch simulator，加速构建 |
| [#140701](https://github.com/openclaw/openclaw/pull/140701) | refactor(infra) | steipete | 共享文件描述符 primitives，统一快照恢复/SQLite 发布/数据库验证的完整性检查 |
| [#140636](https://github.com/openclaw/openclaw/pull/140636) | refactor(codex) | steipete | Codex 复用核心 exec policy algebra，消除策略不一致风险 |
| [#137381](https://github.com/openclaw/openclaw/pull/137381) | fix(sessions) | jalehman | 修复 `sessions_yield` 清理时长期 transcript 暂时不可用的问题 |
| [#140689](https://github.com/openclaw/openclaw/pull/140689) | fix(code-mode) | roboclaw-bot | 修复 Code Mode 下分页文件解析和 handled error 细节丢失 |
| [#132503](https://github.com/openclaw/openclaw/pull/132503) | feat(macos) | Leon-SK668 | macOS exec 审批提示显示 sessionKey，区分同 agent 多 session |
| [#140653](https://github.com/openclaw/openclaw/pull/140653) | fix(xai) | shakkernerd | 修复 Grok subscription token 路由问题，避免错误调用 Console API |
| [#110840](https://github.com/openclaw/openclaw/pull/110840) | fix(codex) | nocodet888-arch | 修复 Codex tool echo 前缀 UTF-16 截断问题，防止 emoji 导致匹配失败 |
| [#129403](https://github.com/openclaw/openclaw/pull/129403) | fix(config) | xydigitLybnnnn | **P0 修复**：限制 JSON 嵌套深度，防止 deeply-nested 配置导致 CLI 栈溢出崩溃 |
| [#140739](https://github.com/openclaw/openclaw/pull/140739) ✅ | perf(ui) | steipete | 优化 Usage session 卡片指标计算，每渲染周期仅扫描一次 |
| [#137169](https://github.com/openclaw/openclaw/pull/137169) | fix(discord) | LiuwqGit | 修复 Discord system-agent 审批回调解析问题 |
| [#140635](https://github.com/openclaw/openclaw/pull/140635) | fix(channels) | jason-allen-oneal | 改进 Discord 策略阻断和延迟重载的错误提示 |

**项目整体进展评估**：今日 PR 以重构和稳定性修复为主，聚焦于代码共享、跨平台一致性和核心运行时健壮性。`#140339`（更新检查点恢复）和 `#129403`（JSON 深度限制）是最高价值的两个 PR，前者填补了中断更新恢复的功能空白，后者解决了 P0 级崩溃问题。

---

## 4. 社区热点

### 高评论 Issue（按 👍 排序）

| Issue | 标题 | 作者 | 👍 | 评论 | 状态 |
|---|---|---|---|---|---|
| [#79077](https://github.com/openclaw/openclaw/issues/79077) | Telegram bot-to-bot & guest-bot 支持 | bautrey | 8 | 14 | ✅ CLOSED |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 子进程泄漏导致 zombie 积累 | avp717 | 1 | 14 | 🔴 OPEN P1 |
| [#135111](https://github.com/openclaw/openclaw/issues/135111) | v2026.8.1 JSON 参数 malformed | 1Vision365-PeterTijsma | 0 | 14 | 🔴 OPEN P1 |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | Gateway 事件循环阻塞 | todddickerson | 0 | 12 | 🔴 OPEN P1 |
| [#140010](https://github.com/openclaw/openclaw/issues/140010) | Windows sleep/resume 后 WebSocket 重连失败 | TommyLei666 | 0 | 9 | 🔴 OPEN P1 |
| [#51572](https://github.com/openclaw/openclaw/issues/51572) | session-memory hook 时机扩展 | martins-oss | 1 | 8 | 🟡 OPEN P2 |
| [#71058](https://github.com/openclaw/openclaw/issues/71058) | 多 Azure/Teams bot 支持 | ashukla147 | 1 | 8 | 🟡 OPEN P2 |
| [#99583](https://github.com/openclaw/openclaw/issues/99583) | 智能 Session 自动命名 | apoapostolov | 2 | 7 | 🟡 OPEN P3 |

**热点分析**：
- **#79077**（Telegram 新特性支持）已成功关闭，反映社区对 Telegram 生态扩展的强烈需求已得到满足。
- **#97616** 和 **#135111** 均与 `2026.8.x` 升级后的回归问题相关，分别涉及子进程管理和 LLM provider 兼容性，是當前最紧迫的稳定性痛点。
- **#119720** 和 **#140010** 指向 Gateway 事件循环的架构级问题，在高负载和 Windows 平台表现尤为突出。
- **#99583**（智能 Session 命名）获得 2 个 👍，显示用户对 session 管理体验的改进有持续兴趣。

---

## 5. Bug 与稳定性

### P0 级问题

| Issue | 标题 | 作者 | 状态 | Fix PR |
|---|---|---|---|---|
| [#136203](https://github.com/openclaw/openclaw/issues/136203) | Windows de-DE 2026.8.2 升级后 Doctor 维护阻塞 | hermannmetzker-ai | 🔴 OPEN | 无 |
| [#129403](https://github.com/openclaw/openclaw/pull/129403) | JSON 嵌套深度导致 CLI 栈溢出 | xydigitLybnnnn | 🟡 OPEN (PR) | — |

### P1 级问题（高优先级）

| Issue | 标题 | 作者 | 状态 | Fix PR |
|---|---|---|---|---|
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 子进程泄漏（zombie accumulation） | avp717 | 🔴 OPEN | 无 |
| [#135111](https://github.com/openclaw/openclaw/issues/135111) | v2026.8.1 JSON 参数 malformed | 1Vision365-PeterTijsma | 🔴 OPEN | 无 |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | Gateway 事件循环阻塞 | todddickerson | 🔴 OPEN | — |
| [#140010](https://github.com/openclaw/openclaw/issues/140010) | Windows sleep/resume 重连失败 | TommyLei666 | 🔴 OPEN | — |
| [#124991](https://github.com/openclaw/openclaw/issues/124991) ✅ | CLI session reseed 在 SQLite store 无效 | alfredjbclaw | ✅ CLOSED | — |
| [#127148](https://github.com/openclaw/openclaw/issues/127148) | Codex sessions.compact 二次 client 冲突 | giangthb | 🔴 OPEN | — |
| [#118018](https://github.com/openclaw/openclaw/issues/118018) | Stale subagent completion 投递到错误 lifecycle | mjnkao | 🔴 OPEN | — |
| [#139847](https://github.com/openclaw/openclaw/issues/139847) | 2026.9.2 回复运行时消息丢失 | motochan | 🔴 OPEN | — |
| [#134579](https://github.com/openclaw/openclaw/issues/134579) | Active Memory before_prompt_build 未分发 | semiar86 | 🔴 OPEN | — |
| [#139215](https://github.com/openclaw/openclaw/issues/139215) | Cron scheduler 静默吞掉 scheduled ticks | WilhelminaVonHunt | 🔴 OPEN | — |

### P2 级问题

| Issue | 标题 | 作者 | 状态 |
|---|---|---|---|
| [#68264](https://github.com/openclaw/openclaw/issues/68264) | Canvas/Browser UI 可视化渲染失败 | Skunezero | 🔴 OPEN |
| [#137729](https://github.com/openclaw/openclaw/issues/137729) | transcript replay 中 .trim() 未保护 | daddyclint82 | 🔴 OPEN |
| [#128637](https://github.com/openclaw/openclaw/issues/128637) | 多 Agent 设置 AgentSelectionRequiredError | JunfXiao | 🔴 OPEN |
| [#140129](https://github.com/openclaw/openclaw/issues/140129) | Anthropic cache 卡在 ~46k tools+system prefix | JFLeonM | 🔴 OPEN |
| [#113701](https://github.com/openclaw/openclaw/issues/113701) | 大 tool outputs 导致 context overflow 失败循环 | ogilvymiles | 🔴 OPEN |

**稳定性总结**：今日新增多个 P1 级 Bug，主要集中在

---

## 横向生态对比



# 2026-09-07 开源 AI 智能体生态横向对比分析报告

## 1. 生态全景

2026年9月，个人 AI 助手开源生态呈现**头部项目高强度迭代、腰部项目质量巩固、长尾项目细分深耕**的分层格局。OpenClaw、Hermes Agent、CoPaw 作为活跃梯队，日均 Issue/PR 更新量超过 50 条，聚焦 Gateway 稳定性、多 Agent 协作和上下文管理三大核心挑战；NanoClaw 通过合约化重构推动多 Provider 标准化；而 PicoClaw、NullClaw、Moltis、ZeptoClaw 等项目处于稳定维护期，围绕特定场景（嵌入式、MCP 传输层、安全策略）做精细化打磨。整体生态正从"功能扩张"转向"稳定性与可观测性优先"阶段。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | Release | 合并/关闭 | 健康度 |
|------|-------------|-----------|---------|----------|--------|
| **OpenClaw** | 500 | 500 | 无 | Issue 36.6% / PR 45% | 🟢 健康 |
| **Hermes Agent** | 50 | 50 | 无 | 3 PR 合并 | 🟡 中（积压偏高） |
| **CoPaw** | 20 (11关闭) | 20 (6合并) | 无 | — | 🟠 注意（稳定性集中） |
| **NanoClaw** | 2 | 16 (8合并) | 无 | — | 🟢 健康（架构重构期） |
| **NanoBot** | 0 | 16 (5合并) | 无 | — | 🟢 良好 |
| **IronClaw** | 0 | 13 (3合并) | 无 | — | 🟢 良好（维护期） |
| **PicoClaw** | 4 (1关闭) | 2 (1合并) | 无 | — | 🟢 良好 |
| **Moltis** | 0 | 2 (0合并) | 无 | — | 🟡 中等（审查慢） |
| **NullClaw** | 0 | 1 (0合并) | 无 | — | 🟢 良好 |
| **ZeptoClaw** | 1 | 0 | 无 | — | 🟡 正常偏低 |
| **LobsterAI** | 1 (stale) | 1 (合并) | 无 | — | 🟡 中低（积压风险） |
| **ZeroClaw** | — | — | — | 摘要生成失败 | ⚠️ 未知 |

---

## 3. OpenClaw 在生态中的定位

**规模优势**：OpenClaw 以 500 条/日的 Issue/PR 吞吐量远超其他项目（次高 Hermes Agent 仅 50 条），社区规模和技术贡献密度均居生态首位。

**技术路线差异**：
- 相比 Hermes Agent 的 **Gateway 中心化架构**，OpenClaw 采用 **Gateway + subagent 索引统一** 的去中心化协作模式，今日合并的 `#140712`（subagent 索引统一）和 `#140339`（中断更新恢复）体现了其对分布式会话管理的深度投入。
- 相比 NanoClaw 的 **Provider 合约化**路线，OpenClaw 更强调 **跨平台一致性**（macOS/Windows/Android 多端修复同日推进）和 **策略代数统一**（Codex 复用核心 exec policy）。
- 相比 CoPaw 的 **多语言 WebUI** 导向，OpenClaw 更偏重 **CLI 稳定性** 和 **底层运行时健壮性**（JSON 深度限制 P0 修复、子进程泄漏治理）。

**生态位**：OpenClaw 定位为**全平台、多渠道、生产级**个人 AI 助手框架，覆盖桌面端、移动端、Gateway 服务和 CLI，是生态中功能完整度最高、用户基数最大的项目。

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **上下文/会话管理稳定性** | OpenClaw、Hermes Agent、CoPaw | OpenClaw：JSON 嵌套深度限制防栈溢出（#129403）、子进程泄漏（#97616）；Hermes Agent：session lease 僵尸锁（#104691）、WAL split-brain（#104596）；CoPaw：上下文意外丢失导致 AI 死循环（#7579/#7584） |
| **多 Provider/多 Profile 兼容** | OpenClaw、Hermes Agent、NanoClaw | Hermes Agent：MCP 多 Profile 注册冲突（#91654）、Anthropic 鉴权缓存失效（#104678）；NanoClaw：Provider 合约化重构；OpenClaw：Grokm xAI token 路由修复（#140653） |
| **长生命周期会话可靠性** | OpenClaw、Hermes Agent、CoPaw | Hermes Agent：Heartbeat tick 未送达（#92837）、Cron 静默吞掉 scheduled ticks（#139215）；CoPaw：Heartbeat cron session 消息重复堆积（#7589）；OpenClaw：子进程 zombie 积累（#97616） |
| **可观测性/异常处理** | Hermes Agent、CoPaw、NullClaw | CoPaw：工具派发层异常栈被吞没（#7572）；Hermes Agent：React useSyncExternalStore 重入崩溃（#90795）；NullClaw：MCP stdio 超时后进程组未清理（#991/#996） |
| **跨设备/分布式部署** | Hermes Agent、CoPaw | Hermes Agent：Bot Group Chat 桌面关闭后保持运行（#97681）、Gateway 托管 Group Room（#95163）；CoPaw：主 Agent 不主动查询子任务状态（#7450） |
| **多 Agent 协作体验** | CoPaw、OpenClaw | CoPaw：阻塞式等待子 Agent 完成的内置 Tool 需求（#7580）；OpenClaw：subagent 索引逻辑统一（#140712） |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 全平台个人助手，多渠道路由，策略系统 | 通用个人用户、开发者 | Gateway + subagent 统一索引，exec policy algebra，跨平台原生客户端 |
| **Hermes Agent** | 分布式 Bot 编排，Group Chat，Cron 自动化 | 需要无人值守 Bot 的用户、团队协作 | Desktop 作为编排中心（被社区质疑为单点故障），Gateway 托管会话 |
| **CoPaw** | 多 Agent 协作，多语言 WebUI，插件生态 | 中文用户、多 Agent 工作流用户 | 前端语言配置共享化，Memory 生命周期重构中，Advisor Mode 双模型协作 |
| **NanoClaw** | Provider 合约化，多 Agent 组，渠道扩展 | 需要深度定制 Provider 的开发者 | 合约化重构消除硬编码依赖，`speed` 属性精细化调控推理性价比 |
| **NanoBot** | MCP 生态增强，搜索 Provider 扩展，可观测性 | MCP 工具链用户、需要链路追踪的开发者 | MCP Schema 字节预算控制（#5388），Langfuse 集成（#5520），AnySearch 匿名搜索 |
| **IronClaw** | WebUI 交互精细化，多渠道适配诊断 | WebUI 用户、Slack/Discord 用户 | 依赖升级为主，前端卡片渲染和斜杠命令体验优化 |
| **PicoClaw** | 嵌入式设备支持，QQ 频道，i18n | 嵌入式开发者、国内渠道用户 | RV1106/RISC-V 适配，OpenCode Go session header 映射 |
| **NullClaw** | MCP stdio 传输层可靠性 | Zig 技术栈用户、MCP 底层开发者 | stdio 超时控制 + 进程组清理，Zig 语言实现 |
| **Moltis** | TLS 配置正确性，执行错误可诊断 | 需要精确 TLS/WebSocket 连接的用户 | ALPN 限制 HTTP/1.1 规避 RFC 8441 兼容性问题 |
| **ZeptoClaw** | 多智能体安全策略边界 | 关注 Agent 安全边界的开发者/研究者 | 子智能体委派框架策略继承审计（#664） |
| **LobsterAI** | 多 Agent 管理 UX | 多 Agent 工作流用户 | 任务列表状态同步优化需求（#1068） |

---

## 6. 社区热度与成熟度分层

```
快速迭代期（高强度功能交付）
├── OpenClaw      🟢 500 条/日，P0/P1 Bug 密集修复，架构重构并行
├── Hermes Agent  🟡 50 条/日，v0.21.0 后稳定性压力集中释放
└── NanoClaw      🟢 16 PR/日，8 条合并，合约化重构密集推进

质量巩固期（稳定性优先，新功能放缓）
├── CoPaw         🟠 20 Issue/日但 12 个为 Bug，上下文管理成为信任瓶颈
├── NanoBot       🟢 16 PR/日但侧重测试加固和文档，无新功能
└── IronClaw      🟢 13 PR/日但 3 条为依赖升级，WebUI 体验精细化

稳定维护期（低频更新，特定场景深耕）
├── PicoClaw      🟢 6 议题/日，嵌入式/N iche 渠道适配
├── NullClaw      🟢 1 PR/日，MCP 传输层可靠性
├── Moltis        🟡 2 PR/日，TLS/执行错误修复，审查节奏慢
├── ZeptoClaw     🟡 1 Issue/日，安全策略专项
└── LobsterAI     🟡 1 Issue + 1 PR/日，测试基础设施维护
```

---

## 7. 值得关注的趋势信号

### 7.1 上下文管理成为生态级痛点
OpenClaw（JSON 深度崩溃）、Hermes Agent（session lease 僵尸锁）、CoPaw（上下文丢失死循环）三个头部项目同时涌现上下文/会话管理 Bug，表明**多轮对话状态持久化**是当前架构的共性薄弱环节，预计将推动行业在 session 压缩、WAL 一致性、状态回滚机制上形成新的最佳实践。

### 7.2 多 Agent 协作从"能跑"到"可靠"
Hermes Agent 的分布式 Bot 诉求（#97681/#95163）、CoPaw 的阻塞式子 Agent 等待 Tool 需求（#7580）、OpenClaw 的 subagent 索引统一（#140712）共同指向一个趋势：**多 Agent 系统的确定性调度**正成为用户核心诉求，行业将从"支持多 Agent"转向"多 Agent 协作的可预期性"。

### 7.3 可观测性基建补强
CoPaw 异常栈吞没（#7572）、Hermes Agent React 重入崩溃（#90795）、NullClaw MCP 进程清理（#996）、NanoBot Langfuse 集成（#5520）表明，**故障定位能力**正从"锦上添花"变为"生产就绪必要条件"，未来版本将普遍标配链路追踪、异常上报和进程生命周期管理。

### 7.4 Provider 标准化与合约化
NanoClaw 的 Provider 合约化重构（#3581/#3584/#3585 等系列 PR）和 Hermes Agent 的多 Provider 冲突（#91654/#104678）反映，随着支持模型数量激增，**Provider 接口的类型安全和边界约束**将成为框架层的核心竞争力，硬编码适配模式正在被淘汰。

### 7.5 安全策略从"功能"升级为"架构"
ZeptoClaw 维护者亲自发起的子智能体策略继承审计（#664）具有标志性意义——**Agent 权限边界**正从功能特性上升为安全架构问题，预计将在未来 6-12 个月内催生行业级的多 Agent 安全策略规范。

---

**报告生成时间**：2026-09-07  
**分析师**：Agnes (Sapiens AI)

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报
**日期：2026-09-07** | 数据来源：HKUDS/nanobot

---

## 1. 今日速览

NanoBot 今日持续保持高频贡献节奏，24小时内共推进 **16 条 PR**，其中 **5 条已合并/关闭**，11 条仍处于开放状态。项目无新 Issue 提交，也无新版本发布。今日重点聚焦于**测试稳定性加固**、**文档更新**、**WeChat Work 渠道修复**以及 **CI/CD 流程优化**，整体健康度良好，社区活跃度稳定。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 摘要 | 链接 |
|----|------|------|------|
| #5683 | Bug Fix | 修复 WeChat Work 渠道媒体上传方式，改用官方 SDK API，替换私有 WebSocket 实现 | [PR #5683](https://github.com/HKUDS/nanobot/pull/5683) |
| #5679 | Bug Fix | 修复 TUI 底部状态栏上下文窗口占用显示逻辑，从聚合 token 统计改为实时上下文占用率 | [PR #5679](https://github.com/HKUDS/nanobot/pull/5679) |
| #5677 | Test | 修复 Windows 环境下游离测试用例，解决 `test_catalog_bounds_failure_only_keys`  nondeterministic 失败问题 | [PR #5677](https://github.com/HKUDS/nanobot/pull/5677) |
| #5680 | CI/CD | 并行化 Linux/Windows Python 测试套件（pytest-xdist），启用 uv 依赖缓存，分离 Windows 进程兼容性测试 | [PR #5680](https://github.com/HKUDS/nanobot/pull/5680) |
| #5309 | Bug Fix | 修复 Marketplace 技能覆盖内置技能的问题，使工作区技能可正确屏蔽同名内置技能 | [PR #5309](https://github.com/HKUDS/nanobot/pull/5309) |

**进展评估：** 今日合并的 PR 主要围绕**稳定性与基础设施**层面，修复了用户可感知的 Bug（TUI 显示错误、WeChat Work 上传失败、技能覆盖异常），同时 CI 效率得到显著提升，为后续功能迭代打下更稳固基础。

---

## 4. 社区热点

以下为今日活跃或值得关注的高讨论度 PR：

| PR | 热度指标 | 摘要 | 链接 |
|----|----------|------|------|
| #5684 | 新提交 | 全面刷新 README，补充 WebUI 功能画廊、对话面板、上下文使用及原生终端客户端说明 | [PR #5684](https://github.com/HKUDS/nanobot/pull/5684) |
| #5607 | 跨月活跃 | 新增 AnySearch 网络搜索 Provider，遵循 Serper Provider 模式，支持匿名配额 | [PR #5607](https://github.com/HKUDS/nanobot/pull/5607) |
| #5580 | 跨月活跃 | 将会话持久化操作移出事件循环，解决文件锁竞争导致的对话卡顿问题 | [PR #5580](https://github.com/HKUDS/nanobot/pull/5580) |
| #5520 | 跨月活跃 | 为 Codex Provider 添加 Langfuse 链路追踪支持 | [PR #5520](https://github.com/HKUDS/nanobot/pull/5520) |

**热点分析：**
- **#5684** 反映社区对文档可读性的强烈需求，老版 README 已无法准确反映当前 WebUI 功能，亟需更新以降低新用户上手门槛。
- **#5607** 是继 Serper 之后新增的第三个搜索 Provider，表明项目正在持续扩展搜索生态，满足多样化部署需求（尤其是无 API Key 场景）。
- **#5580** 涉及性能瓶颈修复，长期未合并且评论较多，说明该问题在用户群体中引发较大关注。

---

## 5. Bug 与稳定性

| 优先级 | PR | 问题描述 | 状态 | 链接 |
|--------|-----|----------|------|------|
| P2 | #5683 | WeChat Work 渠道媒体上传失败，私有 WebSocket 实现不稳定 | ✅ 已合并 | [PR #5683](https://github.com/HKUDS/nanobot/pull/5683) |
| P2 | #5679 | TUI footer 上下文占用显示不准确，误导用户感知 | ✅ 已合并 | [PR #5679](https://github.com/HKUDS/nanobot/pull/5679) |
| P2 | #5682 | ExecTool 相对路径解析错误，相对于 CWD 而非 Workspace | 🔄 待合并 | [PR #5682](https://github.com/HKUDS/nanobot/pull/5682) |
| P2 | #5309 | Marketplace 技能无法正确覆盖内置技能（如 github） | ✅ 已合并 | [PR #5309](https://github.com/HKUDS/nanobot/pull/5309) |
| P2 | #5678 | SSRF 防护缺少关键回归测试覆盖（validate_resolved_url / PinnedDNSAsyncTransport） | 🔄 待合并 | [PR #5678](https://github.com/HKUDS/nanobot/pull/5678) |

**稳定性评估：** 今日修复了 3 个生产级 Bug，剩余 2 个待合并 PR 均已在测试覆盖范围内，整体稳定性持续改善。

---

## 6. 功能请求与路线图信号

| PR | 功能方向 | 信号强度 | 链接 |
|----|----------|----------|------|
| #5607 | Web Search 新增 AnySearch Provider | ⭐⭐⭐ 高 | [PR #5607](https://github.com/HKUDS/nanobot/pull/5607) |
| #5676 | CLI 新增 attach-only Desktop 目标选择 | ⭐⭐ 中 | [PR #5676](https://github.com/HKUDS/nanobot/pull/5676) |
| #5388 | MCP 工具 Schema 字节预算限制（保护上下文） | ⭐⭐⭐ 高 | [PR #5388](https://github.com/HKUDS/nanobot/pull/5388) |
| #5386 | MCP Apps 结果元数据保留（结构化数据透传） | ⭐⭐⭐ 高 | [PR #5386](https://github.com/HKUDS/nanobot/pull/5386) |
| #4549 | Heartbeat 支持配置廉价替代模型 | ⭐⭐ 中 | [PR #4549](https://github.com/HKUDS/nanobot/pull/4549) |
| #4551 | Heartbeat 支持共享会话（isolated_session=false） | ⭐⭐ 中 | [PR #4551](https://github.com/HKUDS/nanobot/pull/4551) |
| #5520 | Codex Provider 支持 Langfuse 链路追踪 | ⭐⭐ 中 | [PR #5520](https://github.com/HKUDS/nanobot/pull/5520) |

**路线图判断：**
- **MCP 生态增强**（#5388、#5386）是当前最活跃的功能方向，聚焦于控制模型可见工具集和优化元数据传递，预计将在下一版本重点纳入。
- **Heartbeat 机制优化**（#4549、#4551）反映用户希望降低长周期守护任务的成本并提升灵活性。
- **搜索 Provider 扩展**（#5607）表明项目正在构建更多元的数据接入能力。

---

## 7. 用户反馈摘要

今日无新增 Issues，但从活跃 PR 的讨论中可以提炼以下用户诉求：

| 诉求领域 | 具体痛点 | 对应 PR |
|----------|----------|---------|
| 文档/ discoverability | 新版 WebUI 功能（对话面板、上下文使用、终端客户端）在 README 中难以发现 | #5684 |
| 搜索灵活性 | 需要无需 API Key 的匿名搜索方案，降低部署门槛 | #5607 |
| 路径解析 | ExecTool 相对路径行为不符合预期，导致工作区外执行 | #5682 |
| 性能体验 | 会话持久化操作阻塞事件循环，影响并发对话流畅度 | #5580 |
| 安全防护 | SSRF 防护缺乏回归测试，安全边界存在盲区 | #5678 |
| 成本控制 | Heartbeat 任务希望使用更便宜的模型以降低 API 开销 | #4549 |
| 上下文管理 | MCP 工具过多时 schema 占用大量 token，需要预算控制机制 | #5388 |

---

## 8. 待处理积压

| PR | 创建日期 | 状态 | 建议关注原因 | 链接 |
|----|----------|------|--------------|------|
| #5580 | 2026-08-28 | OPEN | 跨月未合并，性能修复优先级高，影响多会话并发体验 | [PR #5580](https://github.com/HKUDS/nanobot/pull/5580) |
| #5520 | 2026-08-24 | OPEN | 跨月未合并，填补 Codex Provider 可观测性空白 | [PR #5520](https://github.com/HKUDS/nanobot/pull/5520) |
| #5388 | 2026-08-13 | OPEN | 长期开放，MCP Schema 预算控制是上下文管理的核心机制 | [PR #5388](https://github.com/HKUDS/nanobot/pull/5388) |
| #5386 | 2026-08-13 | OPEN | 与 #5388 配套，MCP 元数据透传依赖两者共同落地 | [PR #5386](https://github.com/HKUDS/nanobot/pull/5386) |
| #4549 | 2026-06-26 | OPEN | 超长期未响应，Heartbeat 成本优化需求明确 | [PR #4549](https://github.com/HKUDS/nanobot/pull/4549) |
| #4551 | 2026-06-26 | OPEN | 与 #4549 配套，会话共享需求长期存在 | [PR #4551](https://github.com/HKUDS/nanobot/pull/4551) |

---

**日报生成时间：** 2026-09-07 | **分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-09-07** | 数据来源：github.com/nousresearch/hermes-agent

---

## 1. 今日速览

Hermes Agent 今日保持高活跃状态：过去24小时新增/更新 **50 条 Issues**、**50 条 PR**，但仅合并/关闭 **3 个 PR**，显示开发端产出速度显著高于合并节奏。项目目前无新版本发布。P1 级 Bug 集中爆发于 Gateway 会话状态管理（#92837、#104691）、MCP 多 Profile 冲突（#91654）及 Anthropic 鉴权缓存（#104678），反映 v0.21.0 发布后多 Profile 和多 Provider 场景的稳定性压力。Bot Group Chat 跨设备连续性（#97681）和 turn-level 时间感知（#10421）是当前社区最关注的功能方向。

---

## 2. 版本发布

无新版本发布。当前最新为 v0.21.0（2026-08-31），相关回归问题已在 Issues 中累计追踪。

---

## 3. 项目进展

今日合并/关闭的 PR 共 **3 个**：

| PR | 类型 | 说明 |
|----|------|------|
| [#104657](https://github.com/NousResearch/hermes-agent/issues/104657) [CLOSED] | Bugfix | 清除持久化会话外发消息中的 `_db_persisted` 标记，修复 OpenAI 兼容端点拒绝额外字段的 400 错误 |
| [#96236](https://github.com/NousResearch/hermes-agent/issues/96236) [CLOSED] | Feature | `/status` 命令新增显示当前会话的 reasoning effort 级别，CLI 与 Gateway 侧同步 |
| [#104688](https://github.com/NousResearch/hermes-agent/pull/104688) | Bugfix (待合并) | 修复 worktree 场景下 prompt cache 共享上下文断裂问题（P0） |

**整体判断**：合并节奏偏慢（3/50），但集中在修复关键兼容性问题和用户体验细节，尚未有重大功能交付。

---

## 4. 社区热点

| 排名 | Issue | 评论数 | 热度指标 | 核心诉求 |
|------|-------|--------|----------|----------|
| 1 | [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 169 | Skills index 持续 degraded（29.8h > 26h 阈值） | 自动化索引健康检查机制失灵，用户长期等待修复 |
| 2 | [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 25 | Bot Group Chat 桌面关闭后保持运行 | 多设备协同、Bot 分布式部署的核心需求 |
| 3 | [#10421](https://github.com/NousResearch/hermes-agent/issues/10421) | 19 | 👍 9 | Turn-level 实时时间感知，当前仅有 session 级时间戳 |
| 4 | [#95163](https://github.com/NousResearch/hermes-agent/issues/95163) | 14 | Gateway 端托管 Group Room，脱离 Desktop 渲染器控制 | 与 #97681 形成互补：一个要连续性，一个要架构解耦 |

**热点分析**：社区关注点高度集中在 **会话生命周期管理** 和 **多设备/多 Bot 协作** 两个维度，反映 Hermes Agent 正从单机工具向分布式 Agent 平台演进，但底层架构（Desktop 作为编排中心）成为瓶颈。

---

## 5. Bug 与稳定性

### P1 级（高优先级）

| Issue | 组件 | 描述 | Fix PR |
|-------|------|------|--------|
| [#90795](https://github.com/NousResearch/hermes-agent/issues/90795) | Desktop/React | `useSyncExternalStore` 重入导致 workspace 面板崩溃（Maximum update depth exceeded） | 无 |
| [#92837](https://github.com/NousResearch/hermes-agent/issues/92837) | Gateway/Cron | Heartbeat tick 被计数但未送达，agent-cache idle-evict 后唤醒丢失 | 无 |
| [#104453](https://github.com/NousResearch/hermes-agent/issues/104453) | Cron/systemd | systemd 249 下 `OOMPolicy=kill` 不被识别，cron 调度全部失败 | 无 |
| [#91654](https://github.com/NousResearch/hermes-agent/issues/91654) | MCP/Gateway | 多 Profile 共享同一 Gateway 进程时 MCP 注册表按 server name 冲突 | 无 |
| [#104691](https://github.com/NousResearch/hermes-agent/issues/104691) | Agent/Core | Session lease 僵尸锁，torn-down lane 后会话永久 "already has a live owner" | 无 |
| [#104678](https://github.com/NousResearch/hermes-agent/issues/104678) | Anthropic/Auth | Pro/Max 订阅耗尽后 `failure_reason=billing` 无过期时间，缓存错误永久复现 | 无 |
| [#42719](https://github.com/NousResearch/hermes-agent/issues/42719) | ACP/MCP | ACP 提供的 MCP tools 注册成功但在 model request 中被丢弃 | 无 |

### P2 级（中优先级）

| Issue | 组件 | 描述 | Fix PR |
|-------|------|------|--------|
| [#104711](https://github.com/NousResearch/hermes-agent/issues/104711) | Agent/xAI | Grok 返回 list-shaped `reasoning_content` 导致流式崩溃 | [#104717](https://github.com/NousResearch/hermes-agent/pull/104717) ✅ 待合并 |
| [#104596](https://github.com/NousResearch/hermes-agent/issues/104596) | Gateway/SQLite | 单进程内 state.db WAL split-brain，journal-mode probe 失败后 unlink 兄弟连接 | 无 |
| [#104622](https://github.com/NousResearch/hermes-agent/issues/104622) | Anthropic/Auth | `resolve_anthropic_token()` 优先借用 Claude Code 登录，导致 Hermes 凭据池被绕过 | 无 |
| [#104357](https://github.com/NousResearch/hermes-agent/issues/104357) | Discord/Cron | 附件上传 404（Unknown Channel），文本消息正常 | 无 |
| [#104694](https://github.com/NousResearch/hermes-agent/issues/104694) | Agent/Discord | 降级标题生成器产出退化单字符标题（如 `{`、``` ``` ```），破坏 Discord 线程名 | 无 |
| [#102658](https://github.com/NousResearch/hermes-agent/issues/102658) | Gateway/Config | 运行中会话的 `model_override` 无法被 config 变更清除 | 无 |

### P3 级（低优先级）

| Issue | 描述 |
|-------|------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index 过期（29.8h > 26h 限制），自动化探针持续报 degraded |
| [#104712](https://github.com/NousResearch/hermes-agent/issues/104712) | Desktop Tasks 列表截断，超过 ~11 项无滚动条 |
| [#104696](https://github.com/NousResearch/hermes-agent/issues/104696) | macOS `search_files` 在 rg 清理阶段因 EPERM 丢失结果 |
| [#104693](https://github.com/NousResearch/hermes-agent/issues/104693) | Honcho 混合模式下 recall 注入上一轮用户消息上下文 |
| [#94921](https://github.com/NousResearch/hermes-agent/issues/94921) | Ghostty 终端 Shift+字母输入原始 ANSI 序列 |
| [#104719](https://github.com/NousResearch/hermes-agent/issues/104719) | z-ai provider 定价缺失，usage 显示 $0/unknown |

---

## 6. 功能请求与路线图信号

| 需求 | Issue | 相关 PR | 纳入下一版本可能性 |
|------|-------|---------|-------------------|
| Bot Group Chat 跨设备连续性 | [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | [#104601](https://github.com/NousResearch/hermes-agent/pull/104601)（待合并） | **高** — 已有渐进式实现 PR |
| Gateway 端托管 Group Room | [#95163](https://github.com/NousResearch/hermes-agent/issues/95163) | 无 | **中** — 架构改动大，需独立设计 |
| Turn-level 实时时间感知 | [#10421](https://github.com/NousResearch/hermes-agent/issues/10421) | 无 | **中** — 社区 👍 9，需求明确 |
| Email session 按 subject 隔离 | [#26277](https://github.com/NousResearch/hermes-agent/issues/26277) | 无 | **低** — P3，边缘场景 |
| `execute_code` 可信 Profile 免审批 | [#44993](https://github.com/NousResearch/hermes-agent/issues/44993) | 无 | **低** — 安全边界问题，需谨慎 |
| Cron 原子化 disabled 创建 | — | [#104715](https://github.com/NousResearch/hermes-agent/pull/104715) | **高** — 操作者需求，PR 已就绪 |
| Desktop 自动化卡片从 Composer 创建 | — | [#104716](https://github.com/NousResearch/hermes-agent/pull/104716) | **中** — UX 改进，PR 已就绪 |
| 自定义 provider 定价覆盖 | — | [#92613](https://github.com/NousResearch/hermes-agent/pull/92613) | **高** — 弥补 billing 盲区 |

---

## 7. 用户反馈摘要

**核心痛点**：
1. **多 Profile/MCP 冲突**：[#91654](https://github.com/NousResearch/hermes-agent/issues/91654) 和 [#104622](https://github.com/NousResearch/hermes-agent/issues/104622) 反映用户运行多 Profile 或多 Provider 时，Gateway 进程内资源隔离不足，凭据和注册表存在隐式共享风险。
2. **长生命周期会话可靠性**：[#92837](https://github.com/NousResearch/hermes-agent/issues/92837)、[#104691](https://github.com/NousResearch/hermes-agent/issues/104691)、[#104596](https://github.com/NousResearch/hermes-agent/issues/104596) 三个 P1 Bug 均与 session lease、WAL、heartbeat 等长时状态管理相关，说明 v0.21.0 在 gateway 稳定性上存在回归。
3. **桌面端作为单点故障**：[#97681](https://github.com/NousResearch/hermes-agent/issues/97681) 和 [#95163](https://github.com/NousResearch/hermes-agent/issues/95163) 共同指向同一诉求——Bot Group Chat 不应依赖 Desktop 持久运行，用户希望在服务器/VPS 上部署无头 Bot。
4. **xAI/Grok 兼容性**：[#104711](https://github.com/NousResearch/hermes-agent/issues/104711) 和 [#104719](https://github.com/NousResearch/hermes-agent/issues/104719) 显示非 OpenAI 原生 provider 的格式差异和定价缺失正在影响用户体验。

**正面反馈**：
- `/status` 新增 reasoning effort 显示（[#96236](https://github.com/NousResearch/hermes-agent/issues/96236)）解决了用户反复切换命令确认状态的操作摩擦。
- `_db_persisted` 标记清除（[#104657](https://github.com/NousResearch/hermes-agent/issues/104657)）修复了resume会话与严格OpenAI兼容端点的互操作性。

---

## 8. 待处理积压

| Issue | 状态 | 风险等级 | 建议关注点 |
|-------|------|----------|-----------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 169 评论未决 | 高 | Skills index watchdog 机制根本性修复，长期影响自动化工作流 |
| [#90795](https://github.com/NousResearch/hermes-agent/issues/90795) | P1，无 PR | 高 | React 重入崩溃影响所有 live session，需紧急修复 |
| [#92837](https://github.com/NousResearch/hermes-agent/issues/92837) | P1，无 PR | 高 | Heartbeat 静默失败导致长时 Bot 会话丢失，无自动恢复路径 |
| [#104596](https://github.com/NousResearch/hermes-agent/issues/104596) | P1，无 PR | 高 | SQLite WAL split-brain 在单进程内复现，可能影响所有持久化 session |
| [#42719](https://github.com/NousResearch/hermes-agent/issues/42719) | P1，无 PR | 高 | ACP + MCP 工具链完全失效，阻塞 ACP 用户 |
| [#96161](https://github.com/NousResearch/hermes-agent/pull/96161) | 待合并 | 中 | Terminal provider 配置支持，阻塞 SSH 工作区功能完整性 |
| [#99220](https://github.com/NousResearch/hermes-agent/pull/99220) | 待合并 | 中 | Relay egress 授权修复，安全相关 |

---

**健康度评估**：项目社区活跃度健康（日均 50+

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-09-07

## 1. 今日速览

过去24小时 PicoClaw 社区活跃度保持稳定：共新增/更新 6 个议题（4 Issues + 2 PRs），其中 1 个 Issue 已关闭、1 个 PR 已合并，项目维护者持续跟进用户反馈。今日无新版本发布，整体状态以 Bug 修复和功能补充为主，社区贡献者正推动多语言支持（捷克语）、QQ 频道附件处理能力以及 OpenCode Go session header 支持等改进。项目健康度良好，Issue 响应及时，但部分问题因 stale 标记需关注长期未决项。

---

## 2. 版本发布

> 今日无新版本发布。

---

## 3. 项目进展

**✅ PR #1349 [CLOSED] — feat(qq): 支持解析和回复更多 QQ 频道附件类型**
- 作者：aishannon
- 合并时间：2026-09-06
- 推进内容：显著扩展了 QQ 频道的消息处理能力，新增对表情结构解析、语音/图片/视频/文件消息的接收与回复支持，并优先使用 Markdown 格式回复，降级兼容原有格式。
- 项目价值：提升 QQ 渠道的完整性和用户体验，减少因附件类型不支持导致的功能盲区。

> 项目整体向前迈进：核心渠道能力持续完善，多语言 i18n 工作仍在进行（PR #3348 待合并）。

---

## 4. 社区热点

| 议题 | 状态 | 评论数 | 亮点 |
|------|------|--------|------|
| [#675](https://github.com/sipeed/picoclaw/issues/675) Add more LLM Provider Support | CLOSED | 7 | 历史上评论数最多的议题之一，用户对扩展 LLM 供应商支持有持续需求 |
| [#3351](https://github.com/sipeed/picoclaw/issues/3351) 自动压缩导致历史记录物理删除 | OPEN [stale] | 1 | 用户定位到 `pkg/memory/jsonl.go` 源码根因，指出 `SetHistory → rewriteJSONL` 会物理覆盖文件 |
| [#3350](https://github.com/sipeed/picoclaw/issues/3350) 低性能设备 Web UI 输入卡顿 | OPEN [stale] | 1 | 嵌入式设备（RV1106、RISC-V）用户体验问题，输入延迟与聊天记录长度相关 |
| [#3369](https://github.com/sipeed/picoclaw/issues/3369) OpenCode Go session header support | OPEN | 0 | 新提出的功能需求，针对 OpenCode Go 的 `x-opencode-session` header 映射问题 |
| [#3348](https://github.com/sipeed/picoclaw/pull/3348) i18n: 完成捷克语标签包裹 | OPEN [stale] | — | 多语言本地化推进中 |

**热点分析：**
- **Issue #675** 虽已关闭，但 7 条评论反映社区对 LLM 供应商扩展的强烈诉求，需关注是否已纳入后续规划。
- **Issue #3351** 和 **#3350** 均被标记 stale，但问题描述详尽、源码定位清晰，表明贡献者具备深度参与能力，值得维护者优先处理。
- **Issue #3369** 为新需求，涉及 OpenCode 生态兼容性，可能影响特定用户群体的集成体验。

---

## 5. Bug 与稳定性

| 严重程度 | 议题 | 描述 | Fix PR |
|----------|------|------|--------|
| 🔴 高 | [#3351](https://github.com/sipeed/picoclaw/issues/3351) | Session 自动压缩导致原始聊天记录物理删除，数据不可恢复 | 暂无 |
| 🟡 中 | [#3350](https://github.com/sipeed/picoclaw/issues/3350) | 嵌入式设备 Web UI 输入框打字卡顿，CPU 飙升 | 暂无 |

**说明：**
- **#3351** 为数据丢失类 Bug，根因已定位至 `JSONLStore` 的 `rewriteJSONL` 方法，建议优先修复以确保用户数据持久化安全。
- **#3350** 影响嵌入式场景用户体验，需优化前端渲染性能或延迟加载策略。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 可能性评估 |
|------|------|-----------|
| 扩展 LLM 供应商支持 | [#675](https://github.com/sipeed/picoclaw/issues/675)（已关闭） | 高 — 用户基数大，需跟进已支持哪些供应商 |
| OpenCode Go session header 映射 | [#3369](https://github.com/sipeed/picoclaw/issues/3369) | 中 — 新需求，涉及 API 兼容性设计 |
| 捷克语 i18n 补全 | [#3348](https://github.com/sipeed/picoclaw/pull/3348) | 高 — PR 已提交，待合并 |
| QQ 频道附件处理增强 | [#1349](https://github.com/sipeed/picoclaw/pull/1349)（已合并） | ✅ 已纳入 |

---

## 7. 用户反馈摘要

**痛点：**
1. **数据持久化担忧**（#3351）：用户发现 session 压缩后原始记录被物理删除，无法找回历史，对"失忆"机制缺乏信任。
2. **嵌入式设备性能**（#3350）：RV1106、RISC-V 等低性能硬件上 Web UI 输入延迟明显，且与聊天记录长度相关，超出预期。
3. **OpenCode 集成兼容**（#3369）：OpenCode Go 需要 `x-opencode-session` header，但当前 OpenAI-compatible provider 无法自动映射 session ID。

**满意点：**
- QQ 频道附件处理能力的增强（#1349）获社区认可。
- i18n 多语言支持持续推进（捷克语 PR #3348）。

---

## 8. 待处理积压

| 类型 | 编号 | 创建时间 | 状态 | 建议 |
|------|------|----------|------|------|
| Issue | [#3351](https://github.com/sipeed/picoclaw/issues/3351) | 2026-08-30 | stale | 优先修复数据丢失问题 |
| Issue | [#3350](https://github.com/sipeed/picoclaw/issues/3350) | 2026-08-30 | stale | 评估嵌入式性能优化方案 |
| PR | [#3348](https://github.com/sipeed/picoclaw/pull/3348) | 2026-08-29 | stale | 尽快合并捷克语本地化 |
| Issue | [#3369](https://github.com/sipeed/picoclaw/issues/3369) | 2026-09-06 | 新 | 评估 OpenCode Go session 支持可行性 |

> **维护者提示**：#3351 和 #3350 已 stale 但问题描述清晰、根因明确，建议尽快响应以避免用户流失。#3348 PR 等待合并以完成捷克语本地化。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期**：2026-09-07  
**数据来源**：GitHub `nanocoai/nanoclaw`

---

### 1. 今日速览
过去24小时 NanoClaw 保持高活跃度，共产生 16 条 PR 更新（8条合并/关闭）与 2 条 Issue 更新。核心工作聚焦于 Provider 架构合约化重构与渠道稳定性修复，成功合入 Slack 共享会话模式修复。暂无新版本发布，项目正处于 v2.3.0 后的底层架构稳固期，多提供者兼容性与代码可维护性显著提升。

### 2. 版本发布
本期无新版本发布。

### 3. 项目进展
今日合并/关闭的 8 条 PR 主要围绕 **Provider 核心合约重构** 与 **渠道修复** 展开，推动项目架构向标准化迈进：
- **架构合约化**：`#3581`、`#3584`、`#3585`、`#3586`、`#3591`、`#3727` 形成一组连贯的重构序列，将容器运行时、主机初始化、安装验证器及指令渲染全面合约化。消除了历史硬编码依赖，实现了多 Provider 字节级输出的可验证性。
- **性能调控增强**：`#3592` 为 Agent 组新增 `speed` 核心属性，与 `model`/`effort` 并列，支持 CLI 配置与 Provider 词法声明，提升了推理性价比的精细化调控能力。
- **渠道 Bug 修复**：`#3731` 修复了 Slack 在 `session_mode: "shared"` 下重复创建独立会话的回归问题，恢复预期行为。

### 4. 社区热点
- **`[Issue #3728]`** Telegram 入站轮询静默失效：`pollingLoop` 无限重试且无成功日志，导致服务呈现“假活”状态，影响生产可靠性。作者验证了 v2.1.54 与 v2.3.0 均复现，反映出用户对监控告警与熔断机制的迫切需求。[链接](https://github.com/nanocoai/nanoclaw/issues/3728)
- **`[PR #3729]`** 浏览器端社区单元与权益管理：推动 Echo/Slack 配置流程迁移至浏览器 Portal，通过 WorkOS 统一身份验证，显著优化首次安装体验。目前状态开放，等待核心团队 Review。[链接](https://github.com/nanocoai/nanoclaw/pull/3729)
- **`[PR #3726]`** 原生 Proton Mail 适配器：填补邮件渠道空白，通过 Proton Mail Bridge 实现入站唤醒与线程回复，契合多模态触达的社区诉求。[链接](https://github.com/nanocoai/nanoclaw/pull/3726)

### 5. Bug 与稳定性
1. **[高] Slack shared session 模式异常**（`#3730`）：`main` 分支下共享会话配置未生效，每条 DM 仍 spawn 新会话。**状态：已通过 `#3731` 修复并合并。**
2. **[高] Telegram 轮询静默死锁**（`#3728`）：缺乏超时熔断与健康度上报，入站服务可静默挂起数日。**状态：待修复，暂无关联 PR。** 建议优先补充轮询失败阈值与告警日志。

### 6. 功能请求与路线图信号
- **多 Provider 深度集成**：`#3356`（Cursor SDK payload）、`#3355`（`/add-cursor` 安装 Skill）、`#3722`（OpenCode 合约适配）技术草案已完整

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 — 2026-09-07

## 1. 今日速览

NullClaw 在过去 24 小时内保持**低活跃状态**，无 Issues 更新，无新版本发布。唯一动态为 PR #996 待合并，聚焦 MCP stdio 响应超时处理与进程清理修复。项目整体处于稳定期，无阻塞性 Bug 或争议性讨论。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

| PR | 标题 | 状态 | 作者 |
|---|---|---|---|
| [#996](https://github.com/nullclaw/nullclaw/pull/996) | `fix(mcp): bound stdio response waits` | 🟡 待合并 | be-student |

**进展分析：**
- PR #996 修复了 #991，为 MCP stdio 传输层引入 `timeout_ms` 超时控制，并补充了请求超时后终止服务器进程组的逻辑，同时修复了初始化失败时的子进程清理问题。
- 测试验证：`zig build test --summary all` 通过 7,373 项，9 项跳过；`zig build -Doptimize=ReleaseSmall` 编译正常。
- 该 PR 对 MCP 子系统的**稳定性与资源泄漏防护**有直接贡献，合并后将提升长时间运行场景下的健壮性。

---

## 4. 社区热点

今日无活跃 Issue 或高评论 PR。PR #996 评论数暂无记录（`undefined`），暂无法评估社区关注度。

---

## 5. Bug 与稳定性

| 关联 Issue | 问题描述 | 严重程度 | Fix PR |
|---|---|---|---|
| [#991](https://github.com/nullclaw/nullclaw/issues/991) | MCP stdio 响应无限等待，超时后进程组未清理，初始化失败时子进程泄漏 | 🟡 中等 | [#996](https://github.com/nullclaw/nullclaw/pull/996) |

**评估：** #991 为已知中等优先级 Bug，已有 PR #996 修复并待合并。测试覆盖率良好，无新崩溃报告。

---

## 6. 功能请求与路线图信号

今日无新功能请求。PR #996 反映社区对 **MCP 传输层可靠性**的关注，未来可关注是否会有超时策略可配置化、进程管理抽象化等相关需求浮现。

---

## 7. 用户反馈摘要

今日无新 Issue 或评论，无法提炼用户反馈。

---

## 8. 待处理积压

| 类型 | 编号 | 说明 |
|---|---|---|
| PR | [#996](https://github.com/nullclaw/nullclaw/pull/996) | `fix(mcp): bound stdio response waits` — 已创建并验证通过，等待维护者合并 |

---

**项目健康度评估：🟢 良好** — 核心测试稳定，关键 Bug 已有修复路径，社区活跃度适中，无阻塞性问题。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-09-07

---

## 1. 今日速览

过去 24 小时内，IronClaw 项目共产生 **13 条 PR 更新**，其中 3 条已合并/关闭，10 条仍待合并，整体开发节奏保持稳定。Issues 无新增或活跃更新，社区讨论热度偏低。今日变更以 **dependabot 自动依赖升级** 和 **webui 交互细节修复** 为主，无新功能推出或版本发布。项目整体处于**常规维护期**，健康度良好，但新功能推进力度偏缓。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭了 3 条 PR，均为依赖升级类变更：

| PR | 类型 | 说明 |
|----|------|------|
| [#8049](https://github.com/nearai/ironclaw/pull/8049) | 依赖升级 | 升级 `everything-else` 组 19 个 Rust 包（含 `uuid` 1.24→1.26、`base64` 0.22→0.23 等） |
| [#7835](https://github.com/nearai/ironclaw/pull/7835) | CI 依赖 | 升级 GitHub Actions 5 个（含 `actions/setup-node` 4.0.2→7.0.0、`anthropics/claude-code-action` 1.0.183→1.0.210） |
| [#7020](https://github.com/nearai/ironclaw/pull/7020) | 依赖升级 | `tokio-tungstenite` 0.29.0→0.30.0 |

**影响评估：** 均为低风险依赖更新，未引入破坏性变更。项目技术栈保持同步，CI 工具链更新至较新版本。

---

## 4. 社区热点

今日无新 Issue 创建，所有 PR 评论数均为 0，**社区讨论热度较低**。

值得关注的开放 PR（按优先级排序）：

- **[PR #8071](https://github.com/nearai/ironclaw/pull/8071)** — 修复 WebUI 命令结果卡片高度塌陷问题，涉及滚动行为优化，对用户体验影响直接。
- **[PR #8076](https://github.com/nearai/ironclaw/pull/8076)** — 区分断连共享频道与未配对账户，改善 Slack 等适配器的诊断提示。
- **[PR #8077](https://github.com/nearai/ironclaw/pull/8077)** — 修复 MCP 响应泄漏诊断分类（ closes [#8009](https://github.com/nearai/ironclaw/issues/8009)），影响 MCP 链路安全性。

---

## 5. Bug 与稳定性

| 问题 | 状态 | 关联 PR | 严重程度 |
|------|------|---------|----------|
| MCP 响应泄漏诊断分类错误 | 已修复（待合并） | [#8077](https://github.com/nearai/ironclaw/pull/8077) | 中 |
| 共享频道断连状态误判 | 已修复（待合并） | [#8076](https://github.com/nearai/ironclaw/pull/8076) | 低 |
| WebUI 命令结果卡片高度异常 | 已修复（待合并） | [#8071](https://github.com/nearai/ironclaw/pull/8071) | 低 |
| Slash-command 菜单对齐问题 | 已修复（待合并） | [#8070](https://github.com/nearai/ironclaw/pull/8070) | 低 |
| Slash-command 激活态不可见 | 已修复（待合并） | [#8068](https://github.com/nearai/ironclaw/pull/8068) | 低 |
| 命令结果卡片缺少关闭操作 | 已修复（待合并） | [#8069](https://github.com/nearai/ironclaw/pull/8069) | 低 |

> 所有已知 Bug 均有对应 PR 修复，无未处理的崩溃或回归问题。

---

## 6. 功能请求与路线图信号

今日无新 Feature Request Issue。

从开放 PR 可观察到以下**潜在路线图方向**：

- **WebUI 体验精细化**：#8068–#8071 四连 PR 聚焦 slash-command 菜单交互、命令结果卡片行为优化，表明项目正持续推进前端交互质量。
- **MCP 可观测性增强**：#8077 改进泄漏诊断分类，反映项目对 MCP 链路安全性的持续投入。
- **多渠道适配完善**：#8076 改善 Slack 等共享频道断连感知，表明多平台适配仍是优先方向。

---

## 7. 用户反馈摘要

今日无新增 Issue，无法提取实时用户反馈。

基于已关闭 PR 的历史上下文推断，用户主要关注点包括：
- **MCP 通道诊断透明度**（#8077 关联 #8009）
- **Slack/共享频道连接状态感知**（#8076）
- **WebUI 卡片渲染与滚动体验**（#8068–#8071）

---

## 8. 待处理积压

以下 PR 已开放超过 3 天未合并，建议维护者关注：

| PR | 作者 | 状态 | 开放天数 | 建议 |
|----|------|------|----------|------|
| [#8068](https://github.com/nearai/ironclaw/pull/8068) | italic-jinxin | OPEN | 3 | 低风险 webui 修复，建议优先合并 |
| [#8069](https://github.com/nearai/ironclaw/pull/8069) | italic-jinxin | OPEN | 3 | 低风险 webui 修复，建议优先合并 |
| [#8070](https://github.com/nearai/ironclaw/pull/8070) | italic-jinxin | OPEN | 3 | 低风险 webui 修复，建议优先合并 |
| [#8071](https://github.com/nearai/ironclaw/pull/8071) | italic-jinxin | OPEN | 3 | 低风险 webui 修复，建议优先合并 |
| [#8076](https://github.com/nearai/ironclaw/pull/8076) | be-student | OPEN | 1 | 功能修复，正常排队 |
| [#8077](https://github.com/nearai/ironclaw/pull/8077) | linhongyu510 | OPEN | 1 | 修复 #8009，建议优先 |
| [#7834](https://github.com/nearai/ironclaw/pull/7834) | dependabot | OPEN | 15 | WASM 依赖批量升级，注意回归测试 |
| [#8078](https://github.com/nearai/ironclaw/pull/8078) | dependabot | OPEN | 1 | Tokio 生态升级，低风险 |
| [#8079](https://github.com/nearai/ironclaw/pull/8079) | dependabot | OPEN | 1 | Actions 组升级，低风险 |
| [#8080](https://github.com/nearai/ironclaw/pull/8080) | dependabot | OPEN | 1 | 通用依赖升级，低风险 |

> **风险提示**：#7834（WASM 组升级）已开放 15 天，属于中等风险依赖变更，建议尽早审核合并或关闭。

---

**报告生成时间：** 2026-09-07  
**数据来源：** [nearai/ironclaw](https://github.com/nearai/ironclaw) GitHub API

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 📊 LobsterAI 项目动态日报
**日期：2026-09-07** | **数据来源：github.com/netease-youdao/LobsterAI**

---

## 1. 今日速览

今日项目整体活跃度处于中低水平：过去24小时内新增 Issue 1 条、处理 PR 1 条，无新版本发布。维护者对测试基础设施的持续优化表明项目正进行代码质量加固，但用户侧功能迭代节奏较为平稳。Issue #1068 已停滞数月，需关注用户体验层面的积压问题。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

**PR #2619** ✅ 已合并 — `test: fix Windows path portability in installer and thumbnail tests`

- **贡献者**：btc69m979y-dotcom
- **内容**：修复将最新 main 合入 OpenClaw v2026.8.1 升级分支后，在 Windows 验收中发现的 4 个测试失败（3 个 macOS 安装器路径用例 + 1 个缩略图队列优先级用例）
- **影响范围**：仅修改两个测试文件，不涉及生产代码、OpenClaw runtime 或 patches
- **项目推进**：解决了跨平台测试兼容性问题，保障了升级分支的验收质量，为后续版本发布扫清了测试层面的障碍

[🔗 PR #2619](https://github.com/netease-youdao/LobsterAI/pull/2619)

---

## 4. 社区热点

| 类型 | 编号 | 标题 | 状态 | 热度 |
|------|------|------|------|------|
| Issue | #1068 | 删除当前 agent 后任务列表未自动刷新 | 🟡 OPEN (stale) | 低（评论 1，👍 0） |

**热点分析**：Issue #1068 反映用户在多 Agent 切换场景下的核心痛点——删除 Agent 后 UI 状态未及时同步，导致任务列表显示异常。该问题已停滞约 5 个月（2026-03-30 创建 → 2026-09-06 更新），可能因优先级较低而被标记为 stale。用户诉求明确：期望删除 Agent 后系统能自动刷新任务列表，提升操作连贯性。

[🔗 Issue #1068](https://github.com/netease-youdao/LobsterAI/issues/1068)

---

## 5. Bug 与稳定性

| 优先级 | Issue | 标题 | 严重程度 | Fix PR |
|--------|-------|------|----------|--------|
| 🟡 中 | #1068 | 删除当前 agent 后切换到别的 agent，任务列表未自动刷新 | 功能缺陷（UI 状态不同步） | 暂无 |

- **今日新增 Bug**：0
- **今日修复 Bug**：0
- **回归风险**：无

> Issue #1068 属于 UX 层面的功能性缺陷，非崩溃类问题，但对多 Agent 工作流用户影响显著。

---

## 6. 功能请求与路线图信号

- **Issue #1068** 暗示用户对 **Agent 管理交互体验** 有持续需求，特别是 Agent 删除后的状态同步机制。若项目后续版本规划涉及 Agent 管理模块优化，此需求可作为优先级参考。
- 当前无明确的新功能 PR 或 RFC，路线图信号较弱。

---

## 7. 用户反馈摘要

**来自 Issue #1068：**

- **使用场景**：用户同时管理多个 Agent，删除非主 Agent 后切换至 `main` Agent
- **痛点**：删除 Agent 后任务列表未自动刷新，导致 `main` Agent 的任务无法立即显示，需手动操作才能恢复
- **满意度**：问题影响日常使用流畅度，用户期望系统具备更智能的状态同步能力

---

## 8. 待处理积压

| Issue/PR | 标题 | 创建时间 | 状态 | 建议关注级别 |
|----------|------|----------|------|--------------|
| #1068 | 删除当前 agent 后任务列表未自动刷新 | 2026-03-30 | 🟡 stale | ⚠️ 中 — 已停滞超 5 个月，影响多 Agent 用户 workflow |

**维护者建议**：
- Issue #1068 虽为 stale 状态，但反映了真实的 UX 痛点，建议评估是否在下一迭代中修复
- 可考虑添加 `auto-refresh` 机制：当检测到当前 Agent 被删除时，自动触发任务列表刷新

---

**📈 项目健康度评估**：测试基础设施持续优化，但用户侧功能迭代节奏较慢，存在中长期未响应用户反馈的积压，建议适度关注用户体验类 Issue 的处理效率。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-09-07

---

## 1. 今日速览

Moltis 项目今日整体活跃度**偏低**。过去 24 小时内无 Issues 更新，无新版本发布，所有活跃变更均集中在 2 条待合并的修复型 PR 上，均由同一贡献者 `be-student` 提交。两个 PR 均属于 bugfix 范畴（TLS 配置修正、执行错误报告优化），无新功能引入。项目目前处于**稳定维护状态**，代码质量在持续打磨，但贡献节奏较为缓慢。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

今日无 PR 被合并或关闭，但存在 **2 条关键修复 PR** 等待审查与合并：

| PR | 类型 | 标题 | 关联 Issue | 状态 |
|----|------|------|-----------|------|
| [#1261](https://github.com/moltis-org/moltis/pull/1261) | Bugfix | `fix(tls): restrict ALPN to HTTP/1.1` | Fixes #245 | OPEN |
| [#1260](https://github.com/moltis-org/moltis/pull/1260) | Bugfix | `fix(exec): report missing shell accurately` | Closes #279 | OPEN |

**进展评估：** 今日无实际合并动作，项目仍处于等待 PR 审查阶段。两个 PR 均已通过测试（`cargo test` / `cargo check` 通过），具备合并条件。

---

## 4. 社区热点

今日无新 Issue，无评论交互。以下两条 PR 为当前唯一关注点：

- **[PR #1261](https://github.com/moltis-org/moltis/pull/1261)** — 限制 TLS 的 ALPN 协商仅 advertise HTTP/1.1，规避 RFC 8441 WebSocket over TLS 升级路径未实现前的兼容性问题。该修复直接回应 [#245](https://github.com/moltis-org/moltis/issues/245)，涉及 TLS 层协议协商的正确性，对依赖 WebSocket 连接的用户有实质影响。

- **[PR #1260](https://github.com/moltis-org/moltis/pull/1260)** — 修复 shell 缺失时的错误分类逻辑，解决"工作目录存在但 `sh` 不在 PATH 中"时的错误掩盖问题。关联 [#279](https://github.com/moltis-org/moltis/issues/279)，提升调试可观测性。

---

## 5. Bug 与稳定性

| 严重级别 | 问题描述 | 关联 Issue | 修复状态 |
|---------|---------|-----------|---------|
| 🟡 中等 | TLS 配置错误 advertise 了当前未支持的 HTTP/2 WebSocket ALPN，可能导致连接异常 | [#245](https://github.com/moltis-org/moltis/issues/245) | ✅ PR #1261 待合并 |
| 🟡 中等 | 执行失败时错误信息不准确，缺失 shell 时可能误判为目录问题 | [#279](https://github.com/moltis-org/moltis/issues/279) | ✅ PR #1260 待合并 |

**稳定性评估：** 今日无崩溃报告或回归反馈，两个待合 PR 均为已知 bug 的修复，合并后预期提升 TLS 配置正确性和执行错误可诊断性。

---

## 6. 功能请求与路线图信号

今日无新功能 Issue 或 PR。从现有 PR 可推断：

- **RFC 8441 WebSocket over TLS 支持**：PR #1261 明确标注当前仅暂限 ALPN 至 HTTP/1.1，待 RFC 8441 支持实现后再扩展。这暗示 WebSocket 升级路径已纳入长期技术规划，但尚未进入近期发布窗口。

- **执行子系统可观测性**：PR #1260 的修复方向表明项目正逐步完善错误分类与诊断体验，符合工具类项目的稳定性优先路线。

---

## 7. 用户反馈摘要

今日无新 Issue 评论，无法提取实时用户反馈。从已修复 Issue 背景可归纳：

- **TLS/HTTP 层用户**：对 ALPN 协商行为的准确性有明确要求，不希望因配置错误导致连接降级或失败。
- **执行环境用户**：关注工具在缺失依赖（如 `sh`）时的错误提示是否清晰，影响故障排查效率。

---

## 8. 待处理积压

| 类型 | 编号 | 标题 | 创建时间 | 备注 |
|------|------|------|---------|------|
| PR | [#1261](https://github.com/moltis-org/moltis/pull/1261) | `fix(tls): restrict ALPN to HTTP/1.1` | 2026-09-06 | 已验证，等待维护者审查 |
| PR | [#1260](https://github.com/moltis-org/moltis/pull/1260) | `fix(exec): report missing shell accurately` | 2026-09-06 | 已验证，等待维护者审查 |

> 两个 PR 均创建于昨日，距今约 1 天，尚未进入审查流程。建议维护者优先处理，这两个修复对 TLS 稳定性和错误诊断均有直接价值。

---

**项目健康度评分：🟡 中等** — 代码质量稳定，修复 PR 具备合并条件，但审查节奏偏慢，社区互动活跃度有待提升。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-09-07

## 1. 今日速览

CoPaw 项目今日保持中高活跃度：过去24小时新增/活跃 Issues 20条、关闭 11条；PR 待合并 20条、合并/关闭 6条，无新版本发布。社区反馈集中在上下文管理稳定性（多条重复报告上下文丢失/压缩问题）、Telegram/飞书渠道渲染异常，以及工具调用异常栈被静默吞没的可观测性缺陷。首次贡献者（kabishou11、Bruce-Yii）提交了4条 PR，社区参与度良好。整体健康度：**注意**，多个稳定性相关 Issue 集中涌现，需优先处理。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已关闭/合并 PR（6条）

| PR | 类型 | 摘要 |
|----|------|------|
| [#7086](https://github.com/agentscope-ai/QwenPaw/pull/7086) | fix | 统一 Console 顶部语言下拉与侧边栏设置的语言选项（补全 Bahasa Indonesia、Tiếng Việt） |
| [#7595](https://github.com/agentscope-ai/QwenPaw/pull/7595) | fix | 将语言配置抽离为共享模块，彻底解决语言选择器不一致问题 |
| [#7584](https://github.com/agentscope-ai/QwenPaw/issue/7584) | — | 与 #7579 合并追踪的上下文丢失严重 Bug 暂时关闭（待 review） |
| [#7447](https://github.com/agentscope-ai/QwenPaw/issue/7447) | — | 长上下文早期记录丢失问题关闭（疑似与 #7579 同类） |
| [#7505](https://github.com/agentscope-ai/QwenPaw/issue/7505) | — | LM Studio LAN 连接 client disconnect 问题关闭（用户自行解决或暂挂） |
| [#6820](https://github.com/agentscope-ai/QwenPaw/issue/6820) | — | 前端 UI 输出/工具调用/思考过程不实时显示问题关闭 |

### 关键待合并 PR 动向

- **#7561** — 统一 Memory 生命周期管理（breaking refactor），涉及自动捕获、召回、后台执行的职责分离，影响面较大
- **#7578** — 修复 `_coordinator.py` `_drain()` 异常栈吞没问题（对应 #7572），首次贡献者提交
- **#7577** — 修复任务运行中发新消息触发 409 错误（对应 #7559），改为入队处理
- **#7593** — 恢复 v2.1.0 主工作目录直接路径输入功能（对应 #7588）
- **#7590/#7592/#7591** — Telegram/飞书渠道三项修复：Markdown 表格渲染、中间消息可选清理、推理卡片自动折叠

---

## 4. 社区热点

### 高讨论度 Issues

| Issue | 状态 | 评论数 | 核心议题 |
|-------|------|--------|----------|
| [#7505](https://github.com/agentscope-ai/QwenPaw/issues/7505) | CLOSED | 12 | LAN 部署 LM Studio 时 qwenpaw 频繁 client disconnect |
| [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | OPEN | 8 | 主 Agent+多子 Agent 模式下，主 Agent 不主动查询子任务状态，需用户追问 |
| [#7559](https://github.com/agentscope-ai/QwenPaw/issues/7559) | OPEN | 5 | 任务运行中提交新消息触发 409，而非入队等待 |
| [#6820](https://github.com/agentscope-ai/QwenPaw/issues/6820) | CLOSED | 5 | 前端 UI 不实时展示模型输出/工具调用/思考过程 |
| [#7363](https://github.com/agentscope-ai/QwenPaw/issues/7363) | OPEN | 4 | Windows 同步调用阻塞事件循环，启动/发消息卡顿 118-135s |
| [#6814](https://github.com/agentscope-ai/QwenPaw/issues/6814) | CLOSED | 4 | macOS 打开 Scroll history.db 时 sqlite3 SIGBUS 崩溃 |

**热点分析：**
- **上下文管理** 是社区最关注的痛点：#7450（子 Agent 状态不主动查询）、#7447/#7579（上下文丢失）、#6541（压缩触发 MODEL_EXECUTION_ERROR）形成问题群，反映当前多 Agent 协作和长上下文场景的稳定性不足。
- **工具调用异常不可观测**（#7572）引发开发者关注，涉及生产环境的故障定位能力。
- **用户体验回归**：#7588 反映 v2.2 相比 v2.1 工作目录选择 UX 退化，用户强烈要求恢复。

---

## 5. Bug 与稳定性

### 🔴 严重

| Issue | 描述 | Fix PR |
|-------|------|--------|
| [#7579](https://github.com/agentscope-ai/QwenPaw/issues/7579) | 模型回复已持久化但后续请求中缺失，AI"看不到自己刚说的话"，陷入 toolcall 死循环 | 无 |
| [#7584](https://github.com/agentscope-ai/QwenPaw/issues/7584) | 同上问题的强化报告（重复输出、行为错乱） | 已关闭，追踪至 #7579 |
| [#7363](https://github.com/agentscope-ai/QwenPaw/issues/7363) | 同步调用阻塞事件循环，Windows 启动/发消息卡顿 2 分钟以上，timeout 失效 | 无 |
| [#6814](https://github.com/agentscope-ai/QwenPaw/issues/6814) | macOS SQLite WAL 模式打开 history.db 触发 SIGBUS 崩溃 | 无 |

### 🟠 高优先级

| Issue | 描述 | Fix PR |
|-------|------|--------|
| [#7572](https://github.com/agentscope-ai/QwenPaw/issues/7572) | 工具派发层 `_drain()` 吞没异常栈，故障无法定位 | [#7578](https://github.com/agentscope-ai/QwenPaw/pull/7578) ✅ |
| [#7559](https://github.com/agentscope-ai/QwenPaw/issues/7559) | 任务运行中提交消息触发 409 错误 | [#7577](https://github.com/agentscope-ai/QwenPaw/pull/7577) ✅ |
| [#7587](https://github.com/agentscope-ai/QwenPaw/issues/7587) | WUSRouter OpenAI-compatible provider 返回 Cloudflare 403 | 无 |
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | RetryChatModel 硬编码 32768 context_size fallback，所有模型受影响 | 无 |
| [#6541](https://github.com/agentscope-ai/QwenPaw/issues/6541) | DeepSeek scroll 压缩上下文触发 MODEL_EXECUTION_ERROR（role 错误） | 无 |
| [#7596](https://github.com/agentscope-ai/QwenPaw/issues/7596) | history.db FTS 全文索引静默损坏，retention purge 每次启动失败 | 无 |
| [#7589](https://github.com/agentscope-ai/QwenPaw/issues/7589) | Heartbeat cron session 消息重复堆积导致 Agent 无响应约 2 小时 | 无 |

### 🟡 中等

| Issue | 描述 | Fix PR |
|-------|------|--------|
| [#7585](https://github.com/agentscope-ai/QwenPaw/issues/7585) | Telegram Markdown 表格原样输出管道符 | [#7590](https://github.com/agentscope-ai/QwenPaw/pull/7590) ✅ |
| [#7513](https://github.com/agentscope-ai/QwenPaw/issues/7513) | DeepSeek-v4-pro 工具调用与回复混合显示异常 | 无 |
| [#7597](https://github.com/agentscope-ai/QwenPaw/issues/7597) | 工具返回图片/PDF二进制以 bare base64 发送触发 400 | 无 |
| [#7567](https://github.com/agentscope-ai/QwenPaw/issues/7567) | 点击停止后 UI 显示已停但实际仍在执行 | 已关闭 |
| [#7548](https://github.com/agentscope-ai/QwenPaw/issues/7548) | 对话切换/重启后导航记录丢失 | 已关闭 |
| [#7594](https://github.com/agentscope-ai/QwenPaw/issues/7594) | 任务执行情况分重复输出3次 | 已关闭 |

### 稳定性总评

今日新增 12 个 Open Bug Issue，其中 4 个为严重级别（上下文丢失、事件循环阻塞、SIGBUS 崩溃、异常栈吞没）。已有 3 条 Fix PR 正在合并流程（#7578、#7577、#7590），但核心上下文管理问题尚未有修复方案。**稳定性风险较高**。

---

## 6. 功能请求与路线图信号

| Issue | 需求 | 关联 PR | 纳入可能性 |
|-------|------|---------|-----------|
| [#7580](https://github.com/agentscope-ai/QwenPaw/issues/7580) | 阻塞式等待子 Agent 任务完成的内置 Tool（替代轮询 check_agent_task） | 无 | ⭐⭐⭐ 高 — 多 Agent 场景刚需 |
| [#7588](https://github.com/agentscope-ai/QwenPaw/issues/7588) | 恢复 v2.1.0 主工作目录直接路径输入 | [#7593](https://github.com/agentscope-ai/QwenPaw/pull/7593) | ⭐⭐⭐⭐ 极高 — 已有 PR |
| [#7570](https://github.com/agentscope-ai/QwenPaw/issues/7570) | 飞书思考卡片流式结束后自动折叠 | [#7591](https://github.com/agentscope-ai/QwenPaw/pull/7591) | ⭐⭐⭐⭐ 极高 — 已有 PR |
| [#7586](https://github.com/agentscope-ai/QwenPaw/issues/7586) | Telegram 最终回复后自动清理中间消息 | [#7592](https://github.com/agentscope-ai/QwenPaw/pull/7592) | ⭐⭐⭐⭐ 极高 — 已有 PR |
| [#7582](https://github.com/agentscope-ai/QwenPaw/issues/7582) | 插件商店一键更新按钮和更新通知 | 无 | ⭐⭐ 中 — 体验优化 |
| [#7583](https://github.com/agentscope-ai/QwenPaw/issues/7583) | 社区登录、信箱、快速反馈联动 AgentScope 社区 | 无 | ⭐⭐ 中 — 生态建设 |
| [#4077](https://github.com/agentscope-ai/QwenPaw/issues/4077) | UI 字体缩放 + 文件路径超链接 | 无 | ⭐⭐ 中 — 长期 QoL |

**路线图信号：**
- **#7569（Advisor Mode）** — 新增双模型协作模式（强模型规划+弱模型执行），是一个值得关注的架构级功能
- **#7509（Make Skill v2）** — Skill 创建工作流升级为审批驱动，反映项目对可复用组件规范的加强
- **#7486（Creator 1.1.2）** — 包含 runtime notification bus、A/B 对比、T2V/I2V/S2V 调度等专业媒体能力，Creator 模块持续迭代

---

## 7. 用户反馈摘要

### 核心痛点

1. **上下文管理不靠谱**：多个用户报告上下文意外丢失（#7447、#7579、#7584），导致任务中断、AI 行为错乱、陷入死循环。这是当前最严重的用户信任问题。

2. **多 Agent 协作缺乏主动性**：#7450 反映主 Agent 在子 Agent 执行期间不主动查询进度，需用户反复追问，严重影响长任务体验。

3. **异常不可观测**：#7572 指出工具调用异常被静默吞没，运维和开发者无法定位故障根源，#7363 反映同步调用阻塞导致界面假死。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw 项目动态日报
**日期：2026-09-07**

---

## 1. 今日速览

ZeptoClaw 今日整体活跃度处于**低水平**。过去24小时内仅有 1 条 Issue 更新，无 PR 合并或关闭，无新版本发布。项目核心维护者 `qhkm` 持续跟进安全问题，当前焦点集中于子智能体委派机制中的权限继承风险。整体来看，项目处于功能迭代间隙期，社区贡献节奏放缓。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 合并或关闭记录。项目代码库在技术实现层面暂无新提交推进。

---

## 4. 社区热点

### 🔴 Issue #664 — 代理论能力继承（高优先级安全议题）

**链接：** [Issue #664](https://github.com/qhkm/zeptoclaw/issues/664)

| 属性 | 详情 |
|------|------|
| 状态 | OPEN |
| 标签 | `area:safety`, `P2-high`, `M` |
| 作者 | qhkm |
| 创建 | 2026-09-05 |
| 最近更新 | 2026-09-06 |
| 评论数 | 1 |

**核心诉求：** 当前 ZeptoClaw 的子智能体委派框架（`src/tools/delegate.rs`）在并发执行、递归阻止和会话隔离方面已有良好基础，但存在**策略继承缺口**——子智能体不应继承超出父策略权限的能力。该 Issue 提出了对委托工具注册表的审计需求，并呼吁建立严格的策略边界约束机制。

**分析：** 作为维护者亲自发起的 Issue，此议题具有较高优先级，可能成为下一版本安全加固的核心方向。

---

## 5. Bug 与稳定性

今日无新报告的 Bug 或崩溃问题。

---

## 6. 功能请求与路线图信号

**Issue #664** 反映了当前系统在安全策略层面的关键缺口。结合 Issue 描述中提到的已有实现基础（`delegate.rs:32–53, 153–250, 254–358`），预计下一版本（可能为 `vX.Y.0`）将围绕以下方向推进：

- **策略继承控制层**：在子智能体创建时强制策略裁剪
- **能力审计机制**：追踪委派链中的权限传播路径
- **安全策略验证框架**：形式化验证子策略 ≤ 父策略

---

## 7. 用户反馈摘要

今日 Issue #664 仅有 1 条评论，反馈量有限。从 Issue 正文可提炼以下用户/开发者关注点：

- **满意点**：现有委派机制在并发执行、递归阻止和会话隔离方面已具备良好基础
- **痛点**：策略边界不清晰，存在子智能体权限越界的安全风险
- **使用场景**：多智能体协作系统中，用户对安全边界和权限控制的诉求强烈

---

## 8. 待处理积压

| Issue/PR | 状态 | 更新时间 | 优先级 | 备注 |
|----------|------|----------|--------|------|
| [#664](https://github.com/qhkm/zeptoclaw/issues/664) | OPEN | 2026-09-06 | P2-high | 安全核心议题，建议优先响应 |

**维护者关注建议：**
- Issue #664 已创建 2 天，有 1 条评论但尚未有 PR 跟进，建议维护者评估并指派开发任务
- 当前缺乏社区贡献者介入的安全类 Issue，建议公开悬赏或细化实现方案以吸引参与者

---

**项目健康度评估：** 🟡 正常偏低 — 核心维护者活跃但社区贡献沉寂，安全问题亟待推进。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

⚠️ 摘要生成失败。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*