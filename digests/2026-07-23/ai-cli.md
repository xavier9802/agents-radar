# AI CLI 工具社区动态日报 2026-07-23

> 生成时间: 2026-07-23 01:23 UTC | 覆盖工具: 10 个

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
**日期**: 2026-07-23
**分析师**: Agnes-2.0-Flash

## 1. 生态全景
当前 AI CLI 生态正从“单一助手”向“多智能体协作平台”演进，Agent 架构（Subagents, Skills）成为各主流工具的核心差异化战场。底层稳定性与跨平台兼容性（尤其是 Windows 和 Linux Wayland）是制约用户体验的最大瓶颈，资源泄漏和权限管理问题频发。同时，社区对成本透明度、上下文精细化管理及第三方 API 兼容性的诉求日益强烈，推动工具向更开放、更可配置的方向发展。

## 2. 各工具活跃度对比

| 工具名称 | Issues (今日/重点) | PRs (今日/重点) | Release 情况 | 核心动态关键词 |
| :--- | :--- | :--- | :--- | :--- |
| **Claude Code** | Top 10 Issues | Top 10 PRs | v2.1.218 (发布) | macOS 文件调用失败、权限绕过失效、后台子代理优化 |
| **OpenAI Codex** | Top 10 Issues | Top 10 PRs | Rust v0.146.0-alpha.4 (连续迭代) | Windows 稳定性差、MCP 内存泄漏、多账户隔离 |
| **Gemini CLI** | Top 10 Issues | Top 10 PRs | v0.53.0-preview.0, v0.52.0 | A2A 协议修复、子代理恢复机制、Wayland 崩溃 |
| **GitHub Copilot** | Top 10 Issues | < 1 显著 PR | v1.0.74-3 (补丁) | Windows 僵尸进程、计费透明度、多代理协作 |
| **Kimi Code** | 5 Issues | 3 PRs | 无 | 第三方 API 兼容 (`prompt_cache_key`)、子代理模型选择 |
| **OpenCode** | Top 10 Issues | Top 10 PRs | 无重大版本 (V2 维护中) | V2 内存泄漏、订阅上游阻断、位置启动缓存 Bug |
| **Pi** | 10 Issues | 10 PRs | 无 | SDK 重试机制修复、Bedrock 自适应思维、TUI 性能 |
| **Qwen Code** | Top 10 Issues | Top 10 PRs | v0.0.0-benchmark-poc (内部测试) | Goal v3 状态协议、CI/CD 稳定性、Prompt 分层优化 |
| **DeepSeek TUI** | Top 10 Issues | Top 10 PRs | v0.9.1 收尾 / v0.9.2 规划 | 上下文瘦身 (Context Diet)、统一技能管理器、Windows PATH 安全 |

## 3. 共同关注的功能方向

*   **多智能体与工作流精细化控制**：
    *   **涉及工具**：Claude Code, Gemini CLI, OpenCode, Kimi Code, DeepSeek TUI。
    *   **具体诉求**：开发者普遍要求支持子代理（Subagent）的独立配置、错误自动恢复、以及更细粒度的权限和计费控制。例如，Kimi Code 提出按代理选择模型以平衡成本，Claude Code 优化了后台子代理体验。
*   **跨平台稳定性与兼容性（特别是 Windows/Linux）**：
    *   **涉及工具**：OpenAI Codex, GitHub Copilot, Gemini CLI, DeepSeek TUI, Claude Code。
    *   **具体诉求**：Windows 端的沙箱崩溃、路径解析错误、进程僵尸化是高频痛点；Linux 端则聚焦于 Wayland 显示服务器支持和终端渲染一致性。
*   **MCP (Model Context Protocol) 集成深化与缺陷修复**：
    *   **涉及工具**：OpenAI Codex, Gemini CLI, Claude Code, OpenCode。
    *   **具体诉求**：随着 MCP 成为标准，社区高度关注其进程管理（泄漏、僵尸进程）、工具发现完整性及配置隔离问题。
*   **上下文管理与 Token 效率**：
    *   **涉及工具**：Qwen Code, DeepSeek TUI, Pi, OpenAI Codex。
    *   **具体诉求**：通过 Prompt 分层、自动压缩阈值调整、以及“上下文瘦身”策略来降低长会话的成本并提升响应速度。

## 4. 差异化定位分析

*   **企业级与标准化导向**：
    *   **Claude Code**：强调工作流的平滑性和无障碍支持，通过后台子代理和代码审查优化专业开发体验，但在原生扩展稳定性上存在争议。
    *   **GitHub Copilot CLI**：深度绑定 GitHub 生态，侧重 CI/CD 集成和企业计费透明性，但近期 Windows 稳定性问题较多。
*   **底层重构与高性能导向**：
    *   **OpenAI Codex**：采用 Rust 重写核心，处于激进的性能优化迭代期，但伴随较高的稳定性和平台适配风险（尤其是 Windows）。
    *   **Qwen Code**：侧重于 Agent 状态协议的标准化（Goal v3）和内部基准测试体系构建，技术路线偏向严谨的工程化落地。
*   **灵活性与生态扩展导向**：
    *   **Gemini CLI**：积极拥抱 A2A 协议和多模型路由，注重 Agent 间的互操作性和安全性（如 RCE 防护）。
    *   **DeepSeek TUI (CodeWhale)**：定位为轻量级、高定制化的替代品，强调“上下文瘦身”和统一技能管理，吸引追求极致效率和本地化部署的用户。
*   **开发者体验与兼容性导向**：
    *   **Pi**：专注于 TUI 交互细节、外部编辑器集成及广泛的 AI 提供商兼容性（如 Bedrock, StepFun），适合喜欢自定义工作流的资深开发者。
    *   **OpenCode**：正处于 V2 架构的关键磨合期，面临性能优化和订阅服务稳定性的双重挑战，旨在提供类似 IDE 的全栈体验。

## 5. 社区热度与成熟度

*   **高热度/快速迭代期**：**OpenAI Codex**（Rust 重构带来大量 Alpha 版本和 Issue）、**DeepSeek TUI**（v0.9.1 收尾及 v0.9.2 规划活跃）、**Pi**（极高的 PR/Issue 更新率，显示开发者参与度极高）。
*   **成熟/稳定维护期**：**Claude Code**（版本迭代相对稳健，社区焦点集中在特定平台 Bug 和功能微调）、**Qwen Code**（侧重基础设施和协议标准，用户基数增长带来的稳定性反馈增多）。
*   **波动/修复期**：**GitHub Copilot CLI**（新功能发布少，主要精力用于修复回归 Bug 和平台稳定性）、**Gemini CLI**（版本更新频繁，重点解决协议兼容性和 Agent 可靠性）。

## 6. 值得关注的趋势信号

1.  **“上下文经济学”成为核心竞争力**：DeepSeek TUI 的“Context Diet”和 Qwen Code 的 Prompt 分层策略表明，未来 CLI 工具的竞争将不仅在于模型能力，更在于如何以更少的 Token 提供更精准的控制和更低的成本。
2.  **多智能体协作的“去黑盒化”**：用户不再满足于简单的任务委托，而是要求对子代理的行为、计费、错误恢复有完全的可观测性和控制权（如 Kimi Code 的独立模型选择、Claude Code 的后台执行）。
3.  **平台适配成为“阿喀琉斯之踵”**：尽管 AI 模型本身是跨平台的，但 CLI 工具在 Windows 和 Linux 特定环境（Wayland, WSL）下的表现严重滞后于 Mac/Linux 原生体验。解决这些碎片化问题是提升大众采用率的关键。
4.  **MCP 从“可用”走向“可靠”**：社区对 MCP 的关注点已从“能否连接”转向“是否泄漏资源”、“是否安全隔离”。这预示着下一代 CLI 工具必须内置更健壮的进程管理和沙箱机制。
5.  **开源与闭源工具的界限模糊**：像 Pi 和 DeepSeek TUI 这样的项目，通过提供高度的可配置性和广泛的提供商支持，正在吸引那些对特定闭源工具（如 Claude Code 或 Codex）的局限性感到不满的企业和个人用户。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills 社区热点报告
**数据截止：** 2026-07-23
**分析师：** Agnes-2.0-Flash (Sapiens AI)

## 1. 热门 Skills 排行 (Top PRs by Engagement)

以下 PR 基于社区评论活跃度及功能影响力排序，反映了当前开发者和用户最关注的技能改进方向。

