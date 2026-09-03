# AI CLI 工具社区动态日报 2026-09-03

> 生成时间: 2026-09-03 04:00 UTC | 覆盖工具: 10 个

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
**日期：2026-09-03**

---

## 1. 生态全景

2026年9月，AI CLI工具生态进入**稳定性攻坚期**与**架构重构期**并存的阶段。头部工具（Claude Code、OpenAI Codex、Gemini CLI、Copilot CLI）均在密集修复权限系统、内存泄漏、平台兼容性等核心问题，同时加速向企业级功能演进（多账号管理、MCP生态、Agent化部署）。开源项目（OpenCode、Qwen Code、DeepSeek TUI）则聚焦TUI架构升级与插件生态建设，形成与商业工具的差异化竞争。整体趋势显示：AI CLI正从"单次对话工具"向"可编排、可观测、多模型协同的开发者平台"演进。

---

## 2. 各工具活跃度对比

| 工具 | 新版本发布 | 今日Issues | 今日PR | 核心动态 |
|------|-----------|-----------|--------|---------|
| **Claude Code** | v2.1.259 | 10 | 4 | 新增`managedMcpServers`、`--permission-prompts none`；权限回归bug集中爆发 |
| **OpenAI Codex** | v0.153.0 | 10 | 10 | Vim撤销/重做；Agent command center接入；Windows daemon支持 |
| **Gemini CLI** | 无 | 9 | 9 | 夜间流水线失败；安全修复密集（4个P1合并）；gemini-3.8-flash注册 |
| **GitHub Copilot CLI** | v1.0.83-3 | 10 | 0 | 新增Claude Fable 5.1；Linux沙箱网络限制改进；MCP连接问题集中 |
| **Kimi Code CLI** | 无 | 5（全关闭） | 0 | 功能对齐类需求为主；社区贡献活跃 |
| **OpenCode** | v1.18.27 | 10 | 10 | 超时配置优化；Session Goal原生支持呼声高；轻量模型分层策略 |
| **Qwen Code** | live-host-v0.2.0 | 10 | 10 | OpenTUI迁移Batch 4；Web Shell安全加固；XML标签泄漏修复组 |
| **DeepSeek TUI** | 无（v0.9.12开发中） | 10 | 11 | 提供商中立性审计完成；per-session control socket；Memory命令系统 |
| **Grok Build** | 无 | 0 | 0 | 无活动 |

---

## 3. 共同关注的功能方向

| 功能方向 | 涉及工具 | 具体诉求 |
|---------|---------|---------|
| **权限系统完善** | Claude Code、OpenCode、Qwen Code | 权限误报/回归频繁；需要更精细的读写规则与hook机制；OpenCode推动权限断言API |
| **多模型/多账号管理** | Claude Code、Copilot CLI、OpenCode、DeepSeek TUI | 单会话切换模型（#3709）、移动端多账号（#36151）、BYOK本地端点支持、提供商中立性 |
| **MCP生态集成** | Claude Code、Copilot CLI、OpenCode、DeepSeek TUI | MCP服务器连接稳定性、OAuth Token缓存、工具继承问题集中爆发 |
| **Agent化与外部编排** | Gemini CLI、DeepSeek TUI、OpenCode | per-session control socket（JSON-RPC）、subagent状态可靠性、Fleet角色管理 |
| **Windows平台稳定性** | Claude Code、Codex、Copilot CLI | 启动失败、进程锁定、headless模式异常、Schannel证书问题 |
| **长会话性能/内存管理** | Copilot CLI、OpenCode、Gemini CLI | Node.js OOM崩溃、libuv句柄泄漏、V8堆溢出、resume场景内存回收 |
| **执行透明性** | Codex、OpenCode、Qwen Code | 命令执行可见性、退出码准确性、JSON输出完整性（CI/CD友好） |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|---------|---------|---------|
| **Claude Code** | 企业级功能（managedMcpServers）、权限系统、多平台适配 |  enterprises、Anthropic生态用户 | TypeScript/React；强调权限控制与MCP标准化 |
| **OpenAI Codex** | TUI体验（Vim模式）、Agent command center、会话恢复 | OpenAI订阅用户、开发者 | Rust CLI；注重交互细节与多模式切换 |
| **Gemini CLI** | 安全加固（变量注入修复）、模型迭代（3.8-flash）、沙箱化 | Google Cloud用户、安全敏感场景 | TypeScript；安全响应速度快，P1漏洞24h内修复 |
| **GitHub Copilot CLI** | MCP生态、自定义Agent、企业代理兼容 | GitHub生态用户、企业开发者 | Node.js；聚焦MCP协议兼容与企业代理环境 |
| **OpenCode** | 插件生态、Session Goal、多模型分层、浏览器集成 | 开源贡献者、LM Studio/Ollama用户 | Go + TypeScript；强调可扩展性与本地模型支持 |
| **Qwen Code** | TUI架构重构（OpenTUI迁移）、Web Shell安全、daemon化 | 中文用户、Qwen模型用户 | TypeScript；激进架构迁移，CI弹性优化 |
| **DeepSeek TUI** | 提供商中立性、插件系统、Memory/Skills命令、Agent编排 | 多模型用户、自动化场景 | Rust；代码架构治理（mega文件拆分）、插件市场建设 |
| **Kimi Code CLI** | 功能对齐、远程开发适配、交互体验 | Kimi用户、SSH远程开发者 | 功能迭代稳健，社区贡献活跃 |

---

## 5. 社区热度与成熟度

| 成熟度层级 | 工具 | 特征 |
|-----------|------|------|
| **高度成熟** | Claude Code、OpenAI Codex、Copilot CLI | 版本迭代规律；企业级功能密集；社区痛点集中在权限/稳定性/兼容性 |
| **快速迭代** | Gemini CLI、OpenCode、Qwen Code | PR合并速度快；安全修复响应迅速；架构重构进行中 |
| **生态构建期** | DeepSeek TUI | 插件市场、控制socket、提供商中立性等基础设施完善中；代码治理力度大 |
| **功能对齐期** | Kimi Code CLI | Issue多为功能增强请求；社区贡献主动；版本发布节奏稳定 |

**活跃度指标**：
- **最高PR产出**：DeepSeek TUI（11个）、OpenAI Codex（10个）、OpenCode（10个）、Qwen Code（10个）
- **最高Issue讨论**：Claude Code（#36151，676赞）、OpenCode（#6231，225赞）
- **最快安全响应**：Gemini CLI（4个P1漏洞24h内修复）

---

## 6. 值得关注的趋势信号

| 趋势信号 | 证据 | 开发者参考 |
|---------|------|-----------|
| **权限系统成为最大痛点** | Claude Code集中爆发5+权限回归bug；OpenCode推动权限断言API；Qwen Code修复XML标签泄漏 | 企业用户需关注权限配置审计；开发者应测试自定义规则与hook的兼容性 |
| **MCP生态进入成熟瓶颈期** | Copilot CLI 4个MCP相关Issue；Claude Code新增managedMcpServers；Gemini CLI修复变量注入绕过 | MCP服务器设计需考虑协议版本兼容、OAuth缓存、进程生命周期管理 |
| **Agent化部署成为新战场** | DeepSeek TUI per-session control socket；Gemini CLI subagent状态修复；OpenCode Session Goal | 自动化流水线集成需评估Agent可靠性、状态恢复、外部编排接口 |
| **本地模型支持需求爆发** | OpenCode #6231（225赞）自动发现模型；DeepSeek TUI #5820 Ollama预算问题；OpenCode轻量模型分层 | 本地部署用户需关注input budget计算、模型自动发现、超时配置 |
| **内存泄漏/OOM反复出现** | Copilot CLI #4664/#4686；OpenCode resume场景；Gemini CLI长会话挂起 | 长会话用户需关注版本升级；CI/CD集成需设置内存上限与超时熔断 |
| **Windows平台仍是重灾区** | Claude Code 3个Windows启动bug；Codex headless启动失败；Copilot TLS代理问题 | Windows用户需关注更新残留进程、权限模式回归、网络重连循环 |
| **架构重构提速** | Qwen Code OpenTUI迁移；DeepSeek TUI crate拆分；OpenCode浏览器插件集成 | 长期使用用户需适应TUI交互变化；贡献者需关注代码结构演进 |

---

**总结**：2026年9月的AI CLI生态呈现"**稳定性优先、架构重构、Agent化演进**"三大主线。企业用户应重点关注权限系统安全性与MCP兼容性；开发者需评估内存管理与长会话稳定性；开源项目正在通过插件生态与多提供商支持建立差异化优势。建议持续跟踪Claude Code权限回归修复、Gemini CLI安全响应机制、以及DeepSeek TUI的插件市场进展。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告
**数据截止：2026-09-03 | 分析师：Agnes-2.0-Flash**

---

## 1. 热门 Skills 排行

