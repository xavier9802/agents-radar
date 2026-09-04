# OpenClaw Ecosystem Digest 2026-09-04

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-09-04 04:02 UTC

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



# OpenClaw Project Digest — 2026-09-04

## 1. Today's Overview

OpenClaw is operating at **very high activity** with 500 issues and 500 PRs touched in the last 24 hours, reflecting intense post-release triage around v2026.9.1. The project shipped one new release today, but it already has a P0 regression on Windows (gateway fails to start). SQLite stability and memory-core integrity remain the dominant engineering concern, with multiple P0/corruption issues unresolved. Closed issues today total ~161, indicating a strong merge/closure cadence, though several critical bugs are still open.

---

## 2. Releases

### v2026.9.1 — Released Today
**Highlights:**
- **Mermaid diagrams** now render in the Control UI and native macOS/iOS/Android apps, with enlarge previews and a retry fallback on mobile.
- Continued work on the "from install to chat" onboarding flow (details truncated in release notes).

**Known regressions reported today:**
- **#137813** [P0] Windows gateway never starts after update — the new `--task-supervisor` flag exits 0 silently and never spawns the child process. [Link](https://github.com/openclaw/openclaw/issues/137813)
- **#136203** [P0] Windows de-DE upgrade leaves Doctor maintenance blocked and legacy workspace state behind. [Link](https://github.com/openclaw/openclaw/issues/136203)

**Migration note:** Operators on Windows should hold on upgrading until #137813 is resolved. The `--task-supervisor` flag appears to be the culprit.

---

## 3. Project Progress

**~85 PRs merged/closed today.** Key advances and fixes based on closed issues and top PRs:

