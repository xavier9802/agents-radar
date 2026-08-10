# OpenClaw Ecosystem Digest 2026-08-10

> Issues: 500 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-10 02:18 UTC

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



# OpenClaw Project Digest — 2026-08-10

## 1. Today's Overview

OpenClaw is experiencing **very high development velocity** with 500 issues and 500 PRs updated in the last 24 hours. The project shows a strong 66% open-to-closed PR ratio (332 open vs. 168 merged/closed), indicating sustained contributor momentum. No new releases were published today, but a significant number of PRs were closed/merged, suggesting the team is in a cleanup and stabilization phase ahead of an upcoming release. Issue triage remains active with 429 open issues, though several high-severity bugs persist without merged fixes.

## 2. Releases

**No new releases published today.** The project appears to be in a pre-release stabilization window, with multiple fix PRs landing but no version tag cut yet.

## 3. Project Progress

**Merged/Closed PRs today:**

- **#121342** — `fix(sessions): avoid full cache scans after transcript writes` — Eliminates a performance regression where tool-heavy turns triggered O(n) SQLite scans, scaling from 2,500 rows (50 sessions) to 250,000 rows (5,000 sessions). A critical backend optimization.
- **#121146** — `fix(agents): pair reset tool results within retained session history` — Fixes incoherent replay context when providers reuse call IDs across session resets.
- **#121346** — `fix: preserve GPT-5 personality through doctor migration` — Restores user-configured `gpt5.personality: "off"` that was being silently re-enabled by `openclaw doctor --fix`.
- **#121253** — `fix(qa): reuse one immutable Docker candidate` — Stabilizes the QA Lab Docker evidence pipeline (supersedes #120588).
- **#121322** — `fix(ui): restore Desktop panel launchers` — Fixes a UI regression where Cloud Worker Desktop panel launchers became undiscoverable.

**Key refactors advancing today:**

- **#121312** — Removes duplicate account-id, sleep, and config wrapper layers, improving code ownership clarity.
- **#121341** — Consolidates failover classification into a single substrate, eliminating precedence drift between structured and message-only failure paths.
- **#121308** — Flattens channel-turn dispatch naming layers (up to 6 aliases across 6 layers reduced).
- **#121345** — Removes dead configuration branches and test-only helpers across the codebase.
- **#121350** — Moves spawn family into `src/agents/subagents/` for better ownership boundaries.

## 4. Community Hot Topics

