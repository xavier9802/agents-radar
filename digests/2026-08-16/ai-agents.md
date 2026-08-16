# OpenClaw 生态日报 2026-08-16

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-16 01:44 UTC

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



# OpenClaw 项目动态日报 — 2026-08-16

## 1. 今日速览

OpenClaw 今日保持高度活跃：过去 24 小时共产生 **500 条 Issue**（478 条活跃/新开，22 条关闭）和 **500 条 PR**（452 条待合并，48 条已合并/关闭），社区参与度持续高位。新版本 **v2026.8.1-beta.2** 发布，聚焦安全加固（Secret egress host binding）与模型支持扩展（GPT-5.6 Ultra）。UI 侧 Sidebar/Chat 重构工作集中推进，同时消息丢失、子代理状态异常、Gateway 内存泄漏等核心稳定性问题仍获大量关注。项目整体处于"功能迭代 + 稳定性攻坚"双轨并行阶段，健康度良好但消息传递链路可靠性仍需重点修复。

---

## 2. 版本发布

### v2026.8.1-beta.2

**核心亮点：**
- **Secret egress host binding** — 将共享存储中的每个 Secret 绑定到精确的 HTTPS 目标 Host，覆盖 CLI、Gateway RPC 和控制面板，未绑定的哨兵替换将 fail-closed，防止明文外泄。
- **GPT-5.6 Ultra 支持 & runtime switching** — 新增对 GPT-5.6 Ultra 模型的运行时切换能力。

**破坏性变更 / 迁移注意：**
- Secret 绑定机制要求用户明确配置目标 Host，未配置的 Secret 引用将拒绝出站，需检查现有配置中涉及 Secret 的外部调用是否已声明目标域名。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（48 条）

