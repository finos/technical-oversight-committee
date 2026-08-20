# Architecture Decision Records

This directory holds the Architecture Decision Records (ADRs) for the FINOS Technical Oversight Committee (TOC).

An ADR captures a governance or technical decision made by the TOC that has lasting effect — the kind of thing someone will otherwise have to reconstruct from scattered issue and meeting history later. See [ADR-0001](./0001-adopt-architecture-decision-records.md) for why the TOC adopted this practice.

## When to write one

Write an ADR when a decision:

- Changes a standard, template, or process the TOC asks FINOS projects to follow (e.g. the `MAINTAINERS.md` format)
- Changes how the TOC itself operates and isn't already covered by [governance.md](../operations/governance.md)
- Was debated with real tradeoffs, where the reasoning is as valuable as the outcome

Routine operational decisions (scheduling, meeting logistics, individual project votes already covered by [voting.md](../operations/processes/voting/voting.md)) don't need one.

## Process

1. Raise a GitHub issue proposing the decision. Discussion and voting happen there (or in TOC meetings), per [Decision-Making and Voting](../operations/governance.md#decision-making-and-voting) in the TOC governance document — this doesn't change.
2. Once a decision is reached, open a PR adding the ADR file to this directory, `Status` set to the outcome (`Accepted` or `Rejected`), linking back to the issue.
3. The PR is for recording the decision, not re-litigating it — substantive discussion belongs on the issue.
4. ADRs are not deleted once merged, even if superseded — the record of what was decided and why should stay intact. A superseding ADR should link back to the one it replaces.

## Numbering and format

Files are named `NNNN-short-kebab-case-title.md`, numbered sequentially starting at `0001`. Use the next unused number when proposing a new ADR.

Each ADR should follow this structure:

```markdown
# ADR-NNNN: Title

**Status:** Proposed | Accepted | Rejected | Superseded by ADR-NNNN
**Date:** YYYY-MM-DD
**Deciders:** who was involved
**Related:** links to relevant issues/PRs

## Context

What prompted this decision, and what constraints or prior discussion shaped it.

## Decision Drivers

The factors that matter most in choosing between options.

## Considered Options

Each option considered, with pros and cons.

## Decision Outcome

The option chosen, and why.

## Consequences

What this makes easier, what it makes harder, and any follow-up it creates.
```

## Index

| ADR | Title | Status |
| --- | --- | --- |
| [0001](./0001-adopt-architecture-decision-records.md) | Adopt Architecture Decision Records | Accepted |
| [0002](./0002-maintainers-md-email-field-optional.md) | Make the `MAINTAINERS.md` email field optional | Accepted |
