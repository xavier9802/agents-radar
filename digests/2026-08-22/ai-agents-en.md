# OpenClaw Ecosystem Digest 2026-08-22

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-22 01:36 UTC

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



# OpenClaw Project Digest — 2026-08-22

## 1. Today's Overview

OpenClaw is experiencing a period of intense development activity with **500 issues and 500 PRs updated** in the past 24 hours, signaling a high-velocity maintenance cycle around the `2026.8.1-beta.2` release. The project is under significant stability pressure: **two P0 issues** (gateway memory leak and SQLite corruption) are dominating the top of the tracker, both rated **platinum hermit**. The team is actively hardening the Codex integration and shipping targeted fixes for session-state, auth-provider, and message-delivery regressions. With 114 PRs merged or closed and only a new beta validation track, the project appears to be in a stabilization sprint rather than feature development.

---

## 2. Releases

**No new releases published today.** The current active track is `v2026.8.1-beta.2`, with release validation ongoing in [Issue #125626](https://github.com/openclaw/openclaw/issues/125626). Two SQLite corruption issues ([#126821](https://github.com/openclaw/openclaw/issues/126821), [#125744](https://github.com/openclaw/openclaw/issues/125744)) have emerged specifically in the beta.2 gateway, both describing ptrmap/freelist corruption recursing within 15–24 hours of a pristine rebuild. These are strong signals that a `beta.3` or a patch release may be imminent.

---

## 3. Project Progress

**Notable PRs advanced or merged today:**

- **[#127724](https://github.com/openclaw/openclaw/pull/127724)** — *feat(codex): upgrade to 0.149 and harden the complete app-server integration* (XL, P2). Addresses multiple connected defects in reply delivery, approval enforcement, sandbox isolation, account identity, MCP app authority, session ownership, Guardian visibility, and more. The largest single PR today and a clear priority for the team.
- **[#127739](https://github.com/openclaw/openclaw/pull/127739)** — *fix(agents): preserve authoritative child completion results* (M, maintainer). Fixes stale or lost child turn results in scheduled jobs and multi-subagent scenarios.
- **[#127729](https://github.com/openclaw/openclaw/pull/127729)** — *fix: preserve message-tool images across gateway restarts* (M, P2). Addresses image attachment loss on restart.
- **[#127469](https://github.com/openclaw/openclaw/pull/127469)** — *fix(memory): respect provenance in automatic context* (L, P1). Prevents untrusted memory content from leaking into automatic context.
- **[#126424](https://github.com/openclaw/openclaw/pull/126424)** — *fix(gateway): keep conversation delivery within agent bindings* (XL, P1). Fixes multi-agent conversation tool misuse.
- **[#127735](https://github.com/openclaw/openclaw/pull/127735)** — *fix(telegram): preserve exact inline callback action values* (closed). Fixes silent disappearance of Telegram inline button actions.
- **[#125471](https://github.com/openclaw/openclaw/pull/125471)** — *fix(models): keep Claude CLI OAuth available in Control UI* (closed). Resolves contradictory auth-profile entries after gateway restart.
- **[#127705](https://github.com/openclaw/openclaw/pull/127705)** — *fix(macos): retire targeted Settings tab request on notification admission* (S). Fixes a Settings tab routing bug.
- **[#127740](https://github.com/openclaw/openclaw/pull/127740)** — *fix(ui): stop empty protected secrets before Gateway save* (S). Prevents invalid secret store requests.

---

## 4. Community Hot Topics

| Rank | Issue | Severity | Comments | Theme |
|------|-------|----------|----------|-------|
| 1 | [#91588](https://github.com/openclaw/openclaw/issues/91588) — Gateway Memory Leak (RSS 350MB→15.5GB, OOM crashes) | **P0, platinum hermit** | 23 | Critical production instability |
| 2 | [#91009](https://github.com/openclaw/openclaw/issues/91009) — Codex PreToolUse hook spawns CPU-bound processes, stalls gateway RPC | **P1, platinum hermit** | 22 | Codex integration regression |
| 3 | [#87744](https://github.com/openclaw/openclaw/issues/87744) — Codex-backed Telegram turns timeout waiting for `turn/completed` | **P1, platinum hermit** | 18 | Channel reliability regression |
| 4 | [#125626](https://github.com/openclaw/openclaw/issues/125626) — Release validation: v2026.8.1-beta.2 | P2 | 18 | Release quality gate |
| 5 | [#68596](https://github.com/openclaw/openclaw/issues/68596) — Configurable streaming watchdog timeout | **P2, diamond lobster** | 16, 👍8 | Feature request for long-reasoning models |
| 6 | [#51429](https://github.com/openclaw/openclaw/issues/51429) — Hardcoded `/Users/wangtao` working path in release | **P2, diamond lobster** | 13 | Shocking release-quality bug |
| 7 | [#67777](https://github.com/openclaw/openclaw/issues/67777) — Subagent completion delivery can be lost | **P1, diamond lobster** | 12 | Session-state reliability |
| 8 | [#86215](https://github.com/openclaw/openclaw/issues/86215) — Codex OAuth refresh failures wedge agent for hours | **P1, diamond lobster** | 11 | Auth-provider resilience |

**Analysis:** The community's top concerns cluster around **reliability of the gateway under sustained load** (memory leak, CPU spike from hooks, SQLite corruption) and **auth/Token rotation fragility**. The Codex integration, while popular, is a recurring source of regressions (Issues #91009, #87744, #86215, #123799). The hardcoded-path bug (#51429) with 13 comments and zero 👍 suggests frustration that such a basic check was missed in review.

---

## 5. Bugs & Stability

### P0 — Critical (production-impacting)

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | Gateway RSS grows from 350MB to 15.5GB over 2–3 days → OOM kill → `launchd-handoff` restart loop | No fix PR yet; `clawsweeper-recovery-stuck` |
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite corruption recurs on pristine rebuilt DBs within 15–24h on `beta.2` (WSL2) — 5 events in 5 days, including "paralyzed gateway" mode | No fix PR; `beta.2` regression |
| [#125744](https://github.com/openclaw/openclaw/issues/125744) | State DB ptrmap corruption recurs on `beta.2` — gateway holds unlinked `-shm`; in-place recovery never fires | No fix PR; same root cause as #126821 likely |
| [#124788](https://github.com/openclaw/openclaw/issues/124788) | Event loop blocks ~100s every ~10 min on `beta.2` (anchored timer; string building + fs scan) | No fix PR; `beta.2` regression |

### P1 — High

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | Codex PreToolUse hook spawns CPU-bound `openclaw-hooks` processes, stalls gateway RPC | No fix PR |
| [#87744](https://github.com/openclaw/openclaw/issues/87744) | Codex-backed Telegram turns time out, never reach `turn/completed` | No fix PR |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | Subagent completion delivery lost on direct-announce timeout/drain/orphan prune | No fix PR |
| [#86215](https://github.com/openclaw/openclaw/issues/86215) | Codex OAuth refresh failures wedge agent for hours without alerting | No fix PR |
| [#91931](https://github.com/openclaw/openclaw/issues/91931) | Preseeded SOUL.md/IDENTITY.md causes auto-complete and deletes user `BOOTSTRAP.md` | Linked PR open |
| [#125570](https://github.com/openclaw/openclaw/issues/125570) | Skill Workshop update overwrites live skill description, silently breaking routing | No fix PR |
| [#83598](https://github.com/openclaw/openclaw/issues/83598) | `anthropic:claude-cli` OAuth refresh still dead-ends in `2026.5.12` | No fix PR |
| [#126246](https://github.com/openclaw/openclaw/issues/126246) | Telegram durable outbound deliveries stuck in `send_attempt_started`, lost on restart | No fix PR |

### P2 — Medium

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| [#78865](https://github.com/openclaw/openclaw/issues/78865) | Tool call circuit breaker missing — LLM retries rate-limited APIs forever | No fix PR; feature request framed as bug |
| [#77930](https://github.com/openclaw/openclaw/issues/77930) | Discord channel not loaded in `2026.5.4` (and beta.2/beta.3) | Linked PR open |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Gateway leaks unreaped hook/tool child processes → zombie accumulation | No fix PR |
| [#58957](https://github.com/openclaw/openclaw/issues/58957) | Model switch fails silently when carried-over context is too large | No fix PR |

**Stability Assessment:** The `beta.2` track has **4 confirmed regressions** (SQLite corruption x2, event loop blocking, Discord channel loading), all without published fix PRs. This strongly suggests the next release will be a `beta.3` or a `2026.8.2` patch focused on gateway stability. The memory leak (#91588) and child-process leak (#97616) are long-standing structural issues that will require deeper architectural work.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Popularity | Likelihood |
|-------|---------|------------|------------|
| [#68596](https://github.com/openclaw/openclaw/issues/68596) | Configurable streaming watchdog timeout | 👍8, 16 comments | **High** — growing adoption of long-reasoning models (Kimi K2.5, DeepSeek-R1) makes this urgent |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) | MathJax/LaTeX support in Control UI | 👍10, 8 comments | **Medium** — low engineering cost, high user demand |
| [#50199](https://github.com/openclaw/openclaw/issues/50199) | Skill Priority Configuration | 👍0, 9 comments | **Low–Medium** — overlapping skills problem is real but complex |
| [#71058](https://github.com/openclaw/openclaw/issues/71058) | Multiple Azure/Teams bots on single gateway | 👍1, 8 comments | **Medium** — enterprise demand, config-schema change |
| [#52640](https://github.com/openclaw/openclaw/issues/52640) | Persistent task-status surface for long-running turns | 👍2, 8 comments | **Medium** — improves UX for Discord-first, generic later |
| [#88154](https://github.com/openclaw/openclaw/issues/88154) | Slack Modal Support for interactive workflows | 👍1, 7 comments | **Low** — channel-specific, lower priority vs. stability |
| [#55249](https://github.com/openclaw/openclaw/issues/55249) | Session labels/nicknames | 👍0, 6 comments | **Low** — QoL improvement |
| [#71195](https://github.com/openclaw/openclaw/issues/71195) | OpenAI Realtime (speech-to-speech) for Talk Mode | 👍1, 6 comments | **Medium** — parity gap with `voice-call` plugin |
| [#47606](https://github.com/openclaw/openclaw/issues/47606) | Execution anti-drift guards (artifact-gated status, escalation timers) | 👍0, 5 comments | **Medium** — multi-batch execution reliability |
| [#45771](https://github.com/openclaw/openclaw/issues/45771) | Built-in pace-aware rate limiting for autonomous agents | 👍2, 7 comments | **Medium** — directly addresses API-cost control |

**Prediction:** The configurable watchdog timeout (#68596) and session labels (#55249) are strong candidates for the next minor release. MathJax support (#42840) is a low-effort win that could ship quickly. The multi-bot Teams feature (#71058) and rate limiting (#45771) are more substantial and likely deferred to a later milestone.

---

## 7. User Feedback Summary

**Pain points dominating user reports:**

1. **Gateway instability under production load** — Users report the gateway becoming unusable after days of operation due to memory leaks (#91588) and SQLite corruption (#126821, #125744). The "paralyzed gateway" mode described in #126821 — refusing all service without exiting — is particularly alarming for production deployments.

2. **Codex integration fragility** — Three separate issues this cycle (#91009, #87744, #86215) all trace back to the Codex plugin: CPU-spinning hooks, Telegram turn timeouts, and OAuth refresh wedging. Users running Codex-backed agents are experiencing degraded reliability.

3. **Auth-provider brittleness** — Beyond Codex OAuth, the `anthropic:claude-cli` OAuth refresh remains broken in production (#83598) despite a prior fix attempt (#73682). This suggests systemic issues in the auth-profile rotation logic that affects multiple providers.

4. **Silent data loss** — Issues #67777 (subagent completion lost), #126246 (Telegram durable delivery lost), and #53408 (write/exec params silently dropped after long conversations) all share a pattern: the agent appears to succeed but the result never reaches the user. This erodes trust in the platform's reliability guarantees.

5. **Release-quality oversight** — The hardcoded `/Users/wangtao` path in #51429 that made it into a published release has generated frustration (13 comments, 0 👍). Users are questioning review rigor.

**Satisfaction signals:** The project has active maintenance — 114 PRs closed/merged in 24h is strong throughput. The `clawsweeper` bot is engaged across many issues, and multiple PRs were opened today by core maintainers (`steipete`, `joshavant`, `chelsealong`), indicating the team is responsive.

---

## 8. Backlog Watch

These issues are high-impact but remain open without fix PRs or have been stuck for extended periods:

| Issue | Age | Why It's Stuck | Risk |
|-------|-----|-----------------|------|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | ~75 days | `claws

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent Ecosystem Digest
**Date:** 2026-08-22 · **Compiled by:** Agnes (Sapiens AI)

---

## 1. Ecosystem Overview

The personal AI assistant open-source landscape in August 2026 is characterized by a maturity inflection point: projects are transitioning from novel single-agent prototypes to production-grade multi-channel platforms. Security hardening, MCP protocol pluggability, and long-session reliability have emerged as the dominant engineering concerns across all tracks. Community velocity varies dramatically — from daily patch cycles to weeks of quiet maintenance — reflecting divergent project scopes ranging from full desktop agents to lightweight provider-routing layers. The ecosystem shows clear segmentation between monolithic platforms (OpenClaw, Hermes, CoPaw) and specialized utility projects (NullClaw, PicoClaw, ZeptoClaw).

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Merged/Closed | Releases | Health Score |
|---------|-------------|-----------|---------------|----------|-------------|
| **ZeroClaw** | 50 | 50 | — | None | 🔴 8.5 |
| **CoPaw** | 34 | 34 | 3 | v2.1.1-beta.1 | 🔴 8.0 |
| **OpenClaw** | 500 | 500 | 114 | v2026.8.1-beta.2 | 🟡 6.5 |
| **IronClaw** | 15 | 35 | 10 | None | 🟡 7.5 |
| **Hermes Agent** | 50 | 50 | 4 | v0.20.5 (Aug 19) | 🟢 8.0 |
| **NanoBot** | 5 | 38 | 24 | None | 🟢 7.5 |
| **NanoClaw** | 1 | 24 | 11 | None | 🟢 7.5 |
| **LobsterAI** | 2 | 13 | 12 | release/2026.8.21 | 🟡 6.5 |
| **Moltis** | 2 | 8 | 1 | None | 🟡 6.0 |
| **PicoClaw** | 0 | 3 | 3 | None | 🟡 5.0 |
| **NullClaw** | 0 | 1 | 0 | None | 🟡 4.5 |
| **ZeptoClaw** | 0 | 0 | 0 | None | 🟡 3.5 |

*Health scores reflect development velocity, issue triage responsiveness, and stability posture.*

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale and scope:** OpenClaw is the only project running a 500-issue/500-PR daily cycle at this magnitude, indicating the broadest community footprint and the most comprehensive feature surface (Codex integration, multi-agent orchestration, 10+ channel adapters).
- **MCP-first architecture:** OpenClaw's MCP (Model Context Protocol) integration is the most mature in the ecosystem, with dedicated memory-provenance controls and authority-isolation layers.

**Technical approach differences:**
- Unlike Hermes (proof-carrying state, architecture-first) or NanoBot (Dream runner, typed LLMUsage contracts), OpenClaw prioritizes breadth of channel support and integration depth over architectural purity.
- OpenClaw's gateway-centric model (SQLite-backed state, event-loop scheduling) contrasts with ZeroClaw's daemon-centric approach and CoPaw's Docker/runtime-isolated model.

**Community size comparison:**
- OpenClaw has ~10× the daily PR throughput of its nearest large competitor (CoPaw), but this volume is disproportionately consumed by P0 stability issues (memory leak, SQLite corruption) rather than feature development — a sign of platform growing pains rather than healthy momentum.

---

## 4. Shared Technical Focus Areas

| Requirement | Projects Involved | Specific Needs |
|-------------|------------------|----------------|
| **Multi-channel messaging parity** | OpenClaw, Hermes, NanoBot, NanoClaw, ZeroClaw, Moltis, LobsterAI | WhatsApp, Telegram, Slack, Discord, DingTalk — with reliable delivery guarantees |
| **Cron/scheduled agent reliability** | OpenClaw, Hermes, NanoBot, Moltis, LobsterAI | Heartbeat active-hours enforcement, durable job persistence, output routing to originating chat |
| **MCP protocol integration** | OpenClaw, Hermes, IronClaw, CoPaw, PicoClaw | Pluggable memory providers, tool discovery after restart, secure capability mediation |
| **Session/memory reliability** | OpenClaw, Hermes, CoPaw, ZeroClaw | Proof-carrying state, durable delegation IDs, cross-session memory isolation, history pruning |
| **Security sandboxing** | ZeroClaw, IronClaw, NanoClaw, OpenClaw | Risk-profile enforcement (no delegate bypass), command allowlisting, sandbox credential mediation |
| **Auth-provider resilience** | OpenClaw, Hermes, ZeroClaw | OAuth refresh recovery, multi-provider token rotation, graceful degradation on auth failure |
| **Streaming & context awareness** | OpenClaw, Hermes, CoPaw, ZeroClaw | Configurable watchdog timeouts, context-window budget hints, progressive streaming defaults |
| **Long-session durability** | OpenClaw, Hermes, CoPaw, ZeroClaw | Memory-leak prevention, SQLite corruption avoidance, WebView2/desktop process stability |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | ZeroClaw | CoPaw | NanoBot | NanoClaw |
|-----------|----------|-------------|----------|-------|---------|----------|
| **Target user** | Enterprise/production agent ops | Research/developer-grade agents | Security-conscious deployments | Multi-user self-hosted teams | Developers, AI researchers | Channel-focused integration builders |
| **Architecture** | Gateway + event loop + SQLite | Proof-carrying state + Bot Mode control plane | Daemon supervisor + Tokio runtime | Docker/runtime-isolated sessions | Dream runner + typed trajectory | Registry-backed skill system |
| **Key differentiator** | Breadth of channel integrations | Architectural correctness & provenance | Security sandbox fidelity | Multi-user Hub + Creator 1.1 | Memory cursor + cron precision | Template-from-chat agent creation |
| **Language** | TypeScript/Node | TypeScript/Python | Rust | Python | Python | TypeScript |
| **Deployment model** | Self-hosted gateway | Docker + desktop | Daemon (Linux/Windows/macOS) | Docker + desktop | Docker + desktop | CLI + desktop |
| **Maturity signal** | Large bug backlog, stabilization sprint | Post-release consolidation | Active security remediation | High velocity, beta-release cycle | Steady hardening | Channel integration polish |

---

## 6. Community Momentum & Maturity

**Tier 1 — High Velocity (rapid iteration):**
- **ZeroClaw** (50/50) and **CoPaw** (34/34) are in aggressive release cycles with parallel fix streams.
- **OpenClaw** (500/500) has the highest volume but is in a stabilization sprint consumed by P0 bugs — momentum is present but directionally corrective.

**Tier 2 — Active Maintenance (steady cadence):**
- **Hermes Agent** (50/50) is post-release, consolidating v0.20.5 with architectural PRs advancing.
- **IronClaw** (15/35) is investing in CI hardening and WebUI standardization.
- **NanoBot** (5/38) shows high PR throughput with low issue volume — healthy signal.

**Tier 3 — Moderate Activity (targeted fixes):**
- **NanoClaw** (1/24) is in pre-release polish for channel integrations.
- **LobsterAI** (2/13) is in iterative maintenance with DSH runtime experiments.
- **Moltis** (2/8) is small-team, focused on gateway and cron reliability.

**Tier 4 — Quiet/Stable (low current activity):**
- **PicoClaw** (0/3), **NullClaw** (0/1), **ZeptoClaw** (0/0) are in maintenance or niche-mode. NullClaw's provider integration PR (#990) suggests continued but slow evolution.

---

## 7. Trend Signals

**For AI agent developers:**

1. **Reliability over features is the winning strategy.** The top community pain points across OpenClaw, Hermes, CoPaw, and ZeroClaw are not missing features — they are gateway memory leaks, SQLite corruption, session data loss, and auth-provider wedging. Projects that ship stable gateways will retain production users.

2. **Security sandbox correctness is a trust multiplier.** ZeroClaw's delegate risk-profile bypass (#10165) and OpenClaw's memory-leak-driven OOM crashes are user-trust killers. IronClaw's sandbox-mediated GitHub CLI credentials and proof-carrying state architecture (Hermes #90866) represent the direction the ecosystem is heading.

3. **Multi-channel parity is table stakes, not differentiators.** Every major project ships Telegram, Slack, WhatsApp, and Discord. The differentiating factor is *delivery guarantee* (durable outbound, no silent message loss) rather than platform count.

4. **MCP pluggability is becoming a core abstraction.** Projects that treat MCP as a first-class protocol layer (OpenClaw, Hermes, PicoClaw) are better positioned for the growing ecosystem of memory providers, tool servers, and routing gateways.

5. **Long-session durability is the unsolved frontier.** Memory bloat (CoPaw's 7.6 GB history.db), SQLite corruption (OpenClaw), and context-window misconfiguration (ZeroClaw's 32k cap) are indicators that the ecosystem has not yet solved sustained multi-day agent operation. This is the highest-value engineering opportunity.

6. **Config fidelity matters.** Users are frustrated when configured limits (`max_context_tokens`, `max_tool_result_chars`, `block_high_risk_commands`) are silently ignored. Projects that honor configuration as a correctness invariant will earn operational trust.

7. **Streaming and context awareness are table stakes for long-reasoning models.** Configurable watchdog timeouts (OpenClaw #68596), context-window budget hints (Hermes #91974), and partial streaming defaults (ZeroClaw #10166) are converging features demanded by the adoption of DeepSeek-R1, Kimi K2.5, and similar models.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-22

## 1. Today's Overview
NanoBot is operating at high development velocity with 38 PRs and 5 issues updated in the past 24 hours, and 24 PRs merged or closed. The dominant theme today is platform hardening and autonomous agent reliability, with focused fixes on the Dream runner, Telegram polling, streaming retry logic, and cron job persistence. No new releases were published today, but the merge volume and targeted stabilization work suggest an upcoming release candidate is being prepared. Project health indicators are strong, with rapid maintainer triage and active community contribution.

## 2. Releases
None.

## 3. Project Progress
**Merged / Closed PRs (24 in 24h)**
- **Agent Reliability:** [#5442](https://github.com/HKUDS/nanobot/pull/5442) fixes Dream runs from permanently blocking the memory cursor when recoverable tool errors occur. [#5407](https://github.com/HKUDS/nanobot/pull/5407) ensures heartbeat/dream cron jobs are retired when disabled, stopping token burn.
- **Provider & Usage Tracking:** [#5478](https://github.com/HKUDS/nanobot/pull/5478) and [#5479](https://github.com/HKUDS/nanobot/pull/5479) ship a typed `LLMUsage` contract and unified trajectory backend, normalizing token/cache metrics across OpenAI, Anthropic, and Bedrock wire boundaries.
- **Channel & Platform Hardening:** [#5156](https://github.com/HKUDS/nanobot/pull/5156) recovers from silently stalled Telegram polling. [#5414](https://github.com/HKUDS/nanobot/pull/5414) validates Slack file downloads across redirect chains. [#5477](https://github.com/HKUDS/nanobot/pull/5477) fixes iOS PWA control placement and theme synchronization.
- **Desktop & UI:** [#1592](https://github.com/HKUDS/nanobot/pull/1592) finalizes Lumina Windows app packaging and installer flow. [#2063](https://github.com/HKUDS/nanobot/pull/2063) completes the Tauri v2 desktop shell with PyInstaller sidecar. [#5476](https://github.com/HKUDS/nanobot/pull/5476) renders LaTeX math as Unicode in the TUI.

## 4. Community Hot Topics
- **[#5441](https://github.com/HKUDS/nanobot/issues/5441) / [#5442](https://github.com/HKUDS/nan

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-22

---

## 1. Today's Overview

Hermes Agent is in a high-velocity patch-and-stabilize phase following the v0.20.5 release (Aug 19), which consolidated approximately 323 merged PRs into a stable tagged release. Activity remains intense: 50 issues and 50 PRs were updated in the last 24 hours, with the majority still open, indicating rapid iteration on both new architecture work and a stream of bug fixes. Maintainers are pushing a coherent reliability campaign focused on proof-carrying state, durable session identifiers, and authority interlocks across agent, gateway, and desktop components. The project shows strong health with balanced front-to-back engagement—no sign of contributor fatigue, though the open-issue backlog continues to grow.

---

## 2. Releases

**v0.20.5 (v2026.8.19)** — Patch release, August 19, 2026.

- Rolls up ~323 PRs merged since v0.20.4 into a stable tagged release.
- Targeted at downstream consumers: Docker images, hosted deployments, fresh installs.
- **Breaking changes:** None declared; classified as a patch release.
- **Migration notes:** Standard upgrade path via `hermes update`. Users on prior v0.20.x versions should upgrade to benefit from the consolidated bug and reliability fixes.

---

## 3. Project Progress

**Merged / Closed today (4 PRs):**

| PR | Summary |
|---|---|
| [#91972](https://github.com/NousResearch/hermes-agent/pull/91972) | Distinguish I/O errors from auth failures in provider resolution (`gateway/platforms/api_server.py`) |
| [#91970](https://github.com/NousResearch/hermes-agent/pull/91970) | Allow `max_spawn_depth=0` to disable subagent spawning (fixed silent coercion to 1) |
| [#91979](https://github.com/NousResearch/hermes-agent/issues/91979) | Duplicate of #47509 — configured MCP silently disabled when SDK missing |

**Actively advancing (open PRs):**

- [#91917](https://github.com/NousResearch/hermes-agent/pull/91917) — **Bot Mode shadow control plane** (Phase 1): introduces `BotAddress`, `BotExecutionContext`, and `RuntimeCapabilitySnapshot` as typed seam for identity and authority.
- [#91981](https://github.com/NousResearch/hermes-agent/pull/91981) — **Kanban Docker workspaces** made task-scoped and host-backed, fixing stale bind-mount contracts.
- [#91974](https://github.com/NousResearch/hermes-agent/pull/91974) — **Context-window budget hint injection** (adapted from openai/codex): advisory line on remaining room to prevent forced truncation.
- [#91963](https://github.com/NousResearch/hermes-agent/pull/91963) — **Durable child attribution IDs** exposed in delegation results (`delegation_id`, `subagent_id`, `child_session_id`).
- [#91913](https://github.com/NousResearch/hermes-agent/pull/91913) — **Proof-carrying authority interlocks** installed as an executable repository contract for architecture rule #90866.
- [#91906](https://github.com/NousResearch/hermes-agent/pull/91906) — **P0 dependency-security remediation** on current main (restacking advisory fixes).

---

## 4. Community Hot Topics

| Issue / PR | Comments | Status | Focus |
|---|---|---|---|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — God-file decomposition epic | 78 | ✅ Closed | Repo-wide architectural sharding |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale/degraded | 72 | 🔵 Open | Automated freshness probe, cron reliability |
| [#90473](https://github.com/NousResearch/hermes-agent/issues/90473) — "Show earlier messages" UX broken on long sessions | 11 | 🔵 Open | Desktop pagination UX regression |
| [#68592](https://github.com/NousResearch/hermes-agent/issues/68592) — Cron agents forced kanban protocol | 10 | 🔵 Open | Cross-component protocol leakage |
| [#79564](https://github.com/NousResearch/hermes-agent/issues/79564) — Discord Feature Parity Campaign (API v10) | 9 | 🔵 Open | Platform alignment meta-issue |
| [#79890](https://github.com/NousResearch/hermes-agent/issues/79890) — WhatsApp Feature Parity Campaign | 8 | 🔵 Open | Platform alignment meta-issue |
| [#91277](https://github.com/NousResearch/hermes-agent/issues/91277) — Fleet update reliability tracking | 7 | 🔵 Open | Cross-platform install/update coherence |
| [#90866](https://github.com/NousResearch/hermes-agent/issues/90866) — Observable state proof-carrying architecture | 7 | 🔵 Open | Core reliability invariant |

**Analysis:** The top-commented issues reveal two dominant community concerns: (1) **platform parity** — Discord, WhatsApp, and Slack campaigns are active meta-issues signaling that Hermes is pushing hard to match native-bot feature sets across messaging surfaces. (2) **reliability & state correctness** — issues around skills-index freshness, cron protocol leakage, and proof-carrying state architecture indicate the community and maintainers are aligning around a "correctness-first" design philosophy for long-running agent sessions.

---

## 5. Bugs & Stability

**Reported today, ranked by severity:**

| Severity | Issue | Summary | Fix PR? |
|---|---|---|---|
| 🔴 **P2** | [#91675](https://github.com/NousResearch/hermes-agent/issues/91675) | Windows: gateway prints ✓ then dies after 6s liveness poll; post-update cold-start only resumes active profile | ⏳ Open (#91981 tracks related Docker fix) |
| 🔴 **P2** | [#89083](https://github.com/NousResearch/hermes-agent/issues/89083) | macOS: chat window permanently unresponsive after sleep/wake (half-open WebSocket never detected) | ⏳ Open |
| 🔴 **P2** | [#63277](https://github.com/NousResearch/hermes-agent/issues/63277) | WhatsApp bridge `/health` reports `connected` during Baileys WS flapping, causing silent message loss | ⏳ Open |
| 🟡 **P2** | [#47509](https://github.com/NousResearch/hermes-agent/issues/47509) | MCP discovery failures logged at DEBUG only — invisible at default log level | ✅ Fixed in [#91979](https://github.com/NousResearch/hermes-agent/issues/91979) (duplicate noted) |
| 🟡 **P2** | [#88758](https://github.com/NousResearch/hermes-agent/issues/88758) | Compression: raw durable watermark lost through replay cleanup / alternation repair | ⏳ Open |
| 🟡 **P2** | [#88740](https://github.com/NousResearch/hermes-agent/issues/88740) | Compression: durable row-ID watermarks discarded across child, CLI, and ACP restores | ⏳ Open |
| 🟡 **P2** | [#76385](https://github.com/NousResearch/hermes-agent/issues/76385) | Buzz gateway connected but agent appears offline (no presence publish) | ⏳ Open |
| 🟡 **P2** | [#90200](https://github.com/NousResearch/hermes-agent/issues/90200) | GitHub automation split authority: metadata writes succeed, repo-object writes fail (403) | ⏳ Open |
| 🟢 **P3** | [#50871](https://github.com/NousResearch/hermes-agent/issues/50871) | Desktop Markdown renders lone `~` as strikethrough — breaks ranges like `1~10,11~20` | ⏳ Open |
| 🟢 **P3** | [#82851](https://github.com/NousResearch/hermes-agent/issues/82851) | HUD drag broken on Linux/Wayland — `setPosition` is a no-op | ⏳ Open |
| 🟢 **P3** | [#87041](https://github.com/NousResearch/hermes-agent/issues/87041) | WhatsApp setup guide links to `whatsmeow` (Go) but bridge is actually Node/Baileys | ⏳ Open |

**Notable regression:** [#91675](https://github.com/NousResearch/hermes-agent/issues/91675) is a follow-up to #84185 (closed Aug 15) — the 6s liveness poll fix introduced a new Windows-specific cold-start symptom. This suggests the Windows service-spawn path needs targeted attention.

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Description | Likelihood for Next Release |
|---|---|---|
| [#91277](https://github.com/NousResearch/hermes-agent/issues/91277) | **Fleet update reliability** — single deployment plan for local, multi-profile, remote, and image-managed installs | High — P1 tracking issue, ~30 open sub-issues |
| [#90866](https://github.com/NousResearch/hermes-agent/issues/90866) | **Proof-carrying observable state** — state provenance from source to side effect | High — architectural foundation driving multiple sub-PRs |
| [#91230](https://github.com/NousResearch/hermes-agent/issues/91230) | **Task completion verification** — exact-object completion as a sixth Hermes law | Medium — architecture publication, needs decision |
| [#90049](https://github.com/NousResearch/hermes-agent/issues/90049) | **False success as first-class defect** — typed completion proofs | Medium — closely tied to #90866 |
| [#91911](https://github.com/NousResearch/hermes-agent/issues/91911) | **Bot Mode unified control plane** — identity, capability, delivery, cancellation | High — PR #91917 already in progress (Phase 1) |
| [#91974](https://github.com/NousResearch/hermes-agent/pull/91974) | **Context-window budget hints** — advisory line for model | Medium-High — PR open, adapted from Codex |
| [#91963](https://github.com/NousResearch/hermes-agent/pull/91963) | **Durable delegation IDs** | Medium-High — PR open, improves auditability |
| [#89418](https://github.com/NousResearch/hermes-agent/pull/89418) | **Rationale-attached provenance for MEMORY_GUIDANCE** | Medium — adds `[why: ...]` tail convention to durable memory |

**Roadmap inference:** The next release (likely v0.21.0) will probably foreground: (1) proof-carrying state infrastructure, (2) Bot Mode control-plane unification, (3) context-window budget awareness, and (4) improved fleet update reliability. The "Hermes laws" publication campaign (#91230) suggests the project is also investing in developer-facing architectural documentation.

---

## 7. User Feedback Summary

| Theme | Source | Signal |
|---|---|---|
| **Pain: Long-session pagination UX** | [#90473](https://github.com/NousResearch/hermes-agent/issues/90473) — Windows 11, ~900-message session | User called the "show earlier messages" design "stupid"; real friction on desktop for power users with long histories |
| **Pain: Silent message loss on WhatsApp** | [#63277](https://github.com/NousResearch/hermes-agent/issues/63277) | Health endpoint lies during WebSocket flapping; messages lost without error — critical for production WhatsApp deployments |
| **Pain: macOS sleep/wake kills chat** | [#89083](https://github.com/NousResearch/hermes-agent/issues/89083) | Half-open WebSocket never detected; requires full app relaunch — significant desktop UX regression |
| **Pain: Markdown `~` renders as strikethrough** | [#50871](https://github.com/NousResearch/hermes-agent/issues/50871) | Breaks number ranges (`1~10,11~20`); small but frequent complaint with 1 👍 |
| **Pain: HUD non-draggable on Wayland** | [#82851](https://github.com/NousResearch/hermes-agent/issues/82851) | Linux/KDE Plasma 6 users cannot reposition HUD; `setPosition` is a no-op under Wayland compositors |
| **Satisfaction: Cron agent reliability** | [#68592](https://github.com/NousResearch/hermes-agent/issues/68592) | Users running scheduled cron agents are hitting protocol leakage; signals active use of automation features |
| **Satisfaction: Discord/WhatsApp/Slack parity demand** | [#79564](https://github.com/NousResearch/hermes-agent/issues/79564), [#79890](https://github.com/NousResearch/hermes-agent/issues/79890), [#79772](https://github.com/NousResearch/hermes-agent/issues/79772) | Multiple active campaign meta-issues show strong community investment in multi-platform deployment |

**Overall sentiment:** Users are deeply engaged with Hermes in production scenarios (long sessions, cron automation, multi-platform messaging). The most acute pain points cluster around **session durability across platform boundaries** (macOS sleep, Windows post-update, Wayland) and **reliable message delivery** (WhatsApp health falseness). These are trust-critical issues for an agent platform.

---

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale/degraded | ~35 days | 72 comments; automated freshness probe failing; affects `/docs/skills` for all users |
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — God-file decomposition (just closed) | ~18 days | Recently closed (Aug 21); likely to surface follow-up issues requiring triage |
| [#91277](https://github.com/NousResearch/hermes-agent/issues/91277) — Fleet update reliability | 1 day | P1 tracking; ~30 open sub-issues and ~15 PRs; no unified plan yet |
| [#90866](https://github.com/NousResearch/hermes-agent/issues/90866) — Proof-carrying observable state | 2 days | Architecture meta-issue; 7 comments; decisions needed on scope and rollout |
| [#63277](https://github.com/NousResearch/hermes-agent/issues/63277) — WhatsApp silent message loss | ~41 days | P2; no fix PR yet; critical for WhatsApp bridge users |
| [#89083](https://github.com/NousResearch/hermes-agent/issues/89083) — macOS sleep/wake unresponsive | 4 days | P2; no fix PR yet; desktop users on macOS affected |
| [#90200](https://github.com/NousResearch/hermes-agent/issues/90200) — GitHub automation split authority | 3 days | P2; security-relevant (403 on repo writes vs metadata writes); no fix PR yet |

**Maintainer note:** Issues #63277 and #89083 are both P2 reliability bugs with no active fix PRs despite significant comment engagement. The WhatsApp issue in particular has been open for 41 days and affects message delivery guarantees — a high-priority candidate for the next patch cycle.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-22

## 1. Today's Overview

PicoClaw activity on 2026-08-22 is moderate but productive. Three pull requests were closed/merged within the last 24 hours, while no new issues were opened and no new releases were published. The project is making incremental improvements to its tooling layer and protocol support, with a notable feature request emerging around steering mode behavior. Overall project health is stable — maintainers are actively reviewing contributions, and community engagement is steady.

## 2. Releases

No new releases were published today. The latest release information is unavailable from the current data set.

## 3. Project Progress

Three PRs were closed/merged, advancing different aspects of the project:

- **PR #647** — *Improve WebFetchTool text extraction with HTML entity decoding and structure preservation* (`liangzhang-keepmoving`). Enhanced the `WebFetchTool` to properly decode HTML entities (`&amp;`, `&lt;`, `&gt;`, `&quot;`, etc.) and preserve content structure with block-level newlines. This improves the reliability of web-scraping workflows where malformed or entity-encoded content was previously difficult to parse. [View PR](https://github.com/sipeed/picoclaw/pull/647)

- **PR #1182** — *Add agents.md* (`bumu`). Refined the `AGENTS.md` repository guide to be more principle-based and lightweight for AI agents and contributors. Updates include clarifying the principle-first approach and adopting `go.mod` as the source of truth for Go versioning. [View PR](https://github.com/sipeed/picoclaw/pull/1182)

- **PR #1158** — *Add anthropic-messages protocol for native Anthropic API format* (`hyperwd`). Added support for the `anthropic-messages` protocol prefix, enabling direct use of Anthropic's native Messages API (`/v1/messages` endpoint). Fixes [#269](https://github.com/sipeed/picoclaw/issues/269), resolving a long-standing limitation where Anthropic-compatible proxy services could not be used. [View PR](https://github.com/sipeed/picoclaw/pull/1158)

## 4. Community Hot Topics

- **Issue #3342** — *Opt-in "after-turn" steering mode: queue busy-session messages instead of interrupting the running turn* (`unedtamps`). This is the only open issue and the most-discussed item today. Users are frustrated by the current steering design that treats a second incoming message during an active turn as a mid-task course correction, causing skipped tool calls and disruption. The proposed opt-in queueing model would preserve in-flight work and process messages sequentially. This reflects a broader community need for **predictable, non-interruptive conversation flow** in agent sessions — particularly important for complex multi-step tool use. [View Issue](https://github.com/sipeed/picoclaw/issues/3342)

## 5. Bugs & Stability

No new bugs, crashes, or regressions were reported today. The closed PRs (#647, #1158) address capability gaps rather than defects, though PR #1158 does fix issue #269 (inability to use Anthropic-native API format services), which could be classified as a functionality bug for users of such proxies.

## 6. Feature Requests & Roadmap Signals

- **Issue #3342** (after-turn steering mode queue) is the strongest roadmap signal today. The request for an opt-in sequential message queue indicates users are hitting friction with the current interrupt-based steering model during complex agent interactions. If adopted, this could become a significant UX improvement for multi-turn tool-heavy workflows. It may appear in a future release as a configuration option rather than a default behavior change.

- **PR #1158** (Anthropic Messages protocol) was recently merged and addresses a gap that many users of Anthropic-compatible proxy services have faced. This signals that protocol extensibility remains a priority area for the project.

## 7. User Feedback Summary

- **Pain Point — Steering Interruption:** Users sending a second message during an active agent turn experience abrupt cancellation of in-progress tool calls, leading to incomplete results and confusion. The phrasing "Skipped due to queued user message" in logs suggests this behavior is not well-communicated to end users. [Issue #3342](https://github.com/sipeed/picoclaw/issues/3342)

- **Pain Point — Anthropic Proxy Compatibility:** Users relying on Anthropic-compatible proxy services (e.g., various third-party API gateways) were unable to use them natively. The merged PR #1158 resolves this, indicating the community values flexibility in LLM provider routing.

- **Satisfaction — Documentation & Agent Guidance:** The refined `AGENTS.md` (PR #1182) suggests contributors appreciate clearer, principle-based onboarding rather than rigid checklists.

## 8. Backlog Watch

- **Issue #269** — Fixed by PR #1158 (merged). No longer in backlog.
- **Issue #3342** — Currently open with 0 comments and 0 reactions since creation on 2026-08-21. This is a significant feature request that has not yet garnered maintainer attention. Given the volume of tool-call interruptions described, this is a **high-priority backlog item** that warrants early maintainer review. [View Issue](https://github.com/sipeed/picoclaw/issues/3342)

---

*Data sourced from GitHub API as of 2026-08-22. Project: [sipeed/picoclaw](https://github.com/sipeed/picoclaw)*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-22

## 1. Today's Overview

NanoClaw is experiencing a high-velocity development day with 24 PRs updated in the last 24 hours (13 open, 11 merged/closed) and only 1 open issue, signaling a healthy code-review pipeline with strong commit throughput. The dominant theme is multi-channel setup hardening—particularly around Telegram multi-bot support, Slack template flows, and Dial skill stabilization—suggesting the team is in a pre-release polish phase for channel integrations. No new releases were published today, though several merged PRs touch container tooling (Claude Code bumped to 2.1.238) and CI reliability, which typically precede a version bump. Overall project health is strong: high merge rate, focused integration work, and minimal open issue backlog.

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

### Merged / Closed PRs Today

- **[PR #3433](https://github.com/nanocoai/nanoclaw/pull/3433)** — Fixed `/add-dial-number` skill to use NC directives instead of raw prose shell blocks, bringing registry discovery in line with other skills.
- **[PR #3439](https://github.com/nanocoai/nanoclaw/pull/3439)** — Bumped `claude-code` CLI from 2.1.197 → 2.1.238 and `@anthropic-ai/claude-agent-sdk` from ^0.3.197 → ^0.3.238 in the agent container.
- **[PR #3424](https://github.com/nanocoai/nanoclaw/pull/3424)** — Added CI tests for registry-backed skills, ensuring each `add-*` skill builds and tests against a pinned registry snapshot.
- **[PR #3403](https://github.com/nanocoai/nanoclaw/pull/3403)** — Fixed Matrix adapter ESM imports for Node 22 compatibility via a committed pnpm patch.
- **[PR #3402](https://github.com/nanocoai/nanoclaw/pull/3402)** — Fixed provider file-event acceptance in registry-backed skills.
- **[PR #3401](https://github.com/nanocoai/nanoclaw/pull/3401)** — Patched `add-whatsapp-cloud` skill payload to remain compatible with the main codebase.
- **[PR #3430](https://github.com/nanocoai/nanoclaw/pull/3430)** — Restored the stable CI required-check that was broken by Node 22/24 matrix naming (`ci (22)` / `ci (24)` vs. `ci`).
- **[PR #3429](https://github.com/nanocoai/nanoclaw/pull/3429)** — Ratified the driver `attach` surface: `SessionExecSpec { bin, argsTty, argsPlain }` now declaratively describes exec invocations for interactive terminal attachment.
- **[PR #3202](https://github.com/nanocoai/nanoclaw/pull/3202)** — Added Mattermost as a Chat SDK channel, following the Slack adapter pattern and wrapping the community `chat-adapter-mattermost` package.
- **[PR #3050](https://github.com/nanocoai/nanoclaw/pull/3050)** — Added Dial to the channel picker and wizard (`runChannelSkill` model).
- **[PR #3436](https://github.com/nanocoai/nanoclaw/pull/3436)** — Added named Telegram bot instances via `TELEGRAM_INSTANCES` with instance-bound pairing (closed after merge).

### Key Advancements

- **Multi-Telegram-bot support** is now complete end-to-end: PR #3436 (core), #3438 (wizard UX), #3437 (docs), #3435 (adapter wiring), and #3431 (pairing card fix) form a cohesive feature set.
- **Template-from-chat agents** (PR #3396) and its Slack re-port (PR #3428) advance the vision of creating agents interactively without leaving the chat UI.
- **CI robustness** improved through registry-skill tests and the CI required-check restoration.

---

## 4. Community Hot Topics

### Most Discussed / Active

1. **[Issue #3426](https://github.com/nanocoai/nanoclaw/issues/3426)** — *send_card docs promise callback buttons that the bridge drops since #2265; agents blame the platform*
   - **Why it matters:** This is the only open issue and highlights a real trust gap: the SDK documentation tells agents that `actions` (buttons) are supported, but the bridge silently drops action items without a `url`, causing agents to misreport platform limitations to end users. The `fallbackText` hint is ambiguous and doesn't guide the agent to a graceful degradation path. This needs a docs + bridge behavior fix to align agent expectations with actual platform capabilities.

2. **[PR #3396](https://github.com/nanocoai/nanoclaw/pull/3396)** — *Create agents from templates in chat*
   - Gaining traction as a coreUX feature; the Slack follow-up (PR #3428) shows cross-channel demand for template-driven agent creation.

3. **[PR #3287](https://github.com/nanocoai/nanoclaw/pull/3287)** — *Strip agent-group suffix from inbound platform message ID*
   - Addresses a message-deduplication bug (fixes #3153) where `getMessageIdBySeq()` returned unstripped IDs, potentially causing duplicate-processing in group-channel scenarios.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| **High** | [Issue #3426](https://github.com/nanocoai/nanoclaw/issues/3426) | `send_card` bridge drops `actions` without `url` since #2265; agents incorrectly report platform limitations to users | No fix PR yet |
| **Medium** | [PR #3434](https://github.com/nanocoai/nanoclaw/pull/3434) | Polling adapters fail to start the webhook server | Open fix PR #3434 |
| **Medium** | [PR #3287](https://github.com/nanocoai/nanoclaw/pull/3287) | Inbound message IDs retain agent-group suffix, breaking deduplication | Open fix PR #3287 |
| **Low** | [PR #3431](https://github.com/nanocoai/nanoclaw/pull/3431) | Telegram pairing card displayed wrong digit count (6 instead of actual) | Merged |
| **Low** | [PR #3403](https://github.com/nanocoai/nanoclaw/pull/3403) | Matrix adapter ESM imports fail under Node 22 | Merged |
| **Low** | [PR #3430](https://github.com/nanocoai/nanoclaw/pull/3430) | CI required-check `ci` never satisfied due to Node-matrix naming | Merged |

The high-severity `send_card` bug (#3426) remains unfixed and is the most impactful stability concern, as it directly affects agent-user interactions across all card-using agents.

---

## 6. Feature Requests & Roadmap Signals

- **Multi-bot Telegram support** — Fully shipped today (PR #3436 + supporting PRs). Signals that the roadmap is prioritizing multi-instance channel support, likely extending to other platforms next.
- **Template-driven agent creation in chat** (PR #3396, #3428) — Strong signal that the team is investing in lowering the onboarding barrier; expect this to be a highlighted feature in the next release.
- **Dial channel integration** — Added to wizard and picker (PR #3050, #3433); the skill is now registry-clean. Future work may include more telephony features.
- **Mattermost support** — Just merged (PR #3202). The team is actively expanding the Chat SDK channel catalog; expect similar community adapters to be onboarded.
- **Driver attach surface** (PR #3429) — The new `SessionExecSpec` contract suggests upcoming interactive/terminal-attachment capabilities for agents, likely for debugging or live tooling sessions.

---

## 7. User Feedback Summary

- **Pain point (critical):** Agents report "platform cannot render buttons" when `send_card` actions are silently dropped by the bridge ([Issue #3426](https://github.com/nanocoai/nanoclaw/issues/3426)). Users are losing trust in card-based agent interactions because the SDK docs promise buttons but the bridge doesn't deliver them consistently.
- **Pain point (moderate):** Polling-mode adapters not starting the webhook server blocks users who can't expose public endpoints ([PR #3434](https://github.com/nanocoai/nanoclaw/pull/3434)).
- **Positive signal:** The multi-Telegram-bot feature and template-from-chat flows address real user demand for multi-instance setups and faster agent provisioning, reducing friction for power users.
- **Satisfaction indicator:** High merge rate (11 PRs closed today) and responsive core-team activity suggest the maintainers are actively addressing community contributions.

---

## 8. Backlog Watch

| Item | Type | Age | Risk |
|------|------|-----|------|
| [Issue #3426](https://github.com/nanocoai/nanoclaw/issues/3426) | Bug | 1 day | **High** — No fix PR; affects all card-using agents |
| [PR #3287](https://github.com/nanocoai/nanoclaw/pull/3287) | Fix | 5 days | **Medium** — Open, unmerged; message deduplication bug |
| [PR #3434](https://github.com/nanocoai/nanoclaw/pull/3434) | Fix | 1 day | **Medium** — Open; webhook server not starting for polling adapters |
| [PR #3432](https://github.com/nanocoai/nanoclaw/pull/3432) | Fix | 1 day | **Low** — Open; post-merge Dial follow-ups (credential re-run, step captions) |

**Recommendation:** Issue #3426 should be prioritized for the next patch cycle, as it undermines agent credibility in production. PR #3287 has been open 5 days and should be reviewed soon to prevent message-deduplication regressions in group channels.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-22

## 1. Today's Overview

NullClaw showed minimal activity today, with only **1 open pull request** updated in the last 24 hours and **zero issues** opened or closed. No new releases were published. The project appears to be in a relatively quiet phase, with development focused on provider integrations rather than core stability or major feature rollouts. The sole activity — a feature PR adding Eden AI support — signals continued expansion of the project's provider ecosystem.

## 2. Releases

No new releases today.

---

## 3. Project Progress

| Type | Number | Details |
|------|--------|---------|
| PRs Open | 1 | PR #990 — Eden AI gateway integration |
| PRs Merged | 0 | — |
| Issues Closed | 0 | — |

**Notable PR:**
- **[PR #990](https://github.com/nullclaw/nullclaw/pull/990)** — *feat(providers): add Eden AI as an OpenAI-compatible gateway* (Author: MVS-source, opened 2026-08-21). This PR adds Eden AI as a new provider through the existing `OpenAiCompatibleProvider` interface, following the same pattern as PR #922 (NEAR AI Cloud / Atlas Cloud). No new provider implementation is required — it leverages the existing OpenAI-compatible gateway abstraction.

---

## 4. Community Hot Topics

| Rank | Item | Activity | Link |
|------|------|----------|------|
| 1 | PR #990 — Eden AI gateway | 1 open, 0 reactions, 0 comments | [#990](https://github.com/nullclaw/nullclaw/pull/990) |

**Analysis:** The community interest is currently centered on **provider diversity**. The Eden AI PR continues a clear pattern — users are requesting support for EU-based, multi-vendor routing providers (following NEAR AI Cloud at #922). This suggests a growing user need for **provider redundancy, cost optimization, and regional compliance** (EU data residency). The lack of comments and reactions on today's PR indicates either early visibility or a niche but steady demand for this capability.

---

## 5. Bugs & Stability

No bugs, crashes, or regressions reported today. Zero open issues were closed, suggesting no urgent stability fixes were deployed.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Interpretation |
|--------|--------|----------------|
| Eden AI multi-vendor gateway | PR #990 | Continued push for OpenAI-compatible abstraction expansion |
| EU-based provider support | PR #990 summary | Growing demand for data-residency-compliant routing options |

**Prediction:** If PR #990 merges, the next release will likely include Eden AI as a first-class provider option alongside NEAR AI Cloud and Atlas Cloud, strengthening NullClaw's value proposition as a unified routing layer for heterogeneous LLM backends.

---

## 7. User Feedback Summary

Today's data does not surface direct user pain points or satisfaction metrics. However, the trajectory of provider integration PRs implies users value:

- **Cost-effective routing** across multiple upstream vendors via a single API key
- **EU data residency compliance** for organizations with regulatory requirements
- **Simplified provider onboarding** — the OpenAI-compatible gateway pattern reduces friction for new integrations

---

## 8. Backlog Watch

| Item | Status | Concern |
|------|--------|---------|
| [PR #990](https://github.com/nullclaw/nullclaw/pull/990) | Open since 2026-08-21, 0 comments | A feature PR with no maintainer review activity yet; may need triage |

No long-unanswered issues were detected today. The project's issue backlog appears clean, but the lack of engagement on PR #990 warrants monitoring — maintainers should prioritize review to keep the provider integration pipeline flowing.

---

**Overall Health Assessment:** 🟡 **Low Activity / Stable.** The project is in a quiet period with no release cadence, no bug activity, and a single unreviewed feature PR. Development momentum is present but slow; the provider integration track is active and consistent with roadmap direction.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-22

## 1. Today's Overview

IronClaw (nearai/ironclaw) shows strong development momentum with 15 issues and 35 PRs updated in the last 24 hours. The project is in an active CI-hardening and WebUI standardization phase, with four issues closed and ten PRs merged/closed today. No new releases were published. Activity is concentrated around Rust CI pipeline optimization (the "CI expedite" track across T1–T4), sandbox credential mediation for GitHub CLI, and WebUI design-system unification — indicating the team is investing in developer experience and platform stability ahead of a likely upcoming release.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**Closed/Merged today (10 PRs):**

- **#7804** — Forward-ported `IRONCLAW_REBORN_WORKSPACE_ROOT` durable workspace override to `release/2026-08-17` ([link](https://github.com/nearai/ironclaw/pull/7804))
- **#7797** — Repo-wide agent-guidance audit: pruned 21.5k lines of drift, consolidated `tests/` onto `AGENTS.md` convention via 13 parallel auditors ([link](https://github.com/nearai/ironclaw/pull/7797))
- **#7803** — Fixed Telegram connection flow: keeps paired bot active even without personal device-link credentials; collapsed reply draft projection ([link](https://github.com/nearai/ironclaw/pull/7803))
- **#7805** — Forward-ported clippy 1.98 lint fixes to `release/1.3` branch, resolving persistent `chunks_exact` compile failures ([link](https://github.com/nearai/ironclaw/pull/7805))
- **#7806 / #7807 / #7810** — Three PRs advancing sandbox-mediated GitHub CLI credentials: persistent per-user sandbox runtime, argument-vector execution with cancellation, and direct-executable sandbox path ([links: #7806](https://github.com/nearai/ironclaw/pull/7806) | [#7807](https://github.com/nearai/ironclaw/pull/7807) | [#7810](https://github.com/nearai/ironclaw/pull/7810))
- **#7796** — Fixed Railway audit append failures: fail-closed on staged audit record append, preserving capture for retry ([link](https://github.com/nearai/ironclaw/pull/7796))
- **#7699** — Closed: published actionable run gates (approval, auth-required, blocked) to the durable user inbox ([link](https://github.com/nearai/ironclaw/pull/7699))
- **#7700** — Closed: materialized scheduled-run completion/failure notifications from Process Journal transitions ([link](https://github.com/nearai/ironclaw/pull/7700))

**Key open PRs advancing today:**

- **#7809** — Implements Tasks 1–5 of CI expedite T4: canonical `preflight-gates.sh` as single gate list with worktree-safe hooks ([link](https://github.com/nearai/ironclaw/pull/7809))
- **#7456** — Making durable Reborn storage profile-agnostic with typed security envelope persistence ([link](https://github.com/nearai/ironclaw/pull/7456))
- **#7794** — Shared page-shell and loading primitives for WebUI (page scroll, skeleton components) ([link](https://github.com/nearai/ironclaw/pull/7794))

## 4. Community Hot Topics

**Most discussed open issues:**

1. **#7801 — CI expedite T4: canonical preflight gate list** ([link](https://github.com/nearai/ironclaw/issues/7801)) — 3 comments. The authoritative single-gate-list CI track continues to draw reviewer attention as the final coordination layer.

2. **#7799 — CI expedite T2: nextest pipeline, full-failure signal** ([link](https://github.com/nearai/ironclaw/issues/7799)) — 3 comments. `cargo-nextest` replacement for sequential test loops is a high-impact CI rewrite; multiple commenters are tracking the transition.

3. **#7664 — Pluggable memory over MCP: wire the provider, land Mnesis** ([link](https://github.com/nearai/ironclaw/issues/7664)) — 2 comments. The long-running memory-pluggability epic (#7661 draft provider crate) remains a strategic priority with external community interest (Mnesis Core).

4. **#7800 — CI expedite T3: PR/queue convergence drift guard** ([link](https://github.com/nearai/ironclaw/issues/7800)) — 2 comments. Addresses planner under-selection root causes and queue clippy gaps; critical for CI reliability.

**Underlying need:** The team is consolidating a four-part CI expedite effort (T1–T4) led by `henrypark133`. This signals a mature, systematic investment in build-test reliability — users can expect faster PR turnaround and fewer silent CI failures in the next release cycle.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|----------|-------|---------|--------|
| **Medium** | [#7783](https://github.com/nearai/ironclaw/issues/7783) (CLOSED) | LLM timeout policy: non-streaming finalization can't measure TTFT; retry budget exceeds 75s deadline | Merged |
| **Medium** | [#7715](https://github.com/nearai/ironclaw/issues/7715) (CLOSED) | Telegram connection flow lacks consent/selection between bot and personal account | Merged (#7803) |
| **Low** | [#7813](https://github.com/nearai/ironclaw/issues/7813) | UI heading cropped when suggestions panel renders on chat home screen | — |
| **Low** | [#7808](https://github.com/nearai/ironclaw/issues/7808) | Memory write path lacks redaction + taint metadata before external provider binding | Blocked on #7664 |

**Analysis:** Two medium-severity bugs were resolved today. The LLM timeout policy fix (#7783) addresses a structural issue where non-streaming clients obscure stalled provider requests. The Telegram pairing bug (#7715) is now fixed. Two open low-severity items remain: a UI layout regression (#7813) and a memory-safety prerequisite (#7808) that blocks the pluggable-memory feature.

## 6. Feature Requests & Roadmap Signals

- **#7812** — Onboarding suggestions should respect user-level tool permissions and generate with read-only access ([link](https://github.com/nearai/ironclaw/issues/7812)). PR #7802 (open) addresses the enabling side by always-mounting OOBE suggestions.
- **#7664** — Pluggable memory over MCP with Mnesis as first consumer ([link](https://github.com/nearai/ironclaw/issues/7664)). The provider crate (#7661 draft) and write-path redaction fix (#7808) are prerequisites.
- **#7687** — Generalize WebUI notification center into a durable user inbox ([link](https://github.com/nearai/ironclaw/issues/7687)). Core inbox infrastructure is now live via #7699/#7700; remaining work is consumption and extension.
- **#7792 / #7793** — Shared page-shell primitives and migration of settings/admin banners to `InlineNotice` ([links: #7792](https://github.com/nearai/ironclaw/issues/7793) | [#7792](https://github.com/nearai/ironclaw/issues/7792)). These are incremental UX standardization work, likely landing in the next patch.
- **#7811** — Bundle Xquik hosted MCP for Twitter/X data with OAuth 2.1 + S256 PKCE ([link](https://github.com/nearai/ironclaw/pull/7811)). New extension bundle PR open for review.

**Prediction:** The next release will likely include the CI expedite completions (T1–T4), sandbox-mediated GitHub CLI credentials, and the durable notification inbox. The pluggable-memory feature (#7664) appears aimed at a later milestone given its prerequisite depth.

## 7. User Feedback Summary

- **Telegram pairing UX gap** (#7715 → fixed #7803): Users connecting via Railway reported confusion over missing bot-vs-personal-account selection. Now resolved.
- **LLM timeout blind spots** (#7783 → fixed): Users experienced cascading run failures when non-streaming providers stalled — a structural retry-budget issue now corrected.
- **Onboarding suggestion quality** (#7812): Users report that suggestion generation lacks grounding in their actual data because internal tools only have search/memory access, not connected tool permissions.
- **UI layout regression** (#7813): Chat home screen heading is cropped when the "Suggested for you" panel renders — a visual regression affecting new-user onboarding.
- **Memory privacy** (#7808): External memory provider binding is blocked until write-path redaction and taint metadata are enforced at the host level — users expect privacy guarantees before third-party memory integration.

Overall sentiment: active bug resolution, improving CI stability, and growing attention to onboarding UX and data-privacy boundaries.

## 8. Backlog Watch

| Issue/PR | Days Open | Risk | Note |
|----------|-----------|------|------|
| [#7664](https://github.com/nearai/ironclaw/issues/7664) — Pluggable memory over MCP | 8 days | Strategic | Dependent on #7661 (provider crate draft) and #7808 (redaction prerequisite). Long horizon feature. |
| [#7813](https://github.com/nearai/ironclaw/issues/7813) — UI heading cropped | 0 days (today) | Low | Fresh report; no fix PR yet. Visible regression on chat home screen. |
| [#7808](https://github.com/nearai/ironclaw/issues/7808) — Memory write-path redaction | 1 day | Medium | Blocks all external memory provider binding (#7664). Needs host-level write-path fix. |
| [#7809](https://github.com/nearai/ironclaw/pull/7809) — CI T4 preflight gates | 1 day | Low-Medium | Large PR implementing canonical gate list; review throughput will determine CI expedite completion. |
| [#7456](https://github.com/nearai/ironclaw/pull/7456) — Reborn durable storage profile-agnostic | 12 days | Medium | Size XL; touches storage layer. Needs maintainer review before merge. |
| [#7257](https://github.com/nearai/ironclaw/pull/7257) — WebUI design-system proposal | 17 days | Low | Docs-only north-star proposal; no merge urgency but tracks Epic #7038. |

**Maintainer attention needed:** #7664 (memory pluggability) and #7808 (redaction) are the highest-impact backlog items — together they gate the external memory ecosystem. #7456 and #7809 are large, high-leverage PRs awaiting review that will unlock significant CI and storage improvements.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-22

## 1. Today's Overview

LobsterAI is in an active maintenance and iteration phase. Over the past 24 hours, 13 PRs were processed (12 merged/closed, 1 still open) and 2 issues were resolved, all without a new versioned release. The project's cadence reflects steady progress on the upcoming 2026.8.21 release cycle, with a focus on performance hardening, i18n fixes, and analytics instrumentation for the experimental DSH runtime. Community engagement is moderate but focused, with no high-traffic discussion threads observed.

## 2. Releases

No new standalone release published today. However, **PR #2519** merged the `release/2026.8.21` branch into `main`, consolidating several changes:

- DSH runtime bumped to `0.1.1-rc.1`
- Improved Windows integration reliability
- Added privacy-conscious analytics for DSH enablement and workbench usage

**Migration note:** Users on previous versions should expect the DSH experimental runtime to update automatically on next launch; no manual action required.

- [PR #2519](https://github.com/netease-youdao/LobsterAI/pull/2519)

## 3. Project Progress

**12 PRs merged/closed today**, spanning several key areas:

| Area | Highlights |
|---|---|
| **DSH (DeepSeek Harness)** | `0.1.1-rc.1` update (#2516); analytics moved to renderer-side service (#2518); usage tracking for enable-toggle and workbench open events (#2515) |
| **Library / Artifacts** | File sharing and bookmarking UX improvements (#2517); local artifact preview and operation streamlining (#2514); library feature work from 2026.8.17 (#2513) |
| **i18n / UX** | Hardcoded Chinese labels in `CoworkPromptInput` replaced with i18n service calls; Escape key and duplicate-click protection added to Agent dialogs (#1224) |
| **Performance** | Eliminated invalid re-renders in cowork session list and detail views (#1219); resolved N+1 query pattern in `CoworkStore` (#1220) |
| **IM / Chat** | Fixed stale chat handler not rebuilding on `setConfig` when platform-specific credentials (DingTalk/Telegram) are saved (#1215) |
| **Scheduled Tasks** | Refactored task list sorting to use creation/executable time instead of UUID string order (#1218) |

## 4. Community Hot Topics

No issues or PRs in the current window show high comment or reaction counts (all at 0–2 comments). The project's community interaction appears low-key this cycle. The most substantive discussions are:

- **[Issue #1223](https://github.com/netease-youdao/LobsterAI/issues/1223)** — Multi-part UX/i18n bug report that drove a consolidated fix.反映出用户对环境一致性（英文系统下不出现中文提示词）和交互细节（Escape关闭、防重复点击）的关注。
- **[Issue #1217](https://github.com/netease-youdao/LobsterAI/issues/1217)** — Intermittent gateway restart bug affecting daily use (3–5 times/day). Still worth monitoring for recurrence patterns.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Status |
|---|---|---|---|
| 🟡 Medium | [#1217](https://github.com/netease-youdao/LobsterAI/issues/1217) | Intermittent gateway restart during use (Windows, ~3–5×/day) | ✅ Closed — likely stale/unsure |
| 🟡 Medium | [#1223](https://github.com/netease-youdao/LobsterAI/issues/1223) | Hardcoded Chinese in i18n flow + missing Escape key + duplicate-click in Agent dialog | ✅ Closed via [#1224](https://github.com/netease-youdao/LobsterAI/pull/1224) |
| 🟠 High | [#1550](https://github.com/netease-youdao/LobsterAI/pull/1550) | Scheduled tasks with "no notification" mode fail at trigger time with "Channel is required" error (session-created tasks only) | 🟡 Open — no fix merged yet |

The open PR #1550 is the most significant remaining stability concern: tasks created via会话/IM with `mode=none` crash at execution, while UI-created tasks with the same mode work fine. Root cause is a divergent `delivery` object construction path.

## 6. Feature Requests & Roadmap Signals

- **DSH Analytics** — The addition of usage telemetry for DSH enablement and workbench opens (#2515, #2518) signals the team is preparing to make data-driven decisions about the experimental runtime's adoption. Expect DSH to be a focal point in the next release notes.
- **Library UX Maturation** — Three consecutive library PRs (#2513, #2514, #2517) over the same day indicate an active feature sprint around artifact management, file sharing, and preview experience. These capabilities are likely to be highlighted in the next major version.
- **Scheduled Task Reliability** — The sorting fix (#1218) and the open channel bug (#1550) suggest the team is investing in making scheduled tasks more robust for power users.

## 7. User Feedback Summary

- **i18n consistency** is a recurring pain point (Issue #1223). English-language users are sensitive to hardcoded Chinese strings leaking into prompts, which violates the project's own `AGENTS.md` guideline.
- **Gateway stability** remains a concern (Issue #1217). Intermittent restarts disrupt workflow and are difficult to reproduce deterministically.
- **Performance** was proactively addressed by contributors (#1219, #1220) without user filing — indicating an engaged developer community that monitors rendering and query patterns.
- **Scheduled task UX** (random sort order, notification mode bugs) shows users are relying on automation features seriously enough to encounter edge-case failures.

## 8. Backlog Watch

| Item | Age | Risk |
|---|---|---|
| [PR #1550](https://github.com/netease-youdao/LobsterAI/pull/1550) — Scheduled task "no notification" channel bug | Open since **2026-04-07** (~4.5 months) | 🔴 High — affects task reliability for IM-created workflows |
| [Issue #1217](https://github.com/netease-youdao/LobsterAI/issues/1217) — Gateway restart | Closed as stale | 🟡 Medium — issue persists for some users; no verified fix |

**PR #1550** is the most important item requiring maintainer attention. It has been open for over four months and affects a real execution-path bug that causes tasks to crash at trigger time. A targeted fix would be straightforward given the root cause is already identified (divergent `delivery` object construction between UI and IM creation paths).

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-22

## 1. Today's Overview

Moltis showed moderate but focused activity on 2026-08-22, with 2 open issues and 8 open pull requests updated in the last 24 hours (1 PR closed/merged). The project is in a steady-state development cycle with no new releases — all effort is directed toward bug fixes and refinements rather than feature launches. Activity is concentrated on stability improvements across messaging gateways (WhatsApp, Slack), cron/heartbeat reliability, and security hardening around sandbox image validation. The contributor base remains small but consistent, with `rubenssoto` driving the majority of today's PRs.

## 2. Releases

No new releases were published today. The project appears to be in a pre-release stabilization phase, with multiple targeted fixes landing in PRs without an accompanying version bump yet.

## 3. Project Progress

**Merged/Closed today:**

- **[#1220](https://github.com/moltis-org/moltis/pull/1220)** — *fix(whatsapp): render Markdown in outbound messages* (Closed) — WhatsApp outbound messages now convert model-generated Markdown to WhatsApp-native markup before delivery, preserving original Markdown in session history and the web UI.

**PRs advancing today:**

- **[#1228](https://github.com/moltis-org/moltis/pull/1228)** — *fix(whatsapp): persist inbound files for local tools* — Inbound WhatsApp documents and photos are now downloaded and exposed via a stable `local_path`, enabling local tools to act on media rather than just metadata. 20 MB limit enforced.
- **[#1227](https://github.com/moltis-org/moltis/pull/1227)** — *fix(browser): enable Obscura stealth mode by default* — The Obscura sidecar now launches with `--stealth` by default, with an opt-out config key `tools.browser.obscura_stealth`.
- **[#1226](https://github.com/moltis-org/moltis/pull/1226)** — *fix(cron): deliver scheduled output to the originating chat* — Cron jobs now route their output back to the chat/channel they were triggered from, using a transient `payload.deliver_to_current_chat` shortcut.
- **[#1225](https://github.com/moltis-org/moltis/pull/1225)** — *fix(i18n): update and improve zh-TW locale* — Significant rewrite and expansion of Traditional Chinese translations across multiple modules, particularly `connectors.ts`.
- **[#1222](https://github.com/moltis-org/moltis/pull/1222)** — *fix(web): validate sandbox image requests* — Image references and package names are now validated before container or Dockerfile use, with checks restricted to operator administrators.
- **[#1208](https://github.com/moltis-org/moltis/pull/1208)** — *fix(cron): honor heartbeat active hours when the scheduler fires* — Addresses the long-standing bug where `heartbeat.active_hours` had no effect because `is_within_active_hours` was never called in the scheduler loop.
- **[#468](https://github.com/moltis-org/moltis/pull/468)** — *fix(plugins): use cmd.exe on Windows for shell hooks* — Shell hooks on Windows now use `cmd.exe /C` instead of the unavailable `sh -c`. Open since March 2026.

## 4. Community Hot Topics

- **[Issue #1224](https://github.com/moltis-org/moltis/issues/1224)** — *Tools stop working in shared Slack channels* — Reported by `affanshahid`. No comments yet, but the bug title suggests a routing or permission issue in multi-channel Slack deployments, a growing concern as teams scale Moltis across shared workspaces.
- **[Issue #1223](https://github.com/moltis-org/moltis/issues/1223)** — *heartbeat active_hours has no effect on a default config* — Reported by `Lstarsky0`, who also authored the fix in PR #1208. This issue highlights a documentation-vs-implementation gap: the feature was coded and documented but never wired into the scheduler.
- **[PR #1220](https://github.com/moltis-org/moltis/pull/1220)** — The most recently closed PR, reflecting sustained user demand for proper Markdown support on WhatsApp, a channel where rich text formatting is expected.

**Underlying need:** Users are pushing for production-grade reliability in messaging integrations (WhatsApp, Slack) and scheduling correctness. The concentration of today's fixes on these areas signals that Moltis is maturing from a prototype to a tool expected to run continuously in real work environments.

## 5. Bugs & Stability

| Severity | Item | Link | Fix PR |
|----------|------|------|--------|
| **High** | `heartbeat.active_hours` has no effect — scheduled tasks ignore user-configured active windows | [Issue #1223](https://github.com/moltis-org/moltis/issues/1223) | [#1208](https://github.com/moltis-org/moltis/pull/1208) |
| **Medium** | Tools stop working in shared Slack channels | [Issue #1224](https://github.com/moltis-org/moltis/issues/1224) | None yet |
| **Medium** | Inbound WhatsApp files not persisted for local tool use (information loss, not crash) | — | [#1228](https://github.com/moltis-org/moltis/pull/1228) |
| **Low** | Markdown not rendered in outbound WhatsApp messages | — | [#1220](https://github.com/moltis-org/moltis/pull/1220) ✓ merged |

No crashes or regressions were reported today. The most impactful open bug (#1224) remains unassigned with no fix PR.

## 6. Feature Requests & Roadmap Signals

- **Inbound file persistence for WhatsApp** ([#1228](https://github.com/moltis-org/moltis/pull/1228)) — Users need local tools to access media sent through WhatsApp, not just filenames. This suggests a broader demand for full media pipeline support across connectors.
- **Cron output delivery to originating chat** ([#1226](https://github.com/moltis-org/moltis/pull/1226)) — Operators want scheduled jobs to reply in context rather than requiring manual address configuration. Likely to ship in the next patch release.
- **Obscura stealth mode on by default** ([#1227](https://github.com/moltis-org/moltis/pull/1227)) — Indicates a roadmap shift toward privacy-by-default browser automation, responding to increasing anti-bot detection pressures.
- **zh-TW locale expansion** ([#1225](https://github.com/moltis-org/moltis/pull/1225)) — Signals ongoing internationalization investment; expect more non-English locales in future releases.

**Prediction:** The next release will likely bundle PRs #1208, #1220, #1226, and #1228 as a stabilization patch, with #1227 and #1222 as supporting fixes.

## 7. User Feedback Summary

- **Pain point:** WhatsApp is a first-class channel users expect full media and formatting support on, but inbound file handling and outbound Markdown were missing — both now being addressed.
- **Pain point:** The `active_hours` heartbeat feature was documented but non-functional, causing user frustration when scheduled tasks ran outside intended windows. The fix PR (#1208) was authored by the same reporter, suggesting the user is actively engaged and satisfied with the response.
- **Satisfaction signal:** Fast turnaround on the WhatsApp Markdown fix (PR #1220 closed the same day it was reported) indicates a responsive maintainer team.
- **Unresolved concern:** Slack shared-channel tool failures ([#1224](https://github.com/moltis-org/moltis/issues/1224)) remain open with no maintainer acknowledgment, which could erode trust among team-deployment users.

## 8. Backlog Watch

- **[PR #468](https://github.com/moltis-org/moltis/pull/468)** — *fix(plugins): use cmd.exe on Windows for shell hooks* — Open since **2026-03-23** (over 5 months). Windows users cannot use shell hooks at all without this fix. CI reportedly passes. This is a long-standing compatibility block that warrants maintainer triage.
- **[Issue #1224](https://github.com/moltis-org/moltis/issues/1224)** — *Tools stop working in shared Slack channels* — Open since 2026-08-21 with zero comments from maintainers. While new, the lack of acknowledgment on a production-impacting bug is worth monitoring.
- **[Issue #1205](https://github.com/moltis-org/moltis/issues/1205)** — Referenced by PR #1208 as the original heartbeat bug report. Should be verified as closed once the PR merges.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-22

---

## 1. Today's Overview

The CoPaw project (agentscope-ai/QwenPaw) shows **high daily activity** with 34 issues and 34 PRs updated in the last 24 hours, reflecting a mature open-source agent platform entering an active release cycle around v2.1.x. No new release was published today, but three PRs were merged/closed (PR #7205, #7200, #7112) and 13 PRs remain open for review. Community engagement is strong, with 19 open issues and 21 open PRs, indicating sustained contributor involvement across bugs, features, and documentation.

---

## 2. Releases

**No new releases published today.** The latest tracked version is **v2.1.1-beta.1**, with PR #7200 bumping the version to **v2.1.1b2**. Users are advised to monitor for an upcoming stable v2.1.1 release that will likely incorporate the day's merged fixes.

---

## 3. Project Progress

### Merged / Closed Today
| PR | Author | Summary |
|----|--------|---------|
| [#7205](https://github.com/agentscope-ai/QwenPaw/pull/7205) | yutai78786 | **Fix:** Windows integration coverage silently reading 0 lines; added fail-closed guard |
| [#7200](https://github.com/agentscope-ai/QwenPaw/pull/7200) | cuiyuebing | **Chore:** Bump version to v2.1.1b2 |
| [#7112](https://github.com/agentscope-ai/QwenPaw/pull/7112) | rayrayraykk | **Feat:** Self-hosted multi-user QwenPaw Hub with local and Docker runtimes |
| [#7176](https://github.com/agentscope-ai/QwenPaw/pull/7176) | rayrayraykk | **Perf:** Kept long chat sessions responsive (eliminated redundant Markdown reparsing and completed-history re-rendering) |

### Key Open PRs Under Review
- [#7190](https://github.com/agentscope-ai/QwenPaw/pull/7190) — PyPI runtime path, docker-compose one-shot demo, env inheritance fix
- [#7187](https://github.com/agentscope-ai/QwenPaw/pull/7187) — Disable thinking for auto title generation
- [#7211](https://github.com/agentscope-ai/QwenPaw/pull/7211) — Prevent injected context from persisting as user chat history
- [#7208](https://github.com/agentscope-ai/QwenPaw/pull/7208) — DingTalk group chat shared session context
- [#7207](https://github.com/agentscope-ai/QwenPaw/pull/7207) — Token usage attribution by agent
- [#7167](https://github.com/agentscope-ai/QwenPaw/pull/7167) — Creator 1.1.0: Anthropic/Gemini protocols, expanded effects, 2GB uploads

---

## 4. Community Hot Topics

| Issue | Comments | Status | Summary |
|-------|----------|--------|---------|
| [#6524](https://github.com/agentscope-ai/QwenPaw/issues/6524) | 6 | OPEN | MCP backend restart → client fails to auto-recover; requires manual `list mcp` |
| [#6780](https://github.com/agentscope-ai/QwenPaw/issues/6780) | 4 | CLOSED | v2.0.1 app hangs after ~30 min idle; only restart resolves it |
| [#7016](https://github.com/agentscope-ai/QwenPaw/issues/7016) | 3 | OPEN | Tool call endpoint returns 404 during streaming sessions |
| [#7156](https://github.com/agentscope-ai/QwenPaw/issues/7156) | 3 | OPEN | Embedding health check times out (>5s) even when backend is pre-warmed; timeout is hardcoded |

**Analysis:** The top discussions center on **MCP connectivity resilience**, **long-idle stability**, and **hardcoded configuration limits**. Users are deploying QwenPaw in production-like server environments where reliability under restart and extended runtime is critical. The hardcoded health-check timeout (#7156) and MCP session recovery (#6524) suggest the platform needs better operational configurability for enterprise deployments.

---

## 5. Bugs & Stability

### High Severity
| Issue | Description | Fix PR? |
|-------|-------------|---------|
| [#6524](https://github.com/agentscope-ai/QwenPaw/issues/6524) | MCP session not auto-recovered after server restart; requires manual intervention | ❌ No |
| [#7016](https://github.com/agentscope-ai/QwenPaw/issues/7016) | `/offload` endpoint returns 404 "Tool call not found" during streaming | ❌ No |
| [#7206](https://github.com/agentscope-ai/QwenPaw/issues/7206) | v2.1.1-beta.1 regression: manual `/compact` always fails with Pydantic ValidationError when `compact_threshold_ratio == 0.9` | ❌ No |
| [#7168](https://github.com/agentscope-ai/QwenPaw/issues/7168) | `history.db` exploded to 7.6 GB due to `recall_history` expand writing duplicate full segments | ✅ Closed |

### Medium Severity
| Issue | Description |
|-------|-------------|
| [#7136](https://github.com/agentscope-ai/QwenPaw/issues/7136) | File card name displays percent-encoded mojibake for non-ASCII (Chinese) filenames |
| [#7193](https://github.com/agentscope-ai/QwenPaw/issues/7193) | Memory search incorrectly pulls content from another session of the same agent |
| [#7199](https://github.com/agentscope-ai/QwenPaw/issues/7199) | `daily_paper` job crashes on PDFs containing surrogate characters (U+D800–U+DFFF) |
| [#6427](https://github.com/agentscope-ai/QwenPaw/issues/6427) | WebView2 render process crashes ~7s after startup in v2.0.0+post.4 (deterministic assertion failure in `msedge.dll`) |
| [#6430](https://github.com/agentscope-ai/QwenPaw/issues/6430) | Desktop startup hangs consistently for ~85 seconds |

### Low Severity
| Issue | Description |
|-------|-------------|
| [#7210](https://github.com/agentscope-ai/QwenPaw/issues/7210) | Built-in tools enabled in `agent.json` but not injected into session function schema |

**Note:** Three high-severity bugs (#6524, #7016, #7206) lack fix PRs and should be prioritized for the v2.1.1 stable release.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Likelihood for v2.1.x |
|-------|---------|----------------------|
| [#7201](https://github.com/agentscope-ai/QwenPaw/issues/7201) | Separate per-provider `max_image_bytes` / `max_video_bytes` / `max_audio_bytes` caps | **High** — clean extensibility improvement; small scope |
| [#7203](https://github.com/agentscope-ai/QwenPaw/issues/7203) | Toggle to show/hide tool call info in UI | **High** — frequently requested (referenced Hermes UI pattern) |
| [#7196](https://github.com/agentscope-ai/QwenPaw/issues/7196) | Default-collapse reasoning/thinking process display | **High** — same user (#rerbin) also filed #7203; strong signal |
| [#7198](https://github.com/agentscope-ai/QwenPaw/issues/7198) | Skip approval for pre-session file operations | **Medium** — UX policy change; needs product decision |
| [#7195](https://github.com/agentscope-ai/QwenPaw/issues/7195) | Fullscreen chat window not blocked by bottom icons | **Low** — simple CSS fix |
| [#7204](https://github.com/agentscope-ai/QwenPaw/issues/7204) | How to add custom tools | Informational; likely docs update |

**Roadmap Signal:** The v2.1.x series is clearly focusing on **reliability hardening** (memory, MCP recovery), **operator UX** (collapsible reasoning, tool visibility toggles), and **multi-user/self-hosted scenarios** (Hub PR #7112, DingTalk shared sessions PR #7208). The feature requests from user `#rerbin` (#7196, #7198, #7203) form a coherent theme around reducing UI noise and approval friction for automated/background agent runs.

---

## 7. User Feedback Summary

**Pain Points:**
- **MCP session fragility** (#6524): Users running remote MCP servers experience broken tool discovery after server restarts — a significant reliability gap for production use.
- **Startup hangs and WebView2 crashes** (#6427, #6430): Desktop users report deterministic failures that block onboarding, especially after minor version bumps (post.3 → post.4).
- **Memory search cross-contamination** (#7193): Agents retrieve context from sibling sessions, causing incorrect behavior in multi-session setups.
- **Database bloat** (#7168 — closed): A long-running agent's `history.db` grew to 7.6 GB due to duplicate segment writes; resolved but signals a need for better history pruning.
- **Approval friction for background jobs** (#7198): Nightly automated agent runs are blocked by unnecessary approval popups for intermediate file operations.

**Satisfaction Signals:**
- Praise for the Creator 1.1.0 update (#7167 PR) bringing mainstream model ecosystem support.
- Positive reception of long-session performance improvements (#7176 merged).
- Community contributors actively improving test coverage (frontend Vitest plan, backend runner tests).

---

## 8. Backlog Watch

| Issue / PR | Age | Concern |
|------------|-----|---------|
| [#6524](https://github.com/agentscope-ai/QwenPaw/issues/6524) — MCP auto-recovery | Created 2026-07-28 (25 days) | Critical for production MCP deployments; no fix PR yet |
| [#7016](https://github.com/agentscope-ai/QwenPaw/issues/7016) — Tool call 404 | Created 2026-08-14 (8 days) | Streaming session regression; no fix PR |
| [#7206](https://github.com/agentscope-ai/QwenPaw/issues/7206) — Compact pydantic error | Created 2026-08-21 (1 day) | v2.1.1-beta regression; blocks stable release candidate |
| [#6427](https://github.com/agentscope-ai/QwenPaw/issues/6427) — WebView2 crash | Created 2026-07-24 (29 days) | Desktop stability; affects Windows users on post.4+ |
| [#6430](https://github.com/agentscope-ai/QwenPaw/issues/6430) — Startup hang | Created 2026-07-24 (29 days) | Desktop onboarding blocker; no fix PR |
| [#5992](https://github.com/agentscope-ai/QwenPaw/pull/5992) — Per-session model overrides | Created 2026-07-12 (41 days) | Under review; high-value feature for multi-model deployments |
| [#6399](https://github.com/agentscope-ai/QwenPaw/pull/6399) — Reranker UI config panel | Created 2026-07-23 (30 days) | Under review; complements backend reranker feature |
| [#7190](https://github.com/agentscope-ai/QwenPaw/pull/7190) — PyPI runtime path / docker-compose demo | Created 2026-08-21 | Critical for easier onboarding and CI demos; needs maintainer review |

**Priority Recommendation:** The v2.1.1 release candidates should address **#7206** (regression), **#6524** (MCP recovery), and **#7016** (tool call 404) before stable publication. The WebView2 crash (#6427) and startup hang (#6430) should be resolved in the next desktop patch to protect Windows user retention.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-22

## 1. Today's Overview

ZeroClaw is exhibiting high development velocity with **50 issues and 50 PRs** updated in the last 24 hours (48 open/active each). The project is in an active bug-fixing and hardening cycle, with a notable concentration of **P1-severity security and runtime bugs** reported around the delegate risk-profile bypass, tool-result truncation, and daemon startup overflow. No new releases were published today, but several closed PRs indicate that release-gate and CI hardening work is progressing. Overall project health is strong — high contributor engagement, fast triage, and parallel fixes in flight for the most critical issues.

---

## 2. Releases

**No new releases published today.**

---

## 3. Project Progress

### Closed / Merged Today

| PR | Description | Author |
|----|-------------|--------|
| [#10174](https://github.com/zeroclaw-labs/zeroclaw/pull/10174) | **test(ci):** Added a two-runner smoke matrix to verify pinned release tools on native Linux and Windows GitHub-hosted runners before the next release depends on them. | @Audacity88 |
| [#10074](https://github.com/zeroclaw-labs/zeroclaw/issues/10074) | **docs/security:** Corrected SECURITY.md to reflect that the CI docker job referenced was removed in April; container checks are now a convention rather than an automated gate. | @melbinjp |

### Notable PRs Advanced (Open, in review)

- **#10236** — Bound daemon capture logs to 8 MiB in the Desktop supervisor, preventing unbounded log growth.
- **#10197** — Persist interrupted Code/ACP turn progress before streaming, so daemon or process exits no longer erase visible assistant text and tool activity.
- **#10210** — Added wall-clock deadlines and `kill_on_drop` to unbounded `agent-browser` subprocess waits.
- **#10176** — Extended Docker CI to enforce Alpine non-root image metadata (`UID 65534:65534`) across all loaded `Dockerfile.alpine` rows.
- **#10201** — Allow setting the WhatsApp bot display name via `push_name` in channel config, eliminating the manual handset workaround.
- **#10239** — Fixed `interrupt_on_new_message` to resolve from any configured channel alias, not just `"default"`.

---

## 4. Community Hot Topics

| Issue / PR | Comments | Topic |
|------------|----------|-------|
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | 3 | Delegate bypasses `block_high_risk_commands` on its own risk profile |
| [#10074](https://github.com/zeroclaw-labs/zeroclaw/issues/10074) | 3 | SECURITY.md documents a removed CI job — docs rot on security policy |
| [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | 3 | Interactive agent session caps context at 32k tokens despite `max_context_tokens = 131072` |
| [#10066](https://github.com/zeroclaw-labs/zeroclaw/issues/10066) | 3 | SOP engine promotes later steps before recording output-schema rejection |
| [#10059](https://github.com/zeroclaw-labs/zeroclaw/issues/10059) | 3 | Support Option-Backspace word deletion in ZeroCode (good first issue) |

**Analysis:** The top-commented issues cluster around **security policy enforcement** (#10165, #10074) and **runtime configuration not being honored** (#10068, #10066). The community is clearly prioritizing correctness of the security sandbox and fidelity of user-configured limits. The Option-Backspace request (#10059) signals macOS power-user adoption of ZeroCode as a daily driver.

---

## 5. Bugs & Stability

### P1 — Critical / High Severity (reported or updated today)

| Issue | Severity | Summary | Fix PR? |
|-------|----------|---------|---------|
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | S0 — data loss / security risk | Independent delegate bypasses `block_high_risk_commands` using its own risk profile | None yet |
| [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) | S2 — degraded behavior | `block_high_risk_commands = false` not honored; allowlisted high-risk commands still blocked on parent path | None yet |
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | S1 — workflow blocked | Daemon startup/reload can overflow during agent initialization (Tokio runtime worker stack overflow) | None yet |
| [#10066](https://github.com/zeroclaw-labs/zeroclaw/issues/10066) | S1 — workflow blocked | SOP engine runs later steps before recording output-schema rejection | None yet |
| [#10121](https://github.com/zeroclaw-labs/zeroclaw/issues/10121) | S0 — data loss / security risk | Partial Code/ACP turns disappear if process exits before completion | **#10197** (open) |
| [#10061](https://github.com/zeroclaw-labs/zeroclaw/issues/10061) | S1 — workflow blocked | Provider-rejected image poisons later turns in a vision-capable session | None yet |
| [#10116](https://github.com/zeroclaw-labs/zeroclaw/issues/10116) | S2 — degraded behavior | Oversized tool results cut byte-wise middle-out; should spill to file handle | None yet |
| [#10115](https://github.com/zeroclaw-labs/zeroclaw/issues/10115) | S2 — degraded behavior | Tool-result truncation invisible outside the model's context | None yet |
| [#10114](https://github.com/zeroclaw-labs/zeroclaw/issues/10114) | S2 — degraded behavior | `max_tool_result_chars` fixed at 50k, unrelated to model context window | None yet |

### P2 — Medium Severity

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) | Interactive agent caps context at 32k tokens ignoring config | None yet |
| [#10175](https://github.com/zeroclaw-labs/zeroclaw/issues/10175) | Google TTS API key header not marked sensitive | None yet |
| [#10199](https://github.com/zeroclaw-labs/zeroclaw/issues/10199) | Plugin egress connect-deadline cannot cancel blocking `getaddrinfo` | None yet |
| [#10058](https://github.com/zeroclaw-labs/zeroclaw/issues/10058) | ZeroCode file explorer search ignores row/page navigation | None yet |
| [#10062](https://github.com/zeroclaw-labs/zeroclaw/issues/10062) | TodoWrite plan leaks across ZeroCode session switches | None yet |
| [#10238](https://github.com/zeroclaw-labs/zeroclaw/issues/10238) | ZeroCode shows stale Connected state after daemon exits | None yet |
| [#10202](https://github.com/zeroclaw-labs/zeroclaw/issues/10202) | Log-based dependency records never reach tracing subscriber | None yet |

**Assessment:** The security sandbox (#10165, #10164) is the most urgent area — two complementary bugs suggest the risk-profile enforcement logic has a systemic flaw. The tool-result truncation chain (#10114 → #10115 → #10116) is a coherent set of related issues that should be addressed together. **#10197** is the only open fix PR for a P1 bug (turn-progress loss).

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Type | Summary | Likelihood for Next Release |
|------------|------|---------|----------------------------|
| [#10166](https://github.com/zeroclaw-labs/zeroclaw/issues/10166) | Enhancement | Default `stream_mode` to `partial` so channel replies stream progressively | **High** — low risk, clear UX win |
| [#10168](https://github.com/zeroclaw-labs/zeroclaw/issues/10168) | Enhancement | Enable stall watchdog by default (`stall_timeout_secs`) | **High** — prevents indefinite hangs |
| [#10073](https://github.com/zeroclaw-labs/zeroclaw/issues/10073) | Enhancement | Retire `StoragePolicy::Rolling`; absorb into `Rotating`; extend `/api/logs` | **Medium** — larger architectural change |
| [#10140](https://github.com/zeroclaw-labs/zeroclaw/issues/10140) | Enhancement | Transcribe inbound iMessage voice attachments | **Medium** — parity with Telegram/Slack/Discord |
| [#10200](https://github.com/zeroclaw-labs/zeroclaw/issues/10200) | Enhancement | Set WhatsApp bot display name from config | **High** — #10201 PR already exists |
| [#10086](https://github.com/zeroclaw-labs/zeroclaw/issues/10086) | Enhancement | Make ZeroCode Logs text selectable and copyable | **High** — #10096 PR already exists |
| [#10138](https://github.com/zeroclaw-labs/zeroclaw/issues/10138) | Enhancement | Include fully compiled Git Channel in `zeroclaw:debian` Docker image | **Low** — packaging change, niche need |
| [#9645](https://github.com/zeroclaw-labs/zeroclaw/pull/9645) | Feature | ZeroRouter preset and device-flow login (self-hosted metered LLM gateway) | **Medium** — large PR, needs review |
| [#10142](https://github.com/zeroclaw-labs/zeroclaw/pull/10142) | Feature | ZeroRelay secure transport and browser enrollment (mutual TLS, per-daemon CA) | **Medium** — security infrastructure, large scope |

---

## 7. User Feedback Summary

**Pain points expressed:**

1. **Security sandbox is unreliable.** Two bugs (#10165, #10164) from the same author (@rawlink) indicate that `block_high_risk_commands` behaves inconsistently depending on whether the command runs through a delegate or the parent path. This is a trust-critical issue for users running agents with shell access.

2. **Configured limits are ignored.** Users setting `max_context_tokens = 131072` are hit with a hard 32k cap in interactive sessions (#10068), and `max_tool_result_chars` is silently fixed at 50k regardless of model (#10114). This erodes confidence in the configuration system.

3. **ZeroCode UX gaps.** File explorer search doesn't respect arrow keys (#10058), logs aren't selectable (#10086), and the Connected state widget goes stale after daemon exits (#10238). These are quality-of-life issues that accumulate frustration for daily users.

4. **Process exit = data loss.** Partial turns in Code/ACP are lost on daemon exit (#10121), and the fix (#10197) is already in flight — users will appreciate this.

5. **WhatsApp bot identity is frustrating.** The display name reverts on every relink (#10200), and the fix (#10201) is ready for review.

**Satisfaction signals:** The project has active "good first issue" labels (#10059) and responsive maintainers (multiple PRs merged/closed within days of opening). The contributor base is diverse, with distinguished contributors and first-time contributors both active.

---

## 8. Backlog Watch

| Issue / PR | Age | Risk | Why It Needs Attention |
|------------|-----|------|------------------------|
| [#10165](https://github.com/zeroclaw-labs/zeroclaw/issues/10165) | 2 days | **Critical** | No fix PR yet. Security sandbox bypass is a P1 trust issue. |
| [#10164](https://github.com/zeroclaw-labs/zeroclaw/issues/10164) | 2 days | **High** | No fix PR yet. Complementary to #10165 — same subsystem. |
| [#10066](https://github.com/zeroclaw-labs/zeroclaw/issues/10066) | 5 days | **High** | SOP engine step-ordering bug; no fix PR. Blocks workflow-correctness claims. |
| [#10230](https://github.com/zeroclaw-labs/zeroclaw/issues/10230) | 1 day | **High** | Stack overflow on daemon reload; `r:needs-repro` tag means it may be环境-specific. Needs a reproducer or a defensive fix. |
| [#10061](https://github.com/zeroclaw-labs/zeroclaw/issues/10061) | 5 days | **High** | Provider-rejected images poison later turns; no fix PR. Vision-session users are affected. |
| [#9645](https://github.com/zeroclaw-labs/zeroclaw/pull/9645) | 21 days | **Medium** | ZeroRouter feature PR — large scope, needs-author-action, needs maintainer review to unblock. |
| [#10142](https://github.com/zeroclaw-labs/zeroclaw/pull/10142) | 3 days | **Medium** | ZeroRelay secure transport — large PR, critical for remote-deployment security, needs review bandwidth. |
| [#10073](https://github.com/zeroclaw-labs/zeroclaw/issues/10073) | 4 days | **Medium** | Logging performance regression under sustained volume; architectural change needed. |

---

**Digest generated by Agnes (Sapiens AI) · Data as of 2026-08-22**

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*