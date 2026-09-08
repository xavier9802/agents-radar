# OpenClaw Ecosystem Digest 2026-09-08

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-08 04:06 UTC

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



# OpenClaw Project Digest — 2026-09-08

## 1. Today's Overview
OpenClaw activity remains high with **500 issues** and **500 pull requests** updated in the last 24 hours. **235 issues were closed** and **198 PRs were merged/closed**, indicating sustained maintenance velocity. No new releases were published today. The project is actively addressing a dense backlog of stability, session‑state, and channel‑integration bugs, with multiple P0/P1 regressions drawing close community scrutiny.

## 2. Releases
*No new releases today.*

## 3. Project Progress
**Closed/Merged PRs today:**
- **#141737** [CLOSED] `refactor(approvals): infer lazy native runtimes` — Removes duplicated type casts across channel approval adapters by leveraging lazily loaded runtimes.
- **#141815** [CLOSED] `refactor(models): share catalog projection across local readers` — Consolidates local model‑listing logic between CLI and Gateway readers into a single projection path.

**Notable PRs awaiting review (high comment count / merge‑risk):**
- **#141779** `fix(ui): load sidebar agent‑menu avatars through authenticated blob loader` — Fixes broken agent‑avatar images when gateway token auth is enabled.
- **#141822** `fix: keep Node 22 supported for SQLite session IDs` — Corrects session‑identity sharing when stored text contains an embedded NUL byte.
- **#141477** `fix(auth): fence shared OAuth refresh generations` — Addresses process‑local OAuth refresh ownership that caused concurrent refresh races (related to #89278).
- **#112227** `fix(gateway/ui): split session group mutations to avoid concurrent add loss` — Prevents silent loss of concurrently created session groups from multiple Control‑UI tabs.

