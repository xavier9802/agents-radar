# OpenClaw 生态日报 2026-08-01

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-01 03:33 UTC

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



# OpenClaw 项目日报 — 2026-08-01

---

## 1. 今日速览

过去24小时，OpenClaw 仓库维持高强度活跃：**500 条 Issue + 500 条 PR**，其中活跃/新开 Issue 464 条、已关闭 36 条；PR 待合并 385 条、已合并/关闭 115 条。**今日无新版本发布**。项目面临的核心挑战集中在 **Gateway 内存泄漏与稳定性**（#91588、#87109、#115908 等多个 P1/P0 级问题集中爆发），同时多平台接入（Linux/Windows 桌面端 #75）、安全能力（遮蔽密钥 #10659、信任标签 #7707）和模型管理（动态发现 #10687）的功能诉求持续升温。整体健康度：**活跃度极高，但稳定性风险处于高位，需优先处理内存与进程管理问题**。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日关闭/合并的重要 PR

| PR | 类型 | 说明 | 状态 |
|---|---|---|---|
| [#116733](https://github.com/openclaw/openclaw/pull/116733) | fix(gateway) | 防止状态 DB schema 迁移错误导致的 Gateway 重启循环（`#116239`） | ✅ **已合并** |
| [#113894](https://github.com/openclaw/openclaw/pull/113894) | fix(ui) | 恢复 Control UI 中自动 Agent 快速模式设置选项 | ✅ **已合并** |
| [#110588](https://github.com/openclaw/openclaw/pull/110588) | fix(minimax) | 修复 MiniMax Portal OAuth 登录后 `models.providers.minimax-portal.models` 为空数组的问题，解决 `? / 400k` 上下文显示错误 | ✅ **已合并** |
| [#99041](https://github.com/openclaw/openclaw/pull/99041) | fix(agents) | 解决旧版 `modelstudio:default` profile 别名无法解析的问题（`#84081`） | ✅ **已合并** |
| [#115107](https://github.com/openclaw/openclaw/pull/115107) | fix(signal) | 修复 Signal 附件上传时暴露内部 UUID 后缀，恢复原始文件名 | ✅ **已合并** |
| [#104240](https://github.com/openclaw/openclaw/pull/104240) | fix(line) | 修复 LINE 发送回执丢失真实 message_id 的问题 | ✅ **已合并** |

### 推进中的重大 PR

| PR | 说明 | 状态 |
|---|---|---|
| [#117034](https://github.com/openclaw/openclaw/pull/117034) | 新增执行身份检查（execution identity inspection）审计能力，替换同步身份持久化为有界不可变 admission envelope | ⏳ 等待作者 |
| [#115698](https://github.com/openclaw/openclaw/pull/115698) | 新增本地 faster-whisper 实时转录 Provider，支持 8kHz G.711 解码、本地 VAD、300ms 前置缓冲区 | ⏳ 等待 proof |
| [#116437](https://github.com/openclaw/openclaw/pull/116437) | 重构 Sessions，将 store 所有权从 Gateway 中剥离，支持本地运行时和插件 SDK 访问 | ⏳ 等待 maintainer |
| [#116403](https://github.com/openclaw/openclaw/pull/116403) | 集中化本地 turn lifecycle 所有权，解决 ACP 直接适配 runtime 的归属问题 | ⏳ 等待 maintainer |
| [#116016](https://github.com/openclaw/openclaw/pull/116016) | 注册 Telnyx 为官方外部 Provider，支持 Kimi/GLM/MiniMax/Qwen 等 OpenAI 兼容路由 | ⏳ 等待 proof |

**进展评估**：今日合并以渠道修复和 minor bug 为主，大型重构（session store 解耦、turn lifecycle 集中化）仍在 review 阶段。内存泄漏和进程泄漏等核心稳定性问题**尚无合并的 fix PR**，是今日最大的进展缺口。

---

## 4. 社区热点

### 🔥 评论最多 / 热度最高 Issue

| Issue | 评论数 | 👍 | 热度评级 | 核心诉求 |
|---|---|---|---|---|
| [#75](https://github.com/openclaw/openclaw/issues/75) Linux/Windows Clawdbot Apps | 116 | 80 | 🌊 off-meta tidepool | 社区对跨平台桌面客户端的强烈需求，macOS/iOS/Android 已有，Linux/Windows 缺失 |
| [#91588](https://github.com/openclaw/openclaw/issues/91588) Gateway 内存泄漏（P0） | 23 | 1 | 🐚 platinum hermit | RSS 从 350MB → 15.5GB 导致 OOM 崩溃循环，生产环境严重受影响 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) Memory Trust Tagging by Source | 23 | 0 | 🌊 off-meta tidepool | 防止 memory poisoning 攻击，按来源对 agent 记忆条目打信任标签 |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) Realtime voice 会话资源未释放 | 19 | 0 | 🦐 gold shrimp | 语音会话在 provider/client 行为异常时可无限累积 state |
| [#10659](https://github.com/openclaw/openclaw/issues/10659) Masked Secrets 遮蔽 API Key | 14 | 4 | 🦞 diamond lobster | Agent 应能使用 API Key 但不可见明文，防 prompt injection 提取凭据 |
| [#51429](https://github.com/openclaw/openclaw/issues/51429) 工作路径被 hardcode | 13 | 0 | 🐚 platinum hermit | 开发者 `wangtao` 的硬编码路径混入发布版本，引发社区信任争议 |
| [#86519](https://github.com/openclaw/openclaw/issues/86519) Telegram 重复回复 | 13 | 1 | 🦞 diamond lobster | 5.20 版本回归，Agent 在同一 Telegram 消息后发送 2-10 条相同回复 |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) Session transcript 死锁 | 12 | 0 | 🐚 platinum hermit | 持续写入下 projection 重建陷入非收敛循环，阻塞主线程数十秒 |

**热点分析**：
- **跨平台桌面端**（#75）是社区呼声最高的功能诉求（80 👍，116 评论），反映 OpenClaw 在非 Apple 生态的用户增长需求。
- **内存泄漏与稳定性**（#91588、#87109、#115908）是当前最紧迫的技术风险，直接影响生产可用性。
- **安全与信任**（#7707、#10659）反映高级用户对 agent 记忆污染和凭据泄露的深层担忧。
- **#51429** 暴露了开源项目代码审查流程的信任危机——硬编码路径被合并发布，需引起维护者重视。

---

## 5. Bug 与稳定性

### P0 — 紧急

| Issue | 描述 | Fix PR |
|---|---|---|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | **Gateway 内存泄漏**：RSS 从 350MB 增长至 15.5GB，触发 OOM 重启循环 | ❌ 无 |

### P1 — 高优先级

| Issue | 描述 | Fix PR |
|---|---|---|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | Realtime voice 会话无界累积 provider/consult state | ❌ 无 |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | Session transcript projection 在持续写入下死锁，阻塞主线程 | ❌ 无 |
| [#113306](https://github.com/openclaw/openclaw/issues/113306) | SQLite snapshot restore 缺少端到端崩溃和身份保障 | ❌ 无 |
| [#114137](https://github.com/openclaw/openclaw/issues/114137) | Visible channel 间歇性 dispatch 无 queued payload，消息持久化但未投递 | ❌ 无 |
| [#87109](https://github.com/openclaw/openclaw/issues/87109) | Gateway heap 空闲时增长至 1073MB+，cron 任务因 event-loop starvation 静默失败 | ❌ 无 |
| [#86519](https://github.com/openclaw/openclaw/issues/86519) | Telegram 重复回复回归（2026.5.20 引入，5.22 缓解未根治） | ❌ 无 |
| [#45494](https://github.com/openclaw/openclaw/issues/45494) | Cron agent job 在 LLM API 持续 500 时耗尽 timeout 而非 fast-fail | ❌ 无 |
| [#51396](https://github.com/openclaw/openclaw/issues/51396) | `clearUnboundScopes` 无条件剥离非本地 token-auth 客户端的 operator scopes | ❌ 无 |
| [#109017](https://github.com/openclaw/openclaw/issues/109017) | Anthropic provider 从模型选择器消失；手动添加模型时列表崩溃；静态 catalog 不拉取新模型 | ❌ 无 |
| [#116418](https://github.com/openclaw/openclaw/issues/116418) | Ollama provider 无法被选为 primary，路由总是 fallback | ✅ [已关闭 #116418](https://github.com/openclaw/openclaw/issues/116418) |
| [#116391](https://github.com/openclaw/openclaw/issues/116391) | WebChat 新日历日第一条消息导致 session 历史消失 | ✅ [已关闭 #116391](https://github.com/openclaw/openclaw/issues/116391) |
| [#116409](https://github.com/openclaw/openclaw/issues/116409) | 所有入站消息被写入 transcript 两次，触发 orphan removal 和 projection rebuild | ✅ [已关闭 #116409](https://github.com/openclaw/openclaw/issues/116409) |
| [#116868](https://github.com/openclaw/openclaw/issues/116868) | SQLite 会话回退到冻结的 JSONL 并复活已完成任务 | ✅ [已关闭 #116868](https://github.com/openclaw/openclaw/issues/116868) |
| [#115476](https://github.com/openclaw/openclaw/issues/115476) | Compaction 后 context refresh 重放旧 message_id，Telegram 缺少 gateway 级去重 | ❌ 无 |

### P2 — 中优先级

| Issue | 描述 | Fix PR |
|---|---|---|
| [#51429](https://github.com/openclaw/openclaw/issues/51429) | 工作路径 hardcode 进代码并发布（信任事件） | ❌ 无 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/tool 子进程泄漏，zombie 累积导致运行时退化 | ❌ 无 |
| [#46786](https://github.com/openclaw/openclaw/issues/46786) | `tools.elevated.enabled: true` 导致所有 exec 路由到 gateway 而非 sandbox | ❌ 无 |
| [#77930](https://github.com/openclaw/openclaw/issues/77930) | Discord channel 在 2026.5.4 / beta.2/beta.3 无法加载 | ❌ 无 |
| [#114255](https://github.com/openclaw/openclaw/issues/114255) | 运行中重启导致 session `status=running` + 无限 Telegram spool 重试 | ❌ 无 |
| [#85844](https://github.com/openclaw/openclaw/issues/85844) | 自动更新后 gateway 继续使用旧 hashed bundle 缓存 | ❌ 无 |
| [#48810](https://github.com/openclaw/openclaw/issues/48810) | Compaction retry 产生 parentId 链中的 orphan fork | ❌ 无 |
| [#77625](https://github.com/openclaw/openclaw/issues/77625) | `reasoningDefault=stream` 导致无限推理递归/反馈循环 | ❌ 无 |
| [#95553](https://github.com/openclaw/openclaw/issues/95553) | Preflight compaction 硬编码 ~60s 上限，忽略 `compaction.timeoutSeconds` | ❌ 无 |
| [#64267](https://github.com/openclaw/openclaw/issues/64267) | Agent 内部思考（英文）暴露给用户 | ❌ 无 |
| [#96692](https://github.com/openclaw/openclaw/issues/96692) | Slack thread 回复生成但未投递，origin tuple 丢失 | ❌ 无 |
| [#86012](https://github.com/openclaw/opencl

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-08-01 | 分析师：Agnes**

---

## 1. 生态全景

2026年夏季，个人AI助手开源生态呈现**"一超多强、分层竞争"**格局：OpenClaw以超高频社区互动确立核心参照地位，但稳定性风险制约生产落地；CoPaw与ZeroClaw凭借架构演进（内存系统重构、Provider统一）快速崛起；LobsterAI与Moltis聚焦企业级场景的安全加固与可观测性；NanoBot系列（NanoBot/NanoClaw/PicoClaw）则走差异化轻量化路线。整体生态从"功能堆砌"转向"稳定性+安全性+可观测性"三维并重，技术债务清理与架构收敛成为主流。

---

## 2. 各项目活跃度对比

| 项目 | Issues (今日) | PRs (今日) | Release | 合并率 | 健康度 |
|------|--------------|-----------|---------|--------|--------|
| **OpenClaw** | 500 (464活跃/36关闭) | 500 (385待合/115已合) | ❌ 无 | 23% | 🟠 高风险 — 稳定性缺口大 |
| **CoPaw** | 16 | 34 | ❌ 无 (2.0.1) | ~9% | 🟢 良好 — 修复密集期 |
| **ZeroClaw** | 50 (45活跃/5关闭) | 50 (41待合/9已合) | ❌ 无 | 18% | 🟢 良好 — 架构演进期 |
| **LobsterAI** | 4 | 12 | ✅ 7.31 | 93.75% | 🟢 良好 — 稳健推进 |
| **NanoClaw** | 8 | 13 | ❌ 无 | 31% | 🟡 中等 — 安全优先 |
| **Moltis** | 2 | 7 | ❌ 无 | 29% | 🟢 良好 — 安全加固期 |
| **NanoBot** | 4 | 13 | ❌ 无 | 46% | 🟢 良好 — 技术债清理 |
| **PicoClaw** | 2 | 3 | ❌ 无 | 0% | 🟡 中等 — 合并瓶颈 |
| **NullClaw** | 0 | 1 | ❌ 无 | 0% | 🟡 平稳 — 低活跃 |
| **ZeptoClaw** | 0 | 0 | ❌ 无 | — | ⚪ 停滞 |
| Hermes Agent | — | — | — | — | ⚠️ 数据缺失 |
| IronClaw | — | — | — | — | ⚠️ 数据缺失 |

---

## 3. OpenClaw 在生态中的定位

**核心参照地位无可替代**：500 Issue + 500 PR 的日活量级是第二名 CoPaw/ZeroClaw 的10倍以上，社区密度形成飞轮效应。

| 维度 | OpenClaw | 同类对比 |
|------|----------|---------|
| **技术路线** | Gateway 架构 + 多 Channel 接入 + 本地运行时 | CoPaw 基于 AgentScope；NanoBot 轻量单进程；ZeroClaw 偏 Rust 服务端 |
| **社区规模** | ★★★★★ (500+/日) | CoPaw/ZeroClaw ★★★★；LobsterAI/Moltis ★★★；其余 ★★ |
| **优势** | 渠道覆盖最广（Telegram/Signal/LINE/Discord/Slack等）、生态插件最丰富、文档最全 | — |
| **劣势** | P0 级内存泄漏未解、Issue 积压严重、信任危机（硬编码路径事件） | CoPaw 有 agentscope 背书；ZeroClaw 架构更现代 |
| **差异化** | 强调"本地优先+网关路由"，适合多通道接入场景 | NanoClaw 主打"极简安全"；PicoClaw 专注嵌入式/边缘 |

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|---------|---------|
| **内存/会话稳定性** | OpenClaw, CoPaw, ZeroClaw, LobsterAI | OpenClaw P0 内存泄漏(#91588)；CoPaw 长会话缓存失效(#6601)；ZeroClaw Hindsight 内存系统重构；LobsterAI Live Prompt 缓存命中率骤降 |
| **安全加固** | OpenClaw, NanoClaw, Moltis, ZeroClaw, LobsterAI | OpenClaw 密钥遮蔽(#10659)/信任标签(#7707)；NanoClaw 卡片伪造点击(#2923)；Moltis 路径越权(#1180)/签名验证(#1179)；ZeroClaw KeySource 抽象(#9127) |
| **多 Agent 协作** | ZeroClaw, LobsterAI, CoPaw | ZeroClaw A2A Outbound(#9106)；LobsterAI BTW 协议泄漏修复(#2414)；CoPaw spawn_subagent schema(#6609) |
| **可观测性** | Moltis, ZeroClaw | Moltis Langfuse v4 + OTLP(#1174)；ZeroClaw 跨轮次 conversation.id 关联(#8933) |
| **本地模型/CLI 集成** | NullClaw, NanoClaw, ZeroClaw | NullClaw Grok CLI(#981)；NanoClaw Apple Container(#2809)；ZeroClaw Ollama v3 schema(#9603) |
| **部署灵活性** | NanoClaw, OpenClaw | NanoClaw #1732/#1225 要求绕过 Docker；OpenClaw Linux/Windows 桌面端(#75)长期诉求 |
| **语音/实时交互** | OpenClaw, NanoBot, CoPaw | OpenClaw Realtime voice 资源泄漏(#116201)；NanoBot DeepSeek Responses API(#5197)；CoPaw 音频转录修复(#6573) |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构 |
|------|---------|---------|---------|
| **OpenClaw** | 全渠道接入 + 本地网关 + 插件生态 | 重度用户、多通道需求者、企业自部署 | Node.js Gateway + Channel Plugin 体系 |
| **CoPaw** | 桌面端体验 + 飞书/企业集成 + AgentScope 生态 | 国内企业用户、飞书生态、AgentScope 用户 | Python (AgentScope 2.x) + 桌面 Electron |
| **ZeroClaw** | 内存系统 + 安全沙箱 + 可观测性 | 生产级部署、Rust 技术栈偏好者 | Rust 服务端 + Hindsight 内存架构 |
| **LobsterAI** | UI 体验打磨 + OAuth 扩展 + 多 Agent 协作 | 中文用户、界面体验敏感者、网易生态 | 基于 OpenClaw 子系统的 UI 增强层 |
| **NanoClaw** | 极简主义 + 安全优先 + 渠道适配 | 安全敏感用户、轻量部署场景 | Go/Rust，模块化技能系统 |
| **NanoBot** | 轻量单进程 + SQLite 迁移 + 快速响应 | 个人用户、边缘设备、Termux 用户 | Python 单进程 + SQLite sessions.db |
| **Moltis** | 安全加固 + 向量记忆 + Nostr 集成 | 安全研究社区、去中心化社交场景 | Go + Zvec/redb 向量记忆 |
| **PicoClaw** | 嵌入式/边缘 + IRC/Simplex 通道 | 边缘计算、IRC 生态用户 | Go，轻量通道适配 |
| **NullClaw** | 本地 CLI 模型统一接入 | xAI/Codex/Gemini CLI 用户 | spawn-per-request Provider 模式 |

---

## 6. 社区热度与成熟度

```
活跃度分层：

🔥 超高频迭代层 (50+ 日更新)
   ├── OpenClaw (1000+/日) — 成熟期但技术债累积
   ├── CoPaw (50/日) — 快速迭代期，2.0.1 后密集修复
   └── ZeroClaw (100/日) — 架构演进期，Hindsight 推进中

🟡 稳健推进层 (10-20 日更新)
   ├── NanoClaw (21/日) — 安全优先，中等节奏
   ├── LobsterAI (16/日) — 高合并率，健康推进
   ├── Moltis (9/日) — 安全+可观测性聚焦
   └── NanoBot (17/日) — 技术债清理期

🟢 低速/休眠层 (<5 日更新)
   ├── PicoClaw (5/日) — PR 积压，合并瓶颈
   ├── NullClaw (1/日) — 单一 PR 在审
   └── ZeptoClaw (0/日) — 完全停滞
```

**关键观察**：
- **OpenClaw** 处于"高活跃+高风险"状态， Issue 积压反映维护带宽不足
- **CoPaw/ZeroClaw** 代表新一代架构的崛起，技术债务相对可控
- **LobsterAI** 以 93.75% 合并率展示成熟维护节奏
- **PicoClaw/NullClaw** 面临合并瓶颈，需警惕社区流失

---

## 7. 值得关注的趋势信号

### ① 从"功能可用"到"生产可用"的拐点
多项目集中处理内存泄漏、会话稳定性、配置损坏恢复等**基础设施级问题**（OpenClaw #91588、CoPaw #6520、ZeroClaw #9037），表明生态正在跨越"玩具项目"门槛，向生产级演进。

### ② 安全从左移走向纵深
- **输入侧**：OpenClaw 密钥遮蔽(#10659)、NanoClaw 卡片防伪造(#2923)
- **运行时**：ZeroClaw KeySource 抽象(#9127)、Moltis 路径硬化(#1180)
- **协作侧**：LobsterAI BTW 协议泄漏修复(#2414)、ZeroClaw Linq webhook 校验(#9604)

→ **建议**：开发者应将安全视为架构一等公民，而非事后补丁。

### ③ 内存/记忆系统成为新战场
ZeroClaw Hindsight 7件套、Moltis Zvec 向量记忆、LobsterAI Live Prompt 缓存优化、OpenClaw 信任标签系统 — **记忆管理**正从附属功能演变为核心竞争力。

→ **建议**：选择框架时评估其记忆系统的抽象层次与可扩展性。

### ④ 本地优先与部署灵活性诉求升温
NanoClaw #1732/#1225 反复要求绕过 Docker、OpenClaw #75 Linux/Windows 桌面端长期未满足、NullClaw Grok CLI 本地接入 — **"去容器化"** 成为边缘场景的明确信号。

→ **建议**：关注非 Docker 部署路径的成熟度，避免供应商锁定。

### ⑤ 可观测性从可选变必修
Moltis Langfuse + OTLP(#1174)、ZeroClaw 跨轮次关联(#8933) — 多轮 Agent 会话的**追踪与调试能力**正成为生产部署的硬门槛。

→ **建议**：优先选择原生支持 OpenTelemetry 或具备结构化日志框架的项目。

### ⑥ 多 Agent 协作从概念走向实现
ZeroClaw A2A Outbound(#9106)、LobsterAI 多 Agent 协作安全性、CoPaw spawn_subagent — **Agent-to-Agent** 通信协议标准化即将提速。

→ **建议**：关注 A2A（Agent-to-Agent）协议进展，提前规划多 Agent 架构。

---

**报告结语**：2026年Q3的AI智能体开源生态正经历从"功能竞赛"到"质量竞赛"的范式转换。OpenClaw 作为生态锚点面临稳定性考验，CoPaw/ZeroClaw 以现代架构追赶，LobsterAI/Moltis 在企业级场景深耕。对开发者而言，**稳定性、安全性、可观测性**已成为选型三大核心维度，建议根据部署场景（本地/云/边缘）与协作需求（单Agent/多Agent）匹配对应项目。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报

**报告日期：2026-08-01 | 数据来源：github.com/HKUDS/nanobot**

---

## 1. 今日速览

NanoBot 今日保持中等活跃度，共处理 **13 条 PR**（6 条合并/关闭、7 条待合并）和 **4 条 Issues**（2 条关闭、2 条开放）。核心亮点是 **会话存储从 JSONL 迁移至 SQLite** 的重大重构已合并，同时 **DeepSeek Responses API** 支持即将上线。微信频道 session 过期恢复机制和 Termux 时区兼容性问题均获得修复。项目整体健康度良好，技术债务清理与新功能开发并行推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#5173](https://github.com/HKUDS/nanobot/pull/5173) | **feat** | 会话存储从 JSONL 迁移至 SQLite，运行时读写统一走 `sessions.db`，JSONL 文件保留为回滚备份。这是本项目长期技术架构的一次重要升级，将显著提升大规模会话场景下的查询性能。 |
| [#5196](https://github.com/HKUDS/nanobot/pull/5196) | **fix** | 修复微信频道 session 过期后重新扫码登录时 token 未被正确加载的问题（关联 Issue #5195）。 |
| [#4223](https://github.com/HKUDS/nanobot/pull/4223) | **fix** | 修复微信频道 `_poll_once()` 在检测到 session 过期后进入 60 分钟暂停时，唤醒后未重新加载 `account.json` 导致永久静默的死循环问题。 |
| [#5192](https://github.com/HKUDS/nanobot/pull/5192) | **fix** | Slack 频道修复：线程消息的会话作用域从通道级收窄至线程级，避免不同线程之间消息交叉污染。 |
| [#5193](https://github.com/HKUDS/nanobot/pull/5193) | **fix** | WebUI 修复：优化滚动行为，保留用户在对话尾部附近的滚动所有权，避免自动跟随导致阅读体验中断。 |
| [#5189](https://github.com/HKUDS/nanobot/pull/5189) | **fix** | 在所有平台安装 `tzdata` 作为 `zoneinfo` 回退，修复 Termux 等最小化 Linux 环境下的时区加载失败问题（关联 Issue #5187）。 |

**项目推进评估**：今日 6 条合并的 PR 中有 1 条重大架构重构（SQLite 迁移）、2 条关键渠道 bug 修复（Weixin session 恢复）、1 条渠道 bug 修复（Slack 线程作用域）、1 条 WebUI 体验优化、1 条环境兼容修复。整体偏向稳定性和基础设施加固。

---

## 4. 社区热点

| 项目 | 类型 | 标题 | 评论/状态 |
|------|------|------|-----------|
| [#5197](https://github.com/HKUDS/nanobot/pull/5197) | PR | feat: support DeepSeek Responses API | 待合并 |
| [#5184](https://github.com/HKUDS/nanobot/pull/5184) | PR | feat: add Quick Chat and Temporary Chat | 待合并 |
| [#5201](https://github.com/HKUDS/nanobot/pull/5201) | PR | fix: tolerate malformed persisted session summary | 待合并 |

**热点分析**：
- **#5197**（DeepSeek Responses API）：响应了用户对 DeepSeek 新 API 的支持需求，复用现有 Responses 请求/流式/函数工具框架，保留明文推理内容。预计将成为社区关注重点。
- **#5184**（Quick Chat / Temporary Chat）：新增快速对话和临时对话功能，临时对话仅内存存储，面向不想保留历史记录的轻量场景。
- **#5201** 和 **#5200**：两条 P1 级 bug fix，分别解决 session summary 异常容错和 `wait_for` 目标在响应截断后丢失的问题，反映社区对稳定性的高要求。

---

## 5. Bug 与稳定性

| Issue/PR | 严重级别 | 描述 | 状态 |
|----------|----------|------|------|
| [#5195](https://github.com/HKUDS/nanobot/issues/5195) / [#5196](https://github.com/HKUDS/nanobot/pull/5196) | **高** | 微信 WebUI 重扫 QR 登录后，新 token 被旧 token 覆盖，导致 `errcode -14` 并触发 60 分钟暂停 | 已修复 |
| [#5198](https://github.com/HKUDS/nanobot/issues/5198) | **中** | 无法在特定 session 中切换模型，UI 交互缺失 | 开放 |
| [#5187](https://github.com/HKUDS/nanobot/issues/5187) / [#5189](https://github.com/HKUDS/nanobot/pull/5189) | **中** | Termux 环境因缺少系统时区数据库导致启动失败 | 已修复 |
| [#5190](https://github.com/HKUDS/nanobot/issues/5190) / [#5191](https://github.com/HKUDS/nanobot/pull/5191) | **中** | Windows 上 MIME 类型错误（`text/plain`）导致 JS 模块加载失败 | 待合并 |

**稳定性总结**：今日修复了 2 个中高严重性 bug（微信 token 覆盖、Termux 时区），1 个 Windows 兼容性问题待合并。仍有 2 个开放 bug 需关注。

---

## 6. 功能请求与路线图信号

| 请求来源 | 内容 | 关联 PR | 纳入可能性 |
|----------|------|---------|------------|
| Issue #5198 | 支持在特定 session 中切换模型 | 无 | 待评估 |
| PR #5184 | Quick Chat / Temporary Chat | [#5184](https://github.com/HKUDS/nanobot/pull/5184) | 高（已在开发中） |
| PR #5197 | DeepSeek Responses API 支持 | [#5197](https://github.com/HKUDS/nanobot/pull/5197) | 高（已在开发中） |

**信号判断**：
- **DeepSeek API 支持**和**快速/临时对话**已处于 PR 阶段，很可能纳入下一版本。
- **Session 级别模型切换**（Issue #5198）尚无对应 PR，但用户诉求明确，建议维护者评估是否纳入路线图。
- **SQLite 会话存储**（PR #5173）已合并，标志着会话管理架构进入新阶段，后续可能围绕此基础推出更多查询和数据分析功能。

---

## 7. 用户反馈摘要

| 用户 | 场景 | 痛点/反馈 |
|------|------|-----------|
| amkile (#5195, #5190) | 微信登录 | 重扫 QR 登录后 session 立即失效，怀疑 token 覆盖问题；Windows 下 WebUI 无法启动 |
| whisperity (#5198) | 日常使用 | 期望像 SaaS AI 产品一样可随时切换模型，当前仅支持全局配置，缺乏灵活性 |
| CVFA1 (#5187) | Termux 测试 | 在 Termux 环境下因时区缺失无法启动，希望支持移动端 Linux 环境 |
| KDB-Wind (#5201, #5200) | 稳定性 | session summary 元数据异常会导致启动失败，`wait_for` 机制在响应截断时丢失目标 |

**整体情绪**：用户关注点集中在 **登录稳定性**（微信 session 管理）、**使用灵活性**（模型切换、多环境兼容）和 **底层健壮性**（异常容错）。

---

## 8. 待处理积压

| 项目 | 类型 | 标题 | 创建时间 | 建议 |
|------|------|------|----------|------|
| [#5198](https://github.com/HKUDS/nanobot/issues/5198) | Bug | 无法在特定 session 中切换模型 | 2026-07-31 | 用户诉求明确，建议评估优先级 |
| [#5190](https://github.com/HKUDS/nanobot/issues/5190) | Bug | Windows MIME 类型导致 JS 加载失败 | 2026-07-31 | 关联 PR #5191 待合并，合并后关闭 |
| [#5201](https://github.com/HKUDS/nanobot/pull/5201) | PR | 容忍 malformed session summary | 2026-07-31 | P1 级修复，建议优先审查 |
| [#5200](https://github.com/HKUDS/nanobot/pull/5200) | PR | 修复 wait_for 在响应截断后丢失 | 2026-07-31 | P1 级修复，建议优先审查 |
| [#5199](https://github.com/HKUDS/nanobot/pull/5199) | PR | 收窄 CLI Pyright 类型抑制范围 | 2026-07-31 | 重构类 PR，建议按计划审查 |

**维护者提示**：今日有 5 条待处理 PR，其中 2 条为 P1 稳定性修复，建议优先合并。Issue #5198 涉及模型切换交互，可能影响用户体验，建议安排排期。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-01

---

## 1. 今日速览

过去24小时内，PicoClaw 仓库保持活跃：**2条 Issues 更新、3条 PR 更新**，整体呈"只进不出"状态——无 Issue 关闭、无 PR 合并、无新版本发布。项目当前处于功能迭代期，社区贡献持续涌入，但合并节奏偏慢，部分 PR 积压时间较长（最长超30天）。Issue 端以功能需求和高优先级 Bug 为主，用户参与度中等（评论数较少，点赞为0）。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

今日无 PR 合并，所有 PR 均维持 Open 状态：

| PR | 状态 | 摘要 |
|---|---|---|
| [#3222](https://github.com/sipeed/picoclaw/issues/3222) | Open | Deltachat 通道实现重构，清理废弃功能，约减少 200 行代码（-200 LOC） |
| [#3193](https://github.com/sipeed/picoclaw/issues/3193) | Open | 新增 Simplex 通道类型支持 |
| [#3200](https://github.com/sipeed/picoclaw/issues/3200) | Open | 新增模型默认回退链可配置功能，支持 Web UI + Backend API |

**评估**：三项 PR 分别覆盖通道扩展（Simplex）、现有通道重构（Deltachat）和模型配置优化（Fallback Chain），均指向功能增强方向。然而 **3 条 PR 均未进入合并流程**，项目推进力偏弱。

---

## 4. 社区热点

### 关注 Issue #3287：IRC 长消息支持
- **链接**: [Issue #3287](https://github.com/sipeed/picoclaw/issues/3287)
- **热度指标**：评论 2 条，创建时间 2026-07-22，最近活跃 2026-07-31
- **分析**：用户提出 IRCv3 长消息被截断的问题，属于协议兼容性与用户体验的交叉痛点。该功能若实现，将显著提升 PicoClaw 在多通道场景下的消息完整性，适合纳入后续版本路线图。

### 关注 Issue #3292：CPU 占用过高 Bug
- **链接**: [Issue #3292](https://github.com/sipeed/picoclaw/issues/3292)
- **热度指标**：评论 1 条，状态标记为 stale，创建时间 2026-07-24，最近活跃 2026-07-31
- **分析**：用户在使用 Firefox 浏览器、聊天界面输入框获得焦点时报告 CPU 异常升高，环境为 PicoClaw 0.3.1 + Go 1.26 + deepseek-v4-flash 模型。此问题具有明确的复现路径，属于中高优先级的性能 Bug，建议尽快排查前端事件循环或渲染开销。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | 是否有 Fix PR |
|---|---|---|---|
| 🔴 高 | [#3292](https://github.com/sipeed/picoclaw/issues/3292) | 聊天界面输入框获焦时 CPU 占用过高，Firefox 浏览器下复现 | ❌ 暂无 |

> 其余今日更新 Issue 均为功能请求，无新增崩溃或回归报告。

---

## 6. 功能请求与路线图信号

| 来源 | 需求描述 | 关联 PR | 纳入下一版本可能性 |
|---|---|---|---|
| [Issue #3287](https://github.com/sipeed/picoclaw/issues/3287) | IRC 长消息支持（IRCv3 消息合并） | 暂无关联 PR | ⭐⭐⭐ 高——明确的协议扩展需求 |
| [PR #3193](https://github.com/sipeed/picoclaw/pull/3193) | 新增 Simplex 通道类型 | — | ⭐⭐⭐ 高——新通道扩展，非破坏性 |
| [PR #3200](https://github.com/sipeed/picoclaw/pull/3200) | 模型回退链可配置化（Web UI + API） | — | ⭐⭐⭐ 高——增强配置灵活性 |
| [PR #3222](https://github.com/sipeed/picoclaw/pull/3222) | Deltachat 实现重构与清理 | — | ⭐⭐ 中——清理性质，需代码审查 |

**综合判断**：未来 1-2 个版本预计将集中覆盖 Simplex 通道支持、IRC 长消息兼容和模型回退链配置三大方向。

---

## 7. 用户反馈摘要

- **IRC 长消息场景**（Issue #3287）：用户反馈 IRCv3 消息在超过 512 字节时被客户端自动截断，PicoClaw 未能将其识别为单条完整消息，导致上下文断裂，影响 AI 模型的理解效果。
- **性能体验**（Issue #3292）：用户在使用 Firefox + deepseek-v4-flash 模型时，输入框获得焦点即触发高 CPU 占用，影响日常交互流畅度，且未提供已知规避方案。
- **整体满意度**：当前 Issue 评论数均较低，未出现大规模负面反馈，社区态度总体积极，问题以建设性需求为主。

---

## 8. 待处理积压

| 类型 | 编号 | 创建时间 | 最近活跃 | 备注 |
|---|---|---|---|---|
| PR | [#3193](https://github.com/sipeed/picoclaw/pull/3193) | 2026-06-27 | 2026-07-31 | Simplex 通道支持，Open 超35天，待审查 |
| PR | [#3200](https://github.com/sipeed/picoclaw/pull/3200) | 2026-07-01 | 2026-07-31 | 模型回退链配置，Open 超30天，待审查 |
| PR | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | 2026-07-03 | 2026-07-31 | Deltachat 重构，Open 超28天，待审查 |
| Issue | [#3292](https://github.com/sipeed/picoclaw/issues/3292) | 2026-07-24 | 2026-07-31 | CPU 高占用 Bug，已标记 stale，需优先跟进 |

> ⚠️ **维护者提醒**：3 条 PR 均已停滞近一个月，建议尽快安排代码审查；Issue #3292 状态为 stale 但问题影响用户体验，建议重新激活处理。

---

**📊 项目健康度评估**：中等偏积极。社区贡献活跃（6项更新/24h），功能方向清晰；但合并节奏偏慢，Bug 修复通道效率有待提升。建议维护侧加强 PR 审查响应速度，优先处理 #3292 性能问题。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-08-01

## 1. 今日速览

NanoClaw 今日活跃度维持中高水平：8 条新 Issue 更新、13 条 PR 更新（9 条待合并、4 条已关闭），无新版本发布。社区对"非 Docker 部署"和"渠道集成扩展"的诉求显著，4 个 PR 今日被合并/关闭，涵盖 iMessage、语音转录技能和发布路径修复，项目整体在安全性和渠道适配两条主线同步推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日关闭/合并的 PR 共 4 条，主要推进方向如下：

- **#3163** [CLOSED] 恢复 v2.1.54 发布路径 — 修复了中断的发布流程，保障版本交付连续性。
- **#3076** [CLOSED] iMessage 统一本地+托管适配器（targeting spectrum-ts v11）— 扩展了 iMessage 渠道支持，为后续托管版 iMessage 铺路。
- **#1678** [CLOSED] 更新 Telegram + Linux 语音转录技能 — 移除 WhatsApp 限制，扩大 `use-local-whisper` 技能适用范围。
- **#3165** [CLOSED] Codex/copilot 相关变更 — 清理或合并了 IDE 集成相关内容。

项目整体在**渠道扩展**和**发布流程稳定性**两个维度持续迭代，安全相关修复（#2801、#2651、#3161）也在并行推进中，整体向前稳步推进。

---

## 4. 社区热点

### 🔥 Issue #1732 — 原生运行模式（绕过 Docker）
- **作者**: stevengonsalvez | **评论**: 3 | 👍 0
- [链接](https://github.com/qwibitai/nanoclaw/issues/1732)
- **热点分析**: 用户明确提出容器隔离在 tmux、headed browser、macOS API 等场景下成为硬阻塞，诉求强烈。同类诉求在 #1225（不用 Docker）和 #2354（K8s 运行时）中反复出现，说明"轻量化部署"是社区持续关注的核心方向。

### 🔥 Issue #2923 — ask_user_question 卡片可被伪造点击欺骗
- **作者**: glifocat | **评论**: 0 | 👍 0
- [链接](https://github.com/qwibitai/nanoclaw/issues/2923)
- **热点分析**: 安全研究者报告了一个显示完整性 spoof 漏洞，虽然响应被 origin check 拒绝，但卡片文本可被篡改。对应 PR #2651 已提出修复方案（验证响应来源），值得持续跟进。

### 🔥 Issue #3162 — Telegram 配对接失败导致永久锁定
- **作者**: glifocat | **评论**: 0 | 👍 0 | **Priority: High**
- [链接](https://github.com/qwibitai/nanoclaw/issues/3162)
- **热点分析**: 启动时单次 `getMe` HTTP 失败即可永久阻断配对流程，且无任何错误提示，用户体验影响严重。高优先级 Bug，需尽快修复。

---

## 5. Bug 与稳定性

| 级别 | Issue/PR | 描述 | 状态 |
|------|----------|------|------|
| 🔴 High | [#3162](https://github.com/qwibitai/nanoclaw/issues/3162) | Telegram 配对接入失败后永久锁定，无错误提示 | 新报，暂无 Fix PR |
| 🟠 Medium | [#2589](https://github.com/qwibitai/nanoclaw/issues/2589) | Apple Container 中 `host.docker.internal` 无法解析，不支持 `--add-host` | 新报 |
| 🟠 Medium | [#2588](https://github.com/qwibitai/nanoclaw/issues/2588) | `skill/apple-container` 分支与主线严重脱节，技能执行即失败 | 新报 |
| 🟡 Low | — | [#2750](https://github.com/qwibitai/nanoclaw/pull/2750) — 容器 SIGKILL 后 `outbound.db` 日志堆积 | PR 待合并中 |

**说明**: 安全相关修复 PR #2801（路由器输入加固）和 #3161（日志脱敏）已在推进，可有效缓解 #2923 类风险。

---

## 6. 功能请求与路线图信号

| 诉求 | Issue/PR | 纳入下版可能性 |
|------|----------|----------------|
| Apple Container 原生运行时 + 远程 OneCLI 网关 | [#2809](https://github.com/qwibitai/nanoclaw/pull/2809) [OPEN] | ✅ 高 — PR 已就绪，环境开关设计合理 |
| K8s 容器运行时（替代本地 Docker） | [#2354](https://github.com/qwibitai/nanoclaw/issues/2354) [OPEN] | 🟡 中 — 诉求明确但 PR 尚未出现 |
| 绕过 Docker 的原生模式（tmux/浏览器/macos API） | [#1732](https://github.com/qwibitai/nanoclaw/issues/1732) [OPEN] | 🟡 中 — 架构影响较大，需谨慎设计 |
| Dial 渠道适配器（SMS + AI 语音通话） | [#3041](https://github.com/qwibitai/nanoclaw/pull/3041) [OPEN] | ✅ 高 — Feature skill 模式，风险低 |
| 托管 iMessage（Photon） | [#3164](https://github.com/qwibitai/nanoclaw/pull/3164) [OPEN] | ✅ 高 — 承接 #3076 合并的基础 |
| 安全报告与分诊策略文档 | [#2954](https://github.com/qwibitai/nanoclaw/pull/2954) [OPEN] | ✅ 高 — 运维基础设施完善 |

---

## 7. 用户反馈摘要

**痛点集中区：**
- **部署门槛**: 多处 Issue（#1184、#1225、#1732）反复询问"能否不用 Docker"，反映出用户在无容器环境（Windows/Linux 裸机、生产 K8s 受限集群）中的部署困境。
- **Apple Container 体验差**: #2588 和 #2589 指出分支脱节和 hostname 解析问题，说明 Apple Container 功能维护滞后，用户信任度受损。
- **Telegram 配对脆弱**: #3162 暴露了启动时单次网络抖动即可永久阻断使用的严重 UX 问题，用户反馈"无任何提示"。

**正面反馈:**
- #1184 中用户高度认可 NanoClaw 的"极简主义"和"轻量安全"定位，认为用既有 code agent 构建 Claw 的思路" Brilliant"。

---

## 8. 待处理积压

| Issue/PR | 创建时间 | 状态 | 备注 |
|----------|----------|------|------|
| [#1732](https://github.com/qwibitai/nanoclaw/issues/1732) — 原生运行模式 | 2026-04-10 | OPEN，3 评论 | 长期诉求，4 个月未响应核心需求 |
| [#1225](https://github.com/qwibitai/nanoclaw/issues/1225) — 不用 Docker 运行 | 2026-03-18 | OPEN，2 评论 | 与 #1732 同诉求，长期未处理 |
| [#1184](https://github.com/qwibitai/nanoclaw/issues/1184) — K8s 受限环境部署 | 2026-03-17 | OPEN，3 评论，👍1 | 生产环境用户真实诉求，持续跟进 |
| [#2588](https://github.com/qwibitai/nanoclaw/issues/2588) — apple-container 分支脱节 | 2026-05-22 | OPEN | 功能断裂，需尽快同步或废弃 |
| [#2354](https://github.com/qwibitai/nanoclaw/issues/2354) — K8s 容器运行时 | 2026-05-08 | OPEN，1 评论 | 有用户主动提出方案，可推动 PR |
| [#2923](https://github.com/qwibitai/nanoclaw/issues/2923) — 安全：卡片伪造点击 | 2026-07-04 | OPEN | 安全漏洞，对应 PR #2651 待合并 |

> ⚠️ **维护者关注建议**: #1732/#1225 长期积压反映部署灵活性是社区核心痛点，建议评估是否将 #2809（Apple Container）和 #3041（Dial 渠道）作为短期优先合并项，同时为原生模式需求给出明确路线图回应。#3162 高优先级 Bug 需尽快修复以避免用户流失。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 — 2026-08-01

---

## 1. 今日速览

过去 24 小时内 NullClaw 项目处于**低活跃度状态**，无任何 Issue 更新，亦无 PR 合并或版本发布。社区仅维持一条正在 Review 中的 PR（#981），整体开发节奏较为平静，未出现关键功能落地或紧急修复事件，项目健康度指标中性偏稳定。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

**今日合并/关闭的 PR：0 条**

当前唯一活跃的 PR 处于开放状态，尚未合并，暂不对主线代码产生贡献。以下为待审核条目：

- **#981 — [OPEN] feat(provider): add grok-cli provider for xAI Grok CLI**
  - 作者：`valonmulolli` | 创建：2026-07-29 | 最后更新：2026-07-31
  - 摘要：新增 `grok-cli` Provider，遵循现有 `codex-cli` / `gemini-cli` / `claude-cli` 的 spawn-per-request 模式，调用本地 `grok` CLI（xAI Grok）作为可选 Provider。
  - 链接：https://github.com/nullclaw/nullclaw/pull/981

> ⚠️ 该 PR 已开放超过 2 天未见合并动作，建议维护者跟进 Review 状态，以判断是否进入加速通道。

---

## 4. 社区热点

今日无新 Issue 或 PR 获得评论互动，社区暂无明显热点话题。唯一活跃 PR #981 目前评论数为零，尚未引发讨论。

---

## 5. Bug 与稳定性

今日无 Bug 报告、崩溃反馈或回归问题。

---

## 6. 功能请求与路线图信号

| 信号 | 详情 |
|------|------|
| **xAI Grok CLI 支持** | PR #981 正在补充 xAI Grok 的本地 CLI Provider，与现有 Codex/Gemini/Claude CLI 形成完整多 Provider 矩阵，反映社区对**本地大模型 CLI 统一接入**的持续需求 |

> 若 #981 顺利合并，NullClaw 的 Provider 生态将进一步扩展，建议将其纳入下一版本路线图评估。

---

## 7. 用户反馈摘要

今日无新的 Issue 评论，无新增用户反馈可供提炼。

---

## 8. 待处理积压

| 类型 | 编号 | 标题 | 开放天数 | 风险 |
|------|------|------|----------|------|
| PR | [#981](https://github.com/nullclaw/nullclaw/pull/981) | feat(provider): add grok-cli provider for xAI Grok CLI | ~3 天 | 低 — 功能扩展型 PR，无紧急性 |

**建议**：今日整体积压较低，维护者可将精力集中于 #981 的代码 Review，确保 Provider 接入模式的代码质量与一致性。

---

> 📊 **项目健康度评估：🟡 平稳** — 无紧急事项，无新贡献流入，但有明确的扩展方向（grok-cli）处于 Review 流程中，项目维持正常推进节奏。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报
**日期：2026-08-01 | 数据来源：GitHub (netease-youdao/LobsterAI)**

---

## 1. 今日速览

过去24小时，LobsterAI 项目保持稳健更新节奏，共处理 **16 个活动项**（4 Issues + 12 PRs），其中 **15 项已关闭/合并**，1 项仍处于待合并状态。今日无明显版本发布，但 **MaoQianTu** 一口气完成了 3 个长期未关闭的 UX 增强 Issue（侧边栏拖拽、快捷键提示、骨架屏加载），反映出社区对界面体验的持续关注。OpenClaw 子系统同步收到多项底层稳定性修复，涉及缓存命中率、协议泄漏和 yield 机制。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 摘要 |
|----|------|------|
| [#2416](https://github.com/netease-youdao/LobsterAI/pull/2416) | Release | Release/2026.7.31 版本发布 |
| [#172](https://github.com/netease-youdao/LobsterAI/pull/172) | feat(oauth) | 新增 Antigravity OAuth 接入及代理兼容支持，含 OAuth 状态管理、持久化及模型同步 |
| [#1315](https://github.com/netease-youdao/LobsterAI/pull/1315) | feat(cowork) | 实现侧边栏拖拽调整宽度（180px~480px），关联关闭 Issue #1314 |
| [#1318](https://github.com/netease-youdao/LobsterAI/pull/1318) | feat(cowork) | 侧边栏按钮展示 `<kbd>` 快捷键徽标，支持平台感知（macOS/Windows/Linux） |
| [#1320](https://github.com/netease-youdao/LobsterAI/pull/1320) | feat(cowork) | 会话列表添加骨架屏加载状态，消除启动时空状态闪烁 |
| [#1308](https://github.com/netease-youdao/LobsterAI/pull/1308) | feat(cowork) | 首页输入草稿按 Agent 隔离，避免不同 Agent 间输入内容互相污染 |
| [#1321](https://github.com/netease-youdao/LobsterAI/pull/1321) | fix(settings) | 修复切换设置标签页时 overlay 未正确关闭的 Bug |
| [#2417](https://github.com/netease-youdao/LobsterAI/pull/2417) | fix(sites) | 站点 URL 复制反馈优化，复用对话复制交互 |
| [#2415](https://github.com/netease-youdao/LobsterAI/pull/2415) | fix(openclaw) | 修复 Live Prompt 投影中 aggregate cap 重写工具结果历史导致的缓存命中率骤降（DeepSeek 从 ~100% 降至 ~57%） |
| [#2414](https://github.com/netease-youdao/LobsterAI/pull/2414) | fix(cowork) | 阻止 BTW 工具协议泄漏至 side-chat 结果，保持错误元数据穿透 OpenClaw 网关 |
| [#2413](https://github.com/netease-youdao/LobsterAI/pull/2413) | fix(openclaw) | 保证 Live Prompt 工具结果历史跨轮次字节稳定性，防止重复重写缓存历史 |

> **总体评估：** 今日 11 个 PR 全部合入主线，覆盖 OAuth 扩展、UX 细节打磨、OpenClaw 底层修复三个方向，项目整体保持健康的合入率。

---

## 4. 社区热点

### 高关注 Issues（全部已关闭）

1. **[Issue #1314](https://github.com/netease-youdao/LobsterAI/issues/1314)** — 拖拽调整侧边栏宽度
   - 作者 MaoQianTu 提出，评论 2 条
   - 核心诉求：不同屏幕尺寸下侧边栏固定 240px 导致布局不适配，用户希望自由调整宽度
   - ✅ 已由 PR #1315 实现

2. **[Issue #1317](https://github.com/netease-youdao/LobsterAI/issues/1317)** — 侧边栏快捷键可视化提示
   - 同一作者，评论 2 条
   - 核心诉求：Ctrl+N / Ctrl+F 快捷键隐藏过深，新用户发现成本高
   - ✅ 已由 PR #1318 实现，新增平台感知的 `<kbd>` 徽标

3. **[Issue #1319](https://github.com/netease-youdao/LobsterAI/issues/1319)** — 会话列表骨架屏加载
   - 评论 2 条
   - 核心诉求：应用启动时空状态闪烁，用户误以为历史丢失
   - ✅ 已由 PR #1320 实现，新增 `sessionsLoaded` 状态标志位

4. **[Issue #1311](https://github.com/netease-youdao/LobsterAI/issues/1311)** — 表格内容换行及长文本 hover 展示
   - 作者 Cathylkx，评论 2 条
   - 核心诉求：表格内换行丢失原始标签、长文本截断无法查看
   - ✅ 已关闭（状态为 stale）

---

## 5. Bug 与稳定性

| 问题 | 严重度 | 状态 | 关联 |
|------|--------|------|------|
| OpenClaw Live Prompt 聚合 cap 重写历史导致缓存命中率骤降 | 🔴 高 | 已修复 | PR #2415 合入 |
| BTW 工具协议泄漏至 side-chat 结果 | 🟡 中 | 已修复 | PR #2414 合入 |
| 切换设置标签页时 overlay 未正确关闭 | 🟡 中 | 已修复 | PR #1321 合入 |
| cron yield 后子 agent 完成事件无法驱动父 agent | 🟡 中 | ⚠️ 待处理 | PR #2234 仍 OPEN |

> **稳定性评估：** 核心 Bug 均有对应修复合入主线。唯一遗留风险为 PR #2234（cron yield 子 agent finalization），已开放 31 天未合并，需关注。

---

## 6. 功能请求与路线图信号

| 诉求来源 | 需求描述 | 当前状态 | 纳入预期 |
|----------|----------|----------|----------|
| Issue #1311 / PR #1308 相关 | 表格渲染优化（换行保留标签、长文本 hover） | Issue 已 stale 关闭，未看到对应 PR | 待定，需确认是否有后续实现 |
| Issue #1314/#1317/#1319 | 侧边栏 UX 增强（宽度拖拽、快捷键提示、骨架屏） | 全部已合入 | ✅ 已在 Release/2026.7.31 中 |
| PR #172 | Antigravity OAuth 接入 | 已合入 | ✅ 可作为第三方 OAuth 扩展能力 |
| PR #2414 | BTW 工具协议隔离 | 已合入 | ✅ 提升多 Agent 协作安全性 |

---

## 7. 用户反馈摘要

- **侧边栏 UX 痛点明确：** 用户反馈固定宽度在小屏设备上挤压主内容区，大屏设备则浪费空间；快捷键隐藏过深导致新用户学习成本高；启动时空状态闪烁引发"历史记录丢失"误解。三项诉求均已通过 MR 解决，反映出维护者对社区反馈响应积极。

- **OpenClaw 长会话缓存问题：** 用户（通过 PR 作者反馈）指出 DeepSeek 长会话缓存命中率从 ~100% 骤降至 ~57%，根源在于 Live Prompt 投影每次请求都重新应用字符上限导致历史被重写。修复方案将 `aggregateMaxCharsOverride` 设为 `null`，保障历史字节稳定性。

- **多 Agent 协作改进：** 首页输入草稿按 Agent 隔离（PR #1308）和 BTW 工具协议泄漏修复（PR #2414）说明项目在 multi-agent 场景下的稳定性持续加固。

---

## 8. 待处理积压

| PR/Issue | 状态 | 创建时间 | 风险说明 |
|----------|------|----------|----------|
| [#2234](https://github.com/netease-youdao/LobsterAI/pull/2234) — fix(openclaw): cron yield descendant finalization | 🔵 OPEN | 2026-06-30 | 已开放 31 天未合入，涉及 cron 场景下子 agent yield 后父 agent 无法继续执行的 Bug，影响多轮会话稳定性，建议优先 Review |
| [#1311](https://github.com/netease-youdao/LobsterAI/issues/1311) — 表格换行及 hover | 🔴 Stale | 2026-04-02 | Issue 已 stale 关闭但无对应 PR，表格渲染优化需求可能落空 |

---

**项目健康度评分：🟢 良好** — 合入率 93.75%（15/16），Bug 修复响应及时，社区反馈闭环率高。唯一关注点为 PR #2234 的合并延迟。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 | 2026-08-01

## 1. 今日速览
2026-08-01 Moltis 项目处于高活跃开发周期，过去24小时内共更新 PR 7 条（已关闭/合并 2 条，待审 5 条）、Issues 2 条。开发重心明显向**安全加固**与**可观测性基础设施**倾斜，同时完成了 Nostr 群聊集成与 Markdown 导出两项功能闭环。项目整体健康度良好，历史技术债（权限边界、路径越权）正被系统性修复，路线图推进有序。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
今日合并/关闭 2 个 PR，标志两项功能正式进入主干：
- **#1176** [feat(web)] 完成 Markdown 复制与会话导出功能，响应了长期社区需求（关联 Issue #1131 已关闭）。
- **#1168** [feat(nostr)] 为 Buzz 渠道补充 NIP-29 群聊支持，完善了 Nostr 生态的即时通讯能力。

此外，3 个安全相关 PR（#1170、#1179、#1180）正处于 Open 状态，聚焦权限隔离与路径越权修复。若按预期合并，将显著提升生产部署的安全基线。

## 4. 社区热点
- **Issue #1181** [OPEN] [Bug] GPT 5.6 Luna 兼容性异常 [链接](https://github.com/moltis-org/moltis/issues/1181)
  用户反馈最新 GPT 模型调用出现异常，反映社区对前沿模型 API 适配的高敏感度。
- **Issue #1131** [CLOSED] 复制/导出 Markdown 功能请求 [链接](https://github.com/moltis-org/moltis/issues/1131)
  伴随 PR #1176 的合并正式闭环。该需求长期存在且获 1 票认可，显示用户对内容可移植性与历史记录管理的强诉求。

## 5. Bug 与稳定性
- **P2 | 模型兼容性问题**：#1181 报告 GPT 5.6 Luna 调用异常，暂无关联 Fix PR。建议优先排查上游 API 变更与上下文解析逻辑。
- **安全修复（主动治理）**：#1179（节点配对签名验证）与 #1180（模型/ZIP 路径硬化）针对任意文件写入与越权执行风险，属于高危级预防性修复。合并后将堵截潜在的 RCE 路径。

## 6. 功能请求与路线图信号
- **可观测性增强**：#1174 引入 Langfuse v4 导出、OTLP 后端支持及用户反馈收集机制，表明项目正从“单点 Agent”向“可监控、可评估的生产级 AI 代理平台”演进。
- **记忆后端扩展**：#1158 提供基于 Zvec + redb 的向量数据库记忆后端，反映用户对本地化/轻量级记忆存储的探索需求，可能丰富未来的后端插件生态。
- **安全与权限精细化**：#1170 明确划分“访问白名单”与“特权操作符列表”，路线图将强化多租户与细粒度权限控制。

## 7. 用户反馈摘要
- **痛点**：最新模型（如 GPT 5.6 Luna）适配滞后；历史会话缺乏便捷导出/复制手段（已缓解）。
- **安全诉求**：用户与安全贡献者（如 tsauvajon）主动提交路径越权与签名伪造修复，说明社区对生产部署安全性高度关注，且具备较强的安全审查意识。
- **功能期待**：Nostr/Buzz 深度集成、可观测性指标下钻、多样化记忆存储后端。

## 8. 待处理积压
以下 Open PR/Issue 建议优先跟进：
- 🔒 **安全修复**：#1170（权限边界隔离）[链接](https://github.com/moltis-org/moltis/pull/1170)、#1179（节点配对签名）[链接](https://github.com/moltis-org/moltis/pull/1179)、#1180（路径硬化）[链接](https://github.com/moltis-org/moltis/pull/1180) —— 建议优先 Code Review 与合并。
- 🔭 **可观测性**：#1174（仪表化与反馈收集）[链接](https://github.com/moltis-org/moltis/pull/1174) —— 涉及架构变更，需确认后端兼容性与性能影响。
- 🧠 **功能扩展**：#1158（Zvec 记忆后端）[链接](https://github.com/moltis-org/moltis/pull/1158) —— 实验性特性，建议验证稳定性后纳入正式文档。
- 🐛 **模型兼容**：#1181（GPT 5.6 Luna Bug）[链接](https://github.com/moltis-org/moltis/issues/1181) —— 需确认是否为上游 API 变更导致的回归。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报

**日期：** 2026-08-01  
**数据来源：** [agentscope-ai/QwenPaw](https://github.com/agentscope-ai/QwenPaw)  
**报告周期：** 2026-07-31 00:00 – 2026-08-01 00:00 (UTC+8)

---

## 1. 今日速览

CoPaw 项目今日保持**高活跃度**，24小时内累计 50 条更新（16 Issues + 34 PRs），新增贡献者 4 位（mohitdebian、dl-g2026、GMsure、lalaliat）。**3 个 PR 已合并**，主要聚焦于音频转录修复、内存压缩修复和 Shell 命令超时处理。项目当前处于 2.0.1 版本后的密集修复期，核心稳定性问题（UI 冻结、JSON 损坏、agentscope 兼容性）均有对应 PR 正在推进，整体健康度良好，但仍有 24 个待合并 PR 积压，需关注审查节奏。

---

## 2. 版本发布

**无新版本发布。** 当前最新版本仍为 **2.0.1**，社区反馈多个兼容性与回归问题，预计下一个补丁版本将集中吸收今日合并的修复。

---

## 3. 项目进展

### 今日合并/关闭的 PR

| PR | 作者 | 类型 | 说明 |
|---|---|---|---|
| [#6573](https://github.com/agentscope-ai/QwenPaw/pull/6573) | hongxicheng | Bugfix | **恢复飞书/频道音频消息转录**——修复 AgentScope 2.0 迁移后 `AudioContent` 链路断裂导致的静默失败（对应 Issue #6544） |
| [#6592](https://github.com/agentscope-ai/QwenPaw/pull/6592) | jinliyl | Bugfix | **Scroll 上下文压缩前刷新 Auto-Memory**——解决早期会话轮次在每日记忆生成前被丢弃的问题（对应 Issue #6555） |
| [#6606](https://github.com/agentscope-ai/QwenPaw/pull/6606) | lalaliat | Bugfix | **`read_file` 支持数字字符串行范围**——提升工具参数兼容性 |

### 进展评估

- **稳定性修复**占主导，3 个合并 PR 全部指向用户感知较强的回归问题（音频无声、记忆丢失、工具参数校验）
- **架构收敛**持续推进：PR #6611 将 Scroll 上下文策略统一为唯一协议，与 AgentScope 生命周期对齐
- **多贡献者协同**：mohitdebian 独立提交了 3 个 PR（#6528、#6609、#6610），覆盖 JSON 损坏、spawn_subagent schema、Shell 超时三大问题，显示社区参与度提升

---

## 4. 社区热点

### 讨论最活跃 Issue

1. **[Issue #6537](https://github.com/agentscope-ai/QwenPaw/issues/6537)** — Skill tags 重启后消失（评论 10 条）  
   用户反馈技能标签通过 API 写入正常，但 manifest 重启 reconciliation 时丢失。属于 **#2.0.1 回归问题**（引用 #3270），影响技能管理核心流程，当前尚无 PR 跟进。

2. **[Issue #6520](https://github.com/agentscope-ai/QwenPaw/issues/6520)** — agent.json 系统性损坏（评论 3 条）  
   涉及 BOM 头、引号缺失、中文双重编码三类损坏，导致系统完全无法启动。已有 **PR #6528** 提交修复，待审查。

3. **[Issue #6608](https://github.com/agentscope-ai/QwenPaw/issues/6608)** — 长时 Shell 命令绕过超时阻塞飞书会话（评论 2 条）  
   某 dedup 脚本卡住飞书频道 **1.5 小时**，后续消息全部排队等待，是生产环境严重可用性事件。已有 **PR #6610** 修复。

4. **[Issue #6589](https://github.com/agentscope-ai/QwenPaw/issues/6589)** — 大量 Shell 输出导致 UI 冻结（评论 3 条）  
   与 #6608 同根，前端一次性渲染数万行 stdout 阻塞主线程。已有 **PR #6610** 一并修复。

### 讨论最活跃 PR

- **[PR #6302](https://github.com/agentscope-ai/QwenPaw/pull/6302)** — 统一 Provider 发现与模型路由（创建 7/21，最新更新 7/31）  
  历时 10 天的架构级重构 PR，涵盖 provider discovery、model metadata、routing 和 Console 模型管理，审查周期较长，预计将在下一版本落地。

- **[PR #6306](https://github.com/agentscope-ai/QwenPaw/pull/6306)** — 桌面侧边栏添加 Workspace 快捷入口（创建 7/21，最新更新 8/1）  
  解决桌面用户打开生成文件时需在文件管理器中手动定位 workspace 的痛点（Issue #6083），功能明确，待合并。

---

## 5. Bug 与稳定性

按严重程度排序：

| 级别 | Issue | 描述 | 状态 |
|---|---|---|---|
| 🔴 严重 | [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) | QwenPaw 2.0.1 与 agentscope 2.0.4.post1 不兼容，导致 proactive agent 崩溃 + 工具权限死锁 | 待修复，PR #6615 已提交 |
| 🔴 严重 | [#6520](https://github.com/agentscope-ai/QwenPaw/issues/6520) | agent.json 系统性损坏（BOM/引号/编码），系统完全无法启动 | Fix PR #6528 已提交 |
| 🟠 高 | [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) | Shell 命令超时绕过，长时间阻塞频道会话 | Fix PR #6610 已提交 |
| 🟠 高 | [#6589](https://github.com/agentscope-ai/QwenPaw/issues/6589) | 大量 Shell 输出导致 UI 完全冻结 | Fix PR #6610 已提交 |
| 🟡 中 | [#6537](https://github.com/agentscope-ai/QwenPaw/issues/6537) | Skill tags 重启丢失（2.0.1 回归） | 无 PR |
| 🟡 中 | [#6601](https://github.com/agentscope-ai/QwenPaw/issues/6601) | 模型空响应不报错，长会话静默失效 | 无 PR |
| 🟡 中 | [#6588](https://github.com/agentscope-ai/QwenPaw/issues/6588) | spawn_subagent 单任务模式因 schema 校验失败不可用 | Fix PR #6609 已提交 |
| 🟡 中 | [#6558](https://github.com/agentscope-ai/QwenPaw/issues/6558) | 多会话切换时消息丢失/漂移/重复渲染 | 已关闭，待验证 |
| 🟢 低 | [#6549](https://github.com/agentscope-ai/QwenPaw/issues/6549) | 桌面应用输入框在高 DPI 缩放后被遮挡 | 已关闭，待验证 |

**关键信号：** 5 个严重/高优先级 Bug 中 4 个已有 Fix PR，修复覆盖率达 80%，剩余 [#6601](https://github.com/agentscope-ai/QwenPaw/issues/6601)（空响应不报错）和 [#6537](https://github.com/agentscope-ai/QwenPaw/issues/6537)（Skill tags 回归）需关注。

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 优先级判断 |
|---|---|---|
| **全局快捷键快速输入窗口**（类豆包体验） | [PR #6607](https://github.com/agentscope-ai/QwenPaw/pull/6607) | 🟢 高——PR 已就绪，功能明确且与桌面端战略对齐 |
| **NVIDIA NIM Provider 原生支持** | [PR #6526](https://github.com/agentscope-ai/QwenPaw/pull/6526) | 🟢 高——利用现有 OpenAIProvider 架构，集成成本低 |
| **Workspace 侧边栏快捷入口** | [PR #6306](https://github.com/agentscope-ai/QwenPaw/pull/6306) | 🟡 中——实用型改进，待合并 |
| **结果呈现优化**（折叠思考过程、突出交付结果） | [Issue #6260](https://github.com/agentscope-ai/QwenPaw/issues/6260)（👍 1） | 🟡 中——用户痛点明确，但涉及 UI 重构，周期较长 |
| **Shell 大输出自动截断/流式读取** | [Issue #6512](https://github.com/agentscope-ai/QwenPaw/issues/6512) | 🟡 中——与 #6589/#6608 同属 Shell 工具改进，可能被纳入同一迭代 |
| **桌面应用名去掉 "Desktop" 后缀** | [Issue #6587](https://github.com/agentscope-ai/QwenPaw/issues/6587) | 🟢 低——纯命名调整，易实施 |
| **Provider 发现与模型路由统一** | [PR #6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) | 🟢 高——架构级改进，影响所有 Provider 集成 |
| **OneBot/QQ 消息格式优化**（清理 Markdown、支持本地媒体） | [PR #6543](https://github.com/agentscope-ai/QwenPaw/pull/6543) | 🟡 中——频道体验改进 |

**路线图判断：** 下一版本（预计 2.0.2）将重点吸收：NVIDIA NIM 支持、全局快捷键窗口、Provider 统一重构、以及当前积压的 Bug 修复。

---

## 7. 用户反馈摘要

### 核心痛点

1. **长上下文会话稳定性差**  
   Issue #6601 和 #6608 共同指向一个深层问题：长会话中模型空响应和 Shell 命令超时形成**级联故障**——模型不报错但无效输出累积，最终导致会话完全卡死。用户需要框架层对此类场景提供明确的错误反馈。

2. **UI 冻结影响用户体验**  
   Issue #6589（Shell 大量输出冻结）和 #6558（多会话切换数据丢失）反映桌面端前端状态管理存在缺陷，大量渲染和状态切换未做防抖/分批处理。

3. **配置损坏恢复困难**  
   Issue #6520 中用户遭遇 agent.json 系统性损坏（~20+ 字段），导致系统完全无法启动。这暴露了配置文件在 Windows 环境下的写入脆弱性（BOM、同步工具干扰）。

### 正面反馈

- Issue #6544 用户明确感谢音频转录修复（已关闭）
- Issue #6558 用户详细描述了多会话切换的三种数据完整性问题，说明对产品质量有较高期待
- Issue #6260 用户提出折叠式交互建议，获得 👍，反映用户对"结果优先"交互模式的偏好

### 使用场景画像

- **企业/飞书集成**：多个 Issue 涉及飞书频道（#6608、#6544、#6614），说明飞书是企业用户重要接入渠道
- **桌面端重度用户**：多会话切换、DPI 缩放、全局快捷键等反馈均来自桌面端
- **长会话工作负载**：股票分析、数据迁移、批量查询等场景频繁触发 Shell 输出和上下文压缩问题

---

## 8. 待处理积压

| 类型 | ID | 标题 | 创建时间 | 风险提示 |
|---|---|---|---|---|
| 🔴 Bug | [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) | 与 agentscope 2.0.4.post1 不兼容导致崩溃 | 2026-07-31 | PR #6615 待审查，阻塞 proactive agent 用户 |
| 🔴 Bug | [#6537](https://github.com/agentscope-ai/QwenPaw/issues/6537) | Skill tags 重启丢失（回归 #3270） | 2026-07-28 | 无 PR，10 条评论，技能用户关注度高 |
| 🟠 Bug | [#6601](https://github.com/agentscope-ai/QwenPaw/issues/6601) | 模型空响应不报错 | 2026-07-31 | 无 PR，长会话用户痛点 |
| 🟠 Bug | [#6614](https://github.com/agentscope-ai/QwenPaw/issues/6614) | 微信 cron 定时推送静默失败 | 2026-07-31 | 无 PR，已消耗 ~44M tokens |
| 🟡 PR | [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) | Provider 统一重构 | 2026-07-21 | 审查中 10 天，架构关键 PR |
| 🟡 PR | [#6203](https://github.com/agentscope-ai/QwenPaw/pull/6203) | Windows tasklist 超时修复 | 2026-07-16 | 审查中 16 天 |
| 🟡 PR | [#6543](https://github.com/agentscope-ai/QwenPaw/pull/6543) | OneBot 消息格式修复 | 2026-07-29 | 审查中 |
| 🟢 PR | [#

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 — 2026-08-01

## 1. 今日速览

ZeroClaw 今日保持高活跃度，过去24小时共产生 **50 条 Issue 更新**（活跃 45、关闭 5）和 **50 条 PR 更新**（待合并 41、已合并/关闭 9）。无新版本发布，但多个关键架构 RFC 处于密集讨论阶段，Hindsight 内存系统的 7 件套 PR 栈持续推进中，今日新增 5 个聚焦运行时安全与网关配置的高优先级修复 PR。整体项目健康度良好，技术债务清理与架构演进并行推进。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR（共 9 条）

具体合并内容在数据中未完整展示，但从开放 PR 流可推断近期推进方向：

| PR | 类型 | 说明 |
|----|------|------|
| [#9037](https://github.com/zeroclaw-labs/zeroclaw/issues/9037) | Bugfix | 修复流式助手文本中终端标记（如 `<eom>`）泄漏到对话历史的问题 |
| [#8918](https://github.com/zeroclaw-labs/zeroclaw/issues/8918) | Bugfix | 漏洞检测器中对 Slack Token 的脱敏处理 |
| [#9449](https://github.com/zeroclaw-labs/zeroclaw/issues/9449) | Bugfix | JSONL 日志迁移过程中保留有效行，修复 schema 迁移数据丢失问题 |

### 进行中的核心功能栈

**Hindsight 内存系统（7/7 PR 栈）** — `logical-and` 主导的内存架构重构：

- [#9063](https://github.com/zeroclaw-labs/zeroclaw/pull/9063) (1/7) — Hindsight 后端 + 配置 + 工厂
- [#9064](https://github.com/zeroclaw-labs/zeroclaw/pull/9064) (2/7) — 共享/系统内存层级与授权
- [#9065](https://github.com/zeroclaw-labs/zeroclaw/pull/9065) (3/7) — 召回/注入调优 + 召回类型过滤
- [#9067](https://github.com/zeroclaw-labs/zeroclaw/pull/9067) (5/7) — 基于 invalidate PATCH 的保留/遗忘
- [#9068](https://github.com/zeroclaw-labs/zeroclaw/pull/9068) (6/7) — 异步保留 + Telegram DM 流式截断
- [#9069](https://github.com/zeroclaw-labs/zeroclaw/pull/9069) (7/7) — Dashboard 按 Agent 统计内存后端

该项目已推进至最后阶段，预计近期可合并。

---

## 4. 社区热点

### 评论最活跃的 RFC/Issue

| Issue | 标题 | 评论数 | 热度分析 |
|-------|------|--------|----------|
| [#9048](https://github.com/zeroclaw-labs/zeroclaw/issues/9048) | RFC: 分离对话历史与 agent 策展的长期记忆 | 14 | **最活跃**。社区对内存生命周期分离有强烈共识，Runtime/Gateway/Channel 的 autosave 逻辑与 MemoryCategory 设计是当前讨论焦点 |
| [#9127](https://github.com/zeroclaw-labs/zeroclaw/issues/9127) | RFC: 抽象 KeySource trait — 按来源/部署形式分类主密钥材料 | 11 | 安全架构核心议题，93 个 `#[secret]` 标注字段的加密基础即将迎来关键抽象 |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | RFC: 高风险 shell 命令的逐执行确认层级 + 策略 | 10 | 用户迫切需要在"完全阻断"与"完全放行"之间存在中间态，Claude Code 模式的 allow/ask/deny 是明确参考目标 |
| [#8933](https://github.com/zeroclaw-labs/zeroclaw/issues/8933) | RFC: OTel 跨轮次对话关联 | 9 | 可观测性体验痛点，需要跨 turn 的 conversation.id 串联追踪 |
| [#9106](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) | RFC: A2A outbound client (A2ATool) | 8 | 多 Agent 协作的核心缺口，#3566 拆分 A2AServer 后，Outbound 是实现 agent-to-agent 主动调用的最后一环 |

### 热点趋势分析

- **内存架构** 是当前最大焦点：#9048（分离历史/记忆）、#6850（解耦生命周期/存储）、Hindsight 7件套 PR 三线并进，社区对记忆系统的抽象层次有较高期待
- **安全抽象化** 受到持续关注：#9127（KeySource）、#6971（安全 UX）、#6996（细粒度沙箱）形成安全子系统的完整 RFC 矩阵
- **可观测性工程化**：#8933 与 #7232 双 RFC 推进，说明项目正从"有日志"向"结构化可关联追踪"演进

---

## 5. Bug 与稳定性

| 严重度 | Issue/PR | 描述 | 状态 |
|--------|----------|------|------|
| P1 | [#6724](https://github.com/zeroclaw-labs/zeroclaw/issues/6724) | 启用但未配置凭证的 Signal/Voice Call channel 导致 supervisor 崩溃循环（~2秒/次） | ✅ **已关闭** |
| P1 | [#8973](https://github.com/zeroclaw-labs/zeroclaw/issues/8973) | Landlock 沙箱阻断 shell 工具访问 `/dev/null`，Fedora 上 shell 工具始终失败 | ✅ **已关闭** |
| P2 | [#9006](https://github.com/zeroclaw-labs/zeroclaw/issues/9006) | OpenRouter/jamba 模型的 `<eom>` 终止标记泄漏到对话文本 | 🔄 PR #9037 修复中 |
| P2 | — | Linq webhook 别名所有权未校验，可能导致消息路由到错误 Agent | 🔄 PR #9604 今日提出 |
| P2 | — | OpenAI Responses 客户端未遵守 runtime proxy 配置 | 🔄 PR #9606 今日提出 |

**今日新增修复 PR（5 个，均标记 high risk）：**

- [#9607](https://github.com/zeroclaw-labs/zeroclaw/pull/9607) — 将 codex_cli / claude_code / gemini_cli / opencode_cli 路由到配置的运行时沙箱
- [#9606](https://github.com/zeroclaw-labs/zeroclaw/pull/9606) — OpenAI Responses 非流式/流式客户端正确应用 proxy 配置
- [#9604](https://github.com/zeroclaw-labs/zeroclaw/pull/9604) — Linq webhook alias 所有权强制校验
- [#9605](https://github.com/zeroclaw-labs/zeroclaw/pull/9605) — Quickstart 中收集 webhook 必需配置（port + HMAC secret）
- [#9603](https://github.com/zeroclaw-labs/zeroclaw/pull/9603) — Ollama 开发模板迁移到 schema V3，修复 uri 字段映射

---

## 6. 功能请求与路线图信号

### 高概率纳入近期版本的功能

| 功能 | 来源 | 进展 | 预期 |
|------|------|------|------|
| **Hindsight 内存系统** | PR #9063-#9069（7件套） | 全部 open，最后 3 件已在 review 尾声 | 近期合并，将支持 per-agent 内存后端、共享/系统层级、recall 过滤 |
| **OpenAI 兼容 Chat Completions 端点** | #8550 + PR #8486 | open，可对接 Open WebUI / LobeChat / LangChain | 网关层重要扩展，兼容生态接入 |
| **Shell 命令确认分级** | #7155 RFC | RFC 讨论中，10 条评论 | allow/ask/deny 三层策略，对齐 Claude Code 体验 |
| **Skills 紧凑注入默认化** | PR #8313 | open，deprecate full mode | 节省 prompt 上下文，按需加载 skill 指令 |
| **Session TTL 清理** | PR #8139 | open | 防止僵尸会话无限增长，支持 `channels.session_ttl_hours` |
| **A2A Outbound Client** | #9106

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*