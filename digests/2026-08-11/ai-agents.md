# OpenClaw 生态日报 2026-08-11

> Issues: 500 | PRs: 500 | 覆盖项目: 12 个 | 生成时间: 2026-08-11 02:09 UTC

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



# OpenClaw 项目日报 — 2026-08-11

## 1. 今日速览

过去24小时项目活跃度维持高位：共收到 500 条 Issue 更新（新开/活跃 439，已关闭 61）及 500 条 PR 更新（待合并 332，已合并/关闭 168）。无新版本发布。今日焦点集中在**会话状态持久化稳定性**与**多通道消息去重**两个核心问题上，多个 P1 级 Bug 引发大量社区讨论。维护者团队正通过一系列重构 PR（PR #121566、#121366）提升代码可维护性，同时持续修复 Telegram、Feishu 等通道的消息重复与丢失问题。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

**已合并/关闭的重要 PR：**

| PR | 类型 | 说明 |
|----|------|------|
| [#121647](https://github.com/openclaw/openclaw/pull/121647) | fix | 修复 durable context engine 在会话历史超过 20k 事件或 8 MiB 后永久停滞的问题 |
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | feat(security) | 新增安装策略警告的交互式确认机制，防止静默接受高风险策略变更 |
| [#101126](https://github.com/openclaw/openclaw/pull/101126) | fix | 原生后台任务启动时发送可见的 `Background task started` 通知 |
| [#101294](https://github.com/openclaw/openclaw/pull/101294) | feat | 新增 WhatsApp phone-code 登录方式，解决无 QR 环境下的首连问题 |
| [#81190](https://github.com/openclaw/openclaw/pull/81190) | fix | 在模型驱动压缩超时前，对工具结果进行确定性截断，避免 Telegram 会话卡死 |
| [#121780](https://github.com/openclaw/openclaw/pull/121780) | improve | 延迟 Gateway 非启动阶段运行时导入，优化冷启动性能 |
| [#103028](https://github.com/openclaw/openclaw/pull/103028) | feat | CLI 支持从文件/stdin 读取 agent 消息输入，解决长 prompt 通过 argv 暴露的隐私问题 |
| [#121108](https://github.com/openclaw/openclaw/pull/121108) | fix | 正确枚举并终止附着 Unix 进程的后代 PID，解决超时后子进程泄漏 |
| [#120419](https://github.com/openclaw/openclaw/pull/120419) | fix | 重新排队在被遗弃前陷入 stalls 的 ingress 事件，防止用户消息静默丢失 |
| [#94719](https://github.com/openclaw/openclaw/pull/94719) | fix | 运行时读取 `claudeCodeVersion`，避免硬编码 user-agent 导致的 Anthropic OAuth 认证失败 |
| [#93952](https://github.com/openclaw/openclaw/pull/93952) | fix | 限制 OAuth refresh 等待时间但不释放 token 所有权，防止单次 pending 操作阻塞后续所有模型调用 |
| [#121378](https://github.com/openclaw/openclaw/pull/121378) | fix | 修复 `sessions.patch` 在 normalize 阶段静默丢弃 `toolOverrides.webSearch: true` 的 bug |
| [#120595](https://github.com/openclaw/openclaw/pull/120595) | fix | 将 virtiofs-backed SQLite DB 路由到 rollback journaling 模式，修复 Docker Desktop/OrbStack 上的数据库损坏和 crash loop |

**进行中的重要重构：**
- [#121566](https://github.com/openclaw/openclaw/pull/121566) — 按概念拆分 Claude live sessions（原 2225 行模块），降低生命周期竞态风险
- [#121366](https://github.com/openclaw/openclaw/pull/121366) — 整合分散在数百处的一致性 coercion 辅助函数，消除核心/插件/UI 间的解析行为漂移

---

## 4. 社区热点

| Issue | 评论数 | 热度分析 |
|-------|--------|----------|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) — Silent reply failures 在 #116277 关闭后仍重现 | 48 | **最高热度**。监控 cron 持续记录新发生事件，用户质疑修复的完整性，维护者需给出明确根因分析 |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging by Source | 34 | 安全敏感功能，用户担忧 memory poisoning 攻击，需产品决策与安全审查双重把关 |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) — 集中化文件名编码工具 | 20 | PR #48578 仅修复 UTF-8/Latin-1 误读，社区期待通用多编码方案（Shift-JIS、EUC-KR、GB18030 等） |
| [#22438](https://github.com/openclaw/openclaw/issues/22438) — 分级 bootstrap 文件加载 | 18 | 大 workspace 用户核心诉求：减少子代理和 cron 会话中无效文件对 context window 的占用 |

**热点背后的诉求：**
- 用户希望**修复可验证**：关闭的 Issue 不应继续被监控告警
- 用户对**安全边界**高度敏感：memory 来源信任、工具权限隔离、子代理 DMZ 模型
- **多编码国际化**是 Feishu/Slack 等企业通道用户的长期痛点

---

## 5. Bug 与稳定性

### P1 级（影响消息丢失/崩溃/会话阻塞）

| Issue | 状态 | 描述 | Fix PR |
|-------|------|------|--------|
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | OPEN | Session transcript projection 在持续写入下 livelock，阻塞主线程和所有通道传输 | — |
| [#40001](https://github.com/openclaw/openclaw/issues/40001) | OPEN | `write` 工具缺少 append 模式，隔离 cron 会话覆盖共享文件导致静默数据丢失 | — |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | OPEN | 长对话（15+ 轮）后 `write`/`exec` 工具参数静默丢失，arguments 对象为空 | — |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | OPEN | 子进程泄漏（hooks/bash/codex 僵尸积累），导致运行时退化 | — |
| [#119087](https://github.com/openclaw/openclaw/issues/119087) | OPEN | Gateway 冷启动性能回归：2026.7.1-beta.1 → 2026.7.2-beta.7 慢约 2.5 倍 | [#121780](https://github.com/openclaw/openclaw/pull/121780)（已在途中） |
| [#89278](https://github.com/openclaw/openclaw/issues/89278) | OPEN | Codex OAuth refresh 成功但 cron/heartbeat 因 10s 超时失败 | — |
| [#96242](https://github.com/openclaw/openclaw/issues/96242) | CLOSED | Telegram 多路径导致重复消息（已修复） | — |
| [#86519](https://github.com/openclaw/openclaw/issues/86519) | CLOSED | 2026.5.20 升级后 Telegram 重复回复 2-10x（已缓解至 2-3x） | — |

### P2 级（体验问题/功能异常）

| Issue | 状态 | 描述 |
|-------|------|------|
| [#57256](https://github.com/openclaw/openclaw/issues/57256) | OPEN | `openclaw status` 错误报告 openclaw-mem0 memory 不可用，实际 gateway 插件正常运行 |
| [#109145](https://github.com/openclaw/openclaw/issues/109145) | CLOSED | v2026.7.1-beta.5 Gateway HTTP 监听但不接受连接（已修复） |
| [#50490](https://github.com/openclaw/openclaw/issues/50490) | OPEN | 飞书群聊 activation 模式切换无效，始终响应所有消息 |
| [#42820](https://github.com/openclaw/openclaw/issues/42820) | OPEN | 飞书 `message` 工具因 poll schema 干扰无法发送纯文件 |

---

## 6. 功能请求与路线图信号

| Issue | 优先级 | 描述 | 路线图判断 |
|-------|--------|------|------------|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | P2 | 按来源对 memory 条目打信任标签，防止 memory poisoning | 安全类功能，需 security review，可能纳入下一安全加固版本 |
| [#22438](https://github.com/openclaw/openclaw/issues/22438) | P2 | 分级 bootstrap 文件加载，精细控制 context 预算 | 大 workspace 用户高频需求，与 PR #121566 重构方向一致，可能随 sessions 重构一起推进 |
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | P2 | Gateway 层 per-agent 成本预算（日/月上限） | 企业部署刚需，需产品决策，暂无关联 PR |
| [#27445](https://github.com/openclaw/openclaw/issues/27445) | P1 | `announceTarget` 选项控制子代理完成通知路由到父会话 | 多步工作流编排核心能力，已有 linked PR，优先级高 |
| [#16670](https://github.com/openclaw/openclaw/issues/16670) | P2 | Onboarding Wizard 将 Memory/Embedding 配置设为必填步骤 | 降低新用户配置摩擦，可能随 setup 流程优化一起推进 |
| [#13700](https://github.com/openclaw/openclaw/issues/13700) | P2 | Session snapshots（保存/加载上下文检查点） | 长会话管理需求，暂无关联 PR |
| [#15032](https://github.com/openclaw/openclaw/issues/15032) | P2 | 子代理 spawn 时的工具权限隔离（DMZ 模型） | 与 #7707 安全诉求同源，可能合并推进 |
| [#38568](https://github.com/openclaw/openclaw/issues/38568) | P3 | 系统 prompt runtime 段注入 context window 使用百分比 | 低摩擦高价值，可快速实现 |

---

## 7. 用户反馈摘要

**核心痛点：**
1. **修复不可验证**：[#121058](https://github.com/openclaw/openclaw/issues/121058) 用户指出 Issue 关闭后监控 cron 仍记录到相同失败，质疑关闭标准与回归检测机制
2. **长对话稳定性**：[#53408](https://github.com/openclaw/openclaw/issues/53408) 反映 15+ 轮后工具参数静默丢失，影响重度 tool-use 用户
3. **子代理生命周期管理**：[#47975](https://github.com/openclaw/openclaw/issues/47975)、[#111010](https://github.com/openclaw/openclaw/issues/111010) 反映子代理 session 持久化、hook relay 丢失等问题，多代理工作流用户受影响
4. **认证刷新竞态**：[#83598](https://github.com/openclaw/openclaw/issues/83598)、[#89278](https://github.com/openclaw/openclaw/issues/89278) 多个 OAuth refresh 超时/死锁问题，影响 cron 和心跳任务
5. **Windows 测试稳定性**：[#119796](https://github.com/openclaw/openclaw/issues/119796) vitest teardown 在 Windows 上 EBUSY unlink，影响 CI

**正面反馈：**
- [#33413](https://github.com/openclaw/openclaw/issues/33413) 用户希望 Slack 线程状态显示工具级进度（当前仅显示 "is typing..."），获得

---

## 横向生态对比



# 2026-08-11 个人 AI 智能体开源生态横向对比分析

## 1. 生态全景

2026年8月的个人 AI 助手开源生态呈现**高竞争、快速分化**态势：OpenClaw 作为核心参照保持高频迭代（500 Issue/500 PR），NanoBot 和 CoPaw 等新兴项目同样活跃，形成差异化竞争格局。**安全加固、多通道稳定性、记忆系统优化**成为跨项目共同焦点，反映行业从"功能实现"向"生产可靠"转型。NullClaw 活跃度明显落后，部分项目（如 LobsterAI）已启动重大技术栈升级（Vite 8、React 19）。

---

## 2. 各项目活跃度对比

| 项目 | Issue 数 | PR 数 | 合并率 | 发布 | 健康度 | 核心特征 |
|------|----------|-------|--------|------|--------|----------|
| **OpenClaw** | 500 | 500 | 33.6% | 无 | ⭐⭐⭐⭐⭐ | 生态核心，P1 Bug 集中 |
| **CoPaw** | 33 | 50 | 34% | 无（v2.1.0 准备中） | ⭐⭐⭐⭐☆ | 高活跃，严格提供商兼容问题 |
| **NanoBot** | 4 | 24 | 42% | 无 | ⭐⭐⭐⭐☆ | 快速迭代，安全加固密集 |
| **LobsterAI** | 1 | 34 | 59% | 无 | ⭐⭐⭐⭐☆ | 合流高效，依赖现代化 |
| **Hermes Agent** | 50 | 50 | 10% | 无 | ⭐⭐⭐☆☆ | god-file 重构，Windows 稳定性集中爆发 |
| **NanoClaw** | 3 | 20 | 50% | 无 | ⭐⭐⭐⭐☆ | 安全与消息可靠性双轨推进 |
| **Moltis** | 3 | 2 | 0% | 无 | ⭐⭐⭐☆☆ | Apple Container 后端问题聚集 |
| **PicoClaw** | 2 | 7 | 100% | 无 | ⭐⭐⭐☆☆ | 中等活跃度，安全边界收紧 |
| **NullClaw** | 1 | 1 | 0% | 无 | ⭐⭐☆☆☆ | 活跃度低，依赖更新积压 |
| **ZeroClaw** | 50 | 50 | 4% | 无 | ⭐⭐⭐⭐☆ | 安全审计与 RFC 治理期 |

---

## 3. OpenClaw 在生态中的定位

**优势：**
- **社区规模碾压**：Issue/PR 量级（500/500）约为次级项目的 10-50 倍，具备最强的生态影响力
- **多通道覆盖最全**：Telegram、Feishu、WhatsApp、Slack、Matrix 等主流渠道均有深度适配
- **架构演进激进**：god-file 重构（#78647 Epic 同类）、sessions 拆分（#121566/#121366）体现对代码质量的长期投入

**技术路线差异：**
- 与 NanoBot/Hermes 相比，OpenClaw 更侧重**生产级多租户与通道稳定性**，而非实验性功能
- 与 CoPaw 相比，OpenClaw 在**企业级部署**（Gateway、OAuth、cron 管理）方面更成熟
- 与 NullClaw 相比，OpenClaw 活跃度高出一个数量级，生态号召力显著

---

## 4. 共同关注的技术方向

| 方向 | 涉及项目 | 具体诉求 |
|------|----------|----------|
| **消息可靠性** | OpenClaw、NanoBot、NanoClaw、CoPaw | 消息重复/丢失、silent loop、平台 ID 复用导致静默丢弃 |
| **安全加固** | NanoBot、Hermes Agent、NanoClaw、ZeroClaw、PicoClaw | 凭据泄露、OAuth 刷新竞态、SSRF、配对码强度、远程 exec 控制 |
| **多通道/多提供商兼容** | OpenClaw、CoPaw、ZeroClaw、NanoBot | StepFun 等严格提供商格式拒绝、OAuth 多路径冲突、MCP OAuth 支持 |
| **长对话稳定性** | OpenClaw、Hermes Agent、CoPaw | 15+ 轮工具参数丢失、Durable Context 停滞、1M context 压缩策略 |
| **Windows 平台稳定性** | Hermes Agent、LobsterAI、OpenClaw | parent-death watchdog 误触发、pip shim 残留、渲染进程 IPC 卡死 |
| **Windows 更新/维护** | Hermes Agent、LobsterAI | 文件锁定、更新后崩溃、修复安装无效 |
| **记忆系统** | CoPaw、NanoBot | ReMe reranker、Dream 记忆无限循环、token 消耗失控 |

---

## 5. 差异化定位分析

| 项目 | 功能侧重 | 目标用户 | 架构特点 |
|------|----------|----------|----------|
| **OpenClaw** | 全渠道网关 + 多 Agent 编排 | 企业/重度用户 | 会话持久化、Gateway 架构、多通道路由 |
| **NanoBot** | MCP 生态 + 安全优先 | 开发者/技术用户 | RuntimeControl 协议、显式状态管理、OAuth 网关 |
| **Hermes Agent** | 多租户 + Windows Desktop | 多用户团队 | god-file 重构、Skills 锁定、凭据隔离 |
| **CoPaw** | 记忆系统 + 严格提供商兼容 | 国内用户（StepFun 等） | ReMe Light、reranker、Creator 插件 |
| **LobsterAI** | 协作功能（Cowork）+ 前端体验 | 多会话用户 | 活动组折叠、IPC 稳定性、依赖现代化 |
| **NanoClaw** | 远程 MCP + 插件化架构 | 技术爱好者 | Agent Plugins 1.0.0、单职责集成规则 |
| **Moltis** | Apple Container 后端 | macOS 用户 | CDP 实时交互、Sandbox 管理 |
| **PicoClaw** | 轻量级 + 安全边界 | 安全敏感用户 | 远程 exec 默认禁用、dispatch rules |
| **NullClaw** | A2A 协议服务端 | 多 Agent 协作探索者 | 仅服务端，缺乏客户端工具链 |
| **ZeroClaw** | 安全审计 + 多通道 | 安全优先场景 | OpenAI Chat Completions 兼容、DAG 规划 |

---

## 6. 社区热度与成熟度

**第一梯队（快速迭代期）：**
- **OpenClaw**：日均 500+ Issue/PR，核心参照系
- **CoPaw**：33 Issue/50 PR，v2.1.0 准备中，记忆系统深度迭代
- **NanoBot**：4 Issue/24 PR，安全与架构重构密集，从"能用"向"可靠"转型
- **LobsterAI**：1 Issue/34 PR，合流效率高，技术栈现代化加速

**第二梯队（质量巩固期）：**
- **Hermes Agent**：50/50，god-file 重构进行中，Windows 问题集中爆发反映平台适配挑战
- **NanoClaw**：3/20，稳健推进安全与基础设施
- **ZeroClaw**：50/50，安全审计与 RFC 治理，4% 合并率反映严格审查
- **PicoClaw**：2/7，中等活跃，安全边界持续收紧

**第三梯队（活跃度不足）：**
- **Moltis**：3/2，Apple Container 问题聚集，PR 0% 合并率
- **NullClaw**：1/1，依赖更新积压 2 个月，社区信任度风险

---

## 7. 值得关注的趋势信号

**（1）安全从"功能"变为"基础设施"**
- NanoBot（OAuth、RuntimeControl）、Hermes（凭据泄露修复）、NanoClaw（CSPRNG 配对码）、PicoClaw（远程 exec 默认禁用）均在本周密集发布安全修复
- **启示**：2026 年个人 AI 助手项目的安全审计不再是锦上添花，而是生产部署的硬性门槛

**（2）多通道消息可靠性成为技术分水岭**
- OpenClaw（重复消息 #121058）、NanoClaw（平台 ID 复用 #3226）、CoPaw（沉默 loop #3311）均暴露同类问题
- **启示**：消息去重、ID 幂等性、失败重试策略是区分"玩具"与"生产级"产品的关键指标

**（3）国内 LLM 提供商兼容性倒逼格式标准化**
- CoPaw（StepFun 400 错误 #6803）、OpenClaw（Anthropic OAuth #94719）均因严格格式校验受阻
- **启示**：OpenClaw 等生态核心项目需建立"提供商兼容性适配层"，否则将失去国内市场份额

**（4）Windows 平台稳定性仍是短板**
- Hermes Agent（5 个 Windows 启动问题）、LobsterAI（pip shim 残留）、CoPaw（IME 崩溃）同时报告 Windows 相关问题
- **启示**：跨平台 AI 助手项目需建立 Windows 专项测试矩阵，尤其是 Electron/Tauri 架构项目

**（5）记忆系统从"实验"走向"生产"**
- CoPaw（ReMe reranker、Auto-Dream 容错）、NanoBot（Dream 无限循环修复）反映记忆模块进入稳定性攻坚期
- **启示**：记忆系统的 token 成本控制、循环检测、来源信任标签将成为下一版本核心竞争点

**（6）技术栈现代化提速**
- LobsterAI（Vite 5→8、React 18→19）、ZeroClaw（DAG 规划）表明头部项目已进入重大版本跃迁期
- **启示**：维护者需平衡技术债清理与功能迭代，避免因依赖过旧导致安全漏洞累积

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot 项目日报 — 2026-08-11

---

## 1. 今日速览

NanoBot 昨日（2026-08-10 ~ 2026-08-11）保持高度活跃，24 小时内共产生 **4 条 Issues**（3 已关闭、1 待处理）和 **24 条 PR**（10 已合并/关闭、14 待合并），整体处于密集迭代期。今日合并的 PR 覆盖了安全修复（Exec 路径绕过、WebSocket 认证）、Bug 修复（Dream 无限循环、文件无操作编辑）、MCP OAuth 支持和 WebUI 重构等多个方向，项目健康度良好。唯一遗留 Bug #5327 涉及推理时的消息重复，尚未有对应修复 PR，建议关注。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

### 今日合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#5316](https://github.com/HKUDS/nanobot/pull/5316) | feat(mcp) | 为远程 MCP 服务器添加浏览器 OAuth 支持，含 Xmind/Notion/Linear 预设 |
| [#5325](https://github.com/HKUDS/nanobot/pull/5325) | fix(files) | 拒绝 `edit_file` 无操作编辑，修复 Dream 记忆整理无限循环（关联 #5324） |
| [#5321](https://github.com/HKUDS/nanobot/pull/5321) | refactor(webui) | WebUI 设置服务由 Gateway 统一管理，OAuth 状态移入 gateway 作用域 |
| [#5319](https://github.com/HKUDS/nanobot/pull/5319) | refactor(agent) | 以显式 `RuntimeControl` 协议替换反射式运行时状态访问，提升安全性 |
| [#5318](https://github.com/HKUDS/nanobot/pull/5318) | refactor(webui) | 提取确定性事件投影工具函数，推理完成时间改为显式输入 |
| [#5317](https://github.com/HKUDS/nanobot/pull/5317) | fix(webui) | WebUI 状态变更迁移至认证 WebSocket，拒绝未认证 GET 修改操作 |
| [#5315](https://github.com/HKUDS/nanobot/pull/5315) | fix(webui) | 改善 UX 恢复流程与空状态，简化认证挑战 UI |
| [#5310](https://github.com/HKUDS/nanobot/pull/5310) | fix(weixin) | 强制微信登录现在执行全新 QR 流程，彻底跳过缓存凭证 |

**整体评价：** 今日合并的 10 条 PR 以重构和安全加固为主轴（5 条），辅以关键 Bug 修复（3 条）和功能补充（2 条）。WebUI 架构正向"Gateway 统一治理"演进，MCP 安全与 OAuth 能力补齐，项目正在从"能用"向"安全可靠"迈进。

---

## 4. 社区热点

### 高关注度 Issue / PR

- **[#5297](https://github.com/HKUDS/nanobot/issues/5297) — MCP 增加 OAuth 网页授权**（已关闭）  
  用户请求对需要网页 OAuth 的 MCP（如 XMind）提供网关远程授权能力。该诉求已被 PR #5316 闭环实现，体现了社区反馈→开发的高效迭代。

- **[#5324](https://github.com/HKUDS/nanobot/issues/5324) — Dream 记忆整理无限循环**（已关闭）  
  2026-08-10 下午，Dream 任务异常运行 23 分钟、消耗超 10M token（约半个月用量）。根本原因是 `edit_file` 接受无操作编辑后触发无限循环，已由 PR #5325 修复。

- **[#5300](https://github.com/HKUDS/nanobot/issues/5300) — MCP 连接失败引发 anyio cancel scope 崩溃**（已关闭）  
  远程 MCP 返回 HTTP 530 时，anyio cancel scope 跨任务退出导致网关进程崩溃、CPU 飙升。此问题揭示了 MCP 异常处理路径的健壮性不足。

- **[#5327](https://github.com/HKUDS/nanobot/issues/5327) — 推理时重复输出相同消息**（待处理）  
  用户报告 Nanobot 在推理过程中随机重复 "Good points, let me investigate the issue" 等短语，尚无对应修复 PR，是今日最值得关注的遗留问题。

- **[#5179](https://github.com/HKUDS/nanobot/pull/5179) — MCP SDK 升级至 v2**（待合并，P1）  
  将 MCP 客户端从 v1 `ClientSession` 迁移至 v2 `Client` API，同时保留 SSRF 校验、DNS 固定等安全特性，并与旧版 SSE 兼容。该 PR 已有冲突，需维护者尽快处理。

---

## 5. Bug 与稳定性

| 严重度 | Issue / PR | 描述 | Fix 状态 |
|---|---|---|---|
| 🔴 P0 | [#5327](https://github.com/HKUDS/nanobot/issues/5327) | 推理时随机重复同一消息 | ❌ 无修复 PR |
| 🔴 P1 | [#5324](https://github.com/HKUDS/nanobot/issues/5324) | Dream 记忆整理无限循环，消耗 10M+ token | ✅ PR #5325 已合并 |
| 🟡 P2 | [#5300](https://github.com/HKUDS/nanobot/issues/5300) | MCP 异常导致 cancel scope 崩溃 + 任务泄漏 | ❌ 无直接修复 PR（需 MCP 升级后评估） |
| 🟡 P2 | [#5271](https://github.com/HKUDS/nanobot/pull/5271) | 后台任务保存覆盖会话数据（待合并） | ⏳ PR #5271 待合并 |
| 🟡 P2 | [#5257](https://github.com/HKUDS/nanobot/pull/5257) | 持续目标在空闲时不受周期限制（待合并） | ⏳ PR #5257 待合并 |

**稳定性评估：** 关键无限循环 Bug 已修复，但 P0 消息重复问题和新提交的两个 P2 会话/目标控制 Bug 仍待处理。PR #5179（MCP v2 升级）合并后有望同步缓解 #5300 的异常处理问题。

---

## 6. 功能请求与路线图信号

| 请求 / 信号 | 来源 | 状态 | 纳入预期 |
|---|---|---|---|
| MCP 远程服务器浏览器 OAuth | #5297 → PR #5316 | ✅ 已合并 | 已发布 |
| OrcaRouter 模型路由网关支持 | PR #5328 | 🔄 待合并 | 高可能性，扩展 Provider 矩阵 |
| WebUI 标签页工作台 | PR #5322 | 🔄 待合并 | 中等，重大 UX 变更需回归测试 |
| 结构化 Token 用量记录 | PR #5299 | 🔄 待合并 | 高可能性，满足开发者诊断需求 |
| Agent Plugins + CLI Apps 集成 | PR #5288 | 🔄 待合并 | 中等，插件生态建设 |
| Matrix 房间级响应修复 | PR #5292 | 🔄 待合并 | 高可能性，修复已知缺陷 |

**路线图解读：** 当前迭代聚焦于**安全加固**（OAuth、认证 WebSocket、权限收缩）和**架构清理**（Gateway 统一治理、设置服务拆分），同时稳步推进 MCP v2 迁移和 Provider 生态扩展。WebUI 标签页工作台是下一版本最显著的用户体验升级。

---

## 7. 用户反馈摘要

- **MCP OAuth 授权刚需：** 用户明确提到 XMind MCP 等需要网页授权的服务无法配置，推动了 PR #5316 的快速实现。
- **Token 消耗失控引发焦虑：** #5324 用户发现 Dream 任务 23 分钟消耗半个月用量，反映对后台任务缺乏熔断机制的担忧。
- **推理重复消息影响体验：** #5327 用户报告随机重复短语，虽然不影响功能但严重影响交互流畅度。
- **MCP 异常导致网关崩溃：** #5300 用户遭遇任意 MCP 异常时整个网关进程崩溃/卡死，凸显了隔离机制的缺失。
- **微信登录凭证缓存问题：** #5310 修复前，强制重新登录时可能恢复旧账号，用户期望彻底干净的 QR 流程。

---

## 8. 待处理积压

| 类型 | ID | 说明 | 建议 |
|---|---|---|---|
| 🐛 Bug (P0) | [#5327](https://github.com/HKUDS/nanobot/issues/5327) | 推理时随机重复消息，无修复 PR | 优先排期，可能源于流式输出缓冲逻辑 |
| 🔀 PR (P1) | [#5179](https://github.com/HKUDS/nanobot/pull/5179) | MCP v2 迁移，存在冲突 | 尽快解决冲突，合并后可缓解 #5300 |
| 🔀 PR (P2) | [#5271](https://github.com/HKUDS/nanobot/pull/5271) | 防止后台任务覆盖会话数据 | 建议优先合并，修复 P2 数据一致性 Bug |
| 🔀 PR (P2) | [#5257](https://github.com/HKUDS/nanobot/pull/5257) | 持续目标空闲时无周期限制 | 建议合并，防止 token 浪费 |
| 🔀 PR (P2) | [#5322](https://github.com/HKUDS/nanobot/pull/5322) | WebUI 标签页工作台 | 功能性强，需充分回归测试 |
| 🔀 PR (P2) | [#5299](https://github.com/HKUDS/nanobot/pull/5299) | 结构化 Token 用量记录 API | 低风险提示合并 |
| 🔀 PR (P1) | [#5329](https://github.com/HKUDS/nanobot/pull/5329) | 修复 ExecTool 路径绕过（安全） | P1 安全修复，建议优先处理 |

---

*报告生成时间：2026-08-11 | 数据来源：HKUDS/nanobot GitHub*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent 项目日报 — 2026-08-11

## 1. 今日速览

过去24小时 Hermes Agent 项目保持高活跃度：**50 条 Issue 更新、50 条 PR 更新**，整体代码贡献与问题追踪节奏稳健。当日无新版本发布，主要工作集中在三项并行主线：**（1）god-file 大规模重构**（#78647 Epic 驱动，单日发起多个 shard PR）；**（2）Windows Desktop 启动问题集中爆发**（至少 5 个相关问题同时出现，已有多条修复 PR 跟进）；**（3）子进程凭据泄露安全修复**（#77164、#82936、#83565 Campaign Epic）。整体项目健康度良好，但 Windows 平台稳定性与安全问题需重点跟进。

---

## 2. 版本发布

今日无新版本发布。

---

## 3. 项目进展

### 已合并/关闭的重要 PR（5 条）

| PR | 作者 | 内容 |
|----|------|------|
| [#67626](https://github.com/NousResearch/hermes-agent/pull/67626) | Hotragn | 修复 turn-lease idle predicate 的 waiter-aware 问题，加固会话状态管理 |
| [#83597](https://github.com/NousResearch/hermes-agent/pull/83597) | hadelive | Skills 安装支持锁定至 GitHub commit SHA，提供完整的锁来源与失败闭环 |
| [#81533](https://github.com/NousResearch/hermes-agent/pull/81533) | Enough1122 | 为所有 BrowserWindow 实例附加渲染器生命周期诊断，修复 Windows 黑窗问题 |
| [#82676](https://github.com/NousResearch/hermes-agent/pull/82676) | JoaoMarcos44 | 为 gateway final-send suppression 建立行为矩阵测试，确认不变量契约 |
| [#83567](https://github.com/NousResearch/hermes-agent/pull/83567) | teknium1 | 全面修复 Desktop 多窗口崩溃恢复，覆盖 secondary/instance/HUD/overlay 等窗口类型 |

**今日推进总结**：5 条合并 PR 覆盖会话状态安全、skills 锁机制、Windows Desktop 稳定性与测试契约，整体向前推进在**平台稳定性**和**核心机制可靠性**两个维度上。

---

## 4. 社区热点

| Issue/PR | 评论数 | 热度分析 |
|----------|--------|----------|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — Epic: Shard all 20 god files | 66 | 本周最大讨论焦点。`main` 分支累积 20 个 god file（单文件 7000+ 行），社区强烈支持模块化重构，单日已衍生出 #78640（gateway.py）、#78641（conversation_loop.py）、#78642（mcp_tool.py）、#78643（api_server.py）等多个 shard PR，说明重构已进入执行阶段。 |
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) — Solving the Multi-Tenant Hermes Problem | 21 | 多租户核心痛点。Memory 操作绕过了 hook 系统，导致 tenant 隔离无法实现。已有用户在生产环境运行修复版本。 |
| [#77164](https://github.com/NousResearch/hermes-agent/issues/77164) — child-process env scrub is name-shape heuristic | 4 | 安全漏洞：凭据清理仅通过名称形状启发式匹配，非凭据形状的敏感值会泄露到子进程。与 #82936、#83565 形成安全修复链。 |
| [#83555](https://github.com/NousResearch/hermes-agent/issues/83555) — Windows parent-death watchdog 误触发 | 2 | 多条修复 PR 已在路上（#83611、#83604），社区反馈快速且配合度高。 |

---

## 5. Bug 与稳定性

### P1 — 严重

| Issue | 描述 | 状态 | Fix PR |
|-------|------|------|--------|
| [#83312](https://github.com/NousResearch/hermes-agent/issues/83312) | DeepSeek 返回 `tool_calls: []` 导致会话永久挂起（HTTP 400） | OPEN | [#83600](https://github.com/NousResearch/hermes-agent/pull/83600)（已开） |
| [#77276](https://github.com/NousResearch/hermes-agent/issues/77276) | Desktop 重启后遗留孤儿 gateway（CLI 重启路径未覆盖） | CLOSED | ✅ 已合并 |
| [#77463](https://github.com/NousResearch/hermes-agent/issues/77463) | 子进程 env scrub 绕过：TUI、LSP、docker 多处 post-scrub 泄露 | OPEN | 关联 #83565 Campaign |

### P2 — 高

| Issue | 描述 | 状态 | Fix PR |
|-------|------|------|--------|
| [#82936](https://github.com/NousResearch/hermes-agent/issues/82936) | `multiplex_profiles` 下默认 profile 凭据泄露到 secondary profile | OPEN | 关联 #83565 |
| [#83569](https://github.com/NousResearch/hermes-agent/issues/83569) | Windows `hermes update` 锁定 `cryptography._rust.pyd`，更新 100% 失败 | OPEN | — |
| [#83548](https://github.com/NousResearch/hermes-agent/issues/83548) | Windows Desktop 更新后崩溃，无法启动 | OPEN | 关联 #83611 |
| [#83583](https://github.com/NousResearch/hermes-agent/issues/83583) | Windows 每次启动 parent-death watchdog 误触发，backend 立即退出 | OPEN | [#83611](https://github.com/NousResearch/hermes-agent/pull/83611)、[#83604](https://github.com/NousResearch/hermes-agent/pull/83604) |
| [#83573](https://github.com/NousResearch/hermes-agent/issues/83573) | `curator adopt --dry-run` 对已 adopt 的 skill 错误报告 | OPEN | [#83613](https://github.com/NousResearch/hermes-agent/pull/83613) |
| [#83580](https://github.com/NousResearch/hermes-agent/issues/83580) | curator-archived skills 不可恢复（`restore` 路径命名不匹配） | OPEN | [#83613](https://github.com/NousResearch/hermes-agent/pull/83613) |
| [#83562](https://github.com/NousResearch/hermes-agent/issues/83562) | Windows Desktop 更新后端 `exited (0)`，修复安装无效 | OPEN | 关联 #83611 |
| [#81547](https://github.com/NousResearch/hermes-agent/issues/81547) | macOS dashboard fd leak，长时间运行后 `Too many open files` | CLOSED | ✅ 已修复 |

**今日 Bug 热点**：Windows Desktop 启动问题形成集群（#83555/#83583/#83548/#83562/#83603），根本原因为 parent-death watchdog 在 Windows uv trampoline venv 场景下误判父进程死亡，已有 2 条修复 PR（#83611、#83604）处于开放状态。

---

## 6. 功能请求与路线图信号

| Issue/PR | 类型 | 内容 | 纳入概率 |
|----------|------|------|----------|
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) | feature | 多租户 Hermes 完整支持（Memory 绕过 hook 是核心障碍） | ⭐⭐⭐ 高，生产用户已反馈 |
| [#83522](https://github.com/NousResearch/hermes-agent/issues/83522) | feature | Gateway 内置自愈合（SIGTERM 后干净重启 + 死 WebSocket 检测） | ⭐⭐⭐ 高，Discord 用户刚需 |
| [#66178](https://github.com/NousResearch/hermes-agent/pull/66178) | feature | `hermes release-notes` 交互式版本查看命令 | ⭐⭐ 中，PR 已开待审 |
| [#83504](https://github.com/NousResearch/hermes-agent/pull/83504) | feature | Slack 频道级成员启动权限（无需 DM 访问） | ⭐⭐ 中，PR 已开待审 |
| [#83523](https://github.com/NousResearch/hermes-agent/pull/83523) | fix | 1M context 会话不再将压缩推迟到 500K，改为 256K 触发 | ⭐⭐⭐ 高，大型模型用户受益 |

**路线图信号**：安全加固（凭据继承）、Windows 稳定性、多租户支持是当前三大战场；重构主线（god-file shard）按计划推进，预计未来数周持续产出。

---

## 7. 用户反馈摘要

| 痛点 | 来源 | 反馈摘要 |
|------|------|----------|
| Windows 更新后 Desktop 无法启动 | #83548, #83555, #83562 | "修复安装多次尝试均无效"、"backend 退出代码 0，从未打印 HERMES_BACKEND_READY" |
| 子进程凭据泄露 | #77164, #82936, #77463 | "secondary profile 配置的 least-privilege 策略被默认 profile 凭据破坏" |
| god file 维护困难 | #78647 | 66 条评论，社区共识：重构刻不容缓，单个文件 7000+ 行影响可维护性 |
| DeepSeek 兼容性 | #83312 | "一个空 tool_calls[] 导致整个会话永久挂起，且无任何恢复路径" |
| curator 技能归档不可逆 | #83580 | "62 个 archived skills 中有 51 个无法通过 CLI 恢复" |
| Langfuse 插件静默失败 | #60961 | "placeholder API key 不报错也不产生 trace，难以排查" |
| 多租户隔离 | #34352 | "我们在生产环境运行了数月的修复方案，期待上游支持" |

**满意点**：修复速度较快（Windows watchdog 问题当日即有 PR 跟进）、repro 信息详尽、社区协作活跃。

---

## 8. 待处理积压

| Issue/PR | 龄期 | 风险 | 建议 |
|----------|------|------|------|
| [#77463](https://github.com/NousResearch/hermes-agent/issues/77463) — 子进程 env scrub 绕过（Critical） | 8 天 | 凭据泄露覆盖 TUI/LSP/Docker 多路径 | 优先合并关联 PR |
| [#77164](https://github.com/NousResearch/hermes-agent/issues/77164) — name-shape heuristic 泄露 | 8 天 | 安全边界问题 | 纳入 #83565 Campaign 统一修复 |
| [#83569](https://github.com/NousResearch/hermes-agent/issues/83569) — Windows update 锁定 .pyd | 当天 | 更新完全阻塞 | 待 PR 合并后验证 |
| [#5908](https://github.com/NousResearch/hermes-agent/issues/5908) — kimi-coding base_url 未重新解析 | 4 个月 | 2 👍 | 需确认优先级 |
| [#81518](https://github.com/NousResearch/hermes-agent/issues/81518) — 代理后连接池积累导致 TTFB 20-219s | 3 天 | Cron/委托调用不稳定 | 需复现环境 |

---

**报告生成时间**：2026-08-11 | **数据范围**：过去 24 小时

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw 项目动态日报
**日期：2026-08-11 | 数据周期：过去 24 小时**

---

## 1. 今日速览

过去 24 小时 PicoClaw 项目保持中等活跃度：7 条 PR 被关闭/合并，2 条 PR 和 2 条 Issue 仍保持开放状态，无新版本发布。项目焦点集中在安全加固（远程 prompt/exec 边界）、Telegram 表格渲染体验优化、以及 tool 调用失败循环修复三个方向。Issues 方面出现 2 个新问题，涉及 dispatch rules 路由场景下的 session 管理缺陷和 model list 展示异常，反映出多代理路由和多模型配置场景的用户需求正在增长。

---

## 2. 版本发布

无新版本发布。

---

## 3. 项目进展

今日合并/关闭的 PR 共 7 条，覆盖安全、渠道体验、国际化与配置三个方向：

- **#3297** — 安全加固：将远程发送者和聊天元数据从 provider system instructions 中剥离，默认禁用远程 exec，要求逐调用独立批准，并强制执行 origin policy。同步迁移配置至 schema v4。`https://github.com/sipeed/picoclaw/pull/3297`
- **#3327** — Telegram 表格渲染：使用 Bot API 原生 rich messages 渲染 GFM 表格和 HTML `<table>`，替代原先的等宽代码块形式。`https://github.com/sipeed/picoclaw/pull/3327`
- **#3295** — 渠道修复：解决 `SplitMessage` 在 fenced-code info string 超过 `maxLen` 时挂起的问题，引入降级有界原始分割确保进度。`https://github.com/sipeed/picoclaw/pull/3295`
- **#3296** — 国际化：补全捷克语（cs）代码包装相关标签。`https://github.com/sipeed/picoclaw/pull/3296`
- **#2132** — 配置增强：解耦 lookup key 与 runtime modelID，支持 model-specific 的 `max_tokens` 等参数覆盖，修复 `GetModelConfig()` 查找异常。`https://github.com/sipeed/picoclaw/pull/2132`
- **#3326** — 构建修复：移除 `pnpm-lock.yaml` 中重复的 `semver@7.8.5` 条目，解决 `ERR_PNPM_BROKEN_LOCKFILE`。`https://github.com/sipeed/picoclaw/pull/3326`
- **#1547** — 合并 PR #1466 和 #1465 的历史修复。`https://github.com/sipeed/picoclaw/pull/1547`

**整体判断：** 今日进展以安全和体验优化为主，安全边界收紧是明显信号，Telegram 渠道体验持续改进，多模型配置灵活性得到增强。

---

## 4. 社区热点

| Issue / PR | 状态 | 评论数 | 关注点 |
|---|---|---|---|
| [#3301](https://github.com/sipeed/picoclaw/issues/3301) | OPEN | 3 | dispatch rules 路由至非默认 agent 时 `/clear` 和 session 自动压缩失效 |
| [#3311](https://github.com/sipeed/picoclaw/issues/3311) | OPEN | 1 | 相同 tool 反复失败时陷入 silent loop 直至 `max_tool_iterations`，用户无响应 |
| [#3314](https://github.com/sipeed/picoclaw/pull/3314) | OPEN | — | 修复 `customAllowPatterns` 不生效（默认拒绝模式优先级过高） |
| [#3312](https://github.com/sipeed/picoclaw/pull/3312) | OPEN | — | 修复重复相同 tool 失败时提前终止 turn 的循环问题 |

**分析：** 热点集中在两个方向：一是 **dispatch rules 路由场景的 session 管理缺陷**（#3301），反映多 agent 路由用户增多后暴露的边界问题；二是 **tool 调用失败重试策略的鲁棒性**（#3311/#3312），该问题影响用户体验最直观（消息发出去无响应），且已有对应 fix PR 待合并。

---

## 5. Bug 与稳定性

| 问题 | 严重程度 | Issue | Fix PR | 状态 |
|---|---|---|---|---|
| 重复相同 tool 失败陷入 silent loop | 🔴 高 | [#3311](https://github.com/sipeed/picoclaw/issues/3311) | [#3312](https://github.com/sipeed/picoclaw/pull/3312) | fix PR 待合并 |
| `/clear` 和 session 压缩在 non-default agent 路由下失效 | 🟡 中 | [#3301](https://github.com/sipeed/picoclaw/issues/3301) | — | 无 fix |
| `/list models` 仅显示当前模型而非全部配置 | 🟢 低 | [#3294](https://github.com/sipeed/picoclaw/issues/3294) | — | 已关闭，推测已修复 |
| `SplitMessage` 超大 fence header 挂起 | 🟡 中 | — | [#3295](https://github.com/sipeed/picoclaw/pull/3295) | 已修复 |

---

## 6. 功能请求与路线图信号

- **#3298**（已关闭）— 请求将 AI Router 作为 OpenAI-compatible provider preset 内置支持。作者为 AI Router 维护者，提出 affiliation disclosure。该 issue 已关闭但未见对应 PR，可能以 Generic OpenAI provider 方式被接受，或暂不纳入。`https://github.com/sipeed/picoclaw/issues/3298`
- **#2132**（已合并）— model-specific `max_tokens` 及配置键修复已合入，多模型精细化配置能力增强。`https://github.com/sipeed/picoclaw/pull/2132`
- **#3327**（已合并）— Telegram 原生表格渲染已合入，渠道体验持续优化方向明确。

**判断：** 多模型配置精细化、Telegram 渠道体验、安全边界收紧是当前明确的演进方向。

---

## 7. 用户反馈摘要

- **多代理路由场景痛点**：#3301 用户在使用 dispatch rules 将聊天路由至非默认 agent 时，`/clear` 命令和 session 自动压缩均失效，影响长时间对话管理体验。
- **多模型配置预期落差**：#3294 用户配置了多个模型，但 `/list models` 仅显示当前模型，与命令名称和描述不符，属于明显的 UX 不一致。
- **工具调用失败无反馈**：#3311 用户在 Telegram 上使用 git 命令时，agent 静默执行多次失败调用后仍无回复，用户完全无感知，体验极差。
- **安全加固获得认可**：#3297 的安全边界收紧修复覆盖远程 prompt 注入和 exec 执行控制，符合生产环境安全诉求。

---

## 8. 待处理积压

| 条目 | 类型 | 创建时间 | 积压天数 | 备注 |
|---|---|---|---|---|
| [#3301](https://github.com/sipeed/picoclaw/issues/3301) | Bug | 2026-07-29 | ~13 天 | dispatch rules 场景 session 管理缺陷，无 fix PR |
| [#3314](https://github.com/sipeed/picoclaw/pull/3314) | Bug Fix | 2026-08-03 | ~8 天 | `customAllowPatterns` 失效修复，待合并 |
| [#3312](https://github.com/sipeed/picoclaw/pull/3312) | Bug Fix | 2026-08-02 | ~9 天 | tool 失败循环修复，待合并 |

**建议关注：** #3301 已积压超过两周且为中等严重程度 bug，建议维护者优先评估；#3312 和 #3314 两个 fix PR 可合并推进，修复当日最活跃的两个用户反馈问题。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw 项目动态日报
**日期：2026-08-11** | 数据来源：[NanoClaw GitHub](https://github.com/qwibitai/nanoclaw)

---

## 1. 今日速览

过去24小时内，NanoClaw 项目保持**高活跃度**，共产生 **3 条 Issue** 与 **20 条 PR**，其中 PR 合并/关闭率达 50%（10/20），显示核心贡献团队推进效率较高。当日无新版本发布，但多项基础设施重构与安全修复已落地，同时围绕 Telegram 配对机制、会话持久化、远程 MCP 服务器支持等关键模块持续迭代。项目整体处于**稳健演进阶段**，安全与稳定性改进是今日主要焦点。

---

## 2. 版本发布

**无新版本发布。**

---

## 3. 项目进展

### 今日已合并/关闭的 PR（共 10 条）

| PR | 类型 | 摘要 | 影响 |
|----|------|------|------|
| [#3228](https://github.com/nanocoai/nanoclaw/issues/3228) | Fix | 去重 turn-scoped chat delivery | 修复重复消息投递问题 |
| [#3222](https://github.com/nanocoai/nanoclaw/pull/3222) | Feature | 可选隐私安全 DM 日志 | 增强隐私保护能力 |
| [#3215](https://github.com/nanocoai/nanoclaw/pull/3215) | Fix | 红act DM 解析日志 | 减少日志中的敏感信息暴露 |
| [#3216](https://github.com/nanocoai/nanoclaw/pull/3216) | Docs | 说明 `install_packages` 仅支持 apt/npm | 消除文档歧义 |
| [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) | Refactor | 为 skill 能力添加 host 扩展点 | 为插件化架构铺路 |
| [#3213](https://github.com/nanocoai/nanoclaw/pull/3213) | Refactor | 注册问题渲染器 | 统一 UI 渲染逻辑 |
| [#3214](https://github.com/nanocoai/nanoclaw/pull/3214) | Refactor | 统一模块生命周期钩子 | 降低模块管理复杂度 |
| [#3212](https://github.com/nanocoai/nanoclaw/pull/3212) | Refactor | 添加模块迁移注册表 | 增强数据库迁移可维护性 |
| [#3211](https://github.com/nanocoai/nanoclaw/pull/3211) | Docs | 定义单一职责集成规则 | 规范化 skill 开发标准 |
| [#3219](https://github.com/nanocoai/nanoclaw/pull/3219) | — | Telegram 与容器环境相关 | 已关闭 |

**进展评估：** 今日以**重构与安全加固**为主，共完成 4 项重构（host 扩展点、生命周期钩子、迁移注册表、渲染器注册）、2 项隐私相关修复（DM 日志红act与安全日志）、1 项核心修复（消息去重）及 2 项文档完善。项目架构整洁度与安全性得到实质性提升，为后续功能扩展奠定基础。

---

## 4. 社区热点

### 热门 Issue

| Issue | 标题 | 作者 | 评论 | 热度分析 |
|-------|------|------|------|----------|
| [#3075](https://github.com/nanocoai/nanoclaw/issues/3075) | 长时间运行后日志静默丢失 + 入站消息重复插入错误 | libellebilai-collab | 1 | 涉及 WSL2/Docker 部署场景，运维稳定性痛点，有 1 条评论说明已引发关注 |
| [#3226](https://github.com/nanocoai/nanoclaw/issues/3226) | 平台复用 message id 时入站消息被静默丢弃 | dweekly | 0 | 直接 UX 影响（用户感知为"agent 忽略消息"），与 #3224 PR 形成对应 |
| [#3223](https://github.com/nanocoai/nanoclaw/issues/3223) | 定时任务错误产生无法路由的消息，操作员无感知 | chiptoe-svg | 0 | 运维可观测性缺陷，影响生产环境任务监控 |

### 热门 PR

| PR | 标题 | 作者 | 关注点 |
|----|------|------|--------|
| [#3229](https://github.com/nanocoai/nanoclaw/pull/3229) | Telegram 配对码改用 CSPRNG 生成 | chiptoe-svg | 安全修复，配对码强度从 4 位扩展，与 #3225 互补 |
| [#3224](https://github.com/nanocoai/nanoclaw/pull/3224) | 修复平台 ID 复用导致入站消息丢失 | dweekly | 直接修复 #3226 提出的 bug |
| [#3225](https://github.com/nanocoai/nanoclaw/pull/3225) | 加固 Telegram 配对码生成与存储权限 | dweekly | 安全加固，文件系统权限修复 |
| [#3092](https://github.com/nanocoai/nanoclaw/pull/3092) | 支持远程 Streamable HTTP MCP 服务器 | amit-shafnir | 核心功能扩展，影响 codex/opencode 集成 |

**热点分析：** 社区今日关注集中在**消息可靠性**（#3226/#3224）与**安全加固**（#3229/#3225）两个维度，反映出用户对生产环境稳定性与安全的重视。远程 MCP 服务器支持（#3092）作为长期功能请求，持续获得推进。

---

## 5. Bug 与稳定性

### 今日报告的问题（按严重程度排列）

| 级别 | Issue | 描述 | Fix PR |
|------|-------|------|--------|
| 🔴 高 | [#3226](https://github.com/nanocoai/nanoclaw/issues/3226) | 平台复用 message id 导致入站消息静默丢失，用户无感知 | [#3224](https://github.com/nanocoai/nanoclaw/pull/3224)（已提交，待合并） |
| 🔴 高 | [#3223](https://github.com/nanocoai/nanoclaw/issues/3223) | 定时任务错误产生无法路由的消息，操作员完全无法感知失败 | 尚无对应 PR |
| 🟡 中 | [#3075](https://github.com/nanocoai/nanoclaw/issues/3075) | 长时间运行后日志丢失 + 消息重复插入，WSL2/Docker 环境 | 尚无对应 PR |
| 🟡 中 | — | Telegram 配对码使用 `Math.random()`（可预测） | [#3229](https://github.com/nanocoai/nanoclaw/pull/3229) + [#3225](https://github.com/nanocoai/nanoclaw/pull/3225)（已提交） |

**稳定性评估：** 今日新增 3 个 Issue，其中 2 个高严重度问题（消息丢失、错误不可观测）直接影响生产可用性。好消息是 #3226 已有对应 Fix PR（#3224），Telegram 安全问题也有双 PR 覆盖。但 #3223 和 #3075 尚缺修复方案，需优先跟进。

---

## 6. 功能请求与路线图信号

| 功能方向 | 相关 PR/Issue | 状态 | 纳入下一版本可能性 |
|----------|---------------|------|---------------------|
| 远程 Streamable HTTP MCP 服务器 | [#3092](https://github.com/nanocoai/nanoclaw/pull/3092), [#3221](https://github.com/nanocoai/nanoclaw/pull/3221) | 核心团队推进中 | ⭐⭐⭐⭐⭐ 高 |
| Agent 模板 → Agent Plugins 1.0.0 目录格式 | [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) | 核心团队，破坏性变更 | ⭐⭐⭐⭐ 较高 |
| 模板向导与首次 agent 生成流程 | [#2909](https://github.com/nanocoai/nanoclaw/pull/2909) | 核心团队，等待合并 | ⭐⭐⭐⭐ 较高 |
| CLI 从 stdin 接收结构化 JSON 输入 | [#3218](https://github.com/nanocoai/nanoclaw/pull/3218) | 待合并 | ⭐⭐⭐ 中等 |
| 隐私安全 DM 日志 | [#3222](https://github.com/nanocoai/nanoclaw/pull/3222) | 已合并 | ✅ 已包含 |
| Telegram 富消息支持 | [#3193](https://github.com/nanocoai/nanoclaw/pull/3193) | 待合并 | ⭐⭐⭐ 中等 |

**路线图信号：** 项目正从"模板"体系向"Agent Plugins 1.0.0"目录格式迁移（#3220），这是架构级变更。远程 MCP 服务器支持（#3092/#3221）是今日最活跃的功能扩展，预计将在近期版本中作为核心能力发布。

---

## 7. 用户反馈摘要

### 真实痛点

| 痛点 | 来源 | 用户场景 |
|------|------|----------|
| **"agent 忽略了我"但实际是消息被丢弃** | #3226 | 长期运行的 agent 会话中，平台复用 message id 导致消息静默丢失，用户完全无感知，归因错误地指向 agent 行为 |
| **定时任务失败无告警** | #3223 | 生产环境中 scheduled task 出错后，错误消息无法路由，运维人员完全无法得知任务失败，缺乏可观测性 |
| **长时间运行后日志丢失 + 重复插入** | #3075 | WSL2/Docker 部署场景下，长时间运行后出现日志静默丢失和消息重复插入，影响审计与调试 |
| **Telegram 配对码可预测** | #3229/#3225 | 配对码使用 `Math.random()` 生成，存在安全风险，且存储目录权限过宽 |

### 满意度信号

- **隐私日志需求得到响应**：#3222 实现了可选的隐私安全 DM 日志，用户可主动选择是否保留用户 ID 等敏感信息
- **文档澄清**：#3216 明确了 `install_packages` 仅支持 apt/npm 的限制，减少用户误用
- **架构清晰化**：#3211 定义了单一职责集成规则，帮助开发者更好地理解 skill 开发规范

---

## 8. 待处理积压

### 需优先关注的 Issue

| Issue | 标题 | 创建时间 | 未响应时长 | 建议优先级 |
|-------|------|----------|------------|------------|
| [#3223](https://github.com/nanocoai/nanoclaw/issues/3223) | 定时任务错误消息无法路由，操作员无感知 | 2026-08-10 | 今日新报 | 🔴 高 — 影响生产可观测性，建议尽快分配开发资源 |
| [#3075](https://github.com/nanocoai/nanoclaw/issues/3075) | 长时间运行后日志丢失 + 消息重复插入 | 2026-07-17 | 25 天 | 🟡 中高 — WSL2/Docker 部署场景的稳定性和调试工具链问题 |

### 待合并的重要 PR

| PR | 标题 | 创建时间 | 状态 | 建议 |
|----|------|----------|------|------|
| [#3224](https://github.com/nanocoai/nanoclaw/pull/3224) | 修复平台 ID 复用导致入站消息丢失 | 2026-08-10 | 待合并 | 🔴 高 — 直接修复 #3226，建议优先合并 |
| [#3229](https://github.com/nanocoai/nanoclaw/pull/3229) | Telegram 配对码改用 CSPRNG | 2026-08-10 | 待合并 | 🟡 中 — 安全修复 |
| [#3225](https://github.com/nanocoai/nanoclaw/pull/3225) | 加固 Telegram 配对码与存储权限 | 2026-08-10 | 待合并 | 🟡 中 — 安全修复，与 #3229 互补 |
| [#3092](https://github.com/nanocoai/nanoclaw/pull/3092) | 支持远程 Streamable HTTP MCP 服务器 | 2026-07-19 | 待合并 | ⭐⭐⭐⭐ 高 — 核心功能，已维护 23 天 |
| [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) | Agent 模板 → Plugins 1.0.0 目录格式 | 2026-08-10 | 待合并 | ⭐⭐⭐⭐ 高 — 架构级变更，影响后续开发 |

---

**报告生成时间：** 2026-08-11 | **分析师：** Agnes (Sapiens AI)

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw 项目日报 — 2026-08-11

## 1. 今日速览

NullClaw 今日整体活跃度偏低，过去 24 小时仅处理 1 条 Issue 并关闭，同时有 1 条 PR 待合并，无新版本发布。项目仍以维护型节奏运行，核心贡献集中在依赖安全更新与 A2A 协议客户端工具的需求确认上。Issue #700 的关闭表明该功能需求已获维护者认可或已在其他分支解决，项目健康度总体稳定但开发动力偏弱。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

- **PR #956**（待合并）— Dependabot 提交的 Alpine 镜像从 3.23 升级至 3.24（`docker-images` 组），属于基础安全与维护性更新，不涉及功能变更。该 PR 尚未合并，若维护者未及时响应，依赖漏洞可能持续存在风险。

- **Issue #700**（已关闭）— 用户 georgeglarson 提出的 `a2a_call` 客户端工具需求已关闭，意味着维护者可能已通过其他方式解决了该诉求（如合并进其他 PR 或暂不支持），但关闭时未附上详细解释，透明度有待提升。

## 4. 社区热点

| 类型 | 编号 | 标题 | 链接 |
|------|------|------|------|
| Issue | #700 | Add a2a_call client tool for calling remote agents | [Issue #700](https://github.com/nullclaw/nullclaw/issues/700) |

- **热度分析**：该 Issue 获得 1 个 👍 和 1 条评论，讨论规模较小但诉求明确。用户描述了多实例部署场景（公共 doorman + 私有个人代理）下的 Agent-to-Agent 调用需求，反映出 nullclaw 在 A2A 协议生态中作为服务端已实现，但客户端工具链存在空白。关闭此 Issue 未附说明可能影响社区信任。

## 5. Bug 与稳定性

今日无新 Bug 报告，无崩溃或回归问题记录。

## 6. 功能请求与路线图信号

- **A2A 客户端工具**（Issue #700）：用户明确提出需要 `a2a_call` 工具来发送 `message/send` JSON-RPC 请求到远程 Agent，以支持多 nullclaw 实例间通信。该需求已关闭，但关闭原因不明，建议社区关注是否有替代方案或待合并 PR。

- **容器依赖现代化**（PR #956）：Alpine 版本升级是被动维护行为，无新功能信号。

## 7. 用户反馈摘要

- **georgeglarson** 的真实使用场景：运行两个 nullclaw 实例（一个面向公众的 doorman，一个私有个人 Agent），需要在它们之间进行 A2A 协议通信。当前 nullclaw 仅支持服务端角色，缺乏客户端实现，限制了多 Agent 协作场景。

- **满意度信号**：Issue 已关闭但未获解释，可能引发用户不满；依赖更新 PR 无评论，说明社区关注度低。

## 8. 待处理积压

| 类型 | 编号 | 内容 | 链接 |
|------|------|------|------|
| PR | #956 | Dependabot: Alpine 3.23 → 3.24 升级，已等待约 2 个月 | [PR #956](https://github.com/nullclaw/nullclaw/pull/956) |

- **风险提示**：PR #956 由 dependabot[bot] 于 2026-06-15 创建，截至 2026-08-10 仍未合并。长期未响应的安全依赖更新可能累积漏洞风险，建议维护者尽快处理或关闭并说明原因。

---

**项目健康度评估**：⭐⭐☆☆☆（2/5）— 活跃度低，依赖更新积压，关键 Issue 关闭透明度不足，建议维护者加强社区沟通与 PR 响应速度。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

⚠️ 摘要生成失败。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 📊 LobsterAI 项目动态日报
**日期：2026-08-11** | 数据源：LobsterAI (netease-youdao/LobsterAI)

---

## 1. 今日速览

今日 LobsterAI 项目保持**高活跃度**，过去 24 小时内共产生 35 次开发者交互（1 Issue + 34 PR），其中 20 个 PR 已合并，14 个仍待审核，代码合流节奏稳健。核心贡献者 `fisherdaddy` 持续输出，聚焦于 Cowork 协作功能增强、OpenClaw 网关稳定性修复及渲染层优化。依赖更新由 Dependabot 批量推进，涵盖 Vite 5→8、React DOM 18→19 等重大版本跃迁，技术栈现代化进程加速。项目整体健康度良好，无明显阻塞性风险。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

### ✅ 今日合并/关闭的重要 PR

| PR | 类型 | 作者 | 说明 |
|---|---|---|---|
| [#2472](https://github.com/netease-youdao/LobsterAI/pull/2472) | feat | fisherdaddy | Cowork 活动组折叠功能，提升多会话协作时的界面整洁度 |
| [#2471](https://github.com/netease-youdao/LobsterAI/pull/2471) | feat | fisherdaddy | 将 Cowork 中提交的非图片文件附件渲染为可点击卡片，统一与图片附件的展示体验 |
| [#2454](https://github.com/netease-youdao/LobsterAI/pull/2454) | fix | fisherdaddy | 修复 OpenClaw 工具循环守卫误杀合法轮询请求的 Bug |
| [#2467](https://github.com/netease-youdao/LobsterAI/pull/2467) | fix | fisherdaddy | 修复 Windows 运行时升级后残留的过期 pip shim，确保健康检查准确性 |
| [#2466](https://github.com/netease-youdao/LobsterAI/pull/2466) | fix | fisherdaddy | 修复渲染进程 IPC 初始化卡死问题，增加重试机制 |
| [#2470](https://github.com/netease-youdao/LobsterAI/pull/2470) | fix | fisherdaddy | 修复延迟聊天错误吞没真实 Provider/LLM 运行时失败的问题（如空闲超时故障转移） |
| [#2469](https://github.com/netease-youdao/LobsterAI/pull/2469) | feat | fisherdaddy | Cowork 添加折叠代理任务快捷键，并允许在输入时触发修饰键快捷键 |
| [#2468](https://github.com/netease-youdao/LobsterAI/pull/2468) | refactor | fisherdaddy | 统一流式加载指示器为单一组件，减少代码重复 |
| [#1766](https://github.com/netease-youdao/LobsterAI/pull/1766) | chore | dependabot | Vite 从 5.4.21 升级至 8.0.13 |
| [#1764](https://github.com/netease-youdao/LobsterAI/pull/1764) | chore | dependabot | react-dom 从 18.3.1 升级至 19.2.6 |
| [#1763](https://github.com/netease-youdao/LobsterAI/pull/1763) | chore | dependabot | @vitejs/plugin-react 从 4.7.0 升级至 6.0.1 |

**进展评估**：今日合并集中在 **Cowork 协作体验优化** 与 **OpenClaw 引擎稳定性修复** 两大方向，技术债清理（依赖升级）同步推进。项目向前推进明显，尤其在渲染层稳定性和协作功能丰富度上有实质提升。

---

## 4. 社区热点

### 🔥 讨论活跃 Issue/PR

| 类型 | 编号 | 标题 | 链接 |
|---|---|---|---|
| Issue | #1243 | qwen-portal-auth 插件配置循环写入导致网关频繁重启 | [链接](https://github.com/netease-youdao/LobsterAI/issues/1243) |
| PR | #2473 | 为本地文件链接添加右键上下文菜单 | [链接](https://github.com/netease-youdao/LobsterAI/pull/2473) |
| PR | #2452 | 保留斜杠模型 ID 的 Provider 前缀 | [链接](https://github.com/netease-youdao/LobsterAI/pull/2452) |

**热点分析**：
- **#1243**（已关闭）：用户报告 `qwen-portal-auth` 插件配置持续自动变更，触发网关每 5-20 分钟重启，严重影响使用。该 Issue 创建时间较长（2026-04-01），今日标记为 stale 后关闭，反映配置持久化逻辑存在缺陷，社区对网关稳定性诉求强烈。
- **#2473**（待合并）：新增右键菜单支持打开/保存/复制路径/复制内容/显示图片/在文件夹中显示等操作，提升本地文件交互体验，评论数较多表明用户对此功能期待度高。
- **#2452**（待合并）：修复自定义模型 ID 含斜杠时 Provider 前缀丢失的问题，影响 `custom_0 + deepseek-ai/DeepSeek-V4-Flash` 等组合场景，技术细节明确，维护者已介入。

---

## 5. Bug 与稳定性

### 🐛 今日 Bug 报告

| 严重度 | Issue/PR | 描述 | Fix 状态 |
|---|---|---|---|
| 🔴 高 | [#1243](https://github.com/netease-youdao/LobsterAI/issues/1243) | qwen-portal-auth 插件配置循环写入导致网关频繁重启（每 5-20 分钟） | ✅ 已关闭（stale） |
| 🟡 中 | [#2470](https://github.com/netease-youdao/LobsterAI/pull/2470) | 延迟聊天错误吞没真实 Provider/LLM 运行时失败 | ✅ 已合并 |
| 🟡 中 | [#2466](https://github.com/netease-youdao/LobsterAI/pull/2466) | 渲染进程 IPC 初始化卡死 | ✅ 已合并 |
| 🟡 中 | [#2454](https://github.com/netease-youdao/LobsterAI/pull/2454) | 工具循环守卫误杀合法轮询 | ✅ 已合并 |
| 🟢 低 | [#2467](https://github.com/netease-youdao/LobsterAI/pull/2467) | Windows pip shim 残留导致健康检查不准确 | ✅ 已合并 |

**稳定性评估**：今日关闭的 #1243 涉及网关频繁重启，属高严重度问题，但标记为 stale 后关闭而非通过代码修复解决，**潜在风险仍存在**。其余 Bug 均已通过 PR 修复，OpenClaw 引擎稳定性显著改善。

---

## 6. 功能请求与路线图信号

### 🚀 用户功能需求

| 需求 | 来源 | 路线图信号 |
|---|---|---|
| 本地文件右键操作菜单（打开/保存/复制路径等） | [#2473](https://github.com/netease-youdao/LobsterAI/pull/2473) | 已开发，待合并，反映用户对文件交互便捷性的强需求 |
| Cowork 活动组折叠与快捷键 | [#2472](https://github.com/netease-youdao/LobsterAI/pull/2472)、[#2469](https://github.com/netease-youdao/LobsterAI/pull/2469) | 已合并，表明多会话协作效率优化是近期重点 |
| 文件附件可视化卡片渲染 | [#2471](https://github.com/netease-youdao/LobsterAI/pull/2471) | 已合并，统一附件展示体验 |
| 自定义模型 ID 保留 Provider 前缀 | [#2452](https://github.com/netease-youdao/LobsterAI/pull/2452) | 待合并，满足高级用户自定义模型配置需求 |

**路线图判断**：下一版本将聚焦 **Cowork 协作体验深化** 与 **OpenClaw 引擎稳定性加固**，依赖栈现代化（Vite 8、React 19）已启动，预计后续版本会全面迁移。

---

## 7. 用户反馈摘要

### 💬 真实用户痛点

| 痛点 | 场景 | 情绪 |
|---|---|---|
| 网关频繁重启影响使用连续性 | 安装 LobsterAI 后配置任意模型，正常使用 5-20 分钟后网关自动重启，伴随"AI 引擎正在启动网关..."弹窗 | 😡 不满 |
| 非图片附件展示简陋 | Cowork 中提交的非图片文件附件显示为原始路径文本，与图片附件的丰富预览体验不一致 | 😐 中性 |
| 自定义模型 ID 含斜杠时 Provider 丢失 | 使用 `custom_0 + deepseek-ai/DeepSeek-V4-Flash` 组合时，Provider 前缀被吞没 | 😤  frustration |
| 等待延迟错误被正确上报 | LLM 空闲超时故障转移等真实运行时失败被当作陈旧通知吞没，用户无法感知 | 😡 不满 |

**满意点**：
- 文件附件卡片化渲染提升视觉一致性
- 快捷键支持增强协作效率
- 依赖升级（Vite、React）表明项目技术栈持续现代化

---

## 8. 待处理积压

### ⏳ 需关注事项

| 类型 | 编号 | 说明 | 风险 |
|---|---|---|---|
| Issue | [#1243](https://github.com/netease-youdao/LobsterAI/issues/1243) | qwen-portal-auth 配置循环写入问题以 stale 关闭，**未真正修复**，使用相同插件的用户仍可能遭遇网关重启 | 🔴 高 |
| PR | [#2473](https://github.com/netease-youdao/LobsterAI/pull/2473) | 本地文件右键菜单，待合并 | 🟢 低 |
| PR | [#2452](https://github.com/netease-youdao/LobsterAI/pull/2452) | Provider 前缀保留修复，待合并 | 🟡 中 |
| PR | [#2465](https://github.com/netease-youdao/LobsterAI/pull/2465) | Vite 升级至 8.2.1，Dependabot 维护 | 🟢 低 |
| PR | [#2464](https://github.com/netease-youdao/LobsterAI/pull/2464) | react-dom 升级至 19.2.8，Dependabot 维护 | 🟢 低 |

**维护者提醒**：Issue #1243 虽已关闭，但根本原因未解决，建议复查 `qwen-portal-auth` 插件的配置持久化逻辑，避免类似问题复发。

---

**📈 项目健康度评分：8.2/10**  
活跃度 ✅ | 合流效率 ✅ | 依赖维护 ✅ | Bug 修复 ⚠️（#1243 未实质解决）| 用户体验 ✅

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis 项目动态日报 — 2026-08-11

---

## 1. 今日速览

过去24小时 Moltis 项目保持**中等活跃度**：新增 3 条 Issue、2 条 PR，无新版本发布，无合并/关闭事件。今日 Issues 全部聚焦于 **Apple Container 后端的稳定性与配置问题**，提示该模块正处于频繁测试与修复阶段。PR #1182 和 #531 均为重要功能改进，但目前仍处于开放状态，尚未合并。整体项目健康度良好，但 Apple Container 相关 Bug 集中出现需关注。

---

## 2. 版本发布

> 无新版本发布。

---

## 3. 项目进展

| PR | 状态 | 推进内容 |
|---|---|---|
| [#1182](https://github.com/moltis-org/moltis/pull/1182) | OPEN | 修复 main session 不可删除/归档的限制，解决 #1132 |
| [#531](https://github.com/moltis-org/moltis/pull/531) | OPEN | 为浏览器交互引入 CDP screencast 实时查看与操作 UI |

- **#1182** 由 `shixi-li` 创建（2026-08-01），最近于今日更新，已明确修复 target（#1132），逻辑清晰，合并前景较好。
- **#531** 由 `penso` 创建（2026-03-31），历时约 4 个月，最近于 2026-08-10 更新，说明仍有维护者持续跟进，属于**长期未合并在途的重要功能 PR**。

> ⚠️ 今日**无 PR 合并**，项目功能迭代在当日暂无实质性落地。

---

## 4. 社区热点

| Issue/PR | 评论数 | 👍 | 热度分析 |
|---|---|---|---|
| [#1185](https://github.com/moltis-org/moltis/issues/1185) | 3 | 0 | 今日 Issue 中讨论最活跃，聚焦 Apple Container 运行时状态误判问题 |
| [#531](https://github.com/moltis-org/moltis/pull/531) | — | 0 | 长期关注 PR，浏览器交互 UI 受到社区期待 |
| [#1188](https://github.com/moltis-org/moltis/issues/1188) | 0 | 0 | 新建 Issue，资源限制未生效，待维护者响应 |
| [#1189](https://github.com/moltis-org/moltis/issues/1189) | 0 | 0 | 新建 Issue，构建 URL 配置错误，快速报告 |

**热点分析**：
- **Apple Container 后端**是当前社区焦点，3 条 Issue 中有 2 条直接相关（#1185、#1188），暗示该模块在最新使用中暴露了多个问题，建议维护者优先排查。
- PR #531 历时较长，用户可能期待合并节奏加快。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | 已有 Fix PR？ |
|---|---|---|---|
| 🔴 **高** | [#1185](https://github.com/moltis-org/moltis/issues/1185) | Apple Container 1.x sandbox 启动后 Moltis 仍判定为未运行 | 暂无 |
| 🔴 **高** | [#1188](https://github.com/moltis-org/moltis/issues/1188) | Apple Container 后端资源限制未生效 | 暂无 |
| 🟡 **中** | [#1189](https://github.com/moltis-org/moltis/issues/1189) | Sandbox 构建因 `gogcli` GitHub URL 配置错误失败 | 暂无 |

> **趋势判断**：今日集中出现 Apple Container 相关 Bug，属于**同一模块的回归或配置问题**，建议维护者统一跟进，避免问题扩散。

---

## 6. 功能请求与路线图信号

| 信号来源 | 内容 | 纳入下一版本可能性 |
|---|---|---|
| PR #1182 | 允许删除/归档 main session | ⭐⭐⭐⭐ 高 — 已明确修复 #1132，逻辑完整 |
| PR #531 | 浏览器 CDP 实时交互 UI | ⭐⭐⭐ 中 — 功能完整但历时较长，需维护者review |
| Issue #1188 | 资源限制修复 | ⭐⭐⭐ 高 — 属于已知 backend 问题，应优先修复 |

---

## 7. 用户反馈摘要

- **Apple Container 体验不佳**：#1185 和 #1188 均来自 `holgzn`，同一用户在短时间内报告两个 Apple Container 后端问题，说明该模块在真实使用中存在问题，**用户信心受影响**。
- **Session 管理灵活性需求**：#1182 回应了 #1132 的诉求，用户希望 main session 具备与其他 session 一致的删除/归档能力，反馈合理。
- **浏览器交互期待较高**：PR #531 虽创建较早，但持续更新表明维护者和社区对实时浏览器操作功能有明确需求。

---

## 8. 待处理积压

| 项目 | 创建时间 | 时长 | 建议 |
|---|---|---|---|
| [#531](https://github.com/moltis-org/moltis/pull/531) | 2026-03-31 | ~4 个月 | 长期未合并的重要功能 PR，建议维护者安排 review |
| [#1185](https://github.com/moltis-org/moltis/issues/1185) | 2026-08-08 | 3 天 | Apple Container 状态误判，已有 3 条评论，建议优先响应 |
| [#1188](https://github.com/moltis-org/moltis/issues/1188) | 2026-08-10 | 1 天 | 资源限制未生效，暂无评论，需维护者介入 |
| [#1189](https://github.com/moltis-org/moltis/issues/1189) | 2026-08-10 | 1 天 | 构建配置错误，修复成本较低，建议快速响应 |

---

**日报总结**：Moltis 项目今日以 Apple Container 后端问题为主导，3 条 Issue 中 2 条直接相关，稳定性信号需重视。功能层面 PR #1182 和 #531 进展良好但尚未合并。建议维护者优先处理 Apple Container 相关 Bug，并加快长期在途 PR 的 review 节奏。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw 项目动态日报
**日期：2026-08-11** | 数据来源：github.com/agentscope-ai/CoPaw

---

## 1. 今日速览

CoPaw 昨日（2026-08-10 至 2026-08-11）保持**高活跃度**：24 小时内新增/活跃 Issue 33 条，关闭 6 条；PR 总数 50 条，其中 17 条已合并/关闭，33 条待审。社区参与积极，多个长期请求首次出现可合并修复 PR。无新版本发布，但 v2.1.0 发布说明已在准备中（PR #6875）。项目整体健康度良好，bug 修复与功能迭代并行推进。

---

## 2. 版本发布

**无新版本发布。**

相关准备：PR #6875（[chore: update release notes for v2.1.0](https://github.com/agentscope-ai/CoPaw/pull/6875)）正在同步更新 v2.1.0 中英双语发布说明及 README 翻译，预计为近期正式版做准备。

---

## 3. 项目进展

### 已合并/关闭的重要 PR

| PR | 类型 | 说明 |
|---|---|---|
| [#6809](https://github.com/agentscope-ai/CoPaw/pull/6809) | Bug fix | 修复 Chat Completions 内容格式问题，解决严格兼容提供商（如 StepFun）拒绝请求的 400 错误 |
| [#6615](https://github.com/agentscope-ai/CoPaw/pull/6615) | Bug fix | 增强 `load_agent_config()` 容错，处理损坏的 agent.json 和无效 UTF-8 字节 |
| [#6398](https://github.com/agentscope-ai/CoPaw/pull/6398) | Feature | ReMe 记忆搜索后端增加 reranker 支持（over-fetch → rerank → cap → rebuild） |
| [#6878](https://github.com/agentscope-ai/CoPaw/pull/6878) | UX | 项目目录选择器增加"显示隐藏文件夹"开关 |

### 待合并的关键 PR（关注度高）

- **#6890** [fix: preserve long multiline tool output](https://github.com/agentscope-ai/CoPaw/pull/6890) — 修复长多行工具输出渲染问题（修复 #6852）
- **#6889** [fix: preserve textarea target for IME events](https://github.com/agentscope-ai/CoPaw/pull/6889) — 修复中文 IME 输入时消息队列崩溃（关联 #6885）
- **#5992** [feat: per-session model overrides](https://github.com/agentscope-ai/CoPaw/pull/5992) — 支持单会话模型覆盖，同一 Agent 可调用不同 LLM
- **#6870** [feat: creator plugin aggregation](https://github.com/agentscope-ai/CoPaw/pull/6870) — Creator 插件大幅更新：设置中心、异步媒体生成、跨平台加固
- **#6772** [feat: embedding hot updates & Daily Paper for ReMe Light](https://github.com/agentscope-ai/CoPaw/pull/6772) — ReMe Light 扩展 Embedding 配置（OpenAI/DashScope/Gemini/Ollama），新增连通性测试与索引维护
- **#6884** [fix: Auto-Dream integration resilience](https://github.com/agentscope-ai/CoPaw/pull/6884) — Auto-Dream 对 LLM 空 schema 输出增加容错与重试
- **#6880** [feat: unify marketplace](https://github.com/agentscope-ai/CoPaw/pull/6880) — 统一应用/插件/技能市场入口至 `/market` 路由
- **#6854** [feat: localized approval purpose descriptions](https://github.com/agentscope-ai/CoPaw/pull/6854) — 审批请求增加用户友好的目的说明

**整体评估**：今日 17 条 PR 已闭环，涵盖配置容错、严格提供商兼容、记忆搜索 reranker 等核心问题；待合并 PR 中 13 条处于 Review 或 Ready 状态，项目迭代节奏稳定。

---

## 4. 社区热点

### 最活跃 Issues（评论数 Top 5）

1. **#6782** — [插件市场/应用市场始终提示维护中](https://github.com/agentscope-ai/CoPaw/issues/6782)（9 评论）  
   Docker 版 2.0.1 用户反馈无法使用插件和应用市场，社区讨论集中在网络连通性与服务配置。

2. **#6803** — [OpenAI-compatible 请求被严格提供商拒绝](https://github.com/agentscope-ai/CoPaw/issues/6803)（6 评论，已关闭）  
   StepFun 等提供商拒绝包含内部字段的请求，已有 PR #6809 修复并关闭。

3. **#6811** — [Responses continuation summary 忽略 disable_thinking](https://github.com/agentscope-ai/CoPaw/issues/6811)（5 评论）  
   Scroll 触发摘要时阻塞主对话，推理模型场景下的并发处理问题。

4. **#6826** — [助手消息结束时间显示异常](https://github.com/agentscope-ai/CoPaw/issues/6826)（5 评论）  
   前端时间戳与实际的思考耗时不符，已有 PR #6845 修复（待合并）。

5. **#4237** — [Shell 命令运行中可观测面板](https://github.com/agentscope-ai/CoPaw/issues/4237)（4 评论，开放 3 个月）  
   用户希望看到正在执行的 shell 命令并提供 kill/extend timeout 控制。

### 趋势分析

- **严格提供商兼容**（#6803/#6809）是近期高频痛点，随着 CoPaw 接入更多第三方 LLM 提供商，此类格式对齐问题将持续出现。
- **前端渲染与时间戳**（#6826/#6871）反映 Console UI 在多视图切换场景下的状态管理问题，PR #6845/#6871 正在修复。
- **ReMe 记忆系统**（#6853/#6840）进入用户深度体验阶段，对 Auto-Dream 完整功能路线图的询问表明记忆模块已成为核心关注点。

---

## 5. Bug 与稳定性

| 严重程度 | Issue | 描述 | 状态 | Fix PR |
|---|---|---|---|---|
| 🔴 高 | [#6885](https://github.com/agentscope-ai/CoPaw/issues/6885) | 中文 IME 输入时 Console 消息队列崩溃（v2.1.0b2） | Open | [#6889](https://github.com/agentscope-ai/CoPaw/pull/6889) 待合并 |
| 🔴 高 | [#6814](https://github.com/agentscope-ai/CoPaw/issues/6814) | macOS SQLite WAL 模式打开 history.db 触发 SIGBUS 崩溃 | Open | — |
| 🟠 中 | [#6820](https://github.com/agentscope-ai/CoPaw/issues/6820) | 前端 UI 不实时显示模型输出/工具调用/思考过程 | Open | — |
| 🟠 中 | [#6828](https://github.com/agentscope-ai/CoPaw/issues/6828) | Console 空闲时 CSS 无限动画导致 ~20% CPU 占用 | Open | — |
| 🟠 中 | [#6813](https://github.com/agentscope-ai/CoPaw/issues/6813) | `consume_model_response` 抛出 `KeyError: '__aiter__'`，auto-title 失败 | Open | — |
| 🟡 低 | [#6839](https://github.com/agentscope-ai/CoPaw/issues/6839) | MCP 工具调用时数字字符串被转为数值类型导致参数错误 | Open | — |
| 🟡 低 | [#6867](https://github.com/agentscope-ai/CoPaw/issues/6867) | Gemini compaction 报错缺少 `thought_signature` | Open | — |
| 🟡 低 | [#6780](https://github.com/agentscope-ai/CoPaw/issues/6780) | 闲置数十分钟后进程卡死，只能强制重启 | Open | — |

**已修复关闭的 Bug**：
- #6871（时区偏移 +8h，PR 待合并中）
- #6866（workspace 自生成文件过多，已关闭确认设计预期）
- #6803（严格提供商格式，PR #6809 已合并）

---

## 6. 功能请求与路线图信号

| Issue/PR | 诉求 | 路线图信号 |
|---|---|---|
| [#6881](https://github.com/agentscope-ai/CoPaw/issues/6881) | 自动记忆更新后刷新会话标题 | 低悬挂果实，可快速纳入 |
| [#4634](https://github.com/agentscope-ai/CoPaw/issues/4634) | 窗口大小/位置记忆（重启保留） | 简单配置增强，可纳入 |
| [#6876](https://github.com/agentscope-ai/CoPaw/issues/6876) | 后台任务面板默认折叠（已关闭） | 用户建议已获认可，可能后续实现 |
| [#6585](https://github.com/agentscope-ai/CoPaw/issues/6585) | 输入框下方字符计数动态显示关闭开关 | UX 可配置化方向 |
| [#4237](https://github.com/agentscope-ai/CoPaw/issues/4237) | Shell 命令运行中可观测面板 | 长期 Feature 请求，与 #6876 同属可观测性 |
| [#6840](https://github.com/agentscope-ai/CoPaw/issues/6840) | ReMe4 完整路线图（Auto-Link、三模搜索、4 类摘要权重） | 用户密切关注，ReMe Light 已在迭代中（PR #6772） |
| PR #5992 | 单会话模型覆盖 | 高价值功能，已在 Review 中 |
| PR #6880 | 统一市场入口 | 已在 Review 中，整合应用/插件/技能 |

**路线图判断**：v2.1.0 将聚焦于（1）记忆系统增强（ReMe Light + reranker）；（2）多提供商兼容修复；（3）市场统一；（4）Creator 插件能力扩展。窗口记忆、字符计数开关等 UX 微调可能在后续 patch 中跟进。

---

## 7. 用户反馈摘要

### 痛点

1. **严格 LLM 提供商兼容问题**：用户反映接入 StepFun 等国内提供商时频繁遇到 400 错误，核心原因是 QwenPaw 透传了内部运行时字段（`delta`、`input_text` 等）。
2. **前端实时渲染缺失**：模型输出、工具调用、思考过程需在全部完成后才显示，用户体验与预期存在差距（#6820）。
3. **中文 IME 崩溃**：v2.1.0b2 使用中文输入法时消息队列完全不可用，严重影响日常使用（#6885）。
4. **CPU 空闲占用**：CSS 无限动画导致空闲时 CPU 占用高达 20%，影响笔记本续航和散热（#6828）。
5. **杀软误报**：部分安全软件将 CoPaw 进程标记为威胁（#6847），可能与子进程创建行为有关。
6. **MCP 参数类型转换**：数字字符串被自动转为数值类型，导致 API 调用失败（#6839）。

### 正面反馈

- ReMe 记忆系统（ReMe Light）获得用户关注，有人主动对比代码与公告功能，显示对记忆架构的高度认可。
- Creator 插件的异步媒体生成能力受到期待。
- 社区贡献者活跃度提升，首次贡献者（first-time-contributor）参与多个 PR。

---

## 8. 待处理积压

### 需维护者关注的长期 Issue

| Issue | 创建时间 | 天数 | 说明 |
|---|---|---|---|
| [#4237](https://github.com/agentscope-ai/CoPaw/issues/4237) | 2026-05-12 | ~91 天 | Shell 命令可观测面板，Feature 请求长期未动 |
| [#4634](https://github.com/agentscope-ai/CoPaw/issues/4634) | 2026-05-22 | ~81 天 | 窗口大小记忆，简单但长期未实现 |
| [#6585](https://github.com/agentscope-ai/CoPaw/issues/6585) | 2026-07-30 | ~13 天 | 字符计数动态显示关闭开关 |
| [#6780](https://github.com/agentscope-ai/CoPaw/issues/6780) | 2026-08-07 | ~4 天 | 闲置卡死问题，稳定性隐患 |

### 待合并 PR（Review 中）

- [#5992](https://github.com/agentscope-ai/CoPaw/pull/5992) — 单会话模型覆盖（29 天未合并）
- [#6399](https://github.com/agentscope-ai/CoPaw/pull/6399) — reranker UI 配置面板
- [#6870](https://github.com/agentscope-ai/CoPaw/pull/6870) — Creator 插件聚合更新
- [#6884](https://github.com/agentscope-ai/CoPaw/pull/6884) — Auto-Dream 容错修复

---

**报告生成时间**：2026-08-11 | **分析师**：Agnes (Sapiens AI)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw 项目日报 | 2026-08-11

## 1. 今日速览
过去24小时项目保持高活跃度，共处理 50 条 Issue 与 50 条 PR 更新（49 条活跃/新开，1 条关闭；PR 待合并 48 条，2 条已关闭/合并）。核心工作集中在安全审计修复、RFC 治理流程优化及多通道（Telegram/Matrix/WhatsApp）稳定性提升。无新版本发布。项目整体健康度良好，处于“安全加固与体验打磨”的关键过渡期，但 P1 级安全与配置类问题积压较多，需维护者优先响应。

## 2. 版本发布
无。

## 3. 项目进展
**已合并/关闭**：
- [#9904](https://github.com/zeroclaw-labs/zeroclaw/pull/9904)：针对 RUSTSEC-2026-0247（`bitmaps` 依赖废弃）添加安全豁免，恢复 CI 构建。
- [#8301](https://github.com/zeroclaw-labs/zeroclaw/pull/8301)：补充工具命名规范回归测试，防止后续 PR 破坏低蛇形命名约束。

**关键推进中**：
- [#8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486)：新增 OpenAI Chat Completions 兼容接口，降低第三方 LLM 客户端接入门槛。
- [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713)：为 `file_download` 添加 `allowed_private_hosts` 显式白名单，修复 SSRF 风险。
- [#9554](https://github.com/zeroclaw-labs/zeroclaw/pull/9554)：引入 `dag_plan_execute` 工具，支持 Agent 多步任务的 DAG 串行/并行规划。
- [#9320](https://github.com/zeroclaw-labs/zeroclaw/pull/9320)：为 Cron Agent 任务添加墙钟超时机制，防止 hung run 永久占用 SQLite 锁。
- [#9

</details>

---
*本日报由 [agents-radar](https://github.com/xavier9802/agents-radar) 自动生成。*