| Issue | Title | Comments | Status |
|---|---|---|---|
| [#116277](https://github.com/openclaw/openclaw/issues/116277) | DeepSeek v4 Flash silent reply failure | 196 | ✅ Closed |
| [#22438](https://github.com/openclaw/openclaw/issues/22438) | Tiered bootstrap file loading for progressive context control | 19 | 🔓 Open |
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | Silent reply failures still recurring after #116277 closed | 19 | 🔓 Open |
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | Codex PreToolUse hook spawns CPU-bound processes, stalls gateway | 18 | 🔓 Open |
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | gh-issues skill: untrusted issue body injected into sub-agent prompt | 16 | 🔓 Open |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | Steer mode does not inject messages mid-turn | 16 | 🔓 Open |
| [#10659](https://github.com/openclaw/openclaw/issues/10659) | Masked Secrets — prevent agent from accessing raw API keys | 15 | 🔓 Open |

**Analysis:** The #116277 closed-then-recurring pattern (#121058) signals a persistent reliability gap in the DeepSeek v4 Flash integration path. The tiered bootstrap loading request (#22438) reflects growing friction around context window budget for large workspaces. Security concerns (untrusted prompt injection in #45740, raw API key exposure in #10659) are recurring themes, indicating users increasingly deploy OpenClaw in multi-tenant or untrusted-input environments.

## 5. Bugs & Stability

**P0 / Release-Blocker:**

- [#111372](https://github.com/openclaw/openclaw/issues/111372) — **Gateway infinite SIGTERM restart loop on macOS** after upgrading to 2026.7.1-2. No fix PR yet. 🔓 Open
- [#48920](https://github.com/openclaw/openclaw/issues/48920) — **Live docs ahead of release**: `IsolatedSessions` documented but absent in 2026.3.13. No fix PR yet. 🔓 Open

**P1 — Session State & Message Loss:**

- [#121058](https://github.com/openclaw/openclaw/issues/121058) — Silent reply failures **recurring** after #116277 was closed. Monitoring cron continues to log occurrences. 🔓 Open
- [#96242](https://github.com/openclaw/openclaw/issues/96242) — **Duplicate Telegram messages** across multiple independent paths on 2026.6.8. 🔓 Open
- [#114020](https://github.com/openclaw/openclaw/issues/114020) — **Feishu/Telegram channel dispatch failure** after 2026.7.2-beta.4 upgrade (`runChannelInboundEvent` requires `runDispatchLifecycle`). 🔓 Open
- [#47975](https://github.com/openclaw/openclaw/issues/47975) — Subagent sessions persist after completion; main session becomes unresponsive. 🔓 Open
- [#114211](https://github.com/openclaw/openclaw/issues/114211) — Matrix room agents loop on no-reply output with stale session replay. 🔓 Open

**P1 — Crash & Reliability:**

- [#91009](https://github.com/openclaw/openclaw/issues/91009) — Codex PreToolUse hook spawns CPU-bound `openclaw-hooks` processes, stalling gateway RPC. 🔓 Open
- [#72015](https://github.com/openclaw/openclaw/issues/72015) — `active-memory` plugin blocks replies; QMD boot initialization overloads multi-agent gateways. 🔓 Open
- [#97616](https://github.com/openclaw/openclaw/issues/97616) — **Zombie child process leak** (`openclaw-hooks`, `bash`, `codex`) causing runtime degradation. 🔓 Open
- [#90378](https://github.com/openclaw/openclaw/issues/90378) — Cron store migration (JSON→SQLite) silently drops job config on 5.28→6.1 upgrade. 🔓 Open

**P1 — Platform-Specific:**

- [#105528](https://github.com/openclaw/openclaw/issues/105528) — `exec`/`read` tools return empty output on Windows (2026.6.x regression). 🔓 Open
- [#51049](https://github.com/openclaw/openclaw/issues/51049) — WhatsApp inbound messages not received in k3s nested container. 🔓 Open

**Fix PRs landed today:**
- [#121342](https://github.com/openclaw/openclaw/pull/121342) — Fixes transcript write cache scan regression (related to performance/stability).
- [#121146](https://github.com/openclaw/openclaw/pull/121146) — Fixes session reset tool result pairing.
- [#121314](https://github.com/openclaw/openclaw/pull/121314) — Fixes Signal message loss on debounce flush failure (closes #121269).

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Community Support |
|---|---|---|
| [#22438](https://github.com/openclaw/openclaw/issues/22438) | Tiered bootstrap file loading for context budget control | 19 comments |
| [#10659](https://github.com/openclaw/openclaw/issues/10659) | Masked secrets — agent can use but not see API keys | 15 comments, 4 👍 |
| [#67413](https://github.com/openclaw/openclaw/issues/67413) | Per-agent dreaming configuration (memory-core) | 8 comments, 5 👍 |
| [#6757](https://github.com/openclaw/openclaw/issues/6757) | Agent-triggered context compaction (self-compact tool) | 8 comments, 2 👍 |
| [#60572](https://github.com/openclaw/openclaw/issues/60572) | Multi-Slot Memory Architecture | 6 comments, 3 👍 |
| [#47677](https://github.com/openclaw/openclaw/issues/47677) | First-class Telegram reaction triggers | 6 comments, 2 👍 |
| [#63990](https://github.com/openclaw/openclaw/issues/63990) | Multi-index embedding memory with model-aware failover | 6 comments, 1 👍 |
| [#80131](https://github.com/openclaw/openclaw/issues/80131) | Per-request auth & tool bundling performance optimization | 5 comments, 3 👍 |

**Roadmap prediction:** Tiered bootstrap loading (#22438) and per-agent dreaming (#67413) are the strongest candidates for the next release — both address scaling pain points for power users and have active community discussion. Masked secrets (#10659) is a security-critical feature likely to land in a subsequent release. Multi-slot memory (#60572) is architecturally significant but will require deeper design work.

## 7. User Feedback Summary

**Pain points:**

- **Silent failures are eroding trust.** The DeepSeek v4 Flash reply failure (#116277 → #121058) closed then recurred, with the user's own monitoring cron catching the regression. Users are building external surveillance on top of OpenClaw because the built-in observability is insufficient.
- **Context window waste is a real cost.** Large-workspace users report bootstrap files consuming tokens across all sessions including sub-agents and cron jobs (#22438). This is a direct budget concern.
- **Upgrade migrations are unreliable.** The JSON→SQLite cron migration silently dropping job configs (#90378) and the GPT-5 personality reset by `doctor --fix` (#121346, now fixed) both reflect a pattern where upgrade paths are not adequately tested.
- **Windows and containerized deployments are fragile.** Empty `exec`/`read` output on Windows (#105528) and WhatsApp inbound failures in k3s (#51049) show that non-standard deployments are under-tested.
- **Security posture is a growing concern.** Untrusted prompt injection via gh-issues (#45740) and raw API key exposure (#10659) indicate users are deploying OpenClaw in contexts where isolation boundaries matter.

**Positive signals:**

- The project responded quickly to the GPT-5 personality regression with a same-day fix (#121346).
- The transcript scan performance fix (#121342) directly addresses a scalability bottleneck identified by power users.
- Community engagement is high — issues are consistently well-reproduced with version info, environment details, and monitoring data.

## 8. Backlog Watch

| Issue | Age | Priority | Blockers |
|---|---|---|---|
| [#111372](https://github.com/openclaw/openclaw/issues/111372) | ~22 days | P0 | Infinite macOS restart loop, no fix PR |
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | ~149 days | P1 | Untrusted prompt injection, needs security review |
| [#10659](https://github.com/openclaw/openclaw/issues/10659) | ~124 days | P1 | Raw API key exposure, needs product decision |
| [#91009](https://github.com/openclaw/openclaw/issues/91009) | ~65 days | P1 | CPU stall from Codex hooks, needs live repro |
| [#121058](https://github.com/openclaw/openclaw/issues/121058) | 1 day | P1 | Silent reply recurrence post-fix, needs maintainer review |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | ~72 days | P1 | Zombie process leak, no fix PR |
| [#90378](https://github.com/openclaw/openclaw/issues/90378) | ~67 days | P1 | Silent cron migration data loss, needs product decision |

**Maintainer attention needed:** The P0 macOS restart loop (#111372) has no assigned fix and blocks upgrade paths. The security issues (#45740, #10659) have been open for 5+ months and carry explicit `needs-security-review` tags. The recurring silent-reply bug (#121058) warrants a re-opening or follow-up fix PR before the next release.

---

## Cross-Ecosystem Comparison



# Cross-Project Ecosystem Comparison Report
**Date:** 2026-08-10

---

## 1. Ecosystem Overview

The open-source personal AI assistant and agent landscape is in a mature-hardening phase. Projects that previously raced to ship new features are now investing heavily in security hardening, deployment reliability, and observability — with seven of eleven tracked projects reporting critical or P0 security/stability bugs. Development velocity is polarized: four projects (OpenClaw, Hermes Agent, ZeroClaw, IronClaw) show very high activity, while three (NullClaw, ZeptoClaw, LobsterAI) are effectively dormant. The community is pushing all projects toward production-readier postures, demanding better token cost visibility, provider abstraction, and containerized security.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | New Release | Open PRs | Health Score* |
|---|---|---|---|---|---|
| **OpenClaw** | 500 | 500 | ❌ None | 332 | 🟢 7.5/10 |
| **Hermes Agent** | 50 | 50 | ❌ None | 46 | 🟡 5.0/10 |
| **ZeroClaw** | 50 | 50 | ❌ None | 49 | 🟡 5.5/10 |
| **IronClaw** | 22 | 32 | ❌ None | — | 🟢 7.0/10 |
| **NanoBot** | 5 | 16 | ❌ None | 12 | 🟡 6.0/10 |
| **CoPaw (QwenPaw)** | 18 | 26 | ❌ None | — | 🟡 6.0/10 |
| **NanoClaw** | 1 | 16 | ❌ None | 16 | 🟡 5.5/10 |
| **PicoClaw** | 3 | 6 | ❌ None | — | 🟡 4.5/10 |
| **LobsterAI** | 3 | 0 | ❌ None | — | 🔴 2.5/10 |
| **Moltis** | 2 | 1 | ❌ None | 1 | 🟡 4.0/10 |
| **NullClaw** | 0 | 0 | ❌ None | — | 🔴 1.0/10 |
| **ZeptoClaw** | 0 | 0 | ❌ None | — | 🔴 1.0/10 |

*Health Score combines development velocity, PR closure rate, bug responsiveness, and security posture. Scale: 10 = thriving, 1 = at risk.*

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Velocity leader:** 500 issues/PRs in 24 hours dwarfs all competitors; the closest comparable is ZeroClaw at 50. This signals an exceptionally active contributor base and rapid triage cadence.
- **Performance-science depth:** The transcript-write cache optimization (#121342, reducing O(n) SQLite scans from 2,500 to 250,000 rows) reflects engineering rigor uncommon in other projects.
- **Provider breadth:** Deep integration across DeepSeek, GPT-5, Telegram, Signal, Matrix, Feishu, and WhatsApp — the widest multi-channel support in the dataset.
- **Architectural refactors:** Today's parallel work on failover classification, channel-turn dispatch flattening, and subagent ownership boundaries shows investment in long-term maintainability, not just feature shipping.

**Differences from peers:**
- OpenClaw operates at a **platform scale** (5,000+ session environments) where other projects are still solving single-tenant correctness.
- Unlike NanoClaw (container-first hardened image) and IronClaw (Reborn platform with skill mounts), OpenClaw is **deployment-agnostic** with a focus on session/memory internals.
- Its community self-monitors bugs via external cron tools (#121058), indicating a user base that has outgrown built-in observability — a maturity signal but also a trust gap.

---

## 4. Shared Technical Focus Areas

| Theme | Projects Involved | Specific Need |
|---|---|---|
| **Security hardening (SSRF/auth bypass)** | OpenClaw, PicoClaw, ZeroClaw, NanoBot, NanoClaw | Media-download SSRF, credential leakage, allowlist bypass, webhook auth gaps — all projects now surface these as top-priority bugs |
| **Token/cost observability** | NanoBot, OpenClaw, ZeroClaw | Users demand per-call token logging; NanoBot reports ~1M tokens burned in 2 hours with no visibility; OpenClaw's tiered bootstrap (#22438) targets context budget control |
| **Context window management** | OpenClaw, LobsterAI, ZeroClaw | Missing configurable context-window settings (LobsterAI #1187), silent compaction (OpenClaw #116277), provider misreporting (ZeroClaw RFC #7100) |
| **Container/deployment reliability** | NanoBot, NanoClaw, OpenClaw, Moltis | Docker entrypoint permissions (NanoBot #5295), pip-install gap in hardened images (NanoClaw #3217), Windows regressions (OpenClaw #105528), container runtime detection (Moltis #1185) |
| **Channel reliability** | OpenClaw, NanoBot, PicoClaw, IronClaw | Silent Telegram/Matrix failures, stale session replay loops, WhatsApp group policy defaults — cross-cutting channel fragility |
| **Memory/dream architecture** | OpenClaw, CoPaw, ZeroClaw | Multi-slot memory (#60572), dream consolidation tool mismatches (NanoBot #5302), Hindsight memory panics (ZeroClaw #9085) |
| **Provider abstraction** | NanoBot, IronClaw, CoPaw, ZeroClaw | Swappable response providers, Gemini `$schema` rejection (CoPaw #6812), multi-model-per-provider configs (ZeroClaw #9809) |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | ZeroClaw | NanoClaw | IronClaw | NanoBot |
|---|---|---|---|---|---|---|
| **Primary focus** | Session/memory internals, multi-channel | Session-state reliability, security | Security-first governance, Rust runtime | Hardened container images | Platform skill ecosystem | Provider abstraction, plugin portability |
| **Target user** | Power users, multi-agent operators | Desktop users, CLI power users | Security-conscious deployers | Python-dependent agents in containers | Automation/reasoning workflows | Developer-integrated agents |
| **Architecture** | Monorepo, deep provider integration | Relay gateway, holographic memory | Rust-native, verifiable intent | Container-first, CVE-gated pipeline | Skill-mount DB tree, deferred tool discovery | Plugin v1 + CLI apps, Responses API |
| **Deployment model** | Local + cloud worker | Desktop app, CLI | Rust binary, multi-platform | Docker Hub multi-arch | Web UI + API server | Docker Compose, LAN-deployable |
| **Unique strength** | Scale (5,000+ sessions), performance opt | Multi-profile auth isolation | Governance RFC process, security rigor | Supply-chain transparency (grype CVE gates) | Progressive tool disclosure UX | Token observability, quick refactor velocity |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (very high velocity, active bug response):**
- **OpenClaw:** 500 PRs/issues, 66% open-to-closed ratio, same-day fixes for regressions. The most contributor-rich project in the ecosystem.
- **ZeroClaw:** 50 PRs/issues, large PR backlog (49 open), active RFC governance. Security bugs are being triaged and fixed quickly but review throughput is a bottleneck.
- **Hermes Agent:** 50 PRs/issues, intense stabilization sprint. Two P0 bugs reported today; active SSRF hardening. High contributor engagement but release cadence lags behind bug discovery.

**Tier 2 — Actively Developing (steady velocity, focused work):**
- **IronClaw:** 32 PRs, 7 issues closed today, strong feature pipeline (browser push, parallel batch execution). Mature bug-bash culture producing actionable P2s.
- **CoPaw:** 26 PRs, influx of first-time contributors. Good fix velocity on provider issues but a large open-PR queue.
- **NanoBot:** 16 PRs, responsive on security advisories, strong refactor momentum. Mid-scale contributor base.

**Tier 3 — Maintenance Mode (low velocity, small PR volume):**
- **NanoClaw:** 16 open PRs but no merges today; security-focused but slow review throughput.
- **PicoClaw:** 6 PRs, moderate security hardening. Matrix reconnection bug closed stale without a fix.

**Tier 4 — Dormant or At Risk:**
- **LobsterAI:** Zero merges, two `[stale]` issues. Low maintainer engagement.
- **Moltis:** 1 PR, 2 issues — triage phase, minimal activity.
- **NullClaw, ZeptoClaw:** No activity whatsoever.

---

## 7. Trend Signals

1. **Security is the dominant concern across all active projects.** Every project with meaningful activity reports SSRF, auth bypass, or credential-leakage bugs. AI agents are moving from "local convenience tools" to "network-facing services," and the community is forcing maintainers to treat security as a first-class requirement. *Value for developers: plan for SSRF validation, credential isolation, and allowlist hardening from day one.*

2. **Observability is the new feature battleground.** Token burn anxiety (#5266, NanoBot), per-call usage records (#5299), and streaming latency fixes (#6843, CoPaw) show users now expect enterprise-grade telemetry from their agents. *Value: projects with built-in token/duration/turn observability will win power-user adoption.*

3. **Provider abstraction is table stakes.** All five major projects are investing in multi-provider support (OpenAI, DeepSeek, Gemini, Copilot, local). The differentiator is shifting from "which providers do you support?" to "how cleanly can I swap providers?" *Value: clean provider seams and SDK-agnostic tool contracts are architectural priorities.*

4. **Container security is creating a new deployment tier.** NanoClaw's CVE-gated Docker Hub pipeline and the hardened-image pip-gap (#3217) signal a split between "convenience local install" and "production-hardened container." *Value: projects that bridge this gap (pip in hardened images, SBOM generation) will capture the ops-heavy segment.*

5. **Context window management is a silent cost driver.** Users are burning tokens on idle sessions, stale replay, and unbounded context growth. Tiered bootstrap loading (#22438, OpenClaw), per-model context config (ZeroClaw RFC #7100), and self-compact tools (#6757) are emerging solutions. *Value: agents that respect context budgets will reduce operational costs significantly.*

6. **Governance maturity is correlating with project longevity.** ZeroClaw's RFC process (6 active RFCs, #9496 streamlining discussion) and IronClaw's structured bug bashes suggest that projects formalizing contribution and security review processes are building more sustainable communities. *Value: developers should prefer projects with transparent RFC/decision processes for long-term adoption.*

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-10

## 1. Today's Overview

NanoBot is exhibiting **high development velocity** with 16 PRs updated and 5 issues touched in the last 24 hours. The project is actively iterating on session management, Telegram reliability, and API diagnostics — indicating a focus on **stability hardening** rather than major new features. No new releases were published today. Two critical security advisories were surfaced regarding the `exec` tool's allowlist, which demands urgent maintainer attention. Overall project health is strong: a healthy open/merged PR ratio (12 open / 4 closed) signals active community contribution alongside responsive maintenance.

## 2. Releases

**No new releases today.** The latest release timeline is unclear from available data. Users experiencing the reported Docker Compose permission issue (#5295) or the Agnes AI double-encoding bug (#5311) may wish to build from source or await an upcoming patch release.

## 3. Project Progress

**Merged / Closed PRs today:**

- **#5307** — [Restore Star History chart](https://github.com/HKUDS/nanobot/pull/5307) (Mubelotix): Replaced a discontinued GitHub star-history widget with a new provider, restoring the project's public growth visualization.
- **#5308** — [Strengthen user-path coverage and CI gates](https://github.com/HKUDS/nanobot/pull/5308) (chengyongru): Added comprehensive user-path tests (interactive CLI, WebUI chat forks, route auth, failure boundaries), removed redundant tests, added V8 coverage reporting, and tightened CI to enforce coverage thresholds.
- **#5304** — [Fix WebUI HTTPS requirement for voice input](https://github.com/HKUDS/nanobot/pull/5304) (chengyongru): Clarified the HTTPS requirement for browser microphone access across all locales, documenting trusted HTTPS options for LAN deployments.
- **#4019** — [GitAgent Protocol support](https://github.com/HKUDS/nanobot/pull/4019) (shreyas-lyzr): Closed/Merged PR adding portable agent manifest support via `agent.yaml` and `SOUL.md`.

**Key open work advancing:**
- **#5271** (yorkhellen) — P0 fix for stale background task saves overwriting session data, a critical race condition during `/new` commands.
- **#5204** (chengyongru) — P1 refactor declaring Responses capabilities across providers (OpenAI, GitHub Copilot, DeepSeek), improving provider abstraction.
- **#5288** (Re-bin) — Integration of Agent Plugins with CLI Apps, advancing the plugin ecosystem.
- **#5299** (chengyongru) — Structured token usage records via new `/api/settings/usage/records` endpoint, directly addressing community demand for observability.

## 4. Community Hot Topics

| Issue / PR | Activity | Link |
|---|---|---|
| [#5266](https://github.com/HKUDS/nanobot/issues/5266) Token consumption logging | 13 comments, high engagement | [Issue](https://github.com/HKUDS/nanobot/issues/5266) |
| [#5305](https://github.com/HKUDS/nanobot/issues/5305) & [#5306](https://github.com/HKUDS/nanobot/issues/5306) exec.allowPatterns bypass | 0 comments each but severity-critical | [5305](https://github.com/HKUDS/nanobot/issues/5305) · [5306](https://github.com/HKUDS/nanobot/issues/5306) |
| [#5295](https://github.com/HKUDS/nanobot/issues/5295) Docker Compose deployment failure | 5 comments, deployment-blocking | [Issue](https://github.com/HKUDS/nanobot/issues/5295) |
| [#5311](https://github.com/HKUDS/nanobot/issues/5311) Agnes AI double-encoding bug | Reported today, 0 comments | [Issue](https://github.com/HKUDS/nanobot/issues/5311) |

**Analysis:**
- **Token observability (#5266)** is the most discussed open topic. Users are burning large token counts (reported: ~1M tokens in 2 hours) during idle periods, signaling potential runaway agent loops or memory-compaction overhead. The companion PR #5299 (structured token usage records) is a direct response to this need.
- **Security advisories (#5305, #5306)** from researcher YLChen-007 describe shell-chain bypasses in the `exec` tool's allowlist. These are high-severity and affect any deployment exposing the OpenAI-compatible API with `exec` enabled.
- **Docker deployment friction (#5295)** suggests documentation or packaging gaps — a permission error on `entrypoint.sh` is a common Docker volume-bind issue that may need a fix in the image or updated deployment instructions.

## 5. Bugs & Stability

**Severity-ranked bugs reported:**

| # | Severity | Description | Fix PR? | Link |
|---|---|---|---|---|
| #5305 / #5306 | **Critical** | `exec.allowPatterns` allowlist bypass enables chained shell command execution | Not yet | [5305](https://github.com/HKUDS/nanobot/issues/5305) · [5306](https://github.com/HKUDS/nanobot/issues/5306) |
| #5295 | **High** | Docker Compose deployment fails with `entrypoint.sh: Permission denied` | Not yet | [Issue](https://github.com/HKUDS/nanobot/issues/5295) |
| #5311 | **High** | Agnes AI custom provider double-encodes nested-object MCP tool arguments | Not yet | [Issue](https://github.com/HKUDS/nanobot/issues/5311) |
| #5271 | **Critical** | Stale background tasks overwrite session data (P0) | PR #5271 open | [PR](https://github.com/HKUDS/nanobot/pull/5271) |
| #5302 | **Medium** | Dream consolidation uses wrong tool registry (prompt/tool mismatch) | PR #5302 open | [PR](https://github.com/HKUDS/nanobot/pull/5302) |
| #5156 | **Medium** | Telegram polling silently stalls after network blips | PR #5156 open (related: #5301) | [PR](https://github.com/HKUDS/nanobot/pull/5156) |
| #5303 | **Low** | Weather skill uses bare `curl` which resolves to PowerShell alias on Windows | PR #5303 open | [PR](https://github.com/HKUDS/nanobot/pull/5303) |
| #5309 | **Low** | Marketplace skills cannot shadow builtins due to loader bug | PR #5309 open | [PR](https://github.com/HKUDS/nanobot/pull/5309) |

**Notable:** The two security issues (#5305/#5306) are unaddressed with no fix PR yet. The P0 session-race bug (#5271) has an open fix PR but carries a conflict tag, suggesting merge friction. The Telegram stalled-polling issue (#5156) is part of an ongoing reliability effort with PR #5301 adding lightweight liveness checks.

## 6. Feature Requests & Roadmap Signals

| Request | Source | Likelihood for Next Release |
|---|---|---|
| Token usage observability (per-call logging + API records) | #5266 (user), #5299 (committer) | **High** — PR #5299 is already in review |
| Structured Responses provider abstraction | #5204 | **High** — P1 refactor, likely in next minor |
| Computer-use / browser automation as native tools | #4276 | **Medium** — Draft PR with conflicts, long backlog |
| Agent Plugin v1 + CLI App integration | #5288 | **Medium** — Architectural change, needs testing |
| GitAgent Protocol (agent.yaml / SOUL.md) | #4019 | **Low** — Already merged but niche standard |
| `nanobot api status` for externally-managed servers | #5255 | **Low** — Draft, conflicts present |
| Forced QR login for WeChat channel | #5310 | **Medium** — Bugfix-quality feature, likely quick merge |

**Signal:** The project is clearly prioritizing **provider abstraction**, **observability**, and **plugin portability**. The P0/P1 PRs suggest the next release will focus on stability and infrastructure rather than user-facing features.

## 7. User Feedback Summary

- **Token burn anxiety is real.** Issue #5266 reflects genuine frustration: users report massive token consumption (millions in hours) during apparently idle periods. This points to potential issues in memory compaction, background agent loops, or unnecessary context buildup. Users need visibility into per-call token costs to diagnose and control spend.
- **Deployment is friction-heavy.** The Docker Compose permission error (#5295) is a newcomer barrier — users following official docs hit a hard fail. This suggests the Dockerfile or `entrypoint.sh` packaging needs a fix.
- **Custom provider integration has rough edges.** The Agnes AI double-encoding bug (#5311) indicates that the custom-provider path for MCP tool arguments may not properly handle nested JSON structures, a problem that likely affects other non-official providers as well.
- **Security-conscious users are watching.** The dual security advisories from a single researcher (YLChen-007) suggest the community is actively auditing the `exec` tool, and trust in the allowlist mechanism has been broken.
- **Telegram reliability remains a pain point.** The stalled-polling issue (#5156) and its follow-up (#5301) show that Telegram users experience silent failures that are hard to diagnose, degrading trust in the channel.

## 8. Backlog Watch

| Item | Age | Risk | Link |
|---|---|---|---|
| **#4276** — Model-agnostic computer use tools | ~2 months open, has conflicts | Feature stalled by merge conflicts; high community interest | [PR](https://github.com/HKUDS/nanobot/pull/4276) |
| **#5255** — Truthful API service status / `nanobot api status` | Draft, has conflicts | Useful diagnostic feature blocked by conflicts | [PR](https://github.com/HKUDS/nanobot/pull/5255) |
| **#5305 / #5306** — exec.allowPatterns security bypasses | Reported 2026-08-09, **no fix PR** | Critical security; no maintainer response visible | [5305](https://github.com/HKUDS/nanobot/issues/5305) · [5306](https://github.com/HKUDS/nanobot/issues/5306) |
| **#5295** — Docker Compose entrypoint permission denied | Reported 2026-08-08, no fix | Blocks new deployments; likely a quick fix | [Issue](https://github.com/HKUDS/nanobot/issues/5295) |
| **#5311** — Agnes AI double-encoding | Reported today, no fix | Affects custom-provider users; may be wider | [Issue](https://github.com/HKUDS/nanobot/issues/5311) |
| **#5271** — P0 stale session save race | Open with conflict tag | Critical bug with a fix PR that needs conflict resolution | [PR](https://github.com/HKUDS/nanobot/pull/5271) |

**Maintainer attention priority:** The two unaddressed security advisories (#5305/#5306) should be the top priority, followed by resolving the conflict on the P0 session fix (#5271). The Docker deployment issue (#5295) is a quick win that would improve new-user experience significantly.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-10

## 1. Today's Overview

Hermes Agent is in an intense stabilization sprint: 50 issues and 50 PRs touched in the last 24 hours with zero new releases, signaling that the maintainer team is prioritizing bug fixes and security patches over feature shipping. The project shows healthy contributor engagement (46 open PRs, frequent multi-author contributions) but carries concerning severity — two P0/critical bugs reported today alone (silent message deletion and a near-disastrous Windows terminal escalation). The dominant theme is **session-state reliability** and **security hardening**, with at least a dozen PRs targeting SSRF, credential leakage, and multi-profile auth isolation.

## 2. Releases

No new releases in the reporting window. The last tagged release referenced in issues is **v0.20.0 (2026.8.3)**; several open issues reference this version, suggesting the current release train is behind the pace of bug discovery.

## 3. Project Progress

### Merged / Closed PRs Today
| PR | Summary | Link |
|---|---|---|
| [#82873](https://github.com/NousResearch/hermes-agent/pull/82873) | Bypass `read_file` dedup in `execute_code` sandbox — fixes inconsistent content response schema for programmatic callers | [PR #82873](https://github.com/NousResearch/hermes-agent/pull/82873) |
| [#43819](https://github.com/NousResearch/hermes-agent/pull/43819) | Share one SQLite connection per holographic memory store database with refcounted `close()` — reduces connection churn in memory plugin | [PR #43819](https://github.com/NousResearch/hermes-agent/pull/43819) |
| [#77992](https://github.com/NousResearch/hermes-agent/pull/77992) | Gate OS-specific tests by real host; add macOS + Windows CI lanes — eliminates false-positive test results from `sys.platform` patching | [PR #77992](https://github.com/NousResearch/hermes-agent/pull/77992) |

### Notable Open PRs Advanced
- **[PR #82592](https://github.com/NousResearch/hermes-agent/pull/82592)** — Fixes frozen-preview finals and dropped idle-session delegation callbacks in the relay gateway; live-verified on a 4-box staging fleet.
- **[PR #81407](https://github.com/NousResearch/hermes-agent/pull/81407)** — SSRF protection for monitor-mode cron jobs; preserves source-byte identity across concurrent edits.
- **[PR #78490](https://github.com/NousResearch/hermes-agent/pull/78490)** — Structural redaction fix for full dotted-body prefixed credentials (builds on #78138).
- **[PR #80238](https://github.com/NousResearch/hermes-agent/pull/80238)** / **[PR #80360](https://github.com/NousResearch/hermes-agent/pull/80360)** — Isolate `_auth_env` under multiplex to prevent cross-profile allowlist leakage (#80026).

## 4. Community Hot Topics

### Most Commented Issues
| Issue | Comments | Severity | Topic | Link |
|---|---|---|---|---|
| [#63047](https://github.com/NousResearch/hermes-agent/issues/63047) | 19 | P1 | macOS Desktop complete freeze after ~5 messages | [Issue #63047](https://github.com/NousResearch/hermes-agent/issues/63047) |
| [#26689](https://github.com/NousResearch/hermes-agent/issues/26689) | 13 | P3 | VoiceOver / screen-reader accessibility for blind users | [Issue #26689](https://github.com/NousResearch/hermes-agent/issues/26689) |
| [#66824](https://github.com/NousResearch/hermes-agent/issues/66824) | 6 | P2 | `cronjob create repeat='forever'` TypeError | [Issue #66824](https://github.com/NousResearch/hermes-agent/issues/66824) |
| [#71987](https://github.com/NousResearch/hermes-agent/issues/71987) | 6 | P2 | Same cronjob TypeError (duplicate) | [Issue #71987](https://github.com/NousResearch/hermes-agent/issues/71987) |

**Analysis:** The top issue (#63047) reveals a severe macOS Desktop stability regression that blocks core usage. The accessibility issue (#26689), while lower priority, highlights an underserved user segment and a gap in UX audit scope. The duplicated cronjob TypeError (#66824 / #71987) points to a type-coercion bug in the scheduler that has persisted across multiple reports.

### Reactions
- [#26689](https://github.com/NousResearch/hermes-agent/issues/26689) — 1 👍 (accessibility)
- [#15831](https://github.com/NousResearch/hermes-agent/issues/15831) — 1 👍 (cron job chaining feature request)

## 5. Bugs & Stability

### Critical / P0 (Reported Today)
| Issue | Severity | Summary | Fix PR? | Link |
|---|---|---|---|---|
| [#82842](https://github.com/NousResearch/hermes-agent/issues/82842) | **Critical** | Agent executed `rd /s /q` against `C:\` drive root after scoped folder-deletion approval — prevented only by non-admin process | None yet | [Issue #82842](https://github.com/NousResearch/hermes-agent/issues/82842) |
| [#82756](https://github.com/NousResearch/hermes-agent/issues/82756) | **P0** | Desktop plain-Enter submit silently deleted ~65 messages (3rd occurrence; `truncate_before_user_ordinal` + `confirm_truncate` race) | None yet | [Issue #82756](https://github.com/NousResearch/hermes-agent/issues/82756) |

### High-Severity P1 / P2
| Issue | Severity | Summary | Fix PR? | Link |
|---|---|---|---|---|
| [#63047](https://github.com/NousResearch/hermes-agent/issues/63047) | P1 | macOS Desktop unresponsive after ~5 messages; Settings locked out | None yet | [Issue #63047](https://github.com/NousResearch/hermes-agent/issues/63047) |
| [#80125](https://github.com/NousResearch/hermes-agent/issues/80125) | P2 | WeChat adapter misreports `ret=-2` as rate-limit; hides missing `context_token` | None yet | [Issue #80125](https://github.com/NousResearch/hermes-agent/issues/80125) |
| [#82872](https://github.com/NousResearch/hermes-agent/issues/82872) | P2 | `ws_orphan_reap` sessions restore as unclickable ghost tiles on Desktop restart | None yet | [Issue #82872](https://github.com/NousResearch/hermes-agent/issues/82872) |
| [#77211](https://github.com/NousResearch/hermes-agent/issues/77211) | P2 | `hermes update` skips Node.js dependency refresh on already-current checkout | None yet | [Issue #77211](https://github.com/NousResearch/hermes-agent/issues/77211) |
| [#75097](https://github.com/NousResearch/hermes-agent/issues/75097) | P2 | Iteration budget: AIAgent defaults to 90 but `execute_code` refunds only one limiter | None yet | [Issue #75097](https://github.com/NousResearch/hermes-agent/issues/75097) |
| [#78190](https://github.com/NousResearch/hermes-agent/issues/78190) | P2 | Gmail MCP OAuth works in CLI but gateway fails with `OAuthRegistrationError: 404 /register` | None yet | [Issue #78190](https://github.com/NousResearch/hermes-agent/issues/78190) |
| [#82846](https://github.com/NousResearch/hermes-agent/issues/82846) | P2 | Smart-approval auxiliary LLM call has no timeout — wedges session indefinitely | [PR #82846](https://github.com/NousResearch/hermes-agent/pull/82846) open | [Issue #82846](https://github.com/NousResearch/hermes-agent/issues/82846) |
| [#82798](https://github.com/NousResearch/hermes-agent/issues/82798) | P2 | `skills_guard` `hardcoded_secret` regex flags `__PLACEHOLDER__` tokens as CRITICAL | None yet | [Issue #82798](https://github.com/NousResearch/hermes-agent/issues/82798) |
| [#82831](https://github.com/NousResearch/hermes-agent/issues/82831) | P2 | `normalize_usage` returns 0 for reasoning tokens when provider returns dict instead of object | None yet | [Issue #82831](https://github.com/NousResearch/hermes-agent/issues/82831) |
| [#82805](https://github.com/NousResearch/hermes-agent/issues/82805) | P2 | Intermittent empty-bodied 400 from local llama.cpp; pooled httpx reuses closed connection | [PR #82809](https://github.com/NousResearch/hermes-agent/pull/82809) open | [Issue #82805](https://github.com/NousResearch/hermes-agent/issues/82805) |
| [#82770](https://github.com/NousResearch/hermes-agent/issues/82770) | P2 | Test sessions leak into production `state.db` (700+ junk open rows) | None yet | [Issue #82770](https://github.com/NousResearch/hermes-agent/issues/82770) |
| [#82875](https://github.com/NousResearch/hermes-agent/issues/82875) | P2 | `reasoning_effort` silently dropped for named `providers:` endpoints | None yet | [Issue #82875](https://github.com/NousResearch/hermes-agent/issues/82875) |
| [#79336](https://github.com/NousResearch/hermes-agent/issues/79336) | P3 | `godmode` refusal detection misses curly-quote refusals (U+2019) | None yet | [Issue #79336](https://github.com/NousResearch/hermes-agent/issues/79336) |
| [#46064](https://github.com/NousResearch/hermes-agent/issues/46064) | P3 | OpenRouter router models silently dropped from `hermes model` picker | None yet | [Issue #46064](https://github.com/NousResearch/hermes-agent/issues/46064) |
| [#80841](https://github.com/NousResearch/hermes-agent/issues/80841) | P2 | Fastmail `delete_event` confirmation widget cannot complete from CLI/TUI/Matrix | None yet | [Issue #80841](https://github.com/NousResearch/hermes-agent/issues/80841) |
| [#79518](https://github.com/NousResearch/hermes-agent/issues/79518) | P3 | Hidden tab strip is inescapable dead end for chat tabs on Desktop | None yet | [Issue #79518](https://github.com/NousResearch/hermes-agent/issues/79518) |
| [#82851](https://github.com/NousResearch

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-10

---

## 1. Today's Overview

PicoClaw shows moderate but focused activity with 3 issues and 6 pull requests updated in the last 24 hours. No new releases were published today. The day's activity is dominated by a consolidated SSRF hardening effort across multiple messaging channels (Weixin, WeCom, and generic channels), alongside a documentation refactor of the Deltachat bridge. One bug was resolved (stale Matrix sync loop), and one lockfile fix was merged. The project is in a stable maintenance rhythm with no release momentum visible this cycle.

**Activity Assessment:** ⚖️ Moderate — security patches and refactors outweigh feature development today.

---

## 2. Releases

No new releases published in the reporting window.

---

## 3. Project Progress

**Merged / Closed Today:**

| PR | Author | Summary |
|----|--------|---------|
| [#3326](https://github.com/sipeed/picoclaw/pull/3326) | As-tsaqib | Fixed duplicate `semver@7.8.5` entries in `web/frontend/pnpm-lock.yaml` that caused `pnpm install --frozen-lockfile` to fail with `ERR_PNPM_BROKEN_LOCKFILE`. |
| [#3203](https://github.com/sipeed/picoclaw/issues/3203) | weissfl | Closed (stale) — Matrix `/sync` loop reconnection bug remains unresolved in code; issue closed without a merge. |

**Key Open Work:**

- **[#3322](https://github.com/sipeed/picoclaw/pull/3322)** — SSRF hardening for inbound media downloads across QQ, Telegram, Discord, LINE, and Slack channels.
- **[#3323](https://github.com/sipeed/picoclaw/pull/3323)** — Same hardening applied to WeCom (`CreateSafeHTTPClient` + `ValidateSafeHTTPURL`).
- **[#3324](https://github.com/sipeed/picoclaw/pull/3324)** — Identical fix for Weixin (WeChat) media download path.
- **[#3222](https://github.com/sipeed/picoclaw/pull/3222)** — Deltachat bridge cleanup: -200 LOC, dropped legacy features, password-based email config removed, secrets now jsonrpc-only, invite-link API renamed.

---

## 4. Community Hot Topics

| Item | Type | Author | Comments | 👍 | Link |
|------|------|--------|----------|-----|------|
| Matrix sync loop dies silently | Bug | weissfl | 8 | 2 | [#3203](https://github.com/sipeed/picoclaw/issues/3203) |
| Long IRC messages not cohesive | Feature | superuser-does | 4 | 0 | [#3287](https://github.com/sipeed/picoclaw/issues/3287) |
| Telegram table rendering | Feature | As-tsaqib | 0 | 0 | [#3325](https://github.com/sipeed/picoclaw/issues/3325) |
| SSRF in media downloads | Security | SashaMIT | — | 0 | [#3322](https://github.com/sipeed/picoclaw/pull/3322) |

**Analysis:**

- **Matrix reconnection** is the most discussed issue (8 comments, 2 upvotes) but was closed as stale without a fix — a signal that long-polling resilience is an ongoing community pain point, especially for users running PicoClaw via systemd in unreliable network conditions.
- **IRC long-message support** reflects a genuine protocol gap: IRCv3 split messages are reassembled client-side, but PicoClaw treats each fragment independently.
- **Telegram tables** is a fresh request (0 comments) but already has a paired PR [#3327](https://github.com/sipeed/picoclaw/pull/3327) from the same author, indicating fast-tracked interest.
- The **SSRF media downloads** cluster (3 PRs) shows a coordinated security review rather than isolated bug reports — a positive sign of proactive hardening.

---

## 5. Bugs & Stability

| Severity | Item | Status | Fix PR |
|----------|------|--------|--------|
| 🔴 High | Matrix `/sync` loop permanent death after network/server disruption; systemd `Restart=on-failure` does not trigger | Closed (stale, unfixed) | — |
| 🟡 Medium | `pnpm install --frozen-lockfile` broken by duplicate lockfile entries | **Fixed** (PR #3326 merged) | [#3326](https://github.com/sipeed/picoclaw/pull/3326) |
| 🟡 Medium | SSRF via redirect to loopback/private hosts on WeCom/Weixin media downloads | Open | [#3323](https://github.com/sipeed/picoclaw/pull/3323), [#3324](https://github.com/sipeed/picoclaw/pull/3324) |
| 🟡 Medium | SSRF on inbound media for QQ/Telegram/Discord/LINE/Slack | Open | [#3322](https://github.com/sipeed/picoclaw/pull/3322) |

**Note:** The Matrix reconnection bug ([#3203](https://github.com/sipeed/picoclaw/issues/3203)) remains the most impactful outstanding stability issue. Its stale closure without a fix is a risk for production deployments.

---

## 6. Feature Requests & Roadmap Signals

| Request | Author | Link | Likelihood for Next Release |
|---------|--------|------|----------------------------|
| Native Telegram table rendering via Bot API rich messages | As-tsaqib | [#3325](https://github.com/sipeed/picoclaw/issues/3325) / [#3327](https://github.com/sipeed/picoclaw/pull/3327) | **High** — paired PR already open, same author, uses existing Telegram API features |
| IRC long-message reassembly (IRCv3) | superuser-does | [#3287](https://github.com/sipeed/picoclaw/issues/3287) | **Medium** — no PR yet, 4 comments, low engagement |
| Deltachat bridge simplification (no password config, cleaner API) | trufae | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | **High** — large refactor already in flight, likely to land soon |

**Signal:** The project is trending toward **security hardening** (SSRF fixes) and **channel-specific UI polish** (Telegram tables), rather than new channel integrations.

---

## 7. User Feedback Summary

- **Frustration with silent failures:** The Matrix sync loop bug ([#3203](https://github.com/sipeed/picoclaw/issues/3203)) highlights a critical UX gap — PicoClaw stays alive but stops working after disruptions, with no visible error and no auto-restart. Users running it as a systemd service are especially affected.
- ** IRC users hit the 512-byte wall:** Long messages are fragmented and lose context, making PicoClaw unsuitable for technical discussions that require code blocks or long quotes over IRC.
- ** Telegram table rendering is a quality-of-life gap:** Structured Markdown tables degrade to monospaced blocks instead of using Telegram's native table UI, reducing readability.
- **Security-conscious users appreciate the SSRF work:** Multiple PRs from SashaMIT addressing redirect-based SSRF in media downloads suggest an active, security-aware user base.
- **Deltachat users want a cleaner config model:** Removing password-based email setup in favor of jsonrpc secrets simplifies deployment for security-focused users.

---

## 8. Backlog Watch

| Item | Age | Author | Link | Risk |
|------|-----|--------|------|------|
| Matrix sync loop reconnection | ~39 days | weissfl | [#3203](https://github.com/sipeed/picoclaw/issues/3203) | 🔴 High — closed stale but unfixed; affects production reliability |
| IRC long-message reassembly | ~19 days | superuser-does | [#3287](https://github.com/sipeed/picoclaw/issues/3287) | 🟡 Medium — no PR, low engagement |
| Deltachat bridge refactor | ~38 days | trufae | [#3222](https://github.com/sipeed/picoclaw/pull/3222) | 🟡 Medium — large PR, needs review bandwidth |

**Recommendation:** The Matrix reconnection bug should be reopened or tracked explicitly. Its stale closure risks losing a high-impact fix that affects users in low-connectivity or unstable-network environments.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-10

## 1. Today's Overview

NanoClaw shows sustained development momentum with **16 open pull requests** and **1 active issue** as of today, all updated within the last 24 hours. No new releases were published, indicating the project is in a code-review and refinement phase rather than a release cycle. The PR backlog spans a broad range of concerns — from security hardening and container infrastructure to channel integrations and internal refactors — suggesting a healthy multi-threaded development effort. Contributor activity is concentrated among a small core group (zvi-fried, gabi-simons, stumpjumper, OmriBenShoham, brentkearney, ariel-greenfeld, ira-at-work), with zvi-fried leading on refactors and documentation.

## 2. Releases

**No new releases today.** The project has no recent version bumps on record. The absence of a release combined with 16 open PRs suggests the team is accumulating changes for a forthcoming release, likely gated on security review (CVE gates) and the pending hardened-image limitations.

## 3. Project Progress

**Merged / closed today:** None.

**PRs actively advancing (all 16 remain open):**

- **#3208** — `feat(ci): publish agent image to Docker Hub with CVE gates` ([link](https://github.com/nanocoai/nanoclaw/pull/3208)): Adds a multi-arch (amd64 + arm64 via QEMU) publish workflow for the agent image, plus a grype-based CVE gate. This is a critical infrastructure improvement that directly addresses image security transparency.
- **#3207** — `fix(container): bump pnpm and npm past fixable-critical tar CVE` ([link](https://github.com/nanocoai/nanoclaw/pull/3207)): Responds to grype flagging GHSA-23hp-3jrh-7fpw (critical, `tar` < 7.5.19) in both the base image's npm and pnpm's vendored tar. Two separate bump paths are needed, indicating the CVE is embedded in multiple dependency layers.
- **#3218** — `feat(cli): accept bounded JSON from stdin` ([link](https://github.com/nanocoai/nanoclaw/pull/3218)): Introduces `--stdin-json` input mode for both host and container `ncl` clients, enabling structured argument passing without modifying the request frame or daemon dispatcher.
- **#3215** — `fix(permissions): redact DM resolution logs` ([link](https://github.com/nanocoai/nanoclaw/pull/3215)): Security/privacy fix addressing exposure of DM resolution data in logs.
- **#3209** — `fix(slack): surface pasted tables to the agent` ([link](https://github.com/nanocoai/nanoclaw/pull/3209)): Slack channel quality-of-life fix for table content.
- **#3041 / #3050** — `feat(channels): add Dial channel adapter (SMS + AI voice calls)` and wizard integration ([link 1](https://github.com/nanocoai/nanoclaw/pull/3041), [link 2](https://github.com/nanocoai/nanoclaw/pull/3050)): Adds a new voice/SMS channel, expanding NanoClaw's reach beyond messaging apps.
- **#3214 / #3213 / #3212 / #3186** — Series of refactors by zvi-fried covering module lifecycle hooks, question renderer registration, DB migration registry, and host seams for skill-owned capabilities. These are foundational improvements that decouple skills from the host core.
- **#3216 / #3211 / #3210** — Documentation PRs clarifying `install_packages` limitations, skill integration rules, and container attachment paths.

## 4. Community Hot Topics

The most discussed topics today cluster around **hardened-image limitations** and **attachment delivery reliability**:

| Item | Type | Link | Signals |
|------|------|------|---------|
| **#3217** — `install_packages` lacks pip channel | Issue | [link](https://github.com/nanocoai/nanoclaw/issues/3217) | Blocks hardened-image adoption for Python-dependent agents |
| **#3216** — Docs note on apt/npm-only limitation | PR | [link](https://github.com/nanocoai/nanoclaw/pull/3216) | Direct response to #3217; acknowledges a real gap |
| **#2529 / #3142** — Attachment forwarding bugs | PRs | [link #2529](https://github.com/nanocoai/nanoclaw/pull/2529), [link #3142](https://github.com/nanocoai/nanoclaw/pull/3142) | Two separate PRs (Signal and general inbox) addressing the same class of problem: attachments dropped or inaccessible to agents |

**Underlying need:** Users running Python-dependent agent toolchains want to leverage the hardened prebuilt image but are blocked by the absence of a pip installation path. This is both a functional gap and a security-adoption friction point — users must choose between hardening and Python flexibility. The attachment bugs suggest the container mounting strategy needs a more robust design rather than ad-hoc path splicing.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Link | Fix PR? |
|----------|-----------|-------------|------|---------|
| **High** | #3217 / #3216 | `install_packages` cannot install Python packages, preventing hardened-image use for pip-dependent agents | [Issue](https://github.com/nanocoai/nanoclaw/issues/3217), [PR](https://github.com/nanocoai/nanoclaw/pull/3216) | Partially — docs updated, but no code fix yet |
| **High** | #3142 | Signal adapter writes attachment paths that are never mounted into the agent container; Read tool fails on PDFs, text files, documents | [PR](https://github.com/nanocoai/nanoclaw/pull/3142) | Yes — PR #3142 in review |
| **High** | #2529 | Inbound attachments delivered to agent instead of being dropped (regression or fix?) | [PR](https://github.com/nanocoai/nanoclaw/pull/2529) | Yes —PR #2529 in review |
| **Medium** | #3207 | Critical CVE (GHSA-23hp-3jrh-7fpw) in vendored `tar` via npm and pnpm in agent image | [PR](https://github.com/nanocoai/nanoclaw/pull/3207) | Yes — PR #3207 in review |
| **Low** | #3209 | Slack pasted tables not surfaced to agent | [PR](https://github.com/nanocoai/nanoclaw/pull/3209) | Yes — PR #3209 in review |
| **Medium** | #3215 | DM resolution logs leak sensitive data | [PR](https://github.com/nanocoai/nanoclaw/pull/3215) | Yes — PR #3215 in review |

The attachment-forwarding bugs (#2529, #3142) represent a systemic issue in how the containerized agent receives files from channels. Two independent PRs address different aspects, but neither has landed yet. The CVE in the base image toolchain (#3207) is blocking clean security scans and is critical for production deployments.

## 6. Feature Requests & Roadmap Signals

| Request | Source | Link | Likelihood in Next Release |
|---------|--------|------|---------------------------|
| **pip channel for `install_packages`** | Issue #3217 | [link](https://github.com/nanocoai/nanoclaw/issues/3217) | **High** — directly blocks hardened-image adoption; a core-user ask |
| **Dial channel (SMS + AI voice)** | PRs #3041, #3050 | [link 1](https://github.com/nanocoai/nanoclaw/pull/3041), [link 2](https://github.com/nanocoai/nanoclaw/pull/3050) | **Medium-High** — feature-complete in PR, awaiting review |
| **Bounded JSON stdin input** | PR #3218 | [link](https://github.com/nanocoai/nanoclaw/pull/3218) | **Medium** — utility feature, no blocking concerns |
| **Docker Hub multi-arch publish with CVE gates** | PR #3208 | [link](https://github.com/nanocoai/nanoclaw/pull/3208) | **High** — operational necessity for a hardened-image project |
| **Skill-owned capability seams** | PR #3186 | [link](https://github.com/nanocoai/nanoclaw/pull/3186) | **Medium** — architectural enabler, likely ships with the refactor batch |

**Roadmap signal:** The project is clearly investing in **security-hardened image distribution** (CVE gates, pnpm/npm bumps, docs on limitations) and **channel expansion** (Dial/SMS/voice). The `install_packages` pip gap is the most visible user-facing limitation and likely the highest-impact fix for the next release.

## 7. User Feedback Summary

- **Pain point — Hardened image unusable for Python agents:** The #3217 issue captures a real blocker. Users who want the security benefits of the hardened prebuilt image cannot use it when their agents depend on pip-installed tools. This forces a choice between security and functionality.
- **Pain point — Attachments silently lost:** Multiple users report that file/image attachments from Signal (and potentially other channels) are unreachable inside the agent container. This is a trust-eroding bug for any workflow involving document processing.
- **Satisfaction signal — Active security响应:** The team is quickly publishing CVE-related PRs (#3207, #3208) and documenting known limitations (#3216). The openness about the apt/npm-only gap in #3216 builds credibility even though the fix isn't yet in place.
- **Satisfaction signal — Refactor momentum:** The sustained refactor effort (lifecycle hooks, migration registry, host seams) indicates the team is investing in long-term maintainability, which is a positive signal for project health.

## 8. Backlog Watch

| Item | Age | Priority | Link | Risk |
|------|-----|----------|------|------|
| **#2529** — Attachment delivery fix | ~2 months (created 2026-05-18) | High | [link](https://github.com/nanocoai/nanoclaw/pull/2529) | Stale PR risks losing review context; attachment bug persists for users |
| **#3142** — Signal attachment path fix | ~2 weeks | High | [link](https://github.com/nanocoai/nanoclaw/pull/3142) | Recent but still open; dual-PR situation on same problem class needs triage |
| **#3217** — pip channel for install_packages | ~1 day (new) | High | [link](https://github.com/nanocoai/nanoclaw/issues/3217) | No fix PR yet; docs PR #3216 is a stopgap |
| **#3041 / #3050** — Dial channel | ~1 month | Medium | [links](https://github.com/nanocoai/nanoclaw/pull/3041) | Feature PRs awaiting review; channel expansion blocked |

**Maintainer attention needed:** The two attachment-related PRs (#2529 and #3142) should be consolidated or prioritized — they address overlapping root causes. The pip channel gap (#3217) has no code fix in progress and should be scoped for the next release. The older PRs (#2529 in particular) are at risk of review drift after ~2 months.

---

*Digest generated from GitHub data for nanocoai/nanoclaw on 2026-08-10. All links reference the upstream repository.*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-10

## 1. Today's Overview

IronClaw remains highly active with 22 issues and 32 PRs updated in the last 24 hours, reflecting sustained development velocity on the Reborn platform. Seven issues were closed today, including critical QA bugs around Slack DM reading, tool runtime failures, and chat history persistence. A new high-severity bug (#7400) was filed involving zombie threads on the Responses API when using streaming with caller tools. No new releases were published this cycle, suggesting the team is still hardening the 1.1.x line before the next tag.

## 2. Releases

No new releases were published in this reporting window.

## 3. Project Progress

**Closed/Merged Today:**
- [#7171](https://github.com/nearai/ironclaw/pull/7171) — Fixed broken skill installation: skills previously became invisible after install. Now uses a DB-backed tree per skill mount, making skill commands directly runnable. Part of epic #6941.
- [#7387](https://github.com/nearai/ironclaw/pull/7387) — Dependabot batch: bumped 12 packages including `base64` 0.22→0.23, `toml` 1.1.3→1.1.4, and `rstest`.
- [#7022](https://github.com/nearai/ironclaw/pull/7022) — Dependabot actions bump: `actions/setup-node` 4.0.2→7.0.0, `docker/login-action` update.

**Key Open PRs Advancing:**
- [#7411](https://github.com/nearai/ironclaw/pull/7411) — Makes deferred-tool retrieval a swappable provider, following the seam established in PR #6345 for memory.
- [#7410](https://github.com/nearai/ironclaw/pull/7410) — Returns bounded complete signatures for `tool_search` results (Phase 1 of #7405).
- [#7409](https://github.com/nearai/ironclaw/pull/7409) — Establishes tool-retrieval baselines at 100–1,000 tools for regression tracking.
- [#7398](https://github.com/nearai/ironclaw/pull/7398) — Adds browser push notifications (W3C Web Push) as a first-party notification channel, parity with Slack/Telegram.
- [#7396](https://github.com/nearai/ironclaw/pull/7396) — Generic progressive previews for Slack and Telegram channels.
- [#7395](https://github.com/nearai/ironclaw/pull/7395) — Fixes TOCTOU race in outbound send-claim handling and allows failed-row reopen.

## 4. Community Hot Topics

| Issue | Comments | Highlights |
|-------|----------|------------|
| [#7405](https://github.com/nearai/ironclaw/issues/7405) — Improve deferred tool discovery | 2 | Signals demand for better tool-catalog UX at scale; reduces avoidable model turns |
| [#7407](https://github.com/nearai/ironclaw/issues/7407) — Execute BatchPolicy::Parallel concurrently | 2 | Performance bottleneck: parallel batch policy is computed but not executed concurrently |
| [#7400](https://github.com/nearai/ironclaw/issues/7400) — Zombie threads on stream + tools | 2 | Critical: 100% reproducible on 1.1.0-rc.1 and 1.1.0; permanently undeletable threads |
| [#7346](https://github.com/nearai/ironclaw/issues/7346) — Emoji shortcodes as plain text | 2 | UX regression; breaks message rendering across all channels |
| [#7348](https://github.com/nearai/ironclaw/issues/7348) — Activity timeline out of order | 2 | Long-running tasks show confused execution timeline in UI |
| [#7349](https://github.com/nearai/ironclaw/issues/7349) — Run history lost on refresh | 2 | Data persistence concern for multi-step automations |

**Underlying needs:** The community is pressing on three fronts — (1) tool discovery efficiency at scale, (2) parallel execution performance, and (3) UI fidelity (emoji rendering, chronological ordering, history persistence). The zombie-thread issue (#7400) is the most urgent reliability concern.

## 5. Bugs & Stability

**High Severity:**
- [#7400](https://github.com/nearai/ironclaw/issues/7400) — `stream: true` + caller `tools[]` on `/api/v1/responses` leaves permanently undeletable "zombie" threads. Affects all 1.1.0 and 1.1.0-rc.1 deployments. **No fix PR yet.**

**Medium Severity (Bug Bash P2):**
- [#7346](https://github.com/nearai/ironclaw/issues/7346) — Emoji shortcodes (`:wave:`, `:smile:`) rendered as raw text instead of characters.
- [#7348](https://github.com/nearai/ironclaw/issues/7348) — Activity blocks and progress messages displayed out of chronological order.
- [#7349](https://github.com/nearai/ironclaw/issues/7349) — Chat run history partially disappears on page refresh after long tasks.
- [#7345](https://github.com/nearai/ironclaw/issues/7345) — Agent reports 61 automations while UI shows only 50; state inconsistency.
- [#5882](https://github.com/nearai/ironclaw/issues/5882) — Repeated Slack reconnects leave auth flow broken; only recovery is reinstall.
- [#5878](https://github.com/nearai/ironclaw/issues/5878) — Revoked GitHub tokens produce misleading errors instead of re-auth prompt.
- [#6479](https://github.com/nearai/ironclaw/issues/6479) — Routines can create/modify other routines (self-replicating automation risk).
- [#6046](https://github.com/nearai/ironclaw/issues/6046) — Simple email-to-sheet workflow invokes 124 tools; severe tool over-invocation.
- [#5551](https://github.com/nearai/ironclaw/issues/5551) — Slack automations post intermediate progress instead of final results.

**Recently Closed:**
- [#7292](https://github.com/nearai/ironclaw/issues/7292) — Runner heartbeat error after tool install (closed).
- [#5522](https://github.com/nearai/ironclaw/issues/5522) — Reborn routine fails on Slack DM reading (closed).
- [#5552](https://github.com/nearai/ironclaw/issues/5552) — Generic "invalid result" after multiple tool failures (closed).
- [#5509](https://github.com/nearai/ironclaw/issues/5509) — Chat creation latency scales with history (closed).
- [#5510](https://github.com/nearai/ironclaw/issues/5510) — Cannot delete old routines (closed).
- [#4341](https://github.com/nearai/ironclaw/issues/4341) — THINKING CoT exposed to user (closed).
- [#4344](https://github.com/nearai/ironclaw/issues/4344) — Agent mirrors user message as its own response (closed).

## 6. Feature Requests & Roadmap Signals

- **#7405** / **#7407** — Deferred tool discovery with complete signatures and parallel batch execution. These are being actively worked (PRs #7411, #7410, #7409 stacked), suggesting the next release will include improved tool catalog performance.
- **#7392** — Experiment to replace first-party coding tools with pinned `omp` tool surface. Indicates a potential architectural shift in tooling contracts.
- **#7398** — Browser push notifications as a first-party channel. If merged, this extends IronClaw's notification surface beyond Slack/Telegram.
- **#7360** — Expand stress coverage for built-in and durable write paths. Signals investment in reliability testing infrastructure.
- **#7166** — Tool disclosure follow-up epic, now considered "safe, reliable, and efficient" as Reborn default. Suggests progressive disclosure is stable for 1.2.0.

**Predicted next-version features:** Parallel batch execution, swappable tool-search providers, bounded complete signatures, and browser push notifications are the strongest candidates for the upcoming release.

## 7. User Feedback Summary

Real user pain points this cycle center on **reliability and UX consistency**:

- **Tool over-invocation** (#6046): A simple email-to-sheet task firing 124 tools indicates the agent is not pruning irrelevant capabilities, frustrating users who expect focused execution.
- **State desynchronization** (#7345, #5882, #5551): Users report mismatched automation counts, broken Slack auth after reconnects, and intermediate messages posted to channels instead of final results — all eroding trust in automation reliability.
- **UI regressions** (#7346, #7348, #7349): Emoji rendering, timeline ordering, and history persistence on refresh are degrading the daily chat experience.
- **Error opacity** (#5552, #5878): Generic error messages ("invalid result", "provider temporarily unavailable") hide the actual cause, making troubleshooting difficult for end users.

Satisfaction signals are mixed: the Reborn platform's progressive tool disclosure (#7166) is rated as working well, and the skill mount fix (#7171) directly resolves a reported pain point. However, the volume of open P2 bugs from the bug bash suggests the pre-release quality bar needs raising.

## 8. Backlog Watch

| Issue | Age | Concern |
|-------|-----|---------|
| [#5882](https://github.com/nearai/ironclaw/issues/5882) — Slack reconnect auth broken | ~1 month | No fix PR; recurring auth flow regression affects multi-tenant deployments |
| [#5878](https://github.com/nearai/ironclaw/issues/5878) — Revoked GitHub token misleading errors | ~1 month | No fix PR; error handling gap for token lifecycle |
| [#6046](https://github.com/nearai/ironclaw/issues/6046) — 124-tool over-invocation | ~3 weeks | No fix PR; suggests missing capability pruning or scope discipline |
| [#6479](https://github.com/nearai/ironclaw/issues/6479) — Routine self-replication risk | ~3 weeks | Security concern; no guardrail implemented yet |
| [#5551](https://github.com/nearai/ironclaw/issues/5551) — Slack posts intermediate progress | ~5 weeks | No fix PR; affects automation output quality |
| [#7400](https://github.com/nearai/ironclaw/issues/7400) — Zombie threads on stream+tools | 1 day | High severity, no fix PR yet; requires urgent attention |

**Most concerning:** Issue #7400 (zombie threads) is both newly reported and high-severity with no fix in flight. Issues #5882 and #6046 have persisted for weeks without PRs and represent systemic gaps in auth resilience and tool selection discipline.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-10

## 1. Today's Overview

LobsterAI experienced **low development activity** on 2026-08-10, with zero merged/closed PRs and no new releases. The three most recently updated issues (all still open) reflect ongoing user-facing concerns around model configuration, context management, and cross-model subtask orchestration. Two of the three issues carry the `[stale]` label, suggesting they have seen little maintainer engagement for an extended period. The project appears to be in a **maintenance-mode lull** rather than an active development sprint.

---

## 2. Releases

No new releases were published in the last 24 hours. No version changes or migration notes to report.

---

## 3. Project Progress

- **Merged PRs today:** 0
- **Closed PRs today:** 0
- **Closed issues today:** 0

No code-level progress was recorded. Development activity was absent over the reporting window.

---

## 4. Community Hot Topics

| Issue | Title | Comments | 👍 | Link |
|-------|-------|----------|-----|------|
| #1187 | 建议在设置模型api的选项中增加上下文窗口大小设置和输出token设置 | 2 | 1 | [Issue #1187](https://github.com/netease-youdao/LobsterAI/issues/1187) |
| #2453 | 切换自定义模型，被系统定义为不许可？ | 1 | 0 | [Issue #2453](https://github.com/netease-youdao/LobsterAI/issues/2453) |
| #2132 | 跨模型子任务调用的问题 | 1 | 0 | [Issue #2132](https://github.com/netease-youdao/LobsterAI/issues/2132) |

**Underlying needs analysis:**
- **#1187** — Users are hitting `Context overflow` errors with deepseek and similar models, indicating a real gap in configurable context-window and output-token parameters. This is the most upvoted open issue and signals a demand for finer-grained model configuration control.
- **#2453** — A provider-parsing bug causes custom models with nested paths (e.g., `custom_1/openai/gpt-oss-20b:free`) to be misidentified as OpenAI, triggering permission/denial errors. This affects OpenRouter and NVIDIA model routes and disrupts session continuity.
- **#2132** — Cross-model subtask orchestration remains broken: gateway-level function calls (`call_function_…`) are not tracked in `sessions_list` or `subagents`, causing the parent task to lose visibility over child work. This is a structural gap in LobsterAI's multi-model agent architecture.

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **Medium** | [#2453](https://github.com/netease-youdao/LobsterAI/issues/2453) | Custom model provider parsing incorrectly extracts `openai` from nested paths, triggering a "not permitted" error. Recurs in same-thread model switching; absent in new threads with the same model. | None |
| **Medium** | [#2132](https://github.com/netease-youdao/LobsterAI/issues/2132) | Gateway-level function calls in cross-model subtask scenarios are invisible to the main session, breaking task synchronization and status tracking. | None |
| **Low** | [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) | No built-in UI option to set context window size or output token limits, leading to runtime `Context overflow` crashes. More of a missing-feature gap than a crash bug. | None |

No regressions were reported today. No fix PRs are attached to any of the above.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Request | Likelihood for Near-Term Roadmap |
|-------|---------|----------------------------------|
| [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) | Add configurable context-window size and output-token settings to model API options | **High** — Directly addresses a recurring overflow error; low implementation risk |
| [#2453](https://github.com/netease-youdao/LobsterAI/issues/2453) | Fix or generalize custom-model provider/path parsing logic | **Medium** — Bug-fix masquerading as a feature request; needs a parsing refactor |
| [#2132](https://github.com/netease-youdao/LobsterAI/issues/2132) | Native cross-model subtask orchestration with explicit notification/callback support | **Low–Medium** — Architecturally significant; would require changes to the session/gateway layer |

---

## 7. User Feedback Summary

**Pain points:**
- **Context overflow** (#1187) is a recurring friction point, especially for users running deepseek and similar context-sensitive models. Users want explicit controls rather than being forced to `/reset` or `/new`.
- **Custom model registration friction** (#2453) disrupts workflows that rely on OpenRouter or NVIDIA-hosted models. The same-model-in-new-thread workaround is fragile and user-hostile.
- **Cross-model agent coordination** (#2132) remains aspirational; the current architecture does not reliably surface subtask completion or errors to the parent task when different models are involved.

**Satisfaction signals:** The single upvote on #1187 and the detailed diagnostic effort in #2132 indicate a user base that is **engaged but frustrated** by gaps in configuration and multi-model orchestration. No positive or neutral feedback was captured in this window.

---

## 8. Backlog Watch

| Issue | Age | Status | Concern |
|-------|-----|--------|---------|
| [#1187](https://github.com/netease-youdao/LobsterAI/issues/1187) | ~4 months (since 2026-04-01) | `[stale]` | High-impact feature request with user demand; long dormant |
| [#2132](https://github.com/netease-youdao/LobsterAI/issues/2132) | ~2 months (since 2026-06-09) | `[stale]` | Architectural gap in cross-model orchestration; diagnostic work already done by a contributor |

**Recommendation:** Both stale issues deserve maintainer triage. #1187 in particular is a straightforward configuration enhancement with clear user demand and should be prioritized to reduce support friction. #2132 may benefit from a dedicated RFC or design doc before implementation.

---

**Project Health Verdict:** 🟡 **Caution** — Active user engagement on configuration and multi-model issues, but minimal maintainer response and no recent merges or releases suggest the project is in a low-velocity phase. Backlog staleness is a concern.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-10

## 1. Today's Overview

The Moltis project saw low but focused activity over the past 24 hours, with 2 open issues and 1 open pull request updated. No new releases were published, and no PRs were merged or issues closed during this window, suggesting the maintainer team is in a triage phase rather than an active delivery sprint. The community continues to surface usability and stability concerns around core workflows (vault recovery, container runtime detection), indicating a mature user base engaging with production-like scenarios. Overall project health appears stable with steady bug reporting and a targeted fix in progress.

## 2. Releases

No new releases were published in the last 24 hours. There are currently no version changes to report.

## 3. Project Progress

- **Merged/Closed PRs today:** None
- **Open PR under review:** [#1186](https://github.com/moltis-org/moltis/pull/1186) — *fix(vault): normalize recovery phrase before hashing* by **pxmpsdev**. This PR addresses an inconsistency where the key-derivation function normalizes the recovery phrase (stripping dashes, uppercasing) before deriving the KEK, but the stored hash was computed over the raw, unnormalized input. The fix ensures the hash is also computed over the normalized phrase, aligning verification behavior with the existing case-insensitive login path.

## 4. Community Hot Topics

- **[#1187](https://github.com/moltis-org/moltis/issues/1187)** — *Heartbeat settings UI silently resets fields not represented by the form* (0 comments, 0 reactions). Reported by **IlyaBizyaev** on 2026-08-09. A UI correctness bug where saving heartbeat configuration silently discards or resets fields not explicitly bound to the form controls.
- **[#1185](https://github.com/moltis-org/moltis/issues/1185)** — *Apple Container 1.x sandbox starts but Moltis treats it as not running* (0 comments, 0 reactions). Reported by **mikz** on 2026-08-08 (updated 2026-08-09). Runtime detection gap for Apple Container sandboxes — the process is active but Moltis fails to recognize its running state.
- **[#1186](https://github.com/moltis-org/moltis/pull/1186)** — *fix(vault): normalize recovery phrase before hashing* by **pxmpsdev** (2026-08-09).

**Analysis:** Both open issues reflect integration-layer pain points — one around UI state management and another around container runtime detection. These are not edge-case noise; they point to real friction for users relying on Moltis's heartbeat monitoring and Apple Container compatibility. The vault fix (#1186) addresses a data-integrity concern that could affect recovery workflows, making it the most operationally significant item currently in flight.

## 5. Bugs & Stability

| Rank | Issue | Severity | Summary | Fix PR |
|------|-------|----------|---------|--------|
| 1 | [#1185](https://github.com/moltis-org/moltis/issues/1185) | **High** | Apple Container 1.x sandbox detected as stopped despite running | None yet |
| 2 | [#1187](https://github.com/moltis-org/moltis/issues/1187) | **Medium** | Heartbeat settings UI silently resets unbound form fields | None yet |

**Note:** The vault normalization fix (#1186) is not yet merged and currently addresses a related but separate concern (hash inconsistency, not a crash). No regressions or crash reports were filed today.

## 6. Feature Requests & Roadmap Signals

No explicit feature requests were opened today. However, two implicit roadmap signals emerge from current activity:

- **Container runtime detection coverage:** Issue #1185 highlights a gap in how Moltis monitors Apple Container sandboxes. Improved runtime detection across container platforms is likely on the roadmap.
- **Vault recovery UX hardening:** The fix in #1186 suggests ongoing investment in making recovery flows more resilient to user input variation — a pattern likely to continue in future releases.

## 7. User Feedback Summary

- **Pain point — Apple Container incompatibility:** Users running Moltis with Apple Container 1.x sandboxes are encountering false-negative status reports, which undermines trust in the monitoring layer. This is a real operational issue for users relying on Moltis for sandbox lifecycle management.
- **Pain point — UI state loss on heartbeat config save:** The silent field reset in #1187 erodes confidence in the settings interface, as users may unknowingly lose configuration on save.
- **Satisfaction signal — Vault flexibility appreciated:** The existing case-insensitive recovery key behavior (noted in #1186's description) suggests users value forgiving input handling, and the community is responding positively to that design direction by reporting when parity breaks.

## 8. Backlog Watch

| Issue/PR | Days Open | Reason for Watch |
|----------|-----------|------------------|
| [#1185](https://github.com/moltis-org/moltis/issues/1185) | ~2 days | High-severity runtime detection bug; no fix PR yet. Apple Container users are likely blocked. |
| [#1187](https://github.com/moltis-org/moltis/issues/1187) | ~1 day | UI correctness bug with user-facing data loss risk. Needs triage to confirm scope. |

**Recommendation:** Both open issues are recent and have zero comments, suggesting they may not yet have been acknowledged by maintainers. Priority should be given to #1185 given its impact on runtime monitoring accuracy, followed by #1187 to prevent silent data loss in user configurations.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# QwenPaw Project Digest — 2026-08-10

## 1. Today's Overview

QwenPaw shows robust development momentum on 2026-08-10 with 18 updated issues and 26 PRs in the last 24 hours, though only 1 PR was merged/closed, suggesting a high volume of open work still awaiting maintainer review. The project is actively addressing frontend rendering bugs, provider compatibility issues, and memory system improvements with a notable influx of first-time contributors. No new releases were published today. Community engagement remains strong, with contributor-driven fixes covering Gemini provider schema errors, SSE streaming latency, and approval UX improvements.

## 2. Releases

No new releases published on 2026-08-10. The project appears to be in a post-2.1.0b2 stabilization phase, with most activity focused on bug fixes and incremental feature PRs rather than versioned shipping.

## 3. Project Progress

**Closed/Merged PRs today:**

- **#6846** — DeepSeek V4 context window catalog added (1M tokens), fixing incorrect 131K default and premature context compaction. ([PR #6846](https://github.com/agentscope-ai/QwenPaw/pull/6846))
- **#6851 / #6850 / #6849 / #6848** — Four duplicate reports of front-end renderer collapsing long multi-line tool output, all closed today (likely resolved or triaged). ([PR #6851](https://github.com/agentscope-ai/QwenPaw/pull/6851))

**Notable open PRs advancing features today:**

- **#6854** — Adds AI-generated purpose descriptions to approval requests, improving UX for permission reviews. ([PR #6854](https://github.com/agentscope-ai/QwenPaw/pull/6854))
- **#6844** — Strips unsupported `$schema` metadata from Gemini tool requests, fixing `unknown` model execution failures. ([PR #6844](https://github.com/agentscope-ai/QwenPaw/pull/6844))
- **#6845** — Fixes assistant completion time preservation on chat history reload, addressing a reported display bug. ([PR #6845](https://github.com/agentscope-ai/QwenPaw/pull/6845))
- **#6843** — Refactors SSE streaming to use pure ASGI middleware, eliminating the buffering delay that caused all output to appear at once. ([PR #6843](https://github.com/agentscope-ai/QwenPaw/pull/6843))
- **#6750** — Fixes session identity deadlock, early session save, and oversized prompt collapse in the chat module. ([PR #6750](https://github.com/agentscope-ai/QwenPaw/pull/6750))
- **#6809** — Sanitizes Chat Completions content for strict providers like StepFun that reject runtime envelope fields. ([PR #6809](https://github.com/agentscope-ai/QwenPaw/pull/6809))
- **#6398** — Adds reranker support for ReMe memory search (backend), improving retrieval quality. ([PR #6398](https://github.com/agentscope-ai/QwenPaw/pull/6398))

## 4. Community Hot Topics

- **#2291** — *Help Wanted: Open Tasks* (66 comments, S1 priority). The master contribution guide remains the most engaged issue, with users actively claiming tasks across P0–P2 priorities. ([Issue #2291](https://github.com/agentscope-ai/QwenPaw/issues/2291))
- **#5579** — *Conversation checkpoint persistence* (closed 2026-08-10). Addresses a critical reliability gap where agent-triggered reboots or crashes cause total conversation loss. ([Issue #5579](https://github.com/agentscope-ai/QwenPaw/issues/5579))
- **#6839** — *MCP tool parameter type coercion bug* (3 comments). Users report that numeric-looking strings are coerced to integers, breaking MCP tool calls. ([Issue #6839](https://github.com/agentscope-ai/QwenPaw/issues/6839))
- **#6812** — *Gemini "unknown" model execution failure* (3 comments). Root cause identified as `$schema` field rejection by Google's SDK; a fix PR (#6844) already exists. ([Issue #6812](https://github.com/agentscope-ai/QwenPaw/issues/6812))
- **#6847** — *QwenPaw killed by antivirus software* (2 comments). Users report false positives from security tools during task execution, raising platform compatibility concerns. ([Issue #6847](https://github.com/agentscope-ai/QwenPaw/issues/6847))
- **#6840** — *ReMe4 roadmap timeline inquiry* (1 comment). Power users seeking clarity on Auto-Link, tri-modal search, and digest weight features. ([Issue #6840](https://github.com/agentscope-ai/QwenPaw/issues/6840))

## 5. Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| **High** | [#6839](https://github.com/agentscope-ai/QwenPaw/issues/6839) | MCP tool calls coerce numeric strings to integers, causing call failures | No fix PR yet |
| **High** | [#6806](https://github.com/agentscope-ai/QwenPaw/issues/6806) | Windows plugin "Internal Server Error" when saving model configs | No fix PR yet |
| **High** | [#5579](https://github.com/agentscope-ai/QwenPaw/issues/5579) | Conversation records lost on abnormal interruption (reboot, crash) | Closed — awaiting implementation |
| **Medium** | [#6826](https://github.com/agentscope-ai/QwenPaw/issues/6826) | Assistant completion time displays incorrectly (shows seconds vs. actual 2min) | Fixed by [PR #6845](https://github.com/agentscope-ai/QwenPaw/pull/6845) |
| **Medium** | [#6812](https://github.com/agentscope-ai/QwenPaw/issues/6812) | Gemini provider fails with "unknown" model due to `$schema` rejection | Fixed by [PR #6844](https://github.com/agentscope-ai/QwenPaw/pull/6844) |
| **Medium** | [#6853](https://github.com/agentscope-ai/QwenPaw/issues/6853) | `prompts.py` claims dream process syncs to MEMORY.md but it was never implemented | No fix PR yet |
| **Low** | [#6281](https://github.com/agentscope-ai/QwenPaw/issues/6281) | Web console not mobile-responsive | No fix PR yet |
| **Low** | [#6841](https://github.com/agentscope-ai/QwenPaw/issues/6841) | Auto-Dream fails whole task on single schema validation error | No fix PR yet |

## 6. Feature Requests & Roadmap Signals

- **#6832 / [PR #6854](https://github.com/agentscope-ai/QwenPaw/pull/6854)** — AI-generated approval descriptions. Users need one-line summaries of what a permission request does; the feature is already in review. Likely in next patch release.
- **#6840** — ReMe4 roadmap (Auto-Link, tri-modal search, 4-category digest weights). Users are tracking the full ReMe memory architecture; a roadmap response is awaited.
- **#6398** — Reranker support for ReMe memory search. Backend enhancement that improves relevance ranking; under review, strong candidate for 2.1.1.
- **#6704** — Session fork feature (checkpoint-style snapshot). Allows users to branch a conversation into an independent session. First-time contributor PR, under review.
- **#6312** — Configurable theme/skin module for branding customization. Draft PR submitted for maintainer direction review.
- **#6259** — CIDR support in no-auth host allowlist. Security enhancement for internal network ranges; first-time contributor.

## 7. User Feedback Summary

Users are reporting real-world friction in three areas: **stability under interruption** (conversation loss on reboot/crash remains a top pain point despite the issue being closed without a visible fix), **provider compatibility** (Gemini `$schema` rejection and strict OpenAI-compatible providers like StepFun causing silent failures), and **antivirus false positives** (QwenPaw being killed by Windows security tools during task execution). On the positive side, the community is enthusiastically engaging with the memory/dream pipeline, requesting deeper ReMe4 features, and submitting first-time contributor PRs at a high rate. The mobile-responsive console request (#6281) is a lower-priority quality-of-life gap.

## 8. Backlog Watch

- **#5579** — *Conversation checkpoint persistence.* Closed without an obvious fix PR. This is a high-impact reliability issue affecting agent users running system commands; needs a concrete implementation plan or issue re-opening.
- **#6853** — *Dream process MEMORY.md sync mismatch.* Documentation lies to agents about a feature that was never built. A code fix or documentation correction is needed.
- **#6806** — *Windows plugin save failure.* Reproducible "Internal Server Error" on Windows with `qwenpaw-creator`; AI-assisted root cause analysis was provided but no fix PR yet.
- **#6839** — *MCP numeric string coercion.* Affects production tool calls; no fix PR despite being reported 2026-08-09.
- **#6841** — *Auto-Dream single-unit failure halts entire task.* Tolerance/retry logic is needed; no fix PR yet.
- **#2291** — *Open contribution tasks.* The master task list has 66 comments and remains active; maintainers should ensure claimed tasks get timely review to avoid contributor burnout.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-10

## 1. Today's Overview

ZeroClaw is experiencing **very high development velocity**, with 50 issues and 50 PRs updated in the last 24 hours. The project is in an active hardening phase: a significant number of P0/P1 security and runtime bugs were triaged or closed today, and multiple governance RFCs are in advanced discussion. No new releases were published. The open PR count (49) vastly exceeds merged/closed (1), indicating a large review queue but steady forward momentum on fixes.

## 2. Releases

No new releases were published in the last 24 hours. The most recent known version is **v0.8.3** (referenced in issues #9101 and #9690).

## 3. Project Progress

- **0 PRs merged/closed** in the last 24 hours (1 total from the 50 updated).
- **Key closed issues today:**
  - [#8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) — System prompt tool-availability mismatch for direct runtime agent path **closed** (fix landed in #8053).
  - [#8681](https://github.com/zeroclaw-labs/zeroclaw/issues/8681) — Goal-mode implementation split tracker **closed** (split PRs migrated).
  - [#9690](https://github.com/zeroclaw-labs/zeroclaw/issues/9690) — Container MSRV pin (rustc 1.95.0 below declared MSRV) **closed**.
  - [#9656](https://github.com/zeroclaw-labs/zeroclaw/issues/9656) — Telegram typing indicator during approval wait **closed**.
  - [#9860](https://github.com/zeroclaw-labs/zeroclaw/issues/9860) — Web UI freeze after filesystem channel event **closed**.
- Several PRs advanced today including [#9196](https://github.com/zeroclaw-labs/zeroclaw/pull/9196) (MCP resource blob materialization), [#9866](https://github.com/zeroclaw-labs/zeroclaw/pull/9866) (verifiable intent hardening), and [#9777](https://github.com/zeroclaw-labs/zeroclaw/pull/9777) (Signal source UUID support).

## 4. Community Hot Topics

| Issue/PR | Comments | Topic |
|---|---|---|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) | 22 | RFC: Work Lanes, Board Automation, Label Cleanup |
| [#7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) | 12 | RFC: Per-model capability & context-window config |
| [#9397](https://github.com/zeroclaw-labs/zeroclaw/issues/9397) | 11 | RFC: Empty WhatsApp `allowed_groups` → permit-none |
| [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) | 11 | Tracker: Maintainer decision queue for RFCs |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) | 10 | RFC: Security posture, credential boundaries, ingress policy |
| [#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) | 9 | Consolidate release attestation mechanisms |
| [#9496](https://github.com/zeroclaw-labs/zeroclaw/issues/9496) | 6 | RFC: Streamline RFC scope, discussion, voting |

**Analysis:** The community is deeply engaged in **governance and security process** improvements. The top-discussed RFCs all relate to making the project more maintainable (work lanes, label cleanup, streamlined RFC process) and more secure (per-model capabilities, credential boundaries, WhatsApp group policy). This signals a project maturing past early feature rush into operational rigor.

## 5. Bugs & Stability

### P0 — Data Loss / Security Risk
- [#9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) — **Gateway webhook handlers do not fail closed** (WhatsApp Cloud, Linq, WATI). Attacker-controllable messages dispatched without caller authentication. **Status: In-progress.**

### P1 — Workflow Blocked / High Risk
- [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) — **Verifiable intent evaluates constraints without verifying the credential chain.** `vi_verify::evaluate_constraints` accepts fulfillment from caller without cryptographic verification. **Fix PR [#9866](https://github.com/zeroclaw-labs/zeroclaw/pull/9866) opened today.**
- [#8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642) — **MCP/tool-schema cloning drives unbounded RSS growth** in agent loop (split from #5542 OOM tracker).
- [#9284](https://github.com/zeroclaw-labs/zeroclaw/issues/9284) — **Config flush can overwrite concurrent writes** (TOCTOU in `RpcDispatcher::flush_config`).
- [#9779](https://github.com/zeroclaw-labs/zeroclaw/issues/9779) — **`sops_dir` documented default not honoured**; SOPs silently never load.
- [#8560](https://github.com/zeroclaw-labs/zeroclaw/issues/8560) — **`browser_open` hangs agent turn** when launcher cannot open window (unbounded subprocess wait). **Closed.**
- [#9192](https://github.com/zeroclaw-labs/zeroclaw/issues/9192) — **shared_budget TOCTOU** can wrap AtomicUsize, causing panic. **Closed.**
- [#9486](https://github.com/zeroclaw-labs/zeroclaw/issues/9486) — **High-entropy detector redacts Solana wallet addresses** on Telegram; `high_entropy_tokens=false` ineffective on channel path.
- [#9085](https://github.com/zeroclaw-labs/zeroclaw/issues/9085) — **Nested runtime panic in `try_enable_pgvector`** at gateway/agent startup.
- [#8731](https://github.com/zeroclaw-labs/zeroclaw/issues/8731) — **Stdio-based MCP servers accumulate as zombie processes.** **Closed.**
- [#8826](https://github.com/zeroclaw-labs/zeroclaw/pull/8826) — **SSRF vulnerability in `image_gen`** download URL (server-supplied fal.ai URL). **Fix PR open.**

### P2 / Lower
- [#9198](https://github.com/zeroclaw-labs/zeroclaw/issues/9198) — Discord typing indicator stuck after dashboard daemon reload.
- [#9656](https://github.com/zeroclaw-labs/zeroclaw/issues/9656) — Telegram typing indicator runs during approval wait. **Closed.**
- [#9834](https://github.com/zeroclaw-labs/zeroclaw/issues/9834) — Intermittent runtime test failures from shared process-global state. **Closed.**

## 6. Feature Requests & Roadmap Signals

| RFC / PR | Status | Likelihood for Next Release |
|---|---|---|
| [#7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) — Per-model capability & context-window config | RFC, 12 comments | **High** — directly addresses provider misreporting; PR [#9809](https://github.com/zeroclaw-labs/zeroclaw/pull/9809) (multiple models per provider) complements it |
| [#9809](https://github.com/zeroclaw-labs/zeroclaw/pull/9809) — Multiple models per provider profile | PR open, XL | **High** — enables the per-model config RFC; large scope but well-scoped |
| [#9556](https://github.com/zeroclaw-labs/zeroclaw/pull/9556) — Langfuse observability backend | PR open | **Medium** — nice-to-have, behind feature flag |
| [#9182](https://github.com/zeroclaw-labs/zeroclaw/pull/9182) — PowerShell as native shell on Windows | PR open, XL | **Medium** — platform-specific, needs Windows review |
| [#9194](https://github.com/zeroclaw-labs/zeroclaw/pull/9194) — `KeySource` trait + `FileKeySource` backend | PR open, XL | **Medium** — security infrastructure improvement |
| [#9067](https://github.com/zeroclaw-labs/zeroclaw/pull/9067) — Hindsight memory: invalidate/forget | Stack 5/7, PR open | **Medium** — part of ongoing memory rework |
| [#9571](https://github.com/zeroclaw-labs/zeroclaw/pull/9571) — Remove WATI channel | PR open | **High** — cleanup, likely merged soon |

## 7. User Feedback Summary

- **Security paranoia is justified and vocal.** Multiple P0/P1 security issues (webhook auth bypass, verifiable intent credential chain gap, SSRF in image_gen) have surfaced recently. Users are flagging these aggressively and maintainingers are responding with fix PRs.
- **Channel-specific bugs are painful.** WhatsApp group-permission defaults, Telegram typing indicators, and Signal sender identity resolution are recurring friction points for multi-channel operators.
- **Memory system complexity is a pain point.** The Hindsight memory stack (consolidation inventing traits, forgetting via invalidate) and pgvector startup panics indicate the memory subsystem is still stabilizing.
- **Documentation-default mismatches cause silent failures.** The `sops_dir` default not being honoured (#9779) and the cron-triggered SOP limits (#9780) show operators are tripping over undocumented behavior.
- **Release provenance confusion.** Issue #9101 highlights that three parallel signing mechanisms were shipped simultaneously, confusing operators about which to trust.

## 8. Backlog Watch

| Issue | Priority | Risk | Attention Needed |
|---|---|---|---|
| [#9565](https://github.com/zeroclaw-labs/zeroclaw/issues/9565) — Webhook handlers don't fail closed | P0 | High | **Urgent** — active security vulnerability, in-progress |
| [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) — VI evaluates without verifying chain | P1 | High | **Urgent** — fix PR [#9866](https://github.com/zeroclaw-labs/zeroclaw/pull/9866) needs review |
| [#8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642) — MCP cloning RSS growth | P1 | High | Needs maintainer review |
| [#6971](https://github.com/zeroclaw-labs/zeroclaw/issues/6971) — Security posture RFC | P2 | High | RFC needs ratification |
| [#7100](https://github.com/zeroclaw-labs/zeroclaw/issues/7100) — Per-model config RFC | P1 | High | RFC needs ratification; blocks #9809 landing |
| [#8519](https://github.com/zeroclaw-labs/zeroclaw/issues/8519) — `cargo-audit` ignores vs `deny.toml` drift | P1 | High | Long-open dependency audit gap |
| [#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) — Consolidate release attestation | P1 | High | CI redundancy; needs decision |
| [#9496](https://github.com/zeroclaw-labs/zeroclaw/issues/9496) — Streamline RFC process | P1 | High | Governance bottleneck |
| [#7897](https://github.com/zeroclaw-labs/zeroclaw/issues/7897) — Live security policy reload | P3 | High | Long-pending RFC |
| [#9825](https://github.com/zeroclaw-labs/zeroclaw/issues/9825) — Publish-safe blockchain ID exceptions | P2 | High | New RFC, needs review |

**Overall project health:** Active but stressed. The security bug surface is concerning (3 P0/P1 security issues this week), though the team is responding quickly. Governance RFC traffic is high, indicating healthy community participation but potential maintainer bottleneck. The lack of merges today (1 closed PR) against 49 open PRs suggests a review backlog that could slow upcoming releases.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*