# Morphir - Semi-Annual Report  2026 H2

**Project Maintainers:** Attila Mihaly (Morgan Stanley), Damian Reeves (Capital One), Michelle Chan (Disney), Nwokafor Choongsaeng (⟨TODO: organization⟩), Peter Smulovics (Morgan Stanley), Stephen Goldbaum (DataHub)

**Repository:** https://github.com/finos/morphir

**Links:**

- https://github.com/finos/morphir-elm — reference implementation and engine
- https://lcr-interactive.finos.org — FINOS-hosted production service (US LCR)
- https://insights.linuxfoundation.org/project/morphir — LFX Insights

> _Metrics below are drawn from the GitHub API across the six actively-developed repositories in the Morphir family (`morphir`, `morphir-elm`, `morphir-scala`, `morphir-jvm`, `morphir-dotnet`, `morphir-examples`) over the trailing-12-month window 2025-08-05 → 2026-08-05, and from LFX Insights. Lifecycle stage: **Graduated**. License: Apache-2.0._

# Project Overview

Morphir captures business logic as data. A domain model written in a strict, declarative language compiles to the **Morphir IR** — a typed, backend-agnostic intermediate representation — from which the toolchain deterministically renders both an interactive visualization for non-technical users (decision tables, execution traces) and production code for multiple targets (Scala, TypeScript, Spark, Snowpark, JSON Schema).

