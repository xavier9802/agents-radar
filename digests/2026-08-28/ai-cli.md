# AI CLI 工具社区动态日报 2026-08-28

> 生成时间: 2026-08-28 10:57 UTC | 覆盖工具: 10 个

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



# AI CLI 工具社区动态横向对比分析报告
**日期：2026-08-28 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026年8月末的AI CLI工具生态呈现"头部加速迭代、长尾聚焦垂直场景"的分化态势。Claude Code与OpenAI Codex持续以周级节奏发布安全与稳定性更新，GitHub Copilot CLI正式拥抱MCP 2026标准，OpenCode与Qwen Code在Web Shell与企业集成方向深化。中国模型工具（Kimi、DeepSeek、Qwen）社区活跃于原生搜索适配与多模型互操作，而Pi等开源工具则聚焦TUI渲染与本地推理的精细化打磨。整体而言，工具竞争从"功能有无"转向"稳定性与可观测性"的深水区。

---

## 2. 各工具活跃度对比

| 工具 | Issues（活跃/精选） | PR（24h） | Release | 更新频率 |
|------|---------------------|-----------|---------|----------|
| **Claude Code** | 10条精选，多账户需求761👍 | 1条（技能插件） | v2.1.250 / v2.1.248 | 高（安全更新优先） |
| **OpenAI Codex** | 10条精选，GPU/历史分页受关注 | 信息不足 | 0.151.0-alpha.6~8（3连发） | 极高（快速试错） |
| **Gemini CLI** | ❌ 摘要生成失败 | ❌ | ❌ | 数据缺失 |
| **GitHub Copilot CLI** | 34条活跃Issue | 信息不足 | v1.0.82-0 | 高（生态集成期） |
| **Kimi Code CLI** | 6条（全部展示） | 3条（含安全修复） | 无 | 中（稳定期） |
| **OpenCode** | 10条精选，订阅问题集中 | 多（skyzhao1223提交6+） | v1.18.25 | 高（工具层精修） |
| **Pi** | 10条精选，XDG规范52👍 | 10条（5合入） | 无 | 中（问题修复期） |
| **Qwen Code** | 10条精选，OpenTUI架构讨论11评论 | 9条（多Review中） | v0.22.2-nightly | 高（架构重构期） |
| **DeepSeek TUI** | 10条精选，多会话锁回归 | 13条（搜索适配器集中） | 无 | 中（性能优化期） |
| **Grok Build** | 无活动 | 无 | 无 | 停滞 |

---

## 3. 共同关注的功能方向

| 方向 | 涉及工具 | 具体诉求 |
|------|----------|----------|
| **🔐 安全与权限控制** | Claude Code、Qwen Code、OpenCode、DeepSeek TUI | Claude Code新增`--restricted`模式；Qwen Code暴露Anthropic通道缺stream-safety；OpenCode glob工具越权访问；DeepSeek MCP Secret作用域限定 |
| **🖥️ TUI/渲染稳定性** | Pi、Claude Code、OpenCode、Qwen Code | Pi多起TUI换行/渲染Bug；Claude Code Windows崩溃残留Job Object；Qwen Code发起ink→OpenTUI迁移讨论；OpenCode GNU Screen兼容问题 |
| **📊 可观测性与调试** | Claude Code、OpenAI Codex、GitHub Copilot CLI | Claude Code社区请求OTel支持（35👍）；Codex历史分页解码不一致；Copilot Hooks接入OTel上下文 |
| **🔄 多会话/多账户** | Claude Code、DeepSeek TUI、OpenCode | Claude Code多账户需求761👍遥遥领先；DeepSeek多会话owner lock阻塞（v0.9.12回归）；OpenCode多会话撤销隔离 |
| **🌐 跨平台/原生搜索** | DeepSeek TUI、Kimi Code CLI、OpenCode | DeepSeek一日合并5个原生Web搜索适配器（DeepSeek/Qwen/Kimi/Z.AI/MiMo）；Kimi Plan mode死循环；OpenCode Azure CLI认证无需Bun |
| **🤖 子代理/扩展机制** | Claude Code、Pi、Qwen Code | Claude Code子代理LSP工具被裁剪；Pi钩子系统触发路径不全；Qwen Code Daemon暴露Workflow控制接口 |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|----------|----------|----------|
| **Claude Code** | 企业级安全控制、权限精细化 | 开发者/安全合规团队 | Rust CLI + `--restricted`沙箱 + MCP生态 |
| **OpenAI Codex** | 快速迭代、会话历史管理 | 开放式开发者社区 | Rust CLI + 高频Alpha试错 + TUI优化 |
| **GitHub Copilot CLI** | 插件生态、MCP 2026标准 | 企业用户/插件开发者 | TypeScript + 插件仪表盘 + OTel集成 |
| **Kimi Code CLI** | Plan mode工作流、OpenAI兼容 | 中文开发者/Moonshot用户 | Python + asyncssh安全响应 |
| **OpenCode** | 多提供商（Azure/Bedrock）、工具层精确性 | 付费订阅用户/企业 | Go + 工具层边界修复 + 深链接桌面端 |
| **Pi** | 本地推理（llama.cpp）、TUI渲染 | 开源爱好者/边缘计算用户 | TypeScript + XDG规范 + 终端协议兼容 |
| **Qwen Code** | Web Shell、多通道集成、架构分层 | 阿里云生态用户/中国开发者 | TypeScript + OpenTUI迁移 + Daemon L2架构 |
| **DeepSeek TUI** | 多模型原生搜索、跨Provider适配 | DeepSeek模型用户 | Rust（68万行单crate）+ 搜索适配器生态 |
| **Grok Build** | — | — | 无活动 |

---

## 5. 社区热度与成熟度

| 梯队 | 工具 | 判断依据 |
|------|------|----------|
| **🔥 高活跃+快速迭代** | OpenAI Codex、Claude Code、GitHub Copilot CLI | Codex三日连发Alpha；Claude Code安全模式急推；Copilot 34条活跃Issue集中爆发 |
| **📈 中高活跃+生态扩张** | Qwen Code、DeepSeek TUI、OpenCode | Qwen Code 9条PR多Review中+OpenTUI架构讨论；DeepSeek一日合并5搜索PR；OpenCode工具层批量修复 |
| **🛠️ 稳定期+问题修复** | Kimi Code CLI、Pi | Kimi无版本发布但安全PR及时；Pi无Release但PR合入率高（5/10）聚焦TUI精修 |
| **⏸️ 低活跃/停滞** | Gemini CLI、Grok Build | Gemini数据缺失；Grok Build零活动 |

**成熟度信号：**
- Claude Code已具备企业级安全模式（`--restricted`），进入成熟期
- OpenCode付费订阅与用量透明度问题（#38255/#41206）反映商业化早期阵痛
- DeepSeek TUI的68万行单crate构建性能瓶颈（#5249）是规模化后的典型技术债
- Pi的XDG规范需求（#2870，52👍）反映开源工具对Linux生态规范的追赶

---

## 6. 值得关注的趋势信号

### 📌 信号一：安全沙箱成为标配竞争点
Claude Code v2.1.248急推`--restricted`模式，Qwen Code暴露Anthropic通道缺stream-safety，OpenCode收紧glob权限校验。**对开发者建议：** 企业部署时优先评估工具的权限隔离能力，Claude Code与OpenCode当前领先。

