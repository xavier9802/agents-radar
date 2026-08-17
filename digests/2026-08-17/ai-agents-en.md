# OpenClaw Ecosystem Digest 2026-08-17

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-17 01:42 UTC

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



# OpenClaw Project Digest — 2026‑08‑17

## 1. Today’s Overview
OpenClaw activity remains intense: **500 issues** were updated in the last 24 h (454 still open/active, 46 closed), while **500 pull requests** saw updates (384 open, 116 merged/closed). A new release artifact (`pr‑124528‑profiles`) posted Gateway CPU‑profile data for performance‑hotspot analysis. The project shows strong developer responsiveness and high community engagement, though the large open‑issue backlog highlights ongoing reliability challenges around message delivery, session state, and event‑loop stalls.

## 2. Releases
No formal version release was published today. The only new release artifact is a **profile archive** (`pr‑124528‑profiles`) containing before/after CPU profiles from a bounded three‑node, twelve‑concurrent‑turn Gateway rig. This is a diagnostic artifact, not a user‑facing release; no migration notes or breaking changes apply.

## 3. Project Progress
**Merged/Closed PRs today (116 total):**  
Notable closed items include:

- **#116489** – `feat(security): require acknowledgement for install policy warnings` [🔗](https://github.com/openclaw/openclaw/pull/116489)  
  Adds an interactive CLI gate that shows bounded findings and requires the exact target name before allowing a suspicious plugin/skill install.

- **#120900** – `feat(ui): review install policy warnings` [🔗](https://github.com/openclaw/openclaw/pull/120900)  
  Extends the above with a Control‑UI path, letting an authenticated admin review and deliberately continue an install‑policy warning via `acknowledgeInstallPolicyWarning: true`.

These close a security‑review gap that previously left operators without a clear audit trail for plugin‑install decisions.

## 4. Community Hot Topics
**Most‑commented issues (top 3):**

1. **#121058** – “Silent reply failures still recurring after #116277 closed — no queued reply payload” [🔗](https://github.com/openclaw/openclaw/issues/121058)  
   *97 comments, P1, impact: message‑loss.* The monitoring cron continues to log new occurrences even after the prior fix was merged. Underlying need: reliable end‑to‑end delivery guarantees for channel‑level reply payloads.

2. **#44925** – “Subagent completion silently lost — no retry, no notification, no auto‑restart on timeout” [🔗](https://github.com/openclaw/openclaw/issues/44925)  
   *31 comments, P1, diamond‑lobster rating.* Multiple failure modes in subagent orchestration cause results to vanish without user feedback. Users demand transparent error propagation and automatic recovery for long‑running delegated tasks.

3. **#42475** – “Per‑agent cost budget enforcement at the gateway level” [🔗](https://github.com/openclaw/openclaw/issues/42475)  
   *26 comments, P2, tidepool rating.* Operators want configurable daily/monthly caps enforced before LLM dispatch, eliminating the need for external spend monitoring.

**Trend:** The top issues cluster around **reliability** (message loss, subagent failures) and **operational control** (cost budgets). Users are increasingly running OpenClaw in production multi‑agent setups and expect enterprise‑grade guarantees.

## 5. Bugs & Stability
**High‑severity bugs reported/open today (ranked by impact):**

