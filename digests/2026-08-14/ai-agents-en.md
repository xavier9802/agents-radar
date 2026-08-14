# OpenClaw Ecosystem Digest 2026-08-14

> Issues: 486 | PRs: 500 | Projects covered: 12 | Generated: 2026-08-14 02:26 UTC

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



# OpenClaw Project Digest — 2026‑08‑14

## 1. Today’s Overview
OpenClaw shows high daily activity with **486 issues** and **500 pull requests** updated in the last 24 hours. No new releases were published, indicating a maintenance‑focused window rather than a feature‑drop cycle. The project is clearly in a heavy bug‑triage and integration‑cleanup phase, with many P1‑severity issues around session reliability, subagent orchestration, and cron delivery. The open‑PR count (374) substantially exceeds merged/closed (126), suggesting a growing review backlog that may slow down near‑term stabilization.

## 2. Releases
*No new releases were published in the last 24 hours.*

## 3. Project Progress
- **Closed PR (today):**
  - [#122344](https://github.com/openclaw/openclaw/pull/122344) – `fix(models): make picker discovery profile‑aware` (OpenAI model discovery now respects runtime auth‑profile order).
- **Notable closed issues:**
  - [#44431](https://github.com/openclaw/openclaw/issues/44431) – Browser tool improvements field report (closed, likely addressed by subsequent PRs).
  - [#42273](https://github.com/openclaw/openclaw/issues/42273) – Backup stall on large directories (closed, marked already‑fixed).
  - [#91456](https://github.com/openclaw/openclaw/issues/91456) – Telegram DM lane guard after send timeout (closed).
  - [#105342](https://github.com/openclaw/openclaw/issues/105342) – Exec outputs rendered as images on Telegram (closed).
  - [#121605](https://github.com/openclaw/openclaw/issues/121605) – Model fallback delivery failure (closed).

## 4. Community Hot Topics
**Most commented issues (top 5):**

1. [#121058](https://github.com/openclaw/openclaw/issues/121058) – *Silent reply failures still recurring after #116277 closed* (92 comments, open).  
   **Underlying need:** Reliable reply‑delivery pipeline; the project’s monitoring cron continues to log failures despite a prior fix, indicating a deeper architectural gap in queued‑reply payload handling.

2. [#7707](https://github.com/openclaw/openclaw/issues/7707) – *Memory Trust Tagging by Source* (48 comments, open).  
   **Underlying need:** Security‑conscious memory management; users want to prevent “memory poisoning” from untrusted web/third‑party sources.

3. [#25592](https://github.com/openclaw/openclaw/issues/25592) – *Text between tool calls leaks to messaging channels* (48 comments, open).  
   **Underlying need:** Clean UX separation between internal processing noise and user‑visible messages.

4. [#44925](https://github.com/openclaw/openclaw/issues/44925) – *Subagent completion silently lost* (27 comments, open).  
   **Underlying need:** Reliable multi‑agent orchestration; loss of subagent results without retry/notification is a critical reliability gap.

5. [#121953](https://github.com/openclaw/openclaw/issues/121953) – *Cron agent stalls on DeepSeek* (16 comments, open).  
   **Underlying need:** Consistent cron‑job execution across LLM providers; the `[cron:… ]` prefix triggers a lower‑priority API edge for DeepSeek, causing tens‑of‑seconds delays.

**Most commented PRs (today):**  
All PRs listed show `Comments: undefined` in the provided data, but several are marked `status: 👀 ready for maintainer look` or `⏳ waiting on author`, indicating active review cycles.

## 5. Bugs & Stability
**P1 / critical bugs reported today (ranked by severity & comment count):**

| Issue | Summary | Severity | Fix PR? |
|-------|---------|----------|---------|
| [#121953](https://github.com/openclaw/openclaw/issues/121953) | Cron agent stalls on DeepSeek due to prefix‑based API routing | P1, 🦪 silver shellfish | No open fix PR |
| [#67777](https://github.com/openclaw/openclaw/issues/67777) | Subagent completion delivery lost on timeout/drain/orphan prune | P1, 🦪 silver shellfish | No open fix PR |
| [#91363](https://github.com/openclaw/openclaw/issues/91363) | Isolated cron consistently fails with “LLM request failed” | P1, 🦪 silver shellfish | No open fix PR |
| [#97616](https://github.com/openclaw/openclaw/issues/97616) | Child‑process leak → zombie accumulation, runtime degradation | P1, 🦐 gold shrimp | No open fix PR |
| [#111498](https://github.com/openclaw/openclaw/issues/111498) | Main agent blocked by persistent workspace‑state migration after auth recovery | P1, 🦐 gold shrimp | No open fix PR |
| [#43367](https://github.com/openclaw/openclaw/issues/43367) | Multi‑agent orchestration unstable (concurrent adds, session‑lock failures) | P1, 🦪 silver shellfish | No open fix PR |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) | Active‑memory plugin blocks replies, QMD boot overloads gateway | P1, 🦞 diamond lobster | No open fix PR |
| [#97983](https://github.com/openclaw/openclaw/issues/97983) | iOS/WebChat messages append but do not trigger assistant replies | P1, 🦞 diamond lobster | No open fix PR |
| [#92433](https://github.com/openclaw/openclaw/issues/92433) | Subagent completion silently dropped when announce steers into requester run | P1, 🦪 silver shellfish | No open fix PR |
| [#89278](https://github.com/openclaw/openclaw/issues/89278) | Codex OAuth refresh succeeds but cron/heartbeat fail with 10s auth timeout | P1, 🐚 platinum hermit (regression) | No open fix PR |

**Regression‑type bugs** (worked before, now broken):  
- #89278 (OAuth timeout)  
- #111498 (workspace‑state migration)  
- #121605 (model‑fallback delivery) – now closed  
- #77733 (`/new`/`/reset` no longer triggers persona greeting)  

**No new fix PRs** were identified for the top‑ranked P1 bugs today; most remain in “needs maintainer review” state.

## 6. Feature Requests & Roadmap Signals
| Issue | Request | Likelihood for Next Version |
|-------|---------|-----------------------------|
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | Memory Trust Tagging by Source | Medium – security‑focused, aligns with upcoming memory‑authorization contract (PR #121422) |
| [#45771](https://github.com/openclaw/openclaw/issues/45771) | Built‑in pace‑aware rate limiting for autonomous agents | High – directly addresses reported API‑rate‑limit burns; PR #123216 (secrets proxy) shows similar infra work |
| [#16555](https://github.com/openclaw/openclaw/issues/16555) | TTL/Expiry for Delivery Queue Messages | Medium – solves stale‑message flooding after gateway restarts |
| [#9016](https://github.com/openclaw/openclaw/issues/9016) | Expose OpenRouter usage cost to agent runtime | Low – niche cost‑tracking feature |
| [#45508](https://github.com/openclaw/openclaw/issues/45508) | Self‑hosted STT/TTS in webchat | Medium – improves privacy‑focused deployments |
| [#41366](https://github.com/openclaw/openclaw/issues/41366) | Durable natural‑language rule learning | Low – long‑standing enhancement |
| [#79165](https://github.com/openclaw/openclaw/issues/79165) | Graduated crash‑recovery ladder for gateway | High – addresses frequent crash‑loop reports (e.g., #78493) |

**Roadmap signal:** The active memory‑authorization work (PR #121422, #121423, #121945) suggests the next release will ship a *multiplayer memory* model with scoped read isolation. Combined with the #7707 trust‑tagging request, the project is clearly moving toward **fine‑grained, source‑aware memory security**.

## 7. User Feedback Summary
**Pain points (recurring themes):**
- **Subagent reliability:** “Silently lost” completions (#44925, #67777, #92433) and persistent subagent sessions after completion (#47975) indicate a fragile orchestration layer.
- **Cron execution:** DeepSeek‑specific stalls (#121953) and isolated‑cron LLM failures (#91363) frustrate automated‑task users.
- **Memory‑management chaos:** Multiple users report inconsistent memory storage across peers (#43747), SQLite unbounded growth (#114612), and active‑memory blocking replies (#72015).
- **Delivery‑queue leaks:** Tool‑call text leaking to channels (#25592), final messages stranded when LLM forgets tool call (#85714), and stale queue entries flooding restarts (#16555) point to a need for better queue‑state management.
- **Auth/timeout regressions:** OAuth refresh timeouts (#89278) and Codex spark empty‑argument bugs (#107814) erode trust in provider integrations.
- **UX friction:** Mixed‑case deep‑link routing (#123207), session‑list automation‑badge not updating (#123253), and missing reasoning‑stream support (#42276) are common complaints.

**Satisfaction signals:**  
The high comment counts on many issues show strong user engagement, but the lack of closed fix PRs for top bugs suggests frustration with the pace of resolution.

## 8. Backlog Watch
**Issues/PRs needing maintainer attention (most urgent first):**

1. [#7707](https://github.com/openclaw/openclaw/issues/7707) – Memory Trust Tagging (48 comments, `clawsweeper:no-new-fix-pr`, `needs-maintainer-review`, `needs-product-decision`, `needs-security-review`).
2. [#43367](https://github.com/openclaw/openclaw/issues/43367) – Multi‑agent orchestration instability (13 comments, `no-new-fix-pr`, `needs-maintainer-review`).
3. [#72015](https://github.com/openclaw/openclaw/issues/72015) – Active‑memory blocks replies & QMD boot overload (10 comments, `no-new-fix-pr`, `needs-maintainer-review`).
4. [#121953](https://github.com/openclaw/openclaw/issues/121953) – Cron agent stalls on DeepSeek (16 comments, `no-new-fix-pr`, `linked-pr-open`).
5. [#91363](https://github.com/openclaw/openclaw/issues/91363) – Isolated cron LLM failures (10 comments, `no-new-fix-pr`).
6. [#97616](https://github.com/openclaw/openclaw/issues/97616) – Child‑process leak / zombie accumulation (7 comments, `no-new-fix-pr`).
7. [#16555](https://github.com/openclaw/openclaw/issues/16555) – TTL for delivery‑queue messages (6 comments, `no-new-fix-pr`).
8. [#45771](https://github.com/openclaw/openclaw/issues

---

## Cross-Ecosystem Comparison



# Cross-Project Comparison Report: AI Agent & Personal Assistant Open-Source Ecosystem
**Date:** 2026-08-14 | **Analyst:** Agnes-2.0-Flash, Sapiens AI

---

## 1. Ecosystem Overview

The 2026 personal AI agent open-source landscape is characterized by rapid architectural divergence — from monolithic desktop shells (CoPaw) to kernel-level orchestration (IronClaw Reborn) to focused channel integrations (NanoBot, PicoClaw). Five of twelve tracked projects show high daily activity (40+ issues and PRs), while three are dormant and four operate at moderate cadence. Security hardening, session persistence reliability, and cross-provider LLM compatibility represent the three dominant pain clusters across all active projects. The ecosystem is in a post-v1.0 maturation phase where stabilization sprints are replacing feature-launch cycles.

---

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Open PRs | Merged/Closed | Release | Health Score* |
|---|---|---|---|---|---|---|
| **OpenClaw** | 486 | 500 | 374 | 126 | None | 🟡 6/10 — maintenance heavy, backlog growing |
| **NanoBot** | 11 | 31 | 22 | 9 | None | 🟢 7.5/10 — responsive stabilization |
| **Hermes Agent** | 50 | 50 | — | — | v0.20.1 (today) | 🟡 6.5/10 — post-release bug surge |
| **PicoClaw** | 2 | 9 | — | 3 | None | 🟡 5/10 — routine maintenance |
| **NanoClaw** | 2 | 19 | — | 13 | v2.2.0 (yesterday) | 🟢 8/10 — strong cadence, security focus |
| **IronClaw** | 50 | 50 | 32 | 6 | v1.2.0 (yesterday) | 🟢 8/10 — architectural transformation |
| **LobsterAI** | 2 | 10 | — | 6 | None | 🟡 5.5/10 — UI refactoring, stale backlog |
| **Moltis** | 1 | 4 | 4 | 0 | None | 🟡 5/10 — maintenance phase, flaky test risk |
| **CoPaw** | 45 | 50 | — | 19 | v2.1.0 + beta.5 (today) | 🟠 5/10 — high velocity but regressions |
| **ZeroClaw** | 50 | 50 | 40 | 10 | None (v0.9.0 pending) | 🟢 7/10 — pre-release hardening, security-aware |
| **NullClaw** | 0 | 0 | — | — | None | 🔴 2/10 — dormant |
| **ZeptoClaw** | 0 | 0 | — | — | None | 🔴 2/10 — dormant |

*Health Score: weighted composite of release velocity, bug-fix responsiveness, PR merge ratio, and community engagement quality.

---

## 3. OpenClaw's Position

**Advantages vs. peers:**
- **Scale of engagement:** 486 issues / 500 PRs daily dwarf all competitors except CoPaw and ZeroClaw, indicating the largest active user and contributor base.
- **Memory architecture ambition:** The memory-trust-tagging roadmap (#7707, PR #121422) is the most sophisticated source-aware memory model in the ecosystem, positioning OpenClaw ahead on security-conscious memory management.
- **Multi-channel breadth:** Native support for Telegram, Discord, Matrix, browser tooling, and iOS/WebChat gives OpenClaw the widest channel surface.

**Technical approach differences:**
- OpenClaw uses a **queued-reply delivery pipeline** with cron-based monitoring — a pattern shared with NanoBot and ZeroClaw but more mature than LobsterAI's scheduled-task approach.
- Unlike IronClaw's kernel-pluggable-loop architecture or CoPaw's OS-shell paradigm, OpenClaw follows a **modular gateway** design with subagent orchestration as a first-class concept.
- OpenClaw's **rate-limiting and cost-tracking** requests (#45771, #9016) reflect a user base heavily invested in API economics, more so than NanoBot's budget model-visible MCP schemas.

**Community size comparison:**
OpenClaw's issue comment counts (92, 48, 48 on top issues) far exceed any peer project, confirming it as the ecosystem's most contested and widely used project. NanoClaw and NanoBot show strong but smaller engagement. ZeroClaw has an active RFC culture with deep technical participation but lower absolute volume.

---

## 4. Shared Technical Focus Areas

| Focus Area | Projects Involved | Specific Needs |
|---|---|---|
| **Session persistence & data loss** | NanoBot, CoPaw, ZeroClaw, OpenClaw | Session corruption on archive failure (NanoBot #5378), concurrent-session state writes (CoPaw #7011), SOP headless persistence (ZeroClaw #9929), delivery-queue leaks (OpenClaw #25592) |
| **Cron / scheduled execution reliability** | OpenClaw, NanoBot, Hermes Agent, CoPaw | DeepSeek stalls (OpenClaw #121953), scheduler die-on-persistence-failure (NanoBot #5373), isolated-cron LLM failures (OpenClaw #91363), `hermes cron run` silent failures (Hermes #83340) |
| **Multi-agent / subagent orchestration** | OpenClaw, CoPaw, ZeroClaw | Silent subagent completion loss (OpenClaw #44925, #67777), unbounded sub-agent spawning (CoPaw #6652), goal-mode bounded execution (ZeroClaw #8303 RFC) |
| **Security hardening & permission models** | NanoClaw, ZeroClaw, CoPaw, IronClaw | CSPRNG pairing codes (NanoClaw #3229), verifiable-intent credential chains (ZeroClaw #9328), plugin RCE via port exposure (CoPaw #6992), SSRF gate for file download (ZeroClaw #8713) |
| **Memory management & context compaction** | OpenClaw, CoPaw, IronClaw, ZeroClaw | Trust-tagging by source (OpenClaw #7707), tool-call structure lost in compaction (CoPaw #5856), cross-conversation recall (IronClaw #7185), memory lifecycle decoupling RFC (ZeroClaw #6850) |
| **Cross-provider LLM compatibility** | OpenClaw, Hermes Agent, NanoBot, ZeroClaw | DeepSeek `response_format` gaps (Hermes #83390, OpenClaw #121953), model fallback delivery (OpenClaw #121605), OpenRouter prompt-cache (ZeroClaw #9631) |
| **WebUI / desktop UX** | NanoBot, CoPaw, LobsterAI, IronClaw | Session collaboration mentions (NanoBot #5358), OS-shell desktop (CoPaw v2.1.0), activity localization (NanoBot #5366), Telegram sticker support (NanoBot #5387) |

---

## 5. Differentiation Analysis

| Dimension | Differentiators |
|---|---|
| **Architecture paradigm** | IronClaw: pluggable kernel with ACP executor. CoPaw: OS-shell desktop environment. OpenClaw: modular gateway with subagent orchestration. NanoBot: channel-first with cron resilience. ZeroClaw: RFC-driven security-first architecture. |
| **Target user segment** | OpenClaw: power users with multi-channel deployments. CoPaw: desktop-first personal AI users migrating from Codex/Qoder. NanoBot: operators needing cron reliability and MCP budget control. IronClaw: enterprise/cloud deployments with local-file access needs. NanoClaw: security-conscious agent-stamp operators. Hermes Agent: desktop users with voice/WakeWord workflows. |
| **Platform focus** | CoPaw is the only project with a native OS-shell paradigm (movable windows, taskbar, launcher). Hermes Agent has the strongest voice/STT/TTS stack. ZeroClaw leads on security RFCs and verifiable-intent contracts. LobsterAI targets the Chinese enterprise market (v4pro demand, enterprise edition). |
| **Release cadence** | High: CoPaw (v2.1.0 today), NanoClaw (v2.2.0 yesterday), Hermes (v0.20.1 today), IronClaw (v1.2.0 yesterday). Medium: OpenClaw, ZeroClaw (v0.9.0 pending). Low/Dormant: PicoClaw, LobsterAI, Moltis, NullClaw, ZeptoClaw. |
| **Plugin / skill ecosystem** | NanoClaw has the most mature Agent Plugins 1.0.0 format with in-place template updates. ZeroClaw is adopting the same standard (RFC #9810). CoPaw has a marketplace with import flows from competitors. IronClaw uses a WASM-sandboxed host-function model. |

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapidly Iterating (40+ PRs/day, frequent releases):**
- **CoPaw** (50 PRs, v2.1.0 shipped today) — highest velocity but carrying regression debt.
- **IronClaw** (50 PRs, v1.2.0 stable) — architectural transformation with strong maintainer alignment.
- **ZeroClaw** (50 PRs) — pre-release hardening with deep RFC culture and security audit participation.
- **OpenClaw** (500 PRs) — largest engagement but in maintenance triage; momentum is reactive rather than feature-driven.

**Tier 2 — Active Stabilization (10–30 PRs/day, responsive bugfixes):**
- **NanoBot** (31 PRs) — strong merge-to-open ratio, responsive to critical issues.
- **Hermes Agent** (50 PRs) — post-release stabilization with active contributor base (Natetgmaxwell, HexLab98).
- **NanoClaw** (19 PRs) — security hardening cadence, template migration complete.

**Tier 3 — Moderate / Maintenance ( <10 PRs/day):**
- **LobsterAI** (10 PRs) — UI refactoring pace, growing stale PR backlog since March.
- **PicoClaw** (9 PRs) — Dependabot-driven, low feature velocity.
- **Moltis** (4 PRs) — local dev ergonomics, flaky test risk.

**Tier 4 — Dormant:**
- **NullClaw, ZeptoClaw** — no activity in 24 hours.

---

## 7. Trend Signals

| Trend | Evidence Across Projects | Value for AI Agent Developers |
|---|---|---|
| **Security-by-design is non-negotiable** | NanoClaw CSPRNG fix (#3229), ZeroClaw SSRF gate (#8713) + credential chain audit (#9328), CoPaw port-exposure incident (#6992), NanoClaw Telegram pairing security | Developers must treat plugin permission models, credential verification, and network exposure as first-class concerns — not afterthoughts. External audits are happening. |
| **Session persistence is the #1 reliability risk** | NanoBot archive corruption (#5378), CoPaw concurrent-session corruption (#7011), ZeroClaw SOP persistence (#9929), OpenClaw delivery-queue leaks (#25592) | Any agent platform targeting production must guarantee atomic session writes with rollback capability. This is the single most common failure mode. |
| **Cron / scheduled execution is a trust boundary** | OpenClaw cron stalls (#121953), NanoBot scheduler death (#5373), Hermes silent cron failures (#83340), CoPaw plugin cron injection (#6916) | Scheduled execution requires isolated sessions, per-run context boundaries, and failure notification — not best-effort delivery. |
| **Context compaction breaks tool-call fidelity** | CoPaw #5856, OpenClaw #25592, ZeroClaw #6850 RFC | Compact/eviction pipelines must preserve structured tool schemas, not just text — this is an emerging architecture gap across the ecosystem. |
| **Multi-provider LLM fragmentation is

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>



# NanoBot Project Digest — 2026-08-14

## 1. Today's Overview

NanoBot saw high development velocity today with 11 updated issues and 31 PRs in the last 24 hours (22 open, 9 merged/closed). Activity is concentrated around session management resilience, cron scheduler stability, and WebUI polish. No new releases were published. The project appears to be in an active stabilization cycle, with multiple bugfix PRs directly addressing critical issues reported earlier today — a strong signal of responsive maintainership.

---

## 2. Releases

No new releases today.

---

## 3. Project Progress

**Merged/Closed PRs today:**

- **PR #5381** — Native workspace folder picker for WebUI (macOS / Windows / Linux), restricted to loopback-bound gateways. ([link](https://github.com/HKUDS/nanobot/pull/5381))
- **PR #5384** — Restored transcript-only session history discovery in the WebUI sidebar, fixing a regression where persisted transcripts without canonical JSONL became invisible. ([link](https://github.com/HKUDS/nanobot/pull/5384))
- **PR #5374 / #5375** — Cron scheduler now survives single job-store persistence failures instead of dying permanently. ([link](https://github.com/HKUDS/nanobot/pull/5374)) · ([link](https://github.com/HKUDS/nanobot/pull/5375))
- **PR #4556** — Wired `model_override` for Dream consolidation, applying the cheaper model at runtime during periodic memory compaction. ([link](https://github.com/HKUDS/nanobot/pull/4556))
- **PR #4550** — Cron jobs now use per-run session keys, preventing stale context leakage across runs. ([link](https://github.com/HKUDS/nanobot/pull/4550))

**Open PRs advancing features today:**

- **PR #5358** — Session collaboration via `@mentions` in WebUI, giving each session a stable server-owned name and extending the composer picker. ([link](https://github.com/HKUDS/nanobot/pull/5358))
- **PR #5388** — Budget model-visible MCP schemas, adding an opt-in byte budget to trim large tool sets before sending to the LLM. ([link](https://github.com/HKUDS/nanobot/pull/5388))
- **PR #5387** — Reusable sticker replies for Telegram, exposing inbound sticker metadata and dispatching sticker-only replies. ([link](https://github.com/HKUDS/nanobot/pull/5387))
- **PR #5386** — Preserves MCP Apps result metadata separately from model-facing text, keeping rich app data in tool progress events. ([link](https://github.com/HKUDS/nanobot/pull/5386))
- **PR #5383** — Serializes canonical file access across session JSONL readers/mutators with a directory lock, fixing race conditions. ([link](https://github.com/HKUDS/nanobot/pull/5383))

---

## 4. Community Hot Topics

1. **Cron scheduler permanence after persistence failure** — Issue #5373 (1 comment) and its three fix PRs (#5374, #5375 merged; #5376 open). The high PR velocity from a single issue author signals strong community engagement. ([Issue #5373](https://github.com/HKUDS/nanobot/issues/5373))

2. **Budget model-visible MCP schemas** — Issue #5298 and PR #5388 address a real pain point: large MCP tool sets bloat context and increase costs. The opt-in byte budget approach is a pragmatic compromise. ([Issue #5298](https://github.com/HKUDS/nanobot/issues/5298)) · ([PR #5388](https://github.com/HKUDS/nanobot/pull/5388))

3. **Telegram sticker & reaction support** — Issue #5289 and PR #5387 reflect user demand for richer Telegram interactions beyond plain text. ([Issue #5289](https://github.com/HKUDS/nanobot/issues/5289)) · ([PR #5387](https://github.com/HKUDS/nanobot/pull/5387))

4. **WebUI session collaboration** — PR #5358 (mentions) and PR #5357 (cancel-before-delete) show active investment in multi-session WebUI workflows. ([PR #5358](https://github.com/HKUDS/nanobot/pull/5358)) · ([PR #5357](https://github.com/HKUDS/nanobot/pull/5357))

5. **Matrix cross-signing / trusted device** — Issue #4841 remains open with no fix PR, a persistent friction point for security-conscious Matrix users. ([Issue #4841](https://github.com/HKUDS/nanobot/issues/4841))

---

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR |
|----------|-------|-------------|--------|
| **Critical** | [#5373](https://github.com/HKUDS/nanobot/issues/5373) | Cron scheduler dies permanently after a single persistence failure (`disk full` / `permission change` / `locked file`) | #5374 ✅ merged, #5376 open |
| **Critical** | [#5306](https://github.com/HKUDS/nanobot/issues/5306) | `exec.allowPatterns` shell-chain bypass allows unintended command execution (security advisory) | — |
| **High** | [#5378](https://github.com/HKUDS/nanobot/issues/5378) | File-cap archive failure mutates live session before persistence, causing data loss on retry | #5380 open |
| **High** | [#5377](https://github.com/HKUDS/nanobot/issues/5377) | Consolidation truncates archive input but advances cursor past full batch, losing messages | #5379 open |
| **Medium** | [#5368](https://github.com/HKUDS/nanobot/issues/5368) | Copy/fork actions appear while Agent turn is still running, creating conflicting UI signals | — |
| **Medium** | [#5382](https://github.com/HKUDS/nanobot/pull/5382) | `os.replace()` on Windows `PermissionError` crashes the entire gateway during heartbeat cron | #5382 open |
| **Low** | [#5349](https://github.com/HKUDS/nanobot/pull/5349) | Tests fail deterministically during ~5h daily window due to UTC timezone mismatch in `record_token_usage` | #5349 open |

**Notable:** Two high-severity session persistence bugs (#5378, #5377) were reported and fixed in the same day, suggesting a coordinated effort to harden session integrity. The security advisory (#5306) remains unfixed and warrants attention.

---

## 6. Feature Requests & Roadmap Signals

- **MCP Apps host support in WebUI** (#5251) — Users want rich MCP App results rendered natively rather than as opaque text. PR #5386 partially addresses this by preserving metadata.
- **ViBo memory integration** (#5372) — Proposal for persistent cross-session memory; currently a vendor pitch with a free trial link. No maintainer response yet.
- **WebUI localization of Agent activity text** (#5366) — User-requested i18n for frontend-generated activity labels ("Working for…", "Searching files…").
- **Heartbeat model override & isolated session** (#4549, #4551) — Cost-reduction features for heartbeat polling; #4549 still open.
- **Predicted next-release features:** Cron scheduler resilience (likely included), file-cap archive recovery (#5380), and consolidated session history fix (#5379) are all high-priority bugfixes with open PRs and strong candidates for the next patch release.

---

## 7. User Feedback Summary

**Pain points:**
- Session data loss when archive/file-cap operations fail mid-write is a recurring theme (#5378, #5377), eroding trust in persistence guarantees.
- Cron scheduler silence-on-failure (#5373) is operationally dangerous — users lose scheduled jobs without warning.
- Matrix bot device marked "untrusted" (#4841) is a persistent trust/friction issue for enterprise Matrix deployments.
- WebUI copy/fork actions appearing during active turns (#5368) creates confusing UX.

**Positive signals:**
- Rapid triage and merging of bugfixes (cron, transcripts, workspace picker) shows the team is responsive.
- Telegram sticker support (#5289 / #5387) and MCP schema budgeting (#5298 / #5388) address real cost and richness gaps.
- Session collaboration via mentions (#5358) indicates maturation toward multi-user WebUI workflows.

---

## 8. Backlog Watch

| Issue / PR | Age | Concern |
|------------|-----|---------|
| [#4841](https://github.com/HKUDS/nanobot/issues/4841) — Matrix untrusted device / no SAS verification path | ~37 days | No fix PR; blocks secure Matrix deployments |
| [#5251](https://github.com/HKUDS/nanobot/issues/5251) — MCP Apps host support in WebUI | ~39 days | Feature gap vs. upstream MCP spec; partial work in #5386 |
| [#5372](https://github.com/HKUDS/nanobot/issues/5372) — ViBo memory integration proposal | 1 day | Vendor pitch; needs maintainer evaluation |
| [#5366](https://github.com/HKUDS/nanobot/issues/5366) — WebUI agent activity localization | 1 day | i18n gap; low engineering cost, high UX value |
| [#4549](https://github.com/HKUDS/nanobot/pull/4549) — Heartbeat model_override | ~49 days | Open with conflict tag; cost-reduction feature for ops |
| [#4551](https://github.com/HKUDS/nanobot/pull/4551) — Heartbeat isolated_session | ~49 days | Open with conflict tag; pairs with #4549 |

**Overall health assessment:** NanoBot is in a productive stabilization phase. The team is actively closing critical session and cron bugs, while feature work on MCP, Telegram, and WebUI collaboration advances in parallel. The main risk is the unfixed security advisory (#5306) and the aging Matrix trust issue (#4841), both of which deserve maintainer attention.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>



# Hermes Agent Project Digest — 2026-08-14

---

## 1. Today's Overview

Hermes Agent is in a high-velocity stabilization phase following the v0.20.1 patch release (2026-08-13), which consolidated ~656 merged PRs. The project saw 50 issues and 50 PRs updated in the last 24 hours, indicating sustained community engagement. Activity is heavily weighted toward bug fixes and desktop/platform regressions — a clear signal that the v0.20.0 release introduced several infrastructural issues requiring rapid remediation. One new release was published today.

---

## 2. Releases

### v0.20.1 (v2026.8.13) — Patch Release

**Release Date:** August 13, 2026

A maintenance patch rolling up approximately 656 PRs merged since v0.20.0. Targets downstream consumers (Docker images, hosted deployments, tag-based installs). No breaking changes noted.

> ⚠️ **Note:** Despite being a patch release, several P1 regressions were reported shortly after v0.20.0's launch (gateway reaping on Windows/macOS, TUI overlay blindness). These remain open and active as of this digest.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Description |
|----|-------------|
| [#84155](https://github.com/NousResearch/hermes-agent/pull/84155) | Fix: persist dropped screenshot bytes before attach (macOS Finder screenshots) |
| [#67257](https://github.com/NousResearch/hermes-agent/pull/67257) | Fix: desktop crash on reasoning content (RangeError/infinite recursion) + py39 compat + profile pin |
| [#67251](https://github.com/NousResearch/hermes-agent/pull/67251) | Fix: desktop crash on reasoning content (RangeError) — duplicate/consolidated path |
| [#85707](https://github.com/NousResearch/hermes-agent/pull/85707) | Fix(cache): establish typed tool-schema boundary before `planned_tools[-1]` |
| [#81639](https://github.com/NousResearch/hermes-agent/issues/81639) | Closed: `_canonicalize_api_tool_calls` mutation bug (marked duplicate) |

### Open PRs Advancing Today

- [#85773](https://github.com/NousResearch/hermes-agent/pull/85773) — Configurable `beam_size` and startup prewarm for local Whisper STT
- [#85772](https://github.com/NousResearch/hermes-agent/pull/85772) — Honor `voice.silence_duration` config in desktop (was hardcoded to 1250ms)
- [#85771](https://github.com/NousResearch/hermes-agent/pull/85771) — MiniMax chunked-PCM streaming TTS provider
- [#85770](https://github.com/NousResearch/hermes-agent/pull/85770) — Fix client-capture wake word arming after backend restarts
- [#85769](https://github.com/NousResearch/hermes-agent/pull/85769) — Consolidated normalization of all provider usage/wire shapes (5-PR salvage)
- [#85764](https://github.com/NousResearch/hermes-agent/pull/85764) — Fix session search recall for `/new`-reset sessions
- [#85765](https://github.com/NousResearch/hermes-agent/pull/85765) — Preserve Discord thread routing for progress-message edits
- [#85766](https://github.com/NousResearch/hermes-agent/pull/85766) — Fix desktop Sessions list bounce at date dividers
- [#85768](https://github.com/NousResearch/hermes-agent/pull/85768) — Accurate per-turn search cap messaging (no false retry claims)
- [#85767](https://github.com/NousResearch/hermes-agent/pull/85767) — Bundled Box productivity skill
- [#85730](https://github.com/NousResearch/hermes-agent/pull/85730) — Block per-profile gateways when `multiplex_profiles` is enabled
- [#85750](https://github.com/NousResearch/hermes-agent/pull/85750) — Fix per-profile remote WS routing (chat attaching to local primary instead of remote)
- [#67934](https://github.com/NousResearch/hermes-agent/pull/67934) — Use native Ollama `/api/tags` catalog for local endpoints
- [#82891](https://github.com/NousResearch/hermes-agent/pull/82891) | Security: pin KittenTTS wheel SHA-256 to refuse tampered releases

---

## 4. Community Hot Topics

| Issue | Comments | Summary |
|-------|----------|---------|
| [#66616](https://github.com/NousResearch/hermes-agent/issues/66616) | 25 | Skills index stale (29.8h old, 26h limit) — automated freshness probe degraded |
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | 20 | **P1** Desktop restart kills gateway on Windows, never relaunches — WeChat/QQ go silent |
| [#84834](https://github.com/NousResearch/hermes-agent/issues/84834) | 16 | Webhook Revolution meta-EPIC: 5×2×3 graph-gated repair campaign |
| [#69592](https://github.com/NousResearch/hermes-agent/issues/69592) | 12 | **P1** TUI `/sessions` and `/models` overlays invisible with ambient widget dock (Day 13) |
| [#83390](https://github.com/NousResearch/hermes-agent/issues/83390) | 9 | `title_generation` fails on DeepSeek — HTTP 400 `response_format` unavailable |

**Underlying needs:** The top-voted issues cluster around **message delivery reliability** (gateway lifecycle on Windows, webhook correctness) and **TUI usability regression**. The Webhook Revolution meta-issue (#84834) signals the team recognizes systemic webhook surface debt. The DeepSeek `response_format` issue (#83390) reflects growing provider fragmentation as users adopt varied LLM backends.

---

## 5. Bugs & Stability

### Critical / P1 Issues

| Issue | Severity | Summary | Fix PR? |
|-------|----------|---------|---------|
| [#83683](https://github.com/NousResearch/hermes-agent/issues/83683) | **P1** | Desktop restart reaps live gateway on Windows — never relaunches (regression from v0.20.0) | No |
| [#85344](https://github.com/NousResearch/hermes-agent/issues/85344) | **P1** | `_reap_unsupervised_gateway_orphans` kills launchd-supervised gateway on macOS | No |
| [#85368](https://github.com/NousResearch/hermes-agent/issues/85368) | **P1** | Gateway process repeatedly SIGKILL'd on Windows — messaging goes offline | No |
| [#84855](https://github.com/NousResearch/hermes-agent/issues/84855) | **P1** | Permission denied killing orphaned gateway PID on Windows startup | No |
| [#85044](https://github.com/NousResearch/hermes-agent/issues/85044) | **P1** | Desktop `serve` kills Scheduled Task-managed gateway on Windows, never restarts | No |
| [#69592](https://github.com/NousResearch/hermes-agent/issues/69592) | **P1** | TUI `/sessions` + `/models` overlays invisible with ambient widget dock (13 days) | No |
| [#80117](https://github.com/NousResearch/hermes-agent/issues/80117) | **P2** | SQLite POSIX lock conflict causes `APIConnectionError` in gateway | No |

### P2 Issues

| Issue | Summary |
|-------|---------|
| [#83427](https://github.com/NousResearch/hermes-agent/issues/83427) | `browser_exec` crashes — `pydantic_core.ModuleNotFoundError` when PYTHONPATH points at Hermes venv |
| [#72064](https://github.com/NousResearch/hermes-agent/issues/72064) | `oneshot` (`-z`) cannot skip built-in memory injection; `--ignore-rules` silently ignored |
| [#52339](https://github.com/NousResearch/hermes-agent/issues/52339) | Terminal `hermes update` rebuilds Desktop locally but leaves `/Applications/Hermes.app` stale |
| [#83846](https://github.com/NousResearch/hermes-agent/issues/83846) | Windows ZIP fallback deletes built desktop app, never rebuilds; reports "Already up to date" |
| [#76267](https://github.com/NousResearch/hermes-agent/issues/76267) | Windows `sync_back` drops remote sandbox file changes |
| [#85406](https://github.com/NousResearch/hermes-agent/issues/85406) | Docker terminal + `vision_analyze` fails on Windows (POSIX→backslash path mangling) |
| [#85104](https://github.com/NousResearch/hermes-agent/issues/85104) | Desktop: assistant message rendered twice in chat view (frontend rendering bug) |
| [#85745](https://github.com/NousResearch/hermes-agent/issues/85745) | Desktop: profile tab switch shows wrong session list (default instead of selected profile) |
| [#83340](https://github.com/NousResearch/hermes-agent/issues/83340) | `hermes cron run` reports "failed" without executing job (desktop-app shell) |
| [#84058](https://github.com/NousResearch/hermes-agent/issues/84058) | Desktop: composer caret lost when tool call starts streaming (silent focus loss) |
| [#85750](https://github.com/NousResearch/hermes-agent/pull/85750) | Per-profile remote WS routing bug (PR open, fixing) |

**Stability Assessment:** The v0.20.0 release introduced a **gateway lifecycle regression** affecting Windows and macOS. At least 5 distinct but related P1 issues converge on the same root cause: the orphan-reaping logic (`_reap_unsupervised_gateway_orphans`) is too aggressive and kills supervised gateways. This is the single biggest stability concern and likely the highest-impact fix needed.

---

## 6. Feature Requests & Roadmap Signals

| Issue | Type | Comments | Likelihood for Near-Term |
|-------|------|----------|--------------------------|
| [#4438](https://github.com/NousResearch/hermes-agent/issues/4438) | Feature — Rich Spreadsheet Skill (xlsx/csv) | 8 | Medium — structured abstraction request |
| [#67798](https://github.com/NousResearch/hermes-agent/issues/67798) | Feature — Lifecycle hooks as shared runtime contract | 6 | Medium — architectural, needs decision |
| [#35966](https://github.com/NousResearch/hermes-agent/issues/35966) | Feature — Native desktop/mobile client | 5 👍4 | Long-term — already partially addressed |
| [#71023](https://github.com/NousResearch/hermes-agent/issues/71023) | Feature — Live upgrade (zero-downtime, preserve subagents) | 4 👍1 | High value, complex |
| [#33049](https://github.com/NousResearch/hermes-agent/issues/33049) | Feature — Configurable credential pool exhaustion TTL | 3 👍1 | Low effort, high value |
| [#75539](https://github.com/NousResearch/hermes-agent/issues/75539) | Feature — Move session to project (Desktop) | 4 | Medium |
| [#85418](https://github.com/NousResearch/hermes-agent/issues/85418) | Feature — Local-first memory provider proposal | 2 | Exploratory |
| [#84317](https://github.com/NousResearch/hermes-agent/issues/84317) | Feature — Opt-out of `drop_pending_updates` on Telegram cold boot | 2 | Low effort, niche |

**Signals:** The project is actively shipping new bundled skills (Box skill in [#85767](https://github.com/NousResearch/hermes-agent/pull/85767)). The lifecycle hooks abstraction (#67798) and live upgrade (#71023) indicate roadmap direction toward more resilient multi-process architecture. The memory provider proposal (#85418) shows community-driven innovation aligning with Hermes' extensibility philosophy.

---

## 7. User Feedback Summary

**Pain Points:**
- **Gateway lifecycle on restart** is the dominant complaint. Users report messaging platforms (WeChat, QQ, Telegram, Discord) going completely silent after desktop restart on Windows and macOS. Multiple users independently reporting the same root cause (#83683, #85344, #85368, #84855, #85044).
- **TUI usability regression** — the ambient widget dock pattern (documented in quota gauge setup) breaks core navigation (`/sessions`, `/models`, `/reload`) (#69592). 13 days open with no fix.
- **Installation/update split-brain** — `hermes update` leaves `/Applications/Hermes.app` stale on macOS (#52339) and silently deletes the Windows app bundle (#83846).
- **DeepSeek compatibility** — auxiliary `title_generation` fails with HTTP 400 on DeepSeek models (#83390), suggesting provider-specific `response_format` support gaps.
- **Desktop UX glitches** — duplicate message rendering (#85104), session list wrong after profile switch (#85745), composer caret loss during streaming (#84058).

**Positive Signals:**
- Community actively contributing fixes (Natetgmaxwell's 4 PRs today on voice/wake/STT/TTS; HexLab98's session search fix).
- Security-conscious user base (SHA-256 pinning for KittenTTS, #82891).
- Feature requests show mature usage patterns (spreadsheet skills, session management, zero-downtime updates).

---

## 8. Backlog Watch

| Issue | Age | Priority | Needs Attention |
|-------|-----|----------|-----------------|
| [#69592](https://github.com/NousResearch

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>



# PicoClaw Project Digest — 2026-08-14

## 1. Today's Overview

PicoClaw shows moderate activity on 2026-08-14, with **9 PRs** updated and **2 issues** touched in the last 24 hours. No new releases were published today. The bulk of PR activity consists of automated **dependabot dependency bumps** (AWS SDK, Anthropic SDK, Matrix client), indicating routine maintenance rather than feature-driven development. Two open issues remain unresolved — a Web UI performance bug and an ASR feature request — neither of which has an active fix in progress.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**3 PRs were merged/closed today**, all dependency updates:

| PR | Description | Status |
|---|---|---|
| [#3305](https://github.com/sipeed/picoclaw/issues/3305) | Bump `aws/aws-sdk-go-v2/service/bedrockruntime` 1.53.3 → 1.56.2 | ✅ Closed |
| [#3306](https://github.com/sipeed/picoclaw/issues/3306) | Bump `aws/aws-sdk-go-v2/config` 1.32.25 → 1.32.33 | ✅ Closed |
| [#3304](https://github.com/sipeed/picoclaw/issues/3304) | Bump `anthropics/anthropic-sdk-go` 1.55.1 → 1.61.0 | ✅ Closed |

Six additional dependency PRs remain open (#3318, #3332, #3333, #3334, #3335, #3336). Notably, **[PR #3318](https://github.com/sipeed/picoclaw/pull/3318)** addresses a **broken `pnpm-lock.yaml`** with duplicate mapping keys that prevents `pnpm` from parsing the lockfile — this is a build-stability fix that should be prioritized.

## 4. Community Hot Topics

- **[Issue #3281](https://github.com/sipeed/picoclaw/issues/3281)** — *Web UI chat input lag with long history* (5 comments, 1 👍). This is the most engaged issue, with a user reporting significant input lag in the Web UI when chat history grows. Underlying need: **responsive UX at scale** — as sessions accumulate messages, the frontend likely re-renders heavy DOM or performs inefficient state management. This is a quality-of-life issue that affects daily power users.

- **[Issue #3331](https://github.com/sipeed/picoclaw/issues/3331)** — *Support non-whisper ASR models via `/audio/transcriptions`* (0 comments, created today). User wants flexibility to use faster/newer transcription models beyond the hardcoded `*-whisper-*` pattern. Underlying need: **ASR model agility** — the current implementation ties transcription routing to model naming conventions, which excludes capable newer models.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|---|---|---|---|
| **Medium** | [#3281](https://github.com/sipeed/picoclaw/issues/3281) | Web UI chat input becomes very laggy with moderate chat history | None yet |
| **Low** | [#3318](https://github.com/sipeed/picoclaw/pull/3318) | Broken `pnpm-lock.yaml` with duplicate keys blocks frontend builds | PR open but stale |

No crashes or regressions reported today. The lockfile issue (#3318) is a **build-time blocker** for contributors using `pnpm` and should be addressed before any frontend work proceeds.

## 6. Feature Requests & Roadmap Signals

- **[Issue #3331](https://github.com/sipeed/picoclaw/issues/3331)** — Request for a config flag (e.g., `whisper-transcription: true`) to force the whisper ASR path regardless of model name, enabling use of modern/faster transcription models. This is a **low-effort, high-value** feature that removes an arbitrary naming constraint. Likely candidate for inclusion in an upcoming maintenance release.

- Ongoing dependency bumps suggest the team is tracking upstream SDKs closely (Anthropic, AWS Bedrock, Matrix). Future roadmap may include **expanded cloud provider support** or **Matrix integration improvements** given the `mautrix` bump to v0.29.0.

## 7. User Feedback Summary

- **Pain point:** Web UI degrades noticeably with longer conversations (#3281). Users want a snappy, responsive interface regardless of session length.
- **Pain point:** ASR model selection is overly restrictive — users feel locked into older Whisper variants (#3331).
- **Satisfaction signal:** Dependabot-driven updates are keeping dependencies current with minimal manual effort, suggesting healthy upstream tracking.
- **Dissatisfaction signal:** The pnpm lockfile issue has been open since Aug 5 with no maintainer response, potentially blocking contributors.

## 8. Backlog Watch

| Item | Open Since | Concern |
|---|---|---|
| [#3281](https://github.com/sipeed/picoclaw/issues/3281) — Web UI lag bug | 2026-07-21 | Performance bug affecting real users; 5 comments, no fix |
| [#3318](https://github.com/sipeed/picoclaw/pull/3318) — Broken lockfile | 2026-08-05 | Blocks frontend builds; marked stale; 9 days old |
| [#3331](https://github.com/sipeed/picoclaw/issues/3331) — ASR flexibility | 2026-08-13 | Fresh request; no response yet but low-hanging fruit |

**Recommended maintainer attention:** Prioritize **#3318** (build breakage) and **#3281** (user-facing degradation). Both have been open for over a week with no resolution in sight.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>



# NanoClaw Project Digest — 2026-08-14

## 1. Today's Overview

NanoClaw (v2.2.0) shows **high activity** with 19 PRs updated and 2 issues touched in the last 24 hours. The project is in a strong release-cadence rhythm, with v2.2.0 landing today and a suite of core CI/security hardening work being merged in parallel. One open bug around agent-group ID prefixing and one open UX issue around unbounded approval cards for webhook senders remain unresolved. Overall project health is positive — merge velocity is high and the core team is actively shipping security and reliability improvements.

## 2. Releases

### v2.2.0 (2026-08-13)
- **In-place plugin updates via templates**: `ncl groups create --template <ref>` now detects when a group already carries the template's plugin and performs an in-place update instead of minting a duplicate agent. A dry-run mode prints a plan of every plugin-owned surface (plugin files, skills, MCP servers).
- **Agent Plugins 1.0.0 format migration** (PR #3220): Templates are now represented as proper Agent Plugins directories with stamp-time symlink/caps/secret hardening.
- **Setup wizard template flow** (PR #2909): First-agent stamping now flows through the setup wizard.
- No explicit breaking changes noted beyond the template format migration, which the release PR frames as a fix for security hardening.

## 3. Project Progress

**Merged / closed today (13 PRs):**

| PR | Summary |
|----|---------|
| [#3237](https://github.com/nanocoai/nanoclaw/pull/3237) | v2.2.0 release |
| [#3236](https://github.com/nanocoai/nanoclaw/pull/3236) | Repin agent image to `hardened-2026-08-13` |
| [#3241](https://github.com/nanocoai/nanoclaw/pull/3241) | CI: verified signature now counts as approving review (off by default, gated by `AGENT_IMAGE_AUTO_APPROVE=true`) |
| [#3240](https://github.com/nanocoai/nanoclaw/pull/3240) | CI: open agent-image bump PR from a repository dispatch |
| [#3238](https://github.com/nanocoai/nanoclaw/pull/3238) | CI: `verify-agent-image` now runs on every PR so it can serve as a required gate |
| [#3231](https://github.com/nanocoai/nanoclaw/pull/3231) | feat: honor plugin MCP cwd in Codex and OpenCode provider config writers |
| [#3229](https://github.com/nanocoai/nanoclaw/pull/3229) | **Fix**: Telegram pairing codes now use `crypto.randomInt` (CSPRNG) instead of `Math.random()` |
| [#3220](https://github.com/nanocoai/nanoclaw/pull/3220) | **Core feature**: Agent templates migrated to Agent Plugins 1.0.0 directories with security hardening |
| [#2909](https://github.com/nanocoai/nanoclaw/pull/2909) | Setup wizard template flow and first-agent stamping |
| [#3158](https://github.com/nanocoai/nanoclaw/pull/3158) | `verify-agent-image`: pin publisher identity and check attestations per architecture |
| [#3145](https://github.com/nanocoai/nanoclaw/pull/3145) | Fix: backfill missing channel destinations for existing wiring configs (migration 021) |
| [#2624](https://github.com/nanocoai/nanoclaw/pull/2624) | feat: per-server `disabledTools` support in `McpServerConfig` |
| [#3230](https://github.com/nanocoai/nanoclaw/pull/3230) | Fix: update removal docs to stop pointing at retired `data/env` mirror |

**Key themes**: Security hardening (CSPRNG pairing, image verification gating, template stamping hardening), CI reliability (auto-merge logic fixes, required status checks), and the Agent Plugins 1.0.0 format migration.

## 4. Community Hot Topics

| Item | Activity | Link |
|------|----------|------|
| [#3235](https://github.com/nanocoai/nanoclaw/issues/3235) — Unknown-sender approval unbounded cards | Created 2026-08-13, 0 comments | Issue |
| [#3234](https://github.com/nanocoai/nanoclaw/issues/3234) — Template-stamped agents get bare UUID (no `ag-` prefix) | 1 comment, closed 2026-08-13 | Issue |
| [#3243](https://github.com/nanocoai/nanoclaw/pull/3243) — verify-agent-image: auto-merge is not a verdict | Open, core-team | PR |
| [#2420](https://github.com/nanocoai/nanoclaw/pull/2420) — `/add-hindsight` MCP wrapper for Hindsight memory | Open since 2026-05-11, long-running | PR |
| [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) — Unknown slash commands treated as normal chat | Open since 2026-05-08 | PR |

**Analysis**: The closed issue #3234 reveals a real usability gap — users stamping templates via CLI expect consistent ID formatting. The open issue #3235 highlights a design flaw in the unknown-sender approval flow: automated senders (webhooks, bots) are indistinguishable from humans at the approval gate, producing unbounded cards that users can't sensibly act on. The two long-open PRs (#2420, #2346) indicate sustained community interest in memory integrations and CLI robustness, but both have been pending for ~3 months.

## 5. Bugs & Stability

| Severity | Issue / PR | Description | Fix Status |
|----------|-----------|-------------|------------|
| **Medium** | [#3234](https://github.com/nanocoai/nanoclaw/issues/3234) | Template-stamped agent groups receive a bare UUID without `ag-` prefix, causing OneCLI `ensureAgent` to reject them at spawn | ✅ Closed (2026-08-13) |
| **Medium** | [#3235](https://github.com/nanocoai/nanoclaw/issues/3235) | `unknown_sender_policy = 'request_approval'` triggers unbounded approval cards for webhook/bot senders; denials don't persist | 🔴 Open — no fix PR yet |
| **Low** | [#3243](https://github.com/nanocoai/nanoclaw/pull/3243) | `Enable auto-merge` step in verify-agent-image fails on drafts / transient API errors, falsely marking the job as failed | 🟡 Open PR, under review |
| **Low** | [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) | Unknown slash commands silently dropped (categorized as `passthrough` → SDK drops response) | 🟡 Open since May 2026 |

**Notable fix shipped**: PR #3229 addressed a **security-adjacent bug** where Telegram pairing codes were generated with `Math.random()` — switched to `crypto.randomInt` with a widened code space. This is a genuine security improvement.

## 6. Feature Requests & Roadmap Signals

| Item | Signal |
|------|--------|
| [#2420](https://github.com/nanocoai/nanoclaw/pull/2420) — Hindsight memory MCP wrapper | Community demand for long-term memory backed by dedicated engines, not just session-local state. Bundled MCP bridge included. |
| [#3218](https://github.com/nanocoai/nanoclaw/pull/3218) — `--stdin-json` bounded input mode | Power-user need for programmatic CLI invocation without reshaping request frames. |
| [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) — Unknown slash command handling | Users are sending unrecognized commands and getting silent failures; a `category: 'none'` fallback is requested. |
| [#2624](https://github.com/nanocoai/nanoclaw/pull/2624) — Per-server `disabledTools` in `McpServerConfig` | Granular tool control per MCP server is needed for operators running multiple servers with overlapping capabilities. |

**Prediction**: `--stdin-json` (PR #3218) and per-server `disabledTools` (PR #2624) are both open and well-scoped — either could land in v2.3. The Hindsight memory integration (#2420) is a larger feature that may require a dedicated SKILL.md and more review. Unknown-sender approval UX (#3235) is likely to surface in a future release as the team ships more webhook/bot integrations.

## 7. User Feedback Summary

- **Pain point — ID inconsistency**: Users stamping agents via `--template` are tripped by bare UUIDs lacking the `ag-` prefix that `--folder` assigns. This is a real breaking experience at spawn time and has since been closed.
- **Pain point — Approval card spam**: Bot/webhook senders in groups with `unknown_sender_policy = 'request_approval'` generate infinite approval cards with no persistent denial state. Operators of automated pipelines find this unusable.
- **Satisfaction signal**: The template in-place update feature in v2.2.0 directly addresses a workflow gap — users previously had to manually clean up duplicate agents when re-stamping.
- **Satisfaction signal**: The Telegram pairing code security fix (#3229) was submitted by a community contributor (`chiptoe-svg`), indicating active community engagement and trust in the project's security posture.
- **Dissatisfaction signal**: Silent dropping of unknown slash commands (#2346) means users get no feedback when they mistype or use unsupported commands — a poor UX pattern.

## 8. Backlog Watch

| Item | Age | Risk |
|------|-----|------|
| [#2420](https://github.com/nanocoai/nanoclaw/pull/2420) — Hindsight MCP wrapper | ~3 months open | Medium — well-scoped, bundled MCP included, but hasn't been triaged |
| [#2346](https://github.com/nanocoai/nanoclaw/pull/2346) — Unknown slash commands as normal chat | ~3 months open | Low-Medium — small fix but affects UX for power users |
| [#3218](https://github.com/nanocoai/nanoclaw/pull/3218) — `--stdin-json` input mode | 5 days open | Medium — useful for automation workflows, waiting on review |
| [#3243](https://github.com/nanocoai/nanoclaw/pull/3243) — verify-agent-image auto-merge fix | 1 day open | Low — CI reliability, core-team owned |
| [#3235](https://github.com/nanocoai/nanoclaw/issues/3235) — Unbounded approval cards for webhook senders | 1 day open | High — blocks users running automated senders in approval-gated groups; no fix PR yet |

**Maintainer attention needed**: Issue #3235 is the most urgent open item — it affects a growing class of users integrating automated senders and has no proposed fix. The two long-standing PRs (#2420, #2346) also merit a triage decision to either advance or close.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>



# IronClaw Project Digest — 2026-08-14

## 1. Today's Overview

IronClaw is experiencing a **high-velocity development cycle** focused on the "Reborn" architectural overhaul. The project released stable **v1.2.0** yesterday (2026-08-13), promoting the fully validated RC3 candidate after fixes to the runtime container image (notably `curl` installation for in-container HTTP healthchecks). Activity is intense: 50 issues and 50 PRs were updated in the last 24 hours, with 32 open/active issues and 26 open PRs. The core team, led by `serrrfirat` and `BenKurrek`, has shipped a large set of consolidated implementation issues for the **Pluggable Agent Loops epic (#7482)**, covering egress proxy wiring, foreign-harness execution, capability sockets, and conformance tooling — signaling that the kernel architecture transition is moving from design into implementation.

## 2. Releases

### ironclaw-v1.2.0 (2026-08-13)
- **Type:** Stable promotion of `1.2.0-rc.3`
- **Key change:** Runtime container image now installs `curl`, enabling in-container HTTP healthchecks. Orchestrators can now probe workers reliably.
- **Breaking changes:** None announced.
- **Migration notes:** No migration required; this is a patch-level fix layered on the RC3 feature set.
- PR: [#7625](https://github.com/nearai/ironclaw/pull/7625)

## 3. Project Progress

### Merged / Closed PRs Today
- **#7625** — Promote `1.2.0-rc.3` to stable `1.2.0` ([link](https://github.com/nearai/ironclaw/pull/7625))
- **#7590** — Fix live-canary bundled-skill marker owner alignment with runtime mint ([link](https://github.com/nearai/ironclaw/pull/7590))
- **#7376** — Extend `check-guidance.py` CI gate to cover the full `docs/` surface, including Mintlify pages and the `docs/zh/` locale mirror ([link](https://github.com/nearai/ironclaw/pull/7376))
- **#7633** — Implement unbound-turns end-state: threads as coordinator unit, kernel no longer carries reply routing ([link](https://github.com/nearai/ironclaw/pull/7633))
- **#7163** — Structural edit support for docx/xlsx/pptx, PDF rendering from HTML, and fix of #7109 text-log regression ([link](https://github.com/nearai/ironclaw/pull/7163))
- **#7506** — Dependabot: 17 dependency bumps (`async-trait`, `thiserror`, `base64`, etc.) ([link](https://github.com/nearai/ironclaw/pull/7506))

### Key Open PRs Advancing
- **#7634** — Completes the unbound-turns switchover: seeded history, OpenAI-compat over the door, forced `tool_choice`, run limits ([link](https://github.com/nearai/ironclaw/pull/7634))
- **#7464** — Telegram linked-device pairing now binds the identity to the workspace bot channel automatically ([link](https://github.com/nearai/ironclaw/pull/7464))
- **#7562** — Internal design docs for detached turns: threads as the unit of work, one `submit_turn` ([link](https://github.com/nearai/ironclaw/pull/7562))
- **#7548** — Structured execution contracts for scheduled automations (goal, success criteria, output instructions, allowed capabilities) ([link](https://github.com/nearai/ironclaw/pull/7548))
- **#7513** — `acp serve` CLI command enabling ACP stdio transport for external tools (VS Code, GitHub Copilot CLI) ([link](https://github.com/nearai/ironclaw/pull/7513))
- **#7184** — Nostr host functions for WASM tools (`nostr-sign-event` with BIP-340 Schnorr signing) ([link](https://github.com/nearai/ironclaw/pull/7184))

### Performance PRs (Tier 3 — Write-Amplification Reductions)
- **#7631** — Coalescing event sink for runtime milestones ([link](https://github.com/nearai/ironclaw/pull/7631))
- **#7629** — Reduced trigger and outbound state writes by moving retention pruning ([link](https://github.com/nearai/ironclaw/pull/7629))
- **#7630** — Stress-test harness for per-turn Postgres write measurement ([link](https://github.com/nearai/ironclaw/pull/7630))
- **#7628** — Removed heartbeat journal churn, keeping lease timestamps on the materialized process row ([link](https://github.com/nearai/ironclaw/pull/7628))

## 4. Community Hot Topics

| Issue / PR | Activity | Link |
|---|---|---|
| **#7482** — Epic: Pluggable agent loops (ACP executor, edge credential injection, kernel architecture) | 6 comments, high risk | [Issue](https://github.com/nearai/ironclaw/issues/7482) |
| **#6257** — PDF `mime_type` error on send/generate | 4 comments | [Issue](https://github.com/nearai/ironclaw/issues/6257) |
| **#2117** — `ironclaw-bridge`: local file/MCP bridge daemon for cloud deployments | 2 comments, 1 👍 | [Issue](https://github.com/nearai/ironclaw/issues/2117) |
| **#7185** — Memory not reliably recalled across conversations | 2 comments | [Issue](https://github.com/nearai/ironclaw/issues/7185) |

**Analysis:** The dominant community and maintainer focus is the **Reborn kernel architecture** (#7482), which aims to decouple IronClaw from owning agent loops and per-integration tool code, making it a scheduling/tenancy/egress kernel instead. This is the project's most ambitious structural shift. The second-hottest issue (#6257) reflects a **practical user pain point** around PDF handling that has been open since July. Issue #2117 (local file bridge for cloud-hosted deployments) and #7185 (cross-conversation memory) both signal **usability gaps** that users are eager to see resolved.

## 5. Bugs & Stability

| Issue | Severity | Summary | Fix PR? |
|---|---|---|---|
| **#7626** | Medium | Custom MCP with browser/email auth (MKT1) gets stuck during connection | No |
| **#7627** | Medium | GitHub extension shows as connected after invalid credentials are entered | No |
| **#7589** | High | NEAR AI Cloud Sonnet-5 returning 500 errors for 3+ days | Referenced in nearai/cloud-api#920 |
| **#7185** | Medium | Memory/context not reliably recalled across conversations | No |
| **#6257** | Medium | `Invalid value (attachments.mime_type)` error on PDF send/generate | No |
| **#7580** | Low | IronClaw Reborn version not exposed in web UI (discoverability) | No |

**Note:** PR #7163 previously fixed a text-log regression (#7109) but left document round-trip as a deferred item, which may relate to the PDF mime-type issue in #6257. The Sonnet-5 500s (#7589) are a cloud-infrastructure issue tracked externally.

## 6. Feature Requests & Roadmap Signals

| Request / Signal | Source | Likelihood in Next Version |
|---|---|---|
| **Pluggable agent loops** — ACP executor, foreign harnesses (claude-code, pi, codex) | #7482, #7624 | **High** — v0 ACP harness executor is the *only* item being built right now per #7624 |
| **Local file/MCP bridge** for cloud-hosted deployments | #2117 | **Medium** — long-standing blocker for Obsidian/local-vault use cases |
| **ACP stdio transport** for external tool integration | #7513 (PR open) | **High** — PR is open and in review |
| **Nostr host functions** in WASM sandbox | #7184 (PR open) | **Medium** — niche but valuable for decentralized identity use cases |
| **Version exposure in web UI** | #7580 | **Low** — trivial UX fix, likely to land soon |
| **Structured automation execution contracts** | #7548 (PR open) | **High** — PR is open and advancing |
| **Telegram linked-device auto-binding** | #7464 (PR open) | **High** — PR is open and advancing |

## 7. User Feedback Summary

- **Pain point — PDF/document handling:** Users report `mime_type` errors when sending/generating PDFs (#6257), and a prior regression (#7109) broke text tools from writing binary documents. The community wants reliable document round-trip capabilities.
- **Pain point — Cross-conversation memory:** Multiple testers independently flagged that context established in one conversation is not reliably recalled in later conversations (#7185), reported in the Champions weekly check-in. This is a **core UX reliability concern**.
- **Pain point — Cloud-local file access:** Cloud-hosted IronClaw users cannot access local files (Obsidian vaults, project directories) (#2117). This is described as a **blocker** for several workflows.
- **Pain point — Auth flows getting stuck:** Custom MCPs requiring browser/email verification (e.g., MKT1) stall during connection (#7626), and GitHub credentials are accepted as "connected" even when invalid (#7627).
- **Satisfaction signal — Telegram pairing improvement:** The linked-device pairing feature (#7464) removes a friction point by eliminating the separate proof-code pairing ceremony.
- **Satisfaction signal — Design doc convergence:** The unbound-turns design (#7562) was verified against the live runtime and converged with team discussion, suggesting strong internal alignment on the architecture direction.

## 8. Backlog Watch

| Issue | Age | Priority | Reason to Watch |
|---|---|---|---|
| **#2117** — ironclaw-bridge local file/MCP daemon | ~4 months | High | Blocker for cloud-hosted local-file workflows; 1 👍 but no active PR |
| **#7185** — Memory not recalled across conversations | ~10 days | High | Core reliability issue surfaced by Champions program; no fix in sight |
| **#6257** — PDF mime_type error | ~25 days | Medium | Direct user-facing bug; may be resolved by broader document work in #7163's follow-ups |
| **#7626** — Custom MCP auth stuck | New | Medium | Auth-flow regression for MCPs requiring browser/email verification |
| **#7627** — GitHub extension false-connected | New | Medium | Credential validation gap in the GitHub extension |
| **#7589** — Sonnet-5 500s | New | High | Cloud infrastructure issue; tracked externally at nearai/cloud-api#920 |

---

**Overall Project Health:** 🟢 **Active and focused.** The Reborn kernel redesign is executing on schedule with a clear v0 priority (ACP harness executor). The v1.2.0 release went smoothly. The main risks are the backlog of user-facing bugs (#7185, #6257, #2117) that have not yet been addressed, and the Sonnet-5 cloud outage. The team is balancing architectural transformation with ongoing bugfixes — a healthy but demanding cadence.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>



# LobsterAI Project Digest — 2026-08-14

---

## 1. Today's Overview

LobsterAI showed moderate development activity on 2026-08-14, with 2 open issues and 10 PRs updated in the last 24 hours. Six PRs were merged or closed today, primarily driven by UI refactoring and the evergreen daily check-in feature by contributor `fisherdaddy` and `btc69m979y-dotcom`. No new releases were published. Two active issues include a user request for v4pro model support and a stale test-coverage PR, while six other PRs from March–April remain open and stale, indicating a growing backlog of community contributions awaiting maintainer review.

---

## 2. Releases

No new releases were published on 2026-08-14.

---

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Author | Description |
|----|--------|-------------|
| [#2488](https://github.com/netease-youdao/LobsterAI/pull/2488) | fisherdaddy | Refactored cowork betweenness and management UI (`renderer`, `cowork`) |
| [#2487](https://github.com/netease-youdao/LobsterAI/pull/2487) | fisherdaddy | Merged skills and MCP views into a unified "skills-and-connectors" view (`renderer`) |
| [#2485](https://github.com/netease-youdao/LobsterAI/pull/2485) | btc69m979y-dotcom | Implemented evergreen daily check-in activity, reusing existing server and management capabilities (`renderer`, `cowork`) |
| [#2486](https://github.com/netease-youdao/LobsterAI/pull/2486) | fisherdaddy | Unified MCP card/detail UI with kits and skills styling; extracted shared `CardOverflowMenu` and `managementTypography` (`renderer`) |
| [#1232](https://github.com/netease-youdao/LobsterAI/pull/1232) | choyuenga | Fixed bug where scheduled task results were not pushed to UI on first execution (`scheduledTask`) |
| [#2484](https://github.com/netease-youdao/LobsterAI/pull/2484) | liugang519 | Enterprise edition feature work spanning renderer, docs, main, and openclaw modules |

**Key takeaways:** Today's merged work is heavily focused on **UI unification and refactoring** (MCP/skills/kits convergence, management UI polish) and **feature stabilization** (evergreen check-in, first-run scheduled task fix). The enterprise edition PR suggests continued commercial-track development.

---

## 4. Community Hot Topics

| Item | Type | Author | Engagement |
|------|------|--------|------------|
| [Issue #2489](https://github.com/netease-youdao/LobsterAI/issues/2489) — "快更新v4pro！" (Update v4pro quickly!) | Issue · Open | nimamasl114514 | 1 comment, 0 👍 |
| [Issue #1162](https://github.com/netease-youdao/LobsterAI/issues/1162) — Vitest unit tests for `openclawMemoryFile` and `openclawLocalTimeContextPrompt` | Issue · Stale | MaoQianTu | 1 comment, 0 👍 |

**Analysis:** Issue #2489 reflects user demand for the v4pro model — a signal that the community is closely tracking model capability updates and expects timely integration. Issue #1162 (also mirrored in PR #1165) represents a sustained community effort to improve test coverage for critical memory-management modules, though it has been open since March without maintainer action.

---

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| **Medium** | [#1232](https://github.com/netease-youdao/LobsterAI/pull/1232) — Scheduled task first-run UI silence | First execution of a cron job did not push results to the UI; users had to wait for the second run to see output. Root cause: `previousRunAtMs` initialized to `0`, causing the `pollOnce()` guard condition to skip the first update. | ✅ Merged today |

No new crash reports or regression issues were opened today.

---

## 6. Feature Requests & Roadmap Signals

| Signal | Source | Description |
|--------|--------|-------------|
| v4pro model integration | [Issue #2489](https://github.com/netease-youdao/LobsterAI/issues/2489) | User explicitly requests the v4pro model update. Likely a high-priority roadmap item given community attention. |
| Enterprise edition | [PR #2484](https://github.com/netease-youdao/LobsterAI/pull/2484) | Ongoing enterprise feature work across multiple modules suggests an upcoming enterprise-focused release track. |
| Evergreen check-in | [PR #2485](https://github.com/netease-youdao/LobsterAI/pull/2485) | User engagement/retention mechanic moved from time-limited to always-available, indicating a shift toward sustained activity loops. |

**Prediction:** v4pro support and enterprise edition features are the most likely candidates for the next release cycle.

---

## 7. User Feedback Summary

| Theme | Source | Summary |
|-------|--------|---------|
| Model freshness | [Issue #2489](https://github.com/netease-youdao/LobsterAI/issues/2489) | Users are eager for the latest model capabilities (v4pro) and perceive delays in integration. |
| UI consistency | [PR #2487](https://github.com/netease-youdao/LobsterAI/pull/2487), [PR #2486](https://github.com/netease-youdao/LobsterAI/pull/2486) | Community appreciates and supports efforts to unify skills, MCP, and kits into a consistent UI — repeated refactoring PRs from `fisherdaddy` indicate this is an ongoing pain point being actively addressed. |
| Task feedback | [PR #1163](https://github.com/netease-youdao/LobsterAI/pull/1163) (open) | Users report poor UX when triggering scheduled tasks manually — no loading state, no immediate feedback, and delay before status refresh. |

Overall sentiment: **constructive and engaged**. Users are reporting specific pain points and community members are submitting targeted fixes.

---

## 8. Backlog Watch

The following important PRs have been open since March–April with no maintainer response (stale status):

| PR | Author | Since | Description |
|----|--------|-------|-------------|
| [#1156](https://github.com/netease-youdao/LobsterAI/pull/1156) | MaoQianTu | 2026-03-31 | Vitest unit tests for `commandSafety` and `coworkMemoryJudge` — critical security/quality modules with zero test coverage |
| [#1163](https://github.com/netease-youdao/LobsterAI/pull/1163) | gongzhi-netease | 2026-03-31 | Fix: add optimistic update and Gateway status sync for scheduled task "run now" interaction |
| [#1165](https://github.com/netease-youdao/LobsterAI/pull/1165) | MaoQianTu | 2026-03-31 | Vitest unit tests for `openclawMemoryFile` and `openclawLocalTimeContextPrompt` (75 tests) |
| [#1166](https://github.com/netease-youdao/LobsterAI/pull/1166) | leedalei | 2026-03-31 | Fix: prevent duplicate custom agent names in the creation modal |

**Risk assessment:** PR #1156 covers security-critical modules (`commandSafety` guards against destructive command execution; `coworkMemoryJudge` filters memory quality). Their lack of test coverage is a **stability and security risk**. PR #1163 addresses a direct UX degradation. All four warrant maintainer review to prevent further backlog stagnation.

---

*Generated by LobsterAI Project Digest · Data source: GitHub via LobsterAI · 2026-08-14*

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>



# Moltis Project Digest — 2026-08-14

## 1. Today's Overview

Moltis is experiencing moderate development activity with 4 open pull requests under review and 1 active issue requiring attention. No releases were shipped in the last 24 hours. All recent PRs are bug-fix oriented, targeting build-script reliability on macOS and correcting Go module paths after upstream organizational moves. The project appears to be in a maintenance-and-hardening phase rather than a feature-launch cadence, with contributor momentum focused on unblocking local development workflows.

## 2. Releases

No new releases reported.

## 3. Project Progress

- **No PRs merged or closed today** — all 4 open PRs remain under review.
- **PR #1194** — Guards empty bash array expansions for macOS bash 3.2, fixing a crash in `just local-validate-full` when run without a PR number.
- **PR #1190** — Adds durable CalDAV and channel-history connectors (Slack, Discord, Matrix, Microsoft Teams) with provider-neutral persistence, atomic snapshots, and bounded full-text search.
- **PR #1192** — Fixes the `wacrawl` skill install metadata to point at the `openclaw` org after its rename.
- **PR #1191** — Fixes the `gogcli` module path in sandbox Dockerfiles to the `openclaw` org, unblocking `moltis sandbox build`.

## 4. Community Hot Topics

- **[Issue #1193](https://github.com/moltis-org/moltis/issues/1193)** — Flaky test `push fanout timeout assertion races under full-suite load`. The test `moltis-gateway push::tests::fanout_is_bounded_and_times_out_a_hung_endpoint` failed 2 of 3 full-suite runs on an idle 10-core macOS machine. No comments or reactions yet.
- **[PR #1194](https://github.com/moltis-org/moltis/pull/1194)** — macOS bash 3.2 compatibility fix; same author as the flaky test issue, suggesting the contributor is actively unblocking their own development environment.
- **[PR #1190](https://github.com/moltis-org/moltis/pull/1190)** — The largest feature PR today, adding connector persistence and multi-platform channel history. Signals strong community demand for durable, provider-neutral integrations.

**Analysis:** The community is actively investing in local dev ergonomics (macOS compatibility, Go module reorgs) alongside meaningful feature growth (CalDAV + channel connectors). The flaky test points to a race condition in the gateway's push fanout logic that will likely surface more frequently as test coverage and CI concurrency increase.

## 5. Bugs & Stability

| Severity | Item | Description | Fix PR |
|----------|------|-------------|--------|
| Medium | [Issue #1193](https://github.com/moltis-org/moltis/issues/1193) | Flaky test: push fanout timeout assertion races under full-suite load (2/3 failures on idle macOS) | None yet |
| Low | [PR #1191](https://github.com/moltis-org/moltis/pull/1191) | `moltis sandbox build` fails on every pre-built image due to stale Go module path | PR #1191 |
| Low | [PR #1192](https://github.com/moltis-org/moltis/pull/1192) | `wacrawl` skill install broken after org rename | PR #1192 |
| Low | [PR #1194](https://github.com/moltis-org/moltis/pull/1194) | `just local-validate-full` crashes on macOS bash 3.2 with unbound variable | PR #1194 |

The flaky test (#1193) is the most concerning stability signal — it indicates a real race in the gateway push fanout mechanism that may affect production reliability under load. No fix PR exists yet.

## 6. Feature Requests & Roadmap Signals

- **[PR #1190](https://github.com/moltis-org/moltis/pull/1190)** — Durable CalDAV and channel-history connectors. This is the most significant feature work this cycle and suggests the roadmap is moving toward persistent, cross-platform data integrations with local-first principles (bounded full-text search, atomic snapshots, projections). If merged, this would likely ship in the next minor release.

No explicit user-requested feature issues were opened today; the feature pipeline appears to be driven by internal roadmap priorities rather than community proposals.

## 7. User Feedback Summary

- **Pain point — macOS development friction:** Two of four PRs address macOS-specific issues (bash 3.2 compatibility, Go module path mismatches). This suggests the project may not have robust CI coverage on macOS, and local contributors are hitting environment-specific breakages.
- **Pain point — Upstream organizational changes:** The `wacrawl` and `gogcli` renames to the `openclaw` org broke install paths. Users relying on pre-built sandbox images or the `wacrawl` skill would be directly impacted.
- **Satisfaction signal:** The CalDAV + channel connector PR (#1190) received no negative feedback or objections in comments, indicating strong alignment with user needs for durable, provider-neutral integrations.

## 8. Backlog Watch

- **[Issue #1193](https://github.com/moltis-org/moltis/issues/1193)** — Open since 2026-08-13 with no comments or assigned fix. The flaky test is the highest-priority backlog item; left unresolved it will erode CI trust and mask real regressions. Maintainer attention is recommended.
- **[PR #1190](https://github.com/moltis-org/moltis/pull/1190)** — Open since 2026-08-11 (3 days) with no review activity noted. This is the largest feature PR and its delay may slow the next release cadence.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>



# CoPaw Project Digest — 2026-08-14

## 1. Today's Overview

CoPaw is experiencing exceptionally high development velocity, with **45 issues** and **50 PRs** updated in the last 24 hours — a strong indicator of a project at the peak of its release cycle. The v2.1.0 major release shipped today alongside a beta patch, introducing a native OS-shell desktop environment and a host of internal fixes. Activity is heavily concentrated around v2.1.0 stabilization, with 17 issues closed and 19 PRs merged in a single day. Security concerns around plugin permissions and API exposure have surfaced prominently, suggesting the growing user base is exercising the platform in production-like environments.

---

## 2. Releases

### v2.1.0 — Major Release
**Key additions (QwenPaw OS Shell):**
- Open apps in movable, resizable windows with a launcher, taskbar, notifications, and saved layouts ([#6645](https://github.com/agentscope-ai/QwenPaw/pull/6645))
- Unified app catalog across installed apps and marketplace in the App Center

### v2.1.0-beta.5 — Patch Release
- `fix(chats)`: handle dict-like model responses ([#6816](https://github.com/agentscope-ai/QwenPaw/pull/6816))
- `fix(memory)`: simplify long-term memory guidance ([#6942](https://github.com/agentscope-ai/QwenPaw/pull/6942))
- `docs(website)`: website Files workspace fixes

> **Migration note:** v2.1.0 introduced a new desktop shell architecture. Users on v2.0.x should review the upgrade guide, as session storage and workspace paths may have shifted.

---

## 3. Project Progress

### Closed / Merged PRs Today
| PR | Type | Summary |
|---|---|---|
| [#6636](https://github.com/agentscope-ai/QwenPaw/pull/6636) | fix | Chat history pagination + GZip compression — fixes 30s timeout on long chats |
| [#6652](https://github.com/agentscope-ai/QwenPaw/pull/6652) | fix | Enforce `max_iterations` server-side in MissionGate — prevents unbounded sub-agent spawning |
| [#6884](https://github.com/agentscope-ai/QwenPaw/pull/6884) | fix | Auto-Dream integration resilience against malformed LLM structured output |
| [#6387](https://github.com/agentscope-ai/QwenPaw/pull/6387) | feat | Install optional channel dependencies on demand |
| [#6989](https://github.com/agentscope-ai/QwenPaw/pull/6989) | chore | v2.1.0 release notes |

### Key Open PRs Advancing
- [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) — **Pawport import flow**: import settings, skills, plugins, and projects from Codex and Qoder
- [#6976](https://github.com/agentscope-ai/QwenPaw/pull/6976) — **Session-scoped multi-project directories**
- [#6302](https://github.com/agentscope-ai/QwenPaw/pull/6302) — **Unified provider discovery and model routing** with catalog-driven system
- [#6998](https://github.com/agentscope-ai/QwenPaw/pull/6998) — **Fix semaphore leaks** from unconsumed LLM streams (refs #5411)
- [#6990](https://github.com/agentscope-ai/QwenPaw/pull/6990) — **File I/O cache** for system prompts and skill files
- [#6975](https://github.com/agentscope-ai/QwenPaw/pull/6975) — **Reset context-usage ring after `/compact`**

---

## 4. Community Hot Topics

| Issue | Status | Comments | Topic |
|---|---|---|---|
| [#5856](https://github.com/agentscope-ai/QwenPaw/issues/5856) | Open | 4 | Tool call structure lost during context compaction → 400 errors |
| [#6921](https://github.com/agentscope-ai/QwenPaw/issues/6921) | Open | 6 | Agent stops after planning multi-step tasks without visual feedback |
| [#6992](https://github.com/agentscope-ai/QwenPaw/issues/6992) | Closed | 3 | **Security incident**: port 8088 exposed without auth, plugin RCE via marketplace |
| [#6916](https://github.com/agentscope-ai/QwenPaw/issues/6916) | Closed | 2 | Plugins can silently create cron jobs and inject messages without approval |
| [#6847](https://github.com/agentscope-ai/QwenPaw/issues/6847) | Open | 4 | Antivirus flagging QwenPaw during task execution |
| [#7003](https://github.com/agentscope-ai/QwenPaw/issues/7003) | Open | 2 | **ViBo memory proposal**: 97.5% token reduction for agent memory |
| [#6811](https://github.com/agentscope-ai/QwenPaw/issues/6811) | Closed | 5 | OpenAI `disable_thinking` ignored during scroll eviction summary |

**Underlying themes:**
- **Context compaction reliability** is the #1 technical pain point (#5856, #6951, #6811) — multiple interrelated bugs in the scroll/compact pipeline.
- **Security & trust** is the #1 community concern — two critical plugin permission issues and one active port-exposure incident in a single week.
- **Agent reliability in multi-step workflows** (#6921, #6768) suggests the planner-executor loop needs robustness improvements.

---

## 5. Bugs & Stability

| Issue | Severity | Summary | Fix PR |
|---|---|---|---|
| [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) | **High** | v2.1.0 regression: agent state saved to wrong session file under concurrent sessions (Feishu WebSocket) | None yet — workaround: revert to v2.0.1 |
| [#7007](https://github.com/agentscope-ai/QwenPaw/issues/7007) | **High** | Windows Desktop TUI crashes with `transport: Connection closed` — `qwenpaw.exe` rejects `-m qwenpaw acp` | None yet |
| [#6951](https://github.com/agentscope-ai/QwenPaw/issues/6951) | **Medium** | After scroll compaction, pre-compaction chat history is invisible in UI; only eviction index shown | [#6975](https://github.com/agentscope-ai/QwenPaw/pull/6975) (partial) |
| [#7008](https://github.com/agentscope-ai/QwenPaw/issues/7008) | **Medium** | Anthropic content moderation triggers false positive on historical non-sensitive images in long conversations | None yet |
| [#6955](https://github.com/agentscope-ai/QwenPaw/issues/6955) | **Medium** | Probabilistic crash on startup — `asyncio.windows_events` `finish_socket_func` exception | None yet |
| [#7005](https://github.com/agentscope-ai/QwenPaw/issues/7005) | **Low** | Enabling Shabox causes UV to fail writing to `~/.cache/uv` | Workaround: add write policy |

> **Critical note:** The v2.1.0 concurrent-session regression (#7011) and Windows TUI crash (#7007) are both high-severity and lack active fix PRs. A hotfix release should be prioritized.

---

## 6. Feature Requests & Roadmap Signals

| Request | Issue/PR | Likelihood for Next Release |
|---|---|---|
| Session-scoped multi-project directories | [#6976](https://github.com/agentscope-ai/QwenPaw/pull/6976) (open PR) | **High** — already in review |
| Embeddable chat UI (no sidebar/header, URL-based API key) | [#6970](https://github.com/agentscope-ai/QwenPaw/issues/6970) | Medium |
| Unified tool panel with web preview & interactive terminal | [#7013](https://github.com/agentscope-ai/QwenPaw/issues/7013) | Medium |
| Session-level model selection (per-tab) | [#7012](https://github.com/agentscope-ai/QwenPaw/issues/7012) | Medium |
| Background/daemon mode for server SSH usage | [#7010](https://github.com/agentscope-ai/QwenPaw/issues/7010) | Medium |
| ViBo memory compression (97.5% token reduction) | [#7003](https://github.com/agentscope-ai/QwenPaw/issues/7003) | Low — research-stage proposal |
| Import flow from Codex/Qoder (Pawport) | [#6960](https://github.com/agentscope-ai/QwenPaw/pull/6960) | **High** — open PR |
| Automatic real-time injection into context | [#6283](https://github.com/agentscope-ai/QwenPaw/issues/6283) | Low |

---

## 7. User Feedback Summary

**Pain points:**
- **Agent spontaneity failures** (#6921, #6768): Users report agents stopping after planning a multi-step task without executing, requiring manual "继续" prompts. Multi-step financial data import tasks have caused agents to hang for hours (#6768). This is the dominant workflow complaint.
- **Context compression breaks UX** (#6951, #5856): After `/compact`, users lose visibility into their full conversation history. Structured tool-call data is permanently lost, causing downstream 400 errors.
- **False-positive security alerts** (#6847): Antivirus software frequently kills the QwenPaw process during task execution, disrupting workflow.
- **Plugin permission gaps** (#6916, #6992): Users are alarmed that installed plugins can create cron jobs, persist SSH backdoors, and execute arbitrary commands without any approval gate — especially after the active port-exposure incident.
- **Server deployment friction** (#7010): No true daemon mode means QwenPaw cannot be run headlessly over SSH, limiting cloud/server use cases.

**Satisfaction signals:**
- Positive feedback on the v2.1.0 OS shell concept and desktop window management.
- Strong community engagement on memory efficiency and long-term agent state (#7003).
- Pawport import flow (#6960) addresses a real onboarding need from users migrating from other agent platforms.

---

## 8. Backlog Watch

| Issue | Age | Why It Needs Attention |
|---|---|---|
| [#5856](https://github.com/agentscope-ai/QwenPaw/issues/5856) — Tool call structure lost during context compaction | ~37 days | Blocks reliable tool-use workflows; causes 400 errors. No active fix PR. |
| [#6100](https://github.com/agentscope-ai/QwenPaw/issues/6100) — Workspace lost on v1→v2 upgrade | ~31 days | Data loss risk during migration; affects upgrading users. |
| [#6768](https://github.com/agentscope-ai/QwenPaw/issues/6768) — Agent infinite loop after multi-step task | ~8 days | Severity: session blocked for hours. No fix PR yet. |
| [#6992](https://github.com/agentscope-ai/QwenPaw/issues/6992) — Port exposure + plugin RCE (security incident) | 1 day | Closed but no visible remediation PR. Needs a security advisory or hotfix. |
| [#6916](https://github.com/agentscope-ai/QwenPaw/issues/6916) — Plugin silent cron job injection | 3 days | Permission model gap affecting all installed plugins. No fix PR yet. |
| [#7007](https://github.com/agentscope-ai/QwenPaw/issues/7007) — Windows TUI connection closed | 1 day | Blocks Windows users from starting sessions on v2.1.0. High severity, no fix. |
| [#7011](https://github.com/agentscope-ai/QwenPaw/issues/7011) — Concurrent session state corruption | 1 day | v2.1.0 regression, high severity, no fix PR. |

---

**Project Health Assessment:** CoPaw is in an aggressive release phase with strong contributor momentum (50 PRs/day). However, the v2.1.0 launch has introduced at least two high-severity regressions (#7011, #7007) and several medium-severity stability issues (#6951, #7008, #6955) that remain unaddressed. The security incidents (#6992, #6916) require a coordinated response. Prioritizing a v2.1.1 hotfix for the concurrent-session and Windows TUI bugs, alongside a security advisory, would strengthen community trust significantly.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>



# ZeroClaw Project Digest — 2026-08-14

## 1. Today's Overview

ZeroClaw shows robust development velocity with **50 issues** and **50 PRs** updated in the last 24 hours, though no new releases were cut. Activity is heavily weighted toward open work (37 open issues, 40 open PRs), with 13 issues closed and 10 PRs merged today — a healthy merge-to-open ratio of ~25%. The project remains in a pre-release hardening phase focused on the v0.9.0 auth/security/gateway workstream, with multiple RFCs at the maintainer decision queue and several high-risk security fixes landing. The contributor base is active across the board (principal contributors, distinguished contributors, and trusted contributors all submitting), indicating strong community engagement.

## 2. Releases

**No new releases today.** The project continues targeting the v0.9.0 milestone. A recently closed RFC (#9712) introduced support for **weekly lettered cuts within a numbered release line** (e.g., `v0.8.5-a`, `v0.8.5-b`), which may facilitate faster iteration on the upcoming release train once v0.9.0 work solidifies.

- [RFC #9712: Weekly lettered cuts](https://github.com/zeroclaw-labs/zeroclaw/issues/9712) *(CLOSED)*

## 3. Project Progress

### Merged / Closed PRs Today

| PR | Author | Summary |
|---|---|---|
| [#9966](https://github.com/zeroclaw-labs/zeroclaw/pull/9966) | NiuBlibing | **fix(container):** Match nested fixture manifests by glob — fixes Docker dependency pre-fetch for crates nested beyond one level. |
| [#9709](https://github.com/zeroclaw-labs/zeroclaw/pull/9709) | Project516 | **fix(tts):** Clean up Edge TTS temp output on every error path — resolves leaked `.mp3` artifacts. |
| [#9705](https://github.com/zeroclaw-labs/zeroclaw/pull/9705) | Project516 | **fix(config):** Allow `config set` on existing hyphenated cron aliases (#9652). |
| [#9969](https://github.com/zeroclaw-labs/zeroclaw/pull/9969) | Audacity88 | **fix(gateway):** Contain filesystem dashboard assets — canonicalize paths, reject symlink escapes. |
| [#9932](https://github.com/zeroclaw-labs/zeroclaw/pull/9932) | JordanTheJet | **ci(codeql):** Drop false-positive `hard-coded-cryptographic-value` query (27 FPs). |
| [#9639](https://github.com/zeroclaw-labs/zeroclaw/pull/9639) | Audacity88 | **docs(architecture):** Document provider routing lifecycle — source-grounded reference page. |
| [#9674](https://github.com/zeroclaw-labs/zeroclaw/pull/9674) | Audacity88 | **fix(infra):** Preserve session queue serialization during eviction — RAII guard prevents race. |

### Notable Open PRs Advancing

- [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713) — **SSRF gate for file_download** — adds `allowed_private_hosts` opt-in to prevent accidental localhost/metadata-route exploitation.
- [#9109](https://github.com/zeroclaw-labs/zeroclaw/pull/9109) — **Native Hailo-Ollama provider** — dedicated provider for Hailo-Ollama's `/api/chat` and `/api/tags`.
- [#9203](https://github.com/zeroclaw-labs/zeroclaw/pull/9203) — **SOP authenticated HTTP fan-in** — wires `POST /sop/{*rest}` with exact-match webhook dispatch.
- [#9942](https://github.com/zeroclaw-labs/zeroclaw/pull/9942) — **vi_verify withheld-tool reporting** — surfaces the security capability notice through the config surface, not just runtime trace.
- [#9986](https://github.com/zeroclaw-labs/zeroclaw/pull/9986) — **Agent export to portable bundle** — `zeroclaw agents export <alias>` writes manifest + config closure + workspace tree.
- [#9968](https://github.com/zeroclaw-labs/zeroclaw/pull/9968) — **Compatible-provider integrity** — fails closed on invalid Zhipu JWT instead of forwarding raw credential as bearer token (P1 security).
- [#9527](https://github.com/zeroclaw-labs/zeroclaw/pull/9527) — **Rust toolchain bump to 1.97.1** — routine toolchain update, source floor remains 1.96.0.

## 4. Community Hot Topics

| Rank | Item | Comments | Type | Link |
|---|---|---|---|---|
| 1 | RFC: Goal mode v1 — bounded foreground Matrix work | 20 | RFC/Agent | [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) |
| 2 | RFC: Per-execution confirmation tier for high-risk shell commands | 18 | RFC/Security | [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) |
| 3 | Tracker: Maintainer decision queue for RFCs | 13 | Tracker | [#8692](https://github.com/zeroclaw-labs/zeroclaw/issues/8692) |
| 4 | RFC: Decouple memory lifecycle from storage backends | 12 | RFC/Architecture | [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) |
| 5 | Bug: vi_verify evaluates constraints without verifying credential chain | 12 | Bug/Security | [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) |
| 6 | RFC: Runtime-owned conversation sessions & transport adapters | 11 | RFC/Architecture | [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) |

**Analysis:** The community is deeply engaged with **agent goal management** (#8303) and **shell command security policy** (#7155) — both are mature RFCs with revision cycles and maintainer scope confirmations. The **maintainer decision queue** (#8692) itself is a hot topic, signaling the team is accumulating design decisions faster than they can be routed. The **verifiable-intent credential chain bug** (#9328) and the **memory lifecycle RFC** (#6850) both reflect growing pains as the agent runtime scales in capability. Users clearly want stronger guarantees around agent autonomy bounds and security boundaries.

## 5. Bugs & Stability

### Critical / High Severity (Open)

| Issue | Severity | Summary | Fix PR? |
|---|---|---|---|
| [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) | P2 / risk:high | `vi_verify` evaluates constraints without verifying the credential chain — security bypass risk | PR [#9942](https://github.com/zeroclaw-labs/zeroclaw/pull/9942) addresses reporting surface; root-cause fix pending |
| [#9389](https://github.com/zeroclaw-labs/zeroclaw/issues/9389) | P1 / risk:high *(CLOSED)* | Unauthenticated POST `/api/pair` keys lockout on attacker-supplied header | **Closed** — likely fixed |
| [#9929](https://github.com/zeroclaw-labs/zeroclaw/issues/9929) | P1 / risk:high | Headless SOP step turns get session path but never persist to session store | Open — blocked, no fix PR yet |
| [#9945](https://github.com/zeroclaw-labs/zeroclaw/issues/9945) | P2 / risk:high | Browser tool exposes 16 of 100+ agent-browser commands — iframes/dialogs/tabs unreachable | Open — blocked, accepted |

### Medium / Low Severity (Closed Today)

| Issue | Summary | Status |
|---|---|---|
| [#9710](https://github.com/zeroclaw-labs/zeroclaw/issues/9710) | macOS desktop screenshot temp files not cleaned on early return | **Closed** — PR [#9709](https://github.com/zeroclaw-labs/zeroclaw/pull/9709) landed |
| [#9706](https://github.com/zeroclaw-labs/zeroclaw/issues/9706) | Edge TTS temp output leaked on error path | **Closed** — PR [#9709](https://github.com/zeroclaw-labs/zeroclaw/pull/9709) landed |
| [#9951](https://github.com/zeroclaw-labs/zeroclaw/issues/9951) | WeChat channel code + 51 tests never compile in CI | **Closed** — acknowledged, no fix yet (low priority) |
| [#9643](https://github.com/zeroclaw-labs/zeroclaw/issues/9643) | wit/VERSIONING.md missing enum-variant classification breaks plugin compat | **Closed** — docs gap identified |

**Stability Assessment:** Two P1 bugs were resolved today (gateway pairing lockout, session queue eviction race). The **SOP headless persistence bug** (#9929) and **browser tool coverage gap** (#9945) remain open and could impact production reliability for power users.

## 6. Feature Requests & Roadmap Signals

| Issue | Summary | Signal |
|---|---|---|
| [#9631](https://github.com/zeroclaw-labs/zeroclaw/issues/9631) | Send stable `session_id` to OpenRouter for prompt-cache savings | **Strong cost-optimization signal** — directly reduces API spend for OpenRouter users |
| [#5907](https://github.com/zeroclaw-labs/zeroclaw/issues/5907) | Opt-in LSP support for ZeroCode coding workflows | **Agent-quality signal** — aligns with Claude Code / OpenCode parity |
| [#9810](https://github.com/zeroclaw-labs/zeroclaw/issues/9810) | Load Agent Plugins 1.0 skill & MCP packages | **Ecosystem signal** — vendor-neutral plugin standard adoption |
| [#9895](https://github.com/zeroclaw-labs/zeroclaw/issues/9895) | Provider-grouped, paginated Telegram `/model` picker | **UX signal** — mobile usability improvement |
| [#9887](https://github.com/zeroclaw-labs/zeroclaw/issues/9887) | Downscale oversized images instead of dropping them | **Usability signal** — reduces hard failures for multimodal users |
| [#9880](https://github.com/zeroclaw-labs/zeroclaw/issues/9880) | Type-resolved peer policy instead of `Vec<String>` grammar | **Architecture signal** — type safety for authorization config |
| [#7929](https://github.com/zeroclaw-labs/zeroclaw/issues/7929) | Unify slash-command registries across web UI, ZeroCode TUI, channel runtime | **DX signal** — eliminates command drift across surfaces |

**Prediction for Next Release (v0.9.x):** The OpenRouter prompt-cache feature (#9631), image downscaling (#9887), and Agent Plugins 1.0 loading (#9810) are the most likely candidates for inclusion. The slash-command unification (#7929) and peer-policy typing (#9880) are deeper architecture changes that may push to v0.10.

## 7. User Feedback Summary

- **Cost concerns are prominent:** The OpenRouter prompt-cache request (#9631) notes that "a single conversation spawns dozens of LLM requests" with system prompt replay, directly impacting operational cost. This is a real pain point for power users.
- **Security paranoia is justified and rewarded:** Multiple high-risk issues (#9389, #9328, #9969) were filed by security-conscious users (including external auditors like `belumume`), and the team is responding with fixes. The verifiable-intent credential chain gap (#9328) suggests users are running real audits against the project.
- **Multimodal friction:** Users are hitting image-size limits (#9887) and browser-tool coverage gaps (#9945) — these are "it mostly works but not quite" complaints that degrade trust.
- **Mobile UX pain:** The Telegram model picker issue (#9895) highlights that text-based runtime commands are cumbersome on mobile, a growing use case as channel support expands.
- **Plugin ecosystem anticipation:** The Agent Plugins 1.0 RFC (#9810) indicates users want a vendor-neutral plugin story, not just ZeroClaw-specific tooling.

## 8. Backlog Watch

| Issue | Days Open | Why It's Stalled | Risk |
|---|---|---|---|
| [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) — Goal mode v1 RFC | ~51 days | Awaiting maintainer review; scope confirmed but implementation not started | **High** — core agent capability |
| [#7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) — Shell confirmation tier RFC | ~72 days | Revision 3 accepted, normative scope narrowed, but no implementation PR yet | **High** — security-critical |
| [#9328](https://github.com/zeroclaw-labs/zeroclaw/issues/9328) — vi_verify credential chain | ~51 days | Bug confirmed, reporting fix in #9942 but root-cause fix pending | **High** — security bypass |
| [#6850](https://github.com/zeroclaw-labs/zeroclaw/issues/6850) — Memory lifecycle RFC | ~84 days | Author action needed; design phase long-running | **Medium** — architectural |
| [#9487](https://github.com/zeroclaw-labs/zeroclaw/issues/9487) — Runtime-owned sessions | ~48 days | Needs maintainer review; tied to #9488/#9600 ownership boundary | **High** — cross-cutting |
| [#9600](https://github.com/zeroclaw-labs/zeroclaw/issues/9600) — Session-persistence tracker | ~45 days | Four independent workstreams, no designated owner yet | **High** — coordination risk |
| [#9598](https://github.com/zeroclaw-labs/zeroclaw/issues/9598) — SOP permission contract | **Blocked** | Awaiting v0.9.0 SOP authorization contract resolution | **Medium** — blocks SOP feature |
| [#9323](https://github.com/zeroclaw-labs/zeroclaw/issues/9323) — Execution-tree iteration budget | **Blocked** | `shared_budget` is `None` everywhere in production; needs ownership decision | **Medium** — correctness |

**Maintainer Attention Required:** The **v0.9.0 auth/security/gateway tracker** (#7432) and the **RFC decision queue** (#8692) are the two coordination hubs that, if unblocked, would unblock a cascade of the above items. The session-persistence ownership ambiguity (#9600) is the single highest-leverage bottleneck — four workstreams are touching the same contract without a designated owner.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/xavier9802/agents-radar).*