### 📌 信号二：MCP 2026标准加速生态整合
GitHub Copilot CLI v1.0.81正式推送MCP 2026支持，DeepSeek TUI一日合并5个原生搜索适配器，Kimi Code CLI修复Notion MCP凭证持久化。**对开发者建议：** MCP生态兼容性将成为工具选型的关键维度，关注各工具对MCP 2026规范的落地进度。

### 📌 信号三：TUI渲染层面临架构级重构
Qwen Code发起ink→OpenTUI迁移讨论，Pi多起TUI换行/渲染Bug，OpenCode修复混合格式化问题。**对开发者建议：** TUI稳定性是当前各工具的共性短板，关注OpenTUI等新一代终端渲染库的采用趋势。

### 📌 信号四：多会话/多账户成为用户体验分水岭
Claude Code多账户需求761👍遥遥领先，DeepSeek TUI多会话锁回归，OpenCode多会话撤销隔离。**对开发者建议：** 多会话管理能力将直接影响团队协作体验，Claude Code在此方向呼声最高但尚未实现。

### 📌 信号五：中国模型工具的"原生适配"竞赛
DeepSeek、Kimi、Qwen、Z.AI、MiMo搜索适配器集中涌现，Qwen Code修复钉钉rich-text，Kimi Code修复OpenAI Legacy兼容。**对开发者建议：** 国内模型工具的生态整合速度超预期，关注原生搜索与跨Provider适配能力。

### 📌 信号六：构建性能成为Rust工具的隐性瓶颈
DeepSeek TUI 68万行单crate引发构建时间税讨论，OpenAI Codex高频Alpha试错依赖快速编译。**对开发者建议：** 关注crate拆分、增量编译、CI缓存等工程实践，Rust CLI工具的构建体验将影响开发者贡献意愿。

---

*报告生成时间：2026-08-28 | 分析师：Agnes (Sapiens AI)*

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告
**数据截止：2026-08-28 | 分析师：Agnes**

---

## 1. 热门 Skills 排行

