# OpenClaw 生态日报 2026-09-02

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-02 04:01 UTC

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



# OpenClaw 项目动态日报 — 2026-09-02

---

## 1. 今日速览

OpenClaw 在 2026-09-02 保持高活跃度，过去 24 小时内共产生 **500 条 Issue 更新** 与 **500 条 PR 更新**，其中新开/活跃 Issue 290 条、已关闭 210 条；PR 待合并 336 条、已合并/关闭 164 条。今日发布了 **v2026.8.2** 版本，主要新增 `Your Home` 侧边栏 Dock 功能与桌面伴侣相关特性。值得注意的是，**升级至 2026.8.1/8.2 引发的崩溃循环与迁移失败问题**成为社区焦点，多个 P0/P1 级 Bug 均源于此，反映出本次版本升级的破坏性较大。

---

## 2. 版本发布

### v2026.8.2

**亮点功能**
- **Your Home agent**：新增可通过 `Cmd/Ctrl+Shift+H` 在右侧或底部 Dock 打开的 Home 代理界面，允许用户保持当前页面可见的同时预览或移除工作上下文快照，或将选中文本附加到消息中（参考 #133632、#133676）
- **桌面伴侣（Desktop Companion）**：新增功能（摘要在文档中被截断）

**⚠️ 破坏性变更与迁移注意事项**
从历史 Issue 来看，**2026.7.x → 2026.8.x 的升级路径存在严重问题**，以下风险需在升级前评估：

| 问题 | 关联 Issue | 状态 |
|------|-----------|------|
| Gateway 无法启动，`doctor --fix` 跳过配置键迁移 | #133984 | OPEN |
| 打包的 Perplexity 插件需要能力同意但无法配置 | #135171 | CLOSED |
| Docker 环境 auth 迁移后凭证丢失，永久阻断修复 | #134608 | CLOSED |
| 小米插件升级后缺失安装包，Gateway 拒绝启动 | #134353 | CLOSED |
| Windows `doctor --fix` 因文件未找到而中止 | #134453 | CLOSED |
| 升级后 7 种不同状态迁移失败导致静默消息丢失 | #134570 | OPEN |
| `doctor --fix` 循环报错 `legacy workspace conflicts with SQLite state` | #134331 | CLOSED |

**建议**：在升级至 2026.8.x 前，务必备份 `~/.openclaw/` 目录，并仔细阅读升级说明。v2026.8.2 已针对部分问题进行了修复，但迁移路径仍需维护者进一步澄清。

---

## 3. 项目进展

### 今日关闭/合并的重要 PR

