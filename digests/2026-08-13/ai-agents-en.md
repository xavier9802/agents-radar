# OpenClaw Ecosystem Digest 2026-08-13

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-13 02:27 UTC

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



# OpenClaw Project Digest — 2026‑08‑13

## 1. Today's Overview
OpenClaw shows **very high activity** with 500 issues and 500 pull requests updated in the last 24 hours. Of the issues, 403 remain open/active and 97 closed; PRs stand at 359 open and 141 merged/closed. No new releases were published. The project is clearly in a heavy maintenance and iteration cycle, with a strong focus on session‑state reliability, subagent orchestration, and gateway stability.

## 2. Releases
*None.* No new versions were published today.

## 3. Project Progress
**Merged / closed PRs today:**
- **#122879** – Fix CI timeout in the `channels add` command test suite (`slack`, `telegram`, `buzz`).  
- **#122912** – Preserve bundled‑plugin inventory during Parallels npm‑update matrix runs.  
- **#122924** – Fix Code Mode dead‑ends on oversized tool results; now returns bounded output instead of terminating the turn.  
- **#122921** – Stop repeated cold dependency rebuilds in canonical `main` CI.  

These changes improve CI reliability, plugin‑update convergence, and Code Mode robustness.

## 4. Community Hot Topics
| Issue | Comments | Tags | Link |
|-------|----------|------|------|
| **#121058** – Silent reply failures recurring after #116277 closed | 91 | P1, session‑state, message‑loss | [Issue](https://github.com/openclaw/openclaw/issues/121058) |
| **#7707** – Memory Trust Tagging by Source | 45 | Enhancement, security, session‑state | [Issue](https://github.com/openclaw/openclaw/issues/7707) |
| **#44925** – Subagent completion silently lost (no retry/notification) | 26 | P1, session‑state, message‑loss | [Issue](https://github.com/openclaw/openclaw/issues/44925) |
| **#77598** – Track live dev agent behavior and trajectory | 23 | Observation, session‑state | [Issue](https://github.com/openclaw/openclaw/issues/77598) |
| **#57901** – Safeguard compaction ignores `compaction.model` config | 15 | P2, session‑state, auth‑provider | [Issue](https://github.com/openclaw/openclaw/issues/57901) |

