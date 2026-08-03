# OpenClaw Ecosystem Digest 2026-08-03

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-03 03:35 UTC

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



# OpenClaw Project Digest — 2026-08-03

## 1. Today's Overview

OpenClaw is experiencing high daily activity with 500 issues and 500 PRs updated in the last 24 hours (449 open issues, 367 open PRs). The latest beta release v2026.7.2-beta.7 shipped with significant state-safety and crash-recovery improvements. The project shows strong maintainer engagement with 51 issues closed and 133 PRs merged/closed today, though the open-issue backlog remains substantial at ~449 active items.

## 2. Releases

**v2026.7.2-beta.7** — State safety and recovery enhancements:
- **Quarantine store** protects persisted data against primary database damage
- **Crash-recoverable SQLite snapshots** for state durability
- **Crash-durable filesystem publication** ensures on-disk writes survive unexpected termination
- **Schema-upgrade data-loss rejection** prevents accidental destructive migrations
- **Rollback-writer snapshot recovery** enables safe downgrades after failed migrations

> Migration note: See also [Issue #115421](https://github.com/openclaw/openclaw/issues/115421) — schema downgrade recovery must not quarantine/wipe the state DB (cron jobs lost), currently open.

## 3. Project Progress

**Closed/Merged today:**
- [#118064](https://github.com/openclaw/openclaw/pull/118064) — `fix(line)`: skip invalid location messages before delivery
- [#117697](https://github.com/openclaw/openclaw/pull/117697) — `fix(whatsapp)`: preserve source direction for automatic reactions
- [#118323](https://github.com/openclaw/openclaw/pull/118323) — `refactor(opencode)`: consolidate session catalog test fixtures

**Key open PRs advancing features:**
- [#118360](https://github.com/openclaw/openclaw/pull/118360) — *Make subagent completion delivery durable and recoverable* (P1, XL size, closes #112616)
- [#118296](https://github.com/openclaw/openclaw/pull/118296) — *Prevent internal subagent completion events from leaking into chats* (P1, XL, mantis-visible proof)
- [#113567](https://github.com/openclaw/openclaw/pull/113567) — *Snapshot state DB before forward schema migration* (P2, L)
- [#118067](https://github.com/openclaw/openclaw/pull/118067) — *feat(discord): support private provider endpoints* (P2, L)
- [#101665](https://github.com/openclaw/openclaw/pull/101665) — *feat: let plugin tools yield turns* (P2, L)

## 4. Community Hot Topics

| Rank | Issue | Comments | Rating | Status |
|------|-------|----------|--------|--------|
| 1 | [#116277](https://github.com/openclaw/openclaw/issues/116277) — DeepSeek v4 Flash silent reply failure | 87 | 🦞 diamond lobster | ✅ Closed |
| 2 | [#116201](https://github.com/openclaw/openclaw/issues/116201) — Realtime voice retains unbounded provider state | 51 | 🦞 diamond lobster | Open |
| 3 | [#115326](https://github.com/openclaw/openclaw/issues/115326) — Crash-loop breaker suppresses Discord/WhatsApp permanently | 26 | 🦞 diamond lobster | ✅ Closed |
| 4 | [#91009](https://github.com/openclaw/openclaw/issues/91009) — Codex PreToolUse hook spawns CPU-bound processes | 19 | 🐚 platinum hermit | Open |
| 5 | [#48003](https://github.com/openclaw/openclaw/issues/48003) — Steer mode does not inject messages mid-turn | 16 | 🐚 platinum hermit | Open |

**Analysis:** The #1 issue (DeepSeek silent failure) having 87 comments and a closed status indicates a high-visibility model integration problem that received extensive community debugging. Realtime voice resource management (#116201) and crash-loop recovery (#115326) reflect growing production usage where reliability and resource bounds are critical. The steer-mode injection issue (#48003) and Codex CPU leak (#91009) point to ongoing subagent/session architecture pain points.

## 5. Bugs & Stability

**P0 / Critical:**
- [#117956](https://github.com/openclaw/openclaw/issues/117956) — `claude-cli` produced **metered API usage despite env scrubbing** (~13.7M tokens billed). Auth boundary regression. 🔒 Security
- [#115421](https://github.com/openclaw/openclaw/issues/115421) — Schema downgrade recovery **wiped state DB**, losing cron jobs. Directly relevant to v2026.7.2-beta.7 release.

**P1 High:**
- [#114234](https://github.com/openclaw/openclaw/issues/114234) — Usage-cost refresh lock **never releasable** after restart (container PID reuse). Permanently freezes cache.
- [#67777](https://github.com/openclaw/openclaw/issues/67777) — Subagent completion **delivery can be lost** on direct-announce timeout, drain, or orphan prune. PR [#118360](https://github.com/openclaw/openclaw/pull/118360) targets this.
- [#92433](https://github.com/openclaw/openclaw/issues/92433) — Subagent completion **silently dropped** when announce steers into a requester run that ends before processing.
- [#106231](https://github.com/openclaw/openclaw/issues/106231) — Loop detection blocks exec but **does not terminate** the stuck agent run (resources burn for hours).
- [#111498](https://github.com/openclaw/openclaw/issues/111498) — Main agent **blocked by persistent workspace-state migration** after Anthropic auth recovery (regression).
- [#109017](https://github.com/openclaw/openclaw/issues/109017) — Anthropic provider **disappears from model picker**; models list crashes on manually-added models; static catalog never pulls new models (Fable 5 / Haiku 4.5).
- [#116010](https://github.com/openclaw/openclaw/issues/116010) — All persistent sessions **capped at 128k context** regardless of model or `contextTokens` config.
- [#53408](https://github.com/openclaw/openclaw/issues/53408) — Write/exec tool parameters **silently dropped** after long conversations (content/command missing).
- [#52249](https://github.com/openclaw/openclaw/issues/52249) — ACP parent session **stuck until refresh** when yielded waiting for child completion.

**P2 Medium:**
- [#57901](https://github.com/openclaw/openclaw/issues/57901) — Safeguard compaction **ignores `compaction.model`** config, uses session model instead.
- [#74586](https://github.com/openclaw/openclaw/issues/74586) — AM embedded run **aborts `memory_search` tool calls**, classifies as timeout despite model completion.
- [#115001](https://github.com/openclaw/openclaw/issues/115001) — Hybrid memory search returns **spurious 1.0 similarity scores** via FTS LIKE-fallback.

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Priority |
|-------|---------|----------|
| [#113251](https://github.com/openclaw/openclaw/issues/113251) | Image viewing in webchat file viewer | P2 |
| [#52640](https://github.com/openclaw/openclaw/issues/52640) | Persistent task-status surface for long-running channel turns | P2 |
| [#50093](https://github.com/openclaw/openclaw/issues/50093) | WhatsApp backfill missed messages after reconnection | P2 |
| [#50291](https://github.com/openclaw/openclaw/issues/50291) | Missing trace context (messageId, runId, parentSpanId) in plugin hooks | P2 |
| [#71195](https://github.com/openclaw/openclaw/issues/71195) | OpenAI Realtime (speech-to-speech) path for Talk Mode on macOS | P2 |
| [#71142](https://github.com/openclaw/openclaw/issues/71142) | Configurable upload size limit for Control UI (currently 5MB hardcoded) | P2 |
| [#71058](https://github.com/openclaw/openclaw/issues/71058) | Multiple Azure/Teams bots on a single OpenClaw gateway | P2 |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | Expose resolved backend model in session_status and agent runtime | P2 |
| [#51028](https://github.com/openclaw/openclaw/issues/51028) | Sessions panel: sort by last meaningful activity | P3 |

**Prediction:** Several of these — particularly WhatsApp message backfill (#50093), task-status surfaces (#52640), and controlled UI upload limits (#71142) — align with the project's current stability focus and are likely candidates for inclusion in the next stable release. The OpenAI Realtime path for Talk Mode (#71195) has strong community interest and would bring parity with the voice-call plugin.

## 7. User Feedback Summary

**Major pain points observed:**
- **Message loss** remains the top complaint across channels (Telegram, WhatsApp, Feishu, Discord), with multiple issues reporting silent delivery failures and post-reconnection gaps
- **Subagent/session lifecycle bugs** are pervasive — completions lost, sessions persisting after completion, parent sessions stuck, and completion events leaking into chats
- **Auth/provider reliability** issues (Anthropic auth recovery blocking migrations, provider disappearance from model picker, metered usage despite key scrubbing) are causing production billing surprises
- **Tool parameter loss** after long conversations (#53408) and CPU-bound process leaks from hooks (#91009) indicate state management fragility under sustained use
- **Container/deployment environments** (k3s, Docker) introduce unique connectivity and PID-reuse bugs that need better support
- **Multi-channel group chat context handling** (#56692) causes agents to respond to messages not directed at them

**Positive signals:** The DeepSeek silent failure issue (#116277) was resolved with 87 comments of community debugging, and the crash-loop breaker issue (#115326) was closed — showing the team responds to high-impact problems.

## 8. Backlog Watch

**Stale/long-open P1 items needing maintainer attention:**

- [#91009](https://github.com/openclaw/openclaw/issues/91009) — Codex PreToolUse hook CPU leak (open since June 6, 19 comments, `clawsweeper-recovery-stuck`)
- [#48003](https://github.com/openclaw/openclaw/issues/48003) — Steer mode mid-turn injection (open since March 16, 16 comments, 4 👍)
- [#52249](https://github.com/openclaw/openclaw/issues/52249) — ACP parent session stuck on child completion (open since March 22, 10 comments)
- [#54488](https://github.com/openclaw/openclaw/issues/54488) — Session lane starvation: followup drain monopolizes lane for 20–30 min (open since March 25, 7 comments)
- [#86540](https://github.com/openclaw/openclaw/pull/86540) — Preserve subagent delivery after lock stalls (open since May 25, needs proof)
- [#50291](https://github.com/openclaw/openclaw/issues/50291) — Missing trace context in plugin hooks (open since March 19, 10 comments)

**Recently stuck:**
- [#116022](https://github.com/openclaw/openclaw/issues/116022) — beta.5 `/new` reuses stable session ID, cannot recover retired Codex binding tombstone (open since July 29, `clawsweeper-recovery-stuck`)
- [#111498](https://github.com/openclaw/openclaw/issues/111498) — Workspace-state migration blocks main agent after Anthropic auth recovery (open since July 19, `clawsweeper-recovery-stuck`)

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Comparison Report
**Date:** 2026-08-03 | **Scope:** 9 Active Projects (2 Inactive, 1 Low-Activity)

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape is in a high-velocity consolidation phase. Projects are converging on shared challenges—subagent lifecycle reliability, cross-channel message delivery, provider compatibility, and production-grade security—while diverging sharply in architecture philosophy and target deployment models. The ecosystem spans from monolithic desktop agents (OpenClaw, ZeroClaw) to modular gateway platforms (Hermes, NanoBot) and embedded/IoT-adjacent runners (PicoClaw, Moltis). Community-driven contributions now account for a significant share of merged PRs across all active projects, indicating maturation beyond maintainer-only development.

---

## 2. Activity Comparison

| Project | Open Issues | Open PRs | Merged Today | Release Status | Health Score |
|---|---|---|---|---|---|
| **OpenClaw** | ~449 | 367 | 133 PRs merged | v2026.7.2-beta.7 (active) | 🟡 Strained — high volume, large backlog |
| **ZeroClaw** | ~50+ | ~50 | Multiple closed today | v0.8.4 (recent, 262 commits / 49 contributors) | 🟢 Strong — active hardening post-release |
| **IronClaw** | ~8 new today | ~6 open PRs | 3 merged today | Stalled — release PR #5598 open 31 days | 🟡 Moderate — QA-burdened, architectural debt |
| **Hermes Agent** | ~50 | ~50 | 13 merged today | v0.19.0 (Jul 20, no new release) | 🟡 Active but Windows Desktop fragility |
| **NanoBot** | ~15 | ~15 | 9 merged today | None today | 🟢 Healthy — fast turnaround, responsive |
| **CoPaw (QwenPaw)** | ~13 today | ~28 today | 3 closed today | v2.0.1 (stabilizing post-upgrade) | 🟡 Post-release churn — 2.0.4.post1 regressions |
| **PicoClaw** | ~3 | ~9 | 3 merged today | None today | 🟢 Steady — small but focused |
| **NanoClaw** | ~3 | ~10 | 3 merged today | None today | 🟢 Moderate — Docker/SQLite pain points |
| **LobsterAI** | ~3 | ~6 | 2 merged today | None recently | 🟡 Stale backlog — 4+ month open PRs |
| **Moltis** | 0 | 1 | 0 | None today | 🟡 Quiet — feature pause, no bugs reported |
| **NullClaw** | — | — | — | No activity | ⚪ Dormant |
| **ZeptoClaw** | — | — | — | No activity | ⚪ Dormant |

*Health scores reflect today's activity velocity, bug-fix turnaround, and backlog management. Not a long-term trajectory assessment.*

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Largest and most active community** by orders of magnitude (~449 open issues, 367 open PRs, 500 daily events). This signals both scale and complexity.
- **Deepest state-safety investment** — the v2026.7.2-beta.7 release introduced quarantine stores, crash-recoverable SQLite snapshots, schema-upgrade data-loss rejection, and rollback-writer recovery. No other project matches this level of durability engineering.
- **Multi-channel breadth** — WhatsApp, Discord, Telegram, Feishu, and more, with active fixes for channel-specific reliability (silent reply failures, crash-loop breakers, delivery durability).

**Technical approach differences:**
- OpenClaw favors a **monolithic session+subagent architecture** with explicit lifecycle management (steer mode, subagent completion delivery, lane starvation). This creates depth but also produces the most complex failure modes (subagent completion loss, parent-session blocking, schema downgrade wipes).
- Projects like **NanoBot** and **Hermes** take a **gateway/plugin model** with clearer modularity; **PicoClaw** targets embedded/resource-constrained environments; **ZeroClaw** emphasizes RFC-driven governance and security hardening.
- OpenClaw's **200k+ context session cap** and subagent architecture create unique debugging surface area that smaller projects avoid entirely.

**Community size comparison:**
- OpenClaw (~449 open issues) dwarfs all others combined. ZeroClaw (~50) and Hermes (~50) are mid-tier. NanoBot (~15), PicoClaw (~3), NanoClaw (~3), LobsterAI (~3) are smaller. CoPaw sits in between (~13 issues, 28 PRs).

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Message/delivery reliability** | OpenClaw, NanoBot, Hermes, ZeroClaw, CoPaw | Silent delivery failures, post-reconnection gaps, subagent completion loss, webhook fail-closed enforcement |
| **Subagent/session lifecycle** | OpenClaw, NanoBot, CoPaw | Completions lost on timeout/drain, parent sessions stuck waiting for children, orphan gateways on restart |
| **Provider compatibility & fallback** | NanoBot, OpenClaw, Hermes, CoPaw | API serde failures, silent 400 errors, model picker crashes, responses-api vs. chat-completions fallback |
| **Auth/security hardening** | OpenClaw, ZeroClaw, IronClaw, PicoClaw | Metered usage despite env scrubbing, unauthenticated webhook dispatch, DNS-rebinding bypass, remote exec boundaries |
| **Cross-channel context handling** | OpenClaw, Hermes, ZeroClaw | Multi-channel group chat message routing, DM routing collision in multiplexed profiles, thread context hydration |
| **Docker/container deployment** | NanoClaw, Hermes, PicoClaw | SQLite lock contention on VirtioFS mounts, arm64 image architecture mismatch, PID-reuse bugs, MSSQL/MSRV pin divergence |
| **Windows Desktop experience** | Hermes, NanoBot, OpenClaw | Frontend MIME type failures, duplicate UI elements, update loops, orphan processes |
| **Cost/usage observability** | OpenClaw, Hermes, IronClaw | Metered API usage despite key scrubbing, missing cost dashboard in Desktop, model budget enforcement gaps |
| **CLI/documentation correctness** | ZeroClaw, PicoClaw | Broken CLI help examples, schema migration notes missing, config format changes undocumented |

---

## 5. Differentiation Analysis

| Project | Feature Focus | Target User | Architecture |
|---|---|---|---|
| **OpenClaw** | State durability, subagent orchestration, multi-channel | Power users, production deployments | Monolithic sessions, explicit lifecycle, SQLite-backed |
| **ZeroClaw** | Security hardening, RFC governance, channel reliability | Enterprise, security-conscious operators | RFC-driven, pluggable auth, compact skill injection |
| **Hermes Agent** | Desktop UX, gateway multiplexing, cost analytics | Desktop-first users, multi-platform operators | Profile-isolated workers, desktop app + gateway split |
| **NanoBot** | Runtime-gated goals, RTK command rewriting, session ergonomics | Workflow automation, team/operational use | Gateway + plugin, explicit goal lifecycle |
| **IronClaw** | Durable delivery, MCP OAuth, budget enforcement | Production infrastructure, reliability-critical | Coordinator-based, atomic state transitions |
| **CoPaw (QwenPaw)** | Multi-agent collaboration, provider discovery, AgentScope integration | Chinese-market users, Qwen ecosystem | AgentScope 2.x dependent, creator module |
| **PicoClaw** | Security boundaries, embedded deployment, shell allow-lists | Resource-constrained / edge deployments | Lightweight, guard-command focused |
| **NanoClaw** | Channel expansion (Dial/SMS/voice), remote MCP | Distributed agent deployments | Channel adapter pattern, SQLite with WAL concerns |
| **LobsterAI** | IM integration (DingTalk, Popo, Telegram), cowork sessions | Chinese enterprise, collaborative workflows | IM-centric, React frontend |
| **Moltis** | MCP server management via Git bundles | MCP ecosystem builders | Git-bundle lifecycle, vault integration |

**Key architectural divides:**
- **Monolithic vs. modular:** OpenClaw and ZeroClaw are monolithic sessions; Hermes and NanoBot split gateway/desktop; Moltis is purely MCP-orchestration.
- **Governance model:** ZeroClaw uses formal RFCs with a maintainer decision queue; others operate on issue/PR triage without published governance.
- **Deployment target:** PicoClaw targets embedded; CoPaw targets Qwen/AgentScope users; IronClaw targets production infrastructure with budget controls.

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (high velocity, active contributor base):**
- **OpenClaw:** 500 daily events, 133 PRs merged/day. Scale creates both momentum and backlog risk.
- **ZeroClaw:** 49 contributors in v0.8.4, active RFC process, security hardening sprint.
- **Hermes Agent:** 13 merged PRs today, strong contributor diversity, Desktop polish track.

**Tier 2 — Healthy & Responsive (steady output, good turnaround):**
- **NanoBot:** 9 PRs merged today, fast bugfix turnaround, responsive to Windows/provider issues.
- **CoPaw:** 41 items updated today, active stabilization post-2.0.4.post1 regression.
- **NanoClaw:** 3 merged today, focused on channel expansion and Docker reliability.

**Tier 3 — Stabilizing or Quieter (maintenance mode, low issue volume):**
- **PicoClaw:** 12 updates today, small but focused; security hardening and tool-loop fixes.
- **IronClaw:** 31 PRs updated but release stalled 31 days; QA audit surfacing production bugs.
- **LobsterAI:** Moderate activity but 4+ month stale PRs; needs maintainer engagement.

**Tier 4 — Dormant:**
- **NullClaw, ZeptoClaw:** No activity in 24 hours.
- **Moltis:** Low activity, single PR, no bugs reported — likely pre-community-testing phase.

---

## 7. Trend Signals

**1. Subagent/session reliability is the #1 cross-cutting concern.**
Every major project reports subagent completion loss, orphan processes, or parent-session blocking. The ecosystem lacks a shared abstraction for durable agent-to-agent communication. *Value for developers:* Investing in delivery guarantees (SCTP-style acks, journaling, single-flight ownership) differentiates production readiness.

**2. Provider compatibility fragility is accelerating.**
Silent 400 errors (NanoBot/Gemini), serde failures (NanoBot/OpenAI), model picker crashes (OpenClaw/Anthropic), and streaming marker leakage (ZeroClaw) all point to under-tested provider integration layers. *Value for developers:* Fallback chains and protocol-agnostic adapters (like NanoBot's chat-completions fallback) are becoming table stakes.

**3. Security hardening is moving from reactive to structural.**
ZeroClaw's fail-closed webhooks, OpenClaw's auth-boundary regression, IronClaw's DNS-rebinding bypass, and PicoClaw's remote-exec defaults all signal that early "convenience-first" designs are creating production security debt. *Value for developers:* Default-deny security postures and schema-versioned config migrations (PicoClaw's v4) are emerging best practices.

**4. Docker/container deployment is a persistent reliability gap.**
SQLite lock contention (NanoClaw/VirtioFS), arm64 image mismatches (Hermes), MSRV pin divergence (ZeroClaw), and PID-reuse bugs (OpenClaw) show that containerized deployments remain under-tested. *Value for developers:* WAL-mode defaults, multi-arch CI, and filesystem-aware fallbacks are differentiators.

**5. Cost visibility and budget enforcement are becoming enterprise requirements.**
OpenClaw's metered-usage- Despite-scrubbing bug, IronClaw's unenforced daily USD caps, and Hermes's Desktop cost analytics demand all signal that operators need spend controls. *Value for developers:* Built-in cost dashboards and hard budget enforcement are becoming expectation, not bonus.

**6. Windows Desktop experience remains a weakness across projects.**
Hermes (sidebar bugs, update loops, orphan gateways), NanoBot (MIME type failures), and LobsterAI (gateway restarts) all report Windows-specific issues. *Value for developers:* Cross-platform consistency, especially Windows, is an underserved differentiator.

**7. RFC-driven governance is emerging as a maturity signal.**
Only ZeroClaw has formalized RFCs with a maintainer decision queue, but the pattern (Chat Completions profile, pluggable auth, goal mode) reflects real community demand for transparent roadmap governance. *Value for developers:* Projects that adopt lightweight RFC processes may see higher contributor retention and better-aligned roadmaps.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-03

---

## 1. Today's Overview

NanoBot shows strong development velocity today, with **15 PRs updated** and **1 issue closed** in the last 24 hours. No new releases were published, but 9 PRs were merged or closed, indicating an active review and integration cycle. The project is resolving a cluster of Windows-specific web UI issues, provider-level fixes for Gemini and OpenAI APIs, and stability improvements around session management and gateway shutdown. Overall health is positive — high contributor engagement with a good mix of bug fixes and feature work landing simultaneously.

---

## 2. Releases

**None today.** No new versions were published. The most recent merged PRs suggest the team is actively addressing bugs and provider compatibility ahead of an upcoming release.

---

## 3. Project Progress

### Merged / Closed PRs (9)

| PR | Author | Summary |
|----|--------|---------|
| [#5191](https://github.com/HKUDS/nanobot/pull/5191) | amkile | **Fix:** Register correct MIME types for static assets on Windows — resolves the `text/plain` module load failure ([#5190](https://github.com/HKUDS/nanobot/issues/5190)) |
| [#5216](https://github.com/HKUDS/nanobot/pull/5216) | arcdrake22 | **Fix:** Send Gemini Flash image hints via `generationConfig.imageConfig` to resolve HTTP 400 errors on aspect ratio / image size requests |
| [#5217](https://github.com/HKUDS/nanobot/pull/5217) | chengyongru | **Fix:** Show timestamps for replayed messages in the WebUI, improving auditability of cron/proactive messages |
| [#4854](https://github.com/HKUDS/nanobot/pull/4854) | chengyongru | **Feature:** Add RTK command rewriter for `tools.exec`, running `rtk rewrite` before sandbox wrapping with noise filtering |
| [#4833](https://github.com/HKUDS/nanobot/pull/4833) | chengyongru | **Feature:** Gate sustained goals behind explicit runtime mode — replaces always-visible `long_task`/`complete_goal` with runtime-gated `create_goal`/`update_goal` |
| [#4822](https://github.com/HKUDS/nanobot/pull/4822) | chengyongru | **Fix:** Preserve automation source metadata on streamed WebUI replies so badges render correctly on session replay |
| [#5196](https://github.com/HKUDS/nanobot/pull/5196) | chengyongru | **Fix:** Recover refreshed Weixin session state after 60-minute pause post-`errcode -14` |
| [#5194](https://github.com/HKUDS/nanobot/pull/5194) | chengyongru | **Perf:** Accelerate JSONL session list and thread loading via scoped caching in the session-list index |
| [#4021](https://github.com/HKUDS/nanobot/pull/4021) | eldar702 | **Fix:** Deduplicate reasoning items before sending to OpenAI Responses API and retry on 400 duplicate-item errors |

**Key takeaways:** Significant progress on Windows web UI compatibility, provider stability (Gemini, OpenAI), session replay fidelity, and long-goal orchestration architecture. The RTK command rewriter and goal-gating features signal a push toward more robust agent runtime control.

---

## 4. Community Hot Topics

The most-discussed items today revolve around **provider compatibility** and **Windows web UI reliability** — both high-pain areas for the user base.

| Topic | Link | Analysis |
|-------|------|----------|
| Windows MIME type bug blocking frontend loads | [#5190](https://github.com/HKUDS/nanobot/issues/5190) / [#5191](https://github.com/HKUDS/nanobot/pull/5191) | A critical onboarding blocker for Windows users; the fix (registry-aware MIME registration) landed quickly, showing responsive maintenance |
| Gemini Flash image model errors | [#5216](https://github.com/HKUDS/nanobot/pull/5216) | Multiple Gemini image variants affected — users need reliable image generation and this was a silent data-loss bug (400 errors) |
| OpenAI Responses API serde failures | [#5214](https://github.com/HKUDS/nanobot/pull/5214) **[OPEN, P1]** | Conversations terminate on body deserialization errors; the proposed fallback to chat completions is a pragmatic resilience pattern |
| Cross-session search & mentions | [#5211](https://github.com/HKUDS/nanobot/pull/5211) **[OPEN]** | Enables `@mention` navigation between sessions — a quality-of-life feature users have likely requested implicitly via session-management friction |

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| **P1** | [#5214](https://github.com/HKUDS/nanobot/pull/5214) **[OPEN]** | OpenAI Responses API serde rejections cause terminal conversation failures | Fix PR open — fallback to chat completions |
| **P1** | [#5215](https://github.com/HKUDS/nanobot/pull/5215) **[OPEN]** | Gateway shutdown stalls with asyncio teardown noise when exec/MCP subprocesses are active | Fix PR open — deterministic resource cleanup |
| **P2** | [#5190](https://github.com/HKUDS/nanobot/issues/5190) | Windows frontend fails to load JS modules (MIME type `text/plain`) | ✅ Fixed in [#5191](https://github.com/HKUDS/nanobot/pull/5191) |
| **P2** | [#5216](https://github.com/HKUDS/nanobot/pull/5216) | Gemini Flash image models return HTTP 400 on aspect-ratio hints | ✅ Merged |
| **P2** | [#5196](https://github.com/HKUDS/nanobot/pull/5196) | Weixin channel stuck after session expiry / `errcode -14` | ✅ Merged |
| **P2** | [#5217](https://github.com/HKUDS/nanobot/pull/5217) | Replay messages lack timestamps in WebUI | ✅ Merged |
| **P2** | [#5152](https://github.com/HKUDS/nanobot/pull/5152) **[OPEN]** | Subagent partial completions not marked — model may infer false completeness | Fix PR open |
| **P2** | [#5213](https://github.com/HKUDS/nanobot/pull/5213) **[OPEN]** | Plugin installs fail when `pip` is unavailable (uv-only environments) | Fix PR open |

**Three P2 bug fixes remain open** and two P1 issues need maintainer review. The project has a healthy bug-turnaround rate — most reported issues received fix PRs within days.

---

## 6. Feature Requests & Roadmap Signals

| PR | Author | Feature | Likelihood for Next Release |
|----|--------|---------|----------------------------|
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) | Re-bin | Cross-session search & `@mention` navigation | **High** — scoped, read-only, well-tested; low risk |
| [#5212](https://github.com/HKUDS/nanobot/pull/5212) | octo-patch | MiniMax music generation guidance & tool contract | **Medium** — niche provider addition, needs maintainer triage |
| [#4854](https://github.com/HKUDS/nanobot/pull/4854) | chengyongru | RTK command rewriter for `tools.exec` | **High** — already merged; opt-in, behind feature flag |
| [#4833](https://github.com/HKUDS/nanobot/pull/4833) | chengyongru | Runtime-gated sustained goals | **High** — merged; represents a significant architecture shift in goal handling |

**Signal:** The roadmap is trending toward **better session ergonomics** (cross-session search, replay fidelity), **harder runtime guards** (goal gating, RTK rewriting), and **provider resilience** (fallback paths, deduplication). MiniMax music support suggests expanding media-generation coverage.

---

## 7. User Feedback Summary

- **Windows onboarding is painful.** The MIME type bug (#5190) blocked entire frontend loads — a first-run critical issue. Users on Windows Script Host environments are a distinct segment that needs continued attention.
- **Provider reliability is a top concern.** Multiple P1/P2 issues today touch Gemini, OpenAI, and Weixin providers. Users expect stable API integration; silent 400 errors and session expiry stalls erode trust quickly.
- **Session replay and auditability matter.** Timestamp fixes (#5217) and automation-source preservation (#4822) indicate users rely on NanoBot for logged, replayable workflows — likely in operational or team contexts.
- **Plugin ecosystem friction.** The `pip`-unavailable issue (#5213) affects users in modern Python environments (uv toolchains). This is a growing segment as `uv` adoption increases.
- **Overall satisfaction appears strong** given the rapid fix turnaround and the volume of merged PRs, but the concentration of provider bugs suggests integration testing coverage could be expanded.

---

## 8. Backlog Watch

| Item | Author | Priority | Risk | Notes |
|------|--------|----------|------|-------|
| [#5214](https://github.com/HKUDS/nanobot/pull/5214) — OpenAI Responses API fallback | arcdrake22 | **P1** | High | Terminal conversation failures; needs maintainer review to merge |
| [#5215](https://github.com/HKUDS/nanobot/pull/5215) — Gateway deterministic shutdown | arcdrake22 | **P1** | High | Asyncio teardown noise; blocks clean deployments |
| [#5211](https://github.com/HKUDS/nanobot/pull/5211) — Cross-session search | Re-bin | — | Medium | Large feature; needs triage on scope and review bandwidth |
| [#5152](https://github.com/HKUDS/nanobot/pull/5152) — Subagent partial completions | yu-xin-c | P2 | Medium | Correctness issue for multi-subagent workflows |
| [#5213](https://github.com/HKUDS/nanobot/pull/5213) — Plugin install with uv | KDB-Wind | P2 | Low | Narrow but growing environment segment |
| [#5212](https://github.com/HKUDS/nanobot/pull/5212) — MiniMax music guidance | octo-patch | P2 | Low | Documentation/guidance PR; low risk but needs review |

**Two P1 PRs are the most pressing items** awaiting maintainer action. The cross-session search feature (#5211) is the largest open PR and may benefit from early maintainer engagement to set expectations on merge timing.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-03

## 1. Today's Overview

Hermes Agent is showing **high development velocity** with 100 issue/PR events in the last 24 hours (50 issues, 50 PRs), signaling an active maintenance burst. The bulk of today's activity is concentrated on the **Desktop application** and **gateway platform integrations** (Telegram, WhatsApp, QQ), with a secondary focus on **cost/usage analytics** and **skill tooling**. No new releases were published today, but 13 PRs were merged or closed, indicating steady forward momentum. The project appears healthy with a strong ratio of open-to-closed activity, though several P0/P1 bugs remain unresolved.

## 2. Releases

**None.** No new versions were published today. The latest referenced version remains **v0.19.0** (2026.7.20, upstream 560800f3).

## 3. Project Progress

**Merged/Closed PRs (13 today):**

| PR | Author | Summary |
|----|--------|---------|
| [#75263](https://github.com/NousResearch/hermes-agent/pull/75263) | allenkaplan | `fix(secrets): hydrate cold multiplex sources locally` — resolves profile-isolated secret bootstrap for multiplexed gateways |
| [#77237](https://github.com/NousResearch/hermes-agent/pull/77237) | teknium1 | `fix(cli): persist YOLO mode across --resume` — YOLO bypass now survives process restart |
| [#77289](https://github.com/NousResearch/hermes-agent/pull/77289) | o269 | `fix(kanban): make boardd runtime restart-safe` — immutable release packaging with systemd unit |
| [#77255](https://github.com/NousResearch/hermes-agent/issues/77255) | dss539 | `fix: API server model split on single colon` — resolves Open WebUI 404s from `@provider:model` format |

**Key PRs advancing today (open):**

- **#77297** — Fix orphan gateway on Desktop backend shutdown (addresses #77276)
- **#77296** — Persist message reactions config in Desktop settings
- **#77285** — Rewrite xAI TTS streaming against real WebSocket protocol (fixes #73985)
- **#77298** — Add timeout to WhatsApp reconnect to prevent permanent disconnect wedge (#77268)
- **#77293** — Add `hermes desktop install` CLI subcommand with cross-platform shortcut creation
- **#77076** — Durable SMART busy-input orchestration across CLI, gateway, TUI, and Desktop

## 4. Community Hot Topics

| Issue/PR | Comments | Focus | Link |
|----------|----------|-------|------|
| [#71837](https://github.com/NousResearch/hermes-agent/issues/71837) | 6 | Duplicate branch lanes in Desktop sidebar on Windows | [Issue](https://github.com/NousResearch/hermes-agent/issues/71837) |
| [#69163](https://github.com/NousResearch/hermes-agent/issues/69163) | 6 | Coder gateway profile import fails to register | [Issue](https://github.com/NousResearch/hermes-agent/issues/69163) |
| [#73985](https://github.com/NousResearch/hermes-agent/issues/73985) | 4 | xAI streaming TTS produces no audio (4 stacked failures) | [Issue](https://github.com/NousResearch/hermes-agent/issues/73985) |
| [#73804](https://github.com/NousResearch/hermes-agent/issues/73804) | 4 | Cron serialization starvation of workdir jobs | [Issue](https://github.com/NousResearch/hermes-agent/issues/73804) |
| [#29530](https://github.com/NousResearch/hermes-agent/issues/29530) | 4 | Shared auth home for profiled workers | [Issue](https://github.com/NousResearch/hermes-agent/issues/29530) |

**Analysis:** The top-commented issues reveal two dominant community needs: **(1) Desktop UX stability on Windows** (sidebar rendering, session editing, update loops) and **(2) gateway reliability across platforms** (Telegram multiplexing, WhatsApp disconnects, Coder profile migration). The xAI TTS issue (#73985) with 4 independent failure modes suggests the provider integration was rushed and needs a ground-up rewrite — already addressed in PR #77285.

## 5. Bugs & Stability

### P0 (Critical)
| Issue | Description | Fix PR |
|-------|-------------|--------|
| [#77217](https://github.com/NousResearch/hermes-agent/issues/77217) | DeepSeek caching on OpenCode Zen breaks with HTTP 400 (`content must be string, not block array`) | — |

### P1 (High)
| Issue | Description | Fix PR |
|-------|-------------|--------|
| [#76870](https://github.com/NousResearch/hermes-agent/issues/76870) | Model switch mid-session triggers `history_version` mismatch — all subsequent output discarded | — |
| [#77268](https://github.com/NousResearch/hermes-agent/issues/77268) | WhatsApp bridge wedges permanently disconnected after reconnect version fetch hang | [#77298](https://github.com/NousResearch/hermes-agent/pull/77298) |
| [#77276](https://github.com/NousResearch/hermes-agent/issues/77276) | Desktop restart leaves orphan gateway (app-managed spawn path) | [#77297](https://github.com/NousResearch/hermes-agent/pull/77297) |
| [#77277](https://github.com/NousResearch/hermes-agent/issues/77277) | Desktop in-app update loops forever on Windows (respawning backend blocks install) | — |
| [#75756](https://github.com/NousResearch/hermes-agent/issues/75756) | Edit earlier message fails with "session not found" (rewind lacks resume+retry) | — |

### P2 (Medium)
| Issue | Description |
|-------|-------------|
| [#71837](https://github.com/NousResearch/hermes-agent/issues/71837) | Duplicate branch lanes in Desktop sidebar on Windows |
| [#77241](https://github.com/NousResearch/hermes-agent/issues/77241) | Desktop message reactions config never reaches backend (4002 unknown key) |
| [#74285](https://github.com/NousResearch/hermes-agent/issues/74285) | Multiplexed Telegram gateway routes DMs to sibling profile's session |
| [#62985](https://github.com/NousResearch/hermes-agent/issues/62985) | Kanban auto-decompose bypasses non-spawnable assignee containment |
| [#74554](https://github.com/NousResearch/hermes-agent/issues/74554) | `linux/arm64` Docker image ships x86_64 wheels — every command fails on ImportError |
| [#69163](https://github.com/NousResearch/hermes-agent/issues/69163) | Coder gateway profile import fails registration |
| [#73804](https://github.com/NousResearch/hermes-agent/issues/73804) | Cron workdir jobs silently starve on single-thread pool |

**Stability assessment:** 6 of 10+ open P1/P0 bugs lack associated fix PRs. The **Windows Desktop experience** is the weakest area, with at least 4 interrelated issues (sidebar lanes, update loops, orphan gateways, reaction config). The arm64 Docker image bug (#74554) is a distribution-quality issue that should be escalated.

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Description | Likelihood for Next Release |
|----------|-------------|----------------------------|
| [#77221](https://github.com/NousResearch/hermes-agent/issues/77221) + [#77223](https://github.com/NousResearch/hermes-agent/issues/77223) + [#77222](https://github.com/NousResearch/hermes-agent/issues/77222) | **Usage/cost analytics surface in Desktop** — three related features: local token/cost dashboard, cost bucket breakdown (included/estimated/unknown), per-day time-series aggregation | **High** — same author, clearly scoped, core metering already exists |
| [#77288](https://github.com/NousResearch/hermes-agent/pull/77288) | `--reasoning` flag for per-invocation reasoning effort control | **High** — simple CLI addition, already in PR |
| [#77287](https://github.com/NousResearch/hermes-agent/pull/77287) | Desktop sidebar "open sessions in tabs" persistent preference | **Medium** — quality-of-life, low risk |
| [#73778](https://github.com/NousResearch/hermes-agent/issues/73778) | Drag sessions between Projects in Desktop sidebar | **Medium** — UX feature, no technical blocker evident |
| [#30975](https://github.com/NousResearch/hermes-agent/pull/30975) | Web tool backend fallback chains | **Low-Medium** — broader architectural change, needs decision |
| [#77290](https://github.com/NousResearch/hermes-agent/pull/77290) | Configurable `voice.concise_responses` toggle | **High** — trivial addition, backward-compatible |
| [#77293](https://github.com/NousResearch/hermes-agent/pull/77293) | `hermes desktop install` subcommand with cross-platform shortcuts | **High** — improves onboarding, low risk |

**Roadmap signal:** The project is clearly investing in **Desktop polish** (install command, tab preferences, cost analytics, reaction persistence) and **per-invocation configurability** (--reasoning, voice conciseness). The analytics cluster (#77221-#77223) suggests a coordinated "Usage Insights" feature coming soon.

## 7. User Feedback Summary

**Pain points:**
- **Desktop on Windows is fragile** — duplicate UI elements, broken updates, orphan processes. Multiple users reporting the same category of issues.
- **Session history is brittle** — model switches mid-conversation erase output (#76870), editing past messages fails (#75756). Users lose work.
- **Gateway reliability across platforms varies** — Telegram drops unmentioned photos (#47415), WhatsApp wedges on reconnect (#77268), multiplexed profiles collide on DM routing (#74285).
- **Docker arm64 support is broken** — published image has wrong-architecture wheels (#74554), blocking ARM users entirely.
- **Cost visibility is missing from Desktop** — metering exists in `state.db` but no UI surface (#77221). Power users want spending insights.
- **xAI TTS is non-functional** — four stacked protocol errors (#73985); a rewrite is in progress (#77285).

**Satisfaction signals:**
- Users appreciate the **kanban/agent workflow** but want more control over task decomposition (#62985).
- The `--resume` + YOLO persistence fix (#77237) addresses a real workflow gap for power users.
- The community is actively contributing fixes (13 merged/closed PRs today), indicating strong contributor engagement.

## 8. Backlog Watch

| Issue | Age | Risk | Note |
|-------|-----|------|------|
| [#29530](https://github.com/NousResearch/hermes-agent/issues/29530) | ~3 months | **High** | Shared auth home for profiled workers — OAuth split-brain risk with rotating tokens. `needs-decision` label. |
| [#62985](https://github.com/NousResearch/hermes-agent/issues/62985) | ~3 weeks | **Medium** | Kanban containment bypass — assignee discipline silently ignored. Affects multi-agent workflows. |
| [#74554](https://github.com/NousResearch/hermes-agent/issues/74554) | ~4 days | **High** | arm64 Docker image ships x86_64 wheels. Blocks entire architecture. Should be priority fix. |
| [#73804](https://github.com/NousResearch/hermes-agent/issues/73804) | ~5 days | **Medium** | Cron serialization starvation — workdir jobs silently block each other on single-thread pool. `needs-decision`. |
| [#39771](https://github.com/NousResearch/hermes-agent/issues/39771) | ~2 months | **Low** | `hermes version` false-positive "860 commits behind" after tag checkout. Cosmetic but confusing. |

**Maintainer attention needed:** Issues #29530 and #73804 carry `needs-decision` labels and have been open for weeks without resolution. The arm64 Docker issue (#74554) is a distribution quality gate that should be addressed before the next release. The Windows Desktop bug cluster (71837, 75756, 76870, 77277, 77286) collectively warrants a dedicated stability sprint.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-03

---

## 1. Today's Overview

PicoClaw showed healthy daily activity with **12 total updates** (3 issues, 9 PRs) in the last 24 hours and no new releases. The project is in a steady development cadence with a mix of bug fixes, security hardening, and feature additions. A notable security-focused PR (#3297) and a critical bug-fix PR (#3312) landed today, signaling active maintenance. No releases were pushed, suggesting the team may be accumulating changes before the next version bump.

---

## 2. Releases

*No new releases were published today.*

---

## 3. Project Progress

**Merged/Closed PRs (3):**

| PR | Author | Summary |
|---|---|---|
| [#3313](https://github.com/sipeed/picoclaw/pull/3313) | j-v | Fixed `customAllowPatterns` not working — default deny patterns were overriding user-configured allow lists in `guardCommand`. |
| [#3310](https://github.com/sipeed/picoclaw/pull/3310) | j-v | Auto PR generated by `picoclanker` (CI automation). |
| [#3261](https://github.com/sipeed/picoclaw/pull/3261) | PeterDaveHello | Added zh-TW locale and Traditional Chinese translations across WebUI and documentation. |

**Key advances:**
- **Security hardening** (#3297) — default remote exec to disabled, enforces origin policy at execution time, migrates configs to schema v4.
- **Tool-loop fix** (#3312) — stops agent turns early when a tool fails repeatedly with the same error, preventing silent infinite loops.
- **Shell allow-list fix** (#3313/#3314) — resolves a bug where `customAllowPatterns` was ignored due to precedence issues in `guardCommand`.

---

## 4. Community Hot Topics

**Most discussed open items:**

1. **[Issue #3298](https://github.com/sipeed/picoclaw/issues/3298)** — *Add AI Router as an OpenAI-compatible provider preset*
   - Maintained by the AI Router project itself. Highlights a community desire for one-click provider integrations rather than manual `api_base` configuration. Low comment activity but represents a strategic partnership opportunity.

2. **[Issue #3294](https://github.com/sipeed/picoclaw/issues/3294)** — *`/list models` only shows current model instead of all configured models*
   - AUX usability bug where the command name and expected behavior diverge. One comment; reflects real user confusion during multi-model setups.

3. **[PR #3297](https://github.com/sipeed/picoclaw/pull/3297)** — *Harden remote prompt and exec boundaries*
   - The most significant open PR. Proposes breaking changes (schema v4 migration, remote exec disabled by default). Active community interest likely given the security implications.

4. **[PR #3312](https://github.com/sipeed/picoclaw/pull/3312)** — *Stop turn early on repeated identical tool failure*
   - Directly addresses a production pain point (see Bugs & Stability). Author is also the issue reporter — strong signal of user-driven development.

**Underlying need:** Users are pushing for better multi-model UX, deeper provider integrations, and stronger security guarantees around remote execution.

---

## 5. Bugs & Stability

| Rank | Issue/PR | Severity | Description | Fix Status |
|---|---|---|---|---|
| 🔴 Critical | [#3311](https://github.com/sipeed/picoclaw/issues/3311) / [#3312](https://github.com/sipeed/picoclaw/pull/3312) | **High** | Agent spins silently for up to `max_tool_iterations` when a tool fails with the same error repeatedly; user never receives a response. Observed in production over Telegram. | ✅ PR #3312 open |
| 🟡 Medium | [#3294](https://github.com/sipeed/picoclaw/issues/3294) | **Medium** | `/list models` command only shows the current model, not all configured models. Contradicts command naming and user expectation. | ❌ No fix PR yet |
| 🟡 Medium | [#3314](https://github.com/sipeed/picoclaw/pull/3314) | **Medium** | `customAllowPatterns` ignored — default deny patterns took precedence, blocking commands like `git push` that users explicitly allowed. | ✅ PR #3314 open (supersedes #3313) |
| 🟢 Low | [#3295](https://github.com/sipeed/picoclaw/pull/3295) | **Low** | `SplitMessage` hangs on oversized fenced-code headers. Falls back to bounded raw split. | ✅ PR #3295 open |

---

## 6. Feature Requests & Roadmap Signals

| Item | Type | Signal |
|---|---|---|
| **[Issue #3298](https://github.com/sipeed/picoclaw/issues/3298)** — AI Router as preset provider | Feature Request | Strong: maintainer of AI Router is contributing. Likely candidate for next release if integration scope is small. |
| **[PR #3299](https://github.com/sipeed/picoclaw/pull/3299)** — Native Exa web search provider | New Feature | Ready for review; adds `tools.web` / `web_search` with Exa's API. Completes search provider matrix. Good candidate for inclusion. |
| **[PR #3297](https://github.com/sipeed/picoclaw/pull/3297)** — Security hardening + schema v4 | Breaking Change | Significant scope. Schema v4 migration will require user config changes. Likely held for a minor version bump. |
| **[PR #3296](https://github.com/sipeed/picoclaw/pull/3296)** — Czech i18n completion | Localization | Low-risk, high-community-value. Likely merge candidate. |

**Prediction:** The next release will likely include the Exa search provider (#3299), Czech i18n (#3296), and the tool-loop fix (#3312). Security hardening (#3297) and AI Router preset (#3298) may be deferred to a later cycle due to scope/breaking-change risk.

---

## 7. User Feedback Summary

**Pain points:**
- **Silent agent loops** — Users report frustration when the agent silently consumes `max_tool_iterations` on a failing tool (e.g., `git` without credentials) without ever responding. This is a top production complaint.
- **Multi-model UX gap** — The `/list models` command behavior does not match its name or user expectations, causing confusion in multi-provider setups.
- **Allow-list overrides** — Users who configure `customAllowPatterns` expect those patterns to work, but default deny rules silently block them.

**Positive signals:**
- Active contributor engagement (j-v with 3 PRs, lucapette driving a bug-to-fix pipeline).
- Localization community is active (zh-TW merged, Czech in review).
- Users are contributing their own provider integrations (AI Router, Exa), indicating a healthy open-source ecosystem.

---

## 8. Backlog Watch

| Item | Age | Status | Maintainer Action Needed |
|---|---|---|---|
| [#3298](https://github.com/sipeed/picoclaw/issues/3298) — AI Router preset | 8 days | Open, stale | Review integration scope; consider accepting or providing a contribution guide. |
| [#3297](https://github.com/sipeed/picoclaw/pull/3297) — Security hardening / schema v4 | 8 days | Open, stale | Large PR requiring careful review; schema migration notes needed for users. |
| [#3296](https://github.com/sipeed/picoclaw/pull/3296) — Czech i18n | 8 days | Open, stale | Low-risk merge candidate; review translation completeness. |
| [#3295](https://github.com/sipeed/picoclaw/pull/3295) — SplitMessage hang fix | 8 days | Open, stale | Regression fix with test coverage; straightforward merge. |
| [#3294](https://github.com/sipeed/picoclaw/issues/3294) — `/list models` bug | 9 days | Open, stale | Quick fix needed; no PR yet. |

**Overall project health:** 🟢 **Good** — Active contributor base, bugs are being addressed with PRs from reporters, and feature requests are coming from downstream maintainers. The main risk is the accumulation of stale PRs (#3295–#3299) that have seen little maintainer engagement in 8+ days.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-03

## 1. Today's Overview

NanoClaw shows moderate-to-high development velocity with 10 PRs updated in the past 24 hours and 3 already merged or closed. Core infrastructure work is ongoing around database stability, channel expansion (Dial/SMS/voice), and MCP server support. No new releases were published during this window. One open issue highlights a persistent Docker-related SQLite lock contention problem affecting production deployments. Overall project health is strong with active contributor engagement across feature, fix, and refactor categories.

## 2. Releases

No new releases published in the last 24 hours.

## 3. Project Progress

**Merged/Closed Today:**

- **#3176** — `fix(release): retry post-publish readback` (glifocat) — Resolves flaky release pipeline readback steps. [Link](https://github.com/nanocoai/nanoclaw/pull/3176)
- **#2626** — `fix(signal): replace silent restartService failure with explicit error` (eldar702) — Fixes a bug where Signal service restart via `launchctl kickstart` silently no-oped after prior unload, masking failures from the wizard. [Link](https://github.com/nanocoai/nanoclaw/pull/2626)
- **#301** — `feat(skill): enhance add-telegram skill` (kadaliao) — Adds Markdown-to-HTML rendering, file download support (≤10MB), and Linux/Docker guidance to the Telegram skill. Currently in **Blocked / Pending Closure** state. [Link](https://github.com/nanocoai/nanoclaw/pull/301)

**Still Open / In Review:**

- **#3050** — `feat(setup): add Dial to channel picker + wizard/skills` — Extends the setup wizard to expose the new Dial channel. [Link](https://github.com/nanocoai/nanoclaw/pull/3050)
- **#3041** — `feat(channels): add Dial channel adapter (SMS + AI voice calls)` — Core adapter implementation for Dial integration. [Link](https://github.com/nanocoai/nanoclaw/pull/3041)
- **#3090** — `fix(templates): prepend all top-level context Markdown` — Ensures context Markdown is correctly prepended in template rendering. [Link](https://github.com/nanocoai/nanoclaw/pull/3090)
- **#3092** — `feat: support remote Streamable HTTP MCP servers` — Enables connecting to remote MCP servers over HTTP. [Link](https://github.com/nanocoai/nanoclaw/pull/3092)
- **#3172** — `chore(skills): remove the two qodo skills` — Cleanup of deprecated qodo skills. [Link](https://github.com/nanocoai/nanoclaw/pull/3172)
- **#2625** — `fix(teams): set supportsFiles: true in Teams manifest` — Unblocks file upload/paperclip UI in Teams personal chats. [Link](https://github.com/nanocoai/nanoclaw/pull/2625)
- **#3175** — `fix: route command-gate denials through the delivery adapter, not outbound.db` — Prevents double-writer corruption risk on session databases. [Link](https://github.com/nanocoai/nanoclaw/pull/3175)

## 4. Community Hot Topics

- **Issue #3177** — [Session database lock contention on Docker cross-mount filesystems](https://github.com/nanocoai/nanoclaw/issues/3177) — The most impactful open issue. SQLite DELETE journal mode fails to propagate across Docker mounts (VirtioFS), causing 29,000+ readonly errors and intermittent message delivery failures on macOS/Linux Docker deployments. This reflects a significant user pain point around containerized reliability and points to the need for better SQLite WAL mode configuration or filesystem-aware fallbacks.

- **PR #3041 / #3050** — [Dial channel adapter + wizard integration](https://github.com/nanocoai/nanoclaw/pull/3041) / [PR #3050](https://github.com/nanocoai/nanoclaw/pull/3050) — The addition of SMS and AI voice call support via a new "Dial" channel adapter is generating sustained PR activity. This signals strong community demand for expanded communication channels beyond the existing integrations.

- **PR #3092** — [Remote Streamable HTTP MCP servers](https://github.com/nanocoai/nanoclaw/pull/3092) — Support for remote MCP servers indicates users are deploying NanoClaw in distributed/clustered environments and need out-of-cluster agent connectivity.

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|----------|------|-------------|------------|
| **High** | #3177 | SQLite lock contention on Docker mounts causing 29K+ readonly errors and delivery failures | Open issue; no fix PR yet |
| **Medium** | #2583 (via #2626) | Signal `restartService()` silently succeeded on already-unloaded plist, masking failures | ✅ Merged in #2626 |
| **Medium** | #3175 | `writeOutboundDirect()` inserting into `outbound.db` as a second writer, risking database corruption | ✅ Open PR #3175 |
| **Low** | #2461 (via #2625) | Teams `supportsFiles: false` hardcoded, disabling paperclip UI and dropping `send_file` deliveries | ✅ Open PR #2625 |

The SQLite lock contention (#3177) is the most critical outstanding stability concern, particularly for Docker-based deployments which are common in production.

## 6. Feature Requests & Roadmap Signals

- **Dial Channel (SMS + AI Voice)** — PRs #3041 and #3050 are well-advanced and likely candidates for the next minor release, given they span both the adapter and the setup wizard.
- **Remote MCP Server Support** — PR #3092 adds Streamable HTTP MCP server connectivity, a feature that aligns with growing distributed-agent architectures.
- **Template Context Prepending** — PR #3090 fixes a rendering bug but also improves context handling; could ship as a patch fix.
- **Telegram Skill Enhancements** — PR #301 (Markdown rendering, file downloads) has been open since February and is currently blocked/pending closure. Its long dormancy suggests it may be superseded or needs rework.

## 7. User Feedback Summary

- **Docker/Container Reliability** — The #3177 issue underscores that Docker deployments on macOS/Linux with VirtioFS mounts are a real production pain point. Users are hitting severe database lock contention that degrades message delivery.
- **Channel Diversity Demand** — Multiple PRs targeting new channel adapters (Dial/SMS/voice) indicate users want broader communication coverage.
- **Teams File Sharing** — The #2625 fix reveals that file transfer was silently broken in Teams personal chats due to a manifest misconfiguration.
- **Signal Restart Reliability** — The #2626 fix addresses user frustration where the wizard reported success but the service wasn't actually restarted.

## 8. Backlog Watch

- **#301** — [Telegram skill enhancement (Blocked/Pending Closure)](https://github.com/nanocoai/nanoclaw/pull/301) — Open since **2026-02-18** (~5.5 months). This PR adds Markdown rendering and file downloads to Telegram but has been stuck in blocked status for an extended period. Requires maintainer review to either merge, rebase, or close.
- **#3177** — [SQLite lock contention on Docker](https://github.com/nanocoai/nanoclaw/issues/3177) — Open since 2026-08-02 with no fix PR yet. High-severity production issue that needs prioritization.
- **#2625** — [Teams `supportsFiles` manifest fix](https://github.com/nanocoai/nanoclaw/pull/2625) — Open since 2026-05-27 (~2.5 months). Simple one-line fix that unblocks a user-facing feature; should be easy to merge.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-03

---

## 1. Today's Overview

IronClaw is experiencing a high-velocity day with 31 PRs and 8 issues updated in the last 24 hours, signaling intense development and QA activity. The project is in an active post-Wave-2 consolidation phase, with core architecture decisions being formally documented and a cluster of production-critical bugs surfaced by recent QA audits. The contributor base is diversifying — new contributors are submitting PRs alongside sustained core-team output, which is a healthy signal. No new releases were published today, but several merged PRs from prior days are still in the open-PR queue awaiting final review.

---

## 2. Releases

**No new releases published today.**

The most recent release activity is captured in the long-running PR **#5598** (open since 2026-07-03), which documents a version bump:
- `ironclaw_common`: 0.4.2 → 0.5.0 *(⚠ API-breaking)*
- `ironclaw_safety`: 0.2.2 → 0.2.3 *(✓ API-compatible)*
- `ironclaw_skills`: 0.3.0 → 0.4.0 *(⚠ API-breaking)*

See: <https://github.com/nearai/ironclaw/pull/5598>

---

## 3. Project Progress

### Merged / Closed Today
| PR | Title | Author |
|---|---|---|
| [#7018](https://github.com/nearai/ironclaw/pull/7018) | Consolidate Wave 2 port-inversion stack (WS2.2, WS2.4, WS5) | BenKurrek |
| [#7013](https://github.com/nearai/ironclaw/pull/7013) | Restore original 90% changed-line coverage floor | serrrfirat |
| [#6952](https://github.com/nearai/ironclaw/pull/6952) | Scope Reborn PR tests by affected area | serrrfirat |
| [#7015](https://github.com/nearai/ironclaw/issues/7015) | UI bug on Staking page | sergeiest |

### Key Advances
- **Wave 2 consolidation**: PR #7018 merged the four previously separate port-inversion PRs into a single branch on `main`, replacing a costly four-step merge cascade.
- **CI/CD hardening**: PR #7013 restored the 90% changed-line coverage threshold; PR #6952 introduced deterministic affected-area planning for PR tests.
- **Architecture documentation**: PRs #7033 and #7032 formally resolve and reconcile eight open Wave 2 architecture decisions against merged `main`.
- **WebUI fixes**: PR #6917 enables authenticated preview for workspace file links; PR #6906 restricts project cards to API-backed data only, removing fabricated metrics.
- **MCP auth**: PR #7024 resolves custom MCP OAuth registration using RFC 9728 path-derived metadata instead of heuristic guessing.

---

## 4. Community Hot Topics

### Most Discussed Open PRs
1. **[PR #6917](https://github.com/nearai/ironclaw/pull/6917)** — *fix(webui): open workspace file links in authenticated previews* (contributor: italic-jinxin)
   - Addresses a usability gap where workspace file links in Markdown bypass authentication, preventing preview access. Reflects growing demand for secure, authenticated content rendering in the web UI.

2. **[PR #6906](https://github.com/nearai/ironclaw/pull/6906)** — *fix: show only API-backed project data* (contributor: italic-jinxin)
   - Removes fabricated spend, gate, failure, thread, activity, and health metrics from project cards. Signals user frustration with misleading dashboard data.

3. **[PR #7024](https://github.com/nearai/ironclaw/pull/7024)** — *fix(extensions): resolve custom MCP auth during registration* (contributor: henrypark133)
   - Implements proper OAuth discovery for hosted MCPs via RFC 9728. Addresses a real pain point for users integrating Stripe and other OAuth-protected MCPs.

4. **[PR #5981](https://github.com/nearai/ironclaw/pull/5981)** — *Reborn queued-message steering (ported to current main)* (contributor: ilblackdragon)
   - A long-running PR (open since 2026-07-11) that has been forward-ported and has turn-boundary races fixed. End-to-end tested. Indicates sustained community interest in reliable message delivery semantics.

---

## 5. Bugs & Stability

### Critical / High Severity

| Issue | Title | Author | Fix PR? |
|---|---|---|---|
| [#7035](https://github.com/nearai/ironclaw/issues/7035) | **Model budget enforcement is not wired in production — daily USD caps unenforced since #6174** | BenKurrek | No |
| [#7016](https://github.com/nearai/ironclaw/issues/7016) | **Ambient proxy env vars bypass DNS-rebinding protection in ReqwestNetworkTransport** | theredspoon | #7027 |
| [#7017](https://github.com/nearai/ironclaw/issues/7017) | **Interrupted-delivery recovery can overwrite a concurrent Delivered status** | theredspoon | #7028 |
| [#7025](https://github.com/nearai/ironclaw/issues/7025) | **Concurrent coordinators can both send the same durable delivery attempt** | theredspoon | #7029 |

### Medium Severity

| Issue | Title | Author | Fix PR? |
|---|---|---|---|
| [#7031](https://github.com/nearai/ironclaw/issues/7031) | Failed lazy delivery recovery is not retried within a coordinator lifetime | theredspoon | — |
| [#7030](https://github.com/nearai/ironclaw/issues/7030) | Host-mediated egress ignoring ambient proxy variables in operator diagnostics | theredspoon | #7034 |
| [#7036](https://github.com/nearai/ironclaw/issues/7036) | Changed-coverage gate does not run on ordinary PRs | BenKurrek | — |

### Low Severity

| Issue | Title | Author | Fix PR? |
|---|---|---|---|
| [#7015](https://github.com/nearai/ironclaw/issues/7015) | UI bug on Staking page | sergeiest | — |

**Summary**: Six open bugs filed in the last 24 hours, four of which already have fix PRs open ( #7027, #7028, #7029, #7034). The most concerning unresolved gap is **#7035** (model budget enforcement not wired in production), which represents a live financial-control deficiency. The DNS-rebinding bypass (#7016 → #7027) is a security-relevant issue that has an active fix.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Interpretation |
|---|---|---|
| **MCP OAuth registration overhaul** | PR #7024 | Moving toward standards-compliant (RFC 9728) OAuth discovery for MCP extensions — likely to be a standard feature in the next release cycle. |
| **Ambient proxy hardening** | PRs #7027, #7034 | The project is actively closing a security gap around proxy env var bypass — expect hardened network transport in the next release. |
| **Durable delivery single-flight ownership** | PRs #7028, #7029 | Restoring atomic `Prepared → Sending` transitions suggests the next release will emphasize delivery reliability guarantees. |
| **Queued-message steering** | PR #5981 | Long-pending but now tested end-to-end; likely to ship in the next minor release if review completes. |
| **Workspace file link authentication** | PR #6917 | Reflects a pattern of improving authenticated content access — likely to continue in web UI iterations. |
| **CI test scoping by affected area** | PR #6952 (merged) | Signals investment in faster PR feedback loops; expect further CI optimization in coming weeks. |

---

## 7. User Feedback Summary

- **Frustration with misleading metrics**: PR #6906 directly addresses user confusion caused by fabricated project-level metrics (spend, activity, health). Users want dashboard data that is verifiably API-backed.
- **Authentication gaps in web UI**: PR #6917 highlights a pain point where workspace file links bypass auth, undermining security expectations.
- **MCP onboarding friction**: PR #7024 shows that custom MCP registration with OAuth is error-prone; users need reliable, standards-based auth flows.
- **Staking page UX bugs**: Issue #7015 reports a UI defect on the Staking page, though the report lacks detail (no screenshots or reproduction steps).
- **General sentiment**: The community is actively engaging with QA findings and reporting production gaps. The volume of self-filed issues by core contributors (BenKurrek, theredspoon) suggests a mature, self-auditing project culture.

---

## 8. Backlog Watch

| Item | Age | Risk | Note |
|---|---|---|---|
| [#7035](https://github.com/nearai/ironclaw/issues/7035) — Model budget enforcement not wired | 1 day | **Critical** | No fix PR yet. Live production gap with financial implications. Needs immediate maintainer attention. |
| [#5981](https://github.com/nearai/ironclaw/pull/5981) — Queued-message steering | 23 days | Medium | Open since 2026-07-11. Forward-ported and tested, but not yet merged. Risk of drift. |
| [#5598](https://github.com/nearai/ironclaw/pull/5598) — Release PR (breaking changes) | 31 days | Medium | Documents API-breaking changes in `ironclaw_common` and `ironclaw_skills`. Still open — release may be delayed. |
| [#7015](https://github.com/nearai/ironclaw/issues/7015) — Staking page UI bug | 1 day | Low | Insufficient detail (no screenshots/repro). Needs reporter follow-up before action. |
| [#7036](https://github.com/nearai/ironclaw/issues/7036) — Coverage gate not running on ordinary PRs | 1 day | Medium | Described as "know what green means" — not an emergency, but the CI policy gap should be documented or resolved. |

---

*Digest generated from GitHub data as of 2026-08-03. All links resolve to `github.com/nearai/ironclaw`.*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI Project Digest — 2026-08-03

## 1. Today's Overview

LobsterAI (netease-youdao/LobsterAI) showed moderate community activity over the past 24 hours with **3 issues** and **6 PRs** updated. No new releases were published. Two issues and two PRs were closed/merged, while one open issue and four open PRs remain pending maintainer review. The project continues to receive community-driven contributions focused on performance optimization, UI improvements, and dependency updates, indicating a healthy open-source rhythm despite the absence of a formal release cycle recently.

## 2. Releases

**No new releases today.**

## 3. Project Progress

**Closed/Merged today:**

| PR | Author | Summary |
|----|--------|---------|
| [#1285](https://github.com/netease-youdao/LobsterAI/pull/1285) | @dependabot[bot] | `chore(deps-dev): bump concurrently 8.2.2 → 9.2.1` |
| [#1286](https://github.com/netease-youdao/LobsterAI/pull/1286) | @dependabot[bot] | `chore(deps-dev): bump tailwindcss 3.4.19 → 4.2.2` |

**Notable open PRs advancing today:**

- **[#1215](https://github.com/netease-youdao/LobsterAI/pull/1215)** — Fixes a regression in IM chat handler initialization where platform-specific config saves (DingTalk, Telegram) bypassed `updateChatHandler()`, leaving stale system prompt/settings.
- **[#1218](https://github.com/netease-youdao/LobsterAI/pull/1218)** — Rebuilds the scheduled-task list sorting logic to use deterministic ordering instead of UUID-string sorting, directly improving UX for task management.
- **[#1219](https://github.com/netease-youdao/LobsterAI/pull/1219)** — Eliminates unnecessary re-renders in the cowork session list/detail views by adding `React.memo` and consolidating Redux selectors.
- **[#1220](https://github.com/netease-youdao/LobsterAI/pull/1220)** — Resolves an N+1 database query problem in `recentChats()` and `conversationSearch()` by batching message-lookups per session.

## 4. Community Hot Topics

| Item | Comments | 👍 | Link |
|------|----------|----|------|
| Issue #1287 — IM connectivity test accepts invalid credentials | 2 | 0 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1287) |
| Issue #1289 — Long code block collapse/expand | 2 | 0 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1289) |
| Issue #1217 — Intermittent gateway restart | 1 | 0 | [Issue](https://github.com/netease-youdao/LobsterAI/issues/1217) |
| PR #1215 — IM chat handler stale config fix | — | 0 | [PR](https://github.com/netease-youdao/LobsterAI/pull/1215) |
| PR #1218 — Task list sorting refactor | — | 0 | [PR](https://github.com/netease-youdao/LobsterAI/pull/1218) |
| PR #1219 — Cowork re-render optimization | — | 0 | [PR](https://github.com/netease-youdao/LobsterAI/pull/1219) |
| PR #1220 — N+1 query elimination | — | 0 | [PR](https://github.com/netease-youdao/LobsterAI/pull/1220) |

**Analysis:** The most discussed topics revolve around **IM integration robustness** (#1287, #1215) and **UI/UX performance** (#1219, #1220, #1289). Users are increasingly sensitive to responsiveness during streaming conversations and session management — a signal that the cowork/session features are seeing real adoption and scaling pain.

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR? |
|----------|------|-------------|---------|
| 🔴 High | [Issue #1287](https://github.com/netease-youdao/LobsterAI/issues/1287) | IM bot connectivity test passes with placeholder credentials (`appkey`/`appsecret`/`aesKey` all set to `"1"`), creating a false sense of successful configuration. | ❌ No PR yet |
| 🟠 Medium | [Issue #1217](https://github.com/netease-youdao/LobsterAI/issues/1217) | Intermittent gateway restart during operation (~3–5×/day on Windows 10), disrupting active sessions. Logs attached. | ❌ No PR yet |
| 🟡 Low | — | No new crash reports today. | — |

**Note:** Issue #1287 is a security-adjacent bug — a misconfigured or untested IM connection could silently fail in production while appearing healthy. Issue #1217 impacts day-to-day reliability and warrants a root-cause investigation.

## 6. Feature Requests & Roadmap Signals

| Item | Description | Likelihood for Next Release |
|------|-------------|----------------------------|
| [#1289](https://github.com/netease-youdao/LobsterAI/issues/1289) — Auto-collapse long code blocks | Users want code blocks >~15 lines to collapse automatically, with a configurable threshold. | 🟢 High — well-scoped, UI-layer change, aligns with current renderer focus |
| [#1218](https://github.com/netease-youdao/LobsterAI/pull/1218) — Deterministic task list sorting | Scheduled-task list should sort by creation/execution time rather than UUID string. | 🟢 High — PR already submitted, directly improves usability |
| [#1219](https://github.com/netease-youdao/LobsterAI/pull/1219) — Session list rendering perf | `React.memo` + selector consolidation for cowork session views. | 🟢 High — PR ready, pure performance win |
| [#1220](https://github.com/netease-youdao/LobsterAI/pull/1220) — N+1 query fix | Batch message lookups in `recentChats`/`conversationSearch`. | 🟢 High — PR ready, database-layer improvement |

**Signal:** The project's near-term roadmap appears to be dominated by **frontend performance and UX polish** rather than new features, suggesting the core capabilities are maturing and the team is investing in quality-of-life improvements.

## 7. User Feedback Summary

- **Pain point — IM configuration UX:** Users are configuring IM bots (DingTalk, Popo, Telegram) and running into silent failures where connectivity tests pass with bogus credentials (#1287). This suggests the validation logic needs to be tightened.
- **Pain point — Reading experience with long outputs:** AI-generated code blocks that are 15–200 lines long fill the screen and force excessive scrolling (#1289). Users want a toggle or auto-collapse behavior.
- **Pain point — Intermittent gateway restarts:** Windows users report the gateway randomly restarting 3–5 times per day (#1217), interrupting active sessions. This is the most disruptive bug reported and likely has the highest impact on daily satisfaction.
- **General sentiment:** The community is actively contributing fixes (4 PRs from 3 distinct contributors), indicating strong engagement and satisfaction with the project's direction. Performance PRs (#1219, #1220) show users are invested in the cowork/session experience at scale.

## 8. Backlog Watch

| Item | Age | Priority | Status |
|------|-----|----------|--------|
| [#1287](https://github.com/netease-youdao/LobsterAI/issues/1287) — IM connectivity bypass | ~4 months | 🔴 High | Open, stale — needs security review and fix |
| [#1217](https://github.com/netease-youdao/LobsterAI/issues/1217) — Gateway intermittent restart | ~4 months | 🟠 Medium | Open, stale — needs log analysis and root-cause assignment |
| [#1215](https://github.com/netease-youdao/LobsterAI/pull/1215) — IM chat handler fix | ~4 months | 🟠 High | Open — reviewer attention needed to unblock |
| [#1218](https://github.com/netease-youdao/LobsterAI/pull/1218) — Task list sorting | ~4 months | 🟡 Medium | Open — ready for review |
| [#1219](https://github.com/netease-youdao/LobsterAI/pull/1219) — Cowork perf | ~4 months | 🟡 Medium | Open — ready for review |
| [#1220](https://github.com/netease-youdao/LobsterAI/pull/1220) — N+1 queries | ~4 months | 🟡 Medium | Open — ready for review |

**Recommendation:** Four PRs and two issues have been open since early April with no maintainer response. The IM connectivity bug (#1287) and gateway instability (#1217) should be prioritized, followed by the three performance/UX PRs which are ready for merge.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-03

## 1. Today's Overview
Moltis shows **low daily activity** with no new issues resolved and no merged pull requests today. The only notable movement is PR #1183, which remains open and introduces managed Git repository bundles for MCP server discovery and lifecycle management. The absence of closed issues and new releases suggests a maintenance lull or a feature-development pause. Project health appears **stable but quiet**, with no regressions or critical bugs reported.

## 2. Releases
No new releases published today.

## 3. Project Progress
- **No merged or closed PRs today.**
- The sole open PR (#1183) advances a significant feature: **managed Git repository bundles for MCP servers**, enabling HTTPS/SSH transport, vault lifecycle integration, and CLI/RPC/web UI workflows. This indicates active development on MCP ecosystem integration rather than bug fixes or quick iterations.

## 4. Community Hot Topics
- **[PR #1183: feat(mcp): add managed repository bundles](https://github.com/moltis-org/moltis/pull/1183)** — Open since 2026-08-02, updated today. Zero reactions/comments so far.
  - **Underlying need:** Users and maintainers are seeking standardized, version-controlled distribution of MCP servers via Git bundles—suggesting growing demand for reproducible, auditable MCP deployment patterns. This aligns with broader ecosystem trends toward git-backed package management.

## 5. Bugs & Stability
No bugs, crashes, or regressions reported today. Zero open issues, indicating either a healthy user base with no blockers or low reporting activity.

## 6. Feature Requests & Roadmap Signals
- **PR #1183** signals a clear roadmap direction: deeper MCP server management via Git repository bundles, including import workflows and database migration support. If merged, this feature is likely to ship in the next minor release, given its comprehensive scope (CLI/RPC/web UI, vault integration, credential transport).

## 7. User Feedback Summary
No direct user feedback captured today (zero issues, zero comments). The project appears to be in a development phase where features are being built before community testing ramps up. Satisfaction/dissatisfaction metrics are unavailable.

## 8. Backlog Watch
No long-unanswered issues or PRs identified today due to minimal issue/PR activity. PR #1183 remains the sole open item and warrants maintainer review to unblock further development momentum.

---
*Data source: GitHub activity for moltis-org/moltis (2026-08-02 to 2026-08-03)*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-03

## 1. Today's Overview

QwenPaw shows strong daily activity with 41 items updated in the last 24 hours (13 issues, 28 PRs), indicating a healthy and responsive development cadence. Three issues were closed today, all addressing concrete bugs (skill-tag persistence, shell-command UI freeze, misplaced cursor). The project has no new releases yet, but a cluster of open PRs targets critical compatibility and UX regressions introduced by the recent `agentscope==2.0.4.post1` upgrade. Overall, the project is in an active stabilization phase following the 2.0.1 release.

## 2. Releases

No new releases today. The latest known version remains **QwenPaw 2.0.1** (both Desktop and pip).

## 3. Project Progress

**Closed / Merged PRs today:**

- **[#6637](https://github.com/agentscope-ai/QwenPaw/pull/6637)** — Fixed UI freeze caused by `execute_shell_command` output exceeding display thresholds. Large tool outputs (>100 KB / 1,000 lines) are now truncated with head/tail indicators and syntax highlighting is skipped.
- **[#6639](https://github.com/agentscope-ai/QwenPaw/pull/6639)** — Fixed monaco-editor CSS breakage in production builds by removing the unconditional `node_modules` CSS stub plugin.
- **[#6640](https://github.com/agentscope-ai/QwenPaw/pull/6640)** — Creator module: rejection feedback loop, overlay stacking, structured logging, and runtime hardening (closed, likely merged).

**PRs advanced today (open/under review):**

- **[#6641](https://github.com/agentscope-ai/QwenPaw/pull/6641)** — Creator rejection-feedback loop with undo/regenerate distinction and specialist delegation fencing.
- **[#6525](https://github.com/agentscope-ai/QwenPaw/pull/6525)** — Transparent user-context passthrough from Chat API through Agent → Tool → MCP → SKILL CLI.
- **[#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302)** — Unified provider discovery, model metadata, routing, and agent controls.
- **[#6636](https://github.com/agentscope-ai/QwenPaw/pull/6636)** — Chat-history pagination + GZip compression to fix slow-network timeouts.
- **[#6629](https://github.com/agentscope-ai/QwenPaw/pull/6629)** — Triggers `summarize_when_compact` memory flow on auto-scroll compression (fixes #6624).
- **[#6623](https://github.com/agentscope-ai/QwenPaw/pull/6623)** — Fixes ACP `delegate_external_agent` text-loss race condition (fixes #6625).

## 4. Community Hot Topics

| Issue / PR | Comments | Focus |
|---|---|---|
| [#6537](https://github.com/agentscope-ai/QwenPaw/issues/6537) — Skill tags vanish on restart | 11 | Persistent storage vs. manifest reconciliation gap |
| [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) — agentscope 2.0.4.post1 incompatibility | 2 | Proactive crashes + tool-permission deadlock |
| [#6565](https://github.com/agentscope-ai/QwenPaw/issues/6565) — Shell command newline collapse + PIPE hang | 1 | Multi-line command syntax + Linux background-process freeze |
| [#6621](https://github.com/agentscope-ai/QwenPaw/issues/6621) — Multi-agent collaboration guidance missing | 1 | User frustration over silent agent non-activation |

**Underlying needs:** The community is pressing on three fronts: (1) **reliability of persistence** (skill tags, chat history), (2) **shell/command execution robustness** on Linux, and (3) **multi-agent discoverability** — users expect agents to auto-activate peers without explicit PROFILE.md instructions.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| 🔴 High | [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) | agentscope 2.0.4.post1 breaks proactive/memory subsystem (crashes + deadlock) | [#6615](https://github.com/agentscope-ai/QwenPaw/pull/6615) (open) |
| 🔴 High | [#6619](https://github.com/agentscope-ai/QwenPaw/issues/6619) | `ToolCallBlock` missing `extra_content` → crash on Gemini streaming | [#6620](https://github.com/agentscope-ai/QwenPaw/pull/6620) (open) |
| 🟡 Medium | [#6635](https://github.com/agentscope-ai/QwenPaw/issues/6635) | Console pages timeout on slow networks (uncompressed MB-level payloads) | [#6636](https://github.com/agentscope-ai/QwenPaw/pull/6636) (open) |
| 🟡 Medium | [#6633](https://github.com/agentscope-ai/QwenPaw/issues/6633) | Skills/Skill Pool pages timeout — same root cause as #6635 | Same as above |
| 🟡 Medium | [#6624](https://github.com/agentscope-ai/QwenPaw/issues/6624) | Auto-scroll compression doesn't trigger memory summarize flow | [#6629](https://github.com/agentscope-ai/QwenPaw/pull/6629) (open) |
| 🟡 Medium | [#6625](https://github.com/agentscope-ai/QwenPaw/issues/6625) | ACP delegate returns "completed without text output" on notification race | [#6623](https://github.com/agentscope-ai/QwenPaw/pull/6623) (open) |
| 🟡 Medium | [#6626](https://github.com/agentscope-ai/QwenPaw/issues/6626) | CI proof-gate strips fenced Evidence blocks entirely | — |
| 🟢 Low | [#6547](https://github.com/agentscope-ai/QwenPaw/issues/6547) | Misplaced cursor in Coding Mode editor | Closed |
| 🟢 Low | [#6589](https://github.com/agentscope-ai/QwenPaw/issues/6589) | Shell command huge output freezes UI | Merged via [#6637](https://github.com/agentscope-ai/QwenPaw/pull/6637) |
| 🟢 Low | [#6565](https://github.com/agentscope-ai/QwenPaw/issues/6565) | Newline collapse + PIPE hang in `execute_shell_command` | [#6566](https://github.com/agentscope-ai/QwenPaw/pull/6566) (open) |
| 🟢 Low | [#66639](https://github.com/agentscope-ai/QwenPaw/pull/6639) | Monaco editor CSS broken in production builds | Closed (merged) |

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Likelihood for Next Release |
|---|---|---|
| Read dragged files by original path instead of upload/download cycle | [#6642](https://github.com/agentscope-ai/QwenPaw/issues/6642) | Medium — workflow convenience, low risk |
| Transparent user-context passthrough (user_id, channel, tenant) across the full call chain | [#6525](https://github.com/agentscope-ai/QwenPaw/pull/6525) | High — already under active review, strong enterprise signal |
| Unified provider discovery & model routing | [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) | High — large PR, likely split across releases |
| Chat-history pagination + GZip compression | [#6636](https://github.com/agentscope-ai/QwenPaw/pull/6636) | High — directly addresses slow-network pain |
| Multi-agent auto-activation / onboarding guidance | [#6621](https://github.com/agentscope-ai/QwenPaw/issues/6621) | Medium — docs/UX improvement, not a code feature |

## 7. User Feedback Summary

- **Frustration with agentscope compatibility churn:** Two issues (#6612, #6619) directly blame `agentscope==2.0.4.post1` API changes for runtime crashes. Users report silent failures (empty responses, deadlocks) that are hard to debug.
- **Shell command execution is a pain point:** Three separate issues (#6589, #6565, #6637) address `execute_shell_command` bugs — UI freeze from large output, newline collapsing, and Linux PIPE hangs. This is a recurring reliability gap.
- **Slow-network UX degradation:** Two issues (#6635, #6633) report the same root cause — monolithic uncompressed API responses exceeding the 30 s frontend timeout. Users on constrained connections are blocked from using Console and Skill pages.
- **Multi-agent confusion:** A user logged 50+ rounds of debugging before discovering that default agents don't auto-invoke peers without explicit PROFILE.md instructions. The community wants either better defaults or stronger onboarding.
- **File-drag workflow friction:** Users find the current upload-then-read cycle for dropped files unnecessary and file-proliferating; they expect direct path reads like competing desktop agents.

## 8. Backlog Watch

| Item | Reason for Watch |
|---|---|
| [#6565](https://github.com/agentscope-ai/QwenPaw/issues/6565) / [#6566](https://github.com/agentscope-ai/QwenPaw/pull/6566) | Shell command bug open since 2026-07-30; fix PR exists but unmerged. Affects all Linux/Unix users. |
| [#6612](https://github.com/agentscope-ai/QwenPaw/issues/6612) / [#6615](https://github.com/agentscope-ai/QwenPaw/pull/6615) | agentscope incompatibility is a high-severity blocking issue for users on the latest agentscope. Fix PR open since 2026-07-31. |
| [#6619](https://github.com/agentscope-ai/QwenPaw/issues/6619) / [#6620](https://github.com/agentscope-ai/QwenPaw/pull/6620) | Gemini streaming crash; fix PR open since 2026-08-01. Blocks any user relying on Gemini tools. |
| [#6621](https://github.com/agentscope-ai/QwenPaw/issues/6621) | Multi-agent guidance gap — no PR yet. Structural/UX issue needing maintainer decision. |
| [#6626](https://github.com/agentscope-ai/QwenPaw/issues/6626) | CI proof-gate stripping fenced evidence blocks — affects contributor experience; no fix yet. |
| [#6642](https://github.com/agentscope-ai/QwenPaw/issues/6642) | File-drag direct-read feature request — open since 2026-08-03, no PR yet. |

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-03

## 1. Today's Overview

ZeroClaw is in an active maintenance and hardening phase following the **v0.8.4** release, with **50 issues** and **50 PRs** updated in the last 24 hours. The project shows strong contributor momentum — v0.8.4 itself spans **262 commits from 49 contributors**. Activity is heavily concentrated around RFC ratification, security hardening, and CI/infrastructure repairs. The project health is solid: a healthy open-to-closed ratio, multiple high-priority bugs receiving fixes, and a clear focus on stability ahead of v0.9.0.

---

## 2. Releases

### v0.8.4 — Maintenance & Hardening Release
- **262 commits** across **49 contributors**
- Expands the **memory and SOP control planes**
- Improves **provider and channel reliability**
- Strengthens **sandbox and credential boundaries**
- Desktop and release pipeline improvements

**No breaking changes announced.** This is a maintenance train release; migration should be straightforward.

---

## 3. Project Progress

**Closed/Merged today:**
- [#9037](https://github.com/zeroclaw-labs/zeroclaw/issues/9037) — Fixed terminal marker leakage (`<eom>`) from streamed assistant text into conversation history and channel delivery
- [#9571](https://github.com/zeroclaw-labs/zeroclaw/issues/9571) — **Removed WATI channel** entirely (security/abandonment rationale)
- [#8838](https://github.com/zeroclaw-labs/zeroclaw/issues/8838) — Hardened SSE completion and idle timeouts across OpenAI, Anthropic, and compatible providers
- [#9519](https://github.com/zeroclaw-labs/zeroclaw/issues/9519) — Fixed race condition in gateway config writes that could silently erase concurrent updates
- [#9478](https://github.com/zeroclaw-labs/zeroclaw/issues/9478) — Fixed silence bug: users now receive a notification when the reply-intent precheck declines their message
- [#9281](https://github.com/zeroclaw-labs/zeroclaw/issues/9281) — Fixed config set to roll back auto-created map aliases on failure (transactional safety)
- [#9676](https://github.com/zeroclaw-labs/zeroclaw/issues/9676) — Restored all-features Docker publishing after MSRV bump

**Key features advancing (open PRs):**
- [#9352](https://github.com/zeroclaw-labs/zeroclaw/issues/9352) — Cross-turn conversation correlation for OTel export (implements RFC #8933 design)
- [#9696](https://github.com/zeroclaw-labs/zeroclaw/issues/9696) — Modalities support in models.dev catalog parsing (enables vision-aware model discovery)
- [#8969](https://github.com/zeroclaw-labs/zeroclaw/issues/8969) — Slack thread context hydration on first bot interaction
- [#8313](https://github.com/zeroclaw-labs/zeroclaw/issues/8313) — Compact skill injection now default; full mode deprecated
- [#9405](https://github.com/zeroclaw-labs/zeroclaw/issues/9405) — Per-server custom CA trust for MCP transports

---

## 4. Community Hot Topics

| Issue | Title | Comments | Status |
|-------|-------|----------|--------|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) | RFC: Work Lanes, Board Automation, and Label Cleanup | 17 | In-progress |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | RFC: ZeroClaw Chat Completions profile | 15 | Open |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) | RFC: Pluggable inbound authentication and canonical principals | 9 | Open |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | RFC: Goal mode for bounded autonomous session work | 9 | Open |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker: Maintainer decision queue for RFCs | 8 | Open |

**Analysis:** The community is most engaged around **governance/process RFCs** and **protocol compatibility**. The Chat Completions profile (#8603) addresses a major interoperability need — many clients (Open WebUI, LobeChat, Continue.dev, LangChain) speak this protocol natively. The **Goal mode** RFC (#8303) fills a gaps in durable autonomous workflows. The **pluggable authentication** RFC (#7141) signals growing demand for enterprise-grade identity integration. Maintainer capacity is a bottleneck: the decision queue tracker (#8692) exists precisely because RFC ratification is backing up.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| **P0 / High** | [#9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) | Gateway webhook handlers for WhatsApp Cloud, Linq, and WATI **do not fail closed** — unauthenticated messages dispatch directly to agents | WATI removed via [#9571](https://github.com/zeroclaw-labs/zeroclaw/issues/9571); WhatsApp/Linq fixes in [#9382](https://github.com/zeroclaw-labs/zeroclaw/issues/9382) |
| **P1 / High** | [#9690](https://github.com/zeroclaw-labs/zeroclaw/issues/9690) | Containerfile StageX pin ships rustc 1.95.0, below declared MSRV — `all-features` Docker variant unbuildable since 2026-07-08 | Open, tracked |
| **P1 / High** | [#9624](https://github.com/zeroclaw-labs/zeroclaw/issues/9624) | Registry WIT pin diverges from master, breaking published plugin components | Accepted, open |
| **P1 / Medium** | [#9672](https://github.com/zeroclaw-labs/zeroclaw/issues/9672) | All three `cron add` CLI examples are broken; empty-state hint prints a fourth broken form | Accepted, open |
| **P2 / Medium** | [#8578](https://github.com/zeroclaw-labs/zeroclaw/issues/8578) | zerocode/tui does not terminate process on daemon startup failure | Closed |
| **P2 / Medium** | [#9465](https://github.com/zeroclaw-labs/zeroclaw/issues/9465) | Declined inbound channel messages produce only an emoji reaction, sender sees nothing | Closed via [#9478](https://github.com/zeroclaw-labs/zeroclaw/issues/9478) |

**Notable fix PRs:** [#9413](https://github.com/zeroclaw-labs/zeroclaw/issues/9413) (fail closed on unresolved Docker workspace roots), [#9419](https://github.com/zeroclaw-labs/zeroclaw/issues/9419) (credential rotation after rate limits), [#8943](https://github.com/zeroclaw-labs/zeroclaw/issues/8943) (Bedrock Nova 2 prompt caching exclusion).

---

## 6. Feature Requests & Roadmap Signals

| RFC/Issue | Summary | Likelihood for v0.9.0 |
|-----------|---------|----------------------|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — Chat Completions profile | Expose agent capabilities via OpenAI-compatible API | **High** — strong community demand, many client integrations depend on it |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) — Goal mode | First-class durable autonomous session mode | **Medium-High** — addresses a clear capability gap; RFC is active |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) — Pluggable authentication | OIDC and pluggable auth providers | **High** — labeled P1, targets Identity & Access milestone |
| [#7232](https://github.com/zeroclaw-labs/zeroclaw/issues/7232) — Structured observability | Rich events + OTel trace correlation | **High** — implementation PR [#9352](https://github.com/zeroclaw-labs/zeroclaw/issues/9352) is open |
| [#6998](https://github.com/zeroclaw-labs/zeroclaw/issues/6998) — Schema-validated memory consolidation | Bounded fallback for memory merges | **Medium** — RFC open, no implementation yet |
| [#9549](https://github.com/zeroclaw-labs/zeroclaw/issues/9549) — Community-powered local model advisor | Help users choose local models | **Low-Medium** — quickstart-tagged, no comments yet |
| [#9644](https://github.com/zeroclaw-labs/zeroclaw/issues/9644) — Retire Lucid memory connector | Upstream dormant since merge | **Certain** — RFC is procedural cleanup |

---

## 7. User Feedback Summary

**Pain points expressed:**
- **Channel silence on rejection:** Users receiving no feedback when the reply-intent precheck declines their message (now fixed in #9478) — indicates the system needs transparent failure modes.
- **Terminal marker leakage:** `<eom>` markers from OpenRouter/AI21 models leaking into transcripts and channel delivery (fixed in #9037/#9695) — reflects fragility in provider-agnostic streaming handling.
- **CLI cron examples broken:** All three `cron add` help examples fail (issue #9672) — signals documentation/test gaps in core CLI surface.
- **Config race conditions:** Concurrent gateway config writes could silently overwrite each other (fixed in #9519) — enterprise operators depend on config reliability.
- **Skill injection bloat:** Full-mode skill injection consuming excessive prompt context (addressed by #8313 defaulting to compact) — users are running into context limits.
- **Model discovery gaps:** No structured way to compare local models by hardware requirements, quantization, and tool support (RFC #9549) — community self-organizing around this need.

**Satisfaction signals:** Strong contributor engagement (49 contributors in v0.8.4), active security remediation, and responsive maintainer closures on bug fixes.

---

## 8. Backlog Watch

| Issue | Reason for Concern |
|-------|-------------------|
| [#9690](https://github.com/zeroclaw-labs/zeroclaw/issues/9690) | `all-features` Docker build broken since 2026-07-08; blocks CI for users relying on container variants |
| [#9624](https://github.com/zeroclaw-labs/zeroclaw/issues/9624) | WIT registry pin divergence breaks published plugin components — ecosystem-impacting |
| [#9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) | P0 security bug: unauthenticated webhook dispatch on WhatsApp Cloud and Linq (WATI removed, but two surfaces remain open) |
| [#9672](https://github.com/zeroclaw-labs/zeroclaw/issues/9672) | All `cron add` examples in CLI help are broken — affects every new user following documentation |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) | Pluggable auth RFC at Rev 6 with no implementation — P1 security architecture item |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | Chat Completions RFC at 15 comments with no merged PR — high-demand interoperability feature |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) | Goal mode RFC — no implementation PR yet; key differentiator for autonomous agent use cases |

**Maintainer attention needed:** The RFC decision queue tracker [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) explicitly calls out that multiple high-value RFCs are awaiting maintainer acceptance/rejection/deferral decisions. The v0.9.0 security architecture (#7141, #7142) and the Chat Completions profile (#8603) are the highest-impact items in this queue.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*