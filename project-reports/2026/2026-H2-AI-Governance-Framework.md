# AI Governance Framework - Semi-Annual Report  2026 H2

**Project Maintainers:** Colin Eberhardt, Naresh Babu Deenadayalan, Asad Ateeque, Alvin Shih, Chamindra de Silva, Francesco Beltramini, Hugo Calderon

**Repository:** https://github.com/finos/ai-governance-framework

> _Metrics below are drawn from GitHub over the trailing-12-month window (2025-08-25 → 2026-08-25), which spans this H2 reporting period and the preceding half. Lifecycle stage: **Incubating**. Licence: CC BY 4.0. Site: https://air-governance-framework.finos.org_

# Project Overview

The **AI Governance Framework** (AIGF) is an open catalogue of the risks that arise when financial institutions deploy AI systems, and the mitigations that address them. Each entry is written to be evidenced — a firm can point at a control and show a supervisor what they do about it — and each is cross-referenced to the external frameworks institutions are already assessed against.

The framework is deliberately architecture-agnostic and vendor-neutral. It covers operational, security and regulatory risk for both generative and agentic AI systems, and is consumed as a website, as structured Markdown with YAML front matter that downstream tools can parse, and through an MCP server that exposes the catalogue to AI coding assistants.

# Current Status

- **v2 published** (2025-10-20), expanding the framework from generative AI into **agentic systems**: `ri-24` to `ri-29` cover agent action authorization bypass, tool-chain manipulation, MCP server supply-chain compromise, state-persistence poisoning, multi-agent trust-boundary violations and agent-mediated credential harvesting, with `mi-17` to `mi-23` as the matching mitigations.
- **Catalogue now stands at 23 risks, 23 mitigations and 4 published use cases** (credit risk analysis, autonomous wealth management, loan approval, anti-financial-crime investigation), with a fifth — buy-side portfolio allocation — in review.
- **Regulatory and standards mapping extended to 13 external frameworks**: EU AI Act, ISO 42001, NIST SP 800-53r5, NIST AI 600-1, OWASP LLM Top 10, OWASP Agentic (ASI), OWASP ML, FFIEC IT Booklets, SR 11-7, IOSCO Supervisory Toolkit, Agent Threat Rules, and UK and Canadian regulations. Each renders as a browsable reference page linking regulation to control.
- **[finos/aigf-mcp-server](https://github.com/finos/aigf-mcp-server)** — a Python MCP server exposing the catalogue to Claude, VS Code, Cursor and other MCP clients, with 11 read-only tools and runtime discovery against the FINOS repositories.
- **The framework was forked to seed a new FINOS project** — the [SDLC Common Controls Framework](https://github.com/finos-labs/SDLC-Controls-Framework) adopted AIGF's structure, look and cross-linking machinery, which is a strong signal that the catalogue format itself is reusable.
- **Leadership and practitioner training material** developed alongside the catalogue, with an eLearning conversion under way.
- **Contribution tooling**: deterministic pre-review checks that validate front matter, reference resolution, sequence collisions, cross-link conventions and amendments to approved specifications — introduced after a silent data defect reached `main` (see Challenges).

> **TODO (Asad):** add adoption evidence if we have any we can name — firms using it internally, citations in vendor or regulator material, conference talks. The TOC weighs this heavily and we currently assert reuse (SDLC Controls) but no named adopters.

# Community & Contribution Metrics

_GitHub (`finos/ai-governance-framework`), trailing 12 months (2025-08-25 → 2026-08-25):_

- **Contributors:** ~23 distinct commit authors in the window, of whom ~15 were first-time contributors. Author identities are split across several aliases, so these are approximate.
- **Commits:** 137 in the window.
- **Pull requests:** 66 opened, **47 merged**; **11** currently open.
- **Issues:** 88 opened, 85 closed; **27** currently open — down from 53 following a backlog review in August 2026 that closed 28 issues, each with a stated reason.
- **Maintainers:** 7, spanning Scott Logic, Citi, FINOS and independent contributors.
- **Repository:** 98 stars, 58 forks. Created April 2025, so the project is ~16 months old.
- **Ecosystem:** one downstream FINOS project seeded from the framework, plus an MCP server and a reference-architecture collaboration.

> **TODO (Asad):** pull the LFX Insights figures for AIGF — quarterly-active contributors, retention, merge lead time, issue-resolution time, and the health rating. The TOC reviews LFX data live during the session, so it is better for us to have read it first. https://insights.linuxfoundation.org/

# Challenges & Blockers

- **Contribution concentration.** The top contributor accounts for ~41% of commits in the window and the top two for ~53%. This is the project's principal health risk. Maintainer breadth is better than commit breadth — seven maintainers across four organisations — but authorship remains concentrated.
- **Review latency, not contribution volume.** Contributions arrive faster than maintainers respond to them. In August 2026, five substantive proposals were found to have received no maintainer response at all, in one case for six weeks, and two pull requests were waiting on reviews that had been requested and never given. The backlog review addressed the specific instances; the underlying capacity problem is unresolved and is the honest answer to why good contributions stall here.
- **No tagged releases.** Versioning is expressed on the site (`v2`, 2025-10-20) but the repository has no GitHub releases, so downstream consumers have no citable, immutable version to pin to. This matters more now that a second FINOS project and an MCP server consume the catalogue.
- **Silent data defects.** A missing newline in generated front matter removed twenty cross-references from the published site and went unnoticed for five weeks, because the YAML remained valid. A contributor fixed it within 48 hours of it being filed, and the deterministic checks that found it now exist — but they are not yet enforced in CI.
- **No operational capacity.** The project has maintainers but no operational function. Anything that needs running rather than reviewing — a hosted MCP endpoint, an assistant on the website — currently has nobody to carry it.
- **AI-assisted contributions are arriving with no stated position.** The repository already receives them. The defect above originated in a generated block that nobody verified.

# Roadmap & Goals for Next 6 Months

- **v4 roadmap: operationalisation.** Move the framework from a catalogue of prose controls toward something a firm can enforce and evidence at runtime. Five contributor proposals now sit under this heading: a runtime policy and evidence reference implementation for the agentic mitigations, signed and independently verifiable decision receipts as the evidence artifact, verifiable operand provenance, scaled adoption tiers for resource-constrained institutions, and a reference operational lifecycle.
- **Hosted AIGF services.** A FINOS-hosted MCP server, an index over the project's own history, and an assistant on the framework site — raised as an infrastructure and budget request modelled on the CALM precedent. Phase one is a beta with no SLA.
- **Adoption material.** Adopter-facing one-pagers, an end-to-end playbook showing how AIGF, CALM and CC4AI compose, and eLearning conversion of the training content. The recurring request from outside the working group is a worked path in, and the catalogue does not yet provide one.
- **Use case expansion**, continuing the pattern of concrete deployments with named risks rather than abstractions.
- **Contributor breadth**, to reduce the concentration above: curated good-first-issues, faster first response, and outreach to member organisations.
- **Supply chain and vendor compliance**, including machine-readable policy for vendor engagement.
- **Tagged releases and CI enforcement** of the catalogue checks.

> **TODO (Asad):** confirm which of these we actually commit to for the next six months versus list as aspiration. The TOC will read this as a plan, and it is better to commit to four things than to list eight.

# TOC Support Needed

- **Infrastructure and budget for hosted AIGF services.** We have raised a request covering a hosted MCP server, an index over the project's history, and a site assistant, following the pattern of the CALM Hub hosting request. Inference cost is usage-based and unlike CALM's fixed hosting profile, so guidance on how FINOS wants to fund and cap that would help. The related question is operational: who runs it.
- **A FINOS position on AI agents maintaining project repositories.** The August backlog review here was performed by an AI agent under maintainer supervision, and every comment it posted carries a disclosure line naming the tool and model. We have proposed a contributing convention — disclose tool and model, remain accountable under the DCO, verify anything checkable before submitting — but this is a question every FINOS project now faces, including the use of GitHub Copilot agents. A foundation-level view would be more useful than fifteen project-level ones.
- **OSPS Baseline guidance.** Concretely, what Maturity Level 2 requires of a documentation-and-data project rather than a software project, and where AIGF currently falls short.
- **Community management support** to broaden the contributor and organisational base.
- **Cross-project collaboration.** Live interfaces with CALM (modelling AI architectures so they can be validated against AIGF controls), the AI Reference Architecture Library, CC4AI, and the SDLC Common Controls Framework, which was seeded from this project. Clarity on where the boundary sits between AIGF and SDLC Controls — skills governance and secure development lifecycle material in particular — would unblock at least one stalled contribution.

# Additional Information

- The catalogue is structured Markdown with YAML front matter, so it is machine-readable by design: every risk and mitigation carries typed references to the external frameworks it maps to, and those relationships are validated mechanically.
- Governance artifacts: working sessions run fortnightly with agendas and minutes kept as GitHub issues; contributions require DCO sign-off and pull request review.
- Related repositories: [aigf-mcp-server](https://github.com/finos/aigf-mcp-server), [ai-reference-architecture-library](https://github.com/finos/ai-reference-architecture-library), [SDLC-Controls-Framework](https://github.com/finos-labs/SDLC-Controls-Framework).

> **TODO (Asad):** three things before this goes up —
> 1. `MAINTAINERS.md` in the AIGF repo has `*please add organization*` placeholders against five of seven maintainers, including you. The TOC looks at maintainer affiliation as a concentration signal; worth filling in first.
> 2. Confirm attendance for 9 September, 12:00 EST / 17:00 BST, and who else from the maintainer group presents.
> 3. The report is meant to land **two weeks before** the session — that was 26 August. Worth a note to the liaison when you open the PR.
