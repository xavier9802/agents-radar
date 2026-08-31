# AI CLI 工具社区动态日报 2026-08-31

> 生成时间: 2026-08-31 04:59 UTC | 覆盖工具: 10 个

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
**日期：2026-08-31**

---

## 1. 生态全景

当前 AI CLI 工具生态进入**稳定性攻坚与功能深化**并行的阶段。主流工具（Claude Code、Codex、Gemini CLI）正集中解决长会话可靠性、跨平台兼容性和多 agent 协作等生产级痛点；开源替代品（OpenCode、CodeWhale、Qwen Code）则通过高频迭代快速追赶，在社区驱动下形成差异化竞争力。工具间功能趋同明显，竞争焦点转向**用户体验细节、成本透明度和企业级特性**（如组织级 agent 管理、安全沙箱）。

---

## 2. 各工具活跃度对比

| 工具 | 新增/更新 Issues | 合并 PR 数 | Release 情况 | 社区活跃度 |
|------|-----------------|-----------|-------------|-----------|
| **OpenCode** | ~50 个更新 | 20 个 | 无 | ⭐⭐⭐⭐⭐ 极高 |
| **Qwen Code** | ~45 个更新 | 50 个 | 无 | ⭐⭐⭐⭐⭐ 极高 |
| **DeepSeek TUI** | ~10 个热点 | 20+ 个 | v0.9.12 准备中 | ⭐⭐⭐⭐ 高 |
| **Pi** | ~10 个热点 | 8 个 | 无 | ⭐⭐⭐⭐ 高 |
| **Gemini CLI** | ~10 个热点 | ~10 个 | v0.59.0-nightly | ⭐⭐⭐⭐ 高 |
| **OpenAI Codex** | ~10 个热点 | 10 个 | 3 个 Rust Alpha | ⭐⭐⭐⭐ 高 |
| **Claude Code** | ~10 个热点 | 1 个 | 无 | ⭐⭐⭐ 中 |
| **GitHub Copilot CLI** | 20 个新增 | 0 个 | 无 | ⭐⭐⭐ 中 |
| **Kimi Code CLI** | 2 个新增 | 0 个 | 无 | ⭐⭐ 低 |
| **Grok Build** | 无活动 | 无 | 无 | ⭐ 无 |

---

## 3. 共同关注的功能方向

| 方向 | 涉及工具 | 具体诉求 |
|------|---------|---------|
| **长会话稳定性** | Claude Code、Copilot CLI、OpenCode、Pi、Codex | 压缩后状态丢失、OOM、会话恢复失败、死循环压缩 |
| **跨平台兼容性** | Claude Code、Codex、Gemini CLI、OpenCode | Windows 桌面端缺陷集中、Wayland 支持、ARM64 适配 |
| **多 Agent 协作** | Claude Code、OpenCode、Qwen Code、Gemini CLI | 子 agent 挂起/恢复、跨会话通信、嵌套通知传递 |
| **MCP 生态完善** | Codex、Gemini CLI、OpenCode、CodeWhale | Schema 标准化、工具名冲突、认证统一化 |
| **成本/配额透明** | Claude Code、Codex、Gemini CLI、Pi | 计量异常、缓存未生效、自动降级策略 |
| **安全与沙箱** | Qwen Code、Codex、CodeWhale | 工具调用权限、hook 触发、Sandbox 绕过需求 |

---

## 4. 差异化定位分析

| 工具 | 技术路线 | 目标用户 | 功能侧重 |
|------|---------|---------|---------|
| **Claude Code** | Anthropic 原生，Max Plan 订阅制 | 付费专业开发者 | 多 agent 编排、上下文压缩精细化 |
| **OpenAI Codex** | Rust SDK，OpenAI 模型 | 企业/Pro 用户 | 自动化工作流、TUI 体验、Rate Limit 横幅 |
| **Gemini CLI** | Google 原生，nightly 迭代快 | 全球开发者（含免费层） | 配额降级 fallback、ACP 成本透明、跨平台 |
| **GitHub Copilot CLI** | 微软生态集成，1.0.x 稳定版 | 企业开发者 | 组织级 agent、BYOK 多模型、VS Code 联动 |
| **OpenCode** | Rust 开源，插件生态活跃 | 极客/自定义需求用户 | Session Goals、压缩逻辑修复、多 Provider |
| **Qwen Code** | 阿里通义，安全优先 | 中国开发者/企业 | 安全审查、Web Shell、编码风格定制 |
| **DeepSeek TUI** | Rust 架构重构中 | DeepSeek 模型用户 | Tideline 交互、Provider wire 兼容、Unix Socket |
| **Pi** | Lua/LLua 生态 | 扩展爱好者 | 多 Provider 接入、扩展 API、JSONL 数据完整性 |
| **Kimi Code CLI** | Moonshot 原生 | 远程开发用户 | Remote Control 移动端、工具调用准确性 |

---

## 5. 社区热度与成熟度

**🔥 高热度 + 快速迭代（成熟度：发展中）**
- **OpenCode**：50 个 issue + 20 个 PR，插件生态活跃，但长会话稳定性问题突出
- **Qwen Code**：50 个 PR 反映高强度开发，安全审查驱动功能演进

**🔥 高热度 + 稳定交付（成熟度：较高）**
- **Codex**：PR 合并效率高（10 个/天），Rust SDK 持续 alpha 发布
- **Gemini CLI**：nightly 迭代节奏稳定，fallback 机制体现产品化思维

**⚠️ 热度中等 + 痛点集中（成熟度：需加固）**
- **Claude Code**：issue 关注度高但 PR 极少（仅 1 个），#38335 额度问题长期未解决
- **Copilot CLI**：20 个新增 issue 暴露 1.0.81 回归，稳定性承压

**📉 低活跃度（成熟度：早期）**
- **Kimi Code CLI**：2 个 issue，功能聚焦但社区规模小

---

## 6. 值得关注的趋势信号

| 趋势 | 信号来源 | 开发者启示 |
|------|---------|-----------|
| **长会话可靠性成为分水岭** | OpenCode 数据库膨胀、Pi OOM、Claude 额度争议、Copilot 内存溢出 | 生产级部署需关注上下文压缩策略和内存管理，避免超过 30 轮后的稳定性骤降 |
| **Windows 端稳定性集体短板** | Claude Code、Codex、Gemini CLI、OpenCode 均集中爆发 Windows 问题 | Windows 用户需谨慎评估，或优先考虑 CLI-only 方案；企业部署建议 Linux 环境 |
| **成本透明化需求上升** | Gemini 自动降级、Pi 缓存未生效、Codex 计量争议、OpenCode 定价修正 | 工具链集成需考虑配额耗尽的优雅降级方案，关注 ACP/缓存 token 计费准确性 |
| **多 Agent 协作从概念走向实践** | Claude 嵌套 agent 通知失败、OpenCode Session Goals、Qwen 跨会话通信 | 复杂工作流编排需关注子 agent 恢复机制和上下文隔离，避免级联失败 |
| **MCP 生态标准化加速** | Codex 包风格名称、Gemini schema 标准化、CodeWhale 统一认证 | 自定义 MCP server 需遵循 `type:object` 等严格校验，避免命名冲突 |
| **开源工具快速追赶商业产品** | OpenCode/Qwen Code 高频 PR、CodeWhale TUI 重构 | 开源方案成熟度快速提升，可评估替代商业产品的可行性 |

---

**核心结论**：AI CLI 生态正从"功能竞赛"转向"稳定性竞赛"。商业工具（Claude Code、Codex）的优势在 agent 编排和模型质量，但 Windows 稳定性和成本透明是普遍短板；开源工具（OpenCode、Qwen Code、CodeWhale）通过高频迭代快速补齐体验，但在长会话可靠性上仍需验证。开发者选型建议：生产环境优先关注长会话稳定性记录和跨平台测试覆盖，个人开发可尝试开源方案以降低成本依赖。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告
**数据截止：2026-08-31**

---

## 1. 热门 Skills 排行

