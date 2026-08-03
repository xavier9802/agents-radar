# OpenClaw 生态日报 2026-08-03

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-03 03:35 UTC

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



# OpenClaw 项目日报 | 2026-08-03

## 1. 今日速览

OpenClaw 今日保持极高活跃度：过去 24 小时新增/活跃 Issue 449 条、PR 367 条，共关闭 Issue 51 条、合并/关闭 PR 133 条，日均吞吐量超过 500 条。v2026.7.2-beta.7 聚焦**状态安全与崩溃恢复**，引入隔离存储、SQLite 快照、模式升级回滚拒绝等机制，标志着项目在数据可靠性方向迈出关键一步。社区核心关注点集中在：子代理完成交付可靠性、认证状态泄漏、DeepSeek/飞书/TWhatsApp 通道异常，整体健康度良好但子代理链路的稳定性仍需持续攻坚。

---

## 2. 版本发布

### v2026.7.2-beta.7

**核心更新：State Safety and Recovery**
- **Quarantine Store**：在持久化数据层引入隔离存储，主数据库受损时仍可存活恢复。
- **Crash-recoverable SQLite Snapshots**：崩溃后可从快照恢复数据库状态。
- **Crash-durable Filesystem Publication**：文件系统发布操作具备崩溃恢复能力。
- **Schema-upgrade Data-loss Rejection**：模式升级若存在数据丢失风险将被拒绝，而非静默执行。
- **Rollback-writer Snapshot Recovery**：支持回滚写入器的快照恢复路径。

