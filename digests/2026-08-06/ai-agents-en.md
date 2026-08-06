# OpenClaw Ecosystem Digest 2026-08-06

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-06 03:16 UTC

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



# OpenClaw Project Digest — 2026-08-06

## 1. Today's Overview

OpenClaw continues to demonstrate high engineering velocity with **1,000 issues and PRs updated in the last 24 hours** (500 each), of which **426 issues remain open/active** and **435 PRs are open**, indicating a heavily active and somewhat backlogged repository. No new releases were published today, though multiple P0 and P1 bug fixes are in-flight. The project's maintainers are focused on session-state reliability, crash-loop remediation, and infrastructure hardening (timeouts, state migrations, audit tracing). The overall health signal is **high activity with elevated bug density**, particularly around session management, message delivery, and provider auth flows.

---

## 2. Releases

**No new releases published today.**

---

## 3. Project Progress

### Merged / Closed PRs (last 24h)
- **#119146** — `fix(scripts): bound gh-read gh CLI child process` — adds configurable timeout to prevent stalled `gh` invocations from hanging CI jobs indefinitely.
- **#110601** — `fix(scripts): bound ci-run-timings git and GitHub CLI operations` — guards `git ls-remote` against indefinite network stalls.
- **#118846** (closed) — Gateway main thread CPU saturation from plugin-metadata snapshotting mitigated; root cause identified as fs statting under load.
- **#106779** (closed) — Local llama.cpp provider regression fixed (400 parser error on certain templates).
- **#92369** (closed) — Subagent cron orchestration issue addressed.
- **#119090** (closed) — Managed media cleanup crash-on-unreadable-store fixed.
- **#91564** (closed) — Telegram forum-topic black-hole after stuck-session recovery fixed.
- **#38076** (closed) — `init_skill --resources` case-sensitivity bug fixed.

### Key Open PRs Advancing Today
- **#119221** — `fix(sessions): reject a transcript turn when the session id rotates mid-append` — addresses silent data corruption when concurrent resets race with transcript writes. High merge risk to session state.
- **#119326** — `fix(agents): honor account-scoped history limits instead of silently ignoring them` — P1 compatibility fix; account-level `historyLimit` configs were being dropped.
- **#82572** — `feat(queue): persist followup queues across gateway restarts` — large-scale feature making in-progress turn followup messages survive gateway restarts via SQLite persistence.
- **#116489** — `feat(security): require acknowledgement for install policy warnings` — closes a security boundary gap where `warn`-level policy responses were treated as allowed.
- **#119516** — `fix(update): recover the managed gateway after a failed CLI update` — P1 availability fix for failed `openclaw update` rollbacks.
- **#119810** — `feat(ui): add durable Activity run inspector` — read-only `/activity?view=run&run=<id>` backed by F0 audit projection.
- **#119791** — `fix(diagnostics): prevent duplicate and leaked lifecycle spans` — OTEL tracing fix for blocked tool execution paths.

---

## 4. Community Hot Topics

