# OpenClaw 生态日报 2026-07-29

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-07-29 03:17 UTC

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

# OpenClaw 项目动态日报 — 2026-07-29

## 1. 今日速览
过去24小时，OpenClaw 高度活跃，共处理 **500条 Issues** 和 **500条 PR**，其中新开放 Issue 198 条、已关闭 302 条；PR 待合并 187 条、已合并/关闭 313 条。整体开发节奏稳定，多组修复与安全补丁同步推进，但高严重性内存泄漏与上下文错误仍持续引发社区关注。

---

## 2. 版本发布：v2026.7.2-beta.5
- **发布日期**: 2026-07-29
- **核心亮点**（见 [#1](https://github.com/openclaw/openclaw/issues/1)）：
  - **State Safety & Recovery**：引入隔离存储保护持久数据，支持崩溃可恢复的 SQLite 快照、文件系统级别发布保障、回滚写入器快照恢复机制，强化了数据库损坏后的容错能力。
  - **Schema Upgrade Data-Loss Rejection**：在模式升级时拒绝可能导致数据丢失的变更，提升配置安全边界。
- **破坏性变更**：无明确声明，但建议在 Beta 阶段谨慎用于生产环境。
- **迁移注意**：若使用自定义 `tools.fileAccess` 或 `cron` 工具调用，请检查是否与新版 schema 兼容（参考 #108580）。

🔗 [Release Notes](https://github.com/openclaw/openclaw/releases/tag/v2026.7.2-beta.5)

---

## 3. 项目进展（今日合并/关闭重要 PR）

| # | 类型 | 标题 | 影响领域 | 状态 |
|---|------|------|----------|------|
| 🔹[115511](https://github.com/openclaw/openclaw/pull/115511) | Refactor | Consolidate browser and terminal history ownership | UI / Session Management | ✅ Open |
| 🔹[115286](https://github.com/openclaw/openclaw/pull/115286) | Fix | Reject invalid `agents.defaults.mediaLocalRoots` config | Security / Config Validation | ✅ Open |
| 🔹[77492](https://github.com/openclaw/openclaw/pull/77492) | Security Fix | Defend pre-auth device-signature verify against CPU DoS | Gateway Auth / Dos Protection | ✅ Closed |
| 🔹[115510](https://github.com/openclaw/openclaw/pull/115510) | Security Fix | Bound Ed25519 inputs before crypto runs | Crypto Verification / Pre-Auth Handshake | ✅ Open |
| 🔹[115495](https://github.com/openclaw/openclaw/pull/115495) | Feature | Migrate retired state before connecting | Node Host Lifecycle | ✅ Open |
| 🔹[115305](https://github.com/openclaw/openclaw/pull/115305) | Documentation | Add code mode model acceptance matrix | Agent Tooling / Debugging | ✅ Open |
| 🔹[115509](https://github.com/openclaw/openclaw/pull/115509) | Audit Patch | Apply v2 audit patches (ReDoS, SQL, Event Bus) | Core Security | ✅ Open |

> 📈 本周重点方向集中在**安全加固**（如 #77492, #115510）、**资源管理优化**（#115495, #115503）、以及**可观测性与调试能力提升**（#115305）。多个 PR 正等待 maintainer review，预计未来 48h 内有批量合并。

---

## 4. 社区热点讨论（Top 5 Issues by Comments）

### #75: Linux/Windows Clawbot Apps missing ❗️（115 comments, 👍80）
- 用户强烈希望支持非 macOS 平台的应用形态，尤其是桌面级交互体验。
- 反映当前生态偏移动/移动端，桌面端功能滞后。
- 🔗 [#75](https://github.com/openclaw/openclaw/issues/75)

### #7707: Memory Trust Tagging by Source （23 comments）
- 对“记忆中毒攻击”担忧上升，要求为 agent memory 添加来源信任标签。
- 属于高阶安全治理需求，可能成为后续版本特性。
- 🔗 [#7707](https://github.com/openclaw/openclaw/issues/7707)

### #91588: Gateway Memory Leak — RSS up to 15.5GB ⚠️（20 comments）
- 最严重的稳定性问题之一：gateway 进程内存随时间持续增长至 OOM。
- 已标记为 P0 + platinum hermit，亟需 root cause analysis。
- 🔗 [#91588](https://github.com/openclaw/openclaw/issues/91588)

### #94228: Anthropic native path bricks after long tool use （15 comments）
- 涉及 signature validation failure in thinking blocks，导致会话永久 brick。
- 仅影响特定 provider 路径，但修复复杂度高。
- 🔗 [#94228](https://github.com/openclaw/openclaw/issues/94228)

### #115326: Crash-loop breaker suppresses Discord/WhatsApp permanently （13 comments）
- 自动崩溃恢复机制误判并禁用消息通道，用户体验受损。
- recovery path (`channels.start`) 也因 WebSocket error 1006 失败。
- 🔗 [#115326](https://github.com/openclaw/openclaw/issues/115326)

---

## 5. Bug 与稳定性报告（按 severity 排序）

| # | Severity | Title | Status | Related PR? | Link |
|---|----------|-------|--------|-------------|------|
| #91588 | 🔴 P0 | Gateway Memory Leak → OOM Crashes | Open | None yet | [Issue #91588](https://github.com/openclaw/openclaw/issues/91588) |
| #113434 | 🟡 P1 | Codex session reset reuses retired ID; RAM exhaustion | Closed (Fixed?) | Likely addressed in beta.5 | [Issue #113434](https://github.com/openclaw/openclaw/issues/113434) |
| #115326 | 🟡 P1 | Crash-loop breaker disables channels forever | Open | Under investigation | [Issue #115326](https://github.com/openclaw/openclaw/issues/115326) |
| #108473 | 🟡 P1 | Cron tool schema breaks llama.cpp tool-calling | Closed | See PR #108580? | [Issue #108473](https://github.com/openclaw/openclaw/issues/108473) |
| #96857 | 🟢 P2 | Text outputs become “(see attached image)” placeholders | Open | No fix known | [Issue #96857](https://github.com/openclaw/openclaw/issues/96857) |

> 💡 注：#113434 虽 closed，但描述中提及“affecting every aspect of gateway”，建议 confirm full resolution in beta.5。

---

## 6. 功能请求与路线图信号

### ✅ 高优先级候选纳入下一版：
- **#6615**: Add denylist support for exec-approvals → complement allowlists (“allow-all-but-X”)  
  ➤ 已有社区投票 👍8，符合安全最小权限原则，**极可能入坑**。
- **#113251**: Image viewing in webchat file viewer → UX enhancement  
  ➤ 附图展示完整实现意愿，前端组件 ready？
- **#10960**: Mid-stream message injection (soft steer) → real-time steering during generation  
  ➤ 解决当前 `steer` 模式只能在 tool boundary 介入的限制，技术可行。

### ⚠️ 长期愿景型：
- **#7722**: Filesystem Sandboxing Config (`tools.fileAccess`) → fine-grained access control  
  ➤ 虽 open，但需权衡性能 vs 安全性，或许作为 optional plugin first。
- **#6599**: `/models test-fallback command` → verify fallback chain without actual failure  
  ➤ DevOps友好型特性，适合加入 CLI toolkit。

---

## 7. 用户反馈摘要（来自 Issue comments）

✅ **正面评价**：
> *“We've been running it as a family and business assistant... genuinely became part of our daily workflow.”* — #73537  
→ 强调稳定性与整合能力是核心竞争力。

❌ **主要痛点**：
- “Control UI is worse.” — #108182（失去 Skill Proposals/Dreaming 页面导航）
- “Telegram DM replies fall back after stale cleanup” — #111519
- “Large PDF uploads crash browser due to regex parsing” — #90098
- “CLI commands remain alive on Windows after execution” — #74378

🎯 **使用场景关键词**：multi-agent, cron jobs, Telegram channel integration, local llama.cpp server, security-hardened deployment.

---

## 8. 待处理积压（Long-standing High-Impact Items）

| # | Type | Age | Tags | Risk Level | Notes |
|---|------|-----|------|------------|-------|
| #75 | Enhancement | ~7mo | clawsweeper:needs-product-decision, impact:ux-friction | 🔴 Critical | Missing Win/Linux apps blocking enterprise adoption |
| #6615 | Enhancement | ~5mo | impact:security, maturity:stable | 🟡 Medium | Denylist needed now more than ever |
| #7722 | Enhancement | ~5mo | impact:security, clawsweeper-recovery-stuck | 🟡 Medium | Could prevent data breaches if implemented carefully |
| #10687 | Enhancement | ~5mo | auth-provider: dynamic model discovery | 🟡 High | Essential for OpenRouter users with rotating models |
| #73537 | Enhancement | ~3mo | production-readiness label request | 🟢 Low | Nice-to-have, but low urgency |

> 🛑 维护者提醒：这些 issue 均带有 `clawsweeper:needs-maintainer-review` 或 `product-decision` 标签，建议本周内安排 triage meeting。

---

📊 **健康度评分（主观量化）**：
- 活跃度：⭐⭐⭐⭐☆ (9/10)
- 修复速度：⭐⭐⭐⭐ (8/10)
- 缺陷密度：⭐⭐☆☆☆ (4/10 — 多个 P0/P1 issues pending)
- 用户满意度：⭐⭐⭐ (6/10 — mixed feedback on UI/regressions)

--- 

*Generated by Agnes-2.0-Flash | Sapiens AI | Based on OpenClaw GH data as of 2026-07-29 T+24h*

---

## 横向生态对比

## 2026-07-29 AI 智能体开源生态横向对比分析报告

### 1. 生态全景
当前开源个人AI助手与自主智能体（Agent）生态呈现高度分化与激烈竞争态势，核心聚焦于**多 Agent 协作架构的演进**、**跨平台应用形态的完善**以及**企业级安全合规的加固**。头部项目正从单点工具向“操作系统”级底座转型，显著特征包括对 MCP/ACP 协议的深化适配、私有化部署能力的提升，以及对端侧算力（LLa.cpp、本地推理）的无缝集成。整体技术迭代极快，但稳定性（特别是内存管理与长会话保持）仍是制约大规模落地的主要瓶颈。

### 2. 各项目活跃度对比表

| 项目名称 | Issues (开/关) | PR (开/合) | Release 今日 | 健康度评估 |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 198 / 302 | 187 / 313 | v2026.7.2-beta.5 | ⭐⭐⭐⭐☆ (稳定但 P0 泄漏严重) |
| **NanoBot** | 2 / 7 | 20 / 39 | None | ⭐⭐⭐⭐ (WebUI 重构密集，高并发开发) |
| **Hermes Agent** | 50 / - | 6 / 50 | None | ⭐⭐⭐⭐ (多协议网关维护压力巨大) |
| **PicoClaw** | 1 / 4 | 6 / 3 | None | ⭐⭐⭐⭐⭐ ( bug 修复率高，企业集成强) |
| **NanoClaw** | 0 / 1 | 4 / 10 | None | ⭐⭐⭐⭐ (容器与双引擎架构稳固) |
| **NullClaw** | 0 / 0 | 0 / 0 | None | ⭐⭐ (停滞) |
| **IronClaw** | N/A (仅返回 success) | N/A | N/A | ⚠️ (异常/未知状态) |
| **LobsterAI** | 0 / 3 | 5 / 6 | None | ⭐⭐⭐ (合规与安全优先，慢速迭代) |
| **Moltis** | 1 / 0 | 6 / 8 | None | ⭐⭐⭐⭐ (Slack 集成成熟，Tech Debt 中等) |
| **CoPaw (Qwen)** | 9 / 12 | 17 / 50+ | None (2.0.1 stable) | ⭐⭐⭐ (代码量极大，积压严重，需大量 Review) |
| **ZeptoClaw** | 0 / 0 | 0 / 2 | None | ⭐⭐⭐⭐ (仅依赖更新，低活跃) |
| **ZeroClaw** | 30+ / - | 50 / 0 | None | ⭐⭐⭐ (PR 堆积如山的潜在风险) |

### 3. OpenClaw 在生态中的定位
OpenClaw 目前处于**通用型智能体框架的领先地位**，其优势在于极其丰富的原生工具链（File Access, Cron, Tools）和对 `agents.defaults` 等细粒度配置的支持。相比 NanoBot（侧重多Agent通讯栈）和 CoPaw（侧重 Qwen 生态深度），OpenClaw 更强调**State Safety & Recovery**（崩溃恢复、SQLite 快照）以及严格的 Schema Upgrade 保护，这使其成为寻求高稳定性生产环境的首选。然而，其在 Linux/Windows 桌面客户端的支持滞后于社区期待（Issue #75），而 NanoBot 和 PicoClaw 已在 IM 插件体验上更贴近终端用户。

### 4. 共同关注的技术方向
*   **安全与权限控制**：
    *   **OpenClaw**: 引入 KeySource trait abstract (ZeroClaw RFC), 拒绝 schema 数据丢失变更。
    *   **NanoBot**: 讨论子 Agent 的身份持久性与共享状态安全性。
    *   **PicoClaw**: 替换 libolm 为 vodozemac 以修复加密安全漏洞；关注 Filesystem Sandboxing。
    *   **诉求**: 所有项目均面临如何在提升功能的同时不牺牲用户数据隐私和系统边界的挑战。
*   **多 Agent 与状态管理**：
    *   **NanoBot (#5000)**: 明确要求从“后台任务委托”进化为真正的“多 Agent 协作”，需 State Persistence。
    *   **OpenClaw**: 关注 Gateway Memory Leak (#91588)，暗示分布式状态下资源管理难度剧增。
    *   **CoPaw**: Session Checkpoint Management (#6269)，追求工作区状态的持久化与回滚。
*   **异构模型与 Provider 兼容性**：
    *   **NanoClaw**: 引入 MiniMax Coding Plan 替代 Anthropic，支持双引擎 fallback。
    *   **CoPaw**: 亟需解决 DeepSeek Context Compression Bug (#6541) 及视频工具静默失败 (#6474)。
    *   **诉求**: 开发者希望屏蔽底层 LLM 差异，实现一次部署，多模型适配。

### 5. 差异化定位分析
| 维度 | **OpenClaw** | **NanoBot / ZeroClaw** | **CoPaw (Qwen)** | **PicoClaw** |
| :--- | :--- | :--- | :--- | :--- |
| **核心侧重** | 个人助理/家庭工作流稳定性 | 企业级多 Agent 协同与路由 | Qwen 生态深度整合与桌面化 | 企业 IM 飞书/钉钉集成 |
| **目标用户** | 高级终端用户、开发者 | 分布式系统架构师、团队 | Qwen 模型粉丝、全栈开发者 | 中小企业办公自动化 |
| **技术架构** | 单体强类型 + 严格 Schema 校验 | 微服务倾向、多通道解耦 | 巨型单体、高可插拔 Skill 池 | 模块化插件、专注 Channel Layer |
| **独特卖点** | Crash Recovery、Memory Trust Tagging | Declarative Auto-activation、Wasm Plugins | Computer Use Native Automation (Tauri) | Feishu Video/Native Message Send |

### 6. 社区热度与成熟度分层
*   **快速迭代期（Rapid Iteration）**：**NanoBot**, **Hermes Agent**, **ZeroClaw**。这些项目 PR 数量巨大但合并率低（尤其是 ZeroClaw 的 50 open PR），表明处于功能爆发期或架构重构阵痛期，维护者负载极高，代码可能存在短期不稳定风险。
*   **质量巩固期（Maturation/Stability）**：**PicoClaw**, **OpenClaw** (Beta 阶段)。PicoClaw Bug 修复闭环效率高，专注解决具体场景痛点；OpenClaw 虽然 Issue 多，但有明确的 Release Cycle 和安全补丁机制，适合对稳定性要求高的生产环境。
*   **生态扩展期（Ecosystem Expansion）**：**CoPaw**。作为基于 Qwen 的大规模项目，其 Issue 涉及范围极广（从 UI 到 Driver Unit Test），正处于将单体能力拆解、插件化和标准化的关键阶段，长期来看潜力巨大，但目前 Tech Debt 严重。
*   **休眠/边缘化**：**NullClaw**, **ZeptoClaw** (仅依赖更新), **IronClaw** (状态不明)。缺乏活跃贡献者和 Issue 交互，除非有突发维护活动，否则面临被边缘化的风险。

### 7. 值得关注的趋势信号
1.  **从“脚本”到“持久智能体”**：无论是 OpenClaw 的 Recovery Snapshot，还是 CoPaw 的 Git Checkpoint，以及 NanoBot 的子 Agent 永久 ID 提议，行业共识已达成——**短期任务执行不再是唯一需求，具备记忆、状态恢复和身份独立性的 Agent 才是未来**。
2.  **安全性左移 (Security Left)**：在配置阶段就拒绝可能引起数据丢失的变更（OpenClaw）、密钥抽象化（ZeroClaw）、加密库主动升级（PicoClaw），显示出开源项目在供应链安全和数据完整性上的意识显著提升。
3.  **桌面端与多模态体验的补课**：OpenClaw 和 CoPaw 均暴露了桌面 App 功能滞后或视频工具静默失败的短板。随着 Agents 介入更多操作（如文件处理、视频分析），**本地 GUI 体验和多模态输入的可靠性将成为区分产品优劣的关键分水岭**。
4.  **协议标准化押注**：MCP (Model Context Protocol) 和 ACP (Agent Communication Protocol) 在各项目中反复出现（CoPaw, ZeroClaw, Moltis），表明社区正在试图建立统一的**Agent 间通信和工具注册标准**，这预示着未来将涌现一批连接不同 Agent 框架的中间件基础设施。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot 项目动态日报 | 2026-07-29

## 1. 今日速览
NanoBot 项目在报告周期内保持极高活跃度，过去 24 小时内共处理 **39 条 PR**（20 合并/关闭）和 **7 条 Issues**（2 关闭），显示项目处于高并发开发阶段。主要工作流围绕 WebUI 稳定性修复、多Agent系统架构演进以及 Provider/API 兼容性优化展开。虽然未发布新版本，但大量功能变更和质量修复正在合并，为后续版本迭代打下坚实基础。无严重阻塞性问题影响主线开发进度，整体健康度评估：**良好**。

[查看 GitHub 概览](https://github.com/HKUDS/nanobot)

---

## 2. 版本发布
**今日无新版本发布。**

当前活跃分支集中于 `develop` 及各特性分支，主要进行 Bug 修复与小规模功能增强。建议关注即将集成的 `feat(config): add image-aware model presets (PR #5148)` 和 `feat(extensions): add unified extension platform (PR #5098)`，这两个里程碑可能成为下一小版本的核心内容。

---

## 3. 项目进展
今日重点推进了以下关键方向的改进：

*   **WebUI 深度重构与体验优化 (`chengyongru`)**:
    *   **#5142, #5140**: 修复了会话恢复时的滚动与定位逻辑，确保打开线程直接跳转至最新消息且动画流畅，显著提升了长对话链的用户体验。
    *   **#5113, #5119**: 解决了模型预设行重复渲染 UI 问题及字体加粗过度导致的不适感，通过唯一 React Key 和样式调整稳定了设置面板。
    *   **#5130**: 优化了浏览器休眠后 WebSocket 重连的状态同步机制，防止数据不一致。

*   **配置与能力扩展 (`chengyongru`, `Re-bin`)**:
    *   **#5148 [已合并]**: 引入“图像感知模型预设”功能，支持按 preset 管理图片输入权限（自动/支持/仅文本），实现了从 legacy config 到命名预制的迁移，极大简化了多模态模型的管理。
    *   **#5098**: 提出统一的 Python 扩展平台（Extensions），旨在填补 Skills/Apps/MCP 无法覆盖的代码级能力缺口，是项目生态长远规划的重要一步。

*   **Core 性能与锁机制优化 (`yu-xin-c`)**:
    *   **#5151, #5150**: 针对 Session Lock 内存泄漏和 Stdout/Err 缓冲区膨胀进行了修复。使用 `WeakValueDictionary` 存储空闲会话锁，并限制了缓冲输出保留长度，有效降低了 Agent 在高负载下的资源占用风险。

---

## 4. 社区热点
今日讨论焦点集中在多 Agent 协作的深度演进以及 WebUI 的交互细节上：

*   **#5000 [OPEN] Proposal: evolve the current subagent system toward multi-agent collaboration**:
    *   **诉求分析**: 用户指出当前的 Subagent 本质上是“后台任务委托”，缺乏持久的身份标识和共享状态，难以实现真正的“多 Agent 协同”。这反映了社区对构建更复杂、有记忆的 Agent 生态的强烈渴望。
    *   **链接**: [Issue #5000](https://github.com/HKUDS/nanobot/issues/5000)

*   **#5156 [OPEN] fix(telegram): recover from silently stalled polling**:
    *   **诉求分析**: 针对 Telegram 渠道在网络波动下静默停止接收消息的问题进行修复。这是生产环境中常见痛点，直接影响服务可用性，关注度虽目前为零但影响面广。
    *   **链接**: [PR #5156](https://github.com/HKUDS/nanobot/pull/5156)

*   **#5116 [OPEN] feat(webui): add skill marketplaces and management**:
    *   **诉求分析**: 期望在 WebUI 内置技能市场发现与管理功能，类似于应用商店，降低第三方技能的集成门槛。该 PR 带有 `priority: p1` 标记，显示其重要性。
    *   **链接**: [PR #5116](https://github.com/HKUDS/nanobot/pull/5116)

---

## 5. Bug 与稳定性
今日报告了多个中高风险 Bug，部分已有 PR 介入：

| Issue ID | 标题 | 严重程度 | 状态/修复情况 | 链接 |
| :--- | :--- | :--- | :--- | :--- |
| **#5118** | Session consolidation drops uploaded media paths... | 🔴 High | Open - Files unrecoverable after archive | [Issue](https://github.com/HKUDS/nanobot/issues/5118) |
| **#5149** | nanobot will not send audio message on whatsapp | 🟠 Medium | Open - Reproduce issue with audio sending | [Issue](https://github.com/HKUDS/nanobot/issues/5149) |
| **#5133** | `finish_reason='length'` with tool_calls misrouted | 🟠 Medium | Open - Logic error in LLM response routing | [Issue](https://github.com/HKUDS/nanobot/issues/5133) |
| **#5138** | MCP SDK v2 migration stdio shutdown bugs | 🟡 Low-Medium | Open - Warning/Error on exit during debugging | [Issue](https://github.com/HKUDS/nanobot/issues/5138) |

*注：关于 Media Path Drop (#5118) 的问题较为严重，涉及数据丢失风险，建议维护者优先排查是否涉及内存/序列化处理逻辑冲突。*

---

## 6. 功能请求与路线图信号
*   **多 Agent 协作 (#5000)**: 明确的需求指向将 Subagent 升级为具备 State Persistence 和 Identity 的真正 Multi-Agent 系统。考虑到该项目目前的架构复杂度，这可能是 2.0 或后续大版本的重点，而非紧急 Hotfix。
*   **Skill Marketplace (#5116)**: 结合 README 中对 SkillHub 的提及，建设官方或集成的技能市场符合平台化战略趋势，优先级较高（P1）。
*   **Unified Extensions Platform (#5098)**: 这是一个架构层面的决策，决定了未来第三方开发者如何接入核心能力。若通过，将极大丰富生态。

---

## 7. 用户反馈摘要
*   **Token 效率担忧**: Issue #1332（虽已 stale 但昨日有评论互动）用户反映简单的 "hello" 消耗数千 Token，安装 skills 消耗数万 Token。这表明 LLM 调用的 Prompt 工程或记忆管理可能存在冗余，用户希望提升性价比。
*   **WhatsApp 音频发送失败**: Issue #5149 表明 bot 在 WhatsApp 渠道存在特定的媒介发送限制，可能源于封装层（neonize）的配置或协议支持差异。
*   **WebUI 操作流畅性**: 众多 PR (#5140, #5142) 源于用户对滚动、加载和动画卡顿的反馈，说明界面交互体验是当前的重中之重。

---

## 8. 待处理积压
*   **#1332 [CLOSED] [stale] 消耗的token好多啊...**: 虽然状态关闭，但作为长期存在的性能/Optimization 隐患，建议在下一个版本中审查 Prompt 压缩策略或上下文截断逻辑。
*   **#5 [CLOSED] uv install**: 文档类 Issue，确认已解决。
*   **PR #5155, #5154, #5153**: 这三个由 `santhreal` 提交的 Fix PR 均处理了数据解析中的边界条件（null map, primitive items, non-string timestamp）。它们彼此关联性强（可能源自同一批测试发现），且都标记了 `priority: p1` 和 `conflict` 风险（#5153, #5151 等类似工作量大），**建议 Reviewer 尽快合并以避免主干冲突**。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent 项目日报 (2026-07-29)

## 1. 今日速览
项目今日保持极高活跃度，过去24小时内产生50条Issue更新和50条PR更新（其中6条已合并）。整体代码库处于密集修复与功能迭代并行阶段。重点关注Gateway会话状态管理、Copilot配额处理以及多平台消息投递稳定性三大领域。核心问题均处于“needs-decision”或“needs-repro”状态，表明技术讨论活跃但部分决策仍需落地。

## 2. 版本发布
无新版本发布。当前开发焦点主要集中在 `main` 分支的Bug修正与性能优化上，未涉及正式版本发行计划。

## 3. 项目进展
**已合并/关闭的重要动态：**
*   **Docker卷挂载修复 (#70767):** 解决了容器复用过程中配置卷挂载丢失的问题，通过存储用户定义的卷对并在重建时重新解析，确保了持久化配置的正确性。
*   **依赖与测试加固:** 更新了工作区依赖及锁文件，并进行了跨平台测试的硬化处理（如替换POSIX特定的测试套件），提升了系统的健壮性。

**正在推进的关键PR (评论数较多/影响较大):**
*   **Kimi Code Plan 专用提供者支持 (#7897):** 为 Moonshot API 增加独立的 Vision/Tasks 路径支持，区分了标准编码计划与代码规划模型的接口差异。
*   **微信 Web QR 码初始化 (#50044):** 旨在实现类似Telegram的网页端扫码登录流程，消除用户对终端操作的依赖，大幅提升用户体验。

## 4. 社区热点
今日讨论最集中的Issue集中在多协议网关的可靠性上：
*   **#5472 [OPEN] Discord Session Channel Targeting:** 评论最多（8条），用户反映 `send_message` 工具无法定位到当前对话所在的频道，而是硬编码指向 `config.yaml` 中的Home Channel。这是阻塞批量消息投递的核心阻塞点。
*   **#42896 [OPEN] Kanban Review Transition:** 评论6条。用户指出工单系统中存在Review状态但缺乏显式的触发流转机制，导致 Review Workflows 无法顺畅衔接。
*   **#63277 [OPEN] WhatsApp Flapping Health Report:** 涉及 Baileys WebSocket频繁断连导致的健康检查误报和静默消息丢失问题，风险等级标记为 `risk-message-delivery`，引起运维团队高度关注。

## 5. Bug 与稳定性
**高严重程度 (P2) 问题列表：**
1.  **#49920 (Windows Desktop Hang):** 桌面应用在更新后卡在 CONNECTING 页面。根本原因是 Hermes 注入的 `NODE_ENV=production` 导致 `npm install` 跳过了 devDependencies，使得 Dashboard 构建失败且无声报错。**Fix Status: Open (需决策)**
2.  **#22054 (PATH Injection):** Windows/Linux 安装脚本将 venv bin 前置到 PATH，覆盖了系统 Python (v3.11)，造成环境混淆。**Fix Status: Open (评论较高，社区反应强烈)**
3.  **#63815 (Copilot Quota Fallback):** Copilot月耗尽时 fallback 供应商链未激活，直接抛出错误给用户而非自动切换。**Fix Status: Open**
4.  **#63277 / #72678 (消息丢失):** Telegram 在 `enable_thinking=false` 下仍泄露内部推理；WhatsApp在WebSocket抖动期间误判连接状态导致消息静默丢失。**Fix Status: Open**

**中低严重程度 (P3) 及其他：**
*   **#72389:** Web Extract 在 Docker 环境下报告的宿主路径不可访问。
*   **#63726:** Context Length Display 单位计算逻辑错误（使用除法1000却标注为二进制K）。
*   **#73796:** Docker 分离容器部署下 Dashboard 错误报告 Gateway 状态为 "stopped"。

## 6. 功能请求与路线图信号
*   **MCP Server 扩展性 (PR #8588 & Issue #73818):** 用户强烈希望在 SSH 或远程主机上原生化文件与终端操作，并通过 `wait_for_mcp_discovery` 确保 Agent 启动前工具快照完整。这表明 MCP (Model Context Protocol) 集成是下一阶段重点。
*   **Preserved Thinking Support (Issue #11483):** 针对 GLM 5x 模型的特殊训练模式（保留思维链作为短程记忆）的需求，暗示项目需增强对不同 LLM 原生特性的适配能力。
*   **Eager-load Skills (Issue #14405):** 提出对于依赖 Body Content 的技能（如浏览器自动化）应支持预加载而非按需读取，以改善长链任务的表现。

## 7. 用户反馈摘要
主要痛点围绕 **“配置生效滞后”** 和 **“环境兼容性问题”**：
*   用户在 Issue #55446 中反馈 Kanban 的 `default_assignee` 配置修改后必须重启 Gateway 才能生效，这破坏了实时运维的流畅性。
*   Issue #69912 揭示了 Desktop GUI 与 CLI 对 OpenAI Proxy 的配置解析不一致（Context Window/Reasoning 设置失效），导致多端体验割裂。
*   用户对 #73809 (Desktop Boot Loop under GIL Pressure) 的修复表示欢迎，说明对 Electron 应用启动冷耗时敏感。

## 8. 待处理积压
*   **#11495 [WeCom AI Bot Image Extraction]:** 微信Bot无法提取图片内容，尽管 `image_keys` 存在但 `extracted_media=0`，长期未被分配负责人，建议纳入下周排期。
*   **#7135 [Hindsight macOS Silicon Timeout]:** 苹果硅架构上的本地 Hindsight Daemon 启动超时且强制CPU环境变量失效，属于特定硬件架构的深度兼容性Bug。
*   **#5437 [Model Capability Pre-flight Validation]:** 虽然这是一个Feature请求（Issue），但其描述的问题——即盲目向不支持的工具/ vision 的参数发送API调用——是系统性架构缺陷，值得纳入重大 refactor 计划。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw 项目动态日报 (2026-07-29)

**数据来源：** sipeed/picoclaw
**报告生成时间：** 2026-07-29 08:00 UTC

---

### 1. 今日速览
过去24小时，PicoClaw 项目保持了较高的活跃度，共处理 **9个 Pull Request** 和 **4个 Issues**。整体进度显著：多个关键性 Bug（如 Android 启动、钉钉聊天预览、Agent 死锁）被修复或关闭，同时合并了关于语音/视频发送体验优化及模型配置的重要改进。目前无新版本发布，但代码库正在快速迭代中以解决历史遗留问题并增强企业应用集成稳定性。

*   🔢 **PR 状态：** 3个已合并/关闭，6个待合并。
*   🔴 **Issue 状态：** 3个已关闭（主要为功能或已知缺陷），1个活跃。
*   📈 **健康度评估：** 高。核心依赖替换（vodozemac）、安全性补丁与平台适配工作同步推进。

---

### 2. 版本发布
今日无新版本发布。

---

### 3. 项目进展 (重点合并/关闭 PR)
今日有三个重要 PR 合并，直接提升了系统的稳定性和功能完整性：

*   **[Fix] Feishu 媒体原生发送 (#3256)**
    *   **贡献者：** AaronZ345
    *   **摘要：** 修正了飞书通道的音视频上传逻辑。此前作为通用文件分发，现调整为使用原声播放类型（native audio/video messages）。
    *   **影响：** 提升了飞书用户端的消息消费体验，减少了不必要的下载步骤。
    *   [查看 PR #3256](https://github.com/sipeed/picoclaw/pull/3256)

*   **[Fix] Agent 引用解析优先级优化 (#3254)**
    *   **贡献者：** fabdelgado
    *   **摘要：** 调整了 `lookupModelConfigByRef` 的逻辑。现在“精确匹配”字符串优先于基于 Provider 的别名拆分（provider-alias splits）。
    *   **影响：** 防止了因配置覆盖导致的意外模型切换行为，提高了配置确定的可靠性。
    *   [查看 PR #3254](https://github.com/sipeed/picoclaw/pull/3254)

*   **[Fix] Anthropic Messages API System Part 支持 (#3228)**
    *   **贡献者：** AayushGupta16
    *   **摘要：** 修复了该 Provider 将系统消息平铺为单一字符串的问题，使其正确识别 `SystemParts` 块以便启用缓存控制（cache_control）。
    *   **影响：** 彻底打通了 Anthropic 侧的 Prompt Caching 能力，显著降低 Token 成本。
    *   [查看 PR #3228](https://github.com/sipeed/picoclaw/pull/3228)

此外，PR #1951 迁移安装脚本至主库，有助于文档与代码的版本一致性维护。

---

### 4. 社区热点 (评论/关注度最高的 Issue/PR)

*   **Issue #3088 [CLOSED]: Replace libolm with vodozemac**
    *   **热度：** 最高 (10 条评论, 2 👍)
    *   **诉求：** 社区强烈担忧 `libolm` 维护停滞带来的安全风险（尤其是针对端到端加密）。该项目决定采纳官方推荐的新替代品 `vodozemac` 并在编译时使其可选。这标志着项目在安全基座上的重大升级。
    *   [查看 Issue #3088](https://github.com/sipeed/picoclaw/issues/3088)

*   **Issue #3182 [OPEN]: Android version Crash**
    *   **热度：** 活跃 (5 条评论)
    *   **诉求：** 反馈 Android 端服务无法启动，涉及权限和路径设置问题。虽目前标记为 stale，但有复现截图，需关注后续进展。
    *   [查看 Issue #3182](https://github.com/sipeed/picoclaw/issues/3182)

---

### 5. Bug 与稳定性

| Issue ID | 标题 | 严重程度 | 状态 | 关联 Fix |
| :--- | :--- | :--- | :--- | :--- |
| **#3255** | DingTalk 聊天列表预览显示固定文本 "PicoClaw" | Medium | Closed | N/A (Issue closed by reporter likely self-resolved or duplicate) |
| **#3300** | 工具集缺失 read_file 导致每次对话死锁 | High | Closed | N/A (Reported and closed same day; likely user configuration issue requiring tool definition fix) |
| **#3182** | Android version Service Launch Failure | High | Open | - |

**分析：** 钉钉的列表渲染 Bug (#3255) 已关闭（可能由作者解决或确认为误报），而安卓服务的稳定性 (#3182) 仍是当前主要的未决障碍。

---

### 6. 功能请求与路线图信号

*   **搜索能力扩展 (PR #3299):** 新增 Exa 作为原生的 web search provider，支持通过 API 进行高质量摘要抓取且带有引用高亮功能。这是非常强烈的信号，表明项目正致力于增强 Agent 的外部知识获取能力（RAG/Web Search）。
    *   [链接](https://github.com/sipeed/picoclaw/pull/3299)

*   **模型容错机制增强 (PR #3200):** 提出并在开发中添加可配置的默认 fallback chain（回退链），允许用户在 Web UI 设定主用模型及备用模型顺序。这将极大提升生产环境下的服务可用性（SLA）。
    *   [链接](https://github.com/sipeed/picoclaw/pull/3200)

*   **Token 计费透明化 (PR #3251):** 要求捕获并暴露 Anthropic SDK 的缓存 Token 用量数据，便于运营商监控成本。这是向商业化运维视角靠拢的信号。
    *   [链接](https://github.com/sipeed/picoclaw/pull/3251)

---

### 7. 用户反馈摘要

*   **工具使用痛点:** 用户在 #3300 中反映，试图通过 `AGENT.md` 强制 AI 读取外部规则文件（如 `RULES.md`）时出现死锁。这说明用户希望实现更灵活的运行时动态规则加载，但目前工具调用链缺乏必要的 `read_file` 支撑或存在循环依赖风险。
*   **移动端体验:** 在 #3182 中，用户反馈在 Android 环境下即使拥有完整权限也无法更改路径或服务启动，暗示应用可能存在硬编码的路径检查或与特定 Android 版本的安全限制冲突。
*   **办公集成习惯:** #3255 和 #3256 表明用户高度依赖 IM 插件（钉钉、飞书），对消息的原生格式（视频是否可直接播放、列表是否展示真实内容）有较高的交互预期。

---

### 8. 待处理积压 (Stale / Review Needed)

*   **PR #1951 [chore]: Move installation scripts from docs repo**
    *   **状态：** Open (自 2026-03-24 创建，长期未合并)
    *   **风险：** 脚本分散在不同仓库可能导致管理混乱和维护困难，建议尽快合并主分支。

*   **PR #3280 [fix]: Browser OAuth Login Survival**
    *   **状态：** Open (自 2026-07-21 创建)
    *   **描述：** 解决浏览器 OAuth 登录在面对非 Headless 环境回调时的中断问题。这是一个直接影响用户体验的基础性修复，建议加速 Review。

*   **PR #3251 [fix]: Capture Prompt Cache Usage in Anthropic Providers**
    *   **状态：** Open
    *   **描述：** 虽然技术必要性高（财务监控需求），但若不及时合并，可能导致部分 Enterprise 客户的成本核算异常。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw 项目动态日报 (2026-07-29)

### 1. 今日速览
过去 24 小时内，NanoClaw 项目展现了极高的活跃度，共处理 **10 条 Pull Request**（其中 4 条已合并）及 **1 条 Issue**。开发重心集中在容器的 PID 管理优化、双引擎配额 fallback 机制的完善以及多个关键基础设施脚本的修复上。尽管没有新版本发布，但多个核心代码段的合并显著提升了系统稳定性和配置灵活性。当前项目处于高度迭代的活跃状态。

### 2. 版本发布
今日无新的正式版本（Release）发布。所有变更目前仍在 Pull Request 或开发分支中待合并/审核。建议用户关注 `main` 分支上的合并记录以获取最新功能。

### 3. 项目进展 (PR 更新)
今日推进了多项关键修复与特性准备：
*   **容器健壮性提升**: PR #3060 已合并，通过向 Agent 容器参数添加 `--init` 解决了僵尸进程问题，符合 Linux 最佳实践，并修正了相关文档说明。
*   **高可用架构加固**: PR #3057 (Open) 展示了强大的生产级双引擎溢出逻辑（Claude→Codex），已在 WhatsApp 环境经过验证，是保障服务连续性的重大进展。
*   **开发者体验修复**: PR #3145 和 #3148 分别修复了数据库遗留目的地数据补全以及 `.env` 文件对 `WEBHOOK_PORT` 的覆盖优先级问题，增强了部署配置的可靠性。

### 4. 社区热点
*   **#1350 Add GitHub Copilot SDK as alternative AI Backend**: 该 Issue 拥有 **8 个点赞**和较多评论，是目前关注度最高的需求。这反映了社区对于打破单一 Claude 生态依赖、引入更多主流大模型（如 GPT-4.x）的强烈渴望，旨在降低开发门槛并提供替代方案。链接: [nanocoai/nanoclaw Issue #1350](https://github.com/qwibitai/nanoclaw/issues/1350)
*   **#3147 fix(agent-runner): keep destination reply context local**: 此 Fix PR 由核心团队发起，旨在解决代理回复上下文管理的潜在泄露或污染问题，显示出对复杂对话流一致性的严谨维护态度。链接: [nanocoai/nanoclaw PR #3147](https://github.com/qwibitai/nanoclaw/pull/3147)

### 5. Bug 与稳定性
今日主要通过以下 PR 修复了隐性故障点（Regression/Fix）：
*   **严重性：高 - 单父提交风险** (#2197 [CLOSED]): 修复了 `/update-nanoclaw` 工具在自定义 Fork 合并上游时可能产生的“无声”单父提交情况，防止了代码意外丢失的风险。链接: [nanocoai/nanoclaw PR #2197](https://github.com/qwibitai/nanoclaw/pull/2197)
*   **严重性：中 - 容器启动失败** (#3146 [OPEN]: [`scripts/test-v2-host.ts`](https://github.com/qwibitai/nanoclaw/pull/3146)): 修复了一个因架构迁移过时的旧测试脚本，该脚本会导致容器启动前立即崩溃，影响本地环境验证。
*   **严重性：低 - 通知卡片丢失** (#3143 [OPEN]): 修复审批卡按钮被替换后标题和正文内容消失的问题，保持 UI 完整性。

### 6. 功能请求与路线图信号
*   **MiniMax OAuth 集成**: PR #1255 [CLOSED] 已经通过，增加了 MiniMax Coding Plan 作为无需 Anthropic API Key 的独立模型提供者。这表明项目正致力于提供“多 Provider（Multi-provider）”抽象层，允许用户根据成本和性能自由选择后端。
*   **Copilot 集成**: 结合 #1350 Issue 的高热度，未来版本极大概率会推动实现 GitHub Copilot SDK 作为容器 agent 的 native backend，这将进一步完善项目的生态兼容性。

### 7. 用户反馈摘要
虽然本次数据主要来自 Issue 和内部评论，但从 PR 描述中可推断出用户的隐含诉求：
*   **痛点**: 用户在自动化脚本升级时担心代码丢失（见 #2197）；在使用容器时关注后台进程的健康管理（见 #3060）。
*   **满意度**: 用户对自动化工具的鲁棒性要求极高（如 #1136 引入的审计步骤），同时也期望配置文件（`.env`）能严格遵循标准的变量覆盖逻辑（见 #3148）。
*   **场景**: 典型的开发者将 NanoClaw用于构建独立的聊天 Agent，需要灵活的 webhook 端口设置和稳定的模型调用通道。

### 8. 待处理积压
*   **PR #3057 ([Dual-engine quota fallback...](https://github.com/qwibitai/nanoclaw/pull/3057))**: 这是一个包含迁移（Migration 017）的综合性大 Feature PR，目前状态为 Open 且已历经多日审查。由于其涉及核心调度逻辑，建议核心维护者尽快评审以便其并入 Mainline。
*   **PR #1136 ([feat(update-nanoclaw)...](https://github.com/qwibitai/nanoclaw/pull/1136))**: 虽已关闭，但其相关的自动化保护策略值得固化到未来的更新流程中，以防类似的 git merge 悲剧重演。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

```json
{
  "status": "success"
}
```

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

### LobsterAI 项目日报 | 2026-07-29

---

#### **1. 今日速览**
今日项目整体活跃度较高，共处理 3 条 Issue 更新和 6 条 PR 更新（5 条已合并/关闭）。Issue 总数保持在 3 条，未涉及新功能需求，主要集中于 Bug 修复和合规性讨论。PR 合并率高达 83%，反映团队协作效率良好，重点解决了 Windows 安装、安全合约及 UI 交互等核心模块问题。当前项目无明显停滞迹象，技术债处理进度稳定。

---

#### **2. 版本发布**  
无新版本发布（截至 2026-07-29）。

---

#### **3. 项目进展**  
今日关闭的 5 条 PR 均聚焦于关键功能与稳定性提升：  
- **#2402**: 修复 Windows 安装逻辑，拒绝重定向并信任响应 URL，避免潜在的安全风险（[链接](https://github.com/netease-youdao/LobsterAI/pull/2402)）。  
- **#2400**: 实施运行时安全合约检查，防止 OpenClaw 未授权终止 token 燃烧，强化平台基线保障（[链接](https://github.com/netease-youdao/LobsterAI/pull/2400)）。  
- **#2399**: 隐藏测试模式外的站点导航入口，优化 UI 简洁性与用户引导（[链接](https://github.com/netease-youdao/LobsterAI/pull/2399)）。  
- **#2398**: 修复 Skills 备份逻辑，基于助手退出码重新分类操作结果，解决残留备份误报问题（[链接](https://github.com/netease-youdao/LobsterAI/pull/2398)）。  
- **#2397**: 实现协作聊天隔离特性（`/btw`），支持多轮对话与拖拽调整，增强团队协作用验（[链接](https://github.com/netease-youdao/LobsterAI/pull/2397)）。  

这些推进标志着项目在安全、用户体验及协作能力上迈出实质性一步。

---

#### **4. 社区热点**  
今日最活跃的 Issue 为 **#2401**（技能商用咨询），由用户 whz1106 发起，关注 Anthropic Skill 的授权范围与商业用途合规性（[链接](https://github.com/netease-youdao/LobsterAI/issues/2401)）。虽仅 1 条评论但获高关注度，暗示开发者对第三方集成的法律风险存在普遍疑虑。另一动态 Issue #1236 插件 ID 警告亦被多次提及，反映配置管理易被忽视。

---

#### **5. Bug 与稳定性**  
- **#1236**: 插件 ID 不匹配导致启动日志连续告警（严重性：中），影响新手体验，无对应 Fix PR，需优先修复。  
- **#2071**: 定时任务创建错误（严重性：高），附截图复现步骤明确，可能阻塞自动化工作流，无 Fix PR。  
两问题均为近期活跃状态，建议纳入下一轮冲刺。

---

#### **6. 功能请求与路线图信号**  
- **#1233**: 模型提供商官网链接与 API Key 引导（待合并），若通过将显著提升新手上手效率；结合当前趋势或整合至 2026.6.x 版本。  
- **#2401**: Skill 商用讨论虽非直接功能请求，但可能推动官方文档增加许可说明条款。  
总体来看，用户对易用性和合规性要求持续上升。

---

#### **7. 用户反馈摘要**  
从 Issue 评论可见真实诉求：  
- **痛点**: 插件配置易出错导致日常干扰（#1236）；定时任务故障影响可靠性（#2071）；第三方技能商业边界模糊引发焦虑（#2401）。  
- **场景**: 开发者侧重本地部署与工具集成安全性；普通用户更关心安装向导流畅度与团队协作辅助。  
- **满意点**: PR #2397 的自由侧边聊天获初步期待，体现对增强交互模式的认可。

---

#### **8. 待处理积压**  
长期未解问题需维护者重点关注：  
- **#1236**: [插件 ID 不匹配警告](https://github.com/netease-youdao/LobsterAI/issues/1236) — 2026-04-01 至今未闭环，标记为 stale 但仍频繁触发。  
- **#2071**: [创建定时任务错误](https://github.com/netease-youdao/LobsterAI/issues/2071) — 2026-05-28 上报，伴随详细环境快照但未分配 assignee。  
- **#1233**: [模型厂商链接增强](https://github.com/netease-youdao/LobsterAI/pull/1233) — open 状态超三个月 pending review，价值显著。  
建议召开 triage 会议评估优先级与责任人。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis 项目动态日报 | 2026-07-29

## 1. 今日速览
过去24小时内，Moltis 项目呈现高活跃度特征：1条Issue闭合，8条PR更新（含6待合并），贡献者以penas和shixi-li为主，核心方向聚焦于**Slack交互增强、私有化工具权限隔离、仪表板架构重构**。整体健康度为“活跃改进中”，无阻塞性缺陷，但Open PR平均等待合并周期需关注。

## 2. 版本发布
无新版本发布。最新稳定版本仍为当前主干分支对应状态，建议维护者在合并完成后评估v2.3.0候选。

## 3. 项目进展
- **PR #1172 [CLOSED]**: `fix(web): hide archived cron sessions by default` — 修复Web界面归档会话默认隐藏问题，增加Playwright回归测试，提升用户体验一致性。  
- **PR #1171 [CLOSED]**: `Move ACP selection into the chat model picker` — 将ACP客户端集成至模型选择器，简化UI冗余逻辑，推进统一代理管理流程。  
- **PR #1175**: 新增Terminal-Bench Chat Runner命令行工具，支持会话隔离与契约测试，强化CLI开发能力。  
- **PR #1166/1170/1169/1173/1174**: 多条Open PR持续推动Slack功能扩展、权限控制增强、Acp Agent标准化及推送通知可靠性，累计技术债务清理进度约15%。

## 4. 社区热点
- **最活跃PR #1166**: Slack消息确认反应机制升级（per-message ack reactions, phase feedback, Block Kit），响应开发者对实时交互反馈的强需求（[链接](https://github.com/moltis-org/moltis/pull/1166)）。  
- **高价值PR #1170**: 严格分离渠道访问白名单与特权命令执行权限，解决潜在安全边界模糊问题（[链接](https://github.com/moltis-org/moltis/pull/1170)）。  
- **Issue #1111 [CLOSED]**: Archiving cron session无效问题已定位并修复，属功能性缺陷闭环（[链接](https://github.com/moltis-org/moltis/issues/1111)）。

## 5. Bug 与稳定性
- **#1111 [BUG]**: Cron会话归档无视觉反馈 → 已由PR #1172修复，验证通过。  
- 无新增崩溃报告或生产级回归测试失败。当前Open Issues均为功能性优化，未触及核心稳定性模块。

## 6. 功能请求与路线图信号
- **ACP Agent over stdio (PR #119)**: 暴露Moltis作为外部系统代理，契合企业级API集成趋势，预计纳入下一版本核心模块。  
- **Instrumentation & Feedback Infrastructure (PR #1174)**: Langfuse导出、OTTL后端、用户反应采集，标志项目开始构建可观测性体系，属于长期路线图关键铺垫。  
- **PWA Push Notifications Reliability (PR #1173)**: 多设备同步通知策略完善，反映移动端体验优先级上升，可能成为v2.4亮点特性。

## 7. 用户反馈摘要
从Issue/PR描述提炼：
- ✅ 用户对Slack交互延迟敏感，迫切希望获得“接收中”等即时视觉确认（源于PR #1166上下文）。
- ⚠️ 管理员担忧privileged tools被非授权账户绕过（驱动PR #1170的权限重设计）。
- 💡 运维团队需要标准化CLI调试工具（促使PR #1175引入Terminal-Bench wrapper）。
- ❗ 无直接负面评论，但Archiving功能缺失暗示操作流程中存在隐性断点。

## 8. 待处理积压
- **PR #1166**: 涉及复杂状态机与Block Kit渲染，需额外Review时间，建议优先安排资深评审。
- **PR #1174**: Instrumentation框架依赖三方服务（Langfuse），存在兼容性风险，需提前mock测试覆盖。
- **PR #1173**: PWA通知策略跨浏览器行为不一致问题尚未完全解决，建议补充Chrome/Safari/Firefox专项测试矩阵。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# 项目动态日报 (CoPaw/QwenPaw)
**日期:** 2026-07-29
**分析者:** Agnes-2.0-Flash / Sapiens AI

### 1. 今日速览
过去24小时内，QwenPaw项目展现出极高的社区活跃度与开发强度。Issues共更新12条（活跃9条），PR合并/关闭达17条，其中包含多项核心模块的深度重构与关键Bug修复。整体项目运行稳健，但Windows端及配置文件的稳定性问题仍是当前主要痛点。新特性（如桌面自动化）的引入标志着项目正从“智能体框架”向更完整的Agent OS演进。

### 2. 版本发布
*   **状态:** 无新版本发布。当前最新稳定版仍为 `2.0.1`。
*   **注:** 虽无Release，但多个PR处于 `Close` 或 `Merged` 状态，累积的变更将在下一补丁或Beta版本中整合。

### 3. 项目进展 (今日重点 PR)
今日PR处理量巨大（50+），以下为对架构和用户体验影响较大的关键合并/更新项：
*   **#6151 [Refactor] 后台工具调用卸载机制**: 引入了双死锁架构 (`offload_deadline` + `kill_deadline`)，修正了背景任务取消信号误触发的问题。这提升了 Agent 在处理长耗时异步任务时的鲁棒性。 [链接](https://github.com/agentscope-ai/QwenPaw/pull/6151)
*   **#6269 [Feature] Workspace Checkpoint Management**: 引入了基于 Git 的会话影分身存档机制，解决了跨会话保存和恢复工作区状态的需求，是实现持久化智能体的重要一步。 [链接](https://github.com/agentscope-ai/QwenPaw/pull/6269)
*   **#6489 [Test] Driver 单元测试**: 将 Driver 子系统覆盖度从 0% 提升至回归保护阈值，填补了底层驱动测试的空白。 [链接](https://github.com/agentscope-ai/QwenPaw/pull/6489)
*   **网站文档更新 (#6330, #5940)**: GA 追踪优化、开发者日博客合集更新以及 2.0 版本的宣传素材落地，表明项目商业化与生态建设同步推进。 [链接](https://github.com/agentscope-ai/QwenPaw/pull/6330)

### 4. 社区热点 (高关注度 Issues/PRs)
以下 Issue 获得了社区较多的关注和讨论，反映了用户当下的核心关切：
*   **#6541 DeepSeek Context Compression Role Bug**: `scroll context compression` 模式下，压缩块角色错误导致 DeepSeek API 报错。该问题是模型接入层面的严重兼容性障碍。 [链接](https://github.com/agentscope-ai/QwenPaw/issues/6541)
*   **#6524 MCP 连接断连自动恢复**: 在使用 streamable_http 时，服务器重启后客户端无法感知 Session 失效，需手动刷新工具列表。这是企业级集成场景下常见的可用性问题。 [链接](https://github.com/agentscope-ai/QwenPaw/issues/6524)
*   **#6474 `view_video` 功能静默失败**: 报告称视频加载成功但实际未发送给 LLM，属于严重的功能缺陷，直接影响多模态能力。 [链接](https://github.com/agentscope-ai/QwenPaw/issues/6474)
*   **#6534 Windows NSIS 安装器死循环**: 即使程序未运行也提示“仍在运行”，导致安装卡死。此类体验阻碍了新用户的获取。 [链接](https://github.com/agentscope-ai/QwenPaw/issues/6534)

### 5. Bug 与稳定性
按严重程度排列的主要隐患如下：
1.  **高 - 系统文件损坏 (#6520)**: `agent.json` 在 Windows 环境下发生 BOM头、缺失引号等系统性编码损坏，可能导致配置完全失效。**已有 PR #6528 (Fix by mohitdebian)** 正在解决此问题。
2.  **中 - 安装器逻辑错误 (#6534)**: Windows 安装包存在自我检测死循环，严重阻碍分发。
3.  **中 - Skill Tag 丢失 (#6537)**: Skill Pool 中的标签在重启后消失，虽已写入 JSON 但未正确反序列化回 UI，属于 UI 与后端同步的回归 Bug。
4.  **低 - Mission 命令报错 (#6533)**: `/mission` command 触发 Python `TypeError`，参数传递不匹配，目前仅影响特定命令行操作。

### 6. 功能请求与路线图信号
基于 Issue 提交的趋势和 PR 的融合，可见以下发展方向：
*   **安全隔离优先**: Issue #6509 强烈要求 Sub Agent 间的隔离及会话 UUID 目录管理。结合 Feature PR #6269 (Checkpoint)，暗示下一版本将加强多线程/多用户环境下的上下文隐私保护和独立性。
*   **外部代理标准化**: Issue #6529 指出 ACP `new_session` 缺少 `models` 字段，导致外部客户端无法发现可用模型。这意味着项目正试图打造开放协议（ACP），**预计即将合并 PR #6531** 以完善标准，支持更多第三方工具集成。
*   **本地化桌面自动化**: PR #6424 添加了对 Windows/macOS 原生机器的 GUI 自动控制（Tauri mode），这是 QwenPaw 迈向通用操作系统的核心里程碑。

### 7. 用户反馈摘要
*   **痛点集中于 “数据可靠性”**: 用户最担心的是崩溃导致的数据丢失（Issue #6542 建议自动存档）、配置文件意外损坏（Issue #6520）以及视频工具不可用（Issue #6474）。
*   **期待“开箱即用”**: 对于视频播放、技能标签显示这样看似简单的功能却出现静默失败的情况，用户体验受损严重；用户希望这些基础功能能像官方文档描述的一样准确工作。
*   **部署便利性受挫**: 针对 Windows 安装器的反馈显示，非技术用户在进行第一次接触时被拦住了，这对开源项目的病毒式传播是不利的。

### 8. 待处理积压 (Backlog Review)
维护团队需关注以下需要人工介入或长时间未获得明确确认的项目：
*   **#6151 Background Tool Call Offload (Open, >14 days)**: 虽然代码功能强大，但由于涉及复杂的并发模型调优，Review 进度较慢。建议协调资深评审尽快合入以缓解长期阻塞。
*   **#5992 Per-session Model Overrides (Open, ~1 month)**: 这是一个非常有用的便捷功能，由新人贡献者提交，给予合并有助于鼓励社区新人。
*   **#6424 Computer Use Native Automation (Open)**: 涉及 Tauri 与原生 API 的深度绑定，平台适配复杂度高，需注意 macOS 与 Windows 分支的一致性问题。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

# ZeptoClaw 项目动态日报 (2026-07-29)

## 1. 今日速览
昨日（2026-07-28）ZeptoClaw 整体活跃度维持平稳水平，主要动作聚焦于依赖项自动化更新。项目过去 24 小时内没有收到新的 Issue 报告，表明当前版本稳定性较好；同时完成了两轮 Docker 基线环境的 Rust 版本升级维护。整体项目健康状况优秀，无紧急阻塞风险。

## 2. 版本发布
**今日无新版本发布。**
本次迭代周期内未涉及新的功能特性或 Bug 修复发布，主要活动集中在开发环境的基础设施维护上。建议关注 PR #649 合并后生成的新版本日志。

## 3. 项目进展
今日有两项 Pull Requests 处理完毕/进行中，均为依赖维护性质：
*   **#613 [CLOSED] chore(deps): bump rust from 1.95-slim-trixie to 1.96-slim-trixie**: 已关闭并合并（或准备流程），完成了对现有 Rust 版本的常规升级，有助于获取上游安全补丁和性能优化。详情: [qhkm/zeptoclaw PR #613](https://github.com/qhkm/zeptoclaw/pull/613)
*   **#649 [OPEN] chore(deps): bump rust from 1.95-slim-trixie to 1.97-slim-trixie**: 处于审查阶段，该 PR 进一步将基础镜像中的 Rust 版本更新至 1.97，跳过了 1.96 直接更新到更高版本以保持代码库的时效性。详情: [qhkm/zeptoclaw PR #649](https://github.com/qhkm/zeptoclaw/pull/649)

## 4. 社区热点
**今日无显著社区讨论或缺陷反馈。**
由于今天发生的均为 Dependabot 自动生成的机器 PR，且没有附带人工评论（Comment Count: undefined），说明此轮升级未引发异常冲突或社区争议，属于正常的 CI/CD 流水线操作。

## 5. Bug 与稳定性
**今日无新报告的 Bug。**
Issue Tracker 显示过去 24 小时新增及活跃 Issue 数量为 0，这表明项目当前的测试覆盖率和构建流程能够有效捕获潜在问题，或者用户近期未遇到需要上报的环境故障。

## 6. 功能请求与路线图信号
虽然今日没有收到功能性 Feature Request，但通过观察 PR #649 的开发逻辑可以看出维护团队对 **容器化部署体验** 的重视。频繁更新 Docker 镜像中的 Rust 版本意味着项目在坚持保持其作为智能体开发框架的技术栈处于前沿状态，这通常是高性能 Agent 任务执行的必要前提。

## 7. 用户反馈摘要
**无可提取的具体用户反馈。**
因今日 Issues 数为零，未能收集到关于使用场景、痛点满意度的具体文本信息。仅能从自动更新的意图侧面反映出用户对保持工具链最新版本的需求。

## 8. 待处理积压
*   **PR #649**: 目前状态为 Open，距离创建时间较短，暂无长期积压问题。维护者需留意该 PR 的检查结果（Checks），确保 CI 环境支持新版 Rust 镜像的特性。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw 项目动态日报（2026-07-29）

## 1. 今日速览
项目在过去24小时内保持极高活跃度：**49 条 Issue**（含 30+ 评论讨论），**50 条 PR**（待合并池达 50，无合并/关闭记录）。整体呈现“高并发开发、维护 backlog 堆积”态势：大量 RFC 进入评审阶段，但 PR 合并滞后可能影响迭代节奏。安全风险修复与架构重构并重，核心模块（Runtime、Channels、Providers）集中爆发问题与改进需求。

---

## 2. 版本发布
> **无新版本发布**。当前基于 `master` 分支最新提交（`f75b36a27` 等），预计后续将根据累积的 PR 与 RFC 决策推进 v0.8.x 或 v0.9.0 版本更新。

---

## 3. 项目进展
尽管当日 **0 条 PR 被合并**，但有 50 条 PR 处于开放状态，其中多件为高优先级（p1/p2）且已获 maintainer review 或 author action 标记，如：
- **#9419** [fix(providers): rotate live credentials after rate limits] — 解决认证凭证轮换逻辑缺陷，保障 provider 稳定性。
- **#9478** [fix(channels): notify sender when reply-intent precheck declines] — 优化用户体验，避免 Telegram 通道无声拒绝。
- **#9410** [fix(security): default command audit logging to disabled] — 安全基线调整，减少默认暴露面。

虽未合并，但这些 PR 已进入最终审查或作者待确认阶段，预示即将密集交付。

---

## 4. 社区热点
### 最活跃 Issue：#9127 [RFC: Abstract a `KeySource` trait] — 8 条评论  
> 涉及密钥材料抽象化与安全域分离，是底层加密架构的重大 refactor，反映团队对“最小权限 + 可审计密钥管理”的深度追求。链接：[#9127](https://github.com/zeroclaw-labs/zeroclaw/issues/9127)

### 最受关注 PR：#8965 [feat(skills): declarative auto-activation...] — 评论数 undefined（但标注 size:XL）  
> 实现技能声明式自动激活能力，支持图像触发与 Provider 切换，显著降低配置复杂度，符合当前 AI Agent 工具链轻量化趋势。链接：[#8965](https://github.com/zeroclaw-labs/zeroclaw/pull/8965)

### 高频讨论主题：
- **安全性**：多条 RFC/Bug 围绕 secrets 处理、auth token 旋转、渠道 credential 校验展开。
- **架构演进**：多个 RFC（#9487, #9488, #8850）推动运行时中心化、插件化、附件统一架构。
- **可观测性与调试**：telemetry attribution、SOP job cancellation、stderr 日志隔离等请求凸显生产环境监控不足。

---

## 5. Bug 与稳定性（按严重程度排序）

| ID | 标题 | 类型 | 严重性 | Fix Status |
|----|------|------|--------|------------|
| #9474 | auth profile store fails to load — `model_provider` required with no migration from pre-rename stores | bug | S1 (workflow blocked) | ✅ Closed (2026-07-28) |
| #9357 | cargo test -p zeroclaw-runtime --lib fails on master in 19 of 20 runs... | bug | S2 (degraded behavior) | ✅ Closed (2026-07-28) |
| #8654 | skill-review fork panics → daemon SIGSEGV after tool-heavy turn | bug | S2 (degraded behavior) | ⚠️ Open (in-progress) |
| #9486 | High-entropy detector redacts Solana wallet addresses, and high_entropy_tokens=false does not stop it on the channel path | bug | S2 (major workflow degradation) | ⚠️ Open (newly filed) |
| #7904 | always-inject SKILL.md frontmatter no longer works in compact prompt mode | bug | S2 (degraded behavior) | ⚠️ Open (in-progress) |

> **关键观察**：稳定性问题集中于 Runtime 单元测试、Agent 内存安全、Channel 输入验证与 Security Detector 误报。多数已有 fix PR 或处于进行中，但未见合并动作，需警惕回归风险。

---

## 6. 功能请求与路线图信号

### 近期纳入可能性高的功能：
- **MCP image pipeline mapping** (#9521 Feature)：将 MCP `type:image` 块映射到 Vision Pipeline，增强多模态处理能力。已有 PR #9405 支持自定义 CA trust，暗示多 provider 集成加速中。
- **ACP embedded resource blob + deliver_file** (#9178 Feature)：已 closed，说明已完成设计，可能随下一个 release 推出。
- **Runtime-owned conversation sessions** (#9487 RFC)：提议将 WebSocket/Web/Dashboard/ACP 作为 transport adapters，指向未来“单一事实来源”架构，极可能是 v0.9 核心特性。

### 长期愿景信号：
- **Wasm plugin-based channels/tools** (#8850 RFC)：移除编译时特性标志，改用运行时 WASM 插件——彻底松耦合模块系统，适合生态扩展。
- **ZeroCode modifier semantics independence** (#9171 Feature)：解耦按键修饰符语义，提升跨平台一致性，表明 TUI 体验升级计划启动。

---

## 7. 用户反馈摘要

从 Issue 评论内容提炼真实痛点：

✅ **满意点**：
- ACP 代理资源嵌入方案 (#9178) 获得作者认可，“drafted with Codex”显示智能辅助工作流被采纳。
- Telegram 通知改进 (#9478) 针对“仅表情回复无文本”的明确抱怨，属典型 UX 修复。

❌ **不满意/痛点点**：
- “empty allowed_groups admits every group” (#9397 RFC) —— 安全预期与实际行为不符，用户希望默认 deny-by-default。
- “context meter severely undercounts image-heavy requests” (#9332 Bug) —— billing/quotas 计算失真，直接影响成本控制。
- “agent returns idle after context exhaustion without terminal status” (#8758 Bug) —— 用户无法判断任务是否挂起还是完成，缺乏可预测性。

场景关键词：*cloud deployment, multi-channel orchestration, cost-aware prompting, enterprise-grade security auditing*

---

## 8. 待处理积压

以下 Item 需注意，部分已持续数周：

| 类型 | ID | 描述 | 风险等级 |
|------|-----|------|----------|
| RFC | #8691 | Restore ADR baseline and audit accepted RFC decision records — 文档治理缺失可能导致技术债务累积 | Medium |
| Tracker | #8692 | Maintainer decision queue for RFCs and design issues — 维护者决策队列阻塞新想法落地 | High |
| CI/Test | #9462 | zeroclaw-plugins lib unit tests behind plugins-wasmtime feature never execute in CI — 测试覆盖率盲区间 | Medium |
| Dependency | #9383 | npm audit failed — 6 个高危依赖项未更新 | Critical |
| Docs | #9242 | Telegram setup guide replaced — 虽已修复，但需确认是否有其他通道文档缺失 | Low-Medium |

> 📌 **特别提醒**：50 条 PR pending merge + 30+ issue threads awaiting maintainer review = **维护者过载警告**。建议设立 PR triage 小组或自动化 merge gatekeeper 以提升交付速度。

--- 

📊 **健康度评分（自定）**：  
功能性 ★★★★☆（功能丰富但交付慢）  
稳定性 ★★★☆☆（Bug 频发有 fix 但未 merge）  
安全性 ★★★★★（高度敏感，频繁审计与 RFC）  
社区参与度 ★★★★★（活跃讨论，贡献者多元）  

> 数据来源：GitHub API / Issue & PR Metadata @ 2026-07-29 UTC

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*