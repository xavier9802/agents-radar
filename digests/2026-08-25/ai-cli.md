# AI CLI 工具社区动态日报 2026-08-25

> 生成时间: 2026-08-25 01:39 UTC | 覆盖工具: 10 个

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
**日期：2026-08-25 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026年8月下旬，AI CLI工具生态呈现**"功能爆发、稳定性承压"**的阶段性特征。多代理（Multi-Agent）架构已成为主流技术路线，但子代理可靠性、长会话上下文管理、跨Provider认证链路仍是各工具社区的共同痛点。开源工具（Gemini CLI、Qwen Code、DeepSeek TUI、Pi）在迭代速度和定制化灵活性上紧追商业产品，而Claude Code与Copilot CLI作为成熟产品则在稳定性修复与企业级功能（MCP集成、成本透明化）上持续投入。整体来看，行业正从"功能竞赛"转向"可靠性与可观测性"的阶段。

---

## 2. 各工具活跃度对比

| 工具 | 今日Issues | 今日PR | Release | 活跃度评级 |
|------|-----------|--------|---------|-----------|
| **Qwen Code** | ~50新增 | ~20 | v0.22.0-nightly | 🔥🔥🔥🔥🔥 |
| **OpenAI Codex** | ~10热点 | ~10+已关闭 | rust-v0.150.0-alpha.8 | 🔥🔥🔥🔥 |
| **Gemini CLI** | ~10热点 | ~8（4合入） | v0.56.0-nightly / v0.57.0-preview.1 | 🔥🔥🔥🔥 |
| **Claude Code** | ~10热点 | 3 | v2.1.243 | 🔥🔥🔥 |
| **GitHub Copilot CLI** | ~10热点 | 1 | v1.0.81-9 | 🔥🔥🔥 |
| **Pi** | ~8热点 | ~10（4今日合入） | v0.84.3 | 🔥🔥🔥 |
| **DeepSeek TUI** | ~10热点 | ~8 | v0.9.12（开发中） | 🔥🔥🔥 |
| **Kimi Code CLI** | 0 | 1 | 无 | 🔥 |
| **Grok Build** | 0 | 0 | 无 | — |
| **OpenCode** | — | — | 摘要失败 | — |

> 注：Qwen Code以50+ Issues/20+ PRs显著领先；Kimi Code与Grok Build过去24小时基本无社区动态。

---

## 3. 共同关注的功能方向

| 功能方向 | 涉及工具 | 具体诉求 |
|----------|----------|----------|
| **MCP/OAuth认证稳定性** | Claude Code、Codex、Copilot CLI、Gemini CLI、Qwen Code | RFC 8414兼容、刷新令牌失效、session cookie丢失、Entra ID/Atlassian集成失败；Copilot CLI #4490/#4582 明确指向scope参数缺失与跨源标识问题 |
| **多代理/子代理可靠性** | Codex、Gemini CLI、Copilot CLI、DeepSeek TUI | 子代理挂起（Gemini #21409）、 prematurely 报告成功（Gemini #22323）、资源泄漏（Codex #39694）、静默取消（DeepSeek #5596） |
| **Memory/上下文管理** | Claude Code、Gemini CLI、DeepSeek TUI、Pi | auto-memory加载透明度不足（Claude #82056）、低信号会话无限重试（Gemini #26522）、跨会话记忆断裂（DeepSeek #2492）、压缩触发时机缺陷（Pi #6879） |
| **长会话上下文压缩** | Codex、Pi、Qwen Code | 按模型精细配置压缩参数（Pi #8133，已PR #8592修复）、上下文超100%后压缩不触发（Pi #6879）、headless运行静默失败（Qwen #9026） |
| **跨平台兼容性** | Claude Code、Codex、Gemini CLI、Pi、DeepSeek TUI | Claude Code Linux segfault（glibc 2.44 + mimalloc）；Codex Windows沙箱/内核崩溃；Gemini Wayland browser agent失效；DeepSeek Windows shell编码乱码 |
| **成本透明化** | Copilot CLI、DeepSeek TUI、Qwen Code | 子代理OTel spans缺少计费属性（Copilot #4224）；MCP工具token成本估算展示（DeepSeek #5603）；非Anthropic模型空prompt消耗47k vs Claude 21k（Copilot #4588） |
| **可观测性与监督操作** | DeepSeek TUI、Pi、Codex | 控制套接字（DeepSeek #5594）、生命周期事件外发JSONL（DeepSeek #5592）、中断hooks补全（Codex #40511）、agent审批持久化（DeepSeek #5584） |

---

## 4. 差异化定位分析

| 工具 | 功能侧重 | 目标用户 | 技术路线 |
|------|----------|----------|----------|
| **Claude Code** | 功能完整性（/usage分解、modelPicker自定义、auto-memory） | 企业级开发者、Anthropic生态用户 | TypeScript/Node.js，bundled mimalloc，Desktop+CLI双端 |
| **OpenAI Codex** | TUI体验打磨（线程标题生成、系统线程隐藏、路径折叠）、Rust CLI重构 | OpenAI生态用户、TUI偏好者 | Rust（rust-v0.150.0-alpha.x），SQLite持久化架构 |
| **Gemini CLI** | 多代理架构（Generalist/Subagent）、安全检测器声明、A2A服务器管理 | Google生态用户、研究型开发者 | TypeScript，A2A协议，preview/nightly双轨发布 |
| **GitHub Copilot CLI** | GitHub生态集成（worktree、PR关联）、MCP OAuth认证、企业SSO | GitHub用户、企业IT管理员 | TypeScript，深度集成GitHub API与MCP生态 |
| **Pi** | 本地模型集成（llama.cpp preset可见性）、跨Provider兼容（OpenAI兼容层）、Windows PowerShell原生支持 | 本地部署用户、多云 Provider 混合用户 | Rust/TypeScript混合，支持llama.cpp/Bedrock/Mantle等 |
| **Qwen Code** | 中国生态集成（钉钉工作区频道）、代码审查增强（容器隔离、执行级验证）、TUI性能优化 | 中国开发者、钉钉企业用户 | TypeScript，openTUI渲染层迁移，cua-driver-rs跨平台 |
| **DeepSeek TUI** | 多提供商中立化（18处DeepSeek专属逻辑审计）、监督操作栈（控制套接字、生命周期事件）、成本可视化 | 技术爱好者、自动化/长时间运行场景用户 | Rust，Fleet多模型编排，Unix JSON-RPC套接字 |
| **Kimi Code CLI** | 文件编码安全（非UTF-8拒绝编辑） | 中文开发者、Moonshot生态用户 | 动态相对静止，聚焦基础稳定性 |

---

## 5. 社区热度与成熟度

| 级别 | 工具 | 特征 |
|------|------|------|
| **🔥 高活跃+快速迭代** | Qwen Code、Gemini CLI、DeepSeek TUI | Issues/PR吞吐量大，nightly/preview双轨或集成冲刺，功能创新密集（钉钉集成、A2A服务器、监督操作栈） |
| **🔥🔥 活跃+问题集中** | OpenAI Codex、Pi | Codex认证bug引发百条评论；Pi今日3个核心PR同日合入（流超时、压缩参数、签名透传），修复节奏快 |
| **🔥🔥🔥 成熟+稳定性承压** | Claude Code、Copilot CLI | 功能完善但遭遇平台级回归（Claude Linux segfault、Copilot MCP OAuth）；社区投票长期痛点（Claude Windows Desktop工作目录）久未解决 |
| **⏸ 低活跃/观察期** | Kimi Code CLI、Grok Build | 过去24小时无显著动态，可能处于功能沉淀期或用户基数较小 |

---

## 6. 值得关注的趋势信号

