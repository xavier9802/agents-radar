# OpenClaw Ecosystem Digest 2026-08-19

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-19 01:40 UTC

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



# OpenClaw Project Digest — 2026-08-19

## 1. Today's Overview

OpenClaw is in a phase of intense stability remediation. With 500 issues and 500 PRs updated in the last 24 hours (478 open issues, 402 open PRs), the project is processing a massive backlog of session-state, crash-loop, and data-loss bugs introduced during the 5.x → 6.x → 7.x migration wave. No new releases were shipped today, but 98 PRs were merged or closed — a strong signal that the maintainer team is actively triaging and closing out fixes. The dominant theme across the issue tracker is **session-state integrity under concurrent load**, with multiple diamond-lobster-rated bugs affecting the gateway event loop, SQLite transcript cleanup, and crash-recovery paths.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

**Notable merged/closed activity (from PR status tags and closed issues):**

- **#116489** [CLOSED] — Security policy install acknowledgment: external `security.installPolicy` commands can now return `warn`, requiring explicit operator confirmation before installing suspicious plugins or skills. This is a significant security hardening step for the plugin ecosystem.

**PRs advancing features or fixes today:**

- **#126074** — Session sidebar category controls exposed via the `sessions` tool; agents can now atomically assign categories at session creation.
- **#124014** — Auth provider profile reset now only affects the profile replaced by a successful login, preventing credential cascading on failed auth attempts.
- **#125528** — Claude CLI backend now end-to-end applies thinking levels and keeps live sessions warm for prompt-cache reuse across compatible turns.
- **#126109** — Link favicons enabled by default in the Control UI (previously behind a guarded feature flag).
- **#120491** — Per-turn, per-target send budget guard added to `message` and `conversations_send` tools to curb within-turn duplicate-answer storms.
- **#126088** — Explicit secrets access model introduced: operators can now mark values as hidden secrets vs. agent-readable environment entries with distinct access boundaries.

---

## 4. Community Hot Topics

| # | Issue | Comments | Rating | Link |
|---|-------|----------|--------|------|
| #116201 | Realtime voice retains unbounded provider/consult state | 60 | 🦞 diamond | [link](https://github.com/openclaw/openclaw/issues/116201) |
| #77598 | Live dev agent behavior tracking (24h watch) | 23 | 🦪 silver | [link](https://github.com/openclaw/openclaw/issues/77598) |
| #112423 | Large SQLite transcript cleanup blocks gateway event loop | 16 | 🦞 diamond | [link](https://github.com/openclaw/openclaw/issues/112423) |
| #115908 | Session transcript projection livelock under sustained writes | 15 | 🦞 diamond | [link](https://github.com/openclaw/openclaw/issues/115908) |
| #101290 | CLI preflight corrupts live SQLite state DB | 15 | 🦪 silver | [link](https://github.com/openclaw/openclaw/issues/101290) |

