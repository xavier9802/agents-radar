# OpenClaw Ecosystem Digest 2026-08-12

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-12 02:27 UTC

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

## OpenClaw Deep Dive



# OpenClaw Project Digest — 2026-08-12

## 1. Today's Overview

OpenClaw is operating at **very high activity** on 2026-08-12, with 500 issues and 500 PRs touched in the last 24 hours. Of the 500 issues, 383 remain open and active while 117 were closed, indicating aggressive triage and resolution throughput. The PR pipeline shows 280 open items against 220 merged/closed, suggesting a healthy merge rate (~44%). No new releases were published today, though a recent P0 incident (Issue #121675) around a botched beta publish (2026.8.1-beta.1) has been closed, signaling the team is actively plugging a critical release-process gap.

## 2. Releases

**No new releases published today.**

> ⚠️ **Reminder:** Issue [#121675](https://github.com/openclaw/openclaw/issues/121675) (now closed) documented that `2026.8.1-beta.1` was published to npm **without companion `@openclaw/*` plugins**, causing an unrecoverable boot loop. The startup convergence guard exacerbated the failure. Any operators on the 2026.8.x beta should verify plugin version alignment before upgrading.

## 3. Project Progress

### Merged / Closed Today (selected highlights)

| PR / Issue | Type | Summary |
|---|---|---|
| [#119528](https://github.com/openclaw/openclaw/pull/119528) [CLOSED] | fix | Timestamp recovery for Claude CLI history — fixes #94679 |
| [#92076](https://github.com/openclaw/openclaw/issues/92076) [CLOSED] | fix | Subagent completion delivery failure when requester session is inactive |
| [#92460](https://github.com/openclaw/openclaw/issues/92460) [CLOSED] | fix | Isolated cron completion announcer dropping `delivery.channel` |
| [#91799](https://github.com/openclaw/openclaw/issues/91799) [CLOSED] | fix (invalid) | Discord agents unable to access MCP tools — resolved via CLI path clarification |
| [#121675](https://github.com/openclaw/openclaw/issues/121675) [CLOSED] | fix | Beta publish without companion plugins — root cause contained |
| [#96827](https://github.com/openclaw/openclaw/issues/96827) [CLOSED] | fix | Agent does not terminate after `sourceReplyDeliveryMode: "message_tool_only"` delivery |
| [#89315](https://github.com/openclaw/openclaw/issues/89315) [CLOSED] | fix | Gateway heap unbounded growth → cgroup OOM kills |

### Actively Advanced PRs (top open items)

- **[PR #121690](https://github.com/openclaw/openclaw/pull/121690)** — CLI spinner-leak fix: adds `fallback: none` to startup progress to prevent stray output in `--version` path.
- **[PR #117321](https://github.com/openclaw/openclaw/pull/117321)** — Rejects malformed base64 MCP App resource blobs; prevents silent HTML injection via corrupted blobs.
- **[PR #119525](https://github.com/openclaw/openclaw/pull/119525)** [automerge armed] — Fixes `memory_search` retry after 15s timeout; removes false 60s provider cooldown block.
- **[PR #115531](https://github.com/openclaw/openclaw/pull/115531)** — iMessage send-timeout reconciliation by exact attempt ID; eliminates duplicate user-visible replies.
- **[PR #82572](https://github.com/openclaw/openclaw/pull/82572)** — Persists followup queues across gateway restarts via SQLite; prevents message loss on restart.
- **[PR #122300](https://github.com/openclaw/openclaw/pull/122300)** — Fixes multi-profile provider card showing "Credentials rejected" when another profile is valid.
- **[PR #97295](https://github.com/openclaw/openclaw/pull/97295)** — Feishu token-invalid retry (99991663/99991664) with cache invalidation.
- **[PR #120768](https://github.com/openclaw/openclaw/pull/120768)** — One-paste device pairing via `oc-pair` setup links; simplifies multi-surface onboarding.

## 4. Community Hot Topics

| # | Type | Title | Comments | Reactions | Link |
|---|---|---|---|---|---|
| #121058 | Issue | Silent reply failures recurring after #116277 closed | 69 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/121058) |
| #116201 | Issue | Realtime voice work retains unbounded provider/consult state | 64 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/116201) |
| #25592 | Issue | Text between tool calls leaks to messaging channels | 46 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/25592) |
| #7707 | Issue | Memory Trust Tagging by Source | 43 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/7707) |
| #92201 | Issue | Anthropic thinking signatures intermittently invalid on replay | 23 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/92201) |
| #42475 | Issue | Per-agent cost budget enforcement at gateway level | 21 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/42475) |
| #87744 | Issue | Codex-backed Telegram turns time out waiting for `turn/completed` | 17 | 3 | [🔗](https://github.com/openclaw/openclaw/issues/87744) |
| #68596 | Issue | Configurable streaming watchdog timeout threshold | 15 | 8 | [🔗](https://github.com/openclaw/openclaw/issues/68596) |
| #42840 | Issue | MathJax/LaTeX support in Control UI | 8 | 10 | [🔗](https://github.com/openclaw/openclaw/issues/42840) |

**Analysis of underlying needs:**
- **Session-state & message-loss** dominate the top issues — the community is experiencing real production pain with reliability (silent failures, duplicates, truncation).
- **Realtime voice unbounded state** (#116201) and **tool-call text leakage** (#25592) point to architectural gaps in how the gateway manages conversation flow.
- **Cost governance** (#42475) and **memory security** (#7707) reflect growing operator maturity — users are running OpenClaw at scale and need budget guardrails and supply-chain trust.
- **Streaming watchdog configurability** (#68596, 8 👍) is a strong signal: extended-reasoning models (Kimi K2.5, DeepSeek R1) are widely used, and the hardcoded 30s timeout is a frequent friction point.

## 5. Bugs & Stability

### Critical / P0–P1 (ranked by severity)

| # | Title | Severity | Fix PR? | Link |
|---|---|---|---|---|
| #121675 | 2026.8.1-beta.1 published without companion plugins → boot loop | **P0** | ✅ Closed | [🔗](https://github.com/openclaw/openclaw/issues/121675) |
| #121058 | Silent reply failures recurring post-#116277 | **P1** | ❌ No fix yet | [🔗](https://github.com/openclaw/openclaw/issues/121058) |
| #116201 | Realtime voice unbounded provider/consult state | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/116201) |
| #97983 | iOS/WebChat messages append to transcript but no assistant reply | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/97983) |
| #96827 | `message_tool_only` agent does not terminate after delivery | **P1** | ✅ Closed | [🔗](https://github.com/openclaw/openclaw/issues/96827) |
| #87744 | Codex-backed Telegram turns time out, never reach `turn/completed` | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/87744) |
| #84516 | Codex app-server long replies silently truncated at ~1000–1100 chars | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/84516) |
| #97616 | Unreaped hook/tool child processes → zombie accumulation | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/97616) |
| #112668 | `sessions_yield` abort-settle timeout drops subagent announce | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/112668) |
| #121953 | Cron agent turns stall on DeepSeek due to `[cron:` prefix deprioritization | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/121953) |
| #83337 | Plugin/core version drift after upgrade → silent channel failure | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/83337) |
| #114020 | Feishu/Telegram dispatch fails: missing `runDispatchLifecycle` | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/114020) |
| #47975 | Subagent sessions persist after completion, main session unresponsive | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/47975) |
| #39476 | A2A `sessions_send` back-call causes duplicate messages | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/39476) |
| #80498 | Subagent completion announcements premature/duplicated after tool-use | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/80498) |
| #92201 | Anthropic thinking signatures invalid on replay; recovery wrapper silent | **P1** | ✅ Closed | [🔗](https://github.com/openclaw/openclaw/issues/92201) |
| #74586 | AM embedded run aborts `memory_search` tool calls; misclassified as timeout | **P1** | ❌ Open | [🔗](https://github.com/openclaw/openclaw/issues/74586) |

### P2–P3 (selected)

| # | Title | Link |
|---|---|---|
| #14785 | Reduce tool schema token overhead (~3,500 tok/session) | [🔗](https://github.com/openclaw/openclaw/issues/14785) |
| #68596 | Configurable streaming watchdog timeout threshold | [🔗](https://github.com/openclaw/openclaw/issues/68596) |
| #98435 | MCP loopback transport no auto-reconnect after gateway restart | [🔗](https://github.com/openclaw/openclaw/issues/98435) |
| #114612 | SQLite unbounded growth: `memory_index_chunks` + `memory_embedding_cache` | [🔗](https://github.com/openclaw/openclaw/issues/114612) |
| #80131 | Per-request auth (5.5s) and tool bundling (8.9s) dominate gateway TTFT | [🔗](https://github.com/openclaw/openclaw/issues/80131) |
| #58957 | Model switch fails silently when carried-over context is too large | [🔗](https://github.com/openclaw/openclaw/issues/58957) |
| #65538 | Accessibility: screen readers announce every token during streaming | [🔗](https://github.com/openclaw/openclaw/issues/65538) |
| #49223 | WhatsApp inter_session delivery requests wrongly suppressed | [🔗](https://github.com/openclaw/openclaw/issues/49223) |
| #97335 | Cron fallback model works in session but fails when triggered via cron | [🔗](https://github.com/openclaw/openclaw/issues/97335) |

**Key stability themes:**
- **Message loss & duplication** is the #1 reliability concern, affecting Discord, Telegram, Feishu, iMessage, and WebChat.
- **Session-state leaks** (zombie processes, unpurged subagent sessions, unbounded SQLite tables) threaten long-running deployments.
- **Plugin version drift** (#83337) remains an operational risk with no automated alignment mechanism.

## 6. Feature Requests & Roadmap Signals

| # | Title | Comments | 👍 | Link |
|---|---|---|---|---|
| #7707 | Memory Trust Tagging by Source | 43 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/7707) |
| #42475 | Per-agent cost budget enforcement at gateway | 21 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/42475) |
| #14785 | Reduce tool schema token overhead (~3,500 tok/session) | 9 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/14785) |
| #72741 | Standard interface for external security/guardrail checks | 10 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/72741) |
| #42840 | MathJax/LaTeX support in Control UI | 8 | 10 | [🔗](https://github.com/openclaw/openclaw/issues/42840) |
| #16670 | Onboarding wizard: mandatory Memory/Embedding setup step | 8 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/16670) |
| #71058 | Multiple Azure/Teams bots on a single gateway | 8 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/71058) |
| #13700 | Session snapshots — save/load context checkpoints | 6 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/13700) |
| #55249 | Session labels / nicknames | 5 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/55249) |
| #47910 | Provider fallback by failure class — quarantine auth-broken providers | 8 | 0 | [🔗](https://github.com/openclaw/openclaw/issues/47910) |
| #74704 | SDK: stabilize app-client happy path for agents/sessions/runs | 8 | 1 | [🔗](https://github.com/openclaw/openclaw/issues/74704) |

**Predictions for next release(s):**
1. **Per-agent cost budgets** (#42475) — strong operator demand; low implementation risk at gateway layer.
2. **Streaming watchdog threshold configurability** (#68596) — widely requested (8 👍), directly impacts extended-reasoning model users.
3. **Session snapshots** (#13

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Open-Source Ecosystem
**Date:** 2026-08-12

---

## 1. Ecosystem Overview

The open-source personal AI agent landscape is in a mature but rapidly evolving phase, characterized by high velocity at the top tier (OpenClaw, NanoBot, IronClaw, CoPaw) and architectural consolidation among mid-tier projects (Hermes, ZeroClaw, NanoClaw). The dominant theme across all active projects is the transition from experimental/single-session tools to production-grade, multi-channel agent platforms with gateway architectures, MCP integration, and enterprise-grade reliability requirements. Community feedback increasingly reflects operators running agents at scale—demanding cost governance, session-state reliability, security sandboxing, and cross-platform stability rather than novel features.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Releases | Health Score |
|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | None | 🟢 Active — aggressive triage, 44% merge rate |
| **NanoBot** | 6 | 141 | None | 🟢 Very active — high throughput, batching pre-release |
| **Hermes Agent** | 50 | 50 | None | 🟡 Active — stabilization phase, Windows regressions |
| **IronClaw** | 19 | 50 | None | 🟢 Active — architectural transition ("Reborn"), 50% closure rate |
| **CoPaw** | 22 | 49 | v2.1.0-beta.3 | 🟢 Sprint mode — pre-v2.1.0 release cadence |
| **ZeroClaw** | 50 | 50 | None | 🟡 Design-heavy — RFC bottleneck, low merge velocity |
| **LobsterAI** | 4 | 9 | v2026.8.11 | 🟢 Release-driven — focused, low noise |
| **NanoClaw** | 1 | 7 | None | 🟡 Moderate — consolidation phase, core-team driven |
| **PicoClaw** | 3 | 6 | None | 🟡 Stalled — multiple stale PRs awaiting review |
| **Moltis** | 0 | 1 | None | 🟢 Quiet — stable, single feature PR in flight |
| **NullClaw** | — | — | — | ⚪ Inactive |
| **ZeptoClaw** | — | — | — | ⚪ Inactive |

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of operation:** OpenClaw's 500-issue/500-PR daily volume is 10–100× the next most active project, reflecting a significantly larger user base and contributor pool.
- **Maturity of reliability engineering:** P0 incident response (beta publish regression, #121675) was contained within 24h with a root-cause closure—matching enterprise SRE velocity uncommon in this ecosystem.
- **Breadth of channel coverage:** Discord, iMessage, Telegram, Feishu, WebChat, and more—all with active fixes for session-state, message-loss, and provider-drift issues.

**Technical approach differences:**
- OpenClaw uses a **gateway-centric architecture** with plugin version alignment, subagent orchestration, and SQLite-backed persistence—distinct from NanoBot's more monolithic single-process model and IronClaw's kernel-channel-storage decoupling.
- OpenClaw's community signals (cost budgets, memory trust tagging, streaming watchdog configurability) indicate **operator-driven maturity**, whereas smaller projects are still solving first-run UX problems.

**Community size comparison:**
- OpenClaw: ~500 concurrent issues/PRs → largest ecosystem by order of magnitude
- NanoBot (~141 PRs/day), Hermes (~50), IronClaw (~50), CoPaw (~49): mid-tier, 3–5× smaller contributor bases
- LobsterAI, NanoClaw, PicoClaw: niche but engaged, 1–5× smaller
- Moltis, NullClaw, ZeptoClaw: minimal or dormant activity

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Session-state & message reliability** | OpenClaw, NanoBot, CoPaw, NanoClaw, LobsterAI | Silent message drops, duplicate replies, lost context on restart, subagent session leaks |
| **Cost governance & token efficiency** | OpenClaw, Hermes, ZeroClaw, LobsterAI | Per-agent budgets, lazy tool schema loading, token estimator accuracy, thinking-level cost control |
| **Security sandboxing & credential handling** | NanoBot, ZeroClaw, IronClaw, Hermes | API key leakage via `os.environ`, exec bypass, workspace isolation, pluggable auth |
| **Multi-channel / MCP integration** | OpenClaw, IronClaw, PicoClaw, NanoClaw, CoPaw | Channel unification, remote MCP HTTP support, provider failover, webhook reliability |
| **Configurable timeouts & streaming** | OpenClaw, CoPaw, LobsterAI | Streaming watchdog thresholds, MCP tool-call timeouts, long-task management |
| **Cross-platform stability** | Hermes, LobsterAI, IronClaw, CoPaw | Windows update regressions, macOS gateway lifecycle, Linux skill compatibility, IME support |
| **Plugin / extension ecosystem** | NanoBot, OpenClaw, NanoClaw, CoPaw | Plugin version drift, skill packaging, marketplace consolidation |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | IronClaw | Hermes | CoPaw | LobsterAI | ZeroClaw | PicoClaw / NanoClaw |
|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Gateway + multi-channel agent platform | General-purpose personal agent | Kernel infrastructure / "Reborn" architecture | CLI-first agent with Windows desktop | Desktop-class IDE-like agent experience | Desktop app (Electron) with thinking levels | RFC-driven protocol/spec platform | Lightweight routing & messaging |
| **Target user** | Enterprise/production operators | Researchers & power users | Infrastructure engineers | Developers & CLI users | Desktop power users | Casual to intermediate desktop users | Protocol designers & spec contributors | Niche / platform-specific deployers |
| **Architecture** | Gateway + plugins + subagents + SQLite | Monolithic with MCP extensions | Decoupled kernel/channel/storage | God-file sharding in progress | Electron desktop + session management | Single-process with WebUI | Spec-first, RFC-gated | Routing-layer abstractions |
| **Release cadence** | Beta-driven, no stable release today | Batching changes, no release today | No release today | No release today | v2.1.0-beta.3 published | v2026.8.11 published | No release; RFC cycle | No release |
| **Key differentiator** | Scale + reliability + channel breadth | Community velocity + security hardening | Kernel unification + pluggable loops | Windows Desktop + god-file refactor | Pre-v2.1.0 polish sprint | Per-model thinking levels + UX polish | OpenAI-protocol compatibility focus | Lightweight, multi-agent routing |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (100+ PRs/day or beta-sprint velocity):**
- **OpenClaw:** Highest absolute volume; production-scale reliability focus; aggressive triage.
- **NanoBot:** Exceptional throughput (141 PRs/day); security and reliability bugs emerging from production-like usage.

**Tier 2 — Active Development (40–60 PRs/day):**
- **IronClaw:** High velocity during architectural transition; "Reborn" epic driving coordinated PRs; strong maintainer engagement.
- **Hermes Agent:** Steady output with focus on Windows/Desktop regressions and god-file refactoring.
- **CoPaw:** Pre-release sprint to v2.1.0; 22 issues/49 PRs with active beta publishing.
- **ZeroClaw:** High issue volume but bottlenecked at maintainer review; design/RFC-heavy phase.

**Tier 3 — Focused & Release-Driven (5–15 PRs/day):**
- **LobsterAI:** Release-driven cadence; post-v2026.8.11 stabilization; 3 of 4 top items stale despite impact.
- **NanoClaw:** Moderate core-team momentum; template→plugin migration in progress; single open bug (#3226).
- **PicoClaw:** Low activity with stale PRs; routing and security regressions pending maintainer review.

**Tier 4 — Quiet / Dormant:**
- **Moltis:** Single feature PR; stable but minimal community engagement.
- **NullClaw / ZeptoClaw:** No activity; effectively dormant.

---

## 7. Trend Signals

1. **Production-grade reliability is the new baseline.** Across OpenClaw, NanoBot, Hermes, and CoPaw, the top complaints are no longer about feature gaps but about silent failures, message loss, session-state leaks, and subprocess cleanup. AI agents are being run 24/7 in production, and the ecosystem is maturing past the "does it work?" phase into the "does it survive?" phase.

2. **MCP is becoming the universal integration layer.** Every active project is investing in MCP support (OpenClaw, NanoBot, NanoClaw, PicoClaw, CoPaw, IronClaw). The direction is clear: MCP tool-server contracts will standardize how agents connect to external systems, and projects without robust MCP implementations will fall behind.

3. **Cost governance is emerging as a first-class requirement.** OpenClaw (#42475), Hermes (#6839), and ZeroClaw (#2269) all show community demand for per-agent budgets, token-aware schema loading, and cost visibility. As extended-reasoning models (Kimi K2.5, DeepSeek R1) become common, uncontrolled token consumption is a real operational risk.

4. **Cross-platform desktop experience is a competitive differentiator.** Hermes (Windows Desktop), LobsterAI (Electron), and CoPaw (desktop-class UX) are all investing heavily in native desktop experiences. Windows update/regression bugs (#83683, #84185 in Hermes; #1183 in LobsterAI) represent the largest cross-platform fragility in the ecosystem.

5. **Security sandboxing is the next arms race.** NanoBot's `exec.allowPatterns` bypass (#5306) and `os.environ` leakage (#4784, #4783), ZeroClaw's workspace isolation bugs (#9872, #9883), and IronClaw's secret redaction work (#7509) all signal that multi-tenant and multi-session deployments are exposing gaps in current security models. Projects that ship robust sandboxing first will gain operator trust.

6. **Protocol interoperability (OpenAI Chat Completions) is a community demand.** ZeroClaw's #8603 RFC (18 comments) explicitly targets Open WebUI, LobeChat, Continue.dev, Aider, and LangChain compatibility. This trend—if adopted broadly—could create a layer of client interoperability across otherwise siloed agent platforms.

7. **RFC-governed development is gaining traction.** ZeroClaw's heavy RFC culture (#8303, #7155, #8603) and IronClaw's "Reborn" epic signal a shift toward community-driven architectural governance. However, ZeroClaw's maintainer bottleneck (#8692) demonstrates the risk: without timely decisions, RFC momentum stalls and community frustration grows.

---

*Report generated from 2026-08-12 community digests across 11 projects. Data reflects GitHub activity only; not all ecosystem projects are represented.*

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-12

## 1. Today's Overview

NanoBot is experiencing **extremely high development velocity**, with 141 PRs updated in the last 24 hours and 6 issues touched. The project is in a mature, high-engagement phase with strong community contribution flow — 119 PRs merged or closed today alone. No new releases were published, suggesting the team is accumulating changes before the next version bump. Activity is heavily concentrated on bug fixes, security patches, and WebUI improvements.

## 2. Releases

**No new releases today.** The last 24 hours show zero new version publishings despite significant merged work, indicating the maintainers may be batching changes for an upcoming release.

## 3. Project Progress

**Merged/Closed PRs Today (key highlights):**

- **#5347** — WebUI provider and model preset management overhaul: added ability to delete custom providers, block removal of referenced presets, and improved the chat model-preset selector UI. ([link](https://github.com/HKUDS/nanobot/pull/5347))
- **#5338** — MCP OAuth credential preservation fix: prevents credential overwrite when OAuth store read fails, a critical reliability improvement for multi-server MCP setups. ([link](https://github.com/HKUDS/nanobot/pull/5338))
- **#5346** — One-shot `exec` process tree cleanup: ensures child processes spawned by shell commands are properly terminated on timeout, cancellation, or error — no more orphaned background processes. ([link](https://github.com/HKUDS/nanobot/pull/5346))
- **#5342** — WebUI apps discovery redesign: new Discover/Installed/All apps tabs with curated featured batches and cached offline fallback. ([link](https://github.com/HKUDS/nanobot/pull/5342))

**Closed issues:**
- **#5327** — Fixed the repeated-message-while-reasoning bug ([link](https://github.com/HKUDS/nanobot/issues/5327))
- **#4784** — Closed; API key leakage via `os.environ` mutation acknowledged ([link](https://github.com/HKUDS/nanobot/issues/4784))
- **#4783** — Closed; CLI subprocess environment leak acknowledged ([link](https://github.com/HKUDS/nanobot/issues/4783))
- **#5333** — OpenRouter Server Tools support feature request logged ([link](https://github.com/HKUDS/nanobot/issues/5333))

## 4. Community Hot Topics

**Most discussed Issues:**

- **[#5327](https://github.com/HKUDS/nanobot/issues/5327)** — *Nanobot repeats the same message while reasoning* (10 comments, closed) — A high-engagement bug where the agent randomly duplicates reasoning phrases like "Good points, let me investigate." Reflects growing user base running longer multi-turn agent sessions where loop-detection gaps become visible.
- **[#5306](https://github.com/HKUDS/nanobot/issues/5306)** — *`exec.allowPatterns` shell-chain bypass* (1 comment, open) — Security advisory about a pattern-matching bypass in the exec tool's allowlist. Indicates security-conscious users are actively stress-testing the agent's command execution sandbox.
- **[#5256](https://github.com/HKUDS/nanobot/issues/5256)** — */goal message produces dozens of repeated replies* (2 comments, open) — Directly related to #5327; users report goal-driven agents spiraling into repetition loops when waiting for user input. Shows a pattern: sustained-goal mode needs better turn-idle detection.
- **[#5283](https://github.com/HKUDS/nanobot/pull/5283)** — *Per-session sandbox isolation for non-WebUI channels* (open) — A significant security feature request gaining traction; users running Nanobot on Slack/Discord want filesystem isolation per session. ([link](https://github.com/HKUDS/nanobot/pull/5283))

**Underlying trend:** The community is pushing hard on **reliability during sustained agent operations** and **security hardening** — both indicate users are moving from casual experimentation to production-like deployments.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| 🔴 High | [#5306](https://github.com/HKUDS/nanobot/issues/5306) | `exec.allowPatterns` shell-chain bypass allows unintended command execution | No fix PR yet |
| 🔴 High | [#4784](https://github.com/HKUDS/nanobot/issues/4784) | Provider API keys leaked between providers via global `os.environ` mutation | Closed (acknowledged) |
| 🔴 High | [#4783](https://github.com/HKUDS/nanobot/issues/4783) | CLI apps inherit full `os.environ` — API keys leaked to subprocesses | Closed (acknowledged) |
| 🟡 Medium | [#5256](https://github.com/HKUDS/nanobot/issues/5256) | `/goal` message produces dozens of repeated replies in waiting state | Open — PR [#5257](https://github.com/HKUDS/nanobot/pull/5257) underway |
| 🟡 Medium | [#5327](https://github.com/HKUDS/nanobot/issues/5327) | Agent repeats reasoning messages randomly | ✅ Closed |
| 🟡 Medium | [#5344](https://github.com/HKUDS/nanobot/pull/5344) | Tool-call loop has no repeat/loop detection — agent can burn `max_iterations` on identical calls | PR open |

**Key observation:** Three high-severity security issues (API key leaks + exec bypass) are either closed-but-unpatched or still open. The `os.environ` leakage (#4784, #4783) was acknowledged but no fix PR appears in today's data — this is a **stale security backlog item**. The exec bypass (#5306) remains entirely unaddressed.

## 6. Feature Requests & Roadmap Signals

- **OpenRouter Server Tools** ([#5333](https://github.com/HKUDS/nanobot/issues/5333)) — Users want native support for OpenRouter's built-in tools (Web Search, Web Fetch, Fusion). Likely to be prioritized given OpenRouter's growing adoption as a gateway.
- **Per-session sandbox isolation** ([#5283](https://github.com/HKUDS/nanobot/pull/5283)) — Opt-in filesystem sandbox per non-WebUI session. Strong security signal from the community; if merged, could become a default in future versions.
- **Subagent model presets** ([#4291](https://github.com/HKUDS/nanobot/pull/4291)) — Allow subagents to use configurable model presets different from the parent. Long-open PR suggesting multi-agent orchestration is a key roadmap area.
- **OrcaRouter provider** ([#5328](https://github.com/HKUDS/nanobot/pull/5328)) — New gateway provider for 150+ models. Indicates continued expansion of provider ecosystem.
- **Weather skill Windows compatibility** ([#5341](https://github.com/HKUDS/nanobot/pull/5341)) — Cross-platform skill robustness is being addressed, suggesting Windows support is a active improvement area.

**Prediction:** The next release will likely include the WebUI improvements (#5347, #5342), MCP OAuth fix (#5338), and exec cleanup (#5346). The sandbox isolation (#5283) and subagent presets (#4291) are significant enough that they may define the next major version.

## 7. User Feedback Summary

**Pain points:**
- **Repetition loops** are the dominant complaint (#5327, #5256) — users report the agent getting stuck in reasoning or goal-waiting loops, burning tokens and degrading UX. This is a core agent-loop reliability issue.
- **Security anxiety** around API key exposure is real and repeated — two separate but related `os.environ` leakage issues (#4784, #4783) suggest the current provider architecture has a fundamental design flaw in how it handles credentials.
- **Windows compatibility gaps** in built-in skills (weather/curl) frustrate non-Linux users (#5341).
- **Orphaned subprocesses** from the exec tool (#5346) indicate cleanup logic is incomplete.

**Satisfaction signals:**
- Praise for OpenRouter Server Tools support request (#5333) shows appreciation for the extensible provider model.
- Active contribution flow (141 PRs/day) suggests a healthy, engaged contributor base.
- WebUI redesign (#5342) and preset management (#5347) indicate the team is responding to usability feedback.

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| [#4784](https://github.com/HKUDS/nanobot/issues/4784) — API key leakage via `os.environ` mutation | ~37 days open, closed but likely **no fix deployed** | 🔴 Critical — credentials exposed in production |
| [#4783](https://github.com/HKUDS/nanobot/issues/4783) — CLI subprocess inherits full environment | ~37 days open, closed but likely **no fix deployed** | 🔴 Critical — same class of vulnerability |
| [#5306](https://github.com/HKUDS/nanobot/issues/5306) — `exec.allowPatterns` shell-chain bypass | 3 days open, **no fix PR** | 🔴 Critical — sandbox bypass in active use |
| [#4291](https://github.com/HKUDS/nanobot/pull/4291) — Subagent configurable model presets | ~62 days open | 🟡 Medium — blocks advanced multi-agent workflows |

**Overall project health:** 🟢 **Active and improving**, but with a **critical security gap** around credential handling that has been acknowledged but not yet patched. The team's throughput is exceptional (141 PRs/day), but the backlog of unpatched security issues needs urgent attention before the next release.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-12

## 1. Today's Overview

Hermes Agent shows strong development momentum with 50 issues and 50 PRs updated in the last 24 hours, of which 8 PRs were merged/closed. The project is in a active stabilization phase, with a major refactoring epic (god-file sharding) underway and a cluster of Windows Desktop update regressions demanding attention. No new releases were published today. Overall, the project is healthy but dealing with a concentrated set of platform-specific regressions and architectural debt.

## 2. Releases

**No new releases today.**

## 3. Project Progress

### Merged/Closed PRs (8)
- **#78149** — `fix(cli): recognize prefixed MCP toolsets` — Resolves MCP toolset name recognition without widening the allowlist. [Link](https://github.com/NousResearch/hermes-agent/pull/78149)
- **#78172** — `fix(cron): enforce profile cap for review dispatch` — Applies per-profile concurrency cap to review dispatch. [Link](https://github.com/NousResearch/hermes-agent/pull/78172)
- **#78143** — `fix(kanban): count dry-run spawns toward global cap` — Fixes concurrency accounting for predicted dry-run task spawns. [Link](https://github.com/NousResearch/hermes-agent/pull/78143)
- **#62191** — `fix(update): resolve venv dir for both venv/ and .venv/ layouts` — Fixes Windows quarantine checks for `.venv` installs. [Link](https://github.com/NousResearch/hermes-agent/pull/62191)
- **#81199** — `feat(tools): report applied edits that fail validation` — Ensures syntax/lint errors in file edits surface clearly instead of being silently ignored by weaker models. [Link](https://github.com/NousResearch/hermes-agent/pull/81199)

### Key Open PRs Advancing
- **#84214** — Fixes Honcho local-memory migration being re-run every conversation, preventing duplicate profile bloat.
- **#84213** — Flags un-appliable staged skill writes at staging time, closing a silent-failure gap.
- **#84212** — Verifies Windows gateway cold-start survival before reporting update success (fixes #84185).
- **#83432** — Stops local bridge impersonation on WhatsApp by adding persistent session secrets and challenge-bound auth.
- **#84202** — Adds OneBot 11 platform adapter for QQ (NapCat/Lagrange/LLOneBot), expanding Chinese messaging support.
- **#84209** — Exposes `host.attachFileToComposer()` SDK door for staging files from plugins.
- **#84192** — Extends OS notifications with icon, action buttons, and deeplink activation for plugins.

## 4. Community Hot Topics

| Issue/PR | Comments | 👍 | Focus |
|---|---|---|---|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — Epic: Shard all 20 god files | 67 | 0 | Architecture debt / repo-wide refactoring |
| [#6839](https://github.com/NousResearch/hermes-agent/issues/6839) — Lazy Tool Schema Loading | 38 | 18 | Token overhead reduction for multi-tool setups |
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) — Solving the Multi-Tenant Hermes Problem | 25 | 3 | Tenant isolation in memory operations |
| [#67442](https://github.com/NousResearch/hermes-agent/issues/67442) — Cross-process turn serialization | 14 | 0 | CLI-continuity session state across processes |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale/degraded | 13 | 0 | Automated index freshness |

**Analysis:** The community is most engaged around **architectural cleanup** (god-file sharding) and **token efficiency** (lazy tool schema loading, 18 upvotes). Multi-tenant isolation remains an open architectural concern with production users reporting workarounds. The skills-index watchdog issue indicates ongoing maintenance burden on the Docs/Skills pipeline.

## 5. Bugs & Stability

### P1 — Critical / High Impact
| Issue | Summary | Fix PR? |
|---|---|---|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | Windows Desktop restart reaps gateway, never relaunches — WeChat/QQ go silent | Partially: #84212 targets cold-start |
| [#84185](https://github.com/NousResearch/hermes-agent/issues/84185) | Windows gateway cold-start dies silently after `hermes update` (no logs, no PID) | **#84212** open |
| [#84109](https://github.com/NousResearch/hermes-agent/issues/84109) | Post-reset gateway sessions invisible in all session lists (regression from d2a4d373eb) | **#84198** open |
| [#83213](https://github.com/NousResearch/hermes-agent/issues/83213) | Background process notifications misrouted to wrong session after `/new` | — |
| [#84200](https://github.com/NousResearch/hermes-agent/issues/84200) | macOS: Desktop backend SIGTERMs launchd-managed gateway after every update | — |

### P2 — Moderate
| Issue | Summary | Fix PR? |
|---|---|---|
| [#73779](https://github.com/NousResearch/hermes-agent/issues/73779) | Feishu multiplex WebSocket loop dies with "Future attached to different loop" | — |
| [#83427](https://github.com/NousResearch/hermes-agent/issues/83427) | `browser_exec` crashes with `pydantic_core ModuleNotFoundError` when PYTHONPATH points at Hermes venv | — |
| [#69672](https://github.com/NousResearch/hermes-agent/issues/69672) | FTS trigram indexes NUL-sentinel JSON, causing SQLite-version-dependent bloat | — |
| [#84102](https://github.com/NousResearch/hermes-agent/issues/84102) | Local TTS writes Ogg/Vorbis into .ogg paths, causing silent degradation on platforms expecting Opus | — |
| [#81410](https://github.com/NousResearch/hermes-agent/issues/81410) | Single-process Nous OAuth refresh returns `invalid_grant` after event loop stall | — |
| [#82186](https://github.com/NousResearch/hermes-agent/issues/82186) | Windows Desktop update button fails with `WinError 5` (Hermes-managed Node) | — |

### P3 — Lower Priority
| Issue | Summary |
|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index 29.8h old, exceeding 26h freshness limit |
| [#57540](https://github.com/NousResearch/hermes-agent/issues/57540) | Desktop leaks explicit text fence language into rendered prose |
| [#83448](https://github.com/NousResearch/hermes-agent/issues/83448) | Text-mode kanban queries DB after connection closed |
| [#47954](https://github.com/NousResearch/hermes-agent/issues/47954) | Memory provider race condition warning on startup |
| [#52179](https://github.com/NousResearch/hermes-agent/issues/52179) | Bedrock Guardrails configured but never enforced |

**Assessment:** The dominant stability theme is **Windows Desktop update/regression bugs** — at least 5 correlated issues (#83683, #84185, #83562, #63717, #68760, #82186) form a chain around the Windows update path and gateway lifecycle. macOS also has a similar regression (#84200). These are likely caused by recent gateway lineage changes (commits bc1223840d / 07298df805 / a9a0648f49 / 0b15eb5f05). A coordinated fix PR is needed.

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood |
|---|---|---|
| [#6839](https://github.com/NousResearch/hermes-agent/issues/6839) | **Lazy Tool Schema Loading** — Two-pass tool injection to cut 3,500–5,000 token overhead per call | High (18 upvotes, clear ROI) |
| [#83244](https://github.com/NousResearch/hermes-agent/issues/83244) | **Antigravity (Google) as OAuth provider** — Expose Claude Sonnet/Opus 4.6 + Gemini 3.x via Google OAuth | Medium (new provider, niche) |
| [#67440](https://github.com/NousResearch/hermes-agent/issues/67440) | **Blast-radius review mode** — Proof-backed safety facts for change impact assessment | Low–Medium (experimental) |
| [#72658](https://github.com/NousResearch/hermes-agent/issues/72658) | **Pre-completion vault verification gate** — Verify docs/vault before marking kanban tasks complete | Low (niche orchestration use case) |
| [#84209](https://github.com/NousResearch/hermes-agent/pull/84209) | **`host.attachFileToComposer()` SDK** — Stage files on chat composer from plugins | High (already in PR) |
| [#84192](https://github.com/NousResearch/hermes-agent/pull/84192) | **Rich plugin OS notifications** — Icons, action buttons, deeplink activation | High (already in PR) |
| [#84204](https://github.com/NousResearch/hermes-agent/pull/84204) | **Discard in-flight dictation** — Allow users to abort accidental recordings | Medium (UX polish) |
| [#84202](https://github.com/NousResearch/hermes-agent/pull/84202) | **OneBot 11 adapter for QQ** — Support NapCat/Lagrange/LLOneBot bridges | Medium-High (community-driven) |

**Prediction:** Lazy Tool Schema Loading (#6839) and the QQ OneBot adapter (#84202) are the most likely features to land in the next minor release, given community interest and active development respectively.

## 7. User Feedback Summary

**Pain Points:**
- **Windows Desktop update chain failure** is the #1 complaint — users report `hermes update` either locking files (WinError 32), failing with PermissionError (WinError 5), or spawning a gateway that dies silently. The root cause traces to Hermes-managed Node and venv `.pyd` lock behavior on Windows.
- **Gateway lifecycle regressions** post-commit d2a4d373eb affect both Windows and macOS: sessions created after `/reset` are invisible, and desktop-triggered updates SIGTERM the system-managed gateway on macOS.
- **Feishu multiplex mode** crashes with async loop mismatches, breaking Chinese enterprise users.
- **TTS silent degradation** — Vorbis-encoded Ogg files play poorly on platforms expecting Opus, causing voice bubbles to fail silently.
- **Honcho memory bloat** — Every conversation re-uploads the full local memory, causing duplicate profile entries to accumulate.

**Satisfaction Signals:**
- The MCP prefixed toolset fix (#78149) and kanban concurrency fixes (#78172, #78143) address real workflow friction and were merged promptly.
- The WhatsApp impersonation fix (#83432) responds to a legitimate security concern.
- File composer SDK (#84209) and rich notifications (#84192) show the team is investing in plugin extensibility.

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|---|---|---|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — Epic: Shard all 20 god files | 8 days | 67 comments, core architecture debt; sub-issue #78642 (`mcp_tool.py`, 7,230 lines) is the largest target |
| [#6839](https://github.com/NousResearch/hermes-agent/issues/6839) — Lazy Tool Schema Loading | 126 days | 38 comments, 18 upvotes; high user value but no PR yet |
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) — Multi-Tenant Hermes | 75 days | 25 comments; production users report running forked fixes; core architecture gap |
| [#63717](https://github.com/NousResearch/hermes-agent/issues/63717) — Windows Desktop update: 7 correlated root causes | 61 days | Comprehensive diagnostic with no merged fix; blocks Windows users |
| [#52179](https://github.com/NousResearch/hermes-agent/issues/52179) — Bedrock Guardrails never enforced | 80 days | Security-relevant; configured guardrails are a false sense of protection |
| [#67442](https://github.com/NousResearch/hermes-agent/issues/67442) — Cross-process turn serialization | 24 days | Follow-up to a closed issue; narrow but affects CLI-continuity power users |
| [#84200](https://github.com/NousResearch/hermes-agent/issues/84200) — macOS gateway SIGTERM on update | <1 day | Fresh regression, affects all macOS Desktop users with launchd-managed gateways |

**Recommendation:** The maintainers should prioritize a **Windows/macOS gateway lifecycle hotfix** (tying together #83683, #84185, #84200, #84109) before the next release, as these regressions collectively break the update-and-restart workflow for desktop users on both platforms.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-12

## 1. Today's Overview

PicoClaw shows moderate but focused development activity with 3 open issues and 6 open pull requests updated in the last 24 hours. No new releases were published. Activity is concentrated around bug fixes for agent routing, configuration handling, and LINE channel webhook support — suggesting the project is in a stabilization phase between feature releases. The presence of multiple `[stale]`-labeled PRs indicates some contributions are awaiting maintainer review, which warrants attention to avoid contributor fatigue.

## 2. Releases

**No new releases.** The latest known version remains **v0.3.1** (`2cf030d`). No migration notes or breaking changes to report.

## 3. Project Progress

**No PRs merged or issues closed today.** Six open PRs were updated, covering:

- **#3314** — Fixes `customAllowPatterns` being overridden by default deny patterns in `guardCommand`, resolving a security/UX regression where explicitly allowed shell commands (e.g., `git push`) were blocked. `[GitHub Link](https://github.com/sipeed/picoclaw/pull/3314)`
- **#3316** — Addresses routed-agent context management: dispatch rules to non-default agents now lose history, summarization, compression, and seahorse bootstrap state. `[GitHub Link](https://github.com/sipeed/picoclaw/pull/3316)`
- **#3315** — Adds Telegram private-chat topic support by recognizing `IsTopicMessage` alongside `IsForum`. `[GitHub Link](https://github.com/sipeed/picoclaw/pull/3315)`
- **#3317** — Enhances LLM debug logging to include prompt-cache token metadata from providers like DeepSeek via Cloudflare AI Gateway. `[GitHub Link](https://github.com/sipeed/picoclaw/pull/3317)`
- **#3299** — Introduces a native **Exa web search** provider with `type: "auto"` and date-range filters. `[GitHub Link](https://github.com/sipeed/picoclaw/pull/3299`)
- **#3329** — Fixes #3328 by warning on inert `webhook_host`/`webhook_port` config rather than silently seeding them. `[GitHub Link](https://github.com/sipeed/picoclaw/pull/3329)`

## 4. Community Hot Topics

| # | Type | Title | Comments | Link |
|---|------|-------|----------|------|
| #3301 | Issue | `/clear` and session auto-compression broken for routed agents | 3 | [Link](https://github.com/sipeed/picoclaw/issues/3301) |
| #3294 | Issue | `/list models` shows only current model | 3 | [Link](https://github.com/sipeed/picoclaw/issues/3294) |
| #3328 | Issue | LINE `webhook_host`/`webhook_port` never read | 0 | [Link](https://github.com/sipeed/picoclaw/issues/3328) |

**Analysis:** The two most-discussed issues (#3301 and #3294) both stem from **dispatch/routing logic** — users configuring multi-agent setups are hitting gaps in context management and model-listing consistency. This signals that as PicoClaw's routing features mature, edge cases in per-agent session state are becoming the primary friction point. The LINE webhook issue (#3328) is a configuration transparency problem with a fix already proposed (#3329).

## 5. Bugs & Stability

| Severity | Bug | Issue | Fix PR |
|----------|-----|-------|--------|
| **High** | Routed agents lose history, summarization, compression, and seahorse bootstrap | #3301 | #3316 (open, stale) |
| **Medium** | `customAllowPatterns` ignored — default deny takes precedence | — | #3314 (open) |
| **Medium** | `/list models` only shows current model, not all configured | #3294 | — |
| **Low** | LINE `webhook_host`/`webhook_port` silently ignored | #3328 | #3329 (open) |

No crashes or regressions reported today. The routing bug (#3301/#3316) is the most impactful — it affects multi-agent deployments and directly degrades user experience for a core feature.

## 6. Feature Requests & Roadmap Signals

- **Exa web search provider** (#3299) — Native integration would broaden tooling options beyond existing providers. Likely candidate for the next minor release if merged.
- **Telegram private-chat topics** (#3315) — Improves parity with Telegram's forum-topic feature in private bot chats. Low-risk, targeted fix.
- **Prompt cache token logging** (#3317) — Observability enhancement for cost-tracking users; low priority but valuable for power users.

**Prediction:** The next release (likely v0.3.2) will prioritize routing context fixes (#3316) and the Exa provider (#3299), given community interest and scope.

## 7. User Feedback Summary

**Pain points:**
- Multi-agent routing feels incomplete — users report broken session state and command-listing inconsistencies when dispatching to non-default agents (#3301, #3294).
- Security allow-lists (`customAllowPatterns`) not functioning as documented creates trust issues around agent sandboxing (#3314).
- LINE webhook configuration is misleading — docs and defaults exist but no code consumes them (#3328).

**Satisfaction signals:**
- Active contributions from multiple authors (j-v, genus, vmuliadi-astro, kesku, ex-takashima) indicate a engaged community.
- Bug reports are well-structured with environment details and reproduction steps, suggesting a mature user base.

## 8. Backlog Watch

| # | Type | Age | Risk |
|---|------|-----|------|
| #3316 | PR (stale) | 9 days | High — blocks routed-agent reliability |
| #3315 | PR (stale) | 9 days | Medium — Telegram feature gap |
| #3299 | PR (stale) | 17 days | Medium — feature request awaiting review |
| #3294 | Issue (stale) | 18 days | Low — cosmetic but confusing |
| #3314 | PR | 9 days | High — security allow-list regression |

**Recommendation:** Maintainers should prioritize reviewing #3316 and #3314, as both address correctness issues in core routing and permission logic. The stale labels on #3315 and #3299 suggest they may be deprioritized; a maintainer response would help set contributor expectations.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-12

## 1. Today's Overview

NanoClaw shows moderate but focused development activity with 7 pull requests and 1 open issue updated in the last 24 hours. The project is in an active consolidation phase, with core-team-driven work on agent template migration, transactional upgrades, and MCP server support. Three PRs were merged/closed today, indicating steady progress on long-standing features. No new releases were published. Issue #3226 remains open with no fix PR yet, representing the only active user-facing bug.

## 2. Releases

No new releases were published in the last 24 hours.

## 3. Project Progress

Three PRs were merged/closed today, each advancing a distinct area of the project:

- **Tavily MCP Tool Skill** (#3190, CLOSED) — A utility skill adding Tavily search capability as a standalone MCP tool, expanding the available skill ecosystem without requiring source-level changes.
- **Remote Streamable HTTP MCP Servers for Codex/OpenCode** (#3221, CLOSED) — Fixes a bug where remote HTTP MCP server configs would throw at write-time in the codex and opencode providers, now that the engine supports them (building on #3092).
- **Remote Streamable HTTP MCP Server Support** (#3092, CLOSED) — A core feature enabling `{ type: 'http', url }` entries in `mcpServers` across the engine and Claude provider, broadening integration flexibility.

Two additional open PRs continue to advance key infrastructure:

- **Agent Templates → Agent Plugins 1.0.0 Directories** (#3220, OPEN) — Major engine-level migration of the template feature into a plugin directory format, with security hardening (symlink stamp-time, caps, secret handling).
- **Transactional Upgrades** (#3195, OPEN) — Makes `nanoclaw update` safe against partial failures, a reliability improvement for production deployments.

## 4. Community Hot Topics

- **[Issue #3226](https://github.com/nanocoai/nanoclaw/issues/3226)** — *Inbound messages silently dropped when a platform reuses a message id*. Created by `dweekly`, this is the only open issue and the most discussed item today (1 comment). Users report that when a messaging platform reuses a message ID within the same session, inbound messages are silently dropped with no user-visible error — indistinguishable from the agent ignoring them. This points to a deduplication or id-tracking flaw in the message ingestion pipeline.

**Underlying need:** Reliable message delivery guarantees are critical for any agent platform. Silent message loss erodes trust and is especially damaging in conversational contexts where users expect every input to be acknowledged. A fix here would likely involve improving idempotency handling or adding fallback resolution when message IDs collide.

## 5. Bugs & Stability

| Severity | Item | Link | Fix PR? |
|----------|------|------|---------|
| **Medium** | Inbound messages silently dropped on platform message ID reuse (#3226) | [Issue #3226](https://github.com/nanocoai/nanoclaw/issues/3226) | No |
| **Low** | Codex/OpenCode providers rejected HTTP MCP server configs (#3221) | [PR #3221](https://github.com/nanocoai/nanoclaw/pull/3221) | ✅ Merged |

Issue #3226 is the primary stability concern. Silent message drops are harder to diagnose than crashes but can significantly degrade the user experience. The merged fix for #3221 resolved a prior configuration-level bug that affected remote MCP server users.

## 6. Feature Requests & Roadmap Signals

- **Agent Templates as Plugin Directories (#3220)** — The shift from "templates" to "Agent Plugins 1.0.0 directories" signals a roadmap direction toward a more modular, versioned plugin system. This is a major structural change that will likely define how third-party agent configurations are packaged and distributed.
- **Transactional Upgrades (#3195)** — Indicates a commitment to production-grade reliability; partial-update failures were a known pain point.
- **Remote MCP HTTP Support (#3092, #3221)** — The rapid follow-up from engine support to provider-specific fixes shows active investment in the MCP ecosystem, which is becoming a central integration layer.

**Prediction:** The next release will likely focus on stabilizing the plugin directory format (#3220) and shipping transactional upgrades (#3195) as reliability improvements, alongside any fixes for Issue #3226.

## 7. User Feedback Summary

- **Primary pain point:** Silent message loss when platforms reuse message IDs (#3226). Users describe this as functionally identical to "the agent ignored me," which is a serious trust issue.
- **Positive signal:** The community is actively contributing skills (Tavily MCP tool via #3190), suggesting a growing and engaged ecosystem.
- **Satisfaction driver:** Transactional upgrades (#3195) address a real operational concern for users who run NanoClaw in production or semi-production contexts.

## 8. Backlog Watch

- **[Issue #3226](https://github.com/nanocoai/nanoclaw/issues/3226)** — Open since 2026-08-10 with no fix PR. Medium-severity reliability bug with direct user impact. Needs maintainer attention.
- **[PR #3220](https://github.com/nanocoai/nanoclaw/pull/3220)** — Open since 2026-08-10. Major engine migration; requires careful review and likely a phased rollout.
- **[PR #3195](https://github.com/nanocoai/nanoclaw/pull/3195)** — Open since 2026-08-06. Important reliability improvement; stalled progress warrants a status check.
- **[PR #3145](https://github.com/nanocoai/nanoclaw/pull/3145)** — Open since 2026-07-28. Database migration to backfill destinations for existing wirings — a compatibility fix for long-term users that has been open for nearly two weeks.

---

**Overall Health Assessment:** Moderate activity with strong core-team momentum on infrastructure improvements. The main risk is the unresolved message-drop bug (#3226), which could erode user confidence if left unaddressed. The project is in a transition period (template → plugin architecture), which typically brings both opportunities and temporary instability.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-12

## 1. Today's Overview

IronClaw is experiencing **high activity** with 19 issues updated and 50 PRs touched in the last 24 hours, of which 25 were merged or closed — a strong signal of active development velocity. The project is in a major architectural transition ("Reborn"), with today's work heavily concentrated on three fronts: **kernel unification** (pluggable agent loops, context management), **channel unification** (single `ChannelAdapter` model for all integrations), and **storage decoupling** from deployment profiles. No new releases were published today. Maintainer engagement is dense, with `serrrfirat` driving most of the day's bug fixes and architectural decisions.

---

## 2. Releases

*No new releases today.*

---

## 3. Project Progress

### Merged / Closed PRs (25 total)

| PR | Summary |
|----|---------|
| [#7471](https://github.com/nearai/ironclaw/pull/7471) | **Lease expiry recovery** — expired automation runs now recover at replay-safe checkpoints instead of failing outright; journal heartbeats isolated from data-plane PostgreSQL traffic. |
| [#7514](https://github.com/nearai/ironclaw/pull/7514) | **Railway shell for hosted volume profile** — enables interactive shell access in Railway-hosted deployments via a strict release-only alias. |
| [#7470](https://github.com/nearai/ironclaw/pull/7470) | **Thread listability restored** — fixes a bug where `thread_index` rows without ordered-projection metadata were invisible in sidebar listings. |
| [#7480](https://github.com/nearai/ironclaw/pull/7480) | **Long conversation titles on hover** — introduces a `MarqueeText` component that shows truncated titles via horizontal marquee on hover. |
| [#6997](https://github.com/nearai/ironclaw/pull/6997) | **Explicit Anthropic `cache_control` breakpoints** — both rig adapter and OAuth transports now place explicit cache breakpoints, replacing unreliable automatic caching (P0 #1 of pi-harness program). |
| [#7503](https://github.com/nearai/ironclaw/pull/7503) | **Retain accepted task across context eviction** — pins the exact user task message across the 128-message tail cut; fails with `BudgetExceeded` instead of silently dropping oversized tasks. |
| [#7487](https://github.com/nearai/ironclaw/pull/7487) | **Fix `tool_search` disarming describe-first** — corrects a bug where `tool_search` marked tools as disclosed without returning schemas, breaking the safety net against blind-call spirals. |
| [#7488](https://github.com/nearai/ironclaw/pull/7488) | **Fix disclosure bridge tool concurrency** — removes hardcoded `Exclusive` hint on side-effect-free `tool_search`/`tool_describe`, preventing unnecessary serialization. |
| [#7405](https://github.com/nearai/ironclaw/pull/7405) | **Improve deferred tool discovery** — adds complete signatures and namespace-aware catalog previews, reducing avoidable model turns at scale. |

### Key Open PRs Advancing Today

| PR | Summary |
|----|---------|
| [#7477](https://github.com/nearai/ironclaw/pull/7477) | **Unified channel model** — replaces per-channel adapters with a single `ChannelAdapter` interface handling inbound, replies, and notifications for all channels (web, Slack, Telegram). |
| [#7456](https://github.com/nearai/ironclaw/pull/7456) | **Profile-agnostic durable storage** — roots Reborn storage at `IRONCLAW_REBORN_HOME` with namespace isolation (`state/`, `system/`, `workspaces/`, etc.), preventing data loss on profile switches. |
| [#7498](https://github.com/nearai/ironclaw/pull/7498) | **Automation suggestion cards V1 backend** — exposes `GET/POST /api/webchat/v2/suggestions` for home-screen automation suggestion generation. |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) | **IronHub agent link WebUI** — adds operator surface for registering and installing shared keys via the Extensions page, previously CLI-only. |
| [#7509](https://github.com/nearai/ironclaw/pull/7509) | **Secret redaction without turn rejection** — replaces credential-content rejection with deterministic redaction, preventing false positives from blocking prompts. |
| [#7365](https://github.com/nearai/ironclaw/pull/7365) | **Memory-save guidance + MEMORY.md prompt lane** — fixes cross-conversation memory recall by teaching models when to persist facts via `ironclaw.memory.write`. |
| [#7464](https://github.com/nearai/ironclaw/pull/7464) | **Telegram linked-device auth** — implements MTProto linked-device session custody with device-link auth and standard-op tools. |
| [#7512](https://github.com/nearai/ironclaw/pull/7512) | **Memory target alias resolution in domain layer** — fixes mem0 storing `target: "memory"` verbatim instead of resolving aliases, breaking canonical `MEMORY.md` reads. |
| [#7504](https://github.com/nearai/ironclaw/pull/7504) | **Compact context on window eviction** — converts silent 128-message eviction into typed forced-compaction, preserving assistant/tool-result exchanges. |
| [#7513](https://github.com/nearai/ironclaw/pull/7513) | **ACP serve CLI command** — exposes agent over Agent Communication Protocol via stdio, enabling external tools (VS Code, Copilot CLI) to connect. |
| [#7515](https://github.com/nearai/ironclaw/pull/7515) | **Slack standard ops expansion** — binds 8 of 16 core messaging operations (edit, delete, reactions, open_dm, resolve_user deferred). |

---

## 4. Community Hot Topics

| Issue / PR | Comments | Heat | Analysis |
|------------|----------|------|----------|
| [#7482](https://github.com/nearai/ironclaw/issues/7482) — *Epic: Pluggable agent loops* | 3 | 🔥 Highest | The defining architectural debate of the Reborn era: IronClaw as kernel vs. owning agent loops. Signals community expectation that the project become infrastructure, not an all-in-one agent. |
| [#7405](https://github.com/nearai/ironclaw/issues/7405) — *Deferred tool discovery* | 2 | 🔥 | Practical pain at scale — model turns accumulating with large tool catalogs. Reflects real usage growth. |
| [#7517](https://github.com/nearai/ironclaw/issues/7517) — *Staking path for Google/GitHub sign-ins* | 0 (new today) | 🔥 | New user-facing friction: Cloud.near.ai OAuth logins can't stake for inference. Points to onboarding gap for non-NEAR-native users. |
| [#6879](https://github.com/nearai/ironclaw/issues/6879) — *Automation runs hit-or-miss* | 0 (open since Jul 29) | ⚠️ | Structural reliability issue for unattended automation — directly impacts production trust. |
| [#7038](https://github.com/nearai/ironclaw/issues/7038) — *Storybook + AI-first Design System* | 0 (linked PRs active) | 🔥 | Long-running design-system epic; PR #7498 (suggestion cards) is a concrete deliverable under it. |

**Underlying needs:** The community is pushing for (1) architectural clarity around the kernel vs. agent boundary, (2) reliability in automation/long-running runs, (3) smoother onboarding for non-crypto-native users, and (4) a consistent design language as the product matures.

---

## 5. Bugs & Stability

| Severity | Issue | Status | Fix PR |
|----------|-------|--------|--------|
| **P0** | [#7485](https://github.com/nearai/ironclaw/issues/7485) — *Token estimator double-counts ASCII, halving effective context window* | Open | [#7504](https://github.com/nearai/ironclaw/pull/7504) (in progress) |
| **P0** | [#7484](https://github.com/nearai/ironclaw/issues/7484) — *Context window silently evicts task at 128-message clamp* | Open | [#7503](https://github.com/nearai/ironclaw/pull/7503) ✅ merged |
| **High** | [#7487](https://github.com/nearai/ironclaw/issues/7487) — *`tool_search` disarms describe-first safety net* | Closed | [#7487](https://github.com/nearai/ironclaw/pull/7487) ✅ merged |
| **High** | [#7488](https://github.com/nearai/ironclaw/issues/7488) — *Disclosure tools hardcoded Exclusive, discarding batch tails* | Closed | [#7488](https://github.com/nearai/ironclaw/pull/7488) ✅ merged |
| **High** | [#7490](https://github.com/nearai/ironclaw/issues/7490) — *`retry_disposition()` silent-redrive table is dead code* | Open | None yet |
| **High** | [#7486](https://github.com/nearai/ironclaw/issues/7486) — *No-progress escape false-positives on idempotent reads* | Open | None yet |
| **Medium** | [#7505](https://github.com/nearai/ironclaw/issues/7505) — *Memory target-alias resolution only in one provider* | Open | [#7512](https://github.com/nearai/ironclaw/pull/7512) (in progress) |
| **Medium** | [#7508](https://github.com/nearai/ironclaw/issues/7508) — *GitHub MCP extension startup gives confusing endpoint prompt* | Open | None yet |
| **Low** | [#7483](https://github.com/nearai/ironclaw/issues/7483) — *Default NEAR AI connection fails with blank API key* | Closed | [#7483](https://github.com/nearai/ironclaw/pull/7483) ✅ merged |

**Assessment:** Two P0 context/window bugs remain open but have active fix PRs. The `retry_disposition` dead code and no-progress false-positive issues are notable reliability gaps with no fixes yet. Overall, the bug closure rate today (6 closed) is healthy relative to new open issues.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Likelihood for v1.3.0 |
|---------|----------|----------------------|
| **ACP CLI serve command** — external tool connectivity via stdio | [#7513](https://github.com/nearai/ironclaw/pull/7513) | **High** — directly enables the "pluggable agent loop" thesis from #7482; already implemented. |
| **IdentyClaw Passport integration** — host-mediated auth for practitioners | [#7496](https://github.com/nearai/ironclaw/issues/7496) | **Medium** — niche but addresses a real practitioner workflow gap. |
| **Google/GitHub sign-in with staking path** | [#7517](https://github.com/nearai/ironclaw/issues/7517) | **Medium** — user-reported friction; small scope, high UX impact. |
| **Automation suggestion cards** | [#7498](https://github.com/nearai/ironclaw/pull/7498) | **High** — backend implemented; likely v1.3.0 candidate. |
| **Telegram linked-device auth** | [#7464](https://github.com/nearai/ironclaw/pull/7464) | **High** — full implementation ready; strong channel-completion signal. |
| **Unified channel model** | [#7477](https://github.com/nearai/ironclaw/pull/7477) | **High** — foundational refactor; likely shipped as a unit. |
| **Design system / Storybook** | [#7038](https://github.com/nearai/ironclaw/issues/7038) | **Medium** — epic-sized; suggestion cards are a partial delivery. |
| **Slack extended ops** (edit, delete, reactions, etc.) | [#7515](https://github.com/nearai/ironclaw/pull/7515) | **Medium** — deliberately deferred; fast-follow listed in spec. |

**Roadmap signal:** The project is clearly targeting v1.3.0 around channel unification, memory reliability, and kernel-level architecture. The "Reborn" epic is the dominant framework, with everything flowing through it.

---

## 7. User Feedback Summary

| Pain Point | Source | Sentiment |
|------------|--------|-----------|
| Long conversation titles are truncated with no way to read them | #7481 / PR #7480 | Frustration → **Resolved** (marquee on hover) |
| Automation runs succeed unpredictably, especially on small models | #6879 | **High concern** — structural reliability issue affecting production use |
| OAuth sign-ins (Google/GitHub) can't stake for inference | #7517 | Onboarding friction for non-NEAR-native users |
| Cross-conversation memory recall fails — facts stated in one chat aren't recalled in another | #7185 / PR #7365 | **Critical** for agent utility; fix in progress |
| GitHub MCP extension gives confusing startup errors | #7508 | UX clarity issue |
| Default NEAR AI connection fails with blank API key | #7483 | **Resolved** — now uses authenticated session |
| Profile switch makes existing deployments appear empty | #7467 / PR #7456 | Data-loss risk; **partially resolved** by profile-agnostic storage PR |
| `result_read` 24 KiB preview ceiling inflates round-trips | #7489 | Performance concern for coding workflows |
| Token estimator double-counting halves effective context | #7485 | **High impact** — silently degrades performance; fix in progress |

---

## 8. Backlog Watch

| Issue

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-12

---

## 1. Today's Overview

LobsterAI showed solid development momentum on 2026-08-11/12, with 4 issues and 9 PRs updated in the past 24 hours, including one new release (v2026.8.11). Activity is release-driven: the 2026.8.11 version shipped several feature improvements (configurable thinking levels, scheduled-task sidebar markers, collapse shortcuts) alongside notable bug fixes (per-model thinking-level isolation, settings unsaved-changes confirmation, modal Escape dismissal). Three of four closed issues were resolved via PRs today, indicating strong triage velocity. One open issue (#1183 — gateway startup loop) remains unresolved and may warrant priority attention.

---

## 2. Releases

### v2026.8.11 (2026-08-11)
[Release PR #2477](https://github.com/netease-youdao/LobsterAI/pull/2477)

**Key changes:**
- **Configurable thinking levels** per model — each model now independently remembers its thinking depth setting (PR #2475, PR #2457)
- **Scheduled-task identification** in the Cowork sidebar (PR #2469)
- **Collapse-agent-tasks shortcut** with modifier support while typing (PR #2469)
- **Settings dirty-check** — unsaved changes now trigger a confirmation dialog before closing (PR #1241, closes #1237)
- **Modal Escape key handling** — topmost overlay dismisses cleanly on Escape, even with nested modals (PR #2476)
- Task-completion window attention (flash/bounce) on Windows/macOS (PR #1239)
- Various stability and runtime reliability improvements

**Breaking changes / Migration notes:** None reported. Per-model thinking-level persistence is transparent to existing users.

---

## 3. Project Progress

**Merged / Closed PRs today:**

| PR | Area | Summary |
|----|------|---------|
| [#2475](https://github.com/netease-youdao/LobsterAI/pull/2475) | renderer | Fix: each model now has its own independent thinking-level setting (was globally shared) |
| [#2477](https://github.com/netease-youdao/LobsterAI/pull/2477) | release | Release/2026.8.10 → main merge |
| [#2476](https://github.com/netease-youdao/LobsterAI/pull/2476) | renderer/im | Fix: modal portal to `document.body`; Escape dismisses topmost layer correctly |
| [#2457](https://github.com/netease-youdao/LobsterAI/pull/2457) | models | Feat: server-driven configurable thinking levels with per-session and per-agent persistence |
| [#1239](https://github.com/netease-youdao/LobsterAI/pull/1239) | main | Feat: taskbar/Dock icon flash/bounce on task completion (Windows/macOS) |
| [#1241](https://github.com/netease-youdao/LobsterAI/pull/1241) | settings | Feat: unsaved-changes confirmation before closing Settings dialog (closes #1237) |
| [#2474](https://github.com/netease-youdao/LobsterAI/pull/2474) | sidebar | Fix: align sites icon stroke weight |

**In review / open:**
- [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Dependabot Electron group bump (40.2.1 → 43.3.0); still open since April
- [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) — Hide main agent sessions from Cowork session list; open since April

---

## 4. Community Hot Topics

| Issue/PR | Status | Comments | Key Discussion |
|----------|--------|----------|----------------|
| [#1237](https://github.com/netease-youdao/LobsterAI/issues/1237) | ✅ Closed | 2 | Settings unsaved changes silently lost — resolved via PR #1241 |
| [#1240](https://github.com/netease-youdao/LobsterAI/issues/1240) | ✅ Closed | 2 | API rate-limit cascade: single provider throttled → all sessions fail; users need better provider failover |
| [#2062](https://github.com/netease-youdao/LobsterAI/issues/2062) | ✅ Closed | 2 | Long-running tasks (24h+) hit timeout and silently stop — unclear whether task is still active in background |
| [#1183](https://github.com/netease-youdao/LobsterAI/issues/1183) | ⏳ Open | 1 | Gateway startup loop on Windows — persistent blocker for some users |

**Underlying needs:**
- **Provider resilience**: Issue #1240 reveals a critical gap — when one API provider is rate-limited, the entire app becomes unusable. Users expect automatic fallback or per-session provider isolation.
- **Long-duration task transparency**: Issue #2062 highlights a UX gap around task timeout feedback — users cannot tell whether a timed-out task is still running or truly stopped.
- **Configuration safety**: Issue #1237 (now fixed) reflects a broader expectation that app settings should protect users from accidental data loss.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| 🔴 High | [#1183](https://github.com/netease-youdao/LobsterAI/issues/1183) | Gateway startup loop — modal overlay continuously reopens after saving model config | ❌ No fix yet; PR #1181 (open) may be tangentially related |
| 🟡 Medium | [#1240](https://github.com/netease-youdao/LobsterAI/issues/1240) | API rate-limit on one provider causes global app paralysis | ❌ No fix; users report workaround is restarting with a prior config backup |
| 🟡 Medium | [#2062](https://github.com/netease-youdao/LobsterAI/issues/2062) | 24h tasks time out with unclear stop/resume state | ❌ No fix; timeout behavior and background execution clarity needed |
| 🟢 Low | (internal) | Thinking-level settings were globally shared across models | ✅ Fixed in PR #2475 |
| 🟢 Low | (internal) | Modal Escape key did not dismiss nested overlays | ✅ Fixed in PR #2476 |
| 🟢 Low | (internal) | Settings close without saving changes confirmation | ✅ Fixed in PR #1241 |

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Likelihood for Next Release |
|--------|--------|----------------------------|
| **Per-model thinking level** | PR #2457, #2475 (merged) | ✅ Already shipped in 2026.8.11 |
| **Scheduled-task sidebar identification** | PR #2469 (merged) | ✅ Shipped |
| **Collapse-agent-tasks shortcut** | PR #2469 (merged) | ✅ Shipped |
| **Automatic API provider failover** | Issue #1240 (closed, unresolved root cause) | 🟡 Likely roadmap — high user impact |
| **Task timeout visibility / background state** | Issue #2062 (closed, unresolved) | 🟡 Moderate — improves long-task UX |
| **Hide internal main-agent sessions** | PR #1181 (open since April) | 🟡 Possible — low user-facing impact but reduces confusion |
| **Electron 43 upgrade** | PR #1277 (open since April) | 🟡 Dependabot-maintained; likely next when Electron security patches require it |

---

## 7. User Feedback Summary

- **Satisfaction drivers**: The configurable thinking-level feature and scheduled-task UI improvements are well-received; users appreciate per-model independence and better sidebar organization.
- **Pain points**:
  - *"I modified my API key in Settings, closed the dialog by accident, and lost everything."* — Issue #1237 (now fixed)
  - *"One API provider got rate-limited and my entire app went dead — I had to restore a backup config."* — Issue #1240
  - *"My 24-hour task timed out and I have no idea if it's still running in the background."* — Issue #2062
  - *"The gateway startup modal keeps looping infinitely after I save model settings."* — Issue #1183
- **Overall sentiment**: The project is actively addressing UX friction (settings safety, modal behavior, thinking-level independence). However, reliability concerns around API provider resilience and long-running task management remain open and could erode trust among power users who run extended autonomous tasks.

---

## 8. Backlog Watch

| Item | Age | Priority | Note |
|------|-----|----------|------|
| [#1183](https://github.com/netease-youdao/LobsterAI/issues/1183) — Gateway startup loop | ~4 months | 🔴 High | Windows-specific; persistent modal loop blocks normal usage. No fix PR yet. |
| [#1240](https://github.com/netease-youdao/LobsterAI/issues/1240) — Global paralysis on single API limit | ~4 months | 🔴 High | Rate-limit handling and per-session provider routing are missing. |
| [#2062](https://github.com/netease-youdao/LobsterAI/issues/2062) — 24h task timeout ambiguity | ~2.5 months | 🟡 Medium | Users need clear task-state feedback after timeout. |
| [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) — Hide main-agent sessions | ~4 months | 🟢 Low | Useful cleanup but non-blocking; remains open. |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Electron 40→43 bump | ~4 months | 🟢 Low | Routine dependency update; should be merged when CI is green. |

**Summary**: Three of the four most impactful open items (gateway loop, API failover, task timeout) have been marked `[stale]` despite significant user impact. These deserve maintainer re-engagement in the next cycle.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-12

## 1. Today's Overview

Moltis activity today is **low to moderate**, with no new issues, merged PRs, or releases published in the last 24 hours. The only notable update is **PR #1190**, an open pull request introducing durable local CalDAV connectors with persistent storage, atomic snapshots, and local full-text search. No closed or merged items were recorded, suggesting a quiet development day. Overall project health appears stable with no reported regressions or blockers.

---

## 2. Releases

No new releases today.

---

## 3. Project Progress

- **Merged/Closed PRs today:** None
- **Active PR:** [#1190 — Add durable local CalDAV connectors](https://github.com/moltis-org/moltis/pull/1190) (open, awaiting review/merge)
  - This PR represents a **significant feature advance**, introducing:
    - Provider-neutral connector persistence layer
    - Atomic CalDAV snapshots for data integrity
    - Local scheduling and projections
    - Bounded local full-text search
    - Prompt-compiled dataset plans
    - A trusted read-only `connectors` agent tool for local dataset access
    - New Settings > Connectors UI for account, dataset, and permissions management
  - Once merged, this will materially expand Moltis's local-first data connectivity and caldav integration capabilities.

---

## 4. Community Hot Topics

| Item | Type | Activity |
|------|------|----------|
| [#1190 — Add durable local CalDAV connectors](https://github.com/moltis-org/moltis/pull/1190) | PR (open) | Author: *penso*; 0 reactions |

**Analysis:** The sole active item is a feature PR rather than a community-driven discussion. No issues or PRs currently show high comment/reaction volume. The absence of hot topics suggests a calm community cycle, with the CalDAV connector PR being the primary technical focus.

---

## 5. Bugs & Stability

No bugs, crashes, or regressions reported today.

---

## 6. Feature Requests & Roadmap Signals

- **[#1190 — Add durable local CalDAV connectors](https://github.com/moltis-org/moltis/pull/1190)** is both a PR and a strong roadmap signal. The breadth of the change — persistence, atomic snapshots, local search, and a read-only agent tool — indicates Moltis is advancing its **local-first, privacy-preserving agent architecture**. This feature is likely headed toward the next minor release if merged.

---

## 7. User Feedback Summary

No new user feedback (issues, comments, or reactions) was recorded today. The CalDAV connector PR addresses an implicit user need for **local, durable calendar data integration** with agent-tool accessibility, suggesting growing demand for private, on-device data handling in the Moltis ecosystem.

---

## 8. Backlog Watch

No long-unanswered issues or stalled PRs were flagged in today's data. The single open PR (#1190) is recent (created 2026-08-11) and actively authored, so no immediate backlog concern is warranted. Maintainers should monitor this PR for review turnaround given its size and scope.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw / QwenPaw Project Digest — 2026-08-12

## 1. Today's Overview

The project remains in an active pre-release sprint toward **v2.1.0**, with **22 issues** and **49 PRs** touched in the last 24 hours. One new beta — **v2.1.0-beta.3** — was published, alongside a version bump to **v2.1.0b4**. Community momentum is strong: 13 issues were closed and 26 PRs merged/closed, indicating healthy triage throughput. Several open issues flag stability regressions (crashes, IME UI failures, idle CPU spin) that warrant attention before a stable v2.1.0 launch.

## 2. Releases

### v2.1.0-beta.3 *(published 2026-08-11)*

**What's Changed:**
- **Feats/files workspace blog** — added a workspace blog feature (`#6783`)
- **Fix (provider): expire stale capability cache entries and clear on model switch** — addresses a caching bug where capability lookups became stale after switching providers/models (`#6723`)
- **Chore: version bump to 2.1.0b4** (`#6920`)

**Migration notes:** No breaking changes announced. The stale cache fix may alter behavior for users on multi-model setups; a full restart is recommended after upgrading.

## 3. Project Progress

**Key PRs merged/closed today:**

| PR | Description | Status |
|---|---|---|
| [#6920](https://github.com/agentscope-ai/QwenPaw/pull/6920) | Bump version to 2.1.0b4 | ✅ Merged |
| [#6898](https://github.com/agentscope-ai/QwenPaw/pull/6898) | Fix `read_file` tool description mismatch | ✅ Closed |
| [#6915](https://github.com/agentscope-ai/QwenPaw/pull/6915) | Fix file previews (Unicode PDFs, SVGs, dark mode alignment) | ✅ Closed |
| [#6911](https://github.com/agentscope-ai/QwenPaw/pull/6911) | Unify code block rendering (LaTeX & Mermaid preview/source tabs) | ✅ Closed |
| [#6909](https://github.com/agentscope-ai/QwenPaw/pull/6909) | Warn when a bot is already used by another agent | ✅ Closed |
| [#6564](https://github.com/agentscope-ai/QwenPaw/pull/6564) | Flush pending memory turns before compression | ✅ Closed |
| [#6891](https://github.com/agentscope-ai/QwenPaw/pull/6891) | Improve native Computer Use input workflows | ✅ Closed |
| [#6875](https://github.com/agentscope-ai/QwenPaw/pull/6875) | Update v2.1.0 release notes (multi-language README sync) | ✅ Closed |

**Notable PRs still open / under review:**
- [#6830](https://github.com/agentscope-ai/QwenPaw/pull/6830) — Preserve auto-memory state across compression and session lifecycles (high-impact fix)
- [#6880](https://github.com/agentscope-ai/QwenPaw/pull/6880) — Unify apps, plugins, and skills marketplace UI
- [#6874](https://github.com/agentscope-ai/QwenPaw/pull/6874) — Configurable MCP tool-call timeout (default 120s)
- [#6779](https://github.com/agentscope-ai/QwenPaw/pull/6779) — Align Scroll context with AgentScope lifecycle
- [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) — Unify provider discovery, model metadata, and routing
- [#6873](https://github.com/agentscope-ai/QwenPaw/pull/6873) — Normalize legacy local-path media sources

## 4. Community Hot Topics

| Issue | Topic | Comments | Link |
|---|---|---|---|
| [#6732](https://github.com/agentscope-ai/QwenPaw/issues/6732) | MCP tools periodically stop working; requires Docker restart | 10 | [link](https://github.com/agentscope-ai/QwenPaw/issues/6732) |
| [#6893](https://github.com/agentscope-ai/QwenPaw/issues/6893) | Formula rendering (LaTeX/KaTeX), chat grouping, active session backgrounds | 7 | [link](https://github.com/agentscope-ai/QwenPaw/issues/6893) |
| [#5790](https://github.com/agentscope-ai/QwenPaw/issues/5790) | Loading spinner never disappears after agent response | 4 | [link](https://github.com/agentscope-ai/QwenPaw/issues/5790) |
| [#5453](https://github.com/agentscope-ai/QwenPaw/issues/5453) | KaTeX / LaTeX rendering support request | 2 | [link](https://github.com/agentscope-ai/QwenPaw/issues/5453) |
| [#4154](https://github.com/agentscope-ai/QwenPaw/issues/4154) | Adjustable font size, background service mode, clickable file paths | 2 | [link](https://github.com/agentscope-ai/QwenPaw/issues/4154) |

**Underlying needs:** The top-voted recurring themes are **mathematical formula rendering** (issues #5453 and #6893, both now closed with the v2.1.0 code-block unification PR #6911), **MCP reliability** (#6732), and **UI polish** (loading states, font scaling, session organization). The community is clearly pushing for a more mature desktop-class UX in v2.1.0.

## 5. Bugs & Stability

### 🔴 Critical / High Severity

| Issue | Description | Fix PR? | Link |
|---|---|---|---|
| [#6919](https://github.com/agentscope-ai/QwenPaw/issues/6919) | v2.0.1 frequent crashes — `console process/reply failed` traceback | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6919) |
| [#6885](https://github.com/agentscope-ai/QwenPaw/issues/6885) | Console UI crashes on Chinese IME `compositionEnd` during agent run (v2.1.0b2) | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6885) |
| [#6697](https://github.com/agentscope-ai/QwenPaw/issues/6697) | v2.1.0-beta.1 Desktop injects `PYTHONHOME` → all Python subprocesses crash with `ModuleNotFoundError` | ⚠️ Partially — beta.3 release may address | [link](https://github.com/agentscope-ai/QwenPaw/issues/6697) |
| [#6732](https://github.com/agentscope-ai/QwenPaw/issues/6732) | MCP tools lose registration periodically; restart required | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6732) |

### 🟡 Medium Severity

| Issue | Description | Fix PR? | Link |
|---|---|---|---|
| [#6828](https://github.com/agentscope-ai/QwenPaw/issues/6828) | Console frontend idle repaint (~20% CPU) from infinite CSS animations | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6828) |
| [#6918](https://github.com/agentscope-ai/QwenPaw/issues/6918) | Inter-agent messages spawn new agent session per message (shadow instances) | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6918) |
| [#6916](https://github.com/agentscope-ai/QwenPaw/issues/6916) | Plugins can silently create cron jobs and inject messages without approval | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6916) |
| [#6722](https://github.com/agentscope-ai/QwenPaw/issues/6722) | Background forked subagent reports completion when worktree finalization fails | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6722) |
| [#6883](https://github.com/agentscope-ai/QwenPaw/issues/6883) | Diary page groups subfolder notes under wrong date | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/6883) |
| [#6910](https://github.com/agentscope-ai/QwenPaw/issues/6910) | Invalid single-channel config payload returns HTTP 500 | ⚠️ PR #6910 open | [link](https://github.com/agentscope-ai/QwenPaw/issues/6910) |

### 🟢 Low Severity

| Issue | Description | Fix PR? | Link |
|---|---|---|---|
| [#5790](https://github.com/agentscope-ai/QwenPaw/issues/5790) | Loading animation persists after agent response completes | ❌ No fix yet | [link](https://github.com/agentscope-ai/QwenPaw/issues/5790) |
| [#6901](https://github.com/agentscope-ai/QwenPaw/issues/6901) | Repeated GitHub links in UI | ✅ Likely addressed | [link](https://github.com/agentscope-ai/QwenPaw/issues/6901) |

**Assessment:** Six high-priority stability/security issues remain unfixed and could block a stable v2.1.0 release. The IME crash (#6885) and periodic MCP failure (#6732) are the most user-impacting.

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Request | Likelihood for v2.1.0 |
|---|---|---|
| [#6917](https://github.com/agentscope-ai/QwenPaw/issues/6917) | Agent-driven inbox delivery for structured reports | ⚠️ Mid-term; not in beta.3 scope |
| [#6874](https://github.com/agentscope-ai/QwenPaw/pull/6874) | Configurable MCP tool-call timeout | ✅ Likely in v2.1.0 (open, well-scoped) |
| [#6877](https://github.com/agentscope-ai/QwenPaw/pull/6877) | Remember desktop window geometry (position & size) | ✅ Likely in v2.1.0 (open, minimal risk) |
| [#6880](https://github.com/agentscope-ai/QwenPaw/pull/6880) | Unified marketplace (apps + plugins + skills) | ✅ Likely in v2.1.0 (under review) |
| [#5869](https://github.com/agentscope-ai/QwenPaw/pull/5869) | Expose system slash commands in TUI & Console autocomplete | ⚠️ Possible; still open |
| [#5490](https://github.com/agentscope-ai/QwenPaw/pull/5490) | Fullscreen image gallery for chat media | ⚠️ Possible; still open |
| [#6817](https://github.com/agentscope-ai/QwenPaw/pull/6817) | Integrate AnySearch as built-in web search (replacing Tavily) | ⚠️ Possible; under review |
| [#6913](https://github.com/agentscope-ai/QwenPaw/pull/6913) | macOS Computer Use element activation improvements | ✅ Likely in v2.1.0 (small fix) |
| [#6897](https://github.com/agentscope-ai/QwenPaw/issues/6897) | Reduce QQ bot message noise / workflow info flooding | ⚠️ Low priority; user-configurable |

**Prediction:** v2.1.0 stable will likely include the MCP timeout, window geometry persistence, unified marketplace, macOS Computer Use fix, and code block unification. The inbox feature and AnySearch integration are more likely v2.2 candidates.

## 7. User Feedback Summary

**Pain points:**
1. **MCP reliability** — tools randomly stop working and require a full container/app restart (#6732, 10 comments). This is the most frequently discussed stability concern.
2. **Chinese IME compatibility** — the Console UI becomes unusable during agent runs when typing in Chinese

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-12

## 1. Today's Overview

ZeroClaw activity remains high with 50 issues and 50 PRs updated in the last 24 hours, though no new releases were shipped. The project is in a design-heavy phase: the majority of today's traffic comes from RFC discussions rather than merged code, with only one PR closed (#9936 — upstream security cherry-picks). Maintainer review bandwidth appears to be the primary bottleneck, as numerous P1/P2 RFCs carry the `needs-maintainer-review` label. Overall project health is strong on community engagement but shows a bottleneck at the acceptance gate.

## 2. Releases

No new releases were published. The last recorded release window produced zero version bumps.

## 3. Project Progress

**Merged/Closed today:**
- [#9936](https://github.com/zeroclaw-labs/zeroclaw/issues/9936) — Cherry-picked nine upstream security and correctness fixes into the release branch.

**PRs actively discussed today (updated 2026-08-12):**
- [#9765](https://github.com/zeroclaw-labs/zeroclaw/pull/9765) — Fix: SOP definitions now load from the shared workspace instead of `data_dir`, resolving a dual-role bug in `build_sop_engine`.
- [#9885](https://github.com/zeroclaw-labs/zeroclaw/pull/9885) — Fix: Daemon now honours the documented `sops_dir` default, closing [#9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779).
- [#9819](https://github.com/zeroclaw-labs/zeroclaw/pull/9819) — Fix: Adds pixel-level image validation to prevent corrupt images from failing provider requests.
- [#9926](https://github.com/zeroclaw-labs/zeroclaw/pull/9926) — Fix: PWA manifest and apple-touch-icon added so installed dashboards display the correct logo.
- [#9385](https://github.com/zeroclaw-labs/zeroclaw/pull/9385) — Feature: `request_approval` implemented for WhatsApp Web, enabling human-in-the-loop tool approval.
- [#9854](https://github.com/zeroclaw-labs/zeroclaw/pull/9854) — Fix: Context-window discovery now derives from the family registry instead of a hardcoded eight-name list.
- [#9419](https://github.com/zeroclaw-labs/zeroclaw/pull/9419) — Fix: Live credential rotation after rate-limit (429) responses, binding retries to the correct credential.
- [#9911](https://github.com/zeroclaw-labs/zeroclaw/pull/9911) — Fix: Matrix `mention_only` now admits bot replies without a fresh @-mention.
- [#9918](https://github.com/zeroclaw-labs/zeroclaw/pull/9918) — Fix: Gateway now accepts full `session_key` on abort/rename/state/message_post without double-prefixing.
- [#9862](https://github.com/zeroclaw-labs/zeroclaw/pull/9862) — Fix: Bounds direct HTTP response handling with streaming and redirect control.

## 4. Community Hot Topics

| Issue | Comments | Topic |
|-------|----------|-------|
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | 19 | Goal mode v1 — bounded multi-turn foreground work |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | 18 | Chat Completions profile (OpenAI protocol compatibility) |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | 17 | Per-execution confirmation tier for high-risk shell commands |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) | 14 | Pluggable inbound authentication & canonical principals |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | 13 | Maintainer decision queue tracker |
| [#2269](https://github.com/zeroclaw-labs/zeroclaw/issues/2269) | 13 | Token consumption & cost management (closed, no resolution) |

**Analysis:** The community is heavily focused on two axes: **agent durability** (goal mode, runtime-owned sessions, SOP control plane) and **interoperability** (Chat Completions profile, LSP support, slash-command unification). Security architecture (pluggable auth, shell confirmation tiers, restrictive overlays) also draws sustained attention. The lack of reactions (👍) across most top issues suggests reviewers are still in evaluation mode rather than endorsement mode.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|----------|-------|---------|--------|
| **P1 / High** | [#9883](https://github.com/zeroclaw-labs/zeroclaw/issues/9883) | Inbound WebP conversion decodes unbounded before image validator runs | Related to [#9819](https://github.com/zeroclaw-labs/zeroclaw/pull/9819) (pixel-level validation) |
| **P1 / High** | [#9872](https://github.com/zeroclaw-labs/zeroclaw/issues/9872) | Bounded delegate resolves filesystem to delegator's workspace instead of own | Open — no fix PR yet |
| **P1 / Medium** | [#9768](https://github.com/zeroclaw-labs/zeroclaw/issues/9768) | Daemon reload signal mismatch: SIGUSR1 kills instead of reloading | Closed — documented as degraded behavior |
| **P2 / High** | [#9035](https://github.com/zeroclaw-labs/zeroclaw/issues/9035) | Docker Compose gateway remains loopback-bound behind published port | Closed — no fix merged |

**Assessment:** Two outstanding P1 bugs relate to security sandboxing (workspace isolation and unbounded image decoding). Both are high-risk but have related PRs in flight or are blocked on maintainer review. No crashes or data-loss regressions reported today.

## 6. Feature Requests & Roadmap Signals

| RFC | Status | Likelihood for Next Release |
|-----|--------|----------------------------|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — Chat Completions profile | Active discussion (18 comments) | **High** — broad client compatibility demand; multiple PRs in flight |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) — Goal mode v1 | Active (19 comments) | **Medium** — scope still being narrowed; coupled with session architecture |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Shell confirmation tier | Rev 3, scope confirmed | **Medium** — P1 security priority; Phase 0 narrowing applied |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — Runtime-owned sessions | Rev 2, accepted boundary | **High** — foundational for goal mode and SOP control plane |
| [#5907](https://github.com/zeroclaw-labs/zeroclaw/issues/5907) — LSP support for ZeroCode | Active (6 comments) | **Low-Medium** — opt-in, lower priority than security RFCs |

The v0.9.0 security architecture milestone is the clearest near-term target, with multiple RFCs (#7141, #7142, #9598) explicitly scoped to it.

## 7. User Feedback Summary

- **OpenAI protocol compatibility** is the strongest signal: [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) explicitly names Open WebUI, LobeChat, Continue.dev, Aider, and LangChain as target clients. Users want ZeroClaw agents behind a familiar API surface.
- **Cost control** remains a pain point: [#2269](https://github.com/zeroclaw-labs/zeroclaw/issues/2269) (closed without resolution) highlights that single-model agent workloads are prohibitively expensive for end users.
- **Security trust gaps**: Users are reporting real sandbox escape concerns — delegate workspace leakage ([#9872](https://github.com/zeroclaw-labs/zeroclaw/issues/9872)) and unbounded image decoding ([#9883](https://github.com/zeroclaw-labs/zeroclaw/issues/9883)) suggest the security model needs harder boundaries before production adoption.
- **WhatsApp approval workflow** ([#9385](https://github.com/zeroclaw-labs/zeroclaw/pull/9385)) fills a genuine gap: tools in `always_ask` mode were default-denying on WhatsApp instead of prompting the user.
- **Matrix follow-up drops**: [#9911](https://github.com/zeroclaw-labs/zeroclaw/pull/9911) addresses a UX break where reply-to-bot messages were silently dropped under `mention_only`.

## 8. Backlog Watch

| Issue | Days Open | Why It Needs Attention |
|-------|-----------|----------------------|
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | ~39 | The maintainer decision queue tracker itself is stalled — RFCs are piling up without decisions |
| [#9496](https://github.com/zeroclaw-labs/zeroclaw/issues/9496) | ~15 | RFC process streamlining accepted but not yet implemented; current 7-day min discussion + unanimity requirements are slowing all other RFCs |
| [#2269](https://github.com/zeroclaw-labs/zeroclaw/issues/2269) | ~164 | Token cost management RFI closed without direction; community signal was clear but no follow-up |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | ~49 | Goal mode v1 has 19 comments but no acceptance decision; scope decoupling is ongoing |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) | ~70 | Shell confirmation tier at Rev 3 with confirmed scope — awaiting maintainer merge decision |

**Key risk:** The maintainer review bottleneck is slowing the entire RFC pipeline. Five P1 RFCs are tagged `needs-maintainer-review` with no recent movement. The project's design momentum is strong, but without maintainer decisions the conversion rate from RFC to merged PR will remain low.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*