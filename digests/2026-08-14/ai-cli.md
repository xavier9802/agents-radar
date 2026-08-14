# AI CLI 工具社区动态日报 2026-08-14

> 生成时间: 2026-08-14 02:26 UTC | 覆盖工具: 10 个

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
**日期：2026-08-14 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

当前 AI CLI 工具生态呈现"多强并起、迭代加速"的格局。头部工具（Claude Code、Codex、Gemini CLI、Copilot CLI）已进入功能深水区，聚焦多 Agent 协作、MCP 生态集成与跨平台稳定性；垂直赛道工具（OpenCode、Pi、CodeWhale）通过性能优化与体验打磨建立差异化优势；国产力量（Kimi Code、Qwen Code）在本地部署与多模态场景持续发力。整体而言，工具竞争从"模型能力比拼"转向"工程体验与生态兼容性"之争，MCP 认证、会话持久化、跨端协同成为新战场。

---

## 2. 各工具活跃度对比

| 工具 | Issues (24h) | PR (24h) | Release | 发布频率 |
|------|-------------|----------|---------|----------|
| **Claude Code** | 10+ 热点 | 2 | v2.1.232 / v2.1.231 | 日更 |
| **OpenAI Codex** | 10 热点 | 10+ | 0.148.0-alpha.11~14 (4个) | 极高频 |
| **Gemini CLI** | 10 热点 | 11 | v0.56.0-nightly | 日更 |
| **GitHub Copilot CLI** | 25 活跃 | 1 | v1.0.80-0 / v1.0.80-1 | 周更 |
| **Kimi Code CLI** | 3 | 0 | 无 | 低频 |
| **OpenCode** | 10+ | 20+ | 无 | 中等 |
| **Pi** | 44 | 12 | 无 | 中等 |
| **Qwen Code** | 10 热点 | 15+ | v0.21.11 / preview | 日更 |
| **DeepSeek TUI (Codewhale)** | 50 | 27 | v0.9.7 | 高频 |
| **Grok Build** | 0 | 0 | 无 | 无活动 |

> 注：Issues/PR 数为今日新增或热点跟踪数，非仓库总量。

---

## 3. 共同关注的功能方向

| 功能方向 | 涉及工具 | 具体诉求 |
|----------|----------|----------|
| **多 Agent/多会话协作** | Claude Code、Codex、Qwen Code、Pi | 跨会话消息通信、Agent 自动调度、后台任务监控 |
| **MCP 生态集成** | Claude Code、Codex、Copilot CLI、OpenCode | OAuth 认证稳定性、并发刷新、服务器发现、端口配置 |
| **Windows 平台稳定性** | Claude Code、Codex、Copilot CLI、Qwen Code、DeepSeek | 跨会话消息回归、粘贴失效、进程泄漏、配置路径碎片化 |
| **会话持久化与恢复** | Claude Code、Copilot CLI、Pi、Qwen Code | 停止执行丢失 prompt、孤儿事件重放、长时间运行稳定性 |
| **启动性能优化** | OpenCode、Pi、Gemini CLI | 懒加载重型依赖、消除启动阻塞、大文本交互卡顿 |
| **模型配置精细化** | Copilot CLI、Qwen Code、Codex | Reasoning Effort 按 Agent 粒度设置、模型静默覆盖、外部 Provider 兼容 |
| **安全与合规** | OpenCode、Gemini CLI、Codex | 升级管道完整性校验、SSRF 防护、供应链 RCE、Cyber Safeguard 误报 |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|----------|----------|----------|
| **Claude Code** | 多 Agent 协作、跨会话通信、prompt cache 继承 | 企业开发者、深度 Claude 用户 | Anthropic 原生模型，Subagent Fork 模式 |
| **OpenAI Codex** | 快速迭代、Bedrock/Ollama 兼容、Skill 模型绑定 | OpenAI 生态用户、多云部署场景 | Rust 重写，实验性 API 先行 |
| **Gemini CLI** | 容量错误静默重试、AST-aware 文件读取、Auto Memory | Google 生态用户、成本敏感型开发者 | 上下文感知容错，模型自动降级 |
| **Copilot CLI** | IDE 深度集成、权限系统、多平台 frontmatter 兼容 | VS Code / GitHub 用户、团队协作 | 策略驱动权限，跨应用一致性 |
| **Qwen Code** | 多 Agent Fleet、Web Shell、Omni 多模态、Plugin 扩展 | 中文用户、多模态场景、自部署需求 | 开源优先，Agent Plugins v1 |
| **OpenCode** | 启动性能、V2 重构、安全审计响应 | 性能敏感开发者、安全研究者 | 懒加载架构，社区驱动安全修复 |
| **Pi** | TUI 体验、扩展系统、长对话上下文管理 | CLI 重度用户、终端爱好者 | 视觉行缓存、扩展单例优化 |
| **DeepSeek TUI (Codewhale)** | 本地模型部署、Auto-Review 守护层、终端窗口管理 | 本地推理用户、中文开发者 | DS4 本地路由，双护层架构 |
| **Kimi Code CLI** | 流式响应稳定性、Memory System、输出质量控制 | Moonshot 用户、长文本场景 | 等待官方迭代，社区反馈驱动 |

---

## 5. 社区热度与成熟度

| 维度 | 高热度/高成熟度 | 快速迭代期 | 成长期/低活跃 |
|------|----------------|-----------|--------------|
| **工具** | Claude Code、Copilot CLI、Codex | OpenCode、Pi、DeepSeek TUI | Kimi Code CLI、Grok Build |
| **特征** | Issue 响应快、版本稳定、企业用户多 | PR 数量大、性能优化集中、社区贡献活跃 | Issue 少但痛点明确、版本发布低频 |
| **信号** | Windows 回归潮反映用户基数大；MCP OAuth 问题普遍存在 | 懒加载重构、TUI 性能优化显示工程投入 | 功能需求（Memory System、流式稳定性） awaiting 官方响应 |

---

## 6. 值得关注的趋势信号

### 信号一：MCP 认证成为全行业痛点
**涉及工具**：Claude Code、Codex、Copilot CLI 均出现 OAuth 相关问题
**解读**：MCP 生态快速扩张但认证层未成熟，silent refresh 失败、并发刷新冲突、临时 5xx 无重试是共性缺陷。建议开发者关注官方修复进度，企业用户暂避免在生产环境依赖 MCP 关键路径。

### 信号二：Windows 平台回归潮集中爆发
**涉及工具**：Claude Code（跨会话消息）、Qwen Code（Ctrl+V 粘贴）、Copilot CLI（进程泄漏）
**解读**：多工具在 Windows Desktop 更新后出现集中性回归，反映跨平台测试覆盖不足。建议 Windows 用户暂缓升级，关注 patch 发布。

### 信号三：多 Agent 协作从概念走向落地
**涉及工具**：Claude Code（@提及/fork模式）、Qwen Code（/coordinate/Fleet）、Codex（线程队列）
**解读**：头部工具均在多 Agent 协作方向投入，但体验尚不成熟（Claude Code Windows 回归打断体验）。这是未来 6-12 个月的核心竞争方向。

### 信号四：启动性能与长对话稳定性成为差异化战场
**涉及工具**：OpenCode（懒加载重构）、Pi（视觉行缓存）、Gemini CLI（容量重试）
**解读**：当模型能力趋同，工程体验成为用户留存关键。懒加载、上下文压缩时机、大文本渲染优化是值得跟进的技术方向。

### 信号五：安全审计从被动响应转向主动治理
**涉及工具**：OpenCode（三条安全 Issue 连续提交）、Gemini CLI（供应链 RCE 修复）
**解读**：安全研究者开始系统性审计 AI CLI 工具，升级管道、SSRF、上下文完整性成为新焦点。建议开发者建立定期安全审查机制。

---

**总结**：2026 年 Q3 的 AI CLI 生态正处于"功能收敛+体验打磨"的关键阶段。多 Agent 协作、MCP 生态、跨平台稳定性是三大主赛道；OpenCode、Pi、Codewhale 等工具通过工程优化建立差异化；Windows 平台问题和 MCP 认证缺陷是行业共性挑战。开发者在选择工具时，建议根据目标平台（Windows/macOS/Linux）、部署场景（云端/本地）、协作需求（单 Agent/多 Agent）综合评估，并关注各工具对高频痛点的修复节奏。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告

**数据截止：2026-08-14 | 分析师：Agnes**

---

## 1. 热门 Skills 排行