## 4. Community Hot Topics
**Most‑discussed issues (by comments):**
- **#44925** – Subagent completion silently lost — no retry, no notification, no auto‑restart on timeout (26 comments, 2 👍)  
  [Issue #44925](https://github.com/openclaw/openclaw/issues/44925)
- **#135111** – Intermittent “Provider completed tool call with malformed JSON arguments” on v2026.8.1 (17 comments)  
  [Issue #135111](https://github.com/openclaw/openclaw/issues/135111)
- **#126360** – AgentSelectionRequiredError floods logs under explicit multi‑agent ownership (16 comments)  
  [Issue #126360](https://github.com/openclaw/openclaw/issues/126360)
- **#115908** – Session transcript projection reconcile can livelock under sustained writes (16 comments)  
  [Issue #115908](https://github.com/openclaw/openclaw/issues/115908)
- **#79077** – Support for Telegram bot‑to‑bot and guest‑bot modes (15 comments, 8 👍)  
  [Issue #79077](https://github.com/openclaw/openclaw/issues/79077)

**Underlying needs:** Community attention is concentrated on **subagent reliability**, **tool‑call JSON integrity**, **multi‑agent orchestration stability**, and **Telegram platform‑feature parity**. These represent core execution‑path weaknesses that directly impact production‑grade agent workflows.

## 5. Bugs & Stability
**Reported today (ranked by severity):**

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **P0** | [#139714](https://github.com/openclaw/openclaw/issues/139714) | Post‑core update resume child admits an `update_runs` row it can never finalize — `openclaw status` reports “update in progress” forever. | No |
| **P0** | [#89278](https://github.com/openclaw/openclaw/issues/89278) | Codex OAuth refresh succeeds but cron/heartbeat fail with 10s auth‑refresh timeout. | [#141477](https://github.com/openclaw/openclaw/pull/141477) |
| **P0** | [#140497](https://github.com/openclaw/openclaw/issues/140497) | Discord setup accepts application ID as bot token, marks channel configured, never starts. | No |
| **P1** | [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent completion silently lost — no retry, no notification, no auto‑restart on timeout. | No |
| **P1** | [#135111](https://github.com/openclaw/openclaw/issues/135111) | Intermittent malformed JSON arguments on v2026.8.1 (claude‑sonnet‑5). | No |
| **P1** | [#126360](https://github.com/openclaw/openclaw/issues/126360) | AgentSelectionRequiredError floods logs under explicit multi‑agent ownership. | No |
| **P1** | [#115908](https://github.com/openclaw/openclaw/issues/115908) | Session transcript projection reconcile livelock under sustained writes, blocking main thread. | No |
| **P1** | [#97616](https://github.com/openclaw/openclaw/issues/97616) | OpenClaw leaks unreaped hook/tool child processes, causing zombie accumulation. | No |
| **P1** | [#43367](https://github.com/openclaw/openclaw/issues/43367) | Multi‑agent orchestration unstable: concurrent agents add/config overwrites, session‑lock failures. | No |
| **P1** | [#137927](https://github.com/openclaw/openclaw/issues/137927) | Internal context block leaks into visible Telegram message text. (Closed) | – |
| **P1** | [#133984](https://github.com/openclaw/openclaw/issues/133984) | 2026.7.1‑2 → 2026.8.1 leaves Gateway unstartable; `doctor --fix` skips config‑key migrations. (Closed) | – |
| **P1** | [#127229](https://github.com/openclaw/openclaw/issues/127229) | Telegram durable update falsely tombstoned before transport tracker settles. | No |
| **P1** | [#119720](https://github.com/openclaw/openclaw/issues/119720) | Synchronous agent persistence and transcript maintenance block Gateway event loop at scale. | No |
| **P1** | [#117262](https://github.com/openclaw/openclaw/issues/117262) | SQLite contention: 3 concurrent write handles on state/openclaw.sqlite cause ~33s event‑loop stalls. | No |
| **P1** | [#137613](https://github.com/openclaw/openclaw/issues/137613) | Pre‑compaction memory flush disabled on CLI backends; compactionCount trap. | No |
| **P1** | [#136311](https://github.com/openclaw/openclaw/issues/136311) | memory‑core: Gateway reacquires reindex lock on every start, 19 GB orphaned temp DBs accumulate. | No |
| **P1** | [#139809](https://github.com/openclaw/openclaw/issues/139809) | Telegram does not receive protected secrets prompt from Codex. | No |
| **P1** | [#126246](https://github.com/openclaw/openclaw/issues/126246) | Telegram durable outbound deliveries stuck in `send_attempt_started` and lost on restart. | No |
| **P1** | [#139485](https://github.com/openclaw/openclaw/issues/139485) | Managed upgrade leaves gateway offline while finalization remains non‑terminal. | No |
| **P1** | [#137332](https://github.com/openclaw/openclaw/issues/137332) | Mixed terminal requester‑settle batches retry forever after ownership check. | No |
| **P1** | [#140455](https://github.com/openclaw/openclaw/issues/140455) | google‑meet 2026.9.2: agent voice broken — circular‑JSON in‑call crash + audio‑routing verification. | No |
| **P1** | [#111578](https://github.com/openclaw/openclaw/issues/111578) | Gateway auth token dropped from service‑env on update (recurs despite 2026.7.1 fix). | No |
| **P2** | **#74586** | AM embedded run aborts `memory_search` tool calls; classifies as timeout despite model completion. | No |
| **P2** | **#48786** | Feishu replied/quoted message mentions show as raw `@_user_N` placeholders. | No |
| **P2** | **#118560** | WebChat canvas hides earlier messages after main session reset. | No |
| **P2** | **#136183** | Command executor hangs when spawning ssh — SIGTERM while waiting for server banner (regression in 2026.8.1). | No |
| **P2** | **#139578** | llama.cpp managed EmbeddingGemma runs at server‑default ubatch 512 (regression). | No |
| **P2** | **#137705** | Telegram streaming path leaks raw `[label](file:///…) ` Markdown when link scheme not in allowlist. | No |
| **P2** | **#101793** | Assistant text preceding a tool call silently dropped on Signal channel. | No |
| **P2** | **#124393** | sync transcript rewrite deletes concurrently committed transcript rows and reports success. (Closed) | – |
| **P2** | **#125764** | Telegram adapter: network‑failed outbound sends dead‑lettered after a single attempt. | No |
| **P2** | **#89430** | Google Chat: agents can't deliver images/files under app authentication (media upload → 403). | No |
| **P2** | **#49223** | WhatsApp inter‑session delivery requests wrongly suppressed as REPLY_SKIP / ANNOUNCE_SKIP / NO_REPLY. | No |

**Stability assessment:** The project is experiencing a **wave of regressions and concurrency bugs** affecting session state, SQLite I/O, OAuth refresh, and channel‑specific delivery paths. Several P1 issues are **diamond‑lobster rated** (highest severity) and remain open without active fix PRs.

## 5. Feature Requests & Roadmap Signals
**Open enhancement requests with significant community interest:**
- **#96675** – Owner‑signed responsibility gates for assistant memory, actions, skills, and evidence reuse (10 comments, 2 👍)  
  [Issue #96675](https://github.com/openclaw/openclaw/issues/96675)
- **#51441** – Expose resolved backend model in `session_status` and agent runtime (8 comments, 1 👍)  
  [Issue #51441](https://github.com/openclaw/openclaw/issues/51441)
- **#60602** – Per‑Agent Bedrock requestMetadata injection for multi‑agent cost attribution (6 comments, 1 👍)  
  [Issue #60602](https://github.com/openclaw/openclaw/issues/60602)
- **#42276** – Reasoning stream (overwrite‑line “thinking” display like OpenAI/Grok) (6 comments)  
  [Issue #42276](https://github.com/openclaw/openclaw/issues/42276)
- **#79077** – Telegram bot‑to‑bot and guest‑bot mode support (15 comments, 8 👍)  
  [Issue #79077](https://github.com/openclaw/openclaw/issues/79077)

**Feature‑focused PRs advancing:**
- **#112623** – Inject Recently Completed Subagents into parent prompt (status: ready for maintainer look)  
  [PR #112623](https://github.com/openclaw/openclaw/pull/112623)
- **#112375** – Shell precheck gate to skip LLM when no work for cron jobs (status: needs proof)  
  [PR #112375](https://github.com/openclaw/openclaw/pull/112375)
- **#131467** – Expose pause/resume to `update_goal` tool (status: waiting on author)  
  [PR #131467](https://github.com/openclaw/openclaw/pull/131467)
- **#140339** – Integrate checkpoints and interrupted‑update recovery (status: ready for maintainer look)  
  [PR #140339](https://github.com/openclaw/openclaw/pull/140339)
- **#131598** – Add Tencent `hy4‑preview` model to bundled plugin (status: needs proof)  
  [PR #131598](https://github.com/openclaw/openclaw/pull/131598)

**Roadmap prediction:** The next release is likely to address **interrupted‑update recovery** (#140339), **cron shell precheck** (#1

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — AI Agent Open-Source Ecosystem
**Date: 2026-09-08**

---

## 1. Ecosystem Overview

The personal AI agent open-source ecosystem is in an aggressive stabilization phase. Projects are converging on common pain points—session reliability, multi-agent orchestration, channel integration parity, and memory/context management—while differentiating on deployment target (desktop vs. edge vs. fleet) and architecture (monolithic gateway vs. plugin-based). OpenClaw remains the largest and most active reference implementation, but newer projects like CoPaw and ZeroClaw are matching its velocity while targeting distinct deployment models. The dominant trend is a shift from feature proliferation toward production-grade reliability, with concurrency bugs and data-loss regressions occupying the top of every project's backlog.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Merged (24h) | Release | Health Score |
|---------|-------------|-----------|-------------|---------|-------------|
| **OpenClaw** | 500 | 500 | 198 | None | 🟡 Moderate — high volume but P0/P1 regression wave |
| **CoPaw** | 34 | 36 | 3 | None | 🟡 Moderate — high velocity, post-release bug surfacing |
| **ZeroClaw** | 37 | 50 | 6 | None | 🟡 Moderate — high velocity, P1 runtime bugs |
| **Hermes Agent** | 50 | 50 | 4 | ✅ v0.21.1 | 🟢 Strong — rapid cadence, active fix delivery |
| **NanoClaw** | 2 | 28 | 17 | None | 🟢 Strong — clean merge window, maintainer-responsive |
| **NanoBot** | 0 | 23 | 7 | None | 🟢 Strong — stable hardening, focused PRs |
| **LobsterAI** | 0 | 7 | 5 | None | 🟢 Strong — responsive triage, no open issues |
| **PicoClaw** | 1 | 5 | 0 | None | 🟡 Moderate — accumulation phase, stale PRs |
| **IronClaw** | 1 | 4 | 0 | None | 🟡 Moderate — polish work, low engagement |
| **Moltis** | 0 | 1 | 0 | None | 🟠 Low — single bug fix, minimal activity |
| **NullClaw** | 0 | 1 | 0 | None | 🔴 Low — maintenance-only, no maintainer response on 3-month-old PR |
| **ZeptoClaw** | 0 | 0 | 0 | None | 🔴 Inactive — no 24h activity |

**Health Score methodology:** Weighted combination of merge velocity, bug resolution rate, release cadence, and community engagement.

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of operation:** 500 issues/PRs in 24h dwarfs all other projects, indicating the largest contributor base and community surface area.
- **Breadth of integrations:** Supports the widest channel matrix (Discord, Telegram, Signal, WhatsApp, Feishu, Google Meet, etc.)—a direct consequence of its user base size.
- **Established architecture:** Multi-agent orchestration, gateway pattern, and session-state model are the most mature in the ecosystem, serving as a reference for smaller projects.

**Technical approach differences:**
- OpenClaw uses a **gateway-centric architecture** with process-local OAuth and SQLite-backed session state, which is now its primary fragility vector (concurrency bugs, SQLite contention at scale).
- Hermes Agent and NanoBot favor **lighter gateway abstractions** with plugin/memory backends decoupled from the core event loop.
- CoPaw takes a **framework/SDK approach** rather than a deployed agent, targeting developers who embed agents rather than end-users running persistent bots.

**Community size:** OpenClaw's community is an order of magnitude larger than any peer, evidenced by comment volume (26+ comments on top issues vs. <10 on equivalent issues elsewhere) and the density of external contributor PRs.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|-----------|------------------|----------------|
| **Session lifecycle reliability** | OpenClaw, Hermes Agent, ZeroClaw, NanoBot | Lease management, zombie session detection, partial-turn persistence, crash recovery |
| **Multi-agent orchestration stability** | OpenClaw, NanoClaw, Hermes Agent | Concurrent agent coordination, approval persistence across restarts, inter-agent messaging |
| **Channel integration parity** | OpenClaw, NanoBot, PicoClaw, ZeroClaw | Streaming UX (cards, threads), voice note transcription, platform-specific features (Telegram bot-to-bot, Feishu consolidation) |
| **Memory / context management** | CoPaw, NanoBot, OpenClaw | Compaction correctness, unbounded growth prevention, context-size config, PDF/media block handling |
| **SQLite / async I/O contention** | OpenClaw, NanoBot | Event-loop blocking from synchronous persistence, connection pooling, file-lock avoidance |
| **OAuth / token refresh reliability** | OpenClaw, ZeroClaw | Concurrent refresh race conditions, cron/heartbeat auth timeout, credential rotation |
| **Scheduled task / cron robustness** | NanoClaw, Moltis, ZeroClaw, CoPaw | Timer rearming races, transcript rotation for persistent containers, active-hours parsing correctness |
| **Provider compatibility** | NanoBot, PicoClaw, OpenClaw, CoPaw | Session header requirements, model-specific caching behavior, fallback chain reliability |
| **Cost attribution & tracking** | ZeroClaw, OpenClaw, Hermes Agent | Per-conversation spend, multi-tenant billing, context compression cost visibility |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | NanoBot | CoPaw | NanoClaw | ZeroClaw |
|-----------|----------|-------------|---------|-------|----------|----------|
| **Primary target** | End-user persistent agents | Multi-profile desktop agents | Desktop/CLI personal assistant | Developer framework/SDK | Fleet/deployed agents | Desktop/TUI agents |
| **Architecture** | Monolithic gateway + channels | Multi-profile with shared MCP | Single-agent event-loop | SDK with plugin system | Durable host + coordination state | ACP + daemon + TUI |
| **Key differentiator** | Largest channel matrix, multi-agent | Multi-profile isolation, TUI | Simplicity, Edge/IoT deployment target | Plugin memory backends, i18n | Stateless task execution, durable hosting | OpenAI Responses adapter, multi-session ACP |
| **Deployment model** | Server + desktop hybrid | Desktop-first | Desktop + CLI + edge | Embeddable | Container/fleet | Desktop/TUI + daemon |
| **Maturity signal** | Reference implementation | Rapid patch cadence (v0.21.1) | Stabilization hardening | Post-v2.2.0 regression phase | Infrastructure rollup complete | Pre-release stabilization |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (high velocity, active fix delivery):**
- **OpenClaw:** Highest raw volume but regression-heavy; velocity reflects community scale more than project health.
- **Hermes Agent:** Healthiest balance—v0.21.1 shipped, 44 open issues with fast turnaround, strong contributor base.
- **ZeroClaw:** High PR throughput with meaningful fixes, but P1 runtime bugs suggest pre-stability.
- **CoPaw:** Very high issue/PR ratio post-release, indicating active community using the product at scale.

**Tier 2 — Steady Development (moderate velocity, focused scope):**
- **NanoBot:** Strong merge discipline, targeting stability hardening before next release.
- **NanoClaw:** Excellent merge-to-issue ratio (17:2), indicating a mature contributor workflow.
- **LobsterAI:** Responsive triage, no open issues, coordinated UX polish.

**Tier 3 — Low Activity / Maintenance (limited velocity):**
- **PicoClaw, IronClaw:** Small but focused contributor bases; PRs accumulating without maintainer triage.
- **Moltis:** Single bug fix, minimal community engagement.

**Tier 4 — Dormant:**
- **NullClaw:** Only Dependabot activity; 3-month-old PR unreviewed.
- **ZeptoClaw:** No 24h activity.

---

## 7. Trend Signals

**1. Session/state management is the #1 industry challenge.** Across OpenClaw, Hermes Agent, ZeroClaw, and NanoBot, the most severe bugs involve session leases, transcript persistence, and partial-turn data loss. This signals the ecosystem is moving beyond "can the agent run?" to "can the agent survive failure?"—a maturation milestone.

**2. Multi-session ACP is a fragile frontier.** ZeroClaw's cluster of P1 bugs (#9333, #10408, #10697) around session switching and parallel runs indicates this is an unsolved architectural problem across the ecosystem. Developers should treat multi-session support as experimental until these patterns are resolved.

**3. Memory compaction correctness is emerging as a critical class of bug.** NanoBot, CoPaw, and ZeroClaw all report compaction-related issues—unbounded growth, stale provider state, truncated tool results on replay. The industry needs standardized compaction semantics.

**4. Channel UX parity is a competitive differentiator.** NanoBot's Feishu card-consolidation request (#5567) and OpenClaw's Telegram multi-mode feature request (#79077) show that end-users evaluate agents by channel experience quality, not just model capability. Projects investing in first-class channel UX (streaming cards, 1-to-1 turn correspondence) will win adoption.

**5. Cost observability is a growing demand.** ZeroClaw's cost-tracking gap (#10700), OpenClaw's per-agent Bedrock attribution request (#60602), and CoPaw's context-compression role bug (#6541) all point to insufficient cost visibility as a production blocker.

**6. Local/edge deployment is expanding the addressable market.** NanoBot's IoT/unmanned-retail request (#5693) and PicoClaw's ARM64 focus indicate the ecosystem is reaching beyond desktop into constrained environments—a segment with different reliability and resource requirements.

**Value for AI agent developers:** The data suggests prioritizing session resilience and memory compaction correctness over feature breadth. Projects that ship with proven failure-recovery semantics will outperform those with more features but fragile state management. The OpenAI Responses adapter race (ZeroClaw) and multi-profile isolation (Hermes Agent) are the architectural fronts most likely to define next-generation agents.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-08

## 1. Today's Overview

NanoBot shows sustained mid-to-high development velocity with **10 PRs merged/closed** and **13 still-open PRs** under active review in the last 24 hours. The project is in a tight iterative cycle focusing on **stability hardening** (cron timers, session persistence, memory compaction, provider failover) alongside incremental feature work (AnySearch provider, macOS sandbox, WebUI enhancements). No new release was published today, suggesting the team is consolidating fixes before the next tagged version. Overall project health is strong — the merge rate is healthy and multiple priority-P1/P2 bugs are being addressed simultaneously.

---

## 2. Releases

No new releases published on this date.

---

## 3. Project Progress

### Merged / Closed PRs (7 documented)

| PR | Type | Summary |
|----|------|---------|
| [#5607](https://github.com/HKUDS/nanobot/pull/5607) | Feature | Added **AnySearch** as a new web-search provider (key-optional, anonymous quota) |
| [#5687](https://github.com/HKUDS/nanobot/pull/5687) | Docs | Clarified gateway health / WebSocket readiness endpoints (200/503 response shapes) |
| [#5691](https://github.com/HKUDS/nanobot/pull/5691) | Fix | Fixed WebUI KaTeX rendering for multiline dollar-math with attached delimiters |
| [#5676](https://github.com/HKUDS/nanobot/pull/5676) | Feature | Added attach-only Desktop CLI target selection, keeping Desktop & Python installs independent |
| [#5690](https://github.com/HKUDS/nanobot/pull/5690) | Docs | Unified personal-agent installation guide with Quick Start to reduce docs drift |
| [#5689](https://github.com/HKUDS/nanobot/pull/5689) | Fix | Fixed inconsistent working-timer display across first output when server clock lags browser |
| [#5688](https://github.com/HKUDS/nanobot/pull/5688) | Fix | Fixed stale provider state after idle compaction causing incorrect transcript resumption |

**Key advancement:** The idle-compaction pipeline (PRs #5688, #5694, #5695) is being systematically hardened — the team is ensuring memory compaction correctly invalidates provider state, uses summary checkpoints for all triggers, and keeps tool results stable across replays.

---

## 4. Community Hot Topics

| Item | Type | Comments | Updated | Link |
|------|------|----------|---------|------|
| [#5567](https://github.com/HKUDS/nanobot/issues/5567) | Issue | 5 | 2026-09-07 | Feishu multi-turn message consolidation |
| [#5580](https://github.com/HKUDS/nanobot/pull/5580) | PR | — | 2026-09-07 | Session persistence off event loop (P1) |
| [#5662](https://github.com/HKUDS/nanobot/pull/5662) | PR | — | 2026-09-07 | OpenCode session header (P1) |
| [#5630](https://github.com/HKUDS/nanobot/pull/5630) | PR | — | 2026-09-07 | Dream memory file size guardrails |
| [#5611](https://github.com/HKUDS/nanobot/pull/5611) | PR | — | 2026-09-07 | Reasoning replay bounding |

**Analysis of #5567 (5 comments):** Users on the **Feishu (Lark) channel** report a poor experience where a single user message triggers *n* separate bot messages (tool hints, progress updates, final reply). The request is to consolidate into a single streaming card message, preserving a clean 1-to-1 turn correspondence. This reflects a growing demand for **multi-channel UX parity** — as NanoBot adds more messaging integrations, each channel's native UX patterns (cards, threads, streaming) need first-class support rather than ad-hoc workarounds.

---

## 5. Bugs & Stability

### Confirmed Bugs / Regressions (ranked by severity)

1. **P1 — [#5662](https://github.com/HKUDS/nanobot/pull/5662):** OpenCode Zen/Go requires `x-opencode-session` header; without it, prompt-cache is lost and requests may error (deadline: 2026-09-06). *Fix PR open.*

2. **P1 — [#5580](https://github.com/HKUDS/nanobot/pull/5580):** Slow session storage / file-lock contention blocks the asyncio event loop, stalling unrelated conversations. *Fix PR open (has conflicts).*

3. **P2 — [#5686](https://github.com/HKUDS/nanobot/pull/5686):** Cron timer rearming race — editing the job store during callback execution cancels the timer task, causing `CancelledError` before results are saved. *Fix PR open.*

4. **P2 — [#5675](https://github.com/HKUDS/nanobot/pull/5675):** Model failover broken after runner deadlines — a hanging primary model exhausts the deadline before `FallbackProvider` can respond; the entire chain is cancelled. *Fix PR open.*

5. **P2 — [#5630](https://github.com/HKUDS/nanobot/pull/5630):** Dream memory files (SOUL.md, USER.md, MEMORY.md) can now grow unboundedly after PR #5622 removed the old size cap — causes excessive injection into every replay. *Fix PR open.*

6. **P2 — [#5682](https://github.com/HKUDS/nanobot/pull/5682):** `ExecTool` resolves relative `working_dir` against the process CWD instead of the effective workspace path. *Fix PR open.*

7. **P2 — [#5692](https://github.com/HKUDS/nanobot/pull/5692):** Recursive glob filters (`**`) don't work in `find_files` and `grep` due to `PurePosixPath.match()` semantics. *Fix PR open.*

8. **P2 — [#5694](https://github.com/HKUDS/nanobot/pull/5694):** Compaction leaves large requests behind — idle/manual compaction retains 8 archived messages and can extend through a full user/tool turn; WebUI shows stale context usage. *Fix PR open.*

9. **P2 — [#5695](https://github.com/HKUDS/nanobot/pull/5695):** Tool results are re-truncated on replay, breaking persistence stability. *Fix PR open.*

**Notable regression fix today:** [#5688](https://github.com/HKUDS/nanobot/pull/5688) resolved a compaction-related bug where idle-archived sessions incorrectly resumed from stale provider history (observed in Codex sessions retaining only 8 replayable messages post-compact).

---

## 6. Feature Requests & Roadmap Signals

| Item | Type | Description | Link |
|------|------|-------------|------|
| #5693 | Feature Request | Ultra-lightweight, self-hosted person for **unmanned retail / IoT** scenarios; requests lightweight deployment & Chinese docs | [Issue](https://github.com/HKUDS/nanobot/issues/5693) |
| #5567 | Feature Request | Feishu channel: consolidate multi-turn replies into single streaming card message | [Issue](https://github.com/HKUDS/nanobot/issues/5567) |
| #5602 / #5547 | PR (open) | WebUI completion notification sound (opt-in chime) — two converging PRs for the same feature | [PR #5602](https://github.com/HKUDS/nanobot/pull/5602) · [PR #5547](https://github.com/HKUDS/nanobot/pull/5547) |
| #5628 | PR (open) | macOS Seatbelt sandbox backend for `ExecTool` — opt-in, no new dependencies | [PR](https://github.com/HKUDS/nanobot/pull/5628) |
| #5611 | PR (open) | Bound reasoning replay to latest assistant turn only, cutting prefill cost | [PR](https://github.com/HKUDS/nanobot/pull/5611) |
| #5676 | Merged | CLI attach-only Desktop target selection | [PR](https://github.com/HKUDS/nanobot/pull/5676) |
| #5607 | Merged | AnySearch web-search provider | [PR](https://github.com/HKUDS/nanobot/pull/5607) |

**Prediction for next release:** The two converging notification-sound PRs (#5602, #5547) will likely be squashed into one merged PR. The macOS Seatbelt sandbox (#5628) and reasoning-replay bounding (#5611) are strong candidates for inclusion given their P1/P2 priority labels and direct performance/security impact.

---

## 7. User Feedback Summary

- **Feishu UX friction (#5567):** Users expect a clean 1-message-in / 1-message-out interaction model on messaging platforms. The current behavior of splattering tool-progress and final-reply across multiple messages is a consistent pain point. This will likely recur for other channels (WeChat, Discord, etc.) as the project expands.
- **Unmanned retail / IoT use case (#5693):** A user from the 落朵 (Luoduo) ecosystem is evaluating NanoBot for edge deployment in smart vending/IoT scenarios. This signals growing interest in **resource-constrained, self-hosted** deployments beyond the current desktop/CLI focus.
- **OpenCode provider compatibility (#5662):** Users are adopting OpenCode Zen/Go as a provider and hitting hard breakages when the session header is missing. This reflects the growing diversity of compatible LLM providers and the need for robust provider-layer error handling.
- **WebUI timer inconsistency (#5689 — fixed):** Server-browser clock skew caused jumpy "Working for Xs" display. Users value real-time feedback accuracy during long-running agent turns.

---

## 8. Backlog Watch

| Item | Type | Priority | Concern | Link |
|------|------|----------|---------|------|
| [#5580](https://github.com/HKUDS/nanobot/pull/5580) | Fix | **P1** | Has merge conflicts; session persistence off event loop is critical for multi-conversation stability. Needs maintainer attention to resolve. | [PR](https://github.com/HKUDS/nanobot/pull/5580) |
| [#5567](https://github.com/HKUDS/nanobot/issues/5567) | Feature | P2 | 5 comments, open since Aug 27 — Feishu card consolidation is a high-visibility UX gap with no active PR yet. | [Issue](https://github.com/HKUDS/nanobot/issues/5567) |
| [#5693](https://github.com/HKUDS/nanobot/issues/5693) | Feature Request | P2 | New IoT/unmanned-retail use case with zero engagement. Could indicate a viable lightweight deployment roadmap branch. | [Issue](https://github.com/HKUDS/nanobot/issues/5693) |
| [#5602](https://github.com/HKUDS/nanobot/pull/5602) | Feature | P2 | Overlaps with #5547 (same feature, different author). Needs resolution to avoid duplicate effort. | [PR](https://github.com/HKUDS/nanobot/pull/5602) |
| [#5547](https://github.com/HKUDS/nanobot/pull/5547) | Feature | P2 | See #5602. | [PR](https://github.com/HKUDS/nanobot/pull/5547) |
| [#5630](https://github.com/HKUDS/nanobot/pull/5630) | Fix | P2 | Dream memory unbounded growth is a regression with real cost impact; PR is open but not yet merged. | [PR](https://github.com/HKUDS/nanobot/pull/5630) |

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-09-08

## 1. Today's Overview

Hermes Agent is in a period of intense activity and refinement, with 50 issues and 50 PRs updated in the last 24 hours. The project just shipped **v0.21.1** (tagged v2026.9.7), a patch release rolling up the current main since v0.21.0. With 44 open/active issues and 49 open PRs, the team is absorbing a high volume of bug reports and feature work simultaneously. The project health is strong: rapid release cadence, active community participation, and a broad set of contributors driving fixes across desktop, gateway, agent core, and TUI components.

---

## 2. Releases

### v0.21.1 (v2026.9.7) — Patch Release
- **Release Date:** September 7, 2026
- **Commit:** `6178e9f4eed8d99f4fc550add939d58c7bed6206`
- **Scope:** Roll-up of current main since v0.21.0; tagged for deployments and downstream consumers.
- **Breaking Changes:** None reported for this patch release.
- **Migration Notes:** Standard upgrade path; users on v0.21.0 should apply the patch. Existing config and session state are preserved.

---

## 3. Project Progress

### Merged / Closed Today
| Item | Type | Summary |
|------|------|---------|
| [#82874](https://github.com/NousResearch/hermes-agent/issues/82874) | Bug (Closed) | Gateway SIGTERM now handles MCP shutdown without blocking the event loop |
| [#105235](https://github.com/NousResearch/hermes-agent/issues/105235) | Feature (Closed) | Streaming TTS first-sentence tuning consolidated into #96933 |
| [#104689](https://github.com/NousResearch/hermes-agent/issues/104689) | Bug (Closed) | Windows updater false-success after AV interruption — root cause identified |
| [#92703](https://github.com/NousResearch/hermes-agent/issues/92703) | Bug (Closed) | Telegram/Kanban notification pollution in long-running sessions |

### Notable Open PRs Advancing
- **#105545** — Native Gemini tool calls now survive nullable/union parameters (salvages #55643)
- **#105546** — Unicode offset preservation in streaming scrubbers
- **#105542** — Shared MCP visibility preserved across profile reloads
- **#105481** — Multi-profile approval flow fixed via durable session key propagation
- **#105543 / #105539** — Group chats can be filed into user-made roster sections
- **#105540** — Resident lease reclaim from dead lanes (fixes #104691)
- **#102411** — Row-addressed `api_content` backfill for pre-persisted user turns
- **#105530** — Usage anchors preserved across display-only transcript rewrites
- **#105308** — Unified replay history canonicalization

---

## 4. Community Hot Topics

### Top Issues by Comment Count

1. **[Issue #97681](https://github.com/NousResearch/hermes-agent/issues/97681)** — *Bot Group Chats should keep working after Desktop closes* (27 comments)
   - Users want multi-device bot continuity: bots running on different hosts (laptop, VPS, home server) should sustain group chats independently. This reflects growing use of Hermes as a distributed bot orchestration layer.

2. **[Issue #53004](https://github.com/NousResearch/hermes-agent/issues/53004)** — *Projects paradigm broke the folder → session → sidebar flow* (14 comments)
   - The #49037 "first-class projects" change (merged 2026-06-25) introduced a workflow regression. This is a high-friction usability issue affecting daily desktop usage.

3. **[Issue #90663](https://github.com/NousResearch/hermes-agent/issues/90663)** — *TUI (Ink) lowercases Shift+letter in Ghostty prompt composer* (12 comments, closed)
   - A P1 bug in the new Ink TUI on macOS/Ghostty. Uppercase input being destroyed is a critical defect for a text entry component. Closed — fix delivered.

4. **[Issue #86146](https://github.com/NousResearch/hermes-agent/issues/86146)** — *Model switching across profiles uses main profile's model list* (10 comments)
   - Profile isolation is broken for model selection, undermining the multi-profile design.

5. **[Issue #52261](https://github.com/NousResearch/hermes-agent/issues/52261)** — *Local MLX/oMLX provider 400s misclassified as `context_overflow`* (9 comments)
   - Destructive compression/reset loop caused by incorrect error classification. Affects local inference users with constrained resources.

### Community Themes
- **Multi-profile / multi-session isolation** is a dominant concern (issues #86146, #101856, #105525, PRs #105542, #105481)
- **Session lifecycle robustness** drives significant engagement (#97681, #52261, #104691)
- **Desktop UX regressions** from recent architecture changes (#53004)

---

## 5. Bugs & Stability

### Critical / P1 Bugs
| Issue | Severity | Description | Fix PR |
|-------|----------|-------------|--------|
| [#53004](https://github.com/NousResearch/hermes-agent/issues/53004) | P1 | Projects paradigm broke folder→session sidebar flow | Pending |
| [#52261](https://github.com/NousResearch/hermes-agent/issues/52261) | P1 | Local provider 400s misclassified → destructive compress loop | Pending |
| [#104691](https://github.com/NousResearch/hermes-agent/issues/104691) | P1 | Zombie session lease locks session permanently ("already has a live owner") | [#105540](https://github.com/NousResearch/hermes-agent/pull/105540) |
| [#103786](https://github.com/NousResearch/hermes-agent/issues/103786) | P1 | Windows gateway-retry loop blocks Electron main thread → AppHangB1 | Pending |
| [#105541](https://github.com/NousResearch/hermes-agent/issues/105541) | P1 | Gateway turn cancellation waits for stream flush and can be swallowed | Pending |
| [#102411](https://github.com/NousResearch/hermes-agent/issues/102194) | P0 | Pre-persisted user turns missing provider prompt cache | [#102411](https://github.com/NousResearch/hermes-agent/pull/102411) |

### P2 Bugs (Selected)
| Issue | Description | Fix PR |
|-------|-------------|--------|
| [#90663](https://github.com/NousResearch/hermes-agent/issues/90663) | TUI Ink Shift+letter lowercase on Ghostty (closed) | ✅ |
| [#91130](https://github.com/NousResearch/hermes-agent/issues/91130) | `drive_preview` off-target clicks on fractional-DPR displays | — |
| [#98524](https://github.com/NousResearch/hermes-agent/issues/98524) | Assistant messages rendered twice in desktop transcript | — |
| [#58083](https://github.com/NousResearch/hermes-agent/issues/58083) | ACP `session/new` hangs on Windows during agent boot | — |
| [#9971](https://github.com/NousResearch/hermes-agent/issues/9971) | Weixin TTS not delivered as voice bubbles (OGG→SILK transcoding) | — |
| [#105311](https://github.com/NousResearch/hermes-agent/issues/105311) | Responses streaming omits `post_api_request.first_chunk_at` | — |
| [#104912](https://github.com/NousResearch/hermes-agent/issues/104912) | Internal execution content rendered as assistant response | — |
| [#101856](https://github.com/NousResearch/hermes-agent/issues/101856) | Browser preview tabs not isolated per session/profile | — |
| [#105497](https://github.com/NousResearch/hermes-agent/issues/105497) | Desktop barge-in transcript silently dropped by stale `busy` closure | — |
| [#99286](https://github.com/NousResearch/hermes-agent/issues/99286) | Desktop shows half the real context window for custom providers | — |
| [#80625](https://github.com/NousResearch/hermes-agent/issues/80625) | SSH remote backend fails with Fish shell | — |
| [#55645](https://github.com/NousResearch/hermes-agent/issues/55645) | Gemini tool translation crashes on array-typed enum params | [#105545](https://github.com/NousResearch/hermes-agent/pull/105545), [#55643](https://github.com/NousResearch/hermes-agent/pull/55643) |
| [#105471](https://github.com/NousResearch/hermes-agent/issues/105471) | `_send_with_retry` re-sends plain-text fallback after in-loop timeout | — |
| [#105525](https://github.com/NousResearch/hermes-agent/issues/105525) | Custom `HERMES_HOME` collides with default service name, rewrites systemd unit | — |
| [#104689](https://github.com/NousResearch/hermes-agent/issues/104689) | Windows updater reports success after AV interruption (closed) | ✅ |
| [#26665](https://github.com/NousResearch/hermes-agent/issues/26665) | Desktop language resets to English on restart | [#105465](https://github.com/NousResearch/hermes-agent/issues/105465) (duplicate) |

### Key Observations
- **Session lifecycle bugs** are the most prevalent category, with 4+ P1/P2 issues affecting lease management, compression loops, and approval routing.
- **Windows-specific issues** are clustered (hangs, updater failures, SSH compatibility), suggesting the platform needs dedicated regression testing.
- **Multi-profile isolation** is an emerging weakness, with 3+ bugs and multiple fix PRs active.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Likelihood for Next Release |
|-------|---------|----------------------------|
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | Bot group chats survive Desktop close / multi-device continuity | High — core to multi-device vision |
| [#44926](https://github.com/NousResearch/hermes-agent/issues/44926) | Configurable rate limit for interim assistant messages on messaging gateways | Medium — depends on gateway architecture |
| [#105543](https://github.com/NousResearch/hermes-agent/pull/105543) | File group chats into user-made roster sections | High — PR is ready and under review |
| [#97510](https://github.com/NousResearch/hermes-agent/pull/97510) | Session model audit/reset CLI + cron list model pins | Medium — CLI-facing, needs decision |
| [#105503](https://github.com/NousResearch/hermes-agent/pull/105503) | Czech i18n translation | Low-Medium — community contribution, incremental |
| [#105235](https://github.com/NousResearch/hermes-agent/issues/105235) | Streaming TTS first-sentence tuning | Medium — consolidation in progress |

**Roadmap Signals:**
- **Multi-device / distributed bot orchestration** is a clear priority (group chat persistence, cross-device session state).
- **Profile isolation** improvements are being actively addressed (MCP visibility, approval flow, model overrides).
- **Session tooling** (audit, compression, cache) is being hardened for production use.
- **Desktop UX organization** (roster sections for group chats) indicates investment in desktop navigation.

---

## 7. User Feedback Summary

### Pain Points
1. **Session reliability** — Users report persistent crashes, hangs, and "zombie lease" conditions that lock sessions permanently. These are high-friction issues that prevent long-running agent use.
2. **Profile isolation failures** — Model switching, MCP tool exposure, and approval prompts bleed across profiles, undermining multi-tenant and multi-project workflows.
3. **Desktop UX regressions** — The "first-class projects" change (#49037) broke the established sidebar workflow, and language settings don't persist after updates.
4. **Windows stability** — Gateway retry loops, updater false-success, and SSH/Fish incompatibility create a poor experience on Windows.
5. **Local inference pain** — Misclassified errors (400s as context overflow) cause destructive auto-compression loops, particularly for MLX/oMLX users.

### Positive Signals
- **Rapid fix turnaround** — Several P1 issues have already landed PRs or were closed within days.
- **Community contributions** — Multiple external contributors are submitting high-quality fixes (Gemini schema, session lease reclaim, Unicode handling).
- **Transparency** — Issue descriptions are detailed, with repro steps, environment info, and root-cause analysis included.
- **i18n expansion** — Czech translation PR shows growing international community engagement.

### User Satisfaction
Generally **cautiously positive**. The project ships frequently and responds to bugs, but the density of P1 issues in session lifecycle and profile isolation suggests the 0.21.x series is still stabilizing core reliability.

---

## 8. Backlog Watch

### Issues Needing Maintainer Attention

| Issue | Why It Matters |
|-------|---------------|
| [#53004](https://github.com/NousResearch/hermes-agent/issues/53004) — Projects sidebar regression | 14 comments, breaks core desktop workflow introduced by a major PR. Needs prioritized fix. |
| [#52261](https://github.com/NousResearch/hermes-agent/issues/52261) — Local provider error misclassification | 9 comments, destructive behavior for local inference users. No fix PR yet. |
| [#86146](https://github.com/NousResearch/hermes-agent/issues/86146) — Profile model list not isolated | 10 comments, directly contradicts multi-profile design promise. |
| [#103786](https://github.com/NousResearch/hermes-agent/issues/103786) — Windows gateway AppHangB1 | P1, causes complete desktop freezes. No fix PR visible. |
| [#58083](https://github.com/NousResearch/hermes-agent/issues/58083) — ACP session/new hangs on Windows | P2, blocks ACP-based workflows on the most common desktop OS. |
| [#9971](https://github.com/NousResearch/hermes-agent/issues/9971) — Weixin TTS voice bubbles | Open since April 2026, no fix progress. Blocks WeChat integration quality. |
| [#26665 / #105465](https://github.com/NousResearch/hermes-agent/issues/26665) — Desktop language reset | Duplicate issues; language persistence is a basic quality bar. |
| [#95837](https://github.com/NousResearch/hermes-agent/issues/95837) — Nous provider 404 on muse-spark-1.2-contributor | Suspected upstream endpoint filter; needs vendor-side investigation. |

### PRs Pending Review
- [#105545](https://github.com/NousResearch/hermes-agent/pull/105545) — Gemini nullable/union fix
- [#105540](https://github.com/NousResearch/hermes-agent/pull/105540) — Session lease reclaim
- [#105481](https://github.com/NousResearch/hermes-agent/pull/105481) — Multi-profile approval fix
- [#105542](https://github.com/NousResearch/hermes-agent/pull/105542) — MCP profile isolation
- [#105546](https://github.com/NousResearch/hermes-agent/pull/105546) — Unicode streaming scrubber fix
- [#105530](https://github.com/NousResearch/hermes-agent/pull/105530) — Usage anchor preservation
- [#105308](https://github.com/NousResearch/hermes-agent/pull/105308) — Replay history canonicalization

---

*Digest generated from GitHub data on 2026-09-08. Source: [Nous

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-08

## 1. Today's Overview

PicoClaw shows moderate daily activity with **1 open issue** and **5 open pull requests** updated in the last 24 hours. No issues were closed and no PRs merged today, indicating the project is in an accumulation phase rather than a release-cleanup cycle. Development momentum is healthy across multiple fronts — new provider integrations (OpenCode Go, Keenable), protocol support (IRCv3 multiline), and tooling improvements are all actively discussed. No releases were published today.

## 2. Releases

No new releases were published today. The latest reported version remains **0.3.1** (nightly build).

## 3. Project Progress

**Merged/Closed PRs today:** None.

**Features advancing today (open PRs):**

- **PR #3371** — Adds a dedicated `opencode-go` provider with automatic per-model routing and `x-opencode-session` header support, addressing a gap in existing OpenCode integration ([sipeed/picoclaw#3371](https://github.com/sipeed/picoclaw/pull/3371)).
- **PR #3370** — Introduces Keenable as a `web_search` provider that requires no API key on fresh install, broadening out-of-the-box search capability ([sipeed/picoclaw#3370](https://github.com/sipeed/picoclaw/pull/3370)).
- **PR #3354** — Assembles IRCv3 `draft/multiline` messages into cohesive inbound payloads, improving IRC channel reliability ([sipeed/picoclaw#3354](https://github.com/sipeed/picoclaw/pull/3354)).
- **PR #3353** — Bounds tool feedback animations with a 5-minute lifetime cap and early termination on edit errors, preventing indefinite message edits ([sipeed/picoclaw#3353](https://github.com/sipeed/picoclaw/pull/3353)).
- **PR #3344** — Adds a Build Remote Agent (`gbr/1`) phone-pairing adapter for desktop-agent spectating ([sipeed/picoclaw#3344](https://github.com/sipeed/picoclaw/pull/3344)).

## 4. Community Hot Topics

| Item | Type | Activity | Link |
|------|------|----------|------|
| QQ channel 401 auth failure | Issue #3365 | 1 comment, 1 👍 | [sipeed/picoclaw#3365](https://github.com/sipeed/picoclaw/issues/3365) |
| OpenCode Go provider addition | PR #3371 | Created today | [sipeed/picoclaw#3371](https://github.com/sipeed/picoclaw/pull/3371) |
| Keenable web search provider | PR #3370 | Created today | [sipeed/picoclaw#3370](https://github.com/sipeed/picoclaw/pull/3370) |

**Analysis:** The QQ channel 401 issue (root-caused to `botgo v0.2.1` + `resty >= v2.17` incompatibility) is the only currently tracked bug with community engagement. The two provider-addition PRs (OpenCode Go, Keenable) signal user demand for **broadening LLM provider coverage** and **zero-config search tools**, respectively. IRCv3 multiline support reflects an ongoing effort to stabilize PicoClaw as a serious IRC bot client.

## 5. Bugs & Stability

| Severity | Item | Details | Fix PR |
|----------|------|---------|--------|
| **Medium** | QQ channel 401 "Authorization parameter format error" (#3365) | Caused by incompatibility between `botgo v0.2.1` and `resty v2.17.1+`; affects QQ Bot API integration on ARM64 (Orange Pi 3B) | No fix PR yet |
| **Low** | Tool feedback animations may run indefinitely | Missed lifecycle cleanup can cause persistent channel message editing | PR #3353 addresses this |

No crashes or regressions reported today.

## 6. Feature Requests & Roadmap Signals

- **OpenCode Go provider** (#3371, closes #3369) — Strong signal that users want deeper OpenCode.ai integration with session-aware routing. Likely to merge given it's cleanly scoped.
- **Keenable web search** (#3370) — Zero-configuration search provider; aligns with the trend of making PicoClaw more plug-and-play for new users.
- **IRCv3 multiline support** (#3354) — Indicates IRC remains a priority channel for active contributors.
- **Build Remote Agent phone pairing** (#3344) — Suggests interest in mobile companion interfaces for desktop agents, though this PR is stale.

**Prediction:** PRs #3371 and #3370 are the most likely candidates for the next release, given their focused scope and fresh creation dates.

## 7. User Feedback Summary

- **Pain point:** QQ channel authentication is broken for users on ARM64 platforms with current dependency versions (#3365). The `botgo` + `resty` version conflict needs a dependency bump or workaround.
- **Satisfaction signal:** Users are actively contributing providers (OpenCode Go, Keenable), suggesting healthy engagement with PicoClaw's plugin/provider architecture.
- **Use cases:** IRC bot operation, QQ bot integration, desktop agent spectating via phone, and out-of-the-box web search are the most commonly referenced scenarios.

## 8. Backlog Watch

| Item | Age | Status | Link |
|------|-----|--------|------|
| PR #3344 — Build Remote Agent phone pairing | 16 days | Stale, no maintainer response | [sipeed/picoclaw#3344](https://github.com/sipeed/picoclaw/pull/3344) |
| PR #3354 — IRCv3 multiline support | 8 days | Stale, no maintainer response | [sipeed/picoclaw#3354](https://github.com/sipeed/picoclaw/pull/3354) |
| PR #3353 — Bound tool feedback animations | 8 days | Stale, no maintainer response | [sipeed/picoclaw#3353](https://github.com/sipeed/picoclaw/pull/3353) |
| Issue #3365 — QQ channel 401 error | 4 days | Open, no fix PR yet | [sipeed/picoclaw#3365](https://github.com/sipeed/picoclaw/issues/3365) |

Three stale PRs and one unresolved bug issue await maintainer triage. The QQ channel issue (#3365) is the most time-sensitive given it blocks a real user on a supported platform.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-08

## 1. Today's Overview

NanoClaw saw robust contributor activity today with **28 PRs updated** (17 merged/closed, 11 still open) and **2 active issues** reported. The project is in a steady development cadence with no new releases deployed. Activity is concentrated around core reliability fixes (agent-to-agent messaging, approval persistence, CI hardening) and new capability additions (email channel adapter, stateless scheduled tasks). The closed-PR count significantly outpacing open issues suggests the team is in a productive merge window.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**Merged / Closed PRs Today:**

- **#3739** — `ci(registry-skills)`: Added a `registry gate` check and made builds resilient to Docker Hub 5xx errors. ([link](https://github.com/nanocoai/nanoclaw/pull/3739))
- **#3737** — `fix(db)`: Stopped a nested-continuation conformance test from racing its own watchdog on PostgreSQL. ([link](https://github.com/nanocoai/nanoclaw/pull/3737))
- **#3736** — `ci`: Added a `gate` job and a post-merge run on `main` to catch dependency failures. ([link](https://github.com/nanocoai/nanoclaw/pull/3736))
- **#3734** — `fix(ci)`: Resolved competing PR label workflows that were overwriting classifications and accumulating duplicates. ([link](https://github.com/nanocoai/nanoclaw/pull/3734))
- **#3518** — `fix(approvals)`: Approvals now survive process restarts via row-keyed resolution through the gateway-provider seam. ([link](https://github.com/nanocoai/nanoclaw/pull/3518))
- **#3517** — `feat(db)`: Shadow-write coordination state alongside in-memory maps for durability. ([link](https://github.com/nanocoai/nanoclaw/pull/3517))
- **#3653** — `rollup`: Integrated the full durable-host chain (coordination state, wake seam, reconcile queue, restart-honest delivery, claim fencing). ([link](https://github.com/nanocoai/nanoclaw/pull/3653))
- **#3661** — `fix(container)`: Bun install in container builds now retries instead of failing on transient network errors. ([link](https://github.com/nanocoai/nanoclaw/pull/3661))
- **#1519** — `fix`: Prevented duplicate task runs, cleaned up orphaned tasks, and hardened IPC in the scheduler. ([link](https://github.com/nanocoai/nanoclaw/pull/1519))
- **#3400** — `fix(typing)`: Slack typing/status indicator now ends when the reply is actually delivered. ([link](https://github.com/nanocoai/nanoclaw/pull/3400))

**Key themes:** Durable hosting infrastructure landed as a full rollup, CI reliability improved across multiple fronts, and scheduler/approval robustness was strengthened.

## 4. Community Hot Topics

- **[#3735] Conversations archives grow without bound** — 1 comment. No retention or cap on `conversations/` archives causes unbounded disk growth on long-lived agent groups. ([link](https://github.com/nanocoai/nanoclaw/issues/3735))
- **[#3732] Transcript rotation never runs for tasks that keep their container alive** — No comments yet, but directly tied to #3735. Long-running scheduled tasks prevent `maybeRotateContinuation()` from ever firing. ([link](https://github.com/nanocoai/nanoclaw/issues/3732))
- **[#3738] Fix: thread replies from the message being answered** — Open PR addressing a UX bug where file replies land in the main channel instead of the correct thread. ([link](https://github.com/nanocoai/nanoclaw/pull/3738))
- **[#3743] AgentMail email channel adapter** — Open PR proposing a native email channel via AgentMail API, avoiding the DNS/MX ownership problem. ([link](https://github.com/nanocoai/nanoclaw/pull/3743))
- **[#3741] Scheduled tasks: `--fresh-session` for stateless runs** — Open PR targeting recurring jobs that re-read ever-growing conversation history, with one user reporting 15% cost growth per week. ([link](https://github.com/nanocoai/nanoclaw/pull/3741))

**Analysis:** The top concerns cluster around **operational cost and disk management** for long-lived agents. Users running scheduled tasks on persistent containers are hitting real pain points with transcript bloat and unbounded growth. The `--fresh-session` feature request (#3741) and the archive retention issue (#3735) are directly related — the community clearly needs better lifecycle management for long-running agent workloads.

## 5. Bugs & Stability

| Severity | Item | Details | Fix PR |
|----------|------|---------|--------|
| **High** | #3735 — Unbounded conversation archive growth | Archives in `groups/<folder>/conversations/` are never rotated or capped, causing disk exhaustion on fleet deployments. | No fix yet |
| **High** | #3732 — Transcript rotation never runs for persistent tasks | `maybeRotateContinuation()` only fires once per container start; tasks with recurrence shorter than the 30-min idle ceiling keep containers alive indefinitely. | No fix yet |
| **Medium** | #3738 — Replies and files land in wrong thread | `resolveRouting` takes thread from `session_routing.thread` instead of the message being replied to, sending files to main channel. | #3738 (open) |
| **Medium** | #3742 — `--ro` mount flag is a no-op | `ncl groups config add-mount --ro` does nothing; read-write mounts cannot be explicitly expressed. | #3742 (open) |
| **Low** | #3400 — Slack typing indicator outlives reply | Resolved and merged; typing status could persist for minutes after delivery. | #3400 (merged) |
| **Low** | #3661 — Bun install failure in container builds | Transient network errors during Docker build caused hard failures. | #3661 (merged) |

## 6. Feature Requests & Roadmap Signals

- **[#3743] AgentMail email channel adapter** — Native email support without DNS/MX ownership. ([link](https://github.com/nanocoai/nanoclaw/pull/3743))
- **[#3741] `--fresh-session` for scheduled tasks** — Stateless execution mode to avoid compounding context costs. ([link](https://github.com/nanocoai/nanoclaw/pull/3741))
- **[#3733] OpenCode provider skill** — Self-contained provider for installation recovery and debugging. ([link](https://github.com/nanocoai/nanoclaw/pull/3733))
- **[#3729] Browser-based community cell connection** — Move Echo/Slack setup into the browser portal with WorkOS sign-in. ([link](https://github.com/nanocoai/nanoclaw/pull/3729))
- **[#3494] Build Remote Agent phone pairing** — QR + 8-char code pairing for phone spectating. ([link](https://github.com/nanocoai/nanoclaw/pull/3494))

**Prediction:** The `--fresh-session` flag (#3741) and AgentMail adapter (#3743) are the most likely candidates for the next release, given they address high-demand operational needs and are already well-scoped.

## 7. User Feedback Summary

- **Pain point:** Long-running scheduled tasks cause **exponential conversation growth** — one user reported a 15% cost increase in a single week (#3741). This is the most frequently cited operational concern.
- **Pain point:** No way to control transcript rotation for persistent containers, leading to **unbounded disk usage** (#3735, #3732).
- **Pain point:** File replies and non-text messages land in the **wrong channel/thread** due to routing logic (#3738).
- **Pain point:** CLI mount options are misleading — `--ro` is a no-op and there's no way to explicitly request read-write (#3742).
- **Positive signal:** The durable-host rollup (#3653) and approval restart resilience (#3518) address long-standing reliability concerns raised by fleet operators.
- **Satisfaction:** CI reliability improvements (#3734, #3736, #3739) reduce friction for contributors.

## 8. Backlog Watch

- **#3735** — Unbounded archive growth: Critical for fleet operators but no fix PR open yet. Needs maintainer triage. ([link](https://github.com/nanocoai/nanoclaw/issues/3735))
- **#3732** — Transcript rotation gap: Same author as #3735, likely part of the same root cause. No fix PR open. ([link](https://github.com/nanocoai/nanoclaw/issues/3732))
- **#3742** — `--ro` no-op bug: Small but misleading CLI behavior; easy fix but unaddressed. ([link](https://github.com/nanocoai/nanoclaw/pull/3742))
- **#3718 / #3719** — Agent-to-agent messaging identity and failure reporting: Two open PRs from September 4 still awaiting review. Important for multi-agent reliability. ([link](https://github.com/nanocoai/nanoclaw/pull/3718), [link](https://github.com/nanocoai/nanoclaw/pull/3719))

---

**Project Health Assessment:** Active and healthy. The core team is delivering meaningful infrastructure improvements (durable host, CI hardening, scheduler fixes) while community contributions are bringing in practical features (email adapter, fresh sessions, phone pairing). The main risk area is **operational hygiene for long-lived agents** — two critical but related issues around transcript/archival growth remain unfixed.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-09-08

## 1. Today's Overview

NullClaw registered minimal activity today, with zero issues updated and no new releases pushed to the repository. The sole signal of movement is a single open dependabot-maintained pull request updating the Alpine base image within the Docker build group. No merged PRs or closed issues appeared in the last 24 hours, indicating a quiet operational window. Overall project health appears stable but low in near-term development velocity.

## 2. Releases

**No new releases** were published. There are no version changes, breaking changes, or migration notes to report.

## 3. Project Progress

- **Merged/Closed PRs today:** None.
- **Open PR in motion:** [#956](https://github.com/nullclaw/nullclaw/pull/956) — `ci(deps): bump alpine from 3.23 to 3.24` — remains open and unmerged. This is an automated dependency update by Dependabot rather than a feature or bug-fix advance. No codebase-level improvements were shipped today.

## 4. Community Hot Topics

With no new issues or discussion activity, there are **no trending topics** this period. The lone item drawing any attention is PR #956 (Dependabot Alpine bump), though it carries zero reactions and no comments. This suggests the community is not currently engaged in public debate around containerization or infrastructure tooling.

**Underlying need signal:** Dependabot's continued operation indicates the project relies on automated dependency hygiene, but the lack of maintainer response on PR #956 (last updated 2026-09-07) may point to limited maintainer bandwidth.

## 5. Bugs & Stability

- **No bugs, crashes, or regressions** were reported today.
- **No fix PRs** are associated with any open issue.

The absence of bug reports is consistent with low overall issue volume and does not necessarily indicate perfect stability — it more likely reflects a quiet reporting cycle.

## 6. Feature Requests & Roadmap Signals

- **No new feature requests** were filed today.
- **No roadmap signals** emerged from issues or discussions.

The project's current activity is dominated by infrastructure maintenance rather than feature development, suggesting the maintainers may be in a stabilization or low-priority phase.

## 7. User Feedback Summary

No user feedback, pain points, or satisfaction signals were captured today. The absence of new issues and comments makes it impossible to assess user sentiment from GitHub data for this reporting period. Any prior user concerns appear to have been resolved or are dormant.

## 8. Backlog Watch

| # | Type | Title | Last Updated | Action Needed |
|---|------|-------|-------------|---------------|
| [#956](https://github.com/nullclaw/nullclaw/pull/956) | PR | `ci(deps): bump alpine from 3.23 to 3.24` | 2026-09-07 | Awaiting maintainer review/merge |

**Notable:** PR #956 has been open since 2026-06-15 and last updated just yesterday, indicating it has been pending review for approximately three months. This is the only item in the active backlog and represents routine infrastructure maintenance. Maintainer attention here is low-risk but would improve the project's dependency freshness posture.

---

**Digest Summary:** NullClaw is in a **low-activity maintenance phase**. No releases, bugs, features, or community debates were recorded today. The single open PR (#956) is a routine Alpine bump awaiting review. Project health is **stable with flat velocity**.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-08

---

## 1. Today's Overview

IronClaw saw moderate activity on 2026-09-08, with 1 open issue and 4 open pull requests updated in the last 24 hours. No new releases were published. Development activity is concentrated in the WebUI layer, where a core contributor (italic-jinxin) has advanced four related PRs addressing slash-command UX refinements — command card height preservation, metadata alignment, dismissal actions, and keyboard navigation visibility. A separate issue (#8081) continues tracking daily benchmark failure taxonomy, indicating ongoing quality assurance efforts around model evaluation. Overall, the project is in a steady maintenance-and-polish phase with no critical blockers reported today.

---

## 2. Releases

No new releases were published during this period.

---

## 3. Project Progress

**No PRs were merged or closed today.** Four open pull requests are under active review, all authored by core contributor `italic-jinxin` and targeting WebUI improvements:

- **[PR #8068](https://github.com/nearai/ironclaw/pull/8068)** — Keeps the active slash command visible during keyboard navigation; includes regression tests and a standalone Chromium POC.
- **[PR #8069](https://github.com/nearai/ironclaw/pull/8069)** — Adds dismiss actions to command result cards (success, command-list, fallback, denial), threaded through `Chat` → `MessageList` → `MessageBubble`.
- **[PR #8070](https://github.com/nearai/ironclaw/pull/8070)** — Replaces variable-width flex rows with a responsive grid in the slash-command menu for consistent title/description alignment.
- **[PR #8071](https://github.com/nearai/ironclaw/pull/8071)** — Prevents structured command-result cards from shrinking inside the transcript flex column; extends protection to inline notices and denial results.

These four PRs form a coherent UX improvement wave focused on the slash-command interface. All are tagged **low risk** and **core-contributor** scope, suggesting they are well-scoped and review-ready.

---

## 4. Community Hot Topics

| Item | Type | Activity | Link |
|------|------|----------|------|
| Daily ironclaw failure taxonomy — 2026-09-07 | Issue | 0 comments, 0 👍 | [#8081](https://github.com/nearai/ironclaw/issues/8081) |
| fix(webui): preserve command result card height | PR | 0 comments, 0 👍 | [#8071](https://github.com/nearai/ironclaw/pull/8071) |
| fix(webui): align slash-command metadata | PR | 0 comments, 0 👍 | [#8070](https://github.com/nearai/ironclaw/pull/8070) |
| fix(webui): add dismiss actions to command result cards | PR | 0 comments, 0 👍 | [#8069](https://github.com/nearai/ironclaw/pull/8069) |
| fix(webui): keep the active slash command visible | PR | 0 comments, 0 👍 | [#8068](https://github.com/nearai/ironclaw/pull/8068) |

**Analysis:** No item has attracted community comments or reactions yet. The dominant topic is the **slash-command WebUI UX overhaul** — four tightly related PRs from a single core contributor signal a coordinated effort to harden the command interface. The failure taxonomy issue (#8081) reflects automated benchmarking infrastructure; its lack of engagement suggests it is a machine-generated report rather than a community-driven discussion. Underlying need: users interacting with slash commands are experiencing layout instability (shrinking cards, hidden selections, misaligned metadata) and a lack of dismiss controls — all legitimate UX pain points for a chat-based agent interface.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| Minor | [#8071](https://github.com/nearai/ironclaw/pull/8071) | Command-result cards shrink inside the transcript flex column, degrading readability | PR #8071 (open) |
| Minor | [#8068](https://github.com/nearai/ironclaw/pull/8068) | Active slash-command option scrolls out of view during keyboard navigation | PR #8068 (open) |
| Minor | [#8070](https://github.com/nearai/ironclaw/pull/8070) | Slash-command metadata (titles/descriptions) misaligned due to variable-width flex rows | PR #8070 (open) |
| Minor | [#8069](https://github.com/nearai/ironclaw/pull/8069) | No way to dismiss ephemeral command-result cards | PR #8069 (open) |

**Assessment:** No crashes, regressions, or high-severity bugs reported today. All identified issues are **minor UI/UX problems** in the WebUI slash-command module, and each has a corresponding open PR from a core contributor. The benchmark failure data in #8081 references "genuine model-quality numeric errors" in the OfficeQA suite (DeepSeek-V4-Flas), which is a **model-performance** concern rather than an IronClaw codebase bug — likely outside the immediate fix scope.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Analysis |
|--------|--------|----------|
| Dismissable command-result cards | PR #8069 | Users need control over ephemeral UI elements; likely to ship with the next WebUI patch |
| Responsive slash-command menu | PR #8070, #8068 | Strong signal that keyboard and pointer navigation in the command palette are roadmap priorities |
| Stable card layout in transcript | PR #8071 | Suggests ongoing investment in transcript readability — likely part of a broader WebUI polish cycle |

**Prediction:** These four PRs are small, low-risk, and from a core contributor — they are strong candidates for inclusion in the **next minor WebUI release**. No new feature requests from external contributors were observed today.

---

## 7. User Feedback Summary

**Pain points identified today:**

1. **Command-result cards collapse unexpectedly** in the chat transcript, making results hard to read — users accumulate results that visually shrink rather than scroll naturally.
2. **Slash-command menu lacks navigation stability** — keyboard-selected items can scroll out of view, and long command names truncate awkwardly on narrow screens.
3. **No dismissal mechanism for ephemeral command results** — once a command result appears, users cannot remove it, cluttering the conversation view.
4. **Metadata alignment inconsistency** — command titles and descriptions are not vertically aligned across desktop and mobile viewports.

**Satisfaction indicators:** No positive feedback or praise was observed in today's activity. Engagement (comments, reactions) is near zero across all items, suggesting either a quiet contributor community or that these issues have not yet reached end-user visibility.

**Use cases implied:** Real-time agent chat interactions where slash commands trigger structured result cards (success, denial, fallback) that users expect to manage within a flowing conversation transcript.

---

## 8. Backlog Watch

| Item | Age | Risk | Note |
|------|-----|------|------|
| [#8081](https://github.com/nearai/ironclaw/issues/8081) — Daily failure taxonomy | ~1 day | Low | Automated benchmark report; no human engagement yet. Monitor for recurring failure patterns. |
| PRs #8068–#8071 | ~4 days open | Low | All created 2026-09-04, still open after 4 days. Not overdue, but no review activity reported. Worth checking if maintainers are actively reviewing. |

**Recommendation:** The four WebUI PRs have been open for approximately 4 days with no merge or review comments visible. While low risk and well-scoped, their delay warrants a gentle maintainer nudge. The benchmark taxonomy issue is routine but should be monitored for trends in OfficeQA numeric errors that may indicate a deeper model-integration issue.

---

**Project Health Verdict:** 🟢 **Stable** — Low-severity UI improvements in flight, no critical bugs, no release activity. Development is focused and coherent.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-09-08

## 1. Today's Overview

LobsterAI saw moderate development activity on 2026-09-07, with **7 PRs updated** in the last 24 hours (2 open, 5 closed/merged) and **no new issues** reported. No releases were published. The project appears to be in a steady maintenance-and-evolution phase — focused on stabilizing the in-app browser (OpenClaw), improving the renderer UI (task sorting, group folding), and patching platform-specific quirks on Windows and macOS. Zero new issues in 24 hours suggests no critical regressions surfaced today.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

**Merged / Closed PRs today (5):**

| PR | Area | Summary |
|---|---|---|
| [#2620](https://github.com/netease-youdao/LobsterAI/pull/2620) | Platform / Installer | Fixed jagged CJK text in the NSIS Windows installer by switching from legacy bitmap fonts (SimSun, PMingLiU, MS PGothic, Gulim at 9 pt) to modern Windows 10+ system UI fonts via `SetFont /LANG`. |
| [#2623](https://github.com/netease-youdao/LobsterAI/pull/2623) | Renderer / Cowork / Docs | Major UX upgrade: task priority sorting, grid-based group folding, independent pagination per group/file, improved session-change notifications, cursor/validation hardening, macOS dev-mode Dock icon fix, and added regression tests. |
| [#2621](https://github.com/netease-youdao/LobsterAI/pull/2621) | OpenClaw / Browser | Fixed a `TypeError` in OpenClaw's `scrollIntoView` action where element refs were treated as strings instead of DOM nodes, eliminating spurious "Uncaught" error banners in the in-app browser. |
| [#2622](https://github.com/netease-youdao/LobsterAI/pull/2622) | OpenClaw / Main | Unified gateway subprocess startup to use `spawn` in Node mode, ensuring environment inheritance by worker processes; added tests and fail-fast on postinstall patch failure. |
| [#2617](https://github.com/netease-youdao/LobsterAI/pull/2617) | Browser / Artifacts | Improved in-app browser login UX (dismissible feedback, credential settings persistence) and replaced the page dropdown with a scrollable tab strip, adjacent-tab selection on close, and a new blank-tab action. |

**Open PRs today (2):**

- [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Dependabot: bump `electron` 40.2.1 → 44.2.0 and `electron-builder` (open since April 2026).
- [#1067](https://github.com/netease-youdao/LobsterAI/pull/1067) — Stop auto-creating `[OpenClaw]` Cowork sessions on main agent heartbeat (stale, open since March 2026).

---

## 4. Community Hot Topics

**Most discussed / reacted items today:**

| Item | Type | Comments / Reactions | Link |
|---|---|---|---|
| [#2623](https://github.com/netease-youdao/LobsterAI/pull/2623) | PR (merged) | 0 👍 | Task priority sorting + group folding — the largest feature PR of the day |
| [#2617](https://github.com/netease-youdao/LobsterAI/pull/2617) | PR (merged) | 0 👍 | In-app browser tab & login UX overhaul |
| [#1067](https://github.com/netease-youdao/LobsterAI/pull/1067) | PR (open, stale) | 0 👍 | Long-standing request to stop phantom `[OpenClaw]` session creation |

**Analysis:** The dominant theme is **in-app browser (OpenClaw) polish** — two browser-related PRs merged today (#2621, #2617) and one stale fix still open (#1067). Users clearly need a more reliable, less intrusive browser experience inside LobsterAI. The task-grouping feature (#2623) signals growing demand for better local-artifact organization as the tool's usage scope expands.

---

## 5. Bugs & Stability

| Severity | Bug / Fix | PR | Status |
|---|---|---|---|
| **Medium** | OpenClaw `scrollIntoView` throws `TypeError` — element refs passed as strings, leaving error banners | [#2621](https://github.com/netease-youdao/LobsterAI/pull/2621) | ✅ Merged |
| **Low** | macOS dev-mode gateway spawns an extra Dock icon | [#2623](https://github.com/netease-youdao/LobsterAI/pull/2623) | ✅ Merged |
| **Low** | Windows installer renders CJK text with jagged legacy fonts at any DPI | [#2620](https://github.com/netease-youdao/LobsterAI/pull/2620) | ✅ Merged |
| **Medium** | Gateway subprocess may not inherit Node environment correctly, causing worker startup failures | [#2622](https://github.com/netease-youdao/LobsterAI/pull/2622) | ✅ Merged |

No new bug reports (issues) were filed today. All four bugs identified above have merging fixes, indicating a healthy triage-and-resolve cadence.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Interpretation |
|---|---|---|
| **Task priority sorting & group folding** | [#2623](https://github.com/netease-youdao/LobsterAI/pull/2623) (merged) | Already shipped — confirms roadmap focus on artifact management UX |
| **In-app browser tab strip & improved login flow** | [#2617](https://github.com/netease-youdao/LobsterAI/pull/2617) (merged) | Browser UX is a current priority; expect further tab/session hardening |
| **Stop auto-creating `[OpenClaw]` sessions** | [#1067](https://github.com/netease-youdao/LobsterAI/pull/1067) (open, stale) | User-requested; likely to land in next patch once stale tag is addressed |
| **Electron 44 upgrade** | [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) (open since Apr 2026) | Long-backlog dependency bump; would unlock modern Electron APIs and security fixes |

**Prediction:** The next release will likely include the task-grouping feature (#2623) as a highlight, along with the OpenClaw browser fixes. The Electron 44 upgrade (#1277) is a strong candidate for inclusion if merge conflicts are resolved.

---

## 7. User Feedback Summary

**Pain points addressed today:**
- **Jagged CJK installer text on Windows** — users on non-Latin locales reported poor visual quality; now fixed with modern system fonts (#2620).
- **Phantom `[OpenClaw]` sessions** — users deleting auto-created Cowork sessions saw them reappear after each heartbeat; fix is drafted (#1067) but still open.
- **Browser `TypeError` on `scrollIntoView`** — in-app browser actions silently failed with an "Uncaught" banner, confusing users (#2621).
- **macOS Dock clutter in dev mode** — an extra icon for the gateway process annoyed developers (#2623).
- **Cluttered browser UI** — the old page dropdown was replaced with a scrollable tab strip for better multi-tab workflows (#2617).

**Satisfaction indicators:** No new issues filed today; multiple bug fixes merged the same day they were tracked. The absence of open issues combined with active PR closure suggests a responsive maintainership cycle.

---

## 8. Backlog Watch

| Item | Open Since | Severity | Why It Matters | Link |
|---|---|---|---|---|
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | 2026-04-02 (~5 months) | Medium | Electron 40 → 44 upgrade brings security patches, modern APIs, and improved stability; long stall risks falling further behind. | [PR #1277](https://github.com/netease-youdao/LobsterAI/pull/1277) |
| [#1067](https://github.com/netease-youdao/LobsterAI/pull/1067) | 2026-03-30 (~5 months) | Low–Medium | Auto-created `[OpenClaw]` sessions are a persistent user annoyance; the fix is ready but tagged stale. | [PR #1067](https://github.com/netease-youdao/LobsterAI/pull/1067) |

Both PRs have valid, tested changes pending maintainer review. Reviving these would address two of the most commonly felt friction points: dependency freshness and session noise.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-09-08

---

## 1. Today's Overview

Moltis (moltis-org/moltis) shows **low but focused activity** today, with one open pull request and no new issues or releases in the past 24 hours. The sole activity centers on a bug fix for the `active_hours` cron time-window logic, which suggests the maintainers are actively addressing correctness in scheduling behavior. No closed PRs or merged changes occurred today, and no new issues were opened. Overall, the project appears stable with a targeted improvement underway rather than a wave of urgent problems.

---

## 2. Releases

**No new releases today.** There is no latest release data to report at this time.

---

## 3. Project Progress

**Open PRs today: 1 | Merged/Closed today: 0**

- **[PR #1262](https://github.com/moltis-org/moltis/pull/1262)** — *fix(cron): treat active_hours end="24:00" as end-of-day* by **atirna** (opened 2026-09-07). This PR addresses a bug where `chrono`'s `%H` format parser rejects hour `24`, causing the `is_within_active_hours` function to fail-parsing the `end = "24:00"` value. Because the default configured window is `start = "08:00"`, `end = "24:00"`, the parse failure triggered a fail-open path that incorrectly treated the schedule as active at every hour — a significant correctness issue for time-windowed scheduling. The PR is still **open** and awaiting review.

---

## 4. Community Hot Topics

No issues or PRs have accumulated comments or reactions today. The community remains quiet on public discussion threads, with activity concentrated in the single open PR noted above.

- **[PR #1262](https://github.com/moltis-org/moltis/pull/1262)** — The only active discussion item today. The `active_hours` time-window bug directly impacts users relying on cron-style scheduling with the documented default configuration, making this the most salient topic for the community.

---

## 5. Bugs & Stability

**One bug-related item today, severity: Medium-High.**

| # | Issue | Severity | Fix PR | Status |
|---|-------|----------|--------|--------|
| 1 | `active_hours` end="24:00" incorrectly parsed, causing always-active schedule | Medium-High | [PR #1262](https://github.com/moltis-org/moltis/pull/1262) | Open |

The bug causes the cron scheduler to treat the default `08:00–24:00` active window as perpetually active due to a `chrono` parsing failure. No other bugs, crashes, or regressions were reported today.

---

## 6. Feature Requests & Roadmap Signals

**No new feature requests were opened today.** The current PR activity is purely corrective (bug fix), with no feature enhancements proposed. No roadmap signals can be inferred from today's data.

---

## 7. User Feedback Summary

Today's activity reflects a **single user-reported pain point**: the `active_hours` configuration did not work as documented when `end` was set to `"24:00"`, a value that appears in the project's own default config. This suggests the bug has been affecting users relying on the standard time-window behavior for scheduled tasks. The fix-by-author **atirna** indicates community-driven maintenance is functional, though the PR remains unreviewed.

---

## 8. Backlog Watch

**No long-unanswered items flagged today** due to zero new issues and no data on previously open backlog items. The single open PR (#1262) was created yesterday and is still awaiting maintainer review — worth monitoring for timely merging given the correctness impact of the bug.

---

*Data source: GitHub API (moltis-org/moltis), snapshot as of 2026-09-08.*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-09-08

## 1. Today's Overview

CoPaw (agentscope-ai/QwenPaw) shows **very high development velocity** on 2026-09-08, with 34 issues updated and 36 PRs updated in the past 24 hours. The project is in an active stabilization phase following the v2.2.0 release cycle, with a heavy concentration of bug reports tied to PDF/media handling, context management, and UI regressions. No new releases were published today. The issue-to-PR ratio (~1:1) suggests the team is actively triaging and responding.

---

## 2. Releases

**None.** The latest reported version in open issues remains **v2.2.0** (with v2.1.0 and v2.0.1 still referenced in older reports). No changelog or migration notes to highlight today.

---

## 3. Project Progress

### Closed/Merged PRs Today
| PR | Description |
|----|-------------|
| [#6936](https://github.com/agentscope-ai/QwenPaw/pull/6936) | **fix(providers):** coerce string-typed tool args emitted as JSON numbers — resolves [Issue #6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) |
| [#7499](https://github.com/agentscope-ai/QwenPaw/pull/7499) | **fix(console):** unify nav & theme-toggle icons with Spark line series — resolves [Issue #7376](https://github.com/agentscope-ai/QwenPaw/issues/7376) |
| [#7530](https://github.com/agentscope-ai/QwenPaw/pull/7530) | **test(console):** expand console unit tests (+245 cases, +5.02pp statement coverage) |

### Notable Open PRs Advancing
- [#7621](https://github.com/agentscope-ai/QwenPaw/pull/7621) — **fix:** handle PDF DataBlocks for text-only models (direct response to [#7597](https://github.com/agentscope-ai/QwenPaw/issues/7597) / [#7617](https://github.com/agentscope-ai/QwenPaw/issues/7617))
- [#7610](https://github.com/agentscope-ai/QwenPaw/pull/7610) — **fix(console):** prevent chat submissions from bypassing the queue
- [#7611](https://github.com/agentscope-ai/QwenPaw/pull/7611) — **fix(console):** correct BiDi rendering for mixed RTL/LTR text
- [#7598](https://github.com/agentscope-ai/QwenPaw/pull/7598) — **fix(shell):** detach child stdin from interactive console
- [#7616](https://github.com/agentscope-ai/QwenPaw/pull/7616) — **refactor(memory):** migrate ADBPG and PowerContext to plugins
- [#7613](https://github.com/agentscope-ai/QwenPaw/pull/7613) — **feat(memory):** add OpenViking long-term memory backend

---

## 4. Community Hot Topics

| Issue | Comments | Theme |
|-------|----------|-------|
| [#7579](https://github.com/agentscope-ai/QwenPaw/issues/7579) — Model reply vanishes from context | 6 | Persistent assistant messages missing on subsequent turns |
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) — ReMe embedding/indexing fails silently | 5 | Background memory job crashes; new memories not indexed |
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) — RetryChatModel hardcoded 32768 context | 5 | `context_size` fallback forces ALL models to 32k, causing CONTEXT_UNFIT errors above ~31k tokens |
| [#7589](https://github.com/agentscope-ai/QwenPaw/issues/7589) — Heartbeat cron feedback loop | 4 | Duplicate message pile-up; agent unresponsive for ~2 hours |
| [#7597](https://github.com/agentscope-ai/QwenPaw/issues/7597) | 4 | Tool-returned image/PDF sent as bare base64 triggers 400 errors on OpenAI-compat endpoints |

**Analysis:** The community's top concerns cluster around **context management integrity** (#7579, #7576), **memory system reliability** (#7469), and **media block compatibility** (#7597). These are systemic issues affecting agent reliability under production workloads — not edge-case bugs. The high comment counts signal that users are hitting these in real deployments.

---

## 5. Bugs & Stability

### Critical / High Severity
| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#7589](https://github.com/agentscope-ai/QwenPaw/issues/7589) | Heartbeat cron causes duplicate message pile-up; agent unresponsive | — |
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | Hardcoded 32768 context_size fallback breaks models needing larger windows | — |
| [#7597](https://github.com/agentscope-ai/QwenPaw/issues/7597) | Image/PDF binary from tools → bare base64 → 400 on OpenAI-compat endpoints | [#7621](https://github.com/agentscope-ai/QwenPaw/pull/7621) (open) |
| [#7617](https://github.com/agentscope-ai/QwenPaw/issues/7617) | Session with PDF DataBlock permanently breaks text-only endpoints (GLM 400 code 1210) | [#7621](https://github.com/agentscope-ai/QwenPaw/pull/7621) (open) |
| [#7567](https://github.com/agentscope-ai/QwenPaw/issues/7567) | Task stop appears successful but execution continues; causes 409 conflict | — |

### Medium Severity
| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | ReMe background embedding job fails with `Dependency as_embedding:default accessed before start()` | — |
| [#7156](https://github.com/agentscope-ai/QwenPaw/issues/7156) | Ollama embedding health check times out at 5s despite pre-warmed backend (actual 10.4s) | — |
| [#7587](https://github.com/agentscope-ai/QwenPaw/issues/7587) | OpenAI-compat provider gets Cloudflare 403 from WUSRouter | — |
| [#6541](https://github.com/agentscope-ai/QwenPaw/issues/6541) | Context compression injects `[context compressed]` with `role=user` instead of `role=system` (DeepSeek) | — |
| [#7604](https://github.com/agentscope-ai/QwenPaw/issues/7604) | LLM stream idle timeout hardcoded to 30s; unconfigurable via WebUI/envs | — |
| [#6885](https://github.com/agentscope-ai/QwenPaw/issues/6885) | Console UI crashes on Chinese IME `compositionEnd` during agent run | — |

### Low Severity
| Issue | Summary |
|-------|---------|
| [#7242](https://github.com/agentscope-ai/QwenPaw/issues/7242) | Dashboard takes 6+ min to load with 74 agents on single instance |
| [#7006](https://github.com/agentscope-ai/QwenPaw/issues/7006) | Language options inconsistent between dropdown and settings gear |
| [#6948](https://github.com/agentscope-ai/QwenPaw/issues/6948) | Admin console displays message timestamps in UTC instead of user-configured timezone |
| [#3328](https://github.com/agentscope-ai/QwenPaw/issues/3328) | Extra sidebar toggle appears at certain zoom levels on Console chat page |

**Stability Assessment:** The project has **moderate stability risk** at current state. The PDF/media handling bugs (#7597, #7617) and the context compression role bug (#6541) affect data integrity and are likely to surface in production workflows. The fix PR [#7621](https://github.com/agentscope-ai/QwenPaw/pull/7621) is a positive signal but remains unmerged.

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Request | Likelihood |
|------------|---------|------------|
| [#7608](https://github.com/agentscope-ai/QwenPaw/issues/7608) | DingTalk channel: support interactive card callbacks in stream mode | Medium — niche channel, but actively requested |
| [#7613](https://github.com/agentscope-ai/QwenPaw/pull/7613) | OpenViking long-term memory backend | High — PR already open, follows existing memory abstraction |
| [#7502](https://github.com/agentscope-ai/QwenPaw/pull/7502) | Console sidebar & settings redesign | High — already in progress, significant UI overhaul |
| [#7482](https://github.com/agentscope-ai/QwenPaw/pull/7482) | Agent Kanban i18n (Chinese + English) | High — PR open, localization effort aligns with user base |
| [#7609](https://github.com/agentscope-ai/QwenPaw/pull/7609) | Expose skill versions & validate declared dependencies | Medium — improves workspace/Pool API maturity |
| [#7526](https://github.com/agentscope-ai/QwenPaw/pull/7526) | Protected execution contract for workspace prompts | Medium — security-focused, addresses agent sandboxing needs |
| [#7616](https://github.com/agentscope-ai/QwenPaw/pull/7616) | Migrate ADBPG & PowerContext memory backends to plugins | High — completes plugin migration strategy |
| [#6399](https://github.com/agentscope-ai/QwenPaw/pull/6399) | Reranker UI config panel in ReMeLightMemoryCard | Medium — complements existing reranker backend |
| [#7588](https://github.com/agentscope-ai/QwenPaw/issues/7588) | Restore v2.1.0 manual path input for working directory | Medium — UI regression reversal, community feedback strong |

**Prediction:** The next release (likely v2.2.1 or v2.3.0) will ship the **Console sidebar redesign** (#7502), **PDF/media block fixes** (#7621), and the **memory backend plugin migration** (#7616) as core improvements. The OpenViking memory backend (#7613) may land as a plugin rather than core.

---

## 7. User Feedback Summary

**Pain Points:**
1. **Context loss & media incompatibility** — Users report models "forgetting" their own replies and text-only endpoints breaking when PDFs appear in session history. This is the #1 friction point.
2. **UI regression in v2.2.0** — The removal of manual path input for working directory (#7588, #7601) is generating significant frustration from power users who rely on deep directory navigation.
3. **Silent memory failures** — ReMe embedding/indexing jobs fail without surfacing errors to users (#7469), leading to data loss in long-term memory.
4. **Hardcoded limits** — Multiple timeout and context-size values are hardcoded with no config path (#7576, #7604, #7156), forcing users to patch source or accept degraded performance.
5. **Stop-not-stopping** — Task cancellation appears successful but continues executing (#7567), wasting resources and causing conflicts.

**Satisfaction Signals:**
- Positive reception of the Kanban i18n (#7482) and sidebar redesign (#7502) efforts.
- Users appreciate the rapid response to bug reports (e.g., #6936 merging quickly after #6839 was filed).
- The open invitation for third-party plugin/skill discussion (#7615) shows community engagement.

---

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|------------------------|
| [#7576](https://github.com/agentscope-ai/QwenPaw/issues/7576) | 3 days | Hardcoded context_size fallback affects ALL models above ~31k tokens; no fix PR yet |
| [#7589](https://github.com/agentscope-ai/QwenPaw/issues/7589) | 2 days | Heartbeat feedback loop causes agent unresponsiveness; severity rated High by reporter |
| [#7579](https://github.com/agentscope-ai/QwenPaw/issues/7579) | 2 days | Most-commented open issue; model reply persistence bug with no apparent fix in progress |
| [#7469](https://github.com/agentscope-ai/QwenPaw/issues/7469) | 7 days | ReMe background job failure; silent data loss in long-term memory |
| [#6541](https://github.com/agentscope-ai/QwenPaw/issues/6541) | ~2.5 months | Closed but root cause may persist — context compression role mismatch for DeepSeek |
| [#6885](https://github.com/agentscope-ai/QwenPaw/issues/6885) | ~1 month | Console unusable with Chinese IME during agent runs; no fix PR visible |
| [#7242](https://github.com/agentscope-ai/QwenPaw/issues/7242) | ~15 days | Dashboard 6+ min load time with 74 agents; scalability concern for production deployments |

**Notable PRs pending review:**
- [#7

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-09-08

## 1. Today's Overview

ZeroClaw shows **high development velocity** with 37 issues and 50 PRs updated in the last 24 hours. The project is in a critical stabilization phase: 6 issues were closed today, but the majority of activity centers on P1-severity bugs in the runtime, daemon, and ACP channel layers — many introduced by recent multi-session and streaming work. No new releases were published today, suggesting the team is consolidating fixes before the next version bump. Community contributions remain strong, with distinguished and trusted contributors actively driving security and provider-fix PRs.

## 2. Releases

**No new releases today.** The last 24h saw 0 new versions published. The team appears to be holding the current line while addressing a cluster of P1 runtime and TUI bugs that block stable workflows.

## 3. Project Progress

**Closed/Merged Today (6 issues resolved):**

| # | Title | Author |
|---|-------|--------|
| [#8720](https://github.com/zeroclaw-labs/zeroclaw/issues/8720) | Disable cachePoint for Bedrock Nova 2 Lite | ngamradt |
| [#10670](https://github.com/zeroclaw-labs/zeroclaw/issues/10670) | heartbeat.target rejects composite key | metalmon |
| [#10660](https://github.com/zeroclaw-labs/zeroclaw/issues/10660) | Third Anthropic cache breakpoint on previous turn | Audacity88 |
| [#10688](https://github.com/zeroclaw-labs/zeroclaw/issues/10688) | WhatsApp Web voice notes never transcribed | badbat75 |
| [#10326](https://github.com/zeroclaw-labs/zeroclaw/issues/10326) | Reliable streaming errors report wrong model | Audacity88 |
| [#10693](https://github.com/zeroclaw-labs/zeroclaw/issues/10693) | ZeroCode silently ignores Enter while Connected | Audacity88 |

**Key open PRs advancing today:**

- [#10214](https://github.com/zeroclaw-labs/zeroclaw/pull/10214) — Log entry-count rotation and multi-segment log queries (NiuBlibing)
- [#10450](https://github.com/zeroclaw-labs/zeroclaw/pull/10450) — Stream webhook chat turns over SSE (jstar0)
- [#9535](https://github.com/zeroclaw-labs/zeroclaw/pull/9535) — Anchor context compaction to model window ratio (NiuBlibing)
- [#10637](https://github.com/zeroclaw-labs/zeroclaw/pull/10637) — Consolidate WS memory on agent's own provider (NiuBlibing)
- [#10712](https://github.com/zeroclaw-labs/zeroclaw/pull/10712) — Trust platform roots for outbound WebSocket TLS (askldjd)

## 4. Community Hot Topics

**Most-discussed Issues (by comment count):**

1. **[Issue #8720](https://github.com/zeroclaw-labs/zeroclaw/issues/8720)** — 12 comments · *Disable cachePoint for Bedrock Nova 2 Lite* (✅ Closed)
   - Users need per-model cache control; the Bedrock Nova 2 Lite model throws random caching errors that operators cannot currently disable via config.

2. **[Issue #10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230)** — 6 comments · *Daemon startup/reload stack overflow during agent init* (🔴 P1, open)
   - Quickstart config application while daemon is running can crash the Tokio runtime. Points to a deeper lifecycle-race issue in zerocode/daemon interaction.

3. **[Issue #9333](https://github.com/zeroclaw-labs/zeroclaw/issues/9333)** — 4 comments · *Failed ACP turns disappear after session switch* (🔴 P1, open)
   - Data loss when switching sessions mid-turn; the live transcript drops entire failed turns. Signals that session-state management in ACP is fragile under multi-session workloads.

4. **[Issue #10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408)** — 3 comments · *Second message during active turn spawns parallel run* (🔴 P1, open)
   - Concurrency bug: rapid user input during an ongoing turn creates duplicate agent runs and duplicate replies. Directly impacts ACP workflow reliability.

5. **[Issue #10121](https://github.com/zeroclaw-labs/zeroclaw/issues/10121)** — 3 comments · *Partial turns disappear if process exits before completion* (🔴 P1, open)
   - Severity S0 (data loss). Streaming assistant text and tool results are lost on abrupt daemon/TUI shutdown. Critical for production reliability.

**Underlying theme:** The community is hitting edge cases in the new multi-session ACP pipeline and daemon lifecycle. The high comment counts on runtime/daemon bugs suggest these are blocking real workflows, not theoretical concerns.

## 5. Bugs & Stability

**Today's reported bugs, ranked by severity:**

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| 🔴 S0 / P1 | [#10121](https://github.com/zeroclaw-labs/zeroclaw/issues/10121) | Partial turns lost on process exit — data loss | None yet |
| 🔴 S1 / P1 | [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | Daemon stack overflow on Quickstart apply | None yet |
| 🔴 S1 / P1 | [#9333](https://github.com/zeroclaw-labs/zeroclaw/issues/9333) | Failed ACP turns vanish after session switch | None yet |
| 🔴 S1 / P1 | [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | Parallel runs from rapid messages → duplicate work | None yet |
| 🔴 S1 / P1 | [#10659](https://github.com/zeroclaw-labs/zeroclaw/issues/10659) | Budget-exceeded turns lose visible progress after restore | None yet |
| 🔴 S1 / P1 | [#9940](https://github.com/zeroclaw-labs/zeroclaw/issues/9940) | Cron delivery channel resolves wrong alias | None yet |
| 🟡 S2 / P1 | [#10115](https://github.com/zeroclaw-labs/zeroclaw/issues/10115) | Tool-result truncation invisible outside model context | None yet |
| 🟡 S2 / P2 | [#10689](https://github.com/zeroclaw-labs/zeroclaw/issues/10689) | Telegram voice replies skipped when text starts with `[` | None yet |
| 🟡 S2 / P2 | [#10697](https://github.com/zeroclaw-labs/zeroclaw/issues/10697) | ACP transcript drops pre-tool-call assistant text | None yet |
| 🟢 S3 / P2 | [#10690](https://github.com/zeroclaw-labs/zeroclaw/issues/10690) | Integrations page slugifies display name instead of family key | None yet |
| 🟢 S3 / P3 | [#10326](https://github.com/zeroclaw-labs/zeroclaw/issues/10326) | Reliable streaming errors report requested vs. pinned model | ✅ Closed |

**Notable regression pattern:** Multiple bugs ([#9333](https://github.com/zeroclaw-labs/zeroclaw/issues/9333), [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408), [#10697](https://github.com/zeroclaw-labs/zeroclaw/issues/10697)) point to the ACP/session-multiplexing code path as a source of regressions. The fix for [#10637](https://github.com/zeroclaw-labs/zeroclaw/pull/10637) (WS memory consolidation on correct provider) may partially address one root cause.

## 6. Feature Requests & Roadmap Signals

| # | Title | Author | Likelihood for Next Release |
|---|-------|--------|----------------------------|
| [#10708](https://github.com/zeroclaw-labs/zeroclaw/issues/10708) | Active-response steering on OpenAI Responses WebSockets | IftekharUddin | Medium — depends on adapter work |
| [#10707](https://github.com/zeroclaw-labs/zeroclaw/issues/10707) | Bounded programmatic tool calling via OpenAI Responses | IftekharUddin | Medium |
| [#10706](https://github.com/zeroclaw-labs/zeroclaw/issues/10706) | Preserve opaque reasoning state across Responses call paths | IftekharUddin | Medium |
| [#10705](https://github.com/zeroclaw-labs/zeroclaw/issues/10705) | Max reasoning effort for compatible OpenAI models | IftekharUddin | High — small config change |
| [#10704](https://github.com/zeroclaw-labs/zeroclaw/issues/10704) | Async function tools with OpenAI Responses | IftekharUddin | Medium |
| [#10663](https://github.com/zeroclaw-labs/zeroclaw/issues/10663) | Configurable 1-hour prompt-cache TTL for Anthropic | Audacity88 | High — directly addresses cost concerns |
| [#10606](https://github.com/zeroclaw-labs/zeroclaw/issues/10606) | Sanitize component errors in unauthenticated health responses | Audacity88 | High — security hardening |
| [#10640](https://github.com/zeroclaw-labs/zeroclaw/pull/10640) | Passive Telegram group context | rifuki | Medium — opt-in feature |
| [#10214](https://github.com/zeroclaw-labs/zeroclaw/pull/10214) | Log entry-count rotation + multi-segment queries | NiuBlibing | High — observability improvement |
| [#10450](https://github.com/zeroclaw-labs/zeroclaw/pull/10450) | Stream webhook turns over SSE | jstar0 | High — API completeness |

**Signal:** The OpenAI Responses adapter work (issues #10704–#10708) is a coordinated feature push by IftekharUddin, suggesting the next release will significantly expand OpenAI-native protocol support. Anthropic cache configurability (#10663) is also high-priority given cost-optimization demands.

## 7. User Feedback Summary

**Pain points emerging from today's activity:**

- **Cache reliability:** Users are hitting Bedrock Nova cache errors (#8720) and Anthropic cache slot exhaustion (#10662, #10660). The current 2-marker, ephemeral-only cache strategy is insufficient for production workloads. Operators want per-model and per-TTL control.
- **ACP session fragility:** Multiple reports of data loss during session switches (#9333), partial turn disappearance (#10121), and parallel-run duplication (#10408) indicate the multi-session ACP pipeline needs stabilization before it can be recommended for production.
- **Daemon lifecycle bugs:** Stack overflow on Quickstart apply (#10230) and budget-exceeded progress loss (#10659) suggest the daemon's restart and recovery paths are not yet robust.
- **Telegram/WhatsApp channel quirks:** Voice note transcription failure on WhatsApp (#10688) and silent skipping of Telegram replies starting with `[` (#10689) point to incomplete channel-provider wiring.
- **Cost tracking is misleading:** Issue [#10700](https://github.com/zeroclaw-labs/zeroclaw/issues/10700) reveals that all cost records for a daemon lifetime share the same session ID, making per-conversation spend analysis impossible — a significant gap for multi-tenant or cost-conscious users.

**Satisfaction signals:** Active contributors are responding quickly (many issues updated within hours), and several security-focused fixes (#9410, #10337, #9977) show the maintainers are prioritizing operator trust.

## 8. Backlog Watch

**Long-open issues requiring maintainer attention:**

| # | Created | Days Open | Title | Risk |
|---|---------|-----------|-------|------|
| [#8966](https://github.com/zeroclaw-labs/zeroclaw/issues/8966) | 2026-07-11 | ~59 | Context meter ceiling was wrong — used trim budget instead of model window | High |
| [#9419](https://github.com/zeroclaw-labs/zeroclaw/issues/9419) | 2026-07-26 | ~44 | Rotate live credentials after rate limits (do-not-merge label) | High |
| [#9272](https://github.com/zeroclaw-labs/zeroclaw/issues/9272) | 2026-07-23 | ~47 | Handle Anthropic refusals with fallback notices | High |
| [#9283](https://github.com/zeroclaw-labs/zeroclaw/issues/9283) | 2026-07-23 | ~47 | Decompress gzip/brotli/deflate web_fetch responses (stale-candidate) | High |
| [#9940](https://github.com/zeroclaw-labs/zeroclaw/issues/9940) | 2026-08-12 | ~27 | Cron delivery channel resolves wrong alias | High |
| [#10104](https://github.com/zeroclaw-labs/zeroclaw/issues/10104) | 2026-08-18 | ~21 | Hardware feature-gated tests never execute in CI | Medium |
| [#10674](https://github.com/zeroclaw-labs/zeroclaw/issues/10674) | — | — | Token-budget history trimming hysteresis gap (referenced in #10702) | Medium |

**Critical PRs awaiting merge:**

- [#9419](https://github.com/zeroclaw-labs/zeroclaw/pull/9419) — Credential rotation after rate limits (do-not-merge flag still active; needs maintainer resolution)
- [#9283](https://github.com/zeroclaw-labs/zeroclaw/pull/9283) — Web fetch decompression (marked stale-candidate; should be revisited)
- [#9724](https://github.com/zeroclaw-labs/zeroclaw/pull/9724) — `always_ask` surviving Full autonomy (needs maintainer review)

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*