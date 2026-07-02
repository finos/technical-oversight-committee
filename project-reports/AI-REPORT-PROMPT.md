# FINOS Project Health-Check Report — AI-Assisted Drafting Prompt

This prompt helps FINOS project maintainers produce their semi-annual TOC health-check
report efficiently, with AI assistance. Paste the prompt below into an AI assistant,
filling in the values in the **Inputs** block first. It works best with an agentic
assistant that has web access and the `gh` GitHub CLI (e.g. Claude Code), but a plain
chat assistant can also use it via the FALLBACK path included in the prompt.

> **Important — this is a drafting aid, not a substitute for maintainer judgement.**
> The assistant produces a *draft* from public GitHub and LFX Insights data. The
> maintainers are expected to **review every section, verify the figures, and amend
> anything that is inaccurate, incomplete, or misframed before raising the PR.** You
> own the final report; the AI only assembles a first pass.
>
> **What happens next:** once the report PR is raised, the TOC reviews it. **If the TOC
> has questions or concerns based on the report, the maintainers will be called to
> present at a TOC meeting.** Reports that are clear and complete may not require a
> presentation — so it is in your interest to make the written report accurate and
> self-explanatory.

---

## Prompt (copy everything below into your AI assistant)

```
You are helping me, a maintainer of a FINOS project, draft our semi-annual TOC
health-check report. Produce a complete, accurate first draft that I will then review
and amend before I raise the PR myself. Do not invent figures — every metric must come
from a real source you queried, and you must tell me the source and the exact window
for each number. Where you have to infer or estimate, say so explicitly.

INPUTS (I have filled these in):
- Project name:            [e.g. CALM (Common Architecture Language Model)]
- GitHub repository:       [e.g. finos/architecture-as-code]
- LFX Insights URL:        [e.g. https://insights.linuxfoundation.org/project/<slug>]
- Reporting period:        [e.g. 2026 H1 — H1 = Jan–Jun, H2 = Jul–Dec]
- Metrics window:          [e.g. trailing 365 days, 2025-06-17 → 2026-06-17]

STEPS:
1. Fetch the FINOS TOC report TEMPLATE and the process README so you match the required
   format exactly:
   - Template: https://github.com/finos/technical-oversight-committee/blob/main/project-reports/YYYY-HX-%5BPROJECT-NAME%5D.md
   - README:   https://github.com/finos/technical-oversight-committee/blob/main/project-reports/README.md
   Use `gh api` to read the raw file contents rather than relying on a rendered summary.
   Note the filename convention: project-reports/<Year>/<Year>-H<X>-<ProjectName>.md.

2. Gather GitHub metrics for the repository over the metrics window using `gh`:
   - PRs opened / merged / currently open
   - Issues opened / closed / currently open
   - Commits in the window and distinct contributors (merge duplicate identities, e.g.
     a person's display name vs their GitHub handle; exclude bots like renovate,
     dependabot, github-actions when reporting *human* contribution)
   - First-time contributors who joined during the window
   - Releases published in the window and the latest release
   - Stars / forks; package download counts where the project publishes packages
     (e.g. npm: https://api.npmjs.org/downloads/point/<start>:<end>/<package>)
   - Maintainer roster: read MAINTAINERS.md if present (note if it is unmerged/draft).

3. Gather LFX Insights data from the project's LFX URL: active contributors, retention,
   contribution concentration (how many contributors / organisations account for >50%
   of contributions), merge lead time, issue-resolution time, active days, and the
   overall health rating. NOTE: the LFX dashboard is client-rendered, so a simple fetch
   may return the same default-window snapshot regardless of the time-range parameter.
   If you cannot get genuinely window-specific figures, say so, and where useful derive
   trends (e.g. contribution concentration over 90 / 180 / 365 days) directly from git
   history instead — and label them as git-derived.

   FALLBACK (if you do NOT have `gh`/CLI or shell access — e.g. a plain chat assistant):
   gather the same figures from public web pages instead, and label each number with
   where it came from:
   - GitHub Insights tabs on the repo: /pulse and /graphs/contributors (contributors,
     commit activity), and the Issues and Pull Requests tabs with filters
     (e.g. `is:pr is:merged merged:<start>..<end>`) — the result header shows the count.
   - Releases page (/releases) for releases in the window and the latest release.
   - The repo's MAINTAINERS.md (raw view) for the maintainer roster.
   - Package registry pages for downloads (e.g. npmjs.com, or the npm downloads API URL
     in step 2, which is a plain GET you can open in a browser).
   - The LFX Insights URL for the project's contributor/health metrics.
   If you cannot retrieve a given figure, leave it clearly marked as
   "[to be filled in by maintainer]" rather than guessing.

4. Fill in the template section by section, using only the headings the template
   defines (Project Overview; Current Status; Community & Contribution Metrics;
   Challenges & Blockers; Roadmap & Goals for Next 6 Months; TOC Support Needed;
   Additional Information). Keep claims factual and attributable. For the metrics
   section, present concrete numbers with their source and window. Highlight notable
   adoption (downstream products built on the project), community-depth signals (e.g.
   maintainers from organisations beyond the FINOS membership), and any health trends
   (improving or worsening) rather than a single snapshot.

5. Output the finished report as a single markdown file named
   <Year>-H<X>-<ProjectName>.md, ready for me to review.

6. After the draft, give me a short reviewer checklist of every figure and claim you are
   least confident about, and anything I should confirm or correct before I raise the PR.

CONSTRAINTS:
- This is a draft for my review — I will verify and amend it before raising the PR.
- Be explicit about sources, windows, and any inference or estimation.
- Do not raise the PR yourself.
```

---

## Metrics window

The report covers the half-year reporting period (H1 = Jan–Jun, H2 = Jul–Dec), but
quantitative metrics use a **trailing-365-day window** so trends aren't distorted by the
six-month boundary. Label every figure with its source and window.

---

## Maintainer checklist before raising the PR

- [ ] Every metric checked against its stated source and window.
- [ ] Maintainer list correct and complete (and reconciled with `MAINTAINERS.md`).
- [ ] Accomplishments, roadmap, and TOC-support asks reflect the maintainers' actual view.
- [ ] Challenges/blockers are honest (don't omit known risks).
- [ ] Filename and format match the FINOS template
      (`project-reports/<Year>/<Year>-H<X>-<ProjectName>.md`).
- [ ] Report is clear and self-explanatory enough to answer likely TOC questions in
      writing — remembering the TOC may call you to present if it has questions or concerns.

Raise the report as a PR to the `project-reports/` folder of
`finos/technical-oversight-committee` at least two weeks before the relevant TOC meeting.
