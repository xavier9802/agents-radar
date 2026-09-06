# AI CLI 工具社区动态日报 2026-09-06

> 生成时间: 2026-09-06 04:06 UTC | 覆盖工具: 10 个

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

**日期：2026-09-06** | 分析师：Agnes

---

## 1. 生态全景

2026年9月，AI CLI 工具生态呈现"多强竞争、快速迭代"态势。Claude Code、OpenAI Codex、Qwen Code 三强持续领跑版本发布节奏，OpenCode 与 Pi 社区活跃度高涨。工具间功能趋同明显——MCP 集成、多 Agent 协作、跨平台稳定性成为共同战场，而差异化竞争聚焦于本地模型支持（Pi、Gemini）、多 Provider 路由（Pi、Qwen）及 Web Shell 工作流（Qwen Code）。Windows 平台稳定性仍是全行业普遍痛点。

---

## 2. 各工具活跃度对比

| 工具 | Issues | PRs | Release | 版本动态 |
|------|--------|-----|---------|----------|
| **Claude Code** | 10 | 3 | v2.1.263 | Bug 修复 + 稳定性提升 |
| **OpenAI Codex** | 10 | 10 | 无 | 功能完善期，无发布 |
| **Gemini CLI** | ≥1 | ≥1 | v0.60.0-nightly | 夜间版本高频迭代 |
| **Kimi Code CLI** | 4 | 1 | 无 | 修复为主，无发布 |
| **OpenCode** | 10+ | 10+ | 无 | 社区驱动，高活跃度 |
| **Pi** | 10 | 10 | v0.85.1 | 新增 GPT-6 Astra 支持 |
| **Qwen Code** | 10 | 10 | v0.23.0/v0.23.1（3个预览版） | 多版本高频发布 |
| **DeepSeek TUI/Codewhale** | ≥5 | ≥2 | v0.9.12 | 品牌迁移 + 版本发布 |
| **GitHub Copilot CLI** | — | — | — | 摘要生成失败 |
| **Grok Build** | 0 | 0 | 无 | 无活动 |

---

## 3. 共同关注的功能方向

| 方向 | 涉及工具 | 具体诉求 |
|------|----------|----------|
| **MCP 集成稳定性** | Claude Code、Codex、Qwen Code、OpenCode | HTTP 传输层工具不可达、OAuth scopes 缺失、重启后配置丢失 |
| **Windows 平台稳定性** | Claude Code、Codex、Pi、Kimi CLI | 启动崩溃、窗口置顶异常、无日志崩溃、Shell 兼容 |
| **多 Agent / 插件扩展** | Claude Code、Qwen Code、Pi、Codex | Function Hooks 提案（Claude）、子 Agent 委托（Qwen via ACP）、子代理继承问题 |
| **跨平台一致性** | Claude Code、Codex、Pi、Kimi CLI | 窗口行为、语音播放、Bash 命令处理、渲染异常 |
| **会话/历史管理** | Codex、OpenCode、Qwen Code | Ordinal 重用、上下文压缩后状态错乱、索引缓存失效 |
| **大文件 / 渲染性能** | OpenCode、Qwen Code、Pi | 大文件卡死、导出体积过大（19.5MB）、流式渲染字符丢失 |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|----------|----------|----------|
| **Claude Code** | 插件扩展（Function Hooks）、安全规则、Agent 系统 | 专业开发者、Claude 生态用户 | 稳定迭代优先，强调整体可靠性 |
| **OpenAI Codex** | GPT-6 模型支持、语音功能（WebRTC/RTP）、Computer Use | OpenAI 订阅用户、Windows 用户 | 多轮实验性功能快速试错 |
| **Qwen Code** | Web Shell 工作流可视化、多模型路由（GPT/Claude/Kimi 独立配置）、ACP 子 Agent 委托 | 中文开发者、多模型使用者 | 高频预览版迭代，功能创新激进 |
| **OpenCode** | 插件系统、SQLite 并发、Provider 适配（Bedrock/AWS）、计费透明 | 开源社区贡献者、多 Provider 用户 | 社区驱动，问题响应快 |
| **Pi** | 多 Provider 路由（Meta/Ollama/Codex 等）、Nix flake、本地模型支持 | 技术极客、多模型实验者 | 灵活扩展，快速响应社区需求 |
| **Kimi Code CLI** | VS Code / Zed IDE 集成、Moonshot API 兼容 | Kimi 订阅用户、中文开发者 | 生态适配优先，稳定性待提升 |
| **Gemini CLI** | Agent 可靠性、A2A 协议、子代理管理 | Gemini 生态用户 | 夜间版本高频迭代 |
| **Codewhale** | 品牌迁移、多 Agent 调度（Fleet）、跨平台一致性 | DeepSeek/Codewhale 用户 | 品牌整合期，功能重构中 |

---

## 5. 社区热度与成熟度

| 维度 | 工具 | 评估 |
|------|------|------|
| **最高社区活跃度** | OpenCode、Pi | 日更 Issues/PRs 密集，社区贡献者活跃（Hona、anishsamant 等持续提交） |
| **最快迭代节奏** | Qwen Code、Gemini CLI | Qwen 单日 3 个 nightly/preview 版本；Gemini 夜间版本日更 |
| **成熟稳定阶段** | Claude Code、Codex | 版本发布节奏稳定，Issue 修复聚焦 Bug 而非功能扩展 |
| **快速成长期** | Kimi Code CLI、Codewhale | 用户增长带动 Issue 反馈增加，基础设施待完善 |
| **生态空白** | Grok Build | 无活动，可能处于早期或内部阶段 |

---

## 6. 值得关注的趋势信号

| 趋势 | 证据 | 对开发者的参考 |
|------|------|----------------|
| **MCP 成为行业标准集成协议** | Claude Code、Codex、Qwen Code、OpenCode 均有多项 MCP 相关 Issue | 优先选择支持 MCP 的 Agent 工具，关注 HTTP 传输层稳定性 |
| **子 Agent / 多 Agent 协作成为核心竞争力** | Qwen Code（ACP 委托）、Claude Code（Function Hooks）、Pi（subagents） | 评估工具时关注 Agent 间委托机制的成熟度 |
| **Windows 平台仍是最大短板** | 4+ 工具将 Windows 稳定性列为 Top 痛点 | Windows 用户需谨慎选择，或等待工具明确标注 Windows 支持等级 |
| **Web Shell / 可视化工作流是新战场** | Qwen Code 投入大量资源（PR #10594、#11053、#11054） | 关注 Web Shell 成熟度，影响长会话和团队协作体验 |
| **本地模型与多 Provider 路由需求上升** | Pi 支持 Meta/Ollama/多种 Gateway；Qwen Code 支持多模型独立配置 | 多模型实验者优先选择支持多 Provider 的工具 |
| **会话生命周期管理亟待完善** | 多个工具存在历史记录丢失、索引缓存失效、重连阻塞等问题 | 选择工具时关注会话持久化和跨版本数据迁移能力 |
| **发布流程质量成为差异化点** | Pi 暴露 npm 依赖缺失；Qwen Code CI 资源竞争 | 关注工具的发布流程和依赖声明完整性，反映工程成熟度 |

---

**总结：** 当前 AI CLI 生态处于功能扩张与稳定性博弈阶段。Qwen Code 和 Pi 在创新节奏上领先，Claude Code 和 Codex 在稳定性上占优，OpenCode 社区贡献最为活跃。开发者应根据自身平台（Windows 用户需谨慎）、模型偏好（多 Provider vs 单一生态）和工作流需求（Web Shell vs 纯 TUI）进行选择。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告
**数据截止：2026-09-06 | 分析范围：50 PR + 15 Issues**

