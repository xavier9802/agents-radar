# OpenClaw 生态日报 2026-08-19

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-19 01:40 UTC

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
**日期：2026-08-19** | 数据来源：github.com/openclaw/openclaw

---

## 1. 今日速览

OpenClaw 项目今日保持**极高活跃度**，过去24小时内 Issues 更新 500 条（活跃 478 条、新关闭 22 条），PR 更新 500 条（待合并 402 条、已合并/关闭 98 条），社区参与热度稳定。项目当前处于 **2026.7.x 版本周期**，无新版本发布，但核心稳定性修复持续推进。今日 Issues 讨论焦点集中在 session-state 状态管理、SQLite 事务阻塞、认证恢复后工作区迁移失败等 P0/P1 级问题，反映用户对生产环境稳定性的强烈诉求。98 个 PR 已合并，涵盖 auth 修复、UI 稳定性改进、Gateway 重启恢复等关键路径，项目整体向前推进明显。

---

## 2. 版本发布

**无新版本发布。**

当前最新稳定版本为 `2026.7.1-2`，用户反馈该版本存在启动迁移预检阻塞 Gateway 的问题（#112395），维护团队正在跟进修复。

---

## 3. 项目进展

### 已合并/关闭 PR 概览（98 条）

今日已合并的重要修复 PR：

| PR | 类型 | 摘要 | 链接 |
|---|---|---|---|
| #124014 | fix(auth) | 重新认证时仅重置被替换的 profile，避免误清除其他有效凭据 | [PR #124014](https://github.com/openclaw/openclaw/pull/124014) |
| #125528 | fix(claude-cli) | 应用 thinking 级别并保持 live session 预热，提升 prompt-cache 复用率 | [PR #125528](https://github.com/openclaw/openclaw/pull/125528) |
| #116327 | fix(agents) | 心跳响应前预加载 context assembly，避免大量原始消息返回 | [PR #116327](https://github.com/openclaw/openclaw/pull/116327) |
| #125904 | fix(sessions) | 修复 session 创建/修改后 Gateway 已提交但客户端收到拒绝的问题 | [PR #125904](https://github.com/openclaw/openclaw/pull/125904) |
| #125909 | fix(apps) | 改进 iOS/macOS 原生 Gateway 连接失败时的错误可见性 | [PR #125909](https://github.com/openclaw/openclaw/pull/125909) |
| #116489 | feat(security) | 安装策略警告需显式确认，提升插件安装安全性 | [PR #116489](https://github.com/openclaw/openclaw/pull/116489) |
| #123189 | fix(gateway) | 恢复 chat 启动时 embedded channel run 的状态投影 | [PR #123189](https://github.com/openclaw/openclaw/pull/123189) |
| #116337 | fix(gateway) | 客户端断开后继续完成媒体预处理器任务，避免资源泄漏 | [PR #116337](https://github.com/openclaw/openclaw/pull/116337) |

**进展评估**：今日合并的 PR 主要集中在**认证状态管理、session 恢复、原生应用错误可见性**三大关键路径，对生产环境稳定性有实质提升。待合并 PR 402 条，表明开发团队正在积极处理大量修复请求。

---

## 4. 社区热点

### 评论最多的 Issues（Top 10）

| Issue | 标题摘要 | 评论数 | 评级 | 链接 |
|---|---|---|---|---|
| #116201 | Realtime voice 会话保留无界 provider/consult 状态 | 60 | 🦞 diamond lobster | [Issue #116201](https://github.com/openclaw/openclaw/issues/116201) |
| #77598 | 跟踪 live dev agent 行为与轨迹（观察性监控） | 23 | 🦪 silver shellfish | [Issue #77598](https://github.com/openclaw/openclaw/issues/77598) |
| #112423 | 大型 SQLite transcript 清理阻塞 Gateway 事件循环 | 16 | 🦞 diamond lobster | [Issue #112423](https://github.com/openclaw/openclaw/issues/112423) |
| #115908 | Session transcript projection 在持续写入下 livelock | 15 | 🦞 diamond lobster | [Issue #115908](https://github.com/openclaw/openclaw/issues/115908) |
| #101290 | CLI 启动预检在 Gateway 运行时损坏 SQLite DB | 15 | 🦪 silver shellfish (已关闭) | [Issue #101290](https://github.com/openclaw/openclaw/issues/101290) |

### 社区热点分析

1. **Realtime Voice 状态管理**（#116201）— 60 条评论，最高活跃。用户反映语音会话在 provider 响应缓慢或突发时，会累积过剩的 consult 状态和音频帧，导致资源泄漏。这是实时语音功能走向生产的关键阻塞点。

2. **SQLite 事务阻塞 Gateway 事件循环**（#112423、#115908）— 两个高评论 Issue 均指向同一架构问题：同步 SQLite 操作阻塞 Node.js 主线程。这已是 6.x 版本的遗留债务，影响所有使用 SQLite 后端的用户。

3. **Dev Agent 行为监控**（#77598）— 23 条评论，反映社区对 agent 可观测性的强烈需求。用户希望建立长期观察机制来理解 agent 在无人干预下的行为模式。

---

## 5. Bug 与稳定性

### 高严重度 Bug 列表（按评级排序）

| Issue | 标题 | 严重度 | 状态 | Fix PR | 链接 |
|---|---|---|---|---|---|
| #101290 | CLI 启动预检损坏 live state DB（macOS） | P0 🦪 | 已关闭 | — | [Issue #101290](https://github.com/openclaw/openclaw/issues/101290) |
| #112395 | 6.11→7.1 升级后迁移预检阻塞 Gateway 启动 | P0 🦞 | 活跃 | — | [Issue #112395](https://github.com/openclaw/openclaw/issues/112395) |
| #115424 | Gateway V8 heap OOM 后重启恢复陷入 core dump 循环 | P1 🐚 | 活跃 | — | [Issue #115424](https://github.com/openclaw/openclaw/issues/115424) |
| #116201 | Realtime voice 无界状态保留 | P1 🦞 | 活跃 | — | [Issue #116201](https://github.com/openclaw/openclaw/issues/116201) |
| #115908 | Session transcript projection livelock | P1 🦞 | 活跃 | — | [Issue #115908](https://github.com/openclaw/openclaw/issues/115908) |
| #112423 | 大型 SQLite transcript 清理阻塞事件循环 | P1 🦞 | 活跃 | — | [Issue #112423](https://github.com/openclaw/openclaw/issues/112423) |
| #111498 | Anthropic auth 恢复后主 agent 被 workspace-state 迁移阻塞 | P1 🐚 | 活跃 | — | [Issue #111498](https://github.com/openclaw/openclaw/issues/111498) |
| #88657 | DeepSeek V4 Flash 不完整 turn（payloads=0） | P2 🦪 | 活跃 | — | [Issue #88657](https://github.com/openclaw/openclaw/issues/88657) |
| #125570 | Skill Workshop update 覆盖 live skill description | P1 🦞 | 活跃 | — | [Issue #125570](https://github.com/openclaw/openclaw/issues/125570) |

### 稳定性评估

- **SQLite 事务问题**是当前最大风险点：#112423 和 #115908 均涉及同步数据库操作阻塞主线程，可能导致 Gateway 整体无响应。
- **重启恢复路径**存在缺陷：#115424 和 #112395 反映升级和崩溃恢复流程不够健壮，可能将单次故障转化为持续故障循环。
- **认证相关回归**：#38327（Google Vertex 崩溃）、#111498（Anthropic 工作区迁移）表明 auth 恢复路径需要更严格的测试覆盖。

---

## 6. 功能请求与路线图信号

### 活跃功能请求

| Issue | 需求摘要 | 评论数 | 优先级 | 链接 | 相关 PR |
|---|---|---|---|---|---|
| #79902 | 为 SQLite transcript/session 添加 companion-friendly 接口 | 14 | P3 | [Issue #79902](https://github.com/openclaw/openclaw/issues/79902) | — |
| #6757 | Agent 自主触发 context compaction（self-compact tool） | 8 | P2 | [Issue #6757](https://github.com/openclaw/openclaw/issues/6757) | — |
| #45508 | Webchat 支持自托管 STT/TTS provider | 7 | P2 | [Issue #45508](https://github.com/openclaw/openclaw/issues/45508) | — |
| #95724 | Memory 按 source directory 索引而非按 agent | 6 | P2 | [Issue #95724](https://github.com/openclaw/openclaw/issues/95724) | — |
| #49259 | Dashboard 清理过期孤立 session | 7 | P3 | [Issue #49259](https://github.com/openclaw/openclaw/issues/49259) | — |

### 路线图信号分析

1. **Session 状态可观测性**（#79902）— 高级用户希望基于 canonical runtime state 构建工具，而非解析内部 blob。这与 #126074（暴露 sidebar category controls）形成呼应，表明 session 管理 API 是近期重点。

2. **Agent 自主上下文管理**（#6757）— 用户希望 agent 能自主触发 context compaction，减少对人工 `/compact` 命令的依赖。这符合项目向更自主 agent 演进的方向。

3. **多 agent 共享 memory index**（#95724）— 当前每个 agent 维护独立向量索引，相同 workspace 下产生冗余。该功能请求若实现，将显著降低存储开销。

---

## 7. 用户反馈摘要

### 主要痛点

1. **SQLite 阻塞问题**（#112423、#115908）：
   > "Under sustained transcript write load, the session transcript projection can enter a non-converging rebuild cycle that occupies the Node main thread... the event loop stalls for tens of seconds"
   
   用户反映在生产环境中，持续写入负载会导致 Gateway 事件循环阻塞数十秒，影响所有 channel transport。

2. **认证恢复后的工作区迁移卡死**（#111498）：
   > "Main agent refuses every Anthropic turn even though its anthropic:default credential is reported effective"
   
   macOS 用户在 Anthropic auth 恢复后，TUI 和 CLI 均卡在 legacy workspace-state 迁移步骤，导致 agent 完全不可用。

3. **大型附件导致堆溢出**（#115424）：
   > "Gateway to FATAL ERROR: Reached heap limit Allocation failed - JavaScript heap out of memory"
   
   长会话中的大型附件处理触发 V8 堆溢出，且重启恢复机制将单次崩溃转化为多核心 dump 循环。

