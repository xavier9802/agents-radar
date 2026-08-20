# AI CLI 工具社区动态日报 2026-08-20

> 生成时间: 2026-08-20 01:38 UTC | 覆盖工具: 10 个

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Pi](https://github.com/badlogic/pi-mono)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [DeepSeek TUI](https://github.com/Hmbown/DeepSeek-TUI)
- [Grok Build](https://github.com/xai-org/grok-build)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## 横向对比



# AI CLI 工具生态横向对比分析报告
**日期：2026-08-20**

---

## 1. 生态全景

2026年8月，AI CLI 工具生态呈现**多极竞争、快速迭代、标准化诉求升温**三大特征。Claude Code、OpenAI Codex、Gemini CLI 三大头部产品持续以周级节奏发布，分别聚焦模型能力扩展、成本控制与安全加固、子代理稳定性。开源替代品 OpenCode、Pi、Qwen Code 社区活跃度极高，Issues/PR 数量领先，反映开发者对自主可控生态的强烈诉求。与此同时，**跨工具标准化（AGENTS.md）、多账号/跨平台身份互通、子代理可靠性**成为行业共性痛点，提示生态正从功能竞赛转向工程化成熟度竞争。

---

## 2. 各工具活跃度对比

| 工具 | Release | Issues | PR | 关键动态 |
|------|---------|--------|-----|----------|
| **Claude Code** | v2.1.237, v2.1.236 | 10 | 1 | 发布事故（原生包未发布）、简洁输出风格上线 |
| **OpenAI Codex** | rust-v0.149.0-alpha.2 | 10 | 11 | 安全信任链强化、Git命令分类重构 |
| **Gemini CLI** | v0.56.0, v0.57.0-preview.0 | 10 | 10 | Gemini 3.x Flash 系列支持、子代理恢复修复 |
| **GitHub Copilot CLI** | v1.0.81 系列×4 | 27 | — | 高频补丁迭代，MCP/权限回归问题集中爆发 |
| **OpenCode** | — | 50 | 50 | 社区最活跃，会话完整性+计费透明度双热点 |
| **Pi** | — | 10 | 10 | 跨会话状态隔离、Bedrock Mantle 支持 |
| **Qwen Code** | v0.21.14 | 10 | 10 | SWE-bench 全量通过，Agent Board MVP 推进 |
| **Kimi Code CLI** | — | 1 | 0 | ACP 集成兼容性问题，活跃度偏低 |
| **DeepSeek TUI** | v0.9.10 | — | — | 稳定性治理，内存/审批持久化修复 |
| **Grok Build** | — | — | — | 无活动 |

---

## 3. 共同关注的功能方向

| 方向 | 涉及工具 | 具体诉求 |
|------|----------|----------|
| **子代理/Agent 稳定性** | Claude Code、Gemini CLI、OpenCode、Qwen Code | 子代理挂起恢复、工具可见性、跨 Agent 协作契约 |
| **跨工具标准化** | Claude Code、Gemini CLI、OpenCode | AGENTS.md 统一标准（#6235 获 4677 👍） |
| **多平台/跨端身份** | Claude Code、Codex、Pi、Gemini CLI | 多账号切换、Desktop/CLI 连接器互通、CVP 跨端一致 |
| **会话管理与持久化** | Claude Code、OpenCode、Pi、Qwen Code | 会话历史丢失、中断恢复、乐观渲染 |
| **成本控制** | Codex、OpenCode | 调用批处理优化、用量透明度、异常计费反馈 |
| **Windows 适配** | Codex、Pi、Copilot CLI | 浏览器插件信任链、键位冲突、终端渲染 |
| **安全与权限管控** | Codex、Gemini CLI、Qwen Code | Git 命令信任分类、MCP OAuth、PAT 隔离沙箱 |
| **模型兼容性** | Pi、Qwen Code、Gemini CLI | 多模型路由、reasoning_details 支持、OpenAI 兼容提供商适配 |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|----------|----------|----------|
| **Claude Code** | 输出风格控制、跨会话协作、模型环境变量 | 企业开发者、Claude 生态用户 | 闭源+高度集成 Anthropic 模型栈 |
| **OpenAI Codex** | 成本控制、安全信任链、Rust 重写 | 注重 ROI 的 Pro/Business 用户 | Rust 原生、聚焦代码执行安全性 |
| **Gemini CLI** | 子代理体系、Flash 系列模型、沙箱执行 | 多平台 Linux 用户、Wayland 生态 | Google 模型栈、强调 bash 原生能力 |
| **GitHub Copilot CLI** | 企业权限管控、MCP 协议兼容、快速补丁 | 已订阅 GitHub Enterprise 用户 | 高频迭代、回归修复驱动 |
| **OpenCode** | 会话完整性、热重载、Skills 生态 | 开源爱好者、自定义工作流重度用户 | Go 编写、高度可配置、插件化 |
| **Pi** | 跨会话状态隔离、Bedrock 支持、TUI 性能 | 多模型路由用户、本地部署场景 | 支持 OpenAI/Bedrock/Gemini 多提供商 |
| **Qwen Code** | Agent 协作编排、SWE-bench 验证、钉钉集成 | 中文用户、企业 CI/CD 场景 | 阿里模型栈、测试驱动开发 |
| **Kimi Code CLI** | ACP 编辑器集成 | Zed/Cursor 用户 | 较保守迭代，聚焦 IDE 深度绑定 |
| **DeepSeek TUI** | 内存治理、i18n 本地化 | 中文用户、资源受限环境 | Rust TUI、轻量级定位 |

---

## 5. 社区热度与成熟度

| 维度 | 头部梯队 | 快速迭代梯队 | 观察期 |
|------|----------|--------------|--------|
| **社区活跃度** | OpenCode (50I/50P)、Copilot CLI (27I) | Gemini CLI、Qwen Code (各10I/10P) | Kimi Code、Grok Build |
| **发布频率** | Copilot CLI (4补丁/天)、Claude Code (2版本/天) | Gemini CLI、Qwen Code | DeepSeek TUI、Pi |
| **问题密度** | Claude Code (发布事故+标准化诉求)、Codex (Windows痛点集中) | OpenCode (计费信任危机) | Kimi Code (低活跃) |
| **成熟度信号** | SWE-bench 全量通过 (Qwen)、Agent Board MVP (Qwen)、跨会话协作 (Claude) | 子代理恢复机制 (Gemini)、安全信任链重构 (Codex) | — |

**判断：** OpenCode 和 Copilot CLI 社区规模最大但问题也最密集，反映高采用率伴随高期望；Qwen Code 在保持活跃的同时通过 SWE-bench 验证建立可信度；Gemini CLI 技术进展扎实但社区讨论相对收敛。

---

## 6. 值得关注的趋势信号

### 6.1 标准化从诉求走向落地临界点
Claude Code #6235 AGENTS.md 提案获 4677 👍，远超其他 Issue，表明社区对**跨工具 agent 配置统一标准**的渴求已积累至峰值。预计未来 6-12 个月将出现事实标准或联盟推动的规范。

### 6.2 子代理可靠性成为下一阶段竞争壁垒
Gemini CLI（#21409 generalist agent 挂起）、Claude Code（#85230 子 Agent 丢失 MCP 工具）、OpenCode（#37852 会话中断）均将子代理稳定性列为高频痛点。**谁能率先解决子代理的可靠恢复与工具可见性，谁就能在企业级工作流中建立优势。**

### 6.3 Windows 适配仍是开源 CLI 工具的集体短板
Codex（#39136 浏览器插件信任链）、Pi（#7547 Windows 体验汇总）、Copilot CLI（#4390 企业模型缺失）均出现 Windows 专项问题。反映**跨平台一致性**是当前 CLI 工具从个人开发者走向企业部署的关键瓶颈。

### 6.4 成本控制从隐性需求变显性 KPI
Codex #35050 提出 GPT-5.6 批处理可降低 27-45% 费用，OpenCode #43409/#43416 反映用户对计费透明度的信任危机。**成本可观测性与优化能力**正在成为企业选型的关键指标，而非单纯模型质量。

### 6.5 安全从"功能属性"升级为"架构属性"
Codex #39524 移除 Git 命令天然安全分类、Qwen Code #9089/#9214 推进 PAT 隔离沙箱、Gemini CLI #28898 加固 subprocess 安全。安全不再仅是附加特性，而是**架构设计的第一性原理**，尤其影响企业用户部署决策。

---

**总结：** AI CLI 工具生态正从"模型能力竞赛"转向"工程可靠性+标准化+成本效率"的综合竞争。开发者选型时建议关注：子代理稳定性、跨平台一致性、计费透明度、以及标准化接口（AGENTS.md）的兼容进度。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告（截至 2026-08-20）

---

## 1. 热门 Skills 排行

| 排名 | Skill / PR | 功能说明 | 社区关注点 | 状态 |
|------|-----------|---------|-----------|------|
| 1 | [#1367](https://github.com/anthropics/skills/pull/1367) — Self-Audit | 交付前机械验证 + 四维推理质量门禁 | 通用质量门控，适用于任意项目/模型 | 🟢 Open |
| 2 | [#1298](https://github.com/anthropics/skills/pull/1298) — fix(skill-creator) eval | 修复 `run_eval.py` 召回率恒为 0% 的致命 bug | skill 描述优化循环依赖此脚本，bug 导致优化失效 | 🟢 Open |
| 3 | [#514](https://github.com/anthropics/skills/pull/514) — document-typography | 检测孤行、寡行、编号错位等排版问题 | 通用文档质量问题，用户反馈频繁 | 🟢 Open |
| 4 | [#723](https://github.com/anthropics/skills/pull/723) — testing-patterns | 覆盖单元测试、React 组件测试、AAA 模式等全栈测试 | 测试最佳实践被广泛需求 | 🟢 Open |
| 5 | [#568](https://github.com/anthropics/skills/pull/568) — ServiceNow | 覆盖 ITSM/ITOM/FSM/Security 等企业服务台全流程 | 企业场景落地需求强 | 🟢 Open |
| 6 | [#486](https://github.com/anthropics/skills/pull/486) — ODT | OpenDocument 格式（.odt/.ods）创建、填充、转换 | 补充 LibreOffice / ISO 标准文档生态 | 🟢 Open |
| 7 | [#83](https://github.com/anthropics/skills/pull/83) — skill-quality/security-analyzer | 从结构、文档、示例、安全等五维度评估 Skill 质量 | 社区自建 Skill 质量保障工具 | 🟢 Open |
| 8 | [#181](https://github.com/anthropics/skills/pull/181) — SAP-RPT-1-OSS | 基于 SAP 开源表格基础模型做业务数据预测 | SAP 生态 + 预测分析交叉场景 | 🟢 Open |

---

## 2. 社区需求趋势

从 Issues 高频议题提炼四大方向：

**① 企业级垂直场景**（Issue #228、#568、#181）
- 组织内 Skill 共享（Issue #228，👍 8）呼声强烈，当前需手动分发 .skill 文件体验差
- ServiceNow、SAP 等企业平台 Skill 需求集中

**② 输出质量与安全性**（Issue #492、#1367、#1385）
- Issue #492（43 条评论）：社区 Skill 冒用 `anthropic/` 命名空间导致信任边界风险，安全问题最突出
- Self-Audit 和推理质量门禁（Issue #1385）是质量保障的主流思路

**③ 工具链健壮性**（Issue #556、#1099、#1050）
- `run_eval.py` 在 Windows 上大量 Bug（Issue #556、PR #1099、#1050），影响 Skill 开发和评测循环
- skill-creator 最佳实践有待完善（Issue #202）

**④ 代码质量与测试**（Issue #723、#1329）
- testing-patterns 被反复讨论；compact-memory（Issue #1329）解决长会话上下文膨胀问题

---

## 3. 高潜力待合并 Skills

以下 PR 评论活跃、指向明确、且属于基础能力补强或广泛痛点，近期合并概率较高：

| PR | 潜力理由 |
|----|---------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `run_eval.py` 是 Skill 优化循环的核心基础设施，Bug 被 10+ 人独立复现，修复优先级最高 |
| [#1367](https://github.com/anthropics/skills/pull/1367) | Self-Audit 通用性强，与 Issue #1385 质量门控提案高度契合，社区认可度高 |
| [#514](https://github.com/anthropics/skills/pull/514) | 文档排版是 Claude 生成内容的通用痛点，技术实现独立清晰 |
| [#723](https://github.com/anthropics/skills/pull/723) | 测试领域 Skill 长期缺失，覆盖面全，PR 质量扎实 |
| [#486](https://github.com/anthropics/skills/pull/486) | 填补 ODT 格式空白，与现有 DOCX/PDF Skill 形成互补 |
| [#83](https://github.com/anthropics/skills/pull/83) | 社区自建 Skill 质量评估刚需，支持生态健康发展 |

---

## 4. Skills 生态洞察

> **当前社区最集中的诉求是：在补齐企业级垂直场景（ServiceNow/SAP/ODT）的同时，优先解决 Skill 开发工具链（eval 脚本 Windows 兼容性、安全命名空间治理）的可靠性问题，让自建 Skill 的质量保障和分发体验跟上官方 Skill 的增长速度。**

---



# Claude Code 社区动态日报
**2026-08-20**

---

## 1. 今日速览

Claude Code 发布 v2.1.237 和 v2.1.236 两个版本，引入"简洁输出风格"、默认模型环境变量及跨会话消息能力。v2.1.237 的 npm 包存在原生平台包未发布的发布事故，同时 AGENTS.md 标准化提案仍为社区最热门需求（4677 👍）。

---

## 2. 版本发布

### v2.1.237
- 修复了使用 LLM 网关或自定义 Base URL 时 prompt caching 失效的问题
- 新增内置"Concise"输出风格：Claude 将直接输出结果，跳过前言和叙述，功能完整度不变。在 `/config` 的 Output style 中选择
- 🔴 **已知问题**：`linux-x64`、`win32-x64` 和 `linux-x64-musl` 三个平台包未实际发布，安装后为无效 stub（Issue #88103）

### v2.1.236
- 新增 `ANTHROPIC_DEFAULT_MODEL` 环境变量：控制新会话的默认模型，可通过 `/model` 覆盖并持久化（区别于 `ANTHROPIC_MODEL`）
- 新增跨会话消息能力：`SendMessage` 支持 `notify_when_idle` 参数，可通知另一 Claude Code 会话

**链接：**
- v2.1.237: https://github.com/anthropics/claude-code/releases/tag/v2.1.237
- v2.1.236: https://github.com/anthropics/claude-code/releases/tag/v2.1.236

---

## 3. 社区热点 Issues

| 排名 | Issue | 亮点 | 关注度 |
|------|-------|------|--------|
| 1 | [#6235] AGENTS.md 标准化支持 | 社区推动统一 agents.md 标准，与 Codex/Cursor 等对齐 | 👍 4677 / 💬 362 |
| 2 | [#77136] Opus 4.8/5.0 行为问题 | 4.8 语气"有毒"，5.0 输出"不可靠"，影响协作体验 | 👍 198 / 💬 31 |
| 3 | [#36151] 移动应用多账号切换 | 无共享邮箱的多账号登录需求 | 👍 611 / 💬 160 |
| 4 | [#80988] heron_brook 提示注入 | v2.1.219 硬编码系统提示覆盖用户委托策略，无退出选项 | 👍 57 / 💬 30 |
| 5 | [#84352] CVP 认证组织仍被拦截 | Cyber Verification Program 通过的组织在 Claude Code 中仍触发安全拦截 | 👍 20 / 💬 127 |
| 6 | [#32479] GitHub Connector 跨应用不互通 | Desktop 中连接的 GitHub 在 Claude Code 中不被识别 | 👍 140 / 💬 89 |
| 7 | [#29017] VSCode 会话历史丢失 | macOS VSCode 扩展会话记录丢失问题 | 👍 20 / 💬 30 |
| 8 | [#15178] Plugin Skills 未注入上下文 | 插件技能加载但不出现在 `<available_skills>` 中，AI 无法感知 | 👍 33 / 💬 22 |
| 9 | [#88054] `claude remote-control` OAuth 24h 过期不刷新 | 服务器在 401 后退出，所有绑定会话中断 | 👍 0 / 💬 1 |
| 10 | [#85230] 后台子 Agent 丢失 MCP 资源工具 | 子 Agent 默认无法访问 `ListMcpResourcesTool` 等 MCP 工具 | 👍 0 / 💬 1 |

**相关链接：**
- #6235: https://github.com/anthropics/claude-code/issues/6235
- #77136: https://github.com/anthropics/claude-code/issues/77136
- #36151: https://github.com/anthropics/claude-code/issues/36151
- #80988: https://github.com/anthropics/claude-code/issues/80988
- #84352: https://github.com/anthropics/claude-code/issues/84352
- #32479: https://github.com/anthropics/claude-code/issues/32479
- #29017: https://github.com/anthropics/claude-code/issues/29017
- #15178: https://github.com/anthropics/claude-code/issues/15178
- #88054: https://github.com/anthropics/claude-code/issues/88054
- #85230: https://github.com/anthropics/claude-code/issues/85230

---

## 4. 重要 PR 进展

过去 24 小时内仅 1 条 PR 更新：

| PR | 说明 |
|----|------|
| [#77977] docs(plugin-dev): document skipLfs marketplace sources | 补充插件开发文档，说明 marketplace 源中 `skipLfs` 选项的用法，支持 GitHub 简写和通用 Git URL 跳过 LFS 下载 |

- 链接: https://github.com/anthropics/claude-code/pull/77977

---

## 5. 功能需求趋势

基于 Issue 数据提炼社区关注方向：

| 趋势方向 | 典型 Issue | 说明 |
|----------|-----------|------|
| **标准化互操作** | #6235 | AGENTS.md 成为跨工具 agent 配置统一标准的核心诉求 |
| **多账号/跨平台身份** | #36151, #32479, #84352 | 移动多账号、桌面与 CLI 间连接器互通、CVP 认证跨端一致 |
| **模型行为可控性** | #77136, #80988 | 用户对系统提示注入和模型输出风格控制需求强烈 |
| **插件/技能系统** | #15178, #85230 | 插件技能发现和子 Agent MCP 工具传递是高频痛点 |
| **会话管理** | #29017, #67835, #69836 | 会话历史持久化、归档/取消归档、命名会话 |
| **跨会话协作** | v2.1.236 | 官方新增 `SendMessage` 跨会话通知，#62426 多实例速率限制诉求 |

---

## 6. 开发者关注点

**痛点汇总：**

1. **发布/安装稳定性** — v2.1.237 原生包未发布、自动更新静默推送无效安装（#88103, #86941），直接影响用户体验

2. **系统提示注入失控** — 用户认为 `heron_brook` 等内部提示段硬编码覆盖自定义策略（#80988），且无退出选项

3. **多端身份与权限割裂** — CVP 认证在 Desktop 通过但在 CLI 被拦截（#84352）、GitHub Connector 在 Desktop 和 CLI 间不共享（#32479）

4. **模型版本质量差异** — Opus 4.8/5.0 的用户体验问题引发集中反馈（#77136），反映用户对模型行为一致性的期待

5. **插件生态可见性** — 插件技能无法被 AI 感知（#15178），后台子 Agent 丢失 MCP 工具（#85230），制约复杂工作流搭建

6. **Windows 平台稳定性** — GPU 崩溃（#81698）、终端渲染损坏（#79025）、自动关机异常（#76249）等多条 Windows 专项 Bug

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-08-20**

---

## 1. 今日速览

OpenAI Codex 发布 `0.149.0-alpha.2` Rust 版本，社区重点聚焦 Windows 平台的浏览器插件信任链问题（#39136，41👍）以及 GPT-5.6 在 Code Mode 中调用序列化的优化建议（#35050，40👍）。安全层面，多个 PR 合并修复了 Git 命令信任分类和 MCP OAuth 相关风险。

---

## 2. 版本发布

### `rust-v0.149.0-alpha.2`
- 最新 alpha 版本发布，具体变更需查看 release notes。
- [GitHub Release](https://github.com/openai/codex/releases)

---

## 3. 社区热点 Issues

| # | 标题 | 评论 | 👍 | 亮点 |
|---|------|------|-----|------|
| #39136 | 内置浏览器插件初始化失败：受信任 RPC 依赖不在可信代码路径中 | 78 | 41 | Windows 平台高频故障，影响浏览器功能 |
| #35050 | GPT-5.6 序列化独立 Code Mode 调用，显式批处理可降低 27–45% 费用 | 24 | 40 | 直接关联成本控制，Pro/Business 用户关注 |
| #25178 | Windows Computer Use 截图在 Windows 10 22H2 上失败 | 28 | 15 | 远程操作功能受阻，Windows 10 用户痛点 |
| #39318 | 浏览器控制失败：信任 RPC 依赖问题（同一根因） | 21 | 2 | #39136 的关联复现 |
| #38350 | 计划任务成功后自动禁用，未获用户授权 | 21 | 0 | Web 端自动化功能异常 |
| #39239 | Windows thread/archive 失败：路径重复导致 os error 2 | 17 | 0 | 会话归档稳定性问题 |
| #28950 | Chrome 插件安装失败：Native Messaging Host 未创建 | 12 | 0 | 插件安装生命周期缺陷 |
| #38754 | 本地 stdio MCP 服务器在单次任务内重复 spawn 且未被回收 | 10 | 2 | 资源泄漏，影响性能 |
| #22486 | 上下文压缩使用可配置模型，独立于会话模型 | 5 | 6 | 功能增强需求，CLI 用户呼声高 |
| #39552 | macOS 恢复持久化 Google 登录标签页导致渲染进程 100% CPU | 3 | 0 | 浏览器性能回归 |

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 说明 |
|----|------|------|------|
| #39524 | Stop treating Git commands as inherently safe | ✅ CLOSED | 移除 Git 命令的"天然安全"分类，防止仓库配置导致不可信 helper 执行 |
| #39520 | Isolate automatic plugin Git operations | ✅ CLOSED | 隔离插件后台 Git 操作，防止继承项目级 Git 配置 |
| #31155 | Fix: release thread writer after failed shutdown | ✅ CLOSED | 修复 rollout 持久化失败后 terminal session 的 writer 泄漏 |
| #39510 | Track built-in control tool calls in analytics | ✅ CLOSED | 新增 `codex_control_tool_call_event` 追踪 request_user_input、update_plan 等控制工具调用 |
| #39523 | Persist thread section moves before the first turn | ✅ CLOSED | 修复新 thread 首次 turn 前移动 section 不持久化的问题 |
| #39474 | Consolidate Guardian extensions into `codex-guardian-v2` | ✅ CLOSED | 统一 Guardian 扩展入口，移除冗余安装逻辑 |
| #39452 | Remove feature gate for async user messages | ✅ CLOSED | 对支持异步消息的模型默认启用 `send_user_message_async` |
| #39410 | Refresh expired AWS credentials for Bedrock | ✅ CLOSED | 新增 `aws.auth_refresh` 配置，支持 Bedrock 会话中自动刷新过期凭据 |
| #39515 | Use `mem::take` to drain unified exec output buffers | ✅ CLOSED | 代码优化，用标准库替代自定义 drain 实现 |
| #39514 | Use stored item types when materializing turn summaries | ✅ CLOSED | 修复 summary 生成时 item_type 为空时的回退逻辑 |

---

## 5. 功能需求趋势

- **成本控制与效率优化**：#35050 明确提出 GPT-5.6 调用批处理可显著降低费用，反映社区对 usage 优化的强烈需求。
- **Windows 平台稳定性**：近半数热点 Issue 集中在 Windows，涉及浏览器、Computer Use、MCP、会话归档等多模块，平台适配仍是重点。
- **安全信任链强化**：多个 PR 围绕 Git 命令安全、MCP OAuth issuer 校验、trusted code path 展开，安全审计持续加强。
- **上下文压缩可配置化**：#22486 提出让 context compaction 使用独立模型，CLI 用户期望更细粒度的模型控制。
- **自动化任务可靠性**：计划任务异常禁用（#38350）和 Android Remote 会话同步问题（#37385）反映用户对自动化稳定性的期待。

---

## 6. 开发者关注点

| 痛点/需求 | 关联 Issue/PR |
|-----------|---------------|
| Windows 浏览器插件信任链断裂，导致内置浏览器不可用 | #39136, #39318, #39562 |
| GPT-5.6 Code Mode 串行调用导致费用虚高 | #35050 |
| Computer Use 截图功能在 Windows 10 上完全失效 | #25178 |
| MCP 服务器资源泄漏（重复 spawn 未回收） | #38754, #38944 |
| 计划任务无端自动暂停/禁用 | #38350 |
| Chrome 插件 Native Messaging Host 注册失败 | #28950 |
| 上下文压缩模型不可独立配置 | #22486 |
| Windows 端鼠标输入卡顿（thinking 状态） | #39450 |
| 窗口频繁 resize 导致内存耗尽、应用无响应 | #39563 |
| Git 命令安全信任策略调整 | #39524, #39520 |

---

*数据来源：github.com/openai/codex | 生成时间：2026-08-20*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报
**日期：2026-08-20**

---

## 1. 今日速览

Gemini CLI 发布 v0.56.0 正式版及 v0.57.0-preview.0 预览版，核心亮点包括新增 Gemini 3.7/3.6/3.5 Flash 模型支持、子代理恢复逻辑修复及 subprocess 执行安全加固。社区持续关注子代理稳定性（generalist agent 挂起、browser agent Wayland 兼容性问题）及 Auto Memory 系统的可靠性改进。

---

## 2. 版本发布

### v0.56.0（正式版）
- 新增 Gemini 3.7 Flash、3.6 Flash、3.5 Flash-Lite 模型配置与选择支持
- 修复核心层空文本轮次（含工具调用或多媒体内容）被错误过滤的问题
- 改进 InvalidStreamError 错误信息传递至 UI，提供 `/compress` 等排查建议

**链接**: [v0.56.0 Release](https://github.com/google-gemini/gemini-cli/releases/tag/v0.56.0)

### v0.57.0-preview.0（预览版）
- 修复 Cloud Workstations OAuth 流程中 proxy redirect URI 动态解析问题
- 修复 IDE 连接中目录不匹配被吞掉的 bug
- 支持在 sandbox 中更精确地控制 DEBUG 环境变量语义

**链接**: [v0.57.0-preview.0 Release](https://github.com/google-gemini/gemini-cli/releases/tag/v0.57.0-preview.0)

---

## 3. 社区热点 Issues

| Issue | 标题 | 关注点 | 评论/👍 | 链接 |
|-------|------|--------|---------|------|
| #22323 | Subagent recovery after MAX_TURNS reported as GOAL success | 子代理达到最大轮次后错误地报告成功，掩盖了中断状态，影响调试与评估准确性 | 12 / 2 | [链接](https://github.com/google-gemini/gemini-cli/issues/22323) |
| #21409 | Generalist agent hangs | Generalist 子代理在执行简单任务（如创建文件夹）时永久挂起，影响核心工作流 | 8 / 8 | [链接](https://github.com/google-gemini/gemini-cli/issues/21409) |
| #19873 | Leverage model's bash affinity via Zero-Dependency OS Sandboxing | 提出利用 Gemini 3 模型的 bash 原生能力，通过零依赖沙箱增强代码探索能力 | 8 / 1 | [链接](https://github.com/google-gemini/gemini-cli/issues/19873) |
| #25166 | Shell command stuck with "Waiting input" | 简单 Shell 命令执行完成后仍显示"等待用户输入"，导致代理卡死 | 4 / 3 | [链接](https://github.com/google-gemini/gemini-cli/issues/25166) |
| #21983 | Browser subagent fails in Wayland | Browser 子代理在 Wayland 环境下失败，影响 Linux 用户浏览器自动化能力 | 4 / 1 | [链接](https://github.com/google-gemini/gemini-cli/issues/21983) |
| #26522 | Auto Memory retrying low-signal sessions indefinitely | Auto Memory 对低价值会话无限重试，浪费资源并可能导致记忆库污染 | 5 / 0 | [链接](https://github.com/google-gemini/gemini-cli/issues/26522) |
| #24246 | 400 error with >128 tools | 工具数量超过 128 个时触发 400 错误，限制大规模项目的使用体验 | 3 / 0 | [链接](https://github.com/google-gemini/gemini-cli/issues/24246) |
| #22672 | Agent should discourage destructive behavior | 建议模型在 git reset --force 等操作中使用更安全的替代方案，减少误操作风险 | 3 / 1 | [链接](https://github.com/google-gemini/gemini-cli/issues/22672) |
| #21968 | Gemini does not use skills/sub-agents enough | 用户反馈 Gemini 不会主动使用自定义 skills 和子代理，需手动指定 | 6 / 0 | [链接](https://github.com/google-gemini/gemini-cli/issues/21968) |
| #22267 | Browser Agent ignores settings.json overrides | Browser 子代理完全忽略 settings.json 中的配置覆盖（如 maxTurns），配置失效 | 3 / 0 | [链接](https://github.com/google-gemini/gemini-cli/issues/22267) |

---

## 4. 重要 PR 进展

| PR | 类型 | 内容摘要 | 链接 |
|----|------|----------|------|
| #28910 | feat | 新增 Gemini 3.7 Flash、3.6 Flash、3.5 Flash-Lite 模型配置与选择支持 | [链接](https://github.com/google-gemini/gemini-cli/pull/28910) |
| #28892 | fix | 修复核心层空文本轮次（含工具调用或多媒体内容）被错误过滤的问题 | [链接](https://github.com/google-gemini/gemini-cli/pull/28892) |
| #28898 | fix | 加固 subprocess 执行安全，防止敏感认证 token 泄露到不受信任的工具执行环境 | [链接](https://github.com/google-gemini/gemini-cli/pull/28898) |
| #28922 | feat | 实现 GCS 轨迹日志和调试工件持久化，支持生产/评估运行的事后分析 | [链接](https://github.com/google-gemini/gemini-cli/pull/28922) |
| #28863 | fix | 扩展更新时强制用户 consent 检查，并清理可能改变运行时的环境变量注入 | [链接](https://github.com/google-gemini/gemini-cli/pull/28863) |
| #28655 / #28917 | fix | Whisper 模型下载改为原子操作，失败时清理临时文件，避免损坏的模型残留 | [链接](https://github.com/google-gemini/gemini-cli/pull/28655) [链接](https://github.com/google-gemini/gemini-cli/pull/28917) |
| #28916 | fix | Whisper 转录输出流增加行缓冲，修复多行时间戳被截断丢失的问题 | [链接](https://github.com/google-gemini/gemini-cli/pull/28916) |
| #28915 | fix | 统一 symlink 路径规范化，确保 `.geminiignore` 和 `.gitignore` 规则在符号链接下行为一致 | [链接](https://github.com/google-gemini/gemini-cli/pull/28915) |
| #28889 | fix | 恢复终端能力检测后 stdin 的 paused 状态，修复交互阻塞问题 | [链接](https://github.com/google-gemini/gemini-cli/pull/28889) |
| #28914 | fix | 将 on-retry 提示从 systemInstruction 移至 contents 末尾，保留 prefix caching 同时确保模型及时感知恢复提示 | [链接](https://github.com/google-gemini/gemini-cli/pull/28914) |

---

## 5. 功能需求趋势

1. **子代理稳定性与可观测性**：多个 Issue 聚焦于 subagent 挂起、恢复逻辑错误、行为不可见等问题，社区希望提升子代理的可靠性与调试体验。
2. **模型能力扩展**：新增 Gemini 3.x Flash 系列模型支持，以及利用模型 bash 原生能力的沙箱方案，反映对更强代码理解和执行能力的期待。
3. **记忆系统（Auto Memory）优化**：用户关注低信号会话去重、隐私脱敏和无效 patch 隔离，希望记忆系统更精准且安全。
4. **跨平台兼容性**：Wayland 下浏览器代理失败、symlink 路径处理不一致等问题，显示多平台适配需求持续存在。
5. **安全与权限管控**：subprocess 安全加固、扩展环境变量清理、用户 consent 强制检查等 PR 表明安全改进是当前重点方向。

---

## 6. 开发者关注点

- **子代理挂起与恢复**：generalist agent 和 browser agent 的稳定性是高频痛点，涉及 Wayland 兼容、settings.json 配置失效、maxTurns 边界处理等多个方面。
- **Shell 交互阻塞**：命令执行完成后仍显示"Waiting input"导致代理卡死，影响核心工作流体验。
- **工具数量限制**：超过 128 个工具时触发 400 错误，限制了大规模项目的可用性。
- **记忆系统可靠性**：Auto Memory 的低信号会话无限重试和隐私脱敏问题需要改进。
- **本地化体验**：Whisper 语音转录的流式处理和模型下载稳定性直接影响语音功能可用性。
- **配置一致性**：symlink、settings.json 覆盖、DEBUG 标志等配置项的行为不一致引发开发者困扰。

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期**：2026-08-20  
**数据源**：github.com/github/copilot-cli

---

## 1. 今日速览
今日 Copilot CLI 社区以 `1.0.81` 系列快速迭代为主，官方在 24 小时内连续发布 4 个补丁版本，集中修复 MCP 握手、环境变量传递及 Sandbox 策略冲突等回归问题。社区焦点集中在企业级权限管控失效、MCP OAuth 协议兼容性以及并行子 Agent 导致终端 UI 卡死等高频痛点，共追踪 27 条活跃 Issue。

---

## 2. 版本发布
| 版本 | 核心更新内容 |
|------|--------------|
| **v1.0.81-5** | 修复 agent 工作期间提交新 prompt 后，转录历史底部残留 `(pending)` 副本的显示问题（对应 #4532） |
| **v1.0.81-4 / 3 / 2** | 连续发布，主要包含多项内部修复与行为调整，针对 1.0.81 引入的 MCP 兼容性、策略覆盖及配置持久化问题进行紧急回退与优化 |

> 注：近期高频发版反映出 1.0.81 系列存在若干影响企业部署与 MCP 扩展的关键回归，建议生产环境谨慎升级并关注后续补丁。

---

## 3. 社区热点 Issues（Top 10）
1. **#4390** [CLOSED] 企业组织启用的模型（Claude Sonnet/Opus 5, Kimi K3）未出现在有效目录中。15条评论，7👍，已闭环。影响多模型编排体验。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-08-20** | 数据来源：[github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)

---

## 1. 今日速览

今日 Kimi Code CLI 社区无新版本发布，无 PR 合并。过去 24 小时内共更新 1 个 Issue（#2609），主要聚焦于 **ACP 集成模式下 Grep/Glob 工具不可用** 的问题，该 Issue 已由作者自行关闭。社区关注度较低，暂无新讨论。

---

## 2. 版本发布

> 过去 24 小时内无新版本发布。

---

## 3. 社区热点 Issues

| 序号 | Issue | 状态 | 关注理由 |
|------|-------|------|----------|
| 1 | [#2609](https://github.com/MoonshotAI/kimi-cli/issues/2609) Grep/Glob blocked in ACP runtime | ✅ CLOSED | 涉及 Zed 编辑器 ACP 集成场景下核心文件搜索工具不可用，影响部分开发者工作流 |

**Issue #2609 详情：**
- **作者**：SolomonFang
- **环境**：kimi-code CLI `0.37.1` / macOS / Zed ACP
- **问题**：在 ACP session 中，内置 `Grep` 和 `Glob` 工具始终报错 `ACP runtime only supports interactive Bash tool processes`；`Read` 工具工作正常。
- **社区反应**：0 条评论，0 👍，已由作者关闭（可能已在本地找到解决方案或自行修复）。

---

## 4. 重要 PR 进展

> 过去 24 小时内无 PR 更新。

---

## 5. 功能需求趋势

基于今日 Issue 数据，社区需求呈现以下方向：

- **IDE 深度集成**：ACP（Agent Control Protocol）场景下的工具兼容性仍是开发者关注重点，尤其是与 Zed、Cursor 等编辑器的协同。
- **文件搜索能力**：Grep/Glob 在特定运行模式下失效，反映出跨模式工具一致性问题亟待解决。

---

## 6. 开发者关注点

**当前痛点：**
- ACP 模式下 `Grep` / `Glob` 工具被限制，仅支持交互式 Bash 进程，影响自动化工作流
- 不同工具在 ACP 环境下的行为不一致（`Read` 正常，`Grep`/`Glob` 失败）

**高频需求：**
- 扩展 ACP runtime 对非交互式工具的支持
- 完善 ACP 与主流编辑器的兼容矩阵文档

---

*注：今日数据量较少，建议持续跟踪后续 Issue 及 PR 动态。*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode 社区动态日报 | 2026-08-20

## 1. 今日速览

过去24小时无新版本发布，但社区活跃度极高，共更新50条 Issues 和50条 PRs。最受关注的技术问题是 **Provider 流中断被错误记录为正常完成**（56赞），以及 **Bun 全局包 postinstall 脚本阻塞**问题。功能开发方面，**优化提示提交体验**、**Web UI 自动同步**、**Skills 热重载**等特性持续推进。

---

## 2. 版本发布

过去24小时内无新版本发布。

---

## 3. 社区热点 Issues

| # | 主题 | 状态 | 评论/赞 | 链接 |
|---|------|------|---------|------|
| #37852 | Provider 流中断被记录为正常完成（finish=unknown） | OPEN | 19 / 56 👍 | [Issue](https://github.com/anomalyco/opencode/issues/37852) |
| #27906 | v1.15.1+ 破坏 Bun 全局安装（postinstall 脚本限制） | OPEN | 24 / 14 👍 | [Issue](https://github.com/anomalyco/opencode/issues/27906) |
| #3028 | 一键切换所有 agent 的模型 | CLOSED | 15 / 2 👍 | [Issue](https://github.com/anomalyco/opencode/issues/3028) |
| #13626 | Web UI 自动从服务器同步项目 | OPEN | 12 / 15 👍 | [Issue](https://github.com/anomalyco/opencode/issues/13626) |
| #39876 | libopentui 临时文件耗尽磁盘（207GiB） | CLOSED | 3 / 1 👍 | [Issue](https://github.com/anomalyco/opencode/issues/39876) |
| #40955 | 中断时队列消息被静默丢弃 | OPEN | 2 / 0 | [Issue](https://github.com/anomalyco/opencode/issues/40955) |
| #43364 | Go 版本 luna session 加密验证失败 | OPEN | 8 / 3 👍 | [Issue](https://github.com/anomalyco/opencode/issues/43364) |
| #43409 | OpenCode Go 异常积分消耗（4小时内用尽42%额度） | OPEN | 3 / 0 | [Issue](https://github.com/anomalyco/opencode/issues/43409) |
| #43416 | 账单与订阅使用量不匹配 | OPEN | 6 / 0 | [Issue](https://github.com/anomalyco/opencode/issues/43416) |
| #43530 | MCP 连接空闲后触发速率限制 | OPEN | 2 / 0 | [Issue](https://github.com/anomalyco/opencode/issues/43530) |

**重点关注：**
- **#37852** 获得最高支持（56赞），涉及会话完整性问题——provider 中断后被当作正常完成处理，可能导致用户丢失生成内容且无错误提示。
- **#27906** 影响 Bun 用户群体的安装体验，是 v1.15.1 引入的兼容性问题。
- **#43409 / #43416** 反映用户对 Go 订阅计费的信任问题，需官方及时回应。
- **#39876** 揭示 macOS 下 TUI 临时文件管理缺陷，直接威胁用户磁盘空间。

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 作者 | 链接 |
|---|------|------|------|------|
| #43520 | 乐观提示提交：客户端生成 ID，立即渲染 | CLOSED | kitlangton | [PR](https://github.com/anomalyco/opencode/pull/43520) |
| #42810 | 简化中断续传逻辑，重构状态机 | CLOSED | kitlangton | [PR](https://github.com/anomalyco/opencode/pull/42810) |
| #43460 | 修复插件工具输入解码（兼容不同 effect 版本） | OPEN | argszero | [PR](https://github.com/anomalyco/opencode/pull/43460) |
| #43282 | 暴露有效的 subagent ID 供工具使用 | OPEN | argszero | [PR](https://github.com/anomalyco/opencode/pull/43282) |
| #43545 | 重构：模型限制由 Core 统一管理 | OPEN | opencode-agent[bot] | [PR](https://github.com/anomalyco/opencode/pull/43545) |
| #43541 | 默认未知模型为 200k 上下文 + 32k 输出限制 | CLOSED | opencode-agent[bot] | [PR](https://github.com/anomalyco/opencode/pull/43541) |
| #42681 | Linux Wayland 窗口显示 fallback | CLOSED | xdagiz | [PR](https://github.com/anomalyco/opencode/pull/42681) |
| #42978 | Desktop 显示当前 worktree 分支 | OPEN | liveonce | [PR](https://github.com/anomalyco/opencode/pull/42978) |
| #43538 | 配置文件热重载（实验性） | OPEN | mccaffrey-jonathan | [PR](https://github.com/anomalyco/opencode/pull/43538) |
| #43537 | Skills 加入斜杠自动补全并按来源分组 | OPEN | mccaffrey-jonathan | [PR](https://github.com/anomalyco/opencode/pull/43537) |

**亮点：**
- **#43520** 和 **#42810** 由 kitlangton 提交，优化了提示提交体验和中断处理逻辑，显著提升交互流畅度。
- **#43545 / #43541** 是 Core 模型管理的重大重构，统一处理未收录模型的 token 限制。
- **#43538** 引入实验性热重载功能，开发者可通过环境变量启用 config/skills/agents 自动热更新。
- **#43460** 解决了插件与 server 之间 effect 版本不匹配导致的工具输入解码失败问题。

---

## 5. 功能需求趋势

从 Issues 中提炼出以下社区关注方向：

| 方向 | 关注点 | 相关 Issue/PR |
|------|--------|---------------|
| **会话体验优化** | 中断恢复、消息不丢失、乐观渲染 | #37852, #40955, #43520 |
| **模型管理** | 跨 agent 统一切换模型、模型限制默认值 | #3028, #43545, #43541 |
| **Web/桌面同步** | 多设备自动同步、工作树分支显示 | #13626, #42978 |
| **MCP/插件生态** | 本地插件发现、热重载、SEA 安全加载 | #41530, #42485, #43538 |
| **计费透明** | 用量统计准确性、账单匹配 | #43409, #43416 |
| **多平台兼容** | Wayland 支持、Bun 安装兼容 | #42681, #27906 |
| **Skills 体验** | 斜杠补全、来源分组、UX 优化 | #43537, #43523 |

---

## 6. 开发者关注点

**高频痛点：**

1. **会话完整性与中断恢复**：多个 Issue 反映 provider 中断、消息丢弃、队列丢失等问题，用户期望更健壮的错误处理和消息保留机制。

2. **计费与用量透明度**：Go 订阅用户的异常扣费和账单不匹配问题引发信任危机，需官方及时修复和沟通。

3. **安装兼容性**：Bun 等现代包管理器对 postinstall 脚本的限制导致安装失败，需在文档或安装流程中明确支持范围。

4. **资源管理**：macOS TUI 的临时文件堆积问题（207GiB）影响生产环境稳定性，需优化清理策略。

5. **MCP 连接管理**：空闲后 MCP 连接触发速率限制，提示需要更智能的连接保活和重试机制。

6. **开发者体验**：热重载、Skills 自动补全、配置文件优化等功能表明社区对"开箱即用"和快速迭代体验的高度需求。

---

*数据来源：github.com/anomalyco/opencode | 统计时段：2026-08-19 ~ 2026-08-20*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 | 2026-08-20

## 1. 今日速览

过去24小时 Pi 无新版本发布，但 Issues 和 PRs 活跃度极高：社区聚焦 **Windows 端体验优化**（终端键位冲突、settings.json 解析、中文渲染）、**模型缓存与压缩机制改进**（跨会话缓存、阈值压缩修复）、以及 **AI 提供商兼容性增强**（Bedrock Mantle、reasoning_details 支持）。

## 2. 版本发布

过去24小时无新 Releases。

## 3. 社区热点 Issues

| # | 标题 | 状态 | 评论 | 重要性 |
|---|------|------|------|--------|
| [#7547](https://github.com/earendil-works/pi/issues/7547) | [Windows] [sink-thread] How do you use Pi on Windows? | OPEN | 31 | Windows 用户基数大但文档/体验分散，该 Issue 旨在收集痛点、明确优先修复方向 |
| [#5263](https://github.com/earendil-works/pi/issues/5263) | Make in-session model and thinking-level changes ephemeral by default | CLOSED | 11 | **👍 13** 用户希望会话内模型切换不污染全局默认，已关闭 |
| [#7829](https://github.com/earendil-works/pi/issues/7829) | Invalid settings.json silently ignored; misleading 'bash not found' error | CLOSED | 6 | Windows 路径转义问题导致静默失败，诊断体验差 |
| [#8183](https://github.com/earendil-works/pi/issues/8183) | Document Windows Terminal's Ctrl+Shift+F conflict with fullscreen search | OPEN | 4 | 全屏转录搜索与 Windows Terminal 默认快捷键冲突，需文档补充 |
| [#8206](https://github.com/earendil-works/pi/issues/8206) | opencode-go: qwen3.6-plus 和 minimax-m2.7 路由不匹配 | OPEN | 4 | 模型目录与 API 端点不对应，影响 OpenCode Go 用户 |
| [#8323](https://github.com/earendil-works/pi/issues/8323) | OpenAI client created with no timeout | CLOSED | 3 | 本地模型生成超10分钟被强制截断，需配置超时 |
| [#8322](https://github.com/earendil-works/pi/issues/8322) | isRecoverableLength misses exact-limit truncation | CLOSED | 3 | `<` 应为 `<=`，模型精确触达 max_output_tokens 时无法正确识别 |
| [#8328](https://github.com/earendil-works/pi/issues/8328) | Threshold compaction never fires for zero-usage providers | CLOSED | 3 | 缺失 usage block 的提供商导致自动压缩永远不触发 |
| [#8133](https://github.com/earendil-works/pi/issues/8133) | Per-model compaction settings | OPEN | 2 | 用户希望按模型配置压缩策略，而非全局统一 |
| [#8372](https://github.com/earendil-works/pi/issues/8372) | Windows terminal (WSL or native) key-bindings | OPEN | 2 | 平台键位冲突系统性问题，需更完善的 Windows 适配 |

## 4. 重要 PR 进展

| # | 标题 | 作者 | 状态 | 功能说明 |
|---|------|------|------|---------|
| [#8383](https://github.com/earendil-works/pi/pull/8383) | fix(ai): derive Gemini's disabled-thinking level from catalog | jingtao-wisdomgraph | OPEN | 修复 Gemini 模型 thinking 级别硬编码问题，改为从目录动态推导 |
| [#8377](https://github.com/earendil-works/pi/pull/8377) | fix(coding-agent): respect min-release-age when checking npm updates | zeke | CLOSED | 修复 npm 包更新检查忽略 `min-release-age`  cutoff 的 Bug |
| [#8374](https://github.com/earendil-works/pi/pull/8374) | fix(coding-agent): abort active run before forking | elithecho | CLOSED | 修复 fork 前未中止活跃运行的竞态问题 |
| [#8066](https://github.com/earendil-works/pi/pull/8066) | fix(tui): add visual lines caching | affanali2k3 | OPEN | 缓存视觉行结果，减少高频重计算，提升 TUI 性能 |
| [#6216](https://github.com/earendil-works/pi/pull/6216) | feat: Add Amazon Bedrock Mantle provider | unexge | CLOSED | 新增 Amazon Bedrock Mantle OpenAI Responses 支持 |
| [#8369](https://github.com/earendil-works/pi/pull/8369) | add fullscreen wheel scroll lines setting | ownlight6 | CLOSED | 全屏模式支持配置滚轮行数，改善触摸板滚动体验 |
| [#8365](https://github.com/earendil-works/pi/pull/8365) | feat: emit input event for built-in slash commands | kapkema | CLOSED | 内置斜杠命令（`/share`、`/export` 等）现在可触发 `input` 事件 |
| [#8356](https://github.com/earendil-works/pi/pull/8356) | fix(coding-agent): keep model and thinking level changes session scoped | cristinaponcela | CLOSED | 实现 #5263，会话内模型/thinking 变更不再污染全局默认 |
| [#8246](https://github.com/earendil-works/pi/pull/8246) | feat(ai): openai completions reasoning details | cristinaponcela | CLOSED | 修复 openai-completions 中 reasoning_details 无法 round-trip 的问题 |
| [#8346](https://github.com/earendil-works/pi/pull/8346) | fix(coding-agent): repair unterminated session tails | acmerfight | CLOSED | 自动修复未终止的 JSONL 会话尾文件 |

## 5. 功能需求趋势

从 Issues 和 PRs 中提炼出以下社区关注方向：

- **跨会话状态隔离**：`/model` 和 thinking-level 变更默认会话作用域（#5263、#8356），减少配置污染
- **模型目录与 API 兼容性**：新增 Bedrock Mantle（#6216、#8302）、修复 reasoning_details round-trip（#8246、#7994）
- **性能优化**：TUI 视觉行缓存（#8066）、阈值压缩修复（#8328、#8322）
- **Windows 适配**：键位冲突文档（#8183）、settings.json 解析容错（#7829）、中文渲染（#8382）
- **可观测性与扩展性**：内置斜杠命令事件暴露（#8365、#8364）、工具元数据 stream 事件（#7953）

## 6. 开发者关注点

**高频痛点：**

1. **Windows 用户体验**：多个 Issue 集中在键位冲突、路径转义、文档缺失，反映 Windows 端适配仍需加强
2. **缓存机制**：跨会话缓存失效（#8348）、模型目录过时（#8358）、阈值压缩失败（#8328）导致重复计算和浪费
3. **推理模型支持**：reasoning_details 无法 round-trip（#7994）、特定模型 reasoningEffort 参数错误（#8381）
4. **本地模型超时**：OpenAI SDK 默认 600s 超时对长推理场景不够（#8323、#8321）
5. **扩展开发限制**：ExtensionContext 无法检测队列中的自定义续接（#8349）、扩展无法注册但不激活工具（#8379）

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报 — 2026-08-20

---

## 1. 今日速览

Qwen Code 发布 **v0.21.14**，核心亮点是新增 `qwen sessions ps` 命令与实时会话注册表，支持以 JSON 格式列出和管理交互式会话。同时，SWE-bench Verified 500 题全量端到端验证**通过**，持续集成安全加固（PAT 隔离沙箱、CI 工作区软链接修复）取得关键进展。社区对 Agent 协作平台、多模型兼容性及上下文压缩等方向讨论活跃。

---

## 2. 版本发布

### v0.21.14（2026-08-20）
主要变更：
- **新增 `qwen sessions ps` 命令**：列出并管理当前运行的交互式会话，输出支持 JSON 格式，便于脚本集成（[PR #8969](https://github.com/QwenLM/qwen-code/pull/8969)、[#9261](https://github.com/QwenLM/qwen-code/pull/9261)、[#9366](https://github.com/QwenLM/qwen-code/pull/9366)）
- **Live-session 注册表**：daemon 新增会话状态追踪能力

相关链接：
- [Release v0.21.14](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.14)
- [v0.21.11-nightly.20260819](https://github.com/QwenLM/qwen-code/releases/tag/v0.21.11-nightly.20260819.d87b272aec)

---

## 3. 社区热点 Issues

| # | 标题 | 评论数 | 优先级 | 关注原因 |
|---|------|--------|--------|----------|
| [#5267](https://github.com/QwenLM/qwen-code/issues/5267) | `context.fileName` 在设置文件中不生效 | 12 | P2 | 配置项 bug，影响多文件上下文注入，长期存在但未修复 |
| [#9194](https://github.com/QwenLM/qwen-code/issues/9194) | mutation-verified 测试覆盖差距 | 11 | P3 | 测试健壮性问题，影响代码变更可靠性保证 |
| [#9089](https://github.com/QwenLM/qwen-code/issues/9089) | PAT-bearing 工作流缺少 runner 级隔离 | 6 | P1 | 安全隐患，CI/CD 流水线中 token 泄露风险 |
| [#8012](https://github.com/QwenLM/qwen-code/issues/8012) | GitHub channel 投递/批处理/PR 审查剩余缺口 | 5 | P2 | 集成完善性，影响自动化工作流体验 |
| [#9309](https://github.com/QwenLM/qwen-code/issues/9309) | 上下文压缩行为异常 | 5 | P3 | 用户体验问题，压缩后 token 计数与实际不符 |
| [#8596](https://github.com/QwenLM/qwen-code/issues/8596) | 弃用 Electron 桌面应用，迁移至 Tauri | 4 | P2 | 架构决策，影响桌面端用户群体 |
| [#9459](https://github.com/QwenLM/qwen-code/issues/9459) | `/effort max` 与 OpenAI 兼容提供商不兼容 | 4 | P1 | **高频痛点**，设 max 后整个会话所有请求返回 400 |
| [#9450](https://github.com/QwenLM/qwen-code/issues/9450) | task_list 误触发重复工具调用检测 | 4 | P2 | Agent Team 协作场景下的逻辑 bug |
| [#9219](https://github.com/QwenLM/qwen-code/issues/9219) | `/review` presubmit 行匹配过于严格 | 4 | P2 | review 工具准确性问题，影响多行注释检测 |
| [#9415](https://github.com/QwenLM/qwen-code/issues/9415) | 调度任务会话清理竞态条件 | 4 | P3 | 会话管理稳定性，delete 与 reuse 可能冲突 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 核心内容 |
|---|------|------|----------|
| [#9520](https://github.com/QwenLM/qwen-code/pull/9520) | Agent 编排契约文档 | OPEN | 梳理 6 种 Agent 启动路径（in-process、fork、named teammate、workflow、Cursor SDK/CLI）的契约关系 |
| [#9402](https://github.com/QwenLM/qwen-code/pull/9402) | Agent Board MVP | OPEN | 基于文件系统的跨 Agent 共享工作台，支持独立启动的 Agent 间协调工作 |
| [#9441](https://github.com/QwenLM/qwen-code/pull/9441) | PreToolUse hook 展示 edit/exec diff | OPEN | 当 hook 返回 `ask` 时，展示完整编辑/执行 diff 而非仅纯文本提示，提升用户确认体验 |
| [#9527](https://github.com/QwenLM/qwen-code/pull/9527) | autofix 沙箱镜像绑定 digest | OPEN | 修复 PR #9214 遗留问题，将导出镜像与拉取 digest 绑定，增强安全性 |
| [#9297](https://github.com/QwenLM/qwen-code/pull/9297) | autofix BLOCKED handoff 正式化 | OPEN | 将 "BLOCKED" 状态作为一等 round 结果处理，修复 round 输出契约 |
| [#9526](https://github.com/QwenLM/qwen-code/pull/9526) | review 收敛停滞预警 | OPEN | 当 review 循环卡在 Critical 问题时，自动向作者说明原因，减少无效迭代 |
| [#9221](https://github.com/QwenLM/qwen-code/pull/9221) | review verifier 私有 scratch 工作树 | OPEN | 验证探针在独立 worktree 中运行，避免污染共享 review 目录 |
| [#9214](https://github.com/QwenLM/qwen-code/pull/9214) | autofix 验证门控移入临时容器 | OPEN | 将验证步骤在 ephemeral container 中执行，解决 PAT 隔离安全需求（#9089） |
| [#9461](https://github.com/QwenLM/qwen-code/pull/9461) | review 循环不收敛提示 | OPEN | 当 review 陷入停滞时，自动生成一段说明给作者，指出比较信号 |
| [#9350](https://github.com/QwenLM/qwen-code/pull/9350) | 钉钉出站文件投递 | OPEN | 新增钉钉原生文件发送能力，Agent 响应中可携带本地文件并通过媒体 API 上传 |

---

## 5. 功能需求趋势

从 Issue 和 PR 分布来看，社区关注方向集中在：

| 方向 | 热度 | 代表性 Issue/PR |
|------|------|----------------|
| **Agent 协作与编排** | ⭐⭐⭐⭐⭐ | #9402（Agent Board）、#9520（编排契约）、#9450（task_list 误报） |
| **多模型/提供商兼容** | ⭐⭐⭐⭐☆ | #9459（/effort max OpenAI 兼容问题）、#889（OpenAI Response API 支持）、#9454（模型切换 token 计数复用 bug） |
| **安全与隔离** | ⭐⭐⭐⭐☆ | #9089（PAT 隔离）、#9214/#9527（沙箱容器）、#9480（CI 工作区加固） |
| **上下文管理** | ⭐⭐⭐⭐☆ | #5267（fileName 配置）、#9309（压缩异常）、#4141（俄语：压缩不工作） |
| **桌面端迁移** | ⭐⭐⭐☆☆ | #8596（弃用 Electron，迁移 Tauri） |
| **Review/Audit 工具链** | ⭐⭐⭐☆☆ | #9194、#9219、#9461、#8403（遗留代码审计） |
| **新渠道集成** | ⭐⭐⭐☆☆ | #8012（GitHub channel）、#9350（钉钉文件）、#9491（Aone Code 评论） |
| **Advisor 功能** | ⭐⭐☆☆☆ | #6542、#9036（对标 Claude Code Advisor） |

---

## 6. 开发者关注点

**高频痛点：**

1. **多模型兼容性**：`/effort max` 在 OpenAI 兼容提供商下会导致整个会话 400 错误（#9459），用户希望 Qwen Code 更好地适配 gpt-5-codex 等仅支持 Response API 的模型（#889）。

2. **上下文配置与压缩**：`context.fileName` 配置长期不生效（#5267），压缩后 token 计数与实际不符（#9309），是日常使用中的高频障碍。

3. **Agent 协作体验**：`task_list` 误触发重复检测（#9450）、跨 Agent 工作共享（#9402）、Agent 启动失败被标记为成功（#9509）等，反映多 Agent 场景下工具行为和状态管理仍需完善。

4. **桌面端迁移阵痛**：Electron 弃用、Tauri 迁移（#8596）影响桌面用户，需关注兼容性过渡。

5. **CI/CD 安全加固**：PAT 泄露、工作区软链接劫持等安全问题受到持续重视，#9089 及其衍生 PR（#9214、#9527、#9498）构成近期核心安全防线建设。

---

*报告生成时间：2026-08-20 | 数据来源：[github.com/QwenLM/qwen-code](https://github.com/QwenLM/qwen-code)*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI 社区动态日报 | 2026-08-20

## 1. 今日速览
今日社区围绕 **v0.9.10 发布后的稳定性治理** 展开，重点修复了内存滞留、审批状态持久化与流处理架构问题。中文本地化工程与 i18n 分支治理取得实质进展，同时用户反馈了升级后的默认配置越界（`max_tokens`）、状态指示器丢失及长程会话卡死等兼容性与可靠性痛点。

---

## 2. 版本发布

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*