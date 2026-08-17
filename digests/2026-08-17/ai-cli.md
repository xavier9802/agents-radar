# AI CLI 工具社区动态日报 2026-08-17

> 生成时间: 2026-08-17 01:42 UTC | 覆盖工具: 10 个

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
**日期：2026-08-17 | 分析模型：Agnes-2.0-Flash (Sapiens AI)**

---

## 1. 生态全景

2026年Q3的AI CLI工具生态呈现"功能深水区"特征：各工具已从基础会话能力竞争转向**多Agent协作、终端原生体验、计费透明度**等深层工程问题。社区反馈显示，开发者对工具可靠性的要求显著提升，Windows稳定性、MCP认证链鲁棒性、长上下文管理成为跨平台共性问题。OpenAI Codex与GitHub Copilot CLI在平台兼容性上承压，而Claude Code、Gemini CLI、Qwen Code则在Agent架构与可扩展性上加速迭代。

---

## 2. 各工具活跃度对比

| 工具 | Issues (Top) | PR 更新 | Release | 核心动态 |
|------|-------------|---------|---------|----------|
| **Claude Code** | 10 | 3 | 无 | 安全glob修复、MCP draft-07兼容、桌面端多账号诉求 |
| **OpenAI Codex** | 10 | 11 (全Closed) | 无 | Windows稳定性修复潮、TUI优化、`codex doctor`增强 |
| **Gemini CLI** | 10 | 11 | v0.56.0-nightly | 子代理恢复、挂起修复、`--list-models` CLI能力 |
| **GitHub Copilot CLI** | 10 | 1 (陈旧) | 无 (1.0.80) | MCP OAuth回归、会话管理缺陷、Windows Socket问题 |
| **Kimi Code CLI** | 4 | 3 | 无 | `--starting-prompt`合并、Session管理诉求、记忆层优化 |
| **OpenCode** | 10+ | 10 | 无 | 计费逻辑争议、V2文档重构、Desktop渲染优化 |
| **Pi** | 10 | 9 | 无 | Kiro OAuth、MiniMax图生图、缓存token追踪修复 |
| **Qwen Code** | 10 | 11 (多OPEN) | v0.21.11-nightly | agent-team核心缺陷修复潮、autofix安全加固、Aone Code集成 |
| **DeepSeek TUI** | 10 | 10 | v0.9.8 (终版) | 子代理Schema精简、宽屏排版修复、bwrap沙箱扩展 |
| **Grok Build** | — | — | — | 无活动 |

**活跃度排名（PR+Issue综合）**：Qwen Code > Pi ≈ DeepSeek TUI > Gemini CLI > OpenCode > Claude Code > OpenAI Codex > Copilot CLI > Kimi Code CLI

---

## 3. 共同关注的功能方向

| 方向 | 涉及工具 | 具体诉求 |
|------|---------|----------|
| **多Agent协作与子代理管理** | Gemini CLI、Qwen Code、DeepSeek TUI、Claude Code | 子代理恢复机制、终止原因传递、Schema精简、自动派发逻辑 |
| **会话管理与持久化** | Copilot CLI、Kimi Code CLI、OpenCode、Claude Code | 会话恢复失败、静默归档、无删除UI、上下文丢失 |
| **终端/TUI原生体验** | Claude Code、OpenAI Codex、Pi、OpenCode、Qwen Code、DeepSeek TUI | tmux兼容、宽屏适配、Windows输入延迟、TUI卡死/崩溃 |
| **MCP/插件生态** | Claude Code、Copilot CLI、OpenAI Codex | OAuth认证回归、并发竞态、插件文件锁冲突、权限配置 |
| **计费与用量透明度** | OpenAI Codex、OpenCode、Pi、DeepSeek TUI | Subagent配额异常、付费余额未生效、缓存token重复计算、实时定价不可靠 |
| **跨平台兼容性** | OpenAI Codex、Copilot CLI、Kimi Code CLI、DeepSeek TUI | Windows系统级卡顿、非系统盘路径、PowerShell默认目录 |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|---------|---------|---------|
| **Claude Code** | 桌面端多工作流管理、MCP生态、安全规则 | 多组织/多角色开发者、企业用户 | TUI优先+桌面端演进，强调配置健壮性 |
| **OpenAI Codex** | IDE集成深化、远程移动协作、诊断工具链 | VS Code/JetBrains用户、远程开发者 | 桌面应用+CLI双轨，强调整合性与诊断能力 |
| **Gemini CLI** | Agent可靠性、Memory系统、评估基建 | 研究/评估场景、Agent架构探索者 | 子代理分层架构，强调可观测性与质量门禁 |
| **GitHub Copilot CLI** | GitHub生态集成、MCP OAuth、CI/CD流水线 | GitHub企业用户、自动化集成场景 | 与GitHub Actions深度绑定，强调企业级认证链 |
| **Kimi Code CLI** | Session生命周期、记忆层架构 | 中文开发者、大项目连续开发场景 | 轻量级设计，借鉴OpenClaw记忆模式 |
| **OpenCode** | 跨设备同步、V2迁移、计费透明度 | 多端用户、付费模型重度用户 | Desktop+Web UI双端，V2重构中 |
| **Pi** | 模型目录准确性、扩展生命周期、多提供商接入 | 多模型切换者、扩展开发者 | 高兼容性抽象层，强调API行为精确性 |
| **Qwen Code** | 多Agent协作、CI/CD安全隔离、Review平台 | 团队协作开发者、企业CI/CD场景 | agent-team原生架构，强调安全边界与可审计性 |
| **DeepSeek TUI** | 长上下文模型适配、沙箱精细化、宽屏体验 | DeepSeek模型用户、Zig/Swift开发者 | Rust原生、bwrap沙箱、按模型路由策略 |

---

## 5. 社区热度与成熟度

### 高热度社区
- **OpenCode**：50+ Issue更新/24h，计费争议与V2迁移痛点集中爆发，反映用户基数大但产品成熟度待验证
- **Qwen Code**：agent-team模块连续4个P1 Issue，处于功能快速迭代期，社区反馈推动修复潮
- **Pi**：TUI性能与模型目录准确性问题高频，反映多提供商集成复杂性

### 快速迭代阶段
- **Gemini CLI**：v0.56.0-nightly持续发布，子代理恢复等核心Bug推进中，处于可靠性攻坚期
- **DeepSeek TUI**：品牌迁移完成，子代理Schema精简、宽屏适配等工程优化加速，技术路线清晰

### 成熟稳定期
- **Claude Code**：无Release但PR质量高（安全修复、MCP兼容），社区诉求集中在功能增强而非基础稳定性
- **OpenAI Codex**：PR全为Closed，修复闭环效率高，但Windows稳定性问题暴露平台适配成本

### 待观察
- **GitHub Copilot CLI**：PR活跃度低（16 Issues/24h仅1陈旧PR），MCP OAuth回归问题需紧急响应
- **Kimi Code CLI**：Issue数量少，功能诉求明确但开发节奏较慢

---

## 6. 值得关注的趋势信号