| Rank | Issue | Comments | Theme |
|------|-------|----------|-------|
| 1 | [#116201](https://github.com/openclaw/openclaw/issues/116201) | 58 | Realtime voice state retention / resource bounds |
| 2 | [#7707](https://github.com/openclaw/openclaw/issues/7707) | 27 | Memory trust tagging by source (security feature) |
| 3 | [#44925](https://github.com/openclaw/openclaw/issues/44925) | 25 | Subagent completion silently lost on timeout |
| 4 | [#118846](https://github.com/openclaw/openclaw/issues/118846) | 19 | Gateway main thread CPU saturation at boot |
| 5 | [#86519](https://github.com/openclaw/openclaw/issues/86519) | 13 | Telegram duplicate replies regression (2-10x) |

**Analysis:** The community's top concerns cluster around **reliability of long-running sessions** (voice state, subagent completion loss, gateway saturation) and **security hardening** (memory trust tagging, install policy acknowledgement). The high-comment issues (#116201, #44925) indicate repeated user encounters with non-deterministic session behavior — a strong signal that session-state correctness is the project's most pressing engineering challenge.

---

## 5. Bugs & Stability

### P0 / Critical
| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#119263](https://github.com/openclaw/openclaw/issues/119263) | DB v14→v15 migration fails with `no such column: entry_valid`; gateway refuses to start | None yet |
| [#119090](https://github.com/openclaw/openclaw/issues/119090) (closed) | Media cleanup deletes entire session's generated media on unreadable store | ✅ Closed |
| [#118846](https://github.com/openclaw/openclaw/issues/118846) (closed) | Gateway thread pegged at 100% CPU from plugin-metadata snapshotting | ✅ Fixed |

### P1 High
| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | Realtime voice retains unbounded provider/consult state | #119221 (related) |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent completion silently lost; no retry/notification | In discussion |
| [#86519](https://github.com/openclaw/openclaw/issues/86519) | Telegram duplicate replies after 5.20 regression | #119501 (related ack fix) |
| [#113306](https://github.com/openclaw/openclaw/issues/113306) | SQLite snapshot restore lacks crash/identity guarantees | None yet |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | Large transcript cleanup blocks gateway event loop | None yet |
| [#109490](https://github.com/openclaw/openclaw/issues/109490) | Client-delegated tool result causes turn interruption, work never executes | None yet |
| [#106231](https://github.com/openclaw/openclaw/issues/106231) | Loop detection blocks exec but doesn't terminate stuck run | None yet |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Child process leak (zombies) causing runtime degradation | None yet |
| [#107873](https://github.com/openclaw/openclaw/issues/107873) | Embedded prompt-lock takeover aborts visible WebChat turns | None yet |
| [#115642](https://github.com/openclaw/openclaw/issues/115642) | Billing cooldown outlives provider outage; no probe-based recovery | #70903 (related, open) |
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | Persistent file-based provider cooldown blocks user hours after billing recovery | In discussion |
| [#119401](https://github.com/openclaw/openclaw/issues/119401) | NO_REPLY suppression unconditional; ignores `silentReply` policy | None yet |

### P2 Medium
| Issue | Summary |
|-------|---------|
| [#51429](https://github.com/openclaw/openclaw/issues/51429) | Hardcoded working path (`/Users/wangtao`) merged into release |
| [#67419](https://github.com/openclaw/openclaw/issues/67419) | Session context bloat: bootstrap files re-injected every turn (20-30% token waste) |
| [#53540](https://github.com/openclaw/openclaw/issues/53540) | Embedded runner "Network connection lost" on large tool-call parameters |
| [#85844](https://github.com/openclaw/openclaw/issues/85844) | Auto-update leaves stale hashed bundle imports in memory |
| [#117609](https://github.com/openclaw/openclaw/issues/117609) | Transient LLM/socket errors not retried at embedded-assistant stage |
| [#46031](https://github.com/openclaw/openclaw/issues/46031) | `auth.order` ignored for GitHub Copilot provider |
| [#106786](https://github.com/openclaw/openclaw/issues/106786) | `gpt-5.6-*` advertised then silently falls back on rejection |
| [#116512](https://github.com/openclaw/openclaw/issues/116512) | Telegram progress duplicates first commentary when snapshot IDs change |
| [#117471](https://github.com/openclaw/openclaw/issues/117471) | `openclaw cron remove` reports "id not found" after successful removal |
| [#77306](https://github.com/openclaw/openclaw/issues/77306) | QQBot duplicate message sending via `message_sending` hook |

**Stability Assessment:** The project is experiencing a **high bug load concentrated in session-state, message delivery, and provider-auth paths**. The P0 DB migration blocker (#119263) and the ongoing child-process leak (#97616) are the most impactful unresolved stability concerns. Several regression bugs trace back to the 2026.5.x–2026.7.x release window, suggesting that release-branch testing coverage may be insufficient for session-concurrency edge cases.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood |
|-------|-------------|------------|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) (27 comments) | Memory trust tagging by source — tag entries by origin trust level to prevent memory poisoning | **High** — directly addresses security concern; linked to `clawsweeper:needs-security-review` |
| [#6615](https://github.com/openclaw/openclaw/issues/6615) (11 comments, 8 👍) | Denylist support for exec-approvals — "allow all except X" policy | **Medium-High** — complements existing allowlist; low implementation risk |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) (9 comments, 10 👍) | MathJax/LaTeX rendering in Control UI | **Medium** — UI polish, popular but low priority vs. stability |
| [#16555](https://github.com/openclaw/openclaw/issues/16555) (6 comments) | TTL/expiry for delivery queue messages | **Medium** — practical ops need; prevents stale-orphaned queue entries |
| [#53654](https://github.com/openclaw/openclaw/issues/53654) (6 comments, 3 👍) | Discord `messageUpdate`/`messageDelete` event support | **Medium** — requested by enterprise user (ScaleWithSystem) |
| [#13597](https://github.com/openclaw/openclaw/issues/13597) (7 comments, 4 👍) | Comprehensive AWS deployment guide (EC2, ECS, Lambda) | **Medium** — documentation request, low engineering cost |
| [#41965](https://github.com/openclaw/openclaw/issues/41965) (5 comments) | Force media delivery as document attachment (`#doc`) | **Low-Medium** — niche but useful for quality-sensitive workflows |
| [#53562](https://github.com/openclaw/openclaw/issues/53562) (5 comments, 1 👍) | Discord voice `sessionChannelId` for text-channel transcript routing | **Low-Medium** — voice-text cross-channel use case |

**Roadmap Prediction:** The next release will likely prioritize **session-state reliability fixes** (#119221, #119326, #82572) and **security hardening** (#116489, #7707). The durable Activity run inspector (#119810) and queue persistence (#82572) are strong candidates for inclusion. Memory trust tagging (#7707) is notable as a potential differentiator but may require a separate design phase.

---

## 7. User Feedback Summary

**Pain Points:**
- **Session state corruption and data loss** — Multiple users report silent message loss, duplicate replies, and subagent result disappearances (#44925, #86519, #96692, #109490). This is the dominant complaint theme.
- **Billing auth lockouts** — Users are stuck for hours after temporary billing errors due to persistent cooldown state (#70903, #115642), creating high frustration even after credit is restored.
- **Provider selection bugs** — `auth.order` ignored (#46031), model advertised but silently fallen back (#106786), and local llama.cpp parser failures (#106779) erode trust in provider configuration.
- **Child process leaks** — Zombie accumulation degrades runtime over hours/days (#97616), particularly affecting long-running cron and embedded-agent workflows.
- **Migration breakage** — The v14→v15 DB migration failure (#119263) prevents upgrades entirely for affected users, a severe operational blocker.
- **Hardcoded paths in release** — A developer's local path (`/Users/wangtao`) was merged and published (#51429), damaging confidence in review processes.

**Positive Signals:**
- The community actively engages with maintainers (high comment counts, reproductions provided).
- Several bugs have closed PRs or in-flight fixes, showing responsive maintainer activity.
- Feature requests with strong upvotes (#42840 with 10 👍, #6615 with 8 👍) indicate an engaged power-user base.

---

## 8. Backlog Watch

| Issue | Age | Severity | Blocker |
|-------|-----|----------|---------|
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | ~7 days | P1 🦞 diamond lobster | `clawsweeper:needs-product-decision`, `needs-maintainer-review` |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | ~25 days | P1 🦞 diamond lobster | `source-repro`, `needs-maintainer-review` |
| [#113306](https://github.com/openclaw/openclaw/issues/113306) | ~13 days | P1 🦐 gold shrimp | `needs-maintainer-review` |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | ~38 days | P1 🦪 silver shellfish | No fix PR; regression |
| [#119263](https://github.com/openclaw/openclaw/issues/119263) | ~2 days | P0 🦞 diamond lobster | **Gateway refuses to start** — no fix PR yet |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | ~16 days | P1 🦞 diamond lobster | `source-repro` |
| [#106231](https://github.com/openclaw/openclaw/issues/106231) | ~24 days | P1 🦞 diamond lobster | `clawsweeper-recovery-stuck` |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | ~185 days | P2 🌊 off-meta tidepool | `needs-security-review`, `needs-product-decision` |
| [#6615](https://github.com/openclaw/openclaw/issues/6615) | ~186 days | P2 🌊 off-meta tidepool | `needs-security-review`, `needs-product-decision` |
| [#70903](https://github.com/openclaw/openclaw/issues/70903) | ~104 days | P0 🦞 diamond lobster | `stale` — persistent billing cooldown, no fix merged |

**Critical Backlog Items:**
- **#119263** (P0) — DB migration blocker with no fix PR; new installs from 2026.7.1→

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: Open-Source AI Agent & Personal Assistant Ecosystem
**Date: 2026-08-06**

---

## 1. Ecosystem Overview

The open-source personal AI assistant landscape is in a high-velocity consolidation phase, with projects converging on session reliability, security hardening, and multi-channel delivery as foundational requirements. Nine of ten tracked projects shipped meaningful activity in the past 24 hours, but stability debt from rapid feature iteration is becoming a visible across the board — particularly around session-state correctness, MCP tool reliability, and containerized deployment friction. The ecosystem is splitting along architectural lines: heavyweight gateways (OpenClaw, IronClaw, Hermes) pursuing multi-tenant extensibility versus focused runtimes (NullClaw, PicoClaw) prioritizing reliability and simplicity.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release | Health Signal |
|---|---|---|---|---|
| **OpenClaw** | ~1,000 updated (500 active) | ~1,000 (435 open) | None | 🔴 High activity, elevated bug density |
| **Hermes Agent** | 50 (45 open) | 50 (46 open) | v0.20.0 (Aug 3) | 🟡 High velocity, regression backlog |
| **IronClaw** | 44 | 50 | v1.1.0-rc.1 (Aug 3) | 🟢 Active and progressing |
| **CoPaw** | 22 (14 open) | 50 (28 open) | None | 🟢 High velocity, strong engagement |
| **NanoClaw** | 2 active | 12 | None | 🟢 Strong contributor momentum |
| **ZeroClaw** | ~50 (40 open) | ~50 (40 open, 1 merged) | None | 🟢 Active consolidation |
| **NanoBot** | 4 | 14 (9 open) | None | 🟡 Active, new critical regression |
| **LobsterAI** | 3 open | 11 (10 merged) | v2026.8.5 (Aug 5) | 🟡 Responsive but stale bug #1200 |
| **PicoClaw** | 0 | 4 | None | 🟡 Moderate, stabilization phase |
| **NullClaw** | 0 closed | 2 open | None | 🟡 Low but focused maintenance |
| **Moltis** | 0 | 0 | — | 🔴 Inactive |

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Scale and velocity** — OpenClaw processes ~1,000 issue/PR updates per day, an order of magnitude above most peers, reflecting the largest active contributor base.
- **Session-state depth** — The project has the most sophisticated session persistence work in-flight (durable activity inspector, queue persistence across restarts, transcript corruption guards), which most competitors lack entirely.
- **Provider ecosystem breadth** — deepest multi-provider support (Telegram, WhatsApp, Matrix, Discord, QQBot, local llama.cpp) with active auth-flow hardening.

**Technical Approach Differences:**
- Unlike IronClaw (extension/MCP-first, multi-tenant) or ZeroClaw (RFC-governed, policy-driven), OpenClaw focuses on **gateway reliability and infra hardening** — timeouts, audit tracing, state migrations.
- Unlike NullClaw's minimal runtime or PicoClaw's OAuth-focused simplicity, OpenClaw embraces **complexity management** through architectural refactors (god-file sharding, OTEL tracing).

**Community Size:** OpenClaw's issue/PR volume and the depth of its backlog (185+ day stale items on security features) suggest the largest community, though also the most demanding user base.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects | Specific Need |
|---|---|---|
| **Session-state reliability** | OpenClaw, Hermes, ZeroClaw | Silent message loss, subagent completion drops, cross-session mixing under load |
| **MCP tool reliability** | NanoBot, CoPaw, NanoClaw, LobsterAI | MCP error envelopes ignored (NanoBot #5237), periodic tool failures requiring restart (CoPaw #6732), server connection instability |
| **Multi-channel delivery** | OpenClaw, IronClaw, NanoClaw, ZeroClaw, CoPaw | Cross-channel message leakage (IronClaw #7249), container media isolation (NanoClaw #2528), WhatsApp session hangs |
| **Security hardening** | OpenClaw, ZeroClaw, IronClaw | Memory trust tagging (OpenClaw #7707), SSRF gates (ZeroClaw #8713, #8826), sandbox profiles (IronClaw #7214), credential URL leaks (NanoBot #5258) |
| **Container/deployment friction** | NanoClaw, NullClaw, CoPaw | Docker socket permissions on LXC (NanoClaw #2006), stack overflows in long-running agents (NullClaw #976), shell process detachment (CoPaw #6480) |
| **Model routing & fallback** | PicoClaw, CoPaw, ZeroClaw | Configurable fallback chains (PicoClaw #3200), automatic per-message model selection (CoPaw #6436), provider-specific parser gaps (ZeroClaw DeepSeek DSML) |
| **Billing/auth lockouts** | OpenClaw, ZeroClaw | Persistent cooldown after billing recovery (OpenClaw #70903), SOP no-network capability (ZeroClaw #9780) |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | IronClaw | ZeroClaw | CoPaw | NanoBot | NanoClaw | NullClaw | PicoClaw | LobsterAI |
|---|---|---|---|---|---|---|---|---|---|---|
| **Architecture** | Gateway + session state | Modular, god-file shard campaign | Extension/MCP-first, multi-tenant | RFC-governed, policy-heavy | AgentScope-integrated, model-routing | WebUI-centric, rapid iteration | Skill-oriented, DB-invariant focused | Minimal runtime, channel-agnostic | Lightweight, OAuth-focused | Desktop/enterprise CLI |
| **Target User** | Power users, multi-channel operators | Developers wanting extensibility | Enterprise multi-tenant admins | Security-conscious operators | Chinese-market users (DingTalk, WeChat) | Developers, MCP adopters | Container/Proxmox deployers | Embedded/edge runtime users | OAuth-preference users | Enterprise (NIM, cowork) |
| **Key Differentiator** | Session persistence depth | AIDE² self-improvement engine | IronHub marketplace, sandbox profiles | Pluggable auth, shell confirmation tiers | Auto model routing, i18n depth | Meta-search (MST), temporary chat | Skill modularity, agent-to-agent messaging | Stack/timeout reliability | OAuth flexibility, fallback chains | Enterprise auth isolation, daily check-in |
| **Release Cadence** | Patch-heavy, no tagged release | v0.20.0 (Aug 3), regression-prone | v1.1.0-rc.1 (Aug 3) | Steady RFC-driven | Incremental, no tagged release | Rapid (Aug 5) | None | None | None | Stable releases |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (High Velocity, High Risk):**
- **OpenClaw** — Massive throughput but elevated bug density; session-state correctness remains the bottleneck.
- **Hermes Agent** — 50 issues/PRs daily with a major refactor (god-file sharding) running in parallel with hot-fix deployment. v0.20.0 regressions suggest release discipline needs strengthening.
- **CoPaw** — 22 issues/50 PRs with strong contributor engagement; MCP and shell reliability are the current friction points.
- **ZeroClaw** — 50/50 activity with mature RFC governance; moving from feature proliferation to security consolidation.

**Tier 2 — Sustained Growth (Steady, Focused):**
- **IronClaw** — Released rc.1, actively addressing v1.1.0 feature set; backlog of trust/accuracy bugs needs triage.
- **NanoClaw** — Strong contributor base building skills and channels; container deployment gaps are the main drag.
- **NanoBot** — Rapid WebUI feature shipping but the goal-loop regression (#5256) signals the need for stability gates before the next release.
- **LobsterAI** — Responsive maintainer team with daily merges; stale bug #1200 (open since April) indicates triage discipline drift.

**Tier 3 — Stabilization / Maintenance:**
- **PicoClaw** — Low activity, focused on infrastructure (lockfile, fallback chains). Maturing rather than growing.
- **NullClaw** — Small team, targeted reliability fixes. Sustainable but limited scope for expansion.
- **Moltis** — Inactive; effectively dormant.

---

## 7. Trend Signals

1. **Session-state correctness is the ecosystem's weakest link.** Every major project reported silent message loss, duplicate replies, or subagent result disappearance. This is the #1 trust barrier for production adoption.

2. **MCP reliability is table-stakes, not a differentiator.** Four projects (NanoBot, CoPaw, NanoClaw, LobsterAI) reported MCP tool failures. The community expects "it just works" — intermittent failures requiring container restarts are unacceptable.

3. **Security hardening is driving architecture, not tacked on.** ZeroClaw's pluggable auth RFC, OpenClaw's memory trust tagging, and IronClaw's sandbox profiles show security is becoming a first-class design concern rather than a post-release fix.

4. **Container deployment friction is a major onboarding barrier.** NanoClaw's LXC Docker permissions (#2006) and Signal media isolation (#2528), plus NullClaw's stack overflow (#976), indicate that "works on my machine" is a real ecosystem problem. Projects that solve this will win the self-hosted market.

5. **Model routing and fallback chains are emerging requirements.** PicoClaw's fallback chains, CoPaw's auto-routing, and ZeroClaw's provider-specific parser fixes all point to users running multi-model workflows where reliability trumps single-model optimization.

6. **Governance maturity is separating projects.** ZeroClaw's RFC ratification process and IronClaw's Configuration-as-Code epic signal that operational users are demanding auditability and declarative management — not just feature lists.

7. **The "desktop viewer" pattern is fading.** OpenClaw's activity inspector, Hermes' minimized-to-tray, and CoPaw's artifact canvas all reflect a shift toward persistent, operational tooling rather than chat-only interfaces.

**Value for AI Agent Developers:** The projects with the strongest trajectories combine **session reliability** (OpenClaw's queue persistence, ZeroClaw's goal mode) with **security-by-design** (ZeroClaw's SSRF gates, IronClaw's sandbox profiles). Developers evaluating a foundation should prioritize projects that treat stability as a feature, not an afterthought — currently ZeroClaw and OpenClaw lead on this axis despite their complexity.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-06

## 1. Today's Overview

NanoBot shows active development momentum with **14 PRs updated** (9 open, 5 closed/merged) and **4 open issues** in the last 24 hours, though no new release was published. The project is in a dense integration and hardening phase: multiple WebUI features (temporary chat, shared terminal, quick chat) are being spun up in parallel, security/cred-handling fixes landed today, and a new metasearch provider was merged. Stability concerns remain — three new bugs were opened today, including a severe infinite-loop regression tied to sustained-goal handling, suggesting the goal system needs continued refinement before the next release.

---

## 2. Releases

No new releases published today. The last visible closed PRs ([#5234](https://github.com/HKUDS/nanobot/pull/5234), [#5254](https://github.com/HKUDS/nanobot/pull/5254), [#5203](https://github.com/HKUDS/nanobot/pull/5203), [#5184](https://github.com/HKUDS/nanobot/pull/5184), [#5249](https://github.com/HKUDS/nanobot/pull/5249)) will likely ship together in the next version, but no release is tagged yet.

---

## 3. Project Progress

**Merged / Closed PRs today:**

| PR | Type | Summary |
|---|---|---|
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) | ✅ Merged | Meta-search provider (mst-python) integrated — aggregates DuckDuckGo, Google, Brave, Bing via Reciprocal Rank Fusion ([priority: p1](https://github.com/HKUDS/nanobot/pull/5234)) |
| [#5254](https://github.com/HKUDS/nanobot/pull/5254) | ✅ Closed | Provider-native request switches added to WebUI (OpenAI Codex Fast mode, web search tools, xAI Grok X Search) ([priority: p2](https://github.com/HKUDS/nanobot/pull/5254)) |
| [#5203](https://github.com/HKUDS/nanobot/pull/5203) | ✅ Closed | WhatsApp outbound media detection improved — detects content via libmagic instead of trusting file extensions, maps unsupported audio to document mode ([priority: p2](https://github.com/HKUDS/nanobot/pull/5203)) |
| [#5184](https://github.com/HKUDS/nanobot/pull/5184) | ✅ Closed | Quick Chat + Temporary Chat WebUI feature (conflicted with #5252 — see open PRs) ([priority: p2](https://github.com/HKUDS/nanobot/pull/5184)) |
| [#5249](https://github.com/HKUDS/nanobot/pull/5249) | ✅ Closed | WebUI visual consistency refactor — elevation system, flattened layouts, removed replay animations on persisted messages ([priority: p2](https://github.com/HKUDS/nanobot/pull/5249)) |

**Notable open PRs awaiting review/merge:**
- [#5252](https://github.com/HKUDS/nanobot/pull/5252) — Temporary Chat mode (stacked on #5259 for memory isolation)
- [#5261](https://github.com/HKUDS/nanobot/pull/5261) — Drag sessions into composer mentions (WebUI UX)
- [#5253](https://github.com/HKUDS/nanobot/pull/5253) — Shared interactive project terminal (persistent PTY dock)
- [#5257](https://github.com/HKUDS/nanobot/pull/5257) — Fix for goal-continuation unbounded loop (direct response to #5256)
- [#5258](https://github.com/HKUDS/nanobot/pull/5258) — Credential URL security fix for Jina reader ([priority: p1](https://github.com/HKUDS/nanobot/pull/5258))

---

## 4. Community Hot Topics

1. **[Issue #5149 — WhatsApp audio not sent](https://github.com/HKUDS/nanobot/issues/5149)** · 4 comments · Updated 2026-08-05
   - Users can receive but not send audio on WhatsApp. Fix PR [#5203](https://github.com/HKUDS/nanobot/pull/5203) has already been merged, which should resolve this. This issue saw the highest comment count in the current window.

2. **[Issue #5256 — /goal produces dozens of repeated replies](https://github.com/HKUDS/nanobot/issues/5256)** · Created 2026-08-05
   - A sustained-goal session can loop unboundedly when waiting for user input, burning tokens and sending near-identical messages. Fix PR [#5257](https://github.com/HKUDS/nanobot/pull/5257) directly addresses this by bounding continuation cycles.

3. **[Issue #5237 — MCP tool error envelope ignored](https://github.com/HKUDS/nanobot/issues/5237)** · 2 comments · Updated 2026-08-05
   - When an MCP server returns a business-error JSON envelope (`isError=False`), nanobot treats it as success and the LLM never retries. No fix PR yet — this is a live gap between MCP spec compliance and nanobot's error handling.

4. **[PR #5251 — MCP Apps host support in WebUI](https://github.com/HKUDS/nanobot/issues/5251)** · Open enhancement
   - Users want MCP server UIs (the `io.modelcontextprotocol/ui` extension) to be rendered inside the nanobot WebUI, not just tool-call results. This reflects growing adoption of the MCP Apps standard and community desire for richer in-app MCP integration.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| 🔴 Critical | [#5256](https://github.com/HKUDS/nanobot/issues/5256) | `/goal` message causes unbounded repeat-loop of near-identical replies during idle waits, consuming tokens | [#5257](https://github.com/HKUDS/nanobot/pull/5257) (open, pending) |
| 🟠 High | [#5237](https://github.com/HKUDS/nanobot/issues/5237) | MCP tools returning error envelopes with `isError=False` are silently treated as successful calls | None yet |
| 🟡 Medium | [#5149](https://github.com/HKUDS/nanobot/issues/5149) | WhatsApp cannot send audio messages (fixed by merged [#5203](https://github.com/HKUDS/nanobot/pull/5203)) | ✅ [#5203](https://github.com/HKUDS/nanobot/pull/5203) merged |

**Security note:** PR [#5258](https://github.com/HKUDS/nanobot/pull/5258) ([priority: p1](https://github.com/HKUDS/nanobot/pull/5258)) closes a cred-leak vector where URLs containing tokens or userinfo were forwarded to the remote Jina reader — currently open for review.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Likelihood for Next Release |
|---|---|---|
| Temporary / Quick Chat mode | [#5252](https://github.com/HKUDS/nanobot/pull/5252), [#5184](https://github.com/HKUDS/nanobot/pull/5184), [#5259](https://github.com/HKUDS/nanobot/pull/5259) | **High** — already coded, stacked, and partially merged |
| Provider-native request switches (Fast mode, web search, X Search) | [#5254](https://github.com/HKUDS/nanobot/pull/5254) | **High** — merged |
| Meta-search provider (MST) | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | **High** — merged |
| Shared interactive project terminal | [#5253](https://github.com/HKUDS/nanobot/pull/5253) | **Medium** — open, p2 priority, larger scope |
| MCP Apps host rendering in WebUI | [#5251](https://github.com/HKUDS/nanobot/issues/5251) | **Low–Medium** — enhancement, no PR yet |
| Drag sessions into composer mentions | [#5261](https://github.com/HKUDS/nanobot/pull/5261) | **Medium** — open, p2 priority |
| Truthful API status for externally-managed servers | [#5255](https://github.com/HKUDS/nanobot/pull/5255) | **Medium** — draft PR, small scope |

The next release is likely to emphasize WebUI polish (temporary chat, terminal dock, visual redesign) and provider flexibility, with the security/cred fix also landing.

---

## 7. User Feedback Summary

- **WhatsApp audio sending** remains a pain point ([#5149](https://github.com/HKUDS/nanobot/issues/5149)), though the merged fix [#5203](https://github.com/HKUDS/nanobot/pull/5203) should resolve it. Users want media to work reliably across all WhatsApp types.
- **MCP error handling** is a significant frustration ([#5237](https://github.com/HKUDS/nanobot/issues/5237)). Agents that silently swallow MCP business errors are unreliable in production workflows — users expect the LLM to see failures and self-correct.
- **Goal-loop regression** ([#5256](https://github.com/HKUDS/nanobot/issues/5256)) caused token burn and spammy behavior. Users reported having to manually intervene, which damages trust in the sustained-goal feature.
- **WebUI improvements** (temporary chat, shared terminal, drag-to-mention) show users are investing heavily in local, project-scoped workflows and want a more integrated desktop-like experience.
- **Security-conscious users** appreciate the credential-URL fix ([#5258](https://github.com/HKUDS/nanobot/pull/5258)) — a clear signal that users are exposing nanobot to internal/credential-protected services and expect safe handling.

---

## 8. Backlog Watch

| Item | Reason | Link |
|---|---|---|
| [Issue #5237](https://github.com/HKUDS/nanobot/issues/5237) | MCP error-envelope bug, no fix PR yet — blocks reliable MCP tool use | [link](https://github.com/HKUDS/nanobot/issues/5237) |
| [PR #5257](https://github.com/HKUDS/nanobot/pull/5257) | Critical loop fix for goal continuation, still open | [link](https://github.com/HKUDS/nanobot/pull/5257) |
| [PR #5258](https://github.com/HKUDS/nanobot/pull/5258) | Credential URL security fix, p1 priority, awaiting review | [link](https://github.com/HKUDS/nanobot/pull/5258) |
| [PR #5248](https://github.com/HKUDS/nanobot/pull/5248) | Matrix/Continuwuity compatibility fix, p2, open since Aug 4 | [link](https://github.com/HKUDS/nanobot/pull/5248) |
| [PR #5260](https://github.com/HKUDS/nanobot/pull/5260) | Memory runtime-file filtering, backportable, open | [link](https://github.com/HKUDS/nanobot/pull/5260) |
| [PR #5253](https://github.com/HKUDS/nanobot/pull/5253) | Shared interactive terminal — larger feature, still open and unmerged | [link](https://github.com/HKUDS/nanobot/pull/5253) |

**Key risk:** The unbounded goal-loop bug (#5256 / #5257) is the most pressing stability concern. If the fix PR does not land before the next release, users running sustained-goal sessions risk token waste and spam behavior. The MCP error-handling gap (#5237) is the second priority — it affects any user relying on MCP tools in production.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-06

## 1. Today's Overview

Hermes Agent is experiencing **very high development velocity**, with 50 issues and 50 PRs updated in the last 24 hours. Activity is predominantly open-ended (45 open issues, 46 open PRs), indicating a strong pipeline of ongoing work rather than release-candidate stabilization. No new version was shipped today. The project is simultaneously advancing a major architecture initiative (god-file sharding across 20 files), pushing Telegram Bot API 10.2 feature parity, and triaging several P1/P2 regressions from the recent v0.20.0 release. The dual focus on deep refactoring and hot-fix deployment suggests a healthy but busy maintainer team managing technical debt alongside user-facing stability.

---

## 2. Releases

**No new releases today.** The latest tagged release remains **v0.20.0 ("The Herald Release", 2026-08-03)**, which is now the source of multiple regression reports (see Bugs & Stability).

---

## 3. Project Progress

**Closed/Merged Today:**
- **PR #53525** (closed) — `fix(gateway): preserve rebound ws sessions during teardown` — resolves a WebSocket reconnect race condition.
- **PR #61326** (closed) — `fix(agent): centralize bounded model fallback` — unifies fallback logic across foreground and worker contexts.
- **Issue #74560** (closed) — Fixed desktop double-render bug caused by `interimBoundaryPending` flag reset.
- **Issue #79820** (closed as duplicate) — DeepSeek native `web_search` via Responses API; feature request acknowledged but deferred.

**Features Advancing:**
- **AIDE² Self-Evaluation Engine** (PR #77236, open) — 5-phase self-improvement loop (Signal → Ledger → LLM verification → LLM improvement) with 198 passing tests and clean CI.
- **God-File Sharding Campaign** (Issue #78647, epic) — Repo-wide decomposition of 20 god files into clean modules; standing policy enforces "never revert."
- **Telegram Feature Parity & Alignment** (Issue #78791, meta-issue) — Batch of ~10 duplicate sub-issues covering Bot API 10.2 features (paid broadcasts, link previews, reactions, forwarding, batch deletes, admin rights).
- **Minimize-to-Tray** (PR #79803, open) — Opt-in Win/Linux tray behavior for desktop.

---

## 4. Community Hot Topics

| # | Title | Comments | Type | Link |
|---|-------|----------|------|------|
| **#78647** | Epic: Shard all 20 god files — repo-wide god-file decomposition | **17** | Refactor / P3 | [Issue](https://github.com/NousResearch/hermes-agent/issues/78647) |
| **#77780** | lifecycle_guard crashes on `ValueError: embedded null byte` from os.open | **12** | Bug / P2 | [Issue](https://github.com/NousResearch/hermes-agent/issues/77780) |
| **#54962** | Extract Gateway Platform Routing from gateway/run.py | **11** | Refactor / P3 | [Issue](https://github.com/NousResearch/hermes-agent/issues/54962) |
| **#71941** | Delegated child context persists through shared terminal snapshots | **5** | Bug / P2 | [Issue](https://github.com/NousResearch/hermes-agent/issues/71941) |
| **#78791** | Telegram Feature Parity & Alignment Campaign (Bot API 10.2) — meta-issue | **5** | Feature / P3 | [Issue](https://github.com/NousResearch/hermes-agent/issues/78791) |

**Analysis:**
- The **god-file sharding epic** dominates discussion (17 comments), reflecting community appetite for improved codebase maintainability. The 5×2×3 methodology and "kill-lock" doctrine are generating engaged architectural debate.
- The **lifecycle_guard crash** (#77780) and **gateway routing extraction** (#54962) both attract high comment counts, signaling that users are actively impacted by terminal-command scanning and gateway monolith complexity.
- The **Telegram campaign** (#78791) shows strong community interest in platform parity, with numerous sub-features being tracked in parallel.

---

## 5. Bugs & Stability

**P1 (Critical):**

| Issue | Summary | Fix PR | Link |
|-------|---------|--------|------|
| **#79407** | v0.20.0 regression — Desktop bottom operation panel completely missing (viewer-only shell) | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/79407) |
| **#78574** | Linux default gateway stays stale after `hermes update`, causing ImportError (Telegram) | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/78574) |

**P2 (High):**

| Issue | Summary | Fix PR | Link |
|-------|---------|--------|------|
| **#77780** | `lifecycle_guard` crashes on `ValueError: embedded null byte` — breaks all terminal commands | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/77780) |
| **#71941** | Delegated child context persists through shared terminal snapshots | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/71941) |
| **#79562** | WeChat `/approve` text fallback stops working after first approval (timing race) | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/79562) |
| **#79220** | Cost labels at 2dp show `$0.00` for sub-cent-per-turn models | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/79220) |
| **#79459** | Local TTS providers (Piper, KittenTTS) ignore configured voice | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/79459) |
| **#79853** | v0.20.0 macOS: high resource usage + cross-session message mixing under load | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/79853) |
| **#79841** | Feishu DM Allow button gated by group policy instead of admins list | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/79841) |
| **#79101** | API server stores virtual model alias as real model, breaking gateway default | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/79101) |

**Fix PRs Open (not yet merged):**
- **PR #79864** — Fixes desktop new-session terminal pane collapse regression
- **PR #79857** — Suppress internal errors on customer-facing channels (SMS)
- **PR #79412** — Fix Signal typing indicators (8s cadence issue)
- **PR #79861** — Make Hindsight prefetch wait configurable
- **PR #79862** — Fix per-model image input for kimi-coding (kimi-k3 multimodal)
- **PR #79799** — Fix Slack free-response channel acknowledgment
- **PR #79851** — Surface iLink business errors on WeChat media sends

**Assessment:** The v0.20.0 release has introduced **multiple regressions** (desktop panel missing, macOS resource spike, message mixing). The P1 gateway staleness bug on Linux post-update is particularly concerning for production users. Several fix PRs are open but unmerged, creating a growing backlog of critical stability work.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Link | Likelihood for Next Release |
|---------|----------|------|----------------------------|
| Desktop minimize-to-tray (opt-in, Win/Linux) | PR #79803 | [PR](https://github.com/NousResearch/hermes-agent/pull/79803) | **High** — small, self-contained, already implements toggle |
| Configurable desktop composer/conversation width | Issue #79856 | [Issue](https://github.com/NousResearch/hermes-agent/issues/79856) | Medium — CSS variable change, low risk |
| Independent conversation font-size setting | Issue #79858 | [Issue](https://github.com/NousResearch/hermes-agent/issues/79858) | Medium — pairs with above |
| Pop-out preview pane as standalone window | Issue #71985 | [Issue](https://github.com/NousResearch/hermes-agent/issues/71985) | Low-Medium — non-trivial E2B window management |
| Memory lifecycle management & maintenance UX | Issue #78307 | [Issue](https://github.com/NousResearch/hermes-agent/issues/78307) | Medium — scoped to built-in memory stores |
| Telegram: paid broadcasts, link previews, reactions, forwarding, batch deletes | Issues #78689–#78693, #78790 | [Meta](https://github.com/NousResearch/hermes-agent/issues/78791) | High — batched as campaign, incremental PRs |
| DeepSeek native server-side `web_search` | Issue #79820 (dup) | [Issue](https://github.com/NousResearch/hermes-agent/issues/79820) | Low — marked duplicate, likely later |

**Roadmap Signal:** The **Telegram Bot API 10.2 alignment campaign** is the clearest upcoming feature push, executed as a series of small, targeted PRs under the 5×2×3 methodology. Desktop customization (tray, font, width) is also well-positioned for inclusion.

---

## 7. User Feedback Summary

**Pain Points:**
- **v0.20.0 regressions are the dominant complaint.** Users report the desktop app becoming a "viewer-only shell" (#79407), severe macOS CPU spikes up to 400% (#79853), and cross-session message mixing under load. These are high-friction issues affecting core functionality.
- **Post-update gateway staleness on Linux** (#78574) causes `ImportError` crashes because the systemd gateway isn't restarted after `hermes update`. This breaks Telegram bot operation silently.
- **Terminal command crashes** from null bytes in heredoc payloads (#77780) are a reliability concern for users running complex shell workflows.
- **WeChat approval race** (#79562) means dangerous-command approval flows fail after the first use per turn, a serious usability and safety issue.
- **Desktop feature requests** (#79856, #79858, #71985) indicate power users want finer-grained UI control over layout and typography.

**Satisfaction Signals:**
- The AIDE² self-improvement system (#77236) generated positive engagement with full CI green and 198 tests — users appreciate investment in agent reliability.
- God-file sharding (#78647) has strong community support (policy enforcement, clear methodology) suggesting users value long-term code health.
- Fast turnarounds on targeted fixes (e.g., Signal typing #79412, Hindsight prefetch #79861) show responsiveness to niche but real issues.

---

## 8. Backlog Watch

| Issue | Open Since | Comments | Reason for Concern | Link |
|-------|-----------|----------|-------------------|------|
| **#54962** — Extract Gateway Platform Routing from `gateway/run.py` | 2026-06-29 | 11 | 858KB god file; blocks further gateway refactor; stale for ~6 weeks | [Issue](https://github.com/NousResearch/hermes-agent/issues/54962) |
| **#41736** — Route Preview links through file tabs | 2026-06-08 | 3 | Desktop UX gap; low complexity but unaddressed for 2 months | [Issue](https://github.com/NousResearch/hermes-agent/issues/41736) |
| **#40124** — Strip ANSI from `session_search` results before model | 2026-06-05 | — | Model context pollution; trivial fix pending for 2+ months | [PR](https://github.com/NousResearch/hermes-agent/pull/40124) |
| **#71866** — Desktop sidebar empty after update (state.db intact) | 2026-07-26 | 2 | Data loss illusion; state.db verified intact — likely a migration or cache bug | [Issue](https://github.com/NousResearch/hermes-agent/issues/71866) |
| **#73744** — WhatsApp outbound mentions producer not wired | 2026-07-29 | — | Plumbing exists since PR #67179 but no call site populates `mentions` — feature is half-implemented | [PR](https://github.com/NousResearch/hermes-agent/pull/73744) |

**Maintainer Attention Needed:**
- **#54962** is the highest-priority backlog item — the 858KB `gateway/run.py` file is a structural bottleneck. It should be prioritized within the ongoing god-file sharding campaign.
- **#40124** is a trivial one-line fix (reuse existing `ansi_strip.py`) that has languished — a quick win for trust.
- **#71866** and **#79853** both relate to v0.20.0 desktop stability and should be triaged together as part of a regression patch.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-06

---

## 1. Today's Overview

PicoClaw saw modest activity today with 4 PRs updated and zero new issues opened or closed in the last 24 hours. The only completed item was a merged enhancement (PR #926) adding Anthropic OAuth setup-token authentication. The project remains active on the frontend and infrastructure fronts, with open PRs targeting lockfile repair, model fallback chains, and documentation workflow consolidation. No new releases were published, suggesting the current codebase is in a stabilization phase rather than a release sprint.

---

## 2. Releases

No new releases today.

---

## 3. Project Progress

- **PR #926** `[CLOSED/MERGED]` — Added Anthropic OAuth setup-token login support (`sk-ant-oat01-*`), streaming for OAuth tokens, and usage endpoint integration for utilization tracking. This significantly expands authentication flexibility for Anthropic users who prefer token-based flows over static API keys.
- **PR #3318** `[OPEN]` — Fixes a broken `pnpm-lock.yaml` containing duplicate `semver` entries, which causes pnpm to refuse installation with `ERR_PNPM_BROKEN_LOCKFILE`. Unmerged but likely urgent given it blocks web frontend builds.
- **PR #3200** `[OPEN]` — Introduces a configurable default model fallback chain persisted through the backend API, enabling graceful degradation when primary models are unavailable.
- **PR #1951** `[OPEN]` — Relocates installation scripts from the separate docs repository into the main PicoClaw repo, centralizing maintenance.

---

## 4. Community Hot Topics

| PR/Issue | Status | Comments | Reactions | Link |
|---|---|---|---|---|
| [#926](https://github.com/sipeed/picoclaw/pull/926) — Anthropic OAuth setup-token | Merged | — | 0 | sipeed/picoclaw#926 |
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) — Fix broken pnpm-lock.yaml | Open | — | 0 | sipeed/picoclaw#3318 |
| [#3200](https://github.com/sipeed/picoclaw/pull/3200) — Configurable model fallback chain | Open | — | 0 | sipeed/picoclaw#3200 |
| [#1951](https://github.com/sipeed/picoclaw/pull/1951) — Move install scripts from docs | Open | — | 0 | sipeed/picoclaw#1951 |

**Analysis:** The absence of comments and reactions across all PRs is notable. PR #3318 addresses a concrete build-breaking bug that likely affects anyone working in the `web/frontend` directory. PR #3200 reflects a growing community need for model reliability — fallback chains are essential for production-grade AI assistants. PR #1951 signals a maturation trend: consolidating scattered repo dependencies to reduce maintenance overhead.

---

## 5. Bugs & Stability

| Severity | Issue | Fix Status | Link |
|---|---|---|---|
| **High** | Broken `pnpm-lock.yaml` with duplicate `semver@7.8.5` mapping keys blocks web frontend builds | Fix PR open (#3318) | sipeed/picoclaw#3318 |

No new crash reports or regressions opened today. The lockfile issue is the only active stability concern and has an open fix PR pending merge.

---

## 6. Feature Requests & Roadmap Signals

- **Configurable model fallback chains** (PR #3200) — Strong signal that users need resilient multi-model routing. Likely to ship in the next minor release, as the PR is well-scoped and already includes backend persistence.
- **Anthropic OAuth setup-token support** (PR #926, merged) — Expands auth diversity; similar OAuth flows for other providers may follow.
- **Centralized install scripts** (PR #1951) — Suggests roadmap toward monorepo consolidation and simpler onboarding.

Predicted next release focus: resolving the lockfile bug, merging the fallback chain feature, and potentially a patch release once these land.

---

## 7. User Feedback Summary

No new issues were filed today, so direct user complaints are absent from this cycle. However, the open PRs reveal clear user-driven needs:

- **Pain point:** Build failures from lockfile corruption — users need reliable `pnpm install` in the web frontend.
- **Pain point:** Lack of model fallback in production workflows — users want graceful degradation when a primary LLM provider is slow or unavailable.
- **Satisfaction signal:** The merged OAuth enhancement (PR #926) addresses a long-standing request for alternative Anthropic auth methods beyond static API keys.

Overall, user engagement appears constructive — feature PRs are well-documented and directly tied to real usage scenarios.

---

## 8. Backlog Watch

| PR/Issue | Open Since | Days Open | Risk | Link |
|---|---|---|---|---|
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) — Fix pnpm lockfile | 2026-08-05 | 1 | ⚠️ Medium (build blocker) | sipeed/picoclaw#3318 |
| [#3200](https://github.com/sipeed/picoclaw/pull/3200) — Model fallback chain | 2026-07-01 | 36 | ⚠️ Medium (feature delay) | sipeed/picoclaw#3200 |
| [#1951](https://github.com/sipeed/picoclaw/pull/1951) — Move install scripts | 2026-03-24 | 135 | ⚠️ Low (deferred cleanup) | sipeed/picoclaw#1951 |

**Recommendation:** PR #3318 should be prioritized for review and merge given it blocks frontend development. PR #3200 has been open over a month and represents high-value functionality — a timely review would improve project velocity. PR #1951 has been open for ~4 months; while lower priority, merging it would reduce docs-repo fragmentation.

---

**Project Health Summary:** 🟡 Moderate — One feature merged, one critical bug fix pending, no new issues. Activity is light but focused on meaningful infrastructure improvements.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-06

---

## 1. Today's Overview

NanoClaw shows sustained contributor momentum with **12 PRs updated** in the last 24 hours and **2 open issues** actively discussed. The release cadence is quiet (no new versions today), but development velocity is high, particularly around channel reliability, skills extensibility, and database correctness. Two PRs were merged today, and several critical fixes address long-standing WhatsApp and container-environment problems. Overall project health is strong with active community participation across bug fixes, refactors, and new skill integrations.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

### Merged / Closed PRs Today
- **[PR #3175](https://github.com/nanocoai/nanoclaw/pull/3175)** — `fix: route command-gate denials through the delivery adapter, not outbound.db` (Author: Joi) · **MERGED**
- **[PR #3187](https://github.com/nanocoai/nanoclaw/pull/3187)** — `fix(agent-runner): disallow built-in SendMessage so agent-to-agent messaging works` (Author: dim0627) · **MERGED**

### Key Advances
- **DB corruption risk mitigated**: Joi's PR (#3175) eliminates a second-writer scenario on `outbound.db`, enforcing the single-writer invariant documented in `docs/db.md`. A follow-up #3192 remains open, possibly re-addressing residual concerns.
- **Agent-to-agent messaging unblocked**: PR #3187 removes the built-in `SendMessage` restriction, enabling proper multi-agent workflows.
- **WhatsApp stability improved**: PR #3191 caps an unbounded `setup()` await, preventing host startup hangs from logged-out WhatsApp sessions.
- **Formatter resilience**: PR #2346 ensures unknown slash commands fall through to normal chat instead of being silently dropped by the Agent SDK.
- **Channel picker expanded**: PR #3050 adds **Dial** as a configurable channel option in the setup wizard.

---

## 4. Community Hot Topics

| Item | Type | Author | Updates | Comments |
|------|------|--------|---------|----------|
| [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) — Signal image/PDF attachments unreachable from container | Issue | brentkearney | 2026-08-05 | 1 |
| [#2006](https://github.com/nanocoai/nanoclaw/issues/2006) — Docker socket permission denied on Debian 12 LXC | Issue | dooha333 | 2026-08-05 | 1 |
| [#3192](https://github.com/nanocoai/nanoclaw/pull/3192) — Route command-gate denials via delivery adapter | PR | Joi | 2026-08-05 | — |
| [#3191](https://github.com/nanocoai/nanoclaw/pull/3191) — WhatsApp `setup()` timeout | PR | apelosi | 2026-08-05 | — |
| [#3156](https://github.com/nanocoai/nanoclaw/pull/3156) — Carry channel attachments to providers as structured parts | PR | glifocat | 2026-08-05 | — |

**Analysis:**
- **Signal media handling** (#2528) and **Debian LXC Docker permissions** (#2006) reflect recurring deployment-environment friction. Users expect self-contained installs to "just work" across containerized and proxmox-based setups.
- The **command-gate DB fix** (#3192 / #3175) drew a follow-up PR, indicating the community is actively scrutinizing database invariants.
- **Attachment forwarding** (#3156) directly complements the Signal bug — users want rich-media channels to function end-to-end inside the agent container.
- **WhatsApp reliability** (#3191) signals that session-lifecycle edge cases are a real pain point for users running always-on personal assistants.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|----------|------|-------------|------------|
| **High** | [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) | Signal image/PDF attachments arrive at host but are unreachable from the agent container | No open fix PR yet; related PR #3156 may partially address attachment forwarding |
| **High** | [#2006](https://github.com/nanocoai/nanoclaw/issues/2006) | Fresh Debian 12 LXC install: docker socket permission denied; recovery path does not fire | No open fix PR yet |
| **Medium** | PR #3191 | WhatsApp `setup()` hangs indefinitely on logged-out sessions | **Merged** — bounded with timeout |
| **Medium** | PR #3175/#3192 | `outbound.db` corruption risk from dual-writer in `writeOutboundDirect()` | **Merged** (#3175); follow-up #3192 open |
| **Low** | PR #2346 | Unknown slash commands silently dropped instead of passed through as chat | **Open** — fix in progress |

---

## 6. Feature Requests & Roadmap Signals

| PR | Type | Description |
|----|------|-------------|
| [#3190](https://github.com/nanocoai/nanoclaw/pull/3190) | **Utility skill** | **Tavily MCP tool** — web search via MCP integration |
| [#3189](https://github.com/nanocoai/nanoclaw/pull/3189) | **Utility skill** | **`add-why`** — explain what happened to a specific message (debug/observability skill) |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | **Feature skill** | **Dial channel** added to setup wizard and channel picker |
| [#3186](https://github.com/nanocoai/nanoclaw/pull/3186) | Refactor | **Host seams for skill-owned capabilities** — architectural improvement for skill modularity |
| [#3188](https://github.com/nanocoai/nanoclaw/pull/3188) | Fix | Forward **OneCLI gateway env vars** (HTTPS_PROXY, CA trust) to spawned MCP servers |

**Predictions for next release:**
- **Tavily search skill** (#3190) and **Dial channel** (#3050) are strong candidates for inclusion.
- **Host-seam refactoring** (#3186) likely precedes a skills architecture update.
- **`add-why` observability skill** (#3189) addresses a clear user need for message-level debugging.

---

## 7. User Feedback Summary

**Pain points expressed:**
1. **Container media access** (#2528): Users send images/PDFs via Signal expecting the agent to process them, but the container isolation breaks file visibility. This undermines the "personal assistant that sees everything" value proposition.
2. **LXC/container deployment friction** (#2006): The recovery path for Docker group permissions fails to re-apply, forcing manual intervention on fresh installs — a poor first-experience signal.
3. **WhatsApp session hangs** (#3191 — now fixed): Logged-out sessions freezing host startup prevent reliable always-on operation.
4. **Silent command drops** (#2346): Unknown slash commands vanishing without error wastes user time and creates confusion.

**Satisfaction signals:**
- Active skill contributions (Tavily, `add-why`, Dial) show a healthy contributor base building on the platform.
- The merged `SendMessage` fix (#3187) unlocks multi-agent scenarios that power users have requested.
- Clean separation of DB writers (#3175) demonstrates responsiveness to architectural feedback.

---

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#2006](https://github.com/nanocoai/nanoclaw/issues/2006) — Docker socket permission on Debian 12 LXC | ~3.5 months | First-install breakage on a growing deployment target (Proxmox/LXC users) |
| [#2528](https://github.com/nanocoai/nanoclaw/issues/2528) — Signal media unreachable in container | ~2.5 months | Blocks core multi-modal agent functionality; no fix PR yet |
| [#3192](https://github.com/nanocoai/nanoclaw/pull/3192) — Command-gate DB fix (follow-up) | 1 day | Open despite #3175 merge; may indicate incomplete resolution |
| [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) — Unknown slash command handling | ~3 months | Long-open fix for a UX-critical formatting bug |

**Recommendation:** Issues #2006 and #2528 have been open for extended periods without merged fixes and should be prioritized — they directly impact onboarding and core functionality. The community is actively building skills and channel integrations; resolving these stability blockers would strengthen the foundation for that growth.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-06

---

## 1. Today's Overview

NullClaw (github.com/nullclaw/nullclaw) showed **low but focused activity** on 2026-08-06. No issues or PRs were closed/merged in the last 24 hours, and no new releases were published. The project is currently in a **maintenance-heavy phase**, with two open pull requests targeting stability fixes for core runtime and channel subsystems. The contributor `raskevichai` has been the sole active author, suggesting a small but concentrated maintainer team.

---

## 2. Releases

**No new releases** were published today.

---

## 3. Project Progress

### Open Pull Requests Awaiting Merge

| # | Title | Author | Status | Linked Issue |
|---|-------|--------|--------|--------------|
| [#985](https://github.com/nullclaw/nullclaw/pull/985) | `fix(runtime): give the agent turn path a 16 MiB stack` | raskevichai | OPEN | [#976](https://github.com/nullclaw/nullclaw/issues/976) |
| [#984](https://github.com/nullclaw/nullclaw/pull/984) | `fix(channels): let poll failures age out a dead polling thread` | raskevichai | OPEN | [#972](https://github.com/nullclaw/nullclaw/issues/972) |

**Notable:** No PRs were merged or issues closed today. Both PRs target stack/timeout failures in long-running agent operation — a sign of maturation in reliability work.

---

## 4. Community Hot Topics

### Most Discussed Open PRs

1. **[PR #985](https://github.com/nullclaw/nullclaw/pull/985)** — Agent stack overflow fix
   - `SESSION_TURN_STACK_SIZE` was aliased to `HEAVY_RUNTIME_STACK_SIZE` (2 MiB), insufficient for the turn path running `SessionManager.processMessage*()` / `Agent.turn()`
   - Root cause identified; fix allocates 16 MiB per turn thread

2. **[PR #984](https://github.com/nullclaw/nullclaw/pull/984)** — Channel polling thread liveness
   - Telegram and Matrix channels go silent after idle periods while `nullclaw agent` continues responding
   - The supervisor was structurally blind to dead polling threads; fix introduces aging-out logic in `supervisionLoop`

---

## 5. Bugs & Stability

| Severity | Bug / Issue | PR Fix | Status |
|----------|-------------|--------|--------|
| **High** | [#976](https://github.com/nullclaw/nullclaw/issues/976) — Agent turn stack overflow (2 MiB insufficient) | [#985](https://github.com/nullclaw/nullclaw/pull/985) | PR OPEN |
| **High** | [#972](https://github.com/nullclaw/nullclaw/issues/972) — Dead polling threads not reclaimed; channels go silent after idle | [#984](https://github.com/nullclaw/nullclaw/pull/984) | PR OPEN |

**Assessment:** Both bugs are **production-impacting** — stack overflows crash the agent, and silent channels degrade user experience silently. Two open PRs provide fixes, but neither has been merged yet.

---

## 6. Feature Requests & Roadmap Signals

No new feature requests or roadmap signals were raised today. The project appears to be in a **stability-first** cycle, with all current effort directed at hardening existing runtime and channel infrastructure rather than adding new capabilities.

**Predicted next version focus:** If both PRs land, a patch release (e.g., `v0.x.y+1`) targeting runtime reliability would be the most likely outcome.

---

## 7. User Feedback Summary

- **Pain point 1:** Agent crashes or stack overflows during message processing — users experience abrupt failures during active conversations.
- **Pain point 2:** Channels (Telegram/Matrix) become unresponsive after idle periods, requiring manual gateway restarts. Users report frustration with silent failures that require intervention.
- **Satisfaction signal:** `nullclaw agent` continues to answer correctly even when channels are dead, suggesting the core agent loop is robust — the issue is in the channel abstraction layer.

---

## 8. Backlog Watch

| Item | Age | Priority | Maintainer Attention Needed |
|------|-----|----------|----------------------------|
| [#985](https://github.com/nullclaw/nullclaw/pull/985) — Stack size fix | 1 day | **Critical** | Review & merge |
| [#984](https://github.com/nullclaw/nullclaw/pull/984) — Dead thread reclamation | 1 day | **Critical** | Review & merge |
| [#976](https://github.com/nullclaw/nullclaw/issues/976) — Stack overflow | 1+ day | **Critical** | Awaiting PR merge |
| [#972](https://github.com/nullclaw/nullclaw/issues/972) — Silent channels | 1+ day | **Critical** | Awaiting PR merge |

**Recommendation:** Both PRs are ready for maintainer review. These are targeted bug fixes with clear root cause analysis — low-risk, high-impact candidates for immediate merge. No stale or abandoned PRs/Issues detected today.

---

*Generated: 2026-08-06 | Source: github.com/nullclaw/nullclaw*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-06

## 1. Today's Overview
IronClaw shows high development velocity with 44 issues and 50 pull requests updated in the last 24 hours. The project released **v1.1.0-rc.1** focusing on extension reach, durable attachments, and Slack slash commands. Active work spans sandbox security profiles, outbound‑delivery recovery, skill‑selection improvements, and a Web Debug Inspector. Several P1/P2 bugs from recent QA cycles remain open, indicating ongoing stability efforts. Overall project health is **active and progressing**, with a clear shift toward multi‑tenant administration, skill extensibility, and operational observability.

## 2. Releases
**ironclaw‑v1.1.0‑rc.1** (2026‑08‑03)  
- **Headline changes:**  
  - Register arbitrary hosted MCP servers.  
  - Install extensions from IronHub deep links.  
  - Durable file attachments that cross channels.  
  - Slack `/ironclaw` slash commands.  
  - Broad pass on making failures more legible.  
- **Breaking changes:** None noted.  
- **Migration notes:** No explicit migration steps provided; review release notes for configuration adjustments if using previous MCP or attachment flows.

## 3. Project Progress
**Merged/Closed today:**
- `#7261` – Fix CI release‑canary temp‑path resolution.
- `#7196` – Bump WASM dependencies (wasmtime‑wasi, wit‑component, wit‑parser).

**Key open PRs advanced:**
- `#7214` – Add explicit Docker and Railway user‑sandbox profiles.
- `#7028` – Preserve terminal status during outbound‑delivery recovery.
- `#7048` – Sanitize guest diagnostics before tracing (depends on `#7063`).
- `#7263` – Program‑closure restructure with dated evidence for all WS12 items.
- `#7157` – Implement explicit channel‑delivery tool (two‑lane model).
- `#6938` – Shift skill selection from keyword scorer to model‑based choice.
- `#7171` – Provide DB‑backed tree for every skill mount; make skill commands runnable.
- `#7230` – Add bounded diagnostic session storage for Web Debug Inspector.
- `#7027` – Disable ambient proxy discovery in hardened network transport.
- `#7237`, `#7262` – Routine dependency bumps (everything‑else, WASM groups).

## 4. Community Hot Topics
**Most commented issues:**
- **#3036** – [EPIC] Configuration‑as‑Code for IronClaw Reborn (7 comments)  
  `https://github.com/nearai/ironclaw/issues/3036`  
  *Underlying need:* Operators want declarative tenant blueprints, schema‑validated settings, and an audit trail instead of hand‑editing `.env`, workspace docs, and JSON.

- **#7194** – Make an admin‑allowed shared channel addressable as an outbound delivery target (3 comments)  
  `https://github.com/nearai/ironclaw/issues/7194`  
  *Underlying need:* Agents can post to Slack channels but cannot set them as sanctioned outbound targets; admins require fine‑grained control over delivery routing.

- **#6257** – “Invalid value (attachments.mime_type)” error when sending/generating PDFs (2 comments)  
  `https://github.com/nearai/ironclaw/issues/6257`  
  *Underlying need:* PDF attachment handling is broken, blocking document‑centric workflows.

**Notable open PRs:**
- `#7263` – Program closure (Reborn target‑architecture restructure) – large, cross‑cutting.
- `#7157` – Explicit channel‑delivery tool – central to the v1.1.0 feature set.

## 5. Bugs & Stability
**Open bugs reported today (ranked by severity):**

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| P1 | [#7247](https://github.com/nearai/ironclaw/issues/7247) | Agent falsely claims GitHub is already connected. | None yet |
| P1 | [#7246](https://github.com/nearai/ironclaw/issues/7246) | Agent hallucinates automation status instead of checking actual state. | None yet |
| P2 | [#7249](https://github.com/nearai/ironclaw/issues/7249) | Slack DM execution result delivered to Telegram. | None yet |
| P2 | [#7254](https://github.com/nearai/ironclaw/issues/7254) | IronClaw cannot access files attached to Slack feedback threads. | None yet |
| P2 | [#7251](https://github.com/nearai/ironclaw/issues/7251) | Agent guesses MCP authentication type instead of discovering/initiating auth. | None yet |
| P2 | [#7250](https://github.com/nearai/ironclaw/issues/7250) | DeepWiki MCP reports misleading authentication guidance for network failures. | None yet |
| P2 | [#7248](https://github.com/nearai/ironclaw/issues/7248) | Invalid custom MCP endpoint accepted, then causes model run to fail. | None yet |
| P2 | [#6257](https://github.com/nearai/ironclaw/issues/6257) | Invalid value (attachments.mime_type) error for PDFs. | None yet |
| — | [#7204](https://github.com/nearai/ironclaw/issues/7204) (closed) | WebUI composer focus and accent‑ring papercuts. | `#7204` itself |

**Note:** The bug‑bash wave (issues #7245‑#7251) highlights trust‑and‑accuracy gaps in agent behavior and channel isolation. No direct fix PRs are linked yet; these will likely be addressed in upcoming patches.

## 6. Feature Requests & Roadmap Signals
- **Configuration‑as‑Code** (#3036) – declarative tenant blueprints, schema, diff, audit trail.
- **Admin‑Managed Agents** (#6578) – tenant admins create non‑human subjects without second identity hierarchy.
- **IronHub integration** (#6731) – runtime skill/tool marketplace with provenance checks.
- **Skill system overhaul** (#6941) – model‑based skill selection, self‑creation, durable mounts.
- **Web Debug Inspector** (#7218) – operator‑only view of prompts, model usage, tool execution.
- **AI‑first Design System** (#7038) – Storybook‑backed theming, assets, interactions.
- **Explicit channel‑delivery tool** (#7157) – two‑lane model separating conversation lifecycle from notification channels.

**Prediction for v1.1.0:** IronHub integration, skill‑selection improvements, channel‑delivery tool, sandbox profiles, Web Debug Inspector storage, and durable attachment cross‑channel support are all active and likely ship in the final 1.1.0 release.

## 7. User Feedback Summary
**Pain points:**
- Configuration is fragmented across `.env`, workspace docs, settings JSON, and runtime flags – no schema or audit trail.
- Admins cannot designate shared Slack channels as outbound delivery targets.
- PDF attachments fail with MIME‑type validation errors.
- Execution results leak across channels (Slack DM → Telegram).
- Agents cannot access files attached to Slack feedback threads.
- MCP authentication is guessed rather than discovered or initiated properly.
- Agent falsely claims connections (GitHub) and fabricates automation status.

**Satisfaction signals:**
- Positive traction on extension reach (MCP registration, IronHub links).
- Durable file attachments across channels address a common multi‑channel workflow.
- Slack slash‑command integration improves operator UX.
- Sandbox profiles and proxy‑discovery fixes enhance security and reliability.

**Use cases driving development:** multi‑tenant administration, skill‑marketplace exploration, cross‑channel durable attachments, and real‑time operational debugging.

## 8. Backlog Watch
**Long‑open issues needing maintainer attention:**
- **#3036** – Configuration‑as‑Code epic (open since 2026‑04‑28, 7 comments).  
  `https://github.com/nearai/ironclaw/issues/3036`
- **#6578** – Admin‑Managed Agents as UserId Subjects (open since 2026‑07‑23).  
  `https://github.com/nearai/ironclaw/issues/6578`
- **#6731** – Integrate IronHub into IronClaw (open since 2026‑07‑27).  
  `https://github.com/nearai/ironclaw/issues/6731`
- **#6941** – Skill‑system epic (model can self‑create, find, choose skills) (open since 2026‑07‑31).  
  `https://github.com/nearai/ironclaw/issues/6941`
- **#7203** – Mount virtual filesystem for skill execution (open since 2026‑08‑05).  
  `https://github.com/nearai/ironclaw/issues/7203`

**Open PRs with broad impact:**
- `#7263` – Program‑closure restructure (blocked on review/merge).
- `#7264` – Guidance‑layer docs (stacked on `#7263`).
- `#7157` – Channel‑delivery tool (core v1.1.0 feature).
- `#6938` – Skill‑selection model shift (stacked on `#6745`).

These items represent the highest‑leverage backlog pieces; timely triage will keep the v1.1.0 trajectory on track.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026‑08‑06

## 1. Today's Overview
LobsterAI shows **high development velocity** with 11 PRs updated in the last 24 h (10 merged/closed) and **one new release** (2026.8.5). Activity is heavily bug‑focused: all three currently open issues are marked `[Bug]`, and two of them report core‑functionality regressions (system‑prompt duplication, skill‑switch mismatch). The project remains active and responsive, though the stale bug #1200 indicates a need for better triage discipline.

## 2. Releases
**LobsterAI 2026.8.5** (2026‑08‑05)  
- `feat(activity)`: added native daily check‑in experience [#2408](https://github.com/netease-youdao/LobsterAI/pull/2408)  
- `feat(enterprise)`: isolated account‑scoped auth and service flows [#2409](https://github.com/netease-youdao/LobsterAI/pull/2409)  
- `style`: minor UI adjustments  
*No breaking changes or migration steps noted.*

## 3. Project Progress
**Merged / closed PRs today (10):**  
- **Renderer / activity** – updated startup credit poster and included close icon [#2439](https://github.com/netease-youdao/LobsterAI/pull/2439), [#2438](https://github.com/netease-youdao/LobsterAI/pull/2438)  
- **Main & cowork** – hardened window‑lifecycle shutdown against hangs [#2437](https://github.com/netease-youdao/LobsterAI/pull/2437)  
- **OpenClaw gateway** – prevented lock‑poisoning from self‑restart races [#2436](https://github.com/netease-youdao/LobsterAI/pull/2436)  
- **Cowork** – added title‑bar conversation search [#2435](https://github.com/netease-youdao/LobsterAI/pull/2435)  
- **Dependency bumps** – cross‑env, react‑dom, vite updated via dependabot [#1279](https://github.com/netease-youdao/LobsterAI/pull/1279), [#1280](https://github.com/netease-youdao/LobsterAI/pull/1280), [#1281](https://github.com/netease-youdao/LobsterAI/pull/1281)  
- **Internal fixes** – two rlog‑related PRs closed [#2434](https://github.com/netease-youdao/LobsterAI/pull/2434), [#2431](https://github.com/netease-youdao/LobsterAI/pull/2431)  

**Key advances:** enterprise auth isolation, daily‑check‑in feature, conversation search, and improved shutdown reliability.

## 4. Community Hot Topics
- **[Issue #1200](https://github.com/netease-youdao/LobsterAI/issues/1200)** – NIM super‑group name resolution broken due to hard‑coded `teamTypeNum`. A fix PR [#1201](https://github.com/netease-youdao/LobsterAI/pull/1201) is open but still unmerged. Underlying need: **correct NIM SDK integration for large‑scale group scenarios**.  
- **[Issue #2441](https://github.com/netease-youdao/LobsterAI/issues/2441)** – skill‑switch persistence fails because OpenClaw matches by `frontmatter name` while LobsterAI writes by directory name. Underlying need: **reliable skill‑management API and persistent user configurations**.  
- **[Issue #2440](https://github.com/netease-youdao/LobsterAI/issues/2440)** – desktop session injects duplicate system‑prompt text (4,425 characters) that mirrors `AGENTS.md`. Underlying need: **single‑source‑of‑truth prompt injection to avoid token waste and confusion**.  

*All three issues have 0 comments and 0 👍, suggesting they are either newly reported or not yet widely noticed.*

## 5. Bugs & Stability
| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **High** | [#1200](https://github.com/netease-youdao/LobsterAI/issues/1200) | NIM super‑group name fallback due to wrong `teamTypeNum` | [#1201](https://github.com/netease-youdao/LobsterAI/pull/1201) (open) |
| **Medium** | [#2441](https://github.com/netease-youdao/LobsterAI/issues/2441) | Skill‑switch inconsistency between directory‑name and frontmatter‑name matching | — |
| **Medium** | [#2440](https://github.com/netease-youdao/LobsterAI/issues/2440) | Duplicate system‑prompt injection in desktop sessions | — |

*No crashes or regressions beyond the above bugs were reported today.*

## 6. Feature Requests & Roadmap Signals
- **Persistent system‑prompt精简入口** – hinted by #2440 and #2441; users want a stable, editable system‑prompt area that survives session restarts.  
- **Skill‑switch reliability** – #2441 highlights a mismatch in OpenClaw config sync; likely to be addressed in a future release to improve developer experience.  
- **Conversation search expansion** – #2435 added title‑bar search; subsequent PRs may extend search to artifact panels or history.  

*Prediction:* Next release will likely prioritize bug fixes for #1200, #2440, and #2441, followed by polishing of the new enterprise‑auth and daily‑check‑in features.

## 7. User Feedback Summary
**Pain points:**  
- Group‑name resolution fails in NIM super‑groups, degrading collaboration experience.  
- Skill switches silently fail, breaking workflow automation.  
- Duplicate system prompts waste tokens and create confusion.  

**Satisfaction:**  
- New daily‑check‑in feature and enterprise‑auth isolation are well‑received (positive framing in release notes).  
- Window‑shutdown hardening and gateway‑lock fixes improve desktop stability.  

**Overall:** Users appreciate new capabilities but are frustrated by persistent core‑functionality bugs that affect daily use.

## 8. Backlog Watch
- **#1200** – stale since 2026‑04‑01, fix PR #1201 open but unmerged. Needs maintainer review and merge.  
- **#2440 & #2441** – newly reported (2026‑08‑05) with no assigned owner or PR. Recommend triage and prioritization in next sprint.  
- **Dependabot PRs** (#1279, #1280, #1281) – automatically closed; verify that updated dependencies do not introduce regressions.  

*Maintainer action:* Address the three open bugs promptly to prevent user churn and improve release quality.

---
*Generated by Agnes (Sapiens AI) based on GitHub data from LobsterAI (netease‑youdao/LobsterAI) as of 2026‑08‑06.*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-06

## 1. Today's Overview
The CoPaw project shows high development velocity with **22 issues updated** (14 open, 8 closed) and **50 PRs updated** (28 open, 22 merged/closed) in the last 24 hours. No new releases were published, indicating the team is focused on merging incremental improvements and bug fixes. Activity is concentrated on stability hardening (MCP, SSE retry, capability caching) and UX refinements across desktop and console interfaces. The project remains in an active development cycle with strong contributor engagement.

## 2. Releases
**None.** No new versions were published today.

## 3. Project Progress
**Merged/Closed PRs (22 today):**
- **#6738** [CLOSED] feat(creator): grounding search, timeline workbench, YOLO reviews, i18n, ASR, and reliability hardening — next batch of Creator (PawApp) capabilities.
- **#6701** [CLOSED] fix(website): website add blog — added blog section to documentation site.
- **#6670** [CLOSED] docs(checkpoint): add checkpoint usage documentation in commands page — consolidated checkpoint command docs into Magic Commands page.
- **#6669** [CLOSED] fix(desktop): stabilize Chrome native messaging and Windows restore locking — resolved Windows startup failures for the Chrome extension.
- **#5598** [CLOSED] feat(console): add LLM fallback configuration UI — users can now configure per‑agent/global fallback candidates from the Models settings page.

## 4. Community Hot Topics
**Most commented issues:**
- **#6436** [OPEN] The Right Model for Every Message: Automatic Model Routing *(3 comments)*  
  [Link](https://github.com/agentscope-ai/QwenPaw/issues/6436)  
  *Underlying need:* Users want dynamic model selection (small/fast for simple turns, vision for images, large for reasoning) instead of pinning a single model per agent.
- **#6726** [OPEN] Long console session with heavy tool usage fails with 400 *(2 comments)*  
  [Link](https://github.com/agentscope-ai/QwenPaw/issues/6726)  
  *Underlying need:* Stability in long‑running sessions with many tool‑call pairs; prevents session crashes.
- **#6452** [CLOSED] 体验优化：取消“当前模型未检测到多模态能力”的提示 *(2 comments)*  
  [Link](https://github.com/agentscope-ai/QwenPaw/issues/6452)  
  *Underlying need:* Reduce noisy UX warnings; align with competitor behavior.
- **#6732** [OPEN] mcp工具规律性失效 *(2 comments)*  
  [Link](https://github.com/agentscope-ai/QwenPaw/issues/6732)  
  *Underlying need:* MCP tool reliability over extended periods; avoid manual restarts.
- **#6480** [OPEN] execute_shell_command: shell process detached via &/nohup never returns to idle *(2 comments)*  
  [Link](https://github.com/agentscope-ai/QwenPaw/issues/6480)  
  *Underlying need:* Proper handling of background shell processes in agent workflows.

## 5. Bugs & Stability
**Bugs reported today (ranked by severity):**
1. **#6726** [Bug] Long console session fails with 400 after many tool calls *(critical)*  
   [Link](https://github.com/agentscope-ai/QwenPaw/issues/6726)  
   *Fix PR:* #6721 addresses reasoning‑content validation errors for AgentScope messages.
2. **#6732** [Bug] MCP tools periodically stop working, requiring container restart *(high)*  
   [Link](https://github.com/agentscope-ai/QwenPaw/issues/6732)  
   *Fix PR:* #6724 proposes configurable MCP tool‑call timeout to prevent indefinite stalls.
3. **#6731** [Bug] execute_shell_command crashes with `replace() should be called on dataclass instances` *(high)*  
   [Link](https://github.com/agentscope-ai/QwenPaw/issues/6731)  
   *Fix PR:* None yet; needs investigation.
4. **#6708** [Bug] 503 in‑stream SSE error not retried, fails request *(medium)*  
   [Link](https://github.com/agentscope-ai/QwenPaw/issues/6708)  
   *Fix PR:* #6714 enables retry for SSE errors with status codes in messages.
5. **#6707** [Bug] 400 when session history contains tool calls with a thinking‑mode upstream *(medium)*  
   [Link](https://github.com/agentscope-ai/QwenPaw/issues/6707)  
   *Fix PR:* #6721 also handles reasoning‑content normalization.

**Additional stability improvements:**
- **#6723** [fix] Expire stale capability cache and clear on model switch — prevents transient upstream failures from causing permanent capability mis‑reporting.
- **#6733** [fix] Preserve multimodal capabilities during OpenRouter metadata probe — avoids overwriting known capabilities with false.

## 6. Feature Requests & Roadmap Signals
**Open enhancement issues & PRs:**
- **#6436** Automatic model routing — high‑interest feature for multi‑model workflows.
- **#6724** Configurable MCP tool‑call timeout — addresses reliability concerns.
- **#6728** WeChat approval prompts support Chinese actions — localization improvement.
- **#6730** Live artifact canvas — render agent‑generated HTML in a side panel.
- **#6525** User context transparent penetration — pass `user_id`, `user_name`, `channel` from Chat API through Agent → Tool → MCP → SKILL CLI.
- **#6734** Rename “新建聊天” to “新任务” — aligns terminology with task‑oriented use case.

**Prediction for next version:** Model routing (#6436) and MCP timeout (#6724) are likely candidates for inclusion given community demand and existing fix PRs. The artifact canvas (#6730) is a notable UX enhancement that may also ship.

## 7. User Feedback Summary
**Pain points:**
- UX confusion around “完整模式” (full mode) vs. “精简模式” (compact mode) — users find the terminology puzzling and prefer a simpler config entry point.
- Auto‑generated session titles are often unhelpful; some users suggest removing them or improving the extraction logic.
- Missing right‑click “copy” menu in chat sessions; users rely on keyboard shortcuts.
- MCP tools intermittently fail, requiring container restarts.
- Shell command crashes when `sandbox_config` is passed.
- Desktop app name “QwenPaw Desktop” is considered redundant; users prefer just “QwenPaw”.

**Satisfaction points:**
- DingTalk org‑app approval flow fixed (#6709).
- LLM fallback configuration UI added (#5598).
- Chrome native messaging and Windows restore locking stabilized (#6669).
- Embedding configuration guide and ReMe improvements (#6739, #6741).

**Overall sentiment:** Users appreciate ongoing stability fixes and UX refinements but report frustration with persistent bugs in tool execution (MCP, shell) and inconsistent session management.

## 8. Backlog Watch
**Long‑unanswered important issues/PRs needing maintainer attention:**
- **#6436** Automatic model routing — open since 2026‑07‑24, 3 comments, still open.
- **#6480** Shell process detached via `&`/`nohup` never returns to idle — open since 2026‑07‑26, 2 comments.
- **#6732** MCP tools periodically fail — open since 2026‑08‑06, 2 comments.
- **#6731** Shell command crash with `sandbox_config` — open since 2026‑08‑06, 1 comment.
- **#6525** User context transparent penetration — open since 2026‑07‑28, no visible reply.
- **#6728** WeChat approval Chinese actions — open since 2026‑08‑05, 1 comment.
- **#6724** MCP timeout — open since 2026‑08‑05, 1 comment.
- **#6730** Live artifact canvas — open since 2026‑08‑05, 1 comment.

**Recommendation:** Prioritize review of issues related to tool stability (MCP, shell) and the model‑routing feature, as they directly impact core agent workflows.

---
*Data sourced from CoPaw GitHub repository (github.com/agentscope-ai/CoPaw) on 2026‑08‑06.*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-06

## 1. Today's Overview

ZeroClaw shows strong mid-week momentum with 50 issues and 50 PRs touched in the last 24 hours, 40 of which remain open/active. No new releases were shipped today, but five issues were closed and one PR (#9750) merged, indicating steady triage velocity. Activity is dominated by security hardening (SSRF gates, WebAuthn validation, agent pipeline policy enforcement) and RFC ratification work across governance, authentication, and runtime architecture. The project is in an active consolidation phase heading toward the v0.9.0 auth/security milestone.

## 2. Releases

No new releases published today.

## 3. Project Progress

**Closed/Merged today:**
- **#9750** [CLOSED] — `fix(service): bound launcher-owned daemon logs` — Replaces unbounded fixed-file daemon log redirection with an 8 MiB-bounded shared service supervisor. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9750)
- **#9462** [CLOSED] — `zeroclaw-plugins` lib unit tests behind the `plugins-wasmtime` feature were not executing in CI. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9462)
- **#7467** [CLOSED] — Zerocode now supports cursor navigation while editing string settings. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7467)
- **#6350** [CLOSED] — WhatsApp Web `allowed-numbers` bypass for LID-based contacts (silent message drops) resolved. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6350)
- **#9335** [CLOSED] — Added support for data-wrapped OpenAI-compatible chat responses. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9335)
- **#9652** [CLOSED] — Fixed `config set` rejecting cron keys with hyphens in aliases while `config list`/`get` accepted them. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9652)

**PRs advancing features today:**
- **#9324** — A2A outbound client config, shared wire-model, and tools (Phase 1 of RFC #9106). [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9324)
- **#8713** — SSRF gate for `file_download` tool with `allowed_private_hosts` opt-in. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/8713)
- **#8826** — SSRF gate for `image_gen` tool against server-supplied fal.ai URLs. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/8826)
- **#9776** — Extends `forbidden_paths` with workspace-relative glob patterns (implements RFC #8424). [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9776)
- **#9737** — Enforces per-agent tool policy in pipelines, binding memory and ACP delivery predicates. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9737)
- **#9695** — Strips provider terminal markers (`<eom>`, `<|eom|>`) from streaming and non-streaming responses. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9695)
- **#9723** — Parses DeepSeek DSML and `<|tool_call|>` envelope formats in the tool-call parser. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9723)
- **#8443** — Matrix single-message progress drafts with edited-in reasoning. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/8443)

## 4. Community Hot Topics

| Issue | Comments | Focus |
|---|---|---|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) — Work Lanes, Board Automation, Label Cleanup | 18 | Governance RFC, ratification deferred, rollout in progress |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) — Goal mode v1 (bounded foreground Matrix work) | 18 | Durable multi-turn agent objectives; 1 👍 |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — Chat Completions profile | 16 | OpenAI-compatible protocol surface for broader client ecosystem |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Per-execution confirmation tier for high-risk shell commands | 16 | Claude Code-style allow/ask/deny policy; Rev 3 scope confirmed |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) — Pluggable inbound auth & canonical principals | 12 | Rev 8, targeting Identity & Access milestone |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue tracker | 11 | Active decision pipeline for RFCs and design issues |

**Analysis:** The community is heavily invested in governance maturity (RFC ratification, work lanes) and security-conscious agent control (shell confirmation tiers, pluggable auth). The Chat Completions profile (#8603) and Goal mode (#8303) reflect demand for OpenAI-ecosystem compatibility and multi-turn durability—both are likely candidates for near-term delivery. The maintainer decision queue (#8692) signals an organizational maturation effort to reduce RFC drift.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|---|---|---|---|
| **S1** | [#9775](https://github.com/zeroclaw-labs/zeroclaw/issues/9775) | OpenRouter streaming requests drop `provider_extra`, breaking configured parameters | — |
| **S2** | [#9768](https://github.com/zeroclaw-labs/zeroclaw/issues/9768) | Daemon reload signal is SIGUSR1 but the degraded-security warning instructs operators to send a signal that kills the daemon | — |
| **S2** | [#9780](https://github.com/zeroclaw-labs/zeroclaw/issues/9780) | Cron-triggered SOPs cannot perform network work (no HTTP capability; shell.exec/notify.channel are unsatisfiable placeholders) | — |
| **S2** | [#9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) | `sops_dir` documented default is not honoured; SOPs silently never load with no error or warning | — |
| **S2** | [#6350](https://github.com/zeroclaw-labs/zeroclaw/issues/6350) ✅ Closed | WhatsApp Web allowed-numbers bypassed for LID-based contacts (silent drops) | Merged |
| **S3** | [#9769](https://github.com/zeroclaw-labs/zeroclaw/issues/9769) | `vi_verify` withheld-capability notice invisible when `log_persistence = "none"` | — |
| **S3** | [#9697](https://github.com/zeroclaw-labs/zeroclaw/issues/9697) | ZeroCode cannot connect to daemon launched by Windows Task Scheduler | — |
| **S3** | [#9652](https://github.com/zeroclaw-labs/zeroclaw/issues/9652) ✅ Closed | `config set` rejects cron keys with hyphens | Merged |

**Notable:** Four new bug/SOP issues surfaced today (9768, 9769, 9775, 9779, 9780), several from the same author (#9768, #9769 by AngryPacifist). The SOP subsystem (#9779, #9780) appears to have two compounding issues—default path not honored and no network capability—suggesting a systemic gap rather than isolated bugs. The S1 OpenRouter streaming bug (#9775) blocks a live workflow for users relying on `provider_extra` configuration.

## 6. Feature Requests & Roadmap Signals

| Issue | Status | Likelihood for Next Release |
|---|---|---|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — Chat Completions profile | RFC, 16 comments, needs maintainer review | **High** — broad client compatibility demand; multiple PRs already landing |
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) — Goal mode v1 | RFC, 18 comments, ratified direction | **High** — directly enables multi-turn bounded work; tied to v0.9.0 |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Shell command confirmation tiers | RFC Rev 3, scope confirmed by maintainer | **High** — security-critical; aligns with v0.9.0 auth/security milestone |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) — Pluggable inbound auth | RFC Rev 8, targeting Identity & Access | **Medium-High** — Rev 8 suggests near-ratification |
| [#9631](https://github.com/zeroclaw-labs/zeroclaw/issues/9631) — OpenRouter `session_id` for prompt-cache | Feature request, 6 comments | **Medium** — low-risk, cost-saving; could land as a config tweak |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) — Computer-use desktop support | RFC, 8 comments, needs author action | **Medium** — long-pending; author action needed to advance |
| [#8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832) — Plugin-owned Kanban board | RFC, 8 comments, updated today | **Low-Medium** — opt-in plugin, lower priority than security RFCs |
| [#9464](https://github.com/zeroclaw-labs/zeroclaw/issues/9464) — Anthropic OAuth alias contract | RFC in-progress, 3 comments | **Medium** — implements PR #9420, focused decision surface |

**Prediction:** The v0.9.0 release (tracked in [#7432](https://github.com/zeroclaw-labs/zeroclaw/issues/7432)) will likely ship the shell confirmation tier (#7155), pluggable auth (#7141), and Goal mode v1 (#8303) as core pillars, with the Chat Completions profile (#8603) as a major compatibility addition. The OpenRouter prompt-cache feature (#9631) is small enough to land in a patch release.

## 7. User Feedback Summary

- **SOP subsystem frustration** (#9779, #9780): Two issues opened by the same author today reveal that cron-triggered SOPs are fundamentally non-functional out of the box—no default `sops_dir` path is loaded, and even when loaded, SOPs lack HTTP capabilities for unattended network work. This suggests a documentation-to-implementation gap that needs both code and docs fixes.
- **OpenRouter cost concerns** (#9631): Users are actively seeking prompt-cache compatibility to reduce per-conversation costs, indicating production-scale usage where API spend matters.
- **Terminal marker leaks** (#9695): Provider-specific markers (`<eom>`, `<|eom|>`) are leaking into user-visible responses, a quality-of-implementation issue affecting streaming and non-streaming paths.
- **DeepSeek model support** (#9723): Users are adopting DeepSeek-family models and hitting parser gaps—tool calls wrapped in DSML or `<|tool_call|>` envelopes are surfaced as raw text instead of being executed.
- **WhatsApp reliability** (#6350 ✅, #9397): The LID-based contact bypass was a silent data-loss bug (now closed). The open #9397 raises the bar further: an empty `allowed_groups` should mean "permit none," not "permit all"—a security-default concern.
- **Config CLI inconsistency** (#9652 ✅): Cron key aliases with hyphens were accepted by the TOML loader and scheduler but rejected by `config set`, breaking the documented workflow. This inconsistency is now resolved.

## 8. Backlog Watch

| Issue | Days Open | Concern |
|---|---|---|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — Chat Completions profile | ~35 days | High-visibility compatibility RFC; still needs maintainer review |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Shell confirmation tiers | ~64 days | Scope confirmed but not yet implemented;

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*