**Analysis:** The top 5 most-discussed issues all converge on **session-state durability and gateway event-loop blocking** under load. The realtime voice issue (#116201) with 60 comments indicates sustained community concern over resource leaks in voice sessions. The two SQLite blocking bugs (#112423, #115908) and the DB corruption bug (#101290) represent a coherent cluster: the database-first runtime's migration to SQLite has introduced concurrency and durability gaps that are affecting production users. The 24-hour agent watch (#77598) reflects the community's growing interest in observable, audit-friendly agent behavior tracking.

---

## 5. Bugs & Stability

### Critical / P0–P1 (Diamond Lobster & Platinum Hermit ratings)

| Issue | Summary | Fix PR? | Link |
|-------|---------|---------|------|
| #116201 | Realtime voice unbounded state retention | No | [link](https://github.com/openclaw/openclaw/issues/116201) |
| #112423 | SQLite transcript cleanup blocks gateway event loop | No | [link](https://github.com/openclaw/openclaw/issues/112423) |
| #115908 | Transcript projection livelock under sustained writes | No | [link](https://github.com/openclaw/openclaw/issues/115908) |
| #101290 | CLI preflight corrupts live SQLite DB | No | [link](https://github.com/openclaw/openclaw/issues/101290) |
| #111498 | Main agent blocked by persistent workspace-state migration after Anthropic auth recovery | No | [link](https://github.com/openclaw/openclaw/issues/111498) |
| #115546 | CLI-budget compaction timeout fires far below deadline; 100% failure on large sessions | No | [link](https://github.com/openclaw/openclaw/issues/115546) |
| #115424 | Gateway V8 heap OOM during main-session turn; restart-recovery converts crash to 7-core-dump loop | No | [link](https://github.com/openclaw/openclaw/issues/115424) |
| #88657 | DeepSeek V4 Flash incomplete turns (payloads=0) | No | [link](https://github.com/openclaw/openclaw/issues/88657) |
| #83959 | Codex app-server startup retries exhaust before replacement ready | No | [link](https://github.com/openclaw/openclaw/issues/83959) |
| #114211 | Matrix room agents loop on no-reply output; stale session replay after restart | No | [link](https://github.com/openclaw/openclaw/issues/114211) |
| #94939 | 6.x state migration leaves channel conversation-store SQLite empty (0 bytes) | Linked PR open | [link](https://github.com/openclaw/openclaw/issues/94939) |
| #112395 | Startup migration preflight blocks gateway after 6.11 → 7.1 upgrade | No | [link](https://github.com/openclaw/openclaw/issues/112395) |
| #103231 | `claude-cli` backend `ownsNativeCompaction` assumption false; sessions grow past 200% context | [CLOSED](https://github.com/openclaw/openclaw/issues/103231) | [link](https://github.com/openclaw/openclaw/issues/103231) |
| #125570 | Skill Workshop update apply overwrites live skill description, breaking skill routing | No | [link](https://github.com/openclaw/openclaw/issues/125570) |

### High-Visibility Regressions

| Issue | Summary | Link |
|-------|---------|------|
| #38327 | "Cannot convert undefined or null to object" with google-vertex/gemini-3.1-pro-preview since 2026.3.2 | [link](https://github.com/openclaw/openclaw/issues/38327) |
| #92241 | Gateway holds stale module import paths after rollback — inbound messages silently dropped | [link](https://github.com/openclaw/openclaw/issues/92241) |
| #90378 | Cron store silently migrated JSON→SQLite on upgrade; new jobs default to `delivery.mode=announce` causing channel errors | [link](https://github.com/openclaw/openclaw/issues/90378) |
| #91892 | Cron jobs stall during AI model calls (`model_call:stream_progress` never completes) | [link](https://github.com/openclaw/openclaw/issues/91892) |
| #91223 | Active memory injection breaks prompt cache hit rate (99.9% → 22%) | [link](https://github.com/openclaw/openclaw/issues/91223) |
| #86612 | Docker gateway container restart loop with `OPENCLAW_SANDBOX=1` on Windows | [link](https://github.com/openclaw/openclaw/issues/86612) |

**Stability assessment:** The project is in a fragile state. 14+ diamond-platinyum issues remain open with no fix PRs, spanning the gateway event loop, SQLite durability, session compaction, and crash-recovery paths. The `claude-cli` compaction bug (#103231) was closed but the underlying `ownsNativeCompaction` assumption may still affect other backends. Multiple migration-related bugs (#94939, #112395, #90378) suggest the 6.x→7.x migration path needs hardening before a stable release can be declared.

---

## 6. Feature Requests & Roadmap Signals

| # | Summary | Comments | Link |
|---|---------|----------|------|
| #79902 | Companion-friendly SQLite transcript/session seams for advanced consumers | 14 | [link](https://github.com/openclaw/openclaw/issues/79902) |
| #6757 | Agent-triggered context compaction (self-compact tool) | 8 | [link](https://github.com/openclaw/openclaw/issues/6757) |
| #45508 | Self-hosted STT/TTS provider support in webchat (bypass browser Speech API) | 7 | [link](https://github.com/openclaw/openclaw/issues/45508) |
| #95724 | Index memory by source directory, not by agent — eliminate duplicate vector stores | 6 | [link](https://github.com/openclaw/openclaw/issues/95724) |
| #49259 | Prune stale orphaned sessions from Dashboard Sessions | 7 | [link](https://github.com/openclaw/openclaw/issues/49259) |
| #39406 | Config option to suppress transient tool error warnings | 7 | [link](https://github.com/openclaw/openclaw/issues/39406) |
| #96975 | Isolate subagent completion from parent context; return status + child session link only | 12 | [link](https://github.com/openclaw/openclaw/issues/96975) |

**Roadmap prediction:** The self-compact tool (#6757) and companion-friendly SQLite seams (#79902) are the most likely candidates for the next feature release — both address core scalability pain points and have maintained community interest (8 and 14 comments respectively). The memory indexing by directory (#95724) is also a strong signal: multi-agent workspaces are a growing use case and the current per-agent vector store duplication is a known cost center. The self-hosted STT/TTS webchat feature (#45508) has been open since March and may ship as a plugin-first approach before being merged into core.

---

## 7. User Feedback Summary

**Pain points (most frequently raised):**

1. **Session state loss on upgrade/migration** — Multiple users report conversation stores becoming empty (0-byte SQLite) or stale after upgrading between 5.x, 6.x, and 7.x releases (#94939, #112395, #90378). This is the single most damaging user experience issue.
2. **Gateway event loop stalling** — Long-running sessions with large transcripts cause the Node event loop to block for tens of seconds (#112423, #115908), making the agent appear frozen to users across all channels.
3. **Crash-recovery loops** — When the gateway OOMs or crashes, the automatic restart-recovery can convert a single crash into an infinite loop (#115424), wasting resources and preventing service restoration.
4. **Auth/provider regressions** —anthropic auth recovery leaves agents blocked (#111498), Google Vertex calls throw type errors (#38327), and pasting a secondary API key can wipe the default agent's credentials (#116248 — PR open).
5. **Cron job unreliability** — Jobs stall during model calls (#91892), timers stop firing after heavy timeouts (#102534), and hot-reload triggers false "failed" notifications causing alert fatigue (#90595).
6. **Prompt cache collapse** — Active memory injection drops cache hit rates from ~99.9% to ~22% (#91223), dramatically increasing latency and cost for users who rely on the memory plugin.

**Satisfaction signals:** The closed security policy acknowledgment PR (#116489) and the auth profile fix (#124014) show the team is responsive to security and credential management concerns. The Claude CLI thinking-level support (#125528) addresses a highly requested capability. The per-turn send budget guard (#120491) shows responsiveness to agent misbehavior (duplicate-answer storms).

---

## 8. Backlog Watch

These long-open, high-impact items need maintainer attention:

| # | Issue | Created | Comments | Why It Matters |
|---|-------|---------|----------|----------------|
| #116201 | Realtime voice unbounded state retention | 2026-07-30 | 60 | Resource leak in voice sessions; blocks production voice deployments |
| #112423 | SQLite transcript cleanup blocks gateway event loop | 2026-07-21 | 16 | Directly impacts gateway responsiveness for all long-running sessions |
| #115908 | Transcript projection livelock under sustained writes | 2026-07-29 | 15 | Causes multi-second event-loop stalls; affects all channel transports |
| #101290 | CLI preflight corrupts live SQLite DB | 2026-07-07 | 15 | Data-loss bug on macOS; reproduces under normal gateway operation |
| #115546 | CLI-budget compaction 100% failure on large sessions | 2026-07-29 | 8 | Breaks context management for long conversations; no retry mechanism |
| #115424 | Gateway V8 heap OOM → crash-recovery loop | 2026-07-28 | 6 | Converts single crash into sustained service disruption |
| #79902 | Companion-friendly SQLite transcript seams | 2026-05-09 | 14 | Enables third-party tooling on top of the database-first runtime |
| #96975 | Isolate subagent completion from parent context | 2026-06-26 | 12 | Prevents parent session bloat from heavy subagent workloads |
| #83959 | Codex app-server startup retry exhaustion | 2026-05-19 | 11 | Blocks scheduled background agent turns using the Codex harness |
| #114612 | SQLite memory tables have no retention policy | 2026-07-27 | 8 | Unbounded disk growth; will fill production disks over time |

**Overall project health:** The project is in a **remediation-heavy** phase. The volume of open P1/P0 issues (14+ diamond/platinum-rated bugs) relative to merged fixes suggests the 6.x→7.x transition has introduced systemic stability debt. The maintainer team is active (98 PRs closed/merged in 24h) but the bug surface outpaces the fix rate. The next stable release should be contingent on resolving the session-state and SQLite durability cluster (#112423, #115908, #101290, #115546) before new features are prioritized.

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Report — 2026-08-19

## 1. Ecosystem Overview

The open-source personal AI assistant and agent ecosystem is in a consolidation-and-hardening phase. After a wave of major version migrations (notably OpenClaw's 5.x→7.x and NanoClaw's async DB refactor), projects are prioritizing session-state durability, security hardening, and cross-platform reliability over new features. Activity is highly uneven: the top four projects (OpenClaw, ZeroClaw, CoPaw, IronClaw) process 40–50+ issues/PRs daily, while two (NullClaw, ZeptoClaw) show zero activity and PicoClaw operates at a slow, maintenance pace. The dominant technical challenge across all active projects is session-state integrity under concurrent load — a problem that no single project has fully resolved.

## 2. Activity Comparison

| Project | Open Issues | Open PRs | PRs Updated (24h) | Release (24h) | Health Score* |
|---|---|---|---|---|---|
| OpenClaw | 478 | 402 | ~900 (500 issues + 500 PRs) | None | ⚠️ Fragile |
| ZeroClaw | ~50+ | ~50+ | ~100 | None | 🟡 Active |
| CoPaw | ~45+ | ~50+ | ~95 | None | 🟡 Active |
| IronClaw | ~21 | ~40 | ~61 | RC.2 | 🟢 Stable |
| NanoBot | ~10+ | ~28+ | ~38 | None | 🟢 Healthy |
| Hermes Agent | 39 | 37 | ~100 | v0.20.4 (prev day) | 🟢 Healthy |
| NanoClaw | 3 | 23 | ~41 | None | 🟡 Refactoring |
| LobsterAI | 9 | 19 | ~25 | 2026.8.18 | 🟡 Backlog-heavy |
| Moltis | 0 | ~6 | ~6 | 2 builds | 🟢 Shipping |
| PicoClaw | 5 | 4 | ~10 | None | 🔴 Stagnant |
| NullClaw | — | — | 0 | — | ⛔ Inactive |
| ZeptoClaw | — | — | 0 | — | ⛔ Inactive |

*Health Score: composite of fix velocity, P0 backlog, release cadence, and community responsiveness.

## 3. OpenClaw's Position

**Advantages vs. peers:** OpenClaw remains the most feature-complete platform with the largest community (478 open issues, 60-comment top issue). It offers the broadest channel ecosystem (Matrix, Slack, Discord, WhatsApp, Signal, Telegram, WebChat), the richest tool surface (MCP, skills, cron, subagents), and the most mature plugin architecture. Its recent security hardening (explicit secrets model, `security.installPolicy` acknowledgment) and per-turn send-budget guards show responsiveness to production concerns.

**Technical approach differences:** OpenClaw is uniquely **database-first** — its entire session layer is built on SQLite, which has become both its greatest strength (transcript query-ability, companion-friendly seams) and its greatest vulnerability (the entire P0 bug cluster centers on SQLite concurrency, compaction, and migration). NanoClaw is making the same architectural bet but is refactoring toward an async, driver-portable database. Hermes Agent and IronClaw are more service-oriented with gateway+desktop split architectures. Moltis and PicoClaw are lighter-weight runtime/conductor projects.

**Community size:** OpenClaw is an order of magnitude larger than any peer by issue/PR volume. ZeroClaw and CoPaw are the next tier (~50 each). NanoBot and Hermes occupy a mid-tier. PicoClaw, LobsterAI, and Moltis are smaller. NullClaw and ZeptoClaw appear dormant.

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Session-state durability** | OpenClaw, Hermes, NanoClaw, ZeroClaw, IronClaw | SQLite compaction, transcript projection livelocks, crash-recovery loops, migration data loss, context recall across sessions |
| **Cross-platform reliability (Windows)** | NanoBot, Hermes, ZeroClaw, IronClaw, OpenClaw | PID handoff failures, self-update locks, approval prompt timeouts, 74 test failures, gateway restart loops |
| **Credential & security hardening** | OpenClaw, NanoBot, CoPaw, ZeroClaw | Explicit secrets model, subprocess sandboxing (ulimits/cgroups), master-key permissions, OAuth refresh rotation, credential exposure in URLs |
| **Multi-agent / multi-profile isolation** | OpenClaw, Hermes, ZeroClaw, LobsterAI | Cross-profile session leakage, DB misrouting in `--isolated` mode, shared primary-profile history divergence |
| **Channel reliability & retry** | CoPaw, OpenClaw, ZeroClaw, NanoBot | Matrix/Feishu auto-reconnect, Slack MCP health probes evicting live sessions, WhatsApp audio send failure, Codex WebSocket silent stalls |
| **Prompt cache / cost optimization** | OpenClaw, PicoClaw, ZeroClaw | Prompt cache collapse from memory injection (99.9%→22% hit rate), cache token observability, per-model capability negotiation |
| **Provider diversity & routing** | NanoClaw, ZeroClaw, LobsterAI, Moltis | LiteLLM router skills, DSH engine, Hailo-Ollama, Grok Build ACP, per-credential rate-limit cooling |
| **Observability & auditability** | NanoBot, OpenClaw, IronClaw, ZeroClaw | LangSmith tracing regressions, 24h agent behavior tracking, downloadable conversation artifacts with timing data, session export quality |

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | NanoClaw | IronClaw | ZeroClaw | NanoBot | Moltis | LobsterAI | PicoClaw |
|---|---|---|---|---|---|---|---|---|---|
| **Primary paradigm** | Gateway + Desktop + multi-channel | Desktop-first with gateway | Runtime/conductor with driver seam | Automation platform | Async Rust gateway | Lightweight multi-channel bot | Home automation hub | Desktop Electron client | Edge/IoT gateway |
| **Target user** | Power users, enterprise | Desktop power users, Mac users | Developers, self-hosters | Automation engineers | Developers, infra-focused | Hobbyists, multi-channel tinkerers | Smart home / IoT operators | Chinese-market desktop users | Raspberry Pi / edge |
| **DB architecture** | SQLite-first (migration debt) | Hybrid (PostgreSQL + SQLite) | Async driver-portable (refactoring) | libSQL (recently fixed starvation) | Async Rust, driver-based | Provider-agnostic | Runtime-specific | SQLite | SQLite |
| **Channel breadth** | Very broad (10+) | Broad (Signal, Slack, Discord, Telegram) | Broad (Slack, Discord, Telegram, Webex) | Broad (Slack, Telegram, Web) | Broad (Matrix, DingTalk, Web) | Broad (WhatsApp, Telegram, Discord) | Connector-focused | Desktop + MCP | Narrow (IRC, Telegram) |
| **Session model** | Per-session transcript + compaction | Per-project persistent agents | Driver-abstracted runtime | Durable inbox + automation runs | Multi-turn goal mode (RFC) | Cross-session messaging | Persistent sessions | Task/activity filter | Dispatch-rule routing |
| **Security posture** | Explicit secrets, policy ack | Browser exec URL re-check | Workspace restriction (P1 open) | Toast-based feedback | Per-provider credential rotation | No subprocess limits (P1 open) | Heartbeat patching | MCP quick-add templates | customAllowPatterns bug |

## 6. Community Momentum & Maturity

**Tier 1 — High Velocity, Shipping Regularly:**
- **IronClaw** — RC cycle with same-day bug fixes, 40 PRs/24h, clean release rhythm. Most mature release discipline.
- **Hermes Agent** — v0.20.4 shipped yesterday with 74 PRs; strong same-day fix turnaround; active Desktop UX investment.
- **Moltis** — 2 releases in 24h, 6 PRs merged, zero open bugs. Small but exceptionally efficient.

**Tier 2 — Active Development, Accumulating Debt:**
- **OpenClaw** — Massive volume (900 updates/24h) but bug surface outpaces fixes. 14+ P0/P1 items with no fix PRs. The 6.x→7.x migration debt is the defining risk.
- **ZeroClaw** — Strong contributor cadence (50/50 issues/PRs), good RFC discipline, but two long-standing P1s (#8642 MCP memory, #7462 Windows tests) are unaddressed.
- **CoPaw** — High activity with rapid security patches, but multiple P1 freezes and regressions suggest the codebase is under stress.
- **NanoClaw** — Very high PR volume (41/24h) but driven almost entirely by a single refactoring wave (async DB + session drivers). No release in sight; feature work is paused.

**Tier 3 — Steady but Smaller:**
- **NanoBot** — Healthy 28 PRs/24h, responsive to regressions, but Windows gaps and the unpatched subprocess sandboxing (#4797, 74 days open) are credibility risks.
- **LobsterAI** — Good merge velocity (16 PRs merged) but 4+ month stale backlog on high-severity bugs (#1587, #1589, #1627).

**Tier 4 — Stagnant / Inactive:**
- **PicoClaw** — 4 PRs updated, 2 stale, 2 high-severity bugs unaddressed. Web UI (8 👍) is 5.5 months old with no merged PR.
- **NullClaw** — Zero activity.
- **ZeptoClaw** — Zero activity.

## 7. Trend Signals

1. **Session-state durability is the ecosystem's unsolved problem.** Every major project has a cluster of bugs around transcript cleanup, compaction, crash recovery, or context recall. OpenClaw's SQLite blocking bugs, Hermes' 4030 compaction errors, ZeroClaw's MCP RSS growth, and IronClaw's context recall gap are different manifestations of the same root challenge: long-lived agent sessions with unbounded state. *Value for developers: any new project entering this space must treat session compaction and crash recovery as first-class concerns, not afterthoughts.*

2. **Windows is the universal weak point.** NanoBot (PID handoff, weather curl), Hermes (profile switch hangs, update self-lock, approval timeouts), ZeroClaw (74 test failures), and OpenClaw (Docker restart loops) all have Windows-specific regressions. *Value: cross-platform CI coverage is a competitive differentiator; projects that ship reliable Windows builds will capture an underserved segment.*

3. **Security hardening is accelerating but uneven.** Explicit secrets (OpenClaw), shell-evasion defaults (CoPaw), master-key permissions (CoPaw), workspace restriction (NanoBot), browser URL re-check (Hermes), credential rotation (ZeroClaw) — all recent additions. The common gap is subprocess sandboxing: NanoBot's P1 (#4797) remains unfixed at 74 days. *Value: the market is moving toward zero-trust agent runtime assumptions; projects that ship with sane defaults (cgroups, workspace isolation, credential scoping) will gain enterprise trust.*

4. **Multi-provider / multi-engine routing is table stakes.** DSH (LobsterAI), LiteLLM router (NanoClaw), Hailo-Ollama (ZeroClaw), Grok Build ACP (ZeroClaw), Hermes engine support requested (LobsterAI), per-credential rate-limit cooling (ZeroClaw). *Value: vendor lock-in is a primary user concern; projects that make provider switching seamless will win self-hosted deployments.*

5. **Desktop UX maturity is the next frontier.** Hermes is investing in guided UI tours, persistent per-project agents, and Quick Entry polish. IronClaw is unifying feedback components and adding voice input. OpenClaw is exposing session sidebar controls. *Value: the wedge from CLI-to-production is UX; projects that reduce the friction of session management, error recovery, and onboarding will capture non-technical users.*

6. **Observability and auditability are becoming differentiators.** LangSmith tracing (NanoBot), 24h behavior tracking (OpenClaw), downloadable timing artifacts (IronClaw), prompt cache token logging (PicoClaw), session export quality (LobsterAI). *Value: enterprise buyers require audit trails; projects that make observability built-in rather than bolted-on will have a structural advantage.*

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-19

## 1. Today's Overview

NanoBot showed robust contributor activity on 2026-08-19, with **28 PRs** updated and **10 issues** touched in a single 24-hour window — a strong signal of sustained development momentum. The project is in a high-velocity patching phase, with multiple security fixes, platform regressions (notably Windows), and async lifecycle bugs receiving immediate attention. No new releases were published, suggesting the team is consolidating changes rather than shipping them yet. The volume of overlapping conflict-tagged PRs hints at a growing codebase where merge coordination is becoming a bottleneck.

## 2. Releases

No new releases published in the last 24 hours.

---

## 3. Project Progress

**Merged / Closed PRs today:**

| PR | Title | Author |
|---|---|---|
| [#5433](https://github.com/HKUDS/nanobot/pull/5433) | test(exec): wait deterministically for truncation output | @chengyongru |
| [#5358](https://github.com/HKUDS/nanobot/pull/5358) | feat(webui): add lightweight cross-session messaging | @chengyongru |
| [#5432](https://github.com/HKUDS/nanobot/pull/5432) | fix(tui): refresh expired API credentials | @chengyongru |

**Key advances:**
- **Cross-session messaging** (#5358) gives persisted sessions stable `@handles` and enables direct inter-session communication through the existing inbound message bus — a notable UX feature for multi-session users.
- **TUI credential refresh** (#5432) eliminates a friction point where expired API tokens silently broke sessions; concurrent refreshes are now deduplicated.
- **Windows exec test flake** (#5433) replaces a brittle 500 ms poll with an output-aware wait, improving CI reliability on Windows.

---

## 4. Community Hot Topics

**Most discussed issues:**

- **[#2493](https://github.com/HKUDS/nanobot/issues/2493) — LangSmith integration broken after latest update** (7 comments, 1 👍)
  The removal of `litellm_provider.py` broke LangSmith tracing. A fix PR (#5436) has already been opened by @ojassharma7. This reflects a real pain point: users relying on observability tooling are sensitive to provider-layer refactors that silently drop integrations.

- **[#5149](https://github.com/HKUDS/nanobot/issues/5149) — No audio on WhatsApp** (6 comments)
  Audio messages are received but never sent on WhatsApp. Likely tied to the neonize/ffmpeg pipeline. Still open with no assigned fix PR as of today.

**Most active PRs (by engagement signals):**

- [#5437](https://github.com/HKUDS/nanobot/pull/5437) — Serply web-search provider (new provider request)
- [#5234](https://github.com/HKUDS/nanobot/pull/5234) — mst-python metasearch provider (multi-engine aggregation via RRF)
- [#5212](https://github.com/HKUDS/nanobot/pull/5212) — MiniMax music generation guidance
- [#5408](https://github.com/HKUDS/nanobot/pull/5408) — WebUI follow-up suggestions
- [#4880](https://github.com/HKUDS/nanobot/pull/4880) — Default `restrict_to_workspace` to `True` (security)

**Underlying need:** The community is pushing hard on **search provider diversity** (3 search-related PRs in the window) and **UI experience polish** (follow-up suggestions, cross-session messaging). Security hardening is also a clear signal with the workspace restriction PR.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| **P1 — Security** | [#4797](https://github.com/HKUDS/nanobot/issues/4797) | No resource limits on shell subprocesses; fork bombs and resource exhaustion possible | [#4880](https://github.com/HKUDS/nanobot/pull/4880) addresses workspace restriction but not cgroups/ulimits directly |
| **P1 — Regression (Windows)** | [#5417](https://github.com/HKUDS/nanobot/issues/5417) | WebUI exits when gateway rejects virtualenv PID handoff on Windows | [#5415](https://github.com/HKUDS/nanobot/pull/5415) (open) |
| **P2 — Regression** | [#2493](https://github.com/HKUDS/nanobot/issues/2493) | LangSmith tracing broken after provider refactor | [#5436](https://github.com/HKUDS/nanobot/pull/5436) (open) |
| **P2 — Bug** | [#5425](https://github.com/HKUDS/nanobot/issues/5425) | `socks://` proxy URLs rejected for custom OpenAI-compatible providers | [#5435](https://github.com/HKUDS/nanobot/pull/5435) (open) |
| **P2 — Bug (async)** | [#5429](https://github.com/HKUDS/nanobot/issues/5429) | `AgentLoop` discards background task exceptions without logging | [#5431](https://github.com/HKUDS/nanobot/pull/5431) (open) |
| **P2 — Bug (async)** | [#5428](https://github.com/HKUDS/nanobot/issues/5428) | Empty `_active_tasks` sets retained after session tasks complete (memory leak) | [#5430](https://github.com/HKUDS/nanobot/pull/5430) (open) |
| **P2 — Bug** | [#5149](https://github.com/HKUDS/nanobot/issues/5149) | WhatsApp audio send failure | None yet |

**Assessment:** Two async lifecycle bugs (#5428, #5429) share the same author and are being fixed in paired PRs — good sign of systematic cleanup. The Windows PID handoff regression and the missing subprocess sandboxing remain the highest-risk open items.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Next Release |
|---|---|---|
| Serply web-search provider | [#5437](https://github.com/HKUDS/nanobot/pull/5437) | **High** — follows existing Serper pattern, minimal integration surface |
| mst-python metasearch provider | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | **Medium** — larger scope, marked P1 but has conflicts |
| MiniMax music generation guidance | [#5212](https://github.com/HKUDS/nanobot/pull/5212) | **Medium** — adds discoverability to existing music stack |
| WebUI follow-up suggestions | [#5408](https://github.com/HKUDS/nanobot/pull/5408) | **High** — UX polish, low risk, directly requested |
| Mattermost system-post filtering | [#5434](https://github.com/HKUDS/nanobot/pull/5434) | **High** — narrow fix, improves Mattermost channel experience |
| Budget model-visible MCP schemas | [#5388](https://github.com/HKUDS/nanobot/pull/5388) | **Low–Medium** — opt-in, sophisticated; may need more review |
| Weather skill Windows compatibility | [#5341](https://github.com/HKUDS/nanobot/pull/5341) | **High** — narrow cross-platform fix |

**Signal:** The roadmap is trending toward **provider expansion** (search, music), **platform reliability** (Windows, proxy), and **UX refinement** (follow-ups, cross-session messaging). Security hardening is also accelerating.

---

## 7. User Feedback Summary

- **Observability is non-negotiable.** The LangSmith issue (#2493) has 1 👍 and 7 comments — users building on NanoBot depend on tracing for production debugging. Provider-layer refactors must preserve or explicitly document migration paths for integrations.
- **Windows support is fragile.** Two Windows-specific bugs (PID handoff #5417, weather curl #5341) surfaced in the same window. The Windows user base appears underserved relative to Linux/macOS, and CI gaps are letting regressions through.
- **Audio on WhatsApp is a dealbreaker for some.** Issue #5149 describes a complete break in media send capability — users who rely on NanoBot for voice-enabled WhatsApp automation are blocked.
- **Resource sandboxing is a growing concern.** Issue #4797 (no ulimit/cgroups on subprocesses) and the "surprise LLM bills" issue (#5409, now closed) both point to users running unconfined agents in shared or low-resource environments. This is a credibility risk as the project matures.
- **Prosocial spam is present.** Issues #5372 (ViBo memory sales pitch) and #5409 (budget firewall proposal from an external account) suggest the project is attracting promotional / vendor outreach. Maintainers should consider stricter issue screening.

---

## 8. Backlog Watch

| Issue / PR | Age | Why It Needs Attention |
|---|---|---|
| [#4797](https://github.com/HKUDS/nanobot/issues/4797) — No resource limits on shell subprocesses | ~74 days | Security-critical; no fix PR yet. Unconfined subprocesses are a liability for any production deployment. |
| [#5149](https://github.com/HKUDS/nanobot/issues/5149) — WhatsApp no audio send | ~23 days | 6 comments, no fix. Blocks a core multimodal use case. |
| [#5421](https://github.com/HKUDS/nanobot/issues/5421) — Idle compaction & concurrent provider state | ~1 day | Design-question issue with no resolution yet; impacts correctness of the consolidation pipeline. Needs maintainer input before any PR can land. |
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) — mst-python metasearch | ~17 days | P1 priority but marked conflict; blocking on merge coordination. |
| [#4880](https://github.com/HKUDS/nanobot/pull/4880) — Default `restrict_to_workspace` to `True` | ~39 days | P1 security PR with conflict tag; long-open security default change needs triage. |
| [#5411](https://github.com/HKUDS/nanobot/pull/5411) — Refactor CLI: isolate local agent runtime | ~2 days | Large refactor with conflict tag; could unblock cleaner architecture but needs review bandwidth. |

**Overall health assessment:** NanoBot is in a healthy development cycle with high PR volume and rapid response to regressions. The main risks are the **unpatched security gap around subprocess sandboxing**, **Windows platform regressions**, and **merge conflicts piling up on key PRs** — all of which require maintainer triage attention in the near term.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-19

## 1. Today's Overview

Hermes Agent is in an active patch-and-stabilize phase following the v0.20.4 release (2026.8.18), which bundled ~74 merged PRs. The project saw high daily velocity today: 50 issues and 50 PRs touched within 24 hours, with 39 open issues and 37 open PRs. Activity is heavily weighted toward Desktop session-state bugs and Windows platform regressions introduced by the recent gateway profile-switch refactor. Overall project health is solid — maintainer responsiveness is strong with multiple same-day fixes — but a cluster of P2 session-state risks on Windows and Desktop warrants close monitoring.

## 2. Releases

**v0.20.4 (v2026.8.18)** — Patch release rolling up ~74 PRs since v0.20.3. Targets Docker images, hosted deployments, and fresh installs. No breaking changes announced.

## 3. Project Progress

### Merged / Closed PRs Today
- **#89619** — Auto lint/format pass (`npm run fix`) applied and squash-merged ([link](https://github.com/NousResearch/hermes-agent/pull/89619))
- **#86961** — Disabled native window shadow on macOS Quick Entry (⌘⇧Space), eliminating the visible border ring ([link](https://github.com/NousResearch/hermes-agent/pull/86961))
- **#89467** — `clarify` tool extended to ask 2–5 independent questions per call, cutting round-trip latency for composite clarifications ([link](https://github.com/NousResearch/hermes-agent/pull/89467))
- **#70129** — `clarify_form` tool for multi-question clarify merged as the underlying implementation ([link](https://github.com/NousResearch/hermes-agent/pull/70129))
- **#58828** — Fixed `/goal` turn counter stuck at 0 when streaming enabled — the goal continuation hook was skipped on streaming responses ([link](https://github.com/NousResearch/hermes-agent/pull/58828))
- **#84999** — Security: browser_exec now re-checks the landed URL after execution, closing a prompt-injection vector where the post-execution URL could diverge from the pre-launch whitelist ([link](https://github.com/NousResearch/hermes-agent/pull/84999))

### Notable Open PRs Advancing
- **#89620** — Live guided UI tours: Hermes can dim the screen, spotlight UI elements, and narrate walkthroughs via a generic `tour` tool ([link](https://github.com/NousResearch/hermes-agent/pull/89620))
- **#89567** — Persistent per-Project agents for Desktop, resuming stable stored sessions with prompt-cache reuse ([link](https://github.com/NousResearch/hermes-agent/pull/89567))
- **#89582** — HERMES HARNESS: recoverable tool-result context economy layer ([link](https://github.com/NousResearch/hermes-agent/pull/89582))
- **#88092** — Fixes 4030 edit-refusal on long Desktop sessions by truncating by durable row ID instead of ordinal ([link](https://github.com/NousResearch/hermes-agent/pull/88092))
- **#89621** — Surfaces profile-switch failures in Desktop instead of silent swallow ([link](https://github.com/NousResearch/hermes-agent/pull/89621))
- **#89616** — Scopes `resolveStoredSession()` to the active Desktop profile, fixing cross-profile session lookups ([link](https://github.com/NousResearch/hermes-agent/pull/89616))
- **#89379** — Preserves history for shared primary-profile routes in the gateway ([link](https://github.com/NousResearch/hermes-agent/pull/89379))
- **#88504** — Paginates archived sessions beyond the 200-row cap in Desktop ([link](https://github.com/NousResearch/hermes-agent/pull/88504))
- **#53696** — Signal adapter migrated to signal-cli-rest-api v0.99 (WebSocket + REST) ([link](https://github.com/NousResearch/hermes-agent/pull/53696))
- **#89618** — Keeps `agent-browser` as a managed Hermes dependency rather than npx-only, fixing cron breakage on workspace refreshes ([link](https://github.com/NousResearch/hermes-agent/pull/89618))

## 4. Community Hot Topics

| # | Type | Title | Comments | Link |
|---|------|-------|----------|------|
| #66616 | Bug | Skills index stale/degraded (29.8h old, limit 26h) | 54 | [link](https://github.com/NousResearch/hermes-agent/issues/66616) |
| #88275 | Bug | Desktop renderer burns 40–73% CPU at idle on macOS Intel, thermal throttling | 9 | [link](https://github.com/NousResearch/hermes-agent/issues/88275) |
| #53902 | Bug | v0.17.0 renderer stuck in fontations+temporal_rs loop, GPU 98%, 13W sustained | 8 | [link](https://github.com/NousResearch/hermes-agent/issues/53902) |
| #88897 | Bug | `--isolated` dashboard writes sessions to root DB instead of profile DB | 6 | [link](https://github.com/NousResearch/hermes-agent/issues/88897) |
| #18885 | Feature | Allow memory-provider tools in cron jobs via `allow_memory` flag | 5 | [link](https://github.com/NousResearch/hermes-agent/issues/18885) |

**Analysis:** The top issue (#66616) is an automated watchdog alert, not a user-reported bug per se, but 54 comments indicate sustained community concern over skills-index freshness. The two highest-comment Desktop performance issues (#88275, #53902) both trace to Electron renderer inefficiencies — one a recent regression (early August), the other a longer-standing v0.17.0 loop. Users are clearly feeling the heat on macOS Intel hardware. The `--isolated` profile DB bug (#88897) and the memory-in-cron feature request (#18885) reflect two distinct user needs: correct multi-profile isolation, and autonomous memory maintenance.

## 5. Bugs & Stability

### Critical / High Severity (P2)

| Issue | Summary | Fix PR? | Link |
|-------|---------|---------|------|
| #89586 | Profile switching hangs silently on Windows after gateway refactor | #89621 (surface failures), #89616 (scope fix) | [link](https://github.com/NousResearch/hermes-agent/issues/89586) |
| #89599 | `hermes update` self-locks its own launcher exe on Windows (EACCES) | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/89599) |
| #89244 | Desktop Restore after in-place compaction refused with 4030 (ordinal ≠ row_id mismatch) | #88092 | [link](https://github.com/NousResearch/hermes-agent/issues/89244) |
| #85624 | Auto-title fails 100% on Bedrock/Anthropic: OpenAI `response_format` leaked | #82816 (same root cause, OpenAI compat) | [link](https://github.com/NousResearch/hermes-agent/issues/85624) |
| #89576 | MCP health probe opens second HTTP session, evicts live session (Slack MCP) | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/89576) |
| #89556 | Re-opening already-focused session from Bots panel hangs forever | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/89556) |
| #89346 | Shared primary profile routes reload session history from root store after #88734 | #89379 | [link](https://github.com/NousResearch/hermes-agent/issues/89346) |
| #89111 | Gateway approval prompts time out on remote Windows Desktop clients | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/89111) |
| #18421 | `/goal` judge false positive when agent claims file created but write silently fails | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/18421) |
| #17157 | Discord slash-command sync times out (recreating unchanged commands) | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/17157) |

### Medium Severity (P3)

| Issue | Summary | Fix PR? | Link |
|-------|---------|---------|------|
| #89600 | `hermes plugins enable` hangs indefinitely when stdout redirected (no isatty guard) | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/89600) |
| #74933 | Hindsight provider rejects shared observation scope, fragments by session | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/74933) |
| #89561 | `hermes config set` stores composite values (lists/mappings) as strings | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/89561) |
| #88895 | `gateway.error.log` no rotation + Slack socket-mode reconnect traceback spam (141 MB) | None yet | [link](https://github.com/NousResearch/hermes-agent/issues/88895) |

### Closed Today
- #83147 — WebSocket reconnect recovers persisted turns without duplicates (fixed)
- #89546 — Hover close buttons hidden on persistent SESSIONS\|BOTS tabs (fixed)
- #89175 — Goal bootstrap grace window race on slow disks (fixed)
- #88955 — Bot Mode group chat empty hidden messages re-triggering sanitizer (fixed)

**Assessment:** Windows platform stability is the weakest area today, with at least 3 P2 bugs directly tied to the recent atomically-published gateway switch refactor. The 4030 compaction bug (#89244) has an active fix PR (#88092). The update-self-lock (#89599) and approval-prompt-timeout (#89111) on Windows remain unfixed and could block adopters on that platform.

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Request | Likelihood for Next Release |
|----------|---------|----------------------------|
| #18885 / — | Memory-provider tools in cron jobs (`allow_memory` flag) | Medium — requires security review |
| #89620 | Live guided UI tours via `tour` tool | High — PR already open, demo-ready |
| #89567 | Persistent per-Project agents in Desktop | High — PR open, aligns with project workflow |
| #89304 | Desktop profile alias targeting remote gateway profile | Medium — nice-to-have for federated setups |
| #89549 | xAI video gen 1080p support (currently clamped to 720p) | Low — doc vs implementation gap, easy fix |
| #88307 | Always-visible connection picker in status bar | Low — UX polish |
| #9056 | Nix Home Manager module (closed, 12 👍) | Already merged/closed |

**Signal:** The project is investing heavily in Desktop UX maturity (tours, project agents, profile routing fixes) while maintaining gateway stability. The HERMES HARNESS context economy (#89582) suggests a longer-term architecture shift toward recoverable tool-result sessions.

## 7. User Feedback Summary

**Pain points:**
- **Windows regressions** from the gateway profile-switch refactor are causing silent failures (profile switch hangs, update broken, approval prompts not propagating). This is the dominant complaint.
- **Desktop performance on macOS Intel** remains poor — two separate issues report renderer CPU/GPU abuse, with #53902 affecting users since v0.17.0.
- **Session state integrity** is a recurring theme: 4030 errors on edit/restore, shared-profile history divergence, isolated-mode DB misrouting. Users building long sessions hit these wall.
- **MCP health probes** breaking live sessions (Slack) is a correctness issue for users relying on MCP-integrated workflows.
- **Log rotation gap** — `gateway.error.log` hit 141 MB unrotated, indicating production environments are underserved on observability hygiene.

**Satisfaction signals:**
- Strong appreciation for the `clarify` multi-question improvement (reduced round-trips).
- The `/goal` streaming fix (#58828) resolves a long-standing correctness gap.
- Browser security re-check (#84999) addresses community trust concerns around prompt injection.
- Quick Entry shadow fix (#86961) is a quality-of-life win for macOS users.

## 8. Backlog Watch

| Issue | Why It Needs Attention | Days Open | Link |
|-------|----------------------|-----------|------|
| #89599 | `hermes update` completely broken on Windows — blocks all Windows users from upgrading | 1 | [link](https://github.com/NousResearch/hermes-agent/issues/89599) |
| #89586 | Profile switching silent-hang on Windows — core Desktop workflow broken | 1 | [link](https://github.com/NousResearch/hermes-agent/issues/89586) |
| #66616 | Skills index watchdog firing repeatedly (54 comments, open since July 18) | 32 | [link](https://github.com/NousResearch/hermes-agent/issues/66616) |
| #53902 | v0.17.0 renderer loop — 13W sustained power draw, open since June 28 | 52 | [link](https://github.com/NousResearch/hermes-agent/issues/53902) |
| #88275 | Desktop CPU burn on macOS Intel — thermal throttling, open since Aug 17 | 2 | [link](https://github.com/NousResearch/hermes-agent/issues/88275) |
| #89599 + #89111 | Two distinct Windows bugs from same refactor — suggest a Windows regression sweep | — | [links above] |
| #18421 | `/goal` false-positive on silent file-write failure — trust boundary issue | 110 | [link](https://github.com/NousResearch/hermes-agent/issues/18421) |

**Priority recommendation:** The Windows platform cluster (#89599, #89586, #89111) should be treated as a release-blocking set for any future patch. The Skills index watchdog (#66616) and the v0.17 renderer loop (#53902) are long-open issues affecting production reliability and deserve maintainer-level investigation.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-19

## 1. Today's Overview

PicoClaw shows moderate but steady activity with 6 open issues and 4 PRs updated in the last 24 hours. Two PRs were merged/closed today (#1158 and #3317), advancing protocol support and observability. Five issues remain open and active, including high-priority feature work on Web UI support and several bug reports around routing, CPU usage, and API integrations. No new releases were published. The project appears to be in a phase of incremental hardening—fixing configuration bugs, adding protocol support, and gathering feedback for a planned Web UI—rather than launching major new versions.

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Project Progress

| PR | Status | Summary |
|----|--------|---------|
| [#1158](https://github.com/sipeed/picoclaw/pull/1158) | **Merged** | Added `anthropic-messages` protocol, enabling native Anthropic API format support (`/v1/messages` endpoint). Fixes #269. |
| [#3317](https://github.com/sipeed/picoclaw/pull/3317) | **Merged** | Logs prompt cache tokens in LLM response debug output, improving observability for providers like DeepSeek via Cloudflare AI Gateway. |
| [#3329](https://github.com/sipeed/picoclaw/pull/3329) | Open (stale) | Warns on inert `webhook_host` / `webhook_port` config keys instead of silently seeding them. Fixes #3328. |
| [#3314](https://github.com/sipeed/picoclaw/pull/3314) | Open (stale) | Fixes `customAllowPatterns` not working—default deny patterns were overriding user-defined allow rules in `guardCommand`. |

**Key advances:** Native Anthropic protocol support is now merged, and debug logging for prompt cache tokens improves cost transparency. Two bug-fix PRs remain open and stale, awaiting maintainer review.

---

## 4. Community Hot Topics

- **[Issue #806](https://github.com/sipeed/picoclaw/issues/806) — Web UI support** · 9 comments · 8 👍 · Updated 2026-08-18
  The most reacted-to open issue. Proposes a browser-based interface to lower the barrier for non-technical users managing PicoClaw instances. Author notes refactoring is underway. This signals a strong community demand for accessibility beyond the TUI.

- **[Issue #3287](https://github.com/sipeed/picoclaw/issues/3287) — Better support for long IRC messages** · 6 comments · Updated 2026-08-18
  Requests that PicoClaw treat IRCv3-split messages (>512 bytes) as a single cohesive input. Reflects real-world IRC usage where modern clients fragment long messages.

- **[Issue #3301](https://github.com/sipeed/picoclaw/issues/3301) — /clear and session auto-compression broken for routed chats** · 4 comments · Updated 2026-08-18
  Bug on Raspberry Pi with dispatch rules routing chats to non-default agents. `/clear` and session compression fail silently. Points to a gap in multi-agent routing logic.

- **[PR #3314](https://github.com/sipeed/picoclaw/pull/3314) — customAllowPatterns not working** · Updated 2026-08-18
  Users adding commands to the exec allow list are finding them blocked by default deny patterns. Affects agents relying on custom command permissions.

**Underlying needs:** Users want PicoClaw to be accessible to non-terminal users (Web UI), more robust in multi-channel/multi-agent routing, and more transparent in cost/usage logging.

---

## 5. Bugs & Stability

| Severity | Issue/PR | Summary | Fix PR? |
|----------|----------|---------|---------|
| 🔴 High | [#3339](https://github.com/sipeed/picoclaw/issues/3339) | Google Antigravity returns generic 429 despite valid OAuth scopes and successful model discovery | No |
| 🔴 High | [#3301](https://github.com/sipeed/picoclaw/issues/3301) | `/clear` and session auto-compression fail in chats routed via dispatch rules to non-default agents | No |
| 🟡 Medium | [#3328](https://github.com/sipeed/picoclaw/issues/3328) | `webhook_host` / `webhook_port` declared but never read—no warning or error | [#3329](https://github.com/sipeed/picoclaw/pull/3329) (open, stale) |
| 🟡 Medium | [#3314](https://github.com/sipeed/picoclaw/pull/3314) | `customAllowPatterns` overridden by default deny in `guardCommand` | Self-fixing PR open (stale) |
| 🟢 Low | [#3292](https://github.com/sipeed/picoclaw/issues/3292) | High CPU usage when input box is focused in Web chat (Firefox, deepseek-v4-flash) · **Closed** | Closed |

**Notes:** Two high-severity bugs lack open fix PRs. The LINE webhook config silence (#3328) has a candidate fix that has gone stale. The CPU issue (#3292) was closed but no resolution detail was provided in the data.

---

## 6. Feature Requests & Roadmap Signals

| Item | Type | Signal |
|------|------|--------|
| [#806](https://github.com/sipeed/picoclaw/issues/806) — Web UI | Enhancement / Roadmap · High priority | Strongest roadmap signal. 8 👍, author actively refactoring. Likely target for next major release. |
| [#1158](https://github.com/sipeed/picoclaw/pull/1158) — Anthropic native protocol | Feature (now merged) | Fulfills long-standing #269. Reflects demand for broader provider compatibility. |
| [#3317](https://github.com/sipeed/picoclaw/pull/3317) — Prompt cache token logging | Feature (now merged) | Observability improvement for cost-conscious users. |
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) — Long IRC messages | Feature | Niche but important for IRC power users. |

**Prediction:** The Web UI (#806) is the most likely candidate for the next version, given its high priority label, active refactoring, and community interest. Anthropic protocol and cache token logging are already merged and may ship in the next patch release.

---

## 7. User Feedback Summary

- **Accessibility gap:** Non-technical users find the TUI insufficient; a Web UI is the #1 requested improvement (#806, 8 👍).
- **Routing reliability:** Multi-agent dispatch routes break basic session operations (`/clear`, auto-compression) (#3301), causing frustration for users running complex agent setups.
- **Permission confusion:** `customAllowPatterns` doesn't work as documented—users expect allow-listed commands to execute but are blocked (#3314 / #3328 pattern).
- **Cost transparency:** Users want visibility into prompt cache tokens to understand billing, especially with DeepSeek via Cloudflare (#3317).
- **IRC message fragmentation:** Long messages sent over IRC are split and not reassembled, degrading conversation quality (#3287).
- **CPU efficiency:** Web chat input box causes high CPU on Firefox (#3292, closed but unresolved).

Overall sentiment: Users are running PicoClaw in production-like multi-agent, multi-channel configurations and hitting edge-case bugs. The community is engaged but frustrated by silent config failures and routing bugs.

---

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#806](https://github.com/sipeed/picoclaw/issues/806) — Web UI | Open since 2026-02-26 (~5.5 months) | High-priority roadmap item. Active refactoring noted, but no merged PR yet. |
| [#3329](https://github.com/sipeed/picoclaw/pull/3329) — LINE webhook warning | Open since 2026-08-11 (stale) | Fixes a config-silence bug. Has been stale since creation. |
| [#3314](https://github.com/sipeed/picoclaw/pull/3314) — customAllowPatterns fix | Open since 2026-08-03 (stale) | Directly impacts agent permission security. Stale for 16+ days. |
| [#3339](https://github.com/sipeed/picoclaw/issues/3339) — Google Antigravity 429 | Open since 2026-08-17 | No fix PR. High-severity provider bug. |
| [#3301](https://github.com/sipeed/picoclaw/issues/3301) — Dispatch rule /clear bug | Open since 2026-07-29 | No fix PR. Affects multi-agent users. |

**Recommendation:** Maintainers should prioritize closing the two stale PRs (#3314, #3329) and triaging the two high-severity open bugs (#3339, #3301) that currently lack fix attempts.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-19

## 1. Today's Overview

NanoClaw shows **high development velocity** with 41 PRs updated in the last 24 hours (23 still open, 18 merged/closed) and 3 issues touched. The project is in an active refactoring phase, with a major push toward an async, driver-portable central database and a new session-runtime abstraction layer. No new releases were published today, suggesting the team is consolidating infrastructure changes before a version bump.

**Activity assessment:** 🔴 **Very High** — core-team-driven refactor wave dominates the timeline.

---

## 2. Releases

**None.** No new releases were published. The current refactoring wave (async DB, session drivers) is likely preparatory for an upcoming release rather than trailing one.

---

## 3. Project Progress

### Merged / Closed PRs (Today)

- **#2949** [CLOSED] — `feat(skill): /add-litellm` — Adds a minimal model router supporting local servers and optional LiteLLM proxy. **[Link](https://github.com/nanocoai/nanoclaw/pull/2949)**
- **#3077** [CLOSED] — `fix(claude): only abort on a rejected rate_limit_event` — Fixes false-positive quota errors by splitting rate-limit telemetry from actual quota-rejected events. **[Link](https://github.com/nanocoai/nanoclaw/pull/3077)**
- **#3323** [CLOSED] — `refactor(db): make central SQL portable` — First step in DB portability refactor. **[Link](https://github.com/nanocoai/nanoclaw/pull/3323)**
- **#3324** [CLOSED] — `refactor(db): add async central database seam` — Introduces the async DB abstraction layer. **[Link](https://github.com/nanocoai/nanoclaw/pull/3324)**
- **#3330** [CLOSED] — `test(db): run central suites through the driver` — Migrates integration tests to the new `DbDriver` API. **[Link](https://github.com/nanocoai/nanoclaw/pull/3330)**

### Key Open PRs Advancing

- **#3306** — `drivers: a session-runtime driver seam, with Docker as the built-in realization` — A purely additive seam between session semantics and runtime execution; 128 files / 1672 tests green. **[Link](https://github.com/nanocoai/nanoclaw/pull/3306)**
- **#3307** — `host: route session lifecycle through the driver seam` — Stacked on #3306; completes the host-side integration. **[Link](https://github.com/nanocoai/nanoclaw/pull/3307)**
- **#3334** — `[BREAKING] refactor(db): adopt async central database safely` — Marks the full async DB adoption; flagged breaking. **[Link](https://github.com/nanocoai/nanoclaw/pull/3334)**
- **#3332 / #3335 / #3333 / #3337** — Supporting DB refactor PRs (portable SQL, backend composition, async seam, Codex await fixes). **[Links](https://github.com/nanocoai/nanoclaw/pull/3332) [Link](https://github.com/nanocoai/nanoclaw/pull/3335) [Link](https://github.com/nanocoai/nanoclaw/pull/3333) [Link](https://github.com/nanocoai/nanoclaw/pull/3337)**
- **#3343** — `feat(channels): add webex-poll REST polling adapter` — New Cisco Webex channel adapter using REST polling instead of inbound webhooks. **[Link](https://github.com/nanocoai/nanoclaw/pull/3343)**
- **#3322** — `skills: add /add-youdotcom-tool for You.com MCP tools` — Utility skill for You.com MCP integration. **[Link](https://github.com/nanocoai/nanoclaw/pull/3322)**
- **#3341 / #3340 / #3339 / #3342** — Slack provisioning, approval, and credential fixes from the core team. **[Links](https://github.com/nanocoai/nanoclaw/pull/3341) [Link](https://github.com/nanocoai/nanoclaw/pull/3340) [Link](https://github.com/nanocoai/nanoclaw/pull/3339) [Link](https://github.com/nanocoai/nanoclaw/pull/3342)**

---

## 4. Community Hot Topics

| # | Type | Title | Activity |
|---|------|-------|----------|
| #3338 | Issue | Codex WebSocket idle retry hidden until 10-min turn timeout | 2 comments |
| #2868 | Issue (closed) | `/update-skills` silent no-op for already-installed channels | 1 comment |
| #3194 | Issue (closed) | `/update-nanoclaw` stamps success without recoverable cutover | 0 comments |

**Analysis:**

- **Issue #3338** — **[Open](https://github.com/nanocoai/nanoclaw/issues/3338)**: The longest-running open issue today. Users report that a simple Telegram request can stall for 10 minutes when the Codex WebSocket idles, because `codex app-server` does not surface the CLI's internal 5-minute retry failure to NanoClaw. This reflects a genuine UX pain point around **silence during WebSocket stalls** — users lose trust when a bot appears unresponsive without feedback. The need is for **observable retry/timeout signals** across all channel adapters, not just Codex.

- **Issues #2868 & #3194** — Both closed today, indicating the team is actively addressing **update reliability**. The underlying theme: NanoClaw's self-update and skill-refresh workflows have fragile cutover semantics that can silently fail or claim success without a clean rollback path. This is a stability concern that affects power users running long-lived instances.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|----------|------|-------------|------------|
| 🔴 High | [#3338](https://github.com/nanocoai/nanoclaw/issues/3338) | Codex WebSocket idle retry hidden; 10-min silent stall | Open — no fix PR yet |
| 🟡 Medium | [#3077](https://github.com/nanocoai/nanoclaw/pull/3077) | False-positive `rate_limit_event` → quota abort | ✅ Merged |
| 🟡 Medium | [#2868](https://github.com/nanocoai/nanoclaw/issues/2868) | `/update-skills` silent no-op for installed channels | ✅ Closed |
| 🟡 Medium | [#3194](https://github.com/nanocoai/nanoclaw/issues/3194) | `/update-nanoclaw` success stamp before validation | ✅ Closed |
| 🟠 Low | [#3339](https://github.com/nanocoai/nanoclaw/pull/3339) | Stored sign-in treated as verified when probe is unreachable | In PR (closed-fail approach) |

**Notable:** The Codex WebSocket issue (#3338) remains the top unresolved bug. It affects end-user experience directly (silent stalls) and has no fix PR in progress yet.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Details |
|--------|--------|---------|
| **Async portable database** | #3334, #3332, #3333, #3335, #3337 | Major architectural shift from synchronous `better-sqlite3` to an async, driver-portable central DB. Suggests future support for remote/managed backends. |
| **Session-runtime driver abstraction** | #3306, #3307, #3308 | Docker was the only runtime; new `SessionDriver` seam opens the door to alternative runtimes (podman, native processes, cloud executors). |
| **New channel adapters** | #3343 (Webex), #3322 (You.com MCP) | Expanding integration surface beyond Slack/Discord/Telegram. Webex targets enterprise users who cannot expose inbound webhooks. |
| **LiteLLM router skill** | #2949 | Added as a utility skill — local-first model routing without requiring a managed proxy. |
| **Slack provisioning hardening** | #3341, #3340, #3342 | Multiple fixes around Slack credential pairing, approval instance tracking, and owner-absent invite handling. Signals ongoing investment in Slack enterprise reliability. |

**Prediction for next release:** The async DB refactor (#3334) is flagged **BREAKING** and will likely ship as a major version change. If merged, expect a **v5.x** release. In the interim, expect feature PRs like Webex and You.com to land in a maintenance release.

---

## 7. User Feedback Summary

| Theme | Source | Sentiment |
|-------|--------|-----------|
| **Silent stalls on WebSocket idle** | #3338 | 😤 Frustrated — a simple Telegram request stuck for 10 min with no feedback |
| **Update commands lying about success** | #2868, #3194 | 😤 Dissatisfied — `/update-skills` and `/update-nanoclaw` both had reliability bugs that were silent or premature |
| **Desire for enterprise channel support** | #3343 | 👍 Positive — Webex polling adapter fills a real gap for orgs that block inbound webhooks |
| **Local-first model routing** | #2949, #3322 | 👍 Positive — LiteLLM router and You.com MCP tools show demand for flexible, self-hosted AI backends |
| **Slack setup complexity** | #3341, #3340, #3339 | 😐 Mixed — multiple small fixes suggest the Slack onboarding experience has pain points around credential pairing and approval flows |

---

## 8. Backlog Watch

| Item | Age | Priority | Risk |
|------|-----|----------|------|
| [#3338](https://github.com/nanocoai/nanoclaw/issues/3338) — Codex WebSocket idle retry hidden | **1 day open**, but unaddressed by a PR | 🔴 High — direct UX impact, affects all Codex-using users | Needs a fix PR; no assignee visible |
| [#3025](https://github.com/nanocoai/nanoclaw/pull/3025) — Agent SDK 32000 output-token cap | **38 days open** | 🟡 Medium — limits model output length; likely a common pain point | Stale; author `javexed` is active elsewhere but this PR has no recent movement |

**Recommendation:** Issue #3338 should be triaged promptly — it represents the gap between the Codex CLI's built-in 5-minute retry and NanoClaw's 10-minute turn timeout, a synchronization blind spot. The token-cap PR (#3025) has been open since mid-July with no maintainer response; consider a ping or a more targeted reproduction if the cap is a blocker for power users.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-19

## 1. Today's Overview

IronClaw is in active pre-v1.3 development with high daily throughput: 21 issues and 40 PRs updated in the past 24 hours, 1 new RC release, and 6 issues closed. The project is in a stabilization phase — RC.2 addresses a startup regression from 1.2 upgrades, and today's closed items are quality-of-life UX fixes (toasts, shared notice component). The open-issue stack is dominated by v1.3/v1.4 epic work and a few lingering reliability bugs (context recall, automation consistency, libSQL journal stalling). The overall health signal is **active and shipping**, though several open bugs suggest the automation pipeline still needs hardening before RC → GA.

## 2. Releases

**ironclaw-v1.3.0-rc.2** (2026-08-18)
- **Fix:** Upgrades from 1.2 now accept and preserve the released extension `activation_state` field instead of crash-looping at startup.
- **Fix:** Reborn runtime image restores opt-in, public-key-only worker SSH on port 2222.
- No breaking changes noted. No migration steps required beyond standard upgrade path.
- 🔗 [Release](https://github.com/nearai/ironclaw/releases) | [Issue #7185 context](https://github.com/nearai/ironclaw/issues/7185)

## 3. Project Progress

**Merged / Closed today:**
| Item | Type | Summary |
|---|---|---|
| [#7734](https://github.com/nearai/ironclaw/pull/7734) | refactor (closed) | Extracted 317 tests from two stalled test-module extractions (`executor/tests.rs` 12.8k lines, `capability_port.rs` 11.3k lines) — zero production lines changed |
| [#7638](https://github.com/nearai/ironclaw/pull/7638) | fix (closed) | Replaced blocking `window.alert()` thread-deletion errors with global toast feedback in WebUI |
| [#7639](https://github.com/nearai/ironclaw/pull/7639) | fix (closed) | Introduced shared `InlineNotice` component for Jobs/Projects/Workspace/Extensions feedback banners, unifying tone and dismissal semantics |

**PRs advancing features (open):**
- [#7735](https://github.com/nearai/ironclaw/pull/7735) — Downloadable conversation artifacts now include per-iteration inference/tool timing data (durable floor for bug reports)
- [#7697](https://github.com/nearai/ironclaw/pull/7697) — Durable user inbox with pagination, unread counts, and read/archive lifecycle APIs; inbox ownership moved to dedicated `ironclaw_notifications` domain
- [#7650](https://github.com/nearai/ironclaw/pull/7650) — Automated run outcomes derived from runtime evidence instead of answer-only semantic judging
- [#7491](https://github.com/nearai/ironclaw/pull/7491) — OMP core-tool contract for coding (replaces first-party tools with `read`/`write`/`edit`/`glob`/`grep`/`bash`)
- [#7724](https://github.com/nearai/ironclaw/pull/7724) — Voice-to-text composer via NEAR AI Whisper (host-side transcription, never auto-sent)
- [#7728](https://github.com/nearai/ironclaw/pull/7728) — Four semantic Google Docs editing capabilities appended to legacy tool set
- [#7682](https://github.com/nearai/ironclaw/pull/7682) — Slack unlinked-user connect nudge now delivered privately with one-click link (#7681)
- [#6994](https://github.com/nearai/ironclaw/pull/6994) — OOBE automation-tasks prototype (carousel, inline cards, agent-mode pill); gated behind `oobe_suggestions` flag

## 4. Community Hot Topics

| Issue | Type | Activity | Core Need |
|---|---|---|---|
| [#7185](https://github.com/nearai/ironclaw/issues/7185) — Memory not reliably recalled across conversations | Bug | 2 comments, reported 2026-08-04 | Context persistence between sessions is a top user-reported reliability gap |
| [#6879](https://github.com/nearai/ironclaw/issues/6879) — Automation runs hit-or-miss | Epic / Bug | 1 comment, reported 2026-07-29 | Structural pipeline issue: trigger fires are executed as plain interactive chat turns, especially on small models |
| [#7673](https://github.com/nearai/ironclaw/issues/7673) — BudgetLedger double-charge gap | Bug | 1 comment, reported 2026-08-15 | Truncated launch windows cause over-counting; errs conservative but blocks legitimate runs |
| [#7736](https://github.com/nearai/ironclaw/issues/7736) — Daily failure taxonomy 2026-08-19 | Meta | New today | Weak model (Qwen3.8-27B) failing multi-step tasks dominates enterprise suite non-passes |
| [#7714](https://github.com/nearai/ironclaw/issues/7714) — libSQL single write connection starvation | Bug (closed) | Reported 2026-08-17, closed 2026-08-18 | Cascading authority invalidation and reservation leaks under bench load; fix likely merged today |
| [#7038](https://github.com/nearai/ironclaw/issues/7038) — Storybook + AI-first Design System | Epic | Open since 2026-08-03 | Full design-system proposal package (PR #7257) and governance phase 2 (PR #7043) in progress |

**Underlying theme:** The community is pressing on two axes — **reliability of the agent loop** (context recall, automation consistency, tool-call budget exhaustion in #7447) and **operator experience** (Slack privacy, WebUI onboarding, shared component consistency).

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix Status |
|---|---|---|---|
| 🔴 High | [#7185](https://github.com/nearai/ironclaw/issues/7185) | Context/information not reliably recalled across conversations | Open |
| 🔴 High | [#6879](https://github.com/nearai/ironclaw/issues/6879) | Automation trigger→run pipeline executes as interactive chat, not unattended | Open |
| 🟡 Medium | [#7447](https://github.com/nearai/ironclaw/issues/7447) | Agent burns through tool-call budget in redundant fetch-retry loops instead of paginating | Open |
| 🟡 Medium | [#7673](https://github.com/nearai/ironclaw/issues/7673) | BudgetLedger truncated-launch double-charge | Open |
| 🟡 Medium | [#7727](https://github.com/nearai/ironclaw/issues/7727) | Catalog `capabilities` artifact mandatory but never read (incl. manifest v3) | Open |
| 🟡 Medium | [#7726](https://github.com/nearai/ironclaw/issues/7726) | `IRONHUB_MANIFEST_URL` hardcoded behind compile-time allowlist | Open |
| 🟢 Low (fixed) | [#7714](https://github.com/nearai/ironclaw/issues/7714) | libSQL write-connection starvation under bench load | Closed |
| 🟢 Low (fixed) | v1.3.0-rc.2 | Crash-loop on upgrade from 1.2 (extension `activation_state`) | Fixed in RC |

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Requested Feature | Likelihood for Next Release |
|---|---|---|
| [#7731](https://github.com/nearai/ironclaw/issues/7731) | Integrate Mnesis as a memory provider (addresses #7185 context recall) | v1.4.0 spike |
| [#7354](https://github.com/nearai/ironclaw/issues/7354) | Extensions vNext: unified channels, Signal channel, rich messaging | v1.3.0 (partial; Web push & Telegram deferred) |
| [#7392](https://github.com/nearai/ironclaw/issues/7392) / [#7491](https://github.com/nearai/ironclaw/pull/7491) | Replace first-party coding tools with pinned OMP surface | v1.3.0 (PR in progress) |
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | Sandboxing solution with CLIs | v1.4.0 epic |
| [#7467](https://github.com/nearai/ironclaw/issues/7467) | Make Reborn durable state profile-agnostic; migrate legacy profile roots | v1.4.0 epic |
| [#6837](https://github.com/nearai/ironclaw/issues/6837) | Minimal info-level logging for growth/usage stats (52 `info!` calls currently all plumbing) | Low priority, no timeline |
| [#7724](https://github.com/nearai/ironclaw/pull/7724) | Voice-to-text composer via NEAR AI Whisper | Likely v1.3.0 (PR merged-ready) |
| [#7697](https://github.com/nearai/ironclaw/pull/7697) | Durable user inbox + notification product APIs | Likely v1.3.0 (PR open, core contributor) |

## 7. User Feedback Summary

**Pain points reported:**
- **"The agent doesn't remember what we discussed earlier"** — multiple testers independently confirmed context loss between conversations (#7185). This is the highest-frequency complaint.
- **Automation is unreliable** — same stored prompt produces inconsistent results; the pipeline runs triggers as interactive chat turns rather than unattended jobs (#6879).
- **Slack unlinked-user messages are public** — connect notices are broadcast to the whole channel and require a manual multi-step process with no context carry-over (#7681); a fix PR (#7682) is open.
- **Tool-call budget exhaustion** — agent gets stuck in redundant fetch-retry loops instead of using pagination, burning through its turn budget (#7447).
- **WebUI alerts are jarring** — thread deletion used blocking `window.alert()`; now replaced with toasts (#7638).

**Positive signals:**
- Shared `InlineNotice` component unifies feedback banners across Jobs/Projects/Workspace/Extensions (#7639).
- Voice input in the composer is a new delight feature (#7724).
- Downloadable artifacts now carry timing evidence, making bug reports more actionable (#7735).

## 8. Backlog Watch

| Issue | Open Since | Days Open | Why It Needs Attention |
|---|---|---|---|
| [#6837](https://github.com/nearai/ironclaw/issues/6837) — Growth/usage stats logging | 2026-07-29 | 21 | Zero `info!` calls in workspace crates; operators have no observability into growth metrics |
| [#7467](https://github.com/nearai/ironclaw/issues/7467) — Reborn durable state profile-agnostic | 2026-08-10 | 9 | Profile switches strand conversations, secrets, extensions, and workspaces in the wrong directory |
| [#7185](https://github.com/nearai/ironclaw/issues/7185) — Memory not reliably recalled | 2026-08-04 | 15 | Top user-reported reliability bug; Mnesis spike (#7731) may address but is still an experiment |
| [#6879](https://github.com/nearai/ironclaw/issues/6879) — Automation hit-or-miss | 2026-07-29 | 21 | Structural pipeline issue; no fix PR yet despite being identified as non-model noise |
| [#7733](https://github.com/nearai/ironclaw/issues/7733) — DESIGN.md governance phases 2–3 | 2026-08-18 | 1 | New epic; design system governance is a prerequisite for consistent WebUI development |
| [#7447](https://github.com/nearai/ironclaw/issues/7447) — Agent tool-call budget exhaustion | 2026-08-10 | 9 | Directly impacts task completion rate; no fix PR visible |

**Overall project health:** 🟢 **Active with minor concerns.** The team is shipping PRs at a high rate (40 updates/24h) and closing bugs quickly (#7714 closed within 1 day). The two risks are **context recall** (#7185) and **automation reliability** (#6879), both open for 2+ weeks with no merged fix yet — these should be prioritized before the v1.3.0 GA cut.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-19

---

## 1. Today's Overview

LobsterAI reported a notably active 24-hour window with **9 open issues** and **19 pull requests** updated, of which **16 were merged or closed**. A new release, **2026.8.18**, shipped yesterday, led primarily by contributor `@fisherdaddy` with the DSH engine integration. The project shows healthy merge velocity, with recent PRs spanning engine integration, UX polish, and critical stability fixes. Maintainer attention appears concentrated on the OpenClaw gateway compatibility issues and core engine evolution.

---

## 2. Releases

### LobsterAI 2026.8.18 (2026-08-18)

Key changes in this release:

- **DSH Engine Integration** (#2502, #2509, #2508) — DeepSeek Harness engine integrated as an optional AI backend, updated to rc.7, with a new process launcher and retry logic for transient model-load failures.
- **Release branch merge** (#2510) — Final `release/2026.8.17` changes merged into `main` (23 commits, +7,004/-39 lines), including experimental DSH support and scheduled-task history improvements.

**Breaking changes / Migration notes:**
- The `skipMissedJobs` cron configuration field was removed in newer OpenClaw versions; users upgrading must ensure their `openclawConfig` no longer contains this field, or the gateway will fail to start (see Bug #1626 fix).

> Links: [#2502](https://github.com/netease-youdao/LobsterAI/pull/2502) · [#2509](https://github.com/netease-youdao/LobsterAI/pull/2509) · [#2510](https://github.com/netease-youdao/LobsterAI/pull/2510)

---

## 3. Project Progress

### Merged / Closed PRs Today (16 items)

| PR | Area | Summary |
|----|------|---------|
| [#2510](https://github.com/netease-youdao/LobsterAI/pull/2510) | Release | Merge of 2026.8.17 release into `main` |
| [#2509](https://github.com/netease-youdao/LobsterAI/pull/2509) | Engine | Update DSH to rc.7 |
| [#2508](https://github.com/netease-youdao/LobsterAI/pull/2508) | Engine | Retry server model load after transient failures (backoff retries) |
| [#2507](https://github.com/netease-youdao/LobsterAI/pull/2507) | Scheduled Tasks | Cap cron run history page size to respect OpenClaw gateway limits |
| [#2481](https://github.com/netease-youdao/LobsterAI/pull/2481) | Sidebar | Move task search to header actions; icon-only, cross-platform alignment |
| [#2425](https://github.com/netease-youdao/LobsterAI/pull/2425) | Settings | Add artifact auto-preview toggle (opt-out of automatic file preview) |
| [#2418](https://github.com/netease-youdao/LobsterAI/pull/2418) | Sidebar | Multi-agent task activity filter (Codex-inspired) |
| [#2410](https://github.com/netease-youdao/LobsterAI/pull/2410) | UI | Align Sites page layout with Skills/MCP management views |
| [#2417](https://github.com/netease-youdao/LobsterAI/pull/2417) | UI | Copy success feedback for site URLs and share codes |
| [#1583](https://github.com/netease-youdao/LobsterAI/pull/1583) | Skills | "Recently Used" tab with usage-count tracking for skills |
| [#1597](https://github.com/netease-youdao/LobsterAI/pull/1597) | Data | Enable SQLite foreign-key constraints; fix cascading-delete failures |
| [#1615](https://github.com/netease-youdao/LobsterAI/pull/1615) | Export | Improve session export quality (timestamps, metadata, copy-to-clipboard) |
| [#1621](https://github.com/netease-youdao/LobsterAI/pull/1621) | Notifications | OS native notifications on scheduled-task completion (closes #1620) |
| [#1626](https://github.com/netease-youdao/LobsterAI/pull/1626) | OpenClaw | **P0 Fix**: Remove invalid `skipMissedJobs` config field causing gateway crash on startup |
| [#1629](https://github.com/netease-youdao/LobsterAI/pull/1629) | UI | User avatar settings feature (6 preset avatars + image upload) |
| [#1631](https://github.com/netease-youdao/LobsterAI/pull/1631) | MCP | Quick-add templates for common MCP services (File System, SQLite, Brave Search) |

### Still Open PRs
- [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Dependabot Electron bump (40.2.1 → 43.4.0)
- [#1628](https://github.com/netease-youdao/LobsterAI/pull/1628) — Model selector UI refactor + toolbar style unification
- [#1634](https://github.com/netease-youdao/LobsterAI/pull/1634) — Global search fix and UX upgrade

---

## 4. Community Hot Topics

### Most Discussed Issues

1. **[#1627](https://github.com/netease-youdao/LobsterAI/issues/1627)** — *Client crashes on moderately complex tasks* (2 comments, stale)
   > Users report the app crashing when handling non-trivial multi-step tasks. WebSocket tick events are logged before the crash, suggesting memory or message-handling overflow. **High community relevance** — any stability concern around complex workflows draws attention.

2. **[#1614](https://github.com/netease-youdao/LobsterAI/issues/1614)** — *Add hermes-agent as optional AI engine* (2 comments, stale)
   > Feature request to extend engine support beyond OpenClaw. Signals demand for **engine diversity** and competition among backends.

3. **[#1632](https://github.com/netease-youdao/LobsterAI/issues/1632)** — *Custom model addition fails after switching to local model* (2 comments, stale)
   > Skill compatibility breaks when switching engines. Highlights a **configuration persistence gap** — skills registered under one model/agent don't carry over cleanly.

4. **[#1620](https://github.com/netease-youdao/LobsterAI/issues/1620) → [#1621](https://github.com/netease-youdao/LobsterAI/pull/1621)** — *System notifications on scheduled task completion* (1 comment, **now closed via PR**)
   > Well-scoped feature request that was quickly implemented. Shows responsive community-to-merge pipeline.

5. **[#1617](https://github.com/netease-youdao/LobsterAI/issues/1617)** — *Deleted skill list not refreshing (persists after restart)* (1 comment, stale)
   > Frontend state desync with backend deletion. A classic stale-state bug with direct UX impact.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix Status |
|----------|-------|---------|------------|
| 🔴 **P0 / Blocker** | [#1626](https://github.com/netease-youdao/LobsterAI/issues/1626) / [PR #1626](https://github.com/netease-youdao/LobsterAI/pull/1626) | OpenClaw gateway fails to start after upgrade due to deprecated `skipMissedJobs` config field; dialog flashes repeatedly | ✅ **Merged** |
| 🔴 **High** | [#1587](https://github.com/netease-youdao/LobsterAI/issues/1587) | App crashes on first launch after update (macOS) | ⚠️ Open — no fix PR yet |
| 🔴 **High** | [#1589](https://github.com/netease-youdao/LobsterAI/issues/1589) | Sessions and scheduled tasks both fail to execute on macOS | ⚠️ Open — no fix PR yet |
| 🟡 **Medium** | [#1627](https://github.com/netease-youdao/LobsterAI/issues/1627) | Client crash on complex tasks (WebSocket-related) | ⚠️ Open — no fix PR yet |
| 🟡 **Medium** | [#1617](https://github.com/netease-youdao/LobsterAI/issues/1617) | Skill deletion not reflected in UI; persists across restarts | ⚠️ Open — no fix PR yet |
| 🟡 **Medium** | [#1622](https://github.com/netease-youdao/LobsterAI/issues/1622) | Custom model test fails after configuration | ⚠️ Open — no fix PR yet |
| 🟢 **Low** | [#1586](https://github.com/netease-youdao/LobsterAI/issues/1586) | Incomplete i18n: some UI elements remain in Chinese after switching to English | ⚠️ Open — no fix PR yet |
| 🟢 **Low** | [#1634](https://github.com/netease-youdao/LobsterAI/issues/1634) | Search incorrectly scoped to current agent instead of global | 🟢 In progress — [PR #1634](https://github.com/netease-youdao/LobsterAI/pull/1634) open |

**Notable regression:** The P0 gateway-crash bug (#1626) affected **all users** upgrading to the newer OpenClaw version and was resolved within the same release cycle. The fix removes the invalid config field and suppresses the dialog flicker during gateway restart.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue → PR | Signal Strength |
|---------|-----------|-----------------|
| OS native notifications for scheduled tasks | [#1620](https://github.com/netease-youdao/LobsterAI/issues/1620) → [#1621](https://github.com/netease-youdao/LobsterAI/pull/1621) | ✅ **Shipped** in 2026.8.18 |
| Recently used skills tab with usage stats | [#1583](https://github.com/netease-youdao/LobsterAI/pull/1583) | ✅ **Shipped** |
| Session export improvements (timestamps, metadata, clipboard) | [#1615](https://github.com/netease-youdao/LobsterAI/pull/1615) | ✅ **Shipped** |
| User avatar settings (presets + upload) | [#1629](https://github.com/netease-youdao/LobsterAI/pull/1629) | ✅ **Shipped** |
| MCP quick-add templates | [#1631](https://github.com/netease-youdao/LobsterAI/pull/1631) | ✅ **Shipped** |
| Multi-agent task activity filter (sidebar) | [#2418](https://github.com/netease-youdao/LobsterAI/pull/2418) | ✅ **Shipped** |
| Hermes-agent engine support | [#1614](https://github.com/netease-youdao/LobsterAI/issues/1614) | 🟡 **Deferred** — feature request open |
| Artifact auto-preview toggle | [#2425](https://github.com/netease-youdao/LobsterAI/pull/2425) | ✅ **Shipped** |
| Model selector UI refactor with vendor icons | [#1628](https://github.com/netease-youdao/LobsterAI/pull/1628) | 🟢 **In review** — open PR |
| Global search fix and UX upgrade | [#1634](https://github.com/netease-youdao/LobsterAI/pull/1634) | 🟢 **In review** — open PR |
| Electron 43 upgrade | [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | 🟡 **Deferred** — Dependabot PR open since April |

**Roadmap prediction:** The next release will likely include the model selector UI refactor (#1628), global search upgrade (#1634), and potentially Hermes-agent engine support (#1614) if the integration scope is manageable. The Electron 43 upgrade (#1277) remains a low-priority maintenance task.

---

## 7. User Feedback Summary

**Pain points expressed:**
- **Engine switching breaks skills** (#1632): Users lose access to previously installed skills after switching from cloud to local models, with no clear path to reinstall.
- **Client instability on complex workloads** (#1627): Multi-step agent tasks cause crashes, undermining trust in the platform for production use.
- **Startup crashes after updates** (#1587, #1589): First-launch regressions on macOS are disrupting user onboarding and updates.
- **Incomplete internationalization** (#1586): Switching to English leaves portions of the UI in Chinese, suggesting i18n coverage is still partial.
- **Deleted items persist in UI** (#1617): State synchronization between backend deletion and frontend listing is unreliable.

**Positive signals:**
- Users actively request **engine diversity** (Hermes-agent, #1614), indicating engagement with the multi-agent architecture.
- Notification and export feature requests (#1620, #1615) were **quickly fulfilled**, reflecting well on the maintainer responsiveness.
- The DSH engine integration (#2502, #2509) shows the project is actively expanding its backend ecosystem.

---

## 8. Backlog Watch

| Item | Age | Priority | Concern |
|------|-----|----------|---------|
| [#1614](https://github.com/netease-youdao/LobsterAI/issues/1614) — Hermes-agent engine | ~4 months | Medium | Community interest in engine diversity; unaddressed |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Electron 40→43 bump | ~4 months | Low-Medium | Dependency security/update debt; stale Dependabot PR |
| [#1587](https://github.com/netease-youdao/LobsterAI/issues/1587) — Launch crash on update | ~4 months | 🔴 High | Blocker for clean upgrades; no fix PR |
| [#1589](https://github.com/netease-youdao/LobsterAI/issues/1589) — Session & scheduled-task failure | ~4 months | 🔴 High | Core functionality broken for affected users |
| [#1627](https://github.com/netease-youdao/LobsterAI/issues/1627) — Crash on complex tasks | ~4 months | 🔴 High | Stability risk for power users; no fix PR |
| [#1617](https://github.com/netease-youdao/LobsterAI/issues/1617) — Skill deletion UI desync | ~4 months | 🟡 Medium | Data integrity UX bug; no fix PR |
| [#1622](https://github.com/netease-youdao/LobsterAI/issues/1622) — Custom model test failure | ~4 months | 🟡 Medium | Onboarding blocker for local-model users |
| [#1586](https://github.com/netease-youdao/LobsterAI/issues/1586) — Incomplete i18n | ~4 months | 🟢 Low | Polish issue; no fix PR |

**Summary:** The backlog contains several long-standing issues (all marked `[stale]`) spanning 4+ months without maintainer response. The most critical are the **launch crash (#1587)** and **core functionality failures (#1589, #1627)**, which directly impact user retention. The project's recent merge velocity is encouraging, but clearing the stale high-severity backlog should be a priority for the next maintenance cycle.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-19

---

## 1. Today's Overview

Moltis showed strong release-cycle momentum on 2026-08-18/19, with **2 new releases** shipped and **6 PRs merged** in a single day. Two bugs were closed, both via targeted fix PRs, suggesting an active triage-and-release rhythm. One open PR (Tesla Fleet API connector) signals ongoing expansion of the connector ecosystem. Overall, project health is **positive** — high merge velocity, rapid bug closure, and consistent feature additions.

---

## 2. Releases

### `20260818.08` & `20260818.06`
Two builds were published on 2026-08-18. Based on the PRs merged into this cycle, these releases likely include:

- **OpenAI reasoning tool calls routed through Responses API** (PR [#1198](https://github.com/moltis-org/moltis/pull/1198))
- **Podman sandbox escape-hatch support** (PR [#1106](https://github.com/moltis-org/moltis/pull/1106))
- **Files library & Settings browser** (PR [#1206](https://github.com/moltis-org/moltis/pull/1206))
- **Heartbeat config patch fix** (PR [#1209](https://github.com/moltis-org/moltis/pull/1209))
- **README star history chart repair** (PR [#1211](https://github.com/moltis-org/moltis/pull/1211))

**Breaking changes:** None explicitly called out. The heartbeat fix (PR #1209) changes the semantics of `heartbeat.update` from a full config overwrite to a patch — existing automation that relied on full-overwrite behavior may need adjustment.

**Migration notes:** If you use `heartbeat.update` via the gateway, ensure you're sending only the fields you intend to change; omitted fields will now retain their prior values rather than resetting to defaults.

---

## 3. Project Progress

**Merged / Closed PRs this cycle (6):**

| PR | Title | Author |
|---|---|---|
| [#1198](https://github.com/moltis-org/moltis/pull/1198) | Route OpenAI reasoning tool calls through Responses | penso |
| [#1209](https://github.com/moltis-org/moltis/pull/1209) | fix(gateway): heartbeat.update as patch | Lstarsky0 |
| [#1211](https://github.com/moltis-org/moltis/pull/1211) | fix(readme): restore star history chart | CrustyMozarella |
| [#1106](https://github.com/moltis-org/moltis/pull/1106) | fix(sandbox): Podman escape hatches | penso |
| [#1206](https://github.com/moltis-org/moltis/pull/1206) | Add managed Files library & Settings browser | penso |
| [#1210](https://github.com/moltis-org/moltis/pull/1210) | Add Tesla Fleet API connector *(open)* | penso |

**Key advances:**
- **AI integration:** OpenAI reasoning tools are now routed through the Responses API, preserving Chat Completions fallback behavior for non-Reasoning or OpenAI-compatible providers (PR #1198).
- **Sandboxing:** Podman users gain validated host-socket passthrough and privileged nested Podman escape hatches, with sandbox recreation on mode/socket changes (PR #1106).
- **Data layer:** A new persistent Files library with full CRUD over streamed APIs, plus a Finder-style Settings browser and multi-container runtime mount support (PR #1206).
- **Reliability:** Heartbeat config patching corrected; README metrics restored (PRs #1209, #1211).

---

## 4. Community Hot Topics

### Most-discussed Issues

- **[#1095](https://github.com/moltis-org/moltis/issues/1095)** — *Podman not working via Moltis* (2 comments, opened 2026-06-03)
  - A long-standing compatibility gap that was finally resolved by PR #1106. The 2-month open period before merge signals that Podman sandboxing was a high-priority community need.

- **[#1187](https://github.com/moltis-org/moltis/issues/1187)** — *Heartbeat settings UI silently resets fields* (0 comments, opened 2026-08-09)
  - Rapidly caught and fixed (PR #1209 merged within 9 days). Low comment count suggests the issue was clearly reproducible and unambiguous.

**Underlying need:** Users are actively pushing Moltis toward **broader runtime support** (Podman parity with Docker) and **more reliable configuration management** (heartbeat patching). Both reflect a user base running Moltis in diverse container and automation environments.

---

## 5. Bugs & Stability

| Severity | Issue | PR Fix | Status |
|---|---|---|---|
| **High** | [#1095](https://github.com/moltis-org/moltis/issues/1095) — Podman sandbox non-functional | [#1106](https://github.com/moltis-org/moltis/pull/1106) | ✅ Closed |
| **Medium** | [#1187](https://github.com/moltis-org/moltis/issues/1187) — Heartbeat UI silently resets config fields | [#1209](https://github.com/moltis-org/moltis/pull/1209) | ✅ Closed |

No new open bugs reported. Both closed bugs had direct fix PRs in the same cycle — a healthy signal for project responsiveness. No regressions observed.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Assessment |
|---|---|---|
| **Tesla vehicle data sync** | PR [#1210](https://github.com/moltis-org/moltis/pull/1210) *(open)* | Read-only connector for local vehicle state. Suggests roadmap interest in **IoT/vehicle integration** as a first-party connector class. |
| **Files library & Settings browser** | PR [#1206](https://github.com/moltis-org/moltis/pull/1206) *(merged)* | Now shipped. Persistent data directory with authenticated CRUD APIs. Expect related features (file search, symlink mounts) in upcoming releases. |
| **OpenAI Responses API routing** | PR [#1198](https://github.com/moltis-org/moltis/pull/1198) *(merged)* | Deepening AI provider integration. Likely precursor to more structured reasoning-mode tool calling. |
| **Podman first-class support** | PR [#1106](https://github.com/moltis-org/moltis/pull/1106) *(merged)* | Container runtime parity is now achieved; future work may focus on other runtimes (e.g., rootless modes, WSL2). |

**Likely next release features:** Tesla connector (if PR #1210 merges), further Responses API enhancements, and Files library expansion (e.g., watch/notify, glob-based sync).

---

## 7. User Feedback Summary

- **Podman users** experienced a significant blocker (2 months open) that is now resolved — high satisfaction gain expected.
- **Heartbeat config users** reported a silent data-loss bug (fields resetting to defaults); the fix restores confidence in configuration persistence.
- **Star history chart** was broken in README due to GitHub API token requirements — the community-contributed fix (PR #1211) restores visibility into project growth.
- Overall sentiment appears **positive**: bugs are being closed rapidly, new features are shipping, and community contributors (Lstarsky0, CrustyMozarella) are actively participating alongside core maintainers.

---

## 8. Backlog Watch

| Item | Age | Priority | Note |
|---|---|---|---|
| PR [#1210](https://github.com/moltis-org/moltis/pull/1210) — Tesla Fleet API connector | Created 2026-08-18 *(1 day open)* | Medium | Still open; no maintainer review comments yet. Low-risk read-only connector — likely to merge soon. |
| No long-open critical issues remain | — | — | Both recently closed issues had fix PRs within the same cycle. |

**Maintainer attention needed:** None critically overdue. The pipeline is moving efficiently with no stale high-priority items.

---

*Generated from GitHub data on 2026-08-19. Source: [moltis-org/moltis](https://github.com/moltis-org/moltis)*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026‑08‑19

## 1. Today’s Overview
CoPaw (agentscope‑ai/CoPaw) shows **high activity** with 45 issues and 50 pull requests updated in the last 24 hours. The project is in a **bug‑fix and stability‑improvement phase**: several critical issues around session freezes, model‑execution errors, and environment‑variable loss were reported today, while multiple security and reliability patches are already in review. No new release was published, indicating the team is focusing on merging existing fixes before a version bump. Community engagement is strong, with open issues drawing 5‑10 comments each and several first‑time contributors submitting PRs.

## 2. Releases
*No new releases in the last 24 hours.*

## 3. Project Progress
**Merged/Closed today:**
- **#7122** – `[first‑time‑contributor] Feature/biz kb` – closed. The description is sparse, but the PR likely added a business‑knowledge base feature or related tests.

**PRs advanced today (open):**
- **#7120** – Security: enables all shell‑evasion checks by default and adds a regression test.
- **#7119** – Security: fixes the master‑key file creation to enforce `0o600` permissions.
- **#7066** – Fixes OAuth2 refresh‑token rotation for remote MCP servers (closes #7053).
- **#7087** – Localizes remote media URLs client‑side before model requests, avoiding hotlink‑protected 403 errors.
- **#7057** – Adds user‑local bin directories to subprocess `PATH`, improving tool discovery in container/service environments.
- **#7112** – Draft PR introducing an opt‑in local QwenPaw Pro control plane (`qwenpaw app --pro`) with multi‑user account management and tenant‑scoped isolation.

## 4. Community Hot Topics
| Issue | Status | Comments | Summary |
|-------|--------|----------|---------|
| [#6684](https://github.com/agentscope‑ai/CoPaw/issues/6684) | OPEN | 10 | **Channel retry feature** –自建Matrix频道连接不稳定，QwenPaw 无自动重试或健康检测，每次启动需手动重连。 |
| [#6921](https://github.com/agentscope‑ai/CoPaw/issues/6921) | OPEN | 8 | **Task halts after planning** – Agent 规划完下一步后无提示停止，需用户输入“继续”才能恢复。 |
| [#7102](https://github.com/agentscope‑ai/CoPaw/issues/7102) | OPEN | 7 | **Freeze >10 min** – 使用 GLM 5.3 时长时间无 token 输出，thinking 也冻结。 |
| [#7011](https://github.com/agentscope‑ai/CoPaw/issues/7011) | OPEN | 7 | **Console stop cancels active Feishu session** – 多 UI 会话间 session identity 交叉导致飞书会话被误终止。 |
| [#6470](https://github.com/agentscope‑ai/CoPaw/issues/6470) | OPEN | 5 | **MCP driver ignores `streamable_http` transport** – 硬编码 `sse_client` 导致 Streamable HTTP MCP 服务器连接失败。 |

**Underlying needs:**  
- **Reliability of external channels** (Matrix, Feishu) – users demand automatic retry and health monitoring.  
- **Smooth multi‑step task execution** – the current stop‑and‑wait behavior breaks workflow continuity.  
- **Session isolation** – concurrent UI sessions must not interfere with each other’s channel connections.  
- **Protocol compliance** – MCP transport configuration should be respected, not bypassed.

## 5. Bugs & Stability
**High severity (reported today):**
- **#7102** – Freeze >10 min during model execution (GLM 5.3).  
- **#7082** – `Model 'unknown'` execution fails: `_StructuredOutputDynamicClass is not fully defined`.  
- **#7118** – Corrupt `envs.json` silently loses all stored environment variables on next write.  
- **#7110** – Unavailable image link in conversation breaks the entire session.  
- **#7076** – LLM model configuration returns 404 in `qwenpaw‑creator` 2.1.0.

**Medium severity (reported earlier, still open):**
- **#7063** – Tool‑call crash in v2.1.0 (`async for` on coroutine).  
- **#7046** – `execute_shell_command` mangles heredoc/multi‑line commands.  
- **#7039** – Spurious new sessions created; no option to disable file preview.  
- **#7065** – Chat history truncated after ~7 rounds.

**Fix PRs available:**
- **#7119** – Addresses the master‑key permission issue (related to #7118).  
- **#7066** – Fixes OAuth2 refresh‑token rotation (mitigates #7053).  
- **#7057** – Adds user‑local `PATH` entries (may help #7076).  
- **#7120** – Enables shell‑evasion checks by default (security hardening).

## 6. Feature Requests & Roadmap Signals
| Issue/PR | Type | Description |
|----------|------|-------------|
| [#6684](https://github.com/agentscope‑ai/CoPaw/issues/6684) | Enhancement | Add retry/health‑check for channel connections (Matrix, etc.). |
| [#7052](https://github.com/agentscope‑ai/CoPaw/issues/7052) | Enhancement | Grant plugin API a `system_prompt` permission to hide company‑specific prompts. |
| [#7062](https://github.com/agentscope‑ai/CoPaw/issues/7062) | Enhancement | Allow `reasoning_effort` to be configured per‑agent or per‑session. |
| [#7090](https://github.com/agentscope‑ai/CoPaw/issues/7090) | Enhancement | Add search/filter to the skill‑pool import page. |
| [#7112](https://github.com/agentscope‑ai/CoPaw/pull/7112) | Feature | Introduce a local QwenPaw Pro control plane (`qwenpaw app --pro`) with multi‑user isolation. |
| [#6880](https://github.com/agentscope‑ai/CoPaw/pull/6880) | Feature | Unify apps, plugins, and skills under a single marketplace UI (`/market`). |

**Predicted for next version:**  
- Channel retry/health‑check (#6684) – high user demand.  
- Per‑agent/session `reasoning_effort` (#7062) – enables differentiated agent roles.  
- Skill‑pool search/filter (#7090) – improves discoverability with large skill sets.  
- Marketplace unification (#6880) – simplifies the UI and is already in review.

## 7. User Feedback Summary
**Pain points:**
- **Channel instability** (#6684, #7011) – manual re‑connection after restarts; cross‑session interference.  
- **Task interruption** (#6921) – agent stops after planning without visual cue.  
- **Session freezes** (#7102, #7063) – hangs during model execution or tool calls.  
- **Configuration regressions** (#7076, #7046, #7039) – 404 on model config, heredoc mangling, spurious new sessions.  
- **Data loss risk** (#7118) – corrupt `envs.json` silently discards all stored env vars.  
- **False‑positive security alerts** (#6775) – Malware Bytes flags desktop version as Trojan Loader.

**Satisfaction notes:**
- Formula rendering improved in 2.1.0 (#7039).  
- Users appreciate the ongoing security hardening (shell‑evasion checks, key permissions).

**Use cases:**
- Multi‑channel enterprise integration (Matrix, Feishu, DingTalk).  
- Long‑running agent workflows requiring uninterrupted execution.  
- Secure handling of API keys and environment variables.

## 8. Backlog Watch
| Issue | Open Since | Comments | Why it needs attention |
|-------|------------|----------|------------------------|
| [#6684](https://github.com/agentscope‑ai/CoPaw/issues/6684) | 2026‑08‑04 | 10 | Critical for channel reliability; no fix PR yet. |
| [#6921](https://github.com/agentscope‑ai/CoPaw/issues/6921) | 2026‑08‑12 | 8 | Breaks multi‑step task workflows; user‑facing regression. |
| [#6470](https://github.com/agentscope‑ai/CoPaw/issues/6470) | 2026‑07‑26 | 5 | MCP transport bug affects all Streamable HTTP users. |
| [#4001](https://github.com/agentscope‑ai/CoPaw/issues/4001) | 2026‑05‑02 | 5 | Long‑standing feature request for message‑level delete. |
| [#5584](https://github.com/agentscope‑ai/CoPaw/issues/5584) | 2026‑06‑27 | 5 | Custom Ascend‑vLLM model connection broken after v1.1.7. |
| [#5900](https://github.com/agentscope‑ai/CoPaw/issues/5900) | 2026‑07‑09 | 2 | MCP session termination without auto‑reconnect. |
| [#6880](https://github.com/agentscope‑ai/CoPaw/pull/6880) | 2026‑08‑10 | – | Marketplace unification PR still under review; blocks UX improvement. |

**Recommendation:** Prioritize merging the security and stability PRs (#7120, #7119, #7066, #7057) before addressing feature requests. The channel‑retry (#6684) and task‑continuation (#6921) issues should be scheduled for the next bug‑fix sprint due to their direct impact on user productivity.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-19

## 1. Today's Overview

ZeroClaw shows strong daily engagement with 50 issues and 50 PRs updated in the last 24 hours, indicating a healthy contributor cadence. No new releases were shipped today, but 19 issues were closed and 2 PRs merged, reflecting steady progress on existing work. The project is actively addressing high-priority bugs (Windows CI gaps, MCP memory growth, credential exposure) while advancing architectural RFCs around goal mode, session-scoped prompts, and slash-command unification. Developer activity is concentrated across runtime, provider, and channel subsystems with several large PRs awaiting maintainer review.

## 2. Releases

No new releases published today.

## 3. Project Progress

**Merged/Closed Today:**
- **#10009** (closed) — Fixed conversation autosave suppression by tying it to turn origin rather than position-dependent prompt sniffing, resolving a heartbeat-worker bypass. [PR #10009](https://github.com/zeroclaw-labs/zeroclaw/pull/10009)
- **#10108** (open) — Aligned ZeroCode health-label translations with dynamic terminal-cell padding, fixing French label truncation. [PR #10108](https://github.com/zeroclaw-labs/zeroclaw/pull/10108)

**Notable Open PRs Advancing:**
- **#9743** — Wires modalities parser into `capabilities_for_model`, enabling per-model capability negotiation across providers and channels. [PR #9743](https://github.com/zeroclaw-labs/zeroclaw/pull/9743)
- **#10003** — Ensures Reliable provider attempt accounting stays exact across retries, failover, cancellation, and stream recovery. [PR #10003](https://github.com/zeroclaw-labs/zeroclaw/pull/10003)
- **#9419** — Rotates live credentials per-provider after rate-limit hits, cooling only the offending credential rather than the entire model. [PR #9419](https://github.com/zeroclaw-labs/zeroclaw/pull/9419)
- **#9420** — Adds stored OAuth profile support for Anthropic providers, separating OAuth and static-key flows. [PR #9420](https://github.com/zeroclaw-labs/zeroclaw/pull/9420)
- **#9109** — Adds native Hailo-Ollama provider support with typed config and text-only capability policy. [PR #9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109)
- **#9104** — Registers Grok Build ACP model provider via stdio JSON-RPC. [PR #9104](https://github.com/zeroclaw-labs/zeroclaw/pull/9104)

## 4. Community Hot Topics

- **[RFC #8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303)** — *Goal mode v1: bounded foreground Matrix work* (22 comments). The community is debating how to give agents a durable, bounded objective across multiple turns without coupling restart handoff, channel admission, and async child work into v1. This is the most discussed open issue and signals a strong demand for multi-turn goal persistence.
- **[Bug #7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462)** — *74 test failures on Windows* (17 comments). Windows CI coverage remains a pain point; the test suite runs only on Linux in CI, allowing platform-specific regressions to slip through.
- **[RFC #7415](https://github.com/zeroclaw-labs/zeroclaw/issues/7415)** — *Unify three agent turn engines* (5 comments, closed). Successfully executed as a single consolidation PR (#7540); demonstrates the team's preference for phased-in refactor-over-time rather than the originally planned phased migration.
- **[PR #9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109)** — Hailo-Ollama provider support (large, needs-author-action). Reflects community demand for diverse model provider integrations beyond the major cloud APIs.
- **[RFC #9998](https://github.com/zeroclaw-labs/zeroclaw/issues/9998)** — *Session-scoped persistent prompt attachments* (4 comments, opened 2026-08-14). A new RFC addressing prompt drift after history trimming or daemon restart — directly builds on the goal-mode discussion in #8303.

**Underlying need:** Users want agents that maintain objectives across turns and session boundaries, with reliable provider routing and broader model coverage. The RFC cluster around goal mode, persistent prompts, and session context indicates the roadmap is heading toward more robust multi-turn agent workflows.

## 5. Bugs & Stability

| # | Severity | Summary | Fix PR? |
|---|----------|---------|---------|
| #8642 | **P1 / High** | MCP/tool-schema cloning causes unbounded RSS growth in agent loop (split from OOM tracker #5542) | No open fix PR yet |
| #10107 | **P1 / High** | Google STT API keys exposed in URLs; proxy logs may capture credentials | **Yes — PR #10107** (in review) |
| #8563 | **P1 / High** | SOPs not detected by agent runtime from web dashboard shared path | Closed |
| #7462 | **P2 / High** | 74 Windows test failures due to Unix-only commands, path semantics, console encoding | No fix yet |
| #8410 | **P2 / High** | Channel tasks lack a first-class "no-reply" outcome; silent branches still send visible responses | No fix PR yet |
| #7069 | **P2 / Medium** | Twitter/X channel missing from pre-built binaries despite feature flag existing | Closed |
| #6679 | **P2 / Medium** | PRs can retain stale CI green checks after master advances | Closed |

**Key concern:** The MCP memory-growth bug (#8642) remains unfixed and was split from a WSL2 OOM tracker — this is the highest-severity open stability issue. The credential exposure in Google STT URLs (#10107) has an active fix PR.

## 6. Feature Requests & Roadmap Signals

- **#8303** — Goal mode v1 for bounded multi-turn objectives. **Likely in next release cycle** given accepted status and active RFC discussion.
- **#9998** — Session-scoped persistent prompt attachments. New RFC (4 days old); complements #8303.
- **#7929** — Unify slash-command registries across web UI, ZeroCode TUI, and channel runtime. Addresses command drift; accepted status suggests it's on the roadmap.
- **#8134** — Auto-reset stale channel sessions after `session_ttl_hours`. Reduces token consumption for team deployments.
- **#8228** — DingTalk channel streaming message support. Community contributor request; latency-sensitive use case.
- **#8409** — Raw stdout output for shell cron jobs. Small quality-of-life improvement.
- **#8519** — Reconcile `cargo-audit` and `cargo deny` ignore drift; remediates wasmtime-wasi CVEs. Security hygiene tracker.
- **#9109 / #9104** — Hailo-Ollama and Grok Build provider integrations. Both large PRs in review; suggest provider diversity is a near-term priority.
- **#9194** — Extract `KeySource` trait + `FileKeySource` backend for encryption key management. Security architecture improvement.

**Prediction:** The next release will likely include goal mode v1 (#8303), session-scoped prompts (#9998), and the new provider integrations (Hailo-Ollama, Grok Build), assuming the large PRs clear maintainer review.

## 7. User Feedback Summary

**Pain points:**
- Agents lose context after history trimming or daemon restart — driving the #8303 and #9998 RFCs.
- Conditional channel tasks (e.g., "reply only if there's new email") cannot stay silent — users see spurious responses (#8410).
- Windows users face broken test coverage and missing channel binaries (#7462, #7069).
- MCP tool-schema cloning causes memory bloat over time — production OOM risk (#8642).
- SOPs configured in shared paths are invisible to the agent runtime via web dashboard (#8563).
- Google STT keys leaking into URLs is a security concern (#10107).

**Satisfaction signals:**
- The successful consolidation of the turn-engine unification RFC (#7415 → PR #7540) shows the team delivers on accepted architectural work.
- Multiple distinguished contributors are actively engaged across provider, runtime, and channel PRs.
- The dependabot-driven rust-all bump (#9808) with 46 updates shows maintenance automation is functioning.

## 8. Backlog Watch

| # | Age | Issue | Risk | Needs |
|---|-----|-------|------|-------|
| #8642 | ~47 days | MCP/tool-schema RSS growth (P1) | High | Fix PR needed |
| #7462 | ~70 days | 74 Windows test failures (P1) | High | CI fix + platform coverage |
| #8367 | ~54 days | Derived capability readiness for agent guidance (P2) | High | Maintainer review |
| #8358 | ~54 days | zerorelay milestone tracker (P2) | High | Maintainer coordination |
| #8309 | ~55 days | Remove orphaned SkillForge engine (P2) | Medium | Decision: wire or remove |
| #8059 | ~60 days | Policy cleanup: deny.toml / audit.toml drift (P2) | Medium | Closed — completed |
| #3542 | ~157 days | Webhook agent-mode support (P2) | Medium | Stale; no recent activity |

**Top priority:** #8642 (MCP memory growth) and #7462 (Windows CI) are the longest-standing P1 issues with no resolved fix, posing the greatest risk to production stability and platform parity. Several large PRs (#9743, #10003, #9013, #9194, #9203, #9341, #9402, #9419, #9420, #9451, #9515) are flagged `needs-maintainer-review` and collectively represent significant runtime, provider, and security work that could unblock the next release if triaged.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*