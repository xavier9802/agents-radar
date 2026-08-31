# OpenClaw Ecosystem Digest 2026-08-31

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-31 04:59 UTC

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



# OpenClaw Project Digest — 2026‑08‑31

## 1. Today's Overview
OpenClaw exhibits **high development velocity** with 500 issues and 500 PRs updated in the last 24 h (266 open/active issues, 309 open PRs). The latest release **v2026.8.1** introduces conversation‑search and cross‑device session capabilities. Community engagement is strong, driven by beta‑feedback loops and a steady stream of bug reports. Project health is active but shows **stability pressure** from critical regressions (memory leak, migration‑induced cron‑job loss) that require maintainer attention.

## 2. Releases
### v2026.8.1 (2026‑08‑31)
**Highlights**
- **Find past conversations** – search visible conversation text by exact words/phrases and reopen surrounding messages (#105057, #105635, #105585).
- **Sessions beyond your Gateway** – run work on paired devices or cloud.

**Migration / Breaking Notes**
- The 2026.8.1 scheduler migration **quarantines valid legacy cron jobs as `invalid‑schedule`**, silently dropping active inventory (#133347). A fix PR (#133773) is open to allow legacy exec‑approvals migration.
- Beta‑tagged updates may leave external official plugins on the `latest` dist‑tag instead of the requested beta (#97680).

**GitHub Links**
- Release: https://github.com/openclaw/openclaw/releases/tag/v2026.8.1
- Beta feedback: https://github.com/openclaw/openclaw/issues/125626
- Cron‑job migration bug: https://github.com/openclaw/openclaw/issues/133347

## 3. Project Progress
**Closed / Merged PRs (last 24 h)**
- **#128995** – Make full session actions (pin, mark unread, copy ID, move to group) available from chat header.
- **#130993** – Fix Responses sessions compacting before reaching context limit (reduces double‑counting of terminal usage).
- **#131733** – Ensure scheduler‑disabled CRUD no longer overwrites shared‑store runtime state of unrelated jobs.
- **#125471** – Keep Claude CLI OAuth available in Control UI after gateway restart.
- **#123535** – Avoid session‑catalog refresh storms on browser focus changes.

**Features Advanced**
- Session‑management reliability (compaction, shared‑store state, catalog refresh).
- UI polish (chat‑header actions, OAuth consistency).
- Cron‑job state integrity.

## 4. Community Hot Topics
| Issue | Comments | Theme | Underlying Need |
|-------|----------|-------|-----------------|
| [#125626](https://github.com/openclaw/openclaw/issues/125626) – 2026.8.1 beta feedback | 24 | Release validation | Users want structured channels for beta feedback and rapid iteration. |
| [#91588](https://github.com/openclaw/openclaw/issues/91588) – Gateway memory leak (350 MB → 15.5 GB) | 23 | Stability / OOM crashes | Critical need for memory‑safe gateway operation under long‑running workloads. |
| [#42475](https://github.com/openclaw/openclaw/issues/42475) – Per‑agent cost budget enforcement | 22 | Feature / cost control | Operators require guardrails against runaway spend at the gateway level. |
| [#102175](https://github.com/openclaw/openclaw/issues/102175) – Embedded prompt cache breaks across boundaries | 18 | Regression / cache inefficiency | Users expect prompt‑cache reuse to survive session‑state transitions. |
| [#22676](https://github.com/openclaw/openclaw/issues/22676) – Signal daemon stop() race on SIGUSR1 | 17 | Crash‑loop / restart reliability | Stable config‑reload requires proper process‑lifecycle management. |
| [#87744](https://github.com/openclaw/openclaw/issues/87744) – Codex‑backed Telegram turns time out | 17 | Channel reliability | Telegram users need deterministic turn completion. |
| [#79077](https://github.com/openclaw/openclaw/issues/79077) – Telegram guest‑bot & bot‑to‑bot support | 13 | Feature request | Demand for new Telegram platform features (released 2026‑05‑07). |

**Analysis**
The community is actively stress‑testing the 2026.8.1 release (beta feedback, memory‑leak reports, cron‑job migration issues). There is a strong appetite for **operational guardrails** (cost budgets, prompt‑cache consistency, restart reliability) and **channel‑specific enhancements** (Telegram guest‑bots, WhatsApp listen‑only mode).

## 5. Bugs & Stability
**Critical / High‑Severity Bugs (P0–P1)**

| Issue | Severity | Summary | Fix PR? |
|-------|----------|---------|---------|
| [#133347](https://github.com/openclaw/openclaw/issues/133347) | P1 | 2026.8.1 migration quarantines valid cron jobs, silently drops active inventory. | Yes – #133773 |
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | P1 | Gateway memory leak (RSS grows to 15.5 GB) → OOM crashes. | No |
| [#108395](https://github.com/openclaw/openclaw/issues/108395) | P0 | Assistant generates fake “Human: [timestamp]” messages, enabling self‑authorization. | No |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | P1 | Leaks unreaped hook/tool child processes → zombie accumulation. | No |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | P1 | WhatsApp inbound image wedges main lane ~3 min before processing. | No |
| [#87744](https://github.com/openclaw/openclaw/issues/87744) | P1 | Codex‑backed Telegram turns repeatedly time out waiting for turn/completed. | No |
| [#114020](https://github.com/openclaw/openclaw/issues/114020) | P1 | Feishu/Telegram channel dispatch fails (`runChannelInboundEvent` requires `runDispatchLifecycle`). | No |
| [#112668](https://github.com/openclaw/openclaw/issues/112668) | P1 | `sessions_yield` abort‑settle timeout drops subagent announce on 2026.7.1‑2. | No |

**Regressions / Notable Bugs (P2)**
- [#102175](https://github.com/openclaw/openclaw/issues/102175) – Embedded prompt‑cache breaks across room‑event/policy/Responses boundaries.
- [#131340](https://github.com/openclaw/openclaw/issues/131340) – Code Mode mutation recovery lacks canonical effect‑provenance contract.
- [#98435](https://github.com/openclaw/openclaw/issues/98435) – MCP loopback transport does not auto‑reconnect after gateway restart.

**Stability Assessment**
The project is experiencing **release‑day instability** (migration bugs, memory leaks, process‑lifecycle races). Critical P0 security issue (#108395) and multiple P1 reliability bugs indicate that the next patch release should prioritize stability fixes.

## 6. Feature Requests & Roadmap Signals
| Issue | Request | Likelihood in Next Version |
|-------|---------|----------------------------|
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | Per‑agent cost‑budget enforcement at gateway | **High** – operator demand is clear; already tagged P2. |
| [#79077](https://github.com/openclaw/openclaw/issues/79077) | Telegram guest‑bot & bot‑to‑bot modes | **Medium** – Telegram released features in May 2026; still stale. |
| [#78963](https://github.com/openclaw/openclaw/issues/78963) | WhatsApp listen‑only / hooks‑only mode | **Medium** – use‑case specific; low‑risk addition. |
| [#90916](https://github.com/openclaw/openclaw/issues/90916) | Topic‑session families for one assistant across multiple named context lanes | **Low** – architectural change; needs product decision. |
| [#53763](https://github.com/openclaw/openclaw/issues/53763) | Built‑in headless browser for reliable web access | **Low** – bundles Chromium; significant dependency. |
| [#12678](https://github.com/openclaw/openclaw/issues/12678) | Capability‑based permissions for skills/tools (default‑deny) | **Medium** – security‑focused; aligns with current hardening trends. |
| [#52640](https://github.com/openclaw/openclaw/issues/52640) | Persistent task‑status surface for long‑running channel turns | **Low** – UX enhancement; can be phased. |

**Roadmap Signals**
- **Cost control & security** are top user priorities (cost budgets, permission models, fake‑message security fix).
- **Channel‑specific capabilities** (Telegram, WhatsApp, Feishu) remain in demand.
- **Session‑management abstractions** (topic‑session families, persistent status surfaces) are requested but may be lower priority.

## 7. User Feedback Summary
**Pain Points**
- **Gateway reliability**: Memory leaks (#91588) and zombie‑process accumulation (#97616) cause crashes and degrade performance.
- **Channel‑specific bugs**: Telegram turns time out (#87744), WhatsApp image processing wedges (#96834), Feishu/Telegram dispatch fails (#114020).
- **Migration pain**: 2026.8.1 upgrade silently quarantines valid cron jobs (#133347), breaking automations.
- **Security concerns**: Assistant can generate fake “Human:” messages to self‑authorize actions (#108395) – a P0 issue.
- **UX friction**: Prompt‑cache breaks across session boundaries (#102175), MCP loopback not auto‑reconnecting (#98435).

**Positive Feedback**
- New conversation‑search feature is well‑received (multiple beta‑feedback comments).
- Session‑management PRs (#130993, #131733) address real operational headaches.

**Overall Satisfaction**
Users are **frustrated by release‑day regressions** but appreciate the rapid bug‑fix cadence and active beta‑testing loop. The project’s strength lies in its responsive community and maintainers’ willingness to engage with complex reliability issues.

## 8. Backlog Watch
**Long‑Unanswered Important Issues (stale / needs maintainer decision)**

| Issue |

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Report — 2026-08-31

## 1. Ecosystem Overview

The open-source personal AI assistant landscape is in a high-velocity stabilization phase. Nine of ten tracked projects shipped significant development activity this period, with a clear industry-wide pivot from feature expansion toward session reliability, local-first deployment, and operational guardrails. Memory management, channel integrity, and startup/onboarding friction are the dominant cross-cutting concerns. Two projects (NullClaw, ZeptoClaw) showed zero activity, suggesting either maintenance-mode status or smaller contributor bases.

## 2. Activity Comparison

| Project | Open Issues | Open PRs | Release Status | Health Signal |
|---|---|---|---|---|
| **OpenClaw** | 266 | 309 | v2026.8.1 (today) | 🔴 High velocity, stability pressure |
| **NanoClaw** | ~2 (new today) | 25 | None today | 🟡 Review-heavy, pre-release consolidation |
| **ZeroClaw** | ~50 | ~50 | None today | 🔴 RFC-dense, architectural review phase |
| **Hermes Agent** | 40 | ~50 | v0.20.5 (Aug 19) | 🟡 Bug-heavy, session-stability focus |
| **CoPaw** | 18 | ~27 | v2.2.0-beta.3 (Aug 28) | 🟡 Pre-release stabilization sprint |
| **IronClaw** | 0 | ~11 | None today | 🟢 Healthy maintenance, active CI hardening |
| **LobsterAI** | ~7 | ~7 | None today | 🟡 Moderate; critical PRs stale 4–5 months |
| **NanoBot** | 7 | 29 | None today | 🟢 Steady resolution, memory refactor cycle |
| **Moltis** | ~1 | ~2 | 20260830.01 (Aug 30) | 🟢 Small but productive |
| **PicoClaw** | 2 | 1 | None today | 🔴 Critical bugs unresolved, single contributor |
| **NullClaw** | — | — | None | ⚪ No activity |
| **ZeptoClaw** | — | — | None | ⚪ No activity |

## 3. OpenClaw's Position

**Advantages vs. peers:**
- Highest raw development velocity (500+ issue/PR updates in 24h), indicating the largest active contributor base and fastest iteration cadence.
- Only project with a **release-grade feature** shipped today (conversation search + cross-device sessions), paired with an active beta-feedback loop.
- Strongest community engagement density — 7+ issues with 15+ comments each, demonstrating a mature support ecosystem.

**Technical approach differences:**
- OpenClaw operates a **gateway-centric** architecture (single process managing channels, sessions, and tools), whereas NanoBot and Hermes Agent use more modular runner-level designs.
- OpenClaw's session-compaction and shared-store fixes (#130993, #131733) show a focus on **operational reliability at scale**, while NanoClaw is simultaneously building provider abstraction layers.
- ZeroClaw is pursuing a **RFC-driven architecture** (session ownership contracts, WASM plugins, mTLS relay) — more fundamental than OpenClaw's incremental hardening.

**Community size:** OpenClaw's 266 open issues and 309 open PRs far exceed every other project, suggesting it has the largest developer and power-user community by an order of magnitude.

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Need |
|---|---|---|
| **Session-state reliability** | OpenClaw, Hermes Agent, CoPaw, NanoBot | Compaction failures, stuck states, and crash-loops are the #1 cross-project pain point |
| **Local-first / cost control** | NanoClaw, ZeroClaw, OpenClaw | BYOK, Ollama integration, per-agent cost budgets, local model prompt optimization |
| **Channel integration quality** | OpenClaw, NanoBot, LobsterAI, CoPaw | Telegram timeouts, WhatsApp wedges, Feishu config corruption, Discord routing |
| **Memory system architecture** | NanoBot, ZeroClaw, OpenClaw | Explicit recall by default, pluggable backends, prompt-cache persistence across boundaries |
| **Onboarding friction** | NanoClaw, LobsterAI, CoPaw | External account requirements, silent auth failures, missing provider keys |
| **Startup / bootstrap performance** | CoPaw, OpenClaw, NanoBot | Windows ACP stalls, gateway memory leaks, session-catalog refresh storms |
| **Loop / runaway guardrails** | IronClaw, ZeroClaw, OpenClaw | Tool-call budgets, wall-clock timeouts, cron-migration safety |

## 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | Hermes Agent | NanoClaw | ZeroClaw | IronClaw | CoPaw | LobsterAI | PicoClaw | Moltis |
|---|---|---|---|---|---|---|---|---|---|---|
| **Primary architecture** | Gateway monolith | Modular runner | Desktop-first agent | Provider-abstracted | RFC-driven runtime | Rust/WASM runtime | Electron + Tauri | Electron renderer | Embedded (RISC-V) | Execution nodes |
| **Target user** | Power users, operators | General assistant | Desktop users | Self-hosters | Researchers / builders | Production reliability | Enterprise / China | Chinese enterprise | Edge/embedded | Multi-node orchestration |
| **Key differentiator** | Cross-device sessions, breadth of channels | Pluggable memory backend, MST metasearch | Subagent compression, skill index | Local web chat, Ollama one-command | WASM plugins, mTLS relay | Loop termination, error taxonomy | Codex/Qoder harness, Feishu depth | In-app browser panel | Embedded deployment | Arm64/Docker support |
| **Security posture** | P0 self-authorization bug (open) | Good (credential preservation) | Multiple P1/P2 stability gaps | Symlink snapshot corruption risk | S1 stack overflow, RUSTSEC advisory | Clean (0 open issues) | glib unsoundness (open) | Stale high-severity PRs | Destructive auto-compression | arm64 fix resolved |
| **Release discipline** | Active (v2026.8.1) | Pre-release | Steady (v0.20.5) | None today | None today | None today | Beta sprint | None today | None today | Daily builds |

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (high velocity, frequent releases):**
- **OpenClaw**: 500+ updates/day, release shipped today, but stability pressure from P0/P1 bugs.
- **ZeroClaw**: 100 updates/day, but all PRs open — RFC review phase, not yet shipping.
- **CoPaw**: 51 updates/day, active beta.3 → beta.4 transition with security patching sprint.

**Tier 2 — Active Development (steady, focused):**
- **NanoBot**: High PR throughput (29 active), memory refactor cycle in progress, no release yet.
- **Hermes Agent**: 50 updates/day, bug-heavy, desktop-first with growing subagent tooling.
- **NanoClaw**: 25 PRs in review, provider abstraction work, pre-release consolidation.

**Tier 3 — Maintenance & Polish (low issue count, targeted fixes):**
- **IronClaw**: 0 open issues, clean CI hardening, loop-termination fix landed.
- **LobsterAI**: Moderate activity, but 4–5 month stale PRs for critical bugs.
- **Moltis**: Small but productive, resolved arm64 issue after 3-month gap.

**Tier 4 — Dormant or Minimal:**
- **PicoClaw**: 2 open issues, both critical, single active contributor, no fix PRs.
- **NullClaw / ZeptoClaw**: Zero activity — likely maintenance-mode or very small teams.

## 7. Trend Signals

1. **Local-first is no longer optional.** NanoClaw (Ollama one-command), ZeroClaw (local_small profile), and OpenClaw (BYOK demand via Conifer) all signal that self-hosted, cost-controlled deployment is a primary user requirement. Developers should prioritize local model compatibility and BYOK flows.

2. **Session state is the new security boundary.** Across OpenClaw (P0 self-authorization), ZeroClaw (session ownership contracts), CoPaw (config corruption), and Hermes Agent (compaction loops), untrusted or partially-trusted session data is a growing attack and reliability surface. Runtime ownership models and compaction persistence are emerging as critical infrastructure.

3. **Channel integration is a reliability moat, not a feature list.** Telegram timeouts, WhatsApp wedges, Feishu config drift, and Discord routing bugs are consistently the top user complaints. Projects that ship robust channel drivers (CoPaw's Feishu depth, OpenClaw's multi-channel breadth) gain disproportionate user trust.

4. **Memory architecture is fragmenting.** NanoBot (pluggable backends, explicit recall), ZeroClaw (lifecycle decoupling RFCs), and OpenClaw (prompt-cache persistence) are pursuing divergent memory models. The lack of a shared standard means tool authors must target multiple abstractions.

5. **RFC-driven architecture is replacing feature-driven shipping.** ZeroClaw's RFC process and IronClaw's design-system phase work indicate a shift toward deliberate architectural decisions before implementation. Projects that ship fast without this discipline (OpenClaw's migration bugs, CoPaw's beta regressions) pay stability costs.

6. **Embedded and edge deployment is a niche with real demand.** PicoClaw's critical data-loss and input-lag bugs on RV1106/RISC-V hardware represent an underserved segment. The community feedback is intense but the project lacks maintainers to address it — a gap for competitors.

**Value for AI agent developers:** The ecosystem is converging on three non-negotiables for 2026–2027: reliable session persistence, local-model support, and channel robustness. Projects that treat these as foundational rather than additive will outperform those that layer them on top of a gateway-only architecture. The open P0 security issue in OpenClaw and the symlink corruption risk in NanoClaw are cautionary signals that data-integrity guarantees must be baked into the runtime, not bolted on.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-31

## 1. Today's Overview

NanoBot shows high development velocity with 7 open issues and 29 active pull requests updated in the last 24 hours. Four issues were closed and eight PRs merged, indicating steady resolution throughput. No new releases were published this period, suggesting the team is focused on stabilizing incoming changes before the next tagged version. Activity is concentrated around memory management refactors, channel integrations, and bug fixes.

## 2. Releases

No new releases were published during this reporting period.

## 3. Project Progress

**Closed/Merged today:**
- **#5463** — DingTalk stream handler now properly observes and drains inbound background tasks, fixing a resource leak.
- **#5582** — Cron jobs created from WebUI quote/@mention turns no longer crash at scheduling or fire time.
- **#5583** — Tool exceptions now carry the "try a different approach" recovery hint, improving agent resilience.
- **#5593** — Rate-limit state for `SendSessionMessageTool` no longer retains expired timestamps from one-shot sessions.
- **#5600** — Native reasoning streams are now properly closed on cancellation, preventing stalled provider connections.
- **#5338** — MCP OAuth credentials are preserved when the OAuth store read fails, preventing cross-server credential overwrite.

**Actively advancing PRs (unmerged):**
- **#5234** — MST (Meta-Search Tool) integrated as a web search provider, aggregating multiple engines via Reciprocal Rank Fusion.
- **#5615** — Ephemeral runtime context lifecycle added, allowing per-turn context that isn't persisted to session.
- **#5610** — Memory summaries now accumulate across consolidations rather than replacing checkpoints.
- **#5580** — Session persistence moved off the event loop for thread safety, a critical refactor for production reliability.
- **#5571** — Explicit memory recall required by default, reducing unnecessary context preloading.
- **#5570** — Pluggable memory recall backend defined, enabling custom storage backends.
- **#5568** — Context compaction ownership moved to `AgentRunner`, unifying the request-fitting pipeline.
- **#5612** — Runner-level request fitting refactored to use provider-reported context usage when decisive.
- **#5608** — Transcript assembly deferred to the runner for tighter coupling with execution flow.
- **#5613** — Replayed provider item IDs are now cleaned before being sent to providers, preventing API errors.
- **#5611** — Reasoning replay is bounded to the latest assistant turn, eliminating unnecessary prefill cost.
- **#5614** — Telegram rich message streaming support added.
- **#5531** — Telegram streaming preview now upgrades to rich format in-place at stream end.
- **#5609** — Microsoft delegated OAuth for Office365/Outlook email channel.
- **#5607** — AnySearch added as a key-optional, anonymous-quota web search provider.
- **#5606** — Email channel now filters by recipient alias to avoid processing irrelevant mail.
- **#5605** — Email `\Seen` flag now applied only to actually delivered messages.
- **#5601** — WebUI rejected messages now roll back saved attachments and WebSocket subscriptions.

## 4. Community Hot Topics

- **AnySearch integration** — [#5505 (Issue)](https://github.com/HKUDS/nanobot/issues/5505) · [#5607 (PR)](https://github.com/HKUDS/nanobot/pull/5607): The AnySearch team proposed and submitted an integration for their key-optional, anonymous-quota search API. Reflects growing demand for cost-effective, no-API-key web search options in agent toolchains.
- **Feishu multi-turn consolidation** — [#5567 (Issue)](https://github.com/HKUDS/nanobot/issues/5567): Users report poor experience when a single user message triggers multiple separate Feishu messages (tool tips, progress, final reply). The request for a single streaming card message highlights a need for cleaner channel UX parity.
- **MST metasearch provider** — [#5234 (PR)](https://github.com/HKUDS/nanobot/pull/5234): Aggregating DuckDuckGo, Google, Brave, Bing via Reciprocal Rank Fusion. Signals community appetite for richer search coverage beyond single-engine providers.
- **Memory system overhaul** — [#5570](https://github.com/HKUDS/nanobot/pull/5570), [#5571](https://github.com/HKUDS/nanobot/pull/5571), [#5610](https://github.com/HKUDS/nanobot/pull/5610): Multiple coordinated PRs reworking memory recall, summarization, and persistence. This is the most significant architectural shift in the current cycle.

## 5. Bugs & Stability

| Severity | Issue/PR | Description | Fix Status |
|----------|----------|-------------|------------|
| **High** | [#5582](https://github.com/HKUDS/nanobot/issues/5582) | Cron jobs from WebUI quote/@mention crash at creation or fire time | ✅ Closed (#5582) |
| **High** | [#5463](https://github.com/HKUDS/nanobot/issues/5463) | DingTalk background tasks not observed/drained, causing resource leak | ✅ Closed (#5463) |
| **Medium** | [#5593](https://github.com/HKUDS/nanobot/issues/5593) | Rate-limit deque retains expired one-shot session timestamps | ✅ Closed (#5593) |
| **Medium** | [#5600](https://github.com/HKUDS/nanobot/pull/5600) | Cancellation mid-reasoning leaves provider stream open | ✅ Merged |
| **Medium** | [#5338](https://github.com/HKUDS/nanobot/pull/5338) | MCP OAuth store read failure overwrites other servers' credentials | ✅ Merged |
| **Low** | [#5613](https://github.com/HKUDS/nanobot/pull/5613) | Replayed provider item IDs cause API errors in fresh/continued requests | In progress |
| **Low** | [#1697](https://github.com/HKUDS/nanobot/issues/1697) | Query results not returned automatically; security permission config unclear | ⚠️ Open (stale since Mar 2026) |

## 6. Feature Requests & Roadmap Signals

- **Ephemeral runtime context** (#5615) — Per-turn context that doesn't persist to session storage. Likely to ship in the next minor release as it addresses token budget concerns.
- **Explicit memory recall by default** (#5571) — Stopping automatic preloading of `MEMORY.md` and `history.jsonl`. This is a behavior change that may become default in the next release pending review.
- **Pluggable memory backend** (#5570) — Defines a clean interface for custom memory stores; may enable third-party backends in future versions.
- **Microsoft OAuth for email** (#5609) — Response to Office365 deprecating basic auth; expected to be included in the next channel-focused release.
- **AnySearch provider** (#5607) — Following the established Serper pattern; low-risk addition likely to be merged soon.
- **Cumulative memory summaries** (#5610) — Retains both previous checkpoint and new content; a significant memory quality improvement.

## 7. User Feedback Summary

- **Feishu UX fragmentation** is the most vocal complaint: users expect a 1:1 message correspondence (one user message → one agent reply) but receive scattered tool-progress messages.
- **Cron job crashes from WebUI** are a high-impact bug — users who rely on quoted-turn scheduling for reminders experience data loss.
- **Search provider diversity** is a recurring theme: both AnySearch and MST PRs demonstrate demand for alternatives to existing providers, especially no-key or aggregated options.
- **Memory bloat** is a growing concern: users and maintainers alike are pushing for explicit recall, bounded reasoning replay, and ephemeral context to control token costs.
- **Email channel reliability**: multiple fixes this cycle (\Seen flag handling, alias filtering, OAuth migration) suggest the email channel had accumulated enough friction to warrant a focused overhaul.

## 8. Backlog Watch

- **[#1697](https://github.com/HKUDS/nanobot/issues/1697)** — Open since March 2026 with no resolution. Reports missing query results and unclear security permission configuration. Needs maintainer triage.
- **[#5531](https://github.com/HKUDS/nanobot/pull/5531)** — Telegram rich message streaming fix has been open since Aug 25. The author notes it will be used in production during the review week, indicating urgency.
- Memory system PRs (#5570, #5571, #5610, #5568, #5612, #5608) form a large coordinated refactor. Their interdependencies may slow individual merges; maintainers should coordinate review ordering to avoid prolonged review queues.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-31

## 1. Today's Overview
Hermes Agent shows **high daily activity** with 50 issues and 50 pull requests updated in the last 24 hours. The project is in a **bug‑heavy phase** (40 open issues today, 10 closed) with a strong focus on session‑state stability, compression reliability, and platform‑specific desktop fixes. No new releases were published today. Development effort is split between resolving critical P1/P2 bugs and advancing long‑standing feature PRs (unified package manager, subagent skill compression, Discord adapter improvements).

## 2. Releases
*No new releases today.* The latest available version remains **v0.20.5** (2026.8.19).

## 3. Project Progress
- **3 PRs merged/closed** in the last 24 hours (per activity metrics).
- **Notable closed PR:** `#64325` – feat(picker): support glob patterns in `model.picker.hide` (advanced model‑picker configuration).
- **Feature PRs advancing in parallel:**
  - `#95281` – **pm: unified package manager** (dependency‑tree consolidation across Docker/Nix/Windows).
  - `#62925` – **feat(delegation): compact skill index for subagents** (reduces ~22k tokens/spawn on large skill trees).
  - `#72048` – **fix(discord): let free‑response channels quote another bot’s mention**.
  - `#71910` – **fix(gateway): reject a blank `prompt.submit` before it costs a full API call**.
- **Desktop/QoL fixes in progress:** `#99119` (wait for session visibility before clicking), `#99086` (fix floating‑pet facing logic inversion).

## 4. Community Hot Topics
| Issue/PR | Comments | Type | Summary |
|----------|----------|------|---------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 127 | bug | **Skills index stale/degraded** – freshness probe fails; index is >26h old. |
| [#48098](https://github.com/NousResearch/hermes-agent/issues/48098) | 8 | bug | **Desktop shows stale “Summarizing thread” status after compaction resumes**. |
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | 7 | feature | **Bot Group Chats should keep working after Desktop closes** (session‑state durability). |
| [#73503](https://github.com/NousResearch/hermes-agent/issues/73503) | 6 | bug | **Context compression is a no‑op at every call site** (session grows past context window). |
| [#95281](https://github.com/NousResearch/hermes-agent/pull/95281) | – | feature | **Unified package manager** – single dependency tree across platforms. |

**Underlying needs:**  
- **Index freshness & reliability** (#66616) is the top‑voted pain point, affecting skill discovery and tool availability.  
- **Session‑state robustness** (#48098, #97681, #73503) dominates discussions; users demand guarantee that long‑running or multi‑bot sessions survive desktop closure and compaction failures.  
- **Platform‑agnostic packaging** (#95281) reflects a community desire for simpler, consistent installation across Windows/macOS/Linux.

## 5. Bugs & Stability
*Ranked by severity (P1 > P2 > P3)*

### P1 – Critical/High Impact
| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#94405](https://github.com/NousResearch/hermes-agent/issues/94405) | **Windows desktop boot‑loop** – `/api/ws` rejects session token (env‑pinned `HERMES_DASHBOARD_SESSION_TOKEN` not reaching spawned backend). | No open fix PR yet. |
| [#98722](https://github.com/NousResearch/hermes-agent/issues/98722) | **Continuous “Summarizing thread” loop** – stale compression lock reclaimed, 600s no‑progress, never escapes. | No open fix PR yet. |
| [#98450](https://github.com/NousResearch/hermes-agent/issues/98450) | **In‑place compaction commit never stamps `_DB_PERSISTED_MARKER`** – live set regrows after compaction. | No open fix PR yet. |

### P2 – Moderate Impact
| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#96775](https://github.com/NousResearch/hermes-agent/issues/96775) | **Stalled preflight compression interrupted** – no durable backoff, re‑enters same strategy. | `#96775` (closed) – follow‑up to #78981. |
| [#84371](https://github.com/NousResearch/hermes-agent/issues/84371) | **Compaction dead‑loop** – preflight charges full reasoning replay but tail‑budget walk excludes it (middle=0). | No open fix PR yet. |
| [#99032](https://github.com/NousResearch/hermes-agent/issues/99032) | **TUI submit silently sends collapsed `[[ N lines ]]` placeholder** when paste token is missing. | No open fix PR yet. |
| [#87106](https://github.com/NousResearch/hermes-agent/issues/87106) | **SSRF guard blocks public URLs** when VPN DNS resolves to RFC 2544 range (198.18.0.0/15). | No open fix PR yet. |
| [#97488](https://github.com/NousResearch/hermes-agent/issues/97488) | **Lean compaction ceiling timeout leaves detached workers** – can falsely auto‑reset sessions. | `#97488` (closed). |
| [#98909](https://github.com/NousResearch/hermes-agent/issues/98909) | **`resolve_provider_full()` bypasses `providers.<name>.enabled: false`** – disabled provider still selectable. | No open fix PR yet. |

### P3 – Low/Trivial Impact
| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#73151](https://github.com/NousResearch/hermes-agent/issues/73151) | **macOS desktop shows two Dock icons** (setup app lacks `LSUIElement`). | No open fix PR yet. |
| [#37421](https://github.com/NousResearch/hermes-agent/issues/37421) | **mem0 `sync_turn` silently drops long conversations** on `INPUT_TOKEN_LIMIT_EXCEEDED`. | No open fix PR yet. |
| [#98774](https://github.com/NousResearch/hermes-agent/issues/98774) | **`run_tests.sh` venv probe only checks pytest** – drifted venv reports code failures instead of missing deps. | No open fix PR yet. |
| [#99065](https://github.com/NousResearch/hermes-agent/issues/99065) | **`/btw` in Desktop prints side‑question notice but answer never appears**. | No open fix PR yet. |
| [#93515](https://github.com/NousResearch/hermes-agent/issues/93515) | **Desktop auto‑speak reads each reply twice** (Edge TTS). | `#93515` (closed). |
| [#85427](https://github.com/NousResearch/hermes-agent/issues/85427) | **Discord typing‑indicator stuck** (two‑owner lifecycle/cleanup race). | No open fix PR yet. |
| [#99086](https://github.com/NousResearch/hermes-agent/issues/99086) | **Desktop floating pet always faces outward** (logic inversion). | `#99119` (open) partially addresses UI interaction; pet logic fix not yet raised. |
| [#99043](https://github.com/NousResearch/hermes-agent/issues/99043) | **Real‑profile refresh does not update browser storage** used by authenticated apps. | No open fix PR yet. |
| [#99066](https://github.com/NousResearch/hermes-agent/issues/99066) | **Desktop image lightbox can’t view tall/high‑res images** (object‑contain shrinks illegibly). | No open fix PR yet. |
| [#98926](https://github.com/NousResearch/hermes-agent/issues/98926) | **Title generation copies few‑shot example verbatim** on vague opening messages. | No open fix PR yet. |

**Stability assessment:** Session‑state and compression bugs dominate the P1/P2 tier, indicating that **long‑running multi‑turn sessions remain fragile**. Platform‑specific desktop issues (Windows boot‑loop, macOS dock icons, TUI paste handling) are actively reported but lack immediate fix PRs.

## 6. Feature Requests & Roadmap Signals
| Issue/PR | Type | Summary | Likelihood for Next Release |
|----------|------|---------|----------------------------|
| [#97681](https://github.com/NousResearch/hermes-agent/issues/97681) | feature | **Bot Group Chats should keep working after Desktop closes** (session‑state durability). | Medium – requires gateway/session‑state overhaul. |
| [#53037](https://github.com/NousResearch/hermes-agent/issues/53037) | feature | **Cron job creation should validate script file existence** (`no_agent: true`). | High – low‑risk, user‑requested validation. |
| [#62925](https://github.com/NousResearch/hermes-agent/pull/62925) | feature | **Compact skill index for subagents** (reduce per‑spawn token overhead). | High – already open, addresses performance pain. |
| [#95281](https://github.com/NousResearch/hermes-agent/pull/95281) | feature | **Unified package manager** (single dependency tree). | Medium – large scope, needs cross‑platform testing. |
| [#72048](https://github.com/NousResearch/hermes-agent/pull/72048) | bugfix | **Discord: allow free‑response channels to quote another bot’s mention**. | High – small, contained fix. |
| [#71910](https://github.com/NousResearch/hermes-agent/pull/71910) | bugfix | **Reject blank `prompt.submit` before it costs a full API call**. | High – prevents wasted tokens. |

**Roadmap signals:**  
- **Session‑state reliability** (issues #97681, #98722, #98450) is the clear top priority for users.  
- **Skill‑index freshness** (#66616) and **subagent compression** (#62925) indicate a push toward **efficiency and scalability** of agent deployments.  
- **Cross‑platform packaging** (#95281) suggests the team is moving toward a **unified distribution model** (Docker/Nix/PM).

## 7. User Feedback Summary
**Pain points (recent & recurring):**
1. **Session state loss** – desktop closure breaks group chats (#97681), compaction loops (#98722, #84371), and compression markers aren’t persisted (#98450).  
2. **Platform‑specific desktop bugs** – Windows boot‑loop (#94405), macOS dual Dock icons (#73151), TUI paste‑token drop‑through (#99032), floating‑pet facing inversion (#99086).  
3. **Tool‑level failures** – mem0 drops long conversations (#37421), Discord typing indicator stuck (#85427), SSRF guard blocks VPN‑resolved public URLs (#87106).  
4. **Configuration & auth gaps** – `resolve_provider_full()` ignores `enabled: false` (#98909), mem0 OSS mode fails without API key (#99121), cron jobs don’t validate script existence (#53037).  


</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-31

---

## 1. Today's Overview

PicoClaw (sipeed/picoclaw) shows modest but focused activity today, with 2 open issues and 1 open PR updated within the last 24 hours and no new releases. Both issues, raised by the same contributor (`chentianxiong123`), target critical runtime defects — one concerning data persistence integrity and the other a severe performance regression on low-resource hardware — suggesting the project is actively used in embedded deployment scenarios but facing growing pains around storage reliability and UI responsiveness. No PRs were merged or issues closed today, and the backlog PR #3222 (deltachat refactor) remains stale after nearly two months. Overall, the project health signal is **cautious**: user engagement is present and concrete, but the absence of recent releases and unresolved critical issues warrant attention.

---

## 2. Releases

No new releases were published today. There are also no recent release notes in the provided data. Users on embedded platforms should monitor the repo for an upcoming patch addressing the data-loss and input-lag issues flagged below.

---

## 3. Project Progress

**Merged/Closed PRs today:** None.

**Open PR under review:**
- [#3222](https://github.com/sipeed/picoclaw/pull/3222) — `refactor(deltachat): cleanup implementation, documentation — 200LOC` by `trufae`. Created 2026-07-03, last updated 2026-08-30, flagged as **stale**. The PR cleans up the Delta Chat integration by dropping legacy features, replacing a hardcoded relay list with a reference to the official website, removing password-based email configuration (secrets now live in jsonrpc), renaming `invite_link` → `join_invite_link`, and adding a full Delta Chat documentation section. Despite removing ~200 lines of code and modernizing the implementation, it has seen no maintainer response in over 55 days.

---

## 4. Community Hot Topics

| Item | Type | Author | Activity | Link |
|------|------|--------|----------|------|
| #3351 | Issue | chentianxiong123 | Open, 0 comments | [Issue #3351](https://github.com/sipeed/picoclaw/issues/3351) |
| #3350 | Issue | chentianxiong123 | Open, 0 comments | [Issue #3350](https://github.com/sipeed/picoclaw/issues/3350) |
| #3222 | PR | trufae | Stale, 55+ days | [PR #3222](https://github.com/sipeed/picoclaw/pull/3222) |

**Analysis of underlying needs:**

- **Issue #3351** reflects a fundamental trust concern: users expect session history to be *durably* stored. The discovery that auto-compression physically rewrites and deletes records from `.jsonl` files — rather than retaining a compressible but recoverable log — undermines the reliability of long-running conversational agents. This is especially critical for users who depend on PicoClaw as a personal memory assistant.
- **Issue #3350** points to a scalability gap in the Web UI's frontend architecture. The fact that input-box latency correlates with conversation history length suggests that the UI is likely re-rendering or re-processing the full history on every keystroke, rather than using virtualized or incremental rendering. This is a common pattern in early-stage agent UIs and signals a need for frontend performance profiling.
- **PR #3222** indicates community interest in cleaning up the Delta Chat module — a feature that appears to have accumulated technical debt. The stale status suggests either a maintainer bottleneck or misalignment on the refactor's scope.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| 🔴 **Critical** | [#3351](https://github.com/sipeed/picoclaw/issues/3351) | Auto-compression of session history **physically deletes** original records via `rewriteJSONL` in `pkg/memory/jsonl.go`, making historical data permanently unrecoverable after "memory loss" events. | None yet |
| 🟠 **High** | [#3350](https://github.com/sipeed/picoclaw/issues/3350) | Web UI input box exhibits **severe character-by-character latency** on embedded/low-performance devices (RV1106, RISC-V boards), with CPU usage spiking proportionally to conversation history length. | None yet |

**Assessment:** Both issues are **regressions or design flaws** rather than edge-case bugs. Issue #3351 is a data-integrity risk that could cause irreversible user data loss — the highest-priority item on the board. Issue #3350 limits the project's viability on its target embedded platforms. Neither has an associated fix PR as of today.

---

## 6. Feature Requests & Roadmap Signals

- **Persistent, append-only session storage** — Implicitly requested by #3351. Users need a guarantee that history compression is reversible or non-destructive. A likely roadmap addition: a dual-layer storage model (raw log + compressed index) or a write-ahead log (WAL) approach for session files.
- **Frontend virtualization / incremental rendering** — Implicitly requested by #3350. The correlation between history length and input lag is a strong signal that the Web UI needs architectural work (e.g., virtual scrolling, debounced history re-renders, or a WebAssembly-optimized rendering path) to remain viable on resource-constrained devices.
- **Delta Chat module cleanup** — PR #3222 signals community desire to modernize the Delta Chat integration. If merged, this could set a precedent for similar cleanups across other communication backends.

**Prediction for next release:** If a patch release is issued, it will most likely address #3351 (data persistence safeguard) as a critical fix, given the irreversible nature of the bug. #3350 may follow in a subsequent release once the rendering bottleneck is profiled.

---

## 7. User Feedback Summary

| Theme | Sentiment | Source |
|-------|-----------|--------|
| Session history is being permanently lost on auto-compression | 😡 Frustration / distrust | #3351 |
| Web UI is unusably slow on target embedded hardware | 😤 Dissatisfaction | #3350 |
| Delta Chat module needs modernization | 📝 Constructive | #3222 |

**Key pain points:**
1. **Data loss anxiety** — The #3351 issue strikes at the core value proposition of a personal AI assistant: remembering the user. When the storage layer silently rewrites and deletes history, user trust erodes rapidly.
2. **Embedded-first promise vs. reality** — PicoClaw positions itself for low-resource deployment, yet the Web UI performance on exactly those devices (RV1106, RISC-V) is degraded to the point of unusability. This is a brand-relevance issue.
3. **Single active contributor pattern** — Both critical issues today were filed by `chentianxiong123`, suggesting a small but deeply engaged power-user cohort. Their feedback is disproportionately valuable for steering the project.

---

## 8. Backlog Watch

| Item | Days Open | Risk |
|------|-----------|------|
| [#3222](https://github.com/sipeed/picoclaw/pull/3222) — Deltachat refactor (stale) | ~58 days | Medium. The PR improves code quality and documentation but has been ignored. Stale flags risk demotivating contributors. |
| [#3351](https://github.com/sipeed/picoclaw/issues/3351) — Destructive session compression | ~1 day | **High.** Critical data-loss bug with no assigned owner or fix PR. Needs maintainer triage immediately. |
| [#3350](https://github.com/sipeed/picoclaw/issues/3350) — Web UI input lag on embedded | ~1 day | **High.** Blocks the project's core embedded-use-case promise. No fix PR yet. |

**Recommendation:** Maintainers should prioritize triaging #3351 and #3350 this week. Both represent threats to the project's credibility with its target audience (embedded / edge AI assistant users). The stale PR #3222 should also be reviewed — even a "close with comment" response is better than silence for contributor retention.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-31

## 1. Today's Overview

NanoClaw is experiencing a period of high internal activity with 25 open PRs updated in the last 24 hours, yet zero merges or closes — indicating a large batch of work in active review rather than completion. Two new issues were filed covering provider integration and a mutable-state bug, both still unresolved. No releases were published, consistent with the project appearing to be in a development-heavy phase. Activity is concentrated around provider contract refactoring and skill/testing improvements, suggesting the core team is consolidating architecture before the next release.

## 2. Releases

No new releases in the reporting window.

## 3. Project Progress

No PRs were merged or closed today. The active PRs represent significant forward movement across several areas:

- **Provider contract refactoring** (PRs #3581, #3584, #3585, #3586, #3588, #3591): A coordinated refactor by `zvi-fried` implementing typed provider contracts for runtime, host, setup verification, Codex, OpenCode, and instruction rendering — foundational work for extensibility.
- **Codex integration** (PR #3593): Maps core tone and speed properties onto Codex personality and service tier, extending agent configurability.
- **Speed inference for groups** (PR #3592): Adds a core-owned speed inference property, improving how agent groups select model performance profiles.
- **Skill system hardening** (PRs #3675, #3676, #3677, #3678): Parallelizes CI checks, makes agent-flow tests executable, adds deterministic apply directives, and expands test coverage for main and companion skills.
- **Slack fixes** (PRs #3505, #3686): Routes attachments through mailbox mounts and preserves human authorship for delegated uploads.
- **Local model accessibility** (PRs #3546, #3547, #3548 by `amit-shafnir`): Ollama provider payload, engine seams for registry providers, and a one-command `ollama launch nanoclaw` experience.
- **Local web chat** (PR #3298): Adds a built-in web chat channel eliminating the account-creation barrier for new users.

## 4. Community Hot Topics

| # | Type | Title | Author | Link |
|---|------|-------|--------|------|
| #3685 | Issue | Support Conifer gateway as a provider | charlespers | [Issue #3685](https://github.com/nanocoai/nanoclaw/issues/3685) |
| #3684 | Issue | update-nanoclaw snapshot captures symlinks not content | dweekly | [Issue #3684](https://github.com/nanocoai/nanoclaw/issues/3684) |
| #3687 | PR | Fix: resolve tasks in chat sessions | matt1995ai | [PR #3687](https://github.com/nanocoai/nanoclaw/pull/3687) |
| #3298 | PR | feat(channels): add local web chat | amit-shafnir | [PR #3298](https://github.com/nanocoai/nanoclaw/pull/3298) |

**Analysis:** Issue #3685 reflects strong community demand for cost-free model access through Conifer's unified gateway — users want BYOK and local model support without vendor lock-in. Issue #3684 exposes a data-integrity risk in the update mechanism that could silently corrupt state on symlinked deployments, a concern for power users with complex directory layouts. PR #3687 addresses a real operational pain point where scheduled tasks become invisible to the agent on legacy installs, directly impacting reliability. PR #3298, though older, remains highly relevant as it removes the friction of external account creation — a top onboarding barrier.

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR | Link |
|----------|------|-------------|--------|------|
| **High** | #3684 | `update-nanoclaw` snapshot captures symlinks instead of content when `data/` or `groups/` are symlinked; rollback can restore links pointing to forward-migrated data, risking state corruption | None yet | [Issue #3684](https://github.com/nanocoai/nanoclaw/issues/3684) |
| **Medium** | #3687 | `ncl tasks` cannot discover tasks in chat sessions on installs predating per-series task sessions, reporting "No tasks." while mailbox holds live series (44 series observed) | [PR #3687](https://github.com/nanocoai/nanoclaw/pull/3687) | [PR #3687](https://github.com/nanocoai/nanoclaw/pull/3687) |
| **Low** | #3682 | Test failure in `skill-directives.test.ts` due to stale hardcoded file list after `add-slack` fence extension | [PR #3682](https://github.com/nanocoai/nanoclaw/pull/3682) | [PR #3682](https://github.com/nanocoai/nanoclaw/pull/3682) |

The symlink snapshot bug (#3684) is the most concerning stability item — it can cause silent data corruption during updates on non-trivial deployments. No fix PR exists yet.

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Next Release |
|---------|--------|----------------------------|
| Conifer gateway as first-class provider | Issue #3685 | Medium — aligns with ongoing provider contract work but adds external dependency |
| Ollama one-command local install | PR #3548 (`ollama launch nanoclaw`) | High — already in progress with supporting PRs #3546, #3547 |
| Local web chat channel | PR #3298 | High — removes onboarding friction, complements Ollama local-first story |
| Deterministic skill apply directives | PR #3676 | Medium — improves reproducibility but may be scoped to next minor |
| Slack authorship preservation | PR #3686 | High — bug-fix-adjacent, small scope |
| Speed/tone inference for Codex | PR #3593 | Medium — part of broader provider abstraction |

**Signal:** The roadmap is clearly trending toward **local-first, low-friction deployment** (Ollama, local web chat) and **provider abstraction** (typed contracts, Conifer). The next release will likely emphasize these themes.

## 7. User Feedback Summary

- **Onboarding friction** is the dominant pain point. Users struggle with external account requirements (bot tokens, QR scans, app registrations) before sending a single message. PR #3298 directly addresses this.
- **Cost sensitivity** is high. Issue #3685's request for Conifer (genuinely free, BYOK, local models) signals a user base actively seeking to reduce API spend.
- **Operational visibility** matters. PR #3687 reveals that users run NanoClaw at scale (44 series, 3602+ completed tasks) and need reliable task discovery — invisibility bugs erode trust.
- **Data integrity** is non-negotiable. The symlink snapshot bug (#3684) concerns users with complex, symlinked data layouts who depend on reliable updates.
- **Local model adoption** is growing. Three coordinated PRs (#3546, #3547, #3548) respond to users wanting to run NanoClaw on local Ollama instances without manual patching.

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [Issue #3684](https://github.com/nanocoai/nanoclaw/issues/3684) — symlink snapshot bug | ~1 day open, 0 comments | High-severity data integrity bug with no fix in progress |
| [PR #3298](https://github.com/nanocoai/nanoclaw/pull/3298) — local web chat | 14 days open | High-value onboarding feature sitting in review |
| [PR #3548](https://github.com/nanocoai/nanoclaw/pull/3548) — ollama launch command | 5 days open | Flagship local-model feature pending merge |
| [PR #3685](https://github.com/nanocoai/nanoclaw/issues/3685) — Conifer provider | ~1 day open, 0 comments | Community-requested provider with no maintainer response yet |

**Maintainer attention needed:** Issue #3684 should be triaged urgently given its data-corruption potential. PR #3298 and the Ollama suite (#3546–#3548) are high-impact features that have been open for multiple days and deserve review prioritization.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-31

## 1. Today's Overview

IronClaw shows moderate but focused development velocity, with 11 pull requests updated in the last 24 hours and zero new issues. Activity is dominated by infrastructure hardening (CI integration test unification, design-system lane integration) and two targeted bug-fix corrections in error handling. No new releases were shipped today. The project's issue backlog is empty, indicating active maintenance, while PR count suggests a healthy contributor cadence — particularly from core team members and Dependabot automation.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**Merged/Closed Today:**
- **#7959** — `chore(deps): bump the everything-else group` (16 updates including `uuid` 1.24.0→1.26.0, `base64` 0.22.1→0.23.1, `toml`). Merged 2026-08-30. [Link](https://github.com/nearai/ironclaw/pull/7959)

**Key PRs Advanced Today:**
- **#7992** — `ci: unify bounded integration execution` (XL, core contributor). Introduces a single `cargo nextest run` with a four-test concurrency ceiling for all integration targets, replacing shell-projection logic. [Link](https://github.com/nearai/ironclaw/pull/7992)
- **#7988** — `chore(agents): refresh codebase knowledge graph` (XS, bot). Nightly bootstrap snapshot refresh via the `Codebase Graph Refresh` workflow. [Link](https://github.com/nearai/ironclaw/pull/7988)
- **#7977** — `fix(loop): terminate on dominant repeated output, cap interactive wall clock` (XL, core). Reinstates a loop-termination mechanism after a prior digest-based terminator was removed (PR #7531), preventing runaway tool-call sessions like production run `e3513a4e` (593 tool calls / 70 minutes). [Link](https://github.com/nearai/ironclaw/pull/7977)
- **#7831** — `Design System Phase 3a foundation — Chromatic lane + missing token axes` (XL). Adds a non-blocking `webui-v2-chromatic` lane to `code_style.yml` for visual-regression coverage of the Phase 3 reskin. [Link](https://github.com/nearai/ironclaw/pull/7831)

## 4. Community Hot Topics

No issues were opened or updated today. Among open PRs, the highest-impact discussion topics are:

- **#7977** — Loop termination & wall-clock capping. Addresses a real production regression where a session ran 593 tool calls over 70 minutes with no progress. Indicates community need for robust agent loop safeguards. [Link](https://github.com/nearai/ironclaw/pull/7977)
- **#7985 & #7990** — Error-kind misclassification by `standardtoaster`. Two companion PRs correcting `FailureKind::InputEncode` misuse for domain failures (missing documents, unresolvable tool names). Reflects ongoing investment in precise error taxonomy for better UX. [Links: [#7985](https://github.com/nearai/ironclaw/pull/7985), [#7990](https://github.com/nearai/ironclaw/pull/7990)]
- **#7831** — Design System Phase 3 Chromatic lane. Long-running UI modernization effort gaining CI integration surface. [Link](https://github.com/nearai/ironclaw/pull/7831)

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| **High** | #7977 — Agent loop runaway | Production run `e3513a4e` (2026-08-27) executed 593 tool calls over 70 minutes with no progress; regression introduced by PR #7531 removing the digest-based terminator. | [#7977](https://github.com/nearai/ironclaw/pull/7977) |
| **Medium** | #7985 — Misclassified memory error | `read_document` returning `None` was mapped to `FailureKind::InputEncode`, producing misleading user-facing error *"the tool input could not be encoded"*. | [#7985](https://github.com/nearai/ironclaw/pull/7985) |
| **Medium** | #7990 — Misclassified tool-disclosure error | `failed_invalid_input` helper stamped `InputEncode` on unresolvable tool names, conflating them with malformed input. | [#7990](https://github.com/nearai/ironclaw/pull/7990) |
| **Low** | #7834 — Wasm dependency group | 4 updates pending (wasmtime, wasmtime-wasi, wit-component, wit-parser). No reported bugs, but stale Wasm runtime deps could introduce regressions. | [#7834](https://github.com/nearai/ironclaw/pull/7834) |

## 6. Feature Requests & Roadmap Signals

- **Design System Phase 3 reskin** (#7831) — Chromatic visual-regression lane signals the project is actively investing in UI consistency and automated visual testing. Likely to appear in the next release cycle as the Phase 3 foundation.
- **Bounded integration test execution** (#7992) — Unifying integration targets under `cargo nextest` with fixed concurrency suggests a roadmap toward faster, more predictable CI. Could ship as a CI/infra improvement in the next patch.
- **Loop termination safeguards** (#7977) — The re-added termination logic and wall-clock cap indicate the roadmap prioritizes agent reliability and resource governance, likely a prerequisite for production-hardened releases.

## 7. User Feedback Summary

- **Pain point: Runaway agent sessions.** The production incident (593 tool calls, 70 min) reported via #7977 is the most significant user-facing concern. Users need reliable termination guarantees.
- **Pain point: Misleading error messages.** PRs #7985 and #7990 correct error taxonomy that previously confused users (e.g., "tool input could not be encoded" for a missing document). This suggests prior releases had poor error signal quality, now being remediated.
- **Satisfaction signal: Active bot maintenance.** Dependabot and the `ironclaw-ci[bot]` are keeping dependencies and knowledge graphs current with no open blockers, indicating a well-maintained operational baseline.

## 8. Backlog Watch

| PR | Size | Age | Concern |
|----|------|-----|---------|
| [#7834](https://github.com/nearai/ironclaw/pull/7834) — `wasm` deps bump | XL | 8 days | Stale Wasm runtime deps; 4 packages pending. |
| [#7020](https://github.com/nearai/ironclaw/pull/7020) — `tokio-tungstenite` 0.29→0.30 | S | 29 days | Long-open dependency update; low risk but neglected. |
| [#7831](https://github.com/nearai/ironclaw/pull/7831) — Design System Phase 3a | XL | 8 days | Critical UI roadmap PR; needs maintainer review to unblock Phase 3. |
| [#7992](https://github.com/nearai/ironclaw/pull/7992) — Bounded integration execution | XL | 1 day | Just opened; high-impact CI change requiring careful review. |

**Notable:** No open issues are languishing; the zero-issue count is a positive health signal. The primary backlog risk is the accumulation of large PRs (#7831, #7834, #7992) that require maintainer attention to merge.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-31

---

## 1. Today's Overview

LobsterAI showed moderate but focused activity on 2026-08-31, with **7 issues and 7 PRs** updated in the last 24 hours. No new releases were published today. The activity is overwhelmingly maintenance-driven: most closed items are stale issues resolved without code changes, while the live PRs target two high-priority areas — in-app browser interactivity and the Cowork authentication flow. The project appears to be in a consolidation phase, stabilizing the Electron/renderer layer rather than shipping major new features.

---

## 2. Releases

**No new releases published today.**

---

## 3. Project Progress

### Closed / Merged PRs (today)

| PR | Area | Summary |
|----|------|---------|
| [#2573](https://github.com/netease-youdao/LobsterAI/pull/2573) | renderer, cowork | Adds a dedicated welcome/login modal for unauthenticated Cowork users, preventing silent chat failures. |
| [#1765](https://github.com/netease-youdao/LobsterAI/pull/1765) | deps | Bumps `@headlessui/react` from 1.7.19 → 2.2.10 (Dependabot). |
| [#1769](https://github.com/netease-youdao/LobsterAI/pull/1769) | renderer, cowork | Replaces plain loading text with animated shimmer skeletons during Cowork initialization. |
| [#1770](https://github.com/netease-youdao/LobsterAI/pull/1770) | renderer | Enriches empty-state UI for Skills Manager and Task Run History with icons and subtitles. |

### Open PRs (still active)

- **[#2574](https://github.com/netease-youdao/LobsterAI/pull/2574)** — *Major*: Adds an interactive in-app browser embedded in the right-side artifact panel, routing OpenClaw browser tools through the MCP bridge. This is the most significant feature-level PR on the board today.
- **[#1127](https://github.com/netease-youdao/LobsterAI/pull/1127)** — *Bug fix*: Fixes a race condition in MCP `stop()` where a force-close timer fires after a new server has already started, incorrectly terminating the new server's connections.
- **[#1130](https://github.com/netease-youdao/LobsterAI/pull/1130)** — *Bug fix*: Fixes Anthropic SSE streaming data loss caused by missing line buffering when chunk boundaries split a JSON line.

---

## 4. Community Hot Topics

### Most Discussed Closed Issues

| Issue | Title | Comments | Link |
|-------|-------|----------|------|
| #1698 | Gateway port conflict & process competition between LobsterAI and 智企帝王蟹 on macOS | 4 | [#1698](https://github.com/netease-youdao/LobsterAI/issues/1698) |
| #1744 | Bug report (attachment failed to upload) | 4 | [#1744](https://github.com/netease-youdao/LobsterAI/issues/1744) |
| #1714 | White/invalid installer icon on Windows 11 | 3 | [#1714](https://github.com/netease-youdao/LobsterAI/issues/1714) |
| #1745 | OAuth2/new auth not supported for Outlook email connections | 3 | [#1745](https://github.com/netease-youdao/LobsterAI/issues/1745) |
| #1783 | Diff display broken after update — root-cause identified by contributor | 3 | [#1783](https://github.com/netease-youdao/LobsterAI/issues/1783) |

**Analysis:** The highest-engagement topics cluster around **integration compatibility** (port conflicts with sibling products, OAuth for email) and **frontend regressions** (diff display, installer icons). Issue #1783 is notable — a user identified the exact frontend bug (`extractDiffFromToolInput` in `app.asar`) and posted a full root-cause analysis, suggesting an engaged power-user base willing to contribute diagnostics.

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix PR? |
|----------|-----------|-------------|---------|
| **High** | [#1130](https://github.com/netease-youdao/LobsterAI/pull/1130) | Anthropic SSE streaming drops text when chunk boundaries split a `data:` line — silent JSON.parse failure. | ✅ Open PR #1130 (identical fix to OpenAI path) |
| **High** | [#1127](https://github.com/netease-youdao/LobsterAI/pull/1127) | MCP `stop()` force-close timer not cancelled; fires after `start()` creates a new server, killing new connections. | ✅ Open PR #1127 |
| **Medium** | [#1783](https://github.com/netease-youdao/LobsterAI/issues/1783) | Edit diff display broken post-update; root cause in `extractDiffFromToolInput` (only checks top-level `old_str`/`new_str`, misses nested paths). | ❌ No linked fix PR yet |
| **Medium** | #1698 | Gateway port conflict between LobsterAI and 智企帝王蟹 on macOS —必现 (deterministic reproduction). | ❌ No linked fix PR yet |
| **Low** | #1714 | Installer icon renders white/invalid on Windows 11. | ❌ No linked fix PR yet |
| **Low** | #1744 | Generic bug report; attachment upload failed, details unclear. | ❌ Unactionable without follow-up |

**Stability note:** Two high-severity bugs (SSE streaming loss, MCP timer race) have open fix PRs but remain unmerged. The diff-display regression (#1783) has a clear root cause identified by the community but no upstream fix yet — a candidate for the next patch cycle.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood for Next Release |
|---------|-------|----------------------------|
| In-app interactive browser panel (artifact-side) | [#2574](https://github.com/netease-youdao/LobsterAI/pull/2574) | **High** — PR is substantial, covers MCP bridge + profile persistence |
| Dynamic temperature adjustment via keywords in-chat | [#1688](https://github.com/netease-youdao/LobsterAI/issues/1688) | Medium — low-complexity but no PR yet |
| OAuth2 / modern auth for Outlook email | [#1745](https://github.com/netease-youdao/LobsterAI/issues/1745) | Medium — required for enterprise email integration |
| Scheduled task notification copy fixes | [#1751](https://github.com/netease-youdao/LobsterAI/issues/1751) | Low — UI copy issue, likely batched with other Cowork polish |

**Roadmap signal:** The in-app browser PR (#2574) is the clearest feature-direction indicator. It suggests the team is investing in deeper agent-browser integration (MCP bridge + profile persistence), which would distinguish LobsterAI from competitors still relying on external browser windows.

---

## 7. User Feedback Summary

**Pain points:**
- **Port/process conflicts** when running LobsterAI alongside related products (帝王蟹) — affects enterprise users who deploy multiple tools.
- **Email auth is stuck on legacy protocols**; Outlook blocks app passwords, leaving OAuth2 as the only path.
- **Diff display regression** after updates breaks the edit workflow — a core power-user feature.
- **Installer UX on Windows** (white/invalid icons) suggests QA gaps in the packaging pipeline.

**Positive signals:**
- Users are contributing deep diagnostics (Issue #1783 root-cause analysis).
- Skeleton loading and empty-state polish PRs show responsiveness to UX feedback.
- The authentication-gate PR (#2573) directly addresses the frustration of unauthenticated users hitting silent failures.

**Satisfaction takeaway:** Core functionality (browser, diff, MCP) is where friction concentrates; UI polish areas are improving steadily.

---

## 8. Backlog Watch

| Item | Days Open | Reason for Attention |
|------|-----------|---------------------|
| [#1127](https://github.com/netease-youdao/LobsterAI/pull/1127) — MCP timer race fix | ~153 days | High-severity bug fix, stale, needs review & merge |
| [#1130](https://github.com/netease-youdao/LobsterAI/pull/1130) — SSE streaming fix | ~153 days | High-severity bug fix, stale, needs review & merge |
| [#1783](https://github.com/netease-youdao/LobsterAI/issues/1783) — Diff display broken | ~132 days | Clear root cause provided by user, no fix PR yet |
| [#1698](https://github.com/netease-youdao/LobsterAI/issues/1698) — Gateway port conflict | ~138 days | Deterministic reproduction, affects enterprise deployments |
| [#1745](https://github.com/netease-youdao/LobsterAI/issues/1745) — Outlook OAuth2 | ~134 days | Blocks email integration for enterprise users |

**Recommendation:** PRs #1127 and #1130 have been open since March and address high-severity bugs. Prioritizing review and merge of these two would materially improve stability. Issue #1783 should be assigned given the contributor has already done the diagnostic work.

---

**Project Health Assessment:** 🟡 **Moderate** — Active maintenance and UX polish continue, but two critical bug-fix PRs and several high-impact issues have stalled for 4–5 months. The in-app browser PR (#2574) is a strong forward signal if it lands. Speeding up review velocity on the backlog would improve confidence significantly.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-31

## 1. Today's Overview

Moltis showed moderate but productive activity on 2026-08-31, with one new release, one bug fix merged, and one feature PR opened. The most notable event was the closure of a long-standing arm64/Docker compatibility issue ([#1085](https://github.com/moltis-org/moltis/issues/1085)) via PR [#1247](https://github.com/moltis-org/moltis/pull/1247), resolved after nearly three months of inactivity. One open PR ([#1248](https://github.com/moltis-org/moltis/pull/1248)) addresses execution node selection semantics. Overall project health appears stable with active bug resolution but low issue volume.

## 2. Releases

**20260830.01** (published 2026-08-30)
- Changelog details are not available from the source data. No breaking changes or migration notes are documented for this release.

## 3. Project Progress

- **Merged/Closed today:**
  - [#1247](https://github.com/moltis-org/moltis/pull/1247) — *fix(sandbox): drop DMI sysfs masks on arm64 Docker daemons* (Saraswat123). Resolves incorrect sysfs masking logic that caused Docker sandbox failures on Apple Silicon by unconditionally mounting DMI paths that do not exist on arm64.
- **Open today:**
  - [#1248](https://github.com/moltis-org/moltis/pull/1248) — *fix(exec): honor explicit null node selection* (mikemikimike). Restores expected behavior when `node: null` is explicitly set, preserving configured and provider-selected defaults. Includes a regression test.

## 4. Community Hot Topics

- **[Issue #1085](https://github.com/moltis-org/moltis/issues/1085)** — Docker sandbox fails on arm64 — *Closed today via #1247.* While this issue had zero comments and zero reactions, it represents a significant compatibility pain point for Mac users on Apple Silicon. The three-month gap between creation (2026-05-29) and resolution suggests the community may be smaller or less active on platform-specific issues, but the fix indicates the problem was real and impactful for affected users.

## 5. Bugs & Stability

| Severity | Bug | Status | Fix |
|----------|-----|--------|-----|
| Medium | [#1085](https://github.com/moltis-org/moltis/issues/1085) — Docker sandbox fails on arm64 due to hardcoded DMI sysfs mounts | ✅ Closed | [#1247](https://github.com/moltis-org/moltis/pull/1247) merged |

No new bugs or regressions were reported today. The resolved arm64 issue was the only stability concern in the reporting window.

## 6. Feature Requests & Roadmap Signals

- [#1248](https://github.com/moltis-org/moltis/pull/1248) signals ongoing refinement of the execution routing and node-selection subsystem. The fix to honor explicit `node: null` suggests users are exercising more sophisticated multi-node or provider-aware workflows and expect precise control over execution targets. This may indicate a roadmap trend toward more granular execution configuration in future releases.

## 7. User Feedback Summary

The primary user feedback captured today centers on **platform compatibility** (arm64/Docker on macOS) and **execution semantics precision** (null node selection). The arm64 bug, though low-visibility in comments/reactions, likely affected a non-trivial subset of Moltis users given the growing Apple Silicon user base. The exec fix PR suggests users are relying on Moltis for production-like orchestration where explicit node routing matters. No widespread satisfaction or dissatisfaction signals are evident from the current data.

## 8. Backlog Watch

- **[Issue #1085](https://github.com/moltis-org/moltis/issues/1085)** — Had been open for ~3 months before resolution. While now closed, its prior inactivity highlights a potential backlog risk for platform-specific issues that may not generate visible community engagement but still require maintainer attention.
- No other long-standing open issues were reported in the data snapshot. The project's low issue count (1 total in window) suggests either a healthy, stable codebase or limited community reporting activity.

---

*Data source: [github.com/moltis-org/moltis](https://github.com/moltis-org/moltis) · Generated 2026-08-31*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-31

---

## 1. Today's Overview

CoPaw (agentscope-ai/CoPaw) is in an active pre-release cycle for v2.2.0, with the beta.3 release currently undergoing installation verification (#7394). In the last 24 hours, 24 issues and 27 PRs were updated, with 18 open issues remaining active and 6 closed — a strong signal of a project in a stabilization sprint. Notably, **zero new releases** were published today, but several release-duty and security-cleanup PRs landed, suggesting the team is hardening beta.3 ahead of a potential final beta or rc. Activity is concentrated around console UI fixes, stream/cancellation correctness, and dependency vulnerability patching.

---

## 2. Releases

**No new releases published today.** The latest tracked release remains **v2.2.0-beta.3** (published 2026-08-28). PR #7423 bumps the version to **2.2.0b4**, indicating the next beta is being prepared. The release-notes PR #7348 (v2.2.0) remains open, suggesting release documentation is still being finalized.

---

## 3. Project Progress

### Merged / Closed Today
| Item | Type | Summary |
|------|------|---------|
| #7419 / #7418 | Bug | Step accordion collapsing — fixed to target only consecutive tool-call runs (#7419 closed, #7418 was duplicate) |
| #7399 | Clarification | `daily_users` UTC timestamp clarified as design choice (naive datetime = process-local time) |
| #6822 | Bug | Transient streamable HTTP MCP failure blocking conversation — resolved |
| #6785 | Bug | Profile category hard-coding regression — resolved |
| #7414 (PR) | Fix | PawApp fail-closed when chat runtime unavailable — merged alongside issue #7411 |

### Key PRs Advanced Today
- **#7429** — Excludes optional GPL Pylint provider from runtime dependencies (fixes #7428)
- **#7427** — Patches 5 frontend vulnerabilities in Creator UI lockfile (React Router → 7.18.3, Nano ID, PostCSS, Undici)
- **#7425** — Patches 86 vulnerable dependency instances in website lockfile (Mermaid → 11.17.2, fixes CVE-2026-4800)
- **#7415** — Makes PawApp SDK stream cancellation non-blocking and idempotent
- **#7413** — Preserves partial runtime state when async generator is closed via `GeneratorExit`
- **#7409** — Drops empty assistant text blocks that poison session history with upstream providers
- **#7421** — Restores protobuf decoding for Yuanbao provider on protobuf 6+
- **#7416** — Exposes `card_auto_layout` toggle for DingTalk widescreen cards in Console
- **#7401** — Prevents Windows ACP agent stalls during workspace bootstrap
- **#7383** — Avoids full `sys.modules` sweep after each plugin load (major Windows startup perf win)
- **#7372** — Unifies packaged Python runtime source for Tauri desktop builds

---

## 4. Community Hot Topics

### Most Discussed Open Issues
| Issue | Comments | Topic |
|-------|----------|-------|
| [#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420) | 4 | Tool results lost + doom-loop after `write_file` on 2.2.0-beta.1 |
| [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) | 4 | Long-running shell commands block Feishu sessions indefinitely |
| [#7408](https://github.com/agentscope-ai/QwenPaw/issues/7408) | 3 | Feishu channel config unexpectedly cleared → `KeyError` on cron dispatch |
| [#7402](https://github.com/agentscope-ai/QwenPaw/issues/7402) | 3 | Empty `output_text` blocks cause 400 errors on Volcengine Ark |
| [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) | 2 | Console stream shows duplicated text chunks mid-stream |
| [#7396](https://github.com/agentscope-ai/QwenPaw/issues/7396) | 2 | Claude Code third-party harness status/roadmap |
| [#7405](https://github.com/agentscope-ai/QwenPaw/issues/7405) | 2 | Plan Mode feature request |

**Analysis:** The dominant theme is **channel reliability under production loads** — Feishu session blocking (#6608), config corruption (#7408), and Ark provider errors from empty text blocks (#7402) all point to edge cases in message serialization and session persistence that surface under heavy or long-running usage. The Claude Code harness question (#7396) signals strong community interest in third-party agent integration beyond Codex/Qoder. The Plan Mode request (#7405) reflects a user desire for **proactive planning visibility** before execution, a pattern consistent with agentic workflow maturity.

---

## 5. Bugs & Stability

### Critical / High Severity
| Issue | Description | Fix Status |
|-------|-------------|------------|
| [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) | Shell command timeout bypass — sessions blocked for 1.5h, orphan subprocesses on cancel | No fix PR yet |
| [#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420) | Tool results lost + doom-loop on `write_file` after 2.2.0-beta.1 upgrade | No fix PR yet |
| [#7408](https://github.com/agentscope-ai/QwenPaw/issues/7408) | Feishu config wiped → cron `KeyError` | No fix PR yet |
| [#7402](https://github.com/agentscope-ai/QwenPaw/issues/7402) | Empty assistant `output_text` poisons session history, causes 400 from Ark | **PR #7409** opened |
| [#7417](https://github.com/agentscope-ai/QwenPaw/issues/7417) | Console shows duplicated text chunks mid-stream | No fix PR yet |
| [#7407](https://github.com/agentscope-ai/QwenPaw/issues/7407) | Console messages drift to wrong agent | No fix PR yet |
| [#7397](https://github.com/agentscope-ai/QwenPaw/issues/7397) | Browser SDK spawns new tab-group per `present()`/`open()` call | No fix PR yet |

### Security / Dependency
| Issue | Description | Fix Status |
|-------|-------------|------------|
| [#7430](https://github.com/agentscope-ai/QwenPaw/issues/7430) | glib unsoundness (GHSA-wrw7-89jp-8q8g) in Linux Tauri graph | No fix PR yet |
| [#7428](https://github.com/agentscope-ai/QwenPaw/issues/7428) | Optional GPL Pylint bundled in runtime | **PR #7429** opened |
| [#7426](https://github.com/agentscope-ai/QwenPaw/issues/7426) | 5 frontend vulns in Creator UI lockfile | **PR #7427** opened |
| [#7424](https://github.com/agentscope-ai/QwenPaw/issues/7424) | 86 vulns in website lockfile (incl. CVE-2026-4800) | **PR #7425** opened |

**Stability Assessment:** 7 open bug issues with no fix PRs, including two that cause session-blocking behavior (#6608, #7420). The v2.2.0-beta.1 upgrade path appears to have introduced regressions. Security PRs are being addressed rapidly (4 PRs landed today for 4 security issues).

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Request | Likelihood in v2.2.0 |
|------------|---------|---------------------|
| [#7396](https://github.com/agentscope-ai/QwenPaw/issues/7396) | Claude Code as third-party harness | Likely post-v2.2.0 (currently "Coming soon") |
| [#7405](https://github.com/agentscope-ai/QwenPaw/issues/7405) | Plan Mode — show model's planned steps before execution | Unclear; no PR yet |
| [#7406](https://github.com/agentscope-ai/QwenPaw/issues/7406) | Official theming support (accent color, font, spacing) | Low priority vs. bug fixes |
| [#7404](https://github.com/agentscope-ai/QwenPaw/issues/7404) | Surface `card_auto_layout` in Console DingTalk settings | **High** — PR #7416 already submitted |
| [#7163](https://github.com/agentscope-ai/QwenPaw/pull/7163) | Refined session thinking & model management UI | In progress — inline agent name editing |

**Prediction:** PR #7416 (DingTalk `card_auto_layout`) is the most likely feature to ship in v2.2.0b4. Plan Mode and Claude Code harness are strong roadmap candidates but unlikely before a v2.3 cycle.

---

## 7. User Feedback Summary

**Pain Points:**
- **Session blocking** is the top complaint: long-running shell commands (#6608) and MCP reconnect failures (#6822) leave users stranded with no recovery path.
- **Upgrade regressions**: Users upgrading from 2.1.0 → 2.2.0-beta.1 report tool-result loss and doom-loop behavior (#7420), suggesting insufficient integration testing on the new beta path.
- **Config fragility**: Feishu channel config being silently cleared (#7408) erodes trust in persistence layers.
- **Console UX quirks**: Duplicated stream chunks (#7417), message drift to wrong agent (#7407), and accordion behavior (#7419) indicate the web UI is still polishing its rendering pipeline.
- **Browser SDK tab management**: Users expect shared tab groups but get a new group per call (#7397).

**Satisfaction Signals:**
- Third-party agent harness support (Codex, Qoder) is well-received (#7396).
- The Plan Mode feature from earlier versions was appreciated and users want it back (#7405).
- Plugin load performance improvements (#7383) address a real Windows startup pain point.

---

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|-------|-----|----------------------|
| [#6608](https://github.com/agentscope-ai/QwenPaw/issues/6608) | ~24 days | Production-blocking; no fix PR. Shell timeout + orphan subprocess is a critical reliability gap. |
| [#7420](https://github.com/agentscope-ai/QwenPaw/issues/7420) | 1 day | Beta.1 regression with 5 stalls in one session. Needs triage before beta.3 is considered stable. |
| [#7408](https://github.com/agentscope-ai/QwenPaw/issues/7408) | 2 days | Config corruption affecting production Feishu deployments. No fix PR. |
| [#7407](https://github.com/agentscope-ai/QwenPaw/issues/7407) | 1 day | Message drift to wrong agent — correctness issue with no fix. |
| [#7397](https://github.com/agentscope-ai/QwenPaw/issues/7397) | 3 days | Browser SDK design flaw; no fix PR. |
| [#7430](https://github.com/agentscope-ai/QwenPaw/issues/7430) | <1 day | glib unsoundness (RUSTSEC-2024-0429) — unpatched in Linux Tauri graph. |
| [#7426](https://github.com/agentscope-ai/QwenPaw/issues/7426) | <1 day | 5 known frontend vulns — **PR #7427 addresses this**. |
| [#7424](https://github.com/agentscope-ai/QwenPaw/issues/7424) | <1 day | 86 vulns in website — **PR #7425 addresses this**. |

**Key Risk:** Issues #6608 and #7420 are the highest-risk open bugs. Both affect session correctness under real workloads and have no fix PRs. If #7420 is a beta.1 regression, it may block the v2.2.0 release candidate timeline. The glib unsoundness (#7430) is a supply-chain risk that will require a Tauri dependency bump.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-31

## 1. Today's Overview

ZeroClaw shows high development velocity with 100 activity items (50 issues + 50 PRs) updated in the last 24 hours, though none of the PRs have merged today. The project is in a dense RFC and architectural review phase, with multiple high-priority design proposals advancing simultaneously around session ownership, memory lifecycle, WASM plugins, and security boundaries. No new releases were published today, suggesting the team is prioritizing design ratification and bug hardening over shipping.

## 2. Releases

No new releases published today.

## 3. Project Progress

**No PRs merged or issues closed today** — all 50 PRs remain open. Active progress is concentrated in these areas:

- **Context compaction** (#9535): Adds model-window-ratio-driven context trimming, replacing fixed token budgets with adaptive compaction.
- **ZeroRelay secure transport** (#10142): Introduces mandatory mTLS with per-daemon CA and blind relay support, superseding #9080.
- **Session ownership contract** (#10412): Extracts atomic session-ownership claim into a shared `SessionBackend` trait with compare-and-set semantics.
- **Per-agent ownership scoping** (#9746): Binds session tools and `discord_search` to trusted per-agent scopes, closing check/use races.
- **Cron wall-clock timeouts** (#9320): Bounds agent job runs with configurable timeouts that properly release locks.
- **ZeroCode disconnect handling** (#10260): Fails RPC calls promptly on socket/WSS disconnect instead of hanging.
- **Rust toolchain bump** (#9527): Moves routine builders to Rust 1.98.0 while keeping source floor at 1.96.0.

## 4. Community Hot Topics

| Issue | Title | Comments | Link |
|---|---|---|---|
| #9487 | RFC: Runtime-owned conversation sessions & transport adapters | 28 | <https://github.com/zeroclaw-labs/zeroclaw/issues/9487> |
| #6850 | RFC: Decouple memory lifecycle from storage backends | 23 | <https://github.com/zeroclaw-labs/zeroclaw/issues/6850> |
| #9488 | RFC: Unified attachment architecture for web chat & channels | 22 | <https://github.com/zeroclaw-labs/zeroclaw/issues/9488> |
| #6996 | RFC: Granular sandbox policy — filesystem & network | 17 | <https://github.com/zeroclaw-labs/zeroclaw/issues/6996> |
| #8396 | RFC: Wire protocol first-class in provider construction | 16 | <https://github.com/zeroclaw-labs/zeroclaw/issues/8396> |
| #9103 | RFC: Separate authoritative memory from enrichment connectors | 16 | <https://github.com/zeroclaw-labs/zeroclaw/issues/9103> |
| #10118 | Tracker: Rust anti-slop policy debt remediation | 16 | <https://github.com/zeroclaw-labs/zeroclaw/issues/10118> |

**Analysis:** The top discussion themes reveal a project maturing its architecture boundaries — session ownership (#9487), memory lifecycle decoupling (#6850, #9103), and sandbox policy (#6996) are all interrelated efforts to separate concerns between runtime, channels, and storage. The anti-slop tracker (#10118) with 307 candidates across 1,078 files signals a serious code-quality initiative. The RFC process is heavily engaged, with multiple proposals receiving maintainer takeovers and revision cycles.

## 5. Bugs & Stability

| Issue/PR | Severity | Description | Fix PR |
|---|---|---|---|
| #10230 | **S1 — workflow blocked** | Daemon startup/reload stack overflow during agent init under Quickstart config | None yet |
| #10061 | **S1 — workflow blocked** | Provider-rejected images poison later turns in vision-capable sessions | #10088 (in progress) |
| #9654 | **P1** | Operator denial reaches model as unsemantic three words, model hallucinates cause | Sibling of #9423 |
| #9899 | **P1 — blocked** | `bitmaps 3.2.1` triggers RUSTSEC-2026-0247 advisory via Matrix SDK dev-deps | None yet |
| #10292 | **S2 — degraded** | ACP session tools cannot list or inspect Code sessions | None yet |
| #9905 | **S2 — degraded** | Discord audio transcription manager never bound to active agent provider | #10487 (in progress) |
| #9382 | — | WhatsApp empty `allowed_groups` admits no groups unless policy is `all` | #9382 |
| #9313 | — | WeChat sync cursor persisted before batch enqueue, causing data loss on retry | #9313 |

**Summary:** Three S1-severity issues are workflow-blocking. The stack overflow on daemon reload (#10230) and the image-poisoning bug (#10061) are the most impactful. The security advisory (#9899) remains blocked pending dependency triage.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Likelihood for Next Release |
|---|---|---|
| #5287 | Compact `local_small` runtime profile with prompt-budget contract | **High** — accepted, in-progress, 2 👍 |
| #10167 | Vendor-neutral lifecycle export for terminal multiplexers | **Medium** — in-progress, addresses real TUI integration gap |
| #10050 | Verbatim channel send over gateway without agent turn | **Medium** — RFC, fills a clear gateway capability gap |
| #10076 | Composable WASM plugin runtime architecture | **Medium** — RFC, extends existing WASM host |
| #6864 | Invert `zeroclaw-channels` → `zeroclaw-runtime` dependency | **Low** — architectural refactor, long-term |
| #10222 | Opt-in single-tool provider rounds for interactive agents | **Low** — RFC, niche interactive use case |
| #8766 | User-behavior E2E coverage for first-run setup | **Medium** — accepted, in-progress, testing infrastructure |

**Signal:** The `local_small` profile (#5287) and terminal multiplexer lifecycle export (#10167) have the strongest momentum and address clear user pain points around local-first deployment and TUI integration.

## 7. User Feedback Summary

- **Local-model prompt bloat** (#5287): Users running local models report excessive prompt size and leaking internal instructions into user-visible output — a real pain point for resource-constrained deployments.
- **First-run config reliability** (#8766): Previous dogfooding (#8505) showed plausible-but-broken first-run configs, driving the E2E test coverage request.
- **ZeroCode session isolation clarity** (#9341): Users need clearer boundaries between session history (resumable) and persistent memory (isolated) in the Code pane.
- **Discord audio transcription** (#9905, #10487): Audio attachments fail silently because the transcription provider is never bound — a degraded but impactful channel experience.
- **Image handling in vision sessions** (#10061, #10088): Rejected images persist in conversation history and corrupt subsequent turns, blocking workflows that mix text and image inputs.

## 8. Backlog Watch

| Issue | Days Open | Risk | Note |
|---|---|---|---|
| #10230 | 10 | **High** | S1 daemon stack overflow — no fix PR yet |
| #9899 | 21 | **High** | Security advisory blocked on dependency triage |
| #9654 | 29 | **High** | P1 denial semantics bug — sibling of #9423 scope gap |
| #8692 | 58 | **Medium** | Maintainer decision queue tracker — RFCs pending review |
| #6909 | 98 | **Medium** | Computer-use RFC — revision 2 accepted, awaiting implementation |
| #10118 | 12 | **Medium** | 307 anti-slop candidates across 1,078 Rust files |

**Key concern:** Three S1/P1 bugs (#10230, #9899, #9654) have no merged fixes and are impacting core daemon stability and security posture. The maintainer decision queue (#8692) being open for 58 days suggests a bottleneck in RFC triage that could slow upcoming releases.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*