4. **Cron 任务通知疲劳**（#90595）：
   > "Cron run 'failed' notifications fire during hot reload and during retries"
   
   热重载和重试期间触发失败通知，导致用户收到大量误报告警。

### 正面反馈

- **Auth 修复**（#124014）：用户认可"仅重置被替换的 profile"的精细策略，避免了过去全量清除凭据的粗暴行为。
- **Claude CLI thinking 支持**（#125528）：end-to-end thinking level 应用和 live session 保持功能获得积极评价。
- **安全安装确认**（#116489）：外部 install policy 返回 warn 级别后需显式确认，提升了插件安装的安全性体验。

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 天数未响应 | 严重度 | 状态 | 链接 |
|---|---|---|---|---|---|
| #38327 | 2026-03-06 | ~166 天 | 🐚 platinum hermit | 活跃 | [Issue #38327](https://github.com/openclaw/openclaw/issues/38327) |
| #77598 | 2026-05-05 | ~106 天 | 🦪 silver shellfish | 活跃 | [Issue #77598](https://github.com/openclaw/openclaw/issues/77598) |
| #79902 | 2026-05-09 | ~102 天 | 🌊 off-meta tidepool | 活跃 | [Issue #79902](https://github.com/openclaw/openclaw/issues/79902) |
| #6757 | 2026-02-02 | ~198 天 | 🌊 off-meta tidepool | 活跃 | [Issue #6757](https://github.com/openclaw/openclaw/issues/6757) |
| #45508 | 2026-03-13 | ~159 天 | 🦞 diamond lobster | 活跃 | [Issue #45508](https://github.com/openclaw/openclaw/issues/45508) |

### 维护者关注建议

1. **#38327**（Google Vertex 崩溃）— 已标记 166 天未解决，影响使用 google-vertex/gemini-3.1-pro-preview 的用户，建议优先处理。

2. **#112395**（7.1 升级阻塞）— P0 级启动问题，直接影响升级用户，建议纳入下一补丁版本修复。

3. **#116201**（Realtime voice 状态泄漏）— 60 条评论的高活跃 Issue，涉及实时语音功能的核心稳定性，建议安排专项修复。

4. **SQLite 事务架构问题**（#112423、#115908）— 两个独立 Issue 指向同一根因，建议维护团队评估是否需要在架构层面将同步 SQLite 操作移至工作线程。

---

**日报生成时间**：2026-08-19 | **分析师**：Agnes-2.0-Flash | **数据范围**：过去 24 小时 GitHub 活动

---

## 横向生态对比



# 个人 AI 助手/自主智能体开源生态横向对比分析
**日期：2026-08-19** | **分析师：Agnes-2.0-Flash**

---

## 1. 生态全景

2026年8月，个人AI助手与自主智能体开源生态呈现**高密度迭代与稳定性焦虑并存**的特征。头部项目（OpenClaw、Hermes、CoPaw、ZeroClaw）日活跃度保持在百级别，社区问题从功能探索转向生产级稳定性验证；SQLite阻塞、认证恢复、跨平台兼容性成为共性痛点。同时，生态分化明显：部分项目（如IronClaw、Moltis）已进入架构重构期，而小众项目（NullClaw、ZeptoClaw）趋于沉寂。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | Release | 健康度 | 核心关注点 |
|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 无 | 🟡 活跃但P0积压 | SQLite阻塞、认证恢复、Session管理 |
| **Hermes Agent** | 50 | 50 | v0.20.4 | 🟢 稳定收敛 | 桌面端稳定性、Windows平台Bug |
| **CoPaw** | 45 | 50 | 无 | 🟡 v2.1.0后密集修复 | MCP/Channel连接、沙箱兼容 |
| **ZeroClaw** | 50 | 50 | 无 | 🟢 RFC驱动演进 | 架构收敛、安全策略、Provider扩展 |
| **IronClaw** | 21 | 40 | v1.3.0-rc.2 | 🟢 架构重构期 | 设计系统、Memory集成、沙箱方案 |
| **NanoBot** | 10 | 28 | 无 | 🟢 快速迭代 | 搜索扩展、AgentLoop生命周期 |
| **Moltis** | ~5 | 5 | 20260818.08 | 🟢 稳健增长 | 文件管理、Podman兼容 |
| **PicoClaw** | 6 | 4 | 无 | 🟡 维护响应慢 | 多Agent路由、配置解析 |
| **NullClaw** | 0 | 0 | 无 | 🔴 无活动 | — |
| **ZeptoClaw** | 0 | 0 | 无 | 🔴 无活动 | — |

---

## 3. OpenClaw 在生态中的定位

**定位：生产级个人AI助手框架，技术深度与社区规模双领先**

| 维度 | OpenClaw | 同类对比 |
|---|---|---|
| **社区规模** | 日活Issues/PRs 500+，远超其他项目（10-50量级） | NanoBot/Moltis为次梯队，PicoClaw/NullClaw为边缘 |
| **技术深度** | 聚焦Session状态管理、SQLite事务、认证恢复等底层问题 | Hermes聚焦桌面体验，IronClaw聚焦架构设计，CoPaw聚焦渠道集成 |
| **问题类型** | P0级稳定性问题为主（阻塞、OOM、重启循环） | 其他项目以功能扩展和体验优化为主 |
| **演进阶段** | 生产环境稳定性攻坚期 | Hermes/Moltis处于功能完善期，IronClaw处于架构重构期 |

**核心优势：**
- 最大社区活跃度与最密集的贡献者网络
- 覆盖Gateway/CLI/Desktop多端，技术栈最完整
- 问题暴露充分，社区反馈驱动修复效率较高（98个PR已合并）

**技术路线差异：**
- OpenClaw：事件循环架构 + SQLite持久化，聚焦长会话稳定性
- Hermes：多Profile + Desktop-first，聚焦桌面用户体验
- IronClaw：模块化解耦 + 设计系统重构，聚焦企业级架构
- CoPaw：Channel/MCP集成优先，聚焦多端接入能力
- ZeroClaw：RFC驱动 + 多引擎协调，聚焦架构演进路径

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|---|---|---|
| **Session/上下文持久化** | OpenClaw、Hermes、IronClaw、ZeroClaw | OpenClaw：session-state管理、transcript projection；Hermes：session恢复4030错误；IronClaw：跨会话记忆召回；ZeroClaw：session-scoped持久化prompt |
| **跨平台兼容性** | OpenClaw、NanoBot、Hermes、ZeroClaw | OpenClaw：macOS auth恢复后工作区迁移；NanoBot：Windows venv PID交接；Hermes：Windows profile切换静默失败；ZeroClaw：Windows测试74项失败 |
| **认证与凭据管理** | OpenClaw、NanoBot、CoPaw、ZeroClaw | OpenClaw：Anthropic auth恢复阻塞；NanoBot：API凭证自动刷新；CoPaw：OAuth2 refresh_token持久化；ZeroClaw：Google STT API Key泄露 |
| **资源隔离与沙箱** | NanoBot、CoPaw、IronClaw、ZeroClaw | NanoBot：Shell子进程无资源限制（fork bomb风险）；CoPaw：沙箱uv写入权限；IronClaw：CLI沙箱方案Epic；ZeroClaw：Podman escape hatches |
| **可观测性与稳定性** | OpenClaw、NanoBot、Hermes、ZeroClaw | OpenClaw：Realtime voice状态泄漏（60评论）；NanoBot：AgentLoop后台任务异常吞掉；Hermes：Skills索引老化（54评论）；ZeroClaw：Goal mode可观测性 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构 |
|---|---|---|---|
| **OpenClaw** | 全功能个人AI助手，Gateway/CLI/Desktop三端 | 技术用户、生产环境部署者 | Node.js事件循环 + SQLite，长会话优化 |
| **Hermes Agent** | 桌面体验优先，多Profile管理 | macOS/Linux桌面用户 | Electron + 多Profile隔离 |
| **IronClaw** | 企业级架构，设计系统重构 | 企业用户、多团队协作 | 模块化架构，Storybook设计系统 |
| **CoPaw** | 多渠道集成（Matrix/飞书等），插件生态 | 多渠道部署场景 | MCP/Channels优先，插件API |
| **NanoBot** | 搜索能力扩展，AgentLoop生命周期 | 开发者、自动化场景 | Python异步框架，多搜索引擎聚合 |
| **ZeroClaw** | RFC驱动架构演进，多引擎协调 | 架构研究者、早期采用者 | Rust，多引擎统一RFC |
| **Moltis** | 轻量级，文件管理扩展 | 开发工具集成场景 | 文件持久化 + 容器兼容 |
| **PicoClaw** | 轻量级，协议兼容性 | 嵌入式/边缘部署 | Anthropic原生协议支持 |

---

## 6. 社区热度与成熟度分层

```
🟢 快速迭代期（高频新功能+架构重构）
   └── ZeroClaw (RFC驱动)、IronClaw (v1.4.0 Epic)、NanoBot (搜索扩展)

🟡 稳定性攻坚期（P0问题密集+生产验证）
   └── OpenClaw (SQLite/OOM)、CoPaw (v2.1.0回归修复)、Hermes (Windows/桌面Bug)

🟢 稳健成熟期（低Bug率+健康发布节奏）
   └── Moltis (Issue闭环率高)、PicoClaw (中等活跃)

🔴 低活跃/停滞期
   └── NullClaw (无活动)、ZeptoClaw (无活动)
```

**成熟度评估：**
- **OpenClaw**：社区规模最大但技术债累积（SQLite遗留问题6.x版本至今），处于**规模扩张后的稳定性收敛期**
- **Hermes**：v0.20.4发布后进入稳定期，但Windows/桌面端问题暴露**平台适配成熟度待提升**
- **IronClaw**：架构重构期，v1.3.0→v1.4.0演进清晰，**工程成熟度高**
- **ZeroClaw**：RFC驱动敏捷演进，**技术前瞻性强但用户基数较小**
- **NanoBot/Moltis**：垂直领域深耕，**生态位明确**

---

## 7. 值得关注的趋势信号

### 7.1 生产稳定性成为核心瓶颈
OpenClaw的SQLite阻塞（#112423）、CoPaw的会话冻结（#7102）、IronClaw的自动化运行不稳定（#6879）共同指向：**Agent系统的长会话持久化与资源管理仍是行业级挑战**。开发者应关注异步化、工作线程隔离等架构模式。

