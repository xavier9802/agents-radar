# OpenClaw Ecosystem Digest 2026-08-16

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-16 01:44 UTC

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



# OpenClaw Project Digest — 2026-08-16

## 1. Today's Overview

OpenClaw is exhibiting **very high development velocity** with 500 issues and 500 PRs updated in the last 24 hours, of which 452 PRs remain open and only 48 merged or closed. The project shipped one new beta release (v2026.8.1-beta.2) featuring secret egress host binding and GPT-5.6 Ultra runtime switching. Activity is overwhelmingly maintenance- and bug-fix-oriented: the top issues by comment count are dominated by message-loss, session-state, and subagent reliability problems, indicating the project is in a hardening phase as it scales to multi-agent deployments. Community engagement is intense, with the most-discussed issue (#121058) accumulating 96 comments on a recurring silent-reply-failure bug.

## 2. Releases

### v2026.8.1-beta.2 (2026-08-16)

**Highlights:**
- **Secret egress host binding** — Each shared-store secret is now bound to exact HTTPS destination hosts across CLI, Gateway RPC, and Control UI. Unbound sentinel substitution fails closed before any plaintext egress occurs. (Thanks @shakkernerd)
- **GPT-5.6 Ultra support** and runtime switching capabilities.

No explicit breaking changes or migration notes were documented in the release summary provided.

## 3. Project Progress

**Merged / Closed (last 24h):** 48 PRs
**New open PRs today:** Multiple UI and gateway fixes landed or advanced, including:

| PR | Summary | Status |
|---|---|---|
| [#124334](https://github.com/openclaw/openclaw/issues/124334) | Fix idle CPU spikes on multi-agent hosts (P1, diamond lobster) | Waiting on author |
| [#124336](https://github.com/openclaw/openclaw/issues/124336) | Show valid values for rejected audit filters | Ready for maintainer |
| [#124329](https://github.com/openclaw/openclaw/issues/124329) | Omit internal class names from RPC failures | Ready for maintainer |
| [#124162](https://github.com/openclaw/openclaw/issues/124162) | Discord disconnection watchdog in provider lifecycle (P1) | Needs proof |
| [#124222](https://github.com/openclaw/openclaw/issues/124222) | Route Telegram model-confirmation edit through rich funnel | Needs proof |
| [#123871](https://github.com/openclaw/openclaw/issues/123871) | Tolerate ownerless multi-agent diagnostics | Needs proof |
| [#123594](https://github.com/openclaw/openclaw/issues/123594) | Consistent session information cards in sidebar | Waiting on author |
| [#123645](https://github.com/openclaw/openclaw/issues/123645) | Refine sidebar Pages navigation | Ready for maintainer |
| [#122177](https://github.com/openclaw/openclaw/issues/122177) | Restore shared browser tabs after relay reconnect (P1) | Ready for maintainer |
| [#121871](https://github.com/openclaw/openclaw/issues/121871) | Stop duplicating channel reply when reasoning is used | Ready for maintainer |

**UI overhaul in progress:** A coordinated set of PRs by @vyctorbrzezowski is reworking the Control UI sidebar and chat experience (session cards, Pages nav, issue panel consolidation, incognito identity, transcript controls). This is the largest single track of activity today.

## 4. Community Hot Topics

| Issue | Comments | Rating | Topic |
|---|---|---|---|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) — Silent reply failures recurring after #116277 close | 96 | P1, diamond lobster | Message loss |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) — Realtime voice unbounded provider/consult state | 66 | P1, diamond lobster | Session state |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging by Source | 53 | P2, off-meta tidepool | Security |
| [#25592](https://github.com/openclaw/openclaw/issues/25592) — Text between tool calls leaks to messaging channels | 49 | P1, diamond lobster | Message loss / UX |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) — Subagent completion silently lost | 29 | P1, diamond lobster | Message loss |
| [#121953](https://github.com/openclaw/openclaw/issues/121953) — Cron agent stalls on DeepSeek due to prefix deprioritization | 20 | P1, platinum hermit | Model routing |

**Analysis:** The dominant theme is **reliability of message delivery and session state** in multi-agent, multi-channel configurations. Six of the top seven issues involve silent failures, message loss, or state leaks. Users are running OpenClaw in production with cron jobs, subagents, and real-time voice — and hitting edge cases where the system silently drops work. The DeepSeek stall issue (#121953) reveals emerging friction with newer model providers whose API edges deprioritize messages with certain prefixes.

## 5. Bugs & Stability

### Critical / P1 Bugs

| Issue | Severity | Summary | Fix PR? |
|---|---|---|---|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | P1, diamond lobster | Silent reply failures recur post-#116277 closure; monitoring cron confirms ongoing occurrences | No confirmed fix |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) | P1, diamond lobster | Realtime voice sessions retain unbounded provider/consult state under bursty behavior | No fix PR |
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | P1, diamond lobster | Tool-call interstitial text leaks into messaging channels (Slack, iMessage) | No fix PR |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | P1, diamond lobster | Subagent completion silently lost — no retry, no notification, no auto-restart on timeout | Linked PR open |
| [#121953](https://github.com/openclaw/openclaw/issues/121953) | P1, platinum hermit | Cron agent stalls on DeepSeek; `[cron:` prefix deprioritized at API edge | No fix PR |
| [#86684](https://github.com/openclaw/openclaw/issues/86684) | P1, diamond lobster | `sessions_yield` subagent wake compacts parent branch at low context usage (regression) | Linked PR open |
| [#87109](https://github.com/openclaw/openclaw/issues/87109) | P1, platinum hermit | Gateway heap grows to 1073MB+ at idle; cron jobs fail silently under memory pressure | No fix PR |
| [#95553](https://github.com/openclaw/openclaw/issues/95553) | P1, diamond lobster | Preflight compaction hard-capped at ~60s, ignores `compaction.timeoutSeconds` | No fix PR |
| [#90944](https://github.com/openclaw/openclaw/issues/90944) | P1, silver shellfish | `sessions_yield` resume reply recorded but not delivered; wrong text mirrored to user | Linked PR open |
| [#80498](https://github.com/openclaw/openclaw/issues/80498) | P1, diamond lobster | Subagent completion announcements premature or duplicated after tool-use turns | No fix PR |
| [#92186](https://github.com/openclaw/openclaw/issues/92186) | P1, diamond lobster | Foreground reply fence cancels delivery of completed replies to earlier concurrent group messages | No fix PR |
| [#94939](https://github.com/openclaw/openclaw/issues/94939) | P1, diamond lobster | 6.x state migration leaves channel conversation-store SQLite empty (0 bytes); breaks Bot Framework sends | Linked PR open |
| [#124162](https://github.com/openclaw/openclaw/issues/124162) | P1, silver shellfish | Discord gateway stays "reconnect scheduled" indefinitely on event-loop stall | PR open |
| [#123073](https://github.com/openclaw/openclaw/issues/123073) | P1, diamond lobster | `dev-channel update` fails with `EUNSUPPORTEDPROTOCOL` on `workspace:*` (updater uses npm, repo requires pnpm) | `fix-shape-clear` |
| [#82662](https://github.com/openclaw/openclaw/issues/82662) | P2→P1, diamond lobster | Isolated cron `agentTurn` fails: "setup timed out before runner start"; all fallback models exhausted | `fix-shape-clear` |
| [#85844](https://github.com/openclaw/openclaw/issues/85844) | P1, platinum hermit | Auto-update leaves running gateway with stale hashed bundle imports | No fix PR |
| [#90098](https://github.com/openclaw/openclaw/issues/90098) | P1, diamond lobster | Stack overflow on large Control UI attachments (full data URL materialization) | Linked PR open |
| [#45224](https://github.com/openclaw/openclaw/issues/45224) | P1, silver shellfish | Unhandled Playwright assertion crashes Gateway process | No fix PR |
| [#124334](https://github.com/openclaw/openclaw/issues/124334) | P1, gold shrimp | Idle CPU spike to 100-140% on multi-agent hosts; 1.8-2.7 GB RSS | PR open |

**Notable regressions:**
- [#86684](https://github.com/openclaw/openclaw/issues/86684) — Parent branch compaction during `sessions_yield` (worked before)
- [#94939](https://github.com/openclaw/openclaw/issues/94939) — 6.x migration empties conversation-store SQLite
- [#82662](https://github.com/openclaw/openclaw/issues/82662) — Cron setup timeout regression on 2026.5.12
- [#90711](https://github.com/openclaw/openclaw/issues/90711) — `launchd` plist `StandardErrorPath` hardcoded to `/dev/null` (5.28 regression, hides all stderr)
- [#74378](https://github.com/openclaw/openclaw/issues/74378) — CLI commands remain alive as `node.exe` on Windows (regression)
- [#48810](https://github.com/openclaw/openclaw/issues/48810) — Compaction retry creates orphan fork in `parentId` chain (regression)

## 6. Feature Requests & Roadmap Signals

| Issue | Comments | Summary | Likelihood |
|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 53 | Memory Trust Tagging by Source — tag entries by origin trust level to prevent memory poisoning | Medium — security-focused, aligns with secret egress work |
| [#10687](https://github.com/openclaw/openclaw/issues/10687) | 10 | Fully dynamic model discovery (OpenRouter + beyond) — current catalog is static | High — user demand for model flexibility is strong |
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | 6 | Multi-Slot Memory Architecture — replace single `plugins.slots.memory` with multiple purpose-specific slots | Medium — requires plugin API changes |
| [#45771](https://github.com/openclaw/openclaw/issues/45771) | 7 | Built-in pace-aware rate limiting for autonomous agents | Medium — practical need for API cost control |
| [#88154](https://github.com/openclaw/openclaw/issues/88154) | 8 | Slack Modal Support for Interactive Workflows | Low-Medium — channel-specific enhancement |
| [#13219](https://github.com/openclaw/openclaw/issues/13219) | 8 | Per-model usage logging for cost tracking | Medium — complements the new secret egress security work |
| [#73537](https://github.com/openclaw/openclaw/issues/73537) | 8 | Production-readiness stability label for releases | Medium — community wants clearer versioning signals |
| [#45758](https://github.com/openclaw/openclaw/issues/45758) | 9 | YAML config file support alongside JSON5 | Low — convenience feature |
| [#81061](https://github.com/openclaw/openclaw/issues/81061) | 8 | `before_route_inbound_message` hook for channel bridging/proxying | Medium — architectural gap for power users |
| [#44309](https://github.com/openclaw/openclaw/issues/44309) | 9 | One-way dispatch mode for A2A handoffs | Medium — useful for async agent workflows |
| [#17840](https://github.com/openclaw/openclaw/issues/17840) | 7 | Opt-in reaction-triggered agent turns | Low — niche use case |

**Predicted next-version inclusions:** Dynamic model discovery (#10687) and per-model usage logging (#13219) are the most actionable feature requests and align with the project's direction toward production multi-agent deployments. Memory Trust Tagging (#7707) is thematically consistent with the new secret egress binding work.

## 7. User Feedback Summary

**Pain points (verbatim themes from issues):**
- **Silent failures are the #1 complaint.** Users report subagent results disappearing, cron jobs stalling without notification, and replies being delivered to the dashboard but never reaching WhatsApp/Telegram. The emotional tone in issues like #44925 and #121058 conveys frustration — these are production systems dropping work with no alert.
- **Memory and resource leaks.** Issue #87109 documents a gateway heap growing from 558MB to 1073MB+ at idle, causing cron failures. Issue #114612 reports unbounded SQLite growth in memory tables with no retention policy.
- **Bootstrap and config fragility.** Issue #91931 describes OpenClaw auto-deleting user-provided `BOOTSTRAP.md` before first run when preseeded with SOUL.md/IDENTITY.md. Issue #123073 shows the updater breaking on pnpm workspace protocols.
- **Channel-specific bugs.** Telegram stickers arrive as raw file refs with no description (#120735); Discord gateway goes deaf on event-loop stalls (#124162); WhatsApp group replies are silently cancelled (#92186).
- **Positive feedback.** Issue #73537 includes a detailed testimonial: *"OpenClaw has genuinely become part of our daily workflow"* — used for family/business assistance, Telegram integration, automations, cron jobs, and Home Assistant control.

**Satisfaction drivers:** Multi-agent orchestration, cron automation, and channel bridging are the core value propositions. When these work, users are highly engaged. When they fail silently, trust erodes quickly.

## 8. Backlog Watch

These important issues have been open for extended periods with no confirmed fix PR, requiring maintainer attention:

| Issue | Open Since | Comments | Rating | Blocker |
|---|---|---|---|---|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) — Silent reply failures recurring | 2026-08-09 | 96 | P1, diamond lobster | Monitoring cron confirms post-close recurrence |
| [#116201](https://github.com/openclaw/openclaw/issues/116201) — Realtime voice unbounded state | 2026-07-30 | 66 | P1, diamond lobster | `clawsweeper:needs-product-decision` |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) — Memory Trust Tagging | 2026-02-03 | 53 | P2, off-meta tidepool | `clawsweeper:needs-security-review` |
| [#25592](https://github.com/openclaw/openclaw/issues/25592)

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal AI Assistant Ecosystem
**Date:** 2026-08-16 | **Scope:** 10 Open-Source Projects

---

## 1. Ecosystem Overview

The open-source personal AI agent ecosystem in mid-2026 is characterized by intense hardening activity rather than greenfield feature development. The dominant theme across all active projects is **reliability under production load** — silent message loss, session-state corruption, and resource leaks are the most frequently reported bugs. Security hardening (allowlist bypasses, OAuth flows, SSRF gates) is a secondary but accelerating focus. The ecosystem is consolidating around multi-agent orchestration, cross-channel bridging, and persistent memory as core value propositions, with several projects (OpenClaw, LobsterAI, Hermes Agent) showing deep interdependence through shared upstream dependencies.

---

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | PRs Merged/Closed | Releases | Health Score |
|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 48 | ✅ v2026.8.1-beta.2 | 🟡 Caution — massive backlog, low merge ratio (9.6%) |
| **NanoBot** | 6 | 16 | 7 | ❌ None | 🟢 Strong — balanced bug/feature throughput |
| **Hermes Agent** | 50 | 50 | 10 (closed) | ❌ None | 🟡 Caution — high engagement, Windows/session-state debt |
| **PicoClaw** | 0 | 2 | 0 | ❌ None | 🔴 Weak — stale PRs, no activity |
| **NanoClaw** | 0 | 22 | 3 | ❌ None | 🟡 Caution — high PR velocity but critical bugs unresolved |
| **NullClaw** | 1 | 1 | 0 | ❌ None | 🟢 Stable — low volume, focused maintenance |
| **IronClaw** | ~21 closed | 5+ | 5 | ❌ None | 🟢 Strong — release-stalled but intense optimization sprint |
| **LobsterAI** | 18 | 6 | 2 | ❌ None | 🟡 Caution — backlog hygiene wave, two open pain points |
| **Moltis** | 0 | 16 | 14 | ❌ None | 🟢 Strong — high merge ratio, swift security fixes |
| **CoPaw** | 9 | 10 | 0 | ❌ None | 🟡 Moderate — review bottleneck, v2.1.0 regression wave |
| **ZeroClaw** | 50 | 50 | 6 | ❌ None | 🟡 Caution — design-heavy RFC phase, review backlog |
| **ZeptoClaw** | 0 | 0 | 0 | ❌ None | ⚪ Inactive |

*Health Score rationale: Based on merge ratio, bug resolution velocity, release cadence, and backlog freshness.*

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Unmatched scale and velocity** — 500 issues/PRs updated daily dwarfs all other projects, indicating the largest active user and contributor base.
- **Production-hardening depth** — Secret egress host binding, GPT-5.6 Ultra runtime switching, and multi-agent session management represent the most sophisticated feature set in the ecosystem.
- **Mature channel ecosystem** — Native support for Discord, Telegram, WhatsApp, Slack, iMessage, and browser relay gives it the broadest deployment surface.

**Technical approach differences:**
- OpenClaw follows a **gateway-centric architecture** with shared-store secrets, subagent orchestration, and cron-based autonomous agents — a departure from NanoBot's lighter session model and IronClaw's prepared-context turn system.
- Unlike ZeroClaw's RFC-driven design phase or Moltis's connector-first approach, OpenClaw is shipping operational features directly.

**Community size:** OpenClaw's issue comment counts (96, 66, 53 on top issues) and daily update volume suggest a community **5–10x larger** than the next busiest projects (Hermes Agent, ZeroClaw at ~50 each). NanoBot and Moltis sit in a mid-tier (~6–16 daily updates). PicoClaw, NullClaw, and ZeptoClaw are niche or dormant.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Message delivery reliability** | OpenClaw, NanoClaw, Hermes Agent, CoPaw | Silent reply failures, subagent completion loss, cron stalls, notification races — the #1 cross-project pain point |
| **Session-state correctness** | OpenClaw, Hermes Agent, NanoBot, ZeroClaw | Unbounded state growth, compression handoff bugs, stale history, approval-card indistinguishability |
| **Security hardening** | NanoBot, Moltis, ZeroClaw, OpenClaw | Allowlist bypass (#5305), arbitrary file write via zip (#1180), SSRF gates (#8713), secret egress binding (OpenClaw) |
| **Cross-channel bridging** | OpenClaw, NanoClaw, ZeroClaw, LobsterAI | Telegram integration (NanoClaw pivot), Discord attachment delivery, Matrix E2E, channel-specific edge cases |
| **Memory & persistence** | OpenClaw, LobsterAI, Hermes Agent, Moltis | Cross-session memory tagging (#7707), memory trust by source (#2046), durable connectors (Moltis PR #1190), compressed history handoffs |
| **Model routing & pricing** | OpenClaw, Hermes Agent, NanoBot, ZeroClaw | Dynamic model discovery (#10687), per-model usage logging (#13219), pricing snapshot correctness (#87369), DeepSeek prefix deprioritization (#121953) |
| **Platform-specific regressions** | Hermes Agent, OpenClaw, NanoBot | Windows `.pyd` locks (#83569), SQLite migration emptiness (#94939), cron setup timeouts (#82662), macOS bash 3.2 compat (Moltis) |
| **Multi-agent orchestration** | OpenClaw, NanoClaw, IronClaw, ZeroClaw | Subagent yield/resume reliability, cross-session context fan-out, delegate model overrides, turn-finality preservation |

---

## 5. Differentiation Analysis

| Project | Feature Focus | Target Users | Architecture |
|---|---|---|---|
| **OpenClaw** | Multi-agent orchestration, cron automation, channel bridging, secret egress | Production users, power users, team deployments | Gateway-centric, shared-store, subagent hierarchy |
| **NanoBot** | WebUI collaboration, plugin hardening, DashScope native protocol | Developers, plugin authors, goal-oriented agent users | Session-bound, plugin-driven, OpenAI-compatible API surface |
| **Hermes Agent** | TUI gateway, skill discoverability, pricing correctness, Windows/Linux platform quality | CLI-heavy users, enterprise deployers, multi-platform operators | TUI-first, desktop-gateway hybrid, modular skill system |
| **PicoClaw** | WhatsApp/Telegram channel integration (embedded/IoT focus) | Edge/IoT deployers, embedded systems users | Lightweight, dependency-pinned, channel-adapter model |
| **NanoClaw** | Telegram pivot, channel extensibility hooks, cross-session context | Users migrating from WhatsApp, modular channel needs | Hook-based channel registry, adapter pattern |
| **NullClaw** | Loop hygiene, prompt caching, proxy support | Local/privacy-focused users, restricted-network deployments | Minimal, local-first, proxy-aware |
| **IronClaw** | Database write optimization, prepared-context turns, coding tools, benchmark system | Production-scale operators, cost-sensitive deployments | Reborn runtime, WASM-compiled, database-optimized |
| **LobsterAI** | Memory system, multi-agent framework support (OpenClaw + Hermes), UI polish | Chinese-market users, NetEase ecosystem participants | Frontend/portal layer over OpenClaw upstream |
| **Moltis** | Durable connectors (CalDAV/Gmail/Himalaya), Slack native cards, sandbox tooling | Enterprise integrators, productivity-focused users | Connector-first, provider-neutral persistence, sandboxed execution |
| **CoPaw** | Video analysis, Matrix integration, per-cron model override, DataPaw workspace | Qwen/Alibaba ecosystem users, video-reliant workflows | Provider-agnostic, ACP-protocol, Console WebUI |
| **ZeroClaw** | Chat Completions protocol, RFC-driven architecture, Anthropic refusal handling | Protocol-interoperability seekers, design-phase contributors | RFC-governed, WebSocket/ACP/webhook transport, typed error surfaces |
| **ZeptoClaw** | — | — | Inactive |

**Key architectural divergence:** OpenClaw and its derivative LobsterAI use a **shared-store gateway** model; NanoBot and CoPaw favor **session-isolated, plugin-driven** architectures; IronClaw pursues a **WASM-compiled, database-optimized** runtime; Moltis and ZeroClaw are investing in **protocol standardization** (Chat Completions, ACP); NullClaw and PicoClaw target **lightweight/edge deployment**.

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (500+ daily updates):**
- **OpenClaw**: Highest velocity but lowest merge ratio (9.6%). In a hardening phase with accumulating maintenance debt. Community is large but frustrated by silent failures.

**Tier 2 — Active & Responsive (16–50 daily updates):**
- **Hermes Agent**: Strong contributor engagement, completing large epics (god-file sharding). Platform-specific bugs (Windows) are the primary risk.
- **ZeroClaw**: Design-heavy phase with 50 daily updates but mostly RFC discussion. Six merged PRs today but review bottleneck visible.
- **NanoClaw**: High PR velocity (22 updated, 3 merged) with a coherent architectural push (gavrielc PR series). Critical heartbeat bugs unresolved.
- **Moltis**: Best-in-class merge ratio (14/16 merged). Swift security response. Maturing from beta toward production readiness.
- **IronClaw**: Intense optimization sprint (21 issues closed, 5 PRs merged). Release-stalled but shipping meaningful architectural milestones.
- **NanoBot**: Balanced activity (7 merged, security fix landed). Responsive maintenance with clear feature roadmap.

**Tier 3 — Low/Stalled Activity (0–2 daily updates):**
- **CoPaw**: 19 items but zero merges — review bottleneck. v2.1.0 regression wave suggests release rushed features without adequate stabilization.
- **LobsterAI**: Backlog hygiene wave (16/18 stale closures) masks low substantive activity. Two persistent open issues (login, memory).
- **NullClaw**: Quiet but focused. Proxy support and loop hygiene PRs indicate maturing toward production use.
- **PicoClaw**: Two stale PRs, no maintainer engagement for 9 days. WhatsApp 405 error unaddressed.
- **ZeptoClaw**: Completely inactive.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Reliability over features** | Silent message loss is the #1 complaint in OpenClaw (#121058, 96 comments), NanoClaw (#3251), Hermes Agent (#82001), CoPaw (#6623) | Developers should prioritize delivery guarantees, retry semantics, and observability over novel capabilities. Silent failures erode trust faster than any missing feature. |
| **Security hardening as table stakes** | NanoBot exec bypass (#5305), Moltis zip RCE (#1180), ZeroClaw SSRF (#8713), OpenClaw secret egress binding | Supply-chain and execution-surface security will differentiate production-ready agents. Projects ignoring this risk reputational and operational damage. |
| **Cross-session memory as the next frontier** | LobsterAI (#2046, #2041), OpenClaw (#7707), Hermes Agent (#8457), Moltis (durable connectors) | Persistent, trustworthy memory is the most requested capability across user bases. Projects that solve this accurately will gain a decisive advantage. |
| **Protocol interoperability demand** | ZeroClaw Chat Completions RFC (#8603, 21 comments), NanoBot OpenAI-compatible API, CoPaw ACP protocol | Users want to plug agents into existing toolchains (Open WebUI, Continue, LangChain). Native protocol support reduces friction and expands distribution. |
| **Multi-agent orchestration maturity** | OpenClaw subagent yield (#44925), NanoClaw cross-session fan-out (#3257), IronClaw prepared-context turns (#7634), ZeroClaw delegate overrides (#10021) | The ecosystem is moving from single-agent demos to multi-agent production systems. Correct yield/resume semantics and cross-session context are now expected, not optional. |
| **Platform-specific regressions as trust killers** | Hermes Agent Windows updates (#83569, #83683), OpenClaw SQLite migration (#94939), NanoBot cron timeouts (#82662) | Cross-platform reliability is a competitive differentiator. Users punish inconsistent platform behavior severely, especially when it breaks production cron jobs. |
| **Pricing transparency and cost control** | OpenClaw per-model logging (#13219), Hermes Agent pricing fixes (#87369, #87360, #87365), NanoBot token underestimation (#5402) | As agent usage scales, cost unpredictability becomes a business risk. Per-model, per-task pricing visibility is emerging as a required feature. |
| **Review bottlenecks as the new constraint** | CoPaw (0 merges), OpenClaw (9.6% merge ratio), ZeroClaw (RFC queue stalled) | The limiting factor across the ecosystem is no longer contributor volume but maintainer review throughput. Projects that invest in review automation and clear PR templates will ship faster. |

---

**Summary:** The ecosystem is in a **hardening phase** — the novelty of agent demos has given way to production reliability challenges. OpenClaw leads in scale but carries the heaviest debt. Moltis and IronClaw demonstrate the highest operational discipline. The most actionable opportunities for new entrants or focus areas are **cross-session memory**, **protocol interoperability**, and **silent-failure prevention** — all areas where existing projects show measurable user frustration and incomplete solutions.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-16

## 1. Today's Overview

NanoBot shows **high development velocity** today with 16 PRs touched (7 merged/closed) and 6 issues updated. No new releases were published, but the project is actively addressing critical bugs and security concerns while advancing WebUI and provider features. The most pressing concern is a **security advisory** (exec allowlist bypass) and a **P0 race-condition fix** that landed today. Overall project health is strong with balanced activity across bug fixes, features, and infrastructure improvements.

## 2. Releases

No new releases published in the last 24 hours.

## 3. Project Progress — Merged/Closed PRs Today

| PR | Title | Impact |
|----|-------|--------|
| [#5328](https://github.com/HKUDS/nanobot/pull/5328) | OrcaRouter as a named gateway provider | New provider support (150+ models via single endpoint) |
| [#5371](https://github.com/HKUDS/nanobot/pull/5371) | Hide assistant actions until turn end | Fixes WebUI race condition on copy/fork during active turns |
| [#5369](https://github.com/HKUDS/nanobot/pull/5369) | Revalidate cached skill roots after package changes | Fixes stale plugin cache after in-place replacement |
| [#5370](https://github.com/HKUDS/nanobot/pull/5370) | Bound per-session file state lifecycle | Prevents unbounded memory growth from high-cardinality sessions |
| [#5376](https://github.com/HKUDS/nanobot/pull/5376) | Keep scheduler alive when job-store persistence fails | Fixes silent cron scheduler death on disk/permission errors |
| [#5399](https://github.com/HKUDS/nanobot/pull/5399) | Clarify model preset display names | UX fix: distinguishes display label from stable command name |
| [#5397](https://github.com/HKUDS/nanobot/pull/5397) | Preserve range selection and turn timing | macOS-style Shift selection + turn identity during guidance |

**Key advances:** Plugin system hardening (#5369), memory leak prevention (#5370), cron resilience (#5376), and two WebUI UX improvements (#5371, #5397).

## 4. Community Hot Topics

- **[Issue #4864](https://github.com/HKUDS/nanobot/issues/4864)** — *Endless loop for `complete_goal`* · 5 comments · 1 👍 · Open since 2026-07-09
  - The gateway parsing `recap` parameter as a bare string instead of JSON is causing an infinite retry loop. This is a **high-impact bug** affecting goal-oriented agent workflows. The 5-comment activity and 1-week open span suggest community frustration.
- **[Issue #4467](https://github.com/HKUDS/nanobot/issues/4467)** — *Dream should update existing workspace skills instead of creating duplicates* · 2 comments · 1 👍 · Open since 2026-06-23
  - Long-standing usability gap: users maintain custom skills but Dream treats each run as a new session, cluttering `skills/`. Reflects a need for **incremental skill evolution** rather than append-only behavior.
- **[Issue #5305](https://github.com/HKUDS/nanobot/issues/5305)** — *Security: `exec.allowPatterns` allowlist bypass via chained shell commands* · Open since 2026-08-09
  - Critical: an API user can execute shell segments outside the allowlist via command chaining. No fix PR yet — **needs urgent maintainer attention**.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| **🔴 Critical (Security)** | [#5305](https://github.com/HKUDS/nanobot/issues/5305) | `exec.allowPatterns` allowlist bypass enables chained shell execution via OpenAI-compatible API | No fix PR yet |
| **🟠 High** | [#5377](https://github.com/HKUDS/nanobot/issues/5377) | Consolidation truncates archive input but advances past full message batch, causing data loss | Fix PR [#5379](https://github.com/HKUDS/nanobot/pull/5379) **open** |
| **🟠 High** | [#4864](https://github.com/HKUDS/nanobot/issues/4864) | Endless loop in `complete_goal` due to gateway JSON serialization regression | No fix PR yet |
| **🟡 Medium** | [#5402](https://github.com/HKUDS/nanobot/issues/5402) | Token consolidation never triggers — tiktoken consistently underestimates actual API token count | Opened today, no fix PR yet |
| **🟡 Medium** | [#5368](https://github.com/HKUDS/nanobot/issues/5368) | WebUI shows copy/fork actions mid-turn, conflicting with active agent state | **Fixed** in [#5371](https://github.com/HKUDS/nanobot/pull/5371) ✅ |
| **🟡 Medium** | [#5364](https://github.com/HKUDS/nanobot/issues/5364) — *side conversations* | Not a bug but an open feature PR; no conflicts noted beyond label | Fix PR [#5364](https://github.com/HKUDS/nanobot/pull/5364) **open** |

**Stability assessment:** Three open bugs (including one security advisory) lack fix PRs. The consolidation data-loss bug (#5377) and its fix (#5379) are a priority pair — the fix introduces lossless bounded chunks and deferred writes but is still awaiting review.

## 6. Feature Requests & Roadmap Signals

| PR | Feature | Status |
|----|---------|--------|
| [#5358](https://github.com/HKUDS/nanobot/pull/5358) | **Session collaboration via mentions** — stable `@name` identities, peer session picker with color coding | Open |
| [#5291](https://github.com/HKUDS/nanobot/pull/5291) | **Persist subagent conversation transcripts** — tool calls, results, reasoning survive after subagent process ends | Open |
| [#5400](https://github.com/HKUDS/nanobot/pull/5400) | **Unify model preset names** — single canonical name across config, WebUI, commands, sessions, Dream, and snapshots | Open |
| [#5398](https://github.com/HKUDS/nanobot/pull/5398) | **DashScope native protocol** — full parameter surface including native thinking mode alongside existing OpenAI-compatible provider | Open |
| [#5364](https://github.com/HKUDS/nanobot/pull/5364) | **Temporary side conversations** (`/side` command) — isolated parallel chats with tab switching, auto-cleanup | Open |
| [#5389](https://github.com/HKUDS/nanobot/pull/5389) | **Drag-and-drop session organization** — reorder sessions/groups in sidebar, create groups by dropping | Open |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) | **P0: Prevent stale background task saves** — serialize `/new` with per-session compaction, reject invalidated saves | Open |

**Roadmap prediction:** The next release will likely include the **WebUI collaboration features** (#5358, #5364, #5389) and **DashScope native support** (#5398), as these are self-contained feature additions. The P0 session-safety fix (#5271) should also ship given its severity. The subagent transcript persistence (#5291) and preset unification (#5400) may carry over if review is slow.

## 7. User Feedback Summary

- **Frustration with Dream skill duplication** (#4467): Users want skills to evolve incrementally, not spawn duplicates each run. This suggests a need for skill-versioning or update-mode in the Dream workflow.
- **Gateway regression breaking goal completion** (#4864): The `complete_goal` endless loop indicates a serialization change in the gateway that broke existing tool contracts. Users relying on goal-oriented agents are directly impacted.
- **Security awareness growing**: The #5305 advisory was reported by a security-minded community member (YLChen-007), reflecting a user base that exercises and audits agent capabilities.
- **Token estimation accuracy matters** (#5402): Underestimation causes consolidation to never trigger, forcing longer contexts and higher costs. Users are noticing the disconnect between estimated and actual token counts.
- **WebUI polish requests**: Range selection (#5397), side conversations (#5364), and drag-and-drop organization (#5389) show users want a more mature, collaborative interface experience.

## 8. Backlog Watch

| Issue/PR | Age | Risk | Notes |
|----------|-----|------|-------|
| [#4467](https://github.com/HKUDS/nanobot/issues/4467) — Dream skill dedup | ~2 months | Medium | Long-open enhancement; no maintainer response. Indicates slow triage on feature requests. |
| [#4864](https://github.com/HKUDS/nanobot/issues/4864) — `complete_goal` endless loop | ~1 month | **High** | No fix PR. Active users hit this daily. Gateway regression requires investigation. |
| [#5305](https://github.com/HKUDS/nanobot/issues/5305) — exec allowlist bypass | ~1 week | **Critical** | Security vulnerability with no fix PR. Should be top priority for maintainers. |
| [#5402](https://github.com/HKUDS/nanobot/issues/5402) — Token consolidation underestimation | Opened today | Medium | New issue; may need a tiktoken provider-specific fix or fallback to actual API-reported counts. |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) — Stale background task saves (P0) | ~10 days | **High** | Labeled P0 but still open with conflicts. Needs maintainer review to land before next release. |
| [#5379](https://github.com/HKUDS/nanobot/pull/5379) — Preserve full consolidation input | ~3 days | High | Fix for #5377; lossless consolidation is a significant refactor that needs careful review. |

**Maintainer attention needed:** The security advisory (#5305) and the P0 session-safety fix (#5271) are the two most time-sensitive items. The `complete_goal` loop (#4864) also warrants investigation as it affects core agent functionality and has no fix in flight.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-16

## 1. Today's Overview

Hermes Agent is in a high-velocity development phase on 2026-08-16, with **50 issues and 50 PRs** updated in the last 24 hours and **no new releases** published. The project is simultaneously addressing critical Windows update regressions, hardening security boundaries around command approval and OAuth flows, and advancing core session/memory architecture. Activity is heavily concentrated around the TUI gateway, session state management, and provider pricing correctness — indicating a maturing codebase that is now deep in reliability and platform-quality work. Community engagement is strong, with several issues drawing 30+ comments.

## 2. Releases

**No new releases today.** The latest relevant version context is v0.20.1, which is the source of several open bugs (Windows `.pyd` lock on update, OAuth callback port collision, SQLite 3.53.4 FTS5 compatibility). The next release is likely to focus on stabilizing these v0.20.x regressions before any major feature landing.

## 3. Project Progress

**Merged / closed today:**

- **#78647** [CLOSED] Large-file decomposition epic completed — 20/20 god-file sharding tasks finished, enforcing the standing policy that all god-files are now modular and never reverted.
- **#83683** [CLOSED] Windows desktop gateway restart regression acknowledged and tracked.
- **#82001** [CLOSED] Agent flush / session compression handoff bug identified — the `session_persistence_failed` error was misattributed to "full disk" when the real cause was a session-identity handoff gap.
- **#50530** [CLOSED] google-antigravity (Gemini via Code Assist) legacy P2 issues tracked.
- **#83569** [CLOSED] Windows `cryptography._rust.pyd` self-lock bug during `hermes update` — the updater process holding the mapped `.pyd` was confirmed and analyzed.
- **#69107** [CLOSED] TUI stale-in-memory-history ordinal rejection bug.
- **#67165** [CLOSED] macOS ScreenCaptureKit `display_count=0` with TCC permissions OK.
- **#81333** [CLOSED] `computer_use` discarding `app=` on placeholder `pid=0` / `window_id=0`.
- **#32962** [CLOSED] WSL2 child PID tracking + MCP subprocess resilience (salvaged).

**PRs advanced today (open, active):**

- **#87372** TUI gateway auto-continue for interrupted turns.
- **#87370** Computer-use wrong-window input rejection + near-miss hints.
- **#87371** Session mirroring announcement + turn-origin stamping on the wire.
- **#87369** Pricing: strip date suffixes when resolving snapshot model IDs.
- **#87367** MCP WSL2 fallback to `ps --ppid`.
- **#87360** Resolve Z.AI Coding Plan and Ollama Cloud as `subscription_included` in pricing.
- **#87361** Linear webhook HMAC-SHA256 signature validation.
- **#87362** Widen pipe-to-remote-shell detection in approval guard.
- **#87363** Bound local image reads to 50 MiB ingest cap.
- **#87365** Add GPT-5.4 family pricing entries.
- **#87366** Per-task model/provider override in `delegate_task` batch mode.
- **#87145** Signed short-lived download tickets for external viewers behind gated dashboards.
- **#86940** Skill discoverability — ghost suggestions, hover descriptions, enable toggle in Desktop and CLI.

## 4. Community Hot Topics

| Issue | Comments | Key Theme |
|---|---|---|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) | 79 | God-file sharding epic — completed; reflects a community demand for architectural cleanliness. |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 37 | Skills index staleness — automated probe shows degraded freshness (29.8h vs 26h limit). |
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | 33 | Windows desktop gateway restart kills live gateway — regression causing WeChat/QQ/Telegram silence. |
| [#8457](https://github.com/NousResearch/hermes-agent/issues/8457) | 21 | Persistent cross-session memory with auto-compression — long-standing feature request. |
| [#82001](https://github.com/NousResearch/hermes-agent/issues/82001) | 19 | Agent flush misreports session-compression failure as "full disk." |
| [#58619](https://github.com/NousResearch/hermes-agent/issues/58619) | 11 | Unbounded `serve` process accumulation on Desktop reconnection. |
| [#51327](https://github.com/NousResearch/hermes-agent/issues/51327) | 9 | Linux `.desktop` silent failure when Electron chrome-sandbox lacks setuid. |

**Analysis:** The most-discussed topics center on **platform reliability** (Windows update locks, Linux desktop crashes, macOS screen capture) and **session-state correctness** (compression handoffs, stale history, unbounded processes). The persistent-session-memory feature request (#8457) has been open since April with 21 comments, indicating strong user demand that has not yet been addressed with a PR.

## 5. Bugs & Stability

### P1 (High Severity)

| Issue | Summary | Fix PR? |
|---|---|---|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | Windows desktop restart reaps live gateway without relaunch — WeChat/QQ/Telegram go silent. | Acknowledged; no linked fix PR yet. |
| [#83569](https://github.com/NousResearch/hermes-agent/issues/83569) | `hermes update` on Windows fails 100% when `cryptography` bumps — process holds `.pyd` lock. | #77394 notes the prior fix (#73684) does not cover respawned gateways; active investigation. |
| [#51327](https://github.com/NousResearch/hermes-agent/issues/51327) | Linux `.desktop` launcher fails silently without setuid `chrome-sandbox`. | No linked fix PR. |

### P2 (Medium-High Severity)

| Issue | Summary | Fix PR? |
|---|---|---|
| [#86027](https://github.com/NousResearch/hermes-agent/issues/86027) | Legacy FTS5 trigram index malformed by SQLite 3.53.4 during v0.18.2 → v0.20.1 upgrade. | No linked fix PR. |
| [#81048](https://github.com/NousResearch/hermes-agent/issues/81048) | Approval timeout misattributed as explicit user denial — security-critical. | No linked fix PR. |
| [#87329](https://github.com/NousResearch/hermes-agent/issues/87329) | OAuth callback port collision makes `hermes mcp login` impossible on headless hosts (regression of #5344). | No linked fix PR. |
| [#83379](https://github.com/NousResearch/hermes-agent/issues/83379) | Some models write fake tool invocations as prose instead of real `tool_calls`. | No linked fix PR. |
| [#70694](https://github.com/NousResearch/hermes-agent/issues/70694) | Gateway drops semantic turn finality at platform-adapter boundary. | No linked fix PR. |
| [#77394](https://github.com/NousResearch/hermes-agent/issues/77394) | Windows `hermes update` still fails on main — paused gateway keeps `.pyd` locked. | Related to #83569. |
| [#49543](https://github.com/NousResearch/hermes-agent/issues/49543) | OAuth MCP servers drop mid-session (`RuntimeError` + 120s hangs). | No linked fix PR. |
| [#87295](https://github.com/NousResearch/hermes-agent/issues/87295) | Second Desktop launch silently kills running backend, breaking connection status. | No linked fix PR. |
| [#87292](https://github.com/NousResearch/hermes-agent/issues/87292) | Timeouts with slow local models (>16 TPS) — WinError 10053 / provider unresponsive. | No linked fix PR. |
| [#85315](https://github.com/NousResearch/hermes-agent/issues/85315) | `auxiliary.free_only` gate rejects explicitly-requested `:free` models and misreports error type. | No linked fix PR. |

### P3 (Medium Severity)

| Issue | Summary | Fix PR? |
|---|---|---|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Skills index stale (29.8h old, limit 26h). | Cron workflow fix needed. |
| [#80439](https://github.com/NousResearch/hermes-agent/issues/80439) | Auto-generated `.desktop` uses wrong `Exec` path, breaking KDE taskbar pinning. | No linked fix PR. |
| [#87356](https://github.com/NousResearch/hermes-agent/issues/87356) | `cronjob update` schema omits `model`/`provider` — drift-guard remediation unreachable. | No linked fix PR. |
| [#66746](https://github.com/NousResearch/hermes-agent/issues/66746) | Telegram rich messages parse bare `$` as LaTeX, garbling financial figures. | No linked fix PR. |

**Overall stability assessment:** The project has a significant concentration of **Windows-specific regressions** (update locks, gateway restarts) and **session-state bugs** that are P1/P2. These suggest the v0.20.x release line needs a stabilization patch before the next major version. Security-adjacent bugs (approval misattribution, OAuth port collision, unbounded process spawn) are particularly concerning for production deployments.

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Status |
|---|---|---|
| Persistent cross-session memory with search & auto-compression | [#8457](https://github.com/NousResearch/hermes-agent/issues/8457) | Open since April; no PR yet. |
| Auto reasoning mode (ChatGPT-style dynamic `reasoning_effort`) | [#40306](https://github.com/NousResearch/hermes-agent/issues/40306) | Open; low comment count but clearly requested. |
| Discord API v10 feature parity campaign | [#79564](https://github.com/NousResearch/hermes-agent/issues/79564) | Active campaign; in-progress. |
| Lean tail compaction mode (+22.5pt recall at 0.30x tokens) | [#87326](https://github.com/NousResearch/hermes-agent/pull/87326) | PR open; strong eval-backed proposal. |
| Per-task model/provider override in batch delegation | [#87366](https://github.com/NousResearch/hermes-agent/pull/87366) | PR open; enables cost-aware multi-model batches. |
| Skill discoverability (ghost suggestions, hover, toggle) | [#86940](https://github.com/NousResearch/hermes-agent/pull/86940) | PR open; improves onboarding. |
| Signed download tickets for external viewers | [#87145](https://github.com/NousResearch/hermes-agent/pull/87145) | PR open; enables secure external file access. |
| Kanban zero-authority workers + durable publication | [#82591](https://github.com/NousResearch/hermes-agent/issues/82591) | Tracker issue; implementation plan posted. |
| Child-process credential-inheritance closure | [#83565](https://github.com/NousResearch/hermes-agent/issues/83565) | Epic tracker; security-hardening campaign. |

**Prediction for next release:** The next version will likely land **lean compaction mode** (#87326), **per-task model override** (#87366), and **skill discoverability** (#86940) as feature additions, alongside **pricing fixes** (#87369, #87360, #87365) and **security hardening** (#87362, #87363, #76063). The persistent-session-memory feature (#8457) is unlikely to ship in the immediate next release given its open status since April with no PR.

## 7. User Feedback Summary

**Pain points:**
- **Windows update process is broken** when `cryptography` is involved — users cannot self-update without manual intervention (#83569, #77394).
- **Desktop gateway dies on restart** — messaging integrations (WeChat, QQ, Telegram) go silent and require manual restart (#83683).
- **Session state is fragile under compression** — users see misleading "full disk" errors when the real issue is a handoff gap (#82001).
- **OAuth login is broken on headless hosts** — port collision makes `hermes mcp login` impossible (#87329).
- **Skills index is stale** — the automated freshness probe reports degradation, suggesting CI pipeline issues (#66616).
- **Linux desktop launcher fails silently** — missing setuid on `chrome-sandbox` causes immediate abort with no error dialog (#51327).
- **Approval timeouts are misattributed** — a security-critical bug where silent timeouts surface as "user denied" (#81048).
- **Slow local models hit timeouts** — models under ~16 TPS trigger WinError 10053 or "provider unresponsive" (#87292).

**Satisfaction signals:**
- The god-file sharding epic was completed with community collaboration (79 comments, fully closed).
- The TUI gateway session-mirroring work (#86784, #87371, #87372) addresses a long-standing multi-client pain point.
- Pricing correctness fixes (#87360, #87365, #87369) respond to a fleet audit, showing the team is acting on data-driven findings.

## 8. Backlog Watch

| Issue | Open Since | Why It Needs Attention |
|---|---|---|
| [#8457](https://github.com/NousResearch/hermes-agent/issues/8457) | Apr 2026 | Persistent cross-session memory is a high-demand feature with no PR; 21 comments indicate strong user interest. |
| [#81048](https://github.com/NousResearch/hermes-agent/issues/81048) | Aug 2026 | Security-critical: approval timeouts misattributed as denials. No fix PR yet. |
| [#86027](https://github.com/NousResearch/hermes-agent/issues/86027) | Aug 2026 | SQLite 3.53.4 FTS5 compatibility break during upgrade — affects any user on newer SQLite. No fix PR. |
| [#49543](https://github.com/NousResearch/hermes-agent/issues/49543) | Jun 2026 | OAuth MCP servers dropping mid-session with `RuntimeError` — impacts long-running gateway users. No fix PR. |
| [#70694](https://github.com/NousResearch/hermes-agent/issues/70694) | Jul 2026 | Gateway drops turn finality at platform boundary — affects all platform integrations. No fix PR. |
| [#58619](https://github.com/NousResearch/hermes-agent/issues/58619) | Jul 2026 | Unbounded `serve` process accumulation on reconnect — resource leak under API errors. No fix PR. |
| [#51327](https://github.com/NousResearch/hermes-agent/issues/51327) | Jun 2026 | Linux desktop silent failure — UX and onboarding blocker. No fix PR. |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | Jul 2026 | Skills index degradation — CI/cron pipeline issue, affects documentation accuracy. No fix PR. |

**Overall project health:** Hermes Agent shows **active development with strong community engagement** but carries a **growing backlog of platform-specific and session-state bugs** that risk user trust if not addressed promptly. The Windows update and desktop-restart regressions are the most urgent stability concerns. The team is making progress on security hardening and pricing correctness, which are positive signals. The absence of a release in the face of 50 open issues updated today suggests the team is prioritizing stabilization over shipping.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-16

---

## 1. Today's Overview

PicoClaw activity is currently low, with no new issues, merged PRs, or releases reported in the last 24 hours. Two open pull requests remain active but are both flagged as **stale**, indicating they have not received maintainer review for some time. The project appears to be in a quiet maintenance phase, with no new versions deployed and no open bug reports surfaced today.

---

## 2. Releases

**No new releases** were published. The project has not shipped a new version since the last release.

---

## 3. Project Progress

**No PRs were merged or closed today.** The two open PRs (#3320 and #3321) remain in review and have not advanced to merge:

- **[PR #3320](https://github.com/sipeed/picoclaw/pull/3320)** — Updates the `whatsmeow` dependency to resolve a WhatsApp API rejection (`Client outdated 405`). This is a **critical fix** for the WhatsApp channel but remains unreviewed.
- **[PR #3321](https://github.com/sipeed/picoclaw/pull/3321)** — Restructures the system prompt to move the dynamic context block (time, runtime, session metadata) **after** conversation history, preserving prefix caching. This is a **performance optimization** with no breaking changes.

Both PRs were created on 2026-08-07 and last updated on 2026-08-15, with no maintainer engagement since.

---

## 4. Community Hot Topics

No issues or PRs attracted comments or reactions today. The two most prominent open PRs — **#3320** (WhatsApp fix) and **#3321** (prefix caching fix) — both show **0 reactions** and remain stale.

**Underlying signal:** The WhatsApp `405 Client Outdated` error (PR #3320) likely affects a noticeable subset of users relying on the native WhatsApp channel. The prefix-caching regression (PR #3321) suggests ongoing work to optimize LLM request efficiency. Neither has drawn community discussion, pointing to low daily engagement or a small active user base.

---

## 5. Bugs & Stability

**No new bugs or regressions reported today.**

However, one **known, open bug** persists and has a fix PR awaiting review:

| Severity | Issue | Fix PR |
|----------|-------|--------|
| 🔴 **High** | WhatsApp channel drops connections with `Client outdated (405)` error; no auto-reconnect | [#3320](https://github.com/sipeed/picoclaw/pull/3320) |

This is the most impactful outstanding issue. Users on the WhatsApp channel are likely experiencing persistent disconnections with no resolution in sight.

---

## 6. Feature Requests & Roadmap Signals

No new feature requests were filed today. No roadmap signals emerged from the current PR/issue activity.

**Inferred from open PRs:**
- **Prefix caching support** — PR #3321 indicates the team is prioritizing LLM inference efficiency, likely aligning with infrastructure that supports KV-cache-based prefix matching (e.g., vLLM, TGI).
- **Dependency freshness** — PR #3320 shows a need for more frequent dependency pinning audits, particularly for messaging backends that enforce version checks.

---

## 7. User Feedback Summary

No new user feedback was captured today. Based on the open PRs, the current user pain points are:

1. **WhatsApp channel instability** — Users are frustrated by the `405 Client Outdated` error and lack of reconnect logic. This is a **high-severity, high-impact** issue for anyone using WhatsApp as an agent channel.
2. **Performance/caching regressions** — The prefix-caching fix in PR #3321 suggests users (or the maintainers) have noticed degraded response times or unnecessary recomputation when dynamic context is placed before history.

Overall satisfaction appears **neutral-to-concerning** on the WhatsApp front, with no visible user complaints in the issue tracker — possibly due to low reporting volume rather than user contentment.

---

## 8. Backlog Watch

Two **stale PRs** require maintainer attention:

| PR | Title | Age | Status |
|----|-------|-----|--------|
| [#3320](https://github.com/sipeed/picoclaw/pull/3320) | `fix(deps): bump whatsmeow to unblock WhatsApp "client outdated (405)"` | 9 days | 🟡 Stale — critical bug fix pending review |
| [#3321](https://github.com/sipeed/picoclaw/pull/3321) | `fix(agent): move dynamic context after history to preserve prefix caching` | 9 days | 🟡 Stale — performance fix pending review |

Both PRs were created on **2026-08-07** and last updated on **2026-08-15**. Neither has received a review comment, and both carry the `stale` label. **PR #3320 is the higher priority** given its direct impact on a live messaging channel.

---

**Project Health Assessment:** 🟡 **Caution** — The project is in a low-activity period with two important fixes blocked in review. The WhatsApp bug (PR #3320) is a blocker for a subset of users and deserves urgent maintainer attention. No releases or new feature work are visible.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-16

## 1. Today's Overview

NanoClaw is experiencing a **high-velocity development sprint**, with 22 PRs updated in the last 24 hours and 3 merged/closed — despite zero issues opened or closed. The project is in an active integration and hardening phase: core channel infrastructure (Telegram support, delivery hooks, cross-session context) is being expanded, while critical stability bugs (heartbeat stalls, poll-loop leaks, attachment delivery) are being simultaneously patched. No new releases were published today, suggesting the team is accumulating changes before a larger merge window.

## 2. Releases

No new releases today. The last significant rename (PR #37, closed today) shifted the project identity from *nanoclaw* to *dotclaw* and replaced WhatsApp with Telegram — but no version tag was shipped with it.

## 3. Project Progress

**Merged / Closed today (3 PRs):**

- **[#37] Rename to DotClaw and switch from WhatsApp to Telegram** — Closed. Full codebase rename, WhatsApp removal, Telegram bot integration via Telegraf. Marks a major platform pivot.
  → [PR #37](https://github.com/nanocoai/nanoclaw/pull/37)

- **[#3268] fix(poll-loop): stopped loops leaked their active query's follow-up poller** — Closed. Fixes a resource leak where aborted poll loops left 500ms follow-up pollers running inside abandoned queries.
  → [PR #3268](https://github.com/nanocoai/nanoclaw/pull/3268)

- **One additional closed PR** (counted in the 3 merged/closed total per the data).

**Key open PRs advancing features:**

- **[#3269] feat(channels): add Telegram channel integration** — New `@chat-adapter/telegram` adapter with pairing flow and Markdown sanitizer. 1483 tests pass; build clean.
  → [PR #3269](https://github.com/nanocoai/nanoclaw/pull/3269)

- **[#3257] Cross-session context: fan-out, DM backfill, echo pruning** — Agent groups can now share context across concurrent sessions via trigger=0 "session-echo" rows.
  → [PR #3257](https://github.com/nanocoai/nanoclaw/pull/3257)

- **[#3260] permissions: 'decline_notify' unknown-sender policy** — Fourth DM policy option: polite decline + one-line owner FYI, no approval card interrupt.
  → [PR #3260](https://github.com/nanocoai/nanoclaw/pull/3260)

- **[#3263–#3266]** Series of channel registry and permissions hooks (hot-start adapter, delivery batch preview, registration interceptor, agent creation options) — all from gavrielc, forming a coherent extensibility layer.
  → [PR #3263](https://github.com/nanocoai/nanoclaw/pull/3263) · [PR #3264](https://github.com/nanocoai/nanoclaw/pull/3264) · [PR #3265](https://github.com/nanocoai/nanoclaw/pull/3265) · [PR #3266](https://github.com/nanocoai/nanoclaw/pull/3266)

## 4. Community Hot Topics

**Most discussed / impactful open PRs:**

| PR | Topic | Why it matters |
|---|---|---|
| [#3269](https://github.com/nanocoai/nanoclaw/pull/3269) | Telegram channel integration | Primary community request; replaces deprecated WhatsApp |
| [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) | Fix: stage inbound Discord attachments | Long-open (since June) bug — attachments arrive as bare `[file: ...]` with no bytes |
| [#3251](https://github.com/nanocoai/nanoclaw/pull/3251) | Fix: heartbeat stall during rate-limiting | Critical — false stale-container kills during API throttling (30+ min stall) |
| [#3254](https://github.com/nanocoai/nanoclaw/pull/3254) | Two-phase inbound batch selection | Context rows could crowd out actual task rows, causing missed turns |
| [#37](https://github.com/nanocoai/nanoclaw/pull/37) | Project rename to DotClaw | Major identity/platform shift, now closed |

**Underlying need:** The community is pushing hard on **platform reliability** (heartbeat, delivery, poll loops) and **multi-platform coverage** (Telegram, Discord attachments). The gavrielc PR wave signals a deliberate architectural push toward modular, hook-based channel extensibility.

## 5. Bugs & Stability

| Severity | Bug | PR |
|---|---|---|
| **Critical** | Heartbeat stalls 30+ min during Claude API rate-limiting, triggering false stale-container kills | [#3251](https://github.com/nanocoai/nanoclaw/pull/3251) (open) |
| **Critical** | Idle containers with no `.heartbeat` file bypass absolute-ceiling kill entirely — may leak forever | [#3252](https://github.com/nanocoai/nanoclaw/pull/3252) (open) |
| **High** | Stopped poll loops leak active query follow-up pollers (resource leak) | [#3268](https://github.com/nanocoai/nanoclaw/pull/3268) ✅ **merged** |
| **High** | Inbound Discord attachments never reach agent in readable form (bare file refs) | [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) (open since Jun 12) |
| **High** | Outbound delivery resolves wrong channel row when multiple instances share same platform address | [#3255](https://github.com/nanocoai/nanoclaw/pull/3255) (open) |
| **Medium** | Legacy Markdown sanitizer downgrades `**bold**` to *italic* in Telegram output | [#3250](https://github.com/nanocoai/nanoclaw/pull/3250) (open) |
| **Medium** | Context rows can push task rows out of the inbound batch cap, causing missed agent turns | [#3254](https://github.com/nanocoai/nanoclaw/pull/3254) (open) |
| **Low** | `skill-apply` heading ordinals render wrong step numbers across skipped steps | [#3259](https://github.com/nanocoai/nanoclaw/pull/3259) (open) |

**Note:** Two critical heartbeat-related bugs remain open. The poll-loop leak is the only bug fixed today.

## 6. Feature Requests & Roadmap Signals

**Active feature PRs likely heading to next release:**

- **Telegram adapter** ([#3269](https://github.com/nanocoai/nanoclaw/pull/3269)) — Test-passed, build-clean; high confidence for next release.
- **`decline_notify` unknown-sender policy** ([#3260](https://github.com/nanocoai/nanoclaw/pull/3260)) — New permission mode; complements existing `strict` and `request_approval`.
- **Cross-session context fan-out** ([#3257](https://github.com/nanocoai/nanoclaw/pull/3257)) — Agent-group multi-session awareness.
- **Optional adapter capabilities** (`setTyping`, `setThreadTitle`, `setSuggestedPrompts`) ([#3261](https://github.com/nanocoai/nanoclaw/pull/3261)) — Rich presence and thread management.
- **`messaging_groups.detached_at`** ([#3256](https://github.com/nanocoai/nanoclaw/pull/3256)) — Tracks when bot is removed from a platform conversation; delivery refused into detached chats.
- **Hot-start registered adapters** ([#3263](https://github.com/nanocoai/nanoclaw/pull/3263)) — Runtime adapter registration without full restart.

**Predicted next-release candidates:** Telegram integration, `decline_notify` policy, and the channel extensibility hooks (3261–3266 series) are the most complete and coherent feature set today.

## 7. User Feedback Summary

- **Pain point — Discord attachments unusable:** [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) has been open since June 12. Users report seeing only `[file: message.txt]` / `[image: foo.png]` with no actual content — a fundamental breaking issue for media-driven workflows.
- **Pain point — False container kills during rate limits:** [#3251](https://github.com/nanocoai/nanoclaw/pull/3251) addresses a critical operational issue where rate-limited API calls cause heartbeat stalls and the host sweep kills healthy containers.
- **Satisfaction signal — Test coverage:** PR #3269 reports 1483 tests passing and a clean TypeScript build, indicating healthy regression coverage.
- **Satisfaction signal — Structured extensibility:** The gavrielc PR series (3261–3266) shows the team is responding to community needs for modular, hook-based customization rather than monolithic channel code.

## 8. Backlog Watch

| PR | Age | Concern |
|---|---|---|
| [#2752](https://github.com/nanocoai/nanoclaw/pull/3252) | ~65 days (open since Jun 12) | Discord inbound attachments broken — critical for any media-dependent use case |
| [#3250](https://github.com/nanocoai/nanoclaw/pull/3250) | 1 day | Legacy Markdown sanitizer downgrades bold→italic; blocks clean Telegram rollout |
| [#3253](https://github.com/nanocoai/nanoclaw/pull/3253) | 1 day | Group reasoning effort not honored in model config — `opencode` skill mismatch |
| [#3255](https://github.com/nanocoai/nanoclaw/pull/3255) | 1 day | Multi-instance channel resolution picks arbitrary row — affects rooms with multiple bot identities |

**Recommendation:** PRs #2752 (Discord attachments) and #3250 (Telegram Markdown sanitizer) should be prioritized — the former is a long-backlogged critical bug, and the latter directly blocks the Telegram integration in #3269 from shipping with correct formatting.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-16

## 1. Today's Overview

NullClaw registered low but steady activity on 2026-08-16, with one open issue and one open pull request updated in the last 24 hours. No new releases were published, and no PRs were merged or issues closed during the window, suggesting a maintenance lull rather than a stalled project. Development momentum appears centered on internal agent hygiene improvements (PR #987) and network-layer feature requests (Issue #988), both indicative of a project maturing its reliability and deployment flexibility. Overall health is stable — activity is lightweight but focused on meaningful infrastructure work.

## 2. Releases

No new releases today. The project has no recent version bumps in this reporting window.

## 3. Project Progress

**PR #987 — feat(agent): loop hygiene for long local tool-heavy runs** ([Link](https://github.com/nullclaw/nullclaw/pull/987))

This open PR introduces several internal optimizations aimed at stability during extended, tool-heavy agent loops:

- **System prompt splitting** into a cache-friendly stable prefix and a variable datetime tail, with a `stablePrefixHash` mechanism to reduce redundant context re-processing.
- **Tool output compression** before history injection via `result_compress.zig`, while preserving full-output visibility in observer logs.
- **Per-turn identical-call deduplication** (summary cut off, but intent is clear — preventing redundant tool invocations in loops).

While not yet merged, this PR signals active investment in making NullClaw more robust for long-running local agent workflows — a critical gap many open-source agent projects face.

## 4. Community Hot Topics

- **Issue #988 — proxy support** ([Link](https://github.com/nullclaw/nullclaw/issues/988)) — Opened 2026-08-15 by `anpic`. Requests HTTP(s) and SOCKS(5h) proxy support for LLM providers. Zero comments and zero reactions so far, but the feature request is notable: proxy support is increasingly important for users operating in restricted network environments, corporate firewalls, or privacy-conscious workflows. Its absence is a common pain point across AI agent frameworks.

- **PR #987 — loop hygiene** ([Link](https://github.com/nullclaw/nullclaw/pull/987)) — Opened 2026-08-15 by `vernonstinebaker`. Addresses performance and stability concerns for local, tool-intensive agent runs. No comments yet. This reflects a community need for reliability at scale — users running complex local agents are hitting edge cases around prompt bloat and redundant computation.

**Underlying needs:** Both items point toward a project transitioning from "works for simple demos" to "works reliably in production-like scenarios." Proxy support enables broader deployment contexts; loop hygiene enables longer, more complex agent sessions.

## 5. Bugs & Stability

No bug reports, crashes, or regressions were filed today. The absence of bug traffic is a positive signal, though the low overall issue volume (1 open issue, 0 closed) means the project may not yet have a large user base reporting production problems — or bug reporting culture may still be developing.

## 6. Feature Requests & Roadmap Signals

- **Proxy support for providers (Issue #988)** — This is a high-signal request. Proxy support is a prerequisite for enterprise and privacy-focused deployments. If NullClaw aims to be a general-purpose agent framework, this feature is likely to land in the next minor release cycle, assuming an implementation PR appears.

- **Prompt caching & tool output compression (PR #987)** — While this is an existing PR rather than a feature request, its focus on loop hygiene and compression suggests the roadmap includes deeper optimizations for local, long-running agent workflows. Expect related work on memory management and context window efficiency.

## 7. User Feedback Summary

Today's activity reveals two distinct user segments:

1. **Deployment-focused users** (Issue #988) — Need network flexibility, operating behind proxies or in restricted environments. Their satisfaction depends on NullClaw's ability to integrate into existing infrastructure.
2. **Power-user/long-run agents** (PR #987 community interest) — Users running complex, tool-heavy local agent loops are hitting performance and stability walls. The existence of this PR (rather than a flood of bug reports) suggests the community is constructive and willing to contribute fixes.

No explicit dissatisfaction signals today. The project appears to be in a phase where early adopters are identifying real-world friction points and some are contributing solutions.

## 8. Backlog Watch

- **Issue #988 — proxy support** ([Link](https://github.com/nullclaw/nullclaw/issues/988)) — Open since 2026-08-15 with no maintainer response yet. While fresh, proxy support is a non-trivial feature that could benefit from early maintainer engagement to scope the implementation (per-provider? global? auth support?). Worth monitoring for a response within the coming week.

- **PR #987 — loop hygiene** ([Link](https://github.com/nullclaw/nullclaw/pull/987)) — Open since 2026-08-15 with no review activity yet. This is a substantial PR touching core agent loop mechanics; maintainer review should be prioritized. If merged, it would be a meaningful stability upgrade.

---

**Digest generated:** 2026-08-16 | **Data source:** GitHub API via NullClaw repository | **Activity level:** Low | **Project trajectory:** Positive — focused on reliability and deployment flexibility.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-16

## 1. Today's Overview

IronClaw is experiencing a significant performance and stability push, with 21 issues closed and 5 PRs merged in the last 24 hours, all anchored around the #7591 epic targeting database write amplification and heartbeat overhead. The project remains release-stalled (no new versions) but activity is intense, concentrated on the Reborn runtime's operational cost reductions. Six issues remain open and active, including one high-priority evaluation benchmark and several architectural follow-ups from the #7634 merged PR. Overall health is strong — the team is closing legacy debt and hardening the production pipeline in parallel.

## 2. Releases

No new releases were published. The project appears to be in a pre-release optimization phase, accumulating performance fixes and architectural cleanups before the next version cut.

## 3. Project Progress

**Merged / Closed PRs (today):**

- **[#7634](https://github.com/nearai/ironclaw/pull/7634)** — *feat(unbound-turns): complete the switchover to prepared-context turns.* A stacked PR completing the unbound-turns model with a 71-clause conformance audit against the design docs. This is a major architectural milestone for the Reborn agent loop.
- **[#7629](https://github.com/nearai/ironclaw/pull/7629)** — *perf: reduce trigger and outbound state writes.* Moves `prune_run_history` from every Running-row update to the initial fire-claim path, eliminating correlated-subquery DELETEs per trigger fire. Directly implements #7595.
- **[#7628](https://github.com/nearai/ironclaw/pull/7628)** — *perf(processes): remove heartbeat journal churn.* Stops appending `ProcessJournalKind::Heartbeat` rows and reserves no cursors for heartbeats; ships a 15-second turn-run heartbeat interval. Implements #7593 and #7599.
- **[#7676](https://github.com/nearai/ironclaw/pull/7676)** — *perf(threads): coalesce thread index touches.* Bursty per-thread activity touches are now coalesced into bounded thread-index writes with monotonic CAS updates. Implements #7596.
- **[#7670](https://github.com/nearai/ironclaw/pull/7670)** — *chore(agents): refresh codebase knowledge graph.* Nightly bootstrap snapshot refresh via CI workflow.

**Notable Open PRs:**

- **[#7677](https://github.com/nearai/ironclaw/pull/7677)** — *perf(threads): fold message lookup indexes into message rows.* Replaces 1–3 sibling entry rows per message with indexed projections on the message entry itself.
- **[#7678](https://github.com/nearai/ironclaw/pull/7678)** — *perf(capabilities): persist invocation state at gate and terminal edges.* Keeps capability invocation state worker-local and atomically materializes at completed/failed/approval-blocked edges.
- **[#7491](https://github.com/nearai/ironclaw/pull/7491)** — *feat(coding): omp core-tool contract + engines + benchmark arm.* Consolidates the coding tool surface to six exact bare names (`read`, `write`, `edit`, `glob`, `grep`, `bash`), removing legacy mixed surfaces.
- **[#7651](https://github.com/nearai/ironclaw/pull/7651)** — *feat(automations): add deterministic no-result suppression.* Introduces `trigger_create` result-delivery semantics for suppress-vs-deliver intent.
- **[#7679](https://github.com/nearai/ironclaw/pull/7679)** — *fix(live-qa): stop harness bugs reddening green canary runs.* Addresses three harness defects that were failing correct product behavior in the Live Canary.

## 4. Community Hot Topics

- **[#467](https://github.com/nearai/ironclaw/issues/467)** — *Trajectory benchmark system for agent quality evaluation* (OPEN, created 2026-03-02, updated 2026-08-15, 4 comments). Proposes a benchmark running real user scenarios through the real agent loop with real LLM calls, evaluated against hard assertions and LLM-as-judge criteria. **Underlying need:** The project lacks a systematic way to measure agent quality over time; this reflects growing maturity and the need for empirical evaluation as Reborn approaches production readiness.

- **[#3236](https://github.com/nearai/ironclaw/issues/3236)** — *Define same-thread follow-up and steering policy* (CLOSED, 3 comments). Covered normal follow-ups, `/btw` steering, queue ordering, promotion, cancellation, and blocked-run behavior. **Underlying need:** As Reborn handles multi-turn threaded conversations, deterministic steering and queue management became critical for user-facing reliability.

- **[#7672](https://github.com/nearai/ironclaw/issues/7672)** — *Typed ToolChoice: retire the overloaded tool_choice string across providers* (OPEN, created 2026-08-15). Flags that `LoopModelRequest.tool_choice` overloads mode strings and tool names as a single `Option<String>`, requiring string-matching in every provider encoder. **Underlying need:** Type safety and provider abstraction cleanliness — a lingering technical debt item from the provider-contracts work in #7634.

- **[#7673](https://github.com/nearai/ironclaw/issues/7673)** — *BudgetLedger accounting refinements* (OPEN, created 2026-08-15). Identifies two bounded gaps: truncated-launch double-charging and charge durability. **Underlying need:** Cost accounting accuracy is critical for a hosted agent platform; even conservative over-counting erodes user trust.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix Status |
|----------|-------|---------|------------|
| **High** | [#7675](https://github.com/nearai/ironclaw/issues/7675) | E2E `qa_6c gmail-to-sheet` flake cascades across the provider-contracts session; intermittent resource-class capability failure | No fix PR yet |
| **Medium** | [#6821](https://github.com/nearai/ironclaw/issues/6821) | IronHub search returns 3 tools from a 18-tool catalog; lists 21 skills, 20 not in catalog | Closed — resolved |
| **Medium** | [#6835](https://github.com/nearai/ironclaw/issues/6835) | MCP `AuthRequired` errors classified as `Client` instead of triggering re-auth gate | Closed — resolved |
| **Low** | [#5239](https://github.com/nearai/ironclaw/issues/5239) | Scheduler misclassifies stale terminal heartbeat as runner failure, emitting false terminal-failure path | Closed — resolved |
| **Low** | [#5237](https://github.com/nearai/ironclaw/issues/5237) | Production debug logging floods Railway with Cranelift/Wasmtime compiler DEBUG output | Closed — resolved |
| **Low** | [#4992](https://github.com/nearai/ironclaw/issues/4992) | Local-dev SSO access mismatch causes Railway automations to fail before run/thread creation | Closed — resolved |

The **#7675** E2E flake is the most concerning open stability item — it indicates a fragility in the live test harness that could mask real regressions. The #7679 PR aims to address harness-induced false positives but was open at time of digest.

## 6. Feature Requests & Roadmap Signals

- **Trajectory benchmark system (#467)** — If funded and scoped, this would be a major addition enabling empirical agent-quality tracking. Likely to appear in a future minor release as a dedicated evaluation module.
- **Deterministic no-result suppression for automations (#7651)** — Advanced in an open PR. Strong signal that the automations surface is maturing toward production-grade predictability.
- **Typed ToolChoice (#7672)** — A refactoring request with user-facing impact (cleaner provider contracts). Likely to be picked up soon given the #7634 switchover completion.
- **IronHub agent link from WebUI (#7516)** — Open PR adding operator-facing IronHub registration surface. Indicates the team is closing the gap between CLI-only and WebUI-only operational workflows.

## 7. User Feedback Summary

- **IronHub catalog discoverability** (#6821) — Users reported severe mismatches between search results and the actual catalog, suggesting the agent was hallucinating or mis-indexing skills. This has been closed, indicating the issue was taken seriously and resolved.
- **Telegram forum-topic delivery gaps** (#6829) — A coverage hole where replies to forum-topic messages lacked `message_thread_id`, causing cross-contamination in supergroups. Closed, signaling improved channel reliability.
- **Heartbeat misclassification** (#5239) — False terminal-failure signals from stale heartbeats would have confused operators monitoring production runs. The fix improves observability trust.
- **Debug log flooding** (#5237) — Railway-hosted users experienced log noise from Wasmtime/Cranelift debug output, increasing costs and reducing signal-to-noise. Closed with a logging-filter fix.

Overall sentiment: The closed-bug volume (21 issues) far exceeds open bugs (6), and the closed items target real operational pain points (logging costs, false failures, catalog accuracy). The project is in a hardening phase.

## 8. Backlog Watch

| Issue | Age | Priority | Risk |
|-------|-----|----------|------|
| [#467](https://github.com/nearai/ironclaw/issues/467) — Trajectory benchmark system | ~5 months | Strategic | Long-term evaluation capability gap |
| [#7675](https://github.com/nearai/ironclaw/issues/7675) — E2E gmail-to-sheet flake | 1 day | High | CI reliability; may mask regressions |
| [#7672](https://github.com/nearai/ironclaw/issues/7672) — Typed ToolChoice | 1 day | Medium | Provider contract cleanliness |
| [#7673](https://github.com/nearai/ironclaw/issues/7673) — BudgetLedger refinements | 1 day | Medium | Cost-accounting accuracy |
| [#7671](https://github.com/nearai/ironclaw/issues/7671) — Capability dispatch stack pressure | 1 day | Low-Medium | Test-stack overflow risk in sandbox paths |

The **#7675** E2E flake and **#7672** Typed ToolChoice are the most actionable backlog items — both are recent, well-scoped, and block further confidence in CI and provider contracts respectively. The benchmark system (#467) is strategically important but lower urgency given its scope.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-16

---

## 1. Today's Overview

LobsterAI (netease-youdao/LobsterAI) showed moderate development activity over the last 24 hours, with 18 issues and 6 pull requests updated. The most notable event was the **merging of two bug-fix PRs** (#1879 and #2234), both addressing correctness issues in the OpenClaw integration layer — specifically plugin path preservation on config sync and cron job descendant finalization. Four Dependabot security update PRs remain open, signaling ongoing supply-chain hygiene efforts. No new releases were published. The overall health signal is positive: the majority of today's issue activity was a wave of stale-issue closures (16/18), suggesting the maintainer team is actively managing backlog hygiene. However, two open issues (#1903, #2046) point to persistent login and memory-system concerns that warrant sustained attention.

---

## 2. Releases

**No new releases** were published in the last 24 hours.

---

## 3. Project Progress

### Merged / Closed PRs

| PR | Title | Summary |
|---|---|---|
| [#1879](https://github.com/netease-youdao/LobsterAI/issues/1879) | `fix: preserve manually-added plugin load paths on config sync` | Fixes a regression where `OpenClawConfigSync.sync()` silently overwrote manually-added plugin paths (e.g., community plugins like `memory-lancedb-pro`) with only the LobsterAI-managed third-party extension directory. |
| [#2234](https://github.com/netease-youdao/LobsterAI/issues/2234) | `fix(openclaw): cron yield descendant finalization` | Resolves a bug where child agents finishing after a `sessions_yield` could not drive the parent agent to continue. Adds a yield-continuation loop during cron finalization covering parallel and serial descendant patterns. |

### Open PRs (Dependabot — 4 items)

| PR | Title | Details |
|---|---|---|
| [#2164](https://github.com/netease-youdao/LobsterAI/pull/2164) | `ci: bump trufflesecurity/trufflehog 3.88.30 → 3.95.5` | Security scanner update |
| [#2165](https://github.com/netease-youdao/LobsterAI/pull/2165) | `ci: bump actions/checkout 4 → 6` | GitHub Actions update |
| [#2166](https://github.com/netease-youdao/LobsterAI/pull/2166) | `ci: bump dorny/paths-filter 3 → 4` | CI path-filter update |
| [#2167](https://github.com/netease-youdao/LobsterAI/pull/2167) | `ci: bump actions/stale 9.1.0 → 10.3.0` | Stale-action update (includes a bug fix) |

> **Assessment:** Today's merged fixes are targeted correctness improvements rather than feature releases. The pipeline is primarily maintaining dependency hygiene via Dependabot.

---

## 4. Community Hot Topics

| Issue | Topic | Comments | Link |
|---|---|---|---|
| [#1903](https://github.com/netease-youdao/LobsterAI/issues/1903) | 会员登录频繁失败 | 3 | [link](https://github.com/netease-youdao/LobsterAI/issues/1903) |
| [#2046](https://github.com/netease-youdao/LobsterAI/issues/2046) | Agent 记忆体系产品建议 | 2 | [link](https://github.com/netease-youdao/LobsterAI/issues/2046) |
| [#2040](https://github.com/netease-youdao/LobsterAI/issues/2040) | OpenClaw 的五大薄弱点 | 2 | [link](https://github.com/netease-youdao/LobsterAI/issues/2040) |
| [#2041](https://github.com/netease-youdao/LobsterAI/issues/2041) | 记忆系统是最大瓶颈 | 2 | [link](https://github.com/netease-youdao/LobsterAI/issues/2041) |
| [#1885](https://github.com/netease-youdao/LobsterAI/issues/1885) | 邮箱 SKILL 路径穿越漏洞 | 2 | [link](https://github.com/netease-youdao/LobsterAI/issues/1885) |

### Underlying Needs Analysis

- **Agent memory & cross-session continuity** (Issues #2046, #2041, #2040): The community is deeply engaged with the memory-system gap in both LobsterAI and its upstream OpenClaw. Users are producing analysis comparing current behavior against ideal self-evolving agent architectures. This is the most consequential product theme — the lack of persistent, retrievable memory across sessions is a top perceived deficiency.
- **Authentication & billing pain** (Issue #1903): Member login failures directly block access to paid models, making this a high-impact usability and revenue concern.
- **Security hardening** (Issue #1885): The path-traversal vulnerability in the IMAP email skill was discovered and reported by a security-conscious community member. While closed, no fix PR is yet referenced, suggesting the patch is pending or the issue was closed without resolution.
- **UX/design dissatisfaction** (Issues #1836, #1920, #1921): Multiple UI/empty-state complaints indicate the interface lags behind competing products. This is a recurring theme rather than a one-off.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix Status |
|---|---|---|---|
| 🔴 High | [#1849](https://github.com/netease-youdao/LobsterAI/issues/1849) | Consecutive queries produce infinite `NO_REPLY` or truncated output; task marked complete while model is still generating | ✅ Closed |
| 🔴 High | [#1988](https://github.com/netease-youdao/LobsterAI/issues/1988) | After update, `qwen3.6-plus` from Alibaba Baicoding plan is forcibly overridden by NetEase's built-in model and fails with quota error | ✅ Closed |
| 🔴 High | [#1885](https://github.com/netease-youdao/LobsterAI/issues/1885) | **Security**: Path traversal in IMAP skill's `downloadAttachments` — unfiltered attachment filenames are concatenated directly into filesystem paths | ✅ Closed (no fix PR linked) |
| 🟡 Medium | [#1993](https://github.com/netease-youdao/LobsterAI/issues/1993) | "AI engine connection lost" on desktop app; IM Bot connection is stable | ✅ Closed |
| 🟡 Medium | [#2017](https://github.com/netease-youdao/LobsterAI/issues/2017) | Local run fails to log in; prompts missing `cfmind` OpenClaw runtime, requires pre-build step | ✅ Closed |
| 🟡 Medium | [#1971](https://github.com/netease-youdao/LobsterAI/issues/1971) | Scroll hijacking in session page with tall elements (e.g., Mermaid diagrams); virtual scrolling re-renders cause infinite scroll event loops | ✅ Closed |
| 🟡 Medium | [#2039](https://github.com/netease-youdao/LobsterAI/issues/2039) | Dreaming switch writes to an unrecognized `memory-core` schema path; breaks on gateway restart | ✅ Closed |
| 🟢 Low | [#1920](https://github.com/netease-youdao/LobsterAI/issues/1920) | Cowork initialization shows static `Loading...` instead of skeleton shimmer | ✅ Closed |
| 🟢 Low | [#1921](https://github.com/netease-youdao/LobsterAI/issues/1921) | Skills Manager and TaskRunHistory empty states lack icons and subtitles | ✅ Closed |
| 🟢 Low | [#1878](https://github.com/netease-youdao/LobsterAI/issues/1878) | WeChat IM bot QR code flow has no input field for the 6-digit verification code | ✅ Closed |

> **Key observation:** The closed bugs cover a mix of upstream OpenClaw sync issues, rendering bugs in the virtual-scroll implementation, and a security vulnerability. The two most impactful bugs (truncated generation #1849 and model override #1988) are now closed, but no associated fix PRs were cited in the data provided, so verification of resolution is pending. The security issue #1885 requires a follow-up to confirm a patch was applied.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Link |
|---|---|---|
| [#1880](https://github.com/netease-youdao/LobsterAI/issues/1880) | Integrate **Hermes Agent** alongside OpenClaw, following Open WebUI's agent integration pattern | [link](https://github.com/netease-youdao/LobsterAI/issues/1880) |
| [#2016](https://github.com/netease-youdao/LobsterAI/issues/2016) | Add **OpenHuman engine** support | [link](https://github.com/netease-youdao/LobsterAI/issues/2016) |
| [#2046](https://github.com/netease-youdao/LobsterAI/issues/2046) | **Agent memory system** — persistent session metadata, cross-session retrieval, automatic historical awareness | [link](https://github.com/netease-youdao/LobsterAI/issues/2046) |
| [#2036](https://github.com/netease-youdao/LobsterAI/issues/2036) | Add `agent:turn` / `agent:loop` events to OpenClaw gateway for real-time log persistence | [link](https://github.com/netease-youdao/LobsterAI/issues/2036) |

### Roadmap Prediction

- **Memory system** is the strongest signal. Multiple community members (#2040, #2041, #2046) independently identified memory as the #1 bottleneck. Issue #2046's detailed proposal — persistent session titles, cross-session retrieval, automatic historical awareness — reads like a product brief. Expect this to be a priority in the next major release cycle.
- **Gateway event hooks** (#2036) are a technical prerequisite for real-time memory persistence and may land first as an upstream contribution to OpenClaw.
- **Hermes Agent** (#1880) is a lower-confidence signal — it's a single request. However, if OpenClaw continues to be the upstream, supporting multiple agent frameworks in LobsterAI would differentiate the product.

---

## 7. User Feedback Summary

| Theme | Sentiment | Key Quotes / Evidence |
|---|---|---|
| **UI/UX quality** | 😠 Dissatisfied | Issue #1836: *"Compared to competitors, it's too ugly and uncomfortable to use."* Multiple empty-state and loading-state complaints (#1920, #1921) reinforce this. |
| **Authentication reliability** | 😠 Frustrated | Issue #1903: *"Member login fails frequently — cannot access NetEase paid models."* Direct impact on paying users. |
| **Model routing correctness** | 😠 Frustrated | Issue #1988: *"After update, qwen3.6-plus is forcibly overridden by NetEase's built-in model and fails."* Suggests a config-sync regression. |
| **Memory & continuity** | 🤔 Needing | Issues #2046, #2041: *"Each new session is independent; Agent cannot auto-perceive, retrieve, or correlate history."* High-level product feedback from power users. |
| **Security awareness** | 👍 Positive | Issue #1885: User discovered and reported a path-traversal vulnerability with PoC code — demonstrates a security-conscious community. |
| **Setup / onboarding** | 😐 Mixed | Issues #2017 (missing runtime), #1878 (WeChat verification flow) — friction points for new users. |

---

## 8. Backlog Watch

| Issue | Reason for Watch | Link |
|---|---|---|
| [#1903](https://github.com/netease-youdao/LobsterAI/issues/1903) | **Open** — member login failures directly block paying users; no visible fix progress | [link](https://github.com/netease-youdao/LobsterAI/issues/1903) |
| [#2046](https://github.com/netease-youdao/LobsterAI/issues/2046) | **Open** — detailed, well-structured feature request for agent memory; high community interest but no maintainer response yet | [link](https://github.com/netease-youdao/LobsterAI/issues/2046) |
| [#1885](https://github.com/netease-youdao/LobsterAI/issues/1885) | **Closed but no fix PR cited** — security vulnerability (path traversal) requires verification that a patch was actually merged | [link](https://github.com/netease-youdao/LobsterAI/issues/1885) |
| [#2036](https://github.com/netease-youdao/LobsterAI/issues/2036) | **Closed** — proposes `agent:turn`/`agent:loop` gateway events; if upstream OpenClaw hasn't adopted it, this capability remains missing | [link](https://github.com/netease-youdao/LobsterAI/issues/2036) |

> **Maintainer attention recommended:** Issue #1903 should be prioritized as it impacts revenue-critical user sessions. Issue #1885 should be followed up to confirm the security patch status. Issue #2046 represents the clearest roadmap signal from the community and deserves a public response even if implementation is deferred.

---

*Digest generated from GitHub data fetched on 2026-08-16. Data source: LobsterAI repository (netease-youdao/LobsterAI) via LobsterAI project analytics.*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-16

## 1. Today's Overview

Moltis is in a high-velocity consolidation phase with 16 PRs activity in the last 24 hours — 14 merged and 2 still open — indicating strong contributor momentum. Two bugs closed today were both addressed within the same window, reflecting responsive maintenance. The project is balancing a notable wave of security hardening with meaningful feature additions across connectors, UX, and sandbox tooling. No new release was published today, but the merged changes suggest an imminent version bump.

## 2. Releases

No new releases were published on this date.

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Type | Summary |
|----|------|---------|
| [#1180](https://github.com/moltis-org/moltis/pull/1180) | Security fix | Hardened model and zip path extraction to prevent arbitrary file write and code execution via malicious zip or HuggingFace repos. |
| [#1179](https://github.com/moltis-org/moltis/pull/1179) | Security fix | Added signature verification for `node.pair.verify` to prevent callers from supplying their own keys or challenges. |
| [#1182](https://github.com/moltis-org/moltis/pull/1182) | Bug fix | Removed the guard preventing the `main` session from being deleted or archived — now behaves like any other session. |
| [#1191](https://github.com/moltis-org/moltis/pull/1191) | Bug fix | Fixed `moltis sandbox build` by pointing `gogcli` module path to the `openclaw` org after its repository migration. |
| [#1192](https://github.com/moltis-org/moltis/pull/1192) | Bug fix | Fixed `wacrawl` skill install metadata to reference the `openclaw` org, resolving broken Go install fallbacks. |
| [#1190](https://github.com/moltis-org/moltis/pull/1190) | Feature | Added durable calendar, channel, and email connectors (CalDAV, Gmail, Himalaya v2) with provider-neutral persistence and atomic snapshots. |
| [#1195](https://github.com/moltis-org/moltis/pull/1195) | Feature | Added Slack native live task cards with channel-neutral tool lifecycle updates and opaque per-run privacy. |
| [#1196](https://github.com/moltis-org/moltis/pull/1196) | Bug fix | Fixed ClawHub skill search timeout by eliminating per-result metadata RPC calls and consuming metadata inline. |
| [#1197](https://github.com/moltis-org/moltis/pull/1197) | Feature | Enabled starting agent chats directly from the command palette, appending "Ask agent" as the final item for any non-empty query. |
| [#1198](https://github.com/moltis-org/moltis/pull/1198) | Feature | Route OpenAI reasoning tool calls through the Responses API when `reasoning_effort` is combined with function tools. |
| [#1194](https://github.com/moltis-org/moltis/pull/1194) | Bug fix | Guarded empty bash array expansions for macOS bash 3.2 compatibility in `just local-validate-full`. |
| [#1158](https://github.com/moltis-org/moltis/pull/1158) | Feature | Added `zvec` vector database memory backend (feature-gated), using `redb` with an external llama-cpp embedding server. |
| [#1184](https://github.com/moltis-org/moltis/pull/1184) | Chore | Bumped `undici` from 7.28.0 to 7.29.0 in `/website`. |
| [#1200](https://github.com/moltis-org/moltis/pull/1200) | Chore | Bumped `postcss` and `js-yaml` dependencies across `/crates/web/ui` and `/docs`. |

### Open PRs

- [#1186](https://github.com/moltis-org/moltis/pull/1186) — **fix(vault):** normalize recovery phrase before hashing (security-adjacent; not yet merged)
- [#1199](https://github.com/moltis-org/moltis/pull/1199) — **Add Coder remote workspace sandbox support** (feature, not yet merged)

## 4. Community Hot Topics

- **[Issue #1132](https://github.com/moltis-org/moltis/issues/1132)** — Users consistently wanted the `main` session to be deletable/archivable. Though it has 0 comments, the issue attracted a fix (PR #1182) quickly, suggesting the pain point was widely felt but under-discussed.
- **[Issue #1189](https://github.com/moltis-org/moltis/issues/1189)** — Sandbox build failures due to the `gogcli` org migration caused immediate breakage for all users building pre-built images. Fixed in PR #1191 the same day.
- **[PR #1190](https://github.com/moltis-org/moltis/pull/1190)** — The durable connectors PR is the largest feature addition this cycle, signaling community demand for persistent, provider-neutral integrations with calendar/email/channel data.
- **[PR #1195](https://github.com/moltis-org/moltis/pull/1195)** — Slack native cards reflect a push toward richer in-platform UX rather than relying on external messaging bot interfaces.

**Underlying need:** Users are maturing past early-stage setup and now demand reliability (security, correct module paths) alongside richer integrations (connectors, Slack cards, command palette).

## 5. Bugs & Stability

| Severity | Issue / PR | Description |
|----------|-----------|-------------|
| **High** | [#1180](https://github.com/moltis-org/moltis/pull/1180) | Arbitrary file write via malicious zip or HuggingFace repo — potential code execution. Fixed in PR #1180. |
| **High** | [#1179](https://github.com/moltis-org/moltis/pull/1179) | Unverified node pairing signatures — attacker could supply own key/challenge. Fixed in PR #1179. |
| **Medium** | [#1186](https://github.com/moltis-org/moltis/pull/1186) | Recovery phrase hashing inconsistency: the stored hash was computed over the raw phrase while unsealing normalizes it first. Open PR; not yet merged. |
| **Medium** | [#1189](https://github.com/moltis-org/moltis/issues/1189) | Sandbox build failure due to `gogcli` org migration. Fixed in PR #1191 (merged). |
| **Low** | [#1132](https://github.com/moltis-org/moltis/issues/1132) | `main` session could not be deleted/archived. Fixed in PR #1182 (merged). |
| **Low** | [#1194](https://github.com/moltis-org/moltis/pull/1194) | `just local-validate-full` crashed on macOS bash 3.2 with unbound variable error. Fixed in PR #1194 (merged). |
| **Low** | [#1196](https://github.com/moltis-org/moltis/pull/1196) | ClawHub search exceeded RPC timeout due to per-result metadata requests. Fixed in PR #1196 (merged). |

The two security fixes (#1180, #1179) are the most significant stability events of the day. The outstanding vault normalization PR (#1186) remains open and could become a release-blocker.

## 6. Feature Requests & Roadmap Signals

- **Durable connectors** (PR #1190) — Calendar, email, and channel integrations with atomic snapshots and full-text search suggest the roadmap is shifting toward persistent, production-grade data hooks.
- **Slack native task cards** (PR #1195) — Indicates investment in in-platform rich UX over bare-text bot responses.
- **Command palette agent launch** (PR #1197) — Lowers the barrier to starting agent conversations, signaling a focus on discoverability and streamlined workflows.
- **OpenAI Responses API routing** (PR #1198) — Adapts to upstream API changes and enables reasoning-effort tool calling, keeping the project aligned with OpenAI's evolving surface.
- **zvec memory backend** (PR #1158) — Experimental vector database support hints at a longer-term memory/search roadmap.
- **Coder sandbox support** (PR #1199, open) — Extends sandbox backends beyond Docker, suggesting plans for cloud IDE integration.

**Predicted next version focus:** Security hardening follow-through, vault fix (#1186), and Coder sandbox (#1199) are the most likely remaining items before the next release.

## 7. User Feedback Summary

- **Sandbox breakage is a real pain point.** The `gogcli` and `wacrawl` org migrations (#1189, #1191, #1192) broke pre-built images for users, indicating that upstream dependency churn needs better mitigation (pinning, fork mirrors).
- **Vault recovery phrase inconsistency** (#1186) suggests users may have encountered failed unsealing after typing phrases with dashes or mixed case — a trust issue for a security-critical component.
- **`main` session immutability** (#1132) was frustrating for users wanting clean session management. The quick fix indicates this was a widely shared annoyance.
- **ClawHub search timeouts** (#1196) point to scaling concerns as the skill catalog grows — users are relying on search more heavily.
- Overall sentiment appears positive: contributors are rapidly addressing bugs, and feature velocity is high.

## 8. Backlog Watch

| Item | Type | Reason for Attention |
|------|------|---------------------|
| [#1186](https://github.com/moltis-org/moltis/pull/1186) | Bug fix (open) | Vault recovery phrase hashing inconsistency — security-adjacent and affects user trust. Needs maintainer review for merge. |
| [#1199](https://github.com/moltis-org/moltis/pull/1199) | Feature (open) | Coder sandbox support is a significant capability expansion but remains unmerged. Worth prioritizing given the active sandbox ecosystem. |
| [#1132](https://github.com/moltis-org/moltis/issues/1132) | Bug (closed) | Fixed but worth verifying the fix doesn't reintroduce the "current channel session" archive restriction edge case. |

**Overall project health: Strong.** High PR throughput, swift bug resolution, and a clear trajectory toward security hardening and richer integrations. The two open PRs (#1186, #1199) are the only items pending maintainer action.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-16

## 1. Today's Overview

CoPaw saw **19 active items** in the last 24 hours (9 issues + 10 PRs), indicating steady community engagement. No new releases were published, and no PRs were merged or closed, suggesting the contributor pipeline is currently **blocked on review** rather than stalled. The activity is heavily weighted toward bug reports and feature requests from v2.1.0 users, pointing to a maturing codebase where early-release edge cases are surfacing. Overall project health is **moderate** — high submission volume but low resolution velocity.

---

## 2. Releases

**No new releases** published in the last 24 hours. The latest referenced version remains **v2.1.0** (pip install, site-packages).

---

## 3. Project Progress

No PRs were merged or closed today. Ten open PRs received updates or new submissions:

| PR | Focus | Status |
|---|---|---|
| [#6940](https://github.com/agentscope-ai/QwenPaw/issues/6940) | Native DataPaw app runtime & durable analysis workspace | Review |
| [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061) | Fix: deliver tool-result videos on OpenAI Responses API | Open |
| [#6302](https://github.com/agentscope-ai/QwenPaw/issues/6302) | Unify provider discovery, model metadata & routing | Review |
| [#7057](https://github.com/agentscope-ai/QwenPaw/issues/7057) | Fix: add user-local bin dirs to subprocess PATH | Open |
| [#7055](https://github.com/agentscope-ai/QwenPaw/issues/7055) | Fix: sync top-level text on agent cron update | Open |
| [#6623](https://github.com/agentscope-ai/QwenPaw/issues/6623) | Fix: prevent final text loss in ACP notification race | Under Review |
| [#7054](https://github.com/agentscope-ai/QwenPaw/issues/7054) | Feat: remote Chrome bridge endpoint for LAN browsers | Open |
| [#7001](https://github.com/agentscope-ai/QwenPaw/issues/7001) | Feat: isolate session/memory per sender in Matrix group rooms | Open |
| [#7050](https://github.com/agentscope-ai/QwenPaw/issues/7050) | Feat: per-cron-job model override picker | Open |
| [#7049](https://github.com/agentscope-ai/QwenPaw/issues/7049) | Feat: limit/before pagination on GET /chats/{chat_id} | Open |

---

## 4. Community Hot Topics

1. **Video support broken on OpenAI Responses API** — Issues [#7059](https://github.com/agentscope-ai/QwenPaw/issues/7059) and [#7060](https://github.com/agentscope-ai/QwenPaw/issues/7060), with fix PR [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061). Same author (xiaoka76) filing back-to-back bugs signals a **real user workflow** (video analysis via Volcengine Ark) that is currently non-functional.

2. **Matrix end-to-end encryption** — Issue [#6476](https://github.com/agentscope-ai/QwenPaw/issues/6476) (closed 2026-08-15) after a multi-step workaround with `libolm-dev` and `matrix-nio[e2e]`. Community interest in secure messaging channels persists.

3. **Long-running conversations cause UI lag** — Issue [#3915](https://github.com/agentscope-ai/QwenPaw/issues/3915) with 3 comments and 1 👍. This is a **long-standing enhancement request** (open since April) for virtual scrolling in the Console WebUI, reflecting growing user bases hitting scalability limits.

4. **OAuth2 refresh token rotation** — Issue [#7053](https://github.com/agentscope-ai/QwenPaw/issues/7053) highlights a correctness gap in the MCP OAuth flow that permanently degrades remote integrations.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| 🔴 High | [#7059](https://github.com/agentscope-ai/QwenPaw/issues/7059) | `view_video` silently drops video frames on OpenAI Responses API — model never receives data | [#7061](https://github.com/agentscope-ai/QwenPaw/issues/7061) |
| 🔴 High | [#7060](https://github.com/agentscope-ai/QwenPaw/issues/7060) | `view_video` inline-media cap hardcoded at 2 MB; provider setting ignored | Related to #7061 |
| 🟠 Medium | [#7051](https://github.com/agentscope-ai/QwenPaw/issues/7051) | Image attachments lost on chat session reload in Console | — |
| 🟠 Medium | [#7053](https://github.com/agentscope-ai/QwenPaw/issues/7053) | OAuth2 refresh token not persisted on rotation; MCP degrades to manual re-auth | — |
| 🟡 Low | [#6476](https://github.com/agentscope-ai/QwenPaw/issues/6476) | Matrix E2E encryption unavailable (closed with workaround) | — |

**Assessment:** Two high-severity video bugs introduced in v2.1.0 appear to share a common root cause in the promotion path from PR #6495, with a fix PR already open. Image persistence and OAuth token rotation are the next most impactful gaps.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Likelihood for Next Release |
|---|---|---|
| Per-cron-job model override | [#7050](https://github.com/agentscope-ai/QwenPaw/issues/7050) | **High** — backend contract exists; UI gap only |
| Pagination on chat history API | [#7049](https://github.com/agentscope-ai/QwenPaw/issues/7049) | **High** — directly addresses #3915 performance concerns |
| Remote Chrome bridge (non-loopback) | [#7054](https://github.com/agentscope-ai/QwenPaw/issues/7054) | Medium — infrastructure improvement |
| Matrix per-sender session isolation | [#7001](https://github.com/agentscope-ai/QwenPaw/issues/7001) | Medium — channel-specific |
| Virtual scrolling for WebUI | [#3915](https://github.com/agentscope-ai/QwenPaw/issues/3915) | Medium — large effort, PR #7049 is a partial step |
| Background task callback/notification | [#7056](https://github.com/agentscope-ai/QwenPaw/issues/7056) | Low — no PR yet, architectural change |
| Plugin API `system_prompt` permission | [#7052](https://github.com/agentscope-ai/QwenPaw/issues/7052) | Low — security/design decision needed |
| Restore native context strategy selector | [#7058](https://github.com/agentscope-ai/QwenPaw/issues/7058) | High — trivial UI restore, backend already supports it |

**Signal:** The roadmap is clearly trending toward **API scalability** (pagination, per-job overrides) and **fixing v2.1.0 regressions**. The backend for several feature requests already exists, suggesting the next release will prioritize finishing work rather than major new architecture.

---

## 7. User Feedback Summary

- **Video workflows are a real pain point.** Two bugs from the same user in one day on the same feature (`view_video`) indicate this is a frequently used path that needs stability.
- **Session reload data loss** (#7051) breaks trust in the Console — users expect persistence.
- **OAuth token rotation failure** (#7053) causes silent degradation of MCP integrations, which is worse than an explicit error.
- **Missing UI controls** (#7058 — context strategy selector, #7050 — per-job model picker) frustrate power users who need fine-grained control.
- **Plugin privacy concerns** (#7052) reflect enterprise users wanting to separate internal system prompts from user-visible context.
- Overall tone: **constructive but frustrated** — users are filing detailed bug reports with reproduction steps and even fix PRs, indicating strong investment in the project.

---

## 8. Backlog Watch

| Item | Open Since | Risk |
|---|---|---|
| [#3915](https://github.com/agentscope-ai/QwenPaw/issues/3915) — Virtual scrolling for WebUI | 2026-04-28 (3.5 months) | High — blocks scaling to large conversations |
| [#6302](https://github.com/agentscope-ai/QwenPaw/issues/6302) — Unified provider/model routing | 2026-07-21 (1.5 months) | High — cross-cutting architecture PR, large scope |
| [#6623](https://github.com/agentscope-ai/QwenPaw/issues/6623) — ACP notification race fix | 2026-08-01 (under review) | Medium — known race condition, fix in review |
| [#7056](https://github.com/agentscope-ai/QwenPaw/issues/7056) — Background task callbacks | 2026-08-15 | Low — no PR yet, feature request |
| [#7052](https://github.com/agentscope-ai/QwenPaw/issues/7052) — Plugin `system_prompt` permission | 2026-08-15 | Low — no PR yet, design decision needed |

**Recommendation:** PRs [#6302](https://github.com/agentscope-ai/QwenPaw/issues/6302) and [#6623](https://github.com/agentscope-ai/QwenPaw/issues/6623) need maintainer review attention. The virtual scrolling request [#3915](https://github.com/agentscope-ai/QwenPaw/issues/3915) has been open since April and is now partially addressed by pagination PR [#7049](https://github.com/agentscope-ai/QwenPaw/issues/7049) — a merged #7049 could unblock or reduce the scope of #3915.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-16

## 1. Today's Overview

ZeroClaw is experiencing high engagement with **50 issues** and **50 PRs** updated in the last 24 hours (46 open issues, 44 open PRs, 6 merged/closed). The project is in a design-heavy phase, with most active discussion centered on architectural RFCs rather than new releases—no new versions were published today. Core work is progressing on reliability (Anthropic fallback/telemetry fixes), security hardening (SSRF gates, webhook audit exports), and zerocode TUI parity. Activity is sustained and maintainer-visible, though the open PR volume suggests a bottleneck in review throughput.

---

## 2. Releases

**No new releases today.**

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Summary | Author |
|---|---|---|
| [#9262](https://github.com/zeroclaw-labs/zeroclaw/pull/9262) | Surface native Anthropic refusals as typed `AnthropicRefusalError` | @IftekharUddin |
| [#9263](https://github.com/zeroclaw-labs/zeroclaw/pull/9263) | Route Anthropic refusals through client-side fallback entries | @IftekharUddin |
| [#9265](https://github.com/zeroclaw-labs/zeroclaw/pull/9265) | Opt-in Anthropic server-side fallback requests | @IftekharUddin |
| [#9266](https://github.com/zeroclaw-labs/zeroclaw/pull/9266) | Detect Anthropic server-side fallback responses | @IftekharUddin |
| [#9268](https://github.com/zeroclaw-labs/zeroclaw/pull/9268) | Surface safeguard fallback notices in channels (closes Anthropic refusal/fallback stack) | @IftekharUddin |

**Key advancement:** The Anthropic refusal-and-fallback stack (#9262–#9268) is now fully merged as a coordinated five-PR set. This introduces typed refusal classification, client-side fallback routing, opt-in server-side fallback, response detection, and operator-visible fallback notices across all channels. This is a significant reliability and transparency improvement for Anthropic-provider users.

### Notable PRs Still Open

- **#9002** — Keep agent turns alive after dashboard viewer disconnect (P1, XL)
- **#10003** — Account Reliable rejected attempts exactly (risk:high)
- **#9109** — Native Hailo-Ollama provider support
- **#9995** — Harden webhook audit exports against credential leaks (P1)
- **#9739** — Multi-session panes with agent sidebar in zerocode
- **#10021** — Apply target thinking to independent delegates

---

## 4. Community Hot Topics

### Top Issues by Comment Count

1. **[#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603)** — *RFC: ZeroClaw Chat Completions profile* (21 comments)
   Bridges the gap between ZeroClaw's native WebSocket/ACP/webhook transport surface and the dominant OpenAI Chat Completions protocol. Enables drop-in compatibility with Open WebUI, LobeChat, Continue.dev, Aider, LangChain, and the OpenAI SDK. High community demand for interoperability.

2. **[#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487)** — *RFC: Runtime-owned conversation sessions and transport surface adapters* (17 comments)
   Proposes a formal ownership boundary for conversations and a durable admission layer. Two revisions since late July suggest evolving consensus around invariants.

3. **[#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488)** — *RFC: Unified attachment architecture for web chat and channels* (16 comments)
   Aims to unify attachment handling across web chat and channel surfaces. Drafted with Codex assistance.

4. **[#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954)** — *RFC: Provenance, conversation binding, and reply contract for internally initiated agent turns* (13 comments)
   Revision 2 (Aug 5) added boundary clarifications on identity stability, binding concurrency, and reply lifecycles.

5. **[#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971)** — *RFC: Security posture, credential boundaries, and universal ingress policy* (13 comments)
   Comprehensive security design covering credentials, sandboxing, workspace policy, and redaction.

### Analysis

The dominant theme is **protocol interoperability and architectural clarity**. The Chat Completions RFC (#8603) signals strong user demand for OpenAI-ecosystem compatibility. The session ownership RFC (#9487) and attachment RFC (#9488) reflect an ongoing effort to formalize ZeroClaw's internal boundaries before the codebase grows further. These are design-phase RFCs, not yet accepted for implementation, but they represent the project's near-term architectural roadmap.

---

## 5. Bugs & Stability

| Issue / PR | Severity | Summary | Fix Status |
|---|---|---|---|
| [#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527) | **P1** (closed) | macOS desktop app reopens blank or without a window; permissions not detected | Closed 2026-08-15 |
| [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) | **P1** | `cron` custom-shell test hits `ETXTBSY` race under parallel runtime gate; causes false CI failures on unrelated PRs | Accepted, fix in progress |
| [#9655](https://github.com/zeroclaw-labs/zeroclaw/issues/9655) | **P1** | Approval cards carry no position; back-to-back cards from one message are indistinguishable before tapping | Accepted, no fix PR yet |
| [#9470](https://github.com/zeroclaw-labs/zeroclaw/issues/9470) | **P2** | Reliable fallback telemetry attribution is incorrect; stale notices shown to users | Fix PR #10003 open |
| [#7870](https://github.com/zeroclaw-labs/zeroclaw/issues/7870) | **P2** | Agent runtime options leak from first configured provider instead of the selected one | Accepted, no fix PR yet |
| [#9753](https://github.com/zeroclaw-labs/zeroclaw/pull/9753) | **P1** | Risk-profile `allowed_tools` treat empty list `[]` as unrestricted (fail-open) | Fix PR #9753 open |

**Notable regression avoided:** The P1 macOS app crash (#7527) was closed today. The `ETXTBSY` test flake (#9965) is a CI stability issue causing real friction for contributors. The approval-card indistinguishability bug (#9655) is a P1 UX flaw in the Telegram channel that currently lacks a fix PR.

---

## 6. Feature Requests & Roadmap Signals

| RFC / Feature | Issue / PR | Status |
|---|---|---|
| Chat Completions protocol support | [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | RFC, 21 comments — **high priority signal** |
| Runtime-owned conversation sessions | [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) | RFC, 17 comments — architecture gate |
| Unified attachment architecture | [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) | RFC, 16 comments — UX unification |
| Realtime speech-to-speech (Gemini Live) | [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) | RFC v2 (broker contract), 11 comments — revision in progress |
| Computer-use desktop support | [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | RFC, 9 comments — security-sensitive |
| Agent Plugins 1.0 (skill + MCP) loading | [#9810](https://github.com/zeroclaw-labs/zeroclaw/issues/9810) | RFC, 3 comments — new, Aug 7 |
| Discord thread-mode on mention | [#7849](https://github.com/zeroclaw-labs/zeroclaw/issues/7849) | Accepted, 2 comments — implementation pending |
| Wecom proactive messaging + media | [#7824](https://github.com/zeroclaw-labs/zeroclaw/issues/7824) | Accepted, 2 comments |
| Hailo-Ollama native provider | PR [#9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109) | Open, awaiting author action |
| Multi-session zerocode panes | PR [#9739](https://github.com/zeroclaw-labs/zeroclaw/pull/9739) | Open, near-complete (depends on #9738 already merged) |

**Predicted for next release window:** The Chat Completions profile (#8603), unified attachments (#9488), and Zerocode multi-session panes (#9739) are the most likely candidates for the next feature release. Gemini Live voice (#8780) and Agent Plugins (#9810) are further out but show active design momentum.

---

## 7. User Feedback Summary

- **Interoperability demand is loud:** The Chat Completions RFC (#8603) has the highest comment count in the issue tracker. Users are actively trying to plug ZeroClaw into Open WebUI, Continue.dev, Aider, and LangChain — and the lack of a native Chat Completions transport is a friction point.
- **Reliability transparency matters:** The Anthropic refusal/fallback stack (#9262–#9268) was contributor-driven but addresses a real operator pain point: users were seeing silent failures or unexplained model switches without knowing why.
- **Cron reliability concerns:** Users report missing cron documentation (#7762) and the inability to assign a specific model to cron jobs. The wall-clock timeout fix (#9320) addresses a critical bug where hung cron jobs held SQLite locks indefinitely.
- **Security paranoia is healthy:** The webhook audit export hardening (#9995) and SSRF gate fix (#8713) show users are actively probing and reporting security edge cases — including credential leaks in audit logs and SSRF risks in file-download URLs.
- **macOS desktop app was blocking workflows:** The blank-window crash (#7527, now closed) was rated S1/workflow-blocked. Closure is a positive signal.

---

## 8. Backlog Watch

| Issue / PR | Age | Concern |
|---|---|---|
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | Open since Jul 4 | Maintainer decision queue tracker — the RFC intake pipeline has no visible throughput metric |
| [#7130](https://github.com/zeroclaw-labs/zeroclaw/issues/7130) | Open since Jun 3 | Workspace-wide `forbid(unsafe_code)` — accepted but stalled for 2+ months |
| [#7089](https://github.com/zeroclaw-labs/zeroclaw/issues/7089) | Open since Jun 2 | Windows shell host evaluation (PowerShell/Git Bash vs cmd.exe) — accepted, no PR |
| [#9330](https://github.com/zeroclaw-labs/zeroclaw/issues/9330) | Open since Jul 24 | AI-assisted PR pre-review — accepted, needs author action |
| [#7870](https://github.com/zeroclaw-labs/zeroclaw/issues/7870) | Open since Jun 17 | Provider runtime option leak — accepted, no fix PR despite P2 severity |
| [#9655](https://github.com/zeroclaw-labs/zeroclaw/issues/9655) | Open since Aug 2 | Approval card position bug (P1) — accepted, **no fix PR** after 14 days |
| [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) | Open since Aug 13 | ETXTBSY cron test flake (P1) — accepted, fix in progress |

**Watch item:** Issue #9655 is a P1 bug with no fix PR after two weeks — the approval-card UX flaw affects Telegram channel operators directly. Issue #7870 has been accepted since June with no assigned fix. The maintainer decision queue (#8692) remains the structural bottleneck for RFC advancement.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*