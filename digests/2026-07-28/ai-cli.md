# AI CLI 工具社区动态日报 2026-07-28

> 生成时间: 2026-07-28 03:14 UTC | 覆盖工具: 10 个

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

# 2026-07-28 AI CLI 工具横向对比分析报告

## 1. 生态全景
当前 AI CLI 工具生态正从“单一辅助向 Agent 化工作流”转变，竞争焦点从基础编码转向多设备协作、跨平台稳定性及企业级安全。OpenAI Codex 与 Gemini CLI 在 Rust 重构与智能体可靠性上深度投入；Claude Code 面临 Windows 端严峻挑战；GitHub Copilot CLI 则在自动化体验上与 Kimi 形成差异化互补，整体呈现技术碎片化与标准化并行的局面。

## 2. 各工具活跃度对比（Top 10 指标）

| 工具名称 | Issues 数 (TOP) | PR 数 (TOP) | 版本发布状态 | 关键风险/机会点 |
| :--- | :---: | :---: | :---: | :--- |
| **Grok Build** | 0 | 0 | 停滞 | **低活跃度**，社区反馈真空，存在被市场边缘化风险。 |
| **Kimi Code CLI** | ~4 (精选) | 5 | 无 | **开发密集**，针对 VSCode 扩展稳定性与钩子机制修复，处于关键补丁期。 |
| **OpenCode** | 10 | 10+ | v1.18.7 (Desktop) | **架构重构**，MCP v2 升级与 Session Controller 拆分是长期核心任务。 |
| **Pi** | Top 3 (高权重) | 10 | 无 | **兼容性强**，专注于多模型 Provider 协议的统一与配置鲁棒性优化。 |
| **Qwen Code** | 10 | 10 | No | **CI 压力大**，SWE-bench 验证未达标且主分支 E2E 测试大量失败。 |
| **DeepSeek TUI** | 10 | 30 | v0.9.2 RC | **性能激进**，聚焦渲染引擎 O(N²) 瓶颈与 Windows CRLF 兼容性攻坚。 |
| **Gemini CLI** | 10 | 10 | v0.54.0-nightly | **高安全优先级**，变量注入漏洞与 A2A 服务器稳定性为首要诉求。 |
| **Copilot CLI** | 10 | 5 (有效) | v1.0.76-0 | **僵尸进程严重**，Plan Mode 权限回退与 macOS Keychain 冲突暴露底层缺陷。 |
| **OpenAI Codex** | 10 | 10 | rust-v0.146.0-alpha.13 | **平台适配难**，Windows 沙箱与安全机制失效阻碍 Alpha 进度。 |
| **Claude Code** | 10 | 10 | 无 | **高危阻塞**，Windows 白屏与 Opus 指令遵循率退化直接影响核心声誉。 |

> *注：Issues 与 PR 数据基于各日报摘要中的“热点/重要”条目统计*

## 3. 共同关注的功能方向
*   **会话管理与连续性**（覆盖所有主流工具）：
    *   *诉求*：自动恢复、本地转录文件云端访问、跨设备设置同步（如 Claude #22648, OpenCode 会话死循环）。
    *   *趋势*：工作流的断点续连已成为生产力基线。
*   **安全性与权限控制**（DeepSeek, Gemini, Copilot）：
    *   *诉求*：代理命令过滤（DeepSeek #4042）、输入变量注入防护（Gemini #28403）、沙箱逃逸检测（Codex #30712）。
    *   *趋势*：从模型幻觉治理延伸至执行环境的安全沙箱。
*   **TUI 性能与渲染效率**（DeepSeek, Qwen, Pi）：
    *   *诉求*：避免长文本重解析卡顿、后台线程阻塞 UI、异步 I/O 假死。
    *   *趋势*：终端界面的流畅度成为新体验分水岭。

## 4. 差异化定位分析
*   **Claude Code**：依赖强大原生模型能力（Opus），但受限于 Windows 生态的底层工程能力，目前重点在于修修补补以挽回桌面端口碑。
*   **OpenAI Codex / DeepSeek TUI**：采用 Rust 构建 CLI 核心，追求极致的跨平台原生性能与内存管理，但在复杂环境（Windows UAC, Wayland）下的适配策略依然充满挑战。
*   **GitHub Copilot CLI**：深耕微软生态与 Git 集成，侧重自动化工作流（Autopilot/Plan Mode），但在进程管理和跨平台签名一致性上存在技术债务。
*   **Pi / OpenCode**：定位为“超级聚合器”，致力于抽象底层 API 差异（Anthropic/Claude/OpenAI/Qwen 等），重点解决多 Provider 的协议标准化问题。

## 5. 社区热度与成熟度判断
*   **快速迭代期（High Velocity）**：**DeepSeek TUI**（每日数十条 PR/Issue，v0.9.2 收尾）、**Gemini CLI**（高频 nightly 更新修复 P0 级漏洞）、**OpenCode**（大规模 Refactor 重构架构）。
*   **成熟稳定期（Stable but Reactive）**：**Claude Code**（社区规模大但主要精力用于危机公关和 Bug 修复）、**Copilot CLI**（功能完善但回归测试频发，需持续打补丁）。
*   **风险警示区（Caution Required）**：**Qwen Code**（CI 流水线大面积崩溃，基准测试隔离）、**Grok Build**（零活动，生态萎缩迹象明显）。

## 6. 值得关注的趋势信号
1.  **Agent Workflows 的“状态机困境”**：多个工具（Gemini #22323, Qwen #7835, OpenCode #29660）普遍反映智能体在循环逻辑、子代理交互及任务回滚（Undo）时逻辑混乱。**建议开发者在设计自动化脚本时，对复杂状态流转增加显式的人工确认或熔断机制。**
2.  **Windows 兼容性的回归**：尽管 Mac/Linux 开发者占比渐高，但 Windows 端的 CRLF 换行符、UAC 授权、Keychain 签名冲突等问题仍是最普遍的 crash 源。**跨平台工具若想在 2026 年取得突破，必须将 Windows Dev 环境列为第一梯队测试用例。**
3.  **MCP 协议的加速落地**：OpenCode、Kimi、Claude、DeepSeek 均提及 MCP（Model Context Protocol）相关的 SDK 升级或工具别名标准化。**关注 MCP v2 的无状态协商特性可能是未来插件集成的关键接口标准。**

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills 社区热点报告 (截止 2026-07-28)

## 1. 热门 Skills 排行（按 PR 评论/关注度排序）

