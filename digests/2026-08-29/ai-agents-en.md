# OpenClaw Ecosystem Digest 2026-08-29

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-29 06:43 UTC

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



# OpenClaw Project Digest — 2026-08-29

---

## 1. Today's Overview

OpenClaw continues to operate at **very high velocity**, with 500 issues and 500 PRs touched in the last 24 hours. The project is in an active stabilization phase: 92 issues were closed and 190 PRs merged/closed today, while 408 issues and 310 PRs remain open. A new beta release, **v2026.9.1-beta.1**, landed today with gateway reliability improvements. The dominant theme across recent activity is **gateway resilience, session-lane stability, and channel reliability** — the team is clearly prioritizing production-grade robustness over new features.

---

## 2. Releases

### v2026.9.1-beta.1 — `openclaw 2026.9.1-beta.1`

**Highlights:**
- **Gateway restart recovery** (#130491): Preserves admitted turns across repeated Gateway restarts so restart-safe runs continue through each checkpoint and deliver their final response. *(Thanks @jalehman)*
- **Gateway config-write reliability**: Improvements to committed config write paths (details truncated in source data).

**Migration notes:** None explicitly stated. As a beta release, operators running production gateways should test in staging before upgrading.

🔗 [GitHub Release](https://github.com/openclaw/openclaw/releases)

---

## 3. Project Progress

**Closed/Merged today (190 PRs, 92 issues):**

- **#132338** — Fixed Full Release Validation (FRV) reruns to write-once, preventing duplicate child/parent reruns when GitHub accepted the first mutation but the client observed a transition delay.
- **#132425** — Separated gateway shutdown policy from process scheduling in tests, resolving false startup/shutdown failure reports on loaded macOS hosts.
- **#128995** — Exposed full session actions (pin, mark unread, set icon, copy session ID, move to group) from the chat header menu, closing a UX gap vs. the sidebar.
- **#128223** — Fixed CLI alias resolution to read from the write snapshot, closing #127618.
- **#123535** — Prevented session catalog refresh storms in the Web UI sidebar caused by browser focus changes and startup requests.
- **#116489** — Added security acknowledgement requirement for `install` policy warnings, letting operators review suspicious plugin/skill installs before continuing.
- **#87711** (closed) — Resolved empty assistant delivery (footer-only, "— out" usage) on first turn after `/new` on Telegram-routed topic lanes.
- **#87938** (closed) — Fixed Feishu DM session rebuilds after gateway restart caused by duplicate keys and maintenance pruning.
- **#88856** (closed) — Addressed silent subagent drops (~3.8% historical rate) where `/sessions_spawn` tool_use emitted with no matching `tool_result`.
- **#88230** (closed) — Fixed `openclaw message send` CLI hanging indefinitely after successful delivery (was stuck in `epoll_wait`).

**Notable open PRs awaiting author/maintainer review:**
- **#131901** — Isolates Codex sessions per conversation to prevent cross-conversation interference.
- **#132186** — Fixes Gateway startup under load (addresses workspace skill indexing and Control UI reconnection bootstrap bloat).
- **#119516** — Recovers the managed Gateway after a failed CLI update.
- **#119052** — Keeps the Windows Gateway running after the foreground window closes.

---

## 4. Community Hot Topics

**Most-discussed issues (by comment count):**

| # | Title | Comments | Rating | Link |
|---|-------|----------|--------|------|
| #91588 | **Critical: Gateway Memory Leak — RSS grows from 350MB to 15.5GB** | 23 | 🐚 platinum hermit | [Issue](https://github.com/openclaw/openclaw/issues/91588) |
| #48788 | **feat: centralized filename encoding utility for multi-encoding Content-Disposition** | 20 | 🌊 off-meta tidepool | [Issue](https://github.com/openclaw/openclaw/issues/48788) |
| #84516 | **Codex app-server: long agent replies silently truncated at ~1000-1100 chars** | 13 | 🦪 silver shellfish | [Issue](https://github.com/openclaw/openclaw/issues/84516) |
| #117609 | **Transient LLM/socket errors retried for channels but not embedded-assistant stage** | 11 | 🦞 diamond lobster | [Issue](https://github.com/openclaw/openclaw/issues/117609) |
| #95610 | **Prompt-cache prefix churn on OpenAI models defeats automatic prefix caching** | 10 | 🦞 diamond lobster | [Issue](https://github.com/openclaw/openclaw/issues/95610) |
| #87756 | **Regression: prompt-launched Lobster workflow hangs on nested /tools/invoke** | 10 | 🐚 platinum hermit | [Issue](https://github.com/openclaw/openclaw/issues/87756) |
| #87711 | **Empty assistant delivery on first turn after /new on Telegram** | 10 | 🐚 platinum hermit | [Issue](https://github.com/openclaw/openclaw/issues/87711) ✅ closed |
| #97616 | **OpenClaw leaks unreaped hook/tool child processes → zombie accumulation** | 9 | 🦐 gold shrimp | [Issue](https://github.com/openclaw/openclaw/issues/97616) |
| #50291 | **Plugin Hooks: Missing trace context for distributed tracing** | 9 | 🦞 diamond lobster | [Issue](https://github.com/openclaw/openclaw/issues/50291) |
| #71058 | **Support for multiple Azure/Teams bots on a single Gateway** | 9 | 🌊 off-meta tidepool | [Issue](https://github.com/openclaw/openclaw/issues/71058) |

**Analysis:** The community is deeply focused on **production reliability**. The top issue (#91588) is a critical memory leak causing OOM crashes — a showstopper for long-running gateways. Multiple high-comment issues cluster around **session/state correctness** (#84516, #97616, #54488, #53008), **channel-specific bugs** (Telegram, Feishu, Discord), and **observability gaps** (#50291). The feature request for centralized filename encoding (#48788) signals growing internationalization needs beyond the Feishu-specific fix in #48578.

---

## 5. Bugs & Stability

**Critical / P0:**

| # | Description | Status | Fix PR | Link |
|---|-------------|--------|--------|------|
| #91588 | **Gateway memory leak** — RSS grows from 350MB to 15.5GB over 2-3 days, triggering repeated OOM kills and `launchd-handoff` restart cycles | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/91588) |
| #97616 | **Child process leak** — unreaped `openclaw-hooks`, `bash`, `codex` zombies accumulate, causing runtime degradation | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/97616) |
| #112259 | **Silently dropped inbound turns** — zero-payload dispatch with no retry, dead-letter, or user-visible failure | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/112259) |

**P1 — Regressions & High-Impact Bugs:**

| # | Description | Status | Fix PR | Link |
|---|-------------|--------|--------|------|
| #84516 | **Codex app-server truncates long replies** at ~1000-1100 chars (`aborted=false`, `stopReason=null`) | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/84516) |
| #117609 | **No retry for transient LLM/socket errors at embedded-assistant stage** — long turns die whole while trivial turns seconds later succeed | Open | Linked PR open | [Issue](https://github.com/openclaw/openclaw/issues/117609) |
| #87756 | **Regression: prompt-launched Lobster workflow hangs** on nested `/tools/invoke` (curl-launched works) | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/87756) |
| #54488 | **Session lane starvation** — followup drain monopolizes session lane, blocking inbound dispatch for 20-30 min | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/54488) |
| #53008 | **Memory compaction blocks main processing lane** — 10+ minute freeze, all inbound messages queue | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/53008) |
| #82662 | **Isolated cron `agentTurn` fails** with "setup timed out before runner start" — all fallback models exhausted | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/82662) |
| #91892 | **Cron jobs stall during AI model calls** — `model_call:stream_progress` never completes | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/91892) |
| #101445 | **Embedded Ollama reports `payloads=0 tools=0`** for certain prompts despite valid tool_calls in response | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/101445) |
| #124284 | **Subagent spawn fails with vLLM openai-completions + thinking** — malformed XML tool calls since v2026.8.1-beta.2 | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/124284) |
| #126906 | **Denying write tool silently disables memory persistence** — agent reports success anyway | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/126906) |
| #55694 | **Agent tool-call failure loop** — infinite retry with repeated message spam (Feishu) | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/55694) |
| #42803 | **Regression: Feishu text commands (`/stop`, `/new`, `/status`) no longer bypass queue** during active agent run | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/42803) |
| #105528 | **exec/read tools silently return empty output on Windows** (v2026.6.x regression) | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/105528) |
| #115642 | **Billing cooldown outlives the outage** on subscription auth — no probe-based recovery | Open | None yet | [Issue](https://github.com/openclaw/openclaw/issues/115642) |

**P2 — Notable Bugs:**

| # | Description | Status | Link |
|---|-------------|--------|------|
| #95610 | Prompt-cache prefix churn on OpenAI models defeats automatic prefix caching | Open | [Issue](https://github.com/openclaw/openclaw/issues/95610) |
| #120735 | Telegram inbound stickers arrive as raw file refs, not staged to disk | Open | [Issue](https://github.com/openclaw/openclaw/issues/120735) |
| #83416 | `openclaw_image` vision times out after 60s on valid Talk JPEG | Open | [Issue](https://github.com/openclaw/openclaw/issues/83416) |
| #86342 | **Race: `MissingAgentHarnessError`** during plugin cache cycle (28 incident windows in 72h) | Closed | [Issue](https://github.com/openclaw/openclaw/issues/86342) ✅ |
| #78865 | **Tool call circuit breaker needed** — LLMs blindly retry forever without one | Open | [Issue](https://github.com/openclaw/openclaw/issues/78865) |
| #101554 | Oversized HTTP/SSE MCP tool-list responses block Gateway before catalog limits apply | Open | [Issue](https://github.com/openclaw/openclaw/issues/101554) |
| #69242 | `exec` tool on Linux intermittently SIGKILLs broad find/grep commands without OOM | Open | [Issue](https://github.com/openclaw/openclaw/issues/69242) |
| #87136 | Compaction absolute token thresholds break when switching models with different context windows | Open | [Issue](https://github.com/openclaw/openclaw/issues/87136) |
| #89257 | `openclaw backup create --verify` exits 13, leaves corrupt .tmp archive | Open | [Issue](https://github.com/openclaw/openclaw/issues/89257) |

---

## 6. Feature Requests & Roadmap Signals

| # | Title | Comments | Link |
|---|-------|----------|------|
| #48788 | **Centralized filename encoding utility** for multi-encoding Content-Disposition (Shift-JIS, EUC-KR, GB18030) | 20 | [Issue](https://github.com/openclaw/openclaw/issues/48788) |
| #71058 | **Multiple Azure/Teams bots** on a single Gateway | 9 | [Issue](https://github.com/openclaw/openclaw/issues/71058) |
| #63990 | **Multi-index embedding memory** with model-aware failover (no mixed vector spaces) | 7 | [Issue](https://github.com/openclaw/openclaw/issues/63990) |
| #88154 | **Slack Modal Support** for interactive workflows | 7 | [Issue](https://github.com/openclaw/openclaw/issues/88154) |
| #53654 | **Discord messageUpdate/messageDelete** events for edit-to-reprocess and delete-to-cancel | 6 | [Issue](https://github.com/openclaw/openclaw/issues/53654) |
| #54373 | **[RFC] Context Provenance** — add source/volatility metadata to injected context segments | 6 | [Issue](https://github.com/openclaw/openclaw/issues/54373) |
| #51184 | **Surface cron job name/session label** in `/status` and statusline | 5 | [Issue](https://github.com/openclaw/openclaw/issues/51

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — Personal AI Agent Open-Source Ecosystem
**Date:** 2026-08-29

---

## 1. Ecosystem Overview

The open-source personal AI assistant and agent landscape is polarized between high-velocity gateway-scale platforms and focused, component-level tools. OpenClaw dominates by volume, operating at ~10× the issue/PR throughput of any peer while simultaneously shipping beta releases and stabilizing production reliability. A second tier—ZeroClaw, CoPaw, and IronClaw—shows robust multi-project momentum with active RFC processes and recent minor releases. Meanwhile, specialized agents (NanoBot, Hermes Agent, NanoClaw) pursue niche strengths in CLI ergonomics, multi-provider compatibility, and security hardening. The ecosystem is clearly migrating from "agent that can do things" toward "agent that is reliable, auditable, and cost-efficient at scale."

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Releases | Health Score |
|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | v2026.9.1-beta.1 (today) | 🟢 Very High |
| **ZeroClaw** | 37 | 50 | None | 🟢 High |
| **Hermes Agent** | 50 | 50 | None | 🟢 High |
| **CoPaw** | 39 | 27 | v2.2.0 beta (today) | 🟢 High |
| **IronClaw** | 14 | 28 | v1.4.0 (Aug 27) | 🟢 Active |
| **NanoClaw** | 3 | 50 | None | 🟡 Moderate |
| **NanoBot** | 8 | 17 | None | 🟡 Moderate |
| **LobsterAI** | 5 | 8 | 2026.8.28 (yesterday) | 🟡 Moderate |
| **PicoClaw** | 1 | 1 | None | 🟡 Low |
| **Moltis** | 1 | 0 | None | 🔴 Low |
| **NullClaw** | 0 | 0 | None | ⚪ Inactive |
| **ZeptoClaw** | 0 | 0 | None | ⚪ Inactive |

*Health Score based on issue/PR throughput, release cadence, and PR closure rate observed in the digest window.*

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale:** 500 issues + 500 PRs in 24h dwarfs every other project (next closest: Hermes and NanoClaw at ~50 each). This suggests OpenClaw serves as the reference gateway/platform others integrate with.
- **Integration breadth:** Active channel support for Telegram, Feishu, Discord, Slack, Microsoft Teams/Azure, and more — far more than any single peer.
- **Release cadence:** Beta releases every ~2 weeks with stabilization focus; other projects ship less frequently or only patch updates.

**Technical approach differences:**
- OpenClaw is a **gateway-centric architecture** (session lanes, gateway restart recovery, channel adapters), while NanoBot and Hermes Agent are **agent-centric** (local CLI, desktop UX, model routing). IronClaw sits between — gateway with strong UX/automation layer.
- OpenClaw's P0 focus (memory leak #91588, child-process zombie leak #97616, session lane starvation #54488) reflects enterprise gateway operational concerns that smaller projects do not yet face.

**Community size:** OpenClaw's issue/PR volume implies a contributor base roughly 5–10× larger than the next tier. Its most-discussed issues attract 20–23 comments each; peers typically see 2–6 comments on comparable issues.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Prompt caching reliability** | OpenClaw (#95610), Hermes Agent (#89886, #97281, #96811), IronClaw (#7824) | Cross-provider cache compatibility; session-ID churn breaks prefix caching; Anthropic/Bedrock/OpenAI divergence |
| **Context cost & compaction** | IronClaw (#7824, #7978), OpenClaw (#53008, #87136), ZeroClaw (#6850 RFC) | Unbounded context growth; $7–10/task cost delta; Pi-style bounded compaction; memory lifecycle decoupling |
| **Session/state correctness** | OpenClaw (#88856, #54488), NanoBot (#5589, #5579), ZeroClaw (#10408) | Stale session revival; session lane starvation; parallel-turn duplication; event-loop blocking from persistence |
| **Channel stability & reliability** | OpenClaw, NanoBot, ZeroClaw, LobsterAI | Crash-on-creation cron jobs (#5582), silent turn drops (#112259), reply-thread context fragmentation (#10237) |
| **Security & secrets hardening** | NanoClaw (#216, #3387, #3392), Hermes Agent (#43666), ZeroClaw (#10432) | Env var bypass via /proc; multi-instance DM leakage; plaintext passwords in state.db; TTS API key exposure |
| **Windows platform support** | Hermes Agent (#96570, #96956, #97702), NanoBot (#5578, #5581), OpenClaw (#119052) | TUI cursor, gateway startup, drag-drop regression — Windows is a consistent pain point across all tiers |
| **Local-model workflows** | NanoClaw (#3643), Hermes Agent (#90031), OpenClaw (#101445) | Hardcoded 30-min ceiling kills long local turns; Ollama tool call mismatches; reasoning_effort drift |
| **MCP integration maturity** | NanoBot (#5251, #5388), OpenClaw (#101554), CoPaw | Schema budgeting, oversized tool-list responses, host support in WebUI |
| **Observability & observability gaps** | OpenClaw (#50291), NanoClaw (#3599), IronClaw (#7961) | Missing trace context, lost failure classification on task runs, need for tenant-scoped telemetry |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | NanoBot | IronClaw | ZeroClaw | NanoClaw |
|---|---|---|---|---|---|---|
| **Primary focus** | Multi-channel gateway | Multi-provider agent + Studio UX | CLI-first local agent | Automation + durable inbox | Runtime architecture + RFC-driven | Security-hardened agent |
| **Target user** | Enterprise/ops, multi-tenant | Power users, multi-model | Developers, CLI enthusiasts | SaaS/automation operators | Infrastructure-focused operators | Security-conscious deployers |
| **Architecture** | Gateway + channel adapters + session lanes | Agent runtime + desktop app + Studio | CLI TUI + session manager | Automation engine + inbox + WebUI | Modular runtime + sandbox + RFC process | Agent + credential proxy + NDJSON setup |
| **Release model** | Weekly betas, fast stabilization | Event-driven, no tag cadence | No tags yet | Minor version (v1.4.0) | No tags yet | No tags yet |
| **Key differentiator** | Scale + channel breadth | Per-subagent model routing + ACP provider | Explicit memory recall + pluggable backend | Context compaction + PinchBench cost metrics | RFC-driven architecture + Telegram fix | Security hardening + OAuth refresh |
| **Security posture** | Install-policy warnings (#116489) | Redaction gap audit (#43666) | Session isolation | Schema-flattening bug (#7987) | Forbidding-path bypass (#9815) | /proc bypass fix (#216), DM isolation (#3387/3392) |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (500+ PRs/issues or strong multi-PR throughput):**
- **OpenClaw:** Highest velocity in the ecosystem; 500/500 daily; stabilizing gateway reliability. Mature enough to surface production-grade P0 bugs (memory leak, zombie processes).
- **ZeroClaw:** 37 issues + 50 PRs; active RFC pipeline with accepted designs awaiting implementation. High signal-to-noise ratio.

**Tier 2 — Active Development (30–60 combined):**
- **Hermes Agent:** 50/50 with strong bug-fix cadence; responsive to community (Anthropic 400 fix, TLS cert renewal, Nova cachePoint). Windows issues indicate platform gap.
- **CoPaw:** 39/27; beta release cadence; MCP protocol resilience focus.
- **IronClaw:** 14/28; post-release stabilization with clear cost-performance problems being addressed. RFC process shows architectural maturity.

**Tier 3 — Moderate/Steady (5–20 combined):**
- **NanoClaw:** 3 issues / 50 PRs — PR-heavy indicates contributor-driven work, but low issue volume suggests smaller user base or lower bug surface.
- **NanoBot:** 8 issues / 17 PRs — healthy contributor momentum; session persistence and memory system overhaul in flight.
- **LobsterAI:** 5 issues / 8 PRs — efficient closure rate (7/8 merged); smaller team but disciplined.

**Tier 4 — Low/No Activity:**
- **PicoClaw** (1/1), **Moltis** (1/0), **NullClaw** (0/0), **ZeptoClaw** (0/0) — minimal or no recent activity.

---

## 7. Trend Signals

1. **Prompt caching is the new battleground.** Every major project reports caching failures across providers. OpenClaw (#95610), Hermes (#89886, #97281, #96811), and IronClaw (#7824) all surface this. *Value for developers:* Investing in provider-agnostic cache strategies and session-ID stability will yield outsized cost reductions.

2. **Context cost is driving architecture.** IronClaw's PinchBench ($10.31 vs $2.52) and OpenClaw's compaction-freeze bugs (#53008) show that unbounded context is a production killer. *Value:* Compaction, result-reference, and projection seams are becoming table-stakes features, not nice-to-haves.

3. **Windows is the universal weak spot.** Hermes Agent (5 Windows issues), NanoBot (TUI cursor, clipboard race), OpenClaw (Gateway foreground-window behavior) — all report consistent degradation. *Value:* Cross-platform testing investment is a differentiator; few projects cover Windows thoroughly.

4. **Security hardening is moving from reactive to systematic.** NanoClaw's `/proc` bypass fix, Hermes's redaction audit, ZeroClaw's key-header sensitivity — all indicate the community is treating secret management as a first-class concern. *Value:* Operators will prefer agents with proven secrets-handling; this is a trust signal.

5. **RFC-driven development is emerging.** ZeroClaw's accepted-but-unimplemented RFCs (#6850, #6954, #6996) and IronClaw's lifecycle hooks epic (#7770) show a shift toward community-informed architecture. *Value:* Projects with transparent RFC processes attract more sustained contributor engagement.

6. **Local-model workflows are maturing.** NanoClaw's 30-min ceiling complaint (#3643), Hermes's reasoning_effort drift (#90031), and OpenClaw's Ollama mismatches (#101445) signal growing local-deployment adoption. *Value:* Configurability and observability for local backends will be a key competitive advantage.

7. **Multi-agent and cross-agent communication is a priority.** ZeroClaw's A2A tracker (#3566) has the most 👍 reactions (7); Hermes shipped per-subagent model routing (#76820); OpenClaw has subagent-drop bugs (#88856). *Value:* Inter-agent protocol support is converging as a required capability, not a differentiator.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-29

## 1. Today's Overview

NanoBot is showing strong contributor momentum with **17 PRs** updated in the last 24 hours and **8 active issues**, indicating a healthy and active development cadence. The project has no new releases yet, but several high-priority bug fixes and feature refactors are in flight. Activity is concentrated around session management, TUI stability, memory system overhaul, and cron reliability — suggesting the team is pushing hard on core architectural improvements ahead of an upcoming release.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**Merged / Closed PRs today:**

- **#5591** — `fix(webui): preserve named pane groups` (Re-bin) — Fixes a bug where removing panes would dissolve user-titled groups back into implicit unnamed ones, losing custom titles.
- **#5560** — `feat(cli): make nanobot the default agent command` (Re-bin) — Allows bare `nanobot` to launch the terminal agent directly, with root-level flags (`-m`, `--workspace`, `--session`, `--classic`) preserved. Major UX improvement for CLI ergonomics.
- **#5579** — `fix(session): move persistence off event loop` (chengyongru) — Adds cancellation-safe async SessionManager APIs and moves all session persistence off the event loop to prevent blocking.
- **#5578** — `test(tui): avoid clipboard status race on Windows` (chengyongru) — Fixes flaky Windows TUI test by waiting for the stable composer placeholder instead of a transient shimmer.
- **#5576 & #5577** — `fix(tui): preserve full UI in Herdr panes` (chengyongru) — Runs Herdr panes through the same alternate-screen TUI layout as standalone terminals; strips redundant metadata reporting.

**Key themes today:** CLI convenience, session persistence reliability, TUI cross-platform stability, and Herdr pane integration hardening.

## 4. Community Hot Topics

| Issue / PR | Topic | Comments | Links |
|---|---|---|---|
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) | MCP Apps host support in WebUI | 2 | [Issue](https://github.com/HKUDS/nanobot/issues/5251) |
| [#4429](https://github.com/HKUDS/nanobot/issues/4429) | Custom provider thinking-style config | 2 | [Issue](https://github.com/HKUDS/nanobot/issues/4429) |
| [#5388](https://github.com/HKUDS/nanobot/pull/5388) | Budget model-visible MCP schemas | 0 | [PR](https://github.com/HKUDS/nanobot/pull/5388) |
| [#5571](https://github.com/HKUDS/nanobot/pull/5571) | Require explicit memory recall by default | 0 | [PR](https://github.com/HKUDS/nanobot/pull/5571) |
| [#5570](https://github.com/HKUDS/nanobot/pull/5570) | Pluggable memory recall backend | 0 | [PR](https://github.com/HKUDS/nanobot/pull/5570) |

**Analysis:** The MCP-related discussions (#5251, #5388) reflect a growing need for better MCP tool/schema management — users want richer UI integration for MCP Apps and finer control over context budget. The memory system PRs (#5570, #5571) signal a major architectural shift toward explicit, pluggable recall, likely driven by users hitting noise/relevance issues with auto-injected memory. The custom provider thinking-style issue (#4429) shows continued demand for non-OpenAI provider parity.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|---|---|---|---|
| **P1** | [#5589](https://github.com/HKUDS/nanobot/pull/5589) | Discarded sessions can revive via stale queue messages on the global bus | PR open |
| **P1** | [#5580](https://github.com/HKUDS/nanobot/pull/5580) | Session persistence blocks the event loop, causing performance and cancellation issues | PR open (#5579 merged) |
| **P2** | [#5582](https://github.com/HKUDS/nanobot/issues/5582) | Cron jobs from WebUI quotes/@mentions crash at creation or fire time | PR #5587 addresses this |
| **P2** | [#5592](https://github.com/HKUDS/nanobot/issues/5592) | `edit_file` docs omit that match selectors are mutually exclusive | No fix yet |
| **P2** | [#5590](https://github.com/HKUDS/nanobot/pull/5590) | Oversized JSON tool results lose root-level fields in model-facing previews | PR open |
| **P2** | [#5581](https://github.com/HKUDS/nanobot/pull/5581) | TUI cursor position not preserved on Windows exit | PR open |
| **P2** | [#5588](https://github.com/HKUDS/nanobot/pull/5588) | Tool exceptions lack the "try a different approach" retry hint | PR open |

**Note:** The P1 session-revival bug (#5589) is the most critical open issue — discarded sessions remaining reachable via the message bus is a data-integrity risk. The cron crash (#5582) directly impacts user trust in scheduled reminders and has an active fix PR (#5587).

## 6. Feature Requests & Roadmap Signals

| Request | Status | Outlook |
|---|---|---|
| **MCP Apps host in WebUI** (#5251) | Open issue | Likely next minor release — aligns with broader MCP integration push |
| **Explicit memory recall by default** (#5571 + #5570) | PRs open | High confidence — the paired PRs form a complete feature; default behavior change suggests it's near landing |
| **Ephemeral runtime-context blocks** (#5586) | Open issue | Useful for transient sessions; moderate priority |
| **Provider retry notices in channels** (#5585) | Open issue | UX polish; low risk, likely to ship soon |
| **Bound reasoning_content replay** (#5584) | Open issue | Context-budget optimization; relevant if memory features ship |
| **Custom provider thinking config** (#4429) | Closed as done | Already merged — confirms active provider-parity roadmap |

**Prediction:** The next release will likely include the memory system overhaul (#5570/#5571), session persistence improvements (#5579/#5580), and the CLI convenience feature (#5560). MCP schema budgeting (#5388) and retry-notice routing (#5585) are also strong candidates.

## 7. User Feedback Summary

- **Pain points:** Cron jobs from WebUI context turns crash silently (#5582) — this is a trust-killer for users relying on reminders. Session persistence blocking the event loop (#5580) causes UI freezes. JSON tool result previews lose critical fields when objects are nested (#5590).
- **Satisfaction signals:** The bare `nanobot` CLI shortcut (#5560) directly addresses a common user complaint about command verbosity. TUI Windows cursor preservation (#5581) shows attention to detail on less-covered platforms.
- **Use cases:** MCP App UI integration (#5251) and provider-specific thinking mode (#4429) show users are running diverse model providers (VolcEngine/Doubao) and want first-class tooling integration, not just API compatibility.

## 8. Backlog Watch

| Item | Age | Concern |
|---|---|---|
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) MCP Apps host support | Created 2026-08-05, 24 days stale | High user interest, no PR yet |
| [#5388](https://github.com/HKUDS/nanobot/pull/5388) Budget model-visible MCP schemas | Created 2026-08-13, 16 days stale | Open PR with conflicts; blocks MCP UX improvements |
| [#5586](https://github.com/HKUDS/nanobot/issues/5586) Ephemeral runtime-context blocks | Created 2026-08-28, 1 day | New, but no maintainer response yet |
| [#5585](https://github.com/HKUDS/nanobot/issues/5585) Retry-wait notices in channels | Created 2026-08-28, 1 day | No PR yet; small but impactful UX gap |
| [#5584](https://github.com/HKUDS/nanobot/issues/5584) Bound reasoning replay | Created 2026-08-28, 1 day | No PR yet; related to memory cost optimization |
| [#5592](https://github.com/HKUDS/nanobot/issues/5592) `edit_file` doc gap | Created 2026-08-29, same day | Documentation fix needed |

**Recommendation:** The two MCP-related items (#5251, #5388) deserve maintainer attention — they're on the critical path for tooling maturity. #5388's conflict tag suggests it needs rebase before it can land.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-29

## 1. Today's Overview

Hermes Agent is experiencing high development velocity with 50 issues and 50 PRs updated in the last 24 hours, though the project remains release-quiet (no new tagged versions shipped today). Activity is heavily concentrated on prompt-caching regressions, Windows platform stability, and provider-compatibility bug fixes. The project maintains a strong open-issue ratio (40 open/active vs. 10 closed), signaling an active but busy community. Security-focused work continues to draw maintainer attention, notably redaction-gap analysis and approval-dialog bypass hardening.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**Closed/Merged PRs (today):**

- **PR #89931** — Fix for prompt-caching 400 errors behind LiteLLM Anthropic proxies ([link](https://github.com/NousResearch/hermes-agent/pull/89931)). The envelope cache layout incorrectly placed `cache_control` on tool messages, causing non-retryable HTTP 400s on the first cached tool turn.
- **PR #97710** — Salvage of PR #89931 rebased onto current `main`, which had drifted ~2,240 commits. Resolved a docstring conflict; zero production-logic conflicts.
- **PR #97393** — Fix for POSIX-only imports aborting the full pytest suite on Windows during collection ([link](https://github.com/NousResearch/hermes-agent/pull/97393)).
- **Issue #60119** (closed) — Kanban workers now correctly receive `kanban_*` lifecycle tools; the `_get_platform_tools` bug that dropped check_fn-gated toolsets for the platform CLI was fixed.

**Notable open PRs advancing features today:**

- **PR #97739** — Gateway worker and queue isolation under resource pressure, directly addressing the cgroup OOM kill vulnerability from Issue #70716.
- **PR #97231** — Global memory policy loaded across all profiles via a root `memories/GLOBAL.md`, with per-profile stores remaining independent.
- **PR #97737** — Mixture-of-Agents (MoA) output compacting reference markers on the messenger gateway.
- **PR #97736** — Master switch to disable the pre-agent auth fallback, giving operators full control over provider substitution behavior.
- **PR #97735** — ACP subprocess provider to run Agent Client Protocol agents (e.g., Claude Code) as model endpoints.
- **PR #97733** — LLM-generated session handoff with insight extraction for durable cross-session continuity.
- **PR #65592** — Hardening against approval-dialog bypass via `execute_code` and tool retry (layered dispatch-layer BLOCKED halt).

## 4. Community Hot Topics

**Most-discussed issues (by comment count):**

1. **[Security] Redaction gaps at persistence boundary** — Issue #43666 (6 comments) — Audit by @nnnarvaez found 23 plaintext password hits in `state.db` after one session. Split from #43083. Critical for operators running Hermes with sensitive tool outputs. [Link](https://github.com/NousResearch/hermes-agent/issues/43666)

2. **[Bug] Group chat system prompt null every turn** — Issue #96570 (6 comments) — Stored system prompt for group-chat sessions is `null` each turn, forcing full rebuild and prefix-cache misses. Affects Hermes Studio 0.6.47 + runtime 0.20.4 on Windows 11. [Link](https://github.com/NousResearch/hermes-agent/issues/96570)

3. **[Bug] Background curator skill_manage loop guard/schema failures** — Issue #64131 (6 comments) + Issue #63964 (5 comments) — Two related reports of the background curator session looping on `skill_manage` patch errors with no mission blockers present. Users report `has_blockers=true` with empty blocker lists. [Links: [#64131](https://github.com/NousResearch/hermes-agent/issues/64131) / [#63964](https://github.com/NousResearch/hermes-agent/issues/63964)]

4. **[Bug] Terminal executors sharing gateway cgroup** — Issue #70716 (5 comments) — Local background terminal commands inherit the gateway service cgroup; memory-heavy executors trigger `systemd-oomd` to kill the entire control plane. PR #97739 targets this. [Link](https://github.com/NousResearch/hermes-agent/issues/70716)

5. **[P0] Per-response session ID churn breaks prompt caching** — Issue #96811 (1 comment, P0) — Hosts minting one physical `session_id` per response cause every conversation-affinity key to re-key, yielding 0% prompt-cache hits. Affects OpenRouter, Nous, OpenAI providers. [Link](https://github.com/NousResearch/hermes-agent/issues/96811)

**Underlying needs:** The community is pushing hard on (a) prompt-caching reliability across providers, (b) Windows desktop stability, (c) long-running unattended bot operations, and (d) security hardening around secrets and approval flows.

## 5. Bugs & Stability

**P0 (critical):**

- **#89886** [CLOSED] — `cache_control` on `tool_result.content[]` rejected by Anthropic-format API, producing non-retryable 400 errors that kill any tool-using session. Fixed in PR #89931 / #97710. [Link](https://github.com/NousResearch/hermes-agent/issues/89886)
- **#97281** [CLOSED] — Amazon Nova models reject `cachePoint` in `toolConfig.tools` via Bedrock Converse API (`ValidationException`). Fixed. [Link](https://github.com/NousResearch/hermes-agent/issues/97281)
- **#90390** [CLOSED] — Quick Install one-liner failed for all new users due to expired Let's Encrypt TLS certificate on `hermes-agent.nousresearch.com` (expired 2026-08-18). Fixed. [Link](https://github.com/NousResearch/hermes-agent/issues/90390)
- **#96956** [OPEN] — `asyncio.start_unix_server` does not exist on Windows; `shutdown_watchdog` liveness witness never created on every gateway start (100% reproduction rate on Windows 11). No fix PR yet. [Link](https://github.com/NousResearch/hermes-agent/issues/96956)

**P2 (high):**

- **#96570** — Group chat sessions: system prompt rebuilt from scratch every turn, prefix cache always misses. No fix yet. [Link](https://github.com/NousResearch/hermes-agent/issues/96570)
- **#64131 / #63964** — Background curator loops on `skill_manage` patch errors. No fix yet. [Links: [#64131](https://github.com/NousResearch/hermes-agent/issues/64131) / [#63964](https://github.com/NousResearch/hermes-agent/issues/63964)]
- **#70716** — Terminal executors share gateway cgroup, can OOM-kill control plane. Fix in PR #97739. [Link](https://github.com/NousResearch/hermes-agent/issues/70716)
- **#90031** — `reasoning_effort` dropped for custom/OpenAI-compatible providers; local llama.cpp falls back to model default. No fix yet. [Link](https://github.com/NousResearch/hermes-agent/issues/90031)
- **#97702** — Desktop drag-and-drop file attachment broken on Windows (regression). No fix yet. [Link](https://github.com/NousResearch/hermes-agent/issues/97702)
- **#93911** — Desktop relay abandons `bot_relay.deliver` after 30s timeout, failing legitimate long-running bot turns. No fix yet. [Link](https://github.com/NousResearch/hermes-agent/issues/93911)
- **#97682** — Large-context Codex TTFB scaling immediately canceled by default 120s cap. No fix yet. [Link](https://github.com/NousResearch/hermes-agent/issues/97682)
- **#88988** — Desktop `/compress` reports timeout after 120s while compression completes successfully in background (~134s). No fix yet. [Link](https://github.com/NousResearch/hermes-agent/issues/88988)
- **#89241** — GLM-5 reasoning models killed by 90s non-stream stale detector during thinking phase. No fix yet. [Link](https://github.com/NousResearch/hermes-agent/issues/89241)

**P3 (medium):**

- **#52556** — Desktop upload over remote gateway fails with `EACCES` when session `cwd` is read-only. [Link](https://github.com/NousResearch/hermes-agent/issues/52556)
- **#96597** [CLOSED] — Failed gateway download truncates/deletes pre-existing files in downloads directory (data-loss severity). Fixed. [Link](https://github.com/NousResearch/hermes-agent/issues/96597)
- **#78374** — Hermes commit identity email (`hermes@nousresearch.com`) resolves to a real GitHub account, causing commit misattribution to "Rafa-Ross". [Link](https://github.com/NousResearch/hermes-agent/issues/78374)
- **#86571** — TUI mouse wheel and selection fail under Windows Terminal/ConPTY. [Link](https://github.com/NousResearch/hermes-agent/issues/86571)

## 6. Feature Requests & Roadmap Signals

- **#95489** — Desktop Debug MCP server: native UI-debugging tools for LLM agents. Addresses the pain of ad-hoc `scripts/eval.mjs` one-liners. [Link](https://github.com/NousResearch/hermes-agent/issues/95489)
- **#76820** [CLOSED] — Per-subagent model routing + API key pooling for delegation. Merged, enabling multi-model subagent workflows. [Link](https://github.com/NousResearch/hermes-agent/issues/76820)
- **#71266** — Native skill-sleep: validation-gated, staged self-improvement for skills (SkillOpt methodology, no external dependencies). [Link](https://github.com/NousResearch/hermes-agent/issues/71266)
- **#75145** — Prevent duplicate transcript replay and surface compression replay diagnostics. [Link](https://github.com/NousResearch/hermes-agent/issues/75145)
- **#97681** — Bot Group Chats should continue operating after Desktop closes. [Link](https://github.com/NousResearch/hermes-agent/issues/97681)
- **#66391** [CLOSED] — Move Discord env-only settings (`DISCORD_HOME_CHANNEL`, etc.) to `config.yaml`. Merged. [Link](https://github.com/NousResearch/hermes-agent/issues/66391)

**Likely candidates for next release:** The ACP subprocess provider (PR #97735), global memory policy across profiles (PR #97231), session handoff with insight extraction (PR #97733), and the MoA reference marker compaction (PR #97737) are all freshly opened and show active development momentum. The `hermes update --merge-ref` CLI improvement (PR #97732) also signals ongoing CLI polish.

## 7. User Feedback Summary

**Pain points:**
- **Prompt caching is fragile across providers.** Multiple P0/P2 issues (#89886, #97281, #96811, #90031) report cache-related failures or misses with Anthropic, Bedrock/Nova, OpenRouter, and custom OpenAI-compatible providers. This is the dominant user complaint.
- **Windows platform instability.** Five distinct Windows issues (#96570, #97702, #96956, #86571, #52556) span TUI, desktop drag-drop, gateway startup, file downloads, and remote uploads. Windows users report consistent degradation.
- **Long-running unattended operations time out.** Bot relay 30s timeout (#93911), GLM-5 90s stale detection (#89241), and compression 120s timeout (#88988) all share the pattern of Hermes killing legitimate slow operations.
- **Secrets redaction gaps.** Issue #43666 highlights plaintext passwords in `state.db` — a serious concern for operators handling credentials.
- **Background curator loops.** Issues #64131 and #63964 describe endless `skill_manage` failure loops with no mission blockers, suggesting a reliability gap in autonomous background sessions.

**Satisfaction signals:**
- The rapid closure of the Anthropic proxy 400 bug (#89886 → PR #89931 → PR #97710) and the Nova cachePoint fix (#97281) show responsive maintenance.
- The TLS certificate fix (#90390) resolved a blocker for all new installers.
- The per-subagent model routing feature (#76820) was implemented, directly addressing a community-requested delegation enhancement.

## 8. Backlog Watch

**Issues needing maintainer attention:**

1. **#43666** — Redaction gaps at persistence boundary (6 comments, open since 2026-06-10). Critical security issue with audit-confirmed plaintext secrets. No fix PR visible.
2. **#70716** — Terminal executors sharing gateway cgroup (5 comments, open since 2026-07-24). Fix PR #97739 is open but not yet merged.
3. **#96570** — Group chat system prompt null every turn (6 comments, opened 2026-08-27). High-impact bug for multi-user deployments; no fix yet.
4. **#64131 / #63964** — Background curator skill_manage loops (6 + 5 comments). Duplicate/related; needs triage consolidation and fix.
5. **#96811** — Per-response session ID churn, P0 (1 comment, opened 2026-08-28). Directly undermines prompt caching on hosted platforms. No fix yet.
6. **#78374** — Commit identity misattribution to real GitHub account (1 comment, open since 2026-08-04). Security/audit concern; no fix yet.
7. **#97702** — Desktop drag-and-drop regression on Windows (3 comments, opened 2026-08-29). Fresh regression needing urgent triage.
8. **#93911** — Bot relay 30s timeout abandoning legitimate long turns (3 comments, open since 2026-08-24). No fix yet.
9. **#89

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-29

---

## 1. Today's Overview

PicoClaw saw modest but focused activity on 2026-08-29, with one issue and one pull request updated in the last 24 hours. The merged PR (#1349) advances QQ Channel integration by adding richer media handling, while the open issue (#3342) reflects ongoing community interest in refining the agent's message-steering behavior. No new releases were published, indicating the team may be stabilizing before the next tagged version. Overall, project health appears steady with sustained community contribution momentum.

---

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Project Progress

**Merged PR: [#1349](https://github.com/sipeed/picoclaw/pull/1349) — feat(qq): support parsing and replying to more attachment types**
- Author: `aishannon`
- This pull request significantly expands QQ Channel channel support by enabling:
  - Parsing of QQ Channel emoji structures
  - Handling of incoming voice, image, video, and file messages
  - Sending replies with local voice, image, video, and file attachments (with pre-upload support)
  - A Markdown-first reply strategy with graceful fallback
- **Impact:** This is a meaningful enhancement to one of PicoClaw's social channel integrations, reducing friction for users relying on QQ as a communication vector and broadening the types of media the agent can process and produce.

---

## 4. Community Hot Topics

**[Issue #3342](https://github.com/sipeed/picoclaw/issues/3342) — Opt-in "after-turn" steering mode: queue busy-session messages instead of interrupting the running turn**
- Author: `unedtamps` | Created: 2026-08-21 | Updated: 2026-08-28 | 1 comment | 👍 0
- **Core ask:** Instead of treating a second user message sent during an active agent turn as a mid-task course correction (which skips remaining tool calls), queue the new message and process it *after* the current turn completes.
- **Underlying need:** Users are encountering frustrating behavior where their follow-up messages cause partial task failures or abandoned tool calls. The current "interrupt and redirect" model doesn't match user expectations for conversational flow. This feature request signals a desire for a more predictable, sequential agent interaction model—particularly important for multi-step tool-use workflows where abrupt interruption leads to lost state or incomplete results.

---

## 5. Bugs & Stability

No new bug reports, crashes, or regressions were filed today. The single open issue (#3342) is a feature request, not a defect. Project stability appears unaffected by recent changes.

---

## 6. Feature Requests & Roadmap Signals

- **[Issue #3342](https://github.com/sipeed/picoclaw/issues/3342)** — The "after-turn" steering mode is the most notable feature signal. If adopted, it would represent a fundamental shift in how PicoClaw handles concurrent user input during active agent turns. Given the explicit use case described (avoiding skipped tool calls), this is likely to resonate with power users and could be prioritized for an upcoming release if maintainers agree on the implementation approach.
- The merged QQ Channel media support (PR #1349) suggests the roadmap continues to emphasize **multi-platform channel parity**, especially for under-served integrations.

---

## 7. User Feedback Summary

- **Pain point (Issue #3342):** Users find the current mid-turn interruption behavior jarring and destructive to multi-step workflows. The explicit request for an *opt-in* mode suggests the community is divided—some users may prefer the existing interrupt behavior for quick course-corrections, while others want sequential processing. A toggle or configuration option would likely satisfy both camps.
- **Satisfaction signal (PR #1349):** The QQ Channel enhancement was contributed by a community member (`aishannon`), indicating healthy external investment in the project's ecosystem. The thoroughness of the PR (covering parsing, reply strategies, and media upload) reflects strong user-driven development.

---

## 8. Backlog Watch

- **[Issue #3342](https://github.com/sipeed/picoclaw/issues/3342)** — Open since 2026-08-21, last updated 2026-08-28, flagged as `[stale]` with no maintainer response yet. This is a high-signal feature request that warrants attention; the stale label may reflect inactivity rather than lack of merit. Maintainer engagement here would clarify whether an "after-turn" mode is in scope and what implementation direction the team prefers.

---

*Digest generated from GitHub data as of 2026-08-29. All links point to [github.com/sipeed/picoclaw](https://github.com/sipeed/picoclaw).*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-29

## 1. Today's Overview

NanoClaw shows robust development momentum with **50 PRs updated** in the last 24 hours (45 open, 5 merged/closed), while only **3 issues were touched** — a strong signal that the contributor base is actively shipping rather than triaging. No new releases were published today. The project is heavily focused on two parallel tracks: refining the **native setup/uninstall driver protocol** (a 9-PR stack by amit-shafnir) and hardening **channel/DM security** across Slack and agent-runner paths. The absence of new releases combined with high PR throughput suggests the team is building toward a upcoming version bump.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

**Merged / Closed PRs today:**

- **#2361** — [codex] tighten codex provider contracts · Replaced the stale Codex SDK provider sketch with the current `codex app-server` JSON-RPC contract; made `CODEX_MODEL` optional. Improves reliability of the Codex integration. (`[nanocoai/nanoclaw#2361](https://github.com/nanocoai/nanoclaw/pull/2361)`)
- **#2363** — fix(credential-proxy): proactively refresh expiring Anthropic OAuth tokens (v2 port of #1102) · Ensures native-credential-proxy users no longer hit silent 401s after ~1 hour. (`[nanocoai/nanoclaw#2363](https://github.com/nanocoai/nanoclaw/pull/2363)`)
- **#1102** — fix(credential-proxy): auto-refresh OAuth token, handle keychain-only auth · Original fix; now closed following the v2 port. (`[nanocoai/nanoclaw#1102](https://github.com/nanocoai/nanoclaw/pull/1102)`)
- **#216** — security: fix secret sanitization bypass via `/proc` and Read tool · Closes a critical bypass where `unset`-based env wiping could be circumvented via `/proc/self/environ`. (`[nanocoai/nanoclaw#216](https://github.com/nanocoai/nanoclaw/pull/216)`)
- **#2326** — docs: add issue templates (bug, enhancement, skill) · Standardizes issue reporting. (`[nanocoai/nanoclaw#2326](https://github.com/nanocoai/nanoclaw/pull/2326)`)

**Notable open PRs advancing today:**

- **Setup driver stack (PRs #3633–#3640, #3485, #3635–#3639)** — A 9-PR coordinated effort by amit-shafnir moving the entire interactive setup flow (auth picker, first chat, channel selection, uninstall) off the terminal prompt library and onto a machine-driven NDJSON protocol. Includes parity tests, entry guards refusing secrets on argv/env, and a native-app uninstall path. (`[nanocoai/nanoclaw#3633](https://github.com/nanocoai/nanoclaw/pull/3633)`, `[nanocoai/nanoclaw#3635](https://github.com/nanocoai/nanoclaw/pull/3635)`, `[nanocoai/nanoclaw#3637](https://github.com/nanocoai/nanoclaw/pull/3637)`, `[nanocoai/nanoclaw#3640](https://github.com/nanocoai/nanoclaw/pull/3640)`)
- **#3392** — fix(slack): keep 1:1 DMs private to the paired user · Prevents cross-user DM exposure via channel registration interceptors. (`[nanocoai/nanoclaw#3392](https://github.com/nanocoai/nanoclaw/pull/3392)`)
- **#3388** — fix(agent-runner): default task-run escalations to the agent's own channel · Prevents task notifications from leaking into another agent's DM. (`[nanocoai/nanoclaw#3388](https://github.com/nanocoai/nanoclaw/pull/3388)`)
- **#3387** — fix(approvals): preserve adapter instance for DMs · Fixes multi-instance channel installs where approval flows could reuse a sibling adapter's cached DM. (`[nanocoai/nanoclaw#3387](https://github.com/nanocoai/nanoclaw/pull/3387)`)
- **#2003** — feat(skill): voice transcription V2 (container-side, sovereign by default) · Re-submission with implementation moved into the agent container per maintainer feedback. (`[nanocoai/nanoclaw#2003](https://github.com/nanocoai/nanoclaw/pull/2003)`)

---

## 4. Community Hot Topics

| # | Type | Title | Comments | Link |
|---|------|-------|----------|------|
| #3645 | Issue | `bash nanoclaw.sh` hangs indefinitely with no feedback | 2 | [#3645](https://github.com/nanocoai/nanoclaw/issues/3645) |
| #3643 | Issue | Hardcoded 30-min ABSOLUTE_CEILING_MS cold-kills long local-model turns | 0 | [#3643](https://github.com/nanocoai/nanoclaw/issues/3643) |
| #3599 | Issue | Persist rate_limit/quota classification on task runs for auto-retry | 0 | [#3599](https://github.com/nanocoai/nanoclaw/issues/3599) |

**Analysis:**

- **#3645** (2 comments) is the most discussed item today. Users launching via `nanoclaw.sh` expect interactive feedback; a silent hang indicates a bootstrap-level UX gap, especially for new or casual users.
- **#3643** reflects a real pain point for **local-model users** whose agent turns exceed 30 minutes and are forcibly killed by the host sweep. The hardcoded ceiling with no config seam is a friction point as the project attracts more local-deployment users.
- **#3599** addresses a telemetry/observability gap: failed task runs lose their failure reason, makingOps debugging and auto-retry logic impossible. This signals users want **reliable scheduled-task reliability** — a feature that would matter most for production deployments.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR? |
|----------|------|-------------|---------|
| **High** | #3645 | `bash nanoclaw.sh` hangs indefinitely with no logging or feedback | No open PR yet |
| **High** | #3643 | Hardcoded 30-min `ABSOLUTE_CEILING_MS` cold-kills long local-model agent turns; no config seam | No open PR yet |
| **Medium** | #216 (now closed) | Secret sanitization bypass via `/proc/self/environ` and Read tool — `unset`-based env wiping was circumventable | ✅ Merged (#216) |
| **Medium** | #1102/#2363 (now closed) | OAuth tokens expired after ~1 hour with silent permanent 401s in credential-proxy | ✅ Merged (#2363) |
| **Medium** | #3392 | Slack DMs could be exposed to unintended users via channel registration interceptor | ✅ Open PR (#3392) |
| **Medium** | #3388 | Task-run escalations could land in another agent's DM | ✅ Open PR (#3388) |
| **Medium** | #3387 | Multi-instance channel installs could reuse wrong adapter's cached DM for approvals | ✅ Open PR (#3387) |

**Trend:** The project is actively closing a cluster of **security and multi-tenant isolation bugs** (#216, #3387, #3392, #3388). The two open high-severity issues (#3645, #3643) both relate to **local/development experience** rather than production safety — a lower-risk but higher-friction category for early adopters.

---

## 6. Feature Requests & Roadmap Signals

| Source | Request | Signal Strength |
|--------|---------|-----------------|
| #3599 | Persist rate-limit/quota classification on task runs; auto-retry once capacity returns | **High** — directly addresses production reliability for scheduled tasks |
| #2003 | Voice transcription V2 skill, container-side and sovereign by default | **High** — re-submitted with architectural feedback incorporated; strong community interest |
| #3643 | Configurable `ABSOLUTE_CEILING_MS` (or removal of hard limit) for local-model backends | **Medium** — enables long-running local-agent workflows; likely to be adopted quickly if accepted |
| amit-shafnir setup stack | Machine-driven setup/uninstall via NDJSON protocol; GUI-app install experience | **High** — 9-PR coordinated effort signals this is a prioritized roadmap item for the next release |
| #3644 | GitHub issue forms (open) | **Low** — process improvement, not user-facing |

**Prediction:** The next release will likely include the **setup driver protocol** (machine-mode install/uninstall), the **credential-proxy OAuth refresh** fix, and possibly the **issue form templates**. Voice transcription V2 and the local-model ceiling fix are strong candidates for the release after next.

---

## 7. User Feedback Summary

- **Pain point — bootstrapping UX:** Users report that `bash nanoclaw.sh` can hang silently with no feedback or logging (#3645). This is a critical onboarding blocker.
- **Pain point — local-model workflows:** Long agent turns on local backends are killed by a hardcoded 30-minute ceiling with no escape hatch (#3643). Users running local models expect configurability.
- **Pain point — observability:** Task failures lose their root cause classification, making it impossible to distinguish rate-limit exhaustion from real bugs (#3599).
- **Satisfaction signal:** The rapid merge of security-critical fixes (#216, #2363) and multi-tenant isolation bugs (#3387, #3392, #3388) shows the team is responsive to community-reported issues.
- **Satisfaction signal:** The voice transcription V2 PR (#2003) was re-opened and re-submitted per maintainer feedback rather than rejected, indicating an open contributor dialogue.

---

## 8. Backlog Watch

| Item | Age | Why It Needs Attention |
|------|-----|------------------------|
| #3645 — `nanoclaw.sh` hangs indefinitely | Created 2026-08-29 (today) | 2 comments but no fix in sight; onboarding-critical bug |
| #3643 — Hardcoded 30-min ceiling, no config seam | Created 2026-08-28 (yesterday) | Blocks local-model power users; no PR yet |
| #3599 — Persist rate-limit classification on task runs | Created 2026-08-28 (yesterday) | No PR; important for scheduled-task reliability |
| #2003 — Voice transcription V2 | Created 2026-04-25 (~4 months) | Re-submitted but still open; architectural scope is large |
| #3427 — fix(agent-runner): send_card drops callback actions | Created 2026-08-21 | Open PR, no merge yet; may block card-based workflows |

**Maintainer note:** The setup driver stack (#3633–#3640, #3485, #3635–#3639) is a large coordinated PR set. Ensuring these land cohesively — and are tested against both terminal and machine-renderer paths — should be a priority before the next release branch is cut.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-29

## 1. Today's Overview

IronClaw is in an active post-1.4.0 stabilization phase, with **14 issues** and **28 PRs** updated in the last 24 hours. The project is heavily focused on **performance optimization** — the majority of today's top issues and PRs address prompt inflation, token waste, and tool-call overhead that were exposed after the 1.4.0 release. Three notification-related issues (#7873, #7874, #7875) were closed today, indicating the durable inbox feature shipped in v1.4.0 is being validated in production. The most consequential theme is context-management cost: users are hitting multi-second inference stalls from unprojected payloads, and the core team is responding with compaction hardening, result-reading budget fixes, and schema flattening work.

---

## 2. Releases

### `ironclaw-v1.4.0` — 2026-08-27

Promoted from `1.4.0-rc.1` after 81 commits. Key additions include the **durable notification inbox** (publishes authoritative outcomes and actionable gates per user, surfaced in the WebUI). Full release notes are tracked in the v1.4.0 milestone.

> No breaking changes announced. No migration notes required beyond the new inbox notification types (`RunFailed`, `AuthenticationRequired`, `RunBlocked`).

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Author | Summary |
|---|---|---|
| [#7899](https://github.com/nearai/ironclaw/pull/7899) | italic-jinxin | feat(notifications): publish automation pre-run failures — `RunFailed` inbox notification |
| [#7982](https://github.com/nearai/ironclaw/pull/7982) | henrypark133 | fix(tools): stop sending the model after a `result_read` budget it cannot reach |
| [#7979](https://github.com/nearai/ironclaw/pull/7979) | henrypark133 | test(extensions): enforce encoded output ownership (fail-closed gate) |
| [#7980](https://github.com/nearai/ironclaw/pull/7980) | henrypark133 | ci: validate integration group topology before group tests execute |
| [#7901](https://github.com/nearai/ironclaw/pull/7901) | italic-jinxin | fix(notifications): persist auth gates before enrichment |
| [#7900](https://github.com/nearai/ironclaw/pull/7900) | italic-jinxin | feat(notifications): publish durable resource blocks → `RunBlocked` |
| [#7965](https://github.com/nearai/ironclaw/pull/7965) | pranavraja99 | perf(tool-search, github): stop offering tools matching one incidental query term |
| [#5563](https://github.com/nearai/ironclaw/pull/5563) | achalvs | feat(webui): design system tokens + /playground (closed after design review) |
| [#5084](https://github.com/nearai/ironclaw/pull/5084) | achalvs | Redesign the automations page (closed, merged) |

### Key Open PRs Advancing

- **[PR #7978](https://github.com/nearai/ironclaw/pull/7978)** — Compaction: bound cumulative summarizer input (fixes unbounded token growth during context compaction)
- **[PR #7977](https://github.com/nearai/ironclaw/pull/7977)** — Loop: terminate on dominant repeated output, cap interactive wall clock (prevents runs like `e3513a4e` that burned 593 tool calls over 70 min)
- **[PR #7961](https://github.com/nearai/ironclaw/pull/7961)** — Telemetry: scoped tenant BI collection (hourly activity, model usage, failure stats)
- **[PR #7958](https://github.com/nearai/ironclaw/pull/7958)** — Learning: shared review router (post-run learning path, disabled by default)
- **[PR #7908](https://github.com/nearai/ironclaw/pull/7908)** — Spike: canonical executor in persistent user sandbox (moves the agent loop into Docker, keeping scheduler/auth on host)

---

## 4. Community Hot Topics

| Rank | Issue/PR | Comments | Author | Theme |
|---|---|---|---|---|
| 1 | [#7891](https://github.com/nearai/ironclaw/issues/7891) | 10 | henrypark133 | 19.2s inference stall from 49 KB unprojected MIME headers |
| 2 | [#7824](https://github.com/nearai/ironclaw/issues/7824) | 5 | serrrfirat | Pi-style context compaction barrier; $10.31 vs $2.52 on PinchBench |
| 3 | [#7770](https://github.com/nearai/ironclaw/issues/7770) | 4 | serrrfirat | Epic: hook the agent lifecycle (after-turn, before-turn, compaction seams) |
| 4 | [#7981](https://github.com/nearai/ironclaw/issues/7981) | 3 | henrypark133 | 64 tool calls + 3m01s to list repos; 519 KB payload for 98 repos |
| 5 | [#7903](https://github.com/nearai/ironclaw/issues/7903) | 2 | serrrfirat | Persistent per-user sandboxed executor decision spike |

**Underlying need:** The community is hitting real production cost walls. Context projection (Issue #7824) is the most strategically important thread — without it, every long conversation grows linearly in token cost. The lifecycle hooks epic (#7770) is the architectural response: make compaction, notification, and tool-result seams extensible so performance fixes don't require core edits.

---

## 5. Bugs & Stability

### Open Bugs (ranked by severity)

| Issue | Severity | Summary | Fix PR |
|---|---|---|---|
| [#7987](https://github.com/nearai/ironclaw/issues/7987) | **High** | `flatten_top_level` silently discards all non-whitelisted top-level schema constraints | None yet |
| [#7891](https://github.com/nearai/ironclaw/issues/7891) | **Medium** | Unprojected 24 KiB head-slice costs 14.3s inference on two Gmail messages | Related to #7824 (in progress) |
| [#7986](https://github.com/nearai/ironclaw/issues/7986) | **Medium** | `github.list_repos` ships 81 raw fields per repo; projection seam unused | [#7965](https://github.com/nearai/ironclaw/pull/7965) (merged) |
| [#7981](https://github.com/nearai/ironclaw/issues/7981) | **Medium** | 64 tool calls to answer a question already answered at call #1 | Related to #7986 |
| [#7930](https://github.com/nearai/ironclaw/issues/7930) | **Medium** | No reference-based tool argument chaining; forces verbatim re-emission | None yet |

### Closed Today

- [#7873](https://github.com/nearai/ironclaw/issues/7873) — Pre-run failure notifications (shipped in #7899)
- [#7875](https://github.com/nearai/ironclaw/issues/7875) — Authentication-required notifications (shipped)
- [#7874](https://github.com/nearai/ironclaw/issues/7874) — Resource/policy blocked-run notifications (shipped in #7900)

**Stability assessment:** The bug surface is narrow but impactful — schema flattening (#7987) is a correctness issue that could silently drop constraints. The performance bugs are architectural (unbounded context) rather than crashes.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Signal |
|---|---|---|
| Context compaction with Pi-style bounds | [#7824](https://github.com/nearai/ironclaw/issues/7824) | **High confidence** — core PR #7978, #7975, #7976 all in flight |
| Tool-argument result references | [#7930](https://github.com/nearai/ironclaw/issues/7930) | Likely in next minor; unblocks chained tool workflows |
| Lifecycle hooks (after-turn, before-turn, compaction) | [#7770](https://github.com/nearai/ironclaw/issues/7770) | Epic phased across multiple PRs; compaction hooks landing first |
| NEAR AI modalities + capability tags in WebUI | #7970, #7969, #7971 | Three linked issues by same author; likely bundled |
| Persistent sandboxed executor | [#7903](https://github.com/nearai/ironclaw/issues/7903) / [#7908](https://github.com/nearai/ironclaw/pull/7908) | Spike PR open; decision pending |
| Tenant-scoped BI telemetry | [#7961](https://github.com/nearai/ironclaw/pull/7961) | In review; high-value for SaaS deployments |
| Shared review router for learning | [#7958](https://github.com/nearai/ironclaw/pull/7958) | Disabled by default; learning feature exploration |

**Next version prediction:** v1.5.0 will likely ship compaction bounds, lifecycle hooks phase 1, and the notification inbox hardening. NEAR AI modality support is small-enough to land in a patch.

---

## 7. User Feedback Summary

**Pain points (from issue descriptions):**

- *"Two `gmail.get_message` calls returning 274 ms and 290 ms cost a 19.7-second turn"* (#7891) — raw MIME headers are being pushed into prompts unasked, inflating inference cost by 70×.
- *"list my github repos took 64 tool calls and 3m01s. The answer was already fully present after call #1"* (#7981) — no result-caching or reference mechanism between tool calls.
- PinchBench cost comparison: $10.31 vs $2.52 for the same 147-task workload (#7824) — context is not being projected before reaching the model.
- `flatten_top_level` silently drops constraints (#7987) — users cannot trust that their schema restrictions are honored.

**Satisfaction signals:**

- The durable inbox notifications are being validated in production (3 issues closed, PRs merged).
- The design system and automations page redesign (#5563, #5084) received positive design leadership feedback.
- New contributors (achalvs, standardtoaster) are landing PRs, indicating growing community engagement.

---

## 8. Backlog Watch

| Item | Age | Risk | Why It Needs Attention |
|---|---|---|---|
| [#7987](https://github.com/nearai/ironclaw/issues/7987) — `flatten_top_level` constraint loss | 1 day | **High** | Correctness bug with no fix PR yet; silently discards user-defined schema constraints |
| [#7903](https://github.com/nearai/ironclaw/issues/7903) — Sandbox executor decision | 3 days | Medium | Architectural spike blocking long-term sandbox strategy; no decision recorded |
| [#7930](https://github.com/nearai/ironclaw/issues/7930) — Tool argument references | 2 days | Medium | Unblocks chained tool workflows; no PR opened |
| [#7824](https://github.com/nearai/ironclaw/issues/7824) — Context projection epic | 7 days | **High** | $7.79/task cost delta in production; multiple PRs in flight but no merged fix yet |
| [#7770](https://github.com/nearai/ironclaw/issues/7770) — Lifecycle hooks epic | 9 days | Medium | Foundational for extensibility; phased rollout needed |

**Overall project health:** 🟢 **Active and responsive.** The core team is moving quickly on the most impactful performance issues (compaction bounds, result_read budgeting, tool-search filtering). The main risk is the unaddressed schema-flattening bug (#7987) and the still-open context projection problem (#7824) — both are being worked but have not landed yet.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# 🦞 LobsterAI Project Digest — 2026-08-29

## 1. Today's Overview

LobsterAI released version **2026.8.28** today, focusing on account menu fixes, a new plan model catalog feature, and a phone nickname correction. Activity remains moderate with 5 issues and 8 PRs updated in the last 24h. The project shows healthy maintenance patterns with 7 of 8 PRs merged/closed, indicating efficient review cycles. Core contributors (liuzhq1986, MaoQianTu) continue driving quality improvements in safety modules and URL handling.

## 2. Releases

### LobsterAI 2026.8.28 (2026-08-28)

**Changes:**
- `Liuzhq/login guide` — Updated login documentation (#2525)
- `feat(settings): add plan model catalog` — New feature for model plan management (#2530)
- `fix(account): resolve phone masking merge conflict` — Account menu fixes preserving phone number masking (#2570)
- `Liuzhq/fix phone nickname` — Nickname display corrections (#2569, #2571)

**Breaking Changes:** None detected.

**Migration Notes:** No database or configuration changes required.

## 3. Project Progress

### Merged/Closed PRs Today (7)

| PR | Author | Summary | Status |
|---|---|---|---|
| [#2572](https://github.com/netease-youdao/LobsterAI/pull/2572) | liuzhq1986 | Release/2026.8.24 | ✅ Merged |
| [#2571](https://github.com/netease-youdao/LobsterAI/pull/2571) | liuzhq1986 | Liuzhq/fix phone nickname | ✅ Closed |
| [#2570](https://github.com/netease-youdao/LobsterAI/pull/2570) | liuzhq1986 | fix(account): resolve phone masking merge conflict | ✅ Closed |
| [#2569](https://github.com/netease-youdao/LobsterAI/pull/2569) | liuzhq1986 | Liuzhq/fix phone nickname | ✅ Closed |
| [#1156](https://github.com/netease-youdao/LobsterAI/pull/1156) | MaoQianTu | Add Vitest unit tests for commandSafety & coworkMemoryJudge | ✅ Closed |
| [#1155](https://github.com/netease-youdao/LobsterAI/pull/1155) | YDXyydsyyds | Session in-page search (Ctrl+F / Cmd+F) | ✅ Closed |
| [#1153](https://github.com/netease-youdao/LobsterAI/pull/1153) | MaoQianTu | Fix Gemini /v1 URL concatenation bug | ✅ Closed |

**Key Advances:**
- **Session Search Feature:** New Ctrl+F/Cmd+F functionality for in-page keyword search within conversation detail views (#1155)
- **Test Coverage:** Significant expansion of unit test coverage for core safety modules (#1156)
- **Bug Fixes:** URL handling improvements for Google Gemini integration (#1153)

## 4. Community Hot Topics

### Most Active Issues

| Issue | Author | Comments | Summary | Status |
|---|---|---|---|---|
| [#2489](https://github.com/netease-youdao/LobsterAI/issues/2489) | nimamasl114514 | 3 | Request for v4pro update | ✅ Closed |
| [#2536](https://github.com/netease-youdao/LobsterAI/issues/2536) | MurrayHubert | 2 | WeChat group full, request for new group | ✅ Closed |
| [#1154](https://github.com/netease-youdao/LobsterAI/issues/1154) | MaoQianTu | 2 | Add Vitest tests for commandSafety & coworkMemoryJudge | ✅ Closed |
| [#1149](https://github.com/netease-youdao/LobsterAI/issues/1149) | MaoQianTu | 1 | Add Vitest tests for coworkMemoryExtractor | 🟡 Open |
| [#1151](https://github.com/netease-youdao/LobsterAI/issues/1151) | MaoQianTu | 1 | Fix Gemini URL拼接错误 | ✅ Fixed via PR #1153 |

**Analysis:**
- **WeChat Community Growth:** Issue #2536 indicates rapid user base expansion, necessitating multiple WeChat groups
- **Testing Momentum:** MaoQianTu's test coverage initiative shows community-driven quality improvement
- **Feature Demand:** Request for v4pro update suggests interest in newer model capabilities

## 5. Bugs & Stability

### Critical Bugs Fixed

| Bug | Severity | Fix PR | Status |
|---|---|---|---|
| [#1151](https://github.com/netease-youdao/LobsterAI/issues/1151) — Gemini /v1 URL off-by-one error | 🔴 High | [#1153](https://github.com/netease-youdao/LobsterAI/pull/1153) | ✅ Fixed |

**Bug Details:**
- **Impact:** URL concatenation error caused malformed API endpoints for Google Gemini integration
- **Root Cause:** `slice(0, -3)` removed an extra `/` character from baseURL
- **Resolution:** Corrected slicing logic in `buildOpenAIChatCompletionsURL`

### Open Bug Reports

| Issue | Severity | Summary |
|---|---|---|
| [#1146](https://github.com/netease-youdao/LobsterAI/issues/1146) | 🟡 Medium | New agent creation not retrieving task records |

**Status:** No fix PR available yet. Requires maintainer attention.

## 6. Feature Requests & Roadmap Signals

### Recent Feature Additions

| Feature | PR | Description |
|---|---|---|
| Session In-Page Search | [#1155](https://github.com/netease-youdao/LobsterAI/pull/1155) | Ctrl+F/Cmd+F for conversation detail views with TreeWalker + Range-based positioning |
| Plan Model Catalog | [#2530](https://github.com/netease-youdao/LobsterAI/pull/2530) | New settings feature for managing model plans |
| Account Menu Fixes | [#2570](https://github.com/netease-youdao/LobsterAI/pull/2570) | Phone masking preservation in account settings |

### User-Requested Features

- **v4pro Update Request** (#2489): Users requesting newer model capabilities
- **New WeChat Group** (#2536): Community scaling necessitates additional support channels
- **Test Coverage Expansion** (#1149, #1154): Community-driven quality assurance initiatives

## 7. User Feedback Summary

### Pain Points Identified

| Issue | User | Feedback |
|---|---|---|
| [#2536](https://github.com/netease-youdao/LobsterAI/issues/2536) | MurrayHubert | WeChat group full — indicates rapid adoption and community demand |
| [#2489](https://github.com/netease-youdao/LobsterAI/issues/2489) | nimamasl114514 | Request for v4pro update — desire for newer model versions |
| [#1146](https://github.com/netease-youdao/LobsterAI/issues/1146) | tzhouzhou | Agent task record retrieval bug — frustration with data inconsistency |

### Positive Signals

- Efficient PR review cycles (7/8 merged/closed)
- Active community testing contributions
- Clear documentation updates (login guide)

## 8. Backlog Watch

### Long-Unanswered Issues Requiring Attention

| Issue | Author | Created | Days Open | Priority |
|---|---|---|---|---|
| [#1149](https://github.com/netease-youdao/LobsterAI/issues/1149) | MaoQianTu | 2026-03-31 | ~151 | 🟡 Medium |
| [#1146](https://github.com/netease-youdao/LobsterAI/issues/1146) | tzhouzhou | 2026-03-31 | ~151 | 🟡 Medium |

**Issue #1149:** Extension of Vitest test coverage to `coworkMemoryExtractor` module — critical for regression prevention but awaiting maintainer review.

**Issue #1146:** Agent task record retrieval bug — impacts user workflow when creating new agents.

### Maintainer Notes

- Consider prioritizing backlog issues #1149 and #1146 for next sprint
- Community testing contributions show strong quality assurance momentum
- WeChat group capacity issues suggest need for scaled community support channels

---

**Project Health Score: 🟢 Good** — Active development, efficient PR cycles, expanding test coverage, responsive community management.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-29

## 1. Today's Overview
Moltis activity is low on this date, with only one issue updated in the last 24 hours and no pull requests or new releases. The single open bug (#1246) indicates a sandbox‑related regression that warrants maintainer attention, but overall project momentum appears steady rather than active. No critical blockers or community‑driven development signals were reported today.

## 2. Releases
No new releases were published in the reporting window.

## 3. Project Progress
No pull requests were merged or closed today; therefore, no features were advanced or fixed in this period.

## 4. Community Hot Topics
- **Issue #1246** – *can't run on sandbox after a node is added* (open, bug)  
  [GitHub Link](https://github.com/moltis-org/moltis/issues/1246)  
  This is the only issue updated today and currently has zero comments and zero reactions. The bug suggests a regression in sandbox execution after node addition, which may affect users who rely on isolated test environments. While not yet highly discussed, it highlights a need for robust sandbox‑node interaction testing.

## 5. Bugs & Stability
- **Bug #1246** (severity: medium) – Users cannot run the application in sandbox mode after adding a node. No fix PR has been opened yet. This is the only bug reported today and points to a potential stability gap in the sandbox‑node lifecycle.

## 6. Feature Requests & Roadmap Signals
No new feature requests or roadmap‑related issues were created today. The single bug report does not signal an explicit feature demand, though improved sandbox reliability could be considered a future enhancement.

## 7. User Feedback Summary
The only direct user feedback today is the bug report (#1246), which indicates dissatisfaction with the current sandbox‑after‑node‑addition workflow. No positive satisfaction signals or broader use‑case discussions were captured in the 24‑hour window.

## 8. Backlog Watch
Issue #1246 is newly created (2026-08-28) and has not yet received maintainer response. While not a long‑standing backlog item, it requires prompt attention to prevent erosion of trust in sandbox functionality. No other issues or PRs are pending maintainer review today.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-29

## 1. Today's Overview
Activity remains high with **39 issues** and **27 PRs** updated in the last 24 hours, signaling strong contributor momentum ahead of the v2.2.0 release. Two new beta versions shipped today, focusing on MCP protocol resilience, workspace startup safety

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-29

---

## 1. Today's Overview

ZeroClaw maintained high development velocity on 2026-08-29, with **37 issues** and **50 PRs** updated in the last 24 hours. No new releases were shipped, but the project advanced several critical RFCs and security fixes. Activity is heavily weighted toward runtime architecture, security hardening, and channel stability. The issue-to-PR ratio (~1.3:1) and 11 closed PRs indicate strong follow-through on open design work.

---

## 2. Releases

No new releases today.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Summary |
|----|---------|
| [#10256](https://github.com/zeroclaw-labs/zeroclaw/pull/10256) | Redact duplicate idempotency keys from gateway logs — fixes a minor information-leak surface. |
| [#10309](https://github.com/zeroclaw-labs/zeroclaw/pull/10309) | Remove orphaned SkillForge engine — cleans up dead code and unused module declarations. |
| [#10314](https://github.com/zeroclaw-labs/zeroclaw/pull/10314) | Bound successful `/models` response body — prevents unbounded buffer allocation from a compromised or misconfigured router. |
| [#10399](https://github.com/zeroclaw-labs/zeroclaw/pull/10399) | Typecheck generated dashboard OpenAPI contract in CI — catches breakage before merge. |
| [#10418](https://github.com/zeroclaw-labs/zeroclaw/pull/10418) | **Telegram reply-threads now stay in main chat history** — closes [#10237](https://github.com/zeroclaw-labs/zeroclaw/issues/10237), a significant context-fragmentation bug. |
| [#9673](https://github.com/zeroclaw-labs/zeroclaw/pull/9673) | Remove 36 unreachable channel re-export files and dead ACP fields — pure refactor. |
| [#10352](https://github.com/zeroclaw-labs/zeroclaw/pull/10352) | Remove unused `async-trait` dep from ZeroCode. |
| [#10365](https://github.com/zeroclaw-labs/zeroclaw/pull/10365) | Remove unused `tokio-socks` dep from channels crate. |
| [#10368](https://github.com/zeroclaw-labs/zeroclaw/pull/10368) | Stabilize stale local IPC cleanup test. |
| [#10377](https://github.com/zeroclaw-labs/zeroclaw/pull/10377) | Gate `axum` dependency by channel features to reduce build surface. |
| [#10387](https://github.com/zeroclaw-labs/zeroclaw/pull/10387) | Fix CI dependency-labeling for nested Cargo manifests. |

**Key advance:** The Telegram conversation-history fix (#10418) is the most impactful merge today, directly restoring multi-turn context integrity for Telegram users.

---

## 4. Community Hot Topics

| Issue | Title | Comments | Why It Matters |
|-------|-------|----------|----------------|
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | RFC: Decouple memory lifecycle from storage backends | 21 | Core architectural tension — operators need predictable consolidation without backend-specific reimplementation. |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) | RFC: Provenance & reply contract for internal agent turns | 16 | Defines how internally-initiated turns (crons, skills) are attributed and bounded — critical for auditability. |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | RFC: Granular sandbox policy | 15 | Resolves a known drift between application-layer and OS-sandbox permissions; high-risk surface. |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Tracker: Maintainer decision queue for RFCs | 14 | Shows RFC throughput is bottlenecked — community is waiting on maintainer triage. |
| [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | RFC: Computer-use desktop screen & input control | 12 | Signals strong interest in headless desktop automation as a first-class capability. |
| [#3566](https://github.com/zeroclaw-labs/zeroclaw/issues/3566) | Tracker: A2A protocol interoperability | 10 · 👍 7 | The most-reacted issue; cross-agent communication is a top user priority. |

**Underlying need:** The community is pushing hard on **bounded, auditable agent autonomy** — internal-turn provenance, sandbox granularity, and cross-agent protocols all reflect a maturing operator base that needs production-grade guarantees.

---

## 5. Bugs & Stability

### P1 Bugs (Severity: S1–S2)

| Issue | Summary | Status | Fix PR |
|-------|---------|--------|--------|
| [#8654](https://github.com/zeroclaw-labs/zeroclaw/issues/8654) | Skill-review fork panic → daemon SIGSEGV after tool-heavy turn | In-progress | — |
| [#9815](https://github.com/zeroclaw-labs/zeroclaw/issues/9815) | `forbidden_paths` silently unreachable under `allowed_roots` | In-progress | — |
| [#9425](https://github.com/zeroclaw-labs/zeroclaw/issues/9425) | No cancel path for running SOP jobs (web dashboard) | Closed | — |
| [#10429](https://github.com/zeroclaw-labs/zeroclaw/issues/10429) | Deepgram/OpenAI drop non-English voice notes (silent skip) | Open | — |
| [#10408](https://github.com/zeroclaw-labs/zeroclaw/issues/10408) | Second message during active turn spawns parallel run → duplicate work | Open | — |
| [#10432](https://github.com/zeroclaw-labs/zeroclaw/issues/10432) | ElevenLabs TTS key header not marked sensitive | Open | — |

### P2 Bugs

| Issue | Summary | Status | Fix PR |
|-------|---------|--------|--------|
| [#10064](https://github.com/zeroclaw-labs/zeroclaw/pull/10064) | Telegram approval cards not self-destructing after operator tap | Open (PR) | PR #10064 in review |

**Assessment:** Security-relevant bugs dominate the open list. The `forbidden_paths` bypass (#9815) is a serious policy violation waiting for a fix. The parallel-run bug (#10408) degrades both performance and cost for active users.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood for Next Release |
|-------|-------------|----------------------------|
| [#10419](https://github.com/zeroclaw-labs/zeroclaw/issues/10419) | Stream agent-loop tokens from `POST /webhook` via SSE | **High** — small surface, clear API contract, hosted-path workers need it. |
| [#10360](https://github.com/zeroclaw-labs/zeroclaw/issues/10360) | Opt-in household edge mesh with pull workers & signed receipts | Medium — ambitious architecture, but aligns with local-first ethos. |
| [#10336](https://github.com/zeroclaw-labs/zeroclaw/issues/10336) | Add AnySearch as built-in `web_search_tool` provider | Medium — single-provider addition, low risk. |
| [#8445](https://github.com/zeroclaw-labs/zeroclaw/issues/8445) | Telegram multi-message mode (one message per turn) | Medium — incremental UX improvement, no backend changes. |
| [#10406](https://github.com/zeroclaw-labs/zeroclaw/issues/10406) | Gemini speech-to-speech broker channel (#8780) | Medium — tracked as an implementation batch; scope is bounded. |

**Predicted next-release candidates:** #10419 (SSE webhook streaming), #10336 (AnySearch provider), and the Telegram multi-message feature (#8445) are the most contained and likely to ship together.

---

## 7. User Feedback Summary

- **Context fragmentation is a real pain point.** The Telegram reply-thread bug (#10237, now fixed in #10418) and the parallel-run bug (#10408) both reflect users losing conversation continuity — a core expectation for personal AI assistants.
- **Non-English voice input silently fails** (#10429). Users relying on Deepgram/OpenAI transcription for Italian, and likely other languages, are getting empty results with no error signal — a trust-eroding experience.
- **SOP job cancel is missing from the dashboard** (#9425). Operators running long automations need explicit stop controls; its absence was rated S1.
- **API key header sensitivity** (#10432, #10175) is a recurring theme. Users want to know their credentials aren't leaking into logs or structured output — two TTS providers were flagged in one week.
- **Cross-agent interoperability** (#3566) has the most 👍 reactions (7), signaling strong user demand for multi-agent workflows.

---

## 8. Backlog Watch

| Issue | Reason for Attention | Age |
|-------|---------------------|-----|
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) | RFC accepted but no implementation PR; memory lifecycle is foundational. | ~3 months |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) | Revision 2 accepted 2026-08-05; no follow-up PR yet. | ~3 months |
| [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) | Sandbox policy RFC in-progress; security-critical, needs maintainer review. | ~3 months |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Maintainer decision queue tracker itself signals RFC backlog pressure. | ~2.5 months |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) | WASM observer capability RFC — needs maintainer review. | ~2 months |
| [#9330](https://github.com/zeroclaw-labs/zeroclaw/issues/9330) | AI-assisted PR pre-review SOP — accepted, awaiting implementation. | ~1.5 months |
| [#8654](https://github.com/zeroclaw-labs/zeroclaw/issues/8654) | P1 SIGSEGV bug, in-progress but no merged fix yet. | ~2 months |
| [#9815](https://github.com/zeroclaw-labs/zeroclaw/issues/9815) | P1 security-policy bypass, in-progress but unfixed. | ~3 weeks |

**Recommendation:** The RFC-to-implementation pipeline is the project's biggest bottleneck. Five high-priority RFCs sit at "accepted" with no implementation PR, while two P1 bugs (#8654, #9815) remain unresolved. Maintainer bandwidth should be the focus of attention in the coming weeks.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*