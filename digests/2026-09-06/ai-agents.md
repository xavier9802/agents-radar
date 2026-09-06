# OpenClaw 生态日报 2026-09-06

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-09-06 04:06 UTC

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



# OpenClaw 项目动态日报 — 2026-09-06

---

## 1. 今日速览

过去24小时 OpenClaw 社区保持极高活跃度：Issues 与 PR 均更新约500条，其中377条活跃/新开、123条关闭；PR 方面276条待合并、224条已合并/关闭，维护团队处理速度接近贡献速度。发布 v2026.9.2，核心聚焦聊天响应性能与 Gateway 事件循环去阻塞。高优先级（P0/P1）Issue 集中在 session-state 丢失、消息丢失和 Gateway 阻塞三大类，反映出项目在规模化部署中仍面临严重的运行时稳定性挑战。整体来看，项目处于**高吞吐迭代**阶段，但技术债积累明显。

---

## 2. 版本发布

### v2026.9.2 — 2026-09-06

**Highlights**
- **聊天响应性能优化：** 在长对话转录和磁盘处理期间，保持聊天、仪表盘和会话交互的响应性
- **直接仪表盘查找：** 减少冷启动时的工作量
- **持久化历史读取：** 将历史读取移出 Gateway 事件循环，避免阻塞主线程（#136862, #138...）

**破坏性变更：** 无已知破坏性变更
**迁移注意：** 无特殊迁移步骤

---

## 3. 项目进展

### 今日重要合并/关闭 PR

