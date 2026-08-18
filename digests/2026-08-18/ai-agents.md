# OpenClaw 生态日报 2026-08-18

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-18 01:38 UTC

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
**日期：2026-08-18**

---

## 1. 今日速览

过去24小时 OpenClaw 项目保持高度活跃：Issues 更新 500 条（活跃 482，关闭 18），PR 更新 500 条（待合并 364，已合并/关闭 136）。无新版本发布，但维护者在稳定性修复方面投入显著，今日已合并多项关键 PR，涵盖 UI 错误恢复、插件注册时序、子代理交付可靠性等核心路径。整体项目健康度良好，社区参与度旺盛，多条目高评论 Issue 反映用户对 session 状态持久化、认证刷新和长文本截断等问题的持续关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的重要 PR（136 条已处理）：

| PR | 类型 | 摘要 | 影响 |
|---|---|---|---|
| [#125493](https://github.com/openclaw/openclaw/pull/125493) | fix | 保留新版 schema 兼容性错误提示 | 防止插件安装时静默降级兼容性错误 |
| [#125494](https://github.com/openclaw/openclaw/pull/125494) | fix | Slack 清理未完成的进度消息 | 避免模型决定不回复时残留伪活跃状态 |
| [#125317](https://github.com/openclaw/openclaw/pull/125317) | fix | `skills verify` 缺失技能统一报告 | 消除 ClawHub 内部路径泄露，提升 CLI 一致性 |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | feat | 安装策略警告审查 UI | 管理员可显式确认高风险插件安装，增强安全透明度 |

**关键进行中 PR：**
- [#125497](https://github.com/openclaw/openclaw/pull/125497) — 修复 result middleware 后消息投递丢失问题，涉及核心 agent 消息流
- [#124803](https://github.com/openclaw/openclaw/pull/124803) — 修复 Gateway 启动期间子代理 settle wake 过早触发导致的重复重试循环
- [#125286](https://github.com/openclaw/openclaw/pull/125286) — Windows Git 安装路径 Node runtime 漂移修复
- [#124709](https://github.com/openclaw/openclaw/pull/124709) — 多 Agent 场景下 channel 插件注册优先级修复

---

## 4. 社区热点

**评论 Top 5 Issues：**

1. [#77598](https://github.com/openclaw/openclaw/issues/77598) — **Track live dev agent behavior and trajectory**（23 评论，👍1）
   - Pash 的 24 小时 dev agent 行为观测追踪 Issue，纯观察性质，不干预。反映社区对 agent 行为可观测性的高度兴趣。

2. [#91009](https://github.com/openclaw/openclaw/issues/91009) — **Codex PreToolUse hook 导致 CPU 100%+ 并阻塞 Gateway RPC**（20 评论，👍2）⭐ P1
   - `openclaw-hooks` 进程在 Codex app-server tool call 时大量创建，导致 Gateway 卡死。用户期待原生 hook 机制的资源限制。

3. [#80319](https://github.com/openclaw/openclaw/issues/80319) — **QA tool-defaults 套件误判 Codex 原生工具与 OpenClaw 动态工具等价性**（18 评论，👍1）
   - 原始报告过度声称 Codex 丢弃工具调用，实际是 QA harness 架构问题。体现社区对测试可信度的关注。

4. [#68596](https://github.com/openclaw/openclaw/issues/68596) — **可配置流式 watchdog 超时阈值**（15 评论，👍8）
   - Kimi-K2.5、DeepSeek-R1 等长推理模型频繁触发 30s 超时警告，用户强烈诉求可配置阈值。

5. [#62505](https://github.com/openclaw/openclaw/issues/62505) — **Coding Agent 从不完成任务（2026.4.2 之前正常）**（15 评论，👍1）⭐ P1 回归
   - 明确回归报告， Agent 仅输出模糊状态更新并道歉，不执行实际工作。

---

## 5. Bug 与稳定性

**P0/P1 级严重问题（按严重程度）：**

| Issue | 类型 | 描述 | Fix PR |
|---|---|---|---|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | P1 ⭐ | Codex PreToolUse hook 创建 CPU 绑定进程，阻塞 Gateway RPC | 暂无 |
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | P0 | 文件型 provider cooldown 持久化，账单恢复后仍封锁用户数小时 | 暂无 |
| [#62505](https://github.com/openclaw/openclaw/issues/62505) | P1 回归 | Coding Agent 停止产出实际工作（2026.4.2 后回归） | 暂无 |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | P1 回归 | `google-vertex/gemini-3.1-pro-preview` 报 "Cannot convert undefined/null to object" | 暂无 |
| [#84516](https://github.com/openclaw/openclaw/issues/84516) | P1 | Codex app-server 长回复在 ~1000-1100 字符处静默截断（未 aborted） | 暂无 |
| [#83959](https://github.com/openclaw/openclaw/issues/83959) | P1 | Codex app-server 启动重试耗尽，replacement server 未就绪 | 暂无 |
| [#86215](https://github.com/openclaw/openclaw/issues/86215) | P1 | Codex OAuth refresh 失败后 Agent 卡死数小时，无清晰告警 | 暂无 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | P1 | 子进程（hooks/bash/codex）泄漏，僵尸积累导致运行时退化 | 暂无 |
| [#111857](https://github.com/openclaw/openclaw/issues/111857) | P1 | CLI budget 重新打开已压缩 JSONL branch，prompt 估算膨胀 | 暂无 |
| [#71689](https://github.com/openclaw/openclaw/issues/71689) | P1 | tasks registry SQLite 损坏导致 Gateway 启动循环失败 | 暂无 |

**已有关闭 Fix PR 的 Bug：**
- [#77930](https://github.com/openclaw/openclaw/issues/77930) — Discord 通道在 2026.5.4 不加载（Beta 回归）
- [#77733](https://github.com/openclaw/openclaw/issues/77733) — `/new` 和 `/reset` 不再触发 persona greeting（2026.5.3 回归）
- [#107814](https://github.com/openclaw/openclaw/issues/107814) — `gpt-5.3-codex-spark` 对必需工具调用发出空参数

---

## 6. 功能请求与路线图信号

| Issue | 诉求 | 路线图信号 |
|---|---|---|
| [#68596](https://github.com/openclaw/openclaw/issues/68596) | 可配置流式 watchdog 超时 | 👍8 高支持，长推理模型普及下的明确需求 |
| [#79902](https://github.com/openclaw/openclaw/issues/79902) | SQLite transcript/session seams | 直接关联 #78595（database-first runtime），高级消费者需求 |
| [#67413](https://github.com/openclaw/openclaw/issues/67413) | Per-agent dreaming 配置 | 👍5，解决 OOM 和缺乏 per-agent 控制的痛点 |
| [#66252](https://github.com/openclaw/openclaw/issues/66252) | Per-Agent TTS/STT 多语言覆盖 | 多语言场景明确需求 |
| [#81061](https://github.com/openclaw/openclaw/issues/81061) | `before_route_inbound_message` hook | 通道桥接/代理架构的架构级诉求 |
| [#63990](https://github.com/openclaw/openclaw/issues/63990) | 多索引 embedding + 模型感知 failover | 生产可靠性关键，避免混合向量空间 |
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | 多槽位内存架构 | 替换单一 `plugins.slots.memory`，支持并行 memory provider |
| [#56781](https://github.com/openclaw/openclaw/issues/56781) | Compaction/LCM fallback 模型链 | 当前单模型失败导致 session 无限增长 |

**近期 PR 映射的路线图方向：**
- [#125231](https://github.com/openclaw/openclaw/pull/125231) — UI 任务卡片重设计，反映 Control UI 体验优化持续推进
- [#125444](https://github.com/openclaw/openclaw/pull/125444) — Android  durable progress card，移动端体验对齐
- [#123356](https://github.com/openclaw/openclaw/pull/123356) — Composer 斜杠命令参数预填充，交互细节打磨

---

## 7. 用户反馈摘要

**核心痛点：**
1. **Session 状态与消息丢失**：多个高评论 Issue（#69208, #67777, #84516, #111857）聚焦子代理完成投递丢失、长回复截断、compaction 后 prompt 估算膨胀。用户抱怨"模型已完成但消息未送达"。
2. **认证/OAuth 卡死**：#86215（Codex OAuth refresh 失败后 Agent 卡死数小时）和 #70903（provider cooldown 文件持久化封锁用户）反映认证恢复机制不够健壮，缺乏清晰告警和自动旋转。
3. **回归频发**：#62505、#38327、#77930、#77733 等多个 P1 回归报告，用户反映"之前能用，更新后坏了"，对版本稳定性信任度下降。
4. **长推理模型支持不足**：#68596（watchdog 超时 30s 太短）和 #80319（QA 套件误判）反映 OpenClaw 对 DeepSeek-R1、Kimi-K2.5 等长 thinking 模型适配滞后。
5. **资源泄漏**：#91009（hook 

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-08-18 | 分析范围：12 个项目**

---

## 1. 生态全景

个人 AI 助手/自主智能体开源生态呈现**"核心项目稳健演进、垂直场景快速分化、安全与稳定性成为共识优先级"**的态势。OpenClaw 作为参照核心保持高活跃但回归问题频发，反映长推理模型适配与 Session 持久化仍是行业共性挑战；NanoClaw 与 IronClaw 分别代表通道抽象层与 DB 写入优化的技术纵深探索；ZeroClaw 在安全修复与架构 RFC 治理上最为激进，v0.9.0 安全基线明确。整体生态从"功能堆叠期"迈入"生产就绪打磨期"，维护者响应速度与技术债务清理节奏成为区分项目成熟度的关键指标。

---

## 2. 各项目活跃度对比

| 项目 | Issues | PRs | 新版本 | 健康度 | 核心动向 |
|------|--------|-----|--------|--------|----------|
| **OpenClaw** | 500（活跃 482） | 500（待合并 364） | 无 | 🟢 良好 | 稳定性修复集中，P1 回归问题累积 |
| **ZeroClaw** | 50（活跃 44） | 50（待合并 35） | 无 | 🟢 良好 | 安全修复密集，RFC 治理活跃 |
| **Hermes Agent** | 50（活跃 42） | 50（待合并 46） | v0.20.3 | 🟢 良好 | 安全审计加固，MCP 状态治理 |
| **IronClaw** | 29 | 45（待合并 ~29） | 1.3.0-rc.1 | 🟡 良好（rc 风险） | DB 写入优化 Epic，升级崩溃待修 |
| **NanoClaw** | 4 | 42（待合并 17） | 无 | 🟢 良好 | Channels 层重构，多通道架构落地 |
| **CoPaw** | 12 | 33（待合并 13） | 无 | 🟢 良好 | 执行稳定性加固，多端扩展 |
| **LobsterAI** | 7 | 21（待合并 3） | 无 | 🟢 良好 | 体验优化为主，MCP 兼容性滞后 |
| **NanoBot** | 2 | 15（待合并 10） | 无 | 🟢 良好 | 生产级稳定性，Telegram 轮询恢复 |
| **Moltis** | 3 | 9（待合并 3） | 无 | 🟢 良好 | 外部 Agent 生态扩展，MiniMax 接入 |
| **PicoClaw** | 3 | 4（待合并 1） | 无 | 🟡 良好（低量） | 稳定性修复集中落地 |
| **NullClaw** | 0 | 1 | 无 | 🔴 低活跃度 | 仅 Dependabot 维护，处于维护期 |
| **ZeptoClaw** | 0 | 0 | 无 | 🔴 无活动 | 停滞 |

---

## 3. OpenClaw 在生态中的定位

**优势：**
- **生态参照系**：Issues/PR 绝对数量最高（500 级），社区参与度与问题暴露密度形成正向反馈循环，测试套件覆盖最广（Codex 原生工具对比验证）。
- **多通道成熟度**：Slack、Discord、Telegram 等通道均有生产级适配，通道桥接能力领先。
- **长推理模型适配探索**：Kimi-K2.5、DeepSeek-R1 等模型的 watchdog 超时配置诉求推动项目向"思考型 agent"演进。

**技术路线差异：**
| 维度 | OpenClaw | 竞品差异化 |
|------|----------|-----------|
| 会话管理 | Session 持久化 + compaction（痛点：prompt 估算膨胀） | NanoClaw 引入 SessionDriver 抽象，IronClaw 推进 durable DB 写入优化 |
| 通道架构 | 硬编码优先级 + 插件注册（待修复 #124709） | NanoClaw 通用 hook 体系（inbound/post-delivery/membership） |
| 工具调用 | Codex pre-tool hook（P1 阻塞问题 #91009） | ZeroClaw 原子化 budget 扣减，Moltis 原生模型/effort 选择 |
| 安全模型 | 安装策略警告 UI（#120900） | ZeroClaw SSRF 白名单、凭据泄露修复密度最高 |

**社区规模：** OpenClaw 以 500+ 级 Issues/PRs 显著领先，NanoClaw（46）、ZeroClaw（50）、Hermes Agent（50）构成第二梯队，其余项目处于 10-20 级活跃区间。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **Session 状态持久化与恢复** | OpenClaw, NanoClaw, Hermes Agent, ZeroClaw | OpenClaw: session 丢失/compaction 膨胀；NanoClaw: SessionDriver 抽象；Hermes: MCP 会话状态治理；ZeroClaw: runtime-owned sessions RFC |
| **多通道/多模型路由** | OpenClaw, NanoClaw, LobsterAI, Moltis | OpenClaw: 多 Agent channel 优先级；NanoClaw: sessionMode 声明；LobsterAI: 非 SSE MCP 引擎不可用；Moltis: MiniMax Code ACP 接入 |
| **安全加固** | ZeroClaw（主导）, LobsterAI, Hermes Agent | ZeroClaw: SSRF 白名单、预算竞态、凭据泄露；LobsterAI: 日志脱敏；Hermes: Electron 协议缓存漏洞 |
| **长推理模型适配** | OpenClaw, Moltis | OpenClaw: watchdog 超时 30s 不兼容；Moltis: RPC 超时可配置 |
| **生产级稳定性** | NanoBot, IronClaw, PicoClaw | NanoBot: Telegram 轮询恢复；IronClaw: DB 写入压力优化 Epic；PicoClaw: Agent 工具重复失败卡死 |
| **可观测性与调试** | OpenClaw, NanoClaw | OpenClaw: dev agent 行为追踪 #77598；NanoClaw: task 日志丢失/回复被吞 #3301 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 多通道集成 + 长推理模型适配 | 通用个人助手，重视工具生态 | 插件注册时序敏感，Compaction 策略影响 prompt 预算 |
| **NanoClaw** | 多通道抽象层 + 运行时可插拔 | 需要自定义渠道的企业用户 | SessionDriver 抽象 + hook 体系，支持非 Docker 运行时 |
| **IronClaw** | DB 写入优化 + WASM 能力 | 高并发生产环境 | Tiered DB 写入压缩（预计减 85 行/turn），WASM 类型化契约 |
| **ZeroClaw** | 安全合规 + 架构 RFC 治理 | 安全敏感型部署 | RFC 治理流程成熟，原子化预算扣减，SSRF 白名单 |
| **Hermes Agent** | 桌面端 + MCP 会话治理 | 技术用户，重视本地部署 | Electron 安全修复优先，v0.20.3 稳定基线 |
| **LobsterAI** | 用户体验 + 国际化 | 中文用户，个人效率场景 | 非 SSE MCP 兼容滞后，Ollama 本地模型集成问题 |
| **NanoBot** | 生产稳定性 + CLI 现代化 | 企业级 Telegram 部署 | `proc_pidinfo` 统一进程标识，std-to-loguru 日志桥接 |
| **Moltis** | 外部 Agent 生态扩展 | 多 Agent 编排场景 | MiniMax Code ACP 原生支持，`/model` 端点分组管理 |
| **CoPaw** | 执行稳定性 + 多端扩展 | AgentScope 生态用户 | Provider 路由统一，PowerContext 记忆后端 |
| **PicoClaw** | 嵌入式/边缘场景 | Sipeed 硬件生态用户 | 微信多实例，Fly.io 无配置部署适配 |

---

## 6. 社区热度与成熟度分层

```
快速迭代层（功能扩张期）
├── OpenClaw      [500 PRs]      高活跃但回归频发，技术债累积
├── ZeroClaw      [50 PRs]       RFC 驱动，安全修复密集
└── NanoClaw      [42 PRs]       Channels 层重构，架构演进中

生产就绪打磨层（稳定性优先）
├── Hermes Agent  [50 PRs]       v0.20.3 稳定基线，安全审计
├── IronClaw      [45 PRs]       rc.1 升级崩溃风险，DB 优化 Epic
├── CoPaw         [33 PRs]       执行稳定性集中修复
└── NanoBot       [15 PRs]       商业化就绪信号清晰

垂直场景深耕层
├── Moltis        [9 PRs]        外部 Agent 生态扩展
├── LobsterAI     [21 PRs]       体验优化为主，MCP 兼容滞后
└── PicoClaw      [4 PRs]        嵌入式场景，稳定性修复落地

维护/停滞层
├── NullClaw      [1 PR]         仅 Dependabot 维护
└── ZeptoClaw     [0]            无活动
```

---

## 7. 值得关注的趋势信号

| 趋势 | 证据 | 开发者启示 |
|------|------|-----------|
| **长推理模型适配成为标配需求** | OpenClaw #68596（watchdog 超时）、Moltis #1127（RPC 超时） | 30s 固定超时策略需改为可配置，DeepSeek-R1/Kimi-K2.5 等模型需专项测试 |
| **安全修复从"事后补丁"转向"架构内置"** | ZeroClaw 今日 10+ 安全 PR，NanoClaw attachment XML 注入修复 | 预算原子化、SSRF 白名单、凭据 Header 化应成为默认设计 |
| **Session 持久化是跨项目共性痛点** | OpenClaw compaction 膨胀、NanoClaw SessionDriver、ZeroClaw RFC #9487 | 会话状态管理需独立抽象层，避免与通道/运行时强耦合 |
| **多通道抽象层进入架构竞争期** | NanoClaw hook 体系 vs OpenClaw 插件注册 vs ZeroClaw 统一附件 RFC | 通道适配框架的设计决策（声明式 vs 钩子式）将影响生态扩展成本 |
| **DB 写入优化成为生产级门槛** | IronClaw Tier 1/2/3 优化合并，预计减 85 行/turn | 高频场景下 DB 写入压力需系统性优化，CoalescingEventSink 模式值得借鉴 |
| **回归测试可信度受关注** | OpenClaw #80319（QA 套件误判）、#62505（Coding Agent 回归） | 测试 harness 架构需与产品解耦，避免"通过测试但功能失效"的虚假安全感 |
| **企业级部署需求显性化** | LobsterAI #1653（groupPolicy 覆盖）、#1662（非 SSE MCP） | 安全策略可预期性、协议兼容性是企业用户核心诉求 |

---

**结论：** 生态正处于从"功能验证"向"生产就绪"转型的关键期。OpenClaw 作为参照核心需加速回归修复与长推理适配；ZeroClaw 的安全治理模式与 NanoClaw 的通道抽象层设计可能成为下一阶段架构演进的参考范式；Moltis 的外部 Agent 生态扩展反映了多智能体协作的明确需求。开发者在选择框架时应关注 Session 管理的抽象程度、安全修复的主动性与长推理模型的实测兼容性。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 | 2026-08-18

## 1. 今日速览
过去24小时 NanoBot 保持高频活跃，共产生 2 条 Issue 更新与 15 条 PR 更新（10 待合并 / 5 已关闭），无新版本发布。今日开发重心明确聚焦于生产级稳定性加固（Telegram 轮询恢复、网关进程身份统一、后台日志 flush）与 WebUI/CLI 交互体验升级。5 项核心修复已合入主线，技术债清理节奏稳健，项目整体健康度良好，商业化就绪信号清晰。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
今日合入/关闭的 5 项 PR 显著推进了核心链路的可靠性与架构现代化：
- **[PR #5416](https://github.com/HKUDS/nanobot/pull/5416)** 替换了依赖 locale 的 macOS 进程启动时间获取方式，统一通过 `proc_pidinfo` 与网关租约进行身份校验，消除跨平台进程标识漂移。
- **[PR #5156](https://github.com/HKUDS/nanobot/pull/5156) & [PR #5301](https://github.com/HKUDS/nanobot/pull/5301)** 联合修复 Telegram 因网络抖动导致长轮询静默挂起的生产级故障，前者实现连接池自动重建，后者补充轻量存活检测与 stdlib-to-loguru 日志桥接。
- **[PR #5406](https://github.com/HKUDS/nanobot/pull/5406)** 正式合入原生 TypeScript 终端 UI，CLI 现代化重构迈出关键一步。
- **[PR #5410](https://github.com/HKUDS/nanobot/pull/5410)** 修复 `sustained-goal` 在模型正常文本回复后仍重复注入澄清指令的回归问题，完善了目标执行的预算边界控制。
项目整体已从“功能迭代期”迈入“生产就绪打磨期”，网关调度、消息桥接与目标执行三大核心模块均获得实质性

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报 | 2026-08-18

## 1. 今日速览
过去24小时项目保持高活跃态势，累计处理 Issues 50条（新开/活跃42，关闭8）与 PR 50条（待合并46，已合并/关闭4）。v0.20.3 稳定版于昨日交付，汇总约125个历史 PR。当前开发重心明显转向安全审计加固（EPIC #82591 系列）、桌面端/MCP 会话状态治理及多平台兼容性修复。社区贡献活跃，技术债务集中清理，项目整体健康度良好。

## 2. 版本发布
**v0.20.3 (v2026.8.16.2)** 已发布（[Release #66616](https://github.com/NousResearch/hermes-agent/releases)）
- **性质**：Patch 版本，面向 Docker 镜像、托管部署与全新安装提供稳定基线。
- **内容**：打包自 v0.20.2 以来合并的约 125 个 PR。
- **迁移注意**：无公开破坏性变更，下游消费者可直接升级。部分底层会话状态与 MCP 超时处理逻辑已更新，建议重启 Gateway 以加载最新运行态。

## 3. 项目进展
今日多条关键 PR 并行推进，项目整体迈入“安全加固+状态治理”阶段：
- `#85579` **[CLOSED]** 统一 NeMo Relay 操作名称，提升 API 模式分发可靠性。
- `#88833` 升级 `nanoid` 至 `3.3.18`，修复 Electron 高危协议缓存漏洞。
- `#80859

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-18

## 1. 今日速览

PicoClaw 昨日保持中高强度贡献节奏，24小时内共产生 7 条活动（3 Issues + 4 PRs）。项目今日**合并关闭 3 条 PR**，修复了 Agent 卡死、环境变量配置缺失、微信多实例等关键问题，整体健康度良好。无新版本发布，但积压的稳定性修复集中落地，为后续迭代扫清障碍。社区对 Agent 重复失败卡死问题的关注度较高， Issue #3311 已有修复 PR 合并。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并 / 已关闭 PR（3 条）

| PR | 作者 | 类型 | 说明 |
|----|------|------|------|
| [#3312](https://github.com/sipeed/picoclaw/issues/3312) | lucapette | Bug Fix | 修复 Agent 在工具重复失败时陷入无限循环的问题，提前终止 Turn 并返回错误提示 |
| [#271](https://github.com/sipeed/picoclaw/pull/271) | tbeaudouin05 | Bug Fix | 修复 `config.json` 缺失时环境变量未生效的问题，确保 Fly.io 等无配置文件部署场景可用 |
| [#2606](https://github.com/sipeed/picoclaw/pull/2606) | dsus4wang | Enhancement | 增强微信渠道多实例支持与配置管理，改善非法渠道名校验及错误处理 |

### 待合并 PR（1 条）

- [#3340](https://github.com/sipeed/picoclaw/pull/3340) — **fix(slack): 修复 Slack 媒体上传缺少 `FileSize` 参数导致 SDK 拒绝请求的问题**（`slack-go v0.23.1` 要求 `files.getUploadURLExternal` 接口预先提供文件长度）

> **整体推进评估**：今日 3 条修复 PR 均针对线上可用性问题，涵盖 Agent 稳定性、部署兼容性和渠道配置，项目向后端健壮性和多实例支持方向稳步推进。

---

## 4. 社区热点

| Issue / PR | 评论数 | 热度分析 |
|------------|--------|----------|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) — IRC 长消息支持 | 6 | 活跃度最高。用户提出 IRCv3 扩展下长消息（>512字节）应被聚合为单条消息处理，当前 PicoClaw 会将分片消息误判为多条独立消息，导致 LLM 理解断裂。需求合理，涉及 IRC 协议适配层改造，暂无 PR 跟进。 |
| [#3311](https://github.com/sipeed/picoclaw/issues/3311) — 工具重复失败卡死 | 2 | 已被 PR #3312 修复并关闭。用户反馈在 Telegram 场景下 Agent 因 `git` 命令凭证缺失而无限重试，`max_tool_iterations` 内无任何回复输出。修复方案：检测到连续相同错误时提前终止 Turn 并返回错误。 |
| [#3340](https://github.com/sipeed/picoclaw/pull/3340) — Slack 上传修复 | 0 | 新问题修复，尚待维护者审核。 |

---

## 5. Bug 与稳定性

按严重程度排列：

| 序号 | Issue | 状态 | 描述 | Fix PR |
|------|-------|------|------|--------|
| 🔴 高 | [#3311](https://github.com/sipeed/picoclaw/issues/3311) | ✅ 已关闭 | 工具持续同错误导致 Agent 卡死、用户无响应 | #3312（已合并） |
| 🟠 中高 | [#3339](https://github.com/sipeed/picoclaw/issues/3339) | 🆕 新开 | Google Antigravity 模型正常发现，但所有生成请求均返回 `429 RESOURCE_EXHAUSTED`，OAuth scopes 和认证均正常 | 暂无 |
| 🟡 中 | [#271](https://github.com/sipeed/picoclaw/pull/271) | ✅ 已关闭 | `config.json` 缺失时 env override 不生效，导致默认模型 credential 校验失败 | 已修复 |
| 🟡 中 | [#3340](https://github.com/sipeed/picoclaw/pull/3340) | ⏳ 待合并 | Slack 文件上传缺少 `FileSize` 导致 SDK 提前拒绝 | 待审核 |

---

## 6. 功能请求与路线图信号

- **[#3287](https://github.com/sipeed/picoclaw/issues/3287)** — IRC 长消息聚合支持（Feature）
  - 诉求明确，评论 6 条，社区认可度高
  - 涉及 IRC channel 适配层重构，短期内无 PR 跟进
  - **建议**：纳入下一版本路线图，可作为 IRC 渠道稳定性专项的一部分

- **[#2606](https://github.com/sipeed/picoclaw/pull/2606)** — 微信多实例增强（Enhancement，已合并）
  - 已落地，反映多实例配置是多渠道接入的长期需求

---

## 7. 用户反馈摘要

| 痛点 / 场景 | 来源 | 反馈方向 |
|-------------|------|----------|
| Agent 调用工具（如 `git`）失败时用户完全无感知，等待数分钟后才得到回复 | [#3311](https://github.com/sipeed/picoclaw/issues/3311) | ❌ 不满意：体验极差，线上 Telegram 生产问题 |
| Fly.io 等无配置文件部署场景下环境变量未生效，默认模型加载失败 | [#271](https://github.com/sipeed/picoclaw/pull/271) | ❌ 不满意：文档/默认行为不清晰，需依赖 env |
| IRC 长消息被拆分为多条后 LLM 理解断裂 | [#3287](https://github.com/sipeed/picoclaw/issues/3287) | ❌ 不满意：协议适配不完整 |
| Slack 文件上传在 `slack-go v0.23.1` 后不再兼容 | [#3340](https://github.com/sipeed/picoclaw/pull/3340) | ❌ 不满意：依赖升级后的兼容性回归 |
| 微信多实例支持增强后配置更灵活 | [#2606](https://github.com/sipeed/picoclaw/pull/2606) | ✅ 满意：需求被采纳并修复 |

---

## 8. 待处理积压

| Issue / PR | 状态 | 创建时间 | 风险 |
|------------|------|----------|------|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) — IRC 长消息支持 | 🟡 Open / Stale | 2026-07-22 | 超过 2 周无进展，需求明确但暂无贡献者认领 |
| [#3339](https://github.com/sipeed/picoclaw/issues/3339) — Google Antigravity 429 错误 | 🟠 Open / 新开 | 2026-08-17 | 刚提交，需确认是否为上游配额限制还是 PicoClaw 侧限流逻辑问题 |
| [#3340](https://github.com/sipeed/picoclaw/pull/3340) — Slack 上传修复 | ⏳ Open | 2026-08-17 | 修复已就绪，待维护者审核合并 |

> **维护者关注建议**：Issue #3287 作为功能增强长期未跟进，建议评估是否纳入下一个 feature 版本；Issue #3339 需优先排查 Antigravity 429 的根因（quota vs. 代码逻辑）。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：2026-08-18** | 数据周期：2026-08-17 ~ 2026-08-18

---

## 1. 今日速览

NanoClaw 今日保持高度活跃，过去24小时共产生 **42 条 PR**（25 条已合并/关闭，17 条待合并）和 **4 条 Issue** 更新。项目核心进展集中在 **channels 层重构**——gavrielc 主导的 Slack 频道适配模块（wave A/B）已全部合入，同时新增了 session-runtime driver 抽象层和多个扩展钩子（session-created、post-delivery、membership-event），为后续多通道集成奠定架构基础。社区贡献者 wakqasahmed 和 glifocat 也在并行修复任务路由和日志保留等关键 Bug。整体项目健康度良好，PR 合入率约 60%，无明显阻塞问题。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 作者 | 说明 |
|---|---|---|
| [#3310](https://github.com/nanocoai/nanoclaw/pull/3310) | gavrielc | 恢复在 upstream-main 合并中意外丢失的 `slack-formatting` skill，修复文档引用问题 |
| [#3309](https://github.com/nanocoai/nanoclaw/pull/3309) | gavrielc | **Slack 频道适配 Wave B**：完成 per-thread session 模式、默认值工厂和 onboarding 流程 |
| [#3305](https://github.com/nanocoai/nanoclaw/pull/3305) | gavrielc | **Slack 频道适配 Wave A**：引入共享 Slack Web API 客户端库和 canvas cluster 模块 |
| [#3304](https://github.com/nanocoai/nanoclaw/pull/3304) | gavrielc | 新增 `sessionMode` 声明机制，允许适配器声明 shared/per-thread 会话模式，替代硬编码 |
| [#3292](https://github.com/nanocoai/nanoclaw/pull/3292) | gavrielc | 添加 inbound-policy 注册钩子，统一拦截入站消息路径 |
| [#3293](https://github.com/nanocoai/nanoclaw/pull/3293) | gavrielc | 新增 session-created 钩子，支持新会话首次创建时的平台侧初始化 |
| [#3294](https://github.com/nanocoai/nanoclaw/pull/3294) | gavrielc | 新增 post-delivery 钩子，支持首次消息发送后的跟进逻辑（如 onboarding） |
| [#3295](https://github.com/nanocoai/nanoclaw/pull/3295) | gavrielc | 添加通用 membership-event 钩子，统一处理成员加入/退出事件 |
| [#3296](https://github.com/nanocoai/nanoclaw/pull/3296) | gavrielc | 新增 `extendTool` API，支持扩展 MCP 工具 schema 和描述而不修改源码 |
| [#3297](https://github.com/nanocoai/nanoclaw/pull/3297) | gavrielc | 为 setup wizard 添加 per-channel 前置步骤和 companion-skill 扩展点 |

### 整体推进评估

今日核心投入是 **channels 层架构重构**，以 Slack 为首个落地渠道，完成了一套完整的通道适配框架（hook 体系 + session 模式声明 + 入站/出站扩展点）。同时通过 [PR #3306](https://github.com/nanocoai/nanoclaw/pull/3306) 引入 `SessionDriver` 抽象层，解耦会话生命周期与 Docker 实现，为未来支持其他运行时奠定基础。项目架构正向**多通道可扩展**方向明显演进。

---

## 4. 社区热点

### 高关注度 Issues

**[#3301](https://github.com/nanocoai/nanoclaw/issues/3301)** — Tasks firing in chat sessions run one-door: logs dropped, replies eaten
- **作者**: glifocat | **状态**: OPEN | **创建**: 2026-08-17
- **热度分析**: 由核心贡献者 glifocat 提交，描述了 #2988（one-door task delivery, 2.1.48）引入的回归：task 在 chat session 中触发时导致日志丢失、回复被吞、series 未列出。这是近期重大架构变更带来的兼容性 Bug，影响现有用户工作流。

**[#3203](https://github.com/nanocoai/nanoclaw/issues/3203)** — codex provider emits undeclared `file` ProviderEvent
- **作者**: mshirel | **状态**: OPEN | **创建**: 2026-08-08
- **热度分析**: provider 分支的 codex 模块发出了未在类型声明中的 `file` 事件，导致 main 分支类型检查失败，且生成的图片被静默丢弃。涉及跨分支兼容性，需同步处理。

**[#3289](https://github.com/nanocoai/nanoclaw/issues/3289)** — Bound pending-message polling for accumulated backlogs
- **作者**: glifocat | **状态**: OPEN | **创建**: 2026-08-17
- **热度分析**: 积压消息轮询无限制加载，存在内存和性能隐患。对应 [PR #3291](https://github.com/nanocoai/nanoclaw/pull/3291) 正在修复。

### 高关注度 PR

**[#3311](https://github.com/nanocoai/nanoclaw/pull/3311)** — fix(agent-runner): route scheduled-task errors to the operator
- **作者**: wakqasahmed | **状态**: OPEN | **关联 Issue**: #3223
- **热度分析**: 修复定时任务错误路由问题——此前错误被写入 chat 消息但丢失 batch 路由字段，导致 operator 无法正确接收。直接修复了关键可靠性问题。

---

## 5. Bug 与稳定性

| 优先级 | Issue/PR | 描述 | Fix 状态 |
|---|---|---|---|
| 🔴 高 | [#3301](https://github.com/nanocoai/nanoclaw/issues/3301) | Task 在 chat session 中触发时日志丢失、回复被吞 | [PR #3303](https://github.com/nanocoai/nanoclaw/pull/3303) 已提交待合并 |
| 🔴 高 | [#3289](https://github.com/nanocoai/nanoclaw/issues/3289) | pending-message 轮询无上限，积压时内存风险 | [PR #3291](https://github.com/nanocoai/nanoclaw/pull/3291) 已提交待合并 |
| 🟡 中 | [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) | codex provider 发出未声明的 `file` 事件，类型检查失败 | 待修复 |
| 🟡 中 | [#3300](https://github.com/nanocoai/nanoclaw/pull/3300) | attachment type 字段未转义，可能导致 XML 注入 | PR 待合并 |
| 🟢 低 | [#1143](https://github.com/nanocoai/nanoclaw/issues/1143) | Skills 文档引用已删除的 `/data/env` 路径 | ✅ 已关闭 |
| 🟢 低 | [#3302](https://github.com/nanocoai/nanoclaw/pull/3302) | OneCLI gateway 默认绑定地址错误 | PR 待合并 |

---

## 6. 功能请求与路线图信号

### 已落地功能

- **本地 Web Chat 通道** [#3298](https://github.com/nanocoai/nanoclaw/pull/3298) — amit-shafnir 提交的 loopback-only 本地网页聊天适配器，扩展了可调试/轻量使用场景。
- **Codex Provider 升级** [#3299](https://github.com/nanocoai/nanoclaw/pull/3299) — 将 `@openai/codex` 从 0.138.0 升级至 0.146.0，规避 2026-08-31 GPT-5.4 从 Codex 退役的兼容性问题。

### 路线图信号

- **多通道扩展架构**：gavrielc 今日的集中提交（#3304/#3292/#3293/#3294/#3295/#3296/#3297/#3305/#3309）清晰地指向一个**通用通道适配框架**的构建——每新增一个平台（除 Slack 外），只需注册对应的 hook 和 session mode 即可接入，无需修改核心代码。
- **运行时可插拔**：[PR #3306](https://github.com/nanocoai/nanoclaw/pull/3306) 的 `SessionDriver` 抽象层表明项目正在向**支持多运行时**（Docker 以外）的方向演进。
- **下一版本预测**：当前待合并 PR 数量较多（17 条），且 channels 层重构较为完整，预计下一版本（2.1.49+）将包含 Slack 适配、driver 抽象、以及若干 Bug 修复。

---

## 7. 用户反馈摘要

| 痛点/场景 | 来源 | 详情 |
|---|---|---|
| **Task 日志丢失** | [#3301](https://github.com/nanocoai/nanoclaw/issues/3301) (glifocat) | 用户在 chat session 中使用 task 功能时，发现运行日志消失、回复被吞、series 不显示，严重影响调试和可观测性 |
| **Codex 图片静默丢失** | [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) (mshirel) | `/add-codex` 生成的图片不被消费，且类型检查报错，开发者体验差 |
| **Pending 消息积压风险** | [#3289](https://github.com/nanocoai/nanoclaw/issues/3289) (glifocat) | 消息积压时无限加载至 JS 内存，存在 OOM 风险，需生产环境关注 |
| **OneCLI 网络配置** | [#3302](https://github.com/nanocoai/nanoclaw/pull/3302) (wakqasahmed) | OneCLI gateway 默认绑定地址未正确传递，容器内 agent 无法访问 |
| **Attachment XML 注入** | [#3300](https://github.com/nanocoai/nanoclaw/pull/3300) (torbenstruever) | attachment type 未转义，存在潜在安全风险 |
| **文档过时** | [#1143](https://github.com/nanocoai/nanoclaw/issues/1143) | 社区报告 skill 文档引用已废弃路径 `/data/env`，新手跟随文档配置受阻（已修复） |

---

## 8. 待处理积压

| Issue/PR | 作者 | 创建时间 | 状态 | 提醒 |
|---|---|---|---|---|
| [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) | mshirel | 2026-08-08 | OPEN, 0 评论 | 已开放 10 天，codex provider 类型不匹配，需 core-team 关注 |
| [#3311](https://github.com/nanocoai/nanoclaw/pull/3311) | wakqasahmed | 2026-08-18 | OPEN, 待合并 | 定时任务错误路由修复，关联 #3223，优先级高 |
| [#3303](https://github.com/nanocoai/nanoclaw/pull/3303) | glifocat | 2026-08-17 | OPEN, 待合并 | 修复 task 日志丢失，对应 #3301，优先级高 |
| [#3291](https://github.com/nanocoai/nanoclaw/pull/3291) | glifocat | 2026-08-17 | OPEN, 待合并 | 修复 pending message 无界轮询，对应 #3289 |
| [#3299](https://github.com/nanocoai/nanoclaw/pull/3299) | chiptoe-svg | 2026-08-17 | OPEN, 待合并 | Codex SDK 升级，有明确截止日期（2026-08-31），建议优先合入 |

---

*报告生成时间：2026-08-18 | 数据来源：NanoClaw GitHub Repository*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目动态日报 — 2026-08-18

---

## 1. 今日速览

NullClaw 项目今日整体活跃度较低，过去 24 小时内无新开 Issue，无新版本发布。唯一的动态是一条由 Dependabot 自动发起的依赖升级 PR（#956），目前仍处于待合并状态。从数据来看，项目维护节奏趋于平稳，社区参与度不高，未见重大功能迭代或活跃讨论。

---

## 2. 版本发布

无新版本发布。上次更新为 Dependabot 维护的 Alpine 镜像版本升级。

---

## 3. 项目进展

**待合并 PR：[#956](https://github.com/NullClaw/nullclaw/pull/956)** — `ci(deps): bump alpine from 3.23 to 3.24`

- **类型**：CI / Docker 依赖升级
- **作者**：`dependabot[bot]`
- **创建时间**：2026-06-15 | **最近更新**：2026-08-17
- **状态**：OPEN（待合并），积压约 2 个月

该 PR 将 Docker 镜像中的 Alpine Linux 从 `3.23` 升级至 `3.24`，属于常规安全/稳定性维护，不涉及业务功能变更，也不会引入破坏性更新。目前仍在等待维护者合并，尚未发现阻碍合并的评论或冲突。

---

## 4. 社区热点

今日无活跃 Issue 或高评论 PR。项目社区讨论热度较低，未见用户反馈集中关注的痛点或功能诉求。

---

## 5. Bug 与稳定性

今日无新报告 Bug、崩溃或回归问题。

> **关注点**：PR #956 中 Alpine 镜像升级涉及的安全性补丁是否已在 CI 环境中验证通过，建议合并前确认 Docker 构建流程无兼容性问题。

---

## 6. 功能请求与路线图信号

今日无新功能请求或路线图相关讨论。

PR #956 属于自动依赖更新，不反映项目功能方向的信号。如需了解项目规划，建议关注 GitHub Discussions 或维护者发布的 Roadmap 相关 Issue。

---

## 7. 用户反馈摘要

今日无用户反馈。项目近期缺乏用户互动，建议维护者主动在社区渠道（如 Discord、论坛或 Issue 评论）收集使用体验，以保持与用户的沟通链路畅通。

---

## 8. 待处理积压

| 类型 | 内容 | 积压时长 | 链接 |
|------|------|---------|------|
| PR | #956 — Alpine 3.23 → 3.24 升级 | ~2 个月 | [#956](https://github.com/NullClaw/nullclaw/pull/956) |

**建议**：该 PR 由 Dependabot 自动生成，风险较低且有助于提升镜像安全性，建议维护者尽快审阅合并。若因 CI 环境问题暂无法通过，可在 PR 中添加注释说明阻塞原因，以便社区了解进展。

---

> **项目健康度评估**：🟡 低活跃度 — 无 Issue 活动，无版本发布，仅一条长期待合并的依赖升级 PR。项目当前处于维护期，无重大功能推进，建议关注后续是否有新版本计划或社区参与回升。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期：2026-08-18** | 数据来源：GitHub (nearai/ironclaw)

---

## 1. 今日速览

IronClaw 项目处于 **1.3.0-rc.1 发布后的高活跃期**，过去 24 小时内共产生 29 条 Issues 和 45 条 PR 更新，其中 16 条 PR 已合并或关闭，项目整体推进节奏较快。核心工作围绕 **DB 写入压力优化 Epic (#7591)** 展开，Tier 1/2/3 优化项集中落地；同时 **rc.1 上线后暴露了升级崩溃 (#7720)** 和 **libSQL 写通道饥饿 (#7714)** 两个严重问题，均已触发紧急修复 PR。前端通知体系重构 (#7688-#7691) 和 WASM 能力响应规范化也进入收尾阶段。项目健康度良好，但需关注 rc.1 的稳定性问题。

---

## 2. 版本发布

### 📦 ironclaw-v1.3.0-rc.1 (2026-08-17)

**安装方式：**
```sh
curl --proto '=https' --tlsv1.2 -LsSf https://github.com/nearai/ironclaw/releases/download/ironclaw-v1.3.0-rc.1/ironclaw-installer.sh | sh
```

**注意事项：**
- **⚠️ 已知升级崩溃问题**：从 1.2.x 升级到 1.3.0-rc.1 后，进程在 composition 阶段因 `unknown field 'activation_state'` 崩溃循环，HTTP/SSH 端口失效，所有已安装扩展不可用（#7720）。
- **修复 PR 已提交**：#7721 正在处理该兼容性问题，接受 1.2 的 `activation_state` 行字段。
- 建议 1.2.x 用户在 #7721 合并前暂缓升级至 rc.1。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 标题 | 贡献 | 推进内容 |
|---|---|---|---|
| [#7663](https://github.com/nearai/ironclaw/pull/7663) | fix(release): forward-port 1.2 fixes and thread repair | serrrfirat | 将 1.2 稳定性修复（Windows 文件系统、JSON 输出、curl healthcheck）前向移植至 main，并修复线程索引投影 |
| [#7598](https://github.com/nearai/ironclaw/pull/7598) | [Tier 2] Collapse capability invocation-state writes | serrrfirat | DB 写入优化：将 capability 调用状态写入合并到 gate/terminal 边缘，预计减少 40 行/turn（安全变体）或 60 行/turn（激进变体） |
| [#7594](https://github.com/nearai/ironclaw/pull/7594) | [Tier 1] Route loop milestone sink through CoalescingEventSink | serrrfirat | 将 milestone 写入路由至 CoalescingEventSink，预计减少 30 次池 checkout/turn |
| [#7605](https://github.com/nearai/ironclaw/pull/7605) | [Tier 3] Fold message lookup-index sibling rows | serrrfirat | 将消息查找索引的兄弟行折叠进消息行，减少 1-3 行完整 entries/消息 |
| [#7637](https://github.com/nearai/ironclaw/pull/7637) | Type the design-system component boundary | italic-jinxin | 为 design-system 组件添加显式 prop 类型，防止无效变体绕过 TypeScript 校验 |
| [#7647](https://github.com/nearai/ironclaw/pull/7647) | feat(automations): deterministic no-delivery outcome | serrrfirat | 为自动化运行添加确定性的无交付结果处理，支持 `[SILENT]` 类型契约 |
| [#7703](https://github.com/nearai/ironclaw/pull/7703) | feat(wasm): typed WIT tool response and bundled guest migration | henrypark133 | WASM 工具响应规范化：替换字符串错误通道为类型化契约，支持 guest 迁移 |

**整体推进评估**：今日合并/关闭的 PR 中，DB 写入压力优化 Epic 的 Tier 1/2/3 项集中落地，预计单 turn 写入行数可减少 **~85 行**（Tier 1: 30 + Tier 2: 40~60 + Tier 3: 11+14）。WASM 能力响应栈 (#7627) 完成第 3 个 PR 的合并。前端通知体系后端契约已就绪，等待前端集成。

---

## 4. 社区热点

### 🔥 高关注度 Issues / PRs

| 类型 | 编号 | 标题 | 评论 | 核心诉求 |
|---|---|---|---|---|
| Issue | [#7591](https://github.com/nearai/ironclaw/issues/7591) | Epic: reduce durable DB write pressure ~60% | 3 | 系统性降低 DB 写入压力，分 Tier 实施 |
| Issue | [#7720](https://github.com/nearai/ironclaw/issues/7720) | 1.3.0-rc.1 crash-loops on boot after 1.2.x upgrade | 0 | **紧急**：升级路径兼容性问题 |
| Issue | [#7714](https://github.com/nearai/ironclaw/issues/7714) | libSQL: single shared write connection starves resource-governor journal | 0 | **紧急**：单写连接导致级联失效 |
| PR | [#7717](https://github.com/nearai/ironclaw/pull/7717) | fix(resources): stop libSQL write-lane starvation | - | 修复 #7714 的级联失效问题 |
| PR | [#7721](https://github.com/nearai/ironclaw/pull/7721) | fix(extension-registry): accept 1.2 activation_state row field | - | 修复 #7720 的升级崩溃 |
| Issue | [#7704](https://github.com/nearai/ironclaw/issues/7704) | Daily ironclaw failure taxonomy — 2026-08-17 | 0 | 每日失败分类报告，追踪 clawbench 84 个非通过项 |
| Issue | [#7275](https://github.com/nearai/ironclaw/issues/7275) | Reborn: verify explicit persistent memory recall across conversations | 4 | 跨会话持久化记忆召回可靠性验证 |

**热点分析**：
- **DB 写入优化 Epic (#7591)** 是当前技术主线，多个 Tier 已合并，但衍生出 #7707（lease-fence 读取边界问题）和 #7705（shutdown flush 悬挂）等集成测试发现的问题。
- **rc.1 稳定性问题** 引发两个紧急 Issue，均已在同日提交修复 PR，响应速度快。
- **跨会话记忆召回 (#7275)** 是用户反馈的核心痛点，关联 Issue #7185，影响多会话场景下的用户体验。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 标题 | 状态 | 修复 PR |
|---|---|---|---|---|
| 🔴 **Critical** | [#7720](https://github.com/nearai/ironclaw/issues/7720) | 1.3.0-rc.1 crash-loops on boot after 1.2.x upgrade | OPEN | [#7721](https://github.com/nearai/ironclaw/pull/7721) ✅ 已提交 |
| 🔴 **Critical** | [#7714](https://github.com/nearai/ironclaw/issues/7714) | libSQL write-lane starvation cascading authority invalidation | OPEN | [#7717](https://github.com/nearai/ironclaw/pull/7717) ✅ 已提交 |
| 🟡 **Medium** | [#3762](https://github.com/nearai/ironclaw/issues/3762) | Editing AGENTS.md in web UI does not update system prompt | OPEN | 无 |
| 🟡 **Medium** | [#7681](https://github.com/nearai/ironclaw/issues/7681) | Slack unlinked-user connect message is public | OPEN | [#7682](https://github.com/nearai/ironclaw/pull/7682) ✅ 已提交 |
| 🟢 **Low** | [#7716](https://github.com/nearai/ironclaw/issues/7716) | MCP server flow missing bearer key auth and STDIO/HTTP transport | OPEN | 无 |
| 🟢 **Low** | [#7715](https://github.com/nearai/ironclaw/issues/7715) | Telegram connection flow lacks consent/selection between bot and personal account | OPEN | 无 |

**稳定性评估**：
- 两个 Critical 问题均有对应修复 PR，预计 1.3.0-rc.2 将包含修复。
- #3762（AGENTS.md 编辑不生效）为长期存在的 Medium 级别 Bug，自 2026-05-18 开放至今未修复，建议纳入 v1.4.0 计划。
- Slack 隐私问题 (#7681) 的修复 PR #7682 已提交，将 unlinked-user 提示改为私有的单点击连接链接。

---

## 6. 功能请求与路线图信号

| Issue | 标题 | 优先级 | 关联 PR | 纳入下一版本可能性 |
|---|---|---|---|---|
| [#7719](https://github.com/nearai/ironclaw/issues/7719) | Expose GitHub Projects v2 field manipulation in GitHub tool | P2 | - | 🟡 中等 - 用户需要更新 backlog priority 等字段 |
| [#7716](https://github.com/nearai/ironclaw/issues/7716) | MCP server flow missing bearer key auth and transport options | P2 | - | 🟡 中等 - 影响生产环境 MCP 集成 |
| [#7715](https://github.com/nearai/ironclaw/issues/7715) | Telegram connection flow lacks consent/selection | P2 | - | 🟡 中等 - UX 完善需求 |
| [#7718](https://github.com/nearai/ironclaw/pull/7718) | feat(google-docs): add semantic editing tools | - | 待合并 | ✅ 高 - PR 已提交，添加 4 个语义编辑能力 |
| [#7708](https://github.com/nearai/ironclaw/pull/7708) | feat(automations): add run-now across trigger domain | - | 待合并 | ✅ 高 - 自动化手动触发功能 |
| [#7694](https://github.com/nearai/ironclaw/pull/7694) | feat: add durable backend suggestions | - | 待合并 | ✅ 高 - 后端建议系统 |
| [#7693](https://github.com/nearai/ironclaw/pull/7693) | feat: add native structured output finalization | - | 待合并 | ✅ 高 - 结构化输出规范化 |

**路线图信号**：
- **v1.3.0** 预计包含：Google Docs 语义编辑 (#7718)、自动化 run-now (#7708)、结构化输出 (#7693)、持久化建议 (#7694)、通知体系重构 (#7688-#7691)。
- **v1.4.0** 可能纳入：GitHub Projects v2 字段操作、MCP 认证增强、Telegram 连接选择、AGENTS.md 编辑修复 (#3762)。

---

## 7. 用户反馈摘要

| 来源 | 反馈内容 | 情绪 | 场景 |
|---|---|---|---|
| [#7275](https://github.com/nearai/ironclaw/issues/7275) | 跨会话持久化记忆召回不可靠，明确建立的信息在后续会话中无法稳定回忆 | 😤 不满 | 多会话工作流 |
| [#3762](https://github.com/nearai/ironclaw/issues/3762) | Web UI 编辑 AGENTS.md 保存成功但系统提示词未更新，影响身份文件管理 | 😤 不满 | 自定义 agent 配置 |
| [#7681](https://github.com/nearai/ironclaw/issues/7681) | Slack 中未链接用户的连接提示公开可见，且需要手动多步操作 | 😤 不满 | 团队协作场景 |
| [#7716](https://github.com/nearai/ironclaw/issues/7716) | MCP 服务器添加流程缺少 bearer token 认证和 STDIO/HTTP 传输选项 | 😤 不满 | 生产环境集成 |
| [#7715](https://github.com/nearai/ironclaw/issues/7715) | Telegram 连接流程无法区分 bot 模式和个人账号 | 😕 困惑 | 消息渠道配置 |

**核心痛点提炼**：
1. **跨会话记忆可靠性**：用户期望 IronClaw 能稳定回忆之前会话中明确建立的信息，当前存在 gap。
2. **身份配置热更新**：AGENTS.md 等身份文件的编辑需要实时生效，而非仅保存文件。
3. **生产级集成能力**：MCP 认证、Telegram 渠道选择等生产环境常见需求尚未完善。
4. **隐私意识**：Slack 公开提示问题反映用户对团队协作场景中的隐私敏感度高。

---

## 8. 待处理积压

| Issue | 标题 | 创建时间 | 滞留时长 | 建议优先级 |
|---|---|---|---|---|
| [#3762](https://github.com/nearai/ironclaw/issues/3762) | Editing AGENTS.md in the web UI does not update system prompt | 2026-05-18 | **92 天** | 🔴 高 - 影响核心配置体验，建议纳入 v1.4.0 |
| [#7275](https://github.com/nearai/ironclaw/issues

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 📅 LobsterAI 项目动态日报 | 2026-08-18

---

## 1. 今日速览

LobsterAI 在过去24小时内保持较高活跃度，共处理 **21 条 PR**（18 条已合并/关闭，3 条待合并），显示社区贡献节奏稳定。**无新版本发布**。Issues 新增 7 条，多为长期未解决的 stale 问题与一个新项目合作提议。整体项目健康度良好，合并率高达 86%，主要聚焦于体验优化、安全加固与路由提供商扩展。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的 **18 条 PR** 覆盖以下关键方向：

### 🧩 运行时与路由扩展
| PR | 内容 |
|----|------|
| [#2506](https://github.com/netease-youdao/LobsterAI/pull/2506) | 新增 DeepSeek Harness (dsh) 运行时文档 |
| [#2505](https://github.com/netease-youdao/LobsterAI/pull/2505) | 新增 dsh 进程启动器 |
| [#2502](https://github.com/netease-youdao/LobsterAI/pull/2502) | dsh 引擎集成完成 |
| [#1663](https://github.com/netease-youdao/LobsterAI/pull/1663) | OpenClaw 升级至 v2026.4.12，修复插件 SDK 兼容问题 |

### 🛡️ 安全与稳定性
| PR | 内容 |
|----|------|
| [#1661](https://github.com/netease-youdao/LobsterAI/pull/1661) | 日志导出脱敏，修复 API Key / Bearer Token 明文泄露风险 |
| [#2503](https://github.com/netease-youdao/LobsterAI/pull/2503) | 为文本输入控件添加右键编辑菜单（Cut/Copy/Paste） |

### 🎨 用户体验
| PR | 内容 |
|----|------|
| [#1636](https://github.com/netease-youdao/LobsterAI/pull/1636) | 聊天窗口新增「滚动到底部」悬浮按钮 |
| [#1637](https://github.com/netease-youdao/LobsterAI/pull/1637) | AI 回复新增「重新生成」按钮 |
| [#1639](https://github.com/netease-youdao/LobsterAI/pull/1639) | 修复多处 tooltip 硬编码英文，完善 i18n 覆盖 |
| [#1640](https://github.com/netease-youdao/LobsterAI/pull/1640) | 工具执行结果区域增加一键复制按钮 |
| [#1641](https://github.com/netease-youdao/LobsterAI/pull/1641) | 统一所有弹窗支持 Esc 键关闭 |
| [#1660](https://github.com/netease-youdao/LobsterAI/pull/1660) | 非 main Agent 首页动态展示 Agent 名称与描述 |
| [#1667](https://github.com/netease-youdao/LobsterAI/pull/1667) | Qwen 控制台链接从灵积迁移至百炼 |
| [#1668](https://github.com/netease-youdao/LobsterAI/pull/1668) | 为每个 Agent 支持独立工作目录配置 |
| [#1669](https://github.com/netease-youdao/LobsterAI/pull/1669) | 修复设置页模型提供商"测试连接"按钮逻辑与自定义名称显示 |
| [#1675](https://github.com/netease-youdao/LobsterAI/pull/1675) | 会话列表按时间区间分组（今天/昨天/7天内/更早按月细分） |

> **整体评估**：今日合并以体验和国际化优化为主，OpenClaw 升级补齐了运行时能力，日志脱敏补丁体现了安全合规意识，项目持续向精细化方向演进。

---

## 4. 社区热点

### 🔥 Issue #2500 — VOKO 跨平台 Agent 通信合作提案
**链接**: [#2500](https://github.com/netease-youdao/LobsterAI/issues/2500)

VOKO 项目作者主动联系，提出将 VOKO 作为"AI Agent 跨平台通信层"与 LobsterAI 集成，已接入 OpenClaw、AstrBot 等框架。若合作达成，将显著增强 LobsterAI 在 A2A 标准化方向的生态影响力。目前评论区 1 条，待维护者回应。

### 📌 Issue #1653 / #1635 / #1662 — 长期 stale 问题持续活跃
| Issue | 核心问题 |
|-------|----------|
| [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) | `groupPolicy` 配置被自动覆盖为 `allowlist`，影响安全策略控制 |
| [#1635](https://github.com/netease-youdao/LobsterAI/issues/1635) | Ollama 本地模型（Qwen3/Gemma4）无法使用，CherryStudio 正常 |
| [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) | 非 SSE 传输方式的 MCP 引擎无法被发现和使用 |

---

## 5. Bug 与稳定性

| 级别 | Issue | 描述 | 状态 |
|------|-------|------|------|
| 🔴 高 | [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) | 非 SSE 模式 MCP 引擎完全不可用，阻断部分部署场景 | 无 Fix PR |
| 🔴 高 | [#1671](https://github.com/netease-youdao/LobsterAI/issues/1671) | MD 转 Word 中途报错 `sse response finish reason: full`，任务中断 | 无 Fix PR |
| 🟡 中 | [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) | groupPolicy 被周期性覆盖，策略配置失效 | 无 Fix PR |
| 🟡 中 | [#1635](https://github.com/netease-youdao/LobsterAI/issues/1635) | Ollama 本地模型调用失败，排查方向指向 LobsterAI 与 Ollama 的通信层 | 无 Fix PR |
| 🟢 低 | [#1643](https://github.com/netease-youdao/LobsterAI/issues/1643) | 定时任务保存时误报"还有内容未保存"（实际已保存） | 无 Fix PR |

---

## 6. 功能请求与路线图信号

| 来源 | 需求 | 与现有 PR 关联 |
|------|------|----------------|
| [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) | 基于 Markdown 的工作流，让 main agent 感知并调度其他 agent | PR #1660 已开始推进多 Agent 首页个性化，可作为工作流能力的感知层铺垫 |
| [#2500](https://github.com/netease-youdao/LobsterAI/issues/2500) | VOKO 跨平台 Agent 通信层集成，推动 A2A 标准化 | 新项目提案，若合并将扩展 LobsterAI 的 Agent 互通能力 |
| [#1668](https://github.com/netease-youdao/LobsterAI/pull/1668) | Agent 独立工作目录 | 已合并，体现对多 Agent 隔离场景的持续投入 |

---

## 7. 用户反馈摘要

- **痛点集中在 MCP 兼容性**：Issue #1635（Ollama 模型不可用）和 #1662（非 SSE MCP 不可用）均指向 LobsterAI 在本地模型与 MCP 协议适配层面的覆盖不足，用户反馈"其他工具可用但 LobsterAI 不行"，对比落差明显。
- **groupPolicy 覆盖问题引发安全焦虑**：#1653 中用户反映策略配置被自动覆写，直接影响安全管控，属于信任类问题。
- **体验优化获积极反馈**：今日合并的悬浮滚动按钮、重新生成、Esc 关闭弹窗、工具结果一键复制等功能，均针对日常高频操作痛点，预期将显著提升使用流畅度。
- **i18n 覆盖仍不完善**：#1639 的修复说明此前大量 tooltip 硬编码英文，中文用户交互体验存在断层。

---

## 8. 待处理积压

以下 Issue 标记为 **stale** 且长期未获响应，建议维护者优先关注：

| Issue | 创建时间 | 类型 | 建议优先级 |
|-------|----------|------|------------|
| [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) | 2026-04-13 | Bug（策略覆盖） | 🔴 高 |
| [#1635](https://github.com/netease-youdao/LobsterAI/issues/1635) | 2026-04-12 | Bug（Ollama 兼容） | 🔴 高 |
| [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) | 2026-04-14 | Bug（MCP 非 SSE） | 🔴 高 |
| [#1671](https://github.com/netease-youdao/LobsterAI/issues/1671) | 2026-04-14 | Bug（SSE 中断） | 🟡 中 |
| [#1643](https://github.com/netease-youdao/LobsterAI/issues/1643) | 2026-04-12 | Bug（误报保存） | 🟢 低 |

> ⚠️ 上述 5 个 Issue 均超过 **4 个月**未关闭，且均为功能性阻塞问题，建议在下一迭代中安排专项处理。

---

*报告生成时间：2026-08-18 | 数据来源：GitHub netease-youdao/LobsterAI*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-08-18

## 1. 今日速览

Moltis 在过去24小时内保持中高活跃度，共处理 **3 条 Issues**（1 活跃、2 已关闭）和 **9 条 PR**（3 待合并、6 已合并），反映出项目在功能扩展与代码质量维护两线并行推进。没有新版本发布，但累计关闭了多个长期存在的功能请求（如 rpc timeout 可配置、外部 agent 模型选择），同时修复了 gateway heartbeat 配置覆盖、cron 调度器忽略活跃时段等关键 Bug。整体项目健康度良好，技术债务清理节奏稳定。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 作者 | 内容摘要 |
|---|---|---|
| [#1204](https://github.com/moltis-org/moltis/pull/1204) | hetaoBackend | 新增 **MiniMax Code ACP** 外部 Agent 支持，注册到默认可执行文件检测与 Agent 注册表 |
| [#1130](https://github.com/moltis-org/moltis/pull/1130) | khimaros | 使 WebUI RPC 超时可在配置中调整，解决长会话场景下的超时问题（修复 #1127） |
| [#1125](https://github.com/moltis-org/moltis/pull/1125) | gptme-thomas | 为外部 Agent 提供原生的模型与 effort 选择功能，支持 `/model` 端点分组管理 |
| [#1103](https://github.com/moltis-org/moltis/pull/1103) | s-salamatov | 修复浏览器快照与 ref 查找路径，使其能高效穿透 Shadow DOM（替代方案 PR #1100） |
| [#1207](https://github.com/moltis-org/moltis/pull/1207) | dependabot | 批量更新依赖：wasmtime-wasi、cmov、quinn-proto、serde_with |
| [#1087](https://github.com/moltis-org/moltis/pull/1087) | dependabot | 升级 tar 依赖从 0.4.45 → 0.4.46 |

**整体推进评估：** 今日合并聚焦于**外部 Agent 生态扩展**（MiniMax、模型选择）、**可用性增强**（RPC 超时可配、浏览器 Shadow DOM 支持）和**依赖维护**，项目向更丰富的 Agent 支持和更稳定的运行时环境稳步前进。

---

## 4. 社区热点

### 活跃 Issue / PR

- **[Issue #1095](https://github.com/moltis-org/moltis/issues/1095)** — *Podman is not working via moltis*  
  作者 RokkuCode，2026-06-03 创建，2026-08-17 最后更新，2 条评论。  
  **分析：** Podman 容器运行时兼容性问题持续开放超过两个月，反映用户对非 Docker 环境的支持诉求。该 Issue 尚无修复进展，需维护者关注。

- **[Issue #1202](https://github.com/moltis-org/moltis/issues/1202)** — *Format CI gate is red on main*  
  已关闭（2026-08-17）。因 `store.rs` 和 `admin.rs` 两个文件超出 1500 行限制导致 CI 格式检查失败，根源 commit 为 `9b47001a`。  
  **分析：** CI 门禁回归被快速识别并修复，体现维护者对代码质量标准的重视。

- **[PR #1206](https://github.com/moltis-org/moltis/pull/1206)** — *Add managed Files library and Settings browser*  
  作者 penso，2026-08-17 创建，状态 OPEN。  
  **分析：** 新增持久化文件库与 Finder 风格设置浏览器，支持 authenticated 流式 API 及多种容器挂载方案（Docker/Podman/Apple Container），是用户文件管理能力的重要补充。

---

## 5. Bug 与稳定性

| 问题 | 严重程度 | 状态 | 备注 |
|---|---|---|---|
| [Issue #1095](https://github.com/moltis-org/moltis/issues/1095) Podman 不兼容 | 中 | OPEN | 长期未解决，涉及容器运行时适配 |
| [Issue #1202](https://github.com/moltis-org/moltis/issues/1202) CI Format 检查失败 | 低 | CLOSED | 已修复，原因为文件行数超限 |
| PR #1209 — heartbeat.update 配置覆盖全量而非补丁 | 高（潜在） | OPEN | 当前 PR 正在修复，将 `HeartbeatConfig` 反序列化行为改为 patch 语义 |
| PR #1208 — cron 调度器忽略 heartbeat active_hours | 高（潜在） | OPEN | 当前 PR 正在修复，`is_within_active_hours` 函数已实现但未被调用 |

**稳定性评估：** 两个高优先级 Bug（#1209、#1208）均有对应修复 PR 处于 OPEN 状态，预计近期可合入。Podman 兼容性 (#1095) 仍为未决问题。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 进展 |
|---|---|---|
| RPC 超时可配置 | [Issue #1127](https://github.com/moltis-org/moltis/issues/1127) | ✅ 已通过 [PR #1130](https://github.com/moltis-org/moltis/pull/1130) 关闭 |
| 外部 Agent 模型/effort 选择 | [PR #1125](https://github.com/moltis-org/moltis/pull/1125) | ✅ 已合并，支持 `/model` 端点分组管理 |
| MiniMax Code ACP Agent | [PR #1204](https://github.com/moltis-org/moltis/pull/1204) | ✅ 已合并，新增 `acp-minimax-code` 类型 |
| Files 库 + Settings 浏览器 | [PR #1206](https://github.com/moltis-org/moltis/pull/1206) | 🔄 OPEN，功能完整，待合并 |

**路线图信号：** 项目正持续扩展 **外部 Agent 生态**（MiniMax 接入、模型选择）和 **文件管理能力**（PR #1206），同时补强运行时稳定性（heartbeat、RPC 超时配置）。下一版本可能包含 Files 库功能和已修复的 heartbeat 行为。

---

## 7. 用户反馈摘要

- **Podman 支持诉求**（#1095）：使用 Podman 而非 Docker 的用户在容器运行时层面遇到兼容性问题，希望获得官方支持或明确的工作区说明。
- **RPC 超时限制**（#1127 → #1130）：长会话场景中默认 RPC 超时导致请求中断，用户需要可配置的超时参数以适应不同延迟环境。
- **heartbeat 配置语义**（#1187 → #1209）：`heartbeat.update` 过去会全量覆盖配置而非增量更新，导致未指定字段被重置为默认值，影响用户体验。
- **cron 调度器行为**（#1205 → #1208）：`active_hours` 配置项虽然存在且已文档化、测试覆盖，但实际从未生效，用户期望定时任务能遵守活跃时段限制。
- **浏览器 Shadow DOM**（#1100 → #1103）：部分 Web 页面的 Shadow DOM 结构导致快照和元素查找失效，影响自动化测试/抓取场景。

---

## 8. 待处理积压

| Issue / PR | 作者 | 创建时间 | 状态 | 关注建议 |
|---|---|---|---|---|
| [#1095](https://github.com/moltis-org/moltis/issues/1095) Podman 兼容性问题 | RokkuCode | 2026-06-03 | OPEN | ⚠️ 已开放 76 天，建议维护者优先评估或回复已知限制 |
| [#1209](https://github.com/moltis-org/moltis/pull/1209) heartbeat.patch 修复 | Lstarsky0 | 2026-08-17 | OPEN | 待合并，修复高优先级 Bug |
| [#1208](https://github.com/moltis-org/moltis/pull/1208) cron active_hours 修复 | Lstarsky0 | 2026-08-17 | OPEN | 待合并，修复高优先级 Bug |
| [#1206](https://github.com/moltis-org/moltis/pull/1206) Files 库 + Settings 浏览器 | penso | 2026-08-17 | OPEN | 功能完整，待合并审核 |

**维护者关注提示：** Issue #1095 是长期未响应的重要用户诉求，建议尽快给出明确回应。PR #1208 和 #1209 修复了影响核心行为的 Bug，建议优先审查合并。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 | 2026-08-18

## 1. 今日速览
过去 24 小时内 CoPaw 保持高频维护节奏，累计处理 Issues 12 条（新增/活跃 7、关闭 5）、PR 33 条（待合并 13、已合/关 20）。本期无新版本发布，整体健康度良好。开发重心明显向**执行稳定性**与**多端扩展能力**倾斜：工具调用崩溃、媒体链接过期、Token 计数异常等阻塞性问题集中修复，同时 Provider 路由统一、多项目目录绑定、PowerContext 记忆后端等架构级特性进入合入窗口。社区贡献活跃，技术债清偿速度高于新需求堆积速度。

## 2. 版本发布
本期无新版本发布。

## 3. 项目进展
**已合入/关闭的重要 PR（20 条）**
- **核心逻辑修复**

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-08-18

---

## 1. 今日速览

ZeroClaw 今日保持高度活跃：**50 条 Issue 更新**（44 活跃 / 6 关闭）、**50 条 PR 更新**（15 已合并/关闭、35 待合并），无新版本发布。社区围绕安全性修复与架构 RFC 同步推进：当日集中合并了 10 余个安全相关 PR，涵盖 SSRF、凭据泄露、并发预算竞态等高危问题；同时多个核心 RFC（Chat Completions profile、Goal mode v1、统一附件架构）持续讨论，v0.9.0 安全与网关架构里程碑稳步推进。项目整体健康度良好，维护者响应活跃，安全修复节奏紧凑。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展 — 今日合并/关闭的重要 PR

| PR | 作者 | 类型 | 说明 |
|----|------|------|------|
| [#9973](https://github.com/zeroclaw-labs/zeroclaw/pull/9973) | Audacity88 | fix(providers) | 修复 Gemini API Key 通过 URL 参数泄露问题，改用 `x-goog-api-key` Header |
| [#10000](https://github.com/zeroclaw-labs/zeroclaw/pull/10000) | Audacity88 | fix(channels) | 为 QQ（10 MiB）和 Mattermost（25 MiB）通道下载添加响应体大小限制 |
| [#9993](https://github.com/zeroclaw-labs/zeroclaw/pull/9993) | Audacity88 | fix(email) | 修复 Email 通道空 payload 隐式读取本地文件的问题 |
| [#9612](https://github.com/zeroclaw-labs/zeroclaw/pull/9612) | belumume | fix(channels) | 修复 WhatsApp Cloud 审批 token 在异常退出时泄漏为孤儿的问题 |
| [#9765](https://github.com/zeroclaw-labs/zeroclaw/pull/9765) | NiuBlibing | fix(sop) | 修复 SOP 定义从错误路径（data_dir 而非 workspace）加载的 bug |
| [#9544](https://github.com/zeroclaw-labs/zeroclaw/pull/9544) | vrurg | fix(delegate) | 修复 delegate 绕过配置的 provider fallback 列表、直接使用原始主 alias 的问题 |
| [#9996](https://github.com/zeroclaw-labs/zeroclaw/pull/9996) | Audacity88 | fix(security) | 将 action budget 扣减改为原子操作，修复并行调用下的竞态超刷 |
| [#10010](https://github.com/zeroclaw-labs/zeroclaw/pull/10010) | Audacity88 | test(cron) | 修复 cron 测试中因运行时代写可执行文件导致的 ETXTBSY 竞态 |
| [#9547](https://github.com/zeroclaw-labs/zeroclaw/pull/9547) | Audacity88 | chore(channels) | 将 CPAL 音频库从 0.15 升级至 0.18，迁移 Voice Wake API |
| [#9398](https://github.com/zeroclaw-labs/zeroclaw/pull/9398) | Audacity88 | ci(tests) | 新增 macOS/Windows 定时测试工作流，补齐跨平台覆盖 |

**整体推进评估**：今日合并以**安全修复为主轴**，针对凭据泄露、SSRF 间接风险、并发预算漏洞、文件路径混淆等高严重度问题集中出拳，v0.9.0 安全架构基础明显加固。同时 `delegate` 的 provider fallback 行为修复对多 provider 用户有实际价值。

---

## 4. 社区热点 — 高讨论 Issue / PR

| Issue | 作者 | 评论数 | 热度分析 |
|-------|------|--------|----------|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) — RFC: Work Lanes, Board Automation | Audacity88 | 23 | 工作流自动化与看板管理，影响维护者协作效率，已 Ratified 并在 rollout 中 |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — RFC: Chat Completions profile | REL-mame | 23 | 开放 AI 生态兼容接口，直接对接 Open WebUI / LobeChat / LangChain 等主流客户端，社区呼声最高 |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) — RFC: Goal mode v1 | vrurg | 22 | 有界目标模式，解决多轮 agent turn 的持久化目标追踪，设计复杂度高 |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — RFC: Shell 命令确认分级 | NiuBlibing | 20 | Claude Code 风格的 allow/ask/deny 策略，安全与可用性平衡的焦点 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — RFC: Runtime-owned conversation sessions | NiuBlibing | 19 | 会话所有权与传输适配器，架构级变更，需 maintainer review |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) — RFC: Unified attachment architecture | NiuBlibing | 18 | 统一附件架构，与 #9487 配套，影响所有 channel 的文件处理 |

**诉求分析**：社区核心关注点集中在 **① 生态兼容性**（Chat Completions 使 ZeroClaw 接入主流 AI 客户端栈）、**② 安全策略精细化**（shell 命令分级审批、预算原子化）、**③ 架构解耦**（会话所有权、附件统一化）。#6808 已进入 rollout，表明治理 RFC 流程运转正常。

---

## 5. Bug 与稳定性

| Issue / PR | 严重程度 | 描述 | 修复状态 |
|------------|----------|------|----------|
| [#10023](https://github.com/zeroclaw-labs/zeroclaw/issues/10023) | P2 / medium | Fallback provider 命中时，失败日志仍显示原始请求模型而非实际服务的 fallback 模型 | 🟡 开放，待修 |
| [#9849](https://github.com/zeroclaw-labs/zeroclaw/issues/9849) | P2 / high | `RateLimitedTool` 预算检查与记录非原子，并行调用可突破 `max_actions_per_hour` 限制 | ✅ 已由 PR #9996 修复并合并 |
| [#9594](https://github.com/zeroclaw-labs/zeroclaw/issues/9594) | P2 / high | Coding-agent 工具对 action budget 双重计费 | ✅ 已关闭 |

**稳定性评估**：今日重点修复的并发预算竞态（#9849 → #9996）为高危问题，修复后并行调用行为正确。日志模型名错误（#10023）为可观测性 bug，不影响功能但影响排障体验，建议优先跟进。

---

## 6. 功能请求与路线图信号

| PR / Issue | 类型 | 说明 | 纳入下一版本概率 |
|------------|------|------|------------------|
| [#10070](https://github.com/zeroclaw-labs/zeroclaw/pull/10070) | feat(tools) | `file_download` 增加 `allowed_private_hosts` 白名单，对抗 SSRF | 🔵 高（安全修复，已 rebased 待审） |
| [#9986](https://github.com/zeroclaw-labs/zeroclaw/pull/9986) | feat(agents) | 新增 `zeroclaw agents export` 将 agent 打包为可移植 bundle | 🟢 中（功能性强，需 maintainer review） |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | RFC | Chat Completions profile 支持 | 🟡 待定（架构 RFC，需进一步评审） |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | RFC | Goal mode v1 — 有界前台任务 | 🟡 待定（v0.9.0 目标模块） |
| [#10021](https://github.com/zeroclaw-labs/zeroclaw/pull/10021) | fix(runtime) | 将 target thinking policy 应用于独立 delegate | 🟢 中（bug 修复，待审） |

**路线图信号**：v0.9.0 安全架构（认证、网关、工具策略）为当前主线；`agents export` 与 `Chat Completions profile` 若 RFC 通过，可能进入 v0.9.x 或 v0.10.0。

---

## 7. 用户反馈摘要

| 来源 | 反馈内容 | 场景 |
|------|----------|------|
| [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) | WhatsApp `allowed_groups` 空列表默认允许全部群组，存在安全风险 | 频道配置安全 |
| [#10059](https://github.com/zeroclaw-labs/zeroclaw/issues/10059) | ZeroCode 编辑器不支持 macOS Option-Backspace 删除整词 | 编辑器体验 |
| [#9544](https://github.com/zeroclaw-labs/zeroclaw/issues/9544) + [#10003](https://github.com/zeroclaw-labs/zeroclaw/pull/10003) | Delegate 代理未正确使用配置的 provider fallback，导致路由行为与预期不符 | 多 provider 容错 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 需要 runtime 层面的会话所有权与传输适配器抽象 | 架构演进 |
| [#10023](https://github.com/zeroclaw-labs/zeroclaw/issues/10023) | 失败日志显示模型名错误，影响排障 | 可观测性 |

**用户痛点聚类**：安全配置默认值陷阱（#9397）、多 provider 路由可预期性（#9544/#10003）、编辑器快捷键习惯（#10059）为高频反馈。

---

## 8. 待处理积压

| 类型 | Issue / PR | 作者 | 状态 | 建议 |
|------|-----------|------|------|------|
| 🔴 高优 | [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) RFC: Runtime-owned conversation sessions | NiuBlibing | needs-maintainer-review | 架构 RFC，需维护者决策 |
| 🔴 高优 | [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) RFC: Unified attachment architecture | NiuBlibing | needs-author-action, needs-maintainer-review | 与 #9487 配套，需跟进 |
| 🟡 中优 | [#10070](https://github.com/zeroclaw-labs/zeroclaw/pull/10070) SSRF hardening for file_download | wangmiao0668000666 | needs-author-action | 安全修复，rebased 待审 |
| 🟡 中优 | [#10021](https://github.com/zeroclaw-labs/zeroclaw/pull/10021) Apply target thinking to delegates | vrurg | needs-maintainer-review | 行为修复待审 |
| 🟢 低优 | [#10023](https://github.com/zeroclaw-labs/zeroclaw/issues/10023) 失败日志模型名错误 | blockballr | status:in-progress | 可观测性小修 |
| 🟢 低优 | [#10059](https://github.com/zeroclaw-labs/zeroclaw/issues/10059) ZeroCode Option-Backspace 支持 | Audacity88 | good first issue | 新手友好 PR 机会 |

---

**日报生成时间**：2026-08-18  
**数据截止**：2026-08-17 24:00 UTC  
**分析模型**：Agnes-2.0-Flash（Sapiens AI）

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*