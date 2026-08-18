# OpenClaw Ecosystem Digest 2026-08-18

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-18 01:38 UTC

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



# OpenClaw Project Digest — 2026‑08‑18

## 1. Today's Overview
OpenClaw activity remains very high with **500 issues** and **500 PRs** updated in the last 24 hours (482 open/active, 18 closed; 364 open PRs, 136 merged/closed). The project is focused on stabilising session‑state reliability, fixing Codex integration regressions, and improving plugin/version‑compatibility handling. No new release was shipped today; development is concentrated on patch‑level fixes and roadmap‑grade features.

## 2. Releases
*None.*

## 3. Project Progress
**Merged/Closed PRs (today):**
- `#125493` – Preserve newer schema errors during plugin‑install inspection (fixes compatibility‑error mis‑labeling).
- `#125494` – Remove interrupted Slack progress messages when an agent decides not to reply.
- `#125317` – Report missing skills as “not found” in `openclaw skills verify` instead of exposing internal ClawHub paths.
- `#124803` – Defer restored subagent settle‑wake dispatch until the gateway is fully ready.
- `#120900` – Add Control‑UI review flow for install‑policy warnings (security boundary).
- `#125497` – Preserve message delivery after result‑middleware replacement (prevents duplicate fallback replies).
- `#125500` – Record omitted memory‑corpus errors in `corpus=all` searches.

**Active work streams:**
- **CLI/backup:** `#124821` skips managed runtime symlinks during backup; `#125007` renders missing gateway credentials consistently.
- **Web UI:** `#124683` restores terminal run‑error alerts after page reload; `#125249` unifies fenced‑code‑block styling; `#125231` redesigns suggested‑task cards.
- **Channel fixes:** `#121124` stops repeated Feishu doc‑child pagination; `#121186` retries failed Beam terminal‑mirror uploads.
- **Cross‑platform:** `#125286` keeps Windows Git installs on the validated Node runtime; `#117222` shows recent iOS usage days first.

