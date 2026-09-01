# AI CLI 工具社区动态日报 2026-09-01

> 生成时间: 2026-09-01 04:39 UTC | 覆盖工具: 10 个

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
**日期：2026-09-01 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026年9月初，AI CLI工具生态呈现"头部集中、多极分化"格局：OpenAI Codex与Claude Code持续迭代核心能力，Gemini CLI与GitHub Copilot CLI聚焦稳定性与安全性加固，Qwen Code与DeepSeek TUI（CodeWhale）在协作与架构层推进创新，Kimi Code CLI进入产品迁移过渡期。跨工具协同标准（AGENTS.md）、MCP协议兼容性、会话恢复可靠性成为行业共性挑战，社区驱动的技术路线日趋收敛。

---

## 2. 各工具活跃度对比

| 工具 | 版本 | Issues | PRs (24h) | Release | 状态 |
|------|------|--------|-----------|---------|------|
| **Claude Code** | v2.1.252 | 10 | 4 | ✅ 正式版 | 稳定迭代 |
| **OpenAI Codex** | rust-v0.152.0 | 10 | 10 | ✅ 正式版 | 高频迭代 |
| **Gemini CLI** | v0.59.0-nightly | 10 | 10 | 🔄 Nightly | 活跃开发 |
| **GitHub Copilot CLI** | v1.0.83-0 | 12 | 0 | 🔄 预发布 | 回归修复期 |
| **Qwen Code** | v0.22.3-nightly | 10 | 10 | 🔄 Nightly | 功能扩展期 |
| **DeepSeek TUI** | — | 10 | 10+ | — | 架构重构期 |
| **Kimi Code CLI** | — | 3 | 2 | — | 迁移过渡期 |
| **Grok Build** | — | — | — | — | 无活动 |
| **OpenCode / Pi** | — | — | — | ⚠️ | 摘要失败 |

---

## 3. 共同关注的功能方向

### 3.1 会话管理与恢复可靠性
| 工具 | 具体问题 |
|------|---------|
| Claude Code | Remote Control 会话卡顿（>60s）、会话自动重命名缺失 |
| GitHub Copilot CLI | JS Heap OOM 崩溃（#4664）、自定义 agent 未还原（#4674） |
| DeepSeek TUI | 核心修复：Engine 采纳 Host session id（#5750） |
| Qwen Code | `--resume` 路径未覆盖 `dangling-unsigned-thought` 隐患（#8535） |
| Gemini CLI | Generalist Agent 无限挂起（#21409）、shell 命令后卡在 "Waiting input"（#25166） |

### 3.2 MCP 协议与扩展生态
| 工具 | 具体问题 |
|------|---------|
| Claude Code | OAuth token 不自动刷新（#65036）、Gmail 附件支持需求 |
| GitHub Copilot CLI | MCP 初始化协议冲突（#4525）、单服务器无响应阻塞启动（#4678） |
| Qwen Code | `toolSearch` threshold 导致 llama.cpp 400 错误（#10520） |
| OpenAI Codex | MCP `tools/list` 分页缺失（#28858） |

### 3.3 安全与权限治理
| 工具 | 具体问题 |
|------|---------|
| Claude Code | Fable 5 `reasoning_extraction` 误报（#87640） |
| GitHub Copilot CLI | ACP 模式 `session/close` 缺失（#4113）、tool 挂起风险（#4670） |
| Gemini CLI | Auto Memory 日志泄露（#26525）、环境变量注入（#28863/#29008） |
| Qwen Code | Review 流程信任锚位于模型会话写表面内（#10654） |

### 3.4 跨平台与本地模型兼容性
| 工具 | 具体问题 |
|------|---------|
| OpenAI Codex | Windows Shell 延迟 8-11x 退化（#41942）、WSL 路径异常（#41290） |
| Gemini CLI | Browser Agent Wayland 兼容性问题（#21983） |
| Kimi Code CLI | Windows GBK 编码崩溃（#2629） |
| Qwen Code | llama.cpp 本地模型 400 解析错误（#10520/#10530） |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|---------|---------|---------|
| **Claude Code** | AGENTS.md 标准化、企业级预算治理、Remote Control | 企业开发者、Anthropic 生态用户 | 权限精细化 + 安全拦截（Fable 5） |
| **OpenAI Codex** | Vim 模式、速率限制管理、插件协调 API | 终端用户、Codex 订阅者 | TUI 交互优化 + Guardian 遥测增强 |
| **Gemini CLI** | 子代理架构、AST 感知工具、零依赖沙箱 | 研究型用户、Google 生态开发者 | Agent 化架构 + 安全审计优先 |
| **GitHub Copilot CLI** | ACP 模式、企业网络适配（mTLS） | 企业 DevOps、GitHub Actions 用户 | 协议兼容 + 企业安全加固 |
| **Qwen Code** | 跨会话 IPC、Web Shell 可视化、本地模型支持 | 多 Agent 协作场景、本地部署用户 | 多 Agent 通信 + 工作流可视化 |
| **DeepSeek TUI** | 原生登录、架构重构（TUI Crate 拆分） | DeepSeek 生态用户、开源贡献者 | Rust/TD 混合架构 + 协议层对齐 |
| **Kimi Code CLI** | 产品迁移（kimi-cli → Kimi Code） | 存量 kimi-cli 用户 | 平滑迁移 + 弃用引导 |

---

## 5. 社区热度与成熟度

### 🔥 高活跃度（高频迭代 + 大量社区反馈）
- **OpenAI Codex**：10 PR/24h 全部闭环，Windows 稳定性问题集中爆发，用户基数大
- **Gemini CLI**：Nightly 版本快速迭代，子代理可靠性问题成 P1 级痛点，安全审计受重视
- **Qwen Code**：Web Shell 功能矩阵完善（工作流可视化 + 会话搜索 + 工作区总览），多 Agent 协作方向明确

### ⚡ 中活跃度（稳定迭代 + 关键修复）
- **Claude Code**：v2.1.252 修复关键回归，AGENTS.md 标准化获 5094👍 社区支持，SEV-1 预算计量问题需关注
- **DeepSeek TUI**：10+ PRs 涵盖架构重构、原生登录、会话恢复，EPIC #5316 持续推进

### 📉 低活跃度（过渡期或规模较小）
- **GitHub Copilot CLI**：1.0.81/82 连续回归导致用户信任受损，当前处于修复窗口期
- **Kimi Code CLI**：仅 3 Issues / 2 PRs，处于产品迁移过渡期，Windows 编码问题未解决

---

## 6. 值得关注的趋势信号

### 6.1 AGENTS.md 成为跨工具协作事实标准
Claude Code #6235 获 5094👍 并已关闭，多家工具跟进。未来多 Agent 协作、权限互认、配置共享将围绕此标准展开。

### 6.2 子代理可靠性成为新战场
Gemini CLI（#22323、#21409、#21983）与 Qwen Code（#8724、#9450）均面临子代理行为不可预测问题。行业正从"能否调用子代理"进入"子代理是否可靠"阶段。

### 6.3 企业级治理需求显性化
- Claude Code SEV-1 预算计量偏差（#83048）
- GitHub Copilot CLI mTLS 支持（v1.0.83-0）
- Qwen Code Review 流程权限隔离（#10654）
企业用户对计费透明、网络适配、权限隔离的需求推动工具向生产级靠拢。