| PR | 状态 | 摘要 | 解决 Issue |
|----|------|------|------------|
| [#139394](https://github.com/openclaw/openclaw/pull/139394) | ✅ 合并 | 修复超时后排队消息丢失问题，5分钟 adoption timeout 后消息可恢复重试 | #139341 |
| [#139685](https://github.com/openclaw/openclaw/pull/139685) | ✅ 合并 | 修复 ACP 会话在完成时丢失缓冲输出、通道投递回调仍在运行时的消息丢失 | #139680 |
| [#139684](https://github.com/openclaw/openclaw/pull/139684) | ✅ 合并 | 重构 Android 定时任务间隔格式化代码复用 | — |
| [#139636](https://github.com/openclaw/openclaw/pull/139636) | ✅ 合并 | 重构认证模块，统一 onboarding 流程中的遗留选择解析 | — |
| [#139681](https://github.com/openclaw/openclaw/pull/139681) | ✅ 合并 | 优化模型目录查询性能，预排序模型桶，避免重复扫描抑制规则 | — |

### 关键进行中的 PR

- [#135599](https://github.com/openclaw/openclaw/pull/135599) — **无需重启 Gateway 即可管理/重载插件**（XL，待审），覆盖 CLI/RPC/UI/Agent 全路径
- [#137381](https://github.com/openclaw/openclaw/pull/137381) — **sessions_yield 保留长转录历史**（XL，待审），修复 SQLite 会话补全期间 transcript 不可用的问题
- [#139421](https://github.com/openclaw/openclaw/pull/139421) — **配对生命周期恢复**（XL，待审），解决 token 撤销后客户端仍保持授权的状态不一致
- [#139394](https://github.com/openclaw/openclaw/pull/139394) — 消息队列超时恢复（已合并）

**进展评估：** 今日合并侧重消息可靠性与内部重构，维护团队正在系统性清理技术债，插件热重载等架构级改进已进入最后审查阶段。

---

## 4. 社区热点

### 评论数最多的 Issue TOP 5

| Issue | 评级 | 评论 | 主题 | 链接 |
|-------|------|------|------|------|
| [#69208](https://github.com/openclaw/openclaw/issues/69208) | 🦪 silver | 14 | 跨通道重复转录/重放/上下文组装的 Umbrella Bug | [链接](https://github.com/openclaw/openclaw/issues/69208) |
| [#132762](https://github.com/openclaw/openclaw/issues/132762) | 🦞 diamond | 13 | overflow-retry 在工具结果后提前结束导致消息丢失 | [链接](https://github.com/openclaw/openclaw/issues/132762) |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | 🦪 silver | 12 | 长对话后 write/exec 工具参数静默丢失 | [链接](https://github.com/openclaw/openclaw/issues/53408) |
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | 🌊 tidepool | 12 | 内置无头浏览器需求，消除对外部 Chrome 依赖 | [链接](https://github.com/openclaw/openclaw/issues/53763) |
| [#39476](https://github.com/openclaw/openclaw/issues/39476) | 🦞 diamond | 12 | A2A sessions_send 双向调用导致消息重复 | [链接](https://github.com/openclaw/openclaw/issues/39476) |

**热点分析：**
- **session-state 与 message-loss 是当前社区最关注的两类问题**，多次出现在 top 列表中（#69208、#132762、#39476、#112259），说明多通道、多 agent 协作场景下的状态一致性是规模化部署的最大瓶颈
- **#53763（内置无头浏览器）** 获12条评论，反映用户对外部 Chrome 依赖链脆弱性的普遍焦虑
- **#53408（工具参数静默丢失）** 获2个 👍，是长对话场景下"无声杀手"型 bug，影响难以察觉但破坏性大

---

## 5. Bug 与稳定性

### P0 / Beta Blocker 级

| Issue | 摘要 | 状态 | Fix PR | 链接 |
|-------|------|------|--------|------|
| [#115642](https://github.com/openclaw/openclaw/issues/115642) | 计费冷却期在服务恢复后仍持续，缺少探活恢复机制 | 待决策 | — | [链接](https://github.com/openclaw/openclaw/issues/115642) |
| [#91931](https://github.com/openclaw/openclaw/issues/91931) | 预置 SOUL.md/IDENTITY.md 会在首次运行前删除用户 BOOTSTRAP.md | 待处理 | — | [链接](https://github.com/openclaw/openclaw/issues/91931) |
| [#124133](https://github.com/openclaw/openclaw/issues/124133) | openclaw-snowluma 频道 `formatInboundEnvelope is not a function`（2026.8.1-beta.2 回归） | 待复现 | — | [链接](https://github.com/openclaw/openclaw/issues/124133) |

### P1 级

| Issue | 摘要 | 状态 | Fix PR | 链接 |
|-------|------|------|--------|------|
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 子进程泄漏导致僵尸进程累积，运行时性能退化 | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/97616) |
| [#110190](https://github.com/openclaw/openclaw/issues/110190) | 运行时上下文载体置于用户消息之后导致模型推理混乱和 token 浪费 | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/110190) |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | 同步持久化阻塞 Gateway 事件循环 | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/119720) |
| [#136183](https://github.com/openclaw/openclaw/issues/136183) | SSH 命令执行 hang（SIGTERM），2026.8.1 回归 | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/136183) |
| [#112259](https://github.com/openclaw/openclaw/issues/112259) | 零有效载荷分派静默丢弃入站消息，无重试/死信 | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/112259) |
| [#132765](https://github.com/openclaw/openclaw/issues/132765) | `agents_wait` 忽略 timeoutSeconds，~60s 后崩溃 | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/132765) |
| [#127148](https://github.com/openclaw/openclaw/issues/127148) | Codex sessions.compact 获取第二个 app-server 触发 active-writer 冲突 | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/127148) |
| [#120162](https://github.com/openclaw/openclaw/issues/120162) | qualityGuard 审计重试共享 timeout 预算被 abort | 活跃 | — | [链接](https://github.com/openclaw/openclaw/issues/120162) |

### 有 Fix PR 的 Bug

| Issue | 摘要 | Fix PR |
|-------|------|--------|
| [#139341](https://github.com/openclaw/openclaw/issues/139341) | 超时后排队消息丢失 | [#139394](https://github.com/openclaw/openclaw/pull/139394) ✅ |
| [#139680](https://github.com/openclaw/openclaw/issues/139680) | ACP 输出丢失 | [#139685](https://github.com/openclaw/openclaw/pull/139685) ✅ |

**稳定性评估：** P1 级 Bug 密集且多数无 Fix PR，核心问题集中在 Gateway 事件循环阻塞、消息丢失和会话状态一致性。v2026.9.2 缓解了事件循环阻塞，但根治性问题（#119720、#112259）仍需架构级改动。

---

## 6. 功能请求与路线图信号

| Issue | 需求 | 优先级 | 路线图判断 |
|-------|------|--------|------------|
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | 内置无头 Chromium，摆脱对外部浏览器的依赖 | P3 | 用户呼声高，但需评估二进制体积；短期可能以插件形式出现 |
| [#6599](https://github.com/openclaw/openclaw/issues/6599) | `/models test-fallback` 命令，验证 fallback 链配置 | P3 | 低摩擦高价值，可能随诊断工具集一起纳入 |
| [#132781](https://github.com/openclaw/openclaw/issues/132781) | 无可 narration 时使用最新评论作为进度标签 | P3 | 小优化，符合渐进式改进方向 |
| [#85461](https://github.com/openclaw/openclaw/issues/85461) | 采集图像生成 provider 的用量/成本元数据 | P3 | 与计费透明化趋势一致，可能随成本追踪功能一起推进 |
| [#71452](https://github.com/openclaw/openclaw/issues/71452) | `list chat / list messages` 支持分页（当前硬编码25条） | P3 | 合理需求，但当前用户基数较小，优先级不高 |
| [#116716](https://github.com/openclaw/openclaw/issues/116716) | Context engine 可选严格失败策略 | P3 | 企业部署需求，与插件化架构方向一致 |

**路线图信号：** 社区需求向**可观测性**（fallback 测试、成本采集）、**可靠性**（内置浏览器、严格失败策略）和**体验打磨**（分页、进度标签）三个方向演进。插件热重载 PR [#135599] 如合并，将是运维体验的里程碑式改进。

---

## 7. 用户反馈摘要

**核心痛点：**

1. **消息静默丢失是最令人不安的问题** — #112259 描述的"入站消息被接受但零有效载荷丢弃、无重试无死信"让用户完全无法感知失败；#53408 的 write/exec 工具参数静默丢失同样属于"无声杀手"
2. **Gateway 事件循环阻塞直接影响可用性** — #119720、#99910（memory dreaming 占用10分钟）、#53008（compaction 阻塞10+分钟）反复出现，用户反映"bot 完全无响应"
3. **长对话质量退化** — #53408 在15+轮重工具使用后参数开始丢失；#110190 上下文载体位置导致模型推理混乱和 token 浪费
4. **TUI 滚动体验差** — #44130 获3个 👍（Issue 中最高），用户抱怨发送消息后视图剧烈跳动
5. **多 agent 协作的状态一致性** — #39476、#78055 反映子 agent 完成注入父会话、双向调用重复消息等问题
6. **飞书流式卡片延迟** — #91941 反映切换到全量文本更新后长回复延迟显著增加
7. **Claude CLI session limit 未触发 fallback** — #118793，limit 错误被当作致命错误而非 Failover 条件

**用户满意点：**
- v2026.9.2 的事件循环优化得到关注，用户长期受困于 Gateway 阻塞
- 插件热重载（#135599）若落地将大幅改善运维体验

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 评级 | 创建时间 | 距今 | 状态 | 风险 |
|-------|------|----------|------|------|------|
| [#69208](https://github.com/openclaw/openclaw/issues/69208) | 🦪 silver | 2026-04-20 | ~4.5月 | 活跃讨论中 | Umbrella Bug，跨通道转录/重放问题的根源 |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | 🦪 silver | 2026-03-24 | ~5.5月 | 活跃 | 长对话工具参数丢失，无 Fix PR |
| [#53008](https://github.com/openclaw/openclaw/issues/53008) | 🐚 platinum | 2026-03-23 | ~5.5月 | 活跃 | compaction 阻塞 Gateway 主处理通道10+分钟 |
| [#99910](https://github.com/openclaw/openclaw/issues/99910) | 🦞 diamond | 2026-07-04 | ~2月 | 活跃 | memory dreaming 占用 Gateway 事件循环10分钟 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 🦐 gold | 2026-06-29 | ~2.5月 | 活跃 | 子进程泄漏导致僵尸累积 |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | 🦞 diamond | 2026-08-05 | ~1月 | 活跃 | 同步持久化阻塞 Gateway 事件循环 |
| [#112259](https://github.com/openclaw/openclaw/issues/112259) | 🦪 silver | 2026-07-21 | ~2月 | 活跃 | 零有效载荷分

---

## 横向生态对比



# 个人 AI 助手开源生态横向对比分析报告
**日期：2026-09-06 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

个人 AI 助手开源生态目前呈现**"一超多强、分层演进"**的格局：OpenClaw 以最高活跃度引领技术方向，ZeroClaw 凭借 WASM 插件架构和安全治理机制快速追赶，Hermes Agent 和 CoPaw 分别占据桌面端和企业协作赛道，其余项目则在垂直渠道或轻量场景形成补充。生态整体处于**从功能实现向规模化生产部署过渡**的关键阶段，Gateway 事件循环阻塞、消息可靠性、沙箱安全边界成为跨项目的共性技术挑战，反映出现有异步运行时架构在复杂多通道场景下已接近性能瓶颈。

---

## 2. 各项目活跃度对比

| 项目 | 新增/活跃 Issues | 新增 PRs | 已合并/关闭 PR | Release | 健康度评估 |
|------|-----------------|----------|----------------|---------|-----------|
| **OpenClaw** | ~500（377活跃/新开） | ~500（276待合并/224已合并） | 224 | ✅ v2026.9.2 | ⚠️ 高吞吐但技术债累积，P1 Bug 密集 |
| **ZeroClaw** | 42 | 50 | ~10 | ✅ v0.8.5 | 🟢 高活跃，RFC 驱动架构演进 |
| **Hermes Agent** | 50 | 50 | 0 | — | 🟡 中高活跃，bug修复主导，无版本节奏 |
| **CoPaw** | 11 | 7 | 0 | — | 🟡 中高活跃，新功能+稳定性并行 |
| **NanoBot** | 1 | 25 | 7 | — | 🟢 活跃，issue-to-pr 响应快 |
| **PicoClaw** | 2 | 5 | 3 | — | 🟡 中等活跃，维护者驱动清理 |
| **ZeptoClaw** | 13（4已关闭） | 4 | 4 | — | 🟢 安全专项高响应，P0当日闭环 |
| **NanoClaw** | 0 | 3 | 0 | — | 🟡 低活跃维护，PR待合并周期长 |
| **IronClaw** | 1 | 1 | 0 | — | 🔴 低活跃，依赖阻塞，响应滞后 |
| **LobsterAI** | 0 | 2 | 0 | — | 🔴 低活跃，stale PR超5个月 |
| **NullClaw / Moltis** | 0 | 0 | 0 | — | ⚪ 无活动 |

**活跃度分层：**
- **第一梯队（高速迭代）**：OpenClaw、ZeroClaw
- **第二梯队（稳定贡献）**：Hermes Agent、CoPaw、NanoBot、ZeptoClaw
- **第三梯队（维护为主）**：PicoClaw、NanoClaw
- **第四梯队（低活/停滞）**：IronClaw、LobsterAI

---

## 3. OpenClaw 在生态中的定位

| 维度 | OpenClaw | 同类对比 |
|------|----------|----------|
| **社区规模** | 最大（单日500+事件） | ZeroClaw次之（92事件），其余项目10-50量级 |
| **技术路线** | Gateway事件循环 + 多通道统一接入 | ZeroClaw走WASM沙箱隔离；Hermes Agent偏桌面CLI；CoPaw企业协作 |
| **发布节奏** | 周级版本（v2026.9.2），修复为主 | ZeroClaw双周级；其余项目无固定节奏 |
| **核心优势** | 渠道覆盖最全（Telegram/Discord/Slack/飞书等）、插件生态最丰富 | NanoBot轻量；ZeptoClaw安全合规强；CoPaw团队协作 |
| **当前瓶颈** | Gateway阻塞、消息丢失、session-state一致性 | ZeroClaw架构迁移期；Hermes Agent更新机制不稳 |

**定位结论：** OpenClaw 是生态中的**"基础设施层"参考实现**，技术方向被多数项目参照或回避（如事件循环阻塞问题）。其高吞吐量迭代模式适合早期快速验证，但技术债已影响生产可靠性，需架构级重构。

---

## 4. 共同关注的技术方向

| 技术方向 | 涉及项目 | 具体诉求 | 成熟度判断 |
|----------|----------|----------|-----------|
| **Gateway/事件循环非阻塞化** | OpenClaw、NanoBot、Hermes Agent | 将持久化、memory dreaming、compaction 等I/O移出事件循环；#119720、#5580、#99910 | 🔴 行业痛点，多项目仍在攻克 |
| **消息可靠性与状态一致性** | OpenClaw、NanoBot、ZeroClaw | 消息静默丢失（#112259）、ACP输出丢失、bounded delegate工具被剥离 | 🔴 核心稳定性问题，规模化部署瓶颈 |
| **沙箱与权限边界** | ZeroClaw、ZeptoClaw、OpenClaw | macOS Seatbelt策略失效、子进程环境变量脱敏、agent_mode权限回退 | 🟡 ZeptoClaw响应最快，ZeroClaw架构领先 |
| **插件/工具热重载** | OpenClaw、CoPaw | 无需重启Gateway即可加载插件（#135599）、make-skill v2 | 🟢 OpenClaw PR已进入最后审查 |
| **可观测性与诊断** | OpenClaw、ZeroClaw、CoPaw | fallback链测试命令（#6599）、异常栈被吞（#7572）、成本采集元数据 | 🟡 需求明确，碎片化实现 |
| **MCP 工具集成** | CoPaw、NanoBot、ZeroClaw | 会话级MCP开关（#1070）、MCP超时可配置（#6874）、结构化结果保留 | 🟡 标准化进行中 |
| **多租户/团队协作** | CoPaw、ZeroClaw | Hub多租户版（#7318）、多用户访问+管理员技能管理 | 🟡 CoPaw 2.2.0目标；ZeroClaw RFC讨论中 |
| **双模型协作** | CoPaw、ZeroClaw | Advisor Mode（强模型规划+廉价模型执行）、单工具provider轮次 | 🟢 CoPaw PR已提交 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构关键差异 |
|------|----------|----------|------------------|
| **OpenClaw** | 全渠道网关 + 多agent协作 | 开发者/企业集成 | 统一Gateway事件循环，插件热重载，多通道transcription |
| **ZeroClaw** | WASM插件沙箱 + 安全治理 | 安全敏感场景 | 独立RFC治理流程、filesystem sandbox、ZeroRelay/ZeroRouter消息架构 |
| **Hermes Agent** | 桌面CLI + 技能索引 | 个人开发者 | launchd服务管理、GitHub Copilot集成、Skills索引机制 |
| **CoPaw** | 企业协作 + 会话管理 | 团队/企业用户 | QwenPaw Hub多租户、make-skill v2工作流、飞书卡片优化 |
| **NanoBot** | 轻量级agent + provider容错 | 个人用户/边缘部署 | runner超时failover、scoped runtime notifications、heartbeat成本优化 |
| **ZeptoClaw** | 安全合规Rust实现 | 合规敏感场景 | agent_mode权限回退修复、子进程环境脱敏、cargo-deny CI |
| **PicoClaw** | IRC渠道专用 | IRC社区用户 | IRCv3长消息支持、after-turn排队模式 |
| **NanoClaw** | Signal渠道专用 | Signal用户 | signal-cli依赖升级、临时目录清理 |
| **LobsterAI** | 企业cowork会话 | 网易有道内部 | CoworkSessionDetail组件拆分、per-session MCP开关 |
| **IronClaw** | 基准测试沙盒 | 评测/研究 | Pi sandbox loop默认启动、benchmark专用 |

**架构路线分化：**
- **网关中心化**：OpenClaw、Hermes Agent（统一Gateway接入多通道）
- **沙箱隔离优先**：ZeroClaw、ZeptoClaw（WASM/独立进程隔离）
- **渠道垂直深耕**：PicoClaw、NanoClaw（单一渠道深度优化）
- **企业协作导向**：CoPaw、LobsterAI（多租户、会话管理、权限管控）

---

## 6. 社区热度与成熟度

```
活跃度热力图（2026-09-06单日事件量）

OpenClaw      ████████████████████████████████████████  ~500
ZeroClaw      ███████████████████                      ~92
Hermes Agent  █████████████                            ~50
CoPaw         ██████                                   ~18
NanoBot       █████                                    ~26（含PR）
ZeptoClaw     ████                                     ~13
PicoClaw      ██                                       ~5
NanoClaw      ██                                       ~3
IronClaw      █                                        ~2
LobsterAI     █                                        ~2
NullClaw      —                                        0
Moltis        —                                        0
```

| 阶段 | 项目 | 特征 | 关键信号 |
|------|------|------|----------|
| **快速迭代期** | OpenClaw、ZeroClaw | 周级版本、RFC密集讨论、技术债与功能并行 | OpenClaw v2026.9.2缓解阻塞但P1密集；ZeroClaw v0.8.5后stabilization |
| **成长巩固期** | Hermes Agent、CoPaw、NanoBot、ZeptoClaw | 稳定贡献流、bug修复主导、新功能PR排队 | ZeptoClaw安全专项突出；CoPaw多租户路线图明确；NanoBot issue-to-pr响应快 |
| **维护稳定期** | PicoClaw、NanoClaw | 低频维护、积压清理、无版本节奏 | PicoClaw批量合并历史修复；NanoClaw PR待合并超1周 |
| **停滞观察期** | IronClaw、LobsterAI | 依赖阻塞、stale PR超5个月、无Issue响应 | 需维护者介入激活 |

---

## 7. 值得关注的趋势信号

### 7.1 架构层面：异步运行时瓶颈倒逼重构

**现象：** OpenClaw（#119720、#99910、#53008）、NanoBot（#5580）、Hermes Agent（compaction阻塞）均报告 Gateway 事件循环被同步I/O阻塞，导致 bot 无响应。

**趋势：** 下一代框架需将 I/O（持久化、compaction、memory dreaming）从事件循环彻底剥离，或采用 actor 模型/工作线程池隔离。ZeroClaw 的 WASM 隔离架构和 OpenClaw #135599 插件热重载可视为应对方向。

### 7.2 可靠性层面：消息丢失从"可接受风险"变为"生产红线"

**现象：** OpenClaw #112259（零有效载荷静默丢弃）、#53408（长对话参数丢失）；ZeroClaw #10534（delegate工具被静默剥离）；CoPaw #7572（异常栈被吞）。

**趋势：** 社区对"无声失败"的容忍度急剧下降。未来框架需在消息队列层提供：死信队列、重试预算、可观测性告警三件套，否则难以进入生产环境。

### 7.3 安全层面：从"功能安全"走向"合规安全"

**现象：** ZeptoClaw 单日关闭4个P0/P1安全问题；ZeroClaw #10536（macOS Seatbelt失效）；OpenClaw #136183（SSH hang回归）。

**趋势：** 企业采用 AI agent 的首要障碍从"能力不足"转向"安全不可审计"。子进程环境脱敏、agent_mode权限回退、审计链跨重启持久化（ZeptoClaw #669）将成为差异化竞争点。

### 7.4 成本层面：多模型分层与可观测性需求爆发

**现象：** CoPaw Advisor Mode（#7569）、NanoBot heartbeat低价模型（#4549/#4551）、OpenClaw成本采集（#85461）。

**趋势：** Agent 从单模型调用走向"规划模型+执行模型"分层架构。成本可观测性（每session/token/工具调用）将成为企业部署的标配需求。

### 7.5 协作层面：多租户与团队权限成为新战场

**现象：** CoPaw #7318（Hub多租户roadmap）、ZeroClaw #6808（Work Lanes已Ratified）、NanoBot spawn模式per-spawn模型预设（#5561）。

**趋势：** 个人 agent 向团队 agent 演进。session 归属、skill 版本管理、管理员权限模型将是下一阶段竞争焦点。

---

## 附录：对 AI 智能体开发者的建议

1. **避免 Gateway 事件循环阻塞陷阱**：参考 ZeroClaw 的 WASM 隔离和 NanoBot 的会话持久化异步化设计
2. **优先构建消息可靠性保障**：死信队列和重试预算应在架构设计阶段纳入，而非事后补救
3. **安全合规左移**：ZeptoClaw 的 P0 响应速度值得借鉴，安全审计应嵌入 CI/CD
4. **关注双模型协作架构**：CoPaw Advisor Mode 代表"高成本低延迟"的分层执行方向
5. **多租户设计提前规划**：即使当前为个人使用，session 归属和权限模型的设计应预留扩展接口

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目日报 — 2026-09-06

## 1. 今日速览

NanoBot 项目在 2026-09-06 保持活跃，过去24小时新增 1 个 Issue 和 25 个 PR，其中 7 个 PR 已合并/关闭，18 个待合并。社区贡献集中在 bug 修复、稳定性增强和功能迭代三个方向，无新版本发布。项目整体健康度良好，开发节奏稳定，重点修复了 provider 容错、会话持久化和安全边界等关键问题。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日已合并/关闭的 PR

| PR | 类型 | 摘要 |
|----|------|------|
| [#5670](https://github.com/HKUDS/nanobot/pull/5670) | refactor | 统一 scoped runtime notifications，迁移 context compaction 端到端流程 |
| [#5672](https://github.com/HKUDS/nanobot/pull/5672) | test | 移除废弃符号/字段的过时测试，保留关键回归检查 |
| [#5671](https://github.com/HKUDS/nanobot/pull/5671) | fix | WebUI dev 模式跳过 bundle 检查，避免虚假警告 |

**进展评估：** 今天合并不涉及新功能上线，而是聚焦于内部重构和测试清理。PR #5670 统一了事件通知架构，为后续功能开发打下基础；PR #5672 和 #5671 提升了开发体验和代码质量。整体来看，项目处于"修内功"阶段，稳步消除技术债务。

---

## 4. 社区热点

### 高关注 Issue / PR

| 编号 | 类型 | 主题 | 热度分析 |
|------|------|------|----------|
| [#5674](https://github.com/HKUDS/nanobot/issues/5674) | bug | Nvidia NIM provider 超时导致 agent 停摆 | 高 — 直接影响生产环境可用性，已触发关联 PR #5675 修复 |
| [#5675](https://github.com/HKUDS/nanobot/pull/5675) | fix | 允许 runner 超时后模型 failover | 高 — 直接修复 #5674，体现 issue-to-pr 快速响应机制 |
| [#5633](https://github.com/HKUDS/nanobot/pull/5633) | security | 拒绝含路径穿越的 session key | 高 — P1 安全修复，防止未授权文件访问 |
| [#5580](https://github.com/HKUDS/nanobot/pull/5580) | performance | 会话持久化移出事件循环 | 高 — 解决 event loop 阻塞导致的对话卡顿，P1 |

**社区诉求分析：**
- **可靠性优先：** #5674/#5675 反映用户对 provider 容错能力的需求，Nvidia NIM 等商业服务的不稳定性需要被优雅处理。
- **安全性关注：** #5633 的安全修复说明用户和贡献者对 session 注入攻击有清晰认知，安全边界正在被主动加固。
- **性能敏感：** #5580 暴露了异步架构中常见的 I/O 阻塞痛点，用户期望长会话不拖慢整体体验。

---

## 5. Bug 与稳定性

### 今日报告/修复的 Bug（按严重程度排序）

| 优先级 | Issue/PR | 描述 | 状态 |
|--------|----------|------|------|
| **P1** | [#5633](https://github.com/HKUDS/nanobot/pull/5633) | Session key 路径穿越漏洞（#5564） | 已有 fix PR |
| **P1** | [#5580](https://github.com/HKUDS/nanobot/pull/5580) | 会话持久化阻塞事件循环 | 已有 fix PR |
| **P1** | [#5589](https://github.com/HKUDS/nanobot/pull/5589) | 已丢弃会话意外复活 | 已有 fix PR |
| **P2** | [#5674](https://github.com/HKUDS/nanobot/issues/5674) | Nvidia NIM 超时导致 agent 停止工作 | 已有关联 fix PR #5675 |
| **P2** | [#5673](https://github.com/HKUDS/nanobot/pull/5673) | WebUI 远程项目路径支持 | 已有 fix PR |
| **P2** | [#5664](https://github.com/HKUDS/nanobot/pull/5664) | 空闲摘要缓存无界增长 | 已有 fix PR |
| **P2** | [#5630](https://github.com/HKUDS/nanobot/pull/5630) | Dream memory 文件无限增长 | 已有 fix PR |
| **P2** | [#5504](https://github.com/HKUDS/nanobot/pull/5504) | 模型重试状态未暴露给 UI | 已有 fix PR |
| **P2** | [#5457](https://github.com/HKUDS/nanobot/pull/5457) | 出站消息派发异常停止后台任务 | 已有 fix PR |

**稳定性评估：** 今天报告的核心问题均已有对应修复 PR，无未处理的紧急 Bug。缓存泄漏（#5664、#5630）和会话状态管理（#5589、#5471）是近期重点修复方向，反映项目正在系统性地解决成长过程中的资源管理问题。

---

## 6. 功能请求与路线图信号

| PR | 功能方向 | 状态 | 纳入可能性 |
|----|----------|------|------------|
| [#5676](https://github.com/HKUDS/nanobot/pull/5676) | CLI attach-only Desktop 目标选择 | Open | 高 — 完善多端部署体验 |
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) | Heartbeat 支持独立低价模型 | Open（长期） | 中 — 已在 review，需解决冲突 |
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) | Heartbeat 共享 session 配置 | Open（长期） | 中 — 同 #4549，设计方向一致 |
| [#5652](https://github.com/HKUDS/nanobot/pull/5652) | 签名直投 webhook | Open | 高 — 满足 CI/监控集成需求 |
| [#5561](https://github.com/HKUDS/nanobot/pull/5561) | Spawn 模式 per-spawn 模型预设 | Open | 高 — 解决 #4231 长期需求 |
| [#5386](https://github.com/HKUDS/nanobot/pull/5386) | MCP Apps 保留结构化结果 | Open | 中 — 增强 MCP 集成能力 |

**路线图信号：**
- **轻量化部署：** #5676 和 #5673 反映用户对 WebUI 远程访问和多端选择的持续需求。
- **成本优化：** #4549/#4551 的 heartbeat 功能说明用户关注长期运行的成本，希望用低价模型处理低频任务。
- **集成扩展：** #5652（webhook）和 #5386（MCP）表明项目在向 enterprise CI/CD 和工具生态靠拢。

---

## 7. 用户反馈摘要

### 真实痛点

1. **Provider 不稳定导致 agent 静默挂起**
   - 来源：#5674
   - 场景：使用 Nvidia NIM 时，300s/600s 超时被误判为模型输出，agent 停止响应
   - 用户情绪： frustrted — 无明确错误提示，排查困难

2. **会话数据无限增长**
   - 来源：#5664、#5630
   - 场景：废弃会话的摘要缓存、Dream memory 文件无上限膨胀
   - 用户情绪： concern — 长期运行后内存/磁盘压力

3. **WebUI 远程体验不佳**
   - 来源：#5673
   - 场景：远程用户无法正确使用项目选择器，可能触发本地文件 chooser
   - 用户情绪： inconvenience — 影响分布式部署场景

4. **事件循环阻塞**
   - 来源：#5580
   - 场景：慢存储或文件锁竞争导致整个 agent 卡死
   - 用户情绪： critical — 影响多会话并发体验

### 满意点
- 快速响应机制：#5674 在报告当天即有 fix PR #5675 跟进
- 安全修复透明：#5633 明确引用 CVE 类问题并给出完整修复方案

---

## 8. 待处理积压

| 编号 | 类型 | 创建时间 | 说明 | 建议 |
|------|------|----------|------|------|
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) | feature | 2026-06-26 | heartbeat 模型覆盖配置，已 open 3+ 月 | 需解决 conflict 后 review |
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) | feature | 2026-06-26 | heartbeat 共享 session，同 #4549 | 与 #4549 协同处理 |
| [#5561](https://github.com/HKUDS/nanobot/pull/5561) | feature | 2026-08-27 | spawn 模式模型预设，有 conflict 标记 | 需协调设计方向 |
| [#5386](https://github.com/HKUDS/nanobot/pull/5386) | feature | 2026-08-13 | MCP 结果元数据保留 | 长期 open，需确认优先级 |
| [#5471](https://github.com/HKUDS/nanobot/pull/5471) | bug | 2026-08-21 | ephemeral run 应不改变 session 状态 | open 两周，建议跟进 |

**维护者提醒：** 当前积压以功能型 PR 为主，多为 design conflict 或 review 周期长导致。建议优先处理 #5471（短周期 bug fix）和 #4549/#4551（用户呼声高的成本优化功能），以保持社区贡献者的参与热情。

---

**报告生成时间：** 2026-09-06  
**数据来源：** [HKUDS/nanobot](https://github.com/HKUDS/nanobot) GitHub API

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-09-06**

---

## 1. 今日速览

Hermes Agent 今日保持**高活跃度**，过去24小时内新增/更新 Issues 50条、PR 50条，社区参与度显著。整体以**bug修复与兼容性优化**为主导方向，涵盖桌面端会话同步、Windows 更新逻辑、GitHub Copilot 模型目录等关键组件。无新版本发布，但多个 P2 级问题已进入修复通道（#104032、#103582、#80583 等），项目健康度良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 合并，但有多个修复型 PR 推进中：

- **#103582** — 修复 launchd 管理的服务被错误报告为离线状态的问题，通过增加运行时指纹比对逻辑提升服务健康检查可靠性。
- **#104032** — 修正 keyless ring 请求路由逻辑，仅对已 pin 的 vendor 使用固定起始点，其余采用轮询分配，提升多 vendor 场景下的负载均衡。
- **#80583** — 修复 MCP OAuth 握手期间 `connect_timeout` 未正确传递的回归问题，避免超时回退到硬编码 60s 默认值。
- **#75679** — 统一内存提供商别名规范化，解决 `builtin`/`built-in`/`none` 在 doctor 和运行时不一致的问题。

项目整体向**稳定性加固**方向稳步推进，修复类 PR 占比高。

---

## 4. 社区热点

| Issue | 标题 | 评论数 | 热度分析 |
|-------|------|--------|----------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index is stale or degraded | 163 | 技能索引老化问题引发大量关注，社区对自动化刷新机制的可靠性存在普遍担忧 |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | Bot Group Chats should keep working after Desktop closes | 23 | 桌面关闭后群聊持续运行的需求强烈，涉及网关会话状态持久化 |
| [#23717](https://github.com/NousResearch/hermes-agent/issues/23717) | RFC: Pluggable SessionDB Provider | 20 | PostgreSQL/MySQL 支持 RFC 获 8 票支持，反映用户对生产级数据库后端的迫切需求 |

---

## 5. Bug 与稳定性

### P1 级
| Issue | 描述 | 状态 | Fix PR |
|-------|------|------|--------|
| [#98022](https://github.com/NousResearch/hermes-agent/issues/98022) | `hermes update` catch-up fleet restart 在 stale receipt 情况下无限循环 | Open | — |
| [#26058](https://github.com/NousResearch/hermes-agent/issues/26058) | `auto_thread` 在 `free_response_channels` 中被错误禁用 | Open | — |

### P2 级
| Issue | 描述 | 状态 | Fix PR |
|-------|------|------|--------|
| [#103900](https://github.com/NousResearch/hermes-agent/issues/103900) | 桌面端 pinned sessions 与原生 Hermes 不同步 | Open | — |
| [#90495](https://github.com/NousResearch/hermes-agent/issues/90495) | ZIP fallback 更新后丢失 Desktop 安装状态 | Open | — |
| [#97394](https://github.com/NousResearch/hermes-agent/issues/97394) | Windows 端更新 watchdog 无法感知日志增长导致误取消 | Open | — |
| [#91212](https://github.com/NousResearch/hermes-agent/issues/91212) | `~/.hermes/` 下出现 root 拥有文件（Debian） | Open | — |
| [#103989](https://github.com/NousResearch/hermes-agent/issues/103989) | OpenAI Codex OAuth credential 添加后未持久化 | Open | — |
| [#103978](https://github.com/NousResearch/hermes-agent/issues/103978) | Claude Code OAuth 自动发现导致 CLI 被登出 | Open | — |
| [#82912](https://github.com/NousResearch/hermes-agent/issues/82912) | Cron job `enabled_toolsets` 配置丢失 web 工具集 | Open | — |
| [#102193](https://github.com/NousResearch/hermes-agent/issues/102193) | 更新过程持续创建 root 拥有文件 | Open | — |

### P3 级
| Issue | 描述 | 状态 | Fix PR |
|-------|------|------|--------|
| [#104005](https://github.com/NousResearch/hermes-agent/issues/104005) | Holographic 实体提取正则产生垃圾实体 | Open | — |
| [#103985](https://github.com/NousResearch/hermes-agent/issues/103985) | Worktree lane 隐藏后在现有 worktree 下仍会重现 | Open | — |
| [#103893](https://github.com/NousResearch/hermes-agent/issues/103893) | 群聊 hold 指令错误分类德语填充词 | Open | — |
| [#79664](https://github.com/NousResearch/hermes-agent/issues/79664) | Vite config 使用 `configLoader: 'native'` 不支持的特性 | Open | — |

**今日已关闭：**
- [#45876](https://github.com/NousResearch/hermes-agent/issues/45876) — web_search 在 cron session 中回退 DDGS 超时问题（标记为已修复）
- [#104012](https://github.com/NousResearch/hermes-agent/issues/104012) — 撤回提交（AI 生成）

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求描述 | 相关 PR | 纳入可能性 |
|----------|----------|---------|------------|
| [#23717](https://github.com/NousResearch/hermes-agent/issues/23717) | 可插拔 SessionDB（PostgreSQL/MySQL） | — | **高**（8 👍，RFC 阶段） |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 桌面关闭后 Bot 群聊持续运行 | — | **高**（已有网关基础代码在 main） |
| [#103748](https://github.com/NousResearch/hermes-agent/issues/103748) | 向现有 live session 投递消息的官方方式 | — | **中**（多代理场景需求明确） |
| [#80994](https://github.com/NousResearch/hermes-agent/issues/80994) | Plan mode 只读探索阶段 | — | **中**（用户希望编辑前有审批环节） |
| [#44106](https://github.com/NousResearch/hermes-agent/issues/44106) | macOS LaunchAgent 生命周期管理 | [#104022](https://github.com/NousResearch/hermes-agent/pull/104022) | **高**（PR 已提交） |
| [#51953](https://github.com/NousResearch/hermes-agent/pull/51953) | 从实时目录解析 Claude reasoning effort | — | **中**（已提 PR，待 review） |
| [#54193](https://github.com/NousResearch/hermes-agent/pull/54193) | Mattermost @mention 后自动 follow thread | — | **中**（Slack parity 需求） |
| [#103965](https://github.com/NousResearch/hermes-agent/pull/103965) | 按任务路由子 agent 到不同 Hermes profile | — | **中**（多 persona 场景） |

---

## 7. 用户反馈摘要

**核心痛点：**

1. **更新机制不可靠** — 多个用户（[#98022](https://github.com/NousResearch/hermes-agent/issues/98022)、[#90495](https://github.com/NousResearch/hermes-agent/issues/90495)、[#102193](https://github.com/NousResearch/hermes-agent/issues/102193)）反映 `hermes update` 存在无限重启、状态丢失、权限文件污染等问题，影响日常使用体验。

2. **跨平台一致性不足** — 桌面端 pinned sessions 与 CLI 不同步（[#103900](https://github.com/NousResearch/hermes-agent/issues/103900)），Windows 更新日志监控逻辑异常（[#97394](https://github.com/NousResearch/hermes-agent/issues/97394)），平台间行为差异明显。

3. **OAuth/认证流程脆弱** — OpenAI Codex（[#103989](https://github.com/NousResearch/hermes-agent/issues/103989)）和 Claude Code（[#103978](https://github.com/NousResearch/hermes-agent/issues/103978)）的认证持久化存在缺陷，影响多 provider 用户。

4. **技能索引健康度** — #66616 引发的 163 条评论表明，自动化索引刷新机制的可靠性是社区高度关注的基础设施问题。

5. **包依赖过时** — #83673 和 #102563 指出项目依赖大量过时且存在安全风险的包，用户期待建立自动化更新机制。

---

## 8. 待处理积压

| Issue | 创建时间 | 优先级 | 建议关注 |
|-------|----------|--------|----------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 2026-07-18 | P3 | 技能索引刷新机制需系统性审查 |
| [#23717](https://github.com/NousResearch/hermes-agent/issues/23717) | 2026-05-11 | P2 | SessionDB 可插拔 RFC 推进中，需尽快确定技术选型 |
| [#43847](https://github.com/NousResearch/hermes-agent/issues/43847) | 2026-06-11 | P2 | Gateway 进程 kill 安全性加固，继 #43846 后的延续工作 |
| [#91212](https://github.com/NousResearch/hermes-agent/issues/91212) | 2026-08-21 | P2 | root 拥有文件问题需定位根因并修复权限设置逻辑 |
| [#82912](https://github.com/NousResearch/hermes-agent/issues/82912) | 2026-08-10 | P2 | Cron job 工具集丢失问题需补充回归测试 |

---

**报告生成时间：** 2026-09-06  
**数据来源：** NousResearch/hermes-agent GitHub Repository  
**分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期：2026-09-06 | 数据周期：过去24小时**

---

## 1. 今日速览

PicoClaw 今日保持中等活跃度，共处理 5 个代码贡献（3 个 PR 合并，2 个 Issue 处理）。项目维护者 xuwei-xy 集中清理了历史积压的修复 PR，显示了明确的技术债偿还意愿。功能请求层面，IRC 长消息支持和转向模式优化仍是社区关注焦点。整体项目健康度良好，代码质量在稳步提升，但新版本发布节奏平稳，暂无重大特性释放。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并的 3 个 PR 均为批量修复整合，由维护者 xuwei-xy 执行：

| PR | 内容 | 状态 |
|---|---|---|
| [#1559](https://github.com/sipeed/picoclaw/pull/1559) | 合并 #1327 #1319 #1318 #1313 的修复 | ✅ 已关闭 |
| [#1545](https://github.com/sipeed/picoclaw/pull/1545) | 合并 #1500 #1490 #1488 #1487 #1485 的修复 | ✅ 已关闭 |
| [#1555](https://github.com/sipeed/picoclaw/pull/1555) | 合并 #1390 #1389 #1383 #1381 的修复 | ✅ 已关闭 |

**推进方向：**
- 累计合并 13 个独立修复 PR，覆盖多个功能模块
- 显示维护团队在系统性清理历史积压 issue/PR，项目代码质量在持续优化

---

## 4. 社区热点

### 🔥 高讨论 Issue #3287 — IRC 长消息支持
**[Issue #3287](https://github.com/sipeed/picoclaw/issues/3287)** · 👍 0 · 💬 10 评论 · 创建于 2026-07-22 · 更新于 2026-09-05

- **核心诉求**：PicoClaw 应识别 IRCv3 扩展的长消息，将其视为单一连贯消息而非被 512 字节限制分割的碎片
- **背景**：IRC 协议默认限制 512 字节，新行会被客户端截断为多条消息。用户希望 AI 能理解这是同一条消息的连续内容
- **活跃度**：10 条评论表明社区对此有持续关注，距创建已 45 天仍为 OPEN 状态

### 📌 已关闭 Issue #3342 — After-turn 转向模式
**[Issue #3342](https://github.com/sipeed/picoclaw/issues/3342)** · 👍 0 · 💬 2 评论 · 创建于 2026-08-21 · 更新于 2026-09-05

- **核心诉求**：当 agent 正在处理任务时收到第二条消息，当前设计会跳过第一个任务的剩余工具调用并注入新消息。用户希望提供可选的"排队模式"，而非强制中断
- **状态**：已关闭（标记为 stale），可能因缺乏维护者响应或方案未达成一致

---

## 5. Bug 与稳定性

今日无新增 Bug 报告。

通过合并的 PR 间接修复的问题（来源 PR 描述未详细列出），需关注后续是否有回归反馈。

---

## 6. 功能请求与路线图信号

| 功能请求 | 来源 | 优先级信号 |
|---|---|---|
| IRCv3 长消息整合支持 | [Issue #3287](https://github.com/sipeed/picoclaw/issues/3287) | ⭐ 中 — 10 条评论表明社区需求明确 |
| After-turn 排队模式 | [Issue #3342](https://github.com/sipeed/picoclaw/issues/3342) | ⭐ 低 — 已关闭，但设计思路可参考 |

**路线图判断：**
- IRC 长消息支持具备纳入下一版本的潜力，建议在后续版本中评估 IRCv3 capabilities 的完整实现
- After-turn 模式虽已关闭，但多任务队列设计思路值得记录，可作为未来参考

---

## 7. 用户反馈摘要

### 痛点
1. **IRC 消息截断体验差**：用户反馈长消息被 512 字节限制分割后，AI 无法理解消息的连贯语义，导致对话质量下降
2. **任务中断不可控**：在多轮对话场景下，用户在 agent 处理期间发送的新消息会强制打断当前任务，缺乏"排队等待"选项

### 满意点
- 批量修复 PR 的合并效率较高，维护者主动清理历史积压

---

## 8. 待处理积压

| Issue | 状态 | 距今 | 建议 |
|---|---|---|---|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) | OPEN · 10 评论 | 45 天 | 高优先级跟进，IRC 长消息支持是明确的社区需求 |

**维护者关注建议：**
- Issue #3287 已有 45 天未获维护者回应，且评论数达 10 条，建议尽快给予反馈或标记为 planned
- 建议建立 IRCv3 扩展支持的专项 issue，整合相关讨论

---

**报告生成时间：** 2026-09-06  
**分析师：** Agnes-2.0-Flash (Sapiens AI)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# 📊 NanoClaw 项目动态日报
**日期：2026-09-06** | 仓库：[nanocoai/nanoclaw](https://github.com/nanocoai/nanoclaw)

---

## 1. 今日速览

过去 24 小时内，NanoClaw 项目整体处于**低活跃度维护状态**：无新版本发布，无新 Issue 报告，但 3 条 PR 均处于待合并阶段，显示贡献者在持续推动代码改进。项目健康度良好，无阻塞性 Bug 或回归问题上报。今天的 PR 集中在**依赖版本修复、测试基础设施优化和示例代码更新**，属于稳健的维护性推进，未涉及核心功能迭代。

---

## 2. 版本发布

暂无新版本发布。

---

## 3. 项目进展

今日有 **3 条 PR 待合并**，虽未直接合并，但均已完成审查流程，预计近期将进入主分支：

| PR | 类型 | 描述 |
|---|---|---|
| [#3725](https://github.com/nanocoai/nanoclaw/pull/3725) | 🐛 Bug 修复 | 修复 Linux `signal-cli` 安装版本过低导致的会话挂起问题 |
| [#3710](https://github.com/nanocoai/nanoclaw/pull/3710) | 🧪 测试改进 | 清理测试套件在 `/tmp` 遗留的约 355 个临时目录 |
| [#3724](https://github.com/nanocoai/nanoclaw/pull/3724) | 📝 文档/示例修复 | 更新 Anthropic 示例中已废弃的模型 ID |

**整体判断**：项目以维护性修复为主，未引入新功能，但对稳定性和开发体验有实质性改善。无破坏性变更风险。

---

## 4. 社区热点

今日无新 Issue 产生，以下 PR 具备较高社区关注度：

- **[PR #3725](https://github.com/nanocoai/nanoclaw/pull/3725)** — 涉及 Signal 渠道安装的核心依赖升级，直接影响 Linux 用户的消息发送稳定性，预计合并后影响面广。
- **[PR #3710](https://github.com/nanocoai/nanoclaw/pull/3710)** — 测试目录泄漏问题在 CI 环境下影响显著，长期运行的 Runner 用户对此有强烈诉求。
- **[PR #3724](https://github.com/nanocoai/nanoclaw/pull/3724)** — 示例代码中使用了已退役的 `claude-sonnet-4-20250514` 模型 ID，可能导致新用户按照文档操作时遇到 API 错误，修复具有及时性。

> ⚠️ 三者均暂无 👍 反应，可能处于刚创建或审查中阶段。

---

## 5. Bug 与稳定性

今日无新 Bug Issue 报告。以下问题已通过 PR 修复，待合并后生效：

| 问题 | 严重程度 | 状态 | 关联 PR |
|---|---|---|---|
| Signal-cli 0.14.3 发送消息至无会话联系人时永久挂起 | 🔴 高（影响核心功能） | 已修复，待合并 | [#3725](https://github.com/nanocoai/nanoclaw/pull/3725) |
| 测试后 `/tmp` 累积约 355 个目录，导致磁盘空间泄漏 | 🟡 中（影响开发/CI 环境） | 已修复，待合并 | [#3710](https://github.com/nanocoai/nanoclaw/pull/3710) |
| 示例代码引用已退役的 Anthropic 模型 ID | 🟢 低（影响使用体验） | 已修复，待合并 | [#3724](https://github.com/nanocoai/nanoclaw/pull/3724) |

**结论**：无未修复的高危 Bug，项目稳定性处于可控状态。

---

## 6. 功能请求与路线图信号

今日无新功能 Issue 或 PR，无明确路线图信号。

当前 PR 均属于维护性质，未体现新功能方向。如需关注后续功能动向，建议留意 Issues 板块的活跃度变化。

---

## 7. 用户反馈摘要

今日无新 Issue，无直接用户反馈。但从已有 PR 的摘要中可以推断出以下用户痛点：

- **Linux 用户**对 Signal 渠道的稳定性有较高期待，signal-cli 版本滞后直接影响消息发送成功率，升级至 0.14.7 是用户明确需求。
- **开发者和 CI 运维**关注测试环境的整洁性，`/tmp` 目录泄漏在持久化环境中积累效应明显，引发持续抱怨。
- **新手用户**依赖示例代码（如 `add-opencode` skill）进行快速上手，过时的模型 ID 会导致配置失败，影响第一印象。

---

## 8. 待处理积压

今日无新增长期未响应 Issue 或 PR。

> 💡 **提醒维护者**：3 条 PR 均已创建 1-3 天，目前均处于 `[OPEN]` 状态，建议及时完成 Code Review 并合并，避免贡献者等待周期过长影响积极性。

---

## 📈 项目健康度评分

| 维度 | 评分 | 说明 |
|---|---|---|
| 活跃度 | ⭐⭐☆☆☆ | 无新 Issue，PR 待合并 |
| 稳定性 | ⭐⭐⭐⭐☆ | 无新 Bug，已有修复待上线 |
| 响应速度 | ⭐⭐⭐☆☆ | PR 待 Review，无新 Issue 响应记录 |
| 社区参与 | ⭐⭐☆☆☆ | 无评论、无 👍，参与度偏低 |
| **综合健康度** | **⭐⭐⭐☆☆ (60/100)** | 维护状态良好，但需加速 PR 合并节奏以提升贡献者体验 |

---

*报告生成时间：2026-09-06 | 数据来源：NanoClaw GitHub API*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目日报 — 2026-09-06

---

## 1. 今日速览

IronClaw 今日活跃度处于**中等偏低**水平，24 小时内新增 1 条 Bug Issue 与 1 条 Feature PR，无任何 PR 合并或 Issue 关闭，版本发布停滞。项目当前处于功能迭代与稳定性修复并行的阶段，但贡献节奏有所放缓，需关注 Issue 响应效率与 PR 积压情况。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

**待合并 PR #8075** — 将嵌入式 Pi sandbox loop 设为启动默认行为（`[OPEN]`，`size: XL`，`risk: low`）

- **推进方向**：该 PR 是对基准测试场景（benchmark use）的显式优化，通过将 Pin Bun/Pi agent-core worker 固定到 sandbox 镜像并设为 `hosted-` 启动 profile 的默认值，为后续沙盒相关功能迭代奠定基础。
- **依赖关系**：堆叠于 #7908 之上，基础分支为 `feat/7903-native-loop-sandbox-spike`，需在基础 PR 合并后再行合入。
- **当前状态**：尚未合并，项目整体推进处于"等待上游依赖"的停滞状态，暂无实质性向前迈进。

> 🔗 [PR #8075](https://github.com/nearai/ironclaw/pull/8075)

---

## 4. 社区热点

| 类型 | 编号 | 标题 | 评论 | 👍 |
|------|------|------|------|-----|
| Issue | #8074 | Paired user 在未连接共享频道收到错误提示文案 | 1 | 0 |
| PR | #8075 | 使嵌入式 Pi sandbox loop 成为启动默认 | — | 0 |

**热点分析**：

Issue #8074 是当前社区讨论焦点，用户 `thisisjoshford` 报告了一个**体验一致性**问题——已配对用户在未连接的共享频道中执行操作时，收到的是为"未配对用户"设计的 `connect_required` 提示文案，而非针对当前场景的"频道未连接"说明。该问题虽不涉及功能崩溃，但直接影响用户使用流畅度与产品专业性，反映出项目在**多状态分支的用户提示覆盖**上存在遗漏。

> 🔗 [Issue #8074](https://github.com/nearai/ironclaw/issues/8074)

---

## 5. Bug 与稳定性

| 级别 | Issue | 描述 | Fix PR |
|------|-------|------|--------|
| 低（体验类） | [#8074](https://github.com/nearai/ironclaw/issues/8074) | Paired user 在 not-connected shared channel 中收到错误的 `connect_required` 文案，而非 channel-not-connected 提示 | 暂无 |

**评估**：今日无严重 Bug 或崩溃报告，无回归问题。现有 Issue 为 UI 文案匹配逻辑缺陷，影响面局限在特定交互路径，稳定性整体可控。

---

## 6. 功能请求与路线图信号

- **PR #8075** 明确回应了**基准测试场景**的需求，团队正在推进 sandbox 环境的默认启动配置优化。结合其依赖的 `feat/7903-native-loop-sandbox-spike` 分支，可推断下一版本将重点围绕**沙盒启动体验**与**基准测试支持**展开，预计 `hosted-*` 启动 profile 将成为默认行为。

---

## 7. 用户反馈摘要

**痛点**（Issue #8074）：
- 用户在配对（paired）状态下操作共享频道时，系统错误地以"未配对用户"的视角输出提示，造成认知混乱。
- 反映出产品在不同用户状态（paired / unpaired × connected / not-connected）下的分支文案覆盖不够完善。

**使用场景**：
- 共享频道（shared channel）协作场景中的配对用户体验是本次 Bug 暴露的盲区。

---

## 8. 待处理积压

| 类型 | 编号 | 创建时间 | 备注 |
|------|------|----------|------|
| Issue | [#8074](https://github.com/nearai/ironclaw/issues/8074) | 2026-09-04 | Bug 已提交超 48 小时，尚无 maintainer 响应或 Fix PR，建议优先分配 |
| PR | [#8075](https://github.com/nearai/ironclaw/pull/8075) | 2026-09-05 | 依赖 #7908，需跟进上游合并进度 |

**维护者提醒**：Issue #8074 属于用户体验类 Bug，修复成本低但影响产品口碑，建议尽快响应。同时需跟踪 PR #8075 的基础分支依赖状态，避免阻塞合入。

---

> 📊 **项目健康度评分**：⭐⭐☆☆☆（活跃度偏低，无版本产出，Issue/PR 响应滞后，但 Bug 规模可控）

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 📅 LobsterAI 项目动态日报（2026-09-06）

## 1. 今日速览
过去24小时 LobsterAI 保持低活跃度：无新 Issue，无版本发布，共更新 2 条 Pull Request（均为待合并状态）。代码库维护工作仍在推进，核心聚焦于 `CoworkSessionDetail` 组件重构与 MCP 细粒度控制拓展。整体开发节奏平缓，项目处于技术债清理与特性沉淀期，社区参与与审查响应速度有待提升。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
今日无 PR 合并或关闭记录。当前活跃 PR 共 2 条，均未直接推动版本迭代：
- [PR #1069](https://github.com/netease-youdao/LobsterAI/pull/1069)：拆分 `CoworkSessionDetail.tsx`（原 2100+ 行），提升可维护性与流式渲染性能。
- [PR #1070](https://github.com/netease-youdao/LobsterAI/pull/1070)：为 OpenClaw 引擎新增会话级 MCP 开关控制，支持独立启用/禁用并持久化至 DB。
项目整体仍停留在特性准备阶段，未出现实质性版本推进。

## 4. 社区热点
今日无新增高热度讨论。现有关注点集中于两条长期悬挂的 PR：
- [#1069](https://github.com/netease-youdao/LobsterAI/pull/1069) 反映团队对核心会话组件性能瓶颈与架构臃肿的长期关注。
- [#1070](https://github.com/netease-youdao/LobsterAI/pull/1070) 直击多会话并行场景下的工具链隔离需求，业务价值明确，但尚未进入合并评估流程。

## 5. Bug 与稳定性
过去24小时内无 Bug 报告、崩溃反馈或回归问题记录。项目未出现新的稳定性波动。

## 6. 功能请求与路线图信号
[PR #1070](https://github.com/netease-youdao/LobsterAI/pull/1070) 明确释放「会话级 MCP 权限管控」信号，暗示产品路线图正朝细粒度 Agent 能力演进。若该 PR 合并，预计将纳入 Cowork 模块下一阶段发布，支撑多场景工具独立配置与状态隔离。

## 7. 用户反馈摘要
今日无新增 Issue 及评论数据。从既有 PR 摘要可间接推断：开发者对「单文件职责过重导致的渲染性能损耗」与「MCP 全局开关缺乏灵活性」存在持续痛点。当前重构与特性 PR 是对上述场景的主动响应，但尚未转化为公开的用户讨论或 Issue 沉淀。

## 8. 待处理积压
⚠️ **需维护者重点关注**：以下 PR 创建已超过 5 个月且标记为 `[stale]`，建议尽快评估状态（继续审查、关闭或同步最新分支）：
- [PR #1069](https://github.com/netease-youdao/LobsterAI/pull/1069) `重构：拆分 CoworkSessionDetail 单文件` — 架构价值高，长期悬挂可能影响代码演进节奏。
- [PR #1070](https://github.com/netease-youdao/LobsterAI/pull/1070) `feat(cowork): 支持 per-session MCP 开关控制` — 功能需求明确，停滞时间过长易导致贡献者流失与分支分歧。

**项目健康度评级**：🟡 稳健但低活。核心维护方向清晰，但 PR 审查与社区响应存在明显瓶颈，建议加快积压条目处理以提升贡献者信心与迭代效率。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目日报 — 2026-09-06

## 1. 今日速览

过去 24 小时 CoPaw 社区活跃度保持高位：11 条 Issue 更新，其中 8 条为新开或活跃，3 条已关闭；7 条 PR 待合并，暂无新发布版本。今日亮点是多个核心稳定性问题已收到修复 PR（#7577、#7578），且 `make-skill v2`（#7509）和 `Advisor Mode`（#7569）两个新功能 PR 已进入评审队列。整体项目健康度良好，技术债清理与功能迭代同步推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 被合并，但 7 条 PR 已进入待合并或评审状态，覆盖稳定性修复、新功能开发和工具链升级三个方向：

| PR | 类型 | 摘要 |
|---|---|---|
| [#7577](https://github.com/agentscope-ai/QwenPaw/pull/7577) | 🐛 fix | 任务执行中提交消息改为排队而非返回 409，直接修复 #7559 |
| [#7578](https://github.com/agentscope-ai/QwenPaw/pull/7578) | 🐛 fix | `coordinator._drain()` 补充 `logger.exception()` 日志，解决异常栈被吞问题（修复 #7572） |
| [#7509](https://github.com/agentscope-ai/QwenPaw/pull/7509) | ✨ feat | `make-skill` 升级至 v2，引入审批驱动、草稿-发布工作流 |
| [#7569](https://github.com/agentscope-ai/QwenPaw/pull/7569) | ✨ feat | 新增 Advisor Mode，支持双模型协作（强模型规划 + 廉价模型执行） |
| [#7547](https://github.com/agentscope-ai/QwenPaw/pull/7547) | 🐛 fix | 恢复飞书渠道卡滞的会话队列消费者 |
| [#7546](https://github.com/agentscope-ai/QwenPaw/pull/7546) | 🐛 fix | 懒加载内置 channel 模块，显著缩短纯控制台环境启动时间 |
| [#6874](https://github.com/agentscope-ai/QwenPaw/pull/6874) | ✨ feat | MCP 工具调用超时可配置，默认 300s |

---

## 4. 社区热点

**🔥 #7318 — QwenPaw Hub 多租户版 roadmap 讨论**
- 评论 23 条 · 👍 3 · 最近更新 2026-09-05
- [链接](https://github.com/agentscope-ai/QwenPaw/issues/7318)

社区对多租户 Hub 的功能期待高度集中，#2324 提出的"多用户访问 + 管理员技能管理"需求在此 issue 下持续发酵。维护者主动征求社区意见，表明 2.2.0 版本将重点推进团队协作能力。

---

## 5. Bug 与稳定性

| 严重度 | Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|---|
| 🔴 高 | [#7572](https://github.com/agentscope-ai/QwenPaw/issues/7572) | 工具派发层 `_drain()` 吞掉异常栈，故障无法定位 | OPEN | ✅ #7578 |
| 🔴 高 | [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | `RetryChatModel` 硬编码 32768 context_size fallback，导致 >31130 token 全部返回 CONTEXT_UNFIT | OPEN | 暂无 |
| 🟡 中 | [#7559](https://github.com/agentscope-ai/QwenPaw/issues/7559) | 任务执行中通过对话框发消息触发 409 报错 | OPEN | ✅ #7577 |
| 🟡 中 | [#7574](https://github.com/agentscope-ai/QwenPaw/issues/7574) | `img-gen` skill 请求体缺少 `model` 字段，回退至 dall-e-2 返回 503 | ✅ 已关闭 | — |
| 🟡 中 | [#7575](https://github.com/agentscope-ai/QwenPaw/issues/7575) | `img-gen` skill `edit()` 无条件发送 `response_format`，导致 gpt-image-2 返回 400 | ✅ 已关闭 | — |
| 🟢 低 | [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | PR #7337 迁移后自定义提供商 `max_tokens` 字段报错 | ✅ 已关闭 | — |

> **关注**：#7576（context_size 硬编码）目前无修复 PR，影响所有超出 32768 token 的模型调用，建议维护者优先处理。

---

## 6. 功能请求与路线图信号

| Issue/PR | 诉求 | 纳入下版本可能性 |
|---|---|---|
| [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | QwenPaw Hub 多租户版功能规划 | 🔵 2.2.0 核心目标 |
| [#7557](https://github.com/agentscope-ai/QwenPaw/issues/7557) | Skills 版本与依赖元数据管理 | 🟡 需评估，与 Hub 多租户能力相关 |
| [#7573](https://github.com/agentscope-ai/QwenPaw/issues/7573) | Web UI 新增"编辑最后一条消息"和"回退"按钮 | 🟡 用户体验类需求，优先级待排 |
| [#7570](https://github.com/agentscope-ai/QwenPaw/issues/7570) | 飞书流式卡片思考过程自动折叠 | 🟢 已验证可行，建议纳入 |
| [#7569](https://github.com/agentscope-ai/QwenPaw/pull/7569) | Advisor Mode 双模型协作 | 🟢 PR 已提交，2.2.0 候选功能 |
| [#7509](https://github.com/agentscope-ai/QwenPaw/pull/7509) | make-skill v2 工作流升级 | 🟢 PR 已提交，2.2.0 候选功能 |

---

## 7. 用户反馈摘要

- **多租户协作需求强烈**：#7318 社区反复呼吁团队版能力，#7557 用户反映在 9 Agent 集群中 skill 无法追踪版本，凸显多租户管理的紧迫性。
- **任务执行期间消息排队是高频痛点**：#7559 用户期望任务执行中发送的消息能自动入队，而非直接 409 拒绝，#7577 已针对性修复。
- **异常可观测性不足**：#7572 开发者反馈工具调用链异常被静默吞掉，无法定位故障根因，#7578 已补充日志。
- **记忆持久化问题**：#7571 用户反映 Agent 反复遗忘配置指令（如文件输出路径限制），且插件开发时自动部署可能覆盖代码，属于模型记忆/工作流设计层面的深层痛点。
- **飞书卡片体验优化**：#7570 用户肯定 2.1.0 流式卡片效果，但希望思考过程输出后自动折叠，避免长文本占用屏幕。
- **img-gen skill API 兼容性**：#7574/#7575 两个关联 Bug 均已被关闭，修复了 OpenAI 图像 API 调用的兼容性问题。

---

## 8. 待处理积压

| Issue/PR | 原因 | 建议 |
|---|---|---|
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | 无修复 PR，影响所有超出 32768 token 的模型调用 | 优先分配修复 |
| [#7571](https://github.com/agentscope-ai/QwenPaw/issues/7571) | Agent 记忆持久化问题，涉及设计层面 | 建议维护者评估是否作为 2.2.0 专题 |
| [#7573](https://github.com/agentscope-ai/QwenPaw/issues/7573) | Web UI 功能请求，无 PR | 可考虑排入后续迭代 |
| [#6874](https://github.com/agentscope-ai/QwenPaw/pull/6874) | MCP 超时配置 PR 已提交但仍在 Under Review 状态较久（创建 2026-08-10） | 建议加速评审 |

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw 项目动态日报
**日期：2026-09-06 | 分析周期：过去24小时**

---

## 1. 今日速览

ZeptoClaw 今日以**安全加固为核心主题**，集中关闭了4个 P0/P1 级别的安全相关 Issue，并通过3个 PR 落地了关键修复，涵盖子进程环境变量泄露、无效 agent_mode 权限回退等高危问题。CI 基础设施（Clippy、cargo-deny）同步恢复，依赖更新由 Dependabot 正常推进。项目整体活跃度中上，安全合规投入显著，无新版本发布。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 摘要 | 状态 |
|----|------|------|------|
| [#672](https://github.com/qhkm/zeptoclaw/pull/672) | `fix(security)` | 在 Plugin/MCP 子进程创建点补齐环境变量脱敏，修复 P0 #660 | ✅ 已合并 |
| [#671](https://github.com/qhkm/zeptoclaw/pull/671) | `fix(security)` | 修复 `agent_mode` 无效值回退至 `Autonomous`（满权限）的问题，改为 `Assistant` + 警告 | ✅ 已合并 |
| [#645](https://github.com/qhkm/zeptoclaw/pull/645) | `fix(runtime)` | 运行时子进程环境脱敏 + 超时进程树终止/回收 | ✅ 已关闭 |
| [#646](https://github.com/qhkm/zeptoclaw/pull/646) | `chore(ci)` | 恢复 Clippy 与 cargo-deny CI 检查 | ✅ 已关闭 |

**项目整体进展评估：** 今日重点修复了安全审计（`docs/reviews/2026-09-06-hermes-comparison-review.md`）中识别的 P0 级问题，特别是**子进程环境变量继承**和**模式回退权限提升**两个高危漏洞。项目向生产安全合规迈出了实质性一步，但9个高优先级（P2-high）功能/架构 Issue 仍处于开放状态，整体仍处"安全补漏 + 架构演进"阶段。

---

## 4. 社区热点

### 最活跃 Issue 分析

**#646 — 恢复 Clippy 与 cargo-deny 检查**（3 条评论）
- 作者: qhkm | 创建: 2026-07-23 | 更新: 2026-09-06
- 背景：PR #645 暴露了两个 CI baseline 失败——Rust 1.97.1 在现有 channel/provider/binary-plugin 代码中报告5条新 Clippy 警告，cargo-deny 拒绝 quick-xml 0.39.2 和 lopdf 0.40.0 的已知漏洞版本。
- 热度来源：基础设施类 Issue，直接影响所有贡献者的 CI 体验。

**#644 — 子进程环境脱敏与进程树回收**（1 条评论）
- 背景：运行时子进程继承完整 ZeptoClaw 环境，可泄露无关凭据；超时后未确保进程树终止回收。
- 热度来源：直接关联今日合并的 PR #672/#645，安全关键 Issue。

**#659 & #660 — 安全审计 P0 发现**（各0条评论，但均今日关闭）
- 均来自 `docs/reviews/2026-09-06-hermes-comparison-review.md` 的 §8 Security posture。
- #659：无效 `agent_mode` 回退到 Autonomous（最大权限）→ 今日 PR #671 修复。
- #660：环境脱敏代码不可验证，四处 spawn 站点未统一 → 今日 PR #672 修复。

**社区诉求分析：** 维护者对安全审计发现响应迅速（P0 问题在发现同日即关闭），体现了对安全合规的高度重视。社区暂无外部 Issue 评论，说明当前以维护者驱动的内部安全整改为主。

---

## 5. Bug 与稳定性

### 今日关闭的 Bug/安全问题

| Issue | 严重程度 | 描述 | 修复 PR | 状态 |
|-------|----------|------|---------|------|
| [#660](https://github.com/qhkm/zeptoclaw/issues/660) | **P0 [security]** | 子进程环境继承未脱敏，可泄露 API Key/Token/DB URL | [#672](https://github.com/qhkm/zeptoclaw/pull/672) | ✅ 已修复 |
| [#659](https://github.com/qhkm/zeptoclaw/issues/659) | **P0 [security]** | 无效 `agent_mode` 回退至 Autonomous（满权限），而非拒绝 | [#671](https://github.com/qhkm/zeptoclaw/pull/671) | ✅ 已修复 |
| [#644](https://github.com/qhkm/zeptoclaw/issues/644) | **P1 [safety]** | 子进程超时后未终止/回收进程树 | [#645](https://github.com/qhkm/zeptoclaw/pull/645) | ✅ 已修复 |
| [#646](https://github.com/qhkm/zeptoclaw/issues/646) | **P1 [safety]** | Clippy 新警告 + cargo-deny 拒绝过期依赖 | — | ✅ 已关闭 |

**回归风险评估：** 无已知回归。#646 提及 cargo-deny 拒绝 `quick-xml 0.39.2` 和 `lopdf 0.40.0` 的已知漏洞版本，提示项目存在依赖安全风险，后续需关注是否已升级。

---

## 6. 功能请求与路线图信号

今日9个开放 Issue 均来自维护者驱动的架构审查，按模块归类如下：

| Issue | 模块 | 优先级 | 路线图信号 |
|-------|------|--------|-----------|
| [#670](https://github.com/qhkm/zeptoclaw/issues/670) | Config | P3-normal | 配置来源可见性 + env-var 弃用 |
| [#669](https://github.com/qhkm/zeptoclaw/issues/669) | Safety/Audit | P2-high [M] | 审计链跨重启持久化与轮转 |
| [#668](https://github.com/qhkm/zeptoclaw/issues/668) | Testing | P2-high [M] | 真实路径的 hermetic 集成测试 |
| [#667](https://github.com/qhkm/zeptoclaw/issues/667) | Extensibility | P2-high [M] | Footprint Ladder + 扩展元数据注册 |
| [#666](https://github.com/qhkm/zeptoclaw/issues/666) | Memory | P2-high [M] | 跨会话持久化记忆 + 事务性写入 |
| [#665](https://github.com/qhkm/zeptoclaw/issues/665) | Cron | P2-high [L] | Cron Job v2：完成确认、运行账本、运营控制 |
| [#664](https://github.com/qhkm/zeptoclaw/issues/664) | Safety/Delegation | P2-high [M] | 子 Agent 能力继承不得超过父策略 |
| [#663](https://github.com/qhkm/zeptoclaw/issues/663) | Architecture | P2-high [L] | Agent Pipeline 迁移完成（当前生产仍跑 5227行 AgentLoop） |
| [#662](https://github.com/qhkm/zeptoclaw/issues/662) | Channels | P2-high [L] | 完成 channel-plugin 协议（当前仅出站） |
| [#661](https://github.com/qhkm/zeptoclaw/issues/661) | Performance | P2-high [L] | Byte-stable Prompt Envelope（当前系统 prompt 每次重建，破坏 prompt-cache） |

**纳入下一版本的判断：**
- **[M] (Medium) 优先级较高**：#669（审计链持久化）、#666（持久化记忆）、#664（子 Agent 策略继承）与安全/核心能力相关，大概率纳入短期迭代。
- **[L] (Large) 架构级**：#663（Pipeline 迁移）、#661（Prompt 稳定性）、#662（Channel 协议）属于大规模重构，需单独排期。
- **#665（Cron v2）** 涉及语义变更（当前"成功"定义有缺陷），需谨慎评估向后兼容性。

---

## 7. 用户反馈摘要

今日 Issues 评论均为0条，无外部用户直接反馈。从 Issue 摘要中可提炼的**隐含用户痛点**：

| 痛点 | 关联 Issue | 说明 |
|------|-----------|------|
| **凭据泄露风险** | #660, #644 | 用户部署 ZeptoClaw 处理敏感任务时，子进程可能继承父进程 API Key/Token，存在横向泄露风险 |
| **配置不可见** | #670 | 用户无法直观查看"当前生效配置来自哪里"（文件 vs 环境变量），排查困难 |
| **审计链不持久** | #669 | 进程重启后审计证据丢失，无法满足合规要求 |
| **系统 Prompt 不稳定** | #661 | 每次对话重建带动态内容的 system prompt，破坏 LLM provider 的 prompt cache，增加成本和延迟 |
| **子 Agent 权限失控** | #664 | 委托的子 Agent 可能突破父 Agent 策略限制 |

**满意点：** 安全审计响应迅速，P0 问题当日闭环；CI 基础设施持续维护（Clippy/cargo-deny）。

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建时间 | 积压时长 | 风险 |
|----------|------|----------|----------|------|
| [#670](https://github.com/qhkm/zeptoclaw/issues/670) | RFC/Config | 2026-09-05 | 1天 | 低 — 刚提出 |
| [#669](https://github.com/qhkm/zeptoclaw/issues/669) | Safety/Audit | 2026-09-05 | 1天 | 中 — 合规需求 |
| [#668](https://github.com/qhkm/zeptoclaw/issues/668) | Testing | 2026-09-05 | 1天 | 中 — 测试覆盖缺口 |
| [#667](https://github.com/qhkm/zeptoclaw/issues/667) | Extensibility | 2026-09-05 | 1天 | 中 — 架构演进 |
| [#666](https://github.com/qhkm/zeptoclaw/issues/666) | Memory | 2026-09-05 | 1天 | 中 — 核心功能 |
| [#665](https://github.com/qhkm/zeptoclaw/issues/665) | Cron | 2026-09-05 | 1天 | 低 — 功能增强 |
| [#664](https://github.com/qhkm/zeptoclaw/issues/664) | Safety/Delegation | 2026-09-05 | 1天 | 高 — 安全策略 |
| [#663](https://github.com/qhkm/zeptoclaw/issues/663) | Architecture | 2026-09-05 | 1天 | 高 — 生产代码陈旧 |
| [#662](https://github.com/qhkm/zeptoclaw/issues/662) | Channels | 2026-09-05 | 1天 | 中 — 功能不完整 |
| [#661](https://github.com/qhkm/zeptoclaw/issues/661) | Performance | 2026-09-05 | 1天 | 高 — 性能瓶颈 |
| [#627](https://github.com/qhkm/zeptoclaw/pull/627) | Deps (serde_json) | 2026-06-03 | **95天** | 低 — 日常依赖更新 |
| [#625](https://github.com/qhkm/zeptoclaw/pull/625) | Deps (rpassword) | 2026-06-03 | **95天** | 低 — 日常依赖更新 |
| [#623](https://github.com/qhkm/zeptoclaw/pull/623) | Deps (tokio) | 2026-06-03 | **95天** | 低 — 日常依赖更新 |
| [#620](https://github.com/qhkm/zeptoclaw/pull/620) | Deps (scraper) | 2026-06-03 | **95天** | 低 — 日常依赖更新 |
| [#617](https://github.com/qhkm/zeptoclaw/pull/617) | Deps (tower-http) | 2026-06-03 | **95天** | 低 — 日常依赖更新 |

**维护者关注建议：**
1. **Dependabot PR 积压**：5个依赖更新 PR 已开放95天未合并，虽为低优先级但可能引入依赖版本碎片化，建议批量处理。
2. **架构迁移（#663）**：生产代码仍在运行5227行的旧 `AgentLoop`，而新 `CoreLoop` Pipeline 仅用于测试，技术债风险高，需优先排期。
3. **Prompt 稳定性（#661）**：被标注为"最大架构性能缺口"，直接影响 LLM 调用成本和延迟，建议纳入近期迭代。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报
**日期：2026-09-06** | 数据来源：GitHub API | 分析周期：过去 24 小时

---

## 1. 今日速览

ZeroClaw 在 v0.8.5 发布后继续保持高活跃度：过去 24 小时共产生 **92 条**仓库事件（42 Issues + 50 PRs），其中新开/活跃 Issues 34 条、PRs 44 条，维护者审查节奏稳健。项目当前处于 **v0.8.5 发布后的 stabilization line** 阶段（见 #9459），整体健康度良好——代码提交量稳定、RFC 讨论密集、Bug 修复与功能迭代并行推进。架构层面，Runtime 会话管理、文件系统沙箱、WASM 插件生命周期等核心 RFC 进入关键决策期，社区参与度较高。

---

## 2. 版本发布

### v0.8.5 — 安全、连接性与操作员体验发布
- **规模**：454 commits / 73 contributors
- **核心新增**：
  - **ZeroRelay** 与 **ZeroRouter**：引入新的消息中继与路由机制
  - **Live Chat 与 Provider 扩展**：支持更多实时通信渠道与模型供应商
  - **边界强化**：Plugin、Sandbox、Webhook、Credential、File 权限隔离全面加固
- **破坏性变更**：未在本次数据中明确列出，建议参考 release notes 全文
- **迁移注意**：v0.8.5 处于"有限周稳定期"（#9459），8 月 4 日已冻结新特性 intake，后续周度 release 仅接纳 ready 状态 work

> 🔗 [Issue #9459](https://github.com/zeroclaw-labs/zeroclaw/issues/9459) | [Releases](https://github.com/zeroclaw-labs/zeroclaw/releases)

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 状态 | 贡献 |
|----|------|------|
| [#10350](https://github.com/zeroclaw-labs/zeroclaw/pull/10350) | ✅ CLOSED | CI：为 PR 增加 Windows affected tests 测量（当前为 advisory，尚未进入 CI gate） |
| [#10435](https://github.com/zeroclaw-labs/zeroclaw/pull/10435) | ✅ CLOSED | Bug fix：修复 Gemini 请求锚定时丢失 model context 的问题 |
| [#10064](https://github.com/zeroclaw-labs/zeroclaw/pull/10064) | ✅ CLOSED | Bug fix：Telegram 审批卡片在操作者点击后自动销毁，提升 UX |
| [#10005](https://github.com/zeroclaw-labs/zeroclaw/pull/10005) | ✅ CLOSED | Bug fix：修正 `/health` 端点基于 channel 而非 listener liveness 判断状态 |
| [#7910](https://github.com/zeroclaw-labs/zeroclaw/issues/7910) | ✅ CLOSED | CI：为 Windows self-update/rollback/sidecar 路径补充运行时测试覆盖 |
| [#9593](https://github.com/zeroclaw-labs/zeroclaw/issues/9593) | ✅ CLOSED | Refactor：使 `TaskRecord` 成为后台委托的唯一生命周期所有者 |

**整体评估**：今日合并以 **稳定性修复** 和 **CI 加固** 为主，3 个高风险 issue 得到解决，项目在 v0.8.5 后的质量闭环正在完善。

---

## 4. 社区热点

### 讨论最活跃的 Issues（过去 24 小时持续更新）

| Issue | 评论数 | 核心议题 | 链接 |
|-------|--------|---------|------|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 33 | Runtime-owned conversation sessions & transport adapters（Rev 5） | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | 26 | Unified file & attachment architecture for conversation surfaces（Rev 10） | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) |
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) | 24 | Work Lanes, Board Automation, Label Cleanup（Rev 26，已 Ratified） | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | 24 | Granular sandbox policy – filesystem restrictions | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |

**诉求分析**：
- **#9487 / #9488** 是 v0.8.x 架构重构的核心 RFC，分别解决会话生命周期归属与文件附件统一表示问题，讨论已进入 Revision 5/10，表明社区对架构演进的深度参与。
- **#6996** 涉及安全沙箱与文件系统策略的分层治理，反映用户对 agent 权限边界的持续关注。
- **#6808** 已进入 rollout 阶段，说明项目治理机制正在从 RFC 决策向自动化工作流落地。

---

## 5. Bug 与稳定性

### 今日报告的高优先级 Bug

| Issue | 严重程度 | 组件 | 状态 | Fix PR | 链接 |
|-------|---------|------|------|--------|------|
| [#10536](https://github.com/zeroclaw-labs/zeroclaw/issues/10536) | **S1** — workflow blocked | security/sandbox (macOS Seatbelt) | in-progress | — | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/10536) |
| [#10534](https://github.com/zeroclaw-labs/zeroclaw/issues/10534) | **S2** — degraded | tool:delegate / security | open | #10391 (已 open) | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/10534) |
| [#10532](https://github.com/zeroclaw-labs/zeroclaw/issues/10532) | **S2** — degraded | config/onboarding | open | — | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/10532) |
| [#10625](https://github.com/zeroclaw-labs/zeroclaw/issues/10625) | **S2** — degraded | channel (non-vision model) | open | — | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/10625) |
| [#10533](https://github.com/zeroclaw-labs/zeroclaw/issues/10533) | **P1** — config schema | provider:router | in-progress | — | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/10533) |
| [#10585](https://github.com/zeroclaw-labs/zeroclaw/issues/10585) | **S3** — minor | ci/observability | open | — | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/10585) |
| [#10626](https://github.com/zeroclaw-labs/zeroclaw/issues/10626) | **S2** — degraded | provider (TTS) | open | — | [→](https://github.com/zeroclaw-labs/zeroclaw/issues/10626) |

**关键风险**：
- **#10536**（macOS Seatbelt ignored allowed_roots）为 S1 级别，直接阻塞 macOS 用户的安全策略配置，需优先跟进。
- **#10534**（bounded delegate 静默剥离 delegate tool）已有 open PR #10391 在追踪，预计近期可合入。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 诉求 | 纳入下版可能性 |
|----------|------|------|---------------|
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) | RFC | Gateway 直接透传消息（无需 agent turn） | 🟡 中 — 属 gateway 扩展，与 v0.8.x 路由重构方向一致 |
| [#10222](https://github.com/zeroclaw-labs/zeroclaw/issues/10222) | RFC | Opt-in single-tool provider rounds | 🟡 中 — 交互体验改进，需权衡复杂度 |
| [#10641](https://github.com/zeroclaw-labs/zeroclaw/issues/10641) | Feature | Web 端 per-field cron schedule 输入 | 🟢 高 — 低-risk UI 增强，快速落地 |
| [#10530](https://github.com/zeroclaw-labs/zeroclaw/issues/10530) | Feature | 通过 OpenAI-compatible gateway 透传 Anthropic extended-thinking | 🟢 高 — 已有 #10063 基础，兼容层完善 |
| [#10356](https://github.com/zeroclaw-labs/zeroclaw/pull/10356) | PR | 新增 AnySearch web search provider | 🟡 中 — 需 maintainer review |
| [#9997](https://github.com/zeroclaw-labs/zeroclaw/pull/9997) | PR | Telegram secure model picker | 🟡 中 — blocked，需架构确认 |

---

## 7. 用户反馈摘要

**痛点集中区**：
1. **权限与沙箱策略不一致**：#6996、#10536 反映用户在不同层面（application vs OS sandbox）遇到策略漂移，期望统一且可预测的权限模型。
2. **委托代理工具丢失**：#10534 中用户发现 bounded delegate 静默移除了 `delegate` 工具，与 `delegation_policy` 配置矛盾，影响多代理协作场景。
3. **配置迁移路径脆弱**：#10532 指出 `degraded-config` 建议的命令可能调用不同二进制，存在升级风险。
4. **非视觉模型的媒体处理**：#10625、#10045 显示文字模型收到图片 marker 时输出 `[media attachment]` 或残留临时路径，影响对话连续性。
5. **TTS 朗读原始内容**：#10626 用户反馈 Markdown 和 emoji 被原文朗读，期望预处理清洗。

**满意点**：
- v0.8.5 的安全边界强化获得认可，社区对 ZeroRelay/ZeroRouter 架构演进保持关注。
- Telegram 审批卡片 UX 改进（#10064）被正面评价。

---

## 8. 待处理积压

### 需维护者关注的长期 Issue / PR

| 类型 | Issue/PR | 创建时间 | 状态 | 建议行动 |
|------|----------|----------|------|---------|
| 🔴 高优先级 Bug | [#10536](https://github.com/zeroclaw-labs/zeroclaw/issues/10536) | 2026-09-02 | in-progress | S1 级别，macOS Seatbelt 策略失效，需优先修复 |
| 🔴 架构 RFC | [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 2026-07-28 | Proposed Rev 5 | 讨论深入，需 maintainer 召开新投票窗口 |
| 🔴 架构 RFC | [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | 2026-07-28 | Proposed Rev 10 | 同上，文件附件架构关键决策 |
| 🟡 阻塞 PR | [#10356](https://github.com/zeroclaw-labs/zeroclaw/pull/10356) | 2026-08-25 | blocked | AnySearch provider，需 review |
| 🟡 阻塞 PR | [#9997](https://github.com/zeroclaw-labs/zeroclaw/pull/9997) | 2026-08-14 | blocked | Telegram model picker，需架构确认 |
| 🟡 治理优化 | [#10549](https://github.com/zeroclaw-labs/zeroclaw/issues/10549) | 2026-09-02 | open | 简化 RFC 投票流程，移除强制讨论窗口 |
| 🟢 低优先级 | [#10641](https://github.com/zeroclaw-labs/zeroclaw/issues/10641) | 2026-09-05 | accepted | Cron 输入 UX 改进，可快速实现 |

---

**报告生成时间**：2026-09-06 | **分析师**：Agnes (Sapiens AI) | **数据来源**：[zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw)

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*