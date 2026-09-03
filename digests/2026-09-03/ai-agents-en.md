# OpenClaw Ecosystem Digest 2026-09-03

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-03 04:00 UTC

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



# OpenClaw Project Digest — 2026-09-03

## 1. Today's Overview

OpenClaw is exhibiting exceptionally high development velocity with 500 issues and 500 PRs touched in the last 24 hours (349 open issues, 151 closed; 393 open PRs, 107 merged/closed). Activity is concentrated around the recently shipped 2026.8.1 release, which triggered a wave of migration regressions, auth-breakage reports, and gateway crash-loop incidents. The project is in a post-release triage crunch: the maintainers are actively shipping fix PRs across nearly every subsystem (cron, agents, Codex, Telegram, Slack, mobile), while new feature work on native realtime audio and operator-configured task lanes also advances. No new release was cut today, suggesting the team is stabilizing rather than iterating outward.

## 2. Releases

**No new releases in the last 24 hours.** The most recent shipped version remains **2026.8.1** (`ea80657`), which is itself the source of multiple regression issues today (see Bugs & Stability). A frozen-prerelease qualification fix (PR #136835) and Docker-scenario capability gating (PR #136761) are in flight to harden future release validation.

## 3. Project Progress

**Key PRs advanced or merged today:**

- **#136845** — `fix(swarm): queue Code Mode fan-out at the bridge limit` — resolves Swarm fan-out failures under Code Mode (opened today by steipete).
- **#136876** — `fix(process): release discarded command head buffers` — fixes a memory pin bug where a 16-byte prefix could hold an entire 64 KiB pipe buffer for the lifetime of a child process.
- **#136949** — `fix(ci): authenticate frozen source checkouts` — repairs CI anonymous Git read failures by passing the job token as a scoped HTTP header.
- **#136959** — `perf(agents): skip unused BTW reasoning collection` — avoids accumulating reasoning text when the stream cannot expose it, shaving unnecessary work from agent turns.
- **#136929** — `perf(mcp): prepare scheduler alias lookup once` — eliminates repeated full-map-to-array conversion in MCP scheduler alias resolution.
- **#136829** — `fix: auto-height dashboard widgets shrink on every resize report` — corrects a UI bug where pinned HTML widgets lost height on each resize round.
- **#136960** — `fix: Tailscale Control UI image previews stay available` — restores media preview visibility when the gateway is accessed via Tailscale Serve with token auth.
- **#136807** — `fix(agents): preserve sibling reroutes and repair Gateway release E2E` — addresses a Gateway E2E validation failure in the 2026.9.1 stable release candidate.
- **#136588** — `fix(update): make chat-triggered self-updates end in a visible outcome` — fixes the common failure mode where chat-initiated `openclaw update` silently dies after the system agent lost its update operation.
- **#134003** — `feat(talk): support native realtime for thin audio clients` — major feature for native realtime audio on constrained clients; still awaiting final CI proof.
- **#135890** — `feat(task-lanes): operator-configured lane boards` — introduces read-side operator boards grouping runs/runs-outputs; stacked on #135889.

## 4. Community Hot Topics

**Most-discussed open issues (by comment count):**

1. **[Bug] Cron agent stall on DeepSeek** (#121953) — 13 comments · 🦞 diamond lobster · P1
   The `[cron:<jobId> <name>]` prefix causes DeepSeek's API edge to deprioritize requests, stalling turns for seconds to minutes. Reflects heavy cron + DeepSeek usage in the community.
   <https://github.com/openclaw/openclaw/issues/121953>

2. **[Bug] MCP tools not injected into subagent sessions** (#85030) — 13 comments · 🦞 diamond lobster · P1 · 6 👍
   `bundle-mcp` and per-tool subagent allowlists are ignored; subagent system prompts receive only built-in tools. A fundamental multi-agent + MCP integration gap.
   <https://github.com/openclaw/openclaw/issues/85030>

3. **[Bug] AgentSelectionRequiredError floods under explicit multi-agent ownership** (#126360) — 12 comments · 🦞 diamond lobster · P1
   Logbook plugin, Control UI global RPCs, and system-agent turns all lack an `agentId` target, causing log floods. Mirrors issue #128637 (also P1) on the same root cause.
   <https://github.com/openclaw/openclaw/issues/126360>

4. **[Bug] MCP loopback transport does not auto-reconnect after gateway restart** (#98435) — 12 comments · 🦪 silver shellfish · P2 · 1 👍
   `recovered=1` is misleading — session transcript restores but the MCP handshake between Claude Code CLI and gateway is not re-established.
   <https://github.com/openclaw/openclaw/issues/98435>

5. **[Bug] Telegram durable update falsely tombstoned** (#127229) — 11 comments · 🦞 diamond lobster · P1
   Durably spooled Telegram DMs are lost during pre-adoption watchdog cycles under context-overflow compaction.
   <https://github.com/openclaw/openclaw/issues/127229>

**Underlying need:** The community is running OpenClaw at scale (multi-agent, multi-channel, scheduled cron), and the pain points cluster around **session-state integrity**, **cross-component handoff correctness**, and **delivery reliability** under failure/restart conditions.

## 5. Bugs & Stability

**Critical / P0–P1 bugs reported or updated today:**

| Issue | Severity | Summary | Fix PR? |
|---|---|---|---|
| [#123327](https://github.com/openclaw/openclaw/issues/123327) | **P0** · 🦐 gold shrimp | Shared-state WAL checkpoint copies index pages over SQLite page 1 on ext4 — **data corruption** on Raspberry Pi 5 + NVMe | — |
| [#134896](https://github.com/openclaw/openclaw/issues/134896) | **P1** · 🦞 diamond lobster | 2026.8.1 upgrade cascade: 5-blocker gateway restart loop + `doctor --fix` self-referential failure on legacy workspace state | — |
| [#134570](https://github.com/openclaw/openclaw/issues/134570) | **P1** · 🦞 diamond lobster | Same 2026.8.1 upgrade path: 7 distinct blockers, misleading errors, silent dispatch failures across Feishu/Discord/agents | — |
| [#134608](https://github.com/openclaw/openclaw/issues/134608) | **P1** · 🦞 diamond lobster · **CLOSED** | Auth migration archives `auth-profiles.json` without making credentials available — **permanently blocks repair** after 2026.7→2026.8.1 Docker upgrade | PR linked |
| [#135835](https://github.com/openclaw/openclaw/issues/135835) | **P1** · 🦞 diamond lobster | Token balance replenishment not recognized after upgrade to 2026.8.1; restart does not recover | — |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | **P1** · 🦐 gold shrimp | Unreaped hook/tool child processes accumulate as zombies, degrading runtime | — |
| [#115424](https://github.com/openclaw/openclaw/issues/115424) | **P1** · 🦞 diamond lobster | Gateway V8 heap OOM during main-session turn; restart-recovery hot-resume converts one crash into a 7-core dump loop | — |
| [#127229](https://github.com/openclaw/openclaw/issues/127229) | **P1** · 🦞 diamond lobster | Telegram durable updates tombstoned by watchdog during context-overflow compaction | — |
| [#128971](https://github.com/openclaw/openclaw/issues/128971) | **P1** · 🦐 gold shrimp | Telegram final reply silently lost when terminal receipt returns `delivery_ambiguous` | — |
| [#126246](https://github.com/openclaw/openclaw/issues/126246) | **P1** · 🦞 diamond lobster | Telegram outbound deliveries stuck in `send_attempt_started` and lost on restart | — |
| [#136262](https://github.com/openclaw/openclaw/issues/136262) | **P1** · 🦞 diamond lobster | OpenAI completions stream: bare `text_delta` replays full accumulated text, doubling message content | — |
| [#121953](https://github.com/openclaw/openclaw/issues/121953) | **P1** · 🦞 diamond lobster | Cron agent stalls on DeepSeek due to prefix deprioritization at API edge | — |
| [#85030](https://github.com/openclaw/openclaw/issues/85030) | **P1** · 🦞 diamond lobster | MCP tools not injected into `sessions_spawn` subagents | — |
| [#123327](https://github.com/openclaw/openclaw/issues/123327) | **P0** · 🦐 gold shrimp | SQLite page-1 corruption via WAL checkpoint on ext4 | — |

**Notable closed bugs today:**
- [#123073](https://github.com/openclaw/openclaw/issues/123073) — `dev-channel update` `EUNSUPPORTEDPROTOCOL` on `workspace:*` (npm vs pnpm) — **closed**.
- [#134608](https://github.com/openclaw/openclaw/issues/134608) — Auth migration archives credentials without making them available — **closed** (PR linked).
- [#96692](https://github.com/openclaw/openclaw/issues/96692) — Slack thread replies generated but not delivered after origin tuple loss — **closed**.
- [#78380](https://github.com/openclaw/openclaw/issues/78380) — Gateway self-restart from chat turn drops in-flight Telegram/Discord replies — **closed**.
- [#134337](https://github.com/openclaw/openclaw/issues/134337) — `memory_search` dirty maintenance full-reindexes under concurrent writes — **closed**.
- [#123335](https://github.com/openclaw/openclaw/issues/123335) — `plugins init` scaffolds `openclaw: latest` picking older CLI — **closed**.
- [#134160](https://github.com/openclaw/openclaw/issues/134160) — Control UI unread badge not clearing on session open — **closed**.

**Assessment:** The 2026.8.1 release introduced significant migration and auth regressions. The P0 SQLite corruption bug (#123327) and the gateway restart cascade (#134896, #134570) are the most dangerous open items. Several Telegram delivery bugs suggest the durable-send path needs hardening. Fix PRs are actively being written (see PRs in §3) but the velocity of bug reports outpaces closure.

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Type | Summary | Likelihood for Next Release |
|---|---|---|---|
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | Feature · P2 | Self-hosted STT/TTS provider support in webchat (route through gateway instead of browser Speech API) | Medium — clear user need for self-hosted voice |
| [#121729](https://github.com/openclaw/openclaw/issues/121729) | Feature · P3 | Daily spending allowances for background agents (shared & per-agent) | Medium — operational safety feature operators request |
| [#16555](https://github.com/openclaw/openclaw/issues/16555) | Feature · P1 | TTL / expiry for delivery queue messages | Medium-High — prevents stale-orphaned delivery queue growth |
| [#52803](https://github.com/openclaw/openclaw/issues/52803) | Feature · P2 | Control UI multi-agent + subagent orchestration (hierarchy, bulk ops) | Medium — UI scaling pain is real but complex |
| [#134003](https://github.com/openclaw/openclaw/pull/134003) | **Feat** · P2 | Native realtime support for thin audio clients | **High** — already in progress, awaiting CI proof |
| [#135890](https://github.com/openclaw/openclaw/pull/135890) | **Feat** · P3 | Operator-configured task lane boards | Medium — stacked PR, depends on #135889 |
| [#134943](https://github.com/openclaw/openclaw/pull/134943) | **Feat** · P2 | Plugin SDK for Control UI customization | Medium-High — enables ecosystem extensibility |
| [#136610](https://github.com/openclaw/openclaw/pull/136610) | **Feat** · P1 | Guarded mobile beta release CI pipeline | High — operational need for mobile release safety |
| [#136079](https://github.com/openclaw/openclaw/pull/136079) | **Feat** · P2 | Show every mounted local disk in Control UI diagnostics | High — small scope, high operator value |

**Signal:** The roadmap is leaning into **operator controllability** (task lanes, spending allowances, disk diagnostics, mobile beta CI) and **platform extensibility** (plugin UI SDK, native realtime audio). The next stable release will likely prioritize stabilization of 2026.8.1 regressions over new features.

## 7. User Feedback Summary

**Pain points:**
- **Upgrade pain is severe.** Multiple users report that upgrading from 2026.7.x → 2026.8.1 causes gateway crash-loops, auth lockouts, and silent dispatch failures. The auth migration (#134608) archived credentials without restoring them, requiring manual intervention.
- **Token balance not refreshing after top-up** (#135835) — users cannot resume conversations after recharging, even after full restarts.
- **Telegram delivery reliability** is a recurring theme: stuck outbound messages (#126246), falsely tombstoned durable updates (#127229), and silently lost final replies (#128971).
- **MCP subagent injection** (#85030) is a blocker for users running tool-rich subagents — a fundamental expectation that is broken.
- **Cron + DeepSeek incompatibility** (#121953) causes multi-minute stalls, making scheduled agents unreliable for users on that provider.
- **iOS app keyboard input ignored** on iOS 26.6.0 (#122648) and credential save failures after force-quit.
- **WebSocket/reasoning stream bugs** (#136262) cause doubled message content in OpenAI completions stream, confusing users and breaking integrations.

**Satisfaction signals:**
- Users actively engage with detailed bug reports including exact commits, reproductions, and environment details — indicating a committed power-user base.
- Several issues have received maintainer acknowledgment and linked PRs, suggesting the team is responsive.
- The `👍` counts on #85030 (6), #78380 (2), #65374 (2), #136262 (1) show community validation on key pain points.

## 8. Backlog Watch

**Long-open, high-impact issues needing maintainer attention:**

| Issue | Open Since | Severity | Comments | Why It Matters |
|---|---|---|---|---|
| [#45494](https://github.com/openclaw/openclaw/issues/45494) | 2026-03-13 | P2 · 🐚 platinum hermit | 9 | Cron jobs silently time out

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Open-Source Ecosystem

**Date:** 2026-09-03 | **Scope:** 12 Open-Source Projects

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape in September 2026 is characterized by rapid post-release stabilization cycles, with most projects simultaneously shipping features and triaging regressions from recent major releases. Development velocity ranges from dormant (NullClaw, ZeptoClaw) to extremely active (OpenClaw at 500+ events/24h, ZeroClaw at 100+ events/24h), with a clear industry shift toward production-grade concerns: session persistence, security sandboxing, multi-agent coordination, and delivery reliability. The ecosystem is moving beyond prototype-stage single-session agents toward multi-tenant, multi-channel, scheduled-automation systems where data integrity and fault tolerance are the dominant engineering challenges.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Open Issues | Open PRs | Latest Release | Health Score |
|---|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 349 | 393 | 2026.8.1 (stalled) | 🟡 Stressed — post-release triage crunch |
| **Hermes Agent** | 50 | 50 | — | 47 | None today | 🟢 Active — strong contributor engagement |
| **IronClaw** | 10 | 26 | — | 6 | None today | 🟢 High velocity — TypeScript cleanup sprint |
| **ZeroClaw** | 100+ | 100+ | — | — | None today | 🟢 High velocity — RFC-driven architecture phase |
| **NanoBot** | — | 23 | — | 19 | None today | 🟢 Active — stabilization focus |
| **Moltis** | 2 | 3 | 2 | 3 | 20260902.03 (3 patches in 1 day) | 🟢 Rapid iteration |
| **CoPaw** | 28 | 27 | — | — | v2.2.0 (just shipped) | 🟡 Post-release bug surface |
| **NanoClaw** | 2 | 21 | — | — | None today | 🟢 Focused — security hardening |
| **LobsterAI** | 8 | 9 | 2 (critical) | — | 2026.8.31 (browser reverted) | 🟡 Caution — stale closures, unmerged critical PRs |
| **PicoClaw** | 1 | 1 | 1 (critical) | — | None today | 🟡 Moderate — core channel broken |
| **NullClaw** | 0 | 0 | — | — | — | 🔴 Inactive |
| **ZeptoClaw** | 0 | 0 | — | — | — | 🔴 Inactive |

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of activity:** OpenClaw processes 5–10× more daily events than any other project, indicating the largest active user base and contributor pipeline in the ecosystem.
- **Multi-channel maturity:** Native support for Telegram, Slack, Discord, Feishu, Tailscale, and mobile — unmatched channel coverage. The community hot topics (MCP subagent injection, cron+DeepSeek stalls, Telegram delivery) reflect production-scale multi-channel deployments that smaller projects haven't yet encountered.
- **Release cadence:** Regular semantic versioning (currently 2026.8.1) with a structured migration path, though the current 2026.8.1 regression wave demonstrates the risk of high velocity without adequate pre-release gating.

**Technical approach differences:**
- OpenClaw uses a gateway-centric architecture with a persistent control plane, session WAL, and provider-agnostic agent runtime — closer to a platform than a single-agent tool. Competing projects like NanoBot and Moltis are lighter-weight, single-process designs.
- The Swarm/Code Mode fan-out architecture and operator-configured task lanes signal a focus on multi-agent orchestration at scale, whereas projects like Hermes and ZeroClaw are building similar capabilities through RFC-driven architectural redesigns rather than incremental feature adds.

**Community size comparison:**
- OpenClaw's community is the largest by an order of magnitude (500 events/24h, diamond lobster / gold shrimp tiered severity labels, 13+ comment hot topics). Hermes and ZeroClaw have moderate but highly engaged technical communities. NanoBot, Moltis, and NanoClaw have smaller contributor bases with strong focused participation. LobsterAI and PicoClaw have the smallest active communities, with LobsterAI showing concerning stale-issue accumulation.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs Identified |
|---|---|---|
| **Session persistence & state integrity** | OpenClaw, Hermes Agent, ZeroClaw, CoPaw | OpenClaw: Telegram durable updates tombstoned, gateway restart loops. Hermes: SQLite WAL corruption, orphaned leases. ZeroClaw: RFC on runtime-owned sessions (32k token cap confusion). CoPaw: Context loss in long sessions (~3 days, 160 pages). |
| **Multi-agent coordination & observability** | OpenClaw, Hermes Agent, IronClaw, ZeroClaw | OpenClaw: MCP tools not injected into subagent sessions (#85030, P1). Hermes: Group chat continuity across device reconnects (#97681). IronClaw: Subagent approval gates invisible to parent owners (#8046). ZeroClaw: Per-agent knowledge graph/session scoping (PRs #9745/#9746). |
| **Delivery reliability (channel integrations)** | OpenClaw, NanoClaw, IronClaw, PicoClaw | OpenClaw: Telegram stuck/outbound lost, Slack thread reply loss. NanoClaw: Retry waste on disconnected adapters (#3703), `send_card` callback drops (#3427). IronClaw: Progressive reply concatenation bug (now fixed). PicoClaw: QQ Channel 401 auth failure blocking entire channel (#3349). |
| **Security sandboxing & supply chain** | CoPaw, NanoBot, ZeroClaw, NanoClaw, LobsterAI | CoPaw: Active sandbox breach attempts (#7511), dangerous instruction evasion (#7443). NanoBot: Path traversal via session keys (#5633), macOS Seatbelt sandbox (#5628). ZeroClaw: Delegate bypassing `block_high_risk_commands` (#10165, P1). NanoClaw: minimumReleaseAge gate finally activated (#2973). LobsterAI: MCP stdio command parsing hardening (#2590). |
| **Token/context management accuracy** | NanoBot, OpenClaw, CoPaw | NanoBot: tiktoken undercounts 30–50%, breaking context consolidation (#5402/P1). OpenClaw: OpenAI stream `text_delta` replays full accumulated text, doubling content (#136262). CoPaw: ReMe embedding failures, silent context loss. |
| **Hook/event lifecycle completeness** | Moltis, Hermes Agent | Moltis: `AgentEnd`, `MessageSending`, `MessageSent` hooks declared but never dispatched (#1255); missing `tool_call_id` correlation (#1254). Hermes: MCP stdio orphans causing OOM on macOS (#81880). |
| **Realtime voice / audio** | OpenClaw, Hermes Agent, CoPaw | OpenClaw: Native realtime audio for thin clients (#134003). Hermes: RFC for unified RealtimeVoiceProvider ABC (#77111), browser WebRTC voice mode demand (#20765, 6 👍). CoPaw: WeCom streaming sluggishness due to 150ms throttle (#7507). |
| **Provider contract & integration hygiene** | ZeroClaw, NanoClaw, IronClaw, LobsterAI | ZeroClaw: Wire protocol as first-class in provider construction (RFC #8396). NanoClaw: Coordinated provider contract refactoring (PRs #3584–#3593). IronClaw: Durable progressive replies with provider-neutral `ReplyDocument` contract (#8006). LobsterAI: Provider-switch race condition on gateway restart (#1101). |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | IronClaw | ZeroClaw | NanoBot | CoPaw | Moltis | LobsterAI |
|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Multi-channel gateway platform | Desktop-first agent with voice | WebUI v2 + TypeScript rigor | Architecture RFCs & sandbox policy | Lightweight personal agent | Multi-user hub + security sandbox | Hook lifecycle + reasoning control | IM/Cowork concurrency |
| **Target user** | Power users, multi-agent operators, enterprise-adjacent | Desktop power users, voice-first workflows | Web UI developers, TypeScript-heavy teams | Researchers, architecture-focused contributors | Individual developers, containers | Multi-tenant team deployments | Event-driven automation builders | Chinese-market IM users |
| **Architecture** | Gateway-centric, WAL-persisted, provider-agnostic runtime | Session-state focused, RFC-governed design | TypeScript/React frontend + Rust backend | RFC-driven architectural evolution | Lightweight, local-first | Hub + workspace-level access control | Hook-based event pipeline | Electron-based desktop |
| **Release model** | Semantic versioning (2026.8.1) | No recent release | No recent release | No recent release | No recent release | v2.2.0 stable + beta cadence | Daily patch releases | 2026.8.31 (stalled) |
| **Key differentiator** | Scale & channel coverage | Voice RFC maturity + group chat continuity | WebUI v2 TypeScript elimination sprint | Deep architectural governance via RFCs | Security hardening (Seatbelt, path traversal) | Multi-user Hub with sandbox security | Hook completeness + reasoning effort tiers | QQ/WeChat ecosystem focus |

---

## 6. Community Momentum & Maturity

**Tier 1 — High Velocity, Production-Grade Activity:**
- **OpenClaw:** 500 events/24h. Largest community. Currently in post-release triage — maturity signal is the volume of regression reporting, not lack of activity. The diamond lobster severity tier and structured issue taxonomy indicate an evolved community.
- **ZeroClaw:** 100+ events/24h. RFC-driven governance with maintainer decision trackers (#8692). Community participates in architectural design, not just bug reporting — a sign of mature contributor culture.
- **Hermes Agent:** 50 events/24h. Strong contributor engagement on session continuity and voice architecture. RFC acceptance process (#77111 → PR #101808) shows healthy community-government feedback loops.

**Tier 2 — Active & Healthy:**
- **IronClaw:** 36 events/24h with a coordinated TypeScript cleanup sprint (170 files, ~62K lines). High-velocity refactoring indicates a project maturing its codebase quality.
- **NanoBot:** 23 PRs, 19 open. Steady contributor momentum on security (Seatbelt, path traversal) and observability. Smaller but focused community.
- **CoPaw:** 28 issues/27 PRs around v2.2.0 launch. Post-release bug surface is normal; the rapid v2.2.0 → v2.2.0-beta.7 cadence shows active maintenance.

**Tier 3 — Moderate / Caution:**
- **NanoClaw:** 21 PRs, focused on security hardening. Small but disciplined contributor base.
- **Moltis:** 3 patch releases in one day — rapid iteration, but only 5 total events. Small team shipping fast.
- **LobsterAI:** 8 issues/9 PRs but 6 stale closures and 2 critical concurrency PRs open since March 2026. Momentum is present but governance concerns exist.
- **PicoClaw:** 1 PR merged after 6 months, 1 critical bug (QQ auth) unresolved. Slow review cycle + broken core channel = caution.

**Tier 4 — Inactive:**
- **NullClaw** and **ZeptoClaw:** Zero activity. Either dormant or pivoted.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Session-state integrity is the #1 engineering challenge** | OpenClaw (WAL corruption, Telegram tombstoning), Hermes (SQLite B-tree corruption, orphaned leases), ZeroClaw (32k context cap confusion, session persistence RFC), CoPaw (context loss in long sessions) | Any production agent system must treat persistence as a first-class concern. SQLite multi-process safety, lease management, and compaction strategy are non-negotiable. |
| **Security sandboxing is moving from optional to core** | CoPaw (active breach testing), ZeroClaw (delegate bypass P1), NanoBot (Seatbelt sandbox, path traversal), NanoClaw (minimumReleaseAge supply-chain gate), LobsterAI (MCP stdio hardening) | Sandboxing is no longer a differentiator — it's a baseline expectation. Multi-tenant deployments will require per-agent permission scoping as a default. |
| **Multi-agent orchestration visibility gaps are universal** | OpenClaw (MCP tools not injected into subagents), Hermes (group chat continuity), IronClaw (blocked subagent invisibility), ZeroClaw (per-agent scoping PRs) | The industry lacks mature patterns for parent-agent observability into child-agent state. Projects solving this (task lanes, approval gates, scoped knowledge graphs) will have a competitive edge. |
| **Hook/event lifecycle completeness is emerging as a quality signal** | Moltis (hooks declared but never dispatched), Hermes (MCP stdio orphans, OOM), OpenClaw (cron stalls) | Reliable event-driven automation requires complete lifecycle hooks. Projects with gaps here will struggle in production cron/trigger scenarios. |
| **Token/context accounting accuracy is silently breaking user workflows** | NanoBot (30–50% tiktoken undercount), OpenClaw (stream text duplication), CoPaw (silent embedding failures) | Inaccurate token estimation causes silent context overflow without compaction triggers. This is a pervasive infrastructure bug across the ecosystem — a reliable token accounting layer is a high-value missing component. |
| **Realtime voice is the next frontier feature** | OpenClaw (native realtime audio PR), Hermes (RFC-driven unified voice provider), CoPaw (WeCom throttling) | Voice is moving from browser-dependent (WebRTC) to native/client-level. Projects with unified voice provider abstractions will enable cross-platform voice agent experiences. |
| **Provider contract unification is reducing integration debt** | ZeroClaw (wire protocol RFC), NanoClaw (coordinated contract refactoring), IronClaw (provider-neutral ReplyDocument) | Ad-hoc provider integrations are a maintenance trap. Canonical provider contracts with typed boundaries are the architectural pattern winning across projects. |
| **Chinese-market channel integration (QQ/WeCom/Feishu) is a distinct subsystem** | OpenClaw (Feishu/Discord blockers), PicoClaw (QQ 401 auth failure), CoPaw (WeCom throttling) | Western-centric agent projects lack these integrations. Projects with mature QQ/WeCom/Feishu support occupy a defensible niche in the Chinese market. |

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-03

---

## 1. Today's Overview

NanoBot is experiencing high integration activity with **23 PRs updated** in the last 24 hours, though the majority (19) remain open awaiting review or CI. Four PRs were merged or closed today, signaling steady forward momentum on bug fixes and UX polish. No new releases were published, and no issues were closed, suggesting the maintainers are focused on stabilizing the current codebase before a release cadence. Overall project health is **active and healthy**, with strong contributor engagement across security, provider integrations, and WebUI improvements.

---

## 2. Releases

No new releases were published today. The project continues to operate on the current main branch with incremental merges.

---

## 3. Project Progress

**Merged / Closed PRs Today:**

- **[#5568](https://github.com/HKUDS/nanobot/pull/5568)** — *refactor(agent): let runner own context compaction* — The `AgentRunner` now directly orchestrates local request-pressure context compaction, consolidating the flow and removing ambiguity about ownership. This is a meaningful architectural cleanup.
- **[#5623](https://github.com/HKUDS/nanobot/pull/5623)** — *fix(agent): drop empty active-task groups after tasks finish* — Fixes a memory leak in long-running gateways where empty task sets accumulated in `_active_tasks` indefinitely (closes #5428).
- **[#5625](https://github.com/HKUDS/nanobot/pull/5625)** — *feat(webui): guide first-run AI setup* — Replaces the alarming "Model not configured" warning with a neutral onboarding prompt that opens the Models settings directly, improving first-time user experience.

**Actively Advanced (Open PRs):**

- **#5628** — macOS Seatbelt sandbox backend for process isolation
- **#5627** — Ephemeral runtime context blocks (implements #5586)
- **#5633** — Path traversal protection for session keys (P1 security)
- **#5403** — Token consolidation fix using API-reported counts (P1)
- **#5636** — Native sidebar control alignment across WebUI and desktop host

---

## 4. Community Hot Topics

| Rank | Item | Type | Comments | Focus |
|------|------|------|----------|-------|
| 1 | [#5628](https://github.com/HKUDS/nanobot/pull/5628) — macOS Seatbelt sandbox | PR (Open) | — | Security/isolation |
| 2 | [#5212](https://github.com/HKUDS/nanobot/pull/5212) — MiniMax music guidance | PR (Open) | — | Provider expansion |
| 3 | [#5403](https://github.com/HKUDS/nanobot/pull/5403) — Token consolidation fix | PR (Open, P1) | — | Reliability |
| 4 | [#5586](https://github.com/HKUDS/nanobot/issues/5586) — Ephemeral runtime context blocks | Issue (Open) | 2 | Feature request |
| 5 | [#5631](https://github.com/HKUDS/nanobot/issues/5631) — Display context & model speed in WebUI | Issue (Open) | 0 | UX visibility |

**Analysis:** The community is driving two clear themes: **(1) security hardening** (Seatbelt sandbox, path traversal fix, OAuth token persistence) and **(2) observability** (WebUI context display, Langfuse tracing for Codex, token consolidation accuracy). The MiniMax music PR, while open for a month, shows sustained interest in expanding the provider ecosystem beyond text.

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Status |
|----------|-----------|-------------|--------|
| **P1** | [#5402 → #5403](https://github.com/HKUDS/nanobot/pull/5403) | Local tiktoken undercounts prompt tokens by 30–50%, preventing context consolidation from ever triggering | Fix PR open |
| **P1** | [#5564 → #5633](https://github.com/HKUDS/nanobot/pull/5633) | Session keys with path traversal components (`../../etc/passwd`) could address files outside the sessions directory | Fix PR open |
| **P2** | [#5428 → #5623](https://github.com/HKUDS/nanobot/pull/5623) | Empty active-task sets leak in long-running gateways | **Fixed (merged)** |
| **P2** | #5635 — SDK stream event loss | Queued events dropped when stream queue is full and completion sentinel is written | Fix PR open |
| **P2** | #5634 — Unbounded fingerprint cache | Origin reply fingerprint cache grows indefinitely in long-running processes | Fix PR open |
| **P2** | #5446 — Codex OAuth token persistence | Tokens stored outside Nanobot's data directory, breaking container deployments | Fix PR open |
| **P2** | #5638 — Copilot OAuth token persistence | Same issue as #5446 but for GitHub Copilot | Fix PR open |
| **P2** | #5637 — Matrix stream delivery failures | `send_delta()` silently suppresses delivery failures instead of propagating them | Fix PR open |

**Assessment:** Three P2 bugs were fixed today (#5623, #5625 indirectly via UX). Two P1 issues (token consolidation, path traversal) have open fix PRs but are not yet merged — these should be prioritized. No regressions reported.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Next Release |
|---------|--------|----------------------------|
| Ephemeral runtime context blocks | #5586 (issue) → #5627 (PR) | **High** — PR already implemented, awaiting review |
| macOS Seatbelt sandbox backend | #5628 (PR) | **High** — PR ready, mirrors existing `bwrap` pattern |
| WebUI context/speed display | #5631 (issue) | **Medium** — requested, no PR yet; similar to DeepSeek Harness |
| Langfuse tracing for Codex | #5520 (PR) | **Medium-High** — PR open, fills a clear observability gap |
| Configurable cron delivery & batch archive | #5620 (PR) | **Medium** — feature-complete PR, needs review |
| Telegram rich message streaming | #5614 (PR) | **Medium** — author notes personal usage this week |
| Shared session heartbeat mode | #4551 (PR) | **Low-Medium** — open since June, has conflicts |

---

## 7. User Feedback Summary

- **"Token counts are wrong"** — Users relying on context consolidation are hitting silent failures because local tiktoken estimates don't match API-reported counts, causing conversations to exceed context windows without triggering compaction. ([#5402](https://github.com/HKUDS/nanobot/issues/5402))
- **"I can't see what's happening in my session"** — Users want real-time visibility into context usage and model speed in the WebUI, similar to DeepSeek Harness. ([#5631](https://github.com/HKUDS/nanobot/issues/5631))
- **"Runtime context leaks across turns"** — Users need ephemeral context blocks for one-shot instructions (e.g., tool schemas) that shouldn't consume persistent context budget. ([#5586](https://github.com/HKUDS/nanobot/issues/5586))
- **"Container deployments lose OAuth tokens"** — Codex and Copilot tokens persist outside Nanobot's managed directory, breaking statefulness in containers. ([#5446](https://github.com/HKUDS/nanobot/issues/5446), [#5638](https://github.com/HKUDS/nanobot/pull/5638))
- **First-run experience is alarming** — New users see a "Model not configured" warning that feels like a broken installation rather than a setup step. ([#5625](https://github.com/HKUDS/nanobot/pull/5625) — now fixed)

---

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) — Isolated session heartbeat config | ~2.5 months | Open since June 26 with conflicts; no maintainer response recently |
| [#5212](https://github.com/HKUDS/nanobot/pull/5212) — MiniMax music guidance | ~1 month | Stalled in review; contributor active but no merge signal |
| [#5614](https://github.com/HKUDS/nanobot/pull/5614) — Telegram rich message streaming | ~4 days | Author intends to use it personally this week; needs formal review |
| [#5403](https://github.com/HKUDS/nanobot/pull/5403) — Token consolidation P1 fix | ~17 days | P1 severity, fix PR open but not yet merged — **highest backlog priority** |
| [#5633](https://github.com/HKUDS/nanobot/pull/5633) — Path traversal P1 fix | ~1 day | Recently submitted; should be fast-tracked given severity |

**Recommendation:** The two P1 fixes (#5403, #5633) and the long-stalled #4551 deserve maintainer attention in the near term. The project has strong contributor momentum but could benefit from clearer triage timelines on open PRs approaching the one-month mark.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-09-03

## 1. Today's Overview

Hermes Agent shows robust development velocity with **50 issues and 50 PRs** updated in the last 24 hours, of which 47 remain open across both tracks. No new release was published today. Three previously open issues were closed (#97948, #98077, #101415), all related to session-state stability. The project is actively advancing session-continuity infrastructure, realtime voice architecture, and desktop reliability, with strong community engagement on group-chat persistence and voice-mode design decisions.

## 2. Releases

*No new releases published in the reporting window.*

## 3. Project Progress

**Closed today (3):**

| Issue | Summary |
|---|---|
| [#97948](https://github.com/NousResearch/hermes-agent/issues/97948) | Manual `/compress` 120s timeout while background worker succeeded — session compression race condition identified |
| [#98077](https://github.com/NousResearch/hermes-agent/issues/98077) | SQLite 3.50.4 WAL B-tree corruption under multi-process load — forensic recovery findings |
| [#101415](https://github.com/NousResearch/hermes-agent/issues/101415) | Backend orphaned lease read as sibling owner, permanently locking sessions |

**Open PRs advancing today:**

- [#101808](https://github.com/NousResearch/hermes-agent/pull/101808) — Realtime voice provider contract, orchestrator, and first built-in provider (by TheSmokeDev)
- [#101052](https://github.com/NousResearch/hermes-agent/pull/101052) — Provider-neutral `AgentRuntime` plugin API for whole-turn runtimes
- [#101855](https://github.com/NousResearch/hermes-agent/pull/101855) — Profile name resolution from symlink-farm overlay homes
- [#101851](https://github.com/NousResearch/hermes-agent/pull/101851) — sherpa-onnx upgrade to 1.13.5 and pypinyin dependency declaration (fixes dead wake-word spotter)
- [#101852](https://github.com/NousResearch/hermes-agent/pull/101852) — Desktop `browser_exec` hang fix via temp-file stdout capture
- [#101850](https://github.com/NousResearch/hermes-agent/pull/101850) — Stream `update.log` / heartbeat past Desktop idle watchdog (Windows)
- [#101824](https://github.com/NousResearch/hermes-agent/pull/101824) — Atomic timeout-to-late-ack handoff in compression path
- [#98307](https://github.com/NousResearch/hermes-agent/pull/98307) — Group Chat continuity: conversation, files, and cross-device control
- [#100303](https://github.com/NousResearch/hermes-agent/pull/100303) — Performance: open desktop transcripts from authoritative persisted pages

## 4. Community Hot Topics

1. **[Issue #97681](https://github.com/NousResearch/hermes-agent/issues/97681)** — *Bot Group Chats should keep working after Desktop closes* — **23 comments**. The most discussed topic; connects gateway-owned authority, same-gateway runner, and scoped cross-gateway transport. Users want seamless bot continuity across device reconnects. A corresponding PR (#98307) is now open.

2. **[Issue #77111](https://github.com/NousResearch/hermes-agent/issues/77111)** — *RFC: RealtimeVoiceProvider ABC* — **22 comments, 2 👍**. Four competing duplex-voice PRs need a unified interface per `AGENTS.md` Footprint Ladder policy. The community is pushing for an ABC + orchestrator pattern rather than merging PRs individually. PR #101808 directly addresses this RFC.

3. **[Issue #78642](https://github.com/NousResearch/hermes-agent/issues/78642)** — *Shard `tools/mcp_tool.py` (god-file decomposition)* — **16 comments**. The 7,230-line god file is a known technical debt target; repo-wide policy mandates decomposition. No active PR yet — a clear opportunity for contributor involvement.

4. **[Issue #20765](https://github.com/NousResearch/hermes-agent/issues/20765)** — *Voice mode in browser dashboard (WebRTC)* — **9 comments, 6 👍**. Highest reaction count; remote users over SSH/PTY cannot access the microphone. Strong demand for browser-based voice capture.

5. **[Issue #81880](https://github.com/NousResearch/hermes-agent/issues/81880)** — *MCP stdio orphans accumulate in Desktop (OOM on 16 GB Macs)* — **4 comments**. Production-impacting memory leak observed on macOS with 300+ node processes.

## 5. Bugs & Stability

**P1 — Critical / High impact:**

| Issue | Title | Fix PR |
|---|---|---|
| [#101800](https://github.com/NousResearch/hermes-agent/issues/101800) | Rate-limit exit sentinel unreachable; quota exhaustion → crashloop | None yet |
| [#101669](https://github.com/NousResearch/hermes-agent/issues/101669) | MCP boolean property schema disables entire server | None yet |
| [#81880](https://github.com/NousResearch/hermes-agent/issues/81880) | MCP stdio orphans cause OOM on desktop (Mac 16 GB) | None yet |
| [#101644](https://github.com/NousResearch/hermes-agent/issues/101644) | v0.21.0 named `/v1/responses` conversations duplicate history (2 turns → 8 msgs) | None yet |
| [#96731](https://github.com/NousResearch/hermes-agent/issues/96731) | `browser_exec` 420s timeout on Windows desktop; fixed in [#101852](https://github.com/NousResearch/hermes-agent/pull/101852) | #101852 open |

**P2 — Moderate:**

| Issue | Title | Fix PR |
|---|---|---|
| [#101748](https://github.com/NousResearch/hermes-agent/issues/101748) | Dashboard serves Electron renderer when `HERMES_DESKTOP=1` | None yet |
| [#101817](https://github.com/NousResearch/hermes-agent/issues/101817) | ACP context meter reports cumulative tokens as current usage | None yet |
| [#101783](https://github.com/NousResearch/hermes-agent/issues/101783) | Discord typing indicator persists after idle (leaked task) | None yet |
| [#101744](https://github.com/NousResearch/hermes-agent/issues/101744) | `rollback.diff` silently truncates at 4000 chars with no flag | None yet |
| [#76457](https://github.com/NousResearch/hermes-agent/issues/76457) | `hermes config set` stringifies list-of-strings as JSON literal | None yet |
| [#101786](https://github.com/NousResearch/hermes-agent/issues/101786) | Project-level skills not callable via `/` in Desktop | None yet |
| [#53836](https://github.com/NousResearch/hermes-agent/issues/53836) | Live multimodal voice mode with real-time interaction | None yet |

## 6. Feature Requests & Roadmap Signals

| Feature | Source | Signal Strength |
|---|---|---|
| **Realtime voice (speech-to-speech)** | #77111 (RFC), #53836, #20765, #101808 (PR) | **High** — RFC accepted, PR #101808 submitted; likely in next minor release |
| **AgentRuntime plugin API** | #101052 (PR) | **High** — provider-neutral runtime seam; architectural enabler |
| **Group Chat continuity** | #97681 (issue), #98307 (PR) | **High** — foundation merged to `main`; continuity layer in PR #98307 |
| **Voice mode in browser dashboard** | #20765 (6 👍) | **Medium** — strong community interest; depends on WebRTC availability |
| **IMAP IDLE receive mode** | #92753 (PR) | **Medium** — opt-in, backward-compatible; low-risk feature |
| **Webhook completion scripts** | #80533 (PR) | **Medium** — async agent + post-completion script |
| **Cron `send_message` tool opt-in** | #20140 | **Low** — known limitation, no active PR |
| **Remote Control / Cowork mode** | #38737 | **Low** — community request; no active PR |

## 7. User Feedback Summary

**Pain points:**
- **Session-state reliability** dominates: compression timeouts (#97948), SQLite corruption (#98077), orphaned leases (#101415), and context-duplication bugs (#101644) indicate session persistence is the most fragile layer.
- **MCP tooling instability**: god-file size (#78642), boolean-schema crashes (#101669), and subprocess leaks (#81880) suggest the MCP integration needs architectural hardening.
- **Desktop on Windows** has recurring issues: browser timeout (#96731, fix in progress), update watchdog (#101850), and config write bugs (#101786).
- **Voice features** are in high demand but currently fragmented; users want a single cohesive experience across TUI, browser, and remote gateway.
- **Configuration ergonomics**: `hermes config set` stringifying lists (#76457) and ACP token metering (#101817) erode trust in basic tooling.

**Satisfaction signals:**
- Group Chat continuity work (#97681 / #98307) is well-received and aligns with multi-device usage patterns.
- The RFC-driven voice architecture (#77111 → #101808) shows the project is listening to community design input rather than merging conflicting PRs.
- Performance work on desktop transcript loading (#100303) addresses a tangible pain point.

## 8. Backlog Watch

| Issue | Reason for Watch |
|---|---|
| [#78642](https://github.com/NousResearch/hermes-agent/issues/78642) | 7,230-line MCP god file — repo policy mandates decomposition, no PR yet |
| [#81880](https://github.com/NousResearch/hermes-agent/issues/81880) | MCP stdio OOM on macOS — production impact, no fix PR |
| [#101800](https://github.com/NousResearch/hermes-agent/issues/101800) | Rate-limit sentinel unreachable — P1, causes crashloops, no fix PR |
| [#101669](https://github.com/NousResearch/hermes-agent/issues/101669) | MCP boolean schema disables entire server — P1, no fix PR |
| [#101644](https://github.com/NousResearch/hermes-agent/issues/101644) | v0.21.0 conversation history duplication — P2 regression, no fix PR |
| [#20140](https://github.com/NousResearch/hermes-agent/issues/20140) | Cron `send_message` opt-in — known gap, no active PR |
| [#57547](https://github.com/NousResearch/hermes-agent/issues/57547) | Custom endpoint API key in `config.yaml` — security concern, no fix PR |

---

**Project health assessment:** Hermes Agent is in a high-activity phase with strong contributor engagement. The most pressing risks are session-state reliability and MCP stability. The voice architecture RFC is a positive signal of mature community governance. The lack of recent releases suggests the team is consolidating fixes before the next tag.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-03

## 1. Today's Overview

PicoClaw (sipeed/picoclaw) shows low but steady activity as of September 3, 2026. One issue was updated and one pull request was merged/closed in the last 24 hours, with no new releases deployed. The project remains focused on multi-channel AI agent integration, with recent efforts centering on QQ Channel support — both enhancements and troubleshooting. Overall project health appears moderate: development momentum is present but incremental, and a notable bug affecting QQ Channel connectivity warrants close attention from maintainers.

## 2. Releases

No new releases were published in the last 24 hours. The project has no latest release data available for this digest window.

## 3. Project Progress

**Merged PR #1349 — feat(qq): support parsing and replying to more attachment types** ([Link](https://github.com/sipeed/picoclaw/pull/1349))

- Closed/merged on 2026-09-02 after being open since 2026-03-11.
- **Author:** aishannon
- **Changes advanced:**
  - Parsing of QQ Channel emoji structures.
  - Handling of incoming voice, image, video, and file messages from QQ Channel.
  - Reply support with local voice, image, video, and file attachments (with pre-upload).
  - Fallback reply strategy: prioritizes Markdown messages, degrades to alternative formats on failure.
- This PR significantly expands QQ Channel's media handling capabilities, addressing a previously limited attachment support gap.

## 4. Community Hot Topics

**Issue #3349 — [BUG] QQ频道无法正常使用** ([Link](https://github.com/sipeed/picoclaw/issues/3349))

- **Author:** bxwl5 | **Opened:** 2026-08-30 | **Last updated:** 2026-09-02 | **Comments:** 2 | **Reactions:** 0
- **Summary:** QQ Channel is non-functional across both Docker and Linux x86 deployments. The gateway logs report an authentication error: `code:401, message: "请求头Authorization参数格式错误"` (error code 11241 / err_code 40011005). This indicates the QQ Channel integration is sending malformed or expired Authorization headers, causing the QQ API to reject requests.
- **Underlying need:** Users are actively relying on PicoClaw for QQ Channel as a messaging surface for AI agents. The bug blocks a key market (Chinese QQ ecosystem), and the 401 error suggests either a credential rotation issue, a header format regression, or an API change from QQ's side that PicoClaw hasn't adapted to.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **High** | [#3349](https://github.com/sipeed/picoclaw/issues/3349) | QQ Channel 401 authorization failure — gateway cannot authenticate with QQ API, affecting both Docker and x86 Linux builds | None yet |

- **Assessment:** The #3349 bug is the most critical open issue. It impacts a core channel (QQ) and affects all deployment variants. No fix PR has been opened as of this digest date. Maintainer triage is recommended.

## 6. Feature Requests & Roadmap Signals

- **PR #1349** (now closed/merged) demonstrates that the project is actively investing in **QQ Channel media richness** — emoji, voice, image, video, and file support. This signals that the roadmap prioritizes expanding QQ as a first-class channel, not just text-based messaging.
- The fallback mechanism (Markdown → alternative formats) suggests the team is building **resilience into channel adapters**, a pattern likely to appear in future channel additions.
- No new feature request issues were flagged today, but the QQ auth bug (#3349) implicitly signals demand for **stable, production-grade QQ integration**.

## 7. User Feedback Summary

- **Pain point:** QQ Channel is currently broken for users on both major deployment paths (Docker and Linux x86). The 401 error is blocking adoption and daily use for Chinese-speaking users who rely on QQ as a primary messaging platform.
- **Satisfaction signal:** The merge of PR #1349 shows the community appreciates expanded QQ media support — users who tested voice/image/video handling likely provided the impetus.
- **Overall sentiment:** Users are engaged but frustrated by the auth regression. The project has strong momentum on feature expansion (attachments, emojis) but is currently let down on reliability for a high-visibility channel.

## 8. Backlog Watch

| Item | Age | Priority | Notes |
|------|-----|----------|-------|
| [#3349](https://github.com/sipeed/picoclaw/issues/3349) | ~4 days | **Critical** | QQ Channel auth bug — no fix PR yet. Requires maintainer investigation into header formatting or QQ API changes. |
| [#1349](https://github.com/sipeed/picoclaw/pull/1349) | ~6 months | Resolved | Long-lived PR finally merged. Suggests the project may have a slow review cycle for community contributions. |

---

**Project Health Score: Moderate** — Feature development is active (QQ media support merged), but a high-severity bug in a core channel remains unresolved with no fix in progress. Maintainer attention on #3349 is the top priority.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-03

## 1. Today's Overview

NanoClaw shows active but focused development today, with 21 PRs updated and only 2 issues touched in the last 24 hours. The project is in a bug-fix and hardening phase rather than a feature-launch cycle — no new releases were published, and the majority of PR activity centers on supply-chain security, provider contract enforcement, and delivery-channel stability. A small number of regressions and usability gaps are being actively addressed by contributors, suggesting healthy community momentum alongside core-team refactoring work.

## 2. Releases

No new releases were published in the last 24 hours. The project remains on its current version.

## 3. Project Progress

**Merged / Closed PRs today:**

- **[PR #2973](https://github.com/nanocoai/nanoclaw/pull/2973)** — *fix(supply-chain): activate the minimumReleaseAge gate* — Moved `minimumReleaseAge: 4320` from under the `pnpm:` key to the top level of `pnpm-workspace.yaml`, finally enabling the 3-day package-retention policy that `CLAUDE.md` had already described but was not enforcing. This was a long-standing security-gap fix that sat open since July 7 before landing today.
- **[PR #3672](https://github.com/nanocoai/nanoclaw/pull/3672)** — *test(skill-directives): expect the slack-raw-text files add-slack copies* — Closed test-update PR ensuring skill-directive tests account for slack-raw-text file copies.

**Key open work advancing today:**
- Provider contract refactoring (PRs #3584, #3585, #3586, #3588, #3591, #3592, #3593) continues to bind Codex, OpenCode, and other providers to a core-owned canonical contract.
- Delivery stability improvements (PRs #3702, #3703) address queue-scheduling and adapter-disconnect behavior.
- Container/MCP networking fix (PR #3597) bypasses the gateway proxy for host-local addresses.

## 4. Community Hot Topics

**Most discussed / longest-standing open items:**

| Item | Type | Author | Days Open | Summary |
|------|------|--------|-----------|---------|
| [Issue #3529](https://github.com/nanocoai/nanoclaw/issues/3529) | Bug | glifocat | 9 | Skill refresh overwrites local adapters; no opt-out |
| [PR #3492](https://github.com/nanocoai/nanoclaw/pull/3492) | Fix | amit-shafnir | 11 | Re-lands the minimumReleaseAge gate with regression test |
| [PR #3427](https://github.com/nanocoai/nanoclaw/pull/3427) | Fix | glifocat | 13 | `send_card` drops callback actions silently |
| [PR #3113](https://github.com/nanocoai/nanoclaw/pull/3113) | Fix | CrAzyScreamx | 13 | WhatsApp inbound media staging |
| [Issue #3701](https://github.com/nanocoai/nanoclaw/issues/3701) | Feature | davekim917 | <1 | Gateway-declared credential lane in `validateSpec` |

**Underlying needs:**
- **Local adapter preservation** (#3529): Power users with custom adapters in their workspace tree need the update mechanism to distinguish skill-provided channels from user-managed ones, with an opt-out path. This reflects a growing base of fork/customization users.
- **Credential injection at scale** (#3701): A maintainer running 24 agent groups on a gateway model is pushing the existing `contributedEnv` placeholder-swap pattern to its limits and seeking a first-class credential-lane abstraction in validation. This signals demand for multi-tenant, per-group credential management.
- **Provider contract unification**: The cluster of PRs from zvi-fried (#3584–#3593) indicates a coordinated push to replace ad-hoc provider logic with a typed, core-owned contract — a structural improvement driven by internal core-team initiative.

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| **High** | [PR #3703](https://github.com/nanocoai/nanoclaw/pull/3703) | Delivery wastes all 3 retry attempts on an adapter that reports `isConnected() = false`; throws during mid-reconnect instead of skipping | Open — authored today by santisiri |
| **High** | [PR #3702](https://github.com/nanocoai/nanoclaw/pull/3702) | `ncl tasks run` inserts a due row but never feeds the reconcile queue, causing up to 60 s delay before the run starts | Open — authored today by santisiri |
| **Medium** | [PR #3596](https://github.com/nanocoai/nanoclaw/pull/3596) | Teams colon-bearing user IDs are not namespaced, breaking card-click auth and sender resolution | Open |
| **Medium** | [PR #3674](https://github.com/nanocoai/nanoclaw/pull/3674) | Outbound files lack MIME type, causing Teams to reject them | Open |
| **Medium** | [Issue #3529](https://github.com/nanocoai/nanoclaw/issues/3529) | Update skill refresh incorrectly identifies local-tree adapters as skill-imported and overwrites them | No fix PR yet |
| **Medium** | [PR #3427](https://github.com/nanocoai/nanoclaw/pull/3427) | `send_card` tool promises callback buttons that the Chat SDK bridge silently drops | Open |
| **Low** | [PR #3680](https://github.com/nanocoai/nanoclaw/pull/3680) | Allowlisted-extra mount bypass in `validateSpec` — minor security hardening | Open |
| **Low** | [PR #3597](https://github.com/nanocoai/nanoclaw/pull/3597) | HTTP MCP servers on `host.docker.internal` unreachable behind gateway proxy | Open |

No crash reports or regressions from the latest release were raised in the last 24 hours.

## 6. Feature Requests & Roadmap Signals

- **[Issue #3701](https://github.com/nanocoai/nanoclaw/issues/3701)** — Gateway-declared credential lane in `validateSpec`. A production operator running multi-tenant agent groups is requesting first-class support for per-group credential injection at the proxy boundary. This aligns with the broader provider-contract hardening effort and is a strong signal that credential scoping will be a roadmap priority.
- **[PR #3592](https://github.com/nanocoai/nanoclaw/pull/3592)** — Core-owned `speed` inference property (gating, CLI, provider vocabulary). Already in review; likely to land in the next release as part of the provider contract refactor.
- **[PR #3573](https://github.com/nanocoai/nanoclaw/pull/3573)** — AIML API integration request. A community contribution proposing a new channel/integration skill.
- **[PR #3113](https://github.com/nanocoai/nanoclaw/pull/3113)** — WhatsApp inbound media staging fix, open since July. If merged, would close a long-standing media-handling gap.

**Prediction:** The next release will likely include the provider contract refactors (#3584–#3593), the `speed` property (#3592), and the delivery-queue fix (#3702). Credential-lane support (#3701) is less certain for the immediate next release but is a clear directional signal.

## 7. User Feedback Summary

- **Pain point — local adapter loss on update** (#3529): Users who maintain custom adapters in their workspace tree report that the update's skill-refresh logic treats every import in `src/channels/index.ts` as skill-provided, causing validation failures or silent overwrites. There is currently no opt-out. This is a friction point for power users and fork maintainers.
- **Pain point — delayed task execution** (#3702): `ncl tasks run` now has a guaranteed fix PR (today), confirming that the 60-second resync delay was a real user-visible bug, not just a theoretical gap.
- **Pain point — silent card action drops** (#3427): Agents are told a button action succeeded when the bridge actually dropped it. This creates confusing agent behavior in production.
- **Satisfaction signal**: The active contributor base (santisiri, orgads, zvi-fried, glifocat) is responding quickly to bugs with well-scoped fix PRs, and the core-team is executing a coherent provider-unification refactor. The project appears to have strong maintainer responsiveness relative to its issue volume.

## 8. Backlog Watch

| Item | Type | Days Open | Risk |
|------|------|-----------|------|
| [Issue #3529](https://github.com/nanocoai/nanoclaw/issues/3529) | Bug | 9 | Users with custom adapters risk data loss on update; no fix PR yet |
| [PR #3492](https://github.com/nanocoai/nanoclaw/pull/3492) | Fix | 11 | Re-land of supply-chain gate with test; blocks #2973's full benefit |
| [PR #3427](https://github.com/nanocoai/nanoclaw/pull/3427) | Fix | 13 | `send_card` callback drop affects agent reliability; no merge yet |
| [PR #3113](https://github.com/nanocoai/nanoclaw/pull/3113) | Fix | 13 | WhatsApp media staging; blocks media-receiving workflows |
| [PR #3596](https://github.com/nanocoai/nanoclaw/pull/3596) | Fix | 6 | Teams namespace bug; affects card interaction for certain user IDs |
| [PR #3597](https://github.com/nanocoai/nanoclaw/pull/3597) | Fix | 6 | MCP host-local networking; blocks local MCP server usage behind gateway |
| [Issue #3701](https://github.com/nanocoai/nanoclaw/issues/3701) | Feature | <1 | Multi-tenant credential scoping; no PR yet but high-value for power users |

**Maintainer attention needed:** Issue #3529 is the most concerning backlog item — it impacts users who rely on custom adapters and has no fix PR after 9 days. The core-team should prioritize either a patch or a documented opt-out mechanism.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-03

## 1. Today's Overview

IronClaw is experiencing high development velocity with 36 issues and PRs updated in the last 24 hours (10 issues, 26 PRs), 6 of which remain open and 6 issues closed. The project is simultaneously advancing three major workstreams: TypeScript hygiene across the WebUI v2 frontend (a large-scale debt-elimination effort), message delivery correctness in channel integrations (Slack/Telegram reply fixes), and CI/build performance optimization. No new releases were published today. The project appears healthy with active contributor participation, though the volume of open TypeScript-related PRs suggests a significant but disciplined cleanup effort is underway.

**Activity Assessment: High** — 26 PRs and 10 issues in 24h is strong output, particularly with multiple XL-sized refactor PRs in review simultaneously.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

### Closed/Merged Today
- **[#8018](https://github.com/nearai/ironclaw/issues/8018)** — Replaced native SettingsField `<input>`/`<select>` controls with shared `Input` and `SelectMenu` components.
- **[#8020](https://github.com/nearai/ironclaw/issues/8020)** — Migrated Workspace and Logs filters to the shared `SearchField` component, including a new compact toolbar size.
- **[#8019](https://github.com/nearai/ironclaw/issues/8019)** — Migrated Automations status banners to the shared `InlineNotice` component.
- **[#8017](https://github.com/nearai/ironclaw/issues/8017)** — Adopted shared form and feedback components in Extension Configure flow (replaced native password input and local banners).
- **[#8051](https://github.com/nearai/ironclaw/pull/8051)** — Fixed reply behavior so Slack/Telegram only emit the **current** model call's text, not the cumulative narration of all prior calls.
- **[#8045](https://github.com/nearai/ironclaw/pull/8045)** — Fixed CLI smoke-test flake by requiring an actual TCP connection for readiness instead of a banner-only wait.
- **[#8050](https://github.com/nearai/ironclaw/pull/8050)** — Major CI optimization: stopped cold-compiling every Reborn lane on every PR/queue run, introducing stable hermetic Cargo home, push-only shared caches, and a warm in-place mutation gate. This eliminates the duplicate full-closure compilations that were the heaviest CI bottleneck.
- **[#8006](https://github.com/nearai/ironclaw/pull/8006)** — Shipped durable progressive replies and native Slack Agent UI, introducing a provider-neutral `ReplyDocument` contract.
- **[#8042](https://github.com/nearai/ironclaw/pull/8042)** — Fixed merge-queue flake where serve smoke tests were killing the server prematurely; now binds before banner and judges only named mutants.

### Active Workstreams
- **WebUI v2 TypeScript Elimination** — Five coordinated PRs (#8032–#8039, #8040) targeting 170 files and ~61,800 lines of `@ts-nocheck` debt. Includes typed API boundaries, test infrastructure typing, and a CI ratchet to prevent new suppressions.
- **WebUI Session-Event Transport** — PR [#8010](https://github.com/nearai/ironclaw/pull/8010) implements unified typed stream contracts and run-completion notifications with durable notices.
- **Subagent Approval Gates** — PR [#8046](https://github.com/nearai/ironclaw/pull/8046) addresses the invisibility of blocked subagent runs to their parent owners.
- **Claude Model Cache Support** — PR [#8044](https://github.com/nearai/ironclaw/pull/8044) extends prompt cache support to new Claude families via denylist approach and sends `prompt_cache_key` on OpenAI Responses.
- **Streaming Performance** — PR [#8043](https://github.com/nearai/ironclaw/pull/8043) coalesces streamed text updates to eliminate O(N·k) re-sanitization on every delta.
- **Codebase Knowledge Graph** — PR [#7988](https://github.com/nearai/ironclaw/pull/7988) refreshes the bootstrap snapshot from the default branch.

---

## 4. Community Hot Topics

### Most Discussed / Impactful

1. **[PR #8010](https://github.com/nearai/ironclaw/pull/8010) — Session-event transport unification and web-app run-completion notifications**
   - Comprehensive redesign of the WebUI event layer with typed stream contracts and multiplexed SSE. Signals a need for real-time reliability as the agent system scales.

2. **[PR #8038](https://github.com/nearai/ironclaw/pull/8038) — Type and validate frontend API boundaries**
   - Introduces runtime decoders for all API response types (device-link, pairing, notifications, projects, settings, workspace). Addresses the pain of silent runtime shape mismatches between frontend and backend.

3. **[PR #8051](https://github.com/nearai/ironclaw/pull/8051) — Fix reply: the answer is the current model call's text**
   - Directly addresses a user-visible bug where Slack/Telegram replies were concatenating all prior model narration. High user impact; live QA confirmed the regression.

4. **[Issue #8041](https://github.com/nearai/ironclaw/issues/8041) — Wrong FailureKind sends model into unrecoverable state**
   - A semantic bug where `NativeMemoryService::read` reports a missing document as `InputEncode` (fixable input) rather than a domain failure. The model interprets this incorrectly and enters a loop. ([PR #7985](https://github.com/nearai/ironclaw/pull/7985) is the corresponding fix.)

5. **[PR #8050](https://github.com/nearai/ironclaw/pull/8050) — CI Reborn lane cold-compile optimization**
   - Community and maintainer interest in CI speed; this PR eliminates the heaviest CI bottleneck by deduplicating the full dependency closure compilation.

**Underlying Needs:** The project is maturing from a prototype to a production system. The dominant themes are **type safety** (eliminating `@ts-nocheck`), **reliability** (fixing reply corruption, CI flake, model recovery loops), and **observability** (run-completion notifications, durable inboxes).

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|----------|------|-------------|------------|
| **High** | [Issue #8041](https://github.com/nearai/ironclaw/issues/8041) / [PR #7985](https://github.com/nearai/ironclaw/pull/7985) | Wrong `FailureKind` for missing documents causes model to enter unrecoverable retry loop | PR #7985 open — maps to `InputEncode` incorrectly; fix reclassifies as domain failure |
| **Medium** | [PR #8051](https://github.com/nearai/ironclaw/pull/8051) (merged) | Slack/Telegram progressive replies concatenated all model call text instead of only the current call's answer | Fixed — merged |
| **Medium** | [PR #8042](https://github.com/nearai/ironclaw/pull/8042) (merged) | Serve smoke tests were flakily killing the server during merge-queue runs | Fixed — merged; binds before banner, stabilizes stderr lifecycle |
| **Medium** | [PR #8046](https://github.com/nearai/ironclaw/pull/8046) | Blocked subagent runs (approval/credential gates) are invisible to the parent owner | Open — no fix merged yet |
| **Low** | [PR #8045](https://github.com/nearai/ironclaw/pull/8045) (merged) | CLI smoke-test readiness probe relied on banner text instead of TCP connection | Fixed — merged; now requires actual loopback connection |

---

## 6. Feature Requests & Roadmap Signals

- **Durable progressive replies** — PR [#8006](https://github.com/nearai/ironclaw/pull/8006) shipped a provider-neutral `ReplyDocument` contract. This signals the roadmap toward unified, durable cross-channel messaging with native UI support.
- **Real-time run-completion notifications** — PR [#8010](https://github.com/nearai/ironclaw/pull/8010) implements typed SSE streams and durable browser notifications. Expect this to become a core feature for agent monitoring.
- **Subagent observability** — PR [#8046](https://github.com/nearai/ironclaw/pull/8046) (R3 slice 3a) signals an active roadmap for multi-agent coordination with visible approval gates.
- **Claude family cache support** — PR [#8044](https://github.com/nearai/ironclaw/pull/8044) extends prompt caching to newer Claude families. Likely to land in the next minor release as Anthropic ships new model variants.
- **WebUI v2 TypeScript complete** — The coordinated #8032–#8040 PRs represent a major quality milestone. Expect the WebUI v2 to ship with full type coverage as a headline improvement.

---

## 7. User Feedback Summary

- **Slack/Telegram reply corruption** is the most pressing user-visible pain point. Users received concatenated narration instead of clean answers, directly degrading the agent experience. ([PR #8051](https://github.com/nearai/ironclaw/pull/8051) — fixed)
- **Model recovery loops** caused by incorrect `FailureKind` classification are a silent but severe issue. When a document is missing, the model is told "your input was wrong" and retries pointlessly rather than adapting. ([Issue #8041](https://github.com/nearai/ironclaw/issues/8041), [PR #7985](https://github.com/nearai/ironclaw/pull/7985))
- **CI flakiness** was ejecting valid PRs from the merge queue 5 out of 6 times, eroding contributor confidence. The cold-compile deduplication fix should resolve this. ([PR #8050](https://github.com/nearai/ironclaw/pull/8050), [#8042](https://github.com/nearai/ironclaw/pull/8042))
- **Blocked subagent visibility** — users cannot see when a child agent is waiting on approval, creating confusion about agent stalls. ([PR #8046](https://github.com/nearai/ironclaw/pull/8046))
- **TypeScript debt** in WebUI v2 (170 files, ~62K lines) is a developer-experience pain point that the current cleanup effort directly addresses.

---

## 8. Backlog Watch

| Item | Age | Priority | Notes |
|------|-----|----------|-------|
| [PR #7985](https://github.com/nearai/ironclaw/pull/7985) — Fix missing-document FailureKind | ~6 days | **High** | Open; fixes a model recovery loop. Linked to Issue #8041. |
| [PR #8046](https://github.com/nearai/ironclaw/pull/8046) — Subagent approval gate inbox | ~1 day | **Medium** | Open; enables parent visibility into blocked children. |
| [PR #8010](https://github.com/nearai/ironclaw/pull/8010) — Session-event transport unification | ~3 days | **Medium** | Open; large infra change with design doc. |
| [PR #8038](https://github.com/nearai/ironclaw/pull/8038) — Type frontend API boundaries | ~1 day | **Medium** | Open; part of coordinated TypeScript cleanup. |
| [PR #8039](https://github.com/nearai/ironclaw/pull/8039) — Type production components/hooks | ~1 day | **Medium** | Open; XL-sized, core to TypeScript elimination. |
| [PR #8040](https://github.com/nearai/ironclaw/pull/8040) — Type test infrastructure | ~1 day | **Low** | Open; 94 test files to clean up. |
| [PR #7988](https://github.com/nearai/ironclaw/pull/7988) — Refresh codebase knowledge graph | ~5 days | **Low** | Routine CI-generated refresh, pending merge. |

**Maintainer Attention Needed:** PR #7985 (bug fix with user impact) and PR #8046 (feature gap in multi-agent observability) are the most impactful open PRs. The coordinated TypeScript PRs (#8037–#8040) are large but mechanical; expect them to land as a batch once review cycles complete.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-09-03

## 1. Today's Overview

LobsterAI shows moderate development activity with 8 issues and 9 pull requests updated in the past 24 hours. Six issues were closed (all marked stale), while two critical concurrency bugs remain open. Two PRs were merged today: a Windows renderer guide fix and a revert of the in-app browser feature from the current release. No new releases were published. The project appears to be in a stabilization phase, with maintainers addressing concurrency regressions and feature rollbacks rather than shipping new capabilities.

---

## 2. Releases

**No new releases** published in the last 24 hours.

Notable revert: **PR #2597** removed the in-app browser feature (originally introduced in #2574) from the `release/2026.8.31` line, deferring it to a later release window. Users on the 2026.8.31 build will not have the in-app browser; the original feature branch remains available for future reapplication.

---

## 3. Project Progress

### Merged / Closed Today
| PR | Area | Summary |
|----|------|---------|
| [#2598](https://github.com/netease-youdao/LobsterAI/pull/2598) | renderer | Fixed Windows installation/user guide documentation |
| [#2597](https://github.com/netease-youdao/LobsterAI/pull/2597) | browser (revert) | Reverted in-app browser from 2026.8.31 release; preserved feature branch for future |

### Notable Open PRs Advancing
- **[PR #1090](https://github.com/netease-youdao/LobsterAI/pull/1090)** — Adds per-session execution serialization to `CoworkRunner` to prevent concurrent `startSession`/`continueSession` calls from corrupting streamed messages.
- **[PR #1100](https://github.com/netease-youdao/LobsterAI/pull/1100)** — Introduces a per-conversation async mutex in `IMCoworkHandler` to eliminate duplicate cowork session creation under concurrent IM message arrival.
- **[PR #1101](https://github.com/netease-youdao/LobsterAI/pull/1101)** — Fixes a race condition where switching AI providers (e.g., Anthropic → DeepSeek) and immediately sending a message causes "model service call failed" errors due to fire-and-forget gateway restarts.
- **[PR #1125](https://github.com/netease-youdao/LobsterAI/pull/1125)** — Extends session search to full message content with keyword highlighting and intelligent摘要 previews.
- **[PR #2590](https://github.com/netease-youdao/LobsterAI/pull/2590)** — Hardens MCP stdio command parsing and external URL handling against shell injection and unvalidated protocol schemes.
- **[PR #1103](https://github.com/netease-youdao/LobsterAI/pull/1103)** — Adds a Docker sandbox readiness probe so users can verify tool-execution capability without changing execution-mode settings.

---

## 4. Community Hot Topics

### Most Discussed Open Issues
1. **[Issue #1099](https://github.com/netease-youdao/LobsterAI/issues/1099)** — IM concurrent message handling causing duplicate sessions and lost responses *(1 comment, stale)*
   - *Underlying need:* Users rely on IM integration for continuous multi-turn workflows; concurrent message bursts (common in team channels) expose a critical concurrency bug. Two companion PRs (#1090, #1100) are directly addressing this.

2. **[Issue #1096](https://github.com/netease-youdao/LobsterAI/issues/1096)** — Markdown-to-PDF conversion leaves orphan browser tabs and injects a membership ad box *(1 comment, stale)*
   - *Underlying need:* Users exporting documentation expect clean, headless output. The current reliance on an online conversion service degrades UX with lingering tabs and unwanted UI chrome.

### Recently Closed Issues (Stale)
- [#1569](https://github.com/netease-youdao/LobsterAI/issues/1569) — Input submitted but no response generated or displayed
- [#1561](https://github.com/netease-youdao/LobsterAI/issues/1561) — Model cannot access uploaded files (regression from earlier behavior where files were placed in project directory)
- [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) — All inputs return identical responses regardless of content
- [#1551](https://github.com/netease-youdao/LobsterAI/issues/1551) — Gateway restarts repeatedly when network environment changes
- [#1563](https://github.com/netease-youdao/LobsterAI/issues/1563) — Typographical errors in data package service terms
- [#1567](https://github.com/netease-youdao/LobsterAI/issues/1567) — Request for quick-action buttons (stop conversation, compress context) and `help` command for recovery

---

## 5. Bugs & Stability

### Confirmed / Open Bugs
| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **High** | [#1099](https://github.com/netease-youdao/LobsterAI/issues/1099) | IM concurrent message handling causes duplicate cowork sessions and message loss | [#1100](https://github.com/netease-youdao/LobsterAI/pull/1100) (open) |
| **High** | — | `CoworkRunner` concurrent `startSession`/`continueSession` corrupts streamed output | [#1090](https://github.com/netease-youdao/LobsterAI/pull/1090) (open) |
| **Medium** | — | Cross-provider model switch + immediate message → "model service call failed" race condition | [#1101](https://github.com/netease-youdao/LobsterAI/pull/1101) (open) |
| **Medium** | [#1096](https://github.com/netease-youdao/LobsterAI/issues/1096) | md-to-pdf leaves orphan browser tabs and injects membership UI | — |
| **Low** | [#1551](https://github.com/netease-youdao/LobsterAI/issues/1551) | Gateway restart loop on network change (closed as stale) | — |
| **Low** | [#1561](https://github.com/netease-youdao/LobsterAI/issues/1561) | File upload not recognized by model — regression (closed as stale) | — |
| **Low** | [#1566](https://github.com/netease-youdao/LobsterAI/issues/1566) | Uniform response regardless of input — possible crash/cycle (closed as stale) | — |

**Stability Assessment:** Two high-severity concurrency bugs in the IM and Cowork runners remain open with active PRs. The closed "stale" issues suggest maintainers may have deprioritized or been unable to reproduce several user-reported regressions from the April 2026 timeframe, which is a concern for long-term reliability.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Next Release |
|---------|--------|----------------------------|
| Full-text session search with keyword highlighting | [PR #1125](https://github.com/netease-youdao/LobsterAI/pull/1125) | **High** — well-scoped, directly improves usability for power users with large session histories |
| Docker sandbox readiness probe | [PR #1103](https://github.com/netease-youdao/LobsterAI/pull/1103) | **High** — read-only diagnostic, low risk, addresses deployability concerns |
| Quick-action buttons (stop conversation, compress context) + `help` command | [Issue #1567](https://github.com/netease-youdao/LobsterAI/issues/1567) | **Medium** — useful but requires UI work; may follow the concurrency fixes |
| In-app browser | [Reverted in #2597](https://github.com/netease-youdao/LobsterAI/pull/2597) | **Deferred** — explicitly moved to a future release window; branch preserved |
| MCP security hardening (stdio command validation, URL allowlisting) | [PR #2590](https://github.com/netease-youdao/LobsterAI/pull/2590) | **High** — security-focused, low functional change, likely to be merged soon |

---

## 7. User Feedback Summary

### Pain Points
- **Concurrent IM/Cowork failures** are the most impactful issue: users lose messages and create duplicate sessions when multiple IM messages arrive rapidly — a dealbreaker for team workflows.
- **File upload regression** ([#1561](https://github.com/netease-youdao/LobsterAI/issues/1561)): previously, uploaded files were placed in the project directory and the model could reference them; the new behavior breaks this flow entirely.
- **Uniform response bug** ([#1566](https://github.com/netease-youdao/LobsterAI/issues/1566)): model returns identical content regardless of input, suggesting an internal error or context pipeline failure.
- **Gateway instability on network changes** ([#1551](https://github.com/netease-youdao/LobsterAI/issues/1551)): mobile or intermittent-network users experience repeated restarts.
- **Poor error recovery UX** ([#1567](https://github.com/netease-youdao/LobsterAI/issues/1567)): no built-in way to stop a stuck conversation or compress context; users must restart the app.

### Satisfaction Signals
- No positive reactions (👍) on any issues, and all closed issues are marked stale — suggesting either resolution without acknowledgment or abandonment.
- The revert of the in-app browser ([#2597](https://github.com/netease-youdao/LobsterAI/pull/2597)) indicates the feature was not production-ready, which may disappoint users who had configured workflows around it.

---

## 8. Backlog Watch

| Priority | Item | Age | Risk |
|----------|------|-----|------|
| **Critical** | [Issue #1099](https://github.com/netease-youdao/LobsterAI/issues/1099) + [PR #1100](https://github.com/netease-youdao/LobsterAI/pull/1100) | Open since 2026-03-31 (~5 months) | Concurrency bug affecting IM multi-message workflows; fix PR is open but unmerged |
| **Critical** | [PR #1090](https://github.com/netease-youdao/LobsterAI/pull/1090) | Open since 2026-03-31 (~5 months) | Same-root-cause bug in CoworkRunner; unmerged for 5 months |
| **High** | [PR #1101](https://github.com/netease-youdao/LobsterAI/pull/1101) | Open since 2026-03-31 (~5 months) | Provider-switch race condition; unmerged |
| **Medium** | [Issue #1096](https://github.com/netease-youdao/LobsterAI/issues/1096) | Open since 2026-03-31 (~5 months) | md-to-pdf UX degradation; no fix PR |
| **Medium** | [Issue #1567](https://github.com/netease-youdao/LobsterAI/issues/1567) | Stale since 2026-09-02 | Quick-recovery UX feature; no PR yet |
| **Low** | Stale closed issues (#1569, #1561, #1566, #1551) | Created 2026-04-08, closed 2026-09-02 | Multiple regressions from April build may be unresolved for affected users |

**Overall Project Health:** 🟡 **Caution** — The project has two critical concurrency PRs open since March 2026 without merge, and five high-impact user issues closed as stale without visible fixes. Active development is present (6 open PRs across cowork, security, Docker, and search), but the backlog of long-open items and stale closures warrants maintainer attention to restore user confidence.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-09-03

---

## 1. Today's Overview

Moltis is in an active development phase, with three patch-level releases pushed yesterday alone (20260902.01 → 20260902.03), indicating rapid iteration and likely hotfix turnover. Two open issues were filed yesterday, both authored by contributor GTanger, and three PRs remain open for review — none yet merged today. Activity is concentrated around hook lifecycle completeness and reasoning effort configuration. Overall project velocity is **high**, though the lack of merged PRs or closed issues this cycle warrants monitoring.

---

## 2. Releases

| Version | Date | Notes |
|---|---|---|
| [20260902.03](https://github.com/moltis-org/moltis/releases) | 2026-09-02 | Patch release; no detailed changelog provided |
| [20260902.02](https://github.com/moltis-org/moltis/releases) | 2026-09-02 | Patch release; no detailed changelog provided |
| [20260902.01](https://github.com/moltis-org/moltis/releases) | 2026-09-02 | Patch release; baseline for today's issues |

**Assessment:** Three consecutive patch releases in a single day suggest the team is stabilizing a recent change set. No breaking changes or migration notes are documented. Users on `20260902.01` are advised to upgrade to `.03` to stay current.

---

## 3. Project Progress

**No PRs merged or issues closed today.** Three open PRs are advancing:

- **[PR #1257](https://github.com/moltis-org/moltis/pull/1257)** — *fix(hooks): complete lifecycle dispatch* — Addresses the core hook gap: dispatches `AgentEnd`, `MessageSending`, and `MessageSent` events for native non-streaming flows, and introduces an optional `tool_call_id` to correlate `BeforeToolCall`/`AfterToolCall`/`ToolResultPersist` payloads end-to-end while preserving backward-compatible JSON.
- **[PR #1253](https://github.com/moltis-org/moltis/pull/1253)** — *feat(reasoning): add max effort level* — Adds `max` to the `ReasoningEffort` schema, `@reasoning-max` model suffix parsing, and forwards it through the OpenAI Codex Responses API with provider clamping. Exposed in UI selector and translations.
- **[PR #1256](https://github.com/moltis-org/moltis/pull/1256)** — *chore(deps-dev): bump browserslist from 4.28.2 to 4.28.8* — Routine Dependabot update in `/crates/web/ui`.

---

## 4. Community Hot Topics

### 🔥 Most Discussed: PR #1257 — Complete Hook Lifecycle Dispatch
**[PR #1257](https://github.com/moltis-org/moltis/pull/1257)** is the most significant item today. It directly resolves **Issue #1255** and partially addresses **Issue #1254**, making it the linchpin of the current development cycle.

- **Issue #1255** ([link](https://github.com/moltis-org/moltis/issues/1255)) — Hooks `AgentEnd`, `MessageSending`, and `MessageSent` are declared in the codebase but never dispatched at runtime. This is a **functional gap** for users relying on shell hooks for observability and automation.
- **Issue #1254** ([link](https://github.com/moltis-org/moltis/issues/1254)) — `BeforeToolCall` and `AfterToolCall` hooks lack a shared tool call ID, preventing end-to-end correlation in process-per-event hook models.

**Underlying need:** Users building agent observability pipelines and event-driven automation require reliable, complete hook coverage. The absence of lifecycle-end hooks and tool-call correlation IDs breaks traceability — a core requirement for production-grade AI agent systems.

---

## 5. Bugs & Stability

| Severity | Issue | PR Fix | Status |
|---|---|---|---|
| **Medium** | [#1255](https://github.com/moltis-org/moltis/issues/1255) — Declared hooks never dispatched (`AgentEnd`, `MessageSending`, `MessageSent`) | [PR #1257](https://github.com/moltis-org/moltis/pull/1257) | Open |
| **Low** | [#1254](https://github.com/moltis-org/moltis/issues/1254) — Missing stable `tool_call_id` in hook payloads | [PR #1257](https://github.com/moltis-org/moltis/pull/1257) | Open |

**Assessment:** No crashes or regressions reported. The bugs are **completeness gaps** rather than stability issues. PR #1257 is a direct fix for both. No other bug reports surfaced today.

---

## 6. Feature Requests & Roadmap Signals

| Item | Link | Prediction |
|---|---|---|
| **Max reasoning effort level** ([PR #1253](https://github.com/moltis-org/moltis/pull/1253)) | Adds `max` tier to `ReasoningEffort`, with UI and translation support | Likely included in the **next minor release** — the PR is well-scoped and already implements provider clamping for non-compliant backends |
| **Stable tool call ID in hooks** ([Issue #1254](https://github.com/moltis-org/moltis/issues/1254)) | Correlate tool call events end-to-end | Likely bundled with the **next patch or minor release** alongside PR #1257 |
| **Complete hook lifecycle dispatch** ([Issue #1255](https://github.com/moltis-org/moltis/issues/1255)) | Ensure all declared hooks fire | Same as above — tied to PR #1257 |

**Signal:** The roadmap is clearly focused on **hook reliability and reasoning control** — both are infrastructure-level improvements that enable more complex agent workflows.

---

## 7. User Feedback Summary

- **Pain point:** Hook declarations exist but don't fire, breaking observability and automation scripts that depend on them. ([#1255](https://github.com/moltis-org/moltis/issues/1255))
- **Pain point:** Inability to correlate tool call start/end events makes debugging multi-step agent flows difficult. ([#1254](https://github.com/moltis-org/moltis/issues/1254))
- **Need expressed:** Users want finer-grained control over reasoning effort, including a maximum tier for models that support it. ([#1253](https://github.com/moltis-org/moltis/pull/1253))
- **Satisfaction signal:** Contributors are actively engaging with structured issue templates (preflight checklists confirmed), suggesting a healthy contributor base familiar with the project's standards.

---

## 8. Backlog Watch

| Item | Link | Concern |
|---|---|---|
| [PR #1257](https://github.com/moltis-org/moltis/pull/1257) | Open since 2026-09-02, updated 2026-09-03 | Critical fix for hook lifecycle — no merge activity yet; needs maintainer review |
| [PR #1253](https://github.com/moltis-org/moltis/pull/1253) | Open since 2026-09-02 | Feature PR for max reasoning effort — scope is clear but unmerged |
| [PR #1256](https://github.com/moltis-org/moltis/pull/1256) | Open since 2026-09-02 | Dependabot dependency bump — routine, low risk |

**Recommendation:** PR #1257 deserves priority review, as it unblocks two user-reported issues and represents a correctness fix for the hooks subsystem. The three concurrent patch releases yesterday suggest the maintainer is in a stabilization sprint — merges may follow once the current release train settles.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-09-03

## 1. Today's Overview

QwenPaw is in an active release window for **v2.2.0**, which has shipped as a stable release today alongside **v2.2.0-beta.7**. The project saw **28 issues** and **27 PRs** updated in the last 24 hours, indicating high community engagement. Activity is concentrated around the v2.2.0 launch: installation verification duties, security sandbox concerns, and a cluster of console/backend bugs surfaced by the new beta. The project is healthy but carries typical post-release noise — several critical and high-severity bugs are already reported against v2.2.0-beta.7.

## 2. Releases

### v2.2.0 (Stable) — just published
- **QwenPaw Hub**: Self-hosted multi-user hub with local-process/Docker runtimes, workspace-level access controls, credential management, and reverse-proxy support ([#7112](https://github.com/agentscope-ai/QwenPaw/pull/7112)).
- **Release notes PR**: [#7348](https://github.com/agentscope-ai/QwenPaw/pull/7348) (closed).
- **Installation verification duty**: [#7515](https://github.com/agentscope-ai/QwenPaw/issues/7515) (deadline passed).

### v2.2.0-beta.7 (Beta)
- **fix(memory)**: Normalize backend-specific embedding dimensions ([#7465](https://github.com/agentscope-ai/QwenPaw/pull/7465)).
- **fix(webui)**: Dark-mode overrides for MCP Clients page ([#7471](https://github.com/agentscope-ai/QwenPaw/issues/7471) — closed).
- **Installation verification duty**: [#7503](https://github.com/agentscope-ai/QwenPaw/issues/7503).

### Breaking / Migration Notes
- PR #7337 (merged previously) renamed `ModelInfo.max_tokens` → `max_output_length`; custom provider configs using the old key now fail to load ([#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474)). Users with custom providers must update their JSON configs.

## 3. Project Progress

**Merged / Closed today:**
- [#7501](https://github.com/agentscope-ai/QwenPaw/pull/7501) — Agent model routing settings (sub-agent model config, fallback model toggle/scope).
- [#7348](https://github.com/agentscope-ai/QwenPaw/pull/7348) — v2.2.0 release notes.
- [#7489](https://github.com/agentscope-ai/QwenPaw/pull/7489) — Fix PyInstaller multiprocessing runtime hook for Desktop on macOS.
- [#7508](https://github.com/agentscope-ai/QwenPaw/pull/7508) — Make-Skill v2 (squashed/closed in favor of [#7509](https://github.com/agentscope-ai/QwenPaw/pull/7509)).
- [#7471](https://github.com/agentscope-ai/QwenPaw/issues/7471) — Dark-mode white background on MCP Clients page.
- [#7481](https://github.com/agentscope-ai/QwenPaw/issues/7481) — macOS StdIO MCP spawn re-entering `backend_guard` and killing the active backend.
- [#7493](https://github.com/agentscope-ai/QwenPaw/issues/7493) — Console never rendering the agent model routing panel.

**Key open PRs advancing:**
- [#7487](https://github.com/agentscope-ai/QwenPaw/pull/7487) — Theme token unification.
- [#7502](https://github.com/agentscope-ai/QwenPaw/pull/7502) — Sidebar and settings experience redesign.
- [#7509](https://github.com/agentscope-ai/QwenPaw/pull/7509) — Make-Skill v2 (approval-driven, script-based skill creation workflow).
- [#7401](https://github.com/agentscope-ai/QwenPaw/pull/7401) — Fix Windows ACP agent stalls during workspace bootstrap (under review).
- [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) — Pawport import flow (import from Codex/Qoder).
- [#7504](https://github.com/agentscope-ai/QwenPaw/pull/7504) — Enforce per-tool whitelist on agent runtime path (security hardening).

## 4. Community Hot Topics

1. **[Bug] Security sandbox breached** — [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) & [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) (5 comments). Users are actively testing and finding ways to evade content filters and breach the sandbox. This is the most discussed topic today and signals growing security-conscious adoption.

2. **[Bug] ReMe background embedding/indexing job fails** — [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) (4 comments). A silent failure in long-term memory indexing with OpenAI-compatible backends; new memories are not persisted. Directly impacts the v2.2.0-beta.7 memory feature.

3. **[Bug] Console stream shows duplicated text chunks** — [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) (6 comments). SSE event replay path produces visual artifacts in the web UI console.

4. **[Question] WeCom streaming sluggishness** — [#7507](https://github.com/agentscope-ai/QwenPaw/issues/7507) (1 comment, open). 150ms character-level throttle makes WeCom feel significantly slower than WeChat.

5. **[Enhancement] A2A protocol support** — [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) (2 comments). User asking when Agent-to-Agent (A2A) protocol will be supported alongside the existing MCP driver.

**Underlying need**: The community is pushing QwenPaw toward production multi-user deployment (Hub, sandbox security, A2A), and the v2.2.0 release is surfacing integration-edge-case bugs in memory, streaming, and governance.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **Critical** | [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) | Security sandbox breached | — |
| **Critical** | [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) | Dangerous instructions easy to evade | [#7497](https://github.com/agentscope-ai/QwenPaw/pull/7497) (open: denies sensitive paths in OFF mode) |
| **High** | [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | ReMe embedding job fails silently (`as_embedding:default accessed before start()`) | — |
| **High** | [#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474) | Custom provider load fails after `max_tokens`→`max_output_length` rename | Needs config migration |
| **High** | [#7510](https://github.com/agentscope-ai/QwenPaw/issues/7510) | `/memory/status` returns 500 on v2.2.0-beta.7 Desktop | — |
| **Medium** | [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) | Console stream duplicated text chunks | — |
| **Medium** | [#7431](https://github.com/agentscope-ai/QwenPaw/issues/7431) | Codex harness returns empty responses with non-streaming backends | — |
| **Medium** | [#7513](https://github.com/agentscope-ai/QwenPaw/issues/7513) | DeepSeek-v4-pro tool calls mixed into chat output | — |
| **Medium** | [#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447) | Early context lost in long sessions, task cannot continue | — |
| **Medium** | [#7496](https://github.com/agentscope-ai/QwenPaw/issues/7496) | CRITICAL policy rules rejected directly instead of triggering inquiry | — |
| **Low** | [#7516](https://github.com/agentscope-ai/QwenPaw/issues/7516) | WeCom cannot send base64 data-URL images | — |
| **Low** | [#7505](https://github.com/agentscope-ai/QwenPaw/issues/7505) | LAN LLM server client disconnect / timeout retries | — |
| **Low** | [#7483](https://github.com/agentscope-ai/QwenPaw/issues/7483) | Cron `share_session=true` re-loads context and accumulates timeout | Closed |
| **Low** | [#7467](https://github.com/agentscope-ai/QwenPaw/issues/7467) | `loop.rubric` confirmation + auto-fold hides first response | Closed |

**Notable regression**: The `max_tokens`→`max_output_length` rename in PR #7337 broke custom provider configs ([#7474](https://github.com/agentscope-ai/QwenPaw/issues/7474)), a breaking change that should have been documented more prominently.

## 6. Feature Requests & Roadmap Signals

- **A2A protocol support** ([#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484)): User explicitly asks for A2A alongside existing MCP. Architecture docs mention it; no timeline given. Likely a v2.3+ item.
- **Remote WebUI first-load speed** ([#7514](https://github.com/agentscope-ai/QwenPaw/issues/7514)): Long conversation histories delay rendering on initial load, especially on mobile. Performance optimization request.
- **Official theming support** ([#7406](https://github.com/agentscope-ai/QwenPaw/issues/7406)): Users want configurable accent color, font, spacing. Currently requires hacking the `.app` bundle.
- **Pawport import from Codex/Qoder** ([#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960)): Import flow for instructions, skills, plugins, projects. Under review — strong community signal for ecosystem interoperability.
- **Make-Skill v2** ([#7509](https://github.com/agentscope-ai/QwenPaw/pull/7509)): Approval-driven skill creation workflow. In progress.
- **Reranker UI config** ([#6399](https://github.com/agentscope-ai/QwenPaw/pull/6399)): Visual reranker settings panel for ReMe. Under review.

**Predicted next-version inclusions**: Pawport import (#6960), Make-Skill v2 (#7509), theme token unification (#7487), and sidebar redesign (#7502) are all open but advanced enough to land in v2.2.1 or v2.3.0.

## 7. User Feedback Summary

- **Pain point — Context loss in long sessions**: [#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447) reports early context being silently dropped after ~3 days of use on 160-page document workflows, breaking tasks. This is a critical reliability concern for power users.
- **Pain point — Sandbox/security trust**: [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) and [#7443](https://github.com/agentscope-ai/QwenPaw/issues/7443) show users actively probing security boundaries. The community takes the sandbox seriously and expects it to hold.
- **Pain point — Silent memory failures**: [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) — ReMe indexing fails silently with no user-facing error, causing data loss anxiety.
- **Pain point — Multi-agent opacity**: [#7450](https://github.com/agentscope-ai/QwenPaw/issues/7450) — Master-agent + sub-agent tasks give no proactive status updates; users must explicitly ask "进度如何" to trigger a check-in. This is a UX gap for complex agent workflows.
- **Satisfaction signal — Import flow**: The Pawport PR (#6960) addresses a real interoperability need, suggesting users value migration from other agent platforms.
- **Satisfaction signal — Release velocity**: Two releases in one day with active verification duties shows a responsive maintainer team.

## 8. Backlog Watch

| Issue / PR | Age | Why It Needs Attention |
|------------|-----|----------------------|
| [#7511](https://github.com/agentscope-ai/QwenPaw/issues/7511) — Sandbox breach | 0 days | Critical security bug on stable release; needs urgent triage. |
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) — ReMe embedding failure | 2 days | Silent data loss in long-term memory; affects v2.2.0-beta.7 users. |
| [#7447](https://github.com/agentscope-ai/QwenPaw/issues/7447) — Context loss in long sessions | 2 days | Breaks multi-day document workflows; no fix PR yet. |
| [#7484](https://github.com/agentscope-ai/QwenPaw/issues/7484) — A2A support timeline | 1 day | Strategic roadmap question with no maintainer response. |
| [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) — Pawport import | 21 days | Open since Aug 13, under review; high community value. |
| [#7401](https://github.com/agentscope-ai/QwenPaw/pull/7401) — Windows ACP stall fix | 5 days | Under review; blocks Windows ACP users. |
| [#7496](https://github.com/agentscope-ai/QwenPaw/issues/7496) — CRITICAL policy bypass | 1 day | Governance logic bug; rules meant to prompt are silently denying. |
| [#6399](https://github.com/agentscope-ai/QwenPaw/pull/6399) — Reranker UI panel | 12 days | Under review; complements existing reranker backend. |

**Overall project health**: Active release cadence and strong contributor participation are positive signals. However, the v2.2.0 stable launch has surfaced several critical-path bugs (sandbox, memory, context retention) that should be prioritized for a prompt v2.2.1 patch release.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-09-03

## 1. Today's Overview

ZeroClaw continues its high-velocity development cadence with 100 issues/PRs touched in the last 24 hours, though no new releases were published this cycle. The project is in a heavy architectural-design phase, with multiple high-stakes RFCs reaching critical review windows around session persistence, memory lifecycle, and sandbox policy. A cluster of security and delegation bugs surfaced this week, several with in-progress fix PRs, signaling the team is actively hardening the runtime ahead of the next release window.

---

## 2. Releases

No new releases today.

---

## 3. Project Progress

**Merged / Closed PRs today:**
- #10288 *(Closed)* — **RFC: deferred vote cycles** — Updated FND-003 to Rev. 16, formalizing what happens when an RFC vote misses quorum or approval thresholds.
- #9635 *(Closed)* — **Git subcommand risk classification** — Fixed `SecurityPolicy::command_risk_level` misreading global `git -C` flags as subcommands, correcting risk classification for repo operations.
- #10414 *(Closed)* — **Cron manual trigger guard** — Added owner-qualified cron-store helpers, preventing cross-agent job interference on manual runs.

**PRs actively advanced today (3+ new comments or major revisions):**
- #10567 — Memory recall entries now stamped with recall date for temporal clarity.
- #10519 — Alias-aware provider construction fix for `llm_task`.
- #10568 — Docs snap-reader scale grid fix (XS, just opened today).
- #10391 — Bounded delegate filesystem tools now respect the target agent's own workspace.
- #9745 / #9746 — Per-agent attribution and scoping for the knowledge graph and session tools (large, multi-component refactor).

---

## 4. Community Hot Topics

| Issue / PR | Comments | Topic |
|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | 32 | RFC: Runtime-owned conversation sessions & transport surface adapters (Rev 5) |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | 25 | RFC: Decouple memory lifecycle from storage backends |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | 22 | RFC: Granular sandbox policy — filesystem & network restrictions |
| [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) | 19 | RFC: Separate authoritative memory from enrichment connectors |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) | 19 | RFC: Wire protocol as first-class in provider construction |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | 16 | RFC: Computer-use desktop screen interaction |
| [#9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) | 15 | Tracker: Session-persistence contract ownership |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | 14 | Tracker: Maintainer decision queue for RFCs |

**Analysis:** The top-volatility topics are all deep-architecture RFCs concerning *session persistence*, *memory ownership*, and *security sandboxing* — the three layers the project is simultaneously re-architecting. The high comment counts with zero thumbs-up suggest these are still in active debate rather than consensus, and the maintainer decision tracker (#8692) is clearly being used to shepherd them forward. The delegate bypass bug (#10165, 6 comments but P1 severity) is a security flashpoint drawing maintainer attention.

---

## 5. Bugs & Stability

| Severity | Issue | Status | Fix PR? |
|---|---|---|---|
| **P1 / S0** | [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) — Independent delegate bypasses `block_high_risk_commands` | In-progress | [#10188](https://github.com/zeroclaw-labs/zeroclaw/pull/10188) (in review) |
| **P1 / S1** | [#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559) — Agents stop when exiting web chat window | In-progress | — |
| **P1 / S2** | [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) — Interactive session caps at 32k tokens despite 128k config | In-progress | [#9535](https://github.com/zeroclaw-labs/zeroclaw/pull/9535) (proposes ratio-based compaction) |
| **P1 / P1** | [#10501](https://github.com/zeroclaw-labs/zeroclaw/issues/10501) — MCP tool-result images return 400 on OpenAI-compatible providers | In-progress | [#10566](https://github.com/zeroclaw-labs/zeroclaw/pull/10566) |
| **P2 / S2** | [#10523](https://github.com/zeroclaw-labs/zeroclaw/issues/10523) — Bootstrap file truncation at 6k chars is invisible | Open | — |
| **P2 / S2** | [#9855](https://github.com/zeroclaw-labs/zeroclaw/issues/9855) — Matrix channel fails `.well-known` discovery | Closed (fixed) | — |
| **P2 / S2** | [#10286](https://github.com/zeroclaw-labs/zeroclaw/issues/10286) — Restored ZeroCode transcripts omit trimmed turns | Closed (fixed) | — |

**Assessment:** Three P1 bugs are currently in-flight with active fix PRs, which is a positive sign for responsiveness. The delegate security bypass (#10165) is the highest-risk item; the fix (#10188) is still awaiting maintainer review. The 32k context cap confusion (#10068) has a conceptual fix in #9535 but may not land before the next release. The invisible truncation bug (#10523) is a new P2 surfaced today — no fix yet.

---

## 6. Feature Requests & Roadmap Signals

| RFC / Feature | Status | Likely in Next Release? |
|---|---|---|
| [#10526](https://github.com/zeroclaw-labs/zeroclaw/issues/10526) — Append-only session event history & deterministic replay | New (opened Sep 1) | Low — still early |
| [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) — Verbatim channel send over gateway (no agent turn) | Accepted, 13 comments | Medium — clear use case for automation pipelines |
| [#10222](https://github.com/zeroclaw-labs/zeroclaw/issues/10222) — Opt-in single-tool provider rounds | Accepted, 5 comments | Medium — improves interactivity responsiveness |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) — WASM plugin observer lifecycle | Accepted, Rev 2 | Medium — needed for plugin ecosystem |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) — Computer-use desktop interaction | Accepted, Rev 2 | Lower — complex, needs more design finalization |
| [#9975](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) — Web bundle/daemon compatibility contract | Accepted, Rev 3 | Medium — enables self-hosted dashboard deploys |

**Prediction:** The next release will likely include verbatim gateway sends (#10050), per-agent memory scoping (PRs #9745/#9746), and the alias-aware provider fix (#10519). The WASM observer lifecycle and computer-use RFCs need more design work before shipping.

---

## 7. User Feedback Summary

**Pain points surfaced this cycle:**

- **Agents die when the browser tab closes** (#8559, S1) — users running long tasks through the web dashboard lose work on navigation, a critical workflow blocker.
- **Context cap confusion** (#10068) — operators configuring `max_context_tokens = 131072` are silently capped at 32k; the fix (#9535) introduces a model-window-ratio approach but doesn't directly communicate the change to users.
- **Delegate security bypass** (#10165) — an independent delegate can execute `rm` and other high-risk commands even when its own risk profile blocks them; this is a trust-boundary violation.
- **MCP image results broken on OpenAI-compatible providers** (#10501) — images in tool-result messages return 400 errors, blocking multimodal MCP workflows.
- **Bootstrap file truncation is invisible** (#10523) — AGENTS.md, SOUL.md, etc. are silently truncated at 6k chars, which may cause agents to miss critical context.

**Satisfaction signals:** The community is actively engaging with RFCs (high comment counts, maintainer takeovers) and contributing large PRs (#9745, #9746, #9584), indicating a healthy contributor base around the core runtime.

---

## 8. Backlog Watch

| Item | Days Open | Concern |
|---|---|---|
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) — Memory lifecycle RFC | ~74 days | Long-running; acceptance label granted but no implementation PR visible |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) — Granular sandbox policy | ~68 days | In-progress but needs maintainer review; security-critical |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) — Wire protocol first-class provider | ~68 days | Awaiting maintainer review; underlies provider onboarding |
| [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) — Memory storage vs enrichment separation | ~49 days | Acceptance granted but no merge signal; depends on #6850 |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — Runtime-owned sessions | ~37 days | Rev 5 with active debate; #9600 tracker needs a decision |
| [#10188](https://github.com/zeroclaw-labs/zeroclaw/pull/10188) — Delegate approval enforcement | ~14 days | **Security-critical fix, needs maintainer review** |
| [#9745](https://github.com/zeroclaw-labs/zeroclaw/pull/9745) — Knowledge graph per-agent scoping | ~30 days | XL-size PR, needs-author-action; foundational for memory RFCs |
| [#9746](https://github.com/zeroclaw-labs/zeroclaw/pull/9746) — Session/Discord tool scoping | ~30 days | XL-size PR, needs-author-action; blocks secure multi-agent deployments |

**Recommendation:** The delegate security fix (#10188) and the two per-agent scoping PRs (#9745, #9746) are the highest-priority items needing maintainer action. The memory-lifecycle RFC cluster (#6850, #9103) should be coordinated through tracker #9600 to avoid divergent implementations.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*