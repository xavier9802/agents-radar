# OpenClaw Ecosystem Digest 2026-08-26

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-26 01:44 UTC

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



# OpenClaw Project Digest — 2026-08-26

---

## 1. Today's Overview

OpenClaw remains in an **intensely active** state, with 500 issues and 500 PRs touched in the last 24 hours. The project is in a release-validation cycle for **v2026.8.1 beta** (#125626), with 66 issues closed today against 434 still open/active. No new stable releases were published. The activity volume and number of P1-rated bugs suggest the current beta is exercising edge cases in subagent orchestration, SQLite durability, and channel-specific delivery paths. Maintainer engagement is high, with multiple PRs ready for review.

---

## 2. Releases

**No new releases.** The project is currently validating **v2026.8.1-beta.3** (commit `5831b80`). Beta feedback issue #125626 tracks known issues; P0 SQLite corruption (#126821) is flagged but not marked a beta release blocker by the reporter.

---

## 3. Project Progress

**PRs merged/closed today (189 total):**

- **#125471** [CLOSED] `fix(models): keep Claude CLI OAuth available in Control UI` — Resolved a Gateway-restart regression where OAuth refresh ownership was lost.
- **#121195** [CLOSED] `fix(agents): settle yielded requester completions exactly once` — Fixed a long-standing parent-subagent completion race (#121187).

**PRs advanced (open, ready for maintainer):**

- **#129386** `fix: preserve unread reminder for open sessions` — Fixes immediate unread-reset bug on active sessions.
- **#129729** `fix(agents): allow requester continuation after settle` — Addresses subagent completion drop (#129455).
- **#129728** `fix(cli): preserve structured core send failures` — Durable failure reporting follow-up to #129202.
- **#129092** `feat(audit): record admitted model routing decisions` — New audit trail for model selection.
- **#129670** `feat(secrets): agent-requested credentials the model never sees` — New secrets injection flow.
- **#116926** `fix(google): preserve stream terminals and provider tool-call identities` — Critical Google/Vertex adapter fix (high merge-risk).
- **#129486** `fix(skills): reject altered download archives before extraction` — Security fix for skill install integrity.
- **#119516** `fix(update): recover the managed gateway after a failed CLI update` — Fixes update-recovery loop (#119515).
- **#119999** `fix(gateway): fence superseded reload channel lifetimes` — Follow-up to reload-generation cancellation.

---

## 4. Community Hot Topics

| Issue | Rating | Comments | Summary |
|---|---|---|---|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 🦞 diamond lobster | 26 | Subagent completion silently lost — timeout/drain/orphan failure modes |
| [#125626](https://github.com/openclaw/openclaw/issues/125626) | 🌊 off-meta tidepool | 19 | v2026.8.1 beta feedback tracker |
| [#80319](https://github.com/openclaw/openclaw/issues/80319) | 🐚 platinum hermit | 17 | QA tool-defaults suite conflates Codex-native tools with OpenClaw parity |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | 🦞 diamond lobster | 14 | Subagent completion delivery lost on direct-announce timeout |
| [#79902](https://github.com/openclaw/openclaw/issues/79902) | 🌊 off-meta tidepool | 14 | Companion-friendly SQLite transcript seams on database-first runtime |

**Analysis:** Subagent reliability is the dominant community concern — issues #44925 and #67777 share root causes in the same delivery path. The beta validation issue (#125626) shows active user testing. SQLite runtime seams (#79902) and QA harness correctness (#80319) reflect power-user demand for observability and testing maturity.

---

## 5. Bugs & Stability

**P0 / Critical:**

| Issue | Impact | Summary |
|---|---|---|
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | crash-loop, data-loss | **SQLite corruption recurs on pristine rebuilt DBs within 15–24h** (WSL2) — 5 events in 5 days, includes "paralyzed gateway" mode |
| [#127710](https://github.com/openclaw/openclaw/issues/127710) | message-loss | prepared-model-runtime **fails closed on transient churn** — fingerprint drift wedges gateway; owner-commit race drops messages |
| [#127948](https://github.com/openclaw/openclaw/issues/127948) | message-loss | WhatsApp group replies render as **blank bubbles** when quote cache expires |
| [#126246](https://github.com/openclaw/openclaw/issues/126246) | message-loss | Telegram durable outbound deliveries **stuck in `send_attempt_started`** and lost on restart |

**P1 — High Severity:**

| Issue | Impact | Summary |
|---|---|---|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | data-loss, session-state | Subagent completion silently lost — no retry, no notification |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | session-state | Subagent completion delivery can be lost on direct-announce timeout/drain/orphan prune |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | crash-loop | **Child process leak** — `openclaw-hooks`, `bash`, `codex`, `occa` zombie accumulation |
| [#94939](https://github.com/openclaw/openclaw/issues/94939) | data-loss | 6.x state migration **leaves conversation-store SQLite empty** — breaks MS Teams proactive sends |
| [#83959](https://github.com/openclaw/openclaw/issues/83959) | crash-loop | Codex app-server startup retries exhaust before replacement is ready |
| [#111372](https://github.com/openclaw/openclaw/issues/111372) | crash-loop | macOS **infinite SIGTERM restart loop** after upgrade (2026.6.11 → 2026.7.1-2) |
| [#87928](https://github.com/openclaw/openclaw/issues/87928) | crash-loop, ux-release-blocker | macOS update leaves **manual-update loop and stale node host** |
| [#112248](https://github.com/openclaw/openclaw/issues/112248) | session-state | `@openclaw/codex` plugin fails to register on gateway boot (`TypeError: openSyncKeyedStore`) |
| [#110771](https://github.com/openclaw/openclaw/issues/110771) | session-state | WebChat persists internal records and **loses durable turn status** after upgrade |

**Fix PRs in flight:** #129729, #129386, #119516, #119999, #129486. No PRs yet addressing the SQLite corruption (#126821) or subagent completion loss (#44925/#67777).

---

## 6. Feature Requests & Roadmap Signals

| Issue | Rating | Summary |
|---|---|---|
| [#79902](https://github.com/openclaw/openclaw/issues/79902) | 🌊 off-meta tidepool | **SQLite transcript/session seams** — companion-friendly API on top of database-first runtime |
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | 🌊 off-meta tidepool | **Multi-slot memory architecture** — multiple memory providers simultaneously |
| [#56781](https://github.com/openclaw/openclaw/issues/56781) | 🌊 off-meta tidepool | **Fallback model chain** for compaction and LCM summaryModel |
| [#63930](https://github.com/openclaw/openclaw/issues/63930) | 🦞 diamond lobster | **Anthropic advisor tool** (beta server-side tool) support |
| [#67413](https://github.com/openclaw/openclaw/issues/67413) | 🐚 platinum hermit | **Per-agent dreaming configuration** — avoid MemoryMax OOM from concurrent dreaming |
| [#45758](https://github.com/openclaw/openclaw/issues/45758) | 🌊 off-meta tidepool | **YAML config file format** support alongside JSON5 |
| [#105494](https://github.com/openclaw/openclaw/issues/105494) | 🌊 off-meta tidepool | **Interactive "memory therapy"** session to resolve open questions & contradictions |
| [#62615](https://github.com/openclaw/openclaw/issues/62615) | 🌊 off-meta tidepool | **Gateway-side circuit breaker** for unhealthy sessions after consecutive failures |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | 🦞 diamond lobster | **Expose resolved backend model** in `session_status` and agent runtime |

**Prediction:** Fallback model chains (#56781), circuit breakers (#62615), and per-agent dreaming config (#67413) address production reliability pain points likely to ship soon. Multi-slot memory (#60572) is a significant architecture change — lower near-term probability.

---

## 7. User Feedback Summary

**Pain points:**
- **Subagent reliability** is the #1 complaint — results lost on timeout, drain, orphan prune, or first-turn `sessions_yield` (#106704). Users report this as silent and unrecoverable.
- **SQLite durability** issues on WSL2 and after upgrades cause data loss and gateway paralysis.
- **Channel-specific regressions** affect WhatsApp (blank bubbles #127948), Telegram (lost durable deliveries #126246), Feishu (mention placeholders #48786, streaming latency #91941), and MS Teams (migration empties conversation store #94939).
- **Process leaks** (#97616) cause runtime degradation over time — users need to restart to recover.
- **Model routing opacity** (#51441) — users can't see which backend model is actually serving when using LiteLLM proxies.
- **Prompt cache collapse** (#91223) — active memory injection drops hit rate from 99.9% to 22%.
- **WebChat regressions** (#110771, #77819) after upgrades — hidden turns, lost history, archived sessions invisible.

**Satisfaction signals:**
- Beta validation community is engaged (#125626 with 19 comments).
- Feature requests like per-agent dreaming (#67413, 5 👍) and Ali bailian support (#26037, 4 👍) show active production use.
- Audit trail features (#129092, #129093) being built respond to enterprise observability demand.

---

## 8. Backlog Watch

| Issue | Rating | Days Open | Concern |
|---|---|---|---|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 🦞 diamond lobster | 166 | Subagent completion loss — **no fix PR**, P1, data-loss |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | 🦞 diamond lobster | 132 | Subagent delivery path — **no fix PR**, P1 |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | 🦐 gold shrimp | 58 | Child process zombie leak — **no fix PR**, P1, crash-loop |
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | 🐚 platinum hermit | 6 | SQLite corruption on WSL2 — **no fix PR**, P0 |
| [#114612](https://github.com/openclaw/openclaw/issues/114612) | 🦞 diamond lobster | 30 | SQLite unbounded growth (`memory_index_chunks`, `memory_embedding_cache`) — no retention policy |
| [#111372](https://github.com/openclaw/openclaw/issues/111372) | 🦞 diamond lobster | 68 | macOS infinite SIGTERM loop — **no fix PR**, P1 |
| [#127710](https://github.com/openclaw/openclaw/issues/127710) | 🦞 diamond lobster | 4 | prepared-model-runtime fail-closed — **no fix PR**, P1 |
| [#129314](https://github.com/openclaw/openclaw/issues/129314) | 🦐 gold shrimp | 1 | Hidden runtime context message dispatched as standalone turn — **new, no fix** |

**Maintainer attention needed:** The subagent completion loss cluster (#44925, #67777) and SQLite durability issues (#126821, #114612) are the most consequential open items with no active fix PRs. The child process leak (#97616) has been open 58 days at P1.

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Open-Source Ecosystem
**Date:** 2026-08-26 | **Projects Analyzed:** 10

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape in mid-2026 is characterized by high fragmentation with overlapping feature sets and architecture patterns. Ten projects were tracked today, ranging from hyper-active (OpenClaw, Hermes, CoPaw, ZeroClaw) to dormant (ZeptoClaw, NullClaw). The ecosystem is converging on common pain points: subagent reliability, channel-specific delivery bugs, SQLite/state durability, and MCP ecosystem integration. A notable thematic signal is the push toward **household/edge mesh computing** — at least four projects (PicoClaw, NanoClaw, ZeroClaw, NullClaw) are simultaneously exploring distributed edge-worker architectures, suggesting an industry-wide inflection point.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Release | Closed Today | Health Score* |
|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | Beta validation | 66 | ⚠️ 6.2/10 |
| **Hermes Agent** | 100 | 100 | — | 9 | 🟡 7.1/10 |
| **CoPaw** | 33 | 50 | v2.1.1-beta.3 | 14 | 🟢 7.8/10 |
| **ZeroClaw** | 50 | 50 | — | 12 | 🟡 7.0/10 |
| **NanoClaw** | 5 | 50 | — | 16 | 🟡 6.8/10 |
| **IronClaw** | 37 | 24 | — | 10 | 🟡 6.5/10 |
| **LobsterAI** | 1 | 11 | v2026.8.25 (5d) | 9 | 🟢 7.5/10 |
| **Moltis** | 2 | 5 | — | 2 | 🟡 6.0/10 |
| **NanoBot** | 5 | 24 | — | 14 | 🟡 6.4/10 |
| **PicoClaw** | 4 | 1 | — | 0 | 🔴 4.5/10 |
| **NullClaw** | 1 | 0 | — | 0 | 🔴 3.0/10 |
| **ZeptoClaw** | 0 | 0 | — | 0 | 🔴 2.0/10 |

*Health Score synthesizes release velocity, issue closure rate, PR throughput, and open-bug severity distribution.

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Unmatched activity scale** — 500 issues/PRs in 24h dwarfs all other projects, indicating the largest contributor base and most intensive QA pressure.
- **Mature channel ecosystem** — WhatsApp, Telegram, Feishu, MS Teams, WebChat all have established adapters with active regression tracking.
- **Enterprise observability push** — audit trail for model routing (#129092), secrets injection (#129670), and structured core failure reporting (#129728) are addressing B2B demand.

**Technical approach differences:**
- OpenClaw uses a **SQLite-first runtime** with a Gateway architecture, whereas ZeroClaw and IronClaw lean Rust-native, and Hermes uses an Electron desktop wrapper.
- OpenClaw's **subagent orchestration** is the most sophisticated (parent-subagent completion contracts, settle semantics) but also the most bug-prone — subagent completion loss (#44925, #67777) is the #1 community complaint.
- Unlike CoPaw (which uses a console/Chat-first UX) or LobsterAI (library/artifacts focus), OpenClaw is channel-agnostic by design.

**Community size comparison:**
- OpenClaw (500+ daily touches) >> Hermes (~100) > ZeroClaw (~50) > NanoClaw (~50) > IronClaw (~37) >> CoPaw (~83) > Moltis (~7) > LobsterAI (~12) > NanoBot (~29) > PicoClaw (~5) > NullClaw/ZeptoClaw (minimal)

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Subagent / child-process reliability** | OpenClaw, Hermes, CoPaw, NanoBot | Silent completion loss, process leaks, orphan pruning, race conditions on settlement |
| **Channel delivery correctness** | OpenClaw, Hermes, NanoBot, Moltis | WhatsApp blank bubbles, Telegram stuck deliveries, Slack duplicates, Feishu streaming latency |
| **State / SQLite durability** | OpenClaw, CoPaw, ZeroClaw | Corruption on WSL2, migration empties stores, SSE serialization loops, memory leaks |
| **MCP server reliability** | Hermes, PicoClaw, Moltis, ZeroClaw | stdio liveness checks, connection failure hangs, OAuth scope hardening, schema compat |
| **Security isolation** | ZeroClaw (S0), NanoClaw, Moltis, IronClaw | Cron scoping between agents, delegate workspace leakage, shell injection in skills, sandbox backends (K8s, Coder, Kata) |
| **Multi-channel session continuity** | Hermes, Moltis, CoPaw | Cross-channel context preservation, unified session state, profile-swap isolation |
| **Edge / household mesh computing** | PicoClaw, NanoClaw, ZeroClaw, NullClaw | Lightweight workers for idle hardware, signed receipts, RuntimeAdapter portability |
| **Observability & audit** | OpenClaw, IronClaw, LobsterAI | Model routing decisions, session health telemetry, structured logging, circuit breakers |
| **i18n / localization** | Hermes, CoPaw | Desktop UI Portuguese support, Telegram/WeChat multi-language rendering |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | CoPaw | ZeroClaw | LobsterAI | NanoClaw | Moltis | PicoClaw | NullClaw |
|---|---|---|---|---|---|---|---|---|---|
| **Language** | TypeScript/JS | TypeScript/JS + Rust | Python/JS | Rust | Electron/JS | TypeScript/JS | Python/Rust | TypeScript/JS | Zig |
| **Architecture** | Gateway + subagents | Desktop-first | Console/chat-first | Runtime + providers | Library/plugin | Runner-based | Sandbox backends | Edge mesh | Zig runtime |
| **Target user** | Power users, enterprises | Desktop users, i18n demand | Chinese-market (Aliyun/Kimi) | Security-conscious, Rust栈 | Content creators, library users | DevOps/automation | Enterprise sandboxing | SiPEED hardware owners | Edge compute researchers |
| **Key differentiator** | Channel breadth, subagent depth | macOS desktop polish, rapid regression fixes | Model catalog (Aliyun/Kimi), session thinking modes | RFC-governed, S0 security focus | Release cadence, analytics instrumentation | Setup hardening, skill ecosystem | K8s/Coder sandbox backends | RISC-V/edge hardware | Minimalist Zig runtime |
| **Open bugs risk** | **High** — P0 SQLite corruption, subagent loss | **Medium** — macOS permission churn, xAI compat | **Medium** — SSE loop, memory leak on Windows | **High** — S0 cron scoping, delegate leakage | **Low** — clean bug pipeline | **Medium** — skill injection patterns | **Low-Med** — schema compat, cron context | **Medium** — MCP hang, UI lag | **Low** — no active bugs |

---

## 6. Community Momentum & Maturity

**Tier 1 — Hyper-Active (rapid iteration, high bug surface):**
- **OpenClaw** — Largest community, most intense QA pressure, but P0 stability issues (SQLite corruption, subagent loss) suggest the beta is still exercising fundamental paths.
- **Hermes Agent** — Dense bug-fixing cycle with rapid closure of regressions; macOS Desktop remains the weakest link.
- **CoPaw** — Strong velocity with new beta releases; SSE loop fix and memory leak remediation in progress.

**Tier 2 — Active & maturing (steady velocity, controlled release cycles):**
- **ZeroClaw** — RFC-driven governance, strong security focus, Rust-native stability; S0 bugs are serious but the community is engaged in design debates.
- **NanoClaw** — High PR throughput from coordinated core-team effort; skill-security audit suggests growing maturity.
- **IronClaw** — CI hardening and design-system work indicate post-feature-delivery stabilization.
- **LobsterAI** — Cleanest bug pipeline, regular releases, community growth signal (WeChat group full).

**Tier 3 — Moderate / Niche:**
- **Moltis** — Steady but small; sandbox backends are the key roadmap bet.
- **NanoBot** — Balanced channel/UI/provider work; no releases yet.
- **PicoClaw** — Small community but clear roadmap signal (edge workers); needs maintainer triage on stale PRs.

**Tier 4 — Dormant / Early:**
- **NullClaw** — Minimal activity; architectural vision stage.
- **ZeptoClaw** — No activity in reporting period.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Edge mesh computing** | PicoClaw (#3345), NanoClaw (#3538), ZeroClaw (#10360), NullClaw (#994) | Consumers want to turn idle hardware into agent compute. Opportunity: standardized worker protocol. |
| **Subagent reliability as first-class problem** | OpenClaw (#44925, #67777), Hermes (child-process leaks), CoPaw (session consistency) | Silent completion loss is the #1 reliability complaint. Any project solving this credibly gains enterprise trust. |
| **MCP ecosystem fragmentation** | Hermes (stdio liveness, xAI compat), PicoClaw (hang on failure), Moltis (OAuth hardening), ZeroClaw (schema compat) | MCP is becoming the standard tool interface, but provider compliance varies. Schema validation and liveness checking are table-stakes. |
| **Channel-specific delivery bugs** | OpenClaw (WhatsApp, Telegram, Feishu), Hermes (Slack dups), NanoBot (Telegram rich messages) | Cross-channel messaging is a minefield. Projects investing in durable delivery primitives will differentiate. |
| **State durability & migration risk** | OpenClaw (SQLite corruption), CoPaw (SSE loops, memory leaks), ZeroClaw (cron workspace resolution) | Database-first runtimes are fragile during upgrades. Projects with migration tooling and WAL-based durability will win enterprise adoption. |
| **Security isolation as requirement, not feature** | ZeroClaw (S0 cron scoping), NanoClaw (shell injection), Moltis (K8s sandbox), IronClaw (sandbox epic) | Multi-tenant or multi-agent deployments require strong isolation. Sandbox-as-a-service is an emerging market. |
| **Observability & audit demands** | OpenClaw (audit trail, model routing), IronClaw (notifications hardening), LobsterAI (analytics instrumentation) | Enterprise buyers require visibility into model selection, session health, and cost attribution. |
| **i18n as differentiator** | Hermes (pt-BR Desktop demand), CoPaw (WeChat/WhatsApp focus) | Chinese-language and Portuguese support are underserved in desktop agent UX. |
| **RFC-governed architecture** | ZeroClaw (work lanes, wire protocol RFCs), LobsterAI (model catalog governance) | Transparent decision-making correlates with contributor retention. Projects with visible RFC processes attract more sustained contributions. |

---

**Summary:** The ecosystem is in a consolidation phase where reliability (subagent delivery, state durability, channel correctness) is superseding feature novelty as the key competitive dimension. OpenClaw has scale but faces P0 stability challenges; ZeroClaw and Moltis are betting on security/isolation primitives; LobsterAI leads on release discipline; and the edge-mesh signal across four projects suggests a new deployment paradigm is emerging.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-26

## 1. Today's Overview
NanoBot demonstrates strong development velocity with 24 pull request updates and 5 open issues in the last 24 hours. Fourteen PRs were merged or closed today, reflecting high maintainer throughput and steady convergence on recent fixes. No new releases were published, indicating the project is currently in a merge-and-refine phase ahead of an upcoming version. Activity remains balanced across channel stability, UI polish, and provider expansion.

## 2. Releases
None today. Development remains focused on integrating and stabilizing the 14 closed PRs before a potential release window.

## 3. Project Progress
**Merged/Closed PRs (14):**
- **Search & Providers:** `#5540` stabilized Codex prompt cache routing; `#5525` shipped demand-driven document retrieval (`grep` + incremental PDF/DOCX/XLSX/PPTX parsing).
- **Channel Reliability:** `#5541` fixed Telegram group message sender attribution; `#5529` adjusted background subagent lifecycle to wait only at turn exit.
- **UI/UX Polish:** `#5389` enabled drag-and-drop session organization; `#5534` added TUI skill autocomplete; `#5538` clarified composer action hints (`Enter send now · Tab send next`); `#5530` aligned short transcripts and composer at the top of tall panes.
- **Performance & Safety:** `#5533` optimized `find_files` with bounded `os.scandir` traversal; `#5526` replaced polling-based exec waits with a unified `exec_session` tool.

## 4. Community Hot Topics
- **#5505** Add AnySearch as a web search provider (3 comments) – [Link](https://github.com/HKUDS/nanobot/issues/5505)  
  *Analysis:* High community interest in quota-friendly, API/MCP/Skill-compatible search alternatives. Signals demand for a more modular search abstraction layer.
- **#5516** Telegram rich messages break when streaming is enabled – [Link](https://github.com/HKUDS/nanobot/issues/5516)  
  *Analysis:* Streaming is now the default, but it currently bypasses `sendRichMessage`, degrading Telegram UX. PR `#5531` targets this regression.
- **#5527** WebUI sidebar titles stay "Untitled" under `unifiedSession` – [Link](https://github.com/HKUDS/nanobot/issues/5527)  
  *Analysis:* Highlights a session-scoping mismatch between title generation (shared session) and sidebar rendering (per-chat WebSocket sessions). PR `#5528` addresses the root cause.

## 5. Bugs & Stability
Ranked by severity:
1. **#5536** `[P1/Security]` Restricted shell executes without sandbox – Open. `[PR]` Addresses symlink/path-traversal bypass in `ExecTool`. No merge yet.
2. **#5532** `[P2/Bug]` Missing `mask_session_key` import in `autocompact.py` – Open. `[Issue]` Triggers crash during specific multi-step query patterns.
3. **#5516** `[P2/Bug]` Telegram rich messages never render with streaming – Open. `[PR #5531]` Fix in review.
4. **#5527** `[P2/Bug]` WebUI sidebar titles not projected under unified sessions – Open. `[PR #5528]` Fix in review.
5. **#5539** `[P2/Bug]` ToolLoader log context uses printf-style placeholders – Open. `[PR]` Causes log formatting failures; fix pending.

*Stability note:* Today's merges significantly improve runtime reliability (Codex cache, subagent rendezvous, exec polling, file scan performance), offsetting the remaining open regressions.

## 6. Feature Requests & Roadmap Signals
- **#

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-26

## 1. Today's Overview

Hermes Agent shows **high activity** today with 100 issues/PRs updated in the last 24 hours (50 issues: 41 open, 9 closed; 50 PRs: 40 open, 10 merged/closed). The project is in a dense bug-fixing cycle, with six closed issues and five merged PRs concentrated on desktop regressions, MCP reliability, and macOS/i18n pain points. No new releases were published today. The maintainer team is actively triaging a cluster of P1/P2 desktop and plugin regressions, signaling a stabilization push ahead of an upcoming release.

## 2. Releases

No new releases today.

## 3. Project Progress

### Merged / Closed Today

| Item | Summary |
|------|---------|
| [PR #95144](https://github.com/NousResearch/hermes-agent/pull/95144) | **fix(mcp):** Corrected inverted `_stdio_children_dead()` return value — previously returned `True` (all dead) when an alive child was found, causing all stdio MCP calls to fail immediately after gateway restart |
| [PR #95158](https://github.com/NousResearch/hermes-agent/pull/95158) | **fix(doctor):** Dropped `--json authenticated` flag for `gh` CLI 2.98+ compatibility (field removed upstream) |
| [PR #91679](https://github.com/NousResearch/hermes-agent/pull/91679) | **fix(desktop):** Self-heal a deleted profile + ad-hoc sign macOS bundle to restore app functionality |
| [PR #95155](https://github.com/NousResearch/hermes-agent/pull/95155) | **fix(web):** Resolve asset base path for code-split chunks served under a proxy prefix |
| [PR #88422](https://github.com/NousResearch/hermes-agent/pull/88422) | **fix(update):** Unshallow shallow clones so `git fetch` crosses the shallow boundary and the updater reflects the real remote tip |

### Open PRs Advancing
- [#92931](https://github.com/NousResearch/hermes-agent/pull/92931) — Bot-mode cross-connection relay made lease-backed and idempotent
- [#93508](https://github.com/NousResearch/hermes-agent/pull/93508) — Serve the Desktop renderer directly in browsers via `hermes webapp`
- [#95152](https://github.com/NousResearch/hermes-agent/pull/95152) — Kanban rework: `done-terminal` gate, `reanimate` verb, `kanban_schedule(task, +N)`
- [#95160](https://github.com/NousResearch/hermes-agent/pull/95160) — Collapse `read_file`/`write_file` shell probes into one round-trip (perf)
- [#95156](https://github.com/NousResearch/hermes-agent/pull/95156) — Fix Feishu DM approval card buttons
- [#95153](https://github.com/NousResearch/hermes-agent/pull/95153) — Retry Playwright downloads over IPv4

## 4. Community Hot Topics

| Rank | Issue | Comments | 👍 | Link |
|------|-------|----------|----|------|
| 1 | Skills index stale/degraded (`degraded` status, 29.8h old) | 97 | 0 | [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) |
| 2 | macOS Full Disk Access revoked after every Desktop update | 21 | 0 | [#52010](https://github.com/NousResearch/hermes-agent/issues/52010) |
| 3 | Add pt-BR language support to Desktop app | 11 | 3 | [#40239](https://github.com/NousResearch/hermes-agent/issues/40239) |
| 4 | xAI rejects `tool_search` as reserved function name | 10 | 8 | [#95003](https://github.com/NousResearch/hermes-agent/issues/95003) |
| 5 | Terminal tools truncate long lines, model sees "corrupted" content | 10 | 2 | [#16520](https://github.com/NousResearch/hermes-agent/issues/16520) ✅ closed |
| 6 | macOS keychain prompt after update (safeStorage rotation) | 9 | 0 | [#91115](https://github.com/NousResearch/hermes-agent/issues/91115) |
| 7 | Hermes Authority Execution Layer — architecture proposal | 9 | 0 | [#95028](https://github.com/NousResearch/hermes-agent/issues/95028) |

**Analysis:** The top issues reflect three recurring themes: (1) **macOS Desktop experience** — permissions revocation and keychain instability after updates are a persistent pain point; (2) **provider compatibility** — xAI's reserved-function enforcement breaks Hermes' tool-naming convention; (3) **localization demand** — strong community appetite for pt-BR Desktop support (3 👍, 11 comments) despite backend already having full i18n coverage.

## 5. Bugs & Stability

### P1
| Issue | Summary | Fix? |
|-------|---------|------|
| [#94906](https://github.com/NousResearch/hermes-agent/issues/94906) | **Windows:** native stdio MCP tools fail immediately with `subprocess has exited` | Related fix merged in [#95144](https://github.com/NousResearch/hermes-agent/pull/95144) (inverted liveness check) — not yet confirmed as resolved for Windows specifically |

### P2
| Issue | Summary | Fix? |
|-------|---------|------|
| [#95003](https://github.com/NousResearch/hermes-agent/issues/95003) | xAI rejects `tool_search` function name — Grok providers unusable | No fix yet |
| [#91115](https://github.com/NousResearch/hermes-agent/issues/91115) | macOS keychain prompt after every `hermes update` (ad-hoc code signing changes ACL) | No fix yet |
| [#52010](https://github.com/NousResearch/hermes-agent/issues/52010) | macOS Full Disk Access revoked after every Desktop update | No fix yet |
| [#90428](https://github.com/NousResearch/hermes-agent/issues/90428) | Messages to WS-detached sessions silently dropped after reconnect | ✅ Closed |
| [#94516](https://github.com/NousResearch/hermes-agent/issues/94516) | Desktop Bot Mode: Cronjobs unavailable until agent in roster (regression) | ✅ Closed |
| [#94471](https://github.com/NousResearch/hermes-agent/issues/94471) | Desktop Bots tab crash — `trim is not a function` | ✅ Closed |
| [#94483](https://github.com/NousResearch/hermes-agent/issues/94483) | CRONJOBS pane stuck on "unavailable" fail-closed message | ✅ Closed |
| [#93594](https://github.com/NousResearch/hermes-agent/issues/93594) | Bot-relay drain loop opens/tears down WebSocket every 4s (log flood) | ✅ Closed |
| [#95054](https://github.com/NousResearch/hermes-agent/issues/95054) | Ollama fallback entries resolve to `(None, None)` silently | No fix yet |
| [#84106](https://github.com/NousResearch/hermes-agent/issues/84106) | `hermes config get mcp_servers` exposes resolved MCP secrets | No fix yet |
| [#94946](https://github.com/NousResearch/hermes-agent/issues/94946) | `browser.inactivity_timeout` and orphan reaper are dead code under Browser Use CLI backend | No fix yet |
| [#95078](https://github.com/NousResearch/hermes-agent/issues/95078) | Nested Hermes inherits stale `TERMINAL_CWD` | No fix yet |
| [#79005](https://github.com/NousResearch/hermes-agent/issues/79005) | Profile swap routes `session.create` to wrong backend (cross-profile `state.db` pollution) | No fix yet |
| [#93617](https://github.com/NousResearch/hermes-agent/issues/93617) | Slack concurrent turns clobber native stream → duplicate messages | ✅ Closed |
| [#94435](https://github.com/NousResearch/hermes-agent/issues/94435) | Slack adapter appends to sealed stream → duplicate messages | No fix yet |
| [#62774](https://github.com/NousResearch/hermes-agent/issues/62774) | Desktop streaming truncates Portuguese accented text | No fix yet |

**Assessment:** Heavy bug volume today, concentrated on the Desktop app (cronjobs, profile swap, session state). The P1 Windows MCP issue (#94906) likely shares root cause with the merged #95144 but needs Windows-specific verification. The xAI provider incompatibility (#95003) is a growing concern as more users adopt Grok.

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Description | Likelihood in Next Release |
|----------|-------------|---------------------------|
| [#40239](https://github.com/NousResearch/hermes-agent/issues/40239) | Add pt-BR language to Desktop app | Medium — backend already complete, frontend i18n work needed |
| [#93382](https://github.com/NousResearch/hermes-agent/issues/93382) | Adaptive explanation policy for interactive learning artifacts | Low — needs architectural decision |
| [#91005](https://github.com/NousResearch/hermes-agent/issues/91005) | Verified local cold archive for soft-archived sessions | Low — trade-off between archival and searchability |
| [PR #93508](https://github.com/NousResearch/hermes-agent/pull/93508) | Serve Desktop renderer in browsers (`hermes webapp`) | Medium — significant scope but actively developed |
| [PR #76661](https://github.com/NousResearch/hermes-agent/pull/76661) | P2P federation heartbeat for multi-device task relay | Low — large architectural change, Phase 24 in progress |
| [PR #89061](https://github.com/NousResearch/hermes-agent/pull/89061) | Add SSYCloud (胜算云) LLM provider | Medium — straightforward provider integration |
| [#95028](https://github.com/NousResearch/hermes-agent/issues/95028) | Authority Execution Layer architecture | Low — foundational rewrite, long-term |

## 7. User Feedback Summary

**Pain points:**
- **macOS permission churn** after every Desktop update is the #1 frustration (#52010, #91115) — users must manually re-grant Full Disk Access and keychain ACLs, eroding trust in the updater.
- **Windows MCP breakage** (#94906) is a blocker for users relying on stdio MCP servers on that platform.
- **Slack duplicate messages** from streaming race conditions (#93617, #94435) disrupt team workflows.
- **Portuguese i18n gaps** — backend is ready but Desktop UI remains English-only (#40239, #26665).
- **Session state leakage** across profile swaps (#79005) and gateway switches (#93937) causes confusion and lost context.

**Positive signals:**
- Rapid closure of several regressions (cronjobs, bot-relay drain, Slack stream clobbering, terminal truncation) shows responsive maintenance.
- Performance work on `read_file`/`write_file` (#95160) and browser-based Desktop (#93508) indicates investment in core UX improvements.
- Community-contributed provider integrations (SSYCloud, #89061) and fixes (Feishu, #95156) demonstrate a healthy contributor base.

## 8. Backlog Watch

| Issue | Priority | Age | Why It Needs Attention |
|-------|----------|-----|----------------------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | P3 | ~39 days | Skills index watchdog fires `degraded` alerts with 97 comments — indicates systemic refresh failures affecting the docs/skills ecosystem |
| [#52010](https://github.com/NousResearch/hermes-agent/issues/52010) | P2 | ~63 days | macOS FDA revocation after every update — no fix in sight, high user impact |
| [#95003](https://github.com/NousResearch/hermes-agent/issues/95003) | P2 | 1 day | xAI provider broken for all Grok users; 8 👍 suggests broad impact |
| [#91115](https://github.com/NousResearch/hermes-agent/issues/91115) | P2 | 6 days | macOS keychain rotation after ad-hoc signing — requires architectural change to updater |
| [#84106](https://github.com/NousResearch/hermes-agent/issues/84106) | P2 | 15 days | Security: MCP secrets leaked via `hermes config get` — urgent remediation needed |
| [#95028](https

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-26

## 1. Today's Overview

PicoClaw shows moderate community activity with 4 open issues and 1 open pull request updated in the last 24 hours. No new releases were published, indicating the project is in a stable maintenance phase rather than a release cadence. Activity is concentrated on Slack media upload fixes and performance/stability concerns around chat UI lag and MCP server hangs. A new proposal for a lightweight worker mode on edge devices was opened, signaling community interest in expanding PicoClaw's hardware footprint. Overall project health is steady with no critical mass of closed items, but several open bugs remain unresolved.

## 2. Releases

No new releases in the reporting period.

## 3. Project Progress

- **#3340** [OPEN, stale] `fix(slack): set FileSize on media upload params` — A fix for Slack media upload failures is open but unmerged. The PR correctly identifies that `slack-go` v0.23.1 requires `FileSize` to be set explicitly in `UploadFileParameters` before the `files.upload.v2` flow can proceed. No other PRs were merged or closed today.

## 4. Community Hot Topics

- **[Issue #3281](https://github.com/sipeed/picoclaw/issues/3281)** — *Web UI chat input is very laggy when history has a little bit long* — 7 comments, 1 👍. High engagement reflects a widespread UX pain point: as chat history grows, input responsiveness degrades noticeably. This suggests the frontend may be re-rendering or processing excessive DOM/state on every keystroke.
- **[Issue #3269](https://github.com/sipeed/picoclaw/issues/3269)** — *MCP server connection failure causes agent loop hang* — 7 comments, 1 👍. Another high-engagement issue pointing to a critical reliability gap: a single MCP server timeout can block the entire chat interface. This is a systemic robustness concern for production deployments.
- **[Issue #3345](https://github.com/sipeed/picoclaw/issues/3345)** — *Proposal: lightweight PicoClaw worker mode for household edge compute* — 0 comments, new today. Signals strong community interest in running PicoClaw on constrained RISC-V/ARM/MIPS devices, Raspberry Pis, and old Android phones — a potential new deployment vector.

## 5. Bugs & Stability

| Severity | Issue / PR | Description |
|----------|-----------|-------------|
| **High** | [#3269](https://github.com/sipeed/picoclaw/issues/3269) | MCP server connection failure hangs the agent loop, freezing the chat UI. No fix PR yet. |
| **Medium** | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI chat input becomes very laggy with moderate history length. Stale; no fix PR yet. |
| **Medium** | [#3338](https://github.com/sipeed/picoclaw/issues/3338) + [#3340](https://github.com/sipeed/picoclaw/pull/3340) | Slack media uploads always fail with `file size cannot be 0`. Fix PR #3340 exists but is open and stale. |

No crashes or regressions reported today. The most urgent item is #3269, as an MCP hang effectively breaks the assistant entirely for affected users.

## 6. Feature Requests & Roadmap Signals

- **Lightweight worker mode for edge devices** [#3345](https://github.com/sipeed/picoclaw/issues/3345) — A community proposal to enable PicoClaw on low-resource hardware (10–20 MB RAM footprint). This aligns with SiPEED's RISC-V ecosystem and could become a major differentiator. Likely candidate for inclusion in a future roadmap release if the community and maintainers validate feasibility.

## 7. User Feedback Summary

- **Frustration with Web UI performance**: Users are hitting lag with relatively small chat histories, suggesting the frontend isn't optimized for incremental rendering or virtualization.
- **Reliability concerns with MCP integrations**: A hanging agent loop due to a single MCP server failure is seen as a critical flaw — users expect graceful degradation, not total freezes.
- **Slack bot experience is broken for media**: Image uploads are non-functional out of the box, which undermines PicoClaw's multi-channel messaging value proposition. The fix is ready in PR #3340 but hasn't been merged.
- **Strong enthusiasm for edge computing**: The #3345 proposal received attention quickly, indicating a ready market among SiPEED hardware owners and distributed-agent enthusiasts.

## 8. Backlog Watch

- **[Issue #3269](https://github.com/sipeed/picoclaw/issues/3269)** — Agent loop hang on MCP failure. 7 comments, no fix. Needs maintainer triage; high severity.
- **[Issue #3281](https://github.com/sipeed/picoclaw/issues/3281)** — Web UI input lag with history. Marked stale, 7 comments, no fix. Impacts core UX for power users.
- **[PR #3340](https://github.com/sipeed/picoclaw/pull/3340)** — Slack media upload fix. Ready and correct but open and stale. A trivial merge that would unblock a documented bug (#3338).

---

**Bottom line:** PicoClaw's activity is healthy but blocked on a few stale items that have clear fixes or analysis. Prioritizing the merge of #3340 and triage of #3269 would address the two most impactful open issues. The edge-compute proposal (#3345) is a promising roadmap signal worth monitoring.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-26

## 1. Today's Overview

NanoClaw showed high integration velocity today with 50 PRs updated (34 open, 16 merged/closed) and 5 active issues. No new releases were published, indicating the current cycle is still in active development rather than stabilization. Activity is heavily concentrated around setup-tooling hardening, Slack integration improvements, and runner reliability — a strong signal the core team is prioritizing operational maturity. The project remains healthy with steady contributor engagement across both core-team and community PRs.

## 2. Releases

No new releases published in the last 24 hours.

## 3. Project Progress

**Merged/Closed PRs today:**

- **#3544** [core-team] fix(slack): add explicit room handoffs — Introduced an explicit Slack room handoff tool with host-side mention resolution and validation, preventing unintended automatic mentions on room creation. ([link](https://github.com/nanocoai/nanoclaw/pull/3544))
- **#3540** [core-team] fix(opencode): run the agent session in the agent workspace — Fixed a cwd mismatch where OpenCode agents were operating from a sibling directory instead of their workspace, breaking project-document resolution. ([link](https://github.com/nanocoai/nanoclaw/pull/3540))
- **#3539** [core-team] refactor(codex): keep the spec, drop the duplicated composer — Consolidated Codex's project-document composer into trunk's shared version, eliminating drift and fixing broken `ncl tasks` manual delivery for scoped-disabled groups. ([link](https://github.com/nanocoai/nanoclaw/pull/3539))
- **#3536** [core-team] fix(compose): inline every instruction source into one project document — Resolved a Claude Code security-gate regression where `@` imports resolving outside the working directory were being declined, disabling capability instructions. ([link](https://github.com/nanocoai/nanoclaw/pull/3536))
- **#3537** [core-team] refactor(codex) — Duplicate of #3539, also closed. ([link](https://github.com/nanocoai/nanoclaw/pull/3537))
- **#2656** fix(add-mnemon): run mnemon setup in index.ts main() — Fixed a long-standing bug where mnemon hooks never registered because the host overrides the image ENTRYPOINT. ([link](https://github.com/nanocoai/nanoclaw/pull/2656))

**Key open PRs advancing:**

- **#3528** feat(runner): lease-id claimants, restart-overlap protection, and the incarnation gate — A major durability feature stacking on `feat/durable-host-integration`, addressing container restart conflicts. ([link](https://github.com/nanocoai/nanoclaw/pull/3528))
- **#3298** feat(channels): add local web chat — Adds a built-in local web chat channel requiring no external account, improving fresh-install onboarding and demo experience. ([link](https://github.com/nanocoai/nanoclaw/pull/3298))
- **#3484–#3487, #3482, #3483** Setup hardening suite — A coordinated set of PRs improving setup wizard security (argv secret exposure), structured driver protocol, timezone preseeding, health exposure, and uninstall atomicity. ([links: #3484](https://github.com/nanocoai/nanoclaw/pull/3484) | [#3485](https://github.com/nanocoai/nanoclaw/pull/3485) | [#3486](https://github.com/nanocoai/nanoclaw/pull/3486) | [#3487](https://github.com/nanocoai/nanoclaw/pull/3487) | [#3482](https://github.com/nanocoai/nanoclaw/pull/3482) | [#3483](https://github.com/nanocoai/nanoclaw/pull/3483))

## 4. Community Hot Topics

- **#3538** Proposal: use isolated NanoClaw containers as opt-in household edge workers — Proposes leveraging users' idle home hardware (PCs, laptops, NAS) as distributed edge workers instead of cloud GPUs. Reflects a strong community interest in cost reduction and self-hosting ethos. ([link](https://github.com/nanocoai/nanoclaw/issues/3538))
- **#2431** Conditional thread policy for Slack adapter (DM=top-level, channels=threaded) — Long-open PR (since May) proposing per-channel thread behavior, addressing user frustration with uniform threading. Still open after ~3 months. ([link](https://github.com/nanocoai/nanoclaw/pull/2431))
- **#3543** add-dial: unquoted `{{owner_email}}` in bash — Security-relevant issue where apostrophe-containing emails break sign-in and pass validation. Highlights ongoing skill-authoring safety gaps. ([link](https://github.com/nanocoai/nanoclaw/issues/3543))

## 5. Bugs & Stability

| Severity | Issue/PR | Description |
|----------|----------|-------------|
| **High** | [#3543](https://github.com/nanocoai/nanoclaw/issues/3543) | `add-dial` skill injects `{{owner_email}}` unquoted into `bash -c`, allowing shell metacharacter injection and breaking on apostrophe emails. No fix PR yet. |
| **High** | [#3535](https://github.com/nanocoai/nanoclaw/issues/3535) | `add-vercel` skill's per-session rsync copies block spawn-time symlink sync and pin groups to stale skills. No fix PR yet. |
| **Medium** | [#3532](https://github.com/nanocoai/nanoclaw/issues/3532) | `add-*-tool` per-agent scoping misses later-created agents/groups, granting tools by default instead of blocking. No fix PR yet. |
| **Medium** | [#3529](https://github.com/nanocoai/nanoclaw/issues/3529) | `update-nanoclaw` skill refresh overwrites or fails validation on local adapters not sourced from skills. No fix PR yet. |
| **Medium** | [#3525](https://github.com/nanocoai/nanoclaw/pull/3525) | Fix PR open: wizard's agent-scope prompt cannot echo user input due to `nc:run effect:step` stdout capture limitation. ([link](https://github.com/nanocoai/nanoclaw/pull/3525)) |
| **Low** | [#3311](https://github.com/nanocoai/nanoclaw/pull/3311) | Fix PR open: scheduled-task errors were written with incorrect batch routing fields, producing misleading error messages. ([link](https://github.com/nanocoai/nanoclaw/pull/3311)) |
| **Low** | [#3542](https://github.com/nanocoai/nanoclaw/pull/3542) | Fix PR open: container_status drift not cleared at startup adoption. ([link](https://github.com/nanocoai/nanoclaw/pull/3542)) |

Five of the six open issues are from a single author (glifocat), suggesting a systematic audit of skill authoring patterns is underway — these are likely interrelated quality issues in the skill template ecosystem.

## 6. Feature Requests & Roadmap Signals

- **Household edge workers** (#3538) — Strong signal for distributed/self-hosted scaling. If adopted, this could become a major architectural feature.
- **Local web chat** (#3298) — Low-friction onboarding channel; likely candidate for next release given it's already in PR.
- **Structured setup driver protocol** (#3485) — Exposes setup wizard to programmatic control; enables automation and CI/CD integration.
- **Slack room handoffs** (#3544 merged) — Now shipped; expect follow-up thread-policy work (#2431) to land next.
- **Timezone & catalog preseeding** (#3486, #3487) — Improves automated deployment scenarios.

**Prediction:** The next release will likely include the local web chat channel, setup hardening improvements, and the Slack handoff feature. The durable runner integration (#3528) may also ship if the parent branch merge completes.

## 7. User Feedback Summary

- **Pain point: Skill security patterns.** glifocat's cluster of issues (#3543, #3535, #3532, #3529) all stem from skills generating shell commands or file operations without proper quoting, scoping, or idempotency. Users are hitting real breakage during setup and update flows.
- **Pain point: Setup wizard not machine-parseable.** The structured driver protocol PR (#3485) confirms users want to automate NanoClaw installation, but the current terminal-dependent wizard blocks this.
- **Pain point: Fresh-install friction.** The local web chat PR (#3298) and conditional Slack threading (#2431) both address the "nothing works until you configure an external account" problem.
- **Satisfaction signal:** High PR throughput from both core-team and community contributors indicates a healthy, engaged contributor base. The coordinated setup-hardening PR set (#3482–#3487) shows the team is responsive to operational concerns.

## 8. Backlog Watch

- **#2431** Conditional thread policy for Slack — Open since 2026-05-12 (~3 months). Important for Slack power users; no maintainer response visible.
- **#3543** add-dial shell injection — Security-relevant; no fix PR. Needs priority triage given the pattern extends to other skills.
- **#3529** update-nanoclaw local adapter overwrite — Blocks custom adapter workflows; no fix PR.
- **#3538** Household edge workers — Proposal-stage; requires architectural decision from maintainers before any work begins.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-26

## 1. Today's Overview

NullClaw activity on 2026-08-26 was minimal, with only a single issue updated in the past 24 hours and no pull requests or releases. The project remains in a low-velocity state, with development concentrated around its core edge mesh architecture rather than rapid iteration. The single open issue (#994) signals ongoing work on household-level edge networking using `RuntimeAdapter` workers and signed receipts — a topic central to NullClaw's identity as a lightweight Zig-based runtime for distributed devices. No regressions or critical bugs were reported today.

## 2. Releases

No new releases were published. The project has no recent version history visible in this reporting window.

## 3. Project Progress

- **Merged/Closed PRs today:** 0
- No features or fixes advanced through pull requests during this period. Development appears to be in a contemplative or design-heavy phase, with the community focusing on issue discussion rather than mergeable contributions.

## 4. Community Hot Topics

**Issue #994 — Household edge mesh using RuntimeAdapter workers and signed receipts**
- 👍 0 | 💬 0 | Open since 2026-08-25
- [View Issue](https://github.com/nullclaw/nullclaw/issues/994)

This is the sole active discussion and points to a core architectural need: enabling everyday users to leverage multiple idle machines (PCs, laptops, etc.) as a coordinated edge mesh. The mention of signed receipts and `RuntimeAdapter` workers suggests the project is maturing its security and portability story. The low engagement (0 comments, 0 reactions) may indicate the idea is still in early framing or that the community is small. The underlying need is clear — users want to turn scattered consumer hardware into a reliable, secure computing fabric, which aligns directly with NullClaw's stated design goals.

## 5. Bugs & Stability

No bugs, crashes, or regressions were reported today. The single open issue (#994) is a feature/architecture discussion, not a defect report. Project stability appears intact with no known active issues affecting correctness.

## 6. Feature Requests & Roadmap Signals

**Household edge mesh with signed receipts (#994)** — The most prominent roadmap signal. This issue outlines a vision forNullClaw to serve as a practical edge computing layer for personal device fleets. Key themes likely to shape upcoming work:

- **RuntimeAdapter portability** (Docker/WASM/hardware adapters) — suggests continued investment in cross-platform deployment
- **Signed receipts** — indicates a push toward verifiable, tamper-evident operation logs, possibly for auditability or trustless coordination
- **Strict size/memory goals** — reinforces NullClaw's positioning as a lightweight alternative to heavier orchestration tools

If this issue gains traction, the next release cycle may include prototype implementations of household-scale mesh provisioning and receipt signing primitives.

## 7. User Feedback Summary

No direct user feedback was posted today. However, Issue #994 reflects an aspirational use case: owners of multiple idle consumer machines seeking a minimal, secure runtime to mesh them together. The emphasis on "unusually good primitives" already present in NullClaw suggests early adopters recognize the project's technical promise but may be waiting for higher-level abstractions (mesh orchestration, signed attestation) before adopting it at scale. Satisfaction appears conditional on the project delivering on its architectural vision rather than any existing production deployment.

## 8. Backlog Watch

| Item | Age | Attention Needed |
|---|---|---|
| [#994](https://github.com/nullclaw/nullclaw/issues/994) — Household edge mesh | ~1 day | Medium — no comments yet; needs maintainer response to gauge feasibility and scope |

No long-unanswered issues were identified beyond #994, which is newly opened. The project's low issue volume makes backlog accumulation unlikely at this time, but the absence of any maintainer response to an architecture-significant issue warrants monitoring over the coming week.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-26

## 1. Today's Overview
IronClaw activity remains high with **37 issues** and **24 PRs** touched in the past 24 hours. Ten PRs have merged or closed today, driven primarily by CI pipeline hardening (nextest consolidation, preflight gates, PR/queue convergence), notification-system refactoring, and WebUI component standardization. The project is in an active stabilization phase around v1.4.0, with two notable performance bugs surfaced in the agent loop (issues #7891 and #7892) and corresponding fix PRs already in flight. No new releases were published today.

## 2. Releases
*None.* The project had zero new releases in the last 24 hours.

## 3. Project Progress

**Merged / Closed PRs (10 today):**

| PR | Summary | Status |
|---|---|---|
| [#7817](https://github.com/nearai/ironclaw/pull/7817) | CI: nextest test pipeline, full-failure signal, PR unthrottle (T2) | ✅ Closed |
| [#7809](https://github.com/nearai/ironclaw/pull/7809) | CI: canonical preflight — one gate list, worktree-safe hooks, self-printing REPRO (T4, tasks 1–5) | ✅ Closed |
| [#7819](https://github.com/nearai/ironclaw/pull/7819) | CI: PR/queue check convergence — planner drift guard, default-features clippy on PRs (T3) | ✅ Closed |
| [#7894](https://github.com/nearai/ironclaw/pull/7894) | CI: reduce required scope checkout transfer | ✅ Closed |
| [#7846](https://github.com/nearai/ironclaw/pull/7846) | Refactor: retire legacy notification approval fallback | ✅ Closed |
| [#7816](https://github.com/nearai/ironclaw/pull/7816) | WebUI: add refresh and connect entries to the OOBE suggestion drawer | ✅ Closed |
| [#7861](https://github.com/nearai/ironclaw/pull/7861) | Fix: restore device-link guidance on the install/activate paths | ✅ Closed |
| [#7820](https://github.com/nearai/ironclaw/pull/7820) | Test: scope-isolation suite consolidation probe (T2 follow-up) | ✅ Closed |
| [#7818](https://github.com/nearai/ironclaw/pull/7818) | Subagent: background mode — receipt spawns, per-child delivery, activation, healing sweeps (slices 2b+2c) | ✅ Closed |

**In-progress PRs with notable activity:**

- [#7896](https://github.com/nearai/ironclaw/pull/7896) — *fix: bound model-visible tool result previews* (addresses perf bug #7891)
- [#7884](https://github.com/nearai/ironclaw/pull/7884) — *fix: unlock stuck threads with wall-clock occupancy* (addresses #7892 and hung-run issues)
- [#7831](https://github.com/nearai/ironclaw/pull/7831) — *Design System Phase 3a foundation* (Chromatic lane + missing token axes)
- [#7491](https://github.com/nearai/ironclaw/pull/7491) — *feat(coding): omp core-tool contract + engines + benchmark arm* (XL, in review)

## 4. Community Hot Topics

| Issue | Comments | Focus |
|---|---|---|
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | 9 | Persistent per-user sandbox with iron-proxy; defer loop executors |
| [#7799](https://github.com/nearai/ironclaw/issues/7799) | 4 | CI nextest pipeline & test consolidation (closed) |
| [#7038](https://github.com/nearai/ironclaw/issues/7038) | 3 | Design System Phase 1 — Storybook integration (closed) |
| [#7862](https://github.com/nearai/ironclaw/issues/7862) | 3 | Telegram device-link fails with opaque error when API credentials unconfigured |

**Analysis:** The top-discussed open issue (#7732) reflects sustained interest in persistent sandboxing—a core architectural need for multi-tenant deployments. The Telegram device-link issue (#7862) surfaced during QA and quickly gathered attention, indicating that channel-credential setup remains a friction point for end users. The CI work (#7799) has largely resolved its immediate concerns through the merged PRs listed above.

## 5. Bugs & Stability

| Issue | Severity | Summary | Fix PR |
|---|---|---|---|
| [#7892](https://github.com/nearai/ironclaw/issues/7892) | **Medium** | Deferred tool invoked 15× but never executed; 123 s run with only 4 distinct calls and no terminating guard | [#7884](https://github.com/nearai/ironclaw/pull/7884) (in progress) |
| [#7891](https://github.com/nearai/ironclaw/issues/7891) | **Medium** | Unprojected 24 KiB Gmail MIME headers pushed into prompt, costing 14.3 s of inference per call | [#7896](https://github.com/nearai/ironclaw/pull/7896) (open) |
| [#7862](https://github.com/nearai/ironclaw/issues/7862) | **Medium** | Telegram device-link fails with generic "something went wrong" when `telegram_api_id`/`api_hash` missing | [#7861](https://github.com/nearai/ironclaw/pull/7861) (merged) |
| [#7888](https://github.com/nearai/ironclaw/issues/7888) | **Medium** | Log retrieval hangs indefinitely on multiple instances | No fix PR yet |
| [#7887](https://github.com/nearai/ironclaw/issues/7887) | **Low** | Extension lookup path improvises device-link setup instructions on Telegram surface | Follow-up to #7861 |

**Stability assessment:** Two performance-correctness bugs in the agent loop are the highest-priority open items. Both have fix PRs in review. The log-hang issue (#7888) lacks an active fix and should be triaged.

## 6. Feature Requests & Roadmap Signals

| Issue | Signal |
|---|---|
| [#4625](https://github.com/nearai/ironclaw/issues/4625) | Slack channel-routed personal and team agents — *suggested P1, open since June* |
| [#7867](https://github.com/nearai/ironclaw/issues/7867) | Voice-to-text input in the WebUI composer |
| [#7871](https://github.com/nearai/ironclaw/issues/7871) | Slack-to-console bridge with rich interactive Slack UX |
| [#7893](https://github.com/nearai/ironclaw/issues/7893) | Per-automation lessons file (`ironclaw.memory.automation_lessons_set`) |
| [#7895](https://github.com/nearai/ironclaw/issues/7895) | Personality (`agent.md`) editor section in Settings UI |
| [#7889](https://github.com/nearai/ironclaw/issues/7889) | RFC: opt-in remote edge workers for the scheduler/orchestrator |
| [#7890](https://github.com/nearai/ironclaw/issues/7890) | Retire `app.css` Tailwind colour-alias compat layer before WS3b reskin |

**Near-term prediction:** The design-system cleanup (#7890) and notifications hardening (#7872–#7876) are small, self-contained items likely to land in the next patch. The per-automation lessons feature (#7893) and Slack-to-console bridge (#7871) are both scoped as v1.4.0 roadmap items and are strong candidates for the next release cycle.

## 7. User Feedback Summary

- **Telegram setup friction:** Users encounter opaque failures and incomplete agent instructions when linking Telegram accounts without pre-configured API credentials. The fix in #7861 addresses the guidance path, but #7887 shows residual UX gaps.
- **Agent loop efficiency:** The 123-second runaway loop (#7892) and the 19.7-second turn dominated by 24 KiB of unprojected MIME headers (#7891) point to pain around tool-result size management and loop-termination guards—issues that directly affect cost and responsiveness.
- **Personality configuration:** Users find it difficult to set up agent personality (#7895), requesting a dedicated Settings UI section rather than manual `agent.md` editing.
- **Log access reliability:** Multiple instances report indefinite hangs when retrieving logs (#7888), impacting operational troubleshooting.
- **Onboarding flow:** The OOBE suggestion drawer received positive follow-up work (#7816), suggesting the cumulative connect → suggest → thread flow is maturing well.

## 8. Backlog Watch

| Issue | Open Since | Concern |
|---|---|---|
| [#4625](https://github.com/nearai/ironclaw/issues/4625) | 2026-06-09 | Slack-as-channel epic—suggested P1, still open with no active PR |
| [#7888](https://github.com/nearai/ironclaw/issues/7888) | 2026-08-25 | Log hangs on multiple instances—no fix PR, confirmed repro |
| [#7895](https://github.com/nearai/ironclaw/issues/7895) | 2026-08-25 | Personality editor request—no maintainer response yet |
| [#7867](https://github.com/nearai/ironclaw/issues/7867) | 2026-08-25 | Voice-to-text in WebUI composer—no maintainer response yet |
| [#7889](https://github.com/nearai/ironclaw/issues/7889) | 2026-08-25 | RFC for remote edge workers—design-phase, needs triage decision |
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | 2026-08-18 | Persistent per-user sandbox—v1.4.0 epic, 9 comments, no active PR yet |

**Recommended maintainer attention:** #4625 (long-open P1 suggestion), #7888 (confirmed bug, no fix), and #7732 (core architectural epic with high comment engagement) are the three items most in need of a roadmap commitment or assignee.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-26

## 1. Today's Overview

LobsterAI is in an active release cycle, with two new versions shipped in the past week (2026.8.21 and 2026.8.25). The project saw **11 PRs updated in the last 24 hours**, of which 9 were merged or closed — indicating strong contributor momentum. Only **1 open issue** remains, focused on community infrastructure (WeChat group capacity) rather than a technical defect. Overall project health is **positive**: frequent releases, consistent PR throughput, and focused work on the library/artifacts subsystem and analytics instrumentation.

---

## 2. Releases

### LobsterAI 2026.8.25 (2026-08-25)
- **feat(library):** Enhanced cross-platform thumbnail and local artifact lifecycle management (#2513, #2524)
- **feat(library):** Optimized local artifact preview and interaction experience (#2524)
- No breaking changes or migration notes reported.

### LobsterAI 2026.8.21 (2026-08-21)
- **feat(dsh):** Added usage analytics for the enable toggle and workbench open events (#2515)
- **feat:** Updated dsh to version 0.1.1-rc.1 (#2516)
- **refactor(dsh):** Moved usage analytics implementation (#2516)
- No breaking changes reported.

---

## 3. Project Progress

**9 PRs merged/closed today**, spanning several subsystems:

| Area | Changes |
|---|---|
| **Library / Artifacts** | Cross-platform thumbnail lifecycle, local preview experience, flicker fix during background refresh, separation of web vs. local service preview types (#2531, #2533, #2524) |
| **Settings** | Plan model catalog added above custom model settings, with categorized model cards for text/image/video (#2530, #2535) |
| **Analytics** | Comprehensive library analytics instrumentation — exposure, filtering, search, preview, favorites, refresh tracking; 7-day last-touch attribution for publish-to-subscription conversion (#2529) |
| **DSH** | Usage analytics for enable toggle and workbench open; version bump to 0.1.1-rc.1 (#2515, #2516) |
| **UI / UX** | Fade-out of login promo tip after 5 seconds; cleanup of promo timers on auth state change (#2532) |
| **CI / Dependencies** | Dependabot updates: electron 40.2.1 → 43.4.1, actions/stale 9.1.0 → 10.2.0, actions/first-interaction bump (#1277, #1275, #1276) |

**Key theme:** The library/artifacts pipeline and analytics instrumentation are the primary focus areas this cycle.

---

## 4. Community Hot Topics

- **Issue #2536 — "WeChat group is full"** ([link](https://github.com/netease-youdao/LobsterAI/issues/2536)): A community user reports the official WeChat group has reached capacity and requests a new group. While low technical severity, this signals **growing community engagement** and active Chinese-language user base. Maintainers may want to establish additional communication channels (Discord, QQ, etc.).

No other open issues were reported in the last 24 hours, suggesting the issue tracker is in a relatively calm state.

---

## 5. Bugs & Stability

| Severity | Item | Details | Fix Status |
|---|---|---|---|
| **Medium** | #2531 — Local artifact background refresh flickering | Already **fixed and merged**. The root cause was merged state handling during background refresh causing full-page skeleton re-renders. Fix includes splitting load states, limiting concurrent requests, and adding batch query by material ID. | ✅ Merged (#2531) |
| **Low** | #2533 — Web vs. local service preview distinction | Previously ambiguous UI; now **resolved** with separate icons and labels for HTML pages vs. local services. | ✅ Merged (#2533) |

**No new crash reports or regressions** filed today. The bug pipeline is clean.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Analysis |
|---|---|---|
| **Plan model catalog** | #2530, #2535 | A structured, categorized model selection UI (text/image/video) with pricing info is being added to settings. Likely to ship in the next release. |
| **Session Fork** | #1159 (OPEN, stale) | Users can branch a cowork session from the detail view. Long-open PR — signal of sustained community interest in session management. |
| **Enhanced library analytics** | #2529 | Comprehensive tracking for library interactions and publish-to-subscription attribution suggests a **monetization/conversion focus** in the near-term roadmap. |
| **Cross-platform thumbnail lifecycle** | #2513, #2524 | Ongoing investment in the library subsystem, indicating it remains a strategic priority. |

**Prediction:** The plan model catalog and library analytics features will likely appear in the next release (post-2026.8.25). Session Fork (#1159) may need re-engagement from maintainers.

---

## 7. User Feedback Summary

- **Positive:** Users appreciate the improved local artifact preview experience and the distinction between web and local service previews (#2533), suggesting UX polish is landing well.
- **Community Engagement:** The WeChat group fullness (#2536) is a **positive pain point** — it reflects active user demand for community interaction, though it also highlights a lack of alternative communication channels.
- **Analytics Transparency:** The new tracking features (#2529) include privacy-conscious design (interval data instead of raw search content, opt-out cleanup on logout), which aligns with user expectations for data transparency.

---

## 8. Backlog Watch

| PR/Issue | Age | Status | Risk |
|---|---|---|---|
| **#1159 — Session Fork** | ~5 months (since 2026-03-31) | OPEN, stale | **Medium** — Feature has clear user value but hasn't been reviewed or merged. May need maintainer triage. |
| **#1277 — Electron bump (40→43)** | ~4 months (since 2026-04-02) | OPEN | **Low** — Dependabot PR for a major Electron upgrade; likely blocked on testing/compatibility. Worth monitoring. |
| **#1275 — actions/stale bump** | ~4 months | CLOSED (stale) | Resolved via staleness workflow. |
| **#1276 — actions/first-interaction bump** | ~4 months | CLOSED (stale) | Resolved via staleness workflow. |

**Recommendation:** Maintainers should triage #1159 (Session Fork) — it has been open the longest with clear feature value. The Electron upgrade in #1277, while low-risk, may benefit from a scheduled review given the major version jump.

---

*Digest generated from GitHub data sourced via LobsterAI on 2026-08-26.*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-26

## 1. Today's Overview

Moltis continues active development with 5 PRs and 2 issues updated in the last 24 hours. No new releases were published, suggesting the team is focused on stabilizing existing code paths before the next version. The project shows healthy community engagement with three open PRs awaiting review, and two merged/closed PRs demonstrating iterative improvement on tooling and cron reliability. Overall project health is strong with sustained contributor participation across sandboxing, tool validation, and MCP integration workstreams.

## 2. Releases

No new releases today. The latest merged changes (Brave search validation, cron context preservation) may accumulate toward an upcoming release pending maintainer triage.

## 3. Project Progress

**Merged / Closed today:**

- **#1245** — *fix(tools): validate Brave search parameters* — Exposed Brave localization parameters conditionally, normalized country/language/freshness values, and added provider-aware enums to the tool schema. Prevents misconfiguration errors when Brave is the active search provider.
- **#1243** — *fix(cron): preserve delivered channel context* — Fixed follow-up questions losing context when cron-delivered messages land in WhatsApp or other channels. Session history is now resolved by the exact conversation, enabling coherent multi-turn interactions post-delivery.

**Key advancements:** Active work spans sandbox backend expansion (Kubernetes, Coder), MCP OAuth hardening, and tool schema robustness — signaling a maturing infrastructure layer.

## 4. Community Hot Topics

- **[Issue #1118](https://github.com/moltis-org/moltis/issues/1118)** — *Kubernetes-native sandbox backend with runtimeClassName support* — 2 comments, 1 👍 | Opened 2026-06-12, last active 2026-08-25. This remains the most discussed open issue, reflecting strong community demand for VM-level isolation (Kata Containers, gVisor) in untrusted LLM command execution. The extended open duration without merge suggests architectural complexity or competing priorities.
- **[PR #1199](https://github.com/moltis-org/moltis/pull/1199)** — *Add Coder remote workspace sandbox support* — Open since 2026-08-15. Extends sandbox diversity alongside the Kubernetes effort, indicating a strategic push toward pluggable isolation backends.
- **[Issue #1224](https://github.com/moltis-org/moltis/issues/1224)** — *Tools stop working in shared Slack channels* — Recently closed (2026-08-25), likely resolved without a direct PR reference, suggesting a quick config or scope-based fix.

## 5. Bugs & Stability

| Severity | Item | Status | Notes |
|----------|------|--------|-------|
| **Medium** | [#1224](https://github.com/moltis-org/moltis/issues/1224) — Tools break in shared Slack channels | **Closed** | Resolved; likely a channel-scoping or permission issue. |
| **Low** | [#1245](https://github.com/moltis-org/moltis/pull/1245) — Brave search parameter validation | **Merged** | Preemptive fix for malformed provider requests. |
| **Low** | [#1243](https://github.com/moltis-org/moltis/pull/1243) — Cron follow-up losing channel context | **Merged** | Fix ensures WhatsApp/other channel replies maintain conversation history. |
| **Medium** | [#1232](https://github.com/moltis-org/moltis/pull/1232) — Object schemas not OpenAI-compatible | **Open** | Unspecified patch/map schemas force null values in strict mode. Affects Codex users — likely to merge soon given targeted scope. |

No crashes or regressions reported today.

## 6. Feature Requests & Roadmap Signals

- **Kubernetes sandbox backend** (#1118): High-priority feature request for enterprise-grade isolation via `runtimeClassName`. Strong signal that Moltis is targeting production/deployment scenarios where untrusted code execution requires VM-level security boundaries.
- **Coder sandbox backend** (#1199): Complements #1118 with a non-Kubernetes ephemeral workspace option. The dual submission suggests the roadmap aims for a **multi-backend sandbox abstraction** rather than a single solution.
- **MCP OAuth refinement** (#1244): Protecting-resource scope prioritization and RFC 7591 registration aligns with growing MCP ecosystem adoption — likely to ship in the next release cycle as a stability hardening patch.

**Predicted in next release:** Brave search validation (#1245), cron context fix (#1243), and OpenAI schema fix (#1232) are all candidates for the upcoming patch release.

## 7. User Feedback Summary

- **Sandbox isolation is a top concern.** Issue #1118's extended engagement (2+ months, reactions, comments) shows users need configurable isolation tiers for untrusted agent commands — a recurring theme in AI agent tooling.
- **Multi-channel continuity matters.** The cron context bug (#1243) and Slack tools issue (#1224) both point to pain around cross-platform session coherence. Users running Moltis across WhatsApp, Slack, and other channels expect conversation history to persist.
- **Tool reliability under strict schemas.** PR #1232 addresses a frustration for users deploying with OpenAI/Codex — rigid schema validation causing silent data loss (null values). This is a developer-experience pain point likely to recur as tool schemas expand.

## 8. Backlog Watch

| Item | Days Open | Risk |
|------|-----------|------|
| [#1118](https://github.com/moltis-org/moltis/issues/1118) — Kubernetes sandbox backend | ~75 days | High — core roadmap feature with community demand; long open time may signal architectural review or scope creep. |
| [#1199](https://github.com/moltis-org/moltis/pull/1199) — Coder sandbox backend | ~11 days | Medium — awaiting review; complements #1118 but independently valuable. |
| [#1244](https://github.com/moltis-org/moltis/pull/1244) — Fastmail MCP OAuth scope fix | ~1 day | Low — small, targeted fix likely to merge quickly. |
| [#1232](https://github.com/moltis-org/moltis/pull/1232) — OpenAI-safe object schemas | ~4 days | Low — small scope, clear fix; should merge soon. |

**Maintainer attention needed:** Issue #1118 has been open since mid-June with only 2 comments — consider an architectural RFC or design doc to unblock review and accelerate merge.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-26

## 1. Today's Overview

CoPaw (agentscope-ai/CoPaw) shows **high development velocity** on 2026-08-26, with 33 issues updated and 50 PRs touched in the last 24 hours. The project released a new beta version (v2.1.1-beta.3) today, while 29 PRs were merged/closed and 14 issues resolved — indicating strong maintainer responsiveness. The open-issue count (19) slightly exceeds closed, suggesting a moderate backlog of incoming reports, primarily around stability and UX polish. Overall project health is **positive**: active CI improvements, security fixes, and expanding test coverage signal a maturing release cadence.

---

## 2. Releases

### v2.1.1-beta.3 (released 2026-08-26)

- **chore(console):** pinned `@agentscope-ai/chat` to 1.1.72 ([PR #7257](https://github.com/agentscope-ai/QwenPaw/pull/7257))
- **docs(loop-engineering):** fixed `PluginAPI` → `PluginApi` casing inconsistency ([PR #7269](https://github.com/agentscope-ai/QwenPaw/pull/7269))
- **test(integration):** expanded integration test suite

> **Migration notes:** No breaking changes announced. Beta status implies ongoing validation; users on v2.1.1-beta.2 should review [Issue #7261](https://github.com/agentscope-ai/QwenPaw/issues/7261) (SSE loop regression) before upgrading.

---

## 3. Project Progress

### Merged / Closed PRs (today)

| PR | Type | Summary |
|----|------|---------|
| [#7300](https://github.com/agentscope-ai/QwenPaw/pull/7300) | docs | Updated scroll context manager blog |
| [#7299](https://github.com/agentscope-ai/QwenPaw/pull/7299) | fix | Reject conflicting chat payloads to prevent silent acks ([chrischen-coder](https://github.com/chrischen-coder)) |
| [#7293](https://github.com/agentscope-ai/QwenPaw/pull/7293) | ci | Split integration tests into 3 parallel shards (p0/p1/p2) for faster CI |
| [#7276](https://github.com/agentscope-ai/QwenPaw/pull/7276) | chore | Bumped `agentscope` dependency to 2.0.7 |
| [#7277](https://github.com/agentscope-ai/QwenPaw/pull/7277) | fix | Refreshed Aliyun and Kimi built-in model catalogs |
| [#7290](https://github.com/agentscope-ai/QwenPaw/pull/7290) | docs | Added blog post for QwenPaw Mail |
| [#7292](https://github.com/agentscope-ai/QwenPaw/pull/7292) | test | Added 19 unit test files (+5.02pp coverage, now 63.06%); fixed `/root` home-dir classification |
| [#7294](https://github.com/agentscope-ai/QwenPaw/pull/7294) | feat | Added opt-in image resizing by pixel limit (`QWENPAW_MAX_IMAGE_PIXELS`) |
| [#7274](https://github.com/agentscope-ai/QwenPaw/pull/7274) | feat | QwenPaw Creator 1.1.1: live website, desktop recording, Bailian Wan3 video, APE-benchmark review operators |

### Open PRs of note

- [#7163](https://github.com/agentscope-ai/QwenPaw/pull/7163) — **Session-level thinking modes** (Off / Low / Medium / High) with cross-device sync via Chat Metadata
- [#7190](https://github.com/agentscope-ai/QwenPaw/pull/7190) — `qwenpaw-data` PyPI-installable runtime with docker-compose GAAP demo
- [#6399](https://github.com/agentscope-ai/QwenPaw/pull/6399) — Reranker UI config panel in ReMeLightMemoryCard
- [#7119](https://github.com/agentscope-ai/QwenPaw/pull/7119) — **Security fix:** master key file created with `0o600` permissions (was insecure)

---

## 4. Community Hot Topics

| Issue | Type | Comments | Summary |
|-------|------|----------|---------|
| [#338](https://github.com/agentscope-ai/QwenPaw/issues/338) | enhancement | 9 👍1 | Webhook feature request — external apps send messages to CoPaw and poll for responses via a returned key |
| [#7258](https://github.com/agentscope-ai/QwenPaw/issues/7258) | bug | 6 | WeChat channel "show thinking process" toggle is ineffective |
| [#5720](https://github.com/agentscope-ai/QwenPaw/issues/5720) | bug | 5 (closed) | Memory leak in v1.1.12.post2 on Windows — async task and HTTP session leaks, ~5.5 MB/min growth |
| [#6810](https://github.com/agentscope-ai/QwenPaw/issues/6810) | bug | 5 | Windows installer fails to overwrite locked files (browser extension NM host); NSIS pops >4 file-in-use errors |
| [#6273](https://github.com/agentscope-ai/QwenPaw/issues/6273) | bug | 4 (open) | Inconsistent task-tracking and same-session concurrency semantics across execution paths |
| [#7261](https://github.com/agentscope-ai/QwenPaw/issues/7261) | bug | 4 (closed) | **Critical:** SSE serialization loop in v2.1.1b2 after agent-to-agent run → 100% CPU, unbounded memory, unresponsive server |
| [#7218](https://github.com/agentscope-ai/QwenPaw/issues/7218) | bug | 4 | `peer closed connection without sending complete message body` during long-reasoning / long-text flows |
| [#7182](https://github.com/agentscope-ai/QwenPaw/issues/7182) | feature | 4 (open) | Workspace-scoped Skill preload policy to avoid redundant first-turn tool discovery |
| [#7228](https://github.com/agentscope-ai/QwenPaw/issues/7228) | bug | 4 (closed) | App market shows "Install" button on hover for already-installed apps |
| [#7196](https://github.com/agentscope-ai/QwenPaw/issues/7196) | enhancement | 3 👍1 (closed) | Make reasoning/thinking process collapsible by default to reduce visual clutter |
| [#7285](https://github.com/agentscope-ai/QwenPaw/issues/7285) | bug | 3 (closed) | Long web-chat sessions cause severe desktop lag (mouse 2s/frame) — browser rendering bottleneck |
| [#7129](https://github.com/agentscope-ai/QwenPaw/issues/7129) | bug | 2 (closed) | WPR-traced Chrome main-thread blocking during long session + streaming output |

**Underlying needs:** Users are pushing hard on **(a)** performance/stability under sustained load, **(b)** UX polish around thinking-process visibility, and **(c)** integration extensibility (webhooks, workspace-scoped skills). The webhook request (#338) reflects a growing ecosystem of users treating CoPaw as a backend service.

---

## 5. Bugs & Stability

### Critical / High Severity

| Issue | Title | Status | Fix PR? |
|-------|-------|--------|---------|
| [#7261](https://github.com/agentscope-ai/QwenPaw/issues/7261) | SSE serialization runaway loop → 100% CPU, unbounded memory | **Closed** | Likely addressed in beta.3 |
| [#5720](https://github.com/agentscope-ai/QwenPaw/issues/5720) | Memory leak: async tasks + HTTP sessions not cleaned (Windows) | **Closed** | Root cause identified; awaiting upstream fix |
| [#7285](https://github.com/agentscope-ai/QwenPaw/issues/7285) | Long web-chat → desktop freezes (browser rendering) | **Closed** | Related to #7129; browser-side fix needed |
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) | Desktop Tauri bundle ships OpenSSL 3.0.x (Python 3.11) → TLS DPI resets | **Open** | No fix PR yet; suggests bumping to Python 3.13 |
| [#7296](https://github.com/agentscope-ai/QwenPaw/issues/7296) | OpenAI Responses multi-turn fails with 400 "Referenced reasoning item not found" | **Open** | No fix PR yet |
| [#7301](https://github.com/agentscope-ai/QwenPaw/issues/7301) | MCP legacy migration leaves dangling credential ref → `CredentialNotFoundError` on every new session | **Open** (new today) | No fix PR yet |

### Medium Severity

| Issue | Title | Status |
|-------|-------|--------|
| [#7218](https://github.com/agentscope-ai/QwenPaw/issues/7218) | Incomplete chunked read on long-reasoning flows | Open |
| [#6273](https://github.com/agentscope-ai/QwenPaw/issues/6273) | Inconsistent task-tracking / concurrency semantics | Open |
| [#7266](https://github.com/agentscope-ai/QwenPaw/issues/7266) | subAgent resolves wrong folder path | Open |
| [#7282](https://github.com/agentscope-ai/QwenPaw/issues/7282) | Markdown lists render with excessive vertical spacing | Open |
| [#7258](https://github.com/agentscope-ai/QwenPaw/issues/7258) | WeChat channel thinking-process toggle ineffective | Open |

### Low / UI Polish

| Issue | Title | Status |
|-------|-------|--------|
| [#7228](https://github.com/agentscope-ai/QwenPaw/issues/7228) | App market hover shows wrong button state | Closed |
| [#7256](https://github.com/agentscope-ai/QwenPaw/issues/7256) | "应用" renamed to "市场" in sidebar — user prefers original | Closed |
| [#7297](https://github.com/agentscope-ai/QwenPaw/issues/7297) | QQ chat memory lost on agent restart | Open |
| [#7291](https://github.com/agentscope-ai/QwenPaw/issues/7291) | qwenpaw-creator Win11 example-project pull fails | Open |

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Request | Likelihood for Next Release |
|------------|---------|----------------------------|
| [#7163](https://github.com/agentscope-ai/QwenPaw/pull/7163) | Session-level thinking modes (Off/Low/Med/High) with persistence | **High** — PR already open, well-scoped |
| [#338](https://github.com/agentscope-ai/QwenPaw/issues/338) | Webhook support for external integrations | **Medium** — community demand growing |
| [#7182](https://github.com/agentscope-ai/QwenPaw/issues/7182) | Workspace-scoped Skill preload policy | **Medium** — clear use case, not yet PR'd |
| [#7280](https://github.com/agentscope-ai/QwenPaw/issues/7280) | Auto-clear completed background tasks from list | **Medium** — simple UX improvement |
| [#7263](https://github.com/agentscope-ai/QwenPaw/issues/7263) | Orange indicator on bottom-bar when task completes | **Low** — nice-to-have visual cue |
| [#7279](https://github.com/agentscope-ai/QwenPaw/issues/7279) | Pop-up choice dialogs instead of text input for multi-option model responses | **Low** — UX enhancement |
| [#7013](https://github.com/agentscope-ai/QwenPaw/issues/7013) | Unified tool panel / web preview / interactive terminal in Chat | **Medium** — large scope, may span multiple releases |
| [#7287](https://github.com/agentscope-ai/QwenPaw/issues/7287) | Zero-intrusion "skin gateway" for theme customization | **Low** — speculative proposal |

---

## 7. User Feedback Summary

**Satisfaction drivers:**
- Users appreciate the rapid release cadence (beta.2 → beta.3 in days) and visible bug closure rate.
- The Creator 1.1.1 feature set (live website, recording, video generation) is generating positive engagement.
- Test coverage improvements (+5pp) and CI parallelization signal investment in quality.

**Pain points:**
- **Performance under load** is the #1 complaint: long sessions cause browser frame drops (#7285, #7129), and SSE loops can crash the server (#7261).
- **Memory leaks on Windows** remain unresolved across multiple versions (#5720, #7259).
- **Desktop TLS issues** on certain carrier networks (#7298) block enterprise/self-hosted use cases.
- **UX inconsistencies** (wrong button states, naming changes, thinking-process visibility) create friction for power users.
- **MCP migration bugs** (#7301) break new sessions immediately after upgrade — a trust-eroding issue.

---

## 8. Backlog Watch

| Issue / PR | Age | Priority | Notes |
|------------|-----|----------|-------|
| [#338](https://github.com/agentscope-ai/QwenPaw/issues/338) — Webhook feature | ~5.5 months | **High** (community demand) | Open since March; 9 comments, 1 👍. No PR yet. |
| [#6273](https://github.com/agentscope-ai/QwenPaw/issues/6273) — Task-tracking concurrency semantics | ~1 month | **High** (stability) | Open; affects multi-agent workflows. |
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) — OpenSSL 3.0.x TLS on desktop | 1 day | **High** (enterprise blocker) | No fix PR; suggests Python 3.13 bump in Tauri CI. |
| [#73

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-26

## 1. Today's Overview

ZeroClaw is showing strong development velocity with **50 issues and 50 PRs updated** in the last 24 hours, indicating an active and healthy contributor base. The project is in a mid-cycle phase — no new releases today — with significant effort directed at RFC ratification, security hardening, and runtime stability. Multiple high-risk security issues (cron scoping, delegate workspace isolation, Copilot credential cache) are being actively addressed, and the parallel runtime hardening effort is gaining traction. The maintainers are also pushing architectural improvements around dependency inversion and execution-tree budget ownership.

## 2. Releases

**No new releases** published today. The latest ratified RFC rollout is tracking against `0.8.4` (Issue #6808). No migration or breaking-change releases were cut.

## 3. Project Progress

**Merged/Closed Today:** 1 PR closed — `#10271` (chore: consolidate crate-local `floor_char_boundary` copies onto std, a follow-up from the UTF-8 truncation audit). 12 issues closed in the last 24h, primarily bug fixes and follow-up tasks.

**Key PRs Advanced:**
- **#10376** — Drift guards for channel production registration (test-only, risk: low)
- **#10377** — Gate `axum` dependency by channel features to reduce surface (risk: low)
- **#10375** — Generate typed `StatusResponse` for gateway `GET /api/status` (risk: high)
- **#10368** — Stabilize the `concurrent_stale_start_is_serialized_before_cleanup` IPC test
- **#10362** — Make cron workspace assertion portable across Windows/POSIX paths
- **#10350** — Add measurement-only Windows test jobs to CI (advisory, not yet required)

## 4. Community Hot Topics

| Issue/PR | Comments | Focus | Link |
|----------|----------|-------|------|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) — RFC: Work Lanes, Board Automation, Label Cleanup | 24 | Governance / triage process | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue tracker | 14 | RFC/design decision workflow | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) — Separate authoritative memory from enrichment connectors | 14 | Architecture / memory backend | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) — Wire protocol first-class in provider construction | 12 | Provider onboarding RFC | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) |
| [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) — Harden runtime test fixtures under parallel gate | 9 | Test reliability / P1 bug | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) |
| [#8132](https://github.com/zeroclaw-labs/zeroclaw/issues/8132) — Evaluate Rust/WASM web UI before React/Vite migration | 9 | Web frontend architecture | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8132) |

**Analysis:** The top-discussed items reveal two dominant community needs: (1) **governance clarity** — contributors want transparent, automated triage and a visible maintainer decision queue; (2) **architectural boundaries** — the memory separation RFC and wire-protocol-first RFC both signal a community push to decouple layered concerns before the v0.9.0 release. The WASM web UI evaluation (#8132) reflects ongoing tension between developer ergonomics and the project's local-first, no-Node.js philosophy.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? | Link |
|----------|-------|---------|---------|------|
| **S0** | [#9947](https://github.com/zeroclaw-labs/zeroclaw/issues/9947) | Cron tools not scoped to owning agent — any agent can read/modify/delete another's jobs | Not yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9947) |
| **S0** | [#9206](https://github.com/zeroclaw-labs/zeroclaw/issues/9206) | Agent cron intermittently resolves `workspace_dir` to `/` (root filesystem) | Closed — needs follow-up | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9206) |
| **S1** | [#10357](https://github.com/zeroclaw-labs/zeroclaw/issues/10357) | Tool execution error path discards detailed error body — agents only see "HTTP 400" | Not yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10357) |
| **S2** | [#9872](https://github.com/zeroclaw-labs/zeroclaw/issues/9872) | Bounded delegate resolves filesystem to delegator's workspace instead of own | Not yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9872) |
| **S2** | [#10058](https://github.com/zeroclaw-labs/zeroclaw/issues/10058) | ZeroCode file explorer search ignores row/page navigation | Closed | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10058) |
| **S2** | [#8999](https://github.com/zeroclaw-labs/zeroclaw/issues/8999) | ZeroCode streamed turns misinterpreted as log data by small local models | Closed — needs follow-up | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8999) |
| **Flaky** | [#10371](https://github.com/zeroclaw-labs/zeroclaw/issues/10371) | `concurrent_stale_start_is_serialized_before_cleanup` panics under parallel harness | PR #10368 in progress | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10371) |

**Notable:** Two **S0-severity** security bugs dominate — the cron scoping issue (#9947) is a cross-agent access control flaw, and the workspace resolution to `/` (#9206) poses data-loss risk. Both remain open with no merged fix yet. The Copilot credential cache hardening (#10370) addresses a related trust-boundary concern.

## 6. Feature Requests & Roadmap Signals

| Item | Description | Likelihood for v0.9.0 | Link |
|------|-------------|----------------------|------|
| Multi-session gateway web chat | Session sidebar with new/switch/rename/delete (#7543) | **High** — already in-progress | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7543) |
| Execution-tree iteration budgets | `max_execution_tree_iterations` per runtime profile (#10351, #9323) | **High** — PR #10351 open, RFC ratified | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9323) |
| Tool registry refresh on config change | No restart needed after enabling/disabling built-in tools (#10297) | **Medium** — needs maintainer review | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10297) |
| Rust/WASM web UI prototype | Replace React/Vite with Dioxus/Leptos/Yew (#8132) | **Low** — evaluation phase, no commitment | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8132) |
| Household edge mesh with pull workers | Opt-in decentralized runtime across idle devices (#10360) | **Low** — early RFC, p3 priority | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10360) |
| v0.9.0 auth/security/gateway hardening | Tracker for breaking-change queue (#7432) | **Definite** — core v0.9.0 scope | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7432) |

## 7. User Feedback Summary

**Pain Points:**
- **Cron job security:** Multi-agent users report that any agent can access another's cron jobs by ID (#9947) — a serious cross-tenant isolation gap.
- **Delegate workspace leakage:** Bounded-mode delegation writes files to the delegator's workspace instead of the delegate's (#9872), breaking sandbox expectations.
- **Poor error visibility:** Tool failures return only bare HTTP status codes to agents, making debugging nearly impossible (#10357).
- **ZeroCode local-model UX:** Small Ollama models interpret streamed chat turns as protocol/log data (#8999), and file explorer search navigation is broken (#10058).
- **Restart fatigue:** Changing tool configuration requires a full daemon restart (#10297), disrupting long-running agent sessions.

**Satisfaction Signals:**
- The Anthropic refusal-handling fix (#9272) and terminal provider failure surfacing (#10234) show the team is responsive to provider-error-quality complaints.
- Telegram media-group batching (#8955) addresses a real multi-photo workflow gap.
- ZeroRelay secure transport (#10142) signals serious investment in remote-agent security.

## 8. Backlog Watch

| Issue | Author | Days Open | Risk | Blocker | Link |
|-------|--------|-----------|------|---------|------|
| [#9103](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) — Separate memory storage from enrichment connectors | yanchenko | 72 | High | Maintainer review needed | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9103) |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) — Wire protocol first-class in provider onboarding | Taswen | 91 | High | Maintainer review needed | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) |
| [#9947](https://github.com/zeroclaw-labs/zeroclaw/issues/9947) — Cron tools not agent-scoped (S0) | wromansky | 45 | High (S0) | No fix PR yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9947) |
| [#9872](https://github.com/zeroclaw-labs/zeroclaw/issues/9872) — Delegate workspace isolation bug | rawlink | 48 | High | No fix PR yet | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9872) |
| [#10360](https://github.com/zeroclaw-labs/zeroclaw/issues/10360) — Household edge mesh RFC | kvnloo | 1 | High | New, needs review | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10360) |
| [#10346](https://github.com/zeroclaw-labs/zeroclaw/issues/10346) — Gateway/channels heartbeat MCP-registry caching mismatch | cheng315ncu | 1 | High | New, needs review | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10346) |
| [#10297](https://github.com/zeroclaw-labs/zeroclaw/issues/10297) — Refresh tool registries after config changes | Audacity88 | 2 | High | Needs maintainer review | [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/10297) |

**Maintainer Attention Required:** Two **S0-priority security bugs** (#9947, #9206) and two high-risk architectural RFCs (#9103, #8396) have been open for 45–91 days without resolution. The v0.9.0 auth/security tracker (#7432) remains the coordinating surface — its milestone page is the source of truth for what will ship.

---

*Generated from ZeroClaw GitHub data on 2026-08-26. Data source: github.com/zeroclaw-labs/zeroclaw.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*