**迁移注意事项**：
- 升级前建议备份 `state/openclaw.sqlite`；本次版本新增了迁移前的快照机制，旧版本可直接升级，但需确保磁盘空间足够存放快照副本。
- 涉及子代理交付链路的进程（如 Codex 绑定）可能触发新的 tombstone 清理逻辑，请参见 Issue #116022。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#118064](https://github.com/openclaw/openclaw/pull/118064) | fix(line) | LINE 位置消息校验：拒绝标题或地址为空的非法位置消息，防止空数据到达 LINE API |
| [#118323](https://github.com/openclaw/openclaw/pull/118323) | refactor(opencode) | 合并 OpenCode 会话目录测试夹具，提升安全敏感测试的可审查性 |
| [#117697](https://github.com/openclaw/openclaw/pull/117697) | fix(whatsapp) | 自动回复时保留消息方向，修复机器人链接账号时自我消息误判问题 |

### 待合并关键 PR（高优先级）

- **#118360** — 子代理完成交付持久化与可恢复性（修复 #112616），解决自动重试 3 次后结果永久丢失问题
- **#118296** — 防止子代理内部完成事件泄漏到聊天频道（修复 #110378）
- **#113567** — 模式迁移前快照状态数据库，防止升级中断导致数据损坏
- **#117951** — Gateway 直播消息中保留助手媒体内容（图片+文本）
- **#116248** — 修复 `paste-api-key --agent <non-default>` 后默认 agent 丢失凭证的回归

---

## 4. 社区热点

| Issue | 标题 | 评论数 | 状态 | 链接 |
|-------|------|--------|------|------|
| #116277 | DeepSeek v4 Flash 静默回复失败 | 87 | ✅ 已关闭 | [链接](https://github.com/openclaw/openclaw/issues/116277) |
| #116201 | 实时语音工作可保留无界 provider 状态 | 51 | 🔄 开放 | [链接](https://github.com/openclaw/openclaw/issues/116201) |
| #115326 | 崩溃循环断路器永久屏蔽 Discord/WhatsApp | 26 | ✅ 已关闭 | [链接](https://github.com/openclaw/openclaw/issues/115326) |
| #91009 | Codex PreToolUse hook 导致 CPU 爆满并卡住 Gateway RPC | 19 | 🔄 开放 | [链接](https://github.com/openclaw/openclaw/issues/91009) |
| #48003 | Steer 模式未在 turn 中途注入消息 | 16 | 🔄 开放 | [链接](https://github.com/openclaw/openclaw/issues/48003) |

**热点分析**：
- **DeepSeek v4 Flash 静默失败**（#116277）是今日最高关注 Issue，反映用户对特定模型回退行为的不满，已关闭但说明模型兼容层仍有脆弱点。
- **子代理交付丢失**（#67777、#92433、#47975）形成聚类讨论，社区强烈诉求提升子代理链路的可靠性，PR #118360 正是对此的直接回应。
- **CPU 泄漏**（#91009）自 6 月持续至今，说明短生命周期进程的 fork/spawn 管理是长期痛点。

---

## 5. Bug 与稳定性

### 高严重度（P0/P1）

| Issue | 描述 | 严重程度 | Fix PR |
|-------|------|----------|--------|
| #115421 | Schema 降级恢复错误隔离/清空状态 DB，导致 cron 任务丢失 | P0 | — |
| #117956 | `CLAUDE_CLI_CLEAR_ENV` 未彻底清理 Anthropic API Key，单日产生 ~13.7M token 计费 | P1 | — |
| #116010 | 所有持久会话上下文被硬编码限制在 128k，忽略模型实际支持 | P1 | — |
| #111498 | Anthropic 认证恢复后，主 Agent 仍被持久化的 workspace-state 迁移阻塞 | P1 | — |
| #114211 | Matrix 房间 Agent 陷入"无回复"死循环，重启后回放陈旧会话状态 | P1 | — |
| #116022 | beta.5 的 `/new` 复用了已退休的 Codex binding tombstone，无法恢复 | P1 | — |
| #99586 | Gateway 操作后 runtime tool surface 返回空白 body | P1 | — |
| #106231 | 循环检测阻止 exec 但无法终止卡住的 agent run，资源持续消耗 | P1 | — |

### 中等严重度（P2）

| Issue | 描述 | Fix PR |
|-------|------|--------|
| #57901 | Safeguard compaction 忽略 `compaction.model` 配置 | — |
| #74586 | AM embedded run 在模型已完成时仍中止 `memory_search` 并误判为超时 | — |
| #50093 | WhatsApp 重连后无法回填丢失消息 | — |
| #53408 | 长对话后 `write`/`exec` 工具参数静默丢失 | — |
| #52249 | ACP 子代理完成后父会话卡死，需手动刷新 | — |
| #115001 | 混合记忆搜索通过 FTS LIKE 回退返回虚假 1.0 相似度分 | — |

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 路线图判断 |
|----------|----------|------------|
| #52640 | 为长 turn 提供持久化任务状态表面（Discord 优先） | 🟡 可能纳入后续版本，属于 UX 体验层优化 |
| #71195 | macOS Talk Mode 支持 OpenAI Realtime（speech-to-speech），对齐 voice-call 插件体验 | 🟢 与 #71195 PR 相关，sub-second turn latency 是明确目标 |
| #71058 | 单 Gateway 支持多个 Azure/Teams Bot | 🟡 架构扩展需求，涉及 provider 多实例化 |
| #113251 | WebChat 文件查看器支持图片浏览 | 🟢 低投入高感知，可能被快速纳入 |
| #51441 | 在 session_status 中暴露解析后的后端模型（解决 LiteLLM 路由黑盒） | 🟡 可观测性需求，符合项目向 enterprise 推进的方向 |
| #50291 | Plugin Hooks 补充 trace context（messageId, runId, parentSpanId） | 🟡 分布式追踪能力，适合后续 observability 专项 |
| #101665 | 允许插件工具 yield turn（外部交互回调不抢跑） | 🟢 PR 已开放，是插件生态成熟的关键基础设施 |
| #103991 | 新增 `/verbose commentary` 模式，仅显示叙述而不显示 tool 摘要 | 🟡 细粒度可控性需求，影响跟踪体验 |
| #106818 | 发布 linux/riscv64 Docker 镜像 | 🟡 边缘/低成本部署场景，维护成本可控时可纳入 |

---

## 7. 用户反馈摘要

**核心痛点**：
1. **子代理链路可靠性**：多个 Issue（#67777、#92433、#47975、#52249）交叉反映同一问题——子代理完成交付在超时、drain、孤儿清理场景下静默丢失，用户称"结果不可追踪"。
2. **认证状态泄漏与计费异常**：#117956 用户报告 `CLAUDE_CLI_CLEAR_ENV` 未能彻底清理 `ANTHROPIC_API_KEY`，导致单日 13.7M token 意外计费，引发对 sandbox 隔离机制的信任危机。
3. **WhatsApp 断连消息丢失**：#50093 长期存在，用户反馈 503 断线期间的消息静默丢失，缺乏 backfill 机制。
4. **模型选择器行为不一致**：#109017 反映 Anthropic 模型目录是静态的，新模型（Fable 5 / Haiku 4.5）不会自动出现；#47840 指出 Control UI 显示原始 provider 名称（如 `bailian`）而非归一化值（`zai`），造成混淆。
5. **飞书 Mention 解析失效**：#48786 和 #50490 反映飞书群聊中 `@user` 引用显示为原始占位符，激活模式切换无效。

**用户满意度信号**：
- v2026.7.2-beta.7 的状态安全机制获得正面预期，用户此前多次遭遇 schema 升级中断导致数据损坏（#115421），新快照机制有望缓解。
- WebChat 图片查看（#113251）和 `/btw` 侧边问题修复（#118396）属于高感知低成本的体验改善，用户反馈积极。

---

## 8. 待处理积压

| Issue/PR | 类型 | 持续时间 | 提醒 |
|----------|------|----------|------|
| #91009 | Bug：Codex PreToolUse hook CPU 泄漏 | ~59 天 | 需 maintainer 介入确认 root cause |
| #48003 | Bug：Steer 模式未中途注入消息 | ~140 天 | 涉及 `KeyedAsyncQueue` 核心逻辑，需产品决策 |
| #50093 | Feature：WhatsApp 重连消息回填 | ~137 天 | 长期诉求，可考虑作为 channel 可靠性专项 |
| #54488 | Bug：Session lane starvation 导致入站 dispatch 阻塞 20-30 分钟 | ~131 天 | P1，影响多租户场景 |
| #55694 | Bug：工具调用失败导致 Agent 死循环刷屏 | ~130 天 | 中文社区高频反馈，需 loop detection 增强 |
| #110692 | Bug：Codex loopback WS 

---

## 横向生态对比



# AI 智能体开源生态横向对比分析
**日期：2026-08-03 | 分析师：Agnes**

---

## 1. 生态全景

个人 AI 助手与自主智能体开源生态呈现"一超多强、分层演进"格局。OpenClaw 以日均 800+ 条社区吞吐量保持绝对领先，成为生态基座；ZeroClaw 与 Hermes Agent 以高频迭代紧随其后，聚焦安全架构与 Desktop 体验；NanoBot、CoPaw、PicoClaw 等差异化项目各自深耕垂直场景。整体生态正从功能扩张转向可靠性加固与生产级稳定性建设，子代理链路、认证安全、跨平台兼容性成为共同攻坚方向。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PR (24h) | 发布 | 健康度 | 核心阶段 |
|------|-------------|----------|------|--------|----------|
| **OpenClaw** | 449 | 367 | v2026.7.2-beta.7 | 🟢 优秀 | 状态安全与崩溃恢复 |
| **ZeroClaw** | 50 | 50 | v0.8.4 (262 commits/49 contributors) | 🟢 优秀 | 安全架构定型 |
| **Hermes Agent** | 50 | 50 | 无 | 🟢 良好 | Desktop 稳定性攻坚 |
| **CoPaw** | 13 | 28 | 无 | 🟢 良好 | 2.0.1 稳定性收尾 |
| **NanoClaw** | 1 | 10 | 无 | 🟢 良好 | 容器化与多渠道扩展 |
| **PicoClaw** | 3 | 9 | 无 | 🟢 良好 | 安全加固与体验修复 |
| **IronClaw** | 8 | 31 | 无 | 🟢 良好 | Wave 2 架构治理 |
| **LobsterAI** | 3 | 6 | 无 | 🟡 平稳 | 性能优化与体验打磨 |
| **Moltis** | 0 | 1 | 无 | 🟢 良好 | MCP 仓库管理演进 |
| **NanoBot** | 1 | 15 | 无 | 🟢 良好 | Windows 兼容与渠道修复 |
| **NullClaw** | 0 | 0 | 无 | ⚪ 休眠 | — |
| **ZeptoClaw** | 0 | 0 | 无 | ⚪ 休眠 | — |

---

## 3. OpenClaw 在生态中的定位

**生态基座与参照系**。OpenClaw 以 10 倍于次级项目的 Issue/PR 吞吐量（816 条 vs 行业均值 ~30 条），构建了最完整的渠道生态（LINE/WhatsApp/DeepSeek/飞书等）与子代理协议体系。

| 维度 | OpenClaw | 同类对比 |
|------|----------|----------|
| **社区规模** | 日均 800+ 吞吐，Issue #116277 单条 87 评论 | ZeroClaw 最高 17 评论；Hermes 次之 |
| **技术路线** | 状态安全优先（Quarantine Store/SQLite 快照） | ZeroClaw 同步强调安全架构；Hermes 聚焦 Desktop |
| **版本节奏** | beta 高频迭代（v2026.7.2-beta.7） | 多数项目以 patch/stable 为主 |
| **子代理生态** | 最完整，PR #118360 直接回应交付可靠性诉求 | NanoBot/CoPaw 均有子代理但规模较小 |

**差异化优势**：OpenClaw 在数据可靠性（schema 升级拒绝数据丢失）、子代理链路可观测性、多渠道兼容性方面处于领先，是生态中"生产级稳定性"的标杆参照。

---

## 4. 共同关注的技术方向

### 4.1 子代理/多代理链路可靠性
| 项目 | 具体诉求 |
|------|----------|
| OpenClaw | PR #118360 修复子代理完成交付永久丢失；Issue #67777/#92433/#47975 聚类讨论 |
| CoPaw | PR #6609 修正 spawn_subagent 参数 Schema；Issue #52249 父会话卡死 |
| NanoBot | PR #5152 修复子代理部分完成结果标记 |

### 4.2 认证安全与凭证隔离
| 项目 | 具体诉求 |
|------|----------|
| OpenClaw | Issue #117956 报告 API Key 未彻底清理导致 13.7M token 意外计费 |
| ZeroClaw | Issue #9565 S0 级安全：webhook 未 fail-closed；RFC #7141 可插拔认证架构 |
| NanoClaw | Issue #3175 writeOutboundDirect 绕过单一写入器规则 |
| Hermes Agent | PR #75263 修复 multiplex profile 冷启动密钥注入 |

### 4.3 跨平台/容器化稳定性
| 项目 | 具体诉求 |
|------|----------|
| NanoBot | PR #5191 修复 Windows MIME 类型导致前端加载失败；Issue #5190 高频反馈 |
| PicoClaw | PR #3297 安全加固（schema v4 迁移）；Issue #3311 工具循环静默挂起 |
| ZeroClaw | Issue #9624 Registry WIT pin 分叉；Issue #9690 MSRV 升级导致 Docker 构建失败 |
| Hermes Agent | Issue #74554 linux/arm64 Docker 镜像包含 x86_64 wheels |

### 4.4 多渠道协议适配
| 项目 | 具体诉求 |
|------|----------|
| OpenClaw | LINE 位置消息校验（#118064）、WhatsApp 断连消息丢失（#50093）、飞书 Mention 解析失效（#48786） |
| NanoClaw | PR #3041/3050 系统性拓展 Dial SMS/语音通话；PR #301 Telegram 技能重构 |
| ZeroClaw | PR #9571 移除 WATI Channel；RFC #8603 Chat Completions 协议适配 |
| LobsterAI | PR #1215 IM 配置刷新缺陷；Issue #1287 连通性测试校验不严 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构特征 |
|------|----------|----------|--------------|
| **OpenClaw** | 全渠道集成+子代理协议+状态安全 | 企业级部署、多通道运营 | Rust 核心，SQLite 持久化，Quarantine Store 隔离架构 |
| **ZeroClaw** | 安全架构+协议扩展+可观测性 | 安全敏感场景、开源贡献者 | Rust，RFC 驱动的架构演进，WASM plugin 生态 |
| **Hermes Agent** | Desktop 体验+CLI+成本透明 | 个人高级用户、Power User | Desktop/CLI 双栈，multiplex profile，成本计量内建 |
| **CoPaw** | 多智能体协作+子代理调度 | 团队协作、Agent 编排场景 | 基于 agentscope 生态，Tauri 桌面端，2.0.1 稳定性期 |
| **NanoClaw** | 容器化部署+多渠道扩展 | DevOps 友好、私有化部署 | Docker-first，MCP 原生支持，Skill 化架构 |
| **NanoBot** | Windows 兼容+WebUI 体验 | 个人用户、Windows 生态 | WebUI 优先，RTK 沙箱包装，Gemini/Codex 多 provider |
| **PicoClaw** | 安全边界+执行控制 | 安全敏感、边缘部署 | customAllowPatterns 权限模型，工具失败提前终止 |
| **IronClaw** | CI/CD 治理+架构文档 | 大型团队、合规场景 | Wave 2 架构，动态 PR 测试范围，覆盖率门禁 |
| **LobsterAI** | IM 机器人集成+定时任务 | 中文用户、自动化办公 | 钉钉/Telegram 深度集成，React 前端性能优化 |
| **Moltis** | MCP 仓库管理 | MCP 生态建设者 | 仓库级 bundles 管理，Vault 版本化存储 |

---

## 6. 社区热度与成熟度分层

### 🟢 快速迭代期（高吞吐、新功能密集）
| 项目 | 特征 | 证据 |
|------|------|------|
| OpenClaw | 日均 800+ 吞吐，beta 高频发布 | 449 Issue + 367 PR，v2026.7.2-beta.7 |
| ZeroClaw | 维护版本 + RFC 并行推进 | v0.8.4 (262 commits/49 contributors)，4 个高评论 RFC |
| Hermes Agent | Desktop 问题集中爆发与快速修复 | 50 Issue + 50 PR，同日多个 P0 修复 PR |
| CoPaw | 上游依赖同步 + 稳定性加固 | 13 Issue + 28 PR，首次贡献者占比 40% |

### 🟡 质量巩固期（中等吞吐、体验打磨）
| 项目 | 特征 | 证据 |
|------|------|------|
| NanoBot | Bug 响应及时，积压可控 | 15 PR/9 合并，2 个 P1 待处理 |
| PicoClaw | 安全与体验并重 | 9 PR/3 Issue，stale 标签需关注 |
| NanoClaw | 有序推进，协作顺畅 | 10 PR/7 待合并，无紧急问题 |
| IronClaw | CI 治理+架构定型 | 31 PR/9 合并，Wave 2 文档收敛 |
| LobsterAI | 性能攻坚+技术债清理 | 6 PR/4 待合并，Dependabot 自动化 |

### 🟢 稳定演进期（低吞吐、方向明确）
| 项目 | 特征 | 证据 |
|------|------|------|
| Moltis | 单 PR 推进，无紧急问题 | 1 PR，MCP bundles 方向明确 |
| NullClaw/ZeptoClaw | 无活动 | 休眠状态 |

---

## 7. 值得关注的趋势信号

### 7.1 状态安全成为基础设施级诉求
OpenClaw 的 Quarantine Store + SQLite 快照机制、ZeroClaw 的 SOP 控制面扩展、NanoClaw 的单一写入器规则，共同指向一个趋势：**AI 智能体系统正从"功能正确"转向"数据可靠"**。schema 升级中断、崩溃后状态丢失、并发写入冲突已成为生产环境的主要故障源。

### 7.2 子代理链路可靠性是下一个攻坚高地
OpenClaw（PR #118360）、CoPaw（PR #6609）、NanoBot（PR #5152）同日或近期均提交子代理交付修复，反映多代理架构的"交付可见性"尚未成熟。社区反馈"结果不可追踪"（OpenClaw #67777）是明确的产品信号。

### 7.3 认证隔离与成本透明化需求激增
OpenClaw #117956（13.7M token 意外计费）、Hermes Agent #77221（缺少成本面板）、ZeroClaw RFC #7141（可插拔认证）共同表明：**用户付费透明度与凭证隔离**已成为产品信任的基础设施，而非可选功能。

### 7.4 跨平台兼容性从"能跑"转向"体验一致"
NanoBot Windows MIME 修复（#5191）、Hermes arm64 镜像错误（#74554）、PicoClaw 工具失败静默（#3311）反映：早期"可用即可"的跨平台策略已进入瓶颈，**平台一致性体验**成为下一阶段竞争点。

### 7.5 MCP 生态从"单点集成"走向"仓库级编排"
Moltis PR #1183 的仓库 bundles 管理、NanoClaw PR #3092 的远程 Streamable HTTP MCP、ZeroClaw 的多 provider 生态，共同指向 MCP 协议正从"工具发现"演进为"配置版本化+批量部署"的基础设施。

---

**总结**：2026 年 Q3 的开源智能体生态已进入"可靠性优先"阶段。OpenClaw 以基座姿态引领状态安全方向，ZeroClaw 与 Hermes Agent 在安全架构与 Desktop 体验形成差异化竞争，NanoBot/CoPaw 等深耕垂直场景。对开发者而言，子代理交付链路、认证隔离机制、跨平台一致性是当下最值得投入的基础设施方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-03

---

## 1. 今日速览

过去24小时 NanoBot 保持中等活跃度：共处理 **16 条** 仓库更新（1 Issue + 15 PR），其中 **9 条 PR 已合并/关闭**，**6 条 PR 仍待处理**。无新版本发布。项目维护者 chengyongru 贡献密集，聚焦 WebUI 稳定性、渠道恢复与性能优化；arcdrake22 主导了多个 P1 优先级修复。整体健康度良好，Bug 响应及时，但积压的 6 个开放 PR 中有 2 个 P1 级问题需尽快跟进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（9 条）

| PR | 类型 | 作者 | 进展说明 |
|---|---|---|---|
| [#5191](https://github.com/HKUDS/nanobot/pull/5191) | 🔧 Fix (P2) | amkile | **Windows 静态资源 MIME 类型注册修复**——解决 Windows 下 `.js` 文件因注册表关联导致 `text/plain` 返回、前端模块加载失败的问题，直接关闭 Issue #5190。 |
| [#5216](https://github.com/HKUDS/nanobot/pull/5216) | 🔧 Fix (P2) | arcdrake22 | **Gemini Flash 图片生成参数修复**——修正 aspect ratio / 尺寸提示未通过 `generationConfig.imageConfig` 传递导致的 `HTTP 400 INVALID_ARGUMENT` 错误。 |
| [#5217](https://github.com/HKUDS/nanobot/pull/5217) | 🔧 Fix (P2) | chengyongru | **WebUI 回放消息时间戳显示**——用户消息显示持久化创建时间，助手消息优先展示完成时间，回放消息（含 cron/proactive）兜底使用创建时间。 |
| [#4854](https://github.com/HKUDS/nanobot/pull/4854) | ✨ Feature (P2) | chengyongru | **RTK 命令重写器**——新增 opt-in `tools.exec.rtk` 配置，在沙箱包装前对命令进行重写，并过滤 RTK hook 噪音。 |
| [#4833](https://github.com/HKUDS/nanobot/pull/4833) | 🔧 Fix (P1) | chengyongru | **持久化目标（sustained goals）运行时门控**——将 `long_task`/`complete_goal` 替换为仅在 `/goal` 或活跃目标回合注入的 `create_goal`/`update_goal`，减少工具噪声。 |
| [#4822](https://github.com/HKUDS/nanobot/pull/4822) | 🔧 Fix (P2) | chengyongru | **WebUI 流式回复保留自动化源标记**——修复 `delta`/`stream_end` 事件中自动化来源元数据丢失导致徽章不显示的问题。 |
| [#5196](https://github.com/HKUDS/nanobot/pull/5196) | 🔧 Fix (P2) | chengyongru | **微信频道会话过期恢复**——修复 `errcode -14` 触发 60 分钟暂停后，频道未能加载刷新状态的问题（修复 #5195）。 |
| [#5194](https://github.com/HKUDS/nanobot/pull/5194) | ⚡ Perf (P2) | chengyongru | **WebUI 会话列表与线程加载加速**——复用 activity 目录与 workspace scope，缓存 workspace-scope 快照以加速 session-list index。 |
| [#4021](https://github.com/HKUDS/nanobot/pull/4021) | 🔧 Fix | eldar702 | **Codex provider reasoning 项去重**——修复 OpenAI Responses API 因重复 `reasoning` 项返回 400 导致多轮对话中断的问题（修复 #3633）。 |

**项目整体推进评估**：本次迭代重点强化了 **Windows 平台兼容性**、**Gemini 图片能力可用性**、**WebUI 回放体验** 以及 **多通道稳定性（微信）**，同时在底层清理了 Codex 与 Goals 两个长期存在的隐患。项目向生产级稳定性迈进明显。

---

## 4. 社区热点

| 项目 | 状态 | 说明 |
|---|---|---|
| [Issue #5190](https://github.com/HKUDS/nanobot/issues/5190) | ✅ 已关闭 | Windows 前端模块加载失败问题，用户 amkile 报告后迅速由同作者提交 PR #5191 修复并关闭，响应链路高效。 |
| [PR #5214](https://github.com/HKUDS/nanobot/pull/5214) | 🟡 待合并 (P1) | OpenAI Responses API 因请求体反序列化失败时无优雅回退，用户反馈频繁遇到终端错误，社区关注度高。 |
| [PR #5211](https://github.com/HKUDS/nanobot/pull/5211) | 🟡 待合并 | 跨会话搜索与 `@` 提及功能，直接回应多会话场景下的用户导航需求，预计影响面广。 |
| [PR #5212](https://github.com/HKUDS/nanobot/pull/5212) | 🟡 待合并 | MiniMax 音乐生成支持，填补现有音乐 provider 的配置发现空白。 |

---

## 5. Bug 与稳定性

| 严重程度 | 问题 | 状态 | 修复 PR |
|---|---|---|---|
| 🔴 P1 | [PR #5214](https://github.com/HKUDS/nanobot/pull/5214) — OpenAI Responses API 反序列化失败后无回退，导致对话终止 | 待合并 | 同 PR 提供 `chat completions` 降级路径 |
| 🔴 P1 | [PR #5215](https://github.com/HKUDS/nanobot/pull/5215) — Gateway 停止时 exec/MCP 子进程未确定性清理，引发 `RuntimeError: Event loop is closed` | 待合并 | 同 PR 实现确定性资源关闭 |
| 🟡 P2 | [Issue #5190](https://github.com/HKUDS/nanobot/issues/5190) / [PR #5191](https://github.com/HKUDS/nanobot/pull/5191) — Windows 下 `.js` MIME 类型错误导致前端模块加载失败 | ✅ 已修复 | PR #5191 |
| 🟡 P2 | [PR #5216](https://github.com/HKUDS/nanobot/pull/5216) — Gemini Flash 图片模型传入尺寸/比例提示时返回 400 | ✅ 已修复 | PR #5216 |
| 🟡 P2 | [PR #5217](https://github.com/HKUDS/nanobot/pull/5217) — WebUI 回放消息无时间戳显示 | ✅ 已修复 | PR #5217 |
| 🟡 P2 | [PR #5196](https://github.com/HKUDS/nanobot/pull/5196) — 微信频道会话暂停后状态未刷新 | ✅ 已修复 | PR #5196 |
| 🟡 P2 | [PR #4021](https://github.com/HKUDS/nanobot/pull/4021) — Codex provider 重复 reasoning 项导致 400 | ✅ 已修复 | PR #4021 |
| 🟡 P2 | [PR #5152](https://github.com/HKUDS/nanobot/pull/5152) — 子代理部分完成结果未正确标记，可能误导模型推断 | 待合并 | 同 PR 添加 `subagent_remaining_count` 元数据 |

**稳定性评估**：今日共修复 6 个已合并 Bug，涵盖 Windows 兼容、多 provider 错误处理及 WebUI 回放体验。仍有 2 个 P1 级问题（PR #5214、#5215）待合并，建议优先审核。

---

## 6. 功能请求与路线图信号

| PR | 类型 | 分析 |
|---|---|---|
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | ✨ Feature | **跨会话搜索与提及**——允许用户通过 `@` 面板引用历史会话，并支持 bounded read-only 访问。反映多会话协作场景的真实需求，可能被纳入下一版本。 |
| [#5212](https://github.com/HKUDS/nanobot/pull/5212) | ✨ Feature | **MiniMax 音乐生成支持**——扩展音乐 provider 生态，已有完整 tool contract 实现，纳入可能性高。 |
| [#5213](https://github.com/HKUDS/nanobot/pull/5213) | 🔧 Fix | **pip 不可用时 fallback 到 uv**——解决 `uv tool` 环境下插件安装失败问题，属于兼容性增强，预计快速合并。 |

**路线图信号**：项目正朝 **多会话管理能力**、**provider 生态扩展**（音乐、图片）和 **部署环境兼容性** 三个方向演进。

---

## 7. 用户反馈摘要

- **Windows 用户体验**：amkile 报告的前端模块加载失败（Issue #5190）是 Windows 用户的长期痛点，根源在于 Windows 注册表将 `.js` 关联至 Windows Script Host 而非 Web JavaScript，修复后 Windows 用户可正常使用 WebUI。
- **Gemini 图片能力**：arcdrake22 发现 Gemini Flash 图片模型因参数格式错误持续返回 400，影响了图片生成工作流的可用性，修复后参数正确路由至 `imageConfig`。
- **微信稳定性**：微信频道在 `errcode -14` 后进入 60 分钟暂停，若此时刷新 `account.json`，旧会话状态未能同步，导致消息收发异常，该问题已修复。
- **WebUI 回放体验**：用户反馈回放消息（含 cron 触发消息）无时间戳，影响对话上下文理解，现已修复。

---

## 8. 待处理积压

| PR | 优先级 | 创建时间 | 说明 | 风险 |
|---|---|---|---|---|
| [#5214](https://github.com/HKUDS/nanobot/pull/5214) | 🔴 P1 | 2026-08-02 | OpenAI Responses API 反序列化失败时无降级路径 | 高——影响 OpenAI provider 用户对话稳定性 |
| [#5215](https://github.com/HKUDS/nanobot/pull/5215) | 🔴 P1 | 2026-08-02 | Gateway 停止时子进程未确定性清理 | 高——可导致停止操作卡死 |
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | 🟡 — | 2026-08-01 | 跨会话搜索与提及功能 | 中——新功能，需充分测试 |
| [#5212](https://github.com/HKUDS/nanobot/pull/5212) | 🟡 — | 2026-08-02 | MiniMax 音乐生成支持 | 中——provider 扩展 |
| [#5213](https://github.com/HKUDS/nanobot/pull/5213) | 🟡 — | 2026-08-02 | pip 不可用时 fallback uv | 低——兼容性修复 |
| [#5152](https://github.com/HKUDS/nanobot/pull/5152) | 🟡 — | 2026-07-28 | 子代理部分完成结果标记 | 中——影响子代理场景下的模型行为 |

**建议**：优先处理 P1 级 PR #5214 和 #5215，两个问题均涉及核心运行时的稳定性，合并后可显著降低生产环境故障率。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报 — 2026-08-03

## 1. 今日速览

Hermes Agent 今日保持高活跃度，过去24小时内共处理 **50 条 Issue**（48 条新开/活跃、2 条关闭）和 **50 条 PR**（37 条待合并、13 条已合并/关闭）。项目无明显版本发布，但社区贡献集中爆发于 Desktop 端稳定性修复与 Windows 平台兼容性治理。多个 P0/P1 级 Bug 同日涌现（WhatsApp 断连、Desktop 更新死循环、模型切换历史版本崩溃），反映出 Desktop 客户端与 Gateway 生命周期管理的系统性风险正在被快速暴露和修复。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

今日已合并/关闭的 PR 主要集中在以下方向：

- **#75263** [CLOSED] `fix(secrets): hydrate cold multiplex sources locally` — 修复了 multiplex profile 冷启动时外部密钥源未本地注入的问题，关闭了 #74317，提升了多 Profile 认证场景下的安全性边界。
- **#77237** [CLOSED] `fix(cli): persist YOLO mode across --resume` — YOLO 模式跃迁现在可跨会话恢复，解决了 `--resume` 后危险命令重新触发确认的回归。
- **#77289** [CLOSED] `fix(kanban): make boardd runtime restart-safe` — 将 `boardd` 打包为不可变运行时，通过 systemd 单位运行，增强看板调度器的崩溃恢复能力。

整体判断：今日合并工作以"止血修复"为主，集中在 secrets 注入、会话状态持久化和基础设施重启安全性，为后续功能迭代清除了技术债。

---

## 4. 社区热点

| Issue/PR | 评论数 | 热度原因 |
|---|---|---|
| [#71837](https://github.com/NousResearch/hermes-agent/issues/71837) | 6 | Windows Desktop sidebar 分支 lane 重复，影响用户项目导航体验 |
| [#69163](https://github.com/NousResearch/hermes-agent/issues/69163) | 6 | Coder profile 迁移后 gateway 无法注册，涉及跨平台 profile 序列化问题 |
| [#73985](https://github.com/NousResearch/hermes-agent/issues/73985) | 4 | xAI TTS streaming 完全失效，4 个独立 bug 叠加，社区技术讨论深入 |
| [#73804](https://github.com/NousResearch/hermes-agent/issues/73804) | 4 | Cron 调度器 workdir  jobs 单线程序列化导致静默饥饿 |
| [#29530](https://github.com/NousResearch/hermes-agent/issues/29530) | 4 | Profiled workers OAuth auth home 分裂问题，长期未决的架构级讨论 |

**热点分析：** Windows 平台兼容性与 Desktop 会话管理是社区当前最集中的痛点。#71837 和 #69163 均涉及状态同步与生命周期管理，反映出 Desktop 端与 CLI/Gateway 之间的状态一致性尚未完全稳固。#73985 的多重协议失败揭示了 streaming TTS 模块在接入新 provider 时缺乏端到端验证。

---

## 5. Bug 与稳定性

### P0 — 紧急
| Issue | 描述 | 关联 PR |
|---|---|---|
| [#77217](https://github.com/NousResearch/hermes-agent/issues/77217) | DeepSeek caching 启用后 OpenCode Zen 返回 HTTP 400（content block 格式不兼容） | — |
| [#76870](https://github.com/NousResearch/hermes-agent/issues/76870) | 会话中途切换模型触发 `history_version` 守卫，导致后续所有 agent 输出被丢弃 | — |

### P1 — 高优先级
| Issue | 描述 | 关联 PR |
|---|---|---|
| [#77268](https://github.com/NousResearch/hermes-agent/issues/77268) | WhatsApp bridge 在 server-side 断连后永久卡死（reconnect 时 `fetchLatestBaileysVersion()` 无超时） | [#77298](https://github.com/NousResearch/hermes-agent/pulls/77298) 已提交修复 |
| [#77276](https://github.com/NousResearch/hermes-agent/issues/77276) | Desktop 重启后遗留孤立 gateway 进程（app-managed spawn 路径未被 #75936 覆盖） | [#77297](https://github.com/NousResearch/hermes-agent/pulls/77297) 已提交修复 |
| [#77277](https://github.com/NousResearch/hermes-agent/issues/77277) | Windows Desktop 内置更新无限循环（updater 误报自身后端为 venv 阻塞） | — |
| [#75756](https://github.com/NousResearch/hermes-agent/issues/75756) | Desktop 编辑历史消息失败："Edit failed" + session not found（rewind 缺少 resume+retry） | — |

### P2 — 中优先级
| Issue | 描述 |
|---|---|
| [#77241](https://github.com/NousResearch/hermes-agent/issues/77241) | Desktop 开启 Message Reactions 后 agent 不响应（config.set 4002 unknown key） |
| [#74285](https://github.com/NousResearch/hermes-agent/issues/74285) | Multiplexed gateway 将用户 DM 错误路由到兄弟 profile 的 session |
| [#74554](https://github.com/NousResearch/hermes-agent/issues/74554) | `linux/arm64` Docker 镜像包含 x86_64 wheels，所有命令 ImportError 崩溃 |
| [#72636](https://github.com/NousResearch/hermes-agent/issues/72636) | auxiliary compression 401 错误被错误归因到主模型 provider |

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 需求摘要 | 纳入可能性 |
|---|---|---|---|
| [#77291](https://github.com/NousResearch/hermes-agent/issues/77291) | perf | 单轮延迟审计（5–13s），建议优化 reasoning effort 与串行 round-trip | 高 — 性能优化一直是核心方向 |
| [#77221](https://github.com/NousResearch/hermes-agent/issues/77221) | feature | Desktop 缺少本地 token/cost 分析面板（core 已有完整计量数据） | 高 — 用户付费透明度需求强烈 |
| [#77222](https://github.com/NousResearch/hermes-agent/issues/77222) | feature | InsightsEngine 增加按日 token/cost 时间序列聚合 | 中 — 与 #77221 配套 |
| [#77223](https://github.com/NousResearch/hermes-agent/issues/77223) | feature | 区分 included/estimated/unknown 成本桶 | 中 — 与 #77221 配套 |
| [#73778](https://github.com/NousResearch/hermes-agent/issues/73778) | feature | Desktop 支持拖拽 session 跨 Project 迁移 | 中 — 提升多项目管理体验 |
| [#77290](https://github.com/NousResearch/hermes-agent/pulls/77290) | feature | `voice.concise_responses` 可配置化 | 高 — PR 已提交，默认行为不变 |
| [#77288](https://github.com/NousResearch/hermes-agent/pulls/77288) | feature | CLI 新增 `--reasoning` 标志（per-invocation reasoning level） | 高 — PR 已提交 |
| [#77293](https://github.com/NousResearch/hermes-agent/pulls/77293) | feature | `hermes desktop install` 子命令 + 自动创建桌面快捷方式 | 高 — PR 已提交，提升 Desktop 分发体验 |
| [#77295](https://github.com/NousResearch/hermes-agent/pulls/77295) | feature | Skill learning loop：lessons overlay + fact_store 注入 | 中 — 技能持续学习机制，影响面较广 |

---

## 7. 用户反馈摘要

**核心痛点：**
1. **Desktop 稳定性不足**：Windows 更新死循环（#77277）、gateway 孤儿进程（#77276）、代码块渲染异常（#77253）连续出现，用户反映 Desktop 端体验远落后于 CLI 成熟度。
2. **Platform 兼容性问题突出**：`linux/arm64` Docker 镜像打包错误（#74554）、Windows 端 lane 重复（#71837）、locale 注入错误（#69474）表明跨平台测试覆盖存在盲区。
3. **成本透明度缺失**：多个 Issue（#77221/#77222/#77223）集中反映用户无法在 Desktop 端查看 token/cost 消耗，而 core 已具备完整计量能力，形成功能断层。
4. **Streaming TTS 可用性归零**：#73985 指出 xAI TTS 在任何代码路径下均无法产出音频，4 个独立缺陷叠加，用户反馈"完全不可用"。

**正面反馈：**
- `--reasoning` 标志（#77288）和 concise response 配置（#77290）获得积极回应，用户认可细粒度控制的价值。
- YOLO mode 跨会话持久化（#77237）解决了 power user 的痛点。

---

## 8. 待处理积压

| Issue | 优先级 | 创建时间 | 积压原因 |
|---|---|---|---|
| [#29530](https://github.com/NousResearch/hermes-agent/issues/29530) | P2 | 2026-05-20 | Profiled workers auth home 分裂问题，需架构决策（`needs-decision` 标签），长期挂起 |
| [#62985](https://github.com/NousResearch/hermes-agent/issues/62985) | P2 | 2026-07-12 | Kanban auto-decompose 绕过非 spawnable assignee 限制，安全边界问题 |
| [#47415](https://github.com/NousResearch/hermes-agent/issues/47415) | P2 | 2026-06-16 | Telegram 群聊未 @mention 图片被丢弃，影响多模态体验 |
| [#39771](https://github.com/NousResearch/hermes-agent/issues/39771) | P3 | 2026-06-05 | `hermes version` 在最新 tag 下仍报 860 commits behind，误导性提示 |
| [#73804](https://github.com/NousResearch/hermes-agent/issues/73804) | P2 | 2026-07-29 | Cron workdir 串行化导致静默饥饿，`needs-decision` 标签 |

**建议维护者关注：** #29530 和 #73804 均带有 `needs-decision` 标签且已积压数月，需要架构层面澄清设计方向；#74554（arm64 Docker 镜像错误）属于发布管道质量问题，应优先排查 CI 构建配置。

---

**项目健康度评估：** 今日 Issue 涌入量较大（50 条新开），但多数为 Desktop 端稳定性问题的集中爆发，已有对应 PR 快速响应（#77297、#77298）。社区贡献活跃，PR 提交节奏密集，整体处于"快速发现-快速修复"的良性循环。建议下一步重点关注 arm64 构建管道修复和 Windows Desktop 更新机制的彻底重构。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期：2026-08-03 | 数据来源：github.com/sipeed/picoclaw**

---

## 1. 今日速览

今日 PicoClaw 项目保持中高强度活跃，过去 24 小时共产生 12 条活动（3 Issues + 9 PRs），PR 吞吐显著高于 Issue 新增量，说明维护者正在积极处理积压。一个较新的安全相关 PR（#3297）和两个 Bug 修复 PR（#3314、#3312）是今日主要焦点，项目整体健康度良好，但多个 stale 标签的 Issue/PR 需关注长期未响应风险。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 作者 | 说明 |
|----|------|------|------|
| [#3313](https://github.com/sipeed/picoclaw/issues/3313) | Bug Fix | j-v | 修复 `customAllowPatterns` 未生效问题——默认拒绝模式优先级错误覆盖了用户自定义白名单 |
| [#3310](https://github.com/sipeed/picoclaw/issues/3310) | 自动 PR | j-v | picoclanker 自动生成的 PR |
| [#3261](https://github.com/sipeed/picoclaw/issues/3261) | i18n | PeterDaveHello | 新增繁体中文（zh-TW）本地化支持，涵盖 WebUI 与文档 |

**项目推进评估：** 安全加固与执行边界问题（#3297）仍处于开放状态，待合并；zh-TW 本地化已合入主线，国际化覆盖进一步完善。

---

## 4. 社区热点

### 高关注度 Issues

- **[Issue #3311](https://github.com/sipeed/picoclaw/issues/3311)** — "Repeated identical tool failure loops silently to max_tool_iterations"
  - **热度：⭐ 高**（今日新报，直接关联用户体验）
  - 生产环境反馈：Telegram 场景下，工具以相同错误反复失败时，用户完全收不到回复，静默等待直到达到 `max_tool_iterations` 上限。
  - **诉求分析：** 用户期望失败的 tool 调用能被快速识别并提前终止，避免无意义的轮次消耗。

- **[Issue #3294](https://github.com/sipeed/picoclaw/issues/3294)** — "`/list models` 仅显示当前模型"
  - **热度：⭐ 中**（stale，但功能预期明确）
  - 配置了 `model_list` 多模型后，`/list models` 命令未如预期展示全部模型，仅显示当前激活的模型。

- **[Issue #3298](https://github.com/sipeed/picoclaw/issues/3298)** — "Add AI Router as OpenAI-compatible provider preset"
  - **热度：⭐ 中**（stale，有维护者贡献意向）
  - AI Router 维护者希望以内置 preset 形式提供原生支持，而非仅通过通用 `openai` provider 配置 `api_base`。

### 高关注度 PR

- **[PR #3312](https://github.com/sipeed/picoclaw/pull/3312)** — 针对 Issue #3311 的修复，提出在工具连续相同失败时提前终止回合，与 Issue 作者相同，预计合并概率较高。
- **[PR #3297](https://github.com/sipeed/picoclaw/pull/3297)** — 安全加固：收紧远程 prompt 和执行边界，默认禁用远程执行并增加逐次审批，属于潜在破坏性变更（迁移至 schema v4）。

---

## 5. Bug 与稳定性

| 优先级 | Issue / PR | 描述 | Fix 状态 |
|--------|-----------|------|----------|
| 🔴 高 | [#3311](https://github.com/sipeed/picoclaw/issues/3311) + [#3312](https://github.com/sipeed/picoclaw/pull/3312) | 工具连续相同错误导致循环静默挂起，用户无响应 | 已有修复 PR，待合并 |
| 🟠 中 | [#3294](https://github.com/sipeed/picoclaw/issues/3294) | `/list models` 命令行为与预期不符 | 暂无 Fix PR |
| 🟡 低 | [#3313](https://github.com/sipeed/picoclaw/issues/3313) / [#3314](https://github.com/sipeed/picoclaw/issues/3314) | `customAllowPatterns` 权限覆盖 Bug（重复 PR） | #3313 已关闭，#3314 待合并（可能为重新提交） |
| 🟡 低 | [#3295](https://github.com/sipeed/picoclaw/issues/3295) | `SplitMessage` 在 fence header 超长时挂起 | 已有修复 PR，待合并 |

---

## 6. 功能请求与路线图信号

| 请求 | Issue/PR | 纳入下一版本可能性 |
|------|---------|------------------|
| AI Router 内置 Provider Preset | [#3298](https://github.com/sipeed/picoclaw/issues/3298) | 🟢 中——有明确贡献者意向，但 Issue 已 stale |
| Exa 原生 Web Search Provider | [#3299](https://github.com/sipeed/picoclaw/issues/3299) | 🟢 中——PR 已提交，功能完整（含 `d/w/m/y` 时间过滤），待评审 |
| 繁体中文本地化 | [#3261](https://github.com/sipeed/picoclaw/issues/3261) | ✅ 已合入 |
| Czech 标签补全 | [#3296](https://github.com/sipeed/picoclaw/issues/3296) | 🟡 低——纯 i18n 补全，优先级取决于维护者排期 |

**路线图信号：** 项目近期在**安全性加固**（#3297）和**用户体验修复**（#3312、#3295）方向投入较多，同时持续扩展**国际化**和**第三方 Provider 集成**。

---

## 7. 用户反馈摘要

- **痛点 1：工具失败静默挂起**（[#3311](https://github.com/sipeed/picoclaw/issues/3311)）  
  生产环境 Telegram 用户反馈，当工具因权限/凭证问题持续失败时，整个回合静默执行至 `max_tool_iterations` 上限，用户全程无响应。这是今日最高优先级体验问题。

- **痛点 2：多模型列表命令行为不符预期**（[#3294](https://github.com/sipeed/picoclaw/issues/3294)）  
  用户配置了多个模型后，`/list models` 未列出全部，仅显示当前激活模型，造成认知偏差。

- **痛点 3：白名单配置失效**（[#3313](https://github.com/sipeed/picoclaw/issues/3313)）  
  `customAllowPatterns` 添加的命令（如 `git push`）因默认拒绝模式优先级过高而被拦截，已修复。

- **正向反馈：** zh-TW 本地化合入，繁体中文用户可获得完整 WebUI 和文档体验。

---

## 8. 待处理积压

以下 Issue/PR 带有 `stale` 标签，长期未获维护者响应，建议优先处理：

| 类型 | 编号 | 标题 | 最后更新 | 建议 |
|------|------|------|---------|------|
| Issue | [#3298](https://github.com/sipeed/picoclaw/issues/3298) | AI Router Provider Preset | 2026-08-02 | 评估是否合入路线图 |
| Issue | [#3294](https://github.com/sipeed/picoclaw/issues/3294) | `/list models` 行为 Bug | 2026-08-02 | 确认是否优先修复 |
| PR | [#3297](https://github.com/sipeed/picoclaw/issues/3297) | 安全加固（schema v4 迁移） | 2026-08-02 | 关键安全 PR，建议加速评审 |
| PR | [#3296](https://github.com/sipeed/picoclaw/issues/3296) | Czech i18n 补全 | 2026-08-02 | 低优先级，可批量处理 |
| PR | [#3295](https://github.com/sipeed/picoclaw/issues/3295) | SplitMessage 挂起修复 | 2026-07-26 | 已有修复，等待合并 |
| PR | [#3299](https://github.com/sipeed/picoclaw/issues/3299) | Exa Web Search Provider | 2026-08-02 | 新功能，待评审 |
| PR | [#3314](https://github.com/sipeed/picoclaw/issues/3314) | customAllowPatterns 修复（重复） | 2026-08-03 | 与 #3313 关系需确认 |

---

**项目健康度评分：🟢 良好**  
- PR 吞吐正常（9 条/24h），维护者活跃
- Bug 响应及时（#3311 同日内出现 Fix PR）
- 国际化持续扩展
- 待关注：stale 标签积压较多，安全 PR #3297 需加速评审

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期**：2026-08-03  
**项目**：NanoClaw (`github.com/qwibitai/nanoclaw`)  
**统计周期**：过去 24 小时

---

### 1. 今日速览
过去 24 小时 NanoClaw 保持高频但有序的开发节奏，新增 1 个 Issue 与 10 个 PR（7 个待合并，3 个已关闭/合并），无新版本发布。开发重心明确落在容器化部署稳定性、通信渠道扩展（Dial/Telegram/Signal）及核心基础设施（MCP/模板）优化三条主线上。维护者与贡献者协作顺畅，代码规范执行度较高，项目整体健康度良好。

### 2. 版本发布
今日无新版本发布。

### 3. 项目进展
本期合并/关闭的 PR 主要推进了底层可靠性与技能化架构落地：
- [#3176](https://github.com/qwibitai/nanoclaw/pull/3176) `fix(release): retry post-publish readback`：增强发布流程容错，降低偶发性部署失败风险。
- [#2626](https://github.com/qwibitai/nanoclaw/pull/2626) `fix(signal): replace silent restartService failure with explicit error`：修复 macOS `launchctl` 服务重启时的静默失效，提升 Signal 渠道的可观测性。
- [#301](https://github.com/qwibitai/nanoclaw/pull/301) `feat(skill): enhance add-telegram skill`：完成 Telegram 技能重构，新增 Markdown 渲染、≤10MB 文件下载及 Linux/Docker 部署指引，补全该渠道长期缺失的能力。
项目整体在“多渠道覆盖”与“部署体验”方向持续向前推进。

### 4. 社区热点
- **[Issue #3177](https://github.com/qwibitai/nanoclaw/issues/3177)**：聚焦 Docker 跨挂载文件系统（VirtioFS）下的 SQLite 锁竞争。摘要指出该问题已累积 29,000+ 只读错误及间歇性投递失败，是近期容器化用户的核心痛点，预计将引发同类环境用户的广泛跟进。
- **[PR #3041](https://github.com/qwibitai/nanoclaw/pull/3041) & [PR #3050](https://github.com/qwibitai/nanoclaw/pull/3050)**：由 `OmriBenShoham` 提交的 Dial 渠道双 PR，分别实现 SMS + AI 语音通话适配器与频道选择器/技能向导集成。两者联动表明项目正系统性拓展传统电信协议支持。
- **[PR #3092](https://github.com/qwibitai/nanoclaw/pull/3092)**：支持远程 Streamable HTTP MCP 服务器，契合当前 AI Agent 生态对标准化工具发现协议的需求，具备较高的技术价值与讨论热度。

### 5. Bug 与稳定性
| 严重程度 | 项目 | 描述 | 状态 |
|:---:|:---|:---|:---|
| 🔴 高 | [#3177](https://github.com/qwibitai/nanoclaw/issues/3177) | Docker VirtioFS 挂载下 SQLite journal mode 未正确传播，导致会话数据库严重锁竞争与写入失败 | 待修复 |
| 🟡 中 | [#3175](https://github.com/qwibitai/nanoclaw/pull/3175) | `writeOutboundDirect()` 绕过单一写入器规则直接写入 `outbound.db`，存在数据库损坏风险 | 待合并（已有 fix PR） |
| 🟢 已修复 | [#2626](https://github.com/qwibitai/nanoclaw/pull/2626) | Signal `restartService` 静默失败伪装成正常重启 | 已合并 |
| 🟢 已修复 | [#3176](https://github.com/qwibitai/nanoclaw/pull/3176) | 发布后回读验证缺失重试机制 | 已合并 |

### 6. 功能请求与路线图信号
- **Dial 渠道集成**（[#3041](https://github.com/qwibitai/nanoclaw/pull/3041), [#3050](https://github.com/qwibitai/nanoclaw/pull/3050)）：明确指向 SMS 与 AI 语音通话支持，预计将作为独立 Skill 在近期版本中提供完整配置流。
- **远程 MCP 服务器支持**（[#3092](https://github.com/qwibitai/n

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 | 2026-08-03

## 1. 今日速览
IronClaw 今日保持高频迭代节奏：24小时内共产生 8 条 Issue 与 31 条 PR，其中 9 项已关闭或合并，22 项处于待合并队列。核心维护者集中推进了 CI 门禁加固、Wave 2 架构文档收敛、交付状态机竞态修复及网络层安全硬化。今日无新版本发布，项目整体处于“架构定型+可靠性加固”的成熟期，健康度良好。

## 2. 版本发布
今日无 Releases 发布。历史发布周期涉及的 `ironclaw_common`、`ironclaw_safety`、`ironclaw_skills` 版本升级仍由 [#5598](https://github.com/nearai/ironclaw/pull/5598) 暂代跟进，待合并后正式落地。

## 3. 项目进展
- **CI/CD 与架构治理**：[#7018](https://github.com/nearai/ironclaw/pull/7018) 成功合并 Wave 2 端口反转栈（WS2.2/WS2.4/WS5），消除多步合并带来的 rebase 成本；[#7013](https://github.com/nearai/ironclaw/pull/7013) 恢复 90% 变更行覆盖率门禁；[#6952](https://github.com/nearai/ironclaw/pull/6952) 实现按影响域动态规划 PR 测试范围，显著提升 CI 效率。
- **架构文档落定**：[#7033](https://github.com/nearai/ironclaw/pull/7033) 与 [#7032](https://github.com/nearai/ironclaw/pull/7032) 正在梳理并闭合并 Wave 2 的 8 项架构决策，对齐 `docs/reborn/target-architecture/` 与当前 `main` 分支。
- **核心功能修复**：[#7026](https://github.com/nearai/ironclaw/pull/7026) 修复旧版 checkpoint 导致的 `ironclaw serve` 启动崩溃；[#7024](https://github.com/nearai/ironclaw/pull/7024) 改进自定义 MCP 的 OAuth 自动发现逻辑；[#6917](https://github.com/nearai/ironclaw/pull/6917) 与 [#6906](https://github.com/nearai/ironclaw/pull/6906) 优化 WebUI 工作区链接预览与项目数据渲染。

## 4. 社区热点
- **[#7036](https://github.com/nearai/ironclaw/issues/7036) & [#7035](https://github.com/nearai/ironclaw/issues/7035)**：分别指出 `changed-coverage` 门禁在非普通 PR 上未触发、以及模型每日预算上限自 [#6174](https://github.com/nearai

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 📅 LobsterAI 项目动态日报（2026-08-03）

## 1. 今日速览
过去24小时 LobsterAI 保持中等活跃度，共更新 3 条 Issue（活跃1、关闭2）与 6 条 PR（待合并4、已合并/关闭2），无新版本发布。今日工作重心明显偏向**底层稳定性修复**与**前端性能调优**：依赖包自动升级完成，IM 配置刷新逻辑、定时任务排序体验、会话列表渲染性能等问题集中推进。项目整体健康度良好，技术债清理与体验打磨并行，尚未进入大规模功能迭代期。

## 2. 版本发布
过去24小时无新版本发布。现有维护主要围绕依赖升级与内部优化，建议关注下一个 Release 中对本次合并项的集成说明。

## 3. 项目进展
**已合并/关闭（2 条）**
- `PR #1285` & `PR #1286`：Dependabot 自动升级构建工具链与样式框架，`concurrently 8.2.2→9.2.1` 与 `tailwindcss 3.4.19→4.2.2`，提升开发环境稳定性和现代 CSS 支持能力。
- `Issue #1287`：IM 机器人连通性测试校验逻辑缺陷已修复/关闭，安全与配置验证边界得到收敛。
- `Issue #1289`：长代码块折叠需求已处理，UI 渲染策略预期纳入后续版本或已通过独立改动闭环。

**持续推进（4 条待合并）**
- `PR #1215`：修复 IM 配置更新时因 payload 缺少 `settings` 字段导致 `chatHandler` 未刷新的缺陷，保障多平台（钉钉/Telegram 等）凭证生效。
- `PR #1218`：重构定时任务列表排序规则，解除对随机 UUID 的依赖，提升任务管理可预期性。
- `PR #1219` & `PR #1220`：针对 Cowork 模块进行性能攻坚，消除会话列表/详情页无效重渲染及 `recentChats` 查询的 N+1 问题，预期显著改善流式输出时的页面卡顿。

## 4. 社区热点
- **[Issue #1217] 网关偶发重启影响正常使用** [链接](https://github.com/netease-youdao/LobsterAI/issues/1217)｜评论 1｜👍 0
  用户反馈 Windows 环境下网关在运行中偶发重启（日均 3-5 次），严重打断工作流。该 Issue 聚焦生产稳定性，虽评论数不高但实际影响面广，是当前社区最关切的质量问题。
- **[Issue #1287] IM 连通性测试校验不严** [链接](https://github.com/netease-youdao/LobsterAI/issues/1287)｜评论 2｜👍 0
  测试接口允许全填 `1` 仍返回连接成功，暴露出配置校验逻辑缺失。社区对 IM 集成的安全性与准确性敏感，该问题关闭后预期将减少误配风险。
- **[Issue #1289] 长代码块可读性优化** [链接](https://github.com/netease-youdao/LobsterAI/issues/1289)｜评论 2｜👍 0
  反映 AI 输出超长代码时会话视图被撑爆的普遍痛点，折叠/展开交互已成为此类工具的标配诉求。

## 5. Bug 与稳定性
| 优先级 | Issue/PR | 描述 | Fix 状态 |
|:---:|:---|:---|:---|
| 🔴 高 | [Issue #1217](https://github.com/netease-youdao/LobsterAI/issues/1217) | Windows 环境下网关偶发重启，干扰正常使用 | 暂无关联 Fix PR，需维护者介入排查根因 |
| 🟡 中 | [Issue #1287](https://github.com/netease-youdao/LobsterAI/issues/1287) | IM 机器人连通性测试未校验凭证合法性 | ✅ 已关闭 |
| 🟢 低 | [Issue #1289](https://github.com/netease-youdao/LobsterAI/issues/1289) | 长代码块全量展示导致页面冗长 | ✅ 已关闭（预期纳入 UI 迭代）|

## 6. 功能请求与路线图信号
- **配置实时生效**：`PR #1215` 表明团队正响应多平台 IM 凭证变更的即时刷新需求，路线图中将强化配置热更新能力。
- **任务管理体验**：`PR #1218` 针对定时任务排序的 UX 缺陷进行重构，预示下一版本将优化后台任务面板的可视性与可操作性。
- **渲染性能专项**：`PR #1219` / `PR #1220` 集中解决 React 状态更新与 Redux 查询的冗余开销，项目已进入“流畅度深耕”阶段，后续版本可期待 Cowork 模块的响应性能显著提升。
- **代码输出优化**：`Issue #1289` 的关闭标志着长文本/代码渲染策略已纳入迭代 backlog，未来会话组件预计默认支持智能折叠。

## 7. 用户反馈摘要
- **痛点集中区**：网关运行稳定性（#1217）、IM 配置校验严谨性（#1287）、超长内容渲染体验（#1289）。
- **使用场景**：开发者依赖 LobsterAI 进行多平台 IM 机器人集成与自动化定时任务调度，对配置生效的即时性与会话交互的流畅度要求较高。
- **满意点**：Dependabot 自动化依赖升级（#1285/#1286）减轻维护负担；社区针对性能与排序的体验反馈能得到快速响应与结构化重构。
- **不满/风险**：部分关键 Issue（如网关重启）长期处于 `stale` 状态但缺乏修复进展，可能影响生产环境用户信任。

## 8. 待处理积压
| 类型 | 编号 | 说明 | 建议 |
|:---|:---|:---|:---|
| 🐛 Bug | [Issue #1217](https://github.com/netease-youdao/LobsterAI/issues/1217) | 网关偶发重启，影响核心稳定性 | 建议提升至 P0/P1，安排日志与内存/进程守护层面排查 |
| 🔄 PR | [PR #1215](https://github.com/netease-youdao/LobsterAI/pull/1215) | IM 配置刷新修复 | 等待 Maintainer Review，已标注 `stale` |
| 🔄 PR | [PR #1218](https://github.com/netease-youdao/LobsterAI/pull/1218) | 定时任务排序重构 | 等待合并，影响日常任务管理体验 |
| 🔄 PR | [PR #1219](https://github.com/netease-youdao/LobsterAI/pull/1219) / [PR #1220](https://github.com/netease-youdao/LobsterAI/pull/1220) | Cowork 性能优化 | 双 PR 互为补充，建议同步 Review 推进 |

> **分析师建议**：项目当前处于“体验打磨+性能攻坚”的平稳期，技术方向清晰。建议维护者优先响应 [#1217](https://github.com/netease-youdao/LobsterAI/issues/1217) 的网关稳定性问题，并加快 4 条 `stale` PR 的 Review 节奏，以维持社区贡献活跃度。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-08-03

## 1. 今日速览

今日 Moltis 项目整体活跃度**较低**。过去24小时内仅收到 1 条 PR 更新，无 Issue 变动，无新版本发布。唯一活跃项为 PR #1183，正在推进 MCP Server 仓库 bundles 的功能开发。项目处于稳定的迭代开发期，无紧急问题或紧急合并需求，维护节奏平稳。

## 2. 版本发布

今日无新版本发布。

## 3. 项目进展

| PR | 状态 | 说明 |
|----|------|------|
| [#1183](https://github.com/moltis-org/moltis/pull/1183) | 🔵 待合并 | 新增 `managed repository bundles` 功能，用于 MCP Server 的发现、预览、安装、更新和移除全流程管理 |

**功能亮点：**
- 支持通过 Git 仓库（HTTPS/SSH）发现和引入 MCP 服务器配置
- 集成 Vault 生命周期管理，实现配置的版本化存储
- 补充 CLI/RPC/Web UI 三层工作流，覆盖多端使用场景
- 包含配套的数据库迁移逻辑

该项目正在从"单点 MCP Server 管理"向"基于仓库的批量/模板化管理"方向演进，是对平台 MCP 生态管理能力的重要增强。

## 4. 社区热点

今日无活跃 Issue 或已合并 PR。唯一关注的讨论项为：

- **[PR #1183](https://github.com/moltis-org/moltis/pull/1183)** — 新增 MCP 仓库 bundles 管理功能
  - 当前评论数：0 | 👍：0
  - **诉求分析：** 用户（penso）持续贡献 MCP 相关能力，反映出社区对"可版本化、可模板化、可批量部署"的 MCP Server 管理需求的强烈期待。该 PR 填补了当前平台在远程仓库驱动的 MCP 配置管理方面的空白，属于高价值功能扩展。

## 5. Bug 与稳定性

今日无 Bug 报告，无崩溃或回归问题反馈。项目整体稳定性良好，无紧急修复需求。

## 6. 功能请求与路线图信号

**潜在路线图信号：**

- **MCP 仓库 bundles 管理**（PR #1183）是当前最明确的功能方向信号。结合摘要中提到的"discovering, previewing, installing, updating, and removing"完整生命周期，可以判断项目正在将 MCP Server 的**仓库级编排能力**纳入正式路线图，预期将成为下一版本的核心特性之一。
- 建议关注该 PR 合并后的影响，以及是否配套推出 CLI 命令（如 `moltis mcp bundle add/remove`）和 Web UI 入口。

## 7. 用户反馈摘要

今日无新 Issue 评论，暂无新增用户痛点或满意度反馈。

## 8. 待处理积压

| 类型 | 编号 | 标题 | 状态 | 提醒 |
|------|------|------|------|------|
| PR | [#1183](https://github.com/moltis-org/moltis/pull/1183) | feat(mcp): add managed repository bundles | 🔵 待合并 | 创建已超1天，建议维护者尽快进行代码审查，推动合并 |

---

**📊 今日健康度评估：🟢 良好**
- 活跃度：低（1 PR，0 Issue）
- 稳定性：无已知问题
- 进展：1 个功能 PR 在途，方向明确
- 风险：无

> *数据来源：[github.com/moltis-org/moltis](https://github.com/moltis-org/moltis)*
> *报告生成时间：2026-08-03*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 | 2026-08-03

## 1. 今日速览
过去24小时 CoPaw 保持高活跃开发节奏，共处理 Issues 13 条（新/活跃 10，关闭 3）、PR 28 条（待合并 17，已合并/关闭 11）。项目整体处于 **2.0.1 版本的稳定性加固与兼容性收尾期**，维护者对关键 UI 冻结、构建产物异常及上游 `agentscope` 依赖变更的响应迅速，已有多个阻塞性 Bug 获得 Fix PR 或已合并。社区贡献者活跃度显著提升，首次贡献者占比约 40%。项目健康度良好，但上游依赖同步与长会话性能优化仍是当前核心攻坚点。

## 2. 版本发布
暂无新版本发布。当前主线版本仍为 `2.0.1`，预计待今日合并的稳定性修复 PR 完成评审后将发行 `2.0.1.patch` 系列。

## 3. 项目进展
今日合并/关闭的 PR 主要聚焦于控制台鲁棒性、多端渲染一致性与子智能体调度逻辑：
- **`#6637`** [CLOSED] 修复控制台大模型输出导致的 UI 冻结，引入 100KB/1000 行阈值跳过语法高亮，仅展示首尾片段并限制单段 32KB，直接解决 `#6589`。
- **`#6639`** [CLOSED] 移除生产/Dev/Tauri 构建中无条件注册的 `css-stub` 插件，恢复 `monaco-editor` 完整样式，消除浮动白块渲染异常。
- **`#6609`** [CLOSED] 修正 `spawn_subagent` 参数 Schema 类型注解顺序，使 `batch`/`allowed_tools`/`skills` 正确识别为可选，修复 `#6588`。
- **`#6543`** [CLOSED] 优化 OneBot/QQ 渠道出站文本与媒体投递逻辑，清理 Markdown 链接格式并适配 NapCat 等运行环境。
- **`#6640`** [CLOSED] 合并 Creator 模块的拒绝反馈循环、叠加层管理与结构化日志能力。
- **`#6521`** [CLOSED] 在斜杠菜单中补齐 OMP 循环模式展示，支持 i18n 与内联 Markdown 提示。

**整体推进评估**：项目已从功能扩张转向底层体验打磨，控制台渲染性能、跨平台构建一致性及子智能体协议兼容性得到实质性强化，为下一轮版本迭代奠定了稳定基座。

## 4. 社区热点
- **[Issue #6537]** [CLOSED] Skill 标签重启后丢失（11 条评论）  
  链接: `agentscope-ai/QwenPaw Issue #6537`  
  **诉求分析**：用户高度关注数据持久性信任。标签通过 `PUT` API 正确写入 `skill.json`，但在 manifest 启动同步阶段被覆盖。高评论数反映该回归问题（`#3270` 重现）已影响实际工作流，社区期待维护者提供明确的持久化保障说明或缓存策略优化。
- **[Issue #6612]** [OPEN] 与 `agentscope==2.0.4.post1` 兼容性破坏（proactive 崩溃 & 权限死锁）  
  链接: `agentscope-ai/QwenPaw Issue #6612`  
  **诉求分析**：上游依赖升级导致 `Msg.content` 类型契约变更与 Agent 阻塞逻辑不匹配，直接阻断核心链路。用户明确标注根因在 agentscope API 迭代，迫切希望 CoPaw 同步适配。该 Issue 已成为当前兼容性修复的风向标。
- **[PR #6525]** [OPEN] 用户上下文透明穿透（Chat API → Agent → Tool → MCP → SKILL CLI）  
  链接: `agentscope-ai/QwenPaw PR #6525`  
  **诉求分析**：首次出现针对企业级可观测性与多租户身份传递的架构级 PR。开发者希望在不暴露 LLM 的前提下，将 `user_id`/`channel`/`tenant` 等 metadata 全链路透传，反映项目正在向生产级协作场景演进。

## 5. Bug 与稳定性
| 严重程度 | Issue / PR | 描述 | 修复状态 |
|:---:|:---|:---|:---|
| 🔴 Critical | [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) | 与 `agentscope 2.0.4.post1` 不兼容，proactive 崩溃、工具权限死锁 | 🟢 PR `#6615` 待合并 |
| 🔴 Critical | [#6619](https://github.com/agentscope-ai/QwenPaw/issues/6619) | `ToolCallBlock` 缺失 `extra_content`

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报
**日期：2026-08-03**

---

## 1. 今日速览

ZeroClaw 今日保持高活跃度，过去24小时内共产生 **50 条 Issue 更新**（37 条活跃/新开，13 条关闭）和 **50 条 PR 更新**（40 条待合并，10 条已合并/关闭）。v0.8.4 维护版本正式发布，涵盖 262 个提交、49 位贡献者，重点强化内存/SOP 控制面、沙箱与凭证边界。社区 RFC 讨论持续升温，涵盖 Chat Completions 协议适配、可插拔认证架构、Goal Mode 等核心方向。整体项目健康度良好，维护节奏稳健。

---

## 2. 版本发布

### v0.8.4 维护版本发布

| 项目 | 详情 |
|------|------|
| **版本** | v0.8.4 |
| **提交数** | 262 commits |
| **贡献者** | 49 人 |
| **目标** | 维护与加固 |

**核心更新内容：**
- 扩展内存与 SOP 控制面
- 提升 Provider 与 Channel 可靠性
- 强化沙箱与凭证边界安全
- 改进 Desktop 与 Release 流水线

**迁移注意事项：**
- Rust MSRV 升级至 1.96.1，Docker `all-features` 变体因 StageX 镜像仍使用 rustc 1.95.0 导致构建失败（Issue #9690，已有 fix PR #9676 已合并）
- WATI Channel 已被移除（PR #9571），相关部署需迁移至其他通道

🔗 Tracker Issue: [#8357](https://github.com/zeroclaw-labs/zeroclaw/issues/8357)

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 摘要 | 状态 |
|----|------|------|------|
| [#9571](https://github.com/zeroclaw-labs/zeroclaw/pull/9571) | 移除 | 移除 WATI Channel 模块、feature、路由、CI 配置 | ✅ Closed |
| [#9676](https://github.com/zeroclaw-labs/zeroclaw/pull/9676) | 修复 | 恢复 all-features Docker 发布（修复 MSRV 不匹配） | ✅ Closed |
| [#9037](https://github.com/zeroclaw-labs/zeroclaw/pull/9037) | 修复 | 清理流式响应中残留的 provider 终止标记 `<eom>` | ✅ Closed |
| [#9478](https://github.com/zeroclaw-labs/zeroclaw/pull/9478) | 修复 | precheck 拒绝消息时通知发送者，避免"假死"体验 | ✅ Closed |
| [#8838](https://github.com/zeroclaw-labs/zeroclaw/pull/8838) | 修复 | 加固 SSE 完成与空闲超时处理 | ✅ Closed |
| [#9519](https://github.com/zeroclaw-labs/zeroclaw/pull/9519) | 修复 | 序列化 Gateway 配置写入，防止并发更新丢失 | ✅ Closed |
| [#9162](https://github.com/zeroclaw-labs/zeroclaw/pull/9162) | 重构 | 提取 OAuth refresh 重试循环到 oauth_common | ✅ Closed |
| [#8847](https://github.com/zeroclaw-labs/zeroclaw/pull/8847) | 修复 | 修复 cargo test --doc 的重复 rustdoc theme flag | ✅ Closed |

**项目推进评估：** 今日 10 条 PR 已合并/关闭，覆盖安全加固、配置一致性、体验修复三个维度，项目稳步向 v0.9.0 安全架构里程碑迈进。

---

## 4. 社区热点

### 高评论数 Issue/PR 排行

| 排名 | 类型 | ID | 主题 | 评论数 | 链接 |
|------|------|----|------|--------|------|
| 1 | Issue | #6808 | RFC: Work Lanes, Board Automation, Label Cleanup | 17 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) |
| 2 | Issue | #8603 | RFC: ZeroClaw Chat Completions profile | 15 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) |
| 3 | Issue | #7141 | RFC: Pluggable inbound authentication and canonical principals | 9 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) |
| 4 | Issue | #8303 | RFC: Goal mode for bounded autonomous session work | 9 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) |
| 5 | Issue | #8692 | Tracker: Maintainer decision queue for RFCs | 8 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |

**热点分析：**
- **#6808 (17评论)**：工作流自动化与标签清理 RFC，反映社区对项目治理效率的关注，当前处于 Ratification correction 阶段
- **#8603 (15评论)**：Chat Completions 协议适配 RFC，旨在打通 Open WebUI、LobeChat、LangChain 等生态，是高优先级集成需求
- **#7141 & #8303**：分别涉及安全认证架构和 Goal Mode 自主会话，均标记为 high risk，是 v0.9.0 的核心设计议题

---

## 5. Bug 与稳定性

### 今日 Bug 报告（按严重程度排列）

| 严重度 | Issue | 描述 | Fix PR | 链接 |
|--------|-------|------|--------|------|
| **S0** | #9565 | Gateway webhook handlers 未 fail-closed，WhatsApp/Linq/WATI 未验证调用方身份 | 待确认 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) |
| **S1** | #9624 | Registry WIT pin 与 master 分叉，破坏已发布组件 | 待确认 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9624) |
| **S1** | #9672 | `cron add` CLI 帮助文档三个示例均无法运行 | 待确认 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9672) |
| **S2** | #8578 | zerocode 启动失败时不终止进程 | ✅ #8578 已关闭 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8578) |
| **S2** | #9690 | Containerfile StageX pin 使用 rustc 1.95.0，低于 MSRV | ✅ #9676 已合并 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9690) |
| **S3** | #9465 | precheck 拒绝的 Telegram 消息仅显示 reaction，无文字反馈 | ✅ #9478 已合并 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9465) |

**稳定性评估：** S0 级安全问题（#9565）需紧急关注，涉及 webhook 未经验证直接 dispatch 消息至 agent。S1 级 WIT pin 分叉问题影响插件生态兼容性。

---

## 6. 功能请求与路线图信号

### 高潜力 RFC/Feature

| Issue | 主题 | 优先级 | 与已有 PR 关联 | 纳入下版本可能性 |
|-------|------|--------|----------------|------------------|
| #8603 | Chat Completions 协议适配 | P2/High | - | ⭐⭐⭐ 高（v0.9.0 集成里程碑） |
| #7141 | 可插拔入站认证与规范主体 | P1/High | #9162 (OAuth 重构) | ⭐⭐⭐ 高（安全架构核心） |
| #8303 | Goal Mode 自主会话 | P2/High | - | ⭐⭐ 中（需进一步设计） |
| #9487 | Runtime 拥有的会话生命周期 | P2/High | - | ⭐⭐ 中（架构重构） |
| #9464 | Anthropic OAuth alias contract | P1/In-progress | #9420 | ⭐⭐⭐ 高（已有实现 PR） |
| #7232 | 结构化可观测性增强 | P2/High | #9352 (OTel 交叉轮次关联) | ⭐⭐ 高（PR #9352 待合并） |
| #9549 | 社区本地模型推荐器 | P2/Medium | - | ⭐ 低（quickstart 类型） |

**路线图信号：** v0.9.0 将聚焦安全架构（#7141, #7142）、可观测性（#7232）和协议扩展（#8603）三大方向。

---

## 7. 用户反馈摘要

### 真实痛点与使用场景

| 反馈来源 | 痛点/场景 | 用户情绪 |
|----------|-----------|----------|
| #9006 (via #9037, #9695) | AI21/Jamba 模型的 `<eom>` 终止标记泄露到对话历史和频道消息 | 😤 不满（内容污染） |
| #9465 | Telegram 消息被 precheck 拒绝后，用户仅看到 emoji reaction，误以为 agent 故障 | 😤 困惑（体验断裂） |
| #9672 | CLI `cron add` 帮助文档示例全部无法运行，用户按文档操作失败 | 😤 不满（文档失真） |
| #8950 (via #8963) | Telegram Bot Commands 超过 100 限制导致 `BOT_COMMANDS_TOO_MUCH` 错误 | 😐 中性（功能受限） |
| #8720 (via #8943) | AWS Bedrock Nova 2 模型不支持 prompt caching，触发 400 错误 | 😤 不满（Provider 兼容） |
| #8321 | 运行时响应缓存策略边界不清晰，多缓存面缺乏统一策略 | 😐 中性（架构模糊） |

**正面反馈：** Gateway 配置写入序列化修复（#9519）和 Telegram 命令截断修复（#8963）解决了实际生产问题。

---

## 8. 待处理积压

### 需维护者关注的长期未响应 Issue

| Issue | 主题 | 创建日期 | 未响应天数 | 风险 | 建议行动 |
|-------|------|----------|------------|------|----------|
| #9624 | Registry WIT pin 分叉破坏插件 | 2026-08-01 | 2 | High | 紧急评估 pin 修复方案 |
| #9565 | Gateway webhook 未 fail-closed | 2026-07-30 | 4 | **Critical** | 安全补丁需优先处理 |
| #9672 | CLI cron 文档示例全失效 | 2026-08-02 | 1 | Medium | 修复示例或标记废弃 |
| #9644 | 退役 Lucid memory connector | 2026-08-01 | 2 | Medium | 确认 v0.9.0 移除计划 |
| #9621 | Staged opt-in telemetry RFC | 2026-08-01 | 2 | Low | 需 maintainer review |
| #7822 | WASM plugin lifecycle hook | 2026-06-17 | 47 | High | 长期 RFC 需决策 |
| #8321 | Response-cache policy RFC | 2026-06-25 | 39 | Medium | 需统一缓存策略 |

**维护者提醒：** Issue #9565 为 S0 级安全问题，建议优先审查并派发 fix PR。WASM hook（#7822）和缓存策略（#8321）为长期 RFC，需在 v0.9.0 前明确方向。

---

*报告生成时间：2026-08-03 | 数据来源：ZeroClaw GitHub Repository*

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*