**Underlying needs:** The top‑voted issue (#121058) shows that a previous fix did not fully resolve silent reply failures—a clear signal that the subagent completion pipeline remains fragile. Memory‑trust tagging (#7707) reflects growing security awareness around memory poisoning. The high comment counts on subagent‑loss issues (#44925, #67777, #92433) indicate that multi‑agent orchestration reliability is a critical community pain point.

## 5. Bugs & Stability
| Issue | Severity | Summary | Fix PR? |
|-------|----------|---------|---------|
| **#121058** | P1 | Silent reply failures recur after supposed fix. | No |
| **#44925** | P1 | Subagent completion silently lost; no retry/notification. | No |
| **#67777** | P1 | Subagent completion delivery lost on direct‑announce timeout/drain. | No |
| **#92433** | P1 | Subagent completion silently dropped when announce steers into a finished run. | No |
| **#91363** | P1 | Isolated cron consistently fails with “LLM request failed.” | No |
| **#89278** | P1 | Codex OAuth refresh succeeds but cron/heartbeat fail with 10s auth timeout. | No |
| **#111498** | P1 | Main agent blocked by persistent workspace‑state migration after Anthropic auth recovery. | No |
| **#72015** | P1 | Active‑memory blocks replies; QMD boot initialization overloads gateway. | No |
| **#40611** | P1 | Heartbeat drift fix causes aggressive retry that blocks Telegram. | No |
| **#54488** | P1 | Session lane starvation: followup drain monopolizes lane for 20‑30 min. | No |
| **#43374** | P1 | All LLM API calls time out simultaneously (multi‑agent concurrency). | No |
| **#97983** | P1 | iOS/WebChat messages append to transcript but do not trigger assistant replies. | No |
| **#97616** | P1 | OpenClaw leaks unreaped hook/tool child processes, causing zombie accumulation. | No |
| **#37966** | P2 | `cacheRetention` ignored for LiteLLM‑proxied Anthropic models. | No |
| **#115001** | P2 | Hybrid memory search returns spurious 1.0 similarity scores via FTS LIKE‑fallback. | No |
| **#114154** | P2 | `bundle‑mcp` tool passes policy and server is healthy, but agent never bundles it. | No |
| **#77733** | P2 | Bare `/new` and `/reset` no longer trigger persona greeting (regression vs 4.x). | No |

**Trend:** The majority of critical bugs relate to **session‑state loss, subagent completion delivery, and authentication/timeout handling**. Several of these (e.g., #44925, #67777, #92433) are variations of the same subagent‑completion pipeline fragility, suggesting a systemic issue that will require architectural work.

## 6. Feature Requests & Roadmap Signals
| Issue | Type | Summary | Link |
|-------|------|---------|------|
| **#7707** | Enhancement | Memory Trust Tagging by Source – tag memory entries by trust level to prevent memory poisoning. | [Issue](https://github.com/openclaw/openclaw/issues/7707) |
| **#45758** | Enhancement | Support YAML as config file format alongside JSON5. | [Issue](https://github.com/openclaw/openclaw/issues/45758) |
| **#50199** | Enhancement | Skill Priority Configuration – resolve overlapping skill selection. | [Issue](https://github.com/openclaw/openclaw/issues/50199) |
| **#45771** | Enhancement | Built‑in pace‑aware rate limiting for autonomous agents. | [Issue](https://github.com/openclaw/openclaw/issues/45771) |
| **#41366** | Enhancement | Durable natural‑language rule learning + explicit multi‑mention reply semantics. | [Issue](https://github.com/openclaw/openclaw/issues/41366) |
| **#9016** | Enhancement | Expose OpenRouter usage cost to agent runtime. | [Issue](https://github.com/openclaw/openclaw/issues/9016) |
| **#45508** | Enhancement | Self‑hosted STT/TTS provider support in webchat (route through gateway). | [Issue](https://github.com/openclaw/openclaw/issues/45508) |

**Prediction:** The memory‑trust tagging (#7707) and pace‑aware rate limiting (#45771) align with security and reliability trends and are likely candidates for the next major release. YAML config support (#45758) is a low‑risk improvement that could be added soon.

## 7. User Feedback Summary
- **Subagent reliability is the dominant pain point.** Users report that subagent completions are silently lost, parent sessions become unresponsive, and completion payloads pollute the parent context (#44925, #96975, #47975).
- **Session‑state management is chaotic.** Memory is stored inconsistently across users, and session lane starvation causes inbound messages to be queued for 20‑30 minutes (#43747, #54488).
- **Auth‑provider integration is fragile.** Codex OAuth refresh succeeds but cron/heartbeat fails due to a 10‑second timeout (#89278); isolated cron jobs consistently fail at the model‑call‑started phase (#91363).
- **Tool‑output handling is problematic.** Oversized tool results in Code Mode destroy the entire call (#122924); LiteLLM‑proxied models ignore cache‑retention settings (#37966).
- **UX friction** remains around session sorting (#51028), gateway‑restart orphan messages (#16555), and Telegram/DM routing leaks (#41165).

Overall, users are experiencing **high frustration with reliability** in multi‑agent and multi‑session scenarios, while feature requests indicate a desire for better security, observability, and configuration flexibility.

## 8. Backlog Watch
| Issue | Created | Days Open | Tags | Link |
|-------|---------|-----------|------|------|
| **#7707** – Memory Trust Tagging | 2026‑02‑03 | ~192 | Enhancement, security, session‑state | [Issue](https://github.com/openclaw/openclaw/issues/7707) |
| **#9016** – OpenRouter usage cost exposure | 2026‑02‑04 | ~191 | Enhancement, auth‑provider | [Issue](https://github.com/openclaw/openclaw/issues/9016) |
| **#16555** – TTL/Expiry for Delivery Queue Messages | 2026‑02‑14 | ~181 | Enhancement, message‑loss | [Issue](https://github.com/openclaw/openclaw/issues/16555) |
| **#41165** – Telegram DMs pollute main session | 2026‑03‑09 | ~158 | P1, session‑state, message‑loss | [Issue](https://github.com/openclaw/openclaw/issues/41165) |
| **#41366** – Durable NL rule learning + multi‑mention semantics | 2026‑03‑09 | ~158 | Enhancement, session‑state | [Issue](https://github.com/openclaw/openclaw/issues/41366) |
| **#77598** – Track live dev agent behavior | 2026‑05‑05 | ~101 | Observation, session‑state | [Issue](https://github.com/openclaw/openclaw/issues/77598) |
| **#77700** – Prepared runtime resolution migration | 2026‑05‑05 | ~101 | Maintainer, session‑state | [Issue](https://github.com/openclaw/openclaw/issues/77700) |
| **#112385** – Compose RFC 0013 recovery points | 2026‑07‑21 | ~54 | Snapshot feature, session‑state | [PR](https://github.com/openclaw/openclaw/pull/112385) |

**Most urgent backlog items:** The Telegram DM routing leak (#41165) and the multi‑agent concurrency timeout issue (#43374) are P1 bugs that have been open for over five months without a fix. The snapshot‑recovery feature stack (#112385, #112865, #112896) is also waiting on author action and could significantly improve recovery guarantees.

---

*Digest generated from OpenClaw GitHub data as of 2026‑08‑13. All links point to the openclaw/openclaw repository.*

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal Assistant Open-Source Ecosystem
**Date: 2026-08-13 | Analyst: Agnes (Sapiens AI)**

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape in August 2026 is characterized by intense maintenance cycles across nearly all active projects, with reliability and session-state management emerging as the dominant engineering challenge. Six of twelve tracked projects show meaningful activity, while four report zero recent changes—suggesting consolidation or abandonment among smaller efforts. The ecosystem is converging on plugin architectures, OAuth/MCP reliability, and multi-channel routing as universal requirements, but divergence remains sharp around target platforms (desktop-first vs. gateway-first vs. cloud-hosted) and release discipline (rapid RC iteration vs. cautious maintenance). No project has achieved a mature, steady-state release cadence; all are either shipping pre-release candidates, refactoring core abstractions, or struggling with inherited stability debt.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Open Issues | Open PRs | Releases (24h) | Health Score* |
|---|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | 403 | 359 | 0 | ⚠️ 42/100 |
| **NanoBot** | 8 | 36 | ~12 | ~15 | 0 | 🟢 71/100 |
| **Hermes Agent** | 50 | 50 | ~85 | ~60 | 0 | 🟢 68/100 |
| **PicoClaw** | 6 | 3 | 3 | 3 | 0 | 🟡 55/100 |
| **NanoClaw** | 14 | 14 | ~20 | ~10 | 0 | 🟡 58/100 |
| **IronClaw** | 41 | 50 | ~30 | ~20 | 2 RCs | 🟢 74/100 |
| **LobsterAI** | 6 | 8 | 4 stale | 2 | 1 (yesterday) | 🟡 60/100 |
| **CoPaw** | 31 | 43 | ~25 | ~18 | 1 beta | 🟢 72/100 |
| **ZeroClaw** | 50 | 50 | ~40 | ~35 | 0 | 🟡 57/100 |
| **NullClaw** | 0 | 0 | — | — | — | 🔴 15/100 |
| **Moltis** | 0 | 0 | — | — | — | 🔴 15/100 |
| **ZeptoClaw** | 0 | 0 | — | — | — | 🔴 15/100 |

*Health Score synthesizes activity velocity, bug resolution rate, release cadence, and community engagement quality. Scale: 0–100.*

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Scale of engagement:** OpenClaw's 500+ issue/PR update count dwarfs every other project, indicating the largest active contributor base and the broadest deployment footprint requiring support.
- **Depth of multi-agent complexity:** OpenClaw is the only project where subagent orchestration reliability (silent completion loss, parent-session unresponsiveness, context pollution) dominates the issue tracker—suggesting it is the most ambitious in multi-agent workflow support.

**Technical Approach Differences:**
- Unlike IronClaw (which ships frequent RCs and runs structured bug-bashes) and CoPaw (which iterates on beta releases with UI polish), OpenClaw has no release in progress and is in a heavy maintenance/iteration cycle without a public release cadence.
- Compared to NanoBot and Hermes Agent—both of which are refactoring core abstractions (MCP lifecycle, plugin interfaces)—OpenClaw's refactoring focus is narrower: session-state reliability, gateway stability, and subagent pipeline integrity.
- ZeroClaw shares OpenClaw's attention to security hardening but approaches it through attestation consolidation and policy centralization rather than session-state debugging.

**Community Size Comparison:**
OpenClaw's community is an order of magnitude larger than any peer by raw issue/PR volume. NanoBot and Hermes Agent represent the next tier (~50–500 updates), while PicoClaw, NanoClaw, and LobsterAI occupy a mid-tier (~6–14 updates). Four projects show zero activity.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs Identified |
|---|---|---|
| **Session-state reliability** | OpenClaw, NanoClaw, CoPaw, ZeroClaw | Silent message loss, subagent completion drops, session lane starvation, stale background saves overwriting active state, deadlock after inactivity |
| **Multi-agent orchestration** | OpenClaw, NanoBot, CoPaw | Subagent transcript persistence, completion delivery guarantees, per-subagent model overrides, inter-agent collaboration UX |
| **Plugin/extension architecture** | Hermes Agent, NanoBot, OpenClaw, NanoClaw | Plugin lifecycle management, manifest v2, auto-discovery, event bus contracts, capability declarations, trust-tagging for memory |
| **OAuth / MCP authentication stability** | OpenClaw, Hermes Agent, ZeroClaw, IronClaw | OAuth refresh race conditions, MCP server deadlocks after keepalive reconnect, parked connections after teardown, token timeout mismatches |
| **Channel integration reliability** | IronClaw, OpenClaw, NanoBot, PicoClaw | Telegram message ordering/delivery, Discord typing-indicator leaks, Signal DM routing, WeChat QR token persistence, gateway webhook activation |
| **Security hardening** | NanoBot, ZeroClaw, OpenClaw, CoPaw | Credential leakage to third-party readers (Jina), memory poisoning via untrusted sources, plugin sandboxing (silent cron injection), SSRF in file downloads |
| **Observability & telemetry** | Hermes Agent, ZeroClaw, NanoBot | Streaming LLM output hooks, approval decision export, Langfuse integration, live dev-agent trajectory tracking, transparent plugin behavior |
| **Cross-platform CI / testing** | ZeroClaw, IronClaw, NanoBot | Windows test failures (74 on ZeroClaw), CI timeout flakiness, UTC-window test failures, macOS blank-window packaging bugs |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | Hermes Agent | IronClaw | CoPaw | ZeroClaw | PicoClaw / NanoClaw | LobsterAI |
|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Multi-agent session reliability | Provider expansion + security | Plugin API maturity | Rapid RC release cadence | UI polish + tool accuracy | Security hardening + governance | Platform correctness / migration | Desktop UX refinement |
| **Target user** | Power users running complex agent workflows | Developers needing broad model coverage | Enterprise/extended-deployment users | Teams shipping to production | Casual to intermediate users | Security-conscious deployers | Niche platform adopters | Desktop-first consumers |
| **Release discipline** | None currently | Low (no recent releases) | Low (no recent releases) | High (2 RCs/day) | Medium (beta cadence) | Low (no releases) | Low (no releases) | Medium (daily/weekly) |
| **Architecture** | Gateway-centric, subagent orchestration | Modular provider abstractions, MCP-first | Plugin-native with manifest v2 | Configuration-driven, extensible | Desktop app with skill system | Policy-driven with attestation | Migration-phase (templates→plugins) | Skilled manager with sandboxing |
| **Key differentiator** | Deepest multi-agent problem space | Fastest provider integration (DeepSeek V4 Pro, QwenCloud) | Most mature plugin interface (9 sub-features shipped) | Fastest release cadence with bug-bash discipline | Best UI/UX polish cycle | Strongest security posture | Platform parity focus | Desktop-first with sandbox enforcement |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (High Velocity, Structured):**
- **IronClaw:** Two RCs in one day, active bug-bash with 20+ P1/P2 issues surfaced and triaged. Most mature release discipline in the ecosystem.
- **CoPaw:** Beta cadence with merged UI/tool fixes, strong community comment engagement, clear roadmap signals.
- **NanoBot:** High PR velocity (36 in 24h), focused security hardening, proactive provider expansion.

**Tier 2 — Sustained Activity (High Volume, Less Structured):**
- **OpenClaw:** Enormous issue/PR volume but no release cadence; heavy maintenance burden suggests a large but fragmented user base.
- **Hermes Agent:** Strong plugin-evolution phase with 9 sub-features shipped, but Windows gateway regressions and OAuth deadlocks indicate platform stability gaps.
- **ZeroClaw:** Active security and governance work, but Windows test failures (74) and missing maintainer decisions signal platform parity debt.

**Tier 3 — Moderate / Stalled:**
- **PicoClaw:** Three substantive community PRs pending review for 10–18 days; MCP hang bug unresolved. Healthy contributor base but maintainer bottleneck.
- **NanoClaw:** Active migration (templates→plugins) but introduced two critical regressions (#3234, #3233) blocking core workflows.
- **LobsterAI:** Stable incremental polish but four stale issues open since March 2026; sandbox enforcement backlash (#1179) indicates community friction.

**Tier 4 — Inactive:**
- NullClaw, Moltis, ZeptoClaw: Zero activity. Likely absorbed, abandoned, or dormant.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Session-state fragility is the #1 cross-cutting risk** | OpenClaw (403 open issues, subagent loss), CoPaw (deadlock after 30min inactivity), NanoClaw (stale background saves), ZeroClaw (cron delivery broken) | Any production deployment must prioritize state persistence, compaction safety, and lane-isolation guarantees before feature expansion |
| **Multi-agent orchestration reliability is unsolved** | OpenClaw's top-voted issues are all subagent-completion loss variants; CoPaw lacks per-subagent model overrides; NanoBot's subagent transcript persistence is still in PR review | Developers should expect silent failures in subagent pipelines; evaluate projects on retry/notification guarantees, not just orchestration APIs |
| **Plugin architectures are converging on manifest v2 + lifecycle hooks + event bus** | Hermes Agent shipped 9 sub-features in this cycle; NanoBot added hook auto-discovery; OpenClaw pursues memory-trust tagging; NanoClaw is migrating templates→plugins | Plugin ecosystem investment is safe; projects standardizing on lifecycle hooks and capability declarations will have the richest extensibility |
| **OAuth/MCP authentication is a universal failure point** | OpenClaw (Codex OAuth timeout), Hermes Agent (3 related deadlock issues), ZeroClaw (deferred-MCP policy centralization) | Authentication layer reliability should be a primary evaluation criterion; projects without OAuth stress-testing are likely to underperform in production |
| **Telegram channel integration is the canary for overall stability** | IronClaw: 11 of 20+ bugs target Telegram; OpenClaw: Telegram DM routing leaks; PicoClaw: Telegram topic support PR | If a project's Telegram integration is buggy, expect broader channel-level fragility; prioritize projects with Telegram bug-bashes completed |
| **Security hardening is accelerating but uneven** | NanoBot fixed Jina credential leakage + ExecTool path guards in one cycle; ZeroClaw merged 3 security PRs; CoPaw flagged plugin cron injection without approval | Security-responsive projects signal maturity; evaluate based on whether fixes are proactive (hardening) vs. reactive (user-reported) |
| **Windows support is a systematic weakness** | ZeroClaw: 74 Windows test failures; Hermes Agent: 2 P1 Windows gateway crashes; IronClaw: Windows filesystem publication fix; PicoClaw: no Windows mention | Cross-platform parity is a differentiator; projects testing only on Linux are at higher risk of production failures for Windows users |
| **Release cadence correlates with perceived trust** | IronClaw's 2 RCs/day vs. OpenClaw's no releases — communities with regular ship cycles report higher confidence despite bugs | Developers should prefer projects with observable release discipline, even if bug counts are higher; silent maintenance cycles erode trust faster |

---

*Report generated by Agnes (Sapiens AI) from community digest data dated 2026-08-13.*

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-13

## 1. Today's Overview

NanoBot is experiencing **high development velocity** with 8 issues and 36 PRs updated in the past 24 hours. The project shows strong momentum in security hardening, provider expansion (DeepSeek V4 Pro, QwenCloud), and WebUI/session architecture improvements. Four bugs and one refactor were closed, while four new feature/enhancement proposals remain open. No new releases were published in this window. The repository is in an active consolidation phase — core infrastructure is being refactored (MCP lifecycle, Responses capabilities, session persistence) alongside targeted bug fixes, suggesting a pre-release stabilization cycle.

## 2. Releases

No new releases published.

## 3. Project Progress

**Closed/Merged PRs:**

| PR | Title | Key Change |
|---|---|---|
| [#5230](https://github.com/HKUDS/nanobot/pull/5230) | `fix(gemini): preserve imported tool calls` | Gemini 3 replay signature fallback preserved |
| [#5329](https://github.com/HKUDS/nanobot/pull/5329) | `fix(exec): guard bare and named-user home paths` | Shell tilde expansion boundary bypasses closed |
| [#5258](https://github.com/HKUDS/nanobot/pull/5258) | `fix(web): keep credential URLs away from Jina reader` | Credential-bearing URLs now routed through local readability path |
| [#5320](https://github.com/HKUDS/nanobot/pull/5320) | `fix(docker): restore capabilities for privilege drop` | `cap_drop: ALL` retained; three required caps restored, `no-new-privileges` enabled |
| [#5362](https://github.com/HKUDS/nanobot/pull/5362) | `feat(providers): support DeepSeek V4 Pro Responses` | DeepSeek V4 Pro routed through native Responses API alongside V4 Flash |
| [#5218](https://github.com/HKUDS/nanobot/pull/5218) | `fix(tools): ExecTool path guard with redirection delimiters` | POSIX expression widened to catch adjacent path extraction edge cases |
| [#4878](https://github.com/HKUDS/nanobot/pull/4878) | `feat(hooks): auto-discovery for agent hooks` | pkgutil scanning + entry_points; hook registration without manual wiring |

**Notable Open PRs advancing today:**

- [#5291](https://github.com/HKUDS/nanobot/pull/5291) — Subagent transcript persistence (P2)
- [#5204](https://github.com/HKUDS/nanobot/pull/5204) — Declarative Responses capabilities for routing, compaction, fallback (P1)
- [#5292](https://github.com/HKUDS/nanobot/pull/5292) — Matrix room-level reply linkage fix
- [#5358](https://github.com/HKUDS/nanobot/pull/5358) — WebUI session collaboration via `@` mentions
- [#5279](https://github.com/HKUDS/nanobot/pull/5279) — Session history moved outside agent workspace (security isolation)
- [#4329](https://github.com/HKUDS/nanobot/pull/4329) — Native TypeScript terminal UI (long-open, ongoing)

## 4. Community Hot Topics

1. **[Issue #4010](https://github.com/HKUDS/nanobot/issues/4010) — Text-to-speech / voice output support** (3 👍, open since May)
   *Users want Nanobot to close the conversational loop on voice-enabled channels (currently voice-in is supported but output is text-only). High demand signal for a full voice pipeline.*

2. **[Issue #5327](https://github.com/HKUDS/nanobot/issues/5327) — Repeated messages during reasoning** (11 comments, closed)
   *A non-deterministic repetition bug during agent reasoning caused significant frustration; now resolved. Community attention high due to direct UX impact.*

3. **[PR #5291](https://github.com/HKUDS/nanobot/pull/5291) — Subagent conversation transcript persistence**
   *Subagent runs previously left no trace — tool calls, reasoning steps vanished after completion. Open with conflicts; high relevance for debugging and auditability.*

4. **[Issue #5350](https://github.com/HKUDS/nanobot/issues/5350) — QwenCloud provider path**
   *Proposal to add QwenCloud as a backward-compatible provider alongside existing DashScope. Reflects growing demand for international Qwen model access.*

5. **[Issue #4884](https://github.com/HKUDS/nanobot/issues/4884) — Security: WebFetch sends full URLs to Jina** (closed, fixed in #5258)
   *Privacy-sensitive issue that drew community scrutiny; now resolved. Reinforces trust in the project's security posture.*

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Status |
|---|---|---|---|
| **P0** | [#5348](https://github.com/HKUDS/nanobot/issues/5348) | Token-usage tests fail deterministically in a ~5 hr/day UTC window | 🟡 Open |
| **P1** | [#5327](https://github.com/HKUDS/nanobot/issues/5327) | Agent repeats the same message during reasoning | ✅ Closed |
| **P1** | [#5295](https://github.com/HKUDS/nanobot/issues/5295) | Docker compose entrypoint.sh permission denied | ✅ Closed |
| **P1** | [#5357](https://github.com/HKUDS/nanobot/pull/5357) | Session data overwritten by stale background saves (fix in #5271) | 🟡 Open PR |
| **P1** | [#5360](https://github.com/HKUDS/nanobot/pull/5360) | Non-ASCII MCP tool names collide after sanitization | 🟡 Open PR |
| **P2** | [#5361](https://github.com/HKUDS/nanobot/pull/5361) | WeChat QR login token lost when config.json has no channels block | 🟡 Open PR |

**Key observations:**
- The P0 test flakiness (#5348) is a CI reliability issue, not a runtime bug, but it blocks clean merge signals.
- Two security-adjacent bugs (workspace-boundary bypasses in ExecTool, #5218 and #5329) were both fixed this cycle — positive stability trend.
- Session lifecycle race conditions (#5271, #5357) remain open and are critical for reliability.

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Signal |
|---|---|---|
| Voice output / TTS | [#4010](https://github.com/HKUDS/nanobot/issues/4010) | Strong community interest; aligns with full voice-channel support |
| QwenCloud provider | [#5350](https://github.com/HKUDS/nanobot/issues/5350) | Direct user proposal; low-risk backward-compatible addition |
| DeepSeek V4 Pro | [#5362](https://github.com/HKUDS/nanobot/pull/5362) | **Merged** — next release will include this |
| Subagent transcript persistence | [#5291](https://github.com/HKUDS/nanobot/pull/5291) | High-value observability feature; likely next release |
| WebUI session mentions | [#5358](https://github.com/HKUDS/nanobot/pull/5358) | Collaboration feature; in progress |
| Native TypeScript TUI | [#4329](https://github.com/HKUDS/nanobot/pull/4329) | Long-standing; architectural shift, low near-term probability |
| Hook auto-discovery | [#4878](https://github.com/HKUDS/nanobot/pull/4878) | **Merged** — extensibility improvement for next release |

**Predicted for next release:** DeepSeek V4 Pro support, hook auto-discovery, subagent transcript persistence, and WeChat QR token fix are strong candidates.

## 7. User Feedback Summary

- **Pain point — Reasoning repetition:** Users reported random repeated messages during agent reasoning (#5327), which erodes trust in output quality. Now closed.
- **Pain point — Docker deployment friction:** Permission-denied errors on entrypoint.sh blocked self-hosted deployments (#5295). Closed, but indicates devex gaps in container documentation.
- **Pain point — Credential leakage to Jina:** Security-conscious users flagged that WebFetch sent full URLs (including auth) to a third-party reader (#4884). Fixed in #5258.
- **Pain point — WeChat token loss:** QR login tokens silently discarded when channels config is absent (#5361), causing re-authentication loops. Fix in progress.
- **Satisfaction — Security responsiveness:** Three security-adjacent fixes shipped in one cycle (Jina credentials, ExecTool path guards, Docker capabilities), indicating strong maintainer attention to trust boundaries.
- **Request — Voice feedback loop:** Users on voice-enabled channels (Discord, etc.) want Nanobot to respond with audio, not just text (#4010).

## 8. Backlog Watch

| Item | Age | Risk | Note |
|---|---|---|---|
| [#4010](https://github.com/HKUDS/nanobot/issues/4010) — TTS / voice output | ~3 months | Medium | 3 👍; clear community demand |
| [#4329](https://github.com/HKUDS/nanobot/pull/4329) — TypeScript TUI | ~2 months | Low | Architectural; slow-moving by nature |
| [#5291](https://github.com/HKUDS/nanobot/pull/5291) — Subagent transcript persistence | ~6 days | Medium | Conflicts need resolution; P2 |
| [#5358](https://github.com/HKUDS/nanobot/pull/5358) — WebUI session mentions | ~1 day | Low | New, needs triage |
| [#5348](https://github.com/HKUDS/nanobot/issues/5348) — UTC test flakiness | ~1 day | Medium | Blocks CI signal; P0 |
| [#5271](https://github.com/HKUDS/nanobot/pull/5271) — Stale background task overwrite | ~7 days | High | Session data integrity; P0 fix in progress |

**Maintainer attention needed:** The session lifecycle race (P0, #5271/#5357) and the WeChat token fix (#5361) are the most time-sensitive open items. The TTS feature (#4010) has accumulated enough community signal to warrant a roadmap commitment soon.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-13

## 1. Today's Overview

Hermes Agent shows **high sustained activity** with 50 issues and 50 PRs touched in the last 24 hours, though no new release was published. The dominant theme is the **July 2026 Plugin Interface Expansion** (tracking issue [#64182](https://github.com/NousResearch/hermes-agent/issues/64182)), with at least 9 related sub-features landed or closed today. Stability work remains active on Windows Desktop and OAuth/MCP connections. The project is in a strong plugin-evolution phase with a major "Webhook Revolution" repair campaign also underway.

## 2. Releases

No new releases were published today. The project continues on the current version track without a tag change.

## 3. Project Progress

**Merged / Closed today:**

| PR | Description |
|----|-------------|
| [#84974](https://github.com/NousResearch/hermes-agent/pull/84974) | Auto-format fix (lint) |
| [#83517](https://github.com/NousResearch/hermes-agent/pull/83517) | Made approval decisions observable — session identity + turn-scoped mark export |
| [#83514](https://github.com/NousResearch/hermes-agent/pull/83514) | Bound native scope lifecycle ops so a wedged observability pipeline cannot block the agent |
| [#65077](https://github.com/NousResearch/hermes-agent/pull/65077) | Observable gateway token stream — `on_stream_delta`/`segment`/`end` hooks for plugins |
| [#81039](https://github.com/NousResearch/hermes-agent/pull/81039) | Fixed Windows console window flash on every subprocess spawn |

**Plugin interface expansion — 9 sub-issues closed today:**
- [#64161](https://github.com/NousResearch/hermes-agent/issues/64161) — Streaming LLM output observer hooks (deltas, lifecycle)
- [#64181](https://github.com/NousResearch/hermes-agent/issues/64181) — Community plugin index + `hermes plugins search`
- [#64168](https://github.com/NousResearch/hermes-agent/issues/64168) — STT request hook (model prompt / vocabulary hints)
- [#64164](https://github.com/NousResearch/hermes-agent/issues/64164) — Inter-plugin event bus with declared emits/listens contracts
- [#64204](https://github.com/NousResearch/hermes-agent/issues/64204) — Pre-command middleware + MCP tool access from hooks
- [#65449](https://github.com/NousResearch/hermes-agent/issues/65449) — Additive-only redaction pattern registry
- [#64165](https://github.com/NousResearch/hermes-agent/issues/64165) — Manifest v2 (API version, dependencies, pip seam, config schema)
- [#64228](https://github.com/NousResearch/hermes-agent/issues/64228) — Capability declarations + install/update consent flow
- [#64229](https://github.com/NousResearch/hermes-agent/issues/64229) — Plugin lifecycle (registration handles, `on_unload`, supervised tasks)

## 4. Community Hot Topics

| Rank | Issue/PR | Comments | Focus |
|------|----------|----------|-------|
| 1 | [#64182](https://github.com/NousResearch/hermes-agent/issues/64182) — Plugin Interface Expansion tracking | 33 | Plugin API roadmap — highest community interest |
| 2 | [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale/degraded | 19 | Skills Hub reliability monitoring |
| 3 | [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) — Desktop restart kills gateway | 10 | Windows Desktop regression (P1) |
| 4 | [#39043](https://github.com/NousResearch/hermes-agent/issues/39043) — Signal native quote/reply/edit | 7 👍 | Signal adapter feature parity |
| 5 | [#45779](https://github.com/NousResearch/hermes-agent/issues/45779) — Multi-gateway per-tab connections | 6 👍 | Multi-backend Desktop workflow |

**Analysis:** The plugin interface remains the top community priority, with a clear demand for a mature, extensible plugin system (lifecycle, event bus, manifest v2, redaction registry). Signal adapter parity and multi-gateway support reflect power-user needs around communication coverage and deployment flexibility.

## 5. Bugs & Stability

**P1 — Critical:**
- [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) — *Desktop restart reaps live gateway, never relaunches* (WeChat/QQ silent). Regression in v0.20.0 on Windows. **No fix PR yet.**
- [#84185](https://github.com/NousResearch/hermes-agent/issues/84185) — *Windows gateway dies silently after `hermes update`* — no logs, no PID, offline until manual restart. **No fix PR yet.**
- [#53479](https://github.com/NousResearch/hermes-agent/issues/53479) — *CLI updater trusts rev-list counts for shallow/diverged installs* — produces bogus version bump counts.

**P2 — High:**
- [#38193](https://github.com/NousResearch/hermes-agent/issues/38193) — *OAuth-backed MCP server deadlocks after keepalive reconnect* — auth lock released cross-task.
- [#81051](https://github.com/NousResearch/hermes-agent/issues/81051) — *OAuth MCP connections stuck "parked" after teardown race in MCP SDK 1.26.0* — only full gateway restart recovers.
- [#49543](https://github.com/NousResearch/hermes-agent/issues/49543) — *OAuth MCP servers drop from toolset mid-session* (`RuntimeError` lock + 120s hangs).
- [#83427](https://github.com/NousResearch/hermes-agent/issues/83427) — *browser_exec crashes with `pydantic_core ModuleNotFoundError`* when PYTHONPATH points at Hermes venv.
- [#77505](https://github.com/NousResearch/hermes-agent/issues/77505) — *Severe scroll jitter in VirtualSessionList* (persists after prior memoization fix).
- [#84206](https://github.com/NousResearch/hermes-agent/issues/84206) — *`@file` text expansion assumes UTF-8*, fails on GBK/Shift_JIS/CP1252 files.
- [#83390](https://github.com/NousResearch/hermes-agent/issues/83390) — *Auxiliary title_generation fails on DeepSeek* (HTTP 400 `response_format` unavailable).

**Fixed today:**
- [#81039](https://github.com/NousResearch/hermes-agent/pull/81039) — Windows console flash on subprocess spawn (merged).
- [#84808](https://github.com/NousResearch/hermes-agent/pull/84808) — Stale todos outliving their policy during compression (open fix PR).
- [#84468](https://github.com/NousResearch/hermes-agent/pull/84468) — Non-idempotent `POST /v1/runs` (open fix PR).

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Signal |
|---------|-------|--------|
| Plugin interface expansion (full) | [#64182](https://github.com/NousResearch/hermes-agent/issues/64182) | **Active — core roadmap priority** |
| Signal native quote/reply/edit/remote-delete | [#39043](https://github.com/NousResearch/hermes-agent/issues/39043) | High community demand (3 👍) |
| Multi-gateway per-tab in Desktop | [#45779](https://github.com/NousResearch/hermes-agent/issues/45779) | Multi-backend power-user need (7 👍) |
| `display.autolink_urls` toggle | [#84921](https://github.com/NousResearch/hermes-agent/issues/84921) | Small UX polish, low risk |
| Webhook Revolution campaign | [#84834](https://github.com/NousResearch/hermes-agent/issues/84834) | Meta-issue — 5×2×3 repair of entire webhook surface |
| Discord API v10 feature parity | [#79564](https://github.com/NousResearch/hermes-agent/issues/79564) | Alignment with discord.py 2.7.1 |
| Steer queued prompts into live turn | [#84971](https://github.com/NousResearch/hermes-agent/pull/84971) | UX improvement for composer |
| Claude Agent SDK as first-class provider | [#65982](https://github.com/NousResearch/hermes-agent/pull/65982) | Subscription OAuth integration |

**Prediction:** The next release will likely include the plugin interface v2 (manifest, lifecycle, event bus), webhook route model, and several P1 Windows fixes if the two gateway-crash regressions are resolved.

## 7. User Feedback Summary

**Pain points:**
1. **Windows Desktop gateway instability** — two distinct P1 bugs (silent post-update crash [#84185](https://github.com/NousResearch/hermes-agent/issues/84185) and restart regressing [#83683](https://github.com/NousResearch/hermes-agent/issues/83683)) suggest a regression in the gateway lifecycle management on Windows.
2. **OAuth MCP reliability** — three related P2 issues (#38193, #81051, #49543) all describe authentication/lock races causing permanent MCP deadlocks, a significant blocker for enterprise and long-running deployments.
3. **Encoding fragility** — `@file` expansion crashing on non-UTF-8 text files [#84206](https://github.com/NousResearch/hermes-agent/issues/84206) is a real-world pain point for non-English users.
4. **Skills index freshness** — automated monitoring flagged stale index (29.8h vs 26h limit) [#66616](https://github.com/NousResearch/hermes-agent/issues/66616), eroding trust in the skills hub.

**Satisfaction signals:**
- Plugin interface expansion is well-received (9 sub-features shipped in one tracking issue cycle).
- Observability fixes (approval decisions now exported, bounded lifecycle ops) address enterprise telemetry needs.
- `hermes plugins update` now autostashes local changes [#84975](https://github.com/NousResearch/hermes-agent/pull/84975), reducing friction for custom plugin tweaks.

## 8. Backlog Watch

| Issue | Age | Concern |
|-------|-----|---------|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) — Desktop restart reaps gateway | 2 days | P1, no fix PR — Windows Desktop regression |
| [#84185](https://github.com/NousResearch/hermes-agent/issues/84185) — Gateway dies after `hermes update` | 1 day | P1, no fix PR — Windows update lifecycle |
| [#38193](https://github.com/NousResearch/hermes-agent/issues/38193) — OAuth MCP permanent deadlock | 2 months | P2, no fix PR — enterprise auth stability |
| [#81051](https://github.com/NousResearch/hermes-agent/issues/81051) — OAuth MCP "parked" after teardown race | 6 days | P2, no fix PR — needs MCP SDK 1.26.0 mitigation |
| [#53479](https://github.com/NousResearch/hermes-agent/issues/53479) — CLI updater shallow install bug | 2 months | P1, no fix PR — consistency with Desktop fix |
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) — Skills index stale | ~1 month | P3 but automated sweeper — indicates cron reliability issue |

**Most urgent:** The two Windows P1 bugs (#83683, #84185) require maintainer attention before the next release, as they break core Desktop functionality on the largest supported platform.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-13

## 1. Today's Overview

PicoClaw (v0.3.1) showed moderate activity today with 6 open items (3 issues, 3 PRs) updated in the last 24 hours. No new releases were published, and zero PRs were merged or issues closed during this window. The project remains in a maintenance-heavy phase, with community-reported bugs around UI responsiveness and agent loop stability competing with feature requests for dynamic model delegation and native search provider support. Overall health appears **stable but bottlenecked** — contributors are actively engaging, but no merged changes today suggest pending PRs may be awaiting review.

## 2. Releases

No new releases today. Current known version remains **0.3.1** (per issue #3281).

## 3. Project Progress

**Merged/Closed Today: None.**

Three open PRs represent meaningful progress:

- **PR #3316** (j-v) — Fixes routed-agent context management, restoring history, summarization, compression, and Seahorse bootstrap behavior that was being ignored for Discord-routed agents.
- **PR #3315** (genuss) — Enables Telegram topic support in private bot chats by checking `IsTopicMessage` in addition to `IsForum`, unblocking forum-mode bot deployments.
- **PR #3299** (kesku) — Adds native **Exa** as a `web_search` provider with `auto` mode, content highlights, date-range filtering, and config schema support.

## 4. Community Hot Topics

| Item | Type | Comments | 👍 | Link |
|------|------|----------|-----|------|
| #3281 — Web UI chat input lag with long history | Issue | 5 | 1 | [GitHub](https://github.com/sipeed/picoclaw/issues/3281) |
| #3269 — Agent loop hangs on MCP server failure | Issue | 4 | 1 | [GitHub](https://github.com/sipeed/picoclaw/issues/3269) |
| #3316 — Routed-agent context management fix | PR | — | 0 | [GitHub](https://github.com/sipeed/picoclaw/pull/3316) |
| #3315 — Telegram topic support in private chats | PR | — | 0 | [GitHub](https://github.com/sipeed/picoclaw/pull/3315) |
| #3330 — Dynamic model override in delegate/spawn/subagent | Issue | 0 | 0 | [GitHub](https://github.com/sipeed/picoclaw/issues/3330) |

**Underlying needs:** Users are pushing PicoClaw toward **longer, more complex agent sessions** — the Web UI lag bug (#3281) and the context-management PR (#3316) both reflect growing use cases involving extended conversation histories and multi-agent routing. The MCP hang issue (#3269) signals that production deployments depend heavily on MCP reliability, and a single failure point is a serious concern for users building agent infrastructures.

## 5. Bugs & Stability

| Severity | Issue | Summary | Link | Fix PR? |
|----------|-------|---------|------|---------|
| 🔴 High | #3269 | Agent loop hangs indefinitely when MCP server connection fails, causing the chat interface to stop responding entirely. | [GitHub](https://github.com/sipeed/picoclaw/issues/3269) | None yet |
| 🟡 Medium | #3281 | Web UI chat input becomes very laggy once conversation history grows moderately long. | [GitHub](https://github.com/sipeed/picoclaw/issues/3281) | None yet |

**Analysis:** Issue #3269 is the most critical open bug — a hang in the agent loop is a complete service outage for any MCP-dependent setup. Issue #3281 degrades UX significantly for power users but doesn't block functionality. Neither bug currently has an associated fix PR.

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Link | Likelihood of Inclusion |
|---------|----------|------|------------------------|
| Dynamic model override for `delegate`/`spawn`/`subagent` tools | #3330 | [GitHub](https://github.com/sipeed/picoclaw/issues/3330) | **Medium** — clear community need for per-call model flexibility in multi-agent workflows |
| Native Exa web search provider | PR #3299 | [GitHub](https://github.com/sipeed/picoclaw/pull/3299) | **High** — PR is complete and well-scoped; likely next merge |
| Telegram topic support in private bot chats | PR #3315 | [GitHub](https://github.com/sipeed/picoclaw/pull/3315) | **High** — small, targeted fix; likely next merge |
| Routed-agent context/summarization fix | PR #3316 | [GitHub](https://github.com/sipeed/picoclaw/pull/3316) | **High** — bugfix with PR ready; likely next merge |

**Roadmap takeaway:** The three open PRs collectively point to a near-term release focused on **multi-agent context reliability** and **channel/platform parity** (Discord routing, Telegram topics, Exa search). Issue #3330 is a feature gap that could appear in a future release if community demand sustains.

## 7. User Feedback Summary

- **Frustration with UI performance:** Long conversation histories cause input lag, making the Web UI feel sluggish (#3281). Users are clearly extending session lengths beyond what the current rendering pipeline handles well.
- **Pain around MCP reliability:** A single MCP connection failure brings the entire agent loop to a halt (#3269). Users expect graceful degradation, not total freeze.
- **Demand for per-tool model control:** Users want to override the model dynamically when spawning sub-agents rather than being locked to statically configured defaults (#3330). This reflects a maturing multi-agent use pattern.
- **Positive signals:** The volume and quality of community PRs (3 substantive PRs from different contributors) indicates a healthy contributor base engaged with real pain points.

## 8. Backlog Watch

| Item | Type | Created | Staleness | Link |
|------|------|---------|-----------|------|
| #3281 — Web UI input lag | Issue (BUG) | 2026-07-21 | 23 days open, stale flag | [GitHub](https://github.com/sipeed/picoclaw/issues/3281) |
| #3269 — Agent loop hang on MCP failure | Issue (BUG) | 2026-07-20 | 24 days open, stale flag | [GitHub](https://github.com/sipeed/picoclaw/issues/3269) |
| PR #3316 — Routed-agent context fix | PR (fix) | 2026-08-03 | 10 days open | [GitHub](https://github.com/sipeed/picoclaw/pull/3316) |
| PR #3315 — Telegram topic support | PR (feature) | 2026-08-03 | 10 days open | [GitHub](https://github.com/sipeed/picoclaw/pull/3315) |
| PR #3299 — Exa search provider | PR (feature) | 2026-07-26 | 18 days open | [GitHub](https://github.com/sipeed/picoclaw/pull/3299) |

**Recommendation:** The two stale bug issues (#3281, #3269) and the three PRs (all 10–18 days open) need maintainer attention. No merged changes today suggests a review bottleneck. Prioritizing the MCP hang fix (#3269) and the context-management PR (#3316) would address the most impactful user pain points.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-13

## 1. Today's Overview

NanoClaw is in a phase of active refactoring and stabilization, with 14 issues and PRs touched in the last 24 hours and no new releases published. The most significant ongoing work is the **Agent Templates → Agent Plugins 1.0.0** migration (#3220), which is stacked with a companion setup-wizard PR (#2909) and a registry-payload PR (#3231). Several platform-level fixes (WhatsApp, Signal, Telegram) are simultaneously advancing through review. Community health is moderate — engagement (comments/reactions) remains low across the board, suggesting a core contributor-driven cycle rather than broad community churn.

---

## 2. Releases

**None** this period. No new tagged versions or release notes published.

---

## 3. Project Progress

| PR | Status | Summary |
|----|--------|---------|
| [#3086](https://github.com/nanocoai/nanoclaw/pull/3086) | ✅ Closed | WhatsApp recipient validation — prevents silent sends to unregistered numbers |
| [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) | 🔄 Open | **Core:** Agent templates restructured as Agent Plugins 1.0.0 directories; includes symlink/caps/secret hardening |
| [#2909](https://github.com/nanocoai/nanoclaw/pull/2909) | 🔄 Open | Stacked on #3220 — template setup wizard flow and first-agent stamping |
| [#3231](https://github.com/nanocoai/nanoclaw/pull/3231) | 🔄 Open | Codex & OpenCode plugin MCP working-directory support |
| [#2689](https://github.com/nanocoai/nanoclaw/pull/2689) | 🔄 Open | Signal DM platform-ID consistency, `isMention` flag fix, approval delivery |
| [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) | 🔄 Open | Formatter now treats unknown slash commands as normal chat instead of dropping them |
| [#3193](https://github.com/nanocoai/nanoclaw/pull/3193) | 🔄 Open | Telegram Chat SDK update for rich messages |
| [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | 🔄 Open | Adds **Dial** channel to the channel picker and wizard |
| [#3230](https://github.com/nanocoai/nanoclaw/pull/3230) | 🔄 Open | Fixes removal docs pointing at retired `data/env` mirror |
| [#3189](https://github.com/nanocoai/nanoclaw/pull/3189) | 🔄 Open | `add-why` utility skill — explains what happened to a single message |

**Key takeaway:** The template→plugin migration is the dominant thread. The #3086 WhatsApp fix is the only item closed this cycle, resolving a real user pain point (silent failures on typo'd numbers).

---

## 4. Community Hot Topics

| Item | Activity | Notes |
|------|----------|-------|
| [#2504](https://github.com/nanocoai/nanoclaw/issues/2504) — `ncl status` health-check command | Open since 2026-05-15, 1 comment | User demand for a lightweight operational diagnostic. No reactions yet. |
| [#3234](https://github.com/nanocoai/nanoclaw/issues/3234) — Template-stamped agent groups get bare UUID | Open since 2026-08-12, 0 comments | Directly caused by the template→plugin migration; blocks `ensureAgent` spawn |
| [#3233](https://github.com/nanocoai/nanoclaw/issues/3233) — `ncl tasks` blind to pre-2.1.54 recurring tasks | Open since 2026-08-12, 0 comments | Migration gap: legacy task rows not re-homed, breaking agent-side task ops |
| [#3232](https://github.com/nanocoai/nanoclaw/issues/3232) — QwenCloud optional provider skill | Open since 2026-08-12, 0 comments | Modular provider proposal following existing skill patterns |

**Analysis:** Issues #3234 and #3233 appear to be **regressions introduced by the 2.1.54 migration and the template restructure**. They carry high practical impact (blocked agent spawns, invisible tasks) but zero community engagement so far — likely because they were just opened and are being tracked internally by the core team. The `ncl status` request (#2504) reflects a sustained operational need that has lingered for ~3 months without a maintainer response.

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix PR |
|----------|-----------|-------------|--------|
| 🔴 High | [#3234](https://github.com/nanocoai/nanoclaw/issues/3234) | Template-stamped agent groups receive a bare UUID without `ag-` prefix, causing `OneCLI ensureAgent` to reject the ID at spawn | No fix PR yet — likely needs a patch in #3220's landed diff |
| 🔴 High | [#3233](https://github.com/nanocoai/nanoclaw/issues/3233) | Post-migration to 2.1.54, `ncl tasks` inside agent containers returns "No tasks" for pre-existing recurring tasks; pause/cancel also fail | No fix PR yet — requires a migration step to rehome legacy task rows |
| 🟡 Medium | [#3230](https://github.com/nanocoai/nanoclaw/pull/3230) | Removal/docs point at retired `data/env` mirror, confusing users during cleanup | Open PR #3230 addresses this |
| 🟡 Medium | [#2689](https://github.com/nanocoai/nanoclaw/pull/2689) | Signal DMs silently dropped because `isMention` not set; group never auto-created | Fix PR #2689 open |
| 🟡 Medium | [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) | Unknown slash commands categorized as `passthrough`, silently dropped by SDK | Fix PR #2346 open |
| 🟢 Low | [#3086](https://github.com/nanocoai/nanoclaw/pull/3086) | **Fixed:** WhatsApp `sendMessage` accepted unregistered JIDs and returned fake success | ✅ Merged/Closed |

**Stability note:** Two high-severity bugs (3234, 3233) are likely direct consequences of the ongoing migration. They should be resolved as part of the #3220 landing or a follow-up patch. No crash reports were noted in this cycle.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Likelihood for Next Release |
|---------|----------|----------------------------|
| `ncl status` — lightweight health-check CLI | [#2504](https://github.com/nanocoai/nanoclaw/issues/2504) | **Medium** — operational need is clear, but lower priority than migration fixes |
| QwenCloud as optional provider skill | [#3232](https://github.com/nanocoai/nanoclaw/issues/3232) | **Medium** — follows existing modular provider pattern; depends on maintainer appetite |
| Dial channel integration | [#3050](https://github.com/nanocoai/nanoclaw/pull/3050) | **Medium-High** — PR is ready, stacked on plugin work; plausible post-migration |
| `add-why` utility skill | [#3189](https://github.com/nanocoai/nanoclaw/pull/3189) | **Low-Medium** — nice-to-have diagnostic skill, not blocking |
| Agent Templates → Plugins 1.0.0 | [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) | **Certain** — this is the current major release focus |
| Signal DM & Telegram rich-message fixes | [#2689](https://github.com/nanocoai/nanoclaw/pull/2689), [#3193](https://github.com/nanocoai/nanoclaw/pull/3193) | **High** — correctness fixes for core platforms, likely bundled |

**Roadmap signal:** The project is clearly prioritizing the **plugin architecture migration** as the next major release. Secondary focus is **platform correctness** (Signal, WhatsApp, Telegram). New provider/channel integrations (QwenCloud, Dial) are queued behind the migration.

---

## 7. User Feedback Summary

| Theme | Source | Sentiment |
|-------|--------|-----------|
| Silent WhatsApp sends to wrong numbers go undetected | [#3086](https://github.com/nanocoai/nanoclaw/pull/3086) (fixed) | ⚠️ → ✅ Resolved; users reported a frustrating UX where typos produced fake success |
| Agent group IDs missing `ag-` prefix break spawns | [#3234](https://github.com/nanocoai/nanoclaw/issues/3234) | 🔴 High frustration; blocking user workflows immediately post-migration |
| Recurring tasks invisible after upgrade to 2.1.54 | [#3233](https://github.com/nanocoai/nanoclaw/issues/3233) | 🔴 High frustration; data migration gap causing silent task loss from agent perspective |
| No quick health-check for running instances | [#2504](https://github.com/nanocoai/nanoclaw/issues/2504) | ⚠️ Operational pain; users work around with `ncl sessions list` plus manual inspection |
| Unknown slash commands silently dropped | [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) | 🟡 Annoyance; users' commands disappear without feedback |
| Signal DMs not creating messaging groups | [#2689](https://github.com/nanocoai/nanoclaw/pull/2689) | ⚠️ Breakage for Signal users; first message in a DM is lost |
| Docs point to retired paths during removal | [#3230](https://github.com/nanocoai/nanoclaw/pull/3230) | 🟢 Minor; documentation drift |

**Overall:** User sentiment is **mixed**. The migration to 2.1.54 / plugin architecture is delivering structural improvements but has introduced two high-severity regressions (#3234, #3233) that directly block core workflows. The WhatsApp fix (#3086) is well-received. Satisfaction is likely depressed this cycle due to migration pain.

---

## 8. Backlog Watch

| Item | Open Since | Priority | Risk |
|------|-----------|----------|------|
| [#3234](https://github.com/nanocoai/nanoclaw/issues/3234) — Bare UUID on template groups | 2026-08-12 | 🔴 Critical | Blocking agent spawns; needs patch in #3220 or immediate follow-up |
| [#3233](https://github.com/nanocoai/nanoclaw/issues/3233) — Legacy tasks invisible post-migration | 2026-08-12 | 🔴 Critical | Data migration gap; users upgrading to 2.1.54 lose task visibility |
| [#2504](https://github.com/nanocoai/nanoclaw/issues/2504) — `ncl status` command | 2026-05-15 (~3 months) | 🟡 Medium | Operational need; no maintainer response in 3 months |
| [#2689](https://github.com/nanocoai/nanoclaw/pull/2689) — Signal DM fixes | 2026-06-04 (~2 months) | 🟡 Medium | Open PR with no merge activity; Signal DMs broken for users |
| [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) — Unknown slash command handling | 2026-05-08 (~3 months) | 🟢 Low | Open PR stalled; minor UX issue |
| [#3189](https://github.com/nanocoai/nanoclaw/pull/3189) — `add-why` skill | 2026-08-05 | 🟢 Low | New PR, still in review |

**Maintainer attention needed:** The two critical bugs (#3234, #3233) must be resolved before or alongside the #3220 merge, or the next release will ship with broken agent-spawning and task-management for migrated users. The long-open PRs (#2689, #2346) may need a priority review to clear the backlog before the next release candidate.

---

*Generated by Sapiens AI. Data source: GitHub API snapshot for nanocoai/nanoclaw, 2026-08-13.*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-13

## 1. Today's Overview

IronClaw is in a high-velocity release cadence, shipping two release candidates (v1.2.0-rc.2 and v1.2.0-rc.3) on 2026-08-12 in a single day — a clear signal that the team is closing out the v1.2.0 release candidate cycle. With 41 issues updated and 50 PRs in the last 24 hours, project activity is exceptionally high. A significant volume of bug-bash P1/P2 issues (20+ today) surfaced across Telegram channel integrations and the multi-user access flow, indicating an active quality-gate phase before v1.2.0. Several core infrastructure fixes — notably the Docker runtime healthcheck `curl` dependency and Windows filesystem publication — were resolved in the rc.2/rc.3 releases, suggesting the team is actively plugging showstopper gaps.

---

## 2. Releases

### ironclaw-v1.2.0-rc.3 (2026-08-12)
- **Fixed:** The runtime container image now installs `curl`, enabling in-container HTTP healthchecks via `curl -fsS http://localhost:3000/`. Without this, orchestrators could never probe the worker, and containers would never be marked healthy. See fix PR [#7555](https://github.com/nearai/ironclaw/pull/7555).
- **Note:** This release was preceded by an initial `x86_64-unknown-linux-musl` installer download failure, mitigated by PR [#7560](https://github.com/nearai/ironclaw/pull/7560) (retry dist installer download, now closed).

### ironclaw-v1.2.0-rc.2 (2026-08-12)
- **Fixed:** Windows first-start filesystem publication now uses native atomic rename semantics instead of hard links, and tolerates unsupported directory syncs — critical for standalone secrets-key security.
- **Fixed:** Release smoke runs now preserve the Windows account identity required to secure the standalone secrets key.
- **Migration note:** No documented breaking changes in rc.2 or rc.3 release notes; both are pre-v1.2.0 release candidates.

---

## 3. Project Progress

**Merged / Closed today (key items):**

| PR | Description | Status |
|----|-------------|--------|
| [#7560](https://github.com/nearai/ironclaw/pull/7560) | `fix(release): retry the dist installer download` — resolved the rc.3 x86_64-musl failure | ✅ Closed |
| [#7555](https://github.com/nearai/ironclaw/pull/7555) | `fix(docker): install curl so orchestrator healthchecks can run` — forward-ported from release/1.1.0-rc.1 | ✅ Closed |
| [#7550](https://github.com/nearai/ironclaw/pull/7550) | `feat(extensions): per-field help text on admin configuration forms + Telegram manifest rewrite` | ✅ Closed |
| [#7427](https://github.com/nearai/ironclaw/pull/7427) | `release: prepare 1.1.1-rc.1` — backports IronHub/custom MCP, WebUI, retrieval, Slack, and Telegram fixes onto the 1.1 line | ✅ Closed |
| [#5503](https://github.com/nearai/ironclaw/pull/5503) | `feat: compact Google extension capabilities` — Gmail summaries, Calendar operations | ✅ Closed |
| [#6836](https://github.com/nearai/ironclaw/pull/6836) | `feat(webui): @ironclaw/ui and workspace refactor` — re-derived design system as workspace package | ✅ Closed |

**Active PRs advancing the roadmap:**
- [#7439](https://github.com/nearai/ironclaw/pull/7439) — **Per-user model preferences** (`/model`, `/model use`, `/model default` commands) with tenant-scoped persistence.
- [#7491](https://github.com/nearai/ironclaw/pull/7491) — **OMP core-tool contract** unifying coding tools to five bare names (`read`, `write`, `edit`, `glob`, `grep`) and removing legacy mixed-surface tooling.
- [#7548](https://github.com/nearai/ironclaw/pull/7548) — **Structured execution contracts** for scheduled automations (goal, success criteria, output instructions).
- [#7456](https://github.com/nearai/ironclaw/pull/7456) — **Durable storage profile-agnostic** refactor for Reborn, rooting every profile at `IRONCLAW_REBORN_HOME`.
- [#7464](https://github.com/nearai/ironclaw/pull/7464) — **Telegram linked-device auth** — MTProto session custody with device-link registration visible in Telegram Settings → Devices.
- [#7556](https://github.com/nearai/ironclaw/pull/7556) — **Railway sandbox workspace file bridge** (`builtin.sandbox_workspace_copy`).
- [#6994](https://github.com/nearai/ironclaw/pull/6994) — **OOBE automation-tasks prototype** (carousel, inline cards, agent-mode pill) gated behind `oobe_suggestions` flag.
- [#7039](https://github.com/nearai/ironclaw/pull/7039) + [#7043](https://github.com/nearai/ironclaw/pull/7043) — **Storybook + Design System governance** (Epic #7038, phases 1 & 2).
- [#7516](https://github.com/nearai/ironclaw/pull/7516) — **IronHub agent-link operator surface** in the WebUI Extensions page.
- [#7559](https://github.com/nearai/ironclaw/pull/7559) — **Docs consolidation:** `docs/reborn/` → `docs/internal/reborn/` (115 files, history preserved).

---

## 4. Community Hot Topics

| Issue / PR | Engagement | Summary |
|------------|-----------|---------|
| [#7360](https://github.com/nearai/ironclaw/issues/7360) — Expand stress coverage across built-in & durable write paths | 3 comments | Nightly API-capacity workload uses a mock model that never exercises tool-call writes; regressions in built-in capabilities can slip through. |
| [#7407](https://github.com/nearai/ironclaw/issues/7407) — Execute `BatchPolicy::Parallel` batches concurrently in `invoke_capability_batch` | 3 comments (✅ Closed) | Production capability port runs batches sequentially despite parallel policy computation; fix is closed, likely merged. |
| [#7484](https://github.com/nearai/ironclaw/issues/7484) — Context window silently evicts task messages; pin user messages, compact on eviction | 1 comment (✅ Closed) | 128-message hard cap in three places causes silent task eviction. |
| [#7485](https://github.com/nearai/ironclaw/issues/7485) — Token estimator double-counts ASCII, halving effective context window | 0 comments (✅ Closed) | Two inconsistent estimators; transcript estimator uses `max(chars/4, bytes/2)`, which for ASCII always yields 2 chars/token. |
| [#7520](https://github.com/nearai/ironclaw/issues/7520) — Epic: retire superseded WebUI frontend surfaces | 0 comments (🆕) | Removing frontend code for retired v1/engine-v2 surfaces; excludes unfinished Jobs surface. |
| [#7044](https://github.com/nearai/ironclaw/issues/7044) — Onboarding to channel-first approach (v1.4.0 epic) | 0 comments | Blank-slate onboarding friction; focuses on General Assistant use case. |
| [#7038](https://github.com/nearai/ironclaw/issues/7038) — Storybook + AI-first Design System (v1.3.0 epic) | 0 comments | Full design-system proposal with 5-phase plan; Phases 1–2 PRs actively in review. |

**Analysis:** The most-discussed items cluster around **context-window management** (issues #7484, #7485 — now closed) and **stress-test coverage gaps** (#7360). The onboarding epic (#7044) and design-system epic (#7038) signal two parallel strategic tracks: improving first-time user experience and maturing the WebUI visual system for v1.3.0. The Telegram integration bugs (see §5) dominate the current issue volume but have low comment counts — they are being triaged rapidly rather than debated.

---

## 5. Bugs & Stability

### 🔴 P1 — Critical / Session-breaking

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| [#7538](https://github.com/nearai/ironclaw/issues/7538) | Telegram agent becomes **completely stuck** after receiving a GIF or sticker; no text messages respond thereafter. | — |
| [#7535](https://github.com/nearai/ironclaw/issues/7535) | Telegram webhook **not activated** after saving bot config in Admin UI; requires full redeploy. Forbidden [nearai-prod] errors visible. | — |
| [#7536](https://github.com/nearai/ironclaw/issues/7536) | Multi-user access flow broken — additional users receive **"Invalid secret"** error on UI open. | — |

### 🟠 P2 — High / Feature-breaking

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| [#7541](https://github.com/nearai/ironclaw/issues/7541) | Agent returns local workspace path as Markdown download link instead of sending file as Telegram attachment. | — |
| [#7540](https://github.com/nearai/ironclaw/issues/7540) | Long Telegram messages split by platform — agent processes only first part, rejects rest with "still working" error. | — |
| [#7543](https://github.com/nearai/ironclaw/issues/7543) | Telegram routine executes successfully but **message not delivered on first run**. | — |
| [#7545](https://github.com/nearai/ironclaw/issues/7545) | Agent incorrectly claims live crypto market data unavailable when querying multiple tokens. | — |
| [#7544](https://github.com/nearai/ironclaw/issues/7544) | Agent exposes **internal reasoning/planning output** directly in chat instead of user-facing response. | — |
| [#7542](https://github.com/nearai/ironclaw/issues/7542) | Agent fails to recognize conversation is already on Telegram; offers to deliver to Telegram mid-chat. | — |
| [#7451](https://github.com/nearai/ironclaw/issues/7451) | Telegram agent incorrectly requests credentials/API keys for operations that should not require them. | — |
| [#7554](https://github.com/nearai/ironclaw/issues/7554) | Custom MCP server add flow shows spurious **red validation error**, blocking server registration. | — |
| [#7508](https://github.com/nearai/ironclaw/issues/7508) | GitHub MCP extension startup shows confusing endpoint-verification prompt instead of connecting cleanly. | — |

### 🟡 P3 — Medium / UX

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| [#7546](https://github.com/nearai/ironclaw/issues/7546) | Telegram stickers are **silently ignored** — no reaction or acknowledgment from agent. | — |
| [#7539](https://github.com/nearai/ironclaw/issues/7539) | Telegram user message appears **after** agent working state in WebUI — out-of-order conversation flow. | — |
| [#7547](https://github.com/nearai/ironclaw/issues/7547) | Instance upgrade fails during **egress apply** on agent-stg (`wise-jay-voros`). | — |

**Pattern:** The Telegram integration is the dominant instability vector, with 11 of the 20+ new bugs targeting Telegram channel behavior (message ordering, delivery, file attachments, webhook activation, sticker handling, credential prompts, and session hang on non-text media). No fix PRs are yet linked to these issues. The P1 Telegram-stuck-after-GIF issue (#7538) is the most impactful regression and likely blocks v1.2.0 release if unfixed.

**Closed bug fixes today:**
- [#7484](https://github.com/nearai/ironclaw/issues/7484) — Context window eviction of task messages (closed)
- [#7485](https://github.com/nearai/ironclaw/issues/7485) — Token estimator double-counts ASCII (closed)
- [#5508](https://github.com/nearai/ironclaw/issues/5508) — Slack delivery target not found despite active connection (closed)
- [#6541](https://github.com/nearai/ironclaw/issues/6541) — WebUI constantly reconnecting (closed)
- [#7302](https://github.com/nearai/ironclaw/issues/7302) — Tool-call failure UI too aggressive (closed)

---

## 6. Feature Requests & Roadmap Signals

| Issue / PR | Target Version | Likelihood |
|------------|---------------|------------|
| [#7537](https://github.com/nearai/ironclaw/issues/7537) — Generic per-request thinking/effort control (DeepSeek V4 Flash trigger) | v1.2.0 / v1.3.0 | **High** — already assigned, core author |
| [#7439](https://github.com/nearai/ironclaw/pull/7439) — Per-user model preferences (`/model` commands) | v1.2.0 | **High** — large PR in active review |
| [#7548](https://github.com/nearai/ironclaw/pull/7548) — Structured execution contracts for automations | v1.3.0 | **Medium-High** — core tooling, in progress |
| [#7464](https://github.com/nearai/ironclaw/pull/7464) — Telegram linked-device auth & session custody | v1.2.0 | **High** — branched off docs PR, ready for review |
| [#7517](https://github.com/nearai/ironclaw/issues/7517) — Staking path for Google/GitHub sign-ins on Cloud.near.ai | v1.3.0 | **Medium** — user-reported, not yet assigned a PR |
| [#7516](https://github.com/nearai/ironclaw/pull/7516) — IronHub agent-link operator surface in WebUI | v1.2.0 | **Medium** — small feature, in review |
| [#7044](https://github.com/nearai/ironclaw/issues/7044) — Onboarding to channel-first approach (OOBE) | v1.4.0 | **Planned** — backend wiring (#6993) and prototype (#6994) in progress |
| [#7520](https://github.com/nearai/ironclaw/issues/7520) — Retire superseded WebUI frontend surfaces | v1.3.0 | **High** — cleanup epic, already started |

**Prediction:** v1.2.0 will ship with per-user model preferences, Telegram linked-device auth, and the OMP core-tool contract unification. The thinking/effort control (#7537) may land in v1.2.0-rc.4 or v1.3.0 depending on provider-testing velocity. The Telegram bug-bash issues (11 open) will likely block or immediately follow the v1.2.0 release.

---

## 7. User Feedback Summary

**Pain points (directly reported via Slack / issue submissions):**

1. **"Can't add my custom MCP server"** — [#7554](https://github.com/nearai/ironclaw/issues/7554): The custom MCP add flow shows a red validation error and blocks registration entirely. Reported via Slack `#x-ai-product-feedback`.
2. **Telegram file attachments return local paths, not files** — [#7541](https://github.com/nearai/ironclaw/issues/7541): Users on Telegram receive a Markdown link to a local workspace path instead of an actual file attachment — a broken UX for mobile users.
3. **Telegram session hangs on GIF/sticker input** — [#7538](https://github.com/nearai/ironclaw/issues/7538): The most severe reported issue; a single non-text message freezes the entire agent session, requiring manual intervention.
4. **Multi-user sharing returns "Invalid secret"** — [#7536](https://github.com/nearai/ironclaw/issues/7536): Collaborative instance sharing is

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-13

---

## 1. Today's Overview

LobsterAI saw moderate community activity on 2026-08-13, with 6 issues updated and 8 PRs touched in the last 24 hours. Three PRs were merged/closed today, primarily addressing renderer polish, plugin stability, and shell icon handling — all incremental fixes rather than major feature launches. No new releases were published, and the open issue count remains elevated with 4 stale open issues and no maintainer response in months. Overall, project health is stable but community engagement on issues is lagging, suggesting a maintainer bandwidth constraint.

---

## 2. Releases

No new releases were published on this date. The most recent release activity was **PR #2480** (`Release/2026.8.12`) merged yesterday, indicating the last release shipped on 2026-08-12.

---

## 3. Project Progress

Three PRs were closed/merged today, representing continued refinement of the renderer layer and Windows plugin stability:

| PR | Status | Area | Summary |
|---|---|---|---|
| [#2482](https://github.com/netease-youdao/LobsterAI/issues/2482) | ✅ Merged | Renderer | Split skills manager into "Mine" and "Builtin" tabs |
| [#2481](https://github.com/netease-youdao/LobsterAI/issues/2481) | ✅ Merged | Renderer / Cowork | Moved task search to header actions; icon-only search; cross-platform layout alignment |
| [#2479](https://github.com/netease-youdao/LobsterAI/issues/2479) | ✅ Merged | Main | Fixed Windows plugin installs preserving junctions and avoiding `EPERM` symlink errors |
| [#2478](https://github.com/netease-youdao/LobsterAI/issues/2478) | ✅ Merged | Shell | Fixed unsupported large file icon size fallback on macOS/Windows |

**Key theme:** Today's merged work focuses on **desktop polish and Windows installation reliability** — no new features shipped, but user-facing UI friction points are being systematically addressed.

---

## 4. Community Hot Topics

| Issue/PR | Status | Comments | Summary |
|---|---|---|---|
| [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | 🔴 Open · Stale | 2 | Users reporting forced sandbox behavior in v3.31 with no UI toggle to disable it |
| [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) | 🔴 Open · Stale | 1 | User concerns about processes persisting after uninstall; trust/security implication |
| [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) | 🔴 Open · Stale | 1 | Feature request: multiple custom model providers |
| [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) | 🔴 Open · Stale | 1 | Gateway restart loop triggered by editing custom agent icons in v2026.3.31 |
| [#2483](https://github.com/netease-youdao/LobsterAI/pull/2483) | 🟡 Open | 0 | Fix: key skill entries by frontmatter name to resolve UI toggle ineffectiveness |
| [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | 🟡 Open | 0 | Fix: hide OpenClaw main agent sessions from user-facing session list |

**Underlying needs:** The most discussed topic is **sandbox enforcement in v3.31** (#1179), which reflects user resistance to opaque policy changes without migration paths. The **multiple model providers** request (#1174) signals growing enterprise/advanced-user adoption where switching or running parallel providers is a real workflow need.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|---|---|---|---|
| 🔴 High | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | v3.31 forces sandbox mode with no user-controllable toggle; rollback to 3.30 resolves it | No fix PR open |
| 🔴 High | [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) | Editing a custom agent's icon triggers gateway infinite restart loop | No fix PR open |
| 🟡 Medium | [#1236](https://github.com/netease-youdao/LobsterAI/issues/1236) | Plugin ID mismatch warning on every gateway restart (config entry key ≠ manifest ID) | ✅ Closed |
| 🟡 Medium | [#2071](https://github.com/netease-youdao/LobsterAI/issues/2071) | Scheduled task creation errors (screenshot provided) | ✅ Closed |
| 🟢 Low | [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) | Process persists after uninstall (uninstall hygiene issue) | No fix PR open |

**Notable:** The two open high-severity bugs (#1179, #1180) both stem from the **v3.31 / 2026.3.31 release** and remain without fix PRs — a potential stability risk for users on that version.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood | Rationale |
|---|---|---|---|
| Multiple custom model providers | [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) | 🟡 Medium | Explicit user request with clear scenarios; aligns with multi-provider trend in AI tooling |
| Sandbox toggle / configurability | [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) | 🟡 Medium | Not a feature per se but a UX gap — users expect control over security policies |
| Hide internal OpenClaw sessions from Cowork list | [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) | 🟢 High (PR already open) | Quality-of-life fix; reduces user confusion |
| Skills manager tab split (Mine vs Builtin) | [#2482](https://github.com/netease-youdao/LobsterAI/pull/2482) | ✅ Done | Merged 2026-08-12 |

The **skills management** and **session list hygiene** changes suggest the team is prioritizing UX clarity for power users. Multi-provider support is the most significant pending feature request and may appear in a future release if demand continues to grow.

---

## 7. User Feedback Summary

- **Sandbox enforcement (v3.31):** Users are frustrated that a mandatory security change removed user control without an opt-out. The phrase "找不到关的按钮" (can't find the toggle to turn it off) indicates poor discoverability. This is the most urgent feedback item.
- **Post-uninstall process persistence (#1173):** A user raised a security-trust concern (" Are you leaving a backdoor?"). Whether or not this is a true bug, the perception risk is real and should be addressed transparently.
- **Gateway restart loop (#1180):** Editing a custom agent's icon triggers a cascade failure, pointing to a possible filesystem watcher or config-reload bug.
- **Plugin ID warnings (#1236):** Long-standing configuration friction for users managing MCP bridge plugins; now resolved.
- **Overall sentiment:** Users are generally satisfied with incremental UI improvements but increasingly vocal about **transparency around mandatory changes** and **system-level hygiene** (uninstall, restart loops).

---

## 8. Backlog Watch

| Item | Open Since | Days Open | Priority |
|---|---|---|---|
| [#1179](https://github.com/netease-youdao/LobsterAI/issues/1179) — Sandbox toggle | 2026-03-31 | ~136 days | 🔴 Critical |
| [#1180](https://github.com/netease-youdao/LobsterAI/issues/1180) — Gateway restart loop | 2026-03-31 | ~136 days | 🔴 Critical |
| [#1173](https://github.com/netease-youdao/LobsterAI/issues/1173) — Post-uninstall process | 2026-03-31 | ~136 days | 🟡 Medium |
| [#1174](https://github.com/netease-youdao/LobsterAI/issues/1174) — Multi-model providers | 2026-03-31 | ~136 days | 🟡 Medium |
| [#2483](https://github.com/netease-youdao/LobsterAI/pull/2483) — Skill key by frontmatter name | 2026-08-13 | 0 days | 🟡 Needs review |
| [#1181](https://github.com/netease-youdao/LobsterAI/pull/1181) — Hide main agent sessions | 2026-04-01 | ~105 days | 🟡 Needs review |

**Recommendation:** The four issues open since March 2026 (#1173, #1179, #1180, #1174) are all stale and represent the highest-impact unresolved items. Maintainer attention on these would significantly improve community confidence. The two open PRs (#2483, #1181) are ready for review and should be merged promptly.

---

*Generated by Agnes · Data source: LobsterAI GitHub activity via LobsterAI*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026‑08‑13

## 1. Today’s Overview
CoPaw (QwenPaw) shows **high development activity** with 31 issue updates and 43 PR updates in the last 24 h. The project recently shipped **v2.1.0‑beta.4**, focusing on UI polish and tool‑description fixes. Community engagement is strong, with several high‑comment issues around memory sync, agent termination, and network resilience. Bug‑fix velocity remains solid, while security and configuration‑regression concerns require maintainer attention.

## 2. Releases
**v2.1.0‑beta.4** (latest)  
- `fix(files)`: repair previews and dark‑mode styling ([#6915](https://github.com/agentscope-ai/QwenPaw/pull/6915))  
- `fix(tools)`: correct `read_file` tool description ([#6898](https://github.com/agentscope-ai/QwenPaw/pull/6898))  
- Version bump to 2.1.0b4  
No breaking changes noted. Migration is straightforward; users on beta3 should test plugin/tool configurations after upgrade.

## 3. Project Progress
**Merged/Closed today:**  
- `docs(website)`: improve Files workspace blog readability ([#6950](https://github.com/agentscope-ai/QwenPaw/pull/6950))  
- `fix(memory)`: simplify long‑term memory guidance, close false “Dream syncs to MEMORY.md” claim ([#6942](https://github.com/agentscope-ai/QwenPaw/pull/6942) closes [#6853](https://github.com/agentscope-ai/QwenPaw/issues/6853))  
- `chore`: update release notes for v2.1.0 ([#6944](https://github.com/agentscope-ai/QwenPaw/pull/6944))  
- `fix(computer‑use)`: macOS element‑activation fixes ([#6913](https://github.com/agentscope-ai/QwenPaw/pull/6913))  
- `fix(agents)`: sanitize tool messages before model calls ([#6540](https://github.com/agentscope-ai/QwenPaw/pull/6540) closed)  

**Under review / in progress:**  
- `fix(#6541)`: scroll‑compression placeholder now uses `SystemMsg` ([#6947](https://github.com/agentscope-ai/QwenPaw/pull/6947))  
- `fix(console)`: preserve textarea target for IME events ([#6889](https://github.com/agentscope-ai/QwenPaw/pull/6889))  
- `feat(channels)`: add MiniMax TTS support ([#6954](https://github.com/agentscope-ai/QwenPaw/pull/6954))  
- `perf`: stabilize LLM prefix cache via sorted tool schemas ([#6953](https://github.com/agentscope-ai/QwenPaw/pull/6953))  

## 4. Community Hot Topics
- **#6853** – *Dream writes to digest/ not MEMORY.md* (5 comments) – Memory‑sync expectation vs. reality; resolved by simplifying prompts.  
- **#6921** – *Agent stops after planning without executing* (5 comments) – Multi‑step task interruption; highlights need for more deterministic agent loops.  
- **#6780** – *Deadlock after 30+ minutes of inactivity* (4 comments) – Process hangs; suggests background‑task cleanup or watchdog issues.  
- **#6847** – *Antivirus kills QwenPaw while WorkBuddy survives* (4 comments) – Security‑software false positives; may indicate heuristic triggers.  
- **#6916** – *Plugins can silently create cron jobs and inject messages* (1 comment, security) – Permission‑model gap; high severity.  

**Underlying needs:** Users demand reliable task continuation, robust idle‑state handling, and tighter plugin sandboxing.

## 5. Bugs & Stability
**High severity**  
- [#6932](https://github.com/agentscope-ai/QwenPaw/issues/6932) – Network‑timeout recovery fails; requires manual restart.  
- [#6955](https://github.com/agentscope-ai/QwenPaw/issues/6955) – Probabilistic startup crashes / unexpected exits.  
- [#6958](https://github.com/agentscope-ai/QwenPaw/issues/6958) – Duplicate tool‑result entries when MCP output exceeds truncation threshold.  

**Medium severity**  
- [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) – Agent halts after planning without execution cue.  
- [#6928](https://github.com/agentscope-ai/QwenPaw/issues/6928) – History not scrollable; text‑input overwrites following characters.  
- [#6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) – MCP tools receive numeric args for string‑typed parameters.  
- [#6826](https://github.com/agentscope-ai/QwenPaw/issues/6826) – Assistant completion time displays seconds instead of actual tool‑call duration.  

**Fix PRs in progress:**  
- [#6936](https://github.com/agentscope-ai/QwenPaw/pull/6936) – Coerce string‑typed tool args.  
- [#6947](https://github.com/agentscope-ai/QwenPaw/pull/6947) – Fix scroll‑compression placeholder error.  
- [#6889](https://github.com/agentscope-ai/QwenPaw/pull/6889) – Resolve IME/textarea issue.  

## 6. Feature Requests & Roadmap Signals
- **#6917** – Inbox for proactive agent message delivery (structured, unread‑count badge).  
- **#6923** – LongHorizon‑Harness integration for sustained multi‑round tasks without state drift.  
- **#6925** – Co‑locate inter‑agent collaboration in a single session window.  
- **#5869** – Expose system slash commands in autocomplete across all UIs.  
- **#5992** – Per‑session model overrides (opt‑in).  

**Likely candidates for next patch/beta:** Slash‑command autocomplete ([#5869](https://github.com/agentscope-ai/QwenPaw/pull/5869)), per‑session model overrides ([#5992](https://github.com/agentscope-ai/QwenPaw/pull/5992)), and inbox‑delivery enhancement ([#6917](https://github.com/agentscope-ai/QwenPaw/issues/6917)).

## 7. User Feedback Summary
**Pain points**  
- Agents frequently stop after planning, requiring explicit “continue” prompts.  
- Network timeouts after transient disruptions are not auto‑recovered.  
- UI glitches: non‑scrollable history, incorrect message timestamps, duplicate tool results.  
- Plugin/tool configurations are lost on version upgrades.  
- False‑positive antivirus detections cause process termination.  

**Positive signals**  
- Simplified memory guidance reduces confusion about Dream/MEMORY.md behavior.  
- Documentation improvements make the Files workspace and long‑term memory more accessible.  
- Performance fixes (prefix‑cache stability) address reproducibility concerns.  

## 8. Backlog Watch
- **#6780** – Deadlock after inactivity (4 comments, 6‑day open).  
- **#6847** – Antivirus interference (4 comments, 4‑day open).  
- **#6916** – Plugin cron‑job injection without approval (security, 1 comment).  
- **#6926** – Session‑ID mismatch causing orphaned history rows (closed, but symptom may persist).  
- **#6813** – `consume_model_response` KeyError on dict‑like responses (closed via revert [#6956](https://github.com/agentscope-ai/QwenPaw/pull/6956); root cause仍需验证).  

Maintainers should prioritize security review for [#6916](https://github.com/agentscope-ai/QwenPaw/issues/6916) and stability investigations for [#6780](https://github.com/agentscope-ai/QwenPaw/issues/6780) and [#6955](https://github.com/agentscope-ai/QwenPaw/issues/6955).

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-13

## 1. Today's Overview
ZeroClaw shows **high contributor activity** with 50 issues and 50 PRs updated in the last 24 hours. The project is in a **maintenance and hardening phase**, with several security fixes, Windows‑test coverage gaps, and architectural RFCs advancing simultaneously. No new releases were shipped today.

## 2. Releases
*No new releases today.*

## 3. Project Progress
**Merged / closed PRs today:**
- [#9956](https://github.com/zeroclaw-labs/zeroclaw/pull/9956) – *fix(wechat): persist sync cursor only after inbound batch is enqueued* – closes a race‑window in WeChat channel listener crashes.
- [#9684](https://github.com/zeroclaw-labs/zeroclaw/issues/9684) – *SOP pane live‑run‑status icons* – task completed (parent #9682).
- [#9796](https://github.com/zeroclaw-labs/zeroclaw/issues/9796) – *cron parent help prints invalid examples* – fixed alongside #9704.
- [#9695](https://github.com/zeroclaw-labs/zeroclaw/pull/9695) – *strip terminal markers from streaming responses* – prevents marker leakage into agent outputs.
- [#8741](https://github.com/zeroclaw-labs/zeroclaw/pull/8741) & [#9362](https://github.com/zeroclaw-labs/zeroclaw/pull/9362) – *browser screenshot path validation* – closed duplicate/security‑hardening PRs.
- [#8496](https://github.com/zeroclaw-labs/zeroclaw/pull/8496) – *centralize deferred‑MCP access policy* – addresses #8054 Surface 1(b).

**Key enhancements in progress:**
- [#9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109) – Native Hailo‑Ollama provider.
- [#9196](https://github.com/zeroclaw-labs/zeroclaw/pull/9196) – MCP resource‑blob materialization with budget preflight.
- [#9556](https://github.com/zeroclaw-labs/zeroclaw/pull/9556) – Langfuse observability backend.
- [#9694](https://github.com/zeroclaw-labs/zeroclaw/pull/9694) – SOP pane read‑only status view.

## 4. Community Hot Topics
**Most commented issues (last 24h activity):**
1. [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) – **74 Windows test failures** (14 comments). Highlights a critical gap: CI runs tests only on Linux, allowing platform‑specific regressions to slip through.
2. [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) – **Maintainer decision queue for RFCs/design issues** (13 comments). Community seeks clearer triage and faster architectural decisions.
3. [#8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832) – **Plugin‑owned Kanban board for agent work** (9 comments). RFC for structured, plugin‑managed workflow coordination.
4. [#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) – **Consolidate release attestation mechanisms** (9 comments). Addresses redundant signing overhead (53 assets → ~20).

*Underlying needs:* Platform parity (Windows/macOS), transparent governance, and streamlined release security.

## 5. Bugs & Stability
**Open bugs ranked by severity (P1/P2):**
- **#7462** – 74 test failures on Windows (P1, high risk). Fix PR [#7461](https://github.com/zeroclaw-labs/zeroclaw/issues/7461) exists but not yet merged.
- **#9207** – `web_fetch` returns garbage for compressed responses (P1, workflow blocked). No fix PR yet.
- **#7527** – macOS desktop app can reopen blank / without a window (P1, high risk). Needs repro.
- **#9290** – Windows desktop installer fails at launch with missing `TaskDialogIndirect` (P1, workflow blocked).
- **#9198** – Discord typing indicator stuck after daemon reload (P2, high risk).
- **#9340** – CLI cron jobs cannot deliver output (P1, high risk). **Closed** but still marked in‑progress.

**Security‑relevant fixes merged today:**
- [#9753](https://github.com/zeroclaw-labs/zeroclaw/pull/9753) – Distinguishes absent vs. empty `allowed_tools` in risk profiles.
- [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713) – Adds `allowed_private_hosts` opt‑in to file‑download SSRF gate.
- [#9362](https://github.com/zeroclaw-labs/zeroclaw/pull/9362) – Validates browser screenshot destination against workspace policy.

## 6. Feature Requests & Roadmap Signals
**Notable open enhancement issues:**
- [#8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832) – Plugin‑owned Kanban board (agent workflow coordination).
- [#7929](https://github.com/zeroclaw-labs/zeroclaw/issues/7929) – Unify slash‑command registries across web UI, ZeroCode TUI, and channel runtime.
- [#5316](https://github.com/zeroclaw-labs/zeroclaw/issues/5316) – Complete SearXNG configuration and web‑search failure recovery.
- [#6998](https://github.com/zeroclaw-labs/zeroclaw/issues/6998) – Schema‑validated memory consolidation with bounded fallback.
- [#5907](https://github.com/zeroclaw-labs/zeroclaw/issues/5907) – Opt‑in LSP support for ZeroCode coding workflows.
- [#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) – Consolidate release attestation (security pipeline simplification).
- [#9644](https://github.com/zeroclaw-labs/zeroclaw/issues/9644) – Retire Lucid memory connector at v0.9.0 (abandoned upstream).

**Likely next‑version inclusions:**
- Kanban board plugin (if RFC accepted).
- Unified slash‑command registry.
- SearXNG support + DDG CAPTCHA detection.
- Memory‑consolidation schema validation.

## 7. User Feedback Summary
**Pain points surfaced today:**
- **Windows test fragmentation** – 74 failures indicate that the Linux‑first CI leaves Windows users exposed to regressions.
- **Compressed‑response handling** – `web_fetch` returning binary garbage breaks agent workflows that rely on HTTP compression.
- **Desktop install/launch issues** – Both macOS (blank window) and Windows (missing `TaskDialogIndirect`) blockers suggest packaging/dependency problems.
- **Cron delivery broken** – CLI‑created cron jobs silently discard output (`delivery.mode = "none"`).
- **Discord typing‑indicator leak** – Stuck after daemon reload, causing UX confusion.

**Satisfaction signals:**
- Active security hardening (PRs #9753, #8713, #9362) and performance bounds (WASM timeout, credential rotation) address enterprise‑grade concerns.
- Observability expansions (Langfuse, Herdr) and provider flexibility (Hailo‑Ollama) show responsiveness to power‑user needs.

## 8. Backlog Watch
**Long‑unanswered or blocked issues requiring maintainer attention:**
- [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) – Maintainer decision tracker (13 comments, updated 2026‑08‑12).
- [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) – Windows test failures (14 comments, no merge).
- [#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) – Release attestation consolidation (9 comments).
- [#6653](https://github.com/zeroclaw-labs/zeroclaw/issues/6653) – Host‑architecture policy for emulated installs (7 comments, needs‑author‑action).
- [#7929](https://github.com/zeroclaw-labs/zeroclaw/issues/7929) – Unify slash‑command registries (7 comments, needs‑author‑action).
- [#6998](https://github.com/zeroclaw-labs/zeroclaw/issues/6998) – Schema‑validated memory consolidation (6 comments, needs‑maintainer‑review).
- [#5907](https://github.com/zeroclaw-labs/zeroclaw/issues/5907) – Opt‑in LSP support (6 comments, needs‑author‑action).
- [#8367](https://github.com/zeroclaw-labs/zeroclaw/issues/8367) – Derived capability readiness (4 comments, **blocked**).
- [#9323](https://github.com/zeroclaw-labs/zeroclaw/issues/9323) – Execution‑tree iteration budget ownership (4 comments, needs‑author‑action).
- [#9644](https://github.com/zeroclaw-labs/zeroclaw/issues/9644) – Retire Lucid memory connector (4 comments, needs‑author‑action).
- [#9511](https://github.com/zeroclaw-labs/zeroclaw/issues/9511) – Diff‑aware Semgrep findings as PR comments (2 comments, **blocked**).
- [#9507](https://github.com/zeroclaw-labs/zeroclaw/issues/9507) – Enforce crate dependency direction (1 comment).

---
*Generated from ZeroClaw GitHub data for 2026‑08‑13. All links point to the zeroclaw‑labs/zeroclaw repository.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*