| 排名 | Skill | 功能简介 | 状态 | 社区热度 |
|------|-------|----------|------|----------|
| 1 | [servicenow](https://github.com/anthropics/skills/pull/568) | ServiceNow 平台全栈助手（ITSM/ITOM/SecOps/FSM 等） | 🟢 OPEN | 长期维护，更新至 08-12 |
| 2 | [self-audit](https://github.com/anthropics/skills/pull/1367) | AI 输出质量审计：机械验证 + 四维推理质量门禁 | 🟢 OPEN | 最新 PR（06-28），覆盖完整交付前校验 |
| 3 | [testing-patterns](https://github.com/anthropics/skills/pull/723) | 全栈测试技能（单元测试/组件测试/Trophy 模型） | 🟢 OPEN | 测试工程领域核心需求 |
| 4 | [skill-creator 修复](https://github.com/anthropics/skills/pull/1298) | 修复 `run_eval.py` 召回率恒为 0% 的严重 bug | 🟢 OPEN | 直接影响 Skill 开发工具链 |
| 5 | [odt](https://github.com/anthropics/skills/pull/486) | OpenDocument 格式（ODT/ODS）创建与解析 | 🟢 OPEN | 填补开源办公格式空白 |
| 6 | [document-typography](https://github.com/anthropics/skills/pull/514) | AI 生成文档的排版质量控制（孤行、寡行检测） | 🟢 OPEN | 文档质量痛点精准打击 |
| 7 | [pyxel](https://github.com/anthropics/skills/pull/525) | 复古像素游戏开发（Pyxel 引擎 MCP 集成） | 🟢 OPEN | 创意编程细分领域 |
| 8 | [frontend-design](https://github.com/anthropics/skills/pull/210) | 前端设计技能清晰度与可执行性优化 | 🟢 OPEN | 已有 Skill 持续迭代优化 |

---

## 2. 社区需求趋势

从 Issues 讨论热度提炼四大核心方向：

| 方向 | 代表 Issue | 核心诉求 |
|------|-----------|----------|
| 🔐 **安全与信任治理** | [#492](https://github.com/anthropics/skills/issues/492)（43 评论） | 社区 Skill 冒充官方 Skill 导致权限越界，亟需命名空间隔离与身份验证机制 |
| 🏢 **企业协作共享** | [#228](https://github.com/anthropics/skills/issues/228)（16 评论，8 👍） | 组织内 Skill 共享链路缺失，当前依赖手动传输，期待原生共享库/链接功能 |
| 🛠️ **开发工具链可靠性** | [#556](https://github.com/anthropics/skills/issues/556)（12 评论，7 👍） | `run_eval.py` 触发检测失效导致 Skill 描述优化循环失效，10+ 独立复现 |
| 📦 **生态规范化** | [#189](https://github.com/anthropics/skills/issues/189)（6 评论，9 👍） | 插件内容重复导致 Skill 冗余注入，期待明确的命名与分类规范 |
| 🧠 **Agent 质量门禁** | [#1385](https://github.com/anthropics/skills/issues/1385)、[#412](https://github.com/anthropics/skills/issues/412) | 推理质量前置校验、Agent 治理策略（信任评分/审计追踪）成为新兴需求 |

---

## 3. 高潜力待合并 Skills

以下 PR 社区反馈活跃、问题描述清晰，具备较高落地概率：

| PR | 作者 | 潜力理由 | 阻塞点 |
|----|------|----------|--------|
| [#1367](https://github.com/anthropics/skills/pull/1367) `self-audit` | YuhaoLin2005 | 覆盖交付前全链路质量校验，提出可复用的四维度推理门禁框架 | 待官方审查 |
| [#1298](https://github.com/anthropics/skills/pull/1298) `skill-creator` 修复 | MartinCajiao | 修复阻塞整个 Skill 优化工作流的 critical bug，10+ 独立复现确认 | 待官方审查 |
| [#568](https://github.com/anthropics/skills/pull/568) `servicenow` | Vanka07 | 企业 IT 服务管理领域覆盖最广的 Skill，更新活跃（08-12） | 待官方审查 |
| [#1538](https://github.com/anthropics/skills/pull/1538) 规范修复 | bechor25 | 修复 Skill 命名与目录不一致问题，符合官方规范 | 待官方审查 |
| [#723](https://github.com/anthropics/skills/pull/723) `testing-patterns` | 4444J99 | 测试工程是开发者高频场景，覆盖完整测试金字塔 | 待官方审查 |

---

## 4. Skills 生态洞察

> **当前社区最集中的诉求是：在技能数量快速扩张的同时，建立可靠的质量门禁机制、企业级安全治理规范，以及稳定的开发工具链——社区不再只关注"有什么 Skill"，更关注"Skill 是否可信、是否安全、是否好用"。**

核心矛盾已从**供给不足**转向**信任与质量基础设施缺失**，体现在安全仿冒问题（#492）、评估工具失效（#556/#1298）、企业协作断层（#228）三大痛点上。

---



# Claude Code 社区动态日报
**日期：2026-08-14**

---

## 1. 今日速览

v2.1.232 正式发布，核心亮点是 **Subagent 分叉模式默认开启**（继承完整会话与 prompt cache）及 **`@` 提及跨会话**功能。Windows Desktop 1.28929.0 上线后出现集中性回归：跨会话消息投递但无法触发回复，已引发大量 Issue 反馈。

---

## 2. 版本发布

### v2.1.232（今日）
- **Subagent Fork 默认开启**：`subagent_type: "fork"` 的子代理现在默认继承完整对话历史和 prompt cache；交互式会话中非队友代理默认后台运行
- **`@` 符号提及**：在 prompt 中输入 `@` 可按名称提及另一个 Claude 会话
- 链接：https://github.com/anthropics/claude-code/releases

### v2.1.231
- 修复 MCP OAuth 登录失败：针对使用预注册 OAuth 客户端的服务器（如 Slack），解决 redirect URI 不匹配问题
- 链接：https://github.com/anthropics/claude-code/releases

---

## 3. 社区热点 Issues

| 排名 | Issue | 评论 | 👍 | 重要性 |
|------|-------|------|----|--------|
| 1 | #84352 - CVP 批准组织仍被 cyber safeguard 拦截 | 94 | 14 | 🔴 高 |
| 2 | #24798 - 多会话间通信功能需求 | 66 | 21 | 🔴 高 |
| 3 | #85603 - TUI 中输入被静默丢弃 | 22 | 1 | 🟡 中 |
| 4 | #53065 - advisor() 工具 inflate tokens 触发提前压缩 | 15 | 7 | 🟡 中 |
| 5 | #86012 - 跨会话消息导致接收方 session 无响应 | 15 | 3 | 🔴 高 |
| 6 | #86138 - Windows Desktop send_message 不送达暂停会话 | 7 | 1 | 🔴 高 |
| 7 | #86069 - 跨会话消息进入 composer 但不提交 | 6 | 1 | 🔴 高 |
| 8 | #86237 / #86298 - 跨会话消息被静默丢弃 | 10 | 1 | 🔴 高 |
| 9 | #73107 - Windows Desktop 升级后无法启动 | 3 | 1 | 🟡 中 |
| 10 | #81620 - advisor tool 双倍 context 触发 auto-compact | 3 | 3 | 🟡 中 |

**重点解读：**
- **#84352**（94 评论）：CVP 认证组织反复遭遇误拦截，Verification Portal 显示"审核中"，影响企业用户信任。社区反应激烈，是当日最受关注的功能 Bug。
- **#24798**（66 评论）：长期未满足的多会话协作需求，v2.1.232 的 `@` 功能和 fork 模式部分回应了此诉求。
- **Windows 跨会话消息回归潮**（#86012, #86138, #86069, #86237, #86298 等）：集中在 desktop 1.28929.0 + runtime 2.1.227 升级后，消息能显示但从不触发模型响应，部分已在 2.1.231 复现。

---

## 4. 重要 PR 进展

| PR | 状态 | 内容 |
|----|------|------|
| #86537 | Open | 修复 CHANGELOG.md 中 `CLAUDE_BASH_NO_LOGIN` 条目的重复词（"to to"）|
| #60280 | Closed | CI 安全加固：将剩余 `actions/checkout` 和 `actions/github-script` 固定到具体 SHA |

> 注：过去 24 小时 PR 数量较少（2 条），当前社区活动集中在 Issue 反馈。

---

## 5. 功能需求趋势

从 Issue 数据提炼社区关注方向：

1. **多 Agent/多会话协作** — 最热方向。#24798（66 评论）长期推动，v2.1.232 的 `@` 提及和 fork 模式是里程碑回应，但 Windows Desktop 的回归问题暂时打断了体验。
2. **Windows Desktop 稳定性** — 近期集中爆发：跨会话消息、GPU 崩溃（#86265, #86146）、更新失败（#86555, #73107）、进程泄漏（#77379, #77421）。
3. **MCP 集成完善** — OAuth 登录修复（v2.1.231）显示团队在跟进，但 OTLP 遥测（#82092）等问题仍存在。
4. **Token 计量与压缩准确性** — `advisor()` 工具 inflate tokens（#53065, #81620）引发用户对成本控制的担忧。
5. **Cyber Safeguard 策略** — CVP 批准用户仍被拦截（#84352, #86527），企业用户对此敏感。

---

## 6. 开发者关注点

**高频痛点汇总：**

| 痛点 | 涉及 Issue | 严重程度 |
|------|-----------|----------|
| 跨会话消息投递后不触发响应 | #86012, #86138, #86069, #86237, #86298, #86386, #86385, #86212, #86088, #86398, #86029 | 🔴 严重 |
| Windows Desktop 版本更新后回归 | 上述所有 + #86555, #73107, #77421 | 🔴 严重 |
| GPU 进程崩溃 | #86265, #86146 | 🟡 中 |
| Cyber Safeguard 误报 | #84352, #86527 | 🔴 高 |
| TUI 交互缺陷（输入丢弃、session 卡死） | #85603, #74017 | 🟡 中 |
| advisor() 工具计量异常 | #53065, #81620 | 🟡 中 |
| PreToolUse Hook 审计信息丢失 | #82642 | 🟢 低 |

**核心结论：** 今日社区最大事件是 **Windows Desktop 1.28929.0 / runtime 2.1.227 升级引发的跨会话通信大规模回归**。超过 10 个 Issue 描述同一根因（消息送达但不触发模型响应），且部分问题在 v2.1.231 中仍未修复。建议关注官方后续 patch 发布。

---

*数据来源：github.com/anthropics/claude-code，统计周期 2026-08-13 ~ 2026-08-14*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-08-14**

---

## 1. 今日速览

Codex CLI 进入 `0.148.0` alpha 快速迭代期，过去24小时连续发布4个版本，同步新增 Amazon Bedrock Runtime 提供商和实验性线程队列 API。社区方面，MCP stdio 进程泄漏（Issue #26984）和 Windows 桌面崩溃安全（Issue #26990）引发广泛讨论，macOS 桌面版出现严重性能回退（Issue #38468）引起开发者高度关注。

---

## 2. 版本发布

**Rust 版本快速迭代：`0.148.0-alpha.11` ~ `0.148.0-alpha.14`**

过去24小时内连续发布4个 alpha 版本，属于密集修复周期。同期合并的 PR 显示以下关键更新：

| PR | 内容 |
|---|---|
| [#38470](https://github.com/openai/codex/pull/38470) | 新增 Amazon Bedrock Runtime 内置提供商，支持区域化 `bedrock-runtime` OpenAI 兼容端点 |
| [#38456](https://github.com/openai/codex/pull/38456) | 新增实验性线程队列 API（`thread/queue/add/list/update/delete/reorder/start`） |
| [#38448](https://github.com/openai/codex/pull/38448) | 支持 MCP OAuth 回调端口按服务器配置 |
| [#38475](https://github.com/openai/codex/pull/38475) | 增加 Skill 模型委托指令，支持 Luna/Sol/Terra 模型绑定与验证 |

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 评论 | 👍 | 重要性 |
|---|---|---|---|---|---|
| [#26984](https://github.com/openai/codex/issues/26984) | MCP stdio servers 泄漏 pipe fds + 孤儿进程 → EMFILE | OPEN | 21 | 4 | 🔴 **严重**：MCP stdio 服务持续泄漏文件描述符，长时间运行后触发 "Too many open files"，影响所有使用 MCP 的 CLI 用户 |
| [#26990](https://github.com/openai/codex/issues/26990) | Windows 桌面本地状态在断电后非崩溃安全 | OPEN | 18 | 0 | 🟠 高：pins/projects 重置、配置回退、时间戳异常，Windows 桌面用户痛点 |
| [#37403](https://github.com/openai/codex/issues/37403) | [macOS] Desktop 无法恢复 Remote Control/CLI 线程：`already has an active writer` | OPEN | 18 | 11 | 🟠 高：8月7日更新后回归，影响远程移动端控制桌面 CLI 的工作流 |
| [#31553](https://github.com/openai/codex/issues/31553) | VS Code 扩展更新后停止自动包含 IDE 上下文 | **CLOSED** | 17 | 12 | 🟡 中：影响 Windows/WSL2 环境，已关闭但反映扩展上下文集成稳定性问题 |
| [#2062](https://github.com/openai/codex/issues/2062) | 请求：监控后台服务 | OPEN | 9 | 10 | 🟡 中：长期需求，支持长时间构建/服务器运行不阻塞 agent，可并行检查日志 |
| [#23454](https://github.com/openai/codex/issues/23454) | `$skill` 显式调用忽略本地仅显式技能 | OPEN | 8 | 7 | 🟡 中：CLI skill 系统行为异常，本地 skills 未正确加载 |
| [#33551](https://github.com/openai/codex/issues/33551) | Multi-Agent V2 向外部 Responses 提供商发送 OpenAI 专用 `agent_message` | OPEN | 8 | 6 | 🟡 中：影响 Ollama 等外部 provider 的多代理兼容性 |
| [#35419](https://github.com/openai/codex/issues/35419) | VS Code IDE 上下文自动禁用，选中文本未附加（WSL2） | **CLOSED** | 6 | 10 | 🟡 中：WSL2 环境下 IDE 上下文集成缺陷，已关闭 |
| [#30435](https://github.com/openai/codex/issues/30435) | WSL agent：cwd 错误 + Chrome/Computer Use 不可用 | OPEN | 5 | 2 | 🟡 中：Windows+WSL2 环境下路径翻译和 bundled plugins 问题 |
| [#38468](https://github.com/openai/codex/issues/38468) | [macOS] 严重性能回退：100%+ CPU、10GB+ RAM、频繁 UI 卡死 | OPEN | 2 | 0 | 🔴 **紧急**：新版本 `26.810.41047` 引入，影响 Apple Silicon 设备用户体验 |

---

## 4. 重要 PR 进展

| PR | 标题 | 状态 | 功能说明 |
|---|---|---|---|
| [#38470](https://github.com/openai/codex/pull/38470) | Add Amazon Bedrock Runtime provider | CLOSED | 新增 AWS Bedrock 提供商，支持区域化端点和 SigV4 认证 |
| [#38456](https://github.com/openai/codex/pull/38456) | Add experimental thread queue APIs | CLOSED | 提供线程持久化队列 API，支持 FIFO 自动分发 |
| [#38475](https://github.com/openai/codex/pull/38475) | Add bounded skill model delegation instructions | CLOSED | Skill 可声明目标模型（Luna/Sol/Terra），解析器按可用提供商绑定 |
| [#38467](https://github.com/openai/codex/pull/38467) | Parse model annotations from skill frontmatter | CLOSED | Skill frontmatter 新增 `model` 字段解析，支持 `model: luna` 标注 |
| [#38463](https://github.com/openai/codex/pull/38463) | Preserve thread subscriptions across revert reloads | CLOSED | 修复线程回滚重载时订阅丢失问题 |
| [#38461](https://github.com/openai/codex/pull/38461) | Centralize turn environment selection state | CLOSED | 将环境选择状态集中到 `TurnEnvironment`，简化环境解析逻辑 |
| [#38448](https://github.com/openai/codex/pull/38448) | Support per-server MCP OAuth callback ports | CLOSED | MCP 服务器配置支持独立 OAuth 回调端口 |
| [#38447](https://github.com/openai/codex/pull/38447) | Add running-task exit choices to local daemon sessions | CLOSED | 本地 daemon 会话支持 Ctrl-C 时选择：取消任务/退出/停止服务 |
| [#38441](https://github.com/openai/codex/pull/38441) | Give Guardian V2 full tool action context | CLOSED | Guardian V2 获取完整 `ToolPayload`，支持风险评估 |
| [#38440](https://github.com/openai/codex/pull/38440) | Add app-server support for reverting paginated threads | CLOSED | 新增实验性 `thread/revert` API，支持分页线程历史回滚 |

---

## 5. 功能需求趋势

基于 Issues 分析，社区最关注的方向：

1. **IDE 集成稳定性** — VS Code 扩展的 IDE Context 自动禁用、路径解析、CSP 资源加载等问题频发（#31553、#34696、#35419、#37517），Windows/WSL2 环境尤甚。
2. **桌面端性能与稳定性** — macOS 端出现内存泄漏（#38455）、CPU/RAM 暴增（#38468）、UI 卡死等问题，桌面端成为反馈重灾区。
3. **远程/移动端协同** — Remote Control 线程恢复失败（#37403）、移动端任务丢失（#33396）反映跨端同步机制尚不完善。
4. **外部 Provider 兼容性** — Multi-Agent V2 与 Ollama 等外部 provider 的协议兼容问题（#33551），以及 Bedrock 等云提供商支持（#38470）。
5. **后台任务与技能系统** — 长期运行的后台服务监控需求（#2062）和技能模型绑定（#23454、#38475）显示开发者对 agent 工作流精细控制的需求。

---

## 6. 开发者关注点

| 痛点 | 高频 Issue |
|---|---|
| **MCP 资源泄漏** | #26984（21 评论，2 个月开放）|
| **Windows 桌面数据持久化** | #26990、#33114、#32948 |
| **IDE 上下文集成脆弱** | #31553、#34696、#35333、#35419 |
| **macOS 性能回退** | #38455、#38468（同日反馈）|
| **远程会话恢复失败** | #37403、#33396 |
| **权限策略不生效** | #24934、#33114 |
| **多代理与外部模型兼容** | #33551、#38107 |
| **语音助手卡死** | #38469 |

---

*数据来源：github.com/openai/codex，统计时段 2026-08-13 ~ 2026-08-14*

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报
**日期：2026-08-14**

---

## 1. 今日速览

今日发布 `v0.56.0-nightly.20260814`，核心更新为容量不足错误的上下文感知静默重试机制，以及稳定化慢速 runner 上的文件系统 e2e 测试。社区 Issues 中，API 参数错误和模型容量不可用仍是最高频痛点，多条历史问题在同日触发更新。

---

## 2. 版本发布

**v0.56.0-nightly.20260814.gc0d192452**
- `fix(core)`: 实现针对容量错误的上下文感知静默重试和可用性 TTL，支持非交互场景自动退避重试
- `test(e2e)`: 稳定化 `file-system-interactive` 测试，解决慢速虚拟化环境下的偶发失败

> [PR #28790](https://github.com/google-gemini/gemini-cli/pull/28790) · [PR #28793](https://github.com/google-gemini/gemini-cli/pull/28793)

---

## 3. 社区热点 Issues

| # | 标题 | 热度 | 关注理由 |
|---|------|------|----------|
| [#18811](https://github.com/google-gemini/gemini-cli/issues/18811) | API Error: Request contains an invalid argument | 🔥 16评论/5👍 | 高频 API 错误，用户反馈自动更新后出现，影响广泛 |
| [#19883](https://github.com/google-gemini/gemini-cli/issues/19883) | No capacity available for gemini-3-flash-preview | 🔥 14评论/8👍 | 模型容量不足问题，14条讨论反映大量用户受扰 |
| [#18903](https://github.com/google-gemini/gemini-cli/issues/18903) | Request contains an invalid argument | 14评论/2👍 | 与 #18811 同类问题，确认非偶发 |
| [#18834](https://github.com/google-gemini/gemini-cli/issues/18834) | Sandbox image missing or could not be pulled | 12评论/1👍 | 沙箱镜像拉取失败，用户主动提供修复方案 |
| [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) | Subagent recovery 误报 GOAL success | 12评论/2👍 | 子代理达到最大轮次后错误标记为成功，影响 Agent 可靠性 |
| [#23297](https://github.com/google-gemini/gemini-cli/issues/23297) | 按 Enter 无响应 | 11评论/10👍 | **最高👍数**，交互卡顿问题，用户体验直接影响大 |
| [#18961](https://github.com/google-gemini/gemini-cli/issues/18961) | VS Code 扩展检测失效 | 9评论 | IDE 集成兼容性，影响插件生态体验 |
| [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) | Component level evaluations | 7评论 | 维护者主导的评估基础设施 Epic，反映团队对质量保障的重视 |
| [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) | AST-aware file reads/search | 7评论/1👍 | 代码理解精度优化方向，社区期待提升工具调用效率 |
| [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) | Skills 和 Sub-agents 未被自动调用 | 6评论 | Agent 智能调度能力不足，用户期望更自主的工具使用 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| [#28597](https://github.com/google-gemini/gemini-cli/pull/28597) | 修复环境变量加载顺序竞争条件 | ✅ Closed | 解决 settings 解析时 `.env` 尚未加载导致占位符无法展开的问题 |
| [#28602](https://github.com/google-gemini/gemini-cli/pull/28602) | Docker 基础镜像升级至 node:24-slim | ✅ Closed | 构建和运行时镜像统一升级 |
| [#28603](https://github.com/google-gemini/gemini-cli/pull/28603) | Sandbox Dockerfile 升级至 Node 22 | ✅ Closed | Node 20 已于 2026-04 EOL，修复安全合规风险 |
| [#28596](https://github.com/google-gemini/gemini-cli/pull/28596) | 新增 `--list-all-sessions` 选项 | ✅ Closed | 跨工作区查看和管理所有会话，解决会话分散难以追踪问题 |
| [#28592](https://github.com/google-gemini/gemini-cli/pull/28592) | 无 preview 权限时保持 Auto 模型可见 | ✅ Closed | 修复动态模型配置下 Auto 选项被错误隐藏 |
| [#28718](https://github.com/google-gemini/gemini-cli/pull/28718) | 流中断时记录已接收用量 | 🔄 Open | 修复 abort 时 usage metadata 丢失，改善用量统计准确性 |
| [#28679](https://github.com/google-gemini/gemini-cli/pull/28679) | 改进 Vertex AI 401 错误提示 | 🔄 Open | 区分标准 API Key 与 GCP 凭据配置错误，提升调试体验 |
| [#28740](https://github.com/google-gemini/gemini-cli/pull/28740) | 修复 eval-pr 工作流供应链 RCE | 🔄 Open | 拆分 `pull_request_target` 为安全构建步骤，阻断恶意 fork 代码执行 |
| [#28778](https://github.com/google-gemini/gemini-cli/pull/28778) | 升级 simple-git 修复 CVE-2026-28292 | 🔄 Open | 修复 **CRITICAL** 级别安全漏洞 |
| [#28801](https://github.com/google-gemini/gemini-cli/pull/28801) | 取消时回滚整个多轮请求 | ✅ Closed | 修复 abort 后聊天历史残留未完成 tool call 的问题 |

---

## 5. 功能需求趋势

- **IDE/扩展集成稳定性**：VS Code 扩展检测 (#18961)、WSL2 剪贴板图片粘贴 (#27588) 持续受关注
- **Agent 智能调度优化**：Skills/Sub-agents 自动调用 (#21968)、AST-aware 文件读取 (#22745)、browser agent 韧性 (#22232)
- **用量与 Session 管理**：跨工作区会话列表 (#28596)、流中断用量记录 (#28718)、logger 会话 ID 污染 (#27280)
- **模型支持扩展**：新增 Claude Sonnet 4.5 / Opus 4.8 (#28803)、Auto 模型可见性修复 (#28592)
- **安全合规加固**：供应链 RCE 防护 (#28740)、简单 git 漏洞修复 (#28778)、A2A 服务器认证缺失 (#28699)

---

## 6. 开发者关注点

| 痛点 | 涉及 Issues |
|------|-------------|
| **API 参数异常 & 容量不足** | #18811, #19883, #18903 |
| **交互卡顿 / 无响应** | #23297, #25166 |
| **自动记忆 (Auto Memory) 行为异常** | #26522, #26523, #27911 |
| **沙箱镜像与运行环境** | #18834 |
| **子代理/Agent 可靠性** | #22323, #21968, #22093 |
| **环境变量与配置加载** | #28597 (PR 已修复) |
| **多轮请求中断状态残留** | #28801 (PR 已修复) |

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-08-14** | 数据来源：[github.com/github/copilot-cli](https://github.com/github/copilot-cli)

---

## 1. 今日速览

Copilot CLI 发布 v1.0.80-0 和 v1.0.80-1 两个补丁版本，新增 `--enable-mcp-server` 标志允许在当前运行中重新启用被禁用的 MCP 服务器。社区反馈集中体现在 MCP  OAuth 认证问题、模型配置兼容性以及会话管理稳定性三个方面，共 25 个活跃 Issue。

---

## 2. 版本发布

### v1.0.80-0 / v1.0.80-1

| 类型 | 内容 |
|------|------|
| **新增** | 添加 `--enable-mcp-server` 参数，可在当前运行中重新启用 settings 中禁用的 MCP 服务器 |
| **改进** | 共享会话 UI 优化：在 `--ahp` 模式下，当有其他客户端加入时，Sessions 标签页的会话行会显示 `2 clients` 或更多 |
| **修复** | Fixes and changes |

---

## 3. 社区热点 Issues

### 🔥 模型与 Agent 配置（6 条）

**#2904 [OPEN] Custom Agent YAML Frontmatter Should Support Reasoning Effort** 👍 20 | 6 评论
自定义 Agent 的 `.agent.md` 文件目前支持 `model` 字段锁定模型，但无法单独设置 reasoning effort。社区呼声强烈，已有 PR 提出实现方案。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/2904)

**#4345 [CLOSED] Reasoning effort 'medium' is not supported for model 'claude-haiku-4.5'**
feature flags 激活时，子 Agent 执行报错：claude-haiku-4.5 不支持 medium reasoning effort。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4345)

**#2133 [OPEN] Custom agent frontmatter `model` field rejects array syntax** 👍 7 | 4 评论
VS Code Copilot Chat 支持 `model` 数组语法，但 CLI 无法解析，导致 Agent 加载失败。跨平台兼容性痛点。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/2133)

**#3954 [OPEN] `explore` tool hardcodes model to `gpt-5.4-mini`**
更新到 v1.0.65 后，`explore` 工具忽略自定义模型配置（如 DeepSeek），强制使用 `gpt-5.4-mini`。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/3954)

**#4462 [OPEN] Explicit code-review subagent model override is ignored**
内置 `code-review` 子 Agent 被配置为使用 `gpt-5.6-luna`，但实际启动时使用 `gpt-5.6-sol`，配置被静默覆盖。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4462)

**#4473 [OPEN] claude-haiku-4.5 sub-agent fails with reasoning effort 'medium'**
与 #4345 类似，内部路由到 claude-haiku-4.5 的子任务错误应用 medium reasoning effort。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4473)

### 🔗 MCP 与 OAuth 认证（7 条）

**#4480 [OPEN] Atlassian MCP OAuth fails — regression from 1.0.71**
升级至 v1.0.79 后，Atlassian MCP 服务器 OAuth 发现失败，报错 "Incompatible authorization server (RFC 8414 §3.3)"，为版本回归问题。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4480)

**#4472 [OPEN] Remote MCP: concurrent tool calls during token refresh**
并发工具调用时，每个调用独立触发认证刷新，创建多个 rmcp service，导致进行中的工具调用被取消。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4472)

**#4464 [OPEN] Remote MCP OAuth silent refresh fails with AADSTS70011**
Microsoft Entra OAuth 的 silent refresh 路径持续失败，约每 60-75 分钟强制要求交互登录。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4464)

**#4466 [OPEN] Remote MCP transient 5xx marks server failed with no retry**
MCP 服务器 `initialize` 返回临时 5xx（如 502）时，CLI 记录为永久失败且无重试机制。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4466)

**#4463 [OPEN] MCP OAuth intermittently fails on Windows with socket error 10013**
Windows 上远程 MCP OAuth 认证偶尔在浏览器打开前失败，报 socket 权限错误。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4463)

**#4478 [OPEN] MCP server collision detection is case-sensitive**
不同作用域中逻辑相同的 MCP 服务器名（如 `MCPBrowser` vs `mcpbrowser`）被视为不同实例，均被加载。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4478)

**#4476 [OPEN] `--enable-mcp-server` 已随 v1.0.80 发布**
今日版本新增功能，缓解上述部分 MCP 问题。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4476)

### 📁 权限与会话管理（5 条）

**#4482 [OPEN] allowed_directories 配置对 shell 命令无效**
`permissions-config.json` 中配置的允许目录无法抑制 shell 命令的路径外访问提示，`/add-dir` 可临时修复。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4482)

**#4477 [OPEN] Session and prompt lost when stopping an action**
用户停止 Agent 执行后，整个会话（包括原始 prompt 和编辑）被删除，导致工作丢失。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4477)

**#4474 [OPEN] General Chat silently archived after session resume timeout**
长时间运行的 General Chat 在 60 秒内无法恢复时被静默归档，侧边栏无恢复 UI。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4474)

**#4469 [OPEN] Orphaned permission.requested event replays on session resume**
长期运行的会话在恢复时重复触发旧的目录访问权限请求，导致无法dismiss的循环提示。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4469)

**#4468 [OPEN] `--server --stdio` 模式下 extension-host 进程不释放**
Windows 桌面应用托管的长生命周期服务器，每个会话会泄漏 4 个 extension-host 子进程。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4468)

### ⚙️ 其他值得关注（2 条）

**#4481 [OPEN] Copilot App 1.1.8 仍受旧组织策略限制**
即使 "GitHub Copilot app" 策略已启用，Copilot App 1.1.8 仍被 "Copilot CLI" 策略阻断。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4481)

**#4470 [OPEN] 请求添加列出运行中会话的命令**
希望新增类似 `claude agents --json` 的命令，查看本机所有运行中的 Copilot CLI 会话及其状态。
→ [查看 Issue](https://github.com/github/copilot-cli/issues/4470)

---

## 4. 重要 PR 进展

### #4476 [CLOSED] docs: document proposed custom-agent effort frontmatter (Option A)
作者：romanstetsenko | 创建：2026-08-13
文档 PR，为 Issue #2904  proposes Option A（独立 `effort` 字段，与 `model` 并列）添加 README 参考章节，覆盖现有 frontmatter 字段（name, description, model）及新增 effort 字段。
→ [查看 PR](https://github.com/github/copilot-cli/pull/4476)

---

## 5. 功能需求趋势

| 趋势方向 | 关注程度 | 说明 |
|----------|----------|------|
| **模型配置精细化** | 🔴 高 | 多个 Issue 涉及 reasoning effort、模型选择、跨平台配置兼容性问题 |
| **MCP 稳定性** | 🔴 高 | OAuth 认证、并发刷新、错误重试、服务器发现等问题集中爆发 |
| **会话持久化** | 🔴 高 | 会话停止丢失、权限请求重放、长时间运行稳定性 |
| **权限系统改进** | 🟡 中 | 目录权限配置不生效、静默拒绝消息丢失 |
| **插件/Agent 管理** | 🟡 中 | TUI 显示问题、disabled 状态不持久化 |
| **跨应用策略一致性** | 🟡 中 | Copilot App 与 CLI 策略隔离问题 |

---

## 6. 开发者关注点

**高频痛点 Top 5：**

1. **Reasoning Effort 配置缺失** — 自定义 Agent 无法按 Agent 粒度设置 reasoning effort，仅支持全局 flag。社区已有 PR 推进实现（#2904，20 👍）。

2. **MCP OAuth 认证不稳定** — 多个独立 Issue 指向同一类问题：silent refresh 失败、并发刷新导致请求取消、临时 5xx 无重试。这是当前 MCP 生态最突出的技术障碍。

3. **会话状态管理缺陷** — 停止执行丢失 prompt、权限请求孤儿事件重放、长时间运行会话资源泄漏。影响核心用户体验。

4. **模型配置被静默覆盖** — `explore` 工具硬编码模型、code-review 子 Agent 配置忽略，破坏用户预期。

5. **平台差异** — Windows 特有 socket 错误、进程泄漏，以及 CLI 与 VS Code 扩展的 frontmatter 语法不一致。

---

**本期总结**：v1.0.80 带来 MCP 重新启用功能，但社区反馈显示 MCP OAuth、会话管理和模型配置仍是主要痛点。建议开发者关注 #2904 和 #4476 的后续实现进展，以及 MCP 相关 Issue 的修复状态。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-08-14** | 数据来源：github.com/MoonshotAI/kimi-cli

---

## 1. 今日速览

过去24小时内，Kimi Code CLI 无新版本发布，但社区活跃度依然较高，共更新 3 条 Issues。用户反馈集中在**流式响应稳定性**（ACP 模式挂死问题）和**异常生成长度控制**两个关键痛点，同时 Memory System 长期功能需求持续获得关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 社区热点 Issues

### #1283 [Feature Request] Memory System - Persistent context across sessions
- **作者**: CatKang | **更新**: 2026-08-13 | **评论**: 38
- **重要性**: 跨会话持久化上下文是 CLI 工具实现"记住用户偏好和项目模式"的核心能力，直接影响长期使用体验。该 Issue 创建时间较长（2026-02-27），累积 38 条评论，社区关注度持续。
- **社区反应**: 需求呼声较高，用户期望同时支持自动记忆（AI 管理）和手动记忆（用户自定义指令）。
- **链接**: [MoonshotAI/kimi-cli Issue #1283](https://github.com/MoonshotAI/kimi-cli/issues/1283)

### #2598 [Bug] ACP/print 流式响应静默挂死
- **作者**: ai-agent-workbench | **创建**: 2026-08-09 | **更新**: 2026-08-13 | **评论**: 1
- **重要性**: 该 Bug 导致 ACP 模式下流式响应内容完整到达后终端帧（`[DONE]`）始终不来，CLI 无限等待且无超时机制。更严重的是，挂死期间的新消息会静默顶替轮次，已流式内容**从未写入 wire.jsonl**，影响会话数据完整性。
- **社区反应**: 用户反馈问题复现偶发但影响严重，当前 0.31.1 仅覆盖 Esc 场景，未解决根本问题。
- **链接**: [MoonshotAI/kimi-cli Issue #2598](https://github.com/MoonshotAI/kimi-cli/issues/2598)

### #2597 [Bug] Runaway garbled generation — 88k tokens of gibberish
- **作者**: kdp123 | **创建**: 2026-08-08 | **更新**: 2026-08-13 | **评论**: 1
- **重要性**: 模型单次 LLM step 运行 **3214 秒（约 53 分钟）**，输出 **88,114 tokens** 的无意义乱码，暴露输出长度控制和异常检测机制缺失。
- **社区反应**: 该问题影响资源浪费和用户体验，用户希望设置合理的 token 上限和步长限制。
- **链接**: [MoonshotAI/kimi-cli Issue #2597](https://github.com/MoonshotAI/kimi-cli/issues/2597)

---

## 4. 重要 PR 进展

过去 24 小时内无新 PR 更新。

---

## 5. 功能需求趋势

从当前 Issues 中可提炼出以下社区关注方向：

| 方向 | 描述 |
|------|------|
| **上下文持久化** | Memory System 需求持续，用户希望 CLI 能记住项目模式、用户偏好，降低重复配置成本 |
| **流式响应稳定性** | ACP 模式下的连接超时、帧同步、异常恢复机制是开发者高频痛点 |
| **输出质量控制** | 需要更严格的 token 上限、步长限制和异常检测，防止 runaway generation |

---

## 6. 开发者关注点

**核心痛点：**
1. **流式响应挂死无超时**：ACP 模式下内容发完后连接静默挂死，无空闲超时配置项，且挂死期间的轮次数据无法恢复。
2. **异常生成长度失控**：单次 step 输出 88k+ tokens 且持续 53 分钟，暴露生成控制和异常检测机制薄弱。
3. **Memory System 长期需求**：跨会话上下文持久化是 CLI 进阶功能的关键，社区期待官方支持自动记忆和手动记忆双模式。

**建议关注：**
- 流式响应的超时配置和错误恢复机制
- 输出 token 上限和步长限制的配置项
- Memory System 的实现方案和时间表

---

*报告生成时间：2026-08-14* | *数据截至：2026-08-13 24:00 UTC*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>



# OpenCode 社区动态日报
**日期：2026-08-14**  
**仓库：** [anomalyco/opencode](https://github.com/anomalyco/opencode)

---

## 1. 今日速览

今天社区重点集中在 **V2 启动性能优化** 和 **安全问题修复** 两个方向。Kit Langton 发起了一轮大规模懒加载重构，涉及 semver、npm 配置、MCP 客户端、HTML 解析等核心模块，显著减少启动开销。同时，安全研究者连续提交了三条安全相关 Issue（升级管道 curl|bash、Context 裁剪完整性、webfetch SSRF），引起关注。桌面端启动失败和二进制自删除问题也亟待解决。

---

## 2. 版本发布

过去 24 小时内 **无新 Release**。

---

## 3. 社区热点 Issues

### 🔴 高优先级 Bug / 安全

| # | 标题 | 评论 | 👍 | 链接 |
|---|------|------|-----|------|
| #11112 | always stuck at "Preparing write..." | 78 | 46 | [Issue](https://github.com/anomalyco/opencode/issues/11112) |
| #42434 | [SECURITY] `opencode upgrade` curl|bash 无完整性校验 | 3 | 0 | [Issue](https://github.com/anomalyco/opencode/issues/42434) |
| #42437 | [SECURITY] Context pruning 静默丢弃指令内容 | 2 | 0 | [Issue](https://github.com/anomalyco/opencode/issues/42437) |
| #42435 | [SECURITY] webfetch 可访问回环/私有地址（SSRF） | 2 | 0 | [Issue](https://github.com/anomalyco/opencode/issues/42435) |
| #40516 | Desktop 应用启动时 provider/model/MCP 加载失败（回归） | 4 | 1 | [Issue](https://github.com/anomalyco/opencode/issues/40516) |
| #42441 | opencode 二进制文件自行消失 | 2 | 0 | [Issue](https://github.com/anomalyco/opencode/issues/42441) |

**重点说明：**
- **#11112** 是最活跃 Issue（78 评论、46 👍），自 2026-01-29 持续至今，写入工具执行反复中止，影响严重。
- **#42434 / #42437 / #42435** 三条安全 Issue 均由同一作者 shafqatevo 提交，涉及升级管道、上下文完整性和 SSRF，建议优先处理。
- **#40516** 明确标记为版本回归（v1.18.5–v1.18.13 均受影响），影响组织级用户。
- **#42441** 描述 pnpm 全局安装后二进制自行消失，与 #42411 为同一问题的重复提交。

### 🟡 体验与功能

| # | 标题 | 评论 | 👍 | 链接 |
|---|------|------|-----|------|
| #37012 | [FEATURE] 保留旧版布局选项 | 37 | 41 | [Issue](https://github.com/anomalyco/opencode/issues/37012) |
| #41470 | VSCode Server 中"已复制到剪贴板"不生效 | 15 | 1 | [Issue](https://github.com/anomalyco/opencode/issues/41470) |
| #33027 | MCP 工具已连接但未暴露给 agent | 8 | 3 | [Issue](https://github.com/anomalyco/opencode/issues/33027) |
| #42376 | 启动时同步 fetch models.dev 导致 10-30s 阻塞 | 2 | 0 | [Issue](https://github.com/anomalyco/opencode/issues/42376) |
| #42448 | [2.0] Compaction 请求超过上下文窗口 | 2 | 0 | [Issue](https://github.com/anomalyco/opencode/issues/42448) |

**重点说明：**
- **#37012** 社区呼声高（41 👍），用户希望保留旧版布局的可访问性优势。
- **#42376** 直接指向启动性能问题，与今天大量懒加载 PR 形成呼应。
- **#41470** 影响远程开发场景（Docker + VSCode Server）。

---

## 4. 重要 PR 进展

### ⚡ 性能与启动优化（Kit Langton 主导）

| # | 标题 | 状态 | 链接 |
|---|------|------|------|
| #42468 | perf(core): 懒加载 MCP 客户端 SDK | OPEN | [PR](https://github.com/anomalyco/opencode/pull/42468) |
| #42470 | refactor(cli): 懒加载 semver（更新检查） | OPEN | [PR](https://github.com/anomalyco/opencode/pull/42470) |
| #42469 | refactor(core): 延迟 WebFetch HTML 解析 | OPEN | [PR](https://github.com/anomalyco/opencode/pull/42469) |
| #42458 | perf(util): 懒加载 npm 配置 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42458) |
| #42467 | refactor(util): 懒加载 npm-package-arg | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42467) |
| #42460 | refactor(core): 移除 Bus.replayAll | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42460) |
| #42222 | refactor(util): 替换 xdg-basedir 依赖 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42222) |
| #40427 | [beta] V2 实验性性能优化合集 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/40427) |

### 🐛 Bug 修复

| # | 标题 | 状态 | 链接 |
|---|------|------|------|
| #42474 | fix(tui): resize 前刷新终端尺寸（重新提交） | OPEN | [PR](https://github.com/anomalyco/opencode/pull/42474) |
| #42330 | fix(tui): resize 前刷新终端尺寸（原始提交） | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42330) |
| #42456 | fix(tui): 隔离 Tab 滚动状态 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42456) |
| #42471 | fix(tui): 未读消息仅限聚焦终端 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42471) |
| #42466 | fix(tui): 通过 SEA-safe runtime import 加载本地插件 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42466) |

### 🧹 清理与维护

| # | 标题 | 状态 | 链接 |
|---|------|------|------|
| #42464 | chore(app): 移除陈旧前端依赖 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42464) |
| #42465 | chore(ui): 移除陈旧 motion pins | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42465) |
| #42463 | refactor(core): 移除未使用的 API 成员 | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42463) |
| #42459 | chore: 移除孤立 V2 exports | CLOSED ✅ | [PR](https://github.com/anomalyco/opencode/pull/42459) |
| #42472 | fix(www): 编辑链接指向 v2 分支 | OPEN | [PR](https://github.com/anomalyco/opencode/pull/42472) |

---

## 5. 功能需求趋势

从今日 Issues 和 PRs 中可提炼出以下社区关注方向：

| 方向 | 具体需求 | 相关 Issue / PR |
|------|----------|----------------|
| **启动性能** | 消除启动时同步网络请求、懒加载重型依赖 | #42376、#42468、#42470、#42469、#42458 |
| **安全加固** | 升级管道完整性校验、SSRF 防护、上下文裁剪安全 | #42434、#42435、#42437 |
| **V2 打磨** | Tab 滚动隔离、未读状态隔离、SEA 插件加载、compaction 边界处理 | #42456、#42471、#42466、#42448 |
| **多语言 / 国际化** | 新增希伯来语（he）支持（RTL） | #42447、#42475 |
| **布局选项** | 保留旧版布局作为可选项 | #37012 |
| **MCP 生态** | MCP 工具正确暴露、客户端懒加载 | #33027、#42468 |
| **远程开发** | VSCode Server / Docker 环境中剪贴板功能修复 | #41470 |

---

## 6. 开发者关注点

1. **写入冻结是头号痛点**：Issue #11112（"Preparing write..." 卡住）已持续近 7 个月，78 条评论，是社区最高关注 Bug，建议优先排查工具执行链路的异常中止逻辑。

2. **安全研究活跃**：shafqatevo 连续提交三条安全 Issue，覆盖升级管道（curl|bash）、上下文完整性和 SSRF，提示社区需要建立常规安全审计流程。

3. **V2 启动性能收到集中改进**：Kit Langton 今日一次性提交十余个 PR，围绕懒加载和依赖清理展开，直接回应 #42376 等启动阻塞反馈，是性能优化的重要里程碑。

4. **桌面端回归影响组织用户**：#40516 明确指出 v1.18.5–v1.18.13 存在启动加载回归，影响多用户场景，需尽快修复或回滚。

5. **V2 与 V1 共存问题**：#42260 和 #42421 反映 V2 对 V1 数据库的迁移破坏以及 TODO 工具缺失，双版本过渡期的兼容性问题仍需重视。

6. **pnpm 全局安装稳定性**：#42441 报告二进制自行消失，虽然被标记为重复，但揭示了 pnpm + post-install script 场景下的潜在风险。

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 — 2026-08-14

---

## 1. 今日速览

过去24小时无新版本发布，但社区活跃度极高，共新增 44 条 Issue 和 12 条 PR。**上下文自动压缩触发时机**（#6879）和 **TUI 大文本性能优化**（#8029/#8066）是最受关注的两个问题，涉及长时间 Agent 会话的实际痛点。同时，`--plan` 等布尔参数吞掉后续 prompt 的 Bug 已被修复（#8084），终端残留问题也得到系统性治理（#8082）。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 社区热点 Issues

| # | Issue | 热度 | 为什么值得关注 |
|---|-------|------|----------------|
| [#6879](https://github.com/earendil-works/pi/issues/6879) | auto-compaction 在上下文超 100% 后不触发 | 19 评论 · 17👍 | **最热门 Issue**。长时间 Agent 会话（>2h）中 footer 突破阈值，但 compaction 直到 API 报错才被触发，严重影响长对话体验。 |
| [#8029](https://github.com/earendil-works/pi/issues/8029) | prompt 编辑器大文本移动极慢 | 7 评论 · 0👍 | 7000 行文本下单次方向键延迟 1.65s，线性增长，直接阻碍大段 prompt 编辑。已有关联 PR #8066 修复。 |
| [#7791](https://github.com/earendil-works/pi/issues/7791) | Undici 继承 16KiB maxHeaderSize 导致响应被拒 | 6 评论 | 全局 fetch 因默认 16KiB header 限制丢弃合法大响应，影响后端提供商兼容性。已关闭。 |
| [#2366](https://github.com/earendil-works/pi/issues/2366) | Rate limiting 不生效 | 5 评论 | 企业环境 TPM 限速被绕过，社区长期痛点。今日关闭，可能已合并修复。 |
| [#7779](https://github.com/earendil-works/pi/issues/7779) | 信任用户共享 PI_CODING_AGENT_DIR | 5 评论 | 多用户环境下 `auth.json`/`models-store.json` 权限过严（0600），阻碍协作场景。 |
| [#7829](https://github.com/earendil-works/pi/issues/7829) | Windows 无效 settings.json 静默忽略 | 5 评论 | 路径转义错误导致 JSON 解析失败，却报 "bash not found" 误导用户，诊断体验差。已关闭。 |
| [#4254](https://github.com/earendil-works/pi/issues/4254) | 共享 jiti 实例加速扩展加载 | 4 评论 | 64 个扩展加载耗时 ~1100ms，建议用单例 + moduleCache 优化启动时间。已关闭。 |
| [#7960](https://github.com/earendil-works/pi/issues/7960) | /resume 进度计数不一致 | 4 评论 | 分母是文件数、分子是已解析 session 数，两者语义不同导致数字对不上，用户体验混乱。 |
| [#5065](https://github.com/earendil-works/pi/issues/5065) | /exit 后 kitty 键盘协议未重置 | 3 评论 | 关闭 TUI 后终端输入变成原始 escape 序列，终端 unusable，必须手动 reset。已关闭。 |
| [#7761](https://github.com/earendil-works/pi/issues/7761) | VTE 终端 TUI copy 复制失败 | 3 评论 | 双击选择文本后显示 "Copied!" 但剪贴板为空，影响日常复制操作。 |

---

## 4. 重要 PR 进展

| # | PR | 状态 | 内容摘要 |
|---|-----|------|----------|
| [#8084](https://github.com/earendil-works/pi/pull/8084) | fix: 布尔扩展标志不吞 prompt | ✅ Closed | 修复 `pi -p --plan "prompt"` 因吞掉后续参数而空跑退出的 Bug。 |
| [#8082](https://github.com/earendil-works/pi/pull/8082) | fix: 仅渲染可见视口 + SIGINT 恢复终端 | ✅ Closed | 大 session resume 不再刷新整个历史到终端；SIGINT 后正确恢复终端状态。 |
| [#8066](https://github.com/earendil-works/pi/pull/8066) | fix: 视觉行缓存减少重复计算 | 🔓 Open | 修复 #8029，通过缓存 visual lines 结果，解决大文本光标移动性能问题。 |
| [#8086](https://github.com/earendil-works/pi/pull/8086) | fix: Gemini 回退旧版工具 Schema | ✅ Closed | 部分 generativelanguage 端点拒绝 JSON Schema 扩展字段，修复后自动回退 legacy schema。 |
| [#8085](https://github.com/earendil-works/pi/pull/8085) | feat: Escape 取消鼠标选区 | 🔓 Open | 拖动选中文本时按 Escape 可清除选区而不复制到剪贴板，符合文本编辑习惯。 |
| [#8070](https://github.com/earendil-works/pi/pull/8070) | fix: 校验扩展 flag 默认值 | 🔓 Open | 防止 `registerFlag()` 中 type 与 default 不一致导致布尔 flag 返回真值字符串。 |
| [#7984](https://github.com/earendil-works/pi/pull/7984) | chore: grok-mermaid 升级至 0.2.3 | 🔓 Open | 解决 #7832，改进 mermaid 渲染支持。 |
| [#6216](https://github.com/earendil-works/pi/pull/6216) | feat: 新增 Amazon Bedrock Mantle provider | 🔓 Open | 支持 AWS Bedrock Mantle 的 OpenAI Responses API，扩展云厂商覆盖。 |
| [#8067](https://github.com/earendil-works/pi/pull/8067) | fix: 用户消息使用 APP_NAME | ✅ Closed | 统一用户界面字符串中的应用名称引用，便于重新打包场景。 |
| [#8057](https://github.com/earendil-works/pi/pull/8057) | fix: todo renderResult 校验错误处理 | 🔓 Open | 修复 schema validation 失败时 `renderResult` 返回 undefined 导致 TUI 崩溃的问题。 |

---

## 5. 功能需求趋势

从 Issue/PR 数据提炼出以下社区关注方向：

| 方向 | 相关 Issue/PR | 趋势说明 |
|------|---------------|----------|
| **长对话与上下文管理** | #6879, #7960, #8031 | 自动压缩时机、大 session resume、流式中断恢复是长时间 Agent 会话的核心痛点。 |
| **TUI 性能与终端体验** | #8029, #8066, #5065, #8080, #8082 | 大文本光标延迟、终端状态残留（kitty 协议、SIGINT）、大量历史刷屏被集中反馈，今日已有多个修复合并。 |
| **扩展/插件系统** | #4254, #7092, #8070, #8078 | 启动速度优化、工具 hook 设计、extension flag 校验、sourceInfo 元数据问题，扩展生态在加速演进。 |
| **多提供商/模型支持** | #6216, #8046, #7689, #8031 | AWS Bedrock、Grok 4.6 支持、Codex 流式终止重试、Anthropic refusal fallback 等，模型覆盖面持续扩大。 |
| **错误可观测性** | #7829, #8081, #8080 | 无效配置静默失败、未知命令被转发、SIGINT 残留等体验问题，诊断清晰度被反复提及。 |

---

## 6. 开发者关注点

**高频痛点 Top 5：**

1. **上下文压缩时机错误** — 当前实现仅在 API 返回超限报错后才触发，期望在每轮 agent turn 后检查并主动压缩（#6879，17👍，社区呼声最高）。
2. **大文本交互卡顿** — prompt 编辑器在数千行文本时性能线性退化，视觉行计算缓存是正确方向（#8029 → #8066）。
3. **终端状态残留** — SIGINT、`/exit`、大 session resume 后终端进入异常状态（kitty 协议未重置、历史刷屏），需系统性修复（#5065, #8080, #8079, #8082）。
4. **Windows 配置静默失效** — JSON 路径转义错误不报错而直接忽略，转而抛出误导性的 "bash not found"（#7829）。
5. **CLI 参数解析 Bug** — 布尔 flag（如 `--plan`）吞掉后续 positional argument，导致空 prompt 启动（#8084），扩展 flag 注册也需要类型校验（#8070）。

**积极信号：** 今日多个长期 Issue（#7791, #2366, #7829, #5065）已关闭，说明社区在 TUI 稳定性和错误处理方面正在快速迭代。

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报 — 2026-08-14

---

## 1. 今日速览

Qwen Code **v0.21.11** 正式版发布，新增 Agent Plugins v1 扩展能力和原生多 Agent 协调工作流（`/coordinate` 命令）。过去 24 小时内，围绕 Windows 平台兼容性（Ctrl+V 粘贴回归、Desktop 终端异常）和 Web Shell 稳定性修复了多项关键问题，同时 Omni 多模态实验与多 Agent Fleet 架构进入密集开发期。

---

## 2. 版本发布

### v0.21.11（正式版）
- **Agent Plugins v1**：支持通过插件扩展 Agent 能力（[#8834](https://github.com/QwenLM/qwen-code/pull/8834)）
- **原生多 Agent 工作流**：通过 `/coordinate` 命令启用只读队友协同（[#8804](https://github.com/QwenLM/qwen-code/pull/8804)）
- **SWE-bench Verified 基准测试**：当前状态为 **QUARANTINED**（隔离中）

### v0.21.12-preview.1 / v0.21.11-nightly.20260814
- 修复 Web Shell standalone session target 保留问题（[#9038](https://github.com/QwenLM/qwen-code/pull/9038)）
- 新增 Web Shell workspace 文件上传支持

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 关注理由 |
|---|------|------|----------|
| [#8718](https://github.com/QwenLM/qwen-code/issues/8718) | RFC: Native coordination for independent Qwen sessions | CLOSED | 多 Agent 协调架构总纲，已实现并关闭，是 Fleet 功能的基石 |
| [#8678](https://github.com/QwenLM/qwen-code/issues/8678) | fix(serve): Preserve session when large restore times out | OPEN | P1 级会话恢复超时保护，已合并 PR #8691，影响 daemon 稳定性 |
| [#7118](https://github.com/QwenLM/qwen-code/issues/7118) | Windows standalone installer fails (Get-FileHash) | CLOSED | Windows 安装经典问题，已修复（3👍） |
| [#9019](https://github.com/QwenLM/qwen-code/issues/9019) | Gemini 2.5 models unusable on Vertex AI | OPEN | P2 级，`thinkingLevel` 参数导致所有请求 400 错误，影响 Gemini 用户 |
| [#9025](https://github.com/QwenLM/qwen-code/issues/9025) | Keyless Vertex AI not inferred from environment | OPEN | P2 级，headless 模式下 ADC 认证无法自动选择，影响无密钥部署 |
| [#9061](https://github.com/QwenLM/qwen-code/issues/9061) | Ctrl+V paste unresponsive in CLI on Windows | OPEN | **P1 回归**：0.21.x 引入，Windows CLI 粘贴完全失效，降级 0.21.0 可恢复 |
| [#8586](https://github.com/QwenLM/qwen-code/issues/8586) | Track activeWork and background Agent recovery | OPEN | 后台 Agent 恢复路径追踪，Daemon 健康监控的关键功能 |
| [#8845](https://github.com/QwenLM/qwen-code/issues/8845) | Web Shell: redesign Channel/session/workspace | OPEN | Web Shell 架构重构，影响所有 Web Shell 用户 |
| [#9083](https://github.com/QwenLM/qwen-code/issues/9083) | record_artifact succeeds without verifying workspacePath | OPEN | P2 级，artifact 状态不一致导致模型误报文件可访问 |
| [#9088](https://github.com/QwenLM/qwen-code/issues/9088) | read_file sends non-image as .png to model API | OPEN | P2 级，基于扩展名而非实际内容发送文件，导致 400 错误中断对话 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|------|------|------|
| [#9107](https://github.com/QwenLM/qwen-code/pull/9107) | feat(telemetry): Trace main agent invocations | OPEN | 新增主 Agent 调用链路追踪，增强可观测性 |
| [#9040](https://github.com/QwenLM/qwen-code/pull/9040) | fix(cli): prevent dialog clipping in short terminals | OPEN | 修复 `/statusline` 和 `/skills` 在矮终端中被截断的问题 |
| [#8890](https://github.com/QwenLM/qwen-code/pull/8890) | refactor(cli): Generalize Conversations runtime | OPEN | 重构 Conversations 运行时基础，为多 Agent 架构铺路 |
| [#8677](https://github.com/QwenLM/qwen-code/pull/8677) | feat(tui): OpenTUI renderer backend | OPEN | 全新 TUI 渲染后端，支持鼠标交互、无闪烁 |
| [#9106](https://github.com/QwenLM/qwen-code/pull/9106) | feat: consolidate Local Control into daemon | OPEN | 将 LAN 配对流程统一到 Daemon，消除双实现 |
| [#8899](https://github.com/QwenLM/qwen-code/pull/8899) | fix(autofix): hold rounds while review-pr in flight | CLOSED | 修复 autofix 与 review-pr 的自取消循环问题 |
| [#9039](https://github.com/QwenLM/qwen-code/pull/9039) | feat(core): privacy-safe tool-result boundary diagnostics | OPEN | 隐私安全的工具结果边界诊断 |
| [#9086](https://github.com/QwenLM/qwen-code/pull/9086) | fix(review): harden pipeline against four live-run failures | OPEN | 修复 `/review` 管道中 4 个真实 PR 测试发现的缺陷 |
| [#8853](https://github.com/QwenLM/qwen-code/pull/8853) | fix(web-shell): surface loop detection turn errors | OPEN | 将工具循环检测转为结构化错误，提升 Web Shell 用户体验 |
| [#8332](https://github.com/QwenLM/qwen-code/pull/8332) | feat(cli): add audio bridge for attachments | OPEN | 为不支持音频的模型添加音频桥接，通过转录模型处理附件 |

---

## 5. 功能需求趋势

1. **多 Agent / Fleet 协作**：`/coordinate` 命令、Fleet Stage 1A-3、后台 Agent 恢复追踪已形成完整功能线，社区关注度高。
2. **Web Shell 体验升级**：Channel 重设计、文件上传、循环检测错误提示、外部链接修复等多 PR 同步推进。
3. **Omni 多模态实验**：S4a-S6 系列 Issue（[#8186](https://github.com/QwenLM/qwen-code/issues/8186)-[#8197](https://github.com/QwenLM/qwen-code/issues/8197)）持续推进三模态 Policy 链路和 Memory 管理。
4. **可观测性增强**：OpenTelemetry 集成（[#9084](https://github.com/QwenLM/qwen-code/pull/9084)）、Agent 调用追踪（[#9107](https://github.com/QwenLM/qwen-code/pull/9107)）受关注。
5. **autofix / review 流程改进**：非收敛 diff 升级维护者（[#9104](https://github.com/QwenLM/qwen-code/pull/9104)）、review 管道健壮性增强（[#9086](https://github.com/QwenLM/qwen-code/pull/9086)）。
6. **Windows 平台稳定性**：粘贴回归、安装失败、Desktop 终端异常等高频问题持续修复中。

---

## 6. 开发者关注点

| 痛点 / 需求 | 涉及 Issue / PR |
|------------|----------------|
| **Windows Ctrl+V 粘贴回归**（0.21.x 引入） | [#9061](https://github.com/QwenLM/qwen-code/issues/9061) |
| **Gemini 2.5 / Vertex AI 兼容性问题** | [#9019](https://github.com/QwenLM/qwen-code/issues/9019), [#9025](https://github.com/QwenLM/qwen-code/issues/9025) |
| **Web Shell 链接打开失败** | [#9108](https://github.com/QwenLM/qwen-code/issues/9108) → 已合并 [#9111](https://github.com/QwenLM/qwen-code/pull/9111) |
| **autofix 与 review-pr 自取消循环** | [#8888](https://github.com/QwenLM/qwen-code/issues/8888) → 已合并 [#8899](https://github.com/QwenLM/qwen-code/pull/8899) |
| **文件操作边界情况**（扩展名 vs 实际内容） | [#9083](https://github.com/QwenLM/qwen-code/issues/9083), [#9088](https://github.com/QwenLM/qwen-code/issues/9088) |
| **Desktop 项目列表 UI 抖动** | [#8985](https://github.com/QwenLM/qwen-code/issues/8985) |
| **压缩 side-query 在短上下文窗口超界** | [#7960](https://github.com/QwenLM/qwen-code/issues/7960) |
| **pinned memory 目录保护需求** | [#6801](https://github.com/QwenLM/qwen-code/issues/6801) |
| **npm update 后暴露 2 个高危漏洞** | [#8944](https://github.com/QwenLM/qwen-code/issues/8944) |
| **跨 worktree Git 操作安全保护** | [#8687](https://github.com/QwenLM/qwen-code/pull/8687) |

---

*数据来源：github.com/QwenLM/qwen-code，统计时段 2026-08-13 至 2026-08-14*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI 社区动态日报
**日期：2026-08-14 | 数据来源：github.com/Hmbown/DeepSeek-TUI**

---

## 1. 今日速览

CodeWhale v0.9.7 正式发布，同时项目完成从 `deepseek-tui` 到 `codewhale` 的品牌迁移，旧 npm 包已弃用。社区活跃度高，过去 24 小时新增 50 个 Issues 和 27 个 PR，主要聚焦于 DS4 本地部署支持、Auto-Review 模型守护层、以及终端窗口管理功能。

---

## 2. 版本发布

### v0.9.7 — 品牌迁移与产品重命名
- **Codewhale** 成为 Shannon Labs 的公开产品名称
- `codewhale` 命令、npm 包和发布资产名保持小写
- 旧版 npm 包 `deepseek-tui` 已弃用，不再发布新版本
- 兼容 v0.8.x 遗留的 `deepseek` / `d` 命令别名

---

## 3. 社区热点 Issues

| # | 标题 | 重要性 | 评论 | 链接 |
|---|------|--------|------|------|
| #998 | 文案展示不全，希望鼠标悬停显示完整内容 | 中文用户高频反馈，影响阅读体验 | 11 | [Issue](https://github.com/Hmbown/CodeWhale/issues/998) |
| #1004 | `/dryrun` 命令：预览即将发送的请求 | 调试长对话的关键功能，避免误发送 | 9 | [Issue](https://github.com/Hmbown/CodeWhale/issues/1004) |
| #5324 | 简化 agent 工具的 32 字段 schema | 模型报错根因，影响多动作支持 | 7 | [Issue](https://github.com/Hmbown/CodeWhale/issues/5324) |
| #2369 | Config 路径在 Windows/Cygwin 下碎片化 | 跨平台迁移 bug，配置丢失风险 | 7 | [Issue](https://github.com/Hmbown/CodeWhale/issues/2369) |
| #1425 | 大文本处理会话卡死（agent_wait 超时） | 多 Agent 协作场景的稳定性问题 | 6 | [Issue](https://github.com/Hmbown/CodeWhale/issues/1425) |
| #894 | 执行过程中图片显示混乱 | UI 渲染 bug，影响多模态体验 | 6 | [Issue](https://github.com/Hmbown/CodeWhale/issues/894) |
| #5316 | EPIC-005: TUI Crate 分解总纲 | 架构重构里程碑，影响长期可维护性 | 5 | [Issue](https://github.com/Hmbown/CodeWhale/issues/5316) |
| #1917 | PreToolUse/PostToolUse 钩子层提案 | 统一取消/暂停/恢复的生命周期管理 | 5 | [Issue](https://github.com/Hmbown/CodeWhale/issues/1917) |
| #5374 | Agent 写作时文本乱码（macOS） | 新报告，立即影响中文用户 | 3 | [Issue](https://github.com/Hmbown/CodeWhale/issues/5374) |
| #5340 | `doctor` 命令卡在 `needs action` 状态 | 升级后首次运行问题，阻碍激活 | 2 | [Issue](https://github.com/Hmbown/CodeWhale/issues/5340) |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 功能说明 | 链接 |
|---|------|------|----------|------|
| #5365 | 新增 DS4 本地提供商支持 | OPEN | 一键配置 DwarfStar 本地 DeepSeek V4 路由 | [PR](https://github.com/Hmbown/CodeWhale/pull/5365) |
| #5353 | Auto-Review 模型守护层 | OPEN | v0.9.8 双护层架构，拒绝理由透明化 | [PR](https://github.com/Hmbown/CodeWhale/pull/5353) |
| #5369 | 降级 Moonshot schema 拒绝逻辑 | OPEN | 修复条件性拒绝，改为优雅降级 | [PR](https://github.com/Hmbown/CodeWhale/pull/5369) |
| #5368 | 隔离测试环境状态 | OPEN | 修复 4 个因读取真实状态而失败的测试 | [PR](https://github.com/Hmbown/CodeWhale/pull/5368) |
| #5339 | 抑制子进程 shell 补全 | OPEN | 过滤子任务补全事件，保留父任务可见性 | [PR](https://github.com/Hmbown/CodeWhale/pull/5339) |
| #5364 | Markdown 引用块渲染优化 | ✅ CLOSED | 新增引用线，支持嵌套和格式化 | [PR](https://github.com/Hmbown/CodeWhale/pull/5364) |
| #5358 | Auto-Review 拒绝理由 + 熔断器 | ✅ CLOSED | 首次 P0 修复，防止模型无限重试 | [PR](https://github.com/Hmbown/CodeWhale/pull/5358) |
| #5333 | 终端窗口置顶迷你模式 | ✅ CLOSED | Windows 支持 `/pin` 命令，640x400 始终置顶 | [PR](https://github.com/Hmbown/CodeWhale/pull/5333) |
| #5336 | MCP nextCursor 修复 | ✅ CLOSED | 移除无效 null 值，符合 MCP 规范 | [PR](https://github.com/Hmbown/CodeWhale/pull/5336) |
| #5326 | 网站 i18n 审计修复 | ✅ CLOSED | 修复文档引用和测试断言 | [PR](https://github.com/Hmbown/CodeWhale/pull/5326) |

---

## 5. 功能需求趋势

基于 Issues 和 PRs 分析，社区最关注的功能方向：

1. **本地模型部署** — DS4（DwarfStar）本地路由成为新焦点，用户希望简化本地 DeepSeek V4 配置流程
2. **多 Agent 协作稳定性** — 大文本处理、子 Agent 超时、会话卡死是高频痛点
3. **跨平台兼容性** — Windows/Cygwin 配置路径、FreeBSD 支持、macOS 乱码问题
4. **审查与安全机制** — Auto-Review 双护层、角色权限控制、工具调用钩子
5. **终端体验优化** — 文字渲染、引用块显示、窗口置顶、快捷键自定义
6. **远程工作区** — CNB/飞书/Telegram 多通道整合，US 地区云服务商支持

---

## 6. 开发者关注点

### 高频痛点
- **配置迁移问题**：v0.8.x → v0.9.x 升级后，config 路径在不同 OS 下解析不一致，导致配置丢失
- **多 Agent 超时**：`agent_wait` 等待子 Agent 完成时缺乏有效超时机制，导致会话假死
- **中文渲染**：macOS 和 Windows 上中文/繁体中文在 Agent 输出中显示乱码
- **JSON Schema 复杂度**：32 字段 schema 导致模型频繁报错，需简化或拆分

### 社区建议
- 增加 `/dryrun` 命令预览请求内容，避免误发送长对话
- 支持可配置的模型可见大小限制，适配自托管长上下文模型
- 提供多行输入模式和可自定义的发送快捷键
- 改进 VS Code 集成稳定性，防止 YOLO Agent 运行时崩溃

---

**报告生成时间**：2026-08-14 | **分析师**：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*