# OpenClaw Ecosystem Digest 2026-08-23

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-23 01:46 UTC

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



# OpenClaw Project Digest — 2026-08-23

---

## 1. Today's Overview

OpenClaw is operating at high velocity with **500 issues and 500 PRs updated** in the last 24 hours, indicating intense community engagement and active maintenance. The project is currently in a **beta validation phase** for v2026.8.1-beta.2, with the top discussion centered on release readiness and a recurring SQLite corruption regression. No new official releases were published during this window. **474 issues remain open/active**, while only 26 were closed — a ratio suggesting the team is absorbing a significant bug influx faster than resolving it. Sixty-five PRs were merged or closed, reflecting steady forward progress despite the load.

---

## 2. Releases

**None.** The project is in a validation cycle for **v2026.8.1-beta.2** (see #125626). The latest closed PRs reference prior releases (2026.7.1-2, 2026.6.10, 2026.5.12), but no new tag was cut during this reporting period.

---

## 3. Project Progress

**Key merged/closed PRs:**

| PR | Summary | Status |
|---|---|---|
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | Require user acknowledgement for install policy warnings (CLI) | ✅ Closed |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | Review install policy warnings in Control UI | ✅ Closed |
| [#125471](https://github.com/openclaw/openclaw/pull/125471) | Keep Claude CLI OAuth available in Control UI after restart | ✅ Closed |
| [#128070](https://github.com/openclaw/openclaw/pull/128070) | Sidebar collapse keeps pointer tooltips quiet | ✅ Closed |
| [#126424](https://github.com/openclaw/openclaw/pull/126424) | Keep conversation delivery within agent bindings (multi-agent safety) | ✅ Closed |
| [#122200](https://github.com/openclaw/openclaw/pull/122200) | Expand truncated assistant messages on Android | ✅ Closed |

**Notable PRs in review (awaiting merge):**

- [#128060](https://github.com/openclaw/openclaw/pull/128060) — Fixes lost subagent completion announces for OpenAI-compatible HTTP sessions
- [#123189](https://github.com/openclaw/openclaw/pull/123189) — Recovers embedded channel runs during chat startup projection
- [#119525](https://github.com/openclaw/openclaw/pull/119525) — Allows retry after memory search timeout (automerge armed)
- [#125900](https://github.com/openclaw/openclaw/pull/125900) — Batches board metadata lookups, coalesces duplicate dashboard reads
- [#126986](https://github.com/openclaw/openclaw/pull/126986) — Preserves agent workspace instructions for native Codex
- [#127881](https://github.com/openclaw/openclaw/pull/127881) — Paints stored conversations while first gateway connect resolves

---

## 4. Community Hot Topics

**Most discussed issues (by comment count):**

1. **[Release validation: v2026.8.1-beta.2](https://github.com/openclaw/openclaw/issues/125626)** — 19 comments. The community is actively stress-testing the beta via a structured worksheet. This is the canonical validation thread for the upcoming release.

2. **[Configurable streaming watchdog timeout](https://github.com/openclaw/openclaw/issues/68596)** — 15 comments, **8 👍**. Extended-reasoning models (Kimi-K2.5, DeepSeek-R1) trigger the 30s streaming watchdog too aggressively. Users need a tunable threshold to avoid silent run resets during long thinking chains.

3. **[WhatsApp image processing wedges main lane](https://github.com/openclaw/openclaw/issues/96834)** — 14 comments. Inbound images on WhatsApp 1:1 block the lane for ~3 minutes before processing begins, causing `active_reply_work/queued_work_without_active_run` strand states.

4. **[Hardcoded working path in production code](https://github.com/openclaw/openclaw/issues/51429)** — 12 comments. A developer's personal path (`/Users/wangtao`) was merged and shipped, causing OpenClaw to create spurious directories. Community alarm over code review hygiene.

5. **[MCP tools not injected into subagent sessions](https://github.com/openclaw/openclaw/issues/85030)** — 12 comments, 6 👍. `mcp.servers` registration is ignored for `sessions_spawn` subagents regardless of allowlist configuration. Affects multi-agent setups heavily.

**Underlying needs:** The community is pushing hard on **multi-agent reliability** (subagent delivery, MCP injection, session recovery), **long-turn robustness** (watchdog timeouts, LLM retry at embedded-assistant stage), and **observability** (missing trace context in plugin hooks).

---

## 5. Bugs & Stability

**Critical / P0 (highest severity):**

| Issue | Summary | Fix PR? |
|---|---|---|
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite corruption recurs on pristine rebuilt DBs within 15–24h (beta.2, WSL2) — includes "paralyzed gateway" mode | ❌ No known fix |
| [#124788](https://github.com/openclaw/openclaw/issues/124788) | beta.2 event loop blocks ~100s every ~10 min (anchored timer; string building + fs scan) | ❌ No known fix |

**High severity (P1, session-state / crash-loop / data-loss):**

| Issue | Summary | Fix PR? |
|---|---|---|
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Leaks unreaped hook/tool child processes → zombie accumulation | Partial: [#115450](https://github.com/openclaw/openclaw/pull/115450) addresses timeout case |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | Subagent completion delivery lost on timeout/drain/orphan prune | [#128060](https://github.com/openclaw/openclaw/pull/128060) (OpenAI-compat HTTP sessions) |
| [#85030](https://github.com/openclaw/openclaw/issues/85030) | MCP tools not injected into subagent sessions | ❌ No fix yet |
| [#124284](https://github.com/openclaw/openclaw/issues/124284) | Subagent spawn fails with vLLM + thinking (malformed XML tool calls in beta.2) | ❌ No fix yet |
| [#45224](https://github.com/openclaw/openclaw/issues/45224) | Unhandled Playwright assertion crashes entire Gateway | ❌ No fix yet |
| [#113701](https://github.com/openclaw/openclaw/issues/113701) | Context overflow: large tool outputs exceed window, compaction can't recover | ❌ No fix yet |
| [#126906](https://github.com/openclaw/openclaw/issues/126906) | Denying write tool silently disables memory persistence | ❌ No fix yet |
| [#99910](https://github.com/openclaw/openclaw/issues/99910) | Memory dreaming run pegs event loop ~10 min | ❌ No fix yet |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) | active-memory blocks replies, QMD boot overloads multi-agent gateways | ❌ No fix yet |

**Notable regressions (marked by authors):**

- [#126821](https://github.com/openclaw/openclaw/issues/126821) — SQLite corruption (regression in beta.2)
- [#124284](https://github.com/openclaw/openclaw/issues/124284) — vLLM subagent XML parsing (regression in beta.2)
- [#89278](https://github.com/openclaw/openclaw/issues/89278) — Codex OAuth refresh timeout in cron/heartbeat
- [#105528](https://github.com/openclaw/openclaw/issues/105528) — exec/read tools return empty on Windows (v2026.6.x regression)
- [#48810](https://github.com/openclaw/openclaw/issues/48810) — Compaction retry creates orphan fork in parentId chain

---

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Community Support |
|---|---|---|
| [#68596](https://github.com/openclaw/openclaw/issues/68596) | Configurable streaming watchdog timeout | **8 👍** — strong signal; extended-reasoning models make this essential |
| [#57425](https://github.com/openclaw/openclaw/issues/57425) | Graceful Gateway Restart with Session Recovery | **1 👍** — longstanding request; no in-flight PR detected |
| [#75947](https://github.com/openclaw/openclaw/issues/75947) | UI quality update based on UX scoring | **2 👍** — cited as hard to navigate, config pages dense |
| [#33102](https://github.com/openclaw/openclaw/issues/33102) | TUI: add config support for --deliver flag default | **1 👍** |
| [#50291](https://github.com/openclaw/openclaw/issues/50291) | Plugin Hooks: missing trace context (messageId, runId, parentSpanId) | **0 👍** but high-value for observability; no PR yet |

**Predicted next-release inclusions:**
- Streaming watchdog timeout configurability (#68596) — high community alignment, directly impacts reasoning-model users
- Memory search retry after timeout (#119525, PR automerge armed) — narrow fix, low risk
- Claude CLI `ask_user` prompt delivery (#117152, PR awaiting author) — completes Claude CLI integration
- SecretRef support in MCP server env/headers (#69417, PR awaiting) — security improvement

---

## 7. User Feedback Summary

**Pain points surfacing this period:**

- **"Someone hardcoded their path and it shipped"** (#51429) — Trust concern around code review rigor; user's machine created a directory named after an unknown `wangtao`.
- **Voice Mode deletes conversations** (#126423) —

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Comparison Report — 2026-08-23

## 1. Ecosystem Overview

The 2026 open-source personal AI assistant landscape is characterized by intense multi-agent hardening, security architecture maturation, and platform-specific reliability gaps. Two projects — OpenClaw and ZeroClaw — dominate in raw activity volume, each processing 500+ and 100+ events respectively in a single day. Mid-tier projects like Hermes Agent and IronClaw show sustained engineering velocity focused on gateway lifecycle and context-cost reduction. A growing number of projects (NanoBot, PicoClaw, Moltis, CoPaw) are in stabilization sprints, while NullClaw and ZeptoClaw show no measurable activity. The ecosystem is clearly transitioning from feature expansion to operational reliability.

## 2. Activity Comparison

| Project | Issues (Open) | PRs (Active/Merged) | Release Status | Health Score |
|---|---|---|---|---|
| **OpenClaw** | 474 | 500 updated / 65 merged-closed | Beta validation (v2026.8.1-beta.2) | 🟡 Moderate — high volume, net-open issue growth |
| **ZeroClaw** | ~100+ (est.) | 100 events / 5 merged-closed | Consolidating toward v0.9.0 | 🟢 Healthy — strong closure momentum |
| **Hermes Agent** | 48 | 50 updated / 2 merged | No release; heavy-fix cycle | 🔴 At Risk — 45+ open corner-patch issues |
| **NanoClaw** | 1 | 26 touched / 8 merged | No release; deployment sprint | 🟢 Healthy — focused, productive |
| **IronClaw** | ~9 | 21 updated / 5 merged | No release | 🟢 Healthy — diverse contributors, clean triage |
| **CoPaw** | ~7 | 4 open / 0 merged | v2.1.0 referenced | 🟡 Moderate — first-time contributor engagement |
| **Moltis** | 0 (1 closed) | 3 under review / 0 merged | No release | 🟡 Moderate — steady but no merges yet |
| **LobsterAI** | 0 (2 stale-closed) | 6 merged-closed (5 stale) | No release | 🔴 Low — stale-closure pattern, low responsiveness |
| **PicoClaw** | 2 | 6 updated / 4 merged | No release | 🟡 Moderate — 2 high-severity open bugs |
| **NanoBot** | 0 | 19 updated / 5 merged | No release | 🟢 Healthy — observability-focused, clean trajectory |
| **NullClaw** | — | — | No activity | 🔴 Inactive |
| **ZeptoClaw** | — | — | No activity | 🔴 Inactive |

*Health Score rationale: based on issue closure rate, PR merge velocity, release cadence, and maintainer responsiveness.*

## 3. OpenClaw's Position

**Advantages vs. peers:**
- Largest community engagement by an order of magnitude (500 events/day vs. next highest at ~100). This translates to broader issue discovery, faster beta validation, and a richer plugin/MCP ecosystem.
- Most advanced multi-agent architecture — subagent delivery, MCP injection, and session recovery are production concerns being actively stress-tested.
- Beta-validation discipline: the structured worksheet approach for v2026.8.1-beta.2 (#125626) signals a mature release process uncommon in smaller projects.

**Technical approach differences:**
- OpenClaw is the only project explicitly debugging SQLite-level data corruption and event-loop anchoring at scale — indicating a heavier stateful workload than competitors.
- Hermes Agent shares the gateway-lifecycle complexity but lacks OpenClaw's multi-agent depth.
- NanoBot and Moltis are more provider-agnostic and integration-focused, avoiding OpenClaw's stateful gateway concerns.

**Community size comparison:**
OpenClaw's 474 open issues and 500+ daily events dwarf all peers. Hermes Agent (~48 open issues) is the next largest by ~10×. NanoClaw (1 open issue) and NanoBot (0) operate at a fraction of OpenClaw's scale, suggesting OpenClaw serves a significantly larger or more active user base.

## 4. Shared Technical Focus Areas

| Theme | Projects Involved | Specific Needs |
|---|---|---|
| **Multi-agent reliability** | OpenClaw, Hermes Agent, ZeroClaw | Subagent session recovery, MCP tool injection across agent boundaries, delivery guarantees |
| **Gateway/session lifecycle** | Hermes Agent, ZeroClaw, OpenClaw | Gateway-owned control surfaces (not process-scanning), WebSocket transport resilience, credential rotation |
| **Token/context cost reduction** | IronClaw, OpenClaw | Context compression (Pi-style barriers), overflow recovery, compaction retry |
| **MCP server resilience** | OpenClaw, PicoClaw, Hermes Agent, Moltis | Circuit-breaker decoupling from tool errors, stale client reuse after restart, graceful degradation on connection failure |
| **Provider contract standardization** | NanoBot, Moltis, ZeroClaw | Typed `LLMUsage` contracts, provider-neutral telemetry, schema compliance (OpenAI strict mode) |
| **Windows platform coverage** | Hermes Agent, ZeroClaw, CoPaw | Platform-specific regressions (path handling, session folders, UTF-8, Docker sandbox) |
| **Security policy correctness** | ZeroClaw, Moltis, IronClaw | Fail-closed hook policies, sandbox egress auth, high-risk command allowlists actually honored |
| **Observability & telemetry** | NanoBot, OpenClaw, CoPaw | Unified trajectory backends, trace context in plugin hooks, cost dashboards, hidden reasoning shells |
| **Config onboarding robustness** | ZeroClaw, Hermes Agent, OpenClaw | Config writes that don't destroy comments, template sections that pass strict loaders, transactional config writes |

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | IronClaw | ZeroClaw | NanoBot | PicoClaw | Moltis | CoPaw | NanoClaw |
|---|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Multi-agent orchestration | Gateway + fleet management | Context efficiency + sandboxing | Security boundaries + SOP | Provider telemetry + UX | Embedded/MCP edge cases | Security hook policy | Chrome bridge + cron | Containerized multi-instance |
| **Target user** | Power users, multi-agent builders | Enterprise fleet operators | Cost-conscious scaling teams | Security-first deployments | Provider-agnostic users | Edge/embedded deployers | Security/research | Multi-machine setups | DevOps/CI deployments |
| **Architecture** | Stateful gateway + SQLite | Process-scan gateway (needs rewrite) | Hook-based lifecycle + evidence-backed runs | WASM plugin runtime + gateway auth | Provider-neutral SDK | MCP-centric agent loop | Policy-as-code hooks | TUI-first + LAN Chrome bridge | Instance-scoped circuit breakers |
| **Release cadence** | Beta validation (high frequency) | No release; fix-heavy | No release; feature sprints | v0.9.0 in progress | No release; refinement | Bug-fix focused | Policy-design focused | v2.1.0 era | Deployment sprint |
| **Key differentiator** | Scale + multi-agent depth | Fleet update reliability (unsolved) | Token-cost measurement + compaction | RFC-driven architecture | Typed usage contracts | MCP hang resilience | Fail-closed security hooks | First-time contributor friendly | Containerized deployment hardening |

## 6. Community Momentum & Maturity

**Tier 1 — High Velocity, Active Development:**
- **OpenClaw** (500 events/day) and **ZeroClaw** (100 events/day) are in heavy iteration. Both are approaching major release boundaries (beta validation / v0.9.0) with structured RFC and PR pipelines.
- **Hermes Agent** (50 events/day) shows momentum but it is predominantly open work — a fix-heavy cycle without release closure signals either complexity or capacity constraints.

**Tier 2 — Moderate, Sustained Progress:**
- **IronClaw** (30 events/day) and **NanoClaw** (26 PRs touched) demonstrate healthy contributor diversity and focused sprint output. Both are advancing architectural features with clean triage.
- **NanoBot** (19 PRs, 5 merged, 0 open issues) is in a mature refinement phase — low issue count indicates a stable core with targeted observability improvements.

**Tier 3 — Stabilizing, Low-Volume:**
- **CoPaw** (7 issues, 4 PRs) and **Moltis** (3 PRs under review) are in bug-fix and integration-hardening cycles. CoPaw shows strong first-time contributor engagement, which is a healthy longevity signal.
- **PicoClaw** (6 PRs, 4 merged) is small but productive; the 2 high-severity open bugs (MCP hang, animation loop) are concentrated risks.

**Tier 4 — Stalled or Inactive:**
- **LobsterAI** shows stale-closure patterns (7/8 closed items auto-closed), suggesting maintainer bandwidth is insufficient for active triage.
- **NullClaw** and **ZeptoClaw** show zero activity — effectively dormant.

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Multi-agent reliability is the frontier** | OpenClaw (subagent delivery, MCP injection), Hermes Agent (fleet updates), ZeroClaw (SOP runs) all surface this as P1 | Building robust inter-agent communication, session recovery, and tool-discovery across agent boundaries should be a priority investment |
| **Gateway lifecycle is unsolved at scale** | Hermes Agent (#92091 gateway control socket), OpenClaw (process-scan fragility), ZeroClaw (auth gateway boundaries) | The industry lacks a canonical gateway abstraction; projects that solve owned gateway contracts will gain a structural advantage |
| **Context cost measurement is becoming standard** | IronClaw (Pi-style compaction, 4× token regression on PinchBench), OpenClaw (compaction retry) | Telemetry around context window utilization and compaction efficiency will become a key differentiator — early invest here |
| **Security hooks are moving to fail-closed** | Moltis (#1230), ZeroClaw (SOP auth, egress grants) | The default for security-critical hooks is shifting from "fail-open" to "fail-closed" — designs should assume auditability and explicit policy |
| **MCP error semantics need rethinking** | Hermes Agent (circuit breaker fixes), PicoClaw (MCP hang), Moltis (stale client after restart) | Tool-level errors must be decoupled from transport-level circuit breakers; this is a cross-cutting reliability gap |
| **Windows coverage is a trust gap** | Hermes Agent (6+ regressions), ZeroClaw (74 CI failures), CoPaw (UTF-8), OpenClaw (WSL2 SQLite) | Projects that invest in cross-platform CI and Windows-native testing will earn disproportionate trust from enterprise users |
| **Config onboarding fragility persists** | ZeroClaw (#9436 template sections), Hermes Agent (#92554 comment stripping), OpenClaw (hardcoded paths) | Transactional config writes and schema strictness are low-cost, high-impact reliability improvements |
| **RFC-driven architecture is emerging** | ZeroClaw (5+ RFCs in flight), Moltis (fail-closed policy via RFC), IronClaw (AfterTurn hooks via RFC) | Projects adopting formal RFC processes show better architectural coherence and community alignment — a signal of maturity |

**Bottom line for developers:** The ecosystem is consolidating around three axes — multi-agent reliability, security-policy correctness, and cost-aware context management. Projects that treat these as first-class concerns rather than afterthoughts will capture the most engaged user base in 2026–2027.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-23

## 1. Today's Overview
NanoBot is in a high-velocity refinement phase, with 19 pull requests updated in the last 24 hours and 5 successfully merged/closed, while issue traffic remains at zero and no new releases were published. Development is tightly focused on web UI turn observability, provider contract standardization, and runtime state correctness. The project appears healthy and operationally active, prioritizing telemetry accuracy and edge-case hardening over major feature launches.

## 2. Releases
No new releases were published today.

## 3. Project Progress
**Merged/Closed Today (5):**
- [#4430](https://github.com/HKUDS/nanobot/pull/4430) — Configurable `web_fetch` provider (`auto`, `tavily`, `jina`, `readability`)
- [#3869](https://github.com/HKUDS/nanobot/pull/3869) — DeepSeek message hardening (null/empty content sanitization, prevents 400s and placeholder leakage)
- [#3294](https://github.com/HKUDS/nanobot/pull/3294) — Optional Dream kill switch + custom Phase 1/2 template paths
- [#5488](https://github.com/HKUDS/nanobot/pull/5488) — Docs refresh: maintainer attribution and responsive community contributor wall
- [#5486](https://github.com/HKUDS/nanobot/pull/5486) — Unified turn observability (single answer surface, collapsible live activity)

**Key Open Advances (14):**
- [#5480](https://github.com/HKUDS/nanobot/pull/5480) & [#5481](https://github.com/HKUDS/nanobot/pull/5481) — Typed `LLMUsage` contract and unified trajectory backend for provider-neutral telemetry
- [#5489](https://github.com/HKUDS/nanobot/pull/5489) — Email IMAP performance: headers fetched before body, UID SEARCH avoids redundant fetches
- [#5408](https://github.com/HKUDS/nanobot/pull/5408) — Chat-scoped follow-up suggestions
- [#5367](https://github.com/HKUDS/nanobot/pull/5367) — Full WebUI localization across 10 supported locales
- [#5420](https://github.com/HKUDS/nanobot/pull/5420) — User-controlled turn recovery with explicit Continue/Dismiss controls
- [#5471](https://github.com/HKUDS/nanobot/pull/5471) — Ephemeral SDK runs now correctly leave session state untouched

## 4. Community Hot Topics
*(Note: Comment and reaction counts are currently `undefined` across listed items. Activity is measured by PR update volume and label density.)*

Focus clusters around **observability**, **provider reliability**, and **session durability**:
- [#5491](https://github.com/HKUDS/nanobot/pull/5491) & [#5490](https://github.com/HKUDS/nanobot/pull/5490) — WebUI answer rendering and aggregate token usage clarity
- [#5480](https://github.com/HKUDS/nanobot/pull/5480) & [#5481](https://github.com/HKUDS/nanobot/pull/5481) — Standardized provider usage contracts and trajectory deltas
- [#5484](https://github.com/HKUDS/nanobot/pull/5484) — MCP business-error envelope detection

These reflect a strong underlying demand for transparent cost tracking, accurate provider integration, and robust tool-calling error handling.

## 5. Bugs & Stability
**High Severity:**
- [#5483](https://github.com/HKUDS/nanobot/pull/5483) — Delayed cross-session messages can recreate deleted sessions; fix enforces session existence checks before persistence
- [#5471](https://github.com/HKUDS/nanobot/pull/5471) — `ephemeral=True` SDK runs were mutating session state; fix restores documented isolation semantics

**Medium Severity:**
- [#5485](https://github.com/HKUDS/nanobot/pull/5485) — LangSmith tracing lost during LiteLLM-to-native SDK migration; restores OpenAI/Anthropic wrapper callbacks
- [#5484](https://github.com/HKUDS/nanobot/pull/5484) — MCP servers returning business errors with `isError=false` are treated as successes; fix flags invalid envelopes

**Low/UI Severity:**
- [#5491](https://github.com/HKUDS/nanobot/pull/5491) — Answer text incorrectly hidden inside reasoning shells across tool turns
- [#5469](https://github.com/HKUDS/nanobot/pull/5469) — TUI footer shows cumulative turn tokens instead of the latest provider-reported request context

## 6. Feature Requests & Roadmap Signals
- [#5408](https://github.com/HKUDS/nanobot/pull/5408) — Ephemeral, provider-neutral follow-up suggestions
- [#5487](https://github.com/HKUDS/nanobot/pull/5487) — File preview panel with markdown rendering, system open, and subagent lifecycle replay
- [#5367](https://github.com/HKUDS/nanobot/pull/5367) — Runtime localization of agent activity labels
- [#5420](https://github.com/HKUDS/nanobot/pull/5420) — Manual turn recovery checkpoints
- Native provider stack (#5482) with typed usage contracts and trajectory deltas

**Predicted Next-Release Focus:** Unified telemetry dash

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-23

## 1. Today's Overview

Hermes Agent shows high activity with 50 issues and 50 PRs updated in the last 24 hours, though momentum is predominantly sustained by open work (48 open issues, 46 open PRs). Only 2 PRs were merged/closed and no new releases were published, indicating the project is in a heavy-fix cycle without a published release boundary. The dominant themes are Windows platform instability, install/update reliability, and gateway connectivity fragility — three areas that share a common root: the gateway lacks a formal control surface and discovers/manages itself via process scanning.

## 2. Releases

No new releases published today.

## 3. Project Progress

**Merged/Closed PRs today:**

- **#79645** [CLOSED] — `fix(mcp): keep tool errors out of server breaker` — Separates tool-level validation/business errors from the MCP transport circuit breaker, preventing invalid arguments or missing resources from blocking neighboring valid tools on an otherwise healthy server.
- **#79298** [CLOSED] — `fix(mcp): separate tool errors from transport breaker` — Companion fix; a completed `tools/call` RPC now closes the server transport breaker even when `isError=true`, while missing sessions and transport exceptions still trip it.

Both PRs address the same class of MCP reliability bug and were closed today, suggesting coordinated resolution of a shared issue.

## 4. Community Hot Topics

| Issue | Title | Comments | Link |
|-------|-------|----------|------|
| #66616 | Skills index is stale or degraded (degraded) | 78 | [Issue](https://github.com/NousResearch/hermes-agent/issues/66616) |
| #84834 | Webhook Feature Package — graph-gated repair (meta-issue) | 22 | [Issue](https://github.com/NousResearch/hermes-agent/issues/84834) |
| #91277 | [Tracking] Fleet update reliability | 14 | [Issue](https://github.com/NousResearch/hermes-agent/issues/91277) |

**Underlying needs:**

- **#66616** (78 comments): The skills-index watchdog has been firing for weeks; users need reliable auto-rebuild of the `/docs/api/skills-index.json` and trust that the deployed index reflects the latest skill definitions.
- **#84834** (22 comments): The webhook surface is fragmented across ingress, execution, delivery, configuration, management UI, deployment, and docs. Users want a single coherent feature package rather than ad-hoc fixes.
- **#91277** (14 comments): Fleet update reliability is the project's "least reliable capability" per the maintainer. ~30 open issues and ~15 open PRs each patch a different corner of the same problem class — users are requesting a unified deployment plan rather than piecemeal fixes.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **P1** | [#78981](https://github.com/NousResearch/hermes-agent/issues/78981) | Session permanently dies after repeated context-compression hangs on DeepSeek 500k-token sessions; stalled stream waits 600s ceiling, interrupted turn never recovers | No |
| **P1** | [#91277](https://github.com/NousResearch/hermes-agent/issues/91277) | Fleet update reliability — imperative per-platform spaghetti with no unified plan | In progress (meta-tracker) |
| **P2** | [#92095](https://github.com/NousResearch/hermes-agent/issues/92095) | `hermes desktop` writes broken `.desktop` Exec= on uv-based installs; points at bare uv interpreter instead of venv python | **#92090** open |
| **P2** | [#58593](https://github.com/NousResearch/hermes-agent/issues/58593) | Linux Desktop in-app update repeatedly fails to stick and resets Electron sandbox permissions | No |
| **P2** | [#83832](https://github.com/NousResearch/hermes-agent/issues/83832) | PKCE state cookie serialized with literal `;` breaks OIDC login (RFC 6265 violation) | No |
| **P2** | [#92302](https://github.com/NousResearch/hermes-agent/issues/92302) | 120s timeout on local model connections with large context — `HERMES_STREAM_STALE_TIMEOUT` no longer effective | No |
| **P2** | [#92271](https://github.com/NousResearch/hermes-agent/issues/92271) | Windows Docker sandbox broken — session folder name contains `:` (WinError 267) | No |
| **P2** | [#92553](https://github.com/NousResearch/hermes-agent/issues/92553) | `pre_tool_call` shell hooks silently discard the documented `approve` action | No |
| **P2** | [#92606](https://github.com/NousResearch/hermes-agent/issues/92606) | Anthropic OAuth: stale credential file overwrites rotated token; two pool rows share one single-use refresh token → 401 revoked → empty pool | No |
| **P2** | [#92506](https://github.com/NousResearch/hermes-agent/issues/92506) | `profiles.list` JSON-RPC never answers — `WSTransport.write` silently kills pool worker on unserializable payload (datetime in `profile.yaml` `ui_meta`) | No |
| **P2** | [#92565](https://github.com/NousResearch/hermes-agent/issues/92565) | MCP server whose credentials change is never reconnected — sessions reused by name alone | No |
| **P3** | [#92095](https://github.com/NousResearch/hermes-agent/issues/92095) | See above | **#92090** open |
| **P3** | [#92607](https://github.com/NousResearch/hermes-agent/issues/92607) | Wispr Flow cannot insert text into Hermes Desktop composer on Windows | No |
| **P3** | [#92608](https://github.com/NousResearch/hermes-agent/issues/92608) | Hindsight `local_embedded` daemon fails to boot under multiplexing — `UnscopedSecretError` on background threads | No |
| **P3** | [#84599](https://github.com/NousResearch/hermes-agent/issues/84599) | SSH backend silently falls back to local after idle-environment cleanup in desktop-remote sessions on non-default profiles | No |
| **Closed** | [#40391](https://github.com/NousResearch/hermes-agent/issues/40391) | Hermes Desktop Remote Gateway — connects to REST but fails WebSocket / flaps back to local | Closed |

**Notable trend:** Windows compatibility regressions are recurring (#92271, #92095, #92607) and no dedicated Windows sweeper is actively closing them. The MCP credential-reuse bug (#92565) and the approval timeout bug (#91980 / #55506) point to deeper lifecycle-management issues in the gateway.

## 6. Feature Requests & Roadmap Signals

| Issue | Title | Comments | Link |
|-------|-------|----------|------|
| #74816 | Multi-device session sync — real-time shared sessions across all interfaces | 3 👍 | [Issue](https://github.com/NousResearch/hermes-agent/issues/74816) |
| #92091 | [Design] Gateway control socket: replace process-scan heuristics with a gateway-owned contract | 5 | [Issue](https://github.com/NousResearch/hermes-agent/issues/92091) |
| #92568 | Azure Foundry: native cross-process token admission, retry, and privacy-safe rate-limit receipts | 1 | [Issue](https://github.com/NousResearch/hermes-agent/issues/92568) |
| #92385 | Desktop: give a renamed default profile its own mark in the profile rail | 0 | [PR](https://github.com/NousResearch/hermes-agent/pull/92385) |
| #92449 | Profiles: restrict file tools to configured paths | 0 | [PR](https://github.com/NousResearch/hermes-agent/pull/92449) |

**Predictions for next release:**
- **#92091** (gateway control socket) is the highest-leverage design ask and directly addresses the root cause flagged in #91277 and #92095. If adopted, it would unblock fleet-update reliability.
- **#92449** (profile-local filesystem boundaries) is a security hardening feature with a closed PR already in review — likely to ship.
- **#74816** (multi-device session sync) is a long-term vision item; unlikely for the next patch but the "like WeChat" framing suggests active community demand.
- **#92385** (profile rail icon for renamed default) is a small UX polish already in PR — probable inclusion.

## 7. User Feedback Summary

**Pain points:**
- **Install/update is broken on multiple platforms.** Linux in-app updates don't stick (#58593), Windows uv-based installs write invalid `.desktop` entries (#92095 → fix #92090), and Docker session folders contain colons on Windows (#92271). These are repeat complaints signaling a systemic lack of install-platform coverage.
- **Gateway lifecycle is opaque and fragile.** Approvals sent over dead WebSocket transports time out silently (#91980), SSH backends silently revert to local (#84599), and the gateway has no owned control surface (#92091). Users report confusion and data loss when sessions unexpectedly revert or stall.
- **MCP servers are hard to trust.** Tool errors trip the circuit breaker (#79645/#79298 — now fixed), but credential changes don't trigger reconnection (#92565), and sessions are reused by name alone.
- **Configuration erases user intent.** `hermes config set` and plugin enable commands strip all comments from `config.yaml` (#92554), frustrating power users who rely on inline documentation.
- **Windows is the weakest platform.** Six+ distinct Windows regressions reported this week with few fixes landed.

**Satisfaction signals:**
- The MCP circuit-breaker fixes (#79645, #79298) address a real reliability gap and were resolved quickly.
- The GitHub Actions-based skills-index watchdog (#66616) shows CI hygiene is improving, even if the index itself is occasionally stale.
- Security-focused PRs (RetainDB URL rejection #70354, BlueBubbles redirect hardening #70341, OAuth XSS escape #6723) demonstrate active security maintenance.

## 8. Backlog Watch

| Issue/PR | Age | Concern |
|----------|-----|---------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale | ~36 days | 78 comments, no closure; cron rebuild may be misconfigured or deployment step is failing silently |
| [#91277](https://github.com/NousResearch/hermes-agent/issues/91277) — Fleet update reliability | 2 days | Maintainer-acknowledged as "least reliable capability"; 45+ open corner-patch issues remain |
| [#92091](https://github.com/NousResearch/hermes-agent/issues/92091) — Gateway control socket design | 1 day | Root-cause design for #91277; needs architecture decision before implementation |
| [#78981](https://github.com/NousResearch/hermes-agent/issues/78981) — DeepSeek 500k session death | ~18 days | P1; context-compression stall leaves sessions unrecoverable |
| [#83832](https://github.com/NousResearch/hermes-agent/issues/83832) — PKCE cookie semicolon | ~12 days | P2 auth breakage; RFC 6265 violation affecting all OIDC logins |
| [#92554](https://github.com/NousResearch/hermes-agent/issues/92554) — Config comments destroyed | 1 day | P2 UX regression; `config set` and plugin enable both strip comments |
| [#92506](https://github.com/NousResearch/hermes-agent/issues/92506) — `profiles.list` JSON-RPC hangs | 1 day | P2; unserializable `datetime` in `ui_meta` silently kills pool worker |
| [#92606](https://github.com/NousResearch/hermes-agent/issues/92606) — Anthropic OAuth token pool corruption | <1 day | P2; stale refresh-token reuse causes mutual revocation and empty credential pool |

**Recommendation:** The gateway control socket design (#92091) should be prioritized as a prerequisite for fleet-update reliability (#91277). Without a gateway-owned control surface, every install/update/connector bug will continue to be patched at arm's length via process scanning heuristics.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-23

## 1. Today's Overview

PicoClaw remains actively maintained with moderate daily engagement: 2 open issues and 6 pull requests updated in the past 24 hours, with 4 PRs merged/closed. No new release was published today. The most notable activity centers on a critical agent-loop hang bug (#3269) triggered by MCP server connection failures, and a corresponding fix PR (#3337) that remains open and stale. Overall project health is stable, though the two high-impact open bugs suggest areas needing timely maintainer attention.

## 2. Releases

No new releases today.

## 3. Project Progress

**4 Pull Requests merged/closed today:**

- **[PR #3319](https://github.com/sipeed/picoclaw/pull/3319)** — *fix(tools): honor exec timeout and boolean run options* — Corrected the `exec` tool to respect per-run `timeout` arguments instead of silently using the global timeout, and fixed misdeclared boolean options (`background`, `pty`) being typed as strings. This is a correctness fix improving tool reliability.
- **[PR #714](https://github.com/sipeed/picoclaw/pull/714)** — *skills: install/reinstall CLI and refactor into skillsCmd* — Added `ParseInstallSpec`, `InstallFromGitHubEx`, and a `reinstall` subcommand; production installs now use the GitHub Trees API. This expands skill management capabilities.
- **[PR #1083](https://github.com/sipeed/picoclaw/pull/1083)** — *fix(cron): preserve recurring job schedule after execution* — Fixed a bug where recurring cron jobs (`every_seconds` / `cron_expr`) silently became one-time tasks after a single execution. Addresses root cause in `executeJobByID` when `computeNextRun()` returned `nil`.
- **[PR #1545](https://github.com/sipeed/picoclaw/pull/1545)** — *merge PR #1500 #1490 #1488 #1487 #1485* — Batch merge of prior fixes.

## 4. Community Hot Topics

- **[Issue #3269](https://github.com/sipeed/picoclaw/issues/3269)** — *MCP server connection failure hangs agent loop* — 6 comments, 1 👍. The agent loop stalls entirely when an MCP server is unreachable, freezing the chat interface. **Underlying need:** Users require resilient agent architectures that degrade gracefully rather than hard-lock on external service failures. This is a high-impact UX issue.
- **[Issue #3343](https://github.com/sipeed/picoclaw/issues/3343)** — *Tool feedback animation edits Telegram message indefinitely after failed turn* — Created today, 0 comments. The animation loop ran for days, producing 228,000+ `editMessageText` calls and triggering a Telegram rate limit. **Underlying need:** Robust lifecycle management for async tool feedback animations, especially on messaging platforms with strict rate limits.

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|----------|------|-------------|------------|
| 🔴 **High** | [Issue #3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP server failure hangs agent loop; chat interface stops responding entirely | [PR #3337](https://github.com/sipeed/picoclaw/pull/3337) open but stale |
| 🔴 **High** | [Issue #3343](https://github.com/sipeed/picoclaw/issues/3343) | Tool feedback animation loops indefinitely, exhausting Telegram API rate limits | No fix PR yet |
| 🟡 **Medium** | [PR #3319](https://github.com/sipeed/picoclaw/pull/3319) *(merged)* | `exec` tool ignored per-run timeout; boolean options mis-typed as strings | ✅ Fixed |
| 🟡 **Medium** | [PR #1083](https://github.com/sipeed/picoclaw/pull/1083) *(merged)* | Recurring cron jobs became one-time after first execution | ✅ Fixed |

## 6. Feature Requests & Roadmap Signals

- **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222)** — *refactor(deltachat): cleanup implementation, documentation (-200 LOC)* — Drops legacy features, removes password-based email config, renames `invite_link` → `join_invite_link`, and adds a full Deltachat section to docs. Still open/stale. Suggests the team is prioritizing codebase hygiene and modernizing channel integrations.
- **[PR #714](https://github.com/sipeed/picoclaw/pull/714)** *(just merged)* — Skill install/reinstall CLI with GitHub Trees API support signals ongoing investment in the skill ecosystem, likely to see further expansion in upcoming releases.

## 7. User Feedback Summary

- **Pain point — MCP fragility:** Users report that a single unreachable MCP server completely freezes the chat experience (#3269). This is a significant UX regression for production deployments relying on MCP tools.
- **Pain point — Animation lifecycle bugs:** The Telegram editMessageText runaway (#3343) indicates a lack of cancellation hooks in the tool feedback animation system, causing real API quota exhaustion.
- **Satisfaction — Cron reliability:** The fix for recurring cron jobs (#1083) addresses a silent data-loss bug that likely affected power users depending on scheduled automation.
- **Satisfaction — Tool precision:** The `exec` timeout fix (#3319) resolves a mismatch between advertised and actual behavior, improving trust in tool contracts.

## 8. Backlog Watch

| Item | Type | Age | Risk |
|------|------|-----|------|
| [PR #3337](https://github.com/sipeed/picoclaw/pull/3337) — Fix MCP hang | Bug fix | Created 2026-08-14 (9 days) | 🔴 High — directly blocks the critical issue #3269 |
| [Issue #3269](https://github.com/sipeed/picoclaw/issues/3269) — MCP agent loop hang | Bug | Created 2026-07-20 (34 days) | 🔴 High — stale tag applied, no merge |
| [Issue #3343](https://github.com/sipeed/picoclaw/issues/3343) — Animation infinite loop | Bug | Created 2026-08-22 (1 day) | 🔴 High — no fix PR, active impact |
| [PR #3222](https://github.com/sipeed/picoclaw/pull/3222) — Deltachat refactor | Enhancement | Created 2026-07-03 (51 days) | 🟡 Medium — stale, but lower urgency |

**Recommendation:** PR #3337 should be prioritized for review and merge given its direct resolution of the most disruptive open bug. Issue #3343 needs a fix PR before the next release cycle to prevent further Telegram API incidents.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-23

## 1. Today's Overview
NanoClaw is in an active development sprint as of 2026-08-23, with **26 PRs touched** in the last 24 hours (18 open, 8 merged/closed) and **1 active issue**. No new releases were published today. Activity is heavily weighted toward deployment hardening, multi-instance isolation, and expanding channel onboarding flows for Telegram and Slack. The project shows strong contributor velocity, though several open fixes indicate ongoing attention to containerized builds, Node.js compatibility, and adapter lifecycle bugs.

## 2. Releases
No new releases were published in the reporting window.

## 3. Project Progress
Eight PRs were merged or closed today, primarily targeting core provisioning reliability and build tooling:
- **#3394** merged a functional fallback for Slack manual-install flows when app-approval policies block managed installs.
- **#3390** closed a duplicate-provisioning bug that occurred when resuming Slack setup after a bot was already created.
- **#3443** streamlined native dependency builds by removing `better-sqlite3` from `onlyBuiltDependencies`, allowing pnpm to consume bundled prebuilds directly.
- A coordinated Telegram suite (#3431, #3434, #3435, #3437, #3438) refined the pairing wizard, fixed polling-adapters incorrectly starting webhook servers, and carried adapter instance state through initialization flows.
- **#3355** and **#3356** advanced a new Cursor Agent SDK integration and its corresponding setup skill.

## 4. Community Hot Topics
Quantitative comment/reaction metrics are not available in the snapshot; ranking is based on topical concentration, recency, and infrastructural impact:
- **[PR #3318](https://github.com/nanocoai/nanoclaw/pull/3318)** – Force baseline (non-AVX2) Bun binary in agent images
- **[PR #3447](https://github.com/nanocoai/nanoclaw/pull/3447)** – Scope circuit-breaker crash strikes to the instance that earned them
- **[Issue #3453](https://github.com/nanocoai/nanoclaw/issues/3453)** – Node 25+ tsx loader deprecation polluting stderr and breaking tests
- **[PR #3438](https://github.com/nanocoai/nanoclaw/pull/3438)** & **[PR #3435](https://github.com/nanocoai/nanoclaw/pull/3435)** – “Add another Telegram bot” wizard and instance-aware pairing

**Analysis:** The community is prioritizing predictable containerized deployments and per-instance fault tolerance. Multi-bot onboarding (Telegram, Slack) and cross-platform build compatibility remain high-interest topics, reflecting a user base running NanoClaw in distributed or ephemeral infrastructure.

## 5. Bugs & Stability
Ranked by severity:
1. **High – [#3447](https://github.com/nanocoai/nanoclaw/pull/3447):** Circuit-breaker crash counters are not instance-scoped, causing shared `data/circuit-breaker.json` mounts to falsely delay restarts across deployments. *Fix PR open.*
2. **Medium – [#3453](https://github.com/nanocoai/nanoclaw/issues/3453):** Node.js 25+ `module.register()` deprecation from `tsx` leaks onto stderr, breaking `stdin-json` test assertions. *No fix PR yet.*
3. **Medium – [#3434](https://github.com/nanocoai/nanoclaw/pull/3434):** Polling adapters incorrectly attempt to start a webhook server during initialization. *Fix PR open.*
4. **Low – [#3394](https://github.com/nanocoai/nanoclaw/pull/3394) & [#3390](https://github.com/nanocoai/nanoclaw/pull/3390):** Slack provisioning edge cases. *Already closed/merged.*

## 6. Feature Requests & Roadmap Signals
- **[PR #3355](https://github.com/nanocoai/nanoclaw/pull/3355) / [#3356](https://github.com/nanocoai/nanoclaw/pull/3356):** Cursor Agent SDK payload and setup skill
- **[PR #3438](https://github.com/nanocoai

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-23

---

## 1. Today's Overview

IronClaw showed strong development velocity on 2026-08-23, with **9 issues** and **21 pull requests** updated in the last 24 hours. Four issues were closed and five PRs merged, indicating healthy triage throughput. Core engineering work is advancing across three major fronts: context-cost reduction (Pi-style compaction), sandbox credential mediation, and CI pipeline stabilization. No new releases were published this cycle. The project maintains an active, contributor-diverse cadence with both core and new contributors engaged.

---

## 2. Releases

**No new releases published.**

---

## 3. Project Progress

### Merged / Closed Today

| Item | Description |
|------|-------------|
| [#7768 → PR #7773](https://github.com/nearai/ironclaw/pull/7773) | Removed unused Settings and Extensions tabs and duplicate route metadata — code cleanup in the WebUI. |
| [#7767 → PR #7774](https://github.com/nearai/ironclaw/pull/7774) | Made Automation presenter date tests timezone-robust, fixing failures in non-UTC environments (e.g., `Asia/Shanghai`). |
| [#7769 → PR #7772](https://github.com/nearai/ironclaw/pull/7772) | Surfaced extension setup phase and blockers in Configure, so modal now correctly reports configuration requirements. |
| [#7691 → PR #7700](https://github.com/nearai/ironclaw/pull/7700) | Published run outcome notifications and hardened notification lifecycle — background run completions and failures now surface authoritatively from Process Journal transitions. |

### Actively Advanced Features

- **Context compression (#7824):** Measured token-cost regression from full-thread replay identified on PinchBench (227.7M vs 55.1M tokens). A Pi-style compaction barrier with structured summaries and overflow recovery is in design.
- **AfterTurn lifecycle hook (#7765):** Phase 1 of #7770 introduces the first act-capable lifecycle point in `ironclaw_hooks`, enabling memory curation as its first consumer.
- **GitHub CLI sandbox mediation (#7810):** GitHub credentials now flow through generic credential bindings via `iron-proxy`, retiring the GitHub-specific carve-out.
- **Background subagents (#7818):** Slices 2b+2c of R2 background subagent mode landed, adding receipt spawns, per-child delivery, activation, and healing sweeps.
- **CI expedite lanes (#7821, #7817, #7819, #7820, #7809):** Four parallel tracks are converging on a canonical preflight gate, nextest pipeline, PR/queue check convergence, and a single setup-rust composite — targeting elimination of "green locally, red in CI" drift.
- **OOBE suggestion drawer (#7816):** Refresh and connect entries added to the onboarding suggestion flow, completing the frontend half of #7815.

---

## 4. Community Hot Topics

| Issue / PR | Engagement | Topic |
|------------|-----------|-------|
| [#7824](https://github.com/nearai/ironclaw/issues/7824) — Context projection: Pi-style compaction | 2 comments | Token-cost explosion from replaying full thread history; benchmarks show 4× inflation. |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) — Operator surface for IronHub agent link | New contributor | WebUI missing a way to complete agent link without CLI — raised by a new contributor. |
| [#7815](https://github.com/nearai/ironclaw/issues/7815) — Onboarding suggestions: connect → suggest → thread flow | Epic / UX | Cumulative net-new work to close the end-to-end OOBE suggestion loop. |
| [#7810](https://github.com/nearai/ironclaw/pull/7810) — Sandbox egress auth via generic credential bindings | Core contributor | Retiring GitHub-specific credential carve-outs in favor of provider-neutral patterns. |
| [#7691 → #7700](https://github.com/nearai/ironclaw/issues/7691) — Run outcome notifications | 0 comments, merged | Notification lifecycle hardening for background runs. |

**Analysis:** The dominant concern is **cost efficiency** — full-thread replay is burning tokens at scale, and the community is tracking the compaction work closely. The second theme is **onboarding completeness**, with the OOBE suggestion flow reaching a milestone. Sandbox credential mediation reflects an architectural shift toward provider-neutral abstractions.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| 🟡 Medium | [#7823](https://github.com/nearai/ironclaw/issues/7823) | Notion integration fails to install in IronClaw | Open — no PR yet |
| 🟡 Medium | [#7822](https://github.com/nearai/ironclaw/issues/7822) | Slack setup fails for a user | Open — no PR yet, possibly related to #7823 |
| 🟢 Low | [#7767] (now closed) | Automation presenter date tests failed in non-UTC timezones | ✅ Fixed in PR #7774 |
| 🟢 Low | [#7768] (now closed) | Duplicate Settings/Extensions tab components and route metadata | ✅ Fixed in PR #7773 |
| 🟢 Low | [#7769] (now closed) | Configure modal discarded non-authentication extension blockers | ✅ Fixed in PR #7772 |

**Note:** The two product-feedback issues (#7822, #7823) appear to be integration-install blockers for third-party tools (Notion, Slack). Neither has an assigned fix PR yet, and they are likely related given the same reporter and date.

---

## 6. Feature Requests & Roadmap Signals

| Item | Signal |
|------|--------|
| [#7824](https://github.com/nearai/ironclaw/issues/7824) — Pi-style context compaction | High-priority cost-reduction feature; directly addresses measured benchmark regression. Likely to ship as a core optimization in an upcoming release. |
| [#7825](https://github.com/nearai/ironclaw/issues/7825) — Sandbox egress auth with native `iron-proxy` recipes | Architectural roadmap item: retiring GitHub-specific credential paths in favor of generic broker patterns. |
| [#7765](https://github.com/nearai/ironclaw/pull/7765) — AfterTurn lifecycle hook | New extensibility surface; memory curation is the first consumer. Enables future hook-based features. |
| [#7818](https://github.com/nearai/ironclaw/pull/7818) — Background subagent mode (slices 2b+2c) | R2 feature progressing in stacked slices; producer half now active. |
| [#7650](https://github.com/nearai/ironclaw/pull/7650) — Evidence-backed run outcomes | Shift from semantic judging to deterministic runtime evidence for automation assessment. |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) — IronHub agent link in WebUI | Operator-experience gap being closed; new contributor PR indicates demand for CLI-less setup. |

**Prediction:** The next release will likely highlight **context compaction** (#7824), **AfterTurn hooks** (#7765), and **background subagent mode** (#7818) as headline features, with CI hardening as a behind-the-scenes improvement.

---

## 7. User Feedback Summary

| Source | Pain Point | Sentiment |
|--------|-----------|-----------|
| [#7823](https://github.com/nearai/ironclaw/issues/7823) (Slack) | Notion tool refuses to install | ❌ Frustrated — integration installer is a friction point |
| [#7822](https://github.com/nearai/ironclaw/issues/7822) (Slack) | Slack setup fails | ❌ Frustrated — same reporter, possibly same root cause as #7823 |
| [#7815](https://github.com/nearai/ironclaw/issues/7815) (internal) | Onboarding suggestion flow has gaps (refresh, connect) | ⚠️ Incomplete — OOBE doesn't fully close the loop for new users |
| [#7824](https://github.com/nearai/ironclaw/issues/7824) (internal benchmark) | Token cost 4× higher than baseline on PinchBench | ❌ Concerned — cost regression is measurable and significant |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) (new contributor) | Cannot complete agent link from WebUI | ⚠️ Gap — CLI-only workflow blocks non-technical operators |

**Overall:** Two clear user-facing bugs (Notion/Slack install) need attention. Internally, context cost and onboarding completeness are the top improvement vectors.

---

## 8. Backlog Watch

| Item | Priority | Concern |
|------|----------|---------|
| [#7823](https://github.com/nearai/ironclaw/issues/7823) — Notion install fails | 🟡 High | User-reported integration blocker, open since 2026-07-28, no fix PR. |
| [#7822](https://github.com/nearai/ironclaw/issues/7822) — Slack setup fails | 🟡 High | Same reporter, same date, likely shared root cause with #7823. No fix PR. |
| [#7824](https://github.com/nearai/ironclaw/issues/7824) — Context compaction | 🟡 High | Benchmark-driven cost regression; design phase, no implementation PR yet. Critical for scaling. |
| [#7825](https://github.com/nearai/ironclaw/issues/7825) — Sandbox egress auth generic recipes | 🟢 Medium | Architectural cleanup; no PR yet but blocked on #7810 merging first. |
| [#7255](https://github.com/nearai/ironclaw/pull/7255) — APDD kit governance evaluation | 🟢 Low | Docs/governance PR open since 2026-08-05, still under review. |

**Recommendation:** Issues #7822 and #7823 should be triaged together — the shared reporter and proximity suggest a common integration-install regression. #7824 is the highest-impact backlog item; an implementation PR would significantly improve project health metrics.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-23

## 1. Today's Overview

LobsterAI (netease-youdao/LobsterAI) showed moderate activity on 2026-08-23, with **2 issues closed** and **6 PRs merged/closed** in the last 24 hours. No new releases were published. All closed items carried the `[stale]` label, indicating they were automatically closed due to inactivity rather than resolution — a signal worth monitoring. The sole open PR (#2452) addresses a provider-persistence bug in OpenClaw. Overall project health is stable but the stale-closure pattern suggests slower maintainer responsiveness on community contributions.

## 2. Releases

No new releases were published during this period.

## 3. Project Progress

Six PRs were closed/merged today, spanning bug fixes and one feature addition:

| PR | Author | Summary |
|---|---|---|
| [#1205](https://github.com/netease-youdao/LobsterAI/pull/1205) | mingoLzm | **fix(cowork):** Added error toast feedback when session rename fails, preserving the rename input for retry |
| [#1208](https://github.com/netease-youdao/LobsterAI/pull/1208) | swuzjb | **feat(cowork):** Added inline retry button for transient errors (429 rate limits, network faults) in Cowork sessions |
| [#1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | 0xFLX | **fix(web-search):** Resolved Chrome `--disable-blink-features=AutomationControlled` flag conflict caused by external injection |
| [#1212](https://github.com/netease-youdao/LobsterAI/pull/1212) | leedalei | **fix(model):** Raised custom provider limit from 10 to 20, removing a hard-coded cap in Settings |
| [#1214](https://github.com/netease-youdao/LobsterAI/pull/1214) | MaoQianTu | **feat(cowork):** Implemented "Export as Markdown" for session details (closes #1345) |
| [#2452](https://github.com/netease-youdao/LobsterAI/pull/2452) | ump45nose | **fix(openclaw):** Preserves provider prefix for slashed model IDs (e.g. `deepseek-ai/DeepSeek-V4-Flash`) — **still open** |

## 4. Community Hot Topics

- **[Issue #1206](https://github.com/netease-youdao/LobsterAI/issues/1206)** — *Kimi 2.5 duplicate action replies in private deployment.* Zero reactions but a concrete reproduction with screenshot. Reflects growing interest in self-hosted LLM integrations and confidence in model reliability for document analysis workflows.
- **[Issue #1213](https://github.com/netease-youdao/LobsterAI/issues/1213)** — *Export session details as Markdown.* Fully addressed by PR #1214. Signals strong user demand for portable, editable conversation records beyond screenshot-based export.
- **[PR #2452](https://github.com/netease-youdao/LobsterAI/pull/2452)** — *OpenClaw provider prefix loss for slashed model IDs.* The only open PR; highlights pain points with providers using slash notation (DeepSeek, etc.) and the need for correct key-persistence logic.

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|---|---|---|---|
| **Medium** | [Issue #1206](https://github.com/netease-youdao/LobsterAI/issues/1206) | Kimi 2.5 model duplicates action progress replies in private deployment (100% reproducible) | Stale-closed; fix uncertain — user noted switching models resolves it |
| **Low** | [PR #1209](https://github.com/netease-youdao/LobsterAI/pull/1209) | Web-search blocked by unsupported Chrome flag `--disable-blink-features=AutomationControlled` | ✅ Merged |
| **Low** | [PR #1205](https://github.com/netease-youdao/LobsterAI/pull/1205) | Session rename failures silently swallowed with no user feedback | ✅ Merged |
| **Medium** | [PR #2452](https://github.com/netease-youdao/LobsterAI/pull/2452) | OpenClaw strips provider prefix from model IDs containing `/` | 🔄 Open, awaiting merge |

## 6. Feature Requests & Roadmap Signals

- **Session export as Markdown** ([Issue #1213](https://github.com/netease-youdao/LobsterAI/issues/1213) → [PR #1214](https://github.com/netease-youdao/LobsterAI/pull/1214)): Now merged. Future iterations may add PDF or plain-text export alongside it.
- **Manual retry for transient errors** ([PR #1208](https://github.com/netease-youdao/LobsterAI/pull/1208)): Merged. Users increasingly expect resilient error handling in AI agent workflows; similar inline-retry patterns may appear in other modules.
- **Increased custom provider limit** ([PR #1212](https://github.com/netease-youdao/LobsterAI/pull/1212)): Raised from 10 to 20. Suggests power users are accumulating many model providers — the cap may be revisited again.

## 7. User Feedback Summary

- **Private deployment confidence:** Issue #1206 reveals that self-hosted Kimi 2.5 exhibits unexpected behavior during document analysis, eroding trust in the model's reliability for automated workflows. Users expect deterministic progress feedback.
- **Export flexibility:** Issue #1213 / PR #1214 shows users want structured, editable conversation records (Markdown) rather than screenshots, indicating a maturing user base that treats LobsterAI outputs as durable knowledge artifacts.
- **Error visibility:** PR #1205 addresses a UX gap where rename failures were silently ignored — users value immediate, actionable feedback over silent failures.
- **Model provider ergonomics:** PR #2452 and #1212 both point to friction around managing diverse custom providers, especially those with slash-separated IDs.

## 8. Backlog Watch

- **[Issue #1206](https://github.com/netease-youdao/LobsterAI/issues/1206)** — Stale-closed but **unresolved**. Kimi 2.5 duplicate-reply bug in private deployment needs a maintainer decision: reopen and fix, or document as known limitation.
- **[PR #2452](https://github.com/netease-youdao/LobsterAI/pull/2452)** — Open since 2026-08-07, still awaiting review/merge. Affects users of OpenClaw with DeepSeek and similar slashed model IDs; delaying merge risks continued data loss on session patches.
- **Stale-closure pattern:** 7 of 8 closed items carry the `[stale]` label, suggesting the project may benefit from a triage pass to distinguish truly abandoned items from those awaiting maintainer action.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-23

---

## 1. Today's Overview

Moltis saw moderate activity today with one issue closed and three pull requests actively under review, indicating steady forward momentum. No new releases were published, and no PRs were merged in the last 24 hours. The project's focus remains on hardening security controls, fixing compatibility gaps with upstream providers (OpenAI, MCP, Browserless), and closing the loop between policy enforcement and runtime reliability. The absence of closed PRs today is offset by active review cycles on three distinct fixes.

**Activity Assessment:** 🟡 Moderate — consistent issue triage and PR activity, but no merges or releases yet.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

**Closed today:**

- **Issue #1230** — *feat(hooks): add an opt-in fail-closed error policy for modifying security hooks* [Issue #1230](https://github.com/moltis-org/moltis/issues/1230)
  - The project confirmed that `BeforeToolCall` and other modifying hooks already support an explicit `Block` result for policy short-circuiting. The work today closed the remaining gap: hook failures (e.g., timeout, crash) currently degrade to *continuation* rather than blocking. This issue tracked the decision and design for an opt-in fail-closed policy for security hooks. With one comment and a closed status, the approach appears to be landing.

**Under active review (no merges today):**

- **PR #1232** — *fix(tools): make object schemas OpenAI-safe* — [PR #1232](https://github.com/moltis-org/moltis/pull/1232)
- **PR #1231** — *fix(mcp): resolve current client after server restart* — [PR #1231](https://github.com/moltis-org/moltis/pull/1231)
- **PR #1229** — *fix(browser): support Browserless v2 containers* — [PR #1229](https://github.com/moltis-org/moltis/pull/1229)

---

## 4. Community Hot Topics

| Rank | Item | Engagement | Focus Area |
|------|------|-----------|------------|
| 1 | [Issue #1230](https://github.com/moltis-org/moltis/issues/1230) | 1 comment, 0 👍 | Security hook failure policy |
| 2 | [PR #1232](https://github.com/moltis-org/moltis/pull/1232) | 0 comments, 0 👍 | OpenAI schema compatibility |
| 3 | [PR #1231](https://github.com/moltis-org/moltis/pull/1231) | 0 comments, 0 👍 | MCP client lifecycle |
| 4 | [PR #1229](https://github.com/moltis-org/moltis/pull/1229) | 0 comments, 0 👍 | Browserless v2 support |

**Analysis:** The closed issue (#1230) generated discussion, reflecting a real community need around security-critical failure modes. The three open PRs address widely-used integrations (OpenAI tools, MCP bridges, browser automation) — all high-impact fixes with likely broad adoption. Low comment counts across PRs may indicate early review stage or maintainer-led changes.

---

## 5. Bugs & Stability

**Reported / Addressed Today:**

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| 🟠 Medium | [PR #1231](https://github.com/moltis-org/moltis/pull/1231) | MCP tool bridges captured a stale client reference; after a server restart, active chat turns continued dispatching through a closed client instance instead of the replacement. | PR #1231 (open) |
| 🟡 Low | [PR #1232](https://github.com/moltis-org/moltis/pull/1232) | OpenAI strict tool schemas close objects with `additionalProperties=false`, forcing Codex to send null/empty values for patch and map schemas. | PR #1232 (open) |
| 🟡 Low | [PR #1229](https://github.com/moltis-org/moltis/pull/1229) | Browserless v2 container protocol was unsupported, breaking users who had upgraded to v2 containers. | PR #1229 (open) |

**Notable:** No crash reports or regressions were raised today. The bugs addressed are integration-level (MCP lifecycle, schema compliance, container protocol) rather than core stability issues.

---

## 6. Feature Requests & Roadmap Signals

- **Opt-in fail-closed for security hooks** ([Issue #1230](https://github.com/moltis-org/moltis/issues/1230)) — Users want explicit, configurable failure behavior for security-critical hooks. The close of this issue suggests the fail-closed policy is being designed for an upcoming release. This could be a **breaking-change-worthy** feature if it changes default behavior.
- **Browserless v2 support** ([PR #1229](https://github.com/moltis-org/moltis/pull/1229)) — Growing demand from users running Browserless v2 containers; the PR is designed to retain v1 defaults for backward compatibility.
- **MCP server restart resilience** ([PR #1231](https://github.com/moltis-org/moltis/pull/1231)) — Signals a need for more robust MCP connection lifecycle management, likely part of ongoing integrations work.

**Prediction:** If merged, PRs #1229, #1231, and #1232 are strong candidates for inclusion in the next patch or minor release, alongside the fail-closed hook policy from #1230.

---

## 7. User Feedback Summary

- **Security-conscious users** are pushing for fail-closed semantics on modifying hooks — a runtime failure should not silently continue execution when a security boundary is in place. (Issue #1230)
- **OpenAI/Codex users** are experiencing schema compliance friction — `additionalProperties=false` from OpenAI strict mode is causing tool calls to drop data. (PR #1232)
- **MCP power users** need reliable client reuse across server restarts without manual reconfiguration. (PR #1231)
- **Browser automation users** upgrading to Browserless v2 need the bridge to keep working without manual intervention. (PR #1229)

**Satisfaction signal:** All today's items are *fixes* rather than new feature requests, suggesting the community is focused on reliability and integration quality — a healthy sign of product maturity.

---

## 8. Backlog Watch

- **[PR #1232](https://github.com/moltis-org/moltis/pull/1232)** — Created 2026-08-22, still open with no comments. High-impact fix for OpenAI compatibility; benefits from maintainer review.
- **[PR #1231](https://github.com/moltis-org/moltis/pull/1231)** — Created 2026-08-22, still open with no comments. Critical for MCP stability; awaiting review.
- **[PR #1229](https://github.com/moltis-org/moltis/pull/1229)** — Created 2026-08-22, still open with no comments. Forward-looking fix for Browserless v2; awaiting review.

**Recommendation:** All three PRs are one day old with no review comments yet — normal for open-source projects, but maintaining momentum on these will be important to avoid a review backlog.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-23

## 1. Today's Overview

The CoPaw project shows moderate daily activity with 7 issues and 4 open PRs updated in the last 24 hours. No new releases were published. The contributor base remains active, with four of the four PRs coming from first-time contributors — a healthy sign for community engagement. The primary focus today has been on bug fixes and UI/UX refinements rather than major feature launches. One issue was closed (#7043), resolving a Windows UTF-8 encoding concern. Overall project health is stable with no critical outages or regressions flagged.

## 2. Releases

No new releases today. The latest referenced version across reported issues is **2.1.0**.

## 3. Project Progress

**Closed today:**
- [#7043](https://github.com/agentscope-ai/QwenPaw/issues/7043) — Resolved by adding a startup option to execute `chcp 65001`, enabling UTF-8 console output on Chinese Windows systems without requiring users to modify their `$PROFILE`.

**Open PRs advancing (no merges today):**
- [#7214](https://github.com/agentscope-ai/QwenPaw/pulls/7214) — Documentation fix: adds the missing **Access Policy** security layer to README descriptions, bringing documentation in line with the feature table.
- [#7054](https://github.com/agentscope-ai/QwenPaw/pulls/7054) — Enables Chrome extension remote bridge endpoints for LAN/network browsers, removing the loopback-only restriction.
- [#7050](https://github.com/agentscope-ai/QwenPaw/pulls/7050) — Adds per-cron-job model override picker, allowing individual cron jobs to specify their own model instead of inheriting the agent's active model.
- [#6808](https://github.com/agentscope-ai/QwenPaw/pulls/6808) — Fixes custom persona markdown files being hidden in the Files workspace Profile category by removing an overly restrictive six-filename filter.

## 4. Community Hot Topics

- [#7196](https://github.com/agentscope-ai/QwenPaw/issues/7196) — **Most reacted issue** (1 👍). Users report that the always-visible inference process causes serious visual distraction and request a collapsible/default-collapsed setting, similar to the Hermes project. This reflects a broader need for **UI customization and information density control** in agent monitoring dashboards.
- [#7212](https://github.com/agentscope-ai/QwenPaw/issues/7212) — A crash bug where images within the inline size cap but exceeding the provider's pixel limit cause a `MODEL_EXECUTION_ERROR` that terminates the conversation. Paired with [#7201](https://github.com/agentscope-ai/QwenPaw/issues/7201), which requests per-media-type byte caps (image/video/audio) exposed in provider settings, both point to a need for **more granular media handling and graceful degradation**.
- [#7054](https://github.com/agentscope-ai/QwenPaw/pulls/7054) — First-time contributor PR for LAN-based Chrome bridge usage, indicating demand from users running QwenPaw and browsers on **separate machines**.

## 5. Bugs & Stability

| Severity | Issue | Summary |
|----------|-------|---------|
| **High** | [#7212](https://github.com/agentscope-ai/QwenPaw/issues/7212) | Inlining an image exceeding provider pixel limits crashes the request and ends the conversation instead of degrading gracefully. |
| **Medium** | [#7215](https://github.com/agentscope-ai/QwenPaw/issues/7215) | OpenRouter and OpenCode model backends are not fully displayed in the GUI after being added. |
| **Medium** | [#7216](https://github.com/agentscope-ai/QwenPaw/issues/7216) | `execute_shell_command` tool name is intermittently character-replaced in LLM output (e.g., `l→|`), causing `ToolNotFoundError`. |
| **Low** | [#7213](https://github.com/agentscope-ai/QwenPaw/issues/7213) | Session output consistently contains meaningless empty lines, persisting even after repeated user instructions to stop. |

No fix PRs have been opened for the above bugs yet. The character-replacement bug (#7216) is particularly concerning as it suggests a tokenization or prompt-injection issue in tool name handling.

## 6. Feature Requests & Roadmap Signals

- [#7196](https://github.com/agentscope-ai/QwenPaw/issues/7196) — **Collapsible inference process view**: Users want the ability to default-hide reasoning traces and only expand them during debugging. This is a strong UX signal; likely candidate for an upcoming release.
- [#7201](https://github.com/agentscope-ai/QwenPaw/issues/7201) — **Separate per-media-type inline byte caps**: Splitting `max_inline_media_bytes` into independent `max_image_bytes`, `max_video_bytes`, and `max_audio_bytes` controls. Given the paired crash bug (#7212), this feature request is likely to be prioritized alongside the fix.
- [#7050](https://github.com/agentscope-ai/QwenPaw/pulls/7050) — **Per-cron-job model override**: Already implemented in PR; would provide per-job model flexibility.
- [#7054](https://github.com/agentscope-ai/QwenPaw/pulls/7054) — **Remote Chrome bridge**: Expands deployment flexibility for multi-machine setups.

## 7. User Feedback Summary

Users are actively engaging with QwenPaw for agent monitoring and cron-based automation. Key pain points include:

- **Visual clutter**: The always-on inference trace is described as a "serious visual distraction," indicating users value a cleaner default interface.
- **Media handling fragility**: Crashes from oversized images (even within byte limits) erode trust in the system's reliability.
- **Encoding issues on Windows**: Chinese Windows users continue to face UTF-8 pain in shell tool execution, though #7043 addresses part of this.
- **Empty line noise**: Persistent output formatting issues suggest the LLM output post-processing pipeline needs attention.
- **Multi-backend visibility**: Adding OpenRouter/OpenCode backends results in incomplete GUI rendering, pointing to a UI refresh or state management issue.

## 8. Backlog Watch

- [#7216](https://github.com/agentscope-ai/QwenPaw/issues/7216) — **Unanswered since 2026-08-22, 0 comments from maintainers.** The `execute_shell_command` tool name corruption is a correctness bug with no assigned fix. Needs prioritization.
- [#7212](https://github.com/agentscope-ai/QwenPaw/issues/7212) — **Unanswered since 2026-08-22.** The conversation-ending crash on pixel-limit violations should be addressed before or alongside the feature request in #7201.
- [#7215](https://github.com/agentscope-ai/QwenPaw/issues/7215) — **Unanswered since 2026-08-22.** GUI rendering gap for OpenRouter/OpenCode backends blocks users relying on those providers.
- [#7054](https://github.com/agentscope-ai/QwenPaw/pulls/7054) — **Open since 2026-08-15, under review.** A valuable but non-blocking feature; maintainers should review to unblock the contributor.
- [#6808](https://github.com/agentscope-ai/QwenPaw/pulls/6808) — **Open since 2026-08-07.** A simple, low-risk fix for custom persona file visibility; overdue for merge.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-23

## 1. Today's Overview

ZeroClaw is experiencing sustained development velocity with **100 activity events** in the last 24 hours (50 issues + 50 PRs). The project is in a heavy security and architecture-refinement phase, with multiple RFCs advancing through the maintainer decision queue and several high-risk bugs being actively addressed. Five PRs and six issues were closed today, indicating steady closure momentum despite a large open backlog. No new release was published today, suggesting the team is consolidating around the v0.9.0 security and gateway boundary work.

## 2. Releases

No new releases were published.

## 3. Project Progress

**Closed / Merged PRs (5):**

- **[#9281](https://github.com/zeroclaw-labs/zeroclaw/issues/9281)** — *fix(config): roll back auto-created map aliases when config set fails.* Transactional config writes now discard partially materialized aliases on failure, preventing degraded fresh configs.
- **[#9291](https://github.com/zeroclaw-labs/zeroclaw/issues/9291)** — *fix(cli): detect installed AppImage and use a working desktop download URL.* Resolves the broken `zeroclaw desktop` command on Linux by correctly locating menu-registered AppImages and updating the fallback URL.
- **[#9694](https://github.com/zeroclaw-labs/zeroclaw/issues/9694)** — *feat(zerocode): expose the SOP pane as a read-only status view.* SOP live run-status visibility is now reachable via `Mode::Sop` keyboard/mouse navigation.
- **[#9203](https://github.com/zeroclaw-labs/zeroclaw/issues/9203)** — *fix(sop): wire authenticated HTTP fan-in.* Adds `POST /sop/{*rest}` authenticated webhook dispatch with `404`-on-no-match semantics, closing an earlier auth gap.
- **[#9960](https://github.com/zeroclaw-labs/zeroclaw/issues/9960)** — *fix(quickstart): reject duplicate enabled webhook ports.* Prevents config from allowing multiple aliases on the same listener port.

**Key Open PRs Advancing:**
- **[#10265](https://github.com/zeroclaw-labs/zeroclaw/pull/10265)** — Principal-owned sessions with predicated storage deletes (RFC 7141 stage 4). Stacked PR chain advancing the session storage boundary RFC.
- **[#9584](https://github.com/zeroclaw-labs/zeroclaw/pull/9584)** — Egress grant ceremony for plugin install/list (Stage 3 of plugin egress policy).
- **[#9476](https://github.com/zeroclaw-labs/zeroclaw/pull/9476)** — Authenticated operator cancellation for running SOP jobs (`POST /api/sops/{name}/runs/{run_id}/cancel`).
- **[#9744](https://github.com/zeroclaw-labs/zeroclaw/pull/9744)** — Requires authenticated webhook ingress for WhatsApp Cloud, Linq, and Nextcloud Talk gateway channels.
- **[#9645](https://github.com/zeroclaw-labs/zeroclaw/pull/9645)** — ZeroRouter self-hostable metered LLM gateway as a first-class compat provider family with device-flow login.

## 4. Community Hot Topics

| Issue | Title | Comments | Link |
|---|---|---|---|
| #9487 | RFC: Runtime-owned conversation sessions and transport surface adapters | 24 | [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) |
| #7462 | Bug: 74 test failures on Windows | 19 | [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) |
| #6850 | RFC: Decouple memory lifecycle policy from storage backends | 16 | [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) |
| #8780 | RFC: Realtime speech-to-speech channel for Gemini Live | 16 | [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) |
| #8692 | Tracker: Maintainer decision queue for RFCs | 13 | [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |

**Analysis:** The top discussion围绕 (revolves around) architectural RFCs — session ownership boundaries (#9487) and memory lifecycle decoupling (#6850) — indicating the community is deeply engaged in the v0.9.0 structural hardening. The Windows CI gap (#7462) remains a persistent pain point with no fix merged. The Gemini Live realtime voice channel (#8780) and the maintainers' RFC decision tracker (#8692) show both feature ambition and process maturation.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|---|---|---|---|
| **P1 / High** | [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) | `block_high_risk_commands = false` not honored — allowlisted commands still blocked on parent path | No open fix PR |
| **P1 / High** | [#9718](https://github.com/zeroclaw-labs/zeroclaw/issues/9718) | Telegram duplicate messages when model emits both `tool_call` and `content` | No open fix PR |
| **P1 / High** | [#9436](https://github.com/zeroclaw-labs/zeroclaw/issues/9436) | `config init` writes template sections that fail strict loader — fresh config born degraded | Closed; expect follow-up |
| **P2 / Medium** | [#10232](https://github.com/zeroclaw-labs/zeroclaw/issues/10232) | Daemon diagnostics drop underlying error chain | No open fix PR |
| **P2 / Medium** | [#9708](https://github.com/zeroclaw-labs/zeroclaw/issues/9708) | Daemon stdout/stderr logs unbounded (no size/age/file-count limits) | No open fix PR |
| **P2 / Medium** | [#9666](https://github.com/zeroclaw-labs/zeroclaw/issues/9666) | Filesystem channel listener not cancellation-aware; blocks shutdown | No open fix PR |
| **P2 / Medium** | [#9590](https://github.com/zeroclaw-labs/zeroclaw/issues/9590) | Concurrent `models refresh` runs can lose cache entries (race condition) | No open fix PR |
| **P2 / Medium** | [#10251](https://github.com/zeroclaw-labs/zeroclaw/issues/10251) | 17 Telegram `listen_*` tests assert on wall-clock timeouts (flaky CI) | No open fix PR |
| **P2 / Medium** | [#9001](https://github.com/zeroclaw-labs/zeroclaw/issues/9001) | Provider turn failures bury cause under generic retry envelope | No open fix PR |
| **P3 / Low** | [#9202](https://github.com/zeroclaw-labs/zeroclaw/issues/9202) | `zeroclaw desktop` dead download URL / AppImage detection | **Fixed in #9291** (closed) |

**Notable closed bugs:** #9255 (WASM plugin no wall-clock timeout), #9640 (WhatsApp doc cites removed V2 config key), #9339 (custom CA trust for MCP servers).

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Description | Likelihood for Next Release |
|---|---|---|
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | Realtime speech-to-speech channel (Gemini Live broker contract) | Medium — RFC v2 rewritten, needs maintainer review |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) | Verbatim channel send over gateway without agent turn | Low — new RFC, 4 comments, needs sponsor |
| [#5607](https://github.com/zeroclaw-labs/zeroclaw/issues/5607) | Deterministic precondition gates for cron jobs | Medium — accepted, low complexity |
| [#7943](https://github.com/zeroclaw-labs/zeroclaw/issues/7943) | Backend-agnostic voice-host channel (CrispASR / Wyoming-aligned) | Medium — in-progress, complements #8780 |
| [#8850](https://github.com/zeroclaw-labs/zeroclaw/issues/8850) | Move optional channels/tools to runtime WASM plugins | High — in-progress, architectural cornerstone |
| [#10141](https://github.com/zeroclaw-labs/zeroclaw/issues/10141) | Make sessions usable in zerocode (copy, navigate) | Medium — accepted, user-facing UX gap |

**Strong roadmap signal:** The v0.9.0 tracker [#7432](https://github.com/zeroclaw-labs/zeroclaw/issues/7432) and SOP milestone tracker [#8288](https://github.com/zeroclaw-labs/zeroclaw/issues/8288) indicate the next release will center on **auth gateway boundaries, SOP daemon ownership, and WASM plugin runtime loading**.

## 7. User Feedback Summary

- **Session management is frustrating.** [#10141](https://github.com/zeroclaw-labs/zeroclaw/issues/10141) — users report difficulty re-entering previous sessions and copying message snippets in zerocode. This is a direct UX quality signal for the TUI.
- **Windows CI exclusion is a credibility gap.** [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) — 74 test failures on Windows go undetected because CI only runs Linux. Contributors are filing workarounds instead of fixes.
- **Auth/permission confusion persists.** [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) — a P1 bug where explicit `block_high_risk_commands = false` is ignored, suggesting the security policy surface is not yet intuitive.
- **Config onboarding is fragile.** [#9436](https://github.com/zeroclaw-labs/zeroclaw/issues/9436) — freshly generated configs fail strict loading, eroding first-run confidence (now closed but indicates schema maturity issues).
- **Desktop Linux experience needs polish.** [#9202](https://github.com/zeroclaw-labs/zeroclaw/issues/9202) — dead download URL and undetected AppImage installs (now fixed in #9291).

## 8. Backlog Watch

| Issue | Age | Risk | Why It Matters |
|---|---|---|---|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | ~74 days | High | 74 Windows test failures unmasked; no maintainer fix yet |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | ~93 days | High | Memory lifecycle RFC needs maintainer review; blocks architecture cleanup |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | ~78 days | Medium | Gemini Live realtime voice RFC v2 pending review |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | ~87 days | High | Granular sandbox policy RFC — drift between app-layer and OS sandbox |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) | ~87 days | Medium | Wire protocol first-class in provider construction — RFC pending review |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | ~80 days | Medium | Maintainer decision queue tracker itself is stalled |
| [#5607](https://github.com/zeroclaw-labs/zeroclaw/issues/5607) | ~135 days | Medium | Cron precondition gates — accepted but no PR |

**Overall health assessment:** Active development with strong RFC throughput and steady PR closure, but a growing backlog of P1/P2 bugs (especially around security policy correctness and Windows test coverage) and several long-open RFCs waiting on maintainer review. The project is investing heavily in v0.9.0 security and gateway boundaries — the community should watch for a release candidate anchored around those changes.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*