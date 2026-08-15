# OpenClaw 生态日报 2026-08-15

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-15 01:37 UTC

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
**日期：2026-08-15** | 数据来源：github.com/openclaw/openclaw

---

## 1. 今日速览

过去24小时项目保持高度活跃：共500条Issue更新（活跃485 / 关闭15）与500条PR更新（待合并400 / 已合并100），社区参与度高。无新版本发布，但100条PR已合并或关闭，涵盖稳定性修复、UI优化和安全机制强化。核心关注点集中在Gateway内存泄漏、WhatsApp/LINE消息丢失、以及DeepSeek/Kimi流式推理渲染等生产级稳定性问题上。整体项目健康度良好，但内存与消息传递类Bug需维护者优先响应。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的100条PR中，以下对稳定性与体验影响较大：

| PR | 类型 | 说明 |
|---|---|---|
| [#123914](https://github.com/openclaw/openclaw/pull/123914) | Bug Fix | 修复无Agent的cron任务在添加第二个Agent后全部失败的问题，含Memory Dreaming Promotion内置调度 |
| [#123901](https://github.com/openclaw/openclaw/pull/123901) | Bug Fix | 限制Gateway worker bundle缓存无限增长，解决长期开发/升级周期中缓存无生命周期管理的问题 |
| [#123913](https://github.com/openclaw/openclaw/pull/123913) | Refactor | 消除SQLite会话适配器一致性测试中的重复运行，提升测试效率 |
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | Security | 新增插件安装策略警告确认机制，CLI与Control UI均支持交互式确认 |
| [#123541](https://github.com/openclaw/openclaw/pull/123541) | Bug Fix | 修复长生命周期会话执行`branches.list`时事件循环阻塞约12秒的问题 |

项目整体在**定时任务可靠性、缓存治理、安全加固、性能瓶颈修复**四个方向持续推进。

---

## 4. 社区热点

**Issue 热度排行（评论数 Top 5）：**

1. [#121058](https://github.com/openclaw/openclaw/issues/121058) — Silent reply failures recurring after #116277 closed（94评论）
   - 监控cron持续记录静默回复失败，已被关闭的修复未根除，社区高度关注

2. [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging by Source（51评论）
   - 提议按来源为agent记忆条目打信任标签，防止memory poisoning攻击，长期需求

3. [#42475](https://github.com/openclaw/openclaw/issues/42475) — Per-agent cost budget enforcement at gateway（25评论，1👍）
   - 网关层per-agent日/月成本上限，已有对应PR #120491 在推进

4. [#91588](https://github.com/openclaw/openclaw/issues/91588) — Gateway Memory Leak: RSS 350MB→15.5GB导致OOM（24评论，1👍）
   - P0级内存泄漏，RSS数天内从350MB飙升至15.5GB，触发反复OOM重启循环

5. [#91009](https://github.com/openclaw/openclaw/issues/91009) — Codex PreToolUse hook 产生CPU绑定进程并卡死网关RPC（20评论，2👍）
   - Codex集成在2026.6.1版本引入，`openclaw-hooks`进程占满CPU并阻塞网关

**PR 热度：** UI侧边栏改造系列（#123597、#123666、#123656、#123582、#123645、#123682、#123874）由同一作者连续提交，显示Control UI重构正在密集推进。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 标题 | 是否已有 Fix PR |
|---|---|---|---|
| 🐚 P0 | [#91588](https://github.com/openclaw/openclaw/issues/91588) | Gateway内存泄漏：RSS 350MB→15.5GB，OOM重启循环 | 暂无 |
| 🦞 P1 | [#91009](https://github.com/openclaw/openclaw/issues/91009) | Codex PreToolUse hook 产生CPU绑定进程并阻塞网关RPC | 暂无 |
| 🦞 P1 | [#121953](https://github.com/openclaw/openclaw/issues/121953) | Cron agent on DeepSeek 卡住：`[cron:...]`前缀被API边缘降级 | 暂无 |
| 🦞 P1 | [#48003](https://github.com/openclaw/openclaw/issues/48003) | `messages.queue.mode: "steer"` 不在活跃turn中注入消息 | 有 PR #120491 部分相关 |
| 🦞 P1 | [#87109](https://github.com/openclaw/openclaw/issues/87109) | Gateway heap 空闲增长至1073MB+，cron静默失败 | 暂无 |
| 🦪 P2 | [#53628](https://github.com/openclaw/openclaw/issues/53628) | 安装skill时`$XDG_CONFIG_HOME`未展开（Docker环境） | 暂无 |
| 🦞 P2 | [#48920](https://github.com/openclaw/openclaw/issues/48920) | Live Docs超前于发布版本（IsolatedSessions） | 暂无 |
| 🦪 P2 | [#120563](https://github.com/openclaw/openclaw/issues/120563) | 自定义/Ollama提供商每轮固定上下文，历史不发送 | 暂无 |
| 🦞 P2 | [#123073](https://github.com/openclaw/openclaw/issues/123073) | `openclaw update` dev通道报`EUNSUPPORTEDPROTOCOL`（pnpm workspace） | 暂无 |
| 🦞 P2 | [#88079](https://github.com/openclaw/openclaw/issues/88079) | WebChat中Kimi Code/DeepSeek Reasoner推理流未渲染 | 暂无 |
| 🦪 P2 | [#50611](https://github.com/openclaw/openclaw/issues/50611) | `reserveTokensFloor == contextWindow` 时memory flush永不触发 | 暂无 |
| 🦞 P1 | [#119270](https://github.com/openclaw/openclaw/issues/119270) | 文件工具删除目标路径前导`@`，写入/删除错误文件 | 暂无 |
| 🦞 P1 | [#91941](https://github.com/openclaw/openclaw/issues/91941) | Feishu流式卡片全量更新导致长回复严重延迟 | 暂无 |
| 🦪 P2 | [#121046](https://github.com/openclaw/openclaw/issues/121046) | `temporalDecay`不适用于`memory/dreaming/`子目录文件 | 暂无 |
| 🦞 P1 | [#92186](https://github.com/openclaw/openclaw/issues/92186) | 前台回复围栏模式导致早期群消息回复丢失 | 暂无 |
| 🐚 P0 | [#51049](https://github.com/openclaw/openclaw/issues/51049) | k3s嵌套容器中WhatsApp入站消息丢失 | 暂无 |
| 🦞 P2 | [#86012](https://github.com/openclaw/openclaw/issues/86012) | LINE消息因reply token过期+无push回退而静默丢失 | 暂无 |

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 关联 PR | 纳入下一版本可能性 |
|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 按来源为记忆打信任标签，防止memory poisoning | 暂无 | 低（无PR，长期RFC） |
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | 网关层 per-agent 成本预算 | [#120491](https://github.com/openclaw/openclaw/pull/120491) | **高**（已有PR，P1） |
| [#50093](https://github.com/openclaw/openclaw/issues/50093) | WhatsApp重连后回填丢失消息 | 暂无 | 中（无PR，但需求明确） |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | Agent自触发上下文压缩 | 暂无 | 中 |
| [#54373](https://github.com/openclaw/openclaw/issues/54373) | Context Provenance 元数据注入 | 暂无 | 低（RFC阶段） |
| [#71142](https://github.com/openclaw/openclaw/issues/71142) | Control UI可配置上传大小限制（当前硬编码5MB） | 暂无 | 中 |
| [#75947](https://github.com/openclaw/openclaw/issues/75947) | 基于UX评分的UI重新设计 | 暂无 | 中（与UI改造系列PR方向一致） |
| [#50900](https://github.com/openclaw/openclaw/issues/50900) | per-pattern会话维护保留规则 | 暂无 | 低 |
| [#87362](https://github.com/openclaw/openclaw/issues/87362) | TaskFlow生命周期hook事件暴露给插件 | 暂无 | 中 |
| [#54128](https://github.com/openclaw/openclaw/issues/54128) | 本地embedding `node-llama-cpp` 的maxThreads配置 | 暂无 | 低 |

**明确信号**：per-agent成本预算（#42475 / #120491）和UI侧边栏重构系列PR是当前推进力度最大的两个方向。

---

## 7. 用户反馈摘要

**核心痛点：**

- **消息丢失是最大不满来源**：WhatsApp（#51049、#50093、#92186）、LINE（#86012）、Telegram贴纸（#120735）等多渠道均存在消息静默丢失或延迟问题，直接影响生产可用性。
- **内存泄漏严重影响稳定性**：#91588（RSS至15.5GB）和#87109（heap至1073MB）均为长期存在的内存问题，用户反馈重启后短期恢复但问题会重现。
- **Cron任务可靠性差**：DeepSeek前缀降级（#121953）、无Agent后cron失败（#123914已修复）、隔离会话静默失败等问题反复出现。
- **WebChat渲染问题**：Kimi/DeepSeek推理流不显示（#88079）、assistant回复早于用户消息显示（#95566）、Feishu流式卡片延迟（#91941）影响用户体验。
- **文档与版本不同步**：#48920 指出Live Docs超前于实际发布版本，导致用户配置无效。

**正面反馈：**
- #120491（per-turn发送预算保护）和#97135（隐藏失败工具进度）获得社区认可，解决重复发送和状态混乱问题。
- UI侧边栏重构系列PR（#123597等）被用户积极跟进，显示对Control UI体验改进的期待。

---

## 8. 待处理积压

| Issue | 创建时间 | 状态 | 风险 |
|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging | 2026-02-03 | 无PR，6个月未推进 | 安全功能长期缺失 |
| [#42475](https://github.com/openclaw/openclaw/issues/42475) — Per-agent cost budget | 2026-03-10 | 有PR #120491 但未合并 | 成本管控核心需求 |
| [#50093](https://github.com/openclaw/openclaw/issues/50093) — WhatsApp消息回填 | 2026-03-19 | 无PR，5个月 | 生产消息可靠性 |
| [#91588](https://github.com/openclaw/openclaw/issues/91588) — Gateway内存

---

## 横向生态对比



# 2026-08-15 个人 AI 助手/自主智能体开源生态横向分析报告

## 1. 生态全景

2026年8月，个人AI助手与自主智能体开源生态呈现**"头部高迭代、边缘稳收敛"**的分层格局。OpenClaw、IronClaw、ZeroClaw、CoPaw、Hermes Agent 五大项目保持高频开发，核心竞争点从功能堆砌转向**生产级稳定性**（内存泄漏、消息丢失、自动化可靠性）与**安全架构治理**（预算原子性、多租户隔离、渠道授权）。零Claw通过RFC驱动安全基础设施决策，NanoBot与LobsterAI已进入体验打磨期，NullClaw、Moltis、ZeptoClaw处于低频维护状态。整体生态正从"可用"迈向"可信可用"。

---

## 2. 各项目活跃度对比

| 项目 | Issue (24h) | PR (24h) | Release | 健康度 | 核心焦点 |
|------|-------------|----------|---------|--------|----------|
| **OpenClaw** | 500 | 500 | — | 🟡 中（P0内存泄漏待修） | Gateway稳定性、消息可靠性、Cron |
| **IronClaw** | 25 | 47 | — | 🟢 良好 | v1.3.0自动化、Reborn WebUI |
| **ZeroClaw** | 33 | 50 | — | 🟢 良好（RFC审议期） | 安全架构、渠道授权、Windows CI |
| **CoPaw** | 50 | 41 | — | 🟢 良好（Issue关闭率74%） | 技能系统、插件隔离、Windows |
| **Hermes Agent** | 50 | 50 | — | 🟢 良好 | Discord集成、多租户、Skills生态 |
| **LobsterAI** | — | 27 | ✅ 2026.8.14 | 🟢 良好 | Sidebar体验、Cowork交互 |
| **NanoClaw** | 2 | 11 | — | 🟡 中（AVX2兼容问题） | 签名验证、Dial通道、安装兼容 |
| **NanoBot** | 3 | 22 | — | 🟢 良好 | WebUI重构、Pyright strict |
| **PicoClaw** | 3 | 9 | — | 🟢 良好 | MCP容错、多渠道对齐 |
| **Moltis** | 0 | 2 | — | 🟡 中低 | Slack卡片、持久化连接器 |
| **NullClaw** | 0 | 1 | — | 🟢 平稳收敛 | 配置灵活性 |
| **ZeptoClaw** | 0 | 0 | — | ⚪ 无活动 | — |

---

## 3. OpenClaw 在生态中的定位

**规模优势**：OpenClaw以500 Issue/500 PR的绝对数量领跑生态，社区参与深度（内存泄漏P0、WhatsApp消息丢失等生产级问题高频讨论）反映其**最大用户基数与最复杂部署场景**。

**技术路线差异**：
- 相比 **ZeroClaw** 的"安全RFC驱动"，OpenClaw走**"快速迭代+问题驱动"**路线，PR吞吐量高但RFC治理较弱
- 相比 **IronClaw** 的"结构化自动化规范"，OpenClaw聚焦**Gateway层稳定性**（内存/缓存/消息队列）
- 相比 **CoPaw/Hermes** 的"技能生态"路线，OpenClaw更侧重**多渠道消息网关**（WhatsApp/LINE/Telegram/Feishu）

**社区规模对比**（按Issue/PR活跃度估算）：
| 梯队 | 项目 | 特征 |
|------|------|------|
| S级 | OpenClaw | 生产级部署，Issue讨论深度高 |
| A级 | IronClaw、ZeroClaw、CoPaw、Hermes | 活跃开发+功能竞争 |
| B级 | LobsterAI、NanoBot、PicoClaw | 体验打磨+垂直场景 |
| C级 | NanoClaw、Moltis、NullClaw | 特定功能/低频维护 |

---

## 4. 共同关注的技术方向

### 4.1 多渠道消息可靠性（生产级核心痛点）
| 项目 | 具体诉求 |
|------|----------|
| OpenClaw | WhatsApp/LINE/Telegram消息静默丢失（#51049、#86012、#121058） |
| Hermes Agent | Windows Desktop重启后WeChat/QQ/Telegram静默（#83683） |
| PicoClaw | Telegram Session管理与多渠道对齐（#3307） |
| ZeroClaw | 渠道授权绑定与Telegram/Slack/Lark身份校验（#9574） |
| IronClaw | Slack状态误报、Telegram MP4上传失败（#7660、#7662） |

### 4.2 内存与资源管理
| 项目 | 具体诉求 |
|------|----------|
| OpenClaw | Gateway RSS内存泄漏（#91588，P0）、heap空闲增长（#87109） |
| NanoBot | Anthropic流式超时治理、会话状态竞态 |
| ZeroClaw | Token预算原子性（#9996）、历史裁剪token消耗透明化（#9713） |
| CoPaw | 后台运行/Daemon模式缺失（#7010） |

### 4.3 自动化与调度可靠性
| 项目 | 具体诉求 |
|------|----------|
| OpenClaw | Cron任务静默失败、DeepSeek前缀降级（#121953、#121058） |
| IronClaw | 自动化"hit-or-miss"问题、结构化执行规范（#6879、#7532） |
| ZeroClaw | Cron并行测试竞争（#9965） |
| CoPaw | 定时任务不投递选项（#2554） |

### 4.4 安全与权限治理
| 项目 | 具体诉求 |
|------|----------|
| ZeroClaw | 安全架构RFC系列（#6971、#7141、#7155）、高熵检测误红（#9486） |
| OpenClaw | 插件安装策略警告确认（#116489）、Memory Trust Tagging（#7707） |
| CoPaw | 插件生态隔离危机（#7025 Creator插件导致全部失效） |
| Hermes Agent | 多租户内存隔离（#34352） |

### 4.5 跨平台兼容性
| 项目 | 具体诉求 |
|------|----------|
| ZeroClaw | Windows 74项测试失败、CI仅跑Linux（#7462） |
| NanoClaw | AVX2依赖导致无AVX2 CPU上SIGILL（#3245） |
| CoPaw | Windows桌面端自动更新、模型配置保存失败（#2846、#6806） |
| Hermes Agent | Windows CRLF换行符破坏MEMORY.md（#85825） |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构 |
|------|----------|----------|----------|
| **OpenClaw** | 多渠道消息网关 + Gateway稳定性 | 生产级部署用户、企业集成 | Go/Rust混合，Gateway-worker架构 |
| **IronClaw** | 结构化自动化 + Reborn WebUI | 自动化工作流构建者 | TypeScript + Rust，pluggable-memory架构 |
| **ZeroClaw** | 安全架构治理 + 渠道授权 | 安全敏感用户、长期任务场景 | Rust，RFC驱动决策 |
| **CoPaw** | 技能系统 + 插件生态 | AgentScope用户、中文社区 | Python，插件隔离架构 |
| **Hermes Agent** | Discord集成 + Skills生态 | Discord用户、多租户场景 | TypeScript，Discord-first设计 |
| **LobsterAI** | 多Agent协作 + Sidebar体验 | 国内用户、桌面端用户 | TypeScript，YD生态集成 |
| **NanoBot** | WebUI交互 + 类型安全 | 开发者、类型安全追求者 | TypeScript，Pyright strict |
| **PicoClaw** | 轻量化 + 嵌入式 | 边缘计算、Raspberry Pi用户 | Rust，<10MB RAM设计 |
| **NanoClaw** | 签名验证 + 多通道 | 安全审计、Dial语音场景 | Node.js，cosign签名链 |
| **Moltis** | Slack原生卡片 + 持久化连接器 | 企业Slack用户、日历/邮件集成 | TypeScript，channel-neutral架构 |
| **NullClaw** | 配置灵活性 | 特定部署场景 | SQLite内存数据库 |

---

## 6. 社区热度与成熟度分层

### 🔥 S级：快速迭代期
| 项目 | 特征 | 阶段判断 |
|------|------|----------|
| **OpenClaw** | 500/500 Issue/PR，P0问题驱动，社区参与深度最高 | 功能成熟但稳定性攻坚期 |
| **IronClaw** | v1.3.0自动化冲刺，QA bug bash收尾 | 从功能构建向质量夯实过渡 |
| **ZeroClaw** | RFC审议密集，安全架构决策期 | 架构治理与功能开发并行 |
| **CoPaw** | 高Issue关闭率(74%)，技能系统动态化 | 功能快速迭代+生态成型 |
| **Hermes Agent** | God File拆解完成，Skills生态扩张 | 架构重构后功能填充期 |

### 🟡 A级：体验打磨期
| 项目 | 特征 | 阶段判断 |
|------|------|----------|
| **LobsterAI** | 有版本发布，UI/UX持续优化 | 功能稳定，体验精细化 |
| **NanoBot** | Pyright strict收尾，WebUI重构 | 技术债清理+交互优化 |
| **PicoClaw** | MCP容错修复，多渠道对齐 | 生产级稳定性加固 |
| **NanoClaw** | 签名验证链路完善，Dial通道扩展 | 安全基础设施+场景扩展 |

### 🟢 B级：低频维护/特定场景
| 项目 | 特征 | 阶段判断 |
|------|------|----------|
| **Moltis** | 2 PR/0 Issue，核心开发者驱动 | 功能积累期，社区待激活 |
| **NullClaw** | 1 PR/0 Issue，平稳收敛 | 维护模式 |
| **ZeptoClaw** | 无活动 | 休眠/暂停 |

---

## 7. 值得关注的趋势信号

### 7.1 从"功能可用"到"生产可信"
**信号**：OpenClaw P0内存泄漏（#91588 RSS 350MB→15.5GB）、ZeroClaw安全RFC系列、CoPaw插件隔离危机，表明生态已进入**稳定性与安全性双轨攻坚期**。
**参考价值**：开发者应优先关注内存管理、并发安全、插件隔离等生产级问题，而非单纯功能堆砌。

### 7.2 多渠道消息可靠性成为胜负手
**信号**：5个项目（OpenClaw、Hermes、PicoClaw、ZeroClaw、IronClaw）均报告消息丢失/延迟/状态误报问题，WhatsApp、LINE、Telegram、Feishu等渠道稳定性直接影响生产可用性。
**参考价值**：消息网关层应建立**死信队列+重试+状态同步**机制，而非依赖渠道原生可靠性。

### 7.3 自动化可靠性是下一竞争高地
**信号**：OpenClaw Cron静默失败、IronClaw "hit-or-miss"、ZeroClaw cron竞争测试，表明**定时任务调度**是当前自动化落地的核心瓶颈。
**参考价值**：结构化执行规范（如IronClaw #7532）取代纯prompt驱动，是提升自动化可预测性的关键方向。

### 7.4 安全架构从"补丁式"转向"RFC驱动"
**信号**：ZeroClaw通过RFC #6971/#7141/#7155建立安全决策框架，OpenClaw通过#116489插件安装确认机制、#7707 Memory Trust Tagging推进安全治理。
**参考价值**：安全能力应从"功能点后补"转向"架构层设计"，RFC机制可作为社区共识构建的有效工具。

### 7.5 跨平台兼容性是隐形技术债
**信号**：ZeroClaw Windows 74测试失败、NanoClaw AVX2依赖、Hermes Windows CRLF问题、CoPaw Windows自动更新缺失，**Windows平台成为各项目的共同痛点**。
**参考价值**：CI应覆盖多平台（尤其Windows），代码中避免平台硬编码（换行符、路径分隔符、命令语法）。

### 7.6 插件/技能生态的"双刃剑"效应
**信号**：CoPaw #7025 Creator插件导致全部失效、Hermes Skills Phase 0+1.3合并但索引老化（#66616），表明**生态扩张与系统稳定性存在张力**。
**参考价值**：插件隔离、依赖版本管理、健康探针是生态治理的基础设施，需在规模扩张前建立。

---

**报告生成时间**：2026-08-15 | **分析师**：Agnes-2.0-Flash (Sapiens AI)

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 | 2026-08-15

## 1. 今日速览
过去 24 小时 NanoBot 保持高频迭代，累计处理 PR 22 条（待合并 14、已合并/关闭 8）、Issues 3 条（活跃 1、已关闭 2）。开发重心集中在 WebUI 交互精细化、会话状态竞态修复与 Anthropic 流式超时治理，同步推进 Pyright strict 类型安全收尾。项目整体健康度良好，无阻塞性新 bug 出现，技术债清理与体验打磨同步进行，符合稳步演进节奏。

## 2. 版本发布
无。

## 3. 项目进展
今日已合并/关闭的关键 PR 共 6 条（另有 2 条未在当前列表展示），主要推进方向：
- **Anthropic 流式超时修复** `#5392`：纠正 `NANOBOT_STREAM_IDLE_TIMEOUT_S` 被误作总超时的问题，避免长文本生成主动中断。[链接](https://github.com/HKUDS/nanobot/pull/5392)
- **WebUI 分组与视觉重构** `#5395`、`#5393`：统一会话分组术语与拖拽逻辑，重构侧边栏层级、连接器线条与过渡动效，提升多会话管理效率。[链接](https://github.com/HKUDS/nanobot/pull/5395) | [链接](https://github.com/HKUDS/nanobot/pull/5393)
- **OAuth 状态可见性** `#4689`：跨 CLI/WebUI/Runtime 暴露 Provider 状态与 Token 过期预警，降低多 Provider 配置盲区。[链接](https://github.com/HKUDS/nanobot/pull/4689)
- **Skills 显式上下文加载** `#5018`：修复 `ContextBuilder` 忽略 `skill_names` 的缺陷，支持按需预加载技能而非仅依赖 `always: true`。[链接](https://github.com/HKUDS/nanobot/pull/5018)
- **Agent 知识图谱探索** `#5390`：初步集成 Agent 与知识图谱路径。[链接](https://github.com/HKUDS/nanobot/pull/5390)

项目正从“功能快速迭代”向“底层稳定性与交互体验并重”过渡，近期合并节奏健康，无架构级回退。

## 4. 社区热点
- **Pyright strict 逐文件收窄** `#5161`（Issue） / `#5396`（PR）：用户与维护者高度关注类型安全治理，

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-08-15 | 数据来源：github.com/nousresearch/hermes-agent**

---

## 1. 今日速览

Hermes Agent 今日保持高频开发节奏，过去24小时共产生50条 Issue 与50条 PR，其中46条 Issue 处于新开/活跃状态，23条 PR 已合并或关闭，社区贡献活跃度高。项目当前重点围绕 **Discord Omniscience 功能对齐战役**、**多租户内存隔离**、以及 **Desktop 应用稳定性修复** 三线并行推进。无新版本发布，但技能生态系统（Skills）持续扩容，新增安全扫描、数据工程、社交媒体等类别。整体项目健康度良好，Bug 修复与功能开发节奏均衡。

---

## 2. 版本发布

今日无新版本发布（Releases: 0）。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 摘要 |
|---|---|---|
| [#83785](https://github.com/NousResearch/hermes-agent/issues/83785) [CLOSED] | Bug | 持久化 row_id 寻址修复 rewind/edit/regenerate 截断问题（#82959 抢救版） |
| [#84859](https://github.com/NousResearch/hermes-agent/issues/84859) [CLOSED] | Bug | 修复 browser-use 子进程因继承父 venv PYTHONPATH 导致 pydantic_core ABI 不匹配崩溃 |
| [#86374](https://github.com/NousResearch/hermes-agent/issues/86374) [CLOSED] | Bug | 修复 Dashboard/Desktop 中 slash_worker PATH 缺失 Hermes 工具目录，恢复 browser_exec 发现能力 |
| [#86572](https://github.com/NousResearch/hermes-agent/issues/86572) [CLOSED] | Bug | 流式中断降级：当 provider 流式路径持续失败时，将反复流 DROP 事件升级至 fallback 链 |
| [#67017](https://github.com/NousResearch/hermes-agent/issues/67017) [CLOSED] | Bug | 修复 anthropic_prompt_cache_policy 缺少位置参数 agent 导致的运行时崩溃 |
| [#86562](https://github.com/NousResearch/hermes-agent/issues/86562) [CLOSED] | Feature | Skills Phase 0+1.3 合并：新增 data-engineering / cloud-native / security / social-media 等类别，106 个社交媒体技能 |
| [#86576](https://github.com/NousResearch/hermes-agent/issues/86576) [CLOSED] | Bug | 跨 provider 委托及模型切换时剥离加密 reasoning tokens，防止上下文污染 |

**进展评估：** 共7项重要 PR 今日完成闭环，涵盖稳定性修复（3）、基础设施完善（2）、安全增强（1）和代码清理（1）。Skills 生态的 Phase 0 合并是今日最大功能进展，为后续 skill 注册表 CI 和更多类别扩展奠定了基础。

---

## 4. 社区热点

### 讨论最活跃的 Issues

| Issue | 评论数 | 类型 | 核心议题 |
|---|---|---|---|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) | 78 | Epic/Refactor | 全量 God File 拆解完成（20/20），架构重构收官之战 |
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) | 31 | Feature | 多租户内存隔离：当前 hook 系统绕过导致租户隔离不可行 |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 31 | Bug | Skills 索引老化：index 29.8h 超出26h阈值，健康探针告警 |
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | 27 | Bug/P1 | Windows Desktop 重启后 gateway 不自动恢复，WeChat/QQ/Telegram 静默 |

**热点分析：**
- **#78647** 作为史诗级重构任务已完整闭环（20/20），78条评论说明社区对代码质量高度关注，该项目确立了"god file 绝不回退"的仓库政策。
- **#34352** 是多租户场景的核心阻塞问题，已有生产环境验证的修复方案等待上游整合，3个 👍 反映社区强烈诉求。
- **#83683** 是 Windows Desktop 用户的重大回归 Bug，影响消息网关生命周期管理，P1 优先级表明紧迫性。
- **#66616** 是自动化监控告警， Skills Hub 索引延迟可能影响用户发现能力。

---

## 5. Bug 与稳定性

### P0 级
| Issue | 摘要 | Fix PR |
|---|---|---|
| [#85825](https://github.com/NousResearch/hermes-agent/issues/85825) [CLOSED] | Windows 上 `memory(replace/remove)` 因 CRLF 换行符不匹配静默覆盖整个 MEMORY.md | —（已关闭，待确认合并） |

### P1 级
| Issue | 摘要 | Fix PR |
|---|---|---|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | Windows Desktop 重启后 gateway 被杀掉且不重新启动，导致消息平台静默 | — |

### P2 级
| Issue | 摘要 | Fix PR |
|---|---|---|
| [#84969](https://github.com/NousResearch/hermes-agent/issues/84969) | Persistent Docker 复用忽略不可变配置漂移 | — |
| [#85834](https://github.com/NousResearch/hermes-agent/issues/85834) | Desktop per-profile SSH 远程会话恢复报 "Session not found" | — |
| [#79625](https://github.com/NousResearch/hermes-agent/issues/79625) | Desktop sessions 忽略 `checkpoints.enabled`，文件系统快照静默禁用 | — |
| [#86558](https://github.com/NousResearch/hermes-agent/issues/86558) | `hermes gateway restart` 在 XDG_RUNTIME_DIR 跨用户泄漏时抛 PermissionError 崩溃 | — |
| [#30449](https://github.com/NousResearch/hermes-agent/issues/30449) | DeepSeek V4 reasoning_content 和 reasoning_effort 未进入 OpenAI 兼容 SSE 流 | — |
| [#86510](https://github.com/NousResearch/hermes-agent/issues/86510) | `read_file` 工具对无尾换行文件 total_lines off-by-one | — |
| [#86513](https://github.com/NousResearch/hermes-agent/issues/86513) | file_tools 对远程/容器后端在宿主机文件系统做去重和新鲜度检查 | — |

### 已有关闭的 Bug（今日修复）
- **#85825** — Windows CRLF memory 覆盖 Bug
- **#83845** — slash_worker PATH 缺失导致 browser_exec 失败
- **#86576** — 跨 provider 委托时 encrypted reasoning tokens 泄露

**稳定性评估：** 今日共报告14个 Bug，其中2个 P2 及以上级别尚未有公开 Fix PR，Desktop/Windows 平台相关问题占比高（6/14），是下一阶段稳定性修复的重点方向。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 诉求摘要 | 纳入下一版本可能性 |
|---|---|---|---|
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) | Feature | 多租户内存隔离，绕过当前 hook 系统限制 | ⭐⭐⭐ 高 — 已有生产验证方案 |
| [#4064](https://github.com/NousResearch/hermes-agent/issues/4064) | Feature | CLI 鼠标支持（光标定位、滚动） | ⭐⭐ 中 — 用户长期诉求，配置开关方案明确 |
| [#67798](https://github.com/NousResearch/hermes-agent/issues/67798) | Feature | 将 lifecycle hooks 提升为跨所有执行面的共享运行时契约 | ⭐⭐⭐ 高 — 架构一致性需求，影响面广 |
| [#85622](https://github.com/NousResearch/hermes-agent/issues/85622) | Bug | 外部 memory provider 覆盖内置 MEMORY.md/USER.md，违反"additive"契约 | ⭐⭐⭐ 高 — 行为与文档不符，应优先修复 |
| [#86561](https://github.com/NousResearch/hermes-agent/issues/86561) | Feature | 支持将已有会话移入/关联到 Project | ⭐⭐ 中 — 用户体验改善，优先级中等 |
| [#85159](https://github.com/NousResearch/hermes-agent/issues/85159) | Feature | Desktop 中 file:// 链接路由至 #media: 渲染 | ⭐ 低 — 功能补全，非阻塞性 |
| [#86578](https://github.com/NousResearch/hermes-agent/pull/86578) | Test | Anthropic prompt cache policy 回归测试 | ⭐⭐⭐ 高 — 配合 #67017 已合并 |

**路线图信号：** Discord Omniscience 战役（#79564）下有8个 Feature Issue 今日并行推进（I1/I3/I4/V1/W3/R3/T5），测试通过率良好，预计将成为下一版本 Discord 集成的核心增量。Skills 生态 Phase 0+1.3 已合并，下一步预期是注册表 CI 和更多垂直类别。

---

## 7. 用户反馈摘要

**主要痛点：**
1. **Windows Desktop 稳定性薄弱**：多个用户反馈重启后 gateway 不恢复（#83683）、SSH 会话恢复失败（#85834）、checkpoints 静默失效（#79625）、memory 操作因 CRLF 破坏数据（#85825）。Windows 平台体验显著落后于 macOS/Linux。
2. **多租户场景缺乏原生支持**：#34352 明确指出当前 memory 操作完全绕过 hook 系统，租户隔离需要 fork 核心代码，社区已有生产级修复方案但尚未合入。
3. **跨 provider 模型切换上下文污染**：#86576 报告 reasoning tokens 跨 provider 传递时成为无效 blob，已在今日关闭，但反映了多 provider 协作的设计缺陷。
4. **Skills 索引老化影响可用性**：#66616 自动探针检测到索引超过26小时阈值，用户无法获取最新 skill 列表。

**正面反馈：**
- God File 拆解 Epic（#78647）获得社区认可，78条评论无负面争议。
- Skills 生态扩展受到欢迎，新增安全扫描、数据工程等类别填补了空白。

---

## 8. 待处理积压

### 需维护者关注的高优先级 Issue

| Issue | 阻塞原因 | 建议行动 |
|---|---|---|
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) | 多租户内存隔离，生产环境已验证修复待合入 | 安排代码审查，评估合入路径 |
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | P1 Windows Desktop gateway 重启回归 | 定位 Desktop 启动流程中 gateway 生命周期管理逻辑 |
| [#85622](https://github.com/NousResearch/hermes-agent/issues/85622) | 外部 memory provider 违反 additive 契约 | 修复 memory provider 初始化顺序，确保内置 memory 始终注入 |
| [#79625](https://github.com/NousResearch/hermes-agent/issues/79625) | Desktop checkpoints 配置被忽略 | 排查 Desktop 后端与 gateway 的 config 传递链路 |
| [#67798](https://github.com/NousResearch/hermes-agent/issues/67798) | Lifecycle hooks 需跨执行面对齐 | 架构决策：将 HookRegistry 从 gateway 所有权升级为运行时级 |

### 长期未响应 Issue
- **#4064**（CLI 鼠标支持）：创建已超过4个月，需求明确且方案清晰，建议排入下一迭代。
- **#68876**（Desktop provider/model 切换不同步）：UI 状态与 live request 脱节，影响用户体验。

---

*报告生成时间：2026-08-15 | 分析模型：Agnes-2.0-Flash (Sapiens AI)*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-15

## 1. 今日速览

过去 24 小时内，PicoClaw 项目保持**高活跃度**：9 条 PR 更新（5 条已合并/关闭），3 条 Issue 更新（2 条已关闭）。今日核心进展集中在 **MCP 稳定性修复** 与 **多渠道消息支持增强**，反映出项目正从功能扩展向生产级稳定性过渡。无新版本发布，但多个独立修复已累积待合并，整体项目健康度良好，社区贡献节奏稳定。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

今日合并/关闭的 PR 是推动项目实质进展的核心：

| PR | 状态 | 说明 |
|----|------|------|
| [#3283](https://github.com/sipeed/picoclaw/pull/3283) | ✅ 已合并 | 新增**钉钉渠道图片消息支持**，实现优雅降级机制，扩展企业 IM 渠道能力 |
| [#3279](https://github.com/sipeed/picoclaw/pull/3279) | ✅ 已合并 | 修复 **Seahorse tool-call 格式泄漏**至 LLM 摘要的问题，提升对话上下文质量 |
| [#3271](https://github.com/sipeed/picoclaw/pull/3271) | ✅ 已合并 | 刷新 **9 个 provider 的默认模型列表**至 2026-07 最新 ID，支持 OpenAI `gpt-5.6-*` 系列与 Anthropic 新模型 |
| [#3270](https://github.com/sipeed/picoclaw/pull/3270) | ✅ 已合并 | 新增 **DashScope（百炼）TTS 提供商** 及**微信音频文件发送**，完善多模态输出能力 |
| [#3303](https://github.com/sipeed/picoclaw/pull/3303) | ✅ 已合并 | 依赖更新：`actions/stale` v10 → v11，保持 CI 工具链同步 |

> **项目推进评估**：今日合并的 PR 覆盖了**渠道扩展（钉钉/微信）、模型新鲜度、对话质量修复**三个关键维度，为即将发布的版本积累了重要稳定性与功能性改进。

---

## 4. 社区热点

### 🔥 Issue #3269 — MCP 连接失败导致 Agent Loop 挂起（最受关注）
- **状态**：🟢 OPEN | **评论**：5 | **👍**：1
- **摘要**：MCP Server 连接失败时，Agent Loop 会永久挂起，导致聊天界面停止响应。
- **链接**：[Issue #3269](https://github.com/sipeed/picoclaw/issues/3269)

> **分析**：这是今日**最高优先级**的稳定性问题。涉及 MCP 集成这一核心架构模块，影响用户体验的连续性。社区共鸣明显（唯一获得 👍 的 Issue），反映出多用户已受此问题困扰。

### ✅ PR #3337 — 修复 MCP 失败导致 Agent Loop 挂起
- **状态**：🟢 OPEN | **作者**：kuzmichus
- **摘要**：针对 Issue #3269 的直接修复，当 `ensureMCPInitialized` 返回错误时，不再让 Agent Loop 永久退出，恢复聊天响应能力。
- **链接**：[PR #3337](https://github.com/sipeed/picoclaw/pull/3337)

> **分析**：该 PR 与 Issue #3269 形成直接闭环，**应作为今日最高优先级合并项**。

### Issue #3307 — Telegram Session 管理功能缺失
- **状态**：🟡 已关闭（stale）| **评论**：2
- **摘要**：Web UI 支持 session 列表/切换，但 Telegram 渠道缺乏同等能力。
- **链接**：[Issue #3307](https://github.com/sipeed/picoclaw/issues/3307)

> **分析**：用户诉求清晰——**跨渠道功能对齐**。当前 stale 关闭不代表需求消失，建议维护者将其纳入 backlog 或标记为 `enhancement` 持续跟踪。

---

## 5. Bug 与稳定性

| 问题 | 来源 | 严重程度 | Fix PR |
|------|------|----------|--------|
| MCP 连接失败导致 Agent Loop 挂起，聊天界面永久无响应 | [Issue #3269](https://github.com/sipeed/picoclaw/issues/3269) | 🔴 **高**（核心功能中断） | [PR #3337](https://github.com/sipeed/picoclaw/pull/3337) |
| Tool-call 格式泄漏至 LLM 摘要，污染对话上下文 | [Issue #3308](https://github.com/sipeed/picoclaw/issues/3308) | 🟡 中（影响对话质量） | [PR #3279](https://github.com/sipeed/picoclaw/pull/3279) ✅ 已合并 |
| `exec` tool 忽略 per-run timeout，boolean 选项类型声明错误 | [PR #3319](https://github.com/sipeed/picoclaw/pull/3319) | 🟡 中（工具行为不符预期） | 待合并 |

> **稳定性评估**：今日修复了 2 个关键 Bug，其中 MCP 挂起问题已有针对性 PR。`exec` tool 的超时与类型问题仍在开放中，建议跟进。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 当前状态 | 纳入可能性 |
|------|------|----------|------------|
| MCP 失败容错恢复 | [Issue #3269](https://github.com/sipeed/picoclaw/issues/3269) → [PR #3337](https://github.com/sipeed/picoclaw/pull/3337) | PR 已开 | 🟢 **高**（稳定性优先） |
| 可配置默认 Model Fallback Chain | [PR #3200](https://github.com/sipeed/picoclaw/pull/3200) | 开放中 | 🟢 **中高**（提升可用性） |
| exec tool 超时与类型修复 | [PR #3319](https://github.com/sipeed/picoclaw/pull/3319) | 开放中 | 🟡 **中**（工具层修复） |
| Telegram Session 管理 | [Issue #3307](https://github.com/sipeed/picoclaw/issues/3307) | 已 stale 关闭 | 🟡 待重新评估 |
| Deltachat 重构与清理 | [PR #3222](https://github.com/sipeed/picoclaw/pull/3222) | 开放中 | 🟡 中（代码整洁度） |

> **路线图信号**：项目正朝**多渠道对齐**（Telegram/Web UI session 管理）、**模型弹性**（fallback chain）、**工具稳定性**（MCP/exec 修复）三个方向演进。建议下一版本优先合并 #3337 与 #3200。

---

## 7. 用户反馈摘要

- **痛点 1**：MCP Server 不可达时整个聊天界面"死掉"，用户无法感知恢复路径，只能重启应用。[Issue #3269](https://github.com/sipeed/picoclaw/issues/3269)
- **痛点 2**：Seahorse 摘要逻辑中 tool-call 原始格式泄漏到用户可见消息，破坏对话连贯性。[Issue #3308](https://github.com/sipeed/picoclaw/issues/3308)
- **痛点 3**：Telegram 用户无法管理多会话，Web UI 的 session 管理能力未跨渠道对齐。[Issue #3307](https://github.com/sipeed/picoclaw/issues/3307)
- **正向反馈**：用户认可 PicoClaw "在 $10 硬件上以 <10MB RAM 和亚秒启动" 的轻量化设计，代码审查 PR（#3308）体现了社区对质量的高标准。[Issue #3308](https://github.com/sipeed/picoclaw/issues/3308)
- **新需求**：企业用户期望钉钉渠道支持图片消息，微信用户需要音频发送能力——今日 PR #3283 和 #3270 已响应。

---

## 8. 待处理积压

| 项目 | 状态 | 建议优先级 | 链接 |
|------|------|------------|------|
| MCP 挂起修复 PR | 🟢 OPEN（创建当日） | 🔴 **P0** | [PR #3337](https://github.com/sipeed/picoclaw/pull/3337) |
| Model Fallback Chain | 🟢 OPEN | 🟡 P1 | [PR #3200](https://github.com/sipeed/picoclaw/pull/3200) |
| exec tool 超时/类型修复 | 🟢 OPEN | 🟡 P1 | [PR #3319](https://github.com/sipeed/picoclaw/pull/3319) |
| Deltachat 重构清理 | 🟢 OPEN | 🟢 P2 | [PR #3222](https://github.com/sipeed/picoclaw/pull/3222) |
| Telegram Session 管理 | 🟡 Stale 关闭（需求有效） | 🟢 P2（需重新激活） | [Issue #3307](https://github.com/sipeed/picoclaw/issues/3307) |

> **维护者关注建议**：PR #3337 直接关联高严重性 Bug，应优先审查合并；Issue #3307 虽 stale 关闭但需求明确，建议重新打开并标记为 `enhancement` 以纳入路线图。

---

**报告生成时间**：2026-08-15 | **数据来源**：PicoClaw GitHub 仓库 | **分析师**：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：2026-08-15 | 数据来源：github.com/qwibitai/nanoclaw**

---

## 1. 今日速览

NanoClaw 今日保持中等活跃度，共收录 13 条动态（2 Issues + 11 PRs）。整体呈现"修复驱动"态势：3 条已关闭 PR 集中于签名验证链路的自动化测试迭代，8 条待合并 PR 涵盖功能扩展（Dial 通道）、基础设施修复（Node.js 版本检查、Windows 容器清理）及细节完善。社区新报告 2 个安装/兼容性 Bug，暂无新版本发布，项目处于功能沉淀与稳定性加固阶段。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭 PR（3 条）

| PR | 作者 | 内容概述 |
|----|------|----------|
| [#3243](https://github.com/nanocoai/nanoclaw/pull/3243) | gavrielc | 修复 `verify-agent-image` 中"启用自动合并"操作在 Draft PR 或 API 瞬态错误时误判为验证失败的问题，引入 `continue-on-error` 逻辑，确保合并行为不干扰验证结论。 |
| [#3242](https://github.com/github.com/nanocoai/nanoclaw/pull/3242) | gavrielc | 签名审批器首轮实时测试（Draft 状态，未合并），推动 verify → approve-agent-image → cosign verify → approving review 全流程验证。 |
| [#3244](https://github.com/nanocoai/nanoclaw/pull/3244) | gavrielc | 签名审批器第二轮测试（Draft 状态，未合并），依赖 #3243 修复后触发独立重新验证与审批发布。 |

> **进展评估**：core-team 成员 gavrielc 在 2 天内完成签名验证链路的三轮迭代，基础设施安全策略正趋于稳定。8 条待合并 PR 中，Dial 通道（#3041/#3050）和多个 Bug Fix 若顺利合并，将显著提升项目的多通道支持与跨平台兼容性。

---

## 4. 社区热点

### 今日活跃 Issue/PR

| 类型 | 编号 | 主题 | 作者 | 链接 |
|------|------|------|------|------|
| Issue | #3248 | setup.sh Node 版本检查无法处理"过旧"情况 | glifocat | [链接](https://github.com/nanocoai/nanoclaw/issues/3248) |
| PR | #3249 | Fix: 处理已存在但过旧的 Node 安装 | glifocat | [链接](https://github.com/nanocoai/nanoclaw/pull/3249) |
| Issue | #3245 | 预构建镜像中 Bun 二进制需要 AVX2，在无 AVX2 CPU 上 SIGILL | sergeykad | [链接](https://github.com/nanocoai/nanoclaw/issues/3245) |
| PR | #2752 | 修复 Discord 入站 Attachment 无法被 Agent 读取的问题 | chubbicorn245 | [链接](https://github.com/nanocoai/nanoclaw/pull/2752) |
| PR | #3041 | 新增 Dial Channel Adapter（SMS + AI 语音通话） | OmriBenShoham | [链接](https://github.com/nanocoai/nanoclaw/pull/3041) |

> **热点分析**：
> - **#3248 → #3249 快速响应**：Issue 创建后同日内即有对应 Fix PR 提交，维护者响应效率高。
> - **#3245 反映硬件兼容性痛点**：预构建镜像默认使用 AVX2 优化的 Bun 二进制，排除了大量入门级/服务器 CPU 用户（Intel Tremont/Elkhart Lake 系列），属于阻塞性安装障碍。
> - **#2752 解决长期存在的 Discord 附件问题**：Inbound 附件（文本粘贴自动转换为 `message.txt` 及图片）无法到达 Agent 的问题影响用户体验，此 PR 若合并将显著改善 Discord 通道可用性。
> - **#3041/#3050 拓展通道生态**：Dial 通道支持 SMS 和 AI 语音通话，配合 Wizard 集成，反映项目正向多模态通信场景扩展。

---

## 5. Bug 与稳定性

### 今日报告 Bug（按严重程度排列）

| 严重级别 | Issue | 描述 | Fix PR | 链接 |
|----------|-------|------|--------|------|
| 🔴 高 | #3245 | 预构建 Agent 镜像的 Bun 二进制要求 AVX2，在无 AVX2 CPU 上触发 SIGILL，导致安装失败 | 暂无 | [链接](https://github.com/nanocoai/nanoclaw/issues/3245) |
| 🟡 中 | #3248 | `setup.sh` 的 Node 版本检查分支无法区分"未安装"与"版本过旧"，导致错误路由 | #3249（待合并） | [链接](https://github.com/nanocoai/nanoclaw/issues/3248) |
| 🟡 中 | #3246 | Windows 平台上 `cleanupOrphans()` 因 POSIX 单引号在 `cmd.exe` 中的传递问题静默失效 | 已有 Fix PR | [链接](https://github.com/nanocoai/nanoclaw/pull/3246) |
| 🟢 低 | #3247 | Malformed cron 表达式在每次调度扫描时重复报错，未做退役处理 | 已有 Fix PR | [链接](https://github.com/nanocoai/nanoclaw/pull/3247) |
| 🟢 低 | #3230 | Skills 移除文档指向已废弃的数据/环境镜像 | 已有 Fix PR | [链接](https://github.com/nanocoai/nanoclaw/pull/3230) |

> **稳定性评估**：今日 5 个 Bug 类问题中有 4 个已有对应 Fix PR，整体修复覆盖率达 80%。唯一未修复的 🔴 级问题（#3245 AVX2 依赖）影响面较广，建议优先处理。

---

## 6. 功能请求与路线图信号

### 新增功能 PR

| PR | 作者 | 功能描述 | 版本纳入评估 |
|----|------|----------|--------------|
| [#3041](https://github.com/nanocoai/nanoclaw/pull/3041) | OmriBenShoham | 新增 Dial Channel Adapter，支持 SMS 和 AI 语音通话 | ✅ 高概率纳入下一版本，完成技能文档 + 源码集成 |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | OmriBenShoham | 将 Dial 集成到 Channel Picker 和 Wizard 配置流程 | ✅ 与 #3041 配套，高概率同步纳入 |

> **路线图信号**：项目正积极扩展多通道通信能力（Dial），同时强化自动化验证与基础设施稳定性（签名审批链、容器清理）。社区对跨平台兼容性的诉求（Issue #3245）可能推动预构建镜像策略的调整。

---

## 7. 用户反馈摘要

| 反馈来源 | 用户痛点/场景 | 情绪倾向 |
|----------|---------------|----------|
| #3245 | 使用入门级 CPU（Celeron J6413/N5105 等 Atom 系列）的用户无法运行默认预构建镜像，安装向导推荐的 `NANOCLAW_HARDENED_IMAGE=true` 模式直接失败 | ❌ 不满：默认配置排除特定硬件 |
| #3248 | Node.js 版本检查逻辑存在缺陷，"版本过旧"与"未安装"被同等处理，导致安装流程无法正确引导用户 | ❌ 不满：安装体验不清晰 |
| #2752 | Discord 通道中入站附件（图片和粘贴文本）对 Agent 不可见，仅显示占位符 `[file: message.txt]` / `[image: foo.png]` | ❌ 不满：核心功能（附件处理）失效 |
| #3041/#3050 | 用户希望扩展通信渠道至 SMS 和语音通话，支持更广泛的 Agent 交互场景 | ✅ 期待：多通道集成需求明确 |

---

## 8. 待处理积压

| 编号 | 类型 | 主题 | 等待时间 | 建议 |
|------|------|------|----------|------|
| [#3245](https://github.com/nanocoai/nanoclaw/issues/3245) | Issue | 预构建镜像 AVX2 依赖导致无 AVX2 CPU 上 SIGILL | 今日 | 🔴 优先处理：考虑提供 non-AVX2 构建或动态检测机制 |
| [#3248](https://github.com/nanocoai/nanoclaw/issues/3248) | Issue | setup.sh Node 版本检查分支缺陷 | 今日 | ✅ 已有 Fix PR #3249，等待合并 |
| [#2427](https://github.com/nanocoai/nanoclaw/pull/2427) | PR | 附件问题修复（closes #2426） | 开放 94 天 | ⚠️ 长期未合并，建议审查状态 |
| [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) | PR | Discord 入站 Attachment 修复 | 开放 63 天 | ⚠️ 长期未合并，影响 Discord 用户体验 |

> **积压提示**：#2427 和 #2752 均已开放数月，若代码审查无重大问题，建议优先合并以释放长期积压。#3245 的 AVX2 兼容性问题需维护者评估是否调整预构建策略。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 | 2026-08-15

---

## 1. 今日速览

今日 NullClaw 项目活跃度**较低**。过去24小时内仅有 **1 条 PR 更新**（已合并），无新 Issue 产生，无新版本发布，仓库整体处于平稳收敛状态。合并的 PR #986 解决了 SQLite 内存数据库路径可配置性问题，是对现有功能的一次优化补充，而非突破性进展。项目暂无明显的阻塞性 Bug 或社区热议话题，维护节奏趋于日常化。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并 PR

| PR | 内容 | 贡献者 | 影响评估 |
|---|---|---|---|
| [#986](https://github.com/nullclaw/nullclaw/pull/986) | `GEN-548`: 使 SQLite 内存数据库路径可配置 | @gently-whitesnow | 小幅优化 |

**详细说明：**

PR #986 为 SQLite 后端主内存引擎新增了 `memory.database_path` 配置项，核心改动包括：
- 支持通过配置指定 SQLite 内存数据库的文件路径
- 当配置为空时，保持原有 `<workspace>/memory.db` 默认行为
- 相对路径自动解析为 workspace 下的路径，同时支持绝对路径以适配只读工作空间部署场景
- 同步更新了相关文档

**推进程度：** 该 PR 是对现有内存引擎灵活性的小幅增强，解决了特定部署场景（只读 workspace）下的痛点，项目整体在此方向稳步推进，但改动规模有限，未涉及核心架构变化。

---

## 4. 社区热点

今日无新开 Issue 或热议 PR。社区互动处于低活跃期，未见集中反馈方向或用户诉求集中爆发点。

---

## 5. Bug 与稳定性

今日无新增 Bug 报告、崩溃反馈或回归问题。

---

## 6. 功能请求与路线图信号

今日无新的功能请求 Issue。

PR #986 的合并释放了 **GEN-548** 标签，该任务已关闭，属于内部任务追踪体系中的常规功能项，暂无额外路线图信号。

---

## 7. 用户反馈摘要

今日无 Issue 评论可供分析。

---

## 8. 待处理积压

基于今日数据，未发现长期未响应的重要 Issue 或 PR。仓库当前积压状态健康，无需特别预警。

---

**📊 项目健康度评级：良好**

| 指标 | 状态 |
|---|---|
| Issue 活跃度 | 🟡 低（0 条/24h） |
| PR 产出 | 🟢 正常（1 条，已合并） |
| Bug 风险 | 🟢 无新增 |
| 版本节奏 | 🟡 无新版本 |
| 社区参与 | 🟡 低互动 |

> *数据来源: [NullClaw GitHub](https://github.com/nullclaw/nullclaw) | 报告生成时间: 2026-08-15*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-08-15

## 1. 今日速览

IronClaw 今日保持高活跃开发节奏：过去24小时共处理25条Issue（16条活跃/9条关闭）与47条PR（23条已合并/关闭，24条待合并）。核心进展集中在 **v1.3.0 自动化结构化执行规范** 的落地推进，以及 **Reborn WebUI** 前端组件体系的重构。QA 冲刺（#7414）同步收尾，多类阻塞性Bug（Slack连接状态误报、Telegram视频上传失败、扩展状态跨用户泄漏）已有对应修复PR。项目整体处于 v1.2.0 发布后的快速迭代修复期，同时 v1.3.0 自动化能力正在系统性地补齐。

---

## 2. 版本发布

**无新版本发布。**

1.2.0 发布线已于今日通过 PR #7657 合并回 main，并完成向前移植（#7663），覆盖线程索引修复、Windows 文件系统/冒烟稳定性、JSON 输出清理及运行时健康检查等修复。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 作者 | 说明 |
|---|---|---|
| [#7634](https://github.com/nearai/ironclaw/pull/7634) | BenKurrek | 完成 unbound-turns 模型切换的71条款一致性审计，标志着 prepared-context 执行模型正式落地 |
| [#7657](https://github.com/nearai/ironclaw/pull/7657) | serrrfirat | 将 1.2.0 发布线合并回 main，携带状态保持型迁移（1.0/1.1→1.2）及 Windows 修复 |
| [#7663](https://github.com/nearai/ironclaw/pull/7663) | serrrfirat | 向前移植 1.2 修复到 main，无 legacy migration，确保双轨一致 |
| [#7668](https://github.com/nearai/ironclaw/pull/7668) | henrypark133 | 扩展 Provider 鉴权诊断可见性，覆盖从 WASM 到 durable gate-record 的全链路错误传播 |
| [#7665](https://github.com/nearai/ironclaw/pull/7665) | henrypark133 | 支持 origin-scoped 托管 MCP OAuth（MKT1 场景），修复 OAuth 资源与元数据持久化 |
| [#7666](https://github.com/nearai/ironclaw/pull/7666) | BenKurrek | 修复扩展卡片"虚假"状态显示（对应 QA #7660），设备链接安装引导用户直达 WebUI 链接步骤 |
| [#7658](https://github.com/nearai/ironclaw/pull/7658) | BenKurrek | 修复 Telegram 跨 DC 迁移场景下的 2FA 登录引导，明确登录码到达位置提示 |
| [#7628](https://github.com/nearai/ironclaw/pull/7628) | serrrfirat | 移除 heartbeat journal 冗余写入，保留 materialized process row 上的 lease timestamp，降低 DB 写入压力 |
| [#7569](https://github.com/nearai/ironclaw/pull/7569) | italic-jinxin | 抽离共享 `SearchField` 组件，统一 Settings/Extensions/Sidebar 搜索输入样式 |
| [#7592](https://github.com/nearai/ironclaw/pull/7592) | serrrfirat | 建立单轮 DB 写入测量基线（pg_stat_statements），作为后续 DB 写压力优化的回归测试 harness |
| [#7655](https://github.com/nearai/ironclaw/pull/7655) | BenKurrek | 重新校准 Slack/Telegram 集成测试覆盖率下界至实测值，避免 ratchet 误报 |
| [#7532](https://github.com/nearai/ironclaw/pull/7532) | serrrfirat | 实现自动化结构化执行规范（structured execution spec），v1.3.0 自动化的核心基石 |

**项目整体推进：** 今日完成 unbound-turns 执行模型最终切换、1.2.0 修复线回归、WebUI 组件体系整理（SearchField/InlineNotice/i18n），以及自动化结构化规范基线确立，项目从"功能构建"向"质量夯实"阶段过渡。

---

## 4. 社区热点

### 高关注 Issue / PR

1. **[#6879](https://github.com/nearai/ironclaw/issues/6879) — Automation runs hit-or-miss（epic, v1.3.0）**
   - 核心痛点：同一存储 prompt 在不同触发时行为不一致，小模型（DeepSeek V4 Flash）尤甚，审计确认为结构性问题。
   - 关联子任务：[#7647](https://github.com/nearai/ironclaw/issues/7647)（确定性无交付抑制）、[#7646](https://github.com/nearai/ironclaw/issues/7646)（预飞行授权与 scoped lease）、[#7645](https://github.com/nearai/ironclaw/issues/7645)（LLM 模型 profile 锁定）、[#7644](https://github.com/nearai/ironclaw/issues/7644)（结构化规范预验证）
   - 诉求：自动化调度的可靠性是 v1.3.0 核心目标，用户期待结构化规格取代纯 prompt-driven 执行。

2. **[#7664](https://github.com/nearai/ironclaw/issues/7664) — Pluggable memory over MCP**
   - 将记忆系统改为配置绑定而非编译期 factory arm，Mnesis Core 作为首个消费者。
   - 关联 PR [#7661](https://github.com/nearai/ironclaw/pull/7661) 已提交，实现 `ironclaw_memory_mcp` crate。
   - 诉求：社区对可插拔记忆架构需求强烈，期望降低自定义 memory backend 的集成成本。

3. **[#7624](https://github.com/nearai/ironclaw/issues/7624) — ACP harness executor（v0）**
   - 作为 pluggable-loops 工作的首个可验证项，以 claude-code 为 loop，dev-only yolo 模式。
   - 关联 PR [#7648](https://github.com/nearai/ironclaw/pull/7648) 已提交，实现 per-run-profile 路由器。
   - 诉求：用户希望 IronClaw 支持外部 ACP（Agent Control Protocol）执行器，扩展生态灵活性。

4. **[#7660](https://github.com/nearai/ironclaw/issues/7660) — Slack 连接状态误报（bug_bash_P2）**
   - Slack 正常工作但 UI 显示 "Reconnect" 与 "Finish Setup" 徽章。
   - 关联修复 PR [#7666](https://github.com/nearai/ironclaw/pull/7666) 已合并。
   - 诉求：Channel 状态一致性直接影响用户体验，此类误报引发信任危机。

---

## 5. Bug 与稳定性

| 严重度 | Issue | 描述 | 状态 |
|---|---|---|---|
| 🔴 P2 | [#7662](https://github.com/nearai/ironclaw/issues/7662) | Telegram 上传 MP4 视频报 `invalid_value (attachments.mime_type)` 错误，文件已识别为 video/mp4 | 待修复 |
| 🔴 P2 | [#7659](https://github.com/nearai/ironclaw/issues/7659) | 其他用户安装的扩展在当前用户的 Extensions/Registry 页面显示为已安装，疑似状态泄漏 | 待修复 |
| 🟡 P2 | [#7660](https://github.com/nearai/ironclaw/issues/7660) | Slack 连接正常但 UI 错误显示 "Reconnect"/"Finish Setup" | ✅ 已修复（[#7666](https://github.com/nearai/ironclaw/pull/7666)）|
| 🟡 P2 | [#7667](https://github.com/nearai/ironclaw/issues/7667) | Telegram phone-mode 登录码提示未反映 `sendCode.type_`（原始TL路径） | 待修复 |
| 🟡 P2 | [#6869](https://github.com/nearai/ironclaw/issues/6869) | 生成的 DOCX 文件 Word 无法打开（损坏），协议违规导致提前终止 | ✅ 已关闭 |
| 🟢 P3 | [#7638](https://github.com/nearai/ironclaw/issues/7638) | 线程删除失败使用 `window.alert()` 而非全局 toast，UX 不一致 | 待修复 |

**稳定性评估：** 今日 QA bug bash 暴露的 P2 级问题主要集中在 **channel 状态显示** 与 **附件处理**，与 Telegram/Slack 集成的深度测试有关。MP4 与扩展状态泄漏尚未有修复 PR，建议关注。

---

## 6. 功能请求与路线图信号

| 需求 | Issue | 对应 PR / 信号 | 纳入 v1.3.0 可能性 |
|---|---|---|---|
| 结构化自动化执行规范 | [#7532](https://github.com/nearai/ironclaw/issues/7532) | 已合并；[#7644-7647](https://github.com/nearai/ironclaw/issues/7644) 系列子任务进行中 | ✅ 核心特性 |
| 确定性无交付抑制 | [#7647](https://github.com/nearai/ironclaw/issues/7647) | PR [#7651](https://github.com/nearai/ironclaw/pull/7651) 已提交 | ✅ 已启动 |
| 扩展记忆系统可插拔 | [#7664](https://github.com/nearai/ironclaw/issues/7664) | PR [#7661](https://github.com/nearai/ironclaw/pull/7661) 已提交 | ✅ 架构级特性 |
| ACP 执行器插件化 | [#7624](https://github.com/nearai/ironclaw/issues/7624) | PR [#7648](https://github.com/nearai/ironclaw/pull/7648) 已提交 | ⚠️ 实验性（dev-only yolo）|
| 用户级 LLM 模型选择 | [#7183](https://github.com/nearai/ironclaw/issues/7183) | 已关闭；当前 admin 独占 | ❓ 未明确 |
| WebUI 结构化 Ask User 卡片 | [#7653](https://github.com/nearai/ironclaw/issues/7653) | 无对应 PR | ❓ 待开发 |
| IronHub Agent Link 操作面 | — | PR [#7516](https://github.com/nearai/ironclaw/pull/7516) 已提交 | ✅ 新增功能 |
| 共享 SearchField / InlineNotice | [#7569](https://github.com/nearai/ironclaw/issues/7569)、[#7639](https://github.com/nearai/ironclaw/issues/7639) | SearchField 已合并；InlineNotice 待实现 | ✅ 组件治理 |

**路线图判断：** v1.3.0 聚焦 **自动化可靠性** 与 **可插拔架构** 两条主线，今日工作明显围绕此展开。ACP 执行器与 Pluggable Memory 属于长期愿景的阶段性落地。

---

## 7. 用户反馈摘要

- **自动化调度不可靠是最大痛点：** #6879 的 "hit-or-miss" 描述反映大量用户在日常自动化场景中的挫败感，尤其小模型场景下 prompt 稳定性差，期待结构化规格取代纯自然语言驱动。
- **Channel 集成体验亟待完善：** Slack 状态误报（#7660）与 Telegram 2FA 登录引导不清（#7667）均源于集成测试覆盖不足，用户反馈集中在"明明连上了却提示重新连接"。
- **DOCX 生成失败影响专业场景：** #6869 用户尝试生成 NDA 文档时遭遇协议违规导致中断，类比 ChatGPT/Claude 能力，对 IronClaw 的文档生成可靠性提出质疑。
- **i18n 覆盖不完整：** #7565 反映多语言用户在使用 Admin/Configuration 页面时仍看到英文字符串，影响非英语用户的体验。
- **Per-user LLM 选择呼声持续：** #7183 虽已关闭但需求未被满足，用户希望摆脱 admin 独占模型配置的约束。

---

## 8. 待处理积压

| Issue | 严重度 | 备注 |
|---|---|---|
| [#7662](https://github.com/nearai/ironclaw/issues/7662) — Telegram MP4 附件失败 | P2 | 影响视频分享场景，无修复 PR，需优先处理 |
| [#7659](https://github.com/nearai/ironclaw/issues/7659) — 扩展状态跨用户泄漏 | P2 | 涉及多租户隔离，潜在数据安全风险 |
| [#7667](https://github.com/nearai/ironclaw/issues/7667) — Telegram 2FA 登录码提示 | P2 | 影响手机模式登录体验 |
| [#7638](https://github.com/nearai/ironclaw/issues/7638) — 线程删除 alert 改 toast | P3 | UX 改进，优先级较低 |


</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报 — 2026-08-15

## 1. 今日速览

LobsterAI 项目今日保持**高活跃状态**，共处理 27 条 PR（22 条已合并/关闭），发布 **2026.8.14** 新版本。开发重心集中在 Sidebar 体验优化（签到、轮播 Banner、多 Agent 任务过滤）、Cowork 会话交互改进（折叠逻辑修复、图片预览增强）、以及 OpenClaw 技能系统 key 规范化。代码质量方面，社区持续推动核心安全模块的测试覆盖（#1154）。整体项目迭代节奏稳定，维护者响应及时。

---

## 2. 版本发布

### 📦 LobsterAI 2026.8.14

**更新内容：**
- **Sidebar 签到与轮播 Banner** — 支持用户签到及 Banner 轮播展示（PR #2411）
- **Sidebar 多 Agent 任务活动过滤** — 新增按任务活跃度筛选多 Agent 会话的能力（PR #2418）

**破坏性变更 / 迁移注意事项：**
- 无已知破坏性变更

---

## 3. 项目进展

今日 22 条 PR 已合并/关闭，主要推进以下方向：

| 方向 | 关键 PR | 说明 |
|------|---------|------|
| **Cowork 交互** | #2499 | 修复会话折叠逻辑——确保有回复内容后才折叠，避免中间态误显示为失败 |
| **Cowork 预览** | #2490 | 浏览器标注截图以编号附件卡片形式渲染，支持独立预览面板 |
| **OpenClaw 技能** | #2491, #2483 | 修复技能 entries 以 frontmatter name 为 key，解决目录名与元数据不一致导致 UI 开关失效的问题 |
| **账号 UI** | #2494, #2492 | 积分图标样式统一，支持亮/暗色模式自适应 |
| **国际化** | #2497 | 优化 Cowork 目标与引导文案措辞 |
| **字体升级** | #2495 | 提升默认 UI/代码字体尺寸，附一次性迁移 |
| **会话导出** | #2493 | 修复导出图片及卡片切换 UI 问题 |
| **依赖更新** | #2460, #2465 | Dependabot 自动 bump rimraf (5→6.1.3)、vite (5→8.2.1) |

**项目整体推进：** 核心会话体验（Cowork）与技能系统稳定性显著增强，UI 细节持续打磨，版本发布流程规范。

> 🔗 PR #2499 | #2490 | #2491 | #2483 | #2494 | #2492 | #2497 | #2495 | #2493 | #2460 | #2465

---

## 4. 社区热点

### 🔥 高关注度 Issue / PR

**#1154 — 为 commandSafety 和 coworkMemoryJudge 补充 Vitest 单元测试**
- **作者:** MaoQianTu | **状态:** OPEN / stale | **评论:** 1
- **诉求分析:** 两个核心安全/质量模块目前零测试覆盖。`commandSafety.ts` 误判可能导致 AI 静默执行 `rm -rf`、`git push --force` 等破坏性命令；`coworkMemoryJudge.ts` 评分逻辑出错会导致记忆写入失控。社区持续呼吁补充测试，反映用户对**系统安全性与可靠性**的高度关注。
- **链接:** https://github.com/netease-youdao/LobsterAI/issues/1154

**#2489 — 快更新 v4pro！**
- **作者:** nimamasl114514 | **状态:** OPEN | **创建:** 2026-08-14
- **诉求分析:** 用户对高级模型（v4pro）更新速度的期待，暗示当前版本模型能力与竞品存在感知差距。
- **链接:** https://github.com/netease-youdao/LobsterAI/issues/2489

**#2374 — 添加永久隐藏 Sidebar 广告 Banner 的开关**
- **作者:** bunnysayzz | **状态:** OPEN
- **诉求分析:** 用户渴望对 UI 元素拥有更多控制权，当前仅支持临时关闭单个 Banner，缺乏全局永久关闭选项。
- **链接:** https://github.com/netease-youdao/LobsterAI/pull/2374

---

## 5. Bug 与稳定性

| 问题 | 严重程度 | 状态 | Fix PR |
|------|----------|------|--------|
| Cowork 会话中间态错误折叠为"失败" | 中 | ✅ 已修复 | #2499 |
| OpenClaw 技能 UI 开关因 key 不匹配而静默失效 | 高 | ✅ 已修复 | #2491, #2483 |
| `buildOpenAIChatCompletionsURL` 处理 Gemini `/v1` 路径时 URL 拼接错误 | 中 | 🔄 待合并 | #1153 |
| 会话导出图片及卡片切换 UI 异常 | 低 | ✅ 已修复 | #2493 |
| 积分图标颜色/样式不一致 | 低 | ✅ 已修复 | #2494, #2492 |

> 🔗 Bug PR #1153 | #2499 | #2491 | #2493

---

## 6. 功能请求与路线图信号

| 请求 | 来源 | 路线图判断 |
|------|------|-----------|
| **会话内页内搜索（Ctrl+F）** | PR #1155 (YDXyydsyyds) | 高潜力——已有完整实现，基于 TreeWalker + CSS Custom Highlight API，待维护者评估合并 |
| **标记会话为未读** | PR #1228 (fhraiwxr) | 中潜力——功能完整，含 Redux action 与 i18n，stale 状态需跟进 |
| **Escape 键关闭 AgentCreateModal + 重置表单** | PR #1231 (choyuenga) | 高潜力——UX 一致性修复，成本低，易合并 |
| **永久隐藏 Sidebar 广告** | PR #2374 (bunnysayzz) | 中潜力——用户控制权诉求明确，已在设置页有先例 |
| **v4pro 模型更新** | Issue #2489 | 依赖模型供应商迭代节奏，非纯客户端可控 |

> 🔗 PR #1155 | #1228 | #1231 | #2374

---

## 7. 用户反馈摘要

- **安全感缺失：** #1154 反映用户对核心安全模块缺乏测试覆盖的焦虑，担心误判导致数据破坏。
- **会话体验痛点：** Cowork 会话折叠逻辑缺陷（#2499）曾导致用户误以为任务失败，现已修复。
- **UI 控制权诉求：** 用户希望自主决定 Sidebar 广告展示（#2374），而非被动接受。
- **技能系统混乱：** OpenClaw 技能开关静默失效（#2491/#2483）源于目录名与 frontmatter 不一致，影响多技能管理场景。
- **效率工具渴望：** 会话内搜索（#1155）和标记未读（#1228）均指向多会话管理场景下的效率瓶颈。

---

## 8. 待处理积压

| 类型 | 编号 | 标题 | 创建时间 | 风险 |
|------|------|------|----------|------|
| ⚠️ Issue | #1154 | 为 commandSafety 和 coworkMemoryJudge 补充单元测试 | 2026-03-31 | 高——核心安全模块零测试，长期 stale |
| 🔀 PR | #1153 | 修复 Gemini `/v1` URL 拼接错误 | 2026-03-31 | 中——影响多模型接入 |
| 🔀 PR | #1155 | 会话内页内搜索（Ctrl+F） | 2026-03-31 | 高——功能完整，长期未合并 |
| 🔀 PR | #1228 | 标记会话为未读 | 2026-04-01 | 中——功能完整，stale |
| 🔀 PR | #1231 | AgentCreateModal Escape 键支持 | 2026-04-01 | 低——UX 修复，易合并 |

**维护者关注建议：** #1154 测试补充请求自 3 月底 stale 至今，涉及安全核心，建议优先响应；#1153、#1155、#1228、#1231 四个 PR 功能完整且创建时间相近，可批量 review。

> 🔗 Issue #1154 | PR #1153 | #1155 | #1228 | #1231

---

*报告生成时间：2026-08-15 | 数据来源：LobsterAI GitHub 过去 24 小时活动*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 | 2026-08-15

---

## 1. 今日速览

今日 Moltis 项目整体保持**中低活跃度**。过去24小时内无新 Issue 提交，无新版本发布。共有 2 条待合并 PR，均由核心贡献者 **penso** 提交，聚焦于**多通道集成扩展**（Slack 原生卡片支持 + 持久化连接器）方向。项目处于功能增量积累阶段，暂无紧急阻塞问题，维护节奏平稳。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

今日无 PR 合并或关闭。当前积压 2 条待合并 PR，均为功能扩展性质：

- **PR #1195** 推进 Slack 原生 live task cards 渲染能力，将 channel-neutral tool lifecycle 更新映射为 Slack 卡片，并引入 per-run ID 隐私保护机制。
- **PR #1190** 推进多提供商连接器持久化（CalDAV、Gmail、Himalaya v2），引入原子快照、定时调度与全量搜索能力，为 Moltis 的"真实世界操作"能力提供底层支撑。

**整体评估：** 项目功能栈向**多通道整合 + 持久化操作**方向稳步推进，核心功能矩阵（Slack + 日历 + 邮件）正在完善。

---

## 4. 社区热点

今日无活跃 Issue 讨论。当前最受关注的 PR 为：

| PR | 标题 | 创建时间 | 链接 |
|----|------|----------|------|
| #1195 | Add Slack native live task cards | 2026-08-15 | [PR #1195](https://github.com/moltis-org/moltis/pull/1195) |
| #1190 | Add durable calendar, channel, and email connectors | 2026-08-11 | [PR #1190](https://github.com/moltis-org/moltis/pull/1190) |

**分析：** 两条 PR 均来自同一贡献者，表明核心开发者正在系统性扩展 Moltis 的**外部系统集成能力**。Slack 卡片（#1195）反映用户对**实时协作体验**的需求；持久化连接器（#1190）则针对**长期任务状态管理**的用户痛点。

---

## 5. Bug 与稳定性

**今日无 Bug 报告。** 无已知崩溃或回归问题。

---

## 6. 功能请求与路线图信号

从待合并 PR 内容可推断以下路线图信号：

| 信号方向 | 来源 | 预期影响 |
|----------|------|----------|
| 多通道原生集成（Slack 卡片） | PR #1195 | 提升 Slack 用户体验，支持实时任务卡片渲染 |
| 持久化连接器（日历/邮件） | PR #1190 | 支持跨会话任务状态保持，增强可靠性 |
| 隐私保护机制（opaque per-run IDs） | PR #1195 | 满足企业用户对任务数据隔离的需求 |
| 提供者中立架构 | PR #1190 | 降低新集成扩展成本，增强可移植性 |

**预判：** 下一版本可能围绕**"多通道实时交互 + 持久化操作"**主题发布，两条 PR 合并后将显著提升 Moltis 的生产级可用性。

---

## 7. 用户反馈摘要

今日无新 Issue 或评论，无法提取实时用户反馈。结合 PR 内容推测：

- **Slack 卡片需求**：用户希望 Moltis 在 Slack 中以**原生卡片**而非纯文本形式呈现任务状态，提升可读性和交互性。
- **持久化需求**：用户对任务状态跨会话保持、失败流清理有明确诉求（PR #1195 中的 "terminal error cleanup"）。
- **隐私诉求**：企业用户关注任务 ID 和工具名称的暴露风险，per-run ID 机制回应了此需求。

---

## 8. 待处理积压

| 优先级 | 类型 | ID | 标题 | 创建时间 | 链接 |
|--------|------|-----|------|----------|------|
| 高 | PR | #1190 | Add durable calendar, channel, and email connectors | 2026-08-11 | [PR #1190](https://github.com/moltis-org/moltis/pull/1190) |
| 高 | PR | #1195 | Add Slack native live task cards | 2026-08-15 | [PR #1195](https://github.com/moltis-org/moltis/pull/1195) |

**建议：** #1190 已开放 4 天，#1195 刚提交。两条 PR 功能互补，建议合并评估时考虑一并 review，以减少集成测试成本。

---

**项目健康度评分：🟡 中等** — 核心开发者活跃，功能方向清晰，但 Issue 参与度低，社区反馈通道待激活。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目日报 — 2026-08-15

## 1. 今日速览

过去24小时 CoPaw 项目保持**高活跃度**，共处理 50 条 Issue（37 条关闭）与 41 条 PR（15 条已合并/关闭）。今日无新版本发布，但维护者积极关闭了大量历史积压 Issue，同时有多个功能 PR 进入审查阶段。主要进展集中在技能系统动态加载、MCP 工具修复、计算机使用能力增强及后台任务超时统一等方向。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 作者 | 内容 |
|----|------|------|
| [#7031](https://github.com/agentscope-ai/QwenPaw/issues/7031) | Ferrum360 | 动态技能加载 + 自动卸载 + frontmatter 修复（已合入 #7033） |
| [#7030](https://github.com/agentscope-ai/QwenPaw/issues/7030) | Ferrum360 | 自动记忆联动标题刷新（已合入 #7032） |
| [#7029](https://github.com/agentscope-ai/QwenPaw/issues/7029) | Ferrum360 | 中文版本动态技能加载 PR，实现 `load_skill/unload_skill/check_skill_status` 工具链 |
| [#6943](https://github.com/agentscope-ai/QwenPaw/issues/6943) | hongxicheng | 恢复插件 Channel 交互式配置器支持 |
| [#2105](https://github.com/agentscope-ai/QwenPaw/issues/2105) | nil957 | 补充 Whisper 本地语音识别安装文档 |
| [#6715](https://github.com/agentscope-ai/QwenPaw/issues/6715) | GMsure | OneBot 入口媒体本地化处理，对齐 AgentScope 2.0 管道 |

### 核心推进方向
- **技能系统生命周期管理**：Ferrum360 连续提交 3 个相关 PR，实现技能的动态加载/自动卸载机制，解决长期存在的技能静态化问题
- **会话体验优化**：PR #6969 修复 MCP 工具返回结构化内容时的重复数据写入问题（关联 #6958）
- **计算机使用能力**：PR #7037 扩展了窗口观察范围，支持有归属关系的子窗口捕获

---

## 4. 社区热点

### 高讨论度 Issue

| Issue | 状态 | 评论数 | 热度分析 |
|-------|------|--------|----------|
| [#3045](https://github.com/agentscope-ai/QwenPaw/issues/3045) | 已关闭 | 8 | 自动获取模型不可用的配置问题，反映用户对模型接入流程的困惑 |
| [#2418](https://github.com/agentscope-ai/QwenPaw/issues/2418) | 已关闭 | 7 | 技能中心快速下载需求，用户期望更便捷的技能管理体验 |
| [#2846](https://github.com/agentscope-ai/QwenPaw/issues/2846) | 已关闭 | 6 | 桌面端自动更新 + Windows 任务栏图标问题，Windows 用户痛点明显 |
| [#7010](https://github.com/agentscope-ai/QwenPaw/issues/7010) | 已关闭 | 6 | **服务器后台运行能力缺失**，SSH/脚本启动卡住，运维场景刚需 |
| [#6405](https://github.com/agentscope-ai/QwenPaw/issues/6405) | 已关闭 | 6 | 升级 2.0 后 MCP 工具找不到，版本迁移兼容性问题 |

### 活跃开放 Issue

| Issue | 状态 | 关注点 |
|-------|------|--------|
| [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) | OPEN | Console 停止请求错误取消飞书会话，多 UI 会话隔离 bug |
| [#7025](https://github.com/agentscope-ai/QwenPaw/issues/7025) | OPEN | Creator 插件导致所有其他插件失效，**插件生态兼容性危机** |
| [#4001](https://github.com/agentscope-ai/QwenPaw/issues/4001) | OPEN | 对话中手动删除单条消息，类微信交互诉求 |
| [#4436](https://github.com/agentscope-ai/QwenPaw/issues/4436) | OPEN | 会话拆分功能，长上下文 token 优化需求 |

---

## 5. Bug 与稳定性

### 今日新报告 Bug（按严重程度排序）

| Issue | 严重程度 | 描述 | Fix PR |
|-------|----------|------|--------|
| [#7016](https://github.com/agentscope-ai/QwenPaw/issues/7016) | 🔴 高 | 流式会话时工具调用接口返回 404，`/api/tool-calls/{id}/offload` 找不到 | — |
| [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) | 🔴 高 | Console 停止请求跨会话干扰，取消活跃飞书会话 | — |
| [#7025](https://github.com/agentscope-ai/QwenPaw/issues/7025) | 🔴 高 | Creator 插件与其他插件冲突导致全部失效 | — |
| [#6958](https://github.com/agentscope-ai/QwenPaw/issues/6958) | 🟡 中 | FastMCP 工具返回结构化内容时写入重复数据 | ✅ [#6969](https://github.com/agentscope-ai/QwenPaw/pull/6969) |
| [#6951](https://github.com/agentscope-ai/QwenPaw/issues/6951) | 🟡 中 | 滚动压缩后重新进入会话，原始消息不可见 | — |
| [#6806](https://github.com/agentscope-ai/QwenPaw/issues/6806) | 🟡 中 | Windows 端无法保存模型配置，持续返回 Internal Server Error | — |
| [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) | 🟡 中 | QwenPaw 2.0.1 与 agentscope 2.0.4.post1 不兼容，proactive 子系统崩溃 | — |
| [#6197](https://github.com/agentscope-ai/QwenPaw/issues/6197) | 🟡 中 | `nvidia-smi` 挂起导致桌面端启动卡死 | — |
| [#7040](https://github.com/agentscope-ai/QwenPaw/issues/7040) | 🟢 低 | 界面文案拼写错误 "Stopp Running" | — |

**稳定性评估**：今日关闭 37 条 Issue，但仍有 13 条活跃 Issue，其中 3 条为高严重程度且暂无 Fix PR，建议优先处理 #7016、#7011、#7025。

---

## 6. 功能请求与路线图信号

| 需求 | Issue | 关联 PR | 纳入可能性 |
|------|-------|---------|------------|
| 动态技能加载/自动卸载 | — | ✅ #7033 / #7029 | **已实现，待发布** |
| 按会话覆盖模型 | #5992 | ✅ #5992（审查中） | 较高，PR 已就绪 |
| 会话标题自动刷新 | — | ✅ #7032 | 已实现，待发布 |
| 子 Agent 会话分组 | — | ✅ #7035 | 已实现，待发布 |
| 媒体下载控制 | — | ✅ #7036 | 已实现，待发布 |
| 对话消息单条删除 | #4001 | — | 待定，用户呼声较高 |
| 会话拆分（上下文迁移） | #4436 | — | 待定，长上下文痛点 |
| 后台运行/Daemon 模式 | #7010 | — | 已关闭但可能未解决，需跟进 |
| 定时任务不投递选项 | #2554 | — | 低优先级 |
| 本地 GGUF 模型内置支持 | #6433 | ✅ 标注 done | 已纳入规划 |

---

## 7. 用户反馈摘要

### 核心痛点
1. **插件生态脆弱**：#7025 报告 Creator 插件导致全部插件失效，暴露插件隔离/依赖管理问题
2. **Windows 体验欠缺**：#2846、#3464 多次要求自动更新功能，#6806 报告配置保存失败，Windows 桌面端稳定性待提升
3. **服务器部署困难**：#7010 明确指出缺少 daemon 模式，SSH 启动卡住，影响自动化/远程部署场景
4. **版本迁移兼容**：#6405、#6612 反映 2.0 升级后 MCP 工具、proactive 子系统出现兼容性问题
5. **会话管理粗糙**：#4001 要求单条消息删除，#6951 报告压缩后历史记录丢失，#4436 提出会话拆分需求

### 积极反馈
- 社区对技能系统动态化（#7033）、会话分组（#7035）等功能持正面态度
- 计算机使用能力持续增强（#7037）受到关注

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建时间 | 风险等级 | 建议 |
|----------|------|----------|----------|------|
| [#7016](https://github.com/agentscope-ai/QwenPaw/issues/7016) | Bug | 2026-08-14 | 🔴 高 | 流式会话 404 影响核心体验，需紧急修复 |
| [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) | Bug | 2026-08-14 | 🔴 高 | 多会话隔离问题，可能影响生产环境 |
| [#7025](https://github.com/agentscope-ai/QwenPaw/issues/7025) | Bug | 2026-08-14 | 🔴 高 | 插件冲突问题，影响生态稳定性 |
| [#5992](https://github.com/agentscope-ai/QwenPaw/pull/5992) | PR | 2026-07-12 | 🟡 中 | 按会话模型覆盖 PR 已提交近一个月，建议加快审查 |
| [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) | PR | 2026-07-21 | 🟡 中 | Provider 统一发现 PR 审查中，影响架构清晰度 |
| [#4001](https://github.com/agentscope-ai/QwenPaw/issues/4001) | 需求 | 2026-05-02 | 🟡 中 | 单条消息删除功能，用户呼声持续 |
| [#4436](https://github.com/agentscope-ai/QwenPaw/issues/4436) | 需求 | 2026-05-16 | 🟡 中 | 会话拆分功能，长上下文场景刚需 |
| [#7010](https://github.com/agentscope-ai/QwenPaw/issues/7010) | Bug/需求 | 2026-08-14 | 🟡 中 | 关闭但未明确解决，需确认后台运行方案 |

---

**项目健康度评分**：🟢 良好
- Issue 关闭率 74%（37/50），响应积极
- 多个功能 PR 进入审查/合并阶段，开发节奏稳定
- 存在 3 条高严重度未修复 Bug，建议维护者优先跟进

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-08-15

## 1. 今日速览

ZeroClaw 在过去24小时内保持高度活跃：**33条 Issue 更新、50条 PR 更新**，其中仅3条 Issue 关闭、3条 PR 合并，整体处于"高投入讨论+代码审查"阶段，而非批量交付期。核心工作聚焦于安全架构 RFC 审议、渠道授权修复、Windows CI 兼容性治理，以及运行时 token 预算原子性加固。项目没有新版本发布，但多项关键基础设施改进（Blacksmith CI 扩展、rust-cache 重构）和渠道安全性 PR 正在快速推进，整体健康度良好。

---

## 2. 版本发布

**无新版本发布**。v0.8.5 稳定线_tracker (#9459) 仍进行中，截止日期为2026-08-30，入闸已于8月4日冻结。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（今日）
无新增合并记录；今日关闭的 Issue 均为非代码交付：

| 类型 | Issue # | 说明 |
|------|---------|------|
| wontfix | #9982 | ViBo Cloud API 托管内存提案被拒绝 |
| 已关闭 | #6663 | Telegram partial streaming draft progress 功能已合并（长期积累） |

### 关键 PR 推进状态
- **#9996** (Audacity88) — `fix(security): make action budget accounting atomic`：将 action 预算保留原子化，防止并发调用突破 `max_actions_per_hour`。**P1 安全修复，今日提交，待合并。**
- **#9999** (vrurg) — `fix(compatible): classify output-limited terminal responses`：将 `finish_reason: "length"` 正确分类为输出限制终端失败，避免 #9421 式误报。基于 #9447 的 stacked PR，**今日提交。**
- **#9574** (jstar0) — `fix(channels): authorize approval responders`：绑定 Telegram/Slack/Lark/Matrix 的工具审批响应者到对话/频道，修复身份校验漏洞。**P1，待合并。**
- **#9839** (JordanTheJet) — `fix(security): block direct spellings of irreversible destructive commands`：修复 allowlist 短路逻辑，防止 `allowed_commands=["*"]` + `block_high_risk_commands=false` 绕过子 shell 守卫。**P1，待合并。**

> **项目整体前进幅度**：今日无版本交付，但有 **4项关键安全/稳定性修复** 进入终轮审查（#9574, #9839, #9996, #9999），配合 #9580（HTTP egress 加固）和 #9137（插件 egress 策略基础），安全架构层正集中加固，预计近期可形成合并波峰。

---

## 4. 社区热点

### 讨论最活跃的 Issue（Top 5）

| # | 主题 | 评论数 | 标签 | 链接 |
|---|------|--------|------|------|
| #8303 | RFC: Goal mode v1 — bounded foreground Matrix work | 22 | enhancement, agent, p2, accepted | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) |
| #7155 | RFC: Per-execution confirmation tier for high-risk shell commands | 20 | enhancement, p1, accepted, shell | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) |
| #8603 | RFC: ZeroClaw Chat Completions profile | 19 | gateway, runtime, p2, needs-maintainer-review | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) |
| #7141 | RFC: Pluggable inbound authentication and canonical principals | 16 | security, p1, in-progress | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) |
| #7462 | Bug: 74 test failures on Windows | 15 | bug, p1, accepted | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) |

### 热点分析
- **#8303 (Goal mode v1)**：社区对跨 agent turn 的持久化目标执行机制高度关注，22条评论反映对"bounded"语义与 restart 交接的广泛争议。
- **#7155 / #7141**：两项 p1 安全 RFC 持续活跃，shell 命令确认策略与身份验证可插拔性是维护者与贡献者的核心分歧点，Revision 3 已收敛范围但仍需 maintainer 最终裁定。
- **#7462 (Windows 测试失败)**：74项测试在 Windows 11 (CP936) 下失败，且 CI 因仅跑 Linux 而漏检，属**长期累积的平台兼容债务**，社区关注度持续。

---

## 5. Bug 与稳定性

| 优先级 | Issue # | 描述 | 状态 | Fix PR |
|--------|---------|------|------|--------|
| **S1** | #9421 | 不完整的终端响应被报告为成功（provider 未返回可信最终答案时 runtime 仍上报成功） | in-progress | #9999 (vrurg, 今日提交) |
| **S2** | #7462 | Windows 下74项测试失败（路径语义、console encoding、Unix-only 命令） | accepted，无 fix PR | — |
| **S2** | #9486 | 高熵检测器误红 Solana 钱包地址，`high_entropy_tokens=false` 在 channel 路径不生效 | accepted，无 fix PR | — |
| **S3** | #9983 | Fallback 模型无 vision 时错误原因报告不准确 | open，无 fix PR | — |
| **S2** | #9965 | cron 自定义 shell 测试在并行运行时遇到 ETXTBSY 竞争，误报无关 PR 失败 | accepted，无 fix PR | — |
| **S2** | #9759 | Quickstart 允许重复启用的 webhook 端口 | accepted，无 fix PR | — |

> **稳定性评估**：S1 级 Bug #9421 已有修复 PR 提交；Windows 测试失败（#7462）为长期技术债，暂无修复进展；#9486 Solana 地址误红反映高熵检测规则需渠道路径适配。

---

## 6. 功能请求与路线图信号

### 高优先级功能请求
| Issue # | 需求 | 标签 | 可能纳入版本 |
|---------|------|------|-------------|
| #8603 | Chat Completions 协议适配（支持 Open WebUI、LobeChat、Aider 等） | p2, needs-maintainer-review | v0.9.0 候选 |
| #9895 | Telegram `/model` 按 provider 分组分页 inline-keyboard 选择器 | p2, accepted | v0.8.5 候选 |
| #9970 | Discord 按 role ID 授权（非仅 user ID） | p2, in-progress | v0.8.5 候选 |
| #9986 | `zeroclaw agents export` — 将 agent 导出为可移植 bundle | p2, open | 待定 |
| #7065 | Agent 评估 harness（replay + live 模式） | p2, in-progress | 长期路线图 |

### 路线图信号
- **#9487 / #9488**：运行时拥有的会话管理与统一附件架构两项 RFC 同步讨论，表明项目正在统一 channel 层的 session/transport 抽象。
- **#9346**：统一 package/capability/config/runtime-state catalog contract，推动 #6489 产品级目录落地。
- **#9967 / #9972 / #8691**：评估框架建立、本地化清理、ADR 基线恢复三项 tracker 并行推进，反映维护团队正在补齐工程治理基础设施。

---

## 7. 用户反馈摘要

| 痛点/场景 | 来源 |
|-----------|------|
| **Telegram 模型选择在移动端极不友好**：多 route 配置时需手动输入，希望有 inline-keyboard 分组选择 | #9895 (morningstarnasser) |
| **Solana 钱包地址被误红**：agent 无法在 Telegram 中输出链地址，破坏正常使用场景 | #9486 (koshak01) |
| **Windows 本地开发体验差**：CI 仅跑 Linux，74项测试失败本地无法复现但影响分发 | #7462 (NiuBlibing) |
| **Agent 跨 turn 目标执行缺乏可靠机制**：Goal mode 设计影响所有长期任务场景 | #8303 (vrurg) |
| **Agent 迁移/共享困难**：用户希望将 agent 打包为可移植 bundle 在其他安装间移动 | #9986 (SheaHawkins) |
| **Discord 频道授权粒度不足**：仅支持 user ID 白名单，不支持 role-based 授权 | #9970 (JordanTheJet) |
| **历史裁剪 token 消耗不透明**：大段删除时 token 预算变化无法追溯 | #9713 (Project516) |

---

## 8. 待处理积压

### 维护者关注重点

| Issue # | 类型 | 风险 | 说明 | 链接 |
|---------|------|------|------|------|
| #8692 | Tracker | 高 | Maintainer decision queue — 积压的 RFC/设计 Issue 等待裁定 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| #7462 | Bug | 高 | Windows 74项测试失败，长期无 fix（platform debt） | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) |
| #6971 | RFC | 高 | Security posture & universal ingress policy — 安全基础架构核心 RFC 久未裁定 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) |
| #7142 | RFC | 高 | Runtime-owned security decision pipeline — v0.9.0 安全架构目标，Rev6 等待合并 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7142) |
| #8603 | RFC | 中 | Chat Completions profile — 生态兼容性关键，needs-maintainer-review | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) |
| #9459 | Tracker | 中 | v0.8.5 稳定线 — 截止 2026-08-30，需确认 release 候选状态 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9459) |
| #8691 | Tracker | 低 | ADR 基线恢复 + 已接受 RFC 决策记录审计 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8691) |

> **维护者建议**：#8692 决策队列是当前最大瓶颈，#7155/#8603/#6971 三项 p1/p2 RFC 需尽快给出 acceptance/rejection 裁定；#7462 Windows 测试债建议指派专人跟进或在 CI 中增加 Windows 运行。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*