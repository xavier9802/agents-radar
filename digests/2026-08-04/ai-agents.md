# OpenClaw 生态日报 2026-08-04

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-04 03:18 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw 项目深度报告



# OpenClaw 项目动态日报 — 2026-08-04

## 1. 今日速览

OpenClaw 在过去24小时内保持极高活跃度：共处理 **500 条 Issue**（463条新开/活跃，37条关闭）和 **500 条 PR**（361条待合并，139条已合并/关闭），并发布了 **2 个补丁版本**（v2026.7.1-1、v2026.7.1-2）。项目整体健康度良好，社区反馈集中指向消息可靠性、会话状态管理和 provider 兼容性三大核心痛点，维护团队正在密集推进修复 PR。

---

## 2. 版本发布

### v2026.7.1-2
- **修复内容：** npm plugin 更新兼容性问题——接受来自新版 npm 客户端的 singleton-array metadata，使受追踪的官方插件能正常安装和更新到修复版本
- **影响范围：** 插件生态系统的更新链路
- **关联 Issue：** #108336

### v2026.7.1-1
- **修复内容：**
  - **Codex 进度回复：** 修复 GPT/Codex 在传递进度消息后 app-server turn 过早终止的问题，确保模型能到达权威的终端响应（#106961, #108487，感谢 @joshavant）
  - **Memory Core 启动修复：** 恢复派生的 legacy-index 和 ca（内容截断）