| 排名 | Skill | 功能 | 社区热点 | 状态 |
|------|-------|------|----------|------|
| 1 | **Hivemind** [#1628](https://github.com/anthropics/skills/pull/1628) | 零成本多代理编排：将机械工作委派给 opencode 免费模型 worker，Claude Code 仅做规划/审查/合并 | 最新提交（8/21），聚焦"上下文窗口即稀缺资源"痛点 | 🔵 OPEN |
| 2 | **scnet-hpc** [#1615](https://github.com/anthropics/skills/pull/1615) | SCNet HPC 集群操作：基于 profile 的 SSH + Slurm 工作流 | 最新提交（8/20），填补高性能计算场景空白 | 🔵 OPEN |
| 3 | **self-audit** [#1367](https://github.com/anthropics/skills/pull/1367) | 输出前自检：机械文件验证 + 四维度推理质量门控 | 通用性高，适配任意项目/技术栈/模型 | 🔵 OPEN |
| 4 | **testing-patterns** [#723](https://github.com/anthropics/skills/pull/723) | 全栈测试技能：Testing Trophy 理念、AAA 单元测试、React 组件测试 | 社区对测试工程化需求强烈 | 🔵 OPEN |
| 5 | **ServiceNow** [#568](https://github.com/anthropics/skills/pull/568) | 企业 ITSM/ITOM/SecOps/FSM 全平台覆盖 | 更新活跃（8/12），企业级场景需求明确 | 🔵 OPEN |
| 6 | **skill-quality-analyzer + skill-security-analyzer** [#83](https://github.com/anthropics/skills/pull/83) | 元技能：五维 Skill 质量评估 + 安全审计 | 长期未合并，但生态健康度关注度高 | 🔵 OPEN |
| 7 | **document-typography** [#514](https://github.com/anthropics/skills/pull/514) | AI 生成文档排版质量控制：孤行/寡行/编号对齐 | 填补文档后处理空白，实用性强 | 🔵 OPEN |
| 8 | **ODT** [#486](https://github.com/anthropics/skills/pull/486) | OpenDocument 格式创建、模板填充、ODT→HTML 解析 | 开源格式生态补全 | 🔵 OPEN |

---

## 2. 社区需求趋势

| 需求方向 | 代表性 Issue/PR | 核心诉求 |
|----------|-----------------|----------|
| **🔒 安全与信任边界** | [#492](https://github.com/anthropics/skills/issues/492)（43 评论） | 社区 Skill 冒用 `anthropic/` 命名空间，需建立官方认证机制 |
| **🏢 企业协作共享** | [#228](https://github.com/anthropics/skills/issues/228)（16 评论，8 👍） | 组织内 Skill 一键共享，替代当前"下载→发送→手动上传"的低效流程 |
| **⚙️ Skill 开发工具链** | [#556](https://github.com/anthropics/skills/issues/556)（12 评论，7 👍） | `run_eval.py` 触发率始终为 0%，Skill 优化循环无法工作 |
| **🧠 推理质量保障** | [#1385](https://github.com/anthropics/skills/issues/1385)（4 评论） | 提案三级质量门：预校准→对抗审查→交付验证 |
| **🤖 Agent 治理** | [#412](https://github.com/anthropics/skills/issues/412)（6 评论） | Policy 执行、威胁检测、信任评分、审计追踪 |
| **📦 生态治理** | [#189](https://github.com/anthropics/skills/issues/189)（6 评论，9 👍） | `document-skills` 与 `example-skills` 插件内容重复，导致上下文浪费 |
| **💰 多模型成本优化** | [#1628](https://github.com/anthropics/skills/pull/1628) | 用免费模型处理机械任务，昂贵模型的上下文用于决策 |

---

## 3. 高潜力待合并 Skills

| Skill | PR | 待解决关键问题 | 合并概率 |
|-------|-----|----------------|----------|
| **Hivemind** | [#1628](https://github.com/anthropics/skills/pull/1628) | 最新 PR，与 opencode 集成方案明确 | ⭐⭐⭐⭐ 高 |
| **scnet-hpc** | [#1615](https://github.com/anthropics/skills/pull/1615) | 最新 PR，垂直场景清晰 | ⭐⭐⭐⭐ 高 |
| **self-audit** | [#1367](https://github.com/anthropics/skills/pull/1367) | 通用性强，有配套 Issue [#1385](https://github.com/anthropics/skills/issues/1385) 支持 | ⭐⭐⭐ 中 |
| **testing-patterns** | [#723](https://github.com/anthropics/skills/pull/723) | 需求明确，覆盖全栈 | ⭐⭐⭐ 中 |
| **document-typography** | [#514](https://github.com/anthropics/skills/pull/514) | 垂直痛点清晰，代码量小 | ⭐⭐⭐ 中 |
| **ServiceNow** | [#568](https://github.com/anthropics/skills/pull/568) | 企业级，覆盖广但维护成本高 | ⭐⭐ 中低 |
| **skill-quality-analyzer** | [#83](https://github.com/anthropics/skills/pull/83) | 长期未动，需官方回应方向 | ⭐ 低 |

---

## 4. Skills 生态洞察

> **社区最集中的诉求是：在保证安全信任边界的前提下，让 Skill 开发工具链真正可用，并支持企业级协作与多模型成本优化。**

三个关键词：**安全认证**（#492 冒用问题）、**工具链修复**（#556 run_eval.py 失灵）、**成本分层**（#1628 Hivemind 方案）。官方需在 Q3 优先修复 skill-creator 评估基础设施，否则社区贡献的质量闭环无法建立。

---



# 📊 Claude Code 社区动态日报

**日期：2026-08-28 | 数据来源：github.com/anthropics/claude-code**

---

## 1. 今日速览

Claude Code 发布 v2.1.250 修复更新，v2.1.248 新增 `--restricted` 安全模式大幅收紧权限控制。社区最热门的多账户切换功能请求已累积 761 赞，Windows 崩溃后残留 Job Object 导致无法启动的问题持续引发关注。

---

## 2. 版本发布

### v2.1.250
- Bug fixes and reliability improvements
- 链接：https://github.com/anthropics/claude-code/releases/tag/v2.1.250

### v2.1.248（重要安全更新）
- 新增 `--restricted` 模式（或 `CLAUDE_CODE_RESTRICTED=1` 环境变量）
- 移除内置的命令/代码执行工具及 `WebFetch`（除非通过 `--tools` 显式声明）
- 文件工具限制在工作目录内，拒绝 `bypassPermissions`，忽略用户/项目/本地配置文件
- 链接：https://github.com/anthropics/claude-code/releases/tag/v2.1.248

---

## 3. 社区热点 Issues（Top 10）

| # | Issue | 摘要 | 评论 | 👍 |
|---|-------|------|------|-----|
| #18435 | 多账户管理功能请求 | Claude Desktop 内支持多账户及快速切换 Profile | 170 | 761 |
| #53247 | Windows 崩溃后无法启动 | 崩溃后残留 Silo/Job Object，仅注销/重启可恢复 (HRESULT 0x80070020) | 29 | 18 |
| #61682 | GitHub Connector 在 Cowork 中无工具 | Windows 11 上显示已连接但暴露不出工具 | 24 | 24 |
| #49655 | Windows 更新失败 | CoworkVMService 运行时更新报 0x80073CF6（已关闭） | 23 | 10 |
| #82049 | Claude.ai 登录邮件延迟 | 2026年7月中旬以来 Magic Link 邮件延迟 2-5 分钟 | 19 | 36 |
| #32364 | Web 版 OpenTelemetry 支持 | claude.ai/code 中支持 OTel 配置 | 8 | 35 |
| #66440 | macOS C# 语法高亮消失 | 短暂后 C# 语法高亮被清除 | 8 | 10 |
| #88405 | .claude/rules/ 符号链接不自动加载 | 文档称支持符号链接但实际未生效 | 6 | 4 |
| #84125 | LSP 工具在子代理中被裁剪 | 交互式会话中 LSP 工具从所有子代理工具集移除 | 3 | 4 |
| #88561 | Bash 工具 `\\` 被静默折叠 | 转义反斜杠在引号内外均被折叠为单 `\`，破坏正则和路径 | 3 | 1 |

**值得关注：**
- **#18435** 是长期热门需求，多账户管理已是社区呼声最高的功能
- **#88561** 是严重的 Bash 工具回归 bug，直接影响跨平台脚本可靠性
- **#32364** 反映开发者对可观测性工具链集成的强烈需求

---

## 4. 重要 PR 进展

> 过去 24 小时内更新 PR 共 1 条：

| # | PR | 作者 | 摘要 | 状态 |
|---|-----|------|------|------|
| #69226 | Update frontend-design skill | williamqian12 | 前端设计技能改进，插件版本 bump 至 1.1.0 | ✅ Closed |

**说明：** 今日 PR 活跃度较低，主要更新集中在技能插件层面。

---

## 5. 功能需求趋势

从 Issue 热度分析，社区关注方向如下：

| 方向 | 代表 Issue | 热度 |
|------|-----------|------|
| 🏠 **账户与权限管理** | #18435, #89911, #88518 | ⭐⭐⭐⭐⭐ |
| 🔌 **IDE/编辑器集成** | #61682, #40766, #75957 | ⭐⭐⭐⭐ |
| 📊 **可观测性与调试** | #32364, #67657, #85477 | ⭐⭐⭐⭐ |
| 🖥️ **平台稳定性** | #53247, #87710, #66440 | ⭐⭐⭐⭐ |
| 🤖 **多代理/子代理** | #84125, #90264, #34692 | ⭐⭐⭐ |
| 🔐 **安全与沙箱** | #12862, #87348, #88518 | ⭐⭐⭐ |
| 🌐 **跨设备/同步** | #78776, #82049, #90298 | ⭐⭐⭐ |

---

## 6. 开发者关注点

### 🔴 高频痛点

1. **多账户工作流缺失** — #18435 以 761 赞遥遥领先，个人与团队账户切换需求强烈
2. **Windows 平台稳定性** — 崩溃残留 Job Object、更新失败、安装后历史丢失等问题集中爆发
3. **MCP 工具注册异常** — GitHub Connector 在 Cowork 中"已连接但无工具" (#61682) 影响工作流
4. **Bash 转义行为回归** — `\\` 被静默折叠为 `\` (#88561) 是严重可靠性问题，影响跨平台脚本
5. **子代理工具集不完整** — LSP 工具在交互式子代理中被裁剪 (#84125)，`PreToolUse/PostToolUse` hooks 在子代理中不触发 (#34692)

### 🟡 新兴需求

- **Web 版可观测性集成**（OTel 支持）— #32364
- **跨设备会话同步可控性** — #78776 请求提供本地模式选项
- **CLAUDE.md 规则治理诊断** — #85477 建议添加指令预算警告、重复/冲突检测
- **Write 工具安全回退** — #88518 请求恢复 v2.1.228 之前的严格读写保护模式

---

*报告生成时间：2026-08-28 | 分析师：Agnes-2.0-Flash*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报（2026-08-28）

## 1. 今日速览
今日 Codex 社区更新活跃，CLI 端连续发布 0.151.0-alpha.6 至 .8 三个测试版本，快速迭代底层会话与历史记录逻辑。Windows 桌面端的登录回环、握手异常及升级后 headless 卡死问题引发集中反馈，成为当日稳定性焦点。核心代码库侧，安全审核（Guardian）预算管控、子 Agent 层级同步、历史记录后端与 PowerShell 沙盒兼容性等多项优化已合并入主分支。

## 2. 版本发布
过去 24 小时内，Rust CLI 连续抛出三个 Alpha 版本，推进 0.151.0 预览链路：
- `rust-v0.151.0-alpha.6` / `.7` / `.8`：连续发布体现快速试错节奏，通常聚焦于会话序列化、历史分页、沙盒执行链路与认证恢复的底层稳定性修复。具体变更建议以 Release Notes 为准。

## 3. 社区热点 Issues（精选 10）
| #ID | 标签 | 标题 | 重要性 & 社区反馈 |
|-----|------|------|------------------|
| #16857 | bug, performance | High GPU usage while the app is “thinking” | 闲置动画占用过高 GPU，51👍/42评论，直接影响 macOS/ARM 设备续航与发热。[链接](https://github.com/openai/codex/issues/16857) |
| #39903 | enhancement, TUI | 禁用“Ran N commands”折叠 | 60👍/33评论，开发者高度期望 TUI 保持命令执行记录的可追溯性。[链接](https://github.com/openai/codex/issues/39903) |
| #41049 | bug, windows-os | code-mode host exited during handshake | 32评论，Win 端最新高频阻塞问题，模型调用链在握手阶段异常中断。[链接](https://github.com/openai/codex/issues/41049) |
| #35746 | bug, CLI | Paginated history drops valid flattened rollout records | 31评论，历史分页解码不一致导致会话回滚数据丢失，影响审计与复用。[链接](https://github.com/openai/codex/issues/35746) |
| #11747 | enhancement, TUI | Add `/add-dir` slash command mid-session | 45👍/14评论，长期功能诉求，解决会话中途需扩展工作目录的割裂体验。[链接](https://github.com/openai/codex/issues/11747) |
| #40036 | bug, windows-os, auth | Codex Stuck in Login Loop Windows 11 | 近期 Win 端认证回环典型案例，基础可用性问题引发高度关注。[链接](https://github.com/openai/codex/issues/40036) |
| #32309 | bug, performance | high-frequency code-mode polling + large resumed context | 600M vs 150-200M Token 消耗对比案例，揭示上下文膨胀与高频轮询的成本隐患。[链接](https://github.com/openai/codex/issues/32309) |
| #18396 | enhancement, TUI | Add way to hide tool calls/output in TUI | 28👍/10评论，终端界面整洁度与噪音过滤的核心诉求。[链接](https://github.com/openai/codex/issues/18396) |
| #39855 / #39678 | bug, remote | Windows Remote & Android→macOS 项目信任验证失败 | 跨设备远程协作的信任校验异常，反映 Remote 链路在不同 OS 间的兼容碎片化。[链接](https://github.com/openai/codex/issues/39855) [链接](https://github.com/openai/codex/issues/39678) |
| #41269 | bug, CLI | Rollouts persist each command's stdout 3x per item | 60% 会话字节为冗余 stdout，存储与 I/O 效率优化点已暴露。[链接](https://github.com/openai/codex/issues/41269) |

## 4. 重要 PR 进展（精选 

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-08-28**  
**监控仓库：** github.com/github/copilot-cli

---

## 1. 今日速览
Copilot CLI 今日发布 `v1.0.82-0` 修复版本，承接 `v1.0.81` 正式引入的 MCP 2026 支持与插件仪表盘功能。过去 24 小时社区反馈高度集中在新版稳定性问题上：`store_memory` 报错、TUI 假死、企业版认证异常及插件兼容性回归，共活跃 34 个 Issue，显示生态集成与内存管理模块仍需持续打磨。

---

## 2. 版本发布
- **v1.0.82-0**：缺陷修复与内部变更（具体变更清单未公开）。
- **v1.0.81**（2026-08-27）：
  - 插件仪表盘全面开放，支持 `/plugin`、`/mcp`、`/skills` 命令；可通过环境变量 `PLUGINS_DASHBOARD=false` 关闭。
  - 正式向 CLI、SDK、IDE 及 in-memory 客户端推送 MCP 2026 支持。
  - Hooks 现已可接收当前 OpenTelemetry 上下文，便于分布式追踪与调试。

---

## 3. 社区热点 Issues（精选 10 项）

| # | 标题摘要 | 核心影响 | 社区

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-08-28** | **数据来源：github.com/MoonshotAI/kimi-cli**

---

## 1. 今日速览

今日无新版本发布，社区聚焦于 Plan mode 死循环 Bug 的反馈以及 OpenAI Legacy 适配文档的完善。安全方面，`asyncssh` 组件已发布依赖升级 PR 修复已知漏洞，文件编码处理也收到针对性修复补丁。

---

## 2. 版本发布

> 过去 24 小时内无新版本发布。

---

## 3. 社区热点 Issues

**（共 6 条，全部展示）**

| # | 标题 | 状态 | 关注点 |
|---|------|------|--------|
| #2623 | Plan mode 下 agent 无限循环 Bash echo/ReadFile，不执行写计划 | 🟢 OPEN | 核心工作流 Bug，K3 模型在 0.38.0 版本出现 |
| #2621 | API 工具调用返回 content 为空导致 400 错误 | 🟢 OPEN | API 规范兼容性问题，社区情绪较激烈（1 👍） |
| #2624 | 补充 openai_legacy 适配 /v1 端点的文档说明 | 🟢 OPEN | Bot 提交，修复用户易踩的配置误区 |
| #1211 | Notion Remote MCP 认证凭证会话结束后丢失 | ✅ CLOSED | MCP 生态集成持久化问题 |
| #1272 | JetBrains AI Assistant 通过 ACP 调用 Kimi 无法识别拖入文件 | ✅ CLOSED | IDE 插件文件感知能力缺陷 |
| #1279 | 请求原生支持 git-ai 进行 AI 代码溯源 | ✅ CLOSED | 开发者对代码溯源的需求 |

**重点解读：**
- **#2623** 是当前最受关注的 Bug，Plan mode 是 Kimi Code 的核心交互模式，无限循环直接阻断工作流。
- **#2621** 暴露了 API 与客户端之间的 content 字段语义不一致问题，社区用户反馈语气强烈，可能影响上游集成体验。

---

## 4. 重要 PR 进展

**（共 3 条，全部展示）**

### #2622 — deps: bump asyncssh to 2.23.1（安全修复）
- **作者：** katsugtgz | **创建：** 2026-08-28
- **内容：** 将 `pykaos` 中的 `asyncssh` 从 2.21.1 升级至 2.23.1，修复 GHSA-2wxc-x7rj-hg8f 和 GHSA-qr67-gv47-xwwh 两个安全漏洞。
- **链接：** https://github.com/MoonshotAI/kimi-cli/pull/2622

### #2176 — fix(hooks): 从 ContentPart 提取文本用于 UserPromptSubmit hook
- **作者：** tears-mysthrala | **创建：** 2026-05-07 | **最近更新：** 2026-08-27
- **内容：** 修复当 `user_input` 为 `list[ContentPart]` 时 `UserPromptSubmit` hook 收到空 `prompt` 的问题，此前仅处理 `str` 类型导致正则匹配失效。解决 #2148。
- **链接：** https://github.com/MoonshotAI/kimi-cli/pull/2176

### #2595 — fix(StrReplaceFile): 拒绝编辑非 UTF-8 文件
- **作者：** shoemoney | **创建：** 2026-08-06 | **最近更新：** 2026-08-27
- **内容：** 修复 `StrReplaceFile` 操作含非 UTF-8 字节文件时将所有非法字节替换为 U+FFFD 并回写的问题，改为直接拒绝编辑此类文件。解决 #2591。
- **链接：** https://github.com/MoonshotAI/kimi-cli/pull/2595

---

## 5. 功能需求趋势

从今日 Issues 中可提炼以下社区关注方向：

| 方向 | 频次 | 典型 Issue |
|------|------|------------|
| **MCP / 外部工具集成** | 2 | #1211（Notion MCP）、#1279（git-ai） |
| **IDE / 编辑器插件** | 1 | #1272（JetBrains 文件识别） |
| **API 兼容性** | 1 | #2621（OpenAI content 字段语义） |
| **文档与配置** | 1 | #2624（openai_legacy 示例） |
| **核心 Agent 稳定性** | 1 | #2623（Plan mode 循环） |

> 整体趋势：社区需求从"能否用"转向"用得好"，重点关注集成生态（MCP/IDE）的稳定性和 API 接口的规范性。

---

## 6. 开发者关注点

**高频痛点：**

1. **Agent 循环问题** — #2623 反映 Plan mode 下模型在探索完成后无法正确退出循环，是核心体验瓶颈。
2. **API content 字段语义歧义** — #2621 指出工具调用响应中 `content` 为空但携带 `tool_calls` 的场景，回传时触发 400，需要客户端额外兼容处理，暴露了 API 规范设计的不一致。
3. **MCP 凭证持久化** — #1211 关闭但反映用户期望 MCP 认证信息跨会话保留。
4. **IDE 文件感知** — #1272 指出通过 ACP 协议传入的文件在 Kimi 侧无法自动识别，需手动补充路径。
5. **安全依赖更新** — #2622 安全团队对 `asyncssh` 漏洞响应及时，PR 已提交。

---

*报告生成时间：2026-08-28 | 分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode 社区动态日报 — 2026-08-28

---

## 1. 今日速览

OpenCode 今日发布 v1.18.25，重点修复 Azure CLI 认证无需 Bun 的限制，以及 Bedrock 推理响应缓存问题。社区高票 Issue #785（禁用流式模式）持续获得关注（38 👍），同时 Go 订阅用量不一致和支付问题引发多起用户反馈。贡献者 skyzhao1223 今日提交大量工具层 Bugfix（glob、edit、webfetch），覆盖权限校验、字符集解码和超时输出保留等核心问题。

---

## 2. 版本发布

### v1.18.25（今日）
- **Bugfix**：修复 Azure 认证，使 Azure CLI 登录无需依赖 Bun

### v1.18.24（近日）
- **Bugfix**：Bedrock 推理响应不再被缓存为不可重放的空消息
- **Improvement**：Azure 提供商支持通过 Azure CLI 使用 Microsoft Entra ID 登录，无需 API Key
- **Improvement**：V1 开始读取支持的 V2 配置字段

🔗 [GitHub Releases](https://github.com/anomalyco/opencode/releases)

---

## 3. 社区热点 Issues

| # | 标题 | 评论 | 👍 | 重要性 |
|---|------|------|-----|--------|
| #785 | 禁用流式模式 | 33 | 38 | 第三方代理不兼容流式，用户强烈需求 |
| #6536 | 移动应用 | 16 | 49 | 高需求功能（已关闭） |
| #38255 | 用量仪表板数据不一致 | 10 | 0 | Go 用户月度/周配额与实际扣费不符 |
| #45278 | 支付被拒绝（稳定卡片） | 7 | 1 | 续费异常，影响付费用户体验 |
| #45867 | Muse Spark 1.2 提示词缓存未命中 | 5 | 0 | 生产环境性能问题 |
| #32985 | GNU Screen 兼容性 | 4 | 3 | 终端环境支持缺陷 |
| #33940 | 撤销操作跨会话影响 | 4 | 2 | 多会话场景数据安全问题 |
| #41206 | 配额与用量历史不匹配 | 4 | 1 | 与 #38255 同类问题，Go 订阅信任危机 |
| #21658 | Azure AI Foundry Entra 认证 | 4 | 10 | 企业用户刚需，已在 v1.18.24 部分实现 |
| #38550 | 手动 Todo 管理 | 4 | 2 | 用户希望绕过 Agent 自主控制任务列表 |

🔗 Issues 链接格式：`https://github.com/anomalyco/opencode/issues/{编号}`

---

## 4. 重要 PR 进展

| PR | 类型 | 内容摘要 |
|----|------|----------|
| #45915 | Bugfix | 格式化器子进程增加超时限制，防止挂起阻塞 |
| #45903 | Bugfix | webfetch 支持按 Content-Type charset 解码，修复 GBK/Shift_JIS 乱码 |
| #45906 | Bugfix | webfetch 正确处理 application/xhtml+xml 响应 |
| #45898 | Bugfix | glob 工具增加 external_directory 权限校验，防止越权访问 |
| #45894 | Bugfix | edit 工具对 newString 进行字面量写入，修复 `$` 替换模式误展开 |
| #45888 | Bugfix | 修复混合换行符文件的 LF 区域匹配问题 |
| #45886 | Bugfix | 命令超时时保留已捕获的部分输出，不再丢失 |
| #45609 | Bugfix | 文件系统监听跳过根目录，降低资源消耗和权限问题 |
| #45607 | Bugfix | 异步提示失败时将会话状态重置为 idle |
| #45557 | Bugfix | auth.json 序列化并原子写入，防止并发竞争 |
| #45103 | Feature | 桌面端支持通过深链接打开已有会话 |
| #45887 | Perf | 会话切换性能优化，与转录本长度解耦 |

🔗 PR 链接格式：`https://github.com/anomalyco/opencode/pull/{编号}`

---

## 5. 功能需求趋势

- **流式模式可配置**：#785 高票开放，部分代理/网关不支持流式，用户希望提供关闭选项
- **移动端访问**：#6536 获 49 👍，虽已关闭但需求强烈，当前仅支持移动浏览器
- **Azure/企业认证**：#21658 + v1.18.24 改进，企业用户持续关注 Entra ID / OAuth 支持
- **用量透明度**：#38255、#41206 集中反馈 Go 订阅配额与实际消耗不符，信任度下降
- **多会话隔离**：#33940 反映多会话场景下操作边界不清，用户需要会话级撤销隔离
- **TUI 环境兼容**：#32985、#45871 涉及 Screen/tmux/Android SSH 等边缘终端场景

---

## 6. 开发者关注点

**付费体验痛点**
- Go 套餐额度计算异常（#38255、#41206、#45899），用户质疑"宣传 $30/周实际仅 $7.5"（#45897）
- 支付成功后订阅未激活（#45907）及卡片无故被拒（#45278）

**工具层精确性**
- skyzhao1223 今日连续提交 6+ PR，聚焦 glob、edit、webfetch 等核心工具的边界行为：字符集解码、权限边界、换行符处理、超时输出保留

**运行时稳定性**
- auth.json 并发写入保护（#45557）、async prompt 状态机修复（#45607）、文件系统监听优化（#45609）

**桌面端体验**
- 深链接支持（#45103）、WSL sidecar 热重载（#45889）、Finder 路径解析 Schema 校验失败（#45895）

**Windows ARM64 支持**
- #45875 报告 bun:ffi 在 stable Bun 中不可用、bun-pty 仅提供 x64 DLL，构建虽可完成但 TUI/pty 会话运行失败

---

*报告生成时间：2026-08-28 | 数据来源：github.com/anomalyco/opencode*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 — 2026-08-28

## 1. 今日速览

过去24小时无新 Release，社区活跃度集中在 TUI 渲染问题修复与新功能探索。高关注 Issue #2870（XDG 目录规范）获 52 赞，多起 TUI 文本换行与表格选择 Bug 引发讨论；PR 方面，Markdown 软换行修复 (#8674) 与写操作输出优化 (#8766) 已合入。

---

## 2. 版本发布

**无新版本发布**

---

## 3. 社区热点 Issues

### 🔥 #2870 — Follow XDG Base Directory [CLOSED]
- **作者**: mks-h | **评论**: 20 | **👍 52**
- **摘要**: Linux 下应将配置/状态目录迁移至 `$XDG_CONFIG_HOME` 等标准路径，避免污染 home 目录。
- **重要性**: 涉及跨平台用户习惯与系统规范兼容，社区呼声最高。
- **链接**: https://github.com/earendil-works/pi/issues/2870

### 🔥 #8584 — TUI row corruption during streaming [OPEN]
- **作者**: ractive | **评论**: 14 | **👍 6**
- **摘要**: 长工具输出后，assistant 文本流式渲染时单词逐行显示，疑似终端宽度计算错误。
- **重要性**: 高频复现的 TUI 显示问题，影响核心交互体验。
- **链接**: https://github.com/earendil-works/pi/issues/8584

### #6922 — Default model cannot be a llama.cpp model [CLOSED]
- **作者**: highlyunavailable | **评论**: 12 | **👍 14**
- **摘要**: 设置 `defaultProvider=llama.cpp` 后启动报 "No models available"。
- **重要性**: llama.cpp 本地模型用户高频痛点，已关闭但反映本地推理集成仍需完善。
- **链接**: https://github.com/earendil-works/pi/issues/6922

### #8673 — TUI soft line breaks render as hard breaks [CLOSED]
- **作者**: manojbajaj95 | **评论**: 4 | **👍 2**
- **摘要**: 思考块中单 `\n` 软换行被渲染为硬断行，导致推理过程难以阅读。
- **重要性**: 直接影响思考链可读性，已有对应 PR #8674 修复。
- **链接**: https://github.com/earendil-works/pi/issues/8673

### #8774 — Compaction fails on OpenAI Responses models [CLOSED]
- **作者**: yupunit | **评论**: 2 | **👍 0**
- **摘要**: 使用 OpenAI Responses API 时，压缩请求因 `tool_choice` 未附带 tools 而返回 400。
- **重要性**: OpenAI 新 API 通道兼容性 Bug，影响上下文管理。
- **链接**: https://github.com/earendil-works/pi/issues/8774

### #8675 — TUI renders text one word per line [CLOSED]
- **作者**: kiszu | **评论**: 3 | **👍 4**
- **摘要**: WSL2/Windows Terminal 下长文本逐词换行，与 #8584 症状相似。
- **重要性**: 多平台复现的 TUI 渲染退化问题。
- **链接**: https://github.com/earendil-works/pi/issues/8675

### #8624 — Kitty key-release sequences typed as literal text [CLOSED]
- **作者**: abbood | **评论**: 2 | **👍 0**
- **摘要**: Kitty 终端键释放序列在 stdin 分块到达时被当作字面量输入。
- **重要性**: Kitty 用户高频痛点，涉及终端协议解析边界问题。
- **链接**: https://github.com/earendil-works/pi/issues/8624

### #8762 — Session list fully parses every session file [CLOSED]
- **作者**: BelovedYaoo | **评论**: 2 | **👍 0**
- **摘要**: `--resume` 选择器遍历所有 session 时完整解析 JSONL，大文件场景性能差。
- **重要性**: 会话管理性能优化，影响大量历史会话用户。
- **链接**: https://github.com/earendil-works/pi/issues/8762

### #8757 — Tool-argument validator missing object→string coercion [CLOSED]
- **作者**: beantownbytes | **评论**: 2 | **👍 0**
- **摘要**: 工具参数校验器支持 JSON 字符串→对象，但缺少反向对象→字符串转换，导致 write/edit 报 "must be string"。
- **重要性**: 工具调用稳定性问题，影响代码编辑流程。
- **链接**: https://github.com/earendil-works/pi/issues/8757

### #8771 — Apple Terminal.app crashes on macOS 26.5.2 [CLOSED]
- **作者**: lixinglong27 | **评论**: 1 | **👍 0**
- **摘要**: Pi TUI 运行时 macOS Terminal.app 崩溃。
- **重要性**: macOS 原生终端兼容性，影响 macOS 用户群体。
- **链接**: https://github.com/earendil-works/pi/issues/8771

---

## 4. 重要 PR 进展

### ✅ #8674 — fix(tui): render markdown soft line breaks as spaces [CLOSED]
- **作者**: manojbajaj95
- **内容**: 修复 `marked` 将 CommonMark 软换行 `\n` 渲染为硬断行问题，使思考块段落正常流式显示。
- **链接**: https://github.com/earendil-works/pi/pull/8674

### ✅ #8731 — feat(tui): allow disable copy on fullscreen [CLOSED]
- **作者**: cristinaponcela
- **内容**: 新增 `copyOnSelect` 设置项，禁用后可通过 `Ctrl+X` 手动复制，解决终端高亮用户误复制问题。
- **链接**: https://github.com/earendil-works/pi/pull/8731

### ✅ #6848 — fix: add retry logic to compaction summarization [CLOSED]
- **作者**: PiedPiper911
- **内容**: 为 `completeSummarization()` 添加带指数退避的有界重试，防止流式中间断连导致压缩失败。
- **链接**: https://github.com/earendil-works/pi/pull/6848

### ✅ #8764 — fix(coding-agent): honor settings.shellPath [CLOSED]
- **作者**: EralChen
- **内容**: 修复 Windows 下 `!` 前缀命令未读取 `settings.shellPath` 的问题。
- **链接**: https://github.com/earendil-works/pi/pull/8764

### ✅ #8723 — fix(coding-agent): expose https-proxy-agent named export [CLOSED]
- **作者**: rwachtler
- **内容**: 通过插件机制暴露 `https-proxy-agent` 具名导出，修复代理模式下 `HttpsProxyAgent is not a constructor` 错误。
- **链接**: https://github.com/earendil-works/pi/pull/8723

### 🔄 #8766 — feat(coding-agent): make write and edit output easier to scan [OPEN]
- **作者**: Panoplos
- **内容**: 优化 write/edit 工具输出展示，添加紧凑的文件级摘要与行号预览，提升变更可读性。
- **链接**: https://github.com/earendil-works/pi/pull/8766

### 🔄 #8262 — feat(coding-agent): dispatch hooks on every turn-start path [OPEN]
- **作者**: LogosZR
- **内容**: 修复 `sendCustomMessage(triggerTurn: true)` 未触发 `input` 钩子与 `before_agent_start` 的问题。
- **链接**: https://github.com/earendil-works/pi/pull/8262

### ✅ #3106 — fix(tui): no trailing spaces with no bg color [CLOSED]
- **作者**: deybhayden
- **内容**: 无背景色时不再用尾随空格填充行宽，避免从 VS Code 终端复制时带入无效空白。
- **链接**: https://github.com/earendil-works/pi/pull/3106

### 🔄 #8744 — feat(tui): add opt-in overlay selection exclusion [OPEN]
- **作者**: wutongyuonce
- **内容**: 允许overlay组件选择性排除在文本选择区域外，确保复制内容来自转录而非合成屏幕。
- **链接**: https://github.com/earendil-works/pi/pull/8744

### 🔄 #7602 — feat(coding-agent): configurable summarization models [OPEN]
- **作者**: haoqixu
- **内容**: 支持为压缩与分支摘要配置独立模型与思考级别，并处理 provider 错误以应对上下文窗口限制。
- **链接**: https://github.com/earendil-works/pi/pull/7602

---

## 5. 功能需求趋势

| 方向 | 热度 | 典型 Issue/PR |
|------|------|---------------|
| **TUI 渲染体验** | ⭐⭐⭐⭐⭐ | #8584, #8673, #8675, #8731, #3106 |
| **终端协议兼容** | ⭐⭐⭐⭐ | #8624 (Kitty), #8771 (Terminal.app) |
| **本地模型支持** | ⭐⭐⭐⭐ | #6922 (llama.cpp), #8752 (Bedrock) |
| **工具调用稳定性** | ⭐⭐⭐⭐ | #8757 (参数校验), #8774 (OpenAI Responses) |
| **性能优化** | ⭐⭐⭐ | #8762 (session 解析), #8711 (CPU 占用) |
| **扩展与钩子系统** | ⭐⭐⭐ | #8761 (openUrl 暴露), #8773 (before_agent_start) |
| **国际化** | ⭐⭐ | #8772 (中文 README) |

---

## 6. 开发者关注点

1. **TUI 文本渲染可靠性**: 多起 issue 反映流式输出、表格、思考块等场景下的换行与选择问题，是当前最集中的反馈领域。
2. **终端差异化兼容**: Kitty 键序列、macOS Terminal.app 崩溃、WSL2 宽度计算等问题凸显终端层抽象仍需完善。
3. **本地推理链路稳定性**: llama.cpp 默认模型加载失败、Bedrock 用量统计归一化等问题影响本地/边缘部署体验。
4. **工具链参数健壮性**: write/edit 工具的类型强制转换缺失、OpenAI Responses 压缩请求格式错误等，反映工具执行层的边界条件仍需覆盖。
5. **扩展 API 可定制性**: 开发者期望暴露 `openUrl` 等内部处理器，以支持浏览器插件、自定义 IDE 集成等场景。

---

*数据来源: github.com/badlogic/pi-mono | 生成时间: 2026-08-28*

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报
**日期：2026-08-28**

---

## 1. 今日速览

Qwen Code 发布 v0.22.2-nightly 更新，修复了 Web Shell 会话 diff 恢复及钉钉 rich-text 支持。社区焦点集中在 TUI 渲染层迁移至 OpenTUI 的架构讨论（#8662，11 评论）以及 Anthropic 通道缺少 stream-safety 保护的安全问题（#9005，8 评论）。多项关键 PR 进入 review 阶段，包括模型提供者热重载、WebShell 脏工作树处理和 HTML 制品托管分享等功能。

---

## 2. 版本发布

**v0.22.2-nightly.20260828.7357136dd1**
- 修复 Web Shell 中保存的会话 diff 无法恢复的问题（#10093）
- 修复钉钉通道 rich-text 多行内容保留问题

---

## 3. 社区热点 Issues

| Issue | 标题 | 评论 | 重要性 |
|-------|------|------|--------|
| [#8662](https://github.com/QwenLM/qwen-code/issues/8662) | Migrate TUI rendering layer from ink to OpenTUI | 11 | 架构级重构，解决当前 ink 渲染层的闪烁、虚拟化视口等结构性问题 |
| [#9005](https://github.com/QwenLM/qwen-code/issues/9005) | Anthropic wire 缺少 stream-safety 保护 | 8 | 安全漏洞：Anthropic 通道缺少 OpenAI 通道已实现的流式安全防护 |
| [#10227](https://github.com/QwenLM/qwen-code/issues/10227) | 自定义模型供应商无法对话 | 7 | 用户痛点：Moonshot 等自定义供应商的 JSON Schema 校验失败 |
| [#8551](https://github.com/QwenLM/qwen-code/issues/8551) | Add Korean (ko) to docs site | 5 | ✅ 已关闭，文档多语言支持完善 |
| [#10210](https://github.com/QwenLM/qwen-code/issues/10210) | Agent Team: team_delete 文件系统清理失败但仍报告成功 | 4 | 数据一致性 bug，`deleteTeamDirs()` 静默失败 |
| [#10356](https://github.com/QwenLM/qwen-code/issues/10356) | Main CI failed: E2E Tests | 4 | 主分支 CI 自动化测试失败跟踪 |
| [#10348](https://github.com/QwenLM/qwen-code/issues/10348) | hooks 触发事件增强 | 4 | ✅ 已关闭，支持智能体提问触发 hooks 推送 |
| [#4542](https://github.com/QwenLM/qwen-code/issues/4542) | L2 能力分层架构提案 | 4 | 长期架构设计：收口 file/auth/agents/memory 能力 |
| [#10369](https://github.com/QwenLM/qwen-code/issues/10369) | MCP Apps inline UI 在 Web Shell 不渲染 | 3 | Web Shell + MCP 集成调试困难 |
| [#10380](https://github.com/QwenLM/qwen-code/issues/10380) | Auto-compaction 在 HTTP 413 后无法恢复 | 2 | 长会话在代理限制下永久不可用 |

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 说明 |
|----|------|------|------|
| [#10269](https://github.com/QwenLM/qwen-code/pull/10269) | fix(serve): Hot-reload runtime model providers | Review | 模型提供者变更后自动重建环境并热重载配置 |
| [#10390](https://github.com/QwenLM/qwen-code/pull/10390) | feat(web-shell): unblock git update on dirty working tree | Review | WebShell "Update Project" 支持脏工作树自动处理 |
| [#10024](https://github.com/QwenLM/qwen-code/pull/10024) | feat(web-shell): share HTML artifacts through managed hosting | Review | 支持通过 Cloudflare/Vercel/Netlify 托管分享 HTML 制品 |
| [#9546](https://github.com/QwenLM/qwen-code/pull/9546) | feat(serve): expose Workflow tasks and controls | Review | Daemon 暴露 Workflow 执行状态和控制接口 |
| [#9895](https://github.com/QwenLM/qwen-code/pull/9895) | feat(daemon): support scoped workspace memory tasks | Review | 新增 project/user 级别内存任务的 scoped 支持 |
| [#9682](https://github.com/QwenLM/qwen-code/pull/9682) | refactor: deepen architecture ownership boundaries | Review | 重构 ACP transport、workspace routes 等核心边界 |
| [#9503](https://github.com/QwenLM/qwen-code/pull/9503) | feat(cli): fold completed read/search tool batches into thought line | Review | TUI 优化：将工具批次结果折叠至思考行 |
| [#10396](https://github.com/QwenLM/qwen-code/pull/10396) | fix(triage): constant-cost subsumption check | Review | 用 `gh pr diff` 替代逐文件 contents-API 调用，解决大文件静默截断 |
| [#10214](https://github.com/QwenLM/qwen-code/pull/10214) | fix(ci): recover protected qwen leftovers before checkout | Review | CI 容器中被标记为只读的 `.qwen` 目录恢复机制 |
| [#9811](https://github.com/QwenLM/qwen-code/pull/9811) | refactor(vscode-ide-companion): complete WebShell UI cutover | Review | VS Code 插件完成 WebShell UI 迁移 |

---

## 5. 功能需求趋势

- **TUI/渲染层重构**：#8662 发起的 OpenTUI 迁移是近期最受关注的架构讨论，反映出社区对当前 ink 渲染层稳定性问题的长期焦虑
- **多通道/集成完善**：钉钉 rich-text、MCP Apps UI、自定义模型供应商兼容性是高频需求
- **WebShell 体验增强**：脏工作树处理、HTML 制品托管分享、会话组持久化、推理力度持久化等 PR 集中涌现
- **Daemon 架构深化**：L2 能力分层（#4542）、工作内存作用域（#9895）、Workflow 暴露（#9546）显示 Daemon 正成为核心扩展平台
- **CI/CD 健壮性**：多份 PR 针对 triage 流程、磁盘空间检查、受保护文件恢复进行加固

---

## 6. 开发者关注点

1. **渲染稳定性**：ink 的闪烁、虚拟视口问题推动 OpenTUI 迁移讨论（#8662）
2. **安全保护缺口**：Anthropic 通道缺少 stream-safety（#9005），与 OpenAI 通道能力不对齐
3. **自定义模型兼容性**：Moonshot 等供应商的 JSON Schema 校验失败（#10227），非标准模型接入门槛高
4. **WebShell 会话状态**：会话组分配在重启后丢失（#10391）、消息编辑索引错误（#10385）
5. **CI 流程健壮性**：大文件 subsumption check 静默失败（#10322）、API 错误被误判为成功（#10314）
6. **MCP 集成调试**：MCP Apps inline UI 不渲染且无错误提示（#10369），开发体验差
7. **长会话恢复**：HTTP 413 后 auto-compaction 无法自愈（#10380），导致会话永久卡死

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI 社区动态日报
**日期：2026-08-28** | 数据来源：github.com/Hmbown/DeepSeek-TUI

---

## 1. 今日速览

今日无新版本发布，但原生 Web 搜索适配器大规模扩展（覆盖 DeepSeek、Qwen、Kimi、Z.AI、MiMo）集中合并，显著增强多模型搜索能力。社区同时聚焦多会话锁冲突、构建性能优化及插件 UX 体验等核心问题。

---

## 2. 版本发布

> 过去24小时无 Releases 发布。

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 重要性 |
|---|------|------|--------|
| #5620 | Context pressure warning 是瞬态的，agent 不主动响应 | OPEN | 🔴 安全信号失效，上下文静默退化 |
| #5630 | Runtime store owner lock 阻塞多会话运行 | CLOSED | 🔴 v0.9.12 引入的回归，仅允许单实例 |
| #5617 | 减少后台 git 命令及避免 `.git/index.lock` 冲突 | CLOSED | 🟠 开发体验痛点，`git commit` 偶发失败 |
| #5668 | 新增 `/copy` 命令复制最后模型输出 | OPEN | 🟠 高频 UX 需求，替代手动选择终端文本 |
| #5249 | Epic: v0.9.5 构建时 Lane 优化（单crate 68万行） | OPEN | 🔴 构建/测试/提交全链路性能瓶颈 |
| #5588 | Provider 中立性：18个 DeepSeek 专属 gate | OPEN | 🟡 架构整洁性，部分 gate 应跨 provider 通用 |
| #5625 | Non-blocking "pending user input" peek tool | OPEN | 🟡 增强 agent 中途引导能力 |
| #4402 | v0.9.2 Attention UX：焦点感知通知 | OPEN | 🟡 终端注意力契约统一 |
| #5579 | Plugin UX 对齐 Claude Code：热重载+推荐 | OPEN | 🟡 插件生态体验竞争力 |
| #5637 | MCP Secret providers 作用域限定至运行时 | OPEN | 🟡 多环境下的密钥生命周期管理 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| #5683 | feat(web): DeepSeek native search adapter | ✅ CLOSED | 启用 DeepSeek V4 原生 `web_search` tool，自定义端点 fail-closed |
| #5682 | fix(web): native search constraints before fallback | ✅ CLOSED | 约束在 fallback 前应用，空结果显式标记 `no_usable_results` |
| #5686 | feat(web): Moonshot & Kimi native search | 🔄 OPEN | 支持 K3 Formula、K2.6 `$web_search`、Kimi Code `/search`，限4轮/8次调用 |
| #5685 | feat(web): Z.AI & BigModel native search | 🔄 OPEN | 选 `search-prime`（全球）/`search_std`（中国），Coding Plan 仍 fail-closed |
| #5684 | feat(web): Qwen native search adapter | 🔄 OPEN | 支持 qwen3.8-max 等 ModelStudio Token Plan，`tool_choice: "required"` |
| #5687 | feat(web): Xiaomi MiMo native search | 🔄 OPEN | 支持 `mimo-v2.5-pro`，需 verifiable citations |
| #5679 | fix(chat): tool result batches 连续性 | ✅ CLOSED | 确保 tool-call/result 批次连续，丢弃被中断的 deferred 媒体 |
| #5658 | feat(tui): MCP & plugin boot 作为 session set | ✅ CLOSED | 首 turn 可见 plugin/MCP 启动状态，失败 toast 改进 |
| #5677 | feat(tui): rescue MCP/plugin session boot | ✅ CLOSED | 将 #5658  cherry-pick 至 main，保留原始提交元数据 |
| #5666 | chore(tui): gate audited test-only helpers | ✅ CLOSED | 将 13 个已审计 test-only 辅助函数从 `#[allow(dead_code)]` 改为 `#[cfg(test)]` |

---

## 5. 功能需求趋势

- **🌐 多模型原生 Web 搜索**：今日最突出趋势，覆盖 DeepSeek、Qwen、Kimi、Z.AI、MiMo，表明社区对跨 provider 搜索能力需求强烈
- **⚡ 构建与运行性能**：682,959 行单 crate 重构（#5249）及 git 探针优化（#5618 → gix 替代）持续关注
- **🔧 多会话稳定性**：runtime lock 冲突（#5630）及上下文压力管理（#5620）反映多实例场景的成熟度诉求
- **🎨 UX 细节打磨**：`/copy` 命令（#5668）、焦点感知通知（#4402）、插件热重载（#5579）
- **🔐 安全与配置迁移**：MCP secret 作用域（#5637）、Claude 配置导入（#5557）

---

## 6. 开发者关注点

1. **多会话并发阻塞**：v0.9.12 引入的全局 owner lock 导致第二实例直接失败（#5630），是近期最高优先级回归
2. **构建时间税**：68万行 TUI crate 每次 edit/commit/test 全量重编译（#5249），开发迭代效率严重受损
3. **Git 探针冲突**：内部只读探针 spawn `git status` 持有 `.git/index.lock`，与用户 `git commit` 竞争（#5617/#5618）
4. **上下文安全信号失效**：context pressure warning 仅为瞬态 toast，agent 不据此主动截断或压缩（#5620）
5. **插件生态体验差距**：用户明确要求热重载、推荐机制对标 Claude Code（#5579）

---

*报告生成时间：2026-08-28 | Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*