### 信号一：MCP认证标准化成为行业瓶颈
Copilot CLI (#4490, #4582)、Claude Code (#84614)、Qwen Code (#9944) 均报告MCP OAuth认证链路问题，涉及RFC 8414 §3.3兼容、scope参数缺失、refresh_token服务端失效。这表明**MCP生态尚未形成稳定的认证标准**，企业用户（尤其Entra ID/Azure AD环境）部署阻力大。对开发者建议：选择工具时优先考察其MCP实现是否遵循标准流程，避免被特定厂商的私有扩展锁定。

### 信号二：多代理可靠性从"概念验证"走向"生产门槛"
Gemini CLI (#22323, #21409)、Codex (#39694)、DeepSeek (#5596) 集中暴露子代理挂起、 prematurely 成功报告、资源泄漏等问题。随着各工具纷纷引入MultiAgent架构，**代理生命周期管理的健壮性**已成为区分"玩具"与"生产力工具"的关键指标。对开发者建议：在复杂任务场景中，优先选择提供代理审批持久化（DeepSeek #5584）与细粒度超时控制（Pi #8593）的工具。

### 信号三：成本透明化从"可选项"变为"刚需"
Copilot CLI #4588 揭示非Anthropic模型空prompt消耗47k token（Claude仅21k），DeepSeek #5603 提案MCP工具成本可视化，Copilot #4224 指出子代理OTel spans缺失计费属性。随着agent调用链拉长，**token成本不可见将直接导致预算失控**。对开发者建议：优先选择提供turn成本指标（Codex #40488已合入）、MCP schema成本估算（DeepSeek #5603）的工具，并建立内部成本监控。

### 信号四：本地模型集成加速，"云端+本地"混合架构兴起
Pi今日合入llama.cpp preset可见性修复（#8479、#6922、#8167），Gemini CLI提议Zero-Dependency OS Sandboxing（#19873），DeepSeek TUI推进多提供商中立化（#5588）。这反映用户**对数据主权、离线可用性、成本控制的复合需求**。对开发者建议：关注支持本地模型回退的工具链，评估在敏感场景下混合部署的可行性。

### 信号五：监督操作栈（Supervision Stack）成为长时Agent的基建
DeepSeek TUI v0.9.12集成控制套接字（#5594）、生命周期事件外发（#5592）、`/relaunch`命令（#5593）、子代理审批持久化（#5584），形成完整的监督能力。Codex亦新增Interrupt hook（#40511）。这表明**行业正从"黑盒agent"向"可观测、可干预、可恢复"的agent演进**。对开发者建议：在生产环境部署agent时，优先选择提供控制套接字或生命周期事件钩子的工具，以便集成外部监控系统。

---

*报告生成时间：2026-08-25 | Agnes (Sapiens AI)*

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)



# Claude Code Skills 社区热点报告
**数据截止：2026-08-25 | 分析师：Agnes**

---

## 1. 热门 Skills 排行（按关注度）

### ① skill-creator 评估工具链修复（系列 PR）
- **涉及 PR**：[#1298](https://github.com/anthropics/skills/pull/1298)、[#1099](https://github.com/anthropics/skills/pull/1099)、[#1050](https://github.com/anthropics/skills/pull/1050)、[#539](https://github.com/anthropics/skills/pull/539)
- **功能**：修复 `run_eval.py` / `run_loop.py` 在 Windows 下的触发检测失效、YAML 解析静默截断等核心缺陷
- **社区热点**：Issue #556 报告 10+ 独立复现，precision=100% / recall=0% 导致描述优化循环在噪声上优化，严重影响 Skill 创作者体验
- **状态**：全部 OPEN，待合并

### ② Hivemind：零成本多智能体编排
- **PR**：[#1628](https://github.com/anthropics/skills/pull/1628)
- **功能**：让 Claude Code 将机械性工作委派给无头 opencode 工人（免费模型），Claude 保持唯一规划者/审查者/合并者角色
- **社区热点**：直击"昂贵模型上下文是稀缺资源"痛点，近期提交（08-21），潜力高
- **状态**：OPEN

### ③ self-audit：机械验证 + 四维度推理质量门
- **PR**：[#1367](https://github.com/anthropics/skills/pull/1367)
- **功能**：交付前审计 AI 输出——先机械文件验证，再按损害严重度优先级做四维度推理审计，跨项目/技术栈通用
- **社区热点**：配套 Issue #1385 提出三阶段流水线（Pre-task Calibration → Adversarial Review → Delivery Verification），形成完整质量治理体系
- **状态**：OPEN

### ④ skill-quality-analyzer & skill-security-analyzer
- **PR**：[#83](https://github.com/anthropics/skills/pull/83)
- **功能**：两个元技能，分别从结构/文档、质量五维度、安全性评估 Skill 本身
- **社区热点**：呼应 Issue #412（Agent Governance 提议），反映社区对 Skill 生态质量和治理的强烈需求
- **状态**：OPEN

### ⑤ document-typography：文档排版质量管控
- **PR**：[#514](https://github.com/anthropics/skills/pull/514)
- **功能**：修复 AI 生成文档中的孤行、寡行、编号错位等排版问题
- **社区热点**：结合 Issue #12（docx 空白格式化问题），反映文档技能用户基数大、痛点集中
- **状态**：OPEN

### ⑥ ServiceNow 平台全栈技能
- **PR**：[#568](https://github.com/anthropics/skills/pull/568)
- **功能**：覆盖 ITSM/ITOM/ITAM/FSM/SPM/SecOps 等 ServiceNow 全平台
- **社区热点**：企业级平台 Skill 的标杆性贡献，更新活跃（最近 08-12）
- **状态**：OPEN

### ⑦ claud-api 技能上下文爆炸问题
- **Issue**：[#1487](https://github.com/anthropics/skills/issues/1487)
- **问题**：该 Skill 单次工具调用即注入约 156k token，直接耗尽上下文窗口
- **状态**：OPEN，尚未有配套修复 PR

---

## 2. 社区需求趋势（基于 Issues）

| 趋势方向 | 代表 Issue/PR | 核心诉求 |
|---|---|---|
| **组织级协作** | [#228](https://github.com/anthropics/skills/issues/228) (16 评/8👍) | 团队内 Skill 共享，类似共享库或直链，替代当前手动下载分发流程 |
| **安全治理** | [#492](https://github.com/anthropics/skills/issues/492) (43 评/2👍)、[#412](https://github.com/anthropics/skills/issues/412) | 社区 Skill 冒充官方 `anthropic/` 命名空间造成信任边界漏洞；需要 Agent Governance 模式 |
| **上下文效率** | [#1487](https://github.com/anthropics/skills/issues/1487)、[#1329](https://github.com/anthropics/skills/issues/1329) | 避免 Skill 一次性注入大量 token；长运行 Agent 需要紧凑状态表示（compact-memory） |
| **跨平台兼容** | [#1099](https://github.com/anthropics/skills/pull/1099)、[#1050](https://github.com/anthropics/skills/pull/1050) | Windows 下 Skill 创建工具链存在系统性兼容缺陷 |
| **AI 输出质量** | [#1367](https://github.com/anthropics/skills/pull/1367)、[#1385](https://github.com/anthropics/skills/issues/1385) | 交付前自动质量门，覆盖机械验证和推理质量双重检查 |
| **专业领域深耕** | [#568](https://github.com/anthropics/skills/pull/568)、[#181](https://github.com/anthropics/skills/pull/181)、[#1615](https://github.com/anthropics/skills/pull/1615) | ServiceNow、SAP 预测模型、SCNet HPC 集群等企业级场景 Skill |
| **MCP 化封装** | [#16](https://github.com/anthropics/skills/issues/16) | 将 Skill 暴露为标准 MCP 接口，便于外部系统调用 |

---

## 3. 高潜力待合并 Skills

以下 PR 评论活跃、需求明确，近期有较大概率高概率被合并：

| PR | Skill 名称 | 优先级理由 |
|---|---|---|
| [#1298](https://github.com/anthropics/skills/pull/1298) | skill-creator 评估修复 | 修复影响 10+ 人、阻碍 Skill 质量优化循环的关键 Bug |
| [#556](https://github.com/anthropics/skills/issues/556) 关联 | run_eval.py 触发修复 | Issue 获 7👍，多个 PR 跟进，基础工具链必须先行 |
| [#1628](https://github.com/anthropics/skills/pull/1628) | Hivemind 多智能体编排 | 最新提交（08-21），解决上下文成本痛点，架构创新性强 |
| [#538](https://github.com/anthropics/skills/pull/538) / [#541](https://github.com/anthropics/skills/pull/541) | PDF/DOCX 大小写 & 书签碰撞修复 | 同类作者（Lubrsy706）系统性修复文档处理 Bug，质量高 |
| [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns | 测试技能覆盖全栈（哲学→单元测试→React→E2E），需求面广 |
| [#1602](https://github.com/anthropics/skills/pull/1602) | 评估/基准/脚本稳定性修复 | 修复多平台兼容性和序列化 Bug，基础设施类修复 |

---

## 4. Skills 生态洞察

> **社区最集中的诉求是"质量治理"与"信任安全"的双重升级**：一方面 skill-creator 工具链的评估缺陷（recall=0%）和上下文效率问题（156k token 注入）严重阻碍 Skill 迭代质量；另一方面社区 Skill 冒充官方命名空间的安全隐患（43 条评论）和组织协作能力缺失（手动分发 Skill），反映出生态从"个人玩具"向"团队协作+企业生产"演进过程中，治理基础设施的严重滞后。

---



# Claude Code 社区动态日报 — 2026-08-25

## 1. 今日速览

v2.1.243 发布，新增 `/usage` 循环分解与 `modelPicker` 自定义设置，但**Linux 平台出现严重 segfault 回归**，多份报告指向 mimalloc 与 glibc 2.44 的兼容性问题，社区高度关注。Windows Desktop 应用长期存在的工作目录与多会话问题持续未解，auto-memory 透明度和性能优化需求稳步上升。

---

## 2. 版本发布

### v2.1.243
- **`/usage` 新增 Loops 分解**：显示每个循环的运行次数、总 token 数、每次运行 token 数及最后运行时间，便于快速定位失控或过于啰嗦的 `/loop` 任务。
- **`modelPicker` 设置**：允许通过有序、带标签的模型列表自定义 `/model` 选择器，支持任意模型 ID 拼写。

> ⚠️ **已知严重问题**：v2.1.243 在 Linux（尤其 glibc 2.44）上启动即 segfault，初步定位原因为 bundled mimalloc 导出版本化 glibc 分配符后，`free(NULL)` 缺少 NULL 检查。v2.1.241 及更早版本不受影响。

---

## 3. 社区热点 Issues

| # | 标题 | 评论 | 👍 | 亮点 |
|---|------|------|-----|------|
| [#89360](https://github.com/anthropics/claude-code/issues/89360) | v2.1.243 Segmentation fault (Linux) | 24 | 8 | 最高关注度 bug，社区集中反馈 Linux segfault 回归 |
| [#89334](https://github.com/anthropics/claude-code/issues/89334) | v2.1.242 segfaults on every launch — mimalloc `free` 无 NULL check | 7 | 6 | 根因分析最深入，指出 2.1.242 首次导出版本化 glibc 分配符 |
| [#89369](https://github.com/anthropics/claude-code/issues/89369) | 2.1.243 native build 启动即 segfault | 2 | 8 | 验证 2.1.241/2.1.236 正常，确认 2.1.243 为引入点 |
| [#54461](https://github.com/anthropics/claude-code/issues/54461) | Desktop 应用无法更改主工作目录或打开新聊天 | 22 | 13 | Windows Desktop 长期痛点，社区投票最高 |
| [#82056](https://github.com/anthropics/claude-code/issues/82056) | auto-memory index 加载状态不可见 | 26 | 1 | 用户希望 session 内暴露 memory 加载完整性 |
| [#89370](https://github.com/anthropics/claude-code/issues/89370) | claude segfaults，install.sh 也 segfaults | 7 | 9 | 安装脚本同样受影响，Linux 用户无法升级 |
| [#85021](https://github.com/anthropics/claude-code/issues/85021) | 权限指示符使用不可渲染的 Unicode 字符 U+23F5 | 2 | 1 | 多次报告后仍关闭未修复，跨终端显示 tofu |
| [#86171](https://github.com/anthropics/claude-code/issues/86171) | 禁用遥测时 Monitor 工具不可用 | 2 | 0 | 隐私设置与功能可用性冲突 |
| [#84878](https://github.com/anthropics/claude-code/issues/84878) | AWS SSO 启动预检在代理后无限挂起 | 1 | 3 | >2.1.187 回归，HTTPS_PROXY 未传递至 SSO-OIDC 调用 |
| [#89371](https://github.com/anthropics/claude-code/issues/89371) | glibc 2.44 (CachyOS) 启动 segfault | 5 | 6 | 具体到 glibc 版本，为根因定位提供关键信息 |

---

## 4. 重要 PR 进展

| # | 状态 | 标题 | 说明 |
|---|------|------|------|
| [#79898](https://github.com/anthropics/claude-code/pull/79898) | ✅ CLOSED | Claude apps gateway AWS 部署资产 | 配套文档的 AWS Bedrock 网关部署示例，与 GCP 示例对称 |
| [#75252](https://github.com/anthropics/claude-code/pull/75252) | ✅ CLOSED | 澄清插件 MCP 配置范围 | 明确 `mcpServers` 配置仅用于插件内置 MCP server，与用户级 allow/deny 列表分开 |
| [#83890](https://github.com/anthropics/claude-code/pull/83890) | 🔄 OPEN | 创建 pylint.yml | 添加 pylint 配置文件 |

> 注：过去 24 小时内共 3 条 PR，均为小范围更新，无重大功能合并。

---

## 5. 功能需求趋势

1. **Memory 功能完善**：auto-memory 的加载状态可观测性（#82056）、索引大小限制可配置（#79217）、持久化内存的用户可见性（#88579）均被多次提及。
2. **Linux 平台稳定性**：segfault 回归是当前最高优先级问题，社区强烈期待紧急修复。
3. **自定义与主题**：diff 颜色覆盖被忽略（#85660）、Unicode 渲染问题（#85021）反映用户对终端 UI 定制化的持续需求。
4. **MCP/OAuth 可靠性**：动态客户端注册失效后缓存 id 永久 replay（#84614）暴露了 OAuth 流程的容错缺陷。
5. **长时 Agentic 任务**：#89372 描述跨数月、多 session 的项目中模型反复走错路径，反映长 horizon 任务的可靠性仍是痛点。

---

## 6. 开发者关注点

- **🔴 紧急**：v2.1.243 Linux segfault 影响全部 Linux 用户，安装脚本同样崩溃，社区呼吁紧急回滚或热修复。
- **🟡 高频**：auto-memory 透明度不足，用户希望 session 内明确知道 memory 加载状态（完整/截断/未加载）。
- **🟡 持续**：Windows Desktop 应用工作目录与多会话管理问题长期未解，投票数持续领先。
- **🟢 体验**：性能问题如 sandbox glob 每次 Bash 调用重复展开（#84681）、git sandbox artifact 噪音（#84662）影响日常开发流畅度。
- **🟢 信任**：AWS SSO 代理兼容回归（#84878）和遥测禁用后功能缺失（#86171）影响企业用户部署信心。

---

*数据来源：github.com/anthropics/claude-code，统计周期 2026-08-24 ~ 2026-08-25*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>



# OpenAI Codex 社区动态日报
**日期：2026-08-25**

---

## 1. 今日速览

auth 会话失效引发的登出循环问题持续霸榜，macOS 与 Windows 平台均有大量用户反馈，累计超过百条评论；同时 Rust CLI 端 0.150.0-alpha.8 首发，多条 PR 聚焦于 TUI 体验优化、持久化架构改进与 MCP 修复。

---

## 2. 版本发布

| 版本 | 说明 |
|---|---|
| `rust-v0.150.0-alpha.8` | 最新 alpha 预览版，于今日发布 |

---

## 3. 社区热点 Issues

| # | 主题 | 评论 | 👍 | 重要性 |
|---|---|---|---|---|
| [#39162](https://github.com/openai/codex/issues/39162) | macOS 打开已有会话导致 ChatGPT 认证失效并跳转登录 | 53 | 31 | 🔴 最高优先级；影响范围最广的认证 bug |
| [#39903](https://github.com/openai/codex/issues/39903) | 请求增加选项禁用"已执行 N 条命令"的折叠行为 | 21 | 36 | 🟡 高人气需求；CLI 可观测性诉求集中体现 |
| [#35746](https://github.com/openai/codex/issues/35746) | 分页历史记录丢弃有效 Rollout 记录并复用序号 | 25 | 1 | 🟡 核心数据一致性 bug，影响历史检索可靠性 |
| [#39189](https://github.com/openai/codex/issues/39189) | Windows 26.814 打开线程后个人 Pro 账号被登出 | 20 | 4 | 🔴 与 #39162 同源的跨平台认证问题 |
| [#39803](https://github.com/openai/codex/issues/39803) | 完成响应或打开会话后反复出现登录界面 | 12 | 0 | 🔴 循环登出问题，与 #39162 互为佐证 |
| [#34227](https://github.com/openai/codex/issues/34227) | Windows 宠物叠加区域随时间偏移 | 17 | 1 | 🟢 体验类 bug，长期存在 |
| [#40267](https://github.com/openai/codex/issues/40267) | macOS 续接线程后刷新令牌未持久化，76 秒内失效 | 7 | 0 | 🔴 认证 bug 的核心技术细节补充 |
| [#39694](https://github.com/openai/codex/issues/39694) | 已完成子 agent 线程未被回收，触发假性线程上限 | 5 | 0 | 🟡 多 agent 场景关键缺陷 |
| [#21777](https://github.com/openai/codex/issues/21777) | 自动压缩机制需暴露给 agent 控制 | 9 | 9 | 🟡 经典增强请求，context window 管理痛点 |
| [#40029](https://github.com/openai/codex/issues/40029) | 无限登录循环：app 始终无法获取 chatgpt.com session cookie | 4 | 0 | 🔴 认证链路根因级问题，CLI 正常但 Desktop 异常 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 说明 |
|---|---|---|---|
| [#40511](https://github.com/openai/codex/pull/40511) | 为中断轮次添加 hooks | ✅ 已关闭 | 新增 `Interrupt` hook 事件，在 abort 前触发，支持完整上下文传递 |
| [#40509](https://github.com/openai/codex/pull/40509) | 添加持久化线程 Artifact 模型 | ✅ 已关闭 | 引入 `thread_artifacts` SQLite 表，支持按线程的类型化身份、级联删除与有序读取 |
| [#40508](https://github.com/openai/codex/pull/40508) | 在时间线中持久化实时事件 | ✅ 已关闭 | 持久化实时会话边界与转录片段，保证语音/agent 工作/轮次生命周期事件有序呈现 |
| [#40502](https://github.com/openai/codex/pull/40502) | 折叠 AGENTS.md 中的家目录路径 | ✅ 已关闭 | `/status` 中 home 路径渲染为 `~`，保留项目相对路径 |
| [#40501](https://github.com/openai/codex/pull/40501) | 去重 unified mentions 中的插件技能 | ✅ 已关闭 | `skills/list` 返回新增 `pluginId` 字段，避免同一能力出现重复入口 |
| [#40499](https://github.com/openai/codex/pull/40499) | 加固启动时 rollout 迁移的并发安全 | ✅ 已关闭 | 等待 rollout 释放后再检测，防止并发写入/压缩导致的路径过期 |
| [#40495](https://github.com/openai/codex/pull/40495) | `/rename` 支持基于对话内容的标题建议 | ✅ 已关闭 | TUI `/rename` 从最新 user/assistant 消息生成暂定标题，可手动覆盖 |
| [#40494](https://github.com/openai/codex/pull/40494) | 对 TUI 路由隐藏临时系统线程 | ✅ 已关闭 | 忽略 `thread/started` 中 feature source 为 `system` 的临时线程 |
| [#40492](https://github.com/openai/codex/pull/40492) | 为 TUI 线程生成描述性标题 | ✅ 已关闭 | 未命名线程在创建时获得暂定标题，随后异步替换为规范化生成标题 |
| [#40488](https://github.com/openai/codex/pull/40488) | 将轮次成本导出为 OTEL 指标 | ✅ 已关闭 | 新增 `codex.turn.cost_microusd` 计数器，含 turn/conversation/interruption 等属性 |

---

## 5. 功能需求趋势

1. **认证与会话稳定性** — 当前最突出的社区痛点，多条 Issue 指向 OAuth 刷新令牌在 Desktop 端失效、session cookie 丢失、登录循环等问题，跨 macOS/Windows 广泛复现。
2. **CLI 可观测性与控制** — 折叠命令输出、hooks 缺省失败信号、自动压缩不可控等诉求持续出现，开发者希望获得更细粒度的执行可见性。
3. **多 Agent 管理** — 子 agent 线程回收、residency 槽位泄漏等问题暴露了 MultiAgentV2 在生命周期管理上的不足。
4. **TUI 体验优化** — 线程标题自动生成、系统线程隐藏、路径折叠等 PR 密集合入，表明团队正系统性打磨 TUI 交互层。
5. **MCP 与工具搜索** — MCP 工具缓存未失效（#33266）与 fallback 模型工具搜索启用（PR #30765）同步推进，反映 MCP 集成仍在快速迭代期。

---

## 6. 开发者关注点

- **认证链路稳定性** 是压倒性的首要问题，累计涉及 5+ 条独立 Issue，覆盖 macOS/Windows/Linux 多平台，核心症状为：刷新令牌服务端失效（`refresh_token_invalidated`）、session cookie 无法获取、登录循环。
- **Windows 平台专项问题集中**：沙箱启动失败（#34928）、内核崩溃（#40119）、IDE 扩展命令执行失败（#39933）、宠物覆盖区偏移（#34227）等多条 Issue 并存，Windows 体验是高风险区。
- **hooks 体系不完善**：`PostToolUse` 无失败标识、`PostToolUseFailure` 不触发（#34289）被明确报告，影响第三方 hook 开发者的错误处理能力。
- **沙箱配置迁移问题**：#40339 指出 `config.toml` 自动迁移生成不符合 `--strict-config` 校验的权限块，`sandbox_workspace_write.network_access` 被静默忽略。
- **子 agent 资源泄漏**：已完成子 agent 线程不回收（#39694 / #35209）在长时间运行任务中累积，最终触发假性线程上限，阻塞正常工作流。

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>



# Gemini CLI 社区动态日报

**日期：2026-08-25 | 数据来源：github.com/google-gemini/gemini-cli**

---

## 一、今日速览

今日发布 v0.56.0-nightly 和 v0.57.0-preview.1 两个版本，核心修复集中在 A2A 服务器状态管理、写入策略安全检测器声明及 Git 环境变量一致性。社区高度关注子代理挂起、自动记忆系统可靠性及 Wayland 兼容性等关键问题。

---

## 二、版本发布

### v0.57.0-preview.1
基于 v0.56.0 构建的预览版本，包含以下关键修复：

| 修复项 | 说明 | PR |
|--------|------|-----|
| A2A 服务器状态清理 | 解决新消息轮次时残留的 cancellation 错误导致 `Execution aborted` 崩溃 | [#28940](https://github.com/google-gemini/gemini-cli/pull/28940) |
| 安全检测器声明对齐 | 将顶层安全检测器正确声明为 `[[safety_checker]]` 表数组，确保 `AllowedPathChecker` 在 `write_file`/`replace` 工具中正常注册 | [#28961](https://github.com/google-gemini/gemini-cli/pull/28961) |
| Git 环境变量一致性 | 防止 sanitization 后 `GIT_CONFIG_*` 键值对不完整导致 Git 解析失败 | [#28938](https://github.com/google-gemini/gemini-cli/pull/28938) |
| 中断响应占位符修复 | 避免中断后残留的 `[The previous response was interrupted...]` 被模型重复输出 | [#28939](https://github.com/google-gemini/gemini-cli/pull/28939) |

---

## 三、社区热点 Issues

### 🔥 P1 级关键问题

**1. #22323 — Subagent 在达到 MAX_TURNS 后被错误报告为 GOAL 成功**
- **热度：** 13 评论 · 2 👍
- **重要性：** `codebase_investigator` 子代理在未执行任何分析的情况下即报告成功，导致主代理误判任务完成，严重破坏多代理工作流可靠性。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/22323

**2. #21409 — Generalist Agent 永久挂起**
- **热度：** 8 评论 · 8 👍（最高点赞）
- **重要性：** 简单操作（如创建文件夹）触发 generalist agent 后永久卡死，用户反馈等待超1小时。这是影响日常使用的高频痛点。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/21409

**3. #25166 — Shell 命令执行完成后卡在 "Waiting input"**
- **热度：** 4 评论 · 3 👍
- **重要性：** 即使是极简命令执行完毕后，CLI 仍显示 "Awaiting user input"，影响用户体验和自动化脚本稳定性。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/25166

**4. #21983 — Browser Subagent 在 Wayland 下失败**
- **热度：** 4 评论 · 1 👍
- **重要性：** Wayland 用户报告 browser subagent 执行后立即以 GOAL 终止，无法完成网页操作任务。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/21983

### 🔧 功能与体验改进

**5. #19873 — 利用 Zero-Dependency OS Sandboxing 增强 Bash 能力**
- **热度：** 8 评论 · 1 👍
- **重要性：** 提议通过沙盒化方式让 Gemini 3 模型发挥原生 bash 操作优势，同时保障安全，是架构层面的重要探索。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/19873

**6. #22745 — AST-aware 文件读取与代码库映射评估**
- **热度：** 7 评论 · 1 👍
- **重要性：** 评估基于 AST 的精确文件读取能否减少 token 消耗、提升代码理解精度，直接影响 agent 效率。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/22745

**7. #21968 — Gemini 未充分使用 Skills 和 Sub-agents**
- **热度：** 6 评论
- **重要性：** 用户反馈模型即使面对高度相关任务也不会主动调用自定义 skills，需要显式指令才会触发。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/21968

**8. #26522 — Auto Memory 无限重试低信号会话**
- **热度：** 5 评论
- **重要性：** Auto Memory 系统将低价值会话标记为未处理并持续重新推荐，浪费上下文和计算资源。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/26522

**9. #22232 — Browser Agent 会话接管与锁恢复增强**
- **热度：** 4 评论
- **重要性：** 当前 browser agent 遇到锁定的 profile 时直接 fail-fast，用户希望支持自动接管和恢复。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/22232

**10. #26525 — 确定性的敏感信息脱敏与 Auto Memory 日志精简**
- **热度：** 4 评论
- **重要性：** 当前脱敏在内容进入模型上下文后才发生，存在安全隐患；同时需要减少日志中的 skill 数据泄露。
- **链接：** https://github.com/google-gemini/gemini-cli/issues/26525

---

## 四、重要 PR 进展

| PR | 状态 | 摘要 |
|----|------|------|
| [#28940](https://github.com/google-gemini/gemini-cli/pull/28940) | ✅ 已合入 | **A2A 服务器修复**：清除新消息轮次时的残留 cancellation 错误，彻底解决 GCA 执行中断崩溃问题 |
| [#28961](https://github.com/google-gemini/gemini-cli/pull/28961) | ✅ 已合入 | **安全策略修复**：将顶层 safety checker 声明对齐为 `[[safety_checker]]` 表数组，确保 write 工具安全检测生效 |
| [#28938](https://github.com/google-gemini/gemini-cli/pull/28938) | 🔄 开放 | **Git 环境变量一致性**：防止 sanitization 后 `GIT_CONFIG_*` 键值对不完整导致 Git 解析失败 |
| [#28939](https://github.com/google-gemini/gemini-cli/pull/28939) | 🔄 开放 | **中断响应占位符修复**：避免中断后的合成模型响应被重复输出 |
| [#29022](https://github.com/google-gemini/gemini-cli/pull/29022) | 🔄 开放 | **ask_user 历史记录保留**：新增 `ui.keepAskUserQuestionsInHistory` 配置项，保留用户交互问题于历史记录 |
| [#28863](https://github.com/google-gemini/gemini-cli/pull/28863) | 🔄 开放 | **扩展安全增强**：MCP 服务器环境变更时强制用户确认，并清洗可能改变运行时的环境变量 |
| [#29019](https://github.com/google-gemini/gemini-cli/pull/29019) | 🔄 开放 | **Session 日志转 Eval**：新增 `eval:from-log` 命令，将真实交互日志快速转化为可审查的 eval 测试 |
| [#29018](https://github.com/google-gemini/gemini-cli/pull/29018) | ✅ 已合入 | **A2A Server 安全清理**：移除误导性的 security schemes 和硬编码凭据，修正本地开发场景下的认证元数据 |
| [#29017](https://github.com/google-gemini/gemini-cli/pull/29017) | 🔄 开放 | **Symlink Skills 去重**：修复 Windows junction 和 POSIX symlink 场景下 skill 目录重复发现的问题 |
| [#29013](https://github.com/google-gemini/gemini-cli/pull/29013) | 🔄 开放 | **文档补充**：补充 6 个缺失的 CLI 标志文档（`--policy`、`--admin-policy`、`--session-id` 等） |

---

## 五、功能需求趋势

从 Issues 聚类分析，社区当前最关注的方向：

| 方向 | 相关 Issues | 热度 |
|------|-------------|------|
| **Agent 可靠性** | #22323, #21409, #21968, #22267 | 🔥🔥🔥 |
| **Memory 系统改进** | #26522, #26525, #26523, #26516 | 🔥🔥 |
| **浏览器 Agent** | #21983, #22232, #22267 | 🔥🔥 |
| **代码理解效率** | #22745, #22746, #19561 | 🔥 |
| **安全与权限** | #26525, #28863, #22672 | 🔥 |
| **操作系统兼容** | #21983 (Wayland), #29017 (Symlink) | 🔥 |

---

## 六、开发者关注点

### 核心痛点

1. **子代理行为不可预期**：多次反馈 generalist/subagent 挂起、过早终止或跳过自定义 skills，影响复杂任务成功率。
2. **Auto Memory 质量参差**：低信号会话被反复推荐、无效 patch 静默丢弃、日志中潜在敏感信息泄露。
3. **环境兼容性**：Wayland 下浏览器 agent 失效、Windows junction/POSIX symlink 的 skill 识别问题。
4. **交互体验**：shell 命令完成后 UI 状态不更新、ask_user 问题历史丢失、中断后残留占位文本。

### 高频需求

- 更精细的 token 效率优化（AST-aware 读取、tactful extraction）
- 可追溯的 eval 体系（从 session log 生成测试）
- 更强的 agent 自我感知与 CLI 工具使用能力
- 更安全的 extension/MCP 环境管理

---

*报告生成时间：2026-08-25 | Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>



# GitHub Copilot CLI 社区动态日报
**日期：2026-08-25 | 数据来源：github.com/github/copilot-cli**

---

## 1. 今日速览

Copilot CLI v1.0.81-9 正式发布，新增模型数据保留警告提示；MCP OAuth 认证链路问题持续引发关注，微软 Entra ID 兼容性及 RFC 8414 §3.3 回归成为焦点；社区对交互式模式工具白名单功能请求热度高涨（27👍），成为当前最受欢迎的功能提案。

---

## 2. 版本发布

### v1.0.81-9
- **改进**：在 `/model` 选择器中显示模型数据保留警告，并提供相关链接，帮助用户了解各模型的数据处理政策
- [GitHub Releases](https://github.com/github/copilot-cli/releases)

---

## 3. 社区热点 Issues

### 🔥 高热度 Bug & 功能请求

**#1274** CLI 频繁返回 400 错误（Invalid Request Body）
- 作者：unusualbob | 评论：27 | 👍：11 | 更新于 2026-08-24
- **为何关注**：影响约 95% 的代码审查尝试，疑似服务端验证或 CLI 请求构造问题，稳定性问题高优先级
- [查看 Issue](https://github.com/github/copilot-cli/issues/1274)

**#1973** 功能请求：交互式模式工具白名单
- 作者：Dicer-J | 评论：12 | 👍：27 | 更新于 2026-08-24
- **为何关注**：当前交互模式仅支持全手动确认或 `/allow-all` 全放行，缺乏细粒度权限控制，开发者呼声最高
- [查看 Issue](https://github.com/github/copilot-cli/issues/1973)

**#4490** [已关闭] Atlassian MCP OAuth 认证在 v1.0.80 中损坏（RFC 8414 §3.3 回归）
- 作者：ChandrasekarCK | 更新于 2026-08-24
- **为何关注**：1.0.78 正常、1.0.80 破坏的明确回归，已关闭但提醒注意 MCP 认证链路的稳定性
- [查看 Issue](https://github.com/github/copilot-cli/issues/4490)

**#4224** Subagent OTel spans 缺少计费属性，导致外部成本核算偏低
- 作者：stefanpinson | 评论：3 | 👍：1 | 更新于 2026-08-24
- **为何关注**：影响企业用户成本分摊准确性，子代理调用的 token 消耗未被正确追踪
- [查看 Issue](https://github.com/github/copilot-cli/issues/4224)

**#4582** MCP OAuth authorize 请求遗漏 `scope` 参数，导致 Entra ID AADSTS900144 错误
- 作者：mikemassa84 | 评论：2 | 创建于 2026-08-24
- **为何关注**：Azure AD 企业用户认证阻塞问题，静态 oauthClientId 配置场景下触发
- [查看 Issue](https://github.com/github/copilot-cli/issues/4582)

**#4421** MCP initialize 握手硬编码 60s 超时且不可重试，npx 启动的 stdio 服务器约 29% 会话失败
- 作者：devinj-msft | 评论：2 | 更新于 2026-08-24
- **为何关注**：微软内部开发者提出的基础设施级问题，超时后服务器永久死亡无恢复机制
- [查看 Issue](https://github.com/github/copilot-cli/issues/4421)

**#4566** Agent 反复确认工作但从不执行工具操作
- 作者：kloudkon | 评论：2 | 👍：1 | 更新于 2026-08-24
- **为何关注**：gpt-5.3-codex 模型在 1.0.80 下出现代理行为异常，影响 autopilot 可用性
- [查看 Issue](https://github.com/github/copilot-cli/issues/4566)

**#4593** Windows 下归档 worktree 会话失败（OS Error 32）
- 作者：azchohfi | 更新于 2026-08-24
- **为何关注**：Windows 平台文件锁释放顺序 bug，会话进程树未先终止即删除 worktree
- [查看 Issue](https://github.com/github/copilot-cli/issues/4593)

**#4568** `--cloud` owner picker 挂起、重连崩溃、task 轮询触发 429
- 作者：haflidif | 更新于 2026-08-24
- **为何关注**：云端会话创建全链路问题，影响无仓库上下文场景
- [查看 Issue](https://github.com/github/copilot-cli/issues/4568)

**#4570** Windows 下插件安装/更新在 VS Code 运行时失败（Access Denied）
- 作者：DDKinger | 更新于 2026-08-24
- **为何关注**：影响所有插件，用户需手动关闭 VS Code 才能操作，体验极差
- [查看 Issue](https://github.com/github/copilot-cli/issues/4570)

---

## 4. 重要 PR 进展

> 过去 24 小时内仅更新 1 条 PR，内容较有限。

**#4573** 重命名 README.md → README.mdmain
- 作者：phuongnam467 | 更新于 2026-08-24
- **说明**：仓库文档结构调整，不影响功能
- [查看 PR](https://github.com/github/copilot-cli/pull/4573)

---

## 5. 功能需求趋势

基于本期 Issues 提炼社区核心诉求方向：

| 方向 | 代表 Issue | 热度 |
|------|-----------|------|
| **MCP 认证与兼容性** | #4490、#4582、#4584、#4408 | 🔥🔥🔥 |
| **细粒度权限控制** | #1973（工具白名单）、#4224（计费追踪） | 🔥🔥🔥 |
| **多轮对话能力** | #4577、#4538（已关闭，建议已采纳） | 🔥🔥 |
| **跨平台稳定性** | #4593（Windows 文件锁）、#4570（VS Code 冲突） | 🔥🔥 |
| **成本透明化** | #4589（状态栏显示原始 token 计数）、#4224 | 🔥 |
| **扩展能力** | #4583（PDF 上传）、#4581（图像生成支持） | 🔥 |
| **非 Anthropic 模型优化** | #4588（MCP 工具延迟对所有非 Claude 模型禁用，空 prompt 21k→47k token） | 🔥🔥 |

---

## 6. 开发者关注点

### 高频痛点总结

1. **MCP OAuth 认证链路脆弱**：本期最集中的问题域。Entra ID（Azure AD）、Atlassian、Enterprise 路由场景下反复出现认证失败，涉及 RFC 8414 兼容、scope 参数缺失、跨源资源标识等问题，企业用户受影响最大。

2. **交互模式权限粒度不足**：开发者强烈期望在交互式模式下对只读工具（grep、cat、find 等）实现自动放行，同时保留对写操作的手动确认，避免 `/allow-all` 的安全风险。

3. **非 Anthropic 模型成本效率低**：Issue #4588 指出，使用 OpenAI/Gemini/Grok 等模型时，MCP 工具定义全量加载导致空 prompt 消耗 47k token（Claude 仅需 21k），成本差异显著。

4. **Windows 平台文件竞争**：VS Code 运行时锁住插件目录导致更新失败，以及 worktree 归档时进程树未先终止，均为 Windows 专属稳定性问题。

5. **Agent 行为可靠性**：子代理反复确认但不执行工具的异常行为，以及背景压缩导致 tool output 丢失进而触发 400 错误，影响 autopilot 场景的实际可用性。

---

*日报生成时间：2026-08-25 | 分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>



# Kimi Code CLI 社区动态日报
**日期：2026-08-25** | 数据源：MoonshotAI/kimi-cli

---

## 1. 今日速览

今日 Kimi Code CLI 社区无新版本发布，Issues 零更新。唯一活跃动态为 **PR #2595**，修复了 `StrReplaceFile` 在处理非 UTF-8 文件时导致文件内容损坏的问题，预计近期合并。

---

## 2. 版本发布

> 过去 24 小时内无新 Release。

---

## 3. 社区热点 Issues

> 过去 24 小时内无新增或更新的 Issues。

---

## 4. 重要 PR 进展

### PR #2595 — fix(StrReplaceFile): refuse to edit files that are not valid UTF-8
- **作者**：shoemoney
- **状态**：OPEN（2026-08-06 创建，2026-08-24 更新）
- **关联 Issue**：[#2591](https://github.com/MoonshotAI/kimi-cli/issues/2591)
- **内容**：修复了 `StrReplaceFile` 使用 `errors="replace"` 解码整个文件后，将所有非 UTF-8 字节替换为 U+FFFD 的缺陷——该缺陷会导致**与编辑位置无关的文件区域内容被破坏**。新方案拒绝编辑非 UTF-8 文件，避免不可逆的数据损坏。
- **链接**：[PR #2595](https://github.com/MoonshotAI/kimi-cli/pull/2595)

---

## 5. 功能需求趋势

当前数据有限，暂无法提炼明确趋势。建议持续关注 Issues 标签分布及社区讨论热度。

---

## 6. 开发者关注点

- **文件编码安全性**：PR #2595 所关联的 Issue #2591 反映了开发者对文件编辑操作中编码兼容性问题的关注，非 UTF-8 文件（如二进制混合文件、某些语言编码文件）的处理是高频痛点。

---

> *数据来源：github.com/MoonshotAI/kimi-cli | 统计周期：2026-08-24 00:00 ~ 2026-08-25 00:00（UTC）*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>



# Pi 社区动态日报 — 2026-08-25

---

## 1. 今日速览

Pi v0.84.3 正式发布，新增可选 PowerShell 工具（Windows）和安全原子更新机制。社区重点攻克了三类问题：长会话上下文压缩触发逻辑缺陷、Provider 流挂起导致 Agent 死循环、以及 Gemini 3.x 的 `thought_signature` 透传丢失。三个核心修复 PR 同日合并，均指向 nitishagar 的贡献。

---

## 2. 版本发布

### v0.84.3（2026-08-25）

| 更新项 | 说明 |
|--------|------|
| **PowerShell Tool** | Windows 平台新增可选原生 PowerShell 命令执行工具，解决 Git Bash 路径处理痛点 |
| **Safer Managed Updates** | 更新流程改为"暂存 → 校验 → 原子激活"，降低中断风险 |

📎 相关文档：[PowerShell Tool](https://github.com/earendil-works/pi/blob/v0.84.3/packages/coding-agent/docs/windows.md#powershell-tool)

---

## 3. 社区热点 Issues

### 🔥 高关注 Issue

| Issue | 状态 | 评论 | 核心问题 | 链接 |
|-------|------|------|----------|------|
| #7547 | OPEN | 44 | Windows 多运行方式混乱，缺乏统一官方指引 | [链接](https://github.com/earendil-works/pi/issues/7547) |
| #6879 | CLOSED | 22 | 上下文超过 100% 后自动压缩不触发，直到 API 拒绝请求 | [链接](https://github.com/earendil-works/pi/issues/6879) |
| #6996 | OPEN | 6 | Gemini 3.x 通过 OpenAI 兼容接口使用时 `thought_signature` 丢失，导致工具调用链断裂 | [链接](https://github.com/earendil-works/pi/issues/6996) |
| #8331 | OPEN | 3 | Provider 流静默挂起时 Agent 循环无限等待，Escape 无法中断 | [链接](https://github.com/earendil-works/pi/issues/8331) |
| #8133 | OPEN | 4 | 不同上下文窗口模型共用全局压缩参数，无法按模型精细调优 | [链接](https://github.com/earendil-works/pi/issues/8133) |
| #8166 | OPEN | 7 | 扩展通过 `triggerTurn: false` 注入消息后，破坏 `tool_calls → tool` 邻接规则 | [链接](https://github.com/earendil-works/pi/issues/8166) |
| #6922 | CLOSED | 11 | llama.cpp 设为默认 Provider 时启动报"No models available" | [链接](https://github.com/earendil-works/pi/issues/6922) |
| #8167 | CLOSED | 11 | llama-server router 模式下模型不出现在选择列表 | [链接](https://github.com/earendil-works/pi/issues/8167) |

> **趋势观察**：Windows 体验和本地模型（llama.cpp）集成是社区高频痛点，两个 Issue 合计 55 条评论。

---

## 4. 重要 PR 进展

### ✅ 已合并（今日）

| PR | 作者 | 修复内容 | 关联 Issue |
|----|------|----------|------------|
| #8593 | nitishagar | 为挂起的 Provider SSE 流添加空闲超时，防止 Agent 无限等待 | #8331 |
| #8592 | nitishagar | 新增 `compaction.profiles` 按模型配置压缩参数 | #8133 |
| #8590 | nitishagar | 修复 OpenAI 兼容接口中 Gemini `thought_signature` 丢失问题 | #6996 |
| #8585 | danscofield | OpenAI 流在 abort signal 触发时立即中止，补全 Anthropic 路径已有的检查 | — |
| #8575 | simonckemper | 修复会话 JSONL 文件中撕裂条目标记导致双条丢失的问题 | — |
| #8479 | KaelWD | 暴露 llama.cpp 未加载的 preset 模型供选择 | #8167 |
| #8578 | c0n419 | 修复 xAI Provider 类型定义编译错误 | #8124 |
| #8580 | vincelwt | 减少工具行多余垂直间距，转录更紧凑 | — |
| #8512 | mitsuhiko | 新增可选 PowerShell 工具 | v0.84.3 |

### 🔄 进行中

| PR | 作者 | 内容 |
|----|------|------|
| #8573 | cristinaponcela | Amazon Bedrock Mantle Anthropic Messages 路由支持 |
| #8572 | cristinaponcela | Bedrock Mantle 通用支持（与 #8302 重复提交） |
| #8559 | Panoplos | 剪贴板图片粘贴时以原子标记展示 |
| #8547 | Panoplos | 点击编辑器区域时移动光标位置 |
| #8158 | xl0 | Mermaid 终端渲染升级 |

---

## 5. 功能需求趋势

从 Issue 和 PR 中提炼出以下社区关注方向：

| 方向 | 代表需求 | 活跃度 |
|------|----------|--------|
| **本地模型集成** | llama.cpp preset 可见性、自动加载、router 模式兼容 | ⭐⭐⭐⭐⭐ |
| **上下文压缩优化** | 按模型配置、触发时机修复、摘要截断问题 | ⭐⭐⭐⭐⭐ |
| **Provider 健壮性** | 流挂起超时、WebSocket 重试覆盖、_abort 信号处理 | ⭐⭐⭐⭐ |
| **Windows 体验** | PowerShell 原生支持、路径处理、多运行方式统一 | ⭐⭐⭐⭐ |
| **新模型支持** | DeepSeek V4 Flash Vision、Gemini 3.x 签名透传 | ⭐⭐⭐ |
| **扩展机制** | 工具 schema 懒加载、Renderer Hook、Presets 导出导入 | ⭐⭐⭐ |
| **多云路由** | Bedrock Mantle、Merge Gateway、Parasail.io | ⭐⭐ |

---

## 6. 开发者关注点

### 高频痛点

1. **长会话稳定性**：#6879（压缩不触发）、#8331（流挂起）均指向长时间 Agent 运行的可靠性问题，v0.84.3 已提交修复但需验证。

2. **本地模型可用性**：#6922 + #8167 反映 llama.cpp 集成仍存在 UX 断层，用户期望像云端 Provider 一样开箱即用。

3. **跨 Provider 兼容性**：#6996（Gemini 签名丢失）说明 OpenAI 兼容层对特定 Provider 扩展字段（`extra_content`）的处理存在遗漏，影响多 Provider 混用场景。

4. **Windows 路径/工具链**：#7547 和 #8582 揭示 Windows 下 bash/pwsh 混用导致的路径解析和工具选择混乱，PowerShell 工具是阶段性解决方案。

5. **扩展开发 DX**：#8583（schema 懒加载）、#8589（Renderer Hook）、#8588（Presets 导出）反映扩展作者对更灵活生命周期控制的需求。

---

*数据来源：github.com/badlogic/pi-mono，统计周期 2026-08-24 ~ 2026-08-25*

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>



# Qwen Code 社区动态日报
**日期：2026-08-25**

---

## 1. 今日速览

Qwen Code 发布 `v0.22.0-nightly.20260825` 预编译版本，同步推进 `cua-driver-rs v0.20.0` 跨平台原生构建。社区活跃度持续攀升，过去24小时内新增50条Issue与20条PR，重点聚焦MCP重连稳定性、TUI渲染性能优化及钉钉（DingTalk）工作区频道集成。

---

## 2. 版本发布

### v0.22.0-nightly.20260825.22bb5e8b9f
- **PR #9730**：修复 web-shell 从概览面板打开时未传递 session workspace cwd 的问题
- **cua-driver-rs v0.20.0**：预编译二进制发布，支持 macOS（codesigned + notarized）、Linux（x86_64 + arm64）、Windows（x86_64 + arm64）

🔗 [PR #9730](https://github.com/QwenLM/qwen-code/pull/9730)

---

## 3. 社区热点 Issues

| # | 标题 | 优先级 | 关注点 | 评论数 |
|---|------|--------|--------|--------|
| #5975 | API Error: No stream activity for 120000ms | P2 | 流式输出长时间无响应导致API报错 | 12 |
| #4063 | core + cli 架构审查 — 12项结构性问题 | P0 | `@google/genai` 类型绑架核心，136个文件直接依赖 | 9 |
| #8083 | derived Config context ownership 显式化 | P1 | 多子Agent/scoped memory配置继承问题 | 6 |
| #6094 | cron + blockStreaming 交互缺陷 | P2 | qqbot 定时任务与流式阻塞消息重复 | 5 |
| #9944 | MCP HTTP重连成功后工具仍不可用 | P2 | `mcp-session-id` 变更后工具调用返回 "Tool not found" | 4 |
| #9942 | 隐藏 skill 命令于顶层 slash 补全 | P3 | 技能过多导致补全菜单臃肿 | 4 |
| #9927 | Artifact updatedAt 过期，write_file 中间状态残留 | P2 | 会话产物时间戳不随内容更新 | 4 |
| #9005 | Anthropic wire 缺少 stream-safety 保护 | P1 | OpenAI wire 已有保护而 Anthropic 缺失 | 4 |
| #9026 | NO_TOOL_RESULT_PROGRESS hard-fails headless runs | P2 | 工具结果后模型静默结束导致headless运行崩溃 | 4 |
| #8662 | TUI 渲染层迁移至 OpenTUI | P3 | ink 7 + React 19 存在闪烁与鼠标支持问题 | 4 |

---

## 4. 重要 PR 进展

| # | 标题 | 类型 | 核心内容 |
|---|------|------|----------|
| #9970 | perf(cli): reduce TUI render overhead | 性能 | VP 模式启用增量终端输出，隔离 history 渲染 |
| #9740 | feat(review): Step 4 verification execution-grade | 功能 | 新增 `qwen review ab-drive` 子命令，对两侧树执行脚本比对 |
| #9723 | feat(review): 容器内执行被审查代码 | 功能 | 审查执行路径隔离至容器，作为可配置策略 |
| #8943 | feat(review): Step 3A fan-out 工作流分发 | 功能 | `/review` 第三步由脚本自动生成并路由，支持回退 |
| #9394 | feat(channels): DingTalk Workspace 频道 | 功能 | 支持 DM、@提及、文档引用、Todo 变更及源码会话 |
| #9844 | fix(telemetry): 会话切换失败时恢复用量统计 | 修复 | 修复 `/resume`/`/branch` 失败后 telemetry 重复计算 |
| #9871 | fix(ci): 中和 autofix 日志中的 legacy ##[ 命令 | 修复 | 防御 GitHub Actions 解析 `##[name]` 遗留语法 |
| #8927 | feat(channels): sessionRotation 会话生命周期控制 | 功能 | 支持按 `maxTurns` 或时间窗口自动开启新会话 |
| #9305 | fix(ui): VP 模式短内容底部对齐 | 修复 | 修复会话内容不满视口时底部留白问题 |
| #9962 | fix(mcp): 恢复重启后的 HTTP MCP 服务器 | 修复 | 修复 `mcp-session-id` 变更后工具不可用的连锁缺陷 |

---

## 5. 功能需求趋势

基于本周 Issue/PR 分析，社区关注方向如下：

| 方向 | 热度 | 关键事件 |
|------|------|----------|
| **MCP 集成稳定性** | 🔥🔥🔥 | #9944 重连失败、#9962 修复、#9951 开源 Mem0 协议支持 |
| **TUI/渲染性能** | 🔥🔥🔥 | #9970 渲染开销优化、#8662 ink→OpenTUI 迁移、#9966 VP 溢出 |
| **多渠道支持** | 🔥🔥 | #9394 钉钉工作区、#8927 会话轮换、#9922 多图片保留 |
| **代码审查增强** | 🔥🔥 | #9740 执行级验证、#9723 容器隔离、#8943 工作流分发 |
| **核心架构治理** | 🔥🔥 | #4063 12项结构性问题、#8083 Config 所有权显式化 |
| **Computer Use 路线图** | 🔥 | #9335/9336 三阶段迁移至持久化 Node REPL + SDK |

---

## 6. 开发者关注点

**高频痛点**：
1. **MCP 重连假成功**：HTTP 传输的 MCP 服务器重启后 `mcp-session-id` 变更，导致工具调用静默失败，社区反馈强烈（#9944）
2. **API 流式超时**：`No stream activity for 120000ms` 在复杂任务中频繁触发，影响 headless 与交互式体验（#5975、#9026）
3. **TUI 渲染异常**：VP 模式下高度预算溢出、短内容对齐、ink 补丁维护成本高等问题持续存在（#9966、#8662）
4. **架构耦合风险**：`@google/genai` 类型贯穿 136 个文件，核心模块自主性受威胁（#4063）

**高频需求**：
- 更细粒度的会话管理（rotation、内存隔离）
- 多渠道（尤其国内 IM）的稳定集成
- 代码审查流程的自动化与可验证性提升
- Computer Use 从原子工具集向 SDK/Skill 架构迁移

---

*数据来源：github.com/QwenLM/qwen-code，统计周期 2026-08-24 00:00 ~ 2026-08-25 00:00 UTC*

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>



# DeepSeek TUI 社区动态日报
**日期：2026-08-25** | 数据来源：github.com/Hmbown/DeepSeek-TUI

---

## 1. 今日速览

v0.9.12 集成进入关键冲刺阶段，核心发布阻塞项已基本完成，正在进行版本升级和发布门禁检查。社区同时推进多项监督操作栈增强：生命周期事件外发、控制套接字、`/relaunch` 命令及目标延续节奏修复已陆续合并。

---

## 2. 版本发布

**v0.9.12 — 开发中（未正式发布）**

- 集成分支 `codex/v0912-integration-20260823` 已代码完整，待版本升级与发布门禁通过后正式推出
- 里程碑追踪：[#5573](https://github.com/Hmbown/CodeWhale/issues/5573)
- 主要分支汇总 PR：[#5576](https://github.com/Hmbown/CodeWhale/pull/5576)（72 commits）

---

## 3. 社区热点 Issues

| # | 标题 | 状态 | 关注度 | 推荐理由 |
|---|------|------|--------|----------|
| #5588 | Provider neutrality: 18 DeepSeek-exclusive gates | OPEN | ⭐⭐⭐ | 全面审计发现18处应转为提供商中立的 DeepSeek 专属逻辑，已修复 NVIDIA NIM env 泄漏问题 |
| #5601 | 全新安装时 MiniMax/Xiaomi 返回 404 | OPEN | ⭐⭐⭐ | 新用户配置非 DeepSeek 模型时高频遇到，URL 内置问题导致无法首次配置 |
| #1482 | nVidia NIM not work | CLOSED | ⭐⭐⭐ | NVIDIA NIM API 404 报错的长期问题，伴随 #5588 修复后有望根本解决 |
| #5596 | Turn end silently cancels subagents | OPEN | ⭐⭐ | 子 agent 在父 turn 结束时被静默销毁，可能导致长时 reviewer 工作丢失 |
| #2492 | 不具备跨会话记忆 | CLOSED | ⭐⭐ | 用户反馈重启后遗忘上下文，影响连续工作流体验 |
| #5589 | Fleet config view Enter 循环 | OPEN | ⭐⭐ | Fleet 角色选择 Enter 无状态变化，UX 问题影响多模型编排 |
| #5551 | Focused-block actions (y/Y/Enter/r) | OPEN | ⭐⭐ | 为转录文本块增加复制内容/元数据/全屏/原始 markdown 操作 |
| #5553 | /context 添加工具/MCP 成本估算 | OPEN | ⭐⭐ | 让用户能看到每个 MCP 服务器的 token 成本，便于优化 |
| #5534 | Goal-continuation cadence 被绕过 | CLOSED | ⭐⭐ | 目标延续静默期在 turn 内分发路径上失效的 bug，已定位 |
| #5585 | Test stack overflow | OPEN | ⭐ | 测试用例在 macOS 上栈溢出，预存在问题，影响测试稳定性 |

---

## 4. 重要 PR 进展

| # | 标题 | 状态 | 作者 | 说明 |
|---|------|------|------|------|
| #5576 | 0.9.12 integration: must-fix + UX fixes | OPEN | Hmbown | v0.9.12 发布分支，72 commits，阻塞项已完成，待门禁 |
| #5606 | 0.9.12 relay integration | CLOSED | Hmbown | 托管 Chat 统一至原生 runtime threads，含 R2 审批修复 |
| #5594 | Control socket - part d (final) | OPEN | M-Maciej | 为每个会话绑定 Unix JSON-RPC 套接字，支持监督操作 |
| #5593 | /relaunch command - part c | OPEN | M-Maciej | 安装新二进制后一键重启切换，无需手动重开 |
| #5592 | Lifecycle outbox - part b | OPEN | M-Maciej | 可选 JSONL 事件外发，支持 turn/subagent/session 生命周期监听 |
| #5591 | Goal continuation cadence fix - part a | CLOSED | M-Maciej | 修复目标延续静默期在 turn 内路径未生效的 bug |
| #5584 | Persist child approval receipts | OPEN | cyq1017 | 子 agent 审批结果持久化，修复内存决策不可恢复问题 |
| #5603 | Show tool and MCP schema costs | OPEN | wuisabel-gif | 上下文检查器展示工具/MCP schema 成本估算 |
| #5602 | fix(shell): decode Windows output | OPEN | zhuowp | 修复 Windows ANSI 编码字符在 shell 输出中乱码问题 |
| #5523 | Extract tool call stages from turn loop | CLOSED | bistack | 重构工具调用流程，提取 plan/execute/process 三阶段 |

---

## 5. 功能需求趋势

| 趋势方向 | 代表 Issues / PRs | 说明 |
|----------|-------------------|------|
| **多提供商兼容性** | #5588, #1482, #5601 | 从 DeepSeek 专属逻辑向提供商中立转型，修复第三方模型 URL 配置问题 |
| **监督操作栈** | #5594, #5593, #5592, #5584 | 控制套接字、生命周期事件、`/relaunch`、子 agent 审批持久化——面向自动化/长时间运行的增强 |
| **成本可视化** | #5553, #5603 | MCP 服务器和工具调用的 token 成本展示，帮助用户优化配置 |
| **Fleet/多模型编排** | #5589, #5604 | Fleet 配置 UX 改进，成员编辑发现性增强 |
| **平台兼容性** | #5602 | Windows shell 输出编码修复 |
| **代码质量** | #5586, #5587 | 巨型文件分解（lib.rs 18.7k、config.rs 12.3k）、死代码清理 |
| **用户体验** | #5551, #5554, #4959 | 焦点块操作、光标颜色强调、`/stop` 命令增强 |

---

## 6. 开发者关注点

1. **跨会话记忆断裂** — #2492 反映用户希望会话状态能持久化，重启后自动恢复上下文
2. **第三方模型配置门槛高** — #5601、#1482 显示 MiniMax、Xiaomi、NVIDIA NIM 等新用户首次配置时 URL/API 报错频繁
3. **子 agent 生命周期管理** — #5596、#5597、#5584 集中暴露子 agent 被静默取消、使用量统计丢失、审批不持久等问题
4. **长时运行稳定性** — #5534（节奏绕过）、#5605（测试不稳定）表明 turn 内分发路径存在竞态或遗漏
5. **Fleet 配置 UX 不直观** — #5589 反馈 Enter 无响应、模型切换入口隐蔽
6. **成本透明度需求** — #5553 用户希望能在 TUI 内直接看到各 MCP 工具的 token 消耗
7. **Windows 平台适配** — #5602 反映 Windows 用户在意 ANSI/UTF-8 混合编码的显示正确性

---

*日报生成时间：2026-08-25 | 分析师：Agnes (Sapiens AI)*

</details>

<details>
<summary><strong>Grok Build</strong> — <a href="https://github.com/xai-org/grok-build">xai-org/grok-build</a></summary>

过去24小时无活动。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*