# AI CLI 工具社区动态日报 2026-09-07

> 生成时间: 2026-09-07 04:04 UTC | 覆盖工具: 10 个

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
**日期：2026-09-07**

---

## 1. 生态全景

2026年Q3的AI CLI工具生态已进入**成熟分化期**：头部工具（Claude Code、Copilot CLI、Gemini CLI、Pi）进入稳定性精修阶段，聚焦上下文管理、多代理协作与跨平台兼容性；新锐工具（Qwen Code、Kimi Code CLI）通过差异化功能（Web Shell、Plan Mode）抢占细分场景；同时，**Windows平台适配、企业级认证合规、成本控制透明度**成为全行业共性挑战。工具竞争从"能力堆叠"转向"可靠性与体验竞争"。

---

## 2. 各工具活跃度对比

| 工具 | 热点Issues | 新增PR | Closed PR | Release | 响应速度 |
|------|-----------|--------|-----------|---------|---------|
| **Claude Code** | 10 | 12 | 8 | ❌ 无 | 中等 |
| **OpenAI Codex** | 10 | 10 | 10 | ❌ 无 | 快 |
| **Gemini CLI** | 10 | 11 | 7 | ✅ nightly | 中等 |
| **GitHub Copilot CLI** | 11 | 1 | 2 | ❌ 无 | 慢 |
| **Kimi Code CLI** | 4 | 2 | 0 | ❌ 无 | 中等 |
| **Pi** | 45（当日大量关闭） | 9 | 7 | ❌ 无 | ⭐ 极快 |
| **Qwen Code** | 10 | 9 | 1 | ✅ preview | 中等 |
| **DeepSeek TUI** | 12 | 11 | 6 | ❌ 无 | ⭐ 极快 |
| **Grok Build** | 0 | 0 | 0 | ❌ 无 | 停滞 |

> 注：Pi与DeepSeek TUI当日Issue/PR大量关闭，反映核心开发者高参与度；Copilot CLI PR更新极少，可能依赖官方内部迭代节奏。

---

## 3. 共同关注的功能方向

| 方向 | 涉及工具 | 具体诉求 |
|------|---------|---------|
| **上下文管理优化** | Claude Code、Gemini CLI、DeepSeek TUI | 压缩阈值可配置、压缩后规则保留、Autocompact抖动修复、CRLF文件导致全量diff浪费token |
| **跨平台稳定性** | Codex、Gemini CLI、Copilot CLI、DeepSeek TUI | Windows路径分隔符/CRLF兼容、WSL2内存泄漏、Wayland浏览器代理失败、macOS符号链接glob失效 |
| **多代理/子代理协作** | Gemini CLI、Qwen Code、DeepSeek TUI | 子代理状态管理、模型选择按任务切换、Fleet交付物展示、代理挂起/误报成功问题 |
| **企业级认证与合规** | Claude Code、Gemini CLI、Copilot CLI | CVP批准组织仍被拦截、Workspace认证失败阻断登录、BYOK模式prompt caching静默失效导致成本飙升 |
| **MCP工具链集成** | Gemini CLI、Copilot CLI、DeepSeek TUI | 工具名截断碰撞、OAuth Token跨会话复用、登录流程改进、连接状态可见性 |
| **成本透明与优化** | Copilot CLI、Pi | BYOK模式下prompt caching失效导致5倍成本增长、Provider实际费用显示、配额消耗异常 |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|---------|---------|---------|
| **Claude Code** | 上下文压缩质量、插件生态、安全合规 | 企业开发者、Anthropic生态用户 | 强调Memory.md与长期会话管理，插件市场机制 |
| **OpenAI Codex** | worktree管理、远程SSH集成、语音功能 | VS Code用户、远程开发场景 | TUI优先，强化项目级会话管理与多worktree支持 |
| **Gemini CLI** | 子代理可靠性、AST感知代码理解、沙箱安全 | 谷歌生态用户、多代理工作流需求者 | 强调Subagent状态机与确定性行为，探索AST优化 |
| **GitHub Copilot CLI** | ACP模式权限审批、BYOK成本可控性 | GitHub Enterprise用户、已有Copilot订阅企业 | 深度集成GitHub生态，ACP模式为差异化特性 |
| **Kimi Code CLI** | 远程会话续接、Plan模式控制、跨工具互操作 | 中文用户、多工具混用场景 | 轻工具策略，聚焦工作流连续性需求 |
| **Pi** | 跨Provider容灾降级、扩展API开放、成本透明 | 多模型用户、扩展开发者 | 开源核心，快速迭代，强调Provider无关性与扩展性 |
| **Qwen Code** | Web Shell可视化、多Agent Mesh架构 | 中文用户、团队协作场景 | Web Shell为核心入口，推进持久化多Agent协作框架 |
| **DeepSeek TUI** | Fleet子代理管理、TUI可配置性、MCP工具链 | Rust生态用户、深度定制需求者 | 高迭代速度，架构级重构（CodeWhale TUI Crate Decomposition） |

---

## 5. 社区热度与成熟度

| 维度 | 高热度/快速迭代 | 中等热度/稳定期 | 低热度/停滞 |
|------|----------------|----------------|-------------|
| **工具** | Pi、DeepSeek TUI、Qwen Code | Claude Code、Gemini CLI、Codex | Copilot CLI（PR少）、Kimi Code CLI |
| **特征** | Issue当日大量关闭、核心开发者直接参与、周级nightly发布 | 稳定release节奏、社区反馈集中但响应周期较长 | 依赖内部迭代、公开PR极少、社区自驱为主 |
| **成熟度判断** | 处于**快速成长期**，产品形态尚未定型 | 处于**成熟稳定期**，聚焦体验精修 | 可能处于**战略观望期**或内部封闭开发 |

> **Pi** 的社区活跃度异常突出（45 Issues/9 PRs/当日大量关闭），反映其开源策略成功吸引贡献者；**DeepSeek TUI** 同样呈现高响应速度，创始人直接参与方向指导。

---

## 6. 值得关注的趋势信号

### 6.1 多代理协作成为必争之地
Gemini CLI（Subagent状态机修复）、Qwen Code（多Agent Mesh准入架构）、DeepSeek TUI（Fleet子代理体系）均在此方向投入。开发者需关注：**代理间通信可靠性、任务分发策略、成本隔离机制**将成为下一代CLI的核心竞争力。

### 6.2 Windows平台仍是"洼地"
Codex、Gemini CLI、Copilot CLI、DeepSeek TUI均报告Windows特异性问题（路径分隔符、CRLF、bash兼容、MSSQL python stub）。**Windows开发者体验**是当前行业普遍短板，预计未来半年各工具将集中投入跨平台适配。

### 6.3 成本透明度从"锦上添花"变为"核心诉求"
Copilot CLI的BYOK prompt caching失效导致5倍成本增长、Pi推动Provider实际费用显示，反映用户对**隐性成本**的敏感度显著提升。工具方需提供明确的token消耗、缓存命中率、配额使用等可观测能力。

### 6.4 企业级合规摩擦持续存在
Claude Code的CVP批准组织仍被拦截、Gemini CLI的企业Workspace认证失败，表明**身份验证与权限管理**在企业部署场景中仍是主要卡点。建议企业用户在选型时重点测试CVP/SSO集成稳定性。

### 6.5 上下文压缩质量直接影响模型行为一致性
Claude Code（压缩后规则丢失）、Gemini CLI（CRLF导致全量diff）、DeepSeek TUI（context pressure warning被绕过）均暴露压缩环节的可靠性风险。**可配置压缩阈值、压缩后行为规则保留**是社区高频需求，值得工具方优先解决。

### 6.6 开源策略决定社区活力
Pi与DeepSeek TUI的高活跃度与其开源模式直接相关；Copilot CLI与Kimi Code CLI的社区自驱特征反映其开源程度有限。**开源程度与社区响应速度呈正相关**，开发者可据此评估工具长期演进的可持续性。

---

*报告生成时间：2026-09-07 | 数据来源：各工具GitHub社区动态*

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告
**数据截止：2026-09-07 | 来源：anthropics/skills**

---

## 1. 热门 Skills 排行

