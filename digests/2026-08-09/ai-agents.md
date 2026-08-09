# OpenClaw 生态日报 2026-08-09

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-09 02:10 UTC

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



# OpenClaw 项目日报 | 2026-08-09

---

## 1. 今日速览

OpenClaw 在过去24小时内保持**极高活跃度**：500条Issue更新（新开/活跃448，关闭52）与500条PR更新（待合并325，已合并/关闭175）形成显著吞吐比，表明大量修复正在排队review。今日发布两个版本（v2026.6.33、v2026.6.34），核心聚焦于**安全边界加固**——sandboxed浏览器路由、可信DNS目标、OAuth路径限流。社区对网关内存泄漏、子代理消息丢失、会话状态恢复等P0/P1级问题高度关注，多个Issue评论数超过20条，显示生产环境稳定性仍是用户最大痛点。整体项目处于"安全加固+稳定性攻坚"双轨并行状态。

---

## 2. 版本发布

### v2026.6.34
**核心亮点：浏览器与网络边界安全加固**
- Sandbox隔离浏览器路由，拒绝不安全访问路径
- 可信DNS目标限制，防止DNS污染攻击
- 自定义浏览器起源限制
- Loopback provider端点安全策略

**贡献者：** @eleqtrizit, @brunowowk, @mosidevv, @pgondhi987

🔗 相关Issue: #97958, #38290, #103075, #110693

### v2026.6.33
**核心亮点：网络与凭证边界安全加固**
- Provider流式响应大小限制，防止资源耗尽
- Discord REST响应防护
- Browser fetch安全策略
- OAuth路径响应大小限制
- 日志中移除Telegram凭证

**贡献者：** @wangmiao0668000666, @Alix-007

🔗 相关Issue: #96989, #95412, #99428

---

## 3. 项目进展

### 今日合并/关闭的重要PR

| PR | 类型 | 说明 |
|----|------|------|
| #119511 | fix | **归档已清理的cron会话转录** — 修复`tasks maintenance --apply`硬删除SQLite行时不写压缩归档的问题，关闭#119269 |
| #120802 | fix | **Windows环境变量大小写保留** — 修复Windows子进程因key大小写不同而忽略配置的env override |
| #120813 | fix | **Mistral转录状态重置** — WebSocket重连后重置转录状态，防止fragment继承 |
| #120817 | fix | **Telegram reply模式恢复** — 修复beta.1中account-specific `replyToMode`设置被忽略的回归 |
| #120820 | fix | **UI暗色模式闪烁修复** — Dashboard组件暗色模式下白色闪烁问题 |

### 项目推进评估
- **安全性**：连续两个版本聚焦网络/浏览器/凭证边界加固，安全优先级明确
- **稳定性**：175条PR已处理，大量session-state和message-loss修复正在review队列
- **功能演进**：Code Mode追溯、子代理路由、设备配对等前沿功能持续投入

---

## 4. 社区热点

### 🔥 高评论Issue TOP5