| PR | 作者 | 主题 | 影响 |
|----|------|------|------|
| [#134413](https://github.com/openclaw/openclaw/pull/134413) | vyctorbrzezowski | macOS 编辑器中显示 Default 权限图标 | UI 修复 |
| [#124993](https://github.com/openclaw/openclaw/pull/124993) | sunlit-deng | Fleet restore 恢复失败正确报告 | 稳定性 |
| [#120105](https://github.com/openclaw/openclaw/pull/120105) | qingminglong | 稳定 Vitest shard 时序键 | 测试基础设施 |
| [#135561](https://github.com/openclaw/openclaw/pull/135561) | fuller-stack-dev | Docker 升级流程修复 | 部署稳定性 |
| [#134307](https://github.com/openclaw/openclaw/pull/134307) | aoclaw-glitch | `auth: oauth` MCP 工具在 claude-cli 运行时缺失问题 | 认证修复 |
| [#103734](https://github.com/openclaw/openclaw/pull/103734) | Maless88 | Codex 用量限制以 `promptError` 形式返回而非抛出 | 错误处理 |
| [#134331](https://github.com/openclaw/openclaw/pull/134331) | Deregtx | `doctor --fix` 循环报错问题 | 迁移修复 |
| [#135566](https://github.com/openclaw/openclaw/pull/135566) | goslingmanagment | Utility 模型选择忽略 Claude CLI runtime | 模型路由 |

### 进行中的关键 PR

- **[PR #135800](https://github.com/openclaw/openclaw/pull/135800)** — 修复内存索引全量 reindex 活锁问题（P1，需 proof）
- **[PR #135884](https://github.com/openclaw/openclaw/pull/135884)** — 修复 Codex 音频消息仅返回文本回复的回归（今日新建）
- **[PR #135016](https://github.com/openclaw/openclaw/pull/135016)** — 修复 Gateway 重启后浏览器消息被标记为中断的问题
- **[PR #135868](https://github.com/openclaw/openclaw/pull/135868)** — 升级/启动失败后触发自动修复 triage 流程
- **[PR #132180](https://github.com/openclaw/openclaw/pull/132180)** — 减少节点完成延迟、澄清执行结果（XL 级，待 maintainer 审核）

**整体评估**：项目正在集中修复 2026.8.x 升级链路上的各类迁移和崩溃问题，同时推进内存索引、Codex 集成、UI 稳定性等核心能力的改进。代码审查与修复节奏较快，维护者响应积极。

---

## 4. 社区热点

### 评论数 Top Issues

| Issue | 评论数 | 评级 | 主题 | 链接 |
|-------|--------|------|------|------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | 59 | 🦐 gold shrimp | 实时语音会话保留未界定状态的 provider/consult 状态 | [链接](https://github.com/openclaw/openclaw/issues/116201) |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | 16 | 🦞 diamond lobster | 大型 SQLite 转录清理阻塞 Gateway 事件循环 | [链接](https://github.com/openclaw/openclaw/issues/112423) |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | 14 | 🐚 platinum hermit | WhatsApp 图片导致主消息通道阻塞约 3 分钟 | [链接](https://github.com/openclaw/openclaw/issues/96834) |
| [#69208](https://github.com/openclaw/openclaw/issues/69208) | 14 | 🦐 gold shrimp | 多渠道重复转录/重放/上下文组装问题总览 | [链接](https://github.com/openclaw/openclaw/issues/69208) |
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | 12 | 🌊 off-meta tidepool | 建议内置无头浏览器作为原生工具 | [链接](https://github.com/openclaw/openclaw/issues/53763) |
| [#114020](https://github.com/openclaw/openclaw/issues/114020) | 11 | 🦞 diamond lobster | Feishu/Telegram 通道调度失败（已关闭） | [链接](https://github.com/openclaw/openclaw/issues/114020) |
| [#133984](https://github.com/openclaw/openclaw/issues/133984) | 11 | 🦞 diamond lobster | 2026.7.1→8.1 升级后 Gateway 无法启动 | [链接](https://github.com/openclaw/openclaw/issues/133984) |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 10 | 🦪 silver shellfish | Hook/Tool 子进程泄漏导致僵尸进程累积 | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| [#127229](https://github.com/openclaw/openclaw/issues/127229) | 10 | 🦞 diamond lobster | Telegram durable update 被错误 tombstoned | [链接](https://github.com/openclaw/openclaw/issues/127229) |
| [#135171](https://github.com/openclaw/openclaw/issues/135171) | 9 | 🦞 diamond lobster | 2026.8.1/8.2 Gateway 崩溃循环：Perplexity 插件能力同意问题（已关闭） | [链接](https://github.com/openclaw/openclaw/issues/135171) |

**热点分析**：
- **升级问题占据主导**：#133984、#135171、#134608 等 Issues 均指向 2026.8.x 升级带来的严重回归，反映出维护团队在版本兼容性测试上存在不足。
- **性能与稳定性问题持续**：SQLite 阻塞（#112423）、进程泄漏（#97616）、实时语音状态管理（#116201）等长期问题仍在积累讨论。
- **功能诉求**：内置无头浏览器（#53763）和 A2A 单向分发（#44309）获得了社区关注，反映了用户对 agent 能力扩展的期待。

---

## 5. Bug 与稳定性

### 今日新增/活跃的高优先级 Bug

| 级别 | Issue | 主题 | 状态 | Fix PR |
|------|-------|------|------|--------|
| **P0** | [#135171](https://github.com/openclaw/openclaw/issues/135171) | 2026.8.1/8.2 Gateway 崩溃循环：Perplexity 插件需要能力同意但无法配置 | ✅ CLOSED | — |
| **P0** | [#107227](https://github.com/openclaw/openclaw/issues/107227) | 2026.7.1 启动迁移门为致命错误，`doctor` 无法修复 | ✅ CLOSED | — |
| **P1** | [#133984](https://github.com/openclaw/openclaw/issues/133984) | 2026.7.1-2 → 2026.8.1 升级后 Gateway 不可启动，`doctor --fix` 跳过配置迁移 | 🟡 OPEN | — |
| **P1** | [#135347](https://github.com/openclaw/openclaw/issues/135347) | 强制内存 reindex 膨胀共享 Agent DB 至 35GB，删除恢复导致会话丢失 | 🟡 OPEN | — |
| **P1** | [#134925](https://github.com/openclaw/openclaw/issues/134925) | ARM64/Raspberry Pi 上 Gateway 主线程每轮消耗 ~100% CPU | 🟡 OPEN | — |
| **P1** | [#117262](https://github.com/openclaw/openclaw/issues/117262) | SQLite 3 并发写入句柄导致 ~33s 事件循环停滞 | 🟡 OPEN | — |
| **P1** | [#134570](https://github.com/openclaw/openclaw/issues/134570) | 升级后 7 种状态迁移失败导致 Gateway 崩溃循环和静默消息丢失 | 🟡 OPEN | — |
| **P1** | [#116201](https://github.com/openclaw/openclaw/issues/116201) | 实时语音会话保留未界定 provider/consult 状态 | 🟡 OPEN | — |
| **P2** | [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/Tool 子进程泄漏导致僵尸进程累积和运行时退化 | 🟡 OPEN | — |
| **P2** | [#88087](https://github.com/openclaw/openclaw/issues/88087) | 长期后台任务 UX 差 + 静默 cron 唤醒失败导致用户弃用 | 🟡 OPEN | — |
| **P2** | [#74848](https://github.com/openclaw/openclaw/issues/74848) | macOS App 节点反复断开连接（"cancelled"），CLI 节点正常 | 🟡 OPEN | — |

### 已关闭的重要 Bug

| Issue | 主题 | 关闭原因 |
|-------|------|----------|
| [#114020](https://github.com/openclaw/openclaw/issues/114020) | Feishu/Telegram 通道调度失败：`runChannelInboundEvent` 需要 `runDispatchLifecycle` | 已修复 |
| [#134353](https://github.com/openclaw/openclaw/issues/134353) | 小米插件升级后缺失安装包，Gateway 拒绝启动 | 已修复 |
| [#134453](https://github.com/openclaw/openclaw/issues/134453) | Windows `doctor --fix` 因文件未找到而中止 | 已修复 |
| [#134608](https://github.com/openclaw/openclaw/issues/134608) | Docker auth 迁移归档 JSON 后无凭证，永久阻断修复 | 已修复 |
| [#134331](https://github.com/openclaw/openclaw/issues/134331) | `doctor --fix` 循环报错 legacy workspace conflicts | 已修复 |

**稳定性评估**：2026.8.x 系列的发布质量存在明显问题，多起 P0/P1 级崩溃和迁移失败均指向升级路径的测试覆盖不足。维护团队已在 v2026.8.2 中修复了部分问题，但仍有多个关键 Bug 待处理。

---

## 6. 功能请求与路线图信号

| Issue | 主题 | 社区反应 | 可能性评估 |
|-------|------|----------|------------|
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | 内置无头 Chromium 浏览器作为原生工具 | 12 条评论，关注可靠网页访问 | 🟢 高 — 与现有 browser 扩展形成互补 |
| [#44309](https://github.com/openclaw/openclaw/issues/44309) | A2A 单向分发模式（无回复 ping-pong） | 9 条评论，1 👍 | 🟡 中 — 需产品决策 |
| [#66252](https://github.com/openclaw/openclaw/issues/66252) | 每 Agent TTS/STT 配置覆盖（多语言支持） | 8 条评论，1 👍 | 🟡 中 — 与 #45508 相关 |
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | WebChat 使用自托管 STT/TTS 而非浏览器 Speech API | 7 条评论，2 👍 | 🟢 高 — 已有 PR 跟进 |
| [#8724](https://github.com/openclaw/openclaw/issues/8724) | 

---

## 横向生态对比



# 个人 AI 智能体开源生态横向对比分析报告
**日期：2026-09-02 | 分析师：Agnes-2.0-Flash（Sapiens AI）**

---

## 1. 生态全景

2026年9月，个人AI助手与自主智能体开源生态呈现**核心项目架构收敛、边缘项目垂直深耕**的分层态势。OpenClaw与CoPaw作为头部项目以万级Issue规模领跑，聚焦升级稳定性与调度可靠性；Hermes、IronClaw、NanoClaw等项目正处于**核心执行机制重构期**，通过大规模PR攻坚架构债务；同时，PicoClaw、Moltis等轻量级项目聚焦边缘部署与工具链诊断，补齐生态多样性。整体而言，生态正从"功能堆叠"向"稳定性与安全性治理"过渡，cron调度、MCP兼容、认证安全成为跨项目共性痛点。

---

## 2. 各项目活跃度对比

| 项目 | Issues | PRs | Release | 健康度 | 核心动态 |
|------|--------|-----|---------|--------|----------|
| **OpenClaw** | 500（新/活跃290，关闭210） | 500（待合并336，已合并164） | v2026.8.2 | 🟡 中（升级链问题突出） | Your Home Dock功能发布；2026.8.x升级崩溃循环成焦点 |
| **CoPaw (QwenPaw)** | 30（活跃17，关闭13） | 40（待合并19，已合并21） | v2.2.0-beta.6 | 🟢 良好 | 测试覆盖冲刺+617用例；cron调度可靠性与MCP安全治理受关注 |
| **Hermes Agent** | 50 | 50 | — | 🟢 良好 | Desktop分支会话修复链（7个PR）系统收敛；成本可见性功能活跃 |
| **IronClaw** | 13 | 19 | — | 🟢 良好 | Agent Loop核心解耦（executor.rs从2938行精简至890行）；Prompt缓存命中率修复 |
| **NanoBot** | 3 | 15（合并6） | — | 🟢 良好 | Agent循环架构解耦；工具调用执行边界独立化 |
| **NanoClaw** | 2 | 13（合并1） | — | 🟢 良好 | Provider合同规范化（6个连续PR）；Sweep超时与调度策略增强 |
| **PicoClaw** | 3 | 4（合并1） | — | 🟢 良好 | Telegram交互三项修复；轻量Worker模式提案引发关注 |
| **LobsterAI** | 9 stale + 3活跃 | 6（合并6） | — | 🟡 中（stale积压） | onboarding与视频分享功能迭代；启动崩溃问题待处理 |
| **Moltis** | 2 | 2（合并2） | — | 🟢 良好 | Docker认证检测修复；MCP Doctor诊断逻辑完善；推理Effort级别新增 |
| **ZeptoClaw** | 0 | 2（Dependabot） | — | 🟡 低（依赖Bot维护） | Rust镜像版本跟进，无核心功能演进 |
| **NullClaw** | 0 | 0 | — | 🔴 无活动 | — |
| **ZeroClaw** | — | — | — | ⚠️ 数据缺失 | 摘要生成失败 |

---

## 3. OpenClaw 在生态中的定位

**相对优势**：
- **社区规模绝对领先**：24小时内500条Issue/PR更新，是CoPaw的17倍、Hermes的10倍，反映其作为早期先行者的用户基数优势
- **功能完整性**：Your Home Dock、Desktop Companion、多渠道集成（WhatsApp/Feishu/Telegram等）已形成闭环，边缘项目（PicoClaw、Moltis）在其基础上做垂直延伸

**技术路线差异**：
| 维度 | OpenClaw | 竞品对比 |
|------|----------|----------|
| 架构范式 | 中心化Gateway + 多通道总线 | Hermes：分支会话路由；IronClaw：Agent Loop状态机解耦 |
| 插件生态 | 市场化工具链（Perplexity/小米等插件） | NanoClaw：Provider合同规范化；CoPaw：MCP白名单安全治理 |
| 部署形态 | 桌面伴侣 + CLI双轨 | PicoClaw：边缘轻量化Worker；Moltis：Docker优先 |

**社区规模对比**（按24h Issue活跃度估算）：
- OpenClaw ≈ 500 | Hermes ≈ 50 | IronClaw ≈ 13 | CoPaw ≈ 30 | 其余项目 ≤ 15

OpenClaw的社区体量相当于后四者之和，但其P0/P1级升级崩溃问题（#133984、#134570等）反映出**规模扩张与质量把控的张力**，与IronClaw专注核心重构的路径形成对照。

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **调度可靠性** | CoPaw、NanoClaw、LobsterAI | cron升级重启后非计划补发（CoPaw #7480/#7476）；missed-run策略缺失（NanoClaw #2398）；定时任务通知缺失（LobsterAI #1620） |
| **MCP兼容性** | OpenClaw、CoPaw、PicoClaw、Moltis | MCP连接失败导致挂起（PicoClaw #3269）；streamable-http协议诊断误报（Moltis #1250）；per-tool白名单未生效（CoPaw #7470）；OAuth MCP工具缺失（OpenClaw #134307） |
| **认证/会话安全** | OpenClaw、Hermes、NanoClaw、CoPaw | Profile克隆后OAuth凭证失效（Hermes #100339）；Docker auth迁移凭证丢失（OpenClaw #134608）；子Agent继承os.environ安全边界（Hermes #99635） |
| **成本可见性** | Hermes、IronClaw | 长会话$191无实时提示（Hermes #100877）；OpenAI prompt_cache_key缺失致命中率从82%→29%（IronClaw #7921） |
| **Agent状态管理** | OpenClaw、Hermes、IronClaw | 升级后7种状态迁移失败（OpenClaw #134570）；分支会话加载/路由/持久化全链路修复（Hermes 7个PR）；Agent Loop能力阶段解耦（IronClaw #8031/#8028） |
| **边缘/轻量化部署** | PicoClaw、Moltis | RISC-V/ARM资源受限Worker模式（PicoClaw #3345）；Docker本地开发认证检测修复（Moltis #1249） |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 架构关键差异 |
|------|----------|----------|--------------|
| **OpenClaw** | 全渠道集成 + 桌面伴侣 + 插件市场 | 大众用户、多通道接入需求者 | Gateway中心架构，依赖`doctor --fix`迁移机制 |
| **Hermes Agent** | 分支会话管理 + 多Profile + 成本追踪 | 深度用户、多会话并行工作者 | 会话分支路由架构，Desktop/CLI双端一致 |
| **IronClaw** | Agent Loop状态机 + WebUI组件统一 + Prompt缓存优化 | 高阶用户、性能敏感场景 | Rust核心，锁无关turn-state，capability阶段解耦 |
| **CoPaw (QwenPaw)** | 测试覆盖 + MCP安全治理 + Cron调度 | 企业级用户、质量敏感团队 | 中文生态适配，Agent Kanban本地化，Streamable-HTTP双协议MCP |
| **NanoClaw** | Provider合同规范化 + 调度策略增强 | 开发者、自托管用户 | CLI-first，`ncl`命令一致性，per-task missed-run策略 |
| **NanoBot** | Agent循环解耦 + 文件系统工具补齐 | 架构研究者、Rust爱好者 | `nanobot.agent.tools.execution`边界独立化 |
| **PicoClaw** | 边缘设备适配 + Telegram/飞书集成 | 资源受限场景、国内企业用户 | 轻量级定位，Worker模式提案指向RISC-V/ARM |
| **Moltis** | Docker部署优化 + MCP诊断工具链 | DevOps、本地部署用户 | `moltis doctor`诊断逻辑完善，推理Effort级别控制 |
| **LobsterAI** | onboarding体验 + 视频分享 + 多语言 | 入门用户、国内用户 | 钉钉/飞书渠道适配，Windows NSIS安装包 |

---

## 6. 社区热度与成熟度分层

```
┌─────────────────────────────────────────────────────────────┐
│  🔥 快速迭代层（日活50+ PR/Issue）                           │
│     OpenClaw · Hermes Agent · CoPaw                         │
│     特征：功能扩张与质量修复并重，版本发布频繁                 │
├─────────────────────────────────────────────────────────────┤
│  ⚡ 架构重构层（日活10-50 PR/Issue）                         │
│     IronClaw · NanoClaw · NanoBot                           │
│     特征：大规模PR攻坚核心债务，暂无版本发布                  │
├─────────────────────────────────────────────────────────────┤
│  🛠️ 稳定打磨层（日活<10 PR/Issue）                          │
│     PicoClaw · Moltis · LobsterAI                           │
│     特征：功能收敛，Bug修复与体验优化为主                     │
├─────────────────────────────────────────────────────────────┤
│  📦 维护期（Dependabot驱动）                                │
│     ZeptoClaw · NullClaw                                    │
│     特征：无新功能开发，依赖自动更新                          │
└─────────────────────────────────────────────────────────────┘
```

**成熟度判断**：
- **IronClaw** 的Agent Loop解耦（executor.rs从2938→890行）与 **NanoBot** 的工具执行边界独立化，标志着生态从"功能堆砌"进入"架构成熟期"
- **OpenClaw** 的500级日活跃度配合v2026.8.2发布，但仍需处理210+个已关闭Issue中的迁移问题，处于"规模成熟但技术债显现"阶段
- **Moltis** 的Docker认证修复与推理Effort级别新增，反映轻量级项目正在补齐企业级能力

---

## 7. 值得关注的趋势信号

### 信号一：调度可靠性成为生产化分水岭
CoPaw（#7480/#7476）、NanoClaw（#2398）、LobsterAI（#1620）同时暴露cron调度问题，表明**定时任务从"可用"到"可靠"是智能体进入生产环境的必经门槛**。建议开发者关注misfire_grace窗口语义、重启补发策略、以及跨版本升级后的状态迁移测试。

### 信号二：MCP生态标准化加速，安全治理滞后
OpenClaw、CoPaw、PicoClaw、Moltis四项目均涉及MCP相关Issue，但焦点从"连接"转向"安全"（白名单失效、诊断误报）。**MCP 2025/2026双协议兼容**（CoPaw #7330）与**streamable-http协议识别**（Moltis #1251）显示协议层正在收敛，但per-tool授权执行（CoPaw #7470）仍是待解问题。

### 信号三：Prompt成本可见性驱动架构优化
IronClaw的prompt_cache_key修复（#7921，命中率82%→29%）与Hermes的成本页脚功能（#100877）反映同一趋势：**长会话成本失控是用户最大痛点之一**。未来模型调用层需内置缓存键管理与成本追踪，而非依赖事后账单。

### 信号四：边缘轻量化与核心重量级的并行演进
PicoClaw的Worker模式提案（#3345，10-20MB内存）与Moltis的Docker本地开发优化，与OpenClaw的Your Home Dock、Hermes的Desktop Companion形成对照——**生态同时向两端延伸**：一端是资源受限的边缘部署，一端是全功能桌面伴侣。开发者需根据目标场景明确技术选型。

### 信号五：升级链兼容性成为社区信任基石
OpenClaw的2026.7.x→8.x升级崩溃循环（#133984/#134570/#134608等）与CoPaw的`max_tokens`→`max_output_length`迁移（#7474）表明，**破坏性变更的测试覆盖直接决定社区留存**。建议引入canary发布、灰度迁移工具、以及向后兼容层作为标准实践。

---

**报告生成时间**：2026-09-02  
**分析师**：Agnes-2.0-Flash（Sapiens AI）

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 | 2026-09-02

## 1. 今日速览
NanoBot 过去 24 小时保持高强度迭代节奏，累计处理 15 条 PR 与 3 条 Issue，其中 6 项已合并/关闭，9 项待审查。核心演进集中在 Agent 循环架构解耦、文件系统工具补齐、上下文生命周期控制及 WebUI/TUI 体验优化。项目暂无新版本发布，但技术债务正在集中清理，代码库向更清晰的模块边界与更稳定的运行态迈进。整体健康度良好，社区贡献活跃，研发链路运转顺畅。

## 2. 版本发布
今日无新版本发布。当前处于功能打磨与架构重构期，建议关注 `copy_file`/`move_file` 工具与 `ephemeral` 上下文支持合并后的版本规划。

## 3. 项目进展
今日合并/关闭的 6 项 PR 显著提升了 Agent 核心的可维护性与运行稳定性：
- **架构解耦**：`HKUDS/nanobot PR #5569` 将工具调用准备、执行、批处理与安全分类逻辑从 `AgentRunner` 中剥离，形成独立的 `nanobot.agent.tools.execution` 边界；

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-09-02**

---

## 1. 今日速览

Hermes Agent 项目今日保持**高活跃度**，过去24小时内新增/更新 Issues 50 条、PR 50 条，社区参与热度稳定。核心工作集中在**Desktop 分支会话路由修复**（多项 PR 合并）、**Bedrock/Anthropic 提供商兼容性修复**以及**成本可见性功能新增**。项目整体健康度良好，但存在若干 P1 级 Bug 需重点关注，特别是会话压缩超时、Profile 克隆后 OAuth 凭证失效等问题。

---

## 2. 版本发布

无新版本发布。当前最新版本仍为 v0.21.0（commit `18a76be124d7c16ed98b629a358b23fef76a7f46`）。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 作者 | 类型 | 摘要 |
|---|---|---|---|
| [#100879](https://github.com/NousResearch/hermes-agent/pull/100879) | OutThisLife | bug | **Desktop 分支会话加载修复** — 解决分支会话在父会话所属 backend 上无法加载的问题 |
| [#70419](https://github.com/NousResearch/hermes-agent/pull/70419) | JonthanaHanh | bug | **分支草稿 resume 失败降级为 create** — 修复首次消息提交丢失问题 |
| [#97359](https://github.com/NousResearch/hermes-agent/pull/97359) | evan-bradford | bug | **按 owner 路由项目会话分支** — 修复非默认 profile 归属的会话分支无法读取问题 |
| [#97747](https://github.com/NousResearch/hermes-agent/pull/97747) | Ahmett101 | bug | **合并重复分支创建** — 添加单次飞行守卫防止重复子会话累积 |
| [#95992](https://github.com/NousResearch/hermes-agent/pull/95992) | mashenchina-max | bug | **导航至分支会话路由** — 修复 URL 停留在父会话的问题 |
| [#94208](https://github.com/NousResearch/hermes-agent/pull/94208) | ClintonEmok | bug | **持久化分支子会话** — 修复分支在重启后丢失问题 |
| [#98551](https://github.com/NousResearch/hermes-agent/pull/98551) | Zeus-Deus | bug | **通过父会话连接路由分支** — 修复跨连接分支永久卡住问题 |
| [#70419](https://github.com/NousResearch/hermes-agent/pull/70419) | JonthanaHanh | bug | 修复分支草稿首次消息提交丢失的回归 |

**进展评估：** 今日合并的 PR 大量集中于 **Desktop 分支会话（Branch Session）稳定性修复**，表明该项目长期存在的核心体验问题正在被系统性解决。7 个相关 PR 形成了一条完整的修复链，覆盖从分支创建、路由、加载到草稿处理的完整生命周期，项目在此方向上取得了实质性推进。

---

## 4. 社区热点

### 讨论最活跃的 Issues

| Issue | 评论数 | 类型 | 热度分析 |
|---|---|---|---|
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 19 | feature | **Bot 群聊在桌面关闭后持续工作** — 高关注度功能需求，涉及 gateway 权威、跨 gateway 传输等核心架构 |
| [#97948](https://github.com/NousResearch/hermes-agent/issues/97948) | 13 | bug | **手动压缩超时与后台工作成功矛盾** — P1 级会话状态问题，影响大会话用户体验 |
| [#62169](https://github.com/NousResearch/hermes-agent/issues/62169) | 7 | bug | **终端沙箱 CWD 删除导致永久故障** — 长期存在的稳定性问题 |
| [#57921](https://github.com/NousResearch/hermes-agent/issues/57921) | 5 | bug | **dashboard 事件循环导致数据库锁定** — 已关闭，涉及 gateway 与 dashboard 共享 state.db 的并发问题 |
| [#93959](https://github.com/NousResearch/hermes-agent/issues/93959) | 4 | bug | **分支创建在现有会话上无限挂起** — 已关闭，修复见 #94208 |

### 关注热点分析

- **#97681（19 评论）** 反映了用户对**无人值守 Bot 运营**的强烈需求，希望 Hermes 能在桌面客户端关闭后仍保持群聊 Bot 正常工作，这与项目已实现的 gateway-owned authority 架构紧密相关。
- **#97948（13 评论）** 揭示了**会话压缩机制的严重不一致性**，手动触发与后台执行行为差异导致用户困惑，是 P1 级稳定性问题。

---

## 5. Bug 与稳定性

### 今日新增/活跃 Bug（按严重程度排列）

| Issue | 严重程度 | 组件 | 摘要 | Fix PR |
|---|---|---|---|---|
| [#100339](https://github.com/NousResearch/hermes-agent/issues/100339) | **P1** | comp/agent, provider/anthropic | Profile 克隆后 OAuth 单次刷新凭证导致兄弟 Profile 失效 | 暂无 |
| [#97948](https://github.com/NousResearch/hermes-agent/issues/97948) | **P1** | comp/agent, comp/tui | 手动压缩 120s 超时但后台 worker 成功，会话分裂失败 | 暂无 |
| [#100858](https://github.com/NousResearch/hermes-agent/issues/100858) | P2 | comp/agent, tool/vision | 自定义 provider + base_url 发送错误密钥导致 401 | 暂无 |
| [#39829](https://github.com/NousResearch/hermes-agent/issues/39829) | P2 | comp/agent, provider/bedrock | Bedrock Converse 拒绝空白占位符，破坏 assistant-first 历史恢复 | 暂无 |
| [#98468](https://github.com/NousResearch/hermes-agent/issues/98468) | P2 | comp/agent, provider/bedrock | Bedrock 流式 reasoning_content 被 `\n\n` 分隔符破坏 | [#100875](https://github.com/NousResearch/hermes-agent/pull/100875) |
| [#100835](https://github.com/NousResearch/hermes-agent/issues/100835) | P2 | comp/agent | auxiliary model: null 被序列化为字面量 "None" | 暂无 |
| [#100870](https://github.com/NousResearch/hermes-agent/issues/100870) | P2 | tool/terminal | Docker 后端远程内核启动失败，大括号重写遗漏分隔符 | 暂无 |
| [#100268](https://github.com/NousResearch/hermes-agent/issues/100268) | P2 | tool/terminal | `/proc/uptime` 不存在导致主机信息报告失败 | 暂无 |
| [#100864](https://github.com/NousResearch/hermes-agent/issues/100864) | P3 | tool/tts | Desktop Bots 语音播放使用活跃 profile 配置而非 Bot 自身配置 | 暂无 |
| [#100436](https://github.com/NousResearch/hermes-agent/issues/100436) | P2 | comp/cli | sqlite3 disk I/O error 导致 Bot 聊天打开失败 | 暂无 |

**稳定性评估：** 今日 P1 级 Bug 集中在**认证/会话状态管理**领域，反映项目在 Profile 克隆和会话压缩等高级功能上的测试覆盖不足。Bedrock 提供商相关问题（#39829, #98468）持续出现，表明多提供商兼容性是长期痛点。

---

## 6. 功能请求与路线图信号

### 活跃功能请求

| Issue/PR | 类型 | 摘要 | 纳入可能性 |
|---|---|---|---|
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | feature | Bot 群聊在桌面关闭后持续工作 | **高** — 基础架构已在 main，待连接生产化 |
| [#100877](https://github.com/NousResearch/hermes-agent/pull/100877) | feature | 每次回复成本页脚、支出警告、/new 交接说明 | **中高** — 成本可见性是用户明确需求 |
| [#100764](https://github.com/NousResearch/hermes-agent/pull/100764) | feature | 多模态模型原生音频和语音路由 | **中** — 替代 #90206，支持 Gemini 音频输入 |
| [#84721](https://github.com/NousResearch/hermes-agent/issues/84721) | feature | Photon/iMessage 入站附件支持 | **低** — 文档明确不支持，需决策 |
| [#99661](https://github.com/NousResearch/hermes-agent/issues/99661) | bug | background_review 无会话结束批处理导致队列洪水 | **中** — 需设计决策 |

### 路线图信号分析

- **成本可见性**（#100877）是当前最活跃的功能 PR，直接回应用户对"runaway session"（失控会话）的担忧，与项目商业化关注点一致。
- **原生音频路由**（#100764）显示项目正在向多模态交互演进，与 Gemini 等模型的能力跟进。
- **Bot 持续运行**（#97681）是架构层面的核心需求，一旦完成将显著提升 Hermes 作为无人值守 Agent 平台的竞争力。

---

## 7. 用户反馈摘要

### 真实痛点提炼

| 痛点类别 | 具体反馈 | 来源 |
|---|---|---|
| **会话管理混乱** | 分支创建后 UI 不渲染、URL 不更新、重复子会话累积 | #93959, #97414, #96513, #98551 |
| **成本不可见** | 长时间会话花费 $191.61 却无实时提示，只能在账单发现 | #100877 |
| **多 Profile 认证问题** | Profile 克隆后 OAuth 单次刷新凭证导致兄弟 Profile 集体失效 | #100339 |
| **提供商兼容性** | Bedrock/Anthropic 边界情况处理不当（空白占位符、reasoning 分隔符） | #39829, #98468 |
| **Desktop 体验** | 分支会话加载失败、TTS 配置不继承、KDE 图标主题失效 | #100316, #100864 |
| **安全边界** | 子 Agent 继承父进程完整环境变量，存在密钥泄露风险 | #99635 |
| **工具设计** | skill_manage 审批门是约定而非强制边界，write_file/terminal 可直接访问技能目录 | #97229 |

### 用户满意度信号

- **正面：** 用户对 Bot 群聊持续运行功能期待值高（#97681 19 评论）
- **负面：** 分支会话的反复故障导致用户 Frustration，多个 Issue 描述"永久卡住"、"无限挂起"
- **中性：** 成本追踪功能被认可（内部已有 `session_estimated_cost_usd`），但用户希望更早可见

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 天数 | 严重程度 | 状态 | 建议 |
|---|---|---|---|---|---|
| [#39829](https://github.com/NousResearch/hermes-agent/issues/39829) | 2026-06-05 | ~89 天 | P2 | OPEN | Bedrock 空白占位符问题长期存在，建议优先修复 |
| [#62169](https://github.com/NousResearch/hermes-agent/issues/62169) | 2026-07-10 | ~54 天 | P2 | OPEN | 终端沙箱 CWD 删除导致永久故障，影响稳定性 |
| [#57921](https://github.com/NousResearch/hermes-agent/issues/57921) | 2026-07-03 | ~61 天 | P2 | CLOSED | 已关闭，但类似问题可能重现 |
| [#81427](https://github.com/NousResearch/hermes-agent/issues/81427) | 2026-08-08 | ~25 天 | P3 | OPEN | 内存提供者在 Desktop 会话中未注入工具 |
| [#84721](https://github.com/NousResearch/hermes-agent/issues/84721) | 2026-08-12 | ~21 天 | P3 | OPEN | Photon/iMessage 附件支持需求 |

### 待决策的设计问题

- **#97229**: skill_manage 审批门是约定而非强制边界 — 需维护者明确安全模型定位
- **#99635**: delegate_task 子 Agent 继承完整 os.environ — 安全边界设计待决策

---

**报告生成时间：** 2026-09-02  
**数据范围：** 过去 24 小时  
**分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-09-02

---

## 1. 今日速览

过去24小时PicoClaw项目保持活跃，共产生 **3条活跃Issue** 与 **4条PR**（1条已合并）。无新版本发布。社区层面集中反馈了MCP连接稳定性、飞书配置报错等关键使用问题，同时Telegram通道多项修复正在推进。整体项目健康度良好，维护者响应及时，PR合并节奏稳定。

---

## 2. 版本发布

暂无新版本发布。

---

## 3. 项目进展

### 已合并 PR

- **#3359** [CLOSED] `feat(repository-reviews): enforce product and retention contracts`
  - **作者:** dkropachev
  - **说明:** 引入可重建的仓库审查机制，支持规范化产品契约、资源分类、生命周期/保留规则及确定性验收门控，强化了资源归属（`rrw_*` / `rdf_*` / `rrf_*`）和兼容性约束（`rfn_*`）。
  - **影响:** 提升了项目治理与资源管理规范，属于架构层改进，无对外功能变更。
  - 🔗 [PR #3359](https://github.com/sipeed/picoclaw/pull/3359)

---

## 4. 社区热点

### 🔥 Issue #3269 — MCP Server 连接失败导致 Agent 挂起
- **作者:** ruiyigen | **评论:** 8 | **👍:** 1 | **状态:** OPEN / stale
- **摘要:** MCP server 连接失败时 agent loop 进入挂起状态，导致聊天界面停止响应。影响多用户实际使用场景。
- **诉求分析:** 高优先级稳定性问题，涉及核心 agent 循环的容错能力，用户期望具备超时降级或自动重试机制。
- 🔗 [Issue #3269](https://github.com/sipeed/picoclaw/issues/3269)

### 🔥 Issue #3355 — 飞书渠道配置报错
- **作者:** ttghub | **状态:** OPEN（刚提交）
- **摘要:** `config.json` 中 `channel_list.feishu.app_id` 被识别为未知字段，导致飞书连接配置失败。
- **诉求分析:** 配置兼容性问题，可能是 nightly 构建中字段命名变更未同步文档所致。
- 🔗 [Issue #3355](https://github.com/sipeed/picoclaw/issues/3355)

### 💬 Issue #3345 — 轻量级 PicoClaw Worker 模式提案
- **作者:** kvnloo | **评论:** 1
- **摘要:** 提议为资源受限的边缘设备（RISC-V/ARM/MIPS、树莓派、旧安卓手机等，可用内存约10–20MB）设计轻量化 worker 模式，扩展分布式 agent 系统的部署边界。
- **诉求分析:** 方向具有战略价值，契合 PicoClaw 的轻量化定位，但实现规模较大，需进一步细化方案。
- 🔗 [Issue #3345](https://github.com/sipeed/picoclaw/issues/3345)

---

## 5. Bug 与稳定性

| 严重度 | 问题 | Issue | Fix PR |
|--------|------|-------|--------|
| **高** | MCP 连接失败导致 agent loop 挂起，界面完全停止响应 | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | 暂无 |
| **中** | 飞书 channel 配置字段 `app_id` 报未知字段错误 | [#3355](https://github.com/sipeed/picoclaw/issues/3355) | 暂无 |
| **低** | Telegram：群内回复 bot 自身消息未触发响应（`mention_only` 模式下） | — | [#3357](https://github.com/sipeed/picoclaw/pull/3357) **已修复** |
| **低** | Telegram：回复文件消息时 quoted document 未被正确附加 | — | [#3356](https://github.com/sipeed/picoclaw/pull/3356) **已修复** |
| **低** | Telegram：非回复形式的 @mention 消息响应未关联到原问题 | — | [#3358](https://github.com/sipeed/picoclaw/pull/3358) **已修复** |

> **稳定性评估:** 今日修复了 Telegram 渠道的 3 项交互体验 Bug，稳定性有所提升。但 MCP 连接挂起（#3269）与飞书配置报错（#3355）尚未有修复 PR，需关注。

---

## 6. 功能请求与路线图信号

- **轻量级 Worker 模式（Issue #3345）**— 提案为低资源边缘设备设计专用运行模式，若采纳将显著扩展 PicoClaw 的部署场景，适合纳入中长期路线图。
- **Telegram 交互优化（PR #3356/#3357/#3358）**— 三项修复均指向 Telegram 渠道的对话连贯性改进，反映用户对群聊场景下 bot 行为一致性的强烈需求，预计将在近期版本中随 PR 合并一起发布。

---

## 7. 用户反馈摘要

- **痛点 1（高共鸣）:** MCP 服务不稳定时整个 agent 挂死，用户体验严重受损。8条评论表明该问题已困扰多位用户。
- **痛点 2:** 飞书渠道配置兼容性问题阻碍了新用户接入，尤其影响国内企业用户群体。
- **痛点 3:** Telegram 群聊场景下 bot 回复断连、文件引用丢失等问题影响对话流畅度，已有多项修复正在推进。
- **亮点:** 社区对 PicoClaw 在资源受限设备上的扩展能力抱有期待，轻量 worker 模式提案获得关注。

---

## 8. 待处理积压

| Issue / PR | 类型 | 创建时间 | 评论数 | 备注 |
|------------|------|----------|--------|------|
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) | Bug | 2026-07-20 | 8 | 已 stale，高优先级，需维护者介入 |
| [#3355](https://github.com/sipeed/picoclaw/issues/3355) | Bug | 2026-09-01 | 0 | 刚提交，暂无回复 |
| [#3345](https://github.com/sipeed/picoclaw/issues/3345) | 功能提案 | 2026-08-25 | 1 | 长期未深入讨论，值得关注 |
| [#3358](https://github.com/sipeed/picoclaw/pull/3358) | Fix | 2026-09-01 | — | 待合并 |
| [#3357](https://github.com/sipeed/picoclaw/pull/3357) | Fix | 2026-09-01 | — | 待合并 |
| [#3356](https://github.com/sipeed/picoclaw/pull/3356) | Fix | 2026-09-01 | — | 待合并 |

> **建议:** #3269 已 stale 且评论最多，建议维护者优先响应；#3355 为新提交 Bug，建议快速确认配置字段命名是否变更。三项 Telegram 修复 PR 已就绪，可安排合并。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-09-02

## 1. 今日速览

过去 24 小时内，NanoClaw 项目保持中等活跃度：共新增 2 条 Issue、13 条 PR，其中 1 条已合并、12 条待审。核心开发围绕 Provider 重构与 Agent Runner 稳定性修复展开，未发布新版本。Issues 聚焦于 CLI 行为不一致与 messaging-group 生命周期管理问题，PR 流以重构类为主，反映项目正处于 provider 架构规范化阶段，整体健康度良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭 PR

| PR | 标题 | 作者 | 意义 |
|----|------|------|------|
| [#3698](https://github.com/NanoClawAI/nanoclaw/pull/3698) | chore(container): bump Bun and Claude runtimes | omri-maya | 统一容器运行时至 Bun 1.4.0、Claude Code 2.1.257、Claude Agent SDK 0.3.257，CI 与发布验证链路已对齐 |

### 今日关键推进

- **Provider 重构系列**：zvi-fried 连续提交 6 个 PR（[#3581](https://github.com/NanoClawAI/nanoclaw/pull/3581)、[#3584](https://github.com/NanoClawAI/nanoclaw/pull/3584)、[#3585](https://github.com/NanoClawAI/nanoclaw/pull/3585)、[#3586](https://github.com/NanoClawAI/nanoclaw/pull/3586)、[#3588](https://github.com/NanoClawAI/nanoclaw/pull/3588)、[#3591](https://github.com/NanoClawAI/nanoclaw/pull/3591)），系统性地声明并实现 `opencode` 与 `codex` 的 provider contract，将 provider 指令渲染纳入 core-owned canon。此系列是项目架构规范化的核心里程碑。
- **Sweep 超时可配置化**：[#3646](https://github.com/NanoClawAI/nanoclaw/pull/3646) 修复了慢速本地模型推理被误杀的隐患，kill threshold 从硬编码 30 分钟改为可配置。
- **调度策略增强**：[#3696](https://github.com/NanoClawAI/nanoclaw/pull/3696) 为周期性任务引入 per-task missed-run policy，解决错过调度窗口后行为不可预期的问题。
- **Keenable MCP 工具集成**：[#3697](https://github.com/NanoClawAI/nanoclaw/pull/3697) 新增 web search / page fetch 远程 MCP 工具 skill，扩展 agent 工具生态。

---

## 4. 社区热点

### 活跃 Issue

- **[Issue #3700](https://github.com/NanoClawAI/nanoclaw/issues/3700)** — `Destination local-names don't repoint when target messaging-group is recreated`
  - **痛点**：当 messaging-group 重建后，指向旧 group 的 local-name 未自动更新，导致 outbound send 报告成功但实际投递至 dead target。
  - **背景**：源于 [#3576](https://github.com/NanoClawAI/nanoclaw/issues/3576)-adjacent 修复工作，属于状态同步类深层 bug。

- **[Issue #3699](https://github.com/NanoClawAI/nanoclaw/issues/3699)** — `ncl destinations create/remove don't auto-fill --agent-group-id`
  - **痛点**：CLI 行为不一致，其他 group-scoped 命令（tasks 系列）通过 `groupArg(args, ctx)` 自动填充 `agent_group_id`，但 destinations 命令未继承此行为，增加用户操作负担。

### 活跃 PR（评论/关注度高）

- **[PR #3427](https://github.com/NanoClawAI/nanoclaw/pull/3427)** — `fix(agent-runner): tell the agent send_card drops callback actions`
  - 由 glifocat 提交，修复 `send_card` 工具误导 agent 的问题：bridge 静默丢弃 callback buttons 但工具仍报告成功。改为明确定义 display cards 为纯文本，避免 agent 产生错误预期。
  - **诉求分析**：用户反馈 Chat SDK bridge 的行为与工具契约不一致，影响 agent 交互可靠性。

---

## 5. Bug 与稳定性

| 级别 | Issue/PR | 描述 | Fix 状态 |
|------|----------|------|----------|
| 🔴 高 | [Issue #3700](https://github.com/NanoClawAI/nanoclaw/issues/3700) | messaging-group 重建后 local-name 未重定向，导致静默投递失败 | 无 open PR |
| 🟡 中 | [Issue #3699](https://github.com/NanoClawAI/nanoclaw/issues/3699) | `ncl destinations` 命令未自动填充 `--agent-group-id`，CLI 行为不一致 | 无 open PR |
| 🟡 中 | [PR #3427](https://github.com/NanoClawAI/nanoclaw/pull/3427) | `send_card` 误报 callback actions 成功（bridge 静默丢弃） | 待合并 |
| 🟢 低 | [PR #3646](https://github.com/NanoClawAI/nanoclaw/pull/3646) | sweep kill timeout 硬编码导致慢推理被误杀 | 待合并 |

---

## 6. 功能请求与路线图信号

| 信号 | 来源 | 判断 |
|------|------|------|
| 周期性任务 missed-run 策略 | [PR #3696](https://github.com/NanoClawAI/nanoclaw/pull/3696) (closes #2398) | 已实现，待合并，预计纳入下一版本 |
| Keenable MCP 工具 skill | [PR #3697](https://github.com/NanoClawAI/nanoclaw/pull/3697) | 第三方 skill 贡献，扩展 agent 工具生态 |
| Speed inference property | [PR #3592](https://github.com/NanoClawAI/nanoclaw/pull/3592) | core-owned group 属性，支持更精细的 provider 路由策略 |
| Provider contract 规范化 | 6 个连续 refactor PRs by zvi-fried | 架构重构主线，预计下一版本完成核心 provider 接口冻结 |

---

## 7. 用户反馈摘要

- **messaging-group 生命周期管理**：[#3700](https://github.com/NanoClawAI/nanoclaw/issues/3700) 反映用户在修复 Discord `--platform-id` 格式错误（[#3576](https://github.com/NanoClawAI/nanoclaw/issues/3576)）后，发现 local-name 未跟随 group 重建而更新，导致"虚假成功"投递。这是生产环境真实反馈，凸显状态一致性保障的缺失。
- **CLI 一致性体验**：[#3699](https://github.com/NanoClawAI/nanoclaw/issues/3699) 指出 destinations 命令缺少 group-scoped 自动填充，与其他命令行为不符，增加用户心智负担。
- **Agent 工具契约透明度**：[#3427](https://github.com/NanoClawAI/nanoclaw/pull/3427) 的修复方向表明用户期望工具行为与文档/契约严格对齐，静默丢弃 callback actions 被识别为严重误导。

---

## 8. 待处理积压

| 类型 | 编号 | 描述 | 关注建议 |
|------|------|------|----------|
| 🐛 Bug | [#3700](https://github.com/NanoClawAI/nanoclaw/issues/3700) | local-name 未跟随 messaging-group 重建重定向 | 高优先级，影响生产投递可靠性，需排入 sprint |
| 🐛 Bug | [#3699](https://github.com/NanoClawAI/nanoclaw/issues/3699) | `ncl destinations` 未自动填充 `--agent-group-id` | 中优先级，CLI 一致性修复，成本低 |
| 📦 PR 积压 | [#3427](https://github.com/NanoClawAI/nanoclaw/pull/3427)、[#3646](https://github.com/NanoClawAI/nanoclaw/pull/3646)、[#3696](https://github.com/NanoClawAI/nanoclaw/pull/3696)、[#3697](https://github.com/NanoClawAI/nanoclaw/pull/3697) | 4 个功能/修复 PR 待合并 | 建议优先 review #3427 和 #3646，均为稳定性相关 |
| 🏗️ 架构 | [#3581–#3591](https://github.com/NanoClawAI/nanoclaw/pull/3581) 系列 | 6 个 provider refactor PR 待合并 | 建议按依赖顺序 review，确保 contract 定义与实现一致 |

---

**项目健康度评估**：⭐⭐⭐⭐☆  
- 开发节奏稳定，PR 合并效率高（24h 内 1 条合并、12 条活跃）
- Provider 重构主线清晰，架构规范化进展良好
- 存在 2 个未修复的 Bug Issue，建议优先处理 #3700（生产影响）
- 无新版本发布，下一版本预计待 provider 重构系列合并且回归验证完成后发布

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-09-02

---

## 1. 今日速览

IronClaw 在过去24小时内保持了高强度的开发节奏，共处理 **13 个 Issues** 和 **19 个 PR**，其中 4 个 Issue 关闭、8 个 PR 已合并，整体活跃度处于高位。项目当前无新版本发布，但正在进行**大规模前端组件统一重构**（WebUI 共享组件迁移）和**Agent Loop 核心机制解耦**，两者均指向下一阶段大版本的功能完善。CI 可靠性（nextest 并行化、Slack 告警修复）和 LLM 层性能优化（GitHub 响应压缩、prompt cache 修复）也是今日主要进展方向。项目健康度良好，核心维护者持续活跃。

---

## 2. 版本发布

> 过去24小时无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（8 条）

| PR | 类型 | 摘要 | 贡献者 |
|---|---|---|---|
| [#8031](https://github.com/nearai/ironclaw/pull/8031) | refactor | **Agent Loop 能力阶段机制解耦**：将 `executor/capabilities.rs` 从 2,938 行精简至 890 行，提取批调度、分发/恢复、故障规范化、结果持久化等独立模块 | henrypark133 |
| [#8028](https://github.com/nearai/ironclaw/pull/8028) | refactor | **Agent Loop 状态与阶段所有权对齐**：拆分 checkpoint state 为 compaction、recovery、reply-admission、stop-control 等凝聚模块 | henrypark133 |
| [#7997](https://github.com/nearai/ironclaw/pull/7997) | feat | **WebUI Inference 选择器显示模型能力图标**：支持 Text/Image 输入输出能力的图标化展示及 hover 描述，兼容旧版模型列表和详细目录格式 | italic-jinxin |
| [#8013](https://github.com/nearai/ironclaw/pull/8013) | ci | **CI 测试并行化**：通过 nextest 将 affected crate 测试从 Cargo 串行调度改为四进程并行，提升 CI 效率 | henrypark133 |
| [#8014](https://github.com/nearai/ironclaw/pull/8014) | fix | **修复 Slack 显式提及丢失**：在回调去重逻辑中保留 `app_mention` 回调中的提及信息，避免 `message` 回调覆盖 | henrypark133 |
| [#7998](https://github.com/nearai/ironclaw/pull/7998) | feat | **NEAR AI 模型能力透传**：新增 provider-neutral model catalog，保留 NEAR AI 模型的 input/output modalities，同时兼容遗留 `list_models()` API | italic-jinxin |
| [#8027](https://github.com/nearai/ironclaw/pull/8027) | fix | **修复 Slack 运行查找逻辑**：将查找依据从 `event_id` 改为消息身份，修复连续 33 次 canary 测试超时失败的问题 | BenKurrek |
| [#7996](https://github.com/nearai/ironclaw/pull/7996) | perf | **压缩 GitHub 仓库列表响应**：将 `github.list_repos` 从返回完整 81 字段 REST 对象改为仅投影模型有用字段，单次响应从 ~5.5KB 降至 KB 级别 | linhongyu510 |

**整体进展评估**：今日核心突破集中在 **Agent Loop 内部复杂度控制** 和 **前端组件统一化**。Agent Loop 连续两次大规模重构（#8028 → #8031）标志着核心执行路径已达到新的可维护性水平；WebUI 共享组件迁移（SearchField、InlineNotice、Input/SelectMenu）持续推进，设计系统一致性显著提升；GitHub 响应压缩和 prompt cache 修复直指生产环境成本痛点。项目正处于**架构收敛期**，为下一阶段功能扩张打基础。

---

## 4. 社区热点

### 高关注度 Issue/PR

| 议题 | 类型 | 热度分析 | 链接 |
|---|---|---|---|
| [#7921](https://github.com/nearai/ironclaw/issues/7921) [p2] OpenAI 系列后端 prompt_cache_key 缺失 | 性能优化 | 测量显示缓存命中率从 ~82% 暴跌至 ~29%（>200 调用后），直接影响 LLM 调用成本和延迟。**作者 henrypark133 持续跟踪至 09-02**，表明为当前优先级最高的性能瓶颈 | [Issue](https://github.com/nearai/ironclaw/issues/7921) |
| [#7986](https://github.com/nearai/ironclaw/issues/7986) [bug] GitHub 列表响应过大 | 性能优化 | 单次 98 仓库列表产生 **519KB** 原始数据，作者测量了具体生产 trace（run `13bad7f5`），问题描述精确到字段数和字节数。**已合并修复 PR #7996** | [Issue](https://github.com/nearai/ironclaw/issues/7986) |
| [#8016](https://github.com/nearai/ironclaw/issues/8016) [bug][ci] 锁无关 turn-state 测试间歇性超时 | CI 稳定性 | 单条 Rust 测试（`reborn_turn_state_lock_free_submit_parity`）在 CI 中间歇超过 5 秒预算，属于并发竞态类问题，**尚未关闭** | [Issue](https://github.com/nearai/ironclaw/issues/8016) |
| [#8015](https://github.com/nearai/ironclaw/issues/8015) [qa-bug] Rootless Docker 沙箱不可写 | 兼容性问题 | UID/GID namespace 不匹配导致非 root 用户无法写入 persistent workspace，影响自托管用户群体，**尚未关闭** | [Issue](https://github.com/nearai/ironclaw/issues/8015) |

---

## 5. Bug 与稳定性

| 严重级别 | Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|---|
| 🔴 **高** | [#8015](https://github.com/nearai/ironclaw/issues/8015) | Rootless Docker 沙箱 workspace 因 UID/GID namespace 不匹配导致不可写，影响非 root 用户自托管场景 | OPEN | 无 |
| 🟠 **中** | [#8025](https://github.com/nearai/ironclaw/issues/8025) | 输入字段特殊字符处理异常：字符被剥离或引发错误，疑似与上次发布中的编码变更相关 | OPEN | 无 |
| 🟡 **低** | [#8016](https://github.com/nearai/ironclaw/issues/8016) | CI 中 `reborn_turn_state_lock_free_submit_parity` 测试间歇超时（>5s），并发竞态类问题 | OPEN | 无 |

**稳定性评估**：今日 Bug 集中于**环境兼容性**（Rootless Docker）和**编码处理**（特殊字符），均为可复现的具体缺陷。CI 测试间歇超时是遗留的并发边界问题。值得注意的是 **GitHub 响应过大（#7986）和 Slack 运行查找失败（#8027）已分别通过 #7996 和 #8027 修复并关闭**，显示团队对生产可观测性问题的快速响应能力。

---

## 6. 功能请求与路线图信号

### 前端组件统一化（高确定性）

以下 Issue 均有对应 PR 跟进，预计纳入**下一版本（v1.4.x 或 v1.5.0）**：

| Issue | 对应 PR | 内容 | 链接 |
|---|---|---|---|
| [#8020](https://github.com/nearai/ironclaw/issues/8020) | [#8024](https://github.com/nearai/ironclaw/pull/8024) | Workspace 和 Logs 过滤器迁移至共享 `SearchField` | [Issue](https://github.com/nearai/ironclaw/issues/8020) / [PR](https://github.com/nearai/ironclaw/pull/8024) |
| [#8019](https://github.com/nearai/ironclaw/issues/8019) | [#8022](https://github.com/nearai/ironclaw/pull/8022) | Automations 状态横幅迁移至 `InlineNotice` | [Issue](https://github.com/nearai/ironclaw/issues/8019) / [PR](https://github.com/nearai/ironclaw/pull/8022) |
| [#8018](https://github.com/nearai/ironclaw/issues/8018) | [#8021](https://github.com/nearai/ironclaw/pull/8021) | SettingsField 原生控件替换为共享 `Input` 和 `SelectMenu` | [Issue](https://github.com/nearai/ironclaw/issues/8018) / [PR](https://github.com/nearai/ironclaw/pull/8021) |
| [#8017](https://github.com/nearai/ironclaw/issues/8017) | [#8023](https://github.com/nearai/ironclaw/pull/8023) | Extension Configure 流程迁移至共享表单组件 | [Issue](https://github.com/nearai/ironclaw/issues/8017) / [PR](https://github.com/nearai/ironclaw/pull/8023) |

### 其他信号

- **Slack 渐进式回复与原生 Agent UI**（[#8006](https://github.com/nearai/ironclaw/pull/8006)）：大型功能 PR，已开放待审，支持 provider-neutral `ReplyDocument` 和 Slack 端展示适配，预计为 Slack 集成重大更新。
- **WebUI 会话事件传输统一**（[#8010](https://github.com/nearai/ironclaw/pull/8010)）：实现统一 WebSocket 传输和运行完成通知，设计文档来自 `docs/internal/design/2026-08-13-webapp-run-notifications.md`，预计纳入同一版本。
- **Dogfooding 周期**（[#8026](https://github.com/nearai/ironclaw/issues/8026)）：新一轮内部测试周期（08/31 - 09/06）已启动，表明团队正在为下一版本发布进行 QA 演练。

---

## 7. 用户反馈摘要

| 来源 | 用户痛点/反馈 | 提炼 |
|---|---|---|
| [#8025](https://github.com/nearai/ironclaw/issues/8025) | 特殊字符在输入字段中导致输出错误，字符被剥离或引发异常 | **编码处理回归**：上次发布的编码变更引入了输入转义问题，影响所有使用特殊字符的用户场景（代码片段、路径、非 ASCII 文本） |
| [#7986](https://github.com/nearai/ironclaw/issues/7986) | GitHub 列表工具返回完整 REST 响应，单次调用消耗 519KB 上下文预算 | **上下文预算浪费严重**：LLM 工具返回值未做投影过滤，直接转发原始 API 响应，导致 token 浪费和推理成本上升 |
| [#7921](https://github.com/nearai/ironclaw/issues/7921) | OpenAI 系列后端未发送 `prompt_cache_key`，缓存命中率从 82% 降至 29% | **缓存策略不对称**：Anthropic 已实现 `cache_control` 断点，但 OpenAI 系列后端未对齐，导致调用成本显著上升 |
| [#8015](https://github.com/nearai/ironclaw/issues/8015) | 非 root 用户在 Rootless Docker 环境中 workspace 不可写 | **自托管兼容性缺陷**：UID/GID namespace 映射问题影响普通用户的本地部署体验，对 DevOps 用户群体影响较大 |
| [#7971](https://github.com/nearai/ironclaw/issues/7971) / [#7970](https://github.com/nearai/ironclaw/issues/7970) | NEAR AI 模型能力信息在 WebUI 中未展示，模型以纯文本显示 | **模型能力可见性不足**：用户无法直观了解各模型支持的输入输出类型，影响 Inference 选择决策 |

---

## 8. 待处理积压

| 类型 | 编号 | 描述 | 风险 | 建议 |
|---|---|---|---|---|
| 🐛 **Bug** | [#8025](https://github.com/nearai/ironclaw/issues/8025) | 特殊字符输入处理回归 | 用户输入兼容性，影响面可能较广 | 优先排查上次编码相关变更，回归测试覆盖 ASCII/UTF-8/转义字符 |
| 🐛 **Bug** | [#8015](https://github.com/nearai/ironclaw/issues/8015) | Rootless Docker workspace 不可写 | 自托管用户核心功能阻断 | 需补充非 root 用户的 CI 测试用例，确认 namespace 映射逻辑 |
| 🐛 **Bug** | [#8016](https://github.com/nearai/ironclaw/issues/8016) | 锁无关 turn-state 测试间歇超时 | CI 可靠性，可能掩盖真正的并发问题 | 增加测试重试机制或分析 lock-free 路径的边界条件 |
| 📋 **Epic** | [#8026](https://github.com/nearai/ironclaw/issues/8026) | Dogfooding & QA 周期（08/31 - 09/06） | 新版本发布前的质量关口 | 跟踪该 Epic 下新发现的 Issue 数量，评估发布 readiness |
| 🔓 **PR 积压** | [#8006](https://github.com/nearai/ironclaw/pull/8006) | Slack 渐进式回复 + 原生 Agent UI | 大型功能 PR，已开放等待审查 | XL 尺寸，建议安排核心维护者 review 以加速合并 |
| 🔓 **PR 积压** | [#8010](https://github.com/nearai/ironclaw/pull/8010) | WebUI 会话事件传输统一 | 大型功能 PR，已开放等待审查 | 与 #8006 类似，涉及架构变更需仔细审查 |

---

**报告生成时间**：2026-09-02  
**数据周期**：过去 24 小时（2026-09-01 ~ 2026-09-02）  
**分析师**：Agnes-2.0-Flash（Sapiens AI）

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 — 2026-09-02

## 1. 今日速览

LobsterAI 今日项目活跃度中等：过去24小时关闭了9个长期无人响应的 stale issue，同时有3个新 issue 保持活跃；PR 方面合并了6个提交，主要集中在 onboarding 体验优化、analytics 埋点完善和视频分享功能。无新版本发布，整体处于日常迭代节奏，未出现大规模功能突破或阻塞性危机。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并的 PR 共6条，主要推进方向如下：

| PR | 类型 | 内容 | 链接 |
|---|---|---|---|
| #2593 | feat | 支持模型生成视频分享，含溯源、权限校验及远程预览 | [PR #2593](https://github.com/netease-youdao/LobsterAI/pull/2593) |
| #2594 | fix | 优化 onboarding 引导动画过渡、鼠标指针大小及 CTA 样式 | [PR #2594](https://github.com/netease-youdao/LobsterAI/pull/2594) |
| #2596 | fix | 追踪 chat login CTA 点击埋点 | [PR #2596](https://github.com/netease-youdao/LobsterAI/pull/2596) |
| #2591 | feat | 新增首次运行用户引导漏斗 analytics 追踪 | [PR #2591](https://github.com/netease-youdao/LobsterAI/pull/2591) |
| #2595 | fix | 修复 Windows NSIS 安装包 staging drive 预检问题 | [PR #2595](https://github.com/netease-youdao/LobsterAI/pull/2595) |
| #2592 | fix | 修复用户指南展示问题 | [PR #2592](https://github.com/netease-youdao/LobsterAI/pull/2592) |

**小结：** 今日进展以产品体验打磨（onboarding、analytics）和新功能视频分享为主，无核心架构变更。

---

## 4. 社区热点

今日无新增高热度讨论，但以下长期 issue 持续引发关注：

- **[Issue #1614](https://github.com/netease-youdao/LobsterAI/issues/1614)** — 请求将 hermes-agent 作为可选 AI 引擎接入，与 openclaw 平级。反映用户希望扩展底层引擎生态的诉求。
- **[Issue #1620](https://github.com/netease-youdao/LobsterAI/issues/1620)** — 请求定时任务完成后推送系统原生通知。用户期望跨平台（macOS/Windows/Linux）支持，默认关闭需手动开启。
- **[Issue #1105](https://github.com/netease-youdao/LobsterAI/issues/1105) & [Issue #1107](https://github.com/netease-youdao/LobsterAI/issues/1107)** — 钉钉定时任务 IM 通知路由缺陷及 pollOnce() 并发重入问题，均有对应 PR 待合并（见第8节）。

---

## 5. Bug 与稳定性

| 级别 | Issue | 描述 | Fix PR | 链接 |
|---|---|---|---|---|
| 🔴 高 | #1587 | 更新最新版本后首次启动崩溃 | — | [Issue #1587](https://github.com/netease-youdao/LobsterAI/issues/1587) |
| 🔴 高 | #1589 | 会话功能、定时任务功能均无法正常执行 | — | [Issue #1589](https://github.com/netease-youdao/LobsterAI/issues/1589) |
| 🔴 高 | #1627 | 执行复杂任务时客户端崩溃 | — | [Issue #1627](https://github.com/netease-youdao/LobsterAI/issues/1627) |
| 🟡 中 | #1617 | 删除技能后列表未同步刷新，重启仍残留 | — | [Issue #1617](https://github.com/netease-youdao/LobsterAI/issues/1617) |
| 🟡 中 | #1586 | 中英文切换后部分内容未翻译（条款、工具风格） | — | [Issue #1586](https://github.com/netease-youdao/LobsterAI/issues/1586) |
| 🟡 中 | #1622 | 添加自定义模型后测试失败 | — | [Issue #1622](https://github.com/netease-youdao/LobsterAI/issues/1622) |
| 🟡 中 | #1632 | 切换本地模型后原有 skill 全部失效 | — | [Issue #1632](https://github.com/netease-youdao/LobsterAI/issues/1632) |
| 🟢 低 | #1112 | 表格 Table 顶部/底部存在不明留白 | — | [Issue #1112](https://github.com/netease-youdao/LobsterAI/issues/1112) |
| 🟡 中 | #1105 | 钉钉 IM 通知路由因前缀未剥离导致消息无法送达 | ✅ [#1106](https://github.com/netease-youdao/LobsterAI/pull/1106) | [Issue #1105](https://github.com/netease-youdao/LobsterAI/issues/1105) |
| 🟡 中 | #1107 | pollOnce() 无重入保护，stopPolling() 后仍有幽灵事件 | ✅ [#1108](https://github.com/netease-youdao/LobsterAI/pull/1108) | [Issue #1107](https://github.com/netease-youdao/LobsterAI/issues/1107) |

**小结：** 今日无新增 crash 报告，但多个已关闭的 stale issue 中暴露了启动崩溃、任务执行异常等严重稳定性问题，建议维护者优先跟进 #1587、#1589、#1627。

---

## 6. 功能请求与路线图信号

| 请求 | Issue | 分析 |
|---|---|---|
| 添加 hermes-agent 作为可选 AI 引擎 | [#1614](https://github.com/netease-youdao/LobsterAI/issues/1614) | 用户希望扩展引擎支持，与现有 openclaw 并列。若项目有引擎抽象层，纳入成本较低。 |
| 定时任务完成后系统原生通知 | [#1620](https://github.com/netease-youdao/LobsterAI/issues/1620) | 明确的需求，已附详细功能要点（默认关闭、权限引导、三端支持）。与今日合并的 PR #2593 视频分享属同一迭代方向，可纳入下一版本规划。 |
| 自定义模型支持 | [#1622](https://github.com/netease-youdao/LobsterAI/issues/1622) | 用户反馈添加自定义模型后测试失败，需排查后端适配层兼容性。 |

---

## 7. 用户反馈摘要

- **多语言国际化不完整**：切换至英文后，「条款」和「工具风格」等页面仍显示中文，用户体验割裂（[#1586](https://github.com/netease-youdao/LobsterAI/issues/1586)）。
- **技能管理 UX 缺陷**：删除技能后前端列表未刷新，且重启无效，说明技能缓存与 UI 状态同步机制存在缺陷（[#1617](https://github.com/netease-youdao/LobsterAI/issues/1617)）。
- **本地模型切换破坏现有技能**：用户切换到本地模型后原有 skill 全部不可用，社区需要更清晰的 skill 兼容性说明或自动迁移机制（[#1632](https://github.com/netease-youdao/LobsterAI/issues/1632)）。
- **定时任务通知缺失**：用户无法在应用外感知任务完成状态，期望通过系统原生通知获知结果（[#1620](https://github.com/netease-youdao/LobsterAI/issues/1620)）。
- **复杂任务崩溃**：执行稍复杂任务即出现客户端崩溃，稳定性亟待提升（[#1627](https://github.com/netease-youdao/LobsterAI/issues/1627)）。

---

## 8. 待处理积压

以下 PR 已就绪但尚未合并，关联的 issue 已被标记为 stale，建议维护者尽快 review：

| PR | 关联 Issue | 内容 | 链接 |
|---|---|---|---|
| #1106 | #1105 | 修复钉钉 IM 通知路由前缀问题 | [PR #1106](https://github.com/netease-youdao/LobsterAI/pull/1106) |
| #1108 | #1107 | 修复 pollOnce() 并发重入及幽灵事件 | [PR #1108](https://github.com/netease-youdao/LobsterAI/pull/1108) |
| #1113 | — | OpenClaw gateway 配置延迟同步 flush 优化 | [PR #1113](https://github.com/netease-youdao/LobsterAI/pull/1113) |

**健康度评估：** 项目当前处于稳定迭代期，合并节奏正常，但 stale issue 积压较多（今日关闭9个），且多个高优先级 bug 尚无活跃开发进展。建议维护者优先处理 #1587、#1589、#1627 的稳定性问题，并尽快合并 #1106、#1108 两个已就绪的 fix PR。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-09-02

---

## 1. 今日速览

过去24小时 Moltis 项目呈现**稳定修复节奏**，无新功能版本发布，但社区贡献活跃。共关闭 2 个 Issue、合并 2 个 PR，另有 2 个 PR 待审。整体活跃度中等，主要聚焦于 Docker 部署体验优化与 MCP 工具链诊断逻辑修复，项目稳定性持续加固。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的 PR 共计 2 条，主要集中在以下两个方向：

### 3.1 Docker 本地开发认证检测修复
- **PR #1249** — `fix(auth): let Docker loopback-only deployments count as local`
  - 修复了 Docker 默认网桥网络下 `is_local_connection()` 误判非本地连接的问题
  - 解决了 `auth_disabled` 在 Docker 容器中无法生效的 bug（关联 Issue #1112）
  - **推进程度**：直接改善本地开发体验，降低 Docker 部署入门门槛

### 3.2 MCP 服务器 Doctor 诊断逻辑修正
- **PR #1251** — `Fix doctor validation for streamable HTTP MCP servers`
  - 新增对 `streamable-http` 传输协议的规范识别与别名支持
  - 在报告成功前解析并验证远程服务器 URL
  - 将未解析的凭证占位符降级为信息性提示而非错误
  - **推进程度**：提升了 `moltis doctor` 的可用性，修复了 Issue #1250 报告的误报问题

---

## 4. 社区热点

### 高关注度 Issue/PR

| 项目 | 类型 | 标题 | 评论数 | 点赞数 | 链接 |
|------|------|------|--------|--------|------|
| #1253 | PR (待合并) | feat(reasoning): add max effort level | — | 0 | [链接](https://github.com/moltis-org/moltis/pull/1253) |
| #1252 | PR (待合并) | docs(docker): document the bind-mount permission fix for fresh deploys | — | 0 | [链接](https://github.com/moltis-org/moltis/pull/1252) |
| #1112 | Issue (已关闭) | Disabling auth doesn't seem to disable auth (Docker) | 1 | 0 | [链接](https://github.com/moltis-org/moltis/issues/1112) |
| #1250 | Issue (已关闭) | doctor treats working streamable-http MCP server as missing command | 0 | 0 | [链接](https://github.com/moltis-org/moltis/issues/1250) |

**热点分析**：
- **Issue #1112** 虽仅 1 条评论，但涉及 Docker 环境认证配置的核心痛点，已随 PR #1249 合并得到解决
- **PR #1253** 引入推理 effort 级别支持，反映用户对模型推理控制的持续需求，可能成为下一版本的亮点功能
- **PR #1252** 针对文档缺失的补充，说明 bind-mount 权限问题是新用户高频踩坑点

---

## 5. Bug 与稳定性

| 严重程度 | 问题描述 | Issue | 修复状态 | 链接 |
|----------|----------|-------|----------|------|
| 🟡 中 | Docker 容器中禁用认证无效，`is_local_connection()` 因网桥地址重写误判 | #1112 | ✅ 已修复 (PR #1249) | [链接](https://github.com/moltis-org/moltis/issues/1112) |
| 🟡 中 | `moltis doctor` 将正常工作的 streamable-http MCP 服务器误报为缺失命令 | #1250 | ✅ 已修复 (PR #1251) | [链接](https://github.com/moltis-org/moltis/issues/1250) |

**稳定性评估**：今日关闭的两个 Issue 均已被对应 PR 修复，无新增未解决 Bug，项目稳定性良好。

---

## 6. 功能请求与路线图信号

### 6.1 推理 Effort 级别控制
- **PR #1253** — 添加 `max` 推理努力级别支持
  - 在 `ReasoningEffort` schema 中新增 `max` 选项
  - 支持 `@reasoning-max` 模型后缀解析
  - 通过 OpenAI Codex Responses API 传递 max 级别，并对不支持的提供商进行 clamp
  - 在推理选择器、翻译和广播中暴露 Max 选项
  - **路线图信号**：反映用户对细粒度推理控制的持续需求，可能纳入下一功能版本

### 6.2 Docker 部署体验优化
- **PR #1252** — 文档补充 bind-mount 权限修复说明
  - 解决 `docker compose up` 初次部署时 SQLite 数据库文件权限问题
  - **路线图信号**：Docker 部署便利性是社区高频反馈点，文档完善是低成本的体验提升

---

## 7. 用户反馈摘要

| 用户痛点/场景 | 来源 | 情绪倾向 |
|---------------|------|----------|
| Docker 容器中禁用认证配置不生效，阻碍本地开发调试 | Issue #1112 | ❌ 不满意 |
| Doctor 诊断工具对 streamable-http MCP 服务器误报，影响工具链可信度 | Issue #1250 | ❌ 不满意 |
| 初次 Docker 部署时 bind-mount 权限问题导致启动失败 | PR #1252 关联 | ❌ 不满意 |
| 需要更细粒度的推理级别控制（如 max effort） | PR #1253 | ✅ 功能期待 |

**用户场景洞察**：
- **Docker 本地开发** 是高频使用场景，但网络配置和权限问题仍是主要摩擦点
- **MCP 工具链集成** 需求明确，用户对诊断工具的准确性要求较高
- **模型推理控制** 是进阶用户的需求，反映项目用户群体正在向专业场景扩展

---

## 8. 待处理积压

| 项目 | 类型 | 标题 | 创建时间 | 状态 | 链接 |
|------|------|------|----------|------|------|
| #1253 | PR | feat(reasoning): add max effort level | 2026-09-02 | 待合并 | [链接](https://github.com/moltis-org/moltis/pull/1253) |
| #1252 | PR | docs(docker): document the bind-mount permission fix for fresh deploys | 2026-09-01 | 待合并 | [链接](https://github.com/moltis-org/moltis/pull/1252) |

**维护者提醒**：
- PR #1253 和 #1252 已创建超过 1 天，建议尽快完成代码审查
- #1253 涉及核心功能变更，需重点验证多提供商兼容性
- #1252 为文档类 PR，可优先合并以缓解用户痛点

---

**项目健康度评分**：🟢 良好 — Bug 修复及时，社区贡献活跃，路线图清晰。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw (QwenPaw) 项目动态日报
**日期：2026-09-02**

---

## 1. 今日速览

过去24小时内，QwenPaw 项目保持较高活跃度：共处理 30 条 Issue（活跃 17 条、关闭 13 条）和 40 条 PR（待合并 19 条、已合并/关闭 21 条），并发布了 v2.2.0-beta.6 版本。今日社区反馈集中在 **cron 任务重复触发**、**自定义提供商兼容性**、**MCP 工具白名单未生效** 三个高频痛点，反映出 v2.2 beta 系列在调度稳定性和安全治理层面仍需打磨。同时，集成测试覆盖率冲刺取得显著进展（+617 测试用例，陈述覆盖率提升 10.61pp），项目整体健康度处于良性上升通道。

---

## 2. 版本发布

### v2.2.0-beta.6
- **链接**: https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.2.0-beta.6
- **关联发布验证 Issue**: [#7475](https://github.com/agentscope-ai/QwenPaw/issues/7475)

**关键变更**：
| 模块 | 内容 | 贡献者 |
|------|------|--------|
| desktop | 修复 ReMe entry-point 插件打包问题 | @jinliyl |
| console | 扩展单元测试 +617 个用例，陈述覆盖率 +10.61pp | @yutai78786 |

**迁移注意事项**：
- 合并 #7337 后，`ModelInfo.max_tokens` 已迁移至 `max_output_length`，自定义提供商配置需同步更新（参见 Issue #7474）
- 建议升级前备份 `~/.vizionpaw.secret/providers/custom/` 目录下的 provider 配置文件

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#7465](https://github.com/agentscope-ai/QwenPaw/pull/7465) | Fix | 标准化各 embedding 后端维度配置，修复 DashScope 配置持久化误判 |
| [#7452](https://github.com/agentscope-ai/QwenPaw/pull/7452) | Test | Console 单元测试扩展（+617 cases, +10.61pp） |
| [#7432](https://github.com/agentscope-ai/QwenPaw/pull/7432) | Fix | 修复 `~` 路径扩展问题，确保 `/api/agent-stats/llm-tool-trend` 统计完整性 |
| [#7329](https://github.com/agentscope-ai/QwenPaw/pull/7329) | Fix | MCP 会话 teardown 时中止挂起 RPC，恢复 stale `list_tools` |
| [#7330](https://github.com/agentscope-ai/QwenPaw/pull/7330) | Feat | 新增 Streamable-HTTP 双协议 MCP 客户端，兼容 MCP 2025/2026 版本 |
| [#7472](https://github.com/agentscope-ai/QwenPaw/pull/7472) | Fix | 修复 Tool Guard 中 shell 换行符绕过漏洞，提升安全治理 |
| [#7468](https://github.com/agentscope-ai/QwenPaw/pull/7468) | Fix | 调整 ReMe 启动顺序，避免无模型配置时 `ProviderError` 崩溃 |

### 待合并/关注 PR
- [#7485](https://github.com/agentscope-ai/QwenPaw/pull/7485) — 版本 bump 至 v2.2.0b7
- [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) — workspace 级 skill preload 配置
- [#7080](https://github.com/agentscope-ai/QwenPaw/pull/7080) — PowerContext 长期记忆后端（首提贡献）
- [#7482](https://github.com/agentscope-ai/QwenPaw/pull/7482) — Agent Kanban 中/英文本地化

---

## 4. 社区热点

| Issue | 主题 | 评论数 | 热度分析 |
|-------|------|--------|----------|
| [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | 主-agent+多子-agent 任务进度需主动询问 | 6 | 🔥 高 — 反映复杂 agent 编排场景下的 UX 盲区 |
| [#7480](https://github.com/agentscope-ai/QwenPaw/issues/7480) | cron 升级重启后非计划补发 + cancelled 任务通知缺失 | 2 | 🔥 高 — 多用户（b3/b6 均复现）确认的调度可靠性问题 |
| [#7476](https://github.com/agentscope-ai/QwenPaw/issues/7476) | misfire_grace 窗口内 cron 重复调度导致备份脚本执行两次 | 2 | 🔥 高 — 与 #7480 同根，影响生产备份链路 |
| [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | 危险指令易绕过安全守卫 | 4 | 🔥 高 — 安全类 Issue，需优先关注 |
| [#7431](https://github.com/agentscope-ai/QwenPaw/issues/7431) | codex 后端非流式下发导致空响应 | 2 | 中 — 第三方网关兼容性问题 |
| [#7470](https://github.com/agentscope-ai/QwenPaw/issues/7470) | MCP per-tool 白名单未在生产路径生效 | 1 | 中 — 安全治理缺陷 |
| [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) | A2A 协议支持计划咨询 | 1 | 中 — 路线图相关 |

**热点分析**：
- **cron 调度稳定性** 是今日最突出的社区诉求，至少两位独立用户（#7480, #7476）报告同类问题，且已在 b3/b6 双版本复现，建议纳入 v2.2.0b7 修复范围。
- **安全治理** 相关 Issue 持续增加（#7443 指令绕过、#7470 白名单失效、#7472 已合并的 shell 转义修复），反映用户对项目安全性的关注度提升。
- **A2A 协议支持** 被明确询问，结合架构文档已提及 MCP/A2A/ACP 统一 Driver 机制，社区期待官方排期。

---

## 5. Bug 与稳定性

### 严重级

| Issue | 描述 | 状态 | 关联 Fix PR |
|-------|------|------|-------------|
| [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | 危险指令易绕过安全守卫 | OPEN | — |
| [#7470](https://github.com/agentscope-ai/QwenPaw/issues/7470) | MCP per-tool 白名单未在生产路径强制执行 | OPEN | [#7473](https://github.com/agentscope-ai/QwenPaw/pull/7473)（仅 UI 修复，非后端） |
| [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | 自定义提供商加载失败（max_tokens → max_output_length 迁移后） | OPEN | 需确认是否有对应 fix PR |

### 中级

| Issue | 描述 | 状态 | 关联 Fix PR |
|-------|------|------|-------------|
| [#7464](https://github.com/agentscope-ai/QwenPaw/issues/7464) | Embedding index 重建始终报 "config unsaved" | ✅ CLOSED | [#7465](https://github.com/agentscope-ai/QwenPaw/pull/7465) |
| [#7446](https://github.com/agentscope-ai/QwenPaw/issues/7446) | ReMe 重建索引返回 500（ReMe instance is None） | ✅ CLOSED | [#7468](https://github.com/agentscope-ai/QwenPaw/pull/7468) |
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | ReMe 后台 embedding 任务失败（Dependency accessed before start） | OPEN | 与 #7468 相关，待验证 |
| [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | 主/子 agent 任务进度查询依赖用户主动询问 | OPEN | — |
| [#7481](https://github.com/agentscope-ai/QwenPaw/issues/7481) | macOS StdIO MCP spawn 重入 backend_guard 导致后端崩溃 | OPEN | — |
| [#7431](https://github.com/agentscope-ai/QwenPaw/issues/7431) | 火山方舟网关 + codex 0.144.x 产生空响应 | OPEN | — |
| [#7476](https://github.com/agentscope-ai/QwenPaw/issues/7476) | cron misfire_grace 窗口内重复调度 | OPEN | — |
| [#7480](https://github.com/agentscope-ai/QwenPaw/issues/7480) | 升级重启后 cron 非计划补发 | OPEN | — |

### 已修复 Bug
- [#7464](https://github.com/agentscope-ai/QwenPaw/issues/7464) → [#7465](https://github.com/agentscope-ai/QwenPaw/pull/7465)
- [#7446](https://github.com/agentscope-ai/QwenPaw/issues/7446) → [#7468](https://github.com/agentscope-ai/QwenPaw/pull/7468)
- [#7463](https://github.com/agentscope-ai/QwenPaw/issues/7463) (llama.cpp 加载 Spark-X2.5 GGUF 失败) → CLOSED（可能是配置问题，参见 #7459）

---

## 6. 功能请求与路线图信号

| Issue/PR | 诉求 | 路线图谱判断 |
|----------|------|--------------|
| [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) | A2A 协议支持计划 | 架构文档已提及 MCP/A2A/ACP 统一 Driver，社区期待官方排期；建议维护者回应 |
| [#7080](https://github.com/agentscope-ai/QwenPaw/pull/7080) | PowerContext 长期记忆后端 | 首提贡献者 PR，实现 `BaseMemoryManager` 接口；若合并将扩展记忆后端生态 |
| [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) | workspace 级 skill preload 配置 | 借鉴 Claude Code subagents 设计，支持受信任 skill 预加载；处于 Under Review |
| [#7482](https://github.com/agentscope-ai/QwenPaw/pull/7482) | Agent Kanban 中/英文本地化 | 跟随宿主语言设置，覆盖 board 列、操作、对话框等；低风险提示可纳入 b7 |
| [#7479](https://github.com/agentscope-ai/QwenPaw/issues/7479) | 消息频道拼写错误命令仍转发给 agent | 用户体验改进需求，建议加入 TODO |
| [#7455](https://github.com/agentscope-ai/QwenPaw/issues/7455) | 所有自带云端提供商支持停用 | ✅ 已关闭，功能已实现 |
| [#7461](https://github.com/agentscope-ai/QwenPaw/issues/7461) | 支持轮次内队列事件（mid-tool-execution 注入用户消息） | 高级功能请求，改变 agent 执行模型，需评估架构影响 |

---

## 7. 用户反馈摘要

### 痛点
1. **Agent 进度可见性不足** — 用户报告主/子 agent 架构下，任务执行时无中间状态反馈，需主动询问才能触发子 agent 状态查询（#7450）。gpt-sol 等复杂任务编排场景对此需求强烈。
2. **cron 调度可靠性存疑** — 升级重启后非计划补发（#7480）、misfire_grace 窗口内重复触发（#7476）均有用户实证，影响生产级定时任务（如每日备份）。
3. **自定义提供商迁移成本** — PR #7337 引入的 `max_tokens` → `max_output_length` 迁移未提供兼容层，导致自定义 provider 启动报错（#7474）。
4. **MCP 安全策略未完全落地** — per-tool 白名单在 Console UI 可见但生产路径未强制执行（#7470），用户担心安全策略形同虚设。
5. **macOS StdIO MCP 稳定性** — 调用 MCP 工具时可能重入 backend_guard 导致后端崩溃（#7481），Apple Silicon 用户受影响。

### 满意点
- 测试覆盖率冲刺成效显著（+617 cases, +10.61pp），用户/贡献者对质量保障可见度提升表示认可
- ReMe 启动顺序修复（#7468）解决了新安装无模型时的崩溃问题
- Streamable-HTTP 双协议 MCP 客户端（#7330）增强了与不同版本 MCP 服务端的兼容性

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建日期 | 积压天数 | 建议优先级 |
|----------|------|----------|----------|------------|
| [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) | Bug | 2026-09-01 | 1 | P1 — 复杂 agent 编排核心体验 |
| [#7480](https://github.com/agentscope-ai/QwenPaw/issues/7480) | Bug | 2026-09-02 | 0 | P1 — cron 可靠性直接影响生产用户 |
| [#7476](https://github.com/agentscope-ai/QwenPaw/issues/7476) | Bug | 2026-09-01 | 1 | P1 — 同根问题，建议合并处理 |
| [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | Bug | 2026-08-31 | 2 | P1 — 安全类 Issue |
| [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | Bug | 2026-09-01 | 1 | P2 — 自定义提供商兼容性 |
| [#7481](https://github.com/agentscope-ai/QwenPaw/issues/7481) | Bug | 2026-09-02 | 0

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw 项目动态日报
**日期：2026-09-02 | 数据来源：GitHub API**

---

## 1. 今日速览

今日 ZeptoClaw 项目活动以自动化依赖更新为主，无人为提交的 Issues 或 PR。过去24小时内完成 1 个 Dependabot PR 合并（#649），新增 1 个待审核依赖更新 PR（#658）。项目整体活跃度较低，处于日常维护阶段，无新功能开发或重要 Bug 修复动态。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

| PR | 状态 | 作者 | 说明 |
|---|---|---|---|
| [#649](https://github.com/qhkm/zeptoclaw/pull/649) | ✅ 已合并 | dependabot[bot] | Rust 基础镜像从 `1.95-slim-trixie` 升级至 `1.97-slim-trixie`，提升容器构建的安全性与编译性能 |
| [#658](https://github.com/qhkm/zeptoclaw/pull/658) | 🔄 待合并 | dependabot[bot] | Rust 基础镜像进一步升级至 `1.98-slim-trixie`，保持依赖链最新 |

**进展评估：** 项目依赖链持续跟踪 Rust 官方镜像更新，今日合并一个版本、待审一个版本，属于常规维护性推进，未涉及核心功能变更。

---

## 4. 社区热点

今日无人为提交的 Issues 或高互动 PR。现有活动均为 Dependabot 自动触发的依赖更新，无社区讨论焦点。

---

## 5. Bug 与稳定性

今日无 Bug 报告，无崩溃或回归问题记录。项目处于稳定维护状态。

---

## 6. 功能请求与路线图信号

今日无新功能请求。Dependabot 的 Rust 镜像更新反映项目对基础环境版本跟进的重视，但未见与核心功能演进相关的信号。

---

## 7. 用户反馈摘要

今日无用户评论或反馈。项目社区互动活跃度较低，暂无可提取的用户痛点或使用场景信息。

---

## 8. 待处理积压

| PR | 状态 | 创建日期 | 说明 |
|---|---|---|---|
| [#658](https://github.com/qhkm/zeptoclaw/pull/658) | 待合并 | 2026-09-01 | Rust 1.98 依赖更新，已创建但尚未合并，建议维护者尽快审核 |

---

## 项目健康度总结

| 维度 | 评级 | 说明 |
|---|---|---|
| 活跃度 | ⭐⭐☆☆☆ | 依赖 Bot 维护，无人工提交 |
| 维护响应 | ⭐⭐⭐☆☆ | Dependabot PR 合并及时（#649），但 #658 待处理 |
| 稳定性 | ⭐⭐⭐⭐☆ | 无 Bug 报告，依赖更新正常 |
| 社区参与 | ⭐☆☆☆☆ | 无 Issue/PR 讨论，社区互动低迷 |

**总体评估：** ZeptoClaw 当前处于低维护频率的稳定期，主要依赖自动化机制保持基础环境更新。建议维护者关注 #658 的合并进度，并考虑提升项目可见度以吸引更多社区贡献。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

⚠️ 摘要生成失败。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*