---

## 1. 热门 Skills 排行

| 排名 | Skill | 功能概述 | 社区热点 | 状态 |
|------|-------|----------|----------|------|
| 1 | [Hivemind 多 Agent 编排](https://github.com/anthropics/skills/pull/1628) | 将机械性工作委派给免费模型的 headless 代理，主代理仅负责规划和审查 | 零成本多代理协作模式引发关注 | OPEN |
| 2 | [Buffer GraphQL Agent Skill](https://github.com/anthropics/skills/pull/1627) | 跨平台社交排程技能，支持任意 AI Agent 调用 Buffer API | 实用工具类 Skill 落地需求强 | OPEN |
| 3 | [scnet-hpc Skill](https://github.com/anthropics/skills/pull/1615) | SCNet HPC 集群的 SSH/Slurm 工作流操作指南 | 超算/高性能计算场景需求明确 | OPEN |
| 4 | [document-typography Skill](https://github.com/anthropics/skills/pull/514) | 防止 AI 生成文档中的孤行、寡行、编号错位等排版问题 | "隐性质量痛点"引发共鸣 | OPEN |
| 5 | [ODT Skill](https://github.com/anthropics/skills/pull/486) | OpenDocument 格式（.odt/.ods）创建、填充、解析与转换 | 开源办公格式支持补充 | OPEN |
| 6 | [testing-patterns Skill](https://github.com/anthropics/skills/pull/723) | 覆盖测试哲学、单元测试、React 组件测试的完整测试栈 | 测试工程化技能需求旺盛 | OPEN |
| 7 | [ServiceNow Platform Skill](https://github.com/anthropics/skills/pull/568) | 覆盖 ITSM/ITOM/FSM/SecOps 等全模块的企业级 ITSM 平台技能 | 企业 IT 运维场景长期关注 | OPEN |
| 8 | [skill-quality-analyzer](https://github.com/anthropics/skills/pull/83) | 从结构/文档/安全等五维度自动评估 Skill 质量的元工具 | Skill 质量基础设施呼声高 | OPEN |

---

## 2. 社区需求趋势

从 Issues 中提炼出五大核心需求方向：

**① 安全与信任边界**（Issue #492，43 评论）
- 社区 Skill 冒充 `anthropic/` 官方命名空间，存在权限滥用风险
- 用户强烈期待官方认证机制和命名空间隔离

**② 组织级协作与共享**（Issue #228，16 评论）
- 当前 Skill 分发依赖手动下载安装，团队内共享成本极高
- 期待内置的组织级 Skill 库或分享链接机制

**③ 推理质量保障**（Issue #1385、#1367）
- 自审计流水线：预校准 → 对抗审查 → 交付验证
- 机械验证 + 四维推理质量门控成为热门提案

**④ 企业/垂直领域集成**（Issue #1175、PR #568）
- SharePoint Online 安全处理、ServiceNow 全模块覆盖等enterprise 场景需求持续积累

**⑤ 工具链可靠性修复**（Issue #556、#1390）
- `run_eval.py` 触发失败（0% recall）长期未解
- MCP Builder 评估脚本序列化问题影响评测可信度

---

## 3. 高潜力待合并 Skills

以下 PR 具备明确的实用价值且讨论活跃，近期有较高合并概率：

| PR | Skill | 合并潜力理由 |
|----|-------|-------------|
| [#1627](https://github.com/anthropics/skills/pull/1627) | Buffer GraphQL Agent Skill | 社交排程跨平台通用，PR 最近更新频繁（09-05），作者响应积极 |
| [#1615](https://github.com/anthropics/skills/pull/1615) | scnet-hpc | HPC 场景 niche 但刚需，覆盖 Slurm/SSH 完整工作流 |
| [#1628](https://github.com/anthropics/skills/pull/1628) | Hivemind 多 Agent | 成本优化思路（免费模型执行机械任务）契合当前趋势 |
| [#1367](https://github.com/anthropics/skills/pull/1367) | Self-audit（四维推理质量门控） | 对应 Issue #1385 提案，自审计能力是 Skill 生态的关键基础设施 |
| [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns | 测试工程是开发者高频需求，覆盖 AAA 模式、Testing Library 等主流实践 |
| [#514](https://github.com/anthropics/skills/pull/514) | document-typography | 痛点明确（孤行/寡行），修复成本低、覆盖广 |

**⚠️ 阻塞项提醒：**
- PR #1298、#1099、#1050 修复 `skill-creator` Windows 兼容性问题，是其他 Skill 开发工具链的地基，建议优先合并
- Issue #556（`run_eval.py` 触发失败）未解决前，Skill 评估流程不可靠

---

## 4. Skills 生态洞察

> **社区最集中的诉求是：在确保官方 Skill 安全认证（防冒充）的前提下，加速企业级工作流 Skill（HPC/ITSM/文档排版）和 Agent 质量基础设施（自审计、多 Agent 编排）的落地，同时修复影响 Skill 开发生命周期的底层工具链缺陷。**

---



# Claude Code 社区动态日报
**日期：2026-09-06**

---

## 1. 今日速览

Claude Code v2.1.263 发布，主要修复 bug 并提升稳定性。社区最热议题为 Function Hooks 扩展能力提案（Issue #91870），引发 112 条评论与 72 个赞的激烈讨论。Windows 平台窗口行为异常和启动崩溃问题持续占据 bug 榜单前列。

---

## 2. 版本发布

### v2.1.263
- 修复多项 bug 并提升整体可靠性
- [GitHub Releases](https://github.com/anthropics/claude-code/releases)

---

## 3. 社区热点 Issues（Top 10）

| # | 标题 | 状态 | 评论 | 👍 | 重要性 |
|---|------|------|------|-----|--------|
| #91870 | Function Hooks - make plugins 10x more powerful | OPEN | 112 | 72 | ⭐⭐⭐⭐⭐ 核心扩展能力提案，通过参数化 `$` 对象实现安全副作用跟踪，支持类 Express/Koa 的注册顺序编排 |
| #53247 | Claude Desktop fails to launch on Windows — orphaned Silo / Job Object | OPEN | 66 | 29 | ⭐⭐⭐⭐ 严重启动故障，崩溃后需重启或注销才能恢复 |
| #66516 | Claude Desktop macOS window stays always on top | CLOSED | 31 | 5 | ⭐⭐⭐ 跨平台行为不一致，macOS 用户反馈窗口始终置顶且无关闭选项 |
| #87895 | Claude Desktop window stays always on top on Windows | CLOSED | 17 | 72 | ⭐⭐⭐ Windows 版同样存在置顶问题，点赞数高于 macOS 版 |
| #72123 | Read Out Loud / Play voice degrades mid-playback | OPEN | 8 | 1 | ⭐⭐ 语音播放中途音质下降、加速、变调 |
| #86647 | Cowork session reports zero connected folders | OPEN | 7 | 2 | ⭐⭐ Cowork 会话与项目 UI 文件夹连接状态不一致 |
| #89679 | Windows "freeze-then-vanish" crash with zero forensic trace | OPEN | 5 | 0 | ⭐⭐⭐ 无日志崩溃，难以定位根因 |
| #85111 | Bash tool silently truncates commands over ~8 KB | OPEN | 5 | 0 | ⭐⭐⭐ 命令静默截断并误报 quoting error |
| #86875 | HTTP-transport MCP server tools unreachable | OPEN | 4 | 0 | ⭐⭐⭐ MCP HTTP 传输层工具可达性问题，连接显示正常但调用失败 |
| #74311 | Configurable target model for Fable 5 classifier fallback | OPEN | 3 | 6 | ⭐⭐ 安全分类器降级目标模型可配置化需求 |

---

## 4. 重要 PR 进展

| # | 标题 | 作者 | 内容摘要 |
|---|------|------|----------|
| #87077 | fix(pr-review-toolkit): repair invalid YAML frontmatter in all agents | anishsamant | 修复 agent 描述中 YAML frontmatter 解析错误问题，未引号标量含 `key: value` 格式导致解析失败 |
| #87079 | fix(security-guidance): make ** glob patterns match zero-depth paths | anishsamant | 修复安全规则中 `**` 模式无法匹配零深度路径的 bug，**/.ts 无法覆盖顶层文件 |
| #89404 | validate-agent.sh: don't abort at the first warning | bcherny | 修复验证脚本过早中止问题，解决 `set -euo pipefail` 导致的有效 agent 被误判为失败 |

---

## 5. 功能需求趋势

| 方向 | 关注热度 | 代表 Issue |
|------|----------|------------|
| **扩展能力 / 插件系统** | 🔥🔥🔥🔥🔥 | #91870 Function Hooks |
| **MCP 集成稳定性** | 🔥🔥🔥🔥 | #86875, #91898 |
| **Windows 平台稳定性** | 🔥🔥🔥🔥 | #53247, #89679, #92337 |
| **模型与计费配置** | 🔥🔥🔥 | #74311, #91488, #75944 |
| **IDE / VS Code 集成** | 🔥🔥🔥 | #91860, #87066 |
| **Agent 系统能力** | 🔥🔥🔥 | #92134, #92426 |
| **跨设备同步** | 🔥🔥 | #66303 |
| **Fable 安全分类器增强** | 🔥🔥 | #74311, #92428 |

---

## 6. 开发者关注点

### 高频痛点
1. **Windows 平台稳定性**：启动崩溃（#53247）、窗口置顶异常（#87895, #92337）、无日志崩溃（#89679）等问题集中爆发，是 Windows 用户反馈最密集的领域。
2. **MCP 连接与工具调用**：HTTP 传输层工具显示已连接但实际不可用（#86875），以及误导性的超时提示（#91898），影响工具生态体验。
3. **Bash 工具行为异常**：超过 8KB 命令静默截断（#85111）和 Auto 模式在 Windows 下仍提示使用 Bash（#92407），暴露平台适配问题。
4. **认证与订阅**：OAuth token 刷新失败（#90688）、个人订阅被组织策略拦截（#75944）等鉴权相关问题持续存在。
5. **插件 / Agent 系统**：Function Hooks 提案（#91870）获得社区高度关注，反映开发者对深度扩展能力的强烈需求；同时存在 Agent 工具描述与实际不符（#92134）和子 Agent 继承问题（#92426）等 bug。

### 核心需求
- **Function Hooks 机制**：通过侧效跟踪和注册顺序编排实现更强大的插件能力
- **多平台一致性**：Windows/macOS 窗口行为、语音播放、Bash 命令处理等跨平台体验需统一
- **MCP 工具调用可靠性**：修复 HTTP 传输层工具不可达和超时提示误导问题
- **Agent 系统完善**：修复子 Agent 定义被忽略、工具描述不一致等问题

---

*数据来源：github.com/anthropics/claude-code | 统计周期：2026-09-05 ~ 2026-09-06*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-09-06**

---

## 1. 今日速览

今日 Codex 社区无新版本发布，但 Windows 端问题集中爆发：多个高关注度 Issue 涉及 GPT-6 Astra 模型缺失、Computer Use 延迟及崩溃、远程会话僵死等。同时，官方连续关闭了 20+ 个 PR，主要围绕原生语音支持（Voice）、Bazel 构建系统优化及 TUI 新功能（managed worktree、reasoning effort 记录）的完善。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 社区热点 Issues

### 1. [CLI] Paginated history drops valid flattened rollout records and reuses ordinals
- **链接**: https://github.com/openai/codex/issues/35746
- **评论**: 39 | 👍: 3
- **重要性**: 影响 Codex CLI 滚动历史记录的完整性，ordinals 重用可能导致对话状态错乱，是长期存在的核心 Bug。

### 2. [Windows] 26.901.1978.0 fails to launch UI when cua_node staging cannot copy node_repl.exe
- **链接**: https://github.com/openai/codex/issues/42501
- **评论**: 9 | 👍: 0
- **重要性**: 新版 Windows 应用完全无法启动，影响大量用户，涉及 `cua_node` 运行时打包问题。

### 3. [Windows] GPT-6 Astra missing from model picker for eligible ChatGPT Pro account
- **链接**: https://github.com/openai/codex/issues/42853
- **评论**: 10 | 👍: 1
- **重要性**: 付费用户无法使用已订阅的高级模型，直接影响用户体验和订阅价值感知。

### 4. [Windows] allow configuring the default session shell via config
- **链接**: https://github.com/openai/codex/issues/16579
- **评论**: 7 | 👍: 45
- **重要性**: 高赞功能请求，Windows 用户长期希望支持 Git Bash 等默认 Shell，社区呼声极高。

### 5. [VS Code Remote-SSH] Server reconnect leaves stale app-server holding thread writer
- **链接**: https://github.com/openai/codex/issues/41849
- **评论**: 6 | 👍: 4
- **重要性**: Remote-SSH 场景下会话阻塞问题，影响远程开发工作流。

### 6. [Windows][Remote] Opening a task from Android triggers git.exe crash storm and system-wide OOM
- **链接**: https://github.com/openai/codex/issues/41982
- **评论**: 4 | 👍: 0
- **重要性**: 远程任务触发系统级 OOM，属于严重性能/稳定性问题。

### 7. [macOS] Chats become unusable after context compaction and print internal validation errors
- **链接**: https://github.com/openai/codex/issues/41922
- **评论**: 7 | 👍: 0
- **重要性**: 上下文压缩后对话不可用，影响长时间会话体验。

### 8. MCP OAuth login does not include scopes during dynamic client registration
- **链接**: https://github.com/openai/codex/issues/20503
- **评论**: 4 | 👍: 11
- **重要性**: MCP 集成关键 Bug，影响 Fastmail 等第三方服务登录，社区关注度高。

### 9. Weekly Codex limit dropped from ~45% to 0% with no sessions run
- **链接**: https://github.com/openai/codex/issues/42765
- **评论**: 3 | 👍: 0
- **重要性**: 配额异常扣减问题，用户信任危机。

### 10. [Windows] Resume reuses two rollout ordinals after trailing token_count records
- **链接**: https://github.com/openai/codex/issues/43142
- **评论**: 2 | 👍: 0
- **重要性**: 与 #35746 类似，历史记录 ordinals 重用问题在桌面端同样存在。

---

## 4. 重要 PR 进展

### 1. Gate experimental context by model capability at session startup
- **链接**: https://github.com/openai/codex/pull/43147
- **状态**: ✅ CLOSED
- **内容**: 会话启动时根据模型能力门控实验性上下文功能，修复子会话继承父会话 token 预算的问题。

### 2. Add managed worktree creation to TUI session commands
- **链接**: https://github.com/openai/codex/pull/43120
- **状态**: ✅ CLOSED
- **内容**: TUI 新增 `/worktree` 命令，支持创建独立工作树或 fork 当前对话，增强项目隔离能力。

### 3. Record reasoning effort changes in conversation history behind a flag
- **链接**: https://github.com/openai/codex/pull/43110
- **状态**: ✅ CLOSED
- **内容**: 新增 `reasoning_effort_override` 功能（默认禁用），在对话历史中记录推理力度变更。

### 4. Move Guardian thread context into `guardianv2` configuration
- **链接**: https://github.com/openai/codex/pull/43104
- **状态**: ✅ CLOSED
- **内容**: 将 Guardian 线程上下文配置迁移至 `guardianv2`，支持同步/异步 Guardian 的线程隔离。

### 5. Add a helper-backed realtime WebRTC session API
- **链接**: https://github.com/openai/codex/pull/43097
- **状态**: ✅ CLOSED
- **内容**: 新增 `RealtimeWebrtcSession` API，支持实时音频会话的启动、协商、控制和错误报告。

### 6. Add bounded incoming Opus RTP handling to the voice host
- **链接**: https://github.com/openai/codex/pull/43100
- **状态**: ✅ CLOSED
- **内容**: 语音宿主新增 Opus RTP 入站处理，限制待发媒体为 64 包/2 MiB，防止内存无限增长。

### 7. Send processed microphone audio over RTP in voice-host
- **链接**: https://github.com/openai/codex/pull/43090
- **状态**: ✅ CLOSED
- **内容**: 语音宿主现在通过 RTP 发送麦克风音频，支持重采样和静音边界处理。

### 8. Add explicit Windows tool selection for native voice builds
- **链接**: https://github.com/openai/codex/pull/43125
- **状态**: ✅ CLOSED
- **内容**: 为 Windows 原生语音构建添加显式工具链选择，避免 Cygwin 与 MSVC 工具冲突。

### 9. Expose native Windows build tools through Bazel targets
- **链接**: https://github.com/openai/codex/pull/43126
- **状态**: ✅ CLOSED
- **内容**: 修复 Bazel 构建中 MSVC 工具被丢弃的问题，保留原生构建所需工具。

### 10. Save subagent and memory opt-ins through the app server
- **链接**: https://github.com/openai/codex/pull/43113
- **状态**: ✅ CLOSED
- **内容**: 子代理和记忆功能的用户选择通过 app server 持久化，新线程生效。

---

## 5. 功能需求趋势

1. **Windows 平台稳定性** - 多个高优先级 Issue 集中在 Windows 桌面端，包括启动失败、模型缺失、Computer Use 延迟等，表明 Windows 客户端仍是当前痛点区域。

2. **会话历史与状态管理** - 历史记录 ordinals 重用、上下文压缩后状态错乱、已删除会话残留等问题频发，用户期望更稳定的会话生命周期管理。

3. **MCP/远程集成** - MCP OAuth scope 缺失、VS Code Remote-SSH 会话僵死、iOS 远程控制失效等问题显示远程集成场景仍需大量完善。

4. **配额与计费透明度** - 用户频繁反馈配额异常扣减，对计费系统的可信度提出质疑。

5. **语音功能完善** - PR 集中展示了原生语音支持、WebRTC 会话、RTP 处理等底层能力建设，语音功能正在快速迭代。

---

## 6. 开发者关注点

| 关注方向 | 具体问题 | 关联 Issue |
|---------|---------|-----------|
| **Shell 配置** | 希望支持 Git Bash 等默认 Shell | #16579 (👍45) |
| **模型可见性** | GPT-6 Astra 对 Pro 用户不可见 | #42853, #43143 |
| **Computer Use** | Windows 端 21-42 秒延迟、macOS 拖拽状态丢失 | #42790, #43047, #43159 |
| **配额管理** | 零使用量下配额归零 | #42765, #43135 |
| **MCP 认证** | OAuth scopes 未传递导致登录失败 | #20503 |
| **远程开发** | Remote-SSH 重连后会话阻塞 | #41849 |
| **子代理可见性** | 桌面搜索和移动端无法找到子代理创建的任务 | #32614 |
| **TUI 体验** | 需要持续显示子代理活动状态 | #43148 |

---

*报告生成时间：2026-09-06 | 数据来源：github.com/openai/codex*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报 | 2026-09-06

## 1. 今日速览
今日社区焦点集中在子代理可靠性、MCP/A2A 协议对接与配置管理三大方向，多项 P1 级 Issue 暴露 Agent 挂起与 Shell 交互阻塞等核心体验痛点。官方同步发布 v0.60.0-nightly 版本，并通过一组 PR 集中修复 Hooks 迁移兼容性、终端滚动异常及 Flash 模型版本锁定等高频问题。

## 2. 版本发布
- **v0.60.0-nightly.20260906.g85aca163f**：今日夜间自动发布版本，包含多项核心修复与配置逻辑优化。
  [Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.60.0-nightly.20260905.g85aca163f...v0.60.0-nightly.20260906.g85aca163f)

## 3. 社区热点 Issues
1. **#21409 Generalist agent hangs** [P1, 8 👍, 8 

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-09-06**

---

## 1. 今日速览

过去24小时内 Kimi Code CLI 无新版本发布，社区活跃度集中在 Issues 修复与功能需求反馈。IDE 集成兼容性问题（Zed VS Code 渲染缺陷）持续受到关注，同时双编码工具调用参数解码问题已有开发者提交修复 PR，进展中。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 社区热点 Issues

### #1284 [CLOSED] Windows 下 Zed IDE ACP 面板无法启动
- **作者:** prashanth057 | **更新:** 2026-09-06
- **重要性:** 反映 Kimi CLI 与新兴编辑器 Zed 的兼容性挑战，影响 Windows 用户群体
- **社区反应:** 0 点赞，1 条评论
- [查看 Issue](https://github.com/MoonshotAI/kimi-cli/issues/1284)

### #1350 [CLOSED] 频繁出现 Authorization failed 认证失败
- **作者:** dapeng1162 | **更新:** 2026-09-06
- **重要性:** 认证稳定性直接影响用户体验，涉及 debian12 + kimi-for-coding 模型场景
- **社区反应:** 0 点赞，0 条评论
- [查看 Issue](https://github.com/MoonshotAI/kimi-cli/issues/1350)

### #1349 [CLOSED] Shell Prompt 不再显示 cwd/git 分支信息
- **作者:** Sirfetch-d | **更新:** 2026-09-06
- **重要性:** 交互体验退化问题，开发者需要在 CLI 中快速获取上下文信息
- **社区反应:** 0 点赞，0 条评论，提出可配置显示需求
- [查看 Issue](https://github.com/MoonshotAI/kimi-cli/issues/1349)

### #2635 [OPEN] VS Code 扩展聊天文本流式渲染字符丢失
- **作者:** TserenTserenov | **更新:** 2026-09-05
- **重要性:** 核心渲染层 Bug，影响 VS Code 扩展用户使用体验，模型输出完整但显示异常
- **社区反应:** 0 点赞，0 条评论，已排除模型层问题
- [查看 Issue](https://github.com/MoonshotAI/kimi-cli/issues/2635)

---

## 4. 重要 PR 进展

### #2513 [OPEN] fix(kosong): 递归解码双编码的工具调用参数
- **作者:** nitishagar | **创建:** 2026-07-19 | **更新:** 2026-09-06
- **修复内容:** Moonshot API 返回的 `function.arguments` 存在嵌套 JSON 字符串（双编码）问题，单次 `json.loads` 后仍为字符串导致 Pydantic 验证失败。本 PR 添加共享的 `decode_tool_arguments` 函数递归处理此问题
- **当前状态:** 待合并，最近更新
- [查看 PR](https://github.com/MoonshotAI/kimi-cli/pull/2513)

---

## 5. 功能需求趋势

| 方向 | 关注度 | 说明 |
|------|--------|------|
| **IDE 集成兼容性** | 高 | Zed、VS Code 适配问题持续出现，新兴编辑器支持需求强烈 |
| **认证与稳定性** | 中 | 认证失败频率高，需增强 token 刷新与连接稳定性 |
| **CLI 交互体验** | 中 | Prompt 信息展示（cwd/git 分支）可配置化需求明确 |
| **渲染性能** | 中 | VS Code 扩展流式渲染存在字符丢失问题 |
| **API 兼容性** | 中 | 双编码参数处理需适配 Moonshot API 实际行为 |

---

## 6. 开发者关注点

**核心痛点：**

1. **编辑器生态兼容性不足** — 开发者反馈 Kimi CLI 在 Zed、VS Code 等编辑器中存在启动失败、渲染异常等问题，对多编辑器支持需求迫切
2. **认证机制稳定性待提升** — 频繁出现 Authorization failed，影响持续开发流程，建议优化 token 管理与自动刷新机制
3. **CLI 交互信息缺失** — 版本迭代后 Prompt 丢失 cwd/git 分支信息，开发者依赖此信息确认上下文，需恢复或提供可配置方案
4. **渲染层 Bug** — VS Code 扩展存在字符丢失问题，虽模型输出正常但影响最终使用体验
5. **API 响应格式兼容** — 双编码参数问题暴露出框架层对 Moonshot API 实际响应的适配不足

---

*报告生成时间：2026-09-06 | 数据来源：github.com/MoonshotAI/kimi-cli*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode 社区动态日报 — 2026-09-06

---

## 1. 今日速览

过去24小时内 OpenCode 无新版本发布，但社区活跃度持续高涨，共新增/更新 50 个 Issues 与 20 个 PRs。核心热点集中在 **多进程 SQLite 锁冲突**、**大文件渲染性能问题**以及 **跨平台会话同步** 等稳定性议题；同时，PR #47571 系列（ stall 检测、重连恢复、请求排队优化）展现了客户端稳定性的集中改进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 评论 | 👍 | 重要性 |
|---|------|------|------|-----|--------|
| #32747 | `@` 文件引用不包含启动后新建的文件 | OPEN | 15 | 13 | 🔴 高频功能 bug |
| #35009 | 升级至 1.17.13 后内存/CPU 使用量飙升 | CLOSED | 10 | 2 | 🔴 性能回归 |
| #34030 | 无法调用 GitHub Copilot 企业第三方模型 | CLOSED | 9 | 2 | 🟡 集成兼容性 |
| #25430 | `json_schema.retryCount` 参数被忽略 | CLOSED | 7 | 0 | 🟡 结构化输出缺陷 |
| #16678 | 启动失败：`CREATE TABLE project` 报错 | CLOSED | 6 | 1 | 🔴 数据库迁移问题 |
| #28695 | 会话生命周期上下文 Hook 请求 | CLOSED | 6 | 2 | 🟢 插件能力扩展 |
| #35690 | 升级后会话历史消失 | CLOSED | 6 | 0 | 🔴 数据可见性 bug |
| #31916 | TUI 处理大文件时卡死（"Preparing to write..."） | CLOSED | 5 | 1 | 🔴 性能/稳定性 |
| #35741 | WebChat agent 模式 LLM 幻觉自答 | CLOSED | 5 | 1 | 🟡 Agent 行为异常 |
| #47547 | Go 订阅额度显示异常导致被锁定 | OPEN | 3 | 0 | 🔴 计费系统 bug |

**热点解读：**
- **#32747** 是持续开放的长期问题，索引缓存未随文件系统更新，影响日常开发效率，社区关注度最高（15 评论 / 13 👍）。
- **#35009** 反映 1.17.x 系列存在资源占用回归，需关注后续版本是否修复。
- **#47547** 是今日最新 Issue，计费展示逻辑（按模型百分比累加 vs 实际金额）与订阅锁定策略存在偏差，影响付费用户体验。

🔗 相关 Issues 链接：
- https://github.com/anomalyco/opencode/issues/32747
- https://github.com/anomalyco/opencode/issues/35009
- https://github.com/anomalyco/opencode/issues/34030
- https://github.com/anomalyco/opencode/issues/25430
- https://github.com/anomalyco/opencode/issues/16678
- https://github.com/anomalyco/opencode/issues/28695
- https://github.com/anomalyco/opencode/issues/35690
- https://github.com/anomalyco/opencode/issues/31916
- https://github.com/anomalyco/opencode/issues/35741
- https://github.com/anomalyco/opencode/issues/47547

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 作者 | 类型 |
|---|------|------|------|------|
| #47571 | 检测停滞事件流并在恢复前台时自动重同步 | OPEN | Hona | 🐛 客户端稳定性 |
| #47573 | 重连后刷新待处理输入队列 | OPEN | Hona | 🐛 客户端修复 |
| #47574 | 事件流重连期间状态点脉冲动画 | OPEN | Hona | ✨ UI 体验 |
| #47570 | 管理"最近关闭的项目"侧边栏 | OPEN | gjoliveira9634 | ✨ 新功能 |
| #47567 | SQLite 锁超时后重试语句 | OPEN | woodsonl | 🐛 并发修复 |
| #47572 | 为无响应的服务器请求设置超时 | OPEN | Hona | 🐛 客户端修复 |
| #47561 | 合并目录目录刷新请求，避免事件风暴 | CLOSED | Hona | ⚡ 性能优化 |
| #47224 | 保留 Zen 模型发现传输元数据 | OPEN | kabishou11 | 🐛 Provider 修复 |
| #47559 | 独立配置 GPT 与 Claude 工具优化 | OPEN | rekram1-node | ✨ 模型适配 |
| #47548 | 在 Provider 插件中自动发现 Bedrock 凭证 | CLOSED | rekram1-node | ✨ AWS 集成 |

**重点 PR 解读：**
- **#47571 系列（Hona 主导）**：针对移动端/锁屏后事件流停滞问题的完整修复栈，包括 stall 检测、重连恢复、请求超时和队列刷新，将显著改善桌面端在网络不稳定场景下的体验。
- **#47567**：直接回应 #47566（多进程 SQLite 锁冲突），通过重试机制缓解 `SQLITE_BUSY` 错误，对共享数据目录的场景尤为重要。
- **#47559**：允许为不同模型家族（GPT/Claude/Kimi 等）独立配置 prompt 和工具优化策略，提升模型适配灵活性。

🔗 相关 PR 链接：
- https://github.com/anomalyco/opencode/pull/47571
- https://github.com/anomalyco/opencode/pull/47573
- https://github.com/anomalyco/opencode/pull/47574
- https://github.com/anomalyco/opencode/pull/47570
- https://github.com/anomalyco/opencode/pull/47567
- https://github.com/anomalyco/opencode/pull/47572
- https://github.com/anomalyco/opencode/pull/47561
- https://github.com/anomalyco/opencode/pull/47224
- https://github.com/anomalyco/opencode/pull/47559
- https://github.com/anomalyco/opencode/pull/47548

---

## 5. 功能需求趋势

从 Issue 中提炼社区最关注的方向：

| 方向 | 代表 Issues | 趋势说明 |
|------|-------------|----------|
| **会话管理与持久化** | #28695, #35690, #35750, #35703 | 开发者强烈期望会话生命周期 Hook、跨版本迁移数据完整性、以及 Desktop/TUI 目录统一 |
| **大文件/渲染性能** | #31916, #32046, #35009 | 1.17.x 系列引入的大 diff 渲染瓶颈和内存回归是高频反馈 |
| **Provider/模型兼容性** | #34030, #35798, #35732, #34676 | Copilot 企业集成、AWS Bedrock 自动发现、DeepSeek XML 格式适配、Claude 思维链支持 |
| **计费与订阅透明** | #47547, #35792 | 用户对 Go 订阅额度计算逻辑和 MiniMax 异常扣费提出明确质疑 |
| **插件系统扩展** | #28695, #35728, #35742 | 希望支持 session 注入消息、插件版本强制更新等高级能力 |

---

## 6. 开发者关注点

**高频痛点：**

1. **SQLite 并发限制**：多进程共享同一数据目录时频繁触发 `SQLITE_BUSY`，#47566/#47567 成为今日焦点，需官方提供明确的多实例支持方案。

2. **索引/缓存时效性**：`@` 文件引用、会话列表等功能的缓存未与文件系统状态同步，导致"新建文件找不到""升级后会话消失"等体验断裂。

3. **大文件处理稳定性**：1.17.x 引入的 diff 渲染和 `write` 工具在处理 150+ 行内容时存在卡死风险，影响大规模代码库使用。

4. **跨平台数据一致性**：Desktop 与 TUI 的会话/项目可见性不一致、macOS/Windows 跨客户端远程连接异常等问题反复出现。

5. **模型格式适配**：DeepSeek 等模型返回 DSML/XML 格式导致工具调用解析失败；GPT-5.5 在自定义 OpenAI 兼容提供商下缺少明确的工作路径。

**开发者建议关注：**
- #47567（SQLite 重试机制）合并后对多进程场景的改善
- Hona 的 stall 检测系列 PR 对移动端稳定性的提升
- #32747 的索引刷新策略优化进展

---

*报告生成时间：2026-09-06 | 数据来源：github.com/anomalyco/opencode*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 — 2026-09-06

## 1. 今日速览

Pi v0.85.1 正式发布，新增 GPT-6 Astra 支持；同时暴露出一系列 npm 发布依赖缺失问题（#9132、#9218），已在 0.85.1 中修复。Windows TUI 兼容性问题持续高热度（#7547 累计 52 条评论），社区对跨平台体验关注度显著提升。

---

## 2. 版本发布

### v0.85.1
- **GPT-6 Astra** 现已可用，支持 OpenAI API Keys 及 OpenAI Codex 订阅
- 修复 #9132：`@earendil-works/pi-server` 缺失依赖导致 `pi-subagents` 无法运行
- 修复 #9218：全局安装后子 agent 启动失败问题

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 热度 | 链接 |
|---|------|------|------|------|
| #7547 | Windows 上如何使用 Pi？社区反馈收集 | OPEN | 52💬 | [链接](https://github.com/earendil-works/pi/issues/7547) |
| #5023 | 终端无故滚动到顶部 | CLOSED | 19💬 | [链接](https://github.com/earendil-works/pi/issues/5023) |
| #8896 | `/export` HTML 静默丢弃 `display:false` 自定义消息 | OPEN | 8💬 | [链接](https://github.com/earendil-works/pi/issues/8896) |
| #6300 | Windows TUI 每键入一个字符即重绘输入行 | OPEN | 8💬 | [链接](https://github.com/earendil-works/pi/issues/6300) |
| #9132 | 0.85.0 发布包缺少 `pi-server` 依赖 | CLOSED | 5💬 | [链接](https://github.com/earendil-works/pi/issues/9132) |
| #8684 | `PI_OFFLINE` 意外禁用全部 provider 模型发现 | OPEN | 5💬 | [链接](https://github.com/earendil-works/pi/issues/8684) |
| #9212 | Sonnet-5 通过 gateway：13% edit tool 调用被截断 | CLOSED | 3💬 | [链接](https://github.com/earendil-works/pi/issues/9212) |
| #9220 | 斜杠命令自动补全竞态：IME 提交时 `/re` 被当作消息发送 | CLOSED | 1💬 | [链接](https://github.com/earendil-works/pi/issues/9220) |
| #9223 | `bun run eval` 递归重入而非执行 evals | CLOSED | 1💬 | [链接](https://github.com/earendil-works/pi/issues/9223) |
| #9036 | openai-codex SSE 解析器全量缓冲导致 Heap OOM | CLOSED | 2💬 | [链接](https://github.com/earendil-works/pi/issues/9036) |

**关注理由**：
- **#7547** 是最活跃的 Windows 兼容性讨论，直接影响大量开发者使用决策
- **#9132/#9218** 暴露发布流程缺陷，0.85.1 已修复，值得发布流程关注
- **#9212/#9036** 反映 gateway 路由和流式解析在生产环境中的稳定性问题

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 内容摘要 | 链接 |
|---|------|------|----------|------|
| #9222 | fix: 拒绝活跃会话期间的重载 | OPEN | RPC 模式下工具执行中 reload 导致 runner 失效，现增加 `isStreaming` 检查 | [链接](https://github.com/earendil-works/pi/pull/9222) |
| #9096 | feat: 新增 Meta provider（含 Muse OAuth） | OPEN | 解决 #7543，支持 Meta API，每日 token 刷新机制，流式输出为 burst 模式 | [链接](https://github.com/earendil-works/pi/pull/9096) |
| #9219 | fix: 保留宿主 UI 原型方法及 Proxy traps | CLOSED | 修复 `wrapUIPromptContext` 对象展开丢失自定义 UI 方法的问题 | [链接](https://github.com/earendil-works/pi/pull/9219) |
| #9214 | feat: 支持句中调用 skill/template | CLOSED | 修复 #8457，`/skill:name` 和 `/template` 不再仅限输入首行 | [链接](https://github.com/earendil-works/pi/pull/9214) |
| #9137 | feat: 新增 Nix flake | OPEN | 为 NixOS/Nix 用户提供声明式构建支持 | [链接](https://github.com/earendil-works/pi/pull/9137) |
| #9117 | feat: 以 system message delta 传递 prompt/工具变更 | OPEN | 替代全量重写 top-level prompt，支持会话中动态更新工具集 | [链接](https://github.com/earendil-works/pi/pull/9117) |
| #8734 | feat: 支持 OpenAI Responses 顶级 instructions | OPEN | 将系统提示移至 `instructions` 字段，兼容 OpenAI Responses API | [链接](https://github.com/earendil-works/pi/pull/8734) |
| #9170 | fix: 声明 pi-server 运行时依赖 | CLOSED | 修复 0.85.0 发布包缺失 `@earendil-works/pi-server` 依赖 | [链接](https://github.com/earendil-works/pi/pull/9170) |
| #9182 | fix: 在失效 extension runner 上跳过会话事件 | CLOSED | 修复 session replacement 竞态中二次 teardown 导致崩溃 | [链接](https://github.com/earendil-works/pi/pull/9182) |
| #9208 | fix: RPC 示例使用正确的 `--no-extensions` 标志 | CLOSED | 修复 #9205，示例因无效 flag 立即退出 | [链接](https://github.com/earendil-works/pi/pull/9208) |

---

## 5. 功能需求趋势

| 方向 | 相关 Issues/PRs | 趋势说明 |
|------|----------------|----------|
| **跨平台 TUI 兼容性** | #7547、#6300、#5200、#9169 | Windows TUI 问题持续高发，IME、全屏、终端渲染是主要痛点 |
| **多 Provider 扩展** | #9096（Meta）、#7610（LLM Gateway）、#5473（Requesty）、#7317/#6676（OpenAI Responses） | 社区对 Meta、LLM Gateway 等新增 provider 需求旺盛，Responses API 适配加速 |
| **本地模型支持** | #9216（Ollama qwen3.8） | 本地模型流式错误和自动压缩回归问题引起关注 |
| **发布质量与工具链** | #9132、#9218、#9223、#9172 | npm 发布依赖声明缺失暴露构建流程缺陷，Nix flake（#9137）受关注 |
| **会话与上下文管理** | #6451、#9051、#8896、#9116 | 会话压缩、上下文投影、`/export` 数据丢失等问题反映对上下文完整性的重视 |

---

## 6. 开发者关注点

**高频痛点：**
1. **Windows TUI 体验**：输入重绘（#6300）、IME 候选窗口（#5200）、全屏图像渲染（#9169）等问题频发，社区呼吁统一修复优先级
2. **npm 发布质量**：#9132 和 #9218 揭示 `pi-server`/`pi-client` 未声明为依赖，导致 `pi-subagents` 子进程启动失败，发布流程需强化
3. **Gateway 路由与计费**：#9210 报告 Anthropic 缓存计费错误（1h 缓存被按 5m 费率计费），#9211 指出 `vercelGatewayRouting` 配置未生效
4. **流式解析稳定性**：#9036 的 Codex SSE 全量缓冲导致 OOM，反映长响应场景下的内存管理隐患
5. **斜杠命令 UX**：#9220 暴露 IME 与自动补全的竞态条件，中文用户受影响显著

**积极信号：**
- `PI_OFFLINE` 行为文档化改进（#8684 已关闭）
- 句中 skill/template 调用（#9214）已合入，显著提升交互灵活性
- Meta provider（#9096）和 Nix flake（#9137）扩展生态覆盖

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报
**日期：2026-09-06**

---

## 1. 今日速览

Qwen Code 在过去24小时内发布了三个 v0.23.0/v0.23.1 夜视版本，核心更新聚焦于 Web Shell 动态工作流的可视化与管理能力。社区活跃度持续走高，共收录 50 个新更新 Issue 与 50 条 PR，其中导出体积优化、MCP 配置加载、后台 Shell 输出丢失等问题引发广泛关注。

---

## 2. 版本发布

过去24小时共发布 **3 个 Nightly/Preview 版本**，核心变更集中于 Web Shell 性能优化与工作流可视化：

| 版本 | 类型 | 核心更新 |
|------|------|----------|
| v0.23.1-preview.0 | Preview | Web Shell 会话工作流项目派生优化 |
| v0.23.0-nightly.20260905.0c945a6136 | Nightly | 动态工作流运行可视化与管理（PR #10594） |
| v0.23.0-nightly.20260905.e3d26283e6 | Nightly | 同上 |

**主要变更：**
- **feat(web-shell)**: 支持可视化与管理动态工作流运行（#10594）
- **perf(web-shell)**: 派生会话工作流项目，减少重复计算

---

## 3. 社区热点 Issues（Top 10）

### 🔥 P1 级别关键问题

**1. [Issue #11031] 导出 HTML 体积过大（19.5MB），停止嵌入 Web Shell 运行时**
- **重要性**: 当前每次导出都内联完整的 React + Web Shell 运行时，空会话也达 19.5MB，严重影响分发效率
- **状态**: OPEN | 评论: 5
- [链接](https://github.com/QwenLM/qwen-code/issues/11031)

**2. [Issue #10780] 长会话重连导致传输管道被历史回放淹没**
- **重要性**: 长生命周期 daemon 会话（10^5–10^6 tokens）每次客户端重连都会产生多 MB 历史回放，阻塞甚至断开无关会话
- **状态**: CLOSED | 评论: 4
- [链接](https://github.com/QwenLM/qwen-code/issues/10780)

**3. [Issue #11119] 后台 Shell 输出在会话运行时回收后丢失**
- **重要性**: `run_shell_command` 启动的后台任务（如 CI 轮询循环）在 turn 结束后输出和唤醒通知被静默丢弃，导致会话卡死
- **状态**: OPEN | 评论: 3
- [链接](https://github.com/QwenLM/qwen-code/issues/11119)

**4. [Issue #7771] MCP 持久化配置未在启动时加载到主进程代理**
- **重要性**: Qwen Desktop 将 MCP 服务器配置持久化到用户设置，但 Electron 主进程启动时未将其加载到 main-process MCP 代理，导致重启后配置丢失
- **状态**: OPEN | 评论: 5 | 更新时间: 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/issues/7771)

### 🔧 性能与体验问题

**5. [Issue #10865] Session Workflow 投影在每次渲染中派生三次**
- **重要性**: 明显性能浪费，每次渲染重复构建索引，已在 nightly 版本中通过 PR #10594 优化
- **状态**: OPEN | 评论: 3
- [链接](https://github.com/QwenLM/qwen-code/issues/10865)

**6. [Issue #9645] Web Shell 左侧栏会话 spinner 在长任务中途消失**
- **重要性**: 用户无法准确感知会话状态，#9487 的修复在 VS Code 伴侣环境中失效（见 #10989）
- **状态**: CLOSED | 评论: 4
- [链接](https://github.com/QwenLM/qwen-code/issues/9645)

**7. [Issue #11108] Cmd+A 在 composer 中选中整个页面而非输入内容**
- **重要性**: 基础 UX 问题，影响用户在 Web Shell 中的日常编辑体验
- **状态**: OPEN | 评论: 3
- [链接](https://github.com/QwenLM/qwen-code/issues/11108)

**8. [Issue #9704] 并发会话加载时工具结果写入延迟导致瞬态错误**
- **重要性**: 实时会话 transcript 中工具调用执行时加载，会显示 "Tool result missing from saved history" 临时占位符
- **状态**: OPEN | 评论: 3
- [链接](https://github.com/QwenLM/qwen-code/issues/9704)

### 🛠 开发与 CI 问题

**9. [Issue #10879] hk4 主机仍携带共享 ecs-qwen 标签，导致发布与 PR CI 竞争**
- **重要性**: 发布验证任务被 pin 到 hk4 专用标签，但标签共享导致 CI 资源竞争
- **状态**: OPEN | 评论: 4
- [链接](https://github.com/QwenLM/qwen-code/issues/10879)

**10. [Issue #11109] release.yml 重复执行已完成的工作，某 20 分钟步骤未验证任何内容**
- **重要性**: 发布流程效率低下，两个连续发布运行在今日均超时
- **状态**: OPEN | 评论: 3
- [链接](https://github.com/QwenLM/qwen-code/issues/11109)

---

## 4. 重要 PR 进展（Top 10）

### 🚀 新功能

**1. [PR #11003] feat: 通过 ACP 将子 Agent 轮次委托给外部 Agent（Claude Code 优先）**
- **内容**: 允许子 Agent 定义通过 ACP 协议将执行委托给外部编程 Agent，所有操作以会话轮次形式重新发布
- **状态**: OPEN | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11003)

**2. [PR #11086] feat(serve): 将扩展作用域限制到工作区运行时**
- **内容**: 使全局扩展目录可通过每个工作区选定的运行时访问，协调扩展状态到实时工作区运行时，暴露工作区限定的 daemon 和 SDK 访问
- **状态**: OPEN (autofix/takeover) | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11086)

**3. [PR #11054] feat(web-shell): 添加无头全局轮次导航**
- **内容**: 作为 Phase 2A，引入有界轮次元数据、历史 transcript 缓存、精确的 live/persisted 轮次定位器
- **状态**: OPEN | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11054)

**4. [PR #11053] feat(web-shell): 添加全局轮次导航 Phase 2 客户端数据层**
- **内容**: 实现设计规范的客户端数据层，维护 transcript 窗口切片记录，将未加载范围视为显式值范围
- **状态**: OPEN | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11053)

### 🐛 关键修复

**5. [PR #11145] fix(serve): 在 ACP 预热后加载持久化 MCP 配置**
- **内容**: 修复 #7771，在 `qwen serve` 启动时立即调用 `reconcileMcpConfiguration()`，无需手动重载
- **状态**: OPEN | 创建于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11145)

**6. [PR #11144] fix(cli): 将实时 transcript 读取屏障置于工具结果写入之后**
- **内容**: 修复 #9704，在 ACP agent 路径中将磁盘读取屏障置于进行中的工具结果写入之后，路由恢复清理共享辅助函数
- **状态**: OPEN | 创建于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11144)

**7. [PR #9466] refactor: 将回退映射锚定到稳定提示标识**
- **内容**: 回退现在通过持久化提示标识解析目标提示，而非位置性轮次顺序， Survives 重编号或重排序操作
- **状态**: OPEN (review/self-reported) | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/9466)

### 🧪 CI/CD 改进

**8. [PR #10439] ci: 监控 /resolve 连续失败并创建跟踪 Issue**
- **内容**: 添加对 `@qwen-code /resolve` 的定时监控，连续失败时创建跟踪 Issue，成功后关闭
- **状态**: OPEN (autofix/takeover) | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/10439)

**9. [PR #11103] ci: 不再因单个 vitest worker RPC 饥饿导致 Test 作业失败**
- **内容**: 添加 `classify-infra-flake.mjs` 脚本，将仅因 vitest worker IPC 故障的情况转为 warning 而非失败
- **状态**: OPEN | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11103)

**10. [PR #11134] fix(ci): 重试 macOS E2E 分片瞬态全绿死亡（一次）**
- **内容**: macOS E2E 环节获得与 Linux `sandbox:none` 环节相同的单次预算门控重试机制
- **状态**: OPEN (review/self-reported) | 更新于 2026-09-06
- [链接](https://github.com/QwenLM/qwen-code/pull/11134)

---

## 5. 功能需求趋势

从社区 Issues 和 PRs 中提炼出以下核心方向：

| 方向 | 关注热点 | 代表 Issue/PR |
|------|----------|---------------|
| **Web Shell 体验优化** | 工作流可视化、全局轮次导航、UI 性能 | #10594, #11054, #11053, #10938 |
| **导出体积优化** | 停止嵌入完整运行时、 Transcript-only 入口 | #11031, #11091, #11100 |
| **MCP 工具链集成** | 配置持久化加载、外部 Agent 委托 | #7771, #11145, #11003 |
| **Daemon/Session 稳定性** | 长会话重连、后台任务存活、工具结果写入 | #10780, #11119, #9704, #11144 |
| **CI/CD 可靠性** | 发布流程优化、测试 flake 处理 | #10879, #11109, #10439, #11103 |
| **多 Agent/Channel 管理** | 命名会话 worktree、会话旋转、扩展作用域 | #11015, #8927, #11086 |

---

## 6. 开发者关注点

### 高频痛点

1. **导出文件体积过大** — 19.5MB 的空会话 HTML 严重影响分享与分发，社区强烈期待 transcript-only 入口方案落地

2. **MCP 配置重启丢失** — 桌面应用重启后 MCP 服务器配置未自动加载，需手动重新配置，影响工作流连续性

3. **长会话重连性能** — 数百轮次、百万 token 级别的会话在客户端重连时产生多 MB 历史回放，阻塞其他会话

4. **后台任务生命周期管理** — `run_shell_command` 启动的后台任务在 turn 结束后输出和通知被静默丢弃，导致 CI 轮询等场景会话卡死

5. **VS Code 伴侣环境与 Web Shell 状态同步** — #9487 的加载指示器修复在 VS Code 扩展中失效，daemon prompt authority 仅在 sidebar 挂载处被轮询

6. **基础 UX 问题** — Cmd+A 在 composer 中选中整个页面、spinner 状态不一致等影响日常使用体验

### 社区反馈热度最高的领域

- **性能优化**（6 个 P1/P2 Issue 涉及渲染/导出/传输性能）
- **Session 生命周期管理**（5 个 Issue 关注重连、回收、后台任务）
- **IDE 集成稳定性**（3 个 Issue 涉及 VS Code/IntelliJ 插件行为）
- **CI/CD 效率**（3 个 Issue 关注发布流程和测试稳定性）

---

*数据截止时间：2026-09-06 | 数据来源：github.com/QwenLM/qwen-code*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI / Codewhale 社区动态日报
**日期**：2026-09-06  
**数据源**：github.com/Hmbown/DeepSeek-TUI（项目已逐步迁移至 Codewhale 品牌标识）

---

## 1. 今日速览
v0.9.12 正式发布，底层 CLI 与 npm 包标识由 `deepseek-tui` 全面迁移至 `codewhale`，旧命令别名进入废弃期。过去 24 小时社区重心集中于 Windows 后端真实性校验、文件换行符跨平台一致性及 Fleet 多 Agent 调度稳定性，同时语音输入、自定义主题选择器等体验优化 PR 已合入主干。

---

## 2. 版本发布
- **v0.9.12** 已上线。公告明确：`codewhale` 为 Shannon Labs 公开产品标识，原 `deepseek-tui` npm 包及 `deepseek`/`d` 命令别名已废弃，后续不再维护。开发者需切换至 `codewhale` 命令与发布源。
- 关联里程碑追踪与交接文档已归档至 #5573。

---

## 3. 社区热点 Issues（精选 10 条）

| 编号 | 标题/类型 | 核心关注点 | 链接 |
|------|-----------|------------|------|
| #5573 | [里程碑] v0.9.12 版本追踪 | 产品 PRD、Operator 交接、Working branch 与自测流程的总入口 | [链接](https://github.com/Hmbown/Codewhale/issues/5573) |
| #5316 | [架构] TUI Crate 解耦总览（EPIC-005） | 所有子功能与 PR 归集点，反映项目模块化重构方向 | [链接](https://github.com/Hmbown/Codewhale/issues/5316) |
| #5620 | [Bug] 上下文压力警告未触发 Agent 响应 | 警告瞬时返回且无后续动作，存在静默上下文退化风险 | [链接](https://github.com/Hmbown/Codewhale/issues/5620) |
| #5909 | [Bug] `write_file` 静默转换 CRLF 为 LF | 覆盖写入丢失 Windows 换行符，与 `edit_file` 行为不一致 | [链接](https://github.com/Hmbown/Codewhale/issues/5909) |
| #5908 | [Bug] Win32 输入假阳性成功 | PowerShell 失败仍返回 `action_sent: true`

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*