| 排名 | PR | Skill 名称 | 功能简述 | 状态 | 热度 |
|:---:|:---|:---|:---|:---|:---|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | skill-creator 评估修复 | 修复 `run_eval.py` 的 recall 恒为 0% 的致命 bug（10+ 独立复现），该 bug 导致描述优化循环在噪声上训练 | 🔓 Open | 高（关联 Issue #556） |
| 2 | [#1628](https://github.com/anthropics/skills/pull/1628) | Hivemind 多智能体编排 | 让 Claude Code 作为唯一规划者，将机械工作委托给免费的 opencode 无头 worker，降低昂贵模型的上下文消耗 | 🔓 Open | 高（主题新颖） |
| 3 | [#514](https://github.com/anthropics/skills/pull/514) | document-typography | 修复 AI 生成文档的排版问题：孤行/寡行、编号错位，覆盖所有 Claude 生成的文档 | 🔓 Open | 中 |
| 4 | [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns | 全面测试 Skill：覆盖测试哲学（测试奖杯）、单元测试 AAA 模式、React 组件测试（Testing Library）、端到端测试 | 🔓 Open | 中 |
| 5 | [#486](https://github.com/anthropics/skills/pull/486) | odt | OpenDocument 格式（.odt/.ods）创建、填充、读取与 HTML 转换，支持 LibreOffice 生态 | 🔓 Open | 中 |
| 6 | [#1627](https://github.com/anthropics/skills/pull/1627) | buffer-api | Buffer GraphQL API 的跨 Agent 社交排程 Skill，支持账户发现、帖子创建与调度 | 🔓 Open | 中 |
| 7 | [#1367](https://github.com/anthropics/skills/pull/1367) | self-audit | 交付前自检 Skill：机械验证（文件存在性）+ 四维度推理质量门禁 | 🔓 Open | 中 |
| 8 | [#568](https://github.com/anthropics/skills/pull/568) | servicenow | ServiceNow 平台全栈 Skill：ITSM/ITOM/FSM/SecOps/CSDM 及 IntegrationHub | 🔓 Open | 中 |

---

## 2. 社区需求趋势（从 Issues 提炼）

| 需求方向 | 代表 Issue | 核心诉求 |
|:---|:---|:---|
| **🔒 安全与信任治理** | [#492](https://github.com/anthropics/skills/issues/492)（43 评） | 社区 Skill 冒充官方 `anthropic/` 命名空间，存在信任边界滥用风险 |
| **🏢 组织级协作共享** | [#228](https://github.com/anthropics/skills/issues/228)（8 👍） | 团队内一键共享 Skill，替代手动下载-上传的繁琐流程 |
| **🧪 测试与质量门禁** | [#723](https://github.com/anthropics/skills/pull/723), [#1385](https://github.com/anthropics/skills/issues/1385) | 测试模式 Skill + 推理质量门禁流水线（校准→对抗审查→交付验证） |
| **📄 文档/Office 处理增强** | [#538](https://github.com/anthropics/skills/pull/538), [#541](https://github.com/anthropics/skills/pull/541), [#1734](https://github.com/anthropics/skills/pull/1734) | PDF/DOCX 大小写敏感修复、修订标记 ID 冲突修复、孤立评论检测 |
| **⚡ 上下文窗口优化** | [#1487](https://github.com/anthropics/skills/issues/1487), [#1329](https://github.com/anthropics/skills/issues/1329) | claude-api Skill 一次性注入 ~156k tokens；提议 compact-memory 符号化状态压缩 |
| **🤖 多智能体/Agent 编排** | [#1628](https://github.com/anthropics/skills/pull/1628), [#412](https://github.com/anthropics/skills/issues/412) | 低成本多 Agent 调度 + Agent 治理（策略执行/审计追踪） |
| **🐧 Windows 兼容性** | [#1099](https://github.com/anthropics/skills/pull/1099), [#1050](https://github.com/anthropics/skills/pull/1050) | subprocess 管道读取、`claude.cmd` 调用、YAML 解析等 Windows 专项修复 |

---

## 3. 高潜力待合并 Skills

以下 PR 讨论活跃、问题明确，且对应 Issues 有社区复现，近期合并概率较高：

| PR | 标题 | 潜力理由 |
|:---|:---|:---|
| [#1298](https://github.com/anthropics/skills/pull/1298) | fix(skill-creator): run_eval.py recall 0% | 阻塞 skill-creator 核心工作流，Issue #556 有 7 👍，修复后直接影响 Skill 质量 |
| [#1628](https://github.com/anthropics/skills/pull/1628) | Hivemind: Zero-Cost Multi-Agent Orchestration | 直击成本痛点，概念清晰，多 Agent 编排是社区高频诉求 |
| [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns | 测试是全栈开发刚需，覆盖完整且结构清晰 |
| [#1367](https://github.com/anthropics/skills/pull/1367) | self-audit | 质量门禁是 Skill 可靠交付的关键保障，与 Issue #1385 呼应 |
| [#486](https://github.com/anthropics/skills/pull/486) | odt | 补全开源文档格式支持，ODF 是 ISO 标准，需求明确 |
| [#514](https://github.com/anthropics/skills/pull/514) | document-typography | 排版质量是用户高频痛点，修复成本低、覆盖面广 |

---

## 4. Skills 生态洞察

> **当前社区最集中的诉求是：在确保 Skill 安全边界（[#492](https://github.com/anthropics/skills/issues/492)）的前提下，快速补齐测试验证、文档处理、多智能体编排三大能力支柱，同时解决 Windows 兼容性与上下文窗口效率等基础体验问题。**

---



# Claude Code 社区动态日报
**日期：2026-09-07**

---

## 1. 今日速览

今日无新版本发布，社区焦点集中在安全合规阻塞（CVP 已批准组织仍被拦截）和长期未解决的稳定性问题（挂起/冻结、Autocompact 抖动）。同时，多个影响 macOS/Windows 跨平台体验的 Bug 引发开发者关注，插件生态和任务工具链的回归问题也成为讨论热点。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 社区热点 Issues

| # | Issue | 亮点 |
|---|-------|------|
| #84352 | CVP-approved 组织仍收到网络保护阻塞 | 🔥 197 评论 / 27 👍 | 已获 Cyber Verification Program 批准的组织在 Claude Code 中仍被拦截，验证门户显示"审核中"，合规用户困扰严重。 |
| #26224 | Claude Code 长时间挂起/冻结 | 🔥 130 评论 / 151 👍 | 提示提交后卡滞 5-20 分钟，社区强烈共鸣，是最高赞 Issue 之一。 |
| #91188 | MEMORY.md 压缩阈值可配置化 | 28 评论 | 希望将 auto-memory 自动压缩的触发阈值设为可配置，当前硬编码限制影响长会话体验。 |
| #13517 | 自定义 statusLine 命令未执行 | 23 评论 / 21 👍 | macOS 下 `settings.json` 中配置的 `statusLine` 命令不被执行，影响 TUI 状态栏定制。 |
| #45810 | 插件市场更新按钮不可点击 | 17 评论 / 8 👍 | 插件有可用更新时，Marketplace UI 的 Update 按钮呈灰色不可交互状态。 |
| #80015 | 任务列表工具不再暴露给模型 | 14 评论 / 13 👍 | 最近更新后 `TaskCreate/TaskUpdate/TaskList/TaskGet` 工具从模型可用工具集中消失，属严重回归。 |
| #82131 | Autocompact 反复抖动（thrashing） | 12 评论 | 上下文压缩后 3 轮内即重新填满至上限，连续发生 3 次，导致频繁压缩循环。 |
| #76694 | Cowork 新项目丢失"选择文件夹"选项 | 12 评论 / 15 👍 | Chat/Cowork 合并后，新项目的右键上下文菜单被替换为仅上传的知识菜单，原生文件夹选择功能消失。 |
| #67500 | Context 压缩恢复后丢失关键行为规则 | 12 评论 | 压缩后 session status block、memory writes、no-stop policy 等核心行为规则被意外丢弃。 |
| #74662 | Claude Desktop 多账户本地会话支持 | 7 评论 / 5 👍 | 同一 Desktop 安装运行两个 claude.ai 账户时，切换账户后另一账户的本地会话在侧栏不可见。 |

> **链接格式**: `https://github.com/anthropics/claude-code/issues/{编号}`

---

## 4. 重要 PR 进展

| # | PR | 状态 | 内容摘要 |
|---|-----|------|---------|
| #87079 | fix(security-guidance): `**` glob 匹配零深度路径 | 🟢 Open | 修复 security-patterns.json 中 `**` 不匹配顶层文件的安全规则静默失效问题。 |
| #68787 | fix(scripts): edit-issue-labels.sh 无参数时报错 | 🔴 Closed | 为 CI 工具脚本添加错误提示，避免静默退出。 |
| #68786 | fix(plugin-dev): 修复 test-hook.sh 中的 shell 注入漏洞 | 🔴 Closed | 通过 stdin 重定向修复 Hook 测试脚本中的命令注入风险。 |
| #68785 | fix(plugin-dev): 修正 hook JSON 输出和 glob 模式 | 🔴 Closed | 修复示例 Hook 脚本的 stderr/stdout 错误、JSON 注入及 CI 检测问题。 |
| #68707 | feat(bug-reporter): 新增 `/bug` 终端提交 Issue 命令 | 🔴 Closed | 从终端直接提交 Bug Report 的插件，提升反馈效率。 |
| #68702 | fix(ralph-wiggum): 兼容 macOS bash 3.x `set -u` | 🔴 Closed | 修复空数组展开导致的 Unbound Variable 错误。 |
| #68701 | fix(security-guidance): Windows Python 版本探测去除 CRLF | 🔴 Closed | 解决 Windows 换行符导致版本比较失败的问题。 |
| #68699 | fix(hookify): Windows Python 包装器和路径规范化 | 🔴 Closed | 解决 Microsoft Store python3 stub 在非 TTY 环境退出码 49 及路径分隔符问题。 |
| #68694 | fix(security-guidance): Windows 路径分隔符规范化 | 🔴 Closed | 将 `CLAUDE_PLUGIN_ROOT` 中的反斜杠转为正斜杠，修复 Hook 脚本中的路径错误。 |
| #68689 | fix(security-guidance): 阻断 symlink 逃逸读取 | 🔴 Closed | 修复恶意仓库通过软链接读取本地文件（如 `~/.ssh/id_rsa`）的安全漏洞。 |

---

## 5. 功能需求趋势

从本期 Issues 中可观察到以下社区关注方向：

| 方向 | 代表 Issue | 说明 |
|------|-----------|------|
| **上下文管理精细化** | #91188, #82131, #67500 | 压缩阈值可配置、Autocompact 抖动修复、压缩后规则保留 |
| **跨平台兼容性与稳定性** | #13517, #76694, #74662 | macOS/Windows 平台 Bug、Cowork 功能回归、多账户支持 |
| **插件生态完善** | #45810 | 插件市场更新机制修复 |
| **安全与合规** | #84352, #87079 | CVP 批准状态同步、安全 glob 规则准确性 |
| **工具链可观测性** | #80015 | 任务工具暴露状态恢复 |

---

## 6. 开发者关注点

**高频痛点：**

1. **会话稳定性**：挂起/冻结（#26224）和 Autocompact 反复抖动（#82131）是开发者体验的最大障碍，直接影响日常使用效率。
2. **上下文压缩质量**：压缩后关键行为规则（session status、memory writes 等）丢失（#67500），导致模型行为不一致。
3. **平台一致性回归**：Chat/Cowork 合并后，Cowork 项目选择文件夹功能消失（#76694）；自定义 statusLine 命令在 macOS 不生效（#13517）。
4. **安全合规摩擦**：CVP 已批准组织仍被拦截（#84352），企业用户流程受阻，验证状态同步存在延迟。
5. **Windows 插件开发体验**：多个 PR 集中修复 Windows 路径分隔符、CRLF、bash 兼容性问题，表明 Windows 生态仍需大量适配工作。
6. **任务工具回归**：`Task*` 工具从模型工具集消失（#80015），影响依赖任务管理的工作流。

---

*数据来源: github.com/anthropics/claude-code | 生成时间: 2026-09-07*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报 — 2026-09-07

## 1. 今日速览

今日 Codex 仓库无新版本发布，共新增 50 条 Issue 和 20 条 PR。社区焦点集中在 **Windows 平台稳定性**（GUI 崩溃、权限面板缺失、Pets 交互失效）和 **VS Code 扩展 26.901.22334 回归**（sidebar 命令找不到）。TUI 侧持续推进 worktree 管理、远程权限配置和语音播放管线优化。

---

## 2. 版本发布

> 过去 24 小时内无新 Release。

---

## 3. 社区热点 Issues

| # | 标题 | 评论 | 👍 | 原因 |
|---|------|------|-----|------|
| [#28919](https://github.com/openai/codex/issues/28919) | Windows Codex app 设置中缺少"Control Other Devices"标签页 | 63 | 59 | 长期未修复的高热度 Windows 功能缺失问题，影响远程设备控制场景 |
| [#22423](https://github.com/openai/codex/issues/22423) | 无法定位 Codex CLI 二进制，App 启动失败 | 31 | 2 | WSL 环境下 App 无法找到 CLI，阻塞 WSL 用户 |
| [#41079](https://github.com/openai/codex/issues/41079) | Windows 分页会话历史卡死（重复序号） | 30 | 3 | 长会话在 Windows 上历史投影异常，数据完整但 UI 不更新 |
| [#41960](https://github.com/openai/codex/issues/41960) | Windows Pets 不响应点击/拖拽 | 20 | 24 | 桌面端宠物交互功能回归，用户反馈强烈 |
| [#42663](https://github.com/openai/codex/issues/42663) | VS Code Remote-SSH 扩展激活失败（Node 22 无法解析 `using`） | 10 | 5 | Remote SSH 场景下扩展崩溃，影响远程开发流 |
| [#42501](https://github.com/openai/codex/issues/42501) | Windows 26.901.1978.0 启动时 cua_node 无法复制 node_repl.exe | 10 | 1 | 新版运行时部署失败，App 进程存在但无窗口 |
| [#26836](https://github.com/openai/codex/issues/26836) | 允许已有线程在项目文件夹重命名后更新工作目录 | 9 | 5 | 工作目录漂移是开发者高频痛点，请求增强容错 |
| [#23671](https://github.com/openai/codex/issues/23671) | Business 账号 Codex 配额消耗速度是 Plus 的 5–10 倍 | 8 | 5 | 跨订阅层级配额行为异常，影响付费用户信任 |
| [#41987](https://github.com/openai/codex/issues/41987) | macOS 桌面端删除会话后侧边栏出现"幽灵"记录 | 7 | 0 | 本地会话数据与 UI 不同步 |
| [#43058](https://github.com/openai/codex/issues/43058) | CLI 发送简单提示被安全策略标记为违规 | 6 | 0 | GPT-6-Astra 在 CLI 场景下的安全策略误判 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| [#43340](https://github.com/openai/codex/pull/43340) | 启用 TUI 中远程命名权限配置选择 | ✅ Closed | 修复远程任务权限配置无法选择的缺陷，通过 `thread/settings/update` 启用 |
| [#43330](https://github.com/openai/codex/pull/43330) | 恢复/分叉远程任务时保留已保存权限 | ✅ Closed | 防止本地权限覆盖远程任务的服务端保存配置 |
| [#43325](https://github.com/openai/codex/pull/43325) | 对 JSON Schema 对象键排序以保证构建一致性 | ✅ Closed | 消除 Cargo 与 Bazel 构建产物的差异 |
| [#43315](https://github.com/openai/codex/pull/43315) | 唯一解析会话标签后再操作 | ✅ Closed | 修复同名会话误选中第一条的 bug |
| [#43308](https://github.com/openai/codex/pull/43308) | Windows app-server 关机改用 socket 请求 | ✅ Closed | 替代文件-based 信号，通过 `/daemon/shutdown` 端点实现可靠关机 |
| [#43304](https://github.com/openai/codex/pull/43304) | 将 Bazel 构建元数据与 Rust 编译输入隔离 | ✅ Closed | 避免 build stamp 导致远程缓存失效 |
| [#43298](https://github.com/openai/codex/pull/43298) | 延迟 managed worktree 转换至新 TUI 循环迭代 | ✅ Closed | 避免大型同步 `ChatWidget` 构造阻塞事件循环 |
| [#43289](https://github.com/openai/codex/pull/43289) | 添加能力门控的 MCP 用户验证处理 | ✅ Closed | 通过 `openai/elicitation/create` 处理 `openai/userVerification` 请求 |
| [#43286](https://github.com/openai/codex/pull/43286) | TUI 新增 managed worktree 浏览器 | ✅ Closed | `/worktree` 命令增加可搜索的 worktree 列表，支持所有者元数据和快速恢复 |
| [#43248](https://github.com/openai/codex/pull/43248) | 语音 Host RTP 音频连接至扬声器播放 | ✅ Closed | 修复语音模式下收到的 RTP 包被丢弃未播放的问题，引入 GStreamer 管线 |

---

## 5. 功能需求趋势

- **Windows 平台稳定性**：Issues 中 Windows 相关问题占比最高（GUI 崩溃、 Pets 交互、运行时部署），是社区最迫切的修复方向。
- **VS Code 扩展可靠性**：26.901.22334 版本出现多起回归（`chatgpt.openSidebar` 命令消失、Remote-SSH 激活失败），开发者对扩展版本质量关注度高。
- **会话与 worktree 管理**：TUI worktree 浏览器（#43286）、工作目录漂移（#26836）、会话标签唯一解析（#43315）等 PR 表明团队在加强项目级会话管理。
- **远程/SSH 集成**：权限配置保留（#43330）、Remote-SSH 扩展问题持续出现，远程开发场景仍有较多摩擦。
- **配额与速率限制**：Business vs Plus 消耗差异（#23671）、速率桶绑定错误（#43136）等问题反映用户对配额透明度的担忧。
- **语音功能**：RTP 音频播放修复（#43248）表明语音功能正进入打磨阶段。

---

## 6. 开发者关注点

1. **Windows 兼容性是最大痛点**：从 GUI 渲染异常（#42493 窗口拉伸）、运行时部署失败（#42501）、功能缺失（#28919）到 Pets 交互失效（#41960），Windows 端问题密集且影响面广。
2. **扩展版本回归频繁**：26.901.22334 在短时间内引发多起 `chatgpt.openSidebar` 不可用问题（#42882、#42969、#43085），社区呼吁加强扩展发布前的回归测试。
3. **CLI 安全策略误判**：简单提示被 `invalid_prompt` 拒绝（#43058、#43237），开发者对 GPT-6-Astra 的安全过滤敏感度提出异议。
4. **会话数据一致性**：分页历史卡死（#41079、#43124）、幽灵会话（#41987）反映本地投影与远程 transcript 之间存在同步缺陷。
5. **远程开发体验**：Remote-SSH 扩展激活失败（#42663、#43240）和权限配置丢失（#43330）说明远程场景的连通性和状态管理仍需完善。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报

**日期：2026-09-07**

---

## 1. 今日速览

今日 Gemini CLI 发布 nightly 版本 v0.60.0-nightly.20260907，核心修复聚焦于会话管理、行尾符处理和 MCP 工具名冲突。社区持续高度关注企业级认证问题（#29101，35 条评论）及子代理稳定性，多项 Agent 相关 bug 仍处于待重测状态，反映出多代理协作可靠性是当前核心痛点。

---

## 2. 版本发布

**v0.60.0-nightly.20260907.g85aca163f**
- [查看完整变更日志](https://github.com/google-gemini/gemini-cli/compare/v0.60.0-nightly.20260906.g85aca163f...v0.60.0-nightly.20260907.g85aca163f)

---

## 3. 社区热点 Issues

| # | Issue | 优先级 | 关注理由 |
|---|-------|--------|----------|
| #29101 | 企业 Workspace 认证失败阻断登录 | P1 | 35 条评论，2 👍，直接影响企业用户正常使用，属高优先级安全认证问题 |
| #22323 | 子代理在 MAX_TURNS 后误报 GOAL success | P1 | 13 条评论，agent 状态机逻辑错误，会导致任务中断被静默掩盖 |
| #29133 | --list-sessions 未标记当前会话，--delete-session 可误删 | P2 | 9 条评论，CLI 路径与交互模式行为不一致，存在数据丢失风险 |
| #21409 | Generalist agent 永久挂起 | P1 | 8 条评论，8 👍，子代理回退机制触发后无限等待，社区反馈强烈 |
| #25166 | Shell 命令执行完成后卡住显示"Awaiting user input" | P1 | 4 条评论，3 👍，简单命令也复现，影响基础可用性 |
| #21983 | browser 子代理在 Wayland 下失败 | P1 | browser agent 兼容性 Issue，Linux Wayland 用户痛点 |
| #22267 | Browser Agent 忽略 settings.json 配置覆盖 | P2 | 3 条评论，配置不生效导致用户预期行为失效 |
| #22745 | 评估 AST 感知文件读取、搜索和代码库映射 | P2 | 7 条评论，探索性能优化方向，影响代码理解精度 |
| #19873 | 基于 Zero-Dependency OS 沙箱利用模型的 bash 亲和力 | P2 | 9 条评论，涉及安全沙箱与模型能力的结合设计 |
| #26525 | 添加确定性敏感信息脱敏并减少 Auto Memory 日志 | P2 | 5 条评论，安全合规相关，涉及模型上下文中的 secrets 处理 |

---

## 4. 重要 PR 进展

| # | PR | 状态 | 内容摘要 |
|---|----|------|----------|
| #29134 | fix(cli): protect current session from deletion | OPEN | 修复 #29133，通过传递 active session ID 并匹配短 ID 后缀防止误删当前会话 |
| #29131 | fix(core): normalize line endings in getDiffContextSnippet | OPEN | 修复 CRLF 文件对比时产生全量 diff 的问题，避免浪费 token 并污染上下文 |
| #29132 | fix(core): normalize line endings in diff context snippets | OPEN | 补充回归测试，确保 CRLF 文件 diff 行为正确 |
| #28975 | fix(core): keep glob results for symlinked workspace roots | CLOSED | 修复 macOS /tmp（符号链接到 /private/tmp）下 glob 无法匹配文件的问题 |
| #28971 | fix(core): keep truncated MCP tool names unique | CLOSED | 修复 MCP 工具名截断后的碰撞问题，确保唯一性 |
| #28983 | fix(core): detect mixed line endings instead of flagging CRLF | CLOSED | 改进行尾符检测逻辑，避免单一 \r\n 误判整个文件为 CRLF |
| #29184 | fix(core): validate git args in Windows sandbox | OPEN | 修复 Windows 沙箱中 `git diff --output=<path>` 静默截断文件的安全漏洞 |
| #28973 | fix(sandbox): bump sandbox image to node:22-slim | CLOSED | 将沙箱基础镜像从 EOL 的 node:20-slim 升级至 node:22-slim |
| #29229 | fix(cli): reject non-finite numbers in settings editor | OPEN | 修复设置编辑器接受 `Infinity` 值后序列化丢失配置的问题 |
| #29106 | fix(core): flush final SSE event on EOF | CLOSED | 修复 SSE 流结束时丢失 `finishReason`/usage 元数据的问题 |

---

## 5. 功能需求趋势

从社区 Issue 中可提炼出以下关键方向：

- **多代理（Subagent）可靠性**：#22323、#21409、#21968、#22267 等多个 Issue 指向子代理的状态管理、配置继承和调用频率问题，是社区当前最集中的反馈领域。
- **AST 感知代码理解**：#22745、#22746 探索基于 AST 的文件读取和代码库映射，旨在减少 token 消耗并提升代码理解的精确度。
- **安全与沙箱加固**：#26525（敏感信息脱敏）、#29184（Windows git 参数验证）、#19873（OS 沙箱）反映社区对操作安全的高度关注。
- **浏览器自动化稳定性**：#21983（Wayland）、#22232（session 锁定恢复）持续推动 browser agent 的跨平台兼容性。
- **Auto Memory 质量改善**：#26522、#26523、#26516 形成系列 Issue，关注记忆提取的低信号过滤、无效 patch 处理和整体质量。

---

## 6. 开发者关注点

基于 Issue 讨论热度与反馈，开发者核心痛点集中在：

1. **子代理行为不可预测**：generalist agent 挂起、subagent 误报成功、不主动调用 skills——用户期望代理能更可靠地执行任务，而非静默失败或无限等待（#21409、#22323、#21968）。
2. **企业环境兼容性**：Workspace 认证问题直接阻断工作流，企业用户需要更稳定的身份验证路径（#29101）。
3. **跨平台行为一致性**：Wayland 下 browser agent 失败、Windows 沙箱安全漏洞、macOS 符号链接 glob 失效——不同 OS 环境下的体验差异显著。
4. **配置与状态持久化**：settings.json 覆盖不生效（#22267）、`/compress` 跨会话不持久（#21335）——配置变更的可见性和持久性仍是短板。
5. **上下文效率**：CRLF 文件导致全量 diff（#29131）、工具名截断碰撞（#28971）——开发者关注 token 消耗优化和工具注册的健壮性。

---

*数据来源：github.com/google-gemini/gemini-cli | 统计周期：2026-09-06 至 2026-09-07*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-09-07**

---

## 1. 今日速览

过去24小时内，Copilot CLI 社区共更新 **21 个 Issues**，无新版本发布。核心焦点集中在 **ACP 模式行为回归**（权限审批丢失、session 异常中止）、**BYOK 模式下 prompt caching 静默失效**导致的成本飙升，以及 **WSL2 端严重内存泄漏**（RSS 达 31GB）等稳定性问题。

---

## 2. 版本发布

今日无新 Release。

---

## 3. 社区热点 Issues

### 🔴 高优先级 Bug

**#4527** `[CLOSED]` `copilot -p` 在 GHEC 数据驻留环境下 401 认证失败
> prompt 模式模型目录请求错误命中了 `api.githubcopilot.com` 而非租户端点，导致非交互模式下认证失败。社区 👍 4，已关闭，疑似已修复。
> [查看详情](https://github.com/github/copilot-cli/issues/4527)

**#4537** `[OPEN]` ACP 模式自动批准工具调用——权限审批机制回归缺陷
> `session/request_permission` 未再发送，shell 命令、文件编辑和删除在无用户确认的情况下直接执行，且 session 日志中无任何记录。这是对 #845 的回归。👍 2
> [查看详情](https://github.com/github/copilot-cli/issues/4537)

**#4555** `[OPEN]` ACP 模式下 `session/prompt` 无条件中止 session，终止所有后台 sub-agent
> `session.abort()` 在 `session/prompt` handler 中作为第一个操作无条件执行，导致通过 `task` 工具启动的后台 sub-agent 被中断。交互式 TUI 无此问题。
> [查看详情](https://github.com/github/copilot-cli/issues/4555)

**#4694** `[OPEN]` WSL2 下 Copilot CLI 1.0.82 内存泄漏：RSS 达 31GB，CPU 占用 57%
> 在 WSL 上运行 Claude Opus 5 模型高耗时 session 时，约 47% 上下文占用处出现严重内存泄漏。影响长期使用体验。
> [查看详情](https://github.com/github/copilot-cli/issues/4694)

**#4720** `[OPEN]` Copilot CLI 1.0.82 BYOK 模式下 prompt caching 静默禁用（约 5 倍成本增长）
> BYOK 模式下 chat 请求未携带 prompt-cache 声明，导致整个 session 的缓存命中率为零，成本显著上升。
> [查看详情](https://github.com/github/copilot-cli/issues/4720)

**#4695** `[OPEN]` MCP OAuth Token 跨会话复用不可靠——不同 cache-key 导致重复认证
> HTTP 类型 MCP 服务器使用 OAuth (PKCE) 时，CLI 频繁生成新的 cache-key 条目而非复用有效 token。
> [查看详情](https://github.com/github/copilot-cli/issues/4695)

### 🟡 中等优先级 Bug

**#4742** `[OPEN]` Desktop 1.1.15 无法在同一项目中创建第二个 Local session
> 当项目内已有活跃的 Local session CLI 进程时，创建新 session 报 "This project already has an active Local workspace" 错误。
> [查看详情](https://github.com/github/copilot-cli/issues/4742)

**#4735** `[OPEN]` 工具调用前的 assistant 文本被错误归类为 reasoning 并折叠
> 当模型在同一 turn 中输出 reasoning block + 多段用户可见文本 + 工具调用时，用户可见文本被折叠进 "Thought for Ns" 中，用户完全看不到。
> [查看详情](https://github.com/github/copilot-cli/issues/4735)

**#4706** `[OPEN]` 工具/函数调用间歇性生成畸形 markup，静默 no-op
> Copilot CLI agent 自身报告：tool invocation markup 格式错误（`<invoke>` 损坏），导致调用静默失败。
> [查看详情](https://github.com/github/copopil
t-cli/issues/4706)

### 🟢 功能需求

**#1665** `[CLOSED]` 支持项目/仓库级别的 Copilot CLI 插件作用域
> 当前插件仅支持 per-user 全局安装，社区希望支持 repo/project 级插件隔离。👍 18，评论 14，已关闭，代表重要需求方向。
> [查看详情](https://github.com/github/copilot-cli/issues/1665)

**#2644** `[OPEN]` 请求在 prompt 输入中支持 Shift+Arrow / Ctrl+A 文本选择
> 当前输入行不支持标准 GUI 文本选择快捷键，影响使用体验。👍 2
> [查看详情](https://github.com/github/copilot-cli/issues/2644)

---

## 4. 重要 PR 进展

**#4739** `[OPEN]` docs: 提出终端级 macOS 通知方案
> 作者 anujb-msft 提出在 macOS 上通过终端通知替代系统级通知的参考方案，含 MIT 许可的示例代码和回归测试。非正式 CLI 变更，为文档性提案。
> [查看详情](https://github.com/github/copilot-cli/pull/4739)

---

## 5. 功能需求趋势

从本周期 Issues 中可识别以下社区关注方向：

| 方向 | 关注点 | 相关 Issues |
|------|--------|-------------|
| **ACP/Agent 模式稳定性** | 权限审批丢失、session 异常中止、后台 agent 管理 | #4537, #4555, #4743 |
| **BYOK/成本优化** | prompt caching 静默失效、企业模型配置异常 | #4720, #4692 |
| **性能与资源管理** | WSL2 内存泄漏（31GB RSS） | #4694 |
| **插件与配置系统** | 项目级插件作用域、MCP Token 缓存复用 | #1665, #4695 |
| **终端交互体验** | 键盘快捷键支持、文本选择、输入行为 | #2644, #4736, #4738 |
| **渲染与输出** | assistant 文本折叠误判、工具调用 markup 错误 | #4735, #4706 |
| **桌面应用** | 多 session 并发创建限制 | #4742 |

---

## 6. 开发者关注点

**核心痛点：**

1. **ACP 模式可靠性严重退步**（1.0.81-1 起）：多个 Issue 指向同一回归窗口——权限审批被跳过（#4537）、session 异常中止（#4555）、后台 shell 完成信号丢失（#4743）。这是当前社区反馈最密集的故障域。

2. **BYOK 模式下成本失控**：prompt caching 静默禁用（#4720）和企业模型配置不一致（#4692）直接冲击使用成本，对付费企业用户影响尤甚。

3. **WSL2 内存泄漏**：31GB RSS 的泄漏规模表明存在严重的资源管理缺陷，需尽快定位。

4. **MCP 生态集成问题**：OAuth Token 缓存键不稳定（#4695）影响 MCP 服务器的平滑集成体验。

5. **终端交互习惯缺失**：用户对标准快捷键（Shift+Arrow、Ctrl+E 接受建议）的需求持续存在，反映 CLI 交互层仍落后于开发者预期。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-09-07**

---

## 1. 今日速览

过去24小时无新版本发布，社区活跃度集中在功能需求讨论与底层问题修复。远程会话控制（Issue #1282）以 32 个 👍 持续领跑社区呼声；PR #2513 修复 Moonshot API 返回的双编码工具调用参数导致的 Pydantic 校验失败，已在内部合并流程中。

---

## 2. 版本发布

- 过去 24 小时内无新版本发布。

---

## 3. 社区热点 Issues

### #1282 [OPEN] Remote Control - 跨设备续接本地会话
- **作者**: CatKang | **热度**: 👍 32 / 13 评论 | **更新**: 2026-09-06
- **链接**: [MoonshotAI/kimi-cli Issue #1282](https://github.com/MoonshotAI/kimi-cli/issues/1282)
- **关注原因**: 当前 Kimi Code CLI 会话绑定本地终端，开发者希望从手机、平板或浏览器续接，是提升工作流连续性的核心需求，社区支持度最高。

### #1354 [CLOSED] Plan 模式需求
- **作者**: panzhiyi87-droid | **热度**: 👍 7 / 1 评论 | **更新**: 2026-09-07
- **链接**: [MoonshotAI/kimi-cli Issue #1354](https://github.com/MoonshotAI/kimi-cli/issues/1354)
- **关注原因**: 用户尝试通过 Skill 实现计划模式，但 Kimi Code 常在讨论完成前自主执行，社区期望原生 Plan 模式控制。

### #2252 [CLOSED] /goal 命令与 Codex 计划导入
- **作者**: DuskLin | **热度**: 👍 2 / 9 评论 | **更新**: 2026-09-06
- **链接**: [MoonshotAI/kimi-cli Issue #2252](https://github.com/MoonshotAI/kimi-cli/issues/2252)
- **关注原因**: 参照 Codex 和 Claude Code（v138+）的 `/goal` 命令，同时希望 Kimi 生成的 coding plan 可直接导入 Codex 使用，跨平台互操作性呼声。

### #1356 [CLOSED] MCP Skill 配置迁移工具
- **作者**: deshes | **热度**: 👍 0 / 0 评论 | **更新**: 2026-09-07
- **链接**: [MoonshotAI/kimi-cli Issue #1356](https://github.com/MoonshotAI/kimi-cli/issues/1356)
- **关注原因**: 多工具用户（Claude CLI / Cursor / Windsurf 等）希望一键迁移 MCP Server / Skill 配置，降低切换成本。

---

## 4. 重要 PR 进展

### #2636 [OPEN] 优化 get_share_dir 缓存与路径处理
- **作者**: gugu8intel-i9 | **更新**: 2026-09-07
- **链接**: [MoonshotAI/kimi-cli PR #2636](https://github.com/MoonshotAI/kimi-cli/pull/2636)
- **内容**: 对 `get_share_dir` 函数添加缓存机制并优化路径处理逻辑，提升共享目录查找性能，适用于多平台路径差异场景。

### #2513 [OPEN] 修复双重编码 tool-call 参数解析
- **作者**: nitishagar | **更新**: 2026-09-06
- **链接**: [MoonshotAI/kimi-cli PR #2513](https://github.com/MoonshotAI/kimi-cli/pull/2513)
- **内容**: Moonshot API 返回的 `function.arguments` 存在嵌套数组/对象被 JSON 字符串化（双重编码）的情况，单次 `json.loads` 后值仍为字符串导致 Pydantic 校验失败。此 PR 引入共享的 `decode_tool_arguments` 函数递归解码，修复该问题。

---

## 5. 功能需求趋势

| 方向 | 代表 Issue | 社区热度 |
|------|-----------|---------|
| **跨设备 / 远程会话** | #1282 | ⭐⭐⭐⭐⭐ |
| **计划模式（Plan Mode）** | #1354 | ⭐⭐⭐ |
| **跨工具互操作性（Codex / MCP）** | #2252, #1356 | ⭐⭐ |
| **稳定性与 Bug 修复** | PR #2513 | 内部优先级 |

社区最关注的是**远程会话续接**与**原生 Plan 模式**，两者直接影响开发者的核心工作流体验。

---

## 6. 开发者关注点

- **痛点一：会话孤岛** — 当前 CLI 会话完全绑定本地终端，无法在移动设备或不同机器间续接，远端开发场景受限。
- **痛点二：执行控制力不足** — Plan 模式下 Kimi Code 常在讨论未结束时自行执行，开发者期望更精细的阶段控制权。
- **痛点三：跨平台生态割裂** — 用户同时使用多个 Agent CLI 工具，MCP 配置与 coding plan 格式无法互通，迁移成本高。
- **痛点四：API 解析稳定性** — 双重编码的 tool-call 参数导致校验失败，影响工具调用的可靠性。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 — 2026-09-07

---

## 1. 今日速览

过去 24 小时内，Pi 社区活跃度极高，45 条 Issue 中有大量在当日被关闭，显示核心开发者响应迅速。**Copilot GPT 模型路由修复**（PR #9253）和 **跨 Provider 容灾降级**（PR #9248/#9251）是最具价值的两个合并改动；同时社区持续关注 OpenAI Codex 连接稳定性这一高频痛点（Issue #4945，76 条评论）。

---

## 2. 版本发布

过去 24 小时内**无新版本发布**。

---

## 3. 社区热点 Issues

| # | 主题 | 状态 | 评论 | 👍 | 重要性说明 |
|---|------|------|------|----|------------|
| [#4945](https://github.com/badlogic/pi-mono/issues/4945) | `openai-codex` 连接可靠性：流式 TUI 卡死在 `Working...` | OPEN / inprogress | 76 | 32 | 社区反馈最多的稳定性问题，反复出现且影响流式体验，已有长期跟进 |
| [#7547](https://github.com/badlogic/pi-mono/issues/7547) | Windows 上 Pi 的使用体验与焦点梳理 | OPEN | 57 | 2 | 大规模 Windows 用户群体发声，请求团队明确平台优先级和文档方向 |
| [#9052](https://github.com/badlogic/pi-mono/issues/9052) | 全屏模式滚轮滚动速度异常（慢 3 倍） | OPEN | 6 | 3 | 直接影响全屏模式可用性，体验痛点明确 |
| [#8826](https://github.com/badlogic/pi-mono/issues/8826) | 建议为 coding-agent 重试退避设置上限 | OPEN | 4 | 0 | 长时运行的 agent 在供应商间歇性故障时容易无限退避，需要可配置上限 |
| [#8823](https://github.com/badlogic/pi-mono/issues/8823) | 流式过程中 Esc 取消请求不可靠 | OPEN | 3 | 0 | 用户打断体验问题，abort 注册成功但 HTTP 请求未能及时终止 |
| [#8827](https://github.com/badlogic/pi-mono/issues/8827) | TUI LaTeX legacy 字体切换导致渲染回退为源码 | OPEN | 3 | 0 | 影响使用传统 TeX 语法用户的公式渲染体验 |
| [#8617](https://github.com/badlogic/pi-mono/issues/8617) | Codex 图像工具结果改用 `file_id` 引用 | OPEN | 3 | 0 | 减少重复上传 base64 的带宽开销，提议者已有本地原型 |
| [#9265](https://github.com/badlogic/pi-mono/issues/9265) | OpenAI 流式处理中 tool-call 参数存在 O(n²) 重解析 | OPEN | 1 | 0 | **性能严重隐患**：单线程 daemon 场景下，tool 调用越大冻结越明显 |
| [#9230](https://github.com/badlogic/pi-mono/issues/9230) | `opencode-go` provider 未发送新要求的 `x-opencode-session` header | CLOSED | 2 | 1 | 上游变更导致 Pi 请求被拒，已修复 |
| [#9242](https://github.com/badlogic/pi-mono/issues/9242) | 跨 Provider 传输/不可达错误时的自动降级 | CLOSED | 2 | 0 | 社区提出需求，已由 PR #9248/#9251 实现并合入 |

---

## 4. 重要 PR 进展

| # | 标题 | 作者 | 状态 | 说明 |
|---|------|------|------|------|
| [#9259](https://github.com/badlogic/pi-mono/pull/9259) | 紧急干预运行中 turn： Steering 消息优先处理 | shuo-huge | ✅ 已合入 | 长工具调用执行期间，用户 steering 消息不再排队等待，而是立即打断当前 turn，大幅提升交互响应感 |
| [#9261](https://github.com/badlogic/pi-mono/pull/9261) | 新增 `sendStrictToolField` 兼容开关 | huangchaodian | ✅ 已合入 | 解决 AWS Bedrock 等代理网关要求 strict schema 但拒绝 `strict` 字段的问题 |
| [#6881](https://github.com/badlogic/pi-mono/pull/6881) | 使用 Provider 返回的实际费用而非目录价 | R-Taneja | 🔄 进行中 | 当响应含 `usage.cost` 时直接使用，否则回退到本地计算，提升成本显示的准确性 |
| [#9253](https://github.com/badlogic/pi-mono/pull/9253) | 将 Copilot GPT 模型路由改为 Responses API | petrroll | ✅ 已合入 | 修复 #9209，解决 `gpt-6-astra` 等模型被错误路由到 `/chat/completions` 而返回 400 的问题 |
| [#9252](https://github.com/badlogic/pi-mono/pull/9252) | undici DNS 查找固定为系统 `dns.lookup` | RaviTharuma | ✅ 已合入 | 修复 MagicDNS / 分割视角主机名在 Pi 中解析失败（#9244）的问题 |
| [#9248](https://github.com/badlogic/pi-mono/pull/9248) | 传输错误时自动切换到备用 Provider | RaviTharuma | ✅ 已合入 | 实现 #9242，支持在活跃 Provider 不可达时降级到配置的备用 Provider |
| [#9233](https://github.com/badlogic/pi-mono/pull/9233) | 启动时实时解析 Model 认证状态 | gpoulios | ✅ 已合入 | 修复因未 await 后台 refresh 导致启动时 `hasConfiguredAuth()` 返回不稳定快照的问题 |
| [#9080](https://github.com/badlogic/pi-mono/pull/9080) | TUI 新增"跳转到最新"控制 | rwachtler | ✅ 已合入 | 长时间流式生成中用户可以一键回到消息末尾，改善滚动体验 |
| [#9224](https://github.com/badlogic/pi-mono/pull/9224) | 限制 OpenRouter `:free` 模型的 maxTokens | GISWLH | ✅ 已合入 | 修复 `minimax:free` 等目录条目 maxTokens 虚高导致上游 400 的问题 |
| [#9227](https://github.com/badlogic/pi-mono/pull/9227) | 新增逐调用工具确认扩展 | juemimgcd | ✅ 已合入 | 为状态变更类 custom tool 提供逐次确认机制，与现有 `permission-gate` bash 策略互补 |

---

## 5. 功能需求趋势

从本期 Issues 和 PR 可观察到以下社区关注方向：

1. **连接可靠性与容灾**：跨 Provider 降级（#9242 → #9248）、重试退避上限（#8826）、`openai-codex` 连接稳定性（#4945）持续高频出现，稳定性是社区第一诉求。
2. **Windows 平台体验**：#7547 发起的讨论反映大量 Windows 开发者使用 Pi，但存在 WSL、原生、多种路径并存的混乱，社区期待明确的平台支持策略。
3. **TUI 交互优化**：全屏模式滚动（#9052）、会话恢复图片渲染（#9256）、跳转最新（#9080）、Esc 取消（#8823）—— 交互流畅度是日常使用的核心体验。
4. **扩展能力开放**：多期 Issue 提出扩展 API 需求——模型运行时暴露（#8791）、TUI 模式切换（#9238）、用户消息投递确认（#9236）、逐调用工具确认（#9228），说明扩展生态正在快速增长。
5. **成本透明**：PR #6881 推动使用 Provider 上报的实际费用，反映用户对成本控制的关注度持续提升。
6. **新模型支持**：`gpt-6-astra`（#9133）、Claude Opus 5（#9165）等新兴模型的适配需求。

---

## 6. 开发者关注点

| 痛点 / 高频需求 | 涉及 Issue / PR | 社区情绪 |
|----------------|----------------|---------|
| `openai-codex` 流式卡死无提示 | #4945 | 😤 高度关注，长期未根治 |
| Windows 多路径并存导致使用混乱 | #7547 | 😐 期待官方明确优先级 |
| 全屏模式滚动性能差异 | #9052 | 😤 体验落差明显 |
| 流式中断（Esc）不可靠 | #8823 | 😐 高频打断场景受影响 |
| 会话恢复后图片异常全尺寸渲染 | #9256 | 😤 长会话用户痛点 |
| 工具调用参数 O(n²) 解析导致事件循环冻结 | #9265 | 😨 性能隐患，嵌入了单进程 daemon 的用户敏感 |
| 长任务中无法及时插入 steering 消息 | #9259 | ✅ 已修复，社区认可 |
| 跨 Provider 无降级导致硬失败 | #9242 → #9248 | ✅ 已修复 |
| 扩展 API 能力不足 | #8791, #9236, #9238 | 📈 扩展开发者诉求强烈 |
| 启动时认证状态快照不稳定 | #9233 | ✅ 已修复 |

---

> **总结**：过去 24 小时 Pi 核心开发者处理了大量社区反馈，**稳定性修复**和**容灾能力**是最大产出。Windows 平台策略和 `openai-codex` 连接可靠性仍是两个长期悬而未决的关键问题，值得关注后续进展。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报 — 2026-09-07

## 1. 今日速览

Qwen Code 今日发布 **v0.23.1-preview.1**，Web Shell 新增动态工作流可视化管理能力。社区聚焦于多 Agent 协作架构（mesh admission 基础）、Web Shell 会话导航体验优化，以及安全性相关的遥测数据泄露问题修复。

---

## 2. 版本发布

### v0.23.1-preview.1
**更新内容：**
- **Web Shell 工作流可视化**：新增对动态工作流运行的可视化与管理能力（PR #10594）
- **性能优化**：Session 工作流项目推导逻辑重构，减少重复计算

### v0.23.0-nightly.20260906.92a8a8d179
- 同步上述 preview 版本改动

---

## 3. 社区热点 Issues

| # | 主题 | 关注点 | 评论数 |
|---|------|--------|--------|
| #8662 | TUI 渲染层从 ink 迁移至 OpenTUI | 长期跟踪，解决当前 ink + React 19 的闪烁/渲染问题 | 30 |
| #3361 | Agent 将成功执行的 Shell 输出误判为空 | OpenAI 兼容 API 下的关键 Bug，影响自动化流程 | 6 |
| #11031 | 导出 HTML 重复嵌入 Web Shell 运行时 | 导致空会话导出文件约 19.5MB，已修复 | 6 |
| #10865 | Session 工作流推导每次渲染重复 3 次 | Web Shell 性能优化，已识别修复 | 4 |
| #11100 | Transcript 条目仍携带 daemon 运行时依赖 | 影响导出功能体积与独立性 | 4 |
| #11146 | 已取消的工具请求可能阻塞后续请求 | Core 调度器并发 Bug，影响交互响应 | 4 |
| #6181 | Web Shell 移动端会话切换卡顿 | 多层性能成本叠加，需系统性优化 | 3 |
| #11198 | 遥测数据上传未脱敏（含 Shell 命令） | **安全/隐私问题**，涉及原始工具错误文本上传 | 2 |
| #11186 | `qwen serve` 主目录场景下 settings 作用域错误 | Daemon 通道所有权模型缺陷 | 3 |
| #9011 | `ask_user_question` 静默返回"用户拒绝" | 缺少实际问题与取消原因的展示 | 3 |

**重点关注：**
- **#8662**（30 条评论）— 迁移 TUI 渲染层是长期技术债，社区期待 OpenTUI 带来更稳定的交互体验
- **#11198** — 安全类 Issue，遥测数据包含 Shell 命令原文，可能泄露敏感信息

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| #11244 | 可配置的 Web Shell 产品名称与 Logo | Open | 支持白标部署，通过 `settings.json` 配置 SVG Logo 和产品名 |
| #10938 | Session Workflow 依赖导航与界面优化 | Open (autofix) | 优化 Plan DAG 展示，以步骤为中心而非状态 |
| #11206 | 多 Agent Mesh 准入基础架构 | Open | 新增持久化工作区 Agent 协作规则，覆盖消息路由、线程门控、Token 限流等 |
| #11252 | 绑定 Dispatcher 运行到 Agent 轮次 | Closed | 将 mesh dispatcher 与后台 Agent 轮次边界关联，记录投递与 Token 用量 |
| #11208 | 有界历史转录视口 | Open | Web Shell 会话导航 Phase 2B，支持回退历史、恢复丢失记录 |
| #11242 | Chrome Native Messaging 桥接 | Open | 通过 Chrome 扩展与 Native Messaging Host 连接 Browser SDK |
| #11090 | 用户令牌驱动会话免审批流程 | Open | 同审查级别的会话间可实现无逐条审批的消息传递 |
| #11251 | Assistant 轮次结算生命周期回调 | Open | 向宿主暴露可选回调，报告轮次完成/取消/失败状态 |
| #11250 | 分屏会话导航体验优化 | Open | 分屏标题悬停显示会话详情，工具审批队列支持快速跳转 |
| #11248 | Goal 消耗可视化 | Open | 在多界面展示 Goal 当前 Token 消耗与窗口配额 |

---

## 5. 功能需求趋势

1. **多 Agent 协作（Agent Mesh）** — PR #11206、#11252 显示核心开发重点转向持久化多 Agent 协作框架，涵盖路由、门控、Token 配额管理。

2. **Web Shell 体验优化** — 多个 PR 同步推进：会话导航（#11208）、分屏优化（#11250）、白标支持（#11244），表明 Web Shell 是当前迭代重点。

3. **浏览器自动化集成** — PR #11242 新增 Chrome Native Messaging 支持，扩展 Browser SDK 能力。

4. **CLI 交互稳定性** — 多个 Bug Fix 聚焦调度器并发（#11146）、工具取消清理（#11162）、SSE 错误处理（#11215、#11217）。

5. **安全与隐私** — Issue #11198 暴露遥测脱敏问题，社区对数据泄露敏感度上升。

---

## 6. 开发者关注点

| 痛点 | 涉及 Issue/PR |
|------|---------------|
| Shell 输出误判为空，导致 Agent 行为异常 | #3361 |
| Web Shell 移动端会话切换严重卡顿 | #6181 |
| 导出 HTML 体积过大（19.5MB+） | #11031, #11100 |
| 取消请求后工具状态残留/阻塞 | #11146, #11162 |
| SSE 流式错误处理不完善（限流/超时） | #11215, #11217 |
| 遥测数据未脱敏，可能泄露命令内容 | #11198 |
| TUI 渲染闪烁与结构问题 | #8662 |
| `/effort` 参数未传递至 OpenAI 兼容后端 | #11227 |
| 右键菜单与快捷键冲突 | #11228 |

---

**整体趋势：** 当前迭代围绕 Web Shell 体验打磨与多 Agent 架构基础建设双线推进，同时修复一系列影响稳定性和安全性的核心 Bug。社区对移动端性能、遥测隐私和并发调度问题关注度较高。

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI 社区动态日报
**日期：2026-09-07**  
**数据来源：github.com/Hmbown/DeepSeek-TUI**

---

## 1. 今日速览

过去 24 小时项目无新版本发布，但社区活跃度极高——39 个 Issue 和 50 个 PR 获得更新，大量问题在当天即被修复并关闭。核心焦点集中在 **TUI 底部状态栏可配置化**（#5950）、**MCP 工具链体验改进**（#5926/#5939）和 **Fleet 子代理管理** 三大方向，整体工程推进节奏明显加快。

---

## 2. 版本发布

过去 24 小时内 **无新 Release 发布**。

---

## 3. 社区热点 Issues

| # | 标题 | 重要性 | 社区反应 |
|---|------|--------|----------|
| #5316 | EPIC-005: CodeWhale TUI Crate Decomposition（总控 Epic） | 🔴 架构级重构的 Umbrella Issue，所有子 EPIC 和 PR 均在此登记追踪，是项目长期技术方向的核心 | 22 条评论，讨论持续 27 天，是社区最活跃 Issue |
| #5620 | [bug] Context pressure warning 是瞬态的，agent 不会主动响应 | 🔴 上下文压缩安全信号被绕过，可能导致 silently context degradation，无崩溃但影响可靠性 | 12 条评论，由核心贡献者 ronohara 提出 |
| #5929 | [bug] 并行执行测试 flaky，6 个测试在负载下失败 | 🟡 CI 稳定性问题，每个 flaky 测试导致重跑或 25 分钟矩阵等待，直接影响开发效率 | 4 条评论，项目所有者 Hmbown 亲自标注 |
| #5901 | [enhancement] 自定义主题 overlays 未出现在 /theme 选择器中 | 🟡 用户已实现自定义主题（commit 312a6e872d），但 picker 只列出编译内置主题，自定义主题不可见 | 4 条评论，已关闭，功能已合入 |
| #5969 | [bug] `serve --acp` initialize 响应违反 ACP schema，JetBrains IDEA 无法连接 | 🟡 `sessionCapabilities.list` 应为 object 却返回 boolean，严格客户端直接失败 | 2 条评论，新提报，待修复 |
| #5950 | [enhancement] 0.9.12 底部 chrome 不可配置，/statusline 机制已失效 | 🟡 0.9.12 重构后底部两行（姿态栏+指标行）硬编码，用户无法自定义 | 2 条评论，已提出可配置化需求 |
| #5915 | [enhancement] Fleet 模型：provider→model→shortlist→role 完整链路 | 🟢 创始人方向性需求，定义子代理 Fleet 的模型选择和角色分配流程 | 2 条评论，指导后续开发 |
| #5955 | [enhancement] 支持 per-task 子代理模型选择（暴露角色配置+成本分类） | 🟢 当前子代理无法按任务切换模型，主 agent 无法指定子任务使用免费模型 | 2 条评论，已关闭，已合入 |
| #5932 | [bug] 测试隔离泄漏：onboarding 测试将 fixture provider 写入真实 `~/.codewhale/setup_state.json` | 🟡 测试污染用户真实配置，严重性高 | 2 条评论，项目所有者提报 |
| #5856 | [enhancement] Computer-use 插件：live-install 回执 + 首次 look-act 循环 | 🟢 计算机操作插件的关键里程碑，完成 install→MCP 连接→截图/点击/验证闭环 | 2 条评论，处于草稿 PR 阶段 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 内容摘要 |
|---|------|------|----------|
| #5973 | feat(tui): compact and hidden presets for bottom chrome | OPEN | 解决 #5950，为 posture_bar 和 metrics_line 添加 `full/compact/hidden` 三档模式，支持 `/config` 实时设置 |
| #5970 | fix(tui): isolate five load-flaky tests | CLOSED | 解决 #5929 中 5/6 个 flaky 测试，根因定位并修复，第六个分析为并行安全 |
| #5972 | tui: a failing runtime store is a visible notice, not a log line | OPEN | 解决 #5931 的 runtime store 部分，session id 分叉错误从静默日志改为可见通知 |
| #5971 | feat(tui): /mcp leads with need-login servers | CLOSED | 解决 #5926，MCP 页脚将 "8 failed" 改为优先展示需要登录的服务器，并保留原始响应回执 |
| #5968 | feat(build): opt-in rusty_alloc global allocator | CLOSED | 解决 #5872，添加 `rusty_alloc` 作为 mimalloc 的可选替代，纯 Rust 实现，无需 C 编译器 |
| #5946 | feat(fleet): surface worker deliverables via summary | OPEN | Fleet 完成任务后展示摘要而非空回执，通过累积流式内容事件生成有界摘要 |
| #5966 | feat(providers): catalog-driven account keys | CLOSED | 动态 account keys 提供者注册，新增 `codewhale` 路由，支持 sandbox/ShannonNet 批量操作 |
| #5962 | feat(tui): /statusline composes the bottom chrome | CLOSED | #5950 的第一部分：ctx 始终可见，/statusline 驱动指标行，废弃死开关 |
| #5960 | tui: diverged engine session id is a visible notice | CLOSED | #5931 的 session id 部分：引擎 session id 与主机分叉时显示可见通知而非仅日志 |
| #5958 | tui(fleet): model filter 无匹配时渲染提示而非 panic | CLOSED | 解决 #5953，Fleet 设置向导中模型过滤器无匹配结果时显示提示，避免 index out of bounds 崩溃 |

---

## 5. 功能需求趋势

从 Issue 和 PR 中提炼出以下社区重点关注方向：

1. **TUI 可配置性 & UX 打磨**：底部状态栏定制（#5950/#5973）、命令发现性（#5952/#5964）、启动体验优化（#5887/#5925），社区对 0.9.12 重构后的 UX 回归有强烈反馈。
2. **MCP 工具链可靠性**：OAuth 登录流程改进（#5926/#5971/#5959）、运行时刷新不干扰当前 turn（#5939/#5957）、连接状态可见性，MCP 是企业级使用的关键依赖。
3. **Fleet 子代理体系**：模型选择与角色分配（#5915/#5955）、Worker 交付物展示（#5946）、写锁冲突释放（#5906），Fleet 能力正在快速成熟。
4. **上下文压缩可控性**：可配置 summarizer 提示词和原始消息保留策略（#5956/#5965），用户希望减少压缩信息损失。
5. **平台兼容性**：Windows 窗口控制阻塞（#5923）、CRLF 行尾保留（#5909）、ACP schema 合规（#5969），跨平台稳定性是持续痛点。

---

## 6. 开发者关注点

**高频痛点：**
- **测试稳定性**：并行 flaky 测试（#5929）和测试隔离泄漏（#5932）直接影响 CI 效率和开发体验，是开发者反馈最集中的工程问题。
- **启动体验**：启动时按键丢失（#5925）、MCP 连接状态长时间停滞（#5887）影响初次使用体验。
- **Fleet 写锁泄漏**：挂起的子代理无限持有写锁，阻塞兄弟代理工作（#5906），是 Fleet 多代理协作的关键 blocker。
- **Windows 后端缺陷**：Win32 computer-use 输入操作报告假成功（#5908）、窗口控制阻塞 TUI 线程（#5923），Windows 平台可靠性亟待加强。
- **命令发现性差**：120 个斜杠命令中约 70 个带参数，但用法字符串对用户隐藏（#5952），已修复（#5964）。

**积极信号：**
- 大量 Issue 在提报当天即被关闭并合入，迭代速度极快。
- 创始人直接参与 Issue 提报和方向指导（#5915、#5932），核心开发与用户需求紧密对齐。

---

*日报生成时间：2026-09-07*  
*数据截止：过去 24 小时 GitHub 活动*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*