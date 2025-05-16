# FINOS Technical Oversight Committee (TOC) Governance Document

## Mission

The TOC is the technical arm of the FINOS Governing Board, committed to fostering the growth of FINOS projects. It operates transparently through open discussion, maintaining alignment with FINOS's technical and strategic goals while ensuring the long-term sustainability of projects.

---

## Roles

The TOC consists of three roles: Members, Vice Chair, and Chair. Each role has specific responsibilities and expectations to ensure the effective functioning of the committee. Responsibilities of each role are outlined in the [Responsibilities](#responsibilities) section.

### Member

TOC members are responsible for actively participating in meetings, discussions, and decision-making processes. Members determine FINOS technical standards, enable cross-project collaboration, provide technical guidance, and help resolve disputes when needed.

Members are also expected to equally share the responsibility of serving as liaisons to projects and technical initiatives approved by the governing board. Assignments will be divided among TOC members based on interest, to ensure each technical effort has a dedicated liaison.

### Vice Chair

The TOC Vice Chair supports the Chair in overseeing the smooth functioning of the committee by handling logistical tasks such as scheduling meetings, maintaining attendance, and ensuring documentation is up to date.

The Vice Chair may act as a delegate for the Chair when necessary.

Vice Chairs are appointed by the TOC to one-year terms beginning with the vacancy of the role. Onboarding a new Vice Chair should be prioritized by the outgoing Vice Chair.

### Chair

The TOC Chair is responsible for ensuring the smooth operation and productivity of the Technical Oversight Committee. This includes leading meetings, driving the agenda, overseeing decision-making processes, and ensuring all TOC responsibilities are completed on time.

The Chair also serves as the primary liaison between the TOC and the Governing Board, including presenting a quarterly report summarizing updates from project liaisons.

Chairs are appointed by the TOC to one-year terms beginning with the vacancy of the role. Onboarding a new Chair should be prioritized by the outgoing Chair.

### Terms and Selection Process

- Members: Appointed to two-year terms through the [elections process](/operations/elections/elections.md). 
- Chair and Vice Chair: Starting with vacancy of the role, these positions are appointed by the TOC to one-year terms or until their membership on the TOC ends — whichever is first. Voting must be done asynchronously to ensure that all members are notified.

---

## Responsibilities

### Responsibilities of the Group

The key responsibilities of the TOC are tabulated below:

| **TOC Responsibilities** | **Outcome** | **Frequency** | **Resources / Process** |
| - | - | - | - | 
| **Landscape Ownership** |
| Solicit and recommend cross-project synergies                              | Review project landscape and recommend                                                                                | Quarterly    | Invite relevant [Project Maintainers](https://groups.google.com/a/finos.org/g/finos-project-maintainers) to join TOC meetings.
| Evolve technical governance, security standards, and best practices  |                                                                                                                       | Twice a year | Propose changes via PR to [FINOS Community Website](https://community.finos.org/)
| Provide impartial and knowledge-based input into technical disputes        | Provide technical recommendations and next steps for dispute resolution and community messaging/engagement            | As needed    | Use [TOC Private List](https://lists.finos.org/g/toc-private) for confidential conversations not suitable to general public.
| Review of project health                                                   | Review project activity and recommend actions as necessary                                                            | Quarterly    | Monitor [FINOS LFX Insight Dashboard](https://insights.lfx.linuxfoundation.org/foundation/finos)
| Evolve the overall landscape                                               | Examine the FINOS project landscape and highlight gaps or potential for additions or removals                         | Twice a year | Propose changes to the [FINOS Landscape](https://landscape.finos.org/)
| Recommend evolution of lifecycle criteria                            | Review existing criteria and recommend potential changes or assert continuation as is.                                | Annually     | Propose PRs to [Project Lifecycle](https://community.finos.org/docs/governance/software-projects/project-lifecycle/)
| Recommend and approve lifecycle transitions                            | Evaluate and respond to submitted proposals on monthly basis                                                          | As needed    | [Project Activations](#project-activations) |
| **Landscape growth** |
| Review and approve contributions                                           | Review new contribution proposals and provide timely recommendations and feedback                                     | As needed    | [Project Contributions](#project-contributions) |
| Assist FINOS in promote new contributions                                  | Engage with community to communicate value of projects and document potential use cases                               | As needed    | Subscribe and engage with [FINOS Community List](http://groups.google.com/a/community) and in [FINOS Community Repo](https://github.com/finos/community)
| Assist FINOS in nurturing new project contributions                        | Identify opportunities to associate existing open source projects with the FSI community; recommend new projects      | As needed    | Propose ideas to [FINOS Leadership](leadership@finos.org)
| **FINOS Governing Board & Strategic interaction** |
| Provide a TOC liaison for each FINOS strategic initiative    | Engage with Executive Sponsors to identify use cases and promote implementation of strategically-significant projects | Quarterly    | TOC Chair source liaison and report to Governing Board
| Report to the board                                                        | Engage in annual strategy planning; provide a quarterly report of TOC activities and decisions                        | Quarterly    | [Board Reporting](#board-reporting) |
| OSFF active participation                               | Participate in program committee, and recruit / recommend approve project-related presentations, project demos, and project booths                        | Twice a year    | Interact via [OSFF alias](ossf@finos.org) |

> [!NOTE]
> The Chair is accountable for ensuring that the above responsibilities are fulfilled by the group, with equitable involvement from all members.

### Member Responsibilities

- Participate in TOC meetings and contribute to discussions, at least 50% of the time
  - Delegates may be sent to meetings, but the member is still responsible for giving feedback or acting on outcomes from the meetings
- Participate in all project applications and promotion requests through discussion and/or voting
  - This may be asynchronous via GitHub issues or in TOC meetings
- Act as a liaison for a project or initiative as agreed with the larger TOC body
  - The definition and expectations of a project liaison are outlined in the [Liaison Guide](./liaison-program/liaison-guide.md)

### Vice Chair Responsibilities

- Provide logistical support for meetings and repository maintenance
- Assist in maintaining attendance and ensuring voting eligibility
- Help coordinate TOC activities and documentation
- Ensure a monthly stakeholder newsletter is sent by FINOS on behalf of the TOC
- Act as a delegate for the Chair when required
- Propose and onboard a Vice Chair replacement before transitioning out

### Chair Responsibilities

- Ensure all collective TOC responsibilities are met
- Support TOC members in understanding and executing upon their responsibilities
- Facilitate meetings
- Lead the engagement on project applications and promotion requests
- Ensure all outcomes are documented in the TOC repository
- Ensure all projects have an active TOC liaison
- Ensure 5 project demos are presented at each OSFF event
- Serve as the primary liaison between the TOC and the Governing Board
- Propose and onboard a Chair replacement before transitioning out

---
## Processes

TOC activities are managed in GitHub via the [TOC Backlog](https://github.com/orgs/finos/projects/39), which is fed by the Community, the FINOS team and owned by the TOC chair. Below a list of transparently documented processes the TOC follows:

## Decision-Making and Voting

- Proposals must be submitted as GitHub issues
- Discussions occur openly on the issue or in TOC meetings
- Operational changes to this governance document require a two-thirds majority vote of all TOC members prior to PR approval
- Any member can propose a resolution which will be binding immediately upon completion
- Votes must last five business days, unless a live vote is done with a supermajority quorum
  - A supermajority quorum entails two-thirds of qualified membership present
- To qualify as a voting member, members must have attended two of the last three TOC meetings
- A majority vote is required to pass proposals
- The Chair must withhold all vote participation except to act as a tie-breaker


### Project Contributions

 - Project contributions are submitted via the [FINOS community project](https://github.com/finos/community) as issues, according to the [FINOS contribution process](https://community.finos.org/docs/governance/software-projects/contribution/).
 - The FINOS team perform initial validation, including completeness of the [Incubation checklist](https://community.finos.org/docs/governance/software-projects/stages/incubating/#incubating-lifecycle-checklist) requirements, and encourage initial socialization with the FINOS community
 - FINOS team indicates contributions are ready for TOC via the `ready-for-toc` label, adding them to the [TOC Backlog](https://github.com/orgs/finos/projects/39) and assigning tho the current TOC chair
 - TOC evaluates contribution using the [TOC contribution principles](https://github.com/finos/technical-steering-committee/blob/master/contribution-principles.md) and the [Incubation checklist](https://community.finos.org/docs/governance/software-projects/stages/incubating/#incubating-lifecycle-checklist)
 - TOC assigns a TOC member and / or ask for contributors to present a TOC and answer questions / provide additional evidence.
 - TOC will indicate the outcome (approve / rejected), providing an explanation narrative, directly on the issue itself
 - FINOS team proceed with further onboarding steps, including evaluating and addressing [Contribution Compliance Requirements](https://community.finos.org/docs/governance/Software-Projects/contribution-compliance-requirements).

### Project Activations

 - Project activations are submitted via the [FINOS community project](https://github.com/finos/community) as issues, according to the [FINOS Activation Process](https://community.finos.org/docs/governance/software-projects/stages/active/#initiating-activation)
 - The FINOS team perform initial validation, including completeness of the [Activation checklist](https://community.finos.org/docs/governance/software-projects/stages/active/#activation-checklist) requirements
 - FINOS team indicates contributions are ready for TOC input via the `ready-for-toc` label, adding them to the [TOC Backlog](https://github.com/orgs/finos/projects/39) and assigning tho the current TOC chair
- TOC evaluates activation using the [Activation checklist](https://community.finos.org/docs/governance/software-projects/stages/active/#activation-checklist)
-  TOC assigns a TOC member to evaluate the activation and / or ask for contributors to present a TOC and answer questions / provide additional evidence.
 - A TOC member is assigned to evaluate the activation
 - The TOC member will provides particular scrutiny and exercise discretion on, but not limited to, these items:
   - Usefulness - is it clear what business problem this project is addressing? What are the use cases that it helps solve? What are its main benefits?
   - Community - how is the project being used and consumed? There may be different ways for firms/individuals to consume and contribute to a project, more or less relevant to assess its maturity.
   - Progress - is the project following the publicly shared roadmap?
- TOC will indicate the outcome (approve / rejected), providing an explanation narrative, directly on the issue itself and assigns a FINOS team members for further processing
 - FINOS team proceed accordingly with further steps, including applying the [active badge](https://community.finos.org/docs/governance/software-projects/stages/active/#badge) in case of successful activation  

### Board reporting

 - It is the responsibility of the Chair to provide regular and timely reports for the Governing Board before each Governing Board meeting. Ideally this should contain:
   - Report on overall project landscape health
   - Stats on activity of TOC itself
   - High level overview of initiatives TOC is undertaking
   - Any other criticality or recommendation for the Governing Board

---

## Communication & Documentation

- Discussions related to community-impacting work should happen in GitHub issues, including proposals, meeting agendas, and suggestions
- Decisions, outcomes, and policies must be documented in the TOC GitHub repository
- Charters, reports, and other key documentation should be maintained and updated on the TOC GitHub repository regularly
- In the event that a requirement from this document is not explicitly captured herein, clarifying documentation may be captured in the TOC repository, where it should be considered equally authoritative unless conflicting with this document.

---

## Amendment Process

Functional modifications to this governance document require an asynchronous supermajority vote prior to merge (two-thirds of qualified votes).
