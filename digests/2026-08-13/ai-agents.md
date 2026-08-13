# OpenClaw 生态日报 2026-08-13

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-13 02:27 UTC

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



# OpenClaw 项目日报 — 2026-08-13

## 1. 今日速览

OpenClaw 在过去 24 小时内保持极高活跃度，共接收 500 条 Issue 更新（新开/活跃 403 条，关闭 97 条）和 500 条 PR 更新（待合并 359 条，已合并/关闭 141 条）。当前项目健康度面临挑战：多代理编排稳定性、Subagent 结果丢失、消息路由异常是社区最集中的痛点，多个 P1 级 Bug 持续发酵。新功能开发集中在 Codex 实时语音集成、快照恢复机制、Custodian 向导体验及 macOS/iOS 实时通话支持上。今日无新版本发布。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 状态 | 说明 |
|----|------|------|
| [#122879](https://github.com/openclaw/openclaw/pull/122879) | ✅ 已关闭 | 修复 `channels add` 命令测试超时（120s），解决同步加载插件源码导致的 CI 失败 |
| [#122912](https://github.com/openclaw/openclaw/pull/122912) | ✅ 已关闭 | 修复 Parallels npm-update 矩阵中 bundled plugins 被隐藏的问题，保障更新后插件清单正确收敛 |
| [#122924](https://github.com/openclaw/openclaw/pull/122924) | ✅ 已关闭 | 修复 Code Mode 下 oversized tool result 导致死端的问题，改为返回有界输出而非终止 turn |
| [#122931](https://github.com/openclaw/openclaw/pull/122931) | ✅ 已关闭 | 文档改进：澄清 Gateway 动态 operator scope 规则，消除 `fs.listDir` RPC 与 admin node-relay 命令的混淆 |
| [#122921](https://github.com/openclaw/openclaw/pull/122921) | ✅ 已关闭 | 修复 CI 重复冷启动依赖重建问题（节省约 105-111s），解决 StickyDisk v6 lineage 回滚导致指纹重复安装 |
| [#122927](https://github.com/openclaw/openclaw/pull/122927) | ✅ 已关闭 | 清理死配置键 `streaming.progress.render`，该键此前已被接受但无任何 channel 读取 |

### 重点进行中的 PR

| PR | 状态 | 说明 |
|----|------|------|
| [#119001](https://github.com/openclaw/openclaw/pull/119001) | 🔵 Open | feat(codex): 将 Codex 原生实时语音绑定到已有 session，使其成为 OpenClaw session 的实时大脑 |
| [#122536](https://github.com/openclaw/openclaw/pull/122536) | 🔵 Open | feat: Portals — 向操作者暴露 agent-run dev server，解决远程访问时无法直观看到 web app 运行状态的问题 |
| [#121562](https://github.com/openclaw/openclaw/pull/121562) | 🔵 Open | feat(ui): 内联渲染 Custodian setup receipt，区分"Answer submitted"/"Setup cancelled"/"Validation rejected"状态 |
| [#121560](https://github.com/openclaw/openclaw/pull/121560) | 🔵 Open | feat(gateway): 支持 Custodian 向导 session 在 reload 后恢复，通过 narrow Gateway contract 维持 live session 权限 |
| [#118954](https://github.com/openclaw/openclaw/pull/118954) | 🔵 Open | fix: Custodian 向导 reload 后丢失 pending control，修复 opaque session id 持久化与恢复逻辑 |
| [#118505](https://github.com/openclaw/openclaw/pull/118505) | 🔵 Open | macOS: 在 Voice & Talk Settings 中暴露实时 Talk 配置入口，默认保持 relay toggle 关闭 |
| [#118499](https://github.com/openclaw/openclaw/pull/118499) | 🔵 Open | macOS: 新增 Gateway-relay Talk 支持，将 iOS 的 Gateway-relay 实时通话会话迁入 OpenClawKit 共享包 |
| [#122764](https://github.com/openclaw/openclaw/pull/122764) | 🔵 Open | fix(queue): 跨分组 lane 的共享容量仲裁，解决 #122763 中的队列调度问题 |
| [#102261](https://github.com/openclaw/openclaw/pull/102261) | 🔵 Open | Interactive parity with Codex: 为所有 OpenClaw session 引入 ask-user-question / plan mode / goal mode |
| [#112896](https://github.com/openclaw/openclaw/pull/112896) | 🔵 Open | feat(snapshot): 接受并恢复已保存的 recovery points，实现会话级快照回滚 |
| [#112865](https://github.com/openclaw/openclaw/pull/112865) | 🔵 Open | feat(snapshot): 捕获最终 recovery points，为快照恢复提供数据源 |
| [#112385](https://github.com/openclaw/openclaw/pull/112385) | 🔵 Open | feat(snapshot): 组合 RFC 0013 定义的 recovery points，完善快照机制底层架构 |
| [#122919](https://github.com/openclaw/openclaw/pull/122919) | 🔵 Open | fix: 修复 steer 重试在目标 run 退出后死

---

## 横向生态对比



# 2026-08-13 个人 AI 助手开源生态横向对比分析报告

---

## 1. 生态全景

2026年8月中旬，个人AI智能体开源生态呈现**多极分化、快速迭代**的格局。OpenClaw 作为核心参照项目维持极高活跃度，IronClaw 与 ZeroClaw 在安全加固与跨平台兼容性上同步冲刺；NanoBot 聚焦安全性修复，CoPaw 处于正式版发布前的体验打磨期。生态整体从"功能堆叠"转向"稳定性与安全性并重"，Telegram 渠道稳定性、多 Agent 协作、记忆系统优化、跨平台适配成为社区共同关注的技术高地。

---

## 2. 各项目活跃度对比

| 项目 | Issues (新开/活跃/关闭) | PRs (待合并/已合并/关闭) | Release | 健康度评估 |
|------|------------------------|--------------------------|---------|-----------|
| **OpenClaw** | 403 / 97 | 359 / 141 | 无 | 🟡 高活跃但有稳定性隐患 |
| **NanoBot** | 4 / 4 | 17 / 19 (≈47% 合并率) | 无 | 🟢 高合并效率，安全修复密集 |
| **PicoClaw** | 3 / 0 | 3 / 0 | 无 | 🟡 输入>输出，stale Bug 积压 |
| **NanoClaw** | 4 / 0 | 9 / 1 | 无 | 🟢 插件化架构冲刺期，稳健推进 |
| **IronClaw** | 12 / 29 | 19 / 31 | v1.2.0-rc.2/rc.3 | 🟡 候选冲刺期，Telegram Bug 集中爆发 |
| **LobsterAI** | 2 / 4 | 2 / 6 | 无 | 🟢 中等活跃，修复导向 |
| **CoPaw** | 23 / 8 | 26 / 17 | v2.1.0-beta.4 | 🟢 高频活跃，v2.1.0 冲刺打磨期 |
| **ZeroClaw** | 30 / 20 | 30 / 20 | 无 | 🟢 安全加固+跨平台并重 |
| **Hermes Agent** | — | — | — | ⚠️ 数据缺失 |
| **NullClaw** | 0 / 0 | 0 / 0 | 无 | 🔴 无活动 |
| **ZeptoClaw** | 0 / 0 | 0 / 0 | 无 | 🔴 无活动 |

---

## 3. OpenClaw 在生态中的定位

| 维度 | OpenClaw | 同类对比 |
|------|----------|----------|
| **社区规模** | 最大（500+ Issue/PR 日更） | 显著领先 NanoBot/IronClaw（40-50 量级） |
| **技术路线** | 多代理编排（Codex 实时语音绑定、快照恢复、Custodian 向导） | 更侧重 Agent 编排与 session 生命周期管理 |
| **平台覆盖** | macOS/iOS 实时通话、Gateway-relay | 与 IronClaw 跨平台策略趋同，但 Apple 生态深耕更早 |
| **核心挑战** | 多代理编排稳定性、Subagent 结果丢失、消息路由异常 | 同类项目（如 NanoBot、IronClaw）同样暴露多 Agent 协作稳定性问题 |
| **差异化优势** | 生态最丰富（Channels/Portals/Snapshot 机制），RFC 0013 快照标准 | ZeroClaw 专注单 Agent 安全加固，CoPaw 侧重记忆系统 |

**定位总结：** OpenClaw 是生态中**规模最大、架构最重**的多代理框架，正从"功能覆盖"转向"稳定性攻坚"；其 OpenAPI 设计与快照机制为同类项目提供了参考范式，但多代理编排的固有问题（路由、结果丢失）也是整个生态的共同挑战。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **多 Agent 协作稳定性** | OpenClaw、PicoClaw、NanoClaw | OpenClaw：Subagent 结果丢失、消息路由异常；PicoClaw：routed-agent 上下文管理缺失历史/压缩；NanoClaw：subagent 对话持久化 conflict 待解 |
| **渠道稳定性（Telegram/WhatsApp/Discord）** | IronClaw、NanoClaw、LobsterAI、ZeroClaw | IronClaw：Telegram 11 个 Bug 集中爆发（GIF 卡死、消息截断、顺序错乱）；NanoClaw：微信 QR 登录 token 丢失；ZeroClaw：Discord typing 指示器卡死 |
| **跨平台兼容** | IronClaw、ZeroClaw、NanoBot | IronClaw：Windows 原子重命名修复；ZeroClaw：Windows 74 测试失败、macOS 窗口消失；NanoBot：Docker entrypoint.sh 权限问题 |
| **安全加固** | NanoBot、ZeroClaw、OpenClaw | NanoBot：4 个 P1 级安全修复（路径注入、凭证泄露、容器权限）；ZeroClaw：SSRF 防护、截图路径注入、WASM 超时墙钟；OpenClaw：Gateway operator scope 规则澄清 |
| **记忆系统优化** | CoPaw、ZeroClaw | CoPaw：长期记忆提示词精简、压缩后孤立 Tool Result 污染；ZeroClaw：Schema 验证记忆合并 + 有界降级、移除休眠 Lucid 连接器 |
| **可观测性与工具链** | ZeroClaw、NanoBot、IronClaw | ZeroClaw：Langfuse/Herdr 集成、Semgrep diff-aware 发现；NanoBot：Agent Hooks 自动发现；IronClaw：OMP core-tool contract 统一 |
| **语音交互闭环** | NanoBot、OpenClaw | NanoBot：TTS 功能请求 3👍 社区呼声高；OpenClaw：Codex 实时语音绑定 session |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 技术架构特点 |
|------|----------|----------|--------------|
| **OpenClaw** | 多代理编排、快照恢复、实时语音 | 重度多 Agent 用户、开发者 | 插件化+Gateway+Channel 架构，RFC 0013 快照标准 |
| **NanoBot** | 安全性、会话稳定性、DeepSeek 路由 | 安全敏感用户、研究型用户 | 原生 Responses API 路由、Agent Hooks 自动发现 |
| **IronClaw** | 渠道集成（Telegram/Slack）、容器运行时 | 企业/团队部署用户 | 容器健康检查、Windows 兼容性、v1.2.0 候选 |
| **CoPaw** | 记忆系统、Computer Use、UI 体验 | 桌面自动化用户、个人助手用户 | 记忆提示词工程、暗黑模式适配、beta 冲刺期 |
| **ZeroClaw** | 安全加固（SSRF/WASM）、跨平台 | 安全研究者、跨平台用户 | 延迟 MCP 策略、凭证冷却、原子迁移 |
| **PicoClaw** | MCP 集成、Telegram/Exa 搜索 | 轻量级集成用户 | routed-agent 上下文管理、Exa 原生搜索 |
| **LobsterAI** | 技能管理、Windows 安装、UI 交互 | 中文用户、Windows 用户 | Skills 标签页拆分、junction 修复、沙箱默认开启 |
| **NanoClaw** | Agent 插件化、多平台消息路由 | 插件生态构建者 | Agent Plugins 1.0 目录规范、模板系统重构 |

---

## 6. 社区热度与成熟度分层

```
🔥 快速迭代阶段（高频发布 + 新功能密集）
   └─ OpenClaw（500+ Issue/PR）｜CoPaw（v2.1.0-beta.4）｜ZeroClaw（50+ Issue/PR，安全修复密集）

🟢 稳定性巩固阶段（Bug 修复导向 + 候选版本）
   └─ IronClaw（v1.2.0-rc.2/rc.3，Telegram Bug 集中爆发）｜NanoBot（47% 合并率，P1 安全修复密集）

🟡 功能建设期（输入>输出，审查周期长）
   └─ PicoClaw（0 合并，stale Bug 积压）｜NanoClaw（稳健推进，插件化冲刺）

⚠️ 维护滞后阶段
   └─ LobsterAI（中等活跃，卸载残留/沙箱控制问题待解）

🔴 休眠/无活动
   └─ NullClaw｜ZeptoClaw｜Hermes Agent（数据缺失）
```

---

## 7. 值得关注的趋势信号

### 信号 1：多 Agent 编排稳定性成为生态瓶颈
OpenClaw、PicoClaw、NanoClaw 同时暴露 Subagent/路由上下文管理问题，表明**多代理协作的可靠性仍是技术痛点**，尚未出现成熟解决方案。对开发者建议：优先选择单 Agent 或成熟编排框架，关注快照恢复机制落地进度。

### 信号 2：安全修复从"加分项"变为"必选项"
NanoBot（4 个 P1 安全 PR）和 ZeroClaw（3 个 P1 安全 PR）同日密集发布安全修复，涵盖 SSRF、WASM 超时、路径注入。行业信号：**AI Agent 的安全边界正在快速定义**， credential 泄露、容器权限降级、WASM 挂起均成为重点关注面。

### 信号 3：Telegram 渠道稳定性是高频故障点
IronClaw 今日集中报告 11 个 Telegram Bug（GIF 卡死、消息截断、顺序错乱），其他项目亦有 WhatsApp/Discord 类似问题。**渠道适配层的质量成为用户体验的分水岭**，建议用户关注项目的渠道测试覆盖率。

### 信号 4：跨平台 CI 缺失是社区共识缺陷
ZeroClaw（74 个 Windows 测试失败）、NanoBot（Docker 权限问题）、IronClaw（Windows 原子重命名）均暴露跨平台兼容性问题。**Windows/macOS 原生支持质量**将成为下一轮竞争焦点。

### 信号 5：记忆系统优化从"功能开发"转向"体验打磨"
CoPaw 精简长期记忆提示词、防止压缩后孤立 Tool Result 污染；ZeroClaw 推进 Schema 验证记忆合并。**记忆系统的可靠性和可解释性**是个人 AI 助手长期可靠性的核心，建议开发者关注此方向的技术演进。

### 信号 6：语音交互闭环呼声渐强
NanoBot TTS 请求获 3👍，OpenClaw 推进 Codex 实时语音绑定。**"语音输入→处理→语音输出"的完整闭环**正在成为社区期待，可能催生新的交互范式标准。

---

**报告生成时间：** 2026-08-13  
**分析师：** Agnes (Sapiens AI)

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报 — 2026-08-13

---

## 1. 今日速览

过去24小时 NanoBot 项目保持高活跃度：共处理 8 条 Issues（4条已关闭）和 36 条 PRs（17条已合并/关闭），合并率约 47%，表明贡献流转效率良好。今日焦点集中在 **安全性修复** 和 **会话稳定性** 两大方向，多个 P1 级安全问题已落地，项目整体向前稳步推进。无新版本发布。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 摘要 | 作者 |
|----|------|------|------|
| [#5230](https://github.com/HKUDS/nanobot/pull/5230) | 🐛 Fix (P1) | 修复 Gemini 3 拒绝重放无 thought signature 的 function-call 步骤，保留原生签名兼容性 | arcdrake22 |
| [#5329](https://github.com/HKUDS/nanobot/pull/5329) | 🛡️ Security (P1) | 修复 ExecTool 中 shell tilde 展开的路径边界绕过问题，覆盖裸 `~`、命名用户 `~user`、重定向等场景 | yorkhellen |
| [#5258](https://github.com/HKUDS/nanobot/pull/5258) | 🛡️ Security (P1) | 防止含凭证的 URL 被发送至远程 Jina 阅读器，修复 Issue #4884 暴露的安全风险 | shixi-li |
| [#5320](https://github.com/HKUDS/nanobot/pull/5320) | 🛡️ Security (P1) | 恢复 Docker 容器因 privilege drop 所需的三个 capabilities，启用 `no-new-privileges` | yu-xin-c |
| [#5218](https://github.com/HKUDS/nanobot/pull/5218) | 🐛 Fix (P1) | 修复 ExecTool 路径守卫在重定向/分组操作符旁遗漏的路径提取问题 | santhreal |
| [#5279](https://github.com/HKUDS/nanobot/pull/5279) | 🐛 Fix (P2) | 将会话历史存储移至 agent workspace 之外，关闭可达性漏洞（#5278） | lmzopq |
| [#5362](https://github.com/HKUDS/nanobot/pull/5362) | ✨ Feature (P2) | 支持 DeepSeek V4 Pro 通过原生 Responses API 路由，保持 `reasoning.effort` 控制 | chengyongru |
| [#4878](https://github.com/HKUDS/nanobot/pull/4878) | ✨ Feature (P2) | 引入 Agent Hooks 自动发现机制，基于 pkgutil scanning + entry_points 注册 | KANG99 |

**项目推进总结**：今日安全修复密度较高，4个 P1 级 PR 集中解决了路径注入、凭证泄露、容器权限降级等问题；同时会话管理和 provider 扩展能力同步增强。

---

## 4. 社区热点

| 条目 | 类型 | 评论数 | 👍 | 热点分析 |
|------|------|--------|-----|----------|
| [#5327](https://github.com/HKUDS/nanobot/issues/5327) | Issue | 11 | 0 | **最高活跃**：用户报告推理时随机重复相同消息（如 "Good points, let me investigate..."），影响多轮对话体验，11条评论反映社区对此问题高度关注 |
| [#5295](https://github.com/HKUDS/nanobot/issues/5295) | Issue | 5 | 0 | Docker Compose 部署时报 `entrypoint.sh: Permission denied`，5条评论说明多用户遭遇同类问题，需社区协作定位根因 |
| [#5350](https://github.com/HKUDS/nanobot/issues/5350) | Issue | 1 | 0 | 提出在现有 DashScope provider 旁增加 QwenCloud 兼容路径，解决国际开发者迁移痛点，刚提交待评估 |
| [#4010](https://github.com/HKUDS/nanobot/issues/4010) | Issue | 3 | 3 | 语音输出（TTS）功能请求获最多点赞，用户期待闭合"语音输入→文本输出"的对话环路 |
| [#5275](https://github.com/HKUDS/nanobot/issues/5275) | Issue | 1 | 0 | Matrix 频道 "reply in thread" 应形成独立上下文，与 Discord/Slack 行为对齐 |

---

## 5. Bug 与稳定性

### 🔴 P1 级（已修复）

| Issue/PR | 描述 | 状态 | 修复 PR |
|----------|------|------|---------|
| [#5295](https://github.com/HKUDS/nanobot/issues/5295) | Docker Compose 部署 entrypoint.sh 权限拒绝 | ✅ Closed | 待确认 |
| [#4884](https://github.com/HKUDS/nanobot/issues/4884) | WebFetch 将完整用户 URL 发送至 Jina（安全） | ✅ Closed | [#5258](https://github.com/HKUDS/nanobot/pull/5258) |
| Gemini 3 function-call 签名不兼容 | 对话迁移后 replay 失败 | ✅ Closed | [#5230](https://github.com/HKUDS/nanobot/pull/5230) |

### 🟡 P2 级

| Issue/PR | 描述 | 状态 | 修复 PR |
|----------|------|------|---------|
| [#5348](https://github.com/HKUDS/nanobot/issues/5348) | `record_token_usage()` 默认 UTC 与配置时区不一致，导致每日约5小时测试失败 | 🔓 Open | 无 |
| [#5361](https://github.com/HKUDS/nanobot/pull/5361) | 微信 WebUI QR 登录在无 channels 配置时 token 丢失 | 🔓 Open | PR #5361（待合并） |
| [#5327](https://github.com/HKUDS/nanobot/issues/5327) | 推理过程随机重复输出相同消息 | 🔓 Open | 无 |

### 🟢 其他

| Issue/PR | 描述 | 状态 |
|----------|------|------|
| [#5275](https://github.com/HKUDS/nanobot/issues/5275) | Matrix thread 上下文隔离问题 | 🔓 Open |
| [#5342](https://github.com/HKUDS/nanobot/pull/5342) | WebUI Apps Discovery 重设计（含 conflict） | 🔓 Open |
| [#5357](https://github.com/HKUDS/nanobot/pull/5357) | 删除会话前取消活跃 turn，防止竞态覆盖 | 🔓 Open |

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 关联 PR | 纳入下一版本可能性 |
|------|------|---------|-------------------|
| **语音输出（TTS）** | [#4010](https://github.com/HKUDS/nanobot/issues/4010)（3👍） | 无 | ⭐⭐⭐ 高 — 闭合对话环路，社区呼声强 |
| **QwenCloud Provider** | [#5350](https://github.com/HKUDS/nanobot/issues/5350) | 无 | ⭐⭐ 中 — 与现有 DashScope 兼容，风险低 |
| **Session 协作（Mentions）** | [#5358](https://github.com/HKUDS/nanobot/pull/5358) | PR #5358 | ⭐⭐⭐ 高 — PR 已提交，功能完整 |
| **WebUI Apps Discovery 重设计** | [#5342](https://github.com/HKUDS/nanobot/pull/5342) | PR #5342 | ⭐⭐ 中 — 含 conflict，需协调 |
| **跨频道 Setup Flow 优化** | [#5356](https://github.com/HKUDS/nanobot/pull/5356) | PR #5356 | ⭐⭐⭐ 高 — 提升新用户上手体验 |
| **原生 TypeScript TUI** | [#4329](https://github.com/HKUDS/nanobot/pull/4329) | PR #4329 | ⭐ 低 — 架构级变更，含 conflict |

---

## 7. 用户反馈摘要

| 痛点 | 来源 | 典型反馈 |
|------|------|----------|
| **推理重复输出** | [#5327](https://github.com/HKUDS/nanobot/issues/5327) | "随机重复 'Good points, let me investigate' 等短语，影响多轮任务推进" |
| **Docker 部署权限** | [#5295](https://github.com/HKUDS/nanobot/issues/5295) | "按文档部署后 gateway 启动失败，Permission denied" |
| **安全隐私担忧** | [#4884](https://github.com/HKUDS/nanobot/issues/4884) | "WebFetch 将含凭证的完整 URL 发送至第三方 Jina 服务，存在泄露风险" |
| **时区敏感性** | [#5348](https://github.com/HKUDS/nanobot/issues/5348) | "测试在每日 UTC 转换窗口（约22:00-03:00 US Central）确定性失败" |
| **Matrix 线程体验** | [#5275](https://github.com/HKUDS/nanobot/issues/5275) | "Reply in thread 后 bot 继续回复线程，但未形成独立上下文，与其他频道行为不一致" |
| **微信登录状态** | [#5361](https://github.com/HKUDS/nanobot/pull/5361) | "无 channels 配置时 QR 登录 token 静默丢失，需手动排查" |

---

## 8. 待处理积压

| 条目 | 类型 | 未响应时长 | 建议 |
|------|------|-----------|------|
| [#4010](https://github.com/HKUDS/nanobot/issues/4010) | Feature Request | ~3个月 | 优先评估 TTS 实现方案，社区需求明确 |
| [#5350](https://github.com/HKUDS/nanobot/issues/5350) | Feature Request | 1天 | 快速响应，与 DashScope provider 策略对齐 |
| [#5348](https://github.com/HKUDS/nanobot/issues/5348) | Bug | 1天 | 修复时区处理逻辑，避免每日窗口性测试失败 |
| [#5327](https://github.com/HKUDS/nanobot/issues/5327) | Bug | 3天 | 推理重复输出需 root-cause 分析，影响核心体验 |
| [#5275](https://github.com/HKUDS/nanobot/issues/5275) | Bug | 7天 | Matrix 线程上下文行为需与 Discord/Slack 对齐 |
| PR #5291 | Enhancement | 6天 | subagent 对话持久化，需解决 conflict 后合并 |
| PR #5204 | Refactor | 12天 | Responses 能力声明重构，需协调 conflict |
| PR #4329 | Feature | 2个月 | TypeScript TUI 重建，含架构争议，需明确方向 |
| PR #5342 | Feature | 2天 | WebUI Apps Discovery 重设计，含 conflict |

---

**项目健康度评估**：今日安全修复密度高（4个 P1），合并效率高，社区参与度良好。主要风险在于多个 PR 存在 conflict 待协调，以及推理重复输出等核心体验类 Bug 尚未修复。建议优先处理 #5327 和 #5348，同时加快高价值 PR（#5358、#5356）的合并节奏。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目日报 — 2026-08-13

---

## 1. 今日速览

PicoClaw 今日社区活跃度维持中上水平，过去24小时内新增 **3条 Issues** 与 **3条 PR**，无合并/关闭记录，项目整体处于"输入大于输出"的建设期。两个历史遗留 Bug（#3281、#3269）仍挂 [stale] 标签未获修复，反映出核心维护者在稳定性问题上的响应有所滞后。与此同时，围绕路由 Agent 上下文管理（#3316）、Telegram 话题支持（#3315）及 Exa 搜索集成（#3299）的 PR 仍在评审阶段，功能迭代持续推进但合并节奏偏慢。整体项目健康度评估：**良好但需关注稳定性响应**。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日 **0 条 PR 被合并**，3 条待合并 PR 均处于开放评审状态：

| PR | 主题 | 作者 | 状态 |
|---|---|---|---|
| [#3316](https://github.com/sipeed/picoclaw/pull/3316) | 修复 routed-agent 上下文管理（历史/摘要/压缩/seahorse bootstrap） | j-v | OPEN |
| [#3315](https://github.com/sipeed/picoclaw/pull/3315) | 支持 Telegram 私聊机器人中的话题（topics） | genuss | OPEN |
| [#3299](https://github.com/sipeed/picoclaw/pull/3299) | 原生集成 Exa 网页搜索 provider | kesku | OPEN |

**进展评估**：三条 PR 分别触及多 Agent 路由、Telegram 集成、搜索工具三大功能域，均具备实际使用价值。但自创建至今（7-11天）均未被合并，反映审查周期偏长，项目推进速度放缓。

---

## 4. 社区热点

### 🔥 讨论活跃 Issue

**[#3281](https://github.com/sipeed/picoclaw/issues/3281) — Web UI 长历史对话输入卡顿**
- 作者：xpader ｜ 评论：5 ｜ 👍：1 ｜ 标签：BUG / stale
- 用户反馈在 Web UI 中累积较长对话历史后，输入框响应严重延迟。涉及版本 0.3.1，Go 1.25.11。
- **诉求分析**：Web UI 性能是当前用户群体中最具普遍性的痛点，长上下文场景下前端渲染与状态管理需优化。

**[#3269](https://github.com/sipeed/picoclaw/issues/3269) — MCP 服务连接失败导致 Agent 循环挂起**
- 作者：ruiyigen ｜ 评论：4 ｜ 👍：1 ｜ 标签：BUG / stale
- MCP server 连接失败后 agent loop 进入挂起状态，聊天界面停止响应。使用 Qwen3 模型，nightly 构建。
- **诉求分析**：MCP 集成是 PicoClaw 的核心能力，容错机制缺失直接影响生产可用性，属于高优先级修复项。

**[#3330](https://github.com/sipeed/picoclaw/issues/3330) — delegate/spawn/subagent 支持动态模型覆盖**
- 作者：v2up-32mb ｜ 评论：0 ｜ 创建时间：今日
- 当前 delegate/spawn/subagent 工具的模型在调用时无法动态指定，完全依赖静态配置。
- **诉求分析**：多 Agent 场景下灵活切换模型是进阶用户需求，该功能若实现将显著提升工具链的可配置性。

---

## 5. Bug 与稳定性

| 优先级 | Issue | 摘要 | 修复状态 |
|---|---|---|---|
| 🔴 高 | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP 连接失败 → agent loop 挂起，界面停止响应 | ❌ 无 fix PR |
| 🟡 中 | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI 长历史对话输入严重卡顿 | ❌ 无 fix PR |

**稳定性评估**：今日新增 Issue 中 2 条为 Bug，均被标记 stale，且**均无对应修复 PR**，稳定性风险持续累积。MCP 容错问题影响核心功能链路，建议维护者优先跟进。

---

## 6. 功能请求与路线图信号

| 需求 | Issue/PR | 纳入下一版本可能性 |
|---|---|---|
| Exa 原生搜索集成 | [#3299](https://github.com/sipeed/picoclaw/pull/3299) | ⭐⭐⭐⭐ 高 — 工具扩展类 PR，实现完整，评审中 |
| Telegram 私聊话题支持 | [#3315](https://github.com/sipeed/picoclaw/pull/3315) | ⭐⭐⭐ 中高 — 修复型功能补全，逻辑清晰 |
| 动态模型覆盖（delegate/spawn/subagent） | [#3330](https://github.com/sipeed/picoclaw/issues/3330) | ⭐⭐ 中 — 纯功能请求，尚无 PR，需评估实现成本 |
| routed-agent 上下文管理修复 | [#3316](https://github.com/sipeed/picoclaw/pull/3316) | ⭐⭐⭐⭐ 高 — Bug 修复，影响多 Agent 路由场景 |

**路线图判断**：Exa 搜索与 Telegram 话题支持具备较高合并概率，或纳入下一版本；动态模型覆盖为进阶功能，需单独排期。

---

## 7. 用户反馈摘要

- **Web UI 性能**：长对话历史下的输入延迟是真实且普遍的用户痛点（#3281），直接影响日常使用体验，多位用户点赞支持。
- **MCP 容错**：MCP 服务连接失败导致整个 Agent 循环挂起，用户无法继续使用，属于阻断性体验问题（#3269）。
- **多 Agent 路由**：routed-agent 在 Discord 场景下不保留历史消息、不触发自动压缩（#3316），影响多 Agent 部署的实用性。
- **Telegram 场景**：私有频道话题消息无法被正确识别（#3315），导致论坛模式下消息路由异常。
- **灵活配置需求**：用户希望在子 Agent 调用时动态指定模型，而非依赖全局静态配置（#3330），体现进阶用户对灵活性的诉求。

---

## 8. 待处理积压

| 类型 | ID | 标题 | 创建时间 | 风险 |
|---|---|---|---|---|
| 🐛 Bug (stale) | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI 输入卡顿 | 2026-07-21 | 用户体验退化 |
| 🐛 Bug (stale) | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP 连接失败导致挂起 | 2026-07-20 | 核心功能阻断 |
| 🔧 PR (待审) | [#3316](https://github.com/sipeed/picoclaw/pull/3316) | routed-agent 上下文修复 | 2026-08-03 | 多 Agent 场景 |
| 🔧 PR (待审) | [#3315](https://github.com/sipeed/picoclaw/pull/3315) | Telegram 话题支持 | 2026-08-03 | 集成补全 |
| 🔧 PR (待审) | [#3299](https://github.com/sipeed/picoclaw/pull/3299) | Exa 搜索集成 | 2026-07-26 | 工具扩展 |

**维护者关注建议**：两条 stale Bug（#3281、#3269）已超过 20 天未获响应，且均无修复 PR，存在社区信任损耗风险。建议优先关闭或指派，以维护项目活跃度信号。三条待合并 PR 审查周期亦偏长，可考虑安排评审排期。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# 📅 NanoClaw 项目日报 | 2026-08-13

## 1. 今日速览
过去24小时 NanoClaw 保持稳健的高频开发节奏，共产生 4 条新 Issue 与 10 条 PR 更新（9 待合并 / 1 已关闭）。项目当前处于**Agent 插件化架构落地**的关键冲刺期，核心工作围绕模板系统重构、多平台消息路由修复及可观测性增强展开。无新版本发布，但底层引擎与 Skill 生态的迭代密度较高，整体健康度良好。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
- **已合并**：`[PR #3086](https://github.com/qwibitai/nanoclaw/pull/3086)` 修复 WhatsApp 渠道在未注册接收方时仍返回虚假 `platformMsgId` 的静默失败问题，提升通道交付可靠性。
- **核心推进**：`[PR #3220](https://github.com/qwibitai/nanoclaw/pull/3220)` 将 Agent 模板全面升级为 Agent Plugins 1.0 目录规范，并同步完成 stamp-time 的 symlink/caps/secret 安全加固；`[PR #2909](https://github.com/qwibitai/nanoclaw/pull/2909)` 在其基础上补齐向导模板流程与首次 Agent 生成逻辑；`[PR #3231](https://github.com

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目动态日报
**日期：2026-08-13** | 数据来源：GitHub (nearai/ironclaw)

---

## 1. 今日速览

过去24小时项目保持**高活跃度**：共更新 Issues 41 条、PR 50 条，其中 12 个 Issue 和 19 个 PR 已关闭/合并。两个 `-rc.3` 级别候选版本发布，核心聚焦于运行时容器健康检查修复与 Windows 文件系统兼容性。今日 bug 集中爆发于 Telegram 渠道交互（6 个 P1/P2 问题），同时 agent loop 上下文窗口优化、多工具并行执行、自定义模型偏好等核心能力持续推进。整体项目处于 v1.2.0 发布候选冲刺期，技术债务清理与新功能交付并行。

---

## 2. 版本发布

### ironclaw-v1.2.0-rc.3（2026-08-12）
**类型：** 候选发布（Release Candidate）

**修复内容：**
- 运行时容器镜像新增 `curl` 安装，使编排器的 HTTP 健康检查（`curl -fsS http://localhost:3000/`）可正常执行
- 解决因镜像缺少 HTTP 客户端导致容器永远无法被标记为健康的问题

**PR 关联：** #7555（已合并）

---

### ironclaw-v1.2.0-rc.2（2026-08-12）
**类型：** 候选发布（Release Candidate）

**修复内容：**
- Windows 首次启动文件系统发布改用原生原子重命名语义，替代原有的硬链接方案，兼容不支持目录同步的环境
- Release smoke 测试保留 Windows 账户身份，用于保护独立密钥并隔离工作区

**破坏性变更：** 无声明
**迁移注意：** 无

---

## 3. 项目进展

### 今日已合并/关闭的重要 PR

| PR | 作者 | 标题 | 影响 |
|----|------|------|------|
| [#7560](https://github.com/nearai/ironclaw/pull/7560) | henrypark133 | fix(release): retry the dist installer download | 修复 musl 发行版下载超时问题 |
| [#7555](https://github.com/nearai/ironclaw/pull/7555) | henrypark133 | fix(docker): install curl for healthchecks | 容器健康检查修复（forward-port） |
| [#7550](https://github.com/nearai/ironclaw/pull/7550) | thisisjoshford | feat(extensions): per-field help text on admin config forms | 管理员配置表单增加字段说明 |
| [#5503](https://github.com/nearai/ironclaw/pull/5503) | serrrfirat | Add compact Google extension capabilities | Gmail/Calendar 能力精简优化 |
| [#7427](https://github.com/nearai/ironclaw/pull/7427) | serrrfirat | release: prepare 1.1.1-rc.1 | 1.1 分支紧急修复发布 |
| [#6836](https://github.com/nearai/ironclaw/pull/6836) | achalvs | @ironclaw/ui and workspace refactor | WebUI 设计系统重构 |

**进展评估：** 今日共完成 19 个 PR 合并/关闭，涵盖发布基础设施、容器运行时、UX 改进和 Google 扩展优化，项目整体向 v1.2.0 正式版稳步迈进。

---

## 4. 社区热点

### 讨论最活跃的 Issue/PR

| ID | 类型 | 标题 | 评论数 | 作者 | 链接 |
|----|------|------|--------|------|------|
| #7360 | Enhancement | Expand stress coverage across built-in and durable write paths | 3 | serrrfirat | [链接](https://github.com/nearai/ironclaw/issues/7360) |
| #7407 | Bug | Execute BatchPolicy::Parallel capability batches concurrently | 3 | serrrfirat | [链接](https://github.com/nearai/ironclaw/issues/7407) |
| #7484 | Bug | Context window silently evicts the task | 1 | serrrfirat | [链接](https://github.com/nearai/ironclaw/issues/7484) |
| #7554 | Bug | Custom MCP server add flow shows validation error | 1 | sergeiest | [链接](https://github.com/nearai/ironclaw/issues/7554) |
| #5508 | Bug | Slack delivery target not found despite active connection | 1 | joe-rlo | [链接](https://github.com/nearai/ironclaw/issues/5508) |
| #6541 | Bug | WebUI constantly reconnecting | 1 | sergeiest | [链接](https://github.com/nearai/ironclaw/issues/6541) |

**热点分析：**
- **#7360** 和 **#7407** 均为 serrrfirat 主导的性能/能力优化议题，反映团队对多工具调用并行化和压力测试覆盖率的重视
- **#7484** 上下文窗口驱逐问题引发关注，涉及 128 条消息硬限制和 prompt 构建策略
- **#7554** 反映用户在实际使用 Custom MCP 时的痛点和产品反馈渠道（Slack → GitHub）的联动

---

## 5. Bug 与稳定性

### 今日新报告 Bug（按严重程度排列）

#### 🔴 P1 — 阻断性

| ID | 标题 | 实例 | 状态 | 关联 PR |
|----|------|------|------|---------|
| [#7538](https://github.com/nearai/ironclaw/issues/7538) | Telegram agent 收到 GIF/贴纸后完全卡死 | Railway | OPEN | — |
| [#7536](https://github.com/nearai/ironclaw/issues/7536) | 多用户访问流损坏 — "Invalid secret" 错误 | Railway | OPEN | — |
| [#7535](https://github.com/nearai/ironclaw/issues/7535) | Telegram webhook 保存后未激活 | Railway | OPEN | — |

#### 🟠 P2 — 高优先级

| ID | 标题 | 实例 | 状态 | 关联 PR |
|----|------|------|------|---------|
| [#7541](https://github.com/nearai/ironclaw/issues/7541) | Agent 无法将生成文件作为 Telegram 附件发送 | Railway | OPEN | — |
| [#7539](https://github.com/nearai/ironclaw/issues/7539) | Telegram 用户消息显示顺序错乱 | Railway | OPEN | — |
| [#7540](https://github.com/nearai/ironclaw/issues/7540) | 超长 Telegram 消息被截断丢失 | Railway | OPEN | — |
| [#7542](https://github.com/nearai/ironclaw/issues/7542) | Agent 未识别对话已在 Telegram 中 | Railway | OPEN | — |
| [#7545](https://github.com/nearai/ironclaw/issues/7545) | Agent 错误声称无法获取实时加密市场数据 | Railway | OPEN | — |
| [#7544](https://github.com/nearai/ironclaw/issues/7544) | Agent 暴露内部推理/规划过程 | Railway | OPEN | — |
| [#7543](https://github.com/nearai/ironclaw/issues/7543) | Telegram routine 执行成功但未投递消息 | Railway | OPEN | — |
| [#7508](https://github.com/nearai/ironclaw/issues/7508) | GitHub MCP 扩展启动时验证提示混乱 | Railway | OPEN | — |
| [#7554](https://github.com/nearai/ironclaw/issues/7554) | Custom MCP server 添加流程验证错误 | — | OPEN | — |

#### 🟡 P3 — 中低优先级

| ID | 标题 | 实例 | 状态 |
|----|------|------|------|
| [#7546](https://github.com/nearai/ironclaw/issues/7546) | Agent 不对 Telegram 贴纸做出反应 | Railway | OPEN |
| [#7547](https://github.com/nearai/ironclaw/issues/7547) | Instance 升级在 egress apply 阶段失败 | Agent Staging | OPEN |

**已有关联修复 PR：**
- Telegram 相关 Bug 群集（#7535/#7538/#7539/#7540/#7541/#7542/#7543/#7546）目前均**尚未合并对应 fix PR**，需重点关注
- #7538（agent 卡死）和 #7536（多用户 secret 失效）为 P1 级别，建议优先处理

---

## 6. 功能请求与路线图信号

### 新功能需求

| ID | 标题 | 作者 | 潜在版本 |
|----|------|------|----------|
| [#7517](https://github.com/nearai/ironclaw/issues/7517) | Cloud.near.ai 支持 Google/GitHub 登录时绑定 NEAR 钱包进行 staking | sergeiest | v1.3.0 |
| [#7537](https://github.com/nearai/ironclaw/issues/7537) | 通用 per-request thinking/effort 控制（含 DeepSeek chat_template_kwargs） | serrrfirat | v1.3.0 |
| [#7044](https://github.com/nearai/ironclaw/issues/7044) | Onboarding to channel-first approach（Epic） | sergeiest | v1.4.0 |

### 已有关联 PR 的功能

| PR | 标题 | 状态 |
|----|------|------|
| [#7439](https://github.com/nearai/ironclaw/pull/7439) | Per-user model preferences and commands（`/model`、`/model use`、`/model default`） | OPEN |
| [#7491](https://github.com/nearai/ironclaw/pull/7491) | OMP core-tool contract + engines + benchmark（read/write/edit/glob/grep 统一） | OPEN |
| [#6994](https://github.com/nearai/ironclaw/pull/6994) | OOBE automation-tasks prototype — carousel, inline cards, agent-mode pill | OPEN |
| [#7464](https://github.com/nearai/ironclaw/pull/7464) | Telegram linked-device — device-link auth, session custody | OPEN |

**路线图判断：**
- **#7439**（用户模型偏好）和 **#7491**（统一 coding tool contract）大概率纳入 v1.2.0 或 v1.3.0
- **#6994**（OOBE onboarding）作为 Epic #7044 的一部分，方向明确，预计 v1.3.0+
- **#7464**（Telegram linked device）是渠道增强的重要功能，处于开放审查中

---

## 7. 用户反馈摘要

### 真实痛点

1. **Telegram 渠道稳定性问题突出**
   - 用户反馈 agent 收到 GIF/贴纸后完全卡死（#7538）
   - 消息顺序错乱导致对话体验不佳（#7539）
   - 长消息被截断、文件无法以附件形式发送（#7540, #7541）
   - Agent 无法识别对话上下文已在 Telegram 中（#7542）

2. **WebUI 交互体验问题**
   - WebUI 持续显示"Reconnecting"提示，虽不影响功能但造成困惑（#6541）
   - Custom MCP server 添加流程出现误导性验证错误（#7554）
   - 多用户共享实例时收到"Invalid secret"错误（#7536）

3. **功能发现与 onboarding 门槛**
   - 新用户进入 WebUI 后面对空白界面不知如何操作（#7044）
   - Google/GitHub 登录用户无法绑定 NEAR 钱包进行 staking（#7517）

### 用户满意点
- 已有用户报告旧 Slack 路由仍正常工作，表明 backward compatibility 保持良好（#5508 中的侧面信息）
- WebUI 重新连接的警告虽烦人但不影响实际工作（#6541）

---

## 8. 待处理积压

### 长期未响应的重要 Issue

| ID | 标题 | 创建时间 | 天数 | 严重程度 | 建议 |
|----|------|----------|------|----------|------|
| [#5508](https://github.com/nearai/ironclaw/issues/5508) | Slack delivery target not found despite active connection | 2026-07-01 | 43 | P2 | 需确认是否仍有重现 |
| [#6993](https://github.com/nearai/ironclaw/issues/6993) | Backend wiring for OOBE automation-tasks | 2026-08-01 | 12 | — | 有对应 PR #6994 |
| [#7042](https://github.com/nearai/ironclaw/issues/7042) | Design System Phase 2: governance & guidelines | 2026-08-03 | 10 | — | 有对应 PR #7043 |
| [#7038](https://github.com/nearai/ironclaw/issues/7038) | Epic: Storybook + AI-first Design System | 2026-08-03 | 10 | — | 多 PR 并行推进中 |

### 维护者关注提醒

- **Telegram Bug 集群**（#7535–#7546）：今日集中报告 11 个 Telegram 相关问题，其中 3 个 P1，建议优先安排修复
- **#7383** 工具披露端口（4,425 行）分解追踪：大文件重构需持续关注
- **#7547** Instance 升级失败：staging 环境的 egress apply 问题可能影响生产发布流程

---

**报告生成时间：** 2026-08-13 | **分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI 项目动态日报
**日期：2026-08-13 | 数据来源：github.com/netease-youdao/LobsterAI**

---

## 1. 今日速览

过去24小时项目保持中等活跃度，共处理 14 个活动（6 Issues + 8 PRs），其中 8 个 PR 已合并/关闭，2 个 PR 待合并。今日无新版本发布，主要聚焦于技能管理优化、Windows 安装修复和 UI 交互改进。项目整体健康度良好，修复类 PR 占比 75%，社区反馈型 Issue 仍在积累中。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|----|------|------|
| [#2480](https://github.com/netease-youdao/LobsterAI/pull/2480) | Release | Release/2026.8.12 版本准备 PR |
| [#2482](https://github.com/netease-youdao/LobsterAI/pull/2482) | feat | Skills 管理器拆分"我的"/"内置"标签页，改善技能分类管理体验 |
| [#2481](https://github.com/netease-youdao/LobsterAI/pull/2481) | feat | 将任务搜索移至侧边栏头部操作区，统一 macOS/Windows 外观 |
| [#2479](https://github.com/netease-youdao/LobsterAI/pull/2479) | fix | 修复 Windows 安装时 junction 符号链接被破坏的问题，避免 `EPERM` 错误 |
| [#2478](https://github.com/netease-youdao/LobsterAI/pull/2478) | fix | 修复 macOS/Windows 上大文件图标尺寸渲染异常 |
| [#1233](https://github.com/netease-youdao/LobsterAI/pull/1233) | feat | 为模型提供商添加官网链接和 API Key 获取引导，合并重复 URL 表 |
| [#2483](https://github.com/netease-youdao/LobsterAI/pull/2483) | fix | **待合并** - 修复 skill 条目 key 与 frontmatter name 不匹配导致 UI 开关静默失效的问题（关联 #244） |
| [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | fix | **待合并** - 在 Cowork 会话列表中隐藏 OpenClaw 内部主 agent 会话，避免用户困惑 |

**整体推进：** 今日修复了 Windows 安装稳定性、技能管理 UX、搜索入口布局等多个问题，项目工程质量和用户体验同步提升。

---

## 4. 社区热点

### 关注度高/有代表性的 Issues

| Issue | 状态 | 主题 | 链接 |
|-------|------|------|------|
| #1179 | OPEN | 3.31 版本强制沙箱，用户找不到关闭入口 | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) |
| #1173 | OPEN | 卸载后程序仍可运行，引发"后门"担忧 | [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) |
| #1174 | OPEN | 请求支持多个自定义模型提供商 | [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) |
| #1180 | OPEN | 修改自建 Agent 图标触发网关反复重启 | [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) |

**诉求分析：**
- **#1179** 反映用户对版本升级后行为变更感知不足，沙箱功能缺乏显式控制入口，建议发布说明中突出说明或提供快捷配置项。
- **#1173** 涉及用户信任问题，需明确解释卸载残留进程的存在原因（后台服务/网关组件），并提供完整的清理方案。
- **#1174** 是多提供商需求，与 #1233（单提供商引导优化）方向互补，可作为下一阶段功能规划参考。

---

## 5. Bug 与稳定性

| 问题 | 严重度 | Issue | Fix PR | 状态 |
|------|--------|-------|--------|------|
| 修改自建 Agent 图标触发网关反复重启 | 中 | [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) | — | 未修复 |
| 创建定时任务报错 | 中 | [#2071](https://github.com/netease-youdao/LobsterAI/issues/2071) | — | 已关闭（待确认是否修复） |
| 插件 ID 不匹配启动警告 | 低 | [#1236](https://github.com/netease-youdao/LobsterAI/issues/1236) | — | 已关闭 |
| Windows 安装破坏 junction 依赖 | 高 | — | [#2479](https://github.com/netease-youdao/LobsterAI/pull/2479) | ✅ 已合并 |

**稳定性评估：** 已合并的 #2479 解决了 Windows 安装路径依赖问题，是高优修复。网关重启问题（#1180）暂无对应 PR，建议关注。

---

## 6. 功能请求与路线图信号

| 需求 | Issue | 关联 PR | 纳入可能性 |
|------|-------|---------|-----------|
| 支持多个自定义模型提供商 | [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) | — | 中 - 需求明确，需前端/后端联调 |
| 隐藏内部 OpenClaw 会话 | — | [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | 高 - PR 已提交待合并 |
| skill 条目 key 规范化 | — | [#2483](https://github.com/netease-youdao/LobsterAI/pull/2483) | 高 - 修复现有缺陷，待合并 |

**路线图信号：** 今日合并的 #2482（技能管理 tab 拆分）和 #2481（搜索入口优化）表明项目正持续推进 UI/UX 精细化改进，下一版本可能侧重配置体验和功能可见性。

---

## 7. 用户反馈摘要

| 痛点/场景 | 来源 | 反馈性质 |
|-----------|------|----------|
| 版本升级后功能行为变更无提示，找不到关闭沙箱入口 | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | 不满意 |
| 卸载不彻底引发安全疑虑 | [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) | 不满意/担忧 |
| 自建 Agent 图标修改导致网关不稳定 | [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) | 不满意 |
| 希望支持多模型提供商切换而不丢失旧配置 | [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) | 需求 |
| 插件配置警告影响使用体验 | [#1236](https://github.com/netease-youdao/LobsterAI/issues/1236) | 已解决 |
| 模型提供商引导信息需优化（官网/API Key 入口） | [#1233](https://github.com/netease-youdao/LobsterAI/pull/1233) | 满意 |

---

## 8. 待处理积压

| 类型 | 编号 | 说明 | 建议优先级 |
|------|------|------|-----------|
| PR | [#2483](https://github.com/netease-youdao/LobsterAI/pull/2483) | skill 条目 key 修复，关联 #244，待合并 | 高 |
| PR | [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | 隐藏内部会话，提升 Cowork 体验，待合并 | 高 |
| Issue | [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) | 自建 Agent 修改触发网关重启，影响稳定性 | 高 |
| Issue | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | 沙箱功能控制入口缺失，用户引导问题 | 中 |
| Issue | [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) | 卸载残留进程引发信任问题，需官方澄清 | 中 |

---

**报告生成时间：** 2026-08-13 | **分析师：** LobsterAI 开源项目观察

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 | 2026-08-13

## 1. 今日速览
过去24小时 CoPaw 保持高频活跃：Issue 更新 31 条（新开/活跃 23，已关闭 8），PR 更新 43 条（待合并 26，已合并/关闭 17），并发布 `v2.1.0-beta.4`。项目当前重心明确指向 **记忆系统提示词精简、多步任务执行稳定性、LLM 缓存性能优化及控制台 UI 体验**。社区反馈显示，Agent 中途“规划后静默停止”、历史会话压缩后内容丢失、网络瞬断后无法自愈等体验问题仍较突出，但维护者响应迅速，多个核心 Bug 已快速跟进修复或进入 Review。整体健康度良好，处于 v2.1.0 正式版发布前的冲刺打磨期。

---

## 2. 版本发布
**v2.1.0-beta.4**
- **更新内容**：修复文件预览与暗黑模式样式错位；更正 `read_file` 工具描述；版本标识升级至 `2.1.0b4`。
- **破坏性变更**：无。
- **迁移注意事项**：Beta 阶段迭代较快，建议升级前备份 `config.json` 与自定义插件配置；部分历史会话的上下文压缩行为已调整，如需验证可配合 `/compact` 命令重新触发。

---

## 3. 项目进展
今日合并/关闭的重要 PR 集中体现在记忆系统、跨平台适配与安全合规三个方向：
- `#6942` **[CLOSED]** 精简长期记忆提示词，修正 `prompts.py` 中关于 Dream 自动同步至 `MEMORY.md` 的错误描述，直接关闭 `#6853`。Agent 不再暴露内部存储实现细节，统一表现为“个人知识库”能力。
- `#6913` **[CLOSED]** 修复 macOS Computer Use 在激活瞬态菜单与复合无障碍元素时的误触问题，提升桌面自动化稳定性。
- `#6540` **[CLOSED]** 增强工具消息清洗逻辑，防止上下文压缩后孤立 Tool Result 污染后续模型调用。
- `#6956` **[CLOSED]** 回滚 `#6816` 对 `dict-like` 模型响应的临时处理，说明上游修复方案仍需重构，团队正通过 `#6956` + 后续 PR 重新打磨 `consume_model_response` 的路由逻辑。
- `#6950` / `#6949` **[CLOSED/OPEN]** 发布 Files 工作区与长期记忆双语言官方博客，降低新用户上手门槛。

**进展评估**：今日修复闭环率高，记忆系统与底层响应处理进入收敛期，项目正从“功能堆叠”转向“体验与稳定性加固”。

---

## 4. 社区热点
以下为评论数最高的 Issue（按热度排序）：
1. `#6853` [CLOSED] **Dream 写入路径与

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报 — 2026-08-13

---

## 1. 今日速览

过去24小时 ZeroClaw 仓库保持高频活跃，共新增/更新 50 条 Issues 与 50 条 PR，其中 20 条 PR 已合并或关闭，涵盖微信通道、MCP 延迟访问策略、浏览器截图路径验证、运行时终端标记清理等多个核心子系统。项目整体处于 **功能完善与安全加固并重** 的阶段：本日发布零版本，但多项 P1 级安全修复（SSRF 防护、截图路径注入、WASM 导出超时边界）已进入待合并队列，社区对跨平台兼容性的诉求（Windows 74 个测试失败、macOS 桌面窗口异常）持续升温。

---

## 2. 版本发布

**无新版本发布。**

上一个已知版本为 `v0.8.3`，已引入 cosign bundles、GitHub artifact attestations 与 slsa-github-generator 三种并行签名机制，但存在冗余问题，预计将在 #9101 合并后统一为单一签名故事。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 摘要 | 推进方向 |
|----|------|----------|
| [#9956](https://github.com/zeroclaw-labs/zeroclaw/pull/9956) | 修复微信通道：仅在入站批次入队后才持久化同步游标，避免崩溃导致消息重复 | 稳定性/数据一致性 |
| [#8496](https://github.com/zeroclaw-labs/zeroclaw/pull/8496) | 统一延迟 MCP 访问策略为单一事实来源，修复 #8054 Surface 1(b) 的策略遗漏 | 安全策略/架构一致性 |
| [#9362](https://github.com/zeroclaw-labs/zeroclaw/pull/9362) | 浏览器截图动作增加 `is_path_allowed` + `resolve_tool_path` 校验，关闭任意文件写入漏洞 | **P1 安全修复** |
| [#8741](https://github.com/zeroclaw-labs/zeroclaw/pull/8741) | 同上（历史重复 PR） | — |
| [#9695](https://github.com/zeroclaw-labs/zeroclaw/pull/9695) | 从流式/非流式响应路径剥离 `<eom>`/`<|eom|>` 终端标记，防止污染 agent 输出 | 运行时稳定性 |
| [#9715](https://github.com/zeroclaw-labs/zeroclaw/pull/9715) | JSONL 会话迁移改为原子事务提交，确保迁移可重试 | 数据迁移可靠性 |
| [#9419](https://github.com/zeroclaw-labs/zeroclaw/pull/9419) | 按 credential 粒度冷却 429 限流，实现活凭证轮换 | -provider 稳定性 |
| [#9403](https://github.com/zeroclaw-labs/zeroclaw/pull/9403) | WASM 插件导出增加 `call_timeout_ms`（默认 30s）墙钟 deadline，防止 guest 无限挂起 | **P1 安全修复** |
| [#9672](https://github.com/zeroclaw-labs/zeroclaw/issues/9672) 关联修复 | CLI cron help 示例修正 | 文档/CLI 一致性 |

**整体判断：** 今日 20 条已关闭 PR 中，**4 条为 P1 级安全修复**（截图注入、WASM 超时、MCP 策略），安全性指标显著提升；3 条为运行时稳定性修复（终端标记、微信游标、凭证轮换），项目健壮性持续累积。

---

## 4. 社区热点

### 讨论最活跃的 Issues

1. **[Issue #7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462)** — 14 条评论  
   Windows 11 运行测试套件产生 74 个失败，根因是 Unix-only 路径语义、console CP936 编码及 CI 仅在 Linux 运行。作者 `NiuBlibing`，S2 严重度。  
   **诉求分析：** 跨平台兼容性是用户痛点，尤其 Windows 用户群体扩大后，CI 缺失 Windows/macOS 覆盖已成为阻塞性缺陷。

2. **[Issue #8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692)** — 13 条评论  
   Maintainer 决策队列 tracker，用于 RFC、设计 Issue、发布策略的集中审批流。  
   **诉求分析：** 项目治理结构化需求强烈，维护者需要工具来管理决策积压，而非散落在各 Issue 中。

3. **[Issue #8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832)** — 9 条评论  
   插件拥有的 Kanban 看板，协调 Agent 工作流，由插件拥有卡片语义、状态机与依赖关系。  
   **诉求分析：** 高级用户期望 ZeroClaw 提供可视化的 Agent 工作编排能力，类似 developer workflow 工具。

4. **[Issue #9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101)** — 9 条评论  
   合并三种并行发布签名机制（cosign/attestations/slsa），从 53 个 release asset 精简至约 20 个。  
   **诉求分析：** v0.8.3 三个签名 PR 在 26 小时内先后合并而互不知情，造成 CI 浪费与 asset 膨胀，社区要求统一签名故事。

5. **[Issue #7929](https://github.com/zeroclaw-labs/zeroclaw/issues/7929)** — 7 条评论  
   统一 web UI、ZeroCode TUI、channel runtime 三处的 slash command 注册表，避免列表漂移。  
   **诉求分析：** 命令列表多处维护导致体验不一致，是典型的架构债问题。

---

## 5. Bug 与稳定性

按严重程度排列：

| Issue | 严重度 | 摘要 | Fix PR |
|-------|--------|------|--------|
| [#9207](https://github.com/zeroclaw-labs/zeroclaw/issues/9207) | **S1** | `web_fetch` 对 gzip/brotli/deflate 压缩响应返回乱码，agent 无法解析 | 无 |
| [#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527) | **S1** | macOS 桌面 App 重启后窗口消失或白屏，权限检测失效 | 无 |
| [#9290](https://github.com/zeroclaw-labs/zeroclaw/issues/9290) | **S1** | Windows 桌面安装器启动时缺失 `TaskDialogIndirect`，导致崩溃 | 无 |
| [#9198](https://github.com/zeroclaw-labs/zeroclaw/issues/9198) | S3 | Discord 输入指示器在 daemon reload 后永久卡住 | 无 |
| [#9202](https://github.com/zeroclaw-labs/zeroclaw/issues/9202) | S3 | `zeroclaw desktop` 命令使用失效下载 URL，且无法检测已安装 AppImage | 无 |
| [#9340](https://github.com/zeroclaw-labs/zeroclaw/issues/9340) | **S1** | CLI 创建的 cron 作业 `delivery.mode = "none"` 导致输出静默丢弃 | #9672（已关闭） |

**风险评估：** 本日公布 **3 个 S1 级阻塞性 Bug**（web_fetch 压缩、macOS 窗口、Windows 崩溃），其中前两个均无关联 fix PR，建议在 v0.9.0 发布前优先处理。#9340 已确认根因，修复 PR 待合并。

---

## 6. 功能请求与路线图信号

| Issue | 类型 | 核心诉求 | 纳入下一版本可能性 |
|-------|------|----------|-------------------|
| [#8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832) | Feature | 插件级 Kanban 看板协调 Agent 工作 | 中（需 RFC 流程） |
| [#5316](https://github.com/zeroclaw-labs/zeroclaw/issues/5316) | Feature | SearXNG 隐私搜索 + DuckDuckGo CAPTCHA 检测 | 高（已在 PR 队列） |
| [#6998](https://github.com/zeroclaw-labs/zeroclaw/issues/6998) | Feature | Schema 验证的记忆合并 + 有界降级 | 高（memory 子系统重构） |
| [#5907](https://github.com/zeroclaw-labs/zeroclaw/issues/5907) | Feature | Opt-in LSP 支持，减少 Agent 幻觉 | 中（需评估与 Claude Code 对齐） |
| [#9644](https://github.com/zeroclaw-labs/zeroclaw/issues/9644) | Feature | v0.9.0 移除 Lucid 内存连接器（上游已休眠） | 确定（已明确版本） |
| [#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) | Enhancement | 统一发布签名机制，精简 asset | 高（安全性驱动） |
| [#7461](https://github.com/zeroclaw-labs/zeroclaw/issues/7461) | Feature | CI 扩展至 Windows/macOS 测试矩阵 | 高（依赖 #7462 修复） |
| [#9511](https://github.com/zeroclaw-labs/zeroclaw/issues/9511) | Feature | Semgrep  diff-aware 发现以 PR comment 形式展示 | 中（安全 CI 改进） |
| [#9556](https://github.com/zeroclaw-labs/zeroclaw/pull/9556) | Enhancement | Langfuse 可观测性后端（OTel 兼容） | 高（PR 已在队列） |
| [#8337](https://github.com/zeroclaw-labs/zeroclaw/pull/8337) | Enhancement | Herdr Agent 生命周期上报集成 | 中（PR 已在队列） |

**路线图判断：** v0.9.0 将聚焦 **记忆后端清理**（移除 Lucid）、**签名机制统一**、**跨平台 CI 覆盖**三大目标，同时 Langfuse/Herdr 可观测性扩展与 LSP 支持有望进入候选功能。

---

## 7. 用户反馈摘要

| 来源 | 真实痛点 | 场景 |
|------|----------|------|
| #7462 / #7461 | Windows 用户运行测试套件时 74 个用例失败，CI 无覆盖 | 本地开发、贡献者体验 |
| #9207 | `web_fetch` 对现代压缩网站返回二进制乱码，agent 完全无法解析 | 自主 Agent 网页抓取 |
| #7527 | macOS 桌面 App 重启后权限检测失效、窗口消失 | 桌面端用户日常使用 |
| #9290 | Windows 安装器因 `TaskDialogIndirect` 缺失而崩溃 | Windows 新用户安装 |
| #9198 | Discord 机器人 typing 指示器在 daemon reload 后永久卡住 | Discord 频道管理员 |
| #9202 | `zeroclaw desktop` 命令指向失效 URL，且无法识别已安装 AppImage | Linux 桌面用户 |
| #9340 | cron 作业输出静默丢弃，运行记录显示 ok 但结果无处可查 | 定时 Agent 任务用户 |
| #9644 | Lucid 内存连接器上游已休眠 4 天，项目被绑定在停滞依赖上 | 记忆功能使用者 |

**满意度信号：** 用户对 **跨平台稳定性**（Windows/macOS 桌面）、**Agent 工具可靠性**（web_fetch 压缩、cron 交付）和 **可观测性扩展**（Langfuse/Herdr）诉求强烈；同时对 **安全加固**（SSRF、截图注入、WASM 超时）持高度认可态度。

---

## 8. 待处理积压

| Issue/PR | 状态 | 风险 | 建议行动 |
|----------|------|------|----------|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | OPEN，14 评论，无 fix PR | **高** — 阻塞 Windows 用户与贡献者 | 排入 v0.9.0 前优先修复，同步 #7461 扩展 CI 矩阵 |
| [#9207](https://github.com/zeroclaw-labs/zeroclaw/issues/9207) | OPEN，5 评论，无 fix PR | **高** — S1 阻塞 Agent 网页抓取 | 紧急修复，`web_fetch` 压缩解码逻辑 |
| [#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527) | OPEN，2 评论，无 fix PR | **高** — macOS 桌面可用性 | 需要 macOS 贡献者复现与修复 |
| [#9290](https://github.com/zeroclaw-labs/zeroclaw/issues/9290) | OPEN，1 评论，无 fix PR | **高** — Windows 安装器崩溃 | 检查 `TaskDialogIndirect` 最低 Windows 版本要求 |
| [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713) | OPEN，待审 | **高** — file_download SSRF 防护 | 尽快合并，SSRF 是 P1 安全风险 |
| [#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) | OPEN，9 评论，RFC 阶段 | 中 — 发布流程优化 | 推进 RFC 决策，统一签名故事 |
| [#9644](https://github.com/zeroclaw-labs/zeroclaw/issues/9644) | OPEN，4 评论 | 中 — 依赖清理 | 在 v0.9.0 中按计划移除 Lucid connector |
| [#9323](https://github.com/zeroclaw-labs/zeroclaw/issues/9323) | OPEN，4 评论 | 中 — 执行树迭代预算未生效 | `shared_budget` 始终为 None，需架构决策 |

---

**报告生成时间：** 2026-08-13  
**数据来源：** ZeroClaw GitHub Repository（github.com/zeroclaw-labs/zeroclaw）  
**项目健康度评级：** 🟢 活跃 — 安全修复密集，跨平台债务需加速清理

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*