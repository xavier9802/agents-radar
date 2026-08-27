# OpenClaw 生态日报 2026-08-27

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-27 08:44 UTC

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



# OpenClaw 项目动态日报 — 2026-08-27

---

## 1. 今日速览

过去24小时内，OpenClaw 共处理 **500 条 Issue**（新开/活跃 319，关闭 181）与 **500 条 PR**（待合并 361，已合并/关闭 139），项目保持高活跃度。核心关注点集中在**子代理生命周期管理**、**Gateway 启动与 Session 持久化稳定性**以及**多通道消息投递可靠性**。今日无新版本发布，但多个关键修复 PR 已进入维护者审查阶段，项目整体处于「修复密集型」阶段，稳定性建设为当前主线。

---

## 2. 版本发布

**无新版本发布。** 当前最新 Beta 版本为 `v2026.8.1-beta.3`，相关反馈追踪见 Issue #125626。

---

## 3. 项目进展

今日合并/关闭的重要 PR 集中在以下几个方向：

| PR | 类型 | 说明 |
|---|---|---|
| [#128995](https://github.com/openclaw/openclaw/pull/128995) | 功能 | 将完整 Session 操作（置顶、标记未读、设置图标、复制 Session ID、移入分组）暴露至聊天头部菜单，提升 Control UI 操作效率 |
| [#126424](https://github.com/openclaw/openclaw/pull/126424) | 修复 | 修复多 Agent 场景下对话工具可导致跨 Agent 绑定泄露的问题，强化隔离边界（涉及 Discord/iMessage/Matrix/Slack/Telegram/飞书等全通道） |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | 功能 | 新增安装策略警告审查流程，管理员可在 Control UI 中显式确认并继续存在风险的插件安装 |
| [#123975](https://github.com/openclaw/openclaw/pull/123975) | 修复 | 修复 `tsgo` 包装器在超时或收到信号时遗留僵尸编译器进程树的问题，新增 `OPENCLAW_TSGO_TIMEOUT_MS` 看门狗 |
| [#130744](https://github.com/openclaw/openclaw/pull/130744) | 修复 | 修复 FRV 全量验证流程中终端 Drain artifact 选择逻辑，防止有效非绿色决策 artifact 被错误丢弃 |
| [#128625](https://github.com/openclaw/openclaw/pull/128625) | 修复 | 修复 Control UI Browser 面板在错误信息变更或路由经过节点时显示错误检测可用状态的问题 |
| [#130828](https://github.com/openclaw/openclaw/pull/130828) | 修复 | 修复 Crabbox 扩展在目录加载失败后丢失机器选择的状态问题 |
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | 功能 | 强化安全策略：外部 `security.installPolicy` 命令现可返回 `warn`，强制操作员在 CLI 中显式确认才可继续安装 |
| [#130818](https://github.com/openclaw/openclaw/pull/130818) | 重构 | 清理 MCP 会话管理器中冗余的每运行时超时记账逻辑，统一使用固定的十分钟空闲超时 |
| [#125471](https://github.com/openclaw/openclaw/pull/125471) | 修复 | 修复 Gateway 重启后 Claude CLI OAuth 刷新令牌所有权丢失的兼容性问题 |

**整体判断**：今日合并/关闭的 PR 以**稳定性修复与边界安全加固**为主，无大型新功能落地，项目推进稳健。

---

## 4. 社区热点

### 🔥 评论数 Top Issues

1. **[#125626](https://github.com/openclaw/openclaw/issues/125626)** — *OpenClaw 2026.8.1 beta feedback*（20 条评论）
   社区集中反馈 2026.8.1 beta.3 的稳定性问题，涵盖模型目录、会话生命周期等多个维度，是当前 Beta 验证的核心议题。

2. **[#108435](https://github.com/openclaw/openclaw/issues/108435)** — *Gateway fails to start after update to 2026.7.1*（15 条评论，👍 3，**P0 回归**）
   升级至 2026.7.1 后 Gateway 无法启动（systemd/ollama/手动启动均失败），是近期影响面最广的启动类 Bug，社区讨论热烈。

3. **[#43367](https://github.com/openclaw/openclaw/issues/43367)** — *Multi-agent orchestration is unstable*（14 条评论，**P1**）
   并发 Agent 场景下配置覆盖、Session 锁冲突与子任务脱节问题长期存在，用户反映多 Agent 批量编排在实际生产中不可靠。

4. **[#38327](https://github.com/openclaw/openclaw/issues/38327)** — *google-vertex/gemini-3.1-pro-preview 报 "Cannot convert undefined or null to object"*（14 条评论，👍 3，**P1 回归**）
   2026.3.2 引入的嵌入 Agent 崩溃回归，影响 Google Vertex 路径用户。

5. **[#53628](https://github.com/openclaw/openclaw/issues/53628)** — *XDG_CONFIG_HOME 在 skill 安装时未被解析*（14 条评论）
   Docker 部署用户痛点，技能安装路径错误导致配置丢失。

### 🔥 高价值 Feature Request

- **[#26037](https://github.com/openclaw/openclaw/issues/26037)** — *阿里云百炼 Coding Plan 支持（含 thinking/reasoning）*（5 条评论，👍 4）
  中国用户呼声较高，当前官方集成方式不支持 reasoning 模式，用户期望原生支持。

---

## 5. Bug 与稳定性

| 严重级别 | Issue | 简述 | Fix PR |
|---|---|---|---|
| 🔴 P0 | [#108435](https://github.com/openclaw/openclaw/issues/108435) | 2026.7.1 升级后 Gateway 完全无法启动（systemd/ollama/手动均失败） | 暂无 |
| 🔴 P1 | [#118839](https://github.com/openclaw/openclaw/issues/118839) | 2026.7.2-beta.7 重现 "restart recovery claim changed before agent adoption" 回归 | 暂无 |
| 🔴 P1 | [#128971](https://github.com/openclaw/openclaw/issues/128971) | Telegram 终端回复在 `delivery_ambiguous` 时静默丢失 | 暂无 |
| 🟠 P1 | [#112259](https://github.com/openclaw/openclaw/issues/112259) | 可见入站 Channel 消息零 payload 派发，无重试/死信/用户可见失败 | 暂无 |
| 🟠 P1 | [#118018](https://github.com/openclaw/openclaw/issues/118018) | 过期子代理完成通知被投递至已被替换的请求方生命周期 | 暂无 |
| 🟠 P1 | [#80498](https://github.com/openclaw/openclaw/issues/80498) | 子代理完成通知在 tool-use 轮次后提前或重复 | 暂无 |
| 🟠 P1 | [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/Tool 子进程泄漏导致僵尸进程累积，运行时退化 | 暂无 |
| 🟠 P1 | [#114234](https://github.com/openclaw/openclaw/issues/114234) | 容器环境下 Usage-cost 刷新锁因 PID 重用无法释放，永久冻结缓存 | 暂无 |
| 🟠 P1 | [#113093](https://github.com/openclaw

---

## 横向生态对比



# 2026-08-27 个人 AI 助手/自主智能体开源生态横向对比分析报告

---

## 1. 生态全景

2026 年 8 月下旬，个人 AI 助手开源生态呈现**分层演化**态势：以 OpenClaw、CoPaw、ZeroClaw 为首的大型项目进入**稳定性与安全性加固期**，通过密集的 PR 合并修复多代理编排、会话持久化、渠道可靠性等核心痛点；以 NanoBot、IronClaw、LobsterAI 为代表的中坚力量正从"功能堆叠"转向**体验打磨与架构治理**双轨并行；部分边缘项目（NullClaw、ZeptoClaw）活跃度明显下滑，生态集中度进一步提升。整体技术路线向**多通道路由、会话生命周期管理、沙箱安全、多租户协作**四大方向收敛。

---

## 2. 各项目活跃度对比

| 项目 | Issues (新开/活跃) | Issues (已关闭) | PR (待合并) | PR (已合并/关闭) | 版本发布 | 健康度评估 |
|---|---|---|---|---|---|---|
| **OpenClaw** | 319 | 181 | 361 | 139 | 无（v2026.8.1-beta.3） | 🟢 高 — 修复密集型，稳定性建设为主线 |
| **CoPaw** | ~26 | — | ~15 | ~24 | ✅ v2.2.0-beta.1 | 🟢 高 — 多租户 Hub 演进加速 |
| **ZeroClaw** | 27 | ~10 | 44 | ~30 | 无 | 🟢 高 — v0.9.0 安全冲刺期 |
| **NanoBot** | 1 | 1 | 17 | 16 | 无 | 🟢 高 — 架构解耦+体验优化 |
| **NanoClaw** | 2 | 1 | 18 | 5 | 无 | 🟢 高 — 底层工程硬化 |
| **IronClaw** | 26 | 47 | 3 | 47 | ✅ v1.4.0-rc.1 | 🟢 高 — 性能优化+Reborn 栈成熟 |
| **LobsterAI** | 1 | 0 | 1 | 10 | 无 | 🟡 中高 — 功能闭环+体验打磨 |
| **PicoClaw** | 5 | 2 | 2 | 4 | 无（0.3.x） | 🟡 中等 — 渠道兼容性维护 |
| **Moltis** | 0 | 1 | 0 | 2 | ✅ 20260826.01 | 🟡 中等 — 稳定性增强，节奏稳健 |
| **NullClaw** | 1 | 0 | 0 | 0 | 无 | 🔴 低 — 平稳期，无实质推进 |
| **ZeptoClaw** | — | — | — | — | 无 | 🔴 停滞 — 24h 无活动 |

---

## 3. OpenClaw 在生态中的定位

**规模与定位**：OpenClaw 以 500 Issues + 500 PR 的绝对体量领先，是生态中**规模最大的多通道 Agent 编排框架**，定位企业级/个人级通用 AI 助手。

**与同类对比**：

| 维度 | OpenClaw | 同类项目 |
|---|---|---|
| **通道覆盖** | Discord/iMessage/Matrix/Slack/Telegram/飞书全通道 | PicoClaw 侧重 Telegram/Slack/LINE；NanoBot 以 TUI/WebUI 为主 |
| **多代理编排** | 深度建设（子代理生命周期、跨代理绑定隔离） | CoPaw 起步多租户；ZeroClaw 关注会话级持久化 |
| **技术路线** | Gateway 中心化 + Session 持久化 + Control UI | NanoBot 轻量级 Agent 循环；IronClaw Reborn 栈架构 |
| **社区规模** | Issue 日处理 500+ 量级，Beta 反馈闭环活跃 | CoPaw 日 65 条；ZeroClaw 日 ~70 条；其余 <20 条 |

**核心优势**：通道生态最全、多代理编排能力最强、企业级安全策略（installPolicy warn/confirm）最完善。主要短板在于 P0 级 Gateway 启动回归（#108435）尚未修复，影响生产信任。

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 |
|---|---|---|
| **会话生命周期与持久化** | OpenClaw、ZeroClaw、CoPaw | OpenClaw：Gateway 重启后 OAuth 刷新令牌丢失（#125471）；ZeroClaw：陈旧 provider 刷新污染替换会话（#9748）；CoPaw：跨会话记忆搜索错乱（#7193） |
| **多代理/多租户编排** | OpenClaw、CoPaw、ZeroClaw | OpenClaw：并发 Agent 配置覆盖与 Session 锁冲突（#43367）；CoPaw：多租户 Hub 版功能规划（#7318）；ZeroClaw：活跃 turn 期间并行消息冲突（#10408） |
| **渠道可靠性与消息投递** | OpenClaw、NanoClaw、ZeroClaw、PicoClaw | OpenClaw：Telegram 静默丢失（#128971）、零 payload 派发（#112259）；NanoClaw：Telegram MarkdownV2 丢失（#3569）；PicoClaw：路由会话继承失效（#3316） |
| **安全与沙箱加固** | ZeroClaw、NanoClaw、OpenClaw | ZeroClaw：temp 文件权限 0o600（#10409）、路径注入（#10381）；NanoClaw：session 路径穿越（#5564）；OpenClaw：installPolicy warn/confirm 强制确认（#116489） |
| **可观测性与缓存优化** | CoPaw、ZeroClaw、NanoBot | CoPaw：提示词缓存命中率可观测（#7335）；ZeroClaw：记忆生命周期与存储解耦（#6850）；NanoBot：工具执行进度流式上报（#5562） |
| **多模型/推理能力** | NanoBot、LobsterAI、Moltis | NanoBot：模型重试状态展示（#5504）；LobsterAI：Synthorai 内置服务商（#2554）；Moltis：模型偏好替换/清空（#1104） |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|---|---|---|---|
| **OpenClaw** | 全通道路由 + 多代理编排 + 企业安全策略 | 企业/高级个人用户，多通道集成需求 | Gateway 中心化架构，Session 持久化合约，Control UI 完整 |
| **CoPaw** | 多租户 Hub 版 + 控制台 UX + 缓存可观测 | 团队协作、企业内网部署 | 中国生态深耕（DashScope/微信），提示词缓存优化 |
| **ZeroClaw** | 安全加固 + 会话持久化 + 实时语音/Computer-use | 安全敏感场景、Rust 技术栈偏好者 | Rust 原生、RFC 治理机制成熟、WASM 插件扩展 |
| **NanoBot** | 轻量 Agent 循环 + TUI/WebUI 体验 + 多模态输入 | 个人开发者、CLI 偏好者 | Python/TS 混合，AgentLoop 解耦重构，SHA-256 缓存优化 |
| **IronClaw** | 持久化通知收件箱 + Reborn 栈 + 性能优化 | 生产环境部署者 | v1.4 RC 阶段，Legacy 单体退役，Railway/GCP/Docker 多部署 |
| **NanoClaw** | 渠道稳定性 + 网关安全策略 + 容器环境硬化 | 生产环境运维者 | OneCLI 网关 MCP 策略执行，启动器边缘故障收敛 |
| **LobsterAI** | 埋点分析 + 云端文件管理 + 内置服务商 | 中国个人用户，数据分析需求 | 网易有道生态，部署/分享链路完善 |
| **PicoClaw** | 渠道协议适配（Telegram/Slack/LINE/IRC） | 多渠道轻量集成用户 | 0.3.x 稳定维护，路由上下文管理 |
| **Moltis** | 模型偏好管理 + MCP OAuth 标准化 | 多模型用户、MCP 生态用户 | Rust，RFC 7591 动态客户端注册，Protected-resource scopes |
| **NullClaw** | 技能管理（symlink 支持） | 技能复用需求用户 | 低活跃度，功能扩展停滞 |
| **ZeptoClaw** | — | — | 停滞，无活动 |

---

## 6. 社区热度与成熟度

### 🚀 快速迭代阶段
- **CoPaw**：日处理 65 条活动，v2.2.0-beta.1 发布，多租户 Hub 功能规划启动，测试覆盖冲刺（495 用例）
- **ZeroClaw**：日处理 ~70 条活动，v0.9.0 安全冲刺，RFC 治理机制成熟（11 个活跃 RFC）
- **NanoBot**：日处理 35 条活动，Agent 循环重构 + 体验打磨双轨并行

### 🏗️ 质量巩固阶段
- **OpenClaw**：日处理 1000 条活动（体量大），但无版本发布，PR 以修复为主，P0 Gateway 回归待解
- **IronClaw**：v1.4.0-rc.1 发布，Legacy 单体退役，性能瓶颈（19s/轮）攻关中
- **NanoClaw**：日处理 26 条活动，底层工程硬化，启动器/容器边缘故障收敛

### 📊 稳定维护阶段
- **LobsterAI**：日处理 12 条活动，功能闭环完成，体验打磨为主
- **PicoClaw**：日处理 13 条活动，渠道兼容性维护
- **Moltis**：日处理 3 条活动，版本发布节奏稳健

### ⚠️ 低活跃/停滞
- **NullClaw**：日 1 Issue，无 PR
- **ZeptoClaw**：24h 无活动

---

## 7. 值得关注的趋势信号

| 趋势 | 证据 | 对开发者的参考价值 |
|---|---|---|
| **从"功能堆叠"到"架构治理"** | NanoBot AgentLoop 重构、ZeroClaw RFC 队列、OpenClaw 修复密集型 | 早期项目需尽早建立贡献规范与审查机制，避免技术债累积 |
| **多租户/团队协作成为新战场** | CoPaw #7318 Hub 规划、OpenClaw 跨代理隔离、ZeroClaw 会话级权限 | 个人助手向团队场景演进是确定性趋势，权限模型与上下文隔离是关键壁垒 |
| **安全加固进入深水区** | ZeroClaw temp 文件权限/路径注入、NanoClaw 邮箱注入、OpenClaw installPolicy | 生产级 Agent 必须内置安全策略执行层，路径校验/沙箱/策略确认是不可绕过的基建 |
| **渠道可靠性成为差异化竞争力** | 多个项目集中修复 Telegram/NanoClaw MarkdownV2 静默丢失、OpenClaw 消息派发失败 | 渠道适配不能仅关注"能通"，需处理边缘场景（消息截断/重试/死信），这是企业级部署的分水岭 |
| **可观测性从"可选"变"必选"** | CoPaw 缓存命中率、NanoBot 工具进度流式上报、LobsterAI 埋点链路 | Agent 内部状态（重试/进度/成本）的可视化是用户体验的关键，黑盒 Agent 将被市场淘汰 |
| **中国生态本土化加速** | CoPaw DashScope 兼容、LobsterAI Synthorai 内置、OpenClaw 飞书通道 | 国内用户需关注本土服务商集成深度，建议优先选择已原生支持 reasoning 模式的项目 |
| **RFC 治理机制兴起** | ZeroClaw 11 个活跃 RFC、维护者决策队列（#8692） | 大型开源项目需建立设计决策透明度机制，降低社区摩擦，提升贡献者体验 |

---

**报告生成时间**：2026-08-27  
**数据来源**：各项目 GitHub API 动态摘要

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目日报 — 2026-08-27

---

## 1. 今日速览

NanoBot 项目今日保持高频开发节奏，24小时内产生 **33 条 PR**（合并 16 条，待合并 17 条）和 **2 条 Issue**（1 开 1 闭），开发者活跃度处于高位。主要推进方向集中在三大领域：**安全性加固**（路径穿越修复）、**TUI/WebUI 体验提升**（模型重试状态、图片粘贴、自动补全）以及 **Agent 核心循环重构**（解耦消息工具状态、统一进度流）。无新版本发布，但今日合并的 PR 质量较高，覆盖了从底层性能到交互层的多处改进，整体健康度良好。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 今日合并的重要 PR（16 条）

| PR | 类型 | 作者 | 说明 |
|---|---|---|---|
| [#5556](https://github.com/HKUDS/nanobot/pull/5556) | Bug Fix | chengyongru | 补全原生推理生命周期，在回答生成前关闭 reasoning 模式，修复推理状态与回答内容竞态问题 |
| [#5558](https://github.com/HKUDS/nanobot/pull/5558) | Refactor | chengyongru | 将 MyTool 通过 ToolLoader 加载，移除 AgentLoop 中的手动注册分支，提升可扩展性 |
| [#5557](https://github.com/HKUDS/nanobot/pull/5557) | Perf | chengyongru | 通过 SHA-256 缓存 TUI 依赖安装状态，避免重复执行 `bun install` |
| [#5543](https://github.com/HKUDS/nanobot/pull/5543) | Bug Fix | chengyongru | 修复 TUI 连接故障时无反馈的问题，复用 `/health` 端点区分不同故障阶段 |
| [#5491](https://github.com/HKUDS/nanobot/pull/5491) | Bug Fix | chengyongru | 修复 WebUI 回答文本被推理外壳吞没的问题，确保多轮工具调用后回答内容正确合并 |
| [#5481](https://github.com/HKUDS/nanobot/pull/5481) | Feature | chengyongru | 新增统一 Provider 用量后端，为每次重试生成独立用量记录 |
| [#5534](https://github.com/HKUDS/nanobot/pull/5534) | Feature | chengyongru | TUI 支持 `$skill-name` 自动补全，含箭头导航和 Tab 插入 |
| [#5533](https://github.com/HKUDS/nanobot/pull/5533) | Perf | chengyongru | 用 `os.scandir` 替代 `pathlib` 元数据调用，修复 `find_files` 大目录扫描卡顿 |
| [#5538](https://github.com/HKUDS/nanobot/pull/5538) | Refactor | chengyongru | 简化 TUI composer 提示文案，`Enter` 立即发送 / `Tab` 提交下次响应 |
| [#5546](https://github.com/HKUDS/nanobot/pull/5546) | Refactor | chengyongru | 移除 `AgentLoop._last_usage` 全局副作用，改为 per-run hook 捕获用量 |
| [#5548](https://github.com/HKUDS/nanobot/pull/5548) | Refactor | chengyongru | 隔离 WebUI WebSocket 编排，事件路由统一收敛到 `WebUIOutboundProjector` |
| [#5555](https://github.com/HKUDS/nanobot/pull/5555) | Refactor | chengyongru | 移除重复的 AgentRunSpec.progress_callback，合并推理/工具/流式事件路径 |
| [#5519](https://github.com/HKUDS/nanobot/pull/5519) | Bug Fix | Re-bin | 收紧单面板聊天头部间距，优化文件编辑时间线排序 |
| [#5560](https://github.com/HKUDS/nanobot/pull/5560) | Feature | Re-bin | 使裸 `nanobot` 命令默认启动原生终端 Agent，提升 CLI 易用性 |

> **整体判断：** 今日合并的 PR 覆盖了"体验修补缺口 + 架构解耦 + 性能优化"三个层面，项目从纯功能驱动向 **可维护性优先** 过渡趋势明显，尤其是 chengyongru 主导的 Agent 循环重构（#5558/#5546/#5548/#5555）为后续大规模演进打下基础。

---

## 4. 社区热点

### 🔥 高关注度 PR / Issue

**PR #5504 — 模型重试状态展示**（[链接](https://github.com/HKUDS/nanobot/pull/5504)）
- 修复 WebUI/TUI 中模型重试时用户无感知的 UX 问题，引入重试倒计时和候选替换提示
- 用户痛点：模型故障时界面长时间无响应，用户不知道是重试中还是卡死

**PR #5563 — TUI 粘贴剪贴板图片**（[链接](https://github.com/HKUDS/nanobot/pull/5563)）
- 新增 `Ctrl+V` / `Alt+V` 支持，保留图片字节并通过 WebSocket 媒体通道传输
- 直接回应用户对多模态输入的期望，与 #5562（工具进度流式上报）形成互补

**PR #5562 — OpenAI 兼容端点流式工具进度事件**（[链接](https://github.com/HKUDS/nanobot/pull/5562)）
- 修复 Issue #3698，使外部客户端可观测工具执行生命周期
- 对集成第三方工具链的用户影响较大，解决"黑盒 Agent"问题

**PR #5234 — MST 元搜索 Provider 集成**（[链接](https://github.com/HKUDS/nanobot/pull/5234)）
- 自 8 月 3 日创建，已开放等待合并，采用 RRF 融合多搜索引擎结果
- 长期未合并非因为质量低，可能是 review 周期较长，建议维护者优先处理

**Issue #5550 — read_session 通配符查询返回空历史**（[链接](https://github.com/HKUDS/nanobot/issue/5550)）
- 用户通过 `@session` 引用对话时，模型使用 `"*"` 等通配符查询，但工具未正确处理
- 已关闭，推测已由某个 PR 修复

---

## 5. Bug 与稳定性

| 优先级 | 问题 | 状态 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#5564](https://github.com/HKUDS/nanobot/issues/5564) session 文件路径穿越漏洞，session_id 未校验 | **Open** | 无 |
| 🟠 中 | [#5550](https://github.com/HKUDS/nanobot/issues/5550) read_session 通配符查询返回空 | **Closed** | 已修复 |
| 🟠 中 | TUI 连接失败无反馈（#5543 已合） | Closed | ✅ #5543 |
| 🟡 低 | WebUI 推理外壳吞没回答文本（#5491 已合） | Closed | ✅ #5491 |
| 🟡 低 | 单面板头部间距过大（#5519 已合） | Closed | ✅ #5519 |

> ⚠️ **今日需关注：** #5564 为安全类问题（路径穿越），涉及 session 文件处理，建议使用方在 #5564 合入前避免接受外部传入的 session_id。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 预测 |
|---|---|---|
| TUI 粘贴图片输入 | PR #5563 | 极可能纳入下一版本，已合入候选状态 |
| 工具执行进度流式上报 | PR #5562 | 极可能纳入，补全 OpenAI 兼容端点的能力缺口 |
| 每个 Spawn 独立模型预设 | PR #5561 | 可能纳入，作为 #4291 的替代实现 |
| MST 元搜索 Provider | PR #5234 | 待定，长期开放，需 review |
| `nanobot` 裸命令启动 Agent | PR #5560 | 已合入，预计下个版本生效 |
| TUI Skill 引用自动补全 | PR #5534 | 已合入，生态友好性增强 |

> **路线图信号：** 项目正从"功能堆叠"转向"体验打磨 + 架构治理"双轨并行。 Agent 循环重构（#5558/#5546/#5555/#5548）为多 Agent Spawn、插件化 Provider 扫清障碍，预示后续版本可能支持更复杂的编排场景。

---

## 7. 用户反馈摘要

- **痛点 1：模型重试无感知。** 用户在使用多模型候选（retry）功能时，遇到界面长时间无响应但实际在重试的情况，希望获得实时状态反馈 → #5504 已修复。
- **痛点 2：大目录扫描卡顿。** `find_files` 在大型工作区中明显延迟，影响 Agent 工具调用效率 → #5533 已修复。
- **痛点 3：通配符查询行为异常。** 用户通过 `@session *` 引用对话时返回空，期望能查询全部消息 → #5550 已关闭。
- **满意度：** TUI Skill 自动补全（#5534）和 `Ctrl+V` 图片粘贴（#5563）回应了高频使用场景；裸 `nanobot` 命令（#5560）简化了日常使用路径。
- **未满足期待：** MST 元搜索 Provider（#5234）自 8 月 3 日提交至今仍未合入，社区对多搜索引擎聚合能力有明确需求。

---

## 8. 待处理积压

| 项目 | 类型 | 创建时间 | 建议优先级 |
|---|---|---|---|
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) MST 元搜索 Provider | PR | 2026-08-03 | 🔴 高 — 功能价值明确，积压超 2 周 |
| [#5561](https://github.com/HKUDS/nanobot/pull/5561) 每 Spawn 模型预设 | PR | 2026-08-27 | 🟠 中 — 同主题 #4291 已有讨论，需尽快 decision |
| [#5564](https://github.com/HKUDS/nanobot/issues/5564) 路径穿越漏洞 | Issue | 2026-08-27 | 🔴 紧急 — 安全修复，应优先合入 |
| [#5504](https://github.com/HKUDS/nanobot/pull/5504) 模型重试状态展示 | PR | 2026-08-24 | 🟡 低 — 已在队列中，预计近期可合入 |

---

**报告生成时间：** 2026-08-27 · 数据来源：GitHub API

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报（2026-08-27）

## 1. 今日速览
过去24小时 PicoClaw 保持中等活跃度，共响应 7 条 Issue（新开/活跃 5 条，已关闭 2 条）与 6 条 PR（待合并 2 条，已合并/关闭 4 条），无新版本发布。维护者与社区聚焦于多通道路由上下文管理、Slack/LINE 渠道集成修复及 Web UI 性能瓶颈。项目整体处于稳定维护期，代码健壮性与渠道兼容性持续得到补充，健康度良好。

## 2. 版本发布
无新版本发布。当前代码库仍基于 `0.3.x` 系列迭代，本次更新以 Bug 修复与配置清理为主，未引入破坏性变更或版本跳跃。

## 3. 项目进展
今日共合并 4 个 PR，重点推进了路由代理稳定性与渠道协议适配：
- [#3316](https://github.com/sipeed/picoclaw/pull/3316) 修复了通过分发规则路由的 Agent 无法继承历史消息、自动压缩与 Seahorse 引导失效的问题，补齐了多智能体路由的核心缺陷。
- [#3315](https://github.com/sipeed/picoclaw/pull/3315) 修正了 Telegram 私聊机器人仅依赖 `IsForum` 判断主题的逻辑，现可正确识别 `IsTopicMessage` 字段。
- [#3314](https://github.com/sipeed/picoclaw/pull/3314) 修复了 `customAllowPatterns` 被默认拒绝规则优先覆盖的 Bug，Shell 命令白名单现在按预期生效。
- [#1549](https://github.com/sipeed/picoclaw/pull/1549) 于今日完成批量合入（#1448/#1447/#1446/#1444），历史修复已并入主干。
另有 2 个 PR 待审核合并：[#3340](https://github.com/sipeed/picoclaw/pull/3340)（Slack 图片上传 `FileSize` 缺失修复）、[#3329](https://github.com/sipeed/picoclaw/pull/3329)（LINE 无效配置项警告）。

## 4. 社区热点
- [#3287](https://github.com/sipeed/picoclaw/issues/3287) **IRC 长消息重组需求**（8 评论）：IRCv3 默认 512 字节限制会导致长消息被客户端拆分，用户希望 PicoClaw 能将其重组为单条连贯输入。该 Issue 评论活跃，反映社区对协议原生适配的诉求。
- [#3281](https://github.com/sipeed/picoclaw/issues/3281) **Web UI 长历史输入卡顿**（7 评论, 1 👍）：会话历史积累后输入框响应显著延迟，暴露前端状态同步或渲染性能瓶颈，是当日讨论热度最高的体验类 Issue。
- [#3301](https://github.com/sipeed/picoclaw/issues/3301) **路由会话清理/

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：** 2026-08-27  
**数据周期：** 过去 24 小时  
**仓库：** nanocoai/nanoclaw

---

## 1. 今日速览
今日 NanoClaw 保持高开发节奏，24 小时内共产生 **23 条 PR**（18 条待评审、5 条已合并/关闭），Issue 更新 **3 条**（2 开放、1 已关闭）。项目本期无新版本发布，但核心维护者与贡献者正集中推进基础设施稳定性、渠道容错与安全配置硬化。整体活跃度与健康度处于高位，工程纪律良好（多数 PR 严格遵循贡献规范与 `core-team` 审核标准）。

---

## 2. 版本发布
无新版本发布。

---

## 3. 项目进展
今日已关闭/合并的 5 条 PR 主要推进了**渠道稳定性**与**网关安全策略**：
- **#3557 & #3556**（`glifocat`）：修复 Mattermost 渠道的初始安装与 SiteURL 处理逻辑，并解决服务重启后交互式卡片线程缓存丢失导致的点击失效问题。
- **#3551 & #3552**（`wildcard`）：强化 OneCLI 网关后的 MCP 策略执行，防止 Codex/OpenCode 等远程模型绕过组级安全限制，提升企业/团队部署的合规性。
- **#3550 & #3549**（`aniruddhaadak80`）：修复邮箱验证正则允许 Shell 元字符注入的风险，并改用 `INSERT OR IGNORE` 消除消息重试时的无限崩溃循环。

项目整体正从“功能快速迭代”转向“底层工程硬化”，技术债收敛速度明显加快。

---

## 4. 社区热点
- **[Issue #3569](https://github.com/nanocoai/nanoclaw/issues/3569)**：Telegram 渠道因 `@chat-adapter/telegram` 锁定在 `4.29.0`，导致包含奇数个未转义 MarkdownV2 标记的消息被永久静默丢弃。上游已于 `4.32.0` 修复，社区对该版本锁定带来的生产阻断表达强烈关注。
- **[Issue #3568](https://github.com/nanocoai/nanoclaw/issues/3568)**：`system` 类型消息积压触发入站队列饥饿，代理在无任何报错的情况下彻底停止响应。该缺陷隐蔽性强，已引起多位生产环境用户的重视。
- **[PR #3567–#3555 系列](https://github.com/nanocoai/nanoclaw/pulls?q=is%3Apr+created%3A2026-08-26)**：`Agi-Asi` 单日连续提交 13 项修复，覆盖 PATH 污染、`launchd` 静默无操作、`apt` 挂起、Node 基线提升、Claude SDK token 上限等底层场景，显示维护者正系统性收敛启动器与容器环境的边缘故障。

---

## 5. Bug 与稳定性
按严重程度排列：
| 级别 | 类型 | 描述 | 状态 / 关联 PR |
|------|------|------|----------------|
| 🔴 严重 | Issue | #3568：`system` 行积压导致队列饥饿，代理静默假死 | 暂无关联 PR，需紧急排查调度器 |
| 🔴 严重 | Issue | #3569：Telegram 消息因 MarkdownV2 奇偶校验错误静默丢失 | 上游 `4.32.0` 已修复，待升级 adapter 锁定版本 |
| 🟡 中等 | PR | #3550：邮箱正则允许 `;`、`` ` ``、`$()` 注入 | ✅ 已修复 |
| 🟡 中等 | PR | #3549：`mailbox` 重试未使用 `INSERT

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 — 2026-08-27

---

## 1. 今日速览

NullClaw 今日整体活跃度偏低，过去 24 小时内仅收到 **1 条新增 Issue**，无 PR 更新或版本发布。新增 Issue #995 为功能增强请求，聚焦于技能（Skills）符号链接支持，反映用户对项目模块化管理和同步便利性的持续需求。项目当前处于平稳期，维护者和社区暂无紧急修复或新功能推进。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

过去 24 小时内**无 PR 合并或关闭记录**，项目未出现实质性的代码推进。整体开发节奏趋于平缓，暂无明确的功能迭代信号。

---

## 4. 社区热点

**Issue #995 — Support Skills Symlinks**
- **状态**: OPEN | **类型**: enhancement
- **作者**: ivostoykov
- **创建时间**: 2026-08-26
- **评论数**: 0 | **👍**: 0
- **链接**: [nullclaw/nullclaw Issue #995](https://github.com/nullclaw/nullclaw/issues/995)

**分析**：该 Issue 虽暂无评论互动，但诉求清晰——当前 `nullclaw skills link` 命令忽略符号链接，导致用户在使用共享技能或跨环境同步时面临不便。用户痛点在于"同步复杂性"和"过时技能可行性"，暗示项目中存在多环境部署或团队协作场景。若维护者响应，可考虑从路径解析层面纳入 symlink 支持。

---

## 5. Bug 与稳定性

今日无 Bug 报告、崩溃或回归问题。

---

## 6. 功能请求与路线图信号

**Issue #995** 提出的 Skills Symlink 支持属于**可用性增强类功能**，若纳入路线图，可能出现在以下方向：
- 技能管理模块的命令增强（`nullclaw skills link --symlink` 或自动识别）
- 技能存储路径解析逻辑优化

目前尚无对应 PR，暂无法判断优先级。建议关注该 Issue 后续评论或作者是否有 PR 跟进。

---

## 7. 用户反馈摘要

从 Issue #995 中提炼用户反馈如下：

| 维度 | 内容 |
|------|------|
| **痛点** | 当前版本不支持技能符号链接，`nullclaw skills link` 会忽略 symlink |
| **使用场景** | 多环境同步、避免技能副本冗余、减少维护负担 |
| **期望** | 自动识别并正确处理符号链接，提升技能管理的灵活性和可行性 |
| **情绪** | 建设性反馈，态度积极，未表现出强烈不满 |

---

## 8. 待处理积压

今日新增 Issue 即为此前未覆盖的功能缺口，无长期未响应的重要积压项。建议维护者关注 **Issue #995** 的后续动态，评估是否需要主动回应或引导贡献者提交 PR。

---

**项目健康度评估**：今日活跃度较低，无紧急问题，社区反馈聚焦于功能增强而非稳定性。项目整体状态**平稳**，建议维护者保持对技能管理相关 Issue 的关注。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期**: 2026-08-27  
**数据来源**: GitHub `nearai/ironclaw`  

---

## 1. 今日速览
过去 24 小时 IronClaw 保持高频交付节奏，共处理 46 条 Issue 与 50 条 PR（26 条活跃/新建，47 条已合并/关闭，3 条待合并）。项目正式推出 `v1.4.0-rc.1` 候选版本，核心聚焦持久化通知收件箱与 Reborn 栈架构硬化。社区讨论重心已从功能开发转向性能成本优化（单轮推理 19s 瓶颈）与上下文管理基建。整体健康度良好，安全补丁、可观测性框架与 MCP 生态同步推进，具备向 stable 版本演进的基础。

---

## 2. 版本发布
**`ironclaw-v1.4.0-rc.1`** (2026-08-26)  
- **覆盖范围**: 自 `v1.3.0` 以来的 81 个 commits，为 1.4.0 首个 Release Candidate。
- **核心新增**: Durable notification inbox（持久化通知收件箱），将权威结果与可操作网关推送至 per-user inbox，并由 WebUI 通知中心统一 surfaced，改善审批与 Auth 流程体验。
- **迁移/兼容性提示**: 
  - v1 遗留单体 (`src/`) 已正式退役，所有生产部署需确保已切换至 Reborn 栈（Railway/GCP/Docker CI 配置已更新）。
  - RC 阶段建议优先在 staging 环境验证 MCP 注册框架与 TOCTOU 修复对现有扩展的兼容性。

---

## 3. 项目进展
今日

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 — 2026-08-27

---

## 1. 今日速览

LobsterAI 今日保持中高强度开发节奏，24小时内共处理 **12 条** 活动（1 Issue + 11 PR），其中 10 条 PR 已合并/关闭，1 条待合并，整体交付效率较高。核心进展集中在**埋点分析链路完善**、**云端文件管理功能扩展**及**UI/UX 细节打磨**三个方向，无新版本发布，无已知严重 Bug 上报。项目健康度良好，贡献者活跃，合并速度快，维护响应及时。

---

## 2. 版本发布

无新版本发布。

> 注：PR [#2549](https://github.com/netease-youdao/LobsterAI/pull/2549) 为 Release/2026.8.26 构建流程，非对外发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（10 条）

| PR | 类型 | 概要 |
|---|---|---|
| [#2555](https://github.com/netease-youdao/LobsterAI/pull/2555) | feat | 完善发布与部署分析链路，新增分享/部署/复制链接等事件埋点，增加异步部署终态跟踪与可靠上报队列 |
| [#2550](https://github.com/netease-youdao/LobsterAI/pull/2550) | feat | 支持永久删除云端分享文件，仅允许删除已停止的分享并通过文件名二次确认，同步更新云端列表与本地收藏 |
| [#2558](https://github.com/netease-youdao/LobsterAI/pull/2558) | feat | 侧边栏登录 CTA 按钮新增彩虹动画效果，区分明暗主题对比度，并补充登录尝试日志 |
| [#2553](https://github.com/netease-youdao/LobsterAI/pull/2553) | fix | 修复智谱（Zhipu）图标在暗黑模式下的显示问题 |
| [#2548](https://github.com/netease-youdao/LobsterAI/pull/2548) | chore | 调整设置页宽度，优化布局体验 |
| [#2547](https://github.com/netease-youdao/LobsterAI/pull/2547) | fix | 修复登录引导流程相关问题 |
| [#2552](https://github.com/netease-youdao/LobsterAI/pull/2552) | feat | 充值引导优化（recharge guide） |
| [#2557](https://github.com/netease-youdao/LobsterAI/pull/2557) | fix | 2026.8.24 系列问题修复 |
| [#2556](https://github.com/netease-youdao/LobsterAI/pull/2556) | chore | 26.8.24 rlog 相关更新 |

**整体判断：** 项目在本日完成了分析数据链路的关键补齐（#2555），并扩展了云分享文件的完整生命周期管理（#2550），功能闭环程度显著提升。

### 待合并 PR

- [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) — **fix: app update preserve ready state**（作者: fisherdaddy），修复应用更新时 ready 状态丢失问题，待合并。

---

## 4. 社区热点

### Issue #2554 — 新增 Synthorai 作为内置服务商

**[链接](https://github.com/netease-youdao/LobsterAI/issues/2554)** | 作者: cuihuan | 创建: 2026-08-26 | 评论: 1 | 👍: 0

**核心诉求：** 用户希望将 Synthorai（一个支持 OpenAI / Anthropic 双协议的聚合网关）纳入内置服务商列表，而非依赖 Custom 自定义槽位。

**痛点分析：**
- 内置服务商具备默认模型列表、`switchableBaseUrls` 一键切换协议、设置页图标与默认 baseUrl 等体验优势
- 自定义槽位缺乏这些配置，新用户容易将 base URL 填错（如结尾是否带斜杠）

**信号判断：** 该请求与项目已有的聚合服务商策略（如 OpenRouter 已内置）一致，未来纳入内置列表的可能性较高，但需评估 Synthorai 的接入可行性和维护成本。

---

## 5. Bug 与稳定性

今日**无新增 Bug 类 Issue**。

已知待处理问题：
- [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) — **app update 后 ready state 丢失**，已通过 PR 修复待合并，属中低优先级，不影响核心功能。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 路线图信号 |
|---|---|---|
| Synthorai 内置服务商支持 | Issue #2554 | ⭐ 中高 — 与已有聚合服务商策略一致，待维护者评估 |
| 云端分享文件永久删除 | PR #2550 | ✅ 已完成合并，进入下一版本 |
| 部署分析链路完善 | PR #2555 | ✅ 已完成合并，数据可观测性增强 |
| 登录引导 & 充值引导优化 | PR #2547 / #2552 | ✅ 已完成合并，新人上手体验改善 |

**综合判断：** 当前迭代重点围绕**用户体验细化**和**数据可观测性**推进，新功能开发节奏稳健，无明显激进变更。

---

## 7. 用户反馈摘要

- **满意点：**
  - 内置服务商的统一体验（图标、默认 baseUrl、模型列表）获得用户认可，反向推动了 Synthorai 内置诉求（Issue #2554）
  - 云端分享文件的删除操作增加"文件名二次确认"机制，体现了对用户数据安全的小心呵护

- **痛点/关注点：**
  - Custom 自定义服务商配置门槛较高，缺少引导和校验，新用户容易出错
  - 应用更新后状态（ready state）维持问题影响使用连贯性（#2551）

---

## 8. 待处理积压

| 项目 | 状态 | 建议 |
|---|---|---|
| [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) — app update preserve ready state | OPEN，待合并 | 建议尽快合并，修复后用户体验更连贯 |
| [#2554](https://github.com/netease-youdao/LobsterAI/issues/2554) — Synthorai 内置支持 | OPEN，无回复 | 维护者可评估是否纳入内置服务商路线图 |

---

**今日活跃度评级：🟢 良好** — 10/11 PR 快速合并，功能迭代健康，社区反馈明确，无阻塞性问题。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-08-27

## 1. 今日速览

Moltis 项目在过去24小时内保持**中等活跃度**，共完成1个新版本发布、1个 Issue 关闭及2个 PR 合并。项目整体进展稳健，主要聚焦于模型偏好管理功能的完善与 MCP OAuth 集成的稳定性修复，无阻塞性 Bug 上报，项目健康度良好。

---

## 2. 版本发布

### `20260826.01`
- **发布时间**：2026-08-26
- **更新内容**：
  - 合并 PR #1104：实现模型偏好替换逻辑，支持清空所有偏好设置
  - 合并 PR #1244：修复 Fastmail MCP OAuth scope 注册问题
- **破坏性变更**：无
- **迁移注意事项**：无需迁移操作，功能为增量修复与增强

---

## 3. 项目进展

| PR | 作者 | 内容 | 状态 |
|---|---|---|---|
| [#1104](https://github.com/moltis-org/moltis/pull/1104) | penso | 允许替换已保存的模型偏好，含后端与 Playwright 回归测试覆盖 | ✅ 已合并 |
| [#1244](https://github.com/moltis-org/moltis/pull/1244) | penso | 修复 Fastmail MCP OAuth scope 注册，优先使用 protected-resource scopes 并在动态客户端注册中包含所选 scopes | ✅ 已合并 |

**进展评估**：今日两个合并均服务于**可靠性增强**——PR #1104 完善了用户模型偏好的管理闭环（支持清空/替换），PR #1244 修复了特定 MCP 服务商（Fastmail）的 OAuth 集成问题。项目功能面稳步扩展，测试覆盖率同步提升。

---

## 4. 社区热点

### 🔴 Issue #1094 — De-Preferring Models [CLOSED]
- **作者**：RokkuCode | **创建**：2026-06-03 | **关闭**：2026-08-26
- [链接](https://github.com/moltis-org/moltis/issues/1094)
- **分析**：该 Issue 历时约 **2 个月** 后被关闭，与同日合并的 PR #1104 高度对应，推测已由 PR #1104 修复。用户诉求明确：希望在对话中能够"解除"对某模型的偏好设定，避免模型被错误绑定。

---

## 5. Bug 与稳定性

| 问题 | 级别 | 状态 | Fix PR |
|---|---|---|---|
| [#1094](https://github.com/moltis-org/moltis/issues/1094)：无法解除模型偏好 | 🟡 中 | ✅ 已关闭（PR #1104 修复） | [#1104](https://github.com/moltis-org/moltis/pull/1104) |
| Fastmail MCP OAuth scope 注册异常 | 🟡 中 | ✅ 已修复（PR #1244） | [#1244](https://github.com/moltis-org/moltis/pull/1244) |

**评估**：今日无新增 Bug，两项已知问题均已通过合并 PR 解决，近期稳定性风险较低。

---

## 6. 功能请求与路线图信号

- **模型偏好管理精细化**（Issue #1094 → PR #1104）：用户希望拥有对模型偏好的完整控制权（含清空、替换）。当前已实现，可作为后续"偏好组/角色化偏好"功能的铺垫。
- **MCP OAuth 标准化支持**（PR #1244）：引入 RFC 7591 动态客户端注册与 protected-resource scope 优先策略，反映项目对 **MCP 生态兼容性**的重视，预计后续还将支持更多 OAuth-protect 的 MCP 服务商。

---

## 7. 用户反馈摘要

- **痛点**：用户在长期对话后难以撤销模型偏好绑定，导致后续会话行为不符合预期（Issue #1094）。
- **使用场景**：快速切换模型偏好以适配不同任务（如开发 vs 写作），要求偏好管理具备原子性操作（单个替换或全部清空）。
- **满意度**：PR #1104 的回复逻辑完整覆盖了用户诉求，且附带回归测试，反馈积极。

---

## 8. 待处理积压

| 项目 | 作者 | 创建时间 | 距今 | 建议 |
|---|---|---|---|---|
| [#1094](https://github.com/moltis-org/moltis/issues/1094)（现已关闭） | RokkuCode | 2026-06-03 | ~2 个月 | 已由 PR #1104 修复，无需跟进 |

**当前积压评估**：今日数据范围内无长期未响应 Issue 或 PR，项目维护响应及时。建议持续监控后续 Issues 的响应周期，保持当前节奏。

---

**📊 项目健康度总结**：今日 Moltis 发布 1 个新版本，关闭 1 个 Issue，合并 2 个 PR，无新增 Bug。核心功能（模型偏好管理、MCP 集成）持续迭代，测试覆盖到位，维护响应良好，整体健康度 **良好**。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目日报 — 2026-08-27

## 1. 今日速览

CoPaw 项目今日保持高活跃度，24小时内共产生 26 条 Issue 更新和 39 条 PR 更新，新发布 v2.2.0-beta.1 版本。开发重心集中在提示词缓存可观测性、Windows 安装器稳定性修复以及控制台 UX 改进（滚动锁定、移动设备优化）三个方向。社区对多租户 Hub 版的功能规划讨论热烈（#7318），同时用户持续反馈多用户管理、上下文隔离等企业级需求，表明项目正从个人助手向团队协作场景演进。

---

## 2. 版本发布

### v2.2.0-beta.1 发布

**发布时间：** 2026-08-27

**核心变更：**
- 文档更新：滚动上下文管理器博客 (#7300)
- Provider 修复：对 DashScope 工具 Schema 进行严格模型兼容处理 (#7284)
- 集成测试覆盖扩展

**迁移注意事项：**
- 使用 DashScope 严格模式的模型需验证工具调用兼容性
- 建议用户先在内网测试环境验证后再升级生产环境

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 作者 | 类型 | 说明 |
|---|---|---|---|
| [#7338](https://github.com/agentscope-ai/QwenPaw/pull/7338) | cuiyuebing | chore | 版本号提升至 2.2.0b2 |
| [#7332](https://github.com/agentscope-ai/QwenPaw/pull/7332) | zhijianma | test | 稳定时序敏感测试，修复 GitHub Actions 失败 |
| [#7323](https://github.com/agentscope-ai/QwenPaw/pull/7323) | jinglinpeng | fix | Windows NSIS 卸载器进程检查修复 |
| [#7194](https://github.com/agentscope-ai/QwenPaw/pull/7194) | jinliyl | fix | 工作区启动失败清理取消安全修复 |
| [#7327](https://github.com/agentscope-ai/QwenPaw/pull/7327) | yutai78786 | test | E2E 控制台覆盖率提升 6-7% |

**项目前进方向：** 今日合并的 PR 主要集中在测试稳定性、Windows 安装器健壮性和代码质量改进，为 v2.2.0 正式版打下基础。待合并的 PR 显示下一步将聚焦于缓存可观测性 (#7342, #7346)、控制台 UX (#7340, #7344, #7334) 和工具调用状态管理 (#7345)。

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issues

| Issue | 类型 | 评论数 | 摘要 |
|---|---|---|---|
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | Discussion | 7 | **多租户 Hub 版 2.2.0 功能规划**：社区讨论下一步应构建什么功能，反映多用户管理是企业用户核心诉求 |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | Bug | 11 | 多步骤任务执行中 LLM 经常"规划后停止"需人工催促 |
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) | Bug | 4 | OpenSSL 3.0.x TLS 栈导致运营商 DPI 重置连接 |
| [#7258](https://github.com/agentscope-ai/QwenPaw/issues/7258) | Bug | 6 | 微信频道"显示思考过程"设置无效 |

**分析：** Issue #7318 标志着项目正式开启多租户 Hub 版的功能规划，这是从个人助手向团队协作平台演进的关键信号。历史 Issue #5780、#4702、#6335 均指向同一需求，说明多用户管理是企业级部署的长期痛点。

---

## 5. Bug 与稳定性

### 严重 Bug（按严重程度）

| Issue | 严重程度 | 状态 | Fix PR |
|---|---|---|---|
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) | 高 | OPEN | — |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | 中 | OPEN | — |
| [#7324](https://github.com/agentscope-ai/QwenPaw/issues/7324) | 中 | 已关闭 | — |
| [#7312](https://github.com/agentscope-ai/QwenPaw/issues/7312) | 中 | OPEN | — |
| [#7206](https://github.com/agentscope-ai/QwenPaw/issues/7206) | 中 | 已关闭 | — |
| [#7321](https://github.com/agentscope-ai/QwenPaw/issues/7321) | 低 | OPEN | — |

**重点说明：**
- **#7298**：桌面和 Docker 镜像基于 Debian bookworm 携带 OpenSSL 3.0.x 时代 TLS 栈，在某些运营商 DPI 环境下握手被重置。此为环境兼容性问题，暂无临时绕过方案。
- **#6921**：LLM 在输出"让我做..."类规划消息后停止执行，需用户手动输入"继续"。此为多步骤任务连续执行的已知痛点，影响用户体验。
- **#7324**：定时任务执行成功但收件箱推送消息缺失，已关闭。

**已有 Fix PR 的 Bug：**
- [#7206](https://github.com/agentscope-ai/QwenPaw/issues/7206) `compact_threshold_ratio == 0.9` 时 `/compact` 失败 → 已通过版本回退验证为回归
- [#7345](https://github.com/agentscope-ai/QwenPaw/pull/7345) 工具卡片停止后卡在"执行中"状态 → PR 待合并
- [#7331](https://github.com/agentscope-ai/QwenPaw/pull/7331) 超长单行工具结果边界处理 → PR 待合并

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 诉求 | 纳入下一版本可能性 |
|---|---|---|---|
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | Discussion | 多租户 Hub 版功能规划 | **已确定**：v2.2.0 核心特性 |
| [#7252](https://github.com/agentscope-ai/QwenPaw/issues/7252) | Enhancement | OpenViking 长期记忆后端 | 评估中，待确认架构契合度 |
| [#7339](https://github.com/agentscope-ai/QwenPaw/issues/7339) | Enhancement | 控制台流式生成时滚动锁定 | **高**：PR #7340 已提交 |
| [#7316](https://github.com/agentscope-ai/QwenPaw/issues/7316) | Question | 工具返回内容精简/删除工具 | 概念讨论，暂无具体 PR |
| [#7279](https://github.com/agentscope-ai/QwenPaw/issues/7279) | Enhancement | 多选项弹窗选择而非文本输入 | 低优先级 UX 改进 |
| [#7335](https://github.com/agentscope-ai/QwenPaw/issues/7335) | Feature | 提示词缓存命中率可观测性 | **已启动**：PR #7342、#7346 |

**路线图信号：** v2.2.0 将聚焦于：① 多租户 Hub 版基础能力；② 提示词缓存优化与可观测性；③ 控制台 UX 改进（滚动锁定、游戏开发文件语言支持、移动端优化）。

---

## 7. 用户反馈摘要

### 痛点
1. **多步骤任务连续性差**：[#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) 用户反馈 LLM 常在规划后停止，需反复输入"继续"，影响自动化任务执行效率。
2. **定时任务推送不可靠**：[#7324](https://github.com/agentscope-ai/QwenPaw/issues/7324) 3 条定时任务仅收到 2 条成功推送，缺失通知影响运维感知。
3. **上下文隔离问题**：[#7193](https://github.com/agentscope-ai/QwenPaw/issues/7193) 同一 agent 不同会话间记忆搜索错乱，混淆上下文。
4. **Windows 安装体验**：[#7188](https://github.com/agentscope-ai/QwenPaw/issues/7188) 安装脚本"删除本地应用缓存"选项缺少说明，用户困惑。
5. **后台任务列表清理**：[#7280](https://github.com/agentscope-ai/QwenPaw/issues/7280) 执行完成的后台任务未自动清除，列表臃肿。

### 满意点
- 快速响应用户反馈：#7206 的 pydantic ValidationError 回归问题在 v2.1.1-beta.1 暴露后立即回退验证。
- 测试覆盖冲刺：PR #7341 一次性提交 495 个集成测试用例，显示 CI/CD 质量提升投入。

---

## 8. 待处理积压

| Issue | 创建时间 | 天数 | 优先级 | 说明 |
|---|---|---|---|---|
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) | 2026-08-25 | 2 | 高 | OpenSSL TLS 栈兼容性，影响部分运营商网络环境 |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | 2026-08-12 | 15 | 中 | LLM 多步骤任务执行中断，用户频繁反馈 |
| [#7312](https://github.com/agentscope-ai/QwenPaw/issues/7312) | 2026-08-26 | 1 | 中 | Windows `execute_shell_command` stdin 管道悬挂 |
| [#7252](https://github.com/agentscope-ai/QwenPaw/issues/7252) | 2026-08-24 | 3 | 低 | OpenViking 长期记忆后端可行性讨论 |

**维护者关注建议：**
- **#7298** 需评估是否需要为 Windows/Docker 捆绑 newer OpenSSL 版本或提供 TLS 配置绕过选项。
- **#6921** 涉及 LLM 调用策略，建议在 v2.2.0 中通过系统提示词或工具链改进缓解。
- **#7312** 为 Windows 平台特定问题，修复相对明确（`stdin=DEVNULL`），可优先处理。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-08-27

---

## 1. 今日速览

ZeroClaw 在过去24小时内保持高强度活跃：Issues 新增/活跃 27 条，PR 提交 44 条待合并，整体贡献热度较高。今日无新版本发布，但维护者在架构 RFC、安全修复和渠道治理层面持续推进，多个高优先级安全与稳定性修复已进入最终审查或合并阶段。核心议题聚焦于会话生命周期管理、沙箱策略细化及渠道安全加固，项目正处在 v0.9.0 安全加固的关键冲刺期。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 内容 | 作者 |
|----|------|------|
| [#9748](https://github.com/zeroclaw-labs/zeroclaw/pull/9748) | 防止陈旧 provider 刷新污染替换会话（`RpcSession` 引入单调 `generation` 计数器） | h03-xydt |
| [#10138](https://github.com/zeroclaw-labs/zeroclaw/pull/10138) | Git Channel 全量编译纳入 `zeroclaw:debian` Docker 镜像 | ofotache |
| [#10327](https://github.com/zeroclaw-labs/zeroclaw/pull/10327) | 修复 Discord URL fallback 误报图片加载部分失败问题 | Audacity88 |
| [#10305](https://github.com/zeroclaw-labs/zeroclaw/pull/10305) | 从源码自动生成 SOP 语法参考文档，消除手工维护漂移 | JordanTheJet |
| [#10264](https://github.com/zeroclaw-labs/zeroclaw/pull/10264) | Quickstart CLI 验证测试_locale 独立化_ | Audacity88 |

### 重大合并成果

项目整体推进显著：
- **会话生命周期管理**：[#9748](https://github.com/zeroclaw-labs/zeroclaw/pull/9748) 以低侵入方式解决了 provider 刷新导致的会话状态污染，为 Session-persistence contract（#9600）扫清了关键障碍。
- **渠道完整性**：[#10138](https://github.com/zeroclaw-labs/zeroclaw/pull/10138) 补齐了 Docker 镜像中 Git Channel 缺失的问题，与 #10400（Telegram 未授权提示可配置）形成渠道治理闭环。
- **文档工程化**：[#10305](https://github.com/zeroclaw-labs/zeroclaw/pull/10305) 消除了 SOP 语法文档与源码的漂移风险，提升了文档可信度。

---

## 4. 社区热点

### 高讨论度 Issue（评论数 ≥ 7）

| Issue | 主题 | 评论数 | 链接 |
|-------|------|--------|------|
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | RFC: Gemini Live 实时语音到语音通道（v2 broker contract） | 21 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | RFC: 将记忆生命周期策略从存储后端解耦 | 20 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker: 维护者 RFC/设计决策队列 | 14 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | RFC: 细粒度沙箱策略（文件系统与网络限制） | 13 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |
| [#9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) | Tracker: 会话持久化合约所有权与层序 | 13 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | RFC: Desktop 屏幕交互与输入控制的 Computer-use 支持 | 11 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) |
| [#9998](https://github.com/zeroclaw-labs/zeroclaw/issues/9998) | RFC: 会话级持久化 Prompt 附件 | 9 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9998) |
| [#9990](https://github.com/zeroclaw-labs/zeroclaw/issues/9990) | RFC: 校准 PR 风险分级与安全审批要求 | 8 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9990) |
| [#9975](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) | RFC: Web bundle/daemon `web_dist_dir` 兼容性定义 | 7 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) | RFC: WASM 插件生命周期观察者订阅 | 7 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) |
| [#9330](https://github.com/zeroclaw-labs/zeroclaw/issues/9330) | RFC: AI 辅助 PR 预审与复审 | 7 | [链接](https://github.com/zeroclaw-labs/zeroclaw/issues/9330) |

### 热点分析

- **架构治理持续升温**：#8692（维护者决策队列）和 #9990（PR 风险分级）表明社区对治理透明度与贡献门槛的诉求强烈，维护者已采纳并推进了 RFC 队列机制。
- **安全边界深化**：#6996（细粒度沙箱）和 #9587（已关闭的 webhook 认证修复）形成安全加固的连续动作，反映项目正系统性收紧 agent 执行边界。
- **实时交互能力**：#8780（Gemini 语音通道）v2 已转为 broker contract 方案，今日 #10406 tracker 已创建，即将进入实现阶段。

---

## 5. Bug 与稳定性

### 高严重程度（S0–S1）

| Issue/PR | 描述 | 严重程度 | 状态 | 修复 PR |
|----------|------|----------|------|---------|
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | Daemon 启动/重载时 agent 初始化可能导致 Tokio 栈溢出 | **S1** | 开放（需复现） | — |
| [#9591](https://github.com/zeroclaw-labs/zeroclaw/issues/9591) | 重载清空所有 channel 时未重置 delivery registry | **S1** | ✅ 已关闭（#9587 修复） | [#9587](https://github.com/zeroclaw-labs/zeroclaw/pull/9587) |
| [#9651](https://github.com/zeroclaw-labs/zeroclaw/issues/9651) | 迁移后 `vision_model_provider` 无法解析密钥凭据 | **S1** | ✅ 已关闭 | — |
| [#10379](https://github.com/zeroclaw-labs/zeroclaw/issues/10379) | ZeroClaw Desktop 无法取消进行中的消息且消息队列阻塞 | **S0** | 开放 | — |
| [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | 活跃 turn 期间发送第二条消息触发并行运行，导致重复工作 | **S2** | 开放 | [#10411](https://github.com/zeroclaw-labs/zeroclaw/pull/10411)（已提交） |

### 中低严重程度（S2–S3）

| Issue | 描述 | 状态 |
|-------|------|------|
| [#10186](https://github.com/zeroclaw-labs/zeroclaw/issues/10186) | Terminal fallback 文本绕过 live delivery 合同 | 开放 |
| [#10396](https://github.com/zeroclaw-labs/zeroclaw/issues/10396) | `reasoning_content` 被重放至每条 assistant 消息 | ✅ 已关闭 |
| [#10103](https://github.com/zeroclaw-labs/zeroclaw/issues/10103) | 法语/西班牙语 Health 状态标签宽度错位 | ✅ 已关闭 |

### 安全修复 PR（今日）

| PR | 描述 |
|----|------|
| [#10409](https://github.com/zeroclaw-labs/zeroclaw/pull/10409) | 修复 temp 文件权限 0o644 → 0o600，防止语音/图像媒体数据泄露 |
| [#10381](https://github.com/zeroclaw-labs/zeroclaw/pull/10381) | 在应用 workspace cwd 前先解析 host launcher 为规范绝对路径，防止路径注入 |
| [#9678](https://github.com/zeroclaw-labs/zeroclaw/pull/9678) | 加固 Git shell 策略参数，统一 quote/escape 感知表示层 |
| [#10337](https://github.com/zeroclaw-labs/zeroclaw/pull/10337) | Git 操作严格遵从 `allowed_roots` 读写分离策略 |

> ⚠️ **#10379（S0）和 #10230（S1）尚未有合并修复 PR**，建议维护者优先跟进。

---

## 6. 功能请求与路线图信号

| 功能方向 | 关联 Issue/PR | 路线图判断 |
|----------|---------------|------------|
| Gemini 实时语音通道 | #8780（RFC 已接受）→ #10406（实现 tracker） | **高确定** — v0.9.0 内实现，broker contract 方案已成熟 |
| Desktop Computer-use | #6909（RFC v2 已更新） | **中确定** — 安全边界已澄清，等待维护者最终审批 |
| 会话级持久化 Prompt | #9998（RFC 已接受） | **高确定** — 解决了 history trimming 导致的目标丢失痛点 |
| 细粒度沙箱策略 | #6996（RFC 开放） | **中确定** — 与 #6850（记忆解耦）并行的基础设施级 RFC |
| ACP 消息序列化 | #10411（PR 已提交） | **高确定** — 修复重复并行运行的直接修复，即将合并 |
| 记忆生命周期解耦 | #6850（RFC 开放） | **中长期** — 涉及架构重构，需与 #9600 会话持久化协同 |
| Telegram 未授权提示可配置 | #10400（Feature 开放） | **中确定** — 渠道安全体验改进，风险低 |
| WASM 插件观察者 | #7822（RFC 开放） | **中长期** — 插件扩展能力的底层机制 |
| AI 辅助 PR 预审 | #9330（RFC 已折叠 pilot 行为） | **已落地** — `pr-review-pilot` 已生产运行，RFC 形式化确认 |

---

## 7. 用户反馈摘要

### 痛点

- **并行消息冲突**（#10408）：用户在 agent 活跃 turn 期间发送新消息时，系统未做串行化保护，导致重复执行和重复回复，影响使用体验。
- **取消功能失效**（#10379）：Desktop 端取消按钮在 AI 处理期间不可点击或无法终止进程，存在数据丢失/安全敏感场景下的失控风险。
- **栈溢出风险**（#10230）：Quickstart 配置应用与 daemon 重载时的初始化路径存在栈溢出隐患，阻断工作流。
- **Reasoning 内容重复发送**（#10396）：OpenAI provider 将 `reasoning_content` 在每条 assistant 消息中重放，浪费 token 且可能暴露思考链。

### 满意点

- **Discord 渠道改进**（#10327）：URL fallback 误报问题修复后，图片处理链路更可靠。
- **语言本地化对齐**（#10103）：法语/西班牙语健康面板标签宽度问题修复，提升了 TUI 国际化体验。
- **Docker 镜像完整性**（#10138）：Git Channel 纳入 debian 镜像，降低了用户部署复杂度。

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建时间 | 未响应时长 | 建议优先级 |
|----------|------|----------|------------|------------|
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | Bug S1 | 2026-08-21 | 6 天 | **紧急** — 栈溢出阻断 Quickstart 工作流 |
| [#10379](https://github.com/zeroclaw-labs/zeroclaw/issues/10379) | Bug S0 | 2026-08-26 | 1 天 | **紧急** — 取消功能失效，存在数据/安全风险 |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | RFC | 2026-05-28 | 81 天 | **高** — 沙箱策略 RFC 长期开放，需维护者裁决 |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | RFC | 2026-05-22 | 87 天 | **高** — 记忆生命周期解耦，架构关键 RFC |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) | RFC | 2026-06-17 | 62 天 | **中** — WASM 观察者订阅，等待维护者 take-over 决策 |
| [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) + [#10411](https://github.com/zeroclaw-labs/zeroclaw/pull/10411) | Bug+PR | 2026-08-27 | 今日 | **高** — PR 已提交但尚未合并，需快速审查 |
| [#10400](https://github.com/zeroclaw-labs/zeroclaw/issues/10400) | Feature | 2026-08-26 | 1 天 | **中** — Telegram 未授权提示可配置 |

---

**项目健康度评估**：🟢 **健康，高风险项需关注**。贡献流活跃（PR 44 条待合并 / Issues 37 条），安全修复节奏紧凑。核心风险在于 #10230（栈溢出）和 #10379（取消失效）两个未修复的 S0/S1 Bug，建议维护者在下一个 iteration 优先处理。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*