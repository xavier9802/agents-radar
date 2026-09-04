# OpenClaw 生态日报 2026-09-04

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-04 04:02 UTC

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



# OpenClaw 项目日报 — 2026-09-04

## 1. 今日速览

OpenClaw 项目今日维持**高活跃状态**，过去24小时 Issues 更新 500 条、PR 更新 500 条，新开/活跃 Issue 339 条，PR 待合并 415 条。新发布的 **v2026.9.1** 带来 Mermaid 图表渲染、从安装到对话的完整工作流优化等关键体验升级。社区反馈集中在 SQLite 内存索引膨胀、Codex 插件兼容性、Windows 升级异常等生产环境痛点，维护者团队同步推进了数十项修复与性能优化 PR，项目整体向前推进显著。

---

## 2. 版本发布

### v2026.9.1（2026-09-04）

**Highlights：**
- **Mermaid 图表全面渲染**：Mermaid 代码块现在可在 Control UI 及 macOS、iOS、Android 原生应用中渲染为图表，支持放大预览，移动端失败时提供重试能力（#134913, #135746, #135470, #135342）
- **从安装到对话的无缝工作流**：进一步优化从安装到首次对话的用户体验链路

**注意：** 本日同时报告 Windows 升级后 Gateway 无法启动的问题（#137813），涉及新增的 `--task-supervisor` 标志静默退出，建议 Windows 用户关注修复进度。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 主题 | 状态 |
|----|------|------|
| [#137863](https://github.com/openclaw/openclaw/pull/137863) | 修复 Slack 原生会话控制路由至所属运行 | 待审核 |
| [#137616](https://github.com/openclaw/openclaw/pull/137616) | 修复 Skills 文件监听器关闭后仍轮询的问题 | 待审核 |
| [#137882](https://github.com/openclaw/openclaw/pull/137882) | 修复文档翻译模型选择暴露隐私问题 | 等待作者 |
| [#136533](https://github.com/openclaw/openclaw/pull/136533) | 修复 Compaction 心跳会话忽略转录字节上限 | 需验证 |
| [#137777](https://github.com/openclaw/openclaw/pull/137777) | 修复 Harness 插件加载失败时模型会话中断 | 待审核 |
| [#137876](https://github.com/openclaw/openclaw/pull/137876) | 新增 Memory 存储用量展示与磁盘恢复指南 | 待审核 |

**进展评估：** 今日合并/关闭 85 条 PR，其中涵盖 Slack 路由、文件监听、隐私修复、会话管理、UI 体验等多个方向，项目核心稳定性与用户体验均有实质性推进。

---

## 4. 社区热点

### 高评论 Issue TOP 5

| # | 标题 | 评论 | 状态 | 热度 |
|---|------|------|------|------|
| [#94518](https://github.com/openclaw/openclaw/issues/94518) | DeepSeek 缓存命中率骤降至 <10%（边界感知缓存破坏前缀匹配） | 11 | ✅ 已关闭 | ⭐⭐⭐⭐⭐ |
| [#114612](https://github.com/openclaw/openclaw/issues/114612) | SQLite memory_index_chunks + embedding_cache 无保留策略，磁盘持续增长 | 11 | 🔓 开放 | ⭐⭐⭐⭐⭐ |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/Tool 子进程泄漏导致僵尸进程积累 | 10 | 🔓 开放 | ⭐⭐⭐⭐⭐ |
| [#96007](https://github.com/openclaw/openclaw/issues/96007) | Discord 内联错误后消息内容被截断 | 9 | 🔓 开放 | ⭐⭐⭐⭐ |
| [#110190](https://github.com/openclaw/openclaw/issues/110190) | 运行时上下文载体位置导致模型混淆与推理 Token 浪费 | 9 | 🔓 开放 | ⭐⭐⭐⭐ |

**热点分析：** 用户最关注的是**运行时稳定性**与**资源管理**——缓存命中率下降直接影响使用成本，SQLite 无界增长威胁生产部署，进程泄漏影响长期运行可靠性。DeepSeek 缓存问题（#94518）已关闭但反映社区对模型兼容性的高度敏感。

---

## 5. Bug 与稳定性

### P0 级紧急问题

| # | 标题 | 状态 | Fix PR |
|---|------|------|--------|
| [#137813](https://github.com/openclaw/openclaw/issues/137813) | **Windows Gateway 升级 2026.9.1 后无法启动** — `--task-supervisor` 标志静默退出 | 🔓 开放 | 无 |
| [#136203](https://github.com/openclaw/openclaw/issues/136203) | Windows de-DE 2026.8.2 升级后 Doctor 维护阻塞 | 🔓 开放 | 无 |
| [#134938](https://github.com/openclaw/openclaw/issues/134938) | `doctor --fix` 在 legacy exec-approvals 门控处死锁 | ✅ 已关闭 | 已修复 |
| [#107694](https://github.com/openclaw/openclaw/issues/107694) | Gateway 因严格启动迁移警告守卫无法启动 | ✅ 已关闭 | 已修复 |

### P1 级重要 Bug

| # | 标题 | 状态 | Fix PR |
|---|------|------|--------|
| [#94518](https://github.com/openclaw/openclaw/issues/94518) | DeepSeek 缓存命中率 <10% | ✅ 已关闭 | 已修复 |
| [#137710](https://github.com/openclaw/openclaw/issues/137710) | Native Codex 完成未唤醒 sessions_yield 父会话 | 🔓 开放 | 无 |
| [#127148](https://github.com/openclaw/openclaw/issues/127148) | Codex sessions.compact 获取第二个 app-server 导致冲突 | 🔓 开放 | 相关 PR #137030 |
| [#135347](https://github.com/openclaw/openclaw/issues/135347) | 强制内存重索引导致 DB 膨胀至 35GB，删除恢复破坏会话 | 🔓 开放 | 相关 PR #137876 |
| [#118185](https://github.com/openclaw/openclaw/issues/118185) | 单次 claude-cli 轮询被写入转录两次 | 🔓 开放 | 无 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 子进程泄漏导致僵尸积累与运行时退化 | 🔓 开放 | 无 |

### 回归问题（Regression）

| # | 标题 | 状态 |
|---|------|------|
| [#136183](https://github.com/openclaw/openclaw/issues/136183) | ssh 命令执行器挂起 — SIGTERM（2026.8.1 引入） | 🔓 开放 |
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite  corruption 在新重建 DB 中 15-24h 内复现 | 🔓 开放 |
| [#125640](https://github.com/openclaw/openclaw/issues/125640) | memory index 批次限制修复回归（#80226 未真正修复） | 🔓 开放 |

---

## 6. 功能请求与路线图信号

### 高优先级功能请求

| # | 标题 | 评论 | 状态 |
|---|------|------|------|
| [#72741](https://github.com/openclaw/openclaw/issues/72741) | 外部安全与护栏检查标准化接口 | 9 | 🔓 开放 |
| [#116473](https://github.com/openclaw/openclaw/issues/116473) | 操作者发起的跨 Agent 委托 `@A ask @B` 语法 | 5 | ✅ 已关闭 |
| [#122654](https://github.com/openclaw/openclaw/issues/122654) | 在 Control UI 管理共享 MCP OAuth | 4 | ✅ 已关闭 |
| [#137872](https://github.com/openclaw/openclaw/issues/137872) | 策略绑定 Prompt Hook 枚举授权工具名称 | 4 | 🔓 开放 |
| [#127208](https://github.com/openclaw/openclaw/issues/127208) | 添加一次性 `/followup` 命令 | 4 | 🔓 开放 |
| [#126781](https://github.com/openclaw/openclaw/issues/126781) | `/loop` 和 Automations 启动 Durable Lobster 工作流 | 5 | 🔓 开放 |
| [#112375](https://github.com/openclaw/openclaw/pull/112375) | Cron 调度 Shell 预检门控 — 无工作时跳过 LLM 调用 | 需验证 | 🔓 开放 |

**路线图信号：** 
- **外部安全接口标准化**（#72741）反映企业对 Agent 安全合规的需求
- **Cron Shell 预检**（#112375）是显著的效率优化方向，可减少不必要的模型调用成本
- **Durable Lobster 工作流**（#126781）显示对长运行任务的持久化需求增强

---

## 7. 用户反馈摘要

### 痛点集中区域

1. **生产稳定性担忧**
   - 僵尸进程积累（#97616）和 SQLite corruption（#126821）是长期存在的稳定性隐患
   - Windows 升级路径不稳定（#136203, #137813），影响生产部署信心

2. **成本与资源管理**
   - DeepSeek 缓存命中率骤降（#94518）直接增加 API 成本
   - SQLite 内存索引无界增长（#114612）威胁长期运行磁盘空间

3. **多平台一致性**
   - Discord 消息截断（#96007）、iMessage 回声缓存（PR #137834）、WhatsApp 崩溃（#125079）等渠道问题持续出现
   - Windows 平台体验明显落后于 macOS/Linux

4. **会话管理复杂性**
   - 运行时上下文位置导致模型混淆（#110190）
   - sessions_yield 未正确唤醒父会话（#137710）
   - 单次轮询被重复写入（#118185）

### 积极反馈
- v2026.9.1 的 Mermaid 图表渲染获得正面关注
- Memory 存储用量可视化（PR #137876）回应了用户对资源透明的需求
- UI 改进（PR #136736 多 Agent 头像显示、#137753 Inbox 自动化爆发时保持当前视图）提升可用性

---

## 8. 待处理积压

### 需维护者关注的 Issue

| # | 标题 | 创建时间 | 评论 | 标注 |
|---|------|----------|------|------|
| [#114612](https://github.com/openclaw/openclaw/issues/114612) | SQLite memory 表无界增长 | 2026-07-27 | 11 | diamonds lobster / needs-product-decision |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 子进程泄漏僵尸积累 | 2026-06-29 | 10 | silver shellfish / needs-maintainer-review |
| [#110190](https://github.com/openclaw/openclaw/issues/110190) | 运行时上下文位置导致模型混淆 | 2026-07-17 | 9 | diamonds lobster / needs-product-decision |
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite corruption 复现 | 2026-08-20 | 7 | silver shellfish / needs-live-repro |
| [#123327](https://github.com/openclaw/openclaw/issues/123327) | WAL checkpoint 覆盖 SQLite page 1 | 2026-08-13 | 5 | gold shrimp / P0 |
| [#137813](https://github.com/openclaw/openclaw/issues/137813) | Windows Gateway 无法启动 | 2026-09-04 | 4 | silver shellfish / P0 |

### 需维护者关注的 PR

| # | 标题 | 状态 |
|---|------|------|
| [#112375](https://github.com/openclaw/openclaw/pull/112375) | Cron Shell 预检门控 | 📣 需验证 |
| [#136533](https://github.com/openclaw/openclaw/pull/136533) | Compaction 心跳会话修复 | 📣 需验证 |
| [#137882](https://github.com/openclaw/openclaw/pull/137882) | 文档翻译隐私修复 | ⏳ 等待作者 |

---

**项目健康度评估：** 整体活跃度高，Issue/PR 流动顺畅，核心维护者响应积极。主要风险集中在 **SQLite 稳定性** 和 **Windows 平台升级路径**，建议优先处理 P0 级问题并建立更完善的升级测试覆盖。

---

## 横向生态对比



# 2026-09-04 个人 AI 助手/自主智能体开源生态横向对比分析报告

---

## 1. 生态全景

2026年9月，个人 AI 助手开源生态呈现**"头部高吞吐迭代、垂直场景差异化深耕"**的格局。OpenClaw、Hermes Agent、ZeroClaw、CoPaw 四强领跑，日活跃 Issue/PR 更新均超 50 条，社区吞吐量进入成熟期；NanoBot、IronClaw、LobsterAI 处于快速迭代期，聚焦 WebUI 稳定性与多端体验；PicoClaw、NanoClaw 等中型项目以垂直渠道优化和架构重构为主。安全治理（沙箱策略、权限模型）和会话持久化（ACP/Code 会话连续性）成为跨项目的共性技术方向。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | Release | 合并率 | 健康度 |
|------|-------------|-----------|---------|--------|--------|
| **OpenClaw** | 339 新/活跃 | 415 待合并 | ✅ v2026.9.1 | ~17% (85/500) | 🟢 高活跃，核心稳定推进 |
| **Hermes Agent** | 49 活跃 | 47 待合并 | ❌ 无 | ~6% (3/50) | 🟢 高活跃，深度 bug 修复 |
| **ZeroClaw** | 50 | 50 | ❌ 无 | ~2% (1/50) | 🟢 高强度，架构治理密集 |
| **CoPaw** | 27 (19新/8关) | 36 (21待/15合) | ❌ 无 | ~42% (15/36) | 🟢 高活跃，安全响应快 |
| **NanoBot** | 4 (1关) | 25 (14合/11待) | ❌ 无 | **56%** | 🟢 高吞吐，稳定性优先 |
| **IronClaw** | 11 | 18 | ❌ 无 | ~56% (10/18) | 🟢 中高强度，技术债清理 |
| **LobsterAI** | 6 | 15 | ❌ 无 (v2026.8.31已发) | ~67% (10/15) | 🟡 稳定迭代，体验打磨 |
| **PicoClaw** | 6 | 8 | ❌ 无 | ~12% (1/8) | 🟡 中等活跃，依赖维护 |
| **NanoClaw** | 5 (4新) | 23 (20待/3合) | ❌ 无 | ~13% (3/23) | 🟡 中高活跃，重构推进中 |
| NullClaw | 0 | 0 | — | — | ⚪ 无活动 |
| Moltis | 0 | 0 | — | — | ⚪ 无活动 |
| ZeptoClaw | 0 | 0 | — | — | ⚪ 无活动 |

---

## 3. OpenClaw 在生态中的定位

**生态位**：OpenClaw 是个人 AI 助手开源生态的**标杆项目**，社区规模最大（日 500+ 条 Issue/PR 流动）、功能覆盖最全（CLI/Gateway/Desktop/Mobile 全平台）、插件生态最丰富（Slack/Discord/iMessage/WhatsApp 等十余渠道）。

**核心优势**：
- **版本节奏稳定**：v2026.9.1 两周内迭代，Mermaid 图表渲染等体验升级快速落地
- **生产级问题响应**：SQLite 内存膨胀、Windows 升级路径、Codex 兼容性等痛点均有 PR 跟进
- **路线图清晰**：外部安全接口标准化、Cron 预检优化、Durable Lobster 工作流等方向明确

**技术路线差异**：
| 维度 | OpenClaw | 竞品对比 |
|------|----------|----------|
| 插件架构 | Skills + MCP + Plugin 三层 | Hermes: 插件钩子系统；ZeroClaw: Provider 合约标准化 |
| 会话持久化 | SQLite + 内存索引 | NanoBot: Gateway 会话恢复；CoPaw: context compaction |
| 多端覆盖 | CLI/Gateway/Desktop/Mobile (macOS/iOS/Android) | LobsterAI: 桌面端优先；PicoClaw: 轻量部署 |
| 安全治理 | Doctor 维护工具 + exec-approvals | CoPaw: CRITICAL 安全规则；ZeroClaw: RFC 沙箱策略 |

**社区规模**：OpenClaw Issue 评论数 TOP5 均在 9-11 条，NanoBot/Hermes/CoPaw 高评论 Issue 在 6-11 条，反映 OpenClaw 社区讨论密度最高，问题透明度最好。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **会话持久化与恢复** | OpenClaw, NanoBot, Hermes, ZeroClaw | NanoBot: Gateway 重启后 WebUI 卡死（#5512）；ZeroClaw: ACP 会话中断丢失上下文（#10197）；Hermes: 多 profile 状态竞争（#102526） |
| **安全治理与权限模型** | OpenClaw, Hermes, CoPaw, ZeroClaw | CoPaw: 沙箱突破（#7511）、CRITICAL 规则绕过（#7496）；Hermes: shell hooks 静默失效（#69825）；ZeroClaw: RFC #6996 细粒度沙箱策略 |
| **多平台一致性** | OpenClaw, NanoBot, PicoClaw, LobsterAI | OpenClaw: Windows 升级路径不稳定（#137813）；PicoClaw: QQ 频道 401 授权失效（#3349）；LobsterAI: Windows DPI/控制台窗口适配 |
| **成本与资源管理** | OpenClaw, NanoBot | OpenClaw: DeepSeek 缓存命中率骤降（#94518）、SQLite 无界增长（#114612）；NanoBot: Context Reuse 可视化（#5649） |
| **渠道稳定性** | OpenClaw, NanoBot, Hermes, PicoClaw, ZeroClaw | OpenClaw: Discord 消息截断（#96007）；NanoBot: Matrix 流交付失败（#5637）；Hermes: 多 profile Telegram 路由错误（#102635） |
| **架构标准化** | ZeroClaw, NanoClaw, IronClaw | ZeroClaw: Provider 合约重构；NanoClaw: Provider 合约系列 PR #3581-#3591；IronClaw: TypeScript 类型化清理 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构特征 |
|------|----------|----------|--------------|
| **OpenClaw** | 全平台 AI 助手，深度插件生态 | 个人用户、开发者、企业 | 三层插件架构（Skills/MCP/Plugin），SQLite 持久化，Doctor 维护工具 |
| **Hermes Agent** | Desktop-first，多 profile 管理，安全钩子系统 | 重度桌面用户、安全敏感用户 | 插件钩子（outbound-send/destructive-command/tenant guards），desktop keychain 加密 |
| **ZeroClaw** | 安全策略 RFC 驱动，ACP/Code 会话持久化 | 架构研究者、安全合规需求 | Provider 合约标准化，RFC 治理流程，细粒度沙箱策略 |
| **CoPaw** | 多租户 Hub，安全治理响应快 | 团队协作、组织部署 | 租户隔离，CRITICAL 安全规则引擎，移动端适配 |
| **NanoBot** | WebUI 稳定性，快速 bug 修复 | 生产环境用户 | 高合并率（56%），Gateway 会话恢复优先 |
| **IronClaw** | TypeScript 类型化，Agent Loop 性能优化 | 代码质量敏感、性能优化需求 | Reborn 架构，text_delta 增量推送优化，prompt budget 动态推导 |
| **LobsterAI** | 桌面端体验，Windows 适配 | Windows 用户、国内用户 | Electron 桌面应用，安装器修复，IM 多 Bot 卡片优化 |
| **PicoClaw** | 轻量部署，多渠道适配 | 资源受限环境、国内用户 | botgo/resty 依赖管理，QQ/Slack/LINE 渠道维护 |
| **NanoClaw** | Provider 合约重构，容器侧能力 | 插件开发者、容器部署用户 | Provider 合约系列化，语音转录 V2 容器化处理 |

---

## 6. 社区热度与成熟度分层

```
┌─────────────────────────────────────────────────────────────┐
│ 第一梯队：高活跃成熟期（日 50+ Issue/PR）                    │
│  OpenClaw · Hermes Agent · ZeroClaw · CoPaw                │
│  特征：版本节奏稳定，安全响应快，路线图清晰                   │
├─────────────────────────────────────────────────────────────┤
│ 第二梯队：快速迭代期（日 20-50 Issue/PR）                    │
│  NanoBot · IronClaw · LobsterAI                             │
│  特征：合并率高（50%+），bug 修复为主，体验打磨               │
├─────────────────────────────────────────────────────────────┤
│ 第三梯队：垂直深耕期（日 5-20 Issue/PR）                     │
│  PicoClaw · NanoClaw                                        │
│  特征：渠道优化、架构重构、依赖维护                         │
├─────────────────────────────────────────────────────────────┤
│ 第四梯队：休眠/低频期                                       │
│  NullClaw · Moltis · ZeptoClaw                              │
│  特征：24h 无活动，可能进入维护或转型阶段                   │
└─────────────────────────────────────────────────────────────┘
```

**质量巩固信号**：
- **OpenClaw**：SQLite corruption、进程泄漏等长期稳定性问题进入治理阶段
- **IronClaw**：TypeScript 类型化收尾，技术债清理进入尾声
- **CoPaw**：安全规则 #7496 当日响应 PR #7525，治理机制成熟
- **ZeroClaw**：RFC 治理流程制度化（#8692 维护者决策队列）

---

## 7. 值得关注的趋势信号

### 7.1 安全治理从"被动修复"转向"主动 RFC 治理"
- **ZeroClaw**：RFC #6996（沙箱策略）23 条评论，#8692 维护者决策队列制度化
- **CoPaw**：沙箱突破（#7511）当日触发 CRITICAL 规则修复（#7525）
- **Hermes**：shell hooks 静默失效（#69825）被标记为安全隐患，安全审计意识提升
- **启示**：AI 智能体安全从"打补丁"进入"架构治理"阶段，建议开发者关注 RFC 流程和安全规则引擎建设

### 7.2 会话持久化成为生产部署核心瓶颈
- **NanoBot**：Gateway 重启后 WebUI 卡死（#5512）高频反馈
- **ZeroClaw**：ACP 中断轮次持久化（#10197）、JSONL 会话文件判定（#9857）
- **OpenClaw**：sessions_yield 未唤醒父会话（#137710）
- **启示**：长会话连续性、中断恢复能力是生产环境刚需，建议优先保障会话状态机稳定性

### 7.3 Provider 合约标准化加速
- **NanoClaw**：Provider 合约系列 PR #3581-#3591 系统化重构
- **ZeroClaw**：Claude Fable、Codex、OpenCode 三大 Provider 标准化
- **IronClaw**：TypeScript 类型化覆盖生产组件（#8038-#8039）
- **启示**：插件/Provider 接口标准化降低生态碎片化，建议新入局者关注合约设计

### 7.4 多端一致性仍是痛点
- **OpenClaw**：Windows 升级路径不稳定（#137813），Linux/macOS 体验领先
- **LobsterAI**：Windows DPI/控制台窗口适配持续投入
- **PicoClaw**：QQ 频道授权失效（#3349）反映国内渠道维护成本高
- **启示**：跨平台一致性需要投入专项测试覆盖，建议建立升级回归测试流程

### 7.5 成本透明化需求凸显
- **NanoBot**：Context Reuse 可视化 PR #5649（token 用量堆叠条形图）
- **OpenClaw**：DeepSeek 缓存命中率骤降（#94518）直接增加 API 成本
- **IronClaw**：prompt budget 动态推导（#8053）避免窗口超支
- **启示**：用户对 API 成本可控性敏感度提升，成本可视化工具将成为差异化功能

---

**总结**：2026 年 9 月，个人 AI 助手开源生态进入**"安全治理制度化、会话持久化工程化、Provider 合约标准化"**的成熟期。OpenClaw 作为标杆保持高吞吐迭代，CoPaw/ZeroClaw 在安全治理和 RFC 流程上领先，NanoBot/IronClaw 以高合并率推进稳定性，LobsterAI/PicoClaw 聚焦垂直场景体验。建议开发者关注安全策略 RFC、会话状态机设计和 Provider 合约接口三个方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-09-04

---

## 1. 今日速览

过去 24 小时内 NanoBot 项目保持高度活跃：**25 条 PR 更新**（14 条已合并/关闭，11 条待合并），**4 条 Issue 更新**（1 条关闭）。项目整体呈现**高吞吐、以 WebUI 修复为主**的态势，核心贡献者（chengyongru、yaoruiquan、Shizoqua 等）多线并行推进 WebUI、Channel、Provider 三端的 bug 修复与功能完善。无新版本发布，但多个 P2 优先级 bug 已被合入主分支，项目稳定性在持续积累性改善中。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

过去 24 小时共**14 条 PR 被关闭/合并**，涵盖 WebUI、Channel、Provider、SDK 四个维度，项目整体向前推进约 **5–6 个高优先级 bug 修复**：

| PR | 状态 | 主题 | 推进意义 |
|---|---|---|---|
| [#5514](https://github.com/HKUDS/nanobot/pull/5514) | ✅ CLOSED | 修复 Gateway 重连后 WebUI 卡死问题 | 解决用户反复反馈的会话挂起痛点 |
| [#5650](https://github.com/HKUDS/nanobot/pull/5650) | ✅ CLOSED | 保持 Hero 模型预设 | 完善会话创建体验一致性 |
| [#5334](https://github.com/HKUDS/nanobot/pull/5334) | ✅ CLOSED | 修复消息分割时缩进丢失 | Signal 频道消息质量改善 |
| [#5637](https://github.com/HKUDS/nanobot/pull/5637) | ✅ CLOSED | Matrix 流交付失败传播修复 | 提升 Matrix 频道可靠性 |
| [#5646](https://github.com/HKUDS/nanobot/pull/5646) | ✅ CLOSED | 语言选择器仅显示原生名称 | 国际化体验优化 |
| [#5385](https://github.com/HKUDS/nanobot/pull/5385) | ✅ CLOSED | Element SAS 验证流程补全 | Matrix 安全配对功能完整化 |
| [#5413](https://github.com/HKUDS/nanobot/pull/5413) | ✅ CLOSED | LLM Provider 异常时 fallback 策略生效 | 提升多 Provider 容错能力 |
| [#5472](https://github.com/HKUDS/nanobot/pull/5472) | ✅ CLOSED | Signal 通配符白名单支持 | 频道安全性增强 |
| [#5515](https://github.com/HKUDS/nanobot/pull/5515) | ✅ CLOSED | 观察 session reply timeout 任务失败 | 后台任务稳定性改善 |
| [#5629](https://github.com/HKUDS/nanobot/pull/5629) | ✅ CLOSED | tool_hints 对普通值应用 max_length | 输出截断一致性修复 |
| [#5635](https://github.com/HKUDS/nanobot/pull/5635) | ✅ CLOSED | 流关闭时保留队列事件 | SDK 事件完整性修复 |
| [#5632](https://github.com/HKUDS/nanobot/pull/5632) | ✅ CLOSED | Codex prompt cache affinity 保持 | Codex Provider 性能优化 |

> **综合评估**：14 条合并 PR 中 10 条为 bug fix，占比 71%，反映出当前阶段以**稳定性修复**为优先，符合项目从功能建设期向稳定期过渡的特征。

---

## 4. 社区热点

### 🔥 高关注 Issue / PR

**[#5644](https://github.com/HKUDS/nanobot/issues/5644) — Channel Locale Registry 并发 Bug（#5651 正在修复）**
- 并发加载两个 locale 时，`en` 等语言会被覆盖丢失
- 根因：`loadChannelLocale()` 在 `await` 前捕获 Map 引用，导致并发写入丢失
- PR [#5651](https://github.com/HKUDS/nanobot/pull/5651) 已提交，预计近期合并
- **背后诉求**：国际化多语言同时加载场景的用户体验保障

**[#5512](https://github.com/HKUDS/nanobot/issues/5512) — Gateway 重启后 WebUI 卡死（已修复）**
- 前端持续显示 spinning 状态，`goal_status: idle` 推送丢失
- PR [#5514](https://github.com/HKUDS/nanobot/pull/5514) 已合入，根因已定位：`useNanobotStream` 未订阅 `onRunStatus` 事件
- **背后诉求**：服务重启后的会话状态恢复是生产环境高频场景

**[#5649](https://github.com/HKUDS/nanobot/pull/5649) — Per-Request Context Reuse 可视化（Feature）**
- 将 token 用量从每条 assistant message 移至 composer popover
- 以百分比 + 堆叠条形图展示每次模型请求的上下文复用率
- **背后诉求**：用户对 API 成本透明度和上下文管理有强烈可视化需求

**[#5620](https://github.com/HKUDS/nanobot/pull/5620) — Cron 可配置投递与批量归档（Feature）**
- 支持 per-cron 结果投递目标、批量归档生命周期状态
- **背后诉求**：定时任务功能趋于成熟，用户需要更细粒度的管理控制

---

## 5. Bug 与稳定性

按严重程度排列（今日新增）：

| 级别 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 P2 | [#5644](https://github.com/HKUDS/nanobot/issues/5644) | Channel locale 并发丢失，多语言环境受影响 | [#5651](https://github.com/HKUDS/nanobot/pull/5651) [OPEN] |
| 🟡 P2 | [#5647](https://github.com/HKUDS/nanobot/issues/5647) | frontend envelope 缺少 webui 标识时 session title 不生成 | [#5648](https://github.com/HKUDS/nanobot/pull/5648) [OPEN] |
| 🟡 P2 | [#5645](https://github.com/HKUDS/nanobot/issues/5645) | 0.3.0 默认缺失 Current Time runtime context（文档与行为不一致） | 暂无 |

> **历史 Bug 今日状态**：[#5512](https://github.com/HKUDS/nanobot/issues/5512)（Gateway 重启后 WebUI 卡死）已通过 [#5514](https://github.com/HKUDS/nanobot/pull/5514) 合入修复。

**稳定性信号**：今日 3 个 open Issue 均为 P2 级别，无 P0/P1 崩溃类 bug 报告，整体稳定性在可控范围内。

---

## 6. 功能请求与路线图信号

| 功能方向 | 相关 PR/Issue | 纳入下一版本可能性 |
|---|---|---|
| **Cron 增强**：可配置投递目标 + 批量归档 | [#5620](https://github.com/HKUDS/nanobot/pull/5620) | ⭐⭐⭐ 高 — PR 已进入 review，文档完善后大概率纳入 |
| **Context Reuse 可视化** | [#5649](https://github.com/HKUDS/nanobot/pull/5649) | ⭐⭐ 中 — 功能完整但 UI 交互细节待打磨 |
| **Model Retry Status 暴露** | [#5504](https://github.com/HKUDS/nanobot/pull/5504) | ⭐⭐ 中 — 已在 WebUI/TUI 双端渲染 |
| **Codex OAuth 持久化** | [#5446](https://github.com/HKUDS/nanobot/pull/5446) | ⭐⭐⭐ 高 — 修复关键可用性缺陷，冲突待解 |
| **iOS PWA 体验修复** | [#5641](https://github.com/HKUDS/nanobot/pull/5641) | ⭐⭐⭐ 高 — 移动端覆盖率提升的战略方向 |

---

## 7. 用户反馈摘要

**痛点：**
- **Gateway 重启后会话卡死**（[#5512](https://github.com/HKUDS/nanobot/issues/5512)）：生产环境中 Gateway 维护重启频繁，用户对此类状态残留容忍度低，已催生出固定修复。
- **locale 并发丢失**（[#5644](https://github.com/HKUDS/nanobot/issues/5644)）：多语言同时加载时部分 locale 被静默覆盖，用户无报错感知，发现成本高。
- **Current Time context 行为回退**（[#5645](https://github.com/HKUDS/nanobot/issues/5645)）：0.3.0 升级后行为与 0.2.2 及文档不一致，用户期望向后兼容。
- **iOS PWA 交互异常**（[#5641](https://github.com/HKUDS/nanobot/pull/5641)）：首次 tap 被吞、status bar 样式问题，移动端体验直接影响用户留存。

**满意点：**
- Hero model preset 在会话创建后保持不变（[#5650](https://github.com/HKUDS/nanobot/pull/5650)），用户反馈正向。
- 语言选择器改用原生名称显示（[#5646](https://github.com/HKUDS/nanobot/pull/5646)），减少对英语的依赖。

---

## 8. 待处理积压

| 类型 | 编号 | 描述 | 建议关注 |
|---|---|---|---|
| 🔴 待合并 PR | [#5651](https://github.com/HKUDS/nanobot/pull/5651) | 修复 locale 并发丢失，阻塞 #5644 | 应优先合并 |
| 🔴 待合并 PR | [#5648](https://github.com/HKUDS/nanobot/pull/5648) | 修复 session title 生成条件，解决 #5647 | 应优先合并 |
| 🟡 待处理 Issue | [#5645](https://github.com/HKUDS/nanobot/issues/5645) | Current Time runtime context 缺失，无 fix PR | 建议维护者响应或标注优先级 |
| 🟡 待合并 PR | [#5446](https://github.com/HKUDS/nanobot/pull/5446) | Codex OAuth token 持久化，标注 conflict | 需解决冲突后合并 |
| 🟢 进行中 PR | [#5641](https://github.com/HKUDS/nanobot/pull/5641) | iOS PWA 三项修复 | 移动端用户增长后价值凸显 |
| 🟢 进行中 PR | [#5639](https://github.com/HKUDS/nanobot/pull/5639) | Session labels、TUI streaming、pairing prompts 综合修复 | 涉及 OpenTUI 版本升级，需验证兼容性 |

---

**项目健康度总结**：NanoBot 在过去 24 小时展现出**高合并率（56%）**和**清晰的 bug 修复节奏**，WebUI 稳定性是当前首要攻坚方向。3 个 open Issue 均已有对应或待对应 PR，积压可控。建议维护者优先处理 #5651 和 #5648 两个阻塞性修复，并尽快响应 #5645 的状态更新。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-09-04

## 1. 今日速览

项目今日保持**高活跃度**：过去 24 小时内共 50 条 Issue 更新（49 活跃）、50 条 PR 更新（47 待合并），无新版本发布。开发重心集中在两个方向：一是修复 `hermes serve`/`dashboard` 命令跳过插件发现导致 shell hooks 和插件钩子不生效的深层 bug；二是应对多 profile Desktop 场景下的状态竞争、媒体路径失效等稳定性问题。整体项目健康度良好，大量 P1/P2 级 Bug 均有对应 PR 跟进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日重点合并/关闭的 PR（3 条）

- **#77157** [CLOSED] `fix(search): zero-match probes fall back to grep; native paths for rg on Windows`  
  修复 Windows 原生路径边界问题，配合 `MSYS_NO_PATHCONV` 保留 MSYS 安全处理，对 Windows 用户搜索能力有直接提升。  
  🔗 [PR #77157](https://github.com/NousResearch/hermes-agent/pull/77157)

- **#99490** [OPEN] `fix(security): make desktop secret storage secure by default`  
  将桌面端密钥存储默认改为 OS keychain 加密；非法/重复存储策略 fail-closed；迁移过程 crash-consistent。显著提升本地凭证安全基线。  
  🔗 [PR #99490](https://github.com/NousResearch/hermes-agent/pull/99490)

- **#31003** [OPEN] `fix(tools): reject redacted-secret placeholders in write_file / patch input`  
  修复安全边界：当 `security.redact_secrets: true` 时，写入工具拒绝包含脱敏占位符（如 `sk-exa...hars`、`PASSWORD=...`）的内容，防止敏感值回写。  
  🔗 [PR #31003](https://github.com/NousResearch/hermes-agent/pull/31003)

### 其他重要待合并 PR

| PR | 类型 | 摘要 |
|---|---|---|
| #102655 | fix | 修复 systemd 249 拒绝 `OOMPolicy=kill` 导致 cron 全部失败 |
| #102654 | fix | TTS 不再静默截断长回复（默认 max_chars 从 4000 移除） |
| #102627 | fix | 修复 cron heartbeat fence 竞争误判为 ownership loss |
| #102646 | fix | 防止 sentinel-only 流被持久化为最终回答 |
| #102647 | fix | 修复多 profile 场景下后台任务路由到错误 Telegram bot |
| #102651 | fix | 将 MEDIA 临时路径暂存到持久缓存，修复 Desktop 附件丢失 |
| #102650 | feat | 新增 `hermes sessions reset-store` owner-only 恢复命令 |
| #102649 | fix | 修复子 Agent 委托 fallback_providers 解析问题 |
| #102645 | fix | 修复压缩器 lazy 路径忽略自定义 provider context_length |
| #102538 | fix | 使 CLI cron 任务与调用方进程解耦，防止死亡调用方残留未知状态 |
| #102624 | fix | 修复 `hermes update` 时 SQLite WAL 重置因模块缺失失败 |
| #100865 | fix | 使持久化 Browser Use daemon 对孤儿回收器可见 |
| #102640 | fix | 修复 Codex 跨 turn 重放时 call_id 重复 |

项目整体向前推进：本次迭代重点修复了 **cron 系统健壮性**、**Desktop 多 profile 状态隔离**、**TTS/媒体路径体验** 三大块，并强化了安全边界。

---

## 4. 社区热点

### 讨论最活跃的 Issue

**#96692 — Unified slash-command registry and execution contract**（11 评论，P3）  
🔗 [Issue #96692](https://github.com/NousResearch/hermes-agent/issues/96692)  
核心诉求：Hermes 需要在所有产品表面（CLI、Gateway、TUI、Desktop、插件、Bundles）实现**一个版本化的斜杠命令目录 + 一个解析器 + 一个调用/结果契约**。这是一个架构级规范提案，涉及面广，是当前评论数最高的 Issue。

**#69825 — serve command never registers shell hooks**（7 评论，P2）  
🔗 [Issue #69825](https://github.com/NousResearch/hermes-agent/issues/69825)  
用户配置了 `config.yaml` 中的 shell hooks，`hermes hooks list/test` 正常，但 Desktop 实际聊天时 hooks 从不触发。根本原因：`serve` 命令跳过了 hooks 注册。已有多个关联 Issue（#102504、#102592）从不同侧面印证此问题，社区关注度高。

**#94726 — Desktop Bot Mode 全量 Bug 追踪**（6 评论，P2）  
🔗 [Issue #94726](https://github.com/NousResearch/hermes-agent/issues/94726)  
维护者整理的 umbrella tracker，涵盖 ~80 个 open items，按 bug 类别分组。反映 Bot Mode 在 Desktop/Gateway/SDK 接缝处存在系统性质量问题，是后续清理的重点。

---

## 5. Bug 与稳定性

按严重程度排列：

### 🔴 P0 / P1

| Issue | 描述 | Fix PR |
|---|---|---|
| [#102574](https://github.com/NousResearch/hermes-agent/issues/102574) | `PeriodicScheduler` 共享调度器一个回调阻塞会卡住所有 safety timer（turn-liveness、fire/turn lease、heartbeat） | 无 |
| [#102486](https://github.com/NousResearch/hermes-agent/issues/102486) | systemd 249 拒绝 `OOMPolicy=kill` 导致所有 cron worker 启动失败 | #102655 |
| [#102526](https://github.com/NousResearch/hermes-agent/issues/102526) | Desktop Bots 面板点击 Hermes 默认 profile 打开的是另一个 profile 的 chat（`HERMES_HOME` 竞争） | 无 |
| [#93817](https://github.com/NousResearch/hermes-agent/issues/93817) | `Reasoning Blocks: off` 时 Desktop 仍输出全部 thinking + tool calls，使界面不可用 | 无 |
| [#102194](https://github.com/NousResearch/hermes-agent/issues/102194) | CLI 路径不持久化 `api_content` sidecar，每 turn 第一次 API 调用丢失 prompt cache | 无 |

### 🟡 P2

| Issue | 描述 | Fix PR |
|---|---|---|
| [#69825](https://github.com/NousResearch/hermes-agent/issues/69825) | `serve` 命令不注册 shell hooks | #102504（关联） |
| [#100858](https://github.com/NousResearch/hermes-agent/issues/100858) | auxiliary vision custom provider 发送 `no-key-required` 导致 401 | #67055 |
| [#76602](https://github.com/NousResearch/hermes-agent/issues/76602) | auxiliary vision 丢失 api_key | #67055 |
| [#101318](https://github.com/NousResearch/hermes-agent/issues/101318) | macOS Desktop composer 拖拽过灵敏，无关闭选项 | 无 |
| [#70422](https://github.com/NousResearch/hermes-agent/issues/70422) | 选中文本时意外触发 composer detach | 无 |
| [#98645](https://github.com/NousResearch/hermes-agent/issues/98645) | `clarify` 工具卡片渲染空白，10 分钟后超时 | 无 |
| [#100855](https://github.com/NousResearch/hermes-agent/issues/100855) | browser daemon 对孤儿回收器不可见，跨 gateway 重启存活 47h | #100865 |
| [#100381](https://github.com/NousResearch/hermes-agent/issues/100381) | `codex_app_server_auto=hermes` 导致压缩在错误阈值触发 | 无 |
| [#101091](https://github.com/NousResearch/hermes-agent/issues/101091) | Desktop 接受不匹配的 provider/model 对，注入错误分组 | 无 |
| [#100870](https://github.com/NousResearch/hermes-agent/issues/100870) | Docker 后端 remote kernel 生成失败，brace group rewriter 缺失分隔符 | 无 |
| [#97296](https://github.com/NousResearch/hermes-agent/issues/97296) | macOS 27 kanban dispatcher fork 导致 gateway SIGSEGV | 无 |
| [#102635](https://github.com/NousResearch/hermes-agent/issues/102635) | 多 profile Telegram 后台任务路由错误 | #102647 |

### 🟢 P3

| Issue | 描述 |
|---|---|
| [#15779](https://github.com/NousResearch/hermes-agent/issues/15779) | `/model` 切换到 named custom provider 时忽略 `context_length`（已关闭） |
| [#102642](https://github.com/NousResearch/hermes-agent/issues/102642) | Windows Studio 群聊间歇性 WinError 10060 超时 |
| [#102057](https://github.com/NousResearch/hermes-agent/issues/102057) | Windows Studio Agent Bridge 冷启动竞态 1s 超时 |
| [#77409](https://github.com/NousResearch/hermes-agent/issues/77409) | Desktop UI 测试 React.act undefined（React 19.1+） |

---

## 6. 功能请求与路线图信号

| Issue | 需求 | 评估 |
|---|---|---|
| [#96692](https://github.com/NousResearch/hermes-agent/issues/96692) | 统一斜杠命令注册表和执行契约 | **高优先级路线图信号** — 跨表面一致性规范，评论量最高，预计影响后续所有产品形态 |
| [#77952](https://github.com/NousResearch/hermes-agent/issues/77952) | 切换 profile 时恢复上次选中的 session | 合理 UX 改进，低风险提示小 |
| [#102597](https://github.com/NousResearch/hermes-agent/issues/102597) | All-profiles 会话列表显示 per-profile 标记 | 多 profile 用户痛点，建议纳入 |
| [#102643](https://github.com/NousResearch/hermes-agent/issues/102643) | 斜杠命令 description 国际化（i18n） | 社区贡献型需求，扩展 `CommandDef.description` 为 dict |
| [#102582](https://github.com/NousResearch/hermes-agent/issues/102582) | `hermes moa configure` 暴露 per-slot reasoning effort | MoA 高级功能完善，已有 schema 支持 |
| [#91329](https://github.com/NousResearch/hermes-agent/issues/91329) | Bot Mode 群设置中直接管理成员 | UX 改进，降低操作路径 |
| [#102650](https://github.com/NousResearch/hermes-agent/pull/102650) | `hermes sessions reset-store` 恢复命令 | **已在 PR 中**，owner-only 安全恢复机制 |

---

## 7. 用户反馈摘要

**痛点（高频）：**
- **Desktop 多 profile 状态混乱**：#102526（默认 profile 打开错误 chat）、#101091（provider/model 配对错乱）、#102635（Telegram 后台任务路由错误）——多 profile 是 Desktop 重度用户的核心场景，当前状态隔离存在明显缺陷。
- **shell hooks / 插件钩子在 serve 模式下不生效**：#69825、#102504、#102592 三 issue 指向同一根因——`serve` 命令跳过插件发现和 hooks 注册，导致用户在 Desktop 中配置的 guards（outbound-send、destructive-command、tenant guards）**全部静默失效**，这是严重的安全隐患。
- **Desktop composer 拖拽交互体验差**：#70422、#101318 两 issue 均抱怨 16px 上滑即可 detach composer，无关闭选项，影响日常文本选择。
- **Reasoning Blocks off 不工作**：#93817 用户评价"makes Desktop unusable"，设置关闭后仍 dump 全部 thinking 和 tool calls。
- **Windows 网络稳定性**：#102642、#102057 反映 Windows 端 Agent Bridge 冷启动和群聊的间歇性超时。

**正面反馈方向：**
- 安全加固类 PR（#99490 密钥存储加密、#31003 写入时拒绝脱敏占位符）受到关注，反映用户对本地凭证安全的重视。
- `hermes sessions reset-store`（#102650）作为 recovery 命令获认可，说明用户需要明确的故障恢复路径。

---

## 8. 待处理积压

| Issue | 严重度 | 距今创建 | 备注 |
|---|---|---|---|
| [#102574](https://github.com/NousResearch/hermes-agent/issues/102574) | P1 | 1 天 | 共享调度器阻塞 safety timer，无 fix PR，建议优先处理 |
| [#102526](https://github.com/NousResearch/hermes-agent/issues/102526) | P1 | 2 天 |

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-09-04

## 1. 今日速览

过去24小时内，PicoClaw 项目保持中等活跃度：共处理 6 条 Issue 和 8 条 PR。其中 1 条 Issue 被关闭（#3339），1 条 PR 被合并（#3329），整体以依赖更新和维护修复为主。Web UI 性能卡顿问题（#3281）持续引发社区关注，已有对应修复 PR（#3347）待审核合并。QQ 频道授权失效问题同日出现两份报告（#3349 / #3365），提示上游依赖可能存兼容性变更，值得关注。

## 2. 版本发布

今日无新版本发布。

## 3. 项目进展

**已合并/关闭的 PR：**
- [#3329](https://github.com/sipeed/picoclaw/pull/3329) `fix(line): warn on inert webhook_host/webhook_port` — 修复 LINE 渠道 `webhook_host` / `webhook_port` 配置声明但未实际读取的缺陷，改为输出警告而非静默忽略，避免了用户配置不生效却无提示的问题。

**开放中的关键 PR：**
- [#3347](https://github.com/sipeed/picoclaw/pull/3347) `fix laggy interface` — 针对 Web UI 长历史记录导致输入卡顿的修复，已在本机和移动端浏览器验证通过，待合并后有望直接解决 #3281。
- 多条 Dependabot 依赖升级 PR（[#3360](https://github.com/sipeed/picoclaw/pull/3360)、[#3361](https://github.com/sipeed/picoclaw/pull/3361)、[#3362](https://github.com/sipeed/picoclaw/pull/3362)、[#3363](https://github.com/sipeed/picoclaw/pull/3363)、[#3364](https://github.com/sipeed/picoclaw/pull/3364)）将 AWS SDK、golang.org/x/term、irc-go、protobuf、Lark SDK 等提升至最新版本，主要为安全性与兼容性改进。

**进展评估：** 核心功能修复（LINE webhook、Web UI 卡顿）稳步推进，依赖链持续更新，整体项目健康度良好。

## 4. 社区热点

| Issue/PR | 热度指标 | 简述 |
|---|---|---|
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) | 9 条评论 · 2 👍 | Web UI 长历史记录下输入严重卡顿，社区共鸣强，已有对应修复 PR #3347 |
| [#3349](https://github.com/sipeed/picoclaw/issues/3349) + [#3365](https://github.com/sipeed/picoclaw/issues/3365) | 同日双报 | QQ 频道 401 授权错误，指向 botgo v0.2.1 + resty ≥ v2.17 的兼容性问题，需维护者关注 |
| [#3340](https://github.com/sipeed/picoclaw/pull/3340) | 关联 #3338 | Slack 图片上传因缺少 `FileSize` 参数被 SDK 拒绝，修复逻辑清晰，待合并 |

**热点分析：** Web UI 性能与 QQ 渠道授权是当前社区最活跃的两个焦点。前者有明确修复路径，后者涉及上游 SDK 兼容性，可能需要维护者协调升级或临时降级处理。

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | 状态 | 修复 PR |
|---|---|---|---|---|
| 🔴 高 | [#3365](https://github.com/sipeed/picoclaw/issues/3365) / [#3349](https://github.com/sipeed/picoclaw/issues/3349) | QQ 频道 401 错误，botgo v0.2.1 + resty ≥ v2.17 兼容性问题 | OPEN | 暂无 |
| 🔴 高 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI 长历史聊天记录导致输入严重卡顿 | OPEN | [#3347](https://github.com/sipeed/picoclaw/pull/3347) 待合并 |
| 🟡 中 | [#3338](https://github.com/sipeed/picoclaw/issues/3338) | Slack 图片上传始终返回 "file size cannot be 0" | OPEN | [#3340](https://github.com/sipeed/picoclaw/pull/3340) 待合并 |
| 🟡 中 | [#3346](https://github.com/sipeed/picoclaw/issues/3346) | RKLLM 在 ARM 开发板上回复异常 | OPEN | 暂无 |
| 🟢 低 | [#3339](https://github.com/sipeed/picoclaw/issues/3339) | Google Antigravity 返回 429，疑似配额耗尽 | CLOSED | — |

## 6. 功能请求与路线图信号

- **Web UI 性能优化**（#3281 / #3347）：用户明确要求改善长会话下的交互体验，修复 PR 已提交，有望纳入下一版本。
- **Slack 媒体上传**（#3338 / #3340）：功能修复类 PR，属于现有渠道的完善，合并后提升 Slack 渠道可用性。
- **LINE webhook 配置警告**（#3329）：已合并，体现项目在可观测性方面的持续改进方向。

无明显新功能需求，当前社区反馈集中于已有渠道的稳定性与性能优化。

## 7. 用户反馈摘要

- **Web UI 体验**：用户反馈在会话历史较长时输入框明显卡顿，影响日常使用，修复后已在 Brave 桌面和移动端验证。
- **QQ 频道**：用户报告 401 错误，错误信息为"请求头 Authorization 参数格式错误"，怀疑与 botgo/resty 版本更新有关，影响 Docker 和 Linux x86 部署。
- **Slack 渠道**：图片上传功能完全不可用，原因是 `FileSize` 字段未被设置，SDK 在发出网络请求前就拒绝了请求。
- **RKLLM**：ARM 开发板用户遇到模型回复异常，需要进一步排查。
- **Google Antigravity**：认证和模型发现正常，但生成请求持续 429，用户推测为 API 配额耗尽。

## 8. 待处理积压

| 类型 | ID | 说明 | 建议 |
|---|---|---|---|
| Bug | [#3365](https://github.com/sipeed/picoclaw/issues/3365) / [#3349](https://github.com/sipeed/picoclaw/issues/3349) | QQ 频道 401 问题涉及上游依赖兼容性，需维护者评估是否升级 botgo 或锁定 resty 版本 | 优先处理，影响渠道可用性 |
| PR | [#3347](https://github.com/sipeed/picoclaw/pull/3347) | Web UI 卡顿修复，已测试验证，开放中 | 审核合并 |
| PR | [#3340](https://github.com/sipeed/picoclaw/pull/3340) | Slack 图片上传修复，逻辑清晰，开放中 | 审核合并 |
| Bug | [#3346](https://github.com/sipeed/picoclaw/issues/3346) | RKLLM ARM 回复异常，缺少复现细节 | 需作者补充日志或截图 |
| PR | [#3360–#3364](https://github.com/sipeed/picoclaw/pulls) | 5 条 Dependabot 依赖升级，自动维护 | 常规审核合并 |

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# 📊 NanoClaw 项目动态日报
**日期：2026-09-04** | 数据来源：GitHub (nanocoai/nanoclaw)

---

## 1. 今日速览

NanoClaw 在过去24小时保持**中高活跃度**：5条 Issue 更新（4新/活跃 + 1关闭）、23条 PR 更新（20待合并 + 3已合并/关闭）。今日无新版本发布，但合并了3个重要修复，涵盖依赖升级、消息重复发送和静默/内部思考块过滤。项目整体处于持续迭代阶段，Provider 合约重构系列（#3581–#3591）持续推进，容器侧开发体验（测试清理 #3710、临时目录泄漏）和 WhatsApp 频道改进（#3711–#3712）是当前焦点。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### ✅ 今日合并/关闭的 PR（3条）

**#3461** [CLOSED] — `chore(deps): bump all @chat-adapter/* + chat 4.29.0 → 4.38.1`
- 升级9个 minor 版本的 channel adapter 依赖，与 trunk 的 `chat` 包保持同步
- 每个 `/add-<channel>` skill 都会复制 branch 的 `package.json`，因此需一次性更新

**#3462** [CLOSED] — `fix(mcp-tools): guard send_message against re-sending content the mid-turn block door already delivered`
- 修复与 #2404 同类的问题：`deliverMidTurnBlocks()` 已通过 DB-backed echo guard 避免了相同内容的重复发送，本次 PR 对 `send_message` 补充了同等保护

**#3126** [CLOSED] — `fix(agent-runner): never deliver silence, never deliver <internal> thinking`
- 修复 agent-runner 将空消息或 `<internal>` 思考块错误投递到出站通道的问题

> **进展评估**：今日合并聚焦于 **bug 修复与依赖维护**，没有新功能上线，但为上层 feature（如 #3713 delivery mode）打下了更稳定的基础。

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issue / PR

| 编号 | 类型 | 摘要 | 链接 |
|------|------|------|------|
| #3709 | Issue | SQLite 测试使用固定 `/tmp` 路径，并发 vitest 会互相删除数据库 | [Issue #3709](https://github.com/nanocoai/nanoclaw/issues/3709) |
| #3440 | PR | docker-driver 修复 SELinux 阻止挂载、组可写 rw 挂载、游离 NUL 字节 | [PR #3440](https://github.com/nanocoai/nanoclaw/pull/3440) |
| #3711 | PR | 延迟加载入站内容直到确认有 agent 接收，避免无用的网络请求/下载 | [PR #3711](https://github.com/nanocoai/nanoclaw/pull/3711) |
| #2003 | PR | 语音转录 V2，容器侧处理、默认主权模型 | [PR #2003](https://github.com/nanocoai/nanoclaw/pull/2003) |
| #3704 | Issue | 请求添加受保护的 session-assembly 钩子以支持子类化实现 | [Issue #3704](https://github.com/nanocoai/nanoclaw/issues/3704) |

**分析**：
- **#3709** 反映了多 worktree / CI 并行测试的痛点，社区对可重复的测试环境需求明显。
- **#3440** 涉及 SELinux 等生产环境敏感问题，作者 dwalthour 持续关注中（最后更新 2026-09-04），PR 已 OPEN 待审。
- **#3711 / #3712** 是一组联动修复（#3712 依赖 #3711），mmv 正在系统性地改进 WhatsApp 频道的内容解析与下载行为，属于用户可感知的质量提升。
- **#2003** 是语音转录能力的重大升级，从宿主机迁移到容器内处理，体现了项目对"主权模型"（sovereignty model）的重视。

---

## 5. Bug 与稳定性

| 严重度 | Issue / PR | 摘要 | 状态 | Fix PR |
|--------|-----------|------|------|--------|
| 🟡 中 | [#3706](https://github.com/nanocoai/nanoclaw/issues/3706) | `ncl groups config add-mount --container` 接受绝对路径时产生嵌套错误路径 | OPEN | — |
| 🔴 高 | [#3709](https://github.com/nanocoai/nanoclaw/issues/3709) | SQLite 测试使用固定 `/tmp` fixture，并发 vitest 进程互相删除数据库 | OPEN | — |
| 🟡 中 | [#3705](https://github.com/nanocoai/nanoclaw/issues/3705) | `ncl tasks update --recurrence` 不重新计算 `process_after`，导致调度时间错误 | OPEN | — |
| 🟢 低 | [#3426](https://github.com/nanocoai/nanoclaw/issues/3426) | `send_card` 文档承诺 callback buttons，但 bridge 自 #2265 起丢弃无 URL 的 actions | ✅ CLOSED | — |

**修复中的问题**：
- **#3708** [PR] 修正 SQLite `busy_timeout` 与 `journal_mode` 的设置顺序（exclusive lock 问题）
- **#3462** [已合并] 修复 `send_message` 重复投递
- **#3126** [已合并] 修复静默/内部块被投递到出站通道

---

## 6. 功能请求与路线图信号

### 近期可预见的功能

| 来源 | 功能描述 | 预计纳入版本 |
|------|---------|-------------|
| [#3713](https://github.com/nanocoai/nanoclaw/pull/3713) | 按 agent group 记录 delivery mode，使不支持 `<message to>` envelope 的模型可通过 outbound tools 投递 | 下一版本（当前仅 Column + plumbing，无读取逻辑） |
| [#3592](https://github.com/nanocoai/nanoclaw/pull/3592) | 新增 `speed` 推理属性（`--speed <tier>`），与 `model` / `effort` 并列 | 下一版本 |
| [#3711](https://github.com/nanocoai/nanoclaw/pull/3711) + [#3712](https://github.com/nanocoai/nanoclaw/pull/3712) | 入站内容延迟加载 + WhatsApp 文档标题读取、停止无效下载 | 下一版本（#3712 依赖 #3711） |
| [#2003](https://github.com/nanocoai/nanoclaw/pull/2003) | 语音转录 V2，容器侧处理，默认主权 | 待定（长期 PR） |

### Provider 重构系列（#3581–#3591, #3355, #3356）
zvi-fried 正在系统性地重构 Provider 合约，涵盖：
- **运行时合约**（#3581）：将 provider seam 转为可执行合约
- **Setup 合约**（#3586）：skill-declared descriptors + 安装时验证器
- **Host 合约**（#3585）：路由 host spawn 和 group-init 表面
- **指令渲染**（#3591）：provider 声明类型化事实，core 渲染 canon
- **Codex / OpenCode 合约实现**（#3584, #3588）
- **Cursor provider 集成**（#3355, #3356）

> **路线图信号**：项目正从"各 provider 自由实现"转向**合约驱动的规范化架构**，Cursor/OpenCode/Codex 三大 provider 的标准化将在近期完成合并。

---

## 7. 用户反馈摘要

| 来源 | 用户痛点 / 反馈 |
|------|---------------|
| [#3706](https://github.com/nanocoai/nanoclaw/issues/3706) | DawoudIO 指出：`--container` 参数文档未限制路径必须为相对路径，用户按直觉传入绝对路径产生不可预期的嵌套路径，属于**文档与行为不一致**的 UX 问题 |
| [#3709](https://github.com/nanocoai/nanoclaw/issues/3709) | davekim917 发现多 worktree 或 CI 并发跑 vitest 时，固定 `/tmp` fixture 路径导致数据库互相覆盖删除——**测试隔离性缺失** |
| [#3705](https://github.com/nanocoai/nanoclaw/issues/3705) | DawoudIO 报告：修改 task 的 recurrence（如周→日）后 `process_after` 未重算，调度器仍按旧周期触发——**状态未同步的隐性 Bug** |
| [#3426](https://github.com/nanocoai/nanoclaw/issues/3426) | glifocat 指出：`send_card` 文档承诺支持按钮，但 bridge 在 #2265 后丢弃无 URL 的 actions，agent 将责任归咎于平台——**文档与实现脱节导致 agent 行为异常** |
| [#3704](https://github.com/nanocoai/nanoclaw/issues/3704) | davekim917（维护 fork 的用户）请求暴露 `session-assembly` 钩子以便子类化扩展——**扩展性需求**，当前 `compose.ts` 单槽注册机制对 fork 场景不够友好 |

---

## 8. 待处理积压

| 编号 | 类型 | 摘要 | 关注建议 |
|------|------|------|---------|
| [#3440](https://github.com/nanocoai/nanoclaw/pull/3440) | PR | docker-driver SELinux / 权限修复 | 已 OPEN 多日，待核心 reviewer 审核 |
| [#2003](https://github.com/nanocoai/nanoclaw/pull/2003) | PR | 语音转录 V2 容器侧实现 | 长期 PR（创建于 2026-04-25），功能重大但需要重新评审 |
| [#3581–#3591](https://github.com/nanocoai/nanoclaw/pulls?q=is%3Apr+is%3Aopen+author%3Azvi-fried) | PR 系列 | Provider 合约重构（7条 PR） | 属于同一工作流，需评估整体合并顺序 |
| [#3713](https://github.com/nanocoai/nanoclaw/pull/3713) | PR | per-agent-group delivery mode | 当前仅有 Column + plumbing，无读取逻辑；需评估何时接入实际使用 |
| [#3704](https://github.com/nanocoai/nanoclaw/issues/3704) | Issue | 子类化扩展请求 | 来自 fork 维护者，反映 upstream 扩展性不足，需 maintainers 决策是否接纳 |

---

**📈 项目健康度评估**：活跃开发中，Bug 修复节奏稳定（今日合并3条），新功能以 Provider 标准化和测试基础设施改进为主。社区参与度良好，davekim917、DawoudIO、glifocat、mmv、zvi-fried 等多位贡献者持续产出。需关注 PR #3440 和 #2003 的合并进度，以及 #3709 / #3705 的修复排期。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期：2026-09-04** | 数据来源：GitHub API | 统计周期：过去24小时

---

## 1. 今日速览

项目今日保持**中高强度活跃**，共处理 **29 条更新**（11 Issues + 18 PRs），其中 **10 条 PR 已合并**、**3 条 Issue 已关闭**，显示维护者对技术债和性能问题的响应效率较高。核心进展集中在 **TypeScript 类型化清理**（WebUI 生产代码和测试基础设施）和 **Agent Loop 性能优化**（text_delta 去重、prompt budget 动态推导）。未发布新版本，但多个高质量 PR 已准备好待合并。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并的重要 PR

| PR | 标题 | 作者 | 影响 |
|---|---|---|---|
| [#8038](https://github.com/nearai/ironclaw/pull/8038) | refactor(webui): type and validate frontend API boundaries | @italic-jinxin | 替换 permissive JSON transport 为 typed object boundaries，覆盖 device-link、pairing、notification setup 等 7 个模块 |
| [#8039](https://github.com/nearai/ironclaw/pull/8039) | refactor(webui): type production components and hooks | @italic-jinxin | 移除 64 个生产组件的 `@ts-nocheck`，添加 React Query、DOM、auth payload 等显式类型 |
| [#8037](https://github.com/nearai/ironclaw/pull/8037) | chore(webui): ratchet TypeScript suppressions | @italic-jinxin | 移除 40 个冗余 `@ts-nocheck`，添加 suppression baseline 和 CI ratchet 防止新指令 |
| [#8043](https://github.com/nearai/ironclaw/pull/8043) | perf(loop-host): coalesce streamed text updates | @henrypark133 | **O(N·k) → O(N)** 优化：`text_delta` 改为增量推送而非全量重序列化，16 KiB/1000 deltas 测试从 1000s 降至可接受范围 |
| [#8046](https://github.com/nearai/ironclaw/pull/8046) | feat(subagent): child approval/auth gate notification | @henrypark133 | 子代理阻塞时主动通知父代理 inbox，修复 R3 slice 3a 债务 |
| [#7984](https://github.com/nearai/ironclaw/pull/7984) | fix(tools): size tool_search replies to first-look envelope | @henrypark133 | tool_search 响应大小与模型 first-look envelope 对齐，避免 16,066B 响应仅 857B 到达模型的问题 |
| [#8060](https://github.com/nearai/ironclaw/pull/8060) | ci(nextest): timeout headroom for architecture scans | @henrypark133 | 为 `reborn_{extension_contract,loop_port,product_contract}_location_scan` 增加超时余量（176.8s 接近 180s 硬杀） |

**项目整体向前推进：**
- **技术债清理**：WebUI TypeScript 类型化进入收尾阶段，test infrastructure 和 production components 已基本覆盖
- **性能优化**：streaming text 去重修复解决了 O(N·k) 复杂度问题
- **功能完善**：subagent approval notification 修复了父子代理通信盲区

---

## 4. 社区热点

### 高关注度 Issues

| Issue | 标题 | 作者 | 状态 | 热度分析 |
|---|---|---|---|---|
| [#7903](https://github.com/nearai/ironclaw/issues/7903) | Decision spike: persistent per-user sandboxed executor behind trusted host kernel | @serrrfirat | OPEN | **高优先级设计讨论**：risk: high，涉及 Reborn 架构核心边界——当前 trusted host 进程保留完整 agent loop，仅 `builtin.shell` 命令进入 Docker sandbox。2 条评论显示维护者在权衡 authority boundary 与 CLI plumbing 复杂度 |
| [#8009](https://github.com/nearai/ironclaw/issues/8009) | MCP egress errors flatten to "response_error" | @pranavraja99 | OPEN | **诊断盲区**：`mcp_http_error` 将所有 `RuntimeHttpEgressError` 折叠为单一 reason code `"response_error"`，导致 hosted-MCP discovery 失败无法诊断。1 条评论 |
| [#8057](https://github.com/nearai/ironclaw/issues/8057) | Prompt budget should account for non-transcript material | @henrypark133 | OPEN | **预算超支风险**：identity/SYSTEM.md、skill snippets、tool schemas 叠加在 transcript budget 之上，可能导致请求超出模型窗口。0 评论但关联 PR #8053 待合并 |
| [#8052](https://github.com/nearai/ironclaw/issues/8052) | Daily ironclaw failure taxonomy — 2026-09-03 | @pranavraja99 | OPEN | **质量追踪**：officeqa 63 个 non-pass 均为 deepseek-v4-flash 过 OCR Treasury Bulletins 的真实模型质量问题。无评论，显示自动化分析管道运行中 |

### 高关注度 PRs（待合并）

| PR | 标题 | 作者 | 状态 |
|---|---|---|---|
| [#8053](https://github.com/nearai/ironclaw/pull/8053) | feat(loop): derive prompt context budget from model's advertised window | @henrypark133 | OPEN [XL, medium risk] |
| [#8062](https://github.com/nearai/ironclaw/pull/8062) | fix(llm): send conversation cache keys on OpenAI request paths | @henrypark133 | OPEN [XL, low risk] |
| [#8044](https://github.com/nearai/ironclaw/pull/8044) | fix(llm): cache-gate new Claude families by denylist | @henrypark133 | OPEN [XL, low risk] |

---

## 5. Bug 与稳定性

### 今日报告的 Bug（按严重程度）

| Issue/PR | 标题 | 严重程度 | 状态 | Fix PR |
|---|---|---|---|---|
| [#8009](https://github.com/nearai/ironclaw/issues/8009) | MCP egress errors flatten to "response_error" | **高** - 诊断能力丧失 | OPEN | 无 |
| [#8056](https://github.com/nearai/ironclaw/pull/8056) | fix(host-api): avoid malformed preview range panic | **高** - 崩溃风险 | OPEN [待合并] | #8056 |
| [#8059](https://github.com/nearai/ironclaw/pull/8059) | fix(responses): send cancel reason the product surface accepts | **中** - API 行为错误 | OPEN [待合并] | #8059 |
| [#8054](https://github.com/nearai/ironclaw/pull/8054) | fix(assistant): check pairing before command admission | **中** - UX 流程错误 | OPEN [待合并] | #8054 |
| [#8066](https://github.com/nearai/ironclaw/issues/8066) | Prevent command result cards from collapsing | **低** - UI 渲染问题 | OPEN | 无 |

**崩溃/回归风险点：**
- [#8056](https://github.com/nearai/ironclaw/pull/8056) 修复了 malformed embedded tool-result text 导致的 panic，根因是 closing JSON delimiter 出现在 first opening delimiter 之前
- [#8055](https://github.com/nearai/ironclaw/pull/8055) 已合并，修复了 `main` 分支 `webui_v2::static_assets` 测试 panic（由 commit `666ebcbf08` 引入）

---

## 6. 功能请求与路线图信号

### 近期功能请求

| Issue/PR | 需求 | 优先级 | 路线图信号 |
|---|---|---|---|
| [#7903](https://github.com/nearai/ironclaw/issues/7903) | 持久化 per-user sandboxed executor 在 trusted host kernel 之后 | **高** | 架构决策 spike，显示团队在重新评估 agent loop 边界划分 |
| [#8064](https://github.com/nearai/ironclaw/issues/8064) | Command result cards 增加 dismiss 动作 | 中 | 用户体验优化，反映 slash command 结果卡片积累问题 |
| [#8063](https://github.com/nearai/ironclaw/issues/8063) | 导航命令菜单时保持 active command 可见 | 低 | UI 可访问性改进 |
| [#8065](https://github.com/nearai/ironclaw/issues/8065) | 命令元数据水平对齐 | 低 | UI 一致性改进 |

### 可能纳入下一版本的功能

基于待合并 PR 判断：
1. **动态 Prompt Budget** (#8053) - 从模型 advertised context window 派生，替代硬编码 128k/20k
2. **Conversation Cache Keys** (#8062) - OpenAI 请求路径发送稳定 pseudonymous cache key
3. **Claude 新家族支持** (#8044) - denylist 替换 allowlist，支持 `claude-fable-*` 等新家族
4. **Subagent Approval Notification** (#8046 已合并) - 子代理阻塞时通知父代理

---

## 7. 用户反馈摘要

### 真实用户痛点

1. **MCP 错误诊断困难** (#8009)
   - 用户反馈：hosted-MCP discovery 失败只显示 `"response_error"` 单一 token，无法区分底层原因（网络超时、认证失败、路由错误等）
   - 痛点等级：高（影响生产环境排障）

2. **Command Result Cards 积累占用空间** (#8064, #8066)
   - 用户反馈：多次执行 `/model` 等命令后，结果卡片不断积累且无法关闭，最终收缩为仅显示边框的水平线
   - 场景：频繁使用 slash command 的开发者

3. **命令菜单导航体验** (#8063, #8065)
   - 用户反馈：键盘导航时 active command 可能移出可见区域；命令名称宽度不一致导致标题/描述起始位置不对齐
   - 影响：降低命令扫描效率

4. **首次接触体验** (#8054)
   - 用户反馈：未配对的 Telegram 用户首次发送 `/start` 时，系统返回 "Available commands" 清单而非 pairing/connect notice
   - 根因：command admission 在 pairing lookup 之前执行

5. **Prompt Budget 超支** (#8057)
   - 用户反馈：identity/SYSTEM.md、skill snippets、tool schemas 叠加在 transcript budget 之上，实际请求可能超出模型窗口
   - 风险：静默截断或 API 错误

### 用户满意点
- TypeScript 类型化进展显著（WebUI 生产代码 + 测试基础设施基本覆盖）
- 性能优化见效（streaming text coalescing 修复 O(N·k) 问题）
- 子代理通知机制完善（#8046 已合并）

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 标题 | 创建时间 | 时长 | 建议优先级 |
|---|---|---|---|---|
| [#7903](https://github.com/nearai/ironclaw/issues/7903) | Decision spike: persistent per-user sandboxed executor | 2026-08-26 | 9 天 | **P0** - 架构核心决策，risk: high |
| [#8009](https://github.com/nearai/ironclaw/issues/8009) | MCP egress errors flatten to "response_error" | 2026-08-31 | 4 天 | **P1** - 诊断能力丧失 |
| [#8057](https://github.com/nearai/ironclaw/issues/8057) | Prompt budget should account for non-transcript material | 2026-09-03 | 1 天 | **P1** - 关联 PR #8053 待合并 |
| [#8052](https://github.com/nearai/ironclaw/issues/8052) | Daily failure taxonomy — 2026-09-03 | 2026-09-03 | 1 天 | P2 - 自动化分析，无需人工响应 |

### 待合并的 PR 积压

| PR | 标题 | 大小 | 风险 | 待合并时长 |
|---|---|---|---|---|
| [#8053](https://github.com/nearai/ironclaw/pull/8053) | feat(loop): derive prompt context budget from window | XL | medium | 1 天 |
| [#8062](https://github.com/nearai/ironclaw/pull/8062) | fix(llm): send conversation cache keys | XL | low | <1 天 |
| [#8044](https://github.com/nearai/ironclaw/pull/8044) | fix(llm): cache-gate new Claude families | XL | low | 2 天 |
| [#8054](https://github.com/nearai/ironclaw/pull/8054) | fix(assistant): pairing before command admission | M | low | 1 天 |
| [#8056](https://github.com/nearai/ironclaw/pull/8056) | fix(host-api): avoid malformed preview range panic | XS | low | 1 天 |
| [#8059](https://github.com/nearai/ironclaw/pull/8059) | fix(responses): send cancel reason product accepts | XS | low | 1 天 |
| [#8061](https://github.com/nearai/ironclaw/pull/8061) | feat(subagent): concurrent-children cap (R2 debt) | M | low | 1 天 |



</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 📊 LobsterAI 项目动态日报 — 2026-09-04

---

## 1. 今日速览

过去 24 小时内，LobsterAI 项目活跃度**较高**：共处理 21 条讨论（6 Issues + 15 PRs），其中 10 个 PR 已合并/关闭，2 个 Issue 已关闭，5 个 PR 和 4 个 Issue 仍待处理。无新版本发布，但近期已合并 2026.8.31 版本，当前开发重心转向桌面端体验优化与架构清理（移除 dsh 功能）。整体项目处于**稳定迭代期**，活跃维护者（fisherdaddy、liuzhq1986）贡献集中，社区 bug 报告质量较高。

---

## 2. 版本发布

无新版本发布。上一版本 **2026.8.31**（[#2600](https://github.com/netease-youdao/LobsterAI/pull/2600)）已合并，包含首次运行引导、Library 浏览性能优化、视频分享支持、Windows 安装器恢复增强等改进。

---

## 3. 项目进展

### 已合并/关闭 PR（10 条）

| PR | 类型 | 摘要 |
|----|------|------|
| [#2609](https://github.com/netease-youdao/LobsterAI/pull/2609) | 🔧 体验优化 | 安装前确认弹窗 + 退出应用二次确认，防止 Agent 执行中被意外打断 |
| [#2608](https://github.com/netease-youdao/LobsterAI/pull/2608) | 🧹 架构清理 | 移除 dsh（DeepSeek Hybrid）MCP 委托功能，简化代码路径 |
| [#2607](https://github.com/netease-youdao/LobsterAI/pull/2607) | 📦 构建优化 | 修复 peer install 膨胀问题，减小插件包体积 |
| [#2605](https://github.com/netease-youdao/LobsterAI/pull/2605) | 🐧 Windows | 声明 DPI 感知，修复图标模糊问题 |
| [#2606](https://github.com/netease-youdao/LobsterAI/pull/2606) | 🐧 Windows | 启动辅助进程时隐藏控制台窗口 |
| [#2604](https://github.com/netease-youdao/LobsterAI/pull/2604) | 🎨 UI | 语音输入按钮配额耗尽时显示置灰状态，保持可点击 |
| [#2603](https://github.com/netease-youdao/LobsterAI/pull/2603) | 🌐 i18n | 优化语音配额耗尽中文提示文案 |
| [#2602](https://github.com/netease-youdao/LobsterAI/pull/2602) | 🌐 功能恢复 | 恢复 2026.9.4 分支的交互式内置浏览器（Agent Browser） |
| [#2599](https://github.com/netease-youdao/LobsterAI/pull/2599) | 🎨 UI | IM 多 Bot 卡片布局优化为双列响应式 |
| [#2600](https://github.com/netease-youdao/LobsterAI/pull/2600) | 🏷️ Release | 打包 2026.8.31 版本 |

**进展评估**：今日合并集中在**Windows 体验打磨、UI 微调、架构清理**，未涉及核心引擎重大变更，项目整体稳步前进。

---

## 4. 社区热点

### 高关注度 Issue

| Issue | 状态 | 亮点 | 链接 |
|-------|------|------|------|
| #2601 | 🟢 OPEN | 今日新建，MCP Apps / Prefab UI 渲染支持需求 | [#2601](https://github.com/netease-youdao/LobsterAI/issues/2601) |
| #1556 | 🔴 CLOSED | IM 配置指南 404 已修复 | [#1556](https://github.com/netease-youdao/LobsterAI/issues/1556) |
| #1552 | 🔴 CLOSED | AI 产物 Markdown 预览功能需求（已关闭，可能已实现） | [#1552](https://github.com/netease-youdao/LobsterAI/issues/1552) |

**分析**：
- **#2601** 反映了用户对 **MCP Apps 扩展生态**的关注，PrefectHQ Prefab 等工具已支持 `ui://` 交互式 HTML UI，社区期望桌面端也能渲染这些交互界面。
- **#1552** 虽已关闭，但需求明确：Write 工具生成文件后需要内建预览，替代"Agent 全文贴到聊天"的低效方式。
- **#1556** 文档 404 问题已解决，但暴露文档维护滞后于功能迭代的问题。

---

## 5. Bug 与稳定性

| 问题 | 严重度 | 状态 | 链接 | Fix PR |
|------|--------|------|------|--------|
| #1088 Prefetch 异步回调不校验 `turnToken`，可能跨轮次污染消息 | 🔴 高 | OPEN | [#1088](https://github.com/netease-youdao/LobsterAI/issues/1088) | — |
| #1089 CoworkRunner `startSession/continueSession` 无重入保护，并发导致流式消息损坏 | 🔴 高 | OPEN | [#1089](https://github.com/netease-youdao/LobsterAI/issues/1089) | — |
| #1079 `continueSession` 失败时展示两条重复错误消息 | 🟡 中 | OPEN (PR #1087) | [#1089](https://github.com/netease-youdao/LobsterAI/issues/1089) | [#1087](https://github.com/netease-youdao/LobsterAI/pull/1087) |
| #1081 MCP 编辑弹窗滚动条超出圆角边框 | 🟢 低 | OPEN (PR #1081) | [#1081](https://github.com/netease-youdao/LobsterAI/issues/1081) | [#1081](https://github.com/netease-youdao/LobsterAI/pull/1081) |

**分析**：
- **#1088、#1089** 均为**并发安全**类 Bug，影响生产环境数据一致性，且均为 stale 标记（久未处理），需优先关注。
- **#1087** 已合并，修复了 `continueSession` 错误消息重复显示问题。
- #1079 的 PR [#1087](https://github.com/netease-youdao/LobsterAI/pull/1087) 已合并，对应 Issue 应跟进关闭。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 关联 PR | 纳入可能性 |
|------|------|---------|-----------|
| MCP Apps / Prefab UI 渲染 | Issue #2601 | 无 | 🟡 中等 — 与浏览器能力修复方向一致 |
| 定时任务失败 IM 告警 | Issue/PR #1078 | [#1078](https://github.com/netease-youdao/LobsterAI/pull/1078) | 🟡 中等 — 异步回调不对称问题明确，但 stale |
| 「当前进程」右侧面板 | PR #1079 | [#1079](https://github.com/netease-youdao/LobsterAI/pull/1079) | 🟢 较高 — 已实现，等待合并 |
| AI 产物 Markdown 预览 | Issue #1552 | 已关闭 | ⚪ 低 — 可能已在后续版本实现 |

**路线图信号**：
- 桌面端**交互体验**是近期重点（浏览器恢复、安装确认、退出确认）。
- **Windows 平台适配**持续投入（DPI、控制台窗口、安装器恢复）。
- 架构清理（dsh 移除）推进中，后续可能进一步精简代码。

---

## 7. 用户反馈摘要

| 反馈点 | 来源 | 情绪 |
|--------|------|------|
| IM 配置指南 404，文档可访问性问题 | [#1556](https://github.com/netease-youdao/LobsterAI/issues/1556) | 😤 不满 |
| Write 工具生成文件后缺少内建预览，需复制全文或切文件管理器 | [#1552](https://github.com/netease-youdao/LobsterAI/issues/1552) | 😤 不满 |
| 定时任务失败无 IM 通知，需手动查看 | [#1078](https://github.com/netease-youdao/LobsterAI/issues/1078) | 😐 中性 |
| 语音配额耗尽提示不够清晰 | [#2603](https://github.com/netease-youdao/LobsterAI/pull/2603) | 😐 中性 |
| MCP 同步提示中英混杂、弹窗滚动条溢出 | [#1081](https://github.com/netease-youdao/LobsterAI/issues/1081) | 😤 不满 |

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建时间 | 天数 | 链接 | 备注 |
|----------|------|----------|------|------|------|
| #1082 openclaw.version 版本兼容性 | ⚠️ 安全 | 2026-03-30 | ~158 | [#1082](https://github.com/netease-youdao/LobsterAI/issues/1082) | 国互中心要求更新，stale |
| #1088 Prefetch turnToken 校验缺失 | 🔴 安全 | 2026-03-31 | ~157 | [#1088](https://github.com/netease-youdao/LobsterAI/issues/1088) | 跨轮次消息污染，stale |
| #1089 CoworkRunner 并发安全 | 🔴 稳定 | 2026-03-31 | ~157 | [#1089](https://github.com/netease-youdao/LobsterAI/issues/1089) | 流式消息损坏，stale |
| #1078 定时任务 IM 告警 | 🆕 功能 | 2026-03-30 | ~158 | [#1078](https://github.com/netease-youdao/LobsterAI/pull/1078) | PR 已提交，stale |
| #1079 「当前进程」面板 | 🆕 功能 | 2026-03-30 | ~158 | [#1079](https://github.com/netease-youdao/LobsterAI/pull/1079) | PR 已提交，stale |
| #1081 MCP 国际化 & 样式修复 | 🐛 Bug | 2026-03-30 | ~158 | [#1081](https://github.com/netease-youdao/LobsterAI/pull/1081) | PR 已提交，stale |
| #1277 Electron 升级 | 📦 依赖 | 2026-04-02 | ~156 | [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | electron 40→44，stale |

**维护者建议**：积压 Issue 多为 **2026-03-30** 附近创建，距今均超过 5 个月且标记 stale。其中 **#1088、#1089** 涉及并发安全和消息污染，建议在下一个迭代中优先处理。PR #1078、#1079、#1081 已实现，待维护者 review 合并。

---

*报告生成时间：2026-09-04 | 数据来源：LobsterAI GitHub*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-09-04

## 1. 今日速览

过去24小时 CoPaw 项目保持高活跃度：共处理 27 条 Issue（新开/活跃 19 条，关闭 8 条）和 36 条 PR（待合并 21 条，已合并/关闭 15 条）。安全治理与控制台体验是今日两大主线——多条安全相关 Issue（沙箱突破、CRITICAL 规则绕过）引发社区关注，同时控制台侧边栏重构、主题统一、模型管理优化等多条 PR 正在推进。项目整体健康度良好，响应速度较快，但存在若干稳定性隐患需持续跟进。

---

## 2. 版本发布

> 无新版本发布。v2.2.0 Stable 已于 2026-09-03 发布并完成安装验证（Issue #7515）。当前开发焦点集中在 v2.2.0 后续迭代及 beta 分支修复。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#7525](https://github.com/agentscope-ai/QwenPaw/pull/7525) | Bug Fix | 修复 CRITICAL 安全发现被直接拒绝而非触发审批的治理逻辑漏洞（修复 Issue #7496） |
| [#7498](https://github.com/agentscope-ai/QwenPaw/pull/7498) | Bug Fix | 未知工具配置更新现在返回 404 而非 500 |
| [#7524](https://github.com/agentscope-ai/QwenPaw/pull/7524) | Bug Fix | 分离免费/付费模型 Tab，修复混合提供商的模型分类显示 |
| [#5399](https://github.com/agentscope-ai/QwenPaw/pull/5399) | Feature | 支持 provider 内模型自定义排序（拖拽/按钮） |
| [#5394](https://github.com/agentscope-ai/QwenPaw/pull/5394) | Feature | 插件管理器移动端卡片布局优化 |
| [#5363](https://github.com/agentscope-ai/QwenPaw/pull/5363) | Bug Fix | 设置/Agent 页面移动端响应式重构 |
| [#5334](https://github.com/agentscope-ai/QwenPaw/pull/5334) | Feature | 折叠侧边栏模式下支持切换 Agent |
| [#7267](https://github.com/agentscope-ai/QwenPaw/pull/7267) | Bug Fix | Channel 契约检查跨平台可移植性修复 |

**整体推进**：今日共合并 8 条 PR，涵盖安全治理、控制台体验优化和移动端适配，项目在"多租户版 Hub 上线（2.2.0）"后的首个迭代周期内稳步推进控制台体验和基础稳定性修复。

---

## 4. 社区热点

| Issue/PR | 标题 | 评论数 | 热度分析 |
|----------|------|--------|----------|
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | QwenPaw Hub 多租户版 2.2.0：你希望我们接下来做什么？ | 17 | ⭐ 社区对多用户/团队协作功能期待强烈，此 Issue 是产品路线图征集的核心阵地 |
| [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) | 安全沙箱被突破 | 9 | 🔴 外部安全研究者的突破报告引发关注，直接推动了 #7525 PR 的合并 |
| [#7505](https://github.com/agentscope-ai/QwenPaw/issues/7505) | 局域网 LLM Server 频繁 disconnect | 6 | 用户部署 LM Studio 本地模型时遇到的连接稳定性痛点 |
| [#4036](https://github.com/agentscope-ai/QwenPaw/issues/4036) | 添加模型步骤过于繁琐 | 6 | 长期 open 的 UX 改进需求，被列为 good first issue |
| [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | 危险指令容易绕过 | 6 | 与 #7511 同类安全议题，持续关注中 |

**热点分析**：社区关注度集中在**安全治理**和**多租户产品化**两个方向。Hub 多租户版的路线图讨论（#7318）获得了最多的社区参与，表明用户群体正在从个人助手向团队协作场景扩展。

---

## 5. Bug 与稳定性

| 级别 | Issue | 描述 | 状态 | Fix PR |
|------|-------|------|------|--------|
| 🔴 高 | [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) | 安全沙箱被突破 | 已关闭 | 关联治理修复 #7525 |
| 🔴 高 | [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | 危险指令可绕过 | Open | 待处理 |
| 🟡 中 | [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | ReMe 后台 embedding 任务失败（依赖访问时序问题） | Open | 待处理 |
| 🟡 中 | [#7476](https://github.com/agentscope-ai/QwenPaw/issues/7476) | Cron 任务在 misfire_grace 窗口内重复调度，备份脚本执行两次 | Open | 待处理 |
| 🟡 中 | [#7534](https://github.com/agentscope-ai/QwenPaw/issues/7534) | 飞书会话 queue consumer 长驻卡死，新消息无法创建新消费者 | Open | 待处理 |
| 🟢 低 | [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | 自定义提供商加载失败（max_tokens 迁移问题） | 已关闭 | 已修复 |
| 🟢 低 | [#7545](https://github.com/agentscope-ai/QwenPaw/issues/7545) | 桌面端右键复制选项缺失 | 已关闭 | 已修复 |
| 🟢 低 | [#7512](https://github.com/agentscope-ai/QwenPaw/issues/7512) | 会话思考/输出期间无法切换 | 已关闭 | 已修复 |

**稳定性评估**：今日关闭 8 条 Issue，其中安全相关 2 条、体验类 2 条。仍有 3 条中等严重程度的 Bug 待处理，尤其是飞书 consumer 卡死（#7534）和 ReMe embedding 失败（#7469）可能影响生产环境稳定性。

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 纳入可能性 |
|----------|----------|------------|
| [#7519](https://github.com/agentscope-ai/QwenPaw/issues/7519) | 手机移动端远程连接桌面端能力 | ⭐⭐⭐ 高优先级，用户远程办公场景明确 |
| [#7543](https://github.com/agentscope-ai/QwenPaw/issues/7543) | 后台静默更新，避免更新期间应用不可用 | ⭐⭐⭐ 高优先级，直接影响用户体验 |
| [#1775](https://github.com/agentscope-ai/QwenPaw/issues/1775) | 类似 Codex steer mode 的消息附加功能 | ⭐⭐ 中优先级，good first issue |
| [#7527](https://github.com/agentscope-ai/QwenPaw/issues/7527) | Context compaction 时保留 agent persona 和对话风格 | ⭐⭐ 中优先级，长期记忆质量改进 |
| [#7533](https://github.com/agentscope-ai/QwenPaw/issues/7533) | 支持消息按钮（选项卡片交互） | ⭐⭐ 中优先级，channel 体验增强 |
| [#7540](https://github.com/agentscope-ai/QwenPaw/issues/7540) | 配置开关关闭 env_context 中的硬编码 identity 行 | ⭐ 低优先级，定制化合规需求 |
| [#7535](https://github.com/agentscope-ai/QwenPaw/issues/7535) | Matrix channel 支持 Element 认证（MSC2965） | ⭐ 低优先级，特定渠道需求 |

**结合已有 PR 判断**：
- 侧边栏重构（#7502）和主题统一（#7487）正在推进，与 #7519（移动端远程连接）形成体验协同
- #7538（运行时环境管理统一）为多租户 Hub 提供了基础设施铺垫
- #7542（滚动回退消息分页）解决 context compaction 后历史消息不可追溯的问题，与 #7527 诉求呼应

---

## 7. 用户反馈摘要

**痛点**：
1. **连接稳定性**：局域网 LLM Server（LM Studio）频繁 disconnect 导致超时（#7505），飞书 consumer 卡死导致会话静默无响应（#7534）
2. **配置复杂度**：添加模型步骤繁琐，多次跳转（#4036）；自定义 provider 因字段迁移报错（#7474）
3. **安全焦虑**：沙箱突破（#7511）和指令绕过（#7443）引发用户对 AI 安全性的担忧
4. **更新体验**：前台更新导致应用不可用，影响工作效率（#7543）
5. **历史消息丢失**：context compaction 后compact掉的对话无法回溯（#7542 的诉求）

**满意点**：
- v2.2.0 多租户 Hub 方向获得社区广泛认可（#7318 高互动）
- 控制台移动端适配持续改进（#5394, #5363, #5334 连续修复）
- 安全治理响应迅速，#7496 提出的 CRITICAL 规则问题当日即有 PR 修复（#7525）

---

## 8. 待处理积压

| 类型 | Issue/PR | 创建时间 | 备注 |
|------|----------|----------|------|
| 🚨 安全 | [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | 2026-08-31 | 危险指令绕过，与 #7511 同类，尚未分配修复 |
| 🚨 安全 | [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) | 2026-09-03 | 沙箱突破，已关闭但需评估修复是否彻底 |
| ⚠️ 稳定性 | [#7534](https://github.com/agentscope-ai/QwenPaw/issues/7534) | 2026-09-03 | 飞书 consumer 卡死，影响生产环境 |
| ⚠️ 稳定性 | [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | 2026-09-01 | ReMe embedding 失败，silent error |
| ⚠️ 稳定性 | [#7476](https://github.com/agentscope-ai/QwenPaw/issues/7476) | 2026-09-01 | Cron 重复调度，备份脚本执行两次 |
| 📌 体验 | [#4036](https://github.com/agentscope-ai/QwenPaw/issues/4036) | 2026-05-04 | 添加模型步骤繁琐，长期未解决（good first issue） |
| 📌 体验 | [#7541](https://github.com/agentscope-ai/QwenPaw/issues/7541) | 2026-09-03 | 按 channel 隔离 session 的架构问题，俄罗斯语用户提出 |

**维护者关注建议**：
- 安全类 Issue #7443 需尽快评估并制定修复计划
- #7534 飞书 consumer 卡死问题涉及队列管理核心逻辑，建议优先级提升
- #4036 作为 good first issue 已 open 近 4 个月，可考虑分配贡献者处理

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-09-04

---

## 1. 今日速览

ZeroClaw 今日保持高强度活跃，过去24小时内共处理 50 条 Issue 与 50 条 PR，其中 **14 条 Issue 已关闭**，**1 条 PR 已合并**，另有大量新 Issue/PR 涌入，整体呈现"高吞吐、高讨论密度"的健康开发节奏。安全策略（沙箱粒度、Shell V1 权限策略）与 ACP/Code 会话持久化成为今日核心话题，多个 RFC 级提案进入实现阶段，项目正在从架构治理向可执行特性快速推进。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已关闭/合并的重要 PR

| PR | 内容 | 影响 |
|---|---|---|
| [#10539](https://github.com/zeroclaw-labs/zeroclaw/pull/10539) | 修复运行时在工具 Schema 中错误广告"自批准"行为 | 安全合规修复，消除模型绕过审批门的风险 |
| [#10529](https://github.com/zeroclaw-labs/zeroclaw/issues/10529) | Claude Fable 5.1 thinking 进度更新支持（已关闭） | 完成 Anthropic 思考模式 UX 适配 |
| [#7543](https://github.com/zeroclaw-labs/zeroclaw/issues/7543) | Gateway Web Chat 多会话侧边栏支持（已关闭） | 完成多会话 UI 需求跟踪 |
| [#9654](https://github.com/zeroclaw-labs/zeroclaw/issues/9654) | 修复操作者拒绝被模型误读为语义内容的 Bug（已关闭） | 修复 #9423 的兄弟问题，完善拒绝语义链 |
| [#10238](https://github.com/zeroclaw-labs/zeroclaw/issues/10238) | ZeroCode 在 daemon 退出后显示陈旧 Connected 状态（已关闭） | 修复 TUI 状态同步 |
| [#9905](https://github.com/zeroclaw-labs/zeroclaw/issues/9905) | Discord 音频转录 Manager 未绑定活跃 agent provider（已关闭） | 修复语音通道关键路径 |
| [#8518](https://github.com/zeroclaw-labs/zeroclaw/issues/8518) | Discord 辅助 Issue 分诊 SOP 功能（已关闭） | 完成功能规划关闭 |
| [#9811](https://github.com/zeroclaw-labs/zeroclaw/issues/9811) | `/health` 误报未连接 Channel 为健康（已关闭） | 修复可观测性误报 |
| [#9857](https://github.com/zeroclaw-labs/zeroclaw/issues/9857) | JSONL Session 有效文件类型判定不一致（已关闭） | 修复持久化层边界条件 |
| [#9584](https://github.com/zeroclaw-labs/zeroclaw/issues/9584) | 插件安装/列表添加 egress 授权仪式（已关闭） | 安全治理增强 |

### 进行中的关键 PR（待合并）

- **#10610** — 实现 RFC #7155 Phase 0+1（Shell V1 权限策略统一），5 个单关注点提交，是当前安全策略的核心落地。
- **#10197** — ACP 中断轮次进度持久化，修复 Code 会话中断后丢失上下文的问题。
- **#10557** — 将 cron 子系统提取为独立 crate `zeroclaw-cron`，11,386 行代码迁移，架构解耦。
- **#10563** — 重新采样并标记声称未收到回执的工具回复，增强模型行为可验证性。
- **#10596** — ACP 持久化转录分页，支持游标反向遍历大会话。
- **#10589** — `multimodal.max_image_size_mb` 默认值从 5MiB 提升至 20MiB，解决手机照片被静默丢弃问题。
- **#10590/#10591** — 新增 `zeroclaw-dist` 发布目标注册表与 `zeroclaw-bootstrap` MCP 启动器，完善安装分发链路。

> **整体判断：** 今日项目推进显著，安全策略落地（RFC #7155）、ACP 会话稳定性、多模态配置合理化、分发链路加固四条主线并行，项目处于**活跃收敛期**。

---

## 4. 社区热点

### 高讨论 Issue

| Issue | 类型 | 评论数 | 核心诉求 |
|---|---|---|---|
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | RFC | 23 | 细粒度沙箱文件系统策略，解决应用层路径控制与 OS 沙箱后端漂移问题 |
| [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) | Bug | 14 | `verifiable-intent` 在未验证凭证链的情况下执行约束检查，安全隐患 |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker | 14 | 维护者 RFC/设计决策队列，建立治理流程 |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) | RFC | 13 | Gateway 无 Agent 轮次的明文 Channel 发送路由 |
| [#9975](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) | RFC | 12 | Web 包与 Daemon 的 `web_dist_dir` 兼容性契约 |

### 热点分析

**沙箱策略（#6996）** 是当前社区最关注的 RFC 之一，23 条评论表明贡献者对运行时安全边界有强烈诉求，agent risk profile 与 OS 沙箱层之间的漂移已被实际使用者感知。

**可验证意图（#9328）** 暴露了安全审计中的逻辑漏洞——`evaluate_constraints` 依赖调用方传入的 `fulfillment`，而非密码学校验结果，P1 级安全隐患。

**维护者决策队列（#8692）** 反映社区对项目治理透明度的需求，RFC  intake 流程需要制度化。

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 描述 | Fix 状态 |
|---|---|---|---|
| **S1** | [#10609](https://github.com/zeroclaw-labs/zeroclaw/issues/10609) | ZeroCode 忽略启动目录，强制使用 agent workspace 为 cwd | 🆕 今日新开，未修复 |
| **S1** | [#10603](https://github.com/zeroclaw-labs/zeroclaw/issues/10603) | OpenCode provider 未发送 `x-opencode-session` 请求头，导致 Go 模型失败且可能触发账号风控 | 🆕 今日新开，未修复 |
| **S1** | [#9231](https://github.com/zeroclaw-labs/zeroclaw/issues/9231) | Docker 运行时命令嵌套在第二层 Docker 沙箱中 | 进行中 |
| **S2** | [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | 交互式 Agent 会话 context 被硬限制在 32k tokens，忽略 `max_context_tokens=131072` 配置 | 进行中 |
| **S2** | [#10486](https://github.com/zeroclaw-labs/zeroclaw/issues/10486) | Matrix 通道忽略 `[providers.transcription.*]` 与 agent `transcription_provider` 配置 | 进行中 |
| **S2** | [#9983](https://github.com/zeroclaw-labs/zeroclaw/issues/9983) | 无视觉能力的 fallback model 错误报告失败原因 | 进行中（已关闭） |
| **S2** | [#10202](https://github.com/zeroclaw-labs/zeroclaw/issues/10202) | log 桥接缺失导致依赖库（whatsapp-rust 等）的日志静默丢失 | 进行中（已关闭） |
| **S2** | [#9387](https://github.com/zeroclaw-labs/zeroclaw/issues/9387) | Telegram/Slack/Lark/Matrix 交互式审批响应被任意聊天成员接受 | 进行中（已关闭） |

> **稳定性评估：** 今日新增 2 个 S1 级 Bug（#10609、#10603），均影响工作流阻断。已有 4 个 Bug 今日关闭（#10238、#9905、#9811、#9857），修复速度尚可。

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 状态 | 纳入可能性 |
|---|---|---|---|
| 细粒度沙箱文件系统策略 | [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) (RFC) | 讨论中 | 高，P2+high risk |
| Gateway 明文 Channel 发送（无 Agent 轮次） | [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) (RFC) | 已接受 | 高 |
| Web bundle/Daemon `web_dist_dir` 兼容性 | [#9975](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) (RFC Rev 3) | 已接受 | 高 |
| Shell V1 权限策略（RFC #7155） | [#10610](https://github.com/zeroclaw-labs/zeroclaw/pull/10610) (PR) | 进行中 | 已在实现 |
| 单工具 Provider 轮次（交互式 Agent） | [#10222](https://github.com/zeroclaw-labs/zeroclaw/issues/10222) (RFC) | 已接受 | 高，P2 |
| Gemini 语音转语音 Broker Channel | [#10406](https://github.com/zeroclaw-labs/zeroclaw/issues/10406) (Tracker) | 已接受 | 中，需协调 |
| Session 级 Prompt 附件 | [#10405](https://github.com/zeroclaw-labs/zeroclaw/issues/10405) (Tracker) | 已接受 | 中，分阶段实现 |
| ACP 会话内存连续性 | [#10570](https://github.com/zeroclaw-labs/zeroclaw/issues/10570) (Tracker) | 进行中 | 高，与 #10197/#10596 联动 |
| 测试覆盖率跟进（13 个分片） | [#7685](https://github.com/zeroclaw-labs/zeroclaw/issues/7685) (Tracker) | 进行中 | 中，持续任务 |

> **路线图信号：** 安全策略（沙箱、权限、可验证意图）和 ACP/Code 会话体验是下一阶段核心，多路 RFC 并行推进表明项目进入**架构治理密集期**。

---

## 7. 用户反馈摘要

- **Context 限制被硬编码**（#10068）：用户配置了 131072 tokens 的上下文上限，但交互式会话被静默截断在 32k，导致长会话异常压缩。这是配置失效类问题，直接影响可信度。
- **OpenCode provider 兼容性断裂**（#10603）：ZeroClaw 未向 OpenCode 中继发送必要 header，导致 Go 模型请求失败且可能触发账号风控——用户反映"工作流被阻断"。
- **零代码 TUI 启动目录丢失**（#10609）：用户从特定目录启动 `zerocode`，期望在该目录运行 agent，但被强制切换到 agent workspace，破坏本地工作流。
- **Docker 嵌套沙箱**（#9231）：在自定义配置下，运行时命令被嵌套进第二层 Docker，增加复杂性与性能开销。
- **图片上传大小限制过低**（#10589 fix）：用户反映 5MiB 默认限制导致普通手机照片被静默丢弃，PR #10589 已将默认值提升至 20MiB 天花板，修复中。
- **Health 检查误报**（#9811）：Telegram channel 未连接时 `/health` 仍报告 healthy，影响监控可靠性（已关闭）。

---

## 8. 待处理积压

| Issue | 类型 | 创建时间 | 未响应时长 | 备注 |
|---|---|---|---|---|
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | RFC（高优先级） | 2026-05-28 | ~3.5 个月 | 沙箱策略 RFC，23 条评论，需维护者最终裁决 |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker | 2026-07-04 | ~2 个月 | 维护者决策队列，治理基础设施 |
| [#7108](https://github.com/zeroclaw-labs/zeroclaw/issues/7108) | CI 优化 | 2026-06-02 | ~3 个月 | PR CI 关键路径优化，15-20 分钟耗时问题 |
| [#7685](https://github.com/zeroclaw-labs/zeroclaw/issues/7685) | 测试覆盖率 | 2026-06-15 | ~2.5 个月 | 13 个分片的测试跟进，长期任务 |
| [#10330](https://github.com/zeroclaw-labs/zeroclaw/issues/10330) | RFC 实现索引 | 2026-08-25 | ~10 天 | 已接受 RFC 的实现追踪映射 |

---

*报告生成时间：2026-09-04 | 数据来源：ZeroClaw GitHub API | 分析师：Agnes-2.0-Flash*

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*