The value proposition for financial services is transparency and portability of regulated logic. The reference proof point is [`finos/open-reg-tech-us-lcr`](https://github.com/finos/open-reg-tech-us-lcr): the US Federal Reserve Liquidity Coverage Ratio modeled end-to-end and published as a public interactive site at `lcr-interactive.finos.org`. The same model produces the visualization a regulator or business analyst can read and the Scala/Spark code that runs the calculation — with the translation between them performed by human-written compiler code, not by inference.

**This reporting period marks a deliberate strategic repositioning of the project**, described below.

# Current Status

## Strategic repositioning: from portable business logic to verifiable knowledge

Morphir's original framing — portable business logic for everything — was built for a market where writing code was the expensive part. That market changed. Code generation is now cheap and abundant; **trust is the scarce resource**. A maintainer review conducted in July 2026 concluded that Morphir's core thesis became *more* valuable under that shift, not less, for a specific structural reason: a deterministic IR-to-code compiler is a categorically stronger correctness story than AI reviewing AI, and a strict, total, side-effect-free language is exactly what makes LLM-authored logic mechanically verifiable rather than merely plausible.

The same review identified the project's real failure honestly: **distribution, not thesis**. Independent public footprint outside FINOS-controlled channels is close to zero after six years — no Hacker News, Reddit, or Stack Overflow presence; the flagship 2025 OSFF London talk has ~120 views. Nobody rejected Morphir. Very few people ever saw it. The barrier was that extracting any value required installing a CLI, configuring a project, and writing Elm.

The maintainers' conclusion, reaffirmed in an August 2026 maintainer discussion ahead of this review, is that the corrective work is primarily **community engagement and ecosystem integration**, not further technical depth. The project has more capability than it has reach.

## Substrate — the strategic direction

**Substrate** ([PR #645](https://github.com/finos/morphir/pull/645), opened April 2026) is the direction the maintainers are setting for Morphir's next phase.

Substrate turns the documents an organization already writes — specifications, regulations, domain models, runbooks — into a structured, link-typed, **mechanically verifiable corpus** that both humans and LLMs can read, edit, and act on. The medium is plain GitHub-flavored markdown: no custom syntax, renders natively on GitHub, written by humans with LLM assistance. Structure is carried by ordinary markdown features — especially **links between documents**, where every reference to a concept, type, or operation points at its definition. The corpus thereby accumulates a semantic knowledge graph that tooling can traverse, type-check, and slice for LLM context, without constraining how authors write prose.

Verification is layered — structural validity, link resolution, type compatibility, and embedded test cases that actually execute — and findings are reported against the originating prose rather than an opaque intermediate form. A `substrate` CLI provides context extraction, corpus validation, corpus-wide safe refactoring, embedded test execution, and versioned package management.

This is continuous with Morphir's thesis rather than a departure from it: the same insight that logic should be captured as inspectable, portable data, applied to the medium institutions actually use. The maintainers have agreed to **merge PR #645 into `finos/morphir` under Apache-2.0**, establishing the direction publicly; further development will be paced against community engagement rather than pursued in isolation.

## Regulatory digitization — FR 2052a

The most substantial Substrate artifact to date is a working regulatory corpus: the **Federal Reserve FR 2052a Complex Institution Liquidity Monitoring Report** (instructions dated 2025-02-26; 106 pages plus Appendices I–VIII) extracted from source PDF into structured markdown, with all product definitions and all eight appendices curated — including the LCR, STWF, and NSFR mapping appendices — and a `knowledge/` corpus layer defining counterparty, account type, maturity bucket, retail outflow rate, and related concepts as typed, linked, testable definitions.

Maintainers reviewing this material observed that the markdown rendering is materially more usable than the source PDF format for both human and machine consumption — which is the point. This directly extends the LCR work that made Morphir a candidate for FINOS regulatory digitization efforts several years ago, and it underpins a collaboration request in TOC Support Needed below.

## Other activity this period

- Continued development across `morphir` (Go/Rust toolchain), `morphir-scala`, and `morphir-dotnet`.
- The `morphir mcp` command (`addModule` / `setTestCases` tools) is merged into `morphir-elm` main, enabling the LLM-authoring workflow demoed at OSFF London 2025.
- 15 releases published across the family; `morphir` at v0.3.3, `morphir-scala` at v0.5.0-M04.
- The LCR reference implementation was used for a live demonstration to Morgan Stanley during this period.
- **Supply-chain hardening in response to the 2026 npm compromise incidents:** the project adopted a mandatory quiet period before consuming newly-published dependency versions, reducing exposure to compromised-package windows.
- Biweekly project meetings resumed in May 2026 after a hiatus (see Challenges).

# Community & Contribution Metrics

_Trailing 12 months (2025-08-05 → 2026-08-05), six active repositories:_

| Metric | Value |
|---|---|
| Human commits (excl. bots) | ~299 |
| Of which by the single most active contributor | **271 (~91%)** |
| GitHub Copilot agent commits | 53 |
| Active contributors per quarter (LFX) | 5 |
| Pull requests merged | 432 |
| Open issues (family-wide) | ~411 |
| Of which untouched for >12 months | **~326** |
| Releases published | 15 |
| `morphir-elm` npm downloads | **18,769** |
| GitHub stars / forks (umbrella) | 204 / 65 |

**Adoption indicators:**

- **18,769 npm downloads** of `morphir-elm` over the trailing year — the strongest quantitative adoption signal the project has, and broadly comparable to peer FINOS projects at this stage.
- `lcr-interactive.finos.org` — a FINOS-hosted production service built on Morphir.
- A published Capital One case study (co-published with FINOS).
- A Snowflake-Labs fork of `morphir-elm` (motivation undocumented, but an unaffiliated-party signal).
- ⟨TODO: current adopter organizations — Graduated requires active use by ≥5 organizations with ≥3 in financial services, and 2 publicly shareable adoption stories. List named organizations here; the TOC accepts private disclosure where public naming isn't possible.⟩

**LFX Insights** rates the project *Healthy* overall while explicitly flagging that one organization accounts for >51% of contributions and one individual accounts for >51% of contributions.

# Challenges & Blockers

The maintainers want to be direct with the TOC rather than have these surfaced during the review.

**1. Contributor and organizational concentration — the primary risk.** A single contributor accounts for ~91% of human commits family-wide, and LFX reports 5 active contributors per quarter. The maintainer roster spans multiple organizations on paper, but day-to-day capacity does not. This is the project's most serious health issue and the one where TOC help would matter most.

**2. Declining community activity, and limited maintainer bandwidth for outreach.** Contributor interest measurably declined over this period. The maintainers' assessment is that this reflects a broad reallocation of open-source attention toward AI-centric work — and the maintainer team followed that shift rather than resisting it, which is what Substrate represents. The harder constraint is bandwidth: all maintainers carry this alongside full-time roles, and attending additional FINOS project meetings is not realistic. The team has therefore committed to **asynchronous-first engagement** — email and Slack with adjacent projects and working groups — rather than promising meeting attendance it cannot sustain. This is stated plainly so the TOC can calibrate expectations.

**3. Issue and PR responsiveness — currently out of compliance.** Approximately 326 open issues have gone untouched for more than 12 months. `morphir-elm` — the repository with the highest external adoption — closed **zero** issues in the reporting window. Two external community pull requests ([#627](https://github.com/finos/morphir/pull/627), [#628](https://github.com/finos/morphir/pull/628)) have been open without review since March 2026. For a project actively trying to rebuild its contributor funnel, unreviewed outside contributions are the worst possible signal, and the maintainers own this failure.

**4. OSPS Baseline Level 3 — gaps acknowledged.** Graduated status requires Maturity Level 3. No `SECURITY.md` is currently published in any repository in the family, and the project has no `project-data.yaml` (Security Insights v2.1.0) filed in the TOC repository. A remediation plan is in the Roadmap section.

**5. Public roadmap — currently absent.** Graduated requires that feature work adhere to a public roadmap. No `ROADMAP.md` exists, and the Substrate work proceeded largely on a fork branch before [PR #645](https://github.com/finos/morphir/pull/645) was opened. The strategic direction has been real but not publicly legible — a governance gap being closed as part of this review.

**6. Community meetings — partially out of compliance.** Biweekly meeting agenda issues resumed on 2026-05-28 and have run on schedule since, but there is a gap from 2025-11-27 to 2026-05-28 with no meetings held, and recent agenda issues carry no recorded attendance or approved minutes.

**7. AI-assisted contribution attribution and CLA friction — a cross-project issue.** AI coding tools default to inserting themselves as commit co-authors, which creates CLA complications: a non-human "contributor" has no CLA on file. Maintainers have had to modify agent-instruction files (`CLAUDE.md`, `AGENTS.md`) in individual repositories to suppress this behavior. Separately, some member firms — Capital One among them — require disclosure of whether a contribution was AI-assisted, and there is currently no consistent FINOS-wide convention for recording that. This is not specific to Morphir and would be better solved once, at foundation level, than repeatedly per project. A maintainer has raised it with FINOS staff; it is restated here as a TOC support request.

**8. Repository sprawl.** The project spans 16 non-archived repositories, several of which are dormant (`morphir-jvm`: zero releases and 6 merged PRs in 12 months; `morphir-gleam`, `morphir-zig`, `morphir-moonbit`, `morphir-editor` at or near zero activity). Maintaining nominal ownership of dormant repositories dilutes attention and distorts health signals. A consolidation proposal is in the Roadmap.

**9. Release cadence.** The umbrella repository remains pre-1.0 (v0.3.3, January 2026) and `morphir-elm`'s last release was September 2025 — inconsistent with the Graduated expectation of a production-ready major release.

# Roadmap & Goals for Next 6 Months

## Compliance remediation (ordered by priority)

| # | Item |
|---|---|
| 1 | Resume recording meeting attendance and approving minutes on the biweekly agenda issues |
| 2 | Complete `MAINTAINERS.md` — organizations for all entries |
| 3 | Merge [PR #645](https://github.com/finos/morphir/pull/645) into `finos/morphir` under Apache-2.0, resolving AI contributor-attribution/CLA issues in the commit history |
| 4 | Publish `SECURITY.md` across all active repositories |
| 5 | Publish `ROADMAP.md` in `finos/morphir` covering the Substrate direction and the engagement goals below |
| 6 | Add root `CONTRIBUTING.md` to `finos/morphir` and fix the broken README link |
| 7 | Review the two open external community PRs (#627, #628) |
| 8 | File `projects/morphir/project-data.yaml` (Security Insights v2.1.0) in the TOC repository |
| 9 | Complete OSPS Baseline Level 3 self-assessment and publish the gap list |
| 10 | Triage the stale issue backlog — review or close the ~326 issues untouched for >12 months |
| 11 | Propose archival of dormant repositories to the TOC |

## Community and ecosystem engagement — the primary goal this cycle

The maintainers treat this as the most important section of the report. The diagnosis is that Morphir's problem is reach, not capability, and the corrective work is integration with the rest of the FINOS ecosystem.

- **CALM.** The clearest integration opportunity: CALM models system architecture, Morphir models the business logic inside it, and the two compose naturally. A maintainer is taking the action to schedule a working session between the Morphir and CALM teams. CALM's own 2026 H2 report independently flags interest in cross-project alignment.
- **Open RegTech.** Direct thematic overlap with the FR 2052a corpus and the LCR reference implementation. The project intends to engage this group asynchronously and offer the regulatory-markdown work as a shared asset.
- **AI Readiness.** Morphir's repositioning — verifiable, constrained, machine-authored logic — is squarely within this group's remit, and the maintainers want Morphir represented in that conversation.
- **TraderX.** Candidate integration demonstrating Morphir-modeled logic inside a realistic trading application.
- **FluxNova.** Identified as the most tractable near-term demonstration: showing Morphir integrated into a workflow. Platform constraints make a serverless/Lambda execution demonstration harder, so scope will be set to what can be shown convincingly.
- **Academic collaboration — University of Kentucky.** A researcher working on AI specifications has published work on extracting business intent from requirements documents, which closely parallels the Substrate thesis and is actively seeking real-world use cases and collaborators. Maintainer introductions are in progress, and the project sees a natural fit: Morphir and Substrate offer exactly the real-world regulatory corpora such research needs.
- **Knowledge engineering across the SDLC.** Ongoing maintainer work on positioning Morphir within the wider software lifecycle, distinguishing the two questions practitioners actually ask — *what does the system do today* versus *what must change to satisfy new intent* — and incorporating Morphir's schemas into language-agnostic requirements representations.

## Product goals

- **Ship the hosted Morphir playground.** A zero-install web front door where a visitor describes business rules in natural language and gets back a decision table they can read, test cases they can click through, and real generated code — in under three minutes, with no signup. This productizes the OSFF London 2025 demo. Curated examples run as pre-recorded transcripts (no inference cost); custom prompts use the visitor's own API key, called directly from the browser and never touching the server. **The project is not asking FINOS to fund LLM inference.**
- **Publish a correctness evaluation**: the same prompts through LLM-plus-Morphir versus LLM-plus-general-purpose-language, measured on unhandled cases and review effort, ideally against the US LCR specification. The playground makes Morphir visible; the eval makes the claim credible.
- **Advance the FR 2052a corpus** from structured extraction to a fully typed, tested knowledge corpus, as the flagship regulatory-digitization reference.
- **Rebuild the contributor funnel**: curate an accurate Good First Issue shortlist, restore review responsiveness as a standing commitment, and recruit maintainers from additional member organizations.
- **Consolidate the repository footprint** so that remaining repositories all show genuine activity.

# TOC Support Needed

**1. Host the playground — the single most valuable thing the TOC can do.** The project is asking for a FINOS-hosted deployment and subdomain (e.g. `try.morphir.finos.org`), reusing the operational pattern already proven by `lcr-interactive.finos.org` on AWS ECS, plus whatever legal/security sign-off an LLM-fronted public service requires. The ask is deliberately small: because curated examples are pre-recorded and custom prompts run on visitors' own keys, **FINOS funds no inference** — the server performs compilation and evaluation only. Specific question: who approves a new public service and subdomain, and should the existing manual ECS deployment process be reused or replaced with CI-driven deploys?

**2. Broker the regulatory-digitization collaboration.** FINOS has reinitiated its push on digitizing regulations and has brought in dedicated expertise for it. The approach of capturing regulations as enriched markdown is, as far as the maintainers can tell, the same idea Substrate arrived at independently — and Morphir already holds a curated FR 2052a corpus and a working LCR reference implementation. The maintainers are asking the TOC to convene a joint working session and to evaluate Morphir/Substrate as candidate technical infrastructure for that effort. This is the collaboration with the clearest mutual payoff on the table.

**3. Warm introductions to adjacent FINOS projects and working groups.** Specifically CALM, Open RegTech, AI Readiness, TraderX, and FluxNova. The maintainers are committed to engaging all of these, but asynchronously — introductions and a shared channel will convert far better than meeting invitations the team cannot reliably attend.

**4. Help address contributor concentration.** Concretely: a call for contributors through FINOS channels and the newsletter, and warm introductions to member firms working on regulatory reporting, decision logic, or LLM context engineering — the areas where Substrate's value proposition lands directly.

**5. Foundation-level guidance on AI-assisted contributions.** As described in Challenges, AI coding agents inserting themselves as commit co-authors creates CLA problems, and member firms increasingly require disclosure of AI assistance. Morphir is hitting this now, but every FINOS project will. The maintainers ask the TOC to establish a consistent convention — attribution format, CLA treatment of agent co-authorship, and a disclosure standard — so projects stop solving it individually and inconsistently.

**6. Marketing and visibility.** The maintainers' own diagnosis is that Morphir's failure was distribution. FINOS controls reach the project does not: amplification for the playground launch, a speaking slot at the next OSFF, and a FINOS blog post on the verifiable-knowledge thesis would each move a number that six years of engineering has not.

**7. Community Development Plan and go-to-market, built with FINOS staff.** Graduated status requires demonstrated progress against such a plan. The maintainers would like staff support to build one around the repositioned direction rather than the original 2020 framing.

**8. Lifecycle guidance — raised by the maintainers, not waiting to be asked.** Given the metrics in this report, the maintainers want to open rather than avoid the question of whether Graduated remains the appropriate stage. Specifically: what evidence would the TOC need to see for Graduated status to remain appropriate, and would a time-boxed remediation plan against the OSPS Level 3 and concentration gaps be the preferred framing? The maintainers are committed to Morphir either way and would rather agree a realistic plan than defend an untenable position.

# Additional Information

- **The strategic assessment behind this report is documented and evidence-based**, drawing on a compiled knowledge base covering the full GitHub history of the main repositories, the LCR reference implementation, an independent public-sentiment survey, and the OSFF London 2025 talk. Maintainers are happy to share it with the TOC or the assigned liaison.
- **OSFF London 2025 talk:** "Amplify AI Productivity and Trust with Morphir" — https://www.youtube.com/watch?v=Dh7oiAMLp6Q
- **On AI-assisted development:** 53 commits in this window are authored by the GitHub Copilot agent. The maintainers regard this as consistent with the project's own thesis — constrained, reviewable machine-authored work — but do not count it as community growth, and it is reported separately above for that reason. See also the attribution and CLA issue raised in Challenges and TOC Support Needed.
- **On security posture:** beyond the OSPS remediation above, the maintainers note that Morphir's constrained IR is itself a supply-chain security property. Logic expressed in a total, side-effect-free language with no IO or FFI cannot exfiltrate data or execute arbitrary code regardless of who or what authored it — a meaningful argument as AI-generated dependencies proliferate, and one the project intends to make explicitly.
- The project maintains an active biweekly public meeting; agenda and minutes are tracked as GitHub issues under the `meeting` label in `finos/morphir`.