| 排名 | Skill 名称/功能 | 状态 | GitHub 链接 | 社区关注点摘要 |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Self-Audit (自审计)** | Open | [PR #1367](https://github.com/anthropics/skills/pull/1367) | 提供机械文件验证与四维推理质量门禁，被视为提升 AI 输出可靠性的关键基础设施。 |
| 2 | **Skill Creator Fix (评估修复)** | Open | [PR #1298](https://github.com/anthropics/skills/pull/1298) | 修复 `run_eval.py` 始终报告 0% recall 的严重 Bug，直接影响技能描述优化的有效性。 |
| 3 | **Frontend Design 优化** | Open | [PR #210](https://github.com/anthropics/skills/pull/210) | 重构前端设计技能，提升指令的可执行性与清晰度，解决“幻觉”指令问题。 |
| 4 | **ODT 支持** | Open | [PR #486](https://github.com/anthropics/skills/pull/486) | 新增对 OpenDocument 格式 (.odt/.ods) 的创建、填充与解析支持，填补开源办公格式空白。 |
| 5 | **Color Expert (色彩专家)** | Open | [PR #1302](https://github.com/anthropics/skills/pull/1302) | 提供专业色彩空间（OKLCH, CAM16等）命名与转换能力，满足高精度 UI/UX 设计需求。 |
| 6 | **Document Typography (排版)** | Open | [PR #514](https://github.com/anthropics/skills/pull/514) | 解决 AI 生成文档中的孤行、寡行及编号对齐问题，提升文档出版级质量。 |
| 7 | **Testing Patterns (测试模式)** | Open | [PR #723](https://github.com/anthropics/skills/pull/723) | 涵盖单元测试至 React 组件测试的全栈测试方法论，强化代码质量保障流程。 |

## 2. 社区需求趋势

从 Issues 反馈中提炼出以下核心需求方向：

*   **企业级协作与共享：** Issue #228 呼声极高，用户迫切希望实现组织内技能的直接共享（如通过 Slack/Teams 集成或共享库），而非手动下载上传。
*   **安全性与信任边界：** Issue #492 揭示了社区对“冒充官方技能”的安全担忧，呼吁建立更严格的命名空间管理和身份验证机制。
*   **Agent 治理与记忆优化：** Issue #412 和 #1329 分别提出了“Agent 治理”和“紧凑记忆”技能的需求，表明用户开始关注长上下文管理中的效率及 AI 行为的安全性。
*   **跨平台兼容性：** Issue #1061 和 #29 显示 Windows 用户和 AWS Bedrock 用户对技能运行环境的兼容性有强烈痛点，急需官方层面的底层支持修复。

## 3. 高潜力待合并 Skills

以下 PR 处于 Open 状态且具有较高的技术价值或修复紧迫性，近期合并概率较大：

1.  **[PR #1298] fix(skill-creator): run_eval.py always reports 0% recall**
    *   **理由：** 该 Bug 导致技能描述优化循环失效，是 `skill-creator` 工作流的阻塞性问题，修复优先级最高。
2.  **[PR #1367] feat(skills): add self-audit**
    *   **理由：** 引入了“交付前审计”的新范式，符合当前对 AI 可靠性的高要求，具有标杆意义。
3.  **[PR #486] Add ODT skill**
    *   **理由：** 补全了主流办公文档格式的支持矩阵（已有 DOCX/PDF，缺失 ODT），实用性强。
4.  **[PR #1302] Add color-expert skill**
    *   **理由：** 针对垂直领域（色彩科学）的深度专业化技能，能显著提升特定任务（如品牌设计）的输出质量。

## 4. Skills 生态洞察

**当前社区最集中的诉求是：从“功能可用性”转向“可靠性与安全治理”，亟需解决评估工具缺陷、Windows 兼容性及企业级共享信任机制。**

---

# Claude Code 社区动态日报
**日期**: 2026-07-23
**数据来源**: github.com/anthropics/claude-code

## 1. 今日速览
今日社区焦点集中在 **macOS 文件系统工具调用静默失败** 及 **权限绕过模式长期失效** 两大核心 Bug 上，引发大量开发者讨论。同时，文档维护工作显著增加，多个关于 Skills、Subagents 和 MCP 配置的文档缺失问题被集中提出。新版本 v2.1.218 优化了代码审查的工作流体验。

## 2. 版本发布
**v2.1.218**
- **核心改进**: `/code-review` 命令现作为后台子代理（background subagent）运行，不再占用主对话窗口，且能正确识别堆叠的斜杠命令作为审查目标。
- **无障碍支持**: 增加了针对单词和行删除操作（如 `Option+Delete`, `Ctrl+W`, `Cmd+Backspace`）的屏幕阅读器文本删除公告功能。

## 3. 社区热点 Issues (Top 10)

1.  **[BUG] macOS: Claude Desktop never dispatches tools/call to the first-party Filesystem extension**
    - **ID**: #80002 | **评论**: 56 | **点赞**: 25
    - **重要性**: 涉及官方原生扩展的核心功能失效，严重影响 macOS 用户的基础文件操作能力。
    - **链接**: https://github.com/anthropics/claude-code/issues/80002

2.  **[META] Bypass permissions mode is fundamentally broken**
    - **ID**: #39523 | **评论**: 33 | **点赞**: 18
    - **重要性**: 这是一个持续近 9 个月的元问题，指出 `bypassPermissions` 模式自 2025 年 7 月以来一直存在根本性缺陷，社区对解决此权限痛点呼声极高。
    - **链接**: https://github.com/anthropics/claude-code/issues/39523

3.  **[BUG] Chat JSONLs deleted from ~/.claude/projects/ despite cleanupPeriodDays set high**
    - **ID**: #62272 | **评论**: 19 | **点赞**: 3
    - **重要性**: 导致历史聊天记录意外丢失，作者甚至开发了恢复脚本，凸显数据持久化的严重隐患。
    - **链接**: https://github.com/anthropics/claude-code/issues/62272

4.  **[BUG] GitHub connector shows "Connected" but exposes no tools in Cowork**
    - **ID**: #61682 | **评论**: 17 | **点赞**: 19
    - **重要性**: Windows 平台下 GitHub 连接器状态显示正常但功能不可用，阻碍了协作开发流程。
    - **链接**: https://github.com/anthropics/claude-code/issues/61682

5.  **[BUG] macOS: filesystem-class MCP tool calls silently dropped**
    - **ID**: #79992 | **评论**: 16 | **点赞**: 4
    - **重要性**: 与 #80002 类似，进一步确认了 macOS 上 MCP 文件系统工具调用在审批后静默丢弃的问题，复现稳定且难以排查。
    - **链接**: https://github.com/anthropics/claude-code/issues/79992

6.  **[BUG] mcp__Claude_in_Chrome__navigate silently denies non-pre-approved domains**
    - **ID**: #50842 | **评论**: 13 | **点赞**: 6
    - **重要性**: 浏览器自动化中的导航功能缺乏用户可见的审批路径，导致非预批准域名被静默拒绝，影响 Web 自动化测试。
    - **链接**: https://github.com/anthropics/claude-code/issues/50842

7.  **[FEATURE] Desktop app: inject queued messages mid-task between tool calls**
    - **ID**: #71726 | **评论**: 9 | **点赞**: 16
    - **重要性**: 请求桌面应用实现 CLI/TUI 中已有的“任务中注入消息”（steering）功能，提升交互式开发的灵活性。
    - **链接**: https://github.com/anthropics/claude-code/issues/71726

8.  **[BUG] Remote Control never connects: Cannot read properties of undefined**
    - **ID**: #78933 | **评论**: 8 | **点赞**: 0
    - **重要性**: 远程控制功能在桌面端完全不可用，报错指向内部对象属性访问错误。
    - **链接**: https://github.com/anthropics/claude-code/issues/78933

9.  **[Bug] Fable 5: confidently claimed 'verified, copy changed' against user's correct report**
    - **ID**: #80348 | **评论**: 3 | **点赞**: 0
    - **重要性**: 反映新模型 Fable 在自我验证时存在幻觉或逻辑错误，影响用户对模型输出准确性的信任。
    - **链接**: https://github.com/anthropics/claude-code/issues/80348

10. **[BUG] Structured Task tools unavailable in top-level CLI session**
    - **ID**: #80213 | **评论**: 2 | **点赞**: 1
    - **重要性**: 环境变量已启用但 Task 工具未暴露，且仅影响 CLI 而不影响桌面端，表明存在环境或配置同步的 Bug。
    - **链接**: https://github.com/anthropics/claude-code/issues/80213

## 4. 重要 PR 进展

1.  **feat(plugins): add /planwith command for inline plan mode prompts**
    - **ID**: #18217 | **状态**: Closed
    - **内容**: 允许 `/plan` 命令直接接受内联参数，简化了计划模式的激活流程，减少操作步骤。
    - **链接**: https://github.com/anthropics/claude-code/pull/18217

2.  **Add account profiles plugin**
    - **ID**: #80326 | **状态**: Open
    - **内容**: 实验性插件，支持在同一机器上管理隔离的 `CLAUDE_CONFIG_DIR` 启动环境，便于区分个人、工作或客户端账户。
    - **链接**: https://github.com/anthropics/claude-code/pull/80326

3.  **Add twilight plugin: spec-first design/implement skills with a durable focus stack**
    - **ID**: #80008 | **状态**: Open
    - **内容**: 演示了一种结合设计、实现和焦点堆栈的新策略，旨在增强 Claude 的功能深度，虽需大量修改但展示了未来插件生态的可能方向。
    - **链接**: https://github.com/anthropics/claude-code/pull/80008

4.  **fix: [BUG] Console scrolling top of history when claude add text to the console**
    - **ID**: #80241 | **状态**: Open
    - **内容**: 修复了当 Claude 向控制台添加文本时，视图自动滚动到历史记录顶部的体验问题。
    - **链接**: https://github.com/anthropics/claude-code/pull/80241

5.  **fix: [Bug] Auto-compact never triggers despite statusline reporting "100% context used"**
    - **ID**: #80196 | **状态**: Open
    - **内容**: 修复了上下文满载时自动压缩机制未触发的 Bug，确保长会话下的内存管理正常。
    - **链接**: https://github.com/anthropics/claude-code/pull/80196

6.  **fix: [BUG] Instantly hitting usage limits with Max subscription**
    - **ID**: #80195 | **状态**: Open
    - **内容**: 修复了 Max 订阅用户在某些情况下立即达到使用限制的错误，保障付费用户体验。
    - **链接**: https://github.com/anthropics/claude-code/pull/80195

7.  **Make devcontainer firewall init resilient to DNS resolution failures**
    - **ID**: #80112 | **状态**: Open
    - **内容**: 增强了 DevContainer 防火墙初始化的鲁棒性，防止因单个域名的 DNS 解析超时导致整个设置失败。
    - **链接**: https://github.com/anthropics/claude-code/pull/80112

8.  **docs(gcp): stop on checksum mismatch**
    - **ID**: #80353 | **状态**: Open
    - **内容**: 改进了 GCP 网关部署脚本，在下载二进制文件校验和不匹配时停止并清理，提高部署安全性。
    - **链接**: https://github.com/anthropics/claude-code/pull/80353

9.  **docs: fix 1 broken link(s) via archive.org**
    - **ID**: #80294 | **状态**: Open
    - **内容**: 使用 Wayback Machine 归档快照修复了文档中的一个失效外链。
    - **链接**: https://github.com/anthropics/claude-code/pull/80294

10. **docs: fix 1 broken link(s) via archive.org**
    - **ID**: #80229 | **状态**: Open
    - **内容**: 另一处文档外链修复，同样采用归档方式保持引用有效性。
    - **链接**: https://github.com/anthropics/claude-code/pull/80229

## 5. 功能需求趋势
- **多账户与环境隔离**: 开发者强烈需要更灵活的多账户管理方案（如 Account Profiles 插件），以支持同一设备上不同身份（个人/工作）的隔离配置。
- **工作流精细化控制**: 对“任务中注入消息”（Steering）、后台子代理执行（如 `/code-review`）以及 Plan Mode 的即时反馈有持续需求，旨在提升交互的流畅度和控制权。
- **文档完整性**: 大量 Issue 集中在文档缺失或过时，特别是关于 Skills、Subagents、MCP 配置及权限模式的细节说明，反映出官方文档更新滞后于功能迭代。

## 6. 开发者关注点
- **稳定性与 Bug 修复**: macOS 平台下的工具调用（特别是文件和浏览器相关）存在严重且频繁的静默失败问题，是社区最大的痛点。
- **权限管理**: `bypassPermissions` 模式的长期失效让用户感到困惑和受阻，亟需官方给出明确解释或修复。
- **数据持久化**: 聊天历史记录的非预期删除引发了对数据安全的担忧，用户希望有更可靠的备份或存储机制。
- **新模型表现**: 对新模型 Fable 的验证逻辑和 Token 效率表示关注，部分用户希望提供更细粒度的模型选择（如 Fable Plan 模式）。

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex 社区动态日报
**日期：** 2026-07-23
**数据来源：** github.com/openai/codex

## 1. 今日速览
OpenAI Codex 今日重点发布了 Rust 核心组件的 `v0.146.0-alpha.4` 连续更新，表明底层引擎正处于快速迭代期。社区反馈显示 Windows 平台稳定性问题集中爆发，包括冷启动卡顿、沙箱崩溃及路径解析错误；同时，MCP（Model Context Protocol）相关的资源泄漏和进程管理缺陷成为技术讨论的高频痛点。

## 2. 版本发布
过去24小时内，Rust 核心库发布了四个 Alpha 版本，暗示正在进行密集的底层重构或性能优化测试：
*   **rust-v0.146.0-alpha.4**: [Release Link](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.4)
*   **rust-v0.146.0-alpha.3**: [Release Link](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.3)
*   **rust-v0.146.0-alpha.2**: [Release Link](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.2)
*   **rust-v0.146.0-alpha.1**: [Release Link](https://github.com/openai/codex/releases/tag/rust-v0.146.0-alpha.1)

## 3. 社区热点 Issues
以下 Issue 因评论数高、点赞多或涉及关键功能缺陷而备受关注：

1.  **[CLI] 禁用自动解决设置的需求** (Issue #28969)
    *   **摘要:** 用户希望增加配置项以禁用60秒内的自动问题解答机制，避免意外中断工作流。
    *   **热度:** 👍 151 | 💬 53
    *   **链接:** [Issue #28969](https://github.com/openai/codex/issues/28969)
2.  **[GUI] MCP 子进程僵尸化与内存泄漏** (Issue #12491)
    *   **摘要:** Codex.app GUI 中 MCP 任务完成后未回收子进程，导致数千个僵尸进程和37GB+内存泄漏。
    *   **热度:** 👍 5 | 💬 27
    *   **链接:** [Issue #12491](https://github.com/openai/codex/issues/12491)
3.  **[App] Desktop 更新后 Hooks 失效** (Issue #21639)
    *   **摘要:** 报告了 Codex Desktop 更新后自定义 Hooks 不再运行的回归 bug。
    *   **热度:** 👍 6 | 💬 23
    *   **链接:** [Issue #21639](https://github.com/openai/codex/issues/21639)
4.  **[Windows] WSL Agent 模式报错** (Issue #16815)
    *   **摘要:** Windows 环境下切换至 WSL Agent 模式时，因绝对路径反序列化缺少基础路径而失败。
    *   **热度:** 👍 13 | 💬 22
    *   **链接:** [Issue #16815](https://github.com/openai/codex/issues/16815)
5.  **[Enhancement] 配置 Worktrees 位置** (Issue #10599)
    *   **摘要:** 用户请求允许自定义 Git worktree 的创建位置，默认行为往往不符合大型项目结构。
    *   **热度:** 👍 66 | 💬 16
    *   **链接:** [Issue #10599](https://github.com/openai/codex/issues/10599)
6.  **[Sandbox] Windows 沙箱初始化失败** (Issue #22428)
    *   **摘要:** Windows 桌面版沙箱环境在设置刷新时失败，报错 `CreateProcessAsUserW failed`。
    *   **热度:** 👍 10 | 💬 15
    *   **链接:** [Issue #22428](https://github.com/openai/codex/issues/22428)
7.  **[CLI] MCP 管道文件描述符泄漏** (Issue #26984)
    *   **摘要:** MCP stdio 服务器存在 FD 泄漏和孤儿进程，长期运行会导致 `EMFILE` 错误。
    *   **热度:** 👍 3 | 💬 14
    *   **链接:** [Issue #26984](https://github.com/openai/codex/issues/26984)
8.  **[iOS] 支持无头远程 Linux 主机** (Issue #23200)
    *   **摘要:** 希望移动端 Codex 能直接控制始终在线的 Linux 服务器，无需依赖本地桌面应用保持在线。
    *   **热度:** 👍 42 | 💬 13
    *   **链接:** [Issue #23200](https://github.com/openai/codex/issues/23200)
9.  **[CLI] 等待用户输入超时问题** (Issue #27458)
    *   **摘要:** 用户在 WSL 环境下报告 Codex 在等待输入时出现非预期的超时现象。
    *   **热度:** 👍 43 | 💬 12
    *   **链接:** [Issue #27458](https://github.com/openai/codex/issues/27458)
10. **[App] 近期项目线程在侧边栏丢失** (Issue #30385)
    *   **摘要:** Windows 版 Codex Desktop 无法在侧边栏或搜索中显示最近的项目线程，尽管数据存在于磁盘索引中。
    *   **热度:** 👍 0 | 💬 9
    *   **链接:** [Issue #30385](https://github.com/openai/codex/issues/30385)

## 4. 重要 PR 进展
以下 PR 已合并或关闭，反映了最新的功能迭代方向：

1.  **PR #34852: 唤醒休眠线程以处理队列邮件**
    *   **内容:** 确保处于持久休眠状态的线程在收到代理工作消息时能被正确唤醒。
    *   **链接:** [PR #34852](https://github.com/openai/codex/pull/34852)
2.  **PR #34851: 使用批量元数据生成插件应用摘要**
    *   **内容:** 优化插件读取和安装响应的元数据加载，通过批量 API 提升效率并保留缓存。
    *   **链接:** [PR #34851](https://github.com/openai/codex/pull/34851)
3.  **PR #34850: 为免费计划禁用图像生成**
    *   **内容:** 识别免费账户计划后，跳过注册独立的 `image_generation` 工具，符合订阅限制。
    *   **链接:** [PR #34850](https://github.com/openai/codex/pull/34850)
4.  **PR #34849: 按作用域缓存远程插件目录**
    *   **内容:** 引入基于磁盘的缓存机制（3小时 TTL），优化全局、用户和工作区范围的插件目录加载。
    *   **链接:** [PR #34849](https://github.com/openai/codex/pull/34849)
5.  **PR #34847: 为审查会话使用 Guardian 模型限制**
    *   **内容:** 修正上下文窗口和自动压缩覆盖逻辑，确保 Guardian 审查会话使用正确的模型限制。
    *   **链接:** [PR #34847](https://github.com/openai/codex/pull/34847)
6.  **PR #34846: 允许自定义提供商启用独立网络搜索**
    *   **内容:** 新增 `supports_standalone_web_search` 设置，允许自定义 Responses 提供商启用独立 Web 搜索工具。
    *   **链接:** [PR #34846](https://github.com/openai/codex/pull/34846)
7.  **PR #34845: 在世界状态中跟踪多代理模式**
    *   **内容:** 将多代理模式指令持久化到世界状态中，确保其在历史变化中保持稳定。
    *   **链接:** [PR #34845](https://github.com/openai/codex/pull/34845)
8.  **PR #34840: 向 App Server 添加持久化线程固定功能**
    *   **内容:** 实现线程的 `isPinned` 属性，支持在列表筛选中按固定状态过滤。
    *   **链接:** [PR #34840](https://github.com/openai/codex/pull/34840)
9.  **PR #34839: 保留 MCP 启动中断时的用户输入**
    *   **内容:** 修复在 MCP 工具启动期间中断会话可能导致用户输入丢失的问题。
    *   **链接:** [PR #34839](https://github.com/openai/codex/pull/34839)
10. **PR #34835: 在轮次配置文件中跟踪压缩时间**
    *   **内容:** 将压缩时间作为独立阶段纳入分析事件，更准确地衡量性能瓶颈。
    *   **链接:** [PR #34835](https://github.com/openai/codex/pull/34835)

## 5. 功能需求趋势
从 Issue 和 PR 的分析中，可以观察到以下社区关注趋势：
*   **Windows 平台稳定性优先:** 大量 Issue (#16815, #22428, #30385, #34025, #34782, #34841, #34854) 集中在 Windows 环境的沙箱、路径解析、UI 渲染和启动性能上，表明 Windows 客户端的成熟度是当前社区最大的痛点。
*   **MCP 集成深化:** 社区对 MCP 的支持既有关怀也有焦虑。一方面希望更好地利用 MCP 扩展功能 (#34851, #34849)，另一方面频繁报告进程泄漏和资源管理问题 (#12491, #26984)。
*   **高级工作流控制:** 用户渴望更细粒度的控制，如禁用自动响应 (#28969)、自定义 Worktree 位置 (#10599)、持久化侧边聊天 (#26227) 以及多代理模式的持久化 (#34845)。
*   **跨平台一致性:** 移动端与远程服务器的解耦需求 (#23200) 以及对 TUI 输出截断问题的关注 (#34037)，反映出用户对无缝跨设备体验的高期待。

## 6. 开发者关注点
*   **资源泄漏与性能:** MCP 子进程未回收 (#12491) 和文件描述符泄漏 (#26984) 是资深用户最担忧的技术债务，直接影响长期运行的稳定性。
*   **Windows 特定 Bug:** 冷启动导致系统卡顿 (#34025)、WSL 路径解析失败 (#16815) 以及 Store 更新后的配置重置 (#32682, #34782) 是 Windows 开发者反馈最密集的问题领域。
*   **可配置性与透明度:** 用户希望了解并控制底层行为，例如配置自动解决超时 (#28969)、查看压缩耗时 (#34835) 以及调整计划模式下的权限 (#32594)。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI 社区动态日报
**日期**: 2026-07-23
**数据来源**: github.com/google-gemini/gemini-cli

## 1. 今日速览
今日 Gemini CLI 发布了 `v0.53.0-preview.0` 和 `v0.52.0` 两个版本，重点修复了 A2A 协议中的 400 Bad Request 错误及工作区信任安全漏洞。社区高度关注 Agent 子代理（Subagent）的恢复机制、浏览器代理在 Wayland 下的崩溃问题以及 Auto Memory 系统的日志隐私与稳定性缺陷。

## 2. 版本发布

### v0.53.0-preview.0 (最新)
*   **核心修复**: 解决了 A2A 协议中取消的工具响应分组问题，合并连续角色以避免触发 400 Bad Request 错误。
*   **新功能**: 引入了 LLM 分诊编排器（LLM triage orchestrator）及容器构建功能，旨在优化内部维护流程。
*   [查看完整更新](https://github.com/google-gemini/gemini-cli/pull/28407)

### v0.52.0
*   **重构**: 排除瞬态 CI 配置文件，优化工作区上下文管理。
*   **基础设施**: 添加了分诊工作器的核心基础模块。
*   [查看完整更新](https://github.com/google-gemini/gemini-cli/releases/tag/v0.52.0)

### v0.52.0-nightly.20260722.gc776c665b
*   **安全修复**: 强制实施工作区信任和任务隔离，防止 A2A 服务器出现远程代码执行（RCE）风险。
*   [查看完整更新](https://github.com/google-gemini/gemini-cli/pull/28470)

## 3. 社区热点 Issues

1.  **[Bug] 子代理达到最大轮次后错误报告成功 (#22323)**
    *   **重要性**: `codebase_investigator` 在因达到最大轮次而中断时，仍返回 `GOAL` 成功状态，误导用户认为任务已完成。
    *   **反应**: 12条评论，2个点赞，P1 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/22323)

2.  **[Bug] 通用代理永久挂起 (#21409)**
    *   **重要性**: 当 CLI 委托给通用代理（generalist agent）时，简单操作（如创建文件夹）会导致无限挂起，严重影响用户体验。
    *   **反应**: 8条评论，8个点赞，P1 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/21409)

3.  **[Bug] Shell 命令执行完成后卡住 (#25166)**
    *   **重要性**: 执行简单的 CLI 命令后，终端显示“等待输入”，但命令实际已结束，导致后续交互阻塞。
    *   **反应**: 4条评论，3个点赞，P2 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/25166)

4.  **[Bug] Browser Agent 在 Wayland 下失败 (#21983)**
    *   **重要性**: 在 Wayland 显示服务器上，浏览器子代理无法正常工作，限制了 Linux 用户的使用场景。
    *   **反应**: 4条评论，1个点赞，P1 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/21983)

5.  **[Feature] AST 感知文件读取与搜索的价值评估 (#22745)**
    *   **重要性**: 探讨通过 AST 感知工具减少上下文噪音、提高代码导航精度的可行性，可能带来重大性能提升。
    *   **反应**: 7条评论，P2 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/22745)

6.  **[Bug] Auto Memory 无限重试低信号会话 (#26522)**
    *   **重要性**: 自动记忆系统若判断会话为低信号但未处理，会无限期重复尝试，造成资源浪费。
    *   **反应**: 5条评论，P2 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/26522)

7.  **[Bug] Gemini 未充分利用技能和子代理 (#21968)**
    *   **重要性**: 用户反馈即使有相关技能描述，模型也很少主动调用自定义技能或子代理，需依赖显式指令。
    *   **反应**: 6条评论，P2 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/21968)

8.  **[Security] 确定性的数据脱敏与 Auto Memory 日志减少 (#26525)**
    *   **重要性**: 当前 Auto Memory 在将转录内容发送给模型前缺乏严格的确定性脱敏，存在隐私泄露风险。
    *   **反应**: 3条评论，P2 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/26525)

9.  **[Bug] 超过 128 个工具时出现 400 错误 (#24246)**
    *   **重要性**: 当可用工具数量较多时，CLI 会因 API 限制报错，需优化工具范围限制逻辑。
    *   **反应**: 3条评论，P2 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/24246)

10. **[Bug] 浏览器代理忽略 settings.json 覆盖配置 (#22267)**
    *   **重要性**: 用户在配置文件中设置的参数（如 `maxTurns`）被浏览器代理完全忽略，导致配置失效。
    *   **反应**: 3条评论，P2 优先级。
    *   [链接](https://github.com/google-gemini/gemini-cli/issues/22267)

## 4. 重要 PR 进展

1.  **PR #28509: 过滤历史中的思考部分 (Thought Parts)**
    *   **内容**: 当禁用上下文管理时，从 `getHistoryTurns` 中完全过滤掉 `thought: true` 的部分，防止思维链泄漏导致重复推理块。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28509)

2.  **PR #28469: 模型回退时轮换 Session ID**
    *   **内容**: 修复了在永久回退到 `gemini-2.5-flash` 时，因状态保持导致的 `[API Error: Please submit a new query...]` 错误。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28469)

3.  **PR #28485: 向所有用户公开 gemini-3.5-flash 模型选择器**
    *   **内容**: 修复了 v0.51.0+ 版本中 `buildAvailableModels` 函数未能正确暴露 `gemini-3.5-flash` 的问题。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28485)

4.  **PR #28446: 使用原生 Fetch 进行 OAuth 令牌交换**
    *   **内容**: 解决在无头 VPS 上登录时出现的 `Premature close` 错误，改用原生 fetch 替代旧版 HTTP 客户端。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28446)

5.  **PR #28506: 修复 /compress 命令的 AbortSignal 传播**
    *   **内容**: 为压缩聊天命令添加 `AbortController`，允许用户通过取消操作终止后台压缩请求，防止悬空网络请求。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28506)

6.  **PR #28499: 限制核心工具通配符 DENY 规则**
    *   **内容**: 引入 `excludeMcp` 属性，确保通配符拒绝规则仅适用于内置核心工具，避免误拒 MCP 工具。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28499)

7.  **PR #28510: 版本升级至 0.54.0-nightly**
    *   **内容**: 自动化版本 bump，为下一个夜间构建版本做准备。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28510)

8.  **PR #28447: 添加 Windows PowerShell 故障排除文档**
    *   **内容**: 针对 Windows 用户在 npm 全局安装后 `gemini` 命令无法运行的问题，补充了具体的 PowerShell 解决方案。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28447)

9.  **PR #28431: 配置 SSR 代码生成管道的云基础设施**
    *   **内容**: 建立了 Cloud Run Job、Eventarc 触发的 Cloud Workflow 等容器化运行时环境，用于支持新的代码生成流水线。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28431)

10. **PR #28169: 添加评估覆盖率报告命令 (eval:coverage)**
    *   **内容**: 新增 `npm run eval:coverage` 命令，通过交叉引用工具注册表报告内置工具的评估覆盖情况。
    *   [链接](https://github.com/google-gemini/gemini-cli/pull/28169)

## 5. 功能需求趋势

*   **Agent 鲁棒性与恢复**: 社区强烈希望改进子代理（Subagent）在超时、崩溃或会话锁定后的自动恢复能力（如 Issue #22323, #22232）。
*   **安全性与隐私强化**: 对 RCE 防护、Auto Memory 的数据脱敏以及 OAuth 连接稳定性的高度关注，表明安全是当前的首要议题。
*   **平台兼容性**: 针对 Wayland 显示服务器、Windows PowerShell 环境以及外部编辑器（如 Vim/Nano）退出后的终端渲染问题的修复需求频繁出现。
*   **性能优化**: 探索 AST 感知工具以减少 Token 消耗和提高代码理解精度，以及优化大量工具加载时的性能瓶颈。

## 6. 开发者关注点

*   **Agent 行为不可预测**: 开发者抱怨模型有时不遵守配置（如忽略 `settings.json`），或者在不该使用时启用子代理，且缺乏足够的透明度来调试这些行为。
*   **交互阻塞**: 多个 Issue 报告了“假死”现象，包括 Shell 命令挂起、通用代理无限循环、浏览器代理锁死等，严重影响了开发工作流的连续性。
*   **配置复杂性**: 随着功能增多（如 Auto Memory, Skills, Subagents），配置文件的复杂度和潜在冲突点也在增加，用户需要更清晰的文档和更稳健的默认行为。

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI 社区动态日报
**日期：** 2026-07-23

## 1. 今日速览
GitHub Copilot CLI 发布 v1.0.74-3 系列补丁版本，重点修复了会话隔离、交互快捷键及新增 Gemini-3.6-flash 模型支持。社区反馈集中在 Windows 平台稳定性（进程僵尸、崩溃）以及多代理（Agent）协作中的计费与状态同步问题上，部分高频 Bug 出现回归迹象。

## 2. 版本发布
**v1.0.74-3 (及 -2, -1)**
*   **新增功能：** 首次启动时显示沙箱选择提示；添加对 `gemini-3.6-flash` 模型的支持。
*   **改进项：** 修复了多路复用会话中的上下文泄漏问题，确保会话切换时选择器正确重置；优化 `$` 交互式 Shell 快捷行为。
*   **其他：** 包含常规修复与变更。

## 3. 社区热点 Issues
以下 Issue 因评论活跃度高或影响面广而备受关注：

1.  **[CLOSED] MCP 服务器连接失败 (#2282)**
    *   **重要性：** 涉及 MCP 协议集成核心功能，影响 Windows WSL 环境用户。
    *   **社区反应：** 11 条评论，1 个点赞。用户反馈配置后无法连接 `github-mcp-server`。
2.  **[OPEN] 内置 PDF 阅读支持 (#443)**
    *   **重要性：** 填补 CLI 处理非文本文档的能力空白，提升学术研究和技术文档处理能力。
    *   **社区反应：** 6 条评论，**33 个点赞**。高需求功能，用户希望原生支持而非依赖外部工具。
3.  **[OPEN] BYOK 认证在 --acp 模式下被拒绝 (#4016)**
    *   **重要性：** 这是一个回归 Bug，导致自定义提供商配置在非交互模式下失效，阻碍企业级集成。
    *   **社区反应：** 5 条评论，4 个点赞。作者指出该问题在 v1.0.61-1.0.68 期间曾声称修复但再次出现。
4.  **[OPEN] Linux 下子进程未回收导致僵尸进程 (#4163)**
    *   **重要性：** 长期运行会导致资源泄漏，影响系统稳定性。
    *   **社区反应：** 3 条评论，2 个点赞。观察到每分钟产生约 2 个僵尸进程。
5.  **[OPEN] 可配置的自动压缩阈值 (#1688)**
    *   **重要性：** 针对大上下文窗口模型（如 Claude Opus 4.6），用户希望更精细地控制上下文管理以平衡性能与延迟。
    *   **社区反应：** 2 条评论，5 个点赞。
6.  **[OPEN] 切换回自动驾驶模式后 task_complete 工具不可用 (#4161)**
    *   **重要性：** 功能回归，破坏了工作流连续性。
    *   **社区反应：** 2 条评论，1 个点赞。
7.  **[OPEN] Auto-compaction 未能防止 CAPI 5MB 限制失败 (#4183)**
    *   **重要性：** 揭示了自动压缩机制在处理大量 Tool History 时的局限性，可能导致请求体过大报错。
    *   **社区反应：** 2 条评论，**7 个点赞**。
8.  **[CLOSED] Alpine Linux 自动更新包架构错误 (#3696)**
    *   **重要性：** 导致 musl 系统运行时崩溃，影响容器化部署体验。
    *   **社区反应：** 1 条评论，1 个点赞。
9.  **[OPEN] 终端滚动与 OSC 133 序列支持 (#3428)**
    *   **重要性：** 改善长对话后的用户体验，方便快速定位历史输入和最终答案。
    *   **社区反应：** 1 条评论，0 个点赞。
10. **[OPEN] Xcode ACP 自定义 Agent 响应失败 (#4227)**
    *   **重要性：** 影响 IDE 深度集成场景，`session/prompt` 始终返回错误。
    *   **社区反应：** 新建 Issue，0 评论。

## 4. 重要 PR 进展
*   **#3163 [ViewSonic monitor]**
    *   **状态：** Open
    *   **摘要：** 关联 issue #2591, #3561, #3559。提及初始化 GitHub Action runners。
    *   **备注：** 此 PR 内容较为模糊，可能为误提交或非核心维护内容，暂无实质性代码贡献描述。

*(注：过去 24 小时内无其他显著的功能性 PR 合并或重大开发进展，社区主要聚焦于 Issue 讨论。)*

## 5. 功能需求趋势
从今日 Issues 中提炼出以下核心需求方向：
1.  **多代理（Multi-Agent）协作增强：** 用户强烈要求改进 Agent 间的通信、显式调用机制（#4208）、计费透明度（#4207, #4224）以及状态同步（#4225）。
2.  **上下文与性能优化：** 需要更智能的上下文压缩策略（#1688, #4183），特别是针对长会话和大量 Tool 调用的场景。
3.  **平台兼容性与稳定性：** Windows 平台的崩溃（#4219, #4217）、渲染冻结（#4222）以及 Linux 下的进程管理（#4163）是当前的痛点。
4.  **IDE 与终端集成：** 期望更好的 tmux 支持（#4212, #4223）、Xcode 集成（#4227）以及终端交互体验优化（#3428）。

## 6. 开发者关注点
*   **Windows 平台稳定性危机：** 多个独立 Issue（#4165, #4219, #4217, #4222）指向 Windows 环境的严重缺陷，包括启动挂起、通知崩溃、退出时 Fatal Error 以及 React 渲染循环导致的界面冻结。这表明 Windows 客户端可能在最新版本的回归测试中存在遗漏。
*   **计费与遥测准确性：** 开发者关注子代理调用中的计费属性缺失（#4224）以及 `/usage` 命令未能准确反映实际消耗的 Token 或成本，这对企业成本管控至关重要。
*   **MCP 与自定义 Provider 集成：** 尽管有新增模型支持，但现有的 BYOK（自带密钥）和 ACP（Agent Client Protocol）集成仍存在认证和握手阻塞问题（#4016, #4206），阻碍了高级用例的落地。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI 社区动态日报
**日期：** 2026-07-23
**数据来源：** github.com/MoonshotAI/kimi-cli

## 1. 今日速览
今日 Kimi Code CLI 社区活跃度较高，主要聚焦于第三方 API 兼容性修复及 Windows 环境下的启动稳定性问题。开发者提交了一项关键 PR 以解决 `prompt_cache_key` 导致的 400 验证错误，同时社区反馈了关于子代理模型独立配置的功能需求，反映出多智能体工作流优化的迫切性。

## 2. 版本发布
**无新版本发布。**
过去 24 小时内未检测到新的 Release 版本。当前社区讨论集中在现有版本的 Bug 修复与新功能提议上。

## 3. 社区热点 Issues
以下 Issues 反映了近期用户遇到的主要技术障碍与功能期待：

*   **#2534 [bug] Model API error 400 Validation: Unsupported parameter(s): `prompt_cache_key`**
    *   **重要性：** 高。影响使用 Nvidia NIM 等第三方兼容接口的用户，导致工具无法正常工作。
    *   **社区反应：** 已关联 PR #2535 进行修复。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/issues/2534)

*   **#2533 Feature Request: Per-agent model selection for sub-agents**
    *   **重要性：** 中高。旨在优化多智能体工作流的成本与性能平衡，允许为子任务分配不同层级的模型。
    *   **社区反应：** 提出者详细阐述了“低成本任务用廉价模型”的场景，符合高阶用户痛点。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/issues/2533)

*   **#2532 kimi web crashes at startup on Windows when stdout is redirected**
    *   **重要性：** 中。涉及 Windows 中文环境下的 Unicode 编码问题，影响自动化脚本集成及 IDE 插件调用。
    *   **社区反应：** 描述了具体的 `gbk` 编码错误场景，是本地化兼容性的典型缺陷。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/issues/2532)

*   **#2531 MCP tool names & schemas rejected by Moonshot API (HTTP 400)**
    *   **重要性：** 中。MCP（Model Context Protocol）集成中的 Schema 验证失败，阻碍了部分高级工具链的接入。
    *   **社区反应：** 建议客户端在发送前进行 sanitize 处理，技术细节清晰。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/issues/2531)

*   **#2318 [bug] request reached organization TPD rate limit, current: 1505241**
    *   **重要性：** 低（历史遗留）。虽然显示为 Open，但创建于 5 月，更新于 7 月 22 日，可能涉及特定的组织配额计算逻辑争议。
    *   **社区反应：** 仅有少量评论，关注度较低。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/issues/2318)

*(注：由于提供的数据仅包含 5 条 Issue，以上列出了全部相关 Issue)*

## 4. 重要 PR 进展
以下 PR 解决了关键的技术缺陷，提升了工具的稳定性与兼容性：

*   **#2535 fix(llm): scope prompt cache keys to Moonshot APIs**
    *   **内容：** 修复了第三方 Kimi 兼容端点因接收不支持的 `prompt_cache_key` 参数而报错的问题。官方 API 保留会话缓存，第三方则移除该参数。
    *   **状态：** 已创建，关联 Issue #2534。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/pull/2535)

*   **#2524 fix(tools): count StrReplaceFile replacements against the running content**
    *   **内容：** 修正了 `StrReplaceFile` 工具在链式编辑时的计数逻辑。之前基于原始文件内容计算，导致后续编辑因找不到旧字符串而失败或计数错误。
    *   **状态：** 已更新，关联 Issue #2526。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/pull/2524)

*   **#2530 fix(shell): stop blocking until timeout when a detached child holds the pipes**
    *   **内容：** 解决了前台 Shell 命令中，当分离的子进程持有管道时导致的无限阻塞问题。改进了退出码检查机制，提升了长运行命令或后台守护进程的兼容性。
    *   **状态：** 已更新，关联 Issue #2468。
    *   [链接](https://github.com/MoonshotAI/kimi-cli/pull/2530)

*(注：由于提供的数据仅包含 3 条 PR，以上列出了全部相关 PR)*

## 5. 功能需求趋势
从社区反馈中提取的核心趋势如下：

1.  **多智能体工作流精细化控制：** 用户强烈希望获得对子代理（Sub-agents）的更细粒度控制，特别是**按代理独立选择模型**的能力，以实现成本效益最优的任务分发。
2.  **第三方 API 兼容性增强：** 随着更多开发者使用非 Moonshot 官方的兼容接口（如 Nvidia NIM），社区对**参数过滤**和**Schema 校验**的容错能力提出了更高要求。
3.  **本地环境与集成稳定性：** Windows 平台的编码问题以及 Shell 命令执行的阻塞问题，显示出在**跨平台一致性**和**进程管理**方面仍有优化空间。

## 6. 开发者关注点
开发者当前最关注的痛点包括：

*   **API 协议差异处理：** 如何优雅地处理不同后端提供商（Provider）之间的参数差异（如 `prompt_cache_key` 和 JSON Schema 格式），避免客户端发送无效请求。
*   **文件编辑准确性：** 在复杂的代码重构场景中，确保替换操作（Replace）基于最新文件状态而非初始状态，防止级联错误。
*   **自动化集成体验：** 解决在 CI/CD 或 IDE 插件中通过管道重定向输出时出现的崩溃问题，提升 CLI 作为底层引擎的健壮性。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode 社区动态日报
**日期：** 2026-07-23
**数据来源：** github.com/anomalyco/opencode

## 1. 今日速览
今日 OpenCode 社区活跃度较高，核心焦点集中在 **V2 架构的稳定性修复**（特别是位置启动失败缓存和长期运行的内存/CPU泄漏问题）以及 **订阅服务上游阻断** 的高频报错。同时，开发者对 V2 主题迁移、文档完善及桌面端 UI 交互优化提交了多项 PR 和 Issue，显示出 V2 版本正在加速迭代并接近成熟可用状态。

## 2. 版本发布
*   **无重大新版本发布**。
*   近期动态主要围绕 `v2` 分支的代码重构与 Bug 修复，以及针对现有稳定版（如 1.18.x）的补丁更新。

## 3. 社区热点 Issues
以下 10 个 Issue 因涉及核心功能故障、性能瓶颈或高关注度而值得关注：

1.  **[BUG] 订阅模型请求被上游提供商拦截 (#38218)**
    *   **重要性：** 影响所有 opencode-go 订阅用户的聊天/补全功能，报错“Request blocked by upstream provider”。
    *   **反应：** 22条评论，5个👍，社区急需官方排查或临时解决方案。
2.  **[PERF] V2 服务器长期运行进入持续分配循环 (#36677)**
    *   **重要性：** 导致 CPU 满载（~1核）且 RSS 占用高达 1.1-1.3GB，严重影响生产环境稳定性。
    *   **反应：** 由官方机器人标记，需核心团队介入。
3.  **[BUG] 大型项目目录下 LLM 调用失败 (#38415)**
    *   **重要性：** 在 WSL2/Linux 的大项目中启动即失效，重启目录可恢复，暗示存在上下文加载或资源限制问题。
    *   **反应：** 新发 Issue，尚未有回复。
4.  **[BUG] 桌面端对话框异常卡顿 (#38412)**
    *   **重要性：** 影响用户体验的核心交互流畅度，标签含 `needs:compliance`。
    *   **反应：** 新发 Issue。
5.  **[BUG] 新建会话按钮失效且跨设备不同步 (#38411)**
    *   **重要性：** Web UI 基本功能故障，且涉及数据同步逻辑错误。
    *   **反应：** 新发 Issue。
6.  **[BUG] LM Studio 自动发现模型不完整 (#18011)**
    *   **重要性：** 本地开发常用工具 LM Studio 集成存在缺陷，仅显示部分模型。
    *   **反应：** 长期未决，6条评论，4个👍。
7.  **[BUG] V2 位置启动失败被缓存 60 分钟无法恢复 (#38405)**
    *   **重要性：** 导致间歇性故障（如插件临时崩溃）引发长时间服务不可用。
    *   **反应：** 已有对应 PR 跟进（见下文）。
8.  **[BUG] 全局工具 Globs 未排除 MCP 工具 (#37675)**
    *   **重要性：** 配置策略失效，MCP 工具仍被发送给 Provider，可能导致意外行为或成本增加。
    *   **反应：** 1条评论，1个👍。
9.  **[BUG] 所有工具返回 SQL 列不存在错误 (#38399, #38400)**
    *   **重要性：** Bash/Grep 等基础工具完全不可用，用户报告重复，疑似数据库 schema 版本冲突。
    *   **反应：** 两个重复 Issue，均被快速关闭（可能已解决或标记为重复）。
10. **[FEATURE] Plan/Build 模式行为不一致 (#37970)**
    *   **重要性：** 高级用户依赖的模式切换逻辑在最新版中表现不稳定。
    *   **反应：** 10条评论，1个👍。

## 4. 重要 PR 进展
以下 10 个 PR 对代码库稳定性和功能完善有显著贡献：

1.  **[FIX] 修复 pr-standards 误报 v2 分支 PR 缺少关联 Issue (#38408)**
    *   **内容：** 修正 GitHub Action 逻辑，解决因 GraphQL API 限制导致的 CI 误报。
    *   **作者：** dondetir | **链接：** [PR #38408](https://github.com/anomalyco/opencode/pull/38408)
2.  **[FIX] V2 位置启动失败不再缓存，改为重试 (#38406)**
    *   **内容：** 解决 Issue #38405，避免临时故障导致长达 60 分钟的服务不可用。
    *   **作者：** dondetir | **链接：** [PR #38406](https://github.com/anomalyco/opencode/pull/38406)
3.  **[REFACTOR] TUI 语法风格直接从 V2 主题生成 (#38397)**
    *   **内容：** 统一 V1/V2 主题渲染逻辑，移除冗余解析，保留兼容性。
    *   **作者：** jlongster | **链接：** [PR #38397](https://github.com/anomalyco/opencode/pull/38397)
4.  **[FIX] 核心：迁移命名代理颜色 (#38414)**
    *   **内容：** 确保 V1 配置中的代理颜色在 V2 验证前正确迁移，保持视觉一致性。
    *   **作者：** jlongster | **链接：** [PR #38414](https://github.com/anomalyco/opencode/pull/38414)
5.  **[FIX] 核心：为生成加载动态模型 (#38401)**
    *   **内容：** 修复 `/api/generate` 端点在使用动态加载 AI SDK（如 Gemini）时的“Unsupported package”错误。
    *   **作者：** kitlangton | **链接：** [PR #38401](https://github.com/anomalyco/opencode/pull/38401)
6.  **[DOCS] 提及 Exa 和 Parallel 作为网页搜索后端 (#38395)**
    *   **内容：** 更新文档，纠正仅提及 Exa 的错误，补充 Parallel 支持及启用标志。
    *   **作者：** dondetir | **链接：** [PR #38395](https://github.com/anomalyco/opencode/pull/38395)
7.  **[FIX] 标准化 Tooltip 延迟 (#38403)**
    *   **内容：** 将全局 Tooltip 悬停延迟统一为 400ms，提升 UI 交互一致性。
    *   **作者：** opencode-agent[bot] | **链接：** [PR #38403](https://github.com/anomalyco/opencode/pull/38403)
8.  **[FEAT] 添加印尼语 README 翻译 (#38033)**
    *   **内容：** 国际化进展，新增印尼语文档以提升可访问性。
    *   **作者：** ideapedyudi | **链接：** [PR #38033](https://github.com/anomalyco/opencode/pull/38033)
9.  **[DOCS] 添加 opencode-hypa 插件到生态列表 (#38022)**
    *   **内容：** 扩展社区插件生态展示。
    *   **作者：** kipyin | **链接：** [PR #38022](https://github.com/anomalyco/opencode/pull/38022)
10. **[FEAT] 每个代理的子代理深度覆盖 (#37226)**
    *   **内容：** 允许在特定代理配置中设置 `subagent_depth`，提供比全局配置更细粒度的控制。
    *   **作者：** M4buAO | **链接：** [PR #37226](https://github.com/anomalyco/opencode/pull/37226)

## 5. 功能需求趋势
从 Issue 和 PR 中可以提炼出以下社区关注方向：
*   **V2 稳定性与性能：** 大量 Issue 和 PR 集中在 V2 分支的资源泄漏、启动失败缓存机制以及主题渲染性能上，表明 V2 正在经历关键的稳定性打磨期。
*   **UI/UX 交互优化：** 用户反馈桌面端卡顿、Web 端新建会话失效、左侧导航栏折叠等功能需求，反映出对现代化 IDE 体验的强烈期待（如 Tab 支持、侧边栏导航）。
*   **本地开发与 MCP 集成：** 对 LM Studio 模型发现不全、MCP 工具过滤配置失效的反馈，说明本地 LLM 集成和 MCP 生态支持是高频痛点。
*   **文档准确性：** 多次出现文档与实际功能不符（如搜索后端、Plan/Build 模式），社区呼吁维护者及时同步文档。

## 6. 开发者关注点
*   **订阅服务可靠性：** `opencode-go` 订阅用户普遍遭遇上游阻断错误，这是当前最紧急的生产环境问题。
*   **大项目性能瓶颈：** 在大型仓库或 WSL2 环境中启动 OpenCode 时出现的 LLM 无响应或卡顿，提示可能存在文件监听或上下文加载的性能极限。
*   **V2 迁移兼容性：** 随着 V2 深入，用户关注旧配置（如颜色、主题、权限映射）在新架构下的兼容性和平滑过渡。
*   **静默执行需求：** Windows 用户提出 PowerShell 窗口后台静默执行（`-WindowStyle Hidden`）的需求，以改善终端体验。

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi 社区动态日报
**日期：** 2026-07-23
**数据来源：** github.com/badlogic/pi-mono

## 1. 今日速览
过去24小时 Pi 社区活跃度极高，共更新 32 个 Issues 和 29 个 Pull Requests，但无新版本发布。核心焦点集中在 **AI 提供商兼容性修复**（特别是 Bedrock 自适应思维支持、OpenAI/Anthropic 重试机制优化）以及 **TUI 体验与性能优化**（终端渲染对齐、临时文件管理、启动基准测试修复）。此外，开发者对 OAuth 认证流程、扩展系统稳定性及成本计费透明度的反馈显著增加。

## 2. 版本发布
*   **无新版本发布。**

## 3. 社区热点 Issues
以下 Issue 因涉及核心功能缺陷、重大用户体验问题或高社区关注度而被选中：

1.  **#6768 [OPEN] Compaction using Copilot Enterprise not possible**
    *   **重要性：** 阻碍了使用 Copilot Enterprise 许可证的用户进行上下文压缩，直接影响长对话处理能力。
    *   **社区反应：** 8 条评论，8 个 👍，表明许多企业用户受此困扰。
    *   [链接](https://github.com/earendil-works/pi/issues/6768)

2.  **#6911 [CLOSED] OpenAI SDK retries sleep full Retry-After (days) and Escape cannot abort**
    *   **重要性：** 揭示了底层 SDK 重试机制的严重缺陷（无限期休眠且无法中断），导致 TUI 假死。
    *   **社区反应：** 5 条评论，已被标记为关闭，预计有对应 PR 修复。
    *   [链接](https://github.com/earendil-works/pi/issues/6911)

3.  **#6686 [CLOSED] Pi automatically logs out of GitHub**
    *   **重要性：** 认证会话意外失效，影响依赖 GitHub 集成（如 Copilot）的用户体验。
    *   **社区反应：** 10 条评论，讨论热烈，涉及多平台复现。
    *   [链接](https://github.com/earendil-works/pi/issues/6686)

4.  **#6978 [CLOSED] Interactive TUI: concurrent extension dialogs hang**
    *   **重要性：** 扩展并发交互导致的 Promise 悬空问题，会导致会话卡死在 "Working..." 状态。
    *   **社区反应：** 1 条评论，但属于关键稳定性 Bug。
    *   [链接](https://github.com/earendil-works/pi/issues/6978)

5.  **#6924 [OPEN] pi: --no-session leaves temp session directories behind**
    *   **重要性：** 资源泄漏问题，特别是在自动化测试脚本中运行 `pi` 时会产生大量垃圾文件。
    *   **社区反应：** 2 条评论，开发者关注点。
    *   [链接](https://github.com/earendil-works/pi/issues/6924)

6.  **#6979 [CLOSED] OAuth-authenticated Anthropic requests get billed as metered API usage**
    *   **重要性：** 计费逻辑错误，OAuth 用户可能被错误收取按量付费费用而非订阅费用，涉及金钱利益。
    *   **社区反应：** 1 条评论，需紧急澄清或修复。
    *   [链接](https://github.com/earendil-works/pi/issues/6979)

7.  **#6210 [OPEN] /scoped-models cannot select model ids containing brackets**
    *   **重要性：** 正则表达式解析缺陷，限制了自定义模型 ID 的灵活性。
    *   **社区反应：** 8 条评论，技术细节讨论较多。
    *   [链接](https://github.com/earendil-works/pi/issues/6210)

8.  **#6774 [CLOSED] Ctrl+G external editor is slow to launch when os.tmpdir() is crowded**
    *   **重要性：** 外部编辑器启动性能问题，源于对全局临时目录的依赖。
    *   **社区反应：** 7 条评论，提出了使用私有临时目录的解决方案。
    *   [链接](https://github.com/earendil-works/pi/issues/6774)

9.  **#6970 [CLOSED] pi's integration with GitHub Copilot Plugin instead of OAuth causes token invalidation**
    *   **重要性：** 解释了 #6686 的部分原因，指出了 Copilot LSP 集成与 OAuth 之间的冲突。
    *   **社区反应：** 1 条评论，关联多个设备同步问题。
    *   [链接](https://github.com/earendil-works/pi/issues/6970)

10. **#6968 [CLOSED] Installing an extension ... collapses all installed skill/prompt/theme source scopes**
    *   **重要性：** 扩展安装导致的元数据损坏，影响自动补全和包管理准确性。
    *   **社区反应：** 1 条评论，属于内部状态管理 Bug。
    *   [链接](https://github.com/earendil-works/pi/issues/6968)

## 4. 重要 PR 进展
以下 PR 解决了上述关键问题或引入了新功能：

1.  **#6980 [OPEN] fix(ai): make provider retries abortable**
    *   **内容：** 修复 #6911。替换 Anthropic/OpenAI SDK 的内部重试逻辑，支持 `AbortSignal` 中断，并限制最大重试延迟。
    *   **状态：** Open
    *   [链接](https://github.com/earendil-works/pi/pull/6980)

2.  **#6984 [CLOSED] feat(ai): honor compat.forceAdaptiveThinking in bedrock-converse-stream**
    *   **内容：** 修复 Bedrock 提供商对自适应思维（Adaptive Thinking）的支持，解决 `ValidationException` 错误。
    *   **状态：** Closed
    *   [链接](https://github.com/earendil-works/pi/pull/6984)

3.  **#6341 [OPEN] feat(ai): support constrained sampling**
    *   **内容：** 引入 `constrainedSampling` 配置，允许工具请求提供商端对工具输入进行 JSON-schema 约束采样，提升结构化输出稳定性。
    *   **状态：** Open
    *   [链接](https://github.com/earendil-works/pi/pull/6341)

4.  **#6903 [CLOSED] fix(coding-agent): speed up external editor launch**
    *   **内容：** 修复 #6774。将外部编辑器提示写入私有临时子目录而非全局 `/tmp`，显著提升启动速度。
    *   **状态：** Closed
    *   [链接](https://github.com/earendil-works/pi/pull/6903)

5.  **#6987 [OPEN] fix(tui): align grapheme widths with terminal cells**
    *   **内容：** 解决 TUI 中字符宽度计算不准导致的渲染错位问题，提升终端显示一致性。
    *   **状态：** Open
    *   [链接](https://github.com/earendil-works/pi/pull/6987)

6.  **#6976 [CLOSED] fix(coding-agent): preserve TTY in startup benchmark**
    *   **内容：** 修复 #6975。确保 TUI 启动基准测试保留 TTY，使测试能正确进入交互模式。
    *   **状态：** Closed
    *   [链接](https://github.com/earendil-works/pi/pull/6976)

7.  **#6927 [CLOSED] Add native OpenRouter OAuth support**
    *   **内容：** 新增 OpenRouter 的原生 OAuth 支持，包括 PKCE S256 流程和本地回调验证。
    *   **状态：** Closed
    *   [链接](https://github.com/earendil-works/pi/pull/6927)

8.  **#6967 [CLOSED] feat(coding-agent): expose session metadata to bash tools**
    *   **内容：** 向 Bash 工具暴露会话元数据（Session ID, Provider, Model 等），便于子进程识别上下文。
    *   **状态：** Closed
    *   [链接](https://github.com/earendil-works/pi/pull/6967)

9.  **#6960 [CLOSED] feat(ai): add StepFun providers**
    *   **内容：** 新增四个 StepFun 原生提供商支持（中国区、全球区、预付费路由等）。
    *   **状态：** Closed
    *   [链接](https://github.com/earendil-works/pi/pull/6960)

10. **#6958 [CLOSED] write tui debug/crash logs into the configured pi agent dir**
    *   **内容：** 修复 #6652。将 TUI 崩溃日志写入配置的 `PI_CODING_AGENT_DIR`，避免硬编码路径导致的问题。
    *   **状态：** Closed
    *   [链接](https://github.com/earendil-works/pi/pull/6958)

## 5. 功能需求趋势
从 Issues 和 PRs 中提炼出以下社区关注方向：
*   **提供商兼容性与高级特性：** 社区强烈要求完善对 AWS Bedrock（自适应思维）、OpenRouter（OAuth）、StepFun 等新提供商的支持，以及对 Copilot Enterprise 等企业级功能的兼容性。
*   **可观测性与成本透明：** 用户关注计费准确性（OAuth vs API Key 计费差异）和运行时指标暴露（PR #6881 提出使用提供商报告的成本）。
*   **TUI 交互与性能：** 对终端渲染精度（字宽对齐）、快捷键响应、外部编辑器启动速度以及并发对话框处理的优化需求持续存在。
*   **扩展生态稳定性：** 扩展系统的元数据完整性、会话隔离性以及 API 规范（如结构化审批请求）是开发者关注的重点。

## 6. 开发者关注点
*   **认证与令牌管理：** GitHub 登出、Copilot 插件冲突、OAuth 流程的健壮性是近期高频痛点。
*   **SDK 行为不可控：** OpenAI/Anthropic SDK 的重试策略（无限休眠、忽略 AbortSignal）直接影响了 Pi 的控制权，开发者迫切希望 Pi 层能接管或屏蔽这些不良行为。
*   **资源泄漏与清理：** 临时目录残留（#6924）、会话目录未清理等问题在自动化场景和长时间运行中尤为突出。
*   **跨平台一致性：** Windows 下的终端键位映射（Kitty/VT-input）、路径分隔符、npm 包依赖标签等问题显示出多平台适配仍有差距。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code 社区动态日报
**日期：** 2026-07-23
**数据来源：** github.com/QwenLM/qwen-code

## 1. 今日速览
今日 Qwen Code 社区活跃度较高，核心焦点集中在 **Agent 状态协议 (Goal v3)** 的引入以及 **CI/CD 稳定性** 的修复。主要 Bug 涉及侧边查询强制禁用 `enable_thinking` 导致 TokenPlan 端点报错，以及 CLI 更新检查因路径解析问题失败。此外，团队正在推进 Web Shell 的 Git 工作流优化和 Daemon 通道的显式交付机制。

## 2. 版本发布
*   **v0.0.0-benchmark-poc.20260722.1**: 这是一个临时预发布版本，主要用于验证 GitHub Actions → ECS 基准测试 worker → GitHub 结果发布的完整链路。**注意：** 这不是正式的产品发布，仅用于内部基准测试 POC 验证。

## 3. 社区热点 Issues
以下 Issue 反映了当前开发中的关键阻塞点和维护需求：

1.  **[CLOSED] #7284: side-query 强制 disable thinking 导致 400 错误**
    *   **重要性：** 高。`web_fetch` 等核心功能依赖侧边查询，若强制关闭 `enable_thinking`，会导致依赖该参数的 TokenPlan 端点返回 400 错误，直接影响部分模型能力的使用。
    *   **链接:** [Issue #7284](https://github.com/QwenLM/qwen-code/issues/7284)

2.  **[OPEN] #7516: Main CI E2E 测试失败**
    *   **重要性：** 中。主分支持续集成失败会阻碍所有 PR 的合并，影响开发效率。
    *   **链接:** [Issue #7516](https://github.com/QwenLM/qwen-code/issues/7516)

3.  **[CLOSED] #7537: Core 测试套件红屏 (fork dispatch test)**
    *   **重要性：** 中。`agent.test.ts` 中的 fork dispatch 测试挂起，导致整个 `test:ci` 失败，波及所有 PR。
    *   **链接:** [Issue #7537](https://github.com/QwenLM/qwen-code/issues/7537)

4.  **[OPEN] #7549: v0.20.1-nightly 发布失败**
    *   **重要性：** 低。夜间构建流程中的 quality 检查失败，需排查自动化脚本问题。
    *   **链接:** [Issue #7549](https://github.com/QwenLM/qwen-code/issues/7549)

5.  **[OPEN] #7543: getNpmCliPath 返回 mise wrapper 导致更新检查失败**
    *   **重要性：** 高。使用 `mise` 作为工具管理器的用户无法通过 `/update` 命令或启动时检查进行更新，属于用户体验阻断性 Bug。
    *   **链接:** [Issue #7543](https://github.com/QwenLM/qwen-code/issues/7543)

6.  **[OPEN] #7167: Fleet Shepherd Dashboard**
    *   **重要性：** 低。自动化维护的 CI 信号看板，用于监控 Fleet Shepherd 工作流的健康状况。
    *   **链接:** [Issue #7167](https://github.com/QwenLM/qwen-code/issues/7167)

7.  *(注：其余 Issue 多为自动化生成的 CI 失败报告或低优先级维护任务，未列入前 10)*

## 4. 重要 PR 进展
以下是过去 24 小时内评论数较多或影响范围较大的 Pull Requests：

1.  **#7388: feat(daemon): add explicit channel delivery**
    *   **内容：** 为 Daemon 通知、Agent prompt 终值和定时任务终值添加显式的 Channel 交付契约，支持按 Workspace 路由到特定 Worker。
    *   **链接:** [PR #7388](https://github.com/QwenLM/qwen-code/pull/7388)

2.  **#7513: ci: matrix ECS runner update + sudo install + repository_dispatch trigger**
    *   **内容：** 修复 ECS Runner 更新工作流中的安装目标错误和权限问题，确保 Runner 能可靠地保持最新状态。
    *   **链接:** [PR #7513](https://github.com/QwenLM/qwen-code/pull/7513)

3.  **#7530: refactor(core): tier prompt fragments by cache stability**
    *   **内容：** 对注入的 Prompt Fragment 进行分层（稳定、上下文、易变），优化缓存策略，提升系统指令渲染效率。
    *   **链接:** [PR #7530](https://github.com/QwenLM/qwen-code/pull/7530)

4.  **#7519: fix(web-shell): suppress stale dist type errors**
    *   **内容：** 通过 `@ts-expect-error` 抑制 web-shell 包中由过时 SDK 类型定义引起的 37 个 TypeScript 编译错误，不改变业务逻辑。
    *   **链接:** [PR #7519](https://github.com/QwenLM/qwen-code/pull/7519)

5.  **#7542: feat(cli): add version upgrade notices**
    *   **内容：** 新增轻量级“What's New”启动提示，展示新版本亮点，提升用户对更新内容的感知。
    *   **链接:** [PR #7542](https://github.com/QwenLM/qwen-code/pull/7542)

6.  **#7186: fix(cli): share one process.stdout resize listener**
    *   **内容：** 优化终端大小监听，复用模块级的 `resize` 监听器，减少内存占用和事件重复触发。
    *   **链接:** [PR #7186](https://github.com/QwenLM/qwen-code/pull/7186)

7.  **#7535: fix(scripts): retry model calls and surface degraded release notes**
    *   **内容：** 增强发布说明生成器的健壮性，增加模型调用重试机制，并在降级运行时暴露警告而非静默成功。
    *   **链接:** [PR #7535](https://github.com/QwenLM/qwen-code/pull/7535)

8.  **#7471: feat(web-shell): add git mode selector**
    *   **内容：** 在 Web Shell 新建会话流程中增加 Git 模式选择器，支持“当前分支”、“新分支”等三种工作流。
    *   **链接:** [PR #7471](https://github.com/QwenLM/qwen-code/pull/7471)

9.  **#7501: fix(cli): open the actual serve fallback port**
    *   **内容：** 修复 Express 监听错误导致的端口回退逻辑缺陷，确保服务器 URL 正确返回。
    *   **链接:** [PR #7501](https://github.com/QwenLM/qwen-code/pull/7501)

10. **#7517: feat(core): add Goal v3 state protocol**
    *   **内容：** 引入版本化的 Goal v3 状态契约，定义了生命周期状态、乐观并发控制及确定性转换，是 Agent 架构演进的关键一步。
    *   **链接:** [PR #7517](https://github.com/QwenLM/qwen-code/pull/7517)

*(其他 PR 如 #7522, #7526, #7527, #7514, #7529, #7531, #7532, #7533, #7534, #7536 均为具体的 Bug 修复或微调，详见原仓库)*

## 5. 功能需求趋势
从本周的 Issue 和 PR 中可观察到以下趋势：
1.  **Agent 状态管理精细化：** Goal v3 协议的引入表明团队正在重构 Agent 的生命周期管理和状态同步机制，追求更强的确定性和并发控制。
2.  **Web Shell 体验增强：** 增加 Git 模式选择和更完善的终端大小监听，显示对交互式编码环境（IDE-like experience）的重视。
3.  **可观测性与 Telemetry：** 对齐 ARMS 的 GenAI 遥测数据（PR #7536），反映了对生产环境监控和数据追踪能力的加强。
4.  **Prompt 工程优化：** 通过分层 Prompt Fragments（PR #7530）来优化缓存和上下文管理，旨在提升响应速度和成本控制。

## 6. 开发者关注点
*   **兼容性痛点：** 多个 Issue 指向与第三方工具（如 `mise`, `npm` wrapper）的兼容性问题，特别是 CLI 更新检查和路径解析。
*   **模型参数灵活性：** 开发者对 `enable_thinking` 等模型参数的传递逻辑非常敏感，任何强制修改都可能导致下游服务（如 TokenPlan）报错。
*   **CI/CD 稳定性：** 频繁的 CI 失败（尤其是 E2E 测试和 Fork 测试）是社区反馈的高频痛点，影响了日常开发的流畅度。
*   **安全性与隐私：** 清理子进程环境变量中的敏感信息（PR #7527）和修复 JSONL 写入空文件问题（PR #7533），显示对底层数据安全和规范性的关注。

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI 社区动态日报
**日期：** 2026-07-23
**数据来源：** github.com/Hmbown/DeepSeek-TUI (注：数据实际指向 CodeWhale 项目)

## 1. 今日速览
v0.9.1 版本进入最终收尾阶段，大量 Issue 和 PR 集中在修复 TUI 工作区（Work Surface）的 UI 细节、统一技能管理器（Skills Manager）以及解决 Kimi 模型集成的路由冲突。同时，v0.9.2 的研发已提前启动，核心聚焦于“上下文瘦身”（Context Diet），旨在通过减少冗余提示词和工具描述来优化 Token 效率和模型响应质量。此外，Windows 安装器存在 PATH 环境变量覆盖的安全隐患被报告。

## 2. 版本发布
*   **v0.9.1 发布候选/收尾中**：无正式 Release 标签更新，但多个标有 `[release-blocker]` 的 Issue 已关闭或正在处理中。
*   **v0.9.2 规划中**：多个关于性能优化和上下文管理的 Issue 已标记为 v0.9.2 目标。

## 3. 社区热点 Issues
以下 Issue 因涉及核心功能修复、重大重构或安全漏洞而备受关注：

1.  **#2870 [OPEN] EPIC: staged command-boundary refactor for #2791**
    *   **重要性**：这是底层命令边界重构的追踪 Epic，涉及复杂的代码清理和 TUI 交互逻辑，评论数最多（17条），显示社区对架构稳定性的关注。
    *   **链接**: [Issue #2870](https://github.com/Hmbown/CodeWhale/issues/2870)

2.  **#4685 [OPEN] CodeWhaleSetup.exe installer overwrites user PATH environment variable on Windows 10**
    *   **重要性**：严重 Bug。Windows 安装程序错误地覆盖了用户 PATH 而非追加，导致其他工具失效，影响用户体验和系统稳定性。
    *   **链接**: [Issue #4685](https://github.com/Hmbown/CodeWhale/issues/4685)

3.  **#4713 [OPEN] v0.9.1 security gate: deep scan and dependency alert disposition**
    *   **重要性**：发布前的安全门禁。存在 17 个 Dependabot 警报（7 高 10 中），需在使用 axios, body-parser 等库前解决，直接影响 v0.9.1 的发布安全性。
    *   **链接**: [Issue #4713](https://github.com/Hmbown/CodeWhale/issues/4713)

4.  **#4691 [CLOSED] v0.9.1: Ship the model-invoked default CodeWhale skill pack**
    *   **重要性**：定义了 v0.9.1 的核心用户体验之一，即提供类似 Kimi Code 和 Claude Code 的一体化技能包，提升开箱即用性。
    *   **链接**: [Issue #4691](https://github.com/Hmbown/CodeWhale/issues/4691)

5.  **#4687 [CLOSED] fix(kimi): fail closed on Kimi Code/direct Moonshot K3 model-ID cross-pairings**
    *   **重要性**：修复了 Kimi/Moonshot 模型集成中的关键路由识别错误，防止因模型 ID 混淆导致的请求失败，确保多模型支持的可靠性。
    *   **链接**: [Issue #4687](https://github.com/Hmbown/CodeWhale/issues/4687)

6.  **#4704 [OPEN] Context diet: minimize every model-facing prompt, schema, and payload**
    *   **重要性**：v0.9.2 的核心战略方向。旨在通过审计和削减非必要的模型可见字节，降低 Token 消耗并提高跨模型兼容性。
    *   **链接**: [Issue #4704](https://github.com/Hmbown/CodeWhale/issues/4704)

7.  **#4686 [OPEN] feat(minimax): add China / Token Plan provider routes for minimaxi.com**
    *   **重要性**：新增对 MiniMax 中国区 API 的支持，扩展了项目的模型生态覆盖范围，满足特定区域用户的需求。
    *   **链接**: [Issue #4686](https://github.com/Hmbown/CodeWhale/issues/4686)

8.  **#2889 [CLOSED] Work Agent rows: real sub-agent details and structured current activity**
    *   **重要性**：改善了侧边栏的工作流展示，使子代理的活动状态更清晰，提升了复杂任务执行时的可观测性。
    *   **链接**: [Issue #2889](https://github.com/Hmbown/CodeWhale/issues/2889)

9.  **#4651 [CLOSED] v0.9.1: Make /skills the single skill manager across project, global, and compatible roots**
    *   **重要性**：统一了技能管理入口 `/skills`，消除了分散的命令体系，简化了用户的技能安装、审计和信任流程。
    *   **链接**: [Issue #4651](https://github.com/Hmbown/CodeWhale/issues/4651)

10. **#4700 [CLOSED] v0.9.1: Replace generic Work chrome with a resizable To-do + Sub-agent bar**
    *   **重要性**：重构了顶部工作区 UI，使其更具可调整性和语义清晰度，解决了普通 Shell 失败与用户任务混淆的问题。
    *   **链接**: [Issue #4700](https://github.com/Hmbown/CodeWhale/issues/4700)

## 4. 重要 PR 进展
以下 PR 展示了 v0.9.1 的最终整合及 v0.9.2 的前期准备：

1.  **#4679 [CLOSED] feat(skills): unified /skills manager with audit and owned mutations**
    *   **内容**：实现了统一的 `/skills` 管理器，支持库存查看、审计、安装/导入、更新、移除和信任，是 v0.9.1 技能体验的核心落地。
    *   **链接**: [PR #4679](https://github.com/Hmbown/CodeWhale/pull/4679)

2.  **#4695 [CLOSED] feat(skills): default CodeWhale skill pack (bundled v5)**
    *   **内容**：发布了包含 interview, plan, implement, debug 等常见开发流程的默认技能包，对标竞品的一体化体验。
    *   **链接**: [PR #4695](https://github.com/Hmbown/CodeWhale/pull/4695)

3.  **#4675 [CLOSED] Integrate CodeWhale v0.9.1 runtime and release surface**
    *   **内容**：将 v0.9.1 运行时简化、空工作区修复及公共发布表面整合到 main 分支，并确定了最终的 TUI 色彩语法。
    *   **链接**: [PR #4675](https://github.com/Hmbown/CodeWhale/pull/4675)

4.  **#4694 [CLOSED] fix(kimi): fail closed on K3 model-ID cross-pairings**
    *   **内容**：修复了 Kimi/Moonshot 模型 ID 交叉配对问题，确保路由身份的唯一性和正确性。
    *   **链接**: [PR #4694](https://github.com/Hmbown/CodeWhale/pull/4694)

5.  **#4711 [CLOSED] fix(tui): focus v0.9.1 chrome on todos and agents**
    *   **内容**：优化了顶部栏渲染，仅显示活跃的 To-dos 和 Sub-agents，隐藏完成项，并支持拖拽调整大小。
    *   **链接**: [PR #4711](https://github.com/Hmbown/CodeWhale/pull/4711)

6.  **#4696 [CLOSED] feat(tui): ship staged /uwu theme**
    *   **内容**：发布了社区定制的 `/uwu` 主题，包括特定的颜色闪烁和空状态鲸鱼标志设计，丰富了主题生态。
    *   **链接**: [PR #4696](https://github.com/Hmbown/CodeWhale/pull/4696)

7.  **#4714 [OPEN] chore(deps): patch npm lockfiles for Dependabot alerts**
    *   **内容**：针对 Dependabot 警报修补 npm 锁文件，特别是修复了 protobufjs 和 axios 等库的安全漏洞，为发布扫清障碍。
    *   **链接**: [PR #4714](https://github.com/Hmbown/CodeWhale/pull/4714)

8.  **#4370 [CLOSED] feat: add TelecomJS provider support with configuration and catalog...**
    *   **内容**：修复并添加了 TelecomJS 提供商支持，解决了模型目录刷新缓存未调用的问题，扩展了自定义模型接入能力。
    *   **链接**: [PR #4370](https://github.com/Hmbown/CodeWhale/pull/4370)

9.  **#4680 [CLOSED] fix(tui): register debt compatibility aliases**
    *   **内容**：注册了 `/slop` 和 `/canzha` 作为 `/debt` 的别名，统一了命令分发和发现的真相来源，增强了命令系统的兼容性。
    *   **链接**: [PR #4680](https://github.com/Hmbown/CodeWhale/pull/4680)

10. **#4087 [OPEN] [v0.9.3] refactor(hooks): split config and executor modules**
    *   **内容**：早期重构 PR，将 hooks 的配置定义与执行器行为分离，提高了代码的可维护性和审查效率，为后续版本打基础。
    *   **链接**: [PR #4087](https://github.com/Hmbown/CodeWhale/pull/4087)

## 5. 功能需求趋势
从当前 Issues 和 PR 可以看出以下明显趋势：
*   **上下文优化（Context Optimization）**：v0.9.2 的重心明确转向“上下文瘦身”，通过减少重复的系统提示、精简工具描述和合并重叠的状态字段，以降低 Token 成本并提升模型理解力。
*   **用户体验标准化（UX Standardization）**：v0.9.1 致力于提供类似主流 AI IDE（如 Cursor, Claude Code）的标准体验，包括统一的工作区视图、技能包管理和清晰的 Agent 活动展示。
*   **多模型与提供商扩展**：持续扩展对国内模型（Kimi/Moonshot, MiniMax, TelecomJS）的支持，并强化对不同 API 路由和模型 ID 的健壮性处理。
*   **UI/主题定制化**：除了官方主题，社区对 `/uwu` 等个性化主题的接纳度提高，且开发者在努力使 UI 元素（如 rails, lanes）更好地适配系统原生主题。

## 6. 开发者关注点
*   **Windows 安装稳定性**：用户对 Windows 安装器破坏 PATH 环境变量的问题反应强烈，这是一个亟待修复的高优先级 Bug。
*   **安全依赖更新**：社区和 Maintainer 高度关注 Dependabot 警报，特别是涉及 `axios` 和 `body-parser` 的高危漏洞，要求发布前必须清零。
*   **TUI 信息密度与可读性**：开发者反馈现有工作区（Work Surface）信息过载或层次不清，特别是在处理 Shell 失败和子代理状态时，需要更清晰的视觉层级和摘要信息。
*   **命令与技能管理的易用性**：用户希望技能管理更加集中化和自动化，减少对记忆具体命令的依赖，强调“开箱即用”的技能包体验。

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>