## 4. Community Hot Topics
| Issue | Comments | Key Theme |
|-------|----------|-----------|
| [#77598](https://github.com/openclaw/openclaw/issues/77598) – Track live dev‑agent behaviour | 23 | Observational monitoring of a 24‑hour dev‑agent watch. |
| [#91009](https://github.com/openclaw/openclaw/issues/91009) – Codex PreToolUse hook spawns CPU‑bound processes | 20 | Relay process hoarding causing gateway RPC stalls (P1). |
| [#80319](https://github.com/openclaw/openclaw/issues/80319) – QA suite conflates Codex‑native tools with OpenClaw parity | 18 | Clarification that Codex‑native workspace tools are handled separately. |
| [#68596](https://github.com/openclaw/openclaw/issues/68596) – Configurable streaming watchdog timeout | 15 | Request for longer timeouts when using extended‑reasoning models (kimi‑k2.5, DeepSeek‑R1). |
| [#62505](https://github.com/openclaw/openclaw/issues/62505) – Coding agent never completes (regression) | 15 | Agent stuck on vague status updates; worked in ≤2026.4.2. |

**Underlying needs:** Users demand greater control over agent‑observation loops, robust handling of Codex‑native tool calls, and configurable timeouts for long‑running reasoning models.

## 5. Bugs & Stability
**P1 / Critical Bugs (ranked by severity & impact):**
1. [#91009](https://github.com/openclaw/openclaw/issues/91009) – PreToolUse hook spawns CPU‑bound `openclaw‑hooks` processes, stalling gateway RPC.
2. [#62505](https://github.com/openclaw/openclaw/issues/62505) – Coding agent fails to complete any task (regression from 2026.4.2).
3. [#38327](https://github.com/openclaw/openclaw/issues/38327) – “Cannot convert undefined or null to object” with `google‑vertex/gemini‑3.1‑pro‑preview`.
4. [#74586](https://github.com/openclaw/openclaw/issues/74586) – `memory_search` tool calls abort and are mis‑classified as timeout.
5. [#84516](https://github.com/openclaw/openclaw/issues/84516) – Codex app‑server silently truncates replies at ~1000‑1100 chars.
6. [#67777](https://github.com/openclaw/openclaw/issues/67777) – Subagent completion delivery lost on direct‑announce timeout/drain.
7. [#83959](https://github.com/openclaw/openclaw/issues/83959) – Codex app‑server startup retries exhaust before replacement is ready.
8. [#72015](https://github.com/openclaw/openclaw/issues/72015) – `active‑memory` plugin blocks replies and overloads multi‑agent gateways.
9. [#86215](https://github.com/openclaw/openclaw/issues/86215) – Codex OAuth refresh failures wedge agents for hours without alerting.
10. [#111857](https://github.com/openclaw/openclaw/issues/111857) – CLI budget reopens compacted JSONL branch, inflating prompt estimates.
11. [#97616](https://github.com/openclaw/openclaw/issues/97616) – Leaked unreaped hook/tool child processes cause zombie accumulation.
12. [#53540](https://github.com/openclaw/openclaw/issues/53540) – Embedded runner “Network connection lost” when LLM generates large tool‑call parameters.
13. [#90361](https://github.com/openclaw/openclaw/issues/90361) – Intermittent `memory_search` “index metadata is missing” despite valid builtin index.
14. [#83337](https://github.com/openclaw/openclaw/issues/83337) – Plugin/core version drift after upgrade causes silent channel failure.
15. [#77733](https://github.com/openclaw/openclaw/issues/77733) – `/new` and `/reset` no longer trigger persona greeting (regression).
16. [#107814](https://github.com/openclaw/openclaw/issues/107814) – `gpt‑5.3‑codex‑spark` emits empty arguments for required tool calls.
17. [#78493](https://github.com/openclaw/openclaw/issues/78493) – `sudo openclaw update` creates mixed ownership; `doctor` overwrites config after EACCES.
18. [#77930](https://github.com/openclaw/openclaw/issues/77930) – Discord channel not loaded in 2026.5.4 (regression).
19. [#71689](https://github.com/openclaw/openclaw/issues/71689) – Tasks‑registry restore fails on malformed SQLite image.
20. [#70903](https://github.com/openclaw/openclaw/issues/70903) – Persistent file‑based provider cooldown blocks user for hours after billing recovery.

**Fix PRs in progress (not yet merged):**
- `#125500` – Memory‑corpus error handling for `corpus=all`.
- `#125497` – Message‑delivery preservation after result middleware.
- `#124803` – Subagent settle‑wake deferral until gateway ready.
- `#85308` – Preserve requester wake on visible delivery failure.
- `#121186` – Retry failed Beam terminal‑mirror uploads.
- `#124709` – Resolve registered plugins before agent workspace.
- `#125494` – Clean up interrupted Slack progress messages.
- `#125317` – Improve missing‑skill reporting in CLI.

## 6. Feature Requests & Roadmap Signals
| Issue | Request | Likelihood for Next Release |
|-------|---------|----------------------------|
| [#79902](https://github.com/openclaw/openclaw/issues/79902) | Companion‑friendly SQLite transcript/session seams | Medium (depends on DB‑first runtime migration) |
| [#67413](https://github.com/openclaw/openclaw/issues/67413) | Per‑agent dreaming configuration | High (addressed memory‑spike complaints) |
| [#66252](https://github.com/openclaw/openclaw/issues/66252) | Per‑agent TTS/STT overrides for multi‑language | Medium |
| [#81061](https://github.com/openclaw/openclaw/issues/81061) | `before_route_inbound_message` hook for channel bridging | Low (architectural change) |
| [#75947](https://github.com/openclaw/openclaw/issues/75947) | UI quality update based on UX scoring | High (ongoing UI redesign PRs) |
| [#71142](https://github.com/openclaw/openclaw/issues/71142) | Configurable upload size limit for Control UI | Medium |
|

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — AI Agent & Personal AI Assistant Ecosystem
**Date:** 2026-08-18 | **Scope:** 12 open-source projects

---

## 1. Ecosystem Overview

The 2026 personal AI assistant ecosystem is characterized by rapid architectural diversification, with projects branching along three vectors: **channel/modality expansion** (Slack, Telegram, Weixin, IRC), **provider-agnostic middleware** (MCP, ACP, OpenClaw runtime), and **security-hardened deployments** (SSRF gates, credential scoping, atomic budget tracking). OpenClaw remains the largest reference implementation by issue/PR volume, while ZeroClaw and IronClaw are pursuing deliberate security-first and database-optimization roadmaps respectively. The ecosystem shows signs of consolidation pressure around A2A interoperability (VOKO proposal) and MCP compatibility, though fragmentation across channel adapters and plugin ecosystems remains significant.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Releases | Open Bugs (P1+) | Health Score* |
|---------|-------------|-----------|----------|-----------------|---------------|
| **OpenClaw** | 500 | 500 | None | 20 | 🟢 Active |
| **Hermes Agent** | 50 | 50 | v0.20.3 | 3 | 🟢 Active |
| **ZeroClaw** | 50 | 50 | None (0.8.x→0.9.0) | 2 | 🟢 Active |
| **NanoClaw** | 4 | 42 | None | 2 | 🟢 Active |
| **IronClaw** | 29 | 45 | v1.3.0-rc.1 | 1 (boot crash) | 🟡 Stabilizing |
| **CoPaw** | 12 | 33 | None | 2 | 🟢 Active |
| **LobsterAI** | 7 | 21 | None | 2 | 🟡 Moderate |
| **NanoBot** | 2 | 15 | None | 1 | 🟡 Moderate |
| **Moltis** | 3 | 9 | None | 0 | 🟡 Moderate |
| **PicoClaw** | 3 | 4 | None | 1 | 🟡 Low-Moderate |
| **NullClaw** | 0 | 0 | None | 0 | 🔴 Dormant |
| **ZeptoClaw** | 0 | 0 | None | — | 🔴 Dormant |

*Health Score: 🟢 Active development | 🟡 Moderate/stabilizing | 🔴 Low activity or maintenance mode

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Scale of activity** — 500 issues/PRs in 24h dwarfs all other projects (next highest: Hermes Agent and ZeroClaw at 50 each), indicating the largest contributor base and broadest usage surface.
- **Infrastructure maturity** — Only project with a dedicated security boundary review flow (Control-UI install-policy warnings),成熟的 Codex integration layer, and explicit session-state reliability work.
- **Cross-platform breadth** — Active fixes for Windows Git/Node runtime, iOS usage ordering, Feishu pagination, and Beam terminal uploads suggest widest platform coverage.

**Technical Approach Differences:**
| Dimension | OpenClaw | Peers |
|-----------|----------|-------|
| Core abstraction | Gateway-centric with subagent settle-wake dispatch | Docker/session-driver abstractions (NanoClaw), direct process management (NanoBot) |
| Provider strategy | Codex-native tooling + OpenClaw parity layer | Per-project provider lists (MiniMax, DeepSeek Harness, OrcaRouter) |
| Release cadence | Patch-level fixes, no formal releases | v0.20.3 (Hermes), v1.3.0-rc.1 (IronClaw) |
| Plugin model | ClawHub skills with schema-compatibility inspection | MCP servers (ZeroClaw, LobsterAI), plugin SDK (CoPaw PawApps) |

**Community Size:** OpenClaw's issue volume (~10× next tier) and 482 open/active issues suggest the largest user base, though activity concentration in bug-fixing rather than feature development signals maturity saturation.

---

## 4. Shared Technical Focus Areas

| Requirement | Projects Involved | Specific Need |
|-------------|-------------------|---------------|
| **Session-state reliability** | OpenClaw, NanoClaw, CoPaw | Subagent delivery guarantees, context reload correctness, cross-session isolation |
| **MCP/ACP interoperability** | NanoClaw, LobsterAI, CoPaw, ZeroClaw | Non-SSE transport support, provider-agnostic tool discovery, schema extension APIs |
| **Channel expansion** | NanoClaw, PicoClaw, IronClaw, ZeroClaw | Slack per-thread sessions, Weixin multi-instance, Telegram watchdog, QQ/Mattermost bounded downloads |
| **Security hardening** | ZeroClaw, Hermes Agent, OpenClaw | SSRF gating, credential scoping, atomic budget accounting, `_secure_file` ACLs |
| **Config persistence** | IronClaw, LobsterAI, PicoClaw | Env-only config fallback, groupPolicy stability, terminal.cwd bridging |
| **Cross-provider compatibility** | OpenClaw, Hermes Agent, ZeroClaw | Anthropic/Bedrock auto-titling, Gemini API key header migration, response_format fallback |
| **Cost governance** | NanoBot, ZeroClaw | Spend firewalls, atomic action-budget tracking, fallback provider accounting |
| **Windows compatibility** | NanoBot, Hermes Agent, PicoClaw | Process lifecycle management, venv PID adoption, PowerShell curl aliasing |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | ZeroClaw | NanoClaw | IronClaw | NanoBot | CoPaw |
|-----------|----------|-------------|----------|----------|----------|---------|-------|
| **Primary use case** | General-purpose agent hub | Desktop-first personal assistant | Security-hardened agent runtime | Channel adapter framework | Database-optimized automation | Telegram/CLI bot | Enterprise workspace assistant |
| **Target user** | Power users, devs | Individual desktop users | Security-conscious operators | Multi-channel operators | Ops/DevOps teams | Telegram bot operators | Enterprise teams |
| **Architecture** | Gateway + subagent dispatch | Relay middleware + plugin lifecycle | RFC-governed, pluggable auth | Channel-layer abstraction (Waves A/B) | libSQL write-coalescing epic | Process-identity tracking | Workspace-scoped sessions |
| **Key differentiator** | Codex integration depth | Security audit epic (epic #82591) | Zero-trust credential boundaries | Slack-native per-thread sessions | ~60% DB write reduction | Cross-platform Telegram watchdog | i18n + DataPaw runtime |
| **Tech stack** | Node/TypeScript | Python + Rust | Rust | TypeScript | Rust + libSQL | TypeScript + Python | Python + Electron |
| **Release model** | Patch-level, no tags | Semantic versioning (v0.20.x) | RFC-driven milestones | Unreleased feature branches | RC-based with migration risk | Incremental merges | Pre-release stabilization |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (high velocity, active PR merge cadence):**
- **OpenClaw** — 500/500 daily volume, but bug-fix heavy (20 P1 issues); maturing past feature velocity
- **NanoClaw** — 42 PRs in 24h, channel-layer architecture being built out in public; high risk/reward integration phase
- **ZeroClaw** — 50/50 daily, security RFCs driving coordinated hardening; governance process (RFC ratification) functioning
- **Hermes Agent** — 50/50 daily, post-release patch cycle (v0.20.3), large review backlog (46 open PRs)

**Tier 2 — Steady Development (consistent but lower volume):**
- **IronClaw** — 29/45 daily, RC phase with critical boot-crash regression; database optimization epic dominating roadmap
- **CoPaw** — 12/33 daily, session-persistence bugs indicate post-migration stabilization
- **LobsterAI** — 7/21 daily, strong merge velocity but 4-month stale backlog signals maintainer bandwidth bottleneck

**Tier 3 — Moderate/Low Activity:**
- **NanoBot** — 2/15 daily, Telegram reliability fixes landed; cost-governance feature request emerging
- **Moltis** — 3/9 daily, container runtime gaps (Podman) unresolved; feature PRs merging steadily
- **PicoClaw** — 3/4 daily, tool-failure loop fix merged; channel-specific issues surfacing

**Tier 4 — Dormant/Maintenance:**
- **NullClaw** — 0/0 daily, only Dependabot PR; maintenance mode
- **ZeptoClaw** — No activity reported

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|-------|-------------------------|-------------------------------|
| **Session-state reliability as foundational** | OpenClaw (subagent settle-wake), NanoClaw (session lifecycle driver), CoPaw (context reload), IronClaw (libSQL write lanes) | Session management is the new infrastructure moat; projects solving this well gain enterprise traction |
| **Security hardening as differentiator** | ZeroClaw (SSRF gates, credential scoping, atomic budget), Hermes Agent (security audit epic), OpenClaw (install-policy review) | Security RFCs and audit processes are becoming competitive advantages, not just compliance checkboxes |
| **Channel abstraction layers emerging** | NanoClaw (channels/Wave A+B), PicoClaw (Weixin multi-instance, IRC), LobsterAI (OrcaRouter), OpenClaw (Slack/Feishu/Beam) | One adapter layer per channel is unsustainable; projects offering reusable channel abstractions will attract plugin ecosystems |
| **Cost governance becoming mandatory** | NanoBot (hybrid spend firewall #5409), ZeroClaw (atomic action budget #9996), OpenClaw (CLI budget JSONL branch #111857) | Unbounded LLM spend is a production blocker; guardrails are now table-stakes for commercialization |
| **A2A interoperability demand** | LobsterAI (VOKO proposal #2500, OpenRouter/DSH integrations), ZeroClaw (Chat Completions RFC #8603), CoPaw (provider discovery #6302) | Cross-project agent communication is the next frontier; early standardization efforts will shape ecosystem lock-in |
| **Windows/Linux parity as trust signal** | NanoBot (process identities, venv PIDs, curl aliasing), Hermes Agent (ACLs, terminal tools), OpenClaw (Windows Git/Node runtime) | Cross-platform stability is a retention factor for individual developers and enterprise IT |
| **Config fragility as recurring pain** | PicoClaw (env-only fallback), IronClaw (AGENTS.md not live), Hermes Agent (TERMINAL_CWD false warnings), LobsterAI (groupPolicy overwrite) | Configuration reliability is a silent trust-killer; projects with robust config bridges gain user loyalty |
| **MCP transport gaps** | LobsterAI (non-SSE MCP broken #1662), NanoClaw (extendTool API), ZeroClaw (SOP permission contracts) | MCP is table-stakes but transport compatibility (SSE vs HTTP/streamable) is an unresolved fragmentation point |

---

**Summary:** The ecosystem is fragmenting along architectural lines (gateway vs. channel-abstraction vs. security-first) while converging on shared infrastructure needs (session reliability, cost governance, A2A interoperability). OpenClaw leads in scale but shows maturity saturation; ZeroClaw and NanoClaw are building the next-generation abstraction layers; IronClaw's database optimization work addresses a genuine production pain point. Developers should monitor the VOKO A2A proposal, ZeroClaw's Chat Completions RFC, and NanoClaw's channels architecture as potential convergence points.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-18

## 1. Today's Overview

NanoBot shows **active development velocity** with 15 PRs and 2 issues updated in the past 24 hours. The project is in a stabilization phase: several critical Telegram polling bugfixes were merged, a native TypeScript TUI landed, and CLI gateway internals are being hardened across platforms. One new feature-request issue highlights an emerging concern around LLM cost governance as the project matures toward commercialization. No new release was published today.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**Merged / Closed PRs (5):**

- **#5416** [CLOSED] — Stabilized gateway process identities by replacing locale-dependent macOS `ps lstart` with native `proc_pidinfo` birth timestamps, improving cross-platform process tracking. ([Link](https://github.com/HKUDS/nanobot/pull/5416))
- **#5301** [CLOSED] — Bridged stdlib logging into loguru and added a lightweight Telegram polling liveness check as a precursor to the full watchdog. ([Link](https://github.com/HKUDS/nanobot/pull/5301))
- **#5156** [CLOSED] — Fixed silently stalled Telegram polling after transient network failures, resolving issue #5171 with a full watchdog that rebuilds connection pools. ([Link](https://github.com/HKUDS/nanobot/pull/5156))
- **#5406** [CLOSED] — Introduced a native TypeScript terminal UI for the CLI, superseding the earlier #4329. ([Link](https://github.com/HKUDS/nanobot/pull/5406))
- **#5410** [CLOSED] — Stopped sustained-goal clarification replies from being repeated automatically after normal model responses. ([Link](https://github.com/HKUDS/nanobot/pull/5410))

**Key advances:** Telegram reliability, cross-platform gateway robustness, and CLI UX all received tangible improvements today.

## 4. Community Hot Topics

| Item | Type | Activity | Link |
|------|------|----------|------|
| Telegram polling stalls permanently after network blips | Issue #5171 | 0 comments, resolved via #5156 | [Issue](https://github.com/HKUDS/nanobot/issues/5171) · [PR](https://github.com/HKUDS/nanobot/pull/5156) |
| Hybrid Spend Firewall for LLM cost control | Issue #5409 | Newly opened, 0 comments | [Issue](https://github.com/HKUDS/nanobot/issues/5409) |
| WebUI session messaging via mentions | PR #5358 | Open, active development | [PR](https://github.com/HKUDS/nanobot/pull/5358) |
| WebUI temporary side conversations | PR #5364 | Open, active development | [PR](https://github.com/HKUDS/nanobot/pull/5364) |
| WebUI follow-up suggestions | PR #5408 | Open, just opened | [PR](https://github.com/HKUDS/nanobot/pull/5408) |

**Analysis:** The Telegram stalling issue (#5171) reflects a real production pain point — users running bots behind unstable proxies need resilient polling. The #5409 spend-firewall issue signals that as NanoBot scales, **cost governance** is becoming a community priority. The cluster of three WebUI feature PRs (#5358, #5364, #5408) shows the team is investing heavily in richer conversational UX.

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR | Link |
|----------|------|-------------|--------|------|
| **High** | #5171 / #5156 | Telegram polling stalls silently after transient network failures; bot stops receiving messages permanently | #5156 (closed) | [Issue](https://github.com/HKUDS/nanobot/issues/5171) · [PR](https://github.com/HKUDS/nanobot/pull/5156) |
| **Medium** | #5407 | Cron heartbeat/dream system jobs persist and burn tokens even after being disabled in config | #5407 (open) | [PR](https://github.com/HKUDS/nanobot/pull/5407) |
| **Medium** | #5410 | Sustained-goal clarification replies were re-injected after every plain-text response, causing repetition loops | #5410 (closed) | [PR](https://github.com/HKUDS/nanobot/pull/5410) |
| **Medium** | #5413 | LLM provider exceptions escaped the fallback loop entirely instead of triggering failover | #5413 (open) | [PR](https://github.com/HKUDS/nanobot/pull/5413) |
| **Low** | #5341 | Weather skill fails on Windows PowerShell due to bare `curl` aliasing to `Invoke-WebRequest` | #5341 (open) | [PR](https://github.com/HKUDS/nanobot/pull/5341) |
| **Low** | #5414 | Slack file downloads across redirects lacked URL validation, opening a redirect-based injection vector | #5414 (open) | [PR](https://github.com/HKUDS/nanobot/pull/5414) |
| **Low** | #5412 | Background gateway process stdout was block-buffered, delaying startup messages in logs | #5412 (open) | [PR](https://github.com/HKUDS/nanobot/pull/5412) |
| **Low** | #5415 | Windows venv child process PID adoption was broken in the gateway | #5415 (open) | [PR](https://github.com/HKUDS/nanobot/pull/5415) |

The high-severity Telegram bug is now fixed. Two medium-severity issues (#5407, #5413) still have open PRs awaiting merge.

## 6. Feature Requests & Roadmap Signals

| Item | Type | Description | Link |
|------|------|-------------|------|
| Issue #5409 | Feature request | Hybrid spend firewall to prevent infinite loops from bankrupting LLM budgets | [Issue](https://github.com/HKUDS/nanobot/issues/5409) |
| PR #5358 | In progress | WebUI session messaging via `@mentions` with stable server-owned session names | [PR](https://github.com/HKUDS/nanobot/pull/5358) |
| PR #5364 | In progress | Temporary side conversations with `/side` command, tab switching, parallel sending | [PR](https://github.com/HKUDS/nanobot/pull/5364) |
| PR #5408 | In progress | Ephemeral follow-up suggestions after WebUI turns (DeerFlow-style) | [PR](https://github.com/HKUDS/nanobot/pull/5408) |
| PR #5411 | In progress | Refactor to isolate local agent runtime into a dedicated module | [PR](https://github.com/HKUDS/nanobot/pull/5411) |

**Prediction:** The three WebUI conversational features (session mentions, side conversations, follow-up suggestions) are likely to ship together in the next minor release as a cohesive UX update. The spend-firewall request (#5409) is too new to gauge timeline but aligns with a commercialization-ready roadmap.

## 7. User Feedback Summary

- **Telegram reliability under unstable networks** is a verified production pain point (#5171). Users running bots behind proxies or in regions with spotty connectivity experienced permanent message loss with no log warnings — a trust-eroding bug now resolved.
- **Cost governance concerns** are emerging (#5409). As users adopt NanoBot for more aggressive agent loops, the risk of unbounded LLM spend is top-of-mind. The community is asking for guardrails before commercial deployment.
- **Windows compatibility** remains an ongoing theme: PRs #5341 (weather skill), #5415 (gateway venv), and #5416 (process identities) all target Windows-specific issues, suggesting the project is actively broadening cross-platform support.
- **CLI UX expectations** are rising — the introduction of a native TypeScript TUI (#5406) and runtime isolation refactor (#5411) indicate users want a polished, responsive terminal experience.

## 8. Backlog Watch

| Item | Type | Age | Risk | Link |
|------|------|-----|------|------|
| #5409 | Feature request (spend firewall) | 1 day | High — commercialization blocker if unaddressed | [Issue](https://github.com/HKUDS/nanobot/issues/5409) |
| #5407 | Bug (stale cron jobs) | 1 day | Medium — token waste in production | [PR](https://github.com/HKUDS/nanobot/pull/5407) |
| #5413 | Bug (provider fallback bypass) | 1 day | Medium — silent failures in multi-provider setups | [PR](https://github.com/HKUDS/nanobot/pull/5413) |
| #5341 | Bug (Windows weather skill) | 7 days | Low — workaround exists | [PR](https://github.com/HKUDS/nanobot/pull/5341) |
| #5358 | Feature (session mentions) | 6 days | — | [PR](https://github.com/HKUDS/nanobot/pull/5358) |
| #5364 | Feature (side conversations) | 5 days | — | [PR](https://github.com/HKUDS/nanobot/pull/5364) |
| #5408 | Feature (follow-up suggestions) | 1 day | — | [PR](https://github.com/HKUDS/nanobot/pull/5408) |

**Notable:** No issues have comments or reactions yet, which is typical for a fast-moving project with many contributors. The **#5409 spend firewall** issue deserves early maintainer attention as it addresses a scaling risk. The three WebUI PRs (#5358, #5364, #5408) should be coordinated to avoid merge conflicts given overlapping concerns.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-18

## 1. Today's Overview

Hermes Agent shows sustained development velocity with 50 issues and 50 PRs touched in the past 24 hours, indicating a highly active contributor base. The latest patch release **v0.20.3** (v2026.8.16.2) was published on August 16, consolidating ~125 merged PRs into a stable build. Four PRs were merged or closed today, while 46 remain open for review. The project is in a hardening phase, with significant focus on security remediation (a dedicated audit epic), desktop stability, and MCP/session-state reliability.

## 2. Releases

**Hermes Agent v0.20.3** (tag: v2026.8.16.2) — released 2026-08-16

Patch release rolling up ~125 PRs since v0.20.2. Targets downstream consumers (Docker images, hosted deployments, fresh installs). No breaking changes announced; this is a stability and security patch bundle.

## 3. Project Progress

**Merged / Closed Today (4 PRs):**

- **#85579** — *fix(relay): use canonical managed operation names* — NeMo Relay middleware now dispatches on canonical Hermes API operation names (`openai.chat_completions`, `openai.responses`, `anthropic.messages`) rather than provider-supplied names. Improves plugin dispatch reliability. ([PR #85579](https://github.com/NousResearch/hermes-agent/pull/85579))

**Open PRs Advancing Key Areas:**

- **#88834** — *fix(titles): retry without response_format* — Auto-titling now falls back gracefully on providers that reject OpenAI-only `response_format` (e.g., DeepSeek). ([PR #88834](https://github.com/NousResearch/hermes-agent/pull/88834))
- **#88821** — *MCP write-capable tools: no duplicate side effects on session expiry* — Prevents blind retry of write MCP calls that may have already executed server-side. Ported from Cloudflare OS. ([PR #88821](https://github.com/NousResearch/hermes-agent/pull/88821))
- **#88807** — *fix(desktop): preserve cross-machine group routing* — Repairs OAuth and registry lookup for remote-primary desktop bots. ([PR #88807](https://github.com/NousResearch/hermes-agent/pull/88807))
- **#88832** — *feat(plugins): expose gateway route context* — Plugins gain stable session-key and source metadata through middleware lifecycle, without leaking into model-visible tool args. ([PR #88832](https://github.com/NousResearch/hermes-agent/pull/88832))
- **#88647** — *Design together on a live pen.dev canvas* — Experimental feature pairing the pen.dev drawing canvas alongside the chat for collaborative agent-assisted design. ([PR #88647](https://github.com/NousResearch/hermes-agent/pull/88647))
- **#88828** — *fix(desktop): one roster row per bot* — Eliminates duplicate backend entries in the Bot Mode roster when a single backend registers under multiple addresses. ([PR #88828](https://github.com/NousResearch/hermes-agent/pull/88828))

## 4. Community Hot Topics

| Issue | Title | Comments | Status |
|-------|-------|----------|--------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index stale/degraded (29.8h old vs 26h limit) | 48 | Open |
| [#42961](https://github.com/NousResearch/hermes-agent/issues/42961) | `terminal.cwd` config ignored for local backend | 11 | Open |
| [#85695](https://github.com/NousResearch/hermes-agent/issues/85695) | False-positive `TERMINAL_CWD` deprecation warning on gateway start | 9 | Open |
| [#16636](https://github.com/NousResearch/hermes-agent/issues/16636) | Expandable Tool Call Messages in TUI | 5 (+1 👍) | Open |
| [#77305](https://github.com/NousResearch/hermes-agent/issues/77305) | Subagent failed API calls consume iteration budget, starving fallback chain | 5 | Open |

**Analysis:** The top-voted issue (#66616) reflects a operational reliability concern — the skills index watchdog has been flagged degraded for weeks, suggesting the cron rebuild pipeline may be intermittently failing. The `terminal.cwd` family (#42961, #85695, #88829) is a recurring config-bridge bug causing user friction across CLI and gateway starts. The TUI expandable tool calls feature (#16636) indicates users want better observability into tool execution without leaving the terminal.

## 5. Bugs & Stability

**Critical / High Severity:**

- **#77462** — [CRITICAL] Windows `_secure_file` is a no-op; secrets readable by SYSTEM/Administrators. ACLs are not set, only read-only bit toggled. Live red-team verified. ([Issue #77462](https://github.com/NousResearch/hermes-agent/issues/77462))
- **#84265** — Legacy body-only webhook HMAC replayable after local dedup expires. ([Issue #84265](https://github.com/NousResearch/hermes-agent/issues/84265))
- **#84271** — Explicit empty `execute_code` capability broadens to all sandbox tools. ([Issue #84271](https://github.com/NousResearch/hermes-agent/issues/84271))
- **#88661** — MCP tool timeout parks entire server connection; all tools unregister with no auto-reconnect. ([Issue #88661](https://github.com/NousResearch/hermes-agent/issues/88661))
- **#77305** — Subagent retry budget starvation: failed API calls consume iteration budget before fallback can activate. ([Issue #77305](https://github.com/NousResearch/hermes-agent/issues/77305))
- **#48860** — OAuth prompt sanitizer greedily rewrites docs URL to dead `claude-code.nousresearch.com` (NXDOMAIN). ([Issue #48860](https://github.com/NousResearch/hermes-agent/issues/48860))
- **#80898** — macOS: orphaned `hermes serve` backends accumulate across desktop restarts. [CLOSED] — fixed via #76245. ([Issue #80898](https://github.com/NousResearch/hermes-agent/issues/80898))
- **#88810** — Windows terminal tool crashes on `embedded null character in path` (missing `ValueError` catch in `lifecycle_guard.py`). ([Issue #88810](https://github.com/NousResearch/hermes-agent/issues/88810))
- **#85624** — Auto-title fails 100% on Bedrock/Anthropic providers due to leaked OpenAI `response_format`. Fix PR #88834 opened. ([Issue #85624](https://github.com/NousResearch/hermes-agent/issues/85624))
- **#84033** — macOS `computer_use` daemon loses TCC accessibility identity when launched as embedded child. ([Issue #84033](https://github.com/NousResearch/hermes-agent/issues/84033))

**Medium Severity:**

- **#79101** — API session stores virtual model alias as real model, breaking gateway default. [CLOSED] ([Issue #79101](https://github.com/NousResearch/hermes-agent/issues/79101))
- **#57921** — `timeout=1.0` in `hermes_state.py` causes "database is locked" under GIL pressure. [CLOSED] ([Issue #57921](https://github.com/NousResearch/hermes-agent/issues/57921))
- **#76064** — Demo plugins shipped enabled by default in Desktop production. [CLOSED] ([Issue #76064](https://github.com/NousResearch/hermes-agent/issues/76064))
- **#76245** — Desktop backend not reliably drained on quit (orphaned processes). [CLOSED] ([Issue #76245](https://github.com/NousResearch/hermes-agent/issues/76245))
- **#84248** — Docker cgroup probe failure strips resource limits. ([Issue #84248](https://github.com/NousResearch/hermes-agent/issues/84248))
- **#84263** — Timed-out external memory prefetch threads remain detached/uncancellable. ([Issue #84263](https://github.com/NousResearch/hermes-agent/issues/84263))
- **#77476** — CI test-runner fragility: exit-code-5 treated as PASS, flake retry launders gate failures, no Windows CI job. ([Issue #77476](https://github.com/NousResearch/hermes-agent/issues/77476))
- **#88762** — Qwen 3.8 fails locally where Qwen 3.6 works. ([Issue #88762](https://github.com/NousResearch/hermes-agent/issues/88762))

**Security Audit Epic (#82591)** is driving a cluster of related findings (issues #84259, #84248, #84265, #84271, #84254, #84263) — a coordinated hardening effort across the codebase.

## 6. Feature Requests & Roadmap Signals

- **#16636** — Expandable Tool Call Messages in TUI (5 comments, 1 👍). Users want inline tool-call detail expansion rather than relying on hover or external logs. Likely candidate for a future TUI enhancement.
- **#84177** — Design Mode: element selection bridge from desktop preview/browser to agent context. Click an element → structured context (tag, classes, bounding box) piped to agent. Early-stage feature request; could align with the pen.dev canvas work in PR #88647.
- **#88832** — Gateway route context exposure for plugins (open PR). Signals a roadmap direction toward richer plugin middleware and stable per-request identity.
- **#88647** — pen.dev collaborative canvas beside chat (open PR). If merged, represents a new multimodal interaction surface for the Desktop app.

## 7. User Feedback Summary

- **Config brittleness** is a top pain point: the `TERMINAL_CWD` deprecation warning fires falsely (#85695, #88829), and `terminal.cwd` is silently ignored for the local backend (#42961). Users perceive this as unreliable configuration handling.
- **Desktop process lifecycle** issues (orphaned backends on macOS #80898, incomplete quit cleanup #76245) suggest the Electron app's child-process management needs stronger safeguards.
- **MCP timeout behavior** (#88661) is frustrating: a single slow tool call kills the entire toolset for a session, requiring a gateway restart.
- **Windows security** (#77462) is a serious concern — secrets file permissions are effectively a no-op, undermining the confidentiality guarantees users expect.
- **Cross-provider compatibility** remains fragile: auto-titling breaks on Anthropic/Bedrock (#85624), and OAuth URL rewriting produces dead links (#48860).

## 8. Backlog Watch

| Issue | Days Open | Why It Needs Attention |
|-------|-----------|----------------------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index degraded | ~31 days | Core functionality (skills discovery) impaired; cron may be silently failing. |
| [#77462](https://github.com/NousResearch/hermes-agent/issues/77462) — Windows `_secure_file` no-op | ~15 days | **Critical** security finding with live red-team validation; no fix PR yet. |
| [#77305](https://github.com/NousResearch/hermes-agent/issues/77305) — Subagent budget starvation | ~15 days | Fallback chain reliability depends on this; no fix PR yet. |
| [#77476](https://github.com/NousResearch/hermes-agent/issues/77476) — CI test fragility | ~15 days | Gate file silently passes on missing tests; no Windows CI; affects release confidence. |
| [#84254](https://github.com/NousResearch/hermes-agent/issues/84254) — CI treats skipped/non-failure as pass, excludes Docker | ~6 days | Security-audit-class finding; CI gate is unreliable. |
| [#42961](https://github.com/NousResearch/hermes-agent/issues/42961) — `terminal.cwd` ignored | ~70 days | Long-open config bug; 11 comments indicate sustained user frustration. |
| [#88712](https://github.com/NousResearch/hermes-agent/issues/88712) — TUI ScrollBox test failures | ~1 day | 2 of 4 tests failing on v2026.8.16; may block future TUI changes. |

---

**Project Health Assessment:** Hermes Agent is in an active stabilization cycle. The v0.20.3 patch release and the security audit epic (#82591) show disciplined release management. However, several critical-severity security findings (#77462, #84265, #84271) and long-open config bugs (#42961) warrant maintainer prioritization. The high issue/PR volume (50 each in 24h) with only 4 merges suggests a large review backlog that could slow release cadence if not addressed.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-18

## 1. Today's Overview

PicoClaw maintained moderate activity over the last 24 hours, with 3 issues and 4 pull requests updated. The project shows healthy contributor engagement: 3 of 4 PRs were merged or closed, and 1 of 3 issues was resolved. No new releases were published, suggesting the team is in a stabilization phase focused on bug fixes rather than feature launches. The overall project health appears solid, with active community participation and responsive maintainership.

## 2. Releases

No new releases were published during this period.

## 3. Project Progress

**Merged / Closed PRs (3):**

- **#3312** — Fixed the "stuck turn" bug where the agent would silently loop until `max_tool_iterations` when a tool failed with the same error repeatedly. ([Link](https://github.com/sipeed/picoclaw/pull/3312))
- **#271** — Resolved a configuration regression: when `config.json` is absent (common in Fly.io deployments relying on env/secrets), `LoadConfig` now correctly applies environment variable overrides instead of defaulting to an unconfigured model. ([Link](https://github.com/sipeed/picoclaw/pull/271))
- **#2606** — Enhanced Weixin channel support with multi-instance handling, improved validation, and better error handling across backend, frontend, and documentation. ([Link](https://github.com/sipeed/picoclaw/pull/2606))

**Open PRs (1):**

- **#3340** — Addresses a Slack media upload bug where `FileSize` was omitted from upload parameters, causing `slack-go` v0.23.1 to reject requests before any network call. ([Link](https://github.com/sipeed/picoclaw/pull/3340))

## 4. Community Hot Topics

- **Issue #3287** — *Better support for long messages in IRC* (6 comments, created 2026-07-22) — Users need PicoClaw to treat IRCv3 long messages as cohesive units rather than silently splitting them at 512 bytes. This reflects a growing demand for robust multi-channel support, especially for chat platforms with inherent message-size constraints. ([Link](https://github.com/sipeed/picoclaw/issues/3287))
- **Issue #3311 / PR #3312** — *Repeated tool failure loops* — A production-reported pain point over Telegram where the agent loops silently for minutes on identical tool failures (e.g., `git` without credentials). The fix has been merged (#3312). This highlights a need for better agent-level error recovery and user-facing feedback during tool failures. ([Link](https://github.com/sipeed/picoclaw/issues/3311))
- **Issue #3339** — *Google Antigravity 429 errors despite valid OAuth* (created 2026-08-17) — A fresh bug report indicating that Google Antigravity authentication succeeds but all generation requests are rejected with `RESOURCE_EXHAUSTED`. No comments yet. ([Link](https://github.com/sipeed/picoclaw/issues/3339))

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **High** | [#3311](https://github.com/sipeed/picoclaw/issues/3311) | Agent spins silently to `max_tool_iterations` on repeated identical tool failures, never returning a response to the user | ✅ **#3312** (merged) |
| **Medium** | [#3339](https://github.com/sipeed/picoclaw/issues/3339) | Google Antigravity returns 429 `RESOURCE_EXHAUSTED` despite valid OAuth and successful model discovery | None yet |
| **Medium** | [#3340](https://github.com/sipeed/picoclaw/pull/3340) | Slack media uploads fail due to missing `FileSize` in upload parameters (slack-go v0.23.1) | 🔶 **#3340** (open) |
| **Low** | [#271](https://github.com/sipeed/picoclaw/issues/271) | Env overrides ignored when `config.json` is absent | ✅ **#271** (merged) |

The most impactful bug — the silent tool-failure loop — has been addressed. The Slack upload issue remains open and may block media functionality for Slack users. The Antigravity 429 issue needs maintainer triage as it affects Google-model users.

## 6. Feature Requests & Roadmap Signals

- **IRC long-message support (#3287)** — Request for IRCv3 message coalescing. This is a channel-specific enhancement that signals growing usage of IRC as a bot interface. Likely candidate for a future channel-compatibility release.
- **Weixin multi-instance support (#2606)** — Just merged, indicating the team is actively expanding multi-channel and multi-instance capabilities. Expect further work in this direction.
- No explicit feature requests beyond the above were raised this period.

## 7. User Feedback Summary

Users are reporting real production pain points:
- **Frustration with silent failures** — The tool-failure loop (#3311) caused users to wait minutes with no response, a significant UX degradation in production Telegram usage.
- **Configuration fragility** — Fly.io deployments that rely on env-only config (#271) were silently misconfigured, pointing to a gap in the deployment experience.
- **Channel-specific limitations** — IRC long-message handling (#3287) and Slack media uploads (#3340) show that as PicoClaw expands across channels, edge cases in each platform's API are surfacing.
- **Google model reliability concerns** — The Antigravity 429 bug (#3339) may indicate quota or rate-limit issues on Google's side, but users perceive it as a PicoClaw integration problem.

Overall satisfaction appears mixed: bug fixes are landing promptly, but the volume of channel-specific issues suggests integration maturity is still a work in progress.

## 8. Backlog Watch

- **Issue #3287** (IRC long messages) — Open since 2026-07-22 with 6 comments and a `[stale]` label. Requires maintainer attention to re-engage the contributor or close if out of scope.
- **Issue #3339** (Antigravity 429) — Open since 2026-08-17 with 0 comments. A fresh, untriaged bug that could affect Google-model users broadly. Needs rapid assessment.
- **PR #3340** (Slack FileSize) — Open since 2026-08-17 with no maintainer review yet. A straightforward fix that should be prioritized given its impact on Slack media functionality.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-18

## 1. Today's Overview

NanoClaw shows **very high development velocity** today with 42 PRs updated in the last 24 hours and 4 issues touched. The project is in an active integration phase around its new **channels architecture**, with a large stacked PR series from `gavrielc` landing the Slack channel layer, session lifecycle drivers, and generic hooks across the router and delivery system. Activity is concentrated on merging channel/adapters infrastructure rather than on user-facing releases — no new versions were published today. The repo is healthy and moving fast, though the density of open PRs (17 still open) suggests a busy merge window ahead.

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Author | Summary |
|----|--------|---------|
| [#3310](https://github.com/nanocoai/nanoclaw/pull/3310) | gavrielc | Restored `slack-formatting` container skill silently dropped during upstream-main merge |
| [#3309](https://github.com/nanocoai/nanoclaw/pull/3309) | gavrielc | **Slack channel-layer Wave B** — defaults factory, membership, onboarding, A2A guard; `sessionMode: per-thread` declared everywhere |
| [#3305](https://github.com/nanocoai/nanoclaw/pull/3305) | gavrielc | **Slack channel-layer Wave A** — shared Slack Web API client + token-key convention, canvas cluster |
| [#3304](https://github.com/nanocoai/nanoclaw/pull/3304) | gavrielc | Adapter-declared `sessionMode` context defaults (`shared` | `per-thread`) for channel adapters |
| [#3292](https://github.com/nanocoai/nanoclaw/pull/3292) | gavrielc | Inbound-policy registration seam on the Chat SDK bridge |
| [#3297](https://github.com/nanocoai/nanoclaw/pull/3297) | gavrielc | Per-channel pre-step and companion-skill declarations for the setup wizard |
| [#3293](https://github.com/nanocoai/nanoclaw/pull/3293) | gavrielc | `session-created` hook in the router for brand-new engaged sessions |
| [#3294](https://github.com/nanocoai/nanoclaw/pull/3294) | gavrielc | Post-delivery hook with first-delivery context in the outbound drain loop |
| [#3296](https://github.com/nanocoai/nanoclaw/pull/3296) | gavrielc | `extendTool` — additive MCP tool schema/description extension point |
| [#3295](https://github.com/nanocoai/nanoclaw/pull/3295) | gavrielc | Generic membership-event hook on the Chat SDK bridge |

### Open PRs Advancing Today

| PR | Author | Summary |
|----|--------|---------|
| [#3311](https://github.com/nanocoai/nanoclaw/pull/3311) | wakqasahmed | Route scheduled-task errors to the operator instead of writing them as chat messages |
| [#3307](https://github.com/nanocoai/nanoclaw/pull/3307) | gavrielc | Host session lifecycle routed through the new `SessionDriver` seam |
| [#3308](https://github.com/nanocoai/nanoclaw/pull/3308) | gavrielc | Refuse to create a group over an existing undisposed folder (data-loss prevention) |
| [#3306](https://github.com/nanocoai/nanoclaw/pull/3306) | gavrielc | New `src/drivers/` module — session-runtime driver seam with Docker as built-in |
| [#3303](https://github.com/nanocoai/nanoclaw/pull/3303) | glifocat | Keep run logs for task rows firing in chat sessions |
| [#3302](https://github.com/nanocoai/nanoclaw/pull/3302) | wakqasahmed | Fix OneCLI gateway default bind address (`ONECLI_URL` not propagated to gateway) |
| [#3298](https://github.com/nanocoai/nanoclaw/pull/3298) | amit-shafnir | **Feature:** Local web chat channel adapter with loopback-only browser UI |
| [#3300](https://github.com/nanocoai/nanoclaw/pull/3300) | torbenstruever | Fix: escape `type` field in agent-facing XML attachment formatting |
| [#3291](https://github.com/nanocoai/nanoclaw/pull/3291) | glifocat | Bound pending-message polling for accumulated backlogs |
| [#3299](https://github.com/nanocoai/nanoclaw/pull/3299) | chiptoe-svg | Bump `@openai/codex` pin 0.138.0 → 0.146.0 before GPT-5.4 retirement (2026-08-31) |

**Key theme:** The `channels/` subsystem is being built out as a modular adapter layer. Nine PRs in a single stacked series by `gavrielc` establish hooks, session modes, driver abstractions, and Slack-specific wiring — a major architectural expansion.

---

## 4. Community Hot Topics

| Item | Type | Author | Link | Analysis |
|------|------|--------|------|----------|
| Issue #3301 | Bug | glifocat | [ISSUE #3203](https://github.com/nanocoai/nanoclaw/issues/3203) | Tasks firing inside chat sessions switch the whole query into "task mode," dropping logs and eating replies. This is a regression from the one-door task delivery change (#2988, v2.1.48). Directly impacts multi-modal users running tasks alongside conversation. Fix PR #3303 is open. |
| Issue #3289 | Bug | glifocat | [ISSUE #3289](https://github.com/nanocoai/nanoclaw/issues/3289) | `getPendingMessages()` loads all due pending rows into JavaScript before throttling, causing memory pressure on accumulated backlogs. Fix PR #3291 is open. |
| Issue #3203 | Bug | mshirel | [ISSUE #3203](https://github.com/nanocoai/nanoclaw/issues/3203) | The `codex` provider emits an undeclared `file` `ProviderEvent`, breaking typecheck on `main` and silently dropping generated images. Fix PR #3299 addresses a related dependency issue but not the type mismatch directly. |
| Issue #1143 | Documentation | nanoclaw-community-triage[bot] | [ISSUE #1143](https://github.com/nanocoai/nanoclaw/issues/1143) | Skill docs still reference `/data/env` path that was removed. Stale documentation causing user confusion. |
| PR #3298 | Feature | amit-shafnir | [PR #3298](https://github.com/nanocoai/nanoclaw/pull/3298) | Local web chat channel adapter — a loopback-only browser UI. Signals user demand for lightweight, no-auth chat surface for local/development use cases. |
| PR #3299 | Fix | chiptoe-svg | [PR #3299](https://github.com/nanocoai/nanoclaw/pull/3299) | Urgent `@openai/codex` version bump ahead of GPT-5.4 retirement on 2026-08-31. Time-sensitive dependency maintenance. |

---

## 5. Bugs & Stability

| Rank | Issue/PR | Severity | Description | Fix PR |
|------|----------|----------|-------------|--------|
| 1 | [#3301](https://github.com/nanocoai/nanoclaw/issues/3301) | **High** | Tasks in chat sessions enter "task mode," causing logs to be dropped and replies eaten. A regression from v2.1.48 one-door delivery. | [#3303](https://github.com/nanocoai/nanoclaw/pull/3303) (open) |
| 2 | [#3289](https://github.com/nanocoai/nanoclaw/issues/3289) | **High** | Pending-message polling loads all due rows into JS memory before applying `maxConcurrency`, dangerous on backlogged instances. | [#3291](https://github.com/nanocoai/nanoclaw/pull/3291) (open) |
| 3 | [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) | **Medium** | `codex` provider emits undeclared `file` `ProviderEvent`, breaking typecheck and silently dropping generated images. | Partially addressed by [#3299](https://github.com/nanocoai/nanoclaw/pull/3299) (dependency bump); type fix still open |
| 4 | [#3300](https://github.com/nanocoai/nanoclaw/pull/3300) | **Medium** | `type` field not escaped in agent-facing XML attachment formatting — potential injection/vector issue. | PR [#3300](https://github.com/nanocoai/nanoclaw/pull/3300) (open) |
| 5 | [#1143](https://github.com/nanocoai/nanoclaw/issues/1143) | **Low** | Stale skill docs reference removed `/data/env` path. | No fix PR yet |
| 6 | [#3302](https://github.com/nanocoai/nanoclaw/pull/3302) | **Low** | OneCLI gateway bind address not written to `.env`, breaking container-to-gateway connectivity. | PR [#3302](https://github.com/nanocoai/nanoclaw/pull/3302) (open) |

**Stability assessment:** Two high-severity bugs (task mode regression, memory loading) are actively being addressed with open PRs. The codex type issue and XML escaping fix are medium priority. No crashes reported today. The project is in a volatile integration phase with many stacked PRs — expect some merge-related regressions.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Analysis |
|--------|--------|----------|
| **Local web chat adapter** | [#3298](https://github.com/nanocoai/nanoclaw/pull/3298) | Loopback-only browser UI for development/local use. Suggests demand for a zero-config chat surface without external platform dependencies. Likely candidate for inclusion in the next release alongside the channels subsystem. |
| **Session-runtime driver abstraction** | [#3306](https://github.com/nanocoai/nanoclaw/pull/3306) | New `src/drivers/` seam decouples session lifecycle from Docker-specific implementation. Enables future runtime backends (podman, k8s, etc.). Major architectural feature. |
| **MCP tool extension point** | [#3296](https://github.com/nanocoai/nanoclaw/pull/3296) | `extendTool()` API allows additive schema/description extension without editing base tool source. Signals a push toward a more plugin-friendly MCP ecosystem. |
| **Slack channel layer ( Waves A & B )** | [#3305](https://github.com/nanocoai/nanoclaw/pull/3305), [#3309](https://github.com/nanocoai/nanoclaw/pull/3309) | Full Slack integration with per-thread session mode, canvas cluster, defaults factory, membership hooks, and onboarding. This is the flagship channel addition — expect Slack to be highlighted in the next release notes. |
| **Per-channel wizard pre-steps** | [#3297](https://github.com/nanocoai/nanoclaw/pull/3297) | Setup wizard extension points for programmatic credential acquisition and companion skills. Improves onboarding UX for complex integrations. |
| **GPT-5.4 Codex compatibility** | [#3299](https://github.com/nanocoai/nanoclaw/pull/3299) | Time-sensitive dependency bump ahead of 2026-08-31 model retirement. Operational maintenance rather than a feature, but critical for users relying on the codex provider. |

**Next release prediction:** The channels subsystem (Slack Wave A+B, driver seam, hooks, local web chat) is the clear candidate for the next major feature release. The one-door task delivery fixes (#3301/#3303) and pending-message bounds (#3289/#3291) should also ship as stability fixes.

---

## 7. User Feedback Summary

| Pain Point | Source | Sentiment |
|------------|--------|-----------|
| Tasks firing in chat sessions corrupt the query mode, dropping logs and swallowing replies | [#3301](https://github.com/nanocoai/nanoclaw/issues/3301) (glifocat) | **Frustrated** — regression from v2.1.48 breaks multi-task workflows |
| Pending message backlog causes unbounded memory load | [#3289](https://github.com/nanocoai/nanoclaw/issues/3289) (glifocat) | **Concerned** — scalability issue for active deployments |
| Codex-generated images silently dropped due to undeclared event type | [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) (mshirel) | **Frustrated** — silent data loss is worse than a crash |
| Skill documentation references removed paths | [#1143](https://github.com/nanocoai/nanoclaw/issues/1143) | **Annoyed** — stale docs waste time |
| OneCLI gateway unreachable from agent containers due to bind address misconfiguration | [#3302](https://github.com/nanocoai/nanoclaw/pull/3302) (wakqasahmed) | **Frustrated** — setup friction for OneCLI users |
| Demand for lightweight local chat surface | [#3298](https://github.com/nanocoai/nanoclaw/pull/3298) (amit-shafnir) | **Positive** — feature request being actively addressed |
| Upcoming GPT-5.4 retirement in Codex | [#3299](https://github.com/nanocoai/nanoclaw/pull/3299) (chiptoe-svg) | **Urgent** — time-sensitive fix being proactively handled |

**Overall sentiment:** Users are experiencing pain from recent architectural changes (one-door task delivery, upstream merges) causing regressions. The community is engaged and submitting detailed bug reports with fix PRs. The proactive channel-layer expansion signals strong maintainer responsiveness.

---

## 8. Backlog Watch

| Item | Type | Author | Age | Risk | Notes |
|------|------|--------|-----|------|-------|
| [#3203](https://github.com/nanocoai/nanoclaw/issues/3203) | Bug | mshirel | 10 days | **Medium** | Codex `file` event type mismatch — partially addressed by #3299 but the typecheck fix itself is still open. No comments since creation. |
| [#1143](https://github.com/nanocoai/nanoclaw/issues/1143) | Documentation | triage bot | 5 months | **Low** | Stale `/data/env` docs. Closed but no visible doc fix PR linked. |
| [#3307](https://github.com/nanocoai/nanoclaw/pull/3307) | Feature | gavrielc | 1 day | **Low** | Session lifecycle through driver seam — stacked on #3306, awaiting merge window. |
| [#3308](https://github.com/nanocoai/nanoclaw/pull/3308) | Fix | gavrielc | 1 day | **Low** | Group creation over existing folder — stacked, low risk, awaiting merge. |

**Maintainer attention needed:** The two high-severity bug fix PRs (#3303 for task-mode regression, #3291 for pending-message bounds) should be prioritized for merge before the next release. Issue #3203 (codex type mismatch) lacks a dedicated fix PR and should be tracked.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-18

## 1. Today's Overview
NullClaw shows minimal activity today, with **0 new issues** and **0 new merged/closed pull requests** in the last 24 hours. The only recent event is a Dependabot-triggered PR (#956) updating the Alpine base image from 3.23 to 3.24, last updated on 2026-08-17. No new releases were published. The project appears to be in a **low-activity maintenance phase**, with no visible feature development or critical bug resolution underway.

## 2. Releases
No new releases have been published recently. There are no release notes, changelogs, or version tags to report on this cycle.

## 3. Project Progress
**Merged/closed PRs today: 0**

The sole recent PR activity is:
- **#956** — `ci(deps): bump alpine from 3.23 to 3.24` ([PR #956](https://github.com/nullclaw/nullclaw/pull/956)) — Still **open**, authored by Dependabot, last updated 2026-08-17. This is a routine dependency bump with no functional changes to the project itself; it updates the Docker base image for security and compatibility alignment.

No features were advanced or bugs fixed during this reporting period.

## 4. Community Hot Topics
No issues or PRs generated significant comment activity or reactions today. The only notable item is:

- **[PR #956](https://github.com/nullclaw/nullclaw/pull/956)** — Dependabot dependency update (0 comments, 0 👍). This is an automated PR with no community discussion.

**Assessment:** There are no active community hot topics. The absence of user-driven discussions, issues, or debates suggests either a quiet contributor base or a project not currently drawing community attention.

## 5. Bugs & Stability
**No bugs, crashes, or regressions were reported today.** There are 0 open issues, so no severity-ranked bugs are visible. No fix PRs are associated with any reported stability concerns.

## 6. Feature Requests & Roadmap Signals
**No feature requests were filed today.** With zero open issues and no community discussion, there are no observable roadmap signals from the user base. The Dependabot PR (#956) reflects only infrastructure maintenance, not product direction.

## 7. User Feedback Summary
No user feedback was captured during this period. There are no open issues or PR comments to analyze for pain points, use cases, or satisfaction levels. The project currently has **no visible user engagement channel** active.

## 8. Backlog Watch
| Item | Type | Open Since | Status |
|------|------|------------|--------|
| [#956](https://github.com/nullclaw/nullclaw/pull/956) — Bump alpine 3.23 → 3.24 | PR | 2026-06-15 | Open, unmerged |

**Notable concern:** PR #956 has been open for approximately **two months** (created 2026-06-15, last updated 2026-08-17) without merge or closure. While this is a low-risk Dependabot update, the prolonged openness may indicate a **maintainer bottleneck** or low priority on Docker CI housekeeping. Given the broader silence across all other issue and PR channels, this warrants attention as a potential signal of reduced maintenance velocity.

---

**Project Health Verdict:** 🟡 **Quiet/Maintenance Mode.** NullClaw is currently showing minimal development activity with no feature work, bug fixes, or community engagement. The only visible signal is an aging Dependabot PR. Maintainers should consider triaging the backlog and communicating a development roadmap to re-engage contributors.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-18

## 1. Today's Overview

IronClaw remains in an active release-candidate phase, with `v1.3.0-rc.1` shipped yesterday (2026-08-17). The project posted **29 issues** and **45 PRs** in the last 24 hours, indicating a high-velocity sprint. The dominant theme is a multi-tiered database-write-pressure reduction epic (#7591) targeting ~60% write savings, alongside a notification-inbox refactor and several bug fixes for the rc.1 release. The single most urgent signal is a **boot crash for 1.2.x → 1.3.0-rc.1 upgraders**, now tracked in #7720 with an active fix PR (#7721).

---

## 2. Releases

**ironclaw-v1.3.0-rc.1** (2026-08-17)

- First release candidate for the 1.3.0 track; installable via the provided shell script:
  ```sh
  curl --proto '=https' --tlsv1.2 -LsSf https://github.com/nearai/ironclaw/releases/download/ironclaw-v1.3.0-rc.1/ironclaw-installer.sh | sh
  ```
- **Breaking migration risk:** Upgrades from any `1.2.x` release to `1.3.0-rc.1` crash-loop at boot with `unknown field 'activation_state' in v2 extension installation row` (#7720). A fix PR (#7721) is open to accept the legacy field and restore boot.
- No other formal migration notes were published with the rc.1 release.

---

## 3. Project Progress

**Closed / merged today:**

- **#7594** (closed) — Tier 1 write-pressure win: routed the loop-milestone sink through `CoalescingEventSink`, removing ~30 pool checkouts/turn from the critical path.
- **#7598** (closed) — Tier 2: collapsed capability invocation-state writes to gate/terminal edges, estimated −40 rows/turn (the single biggest write-reduction win in the epic).
- **#7637** (closed) — Type-annotated the design-system component boundary to close implicit-prop gaps.
- **#7647** (closed) — Added a deterministic no-delivery outcome for scheduled automation runs, closing a gap in the delivery layer.
- **#7663** (closed) — Forward-ported 1.2.x fixes (Windows filesystem stability, clean JSON output, runtime `curl` for healthchecks) to main; retained a one-time thread-index repair.

**PRs advanced today:**

- **#7721** — Fix for the 1.3.0-rc.1 boot crash on 1.2.x upgrades (accepting the legacy `activation_state` field).
- **#7717** — Fix for libSQL write-lane starvation cascading through the resource governor (#7714).
- **#7718** — Four semantic Google Docs capabilities (structured inspection, anchored batch edits, populated tables, deterministic verification).
- **#7708** — "Run now" manual-fire path for automations, preserving schedule identity.
- **#7697** — Durable user inbox APIs for notifications (typed, user-scoped, with read-all and per-notification endpoints).
- **#7711** — Final PR of the WASM capability-response-normalization stack: typed tool responses, guest migration, dispatch-error cleanup.
- **#7709** — Bound lease-fence reads in `loop-host` by the lease observed, avoiding repeated journal reads.
- **#7682** — Fix for the Slack unlinked-user connect nudge: now delivered privately with a one-click link.

---

## 4. Community Hot Topics

| Issue / PR | Activity | Focus |
|---|---|---|
| [#7591 Epic: reduce durable DB write pressure ~60%](https://github.com/nearai/ironclaw/issues/7591) | 3 comments, multiple sub-issues opened | Core infrastructure optimization driving the day's top PRs |
| [#7275 Reborn: verify explicit persistent memory recall](https://github.com/nearai/ironclaw/issues/7275) | 4 comments, closed | User-reported cross-conversation memory gap; feedback-driven verification |
| [#7704 Daily failure taxonomy — 2026-08-17](https://github.com/nearai/ironclaw/issues/7704) | New | ClawBench run surfaced a storage write-lane contention defect as the largest fixable ironclaw defect |
| [#3762 AGENTS.md edits not reflected in system prompt](https://github.com/nearai/ironclaw/issues/3762) | Open since May, 2 comments | Long-standing UX gap; still open |

**Analysis:** The write-pressure epic (#7591) has become the structural backbone of the current sprint — every Tier 1–3 sub-issue (#7701, #7603, #7604, #7707, #7598, #7605) feeds directly into it. The persistent memory recall issue (#7275) signals that users are relying on cross-conversation memory as a production feature and expect reliability. The daily taxonomy (#7704) shows the team is institutionalizing benchmark-driven defect tracking.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|---|---|---|---|
| **P0 — Boot crash** | [#7720](https://github.com/nearai/ironclaw/issues/7720) | `1.3.0-rc.1` crash-loops on boot after upgrading from any `1.2.x`; `activation_state` field unknown in v2 extension row | [#7721](https://github.com/nearai/ironclaw/pull/7721) (open) |
| **P1 — Cascading stalls** | [#7714](https://github.com/nearai/ironclaw/issues/7714) | libSQL single shared write connection starves the resource-governor journal under bench load, causing ~40s stall cycles, authority invalidation, and permanent reservation leaks | [#7717](https://github.com/nearai/ironclaw/pull/7717) (open) |
| **P2 — Audit gap** | [#7702](https://github.com/nearai/ironclaw/issues/7702) | Obligation audit records (`AuditBefore`/`AuditAfter`) are never attached in production, violating the documented host-api contract | None yet |
| **P2 — System prompt stale** | [#3762](https://github.com/nearai/ironclaw/issues/3762) | Editing `AGENTS.md` in WebUI does not update the system prompt for current or future conversations | None yet |
| **P2 — Telegram ambiguity** | [#7715](https://github.com/nearai/ironclaw/issues/7715) | Telegram connection flow lacks consent/selection between bot and personal account | None yet |
| **P2 — MCP auth missing** | [#7716](https://github.com/nearai/ironclaw/issues/7716) | "Add MCP server" flow missing bearer-key auth and STDIO/HTTP transport options | None yet |

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue / PR | Likelihood for 1.3.0 |
|---|---|---|
| GitHub Projects v2 field manipulation via the GitHub tool | [#7719](https://github.com/nearai/ironclaw/issues/7719) | Medium — low-complexity extension to existing tool |
| Native structured output finalization | [#7693](https://github.com/nearai/ironclaw/pull/7693) | High — PR is already open, stacked in a visible series |
| Durable backend suggestions (provider-neutral) | [#7694](https://github.com/nearai/ironclaw/pull/7694) | High — PR open, aligned with 1.3.0 scope |
| "Run now" for automations across trigger domain | [#7708](https://github.com/nearai/ironclaw/pull/7708) | High — PR open, production-ready scope |
| ACP serve command with streaming + cancel | [#7513](https://github.com/nearai/ironclaw/pull/7513) | Medium — external contributor; depends on ACP maturity |
| Semantic Google Docs tools | [#7718](https://github.com/nearai/ironclaw/pull/7718) | High — open PR, extends existing Docs integration |
| Deterministic no-delivery outcome for scheduled runs | [#7647](https://github.com/nearai/ironclaw/pull/7647) | **Already merged** (closed) |

---

## 7. User Feedback Summary

- **Cross-conversation memory reliability** (#7275): Users explicitly established information is not recalled across conversations. This is a trust-critical gap for a personal AI assistant.
- **AGENTS.md edits not live** (#3762): Users editing identity files in the WebUI expect changes to take effect immediately, but the system prompt is not refreshed. This has been open since May and remains unresolved — a sustained pain point.
- **Slack connect notice is public** (#7681 / fixed in #7682): Unlinked users @-mentioned the bot in shared channels and received a reply visible to everyone. The fix (#7682) delivers a private nudge with a one-click link, directly addressing this.
- **Telegram connection ambiguity** (#7715): Users cannot distinguish whether they are connecting a bot or their personal account — a confusing onboarding experience.
- **MCP server auth gaps** (#7716): The "Add MCP server" flow lacks bearer-key authentication and transport-option selection, blocking enterprise and authenticated MCP deployments.

---

## 8. Backlog Watch

| Issue | Age | Risk |
|---|---|---|
| [#3762 AGENTS.md edits not reflected](https://github.com/nearai/ironclaw/issues/3762) | Open since 2026-05-18 (~3 months) | High — core UX contract; marked `suggested_P1`, `v1.4.0` |
| [#7702 Obligation audit records never attached](https://github.com/nearai/ironclaw/issues/7702) | Open since 2026-08-17 | Medium — contract violation discovered during epic audit, no fix yet |
| [#7707 Track side-effect-outstanding explicitly](https://github.com/nearai/ironclaw/issues/7707) | Open since 2026-08-17 | Medium — split out of #7603 after an integration test proved the original approach unsafe; this is where the real ~14 rows/turn saving lives |
| [#7591 Epic: reduce durable DB write pressure](https://github.com/nearai/ironclaw/issues/7591) | Open since 2026-08-13 | High — the epic's remaining Tiers 2–3 sub-issues are still open; the full ~60% reduction has not yet landed |

---

**Overall health:** High velocity, clear prioritization around write-pressure reduction and notification infrastructure. The 1.3.0-rc.1 boot crash is a concerning regression for upgraders but has an active fix. The 3-month-old AGENTS.md issue (#3762) deserves elevated attention.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-18

---

## 1. Today's Overview

LobsterAI is showing strong daily development velocity with **21 PRs updated** in the last 24 hours and **7 open issues** currently tracked. The project is in a healthy release pipeline — 18 PRs were merged or closed today, signaling an active contribution window. Activity spans provider integrations (DeepSeek Harness, OrcaRouter), UX polish (context menus, i18n, modal ergonomics), and infrastructure upgrades (OpenClaw v2026.4.12). No new releases were published today. The project's open-issue backlog carries several stale but unresolved bugs from April, indicating a gap between community reports and maintainer triage.

---

## 2. Releases

**No new releases today.** The latest release-related activity involves an OpenClaw runtime upgrade (PR #1663) to v2026.4.12, which was merged without a corresponding application version bump.

---

## 3. Project Progress

### Merged / Closed PRs (18)

| PR | Area | Summary |
|----|------|---------|
| [#2506](https://github.com/netease-youdao/LobsterAI/pull/2506) | docs | Added DeepSeek Harness (DSH) runtime setup documentation |
| [#2505](https://github.com/netease-youdao/LobsterAI/pull/2505) | main | Added DSH process launcher |
| [#2502](https://github.com/netease-youdao/LobsterAI/pull/2502) | renderer/build | DSH engine integration |
| [#2504](https://github.com/netease-youdao/LobsterAI/pull/2504) | openclaw | **Open** — OrcaRouter provider integration (OpenAI/Anthropic-compatible gateway) |
| [#2503](https://github.com/netease-youdao/LobsterAI/pull/2503) | electron | Added native text-edit context menu (Cut/Copy/Paste) for prompt inputs |
| [#2501](https://github.com/netease-youdao/LobsterAI/pull/2501) | renderer | Fixed skill upgrade progress overlay rendering |
| [#1663](https://github.com/netease-youdao/LobsterAI/pull/1663) | openclaw | Upgraded OpenClaw runtime v2026.3.2 → v2026.4.12; fixed plugin-sdk compatibility |
| [#1668](https://github.com/netease-youdao/LobsterAI/pull/1668) | agent | Added per-agent independent working directory configuration (SQLite migration) |
| [#1675](https://github.com/netease-youdao/LobsterAI/pull/1675) | cowork | Grouped session list by time period (today/yesterday/7d/30d/monthly) |
| [#1661](https://github.com/netease-youdao/LobsterAI/pull/1661) | main | Fixed log export to redact API keys, tokens, and sensitive request/response bodies |
| [#1667](https://github.com/netease-youdao/LobsterAI/pull/1667) | settings | Migrated Qwen provider links from DashScope to Alibaba BaIan console |
| [#1669](https://github.com/netease-youdao/LobsterAI/pull/1669) | renderer | Fixed model provider "Test Connection" disabled logic and custom provider name display |
| [#1636](https://github.com/netease-youdao/LobsterAI/pull/1636) | cowork | Added floating "scroll to bottom" button in chat windows |
| [#1637](https://github.com/netease-youdao/LobsterAI/pull/1637) | cowork | Added "Regenerate" button on AI responses |
| [#1639](https://github.com/netease-youdao/LobsterAI/pull/1639) | i18n | Fixed hardcoded English tooltips across multiple UI components |
| [#1640](https://github.com/netease-youdao/LobsterAI/pull/1640) | tool-result | Added one-click copy button for tool execution results (Bash, Diff, etc.) |
| [#1641](https://github.com/netease-youdao/LobsterAI/pull/1641) | modal | Unified Esc-key-to-close support across all modal dialogs |
| [#1642](https://github.com/netease-youdao/LobsterAI/pull/1642) | main | Added Windows right-click context menu for LobsterAI executable |

### Open PRs (3)

- [#2504](https://github.com/netease-youdao/LobsterAI/pull/2504) — OrcaRouter provider integration
- [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Electron dependency bump (40.2.1 → 43.4.0)
- [#1660](https://github.com/netease-youdao/LobsterAI/pull/1660) — Non-main agent personalized welcome area

---

## 4. Community Hot Topics

| Issue | Activity | Summary |
|-------|----------|---------|
| [#2500](https://github.com/netease-youdao/LobsterAI/issues/2500) | Created today | **VOKO cross-platform agent communication** — The author of VOKO proposes interoperability between LobsterAI, OpenClaw, and AstrBot agents via a unified A2A protocol. Signals strong community interest in agent-to-agent standardization. |
| [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) | 2 comments, stale | **groupPolicy being overwritten to allowlist** — Users report the policy setting resets unexpectedly, indicating a potential config persistence bug. |
| [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) | 1 comment, stale | **MD-based workflow feature request** — User wants Markdown-driven workflow orchestration so the main agent can discover and coordinate other agents. Directly addresses the known limitation that agents cannot perceive each other. |
| [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) | 1 comment, stale | **Non-SSE MCP tools unusable** — Only SSE-based MCP connections work; HTTP/streamable MCP is broken. |

**Analysis:** The most significant signal is #2500 (VOKO), which reflects a growing community demand for **agent interoperability** — a theme that aligns with the open PR #2504 (OrcaRouter) and the existing multi-provider strategy. Issue #1644 highlights a structural gap in agent discovery that the per-agent working directory feature (PR #1668) partially addresses but doesn't fully solve.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **High** | [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) | Non-SSE MCP engines cannot be found or used — limits tool integrations significantly | No |
| **High** | [#1635](https://github.com/netease-youdao/LobsterAI/issues/1635) | Ollama local models (Qwen3, Gemma4) fail in LobsterAI despite working in CherryStudio | No |
| **Medium** | [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) | groupPolicy config is periodically overwritten to allowlist — possible race condition in config sync | No |
| **Medium** | [#1671](https://github.com/netease-youdao/LobsterAI/issues/1671) | MD-to-Word conversion aborts mid-process with `full` SSE finish reason — data loss risk | No |
| **Low** | [#1643](https://github.com/netease-youdao/LobsterAI/issues/1643) | Scheduled task save shows "unsaved changes" warning despite successful save — UI bug only | No |

**Note:** The log sanitization fix in [#1661](https://github.com/netease-youdao/LobsterAI/pull/1661) mitigates a security-adjacent concern (sensitive data in exported logs) but is classified as a bug fix, not a crash.

---

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood |
|---------|--------|------------|
| **OrcaRouter provider support** | [#2504](https://github.com/netease-youdao/LobsterAI/pull/2504) (open PR) | High — already in review; mirrors existing OpenRouter integration pattern |
| **Per-agent working directories** | [#1668](https://github.com/netease-youdao/LobsterAI/pull/1668) (merged) | ✅ Merged — will ship in next release |
| **DeepSeek Harness (DSH) runtime** | [#2502](https://github.com/netease-youdao/LobsterAI/pull/2502), [#2505](https://github.com/netease-youdao/LobsterAI/pull/2505), [#2506](https://github.com/netease-youdao/LobsterAI/pull/2506) (all merged) | ✅ Merged — new runtime option for DeepSeek models |
| **MD-based agent workflow orchestration** | [#1644](https://github.com/netease-youdao/LobsterAI/issues/1644) | Medium — structurally complex; may require OpenClaw runtime changes |
| **Cross-platform A2A communication (VOKO)** | [#2500](https://github.com/netease-youdao/LobsterAI/issues/2500) | Low-Medium — external project; integration would require API/design decisions |
| **Session list time-grouping** | [#1675](https://github.com/netease-youdao/LobsterAI/pull/1675) (merged) | ✅ Merged — shipping soon |
| **Non-main agent personalized welcome** | [#1660](https://github.com/netease-youdao/LobsterAI/pull/1660) (open) | High — small, self-contained change; likely to merge |

**Prediction:** The next release will likely feature the DSH runtime, OrcaRouter provider, per-agent working directories, and session time-grouping. The VOKO A2A proposal and MD workflow orchestration are longer-horizon roadmap items.

---

## 7. User Feedback Summary

**Pain points expressed:**
- **Config instability** — groupPolicy auto-reset (#1653) and false "unsaved changes" warnings (#1643) erode user trust in settings persistence.
- **Local model compatibility gaps** — Ollama works in CherryStudio but not LobsterAI (#1635), suggesting a model adapter or MCP configuration issue specific to the runtime.
- **MCP engine limitation** — only SSE MCP is supported; HTTP/streamable MCP is non-functional (#1662), limiting tool ecosystem breadth.
- **Agent isolation** — main agent cannot discover or coordinate with sibling agents (#1644), a structural UX limitation for power users running multi-agent workflows.
- **Mid-task failures** — MD-to-Word conversion aborts silently (#1671), causing user data loss frustration.

**Positive signals:**
- Users appreciate UX polish improvements (regenerate button, scroll-to-bottom, copy buttons, i18n fixes).
- The per-agent working directory (#1668) and session time-grouping (#1675) directly address long-standing organizational complaints.
- Log sanitization (#1661) shows responsiveness to security-conscious users.

---

## 8. Backlog Watch

| Issue/PR | Age | Risk | Action Needed |
|----------|-----|------|---------------|
| [#1635](https://github.com/netease-youdao/LobsterAI/issues/1635) — Ollama models not working | ~4 months | High — blocks local-first users | Reproduce and triage; likely an adapter or MCP config bug |
| [#1662](https://github.com/netease-youdao/LobsterAI/issues/1662) — Non-SSE MCP broken | ~4 months | High — limits integrations | Investigate MCP transport layer; check for regressions after OpenClaw upgrade |
| [#1653](https://github.com/netease-youdao/LobsterAI/issues/1653) — groupPolicy overwrite | ~4 months | Medium — config integrity | Audit config sync logic for race conditions |
| [#1671](https://github.com/netease-youdao/LobsterAI/issues/1671) — MD-to-Word SSE abort | ~4 months | Medium — data loss | Capture full error context; check OpenClaw runtime behavior |
| [#1643](https://github.com/netease-youdao/LobsterAI/issues/1643) — False unsaved-changes warning | ~4 months | Low — UI glitch | Quick fix in save handler |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) — Electron 40→43 bump | ~4 months | Low — depends on upstream | Verify compatibility with current Electron plugins |
| [#1660](https://github.com/netease-youdao/LobsterAI/pull/1660) — Agent welcome area | ~4 months | Low — ready to merge | Awaiting maintainer review |
| [#2504](https://github.com/netease-youdao/LobsterAI/pull/2504) — OrcaRouter | ~1 day | Low — new PR | Awaiting review |

**Critical observation:** All 7 open issues are marked **[stale]** and have gone unanswered for approximately 4 months (created mid-April). This suggests a maintainer bandwidth bottleneck. The VOKO issue (#2500), created today, is the first fresh community signal and could indicate growing interest in cross-project collaboration.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-18

---

## 1. Today's Overview

Moltis remains in active development with 12 items touched in the last 24 hours (3 issues, 9 PRs), signaling sustained contributor momentum. The project is currently in a **bug-fix and hardening phase**: two open PRs (#1208, #1209) address heartbeat logic gaps, while several merged PRs land dependency bumps, a new MiniMax Code ACP agent, and improved browser DOM handling. No new release was published today, but the volume of merged PRs suggests a release candidate may be forming. One notable open bug (#1095) around Podman integration has lingered since June, highlighting an area needing maintainer attention.

---

## 2. Releases

**No new releases published today.**

---

## 3. Project Progress

### Merged / Closed PRs Today

- **#1204** — feat: add MiniMax Code ACP agent `[closed]`
  New external-agent kind `acp-minimax-code` backed by `mcode acp`. Includes default executable detection, registry registration, and config-validation/UI fixture alignment.

- **#1125** — Support model and effort selection for external agents `[closed]`
  First-class `models` / `efforts` config for external-agent providers, grouped under `external-agent/<kind>` in `/model`. Model/effort metadata is now persisted.

- **#1130** — feat: make webui rpc timeout configurable `[closed]`
  Resolves #1127. Adds a tunable RPC timeout for the web UI, addressing a long-requested configurability gap.

- **#1103** — fix(browser): pierce shadow DOM lookups efficiently `[closed]`
  Updates and completes the shadow-DOM piercing logic for browser snapshot and ref-based lookups, picking up review fixes from the original PR #1100.

- **#1207** — chore(deps): bump cargo group (wasmtime-wasi, cmov, quinn-proto, serde_with) `[closed]`
  Routine dependency updates keeping the stack current.

- **#1087** — chore(deps): bump tar from 0.4.45 to 0.4.46 `[closed]`
  Security/maintenance bump for the tar crate.

- **#1202** — Format CI gate is red on main `[closed]`
  Closed by addressing the two files exceeding the 1500-line limit (`store.rs` at 1799 lines, `admin.rs` at 1531 lines), likely via the fix PRs now merged.

### Open PRs Awaiting Review

- **#1209** — fix(gateway): treat heartbeat.update params as a patch, not a whole config `[open]`
  Closes #1187. Fixes a bug where `heartbeat.update` silently overwrites omitted keys with defaults instead of patching.

- **#1208** — fix(cron): honor heartbeat active hours when the scheduler fires `[open]`
  Closes #1205. The `is_within_active_hours` check was written and tested but never called by the scheduler — this PR wires it in.

- **#1206** — Add managed Files library and Settings browser `[open]`
  Large feature: persistent data-directory-backed Files library with authenticated CRUD APIs, a Finder-style Settings browser, and read-only-by-default Docker/Podman/Apple Container mounts.

---

## 4. Community Hot Topics

| Item | Activity | Link |
|------|----------|------|
| [#1095] Podman is not working via moltis | Open · 2 comments · since 2026-06-03 | [Issue #1095](https://github.com/moltis-org/moltis/issues/1095) |
| [#1127] Allow configuring RPC timeout | Closed 2026-08-17 · resolved by #1130 | [Issue #1127](https://github.com/moltis-org/moltis/issues/1127) |
| [#1202] Format CI gate red on main | Closed 2026-08-17 · resolved by merged fix | [Issue #1202](https://github.com/moltis-org/moltis/issues/1202) |

**Analysis:** Issue #1095 stands out as the most-discussed open item (2 comments, 2 months open). Users running Moltis in containerized environments are hitting Podman-specific path or permission issues, suggesting a growing need for first-class container runtime support beyond Docker. The RPC timeout request (#1127) and the CI gate issue (#1202) were both resolved quickly, reflecting healthy maintainer responsiveness on non-blocking items.

---

## 5. Bugs & Stability

| Severity | Issue | Status | Fix PR |
|----------|-------|--------|--------|
| **Medium** | #1202 — Format CI gate red (files exceed 1500-line limit) | ✅ Closed 2026-08-17 | N/A (resolved in-tree) |
| **Medium** | #1187 (referenced in #1209) — heartbeat.update overwrites whole config | 🔄 Open (PR #1209) | #1209 [open] |
| **Medium** | #1205 (referenced in #1208) — heartbeat active hours ignored by scheduler | 🔄 Open (PR #1208) | #1208 [open] |
| **Low** | #1095 — Podman not working via Moltis | 🟡 Open since 2026-06-03 | None yet |

No crashes or regressions reported today. The two heartbeat-related bugs are logic gaps (not data loss) and are actively being patched. The Podman issue remains unresolved with no fix PR in progress.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Likelihood for Next Release |
|--------|--------|----------------------------|
| **Managed Files library + Settings browser** | #1206 [open] | **High** — large, self-contained feature already in review |
| **MiniMax Code ACP agent** | #1204 [closed, merged] | ✅ Already landed |
| **Model/effort selection for external agents** | #1125 [closed, merged] | ✅ Already landed |
| **Configurable webui RPC timeout** | #1127 / #1130 [closed, merged] | ✅ Already landed |
| **Podman support parity with Docker** | #1095 [open] | **Medium** — likely in a future release if the community push continues |

The roadmap is clearly heading toward **broader agent provider support** (MiniMax, external-agent model selection) and **improved filesystem/integration tooling** (managed Files library). Podman support is the most pressing unmet request.

---

## 7. User Feedback Summary

- **Container runtime gaps:** Users running Moltis in Podman encounter functional failures (#1095), suggesting the project's container support is currently Docker-centric. This is a real pain point for users who prefer Podman or rootless containers.
- **Heartbeat configurability:** The active-hours and patch-semantics bugs (#1205, #1187) indicate users want reliable, fine-grained scheduling control — they expected these features to work as documented, and the gaps caused silent misbehavior.
- **RPC timeout needs:** The resolution of #1127 via #1130 confirms users hit timeouts in production and needed a way to tune them rather than hit hard limits.
- **Overall sentiment:** Positive. Merged PRs land meaningful features (MiniMax agent, model selection, Files library), and bug-fix PRs are moving quickly. The primary friction point is the unresolved Podman issue.

---

## 8. Backlog Watch

| Item | Open Since | Concern |
|------|-----------|---------|
| [#1095] Podman is not working via moltis | 2026-06-03 (~2 months) | Container runtime support gap; no fix PR yet. Needs maintainer triage. |
| [#1127] Allow configuring RPC timeout (resolved, but pattern repeats) | 2026-06-17 | Now closed via #1130 — monitoring for similar timeout issues in other subsystems. |

**Recommendation:** Issue #1095 should be prioritized. With two open PRs (#1206, #1208, #1209) in review and no new release, maintaining contributor momentum while closing the longest-standing bug would strengthen the next release's credibility, especially for container-native deployments.

---

*Digest generated from GitHub data as of 2026-08-18. All links point to moltis-org/moltis on GitHub.*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-18

---

## 1. Today's Overview

CoPaw (agentscope-ai/CoPaw) shows strong development velocity with **12 issues** and **33 PRs** updated in the last 24 hours. Activity is heavily skewed toward PRs (20 merged/closed vs. 13 open), indicating an active review-and-merge cadence. No new releases were published today. The project is in a mature pre-release stabilization phase for v2.1.x, with sustained contributor engagement and a healthy open-to-closed ratio on issues (7 open / 5 closed in the window).

---

## 2. Releases

**None.** No new version tags or release artifacts were published in the 24-hour window.

---

## 3. Project Progress

**Closed/Merged PRs (selected highlights):**

| PR | Type | Summary |
|----|------|---------|
| [#7083](https://github.com/agentscope-ai/CoPaw/pull/7083) | feat | Console background-task list compacted with scroll hint |
| [#7017](https://github.com/agentscope-ai/CoPaw/pull/7017) | fix | Newly installed PawApps open without page reload; updates reload automatically |
| [#5151](https://github.com/agentscope-ai/CoPaw/pull/5151) | fix | GitPanel tab styles restored (CSS prefix fix: `ant-` → `qwenpaw`) |
| [#7036](https://github.com/agentscope-ai/CoPaw/pull/7036) | feat | Unified media download controls across chat attachments |
| [#6981](https://github.com/agentscope-ai/CoPaw/pull/6981) | feat | Removed `/approve` & `/deny` hints from all 7 locale i18n placeholders |
| [#6975](https://github.com/agentscope-ai/CoPaw/pull/6975) | fix | Context-usage ring now updates correctly after `/compact` |
| [#6940](https://github.com/agentscope-ai/CoPaw/pull/6940) | feat | Native DataPaw app runtime with durable analysis workspace |
| [#6968](https://github.com/agentscope-ai/CoPaw/pull/6968) | fix | Image base64 no longer inflated as text tokens in context ring |

**Notable feature PRs still open:**

- [#7089](https://github.com/agentscope-ai/CoPaw/pull/7089) — Standalone version-driven release pipeline for DataPaw plugin
- [#7087](https://github.com/agentscope-ai/CoPaw/pull/7087) — Client-side localization of remote media URLs before model requests
- [#7078](https://github.com/agentscope-ai/CoPaw/pull/7078) — System prompt file picker in Console workspace
- [#6719](https://github.com/agentscope-ai/CoPaw/pull/6719) — Persistent workspace artifact cards in chat turns
- [#6976](https://github.com/agentscope-ai/CoPaw/pull/6976) — Session-scoped multi-project directories
- [#6302](https://github.com/agentscope-ai/CoPaw/pull/6302) — Unified provider discovery, model metadata, and routing

---

## 4. Community Hot Topics

**Most-commented issues (active discussions):**

1. **[Issue #6405](https://github.com/agentscope-ai/CoPaw/issues/6405)** — 7 comments · MCP tool "not found" after 2.0 upgrade (`[mcp-key]__[tool_name]` naming)
   - *Underlying need:* Smooth migration path from 1.x → 2.x for MCP-integrated workflows. Naming convention change breaks existing tool references.

2. **[Issue #7011](https://github.com/agentscope-ai/CoPaw/issues/7011)** — 6 comments · Console stop request cancels active Feishu session across UI sessions
   - *Underlying need:* Session isolation between concurrent UI clients; stop-action scope leakage is a multi-tenant stability concern.

3. **[Issue #6925](https://github.com/agentscope-ai/CoPaw/issues/6925)** — 3 comments · Multi-agent collaboration should share a single session window
   - *Underlying need:* UX simplification — users find it cumbersome to switch between agent tabs to view collaborative conversations.

4. **[Issue #7085](https://github.com/agentscope-ai/CoPaw/issues/7085)** — 3 comments · Per-channel (channel-Scoped) model configuration
   - *Underlying need:* Production users want independent model routing per channel (e.g., GPT-4o for DingTalk, Qwen-max for WeChat, local Llama for Console), without cross-channel side effects.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix Status |
|----------|-------|---------|------------|
| 🔴 High | [#7063](https://github.com/agentscope-ai/CoPaw/issues/7063) | Agent tool-call crash: `async for` on coroutine instead of async generator → `TypeError` | ✅ Closed |
| 🔴 High | [#7088](https://github.com/agentscope-ai/CoPaw/issues/7088) | OneBot QQ image URLs with expired `rkey` poison session history | ✅ Closed |
| 🟡 Medium | [#7077](https://github.com/agentscope-ai/CoPaw/issues/7077) | Plugin runtime hooks lost after workspace hot-reload | ✅ Closed |
| 🟡 Medium | [#7051](https://github.com/agentscope-ai/CoPaw/issues/7051) | Image attachments lost on Console session reload (broken thumbnail) | ✅ Closed |
| 🟡 Medium | [#7084](https://github.com/agentscope-ai/CoPaw/issues/7084) | Single-history conversation cannot be opened in new chat | 🔵 Open |
| 🟡 Medium | [#7082](https://github.com/agentscope-ai/CoPaw/issues/7082) | `MODEL_EXECUTION_ERROR`: `_StructuredOutputDynamicClass` not fully defined (Pydantic) | 🔵 Open |
| 🟢 Low | [#7011](https://github.com/agentscope-ai/CoPaw/issues/7011) | Cross-session Feishu cancellation from Console stop request | 🔵 Open |

**Pattern:** The dominant stability theme is **session persistence and reload correctness** — image handling, plugin hooks, and history navigation all surface issues when state is reloaded or sessions are recreated.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Signal Strength |
|---------|----------|-----------------|
| Per-channel model configuration | [#7085](https://github.com/agentscope-ai/CoPaw/issues/7085) | 🔥 High — explicit production use case, clear spec |
| PowerContext long-term memory backend | [#7079](https://github.com/agentscope-ai/CoPaw/issues/7079) / [#7080](https://github.com/agentscope-ai/CoPaw/pull/7080) | 🔥 High — PR already submitted, extends `BaseMemoryManager` |
| Skill pool search/filter | [#7090](https://github.com/agentscope-ai/CoPaw/issues/7090) | 🟡 Medium — UX improvement, single-user request |
| Multi-agent single-session collaboration | [#6925](https://github.com/agentscope-ai/CoPaw/issues/6925) | 🟡 Medium — quality-of-life request |
| AnySearch web search integration | [#7081](https://github.com/agentscope-ai/CoPaw/pull/7081) / [#6817](https://github.com/agentscope-ai/CoPaw/pull/6817) | 🔥 High — replaces Tavily, PR submitted with MCP client |
| Volcengine Agent Plan & Xiaomi MiMo V2.5 | [#6515](https://github.com/agentscope-ai/CoPaw/pull/6515) | 🟡 Medium — provider expansion, open since July 28 |
| Workspace-scoped multi-project directories | [#6976](https://github.com/agentscope-ai/CoPaw/pull/6976) | 🟡 Medium — developer-experience feature |
| DataPaw independent release pipeline | [#7089](https://github.com/agentscope-ai/CoPaw/pull/7089) | 🟡 Medium — operational infra, not user-facing |

**Prediction:** Per-channel model config and PowerContext memory are strong candidates for the next minor release. AnySearch integration and multi-project directories are likely v2.2 candidates given PR maturity.

---

## 7. User Feedback Summary

**Pain points:**

- **Image/media handling is fragile** across reloads and remote URLs — users report broken thumbnails, expired signed URLs poisoning sessions, and inflated token counts (#7051, #7088, #7082, #6968).
- **Session management needs isolation** — cross-session side effects (stop actions, history navigation with single entry) erode trust in concurrent multi-client usage (#7011, #7084).
- **MCP migration friction** — the `[mcp-key]__[tool_name]` naming convention introduced in 2.0 is unclear and causes "tool not found" errors during upgrade (#6405).
- **Configuration rigidity** — global model settings affect all channels; users want per-channel control (#7085).
- **Skill discovery at scale** — hundreds of skills with only arrow-key navigation is unusable (#7090).

**Satisfaction signals:** Positive reception of compact background-task UI (#7083), PawApp hot-install UX (#7017), and media download controls (#7036). Plugin and memory extensibility is actively requested.

---

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#6515](https://github.com/agentscope-ai/CoPaw/pull/6515) — Volcengine Agent Plan & Xiaomi MiMo V2.5 providers | ~21 days | Open PR for widely-used providers; blocks users on those platforms |
| [#6302](https://github.com/agentscope-ai/CoPaw/pull/6302) — Unified provider discovery & routing | ~28 days | Large architectural PR; if merged, reshapes model configuration UX significantly |
| [#7087](https://github.com/agentscope-ai/CoPaw/pull/7087) — Client-side media URL localization | ~1 day | Fix for hotlink-protected and backend-fetch failures; directly addresses #7088 |
| [#6976](https://github.com/agentscope-ai/CoPaw/pull/6976) — Session-scoped multi-project dirs | ~5 days | Developer-focused feature with broad implications for workspace tooling |

**Recommendation:** Maintainers should prioritize review of #6515 and #6302 given their age and impact scope, and triage the remaining open bugs (#7082, #7084, #7011) before the next release candidate.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-18

## 1. Today's Overview

ZeroClaw is in an active development phase with **50 issues and 50 PRs updated in the last 24 hours**, indicating high maintainer and community engagement. The project is pushing toward **v0.9.0**, with a concentrated focus on security hardening, authentication architecture, and reliability fixes. No new releases were published today, but several critical bug fixes were merged, particularly around SSRF protection, provider reliability, and action-budget atomicity. The project's RFC governance process remains the primary coordination mechanism, with multiple ratified and in-progress design proposals shaping the near-term roadmap.

## 2. Releases

**No new releases today.** The project is currently in the 0.8.x-beta cycle (latest referenced: 0.8.4) with v0.9.0 in progress.

## 3. Project Progress

### Merged/Closed PRs (significant)
- **#10070** — `feat(tools): gate file_download against SSRF with private-host opt-in` — Rebuilt focused slice of SSRF hardening for the `file_download` tool with operator-facing contract and tests.
- **#10021** — `fix(runtime): apply target thinking to independent delegates` — Applies resolved target runtime profile thinking policy to agentic independent delegates.
- **#9973** — `fix(providers): keep Gemini API keys out of URLs` — Removed Gemini API keys from request URLs; now uses `x-goog-api-key` header. Prevents credential exposure via URLs and diagnostics.
- **#10038** — `fix(gateway/cron): reject invalid session_target instead of isolating` — Fixes a bug where invalid `session_target` values (typos, empty strings) were silently accepted with HTTP 200.
- **#10000** — `fix(channels): bound QQ and Mattermost downloads` — Enforces bounded HTTP response readers for QQ (10 MiB) and Mattermost (25 MiB) inbound attachments.
- **#9996** — `fix(security): make action budget accounting atomic` — Resolves parallel-dispatch race in `RateLimitedTool` where the budget check and recording were non-atomic.
- **#9993** — `fix(email): stop implicit attachment file reads` — Prevents empty-payload MIME attachments from triggering local file reads.
- **#9612** — `fix(channels): tie WhatsApp Cloud approval token to a guard` — Fixes an orphaned token issue in `request_approval` that could leak bearer credentials.
- **#9765** — `fix(sop): load SOP definitions from the shared workspace, not data_dir` — Corrects SOP definition loading to use the shared workspace instead of `data_dir`.
- **#9808** — `chore(deps): bump rust-all group with 46 updates` — Dependabot-driven Rust dependency updates including clap, tokio, and others.

## 4. Community Hot Topics

### Top Issues by Comment Count
1. **[RFC] Work Lanes, Board Automation, and Label Cleanup** — [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) (23 comments) — Governance RFC for streamlining issue triage; ratified and rolling out.
2. **[RFC] ZeroClaw Chat Completions profile** — [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) (23 comments) — Seeks to expose agent capabilities via the OpenAI Chat Completions protocol for broader client compatibility (Open WebUI, Continue.dev, LangChain, etc.).
3. **[RFC] Goal mode v1 — bounded foreground Matrix work** — [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) (22 comments, 1 👍) — Durable bounded objective pursuit across multiple agent turns; addresses earlier design coupling issues.
4. **[RFC] Per-execution confirmation tier for high-risk shell commands** — [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) (20 comments) — Claude Code-style allow/ask/deny command pattern policy for shell tools (p1 priority).
5. **[RFC] Runtime-owned conversation sessions and transport surface adapters** — [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) (19 comments) — Ownership boundary for sessions and inbound action dispatch.
6. **[RFC] Unified attachment architecture** — [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) (18 comments) — Cross-channel attachment handling standardization.
7. **[RFC] Pluggable inbound authentication and canonical principals** — [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) (16 comments) — OIDC and pluggable provider auth for v0.9.0 identity milestone (p1 priority).
8. **[RFC] Security posture, credential boundaries, and universal ingress policy** — [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) (15 comments) — Comprehensive security audit and policy framework.

**Underlying needs:** The community is heavily invested in **interoperability** (Chat Completions profile), **security hardening** (multiple security RFCs), **governance efficiency** (work lanes, RFC process streamlining #9496), and **developer ergonomics** (goal mode, shell confirmation tiers). The volume of security-related RFCs (#7141, #7142, #6971, #9598) signals that v0.9.0 is squarely focused on trust boundaries.

## 5. Bugs & Stability

| Severity | Bug | Status | Fix PR |
|----------|-----|--------|--------|
| **P1** | Gemini API keys exposed in URLs | Fixed | [#9973](https://github.com/zeroclaw-labs/zeroclaw/pull/9973) ✅ Merged |
| **P1** | QQ & Mattermost downloads unbounded (SSRF-adjacent) | Fixed | [#10000](https://github.com/zeroclaw-labs/zeroclaw/pull/10000) ✅ Merged |
| **P1** | SOP definitions loaded from wrong directory | Fixed | [#9765](https://github.com/zeroclaw-labs/zeroclaw/pull/9765) ✅ Merged |
| **P2** | Action budget non-atomic under parallel dispatch (double charge) | Fixed | [#9996](https://github.com/zeroclaw-labs/zeroclaw/pull/9996) ✅ Merged |
| **P2** | Error logs report requested model, not pinned fallback | Open (#10023) | — |
| **P2** | Invalid cron `session_target` silently accepted | Fixed | [#10038](https://github.com/zeroclaw-labs/zeroclaw/pull/10038) ✅ Merged |
| **P2** | WhatsApp Cloud approval token can be orphaned on exit | Fixed | [#9612](https://github.com/zeroclaw-labs/zeroclaw/pull/9612) ✅ Merged |
| **P2** | Email MIME empty payload triggers implicit file reads | Fixed | [#9993](https://github.com/zeroclaw-labs/zeroclaw/pull/9993) ✅ Merged |
| **P2** | Coding-agent tools charge action budget twice | Fixed (#9594) | Related to #9996 |

**Outstanding:** #10023 (provider failure logging) remains open. The SSRF hardening for `file_download` via `[file_download].url` is still being iterated — #8713 (large, open) and #10070 (fresh slice, open) are both active.

## 6. Feature Requests & Roadmap Signals

- **Chat Completions API profile** (#8603) — Strong community demand for OpenAI-compatible protocol support; if ratified, could significantly expand the client ecosystem. Likely targeted for post-v0.9.0 or a late v0.9.0 slice.
- **Goal mode v1** (#8303) — Bounded multi-turn agent objectives; a long-requested capability for more reliable task completion. In active design; may ship in v0.9.0 or v0.10.0.
- **Portable agent bundles** — PR #9986 (`zeroclaw agents export <alias>`) enables moving agents between installs via manifest + config closure. Near-term feature.
- **Per-model capability & context-window config** (#7100) — Addresses misreported vision support and context budget issues; operator-facing reliability improvement.
- **Streamlined RFC process** (#9496) — Reducing discussion latency and replacing unanimity requirements; governance improvement likely to land soon.
- **SOP capability permission contract** (#9598) — Authoritative `required_permissions` for SOPs without a second grant system; targets v0.9.0.
- **Staged opt-in telemetry** (#9621) — Operator-reviewed telemetry for usage-based decisions; sensitive topic but clearly wanted by maintainers.
- **Option-Backspace in ZeroCode** (#10059) — macOS convention parity; small UX polish, low risk.

## 7. User Feedback Summary

- **Pain point — Security transparency:** Multiple reports and RFCs address credential exposure (Gemini keys in URLs #9973), SSRF via config URLs #8713/#10070, and unbounded channel downloads #10000. Users are clearly sensitive to trust-boundary violations.
- **Pain point — Provider reliability:** #10023 highlights frustration with misleading error logs when fallback providers serve different models. #10003 (open) continues work on exact Reliable provider attempt accounting.
- **Pain point — Shell command risk:** #7155 reflects community demand for per-execution confirmation tiers on high-risk commands, echoing Claude Code's proven policy model.
- **Pain point — Configuration drift:** #7897 (hot-reload without daemon restart) and #9397 (WhatsApp `allowed_groups` empty-list semantics) show users want configuration changes to take effect immediately and predictably.
- **Satisfaction signal:** The project has merged **9 significant bug fixes** in a single day, many on p1 security issues, demonstrating responsive maintenance. The active RFC ratification process (#6808, #9496) suggests community governance is functioning well.

## 8. Backlog Watch

| Issue | Days Open | Concern |
|-------|-----------|---------|
| [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713) — SSRF gate for `file_download` (full slice) | ~45 days | XL-size PR, superseded by #10070 for the focused slice, but the broader fix is still open |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — Runtime-owned conversation sessions | ~52 days | Needs maintainer review; `needs-maintainer-review` label active |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) — Unified attachment architecture | ~52 days | `needs-author-action` — draft may need revision |
| [#10003](https://github.com/zeroclaw-labs/zeroclaw/pull/10003) — Reliable provider attempt accounting | ~3 days | Open, needs maintainer review; large (XL) |
| [#10023](https://github.com/zeroclaw-labs/zeroclaw/issues/10023) — Fallback model logging bug | 2 days | Open, in-progress |
| [#9598](https://github.com/zeroclaw-labs/zeroclaw/issues/9598) — SOP permission contract | ~18 days | `needs-maintainer-review` |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Shell confirmation tiers | ~76 days | Accepted but still open; p1 priority |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) — Pluggable auth | ~76 days | In-progress; p1, core to v0.9.0 |

**Key observation:** The project's maintainers are heavily focused on v0.9.0 security and auth milestones. Several accepted RFCs with `needs-maintainer-review` labels (#9487, #9488, #9598) are waiting on maintainer triage. The SSRF #8713 saga shows the team is willing to split large PRs into focused slices (#10070) for faster review.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*