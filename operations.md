# FINOS Technical Oversight Committee (TOC) Operating Procedures

## Approach

The TOC is the technical arm of the FINOS Governing Board, committed to fostering the growth of FINOS projects. We operate transparently through open discussion, maintaining alignment with FINOS's technical and strategic goals while ensuring the long-term sustainability of projects.

## Roles & Responsibilities

### TOC Member Responsibilities

TOC members are responsible for actively participating in meetings, discussions, and decision-making processes. Members determine the FINOS technical standards, enable cross-project collaboration, provide technical guidance, and help resolve disputes when needed.

TOC members are also expected to equally share the responsibility of serving as liaisons to projects. Assignments will be divided among TOC members based on interest, to ensure that each project has a dedicated liaison.

- Participate in TOC meetings and contribute to discussions.
- Evaluate project applications and proposals.
- Act as a [project liason](./liason-guide.md).
- Assess and promote cross-project synergies.
- Provide technical oversight and support for project lifecycles.
- Collaborate with the Governing Board to align strategic goals.
- Mentor newly elected TOC members.

> [!NOTE]
> TOC Members are appointed to two-year terms through the [elections](./elections.md) process.**

### TOC Vice Chair Responsibilities

The TOC Vice Chair supports the Chair in overseeing the smooth functioning of the committee by handling logistical tasks such as scheduling meetings, maintaining attendance, and ensuring documentation is up to date.

The Vice Chair may act as a delegate for the Chair when necessary.

- Provide logistical support for meetings and repository maintenance.
- Assist in maintaining attendance and ensuring voting eligibility.
- Help coordinate TOC activities and documentation.
- Ensure a monthly stakeholder newsletter is sent by FINOS on behalf of the TOC.
- Act as a delegate for the Chair when required.
- Propose and onboard a Vice Chair replacement before transitioning out.

> [!NOTE]
> Vice Chairs are appointed by the TOC to one-year terms beginning with the vacancy of the role. Onboarding a new vice chair should be prioritized by the outgoing Vice Chair.

### TOC Chair Responsibilities

The TOC Chair is responsible for ensuring the smooth operation and productivity of the Technical Oversight Committee. This includes leading meetings, driving the agenda, overseeing decision-making processes, and ensuring that all TOC responsibilities are completed on time.

The Chair also serves as the primary liaison between the TOC and the Governing Board, including the presentation of a quarterly report summarizing updates from project liasons.

- Ensure all TOC responsibilities are met, facilitating meetings and project reviews.
- Ensure that all outcomes are documented in the TOC repository.
- Ensure that all projects have an active TOC liason.
- Ensure that 5 project demos are presented at each OSFF event.
- Serve as the primary liaison between the TOC and the Governing Board.
- Propose and onboard a Chair replacement before transitioning out.

> [!NOTE]
> Chairs are appointed by the TOC to one-year terms beginning with the vacancy of the role. Onboarding a new Chair should be prioritized by the outgoing Chair.

## Proposals & Voting

The TOC may need to vote on a variety of proposals, including the approval of new project applications, decisions to promote projects through different lifecycle stages, amendments to technical standards or best practices, and resolutions of cross-project technical disputes.

All proposals should be captured in the form of a GitHub issue, which may be accompanied by a pull request or presentation.

- A majority vote is required to pass any proposal.
- Proposals must be raised as GitHub issues.
- Discussions should held openly on the issue or in TOC meetings.
- To vote, members must have attended two of the last three TOC meetings.

## Communication & Documentation

### GitHub Issues

- All discussions should happen in GitHub issues, including proposals, meeting agendas, and suggestions.
- Members should use GitHub issues to raise concerns, suggest changes, or propose new projects.

### GitHub Repository

- Decisions and outcomes must be documented in the TOC GitHub repository.
- Charters, reports, and other key documentation should be maintained and updated regularly.

## Processes

TOC activities are managed in GitHub via the [Project Backlog](https://github.com/orgs/finos/projects/39), which is maintained in collaboration between the FINOS team and the TOC chair.

The processes needed to support the above responsibilities are still under development. The following section describes those where a process has been defined and is active.

### Project Contributions

 - Project contributions are submitted via the [FINOS community project](https://github.com/finos/community) as issues. The FINOS team perform initial validation, indicating that they are ready for TOC input via the `ready-for-TOC` label
 - A TOC member is assigned to evaluate the contribution using our [contribution principles](https://github.com/finos/technical-steering-committee/blob/master/contribution-principles.md)
 - If the evaluation is straightforward, the TOC member will indicate the outcome, providing a simple narrative, directly on the issue itself
 - For contributions where further debate is needed (on the TOC members discretion), the matter will be raised with the wider TOC

### Project Activations

 - Project activations are submitted via the [FINOS community project](https://github.com/finos/community) as issues. The FINOS team perform initial validation, indicating that they are ready for TOC input via the `ready-for-TOC` label
 - A TOC member is assigned to evaluate the activation
 - The TOC member provides input on the following topics
   - Usefulness - is it clear what business problem this project is addressing? What are the use cases that it helps solve? What are its main benefits?
   - Community - how is the project being used and consumed? There may be different ways for firms/individuals to consume and contribute to a project, more or less relevant to assess its maturity.
   - Progress - is the project following the publicly shared roadmap?
 - If the evaluation is straightforward, the TOC member will indicate the outcome, providing a simple narrative, directly on the issue itself
 - For activations where further debate is needed (on the TOC members discretion), the matter will be raised with the wider TOC

### Board reporting

 - It is the responsibility of the Chair to provide regular and timely reports for the Governing Board

### Reporting on FINOS Initiatives

> [!NOTE]  
> Depending on the type of initiative (Software Project, Standard, Special Interest Group) and maturity (Incubating or Active), metrics and criteria may vary; we will start focusing on Software Projects; the initial focus on reporting will be around **Incubating Software Projects**.

In order to measure project health, the following metrics should be collected:
- **Number of code changes** (commits) and proposals (Pull Requests) in the last quarter made by humans (no bots); if the sum of changes and proposals is lower than 5 (to be confirmed), then the project can be considered `inactive`.
- **Average response time to inquiries** (issues, Pull Requests, emails, ...); if the average response time (in the last quarter) is higher than 5 days (to be confirmed), then the project can be considered `unresponsive`.
- **CII Best Practices badge**; if the project didn't apply for a badge yet, or the score is lower than 70%, then the project can be considered `not aligned with best practices`.
- **OpenSSF Scorecard** result; it's still unclear if/how to interpret the result, but the outcome will be similar to the `CII Best Practices badge` ; would also help to link to the visualizer, e.g. https://securityscorecards.dev/viewer/?uri=github.com/finos/fdc3-dotnet
- **Documentation**; if the project doesn't have a documentation website and the README.md length is lower than 400 words, then the project can be considered `not properly documented`.
- **SBOM report**; if the project has an SBOM available in SPDX or CycloneDX format, which demonstrates that no CVEs and license violations are found, then the project can be considered `fully compliant`.

#### Qualitative checks (optional)
- Response time on mailing list inquiries
- Documentation quality
- Release process in place
- Roadmap and milestones in place

## Operational Changes

- Functional modifications to this operations document require a two-thirds majority vote of all TOC members prior to PR approval.