### 信号1：子代理架构进入"可靠性验收期"
Gemini CLI (#22323)、Qwen Code (#9276/#9282)、DeepSeek TUI (#5458) 集中暴露子代理恢复、任务派发、Schema设计问题。**对开发者的参考价值**：多Agent系统设计需优先考虑终止状态传递、权限继承、调试可观测性，而非仅关注任务拆分能力。

### 信号2：计费透明度成为付费体验分水岭
OpenAI Codex (#35463)、OpenCode (#36506/#33318/#42938)、Pi (#8218/#8119) 均出现用量统计异常。缓存token重复计算、跨订阅余额隔离、Subagent配额耗尽等问题引发信任危机。**对开发者的参考价值**：计费逻辑需与模型调用链解耦，提供可审计的用量明细与降级策略。

### 信号3：Windows平台适配成本被低估
OpenAI Codex (6+ Issues)、Copilot CLI (#4463)、Kimi Code CLI (#2600) 的Windows问题呈现系统性特征：系统级输入延迟、Socket权限、多盘符路径解析。**对开发者的参考价值**：跨平台CLI工具需在架构层面隔离OS差异，而非补丁式修复。

### 信号4：MCP生态进入"认证链压力测试"
Claude Code (MCP draft-07)、Copilot CLI (OAuth回归#4490/#4472)、OpenAI Codex (权限配置清理) 共同反映MCP集成在并发、超时、权限继承等边界场景下的脆弱性。**对开发者的参考价值**：MCP客户端需实现Token刷新防竞态、连接池管理、权限降级策略。

### 信号5：终端原生体验从"可用"走向"好用"
宽屏适配 (DeepSeek TUI #5436/#5446)、tmux兼容 (Claude Code #74122/Qwen Code #8962)、Vim模式 (Codex #38907) 等需求表明开发者对终端工作流有深度依赖。**对开发者的参考价值**：TUI工具需将终端兼容性作为一等公民需求，而非事后适配。

---

**总结**：AI CLI工具生态正从"功能竞赛"转向"工程成熟度竞赛"。多Agent协作、计费透明度、跨平台稳定性、MCP认证链鲁棒性成为下一阶段的差异化竞争点。开发者在选择工具时，应优先评估目标工具在自身核心场景（如Windows开发、多Agent编排、企业级认证集成）下的可靠性表现，而非仅关注模型能力或功能列表。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告

**数据截止**: 2026-08-17 | **分析范围**: anthropics/skills 热门 PR（50）+ Issues（50）

---

## 1. 热门 Skills 排行

| 排名 | PR | 技能名称 | 功能简述 | 状态 | 链接 |
|------|-----|---------|---------|------|------|
| 1 | #83 | skill-quality-analyzer / skill-security-analyzer | 元技能：从结构、文档、安全等五维度评估 Skill 质量 | OPEN | [PR #83](https://github.com/anthropics/skills/pull/83) |
| 2 | #568 | servicenow | 企业级 ServiceNow 平台 Skill，覆盖 ITSM/ITOM/SecOps/FSM 等全模块 | OPEN | [PR #568](https://github.com/anthropics/skills/pull/568) |
| 3 | #1367 | self-audit | 交付前自检：机械文件验证 + 四维度推理质量门控 | OPEN | [PR #1367](https://github.com/anthropics/skills/pull/1367) |
| 4 | #723 | testing-patterns | 全栈测试 Skill：Testing Trophy、AAA 模式、React Testing Library、TDD | OPEN | [PR #723](https://github.com/anthropics/skills/pull/723) |
| 5 | #514 | document-typography | AI 生成文档的排版质量控制：孤立行、孤儿段、编号对齐 | OPEN | [PR #514](https://github.com/anthropics/skills/pull/514) |
| 6 | #486 | odt | OpenDocument 格式支持：创建/填充/解析/转换（ODT/ODS/ODF） | OPEN | [PR #486](https://github.com/anthropics/skills/pull/486) |
| 7 | #181 | SAP-RPT-1-OSS | SAP 开源表格基础模型预测分析 Skill（Apache 2.0） | OPEN | [PR #181](https://github.com/anthropics/skills/pull/181) |
| 8 | #1479 | plan-file-hygiene | 规划产物生命周期管理，解决上下文窗口中历史规划文件堆积问题 | OPEN | [PR #1479](https://github.com/anthropics/skills/pull/1479) |

---

## 2. 社区需求趋势（基于 Issue 讨论）

| 需求方向 | 代表 Issue | 核心诉求 | 热度 |
|---------|-----------|---------|------|
| **生态安全治理** | #492 | 社区 Skill 假冒官方 `anthropic/` 命名空间，存在信任边界滥用风险，亟需命名隔离机制 | ⭐⭐⭐⭐⭐（43 评论） |
| **组织内 Skill 共享** | #228 | 当前 Skill 只能通过手动下载/上传共享，企业用户需要组织级 Skill 库和直接分享链接 | ⭐⭐⭐⭐（16 评论） |
| **skill-creator 工具链修复** | #556 / #1419 | `run_eval.py` 触发评估始终返回 0% recall，导致 Skill 描述优化循环基于噪声迭代 | ⭐⭐⭐⭐（12 评论） |
| **推理质量门控** | #1385 / #1367 | 全生命周期质量管道：任务前校准 → 对抗性审查 → 交付验证，三个门控互补覆盖不同失败模式 | ⭐⭐⭐（8 评论） |
| **Context 消耗管控** | #1487 | `claude-api` Skill 单次工具调用注入约 156k tokens，存在上下文窗口耗尽风险 | ⭐⭐⭐ |
| **企业系统对接** | #568 / #181 / #1175 | ServiceNow、SAP、SharePoint 等企业内部平台 Skill 需求持续旺盛 | ⭐⭐⭐ |

---

## 3. 高潜力待合并 Skills

以下 PR 讨论活跃、issue 关联明确，且修复的是系统性问题，近期合并概率较高：

| PR | 类型 | 核心价值 | 关键支撑 Issue |
|----|------|---------|---------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | 🐛 Bugfix | 修复 `run_eval.py` 在 Windows 上的 stream 读取、trigger 检测和并行 worker 问题 | #556、#1419 |
| [#541](https://github.com/anthropics/skills/pull/541) | 🐛 Bugfix | 修复 DOCX tracked change 与已有 bookmark 的 `w:id` 冲突导致文档损坏 | 无独立 issue，但 #12 有同类文档格式问题反馈 |
| [#539](https://github.com/anthropics/skills/pull/539) | 🐛 Bugfix | `skill-creator` YAML 前缀校验：未引号 description 含 `:` 时静默截断 | #202（最佳实践） |
| [#1538](https://github.com/anthropics/skills/pull/1538) | 🐛 Spec 对齐 | 修复两篇 Skill 的 `name` 字段与目录名不一致，使其符合 Agent Skills spec | 规范合规类，门槛低 |
| [#538](https://github.com/anthropics/skills/pull/538) | 🐛 Bugfix | 修复 PDF Skill 中 8 处大小写敏感的文件引用错误（`REFERENCE.md` → `reference.md`） | 同类：#12 DOCX 格式问题 |
| [#210](https://github.com/anthropics/skills/pull/210) | ✏️ 改进 | 重写 frontend-design Skill，提升指令可执行性和上下文一致性 | 对应 #202 对 skill-creator 最佳实践的讨论延伸 |
| [#1050](https://github.com/anthropics/skills/pull/1050) | 🐛 Bugfix | Windows 11 上 `subprocess.Popen(["claude"])` 失败（应为 `claude.cmd`）的单行修复 | #1298 的前置依赖 |

---

## 4. Skills 生态洞察

> **当前社区最集中的诉求是：从"功能扩展"转向"质量基建"——用户不再只需更多 Skill，更需要可靠的 Skill 评估工具链、严格的质量门控机制，以及安全的生态治理规范。**

这一判断由三条并行信号支撑：
1. **eval 工具链的 0% recall 问题**关联至少 4 个独立 Issue/PR，是阻碍 Skill 质量提升的最大瓶颈；
2. **self-audit** 和 **Reasoning Quality Gate Pipeline** 两个独立提案均聚焦交付前质量验证；
3. **命名空间信任滥用**（Issue #492，43 评论）标志着生态规模扩张后安全治理成为首要议题。

---

*报告生成时间：2026-08-17 | 数据来源：github.com/anthropics/skills*

---



# 📊 Claude Code 社区动态日报
**日期**：2026-08-17  
**数据来源**：[github.com/anthropics/claude-code](https://github.com/anthropics/claude-code)

---

## 1. 今日速览
今日无新版本发布，社区活跃度集中在 **TUI 终端兼容性修复** 与 **桌面端多账号/会话管理诉求**。MCP draft-07 兼容性与安全 glob 规则修复已进 PR，反映开发者对长上下文可控性与配置健壮性的要求快速上升。

---

## 2. 版本发布
过去 24 小时内 **无新 Release**。

---

## 3. 社区热点 Issues（Top 10）

| 编号 | 状态 | 标题 | 评论/👍 | 核心价值 |
|------|------|------|---------|----------|
| [#18435](https://github.com/anthropics/claude-code/issues/18435) | OPEN | 桌面端支持多账号管理与 Profile 切换 | 167 / 730 | 社区长期高赞需求，直接影响多角色/多组织工作流 |
| [#86142](https://github.com/anthropics/claude-code/issues/86142) | ✅CLOSED | MCP draft-07 outputSchema 被拒绝执行 | 11 / 5 | 修复 MCP 生态兼容性，已合入解决 |
| [#70062](https://github.com/anthropics/claude-code/issues/70062) | OPEN | `claude-api` 工具耗尽上下文窗口 | 11 / 5 | API 调用记录占用 prompt budget，影响长会话稳定性 |
| [#71547](https://github.com/anthropics/claude-code/issues/71547) | OPEN | AskUserQuestion 点击即自动提交 | 10 / 21 | TUI 交互回归，误触导致任务中断，修复优先级高 |
| [#74122](https://github.com/anthropics/claude-code/issues/74122) | OPEN | v2.1.200 起 tmux 内 TUI 渲染乱码 | 8 / 2 | 高频终端用户痛点，仅强制重绘可恢复 |
| [#75392](https://github.com/anthropics/claude-code/issues/75392) | ✅CLOSED | `plugin install --scope project` 覆盖配置 | 8 / 1 | 插件管理逻辑缺陷，已修复 |
| [#71700](https://github.com/anthropics/claude-code/issues/71700) | OPEN | Kitty 键盘协议受 terminal-name 白名单限制 | 8 / 2 | Alacritty 等终端无法启用完整键盘协议 |
| [#72181](https://github.com/anthropics/claude-code/issues/72181) | OPEN | 桌面端无法删除“最近项目”记录 | 7 / 15 | 桌面端文件管理 UX 缺失 |
| [#72126](https://github.com/anthropics/claude-code/issues/72126) | OPEN | 支持手动排序桌面端侧边栏分组 | 3 / 19 | 提升多项目工作区组织效率 |
| [#71803](https://github.com/anthropics/claude-code/issues/71803) | OPEN | 允许 Agent 自主触发 `/compact` | 6 / 3 | 长链路 Agent 上下文管理的核心诉求 |

---

## 4. 重要 PR 进展
过去 24 小时内共更新 3 条 PR，均聚焦配置解析与 CI 基建：

1. **[#87079](https://github.com/anthropics/claude-code/pull/87079) fix(security-guidance): `**` glob 匹配零深度路径**  
   修正 `fnmatch` 默认行为导致安全规则漏配根目录文件的问题。`**/*.ts` 等规则现已能按文档预期覆盖顶层路径，对安全扫描完整性至关重要。

2. **[#87077](https://github.com/anthropics/claude-code/pull/87077) fix(pr-review-toolkit): 修复所有 Agent 的无效 YAML frontmatter**  
   修复 Agent 描述中包含 `Assistant: "..."` 等类 YAML 键值对时导致的解析失败，恢复正常加载与路由。

3. **[#87125](https://github.com/anthropics/claude-code/pull/87125) feat(ci): 新增 python-package-conda.yml**  
   补充标准化的 Conda 打包 CI 工作流，便于社区以 Conda 环境分发与依赖管理。

---

## 5. 功能需求趋势

- **多账号与工作区治理**：#18435 持续霸榜，结合 #72181 / #72126，桌面端正从“单会话工具”向“多工作流管理平台”演进。
- **TUI 终端原生体验**：tmux 

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-08-17**

---

## 1. 今日速览

今日 Codex 社区动态集中在 Windows 端性能稳定性与权限配置修复。Windows 平台用户持续反馈桌面应用导致的系统级鼠标卡顿和输入延迟问题，已成为社区最关注的痛点。同时，团队在 PR 中推进了 `codex doctor` 诊断工具增强、TUI 体验优化及权限策略清理，反映出对 CLI 工具链和桌面端用户体验的持续投入。

---

## 2. 版本发布

过去 24 小时内 **无新版本发布**。

---

## 3. 社区热点 Issues

| # | 标题 | 热度 | 为什么重要 |
|---|------|------|-----------|
| #20214 | Windows 11 Pro 上 Codex App 频繁冻结/卡顿 | 👍 85 / 106 评论 | 高关注度 Windows 性能问题，影响 Pro 用户日常使用体验 |
| #38546 | Windows 桌面应用无管理员权限时导致系统级鼠标卡顿 | 👍 13 / 31 评论 | 新发现（48h 内），系统级影响，可能与 #20214 同源 |
| #25319 | 将 VS Code 扩展聊天限制在当前工作区/项目 | 👍 62 / 29 评论 | 关键 IDE 集成需求，影响多项目开发者工作流 |
| #23200 | 支持 Codex Mobile 连接无头远程 Linux 主机 | 👍 48 / 18 评论 | 移动协作场景核心需求，解决远程开发痛点 |
| #20864 | Desktop App 扫描全部 sessions 导致性能下降 | 👍 6 / 21 评论 | 长期性能问题，影响历史会话管理效率 |
| #28855 | Windows 端间歇性系统输入延迟 | 👍 20 / 20 评论 | 独立于 #20214 的新维度性能问题，系统级影响 |
| #35463 | Subagents 夜间耗尽整周配额，用量统计异常 | 👍 0 / 11 评论 | 计费公平性问题，影响 Pro 用户信任度 |
| #32797 | Windows 26.707 版本残留 147 个 node.exe 进程（13.9 GiB） | 👍 1 / 7 评论 | 严重的资源泄漏问题，直接关系系统稳定性 |
| #38856 | `/responses/compact` 404 导致会话连续性丢失 | 👍 0 / 6 评论 | 新报告（昨日），影响远程会话恢复和上下文管理 |
| #38929 | macOS 启动 App 后 mds_stores CPU 飙升至 250-700% | 👍 0 / 1 评论 | P0 级 macOS 主机级影响，可能导致系统不可用 |

> **Windows 稳定性**是当前社区最集中的反馈方向，6 个以上独立 issue 指向同一类系统级性能问题。

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 说明 |
|----|------|------|------|
| #38921 | 压缩 TUI 中成功的命令活动 | ✅ Closed | 将连续成功命令合并为 `Ran N commands` 显示，保留完整 transcript，减少 TUI 噪音 |
| #38919 | 拒绝过时的 app-server permission profile 字段 | ✅ Closed | 修复客户端使用已移除字段时静默忽略权限设置的安全隐患 |
| #38918 | 改进 `codex doctor` 网络诊断 | ✅ Closed | 新增对 Responses 推理端点的探测，分类 TLS/代理/超时等故障类型 |
| #38916 | 兼容遗留 `:project_roots` 权限条目 | ✅ Closed | 防止旧权限配置中 `:project_roots` 被当作未知字段丢弃，保障文件系统限制生效 |
| #38907 | Vim 历史 up 编辑排队消息 | ✅ Closed | 提升 TUI Vim 模式编辑体验，支持恢复并编辑最新的排队跟进消息 |
| #38902 | 按环境执行 shell 变量策略 | ✅ Closed | 不同环境可配置独立的 shell 变量策略，增强安全性与灵活性 |
| #38894 | TUI 新增 `/cd` 工作目录命令 | ✅ Closed | 允许在保持会话历史的前提下切换本地空闲会话的工作目录 |
| #38840 | 远程握手识别 Mac mini 主机 | ✅ Closed | 在 macOS 远程控制场景中自动发送 `mac_mini` 设备类型头 |
| #38837 | TUI composer 共享编辑器快捷键映射 | ✅ Closed | 统一聊天 composer 与内嵌 textarea 的编辑器快捷键行为 |
| #38830 | 将外部编辑器缓冲区隔离出沙盒可写路径 | ✅ Closed | 防止编辑器缓冲区（含当前 composer 文本）被放置在受限文件系统中 |

---

## 5. 功能需求趋势

基于今日 Issues 分析，社区关注方向如下：

1. **性能与稳定性（高优先级）**
   - Windows 系统级卡顿、输入延迟、资源泄漏是最高频痛点
   - macOS 启动时 mds_stores CPU 飙升至 P0 级别

2. **IDE 集成深化**
   - 工作区/项目级会话隔离需求强烈（#25319）
   - JetBrains 等 IDE 的连通性问题持续出现

3. **远程与跨设备协作**
   - Mobile 控制无头 Linux 主机是明确的高投票功能请求
   - ChatGPT 与 Codex 桌面端的上下文双向同步需求

4. **计费透明度与准确性**
   - Subagent 配额耗尽、周限额重置异常等问题引发信任担忧
   - 用户对用量统计逻辑的准确性高度敏感

5. **CLI/TUI 体验优化**
   - Vim 模式、快捷键、命令压缩等 TUI 交互改进持续受欢迎
   - `codex doctor` 诊断能力被频繁提及

---

## 6. 开发者关注点

**核心痛点汇总：**

| 类别 | 具体问题 | 相关 Issues |
|------|---------|-------------|
| Windows 稳定性 | 系统级鼠标/输入延迟、应用卡顿 | #20214, #38546, #28855 |
| 资源泄漏 | node.exe 进程堆积（13.9 GiB）、session 扫描性能 | #32797, #20864 |
| 沙盒/Sandbox | 读取操作失败、ACL 错误、Base64 限制 | #28248, #32315 |
| 计费异常 | Subagent 耗尽配额、限额重置错误 | #35463, #18018, #38900 |
| 会话管理 | compact 404 导致上下文丢失 | #38856 |
| 跨平台一致性 | Windows 渲染 LaTeX 错误、macOS 启动性能 | #37561, #38929 |
| 功能缺失 | 快捷键切换模型/推理力度、移动远程支持 | #26819, #23200 |

---

*数据来源：github.com/openai/codex，统计时段 2026-08-16 ~ 2026-08-17*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报 | 2026-08-17

## 1. 今日速览

今日 Gemini CLI 发布 v0.56.0-nightly 版本，主要修复 SSR Agent 相关构建配置问题。社区关注焦点集中在 **子代理恢复机制** 与 **Agent 挂起问题**，其中 #22323 和 #21409 分别获得 12 条和 8 条评论，反映开发者对 Agent 可靠性的迫切需求。

---

## 2. 版本发布

### v0.56.0-nightly.20260817.g9a15c45fb
**链接**: [PR #28858](https://github.com/google-gemini/gemini-cli/pull/28858)

- 修复 SSR Agent 构建问题（Issue #21911）：为 `packages/cli/tsconfig` 添加 `composite` flag，解决 evals tsconfig 引用导致的构建失败

---

## 3. 社区热点 Issues

| Issue | 标题 | 优先级 | 热度 | 重要性说明 |
|-------|------|--------|------|-----------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery after MAX_TURNS 被错误报告为 GOAL success | P1 | 💬12 👍2 | **核心 Bug**：subagent 达到最大轮次限制后仍被标记为成功，掩盖了实际中断情况，影响调试与评估准确性 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent 永久挂起 | P1 | 💬8 👍8 | **高共鸣 Bug**：调用 generalist agent 时 CLI 无限挂起，用户反馈等待超 1 小时，社区点赞最多 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | 利用模型的 Bash 亲和性进行零依赖 OS 沙箱与执行后意图路由 | P2 | 💬8 | **架构级增强**：建议让 Gemini 3 模型以更原生的方式使用 POSIX 工具链，同时保障安全性 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | 健壮的组件级评估体系 | P1 | 💬7 | **评估基建**：追踪 76 个行为测试的运行框架，直接影响版本发布质量门禁 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST 感知文件读取/搜索/映射的影响评估 | P2 | 💬7 | **性能优化方向**：评估 AST 工具能否减少 token 消耗与轮次，降低代码库探索噪声 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini 未主动使用 skills 和 sub-agents | P2 | 💬6 | **UX 痛点**：用户反馈即使有匹配的 skill，模型也不会自动调用，需显式指令才触发 |
| [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) | 停止 Auto Memory 无限重试低信号会话 | P2 | 💬5 | **Memory 系统 Bug**：低质量会话被反复 surfaced，消耗资源且干扰用户体验 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | 添加确定性脱敏并减少 Auto Memory 日志 | P2 🔒 | 💬4 | **安全增强**：当前脱敏在内容进入模型 context 后发生，存在信息泄露风险 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell 命令执行完成后卡在 "Waiting input" | P1 | 💬4 👍3 | **高频 Bug**：简单命令执行完毕但 CLI 仍显示等待状态，影响自动化流程 |
| [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) | 增强 browser_agent 韧性：自动会话接管与锁恢复 | P3 | 💬4 | **可用性改进**：当前 browser_agent 遇到锁定的 profile 直接 fail-fast，缺乏恢复机制 |

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 说明 |
|----|------|------|------|
| [#28815](https://github.com/google-gemini/gemini-cli/pull/28815) | 修复 #22323：在 subagent 恢复期间保留原始终止原因 | 🔵 OPEN | 关键修复：确保 subagent 达到 MAX_TURNS 时正确传递终止原因，而非错误标记为 GOAL |
| [#28812](https://github.com/google-gemini/gemini-cli/pull/28812) | 修复 #21477：通过执行超时防止 TUI 无限挂起 | 🔵 OPEN | 解决 bare Linux 终端启动时 "Initializing..." 永久卡住的问题 |
| [#28848](https://github.com/google-gemini/gemini-cli/pull/28848) | 修复：非交互模式下优雅处理 refreshAuth 失败 | 🔵 OPEN | 改进 `--prompt` 模式的认证失败体验，避免崩溃并输出清晰错误码 |
| [#28847](https://github.com/google-gemini/gemini-cli/pull/28847) | 更新 /clear 命令文档以包含上下文重置说明 | 🔵 OPEN | 修复文档遗漏：此前未说明 /clear 同时清除活跃上下文 |
| [#28844](https://github.com/google-gemini/gemini-cli/pull/28844) | 添加 Homebrew 弃用通知 | ✅ CLOSED | gemini-cli 在 homebrew-core 已弃用，引导新用户使用 npm 安装 |
| [#28843](https://github.com/google-gemini/gemini-cli/pull/28843) | 新增 `--list-models` 标志以 JSON 格式输出可用模型 | ✅ CLOSED | 支持程序化模型发现，便于集成与编排场景 |
| [#28820](https://github.com/google-gemini/gemini-cli/pull/28820) | 改进隐私通知措辞与选项选择 | 🔵 OPEN | 修复隐私通知中矛盾的描述，澄清用户可选范围 |
| [#28813](https://github.com/google-gemini/gemini-cli/pull/28813) | 为 packages/cli tsconfig 添加 composite flag | ✅ CLOSED | 修复 SSR Agent 构建失败问题（今日 release 修复项） |
| [#28814](https://github.com/google-gemini/gemini-cli/pull/28814) | 修复集成测试中的 TypeScript strict-null 错误 | 🔵 OPEN | 清理 hooks-system.test.ts 等文件的类型错误 |
| [#28849](https://github.com/google-gemini/gemini-cli/pull/28849) | 批量更新 73 个 npm 依赖 | ✅ CLOSED | 包含 simple-git、@modelcontextprotocol/sdk、puppeteer-core 等关键依赖升级 |

---

## 5. 功能需求趋势

基于 Issue 分析，社区关注方向呈以下趋势：

1. **Agent 可靠性与可观测性**：子代理恢复、终止原因传递、调试信息完整性是当前最高频痛点（#22323、#21409、#21763）
2. **Memory 系统优化**：Auto Memory 的日志脱敏、低信号会话去重、补丁验证机制亟需完善（#26522、#26525、#26523、#26516）
3. **评估与质量基建**：组件级评估框架（#24353）和 AST 感知工具（#22745、#22746）是提升模型调用效率的关键方向
4. **终端交互体验**：Shell 命令挂起（#25166）、交互式 prompt 卡死（#22465）、终端 resize 性能（#21924）影响日常使用
5. **安全与隐私**：浏览器 Agent 配置覆盖失效（#22267）、子代理无权限运行（#22093）、命令执行安全（#22672）持续受到关注

---

## 6. 开发者关注点

**高频痛点：**

- **Agent 行为不可预期**：模型不主动使用 skills/sub-agents（#21968）、subagent 无权限运行（#22093），开发者需要显式指令才能触发预期行为
- **挂起与卡死问题频发**：Generalist agent 挂起（#21409）、Shell 命令完成但仍显示等待（#25166）、交互式 prompt 卡住（#22465）
- **浏览器 Agent 鲁棒性不足**：Wayland 环境下失败（#21983）、配置覆盖被忽略（#22267）、缺乏会话恢复机制（#22232）
- **调试信息不完整**：Bug report 不包含 subagent 上下文（#21763），subagent 轨迹难以分享（#22598）
- **临时文件管理混乱**：模型在随机目录创建 tmp 脚本（#23571），增加清理负担

**积极信号：**

- `--list-models` 等 CLI 可程序化能力获得支持（#28843）
- 评估基础设施持续完善， behavioral evals 已达 76 个（#24353）
- 文档质量改善，/clear 命令说明得到补充（#28847）

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-08-17 | 数据来源：github.com/github/copilot-cli**

---

## 1. 今日速览

过去24小时内 Copilot CLI 社区共更新16个 Issues，无新版本发布。热点问题集中在 **MCP OAuth 认证回归**、**Windows 平台兼容性** 以及 **会话管理缺陷**。其中 #4490 报告的 RFC 8414 §3.3 回归问题影响 Atlassian 用户，#4463 涉及 Windows Socket 权限错误，#4506 暴露了内存压力监控逻辑的缺陷。

---

## 2. 版本发布

过去24小时无新 Release。当前版本仍为 **1.0.80**（从 Issue #4490 确认）。

---

## 3. 社区热点 Issues（Top 10）

### 🔴 #4490 [OPEN] Atlassian MCP OAuth 认证在 1.0.80 中中断（RFC 8414 §3.3 回归）
**重要性：** 明确标注为版本回归，影响 Atlassian MCP 用户，需紧急修复。
**社区反应：** 作者提供了完整复现步骤，但尚无官方回复。
🔗 [Issue #4490](https://github.com/github/copilot-cli/issues/4490)

### 🔴 #4463 [OPEN] Windows MCP OAuth 间歇性 Socket 错误 10013
**重要性：** Windows 平台专属问题，`os error 10013` 表示权限被拒绝，影响 OAuth 授权流程的稳定性。
**社区反应：** 暂无评论，需 Windows 用户验证。
🔗 [Issue #4463](https://github.com/github/copilot-cli/issues/4463)

### 🔴 #4488 [OPEN] 插件更新因文件锁失败（Access is denied）
**重要性：** 多会话/VS Code 共存时的常见痛点，插件更新被无关进程的文件锁阻塞。
**社区反应：** 作者描述了明确的复现场景，影响范围较大。
🔗 [Issue #4488](https://github.com/github/copilot-cli/issues/4488)

### 🔴 #4506 [OPEN] 内存压力监控在低上下文使用率时过度压缩
**重要性：** 揭示了 watchdog 逻辑缺陷——仅基于内存压力而非上下文使用量触发压缩，导致无效循环直至 OOM。
**社区反应：** 典型性能/稳定性问题，已 CLOSED 类似问题后再次出现。
🔗 [Issue #4506](https://github.com/github/copilot-cli/issues/4506)

### 🟡 #4505 [OPEN] 会话恢复后残留过期连接 ID，导致所有 prompt 失败
**重要性：** 会话恢复功能的核心缺陷，用户中断后无法继续对话，`/fork` 也无法解决。
**社区反应：** 直接影响长期使用体验。
🔗 [Issue #4505](https://github.com/github/copilot-cli/issues/4505)

### 🟡 #4507 [OPEN] 仓库级 enabledPlugins 配置在非交互模式（-p）下被忽略
**重要性：** 配置不一致问题——交互模式正常、非交互模式失效，影响 CI/CD 流水线集成。
**社区反应：** 作者对比了两种模式的差异，便于定位。
🔗 [Issue #4507](https://github.com/github/copilot-cli/issues/4507)

### 🟡 #4472 [OPEN] 并发工具调用期间 Token 刷新导致 in-flight 请求被取消
**重要性：** MCP OAuth 并发场景下的竞态条件，每个并发调用都会独立触发刷新并创建新服务实例。
**社区反应：** 高并发场景下的稳定性隐患。
🔗 [Issue #4472](https://github.com/github/copilot-cli/issues/4472)

### 🟡 #4473 [OPEN] claude-haiku-4.5 子代理不支持 medium reasoning effort
**重要性：** 模型路由配置缺陷，内部自动路由到不支持的推理级别。
**社区反应：** 影响使用 Haiku 模型的用户。
🔗 [Issue #4473](https://github.com/github/copilot-cli/issues/4473)

### 🟡 #4486 [OPEN] 编辑权限请求"超时"
**重要性：** 长时间运行或多会话场景下的权限交互问题，用户反映近期才开始出现。
**社区反应：** 多位多会话用户可能受影响。
🔗 [Issue #4486](https://github.com/github/copilot-cli/issues/4486)

### 🟡 #4474 [OPEN] General Chat 在会话恢复超时后被静默归档，无恢复 UI
**重要性：** 用户体验缺陷——会话在无警告情况下消失，且没有 UI 可恢复。
**社区反应：** 长时间会话用户的高度关注点。
🔗 [Issue #4474](https://github.com/github/copilot-cli/issues/4474)

---

## 4. 重要 PR 进展

### PR #3163 [OPEN] ViewSonic monitor
**状态：** 自 2026-05-06 创建，最近于 2026-08-16 更新。
**内容：** 关联 Issue #2591、#3561、#3559，涉及 GitHub Actions runner 初始化。该 PR 更新较久，暂无明显进展。
🔗 [PR #3163](https://github.com/github/copilot-cli/pulls/3163)

> **注：** 过去24小时内无其他 PR 更新，社区活跃点主要集中在 Issue 讨论。

---

## 5. 功能需求趋势

从本期 Issues 中可提炼以下社区关注方向：

| 方向 | 关键词 | 相关 Issues |
|------|--------|-------------|
| **MCP 认证与稳定性** | OAuth、token 刷新、并发 | #4490, #4463, #4472 |
| **会话管理改进** | 恢复、归档、持久化 | #4505, #4474, #4489, #4502 |
| **插件系统完善** | 依赖管理、更新机制、文件锁 | #4488, #4487 |
| **多平台兼容** | Windows、非交互模式 | #4463, #4488, #4507 |
| **模型与推理控制** | reasoning effort、子代理 | #4473 |
| **配置一致性** | 仓库级设置、非交互模式 | #4507 |

---

## 6. 开发者关注点

**高频痛点：**

1. **MCP OAuth 认证链脆弱** — 多个 Issue 指向同一子系统的不同缺陷（#4490 回归、#4463 Windows 权限、#4472 并发竞态），表明 OAuth 流程在边界场景下缺乏鲁棒性。

2. **会话持久化体验差** — 用户反映恢复失败、静默归档、无取消归档入口（#4505、#4474、#4502），与"长时间运行会话"的使用模式不匹配。

3. **插件更新与文件锁冲突** — 多进程/多会话共存是常见开发场景，但当前实现无法处理文件锁竞争（#4488），且缺乏依赖管理机制（#4487）。

4. **配置行为不一致** — 仓库级设置在交互/非交互模式下的行为差异（#4507）损害了可预期性，尤其影响自动化集成。

5. **敏感内容过滤** — #4498 报告了模型生成了不当用词，虽为边缘案例，但反映了内容安全审查的持续关注。

---

*报告生成时间：2026-08-17 | 数据截止：过去24小时*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-08-17** | **数据来源：github.com/MoonshotAI/kimi-cli**

---

## 1. 今日速览

过去24小时 Kimi Code CLI 社区无新版本发布，但有 **1 个 PR 合并**（`--starting-prompt` 启动参数功能），以及 **1 个新 Issue 被关闭**（定时任务管理入口缺失）。开发者持续关注 session 管理、记忆层优化和 Windows 兼容性等问题。

---

## 2. 版本发布

**无新版本发布**。

---

## 3. 社区热点 Issues

基于当前数据，挑选 **4 个** 最值得关注的 Issue：

### 🔥 #1783 [Feature Request] 添加 /delete 命令删除 session
- **作者**: proccl | **评论**: 6 | **👍**: 1
- **重要性**: Session 管理是 CLI 高频需求，目前需手动删除 `~/.kimi/sessions/` 目录，体验差且易误删敏感数据
- **社区反应**: 有 6 条评论和 1 个 👍，说明已有开发者关注此功能

🔗 [Issue #1783](https://github.com/MoonshotAI/kimi-cli/issues/1783)

### 🐛 #2600 [Bug] Windows PowerShell 7 默认D盘启动路径问题
- **作者**: RooKichenn | **评论**: 5
- **重要性**: 影响 Windows 非系统盘用户，属于平台兼容性问题
- **复现**: 0.33 版本，PowerShell 7 默认启动目录为 D 盘时无法找到路径

🔗 [Issue #2600](https://github.com/MoonshotAI/kimi-cli/issues/2600)

### 💡 #1478 [Enhancement] 优化记忆层
- **作者**: hahy36 | **评论**: 4
- **重要性**: 大项目场景下记忆能力是核心痛点，用户反馈参考文档中缺乏记忆相关说明
- **建议**: 借鉴 OpenClaw 的记忆架构（SOUL.md / USER.md / MEMORY.md）

🔗 [Issue #1478](https://github.com/MoonshotAI/kimi-cli/issues/1478)

### ✅ #2605 [CLOSED] 定时任务管理入口缺失
- **作者**: WilliamLambertCN | **评论**: 1
- **状态**: 已关闭（可能已解决或确认不做）
- **问题**: `CronCreate` 工具创建的定时任务在 TUI 中无管理入口，用户无从查看

🔗 [Issue #2605](https://github.com/MoonshotAI/kimi-cli/issues/2605)

---

## 4. 重要 PR 进展

### ✅ #864 [CLOSED] feat: --starting-prompt flag to prompt without exit
- **作者**: stebbins | **状态**: 已合并
- **功能**: 新增 `--starting-prompt` / `-s` 参数，允许不退出直接进入 prompt 模式
- **关联**: closes #887

🔗 [PR #864](https://github.com/MoonshotAI/kimi-cli/pull/864)

### 🔄 #2324 [OPEN] fix(web): handle BrokenPipeError in SessionProcess.send_message
- **作者**: Ricardo-M-L | **状态**: 待处理
- **修复**: `SessionProcess.send_message` 在 subprocess 退出后写入 stdin 会抛出 `BrokenPipeError`
- **影响**: 提升 Web 模式稳定性

🔗 [PR #2324](https://github.com/MoonshotAI/kimi-cli/pull/2324)

### 🔄 #2449 [OPEN] fix(string): strip newlines in shorten_middle before length check
- **作者**: Ricardo-M-L | **状态**: 待处理
- **修复**: `shorten_middle` 函数在输入较短时提前返回，未处理换行符，导致后续长度检查不准确
- **影响**: 修复工具调用参数渲染的单行摘要显示问题

🔗 [PR #2449](https://github.com/MoonshotAI/kimi-cli/pull/2449)

---

## 5. 功能需求趋势

从当前 Issues 中提炼出 **3 个** 核心方向：

| 方向 | 优先级 | 说明 |
|------|--------|------|
| **Session 管理** | 高 | 用户需要更灵活的 session 生命周期管理（删除、清理、搜索） |
| **记忆层优化** | 高 | 大项目场景下记忆能力不足，需完善记忆架构和文档 |
| **平台兼容性** | 中 | Windows 非系统盘启动、PowerShell 默认路径等问题需修复 |

---

## 6. 开发者关注点

### 高频痛点
1. **Session 管理体验差** - 手动删除目录操作繁琐，缺乏 CLI 命令
2. **记忆能力不足** - 大项目场景下 AI 记忆断层，影响连续性
3. **Windows 路径问题** - 非系统盘启动时路径解析异常

### 高频需求
1. `/delete` 或 `/remove` 命令删除 session
2. 完善记忆层文档和架构设计
3. Windows 多盘符兼容性修复
4. 定时任务（Cron）用户管理入口

---

**报告生成时间**: 2026-08-17 | **数据范围**: 过去 24 小时

*注：当前数据集中仅包含 4 个 Issues 和 3 个 PRs，未提取不存在的条目。*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode 社区动态日报
**日期：2026-08-17** | 数据来源：anomalyco/opencode

---

## 1. 今日速览

过去24小时无新版本发布，但 Issues 活跃度极高（50条更新），社区反馈集中在计费/订阅体验问题（付费余额未生效、Go计划与Zen余额冲突）以及 Desktop/TUI 稳定性（卡死、超时、剪贴板异常）两大方向。V2 文档重构与桌面端渲染优化持续推进中。

---

## 2. 版本发布

无新版本发布。

---

## 3. 社区热点 Issues

| Issue | 热度 | 主题 | 关注度 |
|-------|------|------|--------|
| [#7957](https://github.com/anomalyco/opencode/issues/7957) | 🔥 49👍 | Ctrl+C 不应退出 OpenCode，与通用复制快捷键冲突 | 长期痛点，高优先级 |
| [#13626](https://github.com/anomalyco/opencode/issues/13626) | 🔥 15👍 | Web UI 跨设备自动同步项目 | 多设备用户强需求 |
| [#41470](https://github.com/anomalyco/opencode/issues/41470) | 16💬 | Docker/VSCode Server 中剪贴板复制静默失败 | 容器部署用户高频反馈 |
| [#36506](https://github.com/anomalyco/opencode/issues/36506) | 11💬 | 付费 Zen 模型统一报 "Upstream request failed"，免费模型正常 | 影响付费用户体验 |
| [#26602](https://github.com/anomalyco/opencode/issues/26602) | 11💬 | Desktop 5分钟 Headers Timeout，无视 provider 超时配置 | 本地慢推理 Provider 用户痛点 |
| [#33318](https://github.com/anomalyco/opencode/issues/33318) | 9💬 | 付费余额已充值仍触发 FreeUsageLimitError | 计费逻辑问题 |
| [#42938](https://github.com/anomalyco/opencode/issues/42938) | 2💬 | Go 计划用量达 100% 后无法使用 Zen 余额 | 订阅降级体验问题 |
| [#25120](https://github.com/anomalyco/opencode/issues/25120) | 5👍 | 压缩性能优化：~90% 成本可避免的 cache miss | 核心性能讨论 |
| [#20458](https://github.com/anomalyco/opencode/issues/20458) | 4👍 | TUI 退出后鼠标转义序列乱码 | 终端用户体验 |
| [#32366](https://github.com/anomalyco/opencode/issues/32366) | 6💬 | Stream 错误后 UI 永久卡在 "thinking..." | 错误恢复机制缺失 |

---

## 4. 重要 PR 进展

| PR | 状态 | 内容 |
|----|------|------|
| [#42952](https://github.com/anomalyco/opencode/pull/42952) | ✅ 已关闭 | **性能优化**：用预渲染 APNG 替换 25 个 CSS opacity 动画，降低 spinner CPU 占用 |
| [#42766](https://github.com/anomalyco/opencode/pull/42766) | 🔄 开放 | **重构**：Desktop 统一使用当前 session messages，移除冗余 legacy Message/Part 转录层 |
| [#42949](https://github.com/anomalyco/opencode/pull/42949) | 🔄 开放 | **功能**：新增 Code Mode 执行专用渲染器，展示子工具进度与错误状态 |
| [#42944](https://github.com/anomalyco/opencode/pull/42944) | ✅ 已关闭 | **修复**：修正 V2 后台子 agent 状态分类逻辑，正确显示 running 子任务进度 |
| [#42945](https://github.com/anomalyco/opencode/pull/42945) | ✅ 已关闭 | **UX 优化**：Skill timeline 展示优化，含图标/标签/分隔符/解析结果 |
| [#42947](https://github.com/anomalyco/opencode/pull/42947) | ✅ 已关闭 | **文档**：V2 文档体系重构，新增 CLI 配置/Provider/主题/键位/插件专页 |
| [#42951](https://github.com/anomalyco/opencode/pull/42951) | 🔄 开放 | **生态**：新增 ClawMetry 到生态系统页（本地 session 成本/Token 看板） |
| [#42948](https://github.com/anomalyco/opencode/pull/42948) | ✅ 已关闭 | **调试**：info 级别日志所有 spawn 进程（可执行文件/参数/工作目录） |
| [#42049](https://github.com/anomalyco/opencode/pull/42049) | ✅ 已关闭 | **TUI修复**：仅当工具明确报告 detached 状态时才显示 Background 徽章 |
| [#37392](https://github.com/anomalyco/opencode/pull/37392) | ✅ 已关闭 | **核心修复**：Anthropic refusal 错误现显示具体原因分类与解释，不再硬编码单一提示 |

---

## 5. 功能需求趋势

- **跨平台/跨设备同步**：Web UI 项目自动同步（#13626）和 session 收藏置顶（#42940）反映用户对多端一致性的强烈需求。
- **计费/订阅透明度**：多条 Issue（#36506、#33318、#42938）指向付费模型调用与余额扣除逻辑不一致，社区期望更清晰的用量指示与降级策略。
- **错误恢复与状态稳定性**：卡死（#32366、#40468）、超时（#26602）、空响应静默失败（#41469）频发，开发者希望增强 session 状态机容错。
- **V2 迁移体验**：V2 CLI 加载 OpenTUI 泄漏临时文件（#37671）和 shell 重启语义（#36348）显示早期 V2 用户仍在磨合边缘场景。

---

## 6. 开发者关注点

| 痛点类别 | 具体问题 | 关联 Issue |
|----------|----------|------------|
| **快捷键冲突** | Ctrl+C 被占用退出应用，与系统复制习惯冲突 | #7957 |
| **容器环境剪贴板** | VSCode Server/Docker 中复制不生效 | #41470 |
| **计费逻辑不一致** | 付费余额未生效、Go 计划与 Zen 余额无法协同 | #36506、#33318、#42938 |
| **超时配置失效** | Desktop provider timeout 配置被硬编码 5 分钟覆盖 | #26602 |
| **错误恢复缺失** | Stream 错误后 UI 永久卡在 thinking，无用户提示 | #32366、#40468 |
| **空响应处理** | LLM 返回 0 token 时 session 静默结束，无错误信息 | #41469 |
| **输入重复** | Prompt 提交后重复显示导致模型困惑 | #42943 |
| **V2 资源泄漏** | 无头命令仍加载 OpenTUI 并残留临时 .so 文件 | #37671 |
| **版本同步** | Web UI 与 CLI 版本号不同步显示 | #24286、#29301 |
| **本地语音输入** | Wispr Flow 在 VSCode 集成终端无法注入文本 | #34499 |

---

**报告生成时间**：2026-08-17 | **分析模型**：Agnes-2.0-Flash (Sapiens AI)

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 — 2026-08-17

## 1. 今日速览

过去 24 小时无新版本发布，仓库活跃于 Issue 修复与功能迭代：46 条 issue 更新、9 条 PR 合并。社区焦点集中在 **TUI 性能与渲染问题**、**pi.dev 目录端点超时**、**openai-completions 缓存 token 追踪**，以及 **Kiro OAuth 登录支持** 的落地。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 社区热点 Issues

| 编号 | 标题 | 关注度 | 原因 |
|------|------|--------|------|
| [#5023](https://github.com/earendil-works/pi/issues/5023) | terminal scrolls to beginning without reason | 🔥 高 | 随机滚动 bug，影响日常使用，14 条评论 |
| [#8029](https://github.com/earendil-works/pi/issues/8029) | Very slow performance on moving in prompt editor | 🔥 高 | 大 buffer 下箭头键延迟线性增长（7000 行需 1650ms） |
| [#6300](https://github.com/earendil-works/pi/issues/6300) | Windows: Input line is redrawn on every keystroke | 🔥 高 | Windows TUI 每键入一个字符即换行，影响交互体验 |
| [#8198](https://github.com/earendil-works/pi/issues/8198) | pi.dev provider catalog endpoint times out | 🔥 高 | 目录刷新持续超时，影响模型列表更新 |
| [#8036](https://github.com/earendil-works/pi/issues/8036) | Edit tool crashes TUI when rendering large diff | 🔥 高 | 大 diff（14.5MB）渲染时 TUI 崩溃，session resume 同样受影响 |
| [#7994](https://github.com/earendil-works/pi/issues/7994) | openai-completions: reasoning_details round-trip | 中 | 仅支持加密 reasoning，signed-text replay 不可用，OpenRouter 官方反馈 |
| [#7870](https://github.com/earendil-works/pi/issues/7870) | Remote catalog overlay 错误覆盖 contextWindow | 中 | z-ai/glm-5.2 被错误解析为 262k，实际应为 1M 上下文 |
| [#5581](https://github.com/earendil-works/pi/issues/5581) | sendMessage triggerTurn bypass before_agent_start | 中 | 自定义消息绕过 agent 生命周期钩子，影响扩展开发 |
| [#8061](https://github.com/earendil-works/pi/issues/8061) | Context budget ignores maxTokens output reservation | 中 | 请求在 78% 输入时被拒绝，自动 compact 重试同样失败 |
| [#8166](https://github.com/earendil-works/pi/issues/8166) | custom message injected mid-tool-batch breaks tool_calls | 中 | 扩展调用 sendMessage 导致后续 turn 的 tool_calls 相邻性断裂，返回 400 错误 |

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 说明 |
|----|------|------|------|
| [#8218](https://github.com/earendil-works/pi/pull/8218) | fix: getStats tokens.total 排除缓存 token | ✅ 已合 | 修复 DeepSeek/OpenAI 缓存定价下 total 被高估 ~120 倍的问题，避免 compaction 过早触发 |
| [#8217](https://github.com/earendil-works/pi/pull/8217) | feat: 新增 Kiro OAuth device login | ✅ 已合 | 支持 Kiro 设备的 OAuth 授权码登录与 refresh，包含错误处理与协议覆盖 |
| [#8209](https://github.com/earendil-works/pi/pull/8209) | fix: defer non-turn custom messages to end of turn | ✅ 已合 | 修复 streaming 期间 `triggerTurn: false` 的消息直接写入导致 tool_calls 断裂的问题（closes #8166） |
| [#8119](https://github.com/earendil-works/pi/pull/8119) | fix: track Kimi cached tokens | ✅ 已合 | 正确解析 Kimi 响应中顶层 `usage.cached_tokens`，避免缓存 token 被重复计入输入 |
| [#8124](https://github.com/earendil-works/pi/pull/8124) | feat: xAI 路由至 Responses API，默认模型切换为 Grok 4.6 | ✅ 已合 | 默认使用 Responses API 而非 Completions，模型从 Grok 4.5 升级至 Grok 4.6 |
| [#8204](https://github.com/earendil-works/pi/pull/8204) | fix: retry hung pi.dev catalog refreshes | ✅ 已合 | 为 pi.dev 目录请求增加单次超时，修复间歇性 TLS 连接无响应导致的整体刷新阻塞 |
| [#8193](https://github.com/earendil-works/pi/pull/8193) | feat: MiniMax image-to-image generation | ✅ 已合 | 新增 `minimax-images` API 模块，支持图生图功能，补齐双区域 image endpoint 覆盖 |
| [#8219](https://github.com/earendil-works/pi/pull/8219) | — | ❌ 已关闭 | 作者要求忽略 |
| [#8076](https://github.com/earendil-works/pi/pull/8076) | DRAFT: dev branch with new harness | ❌ 已关闭 | 草稿分支，未合并 |

---

## 5. 功能需求趋势

1. **TUI 性能优化** — prompt editor 大文本渲染延迟、Windows 输入重绘问题持续被报告，社区对交互流畅性期望较高。
2. **模型目录准确性** — contextWindow 被覆盖、catalog 端点超时、GLM/Qwen 模型路由错误等问题频发，反映模型目录管理的复杂性。
3. **openai-completions 兼容性** — 缓存 token（Kimi、DeepSeek）、reasoning_details round-trip 等细节修复显示开发者对 API 行为精确性的诉求。
4. **扩展生命周期完善** — `before_agent_start`、`agent_end` 钩子、消息注入时机等问题表明扩展 API 仍在打磨中。
5. **新提供商接入** — Kiro OAuth、MiniMax 图生图等新功能持续加入，生态扩展活跃。

---

## 6. 开发者关注点

- **TUI 渲染稳定性**：Windows 下的字符重绘、大 diff 渲染崩溃、主题切换遗留颜色等 bug 影响用户体验，需优先修复。
- **性能瓶颈**：prompt editor 在长文本场景下线性的键盘响应延迟是开发者的明确痛点。
- **模型配置准确性**：`contextWindow`、`maxTokens`、provider 路由错误会直接导致请求失败，catalog 端点的可靠性需保障。
- **扩展 API 语义一致性**：`sendMessage` 消息注入时机、`triggerTurn` 行为与 agent 生命周期钩子的关系需要更清晰的文档或约束。
- **计费统计准确性**：缓存 token 被重复计算或遗漏会直接影响成本估算，开发者对此类细节敏感。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报
**日期：2026-08-17**

---

## 1. 今日速览

Qwen Code 发布 v0.21.11-nightly，核心更新包括 autofix 的 deny-by-default 足迹门控和 web-shell 的 DSW EAS 全链路回归测试。社区多 Agent 协作（agent-team）功能出现多项关键缺陷反馈，涉及消息通信、任务派发和 prompt 设计等问题，开发团队已同步提交修复 PR。

---

## 2. 版本发布

### v0.21.11-nightly.20260817.195128a17a

- **autofix 加固**：新增 deny-by-default 的足迹门控（footprint gate）和位置窗口审查（positional window censuses），强化 PR #9156 的安全边界
- **web-shell 全链路回归**：完成 DSW EAS full E2E r3 基准测试，覆盖 SWE-bench Verified (500) 和 Terminal-Bench 2.0 (89) 场景

🔗 [GitHub Release](https://github.com/QwenLM/qwen-code/releases)

---

## 3. 社区热点 Issues

| Issue | 标题 | 重要性 | 评论 |
|-------|------|--------|------|
| [#9276](https://github.com/QwenLM/qwen-code/issues/9276) | Team members cannot send ordinary messages to their leader | 🔴 Agent 协作核心通信故障 | 5 |
| [#9089](https://github.com/QwenLM/qwen-code/issues/9089) | autofix: PAT-bearing jobs share a host with untrusted branch code | 🔴 CI/CD 安全风险 | 5 |
| [#9291](https://github.com/QwenLM/qwen-code/issues/9291) | Unsupported image MIME can abort a Responses-compatible session | 🟡 多模态兼容性问题 | 3 |
| [#9290](https://github.com/QwenLM/qwen-code/issues/9290) | Interactive session crashes when opening an errored agent-team tab | 🟡 交互稳定性 | 3 |
| [#9282](https://github.com/QwenLM/qwen-code/issues/9282) | Manual team task assignment persists without dispatching work | 🟡 任务派发逻辑缺陷 | 3 |
| [#9283](https://github.com/QwenLM/qwen-code/issues/9283) | Agent-team prompts contradict automatic delivery | 🟡 Prompt 设计矛盾 | 3 |
| [#5966](https://github.com/QwenLM/qwen-code/issues/5966) | 0.19.3 UI不定期错误，中文输入法完全无效 | 🟡 长期未解决的 UX 痛点 | 5 |
| [#8962](https://github.com/QwenLM/qwen-code/issues/8962) | cannot use qwen under tmux | 🟡 tmux 环境兼容性 | 3 |
| [#9275](https://github.com/QwenLM/qwen-code/issues/9275) | Feature request: Add GitHub Copilot authentication | 🟢 新集成需求 | 2 |
| [#9294](https://github.com/QwenLM/qwen-code/issues/9294) | Add ClawMetry to the Ecosystem section | 🟢 生态扩展 | 2 |

**热点分析**：多 Agent 协作（agent-team）是当前社区关注的焦点，连续 4 个高优先级 Issue 集中在该模块，涉及消息路由、任务派发和 prompt 一致性。CI/CD 安全隔离问题也引发持续关注。

---

## 4. 重要 PR 进展

| PR | 标题 | 类型 | 状态 |
|----|------|------|------|
| [#9295](https://github.com/QwenLM/qwen-code/pull/9295) | fix(core): omit image media the model endpoint cannot safely consume (#9291) | Bug 修复 | OPEN |
| [#9289](https://github.com/QwenLM/qwen-code/pull/9289) | fix(core): dispatch manually assigned team tasks to their owner | Bug 修复 | OPEN |
| [#9284](https://github.com/QwenLM/qwen-code/pull/9284) | fix(core): align agent-team prompts and TeamCreate description with actual delivery | Bug 修复 | OPEN |
| [#9292](https://github.com/QwenLM/qwen-code/pull/9292) | fix(cli): contain agent-tab render errors instead of exiting the session | Bug 修复 | OPEN |
| [#9279](https://github.com/QwenLM/qwen-code/pull/9279) | feat(review): enforce the resolved severity floor at the posting boundary | 功能增强 | OPEN |
| [#9267](https://github.com/QwenLM/qwen-code/pull/9267) | refactor(review): build the incremental scope from the PR's diff, not a check | 重构 | OPEN |
| [#9228](https://github.com/QwenLM/qwen-code/pull/9228) | fix(ci): narrow serve-ab's self-hosted wipe to the A/B checkout dirs | Bug 修复 | OPEN |
| [#9226](https://github.com/QwenLM/qwen-code/pull/9226) | feat(review): Aone Code read path (second review-platform provider) | 新功能 | OPEN |
| [#9262](https://github.com/QwenLM/qwen-code/pull/9262) | feat(autofix): audit the approach instead of stopping on growth-budget breach | 功能增强 | OPEN |
| [#8169](https://github.com/QwenLM/qwen-code/pull/8169) | feat(core): add OpenAI Responses API content generator | 新功能 | OPEN |

**重点进展**：
- **Agent 协作修复潮**：#9284、#9289、#9295 形成配套修复，分别解决 prompt 一致性和任务派发问题
- **Review 平台扩展**：#9226 新增 Aone Code 读取路径，成为第二个 review-platform provider
- **CI 稳定性加固**：#9228 修复自托管 ECS 池上工作区误删问题

---

## 5. 功能需求趋势

基于 Issue 分析，社区关注方向呈现以下趋势：

| 方向 | 热度 | 代表 Issue |
|------|------|------------|
| **多 Agent 协作** | 🔥🔥🔥 | #9276, #9282, #9283, #9290 |
| **CI/CD 与自动化** | 🔥🔥🔥 | #9089, #9228, #9265 |
| **Web Shell 体验** | 🔥🔥 | #8962, #9234 |
| **多模态支持** | 🔥🔥 | #9291, #8169 |
| **安全与权限** | 🔥🔥 | #9089, #9250 |
| **生态集成** | 🔥 | #9275 (Copilot), #9294 (ClawMetry) |
| **性能优化** | 🔥 | #8608, #9234 |

**趋势洞察**：多 Agent 协作是当前最活跃的开发方向，同时开发者对 CI/CD 安全性、Web Shell 稳定性提出持续改进需求。

---

## 6. 开发者关注点

### 高频痛点

1. **Agent 协作机制不成熟**
   - 团队成员无法向 leader 发送普通消息
   - 手动任务分配后无实际派发
   - Prompt 描述与实际行为不一致
   - 错误状态的 agent tab 导致会话崩溃

2. **终端环境兼容性问题**
   - tmux 环境下屏幕闪烁严重（#8962）
   - 中文输入法偶发失效（#5966）
   - Web Shell 浏览器标签页因 SSE 帧过大崩溃（#9234）

3. **CI/CD 安全顾虑**
   - autofix 工作流中 PAT 与不受信任代码共享宿主（#9089）
   - 自托管 runner 上工作区清理范围过广（#9228）

4. **多模态支持缺陷**
   - 不支持的图像 MIME 类型导致会话中断（#9291）

### 期待方向
- GitHub Copilot 认证集成（#9275）
- 本地可观测性工具 ClawMetry 集成（#9294）
- Review 工作流稳定性持续加固

---

*报告生成时间：2026-08-17 | 数据来源：github.com/QwenLM/qwen-code*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI (CodeWhale) 社区动态日报

**日期：2026-08-17**

---

## 1. 今日速览

项目已完成从 `deepseek-tui` 到 `codewhale` 的品牌迁移，v0.9.8 作为最后一次旧包发布。今日核心动态集中在：**子代理工具 Schema 精简**（33 字段→12 字段）、**TUI 文本排版宽屏适配修复**、**bwrap 沙箱额外挂载点支持**，以及 i18n 多语言字典全面补充至 codewhale.net。

---

## 2. 版本发布

### v0.9.8 — 旧包 `deepseek-tui` 最终发布

> Codewhale 是 Shannon Labs 的公开产品。`codewhale` 命令、npm 包及 release-asset 名称均保持小写。旧版 npm 包 `deepseek-tui` 已弃用，不再发布新版本。

- 链接：Issue #5434（DSH 集成交互验证）
- 相关：迁移指南见 Issue #5288

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 评论 | 重要性 |
|---|------|------|------|--------|
| **#5424** | v0.9.7 Codewhale TUI 无故崩溃 | OPEN | 5 | 生产环境稳定性问题，用户反馈 prompt 后约一分钟进程自行退出 |
| **#5123** | Agent spawn 表面旋钮过多，builder 模式被误标记为只读 | OPEN | 6 | 影响子代理调度 UX，被标记为 self-blocked |
| **#2693** | v0.9.4 HarnessPosture：按模型路由配置 context 和子代理策略 | OPEN | 6 | DeepSeek V4 / MiMo v2.5 等长上下文模型需要差异化 context 策略 |
| **#5410** | 允许配置 bwrap 沙箱的额外挂载根目录 | OPEN | 1 | Zig 等开发场景下 `/dev/null` 写入和系统库链接被拒绝 |
| **#5322** | 输出区域不再填满宽终端（v0.8.65 正常，v0.9.x 回归） | CLOSED | 5 | 宽屏用户高频痛点，已关闭，见 PR #5446 |
| **#5436** | 正文在 ~105 列处换行，工具单元格跑满宽屏 | CLOSED | 0 | 排版失衡问题，已合并修复 |
| **#5056** | 测试可靠性：flakey verifier 后台测试 + 12 个未分类 #[ignore] | OPEN | 5 | CI 稳定性隐患 |
| **#1917** | 提议：通用 PreToolUse/PostToolUse hook 层 | OPEN | 5 | 统一 Cancel/Pause/Resume 生命周期架构提案 |
| **#5367** | 为自托管长上下文模型配置 model-visible 读写大小限制 | CLOSED | 4 | DeepSeek V4 等模型用户的核心需求 |
| **#5403** | main 分支在 macOS + Windows 全平台 CI 变红 | OPEN | 2 | 阻塞发布流程 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 内容摘要 |
|---|------|------|----------|
| **#5458** | feat(subagent): 子代理工具 Schema 精简至 12 字段 | OPEN | 从 33 字段（+~20 别名）精简为 `action/prompt/type/profile/name/agent_id/message/detached/worktree/write_roots/resume_from/until`，未 advertised 字段仍保留 parse 兼容性 |
| **#5459** | fix(tui): 诚实化 context window / output ceiling / telemetry 展示 | OPEN | 所有被 runtime 估算的数字标注来源，并与配置 key 配对，避免未经验证的数值驱动真实预算 |
| **#5446** | fix(tui): 正文填满全宽 + 新增 `transcript.prose_measure` 上限 | CLOSED | 修复 #5436，移除 `PROSE_MAX_MEASURE=105` 限制 |
| **#5456** | feat(sandbox): bwrap 容器基础挂载 + 可配置额外根目录 | OPEN | 默认挂载 `--dev /dev, --proc /proc, --tmpfs /tmp`，新增 `bwrap_ro_roots` 配置项（修复 #5410） |
| **#5445** | fix(integrations): DSH Routes 支持 Responses 方言 | CLOSED | 修复 `codewhale integrations dsh plan` 拒绝 `deepseek/deepseek-v4-flash` 的 bug（#5434） |
| **#5450** | fix(tui): 实时定价不可验证时恢复会话成本展示 | OPEN | 覆盖 #5402，修复 pricing API 503 时成本永远显示 `unverified_live_pricing` 的问题 |
| **#5454** | feat(web/i18n): 新增 fr/de/ca/hi/tr/it/pl 字典（+ar RTL 基础设施） | OPEN | codewhale.net 补齐至与 v0.9.2 TUI locale packs 同等语言覆盖 |
| **#5455** | feat(tui): 空状态鲸鱼插图重绘（Signal Cut 系列） | OPEN | 新版空状态鲸鱼艺术图 |
| **#5438** | fix(fleet): scout 只读沙箱权限门控对齐 #5426 | OPEN | 修复 scout 子代理连 `git log --oneline` 等基础命令都被拒绝的回归 |
| **#5402** | fix(tui): 会话成本在 live pricing 不可验证时恢复 | OPEN | 独立 PR，与 #5450 含相同两个 commit |

---

## 5. 功能需求趋势

从今日 Issues 中可提炼出以下方向：

1. **子代理（Subagent）架构持续深化** — Schema 精简（#5458）、scout 只读沙箱权限（#5426/#5438）、prompt assembly 下沉至 `crates/core`（#5263）、Hook 生命周期层提案（#1917）
2. **长上下文模型适配** — 按模型配置 context 策略（#2693）、自定义读/写大小限制（#5367）、DeepSeek effort mapping 硬编码问题（#5055）
3. **沙箱与工具链兼容性** — bwrap 额外挂载点（#5410/#5456）、Swift 编译沙箱失败（#2617）、sudo 回退（#5413）
4. **TUI 渲染与宽屏体验** — 正文排版宽度（#5436/#5446）、diff 渲染优化（#5087）、IME 回车延迟修复（#4665）
5. **多语言国际化** — Web 端补齐 7 种语言字典（#5454）、README 多语言翻译（#5452）
6. **可观测性与透明度** — context window / 输出上限 / 实时定价的诚实化展示（#5459/#5450）
7. **DSH 集成** — Responses 方言路由支持（#5434/#5445）

---

## 6. 开发者关注点

- **宽屏终端排版**：v0.9.x 回归导致正文被限制在 105 列，宽屏右侧大片空白，是社区高频反馈的 UX 问题（已修复）
- **子代理只读模式误杀**：scout/reviewer 在 `ShellPolicy::ReadOnly` 下连 `git log` 等基础命令也被拒绝，影响实际工作流
- **bwrap 沙箱过于严格**：`/dev/null` 写入、系统库链接等合法开发操作被拦截，用户请求可配置的额外挂载根
- **实时定价不稳定**：`api.codewhale.net/session` 返回 503 时，会话成本永久显示 `unverified_live_pricing`，影响透明度
- **DSH 集成默认路由被拒**：`deepseek/deepseek-v4-flash` 因 Responses 方言未被声明而拒绝，已修复
- **CI 全平台变红**：macOS + Windows 四个 e2e 用例连续失败，阻塞发布（#5403）
- **依赖升级**：`rmcp`（2.2.0→3.1.2）、`tower-http`（0.6.11→0.7.0）、`rusqlite`（0.39.0→0.40.2）、`thiserror`（2.0.19→2.0.20）持续跟进

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*