| Area | Progress |
|---|---|
| **Slack** | #137863 routes native session controls to owning runs; fixes Stop/title-change event handling |
| **Skills/Watchers** | #137616 retires file polling when watchers close, preventing infinite read loops |
| **Docs i18n** | #137882 keeps translation model selection private; adds fallback when model becomes unavailable |
| **Compaction** | #136533 fixes heartbeat sessions ignoring active transcript byte cap |
| **Agent harness** | #137777 keeps healthy models working when a harness plugin fails to load |
| **UI** | #137401 keeps Archive available during active sessions; #137439 exposes config mode & accordion state; #137753 keeps Inbox current during automation bursts |
| **Memory** | #137876 exposes storage usage and guides safe disk recovery |
| **Cron** | #112375 (open) proposes shell precheck gate to skip LLM calls when no work |
| **Codex** | #137030 bounds live streams and drains Codex startup to prevent queue fill |
| **iMessage** | #137834 fixes echo cache for paired mirror rows |
| **Workboard** | #137809 adds guarded autopilot for card dispatch |
| **Performance** | Multiple small perf PRs (#137862, #137698, #137676, #137670, #137645, #136073) reduce allocations in SQLite reads, backup, diagnostics, and redaction |

---

## 4. Community Hot Topics

**Most-discussed open issues (by comment count):**

1. **#114612** — SQLite `memory_index_chunks` + `memory_embedding_cache` grow without bound, will fill disk. 11 comments. [🔗](https://github.com/openclaw/openclaw/issues/114612)
2. **#97616** — Unreaped hook/tool child processes accumulate as zombies, degrading runtime. 10 comments. [🔗](https://github.com/openclaw/openclaw/issues/97616)
3. **#96007** — Discord multi-part replies truncate after inline errors; only error line renders. 9 comments. [🔗](https://github.com/openclaw/openclaw/issues/96007)
4. **#110190** — Runtime context carrier positioned after user message causes model confusion and token waste. 9 comments. [🔗](https://github.com/openclaw/openclaw/issues/110190)
5. **#39406** — No config option to suppress transient tool error warnings visible to users. 9 comments. [🔗](https://github.com/openclaw/openclaw/issues/39406)

**Underlying needs:** Operators are hitting production-scale reliability issues — disk exhaustion from memory tables, zombie process accumulation, and channel-specific message loss. These are not edge cases; they affect multi-agent deployments with heavy tool use.

---

## 5. Bugs & Stability

### P0 (Release Blockers)
| Issue | Summary | Fix PR? |
|---|---|---|
| [#137813](https://github.com/openclaw/openclaw/issues/137813) | Windows gateway never starts after v2026.9.1 — `--task-supervisor` flag exits silently | No |
| [#136203](https://github.com/openclaw/openclaw/issues/136203) | Windows de-DE upgrade leaves Doctor blocked, legacy state behind | No |
| [#126821](https://github.com/openclaw/openclaw/issues/126821) | SQLite corruption recurs on pristine rebuilt DBs within 15–24h (WSL2, "paralyzed gateway" mode) | No |
| [#123327](https://github.com/openclaw/openclaw/issues/123327) | WAL checkpoint copies index pages over SQLite page 1 on ext4 (Raspberry Pi 5) | No |

### P1 (High Severity)
| Issue | Summary | Fix PR? |
|---|---|---|
| [#135347](https://github.com/openclaw/openclaw/issues/135347) | Forced memory reindex inflates shared DB to 35 GB; deleting it destroys sessions | No |
| [#126906](https://github.com/openclaw/openclaw/issues/126906) | Denying write tool silently disables memory persistence; agent reports success | No |
| [#136183](https://github.com/openclaw/openclaw/issues/136183) | Command executor hangs on `ssh` spawn — SIGTERM during banner (regression in 2026.8.1) | No |
| [#118185](https://github.com/openclaw/openclaw/issues/118185) | Single claude-cli turn written to transcript twice by two writers | No |
| [#115642](https://github.com/openclaw/openclaw/issues/115642) | Billing cooldown outlives provider outage; needs probe-based recovery | No |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Zombie child process accumulation from hooks/tools | No |
| [#110190](https://github.com/openclaw/openclaw/issues/110190) | Runtime context carrier after user message causes reasoning token waste | No |

### P2 (Medium)
| Issue | Summary |
|---|---|
| [#137705](https://github.com/openclaw/openclaw/issues/137705) | Telegram streaming leaks raw `[label](file://…)` Markdown for disallowed schemes |
| [#127239](https://github.com/openclaw/openclaw/issues/127239) | Context window shows 200k hardcoded default instead of real 1M for deepseek-v4-flash |
| [#125640](https://github.com/openclaw/openclaw/issues/125640) | Memory index still fails on item-count batch limits for openai-compatible providers |
| [#119350](https://github.com/openclaw/openclaw/issues/119350) | Light dreaming re-stages already-seen transcript messages after hash-cache eviction |

**Stability assessment:** The project has **4 active P0 bugs**, three of which are SQLite-corruption related. This is a serious stability signal — shared-state database integrity is a recurring failure mode across platforms (WSL2, ext4, Windows). The v2026.9.1 Windows regression further erodes confidence in the release pipeline.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Likelihood for Next Release |
|---|---|---|
| [#72741](https://github.com/openclaw/openclaw/issues/72741) | Standard interface for external security/guardrail checks | Medium — broad community interest, architectural change |
| [#116473](https://github.com/openclaw/openclaw/issues/116473) | Inter-agent delegation via `@A ask @B` syntax with audit log | Low-Medium — security review needed |
| [#126781](https://github.com/openclaw/openclaw/issues/126781) | Durable Lobster workflows via `/loop` and Automations | Medium — fits existing TaskFlow architecture |
| [#127208](https://github.com/openclaw/openclaw/issues/127208) | One-off `/followup` command | High — small scope, clear UX value |
| [#132781](https://github.com/openclaw/openclaw/issues/132781) | Use latest commentary as progress draft label | Low — niche UX tweak |
| [#137872](https://github.com/openclaw/openclaw/issues/137872) | Policy-bound hooks enumerate authorized tool names | Medium — builds on existing `toolAuthority` capability |
| [#122654](https://github.com/openclaw/openclaw/issues/122654) | Manage shared MCP OAuth in Control UI | Medium — ties into existing OAuth coordinator |
| [#112375](https://github.com/openclaw/openclaw/issues/112375) | Shell precheck gate for cron to skip LLM when no work | High — cost-saving, small scope, already has PR |

**Prediction:** `/followup` command (#127208), cron shell precheck (#112375), and tool-name enumeration for hooks (#137872) are the most likely to land in the next release given their scope and clear operator demand.

---

## 7. User Feedback Summary

**Pain points expressed:**
- **Disk exhaustion from unbounded memory tables** (#114612, #135347) — operators in production see GB-scale SQLite databases with no eviction policy.
- **Silent data loss** (#126906) — denying a tool disables memory persistence without any warning to the operator or agent, creating a false sense of success.
- **SQLite corruption** (#126821, #123327) — repeated corruption events on fresh DBs, including a "paralyzed gateway" state that accepts no service but doesn't crash.
- **Windows upgrade fragility** (#136203, #137813) — post-upgrade state is broken; Doctor maintenance is blocked; gateway won't start.
- **Channel-specific message loss** (#96007, #137705) — Discord truncates after errors; Telegram leaks raw Markdown for non-allowed schemes.
- **Billing cooldown overreach** (#115642) — providers in cooldown for hours after an outage has resolved, causing unnecessary service disruption.
- **Zombie processes** (#97616, #86119) — unreaped child processes from hooks, subagents, and cron accumulate over time.

**Satisfaction signals:** The high merge rate (85 PRs/day) and rapid response to bugs (several closed within days of filing) suggest an active, responsive maintainer team. The Mermaid diagram feature in v2026.9.1 is a quality-of-life improvement users clearly want.

---

## 8. Backlog Watch

**Critical items needing maintainer attention:**

| Issue | Age | Severity | Blocker |
|---|---|---|---|
| [#126821](https://github.com/openclaw/openclaw/issues/126821) — SQLite corruption recurs on pristine DBs | ~15 days | P0 | Yes |
| [#123327](https://github.com/openclaw/openclaw/issues/123327) — WAL checkpoint overwrites SQLite page 1 | ~22 days | P0 | Yes |
| [#114612](https://github.com/openclaw/openclaw/issues/114612) — SQLite unbounded memory table growth | ~39 days | P2 | No (but production-impacting) |
| [#97616](https://github.com/openclaw/openclaw/issues

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report — AI Agent & Personal Assistant OSS Ecosystem
**Date:** 2026-09-04

---

## 1. Ecosystem Overview

The open-source personal AI agent landscape in September 2026 is defined by a maturing base layer (OpenClaw as the dominant runtime) surrounded by a diverse set of derivative and specialized projects. Development velocity is high across the board, but the dominant concern across nearly every project is **production reliability** — SQLite stability, multi-channel message integrity, session-state correctness, and security governance. The ecosystem is bifurcating into two trajectories: projects refining operator-facing UX and channel integrations (NanoBot, PicoClaw, LobsterAI) versus those investing in architectural hardening and policy enforcement (ZeroClaw, CoPaw, NanoClaw).

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Merged/Closed | Release | Health Score |
|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | ~161 closed, ~85 merged | v2026.9.1 ✦ today | 🟡 Active but strained |
| **ZeroClaw** | 36 active + 14 closed | 49 open + 1 merged | 1 merged | None | 🟢 Sustained velocity |
| **CoPaw** | 27 | 36 | 8 closed | None (v2.2.0 stable verified) | 🟢 Robust stabilization |
| **Hermes Agent** | 50 | 50 | 3 merged | None | 🟡 Active but strained |
| **IronClaw** | 11 | 18 | ~10 merged | None | 🟢 Strong |
| **NanoBot** | 4 | 25 | 14 merged | None | 🟢 Active & responsive |
| **LobsterAI** | 6 | 15 | 10 merged | None (2026.8.31) | 🟢 Strong |
| **NanoClaw** | 5 | 23 | 2 merged | None | 🟢 Strong velocity |
| **PicoClaw** | 6 | 8 | 1 merged | None (v0.3.1) | 🟢 Steady |
| **NullClaw** | 0 | 0 | 0 | None | ⚪ Inactive |
| **ZeptoClaw** | 0 | 0 | 0 | None | ⚪ Inactive |

*Health Score rationale: balances merge cadence, bug closure rate, and presence of unresolved P0/P1 issues.*

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale and centrality:** OpenClaw is the core reference runtime; multiple projects (LobsterAI, CoPaw) depend on it. Its 500-issue/500-PR daily touch volume dwarfs all others, reflecting its role as the ecosystem's foundational layer.
- **Breadth of channel coverage:** Native integrations across Slack, iMessage, Discord, Telegram, Matrix, and more — far exceeding any derivative project.
- **Release discipline:** Shipped v2026.9.1 today with Mermaid diagram support and onboarding improvements, maintaining a regular cadence despite the P0 bug burden.

**Technical approach differences:**
- OpenClaw treats SQLite as its central shared-state store — a decision that has proven both powerful and fragile (4 active P0 bugs, 3 SQLite-corruption-related). Competing projects like ZeroClaw are moving toward crate-extracted, typed subsystems (cron extraction to `zeroclaw-cron`), while NanoClaw is formalizing provider contracts to avoid OpenClaw's implicit-flag drift.
- OpenClaw's community is larger and more production-heavy, which explains the concentration on disk exhaustion, zombie processes, and billing cooldown bugs — problems that only surface at scale.

**Community size comparison:**
OpenClaw's issue volume (500+ touched) and the depth of its P0/P1 backlog (11 critical items) indicate a user base an order of magnitude larger than NanoBot (~30 touches) or PicoClaw (~14 touches). Hermes Agent sits in a mid-tier bracket (~100 touches). CoPaw and IronClaw show moderate but focused communities.

---

## 4. Shared Technical Focus Areas

| Theme | Projects Involved | Specific Needs |
|---|---|---|
| **SQLite / shared-state integrity** | OpenClaw, NanoClaw, LobsterAI | Unbounded memory table growth, WAL checkpoint corruption, pragma ordering, concurrent test fixture collisions |
| **Multi-channel message reliability** | OpenClaw, NanoBot, PicoClaw, CoPaw | Discord truncation, Telegram streaming leaks, Matrix delivery failure propagation, Feishu consumer deadlocks, QQ 401 auth failures |
| **Session-state correctness** | OpenClaw, Hermes Agent, CoPaw, ZeroClaw | Zombie child processes, `HERMES_HOME` race on session stores, channel-isolated sessions in CoPaw, interrupted-turn persistence in ZeroClaw |
| **Security & governance hardening** | ZeroClaw, CoPaw, NanoClaw, IronClaw | Sandbox breaches, instruction evasion, tool permission policies, admission-gate extensibility, provider contract enforcement |
| **Cron / scheduling reliability** | OpenClaw, Hermes Agent, NanoBot, CoPaw | systemd 249 compat, heartbeat fencing, double-scheduling in misfire windows, shell precheck gates to skip LLM when no work |
| **WebUI / frontend stability** | NanoBot, IronClaw, PicoClaw, LobsterAI | Stream state after gateway restart, TypeScript migration, input lag with long history, iOS PWA tap issues |
| **Provider contract & LLM caching** | NanoClaw, IronClaw, ZeroClaw | Prompt-cache-key support across OpenAI/Anthropic, per-model context_length, typed provider interfaces |
| **MCP ecosystem integration** | LobsterAI, OpenClaw, NanoClaw, IronClaw | MCP Apps UI rendering, delegation support, OAuth coordination, egress error visibility |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | Hermes Agent | ZeroClaw | CoPaw | LobsterAI | NanoClaw | PicoClaw | IronClaw |
|---|---|---|---|---|---|---|---|---|---|
| **Primary focus** | Runtime core + channels | WebUI + multi-channel | Desktop CLI + gateways | Security policy + RFCs | Governance + multi-tenant | Desktop client + Cowork | Provider contracts + agent-runner | Channel integrations (LINE, QQ, Slack) | Type-safe WebUI + LLM caching |
| **Target user** | Operators at scale | Multi-channel power users | Desktop-first users | Security-conscious builders | Teams / enterprises | Chinese-market users | Container/SELinux deployers | Edge/ARM + niche channels | Type-safety advocates |
| **Architecture** | Monolithic Rust + SQLite | Modular channel plugins | Composite desktop/CLI/gateway | RFC-driven, crate-extracted | Multi-tenant Hub architecture | Electron desktop + OpenClaw core | TypeScript monorepo + provider contracts | Go + SDK adapters | TypeScript/React WebUI + Rust backend |
| **Release style** | Versioned releases with regression tracking | Patch-focused, no tagged releases | Sprint-driven, post-release triage | Continuous master, no tags | Milestone-driven (v2.2.0) | Bi-weekly release cadence | Frequent PRs, no recent release | Slow cadence (v0.3.1 stable) | Pre-release iteration |
| **Key differentiator** | Ecosystem centrality | Locale + stream state rigor | Cron/gateway reliability depth | Policy-as-code + verifiable intent | Sandbox breach response + governance | Localized UX + IM/Cowork integration | Provider contract formalization | Channel-specific bug fixes | TypeScript migration + prompt caching |

---

## 6. Community Momentum & Maturity

**Tier 1 — High Velocity, Active Triage:**
- **OpenClaw:** 500 touches/day with 85+ merges. Despite P0 burden, the merge cadence is aggressive. Maturity signal: strong contributor base, but SQLite corruption is a recurring architectural risk.
- **ZeroClaw:** 50 touches/day with RFC-to-implementation momentum. Maturing through design-doc discipline; the 49 open PRs suggest a healthy review pipeline.

**Tier 2 — Strong & Focused:**
- **CoPaw:** 63 touches/day, 8 merges, post-v2.2.0 stabilization. Security issues (#7443, #7511) are being addressed rapidly. Maturity signal: governance layer is becoming a competitive differentiator.
- **IronClaw:** 29 touches/day, ~10 merges. TypeScript migration executed cleanly with no regressions — a maturity signal for frontend orchestration.
- **LobsterAI:** 21 touches/day, 10 merges. Desktop polish and IM/Cowork refinements indicate a product-market fit phase rather than early experimentation.

**Tier 3 — Responsive but Smaller:**
- **NanoBot:** 29 touches/day, 14 merges. High merge ratio (50%) shows lean maintainer bandwidth. WebUI focus suggests a mature but narrower scope.
- **NanoClaw:** 28 touches/day, 2 merges. Provider contract refactor is the defining work — a bet on architectural correctness over feature velocity.

**Tier 4 — Steady / Niche:**
- **Hermes Agent:** 100 touches/day but only 3 merges. Strained maintainer bandwidth relative to issue volume. Desktop and cron are focus areas.
- **PicoClaw:** 14 touches/day, 1 merge. Channel-specific bug fixes dominate; lower overall velocity but targeted impact.

**Inactive:** NullClaw, ZeptoClaw — no activity in 24h.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Security policy as first-class concern** | ZeroClaw's RFC-driven sandbox policy, CoPaw's sandbox breach response, NanoClaw's admission-gate hooks, OpenClaw's guardrail interface request | Operators will demand verifiable intent and policy enforcement; projects investing early will capture enterprise trust |
| **SQLite as both asset and liability** | OpenClaw's 3 P0 corruption bugs, NanoClaw's pragma ordering fix, CoPaw's concurrent test fixture collision | Shared-state databases at scale require bounded growth, eviction policies, and platform-specific WAL testing — not just correctness |
| **Provider contract formalization** | NanoClaw's 9-PR refactor (#3581–#3591), IronClaw's prompt-cache-key standardization, ZeroClaw's typed interfaces | Implicit flag-based providers create drift; typed contracts enable composability and reduce the "works on my model" problem |
| **Multi-channel message integrity** | Broken across OpenClaw (Discord truncation), NanoBot (Matrix delivery), PicoClaw (QQ 401, LINE webhook), CoPaw (Feishu deadlocks) | Channel-specific edge cases are the new production bug frontier; investment in channel abstraction layers yields outsized reliability returns |
| **WebUI state management post-restart** | NanoBot's streaming stall, IronClaw's TypeScript migration, PicoClaw's input lag, LobsterAI's install confirmation | Gateway restarts are unavoidable in production; UI state recovery is a differentiator users notice immediately |
| **Cron reliability as production requirement** | Broken in OpenClaw (precheck gate), Hermes Agent (systemd 249), CoPaw (double-scheduling), NanoBot (archive lifecycle) | Scheduled automation is a top user workflow; projects with robust cron will win operational deployments |
| **Rapid iteration with regression risk** | OpenClaw v2026.9.1 Windows regression, CoPaw v2.2.0 custom-provider breakage, NanoBot locale race, Hermes Agent Desktop Bot Mode debt | High merge velocity without regression buffers creates trust erosion; projects with better release gates (IronClaw's TypeScript ratchet) show the path forward |
| **MCP ecosystem integration depth** | LobsterAI restoring in-app browser, OpenClaw OAuth coordination, NanoClaw provider expansion, ZeroClaw egress grants | MCP is becoming the standard tool interface; projects that render MCP Apps UI and handle delegation well will lead the next wave |

---

**Bottom line for decision-makers:** The ecosystem is transitioning from experimental multi-channel bots to production-grade agent platforms. OpenClaw remains the dominant runtime but carries significant SQLite and Windows stability debt. ZeroClaw and CoPaw are betting on security policy and governance as differentiation. NanoClaw's provider contract formalization and IronClaw's type-safety migration represent the strongest architectural trends. For operators, the key risk across all projects is that high velocity is outpacing regression testing — particularly around shared-state persistence and cross-platform deployment.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-09-04

## 1. Today's Overview

NanoBot shows **active development** with 29 issues/PRs touched in the last 24 hours (4 issues, 25 PRs). The dominant theme is **WebUI bug fixes**, particularly around concurrent locale registration, session title generation, and stream state management after gateway restarts. The project maintains a high merge rate — 14 of 25 PRs were closed/merged today — indicating responsive maintenance. No new releases were published, suggesting today's activity is focused on stabilization rather than version launches.

## 2. Releases

No new releases today.

## 3. Project Progress

**Merged / Closed PRs Today:**

| PR | Author | Summary |
|----|--------|---------|
| [#5650](https://github.com/HKUDS/nanobot/pull/5650) | chengyongru | Fix: preserve Hero model preset during chat creation |
| [#5646](https://github.com/HKUDS/nanobot/pull/5646) | chengyongru | Fix: show language names only in native form in locale picker |
| [#5637](https://github.com/HKUDS/nanobot/pull/5637) | Shizoqua | Fix: propagate Matrix stream delivery failures to retry policy |
| [#5334](https://github.com/HKUDS/nanobot/pull/5334) | pengpengyi92 | Fix: preserve indentation across message splits |
| [#5385](https://github.com/HKUDS/nanobot/pull/5385) | dajiaohuang | Fix: complete Element SAS request flow for Matrix verification |
| [#5413](https://github.com/HKUDS/nanobot/pull/5413) | KDB-Wind | Fix: apply fallback policy to raised LLM provider errors |
| [#5472](https://github.com/HKUDS/nanobot/pull/5472) | Wsp030914 | Fix: honor wildcard (`*`) in Signal inbound allowlists |
| [#5514](https://github.com/HKUDS/nanobot/pull/5514) | Oxygen56 | Fix: clear stale WebUI stream state after Gateway reconnect |
| [#5515](https://github.com/HKUDS/nanobot/pull/5515) | pengpengyi92 | Fix: observe session reply timeout task failures |
| [#5629](https://github.com/HKUDS/nanobot/pull/5629) | loseintwilight | Fix: respect `max_length` for plain tool values in hints |
| [#5635](https://github.com/HKUDS/nanobot/pull/5635) | Shizoqua | Fix: preserve queued SDK events on stream close |
| [#5632](https://github.com/HKUDS/nanobot/pull/5632) | chengyongru | Fix: preserve Codex prompt cache affinity |

**Notable Open PRs Advancing:**

- [#5651](https://github.com/HKUDS/nanobot/pull/5651) — Fix for concurrent channel locale registration (regression fix)
- [#5648](https://github.com/HKUDS/nanobot/pull/5648) — Fix for WebUI session title projection under `unifiedSession` mode
- [#5649](https://github.com/HKUDS/nanobot/pull/5649) — **Feature:** visualize per-request context reuse in WebUI (token usage popover, stacked bar chart)
- [#5620](https://github.com/HKUDS/nanobot/pull/5620) — **Feature:** configurable cron delivery targets and batch archive lifecycle
- [#5504](https://github.com/HKUDS/nanobot/pull/5504) — Fix: surface model retry status in TUI/WebUI (NAN-34)
- [#5639](https://github.com/HKUDS/nanobot/pull/5639) — Fix: stabilize session labels, TUI streaming, and pairing prompts
- [#5641](https://github.com/HKUDS/nanobot/pull/5641) — Fix: iOS PWA tap and status-bar issues

## 4. Community Hot Topics

1. **[Issue #5644](https://github.com/HKUDS/nanobot/issues/5644)** — *Channel locale registry drops a locale when two locales load concurrently* (1 comment, created 2026-09-03)
   - Directly addressed by PR #5651. Indicates a race condition in the WebUI locale loading path during startup.

2. **[Issue #5512](https://github.com/HKUDS/nanobot/issues/5512)** — *WebUI stalls in spinning state after Gateway restart* (1 comment, created 2026-08-24)
   - Fixed by PR #5514 (merged). A long-standing issue (10 days open) where `isStreaming` remains true because the frontend never receives `goal_status: idle` post-reconnect.

3. **[PR #5649](https://github.com/HKUDS/nanobot/pull/5649)** — *Visualize per-request context reuse* (created 2026-09-03)
   - No comments yet, but the feature is significant: moves token usage from inline assistant messages to a popover with percentage bars per model request. Suggests user demand for transparency around context consumption.

4. **[PR #5620](https://github.com/HKUDS/nanobot/pull/5620)** — *Configurable cron delivery and batch archive* (3+ days open, no comments)
   - A substantial feature adding per-cron delivery targets and archive lifecycle. Long lead time without discussion may signal low community visibility or a niche need.

**Underlying Need Analysis:** The majority of today's activity clusters around **WebUI reliability** (locale races, stream state, session titles) and **channel robustness** (Matrix, Signal). Users are running Nanobot in production-like configurations with multiple channels and gateway restarts, exposing edge cases in state management.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| 🔴 **High** | [#5644](https://github.com/HKUDS/nanobot/issues/5644) | Concurrent locale loading drops a locale — breaks multi-language WebUI | [#5651](https://github.com/HKUDS/nanobot/pull/5651) (open) |
| 🔴 **High** | [#5512](https://github.com/HKUDS/nanobot/issues/5512) | WebUI stalls spinning after Gateway restart — `isStreaming` stuck true | [#5514](https://github.com/HKUDS/nanobot/pull/5514) ✅ merged |
| 🟡 **Medium** | [#5647](https://github.com/HKUDS/nanobot/issues/5647) | Session title not generated when frontend envelope lacks `webui` flag | [#5648](https://github.com/HKUDS/nanobot/pull/5648) (open) |
| 🟡 **Medium** | [#5645](https://github.com/HKUDS/nanobot/issues/5645) | Current Time runtime context absent by default in 0.3.0 (regression from 0.2.2) | No fix PR yet |
| 🟡 **Medium** | [#5641](https://github.com/HKUDS/nanobot/pull/5641) | iOS PWA tap swallowed on sidebar rows (status bar interference) | Self-contained in PR |
| 🟢 **Low** | [#5629](https://github.com/HKUDS/nanobot/pull/5629) | Tool hints ignore `max_length` for plain (non-path/non-command) values | ✅ merged |
| 🟢 **Low** | [#5635](https://github.com/HKUDS/nanobot/pull/5635) | SDK stream queue eviction drops unread events on close | ✅ merged |

**Regressions Noted:**
- **#5645** — Timezone context block no longer auto-injected in 0.3.0 despite documentation claiming it exists. This is a documented-behavior mismatch.
- **#5644** — Concurrency regression in locale registry, likely introduced by a recent refactor of `loadChannelLocale()`.

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Assessment |
|--------|--------|------------|
| Context reuse visualization | [PR #5649](https://github.com/HKUDS/nanobot/pull/5649) | Strong — user-facing observability feature, addresses growing complexity of multi-model context windows |
| Cron delivery targets & archive | [PR #5620](https://github.com/HKUDS/nanobot/pull/5620) | Moderate — niche but valuable for automation-heavy deployments |
| Model retry status in UI | [PR #5504](https://github.com/HKUDS/nanobot/pull/5504) | Moderate — improves operational visibility during provider failures |
| iOS PWA improvements | [PR #5641](https://github.com/HKUDS/nanobot/pull/5641) | Moderate — signals mobile/PWA as an active support surface |
| Native-language locale labels | [PR #5646](https://github.com/HKUDS/nanobot/pull/5646) | Low — polish, but reflects commitment to i18n quality |

**Prediction:** The next release (likely **0.3.1**) will include fixes for #5644, #5647, #5512, and the iOS PWA patch. PR #5649 (context visualization) and #5620 (cron archive) are feature-grade and could ship in **0.4.0** if review cycles stay short.

## 7. User Feedback Summary

**Pain Points:**
1. **Gateway restarts break the WebUI experience** — Users report the chat UI getting stuck in a perpetual loading state after restarts ([#5512](https://github.com/HKUDS/nanobot/issues/5512)). This is a trust-destroying bug for production users.
2. **Multi-language setups lose translations at startup** — The locale race condition ([#5644](https://github.com/HKUDS/nanobot/issues/5644)) means non-English users may see partial or missing UI strings, especially on concurrent channel loads.
3. **Documentation-implementation gap on runtime context** — The Current Time context block was automatic in 0.2.2 but silent in 0.3.0, and docs weren't updated ([#5645](https://github.com/HKUDS/nanobot/issues/5645)).
4. **iOS PWA is unusable for some interactions** — Sidebar taps are swallowed by iOS Safari's hover simulation on first touch ([PR #5641](https://github.com/HKUDS/nanobot/pull/5641)).

**Satisfaction Signals:**
- PR #5646 (native language names) received positive reception implicitly — the community values accessibility and localization quality.
- The high merge rate (14/25 PRs closed today) suggests maintainers are responsive, which boosts contributor confidence.

## 8. Backlog Watch

| Item | Age | Concern |
|------|-----|---------|
| [PR #5620](https://github.com/HKUDS/nanobot/pull/5620) — Cron delivery & archive | **3 days open**, 0 comments | Substantial feature with no reviewer engagement; may stall |
| [PR #5649](https://github.com/HKUDS/nanobot/pull/5649) — Context reuse visualization | **1 day open**, 0 comments | Feature PR with no feedback; visibility issue or quiet approval |
| [PR #5639](https://github.com/HKUDS/nanobot/pull/5639) — TUI/session stability | **1 day open**, 0 comments | Multi-component fix (session labels, streaming, pairing); needs careful review |
| [PR #5446](https://github.com/HKUDS/nanobot/pull/5446) — Codex OAuth token persistence | **15 days open**, marked **conflict** | Stale due to merge conflict; important for Codex provider users |
| [Issue #5645](https://github.com/HKUDS/nanobot/issues/5645) — Missing Current Time context | **1 day open**, no fix PR | Documentation regression; needs triage |

**Overall Project Health: 🟢 Active & Responsive.** The maintainer team is processing a high volume of bug fixes, particularly in WebUI and channel stability. The main risk is a cluster of unreviewed feature PRs that could indicate review bandwidth constraints. The 0.3.0 regression on runtime context and locale concurrency should be prioritized in the next patch release.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-09-04

## 1. Today's Overview

Hermes Agent is experiencing exceptionally high activity, with **50 issues and 50 PRs updated in the last 24 hours**, indicating an intense sprint phase likely tied to the post-v0.21.0 release cycle. The project has **0 new releases** today, but 3 PRs were merged/closed, and 1 issue was resolved (the `/model` custom provider `context_length` bug, #15779). Activity is heavily concentrated on Desktop stability, cron/gateway reliability, and session-state safety — suggesting the team is aggressively hunting regressions from recent releases. Overall project health is **active but strained**, with numerous P0/P1 bugs surfacing across Desktop, CLI, and gateway surfaces.

## 2. Releases

No new releases today.

## 3. Project Progress

**Merged/Closed PRs today:**

- **#77157** [CLOSED] — `fix(search)`: zero-match probes now fall back to `grep`; adds native Windows `rg` path handling. Fixes a long-standing Windows compatibility gap.
- **#102655** — `fix(cron)`: drops `OOMPolicy=kill` from systemd scope units, resolving the systemd 249 compat breakage that was failing all cron dispatches post-v0.21.0.
- **#102627** — `fix(cron)`: tri-state fire-claim heartbeat to correctly distinguish fence contention from true ownership loss.

**Notable PRs advanced (open, actively discussed):**

- **#102646** — Prevents sentinel-only stream text (e.g. `[response interrupted]`) from being persisted as a final answer, fixing transport corruption artifacts.
- **#102647** — Routes background Telegram completions to the owning profile's bot under `multiplex_profiles`, fixing cross-profile message leakage.
- **#102650** — Adds `hermes sessions reset-store`, an owner-only recovery command for corrupted SQLite session stores.
- **#99490** — Makes desktop secret storage secure by default (OS keychain-encrypted), with crash-consistent migration from legacy bare-string storage.
- **#102645** — Honors per-model `custom_providers[].models.<id>.context_length` in the compressor's lazy/deferred path, closing a gap exposed by #15779's fix.
- **#67055** — Fixes vision auxiliary resolution losing named provider identity on second-pass resolution, addressing #76602/#100858.
- **#100865** — Makes persistent Browser Use daemons visible to the orphan reaper by wiring `AGENT_BROWSER_SOCKET_DIR`.

## 4. Community Hot Topics

| # | Type | Title | Comments | Link |
|---|------|-------|----------|------|
| #96692 | Feature | Unified slash-command registry & execution contract | 11 | [Issue](https://github.com/NousResearch/hermes-agent/issues/96692) |
| #69825 | Bug | `serve` never registers shell hooks | 7 | [Issue](https://github.com/NousResearch/hermes-agent/issues/69825) |
| #94726 | Bug (Tracking) | Desktop Bot Mode — open bugs sweep (Aug 2026) | 6 | [Issue](https://github.com/NousResearch/hermes-agent/issues/94726) |
| #100858 | Bug | Auxiliary vision with `custom:<name>` sends `no-key-required` | 6 | [Issue](https://github.com/NousResearch/hermes-agent/issues/100858) |
| #97296 | Bug | Kanban dispatcher SIGSEGV on macOS 27 via `Popen(start_new_session=True)` | 5 | [Issue](https://github.com/NousResearch/hermes-agent/issues/97296) |
| #70422 | Bug | Accidental composer drag/pop-out on Desktop | 5 | [Issue](https://github.com/NousResearch/hermes-agent/issues/70422) |

**Analysis:** The #96692 slash-command registry spec (11 comments) signals a strong community desire for a unified command model across all Hermes surfaces (CLI, TUI, Desktop, gateway, plugins). This is an architectural consolidation effort that, if shipped, would reduce the kind of surface-level inconsistencies plaguing today's bug list. The shell-hook registration gap (#69825, #102504, #102592) is a recurring theme — plugin/hooks infrastructure appears fragmented across command entry points. The Desktop Bot Mode tracking issue (#94726) with ~80 open items from an Aug sweep indicates the bot feature ship created a significant debt pile.

## 5. Bugs & Stability

### P0 (Critical)

| # | Title | Status | Fix PR |
|---|-------|--------|--------|
| #102194 | CLI path never persists `api_content` sidecar → first API call of every new turn misses prompt cache | Open | — |
| #93817 | Reasoning Blocks OFF still dumps thinking + every tool call into transcript | Open | — |

> #93817 is tagged **P0 — "makes Hermes Desktop unusable"** by the author. Both issues lack open fix PRs.

### P1 (High)

| # | Title | Status | Fix PR |
|---|-------|--------|--------|
| #102486 | Cron worker dispatch fails closed on systemd 249 (`OOMPolicy=kill` rejected) | Open | **#102655** (open, targeted) |
| #102574 | Shared `PeriodicScheduler` — one blocked callback stalls all safety timers | Open | — |
| #102526 | Desktop session store binds to another profile's `state.db` via `HERMES_HOME` race | Open | — |

### P2 (Medium)

| # | Title | Status | Fix PR |
|---|-------|--------|--------|
| #69825 / #102504 | Shell hooks never register in `hermes serve` (desktop backend) | Open (duplicates) | — |
| #100858 / #76602 | Auxiliary vision with custom provider loses API key → 401 | Open (duplicates) | **#67055** (open, targeted) |
| #97296 | Kanban dispatcher `SIGSEGV` on macOS 27 threaded gateway fork | Open | — |
| #70422 / #101318 | Desktop composer accidental drag/undock (duplicates) | Open | — |
| #101091 | Desktop accepts mismatched provider/model pair, injects into wrong group | Open | — |
| #100870 | Remote code kernel fails on Docker backend (brace rewriter omits separator) | Open | — |
| #100381 | `codex_app_server_auto` compacts tiny threads, thrashes long sessions | Open | — |
| #100855 | Browser daemons invisible to orphan reaper (wedge/survival across restarts) | Open | **#100865** (open, targeted) |
| #98645 | `clarify` card renders blank, times out (regression) | Open | — |
| #102592 | Plugin hooks (`pre_llm_call`, etc.) never fire on `serve`/`dashboard` | Open | — |

### P3 (Low)

| # | Title | Status |
|---|-------|--------|
| #102642 / #102057 | Windows Studio: group chat `WinError 10060` & Agent Bridge `ETIMEDOUT` | Open |
| #77409 | Desktop UI tests: `React.act` undefined under `NODE_ENV=production` | Open |
| #77952 | Restore last selected session when switching profiles | Open |

**Stability Assessment:** The bug density is high, with multiple P0/P1 issues still unpatched. The cron subsystem (systemd 249, heartbeat fencing, CLI detach) is a clear weak point with 3+ interrelated issues. The Desktop session-state / profile isolation bugs (#102526, #101091, #98645) suggest a broader architectural concern around multi-profile correctness.

## 6. Feature Requests & Roadmap Signals

| # | Title | Priority | Likelihood (Next 1-2 Releases) |
|---|-------|----------|-------------------------------|
| #96692 | Unified slash-command registry & execution contract | P3 (spec) | **High** — design-phase; would resolve many surface-inconsistency bugs |
| #77952 | Restore last selected session per profile on switch | P3 | **Medium** — straightforward UX fix |
| #102597 | Per-profile marker on session rows in All-profiles recents | P3 | **Medium** — small UI enhancement |
| #91329 | Bot Mode: manage members from Group settings | P3 | **Low-Medium** — depends on Bot Mode prioritization |
| #102582 | Expose per-slot reasoning effort in `hermes moa configure` | P3 | **Medium** — config parity gap |
| #102643 | Slash command `description` i18n support | P3 | **Low** — nice-to-have for non-EN users |
| #102650 | `hermes sessions reset-store` recovery command | — (PR open) | **High** — already in progress; operational necessity |

**Roadmap Signal:** The unified slash-command registry (#96692) is the most significant architectural proposal. If accepted, it would likely lands in a future major version rather than the next patch release, but the spec discussion is active and has community buy-in (11 comments, cross-component scope).

## 7. User Feedback Summary

**Pain Points:**
- **Desktop UX friction:** Multiple reports of accidental composer undocking (#70422, #101318) — users describe this as happening "constantly in normal use."
- **Reasoning visibility:** #93817 makes Desktop "unusable" for users who want clean transcripts without tool-call and thinking dumps.
- **Multi-profile correctness:** Session store race (#102526) and mismatched provider/model injection (#101091) suggest multi-profile is immature.
- **Plugin/hooks invisibility:** Plugin-registered hooks silently failing on `serve`/`dashboard` (#102592, #69825) is a trust-breaking issue — users configure guards that never execute.
- **Windows stability:** Two distinct Windows issues (#102642, #102057) around Agent Bridge timeouts and group chat socket errors.
- **Prompt cache miss:** #102194 causes every new turn's first API call to miss the cache, directly impacting latency and cost.

**Satisfaction Indicators:**
- Strong engagement on the slash-command unification spec (#96692) shows users want a more coherent product experience.
- The `hermes sessions reset-store` feature request (#102650) being actively addressed is a positive signal for operational tooling.
- i18n demand for

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-09-04

## 1. Today's Overview

PicoClaw (v0.3.1) shows moderate but focused development activity today, with 6 issues and 8 pull requests updated in the last 24 hours. The most visible signal is a direct fix for a long-standing Web UI chat lag issue (PR #3347 responding to Issue #3281), alongside a bot-driven dependency update cycle from Dependabot. One PR was merged/closed today (#3329 for LINE webhook settings), and no new releases were published. Overall project health is steady: maintainers are actively triaging channel integration bugs while routine dependency hygiene continues.

## 2. Releases

No new releases published. The project remains on version **0.3.1** (nightly builds confirm this).

## 3. Project Progress

**Merged/Closed today:**

- **PR #3329** — `fix(line): warn on inert webhook_host / webhook_port instead of seeding them` ([link](https://github.com/sipeed/picoclaw/pull/3329)). Fixes #3328 by addressing a misconfiguration where LINE channel webhook settings were declared and defaulted but never actually consumed by the webhook handler mounted on the shared gateway HTTP server. This closes a silent no-op bug that could mislead users into thinking LINE webhooks were configured.

**Notable open PRs advancing functionality:**

- **PR #3347** — `fix laggy interface` ([link](https://github.com/sipeed/picoclaw/pull/3347)). Directly addresses the Web UI chat input lag with extended history (Issue #3281). Author reports testing on both desktop and mobile via Brave browser with no remaining lag.
- **PR #3340** — `fix(slack): set FileSize on media upload params` ([link](https://github.com/sipeed/picoclaw/pull/3340)). Resolves Issue #3338 by populating the `FileSize` field in `slack.UploadFileParameters`, which the `slack-go` SDK requires before any network call.

## 4. Community Hot Topics

| Topic | Activity | Link |
|-------|----------|------|
| Web UI chat input lag with long history | 9 comments, 2 👍 | [Issue #3281](https://github.com/sipeed/picoclaw/issues/3281) |
| QQ channel 401 Authorization errors | 3 comments (Issue) + new diagnostic issue | [Issue #3349](https://github.com/sipeed/picoclaw/issues/3349) · [Issue #3365](https://github.com/sipeed/picoclaw/issues/3365) |
| Slack media upload failure | 3 comments | [Issue #3338](https://github.com/sipeed/picoclaw/issues/3338) |
| LINE webhook settings silently ignored | Resolved via PR #3329 | [PR #3329](https://github.com/sipeed/picoclaw/pull/3329) |

**Analysis:** Channel integrations dominate community concern. QQ (Tencent) and Slack both report authentication/upload failures, suggesting these connectors need closer maintenance. The Web UI performance issue has the highest engagement (9 comments, 2 reactions), indicating it affects a broad user base. The LINE fix being merged is a positive signal that configuration drift bugs are being addressed.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **Medium** | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI chat input is very laggy when session history is long | [#3347](https://github.com/sipeed/picoclaw/pull/3347) (open) |
| **Medium** | [#3338](https://github.com/sipeed/picoclaw/issues/3338) | Slack media uploads fail with `file size cannot be 0` | [#3340](https://github.com/sipeed/picoclaw/pull/3340) (open) |
| **Medium** | [#3365](https://github.com/sipeed/picoclaw/issues/3365) | QQ channel 401 "Authorization parameter format error" — root cause identified in `botgo v0.2.1` + `resty >= v2.17` | None yet |
| **Low** | [#3346](https://github.com/sipeed/picoclaw/issues/3346) | Abnormal RKLLM replies on ARM dev boards (Qwen3.5-0.8B_w4) | None yet |
| **Low** | [#3339](https://github.com/sipeed/picoclaw/issues/3339) | Google Antigravity returns generic 429 despite valid OAuth (now closed) | — |

**Notable:** Issue #3365 provides a strong diagnostic for the QQ channel failure, pinpointing `botgo v0.2.1` and `resty v2.17.1` as likely culprits. No fix PR exists yet.

## 6. Feature Requests & Roadmap Signals

No explicit feature request issues were opened today. However, the following signals are worth watching:

- **Web UI performance** — The sustained attention on #3281 (2 👍, 9 comments) suggests users expect smooth interaction even with long contexts. If PR #3347 merges, it will set a new baseline for UI responsiveness.
- **QQ channel reliability** — Two issues (#3349, #3365) from the same author point to ongoing friction with the Tencent QQ channel on ARM devices. This may warrant a roadmap item for channel hardening.
- **Dependabot-driven updates** — Five dependency bump PRs landed today (AWS SDK Go v2, `golang.org/x/term`, `irc-go`, `protobuf`, `larksuite/oapi-sdk-go`), indicating the project is on a regular update cadence that could surface compatibility improvements or regressions in the next release.

## 7. User Feedback Summary

- **Web UI lag is a top pain point.** Users are experiencing significant input delay in sessions with moderate history length, affecting both desktop and mobile browsers. This is the most upvoted issue in the dataset.
- **QQ channel authentication is broken for some users.** The error `"请求头Authorization参数格式错误"` (Authorization header format error) on Orange Pi 3B suggests either a botgo REST client regression or an incompatibility with newer resty versions. Users are actively diagnosing the root cause.
- **Slack media uploads are non-functional out of the box.** The missing `FileSize` field is a clear bug that prevents any image/video sharing through Slack, a commonly used channel.
- **LINE webhook misconfiguration was silently failing.** Users who set `webhook_host`/`webhook_port` expected them to take effect; the fact that they were ignored without warning was flagged as misleading.
- **RKLLM on ARM dev boards produces abnormal responses.** A niche but important use case for edge AI deployments.

## 8. Backlog Watch

| Item | Days Open | Concern |
|------|-----------|---------|
| [Issue #3281](https://github.com/sipeed/picoclaw/issues/3281) — Web UI chat lag | ~45 days | High community impact; fix PR #3347 is open but not yet merged |
| [Issue #3338](https://github.com/sipeed/picoclaw/issues/3338) — Slack media upload | ~18 days | Fix PR #3340 is open; blocking a core channel feature |
| [Issue #3346](https://github.com/sipeed/picoclaw/issues/3346) — RKLLM abnormal replies | ~8 days | Edge/ARM deployment use case; no fix PR yet |
| [Issue #3365](https://github.com/sipeed/picoclaw/issues/3365) — QQ channel 401 root cause | 1 day (new) | Well-diagnosed but no fix PR; likely needs botgo upgrade or patch |

**Recommendation:** Prioritize merging PR #3347 and PR #3340, as both address high-visibility bugs with ready fixes. The QQ channel issue (#3365) may require a dependency bump or a patch to the botgo integration rather than a code fix in PicoClaw itself.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-09-04

## 1. Today's Overview

NanoClaw shows strong development velocity with **23 PRs and 5 issues** touched in the past 24 hours, indicating an active contributor base and frequent iteration cycles. No new releases were published today. The project is deep in a major refactoring wave around provider contracts and agent-runner stability, alongside steady bug fixes and channel improvements. Health indicators are positive: high PR throughput, active issue triage, and a clear architectural direction toward contract-based provider extensibility.

---

## 2. Releases

No new releases were published today.

---

## 3. Project Progress

**Merged / Closed Today (2 visible; 1 unlisted in top-20):**

| PR | Summary | Link |
|---|---|---|
| [#3461](https://github.com/nanocoai/nanoclaw/pull/3461) | Bumped all `@chat-adapter/*` packages from 4.29.0 → 4.38.1 and updated `chat` itself — 9 minor versions caught up. | [PR #3461](https://github.com/nanocoai/nanoclaw/pull/3461) |
| [#3126](https://github.com/nanocoai/nanoclaw/pull/3126) | Fixed agent-runner to never deliver silence or `<internal>` thinking blocks to users — closes a user-facing content-leak bug. | [PR #3126](https://github.com/nanocoai/nanoclaw/pull/3126) |

**Key Open Work Advanced Today:**

- **[PR #3713](https://github.com/nanocoai/nanoclaw/pull/3713)** — Added per-agent-group delivery-mode configuration (column + plumbing only; consumer not yet wired). Enables groups running constrained models to opt into outbound-tool delivery instead of `<message to>` envelopes.
- **[PR #3711](https://github.com/nanocoai/nanoclaw/pull/3711)** — Introduced deferred inbound-content resolution in the router, so expensive network fetches/downloads only happen when an agent will actually receive the message.
- **[PR #3712](https://github.com/nanocoai/nanoclaw/pull/3712)** — Fixed WhatsApp channel bugs: document captions are now read, and unnecessary media downloads are suppressed. Depends on #3711.
- **[PR #3708](https://github.com/nanocoai/nanoclaw/pull/3708)** — Fixed SQLite `busy_timeout` / `journal_mode` pragma ordering to prevent lock contention on outbound DB opens.
- **[PR #3707](https://github.com/nanocoai/nanoclaw/pull/3707)** — Added `registerAdmissionGate` seam into the agent-runner poll loop, enabling subclassed admission-gate logic.
- **[PR #3710](https://github.com/nanocoai/nanoclaw/pull/3710)** — Test-suite cleanup: removes ~355 temp directories left behind per `pnpm test` run, critical for CI and long-lived dev environments.
- **[PR #3440](https://github.com/nanocoai/nanoclaw/pull/3440)** — Docker-driver fixes for SELinux-blocked mounts, group-writable rw mounts, and stray NUL bytes (still open since Aug 22).

---

## 4. Community Hot Topics

**Most Discussed / High-Impact Items:**

- **[PR #3440](https://github.com/nanocoai/nanoclaw/pull/3440)** — Docker driver mount/SELinux fixes. A long-standing open PR (since Aug 22) addressing real deployment friction on SELinux-enforced systems. Reflects growing container-runtime usage in production.
- **[PRs #3581–#3591](https://github.com/nanocoai/nanoclaw/pull/3581–#3591)** — A coordinated refactoring cluster redefining provider contracts (runtime, host, setup, and canon rendering). All opened by `zvi-fried` between Aug 19–28. This is the project's most significant architectural initiative, signaling a shift toward typed, verifiable provider interfaces.
- **[Issue #3706](https://github.com/nanocoai/nanoclaw/issues/3706)** — CLI `add-mount --container` silently produces broken double-nested paths with absolute paths. A usability bug that contradicts its own `--help` docs; resonates with users who naturally type absolute paths.
- **[Issue #3705](https://github.com/nanocoai/nanoclaw/issues/3705)** — `ncl tasks update --recurrence` fails to recompute `process_after`, leaving tasks on stale schedules. A correctness bug with direct operational impact for cron-based automation.
- **[Issue #3704](https://github.com/nanocoai/nanoclaw/issues/3704)** — Request for a protected session-assembly hook on `SqliteAgentMailbox` to enable subclassing with custom tables/columns/triggers. Signals demand for extensibility among fork/maintainer users.

**Underlying Needs:** The project is being used in more diverse deployment contexts (SELinux, concurrent CI, WhatsApp, custom SQLite extensions), and the community is pushing for better contract enforcement, extensibility hooks, and CLI correctness.

---

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Link |
|---|---|---|---|
| **High** | #3705 | `--recurrence` update doesn't recompute next fire time — tasks stay on old schedule | [Issue #3705](https://github.com/nanocoai/nanoclaw/issues/3705) |
| **High** | #3706 | `add-mount --container <abs-path>` creates broken double-nested paths | [Issue #3706](https://github.com/nanocoai/nanoclaw/issues/3706) |
| **Medium** | #3709 | SQLite mailbox tests use fixed `/tmp` fixture root — concurrent vitest runs destroy each other's DBs | [Issue #3709](https://github.com/nanocoai/nanoclaw/issues/3709) |
| **Medium** | #3440 (PR open) | Docker driver: SELinux-blocked mounts, group-writable mounts, stray NUL bytes | [PR #3440](https://github.com/nanocoai/nanoclaw/pull/3440) |
| **Low** | #3426 ✅ | `send_card` docs promise callback buttons the bridge drops; agent blames platform | [Issue #3426](https://github.com/nanocoai/nanoclaw/issues/3426) |
| — | #3708 (PR open) | SQLite `busy_timeout`/`journal_mode` pragma ordering fix for outbound open | [PR #3708](https://github.com/nanocoai/nanoclaw/pull/3708) |
| — | #3126 ✅ | Agent-runner was delivering silence and `<internal>` thinking blocks to users | [PR #3126](https://github.com/nanocoai/nanoclaw/pull/3126) |

**Notes:** Two high-severity CLI/scheduling bugs were opened today with no fix PRs yet. The WhatsApp fix (#3712) addresses a related operational pain point. The `send_card` bug (#3426) was closed today, a positive signal.

---

## 6. Feature Requests & Roadmap Signals

| Item | Description | Link | Likelihood for Next Release |
|---|---|---|---|
| **Per-group delivery mode** | Allow agent groups to declare envelope-free delivery for constrained models | [PR #3713](https://github.com/nanocoai/nanoclaw/pull/3713) | **High** — plumbing already merged; consumer wiring expected soon |
| **Deferred inbound content resolution** | Router delays expensive fetches/downloads until an agent will receive the message | [PR #3711](https://github.com/nanocoai/nanoclaw/pull/3711) | **High** — core architectural improvement, WhatsApp fix depends on it |
| **Cursor Agent SDK provider** | New provider payload + `/add-cursor` install skill | [PR #3356](https://github.com/nanocoai/nanoclaw/pull/3356), [PR #3355](https://github.com/nanocoai/nanoclaw/pull/3355) | **Medium** — provider contract refactoring must land first |
| **Speed inference property** | Core-owned `--speed` tier per agent group alongside `model` and `effort` | [PR #3592](https://github.com/nanocoai/nanoclaw/pull/3592) | **Medium** — depends on provider contract consolidation |
| **Voice transcription V2** | Container-side, sovereign-by-default voice transcription | [PR #2003](https://github.com/nanocoai/nanoclaw/pull/2003) | **Low–Medium** — long-open since April 2026, resubmitted |
| **Admission-gate poll-loop seam** | `registerAdmissionGate` hook for subclassed admission logic | [PR #3707](https://github.com/nanocoai/nanoclaw/pull/3707) | **Medium** — extensibility feature, smaller scope |

**Roadmap Signal:** The dominant theme is **provider contract formalization** — a multi-PR refactoring (#3581–#3591) that turns provider behavior from implicit flags into typed, verifiable contracts. This suggests the next major release will emphasize provider extensibility and canonical instruction rendering.

---

## 7. User Feedback Summary

- **CLI path-handling expectations:** Users expect absolute container paths to work naturally with `add-mount` ([#3706](https://github.com/nanocoai/nanoclaw/issues/3706)). The current silent double-nesting is a trust-eroding bug.
- **Scheduling reliability:** Task recurrence changes must recomputed `process_after` correctly ([#3705](https://github.com/nanocoai/nanoclaw/issues/3705)). Users depend on NanoClaw for cron-based automation; stale schedules break workflows.
- **Test infrastructure friction:** Concurrent test runs destroy each other's SQLite fixtures ([#3709](https://github.com/nanocoai/nanoclaw/issues/3709)), and full test suites leak ~355 temp directories per run ([PR #3710](https://github.com/nanocoai/nanoclaw/pull/3710)). These affect CI reliability and developer experience.
- **WhatsApp media waste:** Users are frustrated by unnecessary media downloads and missing document captions ([PR #3712](https://github.com/nanocoai/nanoclaw/pull/3712)).
- **Extensibility demand:** Fork maintainers need protected hooks for subclassing `SqliteAgentMailbox` without forking core ([#3704](https://github.com/nanocoai/nanoclaw/issues/3704)).
- **Provider experience:** The large provider-refactor effort reflects community demand for cleaner, more predictable multi-provider setups.

---

## 8. Backlog Watch

| Item | Open Since | Concern |
|---|---|---|
| [#2003](https://github.com/nanocoai/nanoclaw/pull/2003) — Voice transcription V2 | Apr 2026 (~4 months) | Long-open feature PR; resubmitted after earlier closure. Needs maintainer triage. |
| [#3440](https://github.com/nanocoai/nanoclaw/pull/3440) — Docker driver fixes | Aug 22, 2026 | Critical deployment issue (SELinux, mount permissions) still open for ~2 weeks. |
| [#3581–#3591](https://github.com/nanocoai/nanoclaw/pull/3581–#3591) — Provider contract refactoring (9 PRs) | Aug 19–28, 2026 | Large coordinated refactor still all-open. Blockers for #3356 (Cursor provider) and #3592 (speed property). |
| [#3706](https://github.com/nanocoai/nanoclaw/issues/3706) — add-mount absolute-path bug | Sep 3, 2026 | High-severity CLI bug with no fix PR yet; contradicts own documentation. |
| [#3705](https://github.com/nanocoai/nanoclaw/issues/3705) — recurrence schedule bug | Sep 3, 2026 | High-severity scheduling correctness issue with no fix PR yet. |

**Maintainer Attention Needed:** The provider contract PR cluster (#3581–#3591) is the highest-impact backlog item — it unblocks multiple feature PRs. The two high-severity bugs opened today (#3705, #3706) should be prioritized for quick fix PRs given their operational impact.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-09-04

## 1. Today's Overview

IronClaw shows **high development velocity** with 18 PRs and 11 issues touched in the last 24 hours. The most significant thematic push is the **WebUI TypeScript migration**, which saw three issues (#8033, #8035, #8036) closed and three corresponding PRs (#8037, #8038, #8039, #8040) merged today — eliminating ~134 `@ts-nocheck` suppressions across production and test code. LLM caching infrastructure is also advancing, with PRs #8044 and #8062 workin toward broader prompt-cache support across OpenAI and Anthropic providers. No new releases were published today; the active codebase remains in pre-release iteration.

---

## 2. Releases

**None.** No new versions were published on this date.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Summary | Link |
|----|---------|------|
| [#8060](https://github.com/nearai/ironclaw/pull/8060) | Added timeout headroom for whole-tree architecture scan tests in CI (`nextest`) | [PR #8060](https://github.com/nearai/ironclaw/pull/8060) |
| [#8043](https://github.com/nearai/ironclaw/pull/8043) | **Perf fix:** Coalesced streamed text updates — eliminated O(N·k) re-sanitization cost on each delta | [PR #8043](https://github.com/nearai/ironclaw/pull/8043) |
| [#8046](https://github.com/nearai/ironclaw/pull/8046) | **Subagent R3-3a:** Child approval/auth gate notifications now reach the parent's inbox instead of being silently screened out | [PR #8046](https://github.com/nearai/ironclaw/pull/8046) |
| [#8058](https://github.com/nearai/ironclaw/pull/8058) | Fixed `api-boundary.test.ts` to use live extension ID instead of stale `"web-push"` spelling | [PR #8058](https://github.com/nearai/ironclaw/pull/8058) |
| [#8055](https://github.com/nearai/ironclaw/pull/8055) | **Unblocked `main`:** Fixed `assets_are_embedded` test panic caused by `authorizeTraceHold` path change | [PR #8055](https://github.com/nearai/ironclaw/pull/8055) |
| [#8037](https://github.com/nearai/ironclaw/pull/8037) | Ratcheted TypeScript suppressions — removed 40 `@ts-nocheck` directives, added legacy baseline | [PR #8037](https://github.com/nearai/ironclaw/pull/8037) |
| [#7984](https://github.com/nearai/ironclaw/pull/7984) | **Bug fix:** `tool_search` replies now sized to the model's first-look envelope, preventing silent result truncation | [PR #7984](https://github.com/nearai/ironclaw/pull/7984) |
| [#8038](https://github.com/nearai/ironclaw/pull/8038) | **WebUI refactor:** Replaced permissive JSON transport with typed object boundaries and runtime decoders for device-link, pairing, settings, projects, and workspace APIs | [PR #8038](https://github.com/nearai/ironclaw/pull/8038) |
| [#8040](https://github.com/nearai/ironclaw/pull/8040) | **WebUI tests:** Removed 94 test-side `@ts-nocheck` directives, added typed shared helpers for browser globals, VM module exports, and synthetic JSX rendering | [PR #8040](https://github.com/nearai/ironclaw/pull/8040) |
| [#8039](https://github.com/nearai/ironclaw/pull/8039) | **WebUI production:** Removed `@ts-nocheck` from 64 production components, hooks, pages, and helpers; added explicit React Query, outlet-context, and auth payload types | [PR #8039](https://github.com/nearai/ironclaw/pull/8039) |

### Key Themes
- **WebUI type-safety push:** ~4 major PRs and 3 related issues landed, marking a decisive move toward fully typed frontend code.
- **Subagent reliability:** R3 slices 3a and 3b advance the approval-gate notification pipeline for child runs.
- **LLM caching expansion:** Work continues on prompt-cache-key support across OpenAI and Anthropic transport paths.

---

## 4. Community Hot Topics

| Topic | Link | Analysis |
|-------|------|----------|
| **Persistent per-user sandboxed executor** (#7903) — high-risk architectural decision spike | [Issue #7903](https://github.com/nearai/ironclaw/issues/7903) | The highest-impact open issue. Proposes moving the canonical agent loop into a persistent Docker sandbox, fundamentally shifting the trust boundary. Signals deep investment in sandbox isolation as a first-class feature. |
| **MCP egress errors are undiagnosable** (#8009) | [Issue #8009](https://github.com/nearai/ironclaw/issues/8009) | `mcp_http_error` collapses all `RuntimeHttpEgressError` variants into a single `"response_error"` token, making hosted-MCP discovery failures impossible to debug. Reflects a real pain point for operators running ironclaw with external MCP servers. |
| **Slash-command UX batch** (#8063–#8066) — 4 issues from `italic-jinxin` | [#8063](https://github.com/nearai/ironclaw/issues/8063), [#8064](https://github.com/nearai/ironclaw/issues/8064), [#8065](https://github.com/nearai/ironclaw/issues/8065), [#8066](https://github.com/nearai/ironclaw/issues/8066) | All filed today by the same contributor, all UX-focused: command menu auto-scroll, consistent metadata alignment, dismissible result cards, and preventing card collapse. Clear signal that slash-command ergonomics need polish. |
| **Daily failure taxonomy** (#8052) | [Issue #8052](https://github.com/nearai/ironclaw/issues/8052) | Automated benchmark reporting (`officeqa` suite) flags genuine model-quality errors in deepseek-v4-flash over OCR'd Treasury Bulletins — operational telemetry driving improvement. |

---

## 5. Bugs & Stability

| Severity | Item | Link | Notes |
|----------|------|------|-------|
| **High** | MCP egress errors flatten to `"response_error"` — undiagnosable | [Issue #8009](https://github.com/nearai/ironclaw/issues/8009) | Open. No fix PR yet. Impacts hosted-MCP discovery debugging. |
| **Medium** | `tool_search` reply truncation / silent data loss | [PR #7984](https://github.com/nearai/ironclaw/pull/7984) | ✅ **Fixed** (merged). Reply now sized to the model's first-look envelope. |
| **Medium** | Unpaired Telegram users get commands before pairing notice | [PR #8054](https://github.com/nearai/ironclaw/pull/8054) | Open. Root cause: command admission ran before pairing lookup. |
| **Low** | Command result cards collapse to invisible lines | [Issue #8066](https://github.com/nearai/ironclaw/issues/8066) | Open. UX regression from flex layout behavior. |
| **Low** | Malformed embedded tool-result text panics on JSON delimiter mismatch | [PR #8056](https://github.com/nearai/ironclaw/pull/8056) | Open. Checked lookup + fail-closed redaction fallback proposed. |
| **Low** | `cancel_response` hardcodes reason incompatible with product parser | [PR #8059](https://github.com/nearai/ironclaw/pull/8059) | Open. `/api/v1/responses/{id}/cancel` returns 400 in all states. |
| **Low** | `@ts-nocheck` accumulation in WebUI (now resolved) | [PRs #8037, #8038, #8039, #8040](https://github.com/nearai/ironclaw/pull/8037) | ✅ Fixed. 134 suppressions removed with CI ratchet in place. |

---

## 6. Feature Requests & Roadmap Signals

| Request | Link | Signal |
|---------|------|--------|
| **Prompt budget from model-advertised window** (#8057, PR #8053) | [Issue #8057](https://github.com/nearai/ironclaw/issues/8057), [PR #8053](https://github.com/nearai/ironclaw/pull/8053) | The hardcoded 128k/20k budget ignores provider-advertised windows. PR #8053 derives budget from `PromptContextTokenBudget::from_advertised_window`. **Strong candidate for next release.** |
| **Conversation cache keys on OpenAI paths** (PR #8062) | [PR #8062](https://github.com/nearai/ironclaw/pull/8062) | Stable prompt-cache keys per conversation across all OpenAI-compatible providers. **Likely next-release feature.** |
| **Claude family cache-gate denylist** (PR #8044) | [PR #8044](https://github.com/nearai/ironclaw/pull/8044) | Expands prompt cache support beyond hardcoded `claude-3/4` prefixes. **Will ship with #8062.** |
| **Concurrent-children cap for subagents** (PR #8061) | [PR #8061](https://github.com/nearai/ironclaw/pull/8061) | R2 debt + R3-3b verification. **Ready for inclusion.** |
| **Dismissible command result cards** (#8064) | [Issue #8064](https://github.com/nearai/ironclaw/issues/8064) | UX enhancement requested by active user; no fix PR yet. **Likely next minor release.** |
| **Persistent sandboxed executor architecture** (#7903) | [Issue #7903](https://github.com/nearai/ironclaw/issues/7903) | Major architectural spike. Not imminent, but sets the direction for long-term isolation design. |

---

## 7. User Feedback Summary

- **Slash-command UX is a pain point.** Four issues filed in a single day (#8063–#8066) from `italic-jinxin` cover auto-scroll, alignment, dismissal, and card collapse — all indicating that command result management feels unpolished in daily use.
- **MCP debugging is broken.** Issue #8009 captures operator frustration: egress failures are invisible, making hosted-MCP setups effectively undiagnosable.
- **Prompt budget overflows are real.** Issue #8057 highlights that identity, skills, tool schemas, and channel context are layered on top of the transcript budget without accounting for their token cost — a frequent source of provider errors.
- **First-contact Telegram experience is flawed.** PR #8054 notes that unpaired users see the command inventory before the pairing notice, creating confusion on first interaction.
- **Type-safety improvements are appreciated.** The large TypeScript migration (10+ PRs) was executed cleanly with no reported regressions, reflecting well on maintainer responsiveness.

---

## 8. Backlog Watch

| Item | Link | Reason for Attention |
|------|------|---------------------|
| **#7903** — Persistent sandboxed executor design spike | [Issue #7903](https://github.com/nearai/ironclaw/issues/7903) | Created 2026-08-26, still open. High-risk architectural decision with no resolution timeline. |
| **#8009** — MCP egress error visibility | [Issue #8009](https://github.com/nearai/ironclaw/issues/8009) | Created 2026-08-31, open, no fix PR. Impacts a growing set of hosted-MCP operators. |
| **#8054** — Telegram pairing-before-command admission | [PR #8054](https://github.com/nearai/ironclaw/pull/8054) | Open PR, needs maintainer review. First-contact UX fix for Telegram users. |
| **#8059** — Cancel reason parser mismatch | [PR #8059](https://github.com/nearai/ironclaw/pull/8059) | Open PR from external contributor (`jlwaugh`). `POST /api/v1/responses/{id}/cancel` is non-functional in all states. |
| **#8056** — Malformed tool-result panic | [PR #8056](https://github.com/nearai/ironclaw/pull/8056) | Open PR from `BenKurrek`. Edge-case panic in host API, low severity but easy fix. |
| **#8062** — Conversation cache keys (open) | [PR #8062](https://github.com/nearai/ironclaw/pull/8062) | Open, large PR. Needs review before it can ship alongside #8044. |
| **#8053** — Prompt budget from advertised window (open) | [PR #8053](https://github.com/nearai/ironclaw/pull/8053) | Open, large PR. Directly addresses #8057; merging would close the loop. |

---

**Overall Health Assessment:** Strong. 10 PRs merged in 24h, zero release-blocking regressions, and a clear roadmap emerging around LLM caching, subagent reliability, and WebUI type-safety. The primary concern is the open architectural spike (#7903) and the MCP error-visibility gap (#8009), both of which warrant maintainer attention in the near term.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-09-04

## 1. Today's Overview

LobsterAI activity remains high with **6 issues** and **15 PRs** updated in the last 24 hours. The dominant signal is the continued merge of the 2026.8.31 release cycle (10 PRs merged/closed today), indicating the team is finalizing polish and bug fixes ahead of the next version. Four new open issues surfaced today, including two previously-stale issues (#1082, #1088, #1089) that saw recent updates, and one fresh feature request (#2601) for MCP Apps UI rendering. No new release was published today. Overall project health is strong — a healthy ratio of merged fixes to open bugs, with active community contributions across desktop, IM, and Cowork areas.

## 2. Releases

No new release was published today. The latest release remains **2026.8.31** (PR #2600, merged 2026-09-03), which introduced:
- Guided first-run experience
- Faster Library browsing
- Client support for sharing model-generated videos
- Clearer login and quota messaging
- Stronger Windows installer recovery

**No breaking changes or migration notes** were reported for this release.

## 3. Project Progress

**10 PRs merged/closed today:**

| PR | Area | Summary |
|---|---|---|
| [#2609](https://github.com/netease-youdao/LobsterAI/issues/2609) | Renderer / Main | Added install-confirmation dialog when agent turns or scheduled tasks are running; removed mid-download cancel in favor of silent-download-then-notify flow |
| [#2608](https://github.com/netease-youdao/LobsterAI/issues/2608) | Docs / Main | Removed dsh MCP delegation support |
| [#2605](https://github.com/netease-youdao/LobsterAI/issues/2605) | Windows | Fixed blurry installer icons by declaring DPI awareness |
| [#2606](https://github.com/netease-youdao/LobsterAI/issues/2606) | Windows | Launcher helper processes now start without a console window |
| [#2607](https://github.com/netease-youdao/LobsterAI/issues/2607) | Build / OpenClaw | Removed dsh from peer installs to reduce plugin bundle size |
| [#2604](https://github.com/netease-youdao/LobsterAI/issues/2604) | Renderer / Cowork | Dimmed exhausted voice input button while keeping it clickable |
| [#2603](https://github.com/netease-youdao/LobsterAI/issues/2603) | Renderer | Refined Chinese voice quota exhausted copy with free-trial subscription wording |
| [#2602](https://github.com/netease-youdao/LobsterAI/issues/2602) | Browser / All | Restored interactive in-app Agent Browser with MCP bridge, encrypted credential storage, and approval-gated autofill |
| [#2599](https://github.com/netease-youdao/LobsterAI/issues/2599) | IM | Improved bot card layout with two-column responsive grid |
| [#2600](https://github.com/netease-youdao/LobsterAI/issues/2600) | Release | Released version 2026.8.31 |

**Key theme:** Desktop client polish (Windows installer fixes, browser restoration, install UX) and IM/coworking UI refinements dominated today's merges.

## 4. Community Hot Topics

**Most discussed issues today:**

- **[#2601](https://github.com/netease-youdao/LobsterAI/issues/2601)** — *Support rendering MCP Apps / Prefab UI in the desktop client* (NEW, 1 comment)
  MCP servers using the `ui://` resource protocol (e.g., PrefectHQ Prefab, FastMCP) return interactive HTML UIs that the current desktop client cannot render. Users are requesting full MCP Apps support for richer agent tooling experiences.

- **[#1088](https://github.com/netease-youdao/LobsterAI/issues/1088)** — *Prefetch async callback does not validate turnToken, risking cross-turn data pollution* (OPEN, stale, 1 comment)
  A race condition where a `prefetchChannelUserMessages` fire-and-forget operation from Turn A could resume after Turn B starts, incorrectly writing user messages to the wrong session turn. Root cause traced to `openclawRuntimeAdapter.ts:3809-3814`.

- **[#1089](https://github.com/netease-youdao/LobsterAI/issues/1089)** — *CoworkRunner startSession/continueSession lacks reentrancy protection* (OPEN, stale, 1 comment)
  Concurrent calls to `startSession()`/`continueSession()` on the same `sessionId` (triggered by rapid user messages or IM gateway batch delivery) can corrupt shared `ActiveSession` state and produce garbled streamed messages. File: `coworkRunner.ts:1425-1533`.

- **[#1556](https://github.com/netease-youdao/LobsterAI/issues/1556)** — *IM bot configuration guide returns 404* (CLOSED today)
  Documentation link broken. Now resolved.

- **[#1552](https://github.com/netease-youdao/LobsterAI/issues/1552)** — *File card support for AI-generated Markdown/code artifacts* (CLOSED today)
  Users requested in-app file preview cards after Write tool invocations. Resolved with a FileCard component showing file icon, path, type, size, and action buttons.

**Underlying needs:** The community is pushing for (1) deeper MCP ecosystem integration (UI rendering, delegation), (2) concurrency safety in the Cowork runtime, and (3) better artifact preview workflows.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| **High** | [#1088](https://github.com/netease-youdao/LobsterAI/issues/1088) | Prefetch callbacks can pollute another turn's message queue due to missing turnToken validation | None yet |
| **High** | [#1089](https://github.com/netease-youdao/LobsterAI/issues/1089) | No reentrancy guard on `startSession`/`continueSession`; concurrent calls corrupt shared state and duplicate/garble messages | None yet |
| **Medium** | [#1082](https://github.com/netease-youdao/LobsterAI/issues/1082) | `package.json` `openclaw.version` at v2026.3.2 may not support the latest OpenClaw; national security compliance concern | None yet |
| **Low** | [#2601](https://github.com/netease-youdao/LobsterAI/issues/2601) | MCP Apps `ui://` HTML content not rendered in desktop client | Feature request, not a bug |

**Notable closed bugs today:**
- [#1556](https://github.com/netease-youdao/LobsterAI/issues/1556) — IM config guide 404 (resolved)
- [#1552](https://github.com/netease-youdao/LobsterAI/issues/1552) — No file preview for Write tool artifacts (resolved via FileCard)

## 6. Feature Requests & Roadmap Signals

| PR/Issue | Type | Summary | Likelihood for Next Release |
|---|---|---|---|
| [#2601](https://github.com/netease-youdao/LobsterAI/issues/2601) | Feature | Render MCP Apps / Prefab UI (`ui://` resources) in desktop client | **High** — directly follows the restored in-app browser (#2602) |
| [#1079](https://github.com/netease-youdao/LobsterAI/issues/1079) | Feature | "Current Process" right panel in Cowork showing tool execution logs & diff views | **Medium** — ~400-line PR already prepared with `ProgressPanel.tsx` |
| [#1078](https://github.com/netease-youdao/LobsterAI/issues/1078) | Feature | IM push notification on scheduled task failure | **Medium** — PR addresses asymmetric success/failure notification |
| [#1087](https://github.com/netease-youdao/LobsterAI/issues/1087) | Fix | Duplicate error messages on `continueSession` failure | **High** — simple fix, already has a PR ready |
| [#1081](https://github.com/netease-youdao/LobsterAI/issues/1081) | Fix | MCP sync i18n incomplete + scroll bar clipping in edit dialog | **High** — small UI fix, PR ready |

**Signal:** The team is investing heavily in the Cowork experience (diff panels, voice quota UX, session reliability) and MCP ecosystem integration (browser restoration, Apps UI, delegation cleanup). The next release (targeting 2026.9.4 per PR #2602) will likely ship the in-app browser restore and voice quota refinements, with the diff panel and MCP Apps support as follow-ups.

## 7. User Feedback Summary

**Pain points expressed:**
- **Artifact visibility:** Users want immediate in-app previews of files generated by the Write tool rather than copying content manually or switching to a file manager (#1552 — now resolved).
- **Voice input clarity:** Quota-exhausted state was unclear; users needed better visual feedback and copy (#2603, #2604 — now resolved).
- **Installation UX:** Silent app termination during updates when agent turns were running caused data loss concerns; users want confirmation dialogs (#2609 — now resolved).
- **IM bot discovery:** Bot card layout was cramped and non-responsive; improved to two-column layout (#2599 — now resolved).
- **Scheduled task reliability:** Users couldn't discover failed cron jobs without manually checking the UI; want proactive IM failure notifications (#1078).
- **MCP integration depth:** Power users want the desktop client to render rich MCP App UIs, not just execute tools (#2601).

**Satisfaction indicators:** The rapid closure of documentation (404), artifact preview, voice quota UX, and Windows installer issues suggests the team is responsive to user-reported friction. The two high-severity concurrency bugs (#1088, #1089) remain unfixed and are the most significant risk to user experience.

## 8. Backlog Watch

| Issue/PR | Age | Priority | Status |
|---|---|---|---|
| [#1082](https://github.com/netease-youdao/LobsterAI/issues/1082) | ~5 months | **High** (security/compliance) | Stale, no response — `openclaw.version` may be outdated per national security guidelines |
| [#1088](https://github.com/netease-youdao/LobsterAI/issues/1088) | ~5 months | **High** (data integrity) | Stale, no fix — cross-turn message pollution in prefetch |
| [#1089](https://github.com/netease-youdao/LobsterAI/issues/1089) | ~5 months | **High** (stability) | Stale, no fix — missing reentrancy guard in CoworkRunner |
| [#1078](https://github.com/netease-youdao/LobsterAI/issues/1078) | ~5 months | Medium | Stale, PR exists but unmerged — IM failure notifications for scheduled tasks |
| [#1079](https://github.com/netease-youdao/LobsterAI/issues/1079) | ~5 months | Medium | Stale, PR exists but unmerged — Cowork progress panel with diff views |
| [#1081](https://github.com/netease-youdao/LobsterAI/issues/1081) | ~5 months | Low | Stale, PR exists but unmerged — MCP i18n + scroll bar fix |
| [#1087](https://github.com/netease-youdao/LobsterAI/issues/1087) | ~5 months | Medium | Stale, PR exists but unmerged — duplicate error message on session continue failure |
| [#1277](https://github.com/netease-youdao/LobsterAI/issues/1277) | ~5 months | Low | Open — Dependabot Electron upgrade from 40.2.1 → 44.0.0 (2 updates) |

**Recommendation:** Issues #1082, #1088, and #1089 have been stale for approximately 5 months despite high severity. Maintainer attention is recommended, particularly for #1088 and #1089 which pose real data integrity and stability risks in production Cowork sessions. The four unmerged PRs (#1078, #1079, #1081, #1087) are ready for review and could be triaged together.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-09-04

## 1. Today's Overview

CoPaw (agentscope-ai/QwenPaw) shows robust development activity with **27 issues** and **36 PRs** updated in the last 24 hours. The project has no new releases today but continues to advance toward the **v2.2.0 stable** launch, with the multi-tenant QwenPaw Hub as a flagship initiative. Activity is heavily skewed toward bug fixes (8 closed), security hardening, and UI/UX refinements, indicating a mature codebase in active stabilization. The presence of multiple "good first issue" tags and first-time contributors signals a healthy onboarding funnel.

---

## 2. Releases

**No new releases today.** The v2.2.0 Stable release verification (Issue #7515) was completed on 2026-09-03. The multi-tenant **QwenPaw Hub** is scoped for the 2.2.0 milestone (Issue #7318, 17 comments, 3 👍).

---

## 3. Project Progress

### Merged / Closed PRs Today
- **#7524** — Console: separated free and pro model tabs; added regression coverage for mixed providers.
- **#7525** — Governance: fixed CRITICAL findings being auto-rejected instead of routed to approval workflow (closes #7496).
- **#7498** — Tools: now returns HTTP 404 instead of 500 when updating config for an unknown tool.
- **#7267** — Channels: made contract checks portable and UTF-8 safe across platforms (closes #7264).

### Open PRs Advancing
- **#7539** — Moves managed Chromium install off the 60-second startup critical path, enabling lazy-load on first `Browser.connect()`.
- **#7504** — Enforces per-tool MCP whitelist on the agent runtime path, preventing disabled tools from remaining callable post-2.0 rewrite.
- **#7538** — Unifies runtime environment management via `EnvVarLoader`, with QwenPaw-managed values overriding inherited `.env` values.
- **#6399** — Adds reranker UI config panel to ReMeLightMemoryCard (under review).
- **#7542** — Adds scroll-back message pagination for compacted chats, restoring access to history.db-stored messages.
- **#7080** — Introduces optional PowerContext long-term memory backend as a peer to ReMeLight.

---

## 4. Community Hot Topics

| Issue / PR | Activity | Link |
|---|---|---|
| **#7318** — QwenPaw Hub multi-tenant roadmap | 17 comments, 3 👍 | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7318) |
| **#7511** — Security sandbox breach | 9 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7511) |
| **#7505** — LAN LLM server client disconnect / retry storms | 6 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7505) |
| **#4036** — Adding a model requires too many clicks | 6 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/4036) |
| **#7443** — Dangerous instructions evading safety filters | 6 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7443) |
| **#7469** — ReMe background indexing job fails silently | 5 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7469) |
| **#7476** — Cron tasks double-scheduled within misfire_grace window | 4 comments | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/7476) |

**Analysis:** The community's top concern is **trust and safety** — the sandbox breach (#7511) and instruction evasion (#7443) together indicate users are pushing hard on governance reliability. The Hub roadmap (#7318) being the most-discussed open issue suggests strong demand for **multi-user/team deployment**. The model-addition friction (#4036) is a persistent usability pain point resurfacing after the `max_tokens → max_output_length` migration broke custom providers (#7474).

---

## 5. Bugs & Stability

### Critical / High Severity
- **#7511** — *Security sandbox breach* (closed). External Zhihu post documents a bypass; 9 comments indicate ongoing investigation.
- **#7443** — *Dangerous instructions evading safety filters* (open). User reports evasion of CRITICAL-tier rules. **Fix PR #7525** is now merged, addressing the related auto-rejection bug (#7496).
- **#7534** — *Feishu session queue consumer deadlocks* (open). A priority-10 card message causes the consumer to silently stall; subsequent priority-20 messages cannot spawn a new consumer. **No fix PR yet.**

### Medium Severity
- **#7469** — *ReMe embedding job fails silently* with `Dependency as_embedding:default accessed before start()`. New memories are not indexed. **No fix PR yet.**
- **#7505** — *LAN LLM client disconnect / retry storm* causing timeout failures with LM Studio backends. **No fix PR yet.**
- **#7476** — *Cron double-scheduling* within `misfire_grace` window produces duplicate backup files. **No fix PR yet.**
- **#7541** — *Architectural bug*: sessions are incorrectly isolated by channel (web vs. desktop vs. Telegram), preventing a unified user experience. **No fix PR yet.**
- **#7510** — *ReMe /memory/status returns 500* on v2.2.0-beta.7 Desktop. **No fix PR yet.**
- **#7529** — *Langfuse monitoring shows blank tool outputs* despite tools executing correctly; observation/span `output` field is null. **No fix PR yet.**
- **#7516** — *WeCom cannot send images* represented as base64 data URLs; requires local file path. **No fix PR yet.**

### Low Severity / Cosmetic
- **#7545** — *Desktop right-click copy missing* in chat input (web works fine). **Closed.**
- **#7512** — *Cannot switch conversations* while a session is actively thinking/outputting. **Closed.**

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue | Likelihood for v2.2.0+ |
|---|---|---|
| **QwenPaw Hub multi-tenant edition** | #7318 | ⭐⭐⭐⭐⭐ — Flagship, explicitly scoped |
| **Background / deferred app updates** (current update blocks UI) | #7543 | ⭐⭐⭐⭐ — High user impact, simple to implement |
| **Mobile remote desktop connection** to running QwenPaw Desktop | #7519 | ⭐⭐⭐ — Niche but clear use case |
| **Message buttons / steer-mode** (Codex-like inline correction) | #1775, #7533 | ⭐⭐⭐ — Long-standing request, good first issue |
| **Preserve persona during context compaction** | #7527 | ⭐⭐⭐⭐ — Quality-of-life for long sessions |
| **Opt-out of hardcoded "About" identity line** | #7540 | ⭐⭐⭐ — Power-user request |
| **Matrix channel: Element recovery-key + OIDC (MSC2965)** | #7535 | ⭐⭐ — Niche but valuable for privacy-focused users |
| **Scroll-back pagination for compacted chats** | #7542 (PR open) | ⭐⭐⭐⭐ — Already in progress |
| **Custom model ordering (drag-and-drop)** | #5399 — ✅ Closed | Already shipped |

---

## 7. User Feedback Summary

**Pain points:**
- **Security anxiety is elevated.** Two separate sandbox/instruction-evasion reports in one week (#7511, #7443) suggest users are losing confidence in the governance layer. The #7525 fix helps but doesn't fully address #7443's evasion concern.
- **Local/LAN LLM integration is fragile.** Issue #7505 highlights instability with LM Studio and local backends — a core use case for privacy-conscious users.
- **Custom provider migration is painful.** PR #7337's `max_tokens → max_output_length` rename broke existing custom provider configs (#7474), and the model-addition flow remains too click-heavy (#4036).
- **Channel-specific bugs** (Feishu consumer stall #7534, WeCom base64 images #7516, Matrix OIDC gaps #7535) indicate the multi-channel architecture needs more integration-level testing.
- **ReMe memory reliability** is a concern: silent indexing failures (#7469) and 500 errors on status endpoints (#7510) undermine trust in long-term memory features.

**Satisfaction signals:**
- Rapid response on closed bugs (#7545, #7512) and governance fixes (#7525).
- Strong contributor engagement with multiple PRs from first-time contributors.
- The v2.2.0 stable release verification completed on schedule (#7515).

---

## 8. Backlog Watch

| Issue | Reason for Watch |
|---|---|
| **#7443** — Dangerous instructions evading safety filters | **Critical security.** Open since 2026-08-31 with 6 comments; no fix PR linked. Needs maintainer triage. |
| **#7534** — Feishu consumer deadlocks per session | **Production-impacting.** Open since 2026-09-03; silently kills entire Feishu sessions. No fix PR. |
| **#7469** — ReMe background indexing failure | **Data-loss risk.** Silent failures mean memories are lost without user awareness. No fix PR. |
| **#7505** — LAN LLM client disconnect storms | **Core use case.** Affects local/LAN LLM users; no fix PR after 2 days. |
| **#7541** — Session isolation by channel (architectural) | **Design-level bug.** Open since 2026-09-03; requires architectural decision, not a quick fix. |
| **#4036** — Model addition UX friction (good first issue) | **Usability backlog.** Open since May 2026 with 6 comments; long-standing pain point. |
| **#7510** — ReMe /memory/status 500 on v2.2.0-beta.7 | **Regression.** Should be caught before stable release; open for 2 days with no response. |

**Overall health assessment:** CoPaw is in active stabilization ahead of the v2.2.0 stable launch. The bug-closure rate is healthy (8 closed in 24h), and critical governance fixes are landing. However, **two open security issues (#7443, #7534) and the ReMe reliability cluster (#7469, #7510)** warrant maintainer attention before the next release cycle. The community is engaged and contributing at a strong pace.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-09-04

## 1. Today's Overview

ZeroClaw shows sustained development velocity with **50 issues and 50 PRs updated** in the last 24 hours (36 open issues active, 14 closed; 49 open PRs, 1 merged/closed). No new releases were published. The project is in an active RFC-to-implementation phase, with several accepted security and runtime design documents now moving into code. Activity is dominated by security policy hardening, ACP (Agent Code Pane) session improvements, and cron subsystem extraction.

## 2. Releases

No new releases were published. The project continues to iterate on `master` via merged PRs without a tagged version bump.

## 3. Project Progress

**Merged/Closed today:**

- **[PR #10539](https://github.com/zeroclaw-labs/zeroclaw/issues/10539)** — *fix(runtime): stop advertising self-approval in tool schemas*. Closed. Resolved a security-adjacent issue where the `approved` arg was consumed by `shell`, `schedule`, and cron tools despite being stripped by `call_prep` before the approval gate.
- **[PR #10610](https://github.com/zeroclaw-labs/zeroclaw/pull/10610)** — *feat(security): implement accepted shell V1 permission policy (RFC #7155 Phase 0+1)*. Open, actively developed by @NiuBlibing. Delivers the unified tool permission policy and tiered approval framework in five single-concern commits.
- **[PR #10565](https://github.com/zeroclaw-labs/zeroclaw/pull/10565)** — *fix(zerocode): pin local Code sessions to process cwd*. Open fix for #10609, restoring correct working directory behavior for locally-launched zerocode sessions.

**Key work advancing:**
- Cron extraction into `zeroclaw-cron` crate ([PR #10557](https://github.com/zeroclaw-labs/zeroclaw/pull/10557))
- ACP transcript pagination and interrupted-turn persistence ([PR #10197](https://github.com/zeroclaw-labs/zeroclaw/pull/10197), [#10596](https://github.com/zeroclaw-labs/zeroclaw/pull/10596))
- Memory recall date stamping ([PR #10567](https://github.com/zeroclaw-labs/zeroclaw/pull/10567))

## 4. Community Hot Topics

| # | Issue/PR | Type | Comments | Link |
|---|----------|------|----------|------|
| 1 | Granular sandbox policy – filesystem restrictions | RFC (P2, high risk) | 23 | [#6996](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |
| 2 | Verifiable-intent constraint evaluation bug | Bug (P2, high risk) | 14 | [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) |
| 3 | Maintainer decision queue for RFCs | Tracker (P2) | 14 | [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| 4 | Verbatim channel send over gateway | RFC (P2, high risk) | 13 | [#10050](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) |
| 5 | Web bundle/daemon compatibility | RFC (P2, high risk) | 12 | [#9975](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) |
| 6 | CI cached Rust builds improvement | Enhancement (P2, high risk) | 7 | [#7108](https://github.com/zeroclaw-labs/zeroclaw/issues/7108) |
| 7 | Interactive agent context cap at 32K tokens | Bug (P2, medium) | 5 | [#10068](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) |
| 8 | Single-tool provider rounds for interactive agents | RFC (P2, high risk) | 5 | [#10222](https://github.com/zeroclaw-labs/zeroclaw/issues/10222) |
| 9 | Bitmaps unmaintained advisory waiver tracker | Tracker (P1, high risk) | 4 | [#9899](https://github.com/zeroclaw-labs/zeroclaw/issues/9899) |

**Analysis:** Security policy and sandboxing dominate the top discussions. The granular filesystem restrictions RFC (#6996) has been open since May with 23 comments, indicating strong community engagement on agent safety. The verifiable-intent bug (#9328) highlights a gap between L2 constraint checking and cryptographic credential verification — a trust-chain concern. The P1 bitmap advisory (#9899) remains blocked, suggesting a dependency resolution bottleneck.

## 5. Bugs & Stability

| # | Issue | Severity | Summary | Fix PR | Link |
|---|-------|----------|---------|--------|------|
| 1 | #10609 | S1 - workflow blocked | zerocode ignores launch cwd, forces agent workspace | [PR #10565](https://github.com/zeroclaw-labs/zeroclaw/pull/10565) | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10609) |
| 2 | #10603 | S1 - workflow blocked | OpenCode providers never send `x-opencode-session` header, breaking Go models | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10603) |
| 3 | #10068 | S2 - degraded | Interactive agent session caps context at 32K ignoring `max_context_tokens` | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10068) |
| 4 | #9328 | P2, high risk | `vi_verify` evaluates constraints without verifying credential chain | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) |
| 5 | #9899 | P1, high risk | `bitmaps 3.2.1` triggers RUSTSEC-2026-0247 advisory, CI blocked | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9899) |
| 6 | #10238 | S2 - degraded | ZeroCode shows stale Connected state after daemon exits | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10238) |
| 7 | #9905 | S2 - degraded | Discord audio transcription manager never bound to active agent provider | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9905) |
| 8 | #9231 | S1 - workflow blocked | Docker runtime commands nested inside second Docker sandbox | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9231) |
| 9 | #9387 | P1, high risk | Interactive approval responses accepted from any chat member (Telegram, Slack, Lark, Matrix) | — | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9387) |

**Two S1 bugs opened today** (#10609, #10603). The OpenCode session header issue (#10603) risks account flags on Go-based models and currently has no fix PR. The Docker sandbox nesting bug (#9231) remains unfixed and blocks workflow for users running inside containers.

## 6. Feature Requests & Roadmap Signals

| RFC/Feature | Status | Link |
|-------------|--------|------|
| Granular sandbox filesystem policy (#6996) | RFC, in-progress | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |
| Verbatim channel send without agent turn (#10050) | RFC, accepted | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10050) |
| Web bundle/daemon compatibility contract (#9975) | RFC Rev 3, accepted | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9975) |
| Single-tool provider rounds for interactive agents (#10222) | RFC, accepted | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10222) |
| Session-scoped prompt attachments (#10405) | Tracker, accepted | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10405) |
| Gemini speech-to-speech broker channel (#10406) | Tracker, accepted | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10406) |
| Memory continuity for Code-pane/ACP sessions (#10570) | Tracker, in-progress | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10570) |
| Anthropic thinking display progress updates (#10529) | Implemented, closed | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/10529) |

**Prediction for next release:** The shell V1 permission policy (RFC #7155, PR #10610) is the strongest candidate for inclusion, as implementation is already underway. ACP transcript pagination (#10596) and memory recall date stamping (#10567) are also close to merge. The verbatim channel send RFC (#10050) and Web bundle compatibility (#9975) are accepted but may require more implementation time.

## 7. User Feedback Summary

**Pain points expressed:**
- **Context window caps are opaque:** Users report the interactive agent silently capping at 32K tokens despite higher `max_context_tokens` config (#10068). This suggests a configuration drift or hardcoded fallback.
- **zerocode cwd confusion:** Launching zerocode from a local directory unexpectedly switches to the agent workspace (#10609, S1), breaking workflows that depend on relative paths.
- **OpenCode relay incompatibility:** The missing `x-opencode-session` header causes Go models to fail and may trigger account flags (#10603).
- **Docker double-sandboxing:** Users configuring Docker runtime report commands executing inside a nested sandbox (#9231), creating a workflow-blocking issue.
- **Channel approval trust gaps:** Security audit revealed that interactive approval prompts on Telegram, Slack, Lark, and Matrix are accepted from any chat member (#9387), not just the originating user — a significant trust boundary issue.

**Positive signals:** Anthropic thinking progress updates are now supported (#10529 closed). Twitch setup documentation added (#10581). The egress grant ceremony for plugin install is progressing (#9584).

## 8. Backlog Watch

| # | Issue | Priority | Risk | Wait Time | Link |
|---|-------|----------|------|-----------|------|
| 1 | #6996 — Granular sandbox policy RFC | P2 | High | ~3.5 months | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/6996) |
| 2 | #9899 — Bitmaps RUSTSEC advisory (CI blocked) | **P1** | High | ~1.5 months | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9899) |
| 3 | #9387 — Approval responses from any chat member | **P1** | High | ~1.5 months | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9387) |
| 4 | #9231 — Docker nested sandbox | S1 | High | ~1.5 months | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9231) |
| 5 | #7108 — CI Rust build caching | P2 | High | ~3 months | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/7108) |
| 6 | #7685 — Test coverage across 13 shards | P2 | High | ~3 months | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/7685) |
| 7 | #9328 — Verifiable-intent credential chain bug | P2 | High | ~1.5 months | [link](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) |

**Maintainer attention needed:** Two P1 security issues (#9899 blocking CI, #9387 trust boundary) have been open for over a month without resolution. The test coverage tracker (#7685) and CI optimization (#7108) have been open for 3+ months and represent structural health risks. The sandbox policy RFC (#6996) has 23 comments and is a linchpin for the project's security roadmap.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*