| 排名 | Skill | 功能简述 | 状态 | 链接 |
|------|-------|----------|------|------|
| 1 | **skill-quality-analyzer & skill-security-analyzer** | 元级 Skill，从结构/文档、覆盖率、安全性、可执行性、一致性五个维度评估其他 Skill 质量 | OPEN | [PR #83](https://github.com/anthropics/skills/pull/83) |
| 2 | **self-audit** | 交付前自检 Skill：机械文件验证 + 四维推理质量门禁（v1.3.0） | OPEN | [PR #1367](https://github.com/anthropics/skills/pull/1367) |
| 3 | **Hivemind** | 零成本多 Agent 编排：将机械工作委派给 opencode 无头 worker，Claude Code 保留规划/审查/合并角色 | OPEN | [PR #1628](https://github.com/anthropics/skills/pull/1628) |
| 4 | **frontend-design** | 前端设计 Skill 重构，提升指令清晰度与可执行性，确保单轮对话内可落地 | OPEN | [PR #210](https://github.com/anthropics/skills/pull/210) |
| 5 | **testing-patterns** | 全栈测试 Skill：覆盖测试哲学（Testing Trophy）、单元测试 AAA 模式、React 组件测试等 | OPEN | [PR #723](https://github.com/anthropics/skills/pull/723) |
| 6 | **ServiceNow platform** | 企业级 ServiceNow 平台 Skill，覆盖 ITSM/ITOM/SecOps/FSM/IntegrationHub 等全模块 | OPEN | [PR #568](https://github.com/anthropics/skills/pull/568) |
| 7 | **ODT skill** | OpenDocument 格式（.odt/.ods）创建、填充、解析与转换，支持 LibreOffice 生态 | OPEN | [PR #486](https://github.com/anthropics/skills/pull/486) |
| 8 | **document-typography** | 文档排版质量管控：修复孤行、寡行、编号错位等 AI 生成文档常见排版问题 | OPEN | [PR #514](https://github.com/anthropics/skills/pull/514) |

---

## 2. 社区需求趋势

从 Issues 讨论热度提炼五大方向：

| 趋势方向 | 代表 Issue | 核心诉求 |
|----------|-----------|----------|
| **组织级 Skill 共享** | [#228](https://github.com/anthropics/skills/issues/228) | 企业内直接共享 Skill，无需手动下载-分发-导入 |
| **安全与信任边界** | [#492](https://github.com/anthropics/skills/issues/492) | 社区 Skill 冒充官方 `anthropic/` 命名空间，存在权限滥用风险 |
| **上下文窗口优化** | [#1487](https://github.com/anthropics/skills/issues/1487) | `claude-api` Skill 一次性注入 ~156k tokens，急需惰性加载/按需分发机制 |
| **推理质量门禁** | [#1385](https://github.com/anthropics/skills/issues/1385) | 全流程质量管道：任务前校准 → 对抗性审查 → 交付验证 |
| **跨平台兼容性** | [#29](https://github.com/anthropics/skills/issues/29)、[Issue #12](https://github.com/anthropics/skills/issues/12) | Bedrock 支持、DOCX 空白格式化等底层兼容问题持续反馈 |

---

## 3. 高潜力待合并 Skills

以下 PR 评论活跃、争议明确，近期落地概率较高：

| PR | Skill | 阻塞原因 | 潜在时机 |
|----|-------|----------|----------|
| [PR #1628](https://github.com/anthropics/skills/pull/1628) | **Hivemind** | 多 Agent 架构新颖，需评估与官方能力的兼容性 | 2026 Q3 |
| [PR #1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | 与 Issue #1385 质量门禁提案高度重合，可能合并入同一框架 | 2026 Q3 |
| [PR #1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator 修复** | 对应 Issue #556（10+ 独立复现），修复 eval 召回率恒为 0 的阻塞性 Bug | 2026 Q3 |
| [PR #723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | 覆盖测试全链路，社区需求明确，无已知阻塞 | 2026 Q3-Q4 |
| [PR #1602](https://github.com/anthropics/skills/pull/1602) | **mcp-builder 稳定性修复** | 修复序列化/编码/脚本稳定性等可靠性问题，技术价值高 | 2026 Q3 |
| [PR #568](https://github.com/anthropics/skills/pull/568) | **ServiceNow platform** | 企业场景刚需，作者持续更新（最后更新 2026-08-12） | 2026 Q4 |

---

## 4. Skills 生态洞察

> **当前社区最集中的诉求是：从"单个 Skill 的功能扩展"转向"Skill 质量治理与规模化协作"——包括 Skill 安全审核、质量门禁、组织共享机制，以及解决上下文窗口效率等基础设施问题。**

反映在三个信号：① `skill-quality-analyzer` 等元 Skill 引发讨论；② `self-audit` + `Reasoning Quality Gate` 提案指向交付前验证需求；③ Issue #492 安全信任边界问题与 Issue #1487 上下文消耗问题并列高关注。社区正从"怎么用 Skill"进化到"如何可信地规模化使用 Skill"。

---



# Claude Code 社区动态日报
**日期：2026-08-31**

---

## 1. 今日速览

过去24小时内 Claude Code 仓库无新版本发布，但社区活跃度持续高涨。最受关注的长期 issue #38335（Max plan session 额度异常耗尽）已积累 **839条评论、476个点赞**，成为社区最关注的稳定性问题。今日新增多个 Windows 桌面端关键缺陷（静默重启破坏会话、服务恢复失败、进程泄漏），同时后台 agent 管理和上下文压缩策略成为功能需求热点。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 社区热点 Issues（Top 10）

| # | 标题 | 评论/点赞 | 重要性说明 |
|---|------|-----------|-----------|
| **#38335** | Max plan session 额度自 2026-03-23 起异常快速耗尽 | 839 / 476👍 | **社区最痛点**：大量付费用户反馈 CLI 使用下额度消耗远超预期，长期未解决，影响最广 |
| **#10238** | Skills 支持子目录结构 | 53 / 168👍 | 高频功能请求，用户希望按模块组织 skill 文件，提升可维护性 |
| **#85891** | Windows 11 窗口始终置顶，无关闭选项 | 45 / 101👍 | Windows 用户体验痛点，与 macOS #66516 为同类问题，缺乏平台一致性 |
| **#90172** | 静默重启破坏运行中会话（八大缺陷伞形 issue） | 5 / 2👍 | 新发布的汇总 issue，涵盖更新静默重启导致会话中断的多个子缺陷 |
| **#85840** | Windows CoworkVMService 无法启用恢复动作（"Access is denied"） | 8 / 0👍 | **根本原因**：#59794 和 #66849 的真正根因，服务崩溃后导致 claude.exe 静默挂起 |
| **#75043** | 嵌套子 agent 子任务永远异步，完成通知无法返回父 agent | 20 / 5👍 | 多 agent 协作场景下的关键 bug，影响 orchestrator 模式可用性 |
| **#78224** | 后台子 agent 在可恢复失败时暂停而非终止 | 4 / 2👍 | 功能请求：当前背景 agent 遇限额/瞬态错误直接终止，用户希望保留进度并支持恢复 |
| **#78674** | Linux 低 MemFree 但高 MemAvailable 时后台任务被内存收割器误杀 | 3 / 0👍 | Linux 生产环境稳定性问题，PSI ≈ 0 但工具仍误判内存压力，批量杀死 run_in_background 任务 |
| **#89639** | macOS 定时任务会话在执行工具调用时卡住并占用并发槽 | 3 / 0👍 | 调度任务（scheduled-task）场景下的资源泄漏，卡住后占用全局并发直至整个调度饿死 |
| **#90347** | 按 agent 维度配置独立的上下文压缩窗口 | 3 / 3👍 | 多 agent 场景下的精细化控制需求，协调器与子 agent 需要不同的压缩阈值 |

**热点链接：**
- https://github.com/anthropics/claude-code/issues/38335
- https://github.com/anthropics/claude-code/issues/10238
- https://github.com/anthropics/claude-code/issues/85891
- https://github.com/anthropics/claude-code/issues/90172
- https://github.com/anthropics/claude-code/issues/85840
- https://github.com/anthropics/claude-code/issues/75043
- https://github.com/anthropics/claude-code/issues/78224
- https://github.com/anthropics/claude-code/issues/78674
- https://github.com/anthropics/claude-code/issues/89639
- https://github.com/anthropics/claude-code/issues/90347

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| **#35350** | fix(plugins): 使用可移植 shebang | ✅ 已合并 | 修复 NixOS 等系统中 bash 路径非 `/bin/bash` 导致的插件 hook 失败，将所有 11 个脚本统一为 `#!/usr/bin/env bash` |

**链接：** https://github.com/anthropics/claude-code/pull/35350

> 注：过去 24 小时内仅 1 条 PR 更新，其他开发活动以 issue 讨论为主。

---

## 5. 功能需求趋势

| 趋势方向 | 相关 Issues | 社区诉求 |
|----------|------------|---------|
| **Agent 协作精细化控制** | #78224, #90347, #75043 | 支持后台 agent 暂停/恢复、按 agent 维度配置压缩阈值、修复嵌套子 agent 通知传递 |
| **Windows 桌面端稳定性** | #85840, #90172, #89859, #85891 | 静默更新机制缺陷、服务恢复权限问题、进程泄漏、窗口行为异常 |
| **长会话与调度任务可靠性** | #89639, #78674, #80372 | 定时任务卡住导致并发槽耗尽、内存压力误判杀进程、30分钟后台任务超时 |
| **多平台一致性** | #10238 (skills), #85891 | macOS/Windows 行为对齐、skills 目录结构支持 |
| **权限与边界控制** | #90658 | 防止 Claude 在 auto 模式下访问项目范围外的敏感文件（如登录凭证） |

---

## 6. 开发者关注点

**🔴 高优先级痛点：**

1. **额度消耗异常**（#38335）：Max plan 用户反映 CLI 使用下 session 额度消耗速度异常，自 2026-03 起持续发酵，是当前社区情绪最激烈的 issue。

2. **Windows 桌面端可靠性**（#85840, #90172, #89859）：多个关联 issue 指向 Windows 桌面应用在更新重启、服务恢复、进程生命周期管理方面的系统性缺陷，直接影响生产环境使用。

3. **多 agent 架构稳定性**（#75043, #78224）：使用 Agent 工具编排多子 agent 时，通知传递失败、后台任务被误杀、缺乏恢复机制等问题阻碍了复杂工作流的落地。

4. **长运行会话资源泄漏**（#89639, #80372, #90889）：macOS/Linux 环境下定时任务和后台 bash 任务存在卡死、进程不退出、内存泄漏等问题，长时间运行后导致系统资源耗尽。

**🟡 持续关注方向：**
- Linux 生产环境的内存压力检测准确性（#78674）
- MCP 工具参数序列化问题（#88882, #87361）
- 模型端的新问题：Fable 5 误分类（#90896）、API 政策误报（#90897）、角色标记泄漏（#90893, #90894）

---

*报告生成时间：2026-08-31 | 数据来源：github.com/anthropics/claude-code*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-08-31**

---

## 1. 今日速览

今日 Codex 社区活跃度高，**Windows 桌面端问题集中爆发**，涉及握手失败、UI 渲染异常、权限认证等多类故障；CLI 端则围绕**定时任务异常暂停**和**使用量统计异常**引发热议。同时，`update_plan` 工具改为默认关闭、MCP 服务器名称支持 package 风格等核心功能 PR 已合并。

---

## 2. 版本发布

过去24小时发布 **3 个 Rust SDK Alpha 版本**：

| 版本 | 说明 |
|------|------|
| `rust-v0.152.0-alpha.6` | 最新 alpha 构建 |
| `rust-v0.152.0-alpha.5` | 中间构建 |
| `rust-v0.152.0-alpha.4` | 早期构建 |

> 链接：[GitHub Releases](https://github.com/openai/codex/releases)

---

## 3. 社区热点 Issues

### 🔥 #38350 — 定时任务执行后自动暂停（57 评论）
**重要性**：影响 ChatGPT Web 端自动化工作流，用户未授权却连续4个任务被禁用，可靠性问题严重。  
**社区反应**：高关注，开发者反馈反复出现。  
🔗 [Issue #38350](https://github.com/openai/codex/issues/38350)

### 🔥 #39903 — 禁用"执行了 N 条命令"折叠功能（51 评论，70 👍）
**重要性**：CLI 用户体验优化需求，用户希望始终展开查看已执行命令列表。  
**社区反应**：获得大量认同，70个赞显示需求强烈。  
🔗 [Issue #39903](https://github.com/openai/codex/issues/39903)

### 🔥 #41049 — Windows 端 code-mode 握手失败（41 评论）
**重要性**：gpt-5.6-sol max 模型在 Windows 上无法正常工作，本地命令执行通道初始化异常。  
**社区反应**：Windows 用户普遍受影响。  
🔗 [Issue #41049](https://github.com/openai/codex/issues/41049)

### #33685 — 周限额消耗异常快速（31 评论，17 👍）
**重要性**：用户反馈在 GPT-5.5 High 模式下，周限额消耗速度等同于旧版5小时限额，疑似计量 Bug。  
**社区反应**：Pro 订阅用户高度关注计费公平性。  
🔗 [Issue #33685](https://github.com/openai/codex/issues/33685)

### #40968 — Windows 发送按钮无限旋转（17 评论）
**重要性**：Codex Desktop 核心交互功能失效，提示无法提交。  
**社区反应**：阻塞性 Bug，影响日常使用。  
🔗 [Issue #40968](https://github.com/openai/codex/issues/40968)

### #41290 — Windows + WSL 项目创建/删除失败（17 评论，7 👍）
**重要性**：切换 Agent Environment 到 WSL 后项目操作完全不可用。  
**社区反应**：WSL 用户群体反馈强烈。  
🔗 [Issue #41290](https://github.com/openai/codex/issues/41290)

### #34652 — Remote SSH 文件编辑审批按钮无响应（13 评论）
**重要性**：CLI 审批正常但桌面端 Remote SSH 场景审批失效，影响远程开发工作流。  
**社区反应**：远程开发用户痛点。  
🔗 [Issue #34652](https://github.com/openai/codex/issues/34652)

### #39823 — Session 恢复失败报"active writer"错误（11 评论）
**重要性**：`--not-so-yolo` 或切换环境后 session 恢复机制存在竞争条件。  
**社区反应**：高级用户频繁遇到。  
🔗 [Issue #39823](https://github.com/openai/codex/issues/39823)

### #24453 — Windows 未触发 PreToolUse hooks（9 评论）
**重要性**：hooks 机制在 Windows 命令执行中失效，影响安全审计和自定义拦截需求。  
**社区反应**：安全敏感用户关注。  
🔗 [Issue #24453](https://github.com/openai/codex/issues/24453)

### #41327 — Computer Use 每次点击后 SIGTRAP 崩溃（5 评论）
**重要性**：Computer Use 功能在完成 `get_app_state` 后首次点击即崩溃，功能不可用。  
**社区反应**：新特性稳定性受质疑。  
🔗 [Issue #41327](https://github.com/openai/codex/issues/41327)

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 说明 |
|----|------|------|------|
| [#41744](https://github.com/openai/codex/pull/41744) | Make update_plan tool opt-in | ✅ CLOSED | 默认关闭 `update_plan` 工具，用户需显式启用；移除相关 prompt 内置指导 |
| [#41743](https://github.com/openai/codex/pull/41743) | Mark history ingestion in turn metadata | ✅ CLOSED | 在 Responses turn metadata 中标记 `history_ingest_requested=true`，保护核心字段不被覆盖 |
| [#41742](https://github.com/openai/codex/pull/41742) | Show actionable rate-limit banners in TUI | ✅ CLOSED | TUI 中显示可操作的速率限制横幅，过滤不匹配的账户通知 |
| [#41700](https://github.com/openai/codex/pull/41700) | Support package-style MCP server names | ✅ CLOSED | MCP 服务器名称支持 `:`、`@`、`/`、`.`，可注册 `npm:@modelcontextprotocol/server-xxx` 格式 |
| [#41683](https://github.com/openai/codex/pull/41683) | Set working dirs for env MCP tests | ✅ CLOSED | 为环境型 stdio MCP 服务器测试 fixture 显式设置 `cwd` |
| [#41673](https://github.com/openai/codex/pull/41673) | Repair cursor-style on older JediTerm | ✅ CLOSED | 修复旧版 JediTerm 终端中光标样式渲染异常问题 |
| [#41666](https://github.com/openai/codex/pull/41666) | Approve first Node REPL without Guardian wait | ✅ CLOSED | 首次 Node REPL 执行直接批准，无需等待 Guardian 异步分类 |
| [#41660](https://github.com/openai/codex/pull/41660) | Preserve Guardian auth across history compaction | ✅ CLOSED | 历史压缩时保留 Guardian 授权状态，防止误触发重新审批 |
| [#41630](https://github.com/openai/codex/pull/41630) | Update tests for default-enabled update_plan | ✅ CLOSED | 补充 `update_plan` 默认启用、显式启用、显式禁用三种状态的测试覆盖 |
| [#41613](https://github.com/openai/codex/pull/41613) | Move Vim history tests into history search module | ✅ CLOSED | 重构测试结构，将 Vim 历史导航测试移至历史搜索模块 |

---

## 5. 功能需求趋势

从 Issue 和 PR 中提炼出以下社区关注方向：

| 方向 | 关注点 | 体现 |
|------|--------|------|
| **Windows 稳定性** | 桌面端握手失败、UI 渲染异常、权限认证、WSL 兼容 | 大量 Issue 集中反馈 Windows 平台问题 |
| **CLI/TUI 体验** | 命令折叠展开、速率限制提示、Session 恢复、光标渲染 | #39903、#41742、#39823、#41673 |
| **自动化可靠性** | 定时任务状态保持、hooks 触发、Guardian 授权持久化 | #38350、#24453、#41660 |
| **MCP 生态** | 包风格服务器名称、环境测试工作目录 | #41700、#41683 |
| **计量透明度** | 使用限额消耗合理性、速率限制横幅展示 | #33685、#41742 |
| **Computer Use** | 新特性稳定性、崩溃修复 | #41327 |

---

## 6. 开发者关注点

**高频痛点汇总：**

1. **Windows 平台问题最为突出**：握手失败（#41049、#40913）、按钮无响应（#40968）、项目操作失败（#41290）、认证重定向异常（#39467）、UI 渲染缺陷（#41513、#41472）等多类故障集中爆发，表明 Windows 客户端稳定性是当前最大短板。

2. **自动化任务可靠性不足**：定时任务无故暂停（#38350）直接影响工作流连续性，用户信任度受损。

3. **使用计量争议**：限额消耗异常快速（#33685、#19944）引发用户对计费公平性的担忧，需官方澄清或修复。

4. **安全钩子机制不完善**：Windows 下 `PreToolUse` hooks 未触发（#24453）影响企业级安全审计需求。

5. **Session 管理缺陷**：恢复失败（#39823、#20165）和竞态条件（#41353）影响多任务并行工作流。

6. **新功能稳定性待提升**：Computer Use 崩溃（#41327）、Pets 交互失效（#41501、#41513）表明新特性需要更多测试覆盖。

---

*日报生成时间：2026-08-31 | 数据来源：github.com/openai/codex*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报 — 2026-08-31

---

## 1. 今日速览

今日 Gemini CLI 发布 nightly v0.59.0 迭代，社区持续聚焦 agent 稳定性问题，尤其是 subagent 卡死/挂起（#21409、#22323）和 browser subagent 在 Wayland 下的兼容性问题（#21983）。同时，多个 PR 集中修复了核心体验：Windows 多行粘贴（#26905）、配额耗尽后的模型自动降级（#26914）以及 MCP 工具命名冲突（#28971）。

---

## 2. 版本发布

| 版本 | 链接 |
|------|------|
| `v0.59.0-nightly.20260831.g0bd1d4397` | [Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260830.g0bd1d4397...v0.59.0-nightly.20260831.g0bd1d4397) |

> 本次为 nightly 构建，无公开详细更新说明。

---

## 3. 社区热点 Issues

| # | 标题 | 热度 | 说明 |
|---|------|------|------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS reported as GOAL success | 🔥 13 comments / 2 👍 | `codebase_investigator` 子 agent 达到最大轮次后错误地报告成功，导致中断被掩盖，影响调试和可用性 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent hangs | 🔥 8 comments / 8 👍 | 通用 agent 在简单任务（如创建文件夹）时永久挂起，社区高关注（8👍），禁用 subagent 可规避 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | Zero-Dependency OS Sandboxing via bash affinity | 🔥 8 comments / 1 👍 | 利用 Gemini 模型的 bash 原生能力，通过零依赖沙箱执行 POSIX 工具链，兼顾安全与 UX |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads, search, and codebase mapping | 🔥 7 comments / 1 👍 | 评估 AST 感知工具的价值：精准读取方法边界、减少 token 噪声、提升代码导航效率 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini does not use skills and sub-agents enough | 🔥 6 comments | 用户反馈自定义 skills 和 sub-agents 未被模型主动调用，仅显式指示时才触发 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | Add deterministic redaction and reduce Auto Memory logging | 🔥 5 comments | Auto Memory 在发送内容到模型前缺少确定性脱敏，存在隐私泄露风险 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell command stuck at "Waiting input" after completion | 🔥 4 comments / 3 👍 | 简单 shell 命令执行完毕后仍显示"等待用户输入"，属于高频痛点 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | Enhance browser_agent resilience: session takeover | 🔥 4 comments | 浏览器 agent 在 profile 被锁定时采取 fail-fast 策略，用户希望支持自动接管残存会话 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent fails in Wayland | 🔥 4 comments / 1 👍 | Linux Wayland 环境下 browser subagent 执行失败，终端用户兼容性问题 |
| [#20079](https://github.com/google-gemini/gemini-cli/issues/20079) | Symlinked agent .md files not recognized | 🔥 4 comments | `~/.gemini/agents/` 下的符号链接不被识别，影响模块化管理自定义 agent |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| [#26848](https://github.com/google-gemini/gemini-cli/pull/26848) | Allow IPv6 loopback in Host header validation | ✅ Closed | 修复 IDE companion 拒绝 `Host: [::1]:PORT` 的安全验证问题 |
| [#26905](https://github.com/google-gemini/gemini-cli/pull/26905) | Synthesize bracketed-paste markers for Windows | ✅ Closed | 修复 Windows Terminal / WSL2 下多行粘贴提前提交的问题，通过合成 `\x1b[200~` 序列解决 |
| [#26914](https://github.com/google-gemini/gemini-cli/pull/26914) | Include gemini-2.5-flash-lite in default fallback chain | ✅ Closed | **重要**：Pro/Flash 配额耗尽时自动降级至 `gemini-2.5-flash-lite`（免费版 1000 RPD），改善免费用户可用体验 |
| [#26930](https://github.com/google-gemini/gemini-cli/pull/26930) | Restore previous extension on failed update | ✅ Closed | 扩展更新失败时回滚到旧版本，避免用户失去工作扩展 |
| [#26932](https://github.com/google-gemini/gemini-cli/pull/26932) | Handle refreshAuth rejection in non-interactive path | ✅ Closed | 修复非交互模式下 OAuth token 刷新失败导致的未捕获 Promise 崩溃 |
| [#28834](https://github.com/google-gemini/gemini-cli/pull/28834) | Suppress spurious ENOENT warning in workspace scan | ✅ Closed | 消除 BFS 遍历中因瞬态目录消失导致的噪音警告 |
| [#28835](https://github.com/google-gemini/gemini-cli/pull/28835) | Skip user agents dir when workspace is home | ✅ Closed | 修复从 home 目录运行时出现重复 agent 名称警告的问题 |
| [#28839](https://github.com/google-gemini/gemini-cli/pull/28839) | Normalize MCP tool schemas to ensure type:object | ✅ Closed | 修复 MCP server 工具 schema 缺失 `type` 字段导致严格校验失败的兼容性问题 |
| [#28840](https://github.com/google-gemini/gemini-cli/pull/28840) | Populate cached/thought tokens in ACP usage | ✅ Closed | **重要**：修复 ACP 客户端因缺失缓存/思考 token 导致成本估算偏高约 3 倍的问题 |
| [#28971](https://github.com/google-gemini/gemini-cli/pull/28971) | Keep truncated MCP tool names unique | 🔄 Open | 修复 MCP 工具名截断后发生命名碰撞导致注册失败的问题 |

---

## 5. 功能需求趋势

基于 Issues 和 PRs 的集中方向，社区关注点呈现以下趋势：

| 趋势 | 体现 |
|------|------|
| **Agent 稳定性与可观测性** | Subagent 挂起、超时恢复、轨迹可见性（#22323、#21409、#22598）、bug report 缺少子 agent 上下文（#21763） |
| **MCP / 扩展生态完善** | Schema 标准化（#28839）、工具名截断去重（#28971）、A2A 设置 deep-merge（#26931） |
| **AST 感知代码理解** | 精准方法读取、减少 token 浪费（#22745、#19561） |
| **跨平台兼容性** | Wayland browser agent（#21983）、Windows 多行粘贴（#26905）、IPv6 回环（#26848） |
| **成本透明与配额管理** | 自动降级 fallback（#26914）、ACP token 计费准确（#28840） |
| **安全与隐私** | Auto Memory 确定性脱敏（#26525）、危险操作抑制（#22672） |
| **Shell / 终端体验** | 命令卡住（#25166）、换行符检测（#28983）、行尾归一化（#29132） |

---

## 6. 开发者关注点

从社区反馈中提炼出以下高频痛点和需求：

1. **Agent 行为不可预测**：skills/sub-agents 未被主动调用（#21968）、generalist agent 无故挂起（#21409），开发者希望更可靠的 agent 调度机制。
2. **错误恢复能力不足**：浏览器 agent 遇到锁定时直接 fail-fast（#22232）、扩展更新失败后无回滚（#26930），缺乏优雅降级策略。
3. **跨平台兼容碎片化**：Wayland（#21983）、Windows 粘贴（#26905）、符号链接（#20079）等问题反映多平台测试覆盖不足。
4. **成本估算偏差**：ACP 客户端因缺少缓存 token 信息导致计费严重偏高（#28840），影响商业场景使用。
5. **调试可观测性弱**：bug report 不包含 subagent 上下文（#21763）、subagent 轨迹难以通过 `/chat share` 查看（#22598）。
6. **MCP 生态兼容性**：工具 schema 缺失字段（#28839）、截断命名冲突（#28971），反映第三方 MCP server 质量参差不齐。
7. **终端交互体验**：shell 命令完成后仍等待输入（#25166）、CRLF 文件 diff 显示异常（#29132、#28983），影响日常命令行工作流。

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-08-31**

---

## 1. 今日速览

过去24小时内，Copilot CLI 共新增 **20 条 Issues**，无版本发布和 PR 合并。社区焦点集中在**长会话稳定性**（内存溢出、文件监控死循环）和 **1.0.81 版本回归**（OAuth 认证失败、工具绑定异常）两大主题，反映出用户对生产环境可靠性的强烈关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 👍 | 评论 | 重要性 |
|---|------|------|----|------|--------|
| #1285 | 组织级 Agent 未出现在 CLI/VS Code 中 | OPEN | 9 | 8 | 🔴 高 |
| #4612 | FileWatch 循环导致 TUI 冻结、debug 日志暴涨至 13GB | OPEN | 1 | 8 | 🔴 高 |
| #3978 | 切换 BYOK 后 CLI 错误回退到前一个模型 | OPEN | 4 | 1 | 🟡 中 |
| #4594 | 自定义 Agent 的 `web`/`search` 别名静默绑定 0 个工具 | OPEN | 1 | 1 | 🟡 中 |
| #2861 | 手动 `/compact` 在 Opus 4.6 上连续 3 次空响应失败 | OPEN | 3 | 2 | 🟡 中 |
| #4664 | 恢复长会话时触发 V8 堆内存溢出崩溃 | OPEN | 0 | 1 | 🔴 高 |
| #4671 | 1.0.81 在 TLS 检测代理后 OAuth 登录失败（回归） | OPEN | 0 | 0 | 🔴 高 |
| #4665 | `sessionStart` 的 `additionalContext` 每轮重复注入 | OPEN | 0 | 0 | 🟡 中 |
| #4668 | 中断的 `create_session` 在 1.6 小时后静默创建重复会话 | OPEN | 0 | 0 | 🟡 中 |
| #4669 | 遥测 `headers` 配置导致 OpenTelemetry 导出完全失败 | OPEN | 0 | 0 | 🟡 中 |

**热点说明：**

- **#1285**（组织级 Agent 不可见）— 获得 9 个 👍，是近期热度最高的 Issue，涉及企业用户核心工作流，作者确认模板和命名空间配置正确但 CLI/VS Code 均无法识别组织级 Agent。
- **#4612**（FileWatch 死循环）— 8 条评论显示该问题影响广泛，长时间运行的会话会触发无限循环，导致 TUI 无响应并产生 13GB 日志文件。
- **#4671**（1.0.81 代理认证回归）— 明确指出是 **1.0.81 回归**，1.0.80 正常，涉及企业内网常见部署场景，device-code 和 web flow 两种模式均失败。
- **#4664**（堆内存溢出）— 直接导致 CLI 崩溃，影响长会话恢复场景，属于严重稳定性问题。

---

## 4. 重要 PR 进展

今日无 PR 更新。

---

## 5. 功能需求趋势

从 Issues 中可识别以下社区关注方向：

1. **企业级 Agent 管理**：组织级 Agent 可见性、多环境隔离（#1285）
2. **长会话稳定性**：内存管理、会话恢复、上下文压缩可靠性（#4664、#2861、#4668）
3. **BYOK / 多模型支持**：模型切换后的状态保持、自定义模型压缩兼容性（#3978、#4646）
4. **自定义 Agent 工具系统**：工具别名绑定、静默失败的排查（#4594）
5. **遥测与可观测性**：OTEL 配置灵活性、企业代理环境下的遥测导出（#4669、#4169）
6. **身份认证与网络环境**：TLS 检测代理、OAuth 多模式兼容性（#4671、#4660）
7. **上下文管理**：`additionalContext` 重复注入问题（#4665）

---

## 6. 开发者关注点

**高频痛点汇总：**

| 痛点 | 涉及 Issue |
|------|-----------|
| 长会话恢复崩溃（OOM） | #4664 |
| 文件监控死循环（TUI 冻结 + 日志暴涨） | #4612 |
| 1.0.81 代理 OAuth 回归 | #4671 |
| 自定义 Agent 工具静默失效 | #4594 |
| 模型切换后状态回退 | #3978 |
| 上下文每轮重复注入 | #4665 |
| 中断会话后静默重复创建 | #4668 |
| 遥测头部配置导致导出失败 | #4669 |

**关键信号：** 社区对 **1.0.81 版本稳定性** 的担忧较为集中，多个 Issue 指向认证、工具绑定和遥测方面的回归。同时，长会话（>30 轮）的内存和上下文管理是持续性痛点，期待后续版本有所改善。

---

*数据来源：github.com/github/copilot-cli | 生成时间：2026-08-31*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-08-31**

---

## 1. 今日速览

过去24小时 Kimi Code CLI 仓库无新版本发布，亦无 PR 合并。社区活跃度集中在 Issues 区，共 2 条新增讨论，主要涉及模型工具调用异常和远程登录兼容性问题，暂无社区热点事件。

---

## 2. 版本发布

> 无新版本发布。当前稳定版本为 **0.39.1**。

---

## 3. 社区热点 Issues

### #2628 — Model emits Read tool calls instead of Write/Edit
**链接**: [MoonshotAI/kimi-cli Issue #2628](https://github.com/MoonshotAI/kimi-cli/issues/2628)

- **状态**: OPEN | **评论**: 0 | **👍**: 0
- **作者**: 776138506 | **创建/更新**: 2026-08-30
- **摘要**: 用户使用 Kimi Code CLI `0.39.1` + `kimi-code/k3-256k` 模型时，模型在文本输出中显示"calling Write"，但实际执行的工具调用却是 Read，疑似工具选择与描述不一致的 bug。
- **关注原因**: 直接影响代码编辑功能的正确性，若确认是模型层问题可能影响更多用户。

---

### #2627 — Remote Control login fails to start on iPadOS 16.6 (Safari/WeChat)
**链接**: [MoonshotAI/kimi-cli Issue #2627](https://github.com/MoonshotAI/kimi-cli/issues/2627)

- **状态**: OPEN | **评论**: 0 | **👍**: 0
- **作者**: VBS-you | **创建/更新**: 2026-08-30
- **摘要**: 在 iPadOS 16.6 Safari/微信浏览器中访问 `code-rc.kimi.com` 时，Remote Control 登录流程报错"无法开始登录"。服务端为 Debian 12 x86_64 + 阿里云 ECS。
- **关注原因**: 远程操控是 Kimi Code CLI 的核心功能之一，移动端兼容性问题是影响用户体验的关键痛点。

---

> 本期新增 Issues 仅 2 条，暂无更多可分析内容。

---

## 4. 重要 PR 进展

> 过去24小时内无 PR 更新，暂无相关进展。

---

## 5. 功能需求趋势

基于今日 Issues 分析，社区当前关注焦点如下：

| 方向 | 关注点 |
|------|--------|
| **模型工具调用准确性** | #2628 反映用户对模型工具选择可靠性的关注，Write/Edit vs Read 的误判直接影响代码编辑场景 |
| **跨平台/移动端兼容** | #2627 体现远程控制的移动端接入需求，尤其在 Safari/微信 WebView 环境下的稳定性 |
| **远程操控功能** | Remote Control 作为差异化功能，登录链路畅通是用户使用的前提 |

---

## 6. 开发者关注点

1. **工具调用可靠性**: 模型在输出描述与实际执行工具之间的不一致，是开发者反馈的核心痛点，关系到代码编辑类任务的可信度。
2. **远程登录体验**: 在常见移动端浏览器（Safari/微信）上的登录兼容性问题，反映出用户对随时随地接入远程开发环境的需求。
3. **低评论率**: 两个 Issue 均处于刚创建状态，暂无社区讨论或官方回应，建议关注后续进展。

---

*数据来源: github.com/MoonshotAI/kimi-cli · 统计周期: 2026-08-30 00:00 ~ 2026-08-31 00:00*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode 社区动态日报 — 2026-08-31

---

## 1. 今日速览

过去24小时内 OpenCode 社区保持高频活跃，无新 Release 发布，但共更新 **50 个 Issues** 与 **20 个 PRs**。核心焦点集中在 **长会话 session 稳定性**（自动压缩后状态丢失、无限压缩循环）与 **多 provider 兼容性**（Kimi K3、OpenRouter Gemini 鉴权问题）。社区贡献者积极提交修复，涉及 shell 管道排空、Bedrock 媒体校验、定价计算修正等底层问题。

---

## 2. 版本发布

> 过去24小时内无新版本发布。

---

## 3. 社区热点 Issues

### 🔥 高关注 Issues（按讨论热度排序）

| # | 状态 | 标题 | 作者 | 👍/💬 | 链接 |
|---|------|------|------|------|------|
| #27167 | OPEN | 原生 Session Goals（/goal 命令） | jorgitin02 | 139/76 | [Issue](https://github.com/anomalyco/opencode/issues/27167) |
| #33356 | OPEN | `event` 表无限增长，数据库膨胀至 13GB+ | rustyaos | 8/25 | [Issue](https://github.com/anomalyco/opencode/issues/33356) |
| #19130 | OPEN | Windows ARM64 TUI 初始化失败（bun:ffi dlopen TinyCC 错误） | Carliquiss | 13/20 | [Issue](https://github.com/anomalyco/opencode/issues/19130) |
| #41358 | OPEN | 自动压缩后 Agent 失去目标，继续无确认地运行 | liudongyan13701205717-source | 0/7 | [Issue](https://github.com/anomalyco/opencode/issues/41358) |
| #37354 | OPEN | OpenRouter 向 Gemini 模型发送未授权请求 | paul-phoenix | 1/8 | [Issue](https://github.com/anomalyco/opencode/issues/37354) |
| #31152 | CLOSED | 空会话下无限压缩循环 | GraveEaterMadison | 0/7 | [Issue](https://github.com/anomalyco/opencode/issues/31152) |
| #37946 | OPEN | 中止的 assistant turn 导致后续会话全部失败 | Oloompa | 1/5 | [Issue](https://github.com/anomalyco/opencode/issues/37946) |
| #32202 | OPEN | Skill 重复 roots 导致 restart 后可用技能不一致 | ualtinok | 1/6 | [Issue](https://github.com/anomalyco/opencode/issues/32202) |
| #39451 | OPEN | Kimi K3 切换模型时抛 400 "assistant message must not be empty" | zhujianjie-kevin | 0/3 | [Issue](https://github.com/anomalyco/opencode/issues/39451) |
| #46310 | OPEN | Agent Loop 随机静默卡死 | avikalpa | 0/2 | [Issue](https://github.com/anomalyco/opencode/issues/46310) |

**热点分析：**
- **#27167** 以 139 票成为社区最热功能请求，用户强烈渴望原生 session 目标管理，已有 PR #46328 提供插件方案。
- **#33356** 和 **#31152** 直击生产环境的致命稳定性问题，事件表无压缩/回收机制导致磁盘爆炸，已被多人验证复现。
- **#41358** 反映自动压缩后的状态管理缺陷，Agent 在压缩后"失忆"且不停止运行，严重影响长会话可靠性。

---

## 4. 重要 PR 进展

| # | 状态 | 类型 | 作者 | 内容摘要 | 链接 |
|---|------|------|------|---------|------|
| #45125 | OPEN | feat | ryangamerdev | 增强压缩逻辑：引入比例控制与上下文恢复，修复压缩后丢失任务目标的痛点 | [PR](https://github.com/anomalyco/opencode/pull/45125) |
| #33247 | OPEN | feat | mortenfc | 队列消息编辑、Wrap & Steer、Halt & Steer 功能 | [PR](https://github.com/anomalyco/opencode/pull/33247) |
| #46328 | OPEN | feat | charleneleong-ai | 示例插件：展示如何使用插件 SDK 实现 /goal 和 /loop | [PR](https://github.com/anomalyco/opencode/pull/46328) |
| #46085 | OPEN | fix | Hona | 修复 shell 命令退出后管道未排空导致卡死的问题（跨平台） | [PR](https://github.com/anomalyco/opencode/pull/46085) |
| #46334 | OPEN | fix | kvyb | 无 hook 时跳过无用的压缩历史克隆，优化性能 | [PR](https://github.com/anomalyco/opencode/pull/46334) |
| #46337 | OPEN | fix | rekram1-node | 修正 Anthropic 1小时缓存写入定价计算（按 1.6x 计费） | [PR](https://github.com/anomalyco/opencode/pull/46337) |
| #46332 | OPEN | docs | impptg | 新增 `opencode-fix-empty-assistant-messages` 插件至生态表格 | [PR](https://github.com/anomalyco/opencode/pull/46332) |
| #46329 | OPEN | fix | rekram1-node | 隔离共享事件消费者，防止暂停的权限消费者阻塞无关会话 | [PR](https://github.com/anomalyco/opencode/pull/46329) |
| #46333 | CLOSED | fix | rekram1-node | 校验 Bedrock 媒体数据，拒绝畸形请求避免 400 错误 | [PR](https://github.com/anomalyco/opencode/pull/46333) |
| #46335 | CLOSED | fix | rekram1-node | 过滤 Bedrock 空白文本块，避免 400 ValidationException | [PR](https://github.com/anomalyco/opencode/pull/46335) |

**PR 亮点：**
- **#45125** 是当日最核心的功能改进，尝试解决压缩后上下文丢失与状态断裂问题。
- **#46328** 作为 #27167 的替代方案，通过插件机制实现 session goals，不依赖核心改动。
- **#46085** 解决 Windows/Linux/macOS 上 shell 管道遗留导致的阻塞问题，实用性强。
- **#46337** 修正了 Anthropic 缓存写入的计费逻辑，对成本敏感用户很重要。

---

## 5. 功能需求趋势

从本期 Issues 与 PRs 中可提炼以下社区关注方向：

| 方向 | 关注度 | 代表 Issue/PR |
|------|--------|---------------|
| **长会话稳定性与压缩机制** | ⭐⭐⭐⭐⭐ | #33356、#31152、#41358、#45125、#46334 |
| **Provider 兼容性与鉴权** | ⭐⭐⭐⭐⭐ | #37354、#39451、#37887、#37946、#46333、#46335 |
| **Session 生命周期管理** | ⭐⭐⭐⭐ | #27167、#46328、#37946 |
| **桌面客户端体验** | ⭐⭐⭐⭐ | #19130、#19473、#46336、#46338、#46339 |
| **Shell/终端集成** | ⭐⭐⭐ | #46085、#34749、#32669 |
| **成本透明与定价** | ⭐⭐⭐ | #46337、#39864 |
| **Skill/插件系统** | ⭐⭐⭐ | #32202、#24164、#46332 |

---

## 6. 开发者关注点

**高频痛点汇总：**

1. **数据库膨胀与压缩失效**  
   用户反馈 `event` 表持续增长无回收机制，磁盘占满导致服务不可用；同时存在压缩循环与压缩后 Agent 失忆的双重问题，是当前最影响生产稳定性的瓶颈。

2. **严格 Provider 的兼容性**  
   Kimi K3、Moonshot 等对 assistant message 有严格校验的 provider 频繁返回 400 错误，社区已开发插件 workaround（#46332），但核心层修复尚未合入。

3. **Windows 桌面端体验**  
   ARM64 原生支持、UNC 路径处理、快捷键冲突、滚动行为等问题集中出现，表明桌面端在不同平台上的打磨仍需加强。

4. **长会话中断恢复**  
   系统休眠/恢复后 session 状态残留导致后续请求失败，中断的 assistant turn 被持久化后引发连锁错误。

5. **Skill 加载确定性**  
   同名 Skill 在不同 root 路径下的加载顺序不一致，导致重启后可用技能列表变化，影响可复现性。

---

*报告生成时间：2026-08-31*  
*数据源：github.com/anomalyco/opencode*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 — 2026-08-31

## 1. 今日速览

今日 Pi 社区无新版本发布，主要动态集中在 **0.84.3 内存泄漏/OOM 问题**的持续讨论与修复跟进，以及多路 provider 支持扩展（DeepSeek V4 迁移至 Responses API、腾讯 Token Plan 接入）。同时，JSONL 会话写入重复和数据损坏的 bug 已被修复 PR 合入，分支摘要 token 上限硬编码问题也已解决。

---

## 2. 版本发布

今日（过去 24 小时内）无新版本发布。

---

## 3. 社区热点 Issues

| # | 标题 | 亮点 | 链接 |
|---|------|------|------|
| #7547 | Windows 上运行 Pi 的最佳实践与问题汇总 | **51 条评论**，2 个👍，持续讨论中；社区对 Windows 体验关注度最高 | [Issue #7547](https://github.com/earendil-works/pi/issues/7547) |
| #8746 | 0.84.3 导致会话 OOM（20GB+） | 严重 bug：subagent 进程被内核 OOM Kill，两天内 5 次，作者称 0.84.2 正常 | [Issue #8746](https://github.com/earendil-works/pi/issues/8746) |
| #8852 | JSONL 会话重复打开导致序列号重复、文件损坏 | 严重数据完整性 bug：同一文件被两个 writer 写入 `seq: 1` | [Issue #8852](https://github.com/earendil-works/pi/issues/8852) |
| #8864 | 长会话上下文溢出后进入不可恢复的"死亡螺旋" | `contextWindow` 耗尽后 `max_tokens` 被静默压至 1，会话陷入循环崩溃 | [Issue #8864](https://github.com/earendil-works/pi/issues/8864) |
| #4748 | `getKeybindings()` 单例导致扩展无法正确解析快捷键 | 影响 pi-coding-agent 加载的扩展，`keyText()` 返回空字符串，hints 渲染异常 | [Issue #4748](https://github.com/earendil-works/pi/issues/4748) |
| #8877 | `read` tool 将 U+202F 窄空格规范化为普通空格，破坏 macOS 本地化路径 | 导致截屏文件名（如 `…  p.m..png`）ENOENT | [Issue #8877](https://github.com/earendil-works/pi/issues/8877) |
| #8845 | 分支摘要硬编码 `maxTokens: 2048` 导致大分支必然失败 | `/tree` 的 Summarize 功能确定性失败 | [Issue #8845](https://github.com/earendil-works/pi/issues/8845) |
| #8849 | Anthropic prompt cache 只写不读，`cacheRead` 始终不变 | 长期会话成本异常高，缓存未正确复用 | [Issue #8849](https://github.com/earendil-works/pi/issues/8849) |
| #8854 | 系统提示词膨胀：第三方插件累积 promptGuidelines | 8-15 个插件注入大量多行指令，影响模型表现和 token 消耗 | [Issue #8854](https://github.com/earendil-works/pi/issues/8854) |
| #8533 | 建议增加 Skill 可见性 API（deny-only） | 扩展可隐藏发现的 Skill，供正常会话消费；RFC 级别讨论 | [Issue #8533](https://github.com/earendil-works/pi/issues/8533) |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 | 链接 |
|---|------|------|------|------|
| #8876 | feat(ai): 新增腾讯 Token Plan Individual provider | ✅ Closed | 支持 tc-code-latest、deepseek-v4-flash/pro、glm-5.2、minimax-m2.7，通过 `TENCENT_TOKEN_PLAN_API_KEY` | [PR #8876](https://github.com/earendil-works/pi/pull/8876) |
| #8873 | fix(ai): DeepSeek V4 迁移至 OpenAI Responses API | ✅ Closed | 将 `deepseek-v4-flash/pro` 及 vision-exp 从 Completions API 迁移至 Responses API | [PR #8873](https://github.com/earendil-works/pi/pull/8873) |
| #8872 | fix(coding-agent): 扩展 API 暴露 host keybinding | ✅ Closed | 修复 #4748，解决扩展解析到私有 pi-tui 导致 `keyText()` 返回空字符串的问题 | [PR #8872](https://github.com/earendil-works/pi/pull/8872) |
| #8866 | fix(ai): 解除 codex WebSocket 空闲缓存计时器 | ✅ Closed | 修复 `pi -p` 在响应完成后进程仍存活约 5 分钟的问题（WebSocket 未正确释放） | [PR #8866](https://github.com/earendil-works/pi/pull/8866) |
| #8862 | fix(agent): 分支摘要 token 预算从 `reserveTokens` 动态推导 | ✅ Closed | 修复 #8845，不再硬编码 `maxTokens: 2048`，根据上下文预算动态计算 | [PR #8862](https://github.com/earendil-works/pi/pull/8862) |
| #8853 | fix(agent): 防止重复 JSONL writer | ✅ Closed | 按规范路径序列化 writable open，复用写入时校验，避免 #8852 的数据损坏问题 | [PR #8853](https://github.com/earendil-works/pi/pull/8853) |
| #8635 | fix(ai): 保留 lazy setup 期间的 aborted stop reason | 🔄 Open | 修复 #8409，将 abort signal 传递至 lazy stream setup，工具执行期间 abort 不再丢失 | [PR #8635](https://github.com/earendil-works/pi/pull/8635) |
| #8232 | DONT MERGE: dev branch | 🔄 Open | CI 测试分支，暂不合并 | [PR #8232](https://github.com/earendil-works/pi/pull/8232) |

> 注：今日共 8 条 PR，全部收录。

---

## 5. 功能需求趋势

1. **多 Provider / 多模型接入**：腾讯 Token Plan（#8876）、Ollama Cloud（#4706）、StepFun（#8867）、z.ai（#6723）等新增 provider 请求持续，社区对模型接入速度要求高。
2. **性能与稳定性**：OOM（#8746）、长会话死亡螺旋（#8864）、prompt cache 未生效（#8849）是近期高频痛点，开发者对生产级稳定性期待强烈。
3. **扩展生态完善**：Skill 可见性 API（#8533）、bash tool 可选 description（#8863）、native vs handler 错误区分（#8856）反映扩展开发者对 API 语义清晰度的需求。
4. **TUI/UX 改进**：Markdown 软换行渲染（#8751）、思考模式 word wrap（#8855）、思考深度快捷切换（#2941）属于细节体验优化，需求稳定。
5. **系统提示词治理**：#8854 提出社区方案 `pi-prompt-diet`，反映插件生态膨胀后对核心 prompt 的维护压力。

---

## 6. 开发者关注点

| 痛点 | 涉及 Issue/PR | 说明 |
|------|---------------|------|
| **长会话内存泄漏** | #8746、#8864 | 0.84.3 升级后 OOM 频繁，上下文溢出后无恢复机制，是当下最紧急的稳定性问题 |
| **JSONL 会话文件损坏** | #8852、#8853 | 同一文件被多 writer 打开导致序列号重复，已修复但需确认后续版本 |
| **WebSocket 资源泄漏** | #8868、#8866 | Codex provider 扩展导致 `pi -p` 进程挂起 5 分钟，已修复 |
| **Provider 集成碎片化** | #4748、#8872 | 扩展解析到私有 pi-tui 副本，keybinding/tool 等模块隔离问题反复出现 |
| **Prompt 缓存未生效** | #8849 | Anthropic cacheRead 始终为 0，长期会话成本异常，需关注 provider 侧实现 |
| **路径 Unicode 规范化** | #8877 | macOS 本地化文件名包含窄空格导致 ENOENT，属于边缘但影响真实用户的 bug |
| **分支摘要功能不可用** | #8845、#8862 | 硬编码 2048 token 导致大分支 Summarize 必失败，现已修复 |

---

**总结**：今日社区活跃度集中在 **稳定性修复** 和 **provider 扩展** 两个方向。0.84.3 引入的 OOM 和长会话问题需密切跟踪；扩展生态方面，腾讯 Token Plan 和 DeepSeek V4 Responses API 迁移是最新亮点。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报
**日期：2026-08-31**

---

## 1. 今日速览

过去24小时 Qwen Code 社区活跃度高，共更新 45 个 Issues 和 50 个 PR。核心动向包括：跨会话消息通信功能需求升温（#8724，12 评论）、Web Shell 多项体验改进持续推进，以及多项安全审查发现被系统自动归档为待处理 Issue。

---

## 2. 版本发布

**无新版本发布。** 昨夜(v0.22.3-nightly.20260830)发布流水线因 integration 测试失败中止，已关闭（#10535）。

---

## 3. 社区热点 Issues

| # | 标题 | 重点关注原因 |
|---|------|-------------|
| **#8724** | 跨会话消息通信：同机会话互通 | 多 Agent 协作核心能力，社区呼声高，12 条评论持续跟进 |
| **#8124** | 启动 Banner 首屏偶发缺行 | UI 渲染 bug，与 provider 更新状态相关，15 条评论为近期最高 |
| **#8784** | Streamable HTTP MCP 可选 GET/SSE 被 404 导致连接中断 | MCP 协议兼容性关键问题，影响生产环境稳定性 |
| **#10603** | ToolSearch 触发完整 prompt 重新处理（预填充） | 性能问题，影响 llama.cpp 后端响应延迟 |
| **#4016** | 加密存储敏感配置（AES-256-GCM） | 安全需求强烈，解决 API Key / Token 明文存储痛点 |
| **#10538** | Computer Use driver 0.20.0 在 Windows x64 上 panic | 桌面端核心功能故障，阻塞 Windows 用户 |
| **#10377** | 实现 CodeModeOnly 风格程序化工具调用 | 对齐 OpenAI Codex 能力，探索受限 JS runtime 执行模式 |
| **#10564** | Web Shell 将 provider 错误掩盖为通用 "Internal error" | 调试体验差，影响问题定位效率 |
| **#10568** | 模型配置热加载，无需重启 CLI | 开发者高频痛点，对标竞品 Qoder CLI 已支持 |
| **#10561** | command-execution config keys 安全审查（P1） | 涉及 git hooks / fsmonitor 等攻击面，优先级最高 |

---

## 4. 重要 PR 进展

| # | 标题 | 内容摘要 |
|---|------|---------|
| **#10080** | fix(core): 规范化 grammar-based provider 的工具 schema | 解决旧版 llama.cpp 不兼容空对象 grammar 的问题 |
| **#10602** | fix(sdk): 提高浏览器 daemon bundle 预算至 216KB | 修复 main 分支 CI 构建失败（bundle 超限） |
| **#10489** | fix(web-shell): 持久化模型推理偏好 | 跨 daemon 会话保留 reasoning effort 设置 |
| **#10534** | fix(vscode): WebShell 切换后恢复原生 diff 审批流 | 修复权限审批在 UI 迁移后的断裂问题 |
| **#10589** | feat(web-shell): 新增 Workspaces 概览面板 | 全页表格展示所有 workspace 状态、会话数、MCP 健康度 |
| **#10390** | feat(web-shell): 脏工作树时解锁 git update | 提供处理未提交变更的两种解决方案路径 |
| **#10283** | feat(cli): 通过设置或 flag 选择输出样式 | 支持 `Concise`/`Proactive`/`Explainer` 等内置风格 |
| **#10347** | fix(core): 对不可用 Ctrl+Y 场景自动重试瞬态网络错误 | 将 EOF 类 4xx 识别为可重试传输错误 |
| **#10427** | fix(hooks): 关闭钩子系统四个信任边界漏洞 | 修复 HTTP hooks 不跟随重定向、仓库配置执行风险等安全问题 |
| **#9590** | feat: 支持 provider 感知的推理控制 | 为 DeepSeek V4、GLM 5.2、Kimi 等模型适配差异化 reasoning 选项 |

---

## 5. 功能需求趋势

- **多 Agent / 跨会话协作**：#8724（会话互通）、#9033（Workflow 任务暴露）反映社区对多 Agent 编排的强烈需求。
- **Web Shell 体验升级**：Workspaces 面板（#10589）、推理偏好持久化（#10489）、模型配置热加载（#10568）持续迭代。
- **安全与沙箱强化**：加密存储（#4016）、Bubblewrap 后端（#10583）、钩子信任边界修复（#10427）、P1 级命令执行审查（#10561/#10560）。
- **性能优化**：ToolSearch 触发全 prompt 重处理（#10603）、ECS 测试超时优化（#10597）。
- **模型支持扩展**：provider-aware 推理控制（#9590）、grammar schema 兼容（#10080）。

---

## 6. 开发者关注点

| 痛点 | 关联 Issue / PR |
|------|----------------|
| 敏感配置（API Key / Token）明文存储风险 | #4016 |
| 模型配置修改后需重启 CLI 才能生效 | #10568 |
| Web Shell 错误信息被掩盖，难以定位问题 | #10564、#10570 |
| Windows 端 Computer Use 驱动频繁 panic | #10538 |
| 微信 Bot 发送图片路径限制导致失败 | #4441 |
| 启动 Banner 首屏渲染不稳定 | #8124 |
| 大文件/高竞争环境下 CI 超时 | #10597 |
| Termius SSH 会话中输入内容被损坏 | #10562 |
| MCP Server 对可选 SSE 流返回 404 导致连接断裂 | #8784 |
| ask 模式下 PreToolUse hook 返回值不展示 diff | #9434 |

---

**链接汇总**：所有 Issue/PR 均位于 [github.com/QwenLM/qwen-code](https://github.com/QwenLM/qwen-code)，具体编号已在各条目中标注。

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI 社区动态日报
**日期：2026-08-31**

---

## 1. 今日速览

Codewhale v0.9.12 版本发布准备中（PR #5744），今日集中提交了 20+ 个 TUI 体验改进 PR，涵盖 Tideline composer 重构、provider 选择交互优化、MCP 认证统一化等核心功能。社区对网络错误导致引擎停止（#5769）和 context pressure 警告机制（#5620）的稳定性问题关注度较高。

---

## 2. 版本发布

| 版本 | 状态 | 说明 |
|------|------|------|
| v0.9.12 | 🔄 准备中 | PR #5744 正在准备，包含 113 条更新 bullet（Added 40, Changed, Fixed 等），需 founder 确认后发布 |

---

## 3. 社区热点 Issues

### 高热度问题

**1. #5316 EPIC-005: CodeWhale TUI Crate Decomposition** `[OPEN]` 20 条评论
> 核心架构重构 umbrella issue，跟踪整个 TUI crate 分解工作，影响范围覆盖所有子 EPIC 和 FEAT。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/5316

**2. #5620 Context pressure warning 是瞬态的，agent 未主动响应** `[OPEN]` 11 条评论
> **Medium 严重性 bug**：context pressure 警告在 agent turn metadata 中生成后未触发主动应对措施，导致 silent context degradation。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/5620

**3. #5723 Agent shell 设置 NoNewPrivs，阻塞 sudo** `[CLOSED]` 3 条评论
> **High 严重性 bug**：exec_shell sandbox 设置 `NoNewPrivs` 导致已验证的生产部署流程中断，已修复。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/5723

**4. #5769 网络错误偶尔导致引擎停止** `[OPEN]` 1 条评论
> Linux Mint 环境下网络错误后引擎未自动恢复，影响长时间运行的 agent session 稳定性。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/5769

**5. #5713 自定义 provider 支持 Responses/Anthropic wire** `[OPEN]` 2 条评论
> `kind="openai-compatible"` 配置 `wire = "responses" | "anthropic"` 被忽略，始终走 ChatCompletions，导致部分 provider 不可用。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/5713

### 新功能需求

**6. #3751 Neuralwatt Provider 支持** `[OPEN]` 2 条评论
> 社区请求集成 Neuralwatt（支持 GLM 5.2，非 token 定价模型），反映新兴 provider 集成需求。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/3751

**7. #1330 Zenmux 作为 DeepSeek-V4-Pro & Flash 主 provider** `[OPEN]` 2 条评论
> 请求 first-class 集成 ZenMux，当前需手动 override base URL，影响用户体验。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/1330

**8. #2535 ACP+MCP 支持与 exec 模式流式输出** `[OPEN]` 1 条评论
> 用户希望 ACP 模式支持 MCP 工具调用，实现飞书 IM → Codewhale → MCP 工具的完整链路。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/2535

**9. #1097 FreeBSD 支持** `[OPEN]` 3 条评论
> npm 安装失败，缺少 FreeBSD 平台二进制包，反映边缘平台支持需求。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/1097

**10. #4955 zero-sandbox / --no-sandbox 模式** `[OPEN]` 5 条评论 | 👍 1
> 用户请求完全禁用 sandbox 的本地开发模式，Kernel-level Seatbelt sandbox 导致基础 shell 命令每日失败。
> 🔗 https://github.com/Hmbown/CodeWhale/issues/4955

---

## 4. 重要 PR 进展

### 版本准备

**PR #5744** `release: prepare Codewhale v0.9.12`
> 版本发布准备，包含 workspace/npm/runtime-sdk/VS Code extension 版本 bump 至 0.9.12，CHANGELOG 新增 113 条 bullet。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5744

### TUI 体验改进

**PR #5773** `Give the active-session composer the shared [↑] send hitbox`
> 恢复活跃会话 ComposerWidget 的共享三格 `[↑]` 发送区域，防止长草稿覆盖提交按钮。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5773

**PR #5770** `Compose Tideline startup into the shared composer shell`
> 将 Startup 整合到统一的 Rounded Tideline composer shell，包括 current-mark、route-control 等 source proposals。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5770

**PR #5766** `feat(config): bind catalog and route resolution`
> 将编译后的 provider catalog 绑定到 RouteResolver，返回诚实的 receipt 用于 catalog-backed、custom-endpoint 和 pass-through routes。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5766

**PR #5760** `fix(tui): keep MCP boot detail out of chat`
> 将 MCP 启动详情从聊天/composer shell 移出，保留 footer 作为 compact status surface。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5760

**PR #5758** `fix(tui): restore rounded active composer enclosure`
> 在可行尺寸下恢复真实的 rounded ComposerWidget enclosure，保留 live input、wrapping、cursor 等路径。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5758

### 协议与基础设施

**PR #5751** `feat(protocol): Op/EventMsg parity + compile-enforced guard`
> 实现 Rust core 与 TS surfaces 之间的 Op/EventMsg 对齐，通过编译守护防止静默漂移。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5751

**PR #5749** `feat(app-server): unix-socket transport + daemon/attach advertisement`
> 新增 unix-socket 传输支持和 daemon/attach 广播，作为 desktop Phase 0 基础。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5749

**PR #5752** `feat(cloud-facts): signed, versioned, cached facts channel`
> Slice 1 of Supabase-backed cloud facts channel：签名+版本化+缓存的事实通道，默认关闭。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5752

### 修复与基础设施

**PR #5750** `fix(session): engine adopts the host session id`
> 修复会话恢复 bug：Engine 应采纳 host session id 而非生成自己的，确保 resumed turn 落入正确 session。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5750

**PR #5747** `feat(tui): unified self-serve MCP/plugin auth`
> 统一 MCP/plugin 认证：合成 `authenticate` tool、共享 `/mcp login` 流程、invalid_grant rotation 处理。
> 🔗 https://github.com/Hmbown/CodeWhale/pull/5747

---

## 5. 功能需求趋势

| 趋势方向 | 具体需求 | 相关 Issue/PR |
|----------|----------|---------------|
| **多模型/新 Provider** | Neuralwatt、Zenmux 集成，Responses/Anthropic wire 支持 | #3751, #1330, #5713 |
| **TUI 交互优化** | Composer 提交按钮、Tideline 启动壳、Provider 选择器显式化 | #5773, #5770, #5772, #5763 |
| **MCP/ACP 集成** | ACP 模式支持 MCP 工具调用，统一认证流程 | #2535, #5747 |
| **远程 Workbench** | US-first 基础设施、Self-hosted Mac 支持 | #1990, #1984, #2968 |
| **跨平台支持** | FreeBSD 二进制包、零沙箱本地开发模式 | #1097, #4955 |
| **视觉/UX** | 浏览器 console verification、Hotbar 命令表面 | #3145, #3851, #3361 |

---

## 6. 开发者关注点

### 高频痛点

1. **沙箱限制**：`NoNewPrivs` 阻塞 sudo（#5723）、Seatbelt sandbox 影响基础命令（#4955），开发者需要灵活的控制权
2. **上下文压力管理**：警告机制瞬态且 agent 未主动响应（#5620），影响长 session 稳定性
3. **网络错误恢复**：网络错误后引擎停止而非自动恢复（#5769），影响长时间运行场景
4. **会话恢复 Bug**：Engine 生成自己的 session id 导致恢复失败（#5750），是用户反馈的关键可靠性问题
5. **测试 Flakiness**：并行负载下的 flaky test（#5605, #5735）影响 CI 信任度

### 高频需求

- 自定义 Provider 的 wire format 支持（Responses/Anthropic）
- 零配置/本地开发模式的沙箱绕过
- MCP 工具在 ACP 模式下的可用性
- 跨平台（FreeBSD、Mac self-hosted）的二进制支持
- Provider 选择器的显式确认流程，避免 credential 泄漏

---

*数据来源：github.com/Hmbown/DeepSeek-TUI（CodeWhale）*
*报告生成时间：2026-08-31*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*