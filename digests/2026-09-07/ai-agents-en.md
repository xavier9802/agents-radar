# OpenClaw Ecosystem Digest 2026-09-07

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-07 04:04 UTC

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



# OpenClaw Project Digest — 2026‑09‑07

## 1. Today’s Overview
OpenClaw activity remains **very high** with 500 issues and 500 pull requests updated in the last 24 hours (317 open/active issues, 183 closed; 275 open PRs, 225 merged/closed). No new releases were published today. The project shows strong community engagement and a steady flow of maintenance, bug fixes, and refactor work, though several P1/P0 regressions and session‑state stability concerns persist.

## 2. Releases
*No new releases were published today.*

## 3. Project Progress
**Merged/Closed PRs (today):**
- [#140712](https://github.com/openclaw/openclaw/pull/140712) – Refactor: share latest‑generation indexing across registry, cron, and subagent announcement projection.
- [#140741](https://github.com/openclaw/openclaw/pull/140741) – Refactor: memory‑lancedb embedding fallback tests now run through actual HTTP requests.
- [#140739](https://github.com/openclaw/openclaw/pull/140739) – Performance: selected‑day session metrics are now computed once per render in the web UI.

**Closed Issues (today):**
- [#79077](https://github.com/openclaw/openclaw/issues/79077) – Telegram bot‑to‑bot / guest‑bot support (stale, P2).
- [#124991](https://github.com/openclaw/openclaw/issues/124991) – CLI session reseed inert on SQLite session stores (P1).
- [#78963](https://github.com/openclaw/openclaw/issues/78963) – WhatsApp listen‑only / hooks‑only mode (P2).
- [#140535](https://github.com/openclaw/openclaw/issues/140535) – Discord `/new` does not reset channel session (P1).
- [#136200](https://github.com/openclaw/openclaw/issues/136200) – Feishu quoted merged‑forward messages show only placeholder text (P1).
- [#106920](https://github.com/openclaw/openclaw/issues/106920) – Gateway fails to restart after update (P0).

## 4. Community Hot Topics
**Most‑commented issues (top 5):**
1. [#79077](https://github.com/openclaw/openclaw/issues/79077) – Telegram bot‑to‑bot & guest‑bot modes (14 comments, 8 👍). *Need:* Leverage Telegram’s May‑2026 platform features for direct bot‑to‑bot communication and guest‑bot interactions.
2. [#97616](https://github.com/openclaw/openclaw/issues/97616) – Hook/tool child‑process leak causing zombie accumulation (14 comments, 1 👍). *Need:* Runtime health and resource‑leak prevention.
3. [#135111](https://github.com/openclaw/openclaw/issues/135111) – Intermittent malformed‑JSON tool‑call errors after v2026.8.1 upgrade (14 comments). *Need:* Stability of provider tool‑call parsing.
4. [#119720](https://github.com/openclaw/openclaw/issues/119720) – Synchronous agent persistence blocks Gateway event loop at scale (12 comments). *Need:* Horizontal scaling and event‑loop non‑blocking guarantees.
5. [#140010](https://github.com/openclaw/openclaw/issues/140010) – Windows sleep/resume leaves gateway unreachable for 30‑60s+ (9 comments). *Need:* Robust recovery after OS‑level power states.

## 5. Bugs & Stability
**P0 / P1 bugs reported or updated recently (ranked by severity):**
- [#136203](https://github.com/openclaw/openclaw/issues/136203) – **P0** – Windows de‑DE 2026.8.2 upgrade leaves Doctor maintenance blocked; legacy workspace state remains. *(No fix PR yet.)*
- [#140497](https://github.com/openclaw/openclaw/issues/140497) – **P0** – Discord setup accepts application ID as bot token, channel stuck `not‑running`. *(No fix PR yet.)*
- [#114967](https://github.com/openclaw/openclaw/issues/114967) – **P0** – Agent‑driven live update creates a launchctl keepalive that force‑restarts the gateway every ~2 minutes. *(No fix PR yet.)*
- [#106920](https://github.com/openclaw/openclaw/issues/106920) – **P0** – Gateway fails to restart after `openclaw update`. *(Closed; likely resolved by update process.)*
- [#97616](https://github.com/openclaw/openclaw/issues/97616) – **P1** – Child‑process leak (zombies) from hook/tool execution. *(No fix PR yet.)*
- [#135111](https://github.com/openclaw/openclaw/issues/135111) – **P1** – “Provider completed tool call with malformed JSON arguments” regression on v2026.8.1. *(No fix PR yet.)*
- [#119720](https://github.com/openclaw/openclaw/issues/119720) – **P1** – Synchronous persistence blocks Gateway event loop at scale. *(No fix PR yet.)*
- [#140010](https://github.com/openclaw/openclaw/issues/140010) – **P1** – Windows sleep/resume WebSocket reconnection stalls. *(No fix PR yet.)*
- [#124991](https://github.com/openclaw/openclaw/issues/124991) – **P1** – CLI session reseed inert on SQLite stores. *(Closed; may need follow‑up.)*
- [#127148](https://github.com/openclaw/openclaw/issues/127148) – **P1** – Codex sessions.compact acquires second app‑server, hits active‑writer conflict. *(No fix PR yet.)*
- [#118018](https://github.com/openclaw/openclaw/issues/118018) – **P1** – Stale subagent completion delivered into replaced requester lifecycle. *(No fix PR yet.)*
- [#139714](https://github.com/openclaw/openclaw/issues/139714) – **P1** – Post‑core update resume child admits an un‑finalizable `update_runs` row. *(No fix PR yet.)*
- [#121232](https://github.com/openclaw/openclaw/issues/121232) – **P1** – Memory‑dreaming ranker/applier deadlock (“Ranked N, Promoted 0”). *(No fix PR yet.)*
- [#139578](https://github.com/openclaw/openclaw/issues/139578) – **P1** – llama.cpp EmbeddingGemma runs at ubatch 512 regression. *(No fix PR yet.)*
- [#99910](https://github.com/openclaw/openclaw/issues/99910) – **P1** – Memory dreaming run pegs gateway event loop for ~10 min. *(No fix PR yet.)*
- [#132720](https://github.com/openclaw/openclaw/issues/132720) – **P1** – claude‑cli 410 session_expired after beta upgrade. *(No fix PR yet.)*
- [#54488](https://github.com/openclaw/openclaw/issues/54488) – **P1** – Session lane starvation; followup drain monopolizes lane for 20‑30 min. *(No fix PR yet.)*
- [#101929](https://github.com/openclaw/openclaw/issues/101929) – **P1** – Context‑overflow precheck estimator over‑counts 2.3‑2.6× vs billed usage. *(No fix PR yet.)*
- [#92241](https://github.com/openclaw/openclaw/issues/92241) – **P1** – Gateway holds stale module import paths after rollback, drops inbound messages. *(No fix PR yet.)*
- [#113701](https://github.com/openclaw/openclaw/issues/113701) – **P1** – Context overflow with large tool outputs enters failure loop. *(No fix PR yet.)*
- [#139847](https://github.com/openclaw/openclaw/issues/139847) – **P1** – Message sent during active reply run is dropped (“no active tool authority snapshot”). *(No fix PR yet.)*
- [#134896](https://github.com/openclaw/openclaw/issues/134896) – **P1** – 2026.8.1 update triggers 5‑blocker gateway restart cascade + doctor self‑failure. *(No fix PR yet.)*
- [#137927](https://github.com/openclaw/openclaw/issues/137927) – **P1** – Internal context block leaks into visible Telegram messages. *(No fix PR yet.)*
- [#119454](https://github.com/openclaw/openclaw/issues/119454) – **P1** – Stuck‑session recovery self‑suppresses on leaked idle embedded run. *(No fix PR yet.)*
- [#124393](https://github.com/openclaw/openclaw/issues/124393) – **P1** – Transcript sync rewrite deletes concurrently committed rows. *(No fix PR yet.)*
- [#134579](https://github.com/openclaw/openclaw/issues/134579) – **P1** – Active Memory `before_prompt_build` handler never dispatched since 2026.8.1‑beta.3. *(No fix PR yet.)*
- [#139215](https://github.com/openclaw/openclaw/issues/139215) – **P1** – Cron scheduler silently swallows scheduled ticks since 2026.9.1. *(No fix PR yet.)*
- [#102534](https://github.com/openclaw/openclaw/issues/102534) – **P1** – Cron timer permanently stops after heavy timeouts. *(No fix PR yet.)*
- [#95746](https://github.com/openclaw/openclaw/issues/95746) – **P1** – Memory dreaming exhausts local model context via parallel subagent runs. *(No fix PR yet.)*

**Notable closed bug:**
- [#140535](https://github.com/openclaw/openclaw/issues/140535) – Discord `/new` does not reset channel session. *(Closed; fix pending or accepted as‑is.)*

## 6. Feature Requests & Roadmap Signals
- [#79077](https://github.com/openclaw/openclaw/issues/79077) – Telegram bot‑to‑bot & guest‑bot support (stale, P2). *Likelihood:* Medium; depends on Telegram platform maturity.
- [#71058](https://github.com/openclaw/openclaw/issues/71058) – Multiple Azure/Teams bots on a single Gateway (P2). *Likelihood:* Medium; requires config schema expansion.
- [#51572](https://github.com/openclaw/openclaw/issues/51572) – Fire session‑memory hook on reset/prune, not just compaction (P2). *Likelihood:* High; low‑risk enhancement.
- [#99583](https://github.com/openclaw/openclaw/issues/99583) – Intelligent session auto‑titling with lazy generation & topic‑aware renames (P3). *Likelihood:* Medium; UX polish.
- [#14376](https://github.com/openclaw/openclaw/issues/14376) – Reason‑aware cron guardrails (quota/auth/rate‑limit backoff + circuit breaker) (P2). *Likelihood:* High; operational safety.
- [#120244](https://github.com/openclaw/openclaw/issues/120244) – RFC: cron maintenance window with role isolation (P3). *Likelihood:* Low‑medium; requires design consensus.
- [#84242](https://github.com/openclaw/openclaw/issues/84242) – Expose `memory-lancedb` tools as callable agent tools (P2). *Likelihood:* Medium; plugin integration.

## 7. User Feedback Summary
**Pain points:**
- **Session & context instability:** Multiple reports of session‑lane starvation, transcript overwrite races, context‑overflow mis‑estimation, and large‑tool‑output failures causing loop‑back errors.
- **Update & upgrade regressions:** Several users experienced broken restarts, stale module paths, blocked Doctor maintenance, and cron scheduler failures after upgrading (2026.8.1 → 2026.9.x).
- **Platform‑specific quirks:** Windows sleep/resume recovery stalls, Discord setup accepting invalid tokens, Feishu merged‑forward message placeholder text, Telegram internal‑context leakage.
- **Resource leaks:** Child‑process zombies from hooks/tools, memory‑dreaming runs pegging the event loop for minutes.
- **Multi‑agent & scheduling complexity:** Explicit ownership modes trigger `AgentSelectionRequiredError`, cron jobs silently drop ticks, and stuck‑session recovery self‑suppresses.

**Satisfaction signals:**
- High engagement on feature requests (Telegram, Teams, auto‑titling) indicates users want richer channel support and better session hygiene.
- Refactor PRs (shared indexing, portable redaction, skill‑status types) show maintenance effort to reduce drift and improve consistency.

## 8. Backlog Watch
**Long‑unanswered or stale high‑priority issues requiring maintainer attention:**
- [#119720](https://github.com/openclaw/openclaw/issues/119720) – Synchronous agent persistence blocking Gateway event loop at scale (P1, diamond lobster). *Last updated:* 2026‑09‑06.
- [#54488](https://github.com/openclaw/openclaw/issues/54488) – Session lane starvation (followup drain monopolizes lane for 20‑30 min) (P1, diamond lobster). *Last updated:* 2026‑09‑06.
- [#99910](https://github.com/openclaw/openclaw/issues/99910) – Memory dreaming run pegs gateway event loop for

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — AI Agent & Personal Assistant Open-Source Ecosystem
**Date: 2026-09-07**

---

## 1. Ecosystem Overview

The personal AI assistant and agent open-source ecosystem in September 2026 is characterized by intense stabilization activity following a wave of v2.x releases. Two projects—OpenClaw and CoPaw—dominate issue and PR volume, both grappling with session-state reliability, context retention, and event-loop blocking at scale. A second tier of projects (Hermes Agent, ZeroClaw, NanoClaw) shows focused bug-fix cycles around provider contracts, daemon reliability, and channel robustness. A third tier (PicoClaw, ZeptoClaw, NullClaw, Moltis, LobsterAI, IronClaw) operates at lower cadence, either in quiet maintenance or early-stage development. The dominant architectural shift across the ecosystem is a move toward **durable, backend-hosted session models** and **enforceable multi-agent policy boundaries**, signaling maturation beyond proof-of-concept agents.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Open Issues | Releases | Health |
|---|---|---|---|---|---|
| **OpenClaw** | 500 updated | 500 updated (275 open, 225 merged) | 317 active | None | 🟡 Strained — P0/P1 regression burst |
| **CoPaw** | 31 updated | 26 updated (20 open, 6 merged) | 20 active | None | 🟡 Stabilization wave |
| **Hermes Agent** | 50 updated | 50 updated | Multiple open P0/P1 | v0.21.0 (Aug 31) | 🟡 Regression cycle post-release |
| **ZeroClaw** | 33 updated | 50 updated | Multiple S1 bugs | None (v0.8.5 freeze) | 🟢 Active stabilization |
| **NanoBot** | 0 opened | 16 touched (5 merged, 11 open) | 0 | None | 🟢 Good |
| **NanoClaw** | 2 updated | 16 updated | 1 critical (Telegram) | v2.3.0 (Aug 24) | 🟢 Stable |
| **IronClaw** | 0 updated | 13 updated (3 merged, 10 open) | None | None | 🟢 Stable |
| **LobsterAI** | 1 updated | 1 merged | 1 stale | None | 🟡 Quiet stabilization |
| **PicoClaw** | 4 updated | 2 updated | 2 stale (critical) | None | 🟡 Stale high-priority bugs |
| **ZeptoClaw** | 1 updated | 0 | 1 (policy inheritance) | None | 🟡 Low activity |
| **NullClaw** | 0 | 1 open | 0 | None | 🟢 Stable but quiet |
| **Moltis** | 0 | 2 open | 0 | None | 🟡 Stable but quiet |

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Largest community and issue volume** by far (500x vs. next-highest 50 for Hermes), indicating the broadest user base and most active contributor pool.
- **Breadth of channel integrations** — Telegram, Discord, WhatsApp, Feishu, WeCom, and more — unmatched by any single peer project.
- **Provider-agnostic architecture** with a contract-based provider system (mirroring NanoClaw's emerging approach), supporting Claude, Codex, OpenCode, and Cursor.

**Technical approach differences:**
- Unlike **NanoBot** (lightweight, Python, focused on CLI/TUI ergonomics) and **PicoClaw** (embedded/RISC-V target), OpenClaw is a full gateway-centric runtime with session lanes, cron scheduling, and memory dreaming — positioning it as an infrastructure layer rather than a client tool.
- **ZeroClaw** shares OpenClaw's gateway architecture but is further along in RFC-driven session-architecture design; OpenClaw is still in reactive bug-fix mode for many of the same classes of issues (event-loop blocking, session persistence).

**Community size comparison:**
OpenClaw's 500-issue/PR daily volume is ~10× Hermes Agent and ~16× CoPaw, suggesting an order-of-magnitude larger adoption base. NanoBot and NanoClaw sit in a mid-tier with 16–50 daily touches. PicoClaw, ZeptoClaw, NullClaw, Moltis, and LobsterAI operate at the lower end (1–4 daily touches).

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Event-loop blocking by synchronous I/O** | OpenClaw (#119720), NanoBot (#5580), CoPaw (#7363) | Async session persistence; non-blocking file I/O; coordinator redesign |
| **Session persistence & context retention** | OpenClaw (#54488, #124393), CoPaw (#7579, #7584), ZeroClaw (#10197, #9378), PicoClaw (#3351) | Append-only history; no destructive compression; crash-recovery of in-flight turns |
| **Multi-agent delegation & policy safety** | ZeroClaw (#9487, #9488), ZeptoClaw (#664), NanoClaw (provider contracts) | Policy inheritance enforcement; capability-bound children; cross-device group sessions |
| **Channel rendering & message UX** | OpenClaw (#136200, #137927), CoPaw (#7585, #7586, #7570), ZeroClaw (#10426) | Markdown table rendering; intermediate message cleanup; progress indicators in Telegram/Feishu |
| **Provider contract formalization** | NanoClaw (#3727, #3586), OpenClaw (provider refactor PRs), Hermes Agent (pricing overrides #92613) | Typed provider interfaces; custom pricing; ACP/MCP tool registration reliability |
| **Cron/scheduler reliability** | OpenClaw (#139215, #102534), Hermes Agent (#104453), ZeroClaw (#9191), CoPaw (#7589) | Wall-clock timeouts; systemd restart safety; heartbeat tick delivery guarantees |
| **Resource leak prevention** | OpenClaw (#97616 — zombie processes), OpenClaw (#99910 — memory dreaming pegs loop) | Child-process lifecycle management; bounded parallelism for background runs |
| **Windows platform parity** | OpenClaw (#136203, #140010), ZeroClaw (#7462 — 74 test failures), CoPaw (#7363) | Path portability; sleep/resume recovery; Windows-specific test coverage |

---

## 5. Differentiation Analysis

| Project | Target User | Technical Architecture | Key Differentiator |
|---|---|---|---|
| **OpenClaw** | Power users, multi-channel deployments | Gateway runtime with session lanes, memory dreaming, cron | Breadth of channel integrations; infrastructure-grade feature set |
| **NanoBot** | Developers, CLI enthusiasts | Python async, TUI-first, marketplace skills | Lightweight; fast iteration; WeCom/Telegram focus; test stability investment |
| **Hermes Agent** | Multi-bot group chat users | Gateway + Desktop app; ACP integration | Group-chat host-offline continuity; reasoning-effort visibility; Skills Hub |
| **PicoClaw** | Embedded/edge AI (RISC-V, RV1106) | OpenClaw-compatible runtime for low-power hardware | Only project targeting resource-constrained embedded deployments |
| **NanoClaw** | Multi-provider agent users | Contract-based provider system (Claude, Codex, OpenCode, Cursor) | Provider diversity as first-class concept; contract enforcement at core |
| **NullClaw** | MCP server developers | Zig-based MCP server | ZeroClaw sibling; stdio MCP timeout/lifecycle focus; test-heavy (7,373 tests) |
| **IronClaw** | Web UI-centric users | Rust backend + React web UI | Dependabot hygiene; web transcript UX polish; small but focused team |
| **LobsterAI** | Multi-agent management (Chinese market) | OpenClaw fork; web UI for agent/task management | Agent deletion/switching UX; Windows test parity investment |
| **Moltis** | TLS/WebSocket protocol correctness | Rust; focuses on ALPN and shell execution diagnostics | Protocol-level correctness; RFC 8441 readiness; small contributor base |
| **CoPaw** | QwenPaw users (multi-agent, LAN LLM) | Python; advisor mode; skill v2 | Dual-model advisor loop; Skill approval workflow; LAN LLM server focus |
| **ZeptoClaw** | Multi-agent safety researchers | Rust; delegation system with policy inheritance | Only project explicitly addressing delegated-agent policy containment as a safety requirement |
| **ZeroClaw** | Architecture-forward agent users | Gateway with RFC-driven session/attachment/WASM plugin design | Most mature RFC process; durable session replay; WASM plugin runtime |

---

## 6. Community Momentum & Maturity

**Rapidly Iterating (high velocity, active fixes):**
- **OpenClaw** — 500 daily touches, but burdened by P0/P1 regressions; momentum is high but quality is strained.
- **CoPaw** — 31 issues/26 PRs daily; first-time contributors landing fixes; stabilization wave around v2.2.
- **ZeroClaw** — 33 issues/50 PRs; active RFC process with revision tracking; rapid maintainer follow-through on S1 bugs.
- **Hermes Agent** — 50/50 daily; post-v0.21.0 regression burst with responsive fix PRs.

**Steady & Focused (moderate velocity, controlled cadence):**
- **NanoBot** — 16 PRs daily, zero open issues; test stabilization and provider extensibility focus.
- **NanoClaw** — 16 PRs daily; provider-contract refactor reaching completion; one critical Telegram bug open.
- **IronClaw** — 13 PRs daily; maintainers self-directing UI polish; no community issues filed.

**Stabilizing / Quiet (low velocity, maintenance phase):**
- **LobsterAI** — 1 merged PR; stale UX bug (5+ months); test-parity work ongoing.
- **PicoClaw** — 4 issues/2 PRs; critical data-loss bug stale; embedded-device niche.
- **Moltis** — 2 open PRs; protocol-correctness focus; minimal community churn.
- **NullClaw** — 1 open PR; stable test baseline; low maintainer momentum.
- **ZeptoClaw** — 1 open issue (policy inheritance); architectural hardening phase.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Durable session architecture** | ZeroClaw RFCs #9487/#9488, CoPaw memory-lifecycle refactor #7561, PicoClaw data-loss bug #3351, OpenClaw session-lane starvation #54488 | Session persistence is the #1 reliability concern; append-only history and crash-recovery are table-stakes for production agents |
| **Async/non-blocking I/O as hard requirement** | OpenClaw #119720, NanoBot #5580, CoPaw #7363, ZeroClaw daemon stack overflow #10230 | Any agent runtime blocking the event loop on file I/O or sync calls will face user-visible freezes; async-by-default is now expected |
| **Multi-agent policy containment** | ZeptoClaw #664, ZeroClaw #9487, NanoClaw provider contracts | As delegation becomes common, enforceable policy inheritance — not just functional delegation — is emerging as a safety differentiator |
| **Provider-agnostic contract systems** | NanoClaw #3727/#3586, OpenClaw provider refactor, Hermes Agent pricing overrides #92613 | Markets are demanding support for Claude, Codex, OpenCode, Cursor, and custom providers; typed provider contracts are the architectural response |
| **Channel UX as a competitive frontier** | CoPaw Telegram/Feishu fixes, OpenClaw Feishu #136200, ZeroClaw progress indicators #10426, Hermes Agent group-chat continuity #97681 | Channel rendering quality (Markdown tables, progress cards, intermediate message cleanup) is becoming a key user-facing differentiator |
| **Embedded/edge agent runtimes** | PicoClaw (RV1106, RISC-V), NullClaw (Zig MCP server) | Demand exists for agent runtimes on low-power hardware; session persistence and UI responsiveness on embedded devices remain unsolved |
| **RFC-driven architectural convergence** | ZeroClaw (10+ revision RFCs), emerging in OpenClaw and NanoClaw | Projects using structured RFC processes are converging faster on durable designs; this is becoming a signal of project maturity |
| **Cost-aware agent operations** | Hermes Agent custom pricing #92613, ZeroClaw cost-tracking bugs #10635/#10645, NanoBot cheaper heartbeat models #4549 | As agents run longer and more frequently, cost visibility and budget enforcement are moving from nice-to-have to required |

---

**Summary:** The ecosystem is in a post-release stabilization phase across all major projects. OpenClaw and CoPaw lead in raw activity but carry the heaviest bug burden. ZeroClaw stands out for architectural discipline (RFC process, session replay design). NanoClaw and NanoBot are the most focused on provider diversity and correctness. The clearest industry signal is that **session durability, async correctness, and multi-agent policy safety** are now the defining challenges — projects that solve these reliably will differentiate from those still debugging release regressions.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-07

## 1. Today's Overview

NanoBot is in a high-velocity sprint day: **16 PRs** touched the repo in the last 24 hours while no new issues were opened and no releases shipped. Activity is concentrated on **test stabilization, CI hardening, documentation refresh, and two bug fixes** (WeCom media upload, TUI context display). The project appears healthy — the open/active issue count remains zero, and the team is shipping quality improvements rather than scrambling for regressions. Five PRs merged/closed today; eleven remain open for review.

## 2. Releases

**No new releases today.** The latest version tag has not advanced.

## 3. Project Progress — Merged / Closed Today

| PR | Area | Summary |
|----|------|---------|
| [#5683](https://github.com/HKUDS/nanobot/pull/5683) | `wecom` | Replaced private WebSocket upload with SDK `WSClient.upload_media` API (`wecom-aibot-sdk-python>=0.1.7,<0.2.0`). 156 tests pass; media delivery contract preserved. |
| [#5677](https://github.com/HKUDS/nanobot/pull/5677) | `test` | Stabilized three flaky/environment-dependent tests, including `test_catalog_bounds_failure_only_keys` (3/5 failures on Windows). |
| [#5680](https://github.com/HKUDS/nanobot/pull/5680) | `CI/CD` | Parallelized Linux + Windows Python suites via `pytest-xdist`; isolated Windows process tests into a separate job; enabled `uv` dependency caching. |
| [#5679](https://github.com/HKUDS/nanobot/pull/5679) | `tui` | Footer now shows per-request context-window occupancy (e.g. `11% context`) instead of aggregate token throughput, reducing misrepresentation during idle. |
| [#5309](https://github.com/HKUDS/nanobot/pull/5309) | `skills` | Fixed marketplace skills shadowing builtins — the loader now correctly marks workspace overrides without disabling the install button on bundled equivalents. |

**Features advanced (still open):**
- [#5607](https://github.com/HKUDS/nanobot/pull/5607) — AnySearch web-search provider (key-optional, anonymous quota)
- [#5684](https://github.com/HKUDS/nanobot/pull/5684) — README refreshed with current WebUI feature gallery
- [#5678](https://github.com/HKUDS/nanobot/pull/5678) — Security test coverage for SSRF guard surfaces
- [#5520](https://github.com/HKUDS/nanobot/pull/5520) — Langfuse tracing for Codex provider

## 4. Community Hot Topics

| Rank | PR/Issue | Comments / Reactions | Topic |
|------|----------|---------------------|-------|
| 1 | [#5580](https://github.com/HKUDS/nanobot/pull/5580) | — | **Session persistence blocking the event loop** — slow file I/O stalls unrelated conversations. |
| 2 | [#5388](https://github.com/HKUDS/nanobot/pull/5388) | — | **MCP schema budget model** — opt-in byte limit to cap model-visible tool schemas. |
| 3 | [#5386](https://github.com/HKUDS/nanobot/pull/5386) | — | **MCP app result metadata preservation** — structured data through tool progress events. |
| 4 | [#4551](https://github.com/HKUDS/nanobot/pull/4551) | — | **Shared heartbeat sessions** — `isolated_session` config to allow context carryover. |
| 5 | [#4549](https://github.com/HKUDS/nanobot/pull/4549) | — | **Cheaper heartbeat model override** — `model_override` config for notification eval. |

**Analysis:** The top concerns cluster around **performance (event-loop blocking)**, **cost optimization (cheaper heartbeat models)**, and **MCP integration maturity**. Users want NanoBot to handle larger tool registries without context bloat and to offload heavy I/O from the async pipeline.

## 5. Bugs & Stability

| Severity | PR | Title | Status |
|----------|-----|-------|--------|
| 🔴 High | [#5682](https://github.com/HKUDS/nanobot/pull/5682) | `ExecTool` resolves relative `working_dir` against process CWD instead of workspace | Open — fix in review |
| 🟡 Medium | [#5679](https://github.com/HKUDS/nanobot/pull/5679) | TUI footer misreported context usage as aggregate throughput | ✅ Merged |
| 🟡 Medium | [#5580](https://github.com/HKUDS/nanobot/pull/5580) | Session storage file-lock contention blocks event loop | Open — fix in review |
| 🟢 Low | [#5309](https://github.com/HKUDS/nanobot/pull/5309) | Marketplace skills incorrectly shadowed builtins | ✅ Merged |
| 🟢 Low | [#5677](https://github.com/HKUDS/nanobot/pull/5677) | Flaky test `test_catalog_bounds_failure_only_keys` (Win) | ✅ Merged |

**No crash reports or regressions opened today.** The two open bug fixes (#5682, #5580) are high-visibility items likely to land soon.

## 6. Feature Requests & Roadmap Signals

| PR | Feature | Predicted In Next Release? |
|----|---------|---------------------------|
| [#5607](https://github.com/HKUDS/nanobot/pull/5607) | AnySearch web-search provider | ✅ Likely — follows Serper pattern, small delta |
| [#5676](https://github.com/HKUDS/nanobot/pull/5676) | Attach-only Desktop target selection | ⚠️ Possible — CLI UX improvement |
| [#5388](https://github.com/HKUDS/nanobot/pull/5388) | Model-visible MCP schema budget | ⚠️ Possible — larger architectural change |
| [#5520](https://github.com/HKUDS/nanobot/pull/5520) | Langfuse tracing for Codex | ⚠️ Possible — external dependency adds surface |
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) | Shared heartbeat sessions | ❓ Unlikely — 60+ day open, low signal |
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) | Cheaper heartbeat model | ❓ Unlikely — same age as #4551 |

**Signal:** The team is prioritizing **provider extensibility** (AnySearch, Langfuse), **CLI ergonomics**, and **MCP hardening** over session-sharing features. Expect a provider-add + docs-release cadence in the next version.

## 7. User Feedback Summary

- **Pain point — context misrepresentation:** The TUI footer showed aggregate throughput that masked actual context occupancy, causing confusion during long sessions. (#5679 — fixed)
- **Pain point — file I/O stalling conversations:** Session persistence on the event loop caused visible hangs when file locks contended. (#5580 — fix open)
- **Pain point — relative paths resolving wrong:** `ExecTool`'s `working_dir` was resolved against the process CWD, breaking workspace-relative expectations. (#5682 — fix open)
- **Satisfaction — WeCom media upload:** The SDK replacement simplified the codebase and passed all 156 tests; users of the WeCom channel should see no behavior change.
- **Satisfaction — Skill shadowing fix:** Marketplace skills now correctly override builtins without disabling install buttons. (#5309 — fixed)

**Overall tone:** Users value **correctness of tool resolution** and **non-blocking session I/O**. The community is responsive to stability improvements but still waiting on the two open bug fixes.

## 8. Backlog Watch

| PR | Age | Priority | Risk |
|----|-----|----------|------|
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) | 73 days | p2 | Heartbeat session sharing — low urgency, blocked on design |
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) | 73 days | p2 | Cheaper heartbeat model — same as above |
| [#5388](https://github.com/HKUDS/nanobot/pull/5388) | 25 days | p2 | MCP schema budget — architectural, needs maintainer review |
| [#5386](https://github.com/HKUDS/nanobot/pull/5386) | 25 days | p2 | MCP result metadata — paired with #5388 |
| [#5580](https://github.com/HKUDS/nanobot/pull/5580) | 10 days | p1 | Event-loop session persistence — **high visibility bug**, should be prioritized |
| [#5682](https://github.com/HKUDS/nanobot/pull/5682) | 1 day | p2 | Relative `working_dir` fix — **likely to merge soon** |

**Action items for maintainers:**
1. **#5580** — High-severity performance bug; request triage label or assignee.
2. **#5388 / #5386** — Paired MCP features; consider reviewing together.
3. **#4551 / #4549** — Long-open heartbeat features; confirm whether still desired or close.

---

**Project Health Score: 🟢 Good** — Active PR flow, zero open issues, two high-priority bug fixes in review, test suite stabilizing. No release pressure detected.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026‑09‑07

## 1. Today’s Overview
Hermes Agent shows **high community engagement** with 50 issues and 50 pull requests updated in the last 24 hours, though no new releases were shipped. Activity is dominated by **bug reports, stability fixes, and platform‑specific regressions** (Desktop, Discord, Anthropic auth, systemd cron). The project is in a strong **triage and patch‑cycle** phase, with several P0/P1 bugs receiving immediate fix PRs. No breaking‑change releases are imminent based on today’s data.

## 2. Releases
*None today.* The latest release remains **v0.21.0** (2026‑08‑31). Several closed PRs today address regressions introduced in that release (systemd cron dispatch, `_db_persisted` marker, Anthropic token‑pool priority).

## 3. Project Progress
**Closed/Merged PRs (today):**
- **#104657** – `fix(agent): strip _db_persisted marker from outbound API messages` — resolves 400 errors from strict OpenAI‑compatible endpoints on session resume.
- **#96236** – `feat(gateway,cli): show reasoning effort on /status` — surfaces effective reasoning level in status output across gateways and CLI.

**Key Open PRs advancing features:**
- **#92613** – `feat(pricing): user‑declared pricing_overrides in config.yaml` — enables custom‑provider cost tracking.
- **#104601** – `feat(bot‑mode): retain Group Chat history on participant gateways` – first step toward host‑offline continuity.
- **#104715** – `feat(cron): support atomic disabled job creation` – operator‑only paused‑job creation path.
- **#104716** – `feat(desktop): create automations from the composer` – GUI‑first automation workflow.

## 4. Community Hot Topics
| Issue / PR | Comments | Theme | Underlying Need |
|------------|----------|-------|-----------------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 169 | Skills‑index freshness probe degraded | Automated health‑monitoring for the Skills Hub is critical; users rely on up‑to‑date skill metadata. |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 25 | Bot Group Chats survive Desktop close | Desire for **always‑on, cross‑device bot collaboration** without local host dependency. |
| [#10421](https://github.com/NousResearch/hermes-agent/issues/10421) | 19 | Turn‑level live time context | Agents lack stable “now” awareness; users want deterministic date/time per turn without explicit tool calls. |
| [#95163](https://github.com/NousResearch/hermes-agent/issues/95163) | 14 | Backend‑hosted group rooms | Need for **gateway‑side authoritative session state** to decouple desktop rendering from bot orchestration. |
| [#26277](https://github.com/NousResearch/hermes-agent/issues/26277) | 9 | Email session isolation by normalized subject | Users want finer‑grained conversation threading per email subject, not just sender. |

**Signal:** The community is pushing hard toward **resilient, backend‑orchestrated multi‑bot/group sessions** and **improved session‑state management** (see #97681, #95163, #104601).

## 5. Bugs & Stability
**P0 / P1 (critical/high severity):**
- [#104688](https://github.com/NousResearch/hermes-agent/issues/104688) – **P0** `fix(prompt): preserve shared context across worktrees` – prompt‑cache drift between worktrees.
- [#90795](https://github.com/NousResearch/hermes-agent/issues/90795) – **P1** Re‑entrant `useSyncExternalStore` → “Maximum update depth exceeded” in Desktop workspace pane (every streaming session).
- [#92837](https://github.com/NousResearch/hermes-agent/issues/92837) – **P1** Heartbeat ticks counted as fired but never delivered; wakes silently lost after agent‑cache idle‑evict.
- [#91654](https://github.com/NousResearch/hermes-agent/issues/91654) – **P1** MCP session registries keyed only by server name → profile collisions in multiplexed gateway.
- [#42719](https://github.com/NousResearch/hermes-agent/issues/42719) – **P1** ACP‑provided MCP tools registered but dropped from model request.
- [#104691](https://github.com/NousResearch/hermes-agent/issues/104691) – **P1** Zombie session lease on torn‑down lane locks session permanently.
- [#104453](https://github.com/NousResearch/hermes-agent/issues/104453) – **P1** Restart‑safe cron dispatch broken on systemd 249 (Ubuntu 22.04).
- [#104711](https://github.com/NousResearch/hermes-agent/issues/104711) – **P2** Streaming crash when `reasoning_content` is a list (Grok/OpenAI relays). **Fix PR:** #104717.
- [#104622](https://github.com/NousResearch/hermes-agent/issues/104622) – **P2** Anthropic token resolver borrows Claude Code login, logging users out on refresh.
- [#104678](https://github.com/NousResearch/hermes-agent/issues/104678) – **P2** Anthropic subscription‑exhaustion latches `failure_reason=billing` with no expiry → cached error replayed.

**P2 / P3 (other notable):**
- [#104712](https://github.com/NousResearch/hermes-agent/issues/104712) – Desktop Tasks list cuts off beyond ~11 entries.
- [#104357](https://github.com/NousResearch/hermes-agent/issues/104357) – Discord cron attachments 404 (Unknown Channel).
- [#94921](https://github.com/NousResearch/hermes-agent/issues/94921) – CLI Shift+letter raw escape sequences on Ghostty (regression).
- [#104696](https://github.com/NousResearch/hermes-agent/issues/104696) – macOS `search_files` loses results due to `EPERM` on rg cleanup.
- [#104693](https://github.com/NousResearch/hermes-agent/issues/104693) – Honcho automatic recall injects previous user‑message context.
- [#104652](https://github.com/NousResearch/hermes-agent/issues/104652) – Reply‑context anchor carries no age/timestamp.
- [#104694](https://github.com/NousResearch/hermes-agent/issues/104694) – Degenerate auto‑title (single punctuation) corrupts Discord thread names.
- [#102301](https://github.com/NousResearch/hermes-agent/issues/102301) – Desktop Kanban board doesn’t render dispatcher‑spawned cards.
- [#101185](https://github.com/NousResearch/hermes-agent/issues/101185) – Discord voice‑channel auto‑TTS never plays.
- [#104689](https://github.com/NousResearch/hermes-agent/issues/104689) – Windows updater reports success after antivirus interruption.

**Stability assessment:** The project is experiencing a **regression burst** following v0.21.0 (systemd cron, Anthropic auth, Desktop rendering). Several P1/P2 bugs have active fix PRs, indicating responsive maintenance.

## 6. Feature Requests & Roadmap Signals
**High‑interest user requests:**
- **#97681** – Bot Group Chats survive Desktop close (cross‑device, gateway‑hosted).
- **#95163** – Opt‑in backend‑hosted group rooms with gateway‑side round driver.
- **#10421** – Turn‑level live time context.
- **#26277** – Email session isolation by normalized subject.
- **#44993** – Trusted profile lane for `execute_code` autonomy.
- **#85648** – Delegation timing: let ready dependency affect unfinished parent work.

**Roadmap prediction:** The next release will likely include:
- **Group‑chat host‑offline continuity** (#104601 PR in progress).
- **Custom pricing overrides** (#92613 PR).
- **Atomic disabled cron creation** (#104715 PR).
- **Desktop automation composer** (#104716 PR).
- **Reasoning effort shown on `/status`** (#96236 merged).

The strong demand for **backend‑orchestrated group sessions** and **config‑driven custom pricing** suggests these will be prioritized in the upcoming 0.22 cycle.

## 7. User Feedback Summary
**Pain points:**
- **Session‑state fragility** – heartbeat ticks lost, zombie leases, Kanban cards invisible, tasks list truncated.
- **Provider‑specific regressions** – Anthropic auth pool collision, Discord voice/TTS broken, systemd cron dispatch failed.
- **Desktop rendering bugs** – workspace pane infinite loop, tasks/kanban truncation, Windows updater silent failures.
- **Tool‑registry bugs** – MCP tools dropped, Honcho recall injects stale context, macOS `search_files` permissions error.
- **Quality‑of‑life gaps** – no turn‑level time context, no reply‑age in anchors, degenerate auto‑titles corrupt channel names.

**Satisfaction signals:** Users actively engage with high‑comment issues (e.g., #66616, #97681) and submit detailed repro steps. The quick turn‑around on P0/P1 fixes (e.g., #104717 for #104711) indicates a responsive maintainer team.

## 8. Backlog Watch
**Long‑standing issues needing maintainer attention:**
- [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) – Skills‑index watchdog degraded (169 comments, open since 2026‑07‑18). Automated freshness probe failure impacts all Skills Hub users.
- [#42719](https://github.com/NousResearch/hermes-agent/issues/42719) – ACP‑provided MCP tools dropped from model request (P1, open since 2026‑06‑09). Blocks ACP‑MCP integration.
- [#44993](https://github.com/NousResearch/hermes-agent/issues/44993) – Trusted profile lane for `execute_code` (open since 2026‑06‑12). Friction for trusted operator profiles.
- [#85648](https://github.com/NousResearch/hermes-agent/issues/85648) – Delegation timing contract (open since 2026‑08‑13). Blocks efficient parallel delegation.
- [#26277](https://github.com/NousResearch/hermes-agent/issues/26277) – Email session isolation by normalized subject (open since 2026‑05‑15). Users want finer‑grained email threading.

**Action recommendation:** Prioritize #66616 and #42719 as they affect core functionality (skill freshness, ACP/MCP tool delivery) and have accumulated significant community attention.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-07

---

## 1. Today's Overview

PicoClaw (sipeed/picoclaw) shows moderate but focused activity today with 4 issues and 2 PRs updated in the last 24 hours. The project is actively engaging with embedded-device users, as two of the top open issues directly address performance problems on low-power hardware (RV1106, RISC-V boards). No new releases were published today, indicating the team may be in a stabilization cycle. The merge of PR #1349 (QQ Channel attachment support) is a notable closure, while a new feature request for OpenCode Go session header support signals expanding integration requirements. Overall, project health is steady with clear user-driven signals on pain points around persistence and performance.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

**Merged/Closed PRs:**

- **#1349** — *feat(qq): support parsing and replying to more attachment types* (Author: aishannon) — Closed/Merged. Added support for QQ Channel emoji parsing, incoming voice/image/video/file message handling, and replies with local attachments. Prioritizes Markdown messages with fallback. This significantly expands QQ Channel integration capabilities.
  - https://github.com/sipeed/picoclaw/pull/1349

**Open PRs:**

- **#3348** — *i18n: complete Czech code wrap labels* (Author: KrtCZ) — Open/Stale. Awaiting maintainer review.
  - https://github.com/sipeed/picoclaw/pull/3348

---

## 4. Community Hot Topics

| Issue/PR | Activity | Author | Summary |
|----------|----------|--------|---------|
| [#3351](https://github.com/sipeed/picoclaw/issues/3351) | 1 comment, stale | chentianxiong123 | Session history physically deleted on compression — no true persistence |
| [#3350](https://github.com/sipeed/picoclaw/issues/3350) | 1 comment, stale | chentianxiong123 | Web UI input lag on embedded/low-performance devices |
| [#3369](https://github.com/sipeed/picoclaw/issues/3369) | New, 0 comments | w33ble | Add OpenCode Go session header (`x-opencode-session`) support |
| [#675](https://github.com/sipeed/picoclaw/issues/675) | 7 comments, closed | sheying2013 | Add more LLM Provider Support (closed 2026-09-06) |

**Analysis:** The top two issues (#3350, #3351) come from the same contributor and point to a deeper concern: **PicoClaw's suitability for resource-constrained embedded deployments**. The session persistence bug (#3351) is particularly critical — users expect append-only logging but the `SetHistory` → `rewriteJSONL` path physically overwrites files, destroying history on compression. The OpenCode Go session header request (#3369) reflects an emerging need to support the OpenCode ecosystem's multi-session architecture, which PicoClaw's current OpenAI-compatible provider doesn't yet map correctly.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| 🔴 High | [#3351](https://github.com/sipeed/picoclaw/issues/3351) | Session compression **physically deletes** original `.jsonl` records; history is permanently lost after "memory reset" | None yet |
| 🟡 Medium | [#3350](https://github.com/sipeed/picoclaw/issues/3350) | Web UI input box **severe typing lag** on embedded/Low-performance devices (RV1106, RISC-V); CPU spikes per character | None yet |

**Notes:** Issue #3351 is a data-loss bug with a clear root cause identified in the source (`pkg/memory/jsonl.go`: `SetHistory` calls `rewriteJSONL` which overwrites the entire file rather than appending). Issue #3350 is a performance regression that scales with conversation length, suggesting the frontend may be re-processing or re-rendering the full history on each keystroke. Neither has an associated fix PR yet.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood |
|---------|--------|------------|
| **True append-only session persistence** (no destructive compression) | #3351 | **High** — directly ties to core data integrity; likely candidate for next patch release |
| **OpenCode Go `x-opencode-session` header support** | #3369 | **Medium** — niche but growing demand from OpenCode ecosystem users |
| **Additional LLM provider support** | #675 (closed) | **Medium** — community interest persists; closing may indicate triage or deferred decision |
| **Czech i18n completion** | #3348 (PR open) | **Low** — cosmetic, but easy merge |
| **QQ Channel extended attachment handling** | #1349 (merged) | ✅ **Delivered** |

**Prediction:** The next release is likely to prioritize the session persistence fix (#3351) as it constitutes a data-loss bug. OpenCode Go session support (#3369) may follow if the OpenCode ecosystem integration is on the roadmap.

---

## 7. User Feedback Summary

**Pain Points:**
- **Data permanence anxiety** — Users are shocked that "compressed" sessions destroy their original chat history. The term "失忆后历史无法找回" (history unrecoverable after amnesia) reflects genuine frustration. Users expect AI agents to *remember*, not delete.
- **Embedded device UX** — The Web UI typing lag on low-end hardware is a dealbreaker for PicoClaw's target audience (edge/embedded AI). The fact that input lag scales with conversation length suggests a frontend architecture issue rather than a simple optimization gap.
- **Ecosystem integration gaps** — OpenCode Go users feel the lack of `x-opencode-session` header support as a blocker for multi-session workflows.

**Satisfaction Signals:**
- QQ Channel attachment support (#1349) was well-received and merged, indicating the project is responsive to community contributions in the messaging-channel domain.
- The LLM provider expansion request (#675) being closed after 7 comments suggests the maintainers are actively triaging, even if the outcome wasn't what the requester hoped.

---

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| [#3351](https://github.com/sipeed/picoclaw/issues/3351) — Session history physical deletion | ~8 days, stale | **Critical** — Data loss bug; stale label may cause it to be auto-closed |
| [#3350](https://github.com/sipeed/picoclaw/issues/3350) — Web UI input lag on embedded devices | ~8 days, stale | **High** — Core UX for target hardware; stale label risk |
| [#3369](https://github.com/sipeed/picoclaw/issues/3369) — OpenCode Go session header | 1 day, new | **Medium** — New, needs triage |
| [#3348](https://github.com/sipeed/picoclaw/pull/3348) — Czech i18n completion | ~9 days, stale | **Low** — Trivial merge, stale risk |

**Recommendation:** Maintainers should urgently remove stale labels from #3351 and #3350 to prevent accidental closure of unresolved issues. Both represent significant user-facing problems that, if auto-closed without fixes, will erode community trust.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-07

## 1. Today's Overview

NanoClaw saw moderate activity today with 2 issues and 16 PRs updated in the last 24 hours. The most notable development is the closure of a Slack DM threading bug (issue #3730) alongside its corresponding fix PR (#3731), authored by the original reporter. A significant portion of today's PR churn stems from the ongoing provider-contract refactor initiative led by `zvi-fried`, which continues to clean up and formalize how agent providers (Claude, Codex, OpenCode, Cursor) integrate with the core runtime. No new releases were published, indicating the project is still in a maintenance-and-refactor phase rather than a release-candidate cycle. Overall project health appears stable: bug-fix velocity is reasonable, the refactoring work is systematic, and there are no signs of regressions beyond the known Telegram polling issue.

## 2. Releases

**None.** The latest published release remains v2.3.0 (2026-08-24). The repository is currently 119 commits ahead of that tag.

## 3. Project Progress

**Merged / Closed PRs today:**

- **#3731** — `fix(slack): keep DM thread_ts for reply delivery` (closes #3730) — The reporter `bjsheppa` self-authored and merged a fix for the Slack shared-session-mode bug, preserving `thread_ts` for proper DM thread routing.
- **#3727** — `refactor(providers): render provider instructions from core-owned canon` — Consolidates agent instruction prose into core-owned templates; providers now declare typed facts instead of free-form documents.
- **#3591** — Duplicate of the above refactor, also closed.
- **#3586** — `refactor(providers): declare the setup provider contract and install verifier` — Establishes a validated contract for how providers declare their setup requirements.
- **#3592** — `feat(groups): add a core-owned speed inference property` — Adds `speed` as a per-agent-group property alongside `model` and `effort`, with CLI support (`ncl groups config update --speed <tier>`).
- **#3585** — `refactor(providers): declare the host provider contract` — Routes host provider spawn and group-init through a registration-validated contract.
- **#3581** — `refactor(providers): declare the runtime provider contract` — Turns the container runtime provider seam into an executable, core-enforced contract.

**Key trend:** The provider-contract refactor is reaching completion — the core now declares and enforces provider interfaces, and individual providers (Codex, OpenCode) are being bound to these contracts.

## 4. Community Hot Topics

- **[#3730] Slack shared-session-mode DM threading bug** — https://github.com/nanocoai/nanoclaw/issues/3730
  - Highly relevant to users running Slack with `session_mode: "shared"`. The reporter verified the bug against `main` and then authored the fix PR themselves (#3731), demonstrating strong community contribution.
- **[#3728] Telegram polling loop dies silently** — https://github.com/nanocoai/nanoclaw/issues/3728
  - A serious reliability concern: inbound Telegram messages can fail silently for days with no logging. Affects both v2.1.54 and v2.3.0. No fix PR yet.
- **[#3729] Connect host to community cell / manage perks in browser** — https://github.com/nanocoai/nanoclaw/pull/3729
  - Expands the browser portal setup flow to include Echo and Slack with WorkOS sign-in. Reflects ongoing investment in onboarding UX.
- **[#3726] Native Proton Mail adapter** — https://github.com/nanocoai/nanoclaw/pull/3726
  - New channel proposal for Proton Mail via the Bridge. Addresses a gap for privacy-focused users who lack IMAP/SMTP access.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **High** | [#3728](https://github.com/nanocoai/nanoclaw/issues/3728) | Telegram inbound polling loop retries indefinitely with no exit condition and no success logging; can die silently for days while outbound continues to work. | ❌ None yet |
| **Medium** | [#3730](https://github.com/nanocoai/nanoclaw/issues/3730) | Slack with `session_mode: "shared"` still spawned a new per-thread session per top-level DM, breaking expected shared-session behavior. | ✅ #3731 (merged) |

**Assessment:** The Slack bug is resolved. The Telegram silent-failure issue remains open and is the most critical stability concern — it affects a widely-used channel and can go undetected for extended periods.

## 6. Feature Requests & Roadmap Signals

- **Proton Mail channel** (#3726) — New adapter for Proton Mail via Bridge. Signals demand from privacy-oriented users for email-based agent access without IMAP/SMTP.
- **Cursor Agent SDK provider** (#3356) — Adds a Cursor-specific provider payload built on the new contract system.
- **`/add-cursor` install skill** (#3355) — Companion skill for easy Cursor provider installation.
- **Speed inference property** (#3592) — Now merged; adds a `speed` tier to agent-group configuration alongside `model` and `effort`.
- **Community cell / browser perks management** (#3729) — Extends the browser portal with WorkOS-based setup for Echo and Slack.

**Prediction:** The next release (likely v2.4.0) will probably include the Proton Mail adapter, the Cursor provider skill, and the speed property as new features, alongside the provider-contract refactor as a behind-the-scenes improvement.

## 7. User Feedback Summary

- **Slack shared sessions** — Users expected `session_mode: "shared"` to reuse sessions within DM threads; the bug caused session sprawl. The self-fixed nature of #3730 suggests the affected user is technically proficient and deeply invested in the project.
- **Telegram reliability** — The silent failure in #3728 is a significant pain point: hosts appeared healthy (active status, outbound working) while inbound was completely broken for days. Users need observability into adapter health.
- **Provider diversity** — Multiple PRs for Codex, OpenCode, and Cursor indicate user demand for non-Claude agent providers, and the contract refactor is a direct response to that need.
- **Onboarding UX** — The browser-portal feature (#3729) shows the team is actively improving first-time setup experience, particularly around channel configuration.

## 8. Backlog Watch

- **[#3728](https://github.com/nanocoai/nanoclaw/issues/3728)** — *Telegram silent death*: Open since 2026-09-06 with no comments or fix PR. High severity; should be prioritized.
- **[#3654](https://github.com/nanocoai/nanoclaw/pull/3654)** — *NO_PROXY for host.docker.internal*: Open since 2026-08-29. Fixes host-side MCP server reachability from containers. No maintainer response in ~9 days.
- **[#3464](https://github.com/nanocoai/nanoclaw/pull/3464)** — *Remove v1-only session-commands.ts*: Open since 2026-08-23. Cleans up orphaned v1 code that breaks on merge. Stale for ~15 days.
- **[#3356](https://github.com/nanocoai/nanoclaw/pull/3356)** — *Cursor Agent SDK payload*: Open since 2026-08-19. Feature-complete but unmerged; likely awaiting contract refactor stabilization.
- **[#3355](https://github.com/nanocoai/nanoclaw/pull/3355)** — *`/add-cursor` install skill*: Open since 2026-08-19. Companion to #3356.
- **[#3722](https://github.com/nanocoai/nanoclaw/pull/3722)** — *Adopt OpenCode contract in install skill*: Open since 2026-09-04. Follow-up to the provider refactor.
- **[#3588](https://github.com/nanocoai/nanoclaw/pull/3588)** — *OpenCode provider contract implementation*: Open since 2026-08-27. Binds OpenCode to the new contract system.

**Maintainer attention needed:** Issue #3728 (Telegram) should be triaged urgently. The backlog of provider-contract PRs (#3588, #3356, #3355, #3722) appears to be intentionally held pending refactor completion rather than neglect.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-09-07

## 1. Today's Overview

NullClaw shows **low daily activity** on 2026-09-07, with no issues opened or closed and no merged pull requests. The sole activity is one open PR (#996) addressing stdio MCP response timeout handling, which also relates to a previously filed issue (#991). The project remains stable with a healthy test baseline (7,373 passed, 9 skipped), but the absence of merged PRs and new releases over the tracking window suggests a period of reduced maintainer momentum.

## 2. Releases

No new releases were published today.

## 3. Project Progress

- **PR #996** ([nullclaw/nullclaw#996](https://github.com/nullclaw/nullclaw/pull/996)) is the only pull request updated in the last 24 hours. It remains **open** and has not yet been merged.
  - **Scope:** Fixes timeout handling for stdio-based MCP responses (`timeout_ms`), process-group cleanup on timeout, and child-process cleanup on failed initialization.
  - **Linked issue:** Addresses #991.
  - **Validation:** Passed full test suite (`zig build test --summary all`: 7,373 passed, 9 skipped) and ReleaseSmall build verification.
- No PRs were merged today, indicating no features or fixes landed in this cycle.

## 4. Community Hot Topics

The most discussed item today is:

- **PR #996 — fix(mcp): bound stdio response waits** ([#996](https://github.com/nullclaw/nullclaw/pull/996))
  - Author: `be-student` | Created: 2026-09-06 | 0 reactions
  - **Underlying need:** Users require reliable stdio MCP server interactions with predictable timeout behavior. Unbounded waits can cause indefinite hangs, resource leaks, and poor developer experience—especially in agent workflows where MCP tools are called programmatically. This PR signals active community interest in robustness and error-cleanup guarantees for the stdio transport layer.

No issues attracted significant comment activity today.

## 5. Bugs & Stability

- **No new bug reports** were filed today.
- **PR #996** addresses what appears to be a **bug in stdio MCP timeout handling** (referencing issue #991). The fix covers three related failure modes:
  1. Unbounded stdio response waits — now respects `timeout_ms`.
  2. Orphaned child processes on timeout — process group termination added.
  3. Failed initialization leaving spawned children — cleanup path added.
- **Severity assessment:** Medium. While not a crash, unbounded waits and resource leaks in an MCP server can degrade agent reliability in production. The fix is scoped and test-verified; awaiting merge.
- No regressions were reported today.

## 6. Feature Requests & Roadmap Signals

- No new feature requests were opened today.
- **Signal from PR #996:** The community is pushing for stronger **timeout and lifecycle management** in MCP stdio transports. This may indicate a broader roadmap need for configurable timeout policies and cleaner process lifecycle hooks in future releases.
- No explicit roadmap items or milestone discussions were visible in today's activity.

## 7. User Feedback Summary

- **Pain points reflected in PR #996:** Users experienced hanging stdio MCP calls and orphaned processes when timeouts were not enforced or cleanup was incomplete. These are real operational issues for agents relying on NullClaw as an MCP server.
- **Satisfaction indicators:** The full test suite passing and the ReleaseSmall build check suggests the project maintains good internal quality, which is a positive signal for users concerned about stability.
- No explicit user complaints or praise were captured in today's issue/PR activity.

## 8. Backlog Watch

- **Issue #991** (referenced by PR #996) — likely the originating bug report for the stdio timeout issue. It remains a focal point; once PR #996 merges, this should be closed.
- No other long-unanswered issues or PRs were flagged in today's data. However, the **zero closed issues and zero merged PRs** pattern over the 24-hour window may warrant monitoring if it persists, as it could indicate a backlog of pending review or a temporary maintainer pause.

---

**Overall Health Assessment:** NullClaw is in a **stable but quiet** state. The codebase tests pass robustly, and one meaningful bug-fix PR is in review. The low activity volume makes it difficult to draw strong conclusions about community engagement, but the single PR addresses a genuine reliability concern. Recommend tracking whether PR #996 merges in the coming days and whether issue #991 resolves as a result.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-07

---

## 1. Today's Overview

IronClaw shows moderate-to-active development momentum with **13 PRs updated** in the last 24 hours, though **no issues were filed or updated** and **no new releases** were published. The contributor base is narrow: four authors are responsible for all today's activity, with **italic-jinxin** driving a coordinated set of five web UI polish PRs. The project is in a steady-state refinement cycle—no major feature launches, but consistent fixes around UI stability, dependency hygiene, and MCP diagnostics. Overall health is **stable**; the low issue churn suggests few blockers, while the PR volume indicates active maintenance.

---

## 2. Releases

**No new releases published today.**

---

## 3. Project Progress

### Merged / Closed PRs (3)

| PR | Author | Description |
|----|--------|-------------|
| [#8049](https://github.com/nearai/ironclaw/pull/8049) | dependabot[bot] | Closed large Rust dependency bump (19 updates) — `uuid`, `base64`, `toml`, and others |
| [#7835](https://github.com/nearai/ironclaw/pull/7835) | dependabot[bot] | Closed GitHub Actions group bump (5 updates) — `claude-code-action`, `setup-node`, etc. |
| [#7020](https://github.com/nearai/ironclaw/pull/7020) | dependabot[bot] | Closed `tokio-tungstenite` 0.29→0.30 bump in the tokio-ecosystem group |

### Open PRs Advancing (10)

- **Web UI Polish** — PRs #8071, #8070, #8069, #8068 collectively harden the command-result card layout, slash-command menu alignment, dismissal UX, and keyboard navigation. These are quality-of-life fixes for the transcript interface.
- **Shared Channel Diagnostics** — [#8076](https://github.com/nearai/ironclaw/pull/8076) by `be-student` distinguishes disconnected shared channels from unpaired accounts, improving Slack adapter clarity.
- **MCP Response Leak Diagnostics** — [#8077](https://github.com/nearai/ironclaw/pull/8077) by `linhongyu510` centralizes a `response_leak_blocked` sentinel and teaches the MCP lane to classify it, addressing a prior diagnostic gap (closes #8009).
- **Dependency Updates (open)** — Three Dependabot PRs remain open: #8080 (21 Rust deps), #8078 (tokio-ecosystem), #8079 (GitHub Actions), and #7834 (WASM group, open since Aug 23).

---

## 4. Community Hot Topics

No issues were opened or updated today, so **there are no community hot topics to track**. All activity is PR-driven, suggesting the maintainer team is self-directing fixes rather than responding to community-reported problems.

**Notable open PRs by age (potential backlog signal):**
- [#7834](https://github.com/nearai/ironclaw/pull/7834) — open since **Aug 23** (WASM group deps), 15 days unanswered
- [#7020](https://github.com/nearai/ironclaw/pull/7020) — closed today but open since **Aug 2** (tokio-tungstenite), 36 days

---

## 5. Bugs & Stability

| Issue | Severity | PR | Status |
|-------|----------|----|--------|
| Command-result cards collapsing in flex column | Low (UI regression) | [#8071](https://github.com/nearai/ironclaw/pull/8071) | Open |
| Slash-command menu misalignment on desktop | Low (UI) | [#8070](https://github.com/nearai/ironclaw/pull/8070) | Open |
| No dismiss action on ephemeral command results | Low (UX) | [#8069](https://github.com/nearai/ironclaw/pull/8069) | Open |
| Active slash-command option scrolls out of view | Low (UX/navigability) | [#8068](https://github.com/nearai/ironclaw/pull/8068) | Open |
| MCP response leak diagnostics unclassified | Low (observability) | [#8077](https://github.com/nearai/ironclaw/pull/8077) | Open (closes #8009) |
| Disconnected shared channel indistinguishable from unpaired | Low (diagnostic clarity) | [#8076](https://github.com/nearai/ironclaw/pull/8076) | Open |

**Assessment:** No critical or medium-severity bugs reported today. All tracked issues are low-risk UI/observability improvements. No crashes or regressions flagged.

---

## 6. Feature Requests & Roadmap Signals

No user-requested features surfaced via issues today. However, two open PRs signal near-term roadmap direction:

- **[#8076](https://github.com/nearai/ironclaw/pull/8076)** — Improved shared-channel diagnostics for Slack suggests the team is investing in **adapter-level observability** and channel lifecycle handling. Likely to appear in an upcoming release as part of Slack integration hardening.
- **[#8077](https://github.com/nearai/ironclaw/pull/8077)** — MCP response leak classification points to a growing focus on **MCP (Model Context Protocol) safety and diagnostics**, which may indicate a roadmap emphasis on MCP integration maturity.

The five web UI PRs from `italic-jinxin` suggest a coordinated **transcript/UX polish sprint** is underway, likely targeting a near-term patch release.

---

## 7. User Feedback Summary

**No user-reported issues today.** All activity is maintainer/dependabot-driven. The absence of issue chatter combined with a focused set of UI fixes implies the project has a small, active core team and limited public issue volume. Users experiencing command-result card behavior or slash-command navigation issues are likely being addressed proactively rather than through bug reports.

---

## 8. Backlog Watch

| PR | Open Since | Days Open | Risk | Note |
|----|-----------|-----------|------|------|
| [#7834](https://github.com/nearai/ironclaw/pull/7834) | 2026-08-23 | 15 | Medium | WASM group dependency bump (4 updates) — stalled, may need rebase |
| [#8078](https://github.com/nearai/ironclaw/pull/8078) | 2026-09-06 | 1 | Low | Tokio-ecosystem bump — fresh, expected to merge soon |
| [#8080](https://github.com/nearai/ironclaw/pull/8080) | 2026-09-06 | 1 | Low | 21 Rust dependency updates — fresh, expected to merge soon |
| [#8079](https://github.com/nearai/ironclaw/pull/8079) | 2026-09-06 | 1 | Low | GitHub Actions group bump — fresh, expected to merge soon |

**Key concern:** PR [#7834](https://github.com/nearai/ironclaw/pull/7834) has been open for 15 days without maintainer response. The WASM dependency group (`wasmtime`, `wasmtime-wasi`, `wit-component`, `wit-parser`) may need attention, particularly if newer `wasmtime` versions introduce breaking changes.

---

**Overall Health Rating: 🟢 Stable** — Active PR flow, no critical issues, low community issue volume, small contributor pool. Dependency hygiene is strong via Dependabot. Web UI polish is the dominant thread.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI Project Digest — 2026-09-07

---

## 1. Today's Overview

LobsterAI activity on 2026-09-07 remains **low-key but productive**. One PR was merged today, fixing Windows test portability issues introduced by the OpenClaw v2026.8.1 upgrade branch integration. One issue remains open and stale — a UI refresh bug tied to agent deletion and task list auto-loading. No new releases were published, and overall commit velocity appears modest. The project is in a quiet stabilization phase, with the maintainer team focused on merge hygiene rather than new feature delivery.

---

## 2. Releases

**No new releases** were published today. The latest identifiable upgrade branch is **OpenClaw v2026.8.1**, which recently merged into `main` and triggered downstream test fixes (see PR #2619).

---

## 3. Project Progress

### Merged Today

| PR | Description | Link |
|----|-------------|------|
| [#2619](https://github.com/netease-youdao/LobsterAI/pull/2619) | Fix Windows path portability in installer and thumbnail tests after OpenClaw v2026.8.1 merge | [PR #2619](https://github.com/netease-youdao/LobsterAI/pull/2619) |

**What was advanced:** The OpenClaw v2026.8.1 integration branch is being stabilized on Windows. PR #2619 corrected four failing test cases — three macOS installer path tests and one thumbnail queue priority test — ensuring cross-platform parity without touching production code or the OpenClaw runtime. This is a **test-only, zero-risk fix** that clears the CI deck for the upgrade branch.

---

## 4. Community Hot Topics

| Item | Type | Engagement | Link |
|------|------|------------|------|
| Agent deletion → task list not auto-refreshing | Issue | 1 comment, 0 👍 | [#1068](https://github.com/netease-youdao/LobsterAI/issues/1068) |
| Windows path portability test fix | PR | 0 comments, 0 👍 | [#2619](https://github.com/netease-youdao/LobsterAI/pull/2619) |

**Underlying need analysis:** Issue #1068 reflects a **UX workflow pain point** — users who manage multiple agents expect seamless context switching and list reactivity. When the last non-default agent is deleted and the UI fails to reload the default agent's task list, it breaks trust in the application's responsiveness. This is a common pattern in multi-tenant agent management tools and suggests the frontend state management layer (likely React/Redux or similar) may not be properly subscribing to agent-switch events.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| 🟡 Medium | [#1068](https://github.com/netease-youdao/LobsterAI/issues/1068) | After deleting the current agent and switching to another, the task list does not auto-refresh | No fix PR open; marked **stale** |

**No regressions or crash reports** were filed today. The only open bug is the stale UI refresh issue from March 2026, which has accumulated no maintainer responses in six months.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood |
|---------|--------|------------|
| Auto-refresh task list on agent switch/delete | [#1068](https://github.com/netease-youdao/LobsterAI/issues/1068) | **High** — small fix, high UX impact |
| Cross-platform test parity (Windows/macOS) | [#2619](https://github.com/netease-youdao/LobsterAI/pull/2619) | **In progress** — being addressed as part of OpenClaw upgrade |

**Prediction:** The task list refresh fix (Issue #1068) is a strong candidate for the next patch release. It is a contained, low-risk UI correction that directly addresses a user-reported workflow break. The OpenClaw upgrade branch is likely to land as a minor version bump.

---

## 7. User Feedback Summary

| Signal | Detail |
|--------|--------|
| **Pain point** | Deleting an agent and switching back to `main` does not auto-refresh the task list — users must manually reload |
| **Use case** | Multi-agent management workflows where agents are created, used, and deleted iteratively |
| **Satisfaction** | Neutral-to-frustrated; the bug is a persistent, unaddressed annoyance (open since March, no comments from maintainers) |
| **Test fixes** | Community contributor (`btc69m979y-dotcom`) actively engaged in test stabilization, indicating a healthy contributor base around platform parity |

---

## 8. Backlog Watch

| Item | Open Since | Status | Risk |
|------|------------|--------|------|
| [#1068](https://github.com/netease-youdao/LobsterAI/issues/1068) — Agent deletion task list refresh | 2026-03-30 | **Stale**, 0 👍, 1 comment | 🔴 **High** — 5+ months unresolved, directly impacts core UX; likely to accumulate more frustration if left unaddressed |

**Recommendation:** Issue #1068 should be prioritized. It is a straightforward state-management fix that would materially improve user experience and signal community attentiveness. The stale tag suggests it has fallen through the review pipeline and may need a maintainer ping or community PR to regain traction.

---

*Digest generated from GitHub data via LobsterAI. All links point to the [netease-youdao/LobsterAI](https://github.com/netease-youdao/LobsterAI) repository.*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-09-07

## 1. Today's Overview

Moltis ([moltis-org/moltis](https://github.com/moltis-org/moltis)) showed low activity on 2026-09-07, with no new issues opened or closed and no releases published. Two open pull requests remain under review, both authored by `be-student`, continuing work from the previous day. No merged or closed PRs were recorded in the last 24 hours. The project appears to be in a quiet maintenance phase with incremental fixes in progress rather than major feature development.

## 2. Releases

No new releases were published today. The release pipeline is currently dormant, suggesting the team may be accumulating fixes before the next version bump.

## 3. Project Progress

No PRs were merged or closed today. The two outstanding pull requests represent incremental bug fixes:

- **[PR #1261](https://github.com/moltis-org/moltis/pull/1261)** — Restricts ALPN negotiation to HTTP/1.1 over TLS, addressing [issue #245](https://github.com/moltis-org/moltis/issues/245). This fixes a protocol-level correctness issue pending full WebSocket-over-TLS (RFC 8441) support.
- **[PR #1260](https://github.com/moltis-org/moltis/pull/1260)** — Improves error reporting for missing shell executions by classifying `spawn` `NotFound` errors against the configured working directory, closing [issue #279](https://github.com/moltis-org/moltis/issues/279).

Both PRs are open and awaiting review; no features or fixes landed today.

## 4. Community Hot Topics

No issues were opened or gained significant comment activity today. The two most-discussed items remain the PRs referenced above:

| Item | Type | Author | Engagement |
|------|------|--------|------------|
| [PR #1261](https://github.com/moltis-org/moltis/pull/1261) | TLS/ALPN fix | be-student | 0 reactions |
| [PR #1260](https://github.com/moltis-org/moltis/pull/1260) | Exec/shell fix | be-student | 0 reactions |

**Analysis:** The absence of community commentary on either PR suggests a small, focused contributor base. The TLS ALPN restriction and shell error classification both address genuine developer pain points — incorrect protocol negotiation and misleading error messages — indicating the project is maturing in its error-handling and protocol-compliance layers.

## 5. Bugs & Stability

Two bugfix PRs are in progress today, but neither has been merged:

| Severity | Bug | PR | Status |
|----------|-----|-----|--------|
| **Medium** | TLS ALPN advertises protocols (e.g., h2) not yet supported, violating RFC 8441 readiness — [Issue #245](https://github.com/moltis-org/moltis/issues/245) | [PR #1261](https://github.com/moltis-org/moltis/pull/1261) | Open, unmerged |
| **Low** | Missing `sh` in `PATH` is silently masked when the working directory exists, producing confusing `NotFound` errors — [Issue #279](https://github.com/moltis-org/moltis/issues/279) | [PR #1260](https://github.com/moltis-org/moltis/pull/1260) | Open, unmerged |

No crash reports or regression filings were recorded today. Stability appears steady.

## 6. Feature Requests & Roadmap Signals

No new feature requests were opened today. However, the two active PRs signal near-term roadmap priorities:

1. **RFC 8441 / WebSocket-over-TLS support** — PR #1261 explicitly documents this as a pending capability. Once ALPN restrictions are lifted after WebSocket upgrades are implemented, this will likely be a visible release highlight.
2. **Shell error diagnostics** — PR #1260's refinement of spawn error classification suggests a broader push toward more accurate process-execution feedback, which may inform future debugging-tooling features.

No major new feature requests were observed that would indicate a shift in roadmap direction.

## 7. User Feedback Summary

No new user feedback was recorded today. The two open PRs address previously reported pain points:

- **TLS misconfiguration frustration** ([#245](https://github.com/moltis-org/moltis/issues/245)): Users encountering unexpected protocol behavior over TLS — the ALPN fix directly addresses this.
- **Opaque shell-execution errors** ([#279](https://github.com/moltis-org/moltis/issues/279)): Developers struggling to diagnose why a command failed when the working directory was valid but the shell binary was absent — the fix improves error classification.

Both reflect mature, responsive bug-fixing rather than new feature demand.

## 8. Backlog Watch

No issues or PRs appeared today that would signal backlog accumulation. The two open PRs ([#1261](https://github.com/moltis-org/moltis/pull/1261), [#1260](https://github.com/moltis-org/moltis/pull/1260)) are recent (created 2026-09-06) and actively maintained, so they do not yet constitute a backlog concern. No long-unanswered items were identified from the available data.

---

**Project Health: 🟡 Stable but quiet.** Low daily activity with no regressions, no new features, and two incremental fixes pending merge. The project is in a maintenance rhythm rather than a growth sprint.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-09-07

## 1. Today's Overview

CoPaw (agentscope-ai/CoPaw) remains highly active with **31 issues** and **26 PRs** updated in the past 24 hours, though no new releases were published today. The project shows a healthy open-source cadence: 20 open/active issues and 11 closed, while 20 PRs remain open and 6 were merged or closed. The dominant theme this cycle is **chat/task concurrency bugs** (notably the 409 error on follow-up messages during active runs) and **Telegram/Feishu channel rendering fixes**, alongside foundational work on memory lifecycle unification. First-time contributor PRs are prominent, signaling growing community engagement.

## 2. Releases

No new releases published in the last 24 hours. The latest confirmed versions in circulation remain **QwenPaw v2.2** (web/desktop) and **v2.1.x** for legacy desktop builds.

## 3. Project Progress

### Merged / Closed Today
- **#7595** — Fixed language selector inconsistency between top dropdown (7 langs) and sidebar settings (5 langs); Bahasa Indonesia and Vietnamese are now included.
- **#7584 / #6820 / #7548 / #7505 / #7447 / #7099 / #7567** — Multiple bugs closed, including memory-loss regressions, dark-mode CSS miscompilation, and task-stopping failures.

### Actively Advancing (Open PRs)
- **#7561** — *Refactor: unify automatic memory lifecycle* — consolidates memory capture, recall, and background execution under a single ownership model (breaking change).
- **#7578** — *Fix: log exceptions in coordinator `_drain()`* — addresses silently swallowed exception traces in tool dispatch (fixes #7572).
- **#7577** — *Fix: enqueue follow-up messages during active chat task* — resolves the 409 rejection for messages sent mid-execution (fixes #7559).
- **#7593** — *Restore direct path input for working directory* — re-adds the v2.1 inline path-input UX removed in the multi-directory refactor (fixes #7588).
- **#7592** — *Telegram intermediate message cleanup* — optional auto-cleanup of reasoning/tool-call messages after final answer delivery (fixes #7586).
- **#7590** — *Telegram Markdown table rendering* — fixes raw pipe/dash output by rendering tables as `<pre>` blocks (fixes #7585).
- **#7591** — *Feishu auto-collapse reasoning card* — reasoning stream cards now collapse after generation completes (fixes #7570).
- **#7569** — *Advisor Mode* — new loop mode pairing a strong advisor model with a cheaper worker model.
- **#7509** — *Make Skill v2* — approval-driven draft-then-publish workflow for reusable workspace Skills.

## 4. Community Hot Topics

| Issue | Title | Comments | Link |
|-------|-------|----------|------|
| #7505 | LAN LLM server frequent `client disconnect` → timeout | 12 | [GitHub](https://github.com/agentscope-ai/QwenPaw/issues/7505) |
| #7450 | Main agent doesn't poll child-agent status without user prompt | 8 | [GitHub](https://github.com/agentscope-ai/QwenPaw/issues/7450) |
| #7559 | 409 error when sending messages during active task | 5 | [GitHub](https://github.com/agentscope-ai/QwenPaw/issues/7559) |
| #6820 | UI not rendering tool calls / thinking in real-time | 5 | [GitHub](https://github.com/agentscope-ai/QwenPaw/issues/6820) |
| #7363 | Sync calls block event loop; Windows unresponsive for ~120s | 4 | [GitHub](https://github.com/agentscope-ai/QwenPaw/issues/7363) |
| #6814 | SIGBUS crash opening SQLite WAL `history.db` on macOS | 4 | [GitHub](https://github.com/agentscope-ai/QwenPaw/issues/6814) |

**Analysis:** The #7505 LAN disconnect issue is the top concern, reflecting a significant user base running local LLM servers (LM Studio, etc.) — streaming timeout and connection resilience remain a pain point. The #7450 / #7559 cluster reveals a common workflow friction: users expect background agents to proactively report status and queue follow-up messages rather than erroring out. The SQLite crashes (#6814, #7596) indicate persistent storage reliability needs attention.

## 5. Bugs & Stability

### Critical / High Severity
- **#7584 / #7579** — *Model replies vanishing from context*; AI "forgets" its own responses, causing tool-call loops and behavior regression. **[Fix PR: #7578]** (logging improvement; root-cause fix pending)
- **#7596** — *FTS index corruption in `history.db` undetected by `PRAGMA integrity_check`*; retention purge fails silently on every startup.
- **#7576** — *Hardcoded 32768 `context_size` fallback in `RetryChatModel`* causes `CONTEXT_UNFIT` errors for models with larger contexts — confirmed buggy across v2.1.0–v2.2.0.
- **#7363** — *Sync tool calls block the event loop*; Windows desktop freezes 118–135s at startup and ~126s per message.
- **#7589** — *Heartbeat cron session feedback loop*; duplicate messages pile up, rendering the agent unresponsive for ~2 hours.
- **#6814** — *SIGBUS crash* on macOS when opening SQLite WAL-mode `history.db`.

### Medium Severity
- **#7559** — *HTTP 409 on follow-up messages during active task* — queued message rejection instead of enqueue. **[Fix PR: #7577]**
- **#7572** — *Tool dispatch layer swallows exception traces* — only `str(exc)` returned to model; no `logger.exception()`. **[Fix PR: #7578]**
- **#7567** — *Task stop appears successful but execution continues* — UI and backend state desync.
- **#7585** — *Telegram Markdown tables render as raw pipes/dashes*. **[Fix PR: #7590]**
- **#7587** — *Cloudflare 403 when WUSRouter used as OpenAI-compatible provider*.
- **#7513** — *DeepSeek-v4-pro tool-call mixing with QwenPaw internal tool calls*; boundary character issue in model output.

### Low Severity
- **#7099** — *Dark-mode channel tag unreadable* in "All Chats" drawer (CSS selector miscompilation). **Closed.**
- **#7548** — *Navigation history lost after session switch / restart*. **Closed.**
- **#7594** — *Task execution status duplicated 3× at different time points*. **Closed.**

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood for Next Release |
|---------|-------|----------------------------|
| Blocking `wait_for_agent` tool (replaces polling) | #7580 | **High** — directly addresses #7450 workflow need |
| Telegram intermediate message cleanup | #7586 | **High** — fix PR #7592 already open |
| Feishu reasoning card auto-collapse | #7570 | **High** — fix PR #7591 already open |
| Restore v2.1 direct path input for working dir | #7588 | **High** — fix PR #7593 already open |
| Advisor Mode (dual-model loop) | #7569 | **Medium** — new feature, likely next minor |
| One-click plugin update / update notifications | #7582 | **Low** — UX polish, no PR yet |
| AgentScope community login & in-app feedback | #7583 | **Low** — ecosystem integration, long-term |
| Make Skill v2 (approval-driven workflow) | #7509 | **Medium** — in progress |

## 7. User Feedback Summary

**Pain points:**
1. **Context instability** — Users repeatedly report model replies disappearing from conversation history (#7579, #7584, #7447), causing the agent to re-perform completed work or enter tool-call loops. This is the single most disruptive class of bug.
2. **No proactive status reporting** — Multi-agent tasks silently stall until the user explicitly asks "进度如何" (#7450); users want the main agent to self-monitor and report.
3. **409 errors block async workflows** — Sending follow-up messages during an active run is rejected instead of queued (#7559), breaking natural conversation flow.
4. **Telegram channel UX** — Raw Markdown tables, intermediate message clutter, and missing table rendering make Telegram a degraded experience (#7585, #7586).
5. **Plugin store friction** — Installing/updating multiple plugins requires excessive clicking; no bulk-update or update-notification mechanism (#7582).
6. **LAN local-server connectivity** — Frequent `client disconnect` when connecting to LM Studio / local OAI servers causes cascading timeouts (#7505).

**Satisfaction signals:**
- Feishu streaming cards praised when working (#7570 positive comment on v2.1 behavior).
- Memory lifecycle refactor (#7561) is welcomed as a needed architectural cleanup.
- First-time contributors are successfully landing PRs, indicating a low barrier to entry.

## 8. Backlog Watch

| Issue | Reason for Attention |
|-------|---------------------|
| **#7576** — Hardcoded `context_size=32768` fallback | Affects all models exceeding 32K tokens; confirmed in v2.1.0–v2.2.0. No fix PR yet. |
| **#7596** — FTS corruption silent failure | Data-loss risk; `integrity_check` passes but purge fails every startup. Needs root-cause fix, not just error handling. |
| **#7363** — Event loop blocked by sync calls | Causes ~2-minute freezes on Windows; no fix PR. Architectural issue in coordinator design. |
| **#7589** — Heartbeat cron feedback loop | Agent unresponsive for hours; severity high, no fix PR. |
| **#6814** — SQLite WAL SIGBUS on macOS | Platform-specific crash; no fix PR. |
| **#7505** — LAN client disconnect loop | User-facing reliability issue for local-server deployments; no fix PR. |
| **#7572** — Exception swallowing in `_drain()` | Debugging blocker for all tool-dispatch failures. Fix PR #7578 improves logging but may not address root cause. |

---

**Project Health Assessment:** CoPaw v2.2 is experiencing a **stabilization wave** — high issue volume driven by context-management regressions and channel-rendering gaps, but also strong community response with multiple first-time contributor fix PRs landing. The architecture is maturing (memory lifecycle refactor, Advisor Mode, Skill v2). The critical path for the next release should prioritize: (1) context retention bugs (#7579/#7584/#7447), (2) the 409 enqueue fix (#7577), and (3) SQLite FTS durability (#7596).

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>



# ZeptoClaw Project Digest — 2026-09-07

## 1. Today's Overview

ZeptoClaw saw minimal activity over the last 24 hours, with one open issue updated and no pull requests or new releases. The project's primary ongoing concern is **delegated-agent capability inheritance** — a safety-critical gap where child agents must not exceed their parent's policy scope. With no merged PRs or new releases today, the project appears to be in a quiet maintenance phase focused on architectural hardening rather than feature rollout.

**Activity Assessment:** 🟡 Low — one active issue, no PRs, no releases.

## 2. Releases

No new releases reported in the last 24 hours.

---

## 3. Project Progress

No merged or closed pull requests today. No features or fixes advanced on this date.

---

## 4. Community Hot Topics

**[#664 — Delegated-agent capability inheritance](https://github.com/qhkm/zeptoclaw/issues/664)** *(Open · P2-High · 1 comment · 0 reactions)*

This is the only active issue and the clear focal point of current community concern. It identifies a gap in ZeptoClaw's delegation system: while child agent loops, sessions, concurrency, and recursion blocking are already implemented (`src/tools/delegate.rs`), **policy inheritance is incomplete**. The concern is that delegated/subordinate agents could, through capability inheritance, exceed the policy boundaries set by their parent agent — a serious safety risk for any multi-agent system.

**Underlying need:** As ZeptoClaw's delegation architecture matures, users are demanding enforceable policy containment across agent hierarchies. This signals a maturing user base that is deploying ZeptoClaw in multi-agent scenarios where trust boundaries matter.

---

## 5. Bugs & Stability

No bug reports, crashes, or regressions filed today. No stability concerns flagged in the current data.

---

## 6. Feature Requests & Roadmap Signals

**[#664 — Policy inheritance for delegated agents](https://github.com/qhkm/zeptoclaw/issues/664)** is the dominant signal. The issue goes beyond a feature request — it frames a **safety gap** in an already-existing delegation system. This strongly suggests the next release cycle will prioritize:

- Policy propagation from parent to child agents
- Capability-bound enforcement in delegation chains
- Auditing/visibility into delegated agent permissions

This aligns with a broader trend in the AI agent ecosystem toward **safe multi-agent orchestration** as a differentiator.

---

## 7. User Feedback Summary

The single open issue reflects a **constructive, technically sophisticated user** (author: `qhkm`, the maintainer) who has deeply engaged with the codebase. The feedback is not a complaint but a precise architectural observation — the delegation system works functionally but lacks a safety guarantee at the policy layer. This suggests:

- Users are **deploying ZeptoClaw in multi-agent configurations** and hitting real-world boundary conditions
- Satisfaction with the core delegation mechanism is high (the gaps are described as "already solid")
- The community values **correctness and safety** over feature velocity

---

## 8. Backlog Watch

**[#664](https://github.com/qhkm/zeptoclaw/issues/664)** — Open since 2026-09-05, last updated 2026-09-06. This is a **P2-high** issue authored by the project maintainer, indicating it is on the internal radar but not yet addressed with a fix PR. Given its safety implications, it should be considered a **top-priority backlog item** for the next development cycle. No fix PR currently exists.

---

*Digest generated from GitHub data as of 2026-09-07. Source: [github.com/qhkm/zeptoclaw](https://github.com/qhkm/zeptoclaw)*

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-09-07

## 1. Today's Overview

ZeroClaw remains in an active stabilization cycle for the v0.8.5 milestone, with 33 issues and 50 PRs touched in the last 24 hours. The project is heavily focused on RFC maturation (conversation sessions, file/attachment architecture, WASM plugins, session event history), critical bug fixes around daemon reliability and provider correctness, and channel robustness. No new releases were published today, and the intake freeze for v0.8.5 remains in effect. Overall project health is strong — high contributor engagement, rapid maintainer follow-through on bug reports, and a clear architectural convergence around session persistence and delegation safety.

## 2. Releases

No new releases today. The v0.8.5 stabilization tracker (#9459) remains the active release milestone, with weekly cuts shipping ready work through the August 30, 2026 line.

## 3. Project Progress

**Merged/Closed PRs today:**
- **#10572** — WeCom (WeChat Work) channel documentation completed and closed.
- **#9653** — Plugin WASM `wasi:http` TLS root trust gap closed; plugin egress now aligns with provider HTTPS trust-store behavior.
- **#9575** — OpenAI-compatible provider warmup route fixed to use `/models` instead of `/chat/completions`, avoiding 405 Method Not Allowed responses.

**In-progress work advancing today:**
- **#10637 / #10638** — Gateway boot-default provider seeding fixes consolidate WebSocket memory onto the correct per-agent provider and resolve cases where the first provider entry had no model declared.
- **#10671** — Fixes #10670: `heartbeat.target` now accepts channel instance composite keys (`<type>.<alias>`), unblocking multi-instance channel setups.
- **#10668** — Windows CI locale resource scoping corrected, addressing part of the 74-test Windows regression (#7462).
- **#10669** — Discord STT dispatch test added to verify routed provider selection parity with the recent Matrix fix.
- **#10407** — Persistent session prompt attachments (up to 4 SQLite-backed, opt-in) advancing through review with tools for listing, setting, and deleting attachments.
- **#10197 / #9378** — ACP transcript persistence for interrupted, failed, and cancelled turns continues integration, ensuring turn progress is recoverable across session restores.

## 4. Community Hot Topics

| Issue/PR | Comments | Summary |
|---|---|---|
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — RFC: Runtime-owned conversation sessions & transport adapters | 34 | Revision 5 of a foundational architecture RFC on session ownership and transport surfaces. |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) — RFC: Unified file & attachment architecture | 27 | Revision 10; convergence point for how files/attachments flow across conversation surfaces. |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) — RFC: Granular sandbox filesystem policy | 25 | Aligns application-layer path admission with OS sandbox backends (Bubblewrap, Landlock, Seatbelt). |
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) — 74 test failures on Windows | 19 | CI only runs Linux; full Windows parity remains a gap. |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue tracker | 15 | Active coordination point for RFCs and design issues needing maintainer resolution. |
| [#10076](https://github.com/zeroclaw-labs/zeroclaw/issues/10076) — RFC: Composable WASM plugin runtime | 10 | Defines core APIs, typed extension points, and replaceable providers for the WASM plugin system. |

**Underlying needs:** The community is driving two convergent themes — **(1) durable session architecture** (issues #9487, #9488, #10526, #10407) and **(2) security/sandbox hardening** (#6996, #10076, #10644, #10645). The high comment counts on RFCs indicate deep stakeholder engagement, but also signal that design consensus requires sustained maintainer attention.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|---|---|---|---|
| **S1 — workflow blocked** | [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | Daemon startup/reload stack overflow during agent initialization via Quickstart apply | — |
| **S1** | [#9421](https://github.com/zeroclaw-labs/zeroclaw/issues/9421) | Incomplete terminal responses reported as successful | [#9447](https://github.com/zeroclaw-labs/zeroclaw/pull/9447) (open, in review) |
| **S1** | [#9191](https://github.com/zeroclaw-labs/zeroclaw/issues/9191) | Cron agent jobs lack wall-clock timeout; locks only cleared at process start | — |
| **S1** | [#10670](https://github.com/zeroclaw-labs/zeroclaw/issues/10670) | `heartbeat.target` rejects composite channel instance keys | [#10671](https://github.com/zeroclaw-labs/zeroclaw/pull/10671) (open) |
| **S1** | [#10659](https://github.com/zeroclaw-labs/zeroclaw/issues/10659) | Budget-exceeded Code turn loses visible progress after session restore | — |
| **S2** | [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | 74 Windows test failures (non-Unix path semantics, encoding) | [#10668](https://github.com/zeroclaw-labs/zeroclaw/pull/10668) (partial) |
| **S2** | [#10302](https://github.com/zeroclaw-labs/zeroclaw/issues/10302) | ZeroCode Code pane stuck in Processing state, consuming CPU | — |
| **S2** | [#10635](https://github.com/zeroclaw-labs/zeroclaw/issues/10635) | Runtime profile cost limit shows unbounded value while global daily budget rejects turns | [#10645](https://github.com/zeroclaw-labs/zeroclaw/pull/10645) (open, follow-up) |
| — | [#10617](https://github.com/zeroclaw-labs/zeroclaw/issues/10617) | `thinking.display = "updates"` returns 400 on Claude Fable 5.1; enum narrowed | — |
| — | [#10662](https://github.com/zeroclaw-labs/zeroclaw/issues/10662) | OAuth system-prefix cache marker consumes one of four breakpoint slots, below minimum | — |

**Notable:** Multiple S1 bugs are in the daemon/runtime cost-tracking and session-persistence layers. The incomplete-terminal-response classification fix (#9447) and the heartbeat composite-key fix (#10671) are the most urgent openPRs. No critical crash regressions were reported today beyond #10230 (stack overflow on Quickstart apply).

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood for v0.8.5+ |
|---|---|---|
| [#10526](https://github.com/zeroclaw-labs/zeroclaw/issues/10526) — Append-only session event history | Deterministic state replay and derived agent streams | **High** — RFCRevision 1+, closely tied to #9487 |
| [#10531](https://github.com/zeroclaw-labs/zeroclaw/issues/10531) — Delegate sub-agent progress visibility | Tool receipts and partial output from background delegates | **Medium** — Follow-up to #10601; spans runtime + TUI |
| [#10426](https://github.com/zeroclaw-labs/zeroclaw/issues/10426) — Agent progress in Telegram | User-facing progress during long-running tool calls | **Medium** — Channel-specific UX enhancement |
| [#10660](https://github.com/zeroclaw-labs/zeroclaw/issues/10660) — Third Anthropic cache breakpoint | Placed on previous turn's last message to reduce turn-boundary misses | **Low–Medium** — Provider optimization, may ship post-v0.8.5 |
| [#10580](https://github.com/zeroclaw-labs/zeroclaw/issues/10580) — Repo-wide docs link gate | CI catch dangling internal links across the entire repo | **Low** — CI infra improvement |
| [#7759](https://github.com/zeroclaw-labs/zeroclaw/issues/7759) — Decouple gateway WS from agent turn lifecycle | Background turns survive client reconnect | **High** — P1, long-requested architecture change |

**Roadmap signal:** The project is clearly converging on a **durable, replayable session model** (RFCs #9487, #9488, #10526; PR #10407; fixes #10197, #9378). This architectural shift will likely define the v0.9.0 feature boundary. Cost-tracking correctness (#10644, #10645, #10635) and delegate observability (#10531) are also emerging as cross-cutting priorities.

## 7. User Feedback Summary

- **Pain point — silent Telegram sessions:** Users report that long-running agent turns through Telegram appear stalled with no progress feedback until the final response arrives (#10426).
- **Pain point — budget-exceeded turns lose progress:** When a daily cost limit is hit mid-turn in ZeroCode/ACP, the streamed assistant text and tool activity are discarded on session restore, causing visible data loss (#10659).
- **Pain point — Windows CI gap:** The test suite passes on Linux but fails on Windows due to path semantics and console encoding, meaning Windows users face untested code paths (#7462).
- **Satisfaction — Rapid bug triage:** Issues filed today (#10670, #10659, #10660, #10662) already have maintainer engagement and fix PRs in flight within hours, indicating a responsive maintainership cadence.
- **Satisfaction — RFC process maturity:** The structured revision-based RFC workflow (evidenced by #9487 Rev 5, #9488 Rev 10) provides clear decision trails, though the process itself is cited as a friction point (#10549).

## 8. Backlog Watch

| Issue | Age | Concern |
|---|---|---|
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) — 74 Windows test failures | ~3 months | CI parity gap; partial fix in #10668 but full resolution incomplete |
| [#9191](https://github.com/zeroclaw-labs/zeroclaw/issues/9191) — Cron jobs lack wall-clock timeout | ~2 months | No fix PR; safety risk for unbounded daemon cron execution |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) — Granular sandbox filesystem policy RFC | ~3 months | RFC still in progress; no merged implementation yet |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue | ~2 months | Tracker itself is active but many RFCs are queued behind it |
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) — Daemon stack overflow on Quickstart apply | ~1.5 months | No fix PR yet; S1 severity |

**Recommendation:** The v0.8.5 stabilization line should prioritize #10230 (daemon crash), #9191 (cron timeout safety), and completing #7462 (Windows parity) before the next release cut. The RFC backlog (#6996, #8692) requires dedicated maintainer review windows per the tracker in #8692.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*