| Issue | Severity | Summary | Fix PR? |
|-------|----------|---------|---------|
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | P1, 🦞 diamond lobster | Silent reply failures persist after previous close; no queued payload. | #116277 closed but regression reappeared. |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | P1, 🦞 diamond lobster | Subagent completion silently lost across multiple failure modes. | None yet; issue tagged `no‑new‑fix‑pr`. |
| [#87744](https://github.com/openclaw/openclaw/issues/87744) | P1, 🐚 platinum hermit | Codex‑backed Telegram turns time out waiting for `turn/completed`. | None. |
| [#96834](https://github.com/openclaw/openclaw/issues/96834) | P1, 🐚 platinum hermit | WhatsApp 1:1 inbound image wedges main lane ~3 min before processing. | None. |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | P1, 🦞 diamond lobster | Session‑transcript projection livelocks under sustained writes, stalling the event loop. | None. |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | P1, 🦞 diamond lobster | Large SQLite transcript cleanup blocks the gateway event loop. | None. |

**Stability assessment:** The event loop is a recurring bottleneck (issues #115908, #112423). Message‑loss bugs dominate the P1 list, indicating that delivery semantics are not yet robust enough for production workloads.

## 6. Feature Requests & Roadmap Signals
**Prominent open feature requests:**

- **#42475** – Per‑agent cost‑budget enforcement at the gateway [🔗](https://github.com/openclaw/openclaw/issues/42475)  
- **#22438** – Tiered bootstrap file loading for progressive context control [🔗](https://github.com/openclaw/openclaw/issues/22438)  
- **#6757** – Agent‑triggered context compaction (self‑compact tool) [🔗](https://github.com/openclaw/openclaw/issues/6757)  
- **#88154** – Slack Modal support for interactive workflows [🔗](https://github.com/openclaw/openclaw/issues/88154)  
- **#45508** – Self‑hosted STT/TTS provider support in webchat [🔗](https://github.com/openclaw/openclaw/issues/45508)

**Prediction:** Cost‑budget enforcement (#42475) and tiered bootstrap loading (#22438) are likely candidates for the next release, as they address concrete operational pain points (spend control, context‑window waste) and have clear implementation boundaries. Slack modal support (#88154) may follow if the Teams multi‑bot work (PR #112811) provides a reusable pattern.

## 7. User Feedback Summary
**Pain points highlighted by recent issues:**

- **Message loss** across channels (WhatsApp, Telegram, Feishu) – users report silent drops during reconnections, image processing, and session archiving.
- **Session‑state integrity** – subagent completions lost, transcript projections livelock, large‑SQLite cleanup blocks the main thread.
- **Operational friction** – auto‑update leaves stale module caches (#85844), dev‑channel updates fail with `workspace:*` protocol (#123073), cron jobs exhaust timeouts instead of fast‑failing on API errors (#45494).
- **Observability gaps** – `memory_search` transient timeouts masked as persistent failures (#112196), tool‑call loop‑detection warnings logged server‑side only (#120449).

**Satisfaction signal:** The volume of P1/P2 bugs and the recurring “silently lost” theme indicate that users are frustrated with reliability gaps. However, the high merge rate (116 PRs closed/merged in 24 h) and active maintainer engagement (many issues tagged `clawsweeper:needs‑maintainer‑review`) suggest the team is responsive.

## 8. Backlog Watch
**Long‑standing important issues needing maintainer attention:**

| Issue | Open Since | Days Open | Rating | Why It’s Stuck |
|-------|------------|-----------|--------|----------------|
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 2026‑03‑13 | ~158 | 🦞 diamond lobster | `no‑new‑fix‑pr`, `needs‑maintainer‑review`, `needs‑product‑decision` |
| [#42475](https://github.com/openclaw/openclaw/issues/42475) | 2026‑03‑10 | ~161 | 🌊 off‑meta tidepool | `no‑new‑fix‑pr`, `needs‑maintainer‑review`, `needs‑product‑decision` |
| [#22438](https://github.com/openclaw/openclaw/issues/22438) | 2026‑02‑21 | ~177 | 🌊 off‑meta tidepool | `no‑new‑fix‑pr`, `needs‑maintainer‑review`, `needs‑product‑decision` |
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | 2026‑07‑29 | ~19 | 🦞 diamond lobster | `source‑repro`, `clawsweeper‑recovery‑stuck` |
| [#112423](https://github.com/openclaw/openclaw/issues/112423) | 2026‑07‑21 | ~27 | 🦞 diamond lobster | `source‑repro` |

**Action needed:** The three oldest issues (#44925, #42475, #22438) are tagged with multiple `clawsweeper` flags and have seen no fix PRs. Product‑decision reviews are blocking progress. Maintainer triage should prioritize these or close them with clear roadmap placement.

---
*Digest generated from OpenClaw GitHub data for 2026‑08‑17. All links point to the corresponding issues/PRs on github.com/openclaw/openclaw.*

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Comparison Report
**Date: 2026-08-17 | Source: Community Digests**

---

## 1. Ecosystem Overview

The 2026 personal AI agent open-source landscape is dominated by high-velocity, reliability-focused platforms (OpenClaw, NanoBot, Hermes Agent) where production-deployment pressures are surfacing as P1 bugs around message delivery, subagent orchestration, and event-loop stability. Mid-tier projects (ZeroClaw, LobsterAI, NanoClaw) are aggressively shipping features and security hardening, while a secondary tier (PicoClaw, Moltis, CoPaw, IronClaw) focuses on incremental integration polish and niche channel support. Two projects (NullClaw, ZeptoClaw) show no recent activity, suggesting either dormancy or low public issue/PR velocity. The dominant tension across all active projects is between **reliability at scale** and **feature velocity**, with security hardening emerging as a concurrent priority.

---

## 2. Activity Comparison

| Project | Issues Updated | PRs Updated | Closed/Merged (24h) | Release | Open PR Backlog | Health Signal |
|---|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 116 PRs, 46 issues | None | 384 open | 🟡 High volume, reliability strain |
| **NanoBot** | 15 | 500 | 4 issues, 0 new PRs merged | None | ~499 open | 🟡 PR review bottleneck |
| **Hermes Agent** | 50 | 50 | 7 PRs merged/closed | ✅ v0.20.2 | Low | 🟢 Healthy release cadence |
| **PicoClaw** | 3 | 5 | ~0 merged | None | Moderate | 🟡 Low maintainer bandwidth |
| **NanoClaw** | 1 | 32 | 13 merged/closed | None | 19 open | 🟢 Sprint velocity, core-team driven |
| **NullClaw** | 0 | 0 | 0 | None | — | 🔴 No recent activity |
| **IronClaw** | 1 | 9 | 2 merged/closed | None | Low | 🟢 Steady maintenance |
| **LobsterAI** | 10 | 17 | 9 merged, 3 issues | None | Low | 🟢 Active contributor engagement |
| **Moltis** | 3 | 6 | 5 merged | None | Low | 🟢 Focused bug-fix cycle |
| **CoPaw** | 12 | 11 | 4 closed, 2 PRs merged | None (v2.1.0) | Moderate | 🟡 Critical bugs unfixed |
| **ZeroClaw** | 48 | 50 | 2 closed | None (0.8.x beta) | 46 open | 🟢 Strong contributor momentum |
| **ZeptoClaw** | 0 | 0 | 0 | None | — | 🔴 No recent activity |

*Health Signal Key:* 🟢 Active & stable | 🟡 Strained (backlog/reliability) | 🔴 Dormant or critical gaps

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Sheer scale of engagement** — 500 issue + 500 PR updates in 24h is an order of magnitude above most peers, indicating the largest active developer community.
- **Security-hardening maturity** — Merged interactive install-policy acknowledgment gates (#116489, #120900) that most peers lack; explicit audit-trail support for plugin installs.
- **Multi-channel breadth** — WhatsApp, Telegram, Slack, Feishu, and gateway-level cost budgeting (#42475) signal an enterprise-grade channel aggregator strategy.

**Technical approach differences:**
- Gateway-centric architecture with a bounded event loop (livelock bugs #115908, #112423 are unique to this model); peers like NanoClaw use cross-session fan-out and NanoBot uses a simpler cron scheduler.
- SQLite transcript persistence at scale creates unique blocking issues not seen in Moltis (Rust) or IronClaw (lighter deps).

**Community size comparison:** OpenClaw's 454 open active issues and 384 open PRs dwarf every other project. Hermes Agent (~50 issues/PRs) and ZeroClaw (~48/50) are the next most active, while PicoClaw (3/5) and IronClaw (1/9) operate at a fraction of the volume.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Message delivery reliability** | OpenClaw, NanoBot, CoPaw, ZeroClaw | Silent reply failures, subagent completion loss, cron misfires, undelivered batches |
| **Cost/spend visibility & control** | OpenClaw, NanoBot, CoPaw | Per-agent budget enforcement (#42475), token consumption logging (#5266), per-session reasoning_effort overrides (#7062) |
| **Security hardening** | NanoBot, PicoClaw, LobsterAI, ZeroClaw, OpenClaw | SSRF in media downloads, exec allowlist bypasses, IPC privilege escalation, plugin egress policies |
| **Multi-agent / cross-session coordination** | OpenClaw, NanoClaw, CoPaw, ZeroClaw | Subagent orchestration reliability, context fan-out, delivery hooks, approval card UX |
| **Channel parity & rich output** | PicoClaw, NanoClaw, LobsterAI, ZeroClaw | Telegram tables, Slack modals, Discord attachments, TTS, OAuth 2.1 for MCP |
| **Session/transcript state integrity** | OpenClaw, Hermes Agent, NanoBot | SQLite cleanup blocking, SessionDB FD leaks, cron scheduler crash recovery |
| **Provider compatibility** | LobsterAI, ZeroClaw, Hermes Agent, CoPaw | DeepSeek V4 schema fixes, Chat Completions profile (#8603), Codex OAuth expansion |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | NanoBot | NanoClaw | ZeroClaw | LobsterAI | IronClaw | Moltis | PicoClaw | CoPaw |
|---|---|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Gateway + multi-channel aggregation | Desktop agent + Bot Mode | Lightweight CLI agent | Multi-session orchestration | Protocol/RFC-driven platform | Chinese-market desktop app | IronLoop governance | Calendar/private-data | Channel integrations | Cloud/console agent |
| **Target users** | Production multi-agent operators | Desktop power users | Lightweight/edge deployers | Agent-group coordinators | Protocol-interop adopters | Chinese enterprise (DingTalk/Feishu/QQ) | IronLoop participants | Privacy-focused users | Channel plugin devs | Multi-agent cloud teams |
| **Language** | Node/TypeScript | Python | Python | Go | Rust | Electron/JS | Rust | Rust | Node/TypeScript | Python |
| **Release cadence** | Low (artifacts only) | High (patch releases) | Low (batching) | None visible | None visible | Low | Low | Moderate | None | v2.1.0 |
| **Key differentiator** | Enterprise gateway + cost budgets | Bot Mode bundling + desktop | Cron reliability + security | Cross-session primitives | RFC-driven governance | IM ecosystem depth | IronLoop role schema | CalDAV + vault privacy | OAuth 2.1 MCP + SSRF fixes | DataPaw runtime + cron |
| **Architecture** | Event-loop gateway | Service + desktop hybrid | CLI + scheduler | Agent-group fan-out | Plugin egress stages | Electron shell | IronLoop network | Rust headless | Channel adapters | Cloud console |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (high velocity, frequent fixes):**
- **OpenClaw** — Highest absolute volume; 116 PRs merged in 24h shows strong contributor throughput, though backlog (454 open issues) indicates scaling friction.
- **NanoClaw** — Core-team sprint mode; 13 merges from a single contributor (gavrielc) signals concentrated architectural evolution.
- **Hermes Agent** — Most mature release discipline (v0.20.2 with 397 PRs rolled up); fastest path to production stability.

**Tier 2 — Active Development (steady contributor flow):**
- **ZeroClaw** — 48/50 updates with strong RFC engagement; governance-heavy but technically deep.
- **LobsterAI** — Healthy contributor mix; security hardening burst shows community responsiveness.
- **CoPaw** — Strong first-time contributor engagement but critical bugs (#7063, #7074) remain unfixed — momentum without closure.

**Tier 3 — Maintenance / Niche:**
- **NanoBot** — 500 PR updates but only 4 issue closures; massive open PR backlog (#499) suggests review bottleneck.
- **IronClaw** — Steady but low-velocity; Dependabot-heavy backlog.
- **Moltis** — Focused bug-fix cycle; Format CI debt and file-size limits signal architectural consolidation needs.
- **PicoClaw** — Maintainer bandwidth constraint; security PRs stale in review.

**Tier 4 — Dormant:**
- **NullClaw, ZeptoClaw** — Zero activity; likely abandoned or internal-only.

---

## 7. Trend Signals

**1. Reliability is the new feature frontier.** The dominant P1 theme across OpenClaw, NanoBot, Hermes Agent, and CoPaw is not "missing features" but "features breaking in production" — silent message loss, subagent completion drops, cron misfires, and event-loop stalls. AI agent developers should prioritize **observability and delivery guarantees** over new channel integrations.

**2. Security hardening is accelerating as a community responsibility.** SSRF in media downloads (PicoClaw, ZeroClaw), exec allowlist bypasses (NanoBot), IPC privilege escalation (LobsterAI), and plugin egress policies (ZeroClaw) show that security fixes are increasingly coming from community contributors, not just maintainers. Projects without formal security review workflows risk falling behind.

**3. Multi-agent coordination primitives are emerging as a differentiator.** Cross-session context fan-out (NanoClaw #3257), subagent orchestration (OpenClaw #44925), Bot Mode inter-agent messaging (Hermes #88060), and agent-group task lists (CoPaw #7072) indicate the ecosystem is maturing from single-agent to multi-agent paradigms. This is the next competitive battleground.

**4. Cost visibility and budget enforcement are table-stakes expectations.** Per-agent cost budgets (OpenClaw #42475), token consumption logging (NanoBot #5266), and per-session reasoning effort (CoPaw #7062) show operators demand granular spend control. Projects that ship native cost-awareness will have an enterprise adoption advantage.

**5. Protocol interoperability (Chat Completions, ACP) is a strategic priority.** ZeroClaw's RFC #8603 for OpenAI Chat Completions compatibility, Hermes Agent's Codex OAuth expansion, and NanoClaw's ACP provider model suggest the ecosystem is converging on OpenAI-compatible APIs as a baseline, with ACP (Agent Control Plane) as the emerging coordination standard.

**6. Chinese-market IM integrations are a distinct sub-ecosystem.** LobsterAI's DingTalk/Feishu/QQ focus and PicoClaw's WeCom/Weixin support reflect a parallel track of channel development tailored to Chinese enterprise messaging, with different security and compliance expectations.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-17

## 1. Today's Overview

NanoBot remains highly active with 15 issues and 500 PRs updated in the last 24 hours, indicating sustained contributor momentum despite zero new releases. Four issues were closed, including a security advisory and a cron scheduler crash bug, while 11 remain open and active. The project shows strong community engagement with a significant backlog of open PRs (499) awaiting review or merge. No new releases were published today, suggesting the maintainers are batching changes or focused on stabilization.

## 2. Releases

**None.** No new versions were published on 2026-08-17.

## 3. Project Progress

Four issues were closed today, marking meaningful progress:

- **[#5373] Cron scheduler crash fix** — The cron scheduler was permanently dying after a single job-store persistence failure. The fix ensures `_arm_timer()` sits within the `try/finally` block so recovery is possible after transient disk or permission errors. ([Link](https://github.com/HKUDS/nanobot/issues/5373))
- **[#5305] Security: `exec.allowPatterns` bypass patched** — A critical allowlist bypass in the `exec` tool that enabled chained shell command execution via the OpenAI-compatible API was resolved. ([Link](https://github.com/HKUDS/nanobot/issues/5305))
- **[#2185] Gemini-3-flash-preview regression fixed** — Upgrading from 0.1.4 to 0.1.4post5 broke `gemini-3-flash-preview` usage via Ollama; this regression is now closed. ([Link](https://github.com/HKUDS/nanobot/issues/2185))
- **[#5275] Matrix thread context behavior confirmed** — A matrix messaging stream issue was closed, likely incorporated into a fix or design decision. ([Link](https://github.com/HKUDS/nanobot/issues/5275))

## 4. Community Hot Topics

**Most commented open issues driving discussion:**

| Issue | Comments | Focus |
|---|---|---|
| [#2463] Prompt prefix preservation architectural issue | 15 | Core conversation history accuracy |
| [#5266] Token consumption logging | 14 | Cost visibility and debugging |
| [#4864] Endless loop in `complete_goal` | 7 | Tool serialization bug |
| [#4467] Dream skill deduplication | 3 | UX improvement for workspace skills |

**Underlying needs:** The top-voted and most-discussed issues reveal two dominant community concerns: **(1) cost transparency** — users are burning excessive tokens without visibility into per-call consumption, and **(2) architectural correctness** — the mismatch between persisted history and actual prompt prefixes sent to models is a foundational issue affecting conversation fidelity. The `complete_goal` infinite loop (7 comments, 1 👍) also signals urgency around tool reliability.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|---|---|---|---|
| 🔴 Critical | [#5305] | `exec.allowPatterns` allowlist bypass enabling chained shell commands | ✅ Closed |
| 🟠 High | [#4864] | Endless loop: `complete_goal` errors due to gateway JSON parsing regression | Unknown |
| 🟠 High | [#5402] | Token consolidation never triggers — tiktoken consistently underestimates API token count | Unknown |
| 🟡 Medium | [#5377] | Consolidation truncates archive input but advances past full message batch, losing messages | Unknown |
| 🟡 Medium | [#2185] | Gemini-3-flash-preview broken after 0.1.4→0.1.4post5 upgrade | ✅ Closed |

The cron scheduler persistence crash ([#5373]) was fixed and closed today. Three open bugs directly impact reliability: the `complete_goal` loop, token estimation drift, and consolidation message loss — all affecting core agent loops.

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood for Next Release |
|---|---|---|
| [#5406] | Native TypeScript terminal UI (supersedes #4329) | ⭐⭐⭐ High — major PR, recently resubmitted |
| [#5251] | MCP Apps host support in WebUI | ⭐⭐ Medium — extension of existing MCP client |
| [#5289] | Telegram sticker and reaction support | ⭐⭐ Medium — channel parity feature |
| [#5298] | Budget model-visible MCP schemas for large tool sets | ⭐⭐ Medium — performance optimization |
| [#5404] | Skill `disable-model-invocation` flag | ⭐⭐ Medium — aligns with PI/Cursor/ClaudeCode behavior |
| [#5275] | Matrix thread context isolation | ⭐ Low — already closed |

**Prediction:** The TypeScript terminal UI (PR #5406) is the most likely candidate for the next release, given it supersedes a previously merged-then-reverted effort and carries full cross-terminal test coverage. Token consumption logging ([#5266]) is also a strong candidate given its high comment count and practical value.

## 7. User Feedback Summary

**Pain points:**
- **Token burn is out of control** — users report millions of tokens consumed in 2 hours with no visible activity, and the current consolidation system underestimates actual counts, never triggering truncation ([#5266], [#5402]).
- **Tool reliability issues** — the `complete_goal` tool enters endless loops due to gateway serialization bugs, and cron jobs can die permanently from single persistence failures ([#4864], [#5373]).
- **Security concerns** — the `exec.allowPatterns` bypass allowed arbitrary chained shell execution, eroding trust in sandboxed tool use ([#5305]).
- **Duplicate skills from Dream** — the Dream agent creates duplicate workspace skills on each run instead of updating existing ones, frustrating power users ([#4467]).

**Satisfaction signals:** The community is actively contributing fixes (500 PRs updated) and the maintainers are closing security and crash bugs promptly, suggesting a healthy feedback loop.

## 8. Backlog Watch

| Issue/PR | Age | Why It Needs Attention |
|---|---|---|
| [#2463] Prompt prefix preservation | ~5 months | Foundational architectural issue affecting all conversation history accuracy |
| [#5266] Token consumption logging | ~11 days | High-impact visibility gap; no fix PR yet |
| [#4864] `complete_goal` infinite loop | ~1 month | Core tool reliability; 1 👍 indicates user frustration |
| [#5402] Tiktoken underestimation | ~1 day | Causes consolidation to never trigger; no fix PR yet |
| [#5377] Consolidation message loss | ~4 days | Data-loss bug in conversation archival; no fix PR yet |
| [#5406] TypeScript terminal UI | ~1 day | Large PR needing review; supersedes reverted #4329 |

**Notable long-standing items:** Issue [#2463] has been open since March with 15 comments and no resolution — this architectural gap between persisted history and actual prompt prefixes deserves prioritization. Three bugs in the consolidation/token pipeline ([#5402], [#5377], [#5266]) form a cluster that may benefit from a unified fix.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-17

## 1. Today's Overview

Hermes Agent shows **high development velocity** with 50 issues and 50 PRs updated in the last 24 hours, indicating sustained community engagement and active maintenance. The project shipped **v0.20.2** yesterday as a patch release rolling up approximately 397 PRs since v0.20.1, signaling a mature release cadence for downstream consumers. Activity is dominated by bug fixes and stability work across critical subsystems (gateway, desktop, cron, approval system), with several P0/P1 issues surfacing around session state leaks and Windows installer regressions. Seven PRs were merged or closed today, including notable feature integrations (Bot Mode bundling, Codex OAuth context expansion). Overall project health is strong with active issue triage and rapid PR turnaround.

**Activity Assessment:** 🟢 High — sustained contributor momentum with balanced bug-fix and feature development.

---

## 2. Releases

### v0.20.2 (v2026.8.16) — Patch Release

- **Release Date:** August 16, 2026
- **Scope:** Rolls up ~397 PRs merged since v0.20.1 into a stable tagged release
- **Purpose:** Provides a predictable downstream reference for Docker images, hosted deployments, and fresh installs
- **Breaking Changes:** None indicated (patch release)
- **Migration Notes:** Users on v0.20.1 should upgrade to consume the accumulated fixes; no manual migration required

> Full release details: [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent)

---

## 3. Project Progress

### Merged / Closed PRs (Today)

| PR | Description | Significance |
|----|-------------|--------------|
| [#88056](https://github.com/NousResearch/hermes-agent/pull/88056) | Raise Codex OAuth context to 900K for gpt-5.6/gpt-5.4 family | Enables larger-context ChatGPT-subscription accounts |
| [#87886](https://github.com/NousResearch/hermes-agent/pull/87886) | Bundle Bot Mode as built-in default-on plugin + core teammate protocol | Bot Mode moves from external repo to first-class desktop feature |

### Key Open PRs Advancing

- [#88063](https://github.com/NousResearch/hermes-agent/pull/88063) — Fixes FD leak from abandoned `SessionDB` instances (addresses P1 #88033)
- [#88058](https://github.com/NousResearch/hermes-agent/pull/88058) — Updates vulnerable desktop dependencies (NanoID, Electron 40→41)
- [#88027](https://github.com/NousResearch/hermes-agent/pull/88027) — Exposes Devin ACP as first-class Hermes provider
- [#86880](https://github.com/NousResearch/hermes-agent/pull/86880) — Localizes gateway slash-command descriptions (i18n)
- [#87755](https://github.com/NousResearch/hermes-agent/pull/87755) — Fixes Slack native task card rendering (double-text bug)
- [#88051](https://github.com/NousResearch/hermes-agent/pull/88051) — Reaps Kanban worktree workspaces at task completion
- [#84399](https://github.com/NousResearch/hermes-agent/pull/84399) — Plumbs `config.yaml` `model.temperature` into agent API requests

---

## 4. Community Hot Topics

### Most Discussed Issues

| Issue | Comments | Topic | Link |
|-------|----------|-------|------|
| [#87559](https://github.com/NousResearch/hermes-agent/issues/87559) | 5 | ACP-provided MCP servers registered but tools never reach callable catalog | [Issue](https://github.com/NousResearch/hermes-agent/issues/87559) |
| [#62158](https://github.com/NousResearch/hermes-agent/issues/62158) | 4 | Desktop elapsed-time counter resets on navigation (now closed) | [Issue](https://github.com/NousResearch/hermes-agent/issues/62158) |
| [#87479](https://github.com/NousResearch/hermes-agent/issues/87479) | 3 | Telegram status-message cache grows without bound | [Issue](https://github.com/NousResearch/hermes-agent/issues/87479) |
| [#87356](https://github.com/NousResearch/hermes-agent/issues/87356) | 2 | cronjob update schema omits model/provider params | [Issue](https://github.com/NousResearch/hermes-agent/issues/87356) |
| [#88012](https://github.com/NousResearch/hermes-agent/issues/88012) | 2 | `honcho_search` always empty — peer_perspective filter unsupported | [Issue](https://github.com/NousResearch/hermes-agent/issues/88012) |

### Analysis

The top discussion (#87559) reveals a **critical integration gap** between ACP (Agent Control Plane) and the MCP tool catalog — users configuring Paseo daemon with ACP-mode expect injected MCP servers to be immediately callable, but tools are silently dropped. This points to an architecture-level wiring issue that affects the growing ACP/MCP ecosystem.

The Telegram cache leak (#87479) and honcho search failure (#88012) indicate **platform plugin maturity gaps** — long-running multi-chat deployments and memory-search workflows hit edge cases that weren't caught in standard testing.

---

## 5. Bugs & Stability

### P0 — Critical

| Issue | Summary | Fix PR | Link |
|-------|---------|--------|------|
| [#87368](https://github.com/NousResearch/hermes-agent/issues/87368) | Background review drops gateway ephemeral session context, breaks prompt-cache prefix parity | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87368) |

### P1 — High

| Issue | Summary | Fix PR | Link |
|-------|---------|--------|------|
| [#87331](https://github.com/NousResearch/hermes-agent/issues/87331) | Desktop auto-update can wipe Windows build (venv lock ignored, ZIP fallback deletes win-unpacked) | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87331) |
| [#87304](https://github.com/NousResearch/hermes-agent/issues/87304) | Windows ZIP fallback fires on dependency failure and permanently deletes uncommitted changes | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87304) |
| [#88033](https://github.com/NousResearch/hermes-agent/issues/88033) | `hermes serve` leaks file descriptors to EMFILE (SessionDB never closed, 97% FD table is /dev/null) | [#88063](https://github.com/NousResearch/hermes-agent/pull/88063), [#88048](https://github.com/NousResearch/hermes-agent/pull/88048) | [Issue](https://github.com/NousResearch/hermes-agent/issues/88033) |
| [#87509](https://github.com/NousResearch/hermes-agent/issues/87509) | API-server sessions have no cron_mode approval exemption, stall for `approvals.timeout` | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87509) |
| [#87488](https://github.com/NousResearch/hermes-agent/issues/87488) | Headless approval escalation never resolves — no-timer path queues into `_pending` with no auto-deny | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87488) |

### P2 — Medium

| Issue | Summary | Fix PR | Link |
|-------|---------|--------|------|
| [#87497](https://github.com/NousResearch/hermes-agent/issues/87497) | `lifecycle_guard` null-byte escape still possible after #76762 fix (path with NUL byte) | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87497) |
| [#87503](https://github.com/NousResearch/hermes-agent/issues/87503) | `_save_codex_tokens()` writes only to profile scope, revokes rotation family in multi-profile | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87503) |
| [#87420](https://github.com/NousResearch/hermes-agent/issues/87420) | `pre_tool_call` directive aggregation is first-valid-wins — plugin blocks shadowed | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87420) |
| [#87469](https://github.com/NousResearch/hermes-agent/issues/87469) | Background review receipts not delivered for routed named profiles | — | [Issue](https://github.com/NousResearch/hermes-agent/issues/87469) |

### P3 — Lower / Security

| Issue | Summary | Link |
|-------|---------|------|
| [#87419](https://github.com/NousResearch/hermes-agent/issues/87419) | 🔴 **Security:** Windows destructive commands (`format C:`, `diskpart`, `Remove-Item -Recurse`) bypassable under `approvals.mode=off` / `--yolo` | [Issue](https://github.com/NousResearch/hermes-agent/issues/87419) |
| [#88053](https://github.com/NousResearch/hermes-agent/issues/88053) | read-before-write guard rejects all background-review skill writes (ContextVar lost across threads) | [Issue](https://github.com/NousResearch/hermes-agent/issues/88053) |
| [#87248](https://github.com/NousResearch/hermes-agent/issues/87248) | Desktop billing error bubble persists after auto-failover succeeds | [Issue](https://github.com/NousResearch/hermes-agent/issues/87248) |
| [#87319](https://github.com/NousResearch/hermes-agent/issues/87319) | `transform_llm_output` callbacks lack guaranteed sequential safety pipeline | [Issue](https://github.com/NousResearch/hermes-agent/issues/87319) |
| [#85391](https://github.com/NousResearch/hermes-agent/issues/85391) | WhatsApp pairing wizard writes to different session dir than gateway reads | [Issue](https://github.com/NousResearch/hermes-agent/issues/85391) |

**Stability Summary:** The project is experiencing a **burst of session-state and Windows-specific regressions**, many tied to the recent managed-cron redesign (#84339) and Bot Mode integration. The EMFILE leak (#88033) and Windows updater bugs (#87331, #87304) are the most impactful for production deployments. Fix PRs exist for the FD leak but remain unmerged.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood for Next Release | Link |
|-------|-------------|----------------------------|------|
| [#88061](https://github.com/NousResearch/hermes-agent/issues/88061) | Per-task multi-agent workflow — IM-style task trace + reliable execution (ported from archived Hermes-Bot-Mode) | 🟡 Medium — design-phase, needs maintainer decision | [Issue](https://github.com/NousResearch/hermes-agent/issues/88061) |
| [#88060](https://github.com/NousResearch/hermes-agent/issues/88060) | Composer `@` autocomplete should offer Bot Mode agents | 🟢 High — Bot Mode just bundled (#87886), natural follow-on | [Issue](https://github.com/NousResearch/hermes-agent/issues/88060) |
| [#88059](https://github.com/NousResearch/hermes-agent/issues/88059) | Bot-to-bot reply silently drops when receiver has no Bot Chat session | 🟢 High — bug in newly-bundled feature, likely quick fix | [Issue](https://github.com/NousResearch/hermes-agent/issues/88059) |
| [#87267](https://github.com/NousResearch/hermes-agent/issues/87267) | Add MAX (max.ru) Russian messenger as platform plugin | 🟡 Medium — niche market, depends on contributor | [Issue](https://github.com/NousResearch/hermes-agent/issues/87267) |
| [#88027](https://github.com/NousResearch/hermes-agent/issues/88027) | Expose Devin ACP as first-class Hermes provider | 🟡 Medium — PR open, requires provider integration work | [PR](https://github.com/NousResearch/hermes-agent/pull/88027) |
| [#86880](https://github.com/NousResearch/hermes-agent/issues/86880) | Localize gateway slash-command descriptions | 🟢 High — small scope, internationalization improvement | [PR](https://github.com/NousResearch/hermes-agent/pull/86880) |

**Roadmap Signal:** The recent bundling of Bot Mode (#87886) is creating a cascade of follow-on features and bug fixes around multi-agent workflows, composer integration, and bot-to-bot messaging. The Devin ACP provider integration (#88027) suggests expanding the external-agent provider ecosystem.

---

## 7. User Feedback Summary

### Pain Points
- **Windows desktop instability** is the dominant complaint:

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-17

## 1. Today's Overview

PicoClaw remains in a steady state of incremental development with 3 open issues and 5 PRs active in the last 24 hours. A notable security-focused PR batch landed yesterday addressing SSRF vulnerabilities in media download pipelines across multiple channels. No new releases were published. The project shows healthy community contribution volume but a concerning number of stale-labeled items awaiting maintainer triage. Overall project health: **moderate** — feature development is active, but backlog accumulation and stale PRs suggest maintainership bandwidth is a constraint.

## 2. Releases

No new releases published in the reporting window.

## 3. Project Progress

**Closed/Merged Today:**
- [#3193 — Added simplex channel type](https://github.com/sipeed/picoclaw/pull/3193) (closed 2026-08-16) — Introduces a new simplex communication channel type. Closed but not merged, suggesting it may have been declined or deferred pending further review.

**PRs Still Open:**
- [#3299 — Add native Exa web search provider](https://github.com/sipeed/picoclaw/pull/3299) — Adds Exa as a native `tools.web` / `web_search` provider with `type: "auto"`, `contents.highlights`, API key auth, and date-range filters. Actively progressing toward merge.
- [#3322–#3324 — SSRF hardening for inbound media downloads](https://github.com/sipeed/picoclaw/pull/3322) (channels), [#3323 — WeCom](https://github.com/sipeed/picoclaw/pull/3323), [#3324 — Weixin](https://github.com/sipeed/picoclaw/pull/3324) — Three sibling PRs by SashaMIT that close a consistent SSRF vulnerability: media downloads in QQ, Telegram, Discord, LINE, Slack, WeCom, and Weixin channels followed redirects into private/loopback networks. All three use `utils.CreateSafeHTTPClient` + `ValidateSafeHTTPURL` to block private targets. These are high-priority security fixes awaiting review.

## 4. Community Hot Topics

| # | Type | Title | Comments | Link |
|---|------|-------|----------|------|
| #3302 | Feature | Support OAuth 2.1 for MCP servers | 3 | [Issue](https://github.com/sipeed/picoclaw/issues/3302) |
| #3325 | Feature | Render Telegram tables with rich messages | 1 | [Issue](https://github.com/sipeed/picoclaw/issues/3325) |
| #3338 | Bug | Slack does not attach image media content | 0 | [Issue](https://github.com/sipeed/picoclaw/issues/3338) |

**Analysis:** The OAuth 2.1 feature request (#3302, linked to prior #2546) signals that users are integrating PicoClaw with MCP-based AI server ecosystems and need standards-compliant auth. This is a nice-to-have but aligns with broader ecosystem trends. The Telegram rich-tables request (#3325) reflects users moving beyond basic text output into structured data presentation — a quality-of-life improvement that leverages Telegram Bot API 10.1's native table UI. The Slack media bug (#3338) is a fresh, high-impact issue with zero engagement yet but a clear root cause already identified.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|----------|-------|---------|--------|
| 🔴 High | [#3338 — Slack image upload failure](https://github.com/sipeed/picoclaw/issues/3338) | `SendMedia` builds `UploadFileParameters` without `FileSize`, causing `file.upload.v2: file size cannot be 0` rejection. Affects PicoClaw 0.3+. | None yet |
| 🟡 Medium | [#3322–#3324 — SSRF via media download redirects](https://github.com/sipeed/picoclaw/pull/3322) | Inbound media downloads across QQ/Telegram/Discord/LINE/Slack/WeCom/Weixin followed redirects to private/loopback addresses. | PRs #3322, #3323, #3324 in progress |

The SSRF issues represent a real security regression affecting multiple channel integrations. The Slack media bug is a clean, single-line fix (`FileSize` field missing) but has no open PR yet.

## 6. Feature Requests & Roadmap Signals

| Request | Priority Signal | Likelihood for Next Release |
|---------|----------------|----------------------------|
| OAuth 2.1 for MCP servers (#3302) | Nice-to-have / Enhancement, 3 comments, linked to prior #2546 | Low — non-core, likely deferred |
| Telegram rich table rendering (#3325) | Enhancement, 1 comment, leverages API 10.1 feature | Medium — low effort, high UX value |
| Exa web search provider (#3299 PR) | New native provider, actively reviewed | High — PR is complete and in review |
| Simplex channel type (#3193 PR) | Closed but not merged | Unclear — status ambiguous, may be revisited |

The strongest roadmap signal is the Exa provider PR (#3299), which is functionally complete and likely to land in the next release. The Telegram tables feature is a low-hanging improvement that could be picked up quickly.

## 7. User Feedback Summary

- **Pain point — Slack media uploads broken:** octavioturra reports a hard failure with a precise root cause. Users relying on Slack for image sharing are blocked. This is a regression from a missing `FileSize` field — a one-line fix.
- **Pain point — SSRF exposure on media downloads:** SashaMIT identified and patched a systemic security gap across 7+ channel integrations. While no user has filed a corresponding issue yet, this is a silent vulnerability affecting all users who receive media from QQ, Telegram, Discord, LINE, Slack, WeCom, or Weixin.
- **Demand — Better structured output:** The Telegram tables request (#3325) and OAuth 2.1 request (#3302) both reflect users pushing PicoClaw toward more enterprise-grade integrations — better formatting for end-user consumption and standards-compliant auth for MCP ecosystems.

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [#3302 — OAuth 2.1 for MCP servers](https://github.com/sipeed/picoclaw/issues/3302) | 18 days, stale | Important for MCP ecosystem users; no maintainer response yet |
| [#3193 — Simplex channel type](https://github.com/sipeed/picoclaw/pull/3193) | 51 days, closed | Unclear why closed without merge or comment; contributor may need guidance |
| [#3322–#3324 — SSRF fixes](https://github.com/sipeed/picoclaw/pull/3322) | 8 days, stale | Security-critical PRs sitting in review; delayed merge extends exposure window |
| [#3325 — Telegram rich tables](https://github.com/sipeed/picoclaw/issues/3325) | 8 days, stale | Low-effort enhancement with no traction |

**Overall Assessment:** The project is functionally active but the maintainer team appears bandwidth-constrained, with 4 of 8 tracked items labeled stale. The most urgent action is merging the SSRF hardening PRs (#3322–#3324) and resolving the Slack media bug (#3338). The backlog of feature requests suggests growing user demand for ecosystem integration depth (OAuth, rich formatting) that the current release cadence may not be keeping pace with.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-17

## 1. Today's Overview

NanoClaw is experiencing a **very high activity burst**, with 32 PRs updated in the last 24 hours (19 open, 13 merged/closed) and only 1 issue closed. The pace is driven almost entirely by the core-team (gavrielc), signaling an intensive development sprint. No new releases were published, so this activity represents work-in-progress against the current release line. The project appears healthy and aggressively iterating on core architecture.

## 2. Releases

No new releases today.

## 3. Project Progress

**13 PRs merged/closed today**, heavily concentrated on core platform improvements:

| Area | PRs Merged |
|---|---|
| Agent orchestration & multi-session | #3264, #3265, #3259 (partially) |
| Channel adapter capabilities | #3261, #3263, #3283, #3278 |
| Permissions & DM flows | #3260, #3262, #3266 |
| Community contributions | #1251, #3278 |

**Key advances:**
- **Mid-turn streaming delivery** (#3284) establishes a single "content door" for providers that stream assistant text, preventing duplicate content delivery across segments.
- **Cross-session context fan-out** (#3257, open) and **detached conversation tracking** (#3256, open) extend the multi-session agent model.
- **`decline_notify` policy** (#3260) adds a middle-ground unknown-sender response between strict drop and approval-card interrupt.
- **OpenMail email channel** (#1251) finally merged after ~5 months, adding three operational modes (channel, tool+notify, CLI-on-demand).
- **Chat link preservation** (#3283) fixes a UX regression where shortened display text lost hyperlink targets.
- **`registerDeliveryBatchPreview`** (#3264) gives modules a hook over undelivered outbound batches before row-by-row dispatch.
- **`CreateAgentOptions.suppressCreatedNotify`** (#3265) gives wrapper scripts cleaner success/failure signal control.
- **Channel card interceptor** (#3266) opens a generic seam for modules to auto-handle or suppress registration escalation cards.

## 4. Community Hot Topics

1. **[PR #3257](https://github.com/nanocoai/nanoclaw/pull/3257)** — Cross-session context fan-out, DM backfill, echo pruning, and `ncl sessions history`
   - Highest architectural significance today; addresses the core need for agents operating across concurrent sessions to share context without noise.

2. **[PR #1251](https://github.com/nanocoai/nanoclaw/pull/1251)** — OpenMail email channel (`/add-openmail`)
   - Opened March 2026; merged today. Long-standing community request for native email as a channel, not just a protocol bridge.

3. **[PR #3281](https://github.com/nanocoai/nanoclaw/pull/3281)** — Agent-scoped `ncl tasks` blind to pre-2.1.54 legacy sessions
   - Direct fix for a regression reported in #3233. Users running agent groups with legacy sessions could not see their tasks.

4. **[PR #2752](https://github.com/nanocoai/nanoclaw/pull/2752)** — Stage inbound Discord attachments
   - Open since June 2026. Discord images and pasted-text files reach agents as bare `[file: …]` tokens with no bytes — a significant usability gap.

**Underlying need:** The community is pushing hard on **multi-agent coordination** (cross-session context, delivery hooks, card interceptors) and **channel parity** (email, Discord attachments, Telegram code formatting). Core-team is responding rapidly.

## 5. Bugs & Stability

| Severity | Item | Status |
|---|---|---|
| Medium | [#3282](https://github.com/nanocoai/nanoclaw/pull/3282) — Telegram pairing codes with spaces rejected | Open PR fixes |
| Medium | [#3281](https://github.com/nanocoai/nanoclaw/pull/3281) — `ncl tasks` blind to pre-2.1.54 legacy sessions | Open PR fixes |
| Medium | [#3280](https://github.com/nanocoai/nanoclaw/pull/3280) — `ncl groups config update` cannot unset nullable scalars (stores `""` instead of `NULL`) | Open PR |
| Low | [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) — Discord inbound attachments unstageable | Open since June |

No crash or data-loss reports today. The `ncl tasks` legacy-session bug (#3233 → #3281) and the config-null unset bug (#3280) are the most impactful open issues. The two-phase batch selection fix (#3254, open) also addresses a subtle but real regression where accumulated context rows could crowd out due task rows from the inbound batch.

## 6. Feature Requests & Roadmap Signals

- **`decline_notify` sender policy** (#3260) — suggests users want a softer alternative to approval cards for unknown DM senders without going fully strict.
- **`registerChannelCardInterceptor`** (#3266) — indicates demand for extensibility in the registration/approval flow beyond the existing surface.
- **`registerDeliveryBatchPreview`** (#3264) — prefetch use-case (expensive model calls, etc.) shows users want to optimize outbound cost and latency.
- **`suppressCreatedNotify`** (#3265) — scripting/automation users want cleaner wrapper output.
- **Hot-start adapter** (#3263) — runtime reconfiguration without full restart, important for plugin ecosystems.
- **Document memory (save_document MCP)** (#3278) — Story 1.1 of a larger epic; signals roadmap toward persistent file/memory integration.

**Predicted next release focus:** Multi-session orchestration primitives (PRs #3254–#3257) and the extended adapter capability surface (PRs #3261, #3263, #3264, #3266).

## 7. User Feedback Summary

- **Positive:** Core-team is moving fast on multi-agent coordination — users with complex agent-group setups are seeing their pain points addressed directly.
- **Frustration points:**
  - Telegram pairing code whitespace handling (#3282) — basic UX gap.
  - Legacy session invisibility in `ncl tasks` (#3281 / #3233) — broken expectation after upgrade.
  - `ncl groups config update` string coercion bug (#3280) — tooling quirk that stores `""` instead of NULL, polluting config.
  - Discord attachments never reaching the agent in readable form (#2752) — open for ~2 months, significant for media-heavy workflows.
- **Satisfaction signals:** High engagement on PRs from core-team; rapid merge cadence (#1251 OpenMail after 5 months) shows community contributions are eventually recognized.

## 8. Backlog Watch

| PR | Open Since | Concern |
|---|---|---|
| [#2752](https://github.com/nanocoai/nanoclaw/pull/2752) — Discord inbound attachments | 2026-06-12 | ~2 months open; blocks media-based agent workflows |
| [#3254](https://github.com/nanocoai/nanoclaw/pull/3254) — Two-phase inbound batch selection | 2026-08-15 | Critical regression fix still open; context rows can suppress tasks |
| [#3281](https://github.com/nanocoai/nanoclaw/pull/3281) — Legacy session `ncl tasks` | 2026-08-16 | Impacts users who upgraded past 2.1.54 with agent groups |
| [#3280](https://github.com/nanocoai/nanoclaw/pull/3280) — Nullable scalar unset | 2026-08-16 | Config tooling bug; simple fix pending |
| [#3255](https://github.com/nanocoai/nanoclaw/pull/3255) — Outbound delivery resolves sender's own channel row | 2026-08-15 | Multi-instance room bug; deterministic-but-arbitrary fallback is wrong |

**Recommended maintainer attention:** #2752 (long-open community PR), #3254 and #3255 (correctness regressions in the delivery pipeline), and #3281 (upgraded users losing visibility into legacy sessions).

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-17

## 1. Today's Overview

IronClaw is showing steady maintenance activity with 9 PRs updated and 1 new issue filed in the last 24 hours. Development is currently in a dependency-refresh and polish phase — no new releases or major feature merges occurred today, but two PRs were closed (one merged fix, one cleanup), indicating active triage. The project's health is stable: traffic is modest, all open PRs carry low-to-medium risk ratings, and contributor engagement is concentrated among core and experienced maintainers. No regressions or blocking bugs were reported today.

## 2. Releases

**None.** No new versions were published today. The most recent activity is dependency bumps via Dependabot rather than user-facing releases.

## 3. Project Progress

**Merged / Closed PRs today:**

- **[PR #7683](https://github.com/nearai/ironclaw/pull/7683)** — *chore: remove retired IronLoop network settings* (Closed/Merged). Removes obsolete `network_access` fields from the trusted IronLoop repository configuration, retaining existing Implement, Tester, automatic Review, and automatic Resolve behavior. Confirmed compliant with IronLoop v1 role schema via `git diff --check`.

- **[PR #7682](https://github.com/nearai/ironclaw/pull/7682)** — *fix(slack): deliver the unlinked-user connect nudge privately, with a one-click connect link* (Open, directly addresses Issue #7681). Fixes the UX problem where unlinked Slack users received a public connect notice in shared channels. The PR delivers the nudge privately and includes a one-click connect link, eliminating the manual multi-step round trip.

**Active PRs under review:**

- **[PR #7651](https://github.com/nearai/ironclaw/pull/7651)** — *feat(automations): add deterministic no-result suppression* (Open, XL size). Introduces model-derived `result_delivery` intent from `trigger_create`, allowing deterministic suppression of automations when no meaningful result is produced. This is a notable feature advance.

## 4. Community Hot Topics

- **[Issue #7681](https://github.com/nearai/ironclaw/issues/7681)** — *Slack: unlinked-user connect message is public and requires a manual round trip*. Filed by **sergeiest** on 2026-08-16. This is the only new issue today and has already spawned a direct fix PR (#7682). The underlying need is clear: users expect private, frictionless onboarding flows in Slack. A public connect notice in shared channels is both a privacy concern and a UX dead end — the reported thread ends with *"what's the link to connect you? ..."*, indicating user confusion and abandonment risk.

- **[PR #7682](https://github.com/nearai/ironclaw/pull/7682)** — Already linked above; the rapid PR creation (same day as the issue) signals strong community responsiveness to Slack onboarding pain points.

## 5. Bugs & Stability

**No new bugs or crashes reported today.**

The only issue filed (#7681) is classified as an **enhancement/UX** bug, not a stability or regression problem. A fix PR (#7682) is already open, which bodes well for resolution speed. No other crash reports, regressions, or error-related issues appeared in the 24-hour window.

**Dependency updates** (PRs #7684, #7632, #7406, #7020, #7262) are all routine bumps with low-to-medium risk ratings — no stability concerns raised.

## 6. Feature Requests & Roadmap Signals

- **[Issue #7681 / PR #7682](https://github.com/nearai/ironclaw/pull/7682)** — Private, one-click Slack onboarding for unlinked users. This is a high-visibility UX improvement that directly addresses a real user pain point. Likely to be merged soon given the PR's low risk and direct issue linkage.

- **[PR #7651](https://github.com/nearai/ironclaw/pull/7651)** — *Deterministic no-result suppression for automations*. This is the most significant feature work in the pipeline. If merged, it would reduce automation noise by letting the model infer whether a result warrants delivery. Given its XL size and low risk, this is a strong candidate for the next release cycle.

**Signal:** The project is prioritizing Slack UX polish and automation quality improvements over new integrations in this sprint.

## 7. User Feedback Summary

- **Pain point (Slack onboarding):** Unlinked users @-mentioning or DMing the bot in shared channels receive a public reply directing them to the web app, creating an awkward and confusing experience. The dead-end nature of the current flow ("connect it in the web app, then message me here again") was explicitly called out in the issue, with a commenter noting the thread ended with *"what's the link to connect you? ..."* — a clear signal of user friction and potential drop-off.

- **Satisfaction:** No negative feedback on the recent dependency updates or the IronLoop settings cleanup. The community appears satisfied with the project's responsiveness, as evidenced by the same-day PR response to the Slack issue.

## 8. Backlog Watch

- **[PR #7651](https://github.com/nearai/ironclaw/pull/7651)** — Open since 2026-08-14 (2 days), XL size, low risk. No comments yet. This is a significant feature PR that may benefit from early maintainer review to keep momentum.

- **[PR #7406](https://github.com/nearai/ironclaw/pull/7406)** — Dependabot actions-group update, open since 2026-08-09 (8 days). Medium risk. Routine but long-standing; could use a merge or close to reduce open PR count.

- **[PR #7020](https://github.com/nearai/ironclaw/pull/7020)** — `tokio-tungstenite` bump, open since 2026-08-02 (15 days). Low risk, XS size. Longest-open Dependabot PR; a candidate for automated merge.

- **[PR #7262](https://github.com/nearai/ironclaw/pull/7262)** — WASM group update, open since 2026-08-05 (12 days). Low risk. Similar to #7020 — routine maintenance accumulating in the backlog.

**Overall:** The backlog is light but contains several stale Dependabot PRs that could be batch-closed. The feature PR #7651 is the item most worth prioritizing for maintainer attention.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-17

## 1. Today's Overview

LobsterAI shows moderate development activity on 2026-08-16/17, with **10 issues** and **17 PRs** updated in the last 24 hours. Three issues and nine PRs were closed, indicating steady progress. No new releases were published. The project is actively addressing security hardening (three merged security PRs), UX improvements (agent template import/export, image avatars, TTS), and ongoing stability fixes. Community engagement remains healthy with a balanced mix of bug reports, feature requests, and contributor PRs.

## 2. Releases

No new releases were published on this date.

## 3. Project Progress

**Merged/Closed PRs (9):**

| PR | Author | Summary |
|----|--------|---------|
| [#1690](https://github.com/netease-youdao/LobsterAI/pull/1690) | leedalei | Added confirmation modal before deleting IM instances (DingTalk, Feishu, QQ) |
| [#1691](https://github.com/netease-youdao/LobsterAI/pull/1691) | liulingfeng | Added agent template import/export — JSON-based serialization for cross-device sharing |
| [#1693](https://github.com/netease-youdao/LobsterAI/pull/1693) | leedalei | Improved model setup entry UX; fixed draft input loss on unsent messages |
| [#1715](https://github.com/netease-youdao/LobsterAI/pull/1715) | flowell | Fixed missing `session_id` in OpenClaw server proxy requests |
| [#1760](https://github.com/netease-youdao/LobsterAI/pull/1760) | leedalei | Added image avatar support alongside emoji avatars for custom agents |
| [#1831](https://github.com/netease-youdao/LobsterAI/pull/1831) | kayo5994 | Sanitized sensitive logs in main process and IM module |
| [#1832](https://github.com/netease-youdao/LobsterAI/pull/1832) | kayo5994 | Restricted `store:*` IPC cross-process access and narrowed `ipcRenderer` bridge |
| [#1833](https://github.com/netease-youdao/LobsterAI/pull/1833) | kayo5994 | Added scheme whitelist for `shell.openExternal` (blocking `file:`, `javascript:`, `data:`) |
| [#1835](https://github.com/netease-youdao/LobsterAI/pull/1835) | kayo5994 | Removed duplicate error messages on `continueSession` failure |

**Key advancement:** A significant security hardening burst (PRs #1831–#1833) addressed log leakage, IPC privilege escalation, and unsafe URL handling — all critical for a desktop app with sensitive credentials.

## 4. Community Hot Topics

| Issue/PR | Author | Comments | Reactions | Focus |
|----------|--------|----------|-----------|-------|
| [#1813](https://github.com/netease-youdao/LobsterAI/issues/1813) — DeepSeek V4 LLM request failure | Sun-Ke | 8 | 0 | Provider schema rejection |
| [#1797](https://github.com/netease-youdao/LobsterAI/issues/1797) — Batch conversation deletion | qxjysd | 2 | 1 | Context management UX |
| [#1698](https://github.com/netease-youdao/LobsterAI/issues/1698) — Gateway port conflict with 智企帝王蟹 | yy987y | 3 | 0 | Multi-product coexistence |
| [#1783](https://github.com/netease-youdao/LobsterAI/issues/1783) — Diff broken after update | MiracleOfrRevolutionary | 2 | 0 | Core editing tool regression |
| [#1688](https://github.com/netease-youdao/LobsterAI/issues/1688) — Dynamic temperature control | catubibu | 1 | 0 | LLM parameter tuning |

**Underlying needs:**
- **Product ecosystem coexistence** (Issue #1698): Users running both 有道龙虾 and 智企帝王蟹 expect port isolation — a signal that multi-instance architecture needs deeper design.
- **LLM provider compatibility** (Issue #1813): As users adopt newer models (DeepSeek V4), schema/tool-payload validation errors indicate the provider abstraction layer may need updating.
- **Context hygiene** (Issue #1797): Batch conversation deletion is a strong request — users are accumulating stale context and want better session management.
- **Fine-grained control** (Issue #1688): Keyword-based temperature adjustment mid-conversation is a power-user feature request suggesting the community values runtime LLM parameter tuning.

## 5. Bugs & Stability

| Severity | Issue/PR | Summary | Fix Status |
|----------|----------|---------|------------|
| 🔴 High | [#1813](https://github.com/netease-youdao/LobsterAI/issues/1813) | DeepSeek V4 LLM requests rejected — provider schema/tool payload issue | Closed |
| 🔴 High | [#1796](https://github.com/netease-youdao/LobsterAI/issues/1796) | Write/Edit tools consistently failing | Closed |
| 🟠 Medium | [#1698](https://github.com/netease-youdao/LobsterAI/issues/1698) | Gateway port conflict with 智企帝王蟹 on macOS | Open |
| 🟠 Medium | [#1783](https://github.com/netease-youdao/LobsterAI/issues/1783) | Edit diff broken after update — `extractDiffFromToolInput` bug identified | Open |
| 🟡 Low | [#1714](https://github.com/netease-youdao/LobsterAI/issues/1714) | Windows 11 install — icons rendered white/invalid | Open |
| 🟡 Low | [#1751](https://github.com/netease-youdao/LobsterAI/issues/1751) | Scheduled task notification text incorrect | Open |
| 🟡 Low | [#1744](https://github.com/netease-youdao/LobsterAI/issues/1744) | Unspecified bug report (attachment failed) | Open |

**Notable fix in progress:** Issue #1783 has a detailed root-cause analysis from the reporter — the `extractDiffFromToolInput` function in the renderer only checks top-level `oldText`/`newText` keys. This bug needs a code fix in the frontend layer.

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Summary | Likelihood for Next Release |
|----------|---------|----------------------------|
| [#1797](https://github.com/netease-youdao/LobsterAI/issues/1797) | Batch conversation deletion | 🟢 High — low effort, high impact on UX |
| [#1688](https://github.com/netease-youdao/LobsterAI/issues/1688) | Dynamic temperature control via keyword | 🟡 Medium — requires LLM pipeline integration |
| [#1745](https://github.com/netease-youdao/LobsterAI/issues/1745) | OAuth2/modern auth for Outlook/email | 🟡 Medium — security-sensitive, needs provider support |
| [#1682](https://github.com/netease-youdao/LobsterAI/pull/1682) | TTS for AI replies (Cowork) — open PR | 🟢 High — already implemented, awaiting merge |
| [#1769](https://github.com/netease-youdao/LobsterAI/pull/1769) | Skeleton loading screen for Cowork init — open PR | 🟢 High — UX polish, ready to merge |

**Signals:** The project is investing in security infrastructure and UX polish. Several PRs (TTS, skeleton loading, empty states) are UI enhancements queued for upcoming releases.

## 7. User Feedback Summary

**Satisfaction:**
- Agent template import/export (#1691) and image avatars (#1760) address long-standing personalization and sharing needs — well-received internally.
- Security hardening (PRs #1831–#1833) responds to real concerns about credential exposure in logs and IPC channels.
- IM instance deletion confirmation (#1690) is a small but appreciated quality-of-life improvement.

**Dissatisfaction / Pain Points:**
- **Write/Edit tools broken** (#1796) — core functionality regression affecting daily users for days.
- **DeepSeek V4 compatibility** (#1813) — 8 comments indicate significant user interest in the latest model.
- **Diff display broken** (#1783) — a power-user feature; the reporter provided a detailed bug analysis, showing strong engagement.
- **Port conflicts with sibling products** (#1698) — "必现" (100% reproducible) on macOS Tahoe 26.4, suggesting a systemic issue in the multi-product packaging strategy.
- **Context bloat** (#1797) — no built-in way to delete conversations; user explicitly requested batch deletion.

## 8. Backlog Watch

| Issue/PR | Author | Updated | Concern |
|----------|--------|---------|---------|
| [#1698](https://github.com/netease-youdao/LobsterAI/issues/1698) | yy987y | 2026-08-16 | Port conflict with 智企帝王蟹 — **100% reproducible** on macOS, stale since April |
| [#1783](https://github.com/netease-youdao/LobsterAI/issues/1783) | MiracleOfrRevolutionary | 2026-08-16 | Edit diff broken — **root cause identified**, awaiting maintainer action since April |
| [#1714](https://github.com/netease-youdao/LobsterAI/issues/1714) | Caoxiongk | 2026-08-16 | Windows 11 install icons broken — high visual impact on first run |
| [#1688](https://github.com/netease-youdao/LobsterAI/issues/1688) | catubibu | 2026-08-16 | Dynamic temperature control — power-user feature, no response since April |
| [#1745](https://github.com/netease-youdao/LobsterAI/issues/1745) | jiutianxvanyin | 2026-08-16 | Outlook OAuth2 not supported — email integration blocked for enterprise users |
| [#2452](https://github.com/netease-youdao/LobsterAI/pull/2452) | ump45nose | 2026-08-16 | Provider prefix preservation for slashed model IDs — recent fix, needs review |
| [#1682](https://github.com/netease-youdao/LobsterAI/pull/1682) | gongzhi-netease | 2026-08-16 | TTS for AI replies — fully implemented, pending merge for ~4 months |
| [#1769](https://github.com/netease-youdao/LobsterAI/pull/1769) | xiaoye5200 | 2026-08-16 | Skeleton loading screen — ready to merge, stale since April |

**Overall Assessment:** The project is in a healthy state with active contributor engagement. The most critical backlog items are the **DeepSeek V4 compatibility issue** (#1813, closed), **Write tool regression** (#1796, closed), and the **edit diff bug** (#1783, open with identified root cause). The security hardening PRs (#1831–#1835) represent a significant quality uplift. Several contributor PRs have been open since April and warrant maintainer attention for merging.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-17

## 1. Today's Overview

Moltis is seeing moderate developer activity with 3 issues and 6 PRs updated in the last 24 hours. The project is in a maintenance-heavy cycle: 5 of 6 recent PRs were closed (merged), including two bug fixes and a test stabilization, while 2 new issues were opened. No new releases were cut this cycle. Overall health is positive — the team is actively closing out pre-existing bugs and test flakiness, though the `Format` CI gate on `main` remains broken, which is a signal worth monitoring.

## 2. Releases

No new releases were published.

## 3. Project Progress

**Merged / Closed PRs:**

- **[PR #1147](https://github.com/moltis-org/moltis/issues/1147)** — *fix(caldav): honor list_events time ranges* — Replaces full calendar resource fetches with an RFC 4791 `calendar-query` REPORT, significantly improving CalDAV event-listing performance and correctness for time-bounded queries.
- **[PR #1093](https://github.com/moltis-org/moltis/issues/1093)** — *Add channel activity log visibility settings* — Introduces per-account, per-channel, and per-user `activity_log` visibility controls (`all` / `errors_only` / `off`), giving users granular privacy over channel reply targets.
- **[PR #1201](https://github.com/moltis-org/moltis/issues/1201)** — *fix(gateway): thread start_background_tasks into the memory runtime builder* — Resolves a compilation regression introduced by PR #1158, restoring the headless runtime initialization path.
- **[PR #1203](https://github.com/moltis-org/moltis/issues/1203)** — *test(gateway): run the push fanout test on a paused clock* — Eliminates an intermittent test failure by using a simulated clock, directly addressing [Issue #1193](https://github.com/moltis-org/moltis/issues/1193).
- **[PR #1186](https://github.com/moltis-org/moltis/issues/1186)** — *fix(vault): normalize recovery phrase before hashing* — Ensures vault recovery phrases are normalized (dashes stripped, uppercased) before hashing, aligning stored hashes with the unsealing derivation path and preventing recovery failures for differently-cased inputs.

**Open PRs:**

- **[PR #1204](https://github.com/moltis-org/moltis/issues/1204)** — *feat: add MiniMax Code ACP agent* — Adds a new `acp-minimax-code` external-agent kind backed by `mcode acp`, extending Moltis' agent registry with MiniMax Code support.

## 4. Community Hot Topics

- **[Issue #1205](https://github.com/moltis-org/moltis/issues/1205)** — *Heartbeat ignores configured active hours and runs continuously* — A bug report from IlyaBizyaev flagging that the heartbeat subsystem disregards active-hour configuration. This suggests users rely on throttled heartbeats for battery/network efficiency, and the current behavior may cause unintended resource consumption. **No fix PR yet.**
- **[Issue #1202](https://github.com/moltis-org/moltis/issues/1202)** — *Format CI gate is red on main: two files over the 1500-line limit* — Reported by Lstarsky0, the same contributor driving test and build fixes. Two files (`store.rs` at 1799 lines, `admin.rs` at 1531 lines) exceed the enforced limit. This is a sustained pain point — large files resist formatting and signal architectural debt.
- **[PR #1204](https://github.com/moltis-org/moltis/issues/1204)** — The MiniMax Code ACP agent PR is the only open feature PR, indicating community interest in expanding the external-agent ecosystem. No comments or reactions yet.

## 5. Bugs & Stability

| Severity | Item | Description | Fix Status |
|---|---|---|---|
| **High** | [Issue #1205](https://github.com/moltis-org/moltis/issues/1205) | Heartbeat ignores active hours, runs continuously | No fix PR |
| **Medium** | [Issue #1193](https://github.com/moltis-org/moltis/issues/1193) | Flaky push fanout timeout test under full-suite load | Fixed in [PR #1203](https://github.com/moltis-org/moltis/issues/1203) (merged) |
| **Medium** | [PR #1201](https://github.com/moltis-org/moltis/issues/1201) | Gateway compilation failure on `main` | Merged |
| **Low** | [PR #1186](https://github.com/moltis-org/moltis/issues/1186) | Vault recovery phrase hashing inconsistency | Merged |
| **Low** | [Issue #1202](https://github.com/moltis-org/moltis/issues/1202) | Format CI red due to file-size limits | No fix PR |

The compilation break on `main` has been resolved. The heartbeat bug (#1205) is the most impactful open issue — it affects core reliability for users who depend on active-hour scheduling.

## 6. Feature Requests & Roadmap Signals

- **[PR #1204](https://github.com/moltis-org/moltis/issues/1204)** — *MiniMax Code ACP agent* is the strongest roadmap signal. If merged, it adds a new external-agent provider to the default registry, expanding Moltis' agent ecosystem. The PR is self-contained (config validation, auto-discovery, UI fixtures) and follows established patterns, making it a likely candidate for the next release.
- **[PR #1093](https://github.com/moltis-org/moltis/issues/1093)** — Channel activity log visibility was already merged, suggesting the project is actively investing in privacy-granularity features. Expect similar per-resource visibility controls in future iterations.

## 7. User Feedback Summary

- **Heartbeat misbehavior** ([#1205](https://github.com/moltis-org/moltis/issues/1205)): Users configure active hours expecting the heartbeat to respect them; the current continuous operation is a disconnect between expectation and behavior.
- **Vault recovery reliability** ([#1186](https://github.com/moltis-org/moltis/issues/1186)): Recovery phrase normalization is a high-stakes area — users who type phrases with dashes or mixed case could previously be unable to unseal their vaults. The merged fix addresses a real pain point.
- **CalDAV performance** ([#1147](https://github.com/moltis-org/moltis/issues/1147)): Fetching every calendar resource instead of using time-bounded queries was a performance bottleneck. The fix aligns with user expectations for responsive calendar integration.
- **Activity log privacy** ([#1093](https://github.com/moltis-org/moltis/issues/1093)): Users want control over who sees their activity — the multi-level visibility settings (account / channel / user) reflect this need.

## 8. Backlog Watch

- **[Issue #1205](https://github.com/moltis-org/moltis/issues/1205)** — Heartbeat active-hours bug: open, no assignee, no fix PR. Given the impact on resource usage, this should be prioritized.
- **[Issue #1202](https://github.com/moltis-org/moltis/issues/1202)** — Format CI gate red: two files well over the 1500-line limit. This blocks CI hygiene and will persist until either the files are split or the limit is adjusted. Maintainer attention needed.
- **[PR #1204](https://github.com/moltis-org/moltis/issues/1204)** — MiniMax Code ACP agent: open with no reviews or comments yet. Worth triaging to keep the feature pipeline moving.

---

*Data source: [github.com/moltis-org/moltis](https://github.com/moltis-org/moltis)*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-17

---

## 1. Today's Overview

CoPaw (agentscope-ai/CoPaw) shows **active community engagement** with 12 issues and 11 PRs updated in the last 24 hours. Four issues were closed, including two critical bug fixes and a proposal, while the majority of open items remain in active discussion. No new releases were published today, suggesting the team is focusing on stabilization rather than shipping. The project's issue velocity is healthy, with several first-time contributors submitting PRs—a positive signal for community growth.

---

## 2. Releases

**No new releases today.** The current latest version remains **v2.1.0**.

---

## 3. Project Progress

### Merged / Closed PRs (2 today)

- **PR #7064** — `fix(cli): sync top-level text on cron update --text for agent jobs` ([link](https://github.com/agentscope-ai/CoPaw/pull/7064))
  Fixes a silent bug where `qwenpaw cron update <id> --text "<prompt>"` on agent-type cron jobs updated only the nested request content but left the top-level `text` field stale, making the command appear successful while the prompt remained unchanged.

- **PR #7055** — `fix(cli): sync top-level text on agent cron --text update (#7048)` ([link](https://github.com/agentscope-ai/CoPaw/pull/7055))
  Duplicate/concurrent fix for the same issue #7048, closed in favor of #7064.

### Key Open PRs Advancing

- **PR #6940** — `feat(pawapp): add native DataPaw app runtime and durable analysis workspace` — A significant feature introducing a native app runtime for DataPaw with a durable analysis workspace. In review. ([link](https://github.com/agentscope-ai/CoPaw/pull/6940))
- **PR #6302** — `feat: unify provider discovery, model metadata, routing, and agent controls` — A major architectural PR unifying provider/model systems with catalog-driven discovery and capability-aware routing. Long-running, still open. ([link](https://github.com/agentscope-ai/CoPaw/pull/6302))
- **PR #6975** — `fix(console): update context-usage ring after compact` — Fixes a UI bug where the context-usage ring stalled after `/compact` due to SSE event ordering. ([link](https://github.com/agentscope-ai/CoPaw/pull/6975))
- **PR #7072** — `feat(console): add background chat task list API` — Adds a list endpoint for background tasks submitted via `submit_to_agent`, enabling multi-agent coordination visibility. ([link](https://github.com/agentscope-ai/CoPaw/pull/7072))
- **PR #7071** — `fix(agents): make view_video inline cap configurable instead of hardcoded 2 MB` — Removes a hard 2 MB ceiling on video inline uploads, respecting provider-level `max_inline_media_bytes`. ([link](https://github.com/agentscope-ai/CoPaw/pull/7071))
- **PR #7070** — `fix(agents): promote view_video results on OpenAI Responses API path` — Fixes silent video failure on OpenAI Responses API providers (e.g., Volcengine Ark). ([link](https://github.com/agentscope-ai/CoPaw/pull/7070))
- **PR #7069** — `fix(console): render data-URL images in historical messages on session reload` — Fixes broken image thumbnails after chat re-open. ([link](https://github.com/agentscope-ai/CoPaw/pull/7069))
- **PR #7067** — `fix(console): switch agent from /chat/:agentId/:sessionId` — Adds agent ID to deep links for multi-agent workspaces. ([link](https://github.com/agentscope-ai/CoPaw/pull/7067))
- **PR #7066** — `fix(drivers): persist rotated refresh_token for OAuth2 auth-code providers` — Fixes OAuth token rotatoin persistence for providers like XMind. ([link](https://github.com/agentscope-ai/CoPaw/pull/7066))

---

## 4. Community Hot Topics

| Issue | Type | Comments | Link |
|-------|------|----------|------|
| #7003 — Memory for QwenPaw agents (ViBo) | Proposal | 3 | [link](https://github.com/agentscope-ai/CoPaw/issues/7003) |
| #7063 — Tool call crash | Bug | 3 | [link](https://github.com/agentscope-ai/CoPaw/issues/7063) |
| #7048 — Cron update silent failure | Bug | 2 | [link](https://github.com/agentscope-ai/CoPaw/issues/7048) |
| #7052 — Plugin API system_prompt permission | Feature | 2 | [link](https://github.com/agentscope-ai/CoPaw/issues/7052) |
| #6471 — Cron misfire after idle | Bug | 2 | [link](https://github.com/agentscope-ai/CoPaw/issues/6471) |

**Analysis:** The community is most engaged around **reliability and observability**. Issue #7003's ViBo proposal (97.5% token reduction for memory) taps into a real cost concern as users scale. The cron-related issues (#7048, #6471) indicate that scheduled task reliability is a pain point for production users. The plugin system prompt request (#7052) reflects enterprise users wanting tighter control over agent behavior in shared interfaces.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **Critical** | [#7063](https://github.com/agentscope-ai/CoPaw/issues/7063) | Consistent crash when agent executes tool call — `async for` used on a coroutine instead of async generator in `_execute_tool_call` | ❌ None yet |
| **High** | [#7076](https://github.com/agentscope-ai/CoPaw/issues/7076) | `qwenpaw-creator`: LLM model config returns 404 error on v2.1.0 | ❌ None yet |
| **High** | [#7074](https://github.com/agentscope-ai/CoPaw/issues/7074) | Random crashes during normal operation; requires page refresh to recover — high frequency | ❌ None yet |
| **Medium** | [#7065](https://github.com/agentscope-ai/CoPaw/issues/7065) | Chat history truncated after ~7 rounds; earlier messages invisible even when scrolling | ❌ None yet |
| **Medium** | [#6471](https://github.com/agentscope-ai/CoPaw/issues/6471) | Cron misfire after long event-loop idle — APScheduler AsyncIOScheduler fails to trigger | ❌ None yet |
| **Low** | [#7048](https://github.com/agentscope-ai/CoPaw/issues/7048) | Cron update `--text` silently fails on agent-type jobs | ✅ PR #7064 closed |

**Notable:** Two critical bugs (tool-call crash and creator 404) and a high-frequency instability issue remain unfixed. The tool-call crash (#7063) is a regression likely introduced in v2.1.0 and should be prioritized.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Description | Likelihood for Next Release |
|-------|-------------|----------------------------|
| [#7052](https://github.com/agentscope-ai/CoPaw/issues/7052) | Add `system_prompt` permission to plugin API for enterprise isolation | Medium — clear enterprise need |
| [#7075](https://github.com/agentscope-ai/CoPaw/issues/7075) | Detailed cron task execution logs (start time, duration, result) | High — directly addresses #6471 pain, complements existing cron feature |
| [#7062](https://github.com/agentscope-ai/CoPaw/issues/7062) | Per-agent / per-session `reasoning_effort` override for cloud models | Medium-High — useful for multi-role deployments |
| [#7068](https://github.com/agentscope-ai/CoPaw/issues/7068) | Extend file viewer to C#, shader files (.shader/.hlsl/.gdshader) | Low — niche but requested by game-dev workflow users |
| [#7003](https://github.com/agentscope-ai/CoPaw/issues/7003) | ViBo: encrypted, token-efficient memory for agents | Low-Medium — proposal stage, requires integration work |

**Prediction:** Issue #7075 (cron detail logging) and #7062 (per-agent reasoning_effort) are the strongest candidates for the next release, as they align with existing infrastructure and address widely voiced needs.

---

## 7. User Feedback Summary

- **Frustration with cron reliability:** Users report both silent update failures (#7048) and scheduler misfires after idle (#6471), indicating the cron subsystem needs robustness investment.
- **Crash frequency in Console:** Issue #7074 describes high-frequency random crashes requiring manual page refresh — a major UX pain point for daily users.
- **Enterprise plugin constraints:** Issue #7052 highlights that plugin authors cannot isolate system prompts, exposing internal prompts in shared会话 interfaces — a blocker for B2B adoption.
- **Tool-call regression:** The v2.1.0 crash on tool execution (#7063) is a serious regression affecting core agent functionality.
- **Positive signal:** Strong first-time contributor engagement (PRs #7064, #7055, #7071, #7070, #7069, #7067, #7066 all from first-time contributors), suggesting a growing and healthy community.

---

## 8. Backlog Watch

| Item | Days Open | Risk |
|------|-----------|------|
| [#7063](https://github.com/agentscope-ai/CoPaw/issues/7063) — Tool call crash (critical) | 1 day | 🔴 High — core functionality broken, no fix PR yet |
| [#7076](https://github.com/agentscope-ai/CoPaw/issues/7076) — Creator 404 on model config | 0 days | 🟠 High — blocks onboarding |
| [#7074](https://github.com/agentscope-ai/CoPaw/issues/7074) — Random Console crashes | 1 day | 🟠 High — frequent, degrades UX |
| [#6471](https://github.com/agentscope-ai/CoPaw/issues/6471) — Cron misfire after idle | 22 days | 🟡 Medium — long-standing, no fix PR |
| [#7065](https://github.com/agentscope-ai/CoPaw/issues/7065) — Chat history truncation | 1 day | 🟡 Medium — no fix PR |
| [#6302](https://github.com/agentscope-ai/CoPaw/pull/6302) — Unified provider/model system | 27 days | 🟡 Medium — large PR, may need maintainer review bandwidth |

**Recommendation:** The maintainers should prioritize **#7063** (tool-call crash) and **#7074** (Console instability) as they affect core user workflows. The 22-day-old **#6471** cron misfire also warrants attention alongside the newly filed **#7075** feature request, as they share the same subsystem.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-17

## 1. Today's Overview

ZeroClaw shows strong contributor momentum with **48 issues** and **50 PRs** updated in the last 24 hours, signaling sustained development velocity. Two issues were closed today (#9953, #9580), including a significant security hardening merge, while 46 issues and 46 PRs remain open and active. No new release was published, but the project is clearly working toward the 0.8.x series with active RFC ratification and parallel-runtime test stabilization underway.

## 2. Releases

No new releases in the reporting window. The project remains on the **0.8.x beta track**, with RFC #6808 (Work Lanes) currently at revision 25 and rolled out through 0.8.4.

## 3. Project Progress

**Merged/Closed today:**

- **[#9580](https://github.com/zeroclaw-labs/zeroclaw/pull/9580) — fix(security): harden built-in HTTP egress on the shared network guard** (CLOSED). Dropped all audited non-global IPv4/IPv6 addresses and moved shared network-classification primitives into `zeroclaw-infra::net_guard` for reuse by the plugin egress work. This unblocks PRs #9137, #9582, and #9584, which stack on its head and implement the staged plugin egress policy.
- **[#9953](https://github.com/zeroclaw-labs/zeroclaw/issues/9953) — [Bug]: SOP step schema validation rejects a double-encoded output object** (CLOSED). Fixed S2 degraded behavior where auto-mode SOP steps with `output` schemas failed when the agent turn's final message arrived double-encoded.

**In progress (high-visibility PRs):**
- [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713) — SSRF gate fix for `file_download` allowed private hosts opt-in
- [#9126](https://github.com/zeroclaw-labs/zeroclaw/pull/9126) — typed instance config validation for plugins
- [#9002](https://github.com/zeroclaw-labs/zeroclaw/pull/9002) — keep agent turns alive after WebSocket viewer disconnect
- [#9606](https://github.com/zeroclaw-labs/zeroclaw/pull/9606) — honor runtime proxy for OpenAI Responses API
- [#9582](https://github.com/zeroclaw-labs/zeroclaw/pull/9582) + [#9584](https://github.com/zeroclaw-labs/zeroclaw/pull/9584) — staged plugin egress policy (stages 2 & 3)
- [#9745](https://github.com/zeroclaw-labs/zeroclaw/pull/9745) — per-agent knowledge graph attribution and scoping

## 4. Community Hot Topics

| Issue / PR | Comments | Focus |
|---|---|---|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) — RFC: Work Lanes, Board Automation, Label Cleanup | 23 | Governance / project management automation |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — RFC: ZeroClaw Chat Completions profile | 22 | OpenAI-compatible protocol adoption for broad client ecosystem |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) — RFC: Unified attachment architecture | 17 | Web chat + channel attachment unification |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) — RFC: Provenance & conversation binding | 14 | Internally-initiated agent turn contract |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) — RFC: Security posture & universal ingress | 14 | Cross-cutting credential and sandbox policy |
| [#6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) — RFC: Prefer lighter core via external integrations | 14 | Core bloat reduction strategy |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Tracker: Maintainer decision queue | 13 | Governance process coordination |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) — RFC: Realtime speech-to-speech for Gemini Live | 13 | Realtime voice channel |

**Analysis:** The community is heavily invested in **protocol interoperability** (#8603 Chat Completions, #8780 Gemini Live realtime) and **architecture slimming** (#6165, #9488). Governance fatigue is evident with multiple tracker and RFC coordination issues. The project is balancing rapid feature expansion against core maintainability.

## 5. Bugs & Stability

| Issue | Severity | Status | Fix PR? |
|---|---|---|---|
| [#10013](https://github.com/zeroclaw-labs/zeroclaw/issues/10013) — Edge TTS cancellation test race | S1 — workflow blocked | Open, accepted | Yes — [#10011](https://github.com/zeroclaw-labs/zeroclaw/issues/10011) |
| [#10006](https://github.com/zeroclaw-labs/zeroclaw/issues/10006) — `endpoint_lock_is_held_through_guard_cleanup` flakes | P1 | In progress | Linked to test hardening |
| [#9965](https://github.com/zeroclaw-labs/zeroclaw/issues/9965) — ETXTBSY under parallel runtime gate | P1 | Open, accepted | Yes — [#10011](https://github.com/zeroclaw-labs/zeroclaw/issues/10011) |
| [#9655](https://github.com/zeroclaw-labs/zeroclaw/issues/9655) — Approval cards carry no position | P1 | Open, accepted | No PR yet |
| [#9811](https://github.com/zeroclaw-labs/zeroclaw/issues/9811) — `/health` reports unconnected channel as healthy | P1 | Open, accepted | No PR yet |
| [#10020](https://github.com/zeroclaw-labs/zeroclaw/issues/10020) — Agentic independent delegates ignore target thinking policy | S2 | In progress | No PR yet |
| [#10037](https://github.com/zeroclaw-labs/zeroclaw/issues/10037) — `POST /api/cron` silently stores invalid `session_target` | S2 | In progress | No PR yet |

**Stability theme:** The **parallel runtime test gate** is a persistent pain point, with three flaky-test issues (#9965, #10006, #10013) all tied to runtime-written executable fixtures under multithreaded test processes. This is a known infrastructure-level issue with active mitigation in progress.

## 6. Feature Requests & Roadmap Signals

| Issue | Priority | Likelihood for Next Release |
|---|---|---|
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) — Chat Completions profile | P2 | **High** — broad client compatibility demand; RFC drafted and actively discussed |
| [#8780](https://github.com/zeroclaw-labs/zeroclaw/issues/8780) — Gemini Live speech-to-speech | P2 | Medium — v2 rewritten to broker contract; still needs maintainer review |
| [#9488](https://github.com/zeroclaw-labs/zeroclaw/issues/9488) — Unified attachment architecture | P2 | Medium — proposed, needs human sponsor follow-up |
| [#7887](https://github.com/zeroclaw-labs/zeroclaw/issues/7887) — Date-range conditional cron schedules | P3 | Lower — accepted but P3 priority |
| [#7881](https://github.com/zeroclaw-labs/zeroclaw/issues/7881) — Provider fallback circuit breakers | P2 | Medium-High — accepted, solves real reliability pain |
| [#7883](https://github.com/zeroclaw-labs/zeroclaw/issues/7883) — Intra-family fallback notices | P3 | Lower |
| [#10025](https://github.com/zeroclaw-labs/zeroclaw/issues/10025) — zeroclaw swarm TUI | P2 | Unknown — just filed, needs review |
| [#6998](https://github.com/zeroclaw-labs/zeroclaw/issues/6998) — Schema-validated memory consolidation | P2 | Medium — accepted, addresses fragile JSON parsing path |

**Prediction:** The **Chat Completions profile** (#8603) and **provider fallback circuit breakers** (#7881) are the strongest candidates for inclusion in the next 0.8.x release, given their accepted status and clear user demand.

## 7. User Feedback Summary

- **Client ecosystem friction:** Multiple users (LobeChat, Aider, LangChain, Open WebUI) need OpenAI Chat Completions compatibility — currently only WebSocket/ACP/webhooks are supported (#8603).
- **Telegram group-chat ambiguity:** Shared sessions in Telegram groups make it impossible to distinguish per-user context; a `per_user_session` toggle is needed (#9772 PR, #6565 root issue).
- **Approval UX confusion:** Back-to-back approval cards from a single message are indistinguishable before tapping, causing operator errors (#9655).
- **Health endpoint misleading:** `/health` reports channels as healthy even when they've never connected (invalid Telegram bot token case) (#9811).
- **Delegate thinking policy ignored:** Independent agentic delegates don't inherit the target agent's `thinking` configuration (#10020).
- **Dependency hygiene:** Long-tail integrations bloat the core; users want a lighter default installation (#6165).
- **Test instability:** Parallel runtime tests intermittently fail on unrelated PRs due to race conditions in test fixtures (#9965, #10006, #10013).

## 8. Backlog Watch

| Issue | Days Open | Why It Matters |
|---|---|---|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) — Work Lanes RFC | ~89 days | Governance process affecting all maintainers; ratified but rollout incomplete |
| [#6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165) — Prefer lighter core | ~112 days | Strategic direction; unresolved since April |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) — Security posture RFC | ~113 days | Cross-cutting security policy; needs maintainer review |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) — Provenance & binding RFC | ~114 days | Foundation for internally-initiated agent turns |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) — Maintainer decision queue | ~74 days | Coordination tracker for all the above |
| [#7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822) — WASM plugin lifecycle hooks | ~92 days | Blocks third-party plugin audit capabilities |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) — Wire protocol first-class | ~81 days | Affects provider onboarding strategy |

**Notable closed-but-unresolved:** [#8691](https://github.com/zeroclaw-labs/zeroclaw/issues/8691) tracks ADR baseline restoration that appears stalled. The project has strong RFC volume but maintainer review capacity is the bottleneck.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*