| 排名 | Skill | 功能 | 状态 | 链接 |
|------|-------|------|------|------|
| 1 | **skill-creator 评估工具修复** (#1298) | 修复 `run_eval.py` 始终报告 0% recall 的严重 bug，影响所有技能描述优化流程 | OPEN | [PR #1298](https://github.com/anthropics/skills/pull/1298) |
| 2 | **document-typography** (#514) | 检测 AI 生成文档中的孤立换行、寡妇段落、编号错位等排版问题 | OPEN | [PR #514](https://github.com/anthropics/skills/pull/514) |
| 3 | **scnet-hpc** (#1615) | 面向 SCNet HPC 集群的操作 Skill，支持 profile-based SSH + Slurm 工作流 | OPEN | [PR #1615](https://github.com/anthropics/skills/pull/1615) |
| 4 | **ODT Skill** (#486) | 支持 OpenDocument 格式（.odt/.ods）的创建、填充、读取和 HTML 转换 | OPEN | [PR #486](https://github.com/anthropics/skills/pull/486) |
| 5 | **frontend-design 改进** (#210) | 提升前端设计 Skill 的清晰度与可操作性，确保指令可在单次对话中执行 | OPEN | [PR #210](https://github.com/anthropics/skills/pull/210) |
| 6 | **skill-quality-analyzer** (#83) | 五维质量分析元 Skill：结构文档、逻辑一致性、触发准确率、边界覆盖、安全性 | OPEN | [PR #83](https://github.com/anthropics/skills/pull/83) |
| 7 | **self-audit** (#1367) | AI 输出交付前自动化审计：机械文件验证 + 四维推理质量门禁 | OPEN | [PR #1367](https://github.com/anthropics/skills/pull/1367) |
| 8 | **Hivemind 多智能体编排** (#1628) | 零成本多 Agent 协作：Claude 负责规划/审查，免费模型 worker 执行机械任务 | OPEN | [PR #1628](https://github.com/anthropics/skills/pull/1628) |

---

## 2. 社区需求趋势

从 Issues 讨论热度提炼四大核心方向：

**① 质量保障与治理（最热门）**
- Issue #492（43条评论）：社区 Skills 冒充官方 Anthropic 命名空间的信任边界安全问题引发高度关注
- Issue #412（6条评论）：Agent Governance Skill 提案——策略执行、威胁检测、信任评分、审计追踪
- Issue #1385（4条评论）：推理质量门禁流水线提案（预校准→对抗审查→交付验证）

**② 企业/组织级协作**
- Issue #228（16条评论，8个👍）：组织内 Skills 共享需求——当前只能手动下载/上传，缺乏共享库或直链

**③ 开发者工具链完善**
- Issue #556（12条评论，7个👍）：`run_eval.py` 触发机制 bug 严重影响技能开发体验
- Issue #189（6条评论，9个👍）：document-skills 与 example-skills 插件内容重复导致上下文污染
- Issue #1487（4条评论）：`claude-api` Skill 一次性注入 ~156k tokens 耗尽上下文窗口
- PR #723：testing-patterns Skill 提案，覆盖单元测试→React 组件测试→集成测试全栈

**④ 跨平台兼容性**
- PR #1099 / #1050：skill-creator 在 Windows 平台的 subprocess 和编码 bug 阻塞使用
- Issue #29：AWS Bedrock 集成需求

---

## 3. 高潜力待合并 Skills

以下 PR 讨论活跃或解决关键痛点，近期落地概率较高：

| PR | 方向 | 潜力理由 | 链接 |
|----|------|----------|------|
| **#1367** self-audit | 质量门禁 | 填补 Skill 交付前自检空白，与 Issue #1385 形成互补 | [PR #1367](https://github.com/anthropics/skills/pull/1367) |
| **#83** skill-quality-analyzer | 质量门禁 | 五维评分体系可直接嵌入 Skill 审核流程 | [PR #83](https://github.com/anthropics/skills/pull/83) |
| **#514** document-typography | 文档工程 | 排版问题是 AI 生成文档的普遍痛点，需求明确 | [PR #514](https://github.com/anthropics/skills/pull/514) |
| **#1628** Hivemind | 多 Agent 编排 | 解决"上下文成本"核心矛盾，符合降本趋势 | [PR #1628](https://github.com/anthropics/skills/pull/1628) |
| **#1298** skill-creator 修复 | 开发工具 | 修复阻塞技能优化的关键 bug，合并可释放开发效率 | [PR #1298](https://github.com/anthropics/skills/pull/1298) |
| **#723** testing-patterns | 测试工程 | 测试覆盖是开发者最高频需求之一 | [PR #723](https://github.com/anthropics/skills/pull/723) |

---

## 4. Skills 生态洞察

**当前社区最集中的诉求是：在扩展 Skills 覆盖面的同时，优先建立质量门禁体系与信任安全框架——社区对"如何确保 Skill 可靠可用"的关注已超越"需要更多 Skill"的需求。**

具体表现为：质量问题（eval 工具 bug、上下文注入失控、重复安装）和企业信任边界问题的讨论热度显著高于新功能请求，反映出生态正从快速扩张期进入质量治理期。

---



# Claude Code 社区动态日报 — 2026-09-03

## 1. 今日速览

Claude Code v2.1.259 正式发布，新增 `managedMcpServers` 企业级 MCP 服务器管理和 `--permission-prompts none` 无头模式支持。社区本周热点集中在 Windows 平台的稳定性问题（启动失败、更新残留、进程锁定）以及权限模式的新回归缺陷，多账号切换功能呼声持续高涨（676 赞）。

---

## 2. 版本发布

### v2.1.259（2026-09-03）

| 更新项 | 说明 |
|--------|------|
| `managedMcpServers` 设置 | 组织可向所有用户推送 HTTP/SSE MCP 服务器配置（与 `.mcp.json` 结构一致），包含命令的条目将被跳过 |
| `--permission-prompts none` | 新增无干预模式标志，适用于无人值守的 headless 主机，自动跳过所有权限提示 |

---

## 3. 社区热点 Issues（Top 10）

### 🔥 #36151 — 移动端多账号切换（无共享邮箱）
- **作者**: CorneAussems | **评论**: 169 | **👍**: 676
- **状态**: OPEN | **标签**: invalid, area:auth
- **摘要**: 用户强烈要求在 Claude Mobile 应用中支持多账号切换，无需共享邮箱。此为社区呼声最高的功能需求，持续活跃近6个月。
- [链接](https://github.com/anthropics/claude-code/issues/36151)

### 🪟 #85891 — Windows 桌面窗口始终置顶
- **作者**: kylealty-boop | **评论**: 65 | **👍**: 145
- **状态**: OPEN | **标签**: invalid, BUG
- **摘要**: Windows 11 上 Claude Desktop 窗口强制保持置顶，无内置设置可关闭，严重影响多窗口工作流。
- [链接](https://github.com/anthropics/claude-code/issues/85891)

### 💥 #53247 — Windows 启动失败：孤立 Silo/Job Object
- **作者**: rnpacheco25-sudo | **评论**: 51 | **👍**: 22
- **状态**: OPEN | **标签**: bug, platform:windows
- **摘要**: 应用崩溃后留下孤立的 Windows Job Object，导致无法重新启动，仅注销或重启可恢复（HRESULT 0x80070020）。
- [链接](https://github.com/anthropics/claude-code/issues/53247)

### 💥 #85199 — Windows 反复崩溃需手动修复
- **作者**: romers352 | **评论**: 50 | **👍**: 10
- **状态**: OPEN | **标签**: bug
- **摘要**: Claude Desktop 在 Windows 上频繁崩溃，用户需反复通过"高级选项→修复"才能恢复运行。
- [链接](https://github.com/anthropics/claude-code/issues/85199)

### 🔐 #91683 — 2.1.259 权限模式回归：bypassPermissions 仍提示
- **作者**: TalkingMonkeyOz | **评论**: 1 | **👍**: 0
- **状态**: OPEN | **标签**: bug, has repro, platform:windows, regression
- **摘要**: **今日新增**。v2.1.259 引入回归：配置了 `Read()` 拒绝规则后，`bypassPermissions` 模式下 `cd DIR && grep ...` 仍会弹出权限提示，2.1.258 无此问题。
- [链接](https://github.com/anthropics/claude-code/issues/91683)

### 🔐 #91650 — cd-compound-read guard 误报
- **作者**: railapex | **评论**: 1 | **👍**: 9
- **状态**: OPEN | **标签**: bug, has repro, platform:windows
- **摘要**: **近日本周新增**。当存在 `Read()` 拒绝规则时，绝对路径的 `cd` 命令也会触发权限提示，影响 2.1.257–2.1.259 多个版本。
- [链接](https://github.com/anthropics/claude-code/issues/91650)

### 🔐 #89251 — 权限模式系统提示绕过 PreToolUse Hooks
- **作者**: fvadicamo | **评论**: 4 | **👍**: 1
- **状态**: OPEN | **标签**: bug, area:security, area:hooks
- **摘要**: 权限模式的系统提示指示模型通过 Bash 工具编辑文件，从而绕过了 Write/Edit/NotebookEdit 的 PreToolUse hooks，存在安全盲区。
- [链接](https://github.com/anthropics/claude-code/issues/89251)

### 🌐 #76248 — Cowork 会话 git proxy 阻止所有推送
- **作者**: Loneplanet117 | **评论**: 32 | **👍**: 12
- **状态**: OPEN | **标签**: bug, has repro
- **摘要**: 2026年7月中旬起，Cowork 远程会话无法推送到非授权仓库，即使提供自有 fine-grained PAT 也无效，疑似 CCR_TEST_GITPROXY 灰度推送导致。
- [链接](https://github.com/anthropics/claude-code/issues/76248)

### 🤖 #63819 — claude-opus-4-8 持续不可用阻断 Auto 模式
- **作者**: syk82 | **评论**: 19 | **👍**: 27
- **状态**: OPEN | **标签**: bug, duplicate
- **摘要**: Auto 模式下分类器（claude-opus-4-8）反复报不可用，导致 Bash/Write/Edit 全部被阻断，仅能使用 Read。
- [链接](https://github.com/anthropics/claude-code/issues/63819)

### 📄 #89911 — Agent View 继承权限模式被静默降级
- **作者**: corneliusroemer-agent | **评论**: 5 | **👍**: 0
- **状态**: OPEN | **标签**: bug, has repro, platform:linux, regression
- **摘要**: 从 Agent View 派生的会话权限模式被服务器强制降级为 `defaultMode`， `/fork` 等行为非预期。
- [链接](https://github.com/anthropics/claude-code/issues/89911)

---

## 4. 重要 PR 进展

### #41938 [CLOSED] — Linux/macOS DevContainer 启动脚本
- **作者**: Broccoliux
- **内容**: 新增兼容 Linux/macOS 的 Bash 启动脚本，填补此前仅支持 Windows PowerShell 的空白，提升跨平台 DevContainer 体验。
- [链接](https://github.com/anthropics/claude-code/pull/41938)

### #87079 [OPEN] — 修复 `**` glob 零深度匹配缺陷
- **作者**: anishsamant
- **内容**: 修复安全规则中 `**` glob 模式无法匹配零深度路径的问题（底层的 `fnmatch` 将裸 `*` 错误地跨 `/` 匹配），导致顶层文件被安全规则静默排除。
- [链接](https://github.com/anthropics/claude-code/pull/87079)

### #61691 [OPEN] — GitHub Connector 诊断/修复脚本
- **作者**: giruuuuj
- **内容**: 为 Windows 用户新增 PowerShell 诊断脚本，修复 Cowork 中 GitHub MCP 连接器显示"已连接"但暴露零工具的顽疾（关联 #61682、#28695 等）。
- [链接](https://github.com/anthropics/claude-code/pull/61691)

### #86537 [OPEN] — 修复 CHANGELOG.md 重复词
- **作者**: genesisdayabl-droid
- **内容**: 修复 CLAUDE_BASH_NO_LOGIN 版本条目中"to to"的重复拼写错误（纯文档修复）。
- [链接](https://github.com/anthropics/claude-code/pull/86537)

---

## 5. 功能需求趋势

| 趋势方向 | 相关 Issues | 热度 |
|----------|------------|------|
| **多账号/身份管理** | #36151, #73582 | ⭐⭐⭐⭐⭐ |
| **权限系统完善** | #91683, #91650, #89251, #89911, #91296 | ⭐⭐⭐⭐⭐ |
| **Windows 平台稳定性** | #85891, #53247, #85199, #89680, #78873 | ⭐⭐⭐⭐ |
| **Cowork/远程会话** | #76248, #49655 | ⭐⭐⭐ |
| **模型可用性/性能** | #63819 | ⭐⭐⭐ |
| **IDE 集成体验** | #76440（跨会话关联） | ⭐⭐ |

**核心趋势**：权限系统成为当前最大痛点，近一周涌入多个 regression bug；Windows 平台的更新/启动问题持续高发；多账号管理诉求强烈且长期未获响应。

---

## 6. 开发者关注点

### 🔴 高频痛点
1. **Windows 更新残留进程锁定 AppX 容器**：多次更新后出现孤立进程，新版本的 `.exe` 无法启动，必须手动重启（#53247, #89680, #78873）
2. **权限模式绕过安全 Hooks**：bypassPermissions 下模型被指示走 Bash 执行文件写入，完全绕开 PreToolUse hook 机制（#89251）
3. **2.1.259 权限回归**：`cd` 复合命令触发误报权限提示，影响已有拒绝规则的用户（#91683, #91650）
4. **Cowork git proxy 灰度变更**：远程会话推送能力被静默限制，影响团队协作工作流（#76248）

### 🟡 中长期诉求
- 移动端多账号切换（#36151，676 赞，持续近半年）
- API 凭据加密存储（#73582，替代明文保存）
- 状态行暴露按模型周配额（#73770）
- Claude Code 会话与 claude.ai 网页会话交叉引用（#76440）

### 🟢 文档/工具链
- 插件安全指南文档过时（#89728）、subagent `effort` 字段有实现但无文档（#91415）、hooks 示例在含空格路径下失效（#88188）

---

*数据截止时间：2026-09-03 | 数据来源：github.com/anthropics/claude-code*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-09-03**

---

## 1. 今日速览

Rust CLI 发布 v0.153.0 正式版，Vim 模式新增撤销/重做功能，插件 CLI 能力增强。Windows 桌面应用出现多起启动异常（headless 模式、闪屏、网络连接循环），社区高度关注会话恢复、命令显示透明度及 Pro 配额消耗问题。

---

## 2. 版本发布

### rust-v0.153.0（正式版）

**主要更新：**
- **Vim 模式增强**：支持 `u` 撤销和 `Ctrl+R` 重做，完整保留草稿内容（包括粘贴内容和附件）— [#41941](https://github.com/openai/codex/pull/41941), [#42140](https://github.com/openai/codex/pull/42140)
- **插件 CLI 扩展**：支持列出、安装和远程管理插件

---

## 3. 社区热点 Issues

| Issue | 关注点 | 评论/👍 | 重要性 |
|-------|--------|---------|--------|
| [#39903](https://github.com/openai/codex/issues/39903) | 禁用"Ran N commands"折叠，始终显示已执行命令 | 59 / 79 | 🔥 极高 — 执行透明度是开发者核心需求 |
| [#25828](https://github.com/openai/codex/issues/25828) | 手机验证码无法发送到任意号码（印尼用户） | 32 / 5 | ⚠️ 高 — 影响国际用户认证 |
| [#41622](https://github.com/openai/codex/issues/41622) | 添加配置项禁用自动会话摘要 | 15 / 41 | 🔥 高 — 减少冗余信息干扰 |
| [#40219](https://github.com/openai/codex/issues/40219) | macOS 已删除会话在 Recents 中重新出现且无法删除 | 15 / 14 | 高 — 数据一致性 bug |
| [#41540](https://github.com/openai/codex/issues/41540) | Windows headless 启动因 node_repl.exe 重定位失败 | 15 / 1 | ⚠️ 高 — 阻塞 Windows 用户使用 |
| [#39823](https://github.com/openai/codex/issues/39823) | 会话恢复报错 "already has an active writer" | 13 / 2 | 高 — 影响多模式切换场景 |
| [#31017](https://github.com/openai/codex/issues/31017) | Codex 无法访问 gh（GitHub CLI） | 10 / 12 | 高 — 集成开发者工作流受阻 |
| [#41541](https://github.com/openai/codex/issues/41541) | 0.150 版本处理高推理负载时配额快速耗尽 | 8 / 0 | ⚠️ 高 — 直接影响付费用户体验 |
| [#24224](https://github.com/openai/codex/issues/24224) | 并发会话泄漏工作区根目录上下文 | 8 / 4 | 中 — 多项目场景稳定性问题 |
| [#41969](https://github.com/openai/codex/issues/41969) | Pro Lite 周配额突然耗尽，banked reset 消失 | 6 / 0 | 中 — 配额计量异常 |

---

## 4. 重要 PR 进展

| PR | 内容 | 状态 |
|----|------|------|
| [#42432](https://github.com/openai/codex/pull/42432) | Box the TUI resume picker future，优化异步选择器内存管理 | ✅ Closed |
| [#42428](https://github.com/openai/codex/pull/42428) | Agent command center 接入共享 composer，支持多行编辑、Vim 模式、粘贴处理 | ✅ Closed |
| [#42425](https://github.com/openai/codex/pull/42425) | TUI 从服务器动态发现实验性功能，支持加载/空/失败状态 | ✅ Closed |
| [#42422](https://github.com/openai/codex/pull/42422) | Guardian computer-use 评分遵循模型要求，支持实时模型切换场景 | ✅ Closed |
| [#42419](https://github.com/openai/codex/pull/42419) | Agent command center 新增会话恢复入口（默认 Ctrl+O） | ✅ Closed |
| [#42417](https://github.com/openai/codex/pull/42417) | 暴露 managed application 网络要求，支持精确域名白/黑名单 | ✅ Closed |
| [#42413](https://github.com/openai/codex/pull/42413) | 启用 MCP OAuth 协调刷新，支持 streamable HTTP 连接凭证持久化 | ✅ Closed |
| [#42410](https://github.com/openai/codex/pull/42410) | 允许查看并继续 misalignment 暂停的对话，支持审查策略发现 | ✅ Closed |
| [#42408](https://github.com/openai/codex/pull/42408) | 加固 embedded composer 输入处理，保留特殊字符前缀和 Vim 模式状态 | ✅ Closed |
| [#42405](https://github.com/openai/codex/pull/42405) | Windows 支持 app-server daemon，实现跨会话后台服务共享 | ✅ Closed |

---

## 5. 功能需求趋势

从本期 Issues 和 PR 可归纳出五大趋势：

1. **TUI/CLI 体验精细化** — Vim 模式完善、会话恢复入口、命令显示控制、实验性功能发现
2. **Windows 平台稳定性** — Daemon 支持、headless 启动修复、网络重连优化
3. **认证与权限管理** — MCP OAuth 刷新、gh CLI 集成、managed 网络策略、misalignment 策略审查
4. **配额与性能透明化** — 高推理负载下的配额消耗优化、background backfill 请求抑制
5. **跨平台协作** — Mobile Remote 同步、跨主机接力（handoff）、多会话上下文隔离

---

## 6. 开发者关注点

- **执行可见性**：大量开发者希望完整查看已执行命令而非折叠摘要，以提升调试效率（[#39903](https://github.com/openai/codex/issues/39903)）
- **会话恢复可靠性**：`--not-so-yolo` / `--approve-for-me` 模式切换后恢复失败是高频痛点（[#39823](https://github.com/openai/codex/issues/39823)）
- **Windows 启动障碍**：Store 自动更新后 headless 启动、闪屏、Schannel 证书验证失败导致无限重连循环（[#41540](https://github.com/openai/codex/issues/41540)、[#41275](https://github.com/openai/codex/issues/41275)、[#34351](https://github.com/openai/codex/issues/34351)）
- **配额消耗异常**：0.150 版本推理吞吐量提升后 Pro 周配额快速耗尽，缺乏透明度（[#41541](https://github.com/openai/codex/issues/41541)、[#41969](https://github.com/openai/codex/issues/41969)）
- **工具链集成**：gh CLI 认证状态不同步、MCP 插件启动时被跳过影响工作流（[#31017](https://github.com/openai/codex/issues/31017)、[#42406](https://github.com/openai/codex/pull/42406)）
- **多会话隔离**：并发会话上下文泄漏导致跨项目干扰（[#24224](https://github.com/openai/codex/issues/24224)）

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报
**日期：2026-09-03**  
**数据源：github.com/google-gemini/gemini-cli**

---

## 1. 今日速览

Gemini CLI 夜间自动发布流水线失败，目前未发布新版本。社区层面，Agent 可靠性问题持续占据热点，包括 subagent 状态误报、generalist agent 挂起以及浏览器代理在 Wayland 环境下的兼容性问题。安全方向动作频繁，多个变量注入绕过漏洞被修复，依赖 CVE 升级同步推进。

---

## 2. 版本发布

过去 24 小时内 **无新版本发布**。

> ⚠️ 夜间流水线失败跟踪：[Issue #29174](https://github.com/google-gemini/gemini-cli/issues/29174)

---

## 3. 社区热点 Issues

| # | 标题 | 评论/👍 | 重要性 |
|---|------|---------|--------|
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent 达到 MAX_TURNS 后被错误报告为 GOAL 成功，隐藏了中断信号 | 13 / 2 | P1 bug，subagent 状态机存在误导性的终止报告 |
| [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) | Generalist agent 无限挂起 | 8 / 8 | P1 bug，高社区支持度，文件夹创建等简单操作也会卡死 |
| [#19873](https://github.com/google-gemini/gemini-cli/issues/19873) | 通过零依赖 OS 沙箱利用模型的 bash 亲和力 | 9 / 1 | 长期活跃的功能增强提案，涉及安全沙箱化架构 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | 评估 AST-aware 文件读取/搜索/映射的价值 | 7 / 1 | 性能优化方向，目标减少 token 浪费和误读 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Gemini 未能主动使用自定义 skills 和 subagents | 6 / 0 | 用户体验痛点，模型对用户定义的工具链识别不足 |
| [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) | 为 Auto Memory 添加确定性脱敏并减少日志泄露 | 5 / 0 | P2 安全，背景提取 agent 在内容进入模型上下文后才脱敏 |
| [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) | Shell 命令执行完成后仍卡在"Awaiting user input" | 4 / 3 | P1 bug，简单命令（如 `ls`）也会复现 |
| [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) | Browser subagent 在 Wayland 环境下失败 | 4 / 1 | Linux 用户兼容性问题，终端显示 GOAL 但实际失败 |
| [#22267](https://github.com/google-gemini/gemini-cli/issues/22267) | Browser Agent 忽略 settings.json 中的配置覆盖 | 3 / 0 | 配置失效 bug，`maxTurns` 等参数被无视 |
| [#22672](https://github.com/google-gemini/gemini-cli/issues/22672) | Agent 应阻止/抑制破坏性行为 | 3 / 1 | 安全增强，建议模型在 git reset --force 等操作中主动规避 |

---

## 4. 重要 PR 进展

### 安全修复（P1 / Critical）

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| [#28902](https://github.com/google-gemini/gemini-cli/pull/28902) | 阻止 `$VAR` 和 `${VAR}` 变量注入绕过 | ✅ 已合并 | 修复 `detectBashSubstitution()` 不完整检查，防御 GHSA-wpqr-6v78-jr5g |
| [#29094](https://github.com/google-gemini/gemini-cli/pull/29094) | 升级 `simple-git` 至 3.32.3 修复 CVE-2026-28292 | 🔄 进行中 | 修复 Critical 级 Git 绕过漏洞 |
| [#29095](https://github.com/google-gemini/gemini-cli/pull/29095) | 升级 `shell-quote` 至 1.8.4 修复 CVE-2026-9277 | 🔄 进行中 | 修复 Critical 级 Shell 注入漏洞 |
| [#29115](https://github.com/google-gemini/gemini-cli/pull/29115) | 系统级配置文件强制权限与所有权检查 | 🔄 进行中 | Windows/POSIX 双重验证 ACL |
| [#29170](https://github.com/google-gemini/gemini-cli/pull/29170) | 增强工作区路径边界检查和符号链接解析 | 🔄 进行中 | 防止命令逃逸和路径遍历 |
| [#29116](https://github.com/google-gemini/gemini-cli/pull/29116) | 缓解 NTFS 8.3 短名称路径漏洞 | 🔄 进行中 | 处理 `git~1`、`vscode~1` 等短路径规避 |
| [#29171](https://github.com/google-gemini/gemini-cli/pull/29171) | macOS Seatbelt 沙箱隔离临时目录 | 🔄 进行中 | 防止沙箱内进程共享宿主机 tmp |

### 功能与稳定性修复

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| [#29172](https://github.com/google-gemini/gemini-cli/pull/29172) | 新增 `gemini-3.8-flash` 作为默认 flash 模型 | 🔄 进行中 | 注册 3.5/3.6/3.7/3.8-flash 全系列 |
| [#28914](https://github.com/google-gemini/gemini-cli/pull/28914) | 修复重试 nudge 注入以保留前缀缓存 | ✅ 已合并 | 将 nudge 从 `systemInstruction` 移至 `contents` 末尾 |
| [#29098](https://github.com/google-gemini/gemini-cli/pull/29098) | 保持 `useInputHistoryStore` 状态更新器纯净 | 🔄 进行中 | 修复 React 状态更新器非纯函数导致的副作用 |
| [#28917](https://github.com/google-gemini/gemini-cli/pull/28917) | Whisper 模型原子下载与失败清理 | ✅ 已合并 | 临时文件写入、压力控制、失败回滚 |

---

## 5. 功能需求趋势

| 趋势方向 | 关键 Issue / PR | 社区声音 |
|----------|----------------|----------|
| **Agent 可靠性** | #22323, #21409, #25166, #22267 | 模型挂起、状态误报、配置失效是高频痛点 |
| **安全加固** | #28902, #29094, #29095, #29115, #29170 | 变量注入、依赖 CVE、路径穿越并行修复中 |
| **性能与 Token 优化** | #22745, #22746, #19561 | AST-aware 工具链、节俭式文件读取持续推进 |
| **平台兼容性** | #21983 (Wayland), #29116 (NTFS) | Linux Wayland、Windows NTFS 安全边界问题浮现 |
| **新模型支持** | #29172 | gemini-3.8-flash 系列已注册，默认模型迭代中 |
| **Subagent 可见性** | #21763, #22598 | Bugreport 缺少 subagent 上下文，轨迹分享功能待完善 |
| **记忆系统改进** | #26525, #26523, #26522 | Auto Memory 的脱敏、无效 patch 处理、低信号会话重试均有优化空间 |

---

## 6. 开发者关注点

**高频痛点：**

1. **Subagent 行为不可预测**：模型频繁不调用自定义 skills（#21968），或调用后状态报告错误（#22323）
2. **命令执行卡死**：Shell 命令完成后 UI 仍显示 "Awaiting input"（#25166），generalist agent 无限挂起（#21409）
3. **临时文件污染工作区**：模型在随机目录创建 tmp 脚本，增加清理负担（#23571）
4. **浏览器代理不稳定**：Wayland 环境下完全失败（#21983），settings.json 覆盖被忽略（#22267）
5. **破坏性行为缺乏抑制**：`git reset --force` 等操作未被模型主动规避（#22672）

**积极信号：**
- 安全补丁响应迅速，多个 P1 级漏洞已在 24 小时内合并修复
- gemini-3.8-flash 模型支持已进入 PR 阶段，默认 flash 模型将升级
- Whisper 本地语音功能的稳定性修复（原子下载、stdout 缓冲）已合并

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-09-03** | 数据来源：github.com/github/copilot-cli

---

## 1. 今日速览

今日 Copilot CLI 发布 v1.0.83-3 热修复版本，新增 Claude Fable 5.1 模型支持，并改进 Linux 沙箱网络代理限制。社区焦点集中在 MCP 服务器连接稳定性、自定义 Agent 工具链集成、以及长会话内存泄漏等核心体验问题上。

---

## 2. 版本发布

### v1.0.83-3（最近发布）
- **新增**：自定义 Agent 支持在 `model` 字段配置多个候选模型，按顺序尝试直至可用；新增 `model-policy: required` 保持模型列表锁定
- **新增**：Claude Fable 5.1 模型支持
- **改进**：Linux 沙箱将网络出站流量限制为配置的代理；修复代理相关连接问题

> 链接：https://github.com/github/copilot-cli/releases/tag/v1.0.83-3

---

## 3. 社区热点 Issues

| # | 主题 | 亮点 | 链接 |
|---|------|------|------|
| #3709 | 允许 `/model` 在同一会话中切换多个模型（含 BYOK/本地） | 29 👍，BYOK 用户核心诉求 | [Issue #3709](https://github.com/github/copilot-cli/issues/3709) |
| #3074 | 新增 `/effort` 命令快速切换推理力度 | 9 👍，已关闭 | [Issue #3074](https://github.com/github/copilot-cli/issues/3074) |
| #4438 | `disable-model-invocation: true` 导致 Skill 完全不可达 | 6 👍，Agent 配置缺陷 | [Issue #4438](https://github.com/github/copilot-cli/issues/4438) |
| #2861 | 手动 `/compact` 连续失败：模型返回空响应 | 4 👍，会话压缩稳定性 | [Issue #2861](https://github.com/github/copilot-cli/issues/2861) |
| #2630 | 自定义 Agent 的 MCP 工具在子 Agent 中不连接 | 9 评论，Agent 生态关键 bug | [Issue #2630](https://github.com/github/copilot-cli/issues/2630) |
| #4664 | 恢复长会话时 JavaScript 堆内存溢出崩溃 | 近期高频问题，OOM 反复出现 | [Issue #4664](https://github.com/github/copilot-cli/issues/4664) |
| #4525 | 1.0.81-1 发送旧版 `initialize` 导致 MCP 初始化失败 | MCP 协议兼容性问题 | [Issue #4525](https://github.com/github/copilot-cli/issues/4525) |
| #4695 | MCP OAuth Token 跨会话缓存键重复，导致频繁重认证 | 新提交，直接关联用户体验 | [Issue #4695](https://github.com/github/copilot-cli/issues/4695) |
| #4686 | Node.js OOM 崩溃：31,965 个泄漏的 libuv 异步句柄 | 确定性内存泄漏，影响生产环境 | [Issue #4686](https://github.com/github/copilot-cli/issues/4686) |
| #4224 | 子 Agent 调用的 OTel Span 缺失计费属性，导致成本核算偏低 | 企业用户付费透明度痛点 | [Issue #4224](https://github.com/github/copilot-cli/issues/4224) |

---

## 4. 重要 PR 进展

**今日无新 PR 更新。**

---

## 5. 功能需求趋势

从今日 Issues 可提炼出以下社区关注方向：

1. **多模型灵活管理** — 用户希望在单会话内自由切换模型（包括本地 BYOK 端点），而非进程级锁定
   - #3709、#4275、#4703

2. **MCP 生态稳定性** — MCP 服务器连接、协议版本兼容、OAuth 缓存、进程生命周期管理是当前最集中反馈区
   - #2630、#4525、#4695、#4598、#4697

3. **自定义 Agent 与 Skill 体系** — Agent 插件发现、工具继承、权限控制存在多项回归缺陷
   - #4655、#4438、#4674

4. **长会话性能与内存管理** — OOM 崩溃和内存泄漏问题反复出现，尤其在 `--resume` 场景
   - #4664、#4686、#4699

5. **企业可观测性与计费** — OpenTelemetry 跨代理调用缺乏计费标签，影响成本追踪
   - #4224

---

## 6. 开发者关注点

| 痛点 | 涉及 Issue | 说明 |
|------|-----------|------|
| **MCP 服务器连接不稳定** | #2630、#4525、#4695、#4598 | 连接失败、协议版本混用、Token 缓存键异常、进程未清理叠加出现 |
| **内存泄漏导致 OOM** | #4664、#4686、#4699 | 不同场景（resume、长时间运行）均触发 V8 堆溢出，需系统性修复 |
| **Agent 配置行为与预期不符** | #4438、#4674、#4665 | `disable-model-invocation`、Agent 恢复、`sessionStart` 上下文重复注入 |
| **企业代理环境兼容** | #4671、#4683 | TLS 代理后 OAuth 失败、Windows ConstrainedLanguage 模式误报错误 |
| **成本透明度缺失** | #4224 | 子 Agent 调用不传递计费属性，无法准确核算 AI 消耗 |
| **Windows 路径与显示问题** | #4702、#4701 | 路径分隔符去重失败导致重复加载、工具审批预览截断路径 |

---

**总结**：今日社区动态以稳定性修复为主，v1.0.83-3 针对代理和网络限制作出改进。但 MCP 连接可靠性、内存泄漏、Agent 生命周期管理仍是三大核心攻坚方向，建议开发者关注后续版本对这些问题的响应。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报 | 2026-09-03

## 1. 今日速览

今日 Kimi CLI 仓库无新版本发布，也无新增 PR。过去 24 小时内有 5 个 Issues 关闭，主要集中在功能增强类需求，包括 undo 支持、Mermaid 内联渲染、`--agent-file` 参数一致性等。SSH 远程交互问题获得社区关注（1 点赞）。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 社区热点 Issues

### #1307 [CLOSED] `--agent-file` 支持扩展至 `kimi web`
**作者:** Krivodel | 创建: 2026-03-03 | 更新: 2026-09-03 | 👍 3 | 💬 0
> **摘要:** `kimi` 子命令已支持 `--agent-file`，但 `kimi web` 始终加载默认 agent，缺乏一致性。作者已自行实现该功能。
**链接:** [Issue #1307](https://github.com/MoonshotAI/kimi-cli/issues/1307)
**关注原因:** 最高赞 Issue，体现开发者对 CLI 命令参数一致性的高度关注，且已有社区贡献者主动实现方案。

---

### #1293 [CLOSED] SSH 远程环境下 Kimi CLI 无法通信
**作者:** cshennju | 创建: 2026-03-01 | 更新: 2026-09-03 | 👍 1 | 💬 1
> **摘要:** 在远程 SSH 服务器（无图形界面、无法修改系统 DNS）上使用 Kimi CLI 时出现通信问题。
**链接:** [Issue #1293](https://github.com/MoonshotAI/kimi-cli/issues/1293)
**关注原因:** SSH 远程开发场景日益普遍，该问题涉及网络连通性与环境适配，具有广泛代表性。

---

### #1311 [CLOSED] 希望增加 Undo 功能
**作者:** lasting-yang | 创建: 2026-03-03 | 更新: 2026-09-03 | 👍 1 | 💬 0
> **摘要:** 参考 OpenCode 的 undo 功能，建议为 Kimi CLI 添加撤销操作支持。
**链接:** [Issue #1311](https://github.com/MoonshotAI/kimi-cli/issues/1311)
**关注原因:** 核心交互体验需求，直接影响用户使用信心与容错能力。

---

### #1310 [CLOSED] WebUI 内联渲染 Mermaid 图表
**作者:** chriswingler | 创建: 2026-03-03 | 更新: 2026-09-03 | 👍 1 | 💬 0
> **摘要:** 建议 WebUI 中内联显示 Mermaid 生成的图表（类似 OpenCode 的效果）。代码解析逻辑已存在。
**链接:** [Issue #1310](https://github.com/MoonshotAI/kimi-cli/issues/1310)
**关注原因:** 可视化输出是提升交互体验的重要方向，且实现成本相对较低。

---

### #1309 [CLOSED] 可选的 Openclaw 风格功能
**作者:** chriswingler | 创建: 2026-03-03 | 更新: 2026-09-03 | 👍 0 | 💬 0
> **摘要:** 建议增加心跳系统、定时任务（cron jobs）、记忆功能，或与 nanobot 集成。
**链接:** [Issue #1309](https://github.com/MoonshotAI/kimi-cli/issues/1309)
**关注原因:** 反映社区对 Kimi CLI 向更强自动化能力演进的期待。

---

## 4. 重要 PR 进展

今日无新增 PR。

---

## 5. 功能需求趋势

根据今日 Issues 分析，社区关注方向集中在：

| 方向 | 涉及 Issue | 热度 |
|------|-----------|------|
| **CLI 一致性 & 参数对齐** | #1307 | ⭐⭐⭐ |
| **交互式体验增强**（undo、可视化） | #1311, #1310 | ⭐⭐ |
| **远程/容器环境适配** | #1293 | ⭐⭐ |
| **自动化 & 长期任务能力** | #1309 | ⭐ |

---

## 6. 开发者关注点

- **功能对齐:** 开发者期望 Kimi CLI 与同类工具（OpenCode、Openclaw）保持功能一致，尤其在 undo、agent 文件加载等核心交互上。
- **远程开发支持:** SSH 场景下的通信稳定性是需要持续优化的方向，尤其是无 GUI、受限 DNS 的网络环境。
- **可视化输出:** Mermaid 图表内联渲染是轻量级高价值的体验提升点。
- **社区贡献活跃:** 部分 Issue 已有开发者主动实现方案（如 #1307），表明社区参与度较高，是潜在的贡献者来源。

---

*数据来源: [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode 社区动态日报 — 2026-09-03

## 1. 今日速览

OpenCode 今日发布 **v1.18.27**，重点修复了默认 provider 和流式 chunk 超时配置，降低慢模型启动失败率。社区持续推动 **Session Goal 原生支持**（Issue #27167，78 评论/140 赞）及 **自动发现 OpenAI 兼容模型**（Issue #6231，48 评论/225 赞），多项 Windows 兼容性问题已在近期稳定。

---

## 2. 版本发布

### v1.18.27 — 核心稳定性修复
- **Provider 超时默认值**：将默认 provider header 超时设为 5 分钟，降低慢模型启动时的失败率。
- **流式 Chunk 超时**：默认流式 chunk 超时设为 5 分钟，支持通过配置设为 `false` 以禁用。
- **Anthropic Thinking 配置**：支持通过配置让 `thinking.blockBinding` 选择退出，避免 provider 冲突。

> 链接：[GitHub Release](https://github.com/anomalyco/opencode/releases)

---

## 3. 社区热点 Issues

| 排名 | Issue | 摘要 | 热度 |
|------|-------|------|------|
| 1 | [#27167](https://github.com/anomalyco/opencode/issues/27167) | **原生 Session Goal / 生命周期**：目前无持久化 session 目标功能，社区强烈建议增加 `/goal` 命令支持 | 78 评论 / 140 赞 |
| 2 | [#6231](https://github.com/anomalyco/opencode/issues/6231) | **自动发现 OpenAI 兼容模型**：当前需手动在配置中列出所有模型，对 LM Studio/Ollama 等本地 provider 体验差 | 48 评论 / 225 赞 |
| 3 | [#46729](https://github.com/anomalyco/opencode/issues/46729) | **Thinking 配置报错**：升级到 v1.18.26 后，Bedrock Anthropic 模型返回 `prefix_mismatch_behavior` 错误 | 6 评论 / 13 赞 |
| 4 | [#36413](https://github.com/anomalyco/opencode/issues/36413) | **`opencode run` 退出码错误**：工具调用被自动拒绝且无最终输出时，进程以 `0` 退出，自动化难以检测 | 7 评论 |
| 5 | [#37650](https://github.com/anomalyco/opencode/issues/37650) | **可选搜索元数据导致权限列表失败**：pending glob/grep 权限在省略可选字段时引发 schema 编码错误 | 6 评论 |
| 6 | [#46931](https://github.com/anomalyco/opencode/issues/46931) | **Go 用量 Dashboard 计费错误**：glm-5.3-flash 半价促销期间，Dashboard 显示双倍费用 | 2 评论 |
| 7 | [#28590](https://github.com/anomalyco/opencode/issues/28590) | **writeOSC52 在 GNU screen 下使用 tmux 格式**：剪切板写入在 screen 中误用 tmux DCS 前缀，未做分块处理 | 11 评论 |
| 8 | [#46868](https://github.com/anomalyco/opencode/issues/46868) | **Formatter 配置静默失效**：配置 clang-format/air/uv 名称时会意外关闭格式化器 | 3 评论 |
| 9 | [#45823](https://github.com/anomalyco/opencode/issues/45823) | **houseCARL + Muse Spark 1.2 递归 JSON Schema 报错**：启用 MCP 后特定模型立即失败 | 2 评论 |
| 10 | [#35340](https://github.com/anomalyco/opencode/issues/35340) | **Web UI Session 列表空白回归**：v1.17.13 修复未 cherry-pick 到 stable 分支，导致会话侧栏为空 | 3 评论 / 1 赞 |

---

## 4. 重要 PR 进展

| PR | 摘要 | 状态 |
|----|------|------|
| [#46974](https://github.com/anomalyco/opencode/pull/46974) | **修复 revert 一致性**：解决 V2 session 在撤销过程中接受新 prompt 导致的时序问题 | OPEN |
| [#46928](https://github.com/anomalyco/opencode/pull/46928) | **轻量任务使用小模型**：允许 agent 在轻量 turn（状态更新、确认等）中使用小/快模型，提升多步任务性能 | ✅ CLOSED |
| [#46970](https://github.com/anomalyco/opencode/pull/46970) | **目录浏览复用当前位置**：目录补全和项目选择器改为使用稳定 Location，避免每次切换目录都启动完整运行时 | OPEN |
| [#46973](https://github.com/anomalyco/opencode/pull/46973) | **实验性设置独立页面**：将 Tabs 和 Show project names 从外观设置移至专属 Experimental 页面 | OPEN |
| [#46972](https://github.com/anomalyco/opencode/pull/46972) | **移除后台运行指示器**：删除 transcript 下方的额外 `Running` 标签和 spinner，保留工具/subagent 指示 | OPEN |
| [#46971](https://github.com/anomalyco/opencode/pull/46971) | **嵌入式传输绑定修复**：解决 Effect 应用中 FetchHttpClient 被意外重定向的问题 | OPEN |
| [#46530](https://github.com/anomalyco/opencode/pull/46530) | **暴露权限断言 API**：新增插件专属 `ctx.permission.assert(input)`，复用现有权限引擎 | OPEN |
| [#44838](https://github.com/anomalyco/opencode/pull/44838) | **浏览器 Pane 通过插件 RPC 接入**：新增 Browser tab，连接沙箱 Chromium 到内置浏览器插件 | OPEN |
| [#46272](https://github.com/anomalyco/opencode/pull/46272) | **停止重复工具调用循环**：连续 10 次调用相同工具且参数相同时自动终止会话 | OPEN |
| [#46912](https://github.com/anomalyco/opencode/pull/46912) | **修复管道输出截断**：`export`、`session list`、`db` 等命令在 JSON 模式下确保 stdout 写完再退出 | OPEN |

---

## 5. 功能需求趋势

1. **Session 生命周期管理**：社区持续呼吁原生支持 session goal、持久化目标与自动循环（Issue #27167），相关插件示例 PR #46328 已提交。
2. **模型自动发现与配置简化**：手动维护模型列表是高频痛点（Issue #6231），用户期望 OpenCode 能自动从 OpenAI 兼容端点拉取可用模型。
3. **多模型分层策略**：轻量 turn 使用小模型（PR #46928）反映用户对成本和速度的双重关注，推动"大模型 + 小模型"混合架构。
4. **IDE/编辑器深度集成**：浏览器插件（PR #44838）、权限断言 API（PR #46530）显示 OpenCode 正朝更完整的开发环境演进。
5. **自动化友好性**：非交互模式（`opencode run`）的退出码、JSON 输出完整性（PR #46912、Issue #36413）是 CI/CD 集成用户的核心需求。

---

## 6. 开发者关注点

| 痛点 | 涉及 Issue/PR |
|------|---------------|
| **超时配置不够灵活** | v1.18.27 修复（超时默认 5 分钟） |
| **Thinking 模式兼容问题** | Issue #46729（Bedrock Anthropic 配置报错） |
| **非交互模式信号缺失** | Issue #36413（退出码 0 但无输出）、PR #46912 |
| **权限系统边界缺陷** | Issue #37650（可选字段导致 schema 编码失败） |
| **工具调用循环** | PR #46272（连续 10 次相同调用自动终止） |
| **Windows 路径兼容性** | 系列 Issue #35329–#35332（路径分隔符、终端标题、进程管理） |
| **计费/用量显示错误** | Issue #46931（Go Dashboard 双倍计费） |
| **CLI 剪切板在 screen 下异常** | Issue #28590 |

---

*数据来源：github.com/anomalyco/opencode，统计时间：2026-09-03（过去 24 小时）*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报
**日期：2026-09-03**

---

## 1. 今日速览

Qwen Code 今日发布 **live-host-v0.2.0**，持续推进 OpenTUI 迁移（Batch 4）并优化 CI 弹性；社区重点聚焦于 TUI 架构重构、Web Shell 安全加固，以及核心层 XML tool-call 泄漏问题的修复。

---

## 2. 版本发布

### live-host-v0.2.0
**更新内容：**
- **CI 优化**：使共享 ECS 上 Vitest 并发度可配置化（#10667）
- **OpenTUI 迁移 Batch 4**：继续推进 CLI 界面从 `ink` 向 `OpenTUI` 的架构迁移

> 链接：[GitHub Release](https://github.com/QwenLM/qwen-code/releases)

---

## 3. 社区热点 Issues（Top 10）

| # | 标题 | 状态 | 评论 | 重要性 |
|---|------|------|------|--------|
| #8662 | Migrate TUI rendering layer from ink to OpenTUI (tracking) | OPEN | 24 | ⭐⭐⭐⭐⭐ |
| #10860 | `qwen serve` shell guard 忽略会话审批模式 | OPEN | 3 | ⭐⭐⭐⭐ |
| #10818 | Monitor pulse storm 可导致交互会话 DoS | CLOSED | 3 | ⭐⭐⭐⭐ |
| #10859 | Serve shell guard 阻断所有非 session 目录的 Git 命令 | CLOSED | 3 | ⭐⭐⭐⭐ |
| #10865 | perf: session workflow projection 每次渲染计算三次 | OPEN | 2 | ⭐⭐⭐ |
| #10866 | feat: 使 session workflow DAG 可导航 | OPEN | 2 | ⭐⭐⭐ |
| #10692 | tool-call XML 格式泄漏为纯文本 | OPEN | 2 | ⭐⭐⭐⭐ |
| #10791 | 平衡的 `<thinking>` 块泄漏到用户可见输出 | OPEN | 2 | ⭐⭐⭐⭐ |
| #10797 | 非 thinking 脚手架标签（tool-result/system-reminder）泄漏 | OPEN | 2 | ⭐⭐⭐⭐ |
| #10834 | MCP 工具返回的图片绕过 read_file 图像预算 | OPEN | 2 | ⭐⭐⭐ |

**热点解读：**
- **#8662** 是社区最受关注的架构级 Issue，当前 TUI 基于 `ink 7 + React 19` 存在结构性缺陷（闪烁、自定义渲染补丁等），迁移至 OpenTUI 是根本性解决方案，已持续跟踪近一个月。
- **#10860 / #10859** 聚焦 `qwen serve` 守护进程的安全壳层设计缺陷——无法配置、审计或覆盖，已引发安全标签讨论。
- **#10692 / #10791 / #10797 / #10700** 构成一组核心内容生成 Bug，涉及 XML tool-call 和 thinking 标签的解析/清洗不完整，直接影响用户可见输出质量，@yiliang114 集中提交多个关联 Issue。

> 完整 Issue 列表：[QwenLM/qwen-code Issues](https://github.com/QwenLM/qwen-code/issues)

---

## 4. 重要 PR 进展（Top 10）

| # | 标题 | 状态 | 作者 | 内容摘要 |
|---|------|------|------|---------|
| #10869 | ci: record host occupancy alongside disk-pressure samples | OPEN | yiliang114 | CI 磁盘压力采样增加 CPU/内存占用指标，提升资源监控粒度 |
| #10870 | test: stop millisecond budgets from measuring the shared pool | OPEN | yiliang114 | 单元测试绕过共享 ECS 池的毫秒级超时断言，解决伪失败 |
| #10857 | fix(web-shell): scope select-all in cell value dialog | OPEN | LizunovSergey | 修复 Cmd+A 在对话框内选中整页而非当前字段值的问题 |
| #9099 | feat(review): add Maven multi-module verification | CLOSED | wenshao | 新增 Maven 多模块验证功能，替代先前 PR #8777 |
| #10458 | fix(review): keep quoted code from blinding the footer strip | OPEN | wenshao | 修复 review 评论底部 strip 被引用代码遮挡的显示问题 |
| #10837 | feat(serve): add session resource catalog | OPEN | w9lsky | 新增 `GET /session/:id/resources` 守护进程路由，暴露会话的 Skill/MCP 快照 |
| #10575 | ci: give seconds-long jobs their own ECS lane | CLOSED | wenshao | 将 8 个秒级任务从 `ecs-qwen` 迁移至新建的 `ecs-light` 通道 |
| #10123 | fix(ci): salvage superseded review runs | OPEN | wenshao | 修复 review 工作流：push 不再取消进行中的审查任务，改为排队 |
| #10868 | fix(ci): retry contended unit attempt and bound hung ones | CLOSED | yiliang114 | 为 Ubuntu 单元测试通道增加重试机制和超时上限 |
| #10643 | feat(channels): Add worktree-isolated named tasks | OPEN | doudouOUC | 新增 `--worktree` 选项，支持守护进程管理 Git worktree 隔离的命名任务 |

> 完整 PR 列表：[QwenLM/qwen-code Pull Requests](https://github.com/QwenLM/qwen-code/pulls)

---

## 5. 功能需求趋势

基于本期 Issues 和 PRs，社区关注方向如下：

| 方向 | 关注度 | 说明 |
|------|--------|------|
| **TUI/UX 重构** | 🔴 高 | OpenTUI 迁移是核心主线，配套 DAG 导航、web-shell 交互修复同步推进 |
| **Web Shell 安全与稳定性** | 🔴 高 | shell guard 配置化、跨会话消息隔离、图像预算绕过等安全议题集中爆发 |
| **CI/CD 弹性优化** | 🟡 中 | 共享 ECS 池的资源隔离、超时控制、重试机制持续完善 |
| **Daemon/Channel 架构** | 🟡 中 | worktree 隔离、PID 文件安全、会话资源目录等守护进程功能深化 |
| **核心内容生成质量** | 🔴 高 | XML tool-call 和 thinking 标签泄漏是一组系统性 Bug，社区高度关注修复进度 |
| **MCP/工具集成** | 🟡 中 | MCP 图片预算绕过、Maven 多模块验证等功能扩展 |

---

## 6. 开发者关注点

**核心痛点：**

1. **内容生成污染**：多个 Issue 指出模型输出的 XML 标签（tool-call、thinking、tool-result）未被正确过滤，直接泄漏至用户可见区域，影响输出整洁性和可靠性。

2. **Web Shell 安全边界模糊**：`qwen serve` 的内置 shell guard 设计过于严格且不可配置，阻断合法 Git 操作且无法审计；同时 MCP 工具返回的图片绕过图像预算限制。

3. **TUI 架构历史债务**：基于 ink 的 TUI 存在闪烁、渲染补丁复杂等问题，迁移至 OpenTUI 是社区共识，但迁移进度和范围是持续跟踪焦点。

4. **CI 共享资源争抢**：ECS 共享池导致测试超时不稳定，通过独立通道、超时提升、重试机制逐步缓解，但资源隔离仍是长期课题。

**高频需求：**
- 会话级别的 shell 安全策略可配置化
- 多工作区/多通道场景下的状态隔离（pidfile 复用、会话命名保留等）
- 渲染性能优化（projection 重复计算、DAG 导航体验）

---

*数据来源：[github.com/QwenLM/qwen-code](https://github.com/QwenLM/qwen-code)*
*报告生成时间：2026-09-03*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI (CodeWhale) 社区动态日报
**日期：2026-09-03** | 仓库：[github.com/Hmbown/DeepSeek-TUI](https://github.com/Hmbown/DeepSeek-TUI)

---

## 1. 今日速览

v0.9.12 整合冲刺持续加速，核心进展集中在**提供商中立性审计修复**（#5588 已关闭）、**per-session 控制套接字**（#5533 已关闭）和**内存/技能命令系统**（FEAT-019/022 已合入）三大方向。今日同时合入了 lane TTL 清理的安全修复（#5824）和 tool-call 历史持久化修复（#5823），0.9.12 UX 打磨（Fleet 主题、Workbar 重命名、Underwater 默认主题）也进入收尾阶段。

---

## 2. 版本发布

**过去24小时内无新 Release。** v0.9.12 仍处于 milestone 整合阶段（#5573），当前稳定版本为 v0.9.11。

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 评论 | 重要性 |
|---|------|------|------|--------|
| [#5573](https://github.com/Hmbown/Codewhale/issues/5573) | v0.9.12 milestone tracker | OPEN | 23 | **0.9.12 总控 Issue**，汇总所有子切片（Operator handoff、Working branch、产品 PRD），是追踪发布进度的核心入口。 |
| [#5316](https://github.com/Hmbown/Codewhale/issues/5316) | EPIC-005: TUI Crate Decomposition | OPEN | 21 | **代码架构核心 EPIC**，负责将大型 crate 拆分，直接影响可维护性和后续功能扩展速度。 |
| [#5588](https://github.com/Hmbown/Codewhale/issues/5588) | Provider neutrality: 18 gates fixed | ✅ CLOSED | 7 | 审计发现并修复了 **18 个 DeepSeek 专属 gate**（如 NVIDIA NIM env 泄漏），使项目向多提供商中立迈出关键一步。 |
| [#5586](https://github.com/Hmbown/Codewhale/issues/5586) | Decompose mega files (lib.rs 18.7k, config.rs 12.3k) | OPEN | 6 | 直接响应 #5316，10k+ 行 mega 文件是社区长期痛点，拆分将显著降低贡献门槛。 |
| [#5533](https://github.com/Hmbown/Codewhale/issues/5533) | Per-session control socket | ✅ CLOSED | 5 | 为外部编排器（tmux 包装、CI harness）提供 JSON-RPC 控制面，是**Agent 化部署的关键基础设施**。 |
| [#5820](https://github.com/Hmbown/Codewhale/issues/5820) | Ollama: input budget 坍缩至 1024 tokens | OPEN | 2 | **本地模型用户高频痛点**：32K 窗口模型被默认 64K output reservation 钳制，直接影响用户体验。 |
| [#5637](https://github.com/Hmbown/Codewhale/issues/5637) | Scope MCP secret providers to owning runtime | OPEN | 2 | 安全架构改进：解决进程级环境变量泄露风险，对嵌入式托管场景至关重要。 |
| [#5575](https://github.com/Hmbown/Codewhale/issues/5575) | Fleet/subagent role posture 多源不一致 | OPEN | 2 | #5562 验证器角色矛盾的非孤立症状，涉及至少 5 处定义漂移，影响 Fleet 可信度。 |
| [#5824](https://github.com/Hmbown/Codewhale/issues/5824) | Lane TTL cleanup 可递归删除未验证路径 | ✅ CLOSED | 1 | **数据安全关键修复**：清理逻辑未验证 worktree 归属即可 `remove_dir_all`，已合入 PR #5854。 |
| [#5860](https://github.com/Hmbown/Codewhale/issues/5860) | Continuous Self-Learning from Dialog | OPEN | 1 | 社区创意需求：建议从对话中自动提取模式并生成 `SKILL.md`，实现技能系统的**自进化能力**。 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 内容摘要 |
|---|------|------|----------|
| [#5862](https://github.com/Hmbown/Codewhale/pull/5862) | 0.9.12 Fleet-only UX (workbar, startup, underwater) | OPEN | 整合 10 个 UX 切片：hover 统一样式、Workbar 重命名（原 sidebar/rail）、Underwater 默认主题、Provider 选择器、Settings 重组等。 |
| [#5861](https://github.com/Hmbown/Codewhale/pull/5861) | serve 登录页展示 Canonical Whale 品牌图标 | OPEN | 修复登录/注册页显示**不一致品牌图标**的 Bug，统一使用 C-curl 鲸鱼标记。 |
| [#5858](https://github.com/Hmbown/Codewhale/pull/5858) | 合并 ocean_treatment → ThemeId::Underwater | OPEN | 将 `ocean_treatment` 配置项坍缩进 `ThemeId::Underwater`，简化主题系统并统一配置路径。 |
| [#5854](https://github.com/Hmbown/Codewhale/pull/5854) | Lane TTL cleanup 增加 verified worktree 校验 | ✅ CLOSED | 修复 [#5824](https://github.com/Hmbown/Codewhale/issues/5824)，在删除前验证 managed-worktree 身份，防止误删外部目录。 |
| [#5840](https://github.com/Hmbown/Codewhale/pull/5840) | 持久化 tool-call identity 修复 restart 后 400 错误 | ✅ CLOSED | 修复 [#5823](https://github.com/Hmbown/Codewhale/issues/5823)：`serve --http` 模式在运行时重启后，含 tool-call 历史的线程因缺少 `name` 字段返回 400。 |
| [#5833](https://github.com/Hmbown/Codewhale/pull/5833) | FEAT-019: Memory 命令能力（search/remember/get/export） | ✅ CLOSED | 新增 `CommandCapabilities::MEMORY`，TUI 适配 search/remember/get/export/reindex/delete 等内存操作，带 typed outcomes。 |
| [#5831](https://github.com/Hmbown/Codewhale/pull/5831) | FEAT: Per-session control socket (JSON-RPC) | ✅ CLOSED | 实现 [#5533](https://github.com/Hmbown/Codewhale/issues/5533)，在 `<sessions-dir>/<id>/control.sock` 暴露 `message/interrupt/relaunch/status` 动词。 |
| [#5855](https://github.com/Hmbown/Codewhale/pull/5855) | Computer-use 插件：截图/点击/输入（MCP 协议） | OPEN | 首个独立 Bundle 插件，通过 MCP stdio 实现 1920px JPEG 截图 + 点击/键入，验证了插件系统的可扩展边界。 |
| [#5842](https://github.com/Hmbown/Codewhale/pull/5842) | Plugin + Marketplace 管理 API（Engine 侧） | OPEN | 为本地插件系统提供 `/v1/apps` 端点，支持插件安装/管理，配合 #5855 构建完整插件生态。 |
| [#5832](https://github.com/Hmbown/Codewhale/pull/5832) | Provider neutrality gates 修复（18 gates） | ✅ CLOSED | 实现 [#5588](https://github.com/Hmbown/Codewhale/issues/5588)，修复 NVIDIA NIM env 泄漏、跨协议 ghost-text 建议等 18 项 DeepSeek 专属 gate。 |

---

## 5. 功能需求趋势

从本期 Issues 中可以清晰看到以下社区关注方向：

1. **多模型/多提供商支持**：Provider 中立性（#5588）、Ollama 本地模型配置 bug（#5820）、MCP secret 作用域（#5637）—— 用户期望在不绑定 DeepSeek 的情况下使用各类模型。

2. **Agent 化与外部编排**：Per-session control socket（#5533）、Fleet/Subagent 角色管理（#5575、#5479）、Session Peek（#5271）—— 用户将 CodeWhale 嵌入 CI/CD 和自动化流水线的诉求强烈。

3. **插件与扩展生态**：Computer-use 插件（#5855）、Plugin Marketplace API（#5842）、调试器协议（#3981）、LSP 重命名/代码动作（#3975）—— 社区期待更丰富的工具链集成。

4. **技能系统进化**：FEAT-022 Skills 命令（#5829/#5825）、记忆系统（#5833）、自动技能学习（#5860）—— 从手动维护 `SKILL.md` 向**自学习技能**演进。

5. **UX 打磨与品牌统一**：Fleet UX（#5862）、Underwater 主题（#5858）、品牌图标修复（#5861）、Mid-turn 控制（#5268）、注意力通知（#4402）。

6. **代码架构治理**：Crate 拆分（#5316、#5586）、AppMode 清理（#5844）、 mega 文件分解—— 降低贡献门槛、提升长期可维护性。

---

## 6. 开发者关注点

| 痛点/需求 | 涉及 Issue/PR | 说明 |
|-----------|--------------|------|
| **本地模型输入预算被钳制** | #5820 | 32K 窗口模型因默认 64K output reservation 导致 input 仅 1024 tokens，需修复预算计算逻辑。 |
| **Lane TTL 清理存在数据丢失风险** | #5824 → #5854 | 清理逻辑未验证 worktree 归属即递归删除，已修复但警示了删除类操作的安全审计必要性。 |
| **`serve --http` 重启后 400 错误** | #5823 → #5840 | tool-call 历史在重启后丢失字段名，导致严格 serde schema 的提供商拒绝请求。 |
| **Fleet/Subagent 角色定义漂移** | #5575 | 角色政策在 ≥5 处独立定义且已漂移，需要单一真相源（SSOT）来保证一致性。 |
| **Mega 文件阻碍贡献** | #5586, #5316 | `lib.rs`（18.7k 行）、`config.rs`（12.3k 行）等文件是新人贡献的主要障碍，拆分 EPIC 持续推进中。 |
| **Setup 模块过度膨胀** | #3954 | `setup/mod.rs` 3,847 行，涵盖运行时预设、宪章校验、配置持久化等多重职责，急需拆分。 |
| **多会话控制体验薄弱** | #5271, #5268 | 用户希望在当前 composer 上下文不丢失的情况下，查看/响应其他 session 的审批请求，并支持 mid-turn 排队/发送/取消。 |
| **品牌体验不一致** | #5861 | 登录/注册页显示不同品牌图标的问题已修复，反映出多端品牌资产同步机制有待加强。 |

---

*数据来源：[github.com/Hmbown/DeepSeek-TUI](https://github.com/Hmbown/DeepSeek-TUI) · 统计窗口：2026-09-02 00:00 ~ 2026-09-03 00:00 UTC*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*