### 7.2 跨平台兼容性摩擦加剧
三个项目（OpenClaw/macOS、Hermes/Windows、ZeroClaw/Windows）均报告平台特定Bug，且Windows端问题占比显著。建议开发者在CI中增加多平台测试覆盖，关注路径语义、编码、权限等底层差异。

### 7.3 安全边界与资源隔离成为必答题
NanoBot的Shell fork bomb风险（#4797）、CoPaw的沙箱写入权限（#7005）、IronClaw的CLI沙箱Epic表明：**Agent工具调用权限控制已从可选项变为必选项**。cgroups/ulimit等OS级隔离将被广泛采用。

### 7.4 搜索能力多元化与聚合
NanoBot同时推进Serply（#5437）和mst-python（#5234）两个搜索PR，反映社区对**多引擎聚合+RRF融合**的需求强烈。未来搜索提供者的抽象层设计将成为差异化竞争点。

### 7.5 Session状态管理API化
OpenClaw（#79902）、Hermes（#88897）、ZeroClaw（#9998）均涉及Session状态的可观测性与API暴露。建议开发者关注**canonical runtime state**的标准抽象，避免内部blob解析的脆弱性。

### 7.6 小模型稳定性差异显现
IronClaw（#6879）报告DeepSeek V4 Flash小模型执行结果不一致，CoPaw（#7102）报告glm模型冻结。趋势显示：**任务复杂度与小模型可靠性之间存在明显张力**，多步任务的容错与恢复机制将成为关键能力。

---

**总结：** 个人AI助手开源生态正处于从"功能竞争"向"稳定性竞争"过渡的关键阶段。OpenClaw凭借社区规模占据生态中心，但技术债治理压力显著；Hermes/IronClaw分别聚焦桌面体验和企业架构，形成差异化定位；ZeroClaw以RFC驱动保持技术前沿性。对开发者而言，Session管理、跨平台兼容、资源隔离是三大必攻克领域。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-19

---

## 1. 今日速览

过去24小时 NanoBot 项目保持**高活跃状态**：共更新 38 条社区动态（10 Issues + 28 PRs），其中 7 条 Issue 活跃/新开，6 条 PR 已合并/关闭。今天没有新版本发布，但维护团队在处理一批关键的稳定性修复（AgentLoop 后台任务管理、Windows venv 适配）和功能扩展（新增 Serply/mst-python 搜索提供者）。整体来看，项目在**异步任务生命周期管理**和**跨平台兼容性**两个方向上取得了实质性推进，同时社区对 LangSmith 集成回归和用户控制权增强有明确诉求。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR（3 条）

