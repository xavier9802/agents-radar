# OpenClaw Ecosystem Digest 2026-09-06

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-06 04:06 UTC

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



# OpenClaw Project Digest — 2026-09-06

## 1. Today's Overview

OpenClaw shows very high activity levels today, with **500 issues and 500 PRs updated in the last 24 hours** — a vigorous pace indicating sustained development momentum. The project released **v2026.9.2** today, focused on chat responsiveness and dashboard performance under heavy transcript load. The issue landscape remains dominated by session-state integrity, message-loss, and Gateway event-loop blocking bugs, while PR activity is heavily concentrated on gateway lifecycle, channel reliability, and infrastructure cleanup. Overall project health is strong with clear maintainer engagement (steipete is highly active) and a healthy mix of bug fixes, refactors, and feature work flowing through review.

## 2. Releases

### v2026.9.2 (2026-09-06)

**Highlights:**
- **Faster, more responsive chat** — chat, dashboards, and session interactions remain responsive while long transcripts and disk usage are processed
- Direct dashboard lookup with less cold-load work
- Durable history reads moved outside the Gateway event loop (#136862, #138)

**Breaking changes / migration notes:** None explicitly documented for this release.

## 3. Project Progress

### Notable PRs Advanced Today

- **#139704** — [feat] Report failed updates with explicit consent (Android/WebUI/Gateway/CLI) — lets users submit sanitized issues directly from Control UI after update failures. *(status: open)*
- **#135865** — [fix] Saving agent workspace files from Control UI no longer overwrites content changed since open *(P1, gold shrimp)* — fixes concurrent-edit collision on SOUL.md, MEMORY.md, etc. *(status: open)*
- **#139421** — [fix] Reconcile pairing lifecycle after token removal — fixes broken state when revoking node tokens *(P1, platinum hermit)* — side of #135868 split. *(status: ready for maintainer look)*
- **#139394** — [fix] Recover queued messages after timeouts — closes #139341, prevents message loss after 5-minute adoption timeout *(P0, platinum hermit)* — **high impact**.
- **#139685** — [fix] ACP: preserve queued output and cancel failed deliveries — closes #139680, fixes ACP output loss when completion overtakes slow delivery *(P1, platinum hermit)*.
- **#139614** — [fix] Feishu: stop dead-stream log flooding + non-streaming card fallback — closes #139443 *(P1, silver shellfish, needs proof)*.
- **#139649** — [fix] Report failed bundled catalog refreshes — model list refresh no longer silently swaps in starter models on provider failure.
- **#135599** — [feat] Manage and reload plugins without restarting the Gateway *(P2, platinum hermit)* — major infra improvement, wide scope across channels and plugins.
- **#139657** — [fix] Require cleanup evidence before releasing owned work — prevents resource leaks after transport/session lifecycle events.
- **#139701** — [fix] Preserve restart outcomes and update-history ownership — fixes update history gaps during native service parking.

### Closed/Merged Today
- **#139684** — refactor(android): reuse cron interval formatting
- **#139636** — refactor(auth): share legacy choice resolution across onboarding

## 4. Community Hot Topics

### Top Issues by Comment Activity

| Issue | Title | Comments | Rating |
|---|---|---|---|
| [#69208](https://github.com/openclaw/openclaw/issues/69208) | Umbrella: duplicate transcript, replay, and context assembly across channels | 14 | 🦪 silver shellfish |
| [#132762](https://github.com/openclaw/openclaw/issues/132762) | Overflow retry can end successfully on a tool result without final delivery | 13 | 🦞 diamond lobster |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | Write/exec tool parameters silently dropped after long conversations | 12 | 🦪 silver shellfish |
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | Built-in headless browser for reliable web access | 12 | 🌊 off-meta tidepool |
| [#39476](https://github.com/openclaw/openclaw/issues/39476) | A2A sessions_send: target agent can call back, causing duplicate messages | 12 | 🦞 diamond lobster |
| [#96975](https://github.com/openclaw/openclaw/issues/96975) | Isolate subagent completion from parent context | 12 | 🌊 off-meta tidepool |

**Underlying needs:** The community is heavily focused on **session state integrity** (message loss, duplicate replies, context assembly) and **multi-agent orchestration reliability**. The headless browser request (#53763) signals demand for self-contained web automation without external dependencies. The "umbrella" issue (#69208) suggests systemic architecture debt around transcript replay that affects every channel.

### Top PRs by Discussion

- [#139704](https://github.com/openclaw/openclaw/pulls/139704) — Failed update reporting with consent
- [#135865](https://github.com/openclaw/openclaw/pulls/135865) — Workspace file overwrite fix
- [#139421](https://github.com/openclaw/openclaw/pulls/139421) — Pairing lifecycle reconciliation

## 5. Bugs & Stability

### Critical / P0 Issues

| Issue | Summary | Status | Fix PR |
|---|---|---|---|
| [#115642](https://github.com/openclaw/openclaw/issues/115642) | Billing cooldown outlives outage; no probe-based recovery for subscription auth | Open, P0, diamond lobster | — |
| [#91931](https://github.com/openclaw/openclaw/issues/91931) | Preseeded SOUL.md/IDENTITY.md auto-completes bootstrap and deletes user BOOTSTRAP.md | Open, P0, diamond lobster | — |
| [#124133](https://github.com/openclaw/openclaw/issues/124133) | openclaw-snowluma: `formatInboundEnvelope is not a function` (beta blocker) | Open, beta-blocker | — |
| [#136148](https://github.com/openclaw/openclaw/issues/136148) | Linux desktop AppImage: WebKitWebProcess SIGABRT at EGL init | **Closed** | — |

### High-Severity (P1, diamond lobster) Issues

| Issue | Summary | Fix PR? |
|---|---|---|
| [#132762](https://github.com/openclaw/openclaw/issues/132762) | Overflow retry ends success with toolResult, no final delivery | No |
| [#39476](https://github.com/openclaw/openclaw/issues/39476) | A2A sessions_send callback causes duplicate messages | Linked PR open |
| [#110190](https://github.com/openclaw/openclaw/issues/110190) | Runtime context carrier after user message causes model confusion | No |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | Sync agent persistence blocks Gateway event loop at scale | Partial fix (#133925, #134062) |
| [#136183](https://github.com/openclaw/openclaw/issues/136183) | Command executor hangs on SSH spawn — SIGTERM (regression in 2026.8.1) | No |
| [#112259](https://github.com/openclaw/openclaw/issues/112259) | Zero-payload inbound turn silently dropped, no retry/DLQ | No |
| [#132765](https://github.com/openclaw/openclaw/issues/132765) | `agents_wait` ignores timeoutSeconds, dies after ~60s | No |
| [#127148](https://github.com/openclaw/openclaw/issues/127148) | Codex sessions.compact acquires second app-server, hits conflict | No |
| [#99910](https://github.com/openclaw/openclaw/issues/99910) | Memory dreaming pegs Gateway event loop ~10 min | No |
| [#53008](https://github.com/openclaw/openclaw/issues/53008) | Memory compaction blocks main lane 10+ min | No |
| [#78055](https://github.com/openclaw/openclaw/issues/78055) | Subagent announce delivers stale output, inherits unrelated history | Linked PR open |
| [#84110](https://github.com/openclaw/openclaw/issues/84110) | Codex app-server rewrites prompt mid-turn, busts OpenAI cache (93%→47%) | Linked PR open |
| [#89430](https://github.com/openclaw/openclaw/issues/89430) | Google Chat: can't deliver images/files under app auth (403) | Linked PR open |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Unreaped hook/tool child processes → zombie accumulation | No |
| [#114967](https://github.com/openclaw/openclaw/issues/114967) | Agent-driven live update left launchctl keepalive force-restarting gateway | No |

### Notable Regressions
- **#136183** — SSH executor hang (regression in 2026.8.1, persists in 2026.8.2)
- **#124133** — snowluma channel runtime error (beta blocker, 2026.8.1-beta.2)
- **#91941** — Feishu streaming card full-content updates cause latency regression

### Active Fix PRs
- **#139394** — recovers queued messages after timeouts (addresses #139341)
- **#139614** — Feishu dead-stream log flooding (#139443)
- **#139685** — ACP output loss on slow delivery (#139680)
- **#132491** — visitor-access bounded JSON responses (security)

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Likelihood |
|---|---|---|
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | Built-in headless Chromium for reliable web access | Medium — significant scope, but strong community demand |
| [#6599](https://github.com/openclaw/openclaw/issues/6599) | `/models test-fallback` command to verify fallback chain | Low-Medium — narrow but useful for ops |
| [#132781](https://github.com/openclaw/openclaw/issues/132781) | Use latest commentary as progress draft label when narration unavailable | Low — UX polish |
| [#116716](https://github.com/openclaw/openclaw/issues/116716) | Strict failure policy for context engines | Medium — important for enterprise deployments |
| [#85461](https://github.com/openclaw/openclaw/issues/85461) | Capture image-generation provider usage metadata | Low-Medium — observability improvement |
| [#71452](https://github.com/openclaw/openclaw/issues/71452) | Pagination for `list chat` / `list messages` (current 25 limit) | Medium — simple but widely felt pain point |

**Roadmap signal:** The merged/closed plugin hot-reload work (#135599) and the active #135868 split campaign (lifecycle, pairing, daemon tests) suggest the near-term roadmap prioritizes **operational reliability** (no-restart plugin management, cleanup guarantees, update robustness) over new agent capabilities. The v2026.9.2 release further confirms the responsiveness/performance track.

## 7. User Feedback Summary

**Pain points:**
- **Session state loss and duplication** are the dominant frustration — users report messages vanishing, duplicate replies across channels, and subagent output leaking into parent sessions (#69208, #39476, #78055, #112259)
- **Gateway unresponsiveness during compaction/dreaming** (#53008, #99910) causes real outages in production; users describe the bot going silent for 10+ minutes
- **Tool parameter loss after long conversations** (#53408) — `write`/`exec` tools silently drop arguments, causing confusing failures
- **Billing cooldown too aggressive** (#115642) — 5-hour lockout outlives actual provider outages, especially painful for subscription models
- **Process/zombie leaks** (#97616) — long-running gateways degrade as child processes accumulate
- **Feishu streaming latency** on long replies (#91941) and **log flooding** on dead streams
- **TUI scroll-jump** (#44130) remains an unresolved UX friction point (6 comments, 3 👍)

**Satisfaction signals:**
- The v2026.9.2 responsiveness fix addresses a widely felt pain point
- Plugin hot-reload (#135599) is a highly anticipated feature
- The `agents_wait` timeout fix and ACP output preservation show responsive maintenance

## 8. Backlog Watch

### Long-Standing P1/P0 Issues Needing Maintainer Attention

| Issue | Age | Blockers |
|---|---|---|
| [#115642](https://github.com/openclaw/openclaw/issues/115642) | 2026-07-29 (69 days) | P0, no fix PR, clawsweeper:needs-product-decision |
| [#91931](https://github.com/openclaw/openclaw/issues/91931) | 2026-06-10 (119 days) | P0, no fix PR, impacts bootstrap integrity |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | 2026-03-24 (166 days) | P2 but widely felt; tool params silently dropped |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 2026-06-29 (100 days) | P1, zombie process leak, no fix PR |
| [#112259](https://github.com/openclaw/openclaw/issues/112259) | 2026-07-21 (77 days) | P1, silent message loss, no retry/DLQ |
| [#99910](https://github.com/openclaw/openclaw/issues/99910) | 2026-07-04 (94 days) | P1, Gateway event loop pegged 10 min, recovery-stuck |
| [#53008](https://github.com/openclaw/openclaw/issues/53008) | 2026-03-23 (167 days) | P1, compaction blocks main lane, no fix PR |
| [#119720](https://github.com/openclaw/openclaw/issues/119720) | 2026-08-05 (62 days) | P1, sync persistence blocks Gateway at scale |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) | 2026-04-26 (133 days) | P1, active-memory blocks replies, gateway overload |
| [#69208](https://github.com/openclaw/openclaw/issues/69208) | 2026-04-20 (139 days) | Umbrella issue, 14 comments, no resolution path |

**Key concern:** The backlog contains multiple **platinum hermit** and **diamond lobster** rated issues that are months old with no active fix PRs. The session-state integrity and Gateway event-loop blocking problems form a clustered set of interrelated architectural debt that will likely require a dedicated effort rather than incremental fixes. The `clawsweeper:needs-product-decision` tag on several P0 items (#115642, #91931) suggests these require strategic choices before engineering work can proceed.

---

*Generated from GitHub data for 2026-09-06. OpenClaw is developed by the open-source

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Open-Source Ecosystem
**Date:** 2026-09-06 | **Projects Analyzed:** 10

---

## 1. Ecosystem Overview

The open-source personal AI assistant landscape in September 2026 is characterized by a clear maturity divide: a handful of high-velocity platforms (OpenClaw, ZeroClaw, CoPaw) are shipping major releases and scaling community contributions, while a longer tail of projects oscillates between active hardening and quiet maintenance. The dominant architectural challenge across nearly every project is **session-state integrity and event-loop blocking under load**—a signal that the ecosystem is transitioning from proof-of-concept agents to production-grade deployments. Security hardening, provider reliability, and multi-tenant support have emerged as the three pillars defining the next release cycle across the board.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release | Health Score* |
|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | v2026.9.2 ✅ | 🟢 Excellent |
| **ZeroClaw** | 42 | 50 | v0.8.5 ✅ | 🟢 Excellent |
| **Hermes Agent** | 50 | 50 | — | 🟡 Moderate |
| **CoPaw** | 11 | 7 | — | 🟢 Good |
| **NanoBot** | 1 | 25 (7 merged) | — | 🟡 Moderate |
| **ZeptoClaw** | 10 open | 3 merged | — | 🟢 Good |
| **PicoClaw** | 2 | 3 merged | — | 🟡 Stable |
| **NanoClaw** | 0 | 3 open (0 merged) | — | 🟡 Low |
| **IronClaw** | 1 | 1 open (0 merged) | — | 🟡 Low |
| **LobsterAI** | 0 | 2 stale | — | 🔴 Stalled |
| **NullClaw** | 0 | 0 | — | 🔴 Dormant |

*Health Score: based on issue/PR volume, merge velocity, release cadence, and community engagement.

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Sheer scale:** 500 issues and 500 PRs per day dwarfs every other project (next closest: ZeroClaw at ~92 combined). This indicates the largest active user and contributor base by far.
- **Release velocity:** v2026.9.2 shipped today with measurable performance improvements (dashboard responsiveness, durable history reads), demonstrating a pattern of iterative performance releases rather than feature bloat.
- **Maintainer engagement:** `steipete` is highly active; P0 bugs receive prompt triage with explicit severity ratings (diamond lobster, platinum hermit).

**Technical approach differences:**
- OpenClaw's **Gateway-centric architecture** (event loop, channel pluggability, plugin hot-reload) is more infra-heavy than NanoBot's unified `MessageBus` or ZeptoClaw's Rust-native subprocess model.
- OpenClaw invests heavily in **multi-channel session state** (duplicate transcript assembly, A2A callbacks, subagent context isolation)—a problem set almost entirely absent from smaller projects.
- Its **billing/provisioning stack** (cooldown bugs, provider auth probes) reflects enterprise-grade deployment concerns that lighter projects don't yet face.

**Community size comparison:** OpenClaw's 500+ daily interactions suggest a contributor base an order of magnitude larger than CoPaw (~18) or NanoBot (~8), and likely 5–10x larger than Hermes Agent's active cohort.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Need |
|---|---|---|
| **Session-state integrity** | OpenClaw, NanoBot, Hermes Agent, ZeroClaw | Message loss, duplicate replies, context assembly failures across channels |
| **Gateway / event-loop blocking** | OpenClaw, NanoBot, Hermes Agent | Memory compaction, dreaming, and sync persistence pegging the main thread for 10+ minutes |
| **Provider reliability & failover** | NanoBot, OpenClaw, ZeroClaw | NIM timeouts causing agent freezes; billing cooldown outliving actual outages |
| **Session persistence & lifecycle** | NanoBot, Hermes Agent, ZeroClaw | Path-traversal vulnerability (#5564), discarded sessions reviving, Desktop↔native divergence |
| **Security hardening** | ZeptoClaw, ZeroClaw, NanoBot, Hermes Agent | Credential leakage in spawned subprocesses, OAuth persistence regressions, sandbox misconfiguration |
| **Multi-agent orchestration** | OpenClaw, ZeroClaw, CoPaw | Subagent output leaking into parent context; bounded delegates stripping tools; A2A duplicate messages |
| **Update / deployment reliability** | Hermes Agent, OpenClaw, CoPaw | Fleet restart loops, ZIP fallback deleting assets, stale update receipts |
| **MCP integration maturity** | CoPaw, LobsterAI, Hermes Agent, ZeroClaw | Per-session MCP toggles, OAuth auto-refresh, tool-call timeout configuration |

---

## 5. Differentiation Analysis

| Project | Differentiator | Target User | Architecture |
|---|---|---|---|
| **OpenClaw** | Multi-channel gateway with plugin hot-reload; largest ecosystem | Enterprise / power users running agents across Slack, Discord, Feishu, A2A | Node.js Gateway + pluggable channels |
| **ZeroClaw** | RFC-driven governance; WASM plugin sandbox; ZeroRelay/ZeroRouter | Security-conscious operators; multi-agent teams | Rust-native; structured RFC process |
| **CoPaw** | Multi-tenant Hub edition; Advisor Mode (dual-model per task); skill versioning | Teams / orgs; Qwen ecosystem users | TypeScript; agent-scope tooling |
| **NanoBot** | Unified MessageBus event architecture; per-invocation model presets | Developers wanting clean event plumbing | Node.js; event-driven core |
| **Hermes Agent** | macOS LaunchAgent lifecycle; per-task profile routing; skills-catalog compaction | macOS-native users; multi-persona delegators | Node.js + Python; daemon-focused |
| **ZeptoClaw** | Security-first Rust implementation; fail-closed on invalid config; audit-chain persistence | Security audit-driven deployments | Rust; minimal surface area |
| **PicoClaw** | Embedded/IRC focus; minimalist scope; bulk-merge maintenance style | IRC bot integrators; constrained environments | Likely embedded Rust/C |
| **NanoClaw** | Signal-channel specialization; conservative release cadence | Signal-native users | Node.js |
| **IronClaw** | Pi sandbox defaults; benchmark-oriented; low community velocity | Research / benchmark teams | TBD |
| **LobsterAI** | Enterprise MCP per-session control; monolithic frontend refactoring | Netease internal / enterprise | TypeScript; large React components |
| **NullClaw** | Dormant | — | — |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (high volume, frequent releases, strong maintainer engagement)**
- **OpenClaw:** 500/500 daily throughput; v2026.9.2 shipped; active P0 triage
- **ZeroClaw:** v0.8.5 shipped today (454 commits, 73 contributors); 42 issues / 50 PRs in 24h; RFC-driven governance

**Tier 2 — Active Hardening (steady PR flow, bug-fix focused, no recent release)**
- **CoPaw:** Pre-2.2.0 cycle; 11 issues / 7 PRs; multi-tenant roadmap confirmed; first-time contributors succeeding
- **NanoBot:** 25 PRs updated, 7 merged; architectural unification (MessageBus) landed; provider-failover fixes in flight
- **ZeptoClaw:** 3 security PRs merged in concentrated burst; P0 audit findings addressed rapidly

**Tier 3 — Moderate Activity with Backlog (high issue count, low close rate)**
- **Hermes Agent:** 50/50 daily updates but only 2 closed; large open backlog; 163-comment stale issue on skills freshness

**Tier 4 — Low Velocity / Maintenance Mode**
- **PicoClaw:** 2 issues / 3 merged PRs; bulk-merge pattern; IRC-focused niche
- **NanoClaw:** 0 new issues, 3 open PRs, 0 merges; review bottleneck likely
- **IronClaw:** 1 issue / 1 PR; stacked-PR dependency chain; benchmark-oriented

**Tier 5 — Stalled or Dormant**
- **LobsterAI:** 2 PRs stale for ~5 months; no new issues or merges
- **NullClaw:** Zero activity; project appears inactive

---

## 7. Trend Signals

| Trend | Evidence | Value for AI Agent Developers |
|---|---|---|
| **Session-state integrity is the #1 cross-project concern** | OpenClaw (#69208, #39476), NanoBot (#5589, #5633), ZeroClaw (#10534) | Any production agent must invest in deterministic message delivery, idempotent tool calls, and explicit session boundaries |
| **Event-loop blocking kills production reliability** | OpenClaw (#53008, #99910), NanoBot (#5580), Hermes Agent | Architecture must offload compaction, dreaming, and persistence to background workers; blocking the main dispatch is a deployment-killer |
| **Provider failover is table-stakes** | NanoBot (#5675), OpenClaw (#115642), ZeroClaw (#10533) | Agents that freeze on provider timeout are unusable in production; explicit retry/failover chains with per-model budgets are expected |
| **Security hardening is accelerating post-v1** | ZeptoClaw (credential scrubbing), ZeroClaw (Seatbelt regression), NanoBot (path traversal) | Projects past initial release are treating credential isolation, subprocess sandboxing, and config validation as P0—not nice-to-have |
| **Multi-tenancy and per-session control are emerging requirements** | CoPaw Hub (#7318), LobsterAI (#1070), ZeroClaw (bounded delegates) | Single-user agent architecture is sufficient for personal use but inadequate for team deployments; per-session MCP, model, and tool configuration is the next wave |
| **RFC-driven governance correlates with community ownership** | ZeroClaw (33-comment session RFC), CoPaw (23-comment Hub discussion) | Projects that formalize community proposal processes see higher-quality feature requests and smoother roadmap alignment |
| **Update/deployment reliability is an unsolved class of problems** | Hermes Agent (fleet restart loops, ZIP fallback bugs), OpenClaw (update history gaps) | Self-updating agents need rollback guarantees, stale-receipt detection, and atomic asset replacement—gaps that persist across the ecosystem |
| **MCP integration is maturing from experimental to operational** | CoPaw (#6874), LobsterAI (#1070), Hermes Agent (#80583) | Tool-call timeouts, OAuth auto-refresh, and per-session server toggles are the features users are building now—early movers in MCP UX will capture enterprise adoption |

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-06

## 1. Today's Overview

NanoBot exhibited **high development velocity** today with 25 PRs updated and 7 merged/closed in the last 24 hours, indicating strong contributor momentum. No new releases were published. A single open issue was reported — a P2 bug affecting Nvidia NIM provider stability. The project is in an active hardening phase, with today's merged PRs focusing on event unification, developer experience, and test cleanup rather than feature expansion.

## 2. Releases

No new releases today.

## 3. Project Progress

**Merged / Closed Today (2 PRs with 2026-09-05 close date):**

- **[PR #5670](https://github.com/HKUDS/nanobot/pull/5670)** — `refactor(events): unify scoped runtime notifications across clients` — Replaced ad-hoc event delivery with a unified `MessageBus`-based approach for both awaited local subscriptions and queued channel delivery, while migrating context compaction end-to-end. Wire payloads and persisted session formats remain compatible. This is a significant architectural improvement that reduces event-handling complexity across WebUI and TUI clients.

- **[PR #5671](https://github.com/HKUDS/nanobot/pull/5671)** — `fix(cli): skip WebUI bundle check in dev mode` — Resolved a false-warning issue where `nanobot webui --dev` emitted stale-bundle warnings despite Vite serving the current source tree. Improves developer experience during local development.

**Notable Open PRs Updated Today:**
- **[PR #5675](https://github.com/HKUDS/nanobot/pull/5675)** — Fixes the Nvidia NIM timeout bug (#5674) by allowing model failover after runner deadlines, so healthy fallback providers are attempted instead of the entire chain being cancelled.
- **[PR #5676](https://github.com/HKUDS/nanobot/pull/5676)** — Adds per-invocation Desktop target selection to `nanobot` and `nanobot webui`, keeping Desktop and Python installs independent.

## 4. Community Hot Topics

| Topic | Link | Analysis |
|---|---|---|
| Nvidia NIM timeout → agent deadlock | [Issue #5674](https://github.com/HKUDS/nanobot/issues/5674) · [PR #5675](https://github.com/HKUDS/nanobot/pull/5675) | High-severity user-facing bug: when Nvidia NIM returns a timeout error, Nanobot misclassifies it as a model output and the agent freezes. A fix PR (#5675) was opened the same day, suggesting strong community responsiveness to provider-reliability concerns. |
| Session key path-traversal vulnerability | [PR #5633](https://github.com/HKUDS/nanobot/pull/5633) | Security-critical (P1). Untrusted session IDs like `../../etc/passwd` could escape the sessions directory. Now fixed with input validation at the persistence chokepoint. Highlights growing production adoption where session IDs may be user-supplied. |
| Heartbeat model cost optimization | [PR #4549](https://github.com/HKUDS/nanobot/pull/4549) | Long-standing request (open since June 26) for a cheaper `model_override` on heartbeat checks. Reflects user demand for cost-efficient always-on deployments. Still blocked by conflicts. |
| Discarded sessions reviving | [PR #5589](https://github.com/HKUDS/nanobot/pull/5589) | P1 bug where pending/deferred messages from discarded sessions leak into the global message bus during task cleanup. Indicates session lifecycle management is a pain point as concurrency grows. |

## 5. Bugs & Stability

| Severity | Issue | PR | Status |
|---|---|---|---|
| **P1** | Session path-traversal injection (#5564) | [#5633](https://github.com/HKUDS/nanobot/pull/5633) | Open — fix in progress |
| **P1** | Discarded sessions can revive and leak messages | [#5589](https://github.com/HKUDS/nanobot/pull/5589) | Open — fix in progress |
| **P1** | Session persistence blocks the event loop | [#5580](https://github.com/HKUDS/nanobot/pull/5580) | Open — fix in progress |
| **P2** | Nvidia NIM timeout causes agent to stop ([#5674](https://github.com/HKUDS/nanobot/issues/5674)) | [#5675](https://github.com/HKUDS/nanobot/pull/5675) | Open — fix PR created today |
| **P2** | Idle-session summary cache grows unbounded | [#5664](https://github.com/HKUDS/nanobot/pull/5664) | Open — fix in progress |
| **P2** | Dream memory files (SOUL.md, USER.md) can grow without size caps | [#5630](https://github.com/HKUDS/nanobot/pull/5630) | Open — fix in progress |
| **P2** | Model retry status not surfaced in UI | [#5504](https://github.com/HKUDS/nanobot/pull/5504) | Open — fix in progress |
| **P2** | Dispatcher exception can halt all outbound messaging | [#5457](https://github.com/HKUDS/nanobot/pull/5457) | Open — fix in progress |
| **P2** | Ephemeral SDK runs incorrectly persist session state | [#5471](https://github.com/HKUDS/nanobot/pull/5471) | Open — fix in progress |
| **P2** | WebUI broken for remote project paths | [#5673](https://github.com/HKUDS/nanobot/pull/5673) | Open — fix in progress |

**Assessment:** 10 open bug/regression PRs across P1 and P2 severity. The project has a concentrated burst of stability fixes in flight, particularly around session management, memory bounds, and provider resilience. The P1 path-traversal and session-revival bugs are the most urgent from a security/correctness standpoint.

## 6. Feature Requests & Roadmap Signals

| Feature | PR | Open Since | Signal |
|---|---|---|---|
| Cheaper heartbeat model via `model_override` | [#4549](https://github.com/HKUDS/nanobot/pull/4549) | Jun 26 | Strong cost-optimization demand; likely in next release if conflicts resolve |
| Shared-session heartbeat execution | [#4551](https://github.com/HKUDS/nanobot/pull/4551) | Jun 26 | Complements #4549; users want heartbeat to reuse existing session context |
| Per-spawn model presets with allowlist | [#5561](https://github.com/HKUDS/nanobot/pull/5561) | Aug 27 | Addresses multi-agent deployment flexibility; alternative to earlier #4291 |
| Signed direct-delivery webhooks | [#5652](https://github.com/HKUDS/nanobot/pull/5652) | Sep 4 | Enables CI/monitoring systems to push deterministic notifications — signals production/DevOps use cases |
| MCP App result metadata preservation | [#5386](https://github.com/HKUDS/nanobot/pull/5386) | Aug 13 | Improves MCP tooling integration; preserves structured data without bloating model context |
| OAuth token auto-refresh for MCP | [#5573](https://github.com/HKUDS/nanobot/pull/5573) | Aug 27 | Reliability improvement for authenticated MCP servers; likely merge-ready |

**Prediction:** The next release will likely include PRs #5675 (provider failover), #5633 (session security), #5580 (event loop offload), #5664 (cache bounds), #5630 (memory file size guards), and #5573 (OAuth refresh) — all P1/P2 stability fixes with completed implementations. Cost-optimization features (#4549, #4551) may be deferred due to open conflicts.

## 7. User Feedback Summary

- **Provider reliability is the top concern.** The Nvidia NIM timeout bug (#5674) directly impacts users relying on NVIDIA's hosted models in production. The agent freezing on provider errors suggests the error-handling pipeline needs more robust classification between "model output" and "provider error."
- **Session lifecycle is fragile.** Three separate bugs (#5589, #5633, #5580) all point to session management as a weak spot — path traversal, discarded sessions reviving, and event-loop blocking. Users running Nanobot at scale are hitting session concurrency and isolation issues.
- **Cost optimization is a recurring theme.** The heartbeat model override (#4549) and isolated session config (#4551), both open since June, indicate users are running always-on agents and feeling the token cost. There is strong latent demand for these features.
- **Remote WebUI usage is growing.** PRs #5673 (remote project paths) and #5652 (signed webhooks) suggest users are deploying Nanobot as a remote service accessed via browser, driving needs around path handling and secure external integrations.
- **MCP integration maturing.** Two MCP-related PRs (#5386, #5573) show users are integrating Nanobot with external tool ecosystems and hitting OAuth/credentials management pain points.

## 8. Backlog Watch

| PR | Open Since | Priority | Blocker | Risk |
|---|---|---|---|---|
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) — heartbeat model override | Jun 26 (72 days) | P2 | conflict | High user demand, cost-sensitive deployments blocked |
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) — heartbeat isolated session | Jun 26 (72 days) | P2 | conflict | Paired with #4549; both stalled |
| [#5561](https://github.com/HKUDS/nanobot/pull/5561) — per-spawn model presets | Aug 27 (40 days) | P2 | conflict | Alternative design accepted; awaiting conflict resolution |
| [#5589](https://github.com/HKUDS/nanobot/pull/5589) — stop discarded sessions reviving | Aug 28 (39 days) | P1 | conflict | **Security/correctness gap** — should be prioritized |
| [#5633](https://github.com/HKUDS/nanobot/pull/5633) — session path-traversal fix | Sep 2 (34 days) | P1 | conflict | **Security vulnerability** still unmerged |
| [#5457](https://github.com/HKUDS/nanobot/pull/5457) — dispatcher exception boundary | Aug 20 (47 days) | P2 | conflict | Reliability risk for production deployments |

**Recommended maintainer focus:** The two P1 bugs (#5589 and #5633) have been open for 34–39 days with "conflict" flags but are critical for security and correctness. Resolving these conflicts should be the immediate priority. The heartbeat features (#4549, #4551) have been stalled for 72 days and represent significant user value if unblocked.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026‑09‑06

## 1. Today’s Overview
Hermes Agent shows **high daily activity** with 50 issues and 50 pull requests updated in the last 24 hours, but only 2 issues and 2 PRs were closed/merged, indicating a **large open backlog**. No new releases were published today. The project is actively addressing stability and security concerns (notably HTTP‑response leaks and authentication regressions) while community demand grows for session‑database flexibility and cross‑platform update reliability.

## 2. Releases
*No new releases were published on this date.*

## 3. Project Progress
- **Merged/Closed PRs (2):** Details not visible in the provided top‑20 list; likely include routine fixes.
- **Notable Open PRs Advancing:**
  - **#104022** – First‑class macOS LaunchAgent lifecycle management for the dashboard (`feat(cli)`).
  - **#103965** – Per‑task Hermes‑profile routing for delegated subagents (`feat(delegate)`).
  - **#72200** – Compact skills‑catalog mode to reduce system‑prompt size (`feat(prompt)`).
  - **#103582** – Fix launchd‑managed gateways being incorrectly reported offline (`fix(gateway)`).
  - **#80583** – Propagate `connect_timeout` into MCP OAuth handshake (`fix(cli/mcp)`).
  - **Multiple HTTP‑leak fixes** (#104037, #104035, #104034, #104033, #104024) close unclosed `requests.get()` / `urllib.request.urlopen()` responses across plugins, agents, and evals.

## 4. Community Hot Topics
Issues with the highest comment volume reveal sustained community focus on **reliability, session continuity, and update hygiene**:

| Issue | Comments | Summary |
|-------|----------|---------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 163 | Skills‑index freshness probe fails; index 29.8 h old (limit 26 h). |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 23 | Bot group‑chat sessions should survive Desktop close; foundation on `main`, remaining work needed. |
| [#23717](https://github.com/NousResearch/hermes-agent/issues/23717) | 20 | RFC for pluggable SessionDB providers (PostgreSQL, MySQL) to avoid SQLite hot‑update conflicts. |
| [#26058](https://github.com/NousResearch/hermes-agent/issues/26058) | 10 | `auto_thread` disabled for `free_response_channels` breaks legitimate Discord use cases. |
| [#98022](https://github.com/NousResearch/hermes-agent/issues/98022) | 10 | `hermes update` catch‑up fleet restart loops endlessly when `update_receipts/latest.json` is stale. |

**Underlying needs:** Users demand **persistent cross‑platform sessions**, **reliable skill‑index updates**, and **safe concurrent update paths** that do not corrupt state.

## 5. Bugs & Stability
Ranked by severity (P1 > P2 > P3), focusing on bugs reported or updated today:

**P1**
- [#26058](https://github.com/NousResearch/hermes-agent/issues/26058) – Discord `auto_thread` breaks for `free_response_channels`. *(Related commit: d557544)*
- [#98022](https://github.com/NousResearch/hermes-agent/issues/98022) – Fleet‑restart loop on stale update receipt.
- [#103974](https://github.com/NousResearch/hermes-agent/issues/103974) – Kanban worker identity derived from env presence, not lineage; security boundary risk.
- [#103989](https://github.com/NousResearch/hermes-agent/issues/103989) – `hermes auth add openai-codex --type oauth` prints “Added” but credential never persists.
- [#103978](https://github.com/NousResearch/hermes-agent/issues/103978) – Claude Code OAuth auto‑discovery logs out CLI and conflicts with Anthropic ToS; requests opt‑out.

**P2**
- [#23717](https://github.com/NousResearch/hermes-agent/issues/23717) – RFC for pluggable SessionDB (tracking issue).
- [#94375](https://github.com/NousResearch/hermes-agent/issues/94375) – `npm audit fix` breaks after `hermes doctor` reports vulnerabilities.
- [#90495](https://github.com/NousResearch/hermes-agent/issues/90495) – ZIP‑fallback update deletes packaged Desktop and forgets Desktop was installed.
- [#103900](https://github.com/NousResearch/hermes-agent/issues/103900) – Pinned sessions in Desktop are local‑only; diverge from native Hermes.
- [#90782](https://github.com/NousResearch/hermes-agent/issues/90782) – Terminal env snapshot leaks `HERMES_DELEGATED_CHILD_CONTEXT`, breaks `kanban` CLI.
- [#97394](https://github.com/NousResearch/hermes-agent/issues/97394) – Windows update watchdog cancels healthy updates because `logs/update.log` is never created.
- [#91212](https://github.com/NousResearch/hermes-agent/issues/91212) – Root‑owned file `.gateway‑planned‑stop.json` created under `~/.hermes/` on non‑root installs.
- [#82912](https://github.com/NousResearch/hermes-agent/issues/82912) – Cron jobs with `enabled_toolsets: ["web","file"]` silently lose the `web` toolset.
- [#80594](https://github.com/NousResearch/hermes-agent/pull/80594) – Agent tool‑call argument validation and single‑element array unwrap (open PR).
- [#103582](https://github.com/NousResearch/hermes-agent/pull/103582) – Stop launchd gateways from being reported offline (open PR).
- [#75679](https://github.com/NousResearch/hermes-agent/pull/75679) – Normalize builtin memory‑provider aliases for doctor and runtime (open PR).
- [#104036](https://github.com/NousResearch/hermes-agent/pull/104036) – Expired AWS credentials on Bedrock now classified as auth, not unknown (open PR).

**P3**
- [#94375](https://github.com/NousResearch/hermes-agent/issues/94375) – npm audit breaks after doctor reports vulnerabilities.
- [#79664](https://github.com/NousResearch/hermes-agent/issues/79664) – Vite config uses features unsupported by `configLoader: 'native'`.
- [#83673](https://github.com/NousResearch/hermes-agent/issues/83673) – More than half of Python packages in venv are outdated (including `certifi`).
- [#103900](https://github.com/NousResearch/hermes-agent/issues/103900) – Desktop pinned sessions diverge from native Hermes.
- [#103985](https://github.com/NousResearch/hermes-agent/issues/103985) – “Hide from sidebar” on worktree lane is a silent no‑op.
- [#103893](https://github.com/NousResearch/hermes-agent/issues/103893) – Group‑chat hold directive misclassifies German filler words.

**Fix PRs available:** Many P2/P3 bugs have open PRs (see §3) that address the root causes (HTTP leaks, gateway offline detection, memory‑provider aliasing, credential classification).

## 6. Feature Requests & Roadmap Signals
| Request | Issue / PR | Likelihood for Next Release |
|---------|------------|-----------------------------|
| Bot group chats survive Desktop close | [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | Medium – foundation on `main`, remaining integration work. |
| Pluggable SessionDB (PostgreSQL, MySQL) | [#23717](https://github.com/NousResearch/hermes-agent/issues/23717) | Low‑Medium – RFC stage, needs decision. |
| Official way to deliver message to live session | [#103748](https://github.com/NousResearch/hermes-agent/issues/103748) | Low – niche multi‑agent workflow. |
| Plan mode (read‑only exploration before edits) | [#80994](https://github.com/NousResearch/hermes-agent/issues/80994) | Low – advisory skills already exist; hard to enforce. |
| macOS LaunchAgent lifecycle for dashboard | [#44106](https://github.com/NousResearch/hermes-agent/issues/44106) + PR [#104022](https://github.com/NousResearch/hermes-agent/pull/104022) | **High** – PR ready, directly addresses documented gap. |
| Per‑task Hermes‑profile routing for delegates | [#103965](https://github.com/NousResearch/hermes-agent/pull/103965) | **High** – PR open, solves multi‑persona delegation pain point. |
| Compact skills‑catalog mode | [#72200](https://github.com/NousResearch/hermes-agent/pull/72200) | **High** – PR open, reduces system‑prompt size. |
| Run `npm‑check` & `npm outdated` before release | [#102563](https://github.com/NousResearch/hermes-agent/issues/102563) | Medium – process improvement, not user‑facing feature. |

**Prediction:** The next release will likely include **LaunchAgent lifecycle**, **per‑task profile routing**, and **skills‑catalog compaction**, along with the batch of HTTP‑leak fixes.

## 7. User Feedback Summary
**Pain points:**
- **Update process is fragile:** ZIP fallback deletes Desktop assets, fleet‑restart loops on stale receipts, root‑owned files break future updates, and `npm audit fix` can leave insecure packages.
- **Authentication regressions:** OAuth flows sometimes fail to persist credentials (#103989) and can conflict with provider‑specific ToS (#103978).
- **Session persistence across platforms:** Pinned sessions in Desktop do not sync to native Hermes (#103900); group‑chat sessions break when the client closes (#97681).
- **Environment leakage:** Terminal snapshots leak `HERMES_DELEGATED_CHILD_CONTEXT`, causing `kanban` CLI to misbehave in parent sessions (#90782).
- **Windows‑specific watchdog:** Healthy updates are cancelled because the progress‑signal file is never created (#97394).
- **Skill index staleness:** Automated freshness probe fails frequently, leaving the Skills Hub outdated (#66616).
- **Dependency hygiene:** Over half of the Python packages in the venv are outdated from install (#83673); npm dependencies also lag.

**Satisfaction signals:** Users actively engage with RFCs and feature requests (high comment counts) and appreciate when bug‑fix PRs land (e.g., HTTP‑leak closures). However, the volume of open bugs and the recurrence of update‑related issues suggest **dissatisfaction with release stability**.

## 8. Backlog Watch
Issues that have been open for an extended period with high engagement and need maintainer attention:

- **#66616** – Skills‑index freshness probe (163 comments, open since 2026‑07‑18). *Risk: degraded user experience with stale skills.*
- **#23717** – RFC for pluggable SessionDB (20 comments, open since 2026‑05

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-06

## 1. Today's Overview

PicoClaw showed moderate activity on 2026-09-06 with 2 updated issues and 3 merged pull requests, though no new releases were published. The project remains in a maintenance-heavy phase, with the most recent work focused on consolidating earlier fix PRs rather than shipping new features. Community engagement is steady, with an open feature request around IRC long-message handling generating 10 comments, suggesting sustained interest in IRC protocol robustness. No critical bugs or regressions were reported today, and overall project health appears stable with no blocking issues.

## 2. Releases

No new releases were published in the last 24 hours.

## 3. Project Progress

Three PRs were merged today, all serving as consolidation merges for previously opened fix branches:

- **[PR #1559](https://github.com/sipeed/picoclaw/pull/1559)** — Merged fixes from PRs #1327, #1319, #1318, #1313 (author: xuwei-xy)
- **[PR #1545](https://github.com/sipeed/picoclaw/pull/1545)** — Merged fixes from PRs #1500, #1490, #1488, #1487, #1485 (author: xuwei-xy)
- **[PR #1555](https://github.com/sipeed/picoclaw/pull/1555)** — Merged fixes from PRs #1390, #1389, #1383, #1381 (author: xuwei-xy)

These merged PRs represent accumulated bug fixes and small improvements that were likely stalled in review. The consolidation pattern suggests the maintainer is working through a backlog of smaller contributions rather than developing new features. No new capabilities or architectural changes were introduced today.

## 4. Community Hot Topics

- **[Issue #3287](https://github.com/sipeed/picoclaw/issues/3287)** — *Better support long messages in IRC* (10 comments, open since 2026-07-22)
  - The most discussed open issue on the project. Users need PicoClaw to correctly handle IRCv3 multi-message transfer or message-length extension capabilities, treating split messages as a single cohesive unit rather than fragmenting the AI's response. With 10 comments and no resolution after ~45 days, this signals a genuine pain point for IRC-integrated deployments.
- **[Issue #3342](https://github.com/sipeed/picoclaw/issues/3342)** — *Opt-in "after-turn" steering mode* (2 comments, closed as stale on 2026-09-05)
  - Proposed a queue-based approach to handle user messages that arrive mid-turn, rather than interrupting the current agent execution. Though closed as stale, the underlying use case — smooth multi-turn interaction without disruptive preemption — is likely to resurface.

## 5. Bugs & Stability

No new bugs, crashes, or regressions were reported today. The three merged PRs (#1545, #1555, #1559) are fix-oriented and likely addressed prior bug reports, but the specific issues resolved are not itemized in the merge summaries. Users should monitor the linked source PRs (#1327, #1319, #1318, #1313, #1500, #1490, #1488, #1487, #1485, #1390, #1389, #1383, #1381) for details on what was corrected.

| Severity | Status | Item |
|----------|--------|------|
| Unknown | Fixed (merged) | Multiple fixes via PR #1559 |
| Unknown | Fixed (merged) | Multiple fixes via PR #1545 |
| Unknown | Fixed (merged) | Multiple fixes via PR #1555 |
| Unknown | Open | Issue #3287 — IRC long message handling |

## 6. Feature Requests & Roadmap Signals

- **[Issue #3287](https://github.com/sipeed/picoclaw/issues/3287)** — IRC long-message support is the most prominent open feature request. The depth of discussion (10 comments) indicates strong community demand. If PicoClaw plans to strengthen its IRC integration, this is the highest-priority signal.
- **[Issue #3342](https://github.com/sipeed/picoclaw/issues/3342)** — Though closed as stale, the "after-turn" steering mode concept addresses a real UX gap in multi-turn agent interactions. A future implementation with a queue-based message model could replace the current interrupt-driven behavior.

**Prediction:** If a next release ships, IRC protocol hardening (Issue #3287) is the most likely feature to be included, given its community traction and the project's evident focus on IRC integration.

## 7. User Feedback Summary

- **IRC message handling is a recurring pain point.** Issue #3287's 10 comments show users are actively struggling with messages that exceed IRC's 512-byte limit, which get split by clients and then misinterpreted by PicoClaw as separate messages. This degrades conversational coherence in IRC-based deployments.
- **Mid-turn message interruption frustrates users.** Issue #3342 reveals that the current steering model — skipping remaining tool calls when a new message arrives — is perceived as disruptive. Users want a smoother, queue-based interaction model.
- **Maintenance pace is acceptable but slow.** The reliance on bulk merge PRs suggests contributors have been submitting fixes that sit in review for extended periods. Users appear satisfied with eventual resolution but may grow impatient with the delay.

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| [Issue #3287](https://github.com/sipeed/picoclaw/issues/3287) — IRC long message support | ~45 days open, 10 comments | **Medium** — Active community interest; no maintainer response in recent days |
| [Issue #3342](https://github.com/sipeed/picoclaw/issues/3342) — After-turn steering mode | Closed as stale | **Low** — Concept not implemented, but the stale closure signals low immediate priority |

**Recommendation:** Issue #3287 warrants maintainer attention. The IRC long-message problem affects a concrete user workflow and has sustained discussion. A minimal viable fix — parsing and reassembling IRCv3 multi-messages before passing them to the agent — could resolve significant user frustration with relatively low effort.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-06

---

## 1. Today's Overview

NanoClaw saw **no new issues and no merged PRs** in the last 24 hours, indicating a relatively quiet maintenance cycle. Three open pull requests were updated, none yet merged, covering signal-client pinning, test-cleanup hygiene, and a retired-model-id fix in documentation. With zero new releases and no closed issues, the project appears to be in a low-velocity integration window — contributors are actively improving PRs but maintainers have not yet reviewed or landed them.

---

## 2. Releases

No new releases were published in the last 24 hours. The project has no recent tagged version to report changes against.

---

## 3. Project Progress

**No PRs merged or issues closed today.** The three open PRs represent incremental quality improvements rather than feature advances:

- **#3725** — Pins `signal-cli` to version 0.14.7 on Linux to prevent a session-handling hang.
- **#3710** — Cleans up ~355 leftover temp directories created by `pnpm test`, addressing a CI/dev-box accumulation problem.
- **#3724** — Corrects a retired Anthropic model ID in the `add-opencode` skill documentation.

These are maintenance and correctness fixes; no new features advanced today.

🔗 [PR #3725](https://github.com/nanocoai/nanoclaw/pull/3725) | [PR #3710](https://github.com/nanocoai/nanoclaw/pull/3710) | [PR #3724](https://github.com/nanocoai/nanoclaw/pull/3724)

---

## 4. Community Hot Topics

The most discussed items today are the three open PRs, none of which have reactions or comments yet:

| PR | Topic | Area |
|---|---|---|
| [#3725](https://github.com/nanocoai/nanoclaw/pull/3725) | signal-cli hang on Linux installs | `channels`, `setup-installation` |
| [#3710](https://github.com/nanocoai/nanoclaw/pull/3710) | Test suite temp-dir cleanup | `containers`, `ncl-cli`, `setup` |
| [#3724](https://github.com/nanocoai/nanoclaw/pull/3724) | Retired model ID in docs | `providers`, `skills` |

**Underlying needs:**
- **Reliability of Signal integration** (#3725) — Users hitting the 0.14.3 hang likely ran into silent failures during messaging, a high-pain issue for anyone relying on Signal as a channel.
- **Developer experience / CI hygiene** (#3710) — The 355-directory leak suggests the test suite isn't sandboxed cleanly; this frustrates local developers and CI runners on tmpfs-backed systems.
- **Skill documentation freshness** (#3724) — Retired model IDs cause confusing errors when users follow walkthroughs, eroding trust in the examples.

---

## 5. Bugs & Stability

No bugs or crashes were reported via issues today. However, two PRs address known defects:

| Severity | Issue | Fix PR |
|---|---|---|
| 🔴 High | `signal-cli` 0.14.3 hangs indefinitely when sending to contacts with no existing session | [#3725](https://github.com/nanocoai/nanoclaw/pull/3725) |
| 🟡 Medium | `pnpm test` leaves ~355 orphaned temp directories per run | [#3710](https://github.com/nanocoai/nanoclaw/pull/3710) |

The signal-cli hang is the most impactful bug — it silently breaks message delivery without error feedback. The temp-dir leak is a lower-severity but cumulative stability concern, especially on constrained CI environments.

---

## 6. Feature Requests & Roadmap Signals

No new feature requests were filed today. The PRs that do exist lean toward **stability and correctness** rather than new capabilities:

- **Upgrading signal-cli** (#3725) signals that the project may be evaluating broader channel robustness improvements — a future version could include a full Signal channel rewrite or expanded integration testing.
- **Test suite hardening** (#3710) suggests an ongoing effort to improve CI reliability, which often precedes larger architectural changes.

**Prediction:** The next release is likely to focus on foundational stability (Signal, test infrastructure, provider docs) rather than shipping new skills or channels.

---

## 7. User Feedback Summary

No new user issues were raised today, but the open PRs reflect pain points voiced by the community:

- **Signal hangs silently** — Users are frustrated by non-terse failures when messaging contacts without an established session, a critical path for Signal-channel users.
- **Test pollution** — Developers on persistent boxes and CI runners report accumulation of orphaned temp files, which wastes disk and obscures test outputs.
- **Stale examples** — Following documentation that references retired model IDs leads to confusing runtime errors, reducing confidence in onboarding guides.

Overall sentiment appears to be **neutral-to-positive**: the project is responsive to bugs (PRs are filed and detailed), but the slow merge cadence may be testing contributor patience.

---

## 8. Backlog Watch

All three open PRs are **freshly updated today** and have not yet received maintainer review (0 comments, 0 reactions). Given the absence of any closed issues or merged PRs in the 24-hour window, there is no long-standing backlog item flagging today — but the **review latency on these PRs warrants monitoring**. If these remain open beyond a week, it could signal maintainer bandwidth constraints.

| PR | Age | Status |
|---|---|---|
| [#3710](https://github.com/nanocoai/nanoclaw/pull/3710) | 3 days | Awaiting review |
| [#3724](https://github.com/nanocoai/nanoclaw/pull/3724) | 1 day | Awaiting review |
| [#3725](https://github.com/nanocoai/nanoclaw/pull/3725) | 1 day | Awaiting review |

---

**Project Health Verdict:** 🟡 *Stable but slow.* No critical outages, active community contributions, but zero merges today suggest a potential review bottleneck. Prioritize triaging the three open PRs — especially #3725, which addresses a high-severity runtime bug.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-06

## 1. Today's Overview

Activity on IronClaw remains low today, with only 1 open issue and 1 open PR updated in the last 24 hours and no new releases. The project shows signs of a steady but unhurried development pace, with work concentrated on sandbox configuration and a minor paired-user messaging bug. No merged or closed items were recorded, suggesting the team is in a deliberation phase rather than a sprint-closure window. Overall project health appears stable — nothing is broken publicly beyond a known cosmetic/copy issue, and no regressions have surfaced.

---

## 2. Releases

**No new releases** were published today. The latest shipped version remains unchanged, with no breaking changes or migration notes to report.

---

## 3. Project Progress

**No PRs were merged or closed today.** The sole open PR (#8075) advances the embedded Pi sandbox startup default but remains unmerged due to its dependency on PR #7908 and the `feat/7903-native-loop-sandbox-spike` base branch. This stacking pattern indicates the team is managing sandbox-related features as a coordinated batch rather than shipping incrementally.

---

## 4. Community Hot Topics

| Item | Type | Engagement |
|------|------|------------|
| [#8074](https://github.com/nearai/ironclaw/issues/8074) — Paired user rejected-action copy mismatch | Issue | 1 comment, 0 👍 |
| [#8075](https://github.com/nearai/ironclaw/pull/8075) — Pi sandbox loop startup default | PR | 0 comments, 0 👍 |

**Analysis:** The most discussed item today is Issue #8074, which surfaces a real user-pain point around inconsistent messaging for paired users in disconnected shared channels. The fact that it already has a comment suggests community or maintainer engagement. PR #8075 is internally driven (core contributor, stacked), indicating roadmap work that hasn't yet drawn external attention.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **Low** | [#8074](https://github.com/nearai/ironclaw/issues/8074) | Paired users in non-connected shared channels see the wrong `connect_required` notice copy — the unpaired-actor message is shown instead of the paired-actor variant. | None yet |

No crashes, data-loss bugs, or regressions were reported today. Issue #8074 is a UI/copy bug with no functional impact beyond user confusion, so it is unlikely to block the next release.

---

## 6. Feature Requests & Roadmap Signals

- **[#8075](https://github.com/nearai/ironclaw/pull/8075)** — Make the embedded Pi sandbox loop the startup default for fresh installs. This is explicitly requested for benchmark use, signaling that IronClaw is preparing tooling and configuration for repeatable performance evaluation. Expect this to ship in the next release once the stacked PRs (#7908, #7903) land.

No other user-facing feature requests were raised today.

---

## 7. User Feedback Summary

The primary user feedback today centers on **message clarity for paired users** in shared channels. The current copy assumes the user is unpaired, which creates confusion and friction when a paired user encounters a non-connected channel. This is a classic onboarding/UX consistency gap — the product recognizes pairing status in code but fails to reflect it in user-facing text. No broader dissatisfaction signals were detected.

---

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#8075](https://github.com/nearai/ironclaw/pull/8075) | Open ~1 day | Stacked on two prior PRs; risk of delay if base branches stall |
| [#8074](https://github.com/nearai/ironclaw/issues/8074) | Open ~2 days | Copy bug with no fix PR yet; low severity but affects paired-user experience |

The main backlog risk is the **dependency chain around #8075** — if #7908 or the base branch encounters blockers, the sandbox-default feature will remain stuck. The copy bug (#8074) is small and should be addressable without blocking any release.

---

*Data sources: [nearai/ironclaw Issues](https://github.com/nearai/ironclaw/issues), [nearai/ironclaw PRs](https://github.com/nearai/ironclaw/pulls)*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-09-06

---

## 1. Today's Overview

LobsterAI activity on 2026-09-06 was minimal, with no new releases, issues, or merged/closed pull requests within the last 24 hours. Two open PRs were recently updated (as of 2026-09-05), both still in review and flagged as stale, indicating they have languished since their creation on 2026-03-30. No bugs or regressions were reported today. Overall, the project appears to be in a low-activity maintenance phase with no urgent stability concerns, though the prolonged stale status of pending PRs warrants attention from maintainers.

---

## 2. Releases

**No new releases** were published during this reporting period.

---

## 3. Project Progress

**No PRs were merged or closed today.** The two most recent PRs remain open and stale:

- **[PR #1069](https://github.com/netease-youdao/LobsterAI/pull/1069)** — Refactoring: Split `CoworkSessionDetail` monolith into smaller, maintainable modules. This is a significant code-organization effort targeting a 2100+ line component that suffers from mixed responsibilities, unnecessary re-renders during streaming, and untestable logic.
- **[PR #1070](https://github.com/netease-youdao/LobsterAI/pull/1070)** — Feature: Per-session MCP server toggle control, allowing users to independently enable/disable MCP servers per conversation with state persisted to the database.

Both PRs were created on 2026-03-30 and last updated on 2026-09-05 — roughly **5 months** of inactivity — suggesting a significant backlog in review throughput.

---

## 4. Community Hot Topics

| PR/Issue | Title | Activity | Link |
|---|---|---|---|
| PR #1069 | Refactor: Split CoworkSessionDetail | 0 👍, stale | [#1069](https://github.com/netease-youdao/LobsterAI/pull/1069) |
| PR #1070 | Per-session MCP switch control | 0 👍, stale | [#1070](https://github.com/netease-youdao/LobsterAI/pull/1070) |

**Analysis:** Neither PR has garnered community reactions, which may reflect a small active user base or low engagement on long-open PRs. The two most prominent items reflect distinct community needs:

1. **PR #1069** addresses a developer-experience pain point — the `CoworkSessionDetail` component has become unmaintainable. This signals that the project has grown organically without sufficient architectural discipline, and the community (or contributors) is pushing for sustainable code organization.
2. **PR #1070** responds to a clear user need for ** granular MCP control ** — users want per-session tool integrations rather than global toggle-only behavior, a common pattern in professional agent workflows.

---

## 5. Bugs & Stability

**No bugs, crashes, or regressions were reported today.** Zero issues were opened or closed in the last 24 hours, suggesting no immediate stability incidents. However, the absence of recent issue activity may also indicate low community reporting engagement rather than perfect stability.

---

## 6. Feature Requests & Roadmap Signals

- **Per-session MCP configuration (PR #1070):** Users have a demonstrated need for fine-grained control over MCP server availability on a per-conversation basis. This is a strong roadmap signal that the agent's tool-integration layer should support session-scoped configuration, not just global settings.
- **Component architecture improvement (PR #1069):** While not a user-facing feature, the refactoring effort indicates that the project is approaching a complexity threshold where monolithic components are hindering development velocity. Future roadmap items may include broader modularization efforts.

**Prediction:** If PR #1070 is merged, the next release is likely to highlight per-session MCP toggles as a new capability. PR #1069, being internal refactoring, may not appear in release notes but will improve long-term maintainability.

---

## 7. User Feedback Summary

No new user feedback was recorded today. Based on the open PRs, the most salient user pain points identified by contributors are:

| Pain Point | Source |
|---|---|
| MCP servers cannot be toggled per-session; global-only control limits workflow flexibility | [PR #1070](https://github.com/netease-youdao/LobsterAI/pull/1070) |
| `CoworkSessionDetail` is 2100+ lines, causing performance issues during streaming and making maintenance difficult | [PR #1069](https://github.com/netease-youdao/LobsterAI/pull/1069) |

No satisfaction/dissatisfaction metrics are available from today's data. The stale PRs may indirectly signal frustration with slow review cycles.

---

## 8. Backlog Watch

The following items require maintainer attention due to extended inactivity:

| PR | Created | Last Updated | Age | Status | Link |
|---|---|---|---|---|---|
| #1069 | 2026-03-30 | 2026-09-05 | ~5 months | 🟡 Stale | [#1069](https://github.com/netease-youdao/LobsterAI/pull/1069) |
| #1070 | 2026-03-30 | 2026-09-05 | ~5 months | 🟡 Stale | [#1070](https://github.com/netease-youdao/LobsterAI/pull/1070) |

**Recommendation:** Both PRs carry the `[stale]` label and have seen no maintainer engagement for approximately five months. PR #1070 (per-session MCP control) has clear user value and should be prioritized for review or closure. PR #1069 (refactoring) is important for long-term health but lower urgency. Maintainer action on these items would significantly improve community confidence and project momentum.

---

*Data source: LobsterAI GitHub repository (github.com/netease-youdao/LobsterAI), reported on 2026-09-06.*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# 📋 CoPaw (QwenPaw) Project Digest — 2026-09-06

## 1. Today's Overview

CoPaw remains in active development around the **2.2.0 release cycle**, with strong community engagement (11 issues + 7 PRs updated in the last 24 hours). The project is addressing several **quality-of-life bugs** (409 conflicts, swallowed exceptions, hardcoded context sizes) while simultaneously advancing **multi-tenant architecture** (QwenPaw Hub) and **new interaction modes** (Advisor Mode). No new releases were published today. Overall project health is **healthy and responsive** — most bug reports have corresponding open fix PRs, and the contributor base is expanding (multiple first-time contributors active).

---

## 2. Releases

**No new releases published today.** The project is preparing for the **2.2.0** launch, with the multi-tenant QwenPaw Hub edition being a centerpiece (see #7318).

---

## 3. Project Progress

### Merged / Closed Today
| Issue/PR | Status | Summary |
|---|---|---|
| [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | ✅ Closed | Custom provider loading failure after `max_tokens` → `max_output_length` migration (PR #7337) |
| [#7574](https://github.com/agentscope-ai/QwenPaw/issues/7574) | ✅ Closed | `img-gen` skill omitting `model` field, causing HTTP 503 fallback to dall-e-2 |
| [#7575](https://github.com/agentscope-ai/QwenPaw/issues/7575) | ✅ Closed | `img-gen` skill `edit()` always sending `response_format`, causing HTTP 400 |

### Open PRs Advancing
- **[PR #7509](https://github.com/agentscope-ai/QwenPaw/pull/7509)** — *feat(skill): Update make-skill to v2* — Approval-driven draft-then-publish workflow for Skills. **Ready for Merge.**
- **[PR #7569](https://github.com/agentscope-ai/QwenPaw/pull/7569)** — *feat(modes): add Advisor Mode* — Pairs a stronger advisor model with a cheaper worker agent per conversation.
- **[PR #6874](https://github.com/agentscope-ai/QwenPaw/pull/6874)** — *feat(mcp): add configurable tool call timeout* — Adds `tool_call_timeout` (default 300s). **Under Review.**

---

## 4. Community Hot Topics

### 🔥 Most Active Issue
**[#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318)** — *QwenPaw Hub multi-tenant edition: what should we build next?*
- **23 comments · 3 👍** · Updated 2026-09-05
- Community is driving demand for **team/multi-user support**. This discussion directly references prior requests (#2324) and signals that **multi-tenancy is a top roadmap priority** for 2.2.0.

### Other Notable Discussions
- **[PR #7546](https://github.com/agentscope-ai/QwenPaw/pull/7546)** — Lazy-loading builtin channel modules (e.g., `lark_oapi`) to cut startup time. First-time contributor; addresses a recurring performance complaint.
- **[PR #7547](https://github.com/agentscope-ai/QwenPaw/pull/7547)** — Fixing stuck session queue consumers in Feishu channels, another first-time contributor fix for a real operational issue.

---

## 5. Bugs & Stability

| Severity | Issue | PR Fix | Description |
|---|---|---|---|
| 🔴 **High** | [#7572](https://github.com/agentscope-ai/QwenPaw/issues/7572) | [PR #7578](https://github.com/agentscope-ai/QwenPaw/pull/7578) | Tool dispatch `_drain()` swallows exception stacks — only `str(exc)` returned to model, no `logger.exception()`. Operators cannot debug failures. |
| 🔴 **High** | [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | — | `RetryChatModel` hardcodes 32768 context_size fallback, causing `CONTEXT_UNFIT` errors for all models with >31130 tokens. Confirmed buggy across v2.1.0–v2.2.0. |
| 🟡 **Medium** | [#7559](https://github.com/agentscope-ai/QwenPaw/issues/7559) | [PR #7577](https://github.com/agentscope-ai/QwenPaw/pull/7577) | Sending a new message during task execution returns **HTTP 409** instead of queuing the message. |
| 🟡 **Medium** | [#7571](https://github.com/agentscope-ai/QwenPaw/issues/7571) | — | Agent "forgetfulness" — persistent instructions (e.g., output path rules) are not retained across sessions despite repeated emphasis. |
| 🟢 **Low** | [#7570](https://github.com/agentscope-ai/QwenPaw/issues/7570) | — | Feishu streaming card: thinking-process output should auto-collapse after completion to avoid pushing the final reply off-screen. |

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Likelihood for 2.2.0 |
|---|---|---|
| **QwenPaw Hub (multi-tenant)** | [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | ✅ **Confirmed** — explicitly announced for 2.2.0 |
| **Edit-last-message / Rewind in Web UI** | [#7573](https://github.com/agentscope-ai/QwenPaw/issues/7573) | 🟡 Moderate — small UI enhancement, plausible |
| **Advisor Mode (dual-model per task)** | [PR #7569](https://github.com/agentscope-ai/QwenPaw/pull/7569) | 🟡 Moderate — feature-complete PR, needs review |
| **Skill versioning & dependency metadata** | [#7557](https://github.com/agentscope-ai/QwenPaw/issues/7557) | 🟡 Moderate — useful for fleet management |
| **Configurable MCP tool-call timeout** | [PR #6874](https://github.com/agentscope-ai/QwenPaw/pull/6874) | 🟡 Moderate — long-open PR (since Aug 10), under review |
| **Feishu card auto-collapse** | [#7570](https://github.com/agentscope-ai/QwenPaw/issues/7570) | 🟢 Low — niche, user has local patch |
| **Make-Skill v2** | [PR #7509](https://github.com/agentscope-ai/QwenPaw/pull/7509) | ✅ High — **Ready for Merge** |

---

## 7. User Feedback Summary

**Pain Points:**
- **409 conflicts on concurrent messages** — users expect follow-up messages to queue, not reject. ([#7559](https://github.com/agentscope-ai/QwenPaw/issues/7559), [PR #7577](https://github.com/agentscope-ai/QwenPaw/pull/7577))
- **Swallowed exceptions** in tool dispatch make debugging nearly impossible. ([#7572](https://github.com/agentscope-ai/QwenPaw/issues/7572))
- **Hardcoded context size** breaks models with larger windows. ([#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576))
- **Agent "memory" drift** — users report instructions being forgotten across sessions, suggesting gaps in prompt injection or context management. ([#7571](https://github.com/agentscope-ai/QwenPaw/issues/7571))
- **Slow startup** from eager import of unused channel SDKs (e.g., `lark_oapi`). ([PR #7546](https://github.com/agentscope-ai/QwenPaw/pull/7546))

**Satisfaction Signals:**
- Community actively participating in roadmap discussions (#7318 with 23 comments).
- First-time contributors are successfully submitting fixes (kabishou11 with 3 PRs).
- Bug fixes are being closed promptly (3 issues closed today).

---

## 8. Backlog Watch

| Item | Author | Days Open | Concern |
|---|---|---|---|
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) — Hardcoded context_size fallback | aimastertoast | 1 | 🔴 No fix PR yet; affects all models above ~31k tokens. Confirmed across v2.1.0–v2.2.0. |
| [#7571](https://github.com/agentscope-ai/QwenPaw/issues/7571) — Agent forgetfulness | xiaohushi512 | 1 | 🟡 Root cause unclear (possibly design limitation, not a code bug). Needs maintainer triage. |
| [#7557](https://github.com/agentscope-ai/QwenPaw/issues/7557) — Skill versioning/metadata | laob9444 | 2 | 🟡 No PR yet; important for multi-agent fleet management. |
| [PR #6874](https://github.com/agentscope-ai/QwenPaw/pull/6874) — MCP tool-call timeout | AaronZ345 | 27 | 🟡 Open since Aug 10, still "Under Review." Long backlog item. |

---

**Bottom Line:** CoPaw is in a productive pre-2.2.0 phase with strong bug-fix velocity and growing community contributions. The two most critical unresolved items are the **hardcoded context size** (#7576) and **exception swallowing** (#7572, fix PR exists but needs merge). The multi-tenant Hub roadmap (#7318) is the dominant strategic signal for the next release.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw Project Digest — 2026-09-06

## 1. Today's Overview
ZeptoClaw saw a highly concentrated activity cycle focused on security hardening and CI reliability. The project closed 4 issues and merged 3 PRs, with maintainers rapidly addressing P0 findings from a recent architecture review. Ten open issues remain, predominantly tracking architectural debt, configuration UX, and extensibility roadmap items. Overall project health is strong: critical attack surfaces were patched today while systemic debt is being explicitly cataloged for future sprints.

## 2. Releases
No new releases were published today.

## 3. Project Progress
**Merged PRs:**
- [#672](https://github.com/qhkm/zeptoclaw/pull/672) — Scrubs inherited environment variables at plugin and MCP spawn sites, complementing earlier runtime-level fixes.
- [#671](https://github.com/qhkm/zeptoclaw/pull/671) — Enforces fail-closed behavior on invalid `agent_mode` configurations.
- [#645](https://github.com/qhkm/zeptoclaw/pull/645) — Scrubs subprocess secrets and consistently reaps timed-out process trees in the native runtime.

**Closed Issues:**
- [#660](https://github.com/qhkm/zeptoclaw/issues/660), [#659](https://github.com/qhkm/zeptoclaw/issues/659), [#644](https://github.com/qhkm/zeptoclaw/issues/644), [#646](https://github.com/qhkm/zeptoclaw/issues/646)

These changes directly resolve the immediate security review findings and restore foundational quality gates (Clippy + cargo-deny) on the current toolchain.

## 4. Community Hot Topics
While comment and reaction counts are currently zero across the tracked items, the following issues are driving the current development cycle due to their criticality and architectural scope:
- [#661](https://github.com/qhkm/zeptoclaw/issues/661) Byte-stable Prompt Envelope contract — identifies the single largest prompt-cache performance gap.
- [#663](https://github.com/qhkm/zeptoclaw/issues/663) Finish Agent Pipeline migration — production still runs the legacy 5,227-line `AgentLoop` despite documented Phase 4a targets.
- [#665](https://github.com/qhkm/zeptoclaw/issues/665) Cron Job v2 — surfaces semantic gaps in success/failure tracking and operational control.
- [#660](https://github.com/qhkm/zeptoclaw/issues/660) & [#659](https://github.com/qhkm/zeptoclaw/issues/659) — Drove today’s merged security PRs and reflect strong demand for deterministic, fail-closed security postures.

## 5. Bugs & Stability
All high-severity items resolved today were security-related rather than runtime crashes:
1. **P0/Critical** — Inherited credential leakage across plugin/MCP/runtime spawn sites → Fixed in [#672](https://github.com/qhkm/zeptoclaw/pull/672) and [#645](https://github.com/qhkm/zeptoclaw/pull/645).
2. **P0/Critical** — Invalid `agent_mode` strings falling back to `Autonomous` (max permissions) → Fixed in [#671](https://github.com/qhkm/zeptoclaw/pull/671).
3. **P1-Critical** — CI baseline failures from new Clippy warnings and vulnerable dependencies (`quick-xml`, `lopdf`) → Resolved in [#646](https://github.com/qhkm/zeptoclaw/pull/646).

No new stability regressions or crash reports were logged today.

## 6. Feature Requests & Roadmap Signals
Open issues reveal a deliberate shift toward architectural maturity and security-first extensibility:
- [#669](https://github.com/qhkm/zeptoclaw/issues/669) Persist and rotate audit-chain segments across restarts
- [#666](https://github.com/qhkm/zeptoclaw/issues/666) Durable cross-session recall and transactional memory writes
- [#667](https://github.com/qhkm/zeptoclaw/issues/667) Footprint Ladder + registry-owned extension metadata (Extension Host v2)
- [#670](https://github.com/qhkm/zeptoclaw/issues/670) Config source opacity — effective-view, env-var deprecation, schema-backed get/set

The next release cadence will likely prioritize configuration UX transparency and audit-chain persistence, followed by incremental work on the agent pipeline migration and cron v2 semantics.

## 7. User Feedback Summary
Recent activity reflects strong auditor/user demand for enterprise-grade security guarantees, particularly around credential isolation and deterministic permission boundaries. Pain points center on configuration discoverability, prompt-cache inefficiencies, and the opacity of inherited subprocess environments. Trust is being reinforced through rapid P0 resolution, though the volume of architectural backlog indicates users expect slower but steadier delivery on extensibility, memory durability, and scheduling reliability.

## 8. Backlog Watch
- **Stale Dependabot updates (open since June 2026):** [#617](https://github.com/qhkm/zeptoclaw/pull/617) tower-http, [#620](https://github.com/qhkm/zeptoclaw/pull/620) scraper, [#623](https://github.com/qhkm/zeptoclaw/pull/623) tokio, [#625](https://github.com/qhkm/zeptoclaw/pull/625) rpassword, [#627](https://github.com/qhkm/zeptoclaw/pull/627) serde_json. Prolonged dependency lag may require triage to prevent future security or compatibility debt.
- **Architectural debt:** Issues [#661–670](https://github.com/qhkm/zeptoclaw/issues/661) remain open and require sustained engineering effort beyond immediate security hotfixes. Maintainer attention is needed to sequence these into upcoming milestones.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-09-06

## 1. Today's Overview

ZeroClaw is in an active stabilization and security-hardening phase surrounding the **v0.8.5** release, which shipped today as a major 454-commit, 73-contributor effort focused on ZeroRelay, ZeroRouter, live-chat expansion, and tightened sandbox/credential/file boundaries. The project is running hot: **42 issues and 50 PRs** touched in the last 24 hours, with 8 issues closed and 6 PRs merged/closed today. A cluster of high-risk security and config bugs surfaced within days of the v0.8.5 release, indicating a stabilization wave where latent issues are being exercised by real deployments. Community governance (RFC process) remains a dominant activity track alongside production work.

---

## 2. Releases

### v0.8.5 (released today)
- **Scope:** Security, connectivity, and operator-experience release.
- **Key additions:** ZeroRelay and ZeroRouter; expanded live-chat and provider capabilities; hardened plugin, sandbox, webhook, credential, and file boundaries.
- **Contributors:** 73 | **Commits:** 454
- **Migration notes:** No explicit migration notes in the release summary; however, several open RFCs (#9487, #9488) propose material architectural changes to conversation sessions and file/attachment handling that may affect future upgrades. The v0.8.5 stabilization tracker (#9459) indicates the weekly cutship model through August 30 — post-release bug remediation is now the active track.
- **Tracker:** [#9459](https://github.com/zeroclaw-labs/zeroclaw/issues/9459)

---

## 3. Project Progress

### Merged / Closed PRs (today)
| PR | Summary |
|---|---|
| [#10350](https://github.com/zeroclaw-labs/zeroclaw/pull/10350) | Added measurement-only Windows test jobs (advisory, not yet gated) — CI infrastructure progress |
| [#10435](https://github.com/zeroclaw-labs/zeroclaw/pull/10435) | Fixed Gemini provider context preservation when anchoring requests |
| [#10064](https://github.com/zeroclaw-labs/zeroclaw/pull/10064) | Telegram approval cards now self-destruct after operator tap |
| [#10005](https://github.com/zeroclaw-labs/zeroclaw/pull/10005) | Fixed channel health reporting — was based on listener liveness, now channel-true |
| [#5230](https://github.com/zeroclaw-labs/zeroclaw/pull/5230) | WASM plugin system with security sandbox (historic feature, completed) |
| [#10048](https://github.com/zeroclaw-labs/zeroclaw/pull/10048) | Validated Rust 1.98.0 across CI, demo, and cross-platform build lanes |

### In-Flight PRs Receiving Attention
- [#10241](https://github.com/zeroclaw-labs/zeroclaw/pull/10241) — Restores supervised shell approval routing for channel-driven calls (blocked)
- [#10391](https://github.com/zeroclaw-labs/zeroclaw/pull/10391) — Bounded delegates now respect target agent's own workspace (XL)
- [#10016](https://github.com/zeroclaw-labs/zeroclaw/pull/10016) — Webhook audit call correlation by opaque per-invocation identity
- [#9320](https://github.com/zeroclaw-labs/zeroclaw/pull/9320) — Cron jobs now bounded with wall-clock timeout
- [#10321](https://github.com/zeroclaw-labs/zeroclaw/pull/10321) — Browser PKCE + cross-surface enrollment (stacked, stage 5)
- [#10275](https://github.com/zeroclaw-labs/zeroclaw/pull/10275) — Retires Nevis/iam_policy with config shim (stacked, stage 6)
- [#10274](https://github.com/zeroclaw-labs/zeroclaw/pull/10274) — Route-layer auth with principal consumption (stacked)

---

## 4. Community Hot Topics

| Issue | Comments | Status | Topic |
|---|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 33 | RFC Rev 5 | Runtime-owned conversation sessions & transport adapters |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | 26 | RFC Rev 10 | Unified file/attachment architecture for conversation surfaces |
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) | 24 | RFC Ratified | Work lanes, board automation, label cleanup (rollout in progress) |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | 24 | RFC in-progress | Granular sandbox filesystem policy |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | 15 | Tracker | Maintainer decision queue for RFCs |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) | 14 | RFC accepted | Verbatim channel send via gateway without agent turn |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) | 13 | RFC accepted | WASM plugin lifecycle observer subscriptions |
| [#9975](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) | 13 | RFC accepted | Web bundle/daemon `web_dist_dir` compatibility |

**Analysis:** The top hot topics reveal two concurrent themes: (1) **architecture evolution** — session ownership, file/attachment unification, and WASM plugin observers are all maturing into substantial RFCs with heavy discussion, suggesting the community is actively shaping ZeroClaw's next-gen extensibility model. (2) **governance infrastructure** — work-lane automation (#6808) and the maintainer decision queue (#8692) show the project is professionalizing its triage process, likely a response to the growing issue volume (42 open in 24h). The verbatim-send RFC (#10050) indicates operator demand for gateway-level message primitives independent of agent reasoning.

---

## 5. Bugs & Stability

| Issue | Severity | Summary | Fix PR |
|---|---|---|---|
| [#10536](https://github.com/zeroclaw-labs/zeroclaw/issues/10536) | **S1 — workflow blocked** | macOS Seatbelt ignores configured `allowed_roots` for shell commands | — |
| [#10534](https://github.com/zeroclaw-labs/zeroclaw/issues/10534) | **P1 / high risk** | Bounded delegates silently strip the `delegate` tool, contradicting config | [#10391](https://github.com/zeroclaw-labs/zeroclaw/pull/10391) (in review) |
| [#10533](https://github.com/zeroclaw-labs/zeroclaw/issues/10533) | **P1 / high risk** | `model_routing_config` rejects valid `custom.*` provider slots | — |
| [#10625](https://github.com/zeroclaw-labs/zeroclaw/issues/10625) | S2 — degraded | Non-vision models receive literal `[media attachment]` placeholder | — |
| [#10532](https://github.com/zeroclaw-labs/zeroclaw/issues/10532) | S2 — degraded | Degraded-config remediation may invoke a different binary than the running daemon | — |
| [#10626](https://github.com/zeroclaw-labs/zeroclaw/issues/10626) | S2 — degraded | TTS synthesizes markdown and emoji verbatim (spoken aloud) | — |
| [#10585](https://github.com/zeroclaw-labs/zeroclaw/issues/10585) | S3 — minor | Log-sink regression races migration tests under parallel runner | — |
| [#10045](https://github.com/zeroclaw-labs/zeroclaw/issues/10045) | S2 — degraded | Persisted image markers retain temporary source paths | Closed (fix in progress) |
| [#10282](https://github.com/zeroclaw-labs/zeroclaw/issues/10282) | S2 — degraded | Hardware probe feature doesn't reach tool implementations | Closed (fix in progress) |

**Stability Assessment:** The S1 Seatbelt regression (#10536) is the most concerning — it directly undermines the security hardening that v0.8.5 intended to deliver. The delegation tool-stripping bug (#10534) contradicts an explicitly configured policy and is a high-risk correctness issue. A fix PR exists for delegation (#10391) but is still open. The `model_routing_config` validation divergence (#10533) suggests a schema-tool gap that could block advanced provider routing setups.

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Type | Description | Likelihood for Next Release |
|---|---|---|---|
| [#10530](https://github.com/zeroclaw-labs/zeroclaw/issues/10530) | Feature | Pass Anthropic extended-thinking params through OpenAI-compatible providers (gateway passthrough) | **High** — small, targeted, addresses a real deployment gap |
| [#10641](https://github.com/zeroclaw-labs/zeroclaw/issues/10641) | Feature | Per-field cron schedule input with validation in web UI | **Medium** — UX enhancement, no backend changes |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) | RFC | Verbatim channel send over gateway without agent turn | **Medium** — RFC accepted, but scope is non-trivial |
| [#10356](https://github.com/zeroclaw-labs/zeroclaw/pull/10356) | Feature | AnySearch web search provider | **Low-Medium** — blocked, needs-maintainer-review |
| [#9997](https://github.com/zeroclaw-labs/zeroclaw/pull/9997) | Feature | Secure model picker for Telegram | **Medium** — blocked, size XL |
| [#10526](https://github.com/zeroclaw-labs/zeroclaw/issues/10526) | RFC | Append-only session event history, deterministic state replay | **Future** — foundational architecture, not imminent |
| [#10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) | RFC | Composable WASM plugin runtime architecture | **Future** — major architectural shift |

**Signal:** The extended-thinking passthrough (#10530) and cron UI improvement (#10641) are the most likely candidates for a v0.8.6 patch, given their limited scope and clear user demand. The WASM composable runtime (#10076) and append-only event history (#10526) are clearly v0.9+ roadmap items.

---

## 7. User Feedback Summary

**Pain Points:**
- **Sandbox misconfiguration on macOS** (#10536): Users configuring `allowed_roots` for shell commands encounter `Operation not permitted`, blocking legitimate workflows. This is especially painful for security-conscious deployments that rely on Seatbelt.
- **Delegation tool stripping** (#10534): Bounded delegates lose the `delegate` tool regardless of policy config, silently breaking multi-agent chains that users explicitly configured.
- **TTS reading markup** (#10626): Text with markdown and emoji is spoken verbatim — a frustrating UX issue for voice-channel deployments.
- **Media placeholder leakage** (#10625): Non-vision models surface `[media attachment]` literally to end users instead of gracefully degrading.
- **Custom provider slot rejection** (#10533): The `model_routing_config` tool rejects `custom.*` provider references that are valid in the config schema, creating a tool-schema divergence that blocks advanced routing setups.
- **Android/Termux install** (#7911, closed): The installer selects a generic Linux binary instead of an Android-compatible one — resolved but signals mobile/edge deployment gaps.

**Satisfaction Signals:**
- Telegram approval card self-destruct (#10064) and health check fixes (#10005) show responsiveness to operator-experience concerns.
- The community is actively engaging with RFCs (33+ comments on session architecture) indicating strong ownership of project direction.

---

## 8. Backlog Watch

| Issue / PR | Age | Priority | Why It Needs Attention |
|---|---|---|---|
| [#10536](https://github.com/zeroclaw-labs/zeroclaw/issues/10536) | Created 2026-09-02 | P1 / S1 | macOS Seatbelt bug directly undermines v0.8.5 security hardening; no fix PR yet |
| [#10534](https://github.com/zeroclaw-labs/zeroclaw/issues/10534) | Created 2026-09-02 | P1 / high risk | Delegation tool stripping contradicts explicit config; fix PR #10391 is in review but not yet merged |
| [#10533](https://github.com/zeroclaw-labs/zeroclaw/issues/10533) | Created 2026-09-02 | P1 / high risk | Tool-schema divergence blocks `custom.*` provider routing; no fix PR |
| [#10241](https://github.com/zeroclaw-labs/zeroclaw/pull/10241) | Created 2026-08-22 | Blocked / high risk | Supervised shell approval routing — blocks a key operator-experience flow; status: blocked |
| [#9997](https://github.com/zeroclaw-labs/zeroclaw/pull/9997) | Created 2026-08-14 | Blocked / XL | Telegram secure model picker — 3+ weeks in review, blocked |
| [#10356](https://github.com/zeroclaw-labs/zeroclaw/pull/10356) | Created 2026-08-25 | Blocked / needs-maintainer-review | AnySearch provider — 2+ weeks, blocked |
| [#8966](https://github

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*