# ADR-0002: Make the `MAINTAINERS.md` email field optional

**Status:** Accepted
**Date:** 2026-08-13
**Deciders:** TOC members (via [#308](https://github.com/finos/technical-oversight-committee/issues/308))
**Related:** [#308](https://github.com/finos/technical-oversight-committee/issues/308), [#306](https://github.com/finos/technical-oversight-committee/pull/306), [FINOS software-project-blueprint MAINTAINERS.md](https://github.com/finos/software-project-blueprint/blob/main/MAINTAINERS.md)

## Context

[#306](https://github.com/finos/technical-oversight-committee/pull/306) added a personal email address to one maintainer's row in this repo's `MAINTAINERS.md`, following the FINOS-standard `MAINTAINERS.md` template's `Email` column. Review discussion objected to publishing personal emails on privacy/spam grounds, which was written up as [#308](https://github.com/finos/technical-oversight-committee/issues/308) with four considered options, recommending Option D — replacing individual emails with a per-project maintainers mailing list.

Discussion on #308 moved past that recommendation:

- @maria-mcparland was open to Option D but asked about setup overhead, looping in @TheJuanAndOnly99.
- @TheJuanAndOnly99 raised that Option D carries real operational cost: most FINOS projects don't have a maintainer-specific mailing list today, provisioning one per project is nontrivial, and a public group address needs ongoing moderation to stay useful for spam prevention. They proposed instead making the `Email` column explicitly optional (e.g. `Email (Optional)`), combined with the option of using a GitHub noreply address (Option B) for anyone who wants to be reachable without exposing a personal inbox.
- @rocketstack-matt questioned whether `MAINTAINERS.md` earns its place at all if organization/email are optional and unenforceable, given it duplicates information already in GitHub Teams and risks going stale.
- @TheJuanAndOnly99 clarified the file's value over GitHub Teams: GitHub Teams aren't publicly visible outside the FINOS GitHub org, `MAINTAINERS.md` is required to change before FINOS staff will update GitHub permissions (so it doesn't go stale), all changes go through PRs (a public audit trail), and the file feeds FINOS's LFX Insights.
- @maria-mcparland confirmed (after checking with @mindthegab) that optional emails work for her.
- @eddie-knight summarized the resulting consensus: making the email field optional "accomplishes the best of both worlds: emails can be added by people who want to be contacted (e.g. vendors) and omitted by anyone concerned about spam."
- @TheJuanAndOnly99 then implemented this FINOS-wide: emailed the `finos-project-maintainers` Google group, updated the [FINOS software-project-blueprint `MAINTAINERS.md`](https://github.com/finos/software-project-blueprint/blob/main/MAINTAINERS.md) template to mark the `Email` field as `Optional`, and updated already-open PRs to match.

**Process note:** this decision was reached and implemented FINOS-wide through async discussion in #308's comments, ahead of [ADR-0001](./0001-adopt-architecture-decision-records.md) formally establishing the ADR process this repo now uses for exactly this kind of decision. This ADR documents that decision after the fact so it has a durable record here, consistent with [ADR-0001](./0001-adopt-architecture-decision-records.md)'s consequence that past decisions worth preserving can be written up retroactively.

## Decision Drivers

- **Consistency**: the TOC shouldn't ask projects to publish something the TOC itself won't publish in its own repo.
- **Privacy / spam exposure**: personal emails posted in a public, indexed GitHub file are a durable target for scraping and spam.
- **Reachability**: preserve a way to contact maintainers who are willing to be contacted directly (e.g. by vendors), without forcing it on everyone.
- **Operational overhead**: any option needs to be something FINOS staff and project maintainers can realistically stand up and keep running, across all FINOS projects, not just this repo.

## Considered Options

### Option A — Require a personal email
Rejected in #308: not enforceable, and doesn't address the privacy/spam objection.

### Option B — Use a GitHub-generated noreply email
Rejected as a standalone answer in #308: not enforceable, and noreply addresses generally can't reliably receive external mail. Remains available to anyone who wants a lower-exposure address, now that the field is optional.

### Option C — Drop the email field or the file entirely
Rejected: removes reachability with nothing to replace it, and puts projects out of step with the FINOS-wide `MAINTAINERS.md` standard.

### Option D — Per-project maintainers mailing list
Initially recommended in #308, but reconsidered once the operational cost was raised: most FINOS projects lack a maintainer-specific mailing list today, and a public group address needs active moderation to be useful for the spam concern it's meant to solve. Not adopted.

### Option E — Make the `Email` field optional (Chosen)
Keep the `Email` column, but explicitly mark it optional rather than required. Maintainers who want to be directly reachable (personal address or GitHub noreply) can add one; maintainers who don't want to publish contact info leave it blank.

- Pros: No new infrastructure to provision or moderate. Respects individual choice on privacy versus reachability. Already implemented FINOS-wide via the software-project-blueprint template, so this repo's practice now matches the broader standard rather than diverging from it.
- Cons: Doesn't fully resolve the original inconsistency this ADR series set out to fix — some maintainers will list an email and most won't, so "optional and mostly blank" simply becomes the sanctioned state rather than an accidental one. Doesn't create a single project-level contact channel for someone who wants to reach "the maintainers" collectively, if every individual has opted out (for this repo specifically, `toc@lists.finos.org` and `toc-private@lists.finos.org`, per [Readme.md](../Readme.md), already serve that purpose).

## Decision Outcome

**Option E.** The `Email` column in `MAINTAINERS.md` is optional, FINOS-wide, per the updated [software-project-blueprint template](https://github.com/finos/software-project-blueprint/blob/main/MAINTAINERS.md). This repo's `MAINTAINERS.md` should be brought in line with an explicit `Email (Optional)` header for consistency with that template — tracked as follow-up, not yet done as of this ADR.

## Consequences

- Maintainers in this repo (and FINOS projects generally) are not required to publish a personal or noreply email in `MAINTAINERS.md`; existing entries with an email (e.g. @rocketstack-matt's, from #306) remain valid and don't need to change.
- This repo's `MAINTAINERS.md` header should be updated to read `Email (Optional)` to match the FINOS-wide template — a small follow-up PR, not covered by this ADR.
- The underlying "someone wants to reach the maintainers collectively" need for this repo is already covered by the TOC's public and private mailing lists (see [Readme.md](../Readme.md)); this wasn't re-litigated as part of this decision.
- Supersedes the Option D recommendation in [#308](https://github.com/finos/technical-oversight-committee/issues/308).