| PR | 作者 | 内容 | 关联 Issue |
|---|---|---|---|
| [#5434](https://github.com/HKUDS/nanobot/pull/5434) | Shizoqua | Mattermost 系统帖子过滤：防止频道加入/离开通知被当作用户消息处理 | — |
| [#5433](https://github.com/HKUDS/nanobot/pull/5433) | chengyongru | 测试修复：用输出感知等待替换 write_stdin 截断测试中的固定 500ms 轮询 | — |
| [#5358](https://github.com/HKUDS/nanobot/pull/5358) | chengyongru | WebUI 跨会话轻量消息：为持久化会话分配稳定 `@handle`，支持 `list_sessions`/`send_session_message`/`read_session` | — |
| [#5432](https://github.com/HKUDS/nanobot/pull/5432) | chengyongru | TUI API 凭证过期自动刷新：通过认证 bootstrap 端点刷新 401 凭证，去重并发刷新，失败重试一次 | — |

**整体推进评估：** 今日合并内容以稳定性修复和用户体验优化为主，跨会话消息和新凭证刷新机制为 WebUI/TUI 的用户体验补齐了关键能力。Mattermost 系统消息过滤修复了一个可能导致 agent 行为异常的渠道问题。

---

## 4. 社区热点

### 最受关注的 Issues

1. **[Issue #2493](https://github.com/HKUDS/nanobot/issues/2493)** — LangSmith 集成在最新更新后失效
   - 标签：`good first issue` `feature request` `regression`
   - 评论 7 条，1 个赞
   - 摘要：移除 `litellm_provider.py` 后，LangChain 集成失效
   - **已有修复 PR：[#5436](https://github.com/HKUDS/nanobot/pull/5436)**（ojassharma7 提交）

2. **[Issue #5149](https://github.com/HKUDS/nanobot/issues/5149)** — WhatsApp 音频消息发送失败
   - 标签：`bug`
   - 摘要：nanobot 能接收但无法发送 WhatsApp 音频消息
   - 评论 6 条，**尚无修复 PR**

3. **[Issue #4797](https://github.com/HKUDS/nanobot/issues/4797)** — Shell 子进程无资源限制
   - 标签：`bug`
   - 摘要：`ExecTool._spawn()` 未设置 ulimit/cgroups/CPU 亲和性/内存限制，LLM 可发起 fork bomb 耗尽系统资源
   - **已有安全修复 PR：[#4880](https://github.com/HKUDS/nanobot/pull/4880)**（将 `restrict_to_workspace` 默认值从 `False` 改为 `True`，但资源限制问题仍未完全解决）

### 最受关注的 PR

1. **[PR #5437](https://github.com/HKUDS/nanobot/pull/5437)** — 新增 Serply 搜索引擎提供者
   - 作者：googio | 标签：`new-provider` `p2`
   - 参考现有 Serper 提供者模式，将 `web_search` 路由到 `api.serply.io`

2. **[PR #5234](https://github.com/HKUDS/nanobot/pull/5234)** — 集成 mst-python 元搜索提供者
   - 作者：goodtiding5 | 标签：`p1`
   - 聚合 DuckDuckGo/Google/Brave/Bing 等多引擎结果，使用 RRF 融合算法

3. **[PR #4880](https://github.com/HKUDS/nanobot/pull/4880)** — 安全修复：`restrict_to_workspace` 默认值改为 `True`
   - 作者：adabarbulescu | 标签：`security` `p1`
   - 关联 Issue #4796，限制工具操作默认在工作区范围内

---

## 5. Bug 与稳定性

| 优先级 | Issue/PR | 描述 | 状态 |
|---|---|---|---|
| 🔴 高 | [#4797](https://github.com/HKUDS/nanobot/issues/4797) + [#4880](https://github.com/HKUDS/nanobot/pull/4880) | Shell 子进程无 OS 级资源限制，存在 fork bomb 风险；PR #4880 仅限制 workspace 访问，未解决 CPU/内存限制 | PR 已合并，**问题未完全解决** |
| 🔴 高 | [#5429](https://github.com/HKUDS/nanobot/issues/5429) + [#5431](https://github.com/HKUDS/nanobot/pull/5431) | `AgentLoop.schedule_background()` 的 done 回调未调用 `task.result()`，导致后台任务异常被静默吞掉 | **已有修复 PR #5431** |
| 🟡 中 | [#5428](https://github.com/HKUDS/nanobot/issues/5428) + [#5430](https://github.com/HKUDS/nanobot/pull/5430) | `AgentLoop` 在会话任务完成后保留空 `_active_tasks` 条目，造成内存泄漏 | **已有修复 PR #5430** |
| 🟡 中 | [#5425](https://github.com/HKUDS/nanobot/issues/5425) + [#5435](https://github.com/HKUDS/nanobot/pull/5435) | 自定义 OpenAI 兼容提供者的 `socks://` 代理 URL 未被正确解析 | **已有修复 PR #5435** |
| 🟡 中 | [#2493](https://github.com/HKUDS/nanobot/issues/2493) + [#5436](https://github.com/HKUDS/nanobot/pull/5436) | LangSmith 集成在移除 `litellm_provider.py` 后失效（回归） | **已有修复 PR #5436** |
| 🟢 低 | [#5149](https://github.com/HKUDS/nanobot/issues/5149) | WhatsApp 音频消息发送失败（ffmpeg 警告） | 无修复 PR |
| 🟢 低 | [#5417](https://github.com/HKUDS/nanobot/issues/5417) | Windows WebUI 因 gateway 拒绝 PID 交接而退出 | 已关闭，**PR #5415** 已处理 |

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 信号分析 |
|---|---|---|
| **多搜索引擎聚合** | [#5234](https://github.com/HKUDS/nanobot/pull/5234)（mst-python）+ [#5437](https://github.com/HKUDS/nanobot/pull/5437)（Serply） | 两个新搜索提供者 PR 同时存在，反映社区对**扩展 web_search 工具覆盖**的强烈需求；mst-python 使用 RRF 融合多引擎，定位为 p1 优先级 |
| **MiniMax 音乐生成支持** | [#5212](https://github.com/HKUDS/nanobot/pull/5212) | 扩展 music provider 栈，增加工具契约发现和 skill 引导 |
| **WebUI 跨会话消息** | [#5358](https://github.com/HKUDS/nanobot/pull/5358) ✅ 已合并 | 用户可在 WebUI 中向其他会话发送消息，支持 `@handle` 寻址 |
| **Turn 可观测性与安全恢复** | [#5420](https://github.com/HKUDS/nanobot/pull/5420) | 将单次用户 turn 映射到单一响应面，累积 provider 用量估计，gateway 重启作为生命周期边界 |
| **MCP Schema 预算控制** | [#5388](https://github.com/HKUDS/nanobot/pull/5388) | 新增可选的 byte 级 MCP 工具 schema 预算，默认关闭；模型可见的 MCP 工具集可被确定性地裁剪 |
| **Follow-up 建议** | [#5408](https://github.com/HKUDS/nanobot/pull/5408) | WebUI 在 turn 完成后生成临时跟随建议，参考 DeerFlow 交互模式 |
| **持续性目标边界控制** | [#5257](https://github.com/HKUDS/nanobot/pull/5257) | 修复无终止条件的持续目标（"每天提醒我"）导致 agent 永不过期的问题 |

**路线图判断：** 项目正朝三个方向演进：① **搜索能力多元化**（多提供者并行接入）；② **Agent 生命周期与安全边界强化**（资源限制、预算控制、目标终止）；③ **WebUI/TUI 体验精细化**（跨会话消息、凭证刷新、可观测性）。

---

## 7. 用户反馈摘要

### 痛点
1. **LangSmith 集成回归**（#2493）：用户依赖 LangSmith 进行追踪和调试，litellm_provider 移除后集成中断，影响生产环境可观测性
2. **WhatsApp 音频无法发送**（#5149）：ffmpeg 警告导致音频消息发送失败，影响多通道用户体验
3. **Shell 子进程资源无限制**（#4797）：安全社区成员指出 LLM 可发起 fork bomb 耗尽系统资源，属于**严重安全隐患**
4. **后台任务异常被静默吞掉**（#5429）：AgentLoop 的异步任务完成回调未提取异常，导致调试困难
5. **Windows venv PID 交接问题**（#5417）：Windows 上 WebUI 因 gateway 拒绝前台进程导致退出

### 正面反馈
- 跨会话消息（#5358）和 API 凭证自动刷新（#5432）解决了长期存在的使用痛点
- Mattermost 系统消息过滤（#5434）修复了渠道噪音问题

---

## 8. 待处理积压

| 优先级 | Issue/PR | 描述 | 建议 |
|---|---|---|---|
| 🔴 高 | [#4797](https://github.com/HKUDS/nanobot/issues/4797) | Shell 子进程资源限制（ulimit/cgroups/CPU affinity/memory cap）仍未实现，#4880 仅解决 workspace 限制 | 需维护者评估并实现完整的沙箱机制 |
| 🟡 中 | [#5149](https://github.com/HKUDS/nanobot/issues/5149) | WhatsApp 音频发送失败，已 22 天未获响应 | 需确认 ffmpeg 依赖配置或修复消息发送逻辑 |
| 🟡 中 | [#5421](https://github.com/HKUDS/nanobot/issues/5421) | Idle compaction 是否应保留并发 turn 创建的 provider 状态——设计决策问题 | 需维护者明确 continuation-state contract |
| 🟢 低 | [#5372](https://github.com/HKUDS/nanobot/issues/5372) | ViBo 内存系统集成提案（已关闭） | 可能为推广性质的 PR，需甄别 |
| 🟢 低 | [#5409](https://github.com/HKUDS/nanobot/issues/5409) | 混合支出防火墙提案（已关闭） | 可能为推广性质的 PR，需甄别 |

---

**报告生成时间：** 2026-08-19  
**数据源：** [HKUDS/nanobot](https://github.com/HKUDS/nanobot) GitHub API

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-19

## 1. 今日速览

Hermes Agent 项目今日保持高活跃度，24 小时内共处理 100 条变更（50 Issues + 50 PRs），其中 39 条 Issue 处于活跃状态、11 条关闭，37 条 PR 待合并、13 条已合并/关闭，社区反馈渠道通畅。v0.20.4 正式リリースにより約 74 件の PR がロールアップされ、デスクトップ・CLI・マルチプロファイルの主要な安定化が完了。今日焦点はデスクトップのセッション復旧バグ、プロファイル切り替え静默失败、および Windows 環境の更新ロック問題など、実利用に直結する安定性課題に集まっている。

---

## 2. 版本发布

### v0.20.4 (v2026.8.18)

- **发布日期：** 2026年8月18日
- **性质：** Patch release，累计约 74 个 PR
- **主要变更：** 下游消费者（Docker 镜像、托管部署、全新安装）的稳定 tagged release，涵盖此前 v0.20.3 以来的多项修复。
- **迁移注意事项：** 作为 patch 版本，无破坏性变更；可直接升级。

> 链接：[Release v2026.8.18](https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.18)

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 | 链接 |
|---|---|---|---|
| #89619 | fmt | `npm run fix` 自动格式化，CI 自动合并 | [PR #89619](https://github.com/NousResearch/hermes-agent/pull/89619) |
| #86961 | bug | 修复 macOS Quick Entry 原生窗口阴影问题 | [PR #86961](https://github.com/NousResearch/hermes-agent/pull/86961) |
| #89467 | feature | `clarify` 工具支持单次调用问多个独立问题 | [PR #89467](https://github.com/NousResearch/hermes-agent/pull/89467) |
| #70129 | feature | `clarify_form` 多问题澄清工具 | [PR #70129](https://github.com/NousResearch/hermes-agent/pull/70129) |
| #58828 | bug | 修复 `/goal` turn counter 在 streaming 开启时卡在 0 的问题 | [PR #58828](https://github.com/NousResearch/hermes-agent/pull/58828) |
| #84999 | security | 浏览器执行后重新校验 landed URL，修复安全边界漏洞 | [PR #84999](https://github.com/NousResearch/hermes-agent/pull/84999) |
| #89613 | bug | 修复安全扫描器读取测试目录的误报问题 | [PR #89613](https://github.com/NousResearch/hermes-agent/pull/89613) |

**整体判断：** 今日合并的 13 条 PR 以 bug 修复和功能完善为主，无大型新功能上线，项目处于 v0.20.4 发布后的稳定收敛阶段。

---

## 4. 社区热点

### 评论数最多的 Issues（Top 5）

| Issue | 类型 | 热度 | 摘要 | 链接 |
|---|---|---|---|---|
| #66616 | bug | 54 评论 | Skills 索引老化/退化，29.8h 未刷新 | [Issue #66616](https://github.com/NousResearch/hermes-agent/issues/66616) |
| #88275 | perf | 9 评论 | macOS Intel 桌面版 Renderer 空闲 CPU 占用 40-73% | [Issue #88275](https://github.com/NousResearch/hermes-agent/issues/88275) |
| #53902 | perf | 8 评论 | v0.17.0 引入的 fontations+temporal_rs 渲染循环，GPU 98% | [Issue #53902](https://github.com/NousResearch/hermes-agent/issues/53902) |
| #88897 | bug | 6 评论 | `--isolated` 模式下 agent session 未写入 profile home DB | [Issue #88897](https://github.com/NousResearch/hermes-agent/issues/88897) |
| #18885 | feature | 5 评论 | 为 cron job 添加 `allow_memory` flag 以使用记忆工具 | [Issue #18885](https://github.com/NousResearch/hermes-agent/issues/18885) |

**热点分析：**
- **#66616** 是长期未解决的索引健康度问题，自动化探针持续报告降级，社区关注度最高（54 条评论）。
- **#88275 / #53902** 反映 macOS Intel 设备上的性能回归，GPU/CPU 占用异常，是桌面用户体验的痛点。
- **#88897** 是新版本的潜在回归，`--isolated` 模式下的数据路由逻辑存在问题。

---

## 5. Bug 与稳定性

### 今日报告的重要 Bug（按严重程度排列）

| 级别 | Issue | 标题 | 状态 | Fix PR | 链接 |
|---|---|---|---|---|---|
| **P2** | #88897 | dashboard --isolated 未使用 profile home DB | OPEN | — | [Issue #88897](https://github.com/NousResearch/hermes-agent/issues/88897) |
| **P2** | #89244 | Desktop Restore after compaction 拒绝并返回 4030 | OPEN | #88092 | [Issue #89244](https://github.com/NousResearch/hermes-agent/issues/89244) |
| **P2** | #89586 | Windows 桌面 profile 切换静默挂起 | OPEN | #89621 | [Issue #89586](https://github.com/NousResearch/hermes-agent/issues/89586) |
| **P2** | #89599 | Windows CLI `hermes update` 因自锁无法成功 | OPEN | — | [Issue #89599](https://github.com/NousResearch/hermes-agent/issues/89599) |
| **P2** | #85624 | Bedrock/Anthropic 上 auto-title 100% 失败（response_format 泄漏） | CLOSED | — | [Issue #85624](https://github.com/NousResearch/hermes-agent/issues/85624) |
| **P2** | #89556 | 桌面端重新打开已聚焦 session 永久挂起 | OPEN | — | [Issue #89556](https://github.com/NousResearch/hermes-agent/issues/89556) |
| **P2** | #89576 | Desktop MCP 健康探测开启第二个 HTTP session 导致挤掉活跃 session | OPEN | — | [Issue #89576](https://github.com/NousResearch/hermes-agent/issues/89576) |
| **P2** | #89600 | `hermes plugins enable` 在 stdout 重定向时永久挂起 | OPEN | — | [Issue #89600](https://github.com/NousResearch/hermes-agent/issues/89600) |
| **P3** | #89561 | `hermes config set` 存储复合值（列表/映射）为字符串 | OPEN | — | [Issue #89561](https://github.com/NousResearch/hermes-agent/issues/89561) |

**Bug 统计：** 今日新增/活跃 P2 级 Bug 共 8 个，其中 2 个已有对应 Fix PR（#88092、#89621）。桌面端和 Windows 平台是 Bug 高发区，session 状态管理和 profile 切换逻辑是主要风险点。

---

## 6. 功能请求与路线图信号

| Issue | 类型 | 需求摘要 | 已有 PR | 纳入可能性 |
|---|---|---|---|---|
| #18885 | feature | 为 cron job 添加 `allow_memory` flag | — | 中（需设计安全边界） |
| #89304 | feature | Desktop profile alias 指向远程 gateway profile | — | 低（架构变更较大） |
| #89549 | feature | xAI 视频插件支持 1080p | — | 低（依赖上游 API） |
| #88307 | UX | 状态栏常驻连接选择器 | — | 低（UI 层面改动） |
| #9056 | feature | Nix Home Manager 模块 | — | 中（社区贡献型） |
| #89620 | feature | Hermes 提供实时 UI 导览（guided tours） | #89620 | 高（已在开发中） |
| #89567 | feature | Desktop Projects 持久化 agent | #89567 | 高（已在开发中） |

**路线图判断：** 当前开发重点在桌面端体验优化（Projects 持久化 agent、guided tours）和安全加固（browser URL 重新校验、MCP session 管理）。多问题澄清工具（clarify/clarify_form）已合并，下一步可能关注 Windows 稳定性修复。

---

## 7. 用户反馈摘要

### 真实痛点

1. **桌面端 session 管理混乱**
   - 用户反映 `/isolated` 模式下 session 写入错误数据库（#88897）
   - Restore 后 ordinal 不匹配导致 4030 错误（#89244）
   - 重新打开已聚焦 session 永久挂起（#89556）

2. **Windows 平台体验差**
   - `hermes update` 因自锁无法成功（#89599）
   - Profile 切换静默失败（#89586）
   - 审批弹窗在远程桌面不传播（#89111）

3. **macOS 性能问题**
   - Renderer 空闲时 CPU 占用 40-73%（#88275）
   - fontations+temporal_rs 渲染循环导致 GPU 98%（#53902）

4. **MCP 健康探测挤掉活跃 session**
   - Slack MCP 等单 session 限制的主机被探测请求踢下线（#89576）

### 满意点
- `clarify` 工具支持多问题一次调用，减少 round-trip（#89467）
- Desktop Projects 持久化 agent 设计合理（#89567）
- guided tours 功能提升新用户上手效率（#89620）

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 类型 | 创建时间 | 评论数 | 风险 | 链接 |
|---|---|---|---|---|---|
| #66616 | bug | 2026-07-18 | 54 | 高（索引健康度） | [Issue #66616](https://github.com/NousResearch/hermes-agent/issues/66616) |
| #53902 | perf | 2026-06-28 | 8 | 高（性能回归） | [Issue #53902](https://github.com/NousResearch/hermes-agent/issues/53902) |
| #18885 | feature | 2026-05-02 | 5 | 中 | [Issue #18885](https://github.com/NousResearch/hermes-agent/issues/18885) |
| #17157 | bug | 2026-04-28 | 3 | 中（Discord 集成） | [Issue #17157](https://github.com/NousResearch/hermes-agent/issues/17157) |

### 建议维护者关注
1. **#66616** 持续 32 天未解决，Skills 索引老化影响用户体验，建议优先处理。
2. **#53902** 性能回归已存在 52 天，macOS Intel 用户反馈强烈。
3. **#89599 / #89586** Windows 平台两个高优先级 Bug 尚无 Fix PR，建议加速响应。

---

**日报生成时间：** 2026-08-19  
**数据来源：** NousResearch/hermes-agent GitHub 仓库

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-08-19

## 1. 今日速览

过去 24 小时内，PicoClaw 项目保持中等活跃度：共收到 6 条 Issue 更新和 4 条 PR 更新，其中 2 条 PR 已合并。社区关注点集中在 **Web UI 开发**、**LINE 渠道 Webhook 配置缺陷**、以及 **多渠道会话管理 Bug** 上。整体而言，项目在修复配置层面的隐蔽问题方面有所推进，但多起 Bug 仍未获得实质响应，部分 Issue 已被标记为 stale，需引起维护者注意。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### ✅ 已合并 / 已关闭的 PR（2 条）

| PR | 内容 | 意义 |
|---|---|---|
| [#1158](https://github.com/sipeed/picoclaw/issues/1158) | 新增 `anthropic-messages` 协议，支持 Anthropic 原生 `/v1/messages` 格式 | 解决了仅支持 Anthropic 原生 API 格式的第三方服务（如各类代理）无法接入的问题，扩展了模型供给范围 |
| [#3317](https://github.com/sipeed/picoclaw/issues/3317) | 在 LLM 响应调试日志中增加 prompt cache token 信息 | 提升了对 DeepSeek 等支持 prompt caching 的模型的可观测性，方便用户追踪费用与性能 |

### 🔶 待合并 PR（2 条）

| PR | 内容 | 状态 |
|---|---|---|
| [#3329](https://github.com/sipeed/picoclaw/issues/3329) | 修复 LINE 渠道 `webhook_host`/`webhook_port` 配置项形同虚设的问题，改为主动告警 | Open / stale — 修复了与 [#3328](https://github.com/sipeed/picoclaw/issues/3328) 对应的 Bug，但尚未被合并 |
| [#3314](https://github.com/sipeed/picoclaw/issues/3314) | 修复 `customAllowPatterns` 不生效的 Bug（默认拒绝模式优先于自定义白名单） | Open / stale — 解决了 agent 执行 `git push` 等自定义命令被误拦的问题，等待合并 |

**整体评估**：今日 2 条 PR 成功合入，主要推进了**协议兼容性**和**可观测性**；另有 2 条 Bug 修复 PR 积压，反映出维护者对配置类修复的响应速度有待提升。

---

## 4. 社区热点

### 🔥 Issue #806 — 添加 Web UI 支持（8 👍 / 9 评论）
- **链接**: <https://github.com/sipeed/picoclaw/issues/806>
- **热度分析**：这是今日最受关注的功能请求，拥有 8 个赞和 9 条评论，且标记为 `high` 优先级和 `roadmap` 类型。作者 Zepan 在 2026-08-18 更新了进度（注明 "Refactoring now"）。
- **背后诉求**：降低非技术用户的上手门槛，将 TUI 之外的 Web 界面纳入规划。该需求与长期社区呼声一致，值得在下一版本路线图重点排期。

### ⭐ Issue #3287 — IRC 长消息支持改进（6 评论）
- **链接**: <https://github.com/sipeed/picoclaw/issues/3287>
- **热度分析**：6 条评论，聚焦于 IRCv3 长消息被截断后无法合并为完整语义的问题。涉及 IRC 协议 512 字节限制与 PicoClaw 消息处理逻辑的兼容性。
- **背后诉求**：希望 PicoClaw 能智能识别并重组被 IRC 协议拆分的长消息，提升多模态聊天场景下的体验。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#3301](https://github.com/sipeed/picoclaw/issues/3301) | `/clear` 命令和 session 自动压缩在通过 dispatch rules 路由至非默认 agent 时失效 | 暂无 |
| 🟡 中 | [#3328](https://github.com/sipeed/picoclaw/issues/3328) | `line.settings.webhook_host` / `webhook_port` 配置项声明了默认值且有文档，但代码从未读取 | [#3329](https://github.com/sipeed/picoclaw/issues/3329)（Open/stale） |
| 🟡 中 | [#3339](https://github.com/sipeed/picoclaw/issues/3339) | Google Antigravity 模型鉴权成功但每次生成均返回 429 RESOURCE_EXHAUSTED | 暂无 |
| 🟢 低 | [#3292](https://github.com/sipeed/picoclaw/issues/3292) | 聊天界面输入框聚焦时 CPU 占用过高（已在 Firefox 下复现） | 已关闭（可能已修复或无法复现） |

**稳定性评估**：今日 Bug 报告以**配置解析**和**路由逻辑**为主，未见崩溃类问题。`#3301` 涉及核心会话管理功能，影响多 agent 部署场景，建议优先处理。

---

## 6. 功能请求与路线图信号

| 需求 | Issue | 信号强度 | 关联 PR |
|---|---|---|---|
| Web UI 界面 | [#806](https://github.com/sipeed/picoclaw/issues/806) | ⭐⭐⭐⭐⭐ 高（roadmap + high priority + 8 👍） | — |
| IRC 长消息合并 | [#3287](https://github.com/sipeed/picoclaw/issues/3287) | ⭐⭐⭐ 中 | — |
| Anthropic Messages 协议原生支持 | — | ✅ 已完成 | [#1158](https://github.com/sipeed/picoclaw/issues/1158) |
| Prompt Cache Token 日志 | — | ✅ 已完成 | [#3317](https://github.com/sipeed/picoclaw/issues/3317) |

**预测**：Web UI 功能大概率纳入下一版本核心路线图；`customAllowPatterns` 修复（[#3314](https://github.com/sipeed/picoclaw/issues/3314)）涉及安全策略，建议尽快合并以避免用户误判权限配置。

---

## 7. 用户反馈摘要

- **痛点**：多 agent 路由场景下（dispatch rules），`/clear` 和 session 压缩功能失效，影响多实例用户的使用体验（[#3301](https://github.com/sipeed/picoclaw/issues/3301)）。
- **痛点**：LINE 渠道的 webhook 配置参数形同虚设，用户按照文档配置后无实际效果且无警告提示，容易产生困惑（[#3328](https://github.com/sipeed/picoclaw/issues/3328)）。
- **痛点**：`customAllowPatterns` 自定义白名单被默认拒绝规则覆盖，导致用户信任的配置无法生效（[#3314](https://github.com/sipeed/picoclaw/issues/3314)）。
- **满意**：Anthropic 原生协议支持和 prompt cache 日志的加入提升了开发者的调试效率和模型接入灵活性。
- **不满**：Google Antigravity 鉴权通过但持续 429 错误，用户无法判断是配额问题还是 SDK 兼容问题（[#3339](https://github.com/sipeed/picoclaw/issues/3339)）。

---

## 8. 待处理积压

| 类型 | Issue / PR | 创建时间 | 评论数 | 建议 |
|---|---|---|---|---|
| 🔴 高 | [#3301](https://github.com/sipeed/picoclaw/issues/3301) — 多 agent 路由下 `/clear` 失效 | 2026-07-29 | 4 | 优先修复，涉及核心会话管理 |
| 🟡 中 | [#3329](https://github.com/sipeed/picoclaw/issues/3329) — LINE webhook 配置修复 PR | 2026-08-11 | — | 合并以关闭对应 Bug |
| 🟡 中 | [#3314](https://github.com/sipeed/picoclaw/issues/3314) — `customAllowPatterns` 修复 PR | 2026-08-03 | — | 合并以修复安全策略误拦问题 |
| 🟢 低 | [#3339](https://github.com/sipeed/picoclaw/issues/3339) — Google Antigravity 429 | 2026-08-17 | 1 | 需确认是否为上游限制或 SDK 问题 |
| ⭐ 长期 | [#806](https://github.com/sipeed/picoclaw/issues/806) — Web UI 开发 | 2026-02-26 | 9 | 已有 refactoring 进展，建议排期下一版本 |

---

**项目健康度总结**：PicoClaw 在过去 24 小时内保持稳定的贡献节奏，2 条高质量 PR 成功合入，Web UI 路线图持续推进。主要风险在于 **3 个待合并的 Bug 修复 PR 均处于 stale 状态**，以及 **Issue #3301 的多 agent 路由 Bug** 尚未得到处理，建议维护者优先响应，避免社区活跃度进一步下降。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-08-19

## 1. 今日速览

IronClaw 项目今日保持高活跃度：过去24小时内新增/更新 Issues 21 条（新开+活跃 15，关闭 6），PRs 40 条（合并/关闭 15，待合并 25）。核心动态为 **v1.3.0-rc.2** 预发布版的发布，修复了从 1.2 升级时的启动崩溃回归问题；同时多个 v1.4.0 Epic 进入实质性开发阶段（Mnesis 内存集成、沙箱方案、DESIGN.md 治理）。整体项目健康度良好，Bug 响应及时，架构重构持续推进。

---

## 2. 版本发布

### ironclaw-v1.3.0-rc.2（2026-08-18）

**更新内容：**
- **关键修复**：从 v1.2 升级时，`activation_state` 字段不再被丢弃，避免启动时 crash-loop
- **Reborn runtime 镜像**：恢复对 opt-in 公钥-only SSH（端口 2222）的支持

**破坏性变更/迁移注意：**
- 无新增破坏性变更；此 rc 主要修复 regression
- 建议所有 v1.2 → v1.3 升级路径用户在升级后验证 `activation_state` 持久化是否正常

🔗 [Release #7735](https://github.com/nearai/ironclaw/releases)

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#7734](https://github.com/nearai/ironclaw/pull/7734) | refactor | 完成 loop 模块两项遗留测试提取（317 tests，0 生产代码），清理 `executor/tests.rs` 与 `capability_port.rs` 内联测试 |
| [#7638](https://github.com/nearai/ironclaw/pull/7638) | fix | 将线程删除失败的 `window.alert()` 替换为全局 toast 通知，统一 WebUI 反馈体验 |
| [#7639](https://github.com/nearai/ironclaw/pull/7639) | refactor | 引入共享 `InlineNotice` 组件（info/success/warning/danger），迁移 Jobs/Projects/Workspace/Extensions 的一致性内联提示 |

**整体推进评估：** 今日合并以"清理+体验修复"为主，未涉及核心功能变更；但为 v1.3.0 稳定性打下基础，同时为 v1.4.0 的设计系统统一铺路。

---

## 4. 社区热点

### 高关注 Issues

**#7185 — Memory 跨会话不可靠召回** `[CLOSED]`  
👤 sergeiest · 📅 2026-08-04 → 2026-08-18  
> 多个测试者独立报告：一次对话中建立的信息在后续对话中无法可靠召回。已在 2026-07-23 周报中提出，今日关闭，预计纳入后续修复。  
🔗 [Issue #7185](https://github.com/nearai/ironclaw/issues/7185)

**#6879 — 自动化运行偶发性失败** `[OPEN]`  
👤 serrrfirat · 📅 2026-07-29  
> 同一 prompt 有时成功有时失败，小模型（DeepSeek V4 Flash）尤甚。根因分析确认为结构性问题（trigger → run pipeline），非模型噪声。  
🔗 [Issue #6879](https://github.com/nearai/ironclaw/issues/6879)

**#7736 — 每日失败分类报告** `[OPEN]`  
👤 pranavraja99 · 📅 2026-08-19（今日新建）  
> enterprise 套件 10 个非通过任务，主要由弱模型（Qwen3.8-27B）在多步任务中失败驱动。  
🔗 [Issue #7736](https://github.com/nearai/ironclaw/issues/7736)

### 高关注 PR

**#7697 — 持久化 Inbox 与产品 API** `[OPEN, XL]`  
👤 italic-joshford · 未读通知、分页、归档生命周期 API，将 Inbox 所有权迁移至独立 `ironclaw_notifications` 领域。  
🔗 [PR #7697](https://github.com/nearai/ironclaw/pull/7697)

**#7735 — 对话产物加入运行时间证据** `[OPEN, XL]`  
👤 henrypark133 · 下载型产物 JSON 新增 `timings` 块（推理耗时、工具耗时、调用计数），便于 bug 报告携带时序证据。  
🔗 [PR #7735](https://github.com/nearai/ironclaw/pull/7735)

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#7727](https://github.com/nearai/ironclaw/issues/7727) | `Catalog.capabilities` 字段为 mandatory 但从未被读取，影响 manifest v3 工具 | — |
| 🔴 高 | [#7726](https://github.com/nearai/ironclaw/issues/7726) | `IRONHUB_MANIFEST_URL` 可配置但运行时硬编码为 `hub.ironclaw.com`，私有目录被拒绝 | — |
| 🟡 中 | [#7714](https://github.com/nearai/ironclaw/issues/7714) `[CLOSED]` | libSQL 单写连接在压测下饥饿，导致 journal 卡死、authority 失效级联 | ✅ 已关闭 |
| 🟡 中 | [#7673](https://github.com/nearai/ironclaw/issues/7673) | BudgetLedger 截断启动窗口导致双重计费；charge 耐久性问题 | — |
| 🟠 低 | [#7447](https://github.com/nearai/ironclaw/issues/7447) | Agent 工具调用过多后卡死（fetch-retry 循环耗尽 turn budget） | — |

**稳定性评估：** 两个 🔴 级 Bug 均涉及 IronHub 目录系统，影响私有化部署场景，建议优先修复；#7714 已闭环。

---

## 6. 功能请求与路线图信号

| Issue/PR | 诉求 | 版本信号 | 状态 |
|---|---|---|---|
| [#7731](https://github.com/nearai/ironclaw/issues/7731) | 集成 Mnesis 作为记忆提供者 | v1.4.0 | 🔵 新建 Spike |
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | CLI 沙箱方案（E2E sandboxing） | v1.4.0 | 🔵 新建 Epic |
| [#7392](https://github.com/nearai/ironclaw/issues/7392) → [#7491](https://github.com/nearai/ironclaw/pull/7491) | 用 omp 工具表面替代自有编码工具 | v1.4.0 | 🟢 PR 开发中 |
| [#7038](https://github.com/nearai/ironclaw/issues/7038) → [#7257](https://github.com/nearai/ironclaw/pull/7257), [#7043](https://github.com/nearai/ironclaw/pull/7043) | Storybook + AI-first 设计系统 | v1.4.0 | 🟢 Phase 2 推进中 |
| [#7354](https://github.com/nearai/ironclaw/issues/7354) | Extensions vNext：统一渠道架构 + Signal 通道 | v1.3.0 | 🟡 进行中 |
| [#7467](https://github.com/nearai/ironclaw/issues/7467) | Reborn 持久化 profile 无关化 | v1.4.0 | 🔵 Epic 新建 |
| [#7724](https://github.com/nearai/ironclaw/pull/7724) | WebUI 语音输入（NEAR AI Whisper） | — | 🟢 PR 已提交 |

**路线图判断：** v1.3.0 聚焦 Extensions 统一渠道与稳定性；v1.4.0 明显向设计系统、omp 工具替换、Mnesis 记忆、沙箱四方向扩展。

---

## 7. 用户反馈摘要

| 痛点/场景 | 来源 | 反馈提炼 |
|---|---|---|
| **跨会话记忆丢失** | #7185 · #7447 | 用户期望 Agent 在连续对话中保持上下文，当前实现不可靠；工具调用过多时 Agent 陷入重试循环而非分页获取 |
| **Slack 未链接用户体验差** | #7681 → #7682 | 在共享频道中@机器人时，连接提示公开可见且需多步手动操作；PR #7682 已修复为私信+一键连接链接 |
| **自动化运行不稳定** | #6879 | 同一 prompt 执行结果不一致，小模型表现更差；用户期望自动化可预测、可重复 |
| **WebUI 反馈不一致** | #7638 · #7639 | 各模块使用不同风格的 inline 提示和 alert，体验碎片化；现已统一为 `InlineNotice` + toast |
| **线程删除阻塞** | #7638 | `window.alert()` 阻塞 UI 且与产品通知系统不一致，已改为全局 toast |
| **语音输入需求** | #7724 | 用户希望在 composer 中使用语音输入，PR 已实现：本地录音→服务端转录→插入光标，不自动发送 |

---

## 8. 待处理积压

| Issue/PR | 风险 | 说明 | 建议 |
|---|---|---|---|
| [#6837](https://github.com/nearai/ironclaw/issues/6837) | 🟡 中 | Growth/usage 分析无 `info!` 级别日志，52 个 info call 全是基础设施，workspace 层零日志 | 纳入 v1.4.0 可观测性改进 |
| [#7467](https://github.com/nearai/ironclaw/issues/7467) | 🟠 高 | Reborn 存储按 profile 索引，切换 profile 后历史/密钥/skills  stranded，影响多 profile 用户 | v1.4.0 Epic，需提前规划迁移路径 |
| [#7727](https://github.com/nearai/ironclaw/issues/7727) | 🔴 高 | `capabilities` artifact 必填但从不读取，manifest v3 工具受影响 | 优先修复或移除必填约束 |
| [#7726](https://github.com/nearai/ironclaw/issues/7726) | 🔴 高 | `IRONHUB_MANIFEST_URL` 配置形同虚设，私有目录部署被硬编码 hostlist 拦截 | 优先修复，影响企业用户 |
| [#7673](https://github.com/nearai/ironclaw/issues/7673) | 🟡 中 | BudgetLedger 双重计费与 charge 耐久性问题，导致过早停止 | 纳入 v1.4.0 财务模块重构 |

---

**日报生成时间：** 2026-08-19  
**数据来源：** [nearai/ironclaw](https://github.com/nearai/ironclaw) GitHub API

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报
**日期**：2026-08-19  
**数据周期**：2026-08-18 00:

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-08-19

---

## 1. 今日速览

Moltis 项目今日活跃度维持较高水平，过去24小时内关闭了2个Issue并合并了5个PR，另有1个新功能PR (#1210) 仍处于开放评审状态。项目健康度良好，bug修复与功能扩展并行推进，Podman沙箱兼容性和文件管理能力得到增强。新增两个发布版本（20260818.06 / 20260818.08）表明发布节奏稳定，维护者响应及时。

---

## 2. 版本发布

| 版本 | 日期 | 说明 |
|------|------|------|
| 20260818.08 | 2026-08-18 | 包含今日合并的5个PR更新 |
| 20260818.06 | 2026-08-18 | 上一批次发布 |

**破坏性变更提示：** PR #1209 修复了 `heartbeat.update` 参数处理逻辑——此前该接口将传入参数直接反序列化为完整 `HeartbeatConfig` 并覆盖整个配置，导致未显式传入的字段被重置为默认值。升级后需确认 heartbeat 配置更新流程兼容性。

---

## 3. 项目进展

今日合并的重要PR按影响力排序：

- **#1206** [CLOSED] 新增 `Files` 持久化库与 Settings 浏览器（含 `MOLTIS_FILES_DIR` 发现机制及 Docker/Podman/Apple Container 只读挂载）— 填补了项目长期缺失的文件管理模块，显著提升可扩展性。
  - 链接: [PR #1206](https://github.com/moltis-org/moltis/pull/1206)

- **#1198** [CLOSED] OpenAI reasoning tool calls 路由优化 — 将结合 function tools 与 `reasoning_effort` 的内置 OpenAI 请求统一经 Responses API 路由，同时保留 Chat Completions 行为，增强多提供商兼容性。
  - 链接: [PR #1198](https://github.com/moltis-org/moltis/pull/1198)

- **#1106** [CLOSED] Podman 沙箱 escape hatches — 为 validated Linux host-socket 透传和特权嵌套 Podman 场景提供显式逃逸路径，改善 rootless Podman 诊断能力。
  - 链接: [PR #1106](https://github.com/moltis-org/moltis/pull/1106)

- **#1209** [CLOSED] 修复 heartbeat.update 参数 patch 语义 — 直接关闭 Issue #1187。
  - 链接: [PR #1209](https://github.com/moltis-org/moltis/pull/1209)

- **#1211** [CLOSED] 修复 README 星图 broken 问题 — 更换数据源以绕过 GitHub stargazer API 令牌限制。
  - 链接: [PR #1211](https://github.com/moltis-org/moltis/pull/1211)

**整体评估：** 5个PR合并覆盖 bug修复、基础设施增强、API兼容优化三个维度，项目整体向前推进显著，尤其 Files 库的引入为后续生态扩展奠定基础。

---

## 4. 社区热点

- **#1095** — Podman 通过 Moltis 运行异常（评论2条）
  - 链接: [Issue #1095](https://github.com/moltis-org/moltis/issues/1095)
  - 分析：Podman 作为 Docker 的 rootless 替代方案，用户群体增长推动了对原生兼容性的需求；该 Issue 已有 PR #1106 修复并关闭。

- **#1187** — Heartbeat 设置 UI 静默重置未映射字段
  - 链接: [Issue #1187](https://github.com/moltis-org/moltis/issues/1187)
  - 分析：UI 配置管理的基础性缺陷，影响用户体验信任度；PR #1209 已快速修复。

- **#1210** — Tesla Fleet API 连接器（开放，0评论）
  - 链接: [PR #1210](https://github.com/moltis-org/moltis/pull/1210)
  - 分析：新增 IoT/车载数据同步能力，属于生态扩展类 PR，目前处于评审阶段，预计社区关注度将逐步提升。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | 状态 | Fix PR |
|--------|-------|------|------|--------|
| P2 | [#1187](https://github.com/moltis-org/moltis/issues/1187) | Heartbeat 配置 UI 静默重置未显式传入字段 | ✅ 已关闭 | [#1209](https://github.com/moltis-org/moltis/pull/1209) |
| P2 | [#1095](https://github.com/moltis-org/moltis/issues/1095) | Podman 运行时兼容性问题 | ✅ 已关闭 | [#1106](https://github.com/moltis-org/moltis/pull/1106) |

**结论：** 今日无新增未修复 bug，所有关闭的 Issue 均已配套 PR，稳定性态势良好。

---

## 6. 功能请求与路线图信号

- **#1210** Tesla Fleet API Connector（进行中）
  - 链接: [PR #1210](https://github.com/moltis-org/moltis/pull/1210)
  - 信号：项目在横向扩展「外部服务连接器」矩阵，Tesla 作为主流 EV 平台，此 PR 若合并将补齐智能家居/出行场景的数据采集能力。只读设计降低了安全顾虑，预计通过概率较高。

- **#1206** Files 库与 Settings 浏览器（已合并）
  - 链接: [PR #1206](https://github.com/moltis-org/moltis/pull/1206)
  - 信号：文件管理能力是长期路线图的重要组成部分，本次引入的持久化、流式 API、容器挂载支持为后续更多集成（如文档管理、模型权重托管）打下基础。

**展望：** 下一版本可能继续聚焦于「连接器生态扩展」与「文件/配置管理体验优化」两个方向。

---

## 7. 用户反馈摘要

- **Podman 兼容诉求强烈**：Issue #1095 反映了使用 rootless 容器方案的用户对 Moltis 沙箱层的支持期待，维护者通过 PR #1106 提供了显式 escape hatch 机制并改进诊断，体现了对用户环境的务实响应。
- **配置管理的可靠性是信任基础**：Heartbeat 静默重置（#1187）虽未造成数据丢失，但暴露了序列化/反序列化逻辑的设计盲区，修复后增强了用户对配置持久化的信心。
- **README 星图维护细节**：PR #1211 主动修复展示层问题，说明维护者关注项目形象与社区可见性。

---

## 8. 待处理积压

| PR | 作者 | 状态 | 建议关注 |
|----|------|------|----------|
| [#1210](https://github.com/moltis-org/moltis/pull/1210) | penso | OPEN | Tesla 连接器 PR 已创建1天，建议维护者尽快完成首轮评审以推动路线图落地。 |

**总体评价：** Moltis 项目当前处于稳健增长期，Issue 闭环率高，PR 合并节奏健康，新功能引入方向清晰。建议维护者重点关注 #1210 的评审进度，并保持当前发布节奏。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-08-19

---

## 1. 今日速览

过去24小时项目保持高活跃度：**45条 Issue 更新**（29条新开/活跃，16条关闭）+ **50条 PR 更新**（32条待合并，18条已合并/关闭）。无新版本发布，社区以 bug 修复和安全加固为主。MCP/Channels 连接稳定性、OAuth2 Token 刷新、以及沙箱环境兼容性是今日高频讨论主题，反映出 v2.1.0 发布后用户反馈集中涌入。

---

## 2. 版本发布

无新版本发布。当前最新稳定版本仍为 **v2.1.0**。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#7122](https://github.com/agentscope-ai/QwenPaw/pull/7122) | Feature | 业务知识库（Biz KB）功能合入 |
| [#6617](https://github.com/agentscope-ai/QwenPaw/pull/6617) | Fix | 修复流式重试路径未遵守 `Retry-After` 头限制的问题 |
| [#7072](https://github.com/agentscope-ai/QwenPaw/pull/7072) | Feature | 新增后台聊天任务列表 API（`GET /console/chat/task`） |
| [#7064](https://github.com/agentscope-ai/QwenPaw/pull/7064) | Fix | 修复 `qwenpaw cron update --text` 对 agent 类型任务 top-level text 不同步的 bug |
| [#7069](https://github.com/agentscope-ai/QwenPaw/pull/7069) | Fix | 修复 session 重载后历史消息中 data-URL 图片无法渲染的问题 |

> 整体看，今日关闭的 PR 以细节修复和 CLI 行为对齐为主，未见架构级改动。

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issue

| Issue | 评论数 | 摘要 |
|---|---|---|
| [#6684](https://github.com/agentscope-ai/QwenPaw/issues/6684) | 10 | 自建 Matrix 频道缺少重试机制，导致每次重启需手动恢复连接 |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | 8 | 多步骤任务执行到中间规划节点后无故停止，需用户手动触发"继续" |
| [#7102](https://github.com/agentscope-ai/QwenPaw/issues/7102) | 7 | v2.1.0 使用 glm 模型时出现超过10分钟的完全冻结 |
| [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) | 7 | Console 停止请求误取消活跃飞书会话（多 UI session 会话 ID 交叉） |
| [#6470](https://github.com/agentscope-ai/QwenPaw/issues/6470) | 5 | MCP driver 硬编码 SSE client，忽略 YAML 中 `streamable_http` 配置 |
| [#6260](https://github.com/agentscope-ai/QwenPaw/issues/6260) | 3 👍1 | 工具调用过程占满屏幕，期望折叠思考过程突出交付结果 |

**热点分析：**
- **连接稳定性**是今日核心痛点：#6684（频道重试）、#6470（MCP transport 硬编码）、#5900（MCP 断连无重连）形成共振，用户期望 Channels/MCP 层具备更强的容错能力。
- **Agent 执行异常** (#6921, #7102, #7011) 均指向 v2.1.0 引入的调度或会话管理变更，需优先排查。
- **结果呈现** (#6260) 获得唯一点赞，反映用户对"思考过程折叠"功能有明确付费意愿（体验层面）。

---

## 5. Bug 与稳定性

### 已确认的高优先级 Bug

| Issue | 严重程度 | 摘要 | Fix PR |
|---|---|---|---|
| [#7102](https://github.com/agentscope-ai/QwenPaw/issues/7102) | 🔴 高 | 会话运行中完全冻结 >10分钟，无任何输出 | 暂无 |
| [#7063](https://github.com/agentscope-ai/QwenPaw/issues/7063) | 🔴 高 | 工具调用必现 `TypeError: 'async for' requires __aiter__` 崩溃 | 暂无（需修复 `_acting` 返回类型） |
| [#7082](https://github.com/agentscope-ai/QwenPaw/issues/7082) | 🔴 高 | `_StructuredOutputDynamicClass` 未 fully defined，导致 model execution 失败 | 暂无 |
| [#7110](https://github.com/agentscope-ai/QwenPaw/issues/7110) | 🟡 中 | 会话中任何不可访问的图片链接导致整个会话挂掉，仅 `/clear` 可恢复 | 暂无 |
| [#7074](https://github.com/agentscope-ai/QwenPaw/issues/7074) | 🟡 中 | 正常运行时高频崩溃，需刷新页面才能恢复 | 暂无 |
| [#7005](https://github.com/agentscope-ai/QwenPaw/issues/7005) | 🟡 中 | 启用沙箱后 `uv run` 无法写入 `~/.cache/uv` | [#7116](https://github.com/agentscope-ai/QwenPaw/pull/7116) 待合并 |
| [#7076](https://github.com/agentscope-ai/QwenPaw/issues/7076) | 🟡 中 | qwenpaw-creator 模型配置接口返回 404 | 暂无 |

### 已关闭/已修复的 Bug
- [#7065](https://github.com/agentscope-ai/QwenPaw/issues/7065) — 讨论多轮后历史消息加载不完整（已关闭）
- [#6794](https://github.com/agentscope-ai/QwenPaw/issues/6794) — Agent Kanban 405 错误（已关闭）
- [#7039](https://github.com/agentscope-ai/QwenPaw/issues/7039) — 2.1.0 莫名新建会话（已关闭）

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 优先级评估 |
|---|---|---|
| 频道/连接层自动重试与断线重连 | [#6684](https://github.com/agentscope-ai/QwenPaw/issues/6684)、[#5900](https://github.com/agentscope-ai/QwenPaw/issues/5900) | ⭐⭐⭐ 高 — 多 Issue 重叠，应纳入稳定性专项 |
| 插件 API 支持自定义 `system_prompt` | [#7052](https://github.com/agentscope-ai/QwenPaw/issues/7052) | ⭐⭐ 中 — 企业用户明确诉求 |
| 按 Agent/会话级别配置 `reasoning_effort` | [#7062](https://github.com/agentscope-ai/QwenPaw/issues/7062) | ⭐⭐ 中 — 区分不同角色思考深度 |
| 技能池增加搜索/过滤 | [#7090](https://github.com/agentscope-ai/QwenPaw/issues/7090) | ⭐⭐ 低 — 体验优化 |
| view_video 内联大小限制可配置化 | [#7071](https://github.com/agentscope-ai/QwenPaw/pull/7071) | ⭐⭐ 中 — PR 已提交，待合并 |
| 统一 Marketplace 页面（Apps/Plugins/Skills） | [#6880](https://github.com/agentscope-ai/QwenPaw/pull/6880) | ⭐⭐⭐ 高 — PR 已提交，审查中 |
| 本地隔离 QwenPaw Pro 控制面板 | [#7112](https://github.com/agentscope-ai/QwenPaw/pull/7112) | ⭐⭐ 中 — 企业部署方向，Draft 状态 |
| 智能邮件管理助手 | [#6800](https://github.com/agentscope-ai/QwenPaw/pull/6800) | ⭐⭐ 中 — 新功能提案 |
| 沙箱 `~` 路径展开修复 | [#7116](https://github.com/agentscope-ai/QwenPaw/pull/7116) | ⭐⭐⭐ 高 — 直接解决 #7005 用户痛点 |
| 安全加固：Shell 逃避检测默认开启 | [#7120](https://github.com/agentscope-ai/QwenPaw/pull/7120) | ⭐⭐⭐ 高 — 7项检测项默认启用 |
| 安全加固：master key 文件权限修复 | [#7119](https://github.com/agentscope-ai/QwenPaw/pull/7119) | ⭐⭐⭐ 高 — 修复权限不匹配 |
| Inbox 通知静默优化 | [#7115](https://github.com/agentscope-ai/QwenPaw/pull/7115) | ⭐⭐ 中 — 减少定时任务噪音 |

---

## 7. 用户反馈摘要

### 痛点
- **"重启后频道连接需手动恢复"** (#6684) — 自建 Matrix 等服务不稳定场景下，缺乏健康检测与自动重试是最突出的抱怨。
- **"多步任务执行到规划阶段就停"** (#6921) — 用户期望 Agent 能自主完成全链路执行，而非每次停在规划节点等待确认。
- **"含一个坏图片链接，整个会话报废"** (#7110) — 容错性差，唯一恢复手段是 `/clear`，用户体验极差。
- **"QwenPaw Creator 安装失败"** (#7076, #6683) — 插件安装与加载存在兼容性问题，`utils` 命名冲突已修复但新版本的 404 错误仍需跟进。
- **"Malware Bytes 报 Trojan Loader"** (#6775) — 安全软件误报引发用户信任危机，需官方回应。

### 正面反馈
- **#6260** 点赞数唯一，用户认可"折叠思考过程"的方向，侧面反映 v2.1.0 的流式输出呈现仍有优化空间。
- **#7039** 用户肯定了公式显示正常等改进，同时对"文件点击自动预览"行为表示不满，期望提供开关。

---

## 8. 待处理积压

| Issue/PR | 类型 | 说明 | 建议 |
|---|---|---|---|
| [#7063](https://github.com/agentscope-ai/QwenPaw/issues/7063) | Bug 🔴 | `async for` 对 coroutine 崩溃，必现于工具调用 | **紧急** — 应在 v2.1.1 修复 |
| [#7082](https://github.com/agentscope-ai/QwenPaw/issues/7082) | Bug 🔴 | Pydantic `_StructuredOutputDynamicClass` 未 fully defined | **紧急** — 影响 model execution |
| [#7102](https://github.com/agentscope-ai/QwenPaw/issues/7102) | Bug 🔴 | 会话冻结 >10 分钟无输出 | **高** — 需追踪 glm 模型路径 |
| [#6684](https://github.com/agentscope-ai/QwenPaw/issues/6684) | Feature | 频道重试功能 | 与 #5900 合并评估，纳入稳定性专项 |
| [#5900](https://github.com/agentscope-ai/QwenPaw/issues/5900) | Bug | MCP streamable_http 断连无自动重连 | 同上 |
| [#7053](https://github.com/agentscope-ai/QwenPaw/issues/7053) | Bug | OAuth2 refresh_token 不旋转持久化 | [#7066](https://github.com/agentscope-ai/QwenPaw/pull/7066

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 | 2026-08-19

## 1. 今日速览
过去24小时 ZeroClaw 保持高频迭代节奏，Issues 与 PR 更新量均达 50 条，社区与核心贡献者活跃度维持高位。当日关闭 19 个 Issue、合并/关闭 2 个 PR，无新版本发布，项目处于密集功能打磨与架构 RFC 收敛期。整体健康度良好：安全策略对齐、Windows CI 兼容性、依赖治理与 Agent 运行时优化并行推进，技术债清理与主线功能开发节奏均衡。

## 2. 版本发布
无新版本发布。当前阶段以 RFC 推进、依赖升级与安全审计为主，未触发独立 Release 节点。

## 3. 项目进展
- **#7415** [CLOSED] Agent turn 引擎统一 RFC 已按维护者方向以单 PR（#7540）形式执行落地，标志着多引擎协调架构正式收敛。[链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7415)
- **#10009** [CLOSED] `fix(memory): key conversation autosave suppression on turn origin` 已合并，修复了心跳任务干扰对话自动保存过滤逻辑的缺陷。[链接](https://github.com/zeroclaw-labs/zeroclaw/pull/10009)
- **#8059 / #10097** [CLOSED] 依赖审计策略清理与 advisory scan 告警闭环完成，`deny.toml`/`audit.toml` 漂移问题得到阶段性治理。[链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8059)

## 4. 社区热点
- **#8303** [OPEN] `RFC: Goal mode v1 — bounded foreground Matrix work`（22 评论，1 👍）：讨论最长，聚焦多轮 Agent 对话中的持久目标追踪与有界执行模型，已成为架构层核心议题。[链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8303)
- **#7462** [OPEN] `[Bug]: 74 test failures on Windows`（17 评论）：Windows 11 路径语义、控制台编码与 CI 缺失导致测试大面积失败，社区关注度极高。[链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7462)
- **#7929** [OPEN] `Unify slash-command registries across web UI, ZeroCode TUI, and channel runtime`（8 评论）：三端斜杠命令注册表漂移问题引发一致性与维护成本讨论。[链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7929)
- **#8519** [OPEN] `Reconcile cargo-audit ignores and remediate wasmtime-wasi CVEs`（6 评论）：安全审计与依赖策略双轨配置的 drift 问题，涉及 wasmtime-wasi CVE 修复路径。[链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8519)

## 5. Bug 与稳定性
| 级别 | 问题 | 状态 | Fix PR |
|---|---|---|---|
| P1/S1 | **#8563** SOPs 在 Web Dashboard 中未被 Agent 运行时识别（工作流阻断） | ✅ Closed | — |
| P1 | **#8642** MCP/tool-schema 克隆导致 Agent 循环内 RSS 无界增长（WSL2 OOM 关联路径） | 🔵 Open | 需跟进 |
| P1 | **#10107** Google STT API Key 被拼入请求 URL，存在凭证泄露风险 | 🔵 Open（PR） | [#10107](https://github.com/zeroclaw-labs/zeroclaw/pull/10107) |
| P1 | **#9743** modalities parser 未接入 `capabilities_for_model`，能力识别断裂 | 🔵 Open | [#9743](https://github.com/zeroclaw-labs/zeroclaw/pull/9743) |
| P2 | **#7462** Windows 测试套件 74 项失败（路径/编码/CI 缺失） | 🔵 Open | 待合入 |
| P2 | **#8410** 条件型 Channel Task 在无需回复时仍发送可见空响应 | 🔵 Open | 待合入 |
| P3 | **#10009** 对话自动保存抑制逻辑受心跳任务干扰 | ✅ Closed/Merged | [#10009](https://github.com/zeroclaw-labs/zeroclaw/pull/10009) |

## 6. 功能请求与路线图信号
- **Goal 模式与持久化目标**：#8303（Goal mode v1）与 #9998（Session-scoped persistent prompt attachments）均指向 Agent 多轮任务连贯性，极可能纳入下一版本核心能力。
- **Provider 扩展**：Hailo-Ollama 原生支持（#9109）、Grok Build ACP（#9104）、Anthropic OAuth 存储配置（#9420）PR 已进入评审，显示项目正加速补齐垂直/新型 Provider 接入。
- **Channel 体验升级**：DingTalk 流式消息（#8228）、Telegram 安全 Model Picker（#9997）持续贡献，反映用户对低延迟与多端一致性的强需求。
- **安全与配置架构**：`KeySource` trait 提取（#9194）、TodoWrite 显示配置下沉至 zerocode（#9013）表明运行时抽象层与隐私边界正在重构，预计影响后续配置 Schema。
- **可观测性精简**：#9451 废弃 DORA telemetry，路线趋向轻量可观测性，减少无关指标噪音。

## 7. 用户反馈摘要
- **痛点集中区**：Windows 环境兼容性（#7462）、条件任务空响应干扰（#8410）、API 凭证意外暴露（#10107）、MCP 内存泄漏（#8642）。
- **使用场景诉求**：跨 Channel/零代码/TUI 的命令与配置一致性（#7929、#8584、#8383）；Session 历史与持久记忆的明确边界（#9341、#10009）。
- **正向信号**：RFC 驱动架构演进获得广泛认可；安全策略（`deny.toml`/`audit.toml`）主动对齐；Provider/Channel 适配响应速度快，社区贡献活跃。

## 8. 待处理积压
| Issue/PR | 说明 | 建议关注 |
|---|---

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*