| # | Skill 名称 | 功能描述 | 社区讨论热点 | 状态 | GitHub 链接 |
|---|------------|----------|--------------|------|-------------|
| 1 | `skill-creator` 修复系列 | 解决 `run_eval.py` 评估逻辑失效问题，实现技能描述优化闭环 | 核心工具链可靠性、Windows 兼容性、召回率计算 bug | Open | [#1298](https://github.com/anthropics/skills/pull/1298) |
| 2 | `document-typography` | AI 文档的排版质量控制（断行、寡居、编号对齐） | 提升专业文档输出质量，用户关注度高 | Open | [#514](https://github.com/anthropics/skills/pull/514) |
| 3 | `odt` 技能 | OpenDocument 格式文件的创建、填充与解析 | 企业级文档处理需求、开源文档支持 | Open | [#486](https://github.com/anthropics/skills/pull/486) |
| 4 | `frontend-design` | 前端设计指令清晰度与可执行性优化 | 提升技能落地效果、减少模糊指令反馈 | Open | [#210](https://github.com/anthropics/skills/pull/210) |
| 5 | `skill-quality-analyzer` / `skill-security-analyzer` | 技能质量与安全双重分析工具（元技能） | 技能生态标准化、安全合规性审查 | Open | [#83](https://github.com/anthropics/skills/pull/83) |
| 6 | `testing-patterns` | 完整测试栈技能：单元测试、React 组件测试等 | 开发者对自动化测试覆盖度的强烈需求 | Open | [#723](https://github.com/anthropics/skills/pull/723) |
| 7 | `pyxel` | 复古像素游戏开发技能（Pyxel-MCP 集成） | 创意开发场景、游戏化应用探索 | Open | [#525](https://github.com/anthropics/skills/pull/525) |
| 8 | `self-audit` v1.3.0 | 机械验证 + 四维度推理质量门控的技能审计工具 | AI 交付前的质量保证、通用项目适用 | Open | [#1367](https://github.com/anthropics/skills/pull/1367) |

---

## 2. 社区需求趋势（来自 Issues 高频诉求）

根据 Issue 评论数与互动热度，社区最期待的 **新 Skill 方向**如下：

- ✅ **工作流自动化与上下文管理**：如 `compact-memory`（符号化紧凑代理状态）、`plan-file-hygiene`（计划文件生命周期治理），反映用户对“记忆压缩”、“规划 artifact 清理”的实际痛点。
- ✅ **组织协作与权限控制**：Issue #228 提出“组织范围技能共享”，需支持团队内一键分发技能库；Issue #492 关注 `anthropic/` namespace 被滥用引发的信任边界问题，亟需身份认证或签名机制。
- ✅ **安全与合规审计**：Issue #1175（SharePoint Online 安全上下文泄露风险）、Issue #412（Agent Governance 技能提案）均指向企业级安全合规需求。
- ✅ **跨平台与云原生集成**：Issue #29（AWS Bedrock 兼容）、Issue #16（Skills → MCP 暴露协议）显示社区希望 Skill 能更好接入多云环境与现代 API 协议。
- ✅ **开发者工具链增强**：`skill-creator` 相关 Issue 大量提及 Windows 兼容、YAML 解析错误、编码问题，说明当前 CLI 工具链稳定性是最大瓶颈。

> 📊 **关键词聚类**：`security`, `organize`, `share`, `test`, `platform`, `debug`, `context`, `quality gate`

---

## 3. 高潜力待合并 Skills（评论活跃 + 技术价值高）

| PR # | Skill | 活跃度 | 理由 |
|------|-------|--------|------|
| #1367 | `self-audit` v1.3.0 | 近期更新（7.2），作者跟进积极 | 引入“四维度推理质量门控”，符合当前 AI 生成内容可信度热潮，易被广泛采纳 |
| #525 | `pyxel` retro game dev | 最后更新 7.15，持续维护中 | 创意型用例稀缺且具传播力，可吸引非传统企业用户群体 |
| #1479 | `plan-file-hygiene` | 非常新（7.25），回应社区问题 #1417 | 直接解决“规划 artifact 堆积”这一普遍痛点，实用性强 |
| #723 | `testing-patterns` | 3月底提交，内容全面覆盖测试范式 | 填补 Skill 生态中“工程实践类”技能空白，适合开发者场景 |
| #83 | `skill-quality-analyzer` + `security-analyzer` | 1月提交但仍在 Open，含两个独立分析器 | 构建技能质量基准线，未来可能成为官方审核标准 |

---

## 4. Skills 生态洞察

> **“当前社区最集中的诉求是：在确保技能安全性和可用性的前提下，通过标准化、自动化和协作化手段，让 Skill 真正成为可扩展的生产力引擎。”**

—— 即：**安全可控 + 自动化工具链 + 组织级共享 = Skill 生态成熟度核心指标**

---

# Claude Code 社区动态日报（2026-07-28）

## 今日速览
今日社区活跃于 Windows 平台稳定性与跨设备同步问题，焦点集中在终端快捷键冲突及会话恢复机制的讨论上。无新版本发布，主要议题涉及模型指令遵循失败、GPU 进程崩溃修复以及内存管理等核心底层改进。

## 版本发布
**无**

## 社区热点 Issues
1. **#5064 [FEATURE]** Windows 平台 `Ctrl+Enter` 快捷键与新行功能冲突，导致不符合常规操作习惯。**（52 👍, 30 评论）**：影响最广泛的体验类需求。[链接](https://github.com/anthropics/claude-code/issues/5064)
2. **#22648 [Feature Request]** 账户级设置跨设备同步方案。**（43 👍, 24 评论）**：多设备用户痛点长期未解决。[链接](https://github.com/anthropics/claude-code/issues/22648)
3. **#51143 [BUG]** Windows 桌面端持续白屏问题，多次重装无效。**（20 👍, 18 评论）**：高危可用性阻塞 Bug。[链接](https://github.com/anthropics/claude-code/issues/51143)
4. **#81703 [BUG]** 7月17日批量账单异常争议事件追踪。**（7 评论）**：直接关联资金与服务信任度。[链接](https://github.com/anthropics/claude-code/issues/81703)
5. **#54186 [BUG]** VS Code 重启后本地会话历史丢失。**（14 👍, 13 评论）**：严重干扰工作流连续性。[链接](https://github.com/anthropics/claude-code/issues/54186)
6. **#61172 [BUG]** `/clear` 命令继承旧会话名导致命名混乱。**（12 👍, 8 评论）**：细节缺陷积累易引发混淆。[链接](https://github.com/anthropics/claude-code/issues/61172)
7. **#79366 [BUG]** Worktree 会话复用旧目录而非创建新隔离环境。**（6 评论）**：针对高级用户场景的数据隔离风险。[链接](https://github.com/anthropics/claude-code/issues/79366)
8. **#78946 [BUG]** Windows 认证登录死循环问题。**（3 评论）**：阻碍新用户或特定配置用户的使用。[链接](https://github.com/anthropics/claude-code/issues/78946)
9. **#57902 [CLOSED]** Opus 4.7 + 4.8 版本指令遵循及绕过失败复现率高。**（2 👍, 3 评论）**：模型核心能力退化需重点关注。[链接](https://github.com/anthropics/claude-code/issues/57902)
10. **#81834 [BUG]** `cd <other-dir> && git` 模式下权限询问被静默跳过。**（0 👍, 0 评论）**：潜在的安全风险点。[链接](https://github.com/anthropics/claude-code/issues/81834)

## 重要 PR 进展
1. **#81673**: 修复 Devcontainer 防火墙设置中因域名解析失败导致脚本中断的问题。[链接](https://github.com/anthropics/claude-code/pulls/81673)
2. **#81672**: 使 Hookify 包导入逻辑不再依赖于安装目录的具体名称。[链接](https://github.com/anthropics/claude-code/pulls/81672)
3. **#81670**: 在 Hookify 命令中对 `${CLAUDE_PLUGIN_ROOT}` 进行引号处理并优化示例代码，解决含空格路径下的兼容性 Bug。[链接](https://github.com/anthropics/claude-code/pulls/81670)
4. **#81804**: 修复 VS Code 扩展主机因会话元数据过大导致的 OOM（内存溢出）崩溃问题，显著降低内存占用。[链接](https://github.com/anthropics/claude-code/pulls/81804)
5. **#80662**: 解决 Opus 4.8 模型在长文本生成过程中中间段落内容从转录中静默丢失的回溯性 Bug。[链接](https://github.com/anthropics/claude-code/pulls/80662)
6. **#81837**: 提议将 Claude Desktop 注册为 Windows 11 原生搜索/Copilot 键的目标应用。[链接](https://github.com/anthropics/claude-code/pulls/81837)
7. **#81835**: 建议桌面端支持加载本地磁盘上的转录文件以实现跨机器会话连续性。[链接](https://github.com/anthropics/claude-code/pulls/81835)
8. **#20448**: 引入基于 Web4 治理框架的新插件，用于 AI 行为的信任和审计追踪。[链接](https://github.com/anthropics/claude-code/pulls/20448)
9. **#70368**: 提议在聊天输出中通过字号和粗细区分 Markdown 标题层级，提升可读性。[链接](https://github.com/anthropics/claude-code/pulls/70368)
10. **#81576**: 修正 `plugins/README.md` 中关于安全指导插件钩子配置的文档错误。[链接](https://github.com/anthropics/claude-code/pulls/81576)

## 功能需求趋势
*   **IDE 与编辑器集成深度**：用户强烈要求深化与 VS Code、Windows Shell 的集成，包括 Copilot 键呼出、光标位置高亮显示等。
*   **会话管理与工作流效率**：频繁出现的功能请求围绕自动恢复（Quota/Rate-limit）、会话名自动去重、快捷方式自定义展开。
*   **跨设备一致性**：设置同步和本地转录文件的云端访问是提升生产力的关键诉求。

## 开发者关注点
当前社区反馈高度集中于**系统稳定性**（特别是 Windows 端的白屏、GPU crash 和登录死循环）以及**模型层可靠性**（Opus 系列的指令遵循错误）。此外，性能优化方向主要集中在 V8 内存泄漏修复和终端渲染性能调优上。

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex 社区动态日报 (2026-07-28)

## 今日速览
过去24小时，Codex Rust 版本持续迭代发布至 alpha.13 阶段，同时社区聚焦于 Windows 平台稳定性、MCP 认证刷新机制及 TUI 交互体验修复。GitHub 上高赞 Issue 达到数十条，反映出用户对功能稳定性和多 Agent 协作深度的强烈关切。

## 版本发布
*   **rust-v0.146.0-alpha.13**: 最新 Alpha 版更新，主要包含底层日志客户端与会话管理的优化调整（PR #35695）。
*   **rust-v0.146.0-alpha.12**: 上一版本迭代，作为本次周期内的中间补丁存在。

## 社区热点 Issues (Top 10)
以下问题因评论数、点赞数或技术影响范围而被重点追踪：

1.  **#9203 [TUI] Request "/undo" feature** (⭐65条评论, 👍362)
    *   **重要性**: 用户急需撤销意外文件删除或未提交修改的功能，直接关乎数据安全性。
    *   **链接**: [openai/codex Issue #9203](https://github.com/openai/codex/issues/9203)
2.  **#17265 [auth/mcp] MCP Token Refresh Failure** (⭐27条评论, 👍54)
    *   **重要性**: 涉及核心安全认证机制，Token 过期不刷新会导致工具调用连续失败，严重影响工作流。
    *   **链接**: [openai/codex Issue #17265](https://github.com/openai/codex/issues/17265)
3.  **#32149 [windows-os/app] Windows Setup Fails Before UAC** (⭐27条评论)
    *   **重要性**: 阻碍了 Windows 用户的入门安装体验，属基础环境配置类 blocker。
    *   **链接**: [openai/codex Issue #32149](https://github.com/openai/codex/issues/32149)
4.  **#24948 [TUI] Session Logs Grow Excessively** (⭐24条评论)
    *   **重要性**: 磁盘占用膨胀至 GB 级，导致本地存储压力过大，需优化历史留存策略。
    *   **链接**: [openai/codex Issue #24948](https://github.com/openai/codex/issues/24948)
5.  **#32094 [app/browser] Codex Crash on WebCodecs Pages** (⭐18条评论)
    *   **重要性**: 内嵌浏览器在处理特定图形 API 页面时崩溃，影响代码生成环境的稳定性。
    *   **链接**: [openai/codex Issue #32094](https://github.com/openai/codex/issues/32094)
6.  **#25319 [extension] Scope VS Code Chats to Workspace** (⭐18条评论, 👍48)
    *   **重要性**: 提升 IDE 插件的上下文感知能力，要求限制对话范围为当前项目，避免泛化干扰。
    *   **链接**: [openai/codex Issue #25319](https://github.com/openai/codex/issues/25319)
7.  **#30712 [sandbox] Windows `apply_patch` Injection Failures** (⭐15条评论, 👍13)
    *   **重要性**: 安全沙箱机制失效迫使脚本绕过保护写入文件，威胁系统完整性。
    *   **链接**: [openai/codex Issue #30712](https://github.com/openai/codex/issues/30712)
8.  **#13852 [auth/mcp] Supabase Re-authentication Loop** (⭐14条评论)
    *   **重要性**: 特定第三方服务（Supabase）集成时的重复登录痛点。
    *   **链接**: [openai/codex Issue #13852](https://github.com/openai/codex/issues/13852)
9.  **#11324 [MCP Memory Leak]** (⭐14条评论, 👍5)
    *   **重要性**: 多任务并发下 MCP 服务器内存占用激增，可能导致应用 OOM (Out Of Memory)。
    *   **链接**: [openai/codex Issue #11324](https://github.com/openai/codex/issues/11324)
10. **#35352 [browser GPU] Desktop Exit on Crash** (⭐13条评论)
    *   **重要性**: 显卡进程崩溃导致整个桌面端退出，用户体验极差且频繁。
    *   **链接**: [openai/codex Issue #35352](https://github.com/openai/codex/issues/35352)

## 重要 PR 进展 (Top 10)
开发团队近期提交了多项关键修复与优化，主要集中在 Rust 重构、内存管理和 Windows 兼容性：

1.  **#35695: Logs Client SQLite Home Fix** (已合并)
    *   **内容**: 解决日志客户端读取错误数据库路径的问题，确保 `CODEX_HOME` 配置生效。
    *   **链接**: [PR #35695](https://github.com/openai/codex/pull/35695)
2.  **#35693: Background Subagent Picker Refresh** (已合并)
    *   **内容**: 优化后台子代理选择器渲染逻辑，减少终端输入延迟。
    *   **链接**: [PR #35693](https://github.com/openai/codex/pull/35693)
3.  **#35691: Empty-Preview Threads in Listings** (已合并)
    *   **内容**: 在关系列表中保留无预览文本的线程对象，保持元数据一致性。
    *   **链接**: [PR #35691](https://github.com/openai/codex/pull/35691)
4.  **#35688: Crossterm Patch Update** (已合并)
    *   **内容**: 将终端库依赖切换至 OpenAI OSS 分支，统一代码库管理。
    *   **链接**: [PR #35688](https://github.com/openai/codex/pull/35688)
5.  **#35685: Cloud-Managed Profiles for Sandbox** (已合并)
    *   **内容**: 支持云端托管的沙箱权限配置文件，增强企业级管控能力。
    *   **链接**: [PR #35685](https://github.com/openai/codex/pull/35685)
6.  **#35678: Pagination Metadata Across Resumes** (已合并)
    *   **内容**: 恢复线程分页时保留历史元数据，防止上下文中断。
    *   **链接**: [PR #35678](https://github.com/openai/codex/pull/35678)
7.  **#35675: Concurrent MCP & Plugin Prep** (已合并)
    *   **内容**: 并行准备 MCP 运行时和插件推荐，降低启动等待时间。
    *   **链接**: [PR #35675](https://github.com/openai/codex/pull/35675)
8.  **#35671: Route Plugins by Auth Mode** (已合并)
    *   **内容**: 根据认证模式动态路由插件列表，确保权限匹配。
    *   **链接**: [PR #35671](https://github.com/openai/codex/pull/35671)
9.  **#35670: Raise Windows Exec Yield Floor** (已合并)
    *   **内容**: 提高 Windows 执行命令的最小 yield 时间（10秒），优化进程调度。
    *   **链接**: [PR #35670](https://github.com/openai/codex/pull/35670)
10. **#35655: Terminate Non-TTY Processes on Interrupt** (已合并)
    *   **内容**: 修复 Windows 下非交互式进程无法响应 Ctrl-C 中断的问题。
    *   **链接**: [PR #35655](https://github.com/openai/codex/pull/35655)

## 功能需求趋势
从 Issue 摘要分析，社区未来关注的核心方向包括：
*   **IDE 深度集成**：VS Code 扩展的会话作用域绑定（Issue #25319）和多窗口打开修复是高频诉求。
*   **性能与资源管理**：针对日志体积爆炸（Issue #24948）、内存泄漏（Issue #11324）及 CPU 泄露（Issue #34178）的优化极为迫切。
*   **平台兼容性**：Windows 端的沙箱补丁失败、GPU 崩溃及原生应用闪退问题占比最高，成为当前最大的稳定性的短板。
*   **Agent 协作**：多 Agent 模式下的指令继承（PR #35653）和遗留 Session 工具缺失（Issue #25990）显示复杂工作流支持的需求上升。

## 开发者关注点总结
当前开发者反馈集中于三大痛点：
1.  **数据安全风险**：缺乏 Undo 功能导致的误操作风险以及 Windows 沙箱被 bypass 的安全隐患。
2.  **本地化工具链不稳定**：TUI 下的日志清理失效以及 App 端对 Mac OS 和 Windows 不同版本的适配差异。
3.  **认证与配置同步难题**：MCP OAuth 自动刷新失效导致工具链断连，以及订阅降级后额度计算逻辑的争议。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI 社区动态日报 (2026-07-28)

## 1. 今日速览
Gemini CLI 昨晚发布 v0.54.0-nightly.20260728 版本，主要修复了 A2A 服务器 CRLF 换行问题及 Keychain 标签长度验证。今日社区焦点集中在 Agent 子系统稳定性、Shell 命令执行挂起以及安全相关的变量绕过漏洞上，多个 P1 级别 Bug 获大量关注。

## 2. 版本发布
**v0.54.0-nightly.20260728.gbef611950** (昨晚发布)
- **Core**: 强制实施文件密钥链（file keychain）中显式标签长度与验证 (#PR28523)。
- **A2A Server**: 在 `getProposedContent` 中将 CRLF 行尾符标准化为 LF，解决 Windows 下侧边对比视图无法高亮的问题 (#PR28531)。

## 3. 社区热点 Issues (Top 10)

| # | Issue 标题 | 作者 | 评论/赞 | 为何重要 |
|---|---|---|---|---|
| **#22323** | Subagent recovery after MAX_TURNS is reported as GOAL success... | matei-anghel | 💬 12 👍 2 | **核心逻辑错误**：子代理即使达到最大回合数未分析完内容仍报告成功，导致中断被隐藏，严重误导用户信任。 |
| **#21409** | Generalist agent hangs | turmanticant | 💬 8 👍 8 | **高频阻塞问题**：通用智能体挂起导致基础功能（如文件夹创建）不可用，用户等待超小时数，反馈热烈。 |
| **#26522** | Stop Auto Memory from retrying low-signal sessions indefinitely | SandyTao520 | 💬 5 | **资源浪费风险**：低信度会话无限重试可能导致存储膨胀和性能下降，涉及内存管理架构。 |
| **#26525** | Add deterministic redaction and reduce Auto Memory logging | SandyTao520 | 💬 4 | **隐私与安全**：当前重命名机制先发送内容后脱敏，存在数据泄露风险，亟需改进日志策略。 |
| **#25166** | Shell command execution gets stuck with "Waiting input" after command completes | rnett | 💬 4 👍 3 | **体验痛点**：简单命令执行完成后 UI 仍显示“等待输入”，假死状态干扰 workflow。 |
| **#21983** | browser subagent fails in wayland | sigmaSd | 💬 4 👍 1 | **环境兼容性问题**：Wayland 环境下浏览器子代理终止原因显示异常，影响 Linux 高级用户。 |
| **#21968** | Gemini does not use skills and sub-agents enough | rnett | 💬 6 | **能力 utilization**：用户反映模型不主动调用技能和子智能体，削弱了自动化潜力。 |
| **#22267** | [BUG] Browser Agent ignores settings.json overrides | hsm207 | 💬 3 | **配置失效**：浏览器代理忽略全局或项目级的 `settings.json` 覆盖（如 maxTurns），配置管理混乱。 |
| **#24246** | Gemini CLI encounters 400 error with > 128 tools | gundermanc | 💬 3 | **扩展性限制**：工具数量超过阈值时报错，限制了复杂工作流的编排能力。 |
| **#22672** | Agent should stop/discourage destructive behavior | abhipatel12 | 💬 3 👍 1 | **Safety 机制**：模型可能执行危险命令（如 git reset --force），社区呼吁增加防护审查。 |

*注：所有 Issue 链接均为 `google-gemini/gemini-cli/issues/[ID]*

## 4. 重要 PR 进展 (Top 10)

| # | PR 编号 | 类型 | 摘要 | 状态 | 链接 |
|---|---|---|---|---|---|
| **1** | #28546 | Security | 修复 `GEMINI_API_KEY` 认证时的 Authorization 头部残留问题，防止 401 错误。 | Open | [#28546](https://github.com/google-gemini/gemini-cli/pull/28546) |
| **2** | #28403 | Security | 修补 `$VAR` 和 `${VAR}` 变量展开绕过漏洞 (GHSA-wpqr-6v78-jr5g)，增强 shell 注入防护。 | Open | [#28403](https://github.com/google-gemini/gemini-cli/pull/28403) |
| **3** | #28394 | Core | 修复后台 Shell 执行后临时目录泄漏问题，确保系统清洁退出。 | Closed | [#28394](https://github.com/google-gemini/gemini-cli/pull/28394) |
| **4** | #28397 | Core | 将 Shell 工具关键路径中的同步 I/O 改为异步，消除 Ink 终端卡顿现象。 | Closed | [#28397](https://github.com/google-gemini/gemini-cli/pull/28397) |
| **5** | #28389 | Agent | 引入实时时间预算限制，防止事件驱动的智能体状态转换进入死循环。 | Closed | [#28389](https://github.com/google-gemini/gemini-cli/pull/28389) |
| **6** | #28387 | Core | 为 `customDeepMerge` 添加循环引用保护，修复设置管理器崩溃 bug。 | Closed | [#28387](https://github.com/google-gemini/gemini-cli/pull/28387) |
| **7** | #28388 | Agent | 修复 `tools.core` wildcard deny 误伤 MCP 工具的策略缺陷，恢复工具信任机制。 | Closed | [#28388](https://github.com/google-gemini/gemini-cli/pull/28388) |
| **8** | #28481 | MCP | 修复 MCP OAuth Token 刷新逻辑，避免因客户端 ID 丢失导致的频繁重新认证。 | Open | [#28481](https://github.com/google-gemini/gemini-cli/pull/28481) |
| **9** | #28485 | CLI | 支持新模型 `gemini-3.5-flash` 和 `3.6-flash` 在模型选择器中可见，填补版本兼容空缺。 | Open | [#28485](https://github.com/google-gemini/gemini-cli/pull/28485) |
| **10**| #28551 | CLI | 修复 macOS Seatbelt 配置文件缺失导致的沙箱启动崩溃，提升跨平台鲁棒性。 | Open | [#28551](https://github.com/google-gemini/gemini-cli/pull/28551) |

## 5. 功能需求趋势
基于 Issue 统计，社区关注点呈现以下三大趋势：
1. **Agent 可靠性与自主性**：高频率 Issues 指向智能体的状态机设计（超时处理、死锁预防）、技能调度策略及浏览器环境的稳定性。
2. **安全性加固**：从变量注入防护到敏感信息脱敏（Auto Memory），再到 OAuth 令牌刷新逻辑，安全层是近期开发的重中之重。
3. **新模型与工具兼容性**：用户对最新 Flash 模型的支持呼声强烈，同时对超过一定数量的 MCP 工具报错提出扩容诉求。

## 6. 开发者关注点
- **UI/UX 流畅度**：终端渲染在调整大小时的闪烁、异步 I/O 阻塞导致的假死体验是用户投诉较多的技术细节。
- **调试信息缺失**：Bug Report 缺乏子代理上下文、错误原因描述不够具体（如 Issue #21763），增加了排障难度。
- **配置与行为不一致**：Settings 配置未被所有组件（特别是 Browser Agent）正确读取，暗示了配置系统的解耦或分发机制存在问题。

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI 社区动态日报 (2026-07-28)

## 1. 今日速览
Copilot CLI v1.0.76-0 发布了自动保持 Autopilot 模式和 MCP 工具加载优化的更新。社区当前最关注的是 `plan-mode` 权限回退问题以及僵尸进程泄漏（Issue #4188, #4163），同时 macOS 用户正热议签名冲突导致 Keychain 频繁请求密码的问题（Issue #4273）。

## 2. 版本发布
**v1.0.76-0** (最新发布)
*   **改进**: MCP 工具从定义范围快照加载速度更快；Autopilot 模式在任务完成后默认保持选中状态（可通过 `stayInAutopilot: false` 回调至交互模式）。
*   **修复**: 恢复了早期的警告提示（详情见完整版 release notes）。
*   [查看 Release](https://github.com/github/copilot-cli/releases/tag/v1.0.76-0)

## 3. 社区热点 Issues (Top 10)

1.  **#4188 [OPEN] Regression on plan-mode** (6 评论, 3 👍)
    *   **内容**: 新版 Plan Mode 错误地阻断了 shell 命令（如 gh cli），被视为回归 Bug，严重影响基于计划的自动化工作流。
    *   [链接](https://github.com/github/copilot-cli/issues/4188)

2.  **#2792 [CLOSED] Automatic switching between model for planning and execution** (5 评论, 16 👍)
    *   **内容**: 高票需求：希望 Planning 和 Execution 阶段能使用不同的可配置模型以优化效率和成本。该 Issue 近期关闭表明该功能可能已纳入路线或在讨论中达成一致。
    *   [链接](https://github.com/github/copilot-cli/issues/2792)

3.  **#4163 [CLOSED] copilot CLI 1.0.71 does not reap child processes — zombies accumulate** (5 评论, 3 👍)
    *   **内容**: 严重性能问题，子进程成为僵尸进程并在 Copilot PID 下泄漏（约每分钟 2 个），长期运行会导致资源耗尽。
    *   [链接](https://github.com/github/copilot-cli/issues/4163)

4.  **#1381 [OPEN] "Rewind is not available because you're not in a git repository."** (3 评论, 9 👍)
    *   **内容**: 不使用 Git 的用户反馈“回滚”（Rewind）功能不可用，要求支持非 Git 版本控制系统。
    *   [链接](https://github.com/github/copilot-cli/issues/1381)

5.  **#4183 [CLOSED] Auto-compaction does not prevent CAPI 5 MB failure from accumulated normal tool history** (4 评论, 10 👍)
    *   **内容**: 自动压缩无法防止因工具历史记录累积导致的 CAPI 5MB 体积极限错误，长会话易失败。
    *   [链接](https://github.com/github/copilot-cli/issues/4183)

6.  **#4118 [OPEN] /app command does not select current working directory by default** (0 评论, 35 👍)
    *   **内容**: `/app` 命令打开桌面应用时未自动定位到当前本地目录，被用户标记为高频痛点。
    *   [链接](https://github.com/github/copilot-cli/issues/4118)

7.  **#3977 [CLOSED] Persist autopilot mode across interactive turns via launch flag/setting** (2 评论, 1 👍)
    *   **内容**: 请求增加持久化 Autopilot 模式的启动标志，避免每次任务完成都需手动重新启用。
    *   [链接](https://github.com/github/copilot-cli/issues/3977)

8.  **#4258 [OPEN] Interactive -i startup prompt is ignored with custom/BYOK provider in TTY sessions** (2 评论, 0 👍)
    *   **内容**: 在使用自定义提供商的 TTY 会话中，交互式启动提示 `-i` 未被自动提交，影响工作流连贯性。
    *   [链接](https://github.com/github/copilot-cli/issues/4258)

9.  **#1272 [CLOSED] Plan mode not switching when AI asks to do changes** (4 评论, 1 👍)
    *   **内容**: 当 AI 请求变更时，Plan Mode UI 未能及时刷新状态，造成混淆。
    *   [链接](https://github.com/github/copilot-cli/issues/1272)

10. **#4273 [OPEN] macOS: keychain prompts on every launch...** (0 评论, 0 👍)
    *   **内容**: 新发现的高优先级 macOS 特定 Bug，Microsoft 与 GitHub 签名的二进制文件共享登录项导致 XARA 分区不匹配，每次启动都弹出密钥链密码请求。
    *   [链接](https://github.com/github/copilot-cli/issues/4273)

## 4. 重要 PR 进展

*   **#1598 [OPEN] fix: add trap to clean up temp directory on unexpected exit**
    *   **修复**: 修复了安装脚本在非预期退出（如网络错误）后未清理 `/tmp` 临时目录的问题，防止磁盘泄漏。
    *   [链接](https://github.com/github/copilot-cli/pull/1598)

*   **#1116 [OPEN] Fix misleading doc - 0x models dont reduce quota**
    *   **文档**: 修正了 README 中关于 0x 模型消耗配额的误导性说明，明确此类模型实际不减少可用配额。
    *   [链接](https://github.com/github/copilot-cli/pull/1116)

*   **#988 [OPEN] chore(docs): add missing prefix to brew command**
    *   **文档**: 修复了 Homebrew 安装指令的拼写错误，补充了正确的命令前缀。
    *   [链接](https://github.com/github/copilot-cli/pull/988)

*   **#1609 [OPEN] Update instructions for adding permissions in PAT**
    *   **文档**: 更新了 PAT（个人访问令牌）权限配置的导航路径指引，明确了 "Copilot Requests" 权限的具体位置，降低用户配置门槛。
    *   [链接](https://github.com/github/copilot-cli/pull/1609)

*   *(其余 PR 多为垃圾广告或草稿提交，无实质性技术进展)*

## 5. 功能需求趋势

*   **模型与工作流优化**: 社区强烈要求更灵活的模型切换策略（计划 vs 执行）以及上下文管理（Issue #2792, #4183），以提升大模型调用的经济性和稳定性。
*   **非交互与自动化支持**: 对 ACP (Automatic Code Proposal) 协议的支持呼声很高，开发者希望在非交互模式下也能获取准确的 token/成本统计信息（Issue #4233, #4174）。
*   **平台兼容性**: Windows Terminal 显示乱码、macOS 密钥链锁冲突等跨平台渲染和认证问题成为近期焦点（Issue #4263, #4273）。
*   **工具链集成**: `/app` 命令定位不准以及对非 Git 版本控制系统的适配（Rewind 功能），反映了用户对深度集成本地开发环境的期待（Issue #4118, #1381）。

## 6. 开发者关注点

1.  **稳定性 (Stability)**: 僵尸进程泄漏 (`#4163`) 和 Plan Mode 权限回退 (`#4188`) 是当前最紧急的生产环境问题。
2.  **自动化体验 (Automation)**: 开发者希望 Autopilot 模式更“智能”，能在任务间无缝保持，并解决 `--acp` 模式下统计信息缺失的问题。
3.  **调试与反馈 (Observability)**: 社区希望能更清晰地看到 AI 调用的计费属性（`#4224`），以便进行精确的成本核算。
4.  **边缘场景兼容 (Edge Cases)**: 针对 WSL/tmux 嵌套终端、Windows 垂直分割窗、以及 macOS 混合签名单机环境的适配 bug 频发，是 QA 的重点关注区。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# 2026-07-28 Kimi Code CLI 社区动态日报

## 今日速览
今天社区聚焦于 **VSCode 扩展稳定性**（Issue #2563）和 **命令行钩子任务丢失**（Issue #2564/PR #2565）两大核心问题，修复计划正密集推进。同时针对 Windows 编码环境的兼容性改进成为另一开发焦点。

## 版本发布
过去 24 小时内无新版本发布（当前稳定版仍为 CLI v1.9.0 / VSCode Extension 0.6.4）。

## 社区热点 Issues
| ID | 标题 | 重要性说明 | 社区反应 |
|:---|:---|:---|:---|
| **#2563** | VS Code extension: approval prompts intermittently never render | 阻塞型 Bug：导致 Plan mode 和用户权限确认静默挂起或超时，直接阻断工作流。 | ⚠️ 高优先级新建 Issue，需快速干预 |
| **#2564** | fix(hooks): PostToolUse tasks collected by GC before completion | 严重数据完整性 Bug：异步钩子在执行前被垃圾回收器意外杀死，导致非确定性失败。 | 🔧 有开发者正在定位 Root Cause |
| **#1070** | Login failed: Cannot connect to host auth.kimi.com | 网络连通性问题：涉及认证服务可达性，影响新用户或重连场景。 | 📝 已关闭 (CLOSED) |
| **#2317** | [VSCode Extension] Plan mode file path not clickable in UX细节缺陷：降低 IDE 插件内使用的便捷体验。 | 💬 3 条讨论中 |

*(注：数据源仅提供 4 条最新 Issue，故列出全部)*

## 重要 PR 进展
| ID | 作者 | 摘要链接 | 解决内容 |
|:---|:---|:---|:---|
| **#2565** | LHMQ878 | [#2565](https://github.com/MoonshotAI/kimi-cli/pull/2565) | **修复钩子内存泄漏/回收问题**：通过保持强引用（Strong Reference）确保 `fire-and-forget` 钩子任务不被 GC 提前销毁，呼应 Issue #2564。 |
| **#2562** | lihailong00 | [#2562](https://github.com/MoonshotAI/kimi-cli/pull/2562) | **Prompt Cache 控制增强**：新增配置项允许禁用 Prompt Cache Key，优化特定 Provider 的缓存行为。 |
| **#2539** | lihailong00 | [#2539](https://github.com/MoonshotAI/kimi-cli/pull/2539) | **MCP 工具标准化**：生成 Moonshot API 兼容的工具别名，完善 Schema 对象类型支持。 |
| **#2561** | LHMQ878 | [#2561](https://github.com/MoonshotAI/kimi-cli/pull/2561) | **Windows 启动编码修复**：修复 Git Bash 环境下因 GBK 字符导致的 `UnicodeEncodeError`。 |
| **#2560** | LHMQ878 | [#2560](https://github.com/MoonshotAI/kimi-cli/pull/2560) | **Web Banner 编码修复**：修正 Windows 重定向 stdout 时的网页启动乱码崩溃问题。 |

## 功能需求趋势
1. **IDE 深度集成体验**：VSCode 插件的用户交互逻辑（如 Plan Mode 弹窗、文件路径点击率）是近期高频反馈区。
2. **跨环境健壮性**：对 Windows 本地编码（GBK/UTF-8）的适配显示出开发者关注多平台一致性。
3. **异步流程可靠性**：Hook 机制的任务生命周期管理暴露出并发控制上的技术债务。

## 开发者关注点
*   **痛点**：VSCode 插件的审批提示渲染故障（Intermittent stall）最令用户困扰；Hook 任务的静默丢弃难以排查。
*   **诉求**：期待官方尽快合并 Hook 引用修复（PR #2565）并排查插件端渲染逻辑；同时对 Windows 字符集修复表示欢迎。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode 社区动态日报 (2026-07-28)

## 1. 今日速览
今日 **OpenCode Desktop** 发布 **v1.18.7**，重点修复了 macOS 全屏标题栏及命令面板异常等桌面端问题。社区讨论高度集中于 **Azure/Kimi/Qwen 模型兼容性**、**TUI 与 Desktop 的功能差异（如 Undo）**以及 **MCP 协议 v2 SDK 的升级适配**，同时开发者们正通过多组 Refactor PR 重构 Session Controller 以优化架构。

---

## 2. 版本发布
*   **v1.18.7 (Desktop)**: 
    *   **Bugfix**: 移除 macOS 全屏时的多余标题栏内边距；修复命令面板条目在命令被遮蔽后错误重显的问题；为长列表项目选择器添加滚动条。
    *   **致谢**: 感谢社区贡献者 @david1gp。
    *   [查看 Release](https://github.com/anomalyco/opencode/releases/tag/v1.18.7)

---

## 3. 社区热点 Issues (Top 10)

1.  **#38830 [OPEN] AutoScroller plugin depends on Scroller plugin** - *5 评论*
    *   **重要性**: 核心插件依赖报错，直接影响滚动体验稳定性。
    *   **社区反应**: 新近打开，关注度高，需排查注册顺序或依赖声明。
    *   [链接](https://github.com/anomalyco/opencode/issues/38830)

2.  **#29688 [CLOSED] Bug: qwen3.7-max returns ModelError "not supported for format oa-compat"** - *3 评论*
    *   **重要性**: 重大模型兼容性问题，明确 `qwen3.7-max` 在 Zen/Go 端不兼容 OpenAI 格式。
    *   **社区反应**: 用户反馈直接导致调用失败，提示需调整 API 请求体或 endpoint。
    *   [链接](https://github.com/anomalyco/opencode/issues/29688)

3.  **#29200 [CLOSED] Invalid JSON/C causes "Unexpected server error" on startup** - *5 评论*
    *   **重要性**: 配置校验错误时给出的错误信息过于模糊（"Unexpected server error"），极大影响调试效率。
    *   **社区反应**: 高亮需求，期望提供具体的行号或错误字段定位。
    *   [链接](https://github.com/anomalyco/opencode/issues/29200)

4.  **#18302 [CLOSED] Multi-server: layout state not namespaced per server causes session loop after switching** - *4 评论*
    *   **重要性**: 多服务器切换时的状态隔离 Bug，导致会话恢复死循环。
    *   **社区反应**: 涉及复杂工作流（本地 Sidecar + 远程 Serve），影响生产力。
    *   [链接](https://github.com/anomalyco/opencode/issues/18302)

5.  **#29571 [CLOSED] Conversation permanently stuck after 'vision is not enabled' error from GitHub Copilot provider** - *6 评论* ⭐ (高 👍)
    *   **重要性**: 企业级用户（Copilot Org）遇到视觉功能限制后会话卡死，体验极差。
    *   **社区反应**: 获得 3 个赞，反映该问题对付费/组织用户影响严重。
    *   [链接](https://github.com/anomalyco/opencode/issues/29571)

6.  **#29660 [CLOSED] BUG: should allow "ask" in agents** - *3 评论*
    *   **重要性**: Agent 工具权限配置中的逻辑缺陷，`"bash": "ask"` 未被正确识别为有效指令。
    *   **社区反应**: 配合 Obsidian Vault Assistant 的配置截图，具象化了 Agent 策略的执行漏洞。
    *   [链接](https://github.com/anomalyco/opencode/issues/29660)

7.  **#39210 [CLOSED] BUG (Chinese)** - *2 评论*
    *   **重要性**: 新近反馈，用户描述“发 Prompt 无响应”，可能涉及对话轮次丢失或 Agent 调度挂起。
    *   **社区反应**: 虽评论少但反映了最基础的聊天功能异常。
    *   [链接](https://github.com/anomalyco/opencode/issues/39210)

8.  **#16962 [CLOSED] Clipboard copy not working over SSH (Mac-to-Mac)** - *6 评论* ⭐ (高 👍)
    *   **重要性**: 跨设备剪贴板同步失效，且特别发生在 Mac SSH 场景下。
    *   **社区反应**: 获得 2 个赞，是开发环境流畅度的关键痛点。
    *   [链接](https://github.com/anomalyco/opencode/issues/16962)

9.  **#29494 [CLOSED] [FEATURE]: please support siliconflow-cn/deepseek-ai/DeepSeek-V4-Pro** - *2 评论*
    *   **重要性**: 紧跟开源模型浪潮，请求支持最新的 DeepSeek-V4-Pro。
    *   **社区反应**: 代表用户对最新 SOTA 模型的渴求。
    *   [链接](https://github.com/anomalyco/opencode/issues/29494)

10. **#29794 [CLOSED] Horizontal jitter on /go page caused by LimitsGraph overflow** - *2 评论*
    *   **重要性**: UI 渲染细节问题（水平抖动），出现在 `/go` 监控页面。
    *   **社区反应**: 具体定位到 CSS 属性 `[data-slot="plot"]` 的定位冲突，利于快速修复。
    *   [链接](https://github.com/anomalyco/opencode/issues/29794)

---

## 4. 重要 PR 进展

1.  **#39247 [OPEN] feat(mcp): upgrade client SDK to v2**
    *   **内容**: 将 MCP 客户端 SDK 从 1.x 升级至 2.0.0-beta.5，支持无状态协商、分页及变更订阅。
    *   **意义**: 提升与现代 MCP 服务器的兼容性及性能。
    *   [链接](https://github.com/anomalyco/opencode/pull/39247)

2.  **#39233 / #39232 / #39231 / #39230 / #39229 / #39228 / #39227 [OPEN] Refactor(app): ... controller**
    *   **内容**: Brendonovich 提交的一系列重构 PR，涵盖建立 Session Controller、提取 Timeline/SidePanel/Provider Connection Controller 等。
    *   **意义**: 对 App 端逻辑进行模块化拆解，降低耦合，为新功能（如 v2 会话）铺路。
    *   [链接系列](https://github.com/anomalyco/opencode/pull/39233) (及其他同作者 PR)

3.  **#39240 [CLOSED] fix(core): align Meta system prompt** & **#39237 [CLOSED] fix(core): refresh Meta system prompt**
    *   **内容**: 更新 Meta 模型的系统提示词，删除过时的 `TodoWrite` 指南，工具名对齐 V2 规范。
    *   **意义**: 确保系统提示与当前模型能力及 API 文档保持一致。
    *   [链接 #39240](https://github.com/anomalyco/opencode/pull/39240) | [链接 #39237](https://github.com/anomalyco/opencode/pull/39237)

4.  **#39239 [CLOSED] fix(core): keep config root watches alive and ignore vendored trees**
    *   **内容**: 修复配置文件监视器的生命周期，并排除 vendored 目录，防止配置 reload 死循环。
    *   **意义**: 解决 audit 中发现的 Watch Pipeline 稳定性问题。
    *   [链接](https://github.com/anomalyco/opencode/pull/39239)

5.  **#39238 [OPEN] [contributor] fix(core): bound search tool execution**
    *   **内容**: 为交互式 `glob` 和 `grep` 工具增加 30 秒超时限制，避免无限搜索阻塞模型。
    *   **意义**: 增强工具调用的健壮性，防止资源耗尽。
    *   [链接](https://github.com/anomalyco/opencode/pull/39238)

---

## 5. 功能需求趋势
*   **模型生态扩展**: 持续请求支持最新模型（Kimi k3, DeepSeek-V4-Pro, Qwen3.7）及解决特定模型（Max, Free版）的不可见或格式兼容问题。
*   **IDE/Editor 集成深化**: 强烈建议集成 VS Code 内部浏览器元素到 Chat（Issue #28657），以及加强 Agent 能力（如允许 `"ask"`）。
*   **多环境与多服务器支持**: 关注 Nix 构建、SSH 剪贴板、多 Server 状态下布局状态的隔离问题。
*   **用户体验优化**: 去除无意义的动画加载进度线（Issue #21939），修复 Undo 仅回滚对话不回滚文件的不一致行为（Issue #29520）。

---

## 6. 开发者关注点
*   **配置错误诊断**: Issue #29200 指出配置解析错误时缺乏明确的错误位置和原因，是高频吐槽点。
*   **Agent 权限与控制**: Issue #29660 和 #21793 暴露了权限规则（permission.skill）执行不彻底的问题，开发者关心 Agent 的安全沙箱边界。
*   **平台特异性崩溃**: Windows 端 Sidecar 频繁崩溃（ACCESS_VIOLATION, Issue #29599）及 macOS SSH 剪贴板失效（Issue #16962）是需要跨平台团队优先解决的稳定性杀手。
*   **MCP 协议演进**: 随着 MCP v2 SDK 升级（PR #39247），开发者关注如何在新旧服务器间进行优雅降级和状态管理。

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# 📊 Pi 社区动态日报 (2026-07-28)

## 1. 今日速览
今日 PI 主要聚焦于 **多模型提供商兼容性修复**（特别是 Anthropic、Z.AI 和 OpenCode）及 **会话/扩展稳定性改进**。社区对 Copilot Enterprise 集成报错（Issue #6768）高度关注，且有大量 Issue 集中于性能优化（可见宽度缓存）、命令行体验（快捷键跳转）以及 API 标准规范对齐。

## 2. 版本发布
**无** 新版本发布。昨日及今日主要以维护性更新和功能修补为主。

## 3. 社区热点 Issues (Top 3 综合关注度)

*   **#6768 [OPEN] Compaction using Copilot Enterprise not possible**
    *   **状态**: 未解决 (Open)，高热度。
    *   **问题**: 使用 Copilot Enterprise 许可证进行上下文压缩时触发 `421 Misdirected Request` 错误。
    *   **社区反应**: 👍 12, 评论 14。这是目前最严重的功能阻塞问题，影响大模型企业的核心工作流。
    *   [查看 Issue](https://github.com/earendil-works/pi/issues/6768)

*   **#5263 [OPEN] Make in-session model and thinking-level changes ephemeral by default**
    *   **状态**: 未解决 (Open)。
    *   **问题**: 提议将模型和思维级别的修改默认设为“临时模式”，仅影响当前活跃会话，并引入显式的全局设置入口。
    *   **社区反应**: 👍 10, 评论 10。涉及用户体验的核心交互逻辑变革，反映用户对精细化控制的需求强烈。
    *   [查看 Issue](https://github.com/earendil-works/pi/issues/5263)

*   **#7198 [CLOSED] Markdown renderer crashes on nested email quotes**
    *   **状态**: 已关闭 (Closed)。
    *   **问题**: 渲染深度嵌套的邮件引文会导致调用栈溢出 (`RangeError`) 从而使进程崩溃。
    *   **重要性**: 涉及核心渲染器的稳定性，属于严重的 Bug 修复，已纳入修复队列。
    *   [查看 Issue](https://github.com/earendil-works/pi/issues/7198)

*(注：其余热门 Issue 如终端滚动 bug #5023、Z.AI token 配置错误 #7143 等亦显示开发者正密集处理底层与兼容性问题)*

## 4. 重要 PR 进展 (Top 10)

1.  **#7172 [CLOSED] fix(ai): send x-client-request-id on anthropic-messages**
    *   **内容**: 修复了 Anthropic 路径缺少 `x-client-request-id` 头的问题，解决了代理（如 CliProxyAPI）无法会话亲和性分组的问题。关联 Issue #7161。
    *   [链接](https://github.com/earendil-works/pi/pull/7172)

2.  **#7174 [OPEN] fix(ai): send max_tokens for Z.AI providers**
    *   **内容**: 修复 Z.AI 只识别 `max_tokens` 而忽略 `max_completion_tokens` 的问题，防止长上下文生成被截断。关联 Issue #7143。
    *   [链接](https://github.com/earendil-works/pi/pull/7174)

3.  **#7173 [CLOSED] fix(ai): rename OpenCode Zen Go display name to OpenCode Go**
    *   **内容**: 修正了 `opencode-go` 提供商显示名称的错误拼写，使其与实际命令输出一致。关联 Issue #7157。
    *   [链接](https://github.com/earendil-works/pi/pull/7173)

4.  **#7191 [CLOSED] feat(extensions): expose ctx.scopedModels to extensions**
    *   **内容**: 向扩展接口暴露了会话级的模型集合 (`ctx.scopedModels`)，方便构建模型选择器等外部工具。关联 Issue #7192。
    *   [链接](https://github.com/earendil-works/pi/pull/7191)

5.  **#7169 [CLOSED] fix(coding-agent): dedupe byte-identical context files**
    *   **内容**: 优化了文件加载逻辑，通过哈希值去重而非仅路径去重，避免在处理 Worktrees 或复杂目录结构时重复读取相同的 `AGENTS.md`。关联 Issue #7171。
    *   [链接](https://github.com/earendil-works/pi/pull/7169)

6.  **#7178 [CLOSED] feat(coding-agent): show status when toggling tool-output expansion**
    *   **内容**: 为工具输出展开/收起操作添加状态行提示（如 "Thinking blocks: visible"），提升 TUI 反馈一致性。关联 Issue #7180。
    *   [链接](https://github.com/earendil-works/pi/pull/7178)

7.  **#7163 [OPEN] feat: search index sqlite**
    *   **内容**: 引入基于 SQLite 的会话搜索索引功能（FTS5），旨在解决海量会话记录下的搜索性能瓶颈。
    *   [链接](https://github.com/earendil-works/pi/pull/7163)

8.  **#7081 [CLOSED] feat(ai): support Claude Opus 5 on Bedrock**
    *   **内容**: 增加了在 AWS Bedrock 上支持最新版本 Claude Opus 的功能，并修复了相关的错误消息显示逻辑。
    *   [链接](https://github.com/earendil-works/pi/pull/7081)

9.  **#6881 [OPEN] feat(ai): use provider-reported cost when responses include it**
    *   **内容**: 支持直接采用服务提供商返回的实际账单费用作为 `usage.cost`，提高了计费精度。
    *   [链接](https://github.com/earendil-works/pi/pull/6881)

10. **#7184 [CLOSED] fix(ai): strip multimodal media markers from tool results...**
    *   **内容**: 修复因结果中包含空图片标记 (`|image|`) 而导致模型 Tokenizer 崩溃的严重 Bug。该修复已在两个 PR (#7181, #7184) 中完成合并。
    *   [链接](https://github.com/earendil-works/pi/pull/7184)

## 5. 功能需求趋势
从 Issue 和 PR 的数量分布来看，社区当前的关注点集中在以下三大方向：
1.  **协议与标准化 (Standardization)**: 大量 Issue 关于不同提供商（Anthropic, Z.AI, OpenCode）对标准参数（如 `max_tokens`, `x-client-request-id`）支持不一致，显示开发者致力于统一 API 适配层。
2.  **稳定性与容错 (Stability)**: 针对崩溃（Markdown 解析、Token 处理）、死锁（Copilot 配置）和无响应（空内容导致的 Fork 崩溃）的修复占据主导地位。
3.  **扩展性与权限管理 (Extensibility & Auth)**: 请求提供更细粒度的扩展钩子（`pre_response`）、Scoped Models 暴露以及 OAuth 替代方案，表明用户希望更深地定制 AI Agent 行为。

## 6. 开发者关注点与痛点
*   **环境依赖与配置陷阱**: 许多 Issue (#7170, #7152) 源于证书获取、凭证过程 (`credential_process`) 以及 symlink 目录解析导致的扩展加载失败。开发者正花费大量精力增强配置的鲁棒性。
*   **高性能渲染瓶颈**: 针对大 Buffer 渲染时的 CPU 消耗问题（Issue #7196），社区提出了使用 LRU 替换 FIFO 缓存策略的建议，显示出对 TUI 性能优化的重视。
*   **跨平台一致性**: macOS 上的快捷键失效（Issue #7164）以及不同终端模拟器下的行为差异是持续存在的挑战。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code 社区动态日报（2026-07-28）

## 今日速览
Qwen Code SWE-bench 验证数据集测试完成，但模型处于隔离状态（QUARANTINED），表明基准表现未达预期。主分支 CI 出现大量 E2E 测试失败，共提交了多起自动化故障报告。同时，社区聚焦于外部内存集成、技能上下文生命周期管理及动态工作流 TUI 体验优化等核心议题。

---

## 版本发布
过去 24 小时内暂无新版本发布。最新可追踪的非生产版预发布包括 `dsw-manual-poc-20260727-2` 及 `Benchmark-Qwen-Ref: v0.20.0-nightly.20260722.b98306b7e`，用于手动基准评测。

---

## 社区热点 Issues (精选 10)

1. **#7585 [proposal] Add a direct external context provider profile**
   - **重要性**: 提议为 Qwen CLI 进程提供直接获取外部知识库的能力，实现管理员绑定且无需修改核心代码的上下文集成。
   - **关注度**: 最高（9 评论），涉及 MCP 与扩展性范畴，是未来企业级集成的关键设计。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7585)

2. **#7449 [proposal(memory)] Define an enterprise external-memory integration profile**
   - **重要性**: 旨在定义厂商中立的“企业外部内存集成配置文件”，解决存储层解耦问题，支持增量兼容性测试。
   - **关注度**: 高（6 评论），与 #7585 互补，侧重于标准化接口文档而非纯功能实现。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7449)

3. **#6762 [Feature Request] Skill Context Lifecycle Management**
   - **重要性**: 指出当前 SKILL.md 内容永久滞留导致上下文膨胀的问题，请求增加卸载、压缩或清理机制以提升长会话性能。
   - **关注度**: 中（5 评论），属于核心 Token 管理与 Session 管理范畴。
   - [链接](https://github.com/QwenLM/qwen-code/issues/6762)

4. **#7167 Fleet Shepherd Dashboard**
   - **重要性**: 自动维护的仪表盘显示流水线状态异常（如 `syncs: 0`, `dispatches: 0`），反映自动化运维工具链可能存在瓶颈或监控死区。
   - **关注度**: 关注点在于 CI/CD 流水线的健康度追踪。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7167)

5. **#7687 [feat(dingtalk)] support outbound image delivery**
   - **重要性**: 完善钉钉通道的 Agent 能力，支持发送本地图片（如截图或图表），而不仅是文件路径引用，提升可视化协作体验。
   - **关注度**: 中等（4 评论），属于通讯渠道的功能增强。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7687)

6. **#7832 [priority/P1] YOLO mode: mid-stream socket close is not retried...**
   - **重要性**: P1 级严重 Bug，YOL0 模式下的长代码生成因 TCP 连接在 SSE 流中断后未被重试而直接失败，影响大文件产出稳定性。
   - **关注度**: 高（3 评论），直接影响开发者在高延迟场景下的生产效率。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7832)

7. **#7831 [priority/P2] Repeated ECONNRESET on streaming responses when context exceeds ~150k tokens**
   - **重要性**: 长上下文（>150k token）流式响应时频繁发生 `ECONNRESET` 错误，暴露出 API 网关在面对超长输入时的连接稳定性缺陷。
   - **关注度**: 中等（3 评论），关联 Latency 与 Core 模块的健壮性。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7831)

8. **#7841 [priority/P2] Quota-exhausted 429s retry silently...**
   - **重要性**: 当后端模型配额耗尽返回 429 时，系统将其视为临时限流静默重试而非致命错误并向用户无感，导致资源浪费且无法及时止损。
   - **关注度**: 中等（3 评论），涉及核心错误处理逻辑的用户反馈透明度。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7841)

9. **#7835 sub agent ask user questions but user has no way to answer**
   - **重要性**: 子代理询问问题时，主代理未收集并转发给终端用户，造成死锁。这揭示了多智能体架构（Sub-agent vs Main Agent）间的通信协调机制缺失。
   - **关注度**: 中等（3 评论），属于 Workflows/Subagents 类重要逻辑漏洞。
   - [链接](https://github.com/QwenLM/qwen-code/issues/7835)

10. **#7755 / #7889 / #7878 ... 主 CI 批量失败**
    - **重要性**: 多起 Issue 均标记为主分支 E2E 测试失败，显示近期代码合并可能引入了破坏性回归，急需修复以恢复分支稳定性。
    - **关注度**: 密集的关注点，是项目稳定性的紧急警报。
    - [链接列表示例](https://github.com/QwenLM/qwen-code/issues/7755)

---

## 重要 PR 进展 (精选 10)

1. **#7892 [feat/cli] redesign Dynamic Workflow execution console**
   - **内容**: 将动态工作流的详情视图重构为紧凑的执行控制台（Execution Console），分离运行头、阶段条和实时进度，使复杂流程一目了然。
   - **状态**: Open，与 Issue #7887/7890 对应，旨在解决 TUX 阅读性问题。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7892)

2. **#7891 [feat(channels)] expose loop tools in daemon sessions**
   - **内容**: 允许守护进程管理的通道会话暴露现有的通道循环工具（Loop Tools），使用户能通过自然语言创建、取消周期性任务，实现真正的主动式自动化。
   - **状态**: Open，提升 Daemon 模式的交互能力。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7891)

3. **#7731 [feat/web-shell] add git branch picker, commit dialog, and create PR flow**
   - **内容**: 在 Web Shell 中加入类似 IntelliJ 的分支选择器弹出框，支持搜索过滤、标签查看以及完整的提交流程，极大丰富了源码管理能力。
   - **状态**: Open，显著改善 Web Shell 端的 Git 体验。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7731)

4. **#7484 [fix(core)] bridge tool-result images for text-only models**
   - **内容**: 解决纯文本模型无法理解工具执行中发现的图片的问题，建立了统一的图像路由阶段，确保所有工具结果（含图像）能被正确传递和处理。
   - **状态**: Open，弥补了视觉识别与文本模型之间的桥梁缺口。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7484)

5. **#7894 [feat] Gate session writer lease behind opt-in**
   - **内容**: 引入实验性功能 `experimental.sessionWriterLease`，通过显式的重启配置选项来启用跨进程写围栏（Write Fencing），保障并发写入的安全性。
   - **状态**: Open，针对 ACP 和守护进程的高级并发控制特性。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7894)

6. **#7821 [fix(daemon)] harden Todo Stop Guard continuations**
   - **内容**: 原子化地改进 Todo Stop Guard 的状态机延续协议，为桥接组件增加所有者范围声明/释放协议，增强调度器的可靠性。
   - **状态**: Open，底层守护进程的稳定性加固。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7821)

7. **#7837 [fix(cli)] coordinate terminal teardown**
   - **内容**: 为交互式会话提供同步、幂等的终端销毁流程，涵盖正常退出及各种信号（SIGINT, SIGTERM），确保资源正确清理且不丢失退出码。
   - **状态**: Open，CLI 端口的优雅关闭修复。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7837)

8. **#7859 [feat(web-shell)] add native Live Voice**
   - **内容**: 为 macOS Web Shell 原生支持 Live Voice 体验，通过按下 Command 键两次即可唤起语音对话，无需离开应用环境。
   - **状态**: Open，移动端与桌面端交互的新尝试。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7859)

9. **#7888 [feat] robust ripgrep**
   - **内容**: 提高 Ripgrep 运行时可靠性，区分真正的“无匹配”结果与线程失败；针对 `EAGAIN` 错误添加单线程重试路径，减少误报。
   - **状态**: Open，增强文件检索工具的信噪比。
   - [链接](https://github.com/QwenLM/qwen-code/pull/7888)

10. **#7792 [feat(ci)] Deduplicate E2E failure issues by commenting on existing issue**
    - **内容**: 修改 CI 工作流，不再为每次提交重复创建失败的 Issue，而是先检查是否存在相同 SHA 的旧 Issue 并进行评论，有效清理了 Issues 列表噪音。
    - **状态**: Open，针对前述大量 Issue #7xxx 混乱局面的治理措施。
    - [链接](https://github.com/QwenLM/qwen-code/pull/7792)

---

## 功能需求趋势

基于 Issues 的类别标签（Category & Scope），社区关注点呈现以下趋势：

*   **深度集成与生态扩展 (`integration`, `extensions`, `mcp`)**：
    *   对外部上下文（External Context）、企业内存 Profile 的关注度最高，显示开发者希望打破本地限制，接入企业知识图谱或私有数据库。
    *   对钉钉、飞书、微信等 IM 通道的图片分发和 GitHub Notification 路由功能的频繁迭代，说明“作为聊天机器人的代码助手”定位非常坚实。

*   **性能与扩展性 (`performance`, `long-context`, `token-management`)**：
    *   关于 150k+ Token 上下文崩溃（ECONNRESET）和技能上下文生命周期管理（Skill Context Lifecycle）的报告，反映出随着模型变大，**上下文窗口管理**已成为新的性能瓶颈和优化重点。

*   **UX 与 Terminal Experience (`tui`, `terminal-ux`, `components`)**：
    *   多个 Issue 围绕 Terminal UI (TUI) 展开，特别是动态工作流的可视化展示（Issue #7887/#7890）和 Web Shell 的 Voice/Branch picker，表明团队致力于将复杂的后台操作简化为可视化的终端体验。

*   **稳定性与 DevOps (`ci-cd`, `testing`, `sdk`)**：
    *   大量 Issues 集中于 E2E Test failures，显示出在快速迭代过程中，**主分支回归测试**面临巨大压力，自动化治理（如 PR #7792）变得尤为重要。

---

## 开发者关注点总结

根据 Issue 内容的分析，当前开发者群体最痛的点集中在以下三个方面：

1.  **流式传输与大文件生成的健壮性**：
    *   在 YOLO 模式下生成长代码（>500行）或处理长序列上下文时，Socket 容易意外断开且缺乏完善的重试机制（Issue #7832, #7831）。这直接阻碍了大型项目的自动化代码生成任务。

2.  **多 Agent 架构下的交互阻塞**：
    *   当工作流中启用了子代理（Sub-agent）并与用户互动时，主代理未能有效地捕获子代理的问题并转递给用户，导致“死锁”状态（Issue #7835）。这对复杂自动化流程的使用体验造成了严重影响。

3.  **错误提示的清晰度与配额管理**：
    *   面对明确的 `Quota Exhausted`（配额耗尽）API 错误，系统目前表现得过于“温柔”，仅将其当作普通速率限制进行静默重试，而不是立即报错止损，导致用户困惑且浪费算力（Issue #7841）。

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI 社区动态日报 (2026-07-28)

## 1. 今日速览
今日社区活跃度持续高涨，共处理 Issues 20 条与 PR 30 条。核心进展聚焦于 **v0.9.2 版本收尾**（文档、技能包路由）、**Windows CRLF 行尾修复**（解决 `edit_file` 工具故障）以及**性能优化与代码质量清理**。开发者在远程工作流支持（Remote Mode）和成本透明化上反馈强烈，为下一迭代指明方向。

## 2. 版本发布
过去 24 小时内无新版本 Release 通知。目前主要精力集中在 v0.9.2 候选版本的集成、文档完善及 Bug 修复中，主分支（main）正逐步整合相关功能分支。

## 3. 社区热点 Issues
| ID | 类型 | 标题摘要 | 关注度/重要性分析 | GitHub 链接 |
|----|------|----------|------------------|-------------|
| **#4042** | CLOSED/BUG+ENG | Environment-level tool sandboxing for sub-agents | **高**。涉及子代理执行上下文的核心安全性控制（工具沙箱），评论数达 20，是本周讨论最深入的技术决策问题之一。该issue确认了 `-disallowed-tools` 等参数在不同执行环境下的强制策略落地。 | [Issue #4042](https://github.com/Hmbown/CodeWhale/issues/4042) |
| **#998** | OPEN/ENHANCEMENT | 文案展示不全 | **中**。UI 层面的用户体验建议，希望通过鼠标悬停提示展示完整文案。虽然看似简单，但体现了社区对界面细节打磨的关注。 | [Issue #998](https://github.com/Hmbown/CodeWhale/issues/998) |
| **#4526** | CLOSED/DOCUMENTATION | Request to add dedicated endpoint configurations for StepFun Plan | **中**。反映了多模型提供商接入的标准化需求。StepFun 提供了不同订阅计划的专用 API 端点，用户希望 TUI 能更灵活地配置以适应厂商差异。 | [Issue #4526](https://github.com/Hmbown/CodeWhale/issues/4526) |
| **#3983** | CLOSED/BUG+DOC | v0.9.2 Runtime: make current Work state model-visible on parent turns | **中**。针对工作流运行时（Runtime）的状态可见性改进，确保父级对话轮次能清晰获取子代理的工作状态，对于调试复杂的 Agent 编排至关重要。 | [Issue #3983](https://github.com/Hmbown/CodeWhale/issues/3983) |
| **#4698** | CLOSED/BUG+DOC | v0.9.2: Complete default skill-pack routing metadata... | **中**。属于发布前的收尾工作，完善默认技能包的路由元数据，降低用户上手门槛，确保开箱即用体验。 | [Issue #4698](https://github.com/Hmbown/CodeWhale/issues/4698) |
| **#2342** | OPEN/ENHANCEMENT | 输出内容中的文件，能不能支持点击后打开预览 | **低/UX**。轻量级的 UX 增强请求，期望在 TUI 中直接通过交互操作文件，提升工作流的流畅度。 | [Issue #2342](https://github.com/Hmbown/CodeWhale/issues/2342) |
| **#4764** | OPEN/BUG | `edit_file` tool failed to edit CRLF files on Windows | **高**。严重的跨平台兼容性 Bug。在 Windows 环境下，针对使用 CRLF 换行的文件进行编辑搜索时失效，严重影响 Windows 用户的日常开发体验。后续有 PR #4942 跟进修复。 | [Issue #4764](https://github.com/Hmbown/CodeWhale/issues/4764) |
| **#4785** | OPEN/DOCUMENTATION | Dead-code sweep: 464 #[allow(dead_code)] attributes are hiding drift | **高**。代码质量问题预警。过多的 `#[allow(dead_code)]` 属性掩盖了编译器无法检测到的漂移（Drift），影响长期可维护性。开发团队已着手清理（见 PR #4938）。 | [Issue #4785](https://github.com/Hmbown/CodeWhale/issues/4785) |
| **#4797** | CLOSED/BUG | Renovate cost: two pricing systems, unpriced cache writes... | **中**。成本计算逻辑的审计与重构。指出了旧版计费系统中存在的冗余和低估问题，旨在提供更精确的费用追踪报告，这对于企业级用户尤为重要。 | [Issue #4797](https://github.com/Hmbown/CodeWhale/issues/4797) |
| **#3897** | CLOSED/PERF | perf(tui): streaming re-parses the whole growing message every chunk... | **高**。关键性能瓶颈。TUI 在渲染流式消息时存在 O(N²) 的 Markdown 重解析问题，导致长文本输入时界面卡顿。这是影响极致顺滑体验的核心技术债。 | [Issue #3897](https://github.com/Hmbown/CodeWhale/issues/3897) |

## 4. 重要 PR 进展
*   **#4942 [OPEN] fix(tools): preserve CRLF edits**: 修复了 Issue #4764 中提到的 Windows CRLF 文件编辑问题。通过在 LF 归一化视图下进行匹配，并将替换后的新线尾映射回原始字节，完美解决了跨平台的文件编辑兼容性。 ([PR #4942](https://github.com/Hmbown/CodeWhale/pull/4942))
*   **#4940 [CLOSED] feat(media): executable capture harness...**: 为实现 Issue #4906“录制真实 Codewhale 会话”提供自动化录制工具的脚手架。标志着官方开始重视用动态演示代替静态图文来展示产品特性。 ([PR #4940](https://github.com/Hmbown/CodeWhale/pull/4940))
*   **#4938 [CLOSED] chore: land the bounded dead-code slice and add a budget ratchet...**: 针对 Issue #4785 的代码质量清理行动。引入了一个 CI 闸（ratchet），防止新的无用属性继续增加，从流程上遏制代码漂移风险。 ([PR #4938](https://github.com/Hmbown/CodeWhale/pull/4938))
*   **#4935 [CLOSED] fix(tui): stop the ambient jellyfish reading as a face...**: 细微的美学修复。修正了 TUI 背景中“水母”图形的绘制使其不被误读为抽象的面孔，保持了界面的沉浸感和整洁性。 ([PR #4935](https://github.com/Hmbown/CodeWhale/pull/4935))
*   **#4937 [OPEN] fix(tui): finalize stale shell transcript cells**: 优化后台 Shell 任务结束后的 UI 状态显示。将原本仍在转圈等待的“幽灵”状态更新为静态结果，避免了混淆，提升了状态可视化的准确性。 ([PR #4937](https://github.com/Hmbown/CodeWhale/pull/4937))
*   **#4912 [CLOSED] feat(web): v0.9.2 docs guide/vocabulary...**: 同步前端网站文档体系，增加了词汇表（vocabulary）和引导路径（getting-started path），旨在构建更完善的新手指引生态。 ([PR #4912](https://github.com/Tmbown/CodeWhale/pull/4912))
*   **#4928 [CLOSED] feat(tui): add thinking_default_expanded setting**: 实现了 Issue #4925 的需求，新增设置项让用户可以默认展开思考块（Thinking Blocks），特别方便了 SSH/tmux 环境下按键冲突的用户。 ([PR #4928](https://github.com/Hmbown/CodeWhale/pull/4928))
*   **#4910 [OPEN] docs: sanity check — is there a deterministic verification surface be...**: 一次文档风格或架构的探讨性讨论（草稿），显示了开发团队在进行大规模重构时对概念清晰度和确定性的严谨态度。 ([PR #4910](https://github.com/Hmbown/CodeWhale/pull/4910))
*   **#4929 [CLOSED] fix(acp): preserve numeric JSON-RPC IDs for avante.nvim compatibility**: 修复了与 `avante.nvim` Neovim 插件兼容性的 Bug，保留了 JSON-RPC 请求 ID 的数字类型而非转换为字符串，体现了对生态集成的重视。 ([PR #4929](https://github.com/Hmbown/CodeWhale/pull/4929))
*   **#4467 [CLOSED] Feat/opencode zen provider**: 新增了对 OpenCode Zen 模型提供商的支持，包括特定认证头处理和费率策略完善，进一步丰富了模型选择库。 ([PR #4467](https://github.com/Hmbown/CodeWhale/pull/4467))

## 5. 功能需求趋势
通过分析社区提交的 Issues，可以提炼出以下三个主要关注方向：
1.  **跨平台与本地化深度适配**：从 `#4764` (Windows CRLF) 和 `#998` (UI 文案截断) 等反馈看，开发者对产品在 Windows 环境的稳定性及多语言界面细节有着极高的要求。
2.  **Agent Workflows 的可控性与透明度**：关于 `#4042` (工具沙箱限制)、`#4924` (Fleet 准入规则) 和 `#4797`/`#4939` (费用拆解) 的热烈讨论，显示出专业用户需要更强的权限隔离机制和透明的计费账单，以便在企业环境中安全、合规地使用大模型代理。
3.  **可视化体验与效率优化**：用户对 TUI 的操作流畅度（`#3897` 性能问题）和信息呈现方式（`#2342` 文件预览、`#4930` 终端键位干扰）非常敏感，期待获得更高效、直观的原生终端 IDE 体验。

## 6. 开发者关注点总结
当前开发者群体的痛点主要集中在三类：**基础工具链在复杂环境下的稳定性**（如 Windows 换行符导致的 `edit_file` 崩溃）、**长时间运行时的性能开销**（O(N²) 渲染卡顿），以及**高级工作流管理的精细度不足**（如思考块的展开逻辑、费用统计颗粒度）。社区热度的集中表明，团队在维护代码健康度的同时，需继续投入资源优化核心渲染引擎并确保跨操作系统的一致性。

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*