# TOC Project Health-Check Reports

These reviews are required for **every FINOS project** to ensure transparency, health, alignment with the FINOS mission, and governance.

Project reviews are used to:
* Determine the health and trajectory of a project.
* Identify where the TOC can support the project.
* Share interesting milestones with member companies and the wider community.

# Submitting Project Updates

Project reports are to be submitted as a pull request to the `toc/project-reports` under current year folder. 

The health check is centred on a written **report submitted as a pull request** — not a mandatory in-person presentation. Maintainers present to the TOC only when the TOC has questions or concerns that cannot be resolved on the report PR.

1. **Scheduling:** Check the [Schedule](./SCHEDULE.md) to see upcoming due dates. Each project is assigned a TOC liaison for coordination, and the TOC notifies project maintainers of their due date using the [Email Template](./toc-review-email-template.md).

2. **Preparation:** The project maintainers create a report using the [report template](./YYYY-HX-[PROJECT-NAME].md). Maintainers may, at their discretion, use the [AI-assisted drafting prompt](./AI-REPORT-PROMPT.md) to produce a first draft — but remain responsible for verifying every figure and amending anything inaccurate before submitting.

3. **Submission:** Maintainers submit the report as a PR to the current year's folder at least **two weeks** before the relevant TOC meeting. This report PR is the primary deliverable for the health check.

4. **Review:** TOC members review and comment on the PR, and the liaison works with the project to address questions in the PR thread. As part of the review, the TOC assesses the project's [LFX Insights](https://insights.lfx.linuxfoundation.org/foundation/finos) data to evaluate compliance with its maintenance requirements, including the applicable OSPS Baseline maturity level (Maturity Level 2 for Incubating, Maturity Level 3 for Graduated).

5. **Presentation (only if needed):** If, after reviewing the report, the TOC has open questions or concerns, the project maintainers will be scheduled to present at a future TOC meeting to answer them. A clear, complete written report may remove the need to present at all. The report PR is merged once the TOC is satisfied — after the presentation, if one was required.

6. **Follow-up:** TOC will discuss any lifecycle transitions or support needs and create a follow-up GitHub issue if needed.

## Instructions for submission

1. **Copy the Template:** Start by copying the [report template](./YYYY-HX-[PROJECT-NAME].md).

2. **Name the File:**
   Save the new file in the current year's folder using the following convention:
   `project-reports/[Year]/[Year]-H[X]-[ProjectName].md` 
   * *Example:* `project-reports/2025/2025-H2-FDC3.md`

3. **Fill & PR:**
   * Fill in the project details
   * Remove the instructional text.
   * Open a PR against the `finos/technical-oversight-committee` repository.

## Project Scope
This review process applies to projects in the following lifecycle stages, or projects that are transitioning into or out of these stages:

- **Incubating**
- **Graduated**

> [!NOTE]
> Projects in **Labs** are not required to participate in the semi-annual review, and health status is evaluated by FINOS staff at their sole discretion.

## Non-participation and unreachable projects

A project that does not complete its semi-annual review — by not submitting a report, by not attending a presentation the TOC has scheduled, or by having no maintainer of record or none reachable — is recorded as out of compliance with the [maintenance requirement](../operations/processes/projects/incubation.md) for that cycle. Per the lifecycle requirements, three consecutive out-of-compliance reviews qualify a project for archival.

For a project with no maintainer of record or none reachable, FINOS staff post a notice on the project's issue board requesting confirmation that the project is maintained, with a response deadline (one month, with a reminder one week prior). If no maintainer responds by the deadline, the cycle is recorded as out of compliance and the project is not scheduled to present.

> [!WARNING]
> Any failed health check may disqualify a project from FINOS Marketing benefits, such as the public listing on the FINOS Landscape or qualification for participation at FINOS events. These elements are exclusively managed at the discretion of FINOS Staff.

