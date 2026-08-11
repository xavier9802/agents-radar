# OpenClaw Ecosystem Digest 2026-08-11

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-11 02:09 UTC

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



# OpenClaw Project Digest — 2026-08-11

## 1. Today's Overview

OpenClaw shows exceptionally high development velocity with **500 issues and 500 PRs updated in the last 24 hours**, indicating a very active contributor base and likely an automated triage sweep (clawsweeper labels). No new releases were published today. The project is in a stabilization phase: a significant number of P1 regressions and session-state bugs are being actively discussed, and multiple high-risk PRs are awaiting maintainer review or proof. Community engagement is strong, with several issues reaching 30–50 comments.

## 2. Releases

**No new releases today.** The latest tracked versions in open issues remain in the `2026.5.x`–`2026.7.x` beta/stable range.

## 3. Project Progress

### Notable Merged/Closed Items Today
- **[#86519](https://github.com/openclaw/openclaw/issues/86519)** (Closed) — Telegram duplicate-reply regression (2–10×) after 5.20 update, partially mitigated in 5.22.
- **[#96242](https://github.com/openclaw/openclaw/issues/96242)** (Closed) — Multiple independent paths causing duplicate Telegram messages.
- **[#114690](https://github.com/openclaw/openclaw/issues/114690)** (Closed) — Successful Discord source reply re-sent after native Codex compaction in the same turn.
- **[#90789](https://github.com/openclaw/openclaw/issues/90789)** (Closed) — Claude-cli synthetic "No response requested." placeholder leaving Telegram turns fully silent.
- **[#109145](https://github.com/openclaw/openclaw/issues/109145)** (Closed) — Gateway HTTP server listening but not accepting connections in v2026.7.1-beta.5.

### PRs Advancing Today
- **[PR #121647](https://github.com/openclaw/openclaw/pull/121647)** — *fix(context-engine): durable state stalls in long sessions* — Fixes durable context engine hanging after 20K events / 8 MiB transcript. **High priority, session-state impact.**
- **[PR #121784](https://github.com/openclaw/openclaw/pull/121784)** — *fix(system-agent): setup chat fails silently on dev-roster gateways* — Resolves silent failure in `openclaw gateway --dev` setup chat.
- **[PR #121780](https://github.com/openclaw/openclaw/pull/121780)** — *improve(gateway): defer non-startup runtime imports* — Reduces gateway cold-start time (addresses [regression in #119087](https://github.com/openclaw/openclaw/issues/119087)).
- **[PR #121792](https://github.com/openclaw/openclaw/pull/121792)** — *improve(ui): make warm session switches settle faster* — Reduces UI settle time from 266 ms to near-instant for 100-session / 100-message switches.
- **[PR #121705](https://github.com/openclaw/openclaw/pull/121705)** — *fix(ui): align agent switcher rows on one leading column* — Cosmetic UI fix for sidebar alignment.
- **[PR #121378](https://github.com/openclaw/openclaw/pull/121378)** — *fix(gateway): persist sessions.patch toolOverrides.webSearch true* — Fixes silent drop of `webSearch: true` during session patch normalization.

## 4. Community Hot Topics

| Issue | Comments | Topic | Link |
|-------|----------|-------|------|
| #121058 | 48 | Silent reply failures recurring after prior fix | [Issue](https://github.com/openclaw/openclaw/issues/121058) |
| #7707 | 34 | Memory Trust Tagging by Source (security) | [Issue](https://github.com/openclaw/openclaw/issues/7707) |
| #48788 | 20 | Centralized filename encoding for multi-encoding Content-Disposition | [Issue](https://github.com/openclaw/openclaw/issues/48788) |
| #22438 | 18 | Tiered bootstrap file loading for progressive context control | [Issue](https://github.com/openclaw/openclaw/issues/22438) |

**Analysis:** The top-discussed issues reveal three dominant community concerns:
1. **Reliability of reply delivery** (#121058) — Users are frustrated that previously-closed bug patterns recur, signaling a systemic issue with the monitoring/closure pipeline.
2. **Memory security & trust** (#7707) — Growing demand for source-aware memory tagging to prevent poisoning attacks, especially as OpenClaw integrates more web/third-party sources.
3. **Internationalization & encoding** (#48788) — Feishu/Chinese filename handling remains a pain point; the community wants a centralized encoding utility rather than ad-hoc fixes per channel.

Other high-engagement items include sub-agent orchestration (#27445, 12 comments, 5 👍) and per-agent cost budgeting (#42475, 14 comments), reflecting operator-level maturity in the user base.

## 5. Bugs & Stability

### P1 / Critical Bugs (Open)

| Issue | Summary | Severity | Fix PR? |
|-------|---------|----------|---------|
| [#115908](https://github.com/openclaw/openclaw/issues/115908) | Session transcript projection **livelock** under sustained writes, blocking main thread | 🔴 Crash-loop / diamond lobster | No known fix PR |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | **Zombie child process leak** from hook/tool execution, causing runtime degradation | 🔴 Crash-loop / silver shellfish | No known fix PR |
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | Silent reply failures **recurrence** after #116277 closure | 🔴 Platinum hermit | No fix PR |
| [#39476](https://github.com/openclaw/openclaw/issues/39476) | A2A `sessions_send` circular call causing **duplicate messages** | 🔴 Diamond lobster | No known fix PR |
| [#83598](https://github.com/openclaw/openclaw/issues/83598) | `anthropic:claude-cli` OAuth refresh dead-ends main lane (regression) | 🔴 Diamond lobster | No known fix PR |
| [#98702](https://github.com/openclaw/openclaw/issues/98702) | Inherited OpenAI OAuth rejected at provider for built-in runtime | 🟠 Platinum hermit | No known fix PR |
| [#111010](https://github.com/openclaw/openclaw/issues/111010) | Detached native Codex subagents **lose hook relay** when parent turn releases | 🟠 Platinum hermit | No known fix PR |
| [#89278](https://github.com/openclaw/openclaw/issues/89278) | Codex OAuth refresh succeeds but cron/heartbeat fail with 10s auth timeout | 🟠 Gold shrimp | No known fix PR |
| [#40001](https://github.com/openclaw/openclaw/issues/40001) | Write tool **lacks append mode** — cron sessions destroy shared files | 🟠 Diamond lobster | PR linked: #? (needs maintainer review) |
| [#53408](https://github.com/openclaw/openclaw/issues/53408) | `write`/`exec` tools **silently drop parameters** after 15+ turn conversations | 🟡 Gold shrimp | No known fix PR |
| [#119087](https://github.com/openclaw/openclaw/issues/119087) | Gateway **cold-start regressed ~2.5×** from beta.1 to beta.7 | 🟡 Silver shellfish | [PR #121780](https://github.com/openclaw/openclaw/pull/121780) addresses deferred imports |
| [#92516](https://github.com/openclaw/openclaw/issues/92516) | Containerized deploys can't use externalized channel plugins (trust gating) | 🟠 Diamond lobster | No known fix PR |

### Key Trend
**Session-state and message-loss bugs dominate.** At least 8 of the top 15 most-commented issues involve duplicated messages, lost replies, or session lifecycle failures. The transcript projection livelock (#115908) and zombie process leak (#97616) are the most severe open stability risks with no visible fix PRs.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | 👍 | Likelihood |
|-------|---------|-----|------------|
| #7707 | Memory Trust Tagging by Source | 0 | **High** — security-critical, aligns with plugin unbundling direction |
| #42475 | Per-agent cost budget enforcement at gateway | 1 | **Medium-High** — operator demand, directly addresses spend concerns |
| #27445 | `announceTarget` for sub-agent completion routing | 5 | **Medium** — strong reaction count, improves multi-agent orchestration |
| #22438 | Tiered bootstrap file loading | 0 | **Medium** — context-window efficiency, relevant for large workspaces |
| #13700 | Session snapshots (`/session save\|load`) | 0 | **Low-Medium** — useful but niche |
| #15032 | Per-spawn tool restrictions for sub-agents | 0 | **Medium** — security isolation, complements trust tagging |
| #42648 | Memory MVP write pipeline (classify, dedupe, merge) | 0 | **High** — foundational memory improvement, multiple PRs in progress |
| #51441 | Expose resolved backend model in session status | 1 | **Medium** — observability, useful with LiteLLM routing |
| #38568 | Inject context window % into system prompt | 2 | **Low** — nice-to-have UX improvement |
| #28300 | Theme Customization System for Control UI | 5 | **Low** — aesthetic, lower priority than stability |

**Prediction:** The next minor release will likely include memory write-pipeline improvements (#42648), sub-agent routing (#27445), and cost budgeting (#42475), assuming fix PRs for the P1 session-state bugs land first.

## 7. User Feedback Summary

**Pain Points:**
- **Duplicate/repeated messages** on Telegram, Feishu, and Discord remain the #1 user complaint, with multiple regression reports across versions.
- **OAuth/auth refresh failures** cause complete agent lockups, especially for Codex, Anthropic CLI, and OpenAI built-in runtimes.
- **Cron job reliability** is poor: silent timeouts during API outages (#45494), setup failures (#82662), and file overwrites (#40001) are frequently reported.
- **Gateway cold-start degradation** (#119087) is impacting containerized/self-hosted deployments.
- **Plugin trust model** (#92516) blocks self-hosted channel use post-unbundling.

**Satisfaction Signals:**
- Users appreciate the **Control UI theme customization** (#28300) and **Slack thread status updates** (#33413).
- The **write/exec parameter loss** (#53408) bug has 2 👍, indicating multiple affected users.
- **Memory features** are highly valued (#7707, #42648), but users want them to be more robust and secure.

## 8. Backlog Watch

These items have been open for an extended period and need maintainer attention:

| Issue | Open Since | Comments | Blockers | Link |
|-------|-----------|----------|----------|------|
| #7707 | Feb 2026 | 34 | `needs-product-decision`, `needs-security-review` | [Issue](https://github.com/openclaw/openclaw/issues/7707) |
| #22438 | Feb 2026 | 18 | `needs-product-decision` | [Issue](https://github.com/openclaw/openclaw/issues/22438) |
| #42475 | Mar 2026 | 14 | `needs-product-decision` | [Issue](https://github.com/openclaw/openclaw/issues/42475) |
| #115908 | Jul 2026 | 13 | `source-repro` | [Issue](https://github.com/openclaw/openclaw/issues/115908) |
| #97616 | Jun 2026 | 7 | — | [Issue](https://github.com/openclaw/openclaw/issues/97616) |
| #121058 | Aug 2026 | 48 | `no-new-fix-pr` | [Issue](https://github.com/openclaw/openclaw/issues/121058) |
| #47975 | Mar 2026 | 10 | Subagent sessions persist, main session unresponsive | [Issue](https://github.com/openclaw/openclaw/issues/47975) |
| #92516 | Jun 2026 | 10 | `needs-security-review` — channel plugin trust model | [Issue](https://github.com/openclaw/openclaw/issues/92516) |

**PRs Needing Maintainer Review:**
- [PR #120534](https://github.com/openclaw/openclaw/pull/120534) — Audit refactor (XL, needs 4 explicit owner decisions)
- [PR #121566](https://github.com/openclaw/openclaw/pull/121566) — Claude live sessions refactor (XL, split by concept)
- [PR #121366](https://github.com/openclaw/openclaw/pull/121366) — Consolidate coercion helpers (XL, cross-cutting)

---

**Project Health Assessment:** OpenClaw is in a **high-velocity but stability-stressed** state. The 500-issue/500-PR daily churn suggests strong community involvement, but the concentration of P1 session-state and message-loss bugs — many without fix PRs — indicates the codebase is outpacing its QA coverage. The closed issues today were predominantly duplicates and regressions, confirming this is a refinement cycle rather than a feature-release cycle. The most pressing risk is the transcript projection livelock (#115908) and zombie process leak (#97616), both of which can cause full gateway degradation under sustained load.

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Comparison Report
**Date: 2026-08-11 | Personal AI Agent / Assistant Open-Source Projects**

---

## 1. Ecosystem Overview

The personal AI agent open-source ecosystem in August 2026 is characterized by rapid iteration, increasing security consciousness, and a maturing focus on production reliability. Eleven tracked projects span a spectrum from full-featured gateways (OpenClaw, IronClaw, CoPaw) to lightweight assistants (NanoBot, PicoClaw) and niche protocol implementations (NullClaw, ZeroClaw). The dominant themes across all projects are session-state stability, message-delivery reliability, security hardening, and MCP/plugin ecosystem expansion. Several projects are simultaneously scaling from hobbyist tools toward enterprise-grade deployments, creating tension between feature velocity and operational rigor.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Releases | Health Score* |
|---------|-------------|-----------|----------|---------------|
| **OpenClaw** | 500 | 500 | None | 6.5/10 — high velocity, stability-stressed |
| **IronClaw** | 25 | 33 | v1.1.1-rc.1 (1 day old) | 7.5/10 — active RC phase, responsive |
| **CoPaw** | 33 | 33 | None (v2.1.0b2, 2d old) | 7.0/10 — strong velocity, some critical bugs |
| **ZeroClaw** | 50 | 48 | None (0.8.3 since Jul) | 5.5/10 — high discussion, security backlog |
| **NanoBot** | 4 | 24 | None | 8.0/10 — focused hardening, rapid closures |
| **Hermes Agent** | 6 | 10 | None (v0.20.0) | 6.0/10 — security crisis mode, Windows breakage |
| **LobsterAI** | 1 | 34 | None (2026.4.1) | 7.5/10 — high PR throughput, low issue volume |
| **NanoClaw** | 3 | 20 | None | 7.0/10 — security/refactor sprint, responsive |
| **PicoClaw** | 4 | 9 | None (v0.3.1) | 7.5/10 — clean merge rate (7/9), responsive |
| **NullClaw** | 0 | 1 | None | 5.0/10 — quiet, single feature closure |
| **Moltis** | 3 | 2 | None | 5.5/10 — stagnant delivery, backend issues |
| **ZeptoClaw** | 0 | 0 | None | N/A — no activity |

*Health Score: composite of velocity, issue resolution rate, security posture, and release cadence.

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Largest community and contributor base** by an order of magnitude (500 issues/PRs vs. next-highest IronClaw at ~58 combined). This provides robust issue detection and rapid community-driven patches.
- **Most mature multi-channel support** — Telegram, Discord, Feishu, Slack with deep integration (rich messages, thread status, table rendering via community PRs).
- **Strongest plugin/MCP ecosystem signals** — memory trust tagging (#7707), per-agent cost budgeting (#42475), and sub-agent orchestration (#27445) indicate operator-grade maturity.

**Technical Approach Differences:**
- OpenClaw uses a **gateway-centric architecture** with durable session state and context engines, contrasting with NanoBot's agent-runtime model and NullClaw's A2A-protocol focus.
- **Session-state management is OpenClaw's crown jewel and its Achilles' heel** — the same architecture that enables long-running multi-source conversations also produces the ecosystem's most severe bugs (transcript livelock #115908, zombie leaks #97616).
- Unlike ZeroClaw's RFC-governed, security-first development culture, OpenClaw operates with a **high-velocity, community-triage model** (clawsweeper automation) that prioritizes throughput over deliberation.

**Community Size Comparison:**
- OpenClaw: ~500 daily interactions — largest by far
- IronClaw/CoPaw: ~30-50 daily — mid-tier active communities
- NanoBot/Hermes/NanoClaw: ~10-30 daily — focused contributor bases
- NullClaw/Moltis/ZeptoClaw: <5 daily — niche or dormancy

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|------------|------------------|----------------|
| **Message delivery reliability** | OpenClaw, IronClaw, NanoClaw, Hermes | Duplicate messages, silent failures, lost replies across Telegram/Discord/Matrix |
| **Session-state stability** | OpenClaw, Hermes, NanoBot | Livelocks, transcript corruption, long-uptime degradation |
| **OAuth/auth refresh resilience** | OpenClaw, NanoBot, IronClaw | Provider lockups on token expiry, Codex/Anthropic/OpenAI refresh failures |
| **MCP integration maturity** | NanoBot, NanoClaw, LobsterAI, CoPaw | Remote HTTP MCP servers, OAuth for SaaS MCP, SDK v2 migration |
| **Security hardening** | ZeroClaw, NanoBot, Hermes, PicoClaw, NanoClaw | Credential inheritance, path traversal, pairing-code predictability, env scrub bypasses |
| **Plugin/extension ecosystem** | OpenClaw, IronClaw, NanoBot, NanoClaw | Agent plugins 1.0, skill immutability, vendor-neutral package boundaries |
| **Memory system improvements** | OpenClaw, Hermes, CoPaw | Trust-tagged memory, per-agent attribution, reranker support, compaction triggers |
| **Multi-agent orchestration** | OpenClaw, NullClaw, ZeroClaw | A2A client tools, sub-agent routing, cross-instance communication |
| **Cost/token budget controls** | OpenClaw, NanoBot, CoPaw | Per-agent budgeting, idle-turn guardrails, sustained-goal token caps |
| **Production deployment readiness** | NanoClaw, Hermes, Moltis | systemd units, containerized deploys, health checks, self-healing gateways |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | IronClaw | NanoBot | Hermes Agent | ZeroClaw | CoPaw | PicoClaw | NullClaw | Moltis |
|-----------|----------|----------|---------|--------------|----------|-------|----------|----------|--------|
| **Primary Focus** | Multi-channel gateway | Channel delivery & pairing | Secure agent runtime | Desktop + CLI agent | Sandbox security | Console UI + memory | Lightweight edge assistant | A2A protocol | Container sandboxes |
| **Target User** | Power users, operators | Enterprise channel admins | Security-conscious individuals | Windows/Desktop users | Privacy-focused operators | Chinese-market users | Embedded/Raspberry Pi | Multi-agent builders | Apple Container users |
| **Architecture** | Gateway + context engine | Channel adapters + durable storage | Agent runtime + WebUI | Electron desktop + gateway | WASM sandbox + RFC governance | Tauri console + ReMe memory | Schema-v4 config + channels | A2A server/client | Go + Apple Container |
| **Language** | TypeScript | TypeScript | Python | Rust | Rust | Python | TypeScript | Rust | Go |
| **Release Cadence** | Beta/stable (5.x-7.x) | RC phase (1.1.x) | No recent release | v0.20.0 | Stalled (0.8.3) | v2.1.0b2 | v0.3.1 | No release | No release |
| **Security Posture** | Community-triage | RC hardening | Rapid security PRs | Credential-inheritance campaign | Audit-driven (S0/S1) | Provider compat focus | Remote-exec hardening | Protocol-level | Backend stability focus |
| **Key Differentiator** | Scale + multi-source | Channel depth + pairing | Security hardening speed | Windows desktop integration | RFC governance + sandbox | Memory + reranker | Edge/lightweight | A2A multi-agent | Container isolation |

---

## 6. Community Momentum & Maturity

### Tier 1: High-Velocity Iterators
- **OpenClaw** — 500/500 daily churn. Largest community but stability-stressed. In refinement cycle, not feature release.
- **IronClaw** — Active RC phase (v1.1.1-rc.1). Strong merge throughput (17 merged), new contributors emerging.
- **CoPaw** — 33/33 daily, pre-v2.1.0. Good velocity but critical bugs (SIGBUS, IME crash) need attention.
- **LobsterAI** — 34 PRs merged with only 1 new issue. Efficient pipeline, dependency modernization in progress.

### Tier 2: Focused Hardening
- **NanoBot** — 24 PRs, rapid security fixes (path traversal, OAuth, infinite-loop guard). Small but responsive team.
- **NanoClaw** — 20 PRs, security/refactor sprint. Responsive to operational feedback (systemd, pairing codes).
- **Hermes Agent** — 10 PRs, 6 issues closed. In crisis mode: Windows boot-loop + credential-inheritance campaign.

### Tier 3: Moderate/Stagnant
- **ZeroClaw** — 50/48 but dominated by open governance debates and a 7-issue security audit backlog with no fix PRs.
- **PicoClaw** — 9 PRs, 7 merged (78% merge rate). Clean and responsive but smaller community.
- **Moltis** — 2 PRs, 3 issues. Apple Container backend instability, build breaks, long-open feature PR (5 months).

### Tier 4: Dormant/Niche
- **NullClaw** — 1 issue closed, 1 stale dependabot PR. Quiet but stable A2A protocol focus.
- **ZeptoClaw** — Zero activity. Likely dormant or pre-release.

---

## 7. Trend Signals

### Signal 1: Security Hardening Is No Longer Optional
Every active project is investing in security — credential inheritance (Hermes), path traversal (NanoBot), pairing code predictability (NanoClaw), audit-driven S0 findings (ZeroClaw), remote-exec isolation (PicoClaw). **Value for developers:** Security is now a differentiator, not a checklist. Projects that ship with provenanced, auditable security postures will attract enterprise operators.

### Signal 2: The "Silent Failure" Crisis
Across OpenClaw (#121058), NanoClaw (#3226, #3223), Hermes (#83312), and IronClaw (#7473), the dominant user complaint is **indistinguishable failure modes** — messages lost, sessions wedged, errors swallowed. **Value for developers:** Observable failure is a competitive advantage. Projects that surface error context to users (rather than silent drops) will retain operators running unattended agents.

### Signal 3: MCP Is Becoming the Universal Integration Layer
NanoBot (SDK v2 migration), NanoClaw (remote HTTP MCP), LobsterAI (OpenClaw runtime fixes), and CoPaw (MCP tool parameter bugs) all converge on MCP maturity. **Value for developers:** MCP-compatible tool surfaces are now table stakes. Projects that support both stdio and streaming HTTP MCP will have broader ecosystem reach.

### Signal 4: Memory Systems Are Maturing Beyond Simple Storage
OpenClaw (trust-tagged memory #7707, write pipeline #42648), Hermes (credential-inheritance in memory ops #77164), CoPaw (ReMe reranker #6398), and ZeroClaw (per-agent knowledge graph attribution #9647) all treat memory as a first-class security and quality problem. **Value for developers:** Memory systems that support source-attribution, deduplication, and per-tenant isolation will enable the next wave of enterprise agent deployments.

### Signal 5: Multi-Agent Orchestration Is Emerging as a Separate Discipline
OpenClaw (sub-agent routing #27445), NullClaw (A2A client tools #700), ZeroClaw (cross-agent knowledge graphs #9647), and Hermes (multi-tenant isolation #34352) all signal that single-agent architectures are hitting ceiling. **Value for developers:** Projects that expose clean inter-agent communication primitives (A2A protocol, sub-agent lifecycle management) will capture the orchestration layer of the ecosystem.

### Signal 6: Production Readiness Gap
Multiple projects (NanoClaw lacking systemd, Hermes Windows boot-loop, Moltis build breaks, OpenClaw gateway cold-start regression) reveal that **development-mode tooling is colliding with production expectations**. **Value for developers:** Operational documentation, reference deployment templates, and self-healing capabilities are underserved gaps with high developer demand.

---

*Report generated from community digest data as of 2026-08-11. Source: GitHub repositories of 11 tracked projects.*

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-11

## 1. Today's Overview

NanoBot showed **high development velocity** today with 24 PRs updated and 4 issues touched within 24 hours. The project is in an active hardening phase: multiple security and correctness fixes landed, a significant refactoring wave touched the WebUI and agent runtime, and MCP integration received notable upgrades. No new release was published, suggesting the team is batching changes before a version bump. Overall project health is strong — active contributor engagement, rapid issue closure, and clear direction on key subsystems.

## 2. Releases

**None.** No new release was published today.

## 3. Project Progress

**Merged / Closed PRs today:**

- **#5316** — *feat(mcp): add browser OAuth for remote servers* — Added browser-based OAuth for Streamable HTTP and SSE MCP servers, with one-click presets for Xmind, Notion, and Linear. Directly addresses community demand (#5297).
- **#5325** — *fix(files): reject no-op edits* — Closes the infinite-loop bug in Dream memory consolidation when `edit_file` accepts identical old/new text. Regression tests added.
- **#5321** — *refactor(webui): make gateway own settings services* — Introduced a gateway-owned WebUI settings service with atomic read-modify-write operations; moved OAuth flow state into a gateway-scoped registry.
- **#5319** — *refactor(agent): replace reflective runtime state access* — Replaced `MyTool`'s reflective loop-state wrapper with an explicit `RuntimeControl` protocol and `AgentRuntimeControl` adapter, redacting credential-bearing fields.
- **#5318** — *refactor(webui): extract deterministic event projection helpers* — Made reasoning-completion time an explicit input; added shared live-event/replay fixtures for verification.
- **#5317** — *fix(webui): move mutations to authenticated WebSocket requests* — Security hardening: state-changing ops moved from unauthenticated GET/query calls to correlated request/reply frames on authenticated WebSocket connections.
- **#5315** — *fix(webui): improve UX recovery and empty states* — Preserved first prompt on failed workspace-scoped chat creation; reduced auth challenge to a localized password flow.
- **#5310** — *fix(weixin): honor forced QR login* — Forced Weixin login now performs a fully fresh QR flow across CLI and WebUI, skipping persisted credentials.
- **#5300** (issue) — MCP cancel-scope crash resolved via SDK upgrade path (related to PR #5179).
- **#5324** (issue) — Dream infinite-loop bug fixed via PR #5325.

## 4. Community Hot Topics

- **[Issue #5297](https://github.com/HKUDS/nanobot/issues/5297)** — *MCP OAuth web authorization* (3 comments, closed) — User requested OAuth support for MCP servers requiring web login (e.g., XMind). The community need here is clear: **MCP servers are expanding beyond local tools into SaaS platforms**, and users need seamless auth flows. This was addressed in PR #5316.
- **[Issue #5324](https://github.com/HKUDS/nanobot/issues/5324)** — *Dream memory consolidation infinite loop* (2 comments, closed) — A user reported 10M token burn in 23 minutes due to no-op edits looping. Highlights the need for **budget-guarded long-running agent tasks**. Fixed in PR #5325.
- **[PR #5329](https://github.com/HKUDS/nanobot/pull/5329)** — *Guard bare and named-user home paths in ExecTool* (P1 security fix) — Addresses a workspace-boundary bypass via unhandled tilde expansions (`~`, `~user`). Reflects ongoing security hardening momentum.
- **[PR #5257](https://github.com/HKUDS/nanobot/pull/5257)** — *Bound sustained-goal continuation on idle turns* (P2, open, conflicting) — Prevents token burn when a model repeatedly rephrases the same idle response. Important for cost control.
- **[PR #5179](https://github.com/HKUDS/nanobot/pull/5179)** — *Migrate MCP integration to SDK v2* (P1, open, conflicting) — Long-running migration effort to upgrade the MCP client from v1 to v2 SDK while preserving legacy SSE compatibility. Key infra work.

## 5. Bugs & Stability

| Severity | Item | Status | Fix PR |
|----------|------|--------|--------|
| **P0** | [#5327](https://github.com/HKUDS/nanobot/issues/5327) — Nanobot repeats the same message during reasoning | Open | None yet |
| **P1** | [#5300](https://github.com/HKUDS/nanobot/issues/5300) — MCP connection failure triggers anyio cancel-scope crash, CPU spike, task leak | Closed | Addressed in SDK v2 migration (#5179) |
| **P2** | [#5324](https://github.com/HKUDS/nanobot/issues/5324) — Dream memory consolidation infinite loop on no-op edits | Closed | [#5325](https://github.com/HKUDS/nanobot/pull/5325) ✅ |
| **P1** | [#5329](https://github.com/HKUDS/nanobot/pull/5329) — ExecTool path bypass via unhandled tilde expansions | Open | PR in progress |
| **P2** | [#5271](https://github.com/HKUDS/nanobot/pull/5271) — Stale background task overwrites session data on `/new` | Open | PR #5271 (open) |
| **P1** | [#5317](https://github.com/HKUDS/nanobot/pull/5317) — WebUI mutations via unauthenticated GET (resolved via merge) | Closed | [#5317](https://github.com/HKUDS/nanobot/pull/5317) ✅ |

**Notable:** The P0 repeat-message bug (#5327) remains open without a fix PR. The anyio cancel-scope crash (#5300) was a serious stability issue causing CPU spikes and process hangs; its resolution is tied to the MCP v2 migration.

## 6. Feature Requests & Roadmap Signals

- **MCP OAuth / SaaS integrations** — User demand for web-auth MCP servers (Xmind, Notion, Linear) is being actively addressed. Expect these presets and the OAuth flow to ship in the next release.
- **OrcaRouter provider** ([PR #5328](https://github.com/HKUDS/nanobot/pull/5328)) — New OpenAI-compatible routing gateway supporting 150+ models. Signals continued expansion of the **provider abstraction layer**.
- **Tabbed pane workbench** ([PR #5322](https://github.com/HKUDS/nanobot/pull/5322)) — Major WebUI restructuring: topics as tabs, multi-pane sessions, switchable layouts (grid, monocle, etc.). Indicates a **significant UX overhaul** is incoming.
- **Structured token usage records** ([PR #5299](https://github.com/HKUDS/nanobot/pull/5299)) — On-demand diagnostic API for token usage. Suggests the team is investing in **observability and cost transparency**.
- **Agent Plugins + CLI Apps** ([PR #5288](https://github.com/HKUDS/nanobot/pull/5288)) — Vendor-neutral package boundary for portable skills. Signals a move toward a **plugin ecosystem**.

## 7. User Feedback Summary

- **Pain point: Token waste from unbounded loops.** The Dream consolidation bug burned ~10M tokens (half a month's usage) in 23 minutes. Users are sensitive to runaway costs and need guardrails on sustained agent tasks.
- **Pain point: MCP auth is a friction point.** Multiple issues (#5297, #5300) point to users struggling with OAuth and remote MCP connections. The community wants plug-and-play SaaS integrations.
- **Pain point: Repetitive reasoning output.** Issue #5327 reports random message duplication during reasoning, degrading UX and wasting tokens.
- **Pain point: Workspace security boundaries.** PR #5329 shows users (or security-conscious adopters) are testing edge cases in path traversal, indicating a user base that values sandboxing.
- **Positive signal: Rapid issue resolution.** 3 of 4 issues closed within days; the team is responsive. The OAuth feature request was fulfilled within ~2 days of closing.

## 8. Backlog Watch

- **[PR #5179](https://github.com/HKUDS/nanobot/pull/5179)** — *Migrate MCP to SDK v2* — Open since July 30, P1, has conflicts. This is a **critical infrastructure migration** that unblocks OAuth and stability fixes. Needs maintainer attention to resolve conflicts.
- **[PR #5257](https://github.com/HKUDS/nanobot/pull/5257)** — *Bound sustained-goal continuation* — Open since Aug 5, P2, has conflicts. Addresses token burn on idle turns; important for cost control but blocked by conflicts.
- **[PR #5271](https://github.com/HKUDS/nanobot/pull/5271)** — *Prevent stale background task overwrites* — Open since Aug 6, P0. A session-safety bug with no merged fix yet.
- **[PR #5288](https://github.com/HKUDS/nanobot/pull/5288)** — *Agent Plugins with CLI Apps* — Open since Aug 7. Key ecosystem feature but may be deprioritized vs. hardening work.
- **[Issue #5327](https://github.com/HKUDS/nanobot/issues/5327)** — *Repeat message during reasoning* — Open P0 bug with no fix PR. Single comment so far; may need maintainer triage.
- **[PR #5322](https://github.com/HKUDS/nanobot/pull/5322)** — *Tabbed pane workbench* — Open, P2. Large UX feature that may require significant review before merge.
- **[PR #5299](https://github.com/HKUDS/nanobot/pull/5299)** — *Structured token usage records* — Open, no priority label. Useful but lower urgency.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-11

## 1. Today's Overview

Hermes Agent is in a period of **high-intensity security and stability remediation**. Today's activity is dominated by two parallel efforts: a **campaign-scoped conquest of child-process credential-inheritance vulnerabilities** (epic #83565, spawned from #77027) and a **Windows Desktop boot-loop crisis** triggered by the v0.20.0 update's `uv` trampoline venvs interacting badly with the parent-death watchdog. Both issues are hitting production users daily. In parallel, the project continues its 2026-08 policy of **sharding 20 god-files** into clean modules. No new releases were published today, but the merged/closed PR count (10 in 24h) and issue turnover (6 closed) indicate sustained developer momentum. Activity level: **high**, with critical security and platform-regression focus.

## 2. Releases

**No new releases today.** The project is currently on **v0.20.0 (2026-8.3, upstream a1bfbccc / 33f8e96a)**. Several issues reference the previous upstream commit `42708f8bb3` as the baseline for god-file line counts, suggesting v0.20.0 was released shortly before today.

## 3. Project Progress

### Merged/Closed Today (10 PRs, 6 Issues)

| Item | Type | Summary |
|------|------|---------|
| [PR #67626](https://github.com/NousResearch/hermes-agent/issues/67626) | Bugfix (merged) | Harden turn-lease idle-predicate against latent invariant gap in session state management |
| [PR #75063](https://github.com/NousResearch/hermes-agent/pull/75063) | Bugfix (merged) | Wake origin session on Kanban triage escalation — fixes silent-sleep bug on push platforms (Telegram) |
| [PR #82676](https://github.com/NousResearch/hermes-agent/pull/82676) | Test (merged) | Pin final-send suppression contract across a behaviour matrix, clarifying remaining exposure |
| [PR #83597](https://github.com/NousResearch/hermes-agent/pull/83597) | Feature (merged) | Pin GitHub branch & PR skill installs to immutable commits — adds `--ref`/`--pr` resolution to SHAs |
| [PR #81533](https://github.com/NousResearch/hermes-agent/pull/81533) | Bugfix (merged) | Attach renderer-lifecycle diagnostics to all `BrowserWindow` instances (fixes black secondary windows, #81290) |
| [PR #83567](https://github.com/NousResearch/hermes-agent/pull/83567) | Bugfix (merged) | Full renderer-lifecycle crash recovery for every Desktop window type (secondary, instance, HUD, quick-entry, overlay, wake, login) |
| [Issue #83603](https://github.com/NousResearch/hermes-agent/issues/83603) | Bug (closed) | Windows Desktop boot-loop after update — uv venv shim breaks parent-death watchdog (closed as duplicate of #83555/#83583) |
| [Issue #81547](https://github.com/NousResearch/hermes-agent/issues/81547) | Bug (closed) | Dashboard file-descriptor leak on macOS — `OSError: [Errno 24]` after several days of continuous operation |
| [Issue #77276](https://github.com/NousResearch/hermes-agent/issues/77276) | Bug (closed) | Desktop app restart left orphan gateway — app-managed spawn path was uncovered by #75936 |
| [Issue #83479](https://github.com/NousResearch/hermes-agent/issues/83479) | Feature (closed) | No obvious way to start a new session from Home section in desktop chat list — accepted as UX gap |

### Key Open PRs Advancing Today

- **[PR #83613](https://github.com/NousResearch/hermes-agent/pull/83613)** — *restore timestamped curator archives*: Makes skill restore round-trippable, directly addressing the unrecoverable-archive bug in #83580
- **[PR #83611](https://github.com/NousResearch/hermes-agent/pull/83611)** — *confirm parent death before serve watchdog self-reaps*: Fixes Windows boot-loop (#83555) by adding a confirmation step before the watchdog kills the backend
- **[PR #83604](https://github.com/NousResearch/hermes-agent/pull/83604)** — *Windows parent-death watchdog false-triggers due to ppid mismatch*: Complementary fix to #83611
- **[PR #83600](https://github.com/NousResearch/hermes-agent/pull/83600)** — *strip empty `tool_calls` at wire boundary*: Fixes DeepSeek v4 HTTP 400 session-wedge (#83312)
- **[PR #83523](https://github.com/NousResearch/hermes-agent/pull/83523)** — *stop 1M-context sessions from deferring compaction*: Lowers absolute trigger cap to 256K tokens
- **[PR #83504](https://github.com/NousResearch/hermes-agent/pull/83504)** — *Slack: let channel members initiate work without DM access*: Enables shared-channel agent use without DM authority
- **[PR #83271](https://github.com/NousResearch/hermes-agent/pull/83271)** — *fix mermaid diagram sizing in expand overlay*: Fixes blank dialog (#82836)
- **[PR #78356](https://github.com/NousResearch/hermes-agent/pull/78356)** — *upgrade memory-tencentdb plugin to v2.0.0*: Full MemoryCore v2 release with Python adapter

## 4. Community Hot Topics

| Issue/PR | Type | Comments | Analysis |
|----------|------|----------|----------|
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — *Epic: Shard all 20 god files* | Refactor | 66 | **Highest-discussion item in the repo.** The standing 2026-08 policy mandates all god-files be sharded. This epic coordinates the architectural cleanup of files like `mcp_tool.py` (7,230 loc), `conversation_loop.py` (7,306 loc), `api_server.py` (7,188 loc), and `hermes_cli/gateway.py` (7,461 loc). Community engagement is high because every shard PR touches maintainer review standards. |
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) — *Solving the Multi-Tenant Hermes Problem* | Feature | 21, 👍 2 | **Most upvoted open issue.** Memory operations bypass the hook system entirely, making tenant isolation impossible without forking core. The submitter reports months of production multi-tenant use with a custom fix. This signals a growing enterprise use-case that the core project has not yet addressed. |
| [#77463](https://github.com/NousResearch/hermes-agent/issues/77463) — *Child-env scrub bypasses (CRITICAL)* | Security | 2 | Documents 6 post-scrub env-update bypasses across TUI, LSP, Docker, and `_HERMES_FORCE_` paths. Rated **CRITICAL** by the author. Directly feeds the campaign epic #83565. |
| [#78642](https://github.com/NousResearch/hermes-agent/issues/78642) — *Shard `tools/mcp_tool.py`* | Refactor | 4 | First concrete shard in the epic, targeting the 7,230-line god-file. |
| [#83565](https://github.com/NousResearch/hermes-agent/issues/83565) — *Campaign EPIC: Child-process credential-inheritance conquest* | Security | 1 | **Newly opened today.** Anchors all open PRs/issues that fix the same class of bug (trusted parent secrets leaking to model-authored child processes). Signals a coordinated security sprint. |

## 5. Bugs & Stability

### Critical / P1

| Issue | Severity | Summary | Fix PR |
|-------|----------|---------|--------|
| [#83312](https://github.com/NousResearch/hermes-agent/issues/83312) | **P1** | DeepSeek v4 returns HTTP 400 on `tool_calls: []`, permanently wedging sessions | [PR #83600](https://github.com/NousResearch/hermes-agent/pull/83600) (open) |
| [#77463](https://github.com/NousResearch/hermes-agent/issues/77463) | **P2 (Critical severity)** | 6 child-env scrub bypass paths in TUI, LSP, Docker, `_HERMES_FORCE_` | [Issue #83565](https://github.com/NousResearch/hermes-agent/issues/83565) (campaign epic) |

### High / P2

| Issue | Summary | Fix PR |
|-------|---------|--------|
| [#83555](https://github.com/NousResearch/hermes-agent/issues/83555) | Windows Desktop: `serve` parent-death watchdog self-exits instantly on uv trampoline venvs — backend never becomes ready | [PR #83611](https://github.com/NousResearch/hermes-agent/pull/83611), [PR #83604](https://github.com/NousResearch/hermes-agent/pull/83604) |
| [#83583](https://github.com/NousResearch/hermes-agent/issues/83583) | Same Windows watchdog false-positive, different reporter | (duplicate of #83555) |
| [#83548](https://github.com/NousResearch/hermes-agent/issues/83548) | Hermes Desktop doesn't start after last update (crashes on boot) | (related to #83555) |
| [#82936](https://github.com/NousResearch/hermes-agent/issues/82936) | `multiplex_profiles: true` leaks default profile secrets into secondary profile subprocesses | Part of #83565 campaign |
| [#68367](https://github.com/NousResearch/hermes-agent/issues/68367) | Desktop-spawned profile inherits Tlon credentials from parent process env | Related to #83565 campaign |
| [#81518](https://github.com/NousResearch/hermes-agent/issues/81518) | Half-dead pooled connections behind transparent proxy cause cron API TTFB 20-219s | No fix yet |
| [#5908](https://github.com/NousResearch/hermes-agent/issues/5908) | kimi-coding credential pool `base_url` not re-resolved from key prefix on load (👍 2) | No fix yet |
| [#83580](https://github.com/NousResearch/hermes-agent/issues/83580) | `curator restore` rejects valid archived skills — 51 of 62 archived skills unrecoverable on one user's machine | [PR #83613](https://github.com/NousResearch/hermes-agent/pull/83613) (open) |
| [#83569](https://github.com/NousResearch/hermes-agent/issues/83569) | `hermes update` self-locks `cryptography._rust.pyd` on Windows — 100% failure rate when cryptography bumps | No fix yet |
| [#77164](https://github.com/NousResearch/hermes-agent/issues/77164) | Child-process env scrub is name-shape heuristic; non-credential-shaped secrets leak to children | Part of #83565 campaign |
| [#83573](https://github.com/NousResearch/hermes-agent/issues/83573) | `curator adopt --dry-run` reports "would adopt" for already-adopted skills | No fix yet |
| [#83565](https://github.com/NousResearch/hermes-agent/issues/83565) | Campaign EPIC for all credential-inheritance fixes | Coordinated |

### Medium / P3

| Issue | Summary |
|-------|---------|
| [#60961](https://github.com/NousResearch/hermes-agent/issues/60961) | Langfuse SDK plugin: placeholder API key causes silent failure (no traces emitted, no error) |
| [#83606](https://github.com/NousResearch/hermes-agent/pull/83606) | Desktop: merged tool-call turn painted twice, newer messages appear above older |
| [#83602](https://github.com/NousResearch/hermes-agent/pull/83602) | `hermes doctor` hints `npm audit fix` commands that ETARGET on min-release-age band |
| [#83522](https://github.com/NousResearch/hermes-agent/issues/83522) | Feature request: built-in gateway self-heal (SIGTERM restart + dead-WebSocket detection) |
| [#38079](https://github.com/NousResearch/hermes-agent/issues/38079) | fix(whatsapp): scrub operator environment from bridge subprocess (CVSS 6.8/8.2) |

## 6. Feature Requests & Roadmap Signals

| Item | Type | Signal |
|------|------|--------|
| [#34352](https://github.com/NousResearch/hermes-agent/issues/34352) — Multi-tenant isolation | Feature | **Strong signal.** Production users are running custom forks. Memory hook system needs architectural overhaul. Likely in next major roadmap. |
| [#83522](https://github.com/NousResearch/hermes-agent/issues/83522) — Gateway self-heal | Feature | **Medium signal.** Clean-SIGTERM restart + dead-WebSocket detection for Discord. Low-risk, high-availability value. |
| [PR #83504](https://github.com/NousResearch/hermes-agent/pull/83504) — Slack shared-channel initiation | Feature | **In progress.** Enables team-wide agent use without DM authority. Likely merges soon. |
| [PR #83597](https://github.com/NousResearch/hermes-agent/pull/83597) — Pin skill installs to commits | Feature | **Merged.** Adds immutability to GitHub-based skill installs. Future-proofing for reproducibility. |
| [#83479](https://github.com/NousResearch/hermes-agent/issues/83479) — New session from Home | Feature | **Accepted UX gap.** No button to start new session from Home section. Low priority but high user-facing impact. |
| [PR #66178](https://github.com/NousResearch/hermes-agent/pull/66178) — `hermes release-notes` command | Feature | **In progress.** Interactive release-notes viewer. Improves developer experience. |
| [#78647](https://github.com/NousResearch/hermes-agent/issues/78647) — God-file sharding | Architecture | **Ongoing.** All 20 god files targeted. This is the dominant architectural work for 2026-08. |
| [PR #78356](https://github.com/NousResearch/hermes-agent/pull/78356) — memory-tencentdb v2.0.0 | Feature | **In progress.** TencentDB memory plugin upgrade with full MemoryCore v2 support. |
| [PR #83523](https://github.com/NousResearch/hermes-agent/pull/83523) — 1M-context compaction trigger | Bugfix/Feature | **In progress.** Reduces absolute compaction cap to 256K tokens. Affects large-context model users. |

**Predicted for next version (v0.21.0):** Slack shared-channel auth (#83504), Gateway self-heal (#83522), Curator archive restore fix (#83613), DeepSeek empty-tool_calls fix (#83600), Windows watchdog fixes (#83611/#83604), and the first batch of god-file shards.

## 7. User Feedback Summary

**Pain points:**
- **Windows Desktop is broken after v0.20.0 update.** Multiple reporters confirm the app cannot boot — backend exits with code 0 before becoming ready. This is the single most-reported issue today (5+ linked issues/PRs). Users are frustrated by the boot loop and repair-reinstall cycle not helping (#83555, #83548, #83583, #83603).
- **Curator is unusable for archived skills.** One user reports 51 of 62 archived skills are irrecoverable via documented CLI paths (#83580). This directly impacts LLM-driven skill consolidation workflows.
- **DeepSeek v4 sessions are permanently broken** when the model returns `tool_calls: []` (#83312). No recovery path exists without manual session restart.
- **Multi-tenant isolation is impossible out of the box.** Enterprise users must fork core to achieve tenant isolation in memory operations

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-11

---

## 1. Today's Overview

PicoClaw showed robust activity on 2026-08-11, with **4 issues** and **9 PRs** updated in the last 24 hours. The project is in a active maintenance and hardening phase: security improvements, bug fixes, and feature completions were all merged today, while two open issues and two open PRs remain for community review. No new release was published this cycle. Overall health is positive — the merge rate (7/9 PRs closed) indicates a responsive maintainer team, and several high-impact bugs now have corresponding fix PRs.

---

## 2. Releases

**No new releases published.** The latest version referenced in issues remains **v0.3.1** (`2cf030d`).

---

## 3. Project Progress

### Merged / Closed PRs (7)

| PR | Title | Author | Summary |
|---|---|---|---|
| [#1547](https://github.com/sipeed/picoclaw/pull/1547) | fix: merge PR #1466 #1465 | xuwei-xy | Consolidated fixes from two earlier PRs |
| [#3297](https://github.com/sipeed/picoclaw/pull/3297) | fix(security): harden remote prompt and exec boundaries | SiYue-ZO | **Security hardening**: remote sender/chat metadata now isolated in a normalized user-role envelope; default remote exec disabled with per-call approval required; config migrated to schema v4 |
| [#3296](https://github.com/sipeed/picoclaw/pull/3296) | i18n: complete Czech code wrap labels | KrtCZ | Completed Czech translation for code-wrap UI labels |
| [#3295](https://github.com/sipeed/picoclaw/pull/3295) | fix(channels): prevent SplitMessage hang on oversized fence headers | ErzerLP | Fixed `SplitMessage` hanging when fenced-code info strings exceed `maxLen`; adds regression tests |
| [#3327](https://github.com/sipeed/picoclaw/pull/3327) | feat(telegram): render tables with native rich messages | As-tsaqib | **New feature**: Telegram tables now rendered with Bot API rich messages instead of monospaced code blocks; detects GFM tables and `<table>` HTML outside code fences |
| [#3326](https://github.com/sipeed/picoclaw/pull/3326) | fix(web): remove duplicate pnpm lock entries | As-tsaqib | Removed duplicate `semver@7.8.5` entries in `pnpm-lock.yaml` that broke `pnpm install --frozen-lockfile` |
| [#2132](https://github.com/sipeed/picoclaw/pull/2132) | feat(config): support model-specific max_tokens and fix config key coupling | dtapps | Decouples model lookup key from runtime ID; introduces granular per-model parameter overrides |

### Key Advancements
- **Security hardening** (PR #3297) significantly raises the bar for remote-exec safety — a notable shift toward production readiness.
- **Telegram table rendering** (PR #3327) improves UX for data-heavy agent responses on Telegram.
- **Config schema v4** migration (PR #2132, #3297) signals ongoing structural improvements to configuration management.

---

## 4. Community Hot Topics

| # | Type | Title | Author | Comments | Link |
|---|---|---|---|---|---|
| #3301 | Issue | `/clear` and session auto-compression don't work with non-default agent dispatch rules | j-v | 3 | [Issue #3301](https://github.com/sipeed/picoclaw/issues/3301) |
| #3298 | Issue | Add AI Router as an OpenAI-compatible provider preset | airouter-dev | 2 | [Issue #3298](https://github.com/sipeed/picoclaw/issues/3298) |
| #3294 | Issue | `/list models` only shows current model, not all configured models | 2suige-coder | 2 | [Issue #3294](https://github.com/sipeed/picoclaw/issues/3294) |
| #3311 | Issue | Repeated identical tool failure loops silently to `max_tool_iterations` | lucapette | 1 | [Issue #3311](https://github.com/sipeed/picoclaw/issues/3311) |
| #3314 | PR | Fix: agent not able to execute shell command added to `customAllowPatterns` | j-v | — | [PR #3314](https://github.com/sipeed/picoclaw/pull/3314) |
| #3312 | PR | fix(agent): stop turn early on repeated identical tool failure | lucapette | — | [PR #3312](https://github.com/sipeed/picoclaw/pull/3312) |

**Analysis:** The most active discussions cluster around **agent dispatch routing** and **tool-loop reliability** — both core UX pain points. Issue #3301 (dispatch + session management) and Issue #3311 (tool failure loops) suggest users are running PicoClaw in multi-agent, multi-channel configurations where these edge cases are actively encountered. The AI Router integration request (#3298) reflects growing interest in provider-agnostic routing ecosystems.

---

## 5. Bugs & Stability

### Critical / High Severity

| # | Title | Author | Status | Fix PR | Link |
|---|---|---|---|---|---|
| #3311 | Repeated identical tool failure loops silently to `max_tool_iterations` — user never gets an answer | lucapette | OPEN | [#3312](https://github.com/sipeed/picoclaw/pull/3312) ✅ exists | [Issue #3311](https://github.com/sipeed/picoclaw/issues/3311) |
| #3301 | `/clear` and session auto-compression broken for non-default agent dispatch | j-v | OPEN | — | [Issue #3301](https://github.com/sipeed/picoclaw/issues/3301) |

### Medium Severity

| # | Title | Author | Status | Fix PR | Link |
|---|---|---|---|---|---|
| #3294 | `/list models` only shows current model | 2suige-coder | CLOSED | — | [Issue #3294](https://github.com/sipeed/picoclaw/issues/3294) |
| #3314 | Agent cannot execute shell commands in `customAllowPatterns` | j-v | OPEN | [#3314](https://github.com/sipeed/picoclaw/pull/3314) ✅ exists | [PR #3314](https://github.com/sipeed/picoclaw/pull/3314) |

**Notes:**
- **Bug #3311** is the most impactful open issue: users on Telegram report the agent going silent for minutes, never responding. Fix PR #3312 has been submitted and should terminate the loop early.
- **Bug #3294** is marked closed — likely fixed or deferred; no fix PR is linked.
- **Bug #3301** (dispatch + session management) has no fix PR yet and affects multi-agent deployments.
- PR #3295 resolved a `SplitMessage` hang regression, and PR #3326 fixed a broken `pnpm install` due to lockfile duplicates — both are stability improvements with user impact.

---

## 6. Feature Requests & Roadmap Signals

| # | Title | Author | Status | Link |
|---|---|---|---|---|
| #3298 | Add AI Router as an OpenAI-compatible provider preset | airouter-dev | CLOSED | [Issue #3298](https://github.com/sipeed/picoclaw/issues/3298) |

**Analysis:**
- The **AI Router preset** request (#3298) was closed, suggesting either it was addressed (e.g., accepted as a generic provider) or deferred. Given the author's affiliation disclosure and the generic `openai` provider workaround already available, the maintainer likely deemed a dedicated preset unnecessary — but it signals user demand for first-class multi-router support.
- **Model-specific `max_tokens`** (PR #2132, now merged) was a long-standing feature request that is now live — expect per-model tuning to be documented in the next release notes.
- **Telegram table rendering** (PR #3327, merged) was a community-driven UX enhancement; similar rich-format features for other channels may follow.

**Predicted next-version features:** Dispatch-rule-aware session management, AI Router integration, and expanded channel-rich-content rendering (tables in Discord, Slack, etc.).

---

## 7. User Feedback Summary

| Theme | Source | Sentiment |
|---|---|---|
| Multi-agent dispatch breaks basic session commands (`/clear`, auto-compression) | #3301 | ⚠️ Frustrated — core workflow broken for routed chats |
| Tool failure loops cause silent hangs; user receives no response | #3311 | ⚠️ High dissatisfaction — production-impacting on Telegram |
| `/list models` misleadingly shows only current model | #3294 | 😐 Mild annoyance — expectation vs. reality mismatch |
| `customAllowPatterns` doesn't override default deny patterns | #3314 | ⚠️ Security-config gap — users can't grant exceptions |
| AI Router deserves first-class preset support | #3298 | ✅ Positive engagement — provider-agnostic routing demand |
| Telegram tables rendered as code blocks are ugly | (PR #3327) | ✅ Appreciation — rich-format improvement well-received |
| `pnpm install` broken by duplicate lockfile entries | (PR #3326) | 😐 Infrastructure friction — non-user-facing but affects contributors |

**Overall:** Users are actively running PicoClaw in production (Raspberry Pi, Telegram, Discord) and hitting edge cases around multi-agent routing, tool safety, and session management. The tone is constructive — bug reports include repro steps and environment details. The security hardening PR (#3297) aligns well with the maturing user base.

---

## 8. Backlog Watch

| # | Type | Title | Author | Created | Days Open | Link |
|---|---|---|---|---|---|---|
| #3301 | Issue | `/clear` and session auto-compression broken with non-default agent dispatch | j-v | 2026-07-29 | 13 | [Issue #3301](https://github.com/sipeed/picoclaw/issues/3301) |
| #3314 | PR | Agent cannot execute shell commands in `customAllowPatterns` | j-v | 2026-08-03 | 8 | [PR #3314](https://github.com/sipeed/picoclaw/pull/3314) |
| #3311 | Issue | Tool failure loops silently to `max_tool_iterations` | lucapette | 2026-08-02 | 9 | [Issue #3311](https://github.com/sipeed/picoclaw/issues/3311) |
| #3312 | PR | Fix: stop turn early on repeated identical tool failure | lucapette | 2026-08-02 | 9 | [PR #3312](https://github.com/sipeed/picoclaw/pull/3312) |

**Maintainer Attention Needed:**
1. **PR #3312** (tool failure loop fix) and **PR #3314** (custom allow patterns) are both open and unmerged — they address high-impact production bugs and should be prioritized.
2. **Issue #3301** (dispatch + session) has no fix PR and is the most complex open issue; it affects multi-agent setups and deserves a repro case review.
3. Consider reviewing **Issue #3298** (AI Router preset) — while closed, the underlying need for provider abstraction is valid and may warrant a roadmap item.

---

*Digest generated from GitHub data as of 2026-08-11. Source: [sipeed/picoclaw](https://github.com/sipeed/picoclaw)*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-11

## 1. Today's Overview

NanoClaw showed robust development activity on 2026-08-10 with 20 PRs updated (10 open, 10 merged/closed) and 3 open issues actively discussed. No new releases were published, but the project is clearly in a heavy refactoring and hardening sprint: security fixes for Telegram pairing, deduplication logic for inbound messages, host filesystem access simplification, and module lifecycle unification all landed or are in review today. The issue backlog centers on operational reliability (silent failures, long-uptime stability) rather than feature gaps, suggesting the project is maturing past its initial launch phase. Overall project health is **strong** — high PR throughput with mostly security and correctness work.

## 2. Releases

**None.** The latest referenced commit is `2d9375531b1e52574b6b61861c4153b26f2ae68a` (2026-06-06). No new version tag was published in the reporting window.

## 3. Project Progress

**Merged/Closed PRs (6):**

| PR | Title | Impact |
|----|-------|--------|
| [#3216](https://github.com/nanocoai/nanoclaw/pull/3216) | `docs(hardened-image): note that install_packages covers apt and npm only` | Clarifies a documentation gap in the hardened-image guide |
| [#3228](https://github.com/nanocoai/nanoclaw/pull/3228) | `fix: deduplicate turn-scoped chat delivery` | Prevents duplicate message delivery within a single agent turn |
| [#3222](https://github.com/nanocoai/nanoclaw/pull/3222) | `feat(permissions): add opt-in privacy-safe DM logs` | Adds `privacySafeLogs` option to omit PII from DM resolution logs |
| [#3218](https://github.com/nanocoai/nanoclaw/pull/3218) | `feat(cli): accept bounded JSON from stdin` | Introduces `--stdin-json` for structured input to `ncl` commands |
| [#3215](https://github.com/nanocoai/nanoclaw/pull/3215) | `fix(permissions): redact DM resolution logs` | Redacts sensitive identifiers in DM resolution logging |
| [#3219](https://github.com/nanocoai/nanoclaw/pull/3219) | `Telegram and container env` | Community contribution on Telegram/container environment setup |

**Key Open PRs Advancing Today:**
- **#3227** — Refactors host file-surface declaration to explicit single-writer model ([#3227](https://github.com/nanocoai/nanoclaw/pull/3227))
- **#3229** — Hardens Telegram pairing code generation using CSPRNG ([#3229](https://github.com/nanocoai/nanoclaw/pull/3229))
- **#3224** — Fixes inbound message loss on platform ID reuse ([#3224](https://github.com/nanocoai/nanoclaw/pull/3224))
- **#3225** — Complements #3229 by hardening pairing directory/file permissions ([#3225](https://github.com/nanocoai/nanoclaw/pull/3225))
- **#3092 / #3221** — Remote Streamable HTTP MCP server support for codex and opencode providers ([#3092](https://github.com/nanocoai/nanoclaw/pull/3092), [#3221](https://github.com/nanocoai/nanoclaw/pull/3221))
- **#3220 / #2909** — Agent templates evolve into Agent Plugins 1.0.0 directories with wizard setup flow ([#3220](https://github.com/nanocoai/nanoclaw/pull/3220), [#2909](https://github.com/nanocoai/nanoclaw/pull/2909))

## 4. Community Hot Topics

**Most Discussed Issues:**

1. **[Issue #3075](https://github.com/nanocoai/nanoclaw/issues/3075)** — *Silent log loss + inbound message duplicate-insert errors after long uptime; no systemd unit installed*
   - Active concern from a WSL2/Docker Desktop operator on Matrix. Two distinct failure modes reported: log rot/silence after extended uptime and duplicate-insert collisions. No systemd unit is shipped, making production deployment difficult. 1 comment, created ~24 days ago — **needs maintainer attention.**

2. **[Issue #3226](https://github.com/nanocoai/nanoclaw/issues/3226)** — *Inbound messages silently dropped when a platform reuses a message ID*
   - Opened today by the same author as fix PR #3224. Root cause identified: platforms that recycle message IDs cause primary-key insert failures, and the error is silently swallowed. User-visible symptom: "the agent ignored me." **Directly addressed by [#3224](https://github.com/nanocoai/nanoclaw/pull/3224).**

3. **[Issue #3223](https://github.com/nanocoai/nanoclaw/issues/3223)** — *Scheduled-task errors produce unroutable error messages that are silently dropped*
   - Opened today. Task-triggered agent turns that error out produce messages with no routing fields, making the error unrouteable and invisible to operators. This reveals a deeper architectural gap in how the agent-runner handles errors from the scheduled-task subsystem.

**Underlying Need:** Operators running NanoClaw at scale are hitting reliability walls — silent failures, missing observability, and no production deployment templates (systemd). The project is responsive (PRs #3224, #3229, #3225 landed same day), but these issues point to a gap between "works on my machine" and "runs unattended for weeks."

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| 🔴 High | [#3226](https://github.com/nanocoai/nanoclaw/issues/3226) | Inbound messages silently dropped on platform message-ID reuse | [#3224](https://github.com/nanocoai/nanoclaw/pull/3224) [OPEN] |
| 🟠 Medium | [#3075](https://github.com/nanocoai/nanoclaw/issues/3075) | Silent log loss + duplicate-insert errors after long uptime; no systemd unit | — |
| 🟠 Medium | [#3223](https://github.com/nanocoai/nanoclaw/issues/3223) | Scheduled-task errors are unroutable and silently dropped | — |
| 🟡 Low | — | Telegram pairing codes generated with `Math.random()` (predictable) | [#3229](https://github.com/nanocoai/nanoclaw/pull/3229) [OPEN], [#3225](https://github.com/nanocoai/nanoclaw/pull/3225) [OPEN] |

**Regression risk:** The deduplication fix in #3228 (merged) and the inbound-message preservation in #3224 (open) touch overlapping areas of the message-routing pipeline. Coordination between these PRs should be verified to avoid introducing new edge cases.

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Assessment |
|--------|--------|------------|
| **Remote Streamable HTTP MCP servers** | [#3092](https://github.com/nanocoai/nanoclaw/pull/3092) (open), [#3221](https://github.com/nanocoai/nanoclaw/pull/3221) (open) | Strong roadmap commitment. codex and opencode providers need HTTP MCP support beyond stdio-only. Likely to ship in next feature release. |
| **Agent Plugins 1.0.0** | [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) (open), [#2909](https://github.com/nanocoai/nanoclaw/pull/2909) (open) | Major format migration from "templates" to plugin directories with wizard-driven setup. This is a breaking engine change — will define the next major version. |
| **Privacy-safe DM logs** | [#3222](https://github.com/nanocoai/nanoclaw/pull/3222) [CLOSED], [#3215](https://github.com/nanocoai/nanoclaw/pull/3215) [CLOSED] | Merged. Suggests growing demand for compliance-oriented logging, likely driven by enterprise operators. |
| **Bounded JSON stdin input** | [#3218](https://github.com/nanocoai/nanoclaw/pull/3218) [CLOSED] | Merged. Enables scripted/CI usage patterns — signals expanding automation surface. |
| **Systemd unit / production deployment support** | [#3075](https://github.com/nanocoai/nanoclaw/issues/3075) | Not yet addressed. Repeated operator need; likely candidate for next operational release. |

## 7. User Feedback Summary

- **"The agent ignored me"** ([#3226](https://github.com/nanocoai/nanoclaw/issues/3226)) — Users cannot distinguish between a dropped message and an intentional no-response, creating frustration with no diagnostic path.
- **Long-uptime instability** ([#3075](https://github.com/nanocoai/nanoclaw/issues/3075)) — Operators running NanoClaw 24/7 in WSL2/Docker report silent log loss and database insert collisions, suggesting the project is being tested in production-like conditions beyond its current design assumptions.
- **No systemd unit** ([#3075](https://github.com/nanocoai/nanoclaw/issues/3075)) — Deployment on Linux servers is manual and ad-hoc; users expect a reference unit file.
- **Predictable pairing codes** ([#3229](https://github.com/nanocoai/nanoclaw/pull/3229)) — Security-conscious users flagged that `Math.random()` produces guessable Telegram pairing codes, a real vulnerability for unattended device pairing.
- **Overall sentiment** — Users are engaged and reporting high-quality, actionable bugs. The project is being used in production deployments (Matrix, Telegram, Docker, WSL2) which surfaces real operational pain points. No expressions of dissatisfaction with the project direction; concerns are purely about reliability and observability gaps.

## 8. Backlog Watch

| Item | Age | Risk | Notes |
|------|-----|------|-------|
| [#3075](https://github.com/nanocoai/nanoclaw/issues/3075) — Long-uptime log loss & missing systemd unit | ~25 days | Medium-High | Two operational problems in one issue. No fix PR yet. Author is actively maintaining a fork — risk of divergence if unresolved. |
| [#3223](https://github.com/nanocoai/nanoclaw/issues/3223) — Scheduled-task error silence | Same day | Medium | Architectural gap in error routing. No fix PR yet; requires design discussion before implementation. |
| [#3092](https://github.com/nanocoai/nanoclaw/pull/3092) — Remote Streamable HTTP MCP servers | ~22 days | Low | Still open; depends on [#3221](https://github.com/nanocoai/nanoclaw/pull/3221) for codex/opencode payload fixes. Feature is clearly desired. |
| [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) — Agent Templates → Plugins 1.0.0 | Same day | Low | Breaking change PR just opened. Will need careful review and migration guide. |

**Summary:** The two most critical backlog items are [#3075](https://github.com/nanocoai/nanoclaw/issues/3075) (operational readiness) and [#3223](https://github.com/nanocoai/nanoclaw/issues/3223) (error observability). Both involve silent failures — a pattern that deserves a dedicated stability initiative. The project team is clearly moving fast on security and correctness fixes; ensuring these operational issues don't fall further behind should be a priority.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>



# NullClaw Project Digest — 2026-08-11

## 1. Today's Overview

NullClaw showed low but focused activity over the past 24 hours. One issue was closed and one open PR remains under review, with no new releases published. The project continues to evolve steadily around its A2A protocol implementation, with community contributions driving both feature expansion and infrastructure hygiene. Overall project health appears stable, with maintainers actively closing resolved issues and Dependabot keeping dependencies current.

## 2. Releases

No new releases were published in the last 24 hours.

---

## 3. Project Progress

**Closed Issue (likely resolved/merged):**
- **#700** — *Add a2a_call client tool for calling remote agents* ([Link](https://github.com/nullclaw/nullclaw/issues/700))
  - Author: georgeglarson | Closed: 2026-08-10 | 👍 1
  - This issue, originally opened on 2026-03-23, was closed today after roughly four months. The author built an `a2a_call` client tool enabling nullclaw to send `message/send` JSON-RPC requests to remote A2A agents. Its closure suggests the feature was accepted and merged, filling a notable gap in nullclaw's client-side A2A capabilities.

**Open PR (pending):**
- **#956** — *ci(deps): bump alpine from 3.23 to 3.24 in the docker-images group* ([Link](https://github.com/nullclaw/nullclaw/pull/956))
  - Author: dependabot[bot] | Open since 2026-06-15 | Updated: 2026-08-10
  - A routine dependency update with no feature or bug-fix impact. Still open, awaiting merge.

---

## 4. Community Hot Topics

**Most Discussed / Reacted Item:**
- **Issue #700** — *Add a2a_call client tool* ([Link](https://github.com/nullclaw/nullclaw/issues/700))
  - 1 comment, 1 👍 — Closed today after a long lifecycle.
  - **Analysis:** The community clearly needed a client-side A2A implementation to complement nullclaw's existing server-side protocol support. The author's real-world use case—running dual nullclaw instances (a public doorman and a private personal agent)—highlights a growing demand for multi-agent orchestration and cross-instance communication. This signals that users are pushing nullclaw beyond single-agent personal assistant scenarios toward coordinated agent networks.

---

## 5. Bugs & Stability

No bug reports, crashes, or regressions were filed or resolved in the last 24 hours. The only closed item (#700) was a feature request, not a defect. The project's stability posture appears calm.

---

## 6. Feature Requests & Roadmap Signals

- **A2A Client-Side Tools** — Issue #700's resolution strongly signals that client-side A2A protocol support is a priority. Future versions will likely include additional A2A client tools (e.g., agent discovery, task submission, result polling) beyond the initial `a2a_call` implementation.
- **Multi-Agent Orchestration** — The use case described in #700 (public-facing doorman + private personal agent) points to a roadmap direction toward multi-agent systems and inter-agent communication patterns.

---

## 7. User Feedback Summary

- **Satisfaction Signal:** The 👍 reaction on #700 and its eventual closure indicate the community values client-side A2A capabilities. The author's detailed use case description reflects genuine, production-grade need rather than theoretical interest.
- **Pain Point Addressed:** Prior to #700's resolution, nullclaw users could serve the A2A protocol but had no built-in way to call remote agents—a significant limitation for anyone building multi-agent workflows. This gap is now closed.
- **No Dissatisfaction Indicators:** No negative feedback or complaints surfaced in the current window.

---

## 8. Backlog Watch

- **PR #956** — *Bump alpine from 3.23 to 3.24* ([Link](https://github.com/nullclaw/nullclaw/pull/956))
  - Open since 2026-06-15 (over 2 months). While low-risk, the extended wait time is worth monitoring, as stale Docker base images can introduce security and compatibility drift.

- **Long-Lived Feature Request #700** — Now closed, but its four-month lifecycle from creation to resolution may indicate slower-than-desired turnaround on community-contributed features. Maintainers should watch for similar feature requests to avoid prolonged stagnation.

---

*Digest generated from GitHub data for nullclaw/nullclaw on 2026-08-11.*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-11

## 1. Today's Overview

IronClaw is in an active release-candidate phase for the 1.1.x line, with **50 issues and 50 PRs updated in the last 24 hours** (25 open/active issues, 33 open PRs). A new release candidate, `v1.1.1-rc.1`, shipped yesterday (2026-08-10) focusing on channel delivery, pairing, IronHub/MCP compatibility, WebUI streaming stability, and safe upgrade paths. The project shows strong contributor momentum, including new contributors (theredspoon, zmanian) and core-team parallel work streams spanning architecture audits, channel unification, and durable storage fixes. Overall health is **good** — high PR merge throughput (17 merged/closed) alongside an equally active issue-closing cadence suggests a responsive maintenance rhythm.

---

## 2. Releases

### `ironclaw-v1.1.1-rc.1` — 2026-08-10

**Focus areas:**
- Channel delivery and pairing hardening
- IronHub / custom MCP compatibility
- WebUI streaming stability improvements
- Durable retrieval fixes
- Safe upgrade paths from both supported stable predecessors (1.0.x and 1.1.x)

**Breaking / migration notes:** Upgrading from `1.0.0` requires stopping all writers before installing. No other migration steps documented in the release notes.

---

## 3. Project Progress

### Merged / Closed PRs (last 24h)
- **#7381** [CLOSED] `docs(internal): doc-truth pipeline design record` — completes the doc-truth verification pipeline as proposed in issue #7317.
- **#7336** [CLOSED] `fix(loop-host): dedup consumed steering replays` — prevents duplicate assistant replies from delayed queued-message replays.

### Open PRs Advancing Key Features
| PR | Title | Author | Size / Risk |
|---|---|---|---|
| [#7477](https://github.com/nearai/ironclaw/pull/7477) | Unified channel model — one `ChannelAdapter` per channel | BenKurrek | XL / medium |
| [#7456](https://github.com/nearai/ironclaw/pull/7456) | Make durable storage profile-agnostic | henrypark133 | XL / medium |
| [#7464](https://github.com/nearai/ironclaw/pull/7464) | Telegram linked-device auth & session custody | BenKurrek | XL / low |
| [#7410](https://github.com/nearai/ironclaw/pull/7410) | Complete fair tool-search discovery & benchmark arms | serrrfirat | XL / low |
| [#7426](https://github.com/nearai/ironclaw/pull/7426) | Add durable memory parity matrix (stress tests) | serrrfirat | XL / medium |
| [#7469](https://github.com/nearai/ironclaw/pull/7469) | Reduce captured logprobs to envelope confidence aggregates | zmanian | XL / low |
| [#7471](https://github.com/nearai/ironclaw/pull/7471) | Lease expiry recovers safe runs instead of failing them | serrrfirat | XL / low |

---

## 4. Community Hot Topics

| Issue/PR | Title | Comments | Author | Link |
|---|---|---|---|---|
| **#7137** [OPEN] | live-canary: shard artifacts are 700MB–1.5GB; exclude regenerable paths | 12 | serrrfirat | [Issue](https://github.com/nearai/ironclaw/issues/7137) |
| **#7145** [CLOSED] | WS2: finish extension_host → loops re-layer | 4 | BenKurrek | [Issue](https://github.com/nearai/ironclaw/issues/7145) |
| **#7317** [CLOSED] | Proposal: Doc-Truth Verification Pipeline | 3 | cuongdcdev | [Issue](https://github.com/nearai/ironclaw/issues/7317) |
| **#6257** [OPEN] | "Invalid value (attachments.mime_type)" error on PDF | 3 | sergeiest | [Issue](https://github.com/nearai/ironclaw/issues/6257) |
| **#7147** [CLOSED] | Two shrink-only architecture ratchets carry untracked slack | 3 | BenKurrek | [Issue](https://github.com/nearai/ironclaw/issues/7147) |
| **#5882** [CLOSED] | Repeated Slack reconnect leaves auth flow broken | 3 | joe-rlo | [Issue](https://github.com/nearai/ironclaw/issues/5882) |

**Analysis:**
- **#7137** (12 comments) is the most-discussed open issue — CI artifact bloat is a recurring pain point that directly impacts developer experience and GitHub Actions costs. A fix PR (#7466) has been committed.
- **#7317** (now closed) reflects a real user demand for documentation that stays in sync with code — the doc-truth pipeline is now implemented (#7381).
- **#6257** and **#5882** both center on **channel integration reliability** (PDF attachments, Slack auth), signaling that channel stability is a top user concern.

---

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR |
|---|---|---|---|
| **High** | [#7473](https://github.com/nearai/ironclaw/issues/7473) | `post_notice → release_connect_nudge` collapses "delivered with no vendor ref" into "not delivered", allowing duplicate connect nudges | [#7475](https://github.com/nearai/ironclaw/pull/7475) (open) |
| **High** | [#7476](https://github.com/nearai/ironclaw/issues/7476) | `classify_delivery_outcome` ignores `Failed`'s `vendor_message_refs`, hiding partial-send evidence from the model | — |
| **Medium** | [#6257](https://github.com/nearai/ironclaw/issues/6257) | `Invalid value (attachments.mime_type)` when sending/generating PDFs | — |
| **Medium** | [#5882](https://github.com/nearai/ironclaw/issues/5882) | Repeated Slack reconnects leave auth flow in broken state; requires reinstall | — |
| **Low** | [#7470](https://github.com/nearai/ironclaw/pull/7470) | Thread listability broken for unprojected `thread_index` rows | [#7470](https://github.com/nearai/ironclaw/pull/7470) (open) |
| **Low** | [#7431] | `cwd` overlapping skill roots causes workspace resolution failures | [#7455](https://github.com/nearai/ironclaw/pull/7455) (open) |

**Notable:** Two high-severity delivery-path bugs (#7473, #7476) were opened today by theredspoon, both related to how the system handles vendor message references in notice delivery. PR #7475 addresses #7473. The #7476 gap (ignoring `vendor_message_refs` on failure) still needs a fix PR.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Title | Est. Target | Link |
|---|---|---|---|
| **#7354** [OPEN] | Extensions vNext: Web Push, Rich Messaging, Telegram User Sessions, Signal | v1.3.0 | [Issue](https://github.com/nearai/ironclaw/issues/7354) |
| **#7038** [OPEN] | Storybook + AI-first Design System (theming, assets, interactions, IA) | v1.3.0 | [Issue](https://github.com/nearai/ironclaw/issues/7038) |
| **#7046** [OPEN] | Configure all tools, channels, extensions from AI chat as Admin | — | [Issue](https://github.com/nearai/ironclaw/issues/7046) |
| **#7467** [OPEN] | Make Reborn durable state profile-agnostic | Near-term | [Issue](https://github.com/nearai/ironclaw/issues/7467) |
| **#3762** [OPEN] | Editing `AGENTS.md` in WebUI doesn't update system prompt | v1.3.0 | [Issue](https://github.com/nearai/ironclaw/issues/3762) |

**Signals:**
- **Telegram linked-device support** (PR #7464) is actively in flight and maps directly to the #7354 epic — expect it in v1.1.1 or v1.2.0.
- **Profile-agnostic durable storage** (#7467 / PR #7456) is a near-term priority; a fix PR is already open.
- **AI-admin configuration** (#7046) and the **Design System** (#7038) are both scoped for v1.3.0, indicating a longer-horizon roadmap focused on UX consolidation.
- The **doc-truth pipeline** (#7317 → #7381) is now complete, suggesting future feature proposals will face stricter documentation audits.

---

## 7. User Feedback Summary

| Theme | Source | Sentiment |
|---|---|---|
| **PDF/attachment MIME type errors** | #6257 (Slack reporter: Michael Kelly) | Frustrated — blocks a basic file-sharing workflow |
| **Slack auth broken after reconnects** | #5882, #6834 | High pain — requires full extension reinstall; no in-UI recovery |
| **AGENTS.md edits not reflected in conversations** | #3762 | Confusion — save appears successful but has no effect |
| **Duplicate connect-nudges** | #7473 | Annoyance — user receives repeated "please connect" messages |
| **Custom MCP server support** | #6727 (closed) | Historically requested; now shipped in v1.1.0 |
| **Channel completeness (Telegram)** | #6483 (closed) | Satisfied — Telegram is now a complete channel per the epic outcome |

**Overall:** Channel integration reliability (Slack, Telegram, attachments) is the dominant pain cluster. Users value the directional progress on Telegram completeness but are frustrated by auth fragility and PDF handling in Slack.

---

## 8. Backlog Watch

| Issue | Title | Age | Risk | Link |
|---|---|---|---|---|
| **#3762** | Editing `AGENTS.md` in WebUI does not update system prompt | ~3 months | Medium — UX-critical, flagged P1 | [Issue](https://github.com/nearai/ironclaw/issues/3762) |
| **#5882** | Repeated Slack reconnect leaves auth flow broken | ~1 month | High — no recovery path for users | [Issue](https://github.com/nearai/ironclaw/issues/5882) |
| **#6257** | `Invalid value (attachments.mime_type)` on PDF | ~3 weeks | Medium — blocks file workflows | [Issue](https://github.com/nearai/ironclaw/issues/6257) |
| **#7137** | live-canary shard artifacts 700MB–1.5GB | ~7 days | Low-Medium — CI cost & triage impact; fix PR committed (#7466) | [Issue](https://github.com/nearai/ironclaw/issues/7137) |
| **#7476** | `classify_delivery_outcome` ignores failure vendor refs | New (today) | High — hides partial-send evidence | [Issue](https://github.com/nearai/ironclaw/issues/7476) |

**Maintainer attention needed:**
- **#5882** and **#6257** have no open fix PRs and represent recurring user-facing pain in channel integrations — good candidates for the next patch cycle.
- **#7476** is a new high-severity bug with no fix yet; should be triaged alongside #7475 (which addresses its sibling #7473).
- **#3762** has been open since May and is tagged P1 — still awaiting a fix PR.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-11

## 1. Today's Overview

LobsterAI shows **active development momentum** with 34 PRs updated in the last 24 hours (14 open, 20 merged/closed), while issue activity remains low at just 1 closed bug report. The project is currently between releases with no new version published. Primary effort is concentrated on the **Cowork** collaboration feature, OpenClaw runtime stability, and a broad **dependency upgrade sweep** (Vite 5→8, React DOM 18→19, Mermaid, ESLint plugins). Overall health is positive — high PR throughput with no blocking bugs reported today.

## 2. Releases

**None.** No new releases were published in the last 24 hours. The most recent referenced version remains **2026.4.1**.

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Area | Summary |
|---|---|---|
| [#2472](https://github.com/netease-youdao/LobsterAI/issues/2472) | Cowork | Activity group collapse — UI organization improvement |
| [#2471](https://github.com/netease-youdao/LobsterAI/issues/2471) | Cowork | Render submitted file attachments as clickable cards instead of raw text paths |
| [#2454](https://github.com/netease-youdao/LobsterAI/issues/2454) | OpenClaw | Fix tool-loop guard incorrectly terminating legitimate polling cycles |
| [#2467](https://github.com/netease-youdao/LobsterAI/issues/2467) | Windows / Python Runtime | Repair stale pip shims on Windows runtime upgrade — health checks now verify shim integrity, not just file existence |
| [#2466](https://github.com/netease-youdao/LobsterAI/issues/2466) | Renderer | Fix IPC stall retry on renderer initialization |
| [#2470](https://github.com/netease-youdao/LobsterAI/issues/2470) | OpenClaw | Surface provider runtime failures on late chat errors instead of swallowing them as stale notices |
| [#2469](https://github.com/netease-youdao/LobsterAI/issues/2469) | Cowork | Add collapse-agent-tasks shortcut; allow modifier shortcuts while typing |
| [#2468](https://github.com/netease-youdao/LobsterAI/issues/2468) | Cowork | Unify streaming loading indicators into a single component |
| [#1766](https://github.com/netease-youdao/LobsterAI/issues/1766) | Dev Deps | Bump Vite 5.4.21 → 8.0.13 (long-standing PR finally closed) |
| [#1764](https://github.com/netease-youdao/LobsterAI/issues/1764) | Deps | Bump react-dom 18.3.1 → 19.2.6 |
| [#1763](https://github.com/netease-youdao/LobsterAI/issues/1763) | Dev Deps | Bump @vitejs/plugin-react 4.7.0 → 6.0.1 |

### Key Advances
- **Cowork UX**: Three merged PRs today (#2471, #2469, #2468) significantly improve the collaborative workspace — file attachments now render as rich cards, loading states are unified, and task collapsing shortcuts reduce visual clutter.
- **OpenClaw reliability**: Two critical runtime fixes (#2454, #2470) address silent failures — the tool-loop guard and late-error swallowing were masking real provider failures from users.
- **Windows Python runtime**: #2467 fixes a subtle upgrade bug where stale pip shim files persisted silently after runtime updates.
- **Dependency modernization**: A large dependabot sweep is advancing Vite to v8 and React to v19, with several PRs still open (#2465, #2464, #2463, #2462, #2461, #2460, #2459).

## 4. Community Hot Topics

| Item | Status | Activity |
|---|---|---|
| [#1243](https://github.com/netease-youdao/LobsterAI/issues/1243) — qwen-portal-auth config loop causing gateway restarts | **CLOSED** | 2 comments, reported 2026-04-01, closed 2026-08-10 |
| [#2473](https://github.com/netease-youdao/LobsterAI/pull/2473) — Right-click context menu for local file links | **OPEN** | Created 2026-08-11 |

**Analysis:** The #1243 bug — a configuration loop in the `qwen-portal-auth` plugin triggering frequent gateway restarts every 5–20 minutes — was a significant user-facing issue that persisted for ~4 months before closure. Its resolution suggests the auth plugin configuration sync logic had a race condition or circular dependency. The community interest in local file interactions continues, as shown by the concurrent context-menu PR (#2473), indicating users want richer file handling in the Cowork artifact area.

## 5. Bugs & Stability

| Severity | Issue / PR | Description |
|---|---|---|
| **High** | [#1243](https://github.com/netease-youdao/LobsterAI/issues/1243) — *Closed* | `qwen-portal-auth` plugin caused infinite config-write loop, triggering gateway restarts every 5–20 min. Affects all models, not just Qwen. |
| **Medium** | [#2454](https://github.com/netease-youdao/LobsterAI/pull/2454) — *Merged* | Tool-loop guard was killing legitimate polling — false-positive loop detection. |
| **Medium** | [#2470](https://github.com/netease-youdao/LobsterAI/pull/2470) — *Merged* | Late chat errors from provider/LLM runtime failures (e.g., idle timeout failover) were silently swallowed. |
| **Medium** | [#2466](https://github.com/netease-youdao/LobsterAI/pull/2466) — *Merged* | Renderer IPC stall on initialization — added retry logic. |
| **Low** | [#2467](https://github.com/netease-youdao/LobsterAI/pull/2467) — *Merged* | Stale pip shims on Windows runtime upgrade went undetected by health checks. |

**No new open bugs reported today.** The three medium-severity OpenClaw/runtime bugs (#2454, #2470, #2466) all have merged fixes, suggesting a dedicated stability push.

## 6. Feature Requests & Roadmap Signals

| Signal | Evidence |
|---|---|
| **Richer file interactions in Cowork** | #2473 (right-click context menu with open/save/copy/reveal), #2471 (file attachment cards) — users want desktop-native file handling |
| **Keyboard shortcut customization** | #2469 — modifier shortcuts while typing; suggests power users want more efficient Cowork navigation |
| **Vite 8 / React 19 migration** | Multiple open dependabot PRs (#2465, #2464, #2463) — the project is mid-migration to modern tooling, which will likely ship in the next major version |
| **Mermaid upgrade to v11** | #2462 — improved diagram rendering in artifacts |

**Prediction:** The next release will likely include the Cowork UX improvements (file cards, context menus, collapse shortcuts), OpenClaw runtime fixes, and possibly the Vite 8 / React 19 upgrades if the dependabot PRs are merged before cut-off.

## 7. User Feedback Summary

- **Pain point (resolved):** Gateway instability caused by auth plugin config loops was a top frustration — users experienced unexpected restarts during normal use, disrupting workflows across all models.
- **Pain point (addressed):** Silent failure of provider runtime errors (timeouts, failovers) left users without diagnostic information. The fix in #2470 surfaces these explicitly.
- **Positive signal:** Users are actively engaging with Cowork features and requesting richer file interactions, indicating the collaboration feature is seeing real adoption.
- **Satisfaction indicator:** No new open issues filed today; the single closed bug and high PR merge rate suggest the team is proactively addressing problems before they accumulate.

## 8. Backlog Watch

| Item | Age | Risk |
|---|---|---|
| [#2452](https://github.com/netease-youdao/LobsterAI/pull/2452) — Preserve provider for slashed model IDs | Open since 2026-08-07 | Medium — `custom_0` + `deepseek-ai/DeepSeek-V4-Flash` loses provider prefix, causing renderer misinterpretation. Affects custom model configurations. |
| [#2465](https://github.com/netease-youdao/LobsterAI/pull/2465) — Bump Vite to 8.2.1 | Open since 2026-08-10 | Low — dependency upgrade, needs merge. |
| [#2464](https://github.com/netease-youdao/LobsterAI/pull/2464) — Bump react-dom to 19.2.8 | Open since 2026-08-10 | Low — dependency upgrade, needs merge. |
| [#2463](https://github.com/netease-youdao/LobsterAI/pull/2463) — Bump @vitejs/plugin-react to 6.0.5 | Open since 2026-08-10 | Low — dependency upgrade, needs merge. |
| [#2462](https://github.com/netease-youdao/LobsterAI/pull/2462) — Bump mermaid to 11.16.1 | Open since 2026-08-10 | Low — dependency upgrade, needs merge. |
| [#2461](https://github.com/netease-youdao/LobsterAI/pull/2461) — Bump eslint-plugin-react-hooks to 7.1.1 | Open since 2026-08-10 | Low — dev dependency. |
| [#2460](https://github.com/netease-youdao/LobsterAI/pull/2460) — Bump rimraf to 6.1.3 | Open since 2026-08-10 | Low — dev dependency. |
| [#2459](https://github.com/netease-youdao/LobsterAI/pull/2459) — Bump @nodesecure/js-x-ray to 16.0.0 | Open since 2026-08-10 | Low — security scanner dependency. |

**Notable:** Eight dependabot PRs are queued for the Vite 8 / React 19 migration. #2452 is the only functional bug PR waiting for review. Maintainer attention should prioritize #2452 (user-impacting) and then batch-merge the dependency upgrades.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-11

## 1. Today's Overview

Moltis shows moderate development activity with 3 open issues and 2 open PRs updated in the last 24 hours, and zero merged/closed items. No new releases were published today, indicating the project is in a maintenance-and-feature-phase rather than a release-candidate window. Activity is concentrated around bug reporting for the Apple Container backend and two feature-oriented PRs that remain under review. Overall project health appears stable but somewhat stagnant from a delivery standpoint.

## 2. Releases

No new releases were published today.

## 3. Project Progress

No PRs were merged or closed today. Two open PRs remain under active review:

- **[PR #1182](https://github.com/moltis-org/moltis/pull/1182)** — *fix(sessions): allow deleting and archiving the main session* (author: shixi-li, last updated 2026-08-11). This PR removes the `main`-session guard in the gateway's `delete_impl` and `is_archivable_entry`, enabling users to delete and archive the default session. It explicitly preserves the restriction on archiving the current-active-channel session and keeps `sessions.clear_all` behavior intact.
- **[PR #531](https://github.com/moltis-org/moltis/pull/531)** — *feat(browser): interactive browser viewing UI with CDP screencast* (author: penso, last updated 2026-08-10). This is a larger feature PR adding a full browser interaction UI via Chrome DevTools Protocol screencast, including mouse/keyboard/scroll input, session history with action logs, and per-agent cookie isolation. Created in March 2026 and still open, it represents a significant UX enhancement.

## 4. Community Hot Topics

The most discussed items today are:

- **[Issue #1185](https://github.com/moltis-org/moltis/issues/1185)** — *Apple Container 1.x sandbox starts but Moltis treats it as not running* (3 comments, author: mikz, created 2026-08-08). This issue has the highest engagement and points to a state-detection mismatch between the Apple Container runtime and Moltis's health-check logic.
- **[Issue #1188](https://github.com/moltis-org/moltis/issues/1188)** — *Resource limits not applied for Apple Container backend* (author: holgzn, created 2026-08-10). Raised alongside #1189, this suggests the Apple Container backend may have incomplete resource-management implementation.
- **[Issue #1189](https://github.com/moltis-org/moltis/issues/1189)** — *Sandbox build failing due to wrong goctl github URL* (author: holgzn, created 2026-08-10). A build-breaker tied to an incorrect dependency URL.

**Underlying need:** The cluster of Apple Container–related issues (#1185, #1188) suggests the backend is either newly integrated or undergoing significant changes, and stability around container lifecycle and resource enforcement is a current pain point. The build URL issue (#1189) reflects a maintenance gap in dependency pinning.

## 5. Bugs & Stability

Three bugs reported today, ranked by inferred severity:

| Rank | Issue | Severity | Summary | Fix PR? |
|------|-------|----------|---------|---------|
| 1 | [#1189](https://github.com/moltis-org/moltis/issues/1189) | **High** — blocks sandbox builds | Wrong `goctl` GitHub URL causes build failure | None yet |
| 2 | [#1188](https://github.com/moltis-org/moltis/issues/1188) | **Medium** — resource limits silently ignored | Apple Container backend does not enforce resource limits | None yet |
| 3 | [#1185](https://github.com/moltis-org/moltis/issues/1185) | **Medium** — false-negative runtime status | Sandbox is running but Moltis reports it as not running | None yet |

All three are open with no associated fix PRs. Issue #1189 is the most urgent as it prevents building from source. Issues #1185 and #1188 both point to the Apple Container backend needing attention.

## 6. Feature Requests & Roadmap Signals

- **PR #531** — Interactive browser viewing UI with CDP screencast. This is the most notable feature advancing through the pipeline. If merged, it would be a standout addition for agents that need visual browser interaction. Its long open status (since March 2026) suggests it may require substantial review before merging.
- **PR #1182** — While framed as a bug fix, allowing deletion/archiving of the main session also functions as a user-requested capability improvement. It is likely to merge sooner given its narrower scope.

No new feature-request issues were opened today.

## 7. User Feedback Summary

- **Apple Container backend frustration** is the dominant theme. Users expect the sandbox to be detected as running once it starts (#1185) and for resource limits to actually be enforced (#1188). These two issues from the same author window (holgzn, 2026-08-10) suggest active evaluation of the Apple Container path, and the current bugs may be causing real workflow disruption.
- **Build-tooling friction** (#1189) indicates that even simple contributor onboarding (building from source) is blocked, which can deter community participation.
- **Session management flexibility** (#1182 / #1132) shows users want finer-grained control over session lifecycle, including the ability to clean up the default `main` session.
- Satisfaction appears mixed: the core agent architecture is functional, but backend-specific integration quality (Apple Container) and build reliability are dragging the experience.

## 8. Backlog Watch

- **[PR #531](https://github.com/moltis-org/moltis/pull/531)** — Open since 2026-03-31 (nearly 5 months). This is a high-value feature that has been in review for an extended period. Maintainer attention is needed to move it toward merge or to communicate a clear status to contributors.
- **[Issue #1185](https://github.com/moltis-org/moltis/issues/1185)** — Open for 3 days with 3 comments but no maintainer response yet. As the most-discussed issue today, it warrants triage.
- **[Issues #1188 & #1189](https://github.com/moltis-org/moltis/issues/1188, https://github.com/moltis-org/moltis/issues/1189)** — Both opened today with zero comments. Issue #1189 (build breaker) should be prioritized for quick resolution.

---

*Digest generated from GitHub data as of 2026-08-11. Data source: [moltis-org/moltis](https://github.com/moltis-org/moltis).*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-11

## 1. Today’s Overview
QwenPaw shows high development velocity with **39 issues** and **50 PRs** updated in the last 24 hours (33 open issues, 33 open PRs, 17 merged/closed). No new release was shipped today, but several critical bug fixes and feature improvements were landed. Activity is concentrated on console UI stability, provider compatibility, and memory‑backend enhancements. The project remains in a pre‑release phase for v2.1.0, with a release‑notes PR already prepared.

## 2. Releases
No new releases today. The latest release is **v2.1.0b2** (installed via pip on 2026‑08‑09). A release‑notes PR (#6875) has been merged to document the v2.1.0 changes.

## 3. Project Progress
**Merged / closed PRs today (17):**
- [#6809](https://github.com/agentscope-ai/QwenPaw/pull/6809) – Sanitize Chat Completions content for strict OpenAI‑compatible providers (fixes StepFun 400 errors).
- [#6878](https://github.com/agentscope-ai/QwenPaw/pull/6878) – Add hidden‑folders toggle to project‑directory picker.
- [#6615](https://github.com/agentscope-ai/QwenPaw/pull/6615) – Handle corrupted agent config and invalid JSON in `load_agent_config`.
- [#6398](https://github.com/agentscope-ai/QwenPaw/pull/6398) – Add reranker support for ReMe memory search (backend).

**Features advanced / fixed:**
- **Per‑session model overrides** – PR #5992 is open, allowing different LLMs per conversation without changing defaults.
- **Memory UI** – PR #6399 adds a reranker‑configuration panel to ReMeLightMemoryCard.
- **Console stability** – PR #6890 fixes multiline tool‑output rendering; PR #6889 fixes Chinese‑IME composition bug.
- **Auto‑Dream resilience** – PR #6884 makes integration tolerant of malformed LLM schemas.

## 4. Community Hot Topics
**Top issues by comment count:**
1. [#6782](https://github.com/agentscope-ai/QwenPaw/issues/6782) (9 comments) – Docker‑version plugin/app market always shows “maintenance”.
2. [#6803](https://github.com/agentscope-ai/QwenPaw/issues/6803) (6 comments) – OpenAI‑compatible providers reject internal content fields (fixed by PR #6809).
3. [#6811](https://github.com/agentscope-ai/QwenPaw/issues/6811) (5 comments) – Responses‑API continuation summary ignores `disable_thinking`.
4. [#6826](https://github.com/agentscope-ai/QwenPaw/issues/6826) (5 comments) – Assistant‑message end‑time displayed incorrectly.
5. [#4237](https://github.com/agentscope-ai/QwenPaw/issues/4237) (4 comments) – In‑chat observability for shell commands (feature request).

**Underlying needs:** Users demand better compatibility with strict third‑party providers, accurate timing metadata in conversations, and more transparency into running background tasks. The Docker‑version marketplace issue suggests packaging or backend‑connectivity problems.

## 5. Bugs & Stability
**Reported bugs (ranked by severity):**
| Issue | Severity | Description | Fix PR |
|-------|----------|-------------|--------|
| [#6814](https://github.com/agentscope-ai/QwenPaw/issues/6814) | **Critical** | SIGBUS crash when opening Scroll history.db (SQLite WAL) on macOS. | None yet |
| [#6885](https://github.com/agentscope-ai/QwenPaw/issues/6885) | **High** | Console UI crashes during Chinese IME composition; message queue unusable. | #6889 (open) |
| [#6820](https://github.com/agentscope-ai/QwenPaw/issues/6820) | **High** | Frontend does not stream model output; all content appears only after completion. | None yet |
| [#6813](https://github.com/agentscope-ai/QwenPaw/issues/6813) | **Medium** | `consume_model_response` raises `KeyError: '__aiter__'` on ChatResponse dict subclass. | None yet |
| [#6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) | **Medium** | MCP tools receive numeric strings instead of string parameters, causing call failures. | None yet |
| [#6780](https://github.com/agentscope-ai/QwenPaw/issues/6780) | **Medium** | Application hangs after ~30 minutes of inactivity; requires process restart. | None yet |
| [#6828](https://github.com/agentscope-ai/QwenPaw/issues/6828) | **Low** | Idle console repainting at ~20% CPU due to infinite CSS animations. | None yet |

**Notes:** The SIGBUS crash (#6814) and IME‑induced UI crash (#6885) are the most disruptive. A fix for the IME issue is already in review (#6889).

## 6. Feature Requests & Roadmap Signals
**Open feature requests:**
- [#4237](https://github.com/agentscope-ai/QwenPaw/issues/4237) – In‑chat panel for monitoring/controlling running shell commands.
- [#6881](https://github.com/agentscope-ai/QwenPaw/issues/6881) – Auto‑refresh session title after auto‑memory update.
- [#6724](https://github.com/agentscope-ai/QwenPaw/issues/6724) – Configurable MCP tool‑call timeout (per‑client + call‑level guard).
- [#4634](https://github.com/agentscope-ai/QwenPaw/issues/4634) – Remember window size/position across restarts.
- [#6585](https://github.com/agentscope-ai/QwenPaw/issues/6585) – Toggle to disable dynamic character‑count animation in chat box.

**Likely candidates for v2.1.0:**
- Auto‑dream integration resilience (PR #6884) is already merged.
- Reranker support for ReMe (PR #6398) is merged and will ship with v2.1.0.
- Hidden‑folders toggle (PR #6878) is closed and ready.

## 7. User Feedback Summary
**Pain points:**
- **Provider compatibility:** Strict OpenAI‑compatible endpoints (StepFun, Gemini) reject internal fields or extra schema keys.
- **UI responsiveness:** Console stalls or crashes during IME composition; idle CPU usage is high due to infinite animations.
- **Observability:** Users cannot see running shell commands, kill them, or adjust timeouts from the chat interface.
- **Stability:** Application hangs after idle periods; SQLite WAL crashes on macOS.
- **MCP tool parameter handling:** String‑like numbers are incorrectly cast to integers, breaking tool calls.

**Satisfaction signals:**
- Users praise the project (“非常不错的项目”) and request quality‑of‑life improvements (disable character‑count animation, window‑size memory).
- Feature requests show engaged users who want deeper control over memory, timeouts, and UI behavior.

## 8. Backlog Watch
**Important open issues needing maintainer attention:**
- [#6814](https://github.com/agentscope-ai/QwenPaw/issues/6814) – SIGBUS crash on macOS (critical, no fix yet).
- [#6820](https://github.com/agentscope-ai/QwenPaw/issues/6820) – Frontend does not stream output (high, no fix).
- [#6813](https://github.com/agentscope-ai/QwenPaw/issues/6813) – `KeyError: '__aiter__'` in auto‑title generation (medium).
- [#6780](https://github.com/agentscope-ai/QwenPaw/issues/6780) – Idle hang requiring restart (medium).
- [#6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) – MCP numeric‑string parameter bug (medium).

**Stalled PRs:**
- [#5992](https://github.com/agentscope-ai/QwenPaw/pull/5992) – Per‑session model overrides (open since July 12, no comments).
- [#6724](https://github.com/agentscope-ai/QwenPaw/issues/6724) – MCP timeout configuration (open issue, no PR yet).

These items represent high‑impact bugs and feature requests that could benefit from triage or contribution.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-11

## 1. Today's Overview

ZeroClaw is experiencing high issue and PR velocity with 50 issues and 50 PRs updated in the last 24 hours, though the vast majority remain open (49 open issues, 48 open PRs). The project is in a mature RFC-driven governance phase with multiple governance and security-related discussions active. Notably, there are zero new releases since 0.8.3, and the activity is dominated by security audit follow-ups, CI hardening, and infrastructure issues rather than feature development. The project appears healthy in terms of community engagement but faces a growing backlog of high-risk security findings that require coordinated remediation.

## 2. Releases

No new releases published. Current version remains **0.8.3** (per issue #9562).

## 3. Project Progress

**Merged/Closed today:**

- **PR #9904** — `chore(security): ignore RUSTSEC-2026-0247 (bitmaps unmaintained)`. The `bitmaps` crate was archived by its owner; `cargo deny` now skips the unsolvable vulnerability.
- **PR #8301** — `test(hardware): cover catalog tool name format`. Added a regression test ensuring all catalog tool names are valid `lower_snake_case` identifiers. Closed 2026-08-10.

**Notable PRs advancing today:**

- **PR #9583** — CI rustdoc warning gate landed into config; `-D warnings` now folded into `.cargo/config.toml` so all doc/test paths enforce zero warnings. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9583)
- **PR #9694** — SOP pane exposed as a read-only status view in ZeroCode (closes #9682). [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9694)
- **PR #9903** — Arduino flash temp directories now cleaned up via `tempfile::TempDir` to prevent filesystem leaks. [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/9903)

## 4. Community Hot Topics

| # | Type | Title | Comments | Link |
|---|------|-------|----------|------|
| #6808 | RFC | Work Lanes, Board Automation, and Label Cleanup | 23 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) |
| #7100 | RFC | Per-model capability & context-window config | 13 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) |
| #8692 | Tracker | Maintainer decision queue for RFCs and design issues | 12 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| #9397 | RFC | Empty WhatsApp Web `allowed_groups` → permit-none | 12 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) |
| #9530 | RFC | Risk precedence for test-only changes in high-risk paths | 7 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9530) |
| #9496 | RFC | Streamline RFC scope, discussion, voting, and assignment | 7 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9496) |

**Analysis:** The top-discussed items are overwhelmingly governance and process topics — work lanes, RFC streamlining, and risk-label precedence. This signals a project at a scaling inflection point where maintainer bandwidth is the bottleneck. The community is investing heavily in making the contribution and review process sustainable rather than shipping new features. The WhatsApp `allowed_groups` RFC (#9397) is the most active security-adjacent discussion, reflecting operator concern about default-deny posture.

## 5. Bugs & Stability

**Critical / Security (S0–S1) — ranked by severity:**

| # | Title | Severity | Fix PR? | Link |
|---|-------|----------|---------|------|
| #9647 | Knowledge graph has no per-agent attribution — any agent reads/mutates another agent's knowledge | S0 | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9647) |
| #9855 | Matrix channel fails to resolve homeserver via `.well-known/matrix/client` delegation | S0 | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9855) |
| #9627 | Git write verbs bypass risk classifier via global options like `-C` / `--git-dir` | S0 | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9627) |
| #9779 | `sops_dir` documented default not honoured — SOPs silently never load | High | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) |
| #9425 | Running SOP jobs have no operator cancellation path | S1 | Partial (#9694 adds read-only view) | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9425) |
| #9035 | Docker Compose gateway can remain loopback-bound behind published port | S1 | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9035) |
| #9393 | Bluesky and Reddit have no sender authorization | High | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9393) |
| #9395 | Plugin wasi:http egress has no destination policy | High | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9395) |
| #9392 | LINE group messages skip allowlist and pairing handshake | High | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9392) |
| #9389 | Unauthenticated POST `/api/pair` keys lockout on attacker-supplied header | High | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9389) |
| #9391 | Command audit logging defaults enabled but writes nothing | High | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9391) |
| #9231 | Docker runtime commands nested inside a second Docker sandbox | S1 | No | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9231) |

**High-profile audit batch:** Issues #9389–#9397 (filed by `belumume`) represent a coordinated security audit of the host the project builds against. At least 7 of these remain open with no fix PRs, suggesting a significant remediation backlog.

**Other notable bugs:**
- #9768 — Daemon reload signal mismatch (`SIGUSR1` vs documented signal that kills the daemon). [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9768)
- #9562 — WebChat auto-scroll overrides manual scrolling during streaming. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9562)
- #9844 — ZeroCode dashboard CPU metric measures daemon, not the ZeroCode process itself. [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/9844)
- #8999 — ZeroCode streamed user turns misinterpreted as log/API payloads by small local models (Ollama). [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8999)

## 6. Feature Requests & Roadmap Signals

| # | Title | Status | Link |
|---|-------|--------|------|
| #7100 | Per-model capability & context-window config (vision, context_window) | RFC accepted | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) |
| #9554 | `dag_plan_execute` tool for sequential and parallel task planning | In progress | [PR](https://github.com/zeroclaw-labs/zeroclaw/pull/9554) |
| #8486 | OpenAI chat completions endpoint on gateway | Open | [PR](https://github.com/zeroclaw-labs/zeroclaw/pull/8486) |
| #9339 | Custom CA trust for remote MCP servers | In progress | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9339) |
| #5842 | Warn when Codex CLI `extra_args` weaken sandbox/policy | In progress | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/5842) |
| #9047 | Clarify Code session history and persistent-memory isolation | In progress | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9047) |

**Prediction:** The `dag_plan_execute` tool (#9554) and per-model capability config (#7100) are the strongest candidates for the next release. The OpenAI endpoint (#8486) has been open since late June and may ship if integration testing completes. Custom CA trust for MCP (#9339) is a niche enterprise need that may follow.

## 7. User Feedback Summary

- **Security paranoia is the dominant theme.** Multiple operators are auditing the project against their own threat models, producing detailed, citation-backed bug reports (#9389–#9397). The community values ZeroClaw's sandbox model and is frustrated when enforcement gaps appear.
- **SOP (Standard Operating Procedure) reliability is a pain point.** Users report that SOPs silently fail to load when `sops_dir` relies on its documented default (#9779), and running SOPs cannot be cancelled from the web UI (#9425). This suggests SOP is used in production workflows and opacity around failures is unacceptable.
- **ZeroCode local-model experience is degraded.** Small models like `llama3.2` misinterpret streamed protocol data as user input (#8999), and the dashboard CPU metric is misleading (#9844). This indicates ZeroCode's primary audience (local-first users) is underserved on the UX signal fidelity front.
- **Email threading and Telegram media grouping are live needs.** PRs #9523 (email `Reply-To`/`References`) and #8955 (Telegram batch media) address real interoperability gaps users hit daily.

## 8. Backlog Watch

| # | Title | Age | Risk | Link |
|---|-------|-----|------|------|
| #9647 | Knowledge graph lacks per-agent attribution | ~10 days | S0 / data loss | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9647) |
| #9389 | Pairing endpoint lockout exploit via attacker-supplied header | ~16 days | High | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9389) |
| #9391 | Audit logging defaults on but writes nothing | ~16 days | High | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9391) |
| #9393 | Bluesky/Reddit no sender authorization | ~16 days | High | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9393) |
| #9395 | Plugin wasi:http egress no destination policy | ~16 days | High | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9395) |
| #9397 | WhatsApp empty `allowed_groups` permits all | ~16 days | High | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) |
| #9392 | LINE group messages skip allowlist + pairing | ~16 days | High | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9392) |
| #8486 | OpenAI completions endpoint (open since Jun 29) | ~43 days | P2 | [PR](https://github.com/zeroclaw-labs/zeroclaw/pull/8486) |
| #8692 | Maintainer decision queue tracker | ~37 days | P2 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| #9496 | Streamline RFC process | ~14 days | P1 | [Issue](https://github.com/zeroclaw-labs/zeroclaw/issues/9496) |

**Assessment:** The `belumume` audit batch (#9389–#9397) represents the most critical backlog — seven high-risk security issues with zero fix PRs after 16+ days. These should be the top priority for maintainer triage. The OpenAI endpoint PR (#8486) has been open for over six weeks and may need a sponsor to move forward. The RFC streamlining tracker (#9496) and governance decision queue (#8692) are process items that, if resolved, would unblock much of the stalled work.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*