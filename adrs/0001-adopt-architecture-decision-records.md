# ADR-0001: Adopt Architecture Decision Records

**Status:** Accepted
**Date:** 2026-07-30
**Deciders:** TOC members (via [#308](https://github.com/finos/technical-oversight-committee/issues/308))
**Related:** [#308](https://github.com/finos/technical-oversight-committee/issues/308), [#306](https://github.com/finos/technical-oversight-committee/pull/306)

## Context

[#306](https://github.com/finos/technical-oversight-committee/pull/306) surfaced a real disagreement about how `MAINTAINERS.md` should handle contact information. Rather than let that discussion play out only as unstructured PR comments, it was raised as [#308](https://github.com/finos/technical-oversight-committee/issues/308), an issue laid out in an ADR-like structure — context, decision drivers, considered options, a recommendation — to make the tradeoffs explicit and give TOC members a clear basis to weigh in.

That format worked: it produced a focused discussion and a decision the TOC could point back to. In the same issue, it was proposed that the TOC formally adopt ADRs going forward, with this ADR being the first one — a decision to keep making decisions this way.

The TOC already documents outcomes as part of its [Communication & Documentation](../operations/governance.md#communication--documentation) practice, and proposals are already expected to run through GitHub issues per [Decision-Making and Voting](../operations/governance.md#decision-making-and-voting). What was missing was a durable, consistently-structured record of *why* a given decision was made — issue threads are searchable but the reasoning is diffused across comments, and there was no single place to look for "what did the TOC decide about X, and why."

## Decision Drivers

- **Discoverability**: someone asking "why does the TOC do X this way" should be able to find an answer without reconstructing it from issue comment history.
- **Consistency**: a fixed structure (context, options, decision, consequences) makes proposals easier to evaluate and easier to write, compared to free-form issues.
- **Fits existing process**: this should extend the TOC's existing issue-based proposal and voting process, not replace it.

## Considered Options

### Option A — Continue using ad hoc GitHub issues
Keep raising governance proposals as regular issues, without a required structure or a persistent record beyond the issue itself.

- Pros: No new process to maintain; how the TOC already operates.
- Cons: Reasoning behind past decisions is hard to find later; nothing stops each proposal from being structured differently, which makes them harder to compare or evaluate.

### Option B — Adopt Architecture Decision Records (Chosen)
Formalize the ADR-style structure used in #308 as the standard way to propose and record TOC decisions with lasting effect, stored as versioned markdown files in this repository.

- Pros: Produces a durable, greppable record of decisions and their rationale, sitting alongside the code/docs it affects. Reuses a well-established open-source pattern rather than inventing something bespoke. Composes with the existing issue/PR-based voting process in [governance.md](../operations/governance.md#decision-making-and-voting) rather than replacing it.
- Cons: Adds a small amount of process (a template to follow, a file to keep in sync with the outcome) on top of the existing issue-based flow.

## Decision Outcome

**Option B.** ADRs are adopted as the standard format for documenting TOC decisions of lasting governance or technical significance, stored under [`/adrs`](./README.md) in this repository. See [`adrs/README.md`](./README.md) for the process and template.

## Consequences

- Future governance proposals with real tradeoffs still start as a GitHub issue, per the existing [Decision-Making and Voting](../operations/governance.md#decision-making-and-voting) process — but once decided (like the `MAINTAINERS.md` question in #308), the outcome gets written up as an ADR rather than left to live only in an issue thread.
- The TOC now has one place (`/adrs`) to point to when asked why a given standard or process exists.
- Existing decisions are not retroactively converted — ADRs apply going forward, though a past decision worth preserving can be written up after the fact, as with the `MAINTAINERS.md` email decision reached in [#308](https://github.com/finos/technical-oversight-committee/issues/308).
