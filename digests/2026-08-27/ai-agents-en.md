# OpenClaw Ecosystem Digest 2026-08-27

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-27 08:44 UTC

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



# OpenClaw Project Digest — 2026-08-27

## 1. Today's Overview

OpenClaw remains in a high-velocity development phase with **500 issues and 500 PRs updated in the last 24 hours**, of which 181 issues were closed and 139 PRs merged or closed. No new releases were published today, but the project is actively iterating on the **2026.8.1 beta** track, with beta feedback gathering momentum. Activity is concentrated around gateway stability, session lifecycle correctness, and UI polish, signaling a phase of stabilization preceding the next release. The ratio of open-to-closed issues (319 open vs. 181 closed) suggests a growing backlog of active bugs, many of which are tagged P0/P1 and carry high impact ratings.

## 2. Releases

**No new releases today.** The current beta track is **v2026.8.1-beta.3** (commit `5831b80721f802072b0ec1893b30a16cf42d538c`), with the guidance main commit at `004b06b6a02f0aa5ddcee488caa9c51d38e6d017`. Beta feedback is being collected in [Issue #125626](https://github.com/openclaw/openclaw/issues/125626), which has already accumulated 20 comments. The prior **2026.7.1-2** release (commit `0790d9f`) continues to surface regressions in the Wild (see Bugs & Stability).

## 3. Project Progress

**Merged / Closed PRs today:**

| PR | Summary | Status |
|---|---|---|
| [#128995](https://github.com/openclaw/openclaw/pull/128995) | Make full session actions (pin, mark unread, set icon, copy session ID, move to group) available from the chat header | ✅ Closed |
| [#126424](https://github.com/openclaw/openclaw/pull/126424) | Keep conversation delivery within agent bindings across Discord, iMessage, Matrix, Mattermost, Slack, Telegram, and Feishu | ✅ Closed |
| [#120900](https://github.com/openclaw/openclaw/pull/120900) | Review install-policy warnings in Control UI with operator acknowledgement | ✅ Closed |
| [#123975](https://github.com/openclaw/openclaw/pull/123975) | Clean up `tsgo` process trees on timeout or signal, adding watchdog via `OPENCLAW_TSGO_TIMEOUT_MS` | ✅ Closed |
| [#130828](https://github.com/openclaw/openclaw/pull/130828) | Recover machine choices after catalog failures in the Crabbox extension | ✅ Closed |
| [#116489](https://github.com/openclaw/openclaw/pull/116489) | Require acknowledgement for install policy warnings via `security.installPolicy` command | ✅ Closed |
| [#125471](https://github.com/openclaw/openclaw/pull/125471) | Keep Claude CLI OAuth available in Control UI after gateway restart | ✅ Closed |

**Notable in-progress PRs:**

- [#130788](https://github.com/openclaw/openclaw/pull/130788) — *Fix: keep effort control visible in composer row on mobile/narrow layouts* (P1, waiting on author)
- [#130831](https://github.com/openclaw/openclaw/pull/130831) — *Refactor: remove redundant model catalog suppression paths* (P1, waiting on author)
- [#130758](https://github.com/openclaw/openclaw/pull/130758) — *Fix: keep chat messages separated after scroll interruptions* (P1, waiting on author)
- [#130168](https://github.com/openclaw/openclaw/pull/130168) — *Feat: one consent screen for plugin capabilities, bound to reviewed artifact* (P1, XL, waiting on author)
- [#130586](https://github.com/openclaw/openclaw/pull/130586) — *Fix: reconcile transport-ambiguous subagent dispatch instead of misreporting* (P1, ready for maintainer)
- [#130804](https://github.com/openclaw/openclaw/pull/130804) — *Fix: release stalled captured provider responses promptly* (ready for maintainer)

## 4. Community Hot Topics

**Most discussed issues (by comment count):**

1. **[Issue #125626](https://github.com/openclaw/openclaw/issues/125626)** — *OpenClaw 2026.8.1 beta feedback* (20 comments) — The community is actively stress-testing the latest beta. Concerns span gateway startup, model routing, and channel behavior.

2. **[Issue #108435](https://github.com/openclaw/openclaw/issues/108435)** — *Gateway fails to start after updating to 2026.7.1* (15 comments, 3 👍, P0, diamond lobster) — A critical regression where the gateway refuses to start under systemd, Ollama, or manual launch. High community frustration; no fix PR yet.

3. **[Issue #43367](https://github.com/openclaw/openclaw/issues/43367)** — *Multi-agent orchestration instability: concurrent config overwrites, session-lock failures, detached children* (14 comments, P1, gold shrimp) — A long-standing reliability concern for users running parallel agent batches.

4. **[Issue #38327](https://github.com/openclaw/openclaw/issues/38327)** — *"Cannot convert undefined or null to object" with google-vertex/gemini-3.1-pro-preview* (14 comments, 3 👍, P1, diamond lobster) — Regression in embedded agent handling after 2026.3.2; blocks Vertex AI users.

5. **[Issue #53628](https://github.com/openclaw/openclaw/issues/53628)** — *`$XDG_CONFIG_HOME` not interpreted during skill install* (14 comments, P2) — Blocks Docker-based deployments; a configuration-portability pain point.

6. **[Issue #88657](https://github.com/openclaw/openclaw/issues/88657)** — *DeepSeek V4 Flash incomplete turns (payloads=0, tools=2)* (12 comments, P1, diamond lobster) — Regression between 2026.5.26 and 2026.5.27/28 affecting OpenRouter-powered DeepSeek users.

**Underlying needs:** The community is demanding (a) stable multi-agent orchestration, (b) reliable gateway boot across all deployment modes, (c) consistent behavior across LLM providers (Google Vertex, DeepSeek via OpenRouter, Claude CLI), and (d) proper container/Docker configurability.

## 5. Bugs & Stability

**P0 / Release-Blocking:**

| Issue | Severity | Summary | Fix PR? |
|---|---|---|---|
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | P0 · diamond lobster · crash-loop | Gateway fails to start after 2026.7.1 update (systemd/Ollama/manual) | ❌ None |
| [#48920](https://github.com/openclaw/openclaw/issues/48920) | P0 · platinum hermit · ux-release-blocker | Live docs reference `IsolatedSessions` heartbeat config not present in 2026.3.13 | ❌ None |

**P1 / High-Impact Regressions:**

| Issue | Summary | Fix PR? |
|---|---|---|
| [#128971](https://github.com/openclaw/openclaw/issues/128971) | Telegram final reply silently lost when terminal receipt returns `delivery_ambiguous` | ❌ None |
| [#118839](https://github.com/openclaw/openclaw/issues/118839) | Restart-recovery regression: "claim changed before agent adoption" on 2026.7.2-beta.7 for WebChat→Telegram sessions | ❌ None |
| [#114234](https://github.com/openclaw/openclaw/issues/114234) | Usage-cost refresh lock never releasable after PID-reusing container restart | ❌ None |
| [#113093](https://github.com/openclaw/openclaw/issues/113093) | v2026.7.1-2 + `tools.profile: full` + llama.cpp MTP → 413/400 on tool payload | ❌ None |
| [#118018](https://github.com/openclaw/openclaw/issues/118018) | Stale subagent completion delivered into replaced requester lifecycle | ❌ None |
| [#112259](https://github.com/openclaw/openclaw/issues/112259) | Visible inbound channel turn silently dropped: zero-payload dispatch, no retry/dead-letter | ❌ None |
| [#110771](https://github.com/openclaw/openclaw/issues/110771) | WebChat persists internal records and loses durable turn status after 2026.7.1-2 upgrade | ❌ None |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Child process leak (hooks/bash/codex) causing zombie accumulation and runtime degradation | ❌ None |
| [#80498](https://github.com/openclaw/openclaw/issues/80498) | Subagent completion announcements premature or duplicated after tool-use turns | ❌ None |
| [#88657](https://github.com/openclaw/openclaw/issues/88657) | DeepSeek V4 Flash incomplete turns via OpenRouter | ❌ None |

**P2 / Notable:**

| Issue | Summary | Fix PR? |
|---|---|---|
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | "Cannot convert undefined or null to object" with google-vertex/gemini | ❌ None |
| [#123652](https://github.com/openclaw/openclaw/issues/123652) | Azure/OpenAI runtimeContextCarrier tail relocation breaks GPT-5.6 prompt cache lineage | ❌ None |
| [#115001](https://github.com/openclaw/openclaw/issues/115001) | Hybrid memory search returns spurious 1.0 similarity scores via FTS LIKE-fallback | ✅ Closed |
| [#123792](https://github.com/openclaw/openclaw/issues/123792) | Assistant turns render twice with CLI backends (live per-block + concatenated aggregate) | ❌ None |
| [#118482](https://github.com/openclaw/openclaw/issues/118482) | codex-supervisor WebSocket handshake fails over unix socket (permessage-deflate) | ❌ None |

**Key stability assessment:** The project is experiencing a **regression wave** around the 2026.7.x → 2026.8.x transition. Session lifecycle, gateway startup, and multi-provider routing are the weakest areas. No fix PRs exist for any P0 issue, and most P1 regressions are unaddressed. The **#97616** process-leak bug and **#43367** multi-agent orchestration issue are chronic stability concerns that have persisted for months.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Votes 👍 | Likelihood |
|---|---|---|---|
| [#40786](https://github.com/openclaw/openclaw/issues/40786) | `.gitignore`-like exclude patterns for `openclaw backup create` | 1 | Medium — practical, low-risk |
| [#51441](https://github.com/openclaw/openclaw/issues/51441) | Expose resolved backend model in `session_status` and agent runtime | 1 | Medium — improves LiteLLM/proxy observability |
| [#79163](https://github.com/openclaw/openclaw/issues/79163) | User notification + workspace context re-injection on model fallback | 1 | High — addresses a real failure mode |
| [#45390](https://github.com/openclaw/openclaw/issues/45390) | Session TTL / max lifetime for automatic rotation | 1 | Medium — configuration burden on users now |
| [#45415](https://github.com/openclaw/openclaw/issues/45415) | `MEMORY.md` size warning/limit enforcement | 1 | Low — simple addition |
| [#4

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: Open-Source AI Agent Ecosystem
**Date: 2026-08-27**

---

## 1. Ecosystem Overview

The open-source personal AI agent landscape in mid-2026 is characterized by intense activity concentrated in a handful of projects, with most teams transitioning from feature-blast cycles into stabilization and security hardening. Seven of eleven tracked projects show meaningful daily velocity, while three are dormant or near-stalled. The dominant theme across the ecosystem is a shift from raw capability to production reliability: session lifecycle correctness, gateway boot stability, multi-agent orchestration safety, and provider-agnostic routing are now the primary engineering challenges. Security hardening—ranging from path traversal and shell injection fixes to sandbox TOCTOU closures—has emerged as a cross-project imperative.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Merged/Closed | Releases | Open Bug Backlog | Health Score |
|---|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 181 issues / 139 PRs | Beta track (no new release) | 2 P0 (no fix PRs), 10+ P1 | 🔴 4/10 |
| **Hermes Agent** | 50 | 50 | 6 PRs / ~4 issues | None (holding for fix accumulation) | 3 P1, 6+ P2 open | 🟡 5/10 |
| **ZeroClaw** | 37 | 50 | 10 issues / 6 PRs | None (v0.9.0 in progress) | Multiple blocked PRs | 🟡 5/10 |
| **CoPaw** | 26 | 39 | 12 issues / 19 PRs | v2.2.0-beta.1 | 2 High, 2 Medium | 🟢 7/10 |
| **NanoClaw** | 3 | 23 | 5 PRs | None | 1 Critical, 1 High | 🟡 5/10 |
| **IronClaw** | 46 | 50 | 20 issues / 47 PRs | v1.4.0-rc.1 | 1 High perf, 1 Medium | 🟢 8/10 |
| **NanoBot** | 2 | 33 | 16 PRs / 2 issues | None | 1 Security (P0 equiv.) | 🟢 7/10 |
| **LobsterAI** | 1 | 11 | All merged | v2026.8.26 (yesterday) | 1 Medium | 🟢 8/10 |
| **Moltis** | 0 | 2 | 2 PRs / 1 issue | 20260826.01 (yesterday) | None | 🟢 9/10 |
| **PicoClaw** | 7 | 6 | 3 PRs closed | None | 1 High (Web UI lag), 2 Medium | 🟡 5/10 |
| **NullClaw** | 1 | 0 | 0 | None | None | 🟢 9/10* |
| **ZeptoClaw** | 0 | 0 | 0 | None | None | ⚪ 2/10 |

*NullClaw scores high on stability but near-zero activity suggests potential abandonment.

**Health score methodology:** Weighted composite of merge velocity, bug resolution rate, release cadence, and open critical-backlog severity.

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of community engagement:** 500 issues/PRs in 24h dwarfs every other project, indicating the largest active contributor base and broadest channel coverage (Discord, iMessage, Matrix, Mattermost, Slack, Telegram, Feishu).
- **Channel parity:** The only project explicitly shipping unified delivery across 7+ messaging platforms with session lifecycle preservation per binding.
- **Beta feedback loop:** Issue #125626 (beta feedback) has 20 comments, showing an organized community testing process absent in most peers.

**Technical approach differences:**
- Unlike IronClaw (which retired its v1 monolith for a Reborn architecture) or CoPaw (which ships per-release betas with doc/blog tie-ins), OpenClaw operates on a rolling beta track (2026.8.1) with gradual issue triage rather than structured release cycles.
- OpenClaw's gateway-centric model—with session artifacts, subagent dispatch, and transport-ambiguous routing—creates more moving parts than NanoBot's agent-loop model or LobsterAI's renderer-focused architecture, directly contributing to its regression wave.

**Community size comparison (proxied by 24h issue volume):**
OpenClaw (~500) → Hermes Agent (~50) ≈ IronClaw (~46) > ZeroClaw (~37) > CoPaw (~26) > NanoClaw (~3) > PicoClaw (~7) > NanoBot (~2) > LobsterAI (~1) > Moltis (~0) > NullClaw (~1) >> ZeptoClaw (0).

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Session lifecycle & state persistence** | OpenClaw, Hermes Agent, NanoClaw, CoPaw | Correct recovery after gateway restart, no silent session loss, durable turn status across upgrades |
| **Gateway reliability & boot** | OpenClaw, Hermes Agent, NanoClaw | Gateway must start under systemd/Ollama/manual; Windows cold-start timeouts; SSH remote boot failures |
| **Multi-provider / multi-agent routing** | OpenClaw, Hermes Agent, IronClaw, CoPaw | Stable concurrent config, subagent dispatch correctness, provider-agnostic model fallback with user notification |
| **Security hardening** | NanoBot, NanoClaw, IronClaw, ZeroClaw | Path traversal (#5564), shell injection (#3550), TOCTOU in filesystem (#6817), host-launcher resolution (#10381) |
| **Channel adapter stability** | OpenClaw, PicoClaw, NanoClaw, IronClaw | Telegram markdown parsing, Slack media upload, IRC long-message reassembly, Mattermost thread persistence |
| **Observability & analytics** | IronClaw, CoPaw, LobsterAI | Tenant BI telemetry, prompt-cache hit rates, per-user notification inboxes, cloud artifact lifecycle tracking |
| **Container / deployment robustness** | OpenClaw, NanoClaw, CoPaw | Docker config portability (`$XDG_CONFIG_HOME`), Node version floors, `jq` in containers, Windows installer reliability |
| **MCP integration & OAuth** | Hermes Agent, Moltis, NanoClaw, ZeroClaw | OAuth refresh-token rotation, scope registration correctness, per-group MCP policy enforcement |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | IronClaw | CoPaw | Hermes Agent | NanoBot | LobsterAI | ZeroClaw |
|---|---|---|---|---|---|---|---|
| **Primary target** | Multi-channel personal agent | Production-grade team agent | Chinese-market / Qwen-integrated agent | Desktop-first personal agent | Developer / coding agent | Renderer-first creative agent | Security-first gateway agent |
| **Architecture** | Gateway + channel bindings + subagent dispatch | Reborn stack (retired v1 monolith) | Workspace + console + plugin system | Desktop app + gateway + memory | Agent loop + TUI/WebUI | Renderer + cloud library | Gateway + secure transport |
| **Key differentiator** | 7+ channel parity, session artifacts | Performance hardening, sandbox security | Multi-tenant Hub roadmap, prompt cache | `hermes webapp` browser mode, MCP OAuth resilience | Tool loader decoupling, native reasoning lifecycle | Analytics instrumentation, cloud artifact lifecycle | mTLS transport (ZeroRelay), secure model picker |
| **Release cadence** | Rolling beta (no fixed cadence) | Structured RC → release | Beta track with docs tie-in | Event-driven (bug-dense accumulation) | Accumulation → release | Daily/regular patches | Milestone-tracked (v0.9.0) |
| **Security posture** | Installation-policy warnings, OAuth persistence | TOCTOU closure, TLS seam, bounded JSON views | TLS/OpenSSL concerns (carrier DPI) | MCP OAuth rotation, shared-HERMES_HOME safety | Path traversal risk (open) | Custom-provider friction, icon theme bugs | Host-launcher resolution, Git shell hardening |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (high velocity, active bug resolution):**
- **IronClaw** (47 PRs merged/day, RC shipped, systematic perf closure)
- **OpenClaw** (500 items/day, but regression wave outpacing fixes)
- **CoPaw** (39 PRs, beta released, test coverage sprint: 495 cases)
- **Hermes Agent** (50 items/day, responsive on critical bugs like MCP stdio)

**Tier 2 — Steady Development (moderate velocity, focused work):**
- **ZeroClaw** (50 PRs but many blocked on external factors; v0.9.0 track)
- **NanoBot** (33 PRs, clean merge ratio, security vulnerability surfaced)
- **NanoClaw** (23 PRs, setup hardening wave, 2 critical bugs opened)
- **LobsterAI** (11 PRs all merged, daily release cadence, strong maintainership)

**Tier 3 — Maintenance / Low Activity:**
- **PicoClaw** (6 PRs, channel-specific fixes, stale backlog on UX issues)
- **Moltis** (2 PRs, clean but quiet; release-on-fix cadence)
- **NullClaw** (1 issue, 0 PRs; effectively dormant)

**Tier 4 — Inactive:**
- **ZeptoClaw** (zero activity)

---

## 7. Trend Signals

**1. Production reliability is the new frontier.** The ecosystem-wide regression wave in OpenClaw (gateway boot, session lifecycle), the persistent Desktop/session-state bugs in Hermes Agent, and the session-queue starvation in NanoClaw all signal that the field has moved past "does it work?" to "does it survive production?" Developer tooling should prioritize observability, recovery paths, and graceful degradation.

**2. Multi-tenant architecture is emerging as a table-stakes requirement.** CoPaw's Hub edition roadmap (#7318), IronClaw's tenant BI telemetry (#7931), and per-group MCP policy in NanoClaw (#3551) all point to the same direction: personal AI agents are being adopted by teams, and tenant isolation, admin controls, and per-user policy are becoming core features rather than afterthoughts.

**3. Security is no longer a differentiator—it's a baseline.** Path traversal (#5564), shell injection (#3550), TOCTOU filesystem escapes (#6817), and mTLS transport (#10142) across multiple projects indicate that the community is rapidly maturing past naive trust models. Projects that ship with secure-by-default configurations (ZeroClaw's approach, IronClaw's sandbox work) will gain credibility.

**4. Prompt-cache observability is a cost-leverage point.** CoPaw's user-reported 81.68% vs. 96.02% hit-rate gap (#7335) and IronClaw's P0 cache-identity work (#6986) show that prompt-cache performance is now a measurable, monetizable concern. Agents that expose cache metrics and optimization controls will have a competitive edge for cost-sensitive deployments.

**5. Channel-first deployment is fragmenting the surface layer.** With 7+ messaging platforms as first-class inputs across OpenClaw, PicoClaw, NanoClaw, and IronClaw, the agent framework layer is becoming more important than the UI layer. Developers should invest in abstraction over channel-specific implementations.

**6. Gateway boot reliability is the #1 hidden bottleneck.** Across OpenClaw (#108435, P0), Hermes Agent (SSH remote boot, Windows cold-start), and NanoClaw (signal-cli deadlocks, launchd no-ops), startup failures are the most frustrating and least diagnosable class of bugs. Tools that provide structured boot diagnostics and retry semantics will fill a clear gap.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-27

## 1. Today's Overview

NanoBot's development velocity remains high, with **33 PRs** and **2 issues** updated in the last 24 hours. The project shows a strong balance of bug fixes, refactors, and feature work, with 16 PRs merged/closed today. Activity is concentrated around agent lifecycle improvements, TUI/WebUI polish, and security hardening. No new releases were published today, suggesting the team is currently accumulating changes for an upcoming release.

## 2. Releases

No new releases published today.

## 3. Project Progress

**Merged/Closed PRs (16 today):**

| PR | Summary |
|----|---------|
| [#5558](https://github.com/HKUDS/nanobot/pull/5558) | Refactor: load `MyTool` through tool loader, removing manual registration |
| [#5557](https://github.com/HKUDS/nanobot/pull/5557) | Perf: skip redundant TUI dependency installs via SHA-256 fingerprinting |
| [#5556](https://github.com/HKUDS/nanobot/pull/5556) | Fix: complete native reasoning lifecycle — close provider reasoning before answer content |
| [#5543](https://github.com/HKUDS/nanobot/pull/5543) | Fix: surface chat connection failures in TUI with clearer health-state messaging |
| [#5491](https://github.com/HKUDS/nanobot/pull/5491) | Fix: keep answer text outside reasoning shell across tool turns |
| [#5481](https://github.com/HKUDS/nanobot/pull/5481) | Feature: unified provider usage backend for retry-managed sessions |
| [#5534](https://github.com/HKUDS/nanobot/pull/5534) | Feature: autocomplete skill references in TUI (`$skill-name`) |
| [#5533](https://github.com/HKUDS/nanobot/pull/5533) | Fix: keep `find_files` scans responsive via worker-threading and bounded traversal |
| [#5538](https://github.com/HKUDS/nanobot/pull/5538) | Refactor: clarify active composer actions (`Enter now · Tab next`) |
| [#5546](https://github.com/HKUDS/nanobot/pull/5546) | Refactor: make run usage explicit, removing process-wide side channel |
| [#5548](https://github.com/HKUDS/nanobot/pull/5548) | Refactor: isolate WebSocket app orchestration in WebUI |
| [#5555](https://github.com/HKUDS/nanobot/pull/5555) | Refactor: remove duplicate progress streaming path |
| [#5519](https://github.com/HKUDS/nanobot/pull/5519) | Fix: compact single-pane chat header in WebUI |
| [#5560](https://github.com/HKUDS/nanobot/pull/5560) | Feature: make `nanobot` the default agent command |

**Key themes:** Agent loop decoupling, usage tracking consolidation, TUI responsiveness, and WebUI orchestration isolation are the dominant architectural thrusts today.

## 4. Community Hot Topics

- **[PR #5504](https://github.com/HKUDS/nanobot/pull/5504)** — Surface model retry status in UI (P2, open, conflicts). High comment activity indicates active review discussion. Addresses user frustration with silent model failures.
- **[PR #5234](https://github.com/HKUDS/nanobot/pull/5234)** — Integrate mst-python as metasearch provider (P1, open). Long-running PR (since Aug 3) with community demand for better web search aggregation via Reciprocal Rank Fusion.
- **[PR #5561](https://github.com/HKUDS/nanobot/pull/5561)** — Per-spawn model presets behind allowlist. Alternative implementation of a previously stalled PR (#4291), showing active community design iteration.
- **[Issue #5550](https://github.com/HKUDS/nanobot/issues/5550)** — `read_session` returns empty history with wildcard queries. Closed, but signals a real UX gap when agents reference other sessions.

**Underlying need:** Users are pushing for more transparent agent internals (retry status, tool progress, reasoning lifecycle) and richer search capabilities.

## 5. Bugs & Stability

| Severity | Issue/PR | Description | Fix Status |
|----------|----------|-------------|------------|
| **P1** | [#5533](https://github.com/HKUDS/nanobot/pull/5533) | `find_files` scans became unresponsive under large workspaces | ✅ Merged — worker-threaded, bounded traversal |
| **P2** | [#5550](https://github.com/HKUDS/nanobot/issues/5550) | `read_session` wildcard query returns empty history | ✅ Closed |
| **P2** | [#5543](https://github.com/HKUDS/nanobot/pull/5543) | Chat connection failures silently swallowed in TUI | ✅ Merged — now surfaced with health-state differentiation |
| **P2** | [#5491](https://github.com/HKUDS/nanobot/pull/5491) | Answer text incorrectly rendered inside reasoning shell | ✅ Merged |
| **P2** | [#5556](https://github.com/HKUDS/nanobot/pull/5556) | Native reasoning lifecycle not properly completed | ✅ Merged |
| **P2** | [#5564](https://github.com/HKUDS/nanobot/issues/5564) | **Path traversal via malicious session ID** — potential security vulnerability in `session/manager.py` | 🟡 Open — bot-reported, no fix PR yet |

**Security note:** Issue #5564 flags a path traversal vulnerability where unsanitized session IDs could access arbitrary filesystem paths. This is the highest-severity open item and warrants urgent attention.

## 6. Feature Requests & Roadmap Signals

| Feature | PR | Status | Notes |
|---------|-----|--------|-------|
| Clipboard image paste in TUI | [#5563](https://github.com/HKUDS/nanobot/pull/5563) | Open | `Ctrl+V` / `Alt+V` for image input — high-demand UX improvement |
| Stream tool progress events (OpenAI-compatible) | [#5562](https://github.com/HKUDS/nanobot/pull/5562) | Open | Closes #3698; enables client-side tool lifecycle visibility |
| Per-spawn model presets | [#5561](https://github.com/HKUDS/nanobot/pull/5561) | Open | Resolve #4231; allowlist-based configuration |
| Default `nanobot` as agent command | [#5560](https://github.com/HKUDS/nanobot/pull/5560) | Open | UX simplification — `nanobot` ≡ `nanobot agent` |
| MST metasearch provider | [#5234](https://github.com/HKUDS/nanobot/pull/5234) | Open | P1, open since Aug 3 — multi-engine aggregation |
| Model retry status in UI | [#5504](https://github.com/HKUDS/nanobot/pull/5504) | Open | P2, has conflicts — needs resolution |

**Next release prediction:** The TUI image paste (#5563), tool progress streaming (#5562), and default command shortcut (#5560) are all P2 and recently opened — likely candidates for the next release. The MST provider (#5234) and retry status (#5504) may follow.

## 7. User Feedback Summary

- **Session reference gaps:** Issue #5550 highlights that users expect `@session` + wildcard queries to retrieve full conversation history — a natural interaction pattern that was broken.
- **Connection opacity:** Issue #5543 (now fixed) reflects user pain with silent disconnections; the fix introduces differentiated health messaging, suggesting this was a frequent support concern.
- **Search quality:** PR #5234's extended open status (since Aug 3) indicates strong community demand for better web search, not satisfied by single-engine providers.
- **File search performance:** PR #5533's fix for `find_files` responsiveness addresses a real degradation under large codebases — a known pain point for developers using NanoBot as a coding agent.

## 8. Backlog Watch

| Item | Age | Priority | Risk |
|------|-----|----------|------|
| [#5234](https://github.com/HKUDS/nanobot/pull/5234) — MST metasearch provider | 24 days | P1 | Long-open P1 PR risks community frustration |
| [#5504](https://github.com/HKUDS/nanobot/pull/5504) — Model retry status UI | 3 days | P2 | Has conflicts; blocks transparent agent behavior |
| [#5564](https://github.com/HKUDS/nanobot/issues/5564) — Path traversal in session IDs | 0 days | **Security** | No fix PR yet; bot-reported but needs human review |
| [#5561](https://github.com/HKUDS/nanobot/pull/5561) — Per-spawn model presets | 0 days | P2 | Alternative design — review bandwidth needed |

**Recommendation:** The path traversal issue (#5564) should be triaged immediately. The 24-day-old P1 MST PR (#5234) also needs a maintainer review decision to either merge or close with feedback.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-27

## 1. Today's Overview

Hermes Agent is experiencing a high-velocity development cycle on 2026-08-27, with **50 issues** and **50 PRs** touched in the last 24 hours, indicating intense community engagement and active maintenance. The project is in a **bug-dense phase** — the majority of today's activity centers on Desktop stability, session-state corruption, and platform-specific boot failures rather than new feature development. No new releases were published today, suggesting the team is consolidating fixes before the next version. The balance of 44 open PRs against only 6 merged/closed signals a significant merge backlog, while 46 of 50 open issues remain unresolved.

## 2. Releases

**None today.** The last release stamp referenced in issue #96129 is `791e2ae3257e` (v0.20.5). With 46 open issues and a heavy bug load on `main`, a release is likely being held to allow fix accumulation.

## 3. Project Progress

### Merged / Closed Today
- **#94339** — Fixed the inverted `_stdio_children_dead()` liveness check in MCP stdio tooling (#94335). A one-line logic inversion that was causing all oneshot (`-z`) MCP calls to fail-fast with `TimeoutError`.
- **#96202** — Fixed `test_default_path` for native Windows (`%LOCALAPPDATA%\hermes` vs `~/.hermes`), salvaged from #96003.

### Notable PRs Advanced (Open)
- **#96211** — Passes owning profile in the request body for session archive/pin/unread operations, fixing 404s on non-default profiles.
- **#96210** — Infers MIME `content_type` for Kanban worker completion artifacts, enabling inline rendering of HTML/CSV/PDF deliverables.
- **#94846** — MCP OAuth: recovers from peer-rotated refresh tokens instead of clearing the session, critical for shared `HERMES_HOME` setups.
- **#93580** — Bot Mode: isolates group member sessions by thread, preventing cross-thread session leakage.
- **#96191** — GitHub Enterprise Cloud Copilot authentication: unblocks enterprise token exchange against tenant endpoints.
- **#96192** — Desktop: retains fresh chat socket through the first turn, fixing dropped Bot Chat connections.
- **#96195** — Memory: re-reads and merges on `save_to_disk()` to prevent concurrent data loss when multiple Hermes instances share a profile.
- **#96196** — Coding Worker orchestration closed-loop: adds task model routing, Codex/Claude external worker implementations, and VS Code ACP config.
- **#93508** — Serves the Desktop renderer in browsers via `hermes webapp`, enabling browser-based chat access.

## 4. Community Hot Topics

| # | Type | Title | Comments | Link |
|---|------|-------|----------|------|
| #94335 | Bug (P1, closed) | `_stdio_children_dead()` inverted liveness check | 13 | [Issue](https://github.com/NousResearch/hermes-agent/issues/94335) |
| #93888 | Bug (P1) | Desktop sends local runtime ID to Remote Gateway, can't restore sessions | 13 | [Issue](https://github.com/NousResearch/hermes-agent/issues/93888) |
| #84361 | Bug (P2) | Desktop MEDIA: file links dead — regex + string-concat path bugs | 7 | [Issue](https://github.com/NousResearch/hermes-agent/issues/84361) |
| #95541 | Bug (P2, closed) | macOS TCC anchor re-points venv python3 symlinks, CLI dies | 4 | [Issue](https://github.com/NousResearch/hermes-agent/issues/95541) |
| #86366 | Bug (P1) | `archive_and_compact` duplicates carried-forward tail | 4 | [Issue](https://github.com/NousResearch/hermes-agent/issues/86366) |
| #61443 | Bug (P2) | nix: `.#desktop` breaks on every electron bump (hardcoded hash) | 4 | [Issue](https://github.com/NousResearch/hermes-agent/issues/61443) |
| #77836 | Bug (P2) | Weixin rate-limit circuit breaker → infinite retry loop | 3 👍 | [Issue](https://github.com/NousResearch/hermes-agent/issues/77836) |

**Analysis:** The top-voted issues cluster around **Desktop session state corruption** (#93888, #86366, #94335) and **platform-specific installation/boot failures** (#95541, #61443, #96177). The Weixin circuit breaker issue (#77836) is the only issue with a 👍, signaling community agreement that message-delivery reliability is a critical pain point. The repeated appearance of "sweeper:risk-session-state" tags indicates the team recognizes systemic fragility in session persistence.

## 5. Bugs & Stability

### P1 Bugs
| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#94335](https://github.com/NousResearch/hermes-agent/issues/94335) | MCP stdio children liveness check inverted — all oneshot calls fail-fast | ✅ #94339 (closed) |
| [#93888](https://github.com/NousResearch/hermes-agent/issues/93888) | Desktop cannot restore Remote Gateway sessions (runtime ID mismatch) | ❌ None yet |
| [#86366](https://github.com/NousResearch/hermes-agent/issues/86366) | Compaction duplicates carried-forward tail in session DB | ❌ None yet |
| [#96155](https://github.com/NousResearch/hermes-agent/issues/96155) | Native Responses preflight counts unpruned history, triggers premature compression | ❌ None yet |

### P2 Bugs (Opened Today)
| Issue | Summary |
|-------|---------|
| [#96024](https://github.com/NousResearch/hermes-agent/issues/96024) | SSH remote backend boot failure — zombie processes, timeout loop |
| [#96183](https://github.com/NousResearch/hermes-agent/issues/96183) | Bot Chat panel shows stale messages after reopen |
| [#96134](https://github.com/NousResearch/hermes-agent/issues/96134) | USER.md/MEMORY.md not injected in gateway mode (CLI works) |
| [#96177](https://github.com/NousResearch/hermes-agent/issues/96177) | Windows cold-start: WS probe 10s timeout vs 12–28s backend import, no retry |
| [#96188](https://github.com/NousResearch/hermes-agent/issues/96188) | Desktop SSH: double shell-quoting in `remote-lifecycle.ts` prevents remote start |
| [#96164](https://github.com/NousResearch/hermes-agent/issues/96164) | GHEC Copilot ignores enterprise token exchange / API host |
| [#96160](https://github.com/NousResearch/hermes-agent/issues/96160) | Chat viewport jumps to top during streaming |
| [#96138](https://github.com/NousResearch/hermes-agent/issues/96138) | Context length detection fails behind axonhub gateway |

**Assessment:** The project has a **significant Desktop and session-state stability burden**. At least 6 P2 bugs reported today relate to Desktop boot, SSH remote, and session persistence — many with overlapping root causes (process lifecycle, state serialization). Fix PRs exist for 2 of the P1 bugs (#94339 merged; #94846 in progress for MCP OAuth). The Windows cold-start issue (#96177) and SSH double-quoting (#96188) suggest packaging/regression issues from recent updates.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Likelihood |
|-------|---------|------------|
| [#90446](https://github.com/NousResearch/hermes-agent/issues/90446) | Background review cost guardrails — repeated-refusal circuit breaker + token budget | Medium — addresses production cost overruns |
| [#85845](https://github.com/NousResearch/hermes-agent/issues/85845) | Official OpenSpec plugin for Hermes Agent | 3 👍 — spec-driven development workflow |
| [#96136](https://github.com/NousResearch/hermes-agent/issues/96136) | Bot Mode Group Settings — per-member model/provider/reasoning edits | Medium — complements #91329 |
| [#91329](https://github.com/NousResearch/hermes-agent/issues/91329) | Bot Mode: manage members from Group settings | Medium — already has PR #93580 addressing isolation |
| [#93508](https://github.com/NousResearch/hermes-agent/pull/93508) | Serve Desktop renderer in browsers (`hermes webapp`) | High — PR is actively developed |
| [#75131](https://github.com/NousResearch/hermes-agent/issues/75131) | Cron: inject prior delivery context for reply continuity | Low-Medium — `needs-decision` tag |
| [#96207](https://github.com/NousResearch/hermes-agent/pull/96207) | Windows toast notifications for CLI events | Medium — quality-of-life feature, PR ready |
| [#95377](https://github.com/NousResearch/hermes-agent/pull/95377) | Excel-backed long-term memory provider plugin | Low — niche use case |

**Prediction:** The next release will likely include **Browser-hosted Desktop mode** (#93508), **Windows toast notifications** (#96207), and **Bot Mode session isolation** (#93580) as the highest-signal features. The OpenSpec plugin (#85845) has the strongest community endorsement (3 👍) but may lag behind bug fixes.

## 7. User Feedback Summary

**Pain Points:**
- **Session loss on Desktop restart** (#93888, #96183): Users report permanent "Session not found" errors and stale Bot Chat messages, directly impacting trust in the Desktop app.
- **Windows boot reliability** (#96177, #96182): Cold-start timeouts and update failures on Windows are creating friction for a significant user segment.
- **Cost overrun in background reviews** (#90446): Production users report unbounded token consumption when review forks enter refusal loops.
- **MEDIA links silently broken** (#84361): Desktop file-link clicks produce no feedback, making the bug invisible to users.
- **SSH remote boot failures** (#96024, #96129, #96188): A cluster of related SSH bugs suggests a regression in remote backend lifecycle management.

**Satisfaction Signals:**
- The MCP stdio fix (#94335 → #94339) was addressed within 2 days, showing responsive maintenance on critical bugs.
- The shared `HERMES_HOME` multi-process pattern (desktop + gateway) is being actively supported (#94846).
- The `hermes webapp` browser mode (#93508) indicates investment in accessibility beyond the native Desktop.

## 8. Backlog Watch

| Issue | Age | Risk Tag | Why It Needs Attention |
|-------|-----|----------|------------------------|
| [#61443](https://github.com/NousResearch/hermes-agent/issues/61443) | ~2 months | `risk-compatibility` | nix build breaks on every electron bump — blocks NixOS users permanently |
| [#84361](https://github.com/NousResearch/hermes-agent/issues/84361) | ~2 months | — | MEDIA file links silently dead; two independent defects unaddressed |
| [#77836](https://github.com/NousResearch/hermes-agent/issues/77836) | ~2 months | `risk-message-delivery` | Weixin infinite retry loop; only issue with 👍, signaling community frustration |
| [#91653](https://github.com/NousResearch/hermes-agent/issues/91653) | ~2 months | `risk-message-delivery` | Failed delivery obligations never retried while gateway process is alive |
| [#32504](https://github.com/NousResearch/hermes-agent/issues/32504) | ~3 months | — | Dead code: `_budget_grace_call` and `_budget_exhausted_injected` are non-functional remnants |
| [#75131](https://github.com/NousResearch/hermes-agent/issues/75131) | ~2 months | `risk-session-state`, `needs-decision` | Cron context amnesia — requires architectural decision before implementation |

**Overall Health Assessment:** Hermes Agent is in a **high-activity, high-bug-density** state. The project is actively fixing critical issues (MCP stdio, test fixes, memory concurrency) but carries a growing backlog of Desktop stability and session-state bugs. The 44 open PRs vs. 6 merged today suggests a bottleneck in review/merge capacity. The most urgent concern is the cluster of SSH and session-persistence bugs that may indicate a regression in the recent v0.20.5 release cycle.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-27

## 1. Today's Overview

PicoClaw shows moderate daily activity with 7 issues and 6 PRs updated in the last 24 hours. The project remains in a steady maintenance cadence with no new releases this cycle. Recent effort is concentrated on channel-specific bug fixes (Slack, LINE, Telegram) and context-management improvements for routed agents. The contributor base is actively engaging with open issues, though several stale items suggest slower maintainer response times on longer-running tickets.

## 2. Releases

No new releases were published during this reporting period.

---

## 3. Project Progress

**Merged/Closed PRs:**

- **#3314** — Fixed `customAllowPatterns` not working: default deny patterns in `guardCommand` were taking precedence over user-defined allow patterns, preventing commands like `git push` from executing. This restores expected agent shell-execution behavior.
- **#3315** — Added support for topics in private bot chats on Telegram by recognizing `IsTopicMessage` in addition to `IsForum`, fixing forum-topic handling in direct bot conversations.
- **#3316** — Resolved routed-agent context management: dispatch rules now correctly respect chat history, summarization, compression, and Seahorse bootstrap for per-agent routing.
- **#1549** — Closed as a merged batch PR combining fixes from #1448, #1447, #1446, and #1444.

**Open PRs awaiting review:**

- **#3340** — Fixes Slack media upload by setting `FileSize` on upload parameters, addressing the `file.size cannot be 0` rejection.
- **#3329** — Addresses LINE's inert `webhook_host`/`webhook_port` config fields by emitting a warning instead of silently ignoring them.

---

## 4. Community Hot Topics

| Issue / PR | Activity | Key Focus |
|---|---|---|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) — IRC long message support | 8 comments, stale | IRCv3 message cohesion for payloads exceeding 512 bytes |
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) — Web UI chat lag | 7 comments, 1 👍 | Performance degradation in Web UI with longer chat history |
| [#3339](https://github.com/sipeed/picoclaw/issues/3339) — Antigravity 429 errors | 2 comments | Google Antigravity OAuth auth works but generation is blocked by quota |
| [#3338](https://github.com/sipeed/picoclaw/issues/3338) — Slack media upload failure | 2 comments | `file.size cannot be 0` — fix PR #3340 open |

**Underlying needs:** Users are pushing for better **protocol-level correctness** (IRC message reassembly, Slack file upload spec compliance) and **performance at scale** (Web UI lag with history). The Antigravity issue reflects a dependency on external provider quotas rather than a code bug, but it signals growing interest in Google's AI offerings within PicoClaw.

---

## 5. Bugs & Stability

**Reported today (ranked by severity):**

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| 🔴 High | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI input becomes very laggy with moderate chat history — impacts core user experience | — |
| 🟠 Medium | [#3338](https://github.com/sipeed/picoclaw/issues/3338) | Slack media uploads fail silently with `file.size cannot be 0` | [#3340](https://github.com/sipeed/picoclaw/pull/3340) open |
| 🟠 Medium | [#3339](https://github.com/sipeed/picoclaw/issues/3339) | Google Antigravity returns 429 despite valid OAuth and model discovery | — (likely quota-side) |
| 🟡 Low | [#3328](https://github.com/sipeed/picoclaw/issues/3328) | LINE `webhook_host`/`webhook_port` config fields are inert — no warning or error | [#3329](https://github.com/sipeed/picoclaw/pull/3329) open |
| 🟡 Low | [#3346](https://github.com/sipeed/picoclaw/issues/3346) | RKLLM on ARM returns abnormal responses | — |

**Closed bugs this cycle:** The routed-agent context/compression bug (#3316 → closed) and the `customAllowPatterns` shell-exec bug (#3314 → closed) are now resolved.

---

## 6. Feature Requests & Roadmap Signals

- **IRC long-message support** (#3287): Users need PicoClaw to reassemble IRCv3-split messages into coherent payloads. This is a protocol-level feature request that would improve IRC channel reliability.
- **Slack media uploads** (#3338): Fixing `FileSize` is a bug, but the underlying need for richer media support across channels is a recurring theme.
- **Telegram private-topic support** (#3315): Now merged — signals that multi-channel parity (forum topics in private bots) is an active roadmap area.
- **Web UI performance** (#3281): Lag with history suggests a need for virtualized chat rendering or pagination in future versions.

**Prediction:** The next release will likely include the Slack file-size fix (#3340) and the LINE warning (#3329), both small, low-risk patches. IRC long-message support (#3287) is more involved and may appear in a later milestone.

---

## 7. User Feedback Summary

- **Web UI responsiveness** is the top pain point: a user reports significant input lag with moderate history (#3281), which directly affects daily usability.
- **Channel reliability** remains a concern: Slack media uploads (#3338), LINE webhook config invisibility (#3328), and IRC long-message splitting (#3287) all point to gaps in protocol compliance that frustrate power users.
- **Routed-agent workflows** (#3316) were broken but are now fixed — users relying on per-agent dispatch rules will welcome this.
- **Local/embedded AI** interest is growing: the RKLLM issue (#3346) from an ARM board user indicates the edge-AI use case is active but under-tested.

Overall sentiment: users are engaged and reporting detailed, actionable issues, but some channel integrations feel under-maintained.

---

## 8. Backlog Watch

| Issue | Age | Concern |
|---|---|---|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) — IRC long message support | ~36 days, stale | Important for IRC power users; no PR yet |
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) — Web UI chat lag | ~37 days, stale | Core UX issue with 7 comments but no fix PR |
| [#3339](https://github.com/sipeed/picoclaw/issues/3339) — Antigravity 429 | ~10 days | Blocked on Google quota, but needs documentation or clearer error handling |
| [#3346](https://github.com/sipeed/picoclaw/issues/3346) — RKLLM abnormal reply | 1 day, new | Edge AI use case with no responses yet |

**Maintainer attention recommended:** Issues #3287 and #3281 have accumulated comments without resolution and are marked stale — both address meaningful user needs and risk churn if left unaddressed.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-27

## 1. Today's Overview

NanoClaw is experiencing **high development velocity** with 23 PRs and 3 issues updated in the past 24 hours, indicating an active fix-and-refinement cycle rather than a feature-release cadence (no new versions shipped). Activity is dominated by maintenance, setup robustness, and channel-stability patches from contributor Agi-Asi, with a secondary wave of configuration-security hardening from wildcard. Two high-impact bugs were opened today by users, suggesting that recent changes may have exposed edge-case regressions in Telegram message delivery and session-queue handling. Overall project health is strong: the contributor base is diverse, guidelines are being followed, and the maintainer team is responding to merged PRs the same day.

## 2. Releases

No new releases were published in the last 24 hours.

## 3. Project Progress

**Merged / Closed PRs (5 total):**

| PR | Author | Summary |
|----|--------|---------|
| [#3557](https://github.com/nanocoai/nanoclaw/pull/3557) | glifocat | Mattermost: improved initial setup and SiteURL handling |
| [#3556](https://github.com/nanocoai/nanoclaw/pull/3556) | glifocat | Mattermost: recover card thread after host restart |
| *(3 additional closed PRs not shown in top-20)* | — | — |

**Open PRs advancing:**

- **Setup hardening** — #3567 (PATH ordering for onecli guard), #3563 (signal-cli probe timeout vs. deadlocked config lock), #3562 (non-interactive apt to avoid needrestart hang), #3561 (bootstrap unloaded launchd plist instead of silent kickstart no-op), #3555 (raise Node floor to 22.14.0 to prevent better-sqlite3 segfaults).
- **Container & SDK fixes** — #3566 (notify user when container repeatedly fails to wake), #3558 (raise Claude SDK output-token cap to model ceiling), #3564 (stamp series id into task_log rows).
- **Channel & CLI fixes** — #3565 (let forks keep local adapters through skill refresh), #3560 (fail fast with wiring hint when cli/local has no agent), #3553 (normalize reaction emoji per platform in Chat SDK bridge).
- **Security & config** — #3551 & #3552 (enforce per-group MCP policy and OneCLI gateway routing), #3550 (quote email substitution and tighten validation regex to block shell metacharacters).
- **Docs & testing** — #3559 (clarify group-scope auto-fill args as locked), #3501 (document Dial channel in README/changelog), #3554 (keep stdin-json stderr assertions exact on Node 25+).

## 4. Community Hot Topics

**Most-discussed Issue:**
- [#574](https://github.com/nanocoai/nanoclaw/issues/574) — *containers lack jq* (3 comments, 1 👍, closed 2026-08-26). Users request `jq` in container images for safe API-response parsing, noting that the current `node -e` approach invites eval attacks. Signal for a security-conscious runtime baseline.

**Newly opened Issues (both 0 comments):**
- [#3569](https://github.com/nanocoai/nanoclaw/issues/3569) — *Telegram: URLs with an odd number of underscores never deliver.* Pins `@chat-adapter/telegram@4.29.0` three versions behind the upstream fix (4.32.0). High-impact for Telegram users.
- [#3568](https://github.com/nanocoai/nanoclaw/issues/3568) — *Pending system rows starve the inbound queue; agent silently stops responding.* A session-queue starvation bug that causes silent failure once `maxMessagesPerPrompt` (default 10) pending `system` rows accumulate. Critical for production reliability.

**Underlying needs:** Users are hitting stability boundaries in channel adapters (Telegram markdown parsing, Mattermost thread persistence) and session management. There is strong demand for secure-by-default container tooling (jq, Node version floors) and clearer failure diagnostics.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| **Critical** | [#3568](https://github.com/nanocoai/nanoclaw/issues/3568) | Agent silently stops responding when pending system rows starve the inbound queue | No fix PR yet |
| **High** | [#3569](https://github.com/nanocoai/nanoclaw/issues/3569) | Telegram messages with odd unescaped MarkdownV2 markers never deliver | Fix exists upstream in `@chat-adapter/telegram@4.32.0`; trunk still pins 4.29.0 |
| **Medium** | #3556 (now closed) | Mattermost card-thread cache lost after host restart | ✅ Merged |
| **Medium** | #3550 (open) | Email substitution allows shell metacharacters; unquoted regex breaks onboarding | Fix PR open |
| **Low** | #3555 (open) | better-sqlite3 segfaults on Node < 22.14.0 | Fix PR open (raising floor) |

## 6. Feature Requests & Roadmap Signals

- **[#574](https://github.com/nanocoai/nanoclaw/issues/574)** — Include `jq` in container images for safe JSON parsing. Closed as low-priority enhancement, but the security rationale (avoiding `node -e` eval attacks) is compelling. Likely to reappear as a security hardening item.
- **Dial channel documentation** — [#3501](https://github.com/nanocoai/nanoclaw/pull/3501) closes a docs gap; the feature itself shipped in #3050, suggesting the roadmap includes expanding channel listings with proper onboarding docs.
- **Per-group MCP policy enforcement** — [#3551](https://github.com/nanocoai/nanoclaw/pull/3551) and [#3552](https://github.com/nanocoai/nanoclaw/pull/3552) indicate the project is mature enough to ship granular security policies (MCP routing, OneCLI gateway controls), a pattern likely to continue.

## 7. User Feedback Summary

**Pain points:**
1. **Telegram markdown parsing** — Odd-underscore URLs break message delivery; users feel pinned to an old adapter version.
2. **Silent agent failure** — Session queue starvation causes the agent to stop responding with no error, making debugging difficult.
3. **Setup fragility** — Multiple contributors reported deadlocks (signal-cli config lock), hung installers (apt/needrestart), and silent macOS launchd no-ops. The flood of setup-fix PRs (#3561–#3567) reflects real user frustration with brittle installation paths.
4. **Shell injection risk** — Email validation allowed `;`, backticks, and `$()` in onboarding flows; apostrophe-containing emails broke the installer.
5. **Node version incompatibility** — better-sqlite3 segfaults on older Node releases; users need a clear minimum-version guarantee.

**Satisfaction signals:** The tight turnaround on Mattermost fixes (#3556, #3557) and the volume of same-day merged PRs suggest a responsive maintainership team, which likely offsets some frustration.

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| [#3568](https://github.com/nanocoai/nanoclaw/issues/3568) — Pending system rows starve inbound queue | Opened 2026-08-26 | **Critical** — No fix PR; silent production failures |
| [#3569](https://github.com/nanocoai/nanoclaw/issues/3569) — Telegram adapter pinned 3 versions behind upstream fix | Opened 2026-08-27 | **High** — Requires adapter bump + regression test |
| [#574](https://github.com/nanocoai/nanoclaw/issues/574) — Containers lack jq (security concern) | Opened 2026-02-28 | **Medium** — Closed as low priority, but recurring security pattern |
| [#3550](https://github.com/nanocoai/nanoclaw/pull/3550) — Email substitution shell injection | Opened 2026-08-26 | **Medium** — Fix PR open but not yet merged |
| [#3551](https://github.com/nanocoai/nanoclaw/pull/3551) — Per-group MCP policy enforcement | Opened 2026-08-26 | **Low** — Fix PR open; security improvement |

**Recommended maintainer attention:** #3568 (agent starvation) and #3569 (Telegram adapter pin) are the highest-impact open items; both affect core reliability and have no merged fixes yet.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-27

## 1. Today's Overview

NullClaw activity remains low on this date, with only a single open issue updated in the past 24 hours and no pull requests or new releases. The project shows no merged or closed contributions today, indicating a quiet maintenance cycle rather than active development. The lone open issue (#995) is a feature enhancement request around symlink support for skills, suggesting user-driven improvements continue to flow in even during inactive periods. No stability concerns or critical bugs were reported today.

## 2. Releases

No new releases published. The latest known version remains **2026.5.29**.

## 3. Project Progress

No pull requests were merged or closed today. No features were advanced and no fixes were delivered in this reporting window.

## 4. Community Hot Topics

- **[Issue #995 — Support Skills Symlinks](https://github.com/nullclaw/nullclaw/issues/995)** *(Opened 2026-08-26, 0 comments, 0 reactions)* — Author **ivostoykov** reports that `nullclaw skills list` ignores symlinked skills in the current version. This is the only active issue today and the sole community signal. The request reflects a practical need: users managing skills across multiple machines or environments benefit from symlinks to avoid duplication and stale copies. The reported motivation — reducing synchronization overhead and preventing use of obsolete skills — points to a workflow pain point common among power users who rely on shared or version-controlled skill directories.

## 5. Bugs & Stability

No bugs, crashes, or regressions were reported today. The project appears stable from a user-facing perspective in this window.

## 6. Feature Requests & Roadmap Signals

- **[Issue #995 — Support Skills Symlinks](https://github.com/nullclaw/nullclaw/issues/995)** — The most actionable open request. Symlink support for skills would improve development ergonomics and is a commonly requested capability in modular agent frameworks. Given the clear motivation (deduplication, sync avoidance, stale-skill prevention), this has reasonable potential to appear in a future release if the maintainers prioritize developer tooling improvements.

## 7. User Feedback Summary

The only user feedback today centers on **ivostoykov**'s experience with skill management. The core pain point is the inability to use symbolic links for skills, which creates sync overhead and risks running outdated skill copies. This suggests users are treating NullClaw as part of a larger development workflow — likely integrating it with dotfile managers, git-based configs, or multi-device setups. No satisfaction or dissatisfaction signals beyond this single request are available.

## 8. Backlog Watch

- **[Issue #995 — Support Skills Symlinks](https://github.com/nullclaw/nullclaw/issues/995)** — Opened 2026-08-26 with zero comments and zero reactions. While newly opened, the issue has seen no maintainer response or community engagement yet. It sits in an unattended state and warrants monitoring to see if it gains traction or receives a triage response in the coming days.

---

*Data source: GitHub API via NullClaw project, snapshot taken 2026-08-27.*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-27

## 1. Today's Overview

IronClaw is in a high-velocity release cycle heading toward v1.4.0, with **46 issues** and **50 PRs** updated in the last 24 hours. The team cut the first release candidate (`v1.4.0-rc.1`) yesterday, marking a significant milestone after 81 commits since v1.3.0. Activity is heavily weighted toward performance hardening, sandbox security, and telemetry infrastructure. With 47 PRs merged/closed and 20 issues closed in a single day, the project shows strong maintenance momentum and clear focus on stabilizing the Reborn stack for production deployment.

---

## 2. Releases

### `ironclaw-v1.4.0-rc.1` — 2026-08-26
**[PR #7926](https://github.com/nearai/ironclaw/pull/7926)**

First release candidate for 1.4.0, covering 81 commits since `ironclaw-v1.3.0`.

**Notable additions:**
- **Durable notification inbox**: Publishes authoritative outcomes and actionable gates to a per-user inbox, surfaced by the WebUI notification center, enabling approvals and auth prompts to persist across sessions.

**Breaking changes / migration notes:** None explicitly called out in RC notes. The v1 legacy monolith (`src/`) has been fully retired; all production deploy configs now point to the Reborn stack. Users on pre-1.4 setups should verify channel and extension configs against the new architecture.

---

## 3. Project Progress

**47 PRs merged or closed in the last 24 hours.** Key advances:

| PR | Summary |
|----|---------|
| [#7931](https://github.com/nearai/ironclaw/pull/7931) | **Tenant BI telemetry foundation** — privacy-safe typed contracts, hourly aggregation, six dedicated telemetry tables (libSQL + PostgreSQL), async recorder with batch writes |
| [#7928](https://github.com/nearai/ironclaw/pull/7928) | **Bounded selectable JSON result views** — RFC 6901 pointers, collection limits, UTF-8 paging, self-describing continuation requests for large tool outputs |
| [#7925](https://github.com/nearai/ironclaw/pull/7925) | **Slack subtype fix** — admits `thread_broadcast` subtypes, stops channel mentions depending on `app_mention` |
| [#6817](https://github.com/nearai/ironclaw/pull/6817) | **Filesystem TOCTOU hardening** — closes four containment escapes in `DiskFilesystem` with fd-rooted traversal |
| [#6740](https://github.com/nearai/ironclaw/pull/6740) | **TLS termination seam** for sandbox egress proxy, now that the internal CA dependency has merged |
| [#6157](https://github.com/nearai/ironclaw/pull/6157) | **Terminal UI + service install** for `ironclaw-reborn` (behind `webui-v2-beta` feature flag) |
| [#5970](https://github.com/nearai/ironclaw/pull/5970) | **MCP registration framework skeleton** — owner-scoped store, minted IDs, lifecycle chokepoints |
| [#5918](https://github.com/nearai/ironclaw/pull/5918) | **Hosted MCP server registration & discovery** — user-facing flow on top of the framework |
| [#5917](https://github.com/nearai/ironclaw/pull/5917) | **MCP egress locking** — routes registered-server traffic through host egress, rejects public endpoints |
| [#6096](https://github.com/nearai/ironclaw/pull/6096) | **Concurrent inbound-message serialization** — fixes out-of-order persistence for rapid-fire messages |

**Closed issues (sample):** #4162, #4163 (compaction refactoring), #4796 (LLM date/time awareness), #4425 (`builtin.http` context bomb), #6686 (retired `DockerProcessSandboxBackend`), #3873 (trigger loop), #7392 (omp tool surface experiment).

---

## 4. Community Hot Topics

| Issue | Comments | Focus |
|-------|----------|-------|
| [#7732](https://github.com/nearai/ironclaw/issues/7732) — *Persistent per-user sandbox with iron-proxy* | 10 | Epic-level work to replace per-command Docker containers with persistent sandbox profiles |
| [#7891](https://github.com/nearai/ironclaw/issues/7891) — *Unprojected capability payloads costing 14.3s inference* | 5 | Performance bug: 24 KiB of raw MIME headers injected into prompts unasked, dominating turn latency |
| [#2950](https://github.com/nearai/ironclaw/issues/2950) — *Split provider-safe tool schema cleanup* | 3 | Refactoring LLM schema normalization to decouple provider compatibility from strict optional rewriting |
| [#6986](https://github.com/nearai/ironclaw/issues/6986) — *Cache: keep tool array byte-identical* | 3 | P0 pi-harness item — defer tool promotion to avoid mid-run cache invalidation |
| [#2117](https://github.com/nearai/ironclaw/issues/2117) — *ironclaw-bridge: local file/MCP bridge daemon* | 3 | Cloud-hosted deployments blocked from accessing local files (Obsidian, project dirs) |
| [#6369](https://github.com/nearai/ironclaw/issues/6369) — *Tier B follow-up: gaps from v1 retirement* | 3 | Tracking regressions left by deletion of the `src/` monolith |

**Analysis:** The community is most engaged around **performance** (issues #7891, #6986, #2950 all trace back to inference cost and prompt bloat) and **deployment architecture** (#7732, #2117). The persistent sandbox epic (#7732) is the highest-impact open item, with 10 comments and v1.4.0 roadmap tagging.

---

## 5. Bugs & Stability

| Issue/PR | Severity | Description | Fix Status |
|----------|----------|-------------|------------|
| [#7912](https://github.com/nearai/ironclaw/issues/7912) | **Medium** | Telegram removal returns 503 from WebChat extension endpoint in production | Open — no fix PR yet |
| [#7891](https://github.com/nearai/ironclaw/issues/7891) | **High (perf)** | 19.7s turn latency on two Gmail calls; 19.2s from unprojected 24 KiB MIME headers | Open — relates to #7930 (reference-based tool args) and #7928 (bounded JSON views, merged) |
| [#7925](https://github.com/nearai/ironclaw/pull/7925) | **Medium** | Slack `thread_broadcast` messages silently discarded | **Fixed** — PR merged |
| [#6879](https://github.com/nearai/ironclaw/issues/6879) | **High** | Automation runs hit-or-miss; trigger fires execute as plain interactive chat turns | Closed — structural issue identified, v1.4.0 target |
| [#4425](https://github.com/nearai/ironclaw/issues/4425) | **High** | `builtin.http` is a context bomb — 1.2 MB unstripped responses injected into prompts | Closed — fixed via #7928 (bounded JSON views) and prompt compaction refactors |

**Notable:** The performance bug cluster around unbounded tool output (#7891, #4425) is being addressed systematically through #7928 (merged) and the proposed #7930 (reference-based tool arguments). No crash regressions reported in the last 24h.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Status | Description |
|-------|--------|-------------|
| [#7867](https://github.com/nearai/ironclaw/issues/7867) | Open | **Voice-to-text in WebUI composer** — keyboard-only composer is a parity gap vs. Slack/Telegram |
| [#7934](https://github.com/nearai/ironclaw/issues/7934) | Open | Architecture design for voice-to-text (browser-normalized vs. host-normalized) |
| [#7933](https://github.com/nearai/ironclaw/issues/7933) | Open | Host-normalized voice-to-text architecture proposal |
| [#7932](https://github.com/nearai/ironclaw/issues/7932) | Open | Browser-normalized voice-to-text architecture proposal |
| [#2117](https://github.com/nearai/ironclaw/issues/2117) | Open | **ironclaw-bridge** — local file/MCP bridge daemon for cloud-hosted deployments |
| [#7922](https://github.com/nearai/ironclaw/issues/7922) | Open | **Grammar-constrained `apply_patch`** — eliminate JSON-escaped diffs with typed tool schema |
| [#4625](https://github.com/nearai/ironclaw/issues/4625) | Open | **Slack channel-routed personal and team agents** — Slack as channel-first surface |
| [#7781](https://github.com/nearai/ironclaw/issues/7781) | Open | **Design System Phases 2–3** — DESIGN.md governance + WebUI theme/reskin |

**Prediction for v1.4.0:** The voice-to-text feature (#7867) is unlikely to ship in rc.1 but architecture design issues (#7932–#7934) were opened today, suggesting active planning. The `apply_patch` grammar constraint (#7922) and tenant telemetry (#7931, already merged) are strong candidates. Slack channel routing (#4625) is tagged v1.4.0 roadmap.

---

## 7. User Feedback Summary

**Pain points expressed:**
- **Inference cost from unbounded tool output** is the dominant complaint. Users report turns taking 14–20 seconds purely from MIME headers and HTML bodies being pushed into prompts without filtering (#7891, #4425). The merged #7928 (bounded JSON views) directly addresses this.
- **Cloud-hosted deployments cannot access local files**, blocking real-world workflows like Obsidian vaults and local project directories (#2117). This is described as a "blocker."
- **Slack ingress gaps**: threaded replies with "Also send to channel" were silently dropped (#7925, now fixed).
- **Automation reliability**: trigger-fired runs produce inconsistent results, executing as plain chat turns rather than structured automation (#6879).
- **Voice input parity**: users note every major channel (Slack, Telegram) supports voice except the WebUI composer (#7867).

**Satisfaction signals:** The rapid merge cadence (47 PRs/day), systematic closure of compaction/refactoring issues, and the RC cut suggest the project is in a healthy correction phase after the v1→Reborn transition.

---

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|------------------------|
| [#2950](https://github.com/nearai/ironclaw/issues/2950) | ~4 months | Schema normalization refactor blocks cleaner provider integration; stales PRs accumulate |
| [#6986](https://github.com/nearai/ironclaw/issues/6986) | ~2.5 months | P0 pi-harness item — mid-run tool promotion breaks cache identity, impacts perf work across the stack |
| [#2117](https://github.com/nearai/ironclaw/issues/2117) | ~4.5 months | Blocking cloud-hosted use cases; no visible PR in progress |
| [#7732](https://github.com/nearai/ironclaw/issues/7732) | ~9 days | Epic-level; 10 comments, v1.4.0 roadmap. Persistent sandbox is foundational for security posture |
| [#7891](https://github.com/nearai/ironclaw/issues/7891) | 2 days | Active perf regression; fix depends on #7930 (also open today) — both need traction |
| [#7912](https://github.com/nearai/ironclaw/issues/7912) | 1 day | Production bug (503 on Telegram removal) with no fix PR yet |

**Maintainer attention needed:** Issues #6986 and #2950 have been open for months and are prerequisites for the broader perf work the team is driving. #2117 has no visible PR and blocks a clear customer segment. #7891 is a fresh, high-severity perf bug that should be prioritized alongside the already-merged #7928.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-27

## 1. Today's Overview

LobsterAI shows healthy development velocity today with 11 PRs updated and only 1 active issue, indicating a strong merge bias and efficient review cycle. The project released version **2026.8.26** (PR #2549), suggesting a regular release cadence. Activity is concentrated on renderer-side UX improvements, analytics instrumentation, and cloud library features. No new issues were opened today, and there are zero new releases — the most recent release landed yesterday. Overall project health is **strong**, with consistent contributor engagement from a small core team (liuzhq1986, liugang519, fisherdaddy).

## 2. Releases

**v2026.8.26** — Merged via PR #2549 ([link](https://github.com/netease-youdao/LobsterAI/pull/2549))
- Release PR created and closed on 2026-08-26 by liuzhq1986.
- No detailed changelog was provided in the PR summary; further notes would need to be pulled from release notes or commit history.

## 3. Project Progress

**Merged / Closed PRs today:**

| PR | Area | Summary |
|----|------|---------|
| [#2558](https://github.com/netease-youdao/LobsterAI/pull/2558) | renderer, auth | Added rainbow border/glow animation to the sidebar login CTA; preserves light & dark theme contrast; adds renderer logs for login attempts/failures. |
| [#2557](https://github.com/netease-youdao/LobsterAI/pull/2557) | renderer, docs | Bug fixes (summary not detailed). |
| [#2556](https://github.com/netease-youdao/LobsterAI/pull/2556) | renderer, docs | Logging / rlog updates (summary not detailed). |
| [#2555](https://github.com/netease-youdao/LobsterAI/pull/2555) | renderer, artifacts | Major analytics overhaul: added share/deploy/link-copy/permission events, correlated exposure with outcomes, added async deploy final-state tracking with reliable upload queue, unified account/subscription/env metadata, enriched library refresh/favorite/popup events, added automated tests and server-side integration docs. |
| [#2553](https://github.com/netease-youdao/LobsterAI/pull/2553) | renderer, build, Windows | Fixed Zhipu AI provider icon in dark mode. |
| [#2552](https://github.com/netease-youdao/LobsterAI/pull/2552) | renderer, cowork | Guide/recharge flow improvements (summary not detailed). |
| [#2550](https://github.com/netease-youdao/LobsterAI/pull/2550) | renderer, docs, main, artifacts | Added permanent deletion of cloud-shared files: new API + IPC + client types; delete only stopped shares with filename confirmation; syncs cloud list, status count, and local favorites on delete; handles status conflicts, server incompatibility, and post-delete data calibration; fixed duplicate local service deploy requests on account switch / popup close; optimized share time updates, visit-ranking tooltips, and accessibility. |
| [#2549](https://github.com/netease-youdao/LobsterAI/pull/2549) | renderer, build, docs, Windows | Release v2026.8.26. |
| [#2548](https://github.com/netease-youdao/LobsterAI/pull/2548) | renderer | Adjusted settings panel width. |
| [#2547](https://github.com/netease-youdao/LobsterAI/pull/2547) | renderer | Fixed login guide flow. |

**Key themes:** Analytics instrumentation (#2555) and cloud library lifecycle management (#2550) are the most substantial feature advances. UI polish (rainbow CTA animation, settings width, Zhipu dark-mode icon) accounts for the majority of remaining PRs.

## 4. Community Hot Topics

- **Issue #2554 — Synthorai as built-in provider** ([link](https://github.com/netease-youdao/LobsterAI/issues/2554))
  - *Author:* cuihuan · *Created:* 2026-08-26 · *Comments:* 1 · *Reactions:* 0
  - **Why it matters:** Users want gateway providers that unify multiple model backends (OpenAI / Anthropic protocols under one base URL) to be first-class citizens. The current Custom slot forces manual model ID entry, lacks `switchableBaseUrls`, and has no default icon/URL — creating friction for newcomers. This signal points to a broader demand: **LobsterAI should formalize "aggregator gateway" providers** (similar to how OpenRouter is already内置) rather than treating them as edge-case custom configurations.
  - **Likely next step:** If the maintainer route, expect a new built-in provider entry with auto-discovered model lists and dual-protocol base URL switching.

- **PR #2555 — Analytics pipeline** (10 comments implied by complexity) ([link](https://github.com/netease-youdao/LobsterAI/pull/2555))
  - Reflects active investment in product analytics, suggesting the team is preparing data-driven feature decisions or monitization tracking.

## 5. Bugs & Stability

| Severity | Item | Details |
|----------|------|---------|
| **Medium** | [#2553](https://github.com/netease-youdao/LobsterAI/pull/2553) — Zhipu icon broken in dark mode | Visual regression on Windows; **fixed and merged**. |
| **Medium** | [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) — App update does not preserve ready state | **Still open**; could cause UX disruption during app restart after an update. Worth monitoring. |
| **Low** | Duplicate local service deploy requests on account switch / popup close | Bug referenced in PR #2550 summary; **fixed as part of #2550**. |

No crashes or critical regressions reported today.

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Interpretation |
|--------|--------|----------------|
| Synthorai as built-in provider | Issue #2554 | High-priority community ask; aligns with existing OpenRouter pattern. Likely candidate for next minor release if maintainer agrees. |
| Permanent cloud-share deletion | PR #2550 (merged) | Already shipped — confirms roadmap direction toward full lifecycle management of shared artifacts. |
| Enhanced analytics telemetry | PR #2555 (merged) | Suggests upcoming data dashboards or A/B testing capability. |
| Login UX polish (rainbow CTA, guide fixes) | PRs #2558, #2547 | Continued investment in onboarding conversion. |

**Prediction for next version:** If #2554 is accepted, the next release will add at least one new built-in provider type with dual-protocol support. The analytics work in #2555 may also surface a lightweight analytics dashboard in the settings panel.

## 7. User Feedback Summary

- **Pain point — Custom providers are friction-heavy:** Issue #2554 highlights that gateway-style providers (one key → multiple models) are a growing use case but are treated as second-class citizens. Users must manually fill model IDs, lack icon/URL defaults, and cannot switch between OpenAI/Anthropic base URLs in one click.
- **Pain point — Dark-mode icon regressions:** The Zhipu icon fix (#2553) indicates provider icon assets are not consistently themed across light/dark modes — a recurring maintenance burden.
- **Positive — Cloud library controls:** The permanent-delete feature (#2550) with filename confirmation and state-sync addresses a real privacy/compliance need for users who share files via LobsterAI.
- **Positive — Analytics transparency:** The team's investment in instrumentation (#2555) suggests responsiveness to operational needs, though no user-visible analytics feature is mentioned yet.

## 8. Backlog Watch

| Item | Age | Risk | Note |
|------|-----|------|------|
| [#2551](https://github.com/netease-youdao/LobsterAI/pull/2551) — App update preserves ready state | Open since 2026-08-26 (1 day) | Low–Medium | State loss after update is a UX regression; needs maintainer review. |
| [#2554](https://github.com/netease-youdao/LobsterAI/issues/2554) — Synthorai built-in provider | Open since 2026-08-26 (1 day) | Low | Feature request; no urgency but high community relevance. |
| PR #2557, #2556, #2552, #2547 — Undetailed summaries | Merged | None | Summaries left blank; reviewers should ensure changelog coverage. |

---

*Generated from LobsterAI GitHub data via LobsterAI API · 2026-08-27*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-27

## 1. Today's Overview

Moltis saw moderate activity on 2026-08-26, with one issue closed and two pull requests merged, along with a new release (20260826.01). All resolved items center on model preference handling and MCP OAuth registration, suggesting the project is actively stabilizing its provider and integration layers. No open issues or PRs remain from today's batch, and there are no blocking bugs in flight. The release of a new patch version signals that fixes are being shipped promptly, indicating healthy project maintenance.

## 2. Releases

**20260826.01** (2026-08-26)

This release bundles two merged fixes:
- **PR #1104** — Allows replacing de-preferring models (provider model preference management).
- **PR #1244** — Fixes Fastmail MCP OAuth scope registration, ensuring protected-resource scopes are preferred over the authorization server's broader catalog during discovery.

No breaking changes or migration notes were indicated. This is a standard patch-level release.

## 3. Project Progress

- **PR #1104** [MERGED] — *fix(providers): allow replacing preferred models* — The preferred-model dialog now preselects saved provider model preferences, and saving a new preference replaces the previous selection (including clearing all preferences with an empty selection). Backend and Playwright regression coverage was added.
- **PR #1244** [MERGED] — *Fix Fastmail MCP OAuth scope registration* — MCP OAuth discovery now prefers protected-resource scopes over broader authorization server scope catalogs. Dynamic client registration (RFC 7591) now includes selected scopes, with a Fastmail-shaped regression test covering resource discovery, registration, and localhost redirect handling.

## 4. Community Hot Topics

- **Issue #1094** — [Bug: De-Preferring Models](https://github.com/moltis-org/moltis/issues/1094) — Filed 2026-06-03, resolved 2026-08-26 via PR #1104. While the issue had zero comments and no reactions, its resolution indicates a meaningful user need: the ability to de-prioritize or remove preferred models per provider. This aligns with the PR's feature set, confirming that model flexibility is a top user priority.
- **PR #1244** — [Fix Fastmail MCP OAuth scope registration](https://github.com/moltis-org/moltis/pull/1244) — Filed and merged within 48 hours (2026-08-25 to 2026-08-26). The rapid turnaround on an OAuth-scoped MCP issue suggests growing user adoption of MCP integrations, particularly with email providers like Fastmail.

## 5. Bugs & Stability

| Severity | Issue | Status | Fix PR |
|----------|-------|--------|--------|
| Medium | [#1094: De-Preferring Models](https://github.com/moltis-org/moltis/issues/1094) — Bug in model preference management | ✅ Closed | [PR #1104](https://github.com/moltis-org/moltis/pull/1104) |
| Low | [#1244: Fastmail MCP OAuth scope registration](https://github.com/moltis-org/moltis/pull/1244) — Scope mismatch during OAuth discovery | ✅ Closed | Self-contained fix |

No open bugs or crash reports were recorded in the last 24 hours. No regressions were flagged alongside the merged fixes.

## 6. Feature Requests & Roadmap Signals

No new feature-request issues were filed or closed today. However, the resolution of **Issue #1094 / PR #1104** — which added full replacement/clearing of preferred models — suggests the team is iterating on provider-model preference UX. Future releases may expand this to per-provider model prioritization or ranking, given the foundational work in this patch.

## 7. User Feedback Summary

User pain points addressed today center on **model preference management** and **MCP OAuth configuration**. The de-preferring-models bug indicates users expected full control over their preferred models per provider and encountered a blocker when trying to remove or replace them. The Fastmail MCP OAuth fix suggests users are integrating diverse MCP-compatible services and running into scope-registration edge cases. Both fixes landed with regression tests, indicating responsiveness to real-world usage.

## 8. Backlog Watch

With zero open issues and both PRs closed today, the immediate backlog appears light. However, the long-standing nature of Issue #1094 (open for ~2 months before resolution) warrants monitoring — if similar preference-related issues accumulate in the queue, the team may want to proactively review the model-management UX before more users encounter the same blocker. No PRs are currently pending maintainer review.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-27

## 1. Today's Overview

CoPaw (agentscope-ai/CoPaw) is exhibiting **high velocity** with 26 issues and 39 PRs updated in the past 24 hours, alongside the release of **v2.2.0-beta.1**. The project balance tilts active (14 open issues, 20 open PRs) but with strong closure momentum (12 issues and 19 PRs resolved). Key focus areas today include prompt-cache observability, installer reliability on Windows, console UX polish, and test coverage expansion (495 new integration cases). Community engagement is notably strong around the upcoming multi-tenant Hub edition and long-standing UX pain points around agent continuity and mobile experience.

## 2. Releases

### v2.2.0-beta.1
**Release page:** https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.2.0-beta.1

**Changes:**
- **Docs:** Updated scroll context manager blog ([#7300](https://github.com/agentscope-ai/QwenPaw/pull/7300))
- **Fix:** Sanitize DashScope tool schemas for strict models ([#7284](https://github.com/agentscope-ai/QwenPaw/pull/7284))
- **Test:** Targeted integration test additions

**Migration notes:** None documented. Users should validate DashScope provider configurations if using strict model schemas.

## 3. Project Progress

**Merged/Closed PRs today:**
- [#7338](https://github.com/agentscope-ai/QwenPaw/pull/7338) — chore: bump version to 2.2.0b2
- [#7332](https://github.com/agentscope-ai/QwenPaw/pull/7332) — Stabilize timing-sensitive tests (TUI transport, kill-deadline extensions)
- [#7323](https://github.com/agentscope-ai/QwenPaw/pull/7323) — Fix NSIS uninstaller process blocker detection
- [#7194](https://github.com/agentscope-ai/QwenPaw/pull/7194) — Make workspace startup/reload cleanup cancellation-safe
- [#7327](https://github.com/agentscope-ai/QwenPaw/pull/7327) — Boost console E2E coverage (+23 cases, ~6-7pp gain)
- [#534](https://github.com/agentscope-ai/QwenPaw/pull/534) — Add French (fr-CA) language support (docs, README, web console)
- [#401](https://github.com/agentscope-ai/QwenPaw/pull/401) — Update README with clear run instructions

**Notable open PRs advancing features:**
- [#7346](https://github.com/agentscope-ai/QwenPaw/pull/7346) — Perf: stabilize prompt cache prefixes
- [#7342](https://github.com/agentscope-ai/QwenPaw/pull/7342) — Feat: prompt cache observability (Stage 1)
- [#7340](https://github.com/agentscope-ai/QwenPaw/pull/7340) — Feat: chat scroll lock during streaming
- [#7344](https://github.com/agentscope-ai/QwenPaw/pull/7344) — Feat: game-dev file language support in console
- [#7336](https://github.com/agentscope-ai/QwenPaw/pull/7336) — Fix: NSIS uninstall process blocker handling (follow-up to #7323)
- [#7341](https://github.com/agentscope-ai/QwenPaw/pull/7341) — Integration test coverage sprint batch 5 (495 cases)
- [#7334](https://github.com/agentscope-ai/QwenPaw/pull/7334) — Fix: mobile composer controls
- [#7331](https://github.com/agentscope-ai/QwenPaw/pull/7331) — Fix: bound oversized single-line tool results in context

## 4. Community Hot Topics

1. **[QwenPaw Hub multi-tenant edition roadmap](https://github.com/agentscope-ai/QwenPaw/issues/7318)** — 7 comments. Community actively shaping what features QwenPaw Hub should prioritize. Underlying need: enterprises want team deployment with admin-managed skills and per-user policies, as echoed in related issues [#6335](https://github.com/agentscope-ai/QwenPaw/issues/6335), [#5780](https://github.com/agentscope-ai/QwenPaw/issues/5780), [#4702](https://github.com/agentscope-ai/QwenPaw/issues/4702).

2. **[Prompt cache hit rate observability](https://github.com/agentscope-ai/QwenPaw/issues/7335)** — 2 comments. User reported 81.68% hit rate vs. OpenCode's 96.02%, with direct cost impact. PR [#7342](https://github.com/agentscope-ai/QwenPaw/pull/7342) directly addresses this with Stage 1 observability.

3. **[Tool card stuck after stop](https://github.com/agentscope-ai/QwenPaw/issues/7321)** — 1 comment (today), PR [#7345](https://github.com/agentscope-ai/QwenPaw/pull/7345) in progress. Users frustrated by tool cards showing perpetual "executing…" state after cancellation.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **High** | [#7206](https://github.com/agentscope-ai/QwenPaw/issues/7206) | **Regression:** `/compact` fails with Pydantic ValidationError when `compact_threshold_ratio == 0.9` in v2.1.1-beta.1 | — |
| **High** | [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) | Desktop/Docker ship OpenSSL 3.0.x TLS stack causing carrier DPI handshake resets | — |
| **Medium** | [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | Agent stops mid-task after planning without visual cue; requires manual "continue" | — |
| **Medium** | [#7312](https://github.com/agentscope-ai/QwenPaw/issues/7312) | Windows `execute_shell_command` hangs due to inherited stdin pipe (missing `stdin=DEVNULL`) | — |
| **Medium** | [#7193](https://github.com/agentscope-ai/QwenPaw/issues/7193) | Web版 agent searches cross-session memory incorrectly after pause/resume | — |
| **Low** | [#7324](https://github.com/agentscope-ai/QwenPaw/issues/7324) | Scheduled task success notifications missing from inbox (intermittent) | ✅ Closed |
| **Low** | [#7258](https://github.com/agentscope-ai/QwenPaw/issues/7258) | WeChat channel "hide thinking process" setting ineffective | ✅ Closed |

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood for v2.2.0 |
|---------|-------|----------------------|
| **Prompt cache observability & optimization** | [#7335](https://github.com/agentscope-ai/QwenPaw/issues/7335) | ✅ Active PR [#7342](https://github.com/agentscope-ai/QwenPaw/pull/7342) |
| **Chat scroll lock during streaming** | [#7339](https://github.com/agentscope-ai/QwenPaw/issues/7339) | ✅ Active PR [#7340](https://github.com/agentscope-ai/QwenPaw/pull/7340) |
| **Multi-tenant Hub edition** | [#7318](https://github.com/agentscope-ai/QwenPaw/issues/7318) | Planned for 2.2.0 (announced) |
| **Workspace-scoped skill preload** | — | ✅ Active PR [#7183](https://github.com/agentscope-ai/QwenPaw/pull/7183) |
| **OpenViking long-term memory backend** | [#7252](https://github.com/agentscope-ai/QwenPaw/issues/7252) | Under discussion, not yet in scope |
| **Mobile composer improvements** | — | ✅ Active PR [#7334](https://github.com/agentscope-ai/QwenPaw/pull/7334) |
| **Game-dev file syntax highlighting** | — | ✅ Active PR [#7344](https://github.com/agentscope-ai/QwenPaw/pull/7344) |
| **DingTalk group context mode** | [#7158](https://github.com/agentscope-ai/QwenPaw/issues/7158) | ✅ Closed — likely in upcoming release |
| **Model selection UI:弹窗选单而非输入** | [#7279](https://github.com/agentscope-ai/QwenPaw/issues/7279) | ✅ Closed — feature accepted |

## 7. User Feedback Summary

**Pain points:**
- **Agent continuity breaks** ([#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921)): Users report agents stopping after planning without visual feedback, requiring manual "继续" — a recurring UX frustration across Windows and web clients.
- **Tool result bloat** ([#7316](https://github.com/agentscope-ai/QwenPaw/issues/7316)): React loop tool outputs consume excessive context; users request AI-driven result filtering/simplification.
- **Windows installer confusion** ([#7188](https://github.com/agentscope-ai/QwenPaw/issues/7188)): "Delete local app cache" option lacks explanation during uninstall.
- **Finished background tasks persist** ([#7280](https://github.com/agentscope-ai/QwenPaw/issues/7280)): No auto-clear for completed background tasks; users want a toggle.
- **Mobile UX** ([#7334](https://github.com/agentscope-ai/QwenPaw/pull/7334)): Composer controls and layout need mobile optimization — confirmed active work.
- **Scheduled task notification gaps** ([#7324](https://github.com/agentscope-ai/QwenPaw/issues/7324)): Intermittent missing push notifications for successful cron runs.

**Satisfaction signals:** Positive reception of the Hub multi-tenant announcement, prompt cache observability work, and mobile improvements.

## 8. Backlog Watch

| Issue | Age | Priority | Note |
|-------|-----|----------|------|
| [#7298](https://github.com/agentscope-ai/QwenPaw/issues/7298) — OpenSSL 3.0.x TLS carrier DPI issue | 2 days | High | Affects desktop & Docker; no fix PR yet |
| [#7206](https://github.com/agentscope-ai/QwenPaw/issues/7206) — `/compact` regression | 6 days | High | Confirmed regression from v2.1.0; blocks context management |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) — Agent stops without cue | 15 days | High | 11 comments; core UX issue affecting multi-step workflows |
| [#7312](https://github.com/agentscope-ai/QwenPaw/issues/7312) — Windows stdin pipe hang | 1 day | Medium | Reproduced on Python 3.12 & 3.14; needs `stdin=DEVNULL` fix |
| [#7193](https://github.com/agentscope-ai/QwenPaw/issues/7193) — Cross-session memory search | 6 days | Medium | Web版 only; memory isolation bug |
| [#7252](https://github.com/agentscope-ai/QwenPaw/issues/7252) — OpenViking memory backend | 3 days | Low | Architecture discussion; no PR yet |

---

**Project health assessment:** 🟢 **Strong.** High PR/issue throughput, active bug resolution, and clear roadmap execution on v2.2.0-beta. The multi-tenant Hub direction and prompt-cache observability indicate mature product thinking. Two high-severity bugs (compact regression, TLS) and the agent-stops-without-cue issue warrant maintainer attention in the next cycle.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-27

## 1. Today's Overview
ZeroClaw exhibits high development velocity with **37 issues** and **50 pull requests** updated in the last 24 hours. Ten issues were closed and six PRs merged, reflecting steady progress without a new release. Community activity is concentrated on **security hardening, runtime reliability, and feature‑complete gateways** (Telegram, Discord, Signal). The v0.9.0 milestone tracker (#7432) remains active, and the project health is strong: open issues outnumber closed, but a significant portion of PRs are still awaiting review or are blocked on external factors.

## 2. Releases
No new releases were published in the past 24 hours. The upcoming **v0.9.0** release is tracked via issue [#7432](https://github.com/zeroclaw-labs/zeroclaw/issues/7432), which aggregates auth, security, gateway, and breaking‑change work.

## 3. Project Progress
**Merged/Closed PRs (today):**
- [#9748](https://github.com/zeroclaw-labs/zeroclaw/pull/9748) – Fixed stale provider refreshes that could mutate replacement sessions.

**Features advanced (open/stacked):**
- [#9997](https://github.com/zeroclaw-labs/zeroclaw/pull/9997) – Telegram secure model picker (status: **blocked**).
- [#9971](https://github.com/zeroclaw-labs/zeroclaw/pull/9971) – Discord role‑based authorization (status: **blocked**).
- [#8337](https://github.com/zeroclaw-labs/zeroclaw/pull/8337) – Herdr agent observability integration (status: **blocked**).
- [#10142](https://github.com/zeroclaw-labs/zeroclaw/pull/10142) – ZeroRelay mTLS secure transport.
- [#10381](https://github.com/zeroclaw-labs/zeroclaw/pull/10381) – Security fix: resolve host launchers before workspace cwd.
- [#9678](https://github.com/zeroclaw-labs/zeroclaw/pull/9678) – Harden Git shell policy arguments.
- [#10075](https://github.com/zeroclaw-labs/zeroclaw/pull/10075) – Thread live config through gateway chat to tool registry (depends on [#10072](https://github.com/zeroclaw-labs/zeroclaw/pull/10072)).

**ZeroCode / CLI improvements:**
- [#10393](https://github.com/zeroclaw-labs/zeroclaw/pull/10393) – Refresh inactive Chat without blocking navigation.
- [#10380](https://github.com/zeroclaw-labs/zeroclaw/pull/10380) – Restore persisted ACP transcripts.
- [#10374](https://github.com/zeroclaw-labs/zeroclaw/pull/10374) – Keep input responsive during daemon reconnect.
- [#10386](https://github.com/zeroclaw-labs/zeroclaw/pull/10386) – Make transcript URLs clickable.

**CI & testing:**
- [#10350](https://github.com/zeroclaw-labs/zeroclaw/pull/10350) – Measure affected Windows

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*