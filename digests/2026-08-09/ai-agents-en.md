# OpenClaw Ecosystem Digest 2026-08-09

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-09 02:10 UTC

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



# OpenClaw Project Digest — 2026-08-09

---

## 1. Today's Overview

OpenClaw remains in a period of high activity: **500 issues and 500 PRs were updated in the last 24 hours**, with 448 open/active issues and 325 open PRs. Two new releases (v2026.6.34, v2026.6.33) were shipped today, both tightly focused on hardening security boundaries around browser routes, network requests, and credential exposure. The project is clearly in an aggressive stability and security iteration cycle, with the maintainers responding to a sustained stream of session-state, message-loss, and crash-loop bugs reported by production operators.

---

## 2. Releases

### v2026.6.34
**Focus: Safer browser and network boundaries.**
- Sandboxed browser routes and trusted DNS targets now reject unsafe access paths.
- Custom browser origins and loopback provider endpoints enforce stricter allowlists.
- **Contributors:** @eleqtrizit, @brunowowk, @mosidevv, @pgondhi987
- Issues: [#97958](https://github.com/openclaw/openclaw/issues/97958), [#38290](https://github.com/openclaw/openclaw/issues/38290), [#103075](https://github.com/openclaw/openclaw/issues/103075), [#110693](https://github.com/openclaw/openclaw/issues/110693)

### v2026.6.33
**Focus: Safer network and secret boundaries.**
- Provider streams, Discord REST responses, browser fetches, OAuth paths, and logs now cap hostile response sizes.
- Telegram credentials are excluded from diagnostic output.
- **Contributors:** @wangmiao0668000666, @Alix-007
- Issues: [#96989](https://github.com/openclaw/openclaw/issues/96989), [#95412](https://github.com/openclaw/openclaw/issues/95412), [#99428](https://github.com/openclaw/openclaw/issues/99428)

> **Migration note:** Both releases are patch-level (security hardening). No breaking changes reported. Operators running cloud workers or exposing browser endpoints should upgrade promptly.

---

## 3. Project Progress

**Notable merged/closed items today:**

| PR | Summary | Status |
|---|---|---|
| [#119520](https://github.com/openclaw/openclaw/pull/119520) | `fix(cron): remove deleted job sessions` — cleaned up stale `agent:<agent>:cron:<jobId>` base sessions after cron deletion | ✅ Merged |
| [#119511](https://github.com/openclaw/openclaw/pull/119511) | `fix(sessions): archive cron-run transcripts pruned by tasks maintenance` — addresses [#119269](https://github.com/openclaw/openclaw/issues/119269) | ✅ Closed |
| [#120017](https://github.com/openclaw/openclaw/pull/120017) | `fix(qa): reset Matrix chunk limit between scenarios` — fixes QA scenario isolation bug | ✅ Ready |
| [#120813](https://github.com/openclaw/openclaw/pull/120813) | `fix(mistral): reset transcription state after reconnect` — prevents partial transcript bleed across WebSocket reconnects | ✅ Closed |
| [#120802](https://github.com/openclaw/openclaw/pull/120802) | `fix(windows): preserve configured child env overrides across key casing` — fixes env variable casing bug on Windows | ✅ Closed |

**Actively advanced features:**
- **Code Mode trace preservation** — a cluster of PRs (#120361, #120360, #119892, #120821, #120819, #120818, #120823) is hardening the Code Mode execution trace schema, ensuring causal repair, authenticated dispatch, and auditable frontier evidence.
- **Device pairing** — PR #120768 introduces one-paste `oc-pair` setup links; #120825 adds a non-secret connectivity preflight.
- **Session resume from CLI** — PR #120664 adds `openclaw resume` to attach the TUI to a recent session without knowing the raw session key.

---

## 4. Community Hot Topics

| Issue | Title | Comments | Status |
|---|---|---|---|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | DeepSeek v4 Flash silent reply failure — no reply generated | 179 | ✅ Closed |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Feature Request: Memory Trust Tagging by Source | 31 | 🟡 Open |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent completion silently lost — no retry, no notification | 24 | 🟡 Open |
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | Gateway Memory Leak — RSS grows to 15.5 GB, OOM crashes | 22 | 🟡 Open |
| [#80319](https://github.com/openclaw/openclaw/issues/80319) | QA tool-defaults suite conflates Codex-native tools with OpenClaw parity | 17 | 🟡 Open |

**Analysis:**
- The **top discussion (#116277)** around DeepSeek silent failures reflects ongoing model-provider reliability concerns. The community is increasingly sensitive to "no reply" fallback messages that obscure root-cause.
- **#7707 (Memory Trust Tagging)** has been open since February with 31 comments — users want defense against memory-poisoning attacks from untrusted sources (web scrapes, third-party skills). This signals a maturing security-conscious user base.
- **#91588 (Gateway memory leak)** and **#44925 (subagent completion loss)** are both P1/P0 severity and reflect systemic reliability gaps in long-running production deployments.

---

## 5. Bugs & Stability

| Issue | Severity | Summary | Fix PR? |
|---|---|---|---|
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | 🔴 P0 — Platinum Hermit | Gateway RSS leaks from 350 MB → 15.5 GB over 2–3 days; OOM killer restarts loop | No known fix yet |
| [#108435](https://github.com/openclaw/openclaw/issues/108435) | 🔴 P0 — Gold Shrimp | Gateway fails to start after upgrade to 2026.7.1; `gateway did not start` error | No known fix yet |
| [#112395](https://github.com/openclaw/openclaw/issues/112395) | 🔴 P0 — Diamond Lobster | Startup migration preflight blocks gateway after 6.11→7.1 upgrade; migration tables empty | No known fix yet |
| [#109145](https://github.com/openclaw/openclaw/issues/109145) | 🟠 P1 — Silver Shellfish | Gateway HTTP server listens but does not accept connections (2026.7.1-beta.5) | No known fix yet |
| [#86215](https://github.com/openclaw/openclaw/issues/86215) | 🟠 P1 — Platinum Hermit | Codex OAuth refresh failures wedge agent for hours without alerting | No known fix yet |
| [#106231](https://github.com/openclaw/openclaw/issues/106231) | 🟠 P1 — Diamond Lobster | Loop detection blocks exec but does not terminate stuck agent run | No known fix yet |
| [#93917](https://github.com/openclaw/openclaw/issues/93917) | 🟠 P1 — Diamond Lobster | `genericRepeat` circuit-breaker never fires when exec results vary slightly | No known fix yet |
| [#87327](https://github.com/openclaw/openclaw/issues/87327) | 🟠 P1 — Diamond Lobster | Isolated agent runs stall in `runtime-plugins` phase before execution | No known fix yet |
| [#96692](https://github.com/openclaw/openclaw/issues/96692) | 🟠 P1 — Platinum Hermit | Slack thread replies generated but not delivered after origin tuple lost | No known fix yet |
| [#114020](https://github.com/openclaw/openclaw/issues/114020) | 🟠 P1 — Platinum Hermit | Feishu/Telegram dispatch fails: `runDispatchLifecycle` required after 2026.7.2-beta.4 upgrade | No known fix yet |

> **Pattern:** The dominant failure mode across P0/P1 issues is **session-state loss** — silent completions, wedged OAuth, stuck runs, and migration breakage. The 2026.7.x upgrade path appears particularly fragile (issues #108435, #112395, #114020 all trace to 7.x upgrades). The maintainers should consider a stabilization release before pushing further 7.x features.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Comments | Likely Next-Version Candidate? |
|---|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Memory Trust Tagging by Source | 31 | ⭐ High — security-hardening trend aligns with recent release focus |
| [#10687](https://github.com/openclaw/openclaw/issues/10687) | Fully dynamic model discovery (OpenRouter + beyond) | 10 | Medium — depends on provider catalog stability |
| [#13219](https://github.com/openclaw/openclaw/issues/13219) | Per-model usage logging for cost tracking | 7 | ⭐ High — widely requested by production operators |
| [#73537](https://github.com/openclaw/openclaw/issues/73537) | Production-readiness stability label for releases | 7 | Medium — governance/meta request |
| [#52640](https://github.com/openclaw/openclaw/issues/52640) | Persistent task-status surface for long-running turns | 7 | Medium — Discord-first, generic later |
| [#8299](https://github.com/openclaw/openclaw/issues/8299) | Config option to suppress sub-agent announce | 8 | ⭐ High — directly addresses reported annoyance (#84583) |
| [#71195](https://github.com/openclaw/openclaw/issues/71195) | OpenAI Realtime (speech-to-speech) for Talk Mode | 6 | Medium — parity feature vs. voice-call plugin |

**Prediction:** Memory Trust Tagging (#7707) and per-model usage logging (#13219) are the strongest roadmap signals given the project's current security-and-observability momentum. Sub-agent announce suppression (#8299) is a low-effort, high-impact config addition that could ship quickly.

---

## 7. User Feedback Summary

**Pain points:**
- **Silent data loss** is the #1 complaint — messages that "succeed" but never reach the user (WhatsApp #96834, WeChat #92199, Slack #96692, Feishu #108265, subagent completions #44925/#92076).
- **Upgrade breakage** — multiple users report that moving to 2026.7.x causes gateway startup failure (#108435, #112395) or dispatch regressions (#114020). The 7.x release train is creating friction.
- **Memory bloat** — long-running gateways leak RSS to 10–15 GB (#91588, #87109), requiring manual restarts.
- **Streaming UX degradation** — Feishu streaming "dribbles" characters slowly after 7.1 upgrade (#108265).
- **Compaction loops** — safeguard compaction can enter infinite retry with no circuit breaker (#118923), wedging sessions until `/new`.
- **Positive:** The new security hardening in 6.33/6.34 is well-received; users appreciate visible response-size caps and credential exclusion from diagnostics.

---

## 8. Backlog Watch

| Issue | Age | Why It Matters |
|---|---|---|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Open since Feb 2026 (6 months) | Memory poisoning defense — security-critical, no maintainer review yet |
| [#91588](https://github.com/openclaw/openclaw/issues/91588) | Open since Jun 2026 (2 months) | P0 memory leak; 15.5 GB RSS kills gateways in production |
| [#10687](https://github.com/openclaw/openclaw/issues/10687) | Open since Feb 2026 (6 months) | Dynamic model discovery — core platform capability gap |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Open since Mar 2026 (5 months) | Subagent completion loss — no retry, no notification, no auto-restart |
| [#86215](https://github.com/openclaw/openclaw/issues/86215) | Open since May 2026 (3 months) | OAuth wedging with no alerting — P1 availability risk |
| [#80319](https://github.com/openclaw/openclaw/issues/80319) | Open since May 2026 (3 months) | QA suite conflation — blocks confident Codex parity claims |

> **Recommendation:** The maintainers should prioritize **#91588 (memory leak)** and **#7707 (trust tagging)** — one is a production stability block, the other is a forward-looking security feature with strong community demand. The 2026.7.x upgrade issues (#108435, #112395, #114020) should be treated as release-blockers before further 7.x versions ship.

---

*Generated from GitHub data as of 2026-08-09. Source: [github.com/openclaw/openclaw](https://github.com/openclaw/openclaw)*

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — AI Agent & Personal AI Assistant Open-Source Ecosystem
**Date:** 2026-08-09

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape in mid-2026 is characterized by a maturing "Claw" ecosystem dominating production deployments, alongside specialized agents (Hermes, LobsterAI, Moltis, CoPaw) targeting distinct architecture and workflow niches. Security hardening and deployment reliability have become the primary community demands across all active projects, with session-state loss, credential leakage, and upgrade fragility emerging as universal pain points. The ecosystem is splitting between monolithic gateway architectures (OpenClaw, ZeroClaw, IronClaw) and modular channel/plugin-driven designs (NanoBot, NanoClaw, PicoClaw), while MCP adoption has become a table-stakes integration layer across nearly every project.

---

## 2. Activity Comparison

| Project | Open Issues | 24h Updated | Open PRs | 24h PR Updates | Releases (24h) | Health Score |
|---|---|---|---|---|---|---|
| **OpenClaw** | 448 | 500 | 325 | 500 | 2 (v2026.6.33/34) | 🟡 Stressed — P0 leaks & upgrade breakage |
| **Hermes Agent** | 39 | 50 | 43 | 50 | 0 | 🟡 Active but stressed — desktop instability |
| **ZeroClaw** | ~50* | 50 | ~50* | 50 | 0 | 🟡 High velocity, refinement phase |
| **CoPaw** | ~19* | 19 | ~50* | 50 | 0 | 🟢 High velocity, multi-platform |
| **IronClaw** | ~24* | 30 | ~32* | 32 | 0 | 🟢 High velocity, Reborn architecture |
| **NanoClaw** | 5 | 8 | 3 | 6 | 0 | 🟢 Active, integration-heavy |
| **NanoBot** | 5 | 5 | 9 | 9 | 0 | 🟡 Moderate — critical bugs unpatched |
| **PicoClaw** | 3 | 3 | 4 | 4 | 0 | 🟢 Steady maintenance |
| **LobsterAI** | 1 | 1 | 3 | 3 | 0 | 🟢 Stable, low velocity |
| **Moltis** | 2 | 2 | 1 | 1 | 0 | 🟢 Stabilization phase |
| **NullClaw** | — | 0 | — | 0 | 0 | 🔴 Inactive |
| **ZeptoClaw** | — | 0 | — | 0 | 0 | 🔴 Inactive |

*\*Estimated from digest text; exact open counts not always stated.*

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Release cadence is unmatched.** Two patch releases in 24 hours focused on security hardening; no other project shipped releases today. This signals a production-grade operation with a dedicated security response pipeline.
- **Scale of community.** 448 open issues and 325 open PRs dwarf all other projects combined, indicating the largest user base and contributor pool in the ecosystem.
- **Security-first iteration.** The v2026.6.33/34 releases (response-size caps, credential exclusion, DNS allowlists) directly address the security paranoia that permeates community discussions across *all* projects — OpenClaw is proactively solving problems others are still reporting.

**Technical approach differences:**
- OpenClaw operates as a **monolithic gateway** with embedded browser, cron, OAuth, and multi-channel dispatch — a "batteries included" architecture versus NanoClaw's plugin-driven MCP-first model or IronClaw's Reborn turn model.
- Its session-state and compaction focus (5 P0/P1 issues around silent data loss) reflects the complexity cost of its all-in-one design, whereas modular projects (PicoClaw, NanoBot) avoid this by keeping channels and agents decoupled.

**Community size comparison:**
- OpenClaw (~450+ open issues) → Hermes (~40) → ZeroClaw/CoPaw (~20-50) → NanoClaw/NanoBot (~5-10) → PicoClaw/LobsterAI/Moltis (<5) → NullClaw/ZeptoClaw (inactive). OpenClaw's community is roughly **10× larger** than the next-tier projects.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Need |
|---|---|---|
| **MCP stability & remote support** | NanoBot, NanoClaw, Hermes, ZeroClaw, IronClaw | Remote HTTP/SSE MCP servers, crash isolation on upstream failure, zombie process accumulation |
| **Session-state reliability** | OpenClaw, Hermes, ZeroClaw, NanoBot | Silent completion loss, stuck runs, compaction loops, stale session overwrites |
| **Security hardening** | OpenClaw, Hermes, ZeroClaw, IronClaw | Credential redaction bypasses, forbidden-path enforcement, approval authorization in group channels |
| **Token/cost observability** | NanoBot, ZeroClaw, LobsterAI | Per-iteration token diagnostics, budget-cap enforcement, provider cost tracking |
| **Docker/deployment reliability** | NanoBot, PicoClaw, CoPaw, ZeroClaw, Moltis | Permission issues, filesystem locks, sandbox state detection, gateway binding |
| **Channel parity & UX** | OpenClaw, NanoClaw, ZeroClaw, IronClaw, CoPaw | Streaming UX, approval workflows, typing indicators, attachment handling |
| **Upgrade path stability** | OpenClaw, Hermes | Migration breakage, gateway startup failure post-upgrade, dispatch regressions |
| **Desktop/CLI stability** | Hermes, CoPaw, ZeroClaw | Update brick rate, duplicate process spawning, SIGBUS crashes |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | IronClaw | ZeroClaw | NanoClaw | NanoBot | PicoClaw | LobsterAI | Moltis | CoPaw |
|---|---|---|---|---|---|---|---|---|---|---|
| **Core Architecture** | Monolithic gateway | Desktop-first agent | Reborn turn model | Plugin egress policy | MCP-native, channel plugin | WebUI + lightweight gateway | Minimal IRC/WhatsApp | LiteLLM gateway wrapper | Docker sandbox runtime | Multi-provider agent framework |
| **Target User** | Production operators, DevOps | Power users, desktop users | Early Reborn adopters | Security-conscious operators | Integration builders | Developers, token-conscious users | IRC/WhatsApp minimalists | Enterprise AI gateway users | Container sandbox users | Multi-agent, multi-provider teams |
| **Key Differentiator** | Security hardening velocity | v0.20 session write-policy | Model-driven skill activation | RFC-governed architecture | Remote MCP + Strava skill | Per-iteration token logs | Low footprint, IRC focus | Zero-dependency LiteLLM | Cross-runtime sandbox (Docker + Apple) | Scroll memory, mission mode |
| **Channel Strategy** | 15+ native channels | 10+ channels + desktop | Web + Slack + Telegram + web-push | Telegram + web + Discord | Slack, Discord, Telegram, Mattermost | WebUI + select channels | IRC, WhatsApp, Deltachat, SimpleX | LiteLLM provider routing | Docker, Apple Container | Docker, macOS, Windows |
| **Release Cadence** | Aggressive (2 patches/day) | Stabilization-focused | High velocity, no releases yet | Feature accumulation phase | Integration bursts | Steady, no releases | Slow maintenance | Minimal, stable | Stabilization | High velocity, no releases |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (High Activity, Production Focus):**
- **OpenClaw** (500 updates/24h, 2 releases) — The ecosystem's workhorse. Shipping security patches at production velocity but strained by P0 memory leaks and 7.x upgrade fragility. Maturity signal: strong release discipline, but architectural debt in session state.
- **ZeroClaw** (50/50 updates, RFC-driven) — Governance-mature project. The RFC process (#8692, #9496) and security hardening (#9815, #9387) suggest a project past the "move fast" phase and into "move carefully" territory.
- **IronClaw** (30/50 updates, Reborn architecture) — High velocity with architectural ambition. The Reborn turn model and Inspector debugging tools signal a project reinventing its core, not just iterating.

**Tier 2 — Active Development (Moderate-High, Feature Growth):**
- **CoPaw** (19/50 updates) — Multi-platform momentum. Docker, macOS, Windows all in flight; provider expansion (Volcengine, Xiaomi MiMo) signals ecosystem play.
- **NanoClaw** (8/6 updates) — Integration-focused growth. Remote MCP and Strava skill show community-driven expansion.
- **Hermes Agent** (50/50 updates) — Security audit catching systemic issues. The desktop update trauma (#81969) is a trust risk despite high contributor engagement.

**Tier 3 — Steady Maintenance (Low-Moderate, Niche Focus):**
- **NanoBot** (5/9 updates) — Token observability focus. The community self-solved its top pain point via PR #5293, but Docker and MCP crash bugs remain.
- **PicoClaw** (3/4 updates) — Minimalist channel focus. WhatsApp fix (#3320) and IRC long-message support (#3287) are the immediate priorities.
- **LobsterAI** (1/3 updates) — Stable but slow. LiteLLM addition is the most significant recent change; SQLite perf fix (#1193) long-pending.
- **Moltis** (2/1 updates) — Sandbox specialization. Docker fix merged; Apple Container state-detection (#1185) is the next hurdle.

**Tier 4 — Inactive:**
- **NullClaw, ZeptoClaw** — No activity. Likely dormant or abandoned.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Security hardening is table-stakes** | OpenClaw (6.33/34), Hermes (redaction bypasses), ZeroClaw (forbidden_paths, approval auth), IronClaw (SafetyLayer gap) | New agents must bake in credential scoping, path isolation, and approval authorization from day one — not as add-ons |
| **MCP is the integration standard** | NanoClaw (remote HTTP/SSE), NanoBot (budget-aware schemas), Hermes (cold-spawn stalls), ZeroClaw (zombie processes) | Remote MCP support and failure isolation are now expected; stdio-only is a limitation |
| **Token/cost observability is a top-3 feature request** | NanoBot (per-iteration logs), ZeroClaw ($0.00 Anthropic spend bug), OpenClaw (per-model usage logging #13219) | Developers should ship granular cost tracking as a first-class feature; users will not tolerate invisible bill shock |
| **Session-state reliability is the #1 production risk** | OpenClaw (silent loss #44925), Hermes (stale saves), ZeroClaw (SOP stuck), NanoBot (race condition) | Any agent framework claiming production readiness must guarantee at-least-once delivery and handle compaction without data loss |
| **Docker/container deployment friction is universal** | NanoBot (permission denied), NanoClaw (SQLite locks), Moltis (sandbox I/O), CoPaw (Docker maintenance mode), ZeroClaw (loopback binding) | First-class container support with filesystem-aware SQLite configuration is a differentiator, not optional |
| **Channel parity drives adoption** | ZeroClaw (OpenAI-compatible endpoint #8550), NanoClaw (Mattermost), IronClaw (web-push), CoPaw (Volcengine/Xiaomi) | Supporting well-known channels (Slack, Telegram, Discord) and OpenAI-compatible APIs is essential for ecosystem interoperability |
| **Desktop update reliability erodes trust fast** | Hermes (#81969 brick rate, #75778 duplicate processes), CoPaw (SIGBUS on macOS) | Desktop-first agents must invest in atomic updates and rollback; one bad update cycle can permanently lose users |
| **RFC/governance maturity correlates with project longevity** | ZeroClaw (active RFC queue), IronClaw (ADR-013), OpenClaw (implicit) | Projects with formal design review processes (ZeroClaw's #8692) are better positioned to handle scale without architectural collapse |

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-09

## 1. Today's Overview

NanoBot saw moderate activity on 2026-08-09 with 5 open issues and 9 pull requests updated in the last 24 hours. No new releases were published. The project is actively addressing token-usage observability, Docker deployment bugs, and MCP (Model Context Protocol) stability — all critical infrastructure concerns. Four PRs were merged/closed today, indicating steady contributor momentum.

## 2. Releases

No new releases today.

## 3. Project Progress

**Merged/Closed PRs (4):**

- **[PR #5252](https://github.com/HKUDS/nanobot/pull/5252)** — `feat(webui): add temporary chat mode` — Added a temporary, non-persistent chat mode for the WebUI hero section, supporting multiple concurrent temp sessions without history files.
- **[PR #5293](https://github.com/HKUDS/nanobot/pull/5293)** — `feat(usage): log per-iteration token diagnostics` — Addresses [issue #5266](https://github.com/HKUDS/nanobot/issues/5266) by persisting per-iteration token usage records alongside daily aggregates.
- **[PR #5296](https://github.com/HKUDS/nanobot/pull/5296)** — `refactor: remove verified dead code` — Cleaned up 19 dead-code units and 11 orphaned test seams; preserves 6 API-sensitive units pending maintainer decision.
- **[PR #5294](https://github.com/HKUDS/nanobot/pull/5294)** — `fix(webui): prevent image hover clipping` — Fixed CSS clipping on assistant image previews by removing hover scaling/ring while retaining zoom cursor and focus-visible ring.

## 4. Community Hot Topics

- **[Issue #5266](https://github.com/HKUDS/nanobot/issues/5266)** — *Logs about token consumption* (13 comments, created 2026-08-06) — The most-discussed issue. Users are reporting excessive token burn (millions in hours) with no visibility into which calls drive consumption. Directly addressed by merged PR #5293.
- **[Issue #5298](https://github.com/HKUDS/nanobot/issues/5298)** — *Budget model-visible MCP schemas for large tool sets* — Proposes limiting MCP tool schemas sent to the LLM to reduce context cost. Reflects growing adoption of large MCP tool collections and the need for cost-aware routing.
- **[PR #5299](https://github.com/HKUDS/nanobot/pull/5299)** — *Show recent token usage details* (open) — Companion to #5266/#5293; adds a bounded list of recent per-call token records to the WebUI.

**Underlying need:** Token-cost transparency is a top community priority. Both feature and bug reports converge on the same pain point — users lack granular visibility into per-call/token consumption.

## 5. Bugs & Stability

| Severity | Item | Details | Fix PR |
|----------|------|---------|--------|
| 🔴 High | [Issue #5300](https://github.com/HKUDS/nanobot/issues/5300) — MCP crash on remote failure | Remote MCP returning HTTP 530 triggers `anyio` cancel-scope cross-task error, causing gateway process crash, task leaks, and CPU spike. | No open fix PR yet |
| 🟠 Medium | [Issue #5295](https://github.com/HKUDS/nanobot/issues/5295) — Docker deploy permission denied | `docker compose` deployment fails with `/usr/local/bin/entrypoint.sh: Permission denied`. Blocks first-time Docker users. | No open fix PR yet |
| 🟡 Low | [PR #5271](https://github.com/HKUDS/nanobot/pull/5271) — Stale background task overwrites session data | P0-priority race condition: `/new` during `await provider.chat_with_retry` can cause a stale session save to overwrite new data. Still open with conflicts. | PR #5271 (open, in review) |
| 🟡 Low | [PR #5206](https://github.com/HKUDS/nanobot/pull/5206) — Streamed responses logged twice | Duplicate log lines for every streamed message. P2 priority, still open with conflicts. | PR #5206 (open, in review) |

## 6. Feature Requests & Roadmap Signals

- **[Issue #5266 / PR #5293 / PR #5299](https://github.com/HKUDS/nanobot/issues/5266)** — Token-per-iteration diagnostics. Likely already shipping with the merged #5293; #5299 adds the WebUI view. **High confidence for next release.**
- **[Issue #5297](https://github.com/HKUDS/nanobot/issues/5297)** — MCP OAuth web authorization (e.g., XMind MCP requires browser SSO). Requested via gateway-based remote auth flow. **Plausible for near-term roadmap.**
- **[Issue #5298](https://github.com/HKUDS/nanobot/issues/5298)** — Budget-aware MCP schema visibility. Suggests a model-configurable tool set for large MCP collections. **Feature-request level; depends on maintainer bandwidth.**
- **[PR #4276](https://github.com/HKUDS/nanobot/pull/4276)** — Model-agnostic computer use (PyAutoGUI + Playwright backends). Open since 2026-06-10 with no merge yet. **Long-pending; high interest but not yet merged.**
- **[PR #5292](https://github.com/HKUDS/nanobot/pull/5292)** — Matrix room-level reply threading. Small but usability improvement for Matrix integration. **Likely low-hanging fruit for next patch.**

## 7. User Feedback Summary

- **Token cost anxiety is dominant.** Multiple users report unexplained million-token burns in idle hours, and the lack of per-call diagnostics makes debugging impossible. The community has responded with both a bug report (#5266) and two feature PRs (#5293, #5299), suggesting strong demand.
- **Docker deployment is a friction point.** Issue #5295 blocks new users from getting started with containerized deployments — a basic onboarding blocker.
- **MCP stability under failure is fragile.** Issue #5300 shows that a single upstream MCP failure (HTTP 530) cascades into a full gateway crash with resource leaks. This indicates insufficient error isolation for multi-tenant or production deployments.
- **Temporary chat mode (PR #5252)** was well-received enough to be merged — users want lightweight, non-persistent conversation modes.
- **No overt dissatisfaction signals** beyond the technical issues above; overall sentiment appears constructive.

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| [PR #4276](https://github.com/HKUDS/nanobot/pull/4276) — Computer use tools | Open since 2026-06-10 (~60 days) | High-interest feature stalled; needs maintainer review. |
| [PR #5271](https://github.com/HKUDS/nanobot/pull/5271) — Stale session save race | P0, open with conflicts | Critical bug with no merge yet; conflicts may block resolution. |
| [PR #5206](https://github.com/HKUDS/nanobot/pull/5206) — Duplicate stream logging | P2, open with conflicts | Low severity but easy fix; conflicts may be minor. |
| [Issue #5295](https://github.com/HKUDS/nanobot/issues/5295) — Docker entrypoint permission | Open, 1 day old | Onboarding blocker; likely a 1-line fix, should be triaged quickly. |
| [Issue #5300](https://github.com/HKUDS/nanobot/issues/5300) — MCP crash + task leak | Open, 1 day old | Production-reliability risk; no fix PR yet despite clear reproduction. |

---

**Project Health:** 🟡 Moderate. Strong contributor activity on observability and WebUI polish, but two critical bugs (Docker deploy, MCP crash) and a long-pending feature PR need maintainer attention before the next release.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-09

## 1. Today's Overview

Hermes Agent is experiencing **very high activity** with 50 issues and 50 PRs updated in the last 24 hours, of which 39 issues remain open and 43 PRs are still open. No new releases were published today, suggesting the team is focused on stabilizing the codebase rather than shipping. Activity is dominated by desktop update regressions, security hardening, and gateway reliability fixes. The project shows strong community engagement with multiple contributors filing defense-in-depth security reports and bug fixes in parallel.

## 2. Releases

**No new releases today.** The absence of a release despite 50+ active PRs suggests the maintainers are either in a stabilization phase or batching changes for an upcoming release.

## 3. Project Progress

### Merged/Closed Items Today

- **#82158** [CLOSED] — Fixed a critical Desktop update blocker on Windows where the venv-blocker scan truncated command lines, causing false positives that aborted every update cycle. ([PR #82158](https://github.com/NousResearch/hermes-agent/pull/82158))
- **#80943** [CLOSED] — Session write-policy propagation and enforcement across delegated child agents, Copilot ACP subprocess spawn, and cleanup paths completed. All C19 contract tests pass (9/9). ([PR #80943](https://github.com/NousResearch/hermes-agent/pull/80943))
- **#79723** [CLOSED] — Reconstructed the v0.20 session write-policy migration on `upstream/main` with 29 paths scanned; 27 had effective diffs. Preserves fail-closed session-write behavior. ([PR #79723](https://github.com/NousResearch/hermes-agent/pull/79723))
- **#73624** [CLOSED] — Fixed context compression budget accounting: stale reasoning tokens were incorrectly charged to the compression tail budget, wasting 19–24% of allocated budget on blocks no adapter replays. ([PR #73624](https://github.com/NousResearch/hermes-agent/pull/73624))
- **#82160** [CLOSED] — Codex thread persistence: fixed issue where agent re-instantiation created a new thread instead of resuming the persisted one, losing thread identity across gateway restarts. ([PR #82160](https://github.com/NousResearch/hermes-agent/pull/82160))
- **#79343** [CLOSED] — Memory gate now correctly treats mid-task workflow commands (e.g., "continue", "proceed", "done") as non-trivial, preventing skipped provider recall during active workflows. ([PR #79343](https://github.com/NousResearch/hermes-agent/pull/79343))
- **#79325** [CLOSED] — SiliconFlow provider was missing from `PROVIDER_TO_MODELS_DEV`, causing the model picker to always render an empty list. Fixed. ([PR #79325](https://github.com/NousResearch/hermes-agent/pull/79325))
- **#72337** [CLOSED] — Cron job delivery UI now supports multi-select checkboxes instead of single-select dropdown, allowing users to deliver to both local and chat targets simultaneously. ([PR #72337](https://github.com/NousResearch/hermes-agent/pull/72337))

### Open PRs Advancing Today

- **#82163** — CLI: fences OSC 11 background query with DA1 to prevent terminal reply bytes from leaking into the prompt. Salvages PR #40262.
- **#82162** — Gateway: preserves MEDIA delivery on queued follow-up responses across all platforms, fixing silent attachment drops. Salvages PR #71031.
- **#81929** — Agent/cron: declares skill cache boundaries on messages, preventing Anthropic from rewriting entire expanded skill blocks on every webhook/cron invocation.
- **#82157** — Delegation: adds per-child `child_memory` and toolset permission boundary for subagents.
- **#82152** — Search: strips FTS5 special characters (`it's`, `50%`, `user@host`) that caused silent zero-result queries. Salvages PR #79285.
- **#82151** — Security: routes all model-switch credential lookups through per-profile secret scope, preventing cross-profile API key leakage under multiplexed profiles.
- **#82143** — Desktop (Windows): self-heals missing `get-windows` win32 binding; addresses root cause of PR #81969.
- **#81709** — Telegram: adds bidirectional contextual reactions (users can react to agent messages and agent receives them with target context).
- **#80475** — MCP: adds deterministic `hermes mcp fixtures record/replay` for real protocol coverage without mocks.
- **#82153** — xAI OAuth: refreshes credentials on 403 `unauthenticated:bad-credentials` (was misclassified as non-retryable).

## 4. Community Hot Topics

| Issue/PR | Comments | Focus |
|---|---|---|
| [#78515](https://github.com/NousResearch/hermes-agent/issues/78515) — Skills guard content scan bypass | 6 | Security hardening: agent-authored skills bypass `Skills Guard` by default and enter every session's system prompt. Filed per `SECURITY.md` §3.2. |
| [#40801](https://github.com/NousResearch/hermes-agent/issues/40801) — Cron script-path guard inverse bug | 6 | Profile-scoped cron jobs rejecting scripts from the default profile's `scripts/` dir. Inverse of #32091. |
| [#81969](https://github.com/NousResearch/hermes-agent/issues/81969) — Desktop update brick rate | 6 | Users report repeated update failures causing data loss and reconfiguration fatigue. High emotional intensity. |
| [#75778](https://github.com/NousResearch/hermes-agent/issues/75778) — Duplicate `hermes-setup` on macOS update | 6 | Desktop update spawns two `hermes-setup` processes; second fails against first's marker, masking the real running update. |
| [#70846](https://github.com/NousResearch/hermes-agent/issues/70846) — Compaction erases human-visible history | 5 | Context compaction wipes message history for humans too, breaking long-conversation traceability. 👍1 |

**Analysis:** The dominant themes are **trust and reliability** — users are frustrated by update breakage and data loss, while security-conscious contributors are proactively hardening the skills system. The compaction bug (#70846) reflects a genuine UX gap where agent-internal optimization silently degrades human experience.

## 5. Bugs & Stability

### P0 / Critical

| Issue | Summary | Fix PR |
|---|---|---|
| [#81969](https://github.com/NousResearch/hermes-agent/issues/81969) | Windows desktop `hermes update` bricks on repeated failures; `get-windows` npm binding missing | [#82143](https://github.com/NousResearch/hermes-agent/pull/82143) (open) |
| [#75778](https://github.com/NousResearch/hermes-agent/issues/75778) | macOS Desktop update spawns duplicate `hermes-setup`, second fails and hides real update | — |

### P1 / High

| Issue | Summary | Fix PR |
|---|---|---|
| [#81995](https://github.com/NousResearch/hermes-agent/issues/81995) | Stalled stdio MCP cold-spawn: in-flight tool call attached to dead subprocess for full 300s timeout, no fail-fast | — |
| [#81162](https://github.com/NousResearch/hermes-agent/issues/81162) | Auto voice reply blocks text response on slow TTS backends (synchronous TTS in gateway) | — |
| [#70846](https://github.com/NousResearch/hermes-agent/issues/70846) | Compaction erases human-visible message history | — |
| [#63386](https://github.com/NousResearch/hermes-agent/issues/63386) | FTS index corruption in `state.db` on macOS; `hermes doctor` reports write-health probe failure | [#82152](https://github.com/NousResearch/hermes-agent/pull/82152) (salvage, open) |
| [#40801](https://github.com/NousResearch/hermes-agent/issues/40801) | Cron script-path guard rejects valid profile-scoped jobs referencing default-profile scripts | — |

### P2 / Medium

| Issue | Summary | Fix PR |
|---|---|---|
| [#41225](https://github.com/NousResearch/hermes-agent/issues/41225) | Background terminal processes killed by SIGTERM during agent `release()` | — |
| [#39245](https://github.com/NousResearch/hermes-agent/issues/39245) | ACP `prompt` hangs after final text when `usage_update` doesn't return | — |
| [#57240](https://github.com/NousResearch/hermes-agent/issues/57240) | Forked sessions double-encode reasoning columns, silently losing reasoning replay | — |
| [#77833](https://github.com/NousResearch/hermes-agent/issues/77833) | Kanban WS handler leaks poll tasks on disconnect → 100%+ CPU | — |
| [#82074](https://github.com/NousResearch/hermes-agent/issues/82074) | Podman + SELinux: auto-mounted skills dir inaccessible without `:z` | — |
| [#81430](https://github.com/NousResearch/hermes-agent/issues/81430) | `hermes memory status` reports disabled despite memory injection enabled on Telegram | — |
| [#81012](https://github.com/NousResearch/hermes-agent/issues/81012) | ANSI CSI/SGR sequences defeat token redaction — vendor API keys leak entirely | — |
| [#80966](https://github.com/NousResearch/hermes-agent/issues/80966) | Env keys without secret keywords (e.g., `SPOTIFY_CLIENT_ID`) leak through all redaction passes | — |

**Stability Assessment:** The project has **significant desktop update and credential-redaction instability**. Two security issues (#81012, #80966) from the same author suggest a coordinated audit is uncovering systemic redaction gaps. The Windows update brick rate (#81969) is the most user-impactful bug and has an open salvage PR (#82143).

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Description | Likelihood for Next Release |
|---|---|---|
| [#82165](https://github.com/NousResearch/hermes-agent/issues/82165) | Spanish locale for Desktop app | Medium — small i18n addition |
| [#49103](https://github.com/NousResearch/hermes-agent/issues/49103) | Unified Cmd+K search across files, sessions, skills | Medium — non-trivial scope |
| [#78307](https://github.com/NousResearch/hermes-agent/issues/78307) | Memory lifecycle management UX (dedup, health, conflict detection) | Medium — scoped to memory subsystem |
| [#35573](https://github.com/NousResearch/hermes-agent/issues/35573) | ToolCallStormBreaker — suppress repeated tool-call loops | Low-Medium — RFC stage |
| [#14859](https://github.com/NousResearch/hermes-agent/issues/14859) | Show session title in CLI/TUI status bar | Medium — small UI addition |
| [#82157](https://github.com/NousResearch/hermes-agent/pull/82157) | Per-child memory & toolset permission boundary for delegation | **High** — already in PR, aligns with v0.20 session write-policy work |
| [#81709](https://github.com/NousResearch/hermes-agent/pull/81709) | Telegram bidirectional reactions | **High** — already in PR, feature-complete |
| [#81439](https://github.com/NousResearch/hermes-agent/pull/81439) | Configurable human-facing timestamps | Medium — display-only, no backend impact |

**Roadmap Signal:** The v0.20 session write-policy migration (#79723, #80943) is the largest structural effort and appears to be the centerpiece of the next release. Per-child delegation boundaries (#82157) and Telegram reactions (#81709) are the most advanced feature PRs.

## 7. User Feedback Summary

- **Desktop update trauma is real.** Issue #81969 carries significant emotional weight — users report losing configurations repeatedly and explicitly state it's eroding trust in the product. This is the #1 satisfaction risk.
- **Compaction silently breaks usability.** Issue #70846 highlights a class of bugs where agent-internal optimizations (context compression) degrade the human-visible experience without warning.
- **Security audit feedback is constructive.** Issues #78515, #81012, and #80966 come from a contributor (`EvolveAegis`/`kshitijk4poor`) following the project's own `SECURITY.md` §3.2 process — they're filing defense-in-depth notes, not exploit claims. This is a healthy signal.
- **MCP reliability concerns.** Issue #81995 (300s stall on cold-spawn) and #82074 (Podman/SELinux mount issues) indicate the Docker/MCP integration is a pain point for power users running containerized workflows.
- **Platform parity gaps.** Users are hitting inconsistencies across Telegram (#81430 memory status mismatch), cron (#40801 profile scoping), and desktop (#75778 duplicate processes).

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|---|---|---|
| [#75778](https://github.com/NousResearch/hermes-agent/issues/75778) — Duplicate `hermes-setup` on macOS | 8 days | No fix PR yet. Directly causes update failures; same class as Windows #81969. |
| [#41225](https://github.com/NousResearch/hermes-agent/issues/41225) — Background processes killed on `release()` | 63 days | Long-open; affects terminal tool users. No fix PR. |
| [#39245](https://github.com/NousResearch/hermes-agent/issues/39245) — ACP prompt hang after final response | 66 days | No fix PR. Impacts Copilot ACP users. |
| [#57752](https://github.com/NousResearch/hermes-agent/issues/57752) — Session DB auto-prune+VACUUM opt-in only | 67 days | No fix PR. Causes unbounded `state.db` growth. |
| [#77833](https://github.com/NousResearch/hermes-agent/issues/77833) — Kanban WS handler CPU leak | 37 days | Sustained 100%+ CPU in production. No fix PR. |
| [#35573](https://github.com/NousResearch/hermes-agent/issues/35573) — ToolCallStormBreaker RFC | 71 days | No fix PR. Affects token efficiency and user frustration. |
| [#80966](https://github.com/NousResearch/hermes-agent/issues/80966) + [#81012](https://github.com/NousResearch/hermes-agent/issues/81012) — Redaction bypasses | 2 days each | Coordinated security audit findings. No fix PRs yet; high priority given same author. |

**Overall Project Health:** **Active but stressed.** The maintainers are processing a high volume of community contributions (many salvage PRs from community authors), but critical desktop stability and security redaction gaps remain unpatched. The v0.20 session write-policy work is the most significant structural change and should stabilize delegation behavior. The Windows update brick rate (#81969) and macOS duplicate-process bug (#75778) are the highest-impact outstanding issues for end users.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-09

## 1. Today's Overview

PicoClaw shows moderate daily activity with 3 updated issues and 4 open pull requests in the last 24 hours, and no new releases. The project is in a steady maintenance phase — there are no merged PRs or closed releases today, but a mix of bug fixes, dependency updates, and feature work is actively in review. Community engagement remains low on recent items (zero reactions across all open issues and PRs), though the diversity of topics (IRC, OAuth, CPU optimization, WhatsApp compatibility) signals a broad and growing user base.

## 2. Releases

No new releases were published today.

## 3. Project Progress

No PRs were merged and no issues were closed today. Four open PRs remain under review:

- **PR #3320** — Dependency bump for `whatsmeow` to resolve WhatsApp connectivity failures.
- **PR #3321** — Fixes prefix caching behavior by reordering dynamic context relative to conversation history.
- **PR #3222** — Major cleanup of the Deltachat implementation, removing ~200 lines of legacy code.
- **PR #3193** — Introduces a new SimpleX channel type.

These represent incremental improvements and infrastructure maintenance rather than major feature launches.

## 4. Community Hot Topics

| Item | Type | Comments | Updated | Link |
|------|------|----------|---------|------|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) | Feature | 4 | 2026-08-08 | Long IRC message support |
| [#3302](https://github.com/sipeed/picoclaw/issues/3302) | Feature | 2 | 2026-08-08 | OAuth 2.1 for MCP servers |
| [#3292](https://github.com/sipeed/picoclaw/issues/3292) | Bug | 2 | 2026-08-08 | High CPU on input focus |

**Analysis:** Issue #3287 (long IRC messages) has the most discussion, reflecting a genuine pain point for users who rely on PicoClaw for IRC-based AI interactions. The 512-byte IRC limit causes message fragmentation that breaks conversational coherence — a limitation that becomes more acute as model responses grow longer. Issue #3302 signals growing interest in MCP (Model Context Protocol) server authentication, suggesting the community is adopting more sophisticated agent integrations. Issue #3292, now closed, addressed a noticeable performance regression in the web UI.

## 5. Bugs & Stability

| Severity | Item | Status | Details |
|----------|------|--------|---------|
| Medium | [#3292](https://github.com/sipeed/picoclaw/issues/3292) | ✅ **Closed** | High CPU usage when the chat input box is focused, reported on Firefox/Linux with Go 1.26 and deepseek-v4-flash. Closed as of 2026-08-08. |
| High | [#3320](https://github.com/sipeed/picoclaw/pull/3320) | 🔄 Open PR | WhatsApp channel dies with "Client outdated (405)" error; PR bumps `whatsmeow` dependency to restore connectivity. |

The WhatsApp issue is the most critical open stability concern — it completely breaks one of PicoClaw's most-used channels. A fix is already in progress via PR #3320.

## 6. Feature Requests & Roadmap Signals

| Item | Description | Alignment | Link |
|------|-------------|-----------|------|
| [#3287](https://github.com/sipeed/picoclaw/issues/3287) | Support long messages in IRC (fragment/reassemble) | Core Feature | [Issue](https://github.com/sipeed/picoclaw/issues/3287) |
| [#3302](https://github.com/sipeed/picoclaw/issues/3302) | OAuth 2.1 support for MCP servers | Nice-to-Have / Enhancement | [Issue](https://github.com/sipeed/picoclaw/issues/3302) |
| PR #3193 | New SimpleX channel type | New feature | [PR](https://github.com/sipeed/picoclaw/pull/3193) |
| PR #3222 | Deltachat cleanup & modernization | Refactor | [PR](https://github.com/sipeed/picoclaw/pull/3222) |

**Prediction:** The next release is likely to include PR #3320 (WhatsApp fix) and PR #3321 (caching fix), as both address blocking issues. Long IRC message support (#3287) is a strong candidate for a future feature release given its Core Feature tag and active discussion. OAuth 2.1 for MCP (#3302) is lower priority but aligns with the broader trend of strengthening agent authentication.

## 7. User Feedback Summary

- **IRC users** are frustrated by message truncation — long AI responses are split by IRC's 512-byte limit, destroying conversational continuity. This is a growing concern as model outputs increase in length.
- **WhatsApp users** are experiencing complete channel failure due to an outdated client version string. This is a blocking issue for anyone relying on the WhatsApp integration.
- **Web UI users** reported and experienced a CPU spike when focusing the chat input, now resolved.
- Overall satisfaction signals are neutral-to-positive: bugs are being addressed, new channel types are being added, and dependency updates are proactive. However, the zero-reaction count across all items suggests a quiet community that may not be fully engaged with the issue/PR system.

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [PR #3193](https://github.com/sipeed/picoclaw/pull/3193) — SimpleX channel type | ~43 days open, stale | New channel type that could broaden PicoClaw's reach; needs review and merge. |
| [PR #3222](https://github.com/sipeed/picoclaw/pull/3222) — Deltachat cleanup | ~37 days open, stale | Significant refactor that improves maintainability; low risk, high reward. |
| [Issue #3287](https://github.com/sipeed/picoclaw/issues/3287) — Long IRC messages | ~18 days open, stale | Core feature request with active discussion but no implementation yet. |
| [Issue #3302](https://github.com/sipeed/picoclaw/issues/3302) — OAuth 2.1 for MCP | ~10 days open, stale | Niche but growing in relevance as MCP adoption increases. |

**Recommendation:** Maintainers should prioritize reviewing PRs #3193 and #3222 (low-risk, high-value) and PR #3320 (blocking bug fix). Issue #3287 would benefit from a concrete implementation proposal to move it out of "stale."

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-09

## 1. Today's Overview

NanoClaw is showing **active development velocity** with 8 issues and 6 pull requests updated in the last 24 hours. Three issues and three pull requests were closed today, while five open issues and three open PRs remain for community review. No new releases were published, suggesting this is a maintenance-and-integration-heavy day rather than a release cycle. Project health indicators are strong: bugs are being fixed, integrations are expanding, and community contributors remain engaged.

## 2. Releases

No new releases published today.

---

## 3. Project Progress

### Closed / Merged PRs

- **[#2777 — feat: add /add-strava skill for official Strava MCP](https://github.com/nanocoai/nanoclaw/issues/2777)** ✅ Merged
  One of the two long-awaited PRs from contributor clementdecoligny. Adds an `/add-strava` skill wiring the official Strava MCP endpoint (`https://mcp.strava.com/mcp`) into agent groups via HTTP transport, complete with a host-side OAuth flow and auto-refreshing token module. This expands the skill library with a real-world fitness integration.

- **[#2776 — feat: support remote HTTP/SSE MCP servers](https://github.com/nanocoai/nanoclaw/issues/2776)** ✅ Merged
  Complements the Strava skill by extending `McpServerConfig` to a union type supporting both stdio (existing) and remote HTTP/SSE MCP servers. Adds `McpServerRemoteConfig` with `type`, `url`, `headers`, and optional `instructions` fields, and updates the CLI (`ncl groups config add-mcp-server`) accordingly. This is a **significant architectural improvement** enabling remote MCP server integrations beyond local stdio-only setups.

- **[#3199 — Add Mattermost channel integration (v2 ChannelAdapter)](https://github.com/nanocoai/nanoclaw/issues/3199)** ✅ Closed
  Fresh implementation against the current `ChannelAdapter`/`channel-registry.ts` contract, superseding the stale #546. Wraps the community [`chat-adapter-mattermost`](https://github.com/thiagoferolla/chat-adapter-mattermost) package. Though now closed, PR #3202 appears to be the active continuation (see Bugs & Stability).

### Open PRs Under Review

- **[#3202 — Add Mattermost channel integration](https://github.com/nanocoai/nanoclaw/pull/3202)** 🔶 Open
  Appears to be the refined follow-up to #3199, adding Mattermost as a Chat SDK channel following the `slack.ts` pattern.
- **[#3185 — fix(discord): strip `\n` delimiter in webhook interaction custom_id](https://github.com/nanocoai/nanoclaw/pull/3185)** 🔶 Open
  Addresses the Discord approval rejection bug (see Bugs & Stability).
- **[#2877 — feat(telegram): native rich rendering via Bot API 10.1 sendRichMessage](https://github.com/nanocoai/nanoclaw/pull/2877)** 🔶 Open
  Long-standing feature PR for Telegram rich message rendering.

---

## 4. Community Hot Topics

| Item | Type | Comments | Key Theme |
|------|------|----------|-----------|
| [#3200](https://github.com/nanocoai/nanoclaw/issues/3200) | Issue | 1 | Persona/identity framing for external cognitive architecture |
| [#3201](https://github.com/nanocoai/nanoclaw/issues/3201) | Issue | 2 | Discord approval button clicks not registering |
| [#3177](https://github.com/nanocoai/nanoclaw/issues/3177) | Issue | 1 | SQLite lock contention on Docker cross-mount filesystems |
| [#3185](https://github.com/nanocoai/nanoclaw/pull/3185) | PR | — | Discord custom_id stripping fix |
| [#2776](https://github.com/nanocoai/nanoclaw/issues/2776) | PR | — | Remote MCP server support |

**Analysis:** The Discord approval bug (#3201) and its associated fix PR (#3185) are the hottest topic, with 2 comments. This indicates users are actively relying on approval workflows in Discord and the bug has high operational impact. The remote MCP server feature (#2776) is generating interest as it unlocks integrations beyond local stdio-only MCPs. The Docker SQLite lock contention (#3177) reflects a growing adoption pattern where NanoClaw is being run in containerized environments on non-native filesystems.

---

## 5. Bugs & Stability

### 🔴 Critical

**[#3201 — Discord approval button clicks not registering](https://github.com/nanocoai/nanoclaw/issues/3201)** (CLOSED ✅)
Owner-role users cannot approve config update requests via Discord approval cards. Cards display "0 by [user]" even after clicking Approve, and requests are subsequently rejected. A fix PR exists: **[#3185](https://github.com/nanocoai/nanoclaw/pull/3185)** — strips the `\n` delimiter in webhook interaction `custom_id` so approvals resolve correctly.

**[#3206 — Inbound attachments silently dropped on channels with path separators in message IDs](https://github.com/nanocoai/nanoclaw/issues/3206)** (OPEN)
`extractAttachmentFiles` in `src/session-manager.ts` rejects any message ID containing `/` or `\`, causing attachments on Google Chat (and potentially other channels) to be silently dropped with no error. Severity is high for multi-channel deployments.

### 🟠 High

**[#3203 — codex provider emits undeclared `file` ProviderEvent](https://github.com/nanocoai/nanoclaw/issues/3203)** (OPEN)
The codex provider emits a `file` event not declared in `ProviderEvent`, causing `/add-codex` to fail the container typecheck on `main`. Even when compiled, generated images are silently dropped (no consumer). Affects multi-provider type safety.

**[#3204 — add-opencode skill references removed Dockerfile patterns](https://github.com/nanocoai/nanoclaw/issues/3204)** (OPEN)
`.claude/skills/add-opencode/SKILL.md` still instructs editing `container/Dockerfile` with `ARG` + `RUN pnpm install -g` layers that no longer exist after the `cli-tools.json` refactor. The skill's own guard test asserts the old shape. This creates a broken onboarding experience for new users.

### 🟡 Medium

**[#2528 — Signal channel: image/PDF attachments unreachable from agent container](https://github.com/nanocoai/nanoclaw/issues/2528)** (OPEN, since 2026-05-18)
Images and PDFs sent over Signal arrive at the host but the agent inside the container cannot open them. Open for ~3 months with no fix in progress.

**[#3177 — SQLite session database lock contention on Docker cross-mount filesystems](https://github.com/nanocoai/nanoclaw/issues/3177)** (CLOSED ✅)
Resolved by DawoudIO. Session databases (`inbound.db`, `outbound.db`) experienced 29,000+ readonly errors on Docker-mounted filesystems (macOS/Linux) due to SQLite DELETE journal mode not propagating across VirtioFS mounts. Closed today — fix is likely in the same PR cycle.

---

## 6. Feature Requests & Roadmap Signals

- **[#3205 — Support persistent group-scoped OneCLI secret assignment](https://github.com/nanocoai/nanoclaw/issues/3205)** (OPEN)
  Multi-user NanoClaw has two contradictory open directions for spawn-time secret assignment with no persistent per-group model. This unresolved design fork is a clear roadmap signal — the maintainers need to commit to one approach. Likely candidate for next release architecture work.

- **[#2877 — Telegram native rich rendering via Bot API 10.1 sendRichMessage](https://github.com/nanocoai/nanoclaw/pull/2877)** (OPEN, since 2026-06-28)
  Long-standing PR for rich message rendering on Telegram. Has been open for ~6 weeks with no merge. Suggests the Telegram channel may be a lower priority for maintainers, or the PR may need rework.

- **[#3202 — Mattermost channel integration](https://github.com/nanocoai/nanoclaw/pull/3202)** (OPEN)
  New channel integration following the Slack pattern. The rapid iteration between #3199 (closed) and #3202 (open) suggests active maintainer feedback on the approach. Likely to land in an upcoming release.

**Prediction:** The next release will likely include the Mattermost integration, the Discord approval fix, and possibly remote MCP server configuration refinements. The OneCLI secret assignment design decision is the most significant unresolved roadmap item.

---

## 7. User Feedback Summary

**Pain Points:**
- **Discord approval workflow is broken** for owner-role users — approval cards show zero votes even after clicking Approve, causing automatic rejection. This directly blocks admin workflows.
- **Attachments are silently lost** on Google Chat (and potentially other channels with path-separated message IDs) and Signal, with no user-visible error. Users report confusion when attachments "don't work."
- **The add-opencode skill is outdated** — it guides users to edit Dockerfile patterns that no longer exist, creating a broken first-run experience.
- **Codex integration is non-functional** on `main` due to a typecheck failure from an undeclared `file` ProviderEvent.

**Positive Signals:**
- The Strava MCP integration and remote HTTP/SSE MCP server support (both merged today) address real user demand for expanding integrations beyond local stdio MCPs.
- Docker/container deployment is a growing use case, as evidenced by the SQLite lock contention fix (#3177) and multiple channel integration PRs.

---

## 8. Backlog Watch

| Issue | Open Since | Severity | Status |
|-------|-----------|----------|--------|
| [#2528 — Signal attachments unreachable](https://github.com/nanocoai/nanoclaw/issues/2528) | 2026-05-18 (~3 months) | Medium | No fix in progress |
| [#2877 — Telegram rich rendering](https://github.com/nanocoai/nanoclaw/pull/2877) | 2026-06-28 (~6 weeks) | Feature | Open, no merge |
| [#3205 — Persistent group-scoped OneCLI secrets](https://github.com/nanocoai/nanoclaw/issues/3205) | 2026-08-08 | Design | Unresolved design fork |
| [#3203 — Codex `file` ProviderEvent undeclared](https://github.com/nanocoai/nanoclaw/issues/3203) | 2026-08-08 | High | No fix PR yet |
| [#3206 — Attachments dropped on path-separator message IDs](https://github.com/nanocoai/nanoclaw/issues/3206) | 2026-08-08 | Critical | No fix PR yet |

**Maintainer Attention Needed:**
- **#3205** requires a design decision — the project has two contradictory open directions for secret assignment and needs closure.
- **#3206** and **#3203** are high-impact bugs with no fix PRs yet. The attachment dropping issue affects any channel using path-separated message IDs (Google Chat is confirmed; others may be affected).
- **#2528** has been open for 3 months with no activity — a stale but important Signal integration bug.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-09

## 1. Today's Overview

IronClaw is experiencing **high development velocity** with 30 issues and 50 PRs updated in the past 24 hours. The project is in an active integration and hardening phase around the Reborn architecture, with significant closures (24 issues, 32 PRs) indicating strong forward momentum. No new releases were published. Community contributors are increasingly active, and security/observability work is maturing alongside channel feature expansion.

## 2. Releases

No new releases published.

## 3. Project Progress

**Merged/Closed PRs today:**

- **[PR #7377](https://github.com/nearai/ironclaw/pull/7377)** — *feat!: a run acts as its invoker* — Consolidated run identity semantics across three split surfaces and folded in a full multi-agent audit hardening pass. This is a foundational behavior change for the Reborn turn model.
- **[PR #7382](https://github.com/nearai/ironclaw/pull/7382)** — *feat(stress): scripted tool-call workload* — Phase 1 of stress coverage (issue #7360): mock LLM now drives deterministic builtin/memory tool sequences with durable write read-back verification.
- **[PR #7280](https://github.com/nearai/ironclaw/pull/7280)** — *test(inspector): browser, security, and operator coverage* — Completed security and operator authorization testing for the Web Debug Inspector.
- **[PR #7393](https://github.com/nearai/ironclaw/pull/7393)** — *test(disclosure): wide-catalog benchmark* — Added Core-tier delivery pair benchmarks following #7390.
- **[PR #7389](https://github.com/nearai/ironclaw/pull/7389)** — *fix(live-qa): Slack delivery verification* — Fixed a live-qa lane regression where delivery cases broke after #7157 removed the `triggered-run-delivery` completion record.
- **[PR #6938](https://github.com/nearai/ironclaw/pull/6938)** — *fix(skills): model chooses the skill, not keyword scorer* — The host no longer scores and activates skills; the LLM model decides via `builtin.skill_activate`.

## 4. Community Hot Topics

| Item | Type | Activity | Link |
|------|------|----------|------|
| **Web Debug Inspector** | Epic + multiple PRs | High — #7218 (epic), #7291 (stats/navigation), #7225 (tool details), #7226 (browser/security docs) | [#7218](https://github.com/nearai/ironclaw/issues/7218) |
| **Legacy migration tool** | Feature request | High community need — users resist clean-slate switching | [#6939](https://github.com/nearai/ironclaw/issues/6939) |
| **Web push notifications** | Feature PR | New first-party channel parity with Slack/Telegram | [#7398](https://github.com/nearai/ironclaw/pull/7398) |
| **Stress coverage expansion** | Enhancement | Addressing gap where built-in capability write regressions could slip through | [#7360](https://github.com/nearai/ironclaw/issues/7360) |
| **Progressive previews for Slack** | Feature | Channel-neutral preview contract mapped to Slack streaming APIs | [#7396](https://github.com/nearai/ironclaw/pull/7396) |

**Analysis:** The Inspector epic reflects growing operator demand for debugging tooling as Reborn matures. The migration pain point (#6939) signals that early adopters of legacy products (Hermes/Openclaw) need a real onboarding path. Channel parity work (web-push, Slack previews) shows deliberate product expansion beyond core messaging.

## 5. Bugs & Stability

| Severity | Issue/PR | Description | Fix Status |
|----------|----------|-------------|------------|
| 🔴 **High** | [#6989](https://github.com/nearai/ironclaw/issues/6989) | `ModelWorkRequest::for_assistant` estimates tokens from content-reference string length instead of actual content — affects pi-harness adoption | Open, P1 |
| 🟠 **Medium** | [#7391](https://github.com/nearai/ironclaw/issues/7391) | `SafetyLayer::validate_input` / `scan_inbound_for_secrets` have **no caller** on the live Reborn turn path — security docs describe the flow but it's unimplemented | Open, unassigned |
| 🟠 **Medium** | [#7395](https://github.com/nearai/ironclaw/pull/7395) | TOCTOU race in `claim_delivery_attempt_for_send` — claim loser could misclassify sending rows | PR open (#7395) |
| 🟡 **Low** | [#7352](https://github.com/nearai/ironclaw/pull/7352) | Gate projection identities not bound to their gate ref — multiple gates on same run derive identical projection ID | PR open (#7352) |
| 🟡 **Low** | [#7341](https://github.com/nearai/ironclaw/pull/7341) | WebUI attachment read regression from SSE migration | PR merged (#7341) |

**Notable:** The security gap in #7391 is critical — the documented "Validate, Sanitize, Detect Leaks" pipeline has no active caller on the production turn path.

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Next Release |
|---------|--------|----------------------------|
| **Migration tool for legacy agents** | [#6939](https://github.com/nearai/ironclaw/issues/6939) | Medium-high — clear user demand, high switching-cost pain |
| **Web Debug Inspector** | [#7218](https://github.com/nearai/ironclaw/issues/7218) | High — already partially shipped via inspector PRs |
| **Replace coding tools with pinned OMP surface** | [#7392](https://github.com/nearai/ironclaw/issues/7392) | Medium — epic opened, tied to pi-harness adoption |
| **Web push notification channel** | [#7398](https://github.com/nearai/ironclaw/pull/7398) | High — PR is open, W3C spec-compliant, parity with existing channels |
| **Slack/Telegram progressive previews** | [#7396](https://github.com/nearai/ironclaw/pull/7396) | Medium — channel feature, depends on preview contract stability |
| **Full Reborn approvals parity** | [#4539](https://github.com/nearai/ironclaw/issues/4539) | Medium — closed as done, but follow-up work may remain |

## 7. User Feedback Summary

- **Migration friction is real:** Multiple users report high switching costs from Hermes/Openclaw to IronClaw with no path to carry over configuration and memory. This is the most frequently cited pain point (#6939).
- **Debugging opacity:** The Inspector feature (#7218) emerged from operator need to see prompt construction, tool execution, and model usage in real time — previously unavailable.
- **Skill activation confusion:** The shift from keyword-scoring to model-driven skill selection (#6938) suggests users were experiencing unpredictable skill behavior under the old system.
- **Notification parity expectation:** Web push support (#7398) indicates users expect IronClaw to match Slack/Telegram notification capabilities natively.
- **Stress test confidence:** The push for scripted tool-call workloads (#7360, #7382) reflects community concern that regressions in built-in capability writes were going undetected.

## 8. Backlog Watch

| Issue | Age | Priority | Risk |
|-------|-----|----------|------|
| [#6989](https://github.com/nearai/ironclaw/issues/6989) — Token accounting bug | 8 days | P1 | pi-harness adoption blocked |
| [#7391](https://github.com/nearai/ironclaw/issues/7391) — SafetyLayer unimplemented | 1 day | P0 (security) | Security docs-vs-reality gap |
| [#7392](https://github.com/nearai/ironclaw/issues/7392) — Replace coding tools with OMP | 1 day | Epic | Depends on pi-harness timeline |
| [#3484](https://github.com/nearai/ironclaw/issues/3484) — Reborn Contributor Runway | ~3 months | Epic | Parallel porting infrastructure |
| [#4539](https://github.com/nearai/ironclaw/issues/4539) — Reborn approvals parity | ~2 months | Epic | Closed but may have unaddressed follow-ups |

**Key concern:** Issue #7391 (SafetyLayer) was reported today and represents a gap between documented security architecture and live implementation. This warrants immediate maintainer attention. Issue #6989 (token estimation) is a P1 blocking pi-harness adoption and has been open for over a week.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-09

---

## 1. Today's Overview

LobsterAI shows **low but steady activity** as of 2026-08-09, with 1 open issue and 3 PRs updated in the last 24 hours. No new releases were published. The project maintains a small contributor base with occasional community-driven improvements — a merged PR adding LiteLLM gateway support and two open PRs addressing performance and documentation. The single open issue reflects a recurring user pain point around tool configuration flexibility rather than stability concerns. Overall, the project appears to be in a **maintenance and incremental enhancement phase**, with no critical blockers reported.

---

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Project Progress

**Merged today:**

- **[PR #2193](https://github.com/netease-youdao/LobsterAI/pull/2193) — feat: add LiteLLM as AI gateway provider** (closed/merged)
  - Author: RheagalFire
  - Adds LiteLLM as a configurable AI gateway, enabling access to 100+ LLM providers through a single OpenAI-compatible endpoint. No new dependencies — reuses the existing `chatWithOpenAICompatible` handler. This expands the project's model flexibility significantly at zero dependency cost.

**Open PRs awaiting review/merge:**

- **[PR #1193](https://github.com/netease-youdao/LobsterAI/pull/1193) — perf(sqlite): eliminate write amplification with debounce + batch transactions**
  - Author: Housum
  - Addresses a performance bottleneck where every SQLite row mutation triggered a full `db.export()` + `fs.writeFileSync()` of the in-memory database. This is a meaningful optimization for users with high-frequency agent interactions.

- **[PR #2294](https://github.com/netease-youdao/LobsterAI/pull/2294) — docs: add TakoAPI directory badge**
  - Author: oratis
  - Documentation-only PR adding a discovery badge linking to the TakoAPI agent catalog.

---

## 4. Community Hot Topics

| Topic | Link | Analysis |
|-------|------|----------|
| **Custom default config for existing tools** (Issue #1192) | [#1192](https://github.com/netease-youdao/LobsterAI/issues/1192) | The most discussed open issue. A user requests the ability to hardcode default configurations for built-in tools (e.g., headless mode for the browser tool) rather than relying on LLM instruction-following, which is unreliable. This signals a broader community need for **deterministic tool configuration** that doesn't depend on model behavior. |

The issue has been open since April 2026 with stale labeling, indicating it has received limited maintainer attention. The underlying need — **predictable tool behavior without LLM mediation** — likely extends beyond the browser headless use case to other tools as well.

---

## 5. Bugs & Stability

No new bug reports, crashes, or regressions were filed in the last 24 hours. The project appears **stable** from a defect-reporting standpoint. The open performance issue in PR #1193 (SQLite write amplification) is not a crash but a scalability concern that could affect power users with heavy session activity.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Assessment |
|--------|--------|------------|
| **Deterministic tool default configuration** | Issue #1192 | Strong signal. Users want to override tool defaults at the config level without depending on LLM follow-through. Likely to appear in a future release as a "tool defaults" config section. |
| **Multi-provider gateway support** | PR #2193 (merged) | LiteLLM integration is now live. This may pave the way for additional gateway providers (e.g., local proxies, vLLM endpoints) in upcoming versions. |
| **SQLite performance hardening** | PR #1193 (open) | Debounce + batch transactions could become a standard pattern if merged, suggesting the roadmap prioritizes persistence-layer reliability. |

---

## 7. User Feedback Summary

- **Positive**: The LiteLLM gateway addition (PR #2193) was well-received by the community with zero reported downsides — it's a low-friction, high-value feature.
- **Pain point**: Users find **LLM-based tool configuration unreliable**. Issue #1192 highlights that even with memory/reminder features, the model frequently fails to honor headless-mode instructions for the browser tool. Users want **explicit, hardcoded defaults** as a more dependable alternative.
- **Satisfaction**: No complaints or dissatisfaction signals were detected in the current data. The project's direction (gateway flexibility, performance tuning) aligns with user expectations.

---

## 8. Backlog Watch

| Item | Open Since | Severity | Notes |
|------|-----------|----------|-------|
| [Issue #1192](https://github.com/netease-youdao/LobsterAI/issues/1192) — Custom tool default configs | 2026-04-01 | Medium | Stale label applied. High community relevance; the need for non-LLM-mediated tool defaults is likely to grow as the project attracts more power users. |
| [PR #1193](https://github.com/netease-youdao/LobsterAI/pull/1193) — SQLite write amplification fix | 2026-04-01 | Medium | Performance fix with clear root-cause analysis. Awaiting maintainer review; merging would improve experience for users with large in-memory databases. |

Both items have been open since early April 2026. Maintainer attention to these would significantly improve the project's reliability and configurability for advanced users.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-09

## 1. Today's Overview

Moltis showed moderate maintenance activity over the past 24 hours, with two issues updated and one pull request closed. The project appears to be in a stabilization phase, with efforts focused on Docker sandbox reliability rather than new feature development. No new releases were published, suggesting the team is addressing backend infrastructure concerns before pushing a version update. Overall project health is stable, with active community engagement on sandbox-related bugs.

## 2. Releases

No new releases were published during this reporting period.

## 3. Project Progress

**Closed/Merged PR:**

- **[PR #1105](https://github.com/moltis-org/moltis/pull/1105)** — *Fix Docker sandbox filesystem tool fallback* (author: penso)
  - Added regression coverage for sandboxed Read/Write/Edit/MultiEdit operations on `/home/sandbox` and `workspace/data` paths
  - Implemented a fallback mechanism translating Docker host paths to container operations when the gateway process cannot access the host mount
  - Preserved direct-host missing-list semantics while improving reliability in Docker-sandboxed environments
  - **Impact:** Resolves [Issue #1096](https://github.com/moltis-org/moltis/issues/1096), restoring core filesystem tool functionality for Docker-based sandbox users

## 4. Community Hot Topics

**Most Discussed Issue:**

- **[Issue #1185](https://github.com/moltis-org/moltis/issues/1185)** — *Apple Container 1.x sandbox starts but Moltis treats it as not running* (open, author: mikz, created 2026-08-08)
  - **Analysis:** This bug indicates a state-detection or health-check mismatch in the Apple Container runtime integration. Users expect Moltis to accurately reflect the running state of sandboxed environments, and this discrepancy could prevent debugging workflows from functioning correctly. Low comment/reaction volume suggests the issue was just filed and may still be gathering attention.

- **[Issue #1096](https://github.com/moltis-org/moltis/issues/1096)** — *`Read`/`Write`/`Edit` tools don't work in Docker* (closed 2026-08-08, author: IlyaBizyaev)
  - **Analysis:** This was a high-impact bug affecting core filesystem operations in Docker sandboxes. Its resolution via PR #1105 demonstrates active maintainer responsiveness. The two-month gap between creation (2026-06-03) and closure (2026-08-08) suggests this was a non-trivial fix requiring careful fallback logic.

**Underlying Need:** The community is clearly focused on **sandbox reliability across runtime environments** (Docker, Apple Container). Filesystem operations are fundamental to agent workflows, and failures here block core use cases. Future investment in cross-platform sandbox state management is likely.

## 5. Bugs & Stability

| Rank | Issue | Severity | Status | Fix |
|------|-------|----------|--------|-----|
| 1 | [#1185](https://github.com/moltis-org/moltis/issues/1185) — Apple Container sandbox running but reported as stopped | **High** (runtime state detection) | 🔴 Open | None yet |
| 2 | [#1096](https://github.com/moltis-org/moltis/issues/1096) — Docker `Read`/`Write`/`Edit` tools broken | **High** (core filesystem tools) | ✅ Closed | [PR #1105](https://github.com/moltis-org/moltis/pull/1105) merged |

**Note:** Issue #1185 represents an active regression in Apple Container integration and should be prioritized, as sandbox state detection is critical for agent session reliability.

## 6. Feature Requests & Roadmap Signals

No explicit feature requests were filed today. However, the resolution of Docker sandbox filesystem issues and the emergence of Apple Container state-detection problems signal that **multi-runtime sandbox support** is a near-term roadmap priority. A forthcoming release may include:

- Improved sandbox health-check and state-tracking across Docker and Apple Container runtimes
- Expanded regression test coverage for sandboxed I/O operations

## 7. User Feedback Summary

- **Pain Point (resolved):** Docker sandbox users could not perform basic file operations (`Read`/`Write`/`Edit`), blocking development and debugging workflows. This has been addressed.
- **Pain Point (active):** Apple Container 1.x users report that sandboxes which clearly start successfully are incorrectly flagged as not running by Moltis. This creates confusion and blocks session continuity.
- **Satisfaction Signal:** The quick closure of Issue #1096 with a thorough fix (including regression tests) indicates positive maintainer-community dynamics for infrastructure bugs.

## 8. Backlog Watch

| Issue | Age | Priority |
|-------|-----|----------|
| [#1185](https://github.com/moltis-org/moltis/issues/1185) — Apple Container sandbox state detection failure | 1 day (as of report date) | 🔴 **High** — Needs maintainer triage to prevent session reliability issues for Apple Container users |

**Recommendation:** Maintainers should prioritize investigating the Apple Container runtime integration, as state-detection bugs undermine trust in the sandboxing layer. Consider adding explicit health-check logging or diagnostics to help users and developers troubleshoot runtime mismatches.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026‑08‑09

## 1. Today's Overview
CoPaw (agentscope‑ai/CoPaw) shows **high development velocity** with 19 issues and 50 pull requests updated in the last 24 hours. No new releases were published today. Activity is dominated by bug fixes for Docker, macOS, and Windows desktop clients, alongside several feature requests for provider support, UI improvements, and agent lifecycle management. The project remains actively maintained with a steady stream of community contributions.

## 2. Releases
*No new releases today.*

## 3. Project Progress
- **Closed Issues:** #6756 (`run_tool_batch` toolkit‑context error) and #4558 (high CPU during long text output) were closed today.
- **Merged/Closed PRs:** 3 PRs were merged or closed today (details not fully enumerated in the provided data).
- **Key Advances (Open PRs):**
  - **#6824** – Fixes Scroll recall correctness for CJK searches.
  - **#6536** – Ensures chat deletion cleans up persisted data.
  - **#5861** – Resolves login‑shell PATH for macOS desktop backend.
  - **#6569** – Suppresses EIO/EPIPE errors after detached TTY.
  - **#6652** – Enforces `max_iterations` server‑side in Mission mode.
  - **#6041** – Exempts read‑only tools from doom‑loop detection.
  - **#6381** – Avoids blocking on stale MCP capabilities.

## 4. Community Hot Topics
*Issues with the most engagement (comments/reactions) highlight core user concerns:*

1. **#6782** – [Docker version plugin/marketplace stuck in maintenance](https://github.com/agentscope-ai/CoPaw/issues/6782) (9 comments)  
   *Users report that the Docker‑based QwenPaw consistently shows “under maintenance” for plugin and application markets.*
2. **#6811** – [OpenAI Responses continuation summary ignores `disable_thinking`](https://github.com/agentscope-ai/CoPaw/issues/6811) (5 comments)  
   *Scroll eviction triggers a blocking continuation summary that fails when reasoning is disabled.*
3. **#6490** – [Add Volcengine Agent Plan & Xiaomi MiMo as built‑in providers](https://github.com/agentscope-ai/CoPaw/issues/6490) (5 comments)  
   *Community requests official provider integrations for regional AI services.*
4. **#6820** – [Frontend UI does not display model output until completion](https://github.com/agentscope-ai/CoPaw/issues/6820) (4 comments)  
   *Streaming UI feedback is missing, breaking real‑time interaction expectations.*
5. **#6814** – [SIGBUS crash on macOS when opening Scroll history.db (WAL mode)](https://github.com/agentscope-ai/CoPaw/issues/6814) (3 comments)  
   *SQLite WAL page lookup crashes during history database access.*

**Underlying Needs:** Users demand stable cross‑platform deployment (Docker, macOS, Windows), real‑time streaming UI, provider flexibility, and robust error handling for edge‑case model interactions.

## 5. Bugs & Stability
*Bugs reported today, ranked by severity:*

| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **High** | #6814 | SIGBUS crash in SQLite WAL on macOS | None yet |
| **High** | #6822 | Transient MCP failure permanently blocks conversation | None yet |
| **High** | #6813 | `KeyError: '__aiter__'` breaks auto‑title generation | None yet |
| **Medium** | #6782 | Docker plugin/marketplace stuck in maintenance | None yet |
| **Medium** | #6811 | OpenAI summary ignores `disable_thinking` | None yet |
| **Medium** | #6828 | Idle frontend CSS animations cause ~20% CPU | None yet |
| **Medium** | #6831 | Local Whisper reports ffmpeg disabled on macOS | #5861 (open) |
| **Medium** | #6812 | Google API 400 due to `$schema` in tool definitions | None yet |
| **Low** | #6826 | Assistant message end‑time display incorrect | None yet |
| **Low** | #6819 | Channel tool does not prompt for approval | None yet |

## 6. Feature Requests & Roadmap Signals
*User‑requested enhancements and likely next‑version candidates:*

- **#6490** – Add Volcano Engine & Xiaomi MiMo providers.  
- **#6832** – Show a human‑readable description when AI requests approval. *(Highly plausible for next release.)*
- **#6827** – Option to clean up temporary files when deleting a chat.  
- **#6719** – Persistent workspace artifact cards in chat UI.  
- **#6771** – Embedding model configuration guide.  
- **#6398** – Reranker support for ReMe memory search.  
- **#6293** – Register `qwen3.8‑max‑preview` in Aliyun token plan.  

**Prediction:** Provider expansions, approval‑description UI, and chat‑deletion cleanup are strong candidates for the next minor release.

## 7. User Feedback Summary
- **Pain Points:**  
  - Docker deployment issues (plugin market broken).  
  - macOS/Windows desktop stability (SIGBUS, installer lock, ffmpeg detection).  
  - Frontend performance (CSS animation CPU drain, missing streaming).  
  - Model‑provider compatibility (OpenAI thinking‑mode, Gemini schema, MCP reconnection).  
  - Agent lifecycle (sub‑agent model switching, auto‑title generation failures).  
- **Satisfaction:** High engagement (many comments) indicates an active user base that relies on CoPaw for multi‑provider, multi‑agent workflows. Feature requests are specific and well‑scoped, suggesting mature usage patterns.

## 8. Backlog Watch
*Important open issues/PRs that have awaited maintainer attention for an extended period:*

- **#5861** – [fix(desktop): resolve login‑shell PATH for packaged macOS backend](https://github.com/agentscope-ai/CoPaw/pull/5861) (created 2026‑07‑08, 32 days open) – Critical for macOS desktop functionality.  
- **#5823** – [fix(feishu): send markdown images as image parts](https://github.com/agentscope-ai/CoPaw/pull/5823) (created 2026‑07‑07, 33 days open) – Impacts Feishu integration.  
- **#6102** – [test(isolation): boundary meta‑test pinning #5813 failure modes](https://github.com/agentscope-ai/CoPaw/pull/6102) (created 2026‑07‑14, 26 days open) – Improves test reliability.  
- **#6591** – [fix(scroll): retain active history sessions intact](https://github.com/agentscope-ai/CoPaw/pull/6591) (created 2026‑07‑30, 10 days open) – Affects Scroll memory retention logic.  
- **#6569** – [fix(console): suppress EIO/EPIPE print errors after detached TTY](https://github.com/agentscope-ai/CoPaw/pull/6569) (created 2026‑07‑30, 10 days open) – Console stability improvement.  
- **#6041** – [fix(loop): exempt read‑only tools from doom loop detection](https://github.com/agentscope-ai/CoPaw/pull/6041) (created 2026‑07‑13, 27 days open) – Prevents false‑positive loop termination.  

*Maintainers should prioritize these PRs, especially the macOS PATH fix and the Scroll retention update, which address core stability and memory‑management concerns.*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-09

## 1. Today's Overview

ZeroClaw is experiencing **high development velocity**, with 50 issues and 50 PRs updated in the last 24 hours. The project is in an active refinement phase: no new releases were published, but significant work is flowing through RFC discussion, security hardening, and channel improvements. The maintainers are heavily engaged on governance (RFC process streamlining, decision queues) and critical bug fixes around security policy, SOP execution, and cost tracking. Activity is concentrated on architecture, security, and channel layers — signaling a mature project addressing scale and reliability concerns.

## 2. Releases

**No new releases today.** The latest activity continues on `master`. The project appears to be accumulating fixes and features ahead of an upcoming release cycle.

## 3. Project Progress

### Merged / Closed
- **PR #9494** (CLOSED) — *fix(sop): drive cron-started headless runs* — A cron trigger previously stranded runs at `ExecuteStep` with no agent loop. The shared headless run driver now handles cron-initiated runs. **Superseded and continued by PR #9841**, which closes four additional review findings and one further defect.
- **PR #9798** (CLOSED) — *docs(sop): document which agent executes SOP steps* — Superseded by #9841 after the runtime fix changed the behavior being documented.

### Actively Advanced
- **PR #9841** — Canonical continuation fixing headless SOP run defects (P1). Drives runs that were previously stuck `running` forever.
- **PR #9822** — Telegram tool-progress in partial drafts, routing `update_draft_progress` into the draft-edit path.
- **PR #9823** — Pauses typing indicator during approval waits, fixing the misleading "working" UX during blocked turns.
- **PR #9828** — Agent-facing config authoring with operator-approved policy previews, replacing raw shell config writes.
- **PR #9744** — Authenticated webhook ingress requirement for gateway dispatch, adding a typed `VerifiedWebhookIngress` proof boundary.
- **PR #9580** — Network guard primitives moved to `zeroclaw-infra::net_guard` (Stage 1 of plugin egress policy, ADR-013).
- **PR #9571** — WATI channel removal completed (module, feature flag, gateway routes, CI, container, installer).
- **PR #9854** — Context-window discovery now derived from the family registry instead of a hard-coded provider list.

## 4. Community Hot Topics

| Issue/PR | Comments | Topic |
|----------|----------|-------|
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | 11 | Maintainer decision queue for RFCs and design issues |
| [#8043](https://github.com/zeroclaw-labs/zeroclaw/issues/8043) | 11 | RFC: Retire `aardvark-sys` crate (folded into `zeroclaw-hardware`) — **CLOSED** |
| [#8424](https://github.com/zeroclaw-labs/zeroclaw/issues/8424) | 11 | RFC: Workspace-relative forbidden paths + `.zeroclawignore` |
| [#8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) | 10 | System prompt tool availability mismatch across entry points |
| [#5514](https://github.com/zeroclaw-labs/zeroclaw/issues/5514) | 6 | Telegram batch media groups into one multimodal turn |
| [#8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550) | 6 | OpenAI-compatible chat completions endpoint |

**Analysis:** The top-voted discussions center on **governance process** (#8692, #9496), **security configuration** (#8424, #8054), and **channel UX polish** (#5514, #8550). The community is clearly pushing for more structured maintainer decision-making, tighter security boundaries for workspace-internal files, and better multi-channel parity. The OpenAI-compatible endpoint request (#8550) signals strong demand for ecosystem interoperability with tools like Open WebUI and LobeChat.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|----------|-------|---------|--------|
| **P1 / High** | [#9805](https://github.com/zeroclaw-labs/zeroclaw/issues/9805) | SOP auto-mode runs from channel/cron never execute; stuck `running` forever | #9841 (in progress) |
| **P1 / High** | [#9815](https://github.com/zeroclaw-labs/zeroclaw/issues/9815) | `forbidden_paths` unreachable under `allowed_roots` — security policy bypass | Pending |
| **P1 / High** | [#9816](https://github.com/zeroclaw-labs/zeroclaw/issues/9816) | Anthropic provider reports $0.00 spend; budget caps never fire | Pending |
| **P1 / High** | [#9390](https://github.com/zeroclaw-labs/zeroclaw/issues/9390) | Emergency stop is CLI-only; no runtime path reads the state file | Pending |
| **P1 / High** | [#9825](https://github.com/zeroclaw-labs/zeroclaw/issues/9825) | Leak detector redacts public blockchain addresses (false positive) | Pending |
| **P1 / High** | [#9387](https://github.com/zeroclaw-labs/zeroclaw/issues/9387) | Approval responses accepted from any chat member on Telegram/Slack/Lark/Matrix | Pending |
| **P1 / High** | [#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559) | Agents stop when user exits web dashboard chat window | Pending |
| **P1 / High** | [#8731](https://github.com/zeroclaw-labs/zeroclaw/issues/8731) | Stdio MCP servers accumulate as zombie processes | Pending |
| **P2 / Medium** | [#9486](https://github.com/zeroclaw-labs/zeroclaw/issues/9486) | High-entropy detector redacts Solana wallet addresses on Telegram | Pending |
| **P2 / Medium** | [#9656](https://github.com/zeroclaw-labs/zeroclaw/issues/9656) | Typing indicator runs during approval wait, misleads users | #9823 (in progress) |
| **P2 / Medium** | [#9340](https://github.com/zeroclaw-labs/zeroclaw/issues/9340) | CLI cron jobs have hardcoded `delivery.mode = "none"` | Pending |
| **P2 / Medium** | [#9035](https://github.com/zeroclaw-labs/zeroclaw/issues/9035) | Docker Compose gateway remains loopback-bound behind published port | Pending |
| **P2 / Medium** | [#9573](https://github.com/zeroclaw-labs/zeroclaw/issues/9573) | Cost pricing lookup fails for multiple aliases of same provider | Pending |
| **P3 / Minor** | [#9202](https://github.com/zeroclaw-labs/zeroclaw/issues/9202) | `zeroclaw desktop` uses dead download URL; doesn't detect AppImage | Pending |

**Key concern:** Six P1 issues remain open without assigned fix PRs, including two security-critical bugs (#9815, #9387) and a financial tracking failure (#9816). These should be prioritized for the next release.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Likelihood for Next Release |
|-------|---------|----------------------------|
| [#8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550) | OpenAI-compatible chat completions endpoint | **High** — strong ecosystem demand |
| [#8445](https://github.com/zeroclaw-labs/zeroclaw/issues/8445) | Telegram multi-message mode (one msg per turn) | **Medium** — incremental UX improvement |
| [#9845](https://github.com/zeroclaw-labs/zeroclaw/issues/9845) | Non-ASCII agent aliases (e.g. Chinese/Japanese) | **Medium** — configuration parity |
| [#9824](https://github.com/zeroclaw-labs/zeroclaw/issues/9824) | Simplify default web-tool surface to 3 verbs | **High** — already in progress, reduces tool confusion |
| [#8043](https://github.com/zeroclaw-labs/zeroclaw/issues/8043) | Retire `aardvark-sys`, fold into `zeroclaw-hardware` | **Done** — closed; #9803 continues same pattern for `zeroclaw-robot-kit` |
| [#6663](https://github.com/zeroclaw-labs/zeroclaw/issues/6663) | Telegram tool-call progress during partial streaming | **Medium** — #9822 addresses this |

**Roadmap signal:** The project is consolidating its tool surface (#9824), streamlining its RFC process (#9496, #8692), and removing legacy crates (`aardvark-sys`, `zeroclaw-robot-kit`, WATI channel). The next release will likely emphasize **security hardening, config authoring ergonomics, and channel UX polish** over new integrations.

## 7. User Feedback Summary

- **Security paranoia is healthy but sometimes overreaching:** Users report false positives from the high-entropy leak detector redacting public Solana wallet addresses and blockchain payment URLs (#9486, #9825). The detector works as designed but lacks nuance for public-on-chain data.
- **Approval UX is misleading:** The typing indicator running during approval waits makes blocked turns appear active (#9656), and approval responses are accepted from any chat participant on group channels (#9387) — a real security concern in shared workspaces.
- **SOP automation is broken for headless triggers:** Cron and channel-triggered SOPs in auto-mode run forever stuck at step 1 (#9805), rendering scheduled automation useless.
- **Cost tracking is unreliable:** Anthropic provider shows $0.00 spend (#9816), and multi-alias provider configs ignore token prices (#9573), making budget caps non-functional.
- **Web dashboard aborts agent work on exit:** Users cannot leave a task running while browsing files or stepping away (#8559).
- **Channel UX needs parity:** Requests for OpenAI-compatible endpoints (#8550), Telegram multi-message mode (#8445), and batch media grouping (#5514) all point to users wanting ZeroClaw to fit existing workflows rather than requiring custom integrations.

## 8. Backlog Watch

| Issue | Days Open | Why It Needs Attention |
|-------|-----------|----------------------|
| [#9815](https://github.com/zeroclaw-labs/zeroclaw/issues/9815) | 2 | `forbidden_paths` completely ineffective under `allowed_roots` — security policy bypass, P1 |
| [#9816](https://github.com/zeroclaw-labs/zeroclaw/issues/9816) | 2 | Budget caps non-functional on Anthropic; costs report $0.00 — P1 |
| [#9390](https://github.com/zeroclaw-labs/zeroclaw/issues/9390) | 14 | Emergency stop only works via CLI; runtime paths ignore the state file — P1, safety-critical |
| [#9387](https://github.com/zeroclaw-labs/zeroclaw/issues/9387) | 14 | Any chat member can approve on Telegram/Slack/Lark/Matrix — P1, authorization bypass |
| [#9805](https://github.com/zeroclaw-labs/zeroclaw/issues/9805) | 2 | SOP auto-mode from channel/cron stuck forever — P1, breaks scheduled automation |
| [#9496](https://github.com/zeroclaw-labs/zeroclaw/issues/9496) | 12 | RFC process too slow; broad unanimity requirements bottleneck decisions — architecturally important |
| [#8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) | 50 | System prompt tool mismatch across gateway/WebSocket/multimodal entry points — P1, regressed after #8053 partial fix |
| [#8731](https://github.com/zeroclaw-labs/zeroclaw/issues/8731) | 35 | MCP stdio zombie process accumulation — degrades long-running daemon stability |
| [#9035](https://github.com/zeroclaw-labs/zeroclaw/issues/9035) | 27 | Docker Compose gateway unreachable behind published port — deployment blocker |
| [#9340](https://github.com/zeroclaw-labs/zeroclaw/issues/9340) | 16 | CLI cron delivery hardcoded to `None` — cron jobs silently discard output |

**Maintainer priority recommendation:** Issues #9815, #9816, #9390, and #9387 are security or safety-critical and have been open 2–14 days with no visible fix PR. These should be addressed before the next release. The RFC process reforms (#9496, #8692) are structural and will affect all future decision-making velocity.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*