- **破坏性变更：** 无
- **迁移注意：** 无特殊迁移要求，建议所有使用 Codex/GPT 后端的用户升级

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 内容摘要 | 状态 |
|----|------|---------|------|
| [#108336](https://github.com/openclaw/openclaw/issues/108336) | Fix | npm plugin singleton-array metadata 兼容修复（已发布 v2026.7.1-2） | ✅ Merged |
| [#106961](https://github.com/openclaw/openclaw/issues/106961) | Fix | Codex progress replies 终止逻辑修复（已发布 v2026.7.1-1） | ✅ Merged |

### 即将合并的关键 PR（等待审查）

- **[PR #118884](https://github.com/openclaw/openclaw/pull/118884)** — Control UI 重复提交队列化修复，解决用户连续操作被丢弃的问题（P1，合并风险：消息投递）
- **[PR #118409](https://github.com/openclaw/openclaw/pull/118409)** — 沙箱网关锁隔离修复，防止 live state 目录污染（P1，合并风险：兼容性/可用性）
- **[PR #118211](https://github.com/openclaw/openclaw/pull/118211)** — 网络策略敏感凭证脱敏修复，补充 AWS/GCP 签名参数遮盖（P1，合并风险：安全边界）

> **整体判断：** 项目正从"功能扩张"转向"稳定性深耕"阶段，今日大量 PR 聚焦于消息投递可靠性、会话状态一致性和安全边界加固。

---

## 4. 社区热点

### 🔥 讨论最激烈的 Issues（按评论数排序）

| Issue | 标题 | 评论数 | 状态 | 核心诉求 |
|-------|------|--------|------|---------|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | DeepSeek v4 Flash 静默回复失败 | 101 | ✅ 已关闭 | 模型调用无响应时缺乏有效错误处理和用户通知 |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | Realtime voice 会话资源泄漏 | 52 | 🟡 开放 | 语音会话在 provider 行为异常时无法释放资源 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Memory Trust Tagging by Source | 24 | 🟡 开放 | 按来源对记忆条目进行可信度标记，防止记忆投毒攻击 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent 完成结果静默丢失 | 23 | 🟡 开放 | 子代理超时/异常时无重试、无通知、无自动重启 |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | 统一文件名编码工具 | 20 | 🟡 开放 | 多编码 Content-Disposition 处理（Shift-JIS/EUC-KR/GB18030） |

### 🔥 热门 PR（按关注度）

- **[PR #119047](https://github.com/openclaw/openclaw/pull/119047)** — Canvas agent 测试覆盖补充（QA）
- **[PR #118884](https://github.com/openclaw/openclaw/pull/118884)** — Control UI 提交去重修复（P1，合并风险高）
- **[PR #97103](https://github.com/openclaw/openclaw/pull/97103)** — Codex sessions cleanup 归档报告修复
- **[PR #111146](https://github.com/openclaw/openclaw/pull/111146)** — 飞书回复会话冲突可见提示修复

---

## 5. Bug 与稳定性

### 高优先级 Bug（P0/P1）

| Issue | 严重程度 | 问题描述 | Fix PR |
|-------|---------|---------|--------|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | **P1** | DeepSeek v4 Flash 静默失败，无回复生成 | ✅ 已关闭 |
| [#117956](https://github.com/openclaw/openclaw/issues/117956) | **P1** | `CLAUDE_CLI_CLEAR_ENV` 未彻底清除 ANTHROPIC_API_KEY，单日产生 13.7M token 计费 | 🟡 待处理 |
| [#103804](https://github.com/openclaw/openclaw/issues/103804) | **P0** | service-env 生成器双引号问题破坏 AWS_REGION 主机名 | 🟡 待处理 |
| [#87744](https://github.com/openclaw/openclaw/issues/87744) | **P1** | Codex  backed Telegram 轮次反复超时，无法到达 terminal `turn/completed` | 🟡 待处理 |
| [#116022](https://github.com/openclaw/openclaw/issues/116022) | **P1** | beta.5 `/new` 复用稳定会话 ID，无法恢复已退休的 Codex binding tombstone | 🟡 待处理 |
| [#115700](https://github.com/openclaw/openclaw/issues/115700) | **P1** | `chat.send` 在模型完成后返回 "thread switched branches" 错误 | 🟡 待处理 |
| [#111010](https://github.com/openclaw/openclaw/issues/111010) | **P1** | Detached native Codex subagent 在父 turn 释放后丢失 hook relay | 🟡 待处理 |
| [#89315](https://github.com/openclaw/openclaw/issues/89315) | **P1** | Gateway heap 无界增长，Linux systemd --user 部署被 cgroup OOM 终止 | 🟡 待处理 |
| [#114234](https://github.com/openclaw/openclaw/issues/114234) | **P1** | 容器环境下 usage-cost refresh lock 在重启后无法释放，永久冻结缓存 | 🟡 待处理 |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | **P1** | Realtime voice 会话资源泄漏（provider/consult state 无界保留） | 🟡 待处理 |

### 中优先级 Bug（P2/P3）

| Issue | 问题描述 | Fix PR |
|-------|---------|--------|
| [#45765](https://github.com/openclaw/openclaw/issues/45765) | `OPENCLAW_HOME=~/.openclaw` 产生嵌套目录 `~/.openclaw/.openclaw`（回归） | ✅ 已关闭 |
| [#112906](https://github.com/openclaw/openclaw/issues/112906) | `richMessages: true` 下 ```` 标签渲染回退（v2026.7.1 回归） | 🟡 待处理 |
| [#52249](https://github.com/openclaw/openclaw/issues/52249) | ACP 父会话在等待子代理完成时卡住，需手动刷新 | 🟡 待处理 |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | 长对话后 write/exec tool 参数静默丢失 | 🟡 待处理 |
| [#91144](https://github.com/openclaw/openclaw/issues/91144) | Windows Scheduled Task 无法保持 gateway 运行 | 🟡 待处理 |
| [#39807](https://github.com/openclaw/openclaw/issues/39807) | 402 Billing error 导致内联 provider 无限重试死亡螺旋（无退避） | ✅ 已关闭 |

### 回归问题汇总

- **#45765** — `OPENCLAW_HOME` 嵌套目录（已修复）
- **#112906** — `richMessages` ```` 标签渲染回退
- **#39807** — Billing error 无限重试（已修复）

---

## 6. 功能请求与路线图信号

| Issue | 功能请求 | 社区支持 | 路线图判断 |
|-------|---------|---------|-----------|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Memory Trust Tagging by Source（按来源可信度标记记忆条目） | 24 评论 | ⭐ **高优先级** — 安全审计需求明确，可能纳入下一安全版本 |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | 统一文件名编码工具（多编码 Content-Disposition） | 20 评论，2 👍 | 🟡 **中期** — PR #48578 已修复 UTF-8 个案，架构级修复待推进 |
| [#40786](https://github.com/openclaw/openclaw/issues/40786) | Backup CLI 支持 .gitignore 风格排除模式 | 10 评论，1 👍 | 🟡 **中期** — 大型备份和敏感数据隔离需求 |
| [#45758](https://github.com/openclaw/openclaw/issues/45758) | YAML 配置文件格式支持 | 9 评论，2 👍 | 🟢 **低优先级** — DevOps 友好性改进 |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) | Control UI MathJax/LaTeX 支持 | 9 评论，**10 👍** | 🟡 **中期** — 高赞但非核心功能 |
| [#16670](https://github.com/openclaw/openclaw/issues/16670) | Onboarding Wizard 强制 Memory/Embedding 配置 | 8 评论，1 👍 | 🟡 **中期** — 改善新手体验 |
| [#13700](https://github.com/openclaw/openclaw/issues/13700) | Session Snapshots（保存/加载上下文检查点） | 6 评论 | 🟢 **长期** — 高级功能，依赖会话系统重构 |
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | 自托管 STT/TTS provider 支持（webchat） | 8 评论，2 👍 | 🟡 **中期** — 企业私有化部署需求 |

---

## 7. 用户反馈摘要

### 核心痛点

1. **消息可靠性焦虑**（高频关键词：silent failure, message loss, stuck）
   - 用户反复遭遇"静默失败"场景：模型不回复、子代理结果丢失、轮次超时
   - 痛点：缺乏可观测性和自动恢复机制，用户只能手动发现和处理

2. **会话状态管理脆弱**（高频关键词：session stuck, timeout, tombstone）
   - Codex binding 退休后无法恢复、父会话卡在 yielded 状态、context 被异常压缩
   - 痛点：恢复路径依赖手动干预（refresh UI），自动化修复能力不足

3. **Provider 兼容性成本高**
   - DeepSeek v4 Flash 静默失败、Poe 媒体模型配置接受但运行时失败、Claude API key 清理不彻底
   - 痛点：多 provider 场景下故障排查困难，错误信息不够明确

4. **安全与隐私关切**
   - `CLAUDE_CLI_CLEAR_ENV` 未能完全清除 API key，单日产生 13.7M token 意外计费
   - 记忆投毒攻击风险引发对 Memory Trust Tagging 的强烈需求

### 用户满意度信号

- 👍 **高赞反馈：** MathJax 支持（10 👍）、Self-hosted STT/TTS（2 👍）、CommitmentsConfig model override（2 👍）
- ⚠️ **负面反馈：** `richMessages` 回归、Windows Scheduled Task 稳定性、Telegram 群聊 activation 模式失效

---

## 8. 待处理积压

### ⚠️ 维护者需优先关注

| Issue/PR | 类型 | 积压原因 | 建议行动 |
|----------|------|---------|---------|
| [#117956](https://github.com/openclaw/openclaw/issues/117956) | Bug P1 | 安全边界漏洞 + 实际资损（13.7M token），创建于 2026-08-02，尚无 fix PR | **紧急** — 审查 `CLAUDE_CLI_CLEAR_ENV` 实现 |
| [#103804](https://github.com/openclaw/openclaw/issues/103804) | Bug P0 | service-env 双引号破坏 AWS 配置，影响大规模部署，创建于 2026-07-10 | **高优** — 环境序列化逻辑审查 |
| [#89315](https://github.com/openclaw/openclaw

---

## 横向生态对比



# AI 智能体开源生态横向对比分析报告
**日期：2026-08-04 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026-08-04，个人 AI 助手开源生态呈现"一超多强、分层明显"的格局。OpenClaw 以每日 500+ Issue/PR 的超级活跃度稳居生态核心，持续从功能扩张转向稳定性深耕。NanoBot、IronClaw、CoPaw 构成第二梯队，合计贡献超 100 条 PR，聚焦 Wave 3 架构重构、流式 tool-call 补齐与桌面端体验优化。PicoClaw、NanoClaw、NullClaw、LobsterAI 处于稳健维护期，Moltis 以单一架构级 PR 推进 MCP 标准化。整体生态正从"拼功能"阶段迈入"拼可靠性"的成熟期。

---

## 2. 各项目活跃度对比

| 项目 | Issues | PRs | Release | 健康度 |
|------|--------|-----|---------|--------|
| **OpenClaw** | 500 (463 活跃/37 关闭) | 500 (361 待审/139 已合) | v2026.7.1-1、v2026.7.1-2 | ✅ 优秀 |
| **IronClaw** | 47 | 50 | — | ✅ 优秀 |
| **CoPaw** | 14 | 50 | v2.1.0-beta.1 | ✅ 良好 (B+) |
| **NanoBot** | 3 (2 新/1 关闭) | 32 (12 待审/20 已合) | — | ✅ 良好 |
| **PicoClaw** | 8 (3 活跃/5 关闭) | 5 (2 待审/3 已合) | — | 🟡 中等 |
| **NanoClaw** | 1 | 9 (3 待审/6 已合) | — | 🟡 中等 |
| **NullClaw** | 1 | 5 | — | 🟡 中等 |
| **LobsterAI** | 2 (均为新开) | 12 (7 已合/5 待审) | — | 🟡 中等 |
| **Moltis** | 0 | 1 (待审) | — | 🟡 偏低 |
| **ZeptoClaw** | 0 | 0 | — | ⚪ 停滞 |
| **Hermes Agent** | — | — | ⚠️ 摘要失败 | ⚪ 未知 |
| **ZeroClaw** | — | — | ⚠️ 摘要失败 | ⚪ 未知 |

---

## 3. OpenClaw 在生态中的定位

**生态地位：** OpenClaw 是今日活动量最大的单一项目，Issue/PR 日处理量约为第二梯队（IronClaw + CoPaw）总和的 2-3 倍，处于绝对的"核心参照"位置。

**对比优势：**
- **问题覆盖面最广**：500 条 Issue 涉及消息可靠性、会话状态、Provider 兼容性、安全边界等全链路，反映其用户基数与部署场景的多样性
- **补丁发布最频繁**：24 小时内 2 个 patch 版本（v2026.7.1-1、-2），修复节奏领先
- **社区自驱能力强**：大量 PR 来自外部贡献者（如 @joshavant、@arcdrake22 等），非纯维护者驱动

**技术路线差异：**
| 维度 | OpenClaw | IronClaw | CoPaw | NanoBot |
|------|----------|----------|-------|---------|
| 核心架构 | Model Gateway + Agent Loop 解耦 | Wave 3 容器化 + secret 收紧 | Skills + ACP 协议优先 | Provider 层适配优先 |
| 部署形态 | 服务端 Gateway + Control UI | 全栈 Rust 重写（Reborn） | 桌面端 WebView2 生态 | 轻量多渠道 Bot |
| MCP 定位 | 沙箱网关隔离 | 生命周期托管 | 能力声明式 | 多源搜索聚合 |
| 主要渠道 | Telegram/飞书/Codex | Google Workspace/WebChat | Feishu/微信/Console | Discord/Telegram/Mattermost |

**社区规模推断：** OpenClaw 日处理量级（500 Issue + 500 PR）意味着其 GitHub 仓库至少有数百活跃贡献者，远超其他项目（NanoBot 日 32 PR、CoPaw 日 50 PR 量级），预估星数与fork数在生态中排名第一。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|---------|---------|
| **消息/会话可靠性** | OpenClaw、NanoClaw、CoPaw、PicoClaw | 静默失败无通知（OpenClaw #116277/#44925）、会话状态恢复（NanoClaw #3183/#3184）、ACP 竞态文本丢失（CoPaw #6625）、长历史输入卡顿（PicoClaw #3281） |
| **Provider 兼容性与成本** | OpenClaw、NanoBot | API Key 未彻底清除导致意外计费（OpenClaw #117956）、Opus 5/DeepSeek v4 Flash 适配滞后（NanoBot #5235/#5214）、Billing error 无限重试（OpenClaw #39807 已修复） |
| **MCP 生态集成** | NanoBot、NanoClaw、Moltis、IronClaw | 远程 Streamable HTTP MCP（NanoClaw #3092）、MCP 业务错误被忽略（NanoBot #5237）、MCP 挂起无超时保护（PicoClaw #3269）、仓库级 MCP Bundle 管理（Moltis #1183） |
| **安全与凭据管理** | OpenClaw、NullClaw、IronClaw | Gateway heap 无界增长 OOM（OpenClaw #89315）、curl 凭据 mode-0600 临时文件传递（NullClaw #983）、destructiveHint 默认值与 MCP 规范冲突（IronClaw #7068） |
| **流式响应体验** | NullClaw、IronClaw、CoPaw | 流式 tool-call 结构化支持（NullClaw #964/#965）、SSE 每次 chunk 触发重连状态闪烁（IronClaw #7071）、GPT-5.6 prompt caching（CoPaw #6649） |
| **可观测性与错误恢复** | IronClaw、OpenClaw | error-recoverability 架构设计（IronClaw #6284）、子代理结果静默丢失无自动恢复（OpenClaw #44925） |
| **平台适配** | NanoBot、CoPaw、LobsterAI | 中文输入法 IME 稳定性（NanoBot #5229）、WebView2 崩溃无恢复（CoPaw #6647）、Windows NSIS 安装程序进程残留（LobsterAI #2420） |

---

## 5. 差异化定位分析

| 维度 | OpenClaw | IronClaw | CoPaw | NanoBot | PicoClaw | NanoClaw | NullClaw | LobsterAI | Moltis |
|------|----------|----------|-------|---------|----------|----------|----------|-----------|--------|
| **功能侧重** | 全渠道网关 + 会话引擎 | Wave 3 架构重构 + 企业级可靠性 | 桌面端 Skills + ACP 协议 | 多 Provider 适配 + 搜索增强 | 路由系统 + 渠道本地化 | 会话生命周期 + 安全加固 | 流式 tool-call + 安全传输 | 运营活动 + 安装体验 | MCP Bundle 管理 |
| **目标用户** | 企业/个人全场景用户 | 企业级部署（Rust 重写） | 桌面端用户（Windows/Mac） | 多模型爱好者 | 日本语用户 | 旧版 Node 环境用户 | 生产级调度场景 | 中国私有化部署用户 | MCP 配置管理者 |
| **技术架构** | Node.js Gateway + Control UI | 纯 Rust（Reborn）+ 容器化 | Electron + WebView2 + ACP | Python + 多渠道 Channel | Node.js + 路由分发 | Node.js + Hardened 镜像 | Rust + curl 安全通道 | Electron + 积分系统 | Rust + Vault 集成 |
| **差异化卖点** | 规模最大的插件生态 | 架构级可靠性 + 错误恢复 | 桌面端 OS 级集成 | 多源搜索 + 跨会话能力 | 日语本地化 + Telegram Forum | 会话自动恢复 + imessage | 流式结构化 tool-call | 积分运营 + 安装稳定性 | 仓库级 MCP Bundle |

---

## 6. 社区热度与成熟度

```
活跃度分层
┌─────────────────────────────────────────────────┐
│  🔴 超活跃（日 PR > 100）                        │
│     OpenClaw                                    │
├─────────────────────────────────────────────────┤
│  🟠 高活跃（日 PR 30-100）                       │
│     IronClaw、CoPaw                             │
├─────────────────────────────────────────────────┤
│  🟡 中活跃（日 PR 5-30）                         │
│     NanoBot、PicoClaw、NanoClaw、NullClaw       │
│     LobsterAI                                   │
├─────────────────────────────────────────────────┤
│  🟢 低活跃（日 PR < 5）                          │
│     Moltis                                      │
├─────────────────────────────────────────────────┤
│  ⚪ 停滞/未知                                    │
│     ZeptoClaw、Hermes Agent、ZeroClaw            │
└─────────────────────────────────────────────────┘
```

**成熟度判断：**
- **快速迭代阶段**：OpenClaw（功能→稳定性转型期，日均处理量仍维持高位）、CoPaw（v2.1.0-beta 发布中，多项桌面端能力并行开发）、NanoBot（ Provider 适配持续补充）
- **质量巩固阶段**：IronClaw（Wave 3 重构冲刺，大量 P1 bug bash 待修）、NanoClaw（安全加固+会话恢复）、NullClaw（安全传输路径补齐）
- **功能拓展阶段**：PicoClaw（路由+本地化）、LobsterAI（运营功能完善）
- **架构重构阶段**：Moltis（MCP 仓库 Bundle 化）

---

## 7. 值得关注的趋势信号

### 趋势一：从"能用"到"可靠"——稳定性成为生态分水岭
OpenClaw 的 500 条 Issue 中，**静默失败、会话状态丢失、资源泄漏** 三类问题占比超 60%；IronClaw 的 bug bash 暴露了 6 项 P1/P2 用户体验问题。这说明生态已从功能竞赛进入可靠性深水区，**错误恢复能力**（IronClaw #6284、OpenClaw #44925）将成为区分项目成熟度的关键指标。

> **对开发者的参考价值：** 在设计 Agent 系统时，优先构建可观测的错误恢复机制（超时、重试、状态快照），而非堆叠功能。

### 趋势二：MCP 生态从"连接"走向"管理"
Moltis 的仓库 Bundle 管理（#1183）、NanoClaw 的远程 Streamable HTTP MCP（#3092）、NanoBot 的 MST 多源搜索（#5234）共同指向一个方向：**MCP 不再是简单的工具注册，而是需要版本管理、安全审计、生命周期管控的基础设施**。

> **对开发者的参考价值：** 考虑将 MCP 服务器纳入 GitOps 流程，实现配置的声明式管理和版本回滚。

### 趋势三：Provider 适配成本仍是最大痛点
OpenClaw 的 DeepSeek v4 Flash 静默失败（#116277）、Claude API Key 清理不彻底（#117956）、NanoBot 的 Opus 5 配置被拒（#5235）、DeepSeek reasoning 格式不兼容（#5214），均反映 **多 Provider 兼容性是生态中最普遍且最难根除的问题**。

> **对开发者的参考价值：** 建立 Provider 能力声明式描述（如 NanoBot #5204 的 Responses capabilities）和统一的错误分类体系，而非硬编码 provider 名称检查。

### 趋势四：桌面端体验成为新战场
CoPaw 的 WebView2 崩溃无恢复（#6647）、文件拖入多行显示（#6583）、产出物目录组织（#6643），LobsterAI 的 Windows 安装程序稳定性（#2420），PicoClaw 的日语本地化（#3273），NanoBot 的 IME 稳定性（#5229）——**桌面端用户交互细节**正在成为差异化竞争点。

> **对开发者的参考价值：** 桌面端产品的竞答优势不再来自 Agent 能力本身，而来自对平台交互规范的深度适配。

### 趋势五：安全边界从"可选"变为"必选项"
NullClaw 的 curl 凭据 mode-0600 传递（#983/#982）、OpenClaw 的 Memory Trust Tagging（#7707）、IronClaw 的 destructiveHint 规范对齐（#7068）、CoPaw 的聊天通道身份泄漏（#6382）——**安全从功能附庸升级为架构核心**。

> **对开发者的参考价值：** 在架构设计初期即纳入凭据安全、记忆可信度标记、最小权限原则，避免后期重构成本。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报
**日期：2026-08-04** | 数据周期：2026-08-03 00:00 ~ 2026-08-04 00:00 (UTC+8)

---

## 1. 今日速览

NanoBot 今日保持高活跃度，24小时内共产生 32 条 PR 更新（待合并 12 / 已合并 20）及 3 条 Issue 更新（新开 2 / 已关闭 1），PR 合并比率为 62.5%，贡献节奏健康。核心维护者 `chengyongru` 集中推进 WebUI 体验优化与 Anthropic 适配，`arcdrake22` 专注 Provider 层稳定性修复，多线并进推动项目向前。无新版本发布，但多项 P1 级修复已落地，整体项目健康度 **良好**。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 作者 | 进展说明 |
|----|------|------|---------|
| [#5236](https://github.com/HKUDS/nanobot/pull/5236) | bugfix, provider, p1 | chengyongru | **Anthropic Opus 5 适配**：将硬编码的 sampling 参数排除逻辑替换为模型族版本阈值，支持 Opus 5 的 `effort` 控制，修复新模型配置被 API 拒绝的问题 |
| [#5228](https://github.com/HKUDS/nanobot/pull/5228) | bugfix, webui, p1 | chengyongru | **本地触发消息显示修复**：持久化各本地触发器收到的最新消息，在自动化载荷中返回真实触发内容，解决 WebUI Session 气泡仅显示命令而丢失触发上下文的问题 |
| [#5227](https://github.com/HKUDS/nanobot/pull/5227) | bugfix, webui, p1 | chengyongru | **WebUI 国际化完整审计**：修正简化/繁体中文术语（`网页` → `网络`，`网页搜索` → `网络搜索`），本地化剩余硬编码 UI 与无障碍标签 |
| [#5232](https://github.com/HKUDS/nanobot/pull/5232) | feature, webui, p2 | goodtiding5 | **Mattermost 线程分离策略**：为 Mattermost 渠道新增 `groupPolicyInThread` 配置，区分线程与普通频道的 mention 要求 |
| [#5214](https://github.com/HKUDS/nanobot/pull/5214) | bugfix, provider, p1 | arcdrake22 | **DeepSeek reasoning 兼容修复**：修正通过 OpenAI Responses API 路由时 DeepSeek reasoning items 的 wire 格式，避免反序列化失败 |
| [#1550](https://github.com/HKUDS/nanobot/pull/1550) | feature, provider | Mieluoxxx | **OpenAI Codex 双模式**：在 `openai_codex` 中同时支持 OAuth 与自定义 Responses 模式，用户配置 `api_base`/`api_key` 时自动切换 |
| [#5038](https://github.com/HKUDS/nanobot/pull/5038) | docs, provider, p2 | Krislu1221 | **ModelScope 文档补充**：新增魔搭模型平台内置 Provider 的完整配置说明与示例 |
| [#5229](https://github.com/HKUDS/nanobot/pull/5229) | bugfix, webui, p2 | chengyongru | **IME 输入稳定性**：延迟 textarea 自动调整至输入法提交阶段，修复中文输入法下线程滚动位置异常 |
| [#4861](https://github.com/HKUDS/nanobot/pull/4861) | feature, provider, p2 | MVS-source | **Eden AI 接入**：新增 Eden AI 作为 OpenAI 兼容网关 Provider，保留其原生 `provider/model` ID 格式 |
| [#5226](https://github.com/HKUDS/nanobot/pull/5226) | bugfix, webui, p2 | chengyongru | **移动端键盘收起**：发送后自动 blur textarea，确保移动端虚拟键盘正常关闭 |
| [#5215](https://github.com/HKUDS/nanobot/pull/5215) | bugfix, p1 | arcdrake22 | **Gateway 资源确定性释放**：修复停止 Gateway 时 exec session/MCP 子进程未关闭导致的 asyncio 清理噪声与停滞 |
| [#5213](https://github.com/HKUDS/nanobot/pull/5213) | bugfix, plugins, p2 | KDB-Wind | **uv pip fallback**：在 `pip` 不可用时自动回退 `uv` 安装包管理，解决 uv tool 环境下插件启用失败问题 |

**整体推进**：今日 20 条 PR 合并/关闭中，P1 级修复占比 45%（9/20），涵盖 Provider 兼容性、WebUI 关键体验、Gateway 稳定性，项目整体向前迈进显著。

---

## 4. 社区热点

### 讨论活跃 / 关注度较高的条目

| 类型 | 编号 | 标题 | 热度分析 |
|------|------|------|---------|
| PR | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | feat(agent): integrate mst-python as a metasearch provider | **高潜力**：引入 MST 多源搜索引擎聚合（RRF 融合），若合并将大幅提升搜索覆盖度，解决单一引擎结果不足痛点 |
| PR | [#5211](https://github.com/HKUDS/nanobot/pull/5211) | feat(session): add cross-session search and mentions | **高价值**：跨会话搜索与 `@` 引用功能，拓展 Agent 记忆检索边界，对多会话用户意义重大 |
| PR | [#5204](https://github.com/HKUDS/nanobot/pull/5204) | refactor(providers): declare Responses capabilities | **架构级**：声明式能力描述替代硬编码 provider name 检查，改善 OpenAI/Copilot/DeepSeek 路由可维护性 |
| Issue | [#5237](https://github.com/HKUDS/nanobot/issues/5237) | MCP tool "data not found" 被忽略，等待 tool_timeout | **用户痛点明确**：MCP 业务错误未被正确识别，直接影响工具调用可靠性，已有明确复现路径 |
| Issue | [#5235](https://github.com/HKUDS/nanobot/issues/5235) | Opus 5 配置被 API 拒绝 | **时效性强**：Opus 5 于 2026-07-24 发布，配置适配滞后，已有 PR #5236 跟进修复 |

---

## 5. Bug 与稳定性

| 严重级别 | Issue/PR | 描述 | Fix 状态 |
|----------|----------|------|---------|
| 🔴 P1 | [#5237](https://github.com/HKUDS/nanobot/issues/5237) | MCP 工具返回 `isError=False` 的业务错误被 Agent 忽略，导致无效等待直至 `tool_timeout` | **未修复** |
| 🔴 P1 | [#5235](https://github.com/HKUDS/nanobot/issues/5235) | Opus 5 的 `omit_temperature` 排除列表未更新，导致配置被 API 拒绝 | ✅ **已修复**：PR [#5236](https://github.com/HKUDS/nanobot/pull/5236) |
| 🟡 P2 | [#5190](https://github.com/HKUDS/nanobot/issues/5190) | 前端 JS 模块加载 MIME 类型为 `text/plain` 失败 | ✅ **已关闭**（推测已修复） |
| 🟡 P2 | — | [#5229](https://github.com/HKUDS/nanobot/pull/5229) IME 输入时线程滚动位置异常 | ✅ **已合并** |
| 🟡 P2 | — | [#5215](https://github.com/HKUDS/nanobot/pull/5215) Gateway 停止时子进程残留导致 teardown 噪声 | ✅ **已合并** |
| 🟡 P2 | — | [#5214](https://github.com/HKUDS/nanobot/pull/5214) DeepSeek reasoning 数据格式不兼容 Responses API | ✅ **已合并** |

**稳定性评估**：今日 1 个 P1 Bug 待修复（MCP 错误处理），1 个 P1 已闭环，P2 级别修复均已完成。整体稳定性 **良好**。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 信号强度 | 预期纳入版本 |
|------|------|---------|-------------|
| MST 多源搜索引擎聚合 | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | ⭐⭐⭐⭐ 高 | 下一版本（P1，已有完整实现） |
| 跨会话搜索与 `@` 引用 | [#5211](https://github.com/HKUDS/nanobot/pull/5211) | ⭐⭐⭐⭐ 高 | 下一版本或下两版本（P2，已实现核心逻辑） |
| Mattermost 线程分离策略 | [#5233](https://github.com/HKUDS/nanobot/pull/5233) | ⭐⭐⭐ 中 | 近期迭代（P2，待合并） |
| Eden AI 网关接入 | [#4861](https://github.com/HKUDS/nanobot/pull/4861) | ⭐⭐⭐ 中 | 已合并，随下一版本发布 |
| Dream 空闲会话归档 | [#5231](https://github.com/HKUDS/nanobot/pull/5231) | ⭐⭐ 较低 | 视优先级排期（P2） |
| 声明式 Responses 能力描述 | [#5204](https://github.com/HKUDS/nanobot/pull/5204) | ⭐⭐⭐⭐ 高 | 近期（P1，架构重构） |

---

## 7. 用户反馈摘要

### 真实痛点
- **MCP 错误语义丢失**（[#5237](https://github.com/HKUDS/nanobot/issues/5237)）：用户反馈 MCP 工具返回业务错误（如 `404 data not exist`）时，Agent 无法识别失败，白白等待超时，严重影响工具调用可靠性。
- **新模型适配滞后**（[#5235](https://github.com/HKUDS/nanobot/issues/5235)）：Opus 5 发布后配置被拒，用户关注官方对新模型参数的及时跟进。
- **前端 MIME 类型错误**（[#5190](https://github.com/HKUDS/nanobot/issues/5190)）：项目启动时 JS 模块加载失败，影响首次体验。
- **中文输入法体验**（[#5229](https://github.com/HKUDS/nanobot/pull/5229)）：IME 输入时线程滚动位置跳变，对中文用户影响显著，已修复。

### 用户满意点
- WebUI 国际化持续完善，术语一致性提升。
- Gateway 停止时资源确定性释放，运维体验改善。
- 新增 Provider（Eden AI、ModelScope）丰富了模型选择。

---

## 8. 待处理积压

| 类型 | 编号 | 描述 | 建议跟进 |
|------|------|------|---------|
| 🐛 Bug | [#5237](https://github.com/HKUDS/nanobot/issues/5237) | MCP 工具业务错误被忽略，Agent 无法正确响应 | **建议 P1 优先处理**，影响工具调用链正确性 |
| 🆕 PR | [#5233](https://github.com/HKUDS/nanobot/pull/5233) | Mattermost 线程分离策略（待合并版本） | 与 [#5232](https://github.com/HKUDS/nanobot/pull/5232) 重复，需确认保留哪个 |
| 🆕 PR | [#5211](https://github.com/HKUDS/nanobot/pull/5211) | 跨会话搜索与 mention（待合并） | 功能价值高，建议推进 Code Review |
| 🆕 PR | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | MST 搜索引擎接入（待合并） | 搜索能力增强，建议优先评估合并 |
| 🆕 PR | [#5204](https://github.com/HKUDS/nanobot/pull/5204) | Responses 能力声明式重构（待合并，标记 conflict） | 架构改动，需解决冲突后合并 |
| 🆕 PR | [#5231](https://github.com/HKUDS/nanobot/pull/5231) | Dream 空闲会话归档（待合并） | 功能明确，建议排期评估 |

---

**报告生成时间**：2026-08-04 | **数据来源**：GitHub API (HKUDS/nanobot) | **分析师**：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-04

---

## 1. 今日速览

过去24小时项目保持中等活跃度，共处理 **8条 Issue**（3活跃/5已关闭）和 **5条 PR**（2待合并/3已合并）。主要进展集中在 **路由系统修复**、**日本语本地化落地** 和 **Telegram话题支持** 三个方向，整体项目健康度良好，但存在多个未关闭的稳定性 Bug（MCP挂起、输入卡顿）需持续关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR

| PR | 作者 | 说明 |
|---|---|---|
| [#3267](https://github.com/sipeed/picoclaw/pull/3267) | sarff | 修复 antigravity token 刷新时 scope 传递错误导致的 `PERMISSION_DENIED` 问题 |
| [#3273](https://github.com/sipeed/picoclaw/pull/3273) | honbou | 完成 WebUI 日语本地化，补充 `ja.json`（968行）并注册 dayjs 语言包 |
| [#3202](https://github.com/sipeed/picoclaw/pull/3202) | Osamaali313 | 修复路由 ID 规范化逻辑，去除首尾下划线使其符合 ID 格式约束 |

**总结**：今日合并的 PR 以稳定性修复和本地化为主，为路由分发和国际化体验提供了实质性改进，整体向前推进了约 **3 个独立改进点**。

### 待合并 PR

| PR | 作者 | 优先级 | 说明 |
|---|---|---|---|
| [#3316](https://github.com/sipeed/picoclaw/pull/3316) | j-v | 🔴 高 | 修复 dispatch rules 路由 agent 的上下文管理，使 history/summarization/compression 行为与默认 agent 一致 |
| [#3315](https://github.com/sipeed/picoclaw/pull/3315) | genuss | 🟡 中 | 支持 Telegram 私人聊天中的 Forum Topic 模式（通过 `IsTopicMessage` 字段识别） |

---

## 4. 社区热点

- **[#3281](https://github.com/sipeed/picoclaw/issues/3281)** 🏷️ [BUG] Web UI 长历史会话下输入框严重卡顿（👍 1，3 条评论）  
  用户反映在 WebUI 中 chat 历史较长时输入框响应明显滞后，是 Web 端体验的痛点。目前仍为 `OPEN` 状态。

- **[#3269](https://github.com/sipeed/picoclaw/issues/3269)** 🏷️ [BUG] MCP server 连接失败导致 agent 循环挂起、界面停止响应（👍 1，2 条评论）  
  MCP 服务端不可用时 agent loop 无超时保护，直接造成聊天界面"死锁"，用户体验影响较大，且暂无 fix PR。

- **[#3276](https://github.com/sipeed/picoclaw/issues/3276)** [Feature] Launcher 支持检测 systemd 外部管理的 gateway 生命周期  
  已被合并，反映服务器端用户希望对部署方式有更灵活的管控能力。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP server 连接失败 → agent 循环挂起，界面停止回复 | 无 |
| 🔴 高 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | WebUI 长历史会话输入卡顿 | 无 |
| 🔴 高 | [#3301](https://github.com/sipeed/picoclaw/issues/3301) | dispatch rules 路由 agent 中 `/clear` 和 session 自动压缩失效 | [#3316](https://github.com/sipeed/picoclaw/pull/3316)（待合并） |
| 🟡 中 | [#3264](https://github.com/sipeed/picoclaw/issues/3264) | `SplitMessage` 在超长 fenced-code info string 下死循环（已关闭，推测由相关 PR 修复） | — |
| 🟡 中 | [#3268](https://github.com/sipeed/picoclaw/issues/3268) | `exec` tool 的 `action` 参数应默认为 `"run"` 而非必填（已关闭） | — |
| 🟢 低 | [#3265](https://github.com/sipeed/picoclaw/issues/3265) | Gateway 启动报未知 `deltachat` channel 类型（已关闭） | — |

**本周关键风险**：`#3269`（MCP 挂起）无对应 PR，建议优先跟进。

---

## 6. 功能请求与路线图信号

| 诉求 | 来源 | 状态 |
|---|---|---|
| 路由 agent 的上下文/压缩行为与默认 agent 一致 | [#3301](https://github.com/sipeed/picoclaw/issues/3301) | 已有 PR [#3316](https://github.com/sipeed/picoclaw/pull/3316) 正在处理 |
| Telegram 私人聊天 Forum Topic 支持 | [#3315](https://github.com/sipeed/picoclaw/pull/3315) | PR 待合并 |
| 日语本地化 | [#3272](https://github.com/sipeed/picoclaw/issues/3272) | 已合并 ✅ |
| Launcher systemd 生命周期检测 | [#3276](https://github.com/sipeed/picoclaw/issues/3276) | 已合并 ✅ |

**路线图信号**：用户社区对 **路由分发场景的完整性** 和 **渠道扩展**（Telegram Forum Topics）有明确诉求，且已有对应 PR，预计将纳入近期版本。

---

## 7. 用户反馈摘要

- **WebUI 性能**：长会话历史导致输入卡顿（`#3281`），是 Web 端体验的核心痛点。
- **部署灵活性**：服务器场景用户希望 Launcher 能感知外部进程管理（systemd），而非强制接管 gateway 生命周期（`#3276`）。
- **工具可用性**：`exec` tool 的 `action` 参数不应强制要求，期望默认值（`#3268`）。
- **国际化**：日语本地化需求得到满足（`#3273`），社区对多语言支持持正面态度。
- **MCP 稳定性**：MCP server 断开导致整个 agent 无响应是严重体验问题，用户期望更健壮的超时和容错机制（`#3269`）。

---

## 8. 待处理积压

| Issue / PR | 作者 | 未响应时长 | 备注 |
|---|---|---|---|
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) | xpader | ~14 天（自创建） | WebUI 输入卡顿，无 PR 跟进 |
| [#3269](https://github.com/sipeed/picoclaw/issues/3269) | ruiyigen | ~15 天（自创建） | MCP 挂起导致界面死锁，无 PR 跟进，建议优先级提升 |

> ⚠️ 上述两个 Bug 已标记 `stale` 但仍为 `OPEN` 状态，建议维护者重点关注。

---

**评估结论**：PicoClaw 项目在路由系统和本地化方向有持续产出，但 WebUI 性能和 MCP 容错是两个亟待修复的稳定性隐患，建议近期版本优先解决。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报 — 2026-08-04

---

## 1. 今日速览

NanoClaw 在过去24小时内保持中等活跃度：共提交 **10 条**变更记录（1 Issue + 9 PR），其中 **6 条已合并/关闭**，**3 条待合并**，无新版本发布。核心进展集中在安全性加固（硬化的 agent 镜像）、会话生命周期管理修复以及 imessage 集成优化。社区报告了一个 Node.js 环境兼容性问题（`node:util.styleText`），目前尚无修复 PR。整体项目健康度良好，维护团队响应及时，PR 流转效率较高。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日共 **6 条 PR 被关闭/合并**，主要推进方向如下：

### 安全与基础设施
- **#3182** — 将 agent 镜像重新锁定至 `hardened-2026-08-02`，镜像体积由 611MB 增至 621MB，上游 digest 保持一致，仅基础镜像刷新。
  🔗 [PR #3182](https://github.com/qwibitai/nanoclaw/pull/3182)

- **#3180** — 暴露 hardened image migration 工作流，使用户可自主完成镜像迁移操作。
  🔗 [PR #3180](https://github.com/qwibitai/nanoclaw/pull/3180)

### 会话与消息链路修复
- **#3137** — 修复 engagement 一致性问题：保留累积消息为上下文而不触发 warm-container 轮次，允许 group 作用域的 agent 自检 wiring 并申请策略更新，同时拒绝无效的 JavaScript engagement 正则。
  🔗 [PR #3137](https://github.com/qwibitai/nanoclaw/pull/3137)

- **#3143** — 修复已审批 approval card 的内容丢失问题，卡片在呈现决定状态后仍保留标题与详情。
  🔗 [PR #3143](https://github.com/qwibitai/nanoclaw/pull/3143)

- **#3181** — 修复 imessage 集成：用户首次发送至指定线路的消息现在可正确 opt-in。
  🔗 [PR #3181](https://github.com/qwibitai/nanoclaw/pull/3181)

- **#3178** — 误开至本仓库的 PR，已关闭，无实质变更。
  🔗 [PR #3178](https://github.com/qwibitai/nanoclaw/pull/3178)

> **整体评估：** 今日合并的 PR 以运维加固和会话稳定性修复为主，未见大型功能落地，项目处于稳健维护周期。

---

## 4. 社区热点

### 🔴 活跃 Issue
- **#3179** — `SyntaxError: The requested module 'node:util' does not provide an export named 'styleText'`，由 `@clack/core@1.2.0` 引入，使用 PNPM 环境（JupyterLab）触发。
  - 作者：benjamin920102 | 创建：2026-08-03 | 评论：1 | 👍：0
  - 🔗 [Issue #3179](https://github.com/qwibitai/nanoclaw/issues/3179)
  - **分析：** 该错误源于 `node:util.styleText` 仅在 Node.js 18.16+ 引入，而用户环境可能运行较旧版本。此 Issue 已获 1 条评论，尚未分配修复 PR，建议维护者关注 Node 版本兼容性矩阵。

### 🟡 待合并 PR
- **#3184** — 修复 Claude 会话在 transcript 文件缺失时崩溃问题，改为自动轮转而非进入死会话。
  🔗 [PR #3184](https://github.com/qwibitai/nanoclaw/pull/3184)

- **#3183** — 修复 group-init 中 `cleanupPeriodDays` 未被锁定，导致静默30天以上的会话可能被错误清理。
  🔗 [PR #3183](https://github.com/qwibitai/nanoclaw/pull/3183)

- **#3092** — 支持远程 Streamable HTTP MCP 服务器（功能型 PR，影响面较大）。
  🔗 [PR #3092](https://github.com/qwibitai/nanoclaw/pull/3092)

---

## 5. Bug 与稳定性

| 严重级别 | 问题描述 | Issue/PR | 状态 |
|---------|---------|---------|------|
| 中 | Node.js 版本不兼容导致 `styleText` 导入失败（影响旧版 Node 环境） | [#3179](https://github.com/qwibitai/nanoclaw/issues/3179) | 待修复 |
| 高 | 会话 transcript 文件缺失时 AI 响应崩溃为 `No conversation found` 错误 | [#3184](https://github.com/qwibitai/nanoclaw/pull/3184) | **PR 已提交** |
| 高 | 长期静默会话因 `cleanupPeriodDays` 未锁定而被意外清理 | [#3183](https://github.com/qwibitai/nanoclaw/pull/3183) | **PR 已提交** |
| 低 | Approval card 在决策后丢失原始内容 | [#3143](https://github.com/qwibitai/nanoclaw/pull/3143) | ✅ 已修复 |

---

## 6. 功能请求与路线图信号

- **#3092** — 支持远程 Streamable HTTP MCP 服务器：该 PR 已开放近两周且标记为 `core-team`，若合并将显著提升 NanoClaw 的 MCP 生态兼容性，可能纳入下一版本功能列表。
  🔗 [PR #3092](https://github.com/qwibitai/nanoclaw/pull/3092)

- **#3137** — 已合并的 engagement 自检与 wiring 可见性功能，反映了用户对 agent 可观测性的持续诉求，后续可能围绕"agent 自主策略调整"形成更完整的特性。
  🔗 [PR #3137](https://github.com/qwibitai/nanoclaw/pull/3137)

---

## 7. 用户反馈摘要

- **痛点一：Node.js 环境兼容性。** Issue #3179 的用户在 JupyterLab（`/home/jovyan`）中使用 PNPM 安装 NanoClaw，因底层依赖 `@clack/core` 调用了 `node:util.styleText` 而报错。反映出项目对低版本 Node.js（< 18.16）的支持存在盲区。

- **痛点二：会话静默后的状态恢复。** PR #3183 和 #3184 均源于同一类用户场景：用户多日未与某 group/channel 交互后重新发送消息，遭遇 `No conversation found` 错误。用户期望系统能自动恢复或优雅降级，而非直接报错。

- **满意度信号：** Approval card 内容丢失问题（#3143）和 imessage opt-in 问题（#3181）均已被快速修复并关闭，表明维护团队对用户反馈响应积极。

---

## 8. 待处理积压

| 优先级 | 项目 | 状态 | 说明 |
|-------|------|------|------|
| 高 | [#3179](https://github.com/qwibitai/nanoclaw/issues/3179) | 无 PR | Node.js 版本兼容性 Bug，影响特定部署环境 |
| 中 | [#3184](https://github.com/qwibitai/nanoclaw/pull/3184) | 待合并 | 会话 transcript 缺失导致崩溃的修复 |
| 中 | [#3183](https://github.com/qwibitai/nanoclaw/pull/3183) | 待合并 | cleanupPeriodDays 未锁定的修复 |
| 低 | [#3092](https://github.com/qwibitai/nanoclaw/pull/3092) | 待合并 | 远程 MCP HTTP 服务器支持（功能增强，审阅周期可能较长） |

> **维护者提醒：** Issue #3179 尚未有对应修复 PR，建议评估是否需要为 `@clack/core` 添加 Node 版本兼容层或升级依赖；PR #3184 和 #3183 均围绕同一类会话恢复问题，可考虑合并审阅以提升效率。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 — 2026-08-04

---

## 1. 今日速览

NullClaw 在过去 24 小时内保持中等活跃度：新增 1 条 Issue、5 条 PR 动态，无新版本发布。ArcanePivot 连续提交两条安全加固类修复 PR，聚焦 curl 传输路径的凭据安全，显示项目在基础通信层持续迭代。mtdphn 的两条流式工具调用 PR（#964、#965）已被合并，标志着流式 API 能力的重要补齐。整体健康度良好，维护者响应及时，社区贡献活跃。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭（2 条）

| PR | 作者 | 说明 |
|---|---|---|
| [#964](https://github.com/nullclaw/nullclaw/pull/964) | mtdphn | 启用流式请求中的原生 API 级 tool call，解决 StreamChatResult 不保留结构化 tool-call delta 的问题，使 Agent 可执行纯流式工具响应 |
| [#965](https://github.com/nullclaw/nullclaw/pull/965) | mtdphn | 为 SSE Parser 增加结构化流式 tool-call 支持，作为 #964 的配套补充，兼容仍在 `delta.content` 中返回 XML 的模型服务器 |

**评估：** 两条 PR 共同打通了"流式请求 + 结构化 tool call"的完整链路，是 NullClaw  Agent 能力栈的关键补齐，项目在此方向上迈出实质性一步。

### 待合并（3 条）

- [#983](https://github.com/nullclaw/nullclaw/pull/983) — 非流式 Provider POST 请求经安全 curl 路径转发，凭据通过 mode-0600 临时文件传递，避免暴露于 argv
- [#982](https://github.com/nullclaw/nullclaw/pull/982) — Telegram Bot API 代理请求统一走 curl 传输通道，直连仍保留原生 HTTP
- [#956](https://github.com/nullclaw/nullclaw/pull/956) — Dependabot 升级 Alpine 从 3.23 → 3.24（docker-images 组）

---

## 4. 社区热点

### Issue #915 — Scheduler 认证失败问题 [👍 1 · 4 条评论]
🔗 [Issue #915](https://github.com/nullclaw/nullclaw/issues/915)

- **状态：** OPEN，自 2026-05-15 创建，最近活跃于 2026-08-03
- **背景：** 用户在 Ubuntu 环境下搭配 Ollama（qwen3.6:27b on RTX 3090）运行，LLM 与工具调用基本正常，但 Scheduler 模块在 Telegram 渠道出现 unauthorized 错误
- **诉求分析：** 该 Issue 已开放近 3 个月，用户描述了具体环境配置但维护者尚未提供解决方案。评论数 4 条表明社区已有一定讨论，但问题尚未定位根因。Scheduler 模块对定时/调度类 Agent 工作流至关重要，此 Bug 直接影响生产部署场景

---

## 5. Bug 与稳定性

| 优先级 | 问题 | 状态 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#915](https://github.com/nullclaw/nullclaw/issues/915) Scheduler unauthorized（Telegram + Ollama 环境） | OPEN，待响应 | 无 |

**评估：** 今日无新增 Bug。#915 为已存在的高优先级问题，暂无对应修复 PR，建议维护者关注。

---

## 6. 功能请求与路线图信号

- **流式 tool call（#964 + #965）** — 已通过合并确认，是明确的路线图推进项，后续版本将正式支持
- **PR #982 / #983 安全传输加固** — ArcanePivot 连续提交，反映项目在"凭据安全 + 代理兼容性"方向有持续投入，可预期将纳入近期版本
- **Alpine 3.24 升级（#956）** — 依赖更新，属于维护性事务，不影响功能路线

---

## 7. 用户反馈摘要

| 来源 | 内容提炼 |
|---|---|
| [#915](https://github.com/nullclaw/nullclaw/issues/915) | 用户已在生产级环境（RTX 3090 + Ollama + qwen3.6:27b）验证基础 LLM 与工具调用可用，但 Scheduler 模块在 Telegram 渠道报 unauthorized，阻碍完整工作流部署 |
| [#964](https://github.com/nullclaw/nullclaw/pull/964) / [#965](https://github.com/nullclaw/nullclaw/pull/965) | 贡献者关注流式请求中结构化 tool-call 的完整支持，说明用户对实时 Agent 响应（流式 + 工具调用组合）有明确需求 |

---

## 8. 待处理积压

| 类型 | 条目 | 创建时间 | 备注 |
|---|---|---|---|
| 🐛 Bug | [#915](https://github.com/nullclaw/nullclaw/issues/915) Scheduler unauthorized | 2026-05-15（~81 天） | 高优先级，影响生产调度场景，建议优先响应 |
| 🔄 PR | [#956](https://github.com/nullclaw/nullclaw/pull/956) Alpine 3.23→3.24 升级 | 2026-06-15（~50 天） | Dependabot 自动 PR，待维护者合并 |
| 🔄 PR | [#982](https://github.com/nullclaw/nullclaw/pull/982) Telegram 代理 curl 传输 | 2026-08-03 | 安全相关，建议优先审核 |
| 🔄 PR | [#983](https://github.com/nullclaw/nullclaw/pull/983) Provider curl 凭据安全加固 | 2026-08-03 | 安全相关，建议优先审核 |

---

**综合评估：** NullClaw 今日项目状态健康，维护者响应积极（2 条功能 PR 当日合并），安全类修复 PR 连续提交显示对底层通信安全的重视。主要风险点为 Issue #915 长期未解决，建议维护者在下一个迭代中优先处理 Scheduler 认证问题。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期：2026-08-04** | **数据来源：GitHub (nearai/ironclaw)**

---

## 1. 今日速览

IronClaw 今日保持高强度开发节奏，过去24小时内新增 Issues 47条、PR 50条，社区活跃度处于高位。核心开发工作聚焦于 **Wave 3 重构序列**（容器化迁移、secret 依赖收紧、sandbox 合并）及 **WS6 可观测性切片**，多个底层重构 PR 已进入合入阶段。同时，QA 团队持续推进 bug bash，今日报告多起 P1/P2 级别的用户体验问题（Google 重复认证、Telegram 格式渲染、多工具链失败恢复等）。整体项目健康度良好，技术债清理与用户体验改善双轨并进。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已关闭/合并

| PR | 作者 | 内容概要 |
|---|---|---|
| [#7088](https://github.com/nearai/ironclaw/issues/7088) | henrypark133 | 修复：将自定义 MCP 注册暴露为模型可见的 `builtin.extension_register_hosted_mcp` 生命周期工具 |
| [#7064](https://github.com/nearai/ironclaw/issues/7064) | BenKurrek | 重构（Wave 3/WS3）：从 `ironclaw_loop` 剥离模型网关与工具披露至 `ironclaw_loop_host`，纯移动无行为变更 |
| [#7024](https://github.com/nearai/ironclaw/issues/7024) | henrypark133 | 修复：在注册阶段解析 hosted-MCP 认证，`Auto` 模式执行免凭证握手后再决定 OAuth 路径 |
| [#7049](https://github.com/nearai/ironclaw/issues/7049) | serrrfirat | 文档：新增周三发布策略文档，对齐 RC/QA/Promotion 周度节奏 |
| [#7023](https://github.com/nearai/ironclaw/issues/7023) | dependabot | 依赖更新：base64 0.22→0.23、toml、rstest 等 6 项更新（已合并） |

### 关键在审 PR（待合并）

| PR | 作者 | 内容概要 |
|---|---|---|
| [#7101](https://github.com/nearai/ironclaw/issues/7101) | BenKurrek | WS6：停止在公开 API 中泄露 `deadpool_postgres::Pool`，驱动仅存于私有模块 |
| [#7099](https://github.com/nearai/ironclaw/issues/7099) | BenKurrek | WS6：将 system-prompt 内容从 composition root 移至 `ironclaw_loop_host` 资产目录 |
| [#7094](https://github.com/nearai/ironclaw/issues/7094) | BenKurrek | Wave 2 收官：extension registry 重分层 + `include_str!` 清理 + 嵌套树覆盖修复（含 #7083） |
| [#7096](https://github.com/nearai/ironclaw/issues/7096) | BenKurrek | WS3：将 operator secrets 路由通过 `product_contracts` port，移除 webui/operator 直接依赖 |
| [#7065](https://github.com/nearai/ironclaw/issues/7065) | BenKurrek | WS3：sandbox lane 合并 + `ironclaw_mcp` contracts 翻转，二者为同一结构性问题的两面 |
| [#7090](https://github.com/nearai/ironclaw/issues/7090) | BenKurrek | WS3：将 `host_runtime/obligations.rs` 内部拆分为三个所有者（handle / staged / build） |
| [#7084](https://github.com/nearai/ironclaw/issues/7084) | BenKurrek | Wave 3：将 `wit/` 移入其归属 crate，已修复 #7087 引发的测试规划器缺陷 |
| [#7080](https://github.com/nearai/ironclaw/issues/7080) | BenKurrek | WS3：skill-install 执行器从 `first_party_tools` 移至 `extension_support` |
| [#7077](https://github.com/nearai/ironclaw/issues/7077) | henrypark133 | 修复：一次 vendor 授权覆盖所有共享账户的安装扩展，关闭 #7069 |
| [#6994](https://github.com/nearai/ironclaw/issues/6994) | rdisandro | 功能：WebChat v2 OOBE 自动化任务原型（轮播、内联卡片、agent-mode pill） |
| [#7062](https://github.com/nearai/ironclaw/issues/7062) | serrrfirat | 修复：将 WebUI Workspace/Memory 视图范围限定至认证租户/用户 |

**整体推进：** Wave 3 重构进入冲刺阶段，今日合并/在审 PR 合计涉及 8 个以上 workspace 的依赖层重构；WS6 可观测性切片与系统提示资产重构同步推进；Google OAuth 多服务重复认证问题已修复合入。

---

## 4. 社区热点

| Issue/PR | 作者 | 评论数 | 热度分析 |
|---|---|---|---|
| [#6284](https://github.com/nearai/ironclaw/issues/6284) — EPIC: error-recoverability endgame | serrrfirat | 15 | 核心架构讨论：模型需在运行时从 100% 错误中恢复。这是 Reborn 架构的关键质量属性，引发广泛技术讨论。 |
| [#6524](https://github.com/nearai/ironclaw/issues/6524) — Epic: Hermetic capability & journey testing platform | serrrfirat | 4 | 测试基础设施 epic，解决"每个能力是否有确定性覆盖"的根本问题，关联 CI/CD 可验证性。 |
| [#7087](https://github.com/nearai/ironclaw/issues/7087) — Reborn PR test planner 硬失败于 .claude/ 等路径 | BenKurrek | 3 | CI 基础设施 bug，直接阻塞 PR #7084 的合入，已通过 PR 内修补解除阻塞。 |
| [#7085](https://github.com/nearai/ironclaw/issues/7085) — check-version-bumps.sh 在 macOS 静默跳过 WIT_TOOL_VERSION 检查 | BenKurrek | 2 | 跨平台兼容性 bug，GNU sed BRE 与 BSD sed 的不兼容问题。 |
| [#7100](https://github.com/nearai/ironclaw/issues/7100) — Reborn test planner 因 crates/AGENTS.md 关闭 | BenKurrek | 2 | 与 #7087 同类问题，`crates/AGENTS.md` 未映射导致 CI 误报。 |

**热点趋势：** 开发者社区高度关注 Reborn 架构的测试基础设施（#6524）和错误恢复能力（#6284），这反映了项目正从功能堆叠向可靠性工程演进。CI 规划器缺陷（#7087/#7100）虽为内部工具问题，但影响合入效率，已得到快速响应。

---

## 5. Bug 与稳定性

### P1 级

| Issue | 作者 | 描述 | Fix PR |
|---|---|---|---|
| [#7069](https://github.com/nearai/ironclaw/issues/7069) | joe-rlo | **Google 服务需重复认证**：每次调用不同 Google 服务均触发独立 OAuth 流程，即使已完成授权 | ✅ [#7077](https://github.com/nearai/ironclaw/issues/7077) 已合入 |
| [#7074](https://github.com/nearai/ironclaw/issues/7074) | joe-rlo | **多工具会议研究失败**：模型尝试调用不可用函数后运行中断，无法恢复 | 待修复 |

### P2 级

| Issue | 作者 | 描述 | Fix PR |
|---|---|---|---|
| [#7071](https://github.com/nearai/ironclaw/issues/7071) | joe-rlo | **"Reconnecting" 状态闪烁**：每次流式响应块均触发连接重连状态变化 | 待修复 |
| [#7075](https://github.com/nearai/ironclaw/issues/7075) | joe-rlo | **失败后忽略后续问题**：运行失败后 agent 继续执行旧任务而非响应新问题 | 待修复 |
| [#7073](https://github.com/nearai/ironclaw/issues/7073) | joe-rlo | **内部实现细节泄露**：响应中暴露 tool name 和路由逻辑 | 待修复 |
| [#7072](https://github.com/nearai/ironclaw/issues/7072) | joe-rlo | **Telegram 消息渲染原始 Markdown**：`###`、`**` 等语法未格式化 | 待修复 |

### 其他 Bug

| Issue | 作者 | 描述 | 状态 |
|---|---|---|---|
| [#7081](https://github.com/nearai/ironclaw/issues/7081) | BenKurrek | Docker fail-closed 测试门未连接（`IRONCLAW_REQUIRE_DOCKER_TESTS` 未设置） | 待修复 |
| [#7083](https://github.com/nearai/ironclaw/issues/7083) | BenKurrek | `crates/extensions/` 家族全覆盖缺失（CRATE_RE 要求 crate 直接在 `crates/` 下） | ✅ 已纳入 [#7094](https://github.com/nearai/ironclaw/issues/7094) |
| [#7082](https://github.com/nearai/ironclaw/issues/7082) | BenKurrek | `builtin.skill_install` 输入门拒收合法形状，且 url 安装静默丢弃 source 字段 | 待修复 |
| [#7068](https://github.com/nearai/ironclaw/issues/7068) | BenKurrek | `destructiveHint` 缺失时默认为 `false`，与 MCP 规范默认 `true` 冲突 | 待修复 |

**稳定性评估：** 今日 bug bash 暴露 6 项用户体验问题 + 4 项内部架构缺陷。Google OAuth 重复认证问题已快速修复合入；多工具链恢复、Telegram 渲染等问题尚待处理，建议优先跟进 P1 级 #7074。

---

## 6. 功能请求与路线图信号

| Issue | 作者 | 诉求 | 路线图信号 |
|---|---|---|---|
| [#7097](https://github.com/nearai/ironclaw/issues/7097) | sergeiest | 账单页面增加升级支持路径，解决用户对 NEAR AI 账单问题归口的困惑 | ⚡ 可直接纳入下一版本，低技术风险 |
| [#6941](https://github.com/nearai/ironclaw/issues/6941) | pranavraja99 | Skills 自创建/发现/选择/使用闭环，从 #6565 拆分出可执行子集 | 📅 中期路线图，与 WS3 first-party-tools 重构对齐 |
| [#7044](https://github.com/nearai/ironclaw/issues/7044) | sergeiest | 渠道优先（channel-first）的 onboarding 体验重构 | 📅 中长期，与 #6994 WebUI OOBE 原型呼应 |
| [#6481](https://github.com/nearai/ironclaw/issues/6481) | BenKurrek | Manifest-Driven Extension Lifecycle（已关闭） | ✅ 已完成，扩展生命周期由 normalized lifecycle records 管理 |
| [#6482](https://github.com/nearai/ironclaw/issues/6482) | BenKurrek | Pluggable Memory Providers（已关闭） | ✅ 已完成，provider contract 已稳定 |

**路线图研判：** Wave 3 重构（secrets 收紧、sandbox 合并、skill-install 重定位）已完成大部分合入，预计 Wave 3 序列将在近期收官。`skill_install` 内部 bug（#7082）修复后，skills 自管理 epic（#6941）可加速推进。账单支持路径（#7097）属于产品完善项，建议快速落地。

---

## 7. 用户反馈摘要

| 反馈类型 | 来源 | 核心痛点 |
|---|---|---|
| **❌ 认证摩擦** | #7069（已修复） | 多 Google 服务需重复 OAuth 授权，用户体验断裂 |
| **❌ 流式连接稳定性** | #7071 | 每次 SSE chunk 触发 "Reconnecting" 状态，用户感知连接不可靠 |
| **❌ 错误恢复能力** | #7074 | 多工具链失败后无法继续，模型行为不可恢复 |
| **❌ 信息泄露** | #7073 | 响应中暴露 tool name 和路由逻辑，影响专业性 |
| **❌ 平台渲染异常** | #7072 | Telegram 消息显示原始 Markdown 语法，格式丢失 |
| **❓ 账单支持不明确** | #7097 | 用户不知账单问题应向谁求助，缺少 escalation pathway |
| **✅ 内部重构进展** | 多 Issue | 开发者认可 Wave 系列重构的方向性，依赖层清理提升可维护性 |

**用户满意度信号：** 基础设施重构获得内部开发者认可，但面向最终用户的体验问题（认证、流式、格式、恢复）仍占 bug bash  majority，建议下一阶段优先处理用户可见性问题。

---

## 8. 待处理积压

| Issue | 作者 | 创建时间 | 严重性 | 风险说明 |
|---|---|---|---|---|
| [#7074](https://github.com/nearai/ironclaw/issues/7074) | joe-rlo | 2026-08-03 | P1 | 多工具链失败恢复，影响复杂任务成功率 |
| [#7082](https://github.com/nearai/ironclaw/issues/7082) | BenKurrek | 2026-08-03 | Bug | `skill_install` 输入门缺陷，预存在于 main，阻塞 skill 扩展流程 |
| [#7081](https://github.com/nearai/ironclaw/issues/7081) | BenKurrek | 2026-08-03 | Bug | Docker 测试门未连接，sandbox 测试可能静默跳过 |
| [#7068](https://github.com/nearai/ironclaw/issues/7068) | BenKurrek | 2026-08-03 | Bug | `destructiveHint` 默认值与 MCP 规范不一致，潜在安全风险 |
| [#7071](https://github.com/nearai/ironclaw/issues/7071) | joe-rlo | 2026-08-03 | P2 | 流式连接状态误报，影响用户信任度 |
| [#7075](https://github.com/nearai/ironclaw/issues/7075) | joe-rlo | 2026-08-03 | P2 | 失败后任务恢复逻辑缺陷，用户无法打断 |
| [#7072](https://github.com/nearai/ironclaw/issues/7072) | joe-rlo | 2026-08-03 | P2 | Telegram Markdown 渲染问题，影响渠道体验一致性 |
| [#7097](https://github.com/nearai/ironclaw/issues/7097) | sergeiest | 2026-08-04 | 产品 | 账单支持路径缺失，影响付费用户满意度 |

---

**报告生成时间：** 2026-08-04 | **分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI 项目动态日报 — 2026-08-04

## 1. 今日速览

过去 24 小时内，LobsterAI 共收到 12 条 PR 更新（7 条已合并/关闭）和 2 条 Issue 更新（均为新开放），项目维护者活跃度高，代码合入节奏稳定。**未发布新版本**。主要工作集中在活动运营功能（积分 campaign）的回退修复、Windows NSIS 安装程序稳定性优化、以及侧边栏多 Agent 任务过滤功能。社区贡献方面，3 个功能请求 PR（Markdown 导出、手动重试按钮、自定义 Provider 数量扩容）已就绪待合并，整体项目健康度良好。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的重要 PR 如下：

| PR | 类型 | 摘要 |
|----|------|------|
| [#2424](https://github.com/netease-youdao/LobsterAI/pull/2424) | 🔄 修复 | 回退 aced16fc 提交，恢复活跃的积分 Campaign 活动（含 500 积分领取流程、IPC 通信、UI 及资源） |
| [#2420](https://github.com/netease-youdao/LobsterAI/pull/2420) | 🐛 修复 | Windows NSIS 安装程序：每次停止轮询时重新向残留进程发送终止信号，防止进程存活导致安装失败 |
| [#2423](https://github.com/netease-youdao/LobsterAI/pull/2423) | 🔄 回退 | 回退 `Liuzhq/fix btw tools` 相关提交 |
| [#2419](https://github.com/netease-youdao/LobsterAI/pull/2419) | ✨ 功能 | 为桌面客户端新增启动积分 Campaign 入口（弹窗 + 新对话页持久化入口） |
| [#2418](https://github.com/netease-youdao/LobsterAI/pull/2418) | ✨ 功能 | 侧边栏新增多 Agent 任务活动过滤器（Codex 风格），快速定位需关注的任务 |

> **项目推进总结**：今日主要完成**运营活动稳定性修复**（积分 campaign 恢复）和**安装程序健壮性提升**（Windows 进程清理），同时在多 Agent 协作体验上有所进展（侧边栏任务过滤器）。

---

## 4. 社区热点

今日活跃 Issue/PR（按评论和关注度排序）：

| 类型 | 编号 | 标题 | 作者 | 状态 |
|------|------|------|------|------|
| Issue | [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | 私有化部署 Kimi2.5 模型分析文档重复处理/回复进度 | ze23sw | OPEN / stale |
| Issue | [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) | 为会话详情添加「导出为 Markdown」功能 | MaoQianTu | OPEN / stale |
| PR | [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) | 实现会话详情导出 Markdown 功能 | MaoQianTu | OPEN / stale |
| PR | [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | Cowork 新增手动重试按钮，支持瞬时错误快速重试 | swuzjb | OPEN / stale |
| PR | [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | 允许最多 20 个自定义 Provider | leedalei | OPEN / stale |
| PR | [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | 修复 web-search 不支持 `--disable-blink-features=AutomationControlled` 问题 | 0xFLX | OPEN / stale |

**热点分析**：
- **Markdown 导出功能**（#1213 / #1214）是今日社区讨论最集中的需求，源于用户引用、整理对话记录的痛点，已有完整 PR 实现。
- **Kimi2.5 重复处理 Bug**（#1206）影响私有化部署用户的文档分析体验，属于高优先级问题。
- **手动重试按钮**（#1208）回应了 Cowork 会话因 429 限流或网络故障中断后的用户体验问题。

---

## 5. Bug 与稳定性

| 级别 | Issue/PR | 描述 | 状态 |
|------|----------|------|------|
| 🔴 高 | [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | Kimi2.5 私有化部署下分析文档时重复回复进度，切换模型后正常 | 未修复 |
| 🟡 中 | [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | Web Search 在 Chrome 130+ 下因 `AutomationControlled` flag 被注入而不可用 | PR 已提交 |
| 🟢 低 | — | [#2420](https://github.com/netease-youdao/LobsterAI/pull/2420) 修复的 Windows 安装程序残留进程问题 | ✅ 已合并 |

> **稳定性评估**：今日新增 1 个高优先级 Bug（Kimi2.5 重复处理），1 个中优先级修复 PR 待合并（Web Search）。整体稳定性良好，无崩溃类报告。

---

## 6. 功能请求与路线图信号

| 需求 | Issue | PR | 纳入下版本概率 |
|------|-------|----|----------------|
| 会话详情导出 Markdown | [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) | [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) | ⭐⭐⭐⭐ 高（PR 已完成） |
| Cowork 手动重试按钮 | — | [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | ⭐⭐⭐⭐ 高（PR 已完成） |
| 自定义 Provider 上限提升至 20 | — | [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | ⭐⭐⭐ 中（PR 已完成） |
| 提升 Electron 版本至 43.2.0 | — | [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | ⭐⭐ 低（长期 stale） |

**路线图信号**：社区贡献者已准备好 3 个高质量 PR（Markdown 导出、重试按钮、Provider 扩容），建议维护者优先合并以快速响应用户需求。

---

## 7. 用户反馈摘要

| 来源 | 用户痛点 / 场景 | 满意度 |
|------|----------------|--------|
| [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | Kimi2.5 私有化部署时分析文档会重复输出进度提示，造成 confusion，切换模型后正常 | 😟 不满意 |
| [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) | 会话详情仅支持导出图片，需要引用或分享对话时操作繁琐，截图不利于后续编辑和检索 | 😟 不满意 |
| [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | Cowork 会话因 429 限流或网络故障中断后，只能手动重新输入消息，体验较差 | 😟 不满意 |
| [#2420](https://github.com/netease-youdao/LobsterAI/pull/2420) | Windows 安装程序在停止轮询时无法彻底清理残留进程，可能导致安装失败 | 😟 不满意 |
| [#2424](https://github.com/netease-youdao/LobsterAI/pull/2424) | 积分 Campaign 被意外回退，影响用户获取奖励体验 | 😟 不满意 |

---

## 8. 待处理积压

以下 Issue/PR 已标记为 **stale**，长期未获维护者响应，建议优先处理：

| 编号 | 类型 | 标题 | 最后更新 |
|------|------|------|----------|
| [#1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | 🐛 Bug | Kimi2.5 私有化部署重复处理文档 | 2026-08-03 |
| [#1213](https://github.com/netease-youdao/LobsterAI/issues/1213) | 💡 功能请求 | 会话详情导出 Markdown | 2026-08-03 |
| [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | PR | Cowork 手动重试按钮 | 2026-08-03 |
| [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | PR | Web Search Chrome flag 兼容修复 | 2026-08-03 |
| [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | PR | 自定义 Provider 上限扩容至 20 | 2026-08-03 |
| [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) | PR | 会话详情导出 Markdown 实现 | 2026-08-03 |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | PR | Electron 依赖升级至 43.2.0 | 2026-08-03 |

> **维护者建议**：今日合并的 PR 多为运营/稳定性修复，社区贡献的功能类 PR 积压较多，建议优先 review 并合并 #1208、#1214、#1212 三个已完成的功能 PR，以提升用户满意度。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目日报 — 2026-08-04

## 1. 今日速览

Moltis 今日整体活跃度偏低，过去24小时内无新 Issue 或已关闭 Issue，无新版本发布。唯一动态为一条处于待合并状态的 PR（#1183），聚焦于 MCP 服务器仓库管理功能的增强。项目当前处于功能迭代期，核心贡献者正在推进仓库级 MCP 配置的标准化封装，整体健康度良好，社区参与度暂显平淡。

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 🔄 待合并 PR（1 条）

**[PR #1183](https://github.com/moltis-org/moltis/pull/1183) — feat(mcp): add managed repository bundles**
- **作者**：penso
- **创建时间**：2026-08-02 | **最近更新**：2026-08-03
- **状态**：OPEN（待合并）
- **摘要**：新增托管 Git 仓库 Bundles 能力，支持 MCP 服务器的发现、预览、安装、更新、回滚及卸载全流程管理；集成 HTTPS 凭证、固定版本 SSH 传输、Vault 生命周期管理，并支持导入仓库驱动的 MCP 配置；同时简化了 Web 端 onboarding 流程。

> **项目意义**：此 PR 是 MCP 生态集成的重要里程碑，将仓库级包管理引入 Moltis，显著提升 MCP 服务器配置的标准化程度与部署安全性。若合并，用户将能够以"仓库 Bundle"形式统一管理多个 MCP 服务器的生命周期，降低配置碎片化风险。

---

## 4. 社区热点

今日无高活跃度 Issue 或 PR。待合并 PR [#1183](https://github.com/moltis-org/moltis/pull/1183) 尚未收到评论或点赞，可能仍处于早期 Review 阶段。建议关注后续 Code Review 反馈，该功能涉及安全敏感操作（凭证管理、SSH 传输），预期会引发技术讨论。

---

## 5. Bug 与稳定性

今日无 Bug 报告、崩溃或回归问题。

---

## 6. 功能请求与路线图信号

### 📌 强信号：MCP 仓库 Bundle 管理
- **PR [#1183](https://github.com/moltis-org/moltis/pull/1183)** 明确对应社区对"MCP 服务器集中管理"的诉求。
- 功能覆盖了完整生命周期（安装→更新→回滚→卸载），暗示路线图将向"可复现、可审计的 MCP 配置分发"方向演进。
- **预计纳入版本**：结合 PR 完整度（涵盖凭证、Vault、SSH、Web onboarding），该功能有较大可能进入下一主要版本。

---

## 7. 用户反馈摘要

今日无新 Issue 或评论，无法提炼用户反馈。

---

## 8. 待处理积压

| 类型 | 编号 | 内容简述 | 状态 | 备注 |
|------|------|----------|------|------|
| PR | [#1183](https://github.com/moltis-org/moltis/pull/1183) | feat(mcp): add managed repository bundles | OPEN（待合并） | 创建于 2026-08-02，待 Review 与合并 |

> **建议**：维护者可关注 PR #1183 的 Review 进度，该功能涉及多模块变更（MCP、凭证、Vault、Web），建议尽快完成 Code Review 以推进发布节奏。

---

*报告生成时间：2026-08-04 | 数据来源：github.com/moltis-org/moltis*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw (QwenPaw) 项目动态日报
**日期：2026-08-04 | 数据周期：2026-08-03 ~ 2026-08-04**

---

## 1. 今日速览

CoPaw 项目今日保持高强度开发节奏，过去24小时内共产生14条Issue与50条PR更新，整体活跃度处于高位。v2.1.0-beta.1 新版本正式发布，同步启动了安装验证流程（#6656）。开发重点集中在**Skills性能优化**、**ACP协议稳定性**、**模型容错机制**三大方向，多项关键Bug已获得修复或进入审查阶段。社区对桌面端体验（文件拖拽、多行显示、产出物管理）的关注持续升温，反映出产品正从"可用"向"好用"过渡。

---

## 2. 版本发布

### v2.1.0-beta.1
- **发布链接：** [QwenPaw Releases](https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.1.0-beta.1)
- **核心变更：**
  - 修复聊天通道身份泄漏问题，防止旧会话状态污染新聊天（PR #6382）
  - 新增收件箱交互动效与颜色编码徽章（PR #xxx，作者 @lalaliat）
- **破坏性变更：** 无明确记录
- **迁移注意事项：** 建议用户在 Beta 阶段完成安装验证（参见 #6656），重点关注 Web UI 与桌面端的稳定性。版本号即将 bump 至 2.1.0b2（PR #6665 已合并）。

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 类型 | 内容 | 影响 |
|---|---|---|---|
| [#6634](https://github.com/agentscope-ai/QwenPaw/pull/6634) | Bug fix | Skills API 排除完整内容，修复慢网超时 | 直接关闭 #6633，Skills/Skill Pool 页面加载性能显著改善 |
| [#6650](https://github.com/agentscope-ai/QwenPaw/pull/6650) | 优化 | 分离 Skill 列表与详情接口 | 进一步减少 API 负载，与 #6634 互补 |
| [#6665](https://github.com/agentscope-ai/QwenPaw/pull/6665) | 维护 | 版本号 bump 至 2.1.0b2 | 为下一轮 beta 发布做准备 |
| [#6597](https://github.com/agentscope-ai/QwenPaw/pull/6597) | Bug fix | 恢复 Web 工作空间自动快照 | 修复重复 bootstrap 注册导致的 checkpoint 钩子丢失 |
| [#6203](https://github.com/agentscope-ai/QwenPaw/pull/6203) | Bug fix | 修复 Windows `tasklist` 健康检查无超时问题 | 防止进程探测无限阻塞（作者 @Yigtwxx，首次贡献） |
| [#6623](https://github.com/agentscope-ai/QwenPaw/pull/6623) | Bug fix | 修复 ACP 通知竞态导致文本丢失 | 解决 #6625，提升 ACP 协议可靠性 |
| [#6595](https://github.com/agentscope-ai/QwenPaw/pull/6595) | Bug fix | 修复 `spawn_subagent` 空字符串参数处理 | 解决 #6588 的三步失败链 |

**整体推进评估：** 今日合并的 PR 覆盖了性能、稳定性、开发者体验三个维度，尤其是 Skills 加载问题（#6633）和 ACP 竞态问题（#6625）的修复，对生产环境用户有直接收益。

---

## 4. 社区热点

### 高关注度 Issue

1. **[GPT-5.6 prompt caching 支持](https://github.com/agentscope-ai/QwenPaw/issues/6649)** (#6649)
   - 评论数：9 | 创建者：samluoabc
   - 诉求：支持 GPT-5.6 的 prompt cache 参数（`prompt_cache_key` 等），实现 Agent 循环中的多轮缓存复用，降低延迟与成本。
   - 分析：反映用户对 LLM 调用成本的敏感，随着 Agent 循环场景普及，缓存优化将成为刚需。

2. **[spawn_subagent 空 batch 处理](https://github.com/agentscope-ai/QwenPaw/issues/6588)** (#6588)
   - 评论数：6 | 状态：已有 Fix PR #6595、#6658 合并
   - 分析：OpenAI Responses 兼容端点返回空占位符引发的连锁错误，修复已落地，后续需关注回归测试。

3. **[WebView2 崩溃导致 UI 全黑](https://github.com/agentscope-ai/QwenPaw/issues/6647)** (#6647)
   - 创建者：adolfishxu | 状态：OPEN
   - 分析：桌面端 WebView2 进程崩溃后无恢复路径，严重影响用户体验，属于高危 Bug，亟需维护者关注。

### 高关注度 PR

- [#6659](https://github.com/agentscope-ai/QwenPaw/pull/6659) - **模型 fallback 实现**（Under Review），关联历史 Issue #2199，是提升系统可用性的关键基础设施。
- [#6525](https://github.com/agentscope-ai/QwenPaw/pull/6525) - **用户上下文透明穿透**，实现 `user_id`/`channel` 从 API 到 Tool/MCP/SKILL 的全链路传递，对多租户场景意义重大。
- [#6645](https://github.com/agentscope-ai/QwenPaw/pull/6645) - **OS 级增强**（全屏、Dock、Mission Control 等），作者 zhaozhuang521，展示桌面端深度集成方向。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#6647](https://github.com/agentscope-ai/QwenPaw/issues/6647) | WebView2 崩溃后 UI 全黑，无恢复路径 | 暂无 |
| 🔴 高 | [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) | 长时 shell 命令阻塞 Feishu 会话 1.5 小时，无 per-channel 超时 | 暂无 |
| 🟠 中 | [#6614](https://github.com/agentscope-ai/QwenPaw/issues/6614) | 微信 cron 定时推送静默失败，任务显示 success 但 token 失效 | 暂无 |
| 🟠 中 | [#6625](https://github.com/agentscope-ai/QwenPaw/issues/6625) | ACP 通知竞态导致文本丢失 | ✅ #6623（已合并） |
| 🟠 中 | [#6588](https://github.com/agentscope-ai/QwenPaw/issues/6588) | spawn_subagent 空 batch 占位符处理异常 | ✅ #6595、#6658（已合并） |
| 🟡 低 | [#6633](https://github.com/agentscope-ai/QwenPaw/issues/6633) | Skills 页面慢网超时 | ✅ #6634、#6650（已合并） |

**稳定性评估：** 今日共关闭 4 个 Issue，其中 3 个为 Bug，修复覆盖率 75%。剩余高严重度 Bug（#6647、#6608、#6614）均无对应 PR，建议维护者优先排期。

---

## 6. 功能请求与路线图信号

| 需求 | Issue | 评论数 | 匹配 PR | 纳入下一版本可能性 |
|---|---|---|---|---|
| GPT-5.6 prompt caching | #6649 | 9 | 暂无 | 🟡 中（需模型方支持） |
| 拖入文件多行显示 | #6583 | 2 | ✅ #6662（待合并） | 🔵 高 |
| 任务产出物按目录组织 | #6643 | 2 | 暂无 | 🟡 中 |
| 直接读取原路径文件 | #6642 | 2 | 暂无 | 🟡 中 |
| Console 通道保留安全审批 | #6655 | 3 | ✅ 已关闭 | — |
| 模型 fallback 机制 | — | — | ✅ #6659（Under Review） | 🔵 高 |
| 用户上下文穿透 | — | — | ✅ #6525（待合并） | 🔵 高 |

**路线图判断：** v2.1.x 版本将聚焦**稳定性增强**（fallback、ACP 修复）与**桌面体验优化**（文件预览、OS 集成）。用户上下文穿透（#6525）和模型 fallback（#6659）如通过审查，将成为 v2.1.0 正式版的重大能力升级。

---

## 7. 用户反馈摘要

### 痛点
1. **文件拖入体验差：** 多文件时单行显示无法完整查看文件名（#6583），且需要先上传再读取，产生冗余文件（#6642）。
2. **产出物管理混乱：** 所有任务产出物堆积在 `media/` 目录，缺乏组织（#6643）。
3. **静默失败难排查：** 微信 cron 推送显示 success 但实际未送达，消耗 44M token（#6614）；Console 通道安全审批不渲染导致用户无感知（#6655）。
4. **桌面端崩溃无恢复：** WebView2 崩溃后 UI 全黑，用户无法操作（#6647）。

### 满意点
- Skills 页面加载慢问题得到快速响应，两项 PR 已合并（#6634、#6650）。
- spawn_subagent 的边界条件问题被迅速识别并修复（#6588 → #6595、#6658）。

---

## 8. 待处理积压

### 需维护者关注

| Issue/PR | 创建时间 | 状态 | 建议优先级 |
|---|---|---|---|
| [#6647](https://github.com/agentscope-ai/QwenPaw/issues/6647) WebView2 崩溃全黑 | 2026-08-03 | OPEN | P0 — 影响桌面端核心可用性 |
| [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) 长时 shell 命令阻塞会话 | 2026-07-31 | OPEN | P0 — 存在会话锁定风险 |
| [#6614](https://github.com/agentscope-ai/QwenPaw/issues/6614) 微信 cron 静默失败 | 2026-07-31 | OPEN | P1 — 数据损失 + 资源浪费 |
| [#6659](https://github.com/agentscope-ai/QwenPaw/pull/6659) 模型 fallback | 2026-08-03 | Under Review | P1 — 关键稳定性能力 |
| [#6525](https://github.com/agentscope-ai/QwenPaw/pull/6525) 用户上下文穿透 | 2026-07-28 | OPEN | P1 — 多租户架构基础 |
| [#6645](https://github.com/agentscope-ai/QwenPaw/pull/6645) OS 级增强 | 2026-08-03 | OPEN | P2 — 桌面体验优化 |
| [#6666](https://github.com/agentscope-ai/QwenPaw/pull/6666) App Center 分类修复 | 2026-08-04 | OPEN | P2 |

---

**项目健康度评分：B+**
- 开发活跃度：高（50 PR/24h）
- Bug 修复效率：中高（3/4 高优先级 Bug 已有 Fix）
- 社区响应：积极（ Issue #6649 获 9 评论）
- 风险点：2 个 P0 Bug 暂无 Fix，需尽快排期

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

⚠️ 摘要生成失败。

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*