| PR | 类型 | 内容摘要 |
|---|---|---|
| [#122177](https://github.com/openclaw/openclaw/issues/122177) | bugfix | 修复 Chrome 扩展 relay 重连后共享标签页丢失问题 |
| [#121391](https://github.com/openclaw/openclaw/issues/121391) | bugfix | 修复 setup/tools 写入已废弃配置键的问题 |
| [#121871](https://github.com/openclaw/openclaw/issues/121871) | bugfix | 修复 Telegram 推理回复在 Control UI 中重复渲染为两个气泡的问题 |
| [#124222](https://github.com/openclaw/openclaw/issues/124222) | bugfix | 修复 Telegram 模型确认消息与旧 rich-text  Markup 混合渲染问题 |
| [#123871](https://github.com/openclaw/openclaw/issues/123871) | bugfix | 修复多 Agent 场景下 `openclaw status` 因缺少 systemAgent.agentId 而报错 |
| [#119700](https://github.com/openclaw/openclaw/issues/119700) | ci-fix | 修复 Crabbox 认证 readiness 检查中的假阳性失败 |
| [#124334](https://github.com/openclaw/openclaw/issues/124334) | bugfix | 修复多 Agent 主机上 Gateway 启动时 IDLE CPU 飙升至 100-140% 的问题 |

**整体判断：** 今日合并以 UI polish 和 channel bugfix 为主，核心运行时稳定性 PR（如 #97175 context-engine 阻塞修复）仍在等待 maintainer review，项目向前推进约 10-15% 的已知技术债。

---

## 4. 社区热点

### Top 活跃 Issues（按评论数）

| # | 主题 | 评论 | 状态 | 链接 |
|---|---|---|---|---|
| #121058 | 静默回复失败在 #116277 关闭后仍重复出现 | 96 | ✅ 已关闭 | [链接](https://github.com/openclaw/openclaw/issues/121058) |
| #116201 | 实时语音会话资源无界 retained | 66 | 🔄 活跃 | [链接](https://github.com/openclaw/openclaw/issues/116201) |
| #7707 | 按来源标记 Memory Trust Level | 53 | 🔄 活跃 | [链接](https://github.com/openclaw/openclaw/issues/7707) |
| #25592 | 工具调用间文本泄漏到消息频道 | 49 | 🔄 活跃 | [链接](https://github.com/openclaw/openclaw/issues/25592) |
| #44925 | 子代理完成结果静默丢失 | 29 | 🔄 活跃 | [链接](https://github.com/openclaw/openclaw/issues/44925) |

**热点分析：**
- **#121058** 虽已关闭，但 96 条评论说明该 bug 长期困扰用户，关闭后的复现提醒社区对该 fix 的有效性存疑。
- **#7707** Memory Trust Tagging 获得高关注，反映用户对 AI 记忆被 poisoning 的深层安全担忧。
- **#25592** 工具调用间文本泄漏是高频 UX 痛点，直接关联消息通道的噪音问题。

---

## 5. Bug 与稳定性

### 高优先级 Bug（P1）

| # | 描述 | 严重度 | Fix PR | 链接 |
|---|---|---|---|---|
| #121058 | 静默回复失败 recurring | 🔴 P1 message-loss | 已 close（存疑） | [链接](https://github.com/openclaw/openclaw/issues/121058) |
| #116201 | 实时语音会话资源无界 retained | 🔴 P1 session-state | 无 | [链接](https://github.com/openclaw/openclaw/issues/116201) |
| #25592 | 工具间文本泄漏到消息频道 | 🔴 P1 session-state | 无 | [链接](https://github.com/openclaw/openclaw/issues/25592) |
| #44925 | 子代理完成静默丢失（无重试/通知） | 🔴 P1 message-loss/data-loss | 无 | [链接](https://github.com/openclaw/openclaw/issues/44925) |
| #121953 | Cron agent 在 DeepSeek 上卡顿（prefix 降权） | 🔴 P1 | 无 | [链接](https://github.com/openclaw/openclaw/issues/121953) |
| #86684 | sessions_yield 子代理唤醒导致父分支不当 compaction | 🔴 P1 regression | 无 | [链接](https://github.com/openclaw/openclaw/issues/86684) |
| #87109 | Gateway heap 空闲增长至 1073MB+，cron 静默失败 | 🔴 P1 | 无 | [链接](https://github.com/openclaw/openclaw/issues/87109) |
| #95553 | preflight compaction 硬编码 60s 超时 | 🔴 P1 | 无 | [链接](https://github.com/openclaw/openclaw/issues/95553) |
| #92186 | 前台回复 fence 取消并发消息的 delivery | 🔴 P1 message-loss | 无 | [链接](https://github.com/openclaw/openclaw/issues/92186) |
| #90944 | sessions_yield resume reply 记录但未投递 | 🔴 P1 data-loss | 无 | [链接](https://github.com/openclaw/openclaw/issues/90944) |
| #80498 | 子代理完成通知 premature/duplicated | 🔴 P1 message-loss | 无 | [链接](https://github.com/openclaw/openclaw/issues/80498) |
| #94939 | 6.x 迁移后 channel conversation SQLite 为空 | 🔴 P1 regression data-loss | 无 | [链接](https://github.com/openclaw/openclaw/issues/94939) |
| #83337 | 插件/核心版本 drift 导致 channel 静默失效 | 🔴 P1 | 无 | [链接](https://github.com/openclaw/openclaw/issues/83337) |

### 中低优先级 Bug（P2/P3）

| # | 描述 | 严重度 | 链接 |
|---|---|---|---|
| #67419 | Session context bloat：bootstrap 文件每轮重复注入，浪费 20-30% tokens | P2 | [链接](https://github.com/openclaw/openclaw/issues/67419) |
| #114612 | memory_index_chunks + embedding_cache 无保留策略，SQLite 无界增长 | P2 | [链接](https://github.com/openclaw/openclaw/issues/114612) |
| #119796 | Windows vitest teardown EBUSY unlink agent state DB | P2 | [链接](https://github.com/openclaw/openclaw/issues/119796) |
| #90711 | launchd plist StandardErrorPath 硬编码 /dev/null，隐藏 stderr | P2 regression | [链接](https://github.com/openclaw/openclaw/issues/90711) |
| #74378 | Windows CLI 命令执行后 node.exe 进程残留 | P2 regression | [链接](https://github.com/openclaw/openclaw/issues/74378) |
| #93917 | genericRepeat circuit-breaker 在 exec 结果微变时不触发 | P2 | [链接](https://github.com/openclaw/openclaw/issues/93917) |
| #68920 | /v1/chat/completions TTFB 10-15s，需 lightContext/voice 模式 | P2 | [链接](https://github.com/openclaw/openclaw/issues/68920) |
| #120735 | Telegram sticker 以原始文件引用到达，未 stage 到磁盘 | P2 | [链接](https://github.com/openclaw/openclaw/issues/120735) |
| #50165 | 子代理 UI 显示完成但底层委托工作未实际完成 | P2 | [链接](https://github.com/openclaw/openclaw/issues/50165) |

**稳定性评估：** 今日大量 P1 issue 集中于**消息丢失/子代理状态机异常**，反映出 runtime 核心链路存在系统性脆弱，缺乏有效的 fix PR 覆盖是主要风险。

---

## 6. 功能请求与路线图信号

| # | 需求 | 评论 | 倾向 | 链接 |
|---|---|---|---|---|
| #7707 | Memory Trust Tagging by Source（按来源标记记忆可信度） | 53 | 🟢 高优先级安全功能 | [链接](https://github.com/openclaw/openclaw/issues/7707) |
| #10687 | 完全动态模型发现（OpenRouter + beyond） | 10 | 🟢 高价值功能 | [链接](https://github.com/openclaw/openclaw/issues/10687) |
| #60572 | Multi-Slot Memory Architecture（多内存槽位） | 6 | 🟡 中长期 | [链接](https://github.com/openclaw/openclaw/issues/60572) |
| #45758 | 支持 YAML 配置文件格式 | 9 | 🟡 低优先级 UX | [链接](https://github.com/openclaw/openclaw/issues/45758) |
| #13219 | Per-model usage logging for cost tracking | 8 | 🟢 实用功能 | [链接](https://github.com/openclaw/openclaw/issues/13219) |
| #73537 | 发布稳定性标签（production-readiness label） | 8 | 🟡 项目治理 | [链接](https://github.com/openclaw/openclaw/issues/73537) |
| #45771 | 内置 pace-aware rate limiting for autonomous agents | 7 | 🟢 实用功能 | [链接](https://github.com/openclaw/openclaw/issues/45771) |
| #88154 | Slack Modal 支持交互式工作流 | 8 | 🟡 渠道增强 | [链接](https://github.com/openclaw/openclaw/issues/88154) |
| #81061 | before_route_inbound_message hook（路由前拦截） | 8 | 🟢 架构增强 | [链接](https://github.com/openclaw/openclaw/issues/81061) |
| #44309 | A2A 单向 dispatch 模式（无 reply-back ping-pong） | 9 | 🟡 架构增强 | [链接](https://github.com/openclaw/openclaw/issues/44309) |

**路线图判断：**
- **短期可纳入：** #10687（动态模型发现）和 #13219（usage logging）呼声较高且实现路径清晰。
- **中期重点：** #7707（Memory Trust）安全需求强烈，与新版 Secret binding 安全思路一致。
- **#68920**（TTFB 10-15s 问题）是实时语音场景的关键瓶颈，需优先处理。

---

## 7. 用户反馈摘要

**核心痛点：**

1. **消息丢失/静默失败**（#121058, #44925, #92186, #90944, #80498）
   - 用户反复反馈子代理结果、cron 任务、并发回复的静默丢失，严重影响生产可靠性信任。
   - 典型场景：Telegram/WhatsApp 群组 @mention 后回复不送达；cron 任务超时无任何通知。

2. **Gateway 内存泄漏**（#87109）
   - 生产环境 Gateway heap 从 558MB 增长至 1073MB+，触发 event-loop starvation，cron 任务静默失败。
   - 用户明确提到"重启后恢复，12h+ 后再次增长，可稳定复现"。

3. **上下文膨胀浪费 token**（#67419）
   - Bootstrap 文件每轮重复注入，浪费 20-30% context，多轮对话成本显著。

4. **UX 噪音**（#25592, #120735）
   - 工具调用间的内部处理文本泄漏到 Slack/iMessage；Telegram sticker 无法被 agent 感知。

**用户满意点：**
- 新版 Secret binding 安全机制获认可（#7707 社区积极响应）。
- UI Sidebar/Chat 重构方向获正面反馈（多个 PR 有 screenshot/video proof）。
- 多 Agent 支持持续增强（#123871 fix 获得肯定）。

---

## 8. 待处理积压

### 需维护者关注的长期 Issue

| # | 描述 | 评论 | 未响应时长 | 链接 |
|---|---|---|---|---|
| #116201 | 实时语音会话资源无界 retained | 66 | ~17 天 | [链接](https://github.com/openclaw/openclaw/issues/116201) |
| #7707 | Memory Trust Tagging by Source | 53 | ~194 天 | [链接](https://github.com/openclaw/openclaw/issues/

---

## 横向生态对比



# 个人 AI 助手/自主智能体开源生态横向对比分析报告
**日期：2026-08-16 | 分析师：Agnes**

---

## 1. 生态全景

2026年8月，个人AI助手与自主智能体开源生态呈现"核心项目高速迭代、安全与稳定性成为共同焦点"的态势。OpenClaw作为生态参照系保持极高活跃度（日500+ issue/PR），ZeroClaw、Hermes Agent同步进入架构RFC密集讨论期。安全加固（Secret绑定、命令注入防护、SSRF防御）与消息可靠性（子代理状态机、Gateway内存管理）是跨项目共性痛点。生态正从"功能堆叠"阶段转向"生产级可靠性建设"阶段，多通道编排、跨会话上下文、向量记忆架构成为新赛道。

---

## 2. 各项目活跃度对比

| 项目 | Issues (24h) | PRs (24h) | Release | 健康度 | 核心状态 |
|------|-------------|-----------|---------|--------|----------|
| **OpenClaw** | 500 (478新/22关) | 500 (452待合/48合) | v2026.8.1-beta.2 | 🟢 活跃但有技术债 | 功能迭代+稳定性攻坚双轨 |
| **ZeroClaw** | 50 | 50 | — | 🟢 高活跃 | RFC密集讨论期 |
| **Hermes Agent** | 50 | 50 (14合) | — | 🟢 极高活跃 | 大型重构完成，安全加固推进 |
| **IronClaw** | 27 (6新/21关) | 12 (7待合/5合) | — | 🟢 高质量迭代 | 性能优化窗口期 |
| **Moltis** | 2 | 16 (14合) | — | 🟢 高效交付 | 安全+功能同步推进 |
| **NanoClaw** | 0 | 22 (19待合) | — | 🟡 高产出待review | 多通道架构扩展关键期 |
| **CoPaw** | 9 | 10 (全待合) | — | 🟡 PR积压 | 修复密集型，review滞后 |
| **NanoBot** | 6 (5新/1关) | 16 (9待合/7合) | — | 🟢 稳定推进 | 稳定性显著提升 |
| **LobsterAI** | 18 (16关) | 6 (2合) | — | 🟡 响应快但积压 | 付费体验待解决 |
| **NullClaw** | 1 | 1 | — | 🟢 低频稳健 | 性能优化演进中 |
| **PicoClaw** | 0 | 2 (全stale) | — | 🔴 停滞风险 | PR积压9天+，需维护者介入 |
| **ZeptoClaw** | 0 | 0 | — | ⚪ 无活动 | — |

---

## 3. OpenClaw 在生态中的定位

**核心参照系地位明确：**
- **规模碾压**：日500 issue/PR远超第二梯队（Hermes/ZeroClaw约50量级），社区参与度呈数量级差异
- **技术路线独特性**：聚焦"多Agent协作+多通道编排"，是生态中唯一系统性处理子代理状态机、Gateway内存管理、消息投递可靠性的项目
- **安全先行策略**：v2026.8.1-beta.2的Secret egress host binding机制为生态树立了安全配置最佳实践标杆
- **痛点代表性**：消息丢失（#121058静默失败复现96条评论）、Gateway内存泄漏（#87109堆增长至1GB+）是生态共性问题的集中体现

**与同类差异：**
- vs NanoBot/Hermes：OpenClaw更侧重生产级多Agent调度与通道治理，后者更聚焦单Agent体验优化
- vs ZeroClaw：OpenClaw已完成架构收敛（prepared-context turns），ZeroClaw仍在RFC讨论期
- vs IronClaw：IronClaw专注数据库写入优化与QA基础设施，OpenClaw覆盖全链路

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|----------|----------|----------|
| **消息/状态可靠性** | OpenClaw, Hermes Agent, NanoBot, CoPaw | 子代理完成静默丢失、cron任务失败无通知、会话重载后数据丢失 |
| **安全加固** | OpenClaw, Hermes Agent, NanoBot, Moltis, ZeroClaw | Secret绑定、命令注入白名单绕过、管道注入检测、SSRF防护、任意文件写入 |
| **多通道/多模型支持** | OpenClaw, NanoClaw, Moltis, ZeroClaw | Telegram Channel适配、GPT-5.6 Ultra、动态模型发现、OpenAI Chat Completions协议 |
| **记忆/上下文管理** | OpenClaw, LobsterAI, Moltis, ZeroClaw | 记忆可信度标记、上下文膨胀浪费token、向量数据库后端、跨会话检索 |
| **本地Agent性能** | NullClaw, Hermes Agent, IronClaw | prompt缓存、工具输出压缩、数据库写入优化、长程运行稳定性 |
| **生产部署体验** | OpenClaw, LobsterAI, CoPaw | Gateway内存泄漏、付费登录稳定性、企业级代理支持、权限隔离 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 多Agent协作+通道治理+安全配置 | 企业/生产级部署用户 | 子代理状态机、Gateway RPC、Secret绑定机制 |
| **Hermes Agent** | TUI体验+安全规则+平台兼容 | CLI深度用户、Linux/WSL用户 | god-file分片重构、Lean tail压缩、管道注入检测 |
| **IronClaw** | 数据库性能优化+QA基础设施 | Rust生态用户、可观测性需求者 | prepared-context turns、线程索引合并、Live Canary测试 |
| **ZeroClaw** | 协议适配+架构RFC+安全拒绝栈 | 协议层贡献者、架构研究者 | Chat Completions profile、运行时会话所有权、Anthropic拒绝响应链 |
| **NanoBot** | WebUI体验+会话管理+安全补丁 | 桌面/Web用户 | OrcaRouter网关、per-session文件生命周期、Cron调度器 |
| **NanoClaw** | 多通道扩展+跨会话上下文 | Telegram/Discord重度用户 | Channel Registry钩子系统、心跳机制修复、投递预览 |
| **Moltis** | 安全加固+连接器扩展 | 安全意识强的个人用户 | zvec向量后端、CalDAV/Gmail/Himalaya连接器、Slack live cards |
| **CoPaw** | 视频处理+OAuth+分页API | 多模态用户、企业部署 | 视频工具修复、DataPaw运行时、LAN浏览器bridge |
| **LobsterAI** | 记忆体系+配置同步+调度修复 | 中文生态用户、网易生态用户 | OpenClawConfigSync、cron yield修复、Dream技能管理 |
| **NullClaw** | 本地Agent性能优化 | 本地推理用户、Zig生态 | prompt缓存前缀、工具输出压缩、重复调用检测 |
| **PicoClaw** | 依赖维护+性能微调 | Sipeed硬件生态用户 | WhatsApp通道恢复、prefix caching优化 |

---

## 6. 社区热度与成熟度分层

### 🔥 快速迭代层（高活跃度+新功能密集）
- **OpenClaw**：日500+ issue/PR，新版本持续发布，功能与安全双轨推进
- **ZeroClaw**：RFC密集讨论（5个高评论RFC并行），架构演进活跃
- **Hermes Agent**：大型重构完成（god-file分片），安全PR批量合并

### 🟢 稳定推进层（中高活跃+质量巩固）
- **IronClaw**：性能优化窗口期，数据库写入压力显著降低，测试可靠性修复中
- **Moltis**：14条PR当日合并，安全+功能高效交付，维护者响应及时
- **NanoBot**：关键稳定性问题闭环（会话状态、插件安全、Cron调度）

### 🟡 积压风险层（活跃但review滞后）
- **NanoClaw**：19条PR待合并，核心贡献者gavrielc高产但review节奏慢
- **CoPaw**：10条PR全待合并，2个P1 bug（视频静默丢失、OAuth refresh_token）无fix
- **LobsterAI**：Issue关闭率高但#1903会员登录问题积压3个月

### 🟡 低频维护层
- **NullClaw**：低频但方向明确（性能优化+代理支持）
- **PicoClaw**：PR stale 9天+，依赖维护者介入

### ⚪ 停滞层
- **ZeptoClaw**：过去24小时无活动

---

## 7. 值得关注的趋势信号

### 1. 安全从"功能属性"升级为"架构基石"
OpenClaw的Secret egress host binding、Hermes的管道注入检测扩展、Moltis的路径遍历修复、NanoBot的exec白名单绕过响应——安全加固已成为跨项目共识。趋势信号：**未来6个月，安全配置验证、权限边界审计、输入校验将成为项目准入基准线**。

### 2. 消息可靠性是生产部署的"最后一公里"
OpenClaw的13个P1 message-loss/data-loss issues、Hermes的TUI中断恢复、CoPaw的race condition——多项目同时暴露消息传递链路的系统性脆弱。**开发者应重点关注：子代理状态机设计、Gateway心跳机制、cron任务失败通知、跨会话上下文一致性**。

### 3. 协议层标准化加速（OpenAI兼容 vs 原生协议）
ZeroClaw的Chat Completions RFC（21评论）与NanoBot的OrcaRouter网关形成呼应——**生态正在分化：原生协议栈（WebSocket/ACP）vs OpenAI兼容层**。对开发者而言，选择支持双协议的项目可降低迁移风险。

### 4. 本地Agent性能优化进入深水区
NullClaw的prompt缓存+工具输出压缩、IronClaw的数据库写入优化、Hermes的Lean tail压缩（+22.5pt召回）——**本地推理的token效率与延迟优化成为新竞争点**。建议关注：上下文压缩策略、工具调用去重、缓存命中率监控。

### 5. 多通道编排从"接入"走向"治理"
NanoClaw的Channel Registry钩子系统、OpenClaw的通道路由修复、Moltis的Slack live cards——**多通道支持已进入"治理阶段"**：审批拦截、投递预览、跨会话上下文、未知发送者策略成为新需求。**开发者应优先评估项目的通道抽象层设计是否支持细粒度策略控制**。

### 6. 记忆架构从"存储"走向"可信度管理"
OpenClaw的Memory Trust Tagging（#7707，53评论）、LobsterAI的记忆体系产品建议、Moltis的zvec向量后端——**记忆能力的竞争焦点从"能否存储"转向"如何可信使用"**。趋势：按来源标记可信度、抗poisoning设计、跨会话检索一致性将成为差异化能力。

---

**报告结论：** 个人AI助手开源生态正处于从"功能竞赛"向"可靠性竞赛"转型的关键期。OpenClaw作为生态领导者承担了大量技术债的暴露与沉淀，ZeroClaw/Hermes在架构标准化方面领跑，IronClaw/Moltis在安全与性能优化上树立标杆。对开发者而言，选择项目时应重点关注：消息可靠性机制、安全配置灵活性、协议兼容性、以及社区对P1问题的响应速度。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报
**日期：2026-08-16**

---

## 1. 今日速览

NanoBot 项目当前处于高活跃状态，过去24小时内共收到 6 条 Issue 更新（新开/活跃 5 条，已关闭 1 条）和 16 条 PR 更新（待合并 9 条，已合并/关闭 7 条）。开发者持续推进 WebUI 体验优化（会话协作、拖拽排序、临时对话）、基础设施稳定性修复（会话保存冲突、Cron 调度器、文件状态生命周期）以及安全漏洞响应。无新版本发布，但多项 P0/P2 关键修复已合并，项目整体健康度良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（7 条）

| PR | 类型 | 摘要 |
|---|---|---|
| [#5328](https://github.com/HKUDS/nanobot/pull/5328) | feat | 新增 **OrcaRouter** 网关提供商，支持 150+ 模型统一接入 |
| [#5371](https://github.com/HKUDS/nanobot/pull/5371) | fix | 修复 WebUI 在 Agent 运行中提前显示复制/叉分操作的问题 |
| [#5369](https://github.com/HKUDS/nanobot/pull/5369) | fix/security | 修复插件缓存技能目录未失效的问题，防止包替换后仍可从受限项目读取 |
| [#5370](https://github.com/HKUDS/nanobot/pull/5370) | fix | 限制 per-session 文件状态生命周期，防止高基数会话导致内存无限增长 |
| [#5376](https://github.com/HKUDS/nanobot/pull/5376) | fix | 修复 Cron 调度器在持久化失败时永久崩溃的静默故障模式 |
| [#5399](https://github.com/HKUDS/nanobot/pull/5399) | fix | 优化模型预设显示名称与命令名称的区分展示 |
| [#5397](https://github.com/HKUDS/nanobot/pull/5397) | fix | 保留侧边栏范围选择和 Agent 回合计时逻辑 |

**推进评估**：本次迭代重点修复了**会话状态管理、插件安全、后台任务持久化**三类核心问题，项目稳定性显著提升。`/new` 后数据覆盖、文件状态泄漏、调度器单点故障等高风险问题均已闭环。

---

## 4. 社区热点

### 讨论最活跃的 Issues

**#5305 [Security] `exec.allowPatterns` 白名单绕过** ⚠️ 高危
- 链接：https://github.com/HKUDS/nanobot/issues/5305
- 评论：1 | 点赞：0
- 摘要：通过 OpenAI 兼容 API 可绕过 `exec.allowPatterns` 白名单执行额外 Shell 段，属安全补丁需求
- 分析：安全研究员 YLChen-007 报告，涉及 API 层的命令注入风险，建议优先响应

**#4864 [Bug] `complete_goal` 无限循环**
- 链接：https://github.com/HKUDS/nanobot/issues/4864
- 评论：5 | 点赞：1 | 创建时间：2026-07-09（已开 38 天）
- 摘要：Gateway 将 `recap` 参数解析为裸字符串而非 JSON 对象，导致工具调用持续报错
- 分析：长期未解决，影响目标完成流程，社区关注度较高（5 评论 + 1 赞）

**#4467 [Enhancement] Dream 应更新现有工作区技能而非重复创建**
- 链接：https://github.com/HKUDS/nanobot/issues/4467
- 评论：2 | 点赞：1 | 创建时间：2026-06-23（已开 54 天）
- 摘要：用户希望 Dream 在已有 workspace skill 时进行增量更新，而非每次生成全新 skill 文件
- 分析：反映用户对工作区技能生命周期管理的核心诉求

---

## 5. Bug 与稳定性

| 级别 | Issue | 描述 | 状态 | 关联 PR |
|---|---|---|---|---|
| 🔴 高 | [#5305](https://github.com/HKUDS/nanobot/issues/5305) | `exec.allowPatterns` 白名单绕过，可执行未授权 Shell 命令 | OPEN | — |
| 🔴 高 | [#5377](https://github.com/HKUDS/nanobot/issues/5377) | Consolidation 截断归档输入但跳过完整消息批次，导致数据丢失 | OPEN | [#5379](https://github.com/HKUDS/nanobot/pull/5379) **已提交 fix** |
| 🟡 中 | [#5402](https://github.com/HKUDS/nanobot/issues/5402) | Token 估算（tiktoken）持续低于实际 API 返回量，导致 consolidation 永不触发 | OPEN（今日新建）| — |
| 🟡 中 | [#4864](https://github.com/HKUDS/nanobot/issues/4864) | Gateway 参数序列化变更导致 `complete_goal` 无限循环报错 | OPEN（38天未解）| — |
| 🟢 低 | [#5368](https://github.com/HKUDS/nanobot/issues/5368) | WebUI 在 Agent 运行中提前显示复制/叉分操作，造成信号冲突 | ✅ CLOSED | [#5371](https://github.com/HKUDS/nanobot/pull/5371) |

---

## 6. 功能请求与路线图信号

| PR | 功能 | 状态 | 评估 |
|---|---|---|---|
| [#5358](https://github.com/HKUDS/nanobot/pull/5358) | WebUI 会话协作（提及 @ 其他会话） | OPEN | 高价值协作功能，预计纳入下一版本 |
| [#5364](https://github.com/HKUDS/nanobot/pull/5364) | 临时侧边对话（`/side` 命令） | OPEN | 独立会话隔离需求，符合多任务工作流趋势 |
| [#5389](https://github.com/HKUDS/nanobot/pull/5389) | 会话拖拽排序与分组 | OPEN | 提升 WebUI 可用性，低冲突风险 |
| [#5398](https://github.com/HKUDS/nanobot/pull/5398) | DashScope 原生协议支持 | OPEN | 扩展中文生态覆盖，与已有 OrcaRouter 互补 |

**判断**：以上 4 条功能 PR 均处于待合并状态，其中拖拽排序（#5389）和侧边对话（#5364）用户需求明确、实现独立，纳入下一版本概率较高。

---

## 7. 用户反馈摘要

- **痛点 1 — Token 估算不准确**：[#5402](https://github.com/HKUDS/nanobot/issues/5402) 用户发现 tiktoken 估算持续低于 API 实际返回量，导致 consolidation 机制完全失效，长期运行将耗尽上下文窗口。
- **痛点 2 — 技能重复创建**：[#4467](https://github.com/HKUDS/nanobot/issues/4467) 用户反馈 Dream 每次运行都在 `skills/` 下创建新文件，即使已有维护中的 workspace skill，造成技能库膨胀。
- **痛点 3 — 安全信任**：[#5305](https://github.com/HKUDS/nanobot/issues/5305) 白名单绕过暴露了 API 层的命令执行风险，影响企业内部部署信任。
- **正面反馈**：WebUI 体验类修复（隐藏操作按钮、显示名称区分）获得及时响应，社区对迭代效率认可度较高。

---

## 8. 待处理积压

| Issue | 创建时间 | 天数 | 优先级建议 |
|---|---|---|---|
| [#4864](https://github.com/HKUDS/nanobot/issues/4864) `complete_goal` 无限循环 | 2026-07-09 | **38 天** | 🔴 高 — 影响核心目标完成流程 |
| [#4467](https://github.com/HKUDS/nanobot/issues/4467) Dream 技能重复创建 | 2026-06-23 | **54 天** | 🟡 中 — 用户体验退化，已有 Enhancement 标签 |
| [#5305](https://github.com/HKUDS/nanobot/issues/5305) 安全白名单绕过 | 2026-08-09 | 7 天 | 🔴 紧急 — 安全类 Issue 需优先响应 |
| [#5402](https://github.com/HKUDS/nanobot/issues/5402) Token 估算偏差 | 2026-08-16 | 0 天（今日）| 🟡 中 — 刚提交，需确认是否已有 fix 路径 |

---

**报告生成时间**：2026-08-16  
**数据来源**：GitHub API · HKUDS/nanobot

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-16

## 1. 今日速览

Hermes Agent 项目今日活跃度 **极高**：过去 24 小时内累计处理 100 条 issue/PR 更新（50 条 issue + 50 条 PR），其中 14 条 PR 已合并、9 条 issue 已关闭，无新版本发布。核心工作集中在 **会话状态可靠性**（TUI 中断恢复、多客户端 session 镜像）、**安全加固**（管道注入检测、图片读取边界限制）、**平台兼容性修复**（Windows 更新锁文件、WSL2 MCP 子进程）以及 **pricing 数据补齐**（GPT-5.x 系列、Z.AI / Ollama Cloud）。项目整体推进积极，技术债清理与稳定性修复并行。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日合并 / 关闭的重要 PR

| PR | 作者 | 说明 |
|---|---|---|
| [#32962](https://github.com/NousResearch/hermes-agent/pull/32962) | majordave | **WSL2 MCP 子进程追踪修复**：`/proc/<pid>/task/<pid>/children` 在 WSL2 多线程场景下返回空集，改用 `ps --ppid` 兜底；合并后同步提交了 [#87367](https://github.com/NousResearch/hermes-agent/pull/87367) 作为独立 fallback。 |
| [#76063](https://github.com/NousResearch/hermes-agent/pull/76063) | embwl0x | **安全：拒绝规则强制执行**：`approvals.deny` globs 现在在每个引号感知的可执行文件名处重新评估，env 赋值和包装命令无法再绕过安全检查。 |
| [#87362](https://github.com/NousResearch/hermes-agent/pull/87362) | teknium1 | **安全：管道-远程到-shell 检测扩展**：覆盖路径限定、Windows/MSYS 路径、引号包裹、重定向终止、sudo/env 前缀、fish/tcsh/dash/csh 等多种真实写法，大幅收紧 dangerous-command 守卫。 |
| [#87363](https://github.com/NousResearch/hermes-agent/pull/87363) | teknium1 | **安全：本地图片读取边界限制**：`resolve_image_source` 现在在读操作期间将内存缓冲上限锁定为 50 MiB + 1 字节，防止 oversized/hostile 文件耗尽主机内存。 |
| [#71735](https://github.com/NousResearch/hermes-agent/pull/71735) | fangliquanflq | **安全：Dashboard 端点探测 SSRF 防护**：`OPENAI_BASE_URL` 等自定义端点验证之前会对任意 URL 发起服务端 HTTP GET，现在已限制，防止鉴权调用者在非 loopback 绑定下探测云元数据。 |
| [#87360](https://github.com/NousResearch/hermes-agent/pull/87360) | BowmanStephen | **Pricing：Z.AI / Ollama Cloud 计费补齐**：修复 fleet audit 发现的 82 条 session 未知定价问题，将两者注册为 `subscription_included`。 |
| [#87365](https://github.com/NousResearch/hermes-agent/pull/87365) | BowmanStephen | **Pricing：GPT-5.4 / GPT-5.2 系列补齐**：`_OFFICIAL_DOCS_PRICING` 表补齐 GPT-5.4 generation 条目，修复 Insights 中未知计费问题。 |
| [#87369](https://github.com/NousResearch/hermes-agent/pull/87369) | BowmanStephen | **Pricing：快照模型 ID 日期后缀剥离**：vendor snapshot ids（如 `gpt-5.6-sol-2026-07-09`）现在正确解析为对应基础模型定价。 |
| [#87329](https://github.com/NousResearch/hermes-agent/pull/87329) | andrexibiza | **Epic 完成：Large-file decomposition 20/20 子任务全部完成**，god-file 分片重构落地，项目架构清理迈出重要一步。 |
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | zuowen7 | **关闭（回归确认）**：Windows Desktop 重启杀掉 gateway 问题已确认并关闭（修复方案待 PR）。 |

### 重点进行中的 PR

- **#87372 / #86786 / #86784 / #87371**（ryantuc）：TUI Gateway 会话恢复基础设施，将中断 turn 标记从 JSON sidecar 迁入 `state.db`，支持多客户端 attach/detach，预计构成一轮重大架构改进。
- **#87326**（teknium1）：Lean tail 压缩模式 + recall 评估 harness，报告 **+22.5pt 平均召回提升**，仅使用 30% token 保留量，有望成为下一版本默认压缩策略。
- **#87366**（alywalji7）：`delegate_task` batch 模式下按 task 指定 model/provider，实现混合廉价 worker + frontier 模型的策略性调度。
- **#87145**（gslzwhl）：Gated dashboard 引入 signed short-lived download tickets，解决外部查看器（WPS Office 等）无法附带 cookie 的 401 问题。

---

## 4. 社区热点

| Issue/PR | 评论数 | 热度分析 |
|---|---|---|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — Large-file decomposition epic 完成 | 79 | **项目架构最大话题**：god-file 分片重构历经数月讨论，最终 20/20 子任务完成，社区对"shard first, god-file 不得回退"的政策达成广泛共识。 |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index 过时/降级告警 | 37 | **基础设施可靠性担忧**：Skills Hub 索引超过 26h 限制，cron 重建间隔与部署触发逻辑存在竞态，用户关注自动化监控的实际效果。 |
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) — Desktop 重启后 gateway 不再恢复（Windows 回归） | 33 | **高优先级用户体验问题**：WeChat/QQ/Telegram 插件在 Windows 桌面重启后完全静默，影响生产用户；已关闭但待 PR 跟进。 |
| [#8457](https://github.com/NousResearch/hermes-agent/issues/8457) — Persistent Session Memory | 21 | **长期功能请求**：session memory 在 gateway 重启后丢失，用户强烈期望跨会话持久化、压缩与搜索能力，与 ryantuc 的 TUI 恢复 PR 生态高度相关。 |
| [#81048](https://github.com/NousResearch/hermes-agent/issues/81048) — Approval timeout 误报为 User denied | 8 | **Tier 1 安全问题**：命令超时被标记为用户显式拒绝，违反 Red-decision 语义，可能掩盖真实恶意操作；修复优先级高。 |
| [#86027](https://github.com/NousResearch/hermes-agent/issues/86027) — SQLite 3.53.4 vs 3.46.1 FTS5 升级兼容 | 8 | **升级路径阻塞**：v0.18.2 → v0.20.1 升级失败，legacy `messages_fts_trigram` FTS5 索引在新版 SQLite 下报 malformed。 |

---

## 5. Bug 与稳定性

### 严重（P1）

| Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | Windows Desktop 重启后 gateway 被 force-kill 且永不重启，WeChat/QQ/Telegram 静默 | 已关闭 | 待合并 |
| [#82001](https://github.com/NousResearch/hermes-agent/issues/82001) | Agent flush 在压缩后未 adopt live continuation，报错"full disk"（实际磁盘健康） | 已关闭 | 待合并 |
| [#83569](https://github.com/NousResearch/hermes-agent/issues/83569) | Windows `hermes update` 100% 失败：更新进程自身持有 `cryptography/_rust.pyd` 映射锁 | 已关闭 | [#77394](https://github.com/NousResearch/hermes-agent/issues/77394) 仍有残留 |
| [#51327](https://github.com/NousResearch/hermes-agent/issues/51327) | Linux `.desktop` 启动器静默失败：Electron chrome-sandbox 缺少 setuid 4755 | 开放 | 待修复 |

### 高优先级（P2）

| Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|
| [#87329](https://github.com/NousResearch/hermes-agent/issues/87329) | `hermes mcp login` OAuth 回调端口冲突，headless 主机无法完成认证 | 开放 | 待修复 |
| [#81048](https://github.com/NousResearch/hermes-agent/issues/81048) | Approval timeout 误标为用户显式 deny，安全语义错误 | 开放 | 待修复 |
| [#86027](https://github.com/NousResearch/hermes-agent/issues/86027) | SQLite 3.46 → 3.53 FTS5 升级破坏 legacy index | 开放 | 待修复 |
| [#58619](https://github.com/NousResearch/hermes-agent/issues/58619) | Desktop 重连时 `serve` 进程无界累积，旧进程未清理 | 开放 | 待修复 |
| [#87295](https://github.com/NousResearch/hermes-agent/issues/87295) | 第二次启动 Desktop 静默杀掉已运行实例的 backend，连接状态断开 | 开放 | 待修复 |
| [#87292](https://github.com/NousResearch/hermes-agent/issues/87292) | 慢速本地模型（>16 TPS）出现 WinError 10053 / provider unresponsive 两种超时 | 开放 | 待修复 |
| [#85315](https://github.com/NousResearch/hermes-agent/issues/85315) | `auxiliary.free_only` 门控误拒显式 `:free` 模型，并错误报告为支付/凭证错误 | 开放 | 待修复 |
| [#69107](https://github.com/NousResearch/hermes-agent/issues/69107) | 多客户端共享 session 时 TUI 不感知其他客户端写入，stale in-memory history | 开放 | #86784 部分解决 |
| [#81333](https://github.com/NousResearch/hermes-agent/issues/81333) | `computer_use` 丢弃模型发出的 placeholder `pid=0` / `window_id=0`，导致所有 app-scoped capture 失败 | 已关闭 | [#87370](https://github.com/NousResearch/hermes-agent/pull/87370) 已提交 |
| [#67165](https://github.com/NousResearch/hermes-agent/issues/67165) | macOS cua-driver ScreenCaptureKit `display_count=0`，TCC 权限正常但 capture 返回 0x0 | 已关闭 | 待修复 |

### 中优先级（P3）

| Issue | 描述 | 状态 |
|---|---|---|
| [#80439](https://github.com/NousResearch/hermes-agent/issues/80439) | Linux `hermes.desktop` 自动生成的 `Exec` 路径错误，KDE taskbar pinning 失效 | 开放 |
| [#83379](https://github.com/NousResearch/hermes-agent/issues/83379) | Qwen 模型偶尔将 fake tool invocation 写为文本而非结构化 `tool_calls` | 开放 |
| [#87356](https://github.com/NousResearch/hermes-agent/issues/

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期：2026-08-16 | 分析周期：过去24小时**

---

## 1. 今日速览

PicoClaw 今日整体活跃度较低，过去24小时内无新 Issue 提交，亦无新版本发布。PR 层面有 2 条待合并更新，均由核心贡献者 `grrowl` 维护，聚焦于性能优化（prefix caching）与依赖修复（WhatsApp 通道恢复）。项目暂无合并/关闭的 PR，整体处于稳态待推进阶段。

**活跃度评级：低（🟡）** — 贡献者活跃，但暂无社区新反馈流入。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

过去24小时内无 PR 被合并或关闭。两条待合并 PR 仍待维护者 review：

| PR | 类型 | 状态 | 更新日 |
|----|------|------|--------|
| [#3321](https://github.com/sipeed/picoclaw/pull/3321) | fix(agent) | OPEN / stale | 2026-08-15 |
| [#3320](https://github.com/sipeed/picoclaw/pull/3320) | fix(deps) | OPEN / stale | 2026-08-15 |

两条 PR 均已标记 `stale`（长期未响应），暂无进一步动作。项目整体向前推进有限，依赖维护者介入。

---

## 4. 社区热点

今日无新 Issue 或高活跃度讨论。以下两条 PR 为当前最显著的技术方向：

- **[#3321](https://github.com/sipeed/picoclaw/pull/3321)** — 动态上下文块位置调整，解决 prefix caching 失效问题。反映用户对**推理延迟优化**的持续诉求。
- **[#3320](https://github.com/sipeed/picoclaw/pull/3320)** — 升级 `whatsmeow` 依赖以恢复 WhatsApp 通道。反映**第三方平台兼容性**是用户核心痛点之一。

---

## 5. Bug 与稳定性

| 问题 | 关联 PR | 严重程度 | Fix 状态 |
|------|---------|----------|----------|
| WhatsApp 连接被拒（Client outdated 405） | [#3320](https://github.com/sipeed/picoclaw/pull/3320) | 高（功能阻断） | PR 待合并 |
| Prefix caching 失效导致性能退化 | [#3321](https://github.com/sipeed/picoclaw/pull/3321) | 中（性能） | PR 待合并 |

暂无新崩溃或回归报告。

---

## 6. 功能请求与路线图信号

今日无新功能请求 Issue。但从现有 PR 可观察到以下潜在路线信号：

- **性能优化**：[#3321](https://github.com/sipeed/picoclaw/pull/3321) 针对 prefix caching 的修复暗示项目在持续优化推理链路的缓存命中率和延迟。
- **平台兼容性维护**：[#3320](https://github.com/sipeed/picoclaw/pull/3320) 表明 WhatsApp 通道是活跃使用场景，依赖升级是维持兼容性的必要动作。

---

## 7. 用户反馈摘要

今日无新 Issue，无法提取新的用户评论。基于两条 PR 的描述可间接推断：

- **痛点**：WhatsApp 通道因依赖版本过旧导致连接断开，影响实际使用。
- **满意方向**：prefix caching 优化有望提升 Agent 响应速度，符合用户对低延迟的期望。

---

## 8. 待处理积压

| 项目 | 状态 | 创建日 | 最后更新 | 风险 |
|------|------|--------|----------|------|
| [#3321](https://github.com/sipeed/picoclaw/pull/3321) | OPEN / stale | 2026-08-07 | 2026-08-15 | 性能优化被阻塞 |
| [#3320](https://github.com/sipeed/picoclaw/pull/3320) | OPEN / stale | 2026-08-07 | 2026-08-15 | WhatsApp 功能持续不可用 |

> ⚠️ 两条 PR 均已超过 9 天未获维护者响应，建议优先 review 合并，以恢复 WhatsApp 通道并释放缓存优化收益。

---

**项目健康度总结：** 核心贡献者持续提交修复，但 PR 积压且缺乏社区新反馈，维护者介入是打破当前停滞的关键。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-08-16

---

## 1. 今日速览

NanoClaw 在过去 24 小时内保持**高频开发节奏**，共 22 条 PR 更新，其中 19 条仍待合并，3 条已关闭/合并，Issues 暂无新增。项目当前处于多通道架构扩展的关键窗口期：Telegram 频道适配器的端到端功能已基本落地，围绕 Channel Registry 的多项核心扩展（A1–A8）集中提交，涵盖权限拦截、交付预览、跨会话上下文等模块。gavrielc 为今日核心贡献者，贡献了约 14 条 PR，覆盖了权限、通道、交付、容器、数据库等多个子系统。项目整体健康度良好，代码覆盖率高（1483 测试通过），无回归信号。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭（3 条）

| PR | 类型 | 说明 |
|---|---|---|
| [#3268](https://github.com/nanocoai/nanoclaw/pull/3268) | Bug 修复 | 修复 `runPollLoop` 停止后遗留活跃查询的 follow-up poller，避免轮询循环泄漏资源 |
| [#37](https://github.com/nanocoai/nanoclaw/pull/37) | 项目更名 | 完成从 nanoclaw → dotclaw 的更名及 WhatsApp → Telegram 迁移 |
| *3rd* | — | 数据中未明确列出第三条已关闭 PR |

### 关键待合并 PR

- **#3269** — Telegram 频道适配器（`@chat-adapter/telegram`）正式落地，含配对流程与 Markdown 净化器，1483 测试全部通过，端到端验证完成。
- **#3266** — 新增 `registerChannelCardInterceptor` 钩子，允许模块在注册审批前拦截渠道卡片，支持自动绑定/拒绝/忽略策略。
- **#3264** — 新增 `registerDeliveryBatchPreview` 钩子，可在消息批量投递前预读取内容，用于预加载扩展资源。
- **#3263** — 新增 `startChannelAdapter(key)`，支持热启动已注册适配器，绕过初始化阶段直接激活。
- **#3257** — 跨会话上下文模块：支持会话间消息扇出、DM 回填、echo 剪枝，以及 `ncl sessions history` CLI 命令。
- **#3254** — 修复入站批次选择逻辑，采用两阶段选择避免 context 行挤占任务行。
- **#3255** — 修复出站交付目标解析 bug，多个实例共享同一地址时正确路由到发送者自身实例。

> **整体推进评估**：今日 PR 密集覆盖了"通道注册审批→投递预览→跨会话上下文"的完整链路，项目正向多代理协作（agent-to-agent）与多通道编排方向明显演进。

---

## 4. 社区热点

### 今日最活跃 PR（按贡献密度排序）

1. **[#3269 — Telegram 频道集成](https://github.com/nanocoai/nanoclaw/pull/3269)**（rudysmets7-strid）
   - 首次为 NanoClaw 增加 Telegram Channel（非 Bot）适配，覆盖配对流程与 Markdown 净化，测试通过 1483 项。
   - **诉求分析**：社区对 Telegram 多形态支持（Bot + Channel）需求强烈，#37 已完成 Bot 切换，#3269 补齐 Channel 能力。

2. **[#3251 — 修复 Agent Runner 心跳停滞](https://github.com/nanocoai/nanoclaw/pull/3251)**（DawoudIO）
   - 修复 Claude API 限速时心跳文件 30+ 分钟未更新，导致容器被误判为 stale 而终止。
   - **诉求分析**：生产环境中 API 限速是常见场景，此前心跳机制依赖 API 事件而非定时写入，属设计缺陷。

3. **[#3250 — 修复 Telegram Markdown 加粗降级为斜体](https://github.com/nanocoai/nanoclaw/pull/3250)**（chiptoe-svg）
   - 移除遗留的 Markdown 净化器，解决 `**bold**` 被错误渲染为斜体的问题。
   - **诉求分析**：`telegram-markdown-sanitize.ts` 原为兼容旧版 `parse_mode=Markdown` 的 workaround，随着适配器升级已无需保留。

4. **[#3260 — unknown-sender 拒绝通知策略](https://github.com/nanocoai/nanoclaw/pull/3260)**（gavrielc）
   - 新增 `decline_notify` 政策：优雅拒绝未知发送者并通知 owner，而非静默丢弃或弹审批卡片。
   - **诉求分析**：此前仅有 strict（丢弃）和 request_approval（审批卡片）两种策略，社区期望更精细的未知发送者处理。

---

## 5. Bug 与稳定性

| 严重度 | PR | 问题描述 | 状态 |
|---|---|---|---|
| 🔴 高 | [#3251](https://github.com/nanocoai/nanoclaw/pull/3251) | 心跳停滞导致容器被误杀（30+ 分钟） | OPEN |
| 🟡 中 | [#3268](https://github.com/nanocoai/nanoclaw/pull/3268) | 轮询循环停止后遗留 follow-up poller 泄漏 | ✅ 已关闭 |
| 🟡 中 | [#3255](https://github.com/nanocoai/nanoclaw/pull/3255) | 多实例共享地址时出站交付路由到错误实例 | OPEN |
| 🟡 中 | [#3254](https://github.com/nanocoai/nanoclaw/pull/3254) | context 行积压挤占任务行，导致任务不执行 | OPEN |
| 🟢 低 | [#3250](https://github.com/nanocoai/nanoclaw/pull/3250) | Telegram Markdown 加粗被降级为斜体 | OPEN |
| 🟢 低 | [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) | Discord 入站附件（文本/图片）无法到达 Agent | OPEN（长期未合） |

> **稳定性评估**：今日修复集中在三个高风险点——心跳机制、交付路由、批次选择，均为生产环境常见故障场景，修复后预计可显著降低误杀率和投递失败率。

---

## 6. 功能请求与路线图信号

| 信号 | PR | 方向 |
|---|---|---|
| 多通道热插拔 | [#3263](https://github.com/nanocoai/nanoclaw/pull/3263) | 支持运行时启动/停止适配器，无需重启容器 |
| 通道审批拦截 | [#3266](https://github.com/nanocoai/nanoclaw/pull/3266) | 模块化扩展渠道注册审批流程 |
| 投递前预览 | [#3264](https://github.com/nanocoai/nanoclaw/pull/3264) | 扩展点用于预加载/速率限制/审计 |
| 跨会话上下文 | [#3257](https://github.com/nanocoai/nanoclaw/pull/3257) | 多代理协作的核心能力：消息扇出、DM 回填 |
| 可选能力扩展 | [#3261](https://github.com/nanocoai/nanoclaw/pull/3261) | `setTyping`、`setThreadTitle`、`setSuggestedPrompts` 等可选适配器能力 |
| 未知发送者策略 | [#3260](https://github.com/nanocoai/nanoclaw/pull/3260) | 新增 decline_notify，细粒度控制未知用户交互 |
| Channel 适配器 | [#3269](https://github.com/nanocoai/nanoclaw/pull/3269) | Telegram Channel 支持，与 Bot 形成双通道覆盖 |

> **路线图判断**：项目明显在向"多通道+多代理协作"架构演进，`channels` 子系统今日是最高优先级。以下功能大概率纳入下一版本：跨会话上下文、通道热插拔、投递预览钩子、未知发送者策略。

---

## 7. 用户反馈摘要

- **Discord 附件无法使用**（[#2752](https://github.com/nanocoai/nanoclaw/pull/2752)，创建于 2026-06-12，开放超 2 个月）：用户反馈 Discord 入站附件（图片和粘贴文本）到达 Agent 时仅为 `[file: message.txt]` 占位符，无实际内容。Chat SDK Bridge 未下载附件。
- **心跳误杀**（[#3251](https://github.com/nanocoai/nanoclaw/pull/3251)）：API 限速时容器被误判为卡死而终止，影响生产环境稳定性。
- **Markdown 渲染异常**（[#3250](https://github.com/nanocoai/nanoclaw/pull/3250)）：Telegram 渠道中加粗文本被错误渲染为斜体，属于遗留 workaround 导致。
- **多实例路由错误**（[#3255](https://github.com/nanocoai/nanoclaw/pull/3255)）：同一频道内多个 Bot 实例时，出站消息可能路由到错误实例。
- **心跳文件缺失豁免**（[#3252](https://github.com/nanocoai/nanoclaw/pull/3252)）：无心跳文件的空闲容器应豁免绝对超时杀死，防止调试/开发环境被误杀。

---

## 8. 待处理积压

| PR | 创建时间 | 状态 | 说明 |
|---|---|---|---|
| [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) | 2026-06-12 | OPEN | Discord 附件无法到达 Agent，开放超 2 个月未合，用户痛点明确 |
| [#3253](https://github.com/nanocoai/nanoclaw/pull/3253) | 2026-08-15 | OPEN | opencode 模式未遵循 group reasoning effort 配置，修复类 PR |
| [#3252](https://github.com/nanocoai/nanoclaw/pull/3252) | 2026-08-15 | OPEN | 无心跳文件的空闲容器豁免杀死逻辑，需 review |
| [#3259](https://github.com/nanocoai/nanoclaw/pull/3259) | 2026-08-15 | OPEN | skill-apply 步骤编号错误 + headless browser URL 暴露问题，小型工具修复 |

> **维护者关注建议**：[#2752](https://github.com/nanocoai/nanoclaw/pull/3252) 已开放超 2 个月，Discord 附件问题是用户体验的关键阻塞点，建议优先 review。今日 19 条待合并 PR 数量较多，建议分批合并以降低回归风险。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目动态日报 | 2026-08-16

## 1. 今日速览
NullClaw 项目在 2026-08-16 保持稳健的低频维护节奏：过去 24 小时内仅有 1 条 Issue 与 1 条 PR 更新，无新版本发布。整体活跃度处于常规迭代区间，未见紧急故障或大规模功能推进。社区信号明确指向网络层扩展（代理支持）与本地 Agent 运行时性能优化，项目健康度良好，技术演进方向清晰。

## 2. 版本发布
无新版本发布。当前版本保持稳定，无破坏性变更或迁移注意事项。

## 3. 项目进展
今日无已合并/关闭的 PR。处于评审阶段的 PR [#987](https://github.com/nullclaw/nullclaw/pull/987) 针对长程、重工具调用的本地 Agent 运行场景进行了架构级优化：
- 将系统提示词拆分为缓存友好的静态前缀与动态时间戳后缀，配合 `stablePrefixHash` 提升缓存命中率；
- 引入工具输出压缩机制（`result_compress.zig`），压缩后注入历史，但观察者日志仍保留完整输出；
- 增加单轮重复调用检测逻辑，防止工具循环导致的 Token 与内存浪费。
该 PR 若通过审查并合并，将显著提升本地 Agent 的运行效率与稳定性，是推动项目向“高吞吐本地推理”演进的关键一步。

## 4. 社区热点
- **[Issue #988](https://github.com/nullclaw/nullclaw/issues/988)** `[enhancement] proxy support`（作者: anpic，2026-08-15）
  **诉求分析**：明确要求为 Provider 层添加 HTTP(S) 与 SOCKS5h 代理支持。该需求反映出用户对多云部署、企业内网穿透及受限网络环境的适配诉求，是个人 AI 助手类 Agent 框架走向生产可用性的常见瓶颈。
- **[PR #987](https://github.com/nullclaw/nullclaw/pull/987)** `[feat] loop hygiene for long local tool-heavy runs`（作者: vernonstinebaker，2026-08-15）
  **技术信号**：聚焦 prompt 缓存策略与工具输出压缩，标志着项目重心正从“基础功能集成”向“运行时性能优化”阶段过渡。

## 5. Bug 与稳定性
今日未收到任何 Bug 报告、崩溃日志或回归问题反馈。项目近期稳定性表现平稳，未出现紧急修复需求。

## 6. 功能请求与路线图信号
- **代理支持（Issue #988）**：明确指向网络层扩展，预计将纳入下一版本的 Provider 配置优化。建议维护者评估主流代理协议的优先级与实现路径。
- **本地长程 Agent 优化（PR #987）**：从 PR 描述可推断，路线图正侧重降低本地工具密集型任务的延迟与 Token 消耗，提示词缓存与输出压缩有望成为后续性能调优的标准模块。

## 7. 用户反馈摘要
当日数据中用户评论为零，但核心诉求清晰：
- Issue [#988](https://github.com/nullclaw/nullclaw/issues/988) 直接点出代理缺失这一部署痛点，适用于需要出站流量管控或跨网络访问 LLM Provider 的场景。
- PR [#987](https://github.com/nullclaw/nullclaw/pull/987) 虽暂无用户互动，但其针对“工具调用循环”的优化方向契合了本地部署用户对长时间运行稳定性的核心诉求。
整体反馈呈现“需求明确、技术响应前置”的健康态势。

## 8. 待处理积压
- **[PR #987](https://github.com/nullclaw/nullclaw/pull/987)**：代码已提交但尚未进入评论/合并阶段，建议维护者尽快安排评审，以加速本地 Agent 性能优化的落地。
- **[Issue #988](https://github.com/nullclaw/nullclaw/issues/988)**：作为新增功能请求，当前无维护者回复或关联 PR，建议确认排期或引导贡献者认领实现。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期：2026-08-16**

---

## 1. 今日速览

过去24小时 IronClaw 项目保持高活跃度：**27 条 Issue 更新**（6 新开 / 21 关闭），**12 条 PR 动态**（7 待合并 / 5 已合并）。今日无新版本发布，但多项性能优化与架构重构已合入主干，核心聚焦于：(1) 完成 `unbound-turns` 到 `prepared-context turns` 的切换；(2) 大幅削减数据库写入压力（心跳日志、线程索引合并、触发器状态写入优化）；(3) 修复 Live Canary 测试套件中三类测试工具缺陷导致的误报。项目整体处于**高质量技术债务偿还阶段**，健康度良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并 / 关闭的重要 PR

| PR | 类型 | 摘要 |
|----|------|------|
| [#7634](https://github.com/nearai/ironclaw/pull/7634) | **feat** | 完成 `unbound-turns` → `prepared-context turns` 的最终切换，通过 71 条款合规审计，是长期演进的核心里程碑 |
| [#7676](https://github.com/nearai/ironclaw/pull/7676) | **perf** | 合并线程索引的突发写入，使用单调 CAS 更新保证多 Worker 正确性 |
| [#7629](https://github.com/nearai/ironclaw/pull/7629) | **perf** | 将 `prune_run_history` 从每次 Running 行更新移至初始 fire claim，减少大量冗余写入 |
| [#7628](https://github.com/nearai/ironclaw/pull/7628) | **perf** | 停止每心跳写入 `ProcessJournalKind::Heartbeat` 行，同时将心跳间隔从 5s 放宽至 15s |
| [#7670](https://github.com/nearai/ironclaw/pull/7670) | **chore** | 刷新代码库知识图谱快照（CI 自动触发） |

**推进小结：** 本轮合并以**数据库写入优化**为主轴（Issues #7591 Epic 下的 Tier 1/2 清理），预计单进程每日可节省约 **2,880 条永久日志行**，线程索引写入从每次-turn 多次 CAS 降为每 interval ≤1 次。同时 `prepared-context turns` 切换完成，为后续 Reborn 架构统一奠定基础。

### 待合并重点 PR

- [#7491](https://github.com/nearai/ironclaw/pull/7491) — **核心编码工具合约重构**：统一为 6 个精确裸名（`read/write/edit/glob/grep/bash`），移除遗留混合表面
- [#7679](https://github.com/nearai/ironclaw/pull/7679) — **修复 Live QA 工具缺陷**：停止测试框架本身导致误报（30/30 连续红灯问题）
- [#7678](https://github.com/nearai/ironclaw/pull/7678) — **能力调用状态持久化**：在门控和终端边界原子化落地调用状态
- [#7677](https://github.com/nearai/ironclaw/pull/7677) — **消息查找索引折叠进消息行**：消除每条消息 1-3 条冗余兄弟行写入
- [#7651](https://github.com/nearai/ironclaw/pull/7651) — **自动化无结果抑制**：基于模型推导的确定性 suppression 语义
- [#7516](https://github.com/nearai/ironclaw/pull/7516) — **WebUI 新增 IronHub Agent 链接操作面板**（新贡献者）

---

## 4. 社区热点

| Issue | 类型 | 热度说明 | 链接 |
|-------|------|----------|------|
| [#467](https://github.com/nearai/ironclaw/issues/467) | 功能提议 | 作者 zmanian 提出**轨迹基准测试系统**，支持硬断言 + LLM-as-judge 双层评估，4 条评论 | [Issue #467](https://github.com/nearai/ironclaw/issues/467) |
| [#3236](https://github.com/nearai/ironclaw/issues/3236) | 架构设计 | Reborn 同线程后续消息与引导策略定义，覆盖 `/btw`、队列排序、取消交互等，3 条评论 | [Issue #3236](https://github.com/nearai/ironclaw/issues/3236) |
| [#6821](https://github.com/nearai/ironclaw/issues/6821) | Bug | IronHub 搜索返回结果与签名目录严重不符（报告 3 个 vs 实际 18 个），已在 PR #6780 部署中复现 | [Issue #6821](https://github.com/nearai/ironclaw/issues/6821) |
| [#7671–#7675](https://github.com/nearai/ironclaw/issues/7671) | 架构/测试 | henrypark133 基于 #7634 审查连续提出 5 条关注点：E2E flake、依赖边界符号级审计、预算分类账双重计费、`Typed ToolChoice`、栈深度压力 | [Issue #7671](https://github.com/nearai/ironclaw/issues/7671) · [Issue #7672](https://github.com/nearai/ironclaw/issues/7672) · [Issue #7673](https://github.com/nearai/ironclaw/issues/7673) · [Issue #7674](https://github.com/nearai/ironclaw/issues/7674) · [Issue #7675](https://github.com/nearai/ironclaw/issues/7675) |

**热点分析：** 社区反馈呈现两个鲜明趋势——(1) **测试可靠性焦虑**：henrypark133 集中提出的 5 个问题均与 `prepared-context turns` 切换后的边界行为和 E2E 稳定性有关；(2) **可观测性需求**：Issue #467 轨迹基准系统和 Issue #7673 预算分类账双重计费问题，反映出用户对 Agent 行为可验证性和成本可控性的强烈诉求。

---

## 5. Bug 与稳定性

| Issue | 严重度 | 摘要 | Fix PR | 链接 |
|-------|--------|------|--------|------|
| [#7675](https://github.com/nearai/ironclaw/issues/7675) | 🔴 高 | `qa_6c_gmail_to_sheet` E2E 间歇性失败，能力调用在 provider-contracts session 内级联崩溃 | 待分配 | [Issue #7675](https://github.com/nearai/ironclaw/issues/7675) |
| [#6835](https://github.com/nearai/ironclaw/issues/6835) | 🟡 中 | MCP `AuthRequired` 被错误分类为 `Client` 而非触发重认证门控 | 已关闭（分类修正） | [Issue #6835](https://github.com/nearai/ironclaw/issues/6835) |
| [#5239](https://github.com/nearai/ironclaw/issues/5239) | 🟡 中 | 调度器将已完成 run 的陈旧心跳误判为 runner 失败，产生错误 terminal-failure 路径 | 已关闭 | [Issue #5239](https://github.com/nearai/ironclaw/issues/5239) |
| [#5237](https://github.com/nearai/ironclaw/issues/5237) | 🟢 低 | Reborn hosted 环境下 Cranelift/Wasmtime DEBUG 日志淹没 Railway | 已关闭 | [Issue #5237](https://github.com/nearai/ironclaw/issues/5237) |
| [#4992](https://github.com/nearai/ironclaw/issues/4992) | 🟡 中 | Railway local-dev SSO 访问不匹配导致自动化在 turn/thread 创建前就失败 | 已关闭 | [Issue #4992](https://github.com/nearai/ironclaw/issues/4992) |

**稳定性评估：** 今日关闭的 21 条 Issue 中以 Bug 修复和性能问题为主，说明团队在主动清扫历史债务。待处理的高优先级 Bug 集中在 E2E 测试稳定性（#7675），需持续关注。

---

## 6. 功能请求与路线图信号

| Issue / PR | 诉求 | 路线图判断 |
|------------|------|------------|
| [#467](https://github.com/nearai/ironclaw/issues/467) | 轨迹基准测试系统（Hard Assertions + LLM-as-Judge） | 与 #4775 Reborn 自动化 QA Epic 高度对齐，可能纳入下一阶段 QA 基础设施 |
| [#7672](https://github.com/nearai/ironclaw/issues/7672) | `Typed ToolChoice`：替换各 Provider 中的重载字符串 `tool_choice` | 已在 #7634 审查中被标记，需独立 PR 处理，预计下一迭代 |
| [#7673](https://github.com/nearai/ironclaw/issues/7673) | BudgetLedger 双重计费修复（截断启动窗口导致 over-count） | 直接影响成本准确性，优先级高，应快速跟进 |
| [#7651](https://github.com/nearai/ironclaw/pull/7651) | 自动化确定性无结果抑制 | 待合并，属于 automations 模块的可用性改进 |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) | WebUI 操作面板支持 IronHub Agent 链接 | 新贡献者 PR，扩展 WebUI 功能边界 |

---

## 7. 用户反馈摘要

从 Issue 评论和 PR 讨论中提炼：

- **测试可信度焦虑**：Live Canary 连续 30/30 失败（#7679），但根因是**测试工具本身的缺陷**而非产品行为——三条正确行为被误报，一条 liveness proxy 导致误判。社区对 CI 信号可信度提出强烈关注。
- **Provider 兼容性痛点**：MCP 认证失败分类错误（#6835）和 `tool_choice` 字符串重载问题（#7672）反映出多 Provider 适配层的复杂度仍在累积，用户期望更类型安全的接口。
- **成本可预测性需求**：BudgetLedger 双重计费（#7673）和 IronHub 搜索结果不符（#6821）直接冲击用户信任，前者导致"过早停止、实际未超支"的保守误判。
- **本地开发体验**：Railway local-dev SSO 问题（#4992）和 Reborn/Crabshack 遗留代码清理（#4629）表明迁移期用户对两套运行时并存感到困惑。
- **正面反馈**：`prepared-context turns` 切换完成（#7634）获得审查团队一致认可，71 条款合规审计通过是架构统一的重要信号。

---

## 8. 待处理积压

| Issue / PR | 状态 | 风险 | 建议 |
|------------|------|------|------|
| [#7675](https://github.com/nearai/ironclaw/issues/7675) | OPEN（今日新建） | 🔴 高 | E2E flake 级联影响 provider-contracts session，建议优先排入下一迭代 |
| [#7671](https://github.com/nearai/ironclaw/issues/7671) | OPEN | 🟡 中 | 能力分发栈深度在 kernel sandbox 路径仍接近测试栈边界（2 MiB），已部分修复但需回归验证 |
| [#7674](https://github.com/nearai/ironclaw/issues/7674) | OPEN | 🟡 中 | `openai-compat → threads` 依赖边界的符号级审计，当前仅门控 crate 级依赖，需收窄至符号级 |
| [#7673](https://github.com/nearai/ironclaw/issues/7673) | OPEN | 🟡 中 | BudgetLedger 双重计费，影响成本准确性，需独立 PR 修复 |
| [#7672](https://github.com/nearai/ironclaw/issues/7672) | OPEN | 🟢 低 | `Typed ToolChoice` 重构，技术复杂度中等，可并行推进 |
| [#467](https://github.com/nearai/ironclaw/issues/467) | OPEN（创建较早） | 🟢 低 | 轨迹基准测试系统，属于中长期基础设施，建议与 #4775 QA Epic 对齐后启动 |

---

**整体健康度：🟢 良好** — 项目正处于架构统一后的性能优化窗口期，数据库写入压力显著降低，测试工具缺陷正在修复，新贡献者开始参与（#7516）。建议优先跟进 #7675 E2E flake 和 #7673 预算计费修复，这两项直接影响用户可信度。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报
**日期：2026-08-16** | 数据周期：过去24小时

---

## 1. 今日速览

今日 LobsterAI 项目活跃度较高，共更新 18 条 Issues（其中 16 条已关闭）、6 条 PR（2 条合并/关闭）。项目维护者对社区反馈响应迅速，大部分提交的问题均已妥善处理。无新版本发布。项目整体健康度良好，社区参与度高，问题闭环率高，但仍有一些关键体验问题（如登录、微信配置）和长期需求（如记忆体系）有待持续跟进。

---

## 2. 版本发布

> 本周期内无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（2 条）

| PR | 摘要 | 意义 |
|----|------|------|
| [#1879](https://github.com/netease-youdao/LobsterAI/issues/1879) | 修复配置同步时手动添加的插件路径被覆盖的问题 | 解决用户自定义插件路径在 OpenClawConfigSync 同步时被静默丢弃的 bug，提升插件管理稳定性 |
| [#2234](https://github.com/netease-youdao/LobsterAI/issues/2234) | 修复 cron yield 场景下子 agent 完成事件无法驱动父 agent 继续执行的问题 | 覆盖普通会话并行子 agent、cron 并行/串行子 agent 三种场景，修复了 yield 状态下 completion 事件被错误写入已结束 run 的缺陷 |

**前进评估：** 本次合并的 PR 集中在 **配置管理** 和 **Agent 调度机制** 两个核心模块，均为影响多 agent 协作稳定性的底层问题，修复后对项目可用性有明显提升。

---

## 4. 社区热点

### 高讨论度 Issues（按评论数/关注度排序）

| Issue | 标题 | 状态 | 评论 | 链接 |
|-------|------|------|------|------|
| #2040 | OpenClaw 的五大薄弱点 | ✅ Closed | 2 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2040) |
| #2041 | 最大的瓶颈不是进化算法，而是记忆系统 | ✅ Closed | 2 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2041) |
| #2046 | Agent 记忆体系产品建议 | 🔄 Open | 2 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2046) |
| #1903 | 会员登录频繁失败 | 🔄 Open | 3 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1903) |
| #1988 | 阿里百炼 qwen3.6-plus 无法正常调用 | ✅ Closed | 3 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1988) |
| #1885 | 邮箱 SKILL 路径穿越漏洞 | ✅ Closed | 2 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1885) |

**热点分析：**
- **记忆体系** 是当前社区讨论的核心主题，#2040/#2041 从产品和技术两个维度深度剖析了 OpenClaw/LobsterAI 在记忆能力上的短板，#2046 提出了系统性的产品建议，表明用户希望 Agent 具备跨会话、跨任务的知识积累能力。
- **安全漏洞**（#1885）引发关注，邮箱附件路径穿越漏洞涉及文件操作安全，已关闭但提醒项目需加强技能（Skill）代码的输入校验。
- **付费体验**（#1903）仍未解决，会员登录失败直接影响付费用户权益，是当前最突出的待处理问题。

---

## 5. Bug 与稳定性

### 已关闭的 Bug 修复（5 条）

| Issue | 描述 | 严重程度 | 链接 |
|-------|------|----------|------|
| #1849 | 追问时出现无限 NO_REPLY 或输出中断 | 🟡 中 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1849) |
| #1920 | Cowork 初始化显示空白 Loading 而非 skeleton 屏 | 🟡 低 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1920) |
| #1971 | 会话页超长元素（如 Mermaid）导致滚动异常/无限重渲染 | 🟠 中高 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1971) |
| #1993 | 桌面端 AI engine 连接丢失（IM Bot 正常） | 🟠 中高 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1993) |
| #2039 | Dreaming 开关配置写入错误路径，Gateway 重启后配置丢失 | 🟡 中 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2039) |

### 待处理 Bug（1 条）

| Issue | 描述 | 严重程度 | 链接 |
|-------|------|----------|------|
| #1903 | 会员登录频繁失败，无法使用网易付费模型 | 🔴 高 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1903) |

> **说明：** #1903 涉及付费用户核心体验，建议优先跟进。其他已关闭的 Bug 均涉及 UI/UX 细节和调度机制，影响面相对有限。

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 优先级判断 | 链接 |
|-------|----------|------------|------|
| #2046 | Agent 记忆体系（Session 标题持久化、跨会话检索、历史对话关联） | 🔴 高（社区呼声强烈） | [链接](https://github.com/netease-youdao/LobsterAI/issues/2046) |
| #1880 | 集成 Hermes Agent 功能（参考 Open WebUI） | 🟡 中 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1880) |
| #2016 | 增加 OpenHuman 引擎支持 | 🟡 中 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2016) |
| #2036 | OpenClaw gateway 增加 `agent:turn` / `agent:loop` 事件广播 | 🟠 中高 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2036) |
| #1836 | 整体 UI 重新设计美化 | 🟡 中 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1836) |

**路线图信号分析：**
- **Agent 记忆体系** 是当前最明确的产品方向，#2040/#2041 的技术分析和 #2046 的产品建议已形成完整闭环，建议纳入下一版本核心迭代。
- **#2036** 提出的 gateway 事件广播机制与 #2234 已合并的 cron yield 修复高度相关，可能构成后续调度优化的基础能力。
- **Hermes Agent / OpenHuman** 属于扩展性需求，需评估与现有 OpenClaw 架构的兼容性。

---

## 7. 用户反馈摘要

### 痛点
- **付费体验不佳：** 会员登录频繁失败（#1903），阿里百炼模型被强制切换至网易自带模型（#1988），付费用户权益未得到保障。
- **微信 IM 配置流程阻塞：** 扫码后无输入界面，无法完成验证码输入（#1878），移动端配置体验断裂。
- **滚动与渲染问题：** 会话页含超长内容（Mermaid 图表等）时滚动异常，虚拟滚动高度计算错误导致无限重渲染（#1971）。
- **UI 细节粗糙：** Skeleton 加载状态缺失（#1920）、空状态无图标（#1921）、整体设计落后于竞品（#1836）。

### 满意点
- 项目对社区反馈响应迅速，大部分 Issue 在提交后短时间内即被关闭/修复。
- 安全漏洞（#1885）能被及时发现并关闭，体现社区安全意识。
- 技术讨论深入（#2040/#2041），用户不仅反馈问题，还提供了产品级思考。

---

## 8. 待处理积压

| Issue | 创建时间 | 状态 | 建议关注度 | 链接 |
|-------|----------|------|------------|------|
| #1903 | 2026-05-07 | 🔄 Open | 🔴 高 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1903) |
| #2046 | 2026-05-25 | 🔄 Open | 🔴 高 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2046) |
| #1880 | 2026-05-03 | ✅ Closed | 🟡 中 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1880) |
| #2016 | 2026-05-20 | ✅ Closed | 🟡 中 | [链接](https://github.com/netease-youdao/LobsterAI/issues/2016) |

> **维护者提醒：**
> - **#1903** 自 2026-05-07 提交至今仍处于 Open 状态，已历时近 3 个月，涉及付费用户核心功能，建议尽快响应。
> - **#2046** 提出了系统性的记忆体系方案，结合 #2040/#2041 的技术分析，建议评估纳入 Q3 迭代计划。
> - **#1880 / #2016** 虽已关闭，但功能需求未被实现，可标记为 Feature Request 持续跟踪。

---

*报告生成时间：2026-08-16*  
*数据来源：[LobsterAI GitHub](https://github.com/netease-youdao/LobsterAI)*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 | 2026-08-16

## 1. 今日速览

Moltis 项目今日保持较高活跃度，过去24小时内共处理 **18 条** 更新（2 Issues + 16 PRs），其中 **16 条已关闭**，仅 2 条仍待合并。今日进展以**安全加固**和**功能扩展**为主，包括路径遍历修复、节点配对签名验证、zvec 向量数据库后端接入，以及日历/邮件/Slack 等连接器新增。项目整体健康度良好，维护者响应及时，bug 修复与功能迭代同步推进。

---

## 2. 版本发布

今日无新版本发布（Releases: 0）。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 | 链接 |
|----|------|------|------|
| #1180 | 🔒 安全 | 加固模型和 zip 路径，修复任意文件写入漏洞 | [PR #1180](https://github.com/moltis-org/moltis/pull/1180) |
| #1179 | 🔒 安全 | 验证节点配对签名，防止恶意密钥注入 | [PR #1179](https://github.com/moltis-org/moltis/pull/1179) |
| #1158 | ✨ 功能 | 新增 `zvec` 向量数据库 memory 后端（feature-gated） | [PR #1158](https://github.com/moltis-org/moltis/pull/1158) |
| #1182 | 🐛 修复 | 允许删除/归档 main session，修复 Issue #1132 | [PR #1182](https://github.com/moltis-org/moltis/pull/1182) |
| #1190 | ✨ 功能 | 新增持久化日历、频道、邮件连接器（CalDAV、Gmail、Himalaya v2） | [PR #1190](https://github.com/moltis-org/moltis/pull/1190) |
| #1195 | ✨ 功能 | 新增 Slack 原生 live task cards 支持 | [PR #1195](https://github.com/moltis-org/moltis/pull/1195) |
| #1191 | 🐛 修复 | 修正 sandbox gogcli 模块路径至 openclaw org | [PR #1191](https://github.com/moltis-org/moltis/pull/1191) |
| #1192 | 🐛 修复 | 修正 wacrawl 安装元数据路径至 openclaw org | [PR #1192](https://github.com/moltis-org/moltis/pull/1192) |
| #1196 | 🐛 修复 | 修复 ClawHub 技能搜索结果超时问题 | [PR #1196](https://github.com/moltis-org/moltis/pull/1196) |
| #1197 | ✨ 功能 | 支持从命令面板启动 agent 聊天 | [PR #1197](https://github.com/moltis-org/moltis/pull/1197) |
| #1198 | ✨ 功能 | 路由 OpenAI reasoning tool calls 通过 Responses API | [PR #1198](https://github.com/moltis-org/moltis/pull/1198) |
| #1194 | 🐛 修复 | 修复 macOS bash 3.2 空数组展开导致的脚本崩溃 | [PR #1194](https://github.com/moltis-org/moltis/pull/1194) |
| #1200 / #1184 | 📦 依赖 | dependabot 更新 npm 依赖（postcss、js-yaml、undici） | [PR #1200](https://github.com/moltis-org/moltis/pull/1200) · [PR #1184](https://github.com/moltis-org/moltis/pull/1184) |

**整体进展评估**：今日共合并 14 条 PR，涵盖 2 个安全修复、5 个新功能、7 个 bug 修复。项目在安全性和功能丰富度上均有实质性推进。

---

## 4. 社区热点

### 关注 Issue/PR

| 项目 | 状态 | 说明 | 链接 |
|------|------|------|------|
| #1132 | ✅ 已关闭 | main session 无法删除/归档，社区长期诉求，已由 PR #1182 修复 | [Issue #1132](https://github.com/moltis-org/moltis/issues/1132) |
| #1189 | ✅ 已关闭 | Sandbox build 因 gogcli URL 错误失败，与 PR #1191 对应 | [Issue #1189](https://github.com/moltis-org/moltis/issues/1189) |
| #1180 | ✅ 已合并 | 安全维护者 tsauvajon 推动的路径遍历修复，影响范围较大 | [PR #1180](https://github.com/moltis-org/moltis/pull/1180) |
| #1179 | ✅ 已合并 | 同一维护者推动的节点配对签名验证 | [PR #1179](https://github.com/moltis-org/moltis/pull/1179) |

**热点分析**：
- 安全类 PR（#1180、#1179）由核心维护者 `tsauvajon` 主导，反映项目对安全性的重视度提升。
- Issue #1132 自 2026-06-18 创建后近两个月才被关闭，说明该功能缺口已被社区长期感知，修复具有正面影响。
- Sandbox/构建相关修复（#1191、#1192、#1194）集中于 `Lstarsky0`，显示其对开发体验的持续关注。

---

## 5. Bug 与稳定性

| 优先级 | 问题 | 状态 | Fix PR | 链接 |
|--------|------|------|--------|------|
| 🔴 高 | 恶意 zip/HuggingFace repo 可导致任意文件写入（PR #1180） | ✅ 已修复 | #1180 | [PR #1180](https://github.com/moltis-org/moltis/pull/1180) |
| 🔴 高 | 节点配对可被注入恶意密钥（PR #1179） | ✅ 已修复 | #1179 | [PR #1179](https://github.com/moltis-org/moltis/pull/1179) |
| 🟡 中 | main session 无法删除/归档（#1132） | ✅ 已修复 | #1182 | [Issue #1132](https://github.com/moltis-org/moltis/issues/1132) |
| 🟡 中 | Sandbox build 因 gogcli 路径错误失败（#1189） | ✅ 已修复 | #1191 | [Issue #1189](https://github.com/moltis-org/moltis/issues/1189) |
| 🟡 中 | wacrawl 安装元数据路径错误 | ✅ 已修复 | #1192 | [PR #1192](https://github.com/moltis-org/moltis/pull/1192) |
| 🟡 中 | ClawHub 技能搜索因元数据请求超时 | ✅ 已修复 | #1196 | [PR #1196](https://github.com/moltis-org/moltis/pull/1196) |
| 🟢 低 | macOS bash 3.2 空数组展开崩溃 | ✅ 已修复 | #1194 | [PR #1194](https://github.com/moltis-org/moltis/pull/1194) |

**稳定性评估**：今日无新增未修复 bug，所有 reported issues 均已有对应 fix PR。项目近期修复集中，稳定性有所提升。

---

## 6. 功能请求与路线图信号

| 功能方向 | 相关 PR | 状态 | 纳入下一版本概率 |
|----------|---------|------|------------------|
| 向量数据库 memory 后端 | #1158 (zvec + redb) | ✅ 已合并 | 已纳入 |
| 持久化连接器（日历/邮件/频道） | #1190 | ✅ 已合并 | 已纳入 |
| Slack 原生 live task cards | #1195 | ✅ 已合并 | 已纳入 |
| Coder 远程工作空间 sandbox | #1199 | 🔄 待合并 | 中高 |
| 命令面板启动 agent 聊天 | #1197 | ✅ 已合并 | 已纳入 |
| OpenAI Responses API 路由 | #1198 | ✅ 已合并 | 已纳入 |
| Vault 恢复短语规范化 | #1186 | 🔄 待合并 | 中 |

**路线图信号**：项目正向**多模态连接器**（Slack、日历、邮件）、**可扩展 memory 架构**（zvec 后端）、**远程 sandbox 支持**（Coder）方向演进。`penso` 贡献者活跃度较高，可能成为后续功能迭代的核心力量。

---

## 7. 用户反馈摘要

| 来源 | 用户痛点/反馈 | 提炼 |
|------|--------------|------|
| #1132 | "main session can't be deleted/archived" | 用户期望所有 session 具备对等的管理权限，main session 不应有特殊保护导致无法清理 |
| #1189 | "Sandbox build failing due to wrong gogcli github URL" | 第三方模块迁移（steipete → openclaw org）导致构建链断裂，用户期待项目能及时跟进上游变更 |
| #1180 / #1179 | 安全维护者主动提出加固 | 用户对安全性有较高期待，社区对潜在漏洞敏感 |
| #1194 | macOS bash 3.2 兼容性问题 | 开发工具链在 macOS 旧版 bash 下存在兼容短板 |

**满意度信号**：安全修复和功能扩展获积极反馈；构建链依赖外部模块的项目存在维护风险。

---

## 8. 待处理积压

| 项目 | 类型 | 创建日期 | 久置原因推测 | 链接 |
|------|------|----------|-------------|------|
| #1186 | PR（vault 恢复短语规范化） | 2026-08-09 | 安全修复待审查 | [PR #1186](https://github.com/moltis-org/moltis/pull/1186) |
| #1199 | PR（Coder remote workspace sandbox） | 2026-08-15 | 新功能待审查 | [PR #1199](https://github.com/moltis-org/moltis/pull/1199) |

**提醒**：PR #1186 涉及密钥派生逻辑，建议优先审查；PR #1199 为 sandbox 扩展功能，有助于生态完善。

---

*报告生成时间：2026-08-16 | 数据来源：GitHub API*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-08-16

---

## 1. 今日速览

CoPaw 在 2026-08-16 保持**高活跃度**。过去 24 小时内共产生 9 条 Issue 更新与 10 条 PR，其中 **1 个 Issue 已关闭**（#6476 Matrix E2E 加密），**所有 PR 仍处于待合并状态**，无新版本发布。今日贡献以 **bug 修复** 和 **用户体验增强** 为主，涉及视频处理、OAuth2、Shell 环境、Cron 任务等核心路径，项目稳定性持续改善。

---

## 2. 版本发布

> 今日无新版本发布。

---

## 3. 项目进展

今日 **0 个 PR 被合并**，所有 10 个 PR 均处于开放状态。整体开发节奏以"修复先行、功能跟进"为主，重点推进方向如下：

| PR | 类型 | 摘要 | 状态 |
|----|------|------|------|
| [#6302](https://github.com/agentscope-ai/QwenPaw/issues/6302) | feat | 统一 provider 发现、模型元数据、路由与 agent 控制，引入目录驱动模型系统 | 待合并 |
| [#6940](https://github.com/agentscope-ai/QwenPaw/issues/6940) | feat | 添加原生 DataPaw 应用运行时和持久化分析工作区 | 待合并 |
| [#7054](https://github.com/agentscope-ai/QwenPaw/issues/7054) | feat | 支持远程 LAN 浏览器 Chrome bridge 端点 | 待合并 |
| [#7001](https://github.com/agentscope-ai/QwenPaw/issues/7001) | feat | Matrix 群聊隔离会话与记忆 | 待合并 |
| [#7050](https://github.com/agentscope-ai/QwenPaw/issues/7050) | feat | Cron Jobs 增加单任务模型选择器 | 待合并 |
| [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061) | fix | 修复 OpenAI Responses API 视频工具结果未进入模型上下文的缺陷 | 待合并 |
| [#6623](https://github.com/agentscope-ai/QwenPaw/issues/6623) | fix | 修复 ACP 通知与 prompt 响应竞争导致文本丢失的 race condition | 待合并 |
| [#7057](https://github.com/agentscope-ai/QwenPaw/issues/7057) | fix | Shell 子进程 PATH 添加用户本地 bin 目录 | 待合并 |
| [#7055](https://github.com/agentscope-ai/QwenPaw/issues/7055) | fix | 修复 agent cron --text 更新静默失败问题 | 待合并 |
| [#7049](https://github.com/agentscope-ai/QwenPaw/issues/7049) | feat | GET /chats/{chat_id} 增加 limit/before 分页 | 待合并 |

> **项目健康度评估：** PR 积压达 10 条，且均为高质量修复与功能增强，合并节奏稍慢，需关注 review 进度。

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issue / PR

1. **[#3915](https://github.com/agentscope-ai/QwenPaw/issues/3915)** — *Console WebUI 虚拟滚动性能问题*
   - 创建：2026-04-28 | 评论：3 | 👍：1
   - **诉求分析：** 长对话场景下 DOM 渲染导致严重卡顿，社区长期呼吁虚拟滚动/分页渲染方案，是当前 WebUI 体验的核心痛点之一。

2. **[#7060](https://github.com/agentscope-ai/QwenPaw/issues/7060) & [#7059](https://github.com/agentscope-ai/QwenPaw/issues/7059)** — *view_video 视频大小限制与 silent failure*
   - 同作者 xiaoka76 在同日提交，且已对应 PR [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061) 修复
   - **诉求分析：** 视频处理链路存在两个缺陷——硬编码 2MB 限制 + 大视频 frames 丢失不报错，影响多模态体验，修复已就绪。

3. **[#6476](https://github.com/agentscope-ai/QwenPaw/issues/6476)** — *Matrix E2E 加密不可用（已关闭）*
   - 评论：3 | 创建：2026-07-26 | 更新：2026-08-15
   - **诉求分析：** olm/vodozemac 依赖安装路径复杂，用户已探索出三步解决方案，issue 可能已通过文档或依赖优化关闭。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | Fix PR |
|--------|-------|------|--------|
| 🟠 高 | [#7059](https://github.com/agentscope-ai/QwenPaw/issues/7059) | `view_video` tool-result 视频 frames 静默丢失，模型收不到任何视频数据 | ✅ [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061) |
| 🟠 高 | [#7060](https://github.com/agentscope-ai/QwenPaw/issues/7060) | view_video 2MB 硬编码限制，provider 配置无效 | ✅ [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061) |
| 🟡 中 | [#7053](https://github.com/agentscope-ai/QwenPaw/issues/7053) | OAuth2 refresh_token 不轮换，远程 MCP 永久降级为手动重新认证 | ❌ 无 |
| 🟡 中 | [#7051](https://github.com/agentscope-ai/QwenPaw/issues/7051) | Console 会话重载后图片附件丢失（data URL 回退为空白） | ❌ 无 |
| 🟡 中 | [#6623](https://github.com/agentscope-ai/QwenPaw/issues/6623) | ACP 通知与 prompt 响应 race condition 导致最终文本丢失 | ✅ 待合并 |
| 🟢 低 | [#7055](https://github.com/agentscope-ai/QwenPaw/issues/7055) | `cron update --text` 对 agent 类型 cron 静默失败 | ✅ 待合并 |

---

## 6. 功能请求与路线图信号

| Issue | 需求摘要 | 与现有 PR 关联 | 纳入下版本可能性 |
|-------|----------|---------------|-----------------|
| [#7052](https://github.com/agentscope-ai/QwenPaw/issues/7052) | 插件 API 增加 system_prompt 权限隔离 | 无直接关联 | 🟡 中等——涉及安全模型设计 |
| [#7056](https://github.com/agentscope-ai/QwenPaw/issues/7056) | 后台任务完成自动回调/通知机制（替代轮询） | 无直接关联 | 🟡 中等——架构变更需评估 |
| [#3915](https://github.com/agentscope-ai/QwenPaw/issues/3915) | Console WebUI 虚拟滚动 | 无直接关联 | 🟢 高——明确的用户体验痛点 |
| [#7058](https://github.com/agentscope-ai/QwenPaw/issues/7058) | 恢复 WebUI 中 context-strategy（native/scroll）选择器 | 无直接关联，后端已支持 | 🟢 高——UI 回归，修复成本低 |
| [#7050](https://github.com/agentscope-ai/QwenPaw/issues/7050) | Cron Jobs 单任务模型覆盖 | ✅ PR [#7050](https://github.com/agentscope-ai/QwenPaw/issues/7050) 已提交 | 🟢 极高——PR 已就绪 |
| [#7049](https://github.com/agentscope-ai/QwenPaw/issues/7049) | 聊天历史分页加载 | ✅ PR [#7049](https://github.com/agentscope-ai/QwenPaw/issues/7049) 已提交 | 🟢 极高——PR 已就绪 |

---

## 7. 用户反馈摘要

- **视频处理能力不足：** xiaoka76 连续提交两个 bug（#7060、#7059），反映多模态视频处理路径未经充分测试，silent failure 用户体验差。
- **会话持久化问题：** #7051 用户反馈图片附件在会话重载后丢失，说明 Console 的 history 渲染对 data URL 处理存在缺陷。
- **工具链环境适配：** #7057 提出 systemd/Docker 环境下 PATH 不完整，影响 `gh`、`cmake` 等常用 CLI 工具的可用性。
- **企业安全诉求：** #7052 来自企业用户，希望插件 system_prompt 独立隔离，避免公司提示词泄露给用户。
- **长对话性能：** #3915 创建时间较长（4 个月），评论数 3、👍 1，反映 WebUI 虚拟滚动是社区长期诉求。
- **原生 context 策略回归：** #7058 指出 v2.1.0 移除了 native/scroll 选择器，用户不满 UI 功能回退。
- **OAuth2 生产环境隐患：** #7053 涉及远程 MCP 服务器的 refresh_token 轮换问题，影响企业级部署稳定性。

---

## 8. 待处理积压

| 类型 | Issue/PR | 创建时间 | 风险说明 |
|------|----------|----------|----------|
| 📌 长期未响应 Issue | [#3915](https://github.com/agentscope-ai/QwenPaw/issues/3915) — 虚拟滚动 | 2026-04-28（近 4 个月） | 核心体验痛点，建议优先处理 |
| 📌 Bug 无 Fix | [#7053](https://github.com/agentscope-ai/QwenPaw/issues/7053) — OAuth2 refresh_token 轮换 | 2026-08-15 | 影响企业部署，需安全修复 |
| 📌 Bug 无 Fix | [#7051](https://github.com/agentscope-ai/QwenPaw/issues/7051) — 图片附件会话重载丢失 | 2026-08-15 | 影响 Console 可用性 |
| 📌 PR 积压 | 全部 10 条 PR 待合并 | 2026-08-01 ~ 2026-08-16 | review 节奏偏慢，建议分批合并 |
| 📌 功能请求无响应 | [#7052](https://github.com/agentscope-ai/QwenPaw/issues/7052) — 插件 system_prompt 权限 | 2026-08-15 | 企业用户诉求，需产品决策 |
| 📌 功能请求无响应 | [#7056](https://github.com/agentscope-ai/QwenPaw/issues/7056) — 后台任务回调机制 | 2026-08-15 | 架构级需求，需评估是否纳入路线图 |

---

**整体评估：** CoPaw 今日处于**修复密集型**开发阶段，社区贡献活跃，多个关键 bug 已提供对应 PR。主要风险在于 **PR 合并节奏偏慢**（10 条积压）及 **2 个重要 bug 暂无修复方案**（#7053、#7051）。建议维护者优先 review [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061)、[#7055](https://github.com/agentscope-ai/QwenPaw/issues/7055)、[#7049](https://github.com/agentscope-ai/QwenPaw/issues/7049)、[#7050](https://github.com/agentscope-ai/QwenPaw/issues/7050) 等已就绪 PR，并推动长期 Issue #3915 的虚拟滚动方案落地。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-08-16

---

## 1. 今日速览

过去24小时，ZeroClaw 共新增/更新 **50条 Issues** 和 **50条 PRs**，项目活跃度保持高位。核心进展集中在**架构 RFC 讨论**（Chat Completions 协议适配、运行时会话所有权、安全态势）与**Anthropic 安全拒绝响应栈的完整实现**（5个 PR 已合并）。今日无新版本发布。整体来看，项目处于 RFC 密集讨论期，同时已有明确方向的 Bug 修复稳步推进。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（6条）

| PR | 作者 | 内容摘要 |
|---|---|---|
| [#9262](https://github.com/zeroclaw-labs/zeroclaw/pull/9262) [CLOSED] | IftekharUddin | feat(providers): 将 Anthropic 服务端安全拒绝识别为 typed `AnthropicRefusalError` |
| [#9263](https://github.com/zeroclaw-labs/zeroclaw/pull/9263) [CLOSED] | IftekharUddin | feat(providers): 客户端 Reliable 层对接 Anthropic 拒绝响应，触发 fallback |
| [#9265](https://github.com/zeroclaw-labs/zeroclaw/pull/9265) [CLOSED] | IftekharUddin | feat(providers): 新增 `server_fallback_models` 配置，支持 Anthropic 服务端 fallback 请求 |
| [#9266](https://github.com/zeroclaw-labs/zeroclaw/pull/9266) [CLOSED] | IftekharUddin | feat(providers): 读取 `model` 与 `AnthropicUsage.iterations` 字段，感知真实 serving 模型 |
| [#9268](https://github.com/zeroclaw-labs/zeroclaw/pull/9268) [CLOSED] | IftekharUddin | feat(channels): 在渠道编排层将 safeguard fallback 提示向用户暴露 |
| [#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527) [CLOSED] | swellee | bug: macOS 桌面应用启动后窗口空白/无窗问题（已验证） |

**进展评估：** Anthropic 拒绝响应栈（`#9262→#9263→#9265→#9266→#9268`）今日完成全套合并，使 ZeroClaw 在安全拒绝场景下具备服务端 fallback 感知、客户端重试路由和频道级用户提示的完整能力链，是本次最重要的功能交付。

---

## 4. 社区热点

### 评论最多的 Issues（Top 5）

| Issue | 标题 | 作者 | 评论数 | 热度分析 |
|---|---|---|---|---|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | RFC: ZeroClaw Chat Completions profile | REL-mame | 21 | 极高 — 社区急需 OpenAI Chat Completions 协议适配，以接入 Open WebUI、LobeChat、Continue.dev、LangChain 等生态 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC: Runtime-owned conversation sessions and transport surface adapters | NiuBlibing | 17 | 高 — 运行时会话所有权与传输适配器边界的重构设计，影响全架构 |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | RFC: Unified attachment architecture for web chat and channels | NiuBlibing | 16 | 高 — 统一附件架构，web 与渠道侧文件/媒体处理 |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) | RFC: Provenance, conversation binding, and reply contract for internally initiated agent turns | mov-xound-glitch | 13 | 高 — 内部触发 Agent 回合的溯源与回复契约，涉及 agent 运行时核心语义 |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) | RFC: Security posture, credential boundaries, and universal ingress policy | Audacity88 | 13 | 高 — 安全态势全局性 RFC，涉及凭证、沙箱、入站信任、redaction 等 |

**热点分析：** 当前社区讨论高度聚焦于**协议层兼容性**（#8603）和**架构边界重构**（#9487/#9488/#6954/#6971），反映出项目正从功能堆叠阶段进入系统级标准化阶段，维护者与社区的协作节奏（多轮 RFC 修订）活跃。

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 标题 | 作者 | 状态 | Fix PR |
|---|---|---|---|---|---|
| P1 | [#9655](https://github.com/zeroclaw-labs/zeroclaw/issues/9655) | Bug: Telegram 审批卡片无位置信息，back-to-back 卡片无法区分 | ZiBibro | OPEN | — |
| P1 | [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) | Task: cron 自定义 shell 测试在并行运行时触发 ETXTBSY，污染无关 PR | AngryPacifist | OPEN | — |
| P2 | [#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527) | Bug: macOS 桌面应用启动后窗口空白/消失 | swellee | **CLOSED** | — |
| P2 | [#7870](https://github.com/zeroclaw-labs/zeroclaw/issues/7870) | Tracker: agent runtime options 从首个 provider 泄漏 | Audacity88 | OPEN | — |

**待修复关注：** Telegram 审批卡片位置问题（#9655）为 P1，影响用户操作流程；cron 测试假阳性（#9965）影响 CI 质量。两者目前无明确 fix PR。

---

## 6. 功能请求与路线图信号

| Issue | 标题 | 作者 | 状态 | 可能纳入版本判断 |
|---|---|---|---|---|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | RFC: Chat Completions profile | REL-mame | OPEN | 高优先级，v0.9+ 有望，讨论已深入（21评论） |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | RFC: Gemini Live 实时语音通道 | metalmon | OPEN | Rev v2 已提交（2026-08-16），进度快 |
| [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) | RFC: Memory 权威存储与可选 enrich 连接器分离 | yanchenko | OPEN | 架构级变更，影响 Lucid/Qdrant 集成 |
| [#9598](https://github.com/zeroclaw-labs/zeroclaw/issues/9598) | RFC: SOP 能力权限契约定义 | Audacity88 | OPEN | Rev 3 已出，目标 v0.9.0 |
| [#9621](https://github.com/zeroclaw-labs/zeroclaw/issues/9621) | RFC: Staged opt-in telemetry with operator-reviewed reports | Audacity88 | OPEN | 运维侧新功能，讨论刚启动 |
| [#8010](https://github.com/zeroclaw-labs/zeroclaw/issues/9810) | RFC: 加载 Agent Plugins 1.0 skill & MCP 包 | NiuBlibing | OPEN | 插件生态兼容，近期 RFC |

---

## 7. 用户反馈摘要

**核心痛点：**
- **OpenAI 协议兼容性**（#8603）：用户大量使用 Open WebUI、LobeChat、Aider、LangChain 等工具，但 ZeroClaw 目前仅通过 WebSocket/ACP/Webhook 暴露能力，缺乏 Chat Completions 协议层适配。
- **macOS 桌面应用稳定性**（#7527）：安装后权限未正确识别、窗口空白/消失，影响桌面端首发体验。
- **Cron 文档缺失与功能限制**（#7762）：无法指定特定模型运行低优先级定时任务，文档站缺失 Cron 相关内容。
- **Telegraf 审批卡片 UX**（#9655）：多工具调用产生多张审批卡片时，卡片位置信息缺失导致用户无法区分。

**正向反馈方向：**
- Anthropic 拒绝响应栈（#9262–#9268）的完整实现获得关注，说明用户对安全拒绝可观测性和 fallback 机制有明确需求。
- 多会话 zerocode pane（#9739）、SOP pane 只读视图（#9694）等 TUI 功能持续推进，反映桌面/CLI 体验是核心关注点。

---

## 8. 待处理积压

| Issue/PR | 标题 | 作者 | 创建时间 | 状态 | 建议关注 |
|---|---|---|---|---|---|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | RFC: Chat Completions profile | REL-mame | 2026-07-02 | OPEN，21评论 | 高 — 社区呼声最强，需 maintainer 推动决策 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC: Runtime-owned conversation sessions | NiuBlibing | 2026-07-28 | OPEN，17评论 | 高 — 架构重构，需维护者决策 |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | RFC: Unified attachment architecture | NiuBlibing | 2026-07-28 | OPEN，16评论 | 高 — 与 #9487 关联，需同步跟进 |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) | RFC: Security posture & credential boundaries | Audacity88 | 2026-05-27 | OPEN，13评论 | 高 — 长期开放，安全核心 |
| [#7870](https://github.com/zeroclaw-labs/zeroclaw/issues/7870) | Tracker: agent runtime options leak | Audacity88 | 2026-06-17 | OPEN | 中 — 已接受但待修复 |
| [#9330](https://github.com/zeroclaw-labs/zeroclaw/issues/9330) | RFC: AI-assisted PR pre-review | NiuBlibing | 2026-07-24 | OPEN，4评论 | 中 — CI 流程改进，需 author action |
| [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) | Task: cron ETXTBSY 测试假阳性 | AngryPacifist | 2026-08-13 | OPEN | 中 — 影响 CI 质量，需优先修复 |

---

**报告生成时间：** 2026-08-16  
**数据来源：** [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw) GitHub 仓库

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*