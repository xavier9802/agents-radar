# OpenClaw 生态日报 2026-08-26

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-26 01:44 UTC

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



# OpenClaw 项目动态日报 — 2026-08-26

---

## 1. 今日速览

过去24小时 OpenClaw 社区保持高活跃度：**500 条 Issue 更新**（新开/活跃 434 条，已关闭 66 条）与 **500 条 PR 更新**（待合并 311 条，已合并/关闭 189 条）。今日无新版本发布，但多条关键修复 PR 已进入维护者审查阶段，主要集中在子代理状态丢失、SQLite 稳定性、Google 流式传输质量以及 Android 端体验修复。项目整体处于**高修复吞吐期**，多个 P0/P1 级稳定性问题有活跃 PR 跟进，核心基础设施正在加速加固。

---

## 2. 版本发布

今日 **无新版本发布**。

---

## 3. 项目进展 — 今日合并/关闭的重要 PR

| PR | 作者 | 类型 | 摘要 |
|----|------|------|------|
| [#129748](https://github.com/openclaw/openclaw/pull/129748) | @steipete | fix(ui) | 将 Control UI 热刷新固定睡眠替换为 owner 信号机制，消除 CI 中 600ms+ 固定等待 |
| [#129747](https://github.com/openclaw/openclaw/pull/129747) | @steipete | fix(ui) | 修复 shadow-root 内 modal 键盘焦点泄露问题，防止后台聊天输入框劫持焦点 |
| [#129736](https://github.com/openclaw/openclaw/pull/129736) | @steipete | chore(cron) | 移除运行时 seam 重构后已退化为直接调用的重复 session 覆盖测试 |
| [#129729](https://github.com/openclaw/openclaw/pull/129729) | @Leon-SK668 | fix(agents) | 修复子代理 yield 后请求方无法继续发起新子代理波次的问题（#129455） |
| [#129728](https://github.com/openclaw/openclaw/pull/129728) | @Leon-SK668 | fix(cli) | 保留 CLI core send 的 `failed` / `partial_failed` 结构化结果，避免丢失 `deliveryStatus` |
| [#129727](https://github.com/openclaw/openclaw/pull/129727) | @steipete | fix(ui) | 修复工作区 Copy Path 操作静默忽略成功/失败结果的问题 |
| [#129733](https://github.com/openclaw/openclaw/pull/129733) | @RomneyDa | fix(ci) | 恢复 release-validation lint 与扩展测试类型检查，修复 CI 共享 main 分支失败 |
| [#129746](https://github.com/openclaw/openclaw/pull/129746) | @openclaw-mantis[bot] | chore | Control UI 本地化自动刷新，绕过保护分支检查同步翻译 |

**推进总结**：今日 PR 以 UI 稳定性、测试清理、子代理生命周期修复为主，多个 PR 修复了长期存在的 UX 摩擦点。子代理 completion 可靠性（#129729）与 CLI 消息传递可见性（#129728）是今日最实质性的基础设施改进。

---

## 4. 社区热点

### 高评论 Issue 排行

**🔥 #44925 — Subagent 完成结果静默丢失（26 评论）**
- 链接：[#44925](https://github.com/openclaw/openclaw/issues/44925)
- 评级：🦞 diamond lobster | P1
- 社区关注点：多个失败模式（E31/E42/E45）导致 subagent 结果在 timeout/drain 时无通知、无重试、无自动重启，直接影响多代理编排可靠性。

**🔥 #125626 — v2026.8.1 beta 反馈（19 评论）**
- 链接：[#125626](https://github.com/openclaw/openclaw/issues/125626)
- 当前 beta：v2026.8.1-beta.3
- 社区关注点：beta 验证集中，涉及 memory-core 与 gateway 稳定性交叉验证。

**🔥 #80319 — QA tool-defaults 套件架构争议（17 评论）**
- 链接：[#80319](https://github.com/openclaw/openclaw/issues/80319)
- 社区关注点：原报告夸大 Codex 工具丢失范围，修正后定位为 QA harness 缺陷而非 Codex runtime 广泛问题，影响测试信任度评估。

**⭐ #79902 — SQLite transcript/session seams 功能请求（14 评论）**
- 链接：[#79902](https://github.com/openclaw/openclaw/issues/79902)
- 评级：P3
- 社区关注点：高级消费者需要基于数据库优先运行时构建自定义工具，而非解析不透明 blob。

**⭐ #67777 — Subagent 直接通知超时丢失（14 评论）**
- 链接：[#67777](https://github.com/openclaw/openclaw/issues/67777)
- 评级：P1 | 🦞 diamond lobster
- 与 #44925 高度相关，是同一问题的不同技术视角（direct-announce 路径）。

### 高点赞 Issue
- [#67413](https://github.com/openclaw/openclaw/issues/67413) — 按 agent 隔离 dreaming 配置（👍 5）
- [#26037](https://github.com/openclaw/openclaw/issues/26037) — 阿里百炼 coding plan 支持（👍 4）
- [#60572](https://github.com/openclaw/openclaw/issues/60572) — 多槽位内存架构（👍 3）

---

## 5. Bug 与稳定性

### P0 / 紧急

| Issue | 标题 | 状态 | Fix PR |
|-------|------|------|--------|
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite  corruption recurs on pristine rebuilt DBs within 15–24h（WSL2） | OPEN P0 | 暂无 |
| [#87928](https://github.com/openclaw/openclaw/issues/87928) | macOS update 后 Gateway 重启风暴（node 版本不匹配死循环） | OPEN P0 stale | 暂无 |

### P1 高影响

| Issue | 标题 | 状态 | Fix PR |
|-------|------|------|--------|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent 完成静默丢失 | OPEN | #129729（部分覆盖） |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | Subagent direct-announce 超时丢失 | OPEN | #121195（等待作者） |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Hook/tool 子进程泄漏导致 zombie 累积 | OPEN | 暂无 |
| [#94939](https://github.com/openclaw/openclaw/issues/94939) | 6.x 迁移后 conversation-store SQLite 为空（MS Teams） | OPEN | 暂无 |
| [#111372](https://github.com/openclaw/openclaw/issues/111372) | macOS Gateway 配置加载后立即 SIGTERM 无限重启循环 | OPEN | 暂无 |
| [#127948](https://github.com/openclaw/openclaw/issues/127948) | WhatsApp 群回复 quote cache 过期后渲染空白气泡 | OPEN | 暂无 |
| [#126246](https://github.com/openclaw/openclaw/issues/126246) | Telegram 持久化出站交付 stuck 在 `send_attempt_started` | OPEN | 暂无 |
| [#127710](https://github.com/openclaw/openclaw/issues/127710) | prepared-model-runtime 瞬态 churn 导致永久 gateway 阻塞 | OPEN | 暂无 |
| [#125570](https://github.com/openclaw/openclaw/issues/125570) | Skill Workshop update 覆盖 live skill description 导致路由断裂 | OPEN | 暂无 |
| [#112248](https://github.com/openclaw/openclaw/issues/112248) | @openclaw/codex 插件 boot 注册失败（TypeError） | OPEN | 暂无 |
| [#106704](https://github.com/openclaw/openclaw/issues/106704) | subagent 首次 turn `sessions_yield` 静默完成 | OPEN | #121195（等待作者） |
| [#83959](https://github.com/openclaw/openclaw/issues/83959) | Codex app-server 启动重试耗尽 | OPEN | 暂无 |

### 持续跟进的 PR
- [#116926](https://github.com/openclaw/openclaw/pull/116926) — Google/Vertex 流式终端与 tool-call ID 保留（P1，等待作者）
- [#119516](https://github.com/openclaw/openclaw/pull/119516) — CLI update 失败后 Gateway 恢复（P1，审查中）
- [#129486](https://github.com/openclaw/openclaw/pull/129486) — Skill 下载归档完整性校验（P1，审查中）
- [#129670](https://github.com/openclaw/openclaw/pull/129670) — Agent 请求凭据不进入模型上下文（P1，需要 proof）

---

## 6. 功能请求与路线图信号

| Issue | 需求 | 点赞 | 可能纳入信号 |
|-------|------|------|-------------|
| [#79902](https://github.com/openclaw/openclaw/issues/79902) | SQLite transcript/session seams 暴露给外部消费者 | 2 | 中等 — 数据库优先架构已有基础 |
| [#67413](https://github.com/openclaw/openclaw/issues/67413) | 按 agent 隔离 dreaming 配置，避免内存峰值 | 5 | 高 — 生产环境 OOM 痛点明确 |
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | 多槽位内存架构（替换单 memory slot） | 3 | 中长期 — 架构级改动 |
| [#56781](https://github.com/openclaw/openclaw/issues/56781) | compaction/LCM fallback model chain | 1 | 中等 — 与 #84865 模型回退问题互补 |
| [#63930](https://github.com/openclaw/openclaw/issues/63930) | Anthropic advisor tool 支持 | 1 | 低 — 依赖上游 API 稳定性 |
| [#45758](https://github.com/openclaw/openclaw/issues/45758) | YAML 配置文件格式支持 | 2 | 低 — 维护负担 vs 收益 |
| [#105494](https://github.com/openclaw/openclaw/issues/105494) | 交互式 memory therapy 会话 | 0 | 低 — 概念新颖但实现路径不明确 |
| [#62615](https://github.com/openclaw/openclaw/issues/62615) | Gateway 侧 circuit breaker 防止 unhealthy session 重试风暴 | 0 | 高 — 与 #87928 重启风暴直接相关 |

**路线图判断**：#67413（per-agent dreaming）和 #62615（circuit breaker）是最可能进入下一版本的两个功能请求，两者均针对生产环境实际 OOM 和重启稳定性痛点。

---

## 7. 用户反馈摘要

### 核心痛点
1. **子代理可靠性**：#44925 与 #67777 反映多代理编排场景下 completion 丢失是最高频投诉，用户无法感知失败且无恢复机制。
2. **SQLite 稳定性**：#126821 和 #94939 报告了迁移后 corruption 与空数据库问题，WSL2 和 6.x 升级路径尤为突出。
3. **进程泄漏**：#97616 描述 hook/tool 子进程 zombie 累积导致运行时退化，是回归问题。
4. **渠道交付可靠性**：Telegram（#126246）、WhatsApp（#127948）、Slack（#119395 PR）均有交付丢失报告，影响生产信任。
5. **模型路由盲点**：#51441（无法看到解析后端模型）、#39811（模型名无校验）、#84865（用户切换模型后无 fallback）共同指向路由层可观测性不足。

### 正面反馈
- #125626 beta 验证活跃，说明用户对 2026.8.1 版本有较高参与度。
- #129670 secrets 功能（PR）获得关注，反映用户对凭据安全的强烈需求。
- Android 端支持 Android 9（#121198 PR）回应了长期社区诉求。

---

## 8. 待处理积压

### 长期未响应 / 需要维护者行动

| 类型 | ID | 标题 | 年龄 | 提醒 |
|------|----|------|------|------|
| Bug P0 | [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite corruption on rebuilt DBs | 6 天 | 5 天内 5 次复发，需紧急定位写并发问题 |
| Bug P0 | [#87928](https://github.com/openclaw/openclaw/issues/87928) | macOS Gateway 重启风暴 | 3 个月 | stale 标签但影响持续，需重新评估 |
| Bug P1 | [#97616](https://github.com/openclaw/openclaw/issues/97616) | 子进程泄漏 zombie 累积 | 2 个月 | 回归问题，无 fix PR |
| Bug P1 | [#114612](https://github.com/openclaw/openclaw/issues/114612) | memory_index_chunks 无 retention policy | 30 天 | SQLite 无限增长，无 fix PR |
| PR | [#116926](https://github.com/openclaw/openclaw/pull/116926) | Google 流式传输修复 | 26 天 | 等待作者，P1 高影响 |
| PR | [#121195](https://github.com/openclaw/openclaw/pull/121195) | subagent yield 完成精确 settle | 17 天 | 等待作者，关联 #44925/#67777 |
| PR | [#129670](https://github.com/openclaw/openclaw/pull/129670) | Agent 凭据隔离（secrets） | 1 天 | 需要 proof 材料，高价值功能 |

---

## 项目健康度评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 活跃活跃度 | ⭐⭐⭐⭐☆ | 500+ 日更 Issue/PR，社区参与度高 |
| 修复响应 | ⭐⭐⭐⭐☆ | P1 问题有活跃 PR，但 P0 暂无合并修复 |
| 稳定性趋势 | ⭐⭐⭐☆☆ | SQLite corruption / 进程泄漏 / 子代理丢失等核心问题仍 open |
| 测试覆盖 | ⭐⭐⭐⭐☆ | CI lint 修复、QA 流程改进持续进行 |
| 维护者可见性 | ⭐⭐⭐⭐☆ | 多 PR 处于 `👀 ready for maintainer look`，审查节奏正常 |

**总体评估**：OpenClaw 处于**高频修复窗口期**，社区反馈活跃且维护者响应及时。核心风险集中在 SQLite 持久层稳定性与子代理编排可靠性，建议维护者优先处理 #126821 与 #97616，并在 2026.8.1 正式版发布前确保 #116926（Google 流式）和 #121195（subagent yield settle）合并。

---

## 横向生态对比



# 个人 AI 助手开源生态横向对比分析报告
**日期：2026-08-26** | **分析师：Agnes-2.0-Flash (Sapiens AI)**

---

## 1. 生态全景

2026年8月下旬，个人 AI 智能体开源生态呈现**高频修复与架构收敛**并行的特征。OpenClaw、CoPaw、Hermes Agent 保持高吞吐迭代，NanoClaw 和 IronClaw 在容器编排与 CI 基础设施上集中发力，LobsterAI 率先推进商业化功能落地。社区共识正从"功能堆叠"转向**稳定性加固**（子代理可靠性、SQLite持久层、MCP工具链）与**部署灵活化**（边缘 worker、家庭 mesh 网络）。整体生态处于技术成熟期的关键转折：核心框架趋于稳定，差异化竞争集中在渠道体验、安全隔离与商业化路径。

---

## 2. 各项目活跃度对比

| 项目 | Issue 数 | PR 数 | 版本发布 | 健康度 | 核心状态 |
|------|----------|-------|----------|--------|----------|
| **OpenClaw** | 500 | 500 | 无 | ⭐⭐⭐⭐☆ | 高频修复窗口期，P0 问题待解 |
| **CoPaw** | 33 | 50 | ✅ v2.1.1-beta.3 | ⭐⭐⭐⭐☆ | 快速迭代，SSE/内存问题集中爆发 |
| **Hermes Agent** | 50 | 50 | 无 | ⭐⭐⭐⭐☆ | 稳定推进，桌面端/CLI兼容性修复密集 |
| **NanoClaw** | 5 | 50 | 无 | ⭐⭐⭐⭐☆ | 基建重构期，core-team 主导合并 |
| **IronClaw** | 37 | 24 | 无 | ⭐⭐⭐⭐☆ | 基础设施迭代完整，agent loop 性能待优化 |
| **NanoBot** | 5 | 24 | 无 | ⭐⭐⭐⭐☆ | 体验打磨阶段，安全修复优先级高 |
| **LobsterAI** | 1 | ~9 | ✅ v2026.8.25 / v2026.8.21 | ⭐⭐⭐⭐☆ | 商业化推进，资料库功能完善 |
| **Moltis** | 2 | 5 | 无 | ⭐⭐⭐☆☆ | 中等活跃，sandbox 方向明确 |
| **PicoClaw** | 4 | 1 | 无 | ⭐⭐⭐☆☆ | 低维护节奏，边缘计算提案浮现 |
| **NullClaw** | 1 | 0 | 无 | ⭐⭐☆☆☆ | 低活跃期，技术方向清晰但推进缓慢 |
| **ZeptoClaw** | 0 | 0 | 无 | ⭐⭐☆☆☆ | 无活动 |
| **ZeroClaw** | — | — | — | ⚠️ 异常 | 摘要生成失败 |

---

## 3. OpenClaw 在生态中的定位

**规模优势**：OpenClaw 以日均 500+ Issue/PR 的吞吐量稳居生态头部，社区活跃度远超其他项目（次高 CoPaw 仅 83 条）。其子代理编排（subagent yield/settle）和 SQLite 持久层是生态中最复杂的基础设施，成为其他项目参考的基准。

**技术路线差异**：
- **OpenClaw**：多代理编排 + 渠道聚合（WhatsApp/Telegram/Slack）+ 本地优先架构，强调"个人 AI 操作系统"定位
- **NanoClaw/IronClaw**：容器化部署 + 自动化运维，偏向"可部署的 agent 平台"
- **CoPaw/Hermes**：桌面客户端 + 多渠道集成，偏向"个人助手应用"
- **PicoClaw/NullClaw**：边缘计算 + 低功耗硬件，差异化定位家庭/物联网场景

**社区规模对比**：OpenClaw 的 issue 讨论深度（#44925 子代理丢失 26 评论、#66616 Skills 索引 97 评论）反映其用户群体已进入生产级使用阶段，其他项目仍处于功能完善或早期采用阶段。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **子代理/并发可靠性** | OpenClaw, NanoBot, CoPaw | 完成结果静默丢失（#44925/#67777）、部分完成标记缺失（NanoBot #5152）、SSE 死循环崩溃（CoPaw #7261） |
| **渠道集成稳定性** | OpenClaw, NanoBot, Hermes, Moltis | Telegram 富文本流式互斥、WhatsApp 交付 stuck、Slack 工具失效、微信思考过程设置无效 |
| **安全隔离/Sandbox** | NanoBot, Moltis, NanoClaw, IronClaw | 受限 Shell 沙箱 fail-closed（NanoBot #5536）、K8s 原生 sandbox（Moltis #1118）、Coder 远程工作空间（Moltis #1199） |
| **边缘计算/去中心化部署** | PicoClaw, NullClaw, NanoClaw, IronClaw | 家庭边缘 worker 模式（#3345/#994/#3538）、多设备 mesh 网络、RuntimeAdapter 调度 |
| **SQLite/持久层稳定性** | OpenClaw, Hermes | SQLite corruption 复发（#126821）、空数据库迁移问题（#94939）、keychain 权限泄漏（Hermes #84106） |
| **工具链/MCP 健壮性** | Hermes, Moltis, OpenClaw | gh CLI 2.98+ 兼容、MCP stdio 子进程活检测、多服务器网关重启 |

---

## 5. 差异化定位分析

| 维度 | OpenClaw | CoPaw | Hermes Agent | NanoClaw | LobsterAI |
|------|----------|-------|--------------|----------|-----------|
| **功能侧重** | 多代理编排 + 渠道聚合 | 桌面客户端 + Skill 生态 | 跨平台桌面 + MCP 工具链 | 容器化部署 + 自动化运维 | 资料库 + 商业化变现 |
| **目标用户** | 高阶开发者/生产环境 | 普通用户/中文社区 | 桌面用户/开发者 | DevOps/企业部署 | 内容创作者/付费用户 |
| **技术架构** | Node.js + SQLite + 子代理协议 | Electron + PluginAPI + SSE | Electron + gh CLI + MCP | Docker/K8s + container lifecycle | React + 支付集成 |
| **差异化优势** | 生态最成熟、渠道最全 | 中文社区活跃、迭代快 | 桌面体验优化、i18n 支持 | 运维自动化、setup 协议 | 商业化路径清晰 |
| **核心痛点** | SQLite 稳定性、子代理可靠性 | SSE 序列化、内存泄漏 | macOS 权限管理、Windows 更新 | Shell 注入安全、per-agent 权限 | 会话分支功能停滞 |

---

## 6. 社区热度与成熟度分层

### 🔥 快速迭代层（高频功能推进）
- **CoPaw**：日更 83 条活动，发布 beta 版本，SSE/内存问题集中爆发后快速响应关闭
- **OpenClaw**：500+ 日更，P1 修复 PR 密集，处于"高修复吞吐期"
- **LobsterAI**：双版本发布，商业化功能持续落地

### ⚡ 稳定推进层（基础设施加固）
- **Hermes Agent**：50/50 活跃，桌面端稳定性修复密集，i18n 扩展明确
- **NanoClaw**：50 PR 中 34 待合并，core-team 主导基建重构，向"架构收敛期"过渡
- **IronClaw**：CI 流水线完整迭代（nextest + preflight + convergence），通知中心退役 legacy

### 🟡 质量巩固层（低频修复为主）
- **NanoBot**：24 PR 以稳定性修复和体验打磨为主，安全修复优先
- **Moltis**：中等活跃，sandbox 方向明确但推进节奏稳健

### 🟢 早期/观望层
- **PicoClaw**：低维护节奏，边缘计算提案浮现但无核心开发
- **NullClaw**：极低活跃，技术方向清晰但无代码推进
- **ZeptoClaw/ZeroClaw**：无活动或异常

---

## 7. 值得关注的趋势信号

### 信号一：子代理编排可靠性成为生态分水岭
OpenClaw #44925（26 评论）、NanoBot #5152、CoPaw #7261 共同指向**多代理并发场景下的状态一致性**是生产级使用的核心门槛。未来 6 个月内，谁能解决"completion 静默丢失"和"SSE 序列化死循环"问题，谁就能赢得企业用户信任。

### 信号二：边缘计算从概念走向提案
PicoClaw #3345、NullClaw #994、NanoClaw #3538 几乎同日出现"家庭边缘 worker"提案，反映用户对**去中心化部署、闲置硬件复用**的强烈需求。RuntimeAdapter、signed receipts、边缘 mesh 等概念正在成为跨项目通用词汇。

### 信号三：安全修复从功能层下沉到基础设施层
NanoBot #5536（fail-closed 沙箱）、NanoClaw #3543（Shell 注入）、Hermes #84106（MCP 密钥泄露）表明社区对**权限边界和注入防护**的关注度显著提升。生态正从"功能优先"转向"安全优先"。

### 信号四：多渠道一致性仍是最大短板
OpenClaw（Telegram/WhatsApp stuck）、NanoBot（rich+streaming 互斥）、Moltis（Slack 工具失效）、CoPaw（微信设置无效）共同揭示：**渠道适配的碎片化**是生态级痛点。统一的消息路由和上下文管理协议将是下一个技术突破点。

### 信号五：商业化路径开始分化
LobsterAI 率先推进资料库付费转化（模型目录展示、埋点归因），其他项目仍聚焦技术建设。这暗示生态将分化为**技术开源 + 商业增值**的双层结构，后续需关注付费功能与开源核心的边界界定。

---

**报告结论**：个人 AI 助手开源生态已进入**从功能扩张到质量巩固**的转折期。OpenClaw 作为生态基准持续牵引技术方向，CoPaw 和 Hermes 在客户端体验上竞争，NanoClaw 和 IronClaw 构建可运维的基础设施，LobsterAI 探索商业化路径。未来 3-6 个月，子代理可靠性、边缘部署、安全隔离将是决定项目天花板的关键战场。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-26

## 1. 今日速览

过去 24 小时 NanoBot 社区保持**高活跃度**：5 条 Issue 更新、24 条 PR 动态（14 条已合并/关闭，10 条待审），但**无新版本发布**。今日核心亮点集中在三块：Telegram 消息路由与富文本渲染修复、TUI/WebUI 交互体验优化、以及文档检索与 session 管理的能力扩展。安全相关 PR #5536（受限 Shell 沙箱降级策略）被标记为 P1，值得重点关注。整体项目处于功能性修复与用户体验打磨并行的阶段，技术债务清理节奏良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的 **14 条 PR** 覆盖了多个关键方向：

### 渠道与消息路由
- **#5541** [CLOSED] Telegram 群消息发送者归属修复 — 非私聊消息前缀显示发送者名称，降级链路覆盖昵称/用户名/数字 ID，修复 #1091。
- **#5531** [OPEN] Telegram 流式预览升级为富文本 — 修复 `rich_messages: true` 与 `streaming: true` 互斥的回归，流结束时原地替换为 rich 消息。

### Provider 与缓存
- **#5540** [CLOSED] Codex Prompt Cache 路由稳定性 — 将 nanobot session 身份 propagate 至 provider 调用上下文，`prompt_cache_key` 仅从 session 派生，消除消息哈希的不确定性。

### TUI 体验
- **#5538** [CLOSED] Composer 操作提示重构 — 将 `Steer this turn…` 替换为响应式占位符 `Enter send now · Tab send next`，保留 Enter/Tab 双发送语义。
- **#5534** [CLOSED] TUI Skill 自动补全 — 支持 `$skill-name` 键入时从 gateway 拉取可用技能并展示过滤选择器，支持箭头导航、Escape dismiss。
- **#5530** [CLOSED] 短 transcript 与 composer 顶部对齐 — 解决长终端中内容分布不均问题。

### 文档与执行
- **#5525** [CLOSED] 需求驱动文档检索 — `grep` 改为默认按需返回带上下文的 snippet；新增 PDF/DOCX/XLSX/PPTX 增量搜索，突破 200K 附件预览上限。
- **#5526** [CLOSED] exec_session 工具重构 — 重命名并暴露 7 字段 schema，新增 `until_exit` / `timeout_ms` 控制，消除轮询等待。
- **#5533** [CLOSED] find_files 扫描性能优化 — 用 `os.scandir` 替代重复 `pathlib` 调用，支持分页 lookahead 与取消 propagation。

### WebUI
- **#5389** [CLOSED] 拖拽 Session 组织 — 支持独立 session 与分组内 session 的拖拽重排序，允许拖拽创建分组。

### Agent 生命周期
- **#5529** [CLOSED] 后台子 agent 等待时机优化 — 普通 pending-message drain 保持非阻塞，仅在 turn 出口处 rendezvous 等待子 agent，共享 300s 超时。

> **整体推进评估**：今日 PR 以**稳定性修复 + 体验打磨**为主，新功能（文档检索、Skill 补全、拖拽组织）点缀其中，无架构级变更，项目稳健向前。

---

## 4. 社区热点

| # | 类型 | 标题 | 评论 | 热度分析 |
|---|------|------|------|----------|
| [#5505](https://github.com/HKUDS/nanobot/issues/5505) | Issue | Add AnySearch as web search provider | 3 | 第三方搜索工具团队主动寻求集成，提出 API/MCP/Skill 三种接入方式，反映用户对**多样化搜索后端**的需求 |
| [#5536](https://github.com/HKUDS/nanobot/pull/5536) | PR | fail closed when restricted shell lacks sandbox | — | P1 安全修复，直接关联 #4072，解决 symlink/命令替换绕过路径检查的漏洞，社区关注度高 |
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) | PR | integrate mst-python as metasearch provider | — | 长期开放 PR（创建于 08-03），提出 RRF 多引擎聚合搜索，与 #5505 形成互补，反映用户**多源搜索**诉求 |
| [#5516](https://github.com/HKUDS/nanobot/issues/5516) | Issue | Telegram rich messages never render with streaming | 1 | 明确指向 Bot API 10.1-10.3 draft 可修复，用户已提供技术方案，期待 upstream 跟进 |
| [#5527](https://github.com/HKUDS/nanobot/issues/5527) / [#5528](https://github.com/HKUDS/nanobot/pull/5528) | Issue + PR | WebUI sidebar titles stay "Untitled" under unifiedSession | 0 + 1 | 用户报告与作者修复形成闭环，unifiedSession 与 per-chat session 标题同步机制存在 gap |

---

## 5. Bug 与稳定性

| 严重程度 | Issue/PR | 描述 | Fix 状态 |
|----------|----------|------|----------|
| **P1 安全** | [#5536](https://github.com/HKUDS/nanobot/pull/5536) [OPEN] | 受限 Shell 无沙箱时未 fail-closed，存在路径绕过风险（#4072） | 有 PR，待合并 |
| **P1** | [#5533](https://github.com/HKUDS/nanobot/pull/5533) [CLOSED] | `find_files` 扫描阻塞主线程，pathlib 重复调用导致性能退化 | ✅ 已合并 |
| **P2** | [#5532](https://github.com/HKUDS/nanobot/issues/5532) [OPEN] | `autocompact.py` 缺少 `mask_session_key` import，处理特定中文 query 时崩溃 | 无 Fix PR |
| **P2** | [#5516](https://github.com/HKUDS/nanobot/issues/5516) [OPEN] | Telegram `rich_messages` 与 `streaming` 互斥，富文本永不渲染 | 有 PR #5531 待合并 |
| **P2** | [#5527](https://github.com/HKUDS/nanobot/issues/5527) [OPEN] | unifiedSession 下 WebUI sidebar 标题始终为 "Untitled" | 有 PR #5528 待合并 |
| **回归** | [#5152](https://github.com/HKUDS/nanobot/pull/5152) [OPEN] | 子 agent 部分完成结果未标记，导致模型误判为完整结果 | 有 PR 待合并 |

> **稳定性评估**：今日 2 个 P2 Bug 已有对应 Fix PR 但尚未合并，1 个 P2 import 错误无修复，1 个 P1 安全问题待合并。整体回归风险可控，但安全修复应优先推进。

---

## 6. 功能请求与路线图信号

| 请求 | Issue/PR | 路线图示警 |
|------|----------|-----------|
| AnySearch 作为 Web 搜索 Provider | [#5505](https://github.com/HKUDS/nanobot/issues/5505) | ✅ 已有整合意图，与 #5234 (mst-python) 方向一致，预计纳入搜索后端扩展路线 |
| WebUI 会话结束通知铃声 | [#5524](https://github.com/HKUDS/nanobot/issues/5524) | 🟡 明确需求描述（默认关闭、Settings 开关、短促提示音），但暂无 PR，可能作为低优先级增强 |
| `my` 工具 persist session focus | [#5537](https://github.com/HKUDS/nanobot/pull/5537) [OPEN] | ✅ 修复 #3292，session 级状态持久化能力，符合 agent 连续性设计趋势 |
| MCP 就绪重试机制 | [#5535](https://github.com/HKUDS/nanobot/pull/5535) [OPEN] | 修复 NAN-43，提升 gateway 韧性，属于基础设施稳定性增强 |
| 子 agent 部分完成标记 | [#5152](https://github.com/HKUDS/nanobot/pull/5152) [OPEN] | 修复并发子 agent 结果误判，属于 agent loop 可靠性改进 |

> **路线图判断**：今日社区信号集中在**搜索后端扩展、session 状态管理、MCP/子 agent 可靠性**三个方向，与项目既有演进路径一致。通知铃声类 UX 增强暂无 PR 跟进，可能被排至后续版本。

---

## 7. 用户反馈摘要

**痛点与不满：**
- **Telegram 富文本与流式输出互斥**（#5516）：用户已明确指出 Bot API 10.1-10.3 draft 可提供解法，说明用户对 Telegram 渠道体验有较高期待。
- **unifiedSession 下标题丢失**（#5527）：shared session 与 per-chat session 的标题同步机制断裂，影响多会话用户的工作流。
- **长任务无完成提示**（#5524）：WebUI 用户等待 agent 执行工具调用/文件编辑/Shell 命令时，缺乏明确完成信号，需刷新或盯着屏幕。
- **受限 Shell 安全风险**（#5536 关联 #4072）：path 检查无法覆盖 symlink/命令替换，用户关注安全边界。

**满意点：**
- **拖拽 Session 组织**（#5389）：用户欢迎 WebUI 新增的拖拽排序与分组创建能力。
- **Skill 自动补全**（#5534）：TUI 中输入 `$skill-name` 时的过滤选择器提升了操作效率。
- **文档检索扩展**（#5525）：PDF/DOCX/XLSX/PPTX 增量搜索突破了原有 200K 限制，用户反馈积极。

---

## 8. 待处理积压

| 优先级 | 项目 | 状态 | 建议 |
|--------|------|------|------|
| **P1** | [#5536](https://github.com/HKUDS/nanobot/pull/5536) — fail closed 沙箱修复 | OPEN，待合并 | 安全类修复应优先 review 合并 |
| **P2** | [#5532](https://github.com/HKUDS/nanobot/issues/5532) — `mask_session_key` import 缺失 | OPEN，无 Fix PR | 建议维护者快速跟进，一行修复 |
| **P2** | [#5516](https://github.com/HKUDS/nanobot/issues/5516) — Telegram rich+streaming | 有 PR #5531 待合并 | 合并 #5531 即可关闭 |
| **P2** | [#5527](https://github.com/HKUDS/nanobot/issues/5527) — WebUI 标题同步 | 有 PR #5528 待合并 | 合并 #5528 即可关闭 |
| **长期** | [#5234](https://github.com/HKUDS/nanobot/pull/5234) — mst-python metasearch | OPEN 逾 23 天 | 与 #5505 方向重叠，建议与 AnySearch 整合方案统一评估 |
| **长期** | [#5152](https://github.com/HKUDS/nanobot/pull/5152) — 子 agent 部分完成标记 | OPEN 逾 29 天 | 涉及 agent loop 核心逻辑，需仔细 review |
| **低优** | [#5524](https://github.com/HKUDS/nanobot/issues/5524) — WebUI 通知铃声 | OPEN，无 PR | 可作为 UX 增强待排期 |

---

**报告生成时间**：2026-08-26 | **数据周期**：过去 24 小时 | **项目**：[HKUDS/nanobot](https://github.com/HKUDS/nanobot)

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目动态日报
**日期：2026-08-26** | **分析周期：过去24小时**

---

## 1. 今日速览

Hermes Agent 今日保持**高活跃度**：50条Issue更新（41活跃/9关闭）与50条PR更新（40待合并/10合并），社区响应节奏稳定。整体无新版本发布，但修复类PR密集，主要集中在桌面端稳定性（macOS签名/Profiles）、跨平台兼容性（gh CLI 2.98+、Windows更新）及MCP工具链。项目健康度良好，风险敞口集中在**桌面端session状态管理**与**Slack流式消息去重**两个子系统。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要PR

| PR | 类型 | 摘要 | 影响 |
|----|------|------|------|
| [#91679](https://github.com/NousResearch/hermes-agent/issues/91679) | bugfix | 修复删除backend profile后Desktop卡死；临时签名macOS bundle | 提升桌面端容错能力 |
| [#95162](https://github.com/NousResearch/hermes-agent/issues/95162) / [#95158](https://github.com/NousResearch/hermes-agent/issues/95158) | bugfix | 移除`gh auth status --json authenticated`以兼容gh CLI 2.98+ | 修复doctor检查失败 |
| [#95144](https://github.com/NousResearch/hermes-agent/issues/95144) | bugfix | 修复`_stdio_children_dead()`返回值反转的逻辑错误 | 解决MCP stdio子进程活检测失效 |
| [#88422](https://github.com/NousResearch/hermes-agent/issues/88422) | bugfix | 修复浅克隆场景下`git fetch`不跨越shallow boundary导致更新假成功 | 提升git-based更新可靠性 |
| [#95155](https://github.com/NousResearch/hermes-agent/issues/95155) | bugfix | 修复web dashboard代码分割chunk在proxy prefix下的asset路径 | 改善部署灵活性 |

**整体判断**：今日推进了**5项关键稳定性修复**，主要集中在提升桌面端容错、修复跨平台CLI兼容性及MCP工具链健壮性，为后续版本迭代扫除了若干阻塞性问题。

---

## 4. 社区热点

### 讨论最活跃的Issues（按评论数排序）

| Issue | 评论数 | 摘要 | 链接 |
|-------|--------|------|------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 97 | Skills index过期（29.8h > 26h限制），状态degraded | [链接](https://github.com/NousResearch/hermes-agent/issues/66616) |
| [#52010](https://github.com/NousResearch/hermes-agent/issues/52010) | 21 | macOS Full Disk Access权限每次更新后被撤销，需手动重新授权 | [链接](https://github.com/NousResearch/hermes-agent/issues/52010) |
| [#40239](https://github.com/NousResearch/hermes-agent/issues/40239) | 11 | 请求为Desktop添加巴西葡萄牙语(i18n)支持（已获3👍） | [链接](https://github.com/NousResearch/hermes-agent/issues/40239) |
| [#95003](https://github.com/NousResearch/hermes-agent/issues/95003) | 10 | xAI API拒绝`tool_search`函数名（与内置工具冲突），Grok provider不可用（8👍） | [链接](https://github.com/NousResearch/hermes-agent/issues/95003) |
| [#91115](https://github.com/NousResearch/hermes-agent/issues/91115) | 9 | macOS keychain提示每次更新后出现，因Electron重新签名导致ACL不匹配 | [链接](https://github.com/NousResearch/hermes-agent/issues/91115) |

**热点分析**：
- **#66616**（97评论）长期未决，反映Skills Hub索引刷新机制存在可靠性问题，用户依赖该功能进行skill发现。
- **#52010**与**#91115**共同指向macOS Desktop更新流程中代码签名与权限管理的技术债，需系统层面修复。
- **#95003**获得8👍，表明provider兼容性是高频痛点，建议维护者评估函数名冲突的修复优先级。

---

## 5. Bug 与稳定性

### 已关闭的Bug（今日）

| Issue | 严重程度 | 摘要 | 修复方式 |
|-------|----------|------|----------|
| [#16520](https://github.com/NousResearch/hermes-agent/issues/16520) | P2 | 终端工具`read_file`/`cat`截断长行导致模型误判文件损坏 | 已合并至main |
| [#87703](https://github.com/NousResearch/hermes-agent/issues/87703) | P2 | Windows更新挂起~11分钟（cua-driver刷新UAC提示不可见） | 已关闭 |
| [#94516](https://github.com/NousResearch/hermes-agent/issues/94516) | P2 | Desktop Bot Mode Cronjobs回归："agent appears in the roster"硬编码占位符 | 已关闭 |
| [#90428](https://github.com/NousResearch/hermes-agent/issues/90428) | P2 | WebSocket断连后消息静默丢失，无错误提示 | 已关闭 |
| [#93617](https://github.com/NousResearch/hermes-agent/issues/93617) | P3 | Slack并发对话导致流式消息重复 | 已关闭 |
| [#94471](https://github.com/NousResearch/hermes-agent/issues/94471) | P2 | Desktop Bots tab崩溃：`trim is not a function` | 已关闭 |
| [#93594](https://github.com/NousResearch/hermes-agent/issues/93594) | P2 | bot-relay drain loop每4秒开/关WS导致gateway日志洪泛 | 已关闭 |

### 开放中的高优先级Bug

| Issue | 严重程度 | 摘要 | Fix PR |
|-------|----------|------|--------|
| [#95003](https://github.com/NousResearch/hermes-agent/issues/95003) | P2 | xAI `tool_search`函数名冲突，Grok provider不可用 | — |
| [#94906](https://github.com/NousResearch/hermes-agent/issues/94906) | P1 | Windows stdio MCP工具调用全部失败：`subprocess has exited` | [#95144](https://github.com/NousResearch/hermes-agent/issues/95144) 已合并 |
| [#95078](https://github.com/NousResearch/hermes-agent/issues/95078) | P2 | 嵌套Hermes继承过期`TERMINAL_CWD`导致工作目录错误 | — |
| [#94859](https://github.com/NousResearch/hermes-agent/issues/94859) | P2 | 多MCP服务器网关重启后间歇性调用失败 | — |
| [#94946](https://github.com/NousResearch/hermes-agent/issues/94946) | P2 | Browser Use CLI模式下inactivity_timeout与orphan reaper为死代码 | — |
| [#84106](https://github.com/NousResearch/hermes-agent/issues/84106) | P2 | `hermes config get mcp_servers`泄露MCP密钥 | — |

**稳定性评估**：今日关闭7个Bug，但开放列表中P1/P2级问题仍有6个，其中**Windows MCP工具调用**（#94906）与**密钥泄露**（#84106）需优先关注。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 摘要 | 纳入可能性 |
|----------|------|------|------------|
| [#40239](https://github.com/NousResearch/hermes-agent/issues/40239) | feature | Desktop pt-BR语言支持（已有357+行翻译基础） | **高** — 社区需求明确，已有PR基础 |
| [#95152](https://github.com/NousResearch/hermes-agent/issues/95152) | feature | Kanban rework §1：done-terminal gate、reanimate verb、schedule操作 | **中** — 依赖kanban架构决策 |
| [#93382](https://github.com/NousResearch/hermes-agent/issues/93382) | feature | 交互式学习artifacts的自适应解释策略 | **低** — 需架构决策，`needs-decision` |
| [#91005](https://github.com/NousResearch/hermes-agent/issues/91005) | feature | 软归档session的本地冷存储验证 | **中** — 解决存储膨胀问题 |
| [#89061](https://github.com/NousResearch/hermes-agent/issues/89061) | feature | 添加SSYCloud（胜算云）LLM provider | **中** — 区域化provider扩展 |
| [#93508](https://github.com/NousResearch/hermes-agent/issues/93508) | feature | `hermes webapp`：在浏览器中托管Desktop renderer | **高** — 扩展部署形态，已有PR #93508 |

**路线图信号**：今日PR #93508（浏览器托管Desktop）与#95152（Kanban重构）显示项目正在推进**部署灵活性**与**任务管理架构升级**两条主线。

---

## 7. 用户反馈摘要

### 痛点
1. **macOS权限管理**（#52010, #91115）：每次更新后Full Disk Access与keychain权限被撤销，用户需手动重新授权，体验中断。
2. **Windows更新阻塞**（#87703, #84678）：cua-driver刷新与无Edge环境下的WinForms fallback导致更新挂起或进度卡隐藏。
3. **MCP工具链稳定性**（#94906, #94859, #84106）：Windows stdio MCP调用失败、多服务器重启间歇性错误、密钥泄露风险。
4. **Slack流式重复**（#93617, #94435）：并发对话场景下消息去重逻辑缺陷导致重复发送。
5. **Session状态泄漏**（#90428, #93937, #79005）：WebSocket断连后消息静默丢失、gateway切换时session ID泄漏、profile切换路由到错误backend。

### 满意点
- 社区对**i18n扩展**（#40239）积极响应，3👍表明多语言支持需求强烈。
- **doctor检查修复**（gh CLI 2.98+兼容）获得快速响应，体现维护者对工具链兼容性的重视。
- **MCP活检测修复**（#95144）解决了底层逻辑错误，提升工具链可靠性。

---

## 8. 待处理积压

| Issue | 龄期 | 严重程度 | 建议优先级 |
|-------|------|----------|------------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 39天 | P3 | 高 — 97评论反映广泛用户关切 |
| [#52010](https://github.com/NousResearch/hermes-agent/issues/52010) | 63天 | P2 | 高 — macOS用户核心体验问题 |
| [#91115](https://github.com/NousResearch/hermes-agent/issues/91115) | 36天 | P2 | 高 — 与#52010同根，需联合修复 |
| [#84106](https://github.com/NousResearch/hermes-agent/issues/84106) | 45天 | P2 (security) | 紧急 — 密钥泄露安全风险 |
| [#95003](https://github.com/NousResearch/hermes-agent/issues/95003) | 1天 | P2 | 高 — xAI provider阻塞用户 |
| [#94946](https://github.com/NousResearch/hermes-agent/issues/94946) | 1天 | P2 | 中 — Browser工具死代码问题 |

**维护者提醒**：
- **#84106**为安全类Issue，建议优先处理。
- **#66616**长期无进展，建议评估是否为架构缺陷并明确修复计划。
- **#52010**与**#91115**同属macOS签名/权限技术债，建议合并评估修复方案。

---

**日报生成完毕** | 数据来源：Hermes Agent GitHub API | 分析师：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-26

## 1. 今日速览

PicoClaw 在过去 24 小时内维持中等活跃度，共新增 4 个 Issue 与 1 个 PR，无任何版本发布。项目当前以社区反馈驱动为主：Web UI 性能问题、MCP 连接稳定性缺陷、Slack 集成媒体上传故障构成今日三大焦点，同时出现一版面向边缘计算场景的轻量化架构提案。整体项目健康度良好，但 Issue 修复节奏偏慢，多个高价值问题仍处于 `stale` 标记状态，建议维护团队加快响应。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

| PR | 类型 | 状态 | 关联 Issue |
|----|------|------|------------|
| [#3340](https://github.com/sipeed/picoclaw/issues/3340) `fix(slack): set FileSize on media upload params` | Bug Fix | OPEN / stale | [#3338](https://github.com/sipeed/picoclaw/issues/3338) |

**进展评估：** 今日唯一 PR 修复了 Slack 媒体上传 `file size cannot be 0` 的 SDK 校验问题，直接闭环 Issue #3338。该修复代码量极小（补全 `FileSize` 字段赋值），属于精确补丁。项目整体仍处于"问题发现 → 社区修复"的自然流转阶段，暂无核心功能突破。

---

## 4. 社区热点

### 🔥 评论最多：Web UI 输入卡顿
- [#3281](https://github.com/sipeed/picoclaw/issues/3281) — 7 条评论 · 1 👍 · `stale`
  - 用户 `xpader` 报告：当会话历史较长时，Web UI 输入框出现明显卡顿。
  - **核心诉求：** 输入性能与历史渲染开销的平衡，直接影响日常使用体验。
  - **分析：** 该 Issue 标记为 `stale` 但评论活跃，说明维护者关注但尚未排期修复；高评论数反映社区对该痛点的共鸣较强。

### 🔥 稳定性影响最大：MCP 连接失败导致 Agent 挂死
- [#3269](https://github.com/sipeed/picoclaw/issues/3269) — 7 条评论 · 1 👍
  - 用户 `ruiyigen` 报告：MCP Server 连接失败后 Agent 循环挂起，Chat 界面完全停止响应。
  - **核心诉求：** 异常回路与连接超时机制的健壮性保障。
  - **分析：** 无对应 PR，属于架构级缺陷，可能涉及 Agent Loop 的错误处理路径，修复复杂度较高。

### 🔥 功能完整性：Slack 图片上传失效
- [#3338](https://github.com/sipeed/picoclaw/issues/3338) — 2 条评论 · 0 👍 · `stale`
  - 用户 `octavioturra` 报告：Slack `SendMedia` 未设置 `FileSize`，触发 `files.upload.v2` 校验拒绝。
  - **已有修复 PR：** [#3340](https://github.com/sipeed/picoclaw/pull/3340)，待合并。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | 修复状态 |
|--------|-------|------|----------|
| 🔴 高 | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP 连接失败导致 Agent Loop 挂死，界面完全无响应 | 无 PR |
| 🟠 中 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | 长会话历史下 Web UI 输入框卡顿 | 无 PR，标记 `stale` |
| 🟢 低 | [#3338](https://github.com/sipeed/picoclaw/issues/3338) | Slack 媒体上传文件尺寸为 0 被拒绝 | 已有 PR [#3340](https://github.com/sipeed/picoclaw/pull/3340)，待合并 |

**稳定性结论：** 今日报告 3 个 Bug，其中 2 个为中长期未解问题（`stale` 标记），1 个已有社区修复方案。MCP 挂死问题属于生产环境高风险缺陷，建议优先处理。

---

## 6. 功能请求与路线图信号

- [#3345](https://github.com/sipeed/picoclaw/issues/3345) — **Proposal: lightweight PicoClaw worker mode for household edge compute**
  - **作者：** `kvnloo` | 创建：2026-08-25 | 0 评论
  - **核心提案：** 为低资源设备（RISC-V/ARM/MIPS 开发板、树莓派、旧 Android 手机，可用内存约 10–20 MB）设计轻量级 Worker 模式，支持分布式 Agent 架构。
  - **路线图信号：** 该提案切中 PicoClaw 的硬件适配定位，反映用户对**边缘侧部署**的强烈需求。若维护者采纳，可能推动项目向"中心-边缘协同"架构演进。目前处于提案阶段，尚未进入开发。

---

## 7. 用户反馈摘要

| 痛点场景 | 来源 | 反馈提炼 |
|----------|------|----------|
| Web UI 输入卡顿 | #3281 | 长会话历史导致前端性能劣化，影响核心交互流畅度 |
| Agent 挂死 | #3269 | MCP 连接异常处理缺失，错误传播至 UI 层导致假死 |
| Slack 媒体上传失败 | #3338 | SDK 校验严格，项目方遗漏必要参数，集成体验断裂 |
| 边缘设备部署需求 | #3345 | 用户拥有多类低成本硬件，期望 PicoClaw 成为分布式 Agent 的端侧节点 |

**整体情绪：** 用户对产品定位（轻量、边缘友好）有明确认同，但对稳定性（MCP 挂死）和基础体验（输入卡顿、媒体上传）的容忍度较低，亟需维护者加快修复节奏。

---

## 8. 待处理积压

| Issue/PR | 状态 | 风险 | 建议 |
|----------|------|------|------|
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) | `stale` · 7 评论 | 高 | Web UI 性能问题影响面广，建议维护者复评并排入下一迭代 |
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) | OPEN · 7 评论 | 极高 | MCP 挂死为生产级缺陷，建议优先分配修复资源 |
| [#3338](https://github.com/sipeed/picoclaw/issues/3338) | `stale` · 2 评论 | 中 | 修复 PR [#3340](https://github.com/sipeed/picoclaw/pull/3340) 已就绪，建议尽快合并 |
| [#3340](https://github.com/sipeed/picoclaw/pull/3340) | `stale` · OPEN | 低 | 小补丁，建议作为快速合并项推进 |

---

**日报生成时间：** 2026-08-26  
**数据覆盖：** 过去 24 小时（2026-08-25 至 2026-08-26）

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# 📊 NanoClaw 项目日报 — 2026-08-26

---

## 1. 今日速览

NanoClaw 今日保持高频开发节奏，24小时内共产生 5 条 Issue 和 50 条 PR 更新（34 待合并 / 16 已合并），活跃度过剩且集中在 **core-team** 与外部贡献者协同推进。无新版本发布，但大量合并围绕基础设施加固展开：项目文档组装、容器生命周期管理、认证安全强化。整体项目健康度良好，核心维护者 `amit-shafnir` 单日提交密集，呈现"基建集中重构"态势。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 今日合并 / 关闭的重要 PR（16 条）

| PR | 类型 | 摘要 |
|---|---|---|
| [#3544](https://github.com/nanocoai/nanoclaw/pull/3544) | core-team | Slack 显式房间交接（room handoff）功能上线，含 bot mention 校验逻辑 |
| [#3540](https://github.com/nanocoai/nanoclaw/pull/3540) | core-team | 修复 OpenCode 代理会话 cwd 指向错误，使其正确运行在 agent workspace 内 |
| [#3539](https://github.com/nanocoai/nanoclaw/pull/3539) | core-team | Codex 复用 trunk 共享 composer，删除重复实现 |
| [#3536](https://github.com/nanocoai/nanoclaw/pull/3536) | core-team | 将所有指令源内联到单一 project document，解决 Claude Code 安全门控导致 `@` import 拒绝的问题 |
| [#3537](https://github.com/nanocoai/nanoclaw/pull/3537) | core-team | 与 #3539 同构 Codex composer 重构（双分支） |
| [#2656](https://github.com/nanocoai/nanoclaw/pull/2656) | fix | `add-mnemon` 将 setup 调用从 `entrypoint.sh` 移至 `main()`，修复 host 覆盖 ENTRYPOINT 后 mnemon hooks 永不注册的长期 bug |
| [#3542](https://github.com/nanocoai/nanoclaw/pull/3542) | fix | 启动时清除 `container_status` 漂移，防止旧状态误导健康检查 |

**进展评估：** 今日合并以"修复性重构"为主，核心指向三个方向：① 统一 project document 组装逻辑；② 修复 agent workspace 路径错误；③ 完善容器生命周期状态机。项目从"功能扩展期"向"架构收敛期"过渡。

---

## 4. 社区热点

### 高关注 Issues

| Issue | 标题 | 热度分析 |
|---|---|---|
| [#3538](https://github.com/nanocoai/nanoclaw/issues/3538) | 提案：将 NanoClaw 容器作为家庭边缘 worker 使用 | 🔥 用户希望利用闲置 PC/NAS 构建家庭级 AI 边缘集群，反映社区对"去中心化部署"的强烈诉求 |
| [#3543](https://github.com/nanocoai/nanoclaw/issues/3543) | `add-dial` 中 email 未加引号导致 Shell 元字符注入 | ⚠️ 安全问题，apostrophe email 可绕过输入校验并执行任意命令，建议优先处理 |

### 高关注 PRs

| PR | 标题 | 热度分析 |
|---|---|---|
| [#2431](https://github.com/nanocoai/nanoclaw/pull/2431) | Slack 条件化线程策略（DM 不折叠为 thread） | 开放数月，`jumprope-jesse` 提出更精细的 Slack 交互策略，仍待合并 |
| [#3298](https://github.com/nanocoai/nanoclaw/pull/3298) | 新增本地 Web Chat 渠道 | 解决"无需外部账号即可试用/演示"的核心痛点，具备高用户价值 |
| [#3528](https://github.com/nanocoai/nanoclaw/pull/3528) | Runner lease-id 声明、重启重叠保护、incarnation 门控 | 容器编排稳定性基础设施，建立在三个已验证分支之上，预计即将合并 |

---

## 5. Bug 与稳定性

| 严重程度 | Issue/PR | 描述 | 状态 |
|---|---|---|---|
| 🔴 高 | [#3543](https://github.com/nanocoai/nanoclaw/issues/3543) | `add-dial` skill 将 `{{owner_email}}` 未加引号传入 `bash -c`，apostrophe 可绕过 `validate` 正则并注入任意 shell 命令 | 无 fix PR |
| 🟠 中 | [#3535](https://github.com/nanocoai/nanoclaw/issues/3535) | `add-vercel` skill 的 rsync 会覆盖 spawn 阶段的 symlink，导致 session 间 skill 同步失效 | 无 fix PR |
| 🟠 中 | [#3532](https://github.com/nanocoai/nanoclaw/issues/3532) | `add-*-tool` per-agent 范围限定不涵盖后续新建的 agent group，新 group 默认获得工具权限 | 无 fix PR |
| 🟡 低 | [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) | `update-nanoclaw` skill 刷新时误判本地 adapter 为 skill，导致本地适配器被覆盖或校验失败；无 opt-out 选项 | 无 fix PR |

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 信号强度 | 备注 |
|---|---|---|---|
| 家庭边缘部署（多 PC/NAS 组网） | [#3538](https://github.com/nanocoai/nanoclaw/issues/3538) | ⭐⭐⭐ | 概念提案，尚未有核心维护者回应，需进一步设计 |
| 本地 Web Chat（无需外部渠道账号） | [#3298](https://github.com/nanocoai/nanoclaw/pull/3298) | ⭐⭐⭐⭐ | PR 已提交且规范，预计下一版本纳入 |
| 结构化 Setup 驱动协议 | [#3485](https://github.com/nanocoai/nanoclaw/pull/3485) | ⭐⭐⭐⭐ | 使外部程序可编程驱动安装向导，是自动化部署的基础设施 |
| 时区预置（`--tz`） | [#3487](https://github.com/nanocoai/nanoclaw/pull/3487) | ⭐⭐⭐ | 完善 setup 自动化能力 |
| Host 健康状态结构化暴露 | [#3482](https://github.com/nanocoai/nanoclaw/pull/3482) | ⭐⭐⭐⭐ | 统一的 host CLI 只读查询接口，运维友好 |

**路线图判断：** 今日合并的 PR 群高度集中于 setup 自动化、项目文档内联、容器编排稳定性三个方向，暗示下一版本将围绕"**可运维性**"和"**本地化部署体验**"推进。

---

## 7. 用户反馈摘要

- **安全隐忧突出：** Issue #3543 揭示 skill 脚本中存在未转义的 shell 注入风险，用户期待 core-team 对 skill 安全性审查加强。
- **部署灵活性诉求：** #3538 反映用户不愿额外购买 GPU 或云服务，希望将自有闲置设备纳入 NanoClaw 集群，是社区"去中心化"愿景的直接体现。
- **本地适配器保护：** #3529 表达用户对 skill 刷新机制"一刀切"覆盖本地代码的不满，诉求增加 opt-out 机制。
- **per-agent 权限漏洞：** #3532 指出 `add-*-tool` 的范围限定逻辑遗漏新建 agent，存在权限扩散风险。
- **本地试用门槛：** #3298 直接指出当前所有渠道均需外部账号，阻碍新用户体验，本地 Web Chat 是解决此痛点的自然方案。

---

## 8. 待处理积压

| 条目 | 类型 | 创建时间 | 备注 |
|---|---|---|---|
| [#2431](https://github.com/nanocoai/nanoclaw/pull/2431) | PR（Feature） | 2026-05-12 | 跨季度未合并，Slack 条件化线程策略，建议 core-team 评估优先级 |
| [#3543](https://github.com/nanocoai/nanoclaw/issues/3543) | Issue（安全） | 2026-08-25 | Shell 注入，应优先修复 |
| [#3538](https://github.com/nanocoai/nanoclaw/issues/3538) | Issue（提案） | 2026-08-25 | 家庭边缘部署，需架构评估 |

---

> 📅 报告生成时间：2026-08-26 | 数据来源：[nanocoai/nanoclaw](https://github.com/nanocoai/nanoclaw) GitHub API

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目动态日报 — 2026-08-26

---

## 1. 今日速览

NullClaw 在过去 24 小时内活跃度较低，仅有 1 条新 Issue 提交，无 PR 更新及版本发布。社区处于相对平静期，核心维护者暂无代码合并活动。新开 Issue #994 聚焦于边缘网格（edge mesh）的 RuntimeAdapter 优化，显示用户对低功耗硬件部署场景的关注仍在持续。整体项目健康度：🟡 低活跃期，但技术讨论方向明确。

---

## 2. 版本发布

今日无新版本发布，上一版本状态维持不变。

---

## 3. 项目进展

无 PR 合并或关闭活动，今日无功能推进记录。

---

## 4. 社区热点

**Issue #994 — Household edge mesh using RuntimeAdapter workers and signed receipts**
- 🔗 https://github.com/nullclaw/nullclaw/issues/994
- 状态：OPEN | 评论：0 | 👍：0
- 作者：kvnloo | 创建时间：2026-08-25

> **分析**：该 Issue 是今日唯一社区讨论焦点，提出利用 NullClaw 已有的 RuntimeAdapter、Peripheral vtable、Docker/WASM 适配器等 primitives，构建面向家庭边缘设备（闲置 PC、笔记本等）的轻量级 mesh 网络。诉求核心是**硬件发现自动化**与**严格的内存/体积约束**，反映了用户对低功耗部署场景的强烈兴趣，也侧面印证了 NullClaw 的设计目标与社区需求方向一致。

---

## 5. Bug 与稳定性

今日无 Bug 报告，无崩溃或回归问题记录。

---

## 6. 功能请求与路线图信号

**Issue #994** 提出的家庭边缘 mesh 方案可作为未来路线图的重要参考信号：
- **RuntimeAdapter 作为 worker 调度层**的扩展使用场景
- **signed receipts** 在边缘节点身份验证中的潜在应用
- 对**硬件 discovery 能力**的增强需求

建议维护者关注该 Issue 后续评论，若用户提出 PoC 或 PR，可作为下一版本的功能候选。

---

## 7. 用户反馈摘要

今日无新评论反馈。Issue #994 摘要中体现了以下用户痛点与满意点：

| 维度 | 内容 |
|------|------|
| ✅ 满意点 | NullClaw 已有的 primitives 设计（Zig runtime、vtable、WASM/Docker 适配器）被用户认可 |
| 🎯 使用场景 | 多设备家庭边缘计算、闲置硬件复用 |
| 🔧 潜在痛点 | 硬件发现、隧道、信道管理的易用性可能仍有优化空间 |

---

## 8. 待处理积压

| 类型 | Issue/PR | 状态 | 建议 |
|------|----------|------|------|
| 功能讨论 | [#994](https://github.com/nullclaw/nullclaw/issues/994) | OPEN（今日新开） | 暂无积压，建议维护者在近期对社区需求进行回应或标注优先级 |

---

**报告生成时间**：2026-08-26  
**数据来源**：GitHub API (github.com/nullclaw/nullclaw)  
**下次更新建议**：24 小时后或有新活动触发时自动更新

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报 — 2026-08-26

> 数据来源：GitHub API | 统计周期：2026-08-25 至 2026-08-26

---

## 1. 今日速览

过去24小时 IronClaw 项目保持**中高活跃度**，共产生 37 条 Issue 和 24 条 PR，其中 10 条 PR 已合并/关闭，4 条 Issue 已解决，整体 **合并率约 42%**，属于健康水平。核心进展集中在三条主线：**CI/CD 流水线优化**（nextest 迁移、pre-flight gates、queue convergence 全部落地）、**通知中心持久化**（legacy fallback 已退役，新增多类通知覆盖）以及 **WebUI 组件统一化**（Panel/Form 组件迁移持续推进）。性能层面出现一起严重 Bug（Issue #7891），揭示了 MIME 头 24 KiB 盲目注入 prompt 导致的 19 秒推理开销，相关修复 PR #7896 已提出。项目整体向前推进约一个迭代，无新版本发布。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 作者 | 内容 | 关联 Issue |
|---|---|---|---|
| [#7817](https://github.com/nearai/ironclaw/pull/7817) | henrypark133 | 引入 `cargo-nextest` 替换顺序 `cargo test`，实现全量失败信号和 PR unthrottle | 关闭 #7799 |
| [#7809](https://github.com/nearai/ironclaw/pull/7809) | henrypark133 | 建立单一 `preflight-gates.sh` 作为确定性门禁清单，支持 pre-push hook 自打印 REPRO | 关联 #7801 |
| [#7819](https://github.com/nearai/ironclaw/pull/7819) | henrypark133 | PR/queue 检查收敛：PR 阶段增加 default-features clippy，消灭三类 "queue-only failure" | 关闭 #7800 |
| [#7894](https://github.com/nearai/ironclaw/pull/7894) | henrypark133 | 减少 CI checkout 传输体积，partial-clone 过滤历史 blob，Tests 事件改用 depth-1 checkout | — |
| [#7818](https://github.com/nearai/ironclaw/pull/7818) | henrypark133 | Subagent 后台模式：spawn receipt、per-child delivery、activation、healing sweeps | 关联 #7788 |
| [#7846](https://github.com/nearai/ironclaw/pull/7846) | italic-jinxin | 退役通知中心 legacy approval fallback，durable inbox 成为唯一数据源 | 关联 #7687/#7706 |
| [#7820](https://github.com/nearai/ironclaw/pull/7820) | henrypark133 | Scope-isolation 测试套件整合探针（T2 follow-up） | 关联 #7799 |
| [#7816](https://github.com/nearai/ironclaw/pull/7816) | rdisandro | OOBE 建议抽屉新增 Refresh 和 Connect 入口 | 关联 #7815 |
| [#7861](https://github.com/nearai/ironclaw/pull/7861) | henrypark133 | 修复安装/激活路径中 Telegram 设备链接引导缺失的问题 | 关联 #7862/#7853 |
| [#7859](https://github.com/nearai/ironclaw/pull/7859) | thisisjoshford | Changelog 从侧边栏移至 navbar tab，对齐 Mintlify 标准模式 | — |

**进展总结：** CI 流水线今日完成大规模整合（nextest + preflight + convergence + checkout 瘦身），可视为一个完整的基础设施迭代；通知中心 legacy 代码正式退役，架构更清晰；subagent 后台模式交付，扩展了异步执行能力。

---

## 4. 社区热点

### 🔥 Issue #7732 — Persistent per-user sandbox with iron-proxy
- **作者：** serrrfirat | **评论：9** | **标签：** epic, v1.4.0, roadmap
- **链接：** [Issue #7732](https://github.com/nearai/ironclaw/issues/7732)
- **热度原因：** 这是 v1.4.0 核心史诗级 Issue，涉及 Reborn 架构中每个用户沙箱的持久化方案。当前实现每句 shell 命令启动/销毁一个 Docker 容器，用户希望 `/workspace` 能按 `(tenant, user)` 持久保留。9 条评论表明社区（含维护者）在持续讨论架构取舍，是近期最核心的设计决策点。

### 🔥 Issue #7799 — CI expedite T2: nextest pipeline
- **作者：** henrypark133 | **评论：4** | **状态：** 已关闭（#7817 已合入）
- **链接：** [Issue #7799](https://github.com/nearai/ironclaw/issues/7799)
- **热度原因：** CI 性能优化的关键 Issue，4 条评论记录了从 plan → PR #7817 → follow-up #7820 的完整推进链，是今日最活跃的基础设施讨论。

### 🔥 Issue #7862 — Device link fails with generic error for unconfigured Telegram
- **作者：** henrypark133 | **评论：3** | **风险：** medium
- **链接：** [Issue #7862](https://github.com/nearai/ironclaw/issues/7862)
- **热度原因：** 用户配置 Telegram API ID/hash 缺失时，设备链接抛出模糊的 "Something went wrong" 错误，而非明确提示配置项缺失。社区对错误信息质量敏感，PR #7861 已修复 install/activate 路径，但 Issue #7887 指出扩展查找路径仍有遗留问题。

### Issue #7038 — Design System Phase 1（已关闭）
- **作者：** rdisandro | **评论：3** | **状态：** 已关闭
- **链接：** [Issue #7038](https://github.com/nearai/ironclaw/issues/7038)
- **热度原因：** 设计系统第一阶段收尾，Phase 2–5 已拆分至 #7781/#7782，标志着 WebUI 设计体系进入后半程。

---

## 5. Bug 与稳定性

| 严重度 | Issue | 标题 | 状态 | Fix PR |
|---|---|---|---|---|
| 🔴 高 | [#7891](https://github.com/nearai/ironclaw/issues/7891) | `gmail.get_message` 调用中未投影的 capability payload 将 24 KiB MIME 头注入 prompt，单次推理消耗 19.2s（总共 19.7s） | Open | **#7896**（已提出） |
| 🔴 高 | [#7892](https://github.com/nearai/ironclaw/issues/7892) | Deferred tool 被找到 15 次但从未被调用，123s 的 run 中模型发出 31 次能力调用仅 4 个不同 pair | Open | 无 |
| 🟡 中 | [#7862](https://github.com/nearai/ironclaw/issues/7862) | Telegram 设备链接失败时错误信息过于模糊 | Open | PR #7861 已合入 install 路径，#7887 仍有遗留 |
| 🟡 中 | [#7888](https://github.com/nearai/ironclaw/issues/7888) | 多实例环境下 `logs` 命令无限挂起 | Open | 无 |
| 🟢 低 | [#7867](https://github.com/nearai/ironclaw/issues/7867) | WebUI composer 缺少语音输入支持（功能缺口，非 Bug） | Open | 无 |

**稳定性评估：** 发现 2 个高严重度 Bug，均与 agent loop 性能和工具调用效率相关。#7891 的修复 PR #7896（将盲目字节切片替换为结构感知的 4 KiB 预览边界）已提出，预计可显著改善推理开销。#7892 反映 deferred tool 机制存在逻辑缺陷，尚待修复。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 内容 | 纳入下一版本可能性 |
|---|---|---|---|
| [#4625](https://github.com/nearai/ironclaw/issues/4625) | 功能请求 | Slack 频道级个人/团队 agent 路由（Phase 1: Slack-as-channel） | 🟢 高 — 标为 `suggested_P1`，已标记 epic/roadmap |
| [#7871](https://github.com/nearai/ironclaw/issues/7871) | 功能请求 | Slack-to-console bridge + 富交互 Slack UX | 🟢 高 — 标为 `epic, roadmap`，解决 Slack 目前仅作为薄传输层的问题 |
| [#7867](https://github.com/nearai/ironclaw/issues/7867) | 功能请求 | WebUI composer 语音输入 | 🟡 中 — 技术阻塞已明确（非模型层），需浏览器 API 集成 |
| [#7895](https://github.com/nearai/ironclaw/issues/7895) | 功能请求 | Settings UI 新增 personality (agent.md) 编辑区 | 🟡 中 — 用户痛点明确，但尚未关联到具体 epic |
| [#7893](https://github.com/nearai/ironclaw/issues/7893) | 功能请求 | Per-automation lessons file — 跨 run 持久化学习记录 | 🟡 中 — 标为 `enhancement, reborn`，解决 "每次 run 从零开始" 的痛点 |
| [#7889](https://github.com/nearai/ironclaw/issues/7889) | 功能请求 | Scheduler/Orchestrator 扩展支持 opt-in remote edge workers | 🟡 中 — RFC 阶段，解决 worker pool 单主机限制 |
| [#7885](https://github.com/nearai/ironclaw/issues/7885) + [#7886](https://github.com/nearai/ironclaw/pull/7886) | 安全/质量 | OpenSSF Scorecard 工作流配置 | 🟢 高 — PR 已提出，属于发布前基础设施项 |

**路线图信号：** v1.4.0 的核心叙事围绕 **Slack 作为一等公民渠道**（#4625 + #7871）、**设计系统 Phase 3–5**（#7781/#7782）以及 **持久化沙箱**（#7732）展开。#7893（跨 run 学习）和 #7889（远程 edge workers）属于架构级增强，可能顺延至 v1.5.0。

---

## 7. 用户反馈摘要

**痛点：**
- **推理效率问题突出：** #7891 和 #7892 均反映 agent loop 在实际运行中存在严重的效率问题——前者是原始 MIME 数据盲目注入 prompt，后者是 deferred tool 反复查找但永不执行，导致 79s/86s/123s 的无效消耗。用户期望 agent 更"聪明"，但当前工具发现机制存在缺陷。
- **Telegram 设备链接体验差：** #7862 用户反馈模糊错误信息，#7887 指出扩展查找路径仍生成误导性建议（"it's not available as a tool"）。多重路径的错误处理不一致。
- **Logs 命令在多实例环境下挂起：** #7888 两名用户独立确认，涉及生产环境可用性。
- **Slack 仅作为"薄传输层"：** #4625/#7871 用户对比其他渠道，认为 Slack 缺少 durable continuity、run metadata 和 quick follow-up actions，体验落后于 WebUI。
- **语音输入缺失：** #7867 用户指出 Telegram/Slack 均已支持语音，唯独 WebUI 不支持，影响长文本输入效率。

**满意点：**
- CI 流水线显著优化（nextest + 全量失败信号 + queue convergence），开发者体验改善。
- 通知中心从 approval-only 升级为持久化 inbox（#7687 已关闭，后续 PR 持续扩展覆盖范围）。
- WebUI 组件统一化持续推进（Panel、FormField、SearchField 共享组件逐步替换 legacy 实现）。
- OOBE 建议抽屉体验改善（#7816 新增 refresh/connect 入口）。

---

## 8. 待处理积压

| Issue/PR | 积压原因 | 建议关注 |
|---|---|---|
| [#7892](https://github.com/nearai/ironclaw/issues/7892) — Deferred tool 15x 查找永不调用 | 高严重度 Bug，已报告数小时无响应，涉及 agent loop 核心逻辑 | 🔴 优先处理 |
| [#7888](https://github.com/nearai/ironclaw/issues/7888) — Logs 命令无限挂起 | 多实例复现，影响生产环境运维，尚无 fix PR | 🔴 优先处理 |
| [#7891](https://github.com/nearai/ironclaw/issues/7891) — 24 KiB MIME 头注入 prompt | 已有 PR #7896 提出，但状态仍为 Open，需 review 合并 | 🟡 跟进 PR |
| [#7887](https://github.com/nearai/ironclaw/issues/7887) — Telegram 设备链接引导路径遗留 | PR #7861 修复了 install/activate 路径，但 extension lookup 路径仍有问题 | 🟡 跟进 |
| [#7491](https://github.com/nearai/ironclaw/pull/7491) — OMP core-tool contract | XL 规模 PR，自 08-11 创建以来未合并，涉及 coding tool 的统一重构 | 🟡 长期未合 |
| [#7889](https://github.com/nearai/ironclaw/issues/7889) — Remote edge workers RFC | RFC 阶段，尚未进入实现 | 🟢 关注进展 |
| [#7884](https://github.com/nearai/ironclaw/pull/7884) — 解锁卡住的 threads | 提出 wall-clock occupancy bound 方案，状态 Open | 🟡 等待 review |

---



</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目日报 — 2026-08-26

---

## 1. 今日速览

LobsterAI 在过去24小时内保持**高活跃度**，共完成 9 个 PR 合并，释放 2 个新版本（2026.8.25 与 2026.8.21），迭代节奏紧凑。核心进展集中在**资料库功能增强**（本地产物刷新优化、预览交互区分、埋点体系完善）与**付费转化链路优化**（模型目录展示、试用提示体验调整）。社区侧仅 1 条开放 Issue，无重大 Bug 或稳定性问题上报，项目整体健康状况良好。

---

## 2. 版本发布

### v2026.8.25
- 库（Library）功能持续增强，重点优化跨平台缩略图加载与本地产物生命周期管理
- 改善本地产物预览体验与交互操作流畅度
- 相关 PR：[#2513](https://github.com/netease-youdao/LobsterAI/pull/2513)、[#2524](https://github.com/netease-youdao/LobsterAI/pull/2524)

### v2026.8.21
- DSH（桌面壳）新增启用开关与工作台打开行为的使用分析埋点
- DSH 版本升级至 `0.1.1-rc.1`，进行架构重构
- 相关 PR：[#2515](https://github.com/netease-youdao/LobsterAI/pull/2515)、[#2516](https://github.com/netease-youdao/LobsterAI/pull/2516)

> **破坏性变更提示**：本批次版本均为功能增强与体验优化，无已知破坏性变更。

---

## 3. 项目进展

今日合并/关闭的关键 PR 如下：

| PR | 类型 | 内容 |
|----|------|------|
| [#2531](https://github.com/netease-youdao/LobsterAI/pull/2531) | 修复 | 本地产物后台刷新闪烁问题，通过拆分加载状态、新增批量查询接口、原位合并变更实现 |
| [#2533](https://github.com/netease-youdao/LobsterAI/pull/2533) | 体验 | 区分 HTML 网页与本地产物服务的预览展示样式与图标 |
| [#2530](https://github.com/netease-youdao/LobsterAI/pull/2530) | 功能 | 设置页新增「计划模型目录」选项卡，展示定价/文本/视频模型卡片 |
| [#2529](https://github.com/netease-youdao/LobsterAI/pull/2529) | 数据 | 完善资料库埋点体系，覆盖曝光、搜索、收藏、刷新及付费转化归因 |
| [#2532](https://github.com/netease-youdao/LobsterAI/pull/2532) | 体验 | 登录推广提示5秒后自动淡出，状态变化时清理计时器 |

**整体评估**：今日开发聚焦于资料库模块体验打磨与付费转化链路完善，9 个 PR 全部合并，项目向稳定化与商业化方向稳步推进。

---

## 4. 社区热点

| Issue/PR | 状态 | 热度指标 | 分析 |
|----------|------|----------|------|
| [#2536](https://github.com/netease-youdao/LobsterAI/issues/2536) | OPEN | 1 评论，0 👍 | 用户反馈微信群已满，期望开通新群。反映社区运营需求增长，但尚未形成大规模讨论。 |
| [#1159](https://github.com/netease-youdao/LobsterAI/pull/1159) | OPEN（stale） | 长期未响应 | 会话分支（Session Fork）功能请求，用户希望从当前会话创建分支进行探索性对话，避免破坏原始上下文。属于高价值功能需求，但已进入 stale 状态，需维护者评估是否继续推进。 |

---

## 5. Bug 与稳定性

今日无新增严重 Bug 或崩溃报告。

| 问题 | 严重程度 | 修复状态 |
|------|----------|----------|
| 本地产物后台刷新整页闪烁 | 中 | ✅ 已修复 [#2531](https://github.com/netease-youdao/LobsterAI/pull/2531) |
| 登录推广提示长期残留 | 低 | ✅ 已修复 [#2532](https://github.com/netease-youdao/LobsterAI/pull/2532) |

项目稳定性表现良好，未发现回归问题。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 路线图信号 |
|------|------|------------|
| 会话分支（Session Fork） | [#1159](https://github.com/netease-youdao/LobsterAI/pull/1159) | 用户明确提出「实验不同对话方向时保留原始状态」的诉求，符合多分支对话探索场景，建议纳入下一版本评估 |
| 计划模型目录展示 | [#2530](https://github.com/netease-youdao/LobsterAI/pull/2530) | 已合并，商业化功能持续落地，后续可能扩展更多模型定价展示 |
| 资料库埋点完善 | [#2529](https://github.com/netease-youdao/LobsterAI/pull/2529) | 已合并，数据驱动决策能力增强，预计后续将开放更多数据分析面板 |

---

## 7. 用户反馈摘要

- **正面反馈**：无明显负面评价，资料库体验优化（刷新去闪烁、预览区分）预计提升用户满意度。
- **痛点**：微信群容量已达上限（[#2536](https://github.com/netease-youdao/LobsterAI/issues/2536)），用户活跃交流需求未被满足，建议运营侧扩容或新增群入口。
- **场景需求**：会话分支功能（[#1159](https://github.com/netease-youdao/LobsterAI/pull/1159)）反映用户希望在不破坏原始对话的前提下进行多路径探索，属于 Cowork 协作场景的核心需求。

---

## 8. 待处理积压

| 条目 | 状态 | 创建时间 | 建议 |
|------|------|----------|------|
| [#1159](https://github.com/netease-youdao/LobsterAI/pull/1159) — 会话分支功能 | OPEN（stale） | 2026-03-31 | 超5个月未推进，建议维护者评估是否继续或关闭 |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Electron 依赖升级 | OPEN | 2026-04-02 | Dependabot PR，electron 从 40.2.1 升级至 43.4.1，存在潜在兼容性风险，建议测试后合并 |

---

**日报总结**：LobsterAI 项目今日健康度良好，迭代节奏稳定，资料库与商业化功能持续完善。需关注会话分支功能的技术评估与 Electron 依赖升级的兼容性验证。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 | 2026-08-26

---

## 1. 今日速览

Moltis 项目今日保持中等活跃度，过去24小时内新增 2 条 Issue、5 条 PR，整体开发节奏稳健。其中 2 条 PR 已合并/关闭，主要聚焦于工具层修复与上下文管理优化，无新版本发布。Kubernetes sandbox 支持持续推进，同时 OpenAI 兼容性修复显示项目正在积极适配主流模型提供商的严格校验要求。社区对多渠道消息一致性的需求较为强烈，#1224 和 #1243 均与此相关。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（2 条）

| PR | 标题 | 作者 | 进展说明 |
|----|------|------|----------|
| [#1245](https://github.com/moltis-org/moltis/pull/1245) | fix(tools): validate Brave search parameters | @rubenssoto | 修复 Brave 搜索工具的参数校验逻辑，新增地区/语言/UI语言的枚举约束与 fallback 机制，提升工具调用的稳定性和可预期性 |
| [#1243](https://github.com/moltis-org/moltis/pull/1243) | fix(cron): preserve delivered channel context | @rubenssoto | 解决定时任务通过 WhatsApp 等渠道发送消息后丢失对话上下文的问题，将最终回复追加至目标渠道的现有会话中，改善多轮交互体验 |

**整体判断**：今日合并的 PR 均为 bug 修复类，侧重于工具层的健壮性和渠道上下文管理，项目整体在稳定性层面小幅推进。

---

## 4. 社区热点

| 类型 | 编号 | 标题 | 活跃度 | 分析 |
|------|------|------|--------|------|
| Issue | [#1118](https://github.com/moltis-org/moltis/issues/1118) | Add Kubernetes-native sandbox backend with runtimeClassName support | 创建较早（2026-06-12），今日更新，2 条评论，1 个 👍 | 用户明确提出对 **K8s 原生 sandbox** 的需求，支持 Kata Containers / gVisor 等 OCI 运行时以实现 VM 级隔离，反映社区对 Agent 执行安全性的高度重视 |
| PR | [#1199](https://github.com/moltis-org/moltis/pull/1199) | Add Coder remote workspace sandbox support | 8月15日创建，今日更新，0 评论 | 另一位用户提出 **Coder 远程工作空间**作为替代 sandbox 方案，与 #1118 形成互补，说明用户期望多种隔离后端可选 |
| Issue | [#1224](https://github.com/moltis-org/moltis/issues/1224) | Tools stop working in shared Slack channels | 4天创建，今日更新 | 用户报告 Slack 共享频道中工具失效，反映多渠道集成仍存在稳定性盲区 |

**热点分析**：社区当前最核心的诉求集中在 **隔离环境的安全性**（#1118、#1199）和 **多渠道工具的可靠性**（#1224、#1243）。两条 sandbox 方案 PR 同时存在，表明用户群体对执行环境隔离有多样化期望。

---

## 5. Bug 与稳定性

| 严重程度 | Issue/PR | 标题 | 状态 | 备注 |
|----------|----------|------|------|------|
| 中 | [#1224](https://github.com/moltis-org/moltis/issues/1224) | Tools stop working in shared Slack channels | 已关闭 | 用户报告 Slack 共享频道中工具不可用，未见关联修复 PR，需确认是否已解决或需跟进 |
| 低（已修复） | [#1243](https://github.com/moltis-org/moltis/pull/1243) | fix(cron): preserve delivered channel context | 已合并 | 定时任务上下文丢失问题已修复 |

---

## 6. 功能请求与路线图信号

| 类型 | 编号 | 标题 | 信号强度 | 分析 |
|------|------|------|----------|------|
| 功能请求 | [#1118](https://github.com/moltis-org/moltis/issues/1118) | Kubernetes-native sandbox backend | ⭐⭐⭐ 高 | 需求明确、有具体技术方案，且已有相关 PR（#1199 Coder sandbox）呼应，很可能纳入下一版本 |
| PR | [#1199](https://github.com/moltis-org/moltis/pull/1199) | Add Coder remote workspace sandbox support | ⭐⭐ 中 | 提供另一条 sandbox 路径，若 #1118 的 K8s 方案优先，此 PR 可能作为备选或并列支持 |
| PR | [#1244](https://github.com/moltis-org/moltis/pull/1244) | Fix Fastmail MCP OAuth scope registration | ⭐ 低 | 修复 MCP OAuth 注册问题，属于已有功能的完善，不太可能独立成版本特性 |
| PR | [#1232](https://github.com/moltis-org/moltis/pull/1232) | fix(tools): make object schemas OpenAI-safe | ⭐ 低 | OpenAI 兼容性修复，属于适配层改进 |

**路线图判断**：sandbox 隔离能力是近期最明确的功能方向，K8s 原生后端和 Coder 远程工作空间两条路径可能并存。

---

## 7. 用户反馈摘要

- **安全隔离需求强烈**：#1118 用户详细描述了对 VM 级隔离（Kata Containers、gVisor）的期望，说明当前 sandbox 方案无法满足部分企业用户对执行环境安全性的要求。
- **多渠道一致性待改善**：#1224 报告 Slack 共享频道工具失效，#1243 修复了 WhatsApp 渠道的上下文丢失问题，反映出多渠道接入在工具调用和会话管理上仍有短板。
- **OpenAI 兼容性敏感**：#1232 用户反馈 OpenAI strict mode 下 object schema 兼容性问题，导致 Codex 发送空值，说明 Moltis 需要持续适配主流 LLM 提供商的 schema 校验规则。
- **Brave 搜索参数不够严谨**：#1245 用户主动提出参数校验改进，体现社区对工具参数规范性的关注。

---

## 8. 待处理积压

| 编号 | 类型 | 标题 | 创建时间 | 提醒 |
|------|------|------|----------|------|
| [#1199](https://github.com/moltis-org/moltis/pull/1199) | PR | Add Coder remote workspace sandbox support | 2026-08-15 | 已开放11天，无评论，建议维护者评估是否与 #1118 合并或并行支持 |
| [#1244](https://github.com/moltis-org/moltis/pull/1244) | PR | Fix Fastmail MCP OAuth scope registration | 2026-08-25 | 开放1天，建议跟进合并 |
| [#1232](https://github.com/moltis-org/moltis/pull/1232) | PR | fix(tools): make object schemas OpenAI-safe | 2026-08-22 | 开放4天，无评论，OpenAI 兼容性修复建议优先审核 |
| [#1224](https://github.com/moltis-org/moltis/issues/1224) | Issue | Tools stop working in shared Slack channels | 2026-08-21 | 已关闭但未见明确修复记录，建议确认根因并补充说明 |

---

**项目健康度评估**：🟡 中等偏上 — 开发节奏稳定，bug 修复及时，sandbox 安全方向社区呼声高，但部分 PR 响应周期较长，Slack 渠道稳定性有待加强。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-08-26

---

## 1. 今日速览

CoPaw 今日保持**高活跃度**，过去24小时共产生 33 条 Issue（19 新开/活跃，14 已关闭）和 50 条 PR（21 待合并，29 已合并/关闭），并发布 **v2.1.1-beta.3** 新版本。项目整体健康度良好，社区反馈集中体现于 SSE 序列化崩溃、内存泄漏、浏览器渲染性能等关键技术问题，开发者响应迅速，多 Bug 当日即被追踪或关闭。

---

## 2. 版本发布

### v2.1.1-beta.3（2026-08-26）

**更新内容：**
- `chore(console)`: 将 `@agentscope-ai/chat` pin 至 `1.1.72`（#7257）
- `docs(loop-engineering)`: 修复 PluginAPI 大小写命名（PluginApi → PluginAPI）（#7269）
- `test(integration)`: 扩展集成测试覆盖

**破坏性变更：** 无。

**迁移注意事项：**
- 若自定义插件使用 `PluginAPI` 命名引用，需同步更新为 `PluginApi`。
- 建议同步升级 `@agentscope-ai/chat` 至 `1.1.72` 以保持一致。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 | 状态 |
|----|------|------|------|
| #7276 | chore | 升级 AgentScope 至 `2.0.7` | ✅ 已合并 |
| #7300 | docs | 更新 Scroll Context Manager 博客 | ✅ 已关闭 |
| #2773 | feat | 自进化 Skill（Self-improving Agent Engine）| ✅ 已关闭 |
| #5414 | feat | Skill SOP 与判定规则解耦 | ✅ 已关闭 |
| #1228 | feat | 新增 `read_media` 工具（图像/视频/音频处理）| ✅ 已关闭 |
| #1525 | fix | Cron 失效时隔离持久化任务，避免启动崩溃 | ✅ 已关闭 |
| #4881 | feat | 新增 MiniMax M3 旗舰模型支持 | ✅ 已关闭 |
| #2304 | fix | 兼容返回 404 的模型列表接口（Anthropic兼容提供商）| ✅ 已关闭 |
| #1552 | feat | 自定义 Provider 支持 `custom_headers` | ✅ 已关闭 |

**项目推进评估：** 9 个重要 PR 今日关闭/合并，涵盖性能修复、新模型支持、安全加固和开发者体验改善，整体向前稳步推进。

---

## 4. 社区热点

### 高关注 Issue（按评论数排序）

| Issue | 类型 | 评论数 | 摘要 | 链接 |
|-------|------|--------|------|------|
| #338 | enhancement | 9 | 建议添加 webhook 功能，支持异步回调通知 | [#338](https://github.com/agentscope-ai/QwenPaw/issues/338) |
| #7258 | bug | 6 | 微信频道"显示思考过程"设置无效 | [#7258](https://github.com/agentscope-ai/QwenPaw/issues/7258) |
| #5720 | bug | 5 | v1.1.12.post2 内存泄漏（每分钟涨 5.5MB，64分钟后崩溃）| [#5720](https://github.com/agentscope-ai/QwenPaw/issues/5720) |
| #6810 | bug | 5 | Windows 安装程序未终止占用进程导致更新失败 | [#6810](https://github.com/agentscope-ai/QwenPaw/issues/6810) |
| #6273 | bug | 4 | Task tracking 与 same-session concurrency 行为不一致 | [#6273](https://github.com/agentscope-ai/QwenPaw/issues/6273) |
| #7261 | bug | 4 | **v2.1.1b2 SSE 序列化无限循环，CPU 100%，内存无限增长** | [#7261](https://github.com/agentscope-ai/QwenPaw/issues/7261) |
| #7218 | bug | 4 | 长文本/推理场景频繁出现 `peer closed connection` | [#7218](https://github.com/agentscope-ai/QwenPaw/issues/7218) |
| #7182 | enhancement | 4 | 建议新增 workspace-scoped Skill preload policy | [#7182](https://github.com/agentscope-ai/QwenPaw/issues/7182) |
| #7228 | bug | 4 | 应用市场已安装应用仍显示"安装"按钮 | [#7228](https://github.com/agentscope-ai/QwenPaw/issues/7228) |

**热点分析：**
- **#7261** 是最严重的稳定性问题，SSE 序列化死循环导致服务完全不可用，需优先关注。
- **#5720** 内存泄漏问题具有复现性，根因分析已定位（异步任务泄漏 + HTTP 会话不回收）。
- **#338** 社区对 webhook 需求持续存在，建议纳入后续路线图评估。

---

## 5. Bug 与稳定性

### 今日报告的重要 Bug（按严重程度排列）

| 严重程度 | Issue | 标题 | 状态 | 链接 |
|----------|-------|------|------|------|
| 🔴 严重 | #7261 | v2.1.1b2 SSE 序列化死循环，CPU 100%，内存无限增长 | ✅ 已关闭 | [#7261](https://github.com/agentscope-ai/QwenPaw/issues/7261) |
| 🔴 严重 | #7285 | 长对话导致浏览器严重卡顿，1-2分钟后系统无响应 | ✅ 已关闭 | [#7285](https://github.com/agentscope-ai/QwenPaw/issues/7285) |
| 🟠 高 | #7258 | 微信频道"显示思考过程"设置无效 | 🔄 待处理 | [#7258](https://github.com/agentscope-ai/QwenPaw/issues/7258) |
| 🟠 高 | #7218 | 长文本推理频繁出现连接中断 `peer closed connection` | 🔄 待处理 | [#7218](https://github.com/agentscope-ai/QwenPaw/issues/7218) |
| 🟠 高 | #6273 | Task tracking 与并发语义不一致 | 🔄 待处理 | [#6273](https://github.com/agentscope-ai/QwenPaw/issues/6273) |
| 🟡 中 | #5720 | 内存泄漏（异步任务 + HTTP 会话未回收） | ✅ 已关闭 | [#5720](https://github.com/agentscope-ai/QwenPaw/issues/5720) |
| 🟡 中 | #6810 | Windows 安装程序未终止占用进程 | 🔄 待处理 | [#6810](https://github.com/agentscope-ai/QwenPaw/issues/6810) |
| 🟡 中 | #7296 | OpenAI Responses 多轮对话 400 错误 | 🔄 待处理 | [#7296](https://github.com/agentscope-ai/QwenPaw/issues/7296) |
| 🟡 中 | #7266 | subAgent 找错文件夹路径 | 🔄 待处理 | [#7266](https://github.com/agentscope-ai/QwenPaw/issues/7266) |
| 🟢 低 | #7228 | 应用市场已安装仍显示"安装"按钮 | ✅ 已关闭 | [#7228](https://github.com/agentscope-ai/QwenPaw/issues/7228) |
| 🟢 低 | #7282 | Markdown 列表渲染垂直间距过大 | 🔄 待处理 | [#7282](https://github.com/agentscope-ai/QwenPaw/issues/7282) |
| 🟢 低 | #7297 | QQ 对话重启丢失最后聊天记忆 | 🔄 待处理 | [#7297](https://github.com/agentscope-ai/QwenPaw/issues/7297) |

**修复状态追踪：**
- #7261（SSE 死循环）和 #7285（浏览器卡顿）已关闭，预计在下个版本修复。
- #5720（内存泄漏）已关闭，根因分析完成，待 PR 修复。
- #7258、#7218、#6273 仍有待处理，需维护者关注。

---

## 6. 功能请求与路线图信号

| Issue | 需求描述 | 已有 PR 关联 | 纳入概率 |
|-------|----------|--------------|----------|
| #338 | Webhook 异步回调功能 | 无 | ⚠️ 中等 |
| #7182 | Workspace-scoped Skill preload policy | 无 | ✅ 高（技术可行，需求明确）|
| #7013 | 统一工具面板 + Web 预览 + 交互式终端 | 无 | ⚠️ 中等 |
| #7196 | 推理过程默认折叠可配置 | 无 | ✅ 高（用户反馈强烈）|
| #7280 | 执行完成的后台任务自动清除 | 无 | ✅ 高（低悬 fruit）|
| #7263 | 任务完成底栏橙色提醒 | 无 | ⚠️ 中等 |
| #7279 | 多选弹窗替代手动输入 | 无 | ⚠️ 中等 |
| #7287 | 零侵入"皮肤网关"定制方案 | 无 | ❌ 低（长期建议）|

**综合评估：**
- **#7196**（推理过程折叠）和 **#7280**（任务自动清除）用户呼声高且实现成本低，建议优先纳入。
- **#7182**（Skill preload policy）技术价值明确，可与现有 PR #7163（session thinking 模式）协同推进。
- **#338**（Webhook）需求明确但涉及架构变更，需评估后纳入路线图。

---

## 7. 用户反馈摘要

### 痛点

1. **内存与性能问题**：多用户反馈长会话导致内存持续增长（#5720、#7259）和浏览器卡顿（#7285、#7129），影响生产环境稳定性。
2. **SSE 死循环崩溃**：#7261 描述的问题导致服务完全不可用，CPU 100%，属于阻塞性 Bug。
3. **连接稳定性**：长文本推理场景频繁出现 `peer closed connection`（#7218），自定义模型超时设置不透明。
4. **UI/UX 细节**：应用市场状态显示错误（#7228）、Markdown 渲染异常（#7282）、侧边菜单无响应（#7262）等影响体验。

### 满意点

- 新版本 v2.1.1-beta.3 发布及时，社区响应迅速。
- 多个长期 Issue 已被关闭或追踪（#2773、#5414、#1228 等功能 PR 已合并）。
- 安全修复持续推进（#7119 主密钥文件权限修复）。

### 使用场景

- **企业数据分析师**：使用 MCP 查询时序数据、设备遥测数据（#7288），对上下文溢出敏感。
- **开发者/插件作者**：关注 Skill 开发体验和 Creator 工具链（#7274）。
- **多渠道用户**：微信、QQ、飞书等多渠道使用，对渠道稳定性要求高。

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| Issue | 创建时间 | 天数 | 类型 | 建议优先级 | 链接 |
|-------|----------|------|------|------------|------|
| #338 | 2026-03-02 | ~177天 | enhancement | 🟠 高 | [#338](https://github.com/agentscope-ai/QwenPaw/issues/338) |
| #6810 | 2026-08-07 | 19天 | bug | 🟠 高 | [#6810](https://github.com/agentscope-ai/QwenPaw/issues/6810) |
| #6273 | 2026-07-20 | 37天 | bug | 🟠 高 | [#6273](https://github.com/agentscope-ai/QwenPaw/issues/6273) |
| #5720 | 2026-07-02 | 55天 | bug | 🟡 中 | [#5720](https://github.com/agentscope-ai/QwenPaw/issues/5720) |
| #7296 | 2026-08-25 | 1天 | bug | 🟠 高 | [#7296](https://github.com/agentscope-ai/QwenPaw/issues/7296) |

### 待处理积压 PR

| PR | 类型 | 说明 | 链接 |
|----|------|------|------|
| #7163 | feat | Session 级 thinking 模式管理（Off/Low/Medium/High）| [#7163](https://github.com/agentscope-ai/QwenPaw/pull/7163) |
| #7190 | feat | qwenpaw-data PyPI 安装与 docker-compose 演示 | [#7190](https://github.com/agentscope-ai/QwenPaw/pull/7190) |
| #7293 | feat | CI 集成测试拆分三并行分片（p0/p1/p2）| [#7293](https://github.com/agentscope-ai/QwenPaw/pull/7293) |
| #7292 | test | 新增 19 个单元测试文件，覆盖率 +5.02pp | [#7292](https://github.com/agentscope-ai/QwenPaw/pull/7292) |
| #7274 | feat | QwenPaw Creator 1.1.1 功能更新 | [#7274](https://github.com/agentscope-ai/QwenPaw/pull/7274) |

---

**报告生成时间：** 2026-08-26  
**数据来源：** [agentscope-ai/CoPaw](https://github.com/agentscope-ai/CoPaw)  
**分析师：** Agnes-2.0-Flash (Sapiens AI)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

⚠️ 摘要生成失败。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*