| Issue | 评论 | 状态 | 核心问题 |
|-------|------|------|----------|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | 179 | ✅ Closed | **DeepSeek v4 Flash静默失败** — 无回复生成，通用fallback，影响Telegram群组场景 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 31 | 🔄 Open | **Memory信任标签** — 按来源标记agent记忆条目，防止记忆投毒攻击 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 24 | 🔄 Open | **子代理完成静默丢失** — 超时后无重试、无通知、无自动重启 |
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | 22 | 🔄 Open | **🚨 网关内存泄漏** — RSS从350MB增长至15.5GB，触发OOM崩溃循环 |
| [#80319](https://github.com/openclaw/openclaw/issues/80319) | 17 | 🔄 Open | **QA工具默认套件混淆** — Codex原生工具与OpenClaw动态工具对比验证问题 |

### 热点分析
- **消息丢失**是最大痛点：#116277、#44925、#92076、#84583等多个Issue指向子代理/会话完成交付链路的可靠性问题
- **内存泄漏**（#91588、#87109）持续影响生产环境，RSS无界增长导致OOM
- **安全治理**需求上升：#7707提出记忆来源信任标签，反映用户对AI记忆污染攻击的担忧

---

## 5. Bug 与稳定性

### P0 严重问题

| Issue | 描述 | Fix状态 |
|-------|------|---------|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | 网关RSS从350MB增长至15.5GB，OOM崩溃循环 | ⚠️ 无明确fix PR |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | 升级到2026.7.1后gateway启动失败 | ⚠️ 需更多证据 |
| [#112395](https://github.com/openclaw/openclaw/issues/112395) | 从6.11升级到7.1后migration预检失败，表为空 | ⚠️ 无明确fix PR |

### P1 重要问题

| Issue | 描述 | Fix状态 |
|-------|------|---------|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | DeepSeek v4 Flash静默失败 | ✅ 已关闭 |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 子代理完成静默丢失，无重试 | ⚠️ 需maintainer review |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | WhatsApp图片消息阻塞主通道3分钟 | ⚠️ 无明确fix PR |
| [#86215](https://github.com/openclaw/openclaw/issues/86215) | Codex OAuth刷新失败导致agent挂起数小时 | ⚠️ 需maintainer review |
| [#106231](https://github.com/openclaw/openclaw/issues/106231) | 循环检测阻断exec但不终止卡住的agent run | ⚠️ 无明确fix PR |
| [#103231](https://github.com/openclaw/openclaw/issues/103231) | Claude CLI会话`ownsNativeCompaction`假设错误 | 🔄 PR #120496待proof |
| [#118923](https://github.com/openclaw/openclaw/issues/118923) | 安全压缩重试循环：24次尝试无熔断 | ✅ 已关闭 |

### 回归问题
- [#38327](https://github.com/openclaw/openclaw/issues/38327)：2026.3.2更新后embedded agent失败
- [#116022](https://github.com/openclaw/openclaw/issues/116022)：beta.5 `/new`重用stable session ID

---

## 6. 功能请求与路线图信号

| Issue | 需求 | PR关联 | 版本可能性 |
|-------|------|--------|-----------|
| [#10687](https://github.com/openclaw/openclaw/issues/10687) | 动态模型发现（OpenRouter等） | #120361部分覆盖 | 中期 |
| [#13219](https://github.com/openclaw/openclaw/issues/13219) | 按模型用量日志/成本追踪 | 无直接PR | 需评估 |
| [#52640](https://github.com/openclaw/openclaw/issues/52640) | 长时间channel会话的状态面 | 无直接PR | 长期 |
| [#73537](https://github.com/openclaw/openclaw/issues/73537) | 发布稳定性标签 | 无直接PR | 需评估 |
| [#75947](https://github.com/openclaw/openclaw/issues/75947) | UI可用性重新设计 | 无直接PR | 长期 |
| [#8299](https://github.com/openclaw/openclaw/issues/8299) | 抑制子agent announce | 无直接PR | 需评估 |

### 路线图信号
- **Code Mode可追溯性**：多个PR（#120361、#119892、#120821、#120823、#120818）围绕Code Mode证据保留、审计追溯展开，表明这是当前重点方向
- **子代理路由改进**：#101248提出native `announceTarget`，解决编排拓扑中子代理完成的内部传递问题
- **设备配对简化**：#120768提出"一键粘贴"设备配对流程
- **Memory治理**：#7707的信任标签需求反映社区对AI记忆安全的关注度提升

---

## 7. 用户反馈摘要

### 核心痛点
1. **消息静默丢失**：多个生产场景（Telegram、WhatsApp、Feishu、Slack）报告子代理完成或消息未送达，用户感知为"无输出、无推送、无错误上报"
2. **内存泄漏**：长期运行的gateway RSS无界增长，最终OOM被系统杀死，触发反复重启循环
3. **会话状态恢复**：`/new`命令无法恢复retired绑定、compaction重试无熔断、session transcript链断裂
4. **模型provider可靠性**：DeepSeek静默失败、OAuth刷新超时、Codex app-server mid-turn关闭

### 满意点
- 安全边界加固收到正面反馈（连续版本聚焦此方向）
- `openclaw doctor`诊断工具持续改进
- TUI/CLI用户体验持续迭代（#120664 `openclaw resume`）

### 不满意点
- UI配置页"难以阅读、导航和理解"（#75947）
- Cron任务失败静默，缺乏明确告警（#87109、#84583）
- 跨平台一致性：Windows环境变量大小写问题（#120802）

---

## 8. 待处理积压

### ⚠️ 需维护者关注

| Issue/PR | 类型 | 状态 | 风险提示 |
|----------|------|------|----------|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | P0 Bug | 32天未明确fix | 内存泄漏无根治方案，影响生产稳定性 |
| [#103231](https://github.com/openclaw/openclaw/issues/103231) | P1 Bug | PR #120496待proof | Claude CLI压缩逻辑缺陷，影响长会话 |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | P0 Bug | 需更多repro证据 | 2026.7.1升级阻断，影响beta用户 |
| [#112395](https://github.com/openclaw/openclaw/issues/112395) | P0 Bug | 无明确fix | 从6.11升级后migration预检失败 |
| [#109145](https://github.com/openclaw/openclaw/issues/109145) | P1 Bug | 无明确fix | HTTP server监听但不接受连接 |
| [#80319](https://github.com/openclaw/openclaw/issues/80319) | P2 QA | 需maintainer review | QA套件设计问题，可能误导release判断 |
| [#114154](https://github.com/openclaw/openclaw/issues/114154) | P2 Bug | 无明确fix | bundle-mcp工具通过策略但未注册 |

---

**报告生成时间**：2026-08-09  
**数据周期**：过去24小时  
**分析师**：Agnes (Sapiens AI)

---

## 横向生态对比



# AI 智能体开源生态横向对比分析
**日期：2026-08-09 | 分析师：Agnes (Sapiens AI)**

---

## 1. 生态全景

2026年Q3，个人AI助手开源生态呈现**"头部密集迭代、安全焦虑凸显、渠道战争白热化"**三大特征。OpenClaw、CoPaw、ZeroClaw、Hermes Agent、IronClaw、NanoClaw六个主力项目保持日更节奏，累计处理超过1200条Issue与PR，反映出社区对生产级稳定性的强烈诉求。安全与权限控制成为跨项目共性痛点——Forbidden路径绕过、审批响应越权、凭据泄露等P1级漏洞集中暴露，标志着生态从功能扩张期转入**安全加固与可靠性攻坚期**。

---

## 2. 各项目活跃度对比

| 项目 | Issues | PRs | 发布 | 健康度 | 核心状态 |
|------|--------|-----|------|--------|----------|
| **OpenClaw** | 500 | 500 | v2026.6.33/34 | 🟢 极高 | 安全加固+稳定性双轨攻坚 |
| **CoPaw** | 19 | 50 | — | 🟢 高 | Scroll重构+桌面端优化 |
| **ZeroClaw** | 50 | 50 | — | 🟡 中 | P1安全漏洞集中暴露期 |
| **Hermes Agent** | 50 | 50 | — | 🟡 中 | 桌面端更新信任危机 |
| **IronClaw** | 30 | 50 | — | 🟢 高 | Reborn架构冲刺 |
| **NanoClaw** | 8 | 6 | — | 🟢 高 | 渠道扩展+修复 |
| **NanoBot** | 5 | 9 | — | 🟢 高 | 可观测性建设 |
| **LobsterAI** | 1 | 3 | — | 🟡 中 | 性能优化+网关集成 |
| **Moltis** | 2 | 1 | — | 🟡 中 | 容器兼容性修复 |
| **PicoClaw** | 3 | 4 | — | 🟡 中 | 多渠道协议扩展 |
| **NullClaw** | 0 | 0 | — | ⚪ 停滞 | 无活动 |
| **ZeptoClaw** | 0 | 0 | — | ⚪ 停滞 | 无活动 |

---

## 3. OpenClaw 在生态中的定位

**优势**：
- **吞吐量最高**：单日500条Issue+500条PR，是CoPaw的26倍、ZeroClaw的10倍
- **版本节奏最快**：24小时内发布两个版本，聚焦安全边界（sandboxed浏览器、可信DNS、OAuth限流）
- **生态覆盖最广**：Telegram/Discord/Slack/WhatsApp/Feishu全渠道支持，子代理路由、Code Mode追溯等前沿功能持续投入

**技术路线差异**：
| 维度 | OpenClaw | 竞品共性 |
|------|----------|----------|
| 架构 | 网关+子代理路由 + Sandbox隔离 | ZeroClaw/SOP自动化、IronClaw/Reborn重构 |
| 安全 | 浏览器路由+凭证脱敏+响应限流 | Hermes/Skill Guard、ZeroClaw/Forbidden路径 |
| 治理 | Memory信任标签、cron会话归档 | NanoBot/token追踪、CoPaw/Scroll上下文 |

**社区规模**：OpenClaw Issue评论数最高达179条（DeepSeek静默失败），显著高于NanoBot（13条）、Hermes（6条），反映其用户基数与生产负载最大。

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **MCP稳定性** | NanoBot、ZeroClaw、NanoClaw、Hermes Agent | MCP连接失败导致进程崩溃（anyio cancel scope跨任务）、僵尸进程积累、冷启动300s超时 |
| **Token/成本可观测** | NanoBot、OpenClaw、IronClaw、ZeroClaw | 细粒度消耗追踪、Anthropic成本归零、多别名查询失效、Token估算偏差 |
| **渠道体验** | ZeroClaw、NanoClaw、CoPaw、Hermes Agent | 审批响应越权（任意成员可接受）、消息静默丢失、富文本渲染、进度反馈 |
| **权限/安全边界** | ZeroClaw、Hermes Agent、OpenClaw、IronClaw | Forbidden路径绕过、Skill Guard绕过、凭据泄露（ANSI转义序列）、安全层未接入生产路径 |
| **会话/上下文管理** | OpenClaw、CoPaw、Hermes Agent、ZeroClaw | 子代理完成丢失、上下文压缩清除人类历史、Scroll重构、SOP无人执行 |
| **桌面端稳定性** | Hermes Agent、CoPaw、OpenClaw | Windows/macOS更新损坏安装、PATH识别失败、NSIS进程占用 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 架构差异 |
|------|----------|----------|----------|
| **OpenClaw** | 全渠道网关+子代理路由+Sandbox安全 | 生产级多代理编排用户 | 网关中心化架构，强调边界隔离 |
| **CoPaw** | Scroll上下文协议+AgentScope集成 | 国内开发者（火山/小米API） | 上下文收敛设计，对齐AgentScope 2.0 |
| **ZeroClaw** | SOP自动化+网络守卫 | 企业级自动化工作流 | Rust原生，强调配置安全与审计 |
| **Hermes Agent** | Skill Guard+会话写入策略 | 隐私敏感用户 | fail-closed策略，v0.20安全强化 |
| **IronClaw** | Reborn架构+ProductAdapter | 架构重构追求者 | 契约驱动重构，Web Debug Inspector |
| **NanoClaw** | MCP生态扩展（Strava/远程MCP） | 第三方服务集成用户 | ChannelAdapter v2，插件化渠道 |
| **NanoBot** | 可观测性+临时会话 | 调试/实验型用户 | 轻量级，token诊断优先 |
| **LobsterAI** | LiteLLM网关+SQLite性能 | 多LLM统一接入用户 | 写入优化（debounce+批量事务） |
| **Moltis** | 容器沙盒兼容性 | Docker/Apple Container用户 | 多运行时文件系统回退 |
| **PicoClaw** | 去中心化协议（Simplex/IRC） | 隐私通信用户 | 多渠道协议扩展 |

---

## 6. 社区热度与成熟度

```
快速迭代层（日更节奏，功能扩张）
├── OpenClaw     ████████████████████ 极高
├── CoPaw        ████████████████     高
├── ZeroClaw     ████████████████     高（但安全漏洞集中）
├── IronClaw     ██████████████       高（架构冲刺期）
└── NanoClaw     ███████████          高（渠道扩展）

质量巩固层（修复驱动，稳定性优先）
├── Hermes Agent ██████████           中（桌面端信任危机）
├── NanoBot      █████████            中（可观测性建设）
├── LobsterAI    ███████              中（性能优化）
└── Moltis       ██████               中（容器兼容）

扩展探索层（低频，方向验证）
└── PicoClaw     █████                低（协议扩展）

停滞层
├── NullClaw     █                    无活动
└── ZeptoClaw    █                    无活动
```

**判断**：OpenClaw/CoPaw/IronClaw处于快速迭代期；ZeroClaw/Hermes Agent因P1安全漏洞集中暴露进入**质量巩固期**；NanoBot/LobsterAI/Moltis在修复与技术债清理；PicoClaw探索差异化协议。

---

## 7. 值得关注的趋势信号

### 信号一：安全从"功能属性"变为"核心产品力"
- **现象**：ZeroClaw单日新增13个P1安全漏洞（forbidden_paths失效、审批任意成员响应、凭据泄露），Hermes Agent skill guard绕过，IronClaw安全层未接入生产路径
- **趋势**：社区对AI agent的权限边界、凭据安全、审批信任链关注度空前提升，**defense-in-depth** 成为分水岭
- **建议**：开发者应将安全审计纳入CI门禁，公开安全响应SLA

### 信号二：MCP生态从"可用"走向"可靠"
- **现象**：NanoBot anyio cancel scope崩溃、ZeroClaw僵尸进程、Hermes Agent 300s冷启动超时、OpenClaw子代理消息丢失
- **趋势**：MCP集成从功能拼凑转向**连接隔离、失败降级、资源回收**的工程化能力
- **建议**：优先实现MCP连接池与超时熔断，避免级联崩溃

### 信号三：上下文管理成为性能瓶颈
- **现象**：CoPaw Scroll重构、Hermes Agent压缩清除历史、NanoBot token不可见、OpenClaw compaction重试无熔断
- **趋势**：长会话下的**上下文预算控制、压缩可追溯性、记忆治理**成为核心命题
- **建议**：设计显式上下文协议（如Scroll），提供压缩审计与预算估算

### 信号四：桌面端体验是用户信任的关键触点
- **现象**：Hermes Agent Windows/macOS双平台更新损坏、CoPaw Homebrew PATH缺失、OpenClaw暗色模式闪烁
- **趋势**：CLI能力趋同后，**桌面端稳定性**成为用户留存决定性因素
- **建议**：建立跨平台更新自愈机制，增加安装诊断工具

### 信号五：渠道集成从"覆盖数量"转向"交互质量"
- **现象**：Telegram富渲染、Slack渐进预览、Mattermost企业支持、审批体验优化
- **趋势**：用户不再满足于"消息可达"，追求**富媒体、进度反馈、人机协作流程**
- **建议**：优先优化高频渠道（Telegram/Slack）的交互细节，而非盲目扩展新渠道

---

**总结**：2026年Q3的AI智能体开源生态正处于**从功能竞赛向工程成熟度转型**的关键阶段。OpenClaw凭借高吞吐保持引领，但安全漏洞集中暴露的ZeroClaw、架构重构的IronClaw、上下文创新的CoPaw构成有力竞争。对开发者而言，MCP可靠性、上下文治理、桌面端稳定性、安全边界将是未来6-12个月的核心投资方向。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目动态日报

**日期：2026-08-09** | 数据来源：github.com/HKUDS/nanobot

---

## 1. 今日速览

过去24小时 NanoBot 项目保持较高活跃度：共新增 **5 条 Issues**，PR 更新 **9 条**（4 条已合并/关闭，5 条待合并）。今日无新版本发布。社区在 **token 消耗追踪** 和 **MCP 稳定性** 两个方向讨论热烈，同时一个关于 anyio cancel scope 跨任务崩溃的高严重性 Bug 引起关注。整体项目健康度良好，代码清理与调试能力建设持续推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR（4 条）

| PR | 类型 | 作者 | 说明 |
|----|------|------|------|
| [#5293](https://github.com/HKUDS/nanobot/pull/5293) | feat | kuaijiemei | 新增 per-iteration token 诊断日志，直接回应 #5266 的 token 消耗追踪需求 |
| [#5252](https://github.com/HKUDS/nanobot/pull/5252) | feat | Re-bin | 新增 Temporary Chat 模式，支持多轮临时对话且不持久化存储 |
| [#5296](https://github.com/HKUDS/nanobot/pull/5296) | refactor | chengyongru | 清理 19 个死代码单元及 11 个孤立测试桩，降低维护负担 |
| [#5294](https://github.com/HKUDS/nanobot/pull/5294) | fix | chengyongru | 修复 WebUI 图片 hover 缩放导致边缘被裁剪的 UI 回归问题 |

**推进评估：** 今日合并主要集中在可观测性增强（token 诊断）、功能扩展（临时会话）和技术债务清理（死代码移除），未涉及核心架构变更，为下一版本的功能迭代奠定了较好的代码基础。

### 待合并的重要 PR（5 条）

- **#5271** [P0] 修复后台任务保存覆盖 session 数据的问题，涉及并发安全性
- **#5206** 修复流式响应被重复记录两次的日志冗余问题
- **#5292** 修复 Matrix 平台 room-level 消息未建立 reply 引用的问题
- **#5299** 在 WebUI 展示近期 token 使用详情（与 #5293 配套）
- **#4276** 添加 model-agnostic computer use 工具（长时间未合待 review）

---

## 4. 社区热点

### 🔥 讨论最活跃的 Issue

**#5266 - Logs about token consumption (too many tokens are burned)**
- 评论：13 条 | 创建者：knoppix2 | [链接](https://github.com/HKUDS/nanobot/issues/5266)
- **核心诉求：** 用户观察到 nanobot 在 2 小时内消耗上百万 token 却无明显活动，希望日志能追踪每次 API 调用的具体 token 消耗，便于定位异常。
- **关联 PR：** #5293（已合并，提供 per-iteration 诊断）和 #5299（待合并，展示近期 token 详情）正在直接回应此需求。

**#5300 - MCP连接失败未隔离+anyio cancel scope跨任务崩溃**
- 评论：0 条（新提出，待跟进）| 创建者：sunboy0523 | [链接](https://github.com/HKUDS/nanobot/issues/5300)
- **核心诉求：** 远程 MCP 返回 HTTP 530 时，nanobot 的 MCP 客户端触发了 anyio cancel scope 跨任务退出错误，导致网关进程崩溃、任务泄漏、CPU 飙升。这是一个高严重性稳定性问题，需紧急修复。

### 其他值得关注的 Issue

- **#5297** - MCP OAuth 网页授权需求，反映用户希望扩展认证型 MCP 工具集成 [链接](https://github.com/HKUDS/nanobot/issues/5297)
- **#5298** - 大型 MCP tool sets 的 schema 预算优化建议 [链接](https://github.com/HKUDS/nanobot/issues/5298)

---

## 5. Bug 与稳定性

| 严重程度 | Issue/PR | 描述 | Fix PR |
|----------|----------|------|--------|
| 🔴 高 | [#5300](https://github.com/HKUDS/nanobot/issues/5300) | MCP 异常导致 anyio cancel scope 跨任务崩溃，网关进程挂死/卡死，任务泄漏引发 CPU 飙升 | 暂无 |
| 🟠 中 | [#5295](https://github.com/HKUDS/nanobot/issues/5295) | Docker Compose 部署时 entrypoint.sh 权限不足导致 gateway 启动失败 | 暂无 |
| 🟡 低 | [#5294](https://github.com/HKUDS/nanobot/pull/5294) | WebUI 图片 hover 缩放导致边缘被容器裁剪 | ✅ #5294 已修复 |

**稳定性评估：** 今日发现两个未修复的 Bug，其中 #5300 涉及异步任务隔离和异常处理路径的深层问题，影响生产环境稳定性，建议优先处理。#5295 为部署配置问题，可通过文档更新或权限修复快速解决。

---

## 6. 功能请求与路线图信号

| 需求 | Issue | 关联 PR | 纳入可能性 |
|------|-------|---------|-----------|
| Token 消耗详细日志与追踪 | #5266 | #5293 (已合), #5299 (待合) | ✅ 已在实现中 |
| MCP OAuth 网页授权支持 | #5297 | 无 | 需评估，与 #5298 配套 |
| 大型 MCP tool sets schema 预算优化 | #5298 | 无 | 可能纳入下一版本，涉及上下文成本控制 |
| Temporary Chat 模式 | — | #5252 (已合) | ✅ 已完成 |
| Computer Use 工具 | — | #4276 (待合) | 长期待合并，需 review |

**路线图信号：** 项目当前聚焦于 **可观测性建设**（token 追踪）、**稳定性加固**（MCP 异常隔离）和 **用户体验优化**（临时会话、UI 修复），功能拓展节奏稳健。

---

## 7. 用户反馈摘要

### 痛点
- **Token 消耗不可见：** #5266 中用户反馈 nanobot 在无活动状态下 2 小时消耗百万 token，缺乏细粒度追踪能力，难以定位异常消耗源头。
- **MCP 稳定性差：** #5300 反映远程 MCP 服务不可达时，nanobot 的异常处理机制存在缺陷，导致级联崩溃和资源泄漏。
- **部署体验：** #5295 用户反映 Docker Compose 部署时遇到权限问题，文档或镜像构建流程需优化。

### 满意点
- Temporary Chat 模式（#5252）为需要快速试用的用户提供了轻量级入口。
- Token 诊断能力（#5293）的实现在逐步回应社区长期关注的可观测性需求。
- 死代码清理（#5296）体现了维护者对代码质量的重视。

---

## 8. 待处理积压

| 类型 | ID | 描述 | 创建时间 | 建议 |
|------|-----|------|----------|------|
| Bug | [#5300](https://github.com/HKUDS/nanobot/issues/5300) | MCP 连接失败导致 anyio cancel scope 崩溃 | 2026-08-08 | 紧急跟进，涉及生产稳定性 |
| Bug | [#5295](https://github.com/HKUDS/nanobot/issues/5295) | Docker Compose 部署 entrypoint 权限问题 | 2026-08-08 | 快速修复，影响新手部署体验 |
| Feature | [#4276](https://github.com/HKUDS/nanobot/pull/4276) | Computer Use 工具（model-agnostic） | 2026-06-10 | 已开放近 2 个月，需安排 review |
| Enhancement | [#5271](https://github.com/HKUDS/nanobot/pull/5271) | P0: 修复 session 数据覆盖 bug | 2026-08-06 | 待合并，影响数据一致性 |
| Enhancement | [#5298](https://github.com/HKUDS/nanobot/issues/5298) | 大型 MCP tool sets schema 预算优化 | 2026-08-08 | 需评估实现方案 |

---

**总结：** NanoBot 今日项目运转正常，代码清理和可观测性建设持续推进。需重点关注 #5300 的稳定性 Bug 和 #5271 的 P0 修复，确保生产环境可靠。长期积压的 #4276 建议尽快安排 review。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-09

## 1. 今日速览

Hermes Agent 今日保持**高活跃度**，过去24小时共产生 50 条 Issue 更新（新开/活跃 39 条，已关闭 11 条）和 50 条 PR 更新（待合并 43 条，已合并/关闭 7 条）。项目无新版本发布，但多个关键修复 PR 已进入主分支，涉及 Windows 桌面端安装修复、FTS 搜索稳定性、xAI OAuth 自动刷新等核心痛点。安全与隐私类 Issue（#78515、#81012、#80966）持续引发关注，表明社区对 skill 注入和凭据脱敏机制的健康度审查正在深化。

---

## 2. 版本发布

> 过去24小时无新版本发布。

---

## 3. 项目进展 — 今日已关闭/合并的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#82158](https://github.com/NousResearch/hermes-agent/pull/82158) | Bug Fix | 修复 `venv-blocker` 命令行截断导致 Desktop 更新永久卡死的问题（自星进程误报为冲突进程） |
| [#79723](https://github.com/NousResearch/hermes-agent/pull/79723) | Feature/Migration | 完成 v0.20 session write-policy 迁移（29个路径，27个有效变更），fail-closed 策略落地 |
| [#80943](https://github.com/NousResearch/hermes-agent/pull/80943) | Feature | 在运行时传播并强制执行 session write policy，覆盖 Copilot ACP 子进程 |

**项目整体推进评估**：今日主要推进了**Windows 桌面端安装链路的自愈能力**和**会话写入策略的运行时强制**，两者均是 v0.20 发布周期的关键里程碑。C19 契约 9/9 测试通过，表明 session 安全边界的工程化进度稳健。

---

## 4. 社区热点 — 评论数最多的 Issues

| Issue | 类型 | 评论数 | 核心议题 |
|---|---|---|---|
| [#78515](https://github.com/NousResearch/hermes-agent/issues/78515) | Security | 6 | `background_review` 默认绕过 Skills Guard 内容扫描，skill 被注入每场会话 system prompt |
| [#40801](https://github.com/NousResearch/hermes-agent/issues/40801) | Bug (P2) | 6 | Cron script-path guard 错误拒绝来自 default-profile 的合法脚本引用（#32091 的反向回归） |
| [#81969](https://github.com/NousResearch/hermes-agent/issues/81969) | Bug (P1) | 6 | Windows 桌面端每次更新均损坏安装，用户信任度显著下降 |
| [#75778](https://github.com/NousResearch/hermes-agent/issues/75778) | Bug (P1) | 6 | macOS Desktop 更新产生重复 `hermes-setup` 进程，失败窗口掩盖真实运行实例 |
| [#70846](https://github.com/NousResearch/hermes-agent/issues/70846) | Bug (P2) | 5 | Agent 压缩上下文时同时清除人类侧消息历史，无法回溯 |
| [#41225](https://github.com/NousResearch/hermes-agent/issues/41225) | Bug (P2) | 4 | `terminal(background=true)` 启动的后台进程在 agent `release()` 时被 SIGTERM 杀死 |
| [#39245](https://github.com/NousResearch/hermes-agent/issues/39245) | Bug (P2) | 4 | ACP `prompt` 调用在 `usage_update` 未返回时挂起，不返回 `end_turn` |
| [#73624](https://github.com/NousResearch/hermes-agent/issues/73624) | Bug (P2) | 4 | `_estimate_msg_budget_tokens` 将已归档 reasoning 计费入压缩尾预算，浪费 19-24% budget |

**热点分析**：社区最关切的是**桌面端更新稳定性**（Windows/macOS 双平台均有 P1 Bug）和**安全边界的隐式绕过**（#78515）。后台进程生命周期（#41225）和上下文压缩副作用（#70846）是高频长期痛点，已有多个相关 PR 但未闭环。

---

## 5. Bug 与稳定性

### P0 / P1 严重级别

| Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|
| [#81969](https://github.com/NousResearch/hermes-agent/issues/81969) | Windows 桌面端 `hermes update` 持续损坏安装 | OPEN | [#82143](https://github.com/NousResearch/hermes-agent/pull/82143)（已 OPEN，待合并） |
| [#75778](https://github.com/NousResearch/hermes-agent/issues/75778) | macOS 桌面更新产生重复 `hermes-setup` 进程 | OPEN | 暂无 |
| [#81995](https://github.com/NousResearch/hermes-agent/issues/81995) | 空闲杀死的 stdio MCP 冷启动时，挂起的 tool call 等待完整 300s 超时 | OPEN | 暂无 |

### P2 严重级别

| Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|
| [#70846](https://github.com/NousResearch/hermes-agent/issues/70846) | 上下文压缩同时清除人类可访问的历史消息 | OPEN | 暂无 |
| [#41225](https://github.com/NousResearch/hermes-agent/issues/41225) | 后台 terminal 进程在 agent release 时被 SIGTERM 杀死 | OPEN | 暂无 |
| [#39245](https://github.com/NousResearch/hermes-agent/issues/39245) | ACP prompt 在 usage_update 未返回时挂起 | OPEN | 暂无 |
| [#63386](https://github.com/NousResearch/hermes-agent/issues/63386) | macOS `state.db` FTS 索引损坏，`hermes doctor` 报 write-health 失败 | OPEN | [#82152](https://github.com/NousResearch/hermes-agent/pull/82152)（salvage #79285，已 OPEN） |
| [#81162](https://github.com/NousResearch/hermes-agent/issues/81162) | Auto voice reply 同步阻塞文本响应，慢 TTS 后端体验差 | OPEN | 暂无 |
| [#81430](https://github.com/NousResearch/hermes-agent/issues/81430) | `hermes memory status` 误报 "disabled"，实际 memory 正常工作 | OPEN | 暂无 |
| [#82052](https://github.com/NousResearch/hermes-agent/issues/82052) | xAI OAuth 403 被误判为非可重试错误 | OPEN | [#82153](https://github.com/NousResearch/hermes-agent/pull/82153)（已 OPEN） |

### P3 严重级别

| Issue | 描述 | 状态 |
|---|---|---|
| [#43997](https://github.com/NousResearch/hermes-agent/issues/43997) | npm 11 `allowScripts` 警告影响 `hermes update` | OPEN |
| [#62171](https://github.com/NousResearch/hermes-agent/issues/62171) | npm 12 Linux 默认策略破坏 Hermes Desktop 更新 | OPEN |
| [#82074](https://github.com/NousResearch/hermes-agent/issues/82074) | Podman+SELinux 下 skills 目录挂载无 `:z` 标签导致容器内不可访问 | OPEN |
| [#81012](https://github.com/NousResearch/hermes-agent/issues/81012) | ANSI CSI/SGR 序列绕过 `redact` 前缀掩码，API key 泄露 | OPEN |
| [#80966](https://github.com/NousResearch/hermes-agent/issues/80966) | 不含 secret 关键字的 env key（如 `SPOTIFY_CLIENT_ID`）全部穿透脱敏 | OPEN |

---

## 6. 功能请求与路线图信号

| Issue | 类型 | 描述 | 关联 PR |
|---|---|---|---|
| [#78307](https://github.com/NousResearch/hermes-agent/issues/78307) | Feature | 为内置有界 memory store（`MEMORY.md`/`USER.md`）提供生命周期管理 UX：健康检查、去重、冲突检测、恢复清理 | 暂无 |
| [#35573](https://github.com/NousResearch/hermes-agent/issues/35573) | RFC | ToolCallStormBreaker — 抑制模型重复调用相同工具的循环 | 暂无 |
| [#49103](https://github.com/NousResearch/hermes-agent/issues/49103) | Feature | Cmd+K 统一内容搜索：跨文件、会话历史、已安装 skills 的全局搜索 | 暂无 |
| [#14859](https://github.com/NousResearch/hermes-agent/issues/14859) | Feature | CLI/TUI 状态栏显示当前会话标题 | ✅ 已关闭 |
| [#82165](https://github.com/NousResearch/hermes-agent/issues/82165) | Feature | Desktop 应用新增西班牙语（es）本地化 | 暂无 |
| [#82157](https://github.com/NousResearch/hermes-agent/pull/82157) | Feature | `delegate_task()` 新增 `child_memory` 参数，实现子 agent 独立 memory 和权限边界 | OPEN，待合并 |
| [#81709](https://github.com/NousResearch/hermes-agent/pull/81709) | Feature | Telegram 双向上下文 reaction（用户可对 Hermes 消息添加标准 reaction） | OPEN，待合并 |
| [#81439](https://github.com/NousResearch/hermes-agent/pull/81439) | Feature | 可配置的面向用户的时间戳显示（`display.timestamps`/`display.timestamp_format`） | OPEN，待合并 |
| [#80475](https://github.com/NousResearch/hermes-agent/pull/80475) | Feature | MCP 服务器确定性 record/replay fixture（`hermes mcp fixtures record/replay`） | OPEN，待合并 |
| [#81929](https://github.com/NousResearch/hermes-agent/pull/81929) | Perf | 为 skill 消息声明缓存边界，减少 webhook/cron 重复扩展 | OPEN，待合并 |

**路线图判断**：`child_memory` 权限隔离（#82157）和 skill 缓存优化（#81929）与当前 v0.20 session write-policy 方向一致，极可能纳入下一版本。ToolCallStormBreaker（#35573）为社区高频痛点，有望作为独立 RFC 推进。

---

## 7. 用户反馈摘要

**强烈不满：**
- Windows 用户（[#81969](https://github.com/NousResearch/hermes-agent/issues/81969)）反复反馈"每次更新都破坏一切"，明确指出缺乏生产环境测试，对产品质量信任度下降。
- macOS 用户（[#75778](https://github.com/NousResearch/hermes-agent/issues/75778)）遇到更新后双重进程冲突，失败窗口掩盖真实状态，排查困难。

**高价值反馈：**
- [#70846](https://github.com/NousResearch/hermes-agent/issues/70846)（1👍）：用户需要长对话后回溯历史记录，压缩机制的副作用直接破坏使用体验。
- [#41225](https://github.com/NousResearch/hermes-agent/issues/41225)：后台终端进程生命周期管理是长期痛点，涉及 session 结束、超时、压缩、错误恢复等多个生命周期节点。
- [#73624](https://github.com/NousResearch/hermes-agent/issues/73624)：压缩预算估算浪费 19-24% 空间在已归档 reasoning 上，影响长会话的 token 效率。

**安全关切：**
- [#78515](https://github.com/NousResearch/hermes-agent/issues/78515) 和 [#81012](https://github.com/NousResearch/hermes-agent/issues/81012) 来自安全研究者（EvolveAegis、kshitijk4poor），指出 skill guard 绕过和 ANSI 转义序列泄露凭据的防御纵深问题，属 defense-in-depth 性质，非紧急但需重视。

---

## 8. 待处理积压 — 需维护者关注

| Issue/PR | 状态 | 风险说明 |
|---|---|---|
| [#81969](https://github.com/NousResearch/hermes-agent/issues/81969) / [#82143](https://github.com/NousResearch/hermes-agent/pull/82143) | Fix PR 已开但未合并 | Windows 桌面端更新链路的阻塞性 Bug，影响面广，建议优先合入 |
| [#75778](https://github.com/NousResearch/hermes-agent/issues/75778) | 无 Fix PR | macOS 桌面端双进程问题，P1 级别，尚无对应修复 |
| [#41225](https://github.com/NousResearch/hermes-agent/issues/41225) | 无 Fix PR | 后台进程 SIGTERM 生命周期问题，长期未解决，影响 terminal 工具使用者 |
| [#78515](https://github.com/NousResearch/hermes-agent/issues/78515) | 无 Fix PR | skill guard 绕过的安全隐患，来自外部安全审计，需决策是否默认开启 `background_review` 扫描 |
| [#39245](https://github.com/NousResearch/hermes-agent/issues/39245) | 无 Fix PR | ACP 协议挂起问题，影响集成调用方，P2 长期未响应 |
| [#57752](https://github.com/NousResearch/hermes-agent/issues/57752) | 无 Fix PR | Session DB auto-prune+VACUUM 默认关闭且无提示，长期导致 `state.db` 膨胀 |
| [#81995](https://github.com/NousResearch/hermes-agent/issues/81995) | 无 Fix PR | MCP stdio 冷启动 300s 无 fail-fast，对 MCP 工具依赖用户影响大 |

---

**项目健康度评分**：🟡 **中等偏上** — 活跃开发和维护修复（50 PR/天），但 P1 级桌面端更新问题在 Windows/macOS 双平台同时存在且修复进度不一，需优先闭环以恢复用户信任。安全类 Issue 持续涌入表明社区审查机制正在发挥作用。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报 — 2026-08-09

---

## 1. 今日速览

过去 24 小时，PicoClaw 社区保持中等活跃度：共 3 条 Issue 更新（2 条活跃、1 条已关闭），4 条 PR 处于待合并状态但暂无合并记录。项目未发布新版本。社区反馈集中在 IRC 消息长度支持、MCP 服务器的 OAuth 2.1 认证以及聊天界面性能问题，技术方向持续向多渠道协议扩展。整体项目健康度评估：**平稳**，维护者响应正常，但多个 PR 已进入 stale 状态需关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日无 PR 被合并，项目核心代码库暂无新增变更。

当前 4 条待合并 PR 涵盖以下方向：
- **WhatsApp 客户端兼容性修复**（#3320）— 解决 WhatsApp 服务端拒绝旧版客户端导致的连接断连问题，属于阻断性修复
- **Agent 前缀缓存优化**（#3321）— 改进动态上下文位置以提升 API 调用效率，属于性能优化
- **Deltachat 重构**（#3222）— 清理遗留代码，预计减少 200 行 LOC，改善代码可维护性
- **Simplex 通道支持**（#3193）— 新增去中心化即时通讯协议支持，扩展生态覆盖

---

## 4. 社区热点

| 类型 | 编号 | 主题 | 评论 | 热度分析 |
|------|------|------|------|----------|
| Issue | [#3287](https://github.com/sipeed/picoclaw/issues/3287) | IRC 长消息支持 | 4 条 | 最高 — 4 条评论且涉及 IRCv3 协议的核心使用场景 |
| Issue | [#3302](https://github.com/sipeed/picoclaw/issues/3302) | MCP 服务器 OAuth 2.1 支持 | 2 条 | 中等 — 与安全认证相关，关联已有 Issue #2546 |
| PR | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | Deltachat 重构 | — | 关注度高 — 代码量大（-200LOC），影响现有功能 |
| PR | [#3320](https://github.com/sipeed/picoclaw/pull/3320) | WhatsApp 客户端版本升级 | — | 紧急性高 — 修复阻断性 Bug |

**热点分析**：#3287 的 4 条评论表明社区对 IRC 协议支持有实际需求；#3302 与 #2546 存在关联，反映出用户对 MCP 生态认证标准化的期待。

---

## 5. Bug 与稳定性

| 严重程度 | 编号 | 描述 | 状态 | Fix PR |
|----------|------|------|------|--------|
| 🔴 高 | [#3292](https://github.com/sipeed/picoclaw/issues/3292) | 聊天界面输入框聚焦时 CPU 占用过高 | ✅ 已关闭 | — |
| 🟡 中 | [#3320](https://github.com/sipeed/picoclaw/pull/3320) | WhatsApp 客户端过期导致连接持续断开 | 🔄 待合并 | PR #3320 |

**说明**：
- **#3292** 已于今日关闭，但未见关联 Fix PR，建议确认修复方式是否已合入主分支
- **#3320** 提供明确修复方案，待维护者审查合并

---

## 6. 功能请求与路线图信号

| 编号 | 请求 | 类型 | 路线图信号 |
|------|------|------|------------|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) | IRC 长消息自动重组 | Feature | 🟡 增强 — 符合多渠道协议完善方向 |
| [#3302](https://github.com/sipeed/picoclaw/issues/3302) | MCP 服务器 OAuth 2.1 支持 | Feature | 🟡 Nice-to-Have — 关联 #2546，安全需求明确 |
| [#3193](https://github.com/sipeed/picoclaw/pull/3193) | Simplex 通道支持 | Feature | 🟢 新功能 — 扩展去中心化协议覆盖 |

**判断**：Simplex 通道（#3193）作为新增功能 PR，若通过审查有望纳入下一版本；OAuth 2.1 支持属于延续性增强，优先级中等。

---

## 7. 用户反馈摘要

**痛点**：
- **IRC 消息截断**：用户反映 PicoClaw 无法正确处理超过 512 字节的 IRC 消息，导致语义断裂（[#3287](https://github.com/sipeed/picoclaw/issues/3287)）
- **CPU 性能问题**：在 Firefox 中聚焦聊天输入框时出现明显 CPU 飙升，影响使用体验（[#3292](https://github.com/sipeed/picoclaw/issues/3292) ✅ 已解决）
- **WhatsApp 连接不稳定**：服务端版本更新导致客户端被拒绝，且无自动重连机制（[#3320](https://github.com/sipeed/picoclaw/pull/3320)）

**满意点**：
- Deltachat 重构获得认可，用户期待清理后的代码结构（[#3222](https://github.com/sipeed/picoclaw/pull/3222)）

---

## 8. 待处理积压

| 编号 | 类型 | 主题 | 创建日期 | 状态 | 风险 |
|------|------|------|----------|------|------|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) | Issue | IRC 长消息支持 | 2026-07-22 | stale | 中 |
| [#3302](https://github.com/sipeed/picoclaw/issues/3302) | Issue | MCP OAuth 2.1 | 2026-07-30 | 活跃 | 低 |
| [#3222](https://github.com/sipeed/picoclaw/pull/3222) | PR | Deltachat 重构 | 2026-07-03 | stale | 高 |
| [#3193](https://github.com/sipeed/picoclaw/pull/3193) | PR | Simplex 通道 | 2026-06-27 | stale | 中 |
| [#3320](https://github.com/sipeed/picoclaw/pull/3320) | PR | WhatsApp 修复 | 2026-08-07 | 活跃 | 低 |
| [#3321](https://github.com/sipeed/picoclaw/pull/3321) | PR | 前缀缓存优化 | 2026-08-07 | 活跃 | 低 |

**重点关注**：
- **#3222**（Deltachat 重构）已 stale 超 35 天，改动量大，需维护者优先审查
- **#3193**（Simplex）已 stale 超 42 天，新功能请求但无合并进展

---

**报告生成时间**：2026-08-09
**数据来源**：[sipeed/picoclaw](https://github.com/sipeed/picoclaw) GitHub API

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：2026-08-09 | 数据周期：2026-08-08 00:00 ~ 23:59 UTC**

---

## 1. 今日速览

过去24小时 NanoClaw 项目保持**高活跃度**：Issues 8条（新开5 / 关闭3），PRs 6条（待合并3 / 已合并3）。今日无新版本发布，但合并了两项重要功能（Strava MCP集成、远程MCP服务器支持）及两个关键Bug修复。项目整体健康度良好，社区贡献者积极参与渠道扩展与稳定性修复，Discord审批按钮的阻断性Bug已定位并进入修复流程。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR

| PR | 类型 | 作者 | 说明 |
|---|---|---|---|
| [#2777](https://github.com/nanocoai/nanoclaw/issues/2777) | Feature | clementdecoligny | **新增 `/add-strava` Skill**：集成官方 Strava MCP 端点，包含主机侧 OAuth 流程与自动刷新 Token 模块，扩展了健康/运动数据接入能力 |
| [#2776](https://github.com/nanocoai/nanoclaw/issues/2776) | Feature | clementdecoligny | **支持远程 HTTP/SSE MCP 服务器**：`McpServerConfig` 扩展为 Union 类型，新增 `McpServerRemoteConfig`，CLI 新增 `--type/--url/--header` 参数，大幅拓宽 MCP 接入场景 |
| [#3199](https://github.com/nanocoai/nanoclaw/issues/3199) | Feature | wakqasahmed | **Mattermost 渠道集成（v2）**：已合并，基于当前 `ChannelAdapter` 架构实现；已被 #3202 取代（见下） |

**进展评估**：今日 PR 合并聚焦于 **MCP 生态扩展**（Strava + 远程MCP）与**渠道覆盖**（Mattermost），表明项目正积极拓宽集成矩阵，为多用户 Agent 场景提供丰富工具链。

---

## 4. 社区热点

### 重点关注 Issue / PR

1. **[Discord 审批按钮完全失效](https://github.com/nanocoai/nanoclaw/issues/3201)** — #3201 [CLOSED]
   - owner 角色点击 Approve 无响应，审批请求全部被拒绝
   - 根因定位在 webhook custom_id 解析逻辑，[#3185](https://github.com/nanocoai/nanoclaw/pull/3185) 正在修复（strip `\n` 分隔符）
   - **影响**：阻断性 Bug，涉及 Discord 渠道核心交互流程

2. **[Docker 跨挂载文件系统数据库锁竞争](https://github.com/nanocoai/nanoclaw/issues/3177)** — #3177 [CLOSED]
   - SQLite DELETE journal mode 在 VirtioFS 下不传播，导致 29,000+ readonly 错误
   - 已修复，显著提升 Docker 部署稳定性

3. **[Mattermost 渠道集成](https://github.com/nanocoai/nanoclaw/issues/3202)** — #3202 [OPEN]
   - 取代 #3199，基于最新 v2 ChannelAdapter 架构重新实现
   - 社区对 Mattermost 支持需求强烈（原 #1379 长期跟进）

4. **[Telegram 原生富渲染](https://github.com/nanocoai/nanoclaw/pull/2877)** — #2877 [OPEN]
   - 利用 Bot API 10.1 `sendRichMessage` 提升消息展示体验，等待维护者 review

---

## 5. Bug 与稳定性

| 优先级 | Issue | 描述 | Fix PR |
|---|---|---|---|
| 🔴 高 | [#3201](https://github.com/nanocoai/nanoclaw/issues/3201) | Discord 审批按钮点击不注册，所有 Approve 被拒绝 | [#3185](https://github.com/nanocoai/nanoclaw/pull/3185) [OPEN] |
| 🔴 高 | [#3177](https://github.com/nanocoai/nanoclaw/issues/3177) | Docker 跨挂载文件系统 SQLite 锁竞争，29K+ readonly 错误 | ✅ 已关闭 |
| 🟡 中 | [#3206](https://github.com/nanocoai/nanoclaw/issues/3206) | Google Chat 等含路径分隔符的 messageId 导致附件静默丢弃 | — |
| 🟡 中 | [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) | codex provider 发出未声明的 `file` ProviderEvent，类型检查失败 + 图片静默丢失 | — |
| 🟡 中 | [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) | Signal 渠道图片/PDF 附件在 agent 容器内不可访问（长期未解决） | — |

**稳定性评估**：核心审批流与数据库锁问题已修复或修复中，但附件处理（Google Chat / Signal）和类型安全（codex provider）存在遗留问题，建议纳入下一优先级。

---

## 6. 功能请求与路线图信号

| Issue | 诉求 | 路线图判断 |
|---|---|---|
| [#3205](https://github.com/nanocoai/nanoclaw/issues/3205) | 持久化组级 OneCLI 密钥分配 | 涉及多用户架构核心设计分歧，短期内可能难有定论；与远程MCP支持（#2776）存在设计冲突，需架构层统一 |
| [#3204](https://github.com/nanocoai/nanoclaw/issues/3204) | `add-opencode` Skill 文档与 `cli-tools.json` 重构不匹配 | 属内部文档/技能漂移问题，应尽快修复以保持技能一致性 |
| [#2877](https://github.com/nanocoai/nanoclaw/pull/2877) | Telegram 富消息渲染 | 已 PR，符合渠道体验升级方向，预计纳入后续版本 |
| [#3202](https://github.com/nanocoai/nanoclaw/pull/3202) | Mattermost 渠道 | 已 PR，补齐主流企业通信平台覆盖 |

---

## 7. 用户反馈摘要

- **Discord 审批体验严重受损**：用户报告 owner role 无法通过按钮批准配置更新，审批卡片显示 "0 by [user]"，请求被自动拒绝——这是影响多用户协作流程的关键痛点（#3201）
- **Docker 部署稳定性亟待改善**：macOS/Linux Docker 环境下 SQLite 锁竞争导致大量 readonly 错误和间歇性投递失败，已影响生产稳定性（#3177）
- **附件处理能力不足**：Google Chat（路径分隔符过滤）和 Signal（容器内不可访问）两路渠道均存在附件静默丢失问题，用户无法有效传递图片/PDF（#3206, #2528）
- **MCP 生态扩展需求强烈**：Strava 集成与远程 MCP 服务器支持获得贡献者积极响应，用户期望更多第三方服务接入（#2777, #2776）
- **Signal 长期未解决**：#2528 已 open 超过 2 个月，附件问题持续影响 Signal 渠道用户

---

## 8. 待处理积压

| 类型 | 编号 | 标题 | 开放时长 | 建议 |
|---|---|---|---|---|
| 🐛 Bug | [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) | Signal 渠道图片/PDF 不可访问 | ~83 天 | 优先处理，影响企业用户 |
| 🐛 Bug | [#3206](https://github.com/nanocoai/nanoclaw/issues/3206) | Google Chat 附件静默丢弃 | 今日 | 与 #3185 类似的路径解析问题，建议同步修复 |
| 🐛 Bug | [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) | codex provider 类型检查失败 | 今日 | 合并前需修复，影响 `/add-codex` 流程 |
| 📝 文档 | [#3204](https://github.com/nanocoai/nanoclaw/issues/3204) | add-opencode 技能指令过时 | 今日 | 快速修复，避免技能漂移 |
| 💬 PR | [#3185](https://github.com/nanocoai/nanoclaw/pull/3185) | Discord custom_id 修复 | 5 天 | 阻断性 Bug 修复，建议优先合并 |
| 💬 PR | [#2877](https://github.com/nanocoai/nanoclaw/pull/2877) | Telegram 富渲染 | ~41 天 | 等待 review |
| 💬 PR | [#3202](https://github.com/nanocoai/nanoclaw/pull/3202) | Mattermost 集成 | 今日 | 合并后可扩展企业渠道覆盖 |
| 🏗 设计 | [#3205](https://github.com/nanocoai/nanoclaw/issues/3205) | OneCLI 密钥分配设计分歧 | 今日 | 需架构层决策 |

---

**项目健康度总结**：NanoClaw 在渠道扩展（Mattermost、Strava、远程MCP）方面进展积极，核心审批流与数据库锁问题已有效修复。当前主要风险点为**附件处理链路的系统性缺陷**（Google Chat、Signal）及**类型安全**（codex provider），建议在下个迭代中集中清理，同时尽快决策 OneCLI 密钥分配的架构方向。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw 项目日报 | 2026-08-09

## 1. 今日速览

IronClaw 项目在过去 24 小时内保持高活跃度：新增 30 个 Issue 更新（6 活跃/24 已关闭），50 个 PR 更新（18 待合并/32 已合并）。**Reborn 架构迁移取得关键进展**，24 个 Issue 集中关闭，涵盖 ProductAdapter 契约、WeChat 通道移植、记忆/工作区迁移、引擎驱动适配等核心模块。Web Debug Inspector 功能今日收尾并合并。项目整体处于 Reborn 集成冲刺阶段，架构重构与产品层开发同步推进。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 关键合并 PR

| PR | 内容 | 影响 |
|---|---|---|
| [#7171](https://github.com/nearai/ironclaw/pull/7171) | 修复 Skill 挂载后消失的 bug，改为 DB 驱动的统一挂载树 | 稳定技能系统 |
| [#7377](https://github.com/nearai/ironclaw/pull/7377) | 统一"运行以调用者身份执行"策略，完成多代理审计修复 | 安全与身份一致性 |
| [#6938](https://github.com/nearai/ironclaw/pull/6938) | 技能激活由模型决策替代关键词打分器 | 提升技能选择准确性 |
| [#7382](https://github.com/nearai/ironclaw/pull/7382) | 脚本化工具调用压力测试（#7360 Phase 1） | 增强稳定性保障 |
| [#7280](https://github.com/nearai/ironclaw/pull/7280) | Inspector 浏览器/安全/操作员覆盖测试 | 完善调试工具 |
| [#7393](https://github.com/nearai/ironclaw/pull/7393) | Core 层交付基准测试覆盖 | 性能监控 |
| [#7389](https://github.com/nearai/ironclaw/pull/7389) | 修复 Slack 交付验证 live-qa 失败 | 修复回归 |

### 待合并重点 PR

- [#7398](https://github.com/nearai/ironclaw/pull/7398) — **Web Push 通道**：将 Web 应用升级为正式通知渠道，支持 W3C Web Push 标准，与 Slack/Telegram 平齐
- [#7396](https://github.com/nearai/ironclaw/pull/7396) — **Slack 渐进预览**：新增 channel-neutral 预览契约，映射到 `chat.startStream/appendStream`
- [#7397](https://github.com/nearai/ironclaw/pull/7397) — **基于存在的共享会话**：Slack & Telegram 的共享对话能力，基于 #7377 的身份链路
- [#7395](https://github.com/nearai/ironclaw/pull/7395) — **修复 TOCTOU 竞态**：关闭 `claim_delivery_attempt_for_send` 的竞态条件与失败行重开逻辑
- [#7373](https://github.com/nearai/ironclaw/pull/7373) — **Gate 审计完整报告**：37 个架构测试门文件 + 80 个 CI 脚本的全面审计

---

## 4. 社区热点

| Issue/PR | 热度指标 | 关注点 |
|---|---|---|
| [#6989](https://github.com/nearai/ironclaw/issues/6989) | 5 评论，P1 Bug | Token 估算错误：`ModelWorkRequest::for_assistant` 使用 reference string 长度而非实际内容长度 |
| [#7391](https://github.com/nearai/ironclaw/issues/7391) | 新建，0 评论但关键 | `SafetyLayer::validate_input` / `scan_inbound_for_secrets` 在生产 Reborn turn 路径上**无调用者** |
| [#7360](https://github.com/nearai/ironclaw/issues/7360) | 2 评论，e2e-coverage | 扩展内置能力与持久化写入路径的压测覆盖，当前 mock LLM 不触发工具调用导致回归风险 |
| [#7392](https://github.com/nearai/ironclaw/issues/7392) | 新建，epic | 替换内置编码工具为 pinned `omp` 工具表面（来源：oh-my-pi） |
| [#7218](https://github.com/nearai/ironclaw/issues/7218) | 新建，epic | Web Debug Inspector 功能完整规划，支持 Prompt/Activity/Stats 三视图 |
| [#6939](https://github.com/nearai/ironclaw/issues/6939) | 2 评论，P2 | **迁移工具需求**：Hermes/Openclaw 用户反馈切换成本高，需保留配置与记忆 |

**热点分析**：安全相关 Issue #7391 和 #6989 直接涉及模型输入验证与 Token 计费准确性，可能影响生产环境；#6939 反映 legacy 用户迁移诉求，社区扩张的潜在阻力点。

---

## 5. Bug 与稳定性

| 问题 | 严重程度 | 状态 | 修复 PR |
|---|---|---|---|
| [#7391](https://github.com/nearai/ironclaw/issues/7391) | **高** — 安全层函数在生产路径缺失调用者 | OPEN，新建 | 暂无 |
| [#6989](https://github.com/nearai/ironclaw/issues/6989) | **中** — Token 估算偏差影响计费与配额 | OPEN | 暂无 |
| [#7389](https://github.com/nearai/ironclaw/pull/7389) | **中** — Slack 交付 live-qa 全量失败（#7157 合并后回归） | 已合并 | #7389 |
| [#7341](https://github.com/nearai/ironclaw/pull/7341) | **中** — WebUI 附件读取回归 | 已合并 | #7341 |
| [#7395](https://github.com/nearai/ironclaw/pull/7395) | **高** — 发送竞态条件（TOCTOU）导致交付丢失 | 待合并 | #7395 |
| [#7028](https://github.com/nearai/ironclaw/pull/7028) | **中** — 恢复中断交付时状态丢失 | 待合并 | #7028 |

**稳定性评估**：今日合并了 3 个关键 Bug 修复（#7389、#7341、#6938），但 #7391（安全层未接入）和 #7395（TOCTOU 竞态）仍是待处理的稳定性隐患。

---

## 6. 功能请求与路线图信号

| 需求 | 来源 | 路线图匹配 | 预期版本 |
|---|---|---|---|
| Web Push 通知渠道 | [#7398](https://github.com/nearai/ironclaw/pull/7398) | Reborn 通道扩展 | 近期 |
| 渐进消息预览（Slack） | [#7396](https://github.com/nearai/ironclaw/pull/7396) | 通道体验增强 | 近期 |
| 共享会话（Slack/Telegram） | [#7397](https://github.com/nearai/ironclaw/pull/7397) | 多租户/协作功能 | 近期 |
| Web Debug Inspector | [#7218](https://github.com/nearai/ironclaw/issues/7218) | 可观测性增强 | v1.1.0 Epic |
| Legacy 迁移工具 | [#6939](https://github.com/nearai/ironclaw/issues/6939) | 生态迁移支持 | 待定评估 |
| 替换编码工具为 omp | [#7392](https://github.com/nearai/ironclaw/issues/7392) | 工具标准化 | 待定 |

**信号**：WebUI 可观测性（Inspector）和通知渠道扩展是近期明确路线图；Legacy 迁移工具尚未看到对应 PR，可能需要单独排期。

---

## 7. 用户反馈摘要

| 反馈来源 | 痛点/诉求 | 场景 |
|---|---|---|
| [#6939](https://github.com/nearai/ironclaw/issues/6939) | "切换成本过高" — 现有 Hermes/Openclaw 用户不愿从零开始 | 升级/迁移场景 |
| [#6989](https://github.com/nearai/ironclaw/issues/6989) | Token 估算偏差导致实际用量与预期不符 | 成本核算与配额管理 |
| [#7391](https://github.com/nearai/ironclaw/issues/7391) | 安全文档描述的数据流（Validate → Sanitize → Detect Leaks）在生产路径未实现 | 安全合规与审计 |
| [#7395](https://github.com/nearai/ironclaw/pull/7395) | 交付丢失问题由竞态条件引起 | 消息可靠性 |
| [#7341](https://github.com/nearai/ironclaw/pull/7341) | WebUI 附件读取回归 | 用户体验 |

**整体满意度**：Reborn 架构迁移进度较快，但安全实现与生产路径对齐、Legacy 用户迁移支持是明确的负面反馈点。

---

## 8. 待处理积压

| Issue/PR | 时长 | 风险等级 | 建议优先级 |
|---|---|---|---|
| [#7391](https://github.com/nearai/ironclaw/issues/7391) | 今日新建 | **高** — 安全层未接入生产路径 | P0，需立即响应 |
| [#6989](https://github.com/nearai/ironclaw/issues/6989) | 8 天 | 中 — Token 计费偏差 | P1，影响成本核算 |
| [#7395](https://github.com/nearai/ironclaw/pull/7395) | 今日新建 | 高 — TOCTOU 竞态 | P1，待合并 |
| [#7028](https://github.com/nearai/ironclaw/pull/7028) | 6 天 | 中 — 恢复状态丢失 | P2，待合并 |
| [#6939](https://github.com/nearai/ironclaw/issues/6939) | 9 天 | 中 — 迁移工具需求 | P2，需产品评估 |
| [#7360](https://github.com/nearai/ironclaw/issues/7360) | 2 天 | 低 — 压测覆盖不足 | P2，已有 PR #7382 Phase 1 |
| [#7392](https://github.com/nearai/ironclaw/issues/7392) | 今日新建 | 低 — 工具替换 | P3，需评估兼容性 |

**维护者提醒**：[#7391](https://github.com/nearai/ironclaw/issues/7391) 描述的安全层函数在生产 Reborn turn 路径无调用者，与官方安全文档承诺不符，建议优先处理。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI 项目日报 — 2026-08-09

## 1. 今日速览

过去24小时 LobsterAI 社区保持中等活跃度：共处理 **1 个新 Issue** 和 **3 个 PR**，无新版本发布。一个关于 SQLite 写入性能优化的 PR（#1193）和 LiteLLM 网关集成功能（#2193，已合并）是今日主要推进内容，项目整体向前稳步推进，但 Issue 与 PR 的交互量偏低（全部评论数为 0/undefined，点赞数均为 0），社区讨论热度有待提升。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的 PR

| PR | 类型 | 作者 | 说明 |
|---|---|---|---|
| [#2193](https://github.com/netease-youdao/LobsterAI/pull/2193) | 功能 | RheagalFire | 新增 LiteLLM 作为 AI 网关提供商，用户可通过统一 OpenAI 兼容端点访问 100+ LLM，无需新增依赖 |
| [#1193](https://github.com/netease-youdao/LobsterAI/pull/1193) | 性能优化 | Housum | 消除 SQLite 写入放大问题：通过 debounce + 批量事务替代每次行变更触发全量 `db.export()` + `fs.writeFileSync()`，显著降低持久化开销 |
| [#2294](https://github.com/netease-youdao/LobsterAI/pull/2294) | 文档 | oratis | 添加 TakoAPI 目录徽章，提升项目在开源 Agent 生态中的可见度 |

> **综合评价**：今日 3 个 PR 中 1 个已合并（LiteLLM 集成），2 个仍处于待合并状态（SQLite 性能优化 & 文档徽章）。SQLite 写入优化对长时运行的 AI Agent 场景尤为关键，是本次最有技术价值的贡献。

---

## 4. 社区热点

**📌 #1192 — 自定义已有工具的默认配置**（[链接](https://github.com/netease-youdao/LobsterAI/issues/1192)）
- 状态：Open / stale · 创建：2026-04-01 · 最近更新：2026-08-08 · 评论：1
- **诉求分析**：用户希望在工具层面（如 browser 工具）直接固化默认启动参数（如 `headless: true`），而非依赖 LLM 指令跟随。当前通过记忆注入无头模式参数效果不稳定，暴露了"LLM 指令作为配置机制"的可靠性瓶颈。该 Issue 已 stale 超过4个月，说明核心功能层面对**静态工具配置**的需求尚未被充分满足。

**📌 #2193 — LiteLLM 网关集成**（[链接](https://github.com/netease-youdao/LobsterAI/pull/2193)）
- 状态：Closed · 作者：RheagalFire
- **社区反应**：该 PR 已合并，满足了大量用户通过统一代理接入多 LLM 提供商的需求，扩展了项目对商业/企业 LLM 生态的兼容性。

---

## 5. Bug 与稳定性

今日无新报告的 Bug 或崩溃问题。

> **备注**：PR #1193 提及的 SQLite 写入放大问题虽非崩溃级 Bug，但属于**性能退化隐患**——每次行变更触发全量磁盘写入，在高频交互场景下可能显著拖慢系统响应，影响 Agent 长期运行稳定性。该 PR 已通过 debounce + 批量事务机制修复，待合并后有望缓解。

---

## 6. 功能请求与路线图信号

| 信号来源 | 内容 | 优先级评估 |
|---|---|---|
| Issue #1192 | 工具层静态默认配置（如无头浏览器） | **高** — 用户痛点明确，涉及多工具场景，建议纳入下一版本 |
| PR #2193（已合） | LiteLLM 多 LLM 网关支持 | 已落地，后续可考虑扩展更多网关协议 |
| PR #2294（待合） | 开源目录曝光 | 低优先级，纯文档增强 |

**路线图推断**：工具默认配置机制可能是下一版本的重点方向。当前依赖 LLM 指令注入行为参数的设计存在确定性不足的问题，提供 `tool.defaults` 级别的配置能力可显著提升 Agent 行为可控性。

---

## 7. 用户反馈摘要

- **痛点 #1 — 配置不可控**（Issue #1192）：用户反馈通过记忆注入参数后，大模型指令跟随效果不稳定，导致预期行为无法可靠复现。核心诉求是**在工具定义层提供声明式默认配置**，减少对 LLM 指令的依赖。
- **痛点 #2 — 性能开销**（PR #1193）：SQLite 持久化机制每次写操作触发全量导出，在高频场景下存在明显性能瓶颈，用户期待增量/批量持久化方案。
- **正向反馈**：LiteLLM 网关集成（PR #2193）以零新增依赖的方式扩展了 LLM 兼容性，符合社区对多模型接入的需求；TakoAPI 徽章增强（PR #2294）体现了社区对项目可见度的积极维护。

---

## 8. 待处理积压

| 条目 | 类型 | 状态 | 积压时长 | 建议 |
|---|---|---|---|---|
| [#1192](https://github.com/netease-youdao/LobsterAI/issues/1192) | Issue | stale · Open | ~4 个月 | 维护者需评估是否纳入路线图，或给予用户明确回复 |
| [#1193](https://github.com/netease-youdao/LobsterAI/pull/1193) | PR | stale · Open | ~4 个月 | 性能修复 PR，建议优先审查合并 |
| [#2294](https://github.com/netease-youdao/LobsterAI/pull/2294) | PR | stale · Open | ~1 个月 | 文档增强，合并风险低，可快速通过 |

> **维护者提醒**：PR #1193（SQLite 性能优化）是当前积压中最具技术价值的条目，且逻辑清晰、改动聚焦，建议优先处理以避免 stale 后丢失维护者关注。Issue #1192 涉及工具配置范式讨论，需要更深入的架构决策，可考虑组织社区讨论后给出方向性回复。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# 📊 Moltis 项目日报 — 2026-08-09

---

## 1. 今日速览

过去 24 小时内 Moltis 项目保持**中度活跃**状态，共产生 3 条变更记录（2 Issues + 1 PR），无新版本发布。今日亮点为 Docker 沙盒文件系统工具的回归修复被合并（#1105），同时出现一个新 Bug 报告涉及 Apple Container 1.x 的运行状态检测问题（#1185）。项目整体健康度良好，社区问题响应及时，但 Docker 环境下的工具兼容性仍是近期主要关注点。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### ✅ 已合并 PR

**[#1105] Fix Docker sandbox filesystem tool fallback** — [链接](https://github.com/moltis-org/moltis/pull/1105)
- 作者：penso | 创建：2026-06-05 | 关闭：2026-08-08
- **推进内容**：修复了沙盒环境下 `Read`/`Write`/`Edit`/`MultiEdit` 工具在 Docker 中的降级处理逻辑，增加了对 `/home/sandbox` 和 `workspace/data` 路径的回归测试覆盖；当 gateway 进程无法访问宿主机挂载点时，自动回退至容器内操作，同时保持直接访问宿主机时的 missing-list 语义不变。
- **项目意义**：此 PR 直接关联 Issue #1096 的修复，使 Docker 容器化部署的文件系统工具可用性得到实质性改善，标志着项目在多容器运行时兼容性方面取得关键进展。

---

## 4. 社区热点

| 类型 | Issue/PR | 状态 | 链接 | 热度分析 |
|------|----------|------|------|----------|
| Bug | #1185 | 🟢 新开 | [链接](https://github.com/moltis-org/moltis/issues/1185) | Apple Container 1.x 沙盒启动状态误判，近期容器生态用户关注点 |
| Bug | #1096 | 🔵 已关闭 | [链接](https://github.com/moltis-org/moltis/issues/1096) | Docker 环境下文件系统工具失效，已被 #1105 修复 |
| PR | #1105 | ✅ 已合并 | [链接](https://github.com/moltis-org/moltis/pull/1105) | Docker 沙盒工具回退机制修复，关联上述 Issue |

**热点分析**：社区近期对 Docker 容器化部署的稳定性问题高度关注，#1096/#1105 形成完整的"报告→修复"闭环，响应效率较高。新开 Issue #1185 聚焦 Apple Container 环境，反映用户在 Mac 生态下的容器兼容性诉求正在上升。

---

## 5. Bug 与稳定性

| 严重级别 | Issue | 标题 | 状态 | 修复状态 | 链接 |
|----------|-------|------|------|----------|------|
| 🔴 高 | #1185 | Apple Container 1.x sandbox 启动但被误判为未运行 | 🟢 待处理 | 暂无关联 PR | [链接](https://github.com/moltis-org/moltis/issues/1185) |
| 🟡 中 | #1096 | `Read`/`Write`/`Edit` 工具在 Docker 中不可用 | 🔵 已关闭 | ✅ 已由 #1105 修复 | [链接](https://github.com/moltis-org/moltis/issues/1096) |

> **稳定性评估**：今日新报告 1 个高优先级 Bug，涉及 Apple Container 运行时状态检测逻辑，建议维护者优先排查。Docker 相关文件系统问题已修复，该回归风险解除。

---

## 6. 功能请求与路线图信号

- **Apple Container 支持完善**（Issue #1185）：用户报告 Apple Container 1.x 沙盒状态检测异常，暗示 Moltis 对 Apple 原生容器运行时（非 Docker）的适配仍存在盲区。此问题若被纳入路线图，可能推动项目在 Apple Silicon 生态的兼容性增强。
- **Docker 沙盒工具鲁棒性**：#1105 的合并表明维护者重视多运行时环境的文件系统工具一致性，后续可能继续扩展对其他沙盒环境的类似支持。

---

## 7. 用户反馈摘要

| 来源 | 用户痛点 / 使用场景 | 情感倾向 |
|------|---------------------|----------|
| #1185 | 在 Apple Container 1.x 环境中部署 Moltis 时，沙盒实际已启动，但 Moltis 内部状态机误判为未运行，导致后续操作受阻 | 😤 负面（功能性阻断） |
| #1096 | Docker 容器内 `Read`/`Write`/`Edit` 等文件操作工具完全失效，影响开发工作流 | 😤 负面（核心功能不可用） |
| #1105（合并） | 通过 PR 修复 Docker 沙盒降级逻辑，用户可恢复在容器环境中的文件编辑能力 | 😊 正面（问题已解决） |

---

## 8. 待处理积压

| 类型 | Issue/PR | 标题 | 创建日期 | 距今 | 链接 | 备注 |
|------|----------|------|----------|------|------|------|
| Bug | #1185 | Apple Container 1.x sandbox 状态误判 | 2026-08-08 | 今日 | [链接](https://github.com/moltis-org/moltis/issues/1185) | ⚠️ 新开高优先级，建议优先响应 |

---

> 📌 **日报总结**：Moltis 今日以 Docker 沙盒修复为核心进展，#1105 的合并解决了长期存在的容器工具兼容性问题。新出现的 Apple Container 状态检测 Bug（#1185）需引起维护者重视，建议跟进排查。项目整体处于稳定迭代周期，无版本发布，社区反馈以 Bug 报告为主，功能请求类信号较弱。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报 — 2026-08-09

## 1. 今日速览

CoPaw 在过去24小时内保持高度活跃：**19条 Issues**（17条新开/活跃、2条关闭）与**50条 PR**（47条待合并、3条已合并/关闭）同步推进，社区贡献密度极高。整体项目状态健康，核心开发聚焦于 **Scroll 上下文机制重构**、**桌面端稳定性修复** 及 **多渠道集成增强**，无新版本发布。问题以桌面端体验类 Bug 为主，功能请求类 Issue 集中反映用户对审批交互与子代理配置的改进诉求。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 作者 | 内容摘要 |
|----|------|----------|
| [#6536](https://github.com/agentscope-ai/QwenPaw/pull/6536) | niceIrene | 修复聊天删除时持久化数据未清理的问题（关联 Issue #6299），使删除操作真正释放磁盘空间 |
| [#6828](https://github.com/agentscope-ai/QwenPaw/issues/6828) | jackicy9736 | 用户报告闲置时 CSS 动画导致 ~20% CPU，已引起关注 |
| [#4558](https://github.com/agentscope-ai/QwenPaw/issues/4558) | BLUE0818 | 长时间文本输出时前端渲染导致 CPU 异常攀升的问题已关闭，预计修复已纳入后续版本 |

**推进方向：**
- **Scroll 上下文收敛**：PR #6779 将 Scroll 整合为唯一上下文协议，对齐 AgentScope 2.0 生命周期设计，消除多路径状态不一致风险。
- **历史会话保留策略优化**：PR #6591 将行级年龄裁剪改为会话级不活跃裁剪，避免长会话被意外截断。
- **CI 质量守护**：PR #6764 为主分支合并引入测试门禁，提升发布稳定性。

---

## 4. 社区热点

### 高活跃度 Issues

| Issue | 类型 | 评论数 | 链接 | 分析 |
|-------|------|--------|------|------|
| [#6782](https://github.com/agentscope-ai/QwenPaw/issues/6782) | Bug | 9 | Docker 版本插件/应用市场持续显示"维护中" | 用户反馈 Docker 部署场景下市场功能完全不可用，影响生产环境部署信心 |
| [#6811](https://github.com/agentscope-ai/QwenPaw/issues/6811) | Bug | 5 | OpenAI Responses 模式下 `disable_thinking` 被忽略 | 涉及流式续览与思考模型的兼容性问题，影响高级用户的使用体验 |
| [#6490](https://github.com/agentscope-ai/QwenPaw/issues/6490) | Feature | 5 | 新增火山引擎 Agent Plan 与小米 MiMo API | 国内云厂商接入需求明确，拓展 provider 生态 |

### 高活跃度 PRs

| PR | 作者 | 内容摘要 |
|----|------|----------|
| [#6824](https://github.com/agentscope-ai/QwenPaw/pull/6824) | niceIrene | 修复 Scroll FTS5 中文检索失效问题（CJK 分词器行为导致） |
| [#5861](https://github.com/agentscope-ai/QwenPaw/pull/5861) | alvinlee518 | 修复 macOS 桌面端因 login-shell PATH 缺失导致无法识别 Homebrew 等版本管理工具的问题 |
| [#5823](https://github.com/agentscope-ai/QwenPaw/pull/5823) | albert-zen | 飞书渠道支持 Markdown 图片原生渲染 |
| [#6636](https://github.com/agentscope-ai/QwenPaw/pull/6636) | BlackBox-Labs | 聊天历史接口增加分页与 GZip 压缩，解决长对话 30s 超时问题（关联 #6635） |
| [#6398](https://github.com/agentscope-ai/QwenPaw/pull/6398) | lecheng2018 | ReMe 记忆搜索新增 Reranker 支持，提升检索精度 |
| [#6652](https://github.com/agentscope-ai/QwenPaw/pull/6652) | BlackBox-Labs | 服务端强制限制 MissionGate 最大迭代次数，防止 LLM 无限派发子任务耗尽配额 |

---

## 5. Bug 与稳定性

### 严重级别排序

| Issue | 级别 | 描述 | 状态 | Fix PR |
|-------|------|------|------|--------|
| [#6814](https://github.com/agentscope-ai/QwenPaw/issues/6814) | 🔴 高 | macOS 打开 SQLite WAL 模式历史库时触发 SIGBUS 崩溃 | 新开 | 待定 |
| [#6822](https://github.com/agentscope-ai/QwenPaw/issues/6822) | 🔴 高 | 瞬态 MCP streamable_http 连接失败后永久阻塞当前对话 | 新开 | 待定 |
| [#6828](https://github.com/agentscope-ai/QwenPaw/issues/6828) | 🟡 中 | Console 闲置时 CSS 无限动画导致 ~20% CPU 占用 | 新开 | 待定 |
| [#6831](https://github.com/agentscope-ai/QwenPaw/issues/6831) | 🟡 中 | macOS 本地 Whisper 显示 ffmpeg 已禁用（PATH 不含 Homebrew） | 新开 | [#5861](https://github.com/agentscope-ai/QwenPaw/pull/5861) 在途 |
| [#6820](https://github.com/agentscope-ai/QwenPaw/issues/6820) | 🟡 中 | 前端不流式显示模型输出，全部完成后才渲染 | 新开 | 待定 |
| [#6813](https://github.com/agentscope-ai/QwenPaw/issues/6813) | 🟡 中 | ChatResponse (dict subclass) 触发 `KeyError: '__aiter__'`，导致自动标题生成失败 | 新开 | 待定 |
| [#6821](https://github.com/agentscope-ai/QwenPaw/issues/6821) | 🟡 中 | thinking-mode 模型多轮对话 `reasoning_content` relay 返回 400 | 新开 | 待定 |
| [#6810](https://github.com/agentscope-ai/QwenPaw/issues/6810) | 🟠 低 | Windows 安装时未终止占用进程，导致 NSIS 报错 | 新开 | 待定 |
| [#6782](https://github.com/agentscope-ai/QwenPaw/issues/6782) | 🟠 低 | Docker 版本插件/应用市场始终显示维护中 | 活跃 | 待定 |
| [#6812](https://github.com/agentscope-ai/QwenPaw/issues/6812) | 🟠 低 | Google Gemini API 拒绝含 `$schema` 字段的工具 schema | 新开 | 待定 |

---

## 6. 功能请求与路线图信号

| Issue/PR | 诉求摘要 | 路线图吻合度 |
|----------|----------|--------------|
| [#6490](https://github.com/agentscope-ai/QwenPaw/issues/6490) | 内置火山引擎 Agent Plan 与小米 MiMo API | 高 — 扩展 provider 覆盖，与 PR #6293（阿里云 Token Plan 新增模型）方向一致 |
| [#6832](https://github.com/agentscope-ai/QwenPaw/issues/6832) | 审批提交时附加 AI 生成的简短描述 | 高 — 改善人机协作体验，已在待处理清单中 |
| [#6827](https://github.com/agentscope-ai/QwenPaw/issues/6827) | 删除对话时可选清理临时文件 | 高 — 与 PR #6536（删除清理持久化数据）互补，预计纳入同一版本 |
| [#6719](https://github.com/agentscope-ai/QwenPaw/pull/6719) | 工作区产物卡片（WorkBuddy 风格） | 中 — 增强桌面端文件交互体验，已在 Review 中 |
| [#6715](https://github.com/agentscope-ai/QwenPaw/pull/6715) | OneBot 渠道支持远程音视频媒体 | 中 — 扩展消息渠道能力 |
| [#6398](https://github.com/agentscope-ai/QwenPaw/pull/6398) | ReMe 记忆搜索 Reranker 支持 | 中 — 提升检索质量，技术风险可控 |

---

## 7. 用户反馈摘要

### 核心痛点

1. **桌面端本地工具链识别问题**（[#6831](https://github.com/agentscope-ai/QwenPaw/issues/6831)、[#6810](https://github.com/agentscope-ai/QwenPaw/issues/6810)）
   - macOS 用户反馈 Homebrew 安装的 ffmpeg 无法被识别，Windows 用户反馈安装程序未处理进程占用。两者均指向**桌面端环境初始化路径配置缺陷**。

2. **前端渲染性能**（[#6828](https://github.com/agentscope-ai/QwenPaw/issues/6828)、[#6820](https://github.com/agentscope-ai/QwenPaw/issues/6820)、[#4558](https://github.com/agentscope-ai/QwenPaw/issues/4558)）
   - 持续收到 CSS 动画导致闲置 CPU 高占用、流式输出不实时渲染等反馈，说明前端性能优化是高频诉求。

3. **上下文/记忆机制稳定性**（[#6811](https://github.com/agentscope-ai/QwenPaw/issues/6811)、[#6822](https://github.com/agentscope-ai/QwenPaw/issues/6822)、[#6814](https://github.com/agentscope-ai/QwenPaw/issues/6814)）
   - Scroll 历史库的 SQLite 崩溃、MCP 连接失败后永久阻塞、OpenAI reasoning 模式兼容性问题，均指向**上下文管理模块的鲁棒性有待加强**。

4. **审批与子代理用户体验**（[#6819](https://github.com/agentscope-ai/QwenPaw/issues/6819)、[#6838](https://github.com/agentscope-ai/QwenPaw/issues/6838)）
   - 用户希望审批时有清晰描述、子代理能自动切换模型且共享 workspace，反映进阶用户对**多代理协作流程的精细化控制需求**。

---

## 8. 待处理积压

| Issue/PR | 类型 | 创建时间 | 风险说明 |
|----------|------|----------|----------|
| [#6814](https://github.com/agentscope-ai/QwenPaw/issues/6814) | Bug | 2026-08-08 | macOS SQLite WAL SIGBUS 崩溃，尚未有 Fix PR，影响历史库稳定性 |
| [#6822](https://github.com/agentscope-ai/QwenPaw/issues/6822) | Bug | 2026-08-08 | MCP 瞬态失败永久阻塞对话，无 Fix PR，用户体验影响严重 |
| [#6813](https://github.com/agentscope-ai/QwenPaw/issues/6813) | Bug | 2026-08-08 | ChatResponse `KeyError` 导致自动标题生成持续失败，无 Fix PR |
| [#6821](https://github.com/agentscope-ai/QwenPaw/issues/6821) | Bug | 2026-08-08 | thinking-mode 模型 `reasoning_content` relay 失败，无 Fix PR |
| [#5861](https://github.com/agentscope-ai/QwenPaw/pull/5861) | Fix | 2026-07-08 | macOS PATH 修复 PR 已提交超一个月，仍在 Review 中，关联 Issue #6831 |
| [#6779](https://github.com/agentscope-ai/QwenPaw/pull/6779) | Refactor | 2026-08-07 | Scroll 上下文重构 PR，涉及面广，需充分测试 |
| [#6398](https://github.com/agentscope-ai/QwenPaw/pull/6398) | Feature | 2026-07-23 | Reranker 支持 PR 已提交超两周，仍在 Review 中 |

---

**整体评估：** CoPaw 项目社区活跃度高，贡献者多元（首次贡献者占比显著）。当前主要风险集中在 **桌面端环境兼容** 与 **上下文管理模块稳定性** 两个方向，建议维护者优先关注 #6814、#6822 两个稳定性 Bug 的修复进展。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目动态日报
**日期：2026-08-09**

---

## 1. 今日速览

ZeroClaw 在过去24小时内保持了较高的社区活跃度，共新增/更新 **50条 Issue** 和 **50条 PR**，其中 **47条 Issue** 处于新开或活跃状态，**48条 PR** 待合并，整体研发节奏稳定。项目无新版本发布，但核心基础设施持续演进——SOP（标准操作程序）自动化流程、网络守卫重构、渠道安全加固等关键特性进入实施阶段。安全议题占据今日热点，多个P1级安全漏洞（如`forbidden_paths`失效、交互式审批任意成员响应、泄漏检测误报）集中暴露，反映出项目正在经历从功能扩展到安全加固的关键转折期。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 标题 | 贡献者 | 进展说明 |
|----|------|--------|----------|
| [#9494](https://github.com/zeroclaw-labs/zeroclaw/pull/9494) | fix(sop): drive cron-started headless runs | Lusitaniae | **已关闭** — 修复了cron触发SOP无人执行、卡死在`running`状态的阻塞性缺陷 |
| [#9798](https://github.com/zeroclaw-labs/zeroclaw/pull/9798) | docs(sop): document which agent executes SOP steps | JordanTheJet | **已关闭（被#9841取代）** — 文档补丁，已被运行时修复替代 |
| [#9856](https://github.com/zeroclaw-labs/zeroclaw/pull/9856) | chore(deps): bump actions/attest to v4.2.2 | Audacity88 | **进行中** — 同步发布签名依赖，安全基线升级 |
| [#9817](https://github.com/zeroclaw-labs/zeroclaw/pull/9817) | docs(rfc): route by what the author knows and gate RFC intake on an explicit trigger | JordanTheJet | **进行中** — 修订RFC流程引导规则，降低无效RFC提交 |

### 关键进行中 PR

- **[PR #9841](https://github.com/zeroclaw-labs/zeroclaw/pull/9841)** — 修复headless SOP运行缺陷的完整补丁系列，关闭review中发现的4个阻塞性问题，是#9494的延续
- **[PR #9828](https://github.com/zeroclaw-labs/zeroclaw/pull/9828)** — 新增agent-facing配置编写能力，允许通过JSON Patch由operator审批后安全写入配置
- **[PR #9580](https://github.com/zeroclaw-labs/zeroclaw/pull/9580)** — 网络守卫重构第一阶段：将网络守卫原语移至`zeroclaw-infra::net_guard`，支撑插件egress策略
- **[PR #9744](https://github.com/zeroclaw-labs/zeroclaw/pull/9744)** — 要求webhook入口通过身份认证后才转发agent请求，减少未授权调用风险
- **[PR #9571](https://github.com/zeroclaw-labs/zeroclaw/pull/9571)** — 移除WATI渠道模块，削减维护负担

**整体推进评估：** 今日PR以修复和基础设施重构为主，SOP自动化链路的headless执行能力即将完善；安全与网络边界加固投入显著，符合项目进入成熟期后的防御性演进趋势。

---

## 4. 社区热点

### 讨论最活跃的 Issues

| 排名 | Issue | 类型 | 评论数 | 核心议题 |
|------|-------|------|--------|----------|
| 1 | [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | RFC/架构 | 11 | Maintainer决策队列追踪器 |
| 2 | [#8043](https://github.com/zeroclaw-labs/zeroclaw/issues/8043) | RFC（已关闭） | 11 | 退役aardvark-sys crate，合并入zeroclaw-hardware |
| 3 | [#8424](https://github.com/zeroclaw-labs/zeroclaw/issues/8424) | RFC | 11 | 工作区相对禁止路径模式与可选.zeroclawignore |
| 4 | [#8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) | Bug/P1 | 10 | 系统提示中工具可用性与实际入口不一致 |
| 5 | [#5514](https://github.com/zeroclaw-labs/zeroclaw/issues/5514) | Bug | 6 | Telegram批量媒体分组为单次多模态调用 |
| 6 | [#8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550) | 功能请求 | 6 | 添加OpenAI兼容的chat completions端点 |

### 讨论最活跃的 PRs

| PR | 核心内容 |
|----|----------|
| [#9694](https://github.com/zeroclaw-labs/zeroclaw/pull/9694) | SOP面板只读状态视图暴露 |
| [#9739](https://github.com/zeroclaw-labs/zeroclaw/pull/9739) | 多会话面板+Agent侧边栏+快速启动 |
| [#9272](https://github.com/zeroclaw-labs/zeroclaw/pull/9272) | Web聊天界面展示Safeguard回退通知 |
| [#8337](https://github.com/zeroclaw-labs/zeroclaw/pull/8337) | Herdr agent状态上报集成 |

**热点分析：**
- **架构治理**：#8692（Maintainer决策队列）和#8043（aardvark-sys退役）反映了社区对RFC流程规范化和crate合并的持续关注
- **安全焦虑**：#8424（禁止路径模式）和#8054（工具可用性不一致）揭示了用户对agent权限边界和行为确定性的强烈需求
- **渠道体验**：Telegram/Slack等渠道的多模态支持、进度反馈、审批体验是当前用户痛点集中区
- **OpenAI兼容**：#8550被频繁提及，表明生态集成（Open WebUI、LobeChat等）是用户规模化部署的关键诉求

---

## 5. Bug 与稳定性

### P0/P1 级 Bug（按严重程度）

| Issue | 严重程度 | 摘要 | Fix状态 |
|-------|----------|------|---------|
| [#9815](https://github.com/zeroclaw-labs/zeroclaw/issues/9815) | P1/高危 | `forbidden_paths`在`allowed_roots`或workspace下的路径上完全失效 | 新报告，无Fix |
| [#9816](https://github.com/zeroclaw-labs/zeroclaw/issues/9816) | P1/高危 | Anthropic provider成本归零，导致预算上限永不触发 | 新报告，无Fix |
| [#9390](https://github.com/zeroclaw-labs/zeroclaw/issues/9390) | P1/高危 | CLI紧急停止（estop）仅为状态文件，运行时路径未读取 | 新报告，无Fix |
| [#9805](https://github.com/zeroclaw-labs/zeroclaw/issues/9805) | P1/高危 | auto模式SOP从channel/cron触发时永远卡在`running` | 已有PR #9841 修复中 |
| [#9825](https://github.com/zeroclaw-labs/zeroclaw/issues/9825) | P1/高危 | 泄漏检测将公开区块链地址误标为高熵token并红标 | 新报告，无Fix |
| [#9387](https://github.com/zeroclaw-labs/zeroclaw/issues/9387) | P1/高危 | 交互式审批响应可在Telegram/Slack/Lark/Matrix任意成员接受 | 新报告，无Fix |
| [#8731](https://github.com/zeroclaw-labs/zeroclaw/issues/8731) | P1/高危 | stdio型MCP服务器积累为僵尸进程 | 无Fix |
| [#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559) | P1/高危 | Web Dashboard关闭后agent任务中断 | 无Fix |
| [#8410](https://github.com/zeroclaw-labs/zeroclaw/issues/8410) | P1/高危 | Channel任务缺少"有意不回复"的first-class退出路径 | 无Fix |
| [#9340](https://github.com/zeroclaw-labs/zeroclaw/issues/9340) | P1/高危 | CLI创建的cron job delivery硬编码为None，结果被丢弃 | 无Fix |
| [#9573](https://github.com/zeroclaw-labs/zeroclaw/issues/9573) | P1/高危 | 多别名provider配置导致成本查询失效 | 无Fix |
| [#9035](https://github.com/zeroclaw-labs/zeroclaw/issues/9035) | P1/高危 | Docker Compose部署端口仅绑定loopback | 无Fix |
| [#9486](https://github.com/zeroclaw-labs/zeroclaw/issues/9486) | P2/高危 | Solana钱包地址被高熵检测器红标，`high_entropy_tokens=false`对channel路径无效 | 无Fix |

**稳定性评估：** 今日新增 **13个P1级安全/稳定性Bug**，其中仅1个（#9805）已有修复PR在途。`forbidden_paths`失效（#9815）和审批响应任意成员接受（#9387）属于潜在高危漏洞，建议维护者优先响应。成本追踪（#9816、#9573）和泄漏检测误报（#9825、#9486）影响生产可用性。

---

## 6. 功能请求与路线图信号

| Issue/PR | 需求摘要 | 纳入下一版本的可能性 |
|----------|----------|----------------------|
| [#8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550) | OpenAI兼容chat completions端点 | ⭐⭐⭐⭐ 高 — 生态集成刚需，有明确PR推动 |
| [#9824](https://github.com/zeroclaw-labs/zeroclaw/issues/9824) | 简化默认web工具集（web_fetch + web_research + http_request） | ⭐⭐⭐⭐ 高 — 由JordanTheJet主导，架构清晰 |
| [#9845](https://github.com/zeroclaw-labs/zeroclaw/issues/9845) | 支持agent别名中的非ASCII字符（如中文） | ⭐⭐⭐ 中 — 需求合理，修复简单 |
| [#9346](https://github.com/zeroclaw-labs/zeroclaw/issues/9346) | 统一package/capability/config/runtime-state目录契约 | ⭐⭐⭐ 中 — 架构级RFC，影响面广 |
| [#6663](https://github.com/zeroclaw-labs/zeroclaw/issues/6663) | Telegram工具调用进度显示 | ⭐⭐⭐ 中 — PR #9822 已在实现 |
| [#8445](https://github.com/zeroclaw-labs/zeroclaw/issues/8445) | Telegram多消息模式（每次agent turn发独立消息） | ⭐⭐ 低 — 需求明确但优先级低于安全修复 |
| [#7099](https://github.com/zeroclaw-labs/zeroclaw/issues/7099) | `zeroclaw status`输出国际化 | ⭐⭐ 低 — 体验优化，无阻塞 |

**路线图信号：**
- **安全与权限控制**：#8424（workspace相对禁止路径）、#9824（web工具精简）、#9744（webhook认证）共同指向"更精细的权限边界"方向
- **渠道体验升级**：Telegram/Slack的进度反馈、多消息模式、typing indicator优化将持续迭代
- **SOP自动化**：headless运行修复（#9841）、配置编写能力（#9828）、只读视图（#9694）构成完整的SOP工具链
- **生态兼容**：OpenAI兼容端点（#8550）和Herdr集成（#8337）扩展第三方生态接入能力

---

## 7. 用户反馈摘要

### 核心痛点

1. **权限控制形同虚设**：#9815 指出 `forbidden_paths` 在 `allowed_roots` 下完全失效，用户报告敏感文件（`.env`、`rust-toolchain.toml`）仍可被agent访问，#8424 用户明确提出需要工作区内部的禁止路径机制

2. **审批安全存在严重缺陷**：#9387 审计发现交互式审批可在Telegram/Slack/Lark/Matrix中由**任意群成员**接受，而非仅限授权用户，属于生产环境高危漏洞

3. **成本追踪完全失效**：#9816 和 #9573 同时报告 Anthropic provider 成本归零、多别名配置下成本查询失效，导致预算上限无法触发，用户无法控制支出

4. **渠道体验碎片化**：Telegram 端用户反映批量图片被拆分为多次请求（#5514）、审批等待期间typing indicator持续闪烁（#9656）、批量媒体分组为单次调用等体验问题

5. **SOP自动化链路断裂**：#9805 报告 auto 模式 SOP 从 channel/cron 触发后永远卡在 `running` 状态，消耗并发槽位且永不完成，#9340 报告 CLI 创建的 cron job 结果被硬编码丢弃

### 用户满意点
- PR #9494/#9841 修复 SOP 无人执行问题后，自动化调度链路趋于完整
- PR #9822/#9823 改善 Telegram 工具调用进度反馈和审批期间 typing indicator 行为
- PR #9744 强化 webhook 认证，提升网关安全性
- PR #9571 移除 WATI 渠道降低维护负担

---

## 8. 待处理积压

### 长期未响应的高优先级 Issue

| Issue | 创建时间 | 状态 | 建议行动 |
|-------|----------|------|----------|
| [#8731](https://github.com/zeroclaw-labs/zeroclaw/issues/8731) | 2026-07-05 | in-progress | stdio MCP僵尸进程问题，超过4周无实质进展 |
| [#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559) | 2026-06-30 | in-progress | Web Dashboard关闭导致agent中断，影响核心工作流 |
| [#9035](https://github.com/zeroclaw-labs/zeroclaw/issues/9035) | 2026-07-13 | in-progress | Docker Compose端口绑定loopback，部署失败 |
| [#9340](https://github.com/zeroclaw-labs/zeroclaw/issues/9340) | 2026-07-24 | in-progress | CLI cron job delivery硬编码None，结果丢失 |
| [#9573](https://github.com/zeroclaw-labs/zeroclaw/issues/9573) | 2026-07-31 | accepted | 多别名provider成本查询失效 |

### 今日新增需立即关注

| Issue | 严重性 | 说明 |
|-------|--------|------|
| [#9815](https://github.com/zeroclaw-labs/zeroclaw/issues/9815) | P1/安全 | `forbidden_paths`在workspace内失效，权限控制存在绕过路径 |
| [#9387](https://github.com/zeroclaw-labs/zeroclaw/issues/9387) | P1/安全 | 审批响应可被任意channel成员接受，身份验证缺失 |
| [#9816](https://github.com/zeroclaw-labs/zeroclaw/issues/9816) | P1/稳定性 | Anthropic成本归零，预算控制失效 |
| [#9825](https://github.com/zeroclaw-labs/zeroclaw/issues/9825) | P1/稳定性 | 泄漏检测误红标公开区块链地址，支付请求无法送达 |

---

**报告生成时间：** 2026-08-09  
**数据截止：** 2026-08

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*