# TOC Responsibilities

This page describes the TOC responsibilities, and the processes that support each. At a very high-level, the TOC supports both the [FINOS team](https://www.finos.org/team) and the [Governing Board](https://www.finos.org/governing-board) to provide technical oversight for the projects in the FINOS portfolio.

The key responsibilities of the TOC are tabulated below:

## Reactive, Supported by TOC
- **Supports designing and collecting use cases for hackathons and tech sprints** 
- **Support the creation (and recruitment) of a mentorship program** 
- **Project Contributions** - assessing whether contributions are a good fit for FINOS.
- **Project Activations** - determining when projects are ready to be 'promoted'.

## Proactive
- **Lead recruitment of FINOS Ambassadors** - engage with Grizz, understand how the Ambassador program works, find potential candidates and facilitate the connection with the FINOS team
- **Recruit 5 project demos for OSFFs** - Eteri is the point of contact from the FINOS team
- **Participates in OSFF promotional activities**
- **TOC sponsor is actively engaged in the success of the strategic initiative** - All FINOS Strategic initiatives have a TOC sponsor assigned; this person is expected to join meetings, provide technical steering and report back to the TOC; these reports will be delivered to the FINOS Board on a quarterly cadence
- **Engage with all projects incubating for over 1 year to nurture activation or archiviation**
- **Produce a quarterly report on overall FINOS project landscape / health**

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

### Project reporting

In order to measure project health, the following metrics should be collected:
- Number of code changes (commits) and proposals (Pull Requests) in the last quarter made by humans (no bots); if the sum of changes and proposals is lower than 5 (to be confirmed), then the project can be considered `inactive`.
- Average response time from the project team to issues, pull requests; if the average response time (in the last quarter) is higher than 5 days (to be confirmed), then the project can be considered `unresponsive`.
- CII Best Practices badge; if the project didn't apply for a badge yet, or the score is lower than 70%, then the project can be considered `not aligned with best practices`.
- Documentation; if the project doesn't have a documentation website and the README.md length is lower than 400 words, then the project can be considered `not properly documented`.
- SBOM report publicly; if the project has an SBOM available in SPDX format, which demonstrates that no CVEs and license violations are found, then the project can be considered `fully compliant`.

#### Qualitative checks (optional)
- Response time on mailing list inquiries
- Documentation quality
- Release process in place
- Roadmap and milestones in place