### 6.4 本地模型兼容性仍是短板
OpenAI Codex（Windows 延迟回归）、Qwen Code（llama.cpp 400 错误）、Kimi Code CLI（Windows GBK 编码）均暴露跨平台/本地模型兼容性问题，尤其是亚洲用户群体受影响显著。

### 6.5 会话恢复机制进入深度优化期
DeepSeek TUI（#5750 根因修复）、Qwen Code（#8535 安全隐患）、GitHub Copilot CLI（#4664 OOM 崩溃）均在此方向发力，反映用户对工作流连续性的高度依赖。

---

**建议开发者关注：**
- 企业用户：优先评估 Claude Code 预算计量修复进展、GitHub Copilot CLI mTLS 实际效果
- 多 Agent 场景：跟踪 Gemini CLI 子代理可靠性修复、Qwen Code 跨会话 IPC 落地
- 本地部署：关注 Qwen Code llama.cpp 兼容性修复、各工具 Windows 平台稳定性改进
- 迁移用户：Kimi Code CLI 迁移流程（PR #2630）值得留意，避免后续兼容风险

---

*报告生成时间：2026-09-01 | 数据来源：各工具 GitHub 仓库社区动态*

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告（截至 2026-09-01）

---

## 1. 热门 Skills 排行

| 排名 | PR | Skill 名称 | 功能概述 | 状态 | 社区热度 |
|------|-----|-----------|---------|------|---------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | skill-creator (eval fix) | 修复 `run_eval.py` 始终报告 0% recall 的核心 Bug，关联 10+ 独立复现；含 Windows 流读取、触发检测、并行 Worker 修复 | 🔵 Open | Issue #556 有 12 条评论、7 👍 |
| 2 | [#1628](https://github.com/anthropics/skills/pull/1628) | Hivemind | 零成本多 Agent 编排：将机械工作委托给免费模型（opencode 无头节点），Claude Code 作为唯一规划/审核/合并中枢 | 🔵 Open | 高创新度，解决上下文稀缺痛点 |
| 3 | [#83](https://github.com/anthropics/skills/pull/83) | skill-quality-analyzer + skill-security-analyzer | 双元元技能：从结构/文档（20%）、准确性（25%）、安全性（25%）、可用性（20%）、性能（10%）五维评估 Skills 质量 | 🔵 Open | 填补 Skills 审核基础设施空白 |
| 4 | [#514](https://github.com/anthropics/skills/pull/514) | document-typography | 文档排版质量控制：修复孤儿换行、寡妇段落、编号错位等 AI 生成文档常见问题 | 🔵 Open | 实用高频需求 |
| 5 | [#568](https://github.com/anthropics/skills/pull/568) | servicenow | ServiceNow 全平台 Skill：覆盖 ITSM、ITOM、SecOps、ITAM/SAM、FSM、SPM、CSDM、IntegrationHub | 🔵 Open | 企业级需求，开放超 6 个月 |
| 6 | [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns | 完整测试栈 Skill：Testing Trophy 模型、AAA 模式、React Testing Library、Edge Cases、纯函数测试策略 | 🔵 Open | 测试工程化需求旺盛 |
| 7 | [#1367](https://github.com/anthropics/skills/pull/1367) | self-audit | 交付前自检 Skill：机械文件验证 + 四维度推理质量门禁（v1.3.0），通用技术栈 | 🔵 Open | 质量门禁类 Skill 持续迭代 |
| 8 | [#486](https://github.com/anthropics/skills/pull/486) | odt | OpenDocument 格式（.odt/.ods）创建、模板填充、转 HTML；LibreOffice 生态兼容 | 🔵 Open | ODF 标准生态补充 |

---

## 2. 社区需求趋势

从 Issues 高频讨论中提炼五大方向：

| 趋势 | 代表 Issue/PR | 核心诉求 |
|------|-------------|---------|
| **🔒 安全与信任治理** | [#492](https://github.com/anthropics/skills/issues/492)（43 评论） | 社区 Skills 冒充官方 `anthropic/` 命名空间，触发信任边界漏洞，亟需 namespace 隔离机制 |
| **🏢 组织协作与共享** | [#228](https://github.com/anthropics/skills/issues/228)（16 评论，8 👍） | 企业级 Skill 共享：当前需手动下载/上传，期望支持 Org 内分享链接或共享库 |
| **⚖️ 评估与质量保证** | [#556](https://github.com/anthropics/skills/issues/556)、[#1385](https://github.com/anthropics/skills/issues/1385)、[#1390](https://github.com/anthropics/skills/issues/1390) | `run_eval.py` 触发机制失效、Evaluation 序列化 Bug、推理质量门禁三Gate管线（Pre-task → Adversarial → Delivery） |
| **🧠 上下文效率优化** | [#1487](https://github.com/anthropics/skills/issues/1487)、[#1329](https://github.com/anthropics/skills/issues/1329) | `claude-api` Skill 单次注入 ~156k tokens 撑爆上下文；需要 compact-memory 等符号化状态压缩方案 |
| **🏭 企业平台集成** | [#568](https://github.com/anthropics/skills/pull/568)、[#1175](https://github.com/anthropics/skills/issues/1175)、[#29](https://github.com/anthropics/skills/issues/29) | ServiceNow、SharePoint Online、AWS Bedrock 等平台级 Skill 需求持续增加，同时伴生安全顾虑 |

---

## 3. 高潜力待合并 Skills

以下 PR 讨论活跃、问题明确，具备近期合并条件：

| PR | 理由 |
|----|------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | 阻塞 skill-creator 整个评估链路，多个子修复已收敛，高优先级 |
| [#538](https://github.com/anthropics/skills/pull/538) / [#541](https://github.com/anthropics/skills/pull/541) | 同一作者修复 PDF/DOCX 确定性 Bug，影响面广，低风险 |
| [#1607](https://github.com/anthropics/skills/pull/1607) | 修复已退役模型 ID 列表，纯文档更新，无回归风险 |
| [#1628](https://github.com/anthropics/skills/pull/1628) | Hivemind 解决多 Agent 编排成本痛点，架构创新，但需安全审查 |
| [#1367](https://github.com/anthropics/skills/pull/1367) | self-audit v1.3.0 已迭代至稳定，质量门禁符合社区方向 |
| [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns 覆盖测试全栈，需求明确，合并价值高 |
| [#568](https://github.com/anthropics/skills/pull/568) | ServiceNow 企业 Skill 开放超 6 个月，覆盖范围完整，但需评估权限边界 |

---

## 4. Skills 生态洞察

> **当前社区最集中的诉求是：在确保安全边界和组织协作的前提下，建立可信赖的 Skills 质量评估体系——社区既需要更可靠的 Skill 评估基础设施（eval 修复、自检门禁），也迫切需要解决命名空间信任滥用和组织内 Skill 共享的协作效率问题。**

---



# Claude Code 社区动态日报 — 2026-09-01

## 1. 今日速览

Claude Code v2.1.252 发布，修复了 Bash 命令失败、"always allow" 权限不保存及 Remote Control 会话卡住等关键问题。社区持续热推 AGENTS.md 标准化支持（5094 👍），同时 MCP OAuth 自动刷新、跨平台 Cowork 同步稳定性、Fable 5 安全拦截误报成为近期高频痛点。

---

## 2. 版本发布

### v2.1.252
- **修复** Bash 命令在部分 Mac 上报错 "task output swap refused (tasks dir moved or linked)"
- **修复** 无 `.claude/settings.local.json` 的项目中 "always allow" 权限设置不保存
- **修复** 由 Claude Desktop 或 VS Code 托管的 Remote Control 会话卡顿超过一分钟的问题

---

## 3. 社区热点 Issues

| # | 标题 | 评论 | 👍 | 状态 |
|---|------|------|-----|------|
| #6235 | 支持 AGENTS.md 标准化（对标 Codex/Cursor） | 389 | 5094 | ✅ CLOSED |
| #84352 | CVP 认证组织仍被 cyber safeguard 拦截 | 168 | 25 | 🔄 OPEN |
| #20697 | Desktop 与 CLI 间同步 Skills | 43 | 150 | 🔄 OPEN |
| #29355 | 允许 Claude 程序化重命名会话 | 15 | 92 | ✅ CLOSED |
| #81658 | 跨平台同步故障导致 Cowork 对话消失 | 14 | 4 | 🔄 OPEN |
| #87640 | Fable 5 `[reasoning_extraction]` 误报（单词 "Hi" 也被拦截） | 12 | 14 | 🔄 OPEN |
| #28575 | Gmail MCP：支持文件附件 & 发送草稿工具 | 11 | 33 | 🔄 OPEN |
| #65036 | MCP OAuth 不自动刷新 token，每日提示过期 | 10 | 34 | 🔄 OPEN |
| #88490 | Cloud Cowork OTLP 遥测丢失身份属性 | 7 | 19 | 🔄 OPEN |
| #83048 | `[SEV-1]` budget.spent() 低估 72 倍，绕过预算控制 | 3 | 0 | 🔄 OPEN |

**重点解读：**
- **#6235**：社区对 AGENTS.md 标准化呼声极高（5094 👍），多家 AI 编程工具已跟进，Anthropic 已接受该需求。
- **#84352 / #87640 / #90922**：Fable 5 安全拦截误报问题集中爆发，影响正常会话启动。
- **#65036 / #90647**：MCP OAuth 令牌管理和账户切换体验亟待改善。
- **#83048**：预算监控严重失准，可能导致企业用户超额消费，属 SEV-1 级别。

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| #75541 | fix(sweep): 分页 issue 事件并正确处理 unlabeled 关闭逻辑 | ✅ CLOSED | 修复自动清理过期 issue 的逻辑缺陷 |
| #75537 | fix(hook-development): 识别全部五种 hook handler 类型 | ✅ CLOSED | 修复插件开发文档与实际产品脱节 |
| #75529 | docs: 厘清 code-review plugin 与内置 /code-review skill 的关系 | ✅ CLOSED | 避免用户混淆两者用途和命令空间 |
| #89404 | validate-agent.sh: 不在第一个 warning 时退出，修复误报 | 🔄 OPEN | 修复 `set -e` 与算术表达式交互导致的提前中止 |

> 注：过去24小时内共 4 条 PR 更新，均已闭环或接近完成。

---

## 5. 功能需求趋势

1. **标准化与互操作性**：AGENTS.md 成为跨工具协作的事实标准，社区强烈期望 Claude Code 跟进。
2. **MCP 生态完善**：OAuth 令牌管理、URL-mode elicitation、Gmail 附件支持等功能需求密集。
3. **多端体验一致**：Desktop ↔ CLI ↔ VS Code ↔ Android 的 Skills / 会话 / 权限同步是高频痛点。
4. **企业级治理能力**：预算监控准确性、Cowork 遥测完整性、权限降级问题影响生产使用。
5. **平台稳定性**：macOS (Tahoe)、Windows、Linux 均有专项 bug 反馈，跨平台一致性待加强。

---

## 6. 开发者关注点

**高频痛点：**
- **安全拦截误报**：Fable 5 的 `reasoning_extraction` 对合法输入过度敏感，已出现回归。
- **MCP OAuth 刷新失败**：token 不自动刷新、账户切换后权限全部丢失，需手动重授权。
- **权限系统不稳定**：`bypassPermissions` 被静默降级为 `manual`，`--permission-mode` 参数失效。
- **预算计量严重偏差**：`budget.spent()` 报告值与实际消耗相差 72 倍，风险极高。
- **会话管理缺陷**：自动重命名缺失、远程会话卡顿、scheduled task 卡死占用并发槽位。
- **跨平台同步故障**：Cowork 对话消失、VS Code 扩展在映射网络驱动器/非 ASCII 路径下会话列表为空。

**建议关注：**
- #6235（AGENTS.md）— 已关闭，关注落地进展
- #83048（预算计量）— SEV-1，需官方紧急响应
- #87640 / #90922（Fable 5 误报）— 重复出现，影响面广
- #65036 / #90647（MCP OAuth）— 企业用户高频痛点

---

*数据来源：github.com/anthropics/claude-code | 生成时间：2026-09-01*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-09-01**

---

## 1. 今日速览

今日 Codex 发布 v0.152.0 正式版，重点更新 Vim 模式搜索功能与速率限制管理横幅。社区高频关注 Windows 平台稳定性问题（终端延迟、进程退出）以及模型容量限制导致的任务中断，另有 Pro 用户报告配额异常消耗情况。

---

## 2. 版本发布

### rust-v0.152.0 正式版

**新增功能：**
- **Vim 模式增强**：支持在草稿中使用 `/` 和 `?` 进行搜索，匹配项高亮显示，可通过 `n`/`N` 重复导航 (#41586)
- **速率限制横幅交互升级**：提供查看用量、管理积分、重置限制及管理订阅计划的操作入口 (#41742)
- **终端 UI 与 `codex exec` 改进**：优化后台终端输入预览，限制为 12 行渲染并绑定 64 KiB 处理上限 (#41937)

**相关 Alpha 版本：**
- `rust-v0.152.0-alpha.7.2`、`rust-v0.152.0-alpha.7`

---

## 3. 社区热点 Issues

| # | 标题 | 热度 | 关注原因 |
|---|------|------|----------|
| [#25828](https://github.com/openai/codex/issues/25828) | 手机验证码无法发送 | 31评论 👍5 | 印尼用户反馈登录验证长期失败，涉及多地区手机号 |
| [#27117](https://github.com/openai/codex/issues/27117) | Windows PowerShell 环境继承导致更新失败 | 26评论 👍18 | 跨版本兼容性问题，影响 Windows 自动更新流程 |
| [#41290](https://github.com/openai/codex/issues/41290) | Windows+WSL 项目创建/删除失败 | 21评论 👍8 | WSL 环境切换后项目操作异常，影响开发者工作流 |
| [#41059](https://github.com/openai/codex/issues/41059) | Desktop 外部 CLI 兼容后界面无头运行 | 16评论 | 桌面端与 CLI 协作场景的显示异常 |
| [#39678](https://github.com/openai/codex/issues/39678) | Android→macOS 远程"无项目"信任错误 | 14评论 👍10 | 跨平台远程控制的权限验证缺陷 |
| [#41513](https://github.com/openai/codex/issues/41513) | Windows 悬浮宠物点击穿透 | 13评论 👍2 | UI 交互 bug，影响桌面体验 |
| [#41241](https://github.com/openai/codex/issues/41241) | Windows 本地工具主机更新后握手退出 | 12评论 | 工具调用链中断，影响 Code Mode 执行 |
| [#41942](https://github.com/openai/codex/issues/41942) | Windows Shell 执行延迟回归 8-11x | 6评论 | 性能严重退化，1.7s→18.4s 中位延迟 |
| [#40067](https://github.com/openai/codex/issues/40067) | Plus 周用量数小时内归零 | 8评论 👍2 | 用量计量疑似回归，引发用户信任问题 |
| [#41969](https://github.com/openai/codex/issues/41969) | Pro Lite 配额突然耗尽且未恢复 | 4评论 | 配额重置机制异常，影响付费用户权益 |

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 功能说明 |
|----|------|------|----------|
| [#41941](https://github.com/openai/codex/pull/41941) | 为 TUI Composer 添加 Vim 撤销 | ✅ Closed | 草稿级有界撤销历史，`u` 恢复完整状态 |
| [#41946](https://github.com/openai/codex/pull/41946) | 扩展扩展权限回归测试覆盖 | ✅ Closed | 验证图片生成扩展每轮权限绑定及文件系统权限读取 |
| [#41944](https://github.com/openai/codex/pull/41944) | 为 ChatGPT 会话发射轮次成本遥测 | ✅ Closed | 通过专用端点查询估算成本并记录 `codex.turn.cost_microusd` |
| [#41950](https://github.com/openai/codex/pull/41950) | 改进嵌套工具调用与 exec 进程追踪 | ✅ Closed | 为 Code Mode 回调保留执行上下文并添加嵌套 span |
| [#41934](https://github.com/openai/codex/pull/41934) | 忽略 Code Mode 小于 25ms 的 WAV 输出 | ✅ Closed | 音频模型无法可靠编码过短片段，以文本替代 |
| [#41931](https://github.com/openai/codex/pull/41931) | 提升 Guardian 消息转录限制 | ✅ Closed | 预算从 10K→20K tokens，单条从 2K→5K tokens |
| [#41953](https://github.com/openai/codex/pull/41953) | 强制市场来源策略覆盖精选插件 | ✅ Closed | 验证本地精选目录符合 OpenAI 插件 Git 来源政策 |
| [#41949](https://github.com/openai/codex/pull/41949) | 添加插件协调 App-Server API | ✅ Closed | 新增 `plugin/reconcile` JSON-RPC 方法同步远程插件包 |
| [#41940](https://github.com/openai/codex/pull/41940) | 回溯选择期间保留转录布局缓存 | ✅ Closed | 避免每次选择变更重渲染整个转录 |
| [#41937](https://github.com/openai/codex/pull/41937) | 限制后台终端输入预览 | ✅ Closed | 内联预览限制 12 行/64 KiB，超长时显示提示 |

---

## 5. 功能需求趋势

1. **Windows 平台稳定性**：多起 Issue 聚焦 Windows 端终端延迟、进程退出、WSL 路径处理异常，社区对 Windows 体验改进呼声强烈
2. **认证与配额透明化**：手机验证失败、刷新 token 失效、用量计量异常等问题频发，用户期待更可靠的认证流和用量追踪
3. **长期任务可靠性**：模型容量限制导致任务中断后无优雅恢复机制（#41810、#41808），社区需要更稳定的任务调度
4. **MCP 支持完善**：MCP `tools/list` 分页缺失（#28858）被多次提及，插件协调 API 的 PR 显示官方正在补强此能力
5. **跨平台远程协作**：Android→macOS 远程连接、WSL 集成等跨平台场景的 bug 持续出现，反映分布式工作流需求增长

---

## 6. 开发者关注点

- **性能回归敏感**：Shell 执行延迟 8-11 倍退化（#41942）引发开发者强烈关注，对版本升级后的性能基线要求提高
- **用量计费信任**：Pro/Plus 用户报告配额异常消耗（#40067、#41965、#41969），计费透明度成为高频痛点
- **环境兼容性**：Windows/WSL/PowerShell 环境下的路径处理、进程继承、权限预批准等问题集中在 #27117、#41463、#41928
- **认证链路稳定性**：#25828（手机验证）和 #41973（token 刷新）反映认证环节的脆弱性
- **调试可观测性**：多个 PR 聚焦遥测、诊断报告、Guardian 日志完善，说明开发者对问题定位工具需求强烈

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报 — 2026-09-01

## 1. 今日速览

Gemini CLI 发布 v0.59.0-nightly 版本，今日社区活跃聚焦于 **子代理（Subagent）可靠性修复** 与 **安全增强**。核心痛点包括：子代理在达到最大轮次后错误报告成功状态、浏览器代理在 Wayland 环境下崩溃，以及背景 Git 操作劫持 stdin 的问题。与此同时，团队推进了多项安全修复，包括环境变量清理、NTFS 短路径防护和系统配置权限校验。

---

## 2. 版本发布

| 版本 | 类型 | 链接 |
|------|------|------|
| **v0.59.0-nightly.20260901.g0bd1d4397** | Nightly | [Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.59.0-nightly.20260831.g0bd1d4397...v0.59.0-nightly.20260901.g0bd1d4397) |

---

## 3. 社区热点 Issues（Top 10）

### 🔥 P1 级 Bug — 影响核心体验

**#22323 — Subagent 达到最大轮次后错误报告 GOAL 成功**
- 作者: matei-anghel | 💬 13 | 👍 2
- `codebase_investigator` 子代理在未达到目标、仅因轮次限制而终止时，仍返回 `status: "success"` 和 `Termination Reason: "GOAL"`，掩盖了实际中断原因。
- [链接](https://github.com/google-gemini/gemini-cli/issues/22323)

**#21409 — Generalist Agent 无限挂起**
- 作者: turmanticant | 💬 8 | 👍 8
- 当 Gemini CLI 将任务委托给 generalist agent 时，简单操作（如创建文件夹）也会永久挂起，等待超一小时无响应。禁用子代理可绕过。
- [链接](https://github.com/google-gemini/gemini-cli/issues/21409)

**#25166 — Shell 命令执行后卡在 "Waiting input"**
- 作者: rnett | 💬 4 | 👍 3
- 简单 CLI 命令执行完毕后，终端仍显示命令处于活跃状态并提示 "Awaiting user input"，导致交互阻塞。
- [链接](https://github.com/google-gemini/gemini-cli/issues/25166)

**#21983 — Browser Agent 在 Wayland 下失败**
- 作者: sigmaSd | 💬 4 | 👍 1
- 浏览器子代理在 Wayland 环境中启动即失败，终止原因显示为 GOAL，但实际未执行任何操作。
- [链接](https://github.com/google-gemini/gemini-cli/issues/21983)

**#22186 — get-shit-done 输出钩子导致崩溃**
- 作者: businesscasual98 | 💬 3 | 👍 0
- 任务接近完成打印用户摘要时，Gemini CLI 整体崩溃，影响开发工作流连续性。
- [链接](https://github.com/google-gemini/gemini-cli/issues/22186)

### 🛡️ 安全相关

**#26525 — Auto Memory 日志泄露风险**
- 作者: SandyTao520 | 💬 5 | 👍 0
- Auto Memory 在将转录内容发送至模型前未做确定性脱敏，且服务会记录 skill 内容，存在敏感信息泄露隐患。
- [链接](https://github.com/google-gemini/gemini-cli/issues/26525)

**#22267 — Browser Agent 忽略 settings.json 配置覆盖**
- 作者: hsm207 | 💬 3 | 👍 0
- `maxTurns` 等设置在 `settings.json` 中的覆盖对 Browser Agent 完全无效，导致配置行为不符合预期。
- [链接](https://github.com/google-gemini/gemini-cli/issues/22267)

### 💡 功能增强

**#19873 — 利用 Zero-Dependency OS Sandboxing 发挥模型 Bash 能力**
- 作者: abhipatel12 | 💬 8 | 👍 1
- 建议通过无依赖沙箱机制让 Gemini 3 模型以原生 bash 方式操作， chaining POSIX 工具探索代码库，同时保障安全。
- [链接](https://github.com/google-gemini/gemini-cli/issues/19873)

**#22745 — AST 感知文件读取与搜索评估**
- 作者: gundermanc | 💬 7 | 👍 1
- 评估 AST 感知工具的价值：精确读取方法边界、减少 token 浪费、提升代码库导航效率。
- [链接](https://github.com/google-gemini/gemini-cli/issues/22745)

**#21968 — Gemini 未充分使用 Skills 和 Sub-agents**
- 作者: rnett | 💬 6 | 👍 0
- 用户反馈即使有匹配的自定义 skill（如 gradle、git），模型也不会主动调用，需显式指令才能触发。
- [链接](https://github.com/google-gemini/gemini-cli/issues/21968)

---

## 4. 重要 PR 进展（Top 10）

| # | 标题 | 状态 | 作者 | 说明 |
|---|------|------|------|------|
| #29022 | retain ask_user question in text history | OPEN | RaphaelDDL | 新增 `ui.keepAskUserQuestionsInHistory` 配置，保留 ask_user 工具的问题历史，便于会话恢复和选择回顾。 |
| #28863 | prompt for consent on env changes & sanitize runtime env vars | ✅ CLOSED | amelidev | 修复扩展更新绕过用户同意检查、向 MCP 进程注入未授权环境变量的安全问题。 |
| #28866 | ignore .gemini folder by default in file search | ✅ CLOSED | Rajeev91691 | 将 `.gemini` 加入默认忽略目录，避免 chokidar 监视器和爬虫在用户 home 目录产生冗余索引。 |
| #29017 | dedupe symlinked skill directories | OPEN | Kanika0306 | 修复 Windows junction 和 POSIX symlink 场景下 skill 目录重复加载问题（#28944）。 |
| #29008 | strip execution-affecting GIT_* env vars | OPEN | chelsealong | 修复 `getSafeGitEnv` 仅清理 `GIT_CONFIG_*` 而遗漏其他执行影响变量的问题（#29003）。 |
| #29005 | normalize DEBUG env var truthiness in sandbox | OPEN | Eswar809 | 统一沙箱工具对 `DEBUG` 变量的解释，防止 `"false"` / `"0"` 字符串意外启用调试功能。 |
| #29004 / #28995 | guard formatTruncatedToolOutput against negative maxChars | OPEN | Eswar809 / Kanika0306 | 修复 `formatTruncatedToolOutput` 在 `maxChars` 为负时因 JS `slice()` 负索引行为导致输出膨胀的问题（#28620）。 |
| #29148 | prevent background git ops from hijacking stdin | OPEN | DavidAPierce | 修复后台 Git 操作（`listRemote`、`clone`）未禁用交互式提示，在需要凭据时阻塞 stdin 的问题（#23480）。 |
| #29115 | enforce strict permission checks on system-wide config | OPEN | jesussamuel-byte | 在 Windows 和 POSIX 平台加载系统级配置前强制验证文件所有权和 ACL，增强配置加载安全性。 |
| #29120 | improve web fetch destination validation & connection routing | OPEN | diegogodinezr | 增强 `WebFetchTool` 的目标地址验证，通过异步 DNS 查找和 Undici 传输绑定解决地址，保留 TLS 凭证。 |

---

## 5. 功能需求趋势

基于今日 Issue 分析，社区关注方向集中在：

| 方向 | 热度 | 代表 Issue |
|------|------|------------|
| **子代理可靠性** | ⭐⭐⭐⭐⭐ | #22323, #21409, #21983, #22186 |
| **安全与隐私** | ⭐⭐⭐⭐⭐ | #26525, #26522, #26523, #29008 |
| **配置与技能系统** | ⭐⭐⭐⭐ | #21968, #20079, #29017 |
| **工具调用优化** | ⭐⭐⭐⭐ | #22745, #22466, #19561 |
| **终端交互体验** | ⭐⭐⭐ | #25166, #22465, #21924 |
| **沙箱与执行环境** | ⭐⭐⭐ | #19873, #29005, #29120 |

---

## 6. 开发者关注点

### 高频痛点

1. **子代理行为不可预测**：多个 Issue 指向子代理（codebase_investigator、browser_agent、generalist）在边界条件下表现异常——错误报告成功、无限挂起、忽略配置、Wayland 兼容性问题。这是当前社区最集中的反馈。

2. **安全敏感操作缺乏防护**：环境变量注入（#28863, #29008）、Auto Memory 日志泄露（#26525）、NTFS 短路径穿越（#29116）等问题表明开发者对 CLI 作为代码执行环境的安全性高度关注。

3. **配置系统不一致**：`settings.json` 覆盖对部分 agent 无效（#22267）、symlink 技能不被识别（#20079）、`.gemini` 目录未被默认忽略（#28866），反映出配置解析层存在碎片化。

4. **交互阻塞问题**：shell 命令完成后仍显示 "Waiting input"（#25166）、vite 创建卡在交互式提示（#22465），影响开发流畅度。

### 建议跟踪

- 关注 **#22323** 和 **#21409** 的 retest 状态，这两个 P1 问题直接影响 agent 可靠性。
- **#19873** 提出的 Zero-Dependency OS Sandboxing 方案若落地，可能从根本上改变模型与 shell 的交互模式。
- **#22745** 的 AST 感知工具评估结果将影响后续代码理解能力的优化方向。

---

*数据来源：github.com/google-gemini/gemini-cli | 统计周期：2026-09-01 过去24小时*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-09-01 | 数据来源：github.com/github/copilot-cli**

---

## 1. 今日速览

v1.0.83-0 预发布版本上线，新增 mTLS 代理证书支持及 herdr 终端兼容。过去24小时内社区集中反馈 1.0.81/82 版本的多项回归问题，涉及 BYOK 模式、OAuth 认证、会话恢复等核心功能，ACP 模式与 MCP 集成问题亦有新增报告。

---

## 2. 版本发布

### v1.0.83-0

- **新增**：自动 HTTPS 代理 mTLS 客户端证书支持，用于模型请求和 Web 请求
- **新增**：识别 herdr 终端多路复用器（而非误识别为 tmux），使 Kitty 键盘协议、配色跟随、终端进度、`/copy` 和通知功能在 herdr 窗格中正常工作

---

## 3. 社区热点 Issues

### 🔴 高优先级（回归/阻塞性问题）

| Issue | 摘要 | 关注点 |
|-------|------|--------|
| [#4672](https://github.com/github/copilot-cli/issues/4672) | 1.0.82 回归：BYOK 模式下 `/model` 命令失效 | 环境变量设置模型后命令无法识别，影响自定义模型用户 |
| [#4671](https://github.com/github/copilot-cli/issues/4671) | 1.0.81 回归：TLS  inspecting 代理下 OAuth 登录失败 | 企业网络环境用户无法认证，1.0.80 正常工作 |
| [#4664](https://github.com/github/copilot-cli/issues/4664) | 恢复长会话时 JS Heap OOM 崩溃 | 长时间会话无法恢复，阻塞工作流 |
| [#4678](https://github.com/github/copilot-cli/issues/4678) | ACP 模式 `session/new` 因单个 MCP 无响应阻塞 192s | 无超时预算机制，单个慢服务器拖慢整体启动 |
| [#4663](https://github.com/github/copilot-cli/issues/4663) | compaction 失败后无退避无限重试，产生账单 | 无界计费重试 + 上下文单调增长，无用户可见错误 |

### 🟡 中优先级（功能缺陷）

| Issue | 摘要 | 关注点 |
|-------|------|--------|
| [#4113](https://github.com/github/copilot-cli/issues/4113) ✅ CLOSED | ACP 模式未实现 `session/close` | ACP 客户端无法释放会话，已关闭但需关注修复状态 |
| [#4674](https://github.com/github/copilot-cli/issues/4674) | 恢复会话时未还原自定义 agent（#917 回归） | mcp-servers/tools allow-list 未重新应用 |
| [#4673](https://github.com/github/copilot-cli/issues/4673) | 会话恢复自动继续用户中止的工作 | `working` 标志未在用户中断时清除，导致循环陷阱 |
| [#4670](https://github.com/github/copilot-cli/issues/4670) | 扩展启动失败后 tool call 挂起 | 扩展进程退出后 CLI 仍暴露其自定义工具，调用永久 pending |
| [#4525](https://github.com/github/copilot-cli/issues/4525) | 1.0.81-1 在现代 `server/discover` 后发送 legacy `initialize` | MCP stdio 服务器初始化失败（错误 -32022） |

### 🟢 功能需求

| Issue | 摘要 | 👍 |
|-------|------|-----|
| [#1953](https://github.com/github/copilot-cli/issues/1953) | 永久显示上下文窗口状态 | 9 — 上下文使用率直接影响 LLM 性能，用户希望实时可见 |
| [#4630](https://github.com/github/copilot-cli/issues/4630) | 暴露 `large_output_file_path` 于 TaskShellProgress | 0 — 当前 rolling window 丢失大量输出，客户端无法获取完整结果 |

---

## 4. 重要 PR 进展

> 过去24小时内无新 PR 更新。

---

## 5. 功能需求趋势

从本期 Issues 中提炼出社区最关注的五个方向：

1. **会话管理与恢复可靠性** — 多起回归涉及 session resume（#4664、#4674、#4673），开发者对会话状态保真度要求高
2. **MCP 协议兼容性** — #4525、#4678、#4662 均指向 MCP 初始化、发现和认证链路的稳定性问题
3. **企业网络适配** — OAuth 认证在 TLS Inspecting 代理下失败（#4671），mTLS 支持（v1.0.83-0）正是对此的回应
4. **ACP/Agent 模式成熟度** — session/close 缺失（#4113）、tool 挂起（#4670）、延迟创建（#4668）表明 ACP 协议实现仍待完善
5. **可观测性与成本控制** — compaction 无限重试计费（#4663）、上下文窗口可见性（#1953）反映用户对透明度和费用控制的关切

---

## 6. 开发者关注点

**高频痛点汇总：**

- **1.0.81/82 回归集中爆发**：BYOK `/model` 命令（#4672）、OAuth 认证（#4671）、会话恢复（#4674/#4673）三道回归集中在相邻版本，建议用户评估是否回退至 1.0.80
- **MCP 服务端兼容性问题突出**：Python MCP SDK 2.0.0 dual-era runner 与现代 CLI 的初始化握手存在协议级别冲突（#4525）
- **ACP 模式生产可用性存疑**：无 bounded 启动超时（#4678）、无 session/close（#4113）、中断后延迟创建（#4668）三个问题叠加，不适合关键路径依赖
- **扩展/插件生命周期管理薄弱**：扩展进程异常退出后 tool 悬空（#4670）表明宿主对插件状态追踪不足
- **企业部署障碍**：TLS Inspecting 代理导致 OAuth 断流（#4671）影响大量企业用户，v1.0.83-0 的 mTLS 支持是正确方向，需验证实际效果

---

*报告生成时间：2026-09-01 | 分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报 — 2026-09-01

---

## 1. 今日速览

今日 Kimi Code CLI 社区无新版本发布，共更新 3 条 Issues 与 2 条 Pull Requests。一条关于 StrReplaceFile 工具边界条件的修复 PR 已提交，修复空字符串替换时的静默数据损坏问题；同时推进了 kimi-cli → Kimi Code 的弃用迁移流程开发。社区反馈的 Windows 平台 GBK 编码错误仍需官方跟进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 社区热点 Issues

### #1287 [CLOSED] — 任务执行中无法编写下一个任务的 prompt
- **类型**: enhancement | **作者**: XiaoPengYouCode
- **关注度**: 功能阻塞类问题，影响多步骤任务编排体验
- **状态**: 已关闭，社区反馈当前任务执行期间 prompt 输入字段被锁定
- **链接**: [MoonshotAI/kimi-cli Issue #1287](https://github.com/MoonshotAI/kimi-cli/issues/1287)

### #1292 [CLOSED] — Task 子任务调用时偶发卡死
- **类型**: bug | **作者**: Wolido
- **关注度**: 稳定性问题，涉及多子任务并发执行时的挂起风险
- **状态**: 已关闭，复现条件为特定子任务串行调用
- **链接**: [MoonshotAI/kimi-cli Issue #1292](https://github.com/MoonshotAI/kimi-cli/issues/1292)

### #2629 [OPEN] — Windows 平台 GBK 编码错误
- **类型**: bug | **作者**: tuies
- **关注度**: 中文 Windows 用户高频痛点，特殊 Unicode 字符导致程序崩溃
- **状态**: 未关闭，当前无评论，需官方确认
- **链接**: [MoonshotAI/kimi-cli Issue #2629](https://github.com/MoonshotAI/kimi-cli/issues/2629)

---

## 4. 重要 PR 进展

### #2631 — fix(file): 拒绝 StrReplaceFile 中的空 old 字符串
- **作者**: rootkiller6788
- **内容**: 修复 StrReplaceFile 工具在传入空 `old` 字符串时的异常行为——Python 的 `str.replace('')` 会在字符串首部或字符间插入 `new` 值并返回成功，导致静默数据损坏。本 PR 增加了前置校验，拒绝空 old 字符串的替换请求。
- **状态**: OPEN
- **链接**: [MoonshotAI/kimi-cli PR #2631](https://github.com/MoonshotAI/kimi-cli/pull/2631)

### #2630 — feat(shell): 弃用感知的更新流程与一键迁移
- **作者**: jackfish212
- **内容**: 作为 kimi-cli → Kimi Code 迁移计划的一部分，当 CDN 发布弃用/迁移通知时，CLI 会将当前 Python 版本标记为弃用，并通过一键引导流程帮助用户平滑迁移至 Kimi Code。
- **状态**: OPEN
- **链接**: [MoonshotAI/kimi-cli PR #2630](https://github.com/MoonshotAI/kimi-cli/pull/2630)

---

## 5. 功能需求趋势

从近期社区反馈中可观察到以下方向：

| 趋势方向 | 说明 |
|---------|------|
| **多任务编排增强** | Issue #1287 反映用户对链式任务中"边执行边准备"的需求，期望提升任务间衔接效率 |
| **执行稳定性** | Issue #1292 暴露多子任务串行调用时的挂起风险，社区对长任务链的健壮性有持续关切 |
| **跨平台兼容性** | Issue #2629 凸显 Windows (GBK) 编码问题，中文用户群体对跨平台字符处理关注度较高 |
| **产品迁移路径** | PR #2630 表明官方正在推进 kimi-cli → Kimi Code 的平滑迁移，社区对此更新路径较为关注 |

---

## 6. 开发者关注点

**高频痛点：**

1. **编码兼容性问题** — Windows GBK 环境下含特殊字符（如 Ł `/u0133`）的输出导致程序崩溃，是影响中文用户使用的关键缺陷。
2. **多步骤任务编排体验** — 用户希望在当前任务执行期间即可预写后续任务 prompt，减少等待与上下文切换成本。
3. **子任务执行稳定性** — Task 调用在并发/串行场景下偶发卡死，影响自动化工作流的可靠性。
4. **工具边界条件鲁棒性** — StrReplaceFile 等核心工具对异常输入（空字符串）缺乏防御，易引发静默数据错误。

**建议关注：**
- Issue #2629 尚未获得官方回应，建议跟进 Windows 编码修复进展
- PR #2630 迁移流程设计值得留意，将影响存量 kimi-cli 用户的使用路径

---

*数据来源：github.com/MoonshotAI/kimi-cli | 生成时间：2026-09-01*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报
**日期：2026-09-01**

---

## 1. 今日速览

Qwen Code 发布 v0.22.3-nightly 版本，重点更新 Web Shell Git 状态提示与 Review 流程。社区围绕跨会话通信、会话恢复机制与 llm.cpp 兼容性展开深度讨论，同时多个高价值 PR 集中在工作流可视化、MCP 工具调用与语音守护进程方向。

---

## 2. 版本发布

### v0.22.3-nightly.20260831.3a0c4c6108
- **Web Shell**: 在分支选择器动作旁展示 Git 状态提示，增强 Git 上下文可见性
- **Review**: 优化 Review 流程中的状态发出机制

---

## 3. 社区热点 Issues（精选 10 条）

| # | 主题 | 状态 | 评论 | 重要性 |
|---|------|------|------|--------|
| #8724 | Cross-session messaging：同机多会话通信 | CLOSED | 13 | **多 Agent 协作核心能力**，定义 `list_agents`/`send_message` 接口规范 |
| #10520 | toolSearch threshold 导致 llama.cpp 400 解析错误 | OPEN | 5 | **兼容性问题**，影响使用本地 llama.cpp + MCP 工具的用户 |
| #9450 | task_list 误触发重复工具调用检测 | CLOSED | 5 | **多 Agent 协作 Bug**，共享任务状态时产生假阳性循环检测 |
| #9281 | task_list 将空白可选过滤视为活跃过滤 | CLOSED | 5 | **工具行为偏差**，空值过滤导致查询结果异常 |
| #8535 | --resume 重建 dangling-unsigned-thought 隐患 | OPEN | 4 | **会话恢复安全性**，PR #8260 的修复未覆盖恢复路径 |
| #10530 | 0.22.3 中 400 Failed to initialize samplers | OPEN | 4 | **回归 Bug**，用户在 llama-server 中升级后首次报错 |
| #10640 | `Press ctrl+s to show more lines` 提示出现位置不当 | OPEN | 4 | **UI 体验**，提示在无更多行时仍显示 |
| #10654 | review run 信任锚位于模型会话写表面内 | OPEN | 2 | **安全架构**，CI 审查流程的权限隔离设计 |
| #10380 | Auto-compaction 在 HTTP 413 后无法恢复 | CLOSED | 3 | **长会话稳定性**，反向代理限制导致会话永久不可用 |
| #10187 | Managed Skill 重装可能在 rename 失败时删除现有安装 | CLOSED | 3 | **扩展管理 Bug**，原子性保证不足导致数据丢失风险 |

---

## 4. 重要 PR 进展（精选 10 条）

| # | 功能 | 作者 | 重点 |
|---|------|------|------|
| #10636 | IPC 跨会话 Inbox 认证 | qqqys | 为实验性跨会话消息通道增加 per-session token 认证 |
| #10594 | Web Shell 动态工作流可视化 | qqqys | 新增 Workflow Runs 页面，支持暂停/恢复/取消/重试 |
| #10612 | Web Shell 会话内容搜索 | wenshao | 侧边栏搜索扩展至对话内容匹配，展示命中片段 |
| #10589 | Web Shell Workspaces 总览面板 | wenshao | 全页表格展示所有注册工作区、活跃会话数、MCP 健康状态 |
| #10367 | qwen-live 独立语音守护进程 | LaZzyMan | 将 Live 语音能力抽离为独立包，支持 M1/M2 里程碑 |
| #9739 | 绑定通过 gh pr create 创建的 PR | wenshao | 关闭会话↔PR 绑定的最后一处来源缺口 |
| #10347 | 自动重试瞬态网络错误（EOF） | dev-bot | 将包装的网络错误分类为可重试传输错误 |
| #10575 | CI 短时间作业独立 ECS 队列 | wenshao | 将 8 个秒级作业迁移至 ecs-light 队列 |
| #9541 | 压缩请求准入控制 | AaronZ345 | 对共享缓存与冷压缩请求实施完整的请求准入校验 |
| #10263 | /cd 后重新加载项目运行时 | qqqys | 切换工作目录时事务化刷新设置、工具、MCP、Hook 等 |

---

## 5. 功能需求趋势

从 Issue 与 PR 动态中可归纳出以下社区关注方向：

1. **多 Agent 协作与跨会话通信**：#8724、#9450、#9281、#10636 反映社区对多会话消息传递、任务列表一致性的强烈需求
2. **Web Shell 体验升级**：工作流可视化（#10594）、会话搜索（#10612）、工作区总览（#10589）构成 B2 层 UI 完善方向
3. **本地模型兼容性**：llama.cpp 400 错误（#10520、#10530）与 grammar 解析问题持续影响用户
4. **扩展/技能管理**：原子化安装（#10187）、生命周期钩子（#9511）反映对扩展生态稳定性的关注
5. **语音能力独立化**：qwen-live 守护进程（#10367）表明将语音功能从 serve 中解耦为独立组件

---

## 6. 开发者关注点

- **会话恢复安全性**：`--resume`/`--continue` 路径未完全覆盖 PR #8260 的修复（#8535），开发者关注历史状态重建的一致性
- **HTTP 413 长会话恢复**：自动压缩在反向代理限制下进入不可恢复状态（#10380），影响生产环境稳定性
- **工具调用边界条件**：`task_list` 空值过滤（#9281）与重复检测（#9450）暴露了多 Agent 场景下的边界处理缺陷
- **CI/CD 稳定性**：ECS 队列隔离（#10575）与瞬态错误重试（#10347、#10572）显示社区对测试基础设施可靠性的关注
- **Web Shell 会话冲突**：归档运行中会话可能重建活跃 transcript（#9688），影响会话生命周期管理

---

*数据来源：github.com/QwenLM/qwen-code | 统计周期：2026-08-31 至 2026-09-01*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI 社区动态日报
**日期：2026-09-01**  
**仓库：** github.com/Hmbown/DeepSeek-TUI（CodeWhale）

---

## 1. 今日速览

2026-09-01 无新版本发布，但社区活跃度极高：过去 24 小时内处理了 10 个 Issues 和 37 个 PR。重点进展包括 **原生 ChatGPT/Codex 订阅登录功能**（PR #5784，解决无需 Codex CLI 的痛点）、**TUI 启动流程与 Composer UI 的视觉恢复**（PR #5753/#5758）、以及 **会话恢复（session resume）的核心修复**（PR #5750）。

---

## 2. 版本发布

无新版本发布。

---

## 3. 社区热点 Issues（Top 10）

| Issue | 状态 | 重要性说明 | 社区反应 |
|-------|------|-----------|---------|
| [#5316 EPIC-005: CodeWhale TUI Crate Decomposition](https://github.com/Hmbown/CodeWhale/issues/5316) | OPEN | 核心架构重构任务的汇总 EPIC，涉及 TUI crate 的结构拆分，影响长期可维护性 | 20 条评论，活跃讨论中 |
| [#5778 Native ChatGPT/Codex subscription sign-in](https://github.com/Hmbown/CodeWhale/issues/5778) | OPEN | 用户报告：连接 ChatGPT/Codex 订阅当前依赖 Codex CLI，社区强烈期望原生支持 | 1 条评论，需求明确 |
| [#5772 Make provider selection explicit](https://github.com/Hmbown/CodeWhale/issues/5772) | CLOSED | 解决 Picker 中 provider 选择权限不透明、外部凭据自动采用的安全隐患 | 1 条评论，已修复 |
| [#5755 Unify provider route authority](https://github.com/Hmbown/CodeWhale/issues/5755) | CLOSED | 解决 ProviderLake、Runtime RouteResolver、CLI registry 三方路由权威不一致问题 | 0 条评论，已修复 |
| [#5605 Flaky test: remote_control crashes](https://github.com/Hmbown/CodeWhale/issues/5605) | CLOSED | 修复并行测试负载下的不稳定性，影响 CI 可信度 | 3 条评论，已修复 |
| [#5713 fix(custom): wire="responses"\|"anthropic"](https://github.com/Hmbown/CodeWhale/issues/5713) | CLOSED | 自定义 provider 现支持 Responses/Anthropic 协议，不再强制走 ChatCompletions | 2 条评论，已修复 |
| [#5771 Active-session composer [↑] geometry](https://github.com/Hmbown/CodeWhale/issues/5771) | CLOSED | 统一编辑器提交按钮的鼠标命中区域，提升 UX 一致性 | 1 条评论，已修复 |
| [#5768 Compose Tideline shell as coherent TUI](https://github.com/Hmbown/CodeWhale/issues/5768) | CLOSED | 确保启动流程各切片能正确组装为完整可运行的 TUI | 0 条评论，已修复 |
| [#5775 Make Pod the canonical roster command](https://github.com/Hmbown/CodeWhale/issues/5775) | CLOSED | 统一 `fleet`/`pod` 等多重名词，降低学习成本 | 0 条评论，已修复 |
| [#5767 Fix public website auth links 404](https://github.com/Hmbown/CodeWhale/issues/5767) | CLOSED | 修复 `/signin`/`/signup` 等链接被重定向到 `/en/` 后的 404 | 0 条评论，已修复 |

---

## 4. 重要 PR 进展（Top 10）

| PR | 状态 | 功能/修复说明 |
|----|------|-------------|
| [#5784 feat(tui): native ChatGPT PKCE sign-in](https://github.com/Hmbown/CodeWhale/pull/5784) | OPEN | 通过浏览器 PKCE 流程实现原生登录，无需安装 Codex CLI，刷新令牌存入 Codewhale 本地存储 |
| [#5782 feat(compaction): publish survival contract](https://github.com/Hmbown/CodeWhale/pull/5782) | OPEN | 发布 compaction 契约文档，解决 #4394，明确上下文压缩的行为规范 |
| [#5749 feat(app-server): unix-socket transport](https://github.com/Hmbown/CodeWhale/pull/5749) | OPEN | 为 App-server 添加 Unix 套接字传输支持，实现 daemon/attach 发现机制，桌面端 Phase 0 基础 |
| [#5750 fix(session): engine adopts host session id](https://github.com/Hmbown/CodeWhale/pull/5750) | OPEN | **关键修复**：Engine 现采纳 Host 的 session id，解决恢复会话时新 turn 落入错误会话的根本问题 |
| [#5751 feat(protocol): Op/EventMsg parity + guard](https://github.com/Hmbown/CodeWhale/pull/5751) | OPEN | Rust 核心与 TS 表面层之间的 Op/EventMsg 对齐，通过编译时检查防止未来漂移 |
| [#5711 feat(runtime-api): rehydrate persisted goals](https://github.com/Hmbown/CodeWhale/pull/5711) | OPEN | 将持久化的目标记录重新注入 Engine，支持 `update_goal` 工具和 host 侧持续循环 |
| [#5742 chore: use public name Codewhale](https://github.com/Hmbown/CodeWhale/pull/5742) | OPEN | 将文档、TUI 本地化、CLI 帮助等所有用户可见文本统一为 "Codewhale" |
| [#5789 chore: drop co-author trailer gate](https://github.com/Hmbown/CodeWhale/pull/5789) | OPEN | 移除对 `Co-authored-by` trailer 的过严检查，避免工具自动生成的提交被拒绝 |
| [#5792 fix(engine): emergency recovery trims with hysteresis](https://github.com/Hmbown/CodeWhale/pull/5792) | OPEN | 修复长会话紧急恢复时每步都触发 compaction 的抖动问题，引入迟滞机制 |
| [#5788 fix(cli): label auth list rows by provider](https://github.com/Hmbown/CodeWhale/pull/5788) | CLOSED | 修复 `codewhale auth list` 中重复标签问题（siliconflow/modelstudio-token-plan 重复显示） |

---

## 5. 功能需求趋势

从本期 Issues 和 PR 中提炼出以下社区关注方向：

1. **多提供者统一与扩展**：社区持续推动 provider 选择标准化（#5755）、自定义 provider 协议支持（#5713/#5719），以及 ChatGPT/Codex 原生登录（#5778/#5784）。
2. **CLI 命令与体验优化**：统一 `pod`/`fleet` 命名（#5775）、修复 `auth list` 显示（#5788）、新增 Codewhale 账号机器令牌支持（#5721）。
3. **TUI 启动与界面**：多个 PR 聚焦 Tideline 启动壳、Composer 视觉封装、提交按钮 UX 的一致性（#5771/#5768/#5753/#5758）。
4. **会话恢复与持久化**：Engine 修复 session id 采纳问题（#5750）、目标持久化恢复（#5711）、紧急恢复稳定性（#5792）。
5. **架构重构**：CodeWhale TUI Crate 拆分（#5316）持续进行，协议层 Op/EventMsg 对齐（#5751）。

---

## 6. 开发者关注点

- **痛点 1：Codex CLI 依赖** — 用户反馈连接 ChatGPT/Codex 订阅必须安装 Codex CLI，社区强烈期望原生 PKCE 登录流程（#5778）。
- **痛点 2：会话恢复 Bug** — 恢复会话时新 turn 落入错误会话是已知高频问题（#5750），此次修复触及根因。
- **痛点 3：Provider 路由不一致** — 不同组件（Picker/Runtime/CLI）使用不同来源提供权威，导致体验混乱（#5755）。
- **痛点 4：CI 可靠性** — 不稳定的 flaky test（#5605）和 CI 检查误报（#5740）影响开发效率。
- **高频需求**：`pod` 命令统一、auth 列表修复、compaction 行为契约、协议层编译时保证。

---

**报告生成时间：** 2026-09-01  
**数据截止：** 过去 24 小时 GitHub 活动

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*